> **BASIS-VOID NOTICE (amendment FVG-REALIZABLE, 2026-10-17):** this report's sequencing is "independent replay of every limit order, then one position at a time applied in placement order" (code: ap_fvg_gccl_score.py TickData.trades, the `if filled[i] and pl[i]>=busy` loop; the same rule is in the RZ 1-minute engine `LimFam.run`). That is not an executable order-handling rule, so every verdict, uplift and replication result below is VOID until re-scored with an order-state machine (first-fill-wins OCO / one order at a time / newest replaces / stack-2). The tick-level fill, roll-rule and null machinery is reusable; the book selection is not. FOUND-PENDING-NT8-SPEC is withdrawn.

# REPORT FVG_GCCL - tick replay of the RZ GC tf15 and CL tf15 cells and the RZ9 basket (directive FVG-PAPER item 5)
**No purchase was made**: GC.FUT and CL.FUT trades 2023-02-01..2026-10-12 were already on disk (data/databento/{GC,CL}/trades/GLBX-20261013-*); SPEND.json unchanged ($6,938.18). Pre-registered as BLOCK 'FVG_GCCL' in PREREG_AUTOPILOT.md before the first run. Cells frozen from RZ1 (no re-selection). Replay code: code/census/night_ins/ap_fvg_gccl_replay.py (tick replay, 200+200 null batches, plateau neighbours) and ap_fvg_gccl_score.py (gates). Sections below are the full per-target reports.

## Summary (headline q50, latency 1 min, 1-tick-through target; additive 20% unless stated)
| target | uplift clean/H1/H2 | standalone all-in Sh | own null p95 | plateau | 2x slip uplift c/H1/H2 | worst-decile corr | replication passes | const 30% worst-week chg |
|---|---|---|---|---|---|---|---|---|
| GC | +0.57/+0.97/+0.31 | 3.01 | 0.45 | 83% | +0.38/+0.84/+0.23 | +0.28 | 2/4 | -9.1% |
| CL | +0.39/+0.51/+0.77 | 2.55 | 0.04 | 83% | +0.12/+0.20/+0.57 | -0.04 | 3/4 | -6.7% |
| RZ9 | +0.85/+0.80/+0.73 | 4.31 | -3.59 | 100% | +0.55/+0.49/+0.49 | -0.09 | 3/4 | -17.4% |

Reading:
- All seven measured gates pass on the tick replay for GC, CL and the RZ9 basket (GC and CL members tick-replayed; the other seven basket members have no trades data and stay on the 1-minute model). Replication (>=2 of live weeks, H0, ES/RTY cross, alternating months) is met through H0 + alternating months for all three (CL and RZ9 also live weeks); the ES/RTY cross fails for all three (ES and RTY cells uplift +0.15/+0.13 only, below 50% of the full uplift). Gate 7 (NT8 spec) is not written for these cells: status = FOUND-PENDING-NT8-SPEC, not FOUND.
- Tick replay did not weaken the 1-minute result: GC q50 uplift +0.54 vs 1-min +0.45; CL +0.49 vs +0.43. The conservative through-1-tick bound gives GC +0.49 / CL +0.34.
- Caveats that matter: (a) q0, q50 and q100 are identical because the price at the resting limit was rarely traded in the previous 15 minutes (trailing volume at price ~0), so the queue models collapse; true queue position is unobservable without depth data - treat the through-1-tick bound as the conservative case; (b) the entry-fraction null is NOT beaten (rank 0.73 GC, 0.68 CL): random entry fractions in 0.25-0.75 do about as well, so the edge comes from the FVG setup + 2R/stop structure, not from the 50% location; (c) pre-2023 (1-minute) is positive gross but thin net (GC fixed-cost weekly Sharpe 0.33; CL 1.04); (d) GC worst-decile corr +0.28 sits just under the +0.30 gate; GC live weeks are negative (-$120k at 100% pair-size over 4 weeks, one -$95k week), CL live weeks positive.
- Sized dollars and insurance metrics for each target are in the Sized dollars and insurance tables of the sections below (scaled so the sleeve's clean weekly sd equals the pair's).



---

# REPORT FVG_GC_tick
**Verdict: FOUND-PENDING-REPLICATION** (all measured gates pass; replication required). Selected cell setup=FVG, tf=15, thr=0.25; additive @20% clean/H1/H2 +0.57/+0.97/+0.31; standalone all-in weekly Sharpe 3.01 (2013-26 1.08, dev 2013-22 0.33); pair-window trades 3064. Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

FVG_GCCL (directive FVG-PAPER item 5), tick replay of FVG_GC_tick. DATA: GLBX.MDP3 trades 2023-02-01..2026-10-12 already on disk (no purchase). Fill model: limit at the 50% retrace price, q50 queue bound headline, latency 1 min, target on 1 tick through, stop-market at the first print at/through the stop, 4.36 USD RT; pre-2023 rows use the 1-minute RZ model (no tick data). Pre-registered in PREREG_AUTOPILOT.md BLOCK 'FVG_GCCL'.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 1. Top cells by clean weekly Sharpe:

| cell                       |    n |   sharpe |
|:---------------------------|-----:|---------:|
| setup=FVG, tf=15, thr=0.25 | 1882 |    3.210 |


## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.142e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.298 | +0.481 | +0.166 | +0.283 | +5.6 | [+0.196, +0.382] | 0.48 | NO |
| 20% | add | +0.570 | +0.968 | +0.310 | +0.540 | +12.2 | [+0.369, +0.739] | 0.48 | NO |
| 30% | add | +0.811 | +1.439 | +0.433 | +0.767 | +19.9 | [+0.518, +1.060] | 0.48 | NO |
| 50% | add | +1.197 | +2.222 | +0.616 | +1.125 | +35.3 | [+0.732, +1.589] | 0.48 | NO |
| 10% | const | +0.330 | +0.535 | +0.183 | +0.312 | -4.3 | [+0.217, +0.423] | 0.48 | NO |
| 20% | const | +0.694 | +1.207 | +0.374 | +0.657 | -7.2 | [+0.447, +0.905] | 0.48 | NO |
| 30% | const | +1.073 | +1.975 | +0.559 | +1.012 | -9.1 | [+0.669, +1.419] | 0.48 | INSURANCE |
| 50% | const | +1.716 | +2.792 | +0.801 | +1.560 | -12.0 | [+0.900, +2.328] | 0.48 | INSURANCE |

Standalone at 100% pair-equivalent risk ($): clean: net 2,924,582, Sharpe 3.21, maxDD 222,799, worst wk -116,719; H1: net 668,191, Sharpe 2.87, maxDD 163,598, worst wk -70,234; H2: net 647,719, Sharpe 2.41, maxDD 196,824, worst wk -95,330; all: net 4,240,492, Sharpe 3.01, maxDD 222,799, worst wk -116,719
Correlation with pair (weekly): clean +0.08, H1 -0.49, H2 +0.10, all +0.00; worst-decile weeks (n=17) corr +0.28, sleeve mean in those weeks $22,450, positive share 0.65.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 2.03 | 4.27 | 7.60 | -87,171 | -77,626 | 252,009 | -92,586 | 41.0 |
| clean | add 30% | 2.27 | 4.98 | 8.69 | -91,456 | -78,030 | 254,066 | -98,945 | 39.0 |
| clean | const 20% | 2.15 | 4.63 | 8.15 | -71,451 | -62,263 | 202,430 | -76,612 | 39.0 |
| clean | const 30% | 2.53 | 5.81 | 9.94 | -67,875 | -55,416 | 181,930 | -74,985 | 37.1 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.80 | 9.31 | 5.17 | -63,510 | -55,978 | 140,648 | -70,751 | 28.6 |
| H1 | add 30% | 4.27 | 11.10 | 5.85 | -56,460 | -51,119 | 135,819 | -67,660 | 25.0 |
| H1 | const 20% | 4.04 | 10.19 | 5.52 | -47,988 | -42,839 | 110,306 | -55,365 | 25.0 |
| H1 | const 30% | 4.80 | 13.59 | 6.15 | -36,227 | -31,410 | 100,160 | -44,581 | 25.0 |
| H2 | pair | 2.48 | 5.08 | 3.77 | -81,089 | -79,185 | 217,425 | -82,524 | 41.7 |
| H2 | add 20% | 2.79 | 6.02 | 4.51 | -75,491 | -73,164 | 210,704 | -77,798 | 36.1 |
| H2 | add 30% | 2.92 | 6.44 | 4.89 | -74,202 | -72,585 | 207,343 | -75,435 | 38.9 |
| H2 | const 20% | 2.86 | 6.23 | 4.70 | -59,524 | -58,299 | 167,219 | -61,293 | 38.9 |
| H2 | const 30% | 3.04 | 6.92 | 5.41 | -52,793 | -50,343 | 142,115 | -54,908 | 38.9 |
| all | pair | 1.90 | 3.71 | 9.79 | -79,220 | -78,243 | 280,110 | -82,524 | 42.3 |
| all | add 20% | 2.44 | 5.21 | 14.25 | -83,115 | -75,608 | 252,009 | -92,586 | 38.1 |
| all | add 30% | 2.66 | 5.92 | 15.81 | -85,510 | -75,790 | 254,066 | -98,945 | 36.9 |
| all | const 20% | 2.55 | 5.57 | 15.03 | -67,372 | -60,537 | 202,430 | -76,612 | 36.9 |
| all | const 30% | 2.91 | 6.73 | 17.55 | -62,460 | -53,506 | 181,930 | -74,985 | 35.7 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.570 / +0.968 / +0.310
- [PASS] 3 worst week within share: all-in worst week +12.2% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 3.01 vs p95 0.45 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.369, +0.739]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 83% of 6
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.375 / +0.835 / +0.234
- [PASS] 6 worst-decile corr <=+0.30: +0.28
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section FVG_GC_tick); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (3064 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 8288 | +0.0506 | 1.28 |
| fixed | 8288 | +0.0131 | 0.33 |
| scaled | 8288 | +0.0131 | 0.33 |

Plateau neighbours (all-in 20% uplift; selected +0.540):
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.188'}: +0.651 (trades 3443)
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '1.5'}: +0.516 (trades 3241)
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '15'}: +0.392 (trades 3050)
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.312'}: +0.487 (trades 2739)
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '2.5'}: +0.699 (trades 2930)
- {'sym': 'GC', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '25'}: +0.520 (trades 3049)

