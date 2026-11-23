# D8_LAYER_KEYS_LONDON - London stack TL3_ALN_LO_L19201dfc_R0BRF90_30: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-23 19:38Z by W-LAYERS2 from BAREFIT_LO_L19201dfc_R0BRF90_30.md (pick TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_JT14), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L19201dfc_R0_F90_30    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 0200-0829 ET
median book R (STK) = 90 pts x $20 = $1800 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_JT14 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = STC4    # state-cut cell MF1 mult 15.0    [NEEDS THE 10-LEVEL CANCEL TAPE: not reproducible from an NT8 feed]
LOCK.MF1 = LK3    # lock at 50% -> stop to entry+20 pts
ZONE.MF1 = ZONE3    # zone no-trade set MF1 Half within 50 pts
SC = SC1    # StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots)
CAP = CAP2    # per-book day profit stop +7.5R ($27000)
STK = STK2    # WHOLE-STACK day profit stop +6R of one book ($21600)
SZW = SZW2    # ER sizer (new-book hook) ER(20,5m) < 0.30 -> lots x 0.50, half-up, min 1
DLA = DLA4    # per-book day loss halt at -2.5R (open P&L counts, close the position, halt rest of session)
DLB = DLB3    # stack day loss halt at -$4000 per lot per book (open P&L counts, all books halted, positions closed, rest of session)
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): IN THIS PICK on LOSS.MF1. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```
