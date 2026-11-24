# D8_CARRYOVER: carry-over rule (earlier session lost more than X -> skip / half the later session), 2-lot basis, EXACT rows where landed + emulation for the rest (W-STATUS scorer, 2026-11-24 04:56Z)

Research only. PARTIAL until the XF (fitted-pick) rows land (see status); re-run the scorer (scratchpad/se_xs/run_carry.sh) at the end. Units: per 2 lots per book, net of $4.84 per lot, Globex-day P&L, weekly = Mon-Fri; ulcer = RMS of daily drawdown; ratios = rule / reference (below 1 on risk = better, above 1 on $/wk = better). L6M = 2026-05..10, L3M = 2026-08..10.

## STATUS (landed set-months of the 2-lot carry sets, L6M = 6 months each)

| family | base set | carry sets | set-months landed / needed | base L6M months landed |
|---|---|---|---|---|
| XS | TL3_SR_XS_ASNYLO_BF2_BASE | 32 | 192 / 192 | 6 of 6 |
| XS | TL3_SR_XS_ASNYLONP_BF2_BASE | 16 | 96 / 96 | 6 of 6 |
| XF | TL3_SR_XF_ASNYLO_BF2_BASE__v1 | 32 | 32 / 192 | 6 of 6 |
| XF | TL3_SR_XF_ASNYLONP_BF2_BASE | 16 | 16 / 96 | 6 of 6 |

- XS bare ASNYLO (Asia+NY AM+London, 11 books): COMPLETE (all 32 carry sets x 6 months and the merged BASE x 6 months). Identity of the merged base against the three separate per-session BF2 sets, trade for trade over all 6 months: _SR_XS_ASNYLO_BF2_BASE 4147 trades vs 4147, max daily difference $0.00.
- XF fitted-pick ASNYLO: only part landed (rows above); the identity of its merged base vs the separate picks (JT19 + JT68 + London bare) is exact on 202605,202606,202607,202608,202609,202610 (4171 trades both). Scored below by EMULATION on the separate pick trades, with the landed exact rows as a check (they fire on 0 of the landed days, as the emulation says).
- NY AM -> NY PM (NYNP): bare 15-book set scored exactly in section 1c when its merged base is complete (landed 04:54Z); prior years and the emulation do NOT exist for it (the separate NY PM BF2S sets exist only for 202610).
- NYNP and the ANY row of section 1c use the 15-book NP set; its NP books have no prior-year base rows, so no prior years / emulation for them.
- Prior years: no exact prior-year carry row exists. Prior years below are EMULATED (method below), validated on L6M against the exact rows.
- Null: emulated best-of-32 sign-flip (below), not a random-entry null; the random-entry null needs engine rows (not queued; count: 32 sets x 6 months x 5 random streams ~ 960 rows per base; tell me if wanted).

## EXACT ENGINE DEFINITION (code/th_xsess/xs_hooks.py, carry key)
- Governed books = every book of the merged set (tags MF1-5 Asia, MF6-10 NY AM, MF11 London, MF12-15 NY PM). Session order AS < LO < NY < NP (London is BEFORE NY AM; NY PM is last).
- DAY = the Globex trading day (the engine session key: from 18:00 ET the date rolls to the next day; day P&L rebased at that roll; so the Asia evening of Sunday-Thursday belongs to the next calendar day, together with London and NY AM).
- Evaluated at each ENTRY of a governed book of a later session (the no-trade-set check, ntz_check): prior = SUM over governed books of the EARLIER sessions (and, if "from" is set, only those named) of (day_pnl + open P&L marked at the last 1-minute close for a book still in a trade). day_pnl is the engine realized P&L of the Globex day (after the engine fee; the emulation with the engine-fee-net trade P&L fires on the same days within 1).
- "Lost more than X": fires when prior < -X x L where L = lots per book (base_qty = 2 here), so X is in dollars per lot-per-book and the dollar trigger at 2 lots is 2 x X (X = 6000 means the earlier sessions together are down more than $12,000 on the day). It is a combined dollar loss across ALL books of the earlier session(s), not a per-book or R measure.
- Action: skip = that entry is refused (action Skip, as a no-trade-set block); half = lots = max(1, floor(lots x 0.5 + 0.5)), i.e. 2 lots -> 1 lot (inert at 1 lot). Trades already open and entries of the earlier sessions are untouched.
- When the skip lifts: it is not a latch. The condition is re-read at every later-session entry; with the earlier sessions flat (Asia flattens 02:00 ET, London 08:30 ET) the number is fixed for the rest of that Globex day, so the skip holds for the whole later session(s) of that day and lifts at the 18:00 ET day roll (the next session starts at a fresh day P&L of 0). In particular the NY AM skip does NOT carry into NY PM unless the pair is ANY/NYNP.
- Pairs in the tests: ASNY = from Asia, only NY AM entries governed (London not measured, London entries not governed); ASLO = from Asia to London; LONY = from London to NY AM; NYNP = from NY AM to NY PM; ANY = every earlier session measured, every later session governed (NY AM sees Asia + London; NY PM sees Asia + London + NY AM; London sees Asia).

## METHOD NOTES
- Exact rows = the engine with the hook (xs_hooks.py) on the merged set. Base for the exact comparison = the merged BASE set where all its months landed (XS ASNYLO: yes), else the identity-proven sum of the separate per-session sets.
- Emulation (for prior years, thresholds off the grid, the fitted pick and the null): for every trade of a later session, prior = sum of net P&L of earlier-session trades of the same Globex day already closed at that entry; skip removes the trade, half halves its P&L. It ignores open P&L at entry and knock-on effects (a skipped entry re-opens the book for a later signal; day-level rules that depend on the skipped trade). Validated on the XS L6M exact rows: fired days equal or within 1-2 of exact in every pair tested (e.g. ASNY 3000 skip 16 vs 17; ASLO 3000 skip 14 vs 14 with the same $5,710; LONY 3000 skip 1 vs 1, same $5,273); the largest single-day gap is $5,962 (ASNY 6000, one day) and for ANY 6000 half 4 vs 3 fired days. Total L6M effect: ASNY 3000 skip -$43k emulated vs -$42k exact, ASNY 6000 skip +$13.6k vs +$11.0k.
- Walk-forward: the setting is FIXED (no refit); a block is a 14-day calendar block; win = lower block max drawdown (dollars on ties); "same" = block untouched by the rule. Gate >= 0.58 of the blocks the rule changed (win / (win + lose)); with a rule that fires 2-20 days in 3.5 years most blocks are "same", so I give win/lose/same.

## 1. BARE BASE (XS), 2 lots: EXACT L6M + emulated prior years (rows with no fire in L6M or history are omitted)

Base = TL3_SR_XS_ASNYLO_BF2_BASE; reference row = the same set with the rules off, same months. Base L6M (exact): $/wk / ulcer / max DD / worst week / worst day = 37,882/9,177/-38,898/-12,520/-23,091 (months 202605,202606,202607,202608,202609,202610)