Own random-entry null: 200 draws, standalone all-in Sharpe median -0.42, p95 0.45, real 3.01. Standalone Sharpe at 2x slippage 2.16.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 887 | 6 | 0.16 |
| 2014 | 746 | -27 | -0.80 |
| 2015 | 771 | 53 | 2.03 |
| 2016 | 846 | 13 | 0.42 |
| 2017 | 706 | 23 | 1.00 |
| 2018 | 724 | -18 | -0.65 |
| 2019 | 771 | -1 | -0.03 |
| 2020 | 964 | 56 | 1.34 |
| 2021 | 920 | 6 | 0.14 |
| 2022 | 953 | -1 | -0.03 |
| 2023 | 861 | 88 | 2.84 |
| 2024 | 961 | 114 | 2.69 |
| 2025 | 1012 | 144 | 3.45 |
| 2026 | 752 | 65 | 2.33 |


## Tick-replay specifics (FVG_GCCL)

Setups placed 2023-02..2026-10-12: 8,792; dropped by roll rule 368; valid 8,560; filled (q50, before one-position rule) 6,084 (fill rate 71.1%); trades after one-position rule 3,505; exit mix target/stop/time = 993/1772/740.

### Fill-model and variant table (additive 20% uplift, same cell)

| variant                           |   trades_pairwin |   netR_per_trade |   sa_clean |   up20_clean |   up20_H1 |   up20_H2 |   up20_all |
|:----------------------------------|-----------------:|-----------------:|-----------:|-------------:|----------:|----------:|-----------:|
| through1                          |             3044 |            0.110 |      2.819 |        0.504 |     0.893 |     0.324 |      0.493 |
| q0                                |             3064 |            0.121 |      3.211 |        0.570 |     0.968 |     0.310 |      0.540 |
| q50 (headline)                    |             3064 |            0.121 |      3.210 |        0.570 |     0.968 |     0.310 |      0.540 |
| q100                              |             3064 |            0.121 |      3.210 |        0.570 |     0.968 |     0.310 |      0.540 |
| latency 0 min                     |             3082 |            0.129 |      3.457 |        0.622 |     1.027 |     0.370 |      0.594 |
| latency 2 min                     |             3061 |            0.118 |      3.081 |        0.545 |     0.946 |     0.292 |      0.517 |
| target on touch (0 ticks through) |             3065 |            0.122 |      3.237 |        0.580 |     0.966 |     0.309 |      0.547 |
| 1 tick adverse entry              |             3064 |            0.101 |      2.627 |        0.457 |     0.892 |     0.266 |      0.446 |
| 1-minute RZ model (reference)     |             3240 |            0.102 |      2.591 |        0.458 |     0.755 |     0.355 |      0.453 |

Entry-fraction null (200 replicates, fraction uniform 0.25-0.75, same signals, q50 tick replay): standalone all-in Sharpe real 3.01 vs median 2.89, p95 3.24, rank 0.73.

### Replication battery (Gate Amendment 2)

- alternating months: odd +0.425, even +0.590 vs full +0.540 -> PASS
- H0 2023-02..07: weekly Sharpe 2.44 on 441 trades -> PASS
- cross-instrument uplift (all-in, 20%): {"ES": 0.152, "RTY": 0.129, "CL": 0.494} (rule uses ES and RTY, 1-min model) -> FAIL
- live weeks 2026-09-21..10-16 (tick data to 10-12), weekly USD at 100% pair-equivalent size: [-15593, -95330, -31343, 21829] -> FAIL
- replication passes 2 of 4 candidates (need 2): **REPLICATED**

### Sized dollars (sleeve scaled so its clean weekly sd equals the pair; pair-window all-in span)

| share   |   usd_per_1R |   worst_trade_usd |   worst_day |   worst_week |   pair_worst_week |
|:--------|-------------:|------------------:|------------:|-------------:|------------------:|
| 10%     |        1,142 |           -12,383 |     -12,383 |      -11,672 |           -82,524 |
| 20%     |        2,285 |           -24,766 |     -24,766 |      -23,344 |           -82,524 |
| 30%     |        3,427 |           -37,149 |     -37,149 |      -35,016 |           -82,524 |
| 50%     |        5,711 |           -61,915 |     -61,915 |      -58,359 |           -82,524 |

