# DS3_DIV2_F_NIGHT - NQ and ES night-session map 18:00-09:30 ET and one rule per live window (D3D2F, T-DIVERSIFY-2 section F, 2026-10-28)

Research only. No live/execution/chart change, no purchase or download, no account id. UNTOUCHED (trade date after 2026-02-06) never read: bars are cut inside load() (f_lib.py) and the stack comparator is A's per-trade table cut to label day <= 20260206 (A itself runs to 2026-10-16; I did NOT use the part after the cut). Code `l2vast/ds3/code/dv2f/`, outputs `l2vast/ds3/out/dv2f/`. Prereg `l2vast/ds3/prereg/DVF_prereg.md` sha256 `731fc387eae4417377e5cdf280570ca4c1ed83219dcd8cf4498f890136b3f002` (in DECISIONS.md before scoring); pre-holdout text `autopilot/DS3_DVF_PREHOLD.md` (WFPRE only), one holdout look logged (tracks DS3_DVF and DS3_DVF_SPAN2) before HOLD / X / PRE23 were printed. **Cells: 6 per instrument, F = 12 in total (NQ 6 + ES 6; ES is the registered sibling replication).**

## 0. Verdict

- **0 PASS / 0 CANDIDATE / 12 DEAD of 12; CONFIRMED: none.** No spec is written (no cell is PASS on either instrument).
- **The map shows range and volume at three clocks, direction at only one.** Range/volume jump at the London 08:00 open (2.4x the median window volume, 1.7x the preceding range), at the Tokyo 09:00 JST open (1.5x range), at 08:30 ET (4.3x volume) and at the 18:00 Globex open; 22:30-01:45 ET is dead (volume 0.4-0.7x the night's median window). Signed return is repeatable only in the first 15 minutes after the Tokyo open (short, NQ -1.08 bps t -3.0, ES -0.81 t -2.9, negative in each of 2022, 2023, 2024, 2025) and in the 15 minutes before the London open (02:45 ET, -0.67/-0.71 bps, 4 of 4 years, already scored by D3DVE as DEAD on ES). The Europe-open break and both fades are net negative or inside their MDE.
- **Only NQ AS_SHORT (short the Tokyo-open 15 minutes) is positive in every window** (PRE23 0.019 R, X 0.020, WFPRE 0.032 R [-0.028,0.092] MDE 0.086, HOLD 0.048; every calendar year positive) and beats the random-clock placebo, but the mean is inside its own MDE, it fails beats_a, the stack-add CI, best-of-12 and ES replication (ES mean is negative: the ES tick is 4.5x larger relative to the window range, so the same 0.4 pt gross edge does not cover its cost). Tier DEAD, failed gates beats_a, stack_add_pre, best_of_N, rep. It is the one lead to carry: a gross +1 bp Tokyo-open drift that survives NQ cost, not an established edge.
- **The number: dollars in the stack's 20 worst weeks at 20% risk.** Stack alone -3,534,170 (149 weeks 2023-04-03..2026-02-06). Best cell NQ AS_SHORT adds **+135,073** there (+115,360 of it covariance, the cell's average weekly mean removed), best of 12 chosen on the outcome, tier DEAD. Every cell's own value is in sections 3 and 7.
- The stack's own night P&L (entries 18:00-09:30, A) for comparison: weekly mean +27,122, Sharpe 1.75, maxDD +571,923, worst week -252,568, its own 20 worst weeks -2,951,321; -2,284,360 inside the stack's 20 worst weeks (selected on the whole stack). No cell adds to Sharpe with a CI excluding 0; NQ AS_SHORT is +0.056 marginal Sharpe at 20% with the maxDD +63,630 worse.

## 1. Map (selection span: trade dates 2022-06-01 .. 2025-06-30, 796 trade dates; HOLD and later not read for the map)

15-minute windows by ET wall clock (DST-correct because the windows are ET), signed mean return of (close-open) in bps of the raw price, t of the mean, mean 15-min range in bps, median window volume relative to that night's median window (relv), and the sign of the mean in 2022 (Jun-Dec) / 2023 / 2024 / 2025 (H1). ET windows mix two Asia-open clocks (19:00 EST / 20:00 EDT); the local-clock table below separates them. 62 windows x 2 instruments: with |t| >= 2 expected by chance about 3 per instrument.