| pair | act | X ($ per lot-per-book; $ at 2 lots = 2X) | months | days fired L6M exact / 3.5y emulated | ulcer x | max DD x | $/wk x | worst wk x | worst day x | L3M ulcer x / $/wk x | days that would have recovered: n, cost $ | days saved: n, $ | prior yrs 2023 / 2024 / 2025 emulated: ulcer x, $/wk x | blocks L6M win/lose/same | blocks 3.5y emu win/lose/same |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia -> NY AM | skip | 3000 | 6 | 17 / 74 | 0.87 | 0.76 | 0.959 | 0.84 | 0.73 | 0.80 / 0.96 | 11, -65,366 | 6, 23,397 | 1.04, 0.92 / 0.88, 0.92 / 0.88, 0.96 | 4/7/3 | 21/24/48 |
| Asia -> NY AM | half | 3000 | 6 | 17 / 74 | 0.92 | 0.88 | 0.980 | 0.92 | 0.84 | 0.89 / 0.98 | 11, -32,628 | 6, 11,793 | 1.02, 0.96 / 0.88, 0.96 / 0.94, 0.98 | 4/7/3 | 21/24/48 |
| Asia -> NY AM | skip | 4000 | 6 | 11 / 48 | 0.87 | 0.76 | 0.968 | 0.84 | 0.73 | 0.79 / 0.98 | 7, -52,014 | 4, 19,241 | 1.04, 0.91 / 1.02, 0.95 / 0.79, 1.01 | 4/6/4 | 16/17/60 |
| Asia -> NY AM | half | 4000 | 6 | 11 / 48 | 0.92 | 0.88 | 0.984 | 0.92 | 0.84 | 0.88 / 0.99 | 7, -25,962 | 4, 9,676 | 1.02, 0.96 / 0.97, 0.97 / 0.89, 1.00 | 4/6/4 | 16/17/60 |
| Asia -> NY AM | skip | 5000 | 6 | 7 / 26 | 0.86 | 0.76 | 0.979 | 1.00 | 0.73 | 0.79 / 0.98 | 5, -38,758 | 2, 16,963 | 1.00, 1.00 / 0.90, 0.98 / 0.73, 1.02 | 2/5/7 | 10/13/70 |
| Asia -> NY AM | half | 5000 | 6 | 7 / 26 | 0.92 | 0.88 | 0.989 | 1.00 | 0.84 | 0.88 / 0.99 | 5, -19,349 | 2, 8,516 | 1.00, 1.00 / 0.92, 0.99 / 0.86, 1.01 | 2/5/7 | 10/13/70 |
| Asia -> NY AM | skip | 6000 | 6 | 3 / 14 | 0.82 | 0.76 | 1.011 | 1.00 | 0.73 | 0.74 / 1.02 | 1, -5,962 | 2, 16,963 | 1.00, 1.00 / 0.96, 0.99 / 0.81, 1.04 | 2/1/11 | 8/5/80 |
| Asia -> NY AM | half | 6000 | 6 | 3 / 14 | 0.90 | 0.88 | 1.005 | 1.00 | 0.84 | 0.87 / 1.01 | 1, -2,996 | 2, 8,516 | 1.00, 1.00 / 0.95, 0.99 / 0.90, 1.02 | 2/1/11 | 8/5/80 |
| Asia -> London | skip | 3000 | 6 | 14 / 56 | 0.99 | 1.00 | 1.006 | 1.00 | 0.98 | 1.00 / 1.00 | 6, -10,029 | 8, 15,739 | 1.00, 0.99 / 1.07, 0.97 / 0.99, 0.99 | 6/3/5 | 15/26/52 |
| Asia -> London | half | 3000 | 6 | 14 / 56 | 0.99 | 1.00 | 1.005 | 1.00 | 0.98 | 1.00 / 1.01 | 6, -5,007 | 8, 10,247 | 1.00, 0.99 / 1.03, 0.99 / 0.99, 0.99 | 6/3/5 | 15/26/52 |
| Asia -> London | skip | 4000 | 6 | 9 / 39 | 0.99 | 1.00 | 1.002 | 1.00 | 0.98 | 1.00 / 1.00 | 5, -6,463 | 4, 8,946 | 1.00, 0.99 / 1.05, 0.98 / 0.98, 0.99 | 4/4/6 | 11/18/64 |
| Asia -> London | half | 4000 | 6 | 9 / 39 | 0.99 | 1.00 | 1.001 | 1.00 | 0.98 | 1.00 / 1.00 | 5, -3,227 | 4, 4,488 | 1.00, 1.00 / 1.03, 0.99 / 0.99, 1.00 | 4/4/6 | 11/18/64 |
| Asia -> London | skip | 5000 | 6 | 6 / 22 | 0.99 | 1.00 | 1.004 | 1.00 | 0.98 | 1.00 / 1.00 | 3, -3,542 | 3, 7,767 | 1.00, 1.00 / 1.02, 0.99 / 0.98, 1.00 | 3/3/8 | 8/12/73 |
| Asia -> London | half | 5000 | 6 | 6 / 22 | 0.99 | 1.00 | 1.002 | 1.00 | 0.98 | 1.00 / 1.00 | 3, -1,766 | 3, 3,899 | 1.00, 1.00 / 1.01, 1.00 / 0.99, 1.00 | 3/3/8 | 8/12/73 |
| Asia -> London | skip | 6000 | 6 | 2 / 12 | 0.99 | 1.00 | 1.006 | 1.00 | 0.98 | 1.00 / 1.00 | 0, 0 | 2, 6,603 | 1.00, 1.00 / 1.01, 1.00 / 0.99, 1.01 | 2/0/12 | 5/6/82 |
| Asia -> London | half | 6000 | 6 | 2 / 12 | 0.99 | 1.00 | 1.003 | 1.00 | 0.98 | 1.00 / 1.00 | 0, 0 | 2, 3,314 | 1.00, 1.00 / 1.00, 1.00 / 1.00, 1.00 | 2/0/12 | 5/6/82 |
| London -> NY AM | skip | 3000 | 6 | 1 / 6 | 1.00 | 1.00 | 1.005 | 1.00 | 1.00 | 0.99 / 1.01 | 0, 0 | 1, 5,273 | 1.00, 1.00 / 1.00, 0.99 / 1.04, 0.98 | 1/0/13 | 3/3/87 |
| London -> NY AM | half | 3000 | 6 | 1 / 6 | 1.00 | 1.00 | 1.003 | 1.00 | 1.00 | 1.00 / 1.01 | 0, 0 | 1, 2,639 | 1.00, 1.00 / 1.00, 1.00 / 1.02, 0.99 | 1/0/13 | 3/3/87 |
| London -> NY AM | skip | 4000 | 6 | 0 / 2 | 1.00 | 1.00 | 1.000 | 1.00 | 1.00 | 1.00 / 1.00 | 0, 0 | 0, 0 | 1.00, 1.00 / 1.00, 0.99 / 1.00, 1.00 | 0/0/14 | 1/1/91 |
| London -> NY AM | half | 4000 | 6 | 0 / 2 | 1.00 | 1.00 | 1.000 | 1.00 | 1.00 | 1.00 / 1.00 | 0, 0 | 0, 0 | 1.00, 1.00 / 1.00, 1.00 / 1.00, 1.00 | 0/0/14 | 1/1/91 |
| any earlier session -> each later session | skip | 3000 | 6 | 18 / 86 | 0.87 | 0.76 | 0.955 | 0.84 | 0.73 | 0.81 / 0.97 | 12, -76,015 | 6, 29,517 | 1.05, 0.90 / 0.92, 0.93 / 1.07, 0.82 | 4/7/3 | 19/30/44 |
| any earlier session -> each later session | half | 3000 | 6 | 18 / 86 | 0.91 | 0.88 | 0.980 | 0.92 | 0.78 | 0.88 / 0.99 | 12, -37,324 | 6, 17,224 | 1.02, 0.95 / 0.90, 0.97 / 0.99, 0.91 | 4/7/3 | 20/29/44 |
| any earlier session -> each later session | skip | 4000 | 6 | 12 / 53 | 0.86 | 0.76 | 0.969 | 0.84 | 0.73 | 0.80 / 0.97 | 9, -53,407 | 3, 21,760 | 1.03, 0.96 / 0.98, 0.94 / 0.89, 0.97 | 3/8/3 | 13/22/58 |
| any earlier session -> each later session | half | 4000 | 6 | 12 / 53 | 0.91 | 0.88 | 0.988 | 0.92 | 0.78 | 0.89 / 0.99 | 9, -23,587 | 3, 10,932 | 1.01, 0.98 / 0.96, 0.97 / 0.94, 0.98 | 3/8/3 | 13/22/58 |
| any earlier session -> each later session | skip | 5000 | 6 | 9 / 33 | 0.87 | 0.76 | 0.975 | 1.00 | 0.73 | 0.80 / 0.97 | 7, -45,876 | 2, 19,797 | 1.00, 1.00 / 0.99, 0.96 / 0.72, 1.00 | 2/7/5 | 8/17/68 |
| any earlier session -> each later session | half | 5000 | 6 | 9 / 33 | 0.91 | 0.88 | 0.995 | 1.00 | 0.78 | 0.88 / 0.99 | 7, -14,685 | 2, 9,941 | 1.00, 1.00 / 0.96, 0.98 / 0.85, 1.00 | 2/7/5 | 8/17/68 |
| any earlier session -> each later session | skip | 6000 | 6 | 3 / 18 | 0.81 | 0.76 | 1.017 | 1.00 | 0.73 | 0.74 / 1.02 | 1, -2,193 | 2, 19,797 | 1.00, 1.00 / 0.97, 0.99 / 0.71, 1.05 | 2/1/11 | 7/9/77 |
| any earlier session -> each later session | half | 6000 | 6 | 3 / 18 | 0.90 | 0.88 | 1.009 | 1.00 | 0.78 | 0.87 / 1.01 | 1, -1,106 | 2, 9,941 | 1.00, 1.00 / 0.95, 0.99 / 0.85, 1.02 | 2/1/11 | 7/9/77 |

