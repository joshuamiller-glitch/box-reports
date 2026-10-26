# DS3_TC - T-C other instruments, CTA approach (D3CT, 2026-10-26)

**Verdict: 0 PASS, 0 CANDIDATE, 28 DEAD. No book registered to PAPER-ALL; DS3 pool contribution 0 (want 6, min 1 not met; the evidence says there is nothing here to add).** No PASS, so no 3x3 grid (addendum 2) was run.

Prereg `l2vast/ds3/prereg/T-C_prereg.md` sha256 `7a38325d94e36a0a1601de8060a9227a6717440363125d10c52b90e0fdca07a0` (28 cells, ledger cumulative 28,588, DECISIONS.md). Pre-holdout text `l2vast/ds3/out/TC/PREHOLD.md` logged with `log_holdout_look('TC')` before any WF-full/holdout number was computed; the 2023-04..2024-01 look is logged with it. Rows `l2vast/ds3/rows/DS3_TC.json`; daily series per cell `l2vast/ds3/out/TC/<cell>_daily.parquet` (ld, pnl, trades), `cell_series.pkl`, `corr_cells.csv`. Code `l2vast/ds3/code/tc_{load,engine,run,score,pre,final,prereg}.py`.

## Method (as preregistered)
1-min Databento continuous (.v.0) for ES, RTY(2017-), YM, CL, GC, ZN, 6E, 6J, MBT, MET (2022-); CME BTC not scored separately (same price as MBT). Hourly and CME-trading-day bars; signals on the completed bar, fill at next-bar open. 9 candidates per market-horizon (Supertrend / Donchian stop-and-reverse / time-series momentum, 3 params each), ATR trailing stop (H1 4xATR24, D1 3xATR20), monthly WF re-fit on trailing 500 (H1) / 750 (D1) days net Sharpe (flat if best <= 0, round trip charged on switch). Risk parity: lots = $1,000/day / trailing 60-day vol, equal-risk baskets. Roll: continuous back-adjusted by price difference at every instrument_id change; roll-bar gap removed from P&L, one RT charged per roll while in position; roll-spanning trades kept. Cost proxy: commission RT $4.84 (ES standard value as proxy for RTY, YM, CL, GC, ZN, 6E, 6J), $1.78 (FEES.md micro) for MBT, MET, plus 1 tick per side and 1 extra tick on stop exits; 1.5x and 2x re-run with the 1x selection. Caveats: the commission proxy is the ES value for non-index contracts (stated, not verified); MBT/MET 1-tick slippage is only $0.50/$0.05 per side, so their costs are the weakest evidence; family cells have no 1.5x/2x re-run.

## Results (WF = 2024-02..2026-10 weekly $ at $1,000/day/market risk; 142 weeks; SD in $/wk)