| ET slot | NQ mean bps | t | range bps | relv | yrs | ES mean bps | t | range bps | relv | yrs |
|---|---|---|---|---|---|---|---|---|---|---|
| 18:00 | -0.71 | -1.1 | 19.6 | 1.29 | --+- | -0.60 | -1.2 | 14.9 | 1.22 | --+- |
| 18:15 | +0.34 | +1.1 | 10.8 | 0.71 | -++- | +0.48 | +1.9 | 8.4 | 0.70 | ++++ |
| 18:30 | -0.10 | -0.4 | 9.6 | 0.65 | -+-+ | -0.14 | -0.7 | 7.5 | 0.63 | ---+ |
| 18:45 | +0.02 | +0.1 | 8.2 | 0.52 | ++-- | +0.02 | +0.1 | 6.3 | 0.50 | +--+ |
| 19:00 | -0.02 | -0.1 | 10.6 | 0.74 | +--- | -0.08 | -0.3 | 8.1 | 0.72 | +--- |
| 19:15 | -0.08 | -0.3 | 9.4 | 0.64 | -++- | -0.07 | -0.3 | 7.1 | 0.58 | -++- |
| 19:30 | +0.15 | +0.7 | 9.1 | 0.62 | +--+ | +0.13 | +0.7 | 7.0 | 0.57 | +--+ |
| 19:45 | +0.15 | +0.5 | 9.3 | 0.69 | -++- | +0.05 | +0.2 | 7.3 | 0.65 | -++- |
| 20:00 | -0.59 | -1.6 | 13.5 | 1.04 | ---- | -0.44 | -1.6 | 10.2 | 1.07 | ---- |
| 20:15 | +0.40 | +1.3 | 11.2 | 0.90 | +++- | +0.36 | +1.5 | 8.6 | 0.89 | +++- |
| 20:30 | -0.24 | -0.9 | 11.2 | 0.88 | --+- | -0.26 | -1.1 | 8.5 | 0.85 | -+-- |
| 20:45 | +0.25 | +0.9 | 10.2 | 0.77 | +++- | +0.25 | +1.1 | 7.8 | 0.72 | ++++ |
| 21:00 | +0.05 | +0.2 | 10.2 | 0.82 | +-++ | +0.03 | +0.1 | 7.8 | 0.77 | +--+ |
| 21:15 | -0.08 | -0.3 | 10.2 | 0.81 | -++- | -0.19 | -0.9 | 7.8 | 0.77 | -++- |
| 21:30 | +0.34 | +1.0 | 11.1 | 0.87 | +-++ | +0.27 | +1.0 | 8.5 | 0.87 | +-++ |
| 21:45 | +0.41 | +1.6 | 9.3 | 0.71 | ++++ | +0.45 | +2.0 | 7.2 | 0.67 | ++++ |
| 22:00 | -0.25 | -0.9 | 9.4 | 0.72 | -+-+ | -0.17 | -0.8 | 7.2 | 0.68 | -+-+ |
| 22:15 | +0.45 | +1.8 | 8.8 | 0.63 | ++++ | +0.29 | +1.6 | 6.6 | 0.58 | -+++ |
| 22:30 | -0.19 | -0.8 | 8.5 | 0.61 | +--- | -0.09 | -0.5 | 6.5 | 0.55 | +--- |
| 22:45 | +0.09 | +0.5 | 7.6 | 0.53 | +++- | +0.06 | +0.4 | 5.8 | 0.49 | +++- |
| 23:00 | +0.22 | +1.0 | 7.9 | 0.55 | -+++ | +0.33 | +1.9 | 6.0 | 0.52 | ++++ |
| 23:15 | +0.24 | +1.3 | 7.3 | 0.48 | +-++ | +0.22 | +1.5 | 5.5 | 0.46 | +-++ |
| 23:30 | -0.35 | -1.5 | 7.8 | 0.52 | ---- | -0.38 | -2.1 | 5.9 | 0.47 | ---- |
| 23:45 | +0.06 | +0.4 | 6.5 | 0.44 | --++ | +0.08 | +0.7 | 4.9 | 0.40 | --++ |
| 00:00 | +0.04 | +0.2 | 7.7 | 0.48 | --++ | +0.03 | +0.2 | 5.8 | 0.44 | --++ |
| 00:15 | -0.16 | -0.7 | 7.2 | 0.45 | +--- | -0.09 | -0.5 | 5.4 | 0.40 | +-+- |
| 00:30 | +0.05 | +0.3 | 7.6 | 0.50 | ++-+ | +0.19 | +1.2 | 5.6 | 0.43 | ++-+ |
| 00:45 | -0.18 | -1.0 | 7.0 | 0.46 | ---+ | -0.09 | -0.7 | 5.2 | 0.41 | ---+ |
| 01:00 | +0.01 | +0.0 | 9.1 | 0.66 | ---+ | -0.03 | -0.2 | 6.7 | 0.59 | ---+ |
| 01:15 | -0.04 | -0.2 | 8.6 | 0.58 | --+- | -0.14 | -0.7 | 6.4 | 0.53 | --+- |
| 01:30 | +0.04 | +0.1 | 9.6 | 0.67 | --++ | -0.01 | -0.0 | 7.2 | 0.61 | --+- |
| 01:45 | +0.10 | +0.4 | 9.4 | 0.68 | -+-+ | +0.15 | +0.7 | 7.1 | 0.66 | -+-+ |
| 02:00 | -0.27 | -0.8 | 13.1 | 1.10 | ---+ | -0.29 | -1.0 | 10.1 | 1.12 | ---+ |
| 02:15 | +0.20 | +0.6 | 11.4 | 0.93 | +++- | +0.14 | +0.5 | 8.6 | 0.92 | +++- |
| 02:30 | +0.21 | +0.7 | 11.0 | 0.92 | --++ | +0.07 | +0.3 | 8.3 | 0.91 | --++ |
| 02:45 | -0.67 | -2.4 | 11.0 | 0.92 | ---- | -0.71 | -3.2 | 8.4 | 0.95 | ---- |
| 03:00 | +0.21 | +0.4 | 18.7 | 2.10 | ---+ | +0.31 | +0.7 | 14.6 | 2.45 | ---+ |
| 03:15 | +0.39 | +0.9 | 17.0 | 1.71 | +++- | +0.03 | +0.1 | 13.3 | 1.91 | +++- |
| 03:30 | +0.10 | +0.3 | 15.9 | 1.62 | -++- | -0.18 | -0.5 | 12.4 | 1.80 | -++- |
| 03:45 | +0.57 | +1.6 | 14.2 | 1.40 | +++- | +0.36 | +1.3 | 11.0 | 1.52 | +++- |
| 04:00 | -0.01 | -0.0 | 18.0 | 2.11 | -+-+ | +0.26 | +0.8 | 13.3 | 2.12 | -+-+ |
| 04:15 | -0.31 | -0.8 | 14.6 | 1.56 | ---- | -0.22 | -0.8 | 11.2 | 1.61 | ---+ |
| 04:30 | +0.04 | +0.1 | 13.9 | 1.41 | +-++ | +0.18 | +0.6 | 10.9 | 1.50 | +-++ |
| 04:45 | -0.35 | -1.1 | 12.4 | 1.23 | --+- | -0.31 | -1.2 | 9.8 | 1.30 | -+-- |
| 05:00 | -0.45 | -1.5 | 13.0 | 1.30 | ---- | -0.43 | -1.7 | 10.3 | 1.39 | ---- |
| 05:15 | +0.18 | +0.6 | 12.2 | 1.21 | ++-+ | +0.14 | +0.6 | 9.6 | 1.27 | ++-+ |
| 05:30 | +0.09 | +0.3 | 12.1 | 1.17 | --++ | +0.09 | +0.4 | 9.5 | 1.26 | +-++ |
| 05:45 | +0.50 | +1.6 | 11.6 | 1.13 | +++- | +0.30 | +1.2 | 9.1 | 1.24 | +++- |
| 06:00 | -0.25 | -0.7 | 13.3 | 1.32 | ---+ | -0.13 | -0.4 | 10.4 | 1.39 | +--+ |
| 06:15 | -0.13 | -0.3 | 12.1 | 1.14 | +-+- | -0.03 | -0.1 | 9.4 | 1.19 | +-+- |
| 06:30 | +0.13 | +0.4 | 12.8 | 1.24 | --++ | +0.11 | +0.4 | 10.0 | 1.34 | -+++ |
| 06:45 | +0.50 | +1.6 | 12.3 | 1.26 | +++- | +0.44 | +1.7 | 9.7 | 1.36 | ++++ |
| 07:00 | -0.07 | -0.2 | 15.2 | 1.77 | -++- | -0.03 | -0.1 | 11.4 | 1.94 | -++- |
| 07:15 | +0.21 | +0.6 | 13.4 | 1.56 | +++- | +0.05 | +0.2 | 10.4 | 1.68 | +-+- |
| 07:30 | -0.53 | -1.4 | 14.2 | 1.76 | --+- | -0.42 | -1.3 | 11.3 | 2.02 | --+- |
| 07:45 | +0.11 | +0.3 | 13.2 | 1.66 | +--+ | +0.18 | +0.6 | 10.5 | 1.96 | ++-+ |
| 08:00 | -0.22 | -0.6 | 15.6 | 2.34 | -++- | -0.26 | -0.9 | 12.4 | 2.83 | --+- |
| 08:15 | +0.13 | +0.3 | 16.7 | 2.55 | ++-+ | -0.09 | -0.3 | 13.1 | 3.04 | +--+ |
| 08:30 | -0.47 | -0.3 | 34.5 | 4.25 | --++ | -0.20 | -0.2 | 26.9 | 4.93 | -+++ |
| 08:45 | +0.44 | +0.9 | 19.3 | 3.51 | ++-+ | +0.18 | +0.4 | 15.2 | 4.14 | -+-+ |
| 09:00 | +0.06 | +0.1 | 18.5 | 3.90 | --+- | -0.01 | -0.0 | 14.5 | 4.88 | +-+- |
| 09:15 | -0.81 | -1.9 | 18.5 | 5.11 | ---- | -0.34 | -1.0 | 14.6 | 6.72 | --+- |

|t| >= 2 windows: NQ 1 (02:45), ES 3 (21:45, 23:30, 02:45) of 62 each; windows with the same sign in all four years: NQ 8, ES 9 (chance: 2 x 62/16 = 7.75). Reading: the ET-clock direction map is at chance level except 02:45 (NQ and ES, 4/4 years). Range/volume is not: 03:00-04:00 ET 1.4-2.1x relv, 08:30 4.3x/4.9x, 09:15 5.1x/6.7x, 18:00 1.3x, 20:00 1.0x; 22:30-01:45 0.4-0.7x.

Local-clock windows (15-min steps relative to the foreign cash open; the ET time moves with DST). Tokyo 09:00 JST (no DST) and London 08:00 (Frankfurt 09:00 CET is the same instant):

| clock | offset min | NQ mean bps | t | range bps | vol | y22/y23/y24/y25 | ES mean bps | t | range bps | y22/y23/y24/y25 |
|---|---|---|---|---|---|---|---|---|---|---|
| Tokyo | -30 | +0.14 | +0.6 | 9.2 | 759 | -0.0/+0.2/-0.2/+0.9 | +0.11 | +0.6 | 7.0 | +0.1/+0.0/-0.1/+0.7 |
| Tokyo | -15 | +0.37 | +1.5 | 8.9 | 823 | +0.4/+0.2/+0.3/+0.9 | +0.25 | +1.2 | 7.0 | +0.2/+0.0/+0.3/+0.7 |
| Tokyo | +0 | -1.08 | -3.0 | 13.5 | 1,314 | -1.4/-0.9/-0.8/-1.6 | -0.81 | -2.9 | 10.3 | -1.0/-0.6/-0.7/-1.1 |
| Tokyo | +15 | +0.23 | +0.8 | 11.3 | 1,078 | +0.8/-0.1/+0.6/-0.5 | +0.15 | +0.6 | 8.8 | +0.4/+0.0/+0.3/-0.3 |
| Tokyo | +30 | -0.35 | -1.3 | 10.4 | 1,010 | -0.8/-0.3/-0.3/+0.1 | -0.29 | -1.4 | 8.1 | -0.8/-0.2/-0.3/-0.0 |
| Tokyo | +45 | +0.10 | +0.3 | 10.2 | 946 | -0.0/+0.5/+0.0/-0.3 | +0.08 | +0.3 | 7.8 | -0.0/+0.5/-0.1/-0.3 |
| Tokyo | +60 | +0.19 | +0.6 | 11.0 | 1,090 | +1.3/-0.7/-0.1/+1.3 | +0.14 | +0.6 | 8.3 | +0.9/-0.5/-0.1/+1.0 |
| London | -30 | +0.11 | +0.4 | 11.3 | 1,204 | -0.5/+0.0/+1.0/-0.7 | +0.01 | +0.0 | 8.5 | -0.6/+0.0/+0.6/-0.5 |
| London | -15 | -0.75 | -2.7 | 11.1 | 1,164 | -1.2/-0.5/-0.8/-0.7 | -0.73 | -3.3 | 8.5 | -1.1/-0.4/-0.8/-0.7 |
| London | +0 | +0.44 | +0.8 | 19.2 | 2,778 | -0.3/-0.2/-0.4/+4.3 | +0.50 | +1.1 | 15.0 | +0.2/-0.4/-0.1/+3.7 |
| London | +15 | +0.41 | +0.9 | 17.3 | 2,280 | +0.9/+0.6/+0.3/-0.3 | +0.05 | +0.1 | 13.7 | +0.3/+0.2/+0.1/-0.6 |
| London | +30 | +0.17 | +0.4 | 16.0 | 2,193 | -0.9/+0.0/+0.7/+0.8 | -0.12 | -0.4 | 12.6 | -0.9/-0.2/+0.2/+0.3 |
| London | +45 | +0.61 | +1.7 | 14.3 | 1,843 | +1.6/+0.3/+0.5/+0.3 | +0.35 | +1.2 | 11.2 | +1.1/+0.1/+0.5/-0.3 |
| London | +60 | -0.15 | -0.3 | 17.5 | 2,638 | -2.1/+0.8/-0.5/+0.9 | +0.13 | +0.4 | 12.9 | -1.0/+0.6/-0.1/+1.0 |

