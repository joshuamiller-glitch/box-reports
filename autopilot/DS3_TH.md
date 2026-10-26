# DS3_TH - T-H slow breadth trend panel, 27 markets (D3CT, 2026-10-26)

**Verdict: 0 PASS, 0 CANDIDATE, 14 DEAD (all report-only). Pool contribution 0 (want 4, min 1 not met). No PASS, so no 3x3 grid.**

Prereg `l2vast/ds3/prereg/T-H_prereg.md` sha256 `73199c1202fcd1ab63f5b6a2b294ee4d79a0702b58b4c3ef01df5724da2575b2` (14 cells, ledger/DECISIONS.md), frozen before scoring; scoring began after all T-B final rows existed. Pre-holdout text `l2vast/ds3/out/TH/PREHOLD.md` logged with `log_holdout_look('TH')`; the 2023-04..2024-01 look logged with it. Rows `l2vast/ds3/rows/DS3_TH.json`; daily series `l2vast/ds3/out/TH/<cell>_daily.parquet`; code `l2vast/ds3/code/th_engine.py, th_cells.py, th_common.py`; market cost table `l2vast/ds3/out/TH/market_costs.md`.

## Mechanism and prior
Slow vol-targeted time-series momentum (sign of the L-day return, L = 20/40/60, no stop, position resized monthly) across 27 futures pays a trend premium absent from the intraday books. Not a re-run of T-C (hourly/daily Supertrend/Donchian with ATR stops on 10 markets). Nearest scored: TC_B_D1 (WF -$371/wk, DEAD, 2014-22 t +0.21), TC_FAM_TSM_H1 (WF -$529/wk, t -2.36), STRUCT48 T3.1 negative. Predicted +$0.3-0.8k/wk.

## MDE correction (stated openly)
The prereg estimated the 27-market weekly SD at $7-9k (MDE $1.6-2.1k/wk). Measured SD is about $19k/wk (positively correlated risk across the 27 markets at $1k/day each), so the real MDE is about $4.4k/wk (annual-Sharpe MDE 1.70 on 142 WF weeks, 0.93 on 476 pre-2023 weeks). Either way the predicted effect is below the MDE, which is why every cell is report-only: a null here is inconclusive for any effect under about $4k/wk, and a positive would have been a LEAD only.

## Results
| cell | WF mean | WF SD | MDE | CI WF mean | HOLD | L8W | IS | 2023-04..24-01 | trades/wk | 1.5x WF | 2x WF | pre-2023 t | placebo time | placebo lib | corr DS2 | max corr pool | verdict | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TH_ALL27_L20_D | -1974 | 18429 | 4333 | [-4950, 1066] | -1818 | 3662 | -455 | 65 | 14.07 | -2400 | -2827 | -0.00 | 0.22 | 0.33 | 0.03 | 0.69 | DEAD | c1,c2,c4,c5,c6 |
| TH_ALL27_L40_D | 248 | 18944 | 4454 | [-2893, 3133] | -370 | -444 | -2569 | 217 | 8.92 | -55 | -358 | 0.43 | 0.54 | 0.40 | -0.06 | 0.75 | DEAD | c1,c2,c4 |
| TH_ALL27_L60_D | -1452 | 18878 | 4438 | [-4779, 1349] | -216 | -1276 | -3786 | -2442 | 8.44 | -1730 | -2008 | 1.57 | 0.17 | 0.34 | -0.06 | 0.74 | DEAD | c1,c2,c4,c5,c6 |
| TH_ALL27_L40_W | 121 | 17146 | 4031 | [-2572, 2717] | -391 | 1038 | -1897 | 335 | 4.12 | -57 | -234 | 0.45 | 0.50 | 0.39 | -0.14 | 0.79 | DEAD | c1,c2,c4 |
| TH_ALL27_WF | -655 | 11622 | 2732 | [-2589, 1114] | -1757 | -1898 | -3489 | -1512 | 6.54 | -852 | -1048 | 0.87 | 0.33 | 0.36 | -0.04 | 0.56 | DEAD | c1,c2,c4,c5,c6 |
| TH_ALL27ex_EQ_L40_D | 322 | 18363 | 4317 | [-2641, 3278] | -508 | -397 | -2049 | 380 | 7.95 | 26 | -271 | 0.74 | 0.65 | 0.37 | -0.03 | 0.68 | DEAD | c1,c2,c4 |
| TH_EQ_L40_D | -75 | 6026 | 1417 | [-1139, 883] | 138 | -48 | -520 | -163 | 0.97 | -81 | -88 | -0.67 | 0.14 | 0.21 | -0.11 | 0.72 | DEAD | c2,c3,c4,c5,c6 |
| TH_RATES_L40_D | -40 | 8810 | 2071 | [-1609, 1234] | -518 | 3645 | -143 | 1492 | 1.36 | -135 | -229 | 0.81 | 0.61 | 0.25 | 0.03 | 0.82 | DEAD | c1,c2,c3,c4,c5,c6 |
| TH_FX_L40_D | -311 | 7701 | 1811 | [-1579, 897] | -1190 | -4080 | -737 | -322 | 1.72 | -369 | -426 | 0.02 | 0.18 | 0.22 | -0.10 | 0.35 | DEAD | c1,c2,c3,c4,c5,c6 |
| TH_METALS_L40_D | 376 | 7339 | 1726 | [-825, 1547] | 678 | -2543 | -941 | -406 | 1.42 | 365 | 353 | 0.46 | 0.63 | 0.32 | -0.06 | 0.54 | DEAD | c3,c4,c5 |
| TH_ENERGY_L40_D | 222 | 8302 | 1952 | [-1126, 1646] | 730 | 2387 | -310 | -269 | 1.25 | 205 | 188 | 0.94 | 0.60 | 0.30 | 0.08 | 0.57 | DEAD | c2,c3,c4,c5 |
| TH_GRAINS_L40_D | -463 | 4879 | 1147 | [-1205, 318] | -756 | -448 | -852 | -1139 | 1.03 | -519 | -576 | -0.27 | 0.14 | 0.15 | 0.08 | -0.34 | DEAD | c1,c2,c3,c4,c5,c6 |
| TH_LIVESTOCK_L40_D | 153 | 2869 | 674 | [-307, 623] | 174 | 342 | 728 | 713 | 0.53 | 134 | 114 | 0.20 | 0.66 | 0.26 | -0.13 | 0.36 | DEAD | c3,c4 |
| TH_CRYPTO_L40_D | 386 | 3587 | 843 | [-177, 993] | 373 | 300 | 206 | 311 | 0.65 | 345 | 305 | 0.15 | 0.96 | 0.42 | -0.05 | 0.80 | DEAD | c3,c4 |

