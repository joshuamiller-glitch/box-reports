# D8_LAYER_KEYS_ASIA_4BOOK_JT110 - Asia stack TL3_ALN_AS_STKd8da2eb47b: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-24 15:59Z by W-LAYERS2 from BAREFIT_AS_STKd8da2eb47b_R100_L2.md (pick TL3_SR_AS_STKd8da2eb47b_BF2_JT110), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = Lb0e6dfa3_R0_F40_80    stop 40 pts / target 80 pts ; R per lot = $800 ; entries 0000-2356 ET
MF2 = L385f4f2e_CX502    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0001-2359 ET
MF3 = L9c2622b0_R0_P45    stop 45 pts / target 45 pts ; R per lot = $900 ; entries 0000-2359 ET
MF4 = L4aaacdb2_R0_P30    stop 30 pts / target 30 pts ; R per lot = $600 ; entries 0000-2359 ET
median book R (STK) = 42.5 pts x $20 = $850 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_AS_STKd8da2eb47b_BF2_JT110 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = CU4    # loss cut when unrealised <= -40 pts (1.0 x stop)
TAKE.MF1 = FR_TAKE4    # W-FASTR pick: lock 80% -> +10
ZONE.MF1 = ZONE5    # zone no-trade set MF1 Skip within 30 pts
LOSS.MF2 = CU4    # loss cut when unrealised <= -60 pts (1.0 x stop)
LOCK.MF2 = LK7    # lock at 80% -> stop to entry+0 pts
ZONE.MF2 = ZONE2    # zone no-trade set MF2 Half within 30 pts
LOSS.MF3 = CX2    # context cut (fresh) at -27 pts
TAKE.MF3 = TK2    # take at 50% of target after 15 s without a new extreme
ZONE.MF3 = ZONE3    # zone no-trade set MF3 Half within 50 pts
TAKE.MF4 = SHV3    # target shave MF4 8 ticks
ZONE.MF4 = ZONE4    # zone no-trade set MF4 Skip within 20 pts
BL = BL1    # BookLock arm 1.5R give-back 33%
CAP = CAP2    # per-book day profit stop +7.5R ($12750)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS2    # no-trade-set rule dropped
CG = CGB1    # skip after 1 same-side losses (c_gov, governs every new book MF1..MF5)
DLA = DLA11    # per-book day loss halt at -4R (new entries only, open position runs, rest of session)
DLC = DLC3    # per-book halt after 4 consecutive full-stop losses (rest of session)
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```