Tokyo 09:00 JST = 19:00 ET on 340 weekdays and 20:00 ET on 623; London 08:00 = 03:00 ET on 903 weekdays and 04:00 ET on 60 (the 3-4 weeks a year when US and UK clocks differ). Japanese holidays are not removed (the Tokyo window is traded on all weekdays; holiday dilution reduces any real effect).

The Tokyo-clock first 15 minutes (-1.08 bps NQ, t -3.0) is a stronger and cleaner effect than the ET-clock 20:00 slot (-0.59, t -1.6), i.e. the effect is anchored to the Tokyo open, not to a fixed ET time. The ET 02:45 slot is the same effect as London-15 min (-0.75 bps, t -2.7). Previously scored on these windows (cited, not re-run): ES 02:45-03:00 short (D3DVE DR_0165_m, DEAD, WF -$218/wk at $1k risk, gross 0.75x cost), ES 08:30 range break (RG_0510, DEAD); the T-ASIM and T-CZT finals (`DS3_ASIM_FINAL.md`: NQ 30 cells 0 PASS, 03-04 and 09-10 ET windows show no edge over other hours; `DS3_CZT_FINAL.md`: 41 DEAD) are cited for the NQ session-window work and contain no overnight cell scored here.

## 2. Cells (one rule per live window; mechanism and predicted effect are in the prereg)

EU_BRK_k1.0 / k1.5: break of the 02:00-03:00 ET box (London 07:00-08:00), stop-entry, bracket stop = target = k x median box range, flat 08:00 ET. EU_FADE_k1.0: fade the first 30 min of London (03:00-03:30 ET) if the move >= 0.5 median window range, 1.0 bracket, flat +90 min. AS_SHORT: short the Tokyo open for 15 min (stop 1.5 x median 15-min range). AS_FADE_k1.0 / k1.5: fade the first 30 min after the Tokyo open, flat Tokyo 10:30. Fills D3CX conservative (market +1 tick, stops +2, limit 1-tick trade-through), $4.84 RT, one trade per cell per day.

### Verdict table (R = net $ / stop distance $; WFPRE = 2024-02..2025-06 is the pass/fail window; MDE = 2.8 SE)

| inst | cell | tier | WFPRE n (/wk) | WFPRE mean R [CI] (MDE) | HOLD n, mean R [CI] (MDE) | X n, mean R (MDE) | PRE23 mean R | 2x cost WFPRE R | failed gates |
|---|---|---|---|---|---|---|---|---|---|
| NQ | EU_BRK_k1.0 | DEAD | 360 (4.9) | -0.091 [-0.190,0.008] (0.142) | 151, -0.085 [-0.239,0.068] (0.219) | 215, 0.048 (0.186) | -0.029 | -0.118 | mean_up, beats_a, beats_b, cost2x_pre, year_share, stack_add_pre, hold, best_of_N, rep |
| NQ | EU_BRK_k1.5 | DEAD | 360 (4.9) | -0.075 [-0.164,0.015] (0.128) | 151, -0.056 [-0.192,0.080] (0.195) | 215, 0.009 (0.168) | -0.078 | -0.092 | mean_up, beats_a, beats_b, cost2x_pre, year_share, stack_add_pre, hold, best_of_N, rep |
| NQ | EU_FADE_k1.0 | DEAD | 164 (2.2) | -0.005 [-0.127,0.117] (0.174) | 78, -0.099 [-0.289,0.091] (0.271) | 97, -0.004 (0.232) | 0.062 | -0.024 | mean_up, beats_a, beats_b, cost2x_pre, year_share, stack_add_pre, hold, span2, best_of_N, rep |
| NQ | AS_SHORT | DEAD | 364 (4.9) | 0.032 [-0.028,0.092] (0.086) | 157, 0.048 [-0.031,0.127] (0.113) | 216, 0.020 (0.092) | 0.019 | 0.005 | beats_a, stack_add_pre, best_of_N, rep |
| NQ | AS_FADE_k1.0 | DEAD | 153 (2.1) | -0.112 [-0.245,0.021] (0.190) | 69, 0.038 [-0.156,0.233] (0.278) | 77, -0.042 (0.260) | 0.051 | -0.157 | mean_up, beats_a, beats_b, cost2x_pre, year_share, stack_add_pre, span2, best_of_N, rep |
| NQ | AS_FADE_k1.5 | DEAD | 153 (2.1) | -0.036 [-0.144,0.071] (0.154) | 69, 0.035 [-0.131,0.200] (0.237) | 77, -0.022 (0.201) | 0.097 | -0.056 | mean_up, beats_a, beats_b, cost2x_pre, year_share, stack_add_pre, span2, best_of_N, rep |
| ES | EU_BRK_k1.0 | DEAD | 361 (4.9) | -0.164 [-0.266,-0.061] (0.147) | 149, -0.185 [-0.340,-0.030] (0.221) | 214, -0.231 (0.192) | -0.178 | -0.291 | mean_up, beats_a, beats_b, cost2x_pre, year_share, stack_add_pre, hold, span2, best_of_N, rep |
| ES | EU_BRK_k1.5 | DEAD | 361 (4.9) | -0.098 [-0.189,-0.006] (0.131) | 149, -0.128 [-0.264,0.008] (0.195) | 214, -0.067 (0.173) | -0.164 | -0.186 | mean_up, beats_a, beats_b, cost2x_pre, year_share, stack_add_pre, hold, span2, best_of_N, rep |
| ES | EU_FADE_k1.0 | DEAD | 184 (2.5) | -0.073 [-0.190,0.045] (0.167) | 82, -0.239 [-0.415,-0.063] (0.251) | 102, -0.029 (0.232) | -0.008 | -0.148 | mean_up, beats_a, beats_b, cost2x_pre, year_share, stack_add_pre, hold, span2, best_of_N, rep |
| ES | AS_SHORT | DEAD | 364 (4.9) | -0.046 [-0.108,0.017] (0.089) | 157, -0.005 [-0.083,0.073] (0.112) | 216, -0.093 (0.096) | -0.043 | -0.163 | mean_up, cost2x_pre, year_share, stack_add_pre, hold, span2 |
| ES | AS_FADE_k1.0 | DEAD | 165 (2.2) | -0.213 [-0.344,-0.082] (0.187) | 77, -0.019 [-0.198,0.160] (0.256) | 80, -0.141 (0.240) | -0.026 | -0.351 | mean_up, beats_a, beats_b, cost2x_pre, year_share, stack_add_pre, hold, span2, best_of_N, rep |
| ES | AS_FADE_k1.5 | DEAD | 165 (2.2) | -0.109 [-0.214,-0.004] (0.150) | 77, -0.001 [-0.148,0.146] (0.210) | 80, -0.071 (0.190) | 0.011 | -0.199 | mean_up, beats_a, beats_b, cost2x_pre, year_share, stack_add_pre, hold, span2, best_of_N, rep |

