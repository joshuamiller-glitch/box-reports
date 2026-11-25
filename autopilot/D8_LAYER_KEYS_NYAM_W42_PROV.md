**PROVISIONAL: L6M ONLY, NO WALK-FORWARD, PRIOR YEARS PENDING, NULL PENDING. NOT A GATED PICK. JT91 (STKd8cd0279ff) stays the delivered pick until a gated pick exists.**

# D8_LAYER_KEYS_NYAM_W42_PROV - NYAM stack TL3_ALN_NY_STKd8w42: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-25 12:20Z by W-LAYERS2 from BAREFIT_NY_STKd8w42_PROV.md (pick TL3_SR_NY_STKd8w42_BF1_JT154), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L43f0cbfb.BRS8U_w4_s0    stop 120 pts / target 120 pts ; R per lot = $2400 ; entries 0930-1159 ET
MF2 = B7bfd33b7_w4_s0    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0930-1159 ET
MF3 = Bf428c4a1.BRS8U_w4_s0    stop 120 pts / target 120 pts ; R per lot = $2400 ; entries 0930-1159 ET
MF4 = Le4fede95.BRF90_30_w4_s0    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 0930-1159 ET
MF5 = Lf0346d55.BRP60_w2_s0    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0930-1159 ET
MF6 = L8cfda948.BRF90_30_w4_s0    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 0930-1159 ET
MF7 = L4407508c.BRF120_60_w1_s0    stop 120 pts / target 60 pts ; R per lot = $2400 ; entries 0933-1157 ET
MF8 = Lca8ca9cb_w1_s0    stop 50 pts / target 100 pts ; R per lot = $1000 ; entries 0930-1159 ET
median book R (STK) = 90 pts x $20 = $1800 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_NY_STKd8w42_BF1_JT154 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = CU4    # loss cut when unrealised <= -120 pts (1.0 x stop)
TAKE.MF1 = SHV2    # target shave MF1 4 ticks
ZONE.MF1 = ZONE3    # zone no-trade set MF1 Half within 50 pts
LOSS.MF2 = FR_LOSS7    # W-FASTR pick: no-follow-through: < +10 pts after 20 min
TAKE.MF2 = TK9    # take at 80% of target after 30 s without a new extreme
ZONE.MF2 = ZONE5    # zone no-trade set MF2 Skip within 30 pts
LOCK.MF3 = LK3    # lock at 50% -> stop to entry+20 pts
TAKE.MF3 = NRT2    # near-target latch MF3 X 0.95 stale 20
LOSS.MF4 = FR_LOSS9    # W-FASTR pick: scratch: after -45 exit at -5
LOCK.MF4 = LK1    # lock at 50% -> stop to entry+0 pts
ZONE.MF4 = ZONE1    # zone no-trade set MF4 Half within 10 pts
LOSS.MF5 = CU4    # loss cut when unrealised <= -60 pts (1.0 x stop)
TAKE.MF5 = TK1    # take at 50% of target after 5 s without a new extreme
ZONE.MF5 = ZONE5    # zone no-trade set MF5 Skip within 30 pts
LOCK.MF6 = LK9    # lock at 80% -> stop to entry+20 pts
TAKE.MF6 = SHV3    # target shave MF6 8 ticks
ZONE.MF6 = ZONE3    # zone no-trade set MF6 Half within 50 pts
LOCK.MF7 = LK3    # lock at 50% -> stop to entry+20 pts
TAKE.MF7 = TK2    # take at 50% of target after 15 s without a new extreme
LOSS.MF8 = CX1    # context cut (fresh) at -20 pts
LOCK.MF8 = LK5    # lock at 65% -> stop to entry+10 pts
DLA = DLA9    # per-book day loss halt at -2R (new entries only, open position runs, rest of session)
DLB = DLB11    # stack day loss halt at -$8000 per lot per book (new entries only, open positions run, rest of session)
SC = SC1    # StackCut share 25% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots)
BL = BL6    # BookLock arm 2.0R give-back 67%
STK = STK7    # WHOLE-STACK day loss stop -6R of one book ($36000)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS1    # no-trade-set halving 0.5 (today's rule)
CG = CGB2    # skip after 2 same-side losses (c_gov, governs every new book MF1..MF5)
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```
