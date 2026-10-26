# REPORT BK4 - TOP-10 CONCENTRATION / DISPERSION REGIME TILT (BACKLOG2 #60 and E6; D04 x M4/M8, H5)
**Verdict: NO. FOUND 0. Selected DISP_HIGH_DOWN (clean-only among 6 eligible of 6 cells): weekly Sharpe uplift +0.05 clean / -0.13 H1 / -0.79 H2 (needed +0.10 each); all-in -0.16; bootstrap 90% CI of all-in uplift [-0.47, +0.17]; own null (200 replicates) p95 clean -0.02 / all-in -0.18 (real rank clean 0.97, all-in 0.95); plateau 0.00 of 4.** Pre-registered in PREREG_AUTOPILOT.md / PREREG_BK.md 'BATCH BK' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: When the index is carried by a few names (high top-10 variance share relative to QQQ, high cross-sectional dispersion) the NQ minute path is single-name flow, and the pair's trend edge differs from broad-index days.
- Definition: S10 = ln(Var 1-min EQ10 / Var 1-min QQQ, trailing 20 sessions); DISP = mean of the cross-sectional sd of the ten names' daily returns over 20 sessions (split days dropped); state of the previous session; terciles frozen on clean; HIGH_DOWN/HIGH_UP/TWO_V.
- Data: XNAS.ITCH 2022-01..2026-10-13 (2013-2021 daily top-10 history is NOT on disk, so the E6 long-history question is not testable).
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (4433 touched pair rows); flagged share per cell (clean rows): S10_HIGH_DOWN 33.3%, S10_HIGH_UP 33.3%, S10_TWO_V 66.5%, DISP_HIGH_DOWN 33.2%, DISP_HIGH_UP 33.2%, DISP_TWO_V 66.3%; eligibility (declared): none (regime partition)

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| S10_HIGH_DOWN | +0.013 | +0.000 | +0.000 | +0.032 |
| S10_HIGH_UP | -0.209 | +0.000 | +0.000 | -0.170 |
| S10_TWO_V | -0.532 | -0.638 | -1.185 | -0.677 |
| DISP_HIGH_DOWN **(selected)** | +0.046 | -0.132 | -0.793 | -0.160 |
| DISP_HIGH_UP | -0.052 | -0.350 | -0.553 | -0.218 |
| DISP_TWO_V | -0.187 | -0.782 | -0.404 | -0.316 |

## Result for the carried cell: DISP_HIGH_DOWN
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.51 | +0.046 | +0.109 |
| H1 | 2.83 | 2.70 | -0.132 | -0.142 |
| H2 | 2.48 | 1.69 | -0.793 | -0.975 |
| all | 1.90 | 1.74 | -0.160 | -0.167 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): PASS
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean +0.046 vs -0.025 / 0.97; H1 -0.132 vs +0.225 / 0.59; H2 -0.793 vs -0.257 / 0.56; all -0.160 vs -0.180 / 0.95
- bootstrap 90% CI of all-in uplift: [-0.467, +0.169]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: Wd15 -0.200; Wd25 -0.276; share25 -0.178; share42 -0.409; definitions {'Wd15': "('DISP', 15, 'HIGH_DOWN')", 'Wd25': "('DISP', 25, 'HIGH_DOWN')", 'share25': "('DISP', 20, 'HIGH_DOWN', 0.25)", 'share42': "('DISP', 20, 'HIGH_DOWN', 0.42)"}
- worst week (candidate vs pair): clean -81.9k vs -81.9k; H1 -78.3k vs -78.3k; H2 -79.7k vs -82.5k; all -81.9k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.926); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks -0.64; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift -0.037 -> does not hold.
- Alternating months (select odd/read even, then reverse): select DISP_HIGH_UP (+0.321) reads -0.406; select S10_HIGH_DOWN (+0.024) reads +0.030 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +0 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 0 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.51 | 2.71 | 5.43 | -78.7k | -78.0k | 234k | -81.9k | 41.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.70 | 5.80 | 4.11 | -77.6k | -66.0k | 138k | -78.3k | 39.3 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 1.69 | 3.33 | 2.15 | -78.7k | -78.0k | 268k | -79.7k | 47.2 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.74 | 3.26 | 9.01 | -78.7k | -77.9k | 268k | -81.9k | 42.9 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-18,595 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $9,600.
- Worst day: $-58,519 (pair $-59,109); worst week all-in: $-81,874 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: daily state from ten equity series + QQQ computed after each close; multiplier at the next session.
Library: outputs/library/BK4_DISP_HIGH_DOWN.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift +0.05 is the in-sample maximum of 6 eligible cells; out of sample it reads -0.13 on H1 and -0.79 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.97 (p95 -0.02) and the all-in uplift at 0.95 (p95 -0.18). Gates failed: uplift>=0.10 clean/H1/H2, bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bk4/.

DONE BK4