best-of-12 null: p95 of the max of the 12 placebo-b WFPRE deviations = 0.098 R/day-basis; gate = observed effect over (b) above it. Gate definitions are in the prereg (PASS = no gate failed; CANDIDATE = only best_of_N; rep = the same cell unchanged on the other instrument has WFPRE, HOLD and X means all > 0).

### Placebos (40 draws each; effect = real minus placebo mean, per-day R basis, day-bootstrap CI; rank = share of draws below the real mean)

| inst | cell | (a) random direction WFPRE: effect [CI] rank | (b) random clock WFPRE: effect [CI] rank | (b) HOLD effect | (b) X effect |
|---|---|---|---|---|---|
| NQ | EU_BRK_k1.0 | -0.076 [-0.179,0.023] r0.05 | -0.064 [-0.171,0.040] r0.07 | -0.076 | 0.120 |
| NQ | EU_BRK_k1.5 | -0.070 [-0.160,0.011] r0.10 | -0.079 [-0.172,0.010] r0.03 | -0.013 | 0.053 |
| NQ | EU_FADE_k1.0 | 0.004 [-0.050,0.057] r0.62 | 0.016 [-0.039,0.069] r0.68 | -0.049 | 0.008 |
| NQ | AS_SHORT | 0.053 [-0.002,0.112] r0.95 | 0.069 [0.011,0.134] r1.00 | 0.095 | 0.078 |
| NQ | AS_FADE_k1.0 | -0.030 [-0.084,0.022] r0.05 | -0.029 [-0.087,0.027] r0.12 | 0.027 | 0.010 |
| NQ | AS_FADE_k1.5 | -0.004 [-0.050,0.040] r0.45 | -0.007 [-0.050,0.037] r0.38 | 0.016 | 0.001 |
| ES | EU_BRK_k1.0 | -0.033 [-0.135,0.065] r0.23 | 0.051 [-0.060,0.159] r0.82 | -0.008 | 0.098 |
| ES | EU_BRK_k1.5 | -0.019 [-0.110,0.069] r0.35 | 0.029 [-0.067,0.124] r0.80 | 0.010 | 0.131 |
| ES | EU_FADE_k1.0 | 0.008 [-0.050,0.064] r0.62 | 0.047 [-0.012,0.105] r0.97 | -0.058 | 0.063 |
| ES | AS_SHORT | 0.064 [0.005,0.122] r1.00 | 0.105 [0.042,0.172] r1.00 | 0.114 | 0.086 |
| ES | AS_FADE_k1.0 | -0.035 [-0.094,0.023] r0.10 | -0.022 [-0.083,0.038] r0.30 | 0.064 | 0.026 |
| ES | AS_FADE_k1.5 | -0.015 [-0.062,0.030] r0.28 | -0.003 [-0.050,0.044] r0.42 | 0.035 | 0.027 |

Both placebos are biased: a random night clock carries the night's long drift and its spread, so a short at a random clock earns about -0.02 to -0.10 R and the real AS_SHORT mean beats it mostly because the placebo is negative; beating (b) here means 'better than a random night minute', not 'positive after cost'. The mean_up and cost2x gates are what decide the absolute case.

### By year (mean R per trade [n]; MDE in R) and halves

| inst | cell | 2022 (Jun-Dec) | 2023 | 2024 | 2025 | 2026 (to 02-06) | pre-2025 half | post-2025 half | side/exit mix WF |
|---|---|---|---|---|---|---|---|---|---|
| NQ | EU_BRK_k1.0 | -0.082 [139] (MDE 0.230) | 0.079 [257] (MDE 0.168) | -0.121 [257] (MDE 0.168) | -0.076 [251] (MDE 0.170) | -0.002 [25] (MDE 0.565) | -0.036 | -0.069 | exits {0: 245, 1: 212, 2: 54} |
| NQ | EU_BRK_k1.5 | -0.099 [139] (MDE 0.199) | 0.015 [257] (MDE 0.152) | -0.076 [257] (MDE 0.154) | -0.085 [251] (MDE 0.150) | 0.056 [25] (MDE 0.514) | -0.030 | -0.072 | exits {0: 187, 2: 163, 1: 161} |
| NQ | EU_FADE_k1.0 | 0.066 [52] (MDE 0.271) | -0.036 [119] (MDE 0.202) | 0.108 [115] (MDE 0.217) | -0.113 [120] (MDE 0.200) | -0.107 [17] (MDE 0.644) | 0.032 | -0.112 | exits {2: 102, 1: 71, 0: 69} |
| NQ | AS_SHORT | 0.028 [142] (MDE 0.100) | 0.011 [258] (MDE 0.090) | 0.031 [259] (MDE 0.098) | 0.041 [258] (MDE 0.098) | 0.074 [26] (MDE 0.312) | 0.024 | 0.044 | exits {2: 487, 0: 34} |
| NQ | AS_FADE_k1.0 | 0.040 [57] (MDE 0.266) | -0.015 [104] (MDE 0.219) | -0.128 [106] (MDE 0.229) | -0.008 [110] (MDE 0.218) | 0.052 [14] (MDE 0.752) | -0.100 | -0.001 | exits {2: 85, 0: 76, 1: 61} |
| NQ | AS_FADE_k1.5 | 0.054 [57] (MDE 0.205) | 0.030 [104] (MDE 0.165) | -0.043 [106] (MDE 0.183) | 0.013 [110] (MDE 0.183) | 0.074 [14] (MDE 0.672) | -0.042 | 0.020 | exits {2: 144, 0: 42, 1: 36} |
| ES | EU_BRK_k1.0 | -0.176 [139] (MDE 0.229) | -0.203 [256] (MDE 0.177) | -0.190 [259] (MDE 0.175) | -0.177 [249] (MDE 0.172) | -0.106 [24] (MDE 0.572) | -0.199 | -0.171 | exits {0: 256, 1: 200, 2: 54} |
| ES | EU_BRK_k1.5 | -0.147 [139] (MDE 0.200) | -0.091 [256] (MDE 0.158) | -0.090 [259] (MDE 0.156) | -0.129 [249] (MDE 0.152) | -0.119 [24] (MDE 0.545) | -0.075 | -0.128 | exits {0: 188, 2: 170, 1: 152} |
| ES | EU_FADE_k1.0 | 0.014 [56] (MDE 0.260) | -0.101 [123] (MDE 0.204) | -0.001 [132] (MDE 0.205) | -0.149 [129] (MDE 0.196) | -0.358 [16] (MDE 0.582) | -0.049 | -0.172 | exits {2: 121, 0: 78, 1: 67} |
| ES | AS_SHORT | -0.033 [142] (MDE 0.103) | -0.085 [258] (MDE 0.088) | -0.069 [259] (MDE 0.101) | -0.007 [258] (MDE 0.099) | -0.004 [26] (MDE 0.333) | -0.078 | -0.007 | exits {2: 477, 0: 44} |
| ES | AS_FADE_k1.0 | -0.107 [56] (MDE 0.271) | -0.045 [108] (MDE 0.209) | -0.296 [116] (MDE 0.217) | -0.042 [118] (MDE 0.211) | -0.010 [15] (MDE 0.731) | -0.227 | -0.039 | exits {2: 104, 0: 81, 1: 57} |
| ES | AS_FADE_k1.5 | -0.022 [56] (MDE 0.201) | -0.014 [108] (MDE 0.157) | -0.176 [116] (MDE 0.167) | -0.010 [118] (MDE 0.176) | 0.105 [15] (MDE 0.643) | -0.128 | 0.003 | exits {2: 162, 0: 46, 1: 34} |

## 3. Stack add (exact lock engine for NQ; unlocked $ for ES)

Comparator: the stack of D3D2A (ST10+HM10+WT7+KB/SM/PE, 10 x frozen weights) cut to label days 2023-04-03..2026-02-06: 149 weeks, weekly mean +39,564, SD +131,851, Sharpe 2.164, maxDD (daily) +601,016, worst week -318,557, worst-20-weeks -3,534,170. Cell $ sized R12k (lots from the stop, report-scale contracts), then scaled so the cell's weekly SD = 10/20/30% of the stack's weekly SD (convention of D3D2E). NQ: legs through o2_eng.run_ext (day entry test -2R/+5R, give-back arm, week floor -12R; label-day keys, patched) with sweep surcharge; ES: lock engine has no ES path, so the unlocked daily $ (lots clip(round(12000/(stop x $50)),1,42)). Window ALL = 2023-04-03..2026-02-06.

