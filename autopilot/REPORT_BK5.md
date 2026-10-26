# REPORT BK5 - BREADTH-THRUST DAY LONGER TARGETS (BACKLOG2 #61; D04 x M4/M8, H4)
**Verdict: NO. FOUND 0. Selected thr8_t1.25 (clean-only among 8 eligible of 8 cells): weekly Sharpe uplift -0.06 clean / +0.02 H1 / -0.09 H2 (needed +0.10 each); all-in -0.06; bootstrap 90% CI of all-in uplift [-0.22, +0.07]; own null (200 replicates) p95 clean +0.05 / all-in +0.04 (real rank clean 0.70, all-in 0.69); plateau 0.00 of 4.** Pre-registered in PREREG_AUTOPILOT.md / PREREG_BK.md 'BATCH BK' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: When >= 8 (9) of the ten names are up (down) versus the prior close at 10:30 ET the index is in a one-sided programme; thrust-aligned trend entries have a longer run than the 60-pt target allows.
- Definition: breadth at 10:30 = number of the ten names above their prior session close; thrust days: >= thr up (long entries) or <= 10-thr up (short entries); RTH entries after 10:30 aligned with the thrust get target x m (stop fixed at 60) or size x1.25; thr {8,9} x {t1.25,t1.5,t2.0,s1.25}.
- Data: XNAS.ITCH 1-minute 2022-01..2026-10-13 (split days handled against the first bar).
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (1109 touched pair rows); flagged share per cell (clean rows): thr8_t1.25 10.6%, thr8_t1.5 10.6%, thr8_t2.0 10.6%, thr8_s1.25 10.6%, thr9_t1.25 7.1%, thr9_t1.5 7.1%, thr9_t2.0 7.1%, thr9_s1.25 7.1%; eligibility (declared): share 1.5-45%

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| thr8_t1.25 **(selected)** | -0.057 | +0.016 | -0.091 | -0.057 |
| thr8_t1.5 | -0.113 | -0.035 | -0.116 | -0.106 |
| thr8_t2.0 | -0.118 | +0.028 | -0.074 | -0.083 |
| thr8_s1.25 | -0.229 | -0.119 | -0.060 | -0.179 |
| thr9_t1.25 | -0.121 | -0.052 | +0.014 | -0.085 |
| thr9_t1.5 | -0.181 | -0.055 | +0.019 | -0.123 |
| thr9_t2.0 | -0.206 | -0.048 | +0.093 | -0.121 |
| thr9_s1.25 | -0.114 | +0.018 | +0.056 | -0.061 |

## Result for the carried cell: thr8_t1.25
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.40 | -0.057 | -0.069 |
| H1 | 2.83 | 2.84 | +0.016 | +0.032 |
| H2 | 2.48 | 2.39 | -0.091 | -0.111 |
| all | 1.90 | 1.84 | -0.057 | -0.064 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean -0.057 vs +0.050 / 0.70; H1 +0.016 vs +0.207 / 0.60; H2 -0.091 vs +0.214 / 0.30; all -0.057 vs +0.036 / 0.69
- bootstrap 90% CI of all-in uplift: [-0.218, +0.067]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: thr-1 -0.083; thr+1 -0.085; m x0.75 -0.086; m x1.25 -0.048; definitions {'thr-1': "(7, 't1.25')", 'thr+1': "(9, 't1.25')", 'm x0.75': "(8, 't1.1875')", 'm x1.25': "(8, 't1.3125')"}
- worst week (candidate vs pair): clean -81.9k vs -81.9k; H1 -78.3k vs -78.3k; H2 -79.7k vs -82.5k; all -81.9k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.990); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks -0.64; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift +0.005 -> HOLDS.
- Alternating months (select odd/read even, then reverse): select thr9_s1.25 (+0.049) reads -0.250; select thr8_t1.25 (-0.097) reads -0.006 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +0 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 1 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.40 | 2.68 | 4.41 | -78.8k | -78.1k | 299k | -81.9k | 43.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.84 | 6.16 | 4.03 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 2.39 | 4.88 | 3.67 | -78.5k | -77.9k | 217k | -79.7k | 38.9 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.84 | 3.61 | 9.13 | -78.7k | -78.0k | 299k | -81.9k | 42.3 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-18,595 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $9,600.
- Worst day: $-59,109 (pair $-59,109); worst week all-in: $-81,874 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: ten equity series for the 10:30 count; on a thrust day, aligned entries place the target at 60 x m points (OCO target modifiable at entry) or quantity x1.25.
Library: outputs/library/BK5_thr8_t1.25.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift -0.06 is the in-sample maximum of 8 eligible cells; out of sample it reads +0.02 on H1 and -0.09 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.70 (p95 +0.05) and the all-in uplift at 0.69 (p95 +0.04). Gates failed: uplift>=0.10 clean/H1/H2, own null all-in > p95 (and clean), bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bk5/.

DONE BK5
