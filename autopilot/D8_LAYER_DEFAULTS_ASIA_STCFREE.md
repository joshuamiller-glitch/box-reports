# D8_LAYER_DEFAULTS_ASIA_STCFREE - Asia stack TL3_ALN_AS_STKd8106b26ef: panel values at the 2-lot pick TL3_SR_AS_STKd8106b26ef_BF2_JT243

Written 2026-11-24 02:00Z by W-LAYERS2. The pick applies at every account size (dollar rules scale per lot / per R, see the keys page). Status: walk-forward 0.838 over 80 periods; fixed-pick persistence 0.817; year bands vs bare RED/RED/RED;; null: pending (2-lot null run queued, early-stop gate >= 4 of 5).

Cells ulcer / max DD / worst week / worst day / $ per week per lot (2-lot basis).

| window | truly bare | pick |
|---|---|---|
| L6M | 3481 / -10508 / -9931 / -6608 / 10247 | 1303 / -5701 / -2582 / -3197 / 4749 |
| L3M | 3680 / -10508 / -3086 / -6608 / 10033 | 1308 / -5701 / -1054 / -2599 / 3590 |
| 2023 | 5307 / -11253 / -7808 / -4738 / 1015 | 4218 / -10489 / -6170 / -4051 / 159 |
| 2024 | 5048 / -18731 / -10393 / -8930 / 1783 | 4312 / -12462 / -6023 / -2893 / 781 |
| 2025 | 6865 / -18734 / -11947 / -12080 / 1758 | 11160 / -19208 / -11625 / -4374 / -53 |

```
LOSS.MF1 = CU4
LOCK.MF1 = LK5
ZONE.MF1 = ZONE5
LOSS.MF2 = CU4
LOCK.MF2 = LK9
LOSS.MF3 = CU2
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

**2-LOT NULL (04:27Z, search-aware, best-of the whole screen menu incl. DL / CGB, 5-book Asia stack, L6M): FAIL. Real best-of ulcer cut -42.9% vs null draws -44.0 / -39.9 / -19.0 / -54.5%: beats 2 of the 4 draws run (gate >= 4 of 5; stopped after the 2nd miss). The Asia layer gains are NOT clearly more than what the same search finds on random-entry books: label WEAK / NOT PROVEN for every Asia layer pick (JT19, JT143, JT243); the panel default stays bare (layers OFF = what was tested) until Josh chooses.**