| inst | cell | % risk | scale vs R12k | add weekly mean $ | add Sharpe | add maxDD (own) $ | add worst wk $ | marginal Sharpe | d maxDD $ | worst-20-weeks $ added | (covariance part) | stack worst wk after $ | corr(cell wk, stack wk) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ | EU_BRK_k1.0 | 10% | 0.47 | -1,710 | -0.94 | +356,517 | -30,037 | -0.105 | +5,613 | -15,063 | +19,135 | -313,519 | +0.007 |
| NQ | EU_BRK_k1.0 | 20% | 0.95 | -3,420 | -0.94 | +713,035 | -60,075 | -0.228 | +11,225 | -30,127 | +38,269 | -309,793 | +0.007 |
| NQ | EU_BRK_k1.0 | 30% | 1.42 | -5,130 | -0.94 | +1,069,552 | -90,112 | -0.364 | +16,838 | -45,190 | +57,404 | -311,358 | +0.007 |
| NQ | EU_BRK_k1.5 | 10% | 0.57 | -1,594 | -0.87 | +349,897 | -29,474 | -0.104 | +6,231 | +12,312 | +44,199 | -309,100 | +0.030 |
| NQ | EU_BRK_k1.5 | 20% | 1.14 | -3,189 | -0.87 | +699,794 | -58,948 | -0.224 | +12,462 | +24,624 | +88,398 | -318,531 | +0.030 |
| NQ | EU_BRK_k1.5 | 30% | 1.71 | -4,783 | -0.87 | +1,049,691 | -88,422 | -0.357 | +75,992 | +36,936 | +132,597 | -339,438 | +0.030 |
| NQ | EU_FADE_k1.0 | 10% | 0.84 | -860 | -0.47 | +184,672 | -42,225 | -0.030 | -5,336 | -76,323 | -59,126 | -328,617 | -0.128 |
| NQ | EU_FADE_k1.0 | 20% | 1.67 | -1,720 | -0.47 | +369,345 | -84,449 | -0.082 | +1,519 | -152,646 | -118,251 | -338,678 | -0.128 |
| NQ | EU_FADE_k1.0 | 30% | 2.51 | -2,580 | -0.47 | +554,017 | -126,674 | -0.154 | +26,944 | -228,969 | -177,377 | -352,661 | -0.128 |
| NQ | AS_SHORT | 10% | 0.99 | +493 | 0.27 | +172,314 | -34,323 | +0.039 | +7,852 | +67,537 | +57,680 | -296,335 | -0.106 |
| NQ | AS_SHORT | 20% | 1.99 | +986 | 0.27 | +344,628 | -68,647 | +0.056 | +63,630 | +135,073 | +115,360 | -286,007 | -0.106 |
| NQ | AS_SHORT | 30% | 2.98 | +1,478 | 0.27 | +516,942 | -102,970 | +0.052 | +119,408 | +202,610 | +173,041 | -275,679 | -0.106 |
| NQ | AS_FADE_k1.0 | 10% | 0.88 | -1,949 | -1.07 | +355,432 | -38,490 | -0.126 | -14,032 | -130,473 | -91,485 | -334,678 | +0.045 |
| NQ | AS_FADE_k1.0 | 20% | 1.76 | -3,899 | -1.07 | +710,864 | -76,980 | -0.267 | +19,862 | -260,945 | -182,970 | -350,800 | +0.045 |
| NQ | AS_FADE_k1.0 | 30% | 2.65 | -5,848 | -1.07 | +1,066,295 | -115,471 | -0.419 | +53,755 | -391,418 | -274,455 | -366,921 | +0.045 |
| NQ | AS_FADE_k1.5 | 10% | 1.21 | -864 | -0.47 | +221,287 | -44,656 | -0.062 | -20,349 | -100,161 | -82,886 | -308,555 | +0.020 |
| NQ | AS_FADE_k1.5 | 20% | 2.41 | -1,727 | -0.47 | +442,574 | -89,312 | -0.143 | +7,228 | -200,322 | -165,773 | -321,591 | +0.020 |
| NQ | AS_FADE_k1.5 | 30% | 3.62 | -2,591 | -0.47 | +663,861 | -133,968 | -0.238 | +34,805 | -300,483 | -248,659 | -344,028 | +0.020 |
| ES | EU_BRK_k1.0 | 10% | 0.57 | -5,727 | -3.13 | +864,454 | -37,684 | -0.329 | +20,167 | -52,455 | +62,079 | -313,069 | +0.034 |
| ES | EU_BRK_k1.0 | 20% | 1.13 | -11,453 | -3.13 | +1,728,908 | -75,369 | -0.666 | +65,413 | -104,910 | +124,157 | -321,948 | +0.034 |
| ES | EU_BRK_k1.0 | 30% | 1.70 | -17,180 | -3.13 | +2,593,363 | -113,053 | -1.002 | +198,396 | -157,366 | +186,236 | -344,564 | +0.034 |
| ES | EU_BRK_k1.5 | 10% | 0.56 | -3,134 | -1.71 | +497,052 | -30,579 | -0.170 | +9,463 | +48,484 | +111,161 | -308,916 | -0.055 |
| ES | EU_BRK_k1.5 | 20% | 1.12 | -6,268 | -1.71 | +994,103 | -61,158 | -0.359 | +18,926 | +96,969 | +222,322 | -319,931 | -0.055 |
| ES | EU_BRK_k1.5 | 30% | 1.69 | -9,401 | -1.71 | +1,491,155 | -91,737 | -0.559 | +28,390 | +145,453 | +333,483 | -341,537 | -0.055 |
| ES | EU_FADE_k1.0 | 10% | 0.82 | -2,448 | -1.34 | +383,944 | -42,955 | -0.123 | +10,505 | -108,565 | -59,615 | -329,116 | -0.102 |
| ES | EU_FADE_k1.0 | 20% | 1.64 | -4,895 | -1.34 | +767,887 | -85,910 | -0.267 | +68,935 | -217,131 | -119,229 | -339,675 | -0.102 |
| ES | EU_FADE_k1.0 | 30% | 2.46 | -7,343 | -1.34 | +1,151,831 | -128,865 | -0.426 | +140,458 | -325,696 | -178,844 | -350,233 | -0.102 |
| ES | AS_SHORT | 10% | 1.11 | -2,337 | -1.28 | +410,035 | -34,043 | -0.120 | +22,678 | +16,070 | +62,811 | -306,042 | -0.087 |
| ES | AS_SHORT | 20% | 2.23 | -4,674 | -1.28 | +820,071 | -68,085 | -0.261 | +95,317 | +32,140 | +125,622 | -305,420 | -0.087 |
| ES | AS_SHORT | 30% | 3.34 | -7,011 | -1.28 | +1,230,106 | -102,128 | -0.416 | +187,687 | +48,210 | +188,433 | -304,799 | -0.087 |
| ES | AS_FADE_k1.0 | 10% | 1.12 | -2,738 | -1.50 | +447,065 | -44,419 | -0.169 | -6,278 | -125,474 | -70,709 | -340,776 | +0.045 |
| ES | AS_FADE_k1.0 | 20% | 2.24 | -5,476 | -1.50 | +894,131 | -88,838 | -0.351 | -12,555 | -250,948 | -141,418 | -362,994 | +0.045 |
| ES | AS_FADE_k1.0 | 30% | 3.36 | -8,215 | -1.50 | +1,341,196 | -133,258 | -0.541 | -18,833 | -376,423 | -212,128 | -385,212 | +0.045 |
| ES | AS_FADE_k1.5 | 10% | 1.18 | -2,011 | -1.10 | +374,190 | -39,655 | -0.131 | -5,478 | -129,077 | -88,863 | -339,231 | +0.052 |
| ES | AS_FADE_k1.5 | 20% | 2.37 | -4,021 | -1.10 | +748,381 | -79,310 | -0.276 | -10,955 | -258,154 | -177,726 | -359,905 | +0.052 |
| ES | AS_FADE_k1.5 | 30% | 3.55 | -6,032 | -1.10 | +1,122,571 | -118,965 | -0.432 | -16,433 | -387,231 | -266,589 | -380,579 | +0.052 |

### Add at 20% by window with CIs (paired week bootstrap; MDE = 2.8 SD of the weekly difference / sqrt(weeks))

