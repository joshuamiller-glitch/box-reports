# D8_NYPM_NOTES: NY PM (12:00-16:00 ET) stack for the D8 NinjaTrader port

Written 2026-11-23 17:25Z by W-D8SPEC4 (order 1705Z, Josh: "we have no NY PM yet to code?"). Research only. Same job as D8_LONDON_NOTES.md (London) and the NY AM blocks.
Stack = NY PM FINAL, equal weight, complete pool of 6 (finals_ready 07:45Z, controls beaten 30 / 18 / 30 = L6M drawdown-first / L3M / ulcer-only; the L3M 18 of 30 is the weak spot): `L52359bf4.BRP30 + L8e0bf58c.BRS8U + L4bdd521a.BRF80_40 + L2c6916a5.BRP60`, 1 lot each in the bare run. Stack identity of the layer fit: `STKd893133bd8`.
All SPEC / OPEN labels refer to autopilot/D8_BUILD_SPEC.md blocks `AUTO:BOOK:<book>` (hand-written now; SPEC = read from engine code and confirmed by re-implementation, OPEN = not decided or not measurable here).

## 1. What is where
| item | where |
|---|---|
| hand-written book blocks (bar rule, trigger, bracket, entry, window, data, per-day thresholds) | D8_BUILD_SPEC.md, `AUTO:BOOK:L52359bf4`, `L8e0bf58c`, `L4bdd521a`, `L2c6916a5` (refreshed by code/th_d8spec/gen_book_blocks.py; backups `.bak_1715`-style next to it) |
| independent re-implementation | code/d8_spec4/check4.py (`python3 -I check4.py <book>`), code/d8_spec4/rebuild_anch.py (anchored bars) |
| parity pages (bars, signals, trades, INPUTS with per-day thresholds) | autopilot/D8_PARITY_<book>_<td>.md: L52359bf4 and L2c6916a5 20261109 + 20261110; L4bdd521a 20261109 + 20261110 (both without a signal) + extra day 20261106 (2 signals); L8e0bf58c 20261109 (no anchor, no bars) + 20261110 (bars, no ZN data) + extra days 20261103 (4 signals) and 20261102 (9 signals). Generator: code/d8_spec4/parity4.py (`--refresh` adds the TRADES block when the engine month lands; hooked into parity_md.py, which now skips pages carrying the parity4.py marker) |

## 2. Independent re-implementation against the engine events (23 Nov, own code from raw inputs)
| book | engine events | mine | matched | only-engine | only-mine |
|---|---|---|---|---|---|
| L52359bf4 (tm120 ATR-channel fade) | 6,863 | 6,863 | 6,863 | 0 | 0 |
| L4bdd521a (tm1800 + YM) | 1,554 | 1,554 | 1,554 | 0 | 0 |
| L2c6916a5 (tm15 delta divergence fade) | 6,142 | 6,142 | 6,142 | 0 | 0 |
| L8e0bf58c (anch_PDN_B25 + ZN), PLAIN record anchor store | 1,861 | 1,861 | 1,861 | 0 | 0 |
| L8e0bf58c on the D8 print-rule (_CANR) anchor store | 1,861 | 1,861 | 1,102 | 759 | 758 |

Times and sides compared (events at floor(known second) + 2 s). The anchored buckets were also rebuilt from the raw trade rows (rebuild_anch.py): identical to the stored bars on 4 of 4 sample days that have an anchor hit (20261102, 20261103, 20261110 + one earlier day); 20261109 has no hit.

**OPEN DECISION for the LEAD / Josh (the one real finding): L8e0bf58c was run on bars built from raw trade RECORDS (no merging), not on the D8 print-rule bars.** A port that builds equal-volume anchored bars from merged prints reproduces only 1,102 of the 1,861 engine events (59%). Options: (a) the port builds this book's bars from raw execution records (NT8 tick = one record: nothing merged); (b) re-run the book's events and bare set on the `_d8spec/bars_c/anch_PDN_B25` bars first and judge it again (a new verdict). Recommendation: (a) if NT8 delivers records unmerged, otherwise (b); until decided the book ships OFF.
Also: the ZN and YM 1-minute files on the box end 2026-11-10 07:59Z (ZN) and 2026-11-13 05:59Z (YM); NQ minute store ends 2026-11-13 21:59Z. Hence no ZN parity is possible for the NY PM of 20261110 (no ZN signal that day).