Contracts per trade = share x USD-per-R / (stop distance x point value): {"0.1": {"median": 2.07, "p90": 3.81, "max": 3.81, "pv": 100.0, "med_stop_pts": 5.51, "med_stop_usd_per_contract": 551.06}, "0.2": {"median": 4.15, "p90": 7.62, "max": 7.62, "pv": 100.0, "med_stop_pts": 5.51, "med_stop_usd_per_contract": 551.06}, "0.3": {"median": 6.22, "p90": 11.42, "max": 11.42, "pv": 100.0, "med_stop_pts": 5.51, "med_stop_usd_per_contract": 551.06}, "0.5": {"median": 10.36, "p90": 19.04, "max": 19.04, "pv": 100.0, "med_stop_pts": 5.51, "med_stop_usd_per_contract": 551.06}}

DONE FVG_GC_tick

---

# REPORT FVG_CL_tick
**Verdict: FOUND-PENDING-REPLICATION** (all measured gates pass; replication required). Selected cell setup=FVG, tf=15, thr=0.25; additive @20% clean/H1/H2 +0.39/+0.51/+0.77; standalone all-in weekly Sharpe 2.55 (2013-26 1.45, dev 2013-22 1.04); pair-window trades 2780. Runtime 0.0 min (+selection 0.0 min). 7-worker pool.

FVG_GCCL (directive FVG-PAPER item 5), tick replay of FVG_CL_tick. DATA: GLBX.MDP3 trades 2023-02-01..2026-10-12 already on disk (no purchase). Fill model: limit at the 50% retrace price, q50 queue bound headline, latency 1 min, target on 1 tick through, stop-market at the first print at/through the stop, 4.36 USD RT; pre-2023 rows use the 1-minute RZ model (no tick data). Pre-registered in PREREG_AUTOPILOT.md BLOCK 'FVG_GCCL'.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 8 cells, eligible (>= 40 clean trades): 1. Top cells by clean weekly Sharpe:

| cell                       |    n |   sharpe |
|:---------------------------|-----:|---------:|
| setup=FVG, tf=15, thr=0.25 | 1708 |    2.207 |


## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=1.412e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.207 | +0.291 | +0.408 | +0.263 | +4.4 | [+0.162, +0.374] | 0.39 | NO |
| 20% | add | +0.393 | +0.507 | +0.773 | +0.494 | +12.0 | [+0.296, +0.717] | 0.39 | NO |
| 30% | add | +0.555 | +0.648 | +1.087 | +0.688 | +21.3 | [+0.403, +1.011] | 0.39 | NO |
| 50% | add | +0.804 | +0.746 | +1.553 | +0.970 | +39.9 | [+0.520, +1.462] | 0.39 | NO |
| 10% | const | +0.229 | +0.319 | +0.451 | +0.290 | -5.5 | [+0.179, +0.414] | 0.39 | NO |
| 20% | const | +0.477 | +0.587 | +0.937 | +0.596 | -6.7 | [+0.352, +0.870] | 0.39 | NO |
| 30% | const | +0.726 | +0.733 | +1.410 | +0.885 | -6.7 | [+0.491, +1.321] | 0.39 | NO |
| 50% | const | +1.092 | +0.539 | +2.029 | +1.234 | +0.0 | [+0.519, +1.989] | 0.39 | NO |

