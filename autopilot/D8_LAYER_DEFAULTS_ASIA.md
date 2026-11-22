# D8_LAYER_DEFAULTS_ASIA - fitted layer settings for the 5-book Asia stack TL3_ALN_AS_STKd8106b26ef (truly-bare all-layers fit)

Written 2026-11-22 20:47Z by the LEAD from BAREFIT_AS_STKd8106b26ef.md (verdict 20:45Z, W-LAYERS joint stage; prior-year bare bases added 20:34-20:45Z). Source of truth: that page. This file is OUTSIDE the AUTO:LAYERS markers on purpose (the generator rewrites that block).

**STATUS: WEAK-BUT-POSITIVE / BEST-AVAILABLE-NOT-PROVEN.** Every joint best lowers the last-6-month drawdown a lot and costs dollars; prior years are RED vs bare on the page bands at every lot basis; the search-aware null for the joint pick is still pending. Josh rule: every layer stays ON as a layer to fit; the best setting per layer is delivered and labelled; none/bare is the reference row. The D8 panel default stays bare (layers switched off = what was tested) until Josh chooses; the settings below are the candidates to switch on.

Cells: ulcer / max DD / worst week / worst day / $ per week, per lot (L6M window = last 6 months).

**CG NOT FITTED on new books until done (W-LAYERS2 21:30Z): the c_gov hook of the stack set governs tag P7 only, so every CG row reads zero change and CG1 in any joint pick below is a NO-OP. Fix in progress (gov_book for MF1..MF5); do not build CG from this file.**

## 1 lot(s) per book

| window | truly bare | best joint |
|---|---|---|
| L6M | 3046 / -9450 / -4971 / -6578 / 10834 | 1827 / -5422 / -1892 / -5259 / 7645 |
| L3M | 3375 / -9283 / -1858 / -6578 / 10600 | 1715 / -5422 / -463 / -4244 / 6646 |
| 2023 | 5200 / -11178 / -7756 / -4718 / 1042 | 8030 / -15556 / -7772 / -7029 / 381 |
| 2024 | 4545 / -16311 / -8171 / -8853 / 1917 | 4558 / -12014 / -5882 / -4649 / 1290 |
| 2025 | 6567 / -17403 / -9888 / -11445 / 1982 | 13198 / -26467 / -12614 / -6812 / 762 |

walk-forward vs bare among combos 0.600 over 80 periods; fixed-pick persistence 0.581; year bands vs bare RED/RED/RED;

Best joint combo TL3_SR_AS_STKd8106b26ef_BF1_JT57 (keys = layer.factor):
```
LOCK.MF1 = LK2
TAKE.MF1 = TK10
ZONE.MF1 = ZONE6
ZONE.MF2 = ZONE1
LOSS.MF3 = CU2
LOCK.MF3 = LK2
TAKE.MF3 = TK1
ZONE.MF3 = ZONE5
LOSS.MF4 = STC1
LOCK.MF4 = LK1
TAKE.MF4 = TK12
ZONE.MF4 = ZONE2
ZONE.MF5 = ZONE1
SC = SC1
BL = BL1
CAP = CAP6
STK = STK4
CG = CG2
```

