# D8_LAYER_KEYS_NYAM_NYAMW_JT91 - NYAM stack TL3_ALN_NY_STKd8cd0279ff: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-25 01:56Z by W-LAYERS2 from BAREFIT_NY_STKd8cd0279ff_L1.md (pick TL3_SR_NY_STKd8cd0279ff_BF1_JT91), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

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

## 2. THE 2-LOT PICK TL3_SR_NY_STKd8cd0279ff_BF1_JT91 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = CU4    # loss cut when unrealised <= -120 pts (1.0 x stop)
TAKE.MF1 = SHV2    # target shave MF1 4 ticks
ZONE.MF1 = ZONE2    # zone no-trade set MF1 Half within 30 pts
LOSS.MF2 = FR_LOSS8    # W-FASTR pick: no-follow-through: < +5 pts after 20 min
LOCK.MF2 = LK9    # lock at 80% -> stop to entry+20 pts
ZONE.MF2 = ZONE5    # zone no-trade set MF2 Skip within 30 pts
LOSS.MF3 = CU3    # loss cut when unrealised <= -96 pts (0.8 x stop)
TAKE.MF3 = NRT4    # near-target latch MF3 X 0.95 givep 0.1
ZONE.MF3 = ZONE1    # zone no-trade set MF3 Half within 10 pts
TAKE.MF4 = SHV3    # target shave MF4 8 ticks
ZONE.MF4 = ZONE5    # zone no-trade set MF4 Skip within 30 pts
LOCK.MF5 = LK3    # lock at 50% -> stop to entry+20 pts
TAKE.MF5 = TK6    # take at 65% of target after 30 s without a new extreme
LOSS.MF6 = CU2    # loss cut when unrealised <= -54 pts (0.6 x stop)
LOCK.MF6 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF6 = SHV3    # target shave MF6 8 ticks
ZONE.MF6 = ZONE6    # zone no-trade set MF6 Skip within 50 pts
LOCK.MF7 = LK3    # lock at 50% -> stop to entry+20 pts
TAKE.MF7 = TK2    # take at 50% of target after 15 s without a new extreme
LOSS.MF8 = CU3    # loss cut when unrealised <= -64 pts (0.8 x stop)
LOCK.MF8 = LK8    # lock at 80% -> stop to entry+10 pts
ZONE.MF8 = ZONE2    # zone no-trade set MF8 Half within 30 pts
LOCK.MF9 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF9 = FR_TAKE1    # W-FASTR pick: take 50%/30 s
DLA = DLA9    # per-book day loss halt at -2R (new entries only, open position runs, rest of session)
DLB = DLB9    # stack day loss halt at -$4000 per lot per book (new entries only, open positions run, rest of session)
SC = SC1    # StackCut share 25% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots)
BL = BL4    # BookLock arm 2.0R give-back 33%
CAP = CAP6    # per-book day loss stop -3R ($14400)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS2    # no-trade-set rule dropped
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```