Standalone at 100% pair-equivalent risk ($): clean: net 2,010,738, Sharpe 2.21, maxDD 336,029, worst wk -139,264; H1: net 651,586, Sharpe 2.09, maxDD 264,089, worst wk -102,952; H2: net 1,391,781, Sharpe 3.80, maxDD 196,431, worst wk -90,083; all: net 4,054,105, Sharpe 2.55, maxDD 336,029, worst wk -139,264
Correlation with pair (weekly): clean +0.03, H1 -0.03, H2 -0.01, all +0.02; worst-decile weeks (n=17) corr -0.04, sleeve mean in those weeks $9,943, positive share 0.47.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 1.85 | 3.67 | 6.93 | -86,789 | -81,193 | 249,856 | -92,417 | 41.9 |
| clean | add 30% | 2.01 | 4.06 | 7.26 | -90,990 | -83,032 | 266,276 | -100,096 | 41.9 |
| clean | const 20% | 1.94 | 3.87 | 7.31 | -71,111 | -65,596 | 200,698 | -77,005 | 41.9 |
| clean | const 30% | 2.19 | 4.47 | 7.17 | -67,782 | -61,036 | 214,118 | -76,979 | 41.9 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.34 | 8.00 | 4.15 | -70,334 | -62,358 | 174,523 | -89,485 | 35.7 |
| H1 | add 30% | 3.48 | 8.20 | 4.25 | -75,892 | -69,208 | 185,928 | -95,084 | 32.1 |
| H1 | const 20% | 3.41 | 8.16 | 4.20 | -58,318 | -52,626 | 144,180 | -73,827 | 35.7 |
| H1 | const 30% | 3.56 | 8.10 | 4.35 | -60,277 | -54,611 | 140,414 | -71,597 | 32.1 |
| H2 | pair | 2.48 | 5.08 | 3.77 | -81,089 | -79,185 | 217,425 | -82,524 | 41.7 |
| H2 | add 20% | 3.26 | 7.77 | 5.61 | -80,509 | -71,605 | 195,802 | -86,696 | 33.3 |
| H2 | add 30% | 3.57 | 9.13 | 6.58 | -86,773 | -71,093 | 187,975 | -90,217 | 33.3 |
| H2 | const 20% | 3.42 | 8.46 | 6.13 | -66,913 | -57,079 | 152,475 | -70,765 | 30.6 |
| H2 | const 30% | 3.89 | 10.71 | 7.57 | -66,379 | -49,304 | 130,984 | -66,438 | 30.6 |
| all | pair | 1.90 | 3.71 | 9.79 | -79,220 | -78,243 | 280,110 | -82,524 | 42.3 |
| all | add 20% | 2.39 | 5.03 | 14.23 | -86,152 | -78,846 | 249,856 | -92,417 | 39.3 |
| all | add 30% | 2.59 | 5.57 | 14.87 | -90,508 | -80,680 | 266,276 | -100,096 | 38.7 |
| all | const 20% | 2.49 | 5.32 | 14.98 | -70,480 | -63,629 | 200,698 | -77,005 | 38.7 |
| all | const 30% | 2.78 | 6.12 | 14.65 | -67,894 | -59,464 | 214,118 | -76,979 | 38.1 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.393 / +0.507 / +0.773
- [PASS] 3 worst week within share: all-in worst week +12.0% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 2.55 vs p95 0.04 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.296, +0.717]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 83% of 6
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.116 / +0.203 / +0.570
- [PASS] 6 worst-decile corr <=+0.30: -0.04
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section FVG_CL_tick); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (2780 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 7894 | +0.0823 | 1.87 |
| fixed | 7894 | +0.0460 | 1.04 |
| scaled | 7894 | +0.0460 | 1.04 |

Plateau neighbours (all-in 20% uplift; selected +0.494):
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.188'}: +0.602 (trades 3001)
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '1.5'}: +0.480 (trades 2969)
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '15'}: +0.422 (trades 2803)
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.312'}: +0.352 (trades 2538)
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'R': '2.5'}: +0.441 (trades 2652)
- {'sym': 'CL', 'setup': 'FVG', 'tf': '15', 'thr': '0.25', 'L': '25'}: +0.561 (trades 2767)

Own random-entry null: 200 draws, standalone all-in Sharpe median -0.73, p95 0.04, real 2.55. Standalone Sharpe at 2x slippage 1.31.

## Long history of the selected cell (unit-risk sleeve, weekly Sharpe by year)

| year | trades | net (units $) | weekly Sharpe |
|---|---|---|---|
| 2013 | 731 | 113 | 3.24 |
| 2014 | 698 | 84 | 2.61 |
| 2015 | 768 | 90 | 2.91 |
| 2016 | 806 | -8 | -0.31 |
| 2017 | 547 | -24 | -1.00 |
| 2018 | 760 | -0 | -0.01 |
| 2019 | 738 | -16 | -0.59 |
| 2020 | 839 | 33 | 0.78 |
| 2021 | 908 | 37 | 1.01 |
| 2022 | 1099 | 56 | 1.11 |
| 2023 | 868 | 104 | 2.94 |
| 2024 | 844 | 87 | 2.69 |
| 2025 | 802 | 22 | 0.70 |
| 2026 | 760 | 128 | 3.98 |


## Tick-replay specifics (FVG_GCCL)

Setups placed 2023-02..2026-10-12: 9,319; dropped by roll rule 383; valid 8,888; filled (q50, before one-position rule) 6,445 (fill rate 72.5%); trades after one-position rule 3,197; exit mix target/stop/time = 791/1505/901.

### Fill-model and variant table (additive 20% uplift, same cell)

| variant                           |   trades_pairwin |   netR_per_trade |   sa_clean |   up20_clean |   up20_H1 |   up20_H2 |   up20_all |
|:----------------------------------|-----------------:|-----------------:|-----------:|-------------:|----------:|----------:|-----------:|
| through1                          |             2741 |            0.076 |      1.692 |        0.294 |     0.368 |     0.467 |      0.343 |
| q0                                |             2780 |            0.104 |      2.235 |        0.399 |     0.509 |     0.777 |      0.499 |
| q50 (headline)                    |             2780 |            0.103 |      2.207 |        0.393 |     0.507 |     0.773 |      0.494 |
| q100                              |             2780 |            0.103 |      2.207 |        0.393 |     0.507 |     0.773 |      0.494 |
| latency 0 min                     |             2785 |            0.107 |      2.341 |        0.423 |     0.515 |     0.754 |      0.512 |
| latency 2 min                     |             2775 |            0.100 |      2.182 |        0.389 |     0.506 |     0.696 |      0.475 |
| target on touch (0 ticks through) |             2786 |            0.115 |      2.524 |        0.462 |     0.537 |     0.778 |      0.544 |
| 1 tick adverse entry              |             2780 |            0.075 |      1.403 |        0.236 |     0.339 |     0.652 |      0.343 |
| 1-minute RZ model (reference)     |             3004 |            0.094 |      2.272 |        0.407 |     0.363 |     0.521 |      0.432 |