### 1b. BARE BASE: all thresholds incl. emulation-only (2000, 2500, 7000, 8000), EMULATED all 42 months

EMULATED on the separate per-session exact trade lists (rule applied to trades; see method), base L6M $/wk/ulcer/max DD/worst wk/worst day = 37,882/9,177/-38,898/-12,520/-23,091; base prior-year $/wk 2023 6,476, 2024 8,598, 2025 10,791, 2026 Jan-Apr 4,133.

| pair | act | X | fired days L6M / all 42 months | L6M ulcer x / max DD x / $/wk x | L3M ulcer x / $/wk x | 2023 ulcer x, $/wk x | 2024 | 2025 | 2026 Jan-Apr | ALL ulcer x / $/wk x | blocks win/lose/same (14-day, 42 months) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia -> NY AM | skip | 2000 (emu-only) | 23 / 123 | 0.92 / 0.71 / 0.909 | 0.77 / 0.939 | 1.04, 0.91 | 0.85, 0.99 | 1.08, 0.94 | 0.56, 1.78 | 0.83 / 0.959 | 35/29/29 |
| Asia -> NY AM | half | 2000 (emu-only) | 23 / 122 | 0.93 / 0.86 / 0.955 | 0.87 / 0.970 | 1.02, 0.96 | 0.86, 0.99 | 0.99, 0.97 | 0.77, 1.39 | 0.88 / 0.979 | 37/27/29 |
| Asia -> NY AM | skip | 2500 (emu-only) | 17 / 92 | 0.88 / 0.76 / 0.939 | 0.80 / 0.965 | 1.04, 0.92 | 0.89, 0.93 | 0.87, 1.00 | 0.54, 1.83 | 0.75 / 0.977 | 29/25/39 |
| Asia -> NY AM | half | 2500 (emu-only) | 17 / 92 | 0.92 / 0.88 / 0.970 | 0.89 / 0.982 | 1.02, 0.96 | 0.88, 0.96 | 0.93, 1.00 | 0.77, 1.41 | 0.86 / 0.988 | 29/25/39 |
| Asia -> NY AM | skip | 3000 | 16 / 74 | 0.87 / 0.76 / 0.958 | 0.80 / 0.965 | 1.04, 0.92 | 0.88, 0.92 | 0.88, 0.96 | 0.60, 1.48 | 0.77 / 0.963 | 21/24/48 |
| Asia -> NY AM | half | 3000 | 16 / 74 | 0.92 / 0.88 / 0.979 | 0.89 / 0.982 | 1.02, 0.96 | 0.88, 0.96 | 0.94, 0.98 | 0.79, 1.24 | 0.87 / 0.981 | 21/24/48 |
| Asia -> NY AM | skip | 4000 | 11 / 48 | 0.87 / 0.76 / 0.968 | 0.79 / 0.977 | 1.04, 0.91 | 1.02, 0.95 | 0.79, 1.01 | 0.76, 1.27 | 0.83 / 0.977 | 16/17/60 |
| Asia -> NY AM | half | 4000 | 11 / 48 | 0.92 / 0.88 / 0.984 | 0.88 / 0.989 | 1.02, 0.96 | 0.97, 0.97 | 0.89, 1.00 | 0.88, 1.13 | 0.91 / 0.988 | 16/17/60 |
| Asia -> NY AM | skip | 5000 | 7 / 26 | 0.86 / 0.76 / 0.979 | 0.79 / 0.977 | 1.00, 1.00 | 0.90, 0.98 | 0.73, 1.02 | 0.91, 1.06 | 0.86 / 0.993 | 10/13/70 |
| Asia -> NY AM | half | 5000 | 7 / 26 | 0.92 / 0.88 / 0.989 | 0.88 / 0.989 | 1.00, 1.00 | 0.92, 0.99 | 0.86, 1.01 | 0.95, 1.03 | 0.92 / 0.997 | 10/13/70 |
| Asia -> NY AM | skip | 6000 | 3 / 14 | 0.82 / 0.76 / 1.013 | 0.76 / 1.013 | 1.00, 1.00 | 0.96, 0.99 | 0.81, 1.04 | 0.84, 1.18 | 0.86 / 1.018 | 8/5/80 |
| Asia -> NY AM | half | 6000 | 3 / 14 | 0.91 / 0.88 / 1.007 | 0.87 / 1.007 | 1.00, 1.00 | 0.95, 0.99 | 0.90, 1.02 | 0.92, 1.09 | 0.92 / 1.009 | 8/5/80 |
| Asia -> NY AM | skip | 7000 (emu-only) | 0 / 9 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 0.96, 0.99 | 0.80, 1.02 | 0.84, 1.18 | 0.86 / 1.008 | 5/4/84 |
| Asia -> NY AM | half | 7000 (emu-only) | 0 / 9 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 0.95, 0.99 | 0.89, 1.01 | 0.92, 1.09 | 0.92 / 1.004 | 5/4/84 |
| Asia -> NY AM | skip | 8000 (emu-only) | 0 / 6 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 0.89, 1.02 | 1.01, 0.97 | 0.84, 1.18 | 0.91 / 1.004 | 4/2/87 |
| Asia -> NY AM | half | 8000 (emu-only) | 0 / 6 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 0.92, 1.01 | 1.00, 0.99 | 0.92, 1.09 | 0.95 / 1.002 | 4/2/87 |
| Asia -> London | skip | 2000 (emu-only) | 20 / 96 | 1.02 / 1.03 / 0.992 | 1.03 / 0.982 | 1.00, 0.99 | 1.08, 0.97 | 0.95, 1.00 | 0.99, 0.96 | 1.00 / 0.988 | 24/35/34 |
| Asia -> London | half | 2000 (emu-only) | 20 / 96 | 1.01 / 1.02 / 0.996 | 1.02 / 0.991 | 1.00, 1.00 | 1.04, 0.98 | 0.97, 1.00 | 1.00, 0.98 | 1.00 / 0.994 | 24/35/34 |
| Asia -> London | skip | 2500 (emu-only) | 15 / 72 | 0.99 / 1.00 / 1.004 | 1.00 / 1.002 | 1.00, 0.99 | 1.07, 0.97 | 0.98, 0.99 | 0.99, 1.00 | 1.00 / 0.992 | 19/31/43 |
| Asia -> London | half | 2500 (emu-only) | 15 / 72 | 0.99 / 1.00 / 1.002 | 1.00 / 1.001 | 1.00, 0.99 | 1.03, 0.99 | 0.99, 0.99 | 1.00, 1.00 | 1.00 / 0.996 | 19/31/43 |
| Asia -> London | skip | 3000 | 14 / 56 | 0.99 / 1.00 / 1.006 | 1.00 / 1.002 | 1.00, 0.99 | 1.07, 0.97 | 0.99, 0.99 | 0.97, 1.10 | 0.99 / 0.997 | 15/26/52 |
| Asia -> London | half | 3000 | 14 / 56 | 0.99 / 1.00 / 1.003 | 1.00 / 1.001 | 1.00, 0.99 | 1.03, 0.99 | 0.99, 0.99 | 0.98, 1.05 | 1.00 / 0.998 | 15/26/52 |
| Asia -> London | skip | 4000 | 9 / 39 | 0.99 / 1.00 / 1.002 | 1.00 / 0.997 | 1.00, 0.99 | 1.05, 0.98 | 0.98, 0.99 | 0.95, 1.09 | 0.98 / 0.998 | 11/18/64 |
| Asia -> London | half | 4000 | 9 / 39 | 1.00 / 1.00 / 1.001 | 1.00 / 0.999 | 1.00, 1.00 | 1.03, 0.99 | 0.99, 1.00 | 0.98, 1.05 | 0.99 / 0.999 | 11/18/64 |
| Asia -> London | skip | 5000 | 6 / 22 | 0.99 / 1.00 / 1.004 | 1.00 / 0.997 | 1.00, 1.00 | 1.02, 0.99 | 0.98, 1.00 | 1.00, 1.02 | 1.00 / 1.000 | 8/12/73 |
| Asia -> London | half | 5000 | 6 / 22 | 1.00 / 1.00 / 1.002 | 1.00 / 0.999 | 1.00, 1.00 | 1.01, 1.00 | 0.99, 1.00 | 1.00, 1.01 | 1.00 / 1.000 | 8/12/73 |
| Asia -> London | skip | 6000 | 2 / 12 | 0.99 / 1.00 / 1.004 | 1.00 / 1.003 | 1.00, 1.00 | 1.01, 1.00 | 0.99, 1.01 | 1.00, 1.02 | 1.00 / 1.003 | 5/6/82 |
| Asia -> London | half | 6000 | 2 / 12 | 0.99 / 1.00 / 1.002 | 1.00 / 1.001 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.01 | 1.00 / 1.001 | 5/6/82 |
| Asia -> London | skip | 7000 (emu-only) | 0 / 8 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.01, 1.00 | 1.01, 1.01 | 1.00, 1.02 | 1.00 / 1.001 | 2/6/85 |
| Asia -> London | half | 7000 (emu-only) | 0 / 8 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.01 | 1.00 / 1.001 | 2/6/85 |
| Asia -> London | skip | 8000 (emu-only) | 0 / 5 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.01 | 1.00, 1.02 | 1.00 / 1.003 | 2/3/88 |
| Asia -> London | half | 8000 (emu-only) | 0 / 5 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.01 | 1.00, 1.01 | 1.00 / 1.002 | 2/3/88 |
| London -> NY AM | skip | 2000 (emu-only) | 4 / 18 | 1.00 / 1.00 / 0.996 | 1.00 / 1.010 | 1.00, 1.00 | 1.01, 0.90 | 1.11, 0.89 | 0.88, 1.10 | 0.98 / 0.957 | 5/9/79 |
| London -> NY AM | half | 2000 (emu-only) | 4 / 18 | 1.00 / 1.00 / 0.998 | 1.00 / 1.005 | 1.00, 1.00 | 1.00, 0.95 | 1.05, 0.94 | 0.93, 1.05 | 0.98 / 0.978 | 5/9/79 |
| London -> NY AM | skip | 2500 (emu-only) | 2 / 10 | 1.00 / 1.00 / 0.997 | 0.99 / 1.011 | 1.00, 1.00 | 1.00, 0.98 | 1.05, 0.95 | 0.93, 1.01 | 0.98 / 0.984 | 3/6/84 |
| London -> NY AM | half | 2500 (emu-only) | 2 / 10 | 1.00 / 1.00 / 0.999 | 1.00 / 1.006 | 1.00, 1.00 | 1.00, 0.99 | 1.03, 0.98 | 0.96, 1.01 | 0.99 / 0.992 | 3/6/84 |
| London -> NY AM | skip | 3000 | 1 / 6 | 1.00 / 1.00 / 1.005 | 0.99 / 1.011 | 1.00, 1.00 | 1.00, 0.99 | 1.04, 0.98 | 0.93, 1.01 | 0.98 / 0.996 | 3/3/87 |
| London -> NY AM | half | 3000 | 1 / 6 | 1.00 / 1.00 / 1.003 | 1.00 / 1.006 | 1.00, 1.00 | 1.00, 1.00 | 1.02, 0.99 | 0.96, 1.01 | 0.99 / 0.998 | 3/3/87 |
| London -> NY AM | skip | 4000 | 0 / 2 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 0.99 | 1.00, 1.00 | 1.00, 1.02 | 1.00 / 0.999 | 1/1/91 |
| London -> NY AM | half | 4000 | 0 / 2 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.01 | 1.00 / 0.999 | 1/1/91 |
| any earlier session -> each later session | skip | 2000 (emu-only) | 25 / 140 | 0.88 / 0.77 / 0.943 | 0.82 / 0.950 | 1.08, 0.93 | 0.94, 0.92 | 1.10, 0.68 | 0.66, 1.03 | 0.89 / 0.881 | 31/37/25 |
| any earlier session -> each later session | half | 2000 (emu-only) | 25 / 139 | 0.92 / 0.89 / 0.971 | 0.89 / 0.975 | 1.03, 0.96 | 0.91, 0.96 | 0.95, 0.84 | 0.82, 1.02 | 0.89 / 0.941 | 32/36/25 |
| any earlier session -> each later session | skip | 2500 (emu-only) | 18 / 107 | 0.87 / 0.76 / 0.953 | 0.81 / 0.970 | 1.03, 0.93 | 0.95, 0.90 | 1.25, 0.62 | 0.64, 1.09 | 0.95 / 0.869 | 22/35/36 |
| any earlier session -> each later session | half | 2500 (emu-only) | 18 / 107 | 0.91 / 0.88 / 0.976 | 0.89 / 0.985 | 1.01, 0.97 | 0.91, 0.95 | 1.00, 0.81 | 0.81, 1.04 | 0.90 / 0.935 | 23/34/36 |
| any earlier session -> each later session | skip | 3000 | 17 / 86 | 0.87 / 0.76 / 0.954 | 0.81 / 0.970 | 1.05, 0.90 | 0.92, 0.93 | 1.07, 0.82 | 0.56, 1.57 | 0.84 / 0.933 | 19/30/44 |
| any earlier session -> each later session | half | 3000 | 17 / 86 | 0.91 / 0.88 / 0.977 | 0.89 / 0.985 | 1.02, 0.95 | 0.90, 0.97 | 0.99, 0.91 | 0.78, 1.29 | 0.88 / 0.967 | 20/29/44 |
| any earlier session -> each later session | skip | 4000 | 12 / 53 | 0.86 / 0.76 / 0.975 | 0.80 / 0.972 | 1.03, 0.96 | 0.98, 0.94 | 0.89, 0.97 | 0.70, 1.32 | 0.83 / 0.975 | 13/22/58 |
| any earlier session -> each later session | half | 4000 | 12 / 53 | 0.91 / 0.88 / 0.988 | 0.89 / 0.986 | 1.01, 0.98 | 0.96, 0.97 | 0.94, 0.98 | 0.85, 1.16 | 0.90 / 0.987 | 13/22/58 |
| any earlier session -> each later session | skip | 5000 | 9 / 33 | 0.85 / 0.76 / 0.991 | 0.77 / 0.980 | 1.00, 1.00 | 0.99, 0.96 | 0.72, 1.00 | 0.84, 1.09 | 0.84 / 0.993 | 8/17/68 |
| any earlier session -> each later session | half | 5000 | 9 / 33 | 0.91 / 0.88 / 0.995 | 0.88 / 0.990 | 1.00, 1.00 | 0.96, 0.98 | 0.85, 1.00 | 0.92, 1.05 | 0.91 / 0.996 | 8/17/68 |
| any earlier session -> each later session | skip | 6000 | 4 / 18 | 0.82 / 0.76 / 1.011 | 0.75 / 1.016 | 1.00, 1.00 | 0.97, 0.99 | 0.71, 1.05 | 0.78, 1.21 | 0.80 / 1.019 | 7/9/77 |
| any earlier session -> each later session | half | 6000 | 4 / 18 | 0.90 / 0.88 / 1.006 | 0.87 / 1.008 | 1.00, 1.00 | 0.95, 0.99 | 0.85, 1.02 | 0.88, 1.10 | 0.89 / 1.010 | 7/9/77 |
| any earlier session -> each later session | skip | 7000 (emu-only) | 3 / 14 | 1.00 / 1.00 / 0.998 | 1.01 / 0.993 | 1.00, 1.00 | 0.90, 1.02 | 1.04, 0.96 | 0.77, 1.29 | 0.90 / 1.004 | 4/8/81 |
| any earlier session -> each later session | half | 7000 (emu-only) | 3 / 14 | 1.00 / 1.00 / 0.999 | 1.01 / 0.996 | 1.00, 1.00 | 0.92, 1.01 | 1.02, 0.98 | 0.88, 1.15 | 0.94 / 1.002 | 4/8/81 |
| any earlier session -> each later session | skip | 8000 (emu-only) | 0 / 7 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 0.89, 1.02 | 1.00, 0.98 | 0.77, 1.43 | 0.88 / 1.014 | 3/3/87 |
| any earlier session -> each later session | half | 8000 (emu-only) | 0 / 7 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 0.92, 1.01 | 1.00, 0.99 | 0.88, 1.21 | 0.93 / 1.007 | 3/3/87 |

