# REPORT BQ1 - CROSS-SECTIONAL DISPERSION / AVERAGE CORRELATION ACROSS 14 OUTRIGHTS: PAIR TILT (BATCH 5)
**Verdict: NO. FOUND 0. Selected DISP_HIGH_UP (clean-only among 6 eligible of 6 cells): weekly Sharpe uplift +0.05 clean / +0.19 H1 / -1.35 H2 (needed +0.10 each); all-in -0.25; bootstrap 90% CI of all-in uplift [-0.76, +0.26]; own null (200 replicates) p95 clean +0.08 / all-in -0.23 (real rank clean 0.92, all-in 0.94); plateau 0.00 of 4.** Pre-registered in PREREG_AUTOPILOT.md ('BATCH 5, Part 2') before the first scored run; harness ap_bq_run.py (copy of ap_bk_run.py with the BQ1/BQ2 branches), cross-instrument harness ap_bq_xi.py not run because the pair verdict is NO.

## Mechanism (one sentence) and set-up
- Mechanism: When the 14 liquid outrights move independently (high dispersion, low correlation) NQ is driven by its own flow and the trend books face idiosyncratic trends; when they co-move the index is a macro beta and the book edge differs.
- Definition: A = 5-day mean of the cross-sectional SD of ADR20-scaled daily changes across ES RTY YM GC CL ZN ZB 6E 6J HG SI NG HO RB; B = 20-day average pairwise correlation of the same scaled changes; value known after the previous label day closes (strictly earlier than the entry ET date); tercile tails with edges frozen on clean rows; HIGH_DOWN / HIGH_UP / TWO_V multipliers.
- Data: 1-minute bars 2013-2026 of 14 outrights (data/autopilot/ohlcv1m).
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (4831 touched pair rows); flagged share per cell (clean rows): DISP_HIGH_DOWN 33.3%, DISP_HIGH_UP 33.3%, DISP_TWO_V 66.3%, CORR_HIGH_DOWN 33.3%, CORR_HIGH_UP 33.3%, CORR_TWO_V 66.3%; eligibility (declared): none (regime partition)

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| DISP_HIGH_DOWN | +0.000 | +1.120 | -1.440 | -0.227 |
| DISP_HIGH_UP **(selected)** | +0.053 | +0.187 | -1.352 | -0.250 |
| DISP_TWO_V | -0.269 | -0.290 | -1.198 | -0.477 |
| CORR_HIGH_DOWN | -0.427 | +0.089 | +0.721 | -0.088 |
| CORR_HIGH_UP | +0.011 | -0.192 | +0.105 | -0.013 |
| CORR_TWO_V | +0.008 | -0.670 | -0.206 | -0.122 |

## Result for the carried cell: DISP_HIGH_UP
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.51 | +0.053 | -0.002 |
| H1 | 2.83 | 3.01 | +0.187 | +0.411 |
| H2 | 2.48 | 1.13 | -1.352 | -1.393 |
| all | 1.90 | 1.65 | -0.250 | -0.275 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): FAIL
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean +0.053 vs +0.083 / 0.92; H1 +0.187 vs +0.547 / 0.84; H2 -1.352 vs -0.629 / 0.66; all -0.250 vs -0.230 / 0.94
- bootstrap 90% CI of all-in uplift: [-0.761, +0.261]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: L x0.75 -0.262; L x1.25 +0.001; share25 +0.066; share42 -0.205; definitions {'L x0.75': "('DISP', 'HIGH_UP', 4)", 'L x1.25': "('DISP', 'HIGH_UP', 6)", 'share25': "('DISP', 'HIGH_UP', 5, 0.25)", 'share42': "('DISP', 'HIGH_UP', 5, 0.42)"}
- worst week (candidate vs pair): clean -80.1k vs -81.9k; H1 -83.4k vs -78.3k; H2 -81.2k vs -82.5k; all -83.4k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.862); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks -0.24; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift +0.229 -> HOLDS.
- Alternating months (select odd/read even, then reverse): select DISP_HIGH_UP (+0.147) reads +0.009; select CORR_HIGH_UP (+0.209) reads -0.179 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +0 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 1 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.51 | 2.89 | 4.11 | -78.5k | -78.0k | 352k | -80.1k | 41.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 3.01 | 6.35 | 3.73 | -81.2k | -68.3k | 174k | -83.4k | 32.1 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 1.13 | 1.96 | 1.59 | -80.4k | -80.0k | 243k | -81.2k | 52.8 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.65 | 3.09 | 7.04 | -79.9k | -78.9k | 352k | -83.4k | 42.9 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-26,752 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $14,400.
- Worst day: $-87,434 (pair $-59,109); worst week all-in: $-83,436 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: a daily file of the feature (computed outside NT8) read by DualStrat for the size multiplier; no intraday dependency.
Library: outputs/library/BQ1_DISP_HIGH_UP.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift +0.05 is the in-sample maximum of 6 eligible cells; out of sample it reads +0.19 on H1 and -1.35 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.92 (p95 +0.08) and the all-in uplift at 0.94 (p95 -0.23). Gates failed: uplift>=0.10 clean/H1/H2, worst week not worse (all-in), own null all-in > p95 (and clean), bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bq1/.

DONE BQ1
