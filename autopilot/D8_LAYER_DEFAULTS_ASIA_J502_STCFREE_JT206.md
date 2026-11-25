# D8_LAYER_DEFAULTS_ASIA_J502_STCFREE_JT206 - Asia stack TL3_ALN_AS_L385f4f2e_P2JCX502: panel values at the 2-lot pick TL3_SR_AS_L385f4f2e_P2JCX502_BF2_JT206

Written 2026-11-24 16:10Z by W-LAYERS2. The pick applies at every account size (dollar rules scale per lot / per R, see the keys page). Status: walk-forward 0.846 over 78 periods; fixed-pick persistence 0.902; year bands vs bare GREEN/GREEN/GREEN;; null: pending (2-lot null run queued, early-stop gate >= 4 of 5).

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

## CORRECTION 2026-11-25 (CAP/DLB engine reading) - written 2026-11-25 02:11Z by W-LAYERS2 (documentation only; the history above is not rewritten)
TOP LINE: P2JCX502_BF2_JT206: CODING CHANGE: YES: the CAP pair's second side (and the static median-R dollars) must be coded as above; the written named-side value is correct.
**Set TL3_SR_AS_L385f4f2e_P2JCX502_BF2_JT206**
- CAP: the set carries the SAME static dollar caps on EVERY book: profit +$18,000, loss -$9,600 (engine day cap sim.py:722-730, once per 1-minute bar, CLOSED day P&L only, closing an open trade with exit name DayHalt; the dollars are k x the MEDIAN book R of $2,400 at this basis, stackrule_gen.py:57 reassigns lots = max(2, ...) before the CAP lambda at :71, so the page wording 'each book's own R' is WRONG for CAP). The page names only ONE side of the pair: the profit rows (CAP1-4) ALSO set the loss cap at 4 R (= $9,600) and the loss rows (CAP5-8) ALSO set the profit cap at 10 R (= $24,000): the other side is part of the tested set and must be coded.
- STK (whole-stack day profit stop): static dollars $9,600 on the SUM of the day P&L (closed) of the listed books (lay_hooks.py stack_caps, evaluated in check_limits once per minute); = k x the median book R ($2,400); no per-book scaling; the written value is correct.
- FITTED RESULTS DO NOT CHANGE: the fit ran this exact engine code (the numbers on the page already include the static caps, the hidden side of the CAP pair and the DLB checking-book rule); only the written descriptions were incomplete.
- Engine code: sim.py:722-730 (day caps; `if b.day_halt: return` first line), stackrule_gen.py:57 and :71 (CAP dollars), dl_hooks.py:51 (DLB), D8_LAYER_KEYS_NYAM_NYAMW_JT91.md section Relay readings 2026-11-25 02:15Z.
