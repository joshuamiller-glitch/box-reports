# D8_LAYER_DEFAULTS_NYAM_NYAMW_JT91 - NYAM stack TL3_ALN_NY_STKd8cd0279ff: panel values at the 2-lot pick TL3_SR_NY_STKd8cd0279ff_BF1_JT91

Written 2026-11-25 01:56Z by W-LAYERS2. The pick applies at every account size (dollar rules scale per lot / per R, see the keys page). Status: walk-forward 0.775 over 80 periods; fixed-pick persistence 0.817; year bands vs bare RED/GREEN/GREEN;; null: pending (2-lot null run queued, early-stop gate >= 4 of 5).

Cells ulcer / max DD / worst week / worst day / $ per week per lot (2-lot basis).

| window | truly bare | pick |
|---|---|---|
| L6M | 28581 / -99970 / -20048 / -83394 / 51363 | 9465 / -25973 / -7960 / -15186 / 17388 |
| L3M | 29290 / -99970 / -16356 / -77369 / 36277 | 8365 / -21737 / -1575 / -11284 / 10992 |
| 2023 | 45201 / -129883 / -50599 / -37003 / 10796 | 70766 / -141822 / -25639 / -14683 / -2150 |
| 2024 | 40989 / -109316 / -87056 / -58165 / 7854 | 12241 / -44894 / -24073 / -18514 / 6015 |
| 2025 | 58108 / -188315 / -117277 / -82641 / 16106 | 22161 / -65610 / -34678 / -20923 / 6606 |

```
LOSS.MF1 = CU4
TAKE.MF1 = SHV2
ZONE.MF1 = ZONE2
LOSS.MF2 = FR_LOSS8
LOCK.MF2 = LK9
ZONE.MF2 = ZONE5
LOSS.MF3 = CU3
TAKE.MF3 = NRT4
ZONE.MF3 = ZONE1
TAKE.MF4 = SHV3
ZONE.MF4 = ZONE5
LOCK.MF5 = LK3
TAKE.MF5 = TK6
LOSS.MF6 = CU2
LOCK.MF6 = LK2
TAKE.MF6 = SHV3
ZONE.MF6 = ZONE6
LOCK.MF7 = LK3
TAKE.MF7 = TK2
LOSS.MF8 = CU3
LOCK.MF8 = LK8
ZONE.MF8 = ZONE2
LOCK.MF9 = LK2
TAKE.MF9 = FR_TAKE1
DLA = DLA9
DLB = DLB9
SC = SC1
BL = BL4
CAP = CAP6
SZW = SZW3
NTS = NTS2
```

## CORRECTION 2026-11-25 (CAP/DLB engine reading) - written 2026-11-25 02:11Z by W-LAYERS2 (documentation only; the history above is not rewritten)
TOP LINE: 8cd0279ff_BF1_JT91: CODING CHANGE: YES: the CAP pair's second side (and the static median-R dollars) must be coded as above; the written named-side value is correct.
**Set TL3_SR_NY_STKd8cd0279ff_BF1_JT91**
- CAP: the set carries the SAME static dollar caps on EVERY book: profit +$48,000, loss -$14,400 (engine day cap sim.py:722-730, once per 1-minute bar, CLOSED day P&L only, closing an open trade with exit name DayHalt; the dollars are k x the MEDIAN book R of $4,800 at this basis, stackrule_gen.py:57 reassigns lots = max(2, ...) before the CAP lambda at :71, so the page wording 'each book's own R' is WRONG for CAP). The page names only ONE side of the pair: the profit rows (CAP1-4) ALSO set the loss cap at 4 R (= $19,200) and the loss rows (CAP5-8) ALSO set the profit cap at 10 R (= $48,000): the other side is part of the tested set and must be coded.
  Own R of the books differs here (own R per book at this basis: 9,600, 4,800, 9,600, 7,200, 2,400, 7,200, 2,400, 1,600, 3,200): the static dollars are NOT scaled per book.
- DLB: lots differ per book ([1.0, 2.0, 4.0]): threshold = -$4,000 x the lots of the smallest-lot book not yet halted (dl_hooks.py:51): see the JT91 readings section.
- FITTED RESULTS DO NOT CHANGE: the fit ran this exact engine code (the numbers on the page already include the static caps, the hidden side of the CAP pair and the DLB checking-book rule); only the written descriptions were incomplete.
- Engine code: sim.py:722-730 (day caps; `if b.day_halt: return` first line), stackrule_gen.py:57 and :71 (CAP dollars), dl_hooks.py:51 (DLB), D8_LAYER_KEYS_NYAM_NYAMW_JT91.md section Relay readings 2026-11-25 02:15Z.