Entry-fraction null (200 replicates, fraction uniform 0.25-0.75, same signals, q50 tick replay): standalone all-in Sharpe real 2.55 vs median 2.46, p95 2.78, rank 0.68.

### Replication battery (Gate Amendment 2)

- alternating months: odd +0.594, even +0.354 vs full +0.494 -> PASS
- H0 2023-02..07: weekly Sharpe 2.48 on 417 trades -> PASS
- cross-instrument uplift (all-in, 20%): {"ES": 0.152, "RTY": 0.129, "GC": 0.54} (rule uses ES and RTY, 1-min model) -> FAIL
- live weeks 2026-09-21..10-16 (tick data to 10-12), weekly USD at 100% pair-equivalent size: [149943, 78104, 88065, 44108] -> PASS
- replication passes 3 of 4 candidates (need 2): **REPLICATED**

### Sized dollars (sleeve scaled so its clean weekly sd equals the pair; pair-window all-in span)

| share   |   usd_per_1R |   worst_trade_usd |   worst_day |   worst_week |   pair_worst_week |
|:--------|-------------:|------------------:|------------:|-------------:|------------------:|
| 10%     |        1,412 |            -5,855 |      -7,506 |      -13,926 |           -82,524 |
| 20%     |        2,823 |           -11,710 |     -15,012 |      -27,853 |           -82,524 |
| 30%     |        4,235 |           -17,565 |     -22,518 |      -41,779 |           -82,524 |
| 50%     |        7,058 |           -29,276 |     -37,530 |      -69,632 |           -82,524 |

Contracts per trade = share x USD-per-R / (stop distance x point value): {"0.1": {"median": 4.71, "p90": 4.71, "max": 4.71, "pv": 1000.0, "med_stop_pts": 0.3, "med_stop_usd_per_contract": 300.0}, "0.2": {"median": 9.41, "p90": 9.41, "max": 9.41, "pv": 1000.0, "med_stop_pts": 0.3, "med_stop_usd_per_contract": 300.0}, "0.3": {"median": 14.12, "p90": 14.12, "max": 14.12, "pv": 1000.0, "med_stop_pts": 0.3, "med_stop_usd_per_contract": 300.0}, "0.5": {"median": 23.53, "p90": 23.53, "max": 23.53, "pv": 1000.0, "med_stop_pts": 0.3, "med_stop_usd_per_contract": 300.0}}

DONE FVG_CL_tick

---

# REPORT FVG_RZ9_tick
**Verdict: FOUND-PENDING-REPLICATION** (all measured gates pass; replication required). Selected cell basket ES:FVG/tf15/0.25+RTY:FVG/tf15/0.5+YM:FVG/tf30/0.25+GC:FVG/tf15/0.25+CL:FVG/tf15/0.25+ZN:FVG/tf15/0.25+6E:FVG/tf15/0.25+BTC:FVG/tf15/0.25+ETH:FVG/tf15/0.25, R=2.0, L=20, thr x1.0; additive @20% clean/H1/H2 +0.85/+0.80/+0.73; standalone all-in weekly Sharpe 4.31 (2013-26 2.16, dev 2013-22 1.42); pair-window trades 22676. Runtime 0.1 min (+selection 0.0 min). 7-worker pool.

FVG_GCCL (directive FVG-PAPER item 5), tick replay of FVG_RZ9_tick. DATA: GLBX.MDP3 trades 2023-02-01..2026-10-12 already on disk (no purchase). Fill model: limit at the 50% retrace price, q50 queue bound headline, latency 1 min, target on 1 tick through, stop-market at the first print at/through the stop, 4.36 USD RT; pre-2023 rows use the 1-minute RZ model (no tick data). Pre-registered in PREREG_AUTOPILOT.md BLOCK 'FVG_GCCL'.

## Selection (clean span 2023-08..2025-07 only; H1/H2 read once for the carried cell; Gate Amendment 2)
Grid 1 cells, eligible (>= 40 clean trades): 1. Top cells by clean weekly Sharpe:

| cell       |     n |   sharpe |
|:-----------|------:|---------:|
| RZ9 basket | 13996 |    4.949 |


## Pair-window results of the selected cell (sleeve scaled to the pair clean weekly sd, f=3.729e+04)

