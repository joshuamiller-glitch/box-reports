# REPORT BK7 - 0DTE PIN STRIKE AS TARGET CAP (BACKLOG2 #49 and #53; D03 x M5, H2-H3)
**Verdict: NO. FOUND 0. Selected dmin20_buf0_pintop1 (clean-only among 8 eligible of 8 cells): weekly Sharpe uplift -0.12 clean / +0.15 H1 / -0.07 H2 (needed +0.10 each); all-in -0.05; bootstrap 90% CI of all-in uplift [-0.15, +0.05]; own null (200 replicates) p95 clean -0.03 / all-in -0.05 (real rank clean 0.59, all-in 0.95); plateau 0.00 of 4.** Pre-registered in PREREG_AUTOPILOT.md / PREREG_BK.md 'BATCH BK' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: The largest 0DTE strike-volume cluster near price acts as a magnet/barrier (dealer hedging, round-number order concentration); a 60-pt target beyond it is reached less often than a target at it.
- Definition: pin = strike with the largest cumulative 0DTE (NDXP) traded size through the last completed 30-min slot among strikes within 100 pts of the NDXP forward (PREREG amendment 1); D = signed distance ahead in the trade direction; if dmin <= D < 60 the target becomes max(D-buf, 8) (stop 60); top1 or second-largest; dmin {10,20} x buf {0,5} x {top1,top2}.
- Data: OPRA NDXP trades reduced to 30-min strike tables 2022-2026 (data/autopilot/opt0dte).
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (1053 touched pair rows); flagged share per cell (clean rows): dmin10_buf0_pintop1 10.1%, dmin10_buf0_pintop2 11.4%, dmin10_buf5_pintop1 10.1%, dmin10_buf5_pintop2 11.4%, dmin20_buf0_pintop1 8.2%, dmin20_buf0_pintop2 9.2%, dmin20_buf5_pintop1 8.2%, dmin20_buf5_pintop2 9.2%; eligibility (declared): share 1.5-45%

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| dmin10_buf0_pintop1 | -0.154 | +0.182 | -0.063 | -0.069 |
| dmin10_buf0_pintop2 | -0.287 | -0.374 | -0.149 | -0.269 |
| dmin10_buf5_pintop1 | -0.176 | +0.071 | -0.072 | -0.109 |
| dmin10_buf5_pintop2 | -0.292 | -0.514 | -0.281 | -0.321 |
| dmin20_buf0_pintop1 **(selected)** | -0.116 | +0.152 | -0.066 | -0.053 |
| dmin20_buf0_pintop2 | -0.234 | -0.254 | -0.171 | -0.222 |
| dmin20_buf5_pintop1 | -0.181 | +0.100 | -0.135 | -0.118 |
| dmin20_buf5_pintop2 | -0.227 | -0.373 | -0.267 | -0.256 |

## Result for the carried cell: dmin20_buf0_pintop1
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.34 | -0.116 | -0.217 |
| H1 | 2.83 | 2.98 | +0.152 | +0.207 |
| H2 | 2.48 | 2.42 | -0.066 | -0.042 |
| all | 1.90 | 1.84 | -0.053 | -0.106 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean -0.116 vs -0.025 / 0.59; H1 +0.152 vs +0.090 / 0.97; H2 -0.066 vs +0.014 / 0.74; all -0.053 vs -0.054 / 0.95
- bootstrap 90% CI of all-in uplift: [-0.153, +0.051]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: dmin x0.75 -0.074; dmin x1.25 -0.025; buf+5 -0.118; buf+10 -0.145; definitions {'dmin x0.75': '(15.0, 0, 1)', 'dmin x1.25': '(25.0, 0, 1)', 'buf+5': '(20, 5, 1)', 'buf+10': '(20, 10, 1)'}
- worst week (candidate vs pair): clean -81.9k vs -81.9k; H1 -78.3k vs -78.3k; H2 -82.5k vs -82.5k; all -82.5k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.992); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks +0.01; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift -0.211 -> does not hold.
- Alternating months (select odd/read even, then reverse): select dmin20_buf0_pintop1 (-0.043) reads -0.167; select dmin20_buf5_pintop2 (-0.107) reads -0.321 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +0 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 0 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.34 | 2.52 | 4.64 | -78.7k | -78.0k | 264k | -81.9k | 45.7 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.98 | 6.99 | 4.14 | -77.6k | -66.4k | 162k | -78.3k | 35.7 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 2.42 | 4.86 | 3.63 | -81.1k | -79.2k | 220k | -82.5k | 41.7 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.84 | 3.61 | 10.21 | -79.2k | -78.2k | 264k | -82.5k | 43.5 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-18,595 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $9,600.
- Worst day: $-59,109 (pair $-59,109); worst week all-in: $-82,524 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 8 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: needs a real-time OPRA NDXP trade feed (NOT available via Rithmic/NinjaTrader Brokerage; external options tape and a bridge to the chart would be required). Rule itself is a bracket modification at entry.
Library: outputs/library/BK7_dmin20_buf0_pintop1.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift -0.12 is the in-sample maximum of 8 eligible cells; out of sample it reads +0.15 on H1 and -0.07 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.59 (p95 -0.03) and the all-in uplift at 0.95 (p95 -0.05). Gates failed: uplift>=0.10 clean/H1/H2, own null all-in > p95 (and clean), bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bk7/.

DONE BK7