## 3. Can NinjaTrader reproduce each book? (NQ ticks with bid/ask, level-2 depth, 1-minute bars of other futures)
| book | needs | verdict |
|---|---|---|
| L52359bf4.BRP30 | NQ ticks only (120-second clock-grid bars; the trigger reads OHLC) | YES. No depth, no other symbol. Risk: first-tick-of-next-bar close timing and a cold-start ATR (load >= 2,000 bars). |
| L2c6916a5.BRP60 | NQ ticks with AGGRESSOR side (bar delta); 15-second clock-grid bars | YES in principle (Time & Sales with bid/ask give the side). Real risk = delta-sign agreement between NT8's last-vs-bid/ask classification and the exchange flag the engine used: OPEN, to be measured on Josh's NT8 export (compare per-bar delta signs on the 960 bars of td 20261109/10). If the agreement is poor, ship OFF. |
| L4bdd521a.BRF80_40 | NQ ticks (30-minute bars, only the known time is used) + YM 1-minute closes + NQ 1-minute closes + 3 days of history for sigma | YES with a second data series (YM 1 minute). OPEN: roll timing of the NT8 YM continuous contract vs the Databento calendar front month; completed-minute rule (start + 60 s <= bar known time). |
| L8e0bf58c.BRS8U | NQ records (anchored equal-volume bars; previous-day POC from the previous NY RTH tape; 20-day NY RTH volume history for V) + ZN 1-minute closes + 3 days ZN history | CONDITIONAL. ZN as a second 1-minute series is fine; the anchored bars need unmerged records (see the decision above) and the POC / V history must be kept by the strategy (store a daily file). Ship OFF until the print-rule decision is made. |

None of the four needs the 10-level cancel tape or MBO to produce its SIGNALS. (The engine fills walk the 10-level book, but live fills are real fills.) None needs NQ depth for the trigger. Only the layer fit (W-LAYERS2) may use depth-based layers: that belongs to its keys page.
Data beyond NQ trades, by book: L52359bf4 none; L2c6916a5 aggressor flag; L4bdd521a YM and NQ 1-minute closes (+ contract ids); L8e0bf58c ZN 1-minute closes (+ contract id), NQ prior-day profile and 20-day NY RTH volume.

## 4. Exit verdicts (W-EXITSTAT lines in MORNING.md 17:03Z and 17:09Z; recipes = 8 exit-recipe sets per book, ulcer at L6M and L3M against the fixed bracket; a recipe survives only if BOTH windows are lower)
| book (fixed ulcer L6M / L3M) | best L6M recipe | lowest L3M recipe | verdict |
|---|---|---|---|
| L52359bf4.BRP30 (2,064 / 2,454) | flowp_v15_t2 2,275 (+10%), L3M 2,711 (+10%) | none lower in both | NONE KEPT |
| L8e0bf58c.BRS8U (2,503 / 1,582) | flow_v25 2,707 (+8%), L3M 2,403 | flowp_v15_t2 L3M 754 but L6M 5,922 | NONE KEPT (the 8th recipe sar_v40 scored 17:09Z: L6M 11,461 / L3M 5,471: fails) |
| L4bdd521a.BRF80_40 (2,024 / 1,719) | oppx_v15_t2 3,000 (+48%), L3M 2,543 | sar_v40 L3M 1,370 but L6M 5,166 | NONE KEPT |
| L2c6916a5.BRP60 (2,925 / 2,356) | oppx_v15_t2 3,937 (+35%), L3M 3,533 | sar_v15 L3M 1,975 but L6M 8,694 | NONE KEPT |

Result: the NY PM exit run is complete, NONE KEPT on all four books (no recipe reaches stage 2, no prior-year months queued). D8 NY PM = fixed bracket + scheduled session-end exit at 16:00 ET (rule "nothing in D8 without the exit run": MET). Same verdict as London and NY AM.

