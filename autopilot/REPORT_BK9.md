# REPORT BK9 - 0DTE PUT/CALL PREMIUM IMBALANCE ALIGNMENT TILT (BACKLOG2 #50; D03 x M4/M8, H2-H3)
**Verdict: NO. FOUND 0. Selected L30_TWO (clean-only among 6 eligible of 6 cells): weekly Sharpe uplift +0.04 clean / +0.11 H1 / -0.32 H2 (needed +0.10 each); all-in -0.02; bootstrap 90% CI of all-in uplift [-0.20, +0.19]; own null (200 replicates) p95 clean +0.15 / all-in +0.15 (real rank clean 0.77, all-in 0.43); plateau 0.00 of 4.** Pre-registered in PREREG_AUTOPILOT.md / PREREG_BK.md 'BATCH BK' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: When 0DTE put premium traded dominates call premium over the last 30-60 min the index is being hedged/sold; trend entries aligned with the call-heavy or put-heavy side carry different follow-through.
- Definition: PCI_L = (sum put premium - sum call premium)/(sum both) over the last L minutes of NDXP 0DTE records before the entry; F = side x (-PCI); RTH entries 10:00-15:59; terciles frozen on clean; COUNTER_DOWN / ALIGN_UP / TWO; L {30,60}.
- Data: OPRA NDXP trades per-minute reductions 2022-2026.
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (3662 touched pair rows); flagged share per cell (clean rows): L30_COUNTER_DOWN 14.9%, L30_ALIGN_UP 14.9%, L30_TWO 29.8%, L60_COUNTER_DOWN 14.9%, L60_ALIGN_UP 14.9%, L60_TWO 29.7%; eligibility (declared): none (regime partition)

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| L30_COUNTER_DOWN | +0.026 | +0.089 | -0.451 | -0.061 |
| L30_ALIGN_UP | -0.448 | -0.023 | -0.125 | -0.325 |
| L30_TWO **(selected)** | +0.042 | +0.113 | -0.317 | -0.018 |
| L60_COUNTER_DOWN | -0.279 | -0.090 | -0.351 | -0.258 |
| L60_ALIGN_UP | -0.158 | -0.156 | +0.025 | -0.130 |
| L60_TWO | -0.259 | -0.001 | -0.084 | -0.183 |

## Result for the carried cell: L30_TWO
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.50 | +0.042 | +0.013 |
| H1 | 2.83 | 2.94 | +0.113 | +0.059 |
| H2 | 2.48 | 2.17 | -0.317 | -0.312 |
| all | 1.90 | 1.88 | -0.018 | -0.048 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean +0.042 vs +0.148 / 0.77; H1 +0.113 vs +0.668 / 0.24; H2 -0.317 vs +0.224 / 0.00; all -0.018 vs +0.148 / 0.43
- bootstrap 90% CI of all-in uplift: [-0.197, +0.188]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: L x0.75 -0.207; L x1.25 -0.233; share25 -0.165; share42 -0.037; definitions {'L x0.75': "(22, 'TWO')", 'L x1.25': "(38, 'TWO')", 'share25': "(30, 'TWO', 0.25)", 'share42': "(30, 'TWO', 0.42)"}
- worst week (candidate vs pair): clean -81.9k vs -81.9k; H1 -79.4k vs -78.3k; H2 -82.5k vs -82.5k; all -82.5k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.980); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks +0.17; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift -0.068 -> does not hold.
- Alternating months (select odd/read even, then reverse): select L30_COUNTER_DOWN (+0.182) reads -0.174; select L30_TWO (-0.013) reads +0.045 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +57 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 0 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.50 | 2.86 | 4.88 | -78.4k | -77.9k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.94 | 6.79 | 4.41 | -78.4k | -62.7k | 147k | -79.4k | 39.3 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 2.17 | 4.24 | 3.03 | -81.1k | -79.6k | 242k | -82.5k | 41.7 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.88 | 3.67 | 9.81 | -79.3k | -78.4k | 280k | -82.5k | 42.3 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-22,244 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $12,000.
- Worst day: $-59,299 (pair $-59,109); worst week all-in: $-82,467 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: needs a real-time OPRA NDXP trade feed with premium (NOT available via Rithmic); external bridge required.
Library: outputs/library/BK9_L30_TWO.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift +0.04 is the in-sample maximum of 6 eligible cells; out of sample it reads +0.11 on H1 and -0.32 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.77 (p95 +0.15) and the all-in uplift at 0.43 (p95 +0.15). Gates failed: uplift>=0.10 clean/H1/H2, own null all-in > p95 (and clean), bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bk9/.

DONE BK9