| inst | cell | window | weeks | d mean $/wk [CI] (MDE) | d Sharpe [CI] | d maxDD $ [CI] | worst-20-weeks $ |
|---|---|---|---|---|---|---|---|
| NQ | EU_BRK_k1.0 | WFPRE | 75 | -5,464 [-10,794,-207] (7,434) | -0.345 [-0.67,-0.06] | +68,691 [-47,172,+270,679] | n/a |
| NQ | EU_BRK_k1.0 | HOLD | 32 | -4,921 [-14,521,+5,199] (14,624) | -0.257 [-0.76,+0.24] | +11,225 [-69,916,+160,640] | n/a |
| NQ | EU_BRK_k1.0 | X | 44 | +1,313 [-7,076,+9,835] (12,106) | +0.021 [-0.49,+0.60] | +25,441 [-156,504,+167,367] | n/a |
| NQ | EU_BRK_k1.0 | ALL | 149 | -3,420 [-7,525,+662] (6,049) | -0.228 [-0.46,-0.01] | +11,225 [-90,055,+284,706] | -30,127 |
| NQ | EU_BRK_k1.5 | WFPRE | 75 | -4,897 [-11,063,+1,460] (8,845) | -0.362 [-0.72,-0.01] | +90,109 [-33,431,+302,473] | n/a |
| NQ | EU_BRK_k1.5 | HOLD | 32 | -3,783 [-12,188,+4,960] (12,413) | -0.172 [-0.61,+0.29] | +12,462 [-85,613,+153,760] | n/a |
| NQ | EU_BRK_k1.5 | X | 44 | +300 [-6,876,+7,967] (10,650) | -0.012 [-0.50,+0.52] | +32,220 [-161,197,+184,326] | n/a |
| NQ | EU_BRK_k1.5 | ALL | 149 | -3,189 [-7,240,+776] (6,049) | -0.224 [-0.45,+0.01] | +12,462 [-82,574,+314,568] | +24,624 |
| NQ | EU_FADE_k1.0 | WFPRE | 75 | -525 [-6,215,+5,376] (7,934) | -0.004 [-0.32,+0.32] | +55,765 [-95,893,+123,590] | n/a |
| NQ | EU_FADE_k1.0 | HOLD | 32 | -5,151 [-16,406,+6,368] (16,570) | -0.185 [-0.69,+0.45] | -10,672 [-69,736,+132,626] | n/a |
| NQ | EU_FADE_k1.0 | X | 44 | -1,183 [-7,987,+5,420] (9,834) | -0.115 [-0.54,+0.34] | +49,444 [-124,376,+188,272] | n/a |
| NQ | EU_FADE_k1.0 | ALL | 149 | -1,720 [-5,862,+2,423] (6,049) | -0.082 [-0.30,+0.14] | +1,519 [-124,385,+201,251] | -152,646 |
| NQ | AS_SHORT | WFPRE | 75 | +1,396 [-4,376,+7,259] (8,516) | +0.101 [-0.25,+0.45] | -85,769 [-141,840,+121,765] | n/a |
| NQ | AS_SHORT | HOLD | 32 | +5,451 [-3,052,+14,127] (12,339) | +0.361 [-0.07,+0.74] | -93,578 [-158,017,+87,116] | n/a |
| NQ | AS_SHORT | X | 44 | -3,007 [-10,783,+4,552] (11,300) | -0.247 [-0.74,+0.24] | +111,556 [-26,406,+303,245] | n/a |
| NQ | AS_SHORT | ALL | 149 | +986 [-3,123,+5,100] (6,049) | +0.056 [-0.19,+0.30] | +63,630 [-132,662,+212,947] | +135,073 |
| NQ | AS_FADE_k1.0 | WFPRE | 75 | -6,175 [-12,995,+165] (9,189) | -0.407 [-0.82,-0.06] | +59,444 [-42,103,+298,483] | n/a |
| NQ | AS_FADE_k1.0 | HOLD | 32 | +1,314 [-7,068,+9,168] (11,879) | +0.051 [-0.34,+0.55] | -28,769 [-114,634,+101,477] | n/a |
| NQ | AS_FADE_k1.0 | X | 44 | -3,633 [-10,577,+2,953] (9,912) | -0.282 [-0.68,+0.12] | +67,787 [-18,791,+282,174] | n/a |
| NQ | AS_FADE_k1.0 | ALL | 149 | -3,899 [-8,074,+140] (6,049) | -0.267 [-0.50,-0.05] | +19,862 [-77,668,+298,247] | -260,945 |
| NQ | AS_FADE_k1.5 | WFPRE | 75 | -2,820 [-9,145,+3,189] (9,002) | -0.268 [-0.65,+0.08] | +16,463 [-66,274,+241,836] | n/a |
| NQ | AS_FADE_k1.5 | HOLD | 32 | +1,845 [-7,190,+10,709] (13,105) | +0.170 [-0.28,+0.61] | -82,009 [-145,900,+71,276] | n/a |
| NQ | AS_FADE_k1.5 | X | 44 | -2,385 [-9,232,+4,201] (9,719) | -0.183 [-0.57,+0.24] | +55,154 [-41,615,+236,046] | n/a |
| NQ | AS_FADE_k1.5 | ALL | 149 | -1,727 [-5,941,+2,380] (6,049) | -0.143 [-0.39,+0.08] | +7,228 [-98,605,+223,848] | -200,322 |
| ES | EU_BRK_k1.0 | WFPRE | 75 | -10,012 [-15,399,-4,731] (7,684) | -0.589 [-0.93,-0.30] | +163,132 [-52,301,+362,232] | n/a |
| ES | EU_BRK_k1.0 | HOLD | 32 | -11,679 [-22,102,-413] (15,608) | -0.604 [-1.33,+0.02] | +40,335 [-46,363,+297,082] | n/a |
| ES | EU_BRK_k1.0 | X | 44 | -13,226 [-20,340,-4,817] (11,172) | -0.861 [-1.41,-0.34] | +113,338 [-10,760,+511,917] | n/a |
| ES | EU_BRK_k1.0 | ALL | 149 | -11,453 [-15,886,-7,177] (6,049) | -0.666 [-0.93,-0.42] | +65,413 [-5,172,+608,278] | -104,910 |
| ES | EU_BRK_k1.5 | WFPRE | 75 | -6,414 [-11,657,-1,186] (7,799) | -0.419 [-0.75,-0.12] | +60,694 [-37,435,+320,123] | n/a |
| ES | EU_BRK_k1.5 | HOLD | 32 | -8,047 [-17,782,+1,944] (14,146) | -0.368 [-0.94,+0.14] | +18,926 [-61,301,+192,013] | n/a |
| ES | EU_BRK_k1.5 | X | 44 | -4,440 [-12,394,+4,229] (11,933) | -0.254 [-0.84,+0.33] | -27,885 [-128,933,+222,575] | n/a |
| ES | EU_BRK_k1.5 | ALL | 149 | -6,268 [-10,445,-2,097] (6,049) | -0.359 [-0.62,-0.12] | +18,926 [-63,546,+367,124] | +96,969 |
| ES | EU_FADE_k1.0 | WFPRE | 75 | -3,388 [-8,268,+1,324] (6,888) | -0.161 [-0.45,+0.12] | +63,163 [-63,253,+162,439] | n/a |
| ES | EU_FADE_k1.0 | HOLD | 32 | -12,017 [-23,689,-1,055] (16,166) | -0.528 [-1.11,+0.15] | +12,813 [-40,386,+216,212] | n/a |
| ES | EU_FADE_k1.0 | X | 44 | -2,061 [-10,918,+5,852] (11,901) | -0.200 [-0.72,+0.33] | +116,860 [-85,718,+282,618] | n/a |
| ES | EU_FADE_k1.0 | ALL | 149 | -4,895 [-9,035,-726] (6,049) | -0.267 [-0.51,-0.02] | +68,935 [-74,369,+313,214] | -217,131 |
| ES | AS_SHORT | WFPRE | 75 | -4,036 [-9,932,+2,251] (8,776) | -0.239 [-0.60,+0.12] | -1,678 [-85,604,+221,503] | n/a |
| ES | AS_SHORT | HOLD | 32 | -726 [-10,829,+9,296] (14,413) | +0.079 [-0.46,+0.52] | -76,696 [-129,111,+177,529] | n/a |
| ES | AS_SHORT | X | 44 | -8,421 [-14,657,-2,281] (9,280) | -0.568 [-0.98,-0.17] | +143,243 [+6,262,+410,820] | n/a |
| ES | AS_SHORT | ALL | 149 | -4,674 [-9,068,-566] (6,049) | -0.261 [-0.53,-0.02] | +95,317 [-67,987,+368,432] | +32,140 |
| ES | AS_FADE_k1.0 | WFPRE | 75 | -7,972 [-14,792,-1,188] (9,477) | -0.493 [-0.95,-0.11] | +67,011 [-58,728,+357,544] | n/a |
| ES | AS_FADE_k1.0 | HOLD | 32 | -1,600 [-10,787,+7,609] (13,711) | -0.177 [-0.63,+0.32] | -12,555 [-86,550,+165,844] | n/a |
| ES | AS_FADE_k1.0 | X | 44 | -3,792 [-9,009,+1,240] (7,686) | -0.255 [-0.59,+0.06] | +4,664 [-29,639,+203,552] | n/a |
| ES | AS_FADE_k1.0 | ALL | 149 | -5,476 [-9,704,-1,292] (6,049) | -0.351 [-0.60,-0.12] | -12,555 [-71,983,+321,766] | -250,948 |
| ES | AS_FADE_k1.5 | WFPRE | 75 | -6,258 [-12,960,+216] (9,589) | -0.420 [-0.87,-0.05] | +61,528 [-53,767,+317,689] | n/a |
| ES | AS_FADE_k1.5 | HOLD | 32 | -57 [-8,238,+8,031] (11,510) | -0.065 [-0.46,+0.51] | -10,955 [-89,172,+150,718] | n/a |
| ES | AS_FADE_k1.5 | X | 44 | -2,910 [-8,843,+3,042] (9,064) | -0.207 [-0.59,+0.17] | +15,653 [-45,703,+198,570] | n/a |
| ES | AS_FADE_k1.5 | ALL | 149 | -4,021 [-8,320,+35] (6,049) | -0.276 [-0.53,-0.05] | -10,955 [-73,756,+321,794] | -258,154 |

