# DIS-R prereg (S4b), 2026-11-04, written before any DIS-R statistic

Question: does the prior session's last-30-min tape (15:30-16:00 ET) predict the next day's early direction, and can it be used as a side filter or size overlay on the NY-AM books? Shadow only, no PASS claims, no purchases.

dead_lookup (DEAD_CELLS.csv grep): 'prevday_ret|prevclose|prior-day' 0 rows; '15:30' 80 rows and 'last30' 2767 rows (these are 30-s windows and other contexts, none is a prior-day close-flow predictor of the next morning). No stored cell is repeated.

Features (known at 16:00 ET of day D-1; label day D):
- R1 = (close 16:00 - close 15:30) / ATR14(5-min) at 16:00.
- R2 = sum of delta30 sampled every 30 s over 15:30-16:00, divided by the session's traded volume in that window (flow share).
- R3 = z(R1) + z(R2), z over the previous 60 label days.
- R4 = overnight+open gap sign (09:30 open of D vs 16:00 close of D-1) times sign(R3): 'close flow agrees with the gap'.
Targets (day D): T1 = sign(price 10:30 - price 09:35); T2 = sign(price 09:35 - price 09:30 open) (early direction); T3 = gap filled by 10:30 (yes/no).
Scoring: Spearman/AUC per target, OOS accuracy by walk-forward (expanding, 150-day min, 2-day purge), 5-day block permutation p, shifted-feature-day placebo, family max-T over all (feature x target) cells, BH. Windows L1M..X' with the corrected carrying weeks.
Stage 2 gate: the overlay stage runs only if any predictor has OOS accuracy >= 0.55 on T1 with block-permutation p <= .10 in L6M and no sign flip in the 2023-25 window; otherwise the programme closes as 'prediction fact absent' and no overlay is scored.
Stage 2 (if gated in): same books, actions and tolerant gate as DIS-P (autopilot/DIS_P_PREREG.md), predictors R1-R4 in place of P1-P4, entries 09:35-10:30 ET only. Placebos: shifted-feature-day, random same-count rows, random direction with the same up-share. Family max-T >= 100 worlds over every feature x book x action cell, BH, genuine PA9, MDE = 2.8 SE, NOW-ONLY = REGIME.
Tests: stage 1 = 4 features x 3 targets x 1 (sign) = 12 plus 4 walk-forward = 16 cells; stage 2 up to 9 books x 4 x 4 + 32 = 176 more only if gated.
Outputs: ledger DIS_R, rows FADE_ROWS_DISR.md, n_tested DISR_NTESTED.md, interim in DS3_DISCOVER2.md.
