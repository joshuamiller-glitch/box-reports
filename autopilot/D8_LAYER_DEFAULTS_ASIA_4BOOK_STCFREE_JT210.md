# D8_LAYER_DEFAULTS_ASIA_4BOOK_STCFREE_JT210 - Asia stack TL3_ALN_AS_STKd8da2eb47b: panel values at the 2-lot pick TL3_SR_AS_STKd8da2eb47b_BF2_JT210

Written 2026-11-24 16:10Z by W-LAYERS2. The pick applies at every account size (dollar rules scale per lot / per R, see the keys page). Status: walk-forward 0.875 over 80 periods; fixed-pick persistence 0.839; year bands vs bare RED/GREEN/AMBER;; null: pending (2-lot null run queued, early-stop gate >= 4 of 5).

Cells ulcer / max DD / worst week / worst day / $ per week per lot (2-lot basis).

| window | truly bare | pick |
|---|---|---|
| L6M | 2943 / -10556 / -5111 / -6858 / 7217 | 1000 / -3776 / -2249 / -2251 / 3783 |
| L3M | 3470 / -10556 / 456 / -6858 / 6037 | 993 / -3237 / 253 / -2222 / 3017 |
| 2023 | 2891 / -6436 / -3636 / -2866 / 902 | 2382 / -5159 / -2229 / -1430 / 253 |
| 2024 | 5836 / -15782 / -7343 / -5391 / 1187 | 3829 / -10372 / -4591 / -2764 / 674 |
| 2025 | 6236 / -16098 / -10547 / -7190 / 1285 | 3262 / -11848 / -9100 / -4515 / 553 |

```
LOSS.MF1 = CU4
TAKE.MF1 = FR_TAKE4
ZONE.MF1 = ZONE5
LOSS.MF2 = CU4
LOCK.MF2 = LK7
ZONE.MF2 = ZONE2
LOSS.MF3 = CX2
TAKE.MF3 = TK2
ZONE.MF3 = ZONE3
TAKE.MF4 = SHV3
ZONE.MF4 = ZONE4
BL = BL1
CAP = CAP2
SZW = SZW3
NTS = NTS2
CG = CGB1
DLA = DLA11
DLC = DLC3
```

## CORRECTION 2026-11-25 (CAP/DLB engine reading) - written 2026-11-25 02:11Z by W-LAYERS2 (documentation only; the history above is not rewritten)
TOP LINE: da2eb47b_BF2_JT210: CODING CHANGE: YES: the CAP pair's second side (and the static median-R dollars) must be coded as above; the written named-side value is correct.
**Set TL3_SR_AS_STKd8da2eb47b_BF2_JT210**
- CAP: the set carries the SAME static dollar caps on EVERY book: profit +$12,750, loss -$6,800 (engine day cap sim.py:722-730, once per 1-minute bar, CLOSED day P&L only, closing an open trade with exit name DayHalt; the dollars are k x the MEDIAN book R of $1,700 at this basis, stackrule_gen.py:57 reassigns lots = max(2, ...) before the CAP lambda at :71, so the page wording 'each book's own R' is WRONG for CAP). The page names only ONE side of the pair: the profit rows (CAP1-4) ALSO set the loss cap at 4 R (= $6,800) and the loss rows (CAP5-8) ALSO set the profit cap at 10 R (= $17,000): the other side is part of the tested set and must be coded.
  Own R of the books differs here (own R per book at this basis: 1,600, 2,400, 1,800, 1,200): the static dollars are NOT scaled per book.
- FITTED RESULTS DO NOT CHANGE: the fit ran this exact engine code (the numbers on the page already include the static caps, the hidden side of the CAP pair and the DLB checking-book rule); only the written descriptions were incomplete.
- Engine code: sim.py:722-730 (day caps; `if b.day_halt: return` first line), stackrule_gen.py:57 and :71 (CAP dollars), dl_hooks.py:51 (DLB), D8_LAYER_KEYS_NYAM_NYAMW_JT91.md section Relay readings 2026-11-25 02:15Z.
