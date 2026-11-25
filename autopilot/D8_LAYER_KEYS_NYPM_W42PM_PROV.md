**PROVISIONAL: L6M ONLY, NO WALK-FORWARD, PRIOR YEARS PENDING, NULL PENDING. NOT A GATED PICK. the delivered NY PM stack (STKd893133bd8, BF2_JT9 / JT209) stays the delivered pick until a gated pick exists.**

# D8_LAYER_KEYS_NYPM_W42PM_PROV - NYPM stack TL3_ALN_NP_STKd8w42pm: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-25 16:37Z by W-LAYERS2 from BAREFIT_NP_STKd8w42pm_PROV.md (pick TL3_SR_NP_STKd8w42pm_BF1_JT19), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L6d238076.BRF90_30_w4_s0    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 1201-1559 ET
MF2 = L8dff280f.BRP90_w4_s0    stop 90 pts / target 90 pts ; R per lot = $1800 ; entries 1200-1800 ET
MF3 = L4bdd521a.BRF80_40_w8_s0    stop 80 pts / target 40 pts ; R per lot = $1600 ; entries 1200-1530 ET
MF4 = L8e0bf58c.BRS8U_w4_s0    stop 120 pts / target 120 pts ; R per lot = $2400 ; entries 1200-1559 ET
MF5 = L52359bf4.BRP30_w2_s0    stop 30 pts / target 30 pts ; R per lot = $600 ; entries 1200-1800 ET
median book R (STK) = 90 pts x $20 = $1800 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_NP_STKd8w42pm_BF1_JT19 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = FR_LOSS9    # W-FASTR pick: scratch: after -45 exit at -5
TAKE.MF1 = NRT1    # near-target latch MF1 X 0.90 stale 10
ZONE.MF1 = ZONE1    # zone no-trade set MF1 Half within 10 pts
LOSS.MF2 = CU2    # loss cut when unrealised <= -54 pts (0.6 x stop)
TAKE.MF2 = FR_TAKE4    # W-FASTR pick: lock 80% -> +10
ZONE.MF2 = ZONE1    # zone no-trade set MF2 Half within 10 pts
LOCK.MF3 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF3 = TK6    # take at 65% of target after 30 s without a new extreme
LOSS.MF4 = CU3    # loss cut when unrealised <= -96 pts (0.8 x stop)
TAKE.MF4 = FR_TAKE4    # W-FASTR pick: lock 80% -> +10
ZONE.MF4 = ZONE2    # zone no-trade set MF4 Half within 30 pts
LOCK.MF5 = LK8    # lock at 80% -> stop to entry+10 pts
TAKE.MF5 = SHV2    # target shave MF5 4 ticks
DLA = DLA9    # per-book day loss halt at -2R (new entries only, open position runs, rest of session)
DLB = DLB11    # stack day loss halt at -$8000 per lot per book (new entries only, open positions run, rest of session)
DLC = DLC6    # per-book pause 60 min after 3 consecutive full-stop losses, then re-arm
BL = BL1    # BookLock arm 1.5R give-back 33%
CAP = CAP6    # per-book day loss stop -3R ($21600)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS1    # no-trade-set halving 0.5 (today's rule)
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```