### 1c. NY AM -> NY PM (NYNP), bare 15-book set, EXACT L6M

Base = TL3_SR_XS_ASNYLONP_BF2_BASE (merged BASE rows, merged BASE); reference = same set, rules off, same months. Base L6M: $/wk / ulcer / max DD / worst week / worst day = 46,618/8,389/-37,484/-8,049/-22,329

| pair | act | X | months | days fired L6M | ulcer x | max DD x | $/wk x | worst wk x | worst day x | L3M ulcer x / $/wk x | recovered-day cost n, $ | saved n, $ | blocks win/lose/same | prior years |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NY AM -> NY PM | skip | 3000 | 6 | 20 | 1.15 | 1.01 | 0.930 | 2.93 | 1.03 | 1.02 / 0.97 | 16, -98,821 | 4, 10,998 | 3/7/4 | not available (no NP prior-year base) |
| NY AM -> NY PM | half | 3000 | 6 | 20 | 1.05 | 1.01 | 0.966 | 1.92 | 1.01 | 1.01 / 0.98 | 16, -48,786 | 4, 5,499 | 3/7/4 | not available (no NP prior-year base) |
| NY AM -> NY PM | skip | 4000 | 6 | 16 | 1.12 | 1.01 | 0.943 | 2.93 | 1.02 | 1.02 / 0.98 | 12, -82,662 | 4, 10,998 | 3/6/5 | not available (no NP prior-year base) |
| NY AM -> NY PM | half | 4000 | 6 | 16 | 1.04 | 1.01 | 0.972 | 1.92 | 1.01 | 1.01 / 0.99 | 12, -40,734 | 4, 5,499 | 3/6/5 | not available (no NP prior-year base) |
| NY AM -> NY PM | skip | 5000 | 6 | 8 | 1.03 | 1.00 | 0.981 | 1.00 | 1.00 | 1.00 / 0.98 | 5, -34,393 | 3, 10,217 | 3/3/8 | not available (no NP prior-year base) |
| NY AM -> NY PM | half | 5000 | 6 | 8 | 1.01 | 1.00 | 0.990 | 1.00 | 1.00 | 1.00 / 0.99 | 5, -17,234 | 3, 5,106 | 3/3/8 | not available (no NP prior-year base) |
| NY AM -> NY PM | skip | 6000 | 6 | 5 | 1.03 | 1.00 | 0.989 | 1.00 | 1.00 | 1.00 / 1.00 | 3, -21,749 | 2, 8,024 | 2/2/10 | not available (no NP prior-year base) |
| NY AM -> NY PM | half | 6000 | 6 | 5 | 1.01 | 1.00 | 0.995 | 1.00 | 1.00 | 1.00 / 1.00 | 3, -10,917 | 2, 4,002 | 2/2/10 | not available (no NP prior-year base) |
| any earlier session -> each later session | skip | 3000 | 6 | 29 | 1.10 | 0.83 | 0.876 | 3.75 | 0.88 | 0.86 / 0.92 | 21, -182,472 | 8, 27,024 | 3/9/2 | not available (no NP prior-year base) |
| any earlier session -> each later session | half | 3000 | 6 | 29 | 0.99 | 0.88 | 0.949 | 2.32 | 0.88 | 0.89 / 0.97 | 21, -80,710 | 8, 16,045 | 5/7/2 | not available (no NP prior-year base) |
| any earlier session -> each later session | skip | 4000 | 6 | 21 | 1.08 | 0.83 | 0.914 | 3.75 | 0.88 | 0.85 / 0.95 | 14, -128,350 | 7, 20,709 | 4/8/2 | not available (no NP prior-year base) |
| any earlier session -> each later session | half | 4000 | 6 | 21 | 1.00 | 0.88 | 0.960 | 2.32 | 0.88 | 0.90 / 0.98 | 15, -59,380 | 6, 8,856 | 3/9/2 | not available (no NP prior-year base) |
| any earlier session -> each later session | skip | 5000 | 6 | 14 | 1.00 | 0.84 | 0.943 | 1.97 | 0.88 | 0.85 / 0.95 | 9, -88,397 | 5, 16,994 | 3/8/3 | not available (no NP prior-year base) |
| any earlier session -> each later session | half | 5000 | 6 | 14 | 0.97 | 0.88 | 0.980 | 1.44 | 0.88 | 0.88 / 0.99 | 10, -32,711 | 4, 7,568 | 2/9/3 | not available (no NP prior-year base) |
| any earlier session -> each later session | skip | 6000 | 6 | 5 | 0.87 | 0.76 | 0.989 | 1.00 | 0.88 | 0.74 / 1.02 | 3, -24,996 | 2, 11,574 | 2/3/9 | not available (no NP prior-year base) |
| any earlier session -> each later session | half | 6000 | 6 | 5 | 0.92 | 0.88 | 0.995 | 1.00 | 0.88 | 0.87 / 1.01 | 3, -12,508 | 2, 5,837 | 2/3/9 | not available (no NP prior-year base) |