Conventions: weekly $ at $1,000/day/market risk parity (fractional lots, monthly resize), 142 WF weeks (2024-02..2026-10), HOLD 2025-07+, cost proxy 1 tick/side + $4.84 RT ($1.78 MBT/MET), roll back-adjusted with one RT charged per roll in position. Fail codes: c1 HOLD mean>0, c2 marginal portfolio Sharpe vs DS2 10/10/7 up, c3 trades/wk>=3, c4 both placebos>=0.95, c5 SPAN23 sign = WF sign and WF>0, c6 WF mean>0. Max corr pool = largest |weekly WF corr| to any of the 31,098 pool books (informational, not gating; the pool contains many near-duplicate families so a maximum over 31k books is inflated). All cells are report-only per the prereg because the predicted effect is below the cell MDE.
Engine bug fixed before any holdout look: a market-closed day (e.g. 2018-12-06 in the rates futures) produced a false gap P&L in the first draft; fixed to take the gap from the last valid close on the next valid day and rerun before the pre-holdout text was logged.

## Reading
- The 27-market daily panel at L=40 has WF +$248/wk (CI [-2,893, +3,133]), holdout -$370/wk, 1.5x cost -$55/wk, 2x -$358/wk. L=20 and L=60 are worse (WF -$1,974 and -$1,452). Weekly sampling gives +$121/wk. WF-refit (monthly choice of L) -$655/wk. The panel does not beat its timing-destroyed placebo (rank 0.54 at L=40, 0.17-0.33 at L=20/60/WF).
- Independent history 2014-2022 (476 weeks): the same rule has t +0.43 (L40), +1.57 (L60), 0.0 (L20), +0.87 (WF): positive but not significant, consistent with a small trend premium far below the WF MDE. In-sample 2023-02..2024-01 is -$2,569/wk (L40): the premium is not stable.
- Sub-panels: metals (+$376/wk), energy (+$222), livestock (+$153) and crypto (+$386) are positive in WF and holdout, but none is significant (e.g. crypto CI [-177, +993], metals [-825, +1,547]), trades/wk are 0.5-1.5 (< 3), and none beats the library placebo (0.26-0.42). Equity, rates, FX and grains are negative to zero. With 8 sub-panels the best-of-8 positives are within chance.
- Trades/wk: the 27-market panel trades 4-14 times per week (>= 3), but its P&L is below the placebos and holdout is negative; sub-panels fail the trade bar.
- Marginal portfolio Sharpe vs DS2 10/10/7 (sleeve at ratio 0.5, WF): DS2 alone 1.75; adding the panel gives 1.65-1.69 (down); sub-panels 1.77-1.95 (up slightly, but they fail holdout/placebo/trade-rate). Weekly corr to DS2 is -0.17..+0.0 (the book is diversifying but earns nothing). Max corr to pool books: 0.5-0.8 for several cells, driven by near-duplicate pool families.
- Executability: NT8 charts all 27 markets on daily bars; the rule is a close-versus-close sign comparison plus a monthly lot resize: trivial NinjaScript, no L2. Margin proxy 5% of notional (stated proxy, no exchange margin file on disk); contract-equivalent lots at $1k/day per market are in `market_costs.md` (MET sizing hits the 100-lot cap; its cost is only $1.88 RT, the weakest cost evidence). exec_status PENDING (no identity test: nothing to deliver).
- Prior held: the T-C result (10 markets, |t| <= 1.3 on 2014-22) predicted exactly this. MDE next to the null: any true premium below about $4k/wk (Sharpe < 1.7) cannot be excluded on 142 weeks.

