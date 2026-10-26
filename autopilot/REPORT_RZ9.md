# REPORT RZ9
**Verdict: FOUND-PENDING-REPLICATION** (all measured gates pass; replication required). Selected cell basket ES:FVG/tf15/0.25+RTY:FVG/tf15/0.5+YM:FVG/tf30/0.25+GC:FVG/tf15/0.25+CL:FVG/tf15/0.25+ZN:FVG/tf15/0.25+6E:FVG/tf15/0.25+BTC:FVG/tf15/0.25+ETH:FVG/tf15/0.25, R=2.0, L=20, thr x1.0; additive @20% clean/H1/H2 +0.84/+0.72/+0.69; standalone all-in weekly Sharpe 4.21 (2013-26 2.08, dev 2013-22 1.42); pair-window trades 23007. Runtime 1.1 min (+selection 0.2 min). 10-worker pool.

RZ9: equal-risk basket of the RZ1/RZ2 structural-level limit-order retrace sleeves whose selected cell has clean weekly Sharpe >= 0.5. Pre-registered in PREREG_AUTOPILOT.md BATCH RZ.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 1 cells, eligible (>= 40 clean trades): 1. Top cells by clean weekly Sharpe:

|     n |     R |   L |    tm |   sharpe |     net |   ypos | eligible   |
|------:|------:|----:|------:|---------:|--------:|-------:|:-----------|
| 14217 | 2.000 |  20 | 1.000 |    4.893 | 118.582 |      3 | True       |

Selection-aware null (report only, 20 random-entry replicates of the whole grid selection): real selected clean Sharpe 4.89; replicate best-eligible median -5.09, p95 -4.39; real beats 100% of replicates.

## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.759e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.440 | +0.375 | +0.372 | +0.409 | +1.4 | [+0.311, +0.517] | 0.05 | NO |
| 20% | add | +0.839 | +0.717 | +0.693 | +0.776 | +6.2 | [+0.586, +0.989] | 0.05 | NO |
| 30% | add | +1.193 | +1.012 | +0.958 | +1.096 | +12.5 | [+0.821, +1.412] | 0.05 | NO |
| 50% | add | +1.769 | +1.436 | +1.331 | +1.598 | +25.0 | [+1.161, +2.088] | 0.05 | NO |
| 10% | const | +0.486 | +0.415 | +0.411 | +0.452 | -8.3 | [+0.344, +0.572] | 0.05 | NO |
| 20% | const | +1.021 | +0.871 | +0.833 | +0.942 | -12.5 | [+0.709, +1.207] | 0.05 | NO |
| 30% | const | +1.582 | +1.311 | +1.220 | +1.439 | -15.6 | [+1.053, +1.870] | 0.05 | INSURANCE |
| 50% | const | +2.617 | +1.712 | +1.678 | +2.248 | -21.8 | [+1.554, +3.041] | 0.05 | INSURANCE |

