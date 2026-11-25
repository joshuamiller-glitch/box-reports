# D8_LAYER_DEFAULTS_NYPM_STCFREE - NYPM stack TL3_ALN_NP_STKd893133bd8: panel values at the 2-lot pick TL3_SR_NP_STKd893133bd8_BF2_JT209

Written 2026-11-23 20:47Z by W-LAYERS2. The pick applies at every account size (dollar rules scale per lot / per R, see the keys page). Status: walk-forward 0.887 over 80 periods; fixed-pick persistence 0.946; year bands vs bare RED/GREEN/GREEN;; null: pending (2-lot null run queued, early-stop gate >= 4 of 5).

Cells ulcer / max DD / worst week / worst day / $ per week per lot (2-lot basis).

| window | truly bare | pick |
|---|---|---|
| L6M | 2787 / -12129 / -4283 / -8368 / 4368 | 1447 / -4830 / -3644 / -3384 / 2936 |
| L3M | 2072 / -7272 / -4283 / -4369 / 4359 | 966 / -3870 / -3644 / -2664 / 3032 |
| 2023 | 4065 / -15862 / -8512 / -6553 / 1708 | 3117 / -8808 / -6202 / -3113 / 872 |
| 2024 | 10819 / -29376 / -10817 / -13077 / 1258 | 5578 / -17986 / -7305 / -5655 / 1032 |
| 2025 | 6091 / -17988 / -11441 / -12878 / 2112 | 3108 / -9424 / -6903 / -7436 / 1557 |

```
LOSS.MF2 = CU3
LOCK.MF2 = LK5
TAKE.MF2 = SHV1
ZONE.MF2 = ZONE4
LOSS.MF3 = CU4
LOCK.MF3 = LK7
TAKE.MF3 = SHV2
ZONE.MF3 = ZONE1
LOSS.MF4 = CU4
STK = STK6
SZW = SZW3
NTS = NTS2
CG = CGB3
```

## CORRECTION 2026-11-25 (CAP/DLB engine reading) - written 2026-11-25 02:11Z by W-LAYERS2 (documentation only; the history above is not rewritten)
TOP LINE: 93133bd8_BF2_JT209: NO CHANGE to what the page tells the relay to code (this set has no CAP; DLB / STK values are as written).
**Set TL3_SR_NP_STKd893133bd8_BF2_JT209**
- STK (whole-stack day loss stop): static dollars $11,200 on the SUM of the day P&L (closed) of the listed books (lay_hooks.py stack_caps, evaluated in check_limits once per minute); = k x the median book R ($2,800); no per-book scaling; the written value is correct.
- FITTED RESULTS DO NOT CHANGE: the fit ran this exact engine code (the numbers on the page already include the static caps, the hidden side of the CAP pair and the DLB checking-book rule); only the written descriptions were incomplete.
- Engine code: sim.py:722-730 (day caps; `if b.day_halt: return` first line), stackrule_gen.py:57 and :71 (CAP dollars), dl_hooks.py:51 (DLB), D8_LAYER_KEYS_NYAM_NYAMW_JT91.md section Relay readings 2026-11-25 02:15Z.