### Lock effect (NQ, 20%, ALL) and 2x cost

| cell | locked: d Sharpe / d maxDD / w20 | unlocked: d Sharpe / d maxDD / w20 | 2x cost (locked): d Sharpe / d maxDD / w20 | 2x cost WFPRE d Sharpe |
|---|---|---|---|---|
| EU_BRK_k1.0 | -0.228 / +11,225 / -30,127 | -0.228 / +11,225 / -30,127 | -0.316 / +18,707 / -72,711 | -0.423 |
| EU_BRK_k1.5 | -0.224 / +12,462 / +24,624 | -0.224 / +12,462 / +24,624 | -0.290 / +15,113 / +6,525 | -0.420 |
| EU_FADE_k1.0 | -0.082 / +1,519 / -152,646 | -0.082 / +1,519 / -152,646 | -0.136 / +18,611 / -167,005 | -0.051 |
| AS_SHORT | +0.056 / +63,630 / +135,073 | +0.055 / +63,664 / +141,097 | -0.130 / +94,433 / +68,065 | -0.067 |
| AS_FADE_k1.0 | -0.267 / +19,862 / -260,945 | -0.267 / +19,862 / -260,945 | -0.347 / +27,840 / -287,350 | -0.495 |
| AS_FADE_k1.5 | -0.143 / +7,228 / -200,322 | -0.143 / +7,228 / -200,322 | -0.208 / +14,296 / -229,100 | -0.325 |

