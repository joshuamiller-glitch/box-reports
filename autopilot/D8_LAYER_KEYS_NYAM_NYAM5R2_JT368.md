# D8_LAYER_KEYS_NYAM_NYAM5R2_JT368 - NYAM stack TL3_ALN_NY_STKd8b76ecd35: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-24 21:20Z by W-LAYERS2 from BAREFIT_NY_STKd8b76ecd35_R300_L2.md (pick TL3_SR_NY_STKd8b76ecd35_BF2_JT368), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L8cfda948_R0_F90_30    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 0930-1159 ET
MF2 = Lf0346d55_R0_P60    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0930-1159 ET
MF3 = L7cc56d99    stop 120 pts / target 120 pts ; R per lot = $2400 ; entries 0930-1159 ET
MF4 = Lbb254083_R0_P45    stop 45 pts / target 45 pts ; R per lot = $900 ; entries 0930-1159 ET
MF5 = L8f11883e_R0_F30_90    stop 30 pts / target 90 pts ; R per lot = $600 ; entries 0950-1150 ET
median book R (STK) = 60 pts x $20 = $1200 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_NY_STKd8b76ecd35_BF2_JT368 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = CU2    # loss cut when unrealised <= -54 pts (0.6 x stop)
LOCK.MF1 = LK1    # lock at 50% -> stop to entry+0 pts
ZONE.MF1 = ZONE6    # zone no-trade set MF1 Skip within 50 pts
LOSS.MF2 = CX1    # context cut (fresh) at -24 pts
TAKE.MF2 = TK1    # take at 50% of target after 5 s without a new extreme
ZONE.MF2 = ZONE2    # zone no-trade set MF2 Half within 30 pts
LOSS.MF3 = CU4    # loss cut when unrealised <= -120 pts (1.0 x stop)
ZONE.MF3 = ZONE3    # zone no-trade set MF3 Half within 50 pts
LOSS.MF4 = CU4    # loss cut when unrealised <= -45 pts (1.0 x stop)
LOCK.MF4 = LK7    # lock at 80% -> stop to entry+0 pts
TAKE.MF4 = SHV2    # target shave MF4 4 ticks
LOCK.MF5 = LK8    # lock at 80% -> stop to entry+10 pts
TAKE.MF5 = FR_TAKE4    # W-FASTR pick: lock 80% -> +10
ZONE.MF5 = ZONE4    # zone no-trade set MF5 Skip within 20 pts
BL = BL1    # BookLock arm 1.5R give-back 33%
STK = STK3    # WHOLE-STACK day profit stop +8R of one book ($19200)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS1    # no-trade-set halving 0.5 (today's rule)
DLA = DLA16    # per-book day loss halt at -3R (close position, pause 120 min then re-arm)
DLB = DLB6    # stack day loss halt at -$8000 per lot per book (open P&L counts, all books halted, positions closed, rest of session)
DLC = DLC2    # per-book halt after 3 consecutive full-stop losses (rest of session)
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```
