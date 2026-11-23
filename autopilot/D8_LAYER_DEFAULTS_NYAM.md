# D8_LAYER_DEFAULTS_NYAM - fitted layer picks of the NY AM stack TL3_ALN_NY_STKd8b76ecd35 per lot basis (truly-bare all-layers joint, verdict 2026-11-23 11:08Z)

Source: BAREFIT_NY_STKd8b76ecd35.md; code meanings: D8_LAYER_KEYS_NYAM.md (+ D8_LAYER_KEYS.md for the shared mechanisms). Written 2026-11-23 16:12Z by W-LAYERS2.

**RECOMMENDATION for an account running 2 lots per book: follow the 2-LOT pick (BF2_JT68).** Reason: the picks are lot-basis specific because the rounding rules change with the lots (StackCut share q = ceil(pos x share): the whole position at 1 lot, 1 of 2 at 2 lots, 2 of 4 at 4; sizer and no-trade-set halving act only above 1 lot and halve 2 -> 1 but 4 -> 2; every dollar rule is k x R x lots), and the 2-lot pick has the best evidence (walk-forward 0.838, persistence 0.914, year bands RED/GREEN/GREEN) while the 4-lot pick has the same walk-forward and 0.882 and the 1-lot pick the weakest (0.628, AMBER/AMBER/RED). Asia followed the 4-lot pick because that panel runs 4 lots per book; here the account is 2 lots, so use BF2_JT68. Status of all three: WEAK-BUT-POSITIVE leaning to LEAD at 2 and 4 lots, NOT PROVEN until the null lands; the panel default stays layers OFF (bare = what was tested) until Josh chooses.

## 1 lot(s) per book - TL3_SR_NY_STKd8b76ecd35_BF1_JT22

walk-forward 0.628 over 78 periods; fixed-pick persistence 0.645; year bands vs bare AMBER/AMBER/RED;; null: pending

| window | truly bare | pick |
|---|---|---|
| L6M | 4372 / -15007 / -14493 / -7608 / 7495 | 2102 / -7234 / -3161 / -4849 / 6035 |
| L3M | 3540 / -9765 / -3445 / -7157 / 6747 | 2029 / -5471 / -3138 / -4849 / 4502 |
| 2023 | 11117 / -31342 / -13132 / -12462 / 2016 | 9580 / -23783 / -10375 / -9895 / 1441 |
| 2024 | 10668 / -31020 / -19393 / -10792 / 2349 | 9067 / -28109 / -11458 / -9446 / 1459 |
| 2025 | 15583 / -59504 / -30226 / -17236 / 3561 | 14575 / -48045 / -20849 / -14932 / 1885 |

```
LOSS.MF1 = CU3    # loss cut when unrealised <= -72 pts (0.8 x stop)
LOCK.MF1 = LK1    # lock at 50% -> stop to entry+0 pts
TAKE.MF1 = TK2    # take at 50% of target after 15 s without a new extreme
ZONE.MF1 = OFF
LOSS.MF2 = CX3    # context cut (fresh) at -48 pts
LOCK.MF2 = OFF
TAKE.MF2 = TK6    # take at 65% of target after 30 s without a new extreme
ZONE.MF2 = OFF
LOSS.MF3 = CU4    # loss cut when unrealised <= -120 pts (1.0 x stop)
LOCK.MF3 = LK5    # lock at 65% -> stop to entry+10 pts
TAKE.MF3 = FR_TAKE6    # W-FASTR pick: lock 80% -> +30
ZONE.MF3 = ZONE2    # zone no-trade set MF3 Half within 30 pts
LOSS.MF4 = OFF
LOCK.MF4 = OFF
TAKE.MF4 = SHV2    # target shave MF4 4 ticks
ZONE.MF4 = ZONE5    # zone no-trade set MF4 Skip within 30 pts
LOSS.MF5 = STC3    # state-cut cell MF5 mult 5.0
LOCK.MF5 = LK8    # lock at 80% -> stop to entry+10 pts
TAKE.MF5 = OFF
ZONE.MF5 = ZONE6    # zone no-trade set MF5 Skip within 50 pts
SC = OFF
BL = BL1    # BookLock arm 1.5R give-back 33%
CAP = CAP2    # per-book day profit stop +7.5R ($9000)
STK = OFF
DLA = DLA5    # per-book day loss halt at -3R (open P&L counts, close the position, halt rest of session)
DLB = OFF
DLC = DLC2    # per-book halt after 3 consecutive full-stop losses (rest of session)
```

## 2 lot(s) per book - TL3_SR_NY_STKd8b76ecd35_BF2_JT68

walk-forward 0.838 over 80 periods; fixed-pick persistence 0.914; year bands vs bare RED/GREEN/GREEN;; null: pending

