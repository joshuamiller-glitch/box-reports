# REPORT BQ2 - NQ REALISED SKEW / KURTOSIS OF THE PREVIOUS 5 SESSIONS: PAIR TILT (BATCH 5)
**Verdict: NO. FOUND 0. Selected SKEW_HIGH_UP (clean-only among 6 eligible of 6 cells): weekly Sharpe uplift +0.12 clean / -1.01 H1 / -0.63 H2 (needed +0.10 each); all-in -0.21; bootstrap 90% CI of all-in uplift [-0.69, +0.26]; own null (200 replicates) p95 clean +0.30 / all-in +0.08 (real rank clean 0.83, all-in 0.67); plateau 0.00 of 4.** Pre-registered in PREREG_AUTOPILOT.md ('BATCH 5, Part 2') before the first scored run; harness ap_bq_run.py (copy of ap_bk_run.py with the BQ1/BQ2 branches), cross-instrument harness ap_bq_xi.py not run because the pair verdict is NO.

## Mechanism (one sentence) and set-up
- Mechanism: A skewed or fat-tailed recent return distribution marks jump-driven (gap/shock) markets in which a fixed 60-point bracket is hit by jumps rather than by drift, which changes the trend books edge.
- Definition: pooled 5-session skew (SKEW) or excess kurtosis (KURT) of NQ 1-minute log returns (|r|<1%, same ET date), known before the entry ET date; tercile tails, edges frozen on clean rows; HIGH_DOWN / HIGH_UP / TWO_V.
- Data: NQ 1-minute bars (pair series).
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (5007 touched pair rows); flagged share per cell (clean rows): SKEW_HIGH_DOWN 33.3%, SKEW_HIGH_UP 33.3%, SKEW_TWO_V 66.5%, KURT_HIGH_DOWN 33.3%, KURT_HIGH_UP 33.3%, KURT_TWO_V 66.5%; eligibility (declared): none (regime partition)

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| SKEW_HIGH_DOWN | +0.077 | +0.100 | +0.229 | +0.122 |
| SKEW_HIGH_UP **(selected)** | +0.123 | -1.015 | -0.631 | -0.209 |
| SKEW_TWO_V | -0.407 | +0.628 | +0.199 | -0.112 |
| KURT_HIGH_DOWN | -0.374 | -0.194 | -0.264 | -0.309 |
| KURT_HIGH_UP | -0.394 | -0.566 | -0.592 | -0.480 |
| KURT_TWO_V | -0.597 | +0.414 | -0.858 | -0.523 |

## Result for the carried cell: SKEW_HIGH_UP
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.58 | +0.123 | +0.276 |
| H1 | 2.83 | 1.81 | -1.015 | -0.916 |
| H2 | 2.48 | 1.85 | -0.631 | -0.705 |
| all | 1.90 | 1.69 | -0.209 | -0.118 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean +0.123 vs +0.300 / 0.83; H1 -1.015 vs +0.742 / 0.04; H2 -0.631 vs +0.051 / 0.70; all -0.209 vs +0.077 / 0.67
- bootstrap 90% CI of all-in uplift: [-0.689, +0.255]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: L x0.75 -0.211; L x1.25 -0.235; share25 -0.202; share42 -0.318; definitions {'L x0.75': "('SKEW', 'HIGH_UP', 4)", 'L x1.25': "('SKEW', 'HIGH_UP', 6)", 'share25': "('SKEW', 'HIGH_UP', 5, 0.25)", 'share42': "('SKEW', 'HIGH_UP', 5, 0.42)"}
- worst week (candidate vs pair): clean -81.9k vs -81.9k; H1 -79.5k vs -78.3k; H2 -80.7k vs -82.5k; all -81.9k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.872); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks -0.28; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift +0.361 -> HOLDS.
- Alternating months (select odd/read even, then reverse): select SKEW_HIGH_DOWN (+0.160) reads -0.154; select SKEW_HIGH_UP (+0.778) reads -0.536 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair -14,687 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 1 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.58 | 3.08 | 4.79 | -78.6k | -78.1k | 321k | -81.9k | 43.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 1.81 | 3.30 | 2.00 | -79.2k | -78.7k | 211k | -79.5k | 46.4 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 1.85 | 3.60 | 2.93 | -80.2k | -79.4k | 217k | -80.7k | 44.4 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.69 | 3.23 | 8.09 | -79.4k | -78.5k | 321k | -81.9k | 44.6 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-27,052 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $14,400.
- Worst day: $-87,434 (pair $-59,109); worst week all-in: $-81,874 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: daily feature file from the minute database; size multiplier only.
Library: outputs/library/BQ2_SKEW_HIGH_UP.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift +0.12 is the in-sample maximum of 6 eligible cells; out of sample it reads -1.01 on H1 and -0.63 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.83 (p95 +0.30) and the all-in uplift at 0.67 (p95 +0.08). Gates failed: uplift>=0.10 clean/H1/H2, own null all-in > p95 (and clean), bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bq2/.

DONE BQ2
