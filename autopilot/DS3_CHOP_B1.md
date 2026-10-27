# DS3_CHOP_B1 - T-CHOP full scope, block (i): each entry family ungated, natural bar and bracket (D3CH 2026-10-27)
Prereg l2vast/ds3/prereg/T-CHOP_B1_prereg.md sha256 172cf8cc65d31a6eb9c2f585556abfc36edbf1d91dc2315c819edca61494c063 (28 cells, ledger +28); pre-holdout text DS3_TCHOP_B1_PREHOLD.md; one holdout look (track DS3_TCHOP_B1). Mapped basis (1-min bars, 1 tick/side + stop slip 1.0 pt + 4.84/lot). Reference control: RSI2T_t10 (Sharpe 1.21, corr -0.12, L25 +26.3k, dMaxDD -43k).
**Block (i): 0 PASS (G8 pending), 1 CANDIDATE of 28.**

## All cells
| cell | tr/wk | lots | WF $/wk | HOLD $/wk | X-span $/wk | Sharpe | corr stack WF [HOLD] | L25 $/wk | chop(+60) | marg WF/HOLD | dMaxDD WF/HOLD | placebo a / b | tier | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X01 NQ_RSI2lt5_SMA200 | 0.13 | 25.7 | 3.8k | 9.9k | 3.3k | 0.48 | -0.16 [-0.19] | 21.6k | -5.2k | -0.38/+0.25 | -123.8k/-139.3k | 0.77 / 0.73 | DEAD | G4, G5, G6a, G6b, M |
| X02 NQ_RSI2gt90_short_belowSMA200 | 0.06 | 45.1 | -3.1k | 0.0k | 0.0k | -0.39 | +0.11 [+nan] | -16.7k | 114.8k | -0.61/+0.00 | 90.7k/-89.4k | 0.38 / 0.46 | DEAD | G2, G4, G5, G6a, G6b, G7, M |
| X03 ES_RSI2lt10_SMA200 | 0.32 | 40.8 | 15.7k | 21.8k | 6.8k | 1.98 | -0.11 [-0.15] | 25.8k | 194.8k | -0.72/-1.03 | 318.1k/410.0k | 0.99 / 1.00 | DEAD | G4, M |
| X04 RTY_RSI2lt10_SMA200 | 0.31 | 63.1 | 11.5k | 24.3k | -8.4k | 1.45 | -0.20 [-0.20] | 30.0k | 147.5k | +0.10/+0.15 | 111.6k/203.5k | 0.99 / 1.00 | DEAD | G4, G7, M |
| X05 YM_RSI2lt10_SMA200 | 0.44 | 48.8 | 8.0k | 15.5k | 6.8k | 1.00 | -0.11 [-0.25] | 8.3k | 64.1k | -0.68/+0.57 | 825.3k/-42.3k | 0.90 / 0.92 | DEAD | G4, G6a, G6b, M |
| X06 NQ_IBSlt0.2_SMA200 | 0.64 | 12.5 | 9.6k | 17.4k | 8.8k | 1.21 | -0.16 [-0.19] | 30.6k | 328.1k | +0.40/+0.94 | -48.7k/-35.9k | 0.95 / 0.95 | DEAD | G6a, M |
| X07 NQ_IBSgt0.8_short_belowSMA200 | 0.12 | 21.8 | -2.6k | -7.2k | 0.0k | -0.32 | +0.11 [+0.03] | -4.8k | 189.2k | -0.12/+0.00 | 0.0k/0.0k | 0.34 / 0.46 | DEAD | G2, G4, G5, G6a, G6b, G7, M |
| X08 NQ_down2_SMA200 | 0.79 | 10.1 | 6.0k | 7.7k | 6.2k | 0.75 | -0.15 [-0.26] | 19.7k | 120.5k | +0.34/+0.39 | -93.2k/-9.9k | 0.83 / 0.84 | DEAD | G6a, G6b, M |
| X09 NQ_down3_SMA200 | 0.33 | 17.2 | 11.7k | 12.3k | 8.2k | 1.48 | -0.05 [-0.23] | 22.6k | 248.3k | +0.49/+0.84 | -129.2k/-67.4k | 0.98 / 1.00 | CANDIDATE | M |
| X10 NQ_zreg20_le-2_SMA200 | 0.24 | 25.2 | 6.2k | 15.5k | -0.4k | 0.79 | -0.10 [-0.11] | 11.5k | -24.3k | -0.33/-0.05 | -7.4k/-81.9k | 0.77 / 0.80 | DEAD | G4, G5, G6a, G6b, G7, M |
| X11 NQ_RSI2lt20_SMA200 | 0.73 | 12.5 | 11.2k | 13.9k | 7.4k | 1.40 | -0.07 [-0.19] | 20.4k | 227.8k | +0.52/+0.78 | -55.5k/-19.2k | 0.93 / 0.97 | DEAD | G6a, M |
| X12 Basket4_RSI2lt20_SMA200 | 2.94 | 11.0 | 13.9k | 23.5k | -0.9k | 1.74 | -0.15 [-0.26] | 26.1k | 198.4k | +0.73/+1.50 | 138.5k/-3.8k | 1.00 / 1.00 | DEAD | G4, G7, M |
| X13 Boll20_2_5m | 62.06 | 11.4 | -20.1k | -28.3k | -15.2k | -2.53 | -0.34 [-0.32] | 6.7k | -116.7k | -1.34/-1.91 | -23.7k/68.3k | 0.10 / 0.09 | DEAD | G2, G4, G5, G6a, G6b, G7 |
| X14 Kelt20_2_5m | 49.62 | 11.6 | -26.2k | -27.6k | -10.2k | -3.30 | -0.33 [-0.47] | 4.0k | 78.9k | -1.68/-1.69 | 18.9k/-15.4k | 0.00 / 0.00 | DEAD | G2, G4, G6a, G6b, G7 |
| X15 VWAP2sig_reject | 139.08 | 5.5 | -32.9k | -43.2k | -16.5k | -4.14 | -0.40 [-0.45] | -6.6k | -740.7k | -2.15/-2.72 | 97.9k/114.4k | 0.00 / 0.00 | DEAD | G2, G4, G5, G6a, G6b, G7 |
| X16 VWAP3sig_reject | 79.36 | 7.1 | -15.7k | -19.7k | -5.0k | -1.97 | -0.41 [-0.55] | 15.5k | 59.2k | -0.88/-1.09 | -61.0k/-40.4k | 0.13 / 0.11 | DEAD | G2, G4, G6a, G6b, G7 |
| X17 PDHL_sweep_fade | 1.49 | 63.3 | -9.4k | -2.5k | -5.7k | -1.19 | +0.00 [+0.10] | -15.6k | -460.4k | -0.82/-0.49 | -184.5k/-161.4k | 0.22 / 0.36 | DEAD | G2, G4, G5, G6a, G6b, G7, M |
| X18 ONHL_sweep_fade_NY | 2.58 | 50.8 | -7.0k | -2.5k | -9.9k | -0.88 | -0.02 [-0.12] | -10.4k | -343.8k | -0.67/-0.26 | -101.9k/-156.9k | 0.48 / 0.55 | DEAD | G2, G4, G5, G6a, G6b, G7, M |
| X19 OR_sweep_fade | 3.35 | 49.6 | -11.6k | -5.0k | -10.2k | -1.46 | -0.13 [-0.13] | -3.7k | -788.5k | -0.95/-0.67 | -135.0k/-168.0k | 0.22 / 0.30 | DEAD | G2, G4, G5, G6a, G6b, G7 |
| X20 Asia_range_fade_London | 3.92 | 63.4 | -11.5k | -14.6k | -7.7k | -1.44 | -0.32 [-0.18] | 15.2k | 118.3k | -0.60/-0.95 | -200.5k/-144.1k | 0.62 / 0.74 | DEAD | G2, G4, G6a, G6b, G7 |
| X21 London_range_fade_NY | 2.87 | 49.8 | -5.8k | 1.5k | -7.2k | -0.72 | -0.06 [-0.08] | -8.3k | -316.7k | -0.68/-0.17 | -139.5k/-121.5k | 0.72 / 0.67 | DEAD | G4, G5, G6a, G6b, G7, M |
| X22 KB_failed_break_fade | 28.06 | 28.3 | -31.6k | -35.2k | -20.4k | -3.98 | -0.26 [-0.25] | -14.1k | -1125.6k | -1.98/-2.19 | 5.0k/-15.7k | 0.11 / 0.16 | DEAD | G2, G4, G5, G6a, G6b, G7 |
| X23 SM_failed_break_fade | 7.60 | 69.7 | -31.0k | -26.6k | -24.1k | -3.90 | +0.07 [-0.05] | -30.9k | -853.0k | -2.13/-1.96 | -62.3k/-70.4k | 0.36 / 0.33 | DEAD | G2, G4, G5, G6a, G6b, G7 |
| X24 Gap_fill | 2.09 | 37.9 | 2.6k | 2.9k | -8.9k | 0.33 | -0.16 [-0.08] | 12.2k | 74.2k | +0.02/-0.03 | -87.2k/4.8k | 0.93 / 0.72 | DEAD | G4, G6a, G6b, G7, M |
| X25 FirstHour_reversal | 0.00 | 1.0 | 0.0k | 0.0k | -0.0k | nan | +nan [+nan] | 0.0k | 0.0k | +0.00/+0.00 | 0.0k/0.0k | nan / nan | DEAD | G2, G3, G4, G5, G6a, G6b, G7, M |
| X26 EndAsia_reversal | 3.27 | 54.1 | -15.3k | -30.8k | -4.8k | -1.93 | -0.16 [+0.01] | -4.4k | 244.8k | -0.95/-1.82 | -136.7k/-109.3k | 0.06 / 0.07 | DEAD | G2, G4, G5, G6a, G6b, G7 |
| X27 FOMC_0830_reversion | 0.51 | 117.8 | -6.1k | -2.0k | -3.0k | -0.77 | +0.13 [+0.18] | -19.4k | -145.2k | -0.68/-0.58 | -111.2k/-101.5k | 0.39 / 0.47 | DEAD | G2, G4, G5, G6a, G6b, G7, M |
| X28 NQ_ES_divergence_fade | 55.62 | 8.6 | -23.3k | -24.6k | -10.5k | -2.93 | -0.28 [-0.49] | -1.3k | -173.5k | -1.64/-1.65 | -106.3k/-51.3k | 0.00 / 0.00 | DEAD | G2, G4, G5, G6a, G6b, G7 |

