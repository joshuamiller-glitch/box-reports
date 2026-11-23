# D8_LAYER_DEFAULTS_ASIA_JT143 - Asia stack TL3_ALN_AS_STKd8106b26ef: panel values at the 2-lot pick TL3_SR_AS_STKd8106b26ef_BF2_JT143

Written 2026-11-23 18:35Z by W-LAYERS2. The pick applies at every account size (dollar rules scale per lot / per R, see the keys page). Status: walk-forward 0.875 over 80 periods; fixed-pick persistence 0.817; year bands vs bare RED/RED/RED;; null: pending (2-lot null run queued, early-stop gate >= 4 of 5).

Cells ulcer / max DD / worst week / worst day / $ per week per lot (2-lot basis).

| window | truly bare | pick |
|---|---|---|
| L6M | 3481 / -10508 / -9931 / -6608 / 10247 | 1323 / -6123 / -2808 / -3317 / 4850 |
| L3M | 3680 / -10508 / -3086 / -6608 / 10033 | 1343 / -6123 / 387 / -3317 / 3767 |
| 2023 | 5307 / -11253 / -7808 / -4738 / 1015 | 3836 / -9640 / -6136 / -3872 / 177 |
| 2024 | 5048 / -18731 / -10393 / -8930 / 1783 | 4383 / -12278 / -6023 / -2903 / 768 |
| 2025 | 6865 / -18734 / -11947 / -12080 / 1758 | 10806 / -18069 / -10905 / -4761 / -55 |

```
LOSS.MF1 = CU4
LOCK.MF1 = LK5
ZONE.MF1 = ZONE5
LOSS.MF2 = STC4    # STC: needs cancel tape
LOCK.MF2 = LK9
LOSS.MF3 = STC1    # STC: needs cancel tape
LOCK.MF3 = LK3
TAKE.MF3 = TK1
LOSS.MF4 = CU2
LOCK.MF4 = LK2
TAKE.MF4 = NRT2
LOCK.MF5 = LK6
TAKE.MF5 = NRT2
ZONE.MF5 = ZONE2
BL = BL1
CAP = CAP8
SZW = SZW3
NTS = NTS1
CG = CGB2
DLC = DLC12
```