Standalone at 100% pair-equivalent risk ($): clean: net 4,457,304, Sharpe 4.89, maxDD 211,333, worst wk -82,420; H1: net 687,825, Sharpe 2.96, maxDD 176,902, worst wk -96,071; H2: net 1,377,848, Sharpe 3.45, maxDD 181,025, worst wk -94,426; all: net 6,522,976, Sharpe 4.21, maxDD 211,333, worst wk -96,071
Correlation with pair (weekly): clean +0.21, H1 -0.19, H2 +0.07, all +0.12; worst-decile weeks (n=17) corr -0.07, sleeve mean in those weeks $49,756, positive share 0.76.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 2.30 | 5.11 | 10.59 | -82,304 | -75,905 | 209,854 | -87,628 | 38.1 |
| clean | add 30% | 2.65 | 6.35 | 14.10 | -84,648 | -74,865 | 189,098 | -92,812 | 38.1 |
| clean | const 20% | 2.48 | 5.73 | 12.71 | -66,781 | -60,308 | 153,832 | -72,176 | 38.1 |
| clean | const 30% | 3.04 | 7.92 | 16.17 | -61,364 | -51,690 | 140,305 | -69,635 | 37.1 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.55 | 9.19 | 4.53 | -57,117 | -52,765 | 161,421 | -58,809 | 35.7 |
| H1 | add 30% | 3.84 | 10.37 | 4.81 | -55,975 | -52,795 | 166,275 | -62,203 | 32.1 |
| H1 | const 20% | 3.70 | 9.85 | 4.67 | -45,237 | -41,259 | 131,078 | -47,052 | 32.1 |
| H1 | const 30% | 4.14 | 11.03 | 5.15 | -45,396 | -39,729 | 120,761 | -49,642 | 28.6 |
| H2 | pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| H2 | add 20% | 2.99 | 7.25 | 5.19 | -71,793 | -67,307 | 199,819 | -76,324 | 36.1 |
| H2 | add 30% | 3.25 | 8.63 | 6.11 | -67,146 | -62,651 | 192,152 | -74,659 | 38.9 |
| H2 | const 20% | 3.13 | 7.93 | 5.66 | -55,576 | -51,760 | 156,334 | -60,393 | 38.9 |
| H2 | const 30% | 3.51 | 10.36 | 7.32 | -45,546 | -41,529 | 129,294 | -50,763 | 36.1 |
| all | pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| all | add 20% | 2.63 | 6.04 | 19.01 | -79,390 | -71,859 | 209,854 | -87,628 | 37.5 |
| all | add 30% | 2.95 | 7.30 | 24.16 | -80,184 | -70,208 | 192,152 | -92,812 | 37.5 |
| all | const 20% | 2.80 | 6.67 | 22.08 | -63,830 | -56,655 | 156,334 | -72,176 | 37.5 |
| all | const 30% | 3.29 | 8.82 | 27.34 | -57,802 | -48,684 | 140,305 | -69,635 | 35.7 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.839 / +0.717 / +0.693
- [PASS] 3 worst week within share: all-in worst week +6.2% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 4.21 vs p95 -4.05 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.586, +0.989]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 83% of 6
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.616 / +0.477 / +0.503
- [PASS] 6 worst-decile corr <=+0.30: -0.07
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section RZ9); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (23007 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 40739 | +0.0075 | 3.28 |
| fixed | 40739 | +0.0032 | 1.42 |
| scaled | 40739 | +0.0032 | 1.42 |

Plateau neighbours (all-in 20% uplift; selected +0.776):
- {'n': '9', 'R': '2.0', 'L': '20', 'tm': '0.75'}: +0.940 (trades 25414)
- {'n': '9', 'R': '1.5', 'L': '20', 'tm': '1.0'}: +0.590 (trades 24478)
- {'n': '9', 'R': '2.0', 'L': '15', 'tm': '1.0'}: +0.604 (trades 23170)
- {'n': '9', 'R': '2.0', 'L': '20', 'tm': '1.25'}: +0.567 (trades 20788)
- {'n': '9', 'R': '2.5', 'L': '20', 'tm': '1.0'}: +0.922 (trades 22036)
- {'n': '9', 'R': '2.0', 'L': '25', 'tm': '1.0'}: +0.812 (trades 22766)

Own random-entry null: 300 draws, standalone all-in Sharpe median -5.04, p95 -4.05, real 4.21. Standalone Sharpe at 2x slippage 3.13.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 3059 | 7 | 1.05 |
| 2014 | 2830 | -3 | -0.45 |
| 2015 | 3407 | 25 | 3.82 |
| 2016 | 3481 | 4 | 0.64 |
| 2017 | 2962 | -15 | -2.02 |
| 2018 | 4232 | 18 | 1.80 |
| 2019 | 3790 | -2 | -0.23 |
| 2020 | 4818 | 30 | 2.47 |
| 2021 | 4610 | 23 | 2.29 |
| 2022 | 7550 | 44 | 3.42 |
| 2023 | 6636 | 23 | 1.61 |
| 2024 | 7090 | 54 | 4.86 |
| 2025 | 7311 | 55 | 4.44 |
| 2026 | 5811 | 42 | 3.59 |


## Members and single-instrument comparison

| instrument | clean weekly Sharpe (own R series) | in basket | additive 20% clean/H1/H2 (single report) | single verdict |
|---|---|---|---|---|
| ES | 0.93 | yes | +0.11/-0.14/+0.46 | NO |
| RTY | 1.71 | yes | +0.26/+0.05/-0.16 | NO |
| YM | 1.19 | yes | +0.19/-0.31/+0.81 | NO |
| GC | 2.59 | yes | +0.46/+0.75/+0.36 | FOUND-PENDING-REPLICATION |
| CL | 2.27 | yes | +0.41/+0.36/+0.52 | FOUND-PENDING-REPLICATION |
| ZN | 0.73 | yes | +0.07/+0.00/+0.04 | NO |
| 6E | 0.77 | yes | +0.12/-0.15/+0.07 | NO |
| BTC | 2.24 | yes | +0.37/+0.30/+0.08 | LEAD |
| ETH | 2.04 | yes | +0.36/+0.45/+0.07 | NO |

Best single instrument by clean additive uplift: GC (+0.46). Disclosure: the member list and each member's cell were chosen on clean data in RZ1/RZ2 (selection is not re-nulled here beyond the sleeve null on the fixed basket).

DONE RZ9