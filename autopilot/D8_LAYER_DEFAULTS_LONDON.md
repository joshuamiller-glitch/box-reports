# D8_LAYER_DEFAULTS_LONDON - London stack TL3_ALN_LO_L19201dfc_R0BRF90_30: panel values at the 2-lot pick TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_JT14

Written 2026-11-23 19:38Z by W-LAYERS2. The pick applies at every account size (dollar rules scale per lot / per R, see the keys page). Status: walk-forward 0.775 over 80 periods; fixed-pick persistence 0.796; year bands vs bare AMBER/RED/RED;; null: pending (2-lot null run queued, early-stop gate >= 4 of 5).

Cells ulcer / max DD / worst week / worst day / $ per week per lot (2-lot basis).

| window | truly bare | pick |
|---|---|---|
| L6M | 1329 / -3918 / -2685 / -3315 / 1632 | 883 / -2548 / -1708 / -1437 / 563 |
| L3M | 1528 / -3918 / -2452 / -3315 / 1368 | 764 / -2212 / -1164 / -1337 / 702 |
| 2023 | 1943 / -5248 / -2559 / -1800 / 269 | 1339 / -2628 / -1849 / -1285 / 143 |
| 2024 | 4346 / -11822 / -5813 / -4176 / 257 | 2757 / -5279 / -3942 / -1904 / 42 |
| 2025 | 5379 / -12905 / -4508 / -3012 / 161 | 5422 / -8982 / -3597 / -2718 / 34 |

```
LOSS.MF1 = STC4    # STC: needs cancel tape
LOCK.MF1 = LK3
ZONE.MF1 = ZONE3
SC = SC1
CAP = CAP2
STK = STK2
SZW = SZW2
DLA = DLA4
DLB = DLB3
```

## CORRECTION 2026-11-25 (CAP/DLB engine reading) - written 2026-11-25 02:11Z by W-LAYERS2 (documentation only; the history above is not rewritten)
TOP LINE: 0BRF90_30_BF2_JT14: CODING CHANGE: YES: the CAP pair's second side (and the static median-R dollars) must be coded as above; the written named-side value is correct.
**Set TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_JT14**
- CAP: the set carries the SAME static dollar caps on EVERY book: profit +$27,000, loss -$14,400 (engine day cap sim.py:722-730, once per 1-minute bar, CLOSED day P&L only, closing an open trade with exit name DayHalt; the dollars are k x the MEDIAN book R of $3,600 at this basis, stackrule_gen.py:57 reassigns lots = max(2, ...) before the CAP lambda at :71, so the page wording 'each book's own R' is WRONG for CAP). The page names only ONE side of the pair: the profit rows (CAP1-4) ALSO set the loss cap at 4 R (= $14,400) and the loss rows (CAP5-8) ALSO set the profit cap at 10 R (= $36,000): the other side is part of the tested set and must be coded.
- STK (whole-stack day profit stop): static dollars $21,600 on the SUM of the day P&L (closed) of the listed books (lay_hooks.py stack_caps, evaluated in check_limits once per minute); = k x the median book R ($3,600); no per-book scaling; the written value is correct.
- DLB (stack daily-loss halt, Y = $4,000 per lot per book): threshold = -Y x base_qty of the checking book (dl_hooks.py:51); all books carry 2 lots here, so it is -$8,000 in total: the written meaning is correct (equal lots).
- FITTED RESULTS DO NOT CHANGE: the fit ran this exact engine code (the numbers on the page already include the static caps, the hidden side of the CAP pair and the DLB checking-book rule); only the written descriptions were incomplete.
- Engine code: sim.py:722-730 (day caps; `if b.day_halt: return` first line), stackrule_gen.py:57 and :71 (CAP dollars), dl_hooks.py:51 (DLB), D8_LAYER_KEYS_NYAM_NYAMW_JT91.md section Relay readings 2026-11-25 02:15Z.
