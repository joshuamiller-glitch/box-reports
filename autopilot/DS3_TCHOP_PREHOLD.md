# DS3_TCHOP pre-holdout text (D3CH, written before the holdout look; WF-PRE 2024-02..2025-06, 75 weeks)

Prereg l2vast/ds3/prereg/T-CHOP_prereg.md sha256 fed8a99fa2d38ed9096eba13141b92c7d96852c3c5a73d9bb4c5fb9d545f9ea6 (logged in DECISIONS.md before any scoring). Numbers: l2vast/ds3/out/CHOP/chop_pre.json (code chop_run.py pre; only the WF-PRE window is computed in this stage). MAPPED basis (the sleeves' stored 1-min / 1-s series; direct L2 pricing of the NQ/ES/RTY dip-buy legs is running, see below). Equal risk = WF-PRE weekly SD scaled to ST10 WF-PRE SD.

## Stack (WF-PRE)

DS2 (ST10+HM10+WT7) + DS3 (KB+SM+PB3B_R5_P1, peak 23 lots): mean 47.3k/wk, SD 138.8k, Sharpe 2.46, maxDD 731.3k, worst week -269.0k. Losing weeks WF-PRE: L25 (below the 25th percentile) 19 weeks; negative weeks 28 weeks.
Base KB+SM+PB at the 50-contract cap line: mean 39.7k/wk, SD 94.8k, Sharpe 3.02, maxDD 366.6k, peak 50 lots (interval replay).

## Cells, WF-PRE, mapped basis, equal risk

| cell | instrument | lots at equal risk | mean/wk | Sharpe | maxDD | worst wk | trades/wk | win / required | corr stack | corr KB / SM / PB | L25 mean/wk | LNEG mean/wk | chop(+60) P&L total [per session] | marginal Sharpe (add-one) | dMaxDD cap | shift-placebo rank (marginal / L25) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C01 RSI2C_s20 | NQ | 13.4 | 9.4k | 1.28 | 666.1k | -232.3k | 0.47 | 0.63 / 0.51 | +0.16 | +0.01 / -0.12 / +0.26 | 3.8k | -3.5k | 143.7k [0.9k] | +0.16 | 262.3k | 0.44 / 0.29 |
| C02 ES_RSI2_t10 | ES | 16.2 | 8.9k | 1.22 | 354.3k | -245.6k | 0.41 | 0.61 / 0.41 | +0.14 | +0.01 / -0.09 / +0.23 | 4.3k | -4.3k | 49.0k [0.3k] | -0.07 | 114.3k | 0.17 / 0.36 |
| C04 RSI2T_t10 | NQ | 19.9 | 9.9k | 1.35 | 226.8k | -199.1k | 0.33 | 0.68 / 0.50 | +0.09 | -0.03 / -0.04 / +0.13 | 5.6k | 7.1k | 202.4k [1.2k] | +0.30 | -43.8k | 0.73 / 0.42 |
| C05 IBS_t20_n1 | NQ | 7.7 | 5.6k | 0.77 | 223.0k | -180.2k | 0.80 | 0.60 / 0.51 | -0.00 | +0.08 / -0.12 / +0.18 | 3.8k | -0.8k | 115.7k [0.7k] | -0.35 | -68.7k | 0.05 / 0.41 |
| C06 RTY_IBS_t20_n1 | RTY | 32.1 | 4.5k | 0.62 | 215.9k | -144.3k | 0.77 | 0.55 / 0.48 | +0.02 | -0.01 / -0.08 / +0.18 | 6.1k | 0.6k | 24.3k [0.1k] | -0.13 | 21.0k | 0.50 / 0.63 |
| C07 ORB_ASIA_15_v1_s60 | NQ | 36.7 | 4.0k | 0.55 | 381.9k | -92.9k | 0.88 | 0.45 / 0.41 | +0.31 | +0.05 / +0.06 / +0.30 | -20.1k | -17.3k | -73.3k [-0.4k] | -0.29 | 10.8k | 0.34 / 0.02 |
| C08 ORB_ASIA_15_v1_s75 | NQ | 29.6 | 1.0k | 0.14 | 368.6k | -92.4k | 0.88 | 0.42 / 0.41 | +0.24 | +0.02 / +0.08 / +0.19 | -15.5k | -14.1k | -67.9k [-0.4k] | -0.40 | 12.2k | 0.25 / 0.03 |
| C09 COMB_c3_R | NQ | 10.0 | 7.3k | 1.00 | 279.0k | -208.5k | 1.03 | 0.62 / 0.53 | +0.12 | +0.14 / -0.06 / +0.26 | 2.8k | -2.3k | 157.2k [0.9k] | -0.12 | 13.0k | 0.22 / 0.34 |
| C13 YM_RSI2_t10 | YM | 25.1 | 4.7k | 0.64 | 382.9k | -238.7k | 0.63 | 0.53 / 0.46 | +0.15 | +0.02 / -0.14 / +0.21 | -2.1k | -9.2k | 7.2k [0.0k] | -0.54 | 164.9k | 0.14 / 0.15 |
| C03 DIPBUY_RSI2_2lot | NQ+ES | 7.8 | 9.8k | 1.34 | 538.8k | -254.3k | 0.88 | 0.62 / 0.47 | +0.16 | +0.01 / -0.11 / +0.26 | 4.3k | -4.1k | 107.6k [0.6k] | -0.05 | 358.6k | 0.31 / 0.31 |
| C10 T14_S_s50_t1.5_n14 | NQ(DS2 shorts) | 14.0 | 8.3k | 0.80 | 537.0k | -168.5k | 0.00 | 0.22 / 0.59 | -0.19 | -0.09 / +0.09 / -0.11 | 30.1k | 20.1k | 535.6k [3.2k] | n/a | n/a | n/a |
| C11 FOURTH_R4_k2.0_H60_8lots | NQ | 16.8 | -20.6k | -2.82 | 1915.6k | -166.4k | 32.29 | 0.51 / 0.55 | -0.18 | -0.04 / -0.10 / -0.03 | -15.5k | -19.7k | -167.1k [-1.0k] | -1.84 | 255.3k | 0.37 / 0.69 |
| C12 FOURTH_R2_k1.0_H120_8lots | NQ | 14.9 | -29.2k | -3.98 | 2391.4k | -137.7k | 24.63 | 0.46 / 0.52 | -0.19 | -0.15 / +0.03 / -0.18 | -10.7k | -19.8k | -167.4k [-1.0k] | -1.99 | 262.6k | 0.09 / 0.86 |

Best-of-N (12 add-one cells): best real marginal +0.30 (C04) vs null max q95 +1.24, median +0.82; rank 0.02.

## What this stage decides (WF-PRE information only)

* Direct L2 replay (governor chop_direct.py, orch via corepool) is run for every NQ/ES/RTY DIP-BUY cell: C01, C02, C03 (= C01+C02), C04, C05, C06, C09. All have a stack-losing-week (L25) mean above 0 on WF-PRE and/or a stack correlation near 0, so the prereg selection rule includes them. NOT replayed: C07/C08 (ORB Asia: L25 mean negative, marginal Sharpe negative, corr 0.24-0.31), C11/C12 (range fades: standalone mean negative, DEAD), C10 (trade-modifier, paired from the library), C13 (YM has no L2: mapped with 1 tick/side + 4.84).
* ES and RTY mbp-10 start 2023-08: the 2023-02..2023-07 trades of C02/C06 keep the mapped price (disclosed).
* Identity tests (independent NT8-style replay from 1-min bars, x_chop.py / x_rsi2.py): RSI2C_s20 0/312, ES_RSI2_t10 0/301, IBS_t20_n1 0/585, RSI2T_t10 0/218, COMB_c3_R 0/746, RTY_IBS_t20_n1 1 extra of 449 (0.2%); ORB Asia and the range books: not tested at this stage.
* No cell was dropped or changed on this stage. The final stage will read the holdout 2025-07..2026-10 and the 2023-04..2024-01 span once (track DS3_TCHOP).