## Top 10 by the 2.1 target (conditions met: corr<=0.2, L25>0, chop>0, marginal>0, dMaxDD<0, Sharpe>=0.8)
| rank | cell | target conditions met (of 6) | Sharpe | corr | L25 | failed gates | per-trade MDE | forward weeks to settle |
|---|---|---|---|---|---|---|---|---|
| 1 | X09 NQ_down3_SMA200 | 6 | 1.48 | -0.05 | 22.6k | M | 2.64e+03 ($/trade) on n=47 | M gate: 453 wk to 150 trades at 0.33/wk |
| 2 | X11 NQ_RSI2lt20_SMA200 | 6 | 1.40 | -0.07 | 20.4k | G6a, M | 1.69e+03 ($/trade) on n=104 | M gate: 205 wk to 150 trades at 0.73/wk |
| 3 | X06 NQ_IBSlt0.2_SMA200 | 6 | 1.21 | -0.16 | 30.6k | G6a, M | 1.71e+03 ($/trade) on n=91 | M gate: 234 wk to 150 trades at 0.64/wk |
| 4 | X12 Basket4_RSI2lt20_SMA200 | 5 | 1.74 | -0.15 | 26.1k | G4, G7, M | 759 ($/trade) on n=418 | M gate: 51 wk to 150 trades at 2.94/wk |
| 5 | X04 RTY_RSI2lt10_SMA200 | 5 | 1.45 | -0.20 | 30.0k | G4, G7, M | 692 ($/trade) on n=44 | M gate: 484 wk to 150 trades at 0.31/wk |
| 6 | X08 NQ_down2_SMA200 | 5 | 0.75 | -0.15 | 19.7k | G6a, G6b, M | 1.83e+03 ($/trade) on n=112 | M gate: 190 wk to 150 trades at 0.79/wk |
| 7 | X24 Gap_fill | 5 | 0.33 | -0.16 | 12.2k | G4, G6a, G6b, G7, M | 0.276 (R) on n=297 | M gate: 72 wk to 150 trades at 2.09/wk |
| 8 | X03 ES_RSI2lt10_SMA200 | 4 | 1.98 | -0.11 | 25.8k | G4, M | 1.07e+03 ($/trade) on n=46 | M gate: 463 wk to 150 trades at 0.32/wk |
| 9 | X05 YM_RSI2lt10_SMA200 | 4 | 1.00 | -0.11 | 8.3k | G4, G6a, G6b, M | 671 ($/trade) on n=63 | M gate: 338 wk to 150 trades at 0.44/wk |
| 10 | X20 Asia_range_fade_London | 4 | -1.44 | -0.32 | 15.2k | G2, G4, G6a, G6b, G7 | 0.207 (R) on n=556 | M gate: 38 wk to 150 trades at 3.92/wk |
