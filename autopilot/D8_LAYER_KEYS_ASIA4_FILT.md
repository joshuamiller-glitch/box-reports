**HEADER (W-LAYERS2, 2026-11-26 00:09Z)**
- PICK: TL3_SR_AS_STKd8da2eb47b_BF2_JT275 (filter-first pick, order Josh 20:57Z 11-25); STC-FREE: YES, no STC setting (installable on NT8)
- STACK: TL3_ALN_AS_STKd8da2eb47b; lots at the fit basis: 2 lots per book (4 books)
- FILTER RESULT: 1 of 80 combos pass (no RED prior-year band, $/wk above zero in 2023 / 2024 / 2025, walk-forward persistence >= 0.58); this pick: bands AMBER/AMBER/GREEN, prior-year $/wk $815 / $1223 / $1309, persistence 0.892, L6M ulcer 2886 / max DD -10523 / $7316 per wk (bare L6M ulcer 5887 / max DD -21112 / $14435 per wk); 1 inside the 15% L6M guard
- NULL: FAILED (stack-level null, early stop after 2 misses: real -0.429 vs draws -0.724 / -0.632, beats 0 of 2; gate needs 4 of 5). LABEL: BEST-AVAILABLE-NOT-PROVEN (null failed; it was never a gate for this pick under the filter-first order) and WEAK-BUT-POSITIVE (every prior year above zero, but at a fraction of bare income).
- DATA END: research data to 2026-10 (L6M = 2026-05..2026-10; last month landed 2026-10, research cap 2026-10-31); prior years 2023-04..2025-10 minus 2025-11.
- SIZES: the file runs 6/4/3 per book rows are NOT built for Asia (no size table ordered); scale rule below

# D8_LAYER_KEYS_ASIA_4BOOK_JT275 - Asia stack TL3_ALN_AS_STKd8da2eb47b: the filter-first pick as key = value (fit basis in the header; settings do not change with size; dollar rules per the ENGINE CHECK section)

Written 2026-11-26 00:08Z by W-LAYERS2 from BAREFIT_AS_STKd8da2eb47b_r200_FILT.md (pick TL3_SR_AS_STKd8da2eb47b_BF2_JT275), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = Lb0e6dfa3_R0_F40_80    stop 40 pts / target 80 pts ; R per lot = $800 ; entries 0000-2356 ET
MF2 = L385f4f2e_CX502    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0001-2359 ET
MF3 = L9c2622b0_R0_P45    stop 45 pts / target 45 pts ; R per lot = $900 ; entries 0000-2359 ET
MF4 = L4aaacdb2_R0_P30    stop 30 pts / target 30 pts ; R per lot = $600 ; entries 0000-2359 ET
median book R (STK) = 42.5 pts x $20 = $850 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE PICK TL3_SR_AS_STKd8da2eb47b_BF2_JT275 resolved for THIS stack (factor = code ; the CAP / STK / DLA / DLB / DLC / SC / FR_LOSS comments below are the builders' old wording: the ENGINE CHECK section at the end wins)
```
LOCK.MF1 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF1 = FR_TAKE4    # W-FASTR pick: lock 80% -> +10
ZONE.MF1 = ZONE3    # zone no-trade set MF1 Half within 50 pts
LOSS.MF2 = FR_LOSS9    # W-FASTR pick: scratch: after -45 exit at -5
LOCK.MF2 = LK7    # lock at 80% -> stop to entry+0 pts
TAKE.MF2 = TK12    # take at 95% of target after 30 s without a new extreme
TAKE.MF3 = TK2    # take at 50% of target after 15 s without a new extreme
ZONE.MF3 = ZONE4    # zone no-trade set MF3 Skip within 20 pts
LOSS.MF4 = CU3    # loss cut when unrealised <= -24 pts (0.8 x stop)
LOCK.MF4 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF4 = SHV2    # target shave MF4 4 ticks
ZONE.MF4 = ZONE4    # zone no-trade set MF4 Skip within 20 pts
STK = STK8    # WHOLE-STACK day loss stop -8R of one book ($13600)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS1    # no-trade-set halving 0.5 (today's rule)
CG = CGB1    # skip after 1 same-side losses (c_gov, governs every new book MF1..MF5)
DLA = DLA4    # per-book day loss halt at -2.5R (open P&L counts, close the position, halt rest of session)
DLB = DLB14    # stack day loss halt at -$8000 per lot per book (close positions, pause 60 min then re-arm)
DLC = DLC4    # per-book halt after 5 consecutive full-stop losses (rest of session)
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```

## ENGINE CHECK 2026-11-26 00:09Z (W-LAYERS2; documentation only: the fitted numbers already include all of this; where a line above says otherwise THIS SECTION WINS)

1. **CAP** is NOT in this pick: the set carries the no-op caps (1e12), nothing to code.
2. **STK** (lay_hooks.stack_caps) = whole-stack day stop: loss -$13600, profit off (closed day P&L of all books, same engine path as CAP).
3. **DLA** = per-book daily loss stop X = 2.5 R, mode close (dl_hooks.py book option: the Globex day rolls at 18:00 ET, open P&L counted, checked inside check_book_lock at most every 2 s and by check_limits once a minute).
4. **DLB** = stack daily loss Y = $8000, mode close, pause 60 min: the threshold is -Y x b.base_qty of the CHECKING book (dl_hooks.py:51) = -$8000 x the LOTS of the smallest-lot book not yet halted: at the fit basis (2 lots per book (4 books)) = -$16000; at a file size it is -$8000 x that size's smallest lots (NOT scaled by lots / fit lots; e.g. 3 per book = -$24000, 4 = -$32000, 6 = -$48000).
5. **DLC** = 5 consecutive Stop-named losing closes halts the books (pause 0 min).
6. **SC** (StackCut): NOT in this pick (stackcut_share None); the label "scope Asia-only" in older pages is a hard-coded string in stackrule_gen.py:60 and means nothing here.
7. **Early-exit rules (ec_hooks)** (th_ec/ec_hooks.py:96-112, per 1-second state-tape row from the entry second r_e): MF2 scratch {'d': 45, 's': 5}; MF4 flat {'d': 24.0}. Rule meanings: flat d = exit when adverse excursion x <= -d pts (ec_hooks.py:102); scratch (d, s) = after the trade has been -d pts it exits when price comes back to -s pts (ec_hooks.py:105); nft (X, N) = ONE check at tape row r_e + N x 60, exit if x < X (ec_hooks.py:103, not repeated); this pick's FR_LOSS is FR_LOSS9 = the scratch rule above (continuous per second, NOT the single-check nft of FR_LOSS8): .
8. **Scaling at the file sizes**: the size rows scale the per-book static CAP dollars by file lots / fit lots (PICKC sets); the STK stack dollars, the DLB dollars and the StackCut share are NOT rescaled (DLB follows the smallest-lot rule above). If the build keeps the fit-basis dollars unscaled the file-size results differ; that variant is not tested.