## 2. FITTED-PICK BASE (XF = Asia JT19 + NY AM JT68 + London bare, as D8 delivers), 2 lots

Exact XF rows landed: 32 of 192 (202608); in the months landed every rule fires on 0 days, matching the emulation for those months. Emulated all 42 months below.

EMULATED on the separate per-session exact trade lists (rule applied to trades; see method), base L6M $/wk/ulcer/max DD/worst wk/worst day = 19,190/3,766/-13,321/-106/-10,013; base prior-year $/wk 2023 2,593, 2024 4,728, 2025 4,227, 2026 Jan-Apr 1,197.

| pair | act | X | fired days L6M / all 42 months | L6M ulcer x / max DD x / $/wk x | L3M ulcer x / $/wk x | 2023 ulcer x, $/wk x | 2024 | 2025 | 2026 Jan-Apr | ALL ulcer x / $/wk x | blocks win/lose/same (14-day, 42 months) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia -> NY AM | skip | 2000 (emu-only) | 9 / 56 | 1.22 / 1.22 / 0.973 | 1.03 / 0.984 | 1.05, 0.90 | 1.05, 0.93 | 0.99, 0.93 | 0.65, 2.25 | 0.89 / 0.973 | 17/20/56 |
| Asia -> NY AM | half | 2000 (emu-only) | 9 / 56 | 1.08 / 1.00 / 0.987 | 1.01 / 0.992 | 1.02, 0.95 | 1.01, 0.96 | 0.96, 0.97 | 0.81, 1.63 | 0.92 / 0.987 | 17/20/56 |
| Asia -> NY AM | skip | 2500 (emu-only) | 5 / 33 | 1.20 / 1.22 / 0.984 | 1.00 / 1.000 | 1.07, 0.90 | 0.93, 1.00 | 1.01, 0.92 | 0.78, 1.95 | 0.92 / 0.986 | 11/10/72 |
| Asia -> NY AM | half | 2500 (emu-only) | 5 / 33 | 1.07 / 1.00 / 0.992 | 1.00 / 1.000 | 1.03, 0.95 | 0.96, 1.00 | 0.97, 0.96 | 0.88, 1.47 | 0.94 / 0.993 | 11/10/72 |
| Asia -> NY AM | skip | 3000 | 3 / 19 | 1.21 / 1.22 / 0.980 | 1.00 / 1.000 | 1.04, 0.91 | 1.00, 1.00 | 0.99, 0.98 | 0.88, 1.39 | 0.96 / 0.986 | 8/4/81 |
| Asia -> NY AM | half | 3000 | 3 / 19 | 1.07 / 1.00 / 0.990 | 1.00 / 1.000 | 1.02, 0.95 | 1.00, 1.00 | 0.98, 0.99 | 0.93, 1.20 | 0.97 / 0.993 | 8/4/81 |
| Asia -> NY AM | skip | 4000 | 0 / 8 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.04, 0.97 | 1.00, 1.00 | 0.99, 1.00 | 0.88, 1.38 | 0.95 / 1.005 | 6/2/85 |
| Asia -> NY AM | half | 4000 | 0 / 8 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.02, 0.99 | 1.00, 1.00 | 0.98, 1.00 | 0.93, 1.19 | 0.97 / 1.003 | 6/2/85 |
| Asia -> NY AM | skip | 5000 | 0 / 4 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.03, 0.98 | 0.94, 1.23 | 0.99 / 1.001 | 3/1/89 |
| Asia -> NY AM | half | 5000 | 0 / 4 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.01, 0.99 | 0.97, 1.12 | 0.99 / 1.000 | 3/1/89 |
| Asia -> NY AM | skip | 6000 | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 0.99, 1.03 | 1.00 / 1.001 | 1/0/92 |
| Asia -> NY AM | half | 6000 | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 0.99, 1.02 | 1.00 / 1.000 | 1/0/92 |
| Asia -> NY AM | skip | 7000 (emu-only) | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 0.99, 1.03 | 1.00 / 1.001 | 1/0/92 |
| Asia -> NY AM | half | 7000 (emu-only) | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 0.99, 1.02 | 1.00 / 1.000 | 1/0/92 |
| Asia -> NY AM | skip | 8000 (emu-only) | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 0.99, 1.03 | 1.00 / 1.001 | 1/0/92 |
| Asia -> NY AM | half | 8000 (emu-only) | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 0.99, 1.02 | 1.00 / 1.000 | 1/0/92 |
| Asia -> London | skip | 2000 (emu-only) | 9 / 46 | 0.99 / 1.00 / 1.013 | 0.98 / 1.018 | 0.98, 0.98 | 0.92, 1.01 | 1.02, 1.03 | 0.84, 1.78 | 0.93 / 1.028 | 20/11/62 |
| Asia -> London | half | 2000 (emu-only) | 9 / 46 | 0.99 / 1.00 / 1.006 | 0.99 / 1.009 | 0.99, 0.99 | 0.96, 1.01 | 1.01, 1.02 | 0.89, 1.39 | 0.95 / 1.014 | 20/11/62 |
| Asia -> London | skip | 2500 (emu-only) | 5 / 29 | 1.01 / 1.00 / 0.999 | 1.00 / 1.000 | 0.98, 0.98 | 0.94, 1.01 | 1.02, 1.04 | 0.91, 1.62 | 0.96 / 1.020 | 12/7/74 |
| Asia -> London | half | 2500 (emu-only) | 5 / 29 | 1.00 / 1.00 / 0.999 | 1.00 / 1.000 | 0.99, 0.99 | 0.97, 1.01 | 1.01, 1.02 | 0.92, 1.31 | 0.97 / 1.010 | 12/7/74 |
| Asia -> London | skip | 3000 | 3 / 17 | 1.02 / 1.00 / 0.997 | 1.00 / 1.000 | 1.00, 0.98 | 0.94, 1.01 | 1.01, 1.03 | 1.00, 1.27 | 0.99 / 1.011 | 5/5/83 |
| Asia -> London | half | 3000 | 3 / 17 | 1.01 / 1.00 / 0.999 | 1.00 / 1.000 | 1.00, 0.99 | 0.97, 1.01 | 1.00, 1.02 | 0.97, 1.14 | 0.98 / 1.005 | 5/5/83 |
| Asia -> London | skip | 4000 | 0 / 6 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.01, 1.03 | 1.00, 1.16 | 1.00 / 1.008 | 3/3/87 |
| Asia -> London | half | 4000 | 0 / 6 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.01 | 0.97, 1.08 | 0.99 / 1.004 | 3/3/87 |
| Asia -> London | skip | 5000 | 0 / 4 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 0.95, 1.04 | 1.07, 0.78 | 1.01 / 1.004 | 2/2/89 |
| Asia -> London | half | 5000 | 0 / 4 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 0.98, 1.02 | 1.04, 0.89 | 1.01 / 1.002 | 2/2/89 |
| Asia -> London | skip | 6000 | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 1.06, 0.83 | 1.02 / 0.997 | 0/1/92 |
| Asia -> London | half | 6000 | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 1.03, 0.92 | 1.01 / 0.998 | 0/1/92 |
| Asia -> London | skip | 7000 (emu-only) | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 1.06, 0.83 | 1.02 / 0.997 | 0/1/92 |
| Asia -> London | half | 7000 (emu-only) | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 1.03, 0.92 | 1.01 / 0.998 | 0/1/92 |
| Asia -> London | skip | 8000 (emu-only) | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 1.06, 0.83 | 1.02 / 0.997 | 0/1/92 |
| Asia -> London | half | 8000 (emu-only) | 0 / 1 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.00, 1.00 | 1.03, 0.92 | 1.01 / 0.998 | 0/1/92 |
| London -> NY AM | skip | 2000 (emu-only) | 4 / 18 | 0.99 / 1.00 / 1.002 | 1.00 / 1.000 | 1.00, 1.00 | 1.01, 0.93 | 1.07, 0.89 | 0.90, 1.52 | 0.99 / 0.975 | 6/8/79 |
| London -> NY AM | half | 2000 (emu-only) | 4 / 18 | 1.00 / 1.00 / 1.001 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 0.97 | 1.03, 0.95 | 0.94, 1.26 | 0.99 / 0.988 | 6/8/79 |
| London -> NY AM | skip | 2500 (emu-only) | 2 / 10 | 0.98 / 1.00 / 1.006 | 0.98 / 1.011 | 1.00, 1.00 | 1.00, 0.99 | 1.06, 0.97 | 0.95, 1.20 | 1.00 / 0.998 | 5/4/84 |
| London -> NY AM | half | 2500 (emu-only) | 2 / 10 | 0.99 / 1.00 / 1.003 | 0.99 / 1.005 | 1.00, 1.00 | 1.00, 0.99 | 1.03, 0.98 | 0.97, 1.10 | 1.00 / 0.999 | 5/4/84 |
| London -> NY AM | skip | 3000 | 1 / 6 | 0.99 / 1.00 / 1.004 | 0.98 / 1.011 | 1.00, 1.00 | 1.00, 0.99 | 1.04, 0.98 | 0.95, 1.20 | 1.00 / 0.999 | 3/3/87 |
| London -> NY AM | half | 3000 | 1 / 6 | 0.99 / 1.00 / 1.002 | 0.99 / 1.005 | 1.00, 1.00 | 1.00, 0.99 | 1.02, 0.99 | 0.97, 1.10 | 1.00 / 1.000 | 3/3/87 |
| London -> NY AM | skip | 4000 | 0 / 2 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 0.99 | 1.00, 1.00 | 0.93, 1.15 | 0.97 / 1.000 | 1/1/91 |
| London -> NY AM | half | 4000 | 0 / 2 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 0.99 | 1.00, 1.00 | 0.96, 1.07 | 0.99 / 1.000 | 1/1/91 |
| any earlier session -> each later session | skip | 2000 (emu-only) | 13 / 83 | 1.21 / 1.22 / 1.005 | 0.97 / 1.034 | 1.14, 0.90 | 1.09, 0.92 | 1.01, 0.81 | 0.87, 1.82 | 0.99 / 0.954 | 20/29/44 |
| any earlier session -> each later session | half | 2000 (emu-only) | 13 / 83 | 1.06 / 1.00 / 1.002 | 0.97 / 1.017 | 0.99, 0.95 | 1.02, 0.96 | 0.98, 0.90 | 0.90, 1.41 | 0.96 / 0.977 | 20/29/44 |
| any earlier session -> each later session | skip | 2500 (emu-only) | 9 / 55 | 1.23 / 1.22 / 0.986 | 1.01 / 0.998 | 1.00, 1.00 | 1.14, 0.97 | 1.42, 0.77 | 0.91, 2.27 | 1.16 / 0.967 | 13/22/58 |
| any earlier session -> each later session | half | 2500 (emu-only) | 9 / 55 | 1.08 / 1.00 / 0.993 | 1.01 / 0.999 | 1.00, 1.00 | 1.04, 0.98 | 1.15, 0.89 | 0.91, 1.63 | 1.03 / 0.984 | 13/22/58 |
| any earlier session -> each later session | skip | 3000 | 7 / 34 | 1.25 / 1.22 / 0.972 | 1.01 / 0.998 | 1.07, 0.94 | 1.05, 0.99 | 1.24, 0.88 | 1.02, 1.71 | 1.11 / 0.969 | 9/14/70 |
| any earlier session -> each later session | half | 3000 | 7 / 34 | 1.09 / 1.00 / 0.986 | 1.01 / 0.999 | 1.03, 0.97 | 1.02, 1.00 | 1.08, 0.94 | 0.98, 1.35 | 1.02 / 0.985 | 9/14/70 |
| any earlier session -> each later session | skip | 4000 | 2 / 18 | 1.02 / 1.00 / 0.993 | 1.02 / 0.994 | 1.04, 0.97 | 0.97, 1.01 | 1.22, 0.91 | 0.84, 1.86 | 1.03 / 0.995 | 7/7/79 |
| any earlier session -> each later session | half | 4000 | 2 / 18 | 1.01 / 1.00 / 0.997 | 1.01 / 0.997 | 1.02, 0.99 | 0.99, 1.00 | 1.07, 0.95 | 0.89, 1.43 | 0.98 / 0.997 | 7/7/79 |
| any earlier session -> each later session | skip | 5000 | 0 / 7 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 0.90, 1.04 | 0.89, 1.38 | 0.92 / 1.016 | 4/2/87 |
| any earlier session -> each later session | half | 5000 | 0 / 7 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 0.95, 1.02 | 0.94, 1.19 | 0.96 / 1.008 | 4/2/87 |
| any earlier session -> each later session | skip | 6000 | 0 / 5 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.03, 0.98 | 0.93, 1.23 | 0.98 / 1.001 | 3/2/88 |
| any earlier session -> each later session | half | 6000 | 0 / 5 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.01, 0.99 | 0.96, 1.12 | 0.99 / 1.000 | 3/2/88 |
| any earlier session -> each later session | skip | 7000 (emu-only) | 0 / 4 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.03, 0.98 | 0.99, 0.98 | 1.01 / 0.996 | 2/2/89 |
| any earlier session -> each later session | half | 7000 (emu-only) | 0 / 4 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.01, 0.99 | 0.99, 0.99 | 1.00 / 0.998 | 2/2/89 |
| any earlier session -> each later session | skip | 8000 (emu-only) | 0 / 3 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.04, 0.97 | 0.99, 0.98 | 1.01 / 0.993 | 1/2/90 |
| any earlier session -> each later session | half | 8000 (emu-only) | 0 / 3 | 1.00 / 1.00 / 1.000 | 1.00 / 1.000 | 1.00, 1.00 | 1.00, 1.00 | 1.02, 0.98 | 0.99, 0.99 | 1.00 / 0.997 | 1/2/90 |

