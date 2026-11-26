**HEADER (W-LAYERS2, 2026-11-26 00:09Z)**
- PICK: TL3_SR_NY_STKd8cd0279ff_BF1_JT162 (filter-first pick, order Josh 20:57Z 11-25); STC-FREE: YES, no STC setting (installable on NT8)
- STACK: TL3_ALN_NY_STKd8cd0279ff; lots at the fit basis: native x4 weighted basis: MF1..MF9 = 4 / 4 / 4 / 4 / 2 / 4 / 1 / 1 / 2 lots
- FILTER RESULT: 4 of 242 combos pass (no RED prior-year band, $/wk above zero in 2023 / 2024 / 2025, walk-forward persistence >= 0.58); this pick: bands AMBER/AMBER/GREEN, prior-year $/wk $6909 / $6267 / $14198, persistence 0.860, L6M ulcer 14679 / max DD -52244 / $36786 per wk (bare L6M ulcer 28581 / max DD -99970 / $51363 per wk); 1 inside the 15% L6M guard
- NULL: FAILED (stack-level null, early stop after 2 misses: real -0.412 vs draws -0.504 / -0.819, beats 0 of 2; gate needs 4 of 5). LABEL: BEST-AVAILABLE-NOT-PROVEN (null failed; it was never a gate for this pick under the filter-first order) and WEAK-BUT-POSITIVE (every prior year above zero, but at a fraction of bare income).
- DATA END: research data to 2026-10 (L6M = 2026-05..2026-10; last month landed 2026-10, research cap 2026-10-31); prior years 2023-04..2025-10 minus 2025-11.
- SIZES: 6/3/1 (6/6/6/6/3/6/1/1/3) and 6/3/2 (6/6/6/6/3/6/2/2/3): autopilot/FILTERED_PICKS_FILE_SIZE.md

# D8_LAYER_KEYS_NYAM_NYAMW_JT162 - NYAM stack TL3_ALN_NY_STKd8cd0279ff: the filter-first pick as key = value (fit basis in the header; settings do not change with size; dollar rules per the ENGINE CHECK section)

Written 2026-11-26 00:08Z by W-LAYERS2 from BAREFIT_NY_STKd8cd0279ff_FILT.md (pick TL3_SR_NY_STKd8cd0279ff_BF1_JT162), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L43f0cbfb.BRS8U_w4_s0    stop 120 pts / target 120 pts ; R per lot = $2400 ; entries 0930-1159 ET
MF2 = B7bfd33b7_w4_s0    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0930-1159 ET
MF3 = Bf428c4a1.BRS8U_w4_s0    stop 120 pts / target 120 pts ; R per lot = $2400 ; entries 0930-1159 ET
MF4 = Le4fede95.BRF90_30_w4_s0    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 0930-1159 ET
MF5 = Lf0346d55.BRP60_w2_s0    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0930-1159 ET
MF6 = L8cfda948.BRF90_30_w4_s0    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 0930-1159 ET
MF7 = L4407508c.BRF120_60_w1_s0    stop 120 pts / target 60 pts ; R per lot = $2400 ; entries 0933-1157 ET
MF8 = L39287638.BRF80_40_w1_s0    stop 80 pts / target 40 pts ; R per lot = $1600 ; entries 0930-1159 ET
MF9 = L64390867.BRF80_40_w2_s0    stop 80 pts / target 40 pts ; R per lot = $1600 ; entries 0950-1150 ET
median book R (STK) = 90 pts x $20 = $1800 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE PICK TL3_SR_NY_STKd8cd0279ff_BF1_JT162 resolved for THIS stack (factor = code ; the CAP / STK / DLA / DLB / DLC / SC / FR_LOSS comments below are the builders' old wording: the ENGINE CHECK section at the end wins)
```
BL = BL6    # BookLock arm 2.0R give-back 67%
CAP = CAP6    # per-book day loss stop -3R ($14400)
STK = STK7    # WHOLE-STACK day loss stop -6R of one book ($28800)
SZW = SZW2    # ER sizer (new-book hook) ER(20,5m) < 0.30 -> lots x 0.50, half-up, min 1
NTS = NTS2    # no-trade-set rule dropped
CG = CGB2    # skip after 2 same-side losses (c_gov, governs every new book MF1..MF5)
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```

## ENGINE CHECK 2026-11-26 00:09Z (W-LAYERS2; documentation only: the fitted numbers already include all of this; where a line above says otherwise THIS SECTION WINS)

1. **CAP** = static DOLLAR caps on EVERY book, both sides: profit +$48000, loss -$14400 (engine day cap sim.py:722-730, once per 1-minute bar, CLOSED day P&L only, closes the open trade with exit name DayHalt; stackrule_gen.py:57 and :71 set the dollars as k x the MEDIAN book R, NOT each book's own R; the profit rows CAP1-4 also set the loss cap at 4R and the loss rows CAP5-8 also set the profit cap at 10R, so the pair is coded as above, not one side). Own book R differs but the dollars are NOT scaled per book at the fit basis.
2. **STK** (lay_hooks.stack_caps) = whole-stack day stop: loss -$28800, profit off (closed day P&L of all books, same engine path as CAP).
3. **DLA / DLB / DLC**: none in this pick (no dl_hooks in the set).
4. **SC** (StackCut): NOT in this pick (stackcut_share None); the label "scope Asia-only" in older pages is a hard-coded string in stackrule_gen.py:60 and means nothing here.
5. **Scaling at the file sizes**: the size rows scale the per-book static CAP dollars by file lots / fit lots (PICKC sets); the STK stack dollars, the DLB dollars and the StackCut share are NOT rescaled (DLB follows the smallest-lot rule above). If the build keeps the fit-basis dollars unscaled the file-size results differ; that variant is not tested.