## 5. NY PM bare all-layers fit (W-LAYERS2, stack `STKd893133bd8`, joint) and its keys / defaults pages
- Stack identity: `STKd893133bd8` = the recent-basis equal FINAL above (W-LAYERS2 ruling 17:04Z). The weighted 2-book final `STKd81d0693ad` and the older `STKd8e3868036` are HELD (reference), generators stopped, JT rows parked in `_layers/parked_np_ref_jt_STKd8e3868036.txt`.
- Screen: landed 16:44Z (5,412 single-setting rows at 1 / 2 / 4 lots). Joint: built 16:44Z, 10,080 rows planned (3,360 per lot basis), about 1,500 in the queue file at 17:02Z, 2 joint dirs started at 17:16Z, none done. Rank NP (behind the Asia re-run). LEAD estimate 17:03Z: ~5 h at ~4k rows/h for the two NY PM joints; with the second stack held the one joint alone is ~2.5 h of pool time: **ETA of the joint verdict about 21:30-23:30Z tonight**, later if the Asia daily-loss re-run takes the slots (unconfirmed, ask W-LAYERS2).
- Keys and defaults pages: `autopilot/D8_LAYER_KEYS_NYPM.md` and `autopilot/D8_LAYER_DEFAULTS_NYPM.md` are NOT written yet; they follow the joint verdict (same layout as D8_LAYER_KEYS_NYAM.md / D8_LAYER_DEFAULTS_NYAM.md: MF1..MF4 mapping = L52359bf4 / L8e0bf58c / L4bdd521a / L2c6916a5 in this order with stop/target 30/30, 120/120, 80/40, 60/60 pts as the fit used them; every code of the pick resolved to numbers; recommended lot basis for 2 lots per book with the reason). ASK (MORNING.md line to W-LAYERS2, nothing queued by me): write both pages within one hour of the joint verdict, and say in the defaults page which lot basis (1 / 2 / 4) the 2-lots-per-book account should follow; the Asia defaults followed the 4-lot pick. Until then D8 NY PM ships bare (fixed bracket, 1 position per book, session-end 16:00 ET) with every layer's default OFF/reference.
- Bare D8 NY PM yardstick from the fit's own base sets (1 / 2 / 4 lots; ulcer / max DD / worst week / mean $ per week, net of $4.84, L6M and L3M and years):

| set | L6M | L3M | 2023 | 2024 | 2025 |
|---|---|---|---|---|---|
| D8 NP bare stack, 1 lot per book (`TL3_SR_NP_STKd893133bd8_BF1_BASE`) | 2,723 / -12,121 / -4,238 / +4,629 | 2,089 / -7,269 / -4,238 / +4,340 | 4,061 / -15,835 / -8,495 / +1,725 | 10,467 / -29,188 / -10,807 / +1,325 | 5,998 / -17,976 / -11,409 / +2,157 |
| 2 lots per book (BF2_BASE) | 5,573 / -24,257 / -8,566 / +8,736 | 4,143 / -14,543 / -8,566 / +8,718 | 8,093 / -31,725 / -17,024 / +3,415 | 21,719 / -58,752 / -21,635 / +2,516 | 12,184 / -35,977 / -22,882 / +4,223 |
| 4 lots per book (BF4_BASE) | 11,340 / -48,755 / -17,930 / +16,377 | 8,376 / -29,391 / -17,417 / +17,226 | 16,348 / -63,739 / -34,079 / +6,650 | 44,358 / -113,869 / -43,385 / +4,939 | 25,711 / -76,748 / -45,419 / +7,983 |

## 6. Bare D7 NY PM yardstick rows (the only comparator for bare D8; "judge D8 bare only against D7 bare")
BARE_D7_YARDSTICK.md and BARE_D7_REF.json have NO NY PM section yet (they cover Asia, NY AM, London). The NY PM row comes from the W-COMBO set `TL3_ALN_NP_STKLIVE_BARER0` (truly bare R0, 1 lot, base dollars, net of $4.84; the D7 NY PM stack contains ONE book: K7 = MF1, 596 trades in the 2026 months landed, so "K7 alone" = the stack): 

