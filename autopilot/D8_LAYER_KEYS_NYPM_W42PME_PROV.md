**PROVISIONAL: L6M ONLY, NO WALK-FORWARD, PRIOR YEARS PENDING, NULL PENDING. NOT A GATED PICK. the delivered NY PM stack (STKd893133bd8, BF2_JT9 / JT209) stays the delivered pick until a gated pick exists.**

# D8_LAYER_KEYS_NYPM_W42PME_PROV - NYPM stack TL3_ALN_NP_STKd8w42pme: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-25 15:49Z by W-LAYERS2 from BAREFIT_NP_STKd8w42pme_PROV.md (pick TL3_SR_NP_STKd8w42pme_BF1_JT9), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L6d238076_R0_F90_30    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 1201-1559 ET
MF2 = L8dff280f_R0_P90    stop 90 pts / target 90 pts ; R per lot = $1800 ; entries 1200-1800 ET
median book R (STK) = 90 pts x $20 = $1800 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_NP_STKd8w42pme_BF1_JT9 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF2 = FR_LOSS8    # W-FASTR pick: no-follow-through: < +5 pts after 20 min
LOCK.MF2 = LK9    # lock at 80% -> stop to entry+20 pts
TAKE.MF2 = TK3    # take at 50% of target after 30 s without a new extreme
ZONE.MF2 = ZONE4    # zone no-trade set MF2 Skip within 20 pts
DLA = DLA9    # per-book day loss halt at -2R (new entries only, open position runs, rest of session)
DLB = DLB5    # stack day loss halt at -$6000 per lot per book (open P&L counts, all books halted, positions closed, rest of session)
DLC = DLC2    # per-book halt after 3 consecutive full-stop losses (rest of session)
SC = SC1    # StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots)
BL = BL1    # BookLock arm 1.5R give-back 33%
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```
