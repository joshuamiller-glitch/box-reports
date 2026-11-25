# D8_LAYER_DEFAULTS_NYAM_NYAM5R2_JT368 - NYAM stack TL3_ALN_NY_STKd8b76ecd35: panel values at the 2-lot pick TL3_SR_NY_STKd8b76ecd35_BF2_JT368

Written 2026-11-24 21:20Z by W-LAYERS2. The pick applies at every account size (dollar rules scale per lot / per R, see the keys page). Status: walk-forward 0.838 over 80 periods; fixed-pick persistence 0.914; year bands vs bare RED/GREEN/GREEN;; null: pending (2-lot null run queued, early-stop gate >= 4 of 5).

Cells ulcer / max DD / worst week / worst day / $ per week per lot (2-lot basis).

| window | truly bare | pick |
|---|---|---|
| L6M | 4610 / -17430 / -16945 / -7910 / 7061 | 1760 / -5109 / -2275 / -2752 / 3038 |
| L3M | 3635 / -9728 / -3473 / -7119 / 6339 | 2091 / -5109 / -2275 / -2752 / 2014 |
| 2023 | 11154 / -31407 / -13155 / -12475 / 1954 | 7525 / -20192 / -8146 / -5447 / 869 |
| 2024 | 11309 / -32917 / -19403 / -10812 / 2270 | 4335 / -11167 / -7074 / -4246 / 1266 |
| 2025 | 15615 / -59614 / -30363 / -17271 / 3476 | 7395 / -26262 / -12856 / -9596 / 1686 |

```
LOSS.MF1 = CU2
LOCK.MF1 = LK1
ZONE.MF1 = ZONE6
LOSS.MF2 = CX1
TAKE.MF2 = TK1
ZONE.MF2 = ZONE2
LOSS.MF3 = CU4
ZONE.MF3 = ZONE3
LOSS.MF4 = CU4
LOCK.MF4 = LK7
TAKE.MF4 = SHV2
LOCK.MF5 = LK8
TAKE.MF5 = FR_TAKE4
ZONE.MF5 = ZONE4
BL = BL1
STK = STK3
SZW = SZW3
NTS = NTS1
DLA = DLA16
DLB = DLB6
DLC = DLC2
```

**2-LOT NULL, NY AM equal five (21:49Z, search-aware, best-of the full menu incl. DL and CGB on the L6M screen): FAIL. Real best-of ulcer cut -35.0% vs null draws -30.5 / -40.0 / -56.3% = beats 1 of the 3 draws run (gate >= 4 of 5; stopped after the 2nd miss). Label: WEAK-BUT-POSITIVE (NOT PROVEN) for BF2_JT68 / JT368; the other gates are clean (walk-forward 0.838, persistence 0.914, bands RED / GREEN / GREEN, no STC).**

## CORRECTION 2026-11-25 (CAP/DLB engine reading) - written 2026-11-25 02:11Z by W-LAYERS2 (documentation only; the history above is not rewritten)
TOP LINE: b76ecd35_BF2_JT368: NO CHANGE to what the page tells the relay to code (this set has no CAP; DLB / STK values are as written).
**Set TL3_SR_NY_STKd8b76ecd35_BF2_JT368**
- STK (whole-stack day profit stop): static dollars $19,200 on the SUM of the day P&L (closed) of the listed books (lay_hooks.py stack_caps, evaluated in check_limits once per minute); = k x the median book R ($2,400); no per-book scaling; the written value is correct.
- DLB (stack daily-loss halt, Y = $8,000 per lot per book): threshold = -Y x base_qty of the checking book (dl_hooks.py:51); all books carry 2 lots here, so it is -$16,000 in total: the written meaning is correct (equal lots).
- FITTED RESULTS DO NOT CHANGE: the fit ran this exact engine code (the numbers on the page already include the static caps, the hidden side of the CAP pair and the DLB checking-book rule); only the written descriptions were incomplete.
- Engine code: sim.py:722-730 (day caps; `if b.day_halt: return` first line), stackrule_gen.py:57 and :71 (CAP dollars), dl_hooks.py:51 (DLB), D8_LAYER_KEYS_NYAM_NYAMW_JT91.md section Relay readings 2026-11-25 02:15Z.
