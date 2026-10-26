# REPORT PA7 - EARLY ADVERSE-EXCURSION EXIT AT 2-5 MINUTES (D00 x M5, H1), live pair
**Verdict: NO. Selected (20, 5): weekly Sharpe uplift +0.13 clean / -0.06 H1 / -0.65 H2 (needed +0.10 each); all-in -0.03; bootstrap CI [-0.58, +0.54]; plateau 0.00 of 4; null all-in rank 0.90. Pool of 5, 6 cells, runtime <1 min**

## Set-up and fill model
- Rows: 13,089 live pair rows (ROWS_corrected_engine.parquet, 2023-02-10..2026-10-13) replayed from the fill on 1-second bars (ap_g11_c_core, as K14/K17) with the 60/60 bracket until the trigger bar, exit at that 1-min bar close; rows closed externally (kind 1) exit at the trigger close; untouched rows/later signals keep live P&L; modified rows re-run through the live account B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (baseline 1.46/2.83/2.30). Fill 1 tick/side + $34.88 per 8 lots; 2x slippage SLIP_PT 1.0. Triggers use data through the trigger bar only.
- Rule: At the close of 1-min bar f with entry+1 <= f <= entry+M exit at that close if the trade is >= X points under water (close-based, so the fill can be worse than X). Grid 6: X {10,20,30} points x M {3,5} minutes.
- Null: the same number of rows as fired in the selected cell chosen at random, exited at a random bar entry+1..entry+M at that bar's close, 100 draws, linear delta-P&L on the baseline account.
- Selection clean only (max clean uplift of 6 cells); H1/H2 read once for the carried cell (grid table prints all spans for transparency). Fired rows per cell: (10, 3) 3709; (10, 5) 4656; (20, 3) 1595; (20, 5) 2295; (30, 3) 693; (30, 5) 1128.
- Disclosure: pre-registered in PREREG_AUTOPILOT.md (block PA4/PA5/PA6/PA7) before the first run; no earlier H1/H2 look at this observable. Pair-change framing only (exit rule, no separate book; additive/constant-risk n/a). ES/RTY cross-check not run (NQ gates fail). Pair rows start 2023-02: ERA flag n/a; pre-2023 not testable.

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| (10, 3) | -0.201 | -0.169 | -0.654 | -0.245 |
| (10, 5) | -0.252 | -0.680 | -1.070 | -0.468 |
| (20, 3) | +0.125 | -0.323 | -0.960 | -0.154 |
| (20, 5) **(selected)** | +0.133 | -0.059 | -0.655 | -0.034 |
| (30, 3) | -0.030 | -0.335 | -0.302 | -0.121 |
| (30, 5) | -0.063 | -0.044 | -0.350 | -0.111 |

## Result for the carried cell: (20, 5)
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.59 | +0.133 | +0.342 |
| H1 | 2.83 | 2.77 | -0.059 | -0.106 |
| H2 | 2.30 | 1.64 | -0.655 | -0.986 |
| all | 1.86 | 1.82 | -0.034 | +0.007 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean +0.133 vs +0.067 / 0.98; H1 -0.059 vs +0.760 / 0.59; H2 -0.655 vs +0.587 / 0.09; all -0.034 vs -0.016 / 0.90
- bootstrap 90% CI of all-in uplift: [-0.579, +0.538]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: X x0.75 -0.260; X x1.25 -0.063; M x0.75 -0.009; M x1.25 -0.105
- alternating-month split (pre-registered): select (30, 3) (+0.206) reads -0.233 on the other half; select (20, 5) (+0.393) reads -0.133 on the other half
- H0 (2023-02-10..07-31) uplift: -0.106; replications counted (alt-month, H0): 0 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -79.9k vs -81.9k; H1 -77.8k vs -78.3k; H2 -79.4k vs -82.5k; all -79.9k vs -82.5k; weekly corr with pair 0.823 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.59 | 3.06 | 5.99 | -78.3k | -77.9k | 243k | -79.9k | 41.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.77 | 5.97 | 4.74 | -77.7k | -77.6k | 154k | -77.8k | 32.1 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 1.64 | 3.02 | 2.03 | -79.2k | -78.4k | 251k | -79.4k | 36.1 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 1.82 | 3.52 | 10.76 | -78.5k | -78.0k | 251k | -79.9k | 39.3 |

## Reading
Cutting trades on a fast adverse move in the first 3-5 minutes costs two fills on a loss that the 60/60 bracket often recovers: the pair's entries have the ordinary run-and-return behaviour of a breakout system, so early adverse excursion does not separate eventual losers. Carried cell (20, 5): clean +0.13, H1 -0.06, H2 -0.65; the 10 and 30 points cells are negative on clean. A small clean gain at 20 points reverses on H1/H2 (the common failure).

## Executability / era / replication
NT8: monitor open position price in the first M bars after entry (OnBarUpdate/OnMarketData), exit by market order. Executable. Margin unchanged. Era: pair rows start 2023-02, ERA flag n/a. Replication: alt-month and H0 as listed in the checklist; newest live weeks and ES/RTY not run. Fill model: market exit at the trigger bar close, 1 tick/side + commission; executable at NinjaTrader Brokerage via Rithmic. Files: code/census/night_ins/ap_pa1_exit.py, ap_pa1_exit_rep.py; outputs/autopilot/pa7/ (pa7_all.pkl, pa7_summary.json), log pa7.log.

DONE PA7
