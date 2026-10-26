# REPORT I3
**Verdict: NO** (2/7 measured gates pass). Selected cell kind=post, E=T+5, ev=FOMC, mode=follow, H=60; additive @20% clean/H1/H2 +0.17/+0.03/-0.15; standalone all-in weekly Sharpe 0.82 (2013-26 0.01, dev 2013-22 -0.18); pair-window trades 50 (SMALL-SAMPLE). Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

FOMC/NFP drift (ES+NQ): pre-FOMC long into 13:55 ET, and follow/fade of the first 5-minute post-release move (FOMC 14:00, NFP 08:30); NFP dates before 2023 use the UNVERIFIED BLS rule; FOMC 2013-22 from memory. Small-sample by construction. Sleeve protocol (PREREG_AUTOPILOT.md BATCH I): selection on the clean span only (Gate Amendment 2), H1/H2 read once for one cell; basket normalised to 1 ADR-dollar per trade, scaled to the pair's clean weekly sd; fill model 1-minute bar opens (entry and time exit at the open of the stated bar), 1 tick/side + $4.36 per contract RT, 2x = 2 ticks/side. Executable at NinjaTrader Brokerage via Rithmic (CME products); micros for sizing.


## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 16 cells, eligible (>= 15 clean trades): 16. Top cells by clean weekly Sharpe:

| kind   | E        | ev   | mode   | H     |   n |   sharpe |   net |   ypos | eligible   |
|:-------|:---------|:-----|:-------|:------|----:|---------:|------:|-------:|:-----------|
| post   | T+5      | FOMC | follow | 60    |  32 |    1.408 | 4.508 |      3 | True       |
| post   | T+5      | FOMC | follow | close |  32 |    1.097 | 5.586 |      3 | True       |
| pre    | D_0000   | FOMC | long   | 1355  |  32 |    1.078 | 2.591 |      2 | True       |
| pre    | D-1_1400 | FOMC | long   | 1355  |  32 |    1.063 | 3.867 |      3 | True       |
| pre    | D_0200   | FOMC | long   | 1355  |  32 |    1.047 | 2.338 |      2 | True       |
| post   | T+5      | NFP  | fade   | close |  48 |    0.881 | 4.108 |      2 | True       |
| post   | T+5      | NFP  | fade   | 60    |  48 |    0.758 | 1.133 |      2 | True       |
| pre    | D_0930   | FOMC | long   | 1355  |  32 |    0.662 | 0.749 |      3 | True       |
| post   | T+5      | NFP  | fade   | 30    |  48 |    0.500 | 0.560 |      2 | True       |
| post   | T+5      | FOMC | follow | 30    |  32 |    0.237 | 0.286 |      2 | True       |

