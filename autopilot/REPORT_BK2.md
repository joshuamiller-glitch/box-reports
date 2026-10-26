# REPORT BK2 - QQQ-vs-NQ BASIS-DRIFT REGIME TILT (BACKLOG2 #57; D04 x M4/M8, H5)
**Verdict: NO. FOUND 0. Selected L5_HIGH_DOWN (clean-only among 6 eligible of 6 cells): weekly Sharpe uplift +0.09 clean / -0.37 H1 / +0.70 H2 (needed +0.10 each); all-in +0.11; bootstrap 90% CI of all-in uplift [-0.33, +0.57]; own null (200 replicates) p95 clean +0.20 / all-in +0.22 (real rank clean 0.88, all-in 0.85); plateau 1.00 of 4.** Pre-registered in PREREG_AUTOPILOT.md / PREREG_BK.md 'BATCH BK' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: When the futures-minus-cash spread has been drifting (arbitrage pressure, carry, dividends) index flow is dominated by basis traders and trend entries face more mean-reverting prints.
- Definition: e_d = daily NQ-adj log return minus QQQ log return over 09:30-15:59 closes (|e|>0.5% = artefact -> missing); E_L = sum of e over the L dates before the entry date / (sd60 sqrt L); feature |E_L|; terciles frozen on clean; HIGH_DOWN / HIGH_UP / TWO_V; L {5,20}.
- Data: XNAS.ITCH QQQ 1-min closes 2022-01..2026-10-13 and NQ 1-min harness series.
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (4902 touched pair rows); flagged share per cell (clean rows): L5_HIGH_DOWN 32.3%, L5_HIGH_UP 32.3%, L5_TWO_V 64.4%, L20_HIGH_DOWN 27.3%, L20_HIGH_UP 27.3%, L20_TWO_V 54.4%; eligibility (declared): none (regime partition)

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| L5_HIGH_DOWN **(selected)** | +0.088 | -0.371 | +0.696 | +0.111 |
| L5_HIGH_UP | -0.107 | -0.463 | -0.772 | -0.299 |
| L5_TWO_V | -0.518 | -0.243 | -0.661 | -0.520 |
| L20_HIGH_DOWN | -0.104 | -0.137 | -0.724 | -0.264 |
| L20_HIGH_UP | -0.001 | -0.439 | -1.056 | -0.282 |
| L20_TWO_V | -0.226 | -0.174 | -0.529 | -0.318 |

## Result for the carried cell: L5_HIGH_DOWN
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.55 | +0.088 | +0.121 |
| H1 | 2.83 | 2.46 | -0.371 | -0.339 |
| H2 | 2.48 | 3.18 | +0.696 | +0.566 |
| all | 1.90 | 2.01 | +0.111 | +0.110 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: PASS
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean +0.088 vs +0.204 / 0.88; H1 -0.371 vs +1.377 / 0.12; H2 +0.696 vs +0.685 / 0.95; all +0.111 vs +0.219 / 0.85
- bootstrap 90% CI of all-in uplift: [-0.334, +0.572]
- plateau: 1.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: L x0.75 +0.151; L x1.25 +0.382; share25 +0.278; share42 +0.122; definitions {'L x0.75': "(4, 'HIGH_DOWN')", 'L x1.25': "(6, 'HIGH_DOWN')", 'share25': "(5, 'HIGH_DOWN', 0.25)", 'share42': "(5, 'HIGH_DOWN', 0.42)"}
- worst week (candidate vs pair): clean -79.9k vs -81.9k; H1 -77.9k vs -78.3k; H2 -77.1k vs -82.5k; all -79.9k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.888); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks -0.38; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift +0.523 -> HOLDS.
- Alternating months (select odd/read even, then reverse): select L5_TWO_V (+0.136) reads -1.085; select L5_HIGH_DOWN (+0.254) reads -0.036 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +81,069 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 1 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.55 | 2.91 | 7.12 | -78.1k | -77.6k | 187k | -79.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.46 | 4.74 | 2.22 | -77.4k | -69.2k | 204k | -77.9k | 35.7 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 3.18 | 7.60 | 6.23 | -68.7k | -55.7k | 135k | -77.1k | 41.7 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 2.01 | 3.93 | 12.89 | -77.9k | -77.0k | 204k | -79.9k | 41.7 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-18,115 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $9,600.
- Worst day: $-63,491 (pair $-59,109); worst week all-in: $-79,868 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: QQQ daily close series plus NQ daily close in the same workspace; daily state computed at the prior session close; entry quantity multiplier 0.5/1/1.5 by tercile edges frozen from the clean span.
Library: outputs/library/BK2_L5_HIGH_DOWN.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift +0.09 is the in-sample maximum of 6 eligible cells; out of sample it reads -0.37 on H1 and +0.70 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.88 (p95 +0.20) and the all-in uplift at 0.85 (p95 +0.22). Gates failed: uplift>=0.10 clean/H1/H2, own null all-in > p95 (and clean), bootstrap CI lo > 0, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bk2/.

DONE BK2