## 3. BEST-OF-MANY NULL (emulated, L6M, 32 sets = 4 pairs x 4 thresholds x skip/half)

- XS: pick rule = lowest L6M ulcer among sets with total $ >= reference: real best ANY/6000/skip = 17.5% ulcer gain; null (sign-flipped deltas, 18 nonzero days, 1000 draws) median 9.2%, 80th pct 18.8%, 95th pct 19.9%; real beats 74% of draws (gate 80%): FAIL.
- XF: pick rule = lowest L6M ulcer among sets with total $ >= reference: real best LONY/3000/skip = 1.2% ulcer gain; null (sign-flipped deltas, 8 nonzero days, 1000 draws) median 1.4%, 80th pct 2.5%, 95th pct 3.6%; real beats 22% of draws (gate 80%): FAIL.

## 4. VERDICT PER PAIR OF SESSIONS (bare base, 2 lots, exact L6M; labels from the approved gates: pick on recent, walk-forward >= 0.58 on blocks the rule changes, prior-year band, best-of-many null >= 4 of 5)
"none" = the reference row (no carry-over rule). Drawdown first.

| pair | best setting | L6M ulcer / max DD / worst day / $/wk | L3M ulcer / $/wk | days fired L6M (3.5y) | cost on days that would have recovered vs saved (L6M) | prior years (emulated) ulcer x, $/wk x: 2023 / 2024 / 2025 | walk-forward (changed blocks) | null | label |
|---|---|---|---|---|---|---|---|---|---|
| Asia -> NY AM | SKIP all NY AM entries when Asia lost more than $6,000 per lot-per-book ($12,000 at 2 lots) | 0.82 / 0.76 / 0.73 / 1.011 | 0.74 / 1.02 | 3 (14) | 1 day -$5,962 vs 2 days +$16,963 | 1.00, 1.00 / 0.96, 0.99 / 0.81, 1.04 | 8 win / 5 lose = 0.62 (PASS, thin) | emulated best-of-32 74% (FAIL, gate 80%) | LEAD, thin: the whole L6M gain is two days (2026-07-06 and 2026-08-07 are the two worst base days, -$23,091 and -$22,726; the max-DD gain -24% is identical for every threshold 3000-6000 because it comes from those same days); 3 firing days in L6M, 14 in 42 months |
| Asia -> NY AM | thresholds 3000 / 4000 / 5000 (more days fired) | ulcer 0.87 / 0.87 / 0.86, max DD 0.76, $/wk 0.959 / 0.968 / 0.979 | 0.80 / 0.79 / 0.79; $/wk 0.96-0.98 | 17 / 11 / 7 (74 / 48 / 26) | 11 days -$65,366 vs 6 days +$23,397 (3000); 7 days -$52,014 vs 4 +$19,241 (4000); 5 days -$38,758 vs 2 +$16,963 (5000) | 2023 ulcer 1.04 / 1.04 / 1.00 and $/wk 0.92 / 0.91 / 1.00; 2024 0.88 / 1.02 / 0.90 ($ 0.92 / 0.95 / 0.98); 2025 0.88 / 0.79 / 0.73 | 21/24 = 0.47; 16/17 = 0.48; 10/13 = 0.43 (FAIL all three) | same family null FAIL | WEAK-BUT-POSITIVE for drawdown only (risk down, dollars down 2-4%, loses blocks as often as it wins). The skip costs more on the days that would have recovered than it saves. |
| Asia -> NY AM | HALF size instead of skip (any X) | ulcer 0.90-0.92, max DD 0.88, worst day 0.84, $/wk 0.98-1.005 | 0.87-0.89 | same days | exactly half of the skip numbers | same shape, half the size | same blocks as skip | | same label as the skip at the same X; 2 lots -> 1 lot |
| Asia -> London | ASLO 3000 skip (best of the pair) | 0.99 / 1.00 / 0.98 / 1.006 | 1.00 / 1.00 | 14 (56) | 6 days -$10,029 vs 8 days +$15,739 | 1.00, 0.99 / 1.07, 0.97 / 0.99, 0.99 | L6M 6 win / 3 lose, 3.5y 15 / 26 = 0.37 (FAIL) | not in the pair null | none (reference row). The rule moves ulcer 1% and max DD 0%: London books are too small a part of the day to matter. BEST-AVAILABLE-NOT-PROVEN: 3000 skip |
| London -> NY AM | none | 1.00 / 1.00 / 1.00 / 1.005 (3000 skip) | 0.99 / 1.01 | 1 (6) at 3000; 0 at 4000+ | 0 vs 1 day +$5,273 | no change in 2023 / 2024, 2025 1.04 ulcer worse | 3 / 3 over 3.5y | | none (reference row): 1 firing day in L6M, no evidence either way |
| NY AM -> NY PM | none (reference row); least bad = HALF at 6000 | skip: ulcer 1.03-1.15, max DD 1.00-1.01, $/wk 0.93-0.99; half: ulcer 1.01-1.05, $/wk 0.97-0.995; worst week 1.9-2.9x worse at 3000/4000 | skip 1.00-1.02 / 0.97-1.00 | 20 / 16 / 8 / 5 at 3000 / 4000 / 5000 / 6000 | 3000 skip: 16 days -$98,821 vs 4 days +$10,998; 6000 skip: 3 days -$21,749 vs 2 days +$8,024 | not available (no NP prior-year base rows) | 3/7, 3/6, 3/3, 2/2 (skip) | no | none (reference row): the NY PM books make money back after a bad NY AM; skipping them costs far more than it saves (wrong-signed). BEST-AVAILABLE-NOT-PROVEN is the reference itself |
| ANY earlier -> each later | ANY 6000 skip | 0.81 / 0.76 / 0.73 / 1.017 | 0.74 / 1.02 | 3 (18) | 1 day -$2,193 vs 2 days +$19,797 | 1.00, 1.00 / 0.97, 0.99 / 0.71, 1.05 | 7 win / 9 lose = 0.44 (FAIL) | 74% FAIL | WEAK-BUT-POSITIVE (same two days; in this set it only touches London and NY AM; NY PM not in the set) |