The day/week locks barely fire on a one-trade-a-day cell at R = $12,000 (they are the stack's per-book rule, kept for exactness); the lock changes NQ AS_SHORT by a few thousand dollars only.

### Weekly $ of the 20% add by calendar year (mean [95% CI] (MDE), weeks)

| inst | cell | 2023 (from 04-03) | 2024 | 2025 | 2026 (to 02-06) |
|---|---|---|---|---|---|
| NQ | EU_BRK_k1.0 | +3,039 [-6,313,+12,390] (13,359) n39 | -7,479 [-13,582,-1,376] (8,719) n53 | -4,364 [-10,831,+2,103] (9,239) n53 | -66 [-33,555,+33,424] (47,842) n6 |
| NQ | EU_BRK_k1.5 | +1,790 [-6,223,+9,804] (11,448) n39 | -5,198 [-13,117,+2,721] (11,313) n53 | -5,393 [-11,258,+471] (8,378) n53 | +2,735 [-24,819,+30,288] (39,362) n6 |
| NQ | EU_FADE_k1.0 | -4,048 [-11,065,+2,969] (10,024) n39 | +4,079 [-3,032,+11,190] (10,159) n53 | -5,220 [-12,069,+1,628] (9,784) n53 | -6,312 [-38,007,+25,383] (45,279) n6 |
| NQ | AS_SHORT | -3,069 [-11,113,+4,976] (11,492) n39 | -270 [-8,038,+7,499] (11,098) n53 | +4,505 [-2,299,+11,309] (9,720) n53 | +7,013 [+1,848,+12,177] (7,377) n6 |
| NQ | AS_FADE_k1.0 | -4,222 [-11,637,+3,193] (10,593) n39 | -7,488 [-15,181,+205] (10,990) n53 | -593 [-7,735,+6,549] (10,203) n53 | +2,004 [-10,719,+14,727] (18,176) n6 |
| NQ | AS_FADE_k1.5 | -3,238 [-10,262,+3,785] (10,034) n39 | -3,486 [-11,052,+4,079] (10,808) n53 | +530 [-7,012,+8,072] (10,774) n53 | +4,261 [-5,401,+13,922] (13,802) n6 |
| ES | EU_BRK_k1.0 | -12,523 [-21,046,-4,001] (12,175) n39 | -11,122 [-17,879,-4,366] (9,652) n53 | -11,197 [-17,815,-4,579] (9,455) n53 | -5,870 [-40,636,+28,895] (49,665) n6 |
| ES | EU_BRK_k1.5 | -3,668 [-12,538,+5,202] (12,672) n39 | -5,985 [-13,306,+1,337] (10,460) n53 | -8,228 [-14,214,-2,243] (8,551) n53 | -6,257 [-36,699,+24,185] (43,488) n6 |
| ES | EU_FADE_k1.0 | -5,383 [-14,131,+3,364] (12,496) n39 | -551 [-6,647,+5,545] (8,708) n53 | -7,139 [-14,199,-78] (10,087) n53 | -18,644 [-49,493,+12,206] (44,071) n6 |
| ES | AS_SHORT | -8,706 [-15,748,-1,664] (10,060) n39 | -5,491 [-12,048,+1,065] (9,366) n53 | -1,183 [-9,451,+7,085] (11,811) n53 | -532 [-17,555,+16,491] (24,318) n6 |
| ES | AS_FADE_k1.0 | -3,382 [-9,242,+2,478] (8,371) n39 | -10,196 [-17,397,-2,995] (10,288) n53 | -2,561 [-10,798,+5,675] (11,767) n53 | -1,327 [-16,580,+13,927] (21,790) n6 |
| ES | AS_FADE_k1.5 | -2,305 [-9,179,+4,569] (9,820) n39 | -9,783 [-17,089,-2,478] (10,436) n53 | -663 [-8,063,+6,738] (10,572) n53 | +7,388 [-12,883,+27,658] (28,958) n6 |

## 4. Where the stack loses (A's overnight loss slots 22:00, 23:30, 03:30, 05:00, 05:30, 07:00, 08:00 ET) and the 20 worst weeks

Stack entries in those seven slots (A table cut to 2026-02-06): 2,270 trades, $-467,366; stack P&L in its 20 worst weeks from entries in those slots: -463,635. 'Cell $ in overlapping trades' = the 20%-scaled P&L of cell trades whose hold [entry, exit] overlaps any of those half-hour slots (EU_* cells hold through 03:30, 05:00, 05:30, 07:00; the Tokyo cells end by 21:30 ET and overlap none; AS_FADE ends 22:00 at the latest). corr = daily corr of the cell with the stack's loss-slot entries' P&L; bad-days = the stack's worst 25% days by loss-slot P&L (n days listed).

| inst | cell | trades overlapping | cell $ overlapping (20%) | cell $ other trades (20%) | corr to stack loss-slot $ (daily) | corr to stack night $ (daily) | cell $ on stack's bad loss-slot days (20%) | cell $ in stack 20 worst weeks (20%) |
|---|---|---|---|---|---|---|---|---|
| NQ | EU_BRK_k1.0 | 561 of 762 | -384,585 | -126,757 | +0.072 | +0.020 | -201,498 (n 153) | -30,127 |
| NQ | EU_BRK_k1.5 | 684 of 762 | -527,298 | +11,150 | +0.106 | +0.085 | -369,590 (n 153) | +24,624 |
| NQ | EU_FADE_k1.0 | 351 of 357 | -179,817 | -82,921 | -0.081 | -0.014 | +59,374 (n 153) | -152,646 |
| NQ | AS_SHORT | 0 of 773 | +0 | +109,033 | +0.030 | +0.071 | -119,180 (n 153) | +135,073 |
| NQ | AS_FADE_k1.0 | 0 of 318 | +0 | -573,853 | +0.051 | +0.023 | -253,492 (n 153) | -260,945 |
| NQ | AS_FADE_k1.5 | 0 of 318 | +0 | -140,920 | +0.042 | -0.008 | -83,629 (n 153) | -200,322 |
| ES | EU_BRK_k1.0 | 558 of 760 | -993,470 | -765,277 | +0.061 | +0.040 | -588,889 (n 153) | -104,910 |
| ES | EU_BRK_k1.5 | 676 of 760 | -750,077 | -266,579 | +0.045 | +0.070 | -418,812 (n 153) | +96,969 |
| ES | EU_FADE_k1.0 | 378 of 385 | -767,006 | -26,148 | -0.064 | -0.035 | -87,131 (n 153) | -217,131 |
| ES | AS_SHORT | 0 of 773 | +0 | -757,009 | +0.040 | +0.075 | -308,566 (n 153) | +32,140 |
| ES | AS_FADE_k1.0 | 0 of 342 | +0 | -748,765 | +0.001 | -0.029 | -111,506 (n 153) | -250,948 |
| ES | AS_FADE_k1.5 | 0 of 342 | +0 | -494,687 | +0.003 | -0.050 | -74,349 (n 153) | -258,154 |

Reading: a Europe-session cell is exactly where the stack loses (03:30, 05:00, 05:30, 07:00, 08:00 are all inside the EU_* hold), yet the EU_BRK cells lose there too: a fixed-clock range break does not hedge a trend-follower that is already taking the same breaks. The Tokyo AS_SHORT has small negative correlation to the stack's night P&L and adds in the worst weeks mostly through covariance, which is the property wanted, but at an unproven mean.

## 5. Print-level fill check (NQ AS_SHORT, the only positive cell)

Databento trades (parent, front contract, 2023-02+). For the 773 NQ AS_SHORT trades 2023-02..2026-02-06 (730 time exits, 43 stop-outs) the entry is replaced by the first SELL-aggressor print at or after entry +1 s and the exit by the first BUY-aggressor print at or after the flat time +1 s (within 20 s). 578 trades have both prints; the other 152 time-exit trades have no qualifying print inside 20 s (the Tokyo open is thin in the first seconds; a real market order would still fill at the quote, which this trades-only check cannot see) and the 43 stop-outs were not print-checked (bar model: stop level +2 ticks). Same trades, bar model vs prints (this subset excludes the stop-outs and the trades without prints, so its mean R is higher than the cell's overall mean; compare the two columns, not the level):

| window | n | bar-model mean pts | print-level mean pts | bar-model mean R | print-level mean R | SE of print R |
|---|---|---|---|---|---|---|
| X | 166 | +0.819 | +1.318 | +0.0284 | +0.0548 | 0.0337 |
| WFPRE | 267 | +3.688 | +4.376 | +0.1019 | +0.1254 | 0.0302 |
| HOLD | 118 | +4.617 | +4.975 | +0.1213 | +0.1329 | 0.0411 |

The bar-model fill (open -1 tick in, close +1 tick out) is not optimistic against the prints on the time-exit trades (prints are +0.3 to +0.7 pt better on average, 2x the cost is not tested at print level). This is a check of the fill model only; it does not change the tier.

## 6. Disclosures, bugs, limits

- Selection overlap: the map and my reading of D3DV1 (which includes HOLD for the 02:45 window) saw 2022-06..2025-06; X and PRE23 are inside the map span, so only HOLD is a post-map window for AS_SHORT and the London cells. WFPRE gates are in-sample for the window choice (disclosed in the prereg before scoring).
- Smoke test: after coding the engine I printed whole-span NQ mean R / points per cell (all windows mixed) before the prereg was written, and f_stack.py printed whole-span engine $ per cell before the holdout look was logged (all negative except NQ AS_SHORT). No cell, window, parameter or gate changed after either print.
- BUG FIXED (logged): the first engine run of the lock bridge produced -$279M for AS_SHORT because the cache_te2 back-adjusted bars and the engine's 1-s path (library adjustment) differ by a per-contract constant of about 3,700 NQ points; entry prices in path space are now bar fill + (path price at the entry second - bar open). The unlocked daily $ matches the closed-form sum lots x (pts x 20 - 4.84 - sweep) to the dollar for all cells. A second first-run problem (events before the path starts 2023-02-08) is handled by dropping trades before 2023-02-10 from the engine.
- o2_eng.book_from_legs keys the day lock by the ET calendar date; overnight entries after 18:00 belong to the next label day, so f_eng.py uses label-day and label-week keys. The engine's size surcharge is applied to NQ lots (o2_gen.size_pts); not applied to ES.
- ES stack add is unlocked (no ES 1-s path in the engine); ES<->NQ replication is on standalone R plus the unlocked $ add. The NQ lock effect is shown (locks barely fire on a one-trade-a-day cell).
- Placebo definitions follow D3DVE ((a) random direction same clock, (b) same rule random clock, 40 draws). For EU_BRK the (a) draw enters at the break bar's close in a random side with the same bracket; (b) keeps the anchor-to-flat duration and draws the anchor on a 5-min grid between 19:30 ET and 09:00 ET minus the duration.
- Fees: NQ $4.84 RT is a PROXY of the ES NT-published value (FEES.md flag 1); ES $4.84 is NT-published. Overnight spreads in the first seconds after the Tokyo and London opens are wider than the 1-tick market-slippage assumption; the print check above covers AS_SHORT only. Japanese and UK holidays are not removed.
- The stack comparator is A's corrected stack cut to 2026-02-06 (149 weeks, Sharpe 2.16, worst-20-weeks -3.53M); D3D2E used the D3SL stack (Sharpe 2.235, worst-20 -3.30M) over the same weeks, so worst-20-weeks $ are not additive across the two reports.
- Day-of-week and holiday handling: one anchor per weekday; days without a 25+ minute box or window are skipped; both-sides-in-one-minute breaks are skipped (counted, not traded).

## 7. Hand-back numbers

| inst | cell | tier | mean R WFPRE (MDE) | d Sharpe @20% | d maxDD @20% | worst-20-weeks $ @10 / 20 / 30% |
|---|---|---|---|---|---|---|
| NQ | EU_BRK_k1.0 | DEAD | -0.091 (0.142) | -0.228 | +11,225 | -15,063 / -30,127 / -45,190 |
| NQ | EU_BRK_k1.5 | DEAD | -0.075 (0.128) | -0.224 | +12,462 | +12,312 / +24,624 / +36,936 |
| NQ | EU_FADE_k1.0 | DEAD | -0.005 (0.174) | -0.082 | +1,519 | -76,323 / -152,646 / -228,969 |
| NQ | AS_SHORT | DEAD | 0.032 (0.086) | +0.056 | +63,630 | +67,537 / +135,073 / +202,610 |
| NQ | AS_FADE_k1.0 | DEAD | -0.112 (0.190) | -0.267 | +19,862 | -130,473 / -260,945 / -391,418 |
| NQ | AS_FADE_k1.5 | DEAD | -0.036 (0.154) | -0.143 | +7,228 | -100,161 / -200,322 / -300,483 |
| ES | EU_BRK_k1.0 | DEAD | -0.164 (0.147) | -0.666 | +65,413 | -52,455 / -104,910 / -157,366 |
| ES | EU_BRK_k1.5 | DEAD | -0.098 (0.131) | -0.359 | +18,926 | +48,484 / +96,969 / +145,453 |
| ES | EU_FADE_k1.0 | DEAD | -0.073 (0.167) | -0.267 | +68,935 | -108,565 / -217,131 / -325,696 |
| ES | AS_SHORT | DEAD | -0.046 (0.089) | -0.261 | +95,317 | +16,070 / +32,140 / +48,210 |
| ES | AS_FADE_k1.0 | DEAD | -0.213 (0.187) | -0.351 | -12,555 | -125,474 / -250,948 / -376,423 |
| ES | AS_FADE_k1.5 | DEAD | -0.109 (0.150) | -0.276 | -10,955 | -129,077 / -258,154 / -387,231 |