Best setting of each layer ALONE (screen, L6M):
```
LOSS.MF1 = STC4  # state-cut cell MF1 mult 15.0  d_ulcer -6 d_$/wk -55
LOCK.MF1 = LK2  # lock at 50% -> stop to entry+10 pts  d_ulcer -286 d_$/wk +345
TAKE.MF1 = TK10  # take at 95% of target after 5 s without a new extreme  d_ulcer -66 d_$/wk +309
ZONE.MF1 = ZONE6  # zone no-trade set MF1 Skip within 50 pts  d_ulcer -360 d_$/wk -786
LOSS.MF2 = CU4  # loss cut when unrealised <= -60 pts (1.0 x stop)  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
LOCK.MF2 = LK6  # lock at 65% -> stop to entry+20 pts  d_ulcer -148 d_$/wk -126
TAKE.MF2 = TK4  # take at 65% of target after 5 s without a new extreme  d_ulcer -56 d_$/wk -46
ZONE.MF2 = ZONE1  # zone no-trade set MF2 Half within 10 pts  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
LOSS.MF3 = CU2  # loss cut when unrealised <= -36 pts (0.6 x stop)  d_ulcer -106 d_$/wk -497
LOCK.MF3 = LK2  # lock at 50% -> stop to entry+10 pts  d_ulcer +47 d_$/wk -543  WEAK (fails 15% guard)
TAKE.MF3 = TK2  # take at 50% of target after 15 s without a new extreme  d_ulcer -23 d_$/wk -522
ZONE.MF3 = ZONE6  # zone no-trade set MF3 Skip within 50 pts  d_ulcer -75 d_$/wk -424
LOSS.MF4 = CU2  # loss cut when unrealised <= -36 pts (0.6 x stop)  d_ulcer -316 d_$/wk +494
LOCK.MF4 = LK2  # lock at 50% -> stop to entry+10 pts  d_ulcer -36 d_$/wk -790
TAKE.MF4 = TK1  # take at 50% of target after 5 s without a new extreme  d_ulcer -1 d_$/wk -1551  WEAK (fails 15% guard)
ZONE.MF4 = ZONE1  # zone no-trade set MF4 Half within 10 pts  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
LOSS.MF5 = CU4  # loss cut when unrealised <= -30 pts (1.0 x stop)  d_ulcer -0 d_$/wk +1
LOCK.MF5 = LK6  # lock at 65% -> stop to entry+20 pts  d_ulcer +372 d_$/wk +161  WEAK (fails 15% guard)
TAKE.MF5 = NRT2  # near-target latch MF5 X 0.95 stale 20  d_ulcer -310 d_$/wk -1499
ZONE.MF5 = ZONE1  # zone no-trade set MF5 Half within 10 pts  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
SC = SC1  # StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots)  d_ulcer +1700 d_$/wk -1686  WEAK (fails 15% guard)
BL = BL1  # BookLock arm 1.5R give-back 33%  d_ulcer -1180 d_$/wk -1290
CAP = CAP8  # per-book day loss stop -6R ($7200)  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
STK = STK3  # WHOLE-STACK day profit stop +8R of one book ($9600)  d_ulcer -0 d_$/wk -545
CG = CG1  # skip after 1 same-side losses (c_gov)  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
```

## 2 lot(s) per book

| window | truly bare | best joint |
|---|---|---|
| L6M | 3481 / -10508 / -9931 / -6608 / 10247 | 1367 / -4347 / -1830 / -3817 / 4925 |
| L3M | 3680 / -10508 / -3086 / -6608 / 10033 | 1006 / -3214 / 423 / -2338 / 4431 |
| 2023 | 5307 / -11253 / -7808 / -4738 / 1015 | 4844 / -9951 / -5467 / -4594 / 158 |
| 2024 | 5048 / -18731 / -10393 / -8930 / 1783 | 4450 / -12346 / -5401 / -3836 / 851 |
| 2025 | 6865 / -18734 / -11947 / -12080 / 1758 | 10979 / -24388 / -10670 / -5674 / 266 |

walk-forward vs bare among combos 0.850 over 80 periods; fixed-pick persistence 0.817; year bands vs bare RED/RED/RED;

Best joint combo TL3_SR_AS_STKd8106b26ef_BF2_JT19 (keys = layer.factor):
```
LOSS.MF1 = CU4
TAKE.MF1 = TK10
ZONE.MF1 = ZONE6
LOSS.MF2 = CU4
TAKE.MF2 = NRT4
ZONE.MF2 = ZONE1
LOCK.MF3 = LK2
TAKE.MF3 = TK1
LOSS.MF4 = CU2
TAKE.MF4 = NRT4
ZONE.MF4 = ZONE3
LOCK.MF5 = LK6
TAKE.MF5 = NRT2
SC = SC1
BL = BL2
CAP = CAP8
SZW = SZW3
NTS = NTS2
```