| cell | WF mean | WF SD | MDE (80%) | HOLD mean | L8W | IS | 2023-04..24-01 | trades/wk | 2x WF mean | pre-2023 t (2014-22) | placebo | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TC_ES_H1 | 24 | 1000 | 235 | -43 | 290 | -14 | 31 | 1.16 | 4 | -0.52 | 0.29 | DEAD |
| TC_ES_D1 | -52 | 1616 | 380 | -55 | 0 | 241 | 128 | 0.15 | -55 | 0.22 | 0.20 | DEAD |
| TC_RTY_H1 | 15 | 1167 | 274 | -24 | 161 | -104 | 45 | 1.89 | -9 | -1.11 | 0.27 | DEAD |
| TC_RTY_D1 | 2 | 1051 | 247 | 36 | 34 | -165 | -172 | 0.06 | 1 | -1.58 | 0.25 | DEAD |
| TC_YM_H1 | 2 | 847 | 199 | -134 | -54 | -172 | -155 | 0.90 | -8 | 0.26 | 0.25 | DEAD |
| TC_YM_D1 | -56 | 1147 | 270 | -58 | 0 | -3 | 42 | 0.16 | -58 | 0.03 | 0.18 | DEAD |
| TC_CL_H1 | -4 | 979 | 230 | 6 | 97 | -279 | -209 | 1.59 | -33 | -0.59 | 0.23 | DEAD |
| TC_CL_D1 | -164 | 1085 | 255 | -140 | 0 | -379 | -448 | 0.15 | -169 | 1.89 | 0.12 | DEAD |
| TC_GC_H1 | -33 | 918 | 216 | 81 | 90 | 131 | 163 | 0.93 | -42 | 0.26 | 0.20 | DEAD |
| TC_GC_D1 | -55 | 1405 | 330 | 7 | -24 | -83 | -218 | 0.17 | -58 | 0.61 | 0.19 | DEAD |
| TC_ZN_H1 | -28 | 811 | 191 | -165 | 0 | -42 | -30 | 0.34 | -80 | -1.92 | 0.20 | DEAD |
| TC_ZN_D1 | -55 | 1348 | 317 | -181 | 0 | -59 | -184 | 0.11 | -76 | -1.50 | 0.19 | DEAD |
| TC_6E_H1 | -136 | 700 | 165 | -89 | -102 | -17 | -35 | 0.52 | -160 | -1.21 | 0.11 | DEAD |
| TC_6E_D1 | -18 | 1703 | 400 | 56 | 711 | 225 | 265 | 0.18 | -28 | 0.33 | 0.23 | DEAD |
| TC_6J_H1 | -125 | 919 | 216 | -162 | 106 | 190 | 320 | 1.59 | -193 | -0.04 | 0.13 | DEAD |
| TC_6J_D1 | 88 | 1702 | 400 | -36 | 126 | 275 | 390 | 0.18 | 78 | -0.47 | 0.33 | DEAD |
| TC_MBT_H1 | 33 | 1300 | 306 | 136 | -2 | 41 | -69 | 1.73 | 8 | -1.03 | 0.29 | DEAD |
| TC_MBT_D1 | -26 | 1629 | 383 | -102 | -28 | -37 | -44 | 0.11 | -29 | 0.00 | 0.23 | DEAD |
| TC_MET_H1 | -8 | 406 | 96 | 7 | -120 | -20 | 0 | 0.15 | -37 | -1.00 | 0.22 | DEAD |
| TC_MET_D1 | -36 | 1081 | 254 | 34 | -123 | 0 | 0 | 0.13 | -69 | 0.00 | 0.20 | DEAD |
| TC_B_H1 | -259 | 3545 | 833 | -388 | 465 | -286 | 60 | 10.81 | -550 | -1.31 | 0.25 | DEAD |
| TC_B_D1 | -371 | 4830 | 1135 | -439 | 696 | 15 | -240 | 1.39 | -465 | 0.21 | 0.26 | DEAD |
| TC_B_ALL | -630 | 5738 | 1349 | -827 | 1161 | -271 | -180 | 12.20 | -1015 | -0.49 | 0.34 | DEAD |
| TC_X_H1 | -300 | 2460 | 578 | -187 | 68 | 5 | 139 | 6.86 | -537 | -1.21 | 0.22 | DEAD |
| TC_X_D1 | -265 | 4285 | 1007 | -363 | 662 | -58 | -238 | 1.03 | -352 | 0.64 | 0.24 | DEAD |
| TC_FAM_ST_H1 | -158 | 4472 | 1051 | -759 | -1101 | 222 | 272 | 11.11 | n/a | -1.30 | 0.27 | DEAD |
| TC_FAM_DON_H1 | -109 | 1882 | 443 | -298 | -444 | 272 | 321 | 2.34 | n/a | -0.54 | 0.27 | DEAD |
| TC_FAM_TSM_H1 | -529 | 3010 | 708 | -507 | 238 | -197 | 6 | 17.64 | n/a | -2.36 | 0.23 | DEAD |

