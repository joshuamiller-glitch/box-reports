# D8_LAYER_KEYS_ASIA_J502_JT6 - Asia stack TL3_ALN_AS_L385f4f2e_P2JCX502: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-24 15:58Z by W-LAYERS2 from BAREFIT_AS_L385f4f2e_P2JCX502_L2.md (pick TL3_SR_AS_L385f4f2e_P2JCX502_BF2_JT6), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L385f4f2e_CX502    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0001-2359 ET
median book R (STK) = 60 pts x $20 = $1200 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_AS_L385f4f2e_P2JCX502_BF2_JT6 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOCK.MF1 = LK4    # lock at 65% -> stop to entry+0 pts
TAKE.MF1 = FR_TAKE2    # W-FASTR pick: take 95%/30 s
ZONE.MF1 = ZONE2    # zone no-trade set MF1 Half within 30 pts
SC = SC2    # StackCut share 50% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots)
BL = BL4    # BookLock arm 2.0R give-back 33%
CAP = CAP2    # per-book day profit stop +7.5R ($18000)
STK = STK1    # WHOLE-STACK day profit stop +4R of one book ($9600)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS2    # no-trade-set rule dropped
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```
