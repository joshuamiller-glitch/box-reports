**HEADER (W-LAYERS2, 2026-11-26 00:09Z)**
- PICK: TL3_SR_NP_STKd893133bd8_BF2_JT241 (filter-first pick, order Josh 20:57Z 11-25); STC-FREE: YES, no STC setting (installable on NT8)
- STACK: TL3_ALN_NP_STKd893133bd8; lots at the fit basis: 2 lots per book (4 books)
- FILTER RESULT: 10 of 80 combos pass (no RED prior-year band, $/wk above zero in 2023 / 2024 / 2025, walk-forward persistence >= 0.58); this pick: bands AMBER/GREEN/GREEN, prior-year $/wk $1718 / $1576 / $2907, persistence 0.957, L6M ulcer 3173 / max DD -10368 / $5606 per wk (bare L6M ulcer 5573 / max DD -24257 / $8736 per wk); 1 inside the 15% L6M guard
- NULL: FAILED (stack-level null, early stop after 2 misses: real -0.250 vs draws -0.531 / -0.303, beats 0 of 2; gate needs 4 of 5). LABEL: BEST-AVAILABLE-NOT-PROVEN (null failed; it was never a gate for this pick under the filter-first order) and WEAK-BUT-POSITIVE (every prior year above zero, but at a fraction of bare income).
- DATA END: research data to 2026-10 (L6M = 2026-05..2026-10; last month landed 2026-10, research cap 2026-10-31); prior years 2023-04..2025-10 minus 2025-11.
- SIZES: 3 / 4 / 6 lots per book: autopilot/FILTERED_PICKS_FILE_SIZE.md

# D8_LAYER_KEYS_NYPM_4BOOK_JT241 - NYPM stack TL3_ALN_NP_STKd893133bd8: the filter-first pick as key = value (fit basis in the header; settings do not change with size; dollar rules per the ENGINE CHECK section)

Written 2026-11-26 00:08Z by W-LAYERS2 from BAREFIT_NP_STKd893133bd8_r200_FILT.md (pick TL3_SR_NP_STKd893133bd8_BF2_JT241), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L52359bf4_R0_P30    stop 30 pts / target 30 pts ; R per lot = $600 ; entries 1200-1800 ET
MF2 = L8e0bf58c_R0_S8U    stop 120 pts / target 120 pts ; R per lot = $2400 ; entries 1200-1559 ET
MF3 = L4bdd521a_R0_F80_40    stop 80 pts / target 40 pts ; R per lot = $1600 ; entries 1200-1530 ET
MF4 = L2c6916a5_R0_P60    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 1200-1559 ET
median book R (STK) = 70 pts x $20 = $1400 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE PICK TL3_SR_NP_STKd893133bd8_BF2_JT241 resolved for THIS stack (factor = code ; the CAP / STK / DLA / DLB / DLC / SC / FR_LOSS comments below are the builders' old wording: the ENGINE CHECK section at the end wins)
```
LOSS.MF1 = CU4    # loss cut when unrealised <= -30 pts (1.0 x stop)
LOCK.MF1 = LK8    # lock at 80% -> stop to entry+10 pts
ZONE.MF1 = ZONE3    # zone no-trade set MF1 Half within 50 pts
LOSS.MF2 = CU3    # loss cut when unrealised <= -96 pts (0.8 x stop)
TAKE.MF2 = SHV2    # target shave MF2 4 ticks
ZONE.MF2 = ZONE1    # zone no-trade set MF2 Half within 10 pts
LOSS.MF3 = CU4    # loss cut when unrealised <= -80 pts (1.0 x stop)
ZONE.MF3 = ZONE2    # zone no-trade set MF3 Half within 30 pts
LOSS.MF4 = CU4    # loss cut when unrealised <= -60 pts (1.0 x stop)
LOCK.MF4 = LK7    # lock at 80% -> stop to entry+0 pts
ZONE.MF4 = ZONE2    # zone no-trade set MF4 Half within 30 pts
DLA = DLA5    # per-book day loss halt at -3R (open P&L counts, close the position, halt rest of session)
DLB = DLB10    # stack day loss halt at -$6000 per lot per book (new entries only, open positions run, rest of session)
BL = BL7    # BookLock arm 3.0R give-back 33%
CAP = CAP6    # per-book day loss stop -3R ($8400)
STK = STK1    # WHOLE-STACK day profit stop +4R of one book ($11200)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```

## ENGINE CHECK 2026-11-26 00:09Z (W-LAYERS2; documentation only: the fitted numbers already include all of this; where a line above says otherwise THIS SECTION WINS)

1. **CAP** = static DOLLAR caps on EVERY book, both sides: profit +$28000, loss -$8400 (engine day cap sim.py:722-730, once per 1-minute bar, CLOSED day P&L only, closes the open trade with exit name DayHalt; stackrule_gen.py:57 and :71 set the dollars as k x the MEDIAN book R, NOT each book's own R; the profit rows CAP1-4 also set the loss cap at 4R and the loss rows CAP5-8 also set the profit cap at 10R, so the pair is coded as above, not one side). Own book R differs but the dollars are NOT scaled per book at the fit basis.
2. **STK** (lay_hooks.stack_caps) = whole-stack day stop: loss -$0, profit +$11200 (closed day P&L of all books, same engine path as CAP).
3. **DLA** = per-book daily loss stop X = 3 R, mode close (dl_hooks.py book option: the Globex day rolls at 18:00 ET, open P&L counted, checked inside check_book_lock at most every 2 s and by check_limits once a minute).
4. **DLB** = stack daily loss Y = $6000, mode new, pause 0 min: the threshold is -Y x b.base_qty of the CHECKING book (dl_hooks.py:51) = -$6000 x the LOTS of the smallest-lot book not yet halted: at the fit basis (2 lots per book (4 books)) = -$12000; at a file size it is -$6000 x that size's smallest lots (NOT scaled by lots / fit lots; e.g. 3 per book = -$18000, 4 = -$24000, 6 = -$36000).
5. **SC** (StackCut): NOT in this pick (stackcut_share None); the label "scope Asia-only" in older pages is a hard-coded string in stackrule_gen.py:60 and means nothing here.
6. **Early-exit rules (ec_hooks)** (th_ec/ec_hooks.py:96-112, per 1-second state-tape row from the entry second r_e): MF1 flat {'d': 30.0}; MF2 flat {'d': 96.0}; MF3 flat {'d': 80.0}; MF4 flat {'d': 60.0}. Rule meanings: flat d = exit when adverse excursion x <= -d pts (ec_hooks.py:102); scratch (d, s) = after the trade has been -d pts it exits when price comes back to -s pts (ec_hooks.py:105); nft (X, N) = ONE check at tape row r_e + N x 60, exit if x < X (ec_hooks.py:103, not repeated).
7. **Scaling at the file sizes**: the size rows scale the per-book static CAP dollars by file lots / fit lots (PICKC sets); the STK stack dollars, the DLB dollars and the StackCut share are NOT rescaled (DLB follows the smallest-lot rule above). If the build keeps the fit-basis dollars unscaled the file-size results differ; that variant is not tested.
