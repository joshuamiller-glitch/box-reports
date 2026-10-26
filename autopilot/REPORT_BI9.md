# REPORT BI9 - OVERNIGHT VS RTH DECOMPOSITION FILTER OF THE PAIR (BI9; D06 x M4/M8, H4-H5)
**Verdict: NO. FOUND 0. Selected RTH_al_ALIGN_UP (clean-only among 6 eligible of 6 cells): weekly Sharpe uplift +0.25 clean / -0.06 H1 / -1.11 H2 (needed +0.10 each); all-in -0.08; bootstrap 90% CI of all-in uplift [-0.62, +0.45]; own null (200 replicates) p95 clean +0.18 / all-in -0.05 (real rank clean 0.97, all-in 0.91); plateau 0.00 of 4.** Pre-registered in PREREG_AUTOPILOT.md / IDEAS_BI.md 'BATCH BI' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: The overnight return tends to reverse and the RTH return to continue (Lou-Polk-Skouras), so pair entries aligned with the continuing component should keep more of their edge than entries aligned with the reversing component.
- Definition: ON = (price at the entry minute-1 / last RTH close - 1 in points) / trailing 60-RTH-day sd of RTH open-to-close moves; RTHP = last completed RTH open-to-close move / the same sd; features side x ON and side x RTHP; terciles frozen on clean; schemes COUNTER_DOWN (bottom tercile x0.5), ALIGN_UP (top tercile x1.5), TWO.
- Data: NQ 1-minute harness series (pair rows).
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (4411 touched pair rows); flagged share per cell (clean rows): ON_al_COUNTER_DOWN 33.3%, ON_al_ALIGN_UP 33.3%, ON_al_TWO 66.7%, RTH_al_COUNTER_DOWN 33.3%, RTH_al_ALIGN_UP 33.3%, RTH_al_TWO 66.6%; eligibility (declared): none (regime partition)

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| ON_al_COUNTER_DOWN | -0.211 | -0.892 | +1.257 | +0.044 |
| ON_al_ALIGN_UP | -0.039 | +0.304 | -0.082 | +0.038 |
| ON_al_TWO | +0.209 | -0.563 | +0.507 | +0.188 |
| RTH_al_COUNTER_DOWN | -0.457 | +1.268 | -0.450 | -0.193 |
| RTH_al_ALIGN_UP **(selected)** | +0.248 | -0.062 | -1.106 | -0.078 |
| RTH_al_TWO | -0.257 | +1.194 | -0.908 | -0.203 |

## Result for the carried cell: RTH_al_ALIGN_UP
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.71 | +0.248 | +0.206 |
| H1 | 2.83 | 2.77 | -0.062 | +0.008 |
| H2 | 2.48 | 1.38 | -1.106 | -1.211 |
| all | 1.90 | 1.82 | -0.078 | -0.117 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean +0.248 vs +0.183 / 0.97; H1 -0.062 vs +0.569 / 0.76; H2 -1.106 vs -0.073 / 0.32; all -0.078 vs -0.046 / 0.91
- bootstrap 90% CI of all-in uplift: [-0.622, +0.454]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: win45 -0.187; win75 -0.109; share25 -0.134; share42 -0.259; definitions {'win45': "('RTH_al', 45, 'ALIGN_UP')", 'win75': "('RTH_al', 75, 'ALIGN_UP')", 'share25': "('RTH_al', 60, 'ALIGN_UP', 0.25)", 'share42': "('RTH_al', 60, 'ALIGN_UP', 0.42)"}
- worst week (candidate vs pair): clean -80.6k vs -81.9k; H1 -79.3k vs -78.3k; H2 -78.9k vs -82.5k; all -80.6k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.823); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks +0.11; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift -0.081 -> does not hold.
- Alternating months (select odd/read even, then reverse): select ON_al_TWO (+0.318) reads +0.006; select RTH_al_ALIGN_UP (+0.859) reads -0.326 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +47,018 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 0 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.71 | 3.27 | 5.57 | -78.9k | -78.3k | 284k | -80.6k | 40.0 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.77 | 6.13 | 5.61 | -79.2k | -78.7k | 133k | -79.3k | 32.1 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 1.38 | 2.46 | 2.28 | -78.9k | -78.6k | 225k | -78.9k | 50.0 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.82 | 3.48 | 10.02 | -79.2k | -78.5k | 284k | -80.6k | 41.1 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-27,712 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $14,400.
- Worst day: $-68,844 (pair $-59,109); worst week all-in: $-80,611 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: prior RTH close/open and current price are chart values; entry quantity multiplier 0.5/1/1.5 by tercile edges frozen from the clean span.
Library: outputs/library/BI9_RTH_al_ALIGN_UP.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift +0.25 is the in-sample maximum of 6 eligible cells; out of sample it reads -0.06 on H1 and -1.11 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.97 (p95 +0.18) and the all-in uplift at 0.91 (p95 -0.05). Gates failed: uplift>=0.10 clean/H1/H2, own null all-in > p95 (and clean), bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bi_ov_run.py, ap_bk_rep.py; outputs/autopilot/bk/bi9/.

DONE BI9
