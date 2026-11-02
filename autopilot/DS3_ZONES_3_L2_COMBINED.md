# DS3_ZONES_3_L2_COMBINED - ZL-3 (ZONES-3 L2 addendum, sections B/C): scoring of order-flow zones, density, confirmed/weak lines, learned rule
ROLLING FILE, written by ZL-3, first version 2026-11-01 ~23:55Z. Research only, post-hoc, Shadow only, NO PASS CLAIMS. Prereg: l2vast/ds3/prereg/ZONES3_L2C_prereg.md (sha256 in DECISIONS.md, logged 22:34Z before any statistic). Code: l2vast/ds3/code/zl3/ (zl3lib.py engine hooks + feature kernel, cells.py cell definitions, runner.py, placebo.py, proxy.py, learned.py, an_s1.py). Results: /mnt/l2/l2vast/ds3_zones3_new/ZL-3/.
**BASE of every table below: stage 1 = D7 v1.2 INTERIM (windows L6M/HOLD/PRE/X'); the v1.3 re-run of stage 2 (conf/weak, density, learned rule) is running and will be added as a section headed `v1.3`.** Windows: new set only (L6M 2026-05..10, HOLD 2025-11..2026-10, PRE, X'); L1M/L2M/MID/L3M columns exist in the stored cells and are in the CSVs but are not selected on.
**COVERAGE.** TAPE streams: new (ZL-2, streams_tape_new, ek to 2026-10-30), all four windows covered. ORDER-BOOK streams: NOT yet available on the new cap at the time of writing (ZL-1 streams_book empty); book-zone cells are therefore NOT scored and no book number is quoted (old-cap book streams end 2026-02-06 and are not used for any new-window cell).

## 1. Method points that change how to read the numbers
* Engine path: zone masks enter D7 v1.2 as `extra_skip` / `extra_mult`; B73/WT through the OTE-62 row kernel with the zone distance; U7 fixed-point warm-started from the base mask (verified identical to the cold start, max |diff| 0.0 on 2 random masks); a cell that changes no base-taken trade is stored as a no-op (identical to the base).
* **Volume trap.** A zone family that fires on 40% of the rows cuts maxDD by roughly 40% by itself (TAPEALL D20: 35,047 rows fired, 7,567 base trades removed, cut L6M/HOLD/PRE/X' +47/+39/+24/+65%). The ranking therefore uses the same-count random-skip placebo (random base-taken rows, same number per book x session, 200 draws; `rank` = share of draws with an average cut over L6M/HOLD/PRE/X' >= observed; computed on the no-interaction proxy that removes the removed trades' base P&L, finalists get engine placebos) and not the raw cut. Proxy vs engine fidelity is checked on the stage-1 cells (proxy_avg vs avg columns in an_*.csv: they differ by lock/U7 interaction; engine numbers are the reported cut columns).
* Mean deltas are all inside MDE (L6M: |d| < MDE in 268 of 268 cells).

## 2. Stage 1 - every tape zone stream and family, AHEAD, fresh, D20 and D40, skip (268 cells, v1.2 interim)
Full table: /mnt/l2/l2vast/ds3_zones3_new/ZL-3/an_jobs_s1tapenew.csv (columns: cut per window from the engine, mean delta and MDE per window, fired rows, base trades removed, placebo rank avg / L6M).
Plain result: **no tape zone stream beats the same-count random-skip placebo by more than chance.** 14 of 268 cells have rank_avg <= 0.05 (13.4 expected by chance), 10 <= 0.025 (6.7 expected). The cells with a non-trivial effect and a low rank:

| cell (AHEAD fresh skip) | fired rows | base trades removed | maxDD cut L6M / HOLD / PRE / X' | d mean L6M (MDE) | placebo rank avg / L6M | label |
|---|---|---|---|---|---|---|
| TPF hvn1 sw1h D20 | 1,148 | 246 | +12 / +12 / +3 / +8% | +399 (2,347) | 0.035 / 0.105 | LEAD (weak: 1 of 268, PRE cut 3%) |
| TLQ SES asia D20 | 1,600 | 207 | +7 / +7 / +14 / +9% | -17 (4,880) | 0.025 / 0.22 | LEAD (weak) |
| TCP hvn2 60d D40 | 371 | 59 | +9 / +9 / +13 / +4% | +394 (1,067) | 0.005 / 0.065 | (tiny volume: 59 trades) |
| TCD divbull D20 | 636 | 89 | +8 / +8 / +4 / +6% | +42 (1,447) | 0.025 / 0.07 | LEAD (weak) |
| TCD divbull D40 | 945 | 161 | +9 / +9 / -19 / +16% | -648 (2,601) | 0.020 / 0.155 | PRE disagrees |

Big raw cuts are volume effects: TAPEALL D20 +47/+39/+24/+65% rank 0.325 (volume effect); TAPEALL D40 +64/+50/-19/+65% rank 0.345; TCD (all) D20 +30/+4/+19/+30% rank 0.25; TVP (volume-profile family) D40 +59/+20/-45/-4% rank 0.77; TLQ (liquidity pools: swing / equal / session / kill-zone highs and lows) cuts L6M negative (-9% D20, -25% D40): consistent with ZL-2's finding that those levels are run-through levels. L6M and HOLD share one maxDD episode, so their columns repeat (cuts differ only where HOLD has a different trough).
RISK-KEEP (L6M cut >= 20% with L6M mean inside MDE, beating the placebo, PRE/X'/HOLD agree): **none** at stage 1. The four rows above are LEADS at most; none passes the robustness standard (leave-one-episode-out, month-block CI, three placebos, D +-25/50%) which is queued for the finalists.
