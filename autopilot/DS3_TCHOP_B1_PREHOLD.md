# DS3_TCHOP_B1 pre-holdout text (WF-PRE 2024-02..2025-06 only; prereg T-CHOP_B1_prereg.md sha256 172cf8cc65d31a6eb9c2f585556abfc36edbf1d91dc2315c819edca61494c063)

Mapped basis, equal risk to ST10 WF-PRE SD, stack = DS2+DS3 (PB3B_R5_P1). Numbers: out/CHOP/chop_pre_B1.json, B1_placebo_pre.json.

| cell | trades/wk | equal-risk lots | mean/wk | Sharpe | corr stack | L25 $/wk | chop(+60) total | marginal Sharpe | dMaxDD cap | placebo (a) / (b) rank | n |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X01 NQ_RSI2lt5_SMA200 | 0.09 | 37.7 | -2.5k | -0.34 | -0.12 | 1.2k | -84.7k | -0.89 | -123.1k | 0.30 / 0.31 | 7 |
| X02 NQ_RSI2gt90_short_belowSMA200 | 0.12 | 30.2 | -3.9k | -0.53 | +0.16 | -21.1k | 77.6k | -0.96 | 89.0k | 0.34 / 0.42 | 9 |
| X03 ES_RSI2lt10_SMA200 | 0.28 | 47.2 | 11.6k | 1.59 | -0.07 | 13.3k | 103.8k | +0.44 | 130.3k | 0.91 / 0.95 | 21 |
| X04 RTY_RSI2lt10_SMA200 | 0.24 | 99.9 | -0.4k | -0.06 | -0.25 | 19.8k | -4.5k | +0.04 | 36.8k | 0.48 / 0.44 | 18 |
| X05 YM_RSI2lt10_SMA200 | 0.48 | 54.3 | 1.2k | 0.16 | +0.06 | -4.6k | -6.9k | -1.26 | 563.9k | 0.47 / 0.52 | 36 |
| X06 NQ_IBSlt0.2_SMA200 | 0.68 | 14.9 | 2.8k | 0.38 | -0.13 | 8.0k | 190.4k | -0.06 | -48.7k | 0.56 / 0.58 | 51 |
| X07 NQ_IBSgt0.8_short_belowSMA200 | 0.19 | 17.6 | 1.3k | 0.18 | +0.16 | -7.3k | 159.1k | -0.20 | -4.8k | 0.66 / 0.64 | 14 |
| X08 NQ_down2_SMA200 | 0.72 | 13.7 | 6.0k | 0.82 | +0.03 | -1.9k | 200.7k | +0.28 | -93.2k | 0.65 / 0.74 | 54 |
| X09 NQ_down3_SMA200 | 0.29 | 18.3 | 11.8k | 1.61 | +0.17 | -0.1k | 227.7k | +0.25 | -129.2k | 0.94 / 0.99 | 22 |
| X10 NQ_zreg20_le-2_SMA200 | 0.25 | 32.3 | -2.9k | -0.40 | -0.08 | -2.9k | 9.1k | -0.60 | -6.7k | 0.35 / 0.30 | 19 |
| X11 NQ_RSI2lt20_SMA200 | 0.64 | 13.9 | 9.6k | 1.30 | +0.08 | 8.5k | 217.1k | +0.29 | -55.5k | 0.83 / 0.91 | 48 |
| X12 Basket4_RSI2lt20_SMA200 | 2.79 | 11.2 | 5.0k | 0.68 | -0.04 | 9.0k | 150.1k | +0.14 | 138.5k | 0.72 / 0.74 | 209 |
| X13 Boll20_2_5m | 59.67 | 11.4 | -12.4k | -1.69 | -0.37 | 13.4k | 302.4k | -0.81 | -91.5k | 0.63 / 0.67 | 4475 |
| X14 Kelt20_2_5m | 47.08 | 10.8 | -23.0k | -3.13 | -0.20 | -1.5k | 244.7k | -1.65 | 18.9k | 0.00 / 0.00 | 3531 |
| X15 VWAP2sig_reject | 136.12 | 5.6 | -23.5k | -3.21 | -0.35 | -2.0k | -99.8k | -1.70 | 97.9k | 0.02 / 0.02 | 10209 |
| X16 VWAP3sig_reject | 81.67 | 7.9 | -13.1k | -1.79 | -0.26 | 8.4k | 219.7k | -0.70 | -61.0k | 0.55 / 0.48 | 6125 |
| X17 PDHL_sweep_fade | 1.67 | 61.7 | -15.1k | -2.06 | -0.10 | -12.9k | -527.0k | -1.08 | -184.8k | 0.06 / 0.10 | 125 |
| X18 ONHL_sweep_fade_NY | 3.07 | 46.1 | -9.7k | -1.32 | +0.08 | -11.6k | -130.6k | -0.93 | -98.2k | 0.30 / 0.40 | 230 |
| X19 OR_sweep_fade | 3.47 | 54.5 | -19.5k | -2.67 | -0.13 | -9.3k | -450.3k | -1.21 | -133.5k | 0.08 / 0.08 | 260 |
| X20 Asia_range_fade_London | 3.96 | 58.2 | -7.2k | -0.99 | -0.45 | 23.4k | 114.9k | -0.25 | -201.4k | 0.77 / 0.83 | 297 |
| X21 London_range_fade_NY | 3.37 | 50.4 | -12.4k | -1.70 | -0.04 | -6.4k | -212.5k | -1.07 | -139.0k | 0.28 / 0.32 | 253 |
| X22 KB_failed_break_fade | 23.33 | 29.6 | -29.9k | -4.08 | -0.26 | -21.3k | -614.7k | -1.82 | 15.7k | 0.10 / 0.12 | 1750 |
| X23 SM_failed_break_fade | 7.12 | 58.5 | -26.8k | -3.65 | +0.16 | -30.0k | -500.7k | -2.11 | -84.5k | 0.14 / 0.14 | 534 |
| X24 Gap_fill | 1.97 | 35.5 | 2.3k | 0.31 | -0.25 | 16.0k | 155.3k | +0.08 | -151.3k | 0.91 / 0.56 | 148 |
| X25 FirstHour_reversal | 0.00 | 1.0 | 0.0k | nan | +nan | 0.0k | 0.0k | +0.00 | 0.0k | nan / nan | 0 |
| X26 EndAsia_reversal | 2.88 | 60.5 | -1.8k | -0.24 | -0.39 | 28.9k | 202.0k | -0.22 | -135.0k | 0.89 / 0.91 | 216 |
| X27 FOMC_0830_reversion | 0.52 | 106.1 | -8.5k | -1.17 | +0.08 | -12.1k | 39.3k | -0.74 | -84.9k | 0.14 / 0.23 | 39 |
| X28 NQ_ES_divergence_fade | 48.87 | 9.4 | -23.7k | -3.23 | -0.02 | -27.2k | 87.9k | -1.59 | -106.3k | 0.00 / 0.00 | 3665 |

Reading (pre-holdout): intraday band/range/failed-breakout fades are negative after cost on NQ ungated (mean R/trade -0.02..-0.11), placebo ranks mostly <0.7; X25 produced 0 trades in WF-PRE (rule too tight, reported DEAD for count). Candidates for block (ii) gating chosen from WF-PRE: best cell per family by WF-PRE target conditions: dip-buy X09/X11/X03 (X11 for frequency), band X13/X16, range X20/X26 (Asia-London and end-of-Asia fades have corr -0.45/-0.39 and L25 +23k/+29k despite negative mean), gap X24, failed-breakout X22, cross X28, events X27. No cell changed or dropped.