## Market cost and sizing table
| market | pv | tick $ | RT commission | RT cost $ (comm + 2 ticks) | last price | notional $ | margin proxy 5% | 1-day vol $ (60d, last) | lots at $1k/day |
|---|---|---|---|---|---|---|---|---|---|
| ES | 50 | 12.50 | 4.84 | 29.84 | 7703 | 385,150 | 19,258 | 2,722 | 0.37 |
| RTY | 50 | 5.00 | 4.84 | 14.84 | 2737 | 136,850 | 6,842 | 1,305 | 0.77 |
| YM | 5 | 5.00 | 4.84 | 14.84 | 52200 | 261,000 | 13,050 | 1,963 | 0.51 |
| ZN | 1000 | 15.62 | 4.84 | 36.09 | 105.625 | 105,625 | 5,281 | 319 | 3.13 |
| ZB | 1000 | 31.25 | 4.84 | 67.34 | 105.656 | 105,656 | 5,283 | 625 | 1.60 |
| ZF | 1000 | 7.81 | 4.84 | 20.46 | 104.219 | 104,219 | 5,211 | 219 | 4.56 |
| ZT | 2000 | 7.81 | 4.84 | 20.46 | 102.016 | 204,031 | 10,202 | 189 | 5.29 |
| 6E | 125000 | 6.25 | 4.84 | 17.34 | 1.1265 | 140,812 | 7,041 | 398 | 2.51 |
| 6J | 1.25e+07 | 6.25 | 4.84 | 17.34 | 0.006357 | 79,462 | 3,973 | 469 | 2.13 |
| 6A | 100000 | 10.00 | 4.84 | 24.84 | 0.6939 | 69,390 | 3,469 | 278 | 3.60 |
| 6B | 62500 | 6.25 | 4.84 | 17.34 | 1.3328 | 83,300 | 4,165 | 269 | 3.71 |
| 6C | 100000 | 5.00 | 4.84 | 14.84 | 0.70915 | 70,915 | 3,546 | 192 | 5.21 |
| GC | 100 | 10.00 | 4.84 | 24.84 | 4186.7 | 418,670 | 20,934 | 6,891 | 0.15 |
| SI | 5000 | 25.00 | 4.84 | 54.84 | 57.135 | 285,675 | 14,284 | 7,974 | 0.13 |
| HG | 25000 | 12.50 | 4.84 | 29.84 | 6.562 | 164,050 | 8,203 | 2,366 | 0.42 |
| PL | 50 | 5.00 | 4.84 | 14.84 | 1639.7 | 81,985 | 4,099 | 2,036 | 0.49 |
| CL | 1000 | 10.00 | 4.84 | 24.84 | 101.84 | 101,840 | 5,092 | 3,095 | 0.32 |
| NG | 10000 | 10.00 | 4.84 | 24.84 | 3.117 | 31,170 | 1,559 | 661 | 1.51 |
| HO | 42000 | 4.20 | 4.84 | 13.24 | 4.8932 | 205,514 | 10,276 | 5,686 | 0.18 |
| RB | 42000 | 4.20 | 4.84 | 13.24 | 3.1429 | 132,002 | 6,600 | 3,397 | 0.29 |
| ZC | 50 | 12.50 | 4.84 | 29.84 | 474.25 | 23,712 | 1,186 | 364 | 2.75 |
| ZS | 50 | 12.50 | 4.84 | 29.84 | 1260.5 | 63,025 | 3,151 | 729 | 1.37 |
| ZW | 50 | 12.50 | 4.84 | 29.84 | 659.75 | 32,988 | 1,649 | 734 | 1.36 |
| HE | 400 | 10.00 | 4.84 | 24.84 | 66.875 | 26,750 | 1,338 | 405 | 2.47 |
| LE | 400 | 10.00 | 4.84 | 24.84 | 228.45 | 91,380 | 4,569 | 936 | 1.07 |
| MBT | 0.1 | 0.50 | 1.78 | 2.78 | 81675 | 8,168 | 408 | 182 | 5.48 |
| MET | 0.1 | 0.05 | 1.78 | 1.88 | 2421 | 242 | 12 | 10 | 100.00 |

