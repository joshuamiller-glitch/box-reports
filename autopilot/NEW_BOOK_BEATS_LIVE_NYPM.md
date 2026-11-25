# NEW_BOOK_BEATS_LIVE_NYPM - does a new book beat the live NY PM book(s) in the exact engine? (W-NYENG, order 0210Z), refreshed 2026-11-25 15:00Z

**vs TODAY's stack (JL3, today's DAY-DONE); provisional until Asia and London are decided; label BETTER = calibration pending, NOT calibrated.** Rule: REPLACE row (the new book switched on, the named live book's NY PM entries switched OFF) beats that live book when, DRAWDOWN FIRST, the stack ulcer change is < 0 AND the mean $/week change is >= 0 on BOTH the last 6 and last 3 months (engine base lots, $4.84 RT proxy); then prior years must show no RED (> 30% worse on ulcer / max DD / mean) where run; persistence > 0.60 and the 30 date-shift controls are still PENDING for every row below (shown as counts). Bare R0/R3 only orders the engine queue. Live books of this session: K7. verdict yes / no / pending (not run or months not landed). Sorted by the best last-6-month stack-ulcer change of any REPLACE row (most negative first). Full table of every cell: /mnt/l2/l2vast/_nye/beats_NYPM.csv.

**Counts (distinct event streams: parked twins are listed with the label [twin of ...] but NOT counted again):** cells with any engine row 384; cells with a finished REPLACE verdict (L6M+L3M landed) 181; cells that beat at least one live book on L6M+L3M (BETTER, calibration pending) 4; twin cells listed 405.

## Cells that beat a live book (yes), drawdown first
| rank | cell | REPLACE K7 | ADD | prior years run | controls |
|---|---|---|---|---|---|
| 51 | time_m_3 / manual_macd.zero {"f": 5, "s": 13, "g": 5} / sym15u / both | yes (L6M du -411 dm +419 | L3M du -721 dm +324) | not run | K7:0 | 0 of 30 |
| 231 | [twin of L200d27da] time_m_3 / manual_macd.zero {"f": 5, "s": 13, "g": 5} / sym15u / both | yes (L6M du -411 dm +419 | L3M du -721 dm +324) | not run | K7:0 | 0 of 30 |
| 227 | [twin of L0ff67f61] swing_atr_0.4 / tape_stack.r5_fade {"k": 4} / sym15u / both | yes (L6M du -347 dm +694 | L3M du -563 dm +2012 RED Y2023) | not run | K7:3 | 0 of 30 |
| 221 | [twin of L79612dbe] drb_1200 / levels_profile_va.break {"n": 2, "k": 0.5} / asym20u/10u / both | yes (L6M du -96 dm +109 | L3M du -311 dm +1142) | not run | K7:3 | 0 of 30 |
| 273 | [twin of Lba08182a] drb_1200 / book_cancel.net_follow_native {"L": 3600, "z": 2.0} / plain60/60 / both | yes (L6M du -75 dm +434 | L3M du -367 dm +1130) | not run | K7:0 | 0 of 30 |
| 206 | mom_20 / momentum_roc.zero {"len": 60, "wd": 5} / sym15u / both | yes (L6M du -53 dm +200 | L3M du -265 dm +810 RED Y2023) | not run | K7:3 | 0 of 30 |
| 662 | mrenko_14 / trend_ma_kama.cross_native {"len": 25, "width": 1.0, "ratio": 3} / sym15u / both | yes (L6M du -36 dm +237 | L3M du -113 dm +1089) | not run | K7:0 | 0 of 30 |
| 157 | [twin of L087795dd] mrenko_14 / trend_ma_kama.cross_native {"len": 25, "width": 1.0, "ratio": 3} / sym15u / both | yes (L6M du -36 dm +237 | L3M du -113 dm +1089) | not run | K7:0 | 0 of 30 |
| 31 | tib_6000 / levels_trendline.break_native {"n": 3, "k": 0.5} / sym15u / long | yes (L6M du -13 dm +369 | L3M du -98 dm +1096) | not run | K7:0 | 0 of 30 |
| 106 | [twin of L9e5dc1ad] tib_6000 / levels_trendline.break_native {"n": 3, "k": 0.5} / sym15u / long | yes (L6M du -13 dm +369 | L3M du -98 dm +1096) | not run | K7:0 | 0 of 30 |

## Both-side / long-only / short-only rows side by side (order 1014Z; both-side sets are VALID engine results for the both-side book; LO / SO = mode-correct sets, engine-tested separately; replace K7 and ADD; vs the live stack, engine base lots; d = change vs JL3, ulcer first)
| cell (id) | row | variant | L6M d ulcer / d worst wk / d max DD / d mean $/wk | L3M d ulcer / d worst / d max DD / d mean | beats K7 (yes/no/pending) |
|---|---|---|---|---|---|
| L200d27da | both sides | RK7 | -411 / +3357 / +1257 / +419 | -721 / +4026 / +1257 / +324 | yes |
| L200d27da (both) | both sides | ADD | not run yet | | |
| L200d27da (both) | long-only | RK7 | not run yet | | |
| L200d27da (both) | long-only | ADD | not run yet | | |
| L200d27da (both) | short-only | RK7 | not run yet | | |
| L200d27da (both) | short-only | ADD | not run yet | | |
| Ldc3ee3f7 | both sides | RK7 | -411 / +3357 / +1257 / +419 | -721 / +4026 / +1257 / +324 | yes |
| Ldc3ee3f7 (both) | both sides | ADD | not run yet | | |
| Ldc3ee3f7 (both) | long-only | RK7 | not run yet | | |
| Ldc3ee3f7 (both) | long-only | ADD | not run yet | | |
| Ldc3ee3f7 (both) | short-only | RK7 | not run yet | | |
| Ldc3ee3f7 (both) | short-only | ADD | not run yet | | |
| L5b7d6160 | both sides | RK7 | -347 / +3386 / +1182 / +694 | -563 / +3386 / +1182 / +2012 | yes |
| L5b7d6160 (both) | both sides | ADD | not run yet | | |
| L5b7d6160 (both) | long-only | RK7 | not run yet | | |
| L5b7d6160 (both) | long-only | ADD | not run yet | | |
| L5b7d6160 (both) | short-only | RK7 | not run yet | | |
| L5b7d6160 (both) | short-only | ADD | not run yet | | |
| Lc536dec7 | both sides | RK7 | -96 / +21 / +487 / +109 | -311 / +21 / +487 / +1142 | yes |
| Lc536dec7 (both) | both sides | ADD | not run yet | | |
| Lc536dec7 (both) | long-only | RK7 | not run yet | | |
| Lc536dec7 (both) | long-only | ADD | not run yet | | |
| Lc536dec7 (both) | short-only | RK7 | not run yet | | |
| Lc536dec7 (both) | short-only | ADD | not run yet | | |
| Lc8319f0b | both sides | RK7 | -75 / +978 / +1827 / +434 | -367 / +2346 / +1827 / +1130 | yes |
| Lc8319f0b (both) | both sides | ADD | not run yet | | |
| Lc8319f0b (both) | long-only | RK7 | not run yet | | |
| Lc8319f0b (both) | long-only | ADD | not run yet | | |
| Lc8319f0b (both) | short-only | RK7 | not run yet | | |
| Lc8319f0b (both) | short-only | ADD | not run yet | | |
| L87139436 | both sides | RK7 | -53 / +1571 / +492 / +200 | -265 / +1571 / +492 / +810 | yes |
| L87139436 (both) | both sides | ADD | not run yet | | |
| L87139436 (both) | long-only | RK7 | not run yet | | |
| L87139436 (both) | long-only | ADD | not run yet | | |
| L87139436 (both) | short-only | RK7 | not run yet | | |
| L87139436 (both) | short-only | ADD | not run yet | | |
| L087795dd | both sides | RK7 | -36 / +1061 / -943 / +237 | -113 / +1061 / -943 / +1089 | yes |
| L087795dd (both) | both sides | ADD | not run yet | | |
| L087795dd (both) | long-only | RK7 | not run yet | | |
| L087795dd (both) | long-only | ADD | not run yet | | |
| L087795dd (both) | short-only | RK7 | not run yet | | |
| L087795dd (both) | short-only | ADD | not run yet | | |
| Lea540208 | both sides | RK7 | -36 / +1061 / -943 / +237 | -113 / +1061 / -943 / +1089 | yes |
| Lea540208 (both) | both sides | ADD | not run yet | | |
| Lea540208 (both) | long-only | RK7 | not run yet | | |
| Lea540208 (both) | long-only | ADD | not run yet | | |
| Lea540208 (both) | short-only | RK7 | not run yet | | |
| Lea540208 (both) | short-only | ADD | not run yet | | |
| L9e5dc1ad | both sides | RK7 | -13 / +2056 / +92 / +369 | -98 / +2056 / +92 / +1096 | yes |
| L9e5dc1ad (both sides, engine-tested) | both sides | ADD | not run yet | | |
| L9e5dc1ad (long) | long-only | RK7 | not run yet | | |
| L9e5dc1ad (long) | long-only | ADD | not run yet | | |
| L9e5dc1ad (long) | short-only | RK7 | not run yet | | |
| L9e5dc1ad (long) | short-only | ADD | not run yet | | |
| Lf653e682 | both sides | RK7 | -13 / +2056 / +92 / +369 | -98 / +2056 / +92 / +1096 | yes |
| Lf653e682 (both sides, engine-tested) | both sides | ADD | not run yet | | |
| Lf653e682 (long) | long-only | RK7 | not run yet | | |
| Lf653e682 (long) | long-only | ADD | not run yet | | |
| Lf653e682 (long) | short-only | RK7 | not run yet | | |
| Lf653e682 (long) | short-only | ADD | not run yet | | |

## D8 gate under the exit-run rule (order 0213Z)
Nothing enters D8 without the EXIT RUN (all 68 recipes, 7 families) on its own entries beside the fixed brackets. Candidate hand-over: autopilot/D8_CANDIDATES.txt (append-only; 789 cells with engine rows listed, one line per live book). Exit run progress: screen stage (68 recipes x params on real entries + null draws) NOT started by W-NYENG on these candidates yet (owner: the exit-screen stage; start order = D8_CANDIDATES.txt engine rank); engine families that cannot run a recipe yet and their build dates: autopilot/D8_EXIT_ENGINE_SUPPORT.md (per-entry stops/targets/time exits run now; opposite-signal exit 11-19 14:00Z; trailing / staged / SAR 11-19 18:00Z; order-flow exits 11-20 12:00Z). Engine cost after the exit screen per candidate: top 3 recipes x (ADD + REPLACE) x (6 last-6-month + 37 prior-year months) + 30 date-shift controls x 6 = 438 set-months; for the 10 candidates that beat a live book now = 4380 set-months = 4.7 h at 928 set-months/h (1.5 h at 2,894/h). D8 SPEC DATE: not before the exit-screen stage and the unbuilt engine families are done; earliest realistic 2026-11-20 12:00Z for the cells that beat a live book today if the exit screen starts by 11-19 06:00Z (cannot be firmer: the screen duration is not measured, the candidate list is still growing).

## All other cells: see the csv (verdict per live book: no / pending)