Selection-aware null (report only, 30 random-entry replicates of the whole grid selection): real selected clean Sharpe 1.41; replicate best-eligible median 1.26, p95 1.93; real beats 67% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=2.746e+05)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.095 | +0.019 | -0.070 | +0.043 | +4.7 | [-0.011, +0.102] | 0.08 | NO |
| 20% | add | +0.173 | +0.026 | -0.148 | +0.071 | +9.4 | [-0.033, +0.184] | 0.08 | NO |
| 30% | add | +0.232 | +0.023 | -0.235 | +0.085 | +14.1 | [-0.066, +0.248] | 0.08 | NO |
| 50% | add | +0.309 | -0.014 | -0.429 | +0.080 | +23.4 | [-0.166, +0.338] | 0.08 | NO |
| 10% | const | +0.105 | +0.020 | -0.078 | +0.047 | -5.3 | [-0.012, +0.112] | 0.08 | NO |
| 20% | const | +0.204 | +0.026 | -0.191 | +0.080 | -10.6 | [-0.049, +0.216] | 0.08 | NO |
| 30% | const | +0.287 | +0.003 | -0.357 | +0.086 | -15.9 | [-0.126, +0.311] | 0.08 | NO |
| 50% | const | +0.350 | -0.210 | -0.967 | -0.040 | -26.6 | [-0.490, +0.422] | 0.08 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 1,237,849, Sharpe 1.36, maxDD 161,014, worst wk -111,433; H1: net 92,462, Sharpe 0.68, maxDD 97,726, worst wk -97,726; H2: net -277,167, Sharpe -1.38, maxDD 277,167, worst wk -210,943; all: net 1,053,145, Sharpe 0.82, maxDD 302,348, worst wk -210,943
Correlation with pair (weekly): clean +0.21, H1 +0.10, H2 -0.13, all +0.13; worst-decile weeks (n=17) corr +0.27, sleeve mean in those weeks $1,510, positive share 0.12.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.63 | 3.34 | 5.91 | -78,727 | -77,975 | 267,009 | -81,874 | 41.0 |
| clean | add 30% | 1.69 | 3.62 | 6.53 | -78,727 | -77,975 | 260,459 | -81,874 | 41.9 |
| clean | const 20% | 1.66 | 3.48 | 6.22 | -62,981 | -62,380 | 210,987 | -65,499 | 41.9 |
| clean | const 30% | 1.75 | 3.97 | 7.38 | -55,109 | -54,583 | 176,426 | -57,312 | 42.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 2.85 | 6.25 | 4.29 | -77,610 | -66,030 | 142,669 | -78,287 | 39.3 |
| H1 | add 30% | 2.85 | 6.33 | 4.28 | -77,610 | -66,030 | 145,187 | -78,287 | 39.3 |
| H1 | const 20% | 2.85 | 6.29 | 4.29 | -62,088 | -52,824 | 115,142 | -62,630 | 39.3 |
| H1 | const 30% | 2.83 | 6.42 | 4.27 | -54,327 | -46,221 | 103,897 | -54,801 | 42.9 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.15 | 4.20 | 3.25 | -87,846 | -83,190 | 217,425 | -90,261 | 44.4 |
| H2 | add 30% | 2.06 | 3.97 | 3.12 | -91,851 | -85,193 | 217,425 | -94,130 | 44.4 |
| H2 | const 20% | 2.10 | 4.08 | 3.18 | -71,879 | -67,353 | 173,940 | -73,756 | 44.4 |
| H2 | const 30% | 1.94 | 3.67 | 2.95 | -67,900 | -61,437 | 152,198 | -69,372 | 44.4 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 1.93 | 3.92 | 10.84 | -80,970 | -79,159 | 267,009 | -90,261 | 41.7 |
| all | add 30% | 1.94 | 4.05 | 11.52 | -81,860 | -79,630 | 260,459 | -94,130 | 42.3 |
| all | const 20% | 1.94 | 3.99 | 11.18 | -65,132 | -63,516 | 210,987 | -73,756 | 42.3 |
| all | const 30% | 1.94 | 4.22 | 12.44 | -58,103 | -56,165 | 176,426 | -69,372 | 43.5 |

## Gate checklist (headline 20% additive)

- [FAIL] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.173 / +0.026 / -0.148
- [PASS] 3 worst week within share: all-in worst week +9.4% vs share 20%
- [FAIL] 4 own random-entry null p95 (standalone all-in): real 0.82 vs p95 0.85 (rank 0.94)
- [FAIL] 4 bootstrap 90% CI of all-in uplift >0: [-0.033, +0.184]
- [FAIL] 5 plateau >=75% of neighbours keep >=75% of uplift: 0% of 2
- [FAIL] 5 2x slippage uplift>=+0.10 each span: +0.169 / +0.022 / -0.151
- [PASS] 6 worst-decile corr <=+0.30: +0.27
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section I3); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: YES (50 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): negative pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 155 | -0.0057 | -0.08 |
| fixed | 155 | -0.0138 | -0.18 |
| scaled | 155 | -0.0088 | -0.12 |

Plateau neighbours (all-in 20% uplift; selected +0.071):
- {'kind': 'post', 'E': 'T+5', 'ev': 'FOMC', 'mode': 'follow', 'H': '45'}: -0.008 (trades 50)
- {'kind': 'post', 'E': 'T+5', 'ev': 'FOMC', 'mode': 'follow', 'H': '75'}: +0.042 (trades 50)

Own random-entry null: 500 draws, standalone all-in Sharpe median 0.02, p95 0.85, real 0.82. Standalone Sharpe at 2x slippage 0.80.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 14 | 2 | 1.75 |
| 2014 | 16 | -2 | -1.11 |
| 2015 | 16 | 0 | 0.03 |
| 2016 | 15 | -1 | -0.57 |
| 2017 | 16 | -0 | -0.59 |
| 2018 | 16 | 0 | 0.47 |
| 2019 | 16 | 1 | 1.15 |
| 2020 | 14 | -1 | -2.03 |
| 2021 | 16 | -0 | -0.02 |
| 2022 | 16 | -2 | -1.31 |
| 2023 | 16 | -1 | -0.42 |
| 2024 | 16 | 2 | 1.28 |
| 2025 | 16 | 2 | 1.52 |
| 2026 | 12 | -1 | -1.54 |


DONE I3