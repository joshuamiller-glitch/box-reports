# REPORT BK6 - GEX-SIGN BRACKET SCALING (BACKLOG2 #54; D03 x M5/M7, H5)
**Verdict: NO. FOUND 0. Selected a1.5_b1.0 (clean-only among 6 eligible of 6 cells): weekly Sharpe uplift +0.29 clean / -0.39 H1 / -1.78 H2 (needed +0.10 each); all-in -0.29; bootstrap 90% CI of all-in uplift [-0.76, +0.15]; own null (200 replicates) p95 clean +0.55 / all-in -0.08 (real rank clean 0.76, all-in 0.69); plateau 0.00 of 4.** Pre-registered in PREREG_AUTOPILOT.md / PREREG_BK.md 'BATCH BK' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: Negative dealer gamma amplifies moves (a 60-pt stop is inside the noise, targets are reached faster), positive gamma damps them; scale stop and target by a (negative GEX) / b (positive GEX).
- Definition: gex_norm of the previous trading date (NQ options open interest, outputs/autopilot/opt/feat_NQ.parquet), sign cut at 0; stop AND target x a / x b with unchanged contract count (risk per trade scales with the stop); (a,b) in {(1.25,1),(1,0.8),(1.25,0.8),(1.5,1),(1,0.67),(1.5,0.67)}; no eligibility share rule (sign split is a regime partition, declared before the run).
- Data: NQ options OI/greeks daily features 2019-2026.
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (4451 touched pair rows); flagged share per cell (clean rows): a1.25_b1.0 35.0%, a1.0_b0.8 64.9%, a1.25_b0.8 99.8%, a1.5_b1.0 35.0%, a1.0_b0.67 64.9%, a1.5_b0.67 99.8%; eligibility (declared): none (regime partition)

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| a1.25_b1.0 | +0.011 | -0.525 | -1.907 | -0.506 |
| a1.0_b0.8 | -1.659 | -1.303 | -1.582 | -1.559 |
| a1.25_b0.8 | -1.556 | -1.663 | -3.315 | -1.944 |
| a1.5_b1.0 **(selected)** | +0.285 | -0.395 | -1.782 | -0.289 |
| a1.0_b0.67 | -2.619 | -3.018 | -4.361 | -3.064 |
| a1.5_b0.67 | -2.195 | -3.180 | -5.928 | -3.151 |

## Result for the carried cell: a1.5_b1.0
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.75 | +0.285 | +0.345 |
| H1 | 2.83 | 2.43 | -0.395 | -0.340 |
| H2 | 2.48 | 0.70 | -1.782 | -1.993 |
| all | 1.90 | 1.61 | -0.289 | -0.294 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): FAIL
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean +0.285 vs +0.551 / 0.76; H1 -0.395 vs +0.027 / 0.75; H2 -1.782 vs -0.939 / 0.35; all -0.289 vs -0.081 / 0.69
- bootstrap 90% CI of all-in uplift: [-0.764, +0.153]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: a-1 x0.75 -0.390; a-1 x1.25 -0.345; b-1 x0.75 -0.289; b-1 x1.25 -0.289; definitions {'a-1 x0.75': '(1.375, 1.0)', 'a-1 x1.25': '(1.625, 1.0)', 'b-1 x0.75': '(1.5, 1.0)', 'b-1 x1.25': '(1.5, 1.0)'}
- worst week (candidate vs pair): clean -82.7k vs -81.9k; H1 -82.3k vs -78.3k; H2 -82.5k vs -82.5k; all -82.7k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.888); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks +0.12; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift -0.920 -> does not hold.
- Alternating months (select odd/read even, then reverse): select a1.25_b1.0 (+0.133) reads -0.168; select a1.5_b1.0 (+0.593) reads -0.006 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +0 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 0 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.75 | 3.29 | 5.88 | -79.2k | -78.3k | 278k | -82.7k | 41.0 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.43 | 5.09 | 3.86 | -80.3k | -79.4k | 152k | -82.3k | 39.3 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 0.70 | 1.22 | 1.09 | -81.2k | -79.9k | 240k | -82.5k | 55.6 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.61 | 2.99 | 8.00 | -80.2k | -79.1k | 311k | -82.7k | 44.0 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-18,595 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $14,400.
- Worst day: $-80,219 (pair $-59,109); worst week all-in: $-82,749 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: daily gamma sign must come from an external OI-based GEX file (NQ.OPT OI + greeks) updated each morning; strategy reads the sign and sets stop/target ticks x a/b at entry.
Library: outputs/library/BK6_a1.5_b1.0.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift +0.29 is the in-sample maximum of 6 eligible cells; out of sample it reads -0.39 on H1 and -1.78 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.76 (p95 +0.55) and the all-in uplift at 0.69 (p95 -0.08). Gates failed: uplift>=0.10 clean/H1/H2, worst week not worse (all-in), own null all-in > p95 (and clean), bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Diagnostic (report-only, run after selection): the clean gain is a sizing artefact. Same cell with constant-dollar risk (contracts scaled by 1/scale so a full stop stays $9,600) gives uplift -0.01 clean / +0.05 H1 / -1.83 H2 / -0.43 all-in; wider brackets on negative-GEX days at constant contract count simply add exposure in the clean span (which was bullish for the pair), and the H2 loss (-1.8) shows the exposure bites when the pair loses. The tighter-bracket cells on positive-GEX days (b = 0.8, 0.67) lose 1.6-2.6 Sharpe on clean already: tightening stops on quiet days is destructive for the trend books.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bk6/.

DONE BK6
