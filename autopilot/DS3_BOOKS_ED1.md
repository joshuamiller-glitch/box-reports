# DS3_BOOKS - the DS3 container (D3L, 2026-10-26; research only; no spec is a live recommendation)
Companion to autopilot/DS3_PORTFOLIO.md (scoring, verdict line) and autopilot/DS3_SPEC_<book>.md (the exact NT8 rule + identity test, written by D3X). Dollars below are at nominal lots with R = lots x stop x $20 = 12,000 for every book here (10 lots x 60 pt; ST/HM/WT as in DS2: ST10/HM10 R = 12,000, WT7 45-pt stop R = 6,300). Series are per-book-lock, live cost (stop-join 1.01 pt, market 0.995 pt, $4.84 RT). 14/14-scale equivalents multiply by 1.4 (R 16,800).

## Selected set (pre-registered selection on WF-PRE; risk-parity weights monthly): 3 books
All three are NQ, NT8 1-minute chart data only (no L2). Per-book locks (identical for every book, in book-R): day -2R / +5R, give-back arm +2R keep 50%, cap off, week floor 12R. At R = 12,000: day -$24,000 / +$60,000, arm +$24,000, week floor -$144,000. Execution mode: separate NT8 strategy / own lock group per book on the same account as DS2.
| book | status | instrument / bars | signal rule (see SPEC for exact entry/exit) | stop / exit | filters / session (ET) | lots at nominal (R=12,000) | exec mode |
|---|---|---|---|---|---|---|---|
| ST10 | CANDIDATE (fails only per-book timing placebo 0.68) | NQ, DS2 ST book | ATR120 x2.0 Supertrend on Close, EMA200 filter, market entry (spec autopilot/DS3_SPEC_ST10.md; identity 1.07% entry mismatch, 1.40% entry+exit, limit 2%; entry-window start/end inferred from library rows, to be confirmed against live DualStrat2 properties; the P9 stop-join fill mapping inside the DS2 series is not re-derived, so the series assume a better fill than default Market/Native) | 60 pt stop, target 1.0R | DS2 session gates | 10 | market entries, stop-join exits, per-book locks |
| TB7_ORBNY_k3_P60_N | CANDIDATE (fails only 2023-04..24-01 sign, -$137/wk) | NQ 3-min | NY opening range break: OR over L min from 09:30 (L in 15/30/60, buffer 0/5/10 pt re-fit monthly on the trailing 6 months), close beyond OR +/- buffer sets sticky state, flat->enter at next bar open, reversal flips | 60 pt stop from entry-bar open, flat 16:57, no target | entries bars starting before 15:00, flat by 16:57 | 10 | market entry, stop-market; Calculate OnBarClose |
| TB9_RENKO_c2_k1_P60_N | DEAD on the book bar (lock-dependent; sign negative 2023-04..24-01; LOO holdout negative) but carried in the scored portfolio | NQ, Renko logic on 1-min closes | bricks R in 12/20/30 pt re-fit monthly, enter after 2 confirming bricks | 60 pt stop | see SPEC | 10 | market entry, stop-market |
Weights (average NQ lots in the WF window): equal weekly SD with DS2: ST 9.0, TB7 11.0, TB9c2 9.2; same 27-contract budget: 8.3 / 10.2 / 8.5; half of the equal-SD scale: 4.5 / 5.5 / 4.6; DS3 inside DS2+DS3 (peak 23): 3.4 / 4.2 / 3.5. Monthly re-fit parameter files for TB7/TB9c2 (45 months) are in the SPECs; without them the series cannot be reproduced.

## Standalone backtest expectation (WF 142 weeks 2024-02..2026-10, per-book locks, nominal lots, live cost)
| book | mean $/wk | SD | trades/wk | maxDD | worst wk | HOLD $/wk | 2023-04..24-01 $/wk | win rate (pre-lock trades) | avg win / avg loss ($, nominal lots) |
|---|---|---|---|---|---|---|---|---|---|
| ST10 | 14,350 | 57,331 | 26.0 | 263,432 | -91,189 | 16,463 | 6,055 | 51.7% | 11,233 / -11,168 |
| HM10 (not selected) | 10,052 | 53,295 | 23.9 | 251,800 | -108,226 | 10,598 | 3,808 | see DS2 | |
| WT7 (not selected) | 1,438 | 27,750 | 38.2 | 244,807 | -66,053 | 786 | 1,293 | 58.3% | 4,243 / -5,740 |
| TB7_ORBNY_k3 | 6,074 | 47,887 | 6.0 | 392,931 | -80,089 | 4,812 | -137 | 32.1% | 27,629 / -11,660 |
| TB9_RENKO_c2 | 6,623 | 53,666 | 13.1 | 420,763 | -134,136 | 6,037 | -5,245 | 33.9% | 18,899 / -9,771 |
| TB1_ST_k15 (not selected) | 7,737 | 60,467 | 14.2 | 403,523 | -145,427 | 11,521 | -3,101 | 30.7% | 22,097 / -9,247 |
Trade distribution columns are pre-lock closed trades in the WF window at nominal lots, net of cost (ST/WT from the P9-mapped engine rows, TB from the T-B trade tables). They describe the entry rule, not the locked series; win rates of 31-34% mean the TB books are low-hit-rate, large-winner books. Costs: ST/HM/WT 1.5x/2x per DS3_PORTFOLIO; TB7 WF 5,033 / 3,873 and TB9c2 2,778 / 836 per week at 1.5x / 2x.

## Weekly correlations (WF, per-book-lock series)
| |ST|HM|WT|TB1_ST_k15_P60_N|TB7_ORBNY_k3_P60_N|TB9_RENKO_c2_k1_P60_N|DS2|
|---|---|---|---|---|---|---|---|
| ST |1.0|0.41|0.43|0.41|0.13|0.38|0.85|
| HM |0.41|1.0|0.2|0.26|0.25|0.49|0.77|
| WT |0.43|0.2|1.0|0.32|0.1|0.19|0.6|
| TB1_ST_k15_P60_N |0.41|0.26|0.32|1.0|0.2|0.23|0.44|
| TB7_ORBNY_k3_P60_N |0.13|0.25|0.1|0.2|1.0|0.13|0.22|
| TB9_RENKO_c2_k1_P60_N |0.38|0.49|0.19|0.23|0.13|1.0|0.5|
| DS2 |0.85|0.77|0.6|0.44|0.22|0.5|1.0|
Corr of the selected set (equal-SD) to DS2 alone: 0.75 (ST in both). Between selected books: ST-TB7 0.13, ST-TB9c2 0.38, TB7-TB9c2 0.13 (all <= 0.5). DS2 books vs TB books: HM-TB9c2 0.49 (the reason HM was not selected under the 0.5 cap).

## Not in the set (and why)
HM10, WT7 (no WF-PRE Sharpe gain under the 0.5 cap; HM/WT placebo ranks 0.62/0.39), TB1_ST_k15 (marginal Sharpe down; span negative), TB9_RENKO_c5 (DEAD after the exact-lock re-score: WF -$244/wk), TF1_FOMC_NY (an entry filter for NQ NY entries, CANDIDATE, below its MDE: spec DS3_SPEC_TF1_FOMC_NY_block.md), every T-A/T-C/T-D/T-E/T-H/T-I/T-J/T-K cell (all DEAD; T-J vol-state sizing is plain de-leveraging).