| share | framing | clean dSh | H1 dSh | H2 dSh | all dSh | worst wk chg % | boot 90% CI | shift-null rank | verdict |
|---|---|---|---|---|---|---|---|---|---|
| 10% | add | +0.444 | +0.416 | +0.393 | +0.421 | +1.1 | [+0.320, +0.530] | 0.08 | NO |
| 20% | add | +0.847 | +0.803 | +0.730 | +0.799 | +5.4 | [+0.604, +1.013] | 0.08 | NO |
| 30% | add | +1.205 | +1.145 | +1.007 | +1.129 | +10.7 | [+0.851, +1.445] | 0.08 | NO |
| 50% | add | +1.786 | +1.659 | +1.389 | +1.646 | +22.0 | [+1.213, +2.129] | 0.08 | NO |
| 10% | const | +0.491 | +0.461 | +0.433 | +0.465 | -8.6 | [+0.354, +0.586] | 0.08 | NO |
| 20% | const | +1.032 | +0.980 | +0.876 | +0.970 | -13.8 | [+0.733, +1.236] | 0.08 | NO |
| 30% | const | +1.598 | +1.503 | +1.277 | +1.483 | -17.4 | [+1.098, +1.913] | 0.08 | INSURANCE |
| 50% | const | +2.645 | +2.071 | +1.713 | +2.315 | -24.8 | [+1.627, +3.102] | 0.08 | INSURANCE |

Standalone at 100% pair-equivalent risk ($): clean: net 4,508,789, Sharpe 4.95, maxDD 182,667, worst wk -74,035; H1: net 751,558, Sharpe 3.29, maxDD 170,978, worst wk -86,647; H2: net 1,420,570, Sharpe 3.51, maxDD 180,758, worst wk -93,604; all: net 6,680,917, Sharpe 4.31, maxDD 182,667, worst wk -93,604
Correlation with pair (weekly): clean +0.22, H1 -0.22, H2 +0.05, all +0.11; worst-decile weeks (n=17) corr -0.09, sleeve mean in those weeks $49,607, positive share 0.71.

## Insurance metric set (pair, 20%/30% additive and constant-risk), per span

| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst wk | % neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | add 20% | 2.31 | 5.15 | 10.13 | -82,535 | -76,117 | 220,302 | -86,952 | 40.0 |
| clean | add 30% | 2.66 | 6.42 | 14.09 | -84,995 | -75,182 | 190,424 | -91,313 | 39.0 |
| clean | const 20% | 2.49 | 5.78 | 11.97 | -67,012 | -60,520 | 164,280 | -71,177 | 40.0 |
| clean | const 30% | 3.06 | 8.03 | 16.12 | -61,710 | -51,847 | 141,631 | -68,136 | 39.0 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | add 20% | 3.63 | 9.50 | 4.82 | -56,445 | -52,125 | 154,490 | -59,090 | 35.7 |
| H1 | add 30% | 3.97 | 10.93 | 5.26 | -54,966 | -51,179 | 155,878 | -59,763 | 32.1 |
| H1 | const 20% | 3.81 | 10.28 | 5.04 | -44,564 | -40,182 | 124,147 | -45,425 | 35.7 |
| H1 | const 30% | 4.33 | 11.87 | 5.78 | -42,762 | -37,983 | 110,984 | -47,202 | 28.6 |
| H2 | pair | 2.48 | 5.08 | 3.77 | -81,089 | -79,185 | 217,425 | -82,524 | 41.7 |
| H2 | add 20% | 3.21 | 7.87 | 5.57 | -70,556 | -66,758 | 198,058 | -76,204 | 36.1 |
| H2 | add 30% | 3.49 | 9.41 | 6.59 | -65,388 | -60,619 | 189,188 | -74,479 | 36.1 |
| H2 | const 20% | 3.36 | 8.63 | 6.08 | -54,339 | -50,921 | 154,572 | -60,273 | 36.1 |
| H2 | const 30% | 3.76 | 11.40 | 7.92 | -44,646 | -39,888 | 126,331 | -50,583 | 33.3 |
| all | pair | 1.90 | 3.71 | 9.79 | -79,220 | -78,243 | 280,110 | -82,524 | 42.3 |
| all | add 20% | 2.70 | 6.23 | 18.52 | -79,486 | -71,783 | 220,302 | -86,952 | 38.7 |
| all | add 30% | 3.03 | 7.55 | 24.93 | -80,326 | -69,717 | 190,424 | -91,313 | 37.5 |
| all | const 20% | 2.87 | 6.89 | 21.49 | -63,925 | -56,452 | 164,280 | -71,177 | 38.7 |
| all | const 30% | 3.38 | 9.18 | 27.71 | -57,451 | -47,983 | 141,631 | -68,136 | 36.3 |

## Gate checklist (headline 20% additive)

