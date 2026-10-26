# REPORT J6b
**Verdict: NO** (1/6 measured gates pass). Selected cell h30k1_m0.5: weekly Sharpe uplift clean/H1/H2/all-in -0.24 / -0.07 / +0.04 / -0.14 (needed +0.10 on each of clean, H1, H2). Family: :00/:30 neighbourhood entry avoidance on the pair (M7, H1-H2).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via d3_common in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill model 1 tick/side + $34.88 per 8-lot round trip (2x = 2 ticks/side for the slippage test), ET clock, 1-min harness for locks.
- Rule: Entry within k minutes (before or after) of :00/:30 (or :00 only) gets mm in {0,0.5}; 6 cells; reduce-only. Applied through B.Cfg.sizefn.
- Null: 100 permutations of the per-trade multiplier vector across trades. Bootstrap 3000 weekly draws.
- Selection on clean only (max clean uplift over 6 cells); H1/H2 read once for the carried cell. Cells (clean uplift): h30k1_m0.0 -0.34; h30k1_m0.5 -0.24; h30k3_m0.0 -1.26; h30k3_m0.5 -0.53; h00k3_m0.0 -0.62; h00k3_m0.5 -0.54.

## Result (weekly Sharpe)
| span | pair | candidate | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.22 | -0.24 | +0.09 | -0.09 |
| H1 | 2.83 | 2.75 | -0.07 | +0.62 | +0.02 |
| H2 | 2.30 | 2.34 | +0.04 | +0.09 | -0.16 |
| all-in | 1.86 | 1.71 | -0.14 | +0.18 | -0.08 |

Whole-lot rounding (round(8m)/8) uplift: -0.24 / -0.07 / +0.04 (all-in -0.14).

## Gate checklist
- 3. uplift >= +0.10 on clean, H1, H2: FAIL. -0.24 / -0.07 / +0.04
- 3b. worst week not worse (per span): PASS. -81.9k vs -81.9k / -78.1k vs -78.3k / -78.9k vs -82.5k
- 4a. own null p95 (all-in uplift; rank): FAIL. real -0.14 vs p95 +0.13 (rank 0.47); clean -0.24 vs +0.08 (rank 0.29)
- 4b. bootstrap 90% CI all-in > 0: FAIL. [-0.44, +0.14]; clean [-0.61, +0.08]
- 5a. plateau >= 75% of neighbours keep >= 75% of uplift: FAIL. 0 of 4; mm x0.75 -0.20, k x0.75 -0.14, mm x1.25 -0.39, k x1.25 -0.14
- 5b. 2x slippage uplift >= +0.10 each span: FAIL. -0.09 / +0.02 / -0.16
- 6. worst-decile corr (overlay; weekly corr with the pair): PASS. n/a for an overlay (weekly corr 0.95); no hedge claim
- 7. NT8 spec: yes. see Executability
- R. replication H0 2023-02..07 (uplift): PASS. +0.04 (pair H0 Sharpe 0.67, 26 weeks)
- R. alternating split (carried cell odd/even; months; protocol): FAIL. carried cell uplift odd -0.19 / even -0.09; select-odd h30k1_m0.5 -0.19 -> even -0.09; select-even h30k3_m0.5 +0.18 -> odd -0.36
- 1/2. Pre-registered in PREREG_AUTOPILOT.md before the first run; clean-only selection, H1/H2 read once: PASS (process).

## Insurance metrics (weekly; $)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81,089 | -79,185 | 217,425 | -82,524 | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79,220 | -78,243 | 280,110 | -82,524 | 42.9 |
| clean cand | 1.22 | 2.19 | 3.06 | -78,725 | -78,071 | 366,983 | -81,874 | 42.9 |
| H1 cand | 2.75 | 6.32 | 3.99 | -77,818 | -65,432 | 153,531 | -78,111 | 39.3 |
| H2 cand | 2.34 | 4.89 | 4.36 | -78,304 | -76,549 | 183,154 | -78,933 | 41.7 |
| all cand | 1.71 | 3.27 | 6.90 | -78,563 | -77,953 | 366,983 | -81,874 | 42.3 |

INSURANCE flags (rep_common/ins_metrics, per span: flag, cost %, CVaR5 impr, worst-week impr, maxDD impr): clean: [False, -15.655487412421332, 0.013987757156300743, 0.0, -31.014013935108533]; H1: [False, 3.1057863772534833, -0.2681100560340576, 0.22583466858507292, -1.19826535218151]; H2: [False, 4.980453314949591, 3.434351605939917, 4.351484553431862, 15.762362131947167]; all: [False, -5.655676825345496, 0.8299327849369199, 0.7883236586282869, -31.014013935108533]

## Replication and era
- H0 window (2023-02-10..07-31, pair only; the pair rows start 2023-02): uplift +0.04.
- Alternating split (2023-08..2026-10 weeks by month parity): protocol result in checklist. ES/RTY replication: not available (pair engine is NQ-only).
- ERA FLAG: n/a pre-2023 (the pair has no history before 2023-02; this overlay cannot be scaled back). Mechanism depends on the current clock-structure of NQ flow; no pre-2023 evidence.

## Executability
NT8: entry-time minute test in the strategy; 0 = skip entry, 0.5x = 4 lots. NinjaTrader Brokerage via Rithmic, NQ; no data beyond the strategy's own clock. Not recommended unless FOUND.

Cells closed: see GAPMAP_UPDATES.md (J6 worker).

DONE J6b