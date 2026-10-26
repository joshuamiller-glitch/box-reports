# REPORT Q26 - intraday cross-sectional momentum / reversal across 14 outrights

**Verdict: NO. FOUND 0.** All 12 pre-registered cells fail the clean-only rule (positive weekly Sharpe in both clean halves): clean-span Sharpe -0.61 to -2.66 for every cell. Rule: rank 14 outrights (ES RTY YM GC CL ZN ZB 6E 6J HG SI NG HO RB) by the return from 08:00 ET to 10:30 or 12:00 ET divided by ADR20; long the top-g and short the bottom-g (momentum) or the reverse (reversal), g in {2,3,4}, equal ADR-risk legs ($10,000 of one-ADR risk split across the g legs), entry at the next open, exit at 15:00 ET, 1 tick/side per leg plus $4.36 per contract. 12 cells, 3,423 trading days 2013-2026. PREREG_AUTOPILOT.md 'BATCH 4', Q26.

| cell (window end, direction, g) | clean | half A | half B | 2013-22 net | 2013-22 gross |
|---|---|---|---|---|---|
| 10:30 momentum g=2 / 3 / 4 | -0.61 / -1.05 / -1.25 | -0.72 / -0.70 / -0.85 | -0.50 / -1.33 / -1.58 | -1.21 / -1.42 / -1.82 | +0.51 / +0.44 / +0.24 |
| 10:30 reversal g=2 / 3 / 4 | -2.18 / -2.20 / -2.35 | all negative | all negative | -2.22 / -2.29 / -2.32 | -0.51 / -0.44 / -0.24 |
| 12:00 momentum g=2 / 3 / 4 | -1.00 / -1.33 / -1.52 | -1.03 / -1.13 / -1.54 | -0.98 / -1.49 / -1.50 | -1.60 / -1.87 / -2.10 | +0.63 / +0.57 / +0.58 |
| 12:00 reversal g=2 / 3 / 4 | -2.45 / -2.25 / -2.66 | all negative | all negative | -2.87 / -3.02 / -3.29 | -0.63 / -0.57 / -0.58 |

Reading: momentum carries a small positive gross edge in 2013-2022 (weekly Sharpe +0.24 to +0.63 before cost) and cost (6 legs per day, one tick each side) turns it into -1.2 to -2.1; in the clean span it is negative even before the pair window is read. ERA flag: 'gross-positive, cost-negative pre-2023' for the momentum cells, 'negative pre-2023' for reversal. The pair window was not read (no cell passed selection; the protocol's diagnostic read was not run for this multi-leg portfolio). Look-ahead check: the ranking uses closes at or before the entry minus 1 minute; entry price is the next open; exit 15:00 open.

Code ap_q26_xs.py; data outputs/autopilot/l/q26_cells.csv.

DONE Q26