- [PASS] 3 uplift>=+0.10 clean/H1/H2 @20%: +0.847 / +0.803 / +0.730
- [PASS] 3 worst week within share: all-in worst week +5.4% vs share 20%
- [PASS] 4 own random-entry null p95 (standalone all-in): real 4.31 vs p95 -3.59 (rank 1.00)
- [PASS] 4 bootstrap 90% CI of all-in uplift >0: [+0.604, +1.013]
- [PASS] 5 plateau >=75% of neighbours keep >=75% of uplift: 100% of 6
- [PASS] 5 2x slippage uplift>=+0.10 each span: +0.545 / +0.487 / +0.488
- [PASS] 6 worst-decile corr <=+0.30: -0.09
- [PASS] 1 pre-registered before first run (PREREG_AUTOPILOT.md section FVG_RZ9_tick); 2 selection on clean only, H1/H2 read once for one cell
- [INFO] 7 executability: see below; small-sample flag: no (22676 trades in pair window)

## ERA FLAG (Gate Amendment 2; not gating): positive pre-2023

2013-2022 run of the same cell (unit = 1 ADR-dollar of risk per trade): gross = zero cost; fixed = 1 tick/side + $4.36; scaled = fixed cost x ADR_t / median clean ADR.

| cost | trades | mean per trade (ADR units) | weekly Sharpe |
|---|---|---|---|
| gross | 40739 | +0.0075 | 3.28 |
| fixed | 40739 | +0.0032 | 1.42 |
| scaled | 40739 | +0.0032 | 1.42 |

Plateau neighbours (all-in 20% uplift; selected +0.799):
- {'n': '9', 'R': '2.0', 'L': '20', 'tm': '0.75'}: +0.953 (trades 25068)
- {'n': '9', 'R': '1.5', 'L': '20', 'tm': '1.0'}: +0.641 (trades 24116)
- {'n': '9', 'R': '2.0', 'L': '15', 'tm': '1.0'}: +0.637 (trades 22857)
- {'n': '9', 'R': '2.0', 'L': '20', 'tm': '1.25'}: +0.610 (trades 20480)
- {'n': '9', 'R': '2.5', 'L': '20', 'tm': '1.0'}: +0.942 (trades 21720)
- {'n': '9', 'R': '2.0', 'L': '25', 'tm': '1.0'}: +0.846 (trades 22453)

Own random-entry null: 200 draws, standalone all-in Sharpe median -4.53, p95 -3.59, real 4.31. Standalone Sharpe at 2x slippage 2.88.

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
| 2023 | 6514 | 30 | 2.18 |
| 2024 | 6986 | 57 | 4.94 |
| 2025 | 7188 | 55 | 4.50 |
| 2026 | 5743 | 43 | 3.65 |


## Tick-replay specifics (FVG_GCCL)



### Fill-model and variant table (additive 20% uplift, same cell)

| variant              |   trades_pairwin |   netR_per_trade |   sa_clean |   up20_clean |   up20_H1 |   up20_H2 |   up20_all |
|:---------------------|-----------------:|-----------------:|-----------:|-------------:|----------:|----------:|-----------:|
| through1             |            22617 |            0.007 |      4.625 |        0.791 |     0.736 |     0.645 |      0.735 |
| q0                   |            22676 |            0.008 |      4.956 |        0.849 |     0.803 |     0.731 |      0.800 |
| q50 (headline)       |            22676 |            0.008 |      4.949 |        0.847 |     0.803 |     0.730 |      0.799 |
| q100                 |            22676 |            0.008 |      4.949 |        0.847 |     0.803 |     0.730 |      0.799 |
| 1 tick adverse entry |            22676 |            0.007 |      4.506 |        0.763 |     0.725 |     0.680 |      0.723 |

### Replication battery (Gate Amendment 2)

- alternating months: odd +0.879, even +0.647 vs full +0.799 -> PASS
- H0 2023-02..07: weekly Sharpe 1.30 on 3232 trades -> PASS
- cross-instrument uplift (all-in, 20%): {"ES": 0.152, "RTY": 0.129} (rule uses ES and RTY, 1-min model) -> FAIL
- live weeks 2026-09-21..10-16 (tick data to 10-12), weekly USD at 100% pair-equivalent size: [-76002, -59426, 45232, 96024] -> PASS
- replication passes 3 of 4 candidates (need 2): **REPLICATED**

### Sized dollars (sleeve scaled so its clean weekly sd equals the pair; pair-window all-in span)

| share   |   usd_per_1R |   worst_trade_usd |   worst_day |   worst_week |   pair_worst_week |
|:--------|-------------:|------------------:|------------:|-------------:|------------------:|
| 10%     |        3,729 |            -4,492 |      -7,567 |       -9,360 |           -82,524 |
| 20%     |        7,459 |            -8,984 |     -15,133 |      -18,721 |           -82,524 |
| 30%     |       11,188 |           -13,477 |     -22,700 |      -28,081 |           -82,524 |
| 50%     |       18,647 |           -22,461 |     -37,833 |      -46,802 |           -82,524 |

DONE FVG_RZ9_tick