### FITTED-PICK BASE (what D8 delivers)
Carry-over does NOT help the delivered picks. Emulated on the separate pick trades (Asia JT19 + NY AM JT68 + London bare): at 3000 Asia -> NY AM fires 3 days in L6M and makes it WORSE (ulcer x1.21, max DD x1.22, $/wk x0.98); at 4000 and above it does not fire in L6M or L3M at all (8, 4 and 1 days in 42 months at 4000 / 5000 / 6000); ANY 3000 ulcer x1.25. The pick already carries StackCut / BookLock / the stack day stop which cut the same losing nights, so an extra cross-session skip has almost nothing left to remove. Label for the delivered picks: none (reference row); BEST-AVAILABLE-NOT-PROVEN = Asia -> NY AM skip at 4000 ($8,000 at 2 lots) over 42 months: ulcer x0.95, $/wk x1.005, 8 days fired, 6 win / 2 lose blocks, but 0 firing days in L6M so the "pick on recent" gate has nothing to stand on. The exact XF rows are still arriving (landed months fired 0 days, consistent); I will re-score them in the end-of-run pass.

### EXACT RULE TEXT FOR THE RELAY (only if LEAD decides to carry the Asia -> NY AM LEAD)
"At each NY AM entry: prior = sum over all Asia books of (realized P&L of today's Globex day since the 18:00 ET roll + the open P&L of any Asia trade still open at the last 1-minute close). If prior < -(6,000 x lots-per-book) dollars (i.e. -$12,000 at 2 lots, -$6,000 at 1 lot) skip that entry. Re-read at every NY AM entry; the skip is only for today's NY AM session (nothing carries into NY PM or into tomorrow); open trades and the Asia books are untouched. Variant: instead of skip, enter with max(1, floor(lots x 0.5 + 0.5)) lots." Evidence is two days; do not size it up. The delivered picks (D8 file) should carry NO carry-over rule.

## WHAT I COULD NOT VERIFY
- Prior years are emulated, not engine rows; the emulator reproduces L6M exact fired days within 0-2 days and the deltas within about $1k per day except the single days noted, so prior-year numbers are good to about that, not exact.
- Prior years for NYNP / ANY in the NP set (no NP prior-year bases) and the exact XF rows (still running).
- The null is a sign-flip emulation, not the random-entry null; a real one needs engine rows (count above).
- Whether the engine's day_pnl includes the $1.18 fee exactly (inferred from the emulation matching on the engine-fee basis).
- The carry rule in D8's live relay: the engine reads the open P&L of an earlier-session trade still in progress; the Asia books are flat by 02:00 ET so in practice this term is zero.
