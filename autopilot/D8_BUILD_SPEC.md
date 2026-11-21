# D8_BUILD_SPEC.md, DRAFT Asia v1 (rev 2: option C added), pool hash 40997a38e64772fd, written 2026-11-21T10:00Z, revised 2026-11-21T11:43Z

**STATUS: DRAFT, NOT FROZEN.** **ALL NUMBERS IN THIS DRAFT ARE 'POOL 28' (the 28-book pool of the hash below). The ENLARGED UNIVERSE (the 1,244 _CANC ids; the first 11:3xZ fix found only 718 in the loops' universe) is being re-run by W-COMBO; its finals are NOT in this draft and will be added in a separate block labelled 'ENLARGED UNIVERSE' when W-COMBO posts them. The two are never mixed.** Pool hash = first 16 hex of sha256 of the comma-joined sorted pool ids of `/mnt/l2/l2vast/_combo/reselect_asia_own_d8.json` key `pool` (28 books; file time 09:52Z). **The final choice between option A and option B, and every number marked PENDING, wait for the loop re-run (about 11:00Z) and Josh's choice.** Written by W-D8SPEC (documentation only, no engine slots). Freeze rule (Josh 02:01Z): the Asia spec v1 is frozen into this file when the Asia chain completes (estimate 11:00-12:00Z). Labels: SPEC-BACKED (engine-tested exactly as written) / BEST-AVAILABLE-NOT-PROVEN (stated per item).

## 1. Common facts (apply to every Asia book below)

### 1.1 Print rule (SPEC-BACKED; full text and proof tables in `D8_PRINT_RULE.md`)
- **Prints** = consecutive trade records with the same price and the same side, no time condition, merged (sizes added). Side = **last >= ask: buy; last <= bid: sell; else unclassified (0)**; the buy test comes first (locked or crossed book gives buy); a missing bid or ask: treat as 0 and log (never seen in the engine data). A run never crosses a session boundary or a contract change.
- **Causal stamp (_CANC):** a bar closed by a print is stamped with the time the run is KNOWN complete = the timestamp of the next print with a different price or side (the last run of a session: its last record). This is the D8 working rule (lead decision; 100.000% of print boundaries identical to Josh's NT8/CQG export on Asia and NY AM td 20261110: `D8_FEED_CHECK.md` section 7). `_CANR` (first-record stamp) is look-ahead and reference only.
- **Event time** = floor(known time of the signal bar in whole seconds) + 2 s. Entry fill: first print after the event time (engine set parameters: fill "through", hair 0.5, wait 10 s).

### 1.2 Bar classes (SPEC-BACKED; `D8_PRINT_RULE.md` section 5, month 2026-10 test)
- **Unaffected by the print rule (build from raw ticks; BASE results stand):** time bars tm<N> / time_m / time_s, rng, renko, mrenko, urenko, frenko, kagi, dchg, swing, pnf, pasl, lbrk.
- **Affected (need the run merge / _CANC): vol, vsess, tick, dlt, dol, cdr, dib, tib, vib, drb, trb, vrb, mom, cusum, vnorm, trend, wrenko** (anch, entropy, dltor treated as affected, builder pending). Bars are rebuilt per `D8_BAR_DEFS.md` (rules, daily thresholds from the previous 20 trading days' total volume / 610,702 for volume-type bars, session resets at 02:00, 08:30, 09:30, 12:00, 16:00, 18:00 ET, truncated last bar of each session gives no signal).
- **Epoch time bars tm<N>:** boundaries = multiples of N seconds since 1970-01-01 UTC, boundary print goes to the new bar, empty buckets give no bar, close stamped at max(boundary, first print of the next bucket), no session reset (`D8_BAR_DEFS.md` section 8). time_m_<N>: grid anchored on the first print of the session segment (Asia: 23:00:00 UTC = 18:00:00 ET), known at the bucket end, truncated last bucket (part = 1, no signal).

### 1.3 Session, roll and back-adjust facts
- Sessions (ET): Asia 18:00-02:00 (= 23:00-07:00 UTC in EST, 22:00-06:00 UTC in EDT); London 02:00-08:30; pre 08:30-09:30; NY AM 09:30-12:00; NY PM 12:00-16:00; close 16:00-18:00; trading date = ET + 6 h. Asia signals only; every position is flat at the session end (07:00 UTC in EST), with the 120 s exit cap (if no print follows the scheduled exit within 120 s, exit at the last print before it).
- **Roll back-adjust (iid, real-roll version):** the older bars are shifted by the roll gap at the 14 real contract rolls only (instrument id = number of real rolls with roll time <= bar known time; `/mnt/l2/l2vast/_bars/feat_d/nq_rolls.csv`). The earlier _CANC events of triggers_b books (pullback / structure / libstack) used the instrument id of the ORIGINAL bar store keyed by (session, bar index): up to about 0.7% of those books' signals carry extra adjust steps (La010c3eb 0.72%, M3f6f752c 0.52%, Lfb608c7b 0.33%); La010c3eb was rebuilt as **_CANF** with real rolls. Momentum, bands and level triggers (incl. the L385f4f2e parent) do not back-adjust at all.
- Fees and lots: **$4.84 round trip per lot** (fee included in all results). **Base lots = 1**; live lots = max(1, floor(1.75 x base + 0.5)) (so base 1 gives live 2). All engine results below are at base 1 lot, book alone on the all-new base (account layers of the D7 stand-in on, no other live book trading in the session).
- **Entry / stop / target / flat as tested:** market entry on the event, stop 60 points and target 60 points (bracket plain60/60) from the fill, flat at session end (section 1.3), both sides. **Layers kept: none** (no pass-2 layer other than the J502 entry filter of option A; no loss cut, no lock, no take rules, no exit family, no zones/sizer layer). **Exits kept: none** beyond the bracket and the session-end flat.

### 1.4 Known artefacts (state them in every port review)
- **November 2026 tape hole** (trading dates 2026-11-02 to 11-04 and the morning of 11-05 missing): the engine's OPEN_MONTH and MVWAP in November are anchored at 2026-11-05 16:00 UTC (a complete NT8 month differs), PRF5 for label days 11-10 to about 11-16 includes the partial 11-05 session (a complete history differs), stats-table scales skip the hole. J502 reads OPEN_MONTH (condition c1) and PRF1 only; PRF5 and MVWAP are not in the Asia options.
- **CQG timestamps lag the exchange stamps** (median about 0, p99 +43 ms Asia, max +0.26 s Asia; NY p99 +0.59 s, max +1.58 s): bars are exact (identical contract stream), minute-grid line lookups can move only for events within the lag of a minute boundary (measured effect on J502: 2 of 1,507 condition flags, 0 survivors at 0.26 s).
- **First 2000-bar constants of native triggers** are not used by any Asia option (no native variant).

## 2. The two Asia OPTIONS (Josh chooses; both carried; PENDING = re-run)

### 2A. OPTION A [POOL 28]: one book, L385f4f2e.J502 (set TL3_ALN_AS_L385f4f2e_P2JCX502)
- **Bar:** vol_2600 on the _CANC rule (threshold 2600 x s_vol contracts per trading date; 20261110: 2888.67). Vectors: `D8_VECTORS_CANC_L385f4f2e.md`.
- **Trigger (parent):** trig_momentum_rsi mom, RSI(14) Wilder on the bar closes of the continuous series: long when RSI crosses up through 60, short when it crosses down through 40, both sides. Exact definition, state, per-bar tables, my recompute = the module on 18,566 signals: `D8_TRIGDEBUG_L385f4f2e.md`.
- **Bracket:** plain60/60, flat at session end. **Layers/exits kept:** none.
- **Entry filter J502 = C1 setting `C1_X10_5_084f2c` (5 of 10 conditions) AND C3 setting `C3_dropblk10` (drop Asia 30-minute block 10 = 23:00-23:30 ET)**, nothing flipped. Whole history: 1,507 parent events, 847 after C1, 1,446 after C3, **815 after both**. Every condition in words and formula, the data each reads, per-event values for the sample sessions and the NT8 feasibility of each condition: `D8_P2_J502_FILTER.md`.
- **NT8 computability:** the bar, RSI, C3 and conditions c1, c3-c8 from NQ last/bid/ask ticks; **c2 (Fibonacci touch from 15/60-minute fractal-pivot zig-zag levels) needs an exact port of pivot/zig-zag code and up to 30 days of 1-minute history; c9 (ES) and c10 (YM) need ES and YM 1-minute data (CQG) and 72 hours of history: NOT computable from NQ ticks.** No depth needed.
- **Risks:** thin prior years (2023 +$40/wk); L6M from a quiet period (166 trades); its plain _CANC base earns only $476/wk in L6M (the filter is what makes it); several conditions sit near their thresholds (fragile to one contract of delta or to a missing ES/YM minute); the filter needs two other instruments' data.
- **Results (W-COMBO, ASIA_ONE_BOOK_EXPLAIN.md; ulcer / max DD / worst week / $ per week, base 1 lot; label LEAD: one book, prior years thin, fits pending; PENDING loop re-run):**

| window | J502 alone | BARE D7 Asia at the same L6M drawdown (x0.04) |
|---|---|---|
| L6M | 469 / -1915 / -1600 / 2157 | 469 / -1153 / -755 / 202 |
| L3M | 519 / -1915 / -219 / 2514 | 436 / -998 / -637 / 114 |
| 2023 | 2327 / -4696 / -2024 / 40 | 731 / -1195 / -292 / -6 |
| 2024 | 4263 / -11407 / -3539 / 217 | 332 / -917 / -289 / 50 |
| 2025 | 4368 / -10172 / -3904 / 179 | 697 / -1380 / -525 / 45 |

  Own persistence 0.65; controls beaten (30, 27, 30) (L6M drawdown-first / L3M / ulcer-only). Trades: L6M 166 (27.7 a month), L3M 76, 2023 76, 2024 141, 2025 186; 5 best days = 23% of L6M profit, best month 25% (2026-09).

### 2B. OPTION B [POOL 28]: two books, L7c368a4f + La010c3eb (previous final, pool 27; stack set TL3_ALN_AS_STKd89353ef89, _CANF)
- **Book B1 = L7c368a4f:** bar **time_m_5** (5-minute, anchored on the first session print; unaffected bar class, BASE bars). Trigger **trig_pullback_ema depth** (len 10, w 0.5): trend up if EMA10 > EMA20 of the closes, pullback depth >= 0.5 x ATR14(previous bar) from the swing extreme, long when the close exceeds the previous bar's high (short mirrored), EMAs seeded at the series start, ATR Wilder; both sides. Bracket plain60/60, flat at session end. Exact definition and per-bar tables: `D8_TRIGDEBUG_L7c368a4f.md`. NT8: from last ticks alone, yes (time bar from ticks, no other data).
- **Book B2 = La010c3eb:** bar **vol_500 on the _CANC rule** (500 x s_vol contracts; 20261110: 555.51), trigger **trig_trend_libstack ema_stack 10-20-50**: edge into the stack state EMA10 > EMA20 > EMA50 (long) or the reverse (short), on the bar closes, both sides. Instrument ids by real roll (**_CANF**; standalone CANF vs CANC: L6M identical, 2023 $459 vs $447/wk, 2024 $396 vs $414, 2025 $75 vs $90). Bracket plain60/60, flat at session end. Exact definition and tables: `D8_TRIGDEBUG_La010c3eb.md`; bars: `D8_VECTORS_CANC_La010c3eb.md`. NT8: from last/bid/ask ticks alone (volume bar with the D8 print rule, EMAs).
- **Layers/exits kept:** none (account layers only as in the engine stand-in). **Risks:** the two books trade the same session and can overlap (one-position rule per book; the stack rules of the engine run both); results below are the engine's stack set, not a simple sum; controls beaten (27, 16, 29) (the L3M count 16 of 30 is the weakest).
- **Results (stack set, base 1 lot; ulcer / max DD / worst week / $ per week; label: previous final, pool 27; PENDING loop re-run):**

| window | L7c368a4f + La010c3eb | BARE D7 Asia at the same L6M drawdown (x0.36) |
|---|---|---|
| L6M | 4789 / -14639 / -9096 / 3848 | 4789 / -11770 / -7703 / 2062 |
| L3M | 4700 / -14639 / -8658 / 3853 | 4453 / -10181 / -6499 / 1163 |
| 2023 | 2746 / -7215 / -2853 / 660 | 7455 / -12191 / -2979 / -58 |
| 2024 | 7791 / -22530 / -6082 / 1078 | 3392 / -9360 / -2950 / 506 |
| 2025 | 12684 / -28865 / -16300 / 633 | 7110 / -14076 / -5353 / 464 |

  Own persistence 0.68.
- **Third option (information, APPROXIMATE, not a stack run):** the sum of the three landed book-alone series L7c368a4f + La010c3eb + L385f4f2e.J502: L6M 4196 / -11846 / -9409 / 5475, 2024 11566 / -32884 / -8456 / 1267, 2025 16365 / -39840 / -15570 / 783 (own persistence 0.70, no controls run).
- **Why nothing was added to J502 (W-COMBO):** every two-book stack has x4.5 to x8.5 of J502's ulcer and 0.83-1.59 dollars of weekly profit per unit of ulcer against J502's 4.60 (the +1% return-per-ulcer clause fails for all 15 landed candidates; the drawdown guards pass).


### 2C. OPTION C [POOL 28] (asia-stay final of W-COMBO): three books, L7c368a4f + L578701ed + L385f4f2e.J502 (stack set TL3_ALN_AS_STKd88bbb46dc)
- **Books:** C1 = L7c368a4f (as B1: time_m_5 + pullback_ema depth len 10 w 0.5; `D8_TRIGDEBUG_L7c368a4f.md`); C2 = **L578701ed**; C3 = L385f4f2e.J502 (as option A; `D8_TRIGDEBUG_L385f4f2e.md`, `D8_P2_J502_FILTER.md`, `D8_VECTORS_CANC_L385f4f2e.md`). All plain60/60, both sides, flat at session end; layers kept: none; exits kept: none.
- **L578701ed, bar:** **time_m_1** = 1-minute bars (time-bar class, unaffected by the print rule, BASE kept): bucket = floor((print time - first print of the session) / 60 s), the Asia grid starts at 18:00:00 ET = 23:00:00 UTC so boundaries are the clock minutes; a print on a boundary belongs to the new bar; empty minutes give no bar; the bar is KNOWN at the minute boundary exactly (no wait for a next print); the last minute of a session is truncated (part = 1, no signal; stays in the series). The NT8 native 1-minute bar has the same grid on Asia. (tm60, the epoch-aligned 60 s bar of other books, has identical OHLCV but is known at the first print of the next minute.)
- **L578701ed, trigger: trig_book_dwm dev_follow (L 200, z 2.0)** (exact text in `D8_TRIGGER_DEFS.md` 3.12; per-bar inputs and signals in `D8_VECTORS_CANR_L578701ed.md`): at each 1-minute bar close take the last valid 10-level book snapshot at or before the close (engine: 100 ms grid of the exchange book; valid = best bid > 0, best ask > best bid, both best sizes > 0); bw = sum(bid price x bid size) / sum(bid size) over the 10 bid levels, aw likewise over the 10 ask levels; DWM = (bw + aw)/2; **x = DWM - mid in ticks**, mid = (best bid + best ask)/2; z = x / sample std (ddof 1) of x over the last 200 one-minute bars of the continuous series (at least 66); **long when z >= 2.0, short when z <= -2.0**, edge-triggered, follow direction. Event time = floor(bar close second) + 2 s.
- **NT8 computability of L578701ed:** the bars from ticks (yes, trades only). The trigger needs **Level 2 depth, 10 price levels per side with sizes (CQG market depth via OnMarketDepth): YES available per Josh (CQG L2)**; it uses only level prices and aggregate sizes, NO per-order data (so a price-aggregated 10-level feed loses nothing); sampled once per minute at the bar close. **Risks:** (a) the engine samples a 100 ms grid on RECEIVE time, NT8 would sample the live book at the exact minute boundary (fresher by up to 100 ms; effect not measured); (b) CQG's treatment of implied quantities and the delivery of all 10 levels are unverified (needs a recorded sim day compared with the engine's snapshots); (c) 200 one-minute bars (3.3 h) of x history are needed before the first z, crossing sessions (so the depth stream must run from the previous session); (d) crossed or empty-side records must be skipped (use the last valid snapshot); (e) depth is the one input of the whole Asia spec that has not been compared bar by bar with the NT8 feed.
- **Layers/exits kept:** none. **Results (stack set, base 1 lot; ulcer / max DD / worst week / $ per week; W-COMBO ALL_NEW_STACK_ASIA_STAY.md steps 1-3; label: asia-stay final, POOL 28; PENDING loop re-run):**

| window | L7c368a4f (step 1) | + L578701ed (step 2) | + L385f4f2e.J502 = OPTION C (step 3) |
|---|---|---|---|
| L6M | 4075 / -11123 / -7409 / 2456 | 5675 / -14801 / -10059 / 4229 | 4930 / -13326 / -7847 / 6056 |
| L3M | 2028 / -5118 / -3617 / 2434 | 4927 / -10072 / -8937 / 3064 | 6275 / -13326 / -6941 / 4446 |
| 2023 | 4013 / -9990 / -2484 / 203 | 2095 / -5134 / -3277 / 965 | 3347 / -10314 / -6247 / 963 |
| 2024 | 4626 / -11465 / -2843 / 654 | 8225 / -23263 / -4698 / 696 | 7859 / -23992 / -5607 / 1011 |
| 2025 | 5940 / -14312 / -10102 / 528 | 6804 / -20199 / -14470 / 1049 | 7320 / -21203 / -16459 / 1221 |

  Own persistence 0.62 / 0.70 / 0.70 (steps 1 / 2 / 3). Step 2 carries the note "L3M DISAGREES: L3M return per ulcer worse by 48% than the stack before this step (shown, not a gate)". Controls beaten for the three-book stack set: not stated on the W-COMBO page at the time of writing (PENDING). Option C in one line: ulcer 4930 for $6,056 a week in L6M (the highest weekly profit of the three options, between A's 469 and B's 4789 in ulcer), prior years $963 / $1,011 / $1,221 a week; needs depth (L578701ed) and ES/YM (J502).

## 3. Comparison in one line each (PENDING; all POOL 28)
Option A earns more per unit of ulcer and has far smaller drawdowns in L6M/L3M (469 ulcer / $2157 a week) but is thin in 2023-2025 ($40, $217, $179 a week), depends on ES and YM data and on the Fibonacci port; option B has an ulcer ten times larger (4789) for $3848 a week, steadier prior years ($660, $1078, $633) and needs only NQ ticks. Option C (A + B1 + L578701ed) combines J502 with the two time-bar books: L6M $6,056 a week at ulcer 4930, prior years $963 / $1,011 / $1,221, needing NQ ticks + 10-level depth + ES/YM data. Choice is Josh's.

## 4. Open items (what the NT8 port still needs)
1. **ES and YM 1-minute data in NT8 (CQG)** with 72 hours of history, the engine's z-score definitions (J502 c9, c10): without them option A cannot be ported as tested.
2. **Fibonacci / fractal-pivot port** (J502 c2): 15- and 60-minute pivots (strength 2), alternating zig-zag, last-leg retracements 38.2/50/61.8/78.6%, validity 10 days (15 min) / 30 days (60 min); needs 1-minute history of 30 days.
3. **1-minute history for the level conditions:** opens (week/month: up to 31 days), previous RTH close, previous RTH day's volume profile (value-area low, 1-tick bins, 70% two-row expansion), minute closes; the November 2026 month anchor artefact.
4. **Depth for L578701ed (option C):** CQG 10-level market depth recorded on a sim day and compared with the engine's 100 ms snapshots (levels, sizes, implied quantities, validity rules); the 200-bar x history across sessions; sampling at the minute boundary.
5. **Bar builders to verify against the vectors:** vol_2600 (option A), vol_500 (B2), time_m_5 (B1): each bar-by-bar on Josh's ticks first (relay builder reproduced vol_500 115/115, cdr_100 79/79).
6. **Feed-clock differences:** CQG stamps lag the exchange stamps up to 0.26 s (Asia): only minute-boundary line lookups and the 23:00/23:30 ET window can move; implement windows and swing footprints by tick order, not wall-clock, where stated.
7. **History to load before the first Asia bar:** the vol_2600 / vol_500 / time_m_5 series from the start of the previous trading day's Asia session (18:00 ET two days earlier) so that more than 1,000 bars precede the first bar tested (EMA50, ATR14, RSI14 seeds).
8. **Pending numbers:** every results table above is from the landed sets of 09:5xZ; the loop re-run (about 11:00Z) and the final fits (stage 2/3) may change them; this draft is replaced by the frozen v1 when the Asia chain completes.
9. **Enlarged universe:** W-COMBO's four Asia loops are being re-run on the enlarged universe (1,244 _CANC ids, 11:3xZ fix); this draft carries only pool 28; the enlarged-universe finals, their new books (bars, triggers, NT8 computability) and their results tables will be added as a separate block labelled ENLARGED UNIVERSE when W-COMBO posts them.
10. **Not decided here:** which option; lots (live lots formula above); daylight-time handling of the window (follows the New York clock) and of the session end (07:00 UTC in EST, 06:00 UTC in EDT).

## 5. Where the exact definitions are
`D8_PRINT_RULE.md` (print rule, causal variants, bar classes), `D8_BAR_DEFS.md` (bar rules, tm rule, thresholds), `D8_FEED_CHECK.md` (feed alignment), `D8_TRIGDEBUG_*`, `D8_VECTORS_*` (per-book tables), `D8_P2_J502_FILTER.md`, `D8_CANF_COMPARE.md`, `D8_CAN_RESULTS.md`, `ASIA_ONE_BOOK_EXPLAIN.md`.