Best setting of each layer ALONE (screen, L6M):
```
LOSS.MF1 = CU4  # loss cut when unrealised <= -40 pts (1.0 x stop)  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
LOCK.MF1 = LK4  # lock at 65% -> stop to entry+0 pts  d_ulcer -405 d_$/wk +750
TAKE.MF1 = TK10  # take at 95% of target after 5 s without a new extreme  d_ulcer -75 d_$/wk +608
ZONE.MF1 = ZONE5  # zone no-trade set MF1 Skip within 30 pts  d_ulcer -1042 d_$/wk +25
LOSS.MF2 = STC4  # state-cut cell MF2 mult 15.0  d_ulcer -46 d_$/wk +68
LOCK.MF2 = LK6  # lock at 65% -> stop to entry+20 pts  d_ulcer -83 d_$/wk -252
TAKE.MF2 = NRT4  # near-target latch MF2 X 0.95 givep 0.1  d_ulcer -327 d_$/wk -4
ZONE.MF2 = ZONE2  # zone no-trade set MF2 Half within 30 pts  d_ulcer -38 d_$/wk -416
LOSS.MF3 = STC1  # state-cut cell MF3 arm 30.0  d_ulcer -480 d_$/wk -607
LOCK.MF3 = LK2  # lock at 50% -> stop to entry+10 pts  d_ulcer +95 d_$/wk -1012  WEAK (fails 15% guard)
TAKE.MF3 = TK2  # take at 50% of target after 15 s without a new extreme  d_ulcer -48 d_$/wk -981
ZONE.MF3 = ZONE6  # zone no-trade set MF3 Skip within 50 pts  d_ulcer -113 d_$/wk -672
LOSS.MF4 = CU2  # loss cut when unrealised <= -36 pts (0.6 x stop)  d_ulcer -842 d_$/wk +1095
LOCK.MF4 = LK2  # lock at 50% -> stop to entry+10 pts  d_ulcer -231 d_$/wk -1812
TAKE.MF4 = NRT4  # near-target latch MF4 X 0.95 givep 0.1  d_ulcer -138 d_$/wk -380
ZONE.MF4 = ZONE2  # zone no-trade set MF4 Half within 30 pts  d_ulcer -105 d_$/wk -823
LOSS.MF5 = STC2  # state-cut cell MF5 arm 60.0  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
LOCK.MF5 = LK6  # lock at 65% -> stop to entry+20 pts  d_ulcer +435 d_$/wk +678  WEAK (fails 15% guard)
TAKE.MF5 = TK7  # take at 80% of target after 5 s without a new extreme  d_ulcer -1004 d_$/wk -1572
ZONE.MF5 = ZONE3  # zone no-trade set MF5 Half within 50 pts  d_ulcer -421 d_$/wk -344
SC = SC1  # StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots)  d_ulcer -271 d_$/wk -651
BL = BL1  # BookLock arm 1.5R give-back 33%  d_ulcer -2722 d_$/wk -1886
CAP = CAP6  # per-book day loss stop -3R ($7200)  d_ulcer -198 d_$/wk -324  WEAK (fails 15% guard)
STK = STK4  # WHOLE-STACK day profit stop +12R of one book ($28800)  d_ulcer +0 d_$/wk -838  WEAK (fails 15% guard)
SZW = SZW3  # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1  d_ulcer -2989 d_$/wk -6857
NTS = NTS1  # no-trade-set halving 0.5 (today's rule)  d_ulcer -783 d_$/wk -550
CG = CG1  # skip after 1 same-side losses (c_gov)  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
```

## 4 lot(s) per book

| window | truly bare | best joint |
|---|---|---|
| L6M | 3922 / -13091 / -10215 / -8185 / 9653 | 1578 / -4578 / -2508 / -4376 / 5348 |
| L3M | 4215 / -13091 / -5657 / -6646 / 9824 | 1330 / -4208 / -2508 / -2859 / 4962 |
| 2023 | 5154 / -11587 / -6684 / -4763 / 969 | 4994 / -9741 / -5511 / -4948 / 199 |
| 2024 | 5231 / -19296 / -10562 / -9080 / 1668 | 4479 / -12147 / -5483 / -3964 / 936 |
| 2025 | 8145 / -22961 / -16183 / -11899 / 1317 | 9328 / -19470 / -9278 / -6117 / 519 |

walk-forward vs bare among combos 0.912 over 80 periods; fixed-pick persistence 0.914; year bands vs bare RED/RED/RED;

