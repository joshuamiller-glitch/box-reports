# D8_LAYER_KEYS_ASIA_BF2_JT19 - Asia stack TL3_ALN_AS_STKd8106b26ef: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-23 18:35Z by W-LAYERS2 from BAREFIT_AS_STKd8106b26ef.md (pick TL3_SR_AS_STKd8106b26ef_BF2_JT19), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = Lb0e6dfa3_R0_F40_80    stop 40 pts / target 80 pts ; R per lot = $800 ; entries 0000-2356 ET
MF2 = L385f4f2e_CX502    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0001-2359 ET
MF3 = L92a90948_CANC    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0000-2359 ET
MF4 = L6b373671_R0_P60    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0001-2359 ET
MF5 = L578701ed_R0_F30_90    stop 30 pts / target 90 pts ; R per lot = $600 ; entries 0000-2359 ET
median book R (STK) = 60 pts x $20 = $1200 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_AS_STKd8106b26ef_BF2_JT19 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = CU4    # loss cut when unrealised <= -40 pts (1.0 x stop)
TAKE.MF1 = TK10    # take at 95% of target after 5 s without a new extreme
ZONE.MF1 = ZONE6    # zone no-trade set MF1 Skip within 50 pts
LOSS.MF2 = CU4    # loss cut when unrealised <= -60 pts (1.0 x stop)
TAKE.MF2 = NRT4    # near-target latch MF2 X 0.95 givep 0.1
ZONE.MF2 = ZONE1    # zone no-trade set MF2 Half within 10 pts
LOCK.MF3 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF3 = TK1    # take at 50% of target after 5 s without a new extreme
LOSS.MF4 = CU2    # loss cut when unrealised <= -36 pts (0.6 x stop)
TAKE.MF4 = NRT4    # near-target latch MF4 X 0.95 givep 0.1
ZONE.MF4 = ZONE3    # zone no-trade set MF4 Half within 50 pts
LOCK.MF5 = LK6    # lock at 65% -> stop to entry+20 pts
TAKE.MF5 = NRT2    # near-target latch MF5 X 0.95 stale 20
SC = SC1    # StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots)
BL = BL2    # BookLock arm 1.5R give-back 50%
CAP = CAP8    # per-book day loss stop -6R ($14400)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS2    # no-trade-set rule dropped
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.
