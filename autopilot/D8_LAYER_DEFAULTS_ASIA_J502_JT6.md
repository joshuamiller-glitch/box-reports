# D8_LAYER_DEFAULTS_ASIA_J502_JT6 - Asia stack TL3_ALN_AS_L385f4f2e_P2JCX502: panel values at the 2-lot pick TL3_SR_AS_L385f4f2e_P2JCX502_BF2_JT6

Written 2026-11-24 15:58Z by W-LAYERS2. The pick applies at every account size (dollar rules scale per lot / per R, see the keys page). Status: walk-forward 0.846 over 78 periods; fixed-pick persistence 0.902; year bands vs bare GREEN/GREEN/GREEN;; null: pending (2-lot null run queued, early-stop gate >= 4 of 5).

Cells ulcer / max DD / worst week / worst day / $ per week per lot (2-lot basis).

| window | truly bare | pick |
|---|---|---|
| L6M | 530 / -1922 / -1617 / -1922 / 2071 | 315 / -1267 / -800 / -1240 / 1259 |
| L3M | 615 / -1922 / -992 / -1922 / 2410 | 373 / -1267 / -102 / -1240 / 1392 |
| 2023 | 2262 / -4724 / -2032 / -1252 / 42 | 1080 / -2148 / -1012 / -625 / 19 |
| 2024 | 4476 / -11457 / -3549 / -1205 / 235 | 2446 / -6496 / -1770 / -1192 / 180 |
| 2025 | 4428 / -10223 / -3912 / -3615 / 160 | 1728 / -5154 / -2200 / -1775 / 159 |

```
LOCK.MF1 = LK4
TAKE.MF1 = FR_TAKE2
ZONE.MF1 = ZONE2
SC = SC2
BL = BL4
CAP = CAP2
STK = STK1
SZW = SZW3
NTS = NTS2
```

**2-LOT NULL (15:45Z, search-aware, best-of the full menu on the L6M screen of J502 alone): FAIL. Real best-of ulcer cut -36.8% vs null draws -67.3 / -35.3 / -46.3% = beats 1 of the 3 draws run (gate >= 4 of 5; stopped after the 2nd miss). Label: WEAK-BUT-POSITIVE (NOT PROVEN): the other gates are clean (walk-forward 0.846, persistence 0.902, bands GREEN / GREEN / GREEN, no STC). BARE vs BARE vs the bare D7 Asia stack (TL3_ALN_AS_STKLIVE_BARE, 1-lot base, scaled to the SAME max drawdown): J502 alone bare per lot L6M 530 / -1,922 / -1,617 / $2,071 vs D7 scaled (k 0.0595) 782 / -1,922 / -1,258 / $337 per wk = 6.1x the dollars at equal max DD; the pick JT6 1,267 DD: $1,259 per wk vs D7 scaled (k 0.0392) $222 = 5.7x.**