| window | ulcer / max DD / worst week / mean $ per week |
|---|---|
| L6M (202605-202610) | 10,771 / -22,593 / -6,658 / -48 |
| L3M (202608-202610) | 13,886 / -21,422 / -6,658 / -943 |
| 2023 (Apr-Dec) | 13,941 / -26,816 / -6,953 / -505 |
| 2024 | 10,794 / -26,604 / -8,098 / +677 |
| 2025 | 17,875 / -33,310 / -8,264 / -298 |

Bare D8 4-book stack at 1 lot per book, L6M: ulcer 2,723 (25% of D7's), max DD -12,121 (54% of D7's), worst week -4,238 (64%), mean +4,629 per week against -48 (D7). Same windows for the four bare books alone (1 lot, ulcer / max DD / worst week / mean $/wk), sets `TL3_ALN_NP_<book>_R0<tag>`:
| book | L6M | L3M | 2023 | 2024 | 2025 |
|---|---|---|---|---|---|
| L52359bf4.BRP30 | 2,064 / -6,398 / -3,204 / +1,188 | 2,454 / -6,398 / -3,204 / +483 | 3,604 / -10,745 / -4,977 / +179 | 4,798 / -12,186 / -5,767 / +189 | 3,153 / -7,798 / -3,803 / +769 |
| L8e0bf58c.BRS8U | 2,503 / -9,569 / -3,064 / +1,152 | 1,582 / -4,374 / -3,064 / +1,522 | 3,254 / -8,697 / -3,360 / +725 | 10,721 / -25,175 / -5,099 / +486 | 8,147 / -19,848 / -7,099 / +191 |
| L4bdd521a.BRF80_40 | 2,024 / -5,637 / -2,415 / +1,057 | 1,719 / -3,944 / -2,374 / +1,080 | 2,453 / -6,278 / -3,184 / +628 | 6,574 / -15,622 / -5,984 / +187 | 2,124 / -6,533 / -4,774 / +1,131 |
| L2c6916a5.BRP60 | 2,925 / -9,413 / -3,114 / +1,233 | 2,356 / -5,590 / -3,114 / +1,254 | 9,016 / -18,840 / -6,774 / +193 | 5,902 / -16,738 / -6,043 / +463 | 7,559 / -15,295 / -6,623 / +65 |
Caution: the prior-year columns for L8e0bf58c (2024, 2025) and L2c6916a5 (2023) are weak against the L6M pick (ulcer 3-4x L6M); the stack (row above) is milder. These figures are the bare sets (account layers at the R0 stand-in, no pick); the 1,861 / 6,142 event counts are the all-history events. W-COMBO2 rows: the stack final scored by W-COMBO2 (controls 30 / 18 / 30; L6M step 1 R1 $1,188 per week for L52359bf4) is the one named in the header; its pick pages are COMBO2 pages (see MORNING.md 10:07Z).
NOTE to the LEAD (needs a one-line fix by the owner): add the NY PM rows above to BARE_D7_YARDSTICK.md / BARE_D7_REF.json (key `NP`), because bare_score.py has no `NP` session; I did not edit that file (not mine).

## 7. What stays OPEN for the port (plain list)
1. L8e0bf58c print rule (section 2): decision needed.
2. L2c6916a5: per-bar delta sign agreement NT8 versus the engine flag (measure on Josh's NT8 export).
3. L4bdd521a / L8e0bf58c: roll rule of YM / ZN in NT8 versus the Databento calendar front month; completed-minute timing.
4. TRADES blocks of the parity pages for td 202611: the bare sets (`TL3_ALN_NP_<book>_R0<tag>`) hold months 202304-202610 only. ASK (nothing queued by me): run month 202611 of the four bare sets so the 1109 / 1110 trade blocks can be filled; the refresher (`parity4.py --refresh`, called by parity_md.py) fills them within one cycle once `<set>/202611/trades.parquet` exists.
5. NY PM layer keys / defaults pages (section 5) after the joint verdict.
6. Session-end exit for NY PM books = 16:00:00 ET (21:00Z in winter, 20:00Z in summer), executed 1.0 s later with the 120 s last-print rule; the generic stack-rule text in the spec still lists Asia / NY AM session-end times: read block line (d) of each NY PM book.
7. Both L52359bf4 and L4bdd521a produce signals only through 15:59:xx ET: the 16:00 bar is dropped by the session end.