## Reading
- Every cell is DEAD. The per-market cells: WF means within +-$165/wk of zero (max +$88) against an MDE of $100-400/wk (a null here is inconclusive for effects smaller than the MDE, but the sign pattern is the point: 14 of 20 market cells have WF mean <= 0 (19 of 20 below +$50), holdout is negative in 12 of 20, none clears placebo 0.95; best single-market placebo rank is 0.33).
- Baskets are the clearest read: B_ALL (all 10 markets, hourly+daily) WF -$630/wk (CI [-1,560, +302]), holdout -$827/wk, 12.2 trades/wk (so it would satisfy the >= 3/wk bar if it were positive), 2x cost -$1,015/wk. Cross-asset diversification did not turn single-market noise into a trend premium: B_H1 -$259, B_D1 -$371, ex-equity X_H1 -$300, X_D1 -$265 per week. Basket MDE is $0.8-1.3k/wk, so the baskets cannot rule out a true effect of up to about +$1k/wk, but the point estimates and holdouts are on the wrong side.
- Longer evidence: the same WF procedure over 2014-2022 (476 weeks, outside the harness windows) gives t between -1.3 and +0.6 for baskets (B_ALL -0.49, B_H1 -1.31, B_D1 +0.21, X_D1 +0.64); 9 of 28 cells have positive pre-2023 means, none significant. This is consistent with STRUCT48 T3.1 (D2 signals on 8 markets: all negative standalone): hourly/daily trend on index, rates, FX and energy futures at 2013-2026 costs shows no net edge at 1-tick-per-side costs, and 1-h trend is cost-hungry (hourly baskets trade 7-11 times/wk).
- Daily books fail the >= 3/wk bar as expected (0.06-0.2 trades/wk per market, 1.0-1.4 for 10-market baskets; the hourly baskets and B_ALL do exceed 3/wk). Because the only baskets with >= 3 trades/wk are negative, no DS3 book is proposed from T-C.
- Marginal portfolio Sharpe vs DS2 10/10/7 (sleeve at 0.5 weekly-SD ratio, WF): DS2 alone 1.75; adding any basket lowers it (B_ALL 1.19, B_H1 1.27, B_D1 1.34, X_H1 1.17, X_D1 1.36); single markets lower it slightly (1.56-1.70). Weekly corr to DS2 is small (-0.05..+0.13), i.e. low-correlation but zero-or-negative return, so no diversification credit. Corr to other DS3 books: pool.parquet did not exist at scoring time (pending; irrelevant for DEAD cells).
- Placebo: 500 draws of k random library books (outputs/library, 1,0xx series, each scaled to the candidate's per-book WF weekly SD, summed): the library median book earns more than the CTA cells, so ranks are 0.11-0.34. DSR ~0 for all (28,588 trials). Year-share and holdout single-look: holdout looked once, post-log.

## Executability (all 10 markets)
NT8 charts ES, RTY, YM, CL, GC, ZN, 6E, 6J, MBT, MET from CME data on 60-min and daily bars (24h session template, hour bars anchored at the 18:00 ET session start = UTC-hour aligned); ATR and DonchianChannel are built in; Supertrend is not built in (custom NinjaScript or third-party indicator); TSM is a close-minus-close comparison; trailing ATR stop via SetTrailStop/ managed stops; no L2 needed. Continuous contract: NT8 merge-back-adjusted. exec_status = PENDING (identity test not run, since nothing passes). Not DS3-deliverable anyway.

## Nearest previous cells
STRUCT48 T3.1 (ST+HM on 8 markets, all negative standalone, ZN -84k at unit risk): confirmed here with own parameters, WF-re-fit grids and hourly/daily bars. The BTC assembly-top-5 books were not re-scored (not T-C cells; the MBT cells here, 2022-, give MBT_H1 holdout +$136/wk but WF +$33/wk, CI [-192,+250], placebo 0.29: DEAD).

## Structural question (MORNING.md, not pausing)
Is a slower horizon (weekly bars, multi-month trend, 20+ markets incl. the on-disk ZB, ZF, 6A, 6B, 6C, HG, NG, SI, PL, grains, which would be the standard CTA breadth) worth one prereg? The 10-market basket is far narrower than a real CTA panel; the MDE for a 20-market basket would drop but cost per trade matters less at weekly horizon. Not run (outside the track list).