Best joint combo TL3_SR_AS_STKd8106b26ef_BF4_JT1 (keys = layer.factor):
```
LOSS.MF1 = CU4
TAKE.MF1 = SHV2
ZONE.MF1 = ZONE5
LOCK.MF2 = LK9
TAKE.MF2 = NRT1
LOSS.MF3 = CU2
LOCK.MF3 = LK7
ZONE.MF3 = ZONE6
LOSS.MF4 = CU3
TAKE.MF4 = NRT4
ZONE.MF4 = ZONE3
LOCK.MF5 = LK5
TAKE.MF5 = TK8
SC = SC2
BL = BL2
STK = STK4
SZW = SZW2
CG = CG1
```

Best setting of each layer ALONE (screen, L6M):
```
LOSS.MF1 = CU4  # loss cut when unrealised <= -40 pts (1.0 x stop)  d_ulcer -10 d_$/wk +3
LOCK.MF1 = LK5  # lock at 65% -> stop to entry+10 pts  d_ulcer -1228 d_$/wk +1657
TAKE.MF1 = SHV2  # target shave MF1 4 ticks  d_ulcer -953 d_$/wk +897
ZONE.MF1 = ZONE6  # zone no-trade set MF1 Skip within 50 pts  d_ulcer -2177 d_$/wk -2702
LOSS.MF2 = STC3  # state-cut cell MF2 mult 5.0  d_ulcer -217 d_$/wk -1396
LOCK.MF2 = LK9  # lock at 80% -> stop to entry+20 pts  d_ulcer +62 d_$/wk -304  WEAK (fails 15% guard)
TAKE.MF2 = NRT4  # near-target latch MF2 X 0.95 givep 0.1  d_ulcer -480 d_$/wk -241
ZONE.MF2 = ZONE2  # zone no-trade set MF2 Half within 30 pts  d_ulcer -132 d_$/wk -824
LOSS.MF3 = CU2  # loss cut when unrealised <= -36 pts (0.6 x stop)  d_ulcer -451 d_$/wk -1297
LOCK.MF3 = LK9  # lock at 80% -> stop to entry+20 pts  d_ulcer +461 d_$/wk -812  WEAK (fails 15% guard)
TAKE.MF3 = SHV1  # target shave MF3 2 ticks  d_ulcer +31 d_$/wk -124  WEAK (fails 15% guard)
ZONE.MF3 = ZONE6  # zone no-trade set MF3 Skip within 50 pts  d_ulcer -260 d_$/wk -1320
LOSS.MF4 = CU2  # loss cut when unrealised <= -36 pts (0.6 x stop)  d_ulcer -1479 d_$/wk +2058
LOCK.MF4 = LK2  # lock at 50% -> stop to entry+10 pts  d_ulcer -512 d_$/wk -3632
TAKE.MF4 = NRT4  # near-target latch MF4 X 0.95 givep 0.1  d_ulcer -579 d_$/wk -695
ZONE.MF4 = ZONE2  # zone no-trade set MF4 Half within 30 pts  d_ulcer -525 d_$/wk -1264
LOSS.MF5 = STC1  # state-cut cell MF5 arm 30.0  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
LOCK.MF5 = LK5  # lock at 65% -> stop to entry+10 pts  d_ulcer +1397 d_$/wk +426  WEAK (fails 15% guard)
TAKE.MF5 = TK7  # take at 80% of target after 5 s without a new extreme  d_ulcer -1552 d_$/wk -3303
ZONE.MF5 = ZONE3  # zone no-trade set MF5 Half within 50 pts  d_ulcer -249 d_$/wk -1039
SC = SC2  # StackCut share 50% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots)  d_ulcer -1874 d_$/wk -1602
BL = BL1  # BookLock arm 1.5R give-back 33%  d_ulcer -6720 d_$/wk -2991
CAP = CAP5  # per-book day loss stop -2R ($9600)  d_ulcer -6 d_$/wk -1879
STK = STK4  # WHOLE-STACK day profit stop +12R of one book ($57600)  d_ulcer +0 d_$/wk -911  WEAK (fails 15% guard)
SZW = SZW3  # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1  d_ulcer -7391 d_$/wk -12203
NTS = NTS1  # no-trade-set halving 0.5 (today's rule)  d_ulcer -1101 d_$/wk -1370
CG = CG1  # skip after 1 same-side losses (c_gov)  d_ulcer +0 d_$/wk +0  WEAK (fails 15% guard)
```

