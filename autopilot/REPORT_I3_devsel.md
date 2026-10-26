# REPORT I3
**Verdict: NO** (2/7 measured gates pass). Selected cell kind=post, E=T+5, ev=FOMC, mode=fade, H=30; additive @20% clean/H1/H2 -0.06/+0.08/+0.20; standalone all-in weekly Sharpe 0.32 (2013-26 0.11, dev 2013-22 0.07); pair-window trades 50 (SMALL-SAMPLE). Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

FOMC/NFP drift (ES+NQ): pre-FOMC long into 13:55 ET, and follow/fade of the first 5-minute post-release move (FOMC 14:00, NFP 08:30); NFP dates before 2023 use the UNVERIFIED BLS rule; FOMC 2013-22 from memory. Small-sample by construction. Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on 2013-2022, one cell read on the pair window; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


## Selection (2013-2022 development span; pair window untouched until one cell was chosen)
Grid 16 cells, eligible (>= 60 dev trades and net>0 in >=6 of 10 years): 3. Top cells by dev weekly Sharpe:

| kind   | E        | ev   | mode   | H     |   n |   sharpe |    net |   ypos | eligible   |
|:-------|:---------|:-----|:-------|:------|----:|---------:|-------:|-------:|:-----------|
| pre    | D-1_1400 | FOMC | long   | 1355  | 158 |    0.374 |  4.394 |      4 | False      |
| post   | T+5      | NFP  | fade   | close | 233 |    0.239 |  4.618 |      5 | False      |
| post   | T+5      | FOMC | fade   | 30    | 155 |    0.075 |  0.538 |      6 | True       |
| post   | T+5      | FOMC | fade   | close | 155 |    0.030 |  0.454 |      7 | True       |
| post   | T+5      | NFP  | fade   | 60    | 233 |    0.010 |  0.067 |      5 | False      |
| post   | T+5      | FOMC | fade   | 60    | 155 |   -0.031 | -0.364 |      4 | False      |
| post   | T+5      | NFP  | fade   | 30    | 233 |   -0.078 | -0.468 |      6 | True       |
| pre    | D_0000   | FOMC | long   | 1355  | 149 |   -0.157 | -1.458 |      3 | False      |
| post   | T+5      | FOMC | follow | 60    | 155 |   -0.185 | -2.138 |      4 | False      |
| post   | T+5      | FOMC | follow | close | 155 |   -0.197 | -2.956 |      3 | False      |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected dev Sharpe 0.07; replicate best-eligible median 0.45, p95 0.76; real beats 3% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=7.235e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | -0.021 | +0.072 | +0.109 | +0.029 | +5.7 | [-0.043, +0.103] | 0.65 | NO |
| 20% | add | -0.057 | +0.083 | +0.199 | +0.039 | +17.8 | [-0.110, +0.180] | 0.65 | NO |
| 30% | add | -0.108 | +0.045 | +0.272 | +0.029 | +29.9 | [-0.198, +0.236] | 0.65 | NO |
| 50% | add | -0.241 | -0.115 | +0.369 | -0.038 | +54.0 | [-0.429, +0.294] | 0.65 | NO |
| 10% | const | -0.025 | +0.076 | +0.120 | +0.032 | -3.6 | [-0.050, +0.113] | 0.65 | NO |
| 20% | const | -0.081 | +0.069 | +0.238 | +0.036 | -0.9 | [-0.152, +0.213] | 0.65 | NO |
| 30% | const | -0.189 | -0.050 | +0.341 | -0.008 | +1.8 | [-0.341, +0.274] | 0.65 | NO |
| 50% | const | -0.625 | -0.583 | +0.439 | -0.314 | +57.5 | [-1.059, +0.296] | 0.65 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net -349,089, Sharpe -0.38, maxDD 737,867, worst wk -430,946; H1: net 275,471, Sharpe 0.88, maxDD 159,702, worst wk -159,702; H2: net 557,510, Sharpe 2.02, maxDD 16,812, worst wk -16,812; all: net 483,892, Sharpe 0.32, maxDD 737,867, worst wk -430,946
Correlation with pair (weekly): clean -0.17, H1 +0.07, H2 +0.26, all -0.03; worst-decile weeks (n=17) corr -0.43, sleeve mean in those weeks $-4,115, positive share 0.06.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.40 | 2.61 | 4.28 | -82,054 | -79,866 | 294,478 | -97,223 | 41.9 |
| clean | add 30% | 1.35 | 2.51 | 4.06 | -83,759 | -80,796 | 301,663 | -107,179 | 41.9 |
| clean | const 20% | 1.38 | 2.56 | 4.17 | -66,325 | -64,264 | 238,456 | -81,761 | 41.9 |
| clean | const 30% | 1.27 | 2.35 | 3.80 | -60,166 | -57,394 | 217,630 | -83,986 | 43.8 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.91 | 6.65 | 3.53 | -77,610 | -66,030 | 183,653 | -78,287 | 42.9 |
| H1 | add 30% | 2.87 | 6.84 | 3.39 | -77,610 | -66,030 | 199,623 | -78,287 | 42.9 |
| H1 | const 20% | 2.90 | 6.76 | 3.46 | -62,088 | -52,824 | 153,311 | -62,630 | 42.9 |
| H1 | const 30% | 2.78 | 6.94 | 3.23 | -54,327 | -46,335 | 154,110 | -54,801 | 42.9 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.49 | 5.45 | 4.01 | -80,081 | -77,568 | 217,425 | -80,509 | 44.4 |
| H2 | add 30% | 2.57 | 5.83 | 4.27 | -80,922 | -76,759 | 217,425 | -82,190 | 44.4 |
| H2 | const 20% | 2.53 | 5.64 | 4.14 | -64,401 | -61,731 | 173,940 | -65,080 | 44.4 |
| H2 | const 30% | 2.64 | 6.32 | 4.60 | -57,402 | -53,004 | 152,198 | -59,046 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.89 | 3.75 | 9.45 | -81,197 | -79,316 | 294,478 | -97,223 | 42.9 |
| all | add 30% | 1.88 | 3.79 | 9.38 | -82,520 | -80,017 | 301,663 | -107,179 | 42.9 |
| all | const 20% | 1.89 | 3.77 | 9.41 | -65,487 | -63,733 | 238,456 | -81,761 | 42.9 |
| all | const 30% | 1.85 | 3.79 | 9.30 | -58,955 | -56,642 | 217,630 | -83,986 | 44.0 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: -0.057 / +0.083 / +0.199
- [PASS] 3 worst week within share: all-in worst week +17.8% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.32 vs p95 0.63 (rank 0.85)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.110, +0.180]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 50% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: -0.070 / +0.074 / +0.193
- [PASS] 6 worst-decile corr <=+0.30: -0.43
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section I3); 2 selection on 2013-2022 only, pair window read once for one cell
- [INFO] 7 executability: see below; small-sample flag: YES (50 trades in pair window)

