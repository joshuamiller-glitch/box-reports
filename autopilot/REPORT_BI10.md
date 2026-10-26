# REPORT BI10 - TIME-SINCE-LAST-FLIP TILT OF THE PAIR (BI10; D00 x M4/M7, H2-H3)
**Verdict: NO. FOUND 0. Selected g2_TWO_V (clean-only among 9 eligible of 9 cells): weekly Sharpe uplift +0.01 clean / -0.55 H1 / +0.23 H2 (needed +0.10 each); all-in -0.00; bootstrap 90% CI of all-in uplift [-0.49, +0.50]; own null (200 replicates) p95 clean +0.23 / all-in +0.11 (real rank clean 0.68, all-in 0.86); plateau 0.00 of 2.** Pre-registered in PREREG_AUTOPILOT.md / IDEAS_BI.md 'BATCH BI' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: A flip arriving soon after another pair entry (same book, either book or opposite direction) marks a whipsaw/cluster regime in which trend entries have lower expectancy (order-flow clustering).
- Definition: g1 = -ln(minutes since the previous entry of the same book), g2 = same for either book, g3 = same for the opposite direction; high g = short gap; terciles frozen on clean; schemes HIGH_DOWN (short-gap tercile x0.5), HIGH_UP (x1.5), TWO_V.
- Data: pair rows only.
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (8381 touched pair rows); flagged share per cell (clean rows): g1_HIGH_DOWN 33.0%, g1_HIGH_UP 33.0%, g1_TWO_V 66.3%, g2_HIGH_DOWN 32.2%, g2_HIGH_UP 32.2%, g2_TWO_V 65.5%, g3_HIGH_DOWN 33.3%, g3_HIGH_UP 33.3%, g3_TWO_V 66.6%; eligibility (declared): none (regime partition)

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| g1_HIGH_DOWN | -0.115 | +0.611 | -1.291 | -0.271 |
| g1_HIGH_UP | -0.752 | +0.525 | -0.171 | -0.398 |
| g1_TWO_V | -0.151 | -0.797 | +0.268 | -0.134 |
| g2_HIGH_DOWN | -0.335 | +0.041 | -1.208 | -0.484 |
| g2_HIGH_UP | -0.503 | -0.420 | -1.867 | -0.828 |
| g2_TWO_V **(selected)** | +0.009 | -0.549 | +0.231 | -0.001 |
| g3_HIGH_DOWN | -0.057 | -0.485 | -0.599 | -0.226 |
| g3_HIGH_UP | -0.231 | +0.039 | -0.285 | -0.184 |
| g3_TWO_V | -0.023 | -0.231 | -0.117 | -0.056 |

## Result for the carried cell: g2_TWO_V
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.47 | +0.009 | +0.369 |
| H1 | 2.83 | 2.28 | -0.549 | -0.591 |
| H2 | 2.48 | 2.71 | +0.231 | -0.047 |
| all | 1.90 | 1.90 | -0.001 | +0.152 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): FAIL
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean +0.009 vs +0.233 / 0.68; H1 -0.549 vs +0.744 / 0.27; H2 +0.231 vs +0.308 / 0.93; all -0.001 vs +0.107 / 0.86
- bootstrap 90% CI of all-in uplift: [-0.486, +0.499]
- plateau: 0.00 of 2 neighbours keep >= 75% of the all-in uplift; neighbours: share25 +0.214; share42 -0.031; definitions {'share25': "('g2', 'TWO_V', 0.25)", 'share42': "('g2', 'TWO_V', 0.42)"}
- worst week (candidate vs pair): clean -84.5k vs -81.9k; H1 -79.0k vs -78.3k; H2 -80.5k vs -82.5k; all -84.5k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.876); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks +0.02; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift +0.444 -> HOLDS.
- Alternating months (select odd/read even, then reverse): select g2_HIGH_UP (+0.328) reads -1.274; select g2_HIGH_DOWN (-0.033) reads -0.617 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +51,120 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 1 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.47 | 2.61 | 5.09 | -80.7k | -79.4k | 263k | -84.5k | 41.0 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.28 | 4.69 | 2.87 | -79.0k | -78.8k | 204k | -79.0k | 35.7 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 2.71 | 6.04 | 4.58 | -79.5k | -76.4k | 203k | -80.5k | 33.3 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.90 | 3.61 | 10.85 | -80.3k | -79.2k | 263k | -84.5k | 38.7 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-23,244 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $12,000.
- Worst day: $-65,655 (pair $-59,109); worst week all-in: $-84,514 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: the strategy keeps timestamps of its own last entries; quantity multiplier by gap tercile edges frozen from the clean span.
Library: outputs/library/BI10_g2_TWO_V.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift +0.01 is the in-sample maximum of 9 eligible cells; out of sample it reads -0.55 on H1 and +0.23 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.68 (p95 +0.23) and the all-in uplift at 0.86 (p95 +0.11). Gates failed: uplift>=0.10 clean/H1/H2, worst week not worse (all-in), own null all-in > p95 (and clean), bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bi_ov_run.py, ap_bk_rep.py; outputs/autopilot/bk/bi10/.

DONE BI10