| window | truly bare | pick |
|---|---|---|
| L6M | 4610 / -17430 / -16945 / -7910 / 7061 | 1760 / -5109 / -2275 / -2752 / 3038 |
| L3M | 3635 / -9728 / -3473 / -7119 / 6339 | 2091 / -5109 / -2275 / -2752 / 2014 |
| 2023 | 11154 / -31407 / -13155 / -12475 / 1954 | 7525 / -20192 / -8146 / -5447 / 869 |
| 2024 | 11309 / -32917 / -19403 / -10812 / 2270 | 4335 / -11167 / -7074 / -4246 / 1266 |
| 2025 | 15615 / -59614 / -30363 / -17271 / 3476 | 7395 / -26262 / -12856 / -9596 / 1686 |

```
LOSS.MF1 = CU2    # loss cut when unrealised <= -54 pts (0.6 x stop)
LOCK.MF1 = LK1    # lock at 50% -> stop to entry+0 pts
TAKE.MF1 = OFF
ZONE.MF1 = ZONE6    # zone no-trade set MF1 Skip within 50 pts
LOSS.MF2 = CX1    # context cut (fresh) at -24 pts
LOCK.MF2 = OFF
TAKE.MF2 = TK1    # take at 50% of target after 5 s without a new extreme
ZONE.MF2 = ZONE2    # zone no-trade set MF2 Half within 30 pts
LOSS.MF3 = CU4    # loss cut when unrealised <= -120 pts (1.0 x stop)
LOCK.MF3 = OFF
TAKE.MF3 = OFF
ZONE.MF3 = ZONE3    # zone no-trade set MF3 Half within 50 pts
LOSS.MF4 = CU4    # loss cut when unrealised <= -45 pts (1.0 x stop)
LOCK.MF4 = LK7    # lock at 80% -> stop to entry+0 pts
TAKE.MF4 = SHV2    # target shave MF4 4 ticks
ZONE.MF4 = OFF
LOSS.MF5 = OFF
LOCK.MF5 = LK8    # lock at 80% -> stop to entry+10 pts
TAKE.MF5 = FR_TAKE4    # W-FASTR pick: lock 80% -> +10
ZONE.MF5 = ZONE4    # zone no-trade set MF5 Skip within 20 pts
SC = OFF
BL = BL1    # BookLock arm 1.5R give-back 33%
CAP = OFF
STK = STK3    # WHOLE-STACK day profit stop +8R of one book ($19200)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS1    # no-trade-set halving 0.5 (today's rule)
DLA = OFF
DLB = DLB6    # stack day loss halt at -$8000 per lot per book (open P&L counts, all books halted, positions closed, rest of session)
DLC = DLC10    # per-book pause 120 min after 3 consecutive full-stop losses, then re-arm
```

## 4 lot(s) per book - TL3_SR_NY_STKd8b76ecd35_BF4_JT15

walk-forward 0.838 over 80 periods; fixed-pick persistence 0.882; year bands vs bare RED/GREEN/GREEN;; null: pending

| window | truly bare | pick |
|---|---|---|
| L6M | 4889 / -19461 / -17056 / -8001 / 6433 | 1733 / -6632 / -3040 / -3267 / 2532 |
| L3M | 3663 / -9796 / -3618 / -7169 / 6269 | 1752 / -4667 / -3040 / -3267 / 1925 |
| 2023 | 11176 / -31494 / -13161 / -12437 / 1911 | 11959 / -29961 / -8381 / -4380 / 572 |
| 2024 | 11708 / -33452 / -19500 / -10999 / 2082 | 3862 / -11795 / -6297 / -4249 / 1447 |
| 2025 | 15774 / -59782 / -30496 / -17249 / 3266 | 7685 / -23403 / -10215 / -7279 / 1457 |

```
LOSS.MF1 = OFF
LOCK.MF1 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF1 = SHV1    # target shave MF1 2 ticks
ZONE.MF1 = ZONE6    # zone no-trade set MF1 Skip within 50 pts
LOSS.MF2 = CX1    # context cut (fresh) at -24 pts
LOCK.MF2 = LK6    # lock at 65% -> stop to entry+20 pts
TAKE.MF2 = TK6    # take at 65% of target after 30 s without a new extreme
ZONE.MF2 = OFF
LOSS.MF3 = OFF
LOCK.MF3 = OFF
TAKE.MF3 = FR_TAKE6    # W-FASTR pick: lock 80% -> +30
ZONE.MF3 = ZONE3    # zone no-trade set MF3 Half within 50 pts
LOSS.MF4 = STC2    # state-cut cell MF4 arm 60.0
LOCK.MF4 = OFF
TAKE.MF4 = OFF
ZONE.MF4 = OFF
LOSS.MF5 = STC1    # state-cut cell MF5 arm 30.0
LOCK.MF5 = LK8    # lock at 80% -> stop to entry+10 pts
TAKE.MF5 = SHV2    # target shave MF5 4 ticks
ZONE.MF5 = ZONE4    # zone no-trade set MF5 Skip within 20 pts
SC = SC2    # StackCut share 50% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots)
BL = BL7    # BookLock arm 3.0R give-back 33%
CAP = CAP1    # per-book day profit stop +5R ($24000)
STK = STK1    # WHOLE-STACK day profit stop +4R of one book ($19200)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = OFF
DLA = OFF
DLB = OFF
DLC = DLC10    # per-book pause 120 min after 3 consecutive full-stop losses, then re-arm
```