Plateau neighbours (all-in 20% uplift; selected +0.039):
- {'kind': 'post', 'E': 'T+5', 'ev': 'FOMC', 'mode': 'fade', 'H': '22'}: +0.044 (trades 50)
- {'kind': 'post', 'E': 'T+5', 'ev': 'FOMC', 'mode': 'fade', 'H': '38'}: -0.061 (trades 50)

Own random-entry null: 500 draws, standalone all-in Sharpe median -0.31, p95 0.63, real 0.32. Standalone Sharpe at 2x slippage 0.27.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 14 | -1 | -1.51 |
| 2014 | 16 | 0 | 0.39 |
| 2015 | 16 | -0 | -0.05 |
| 2016 | 15 | 1 | 1.58 |
| 2017 | 16 | -0 | -0.93 |
| 2018 | 16 | 0 | 0.31 |
| 2019 | 16 | -0 | -0.99 |
| 2020 | 14 | 0 | 1.38 |
| 2021 | 16 | 1 | 1.11 |
| 2022 | 16 | 0 | 0.37 |
| 2023 | 16 | -0 | -0.95 |
| 2024 | 16 | -1 | -0.80 |
| 2025 | 16 | 1 | 1.07 |
| 2026 | 12 | 1 | 2.10 |


DONE I3