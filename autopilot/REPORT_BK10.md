# REPORT BK10 - MEGA-CAP EARNINGS NIGHTS: SKIP/HALF GLOBEX ENTRIES (BACKLOG2 #76; D10 x M4/M7, H3-H4)
**Verdict: NO. FOUND 0. Selected scopeA_HALF_six (clean-only among 8 eligible of 8 cells): weekly Sharpe uplift -0.09 clean / +0.43 H1 / -0.02 H2 (needed +0.10 each); all-in +0.01; bootstrap 90% CI of all-in uplift [-0.16, +0.18]; own null (200 replicates) p95 clean +0.11 / all-in +0.11 (real rank clean 0.56, all-in 0.78); plateau 0.00 of 3.** Pre-registered in PREREG_AUTOPILOT.md / PREREG_BK.md 'BATCH BK' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: After an after-close release by one of the ten names Globex NQ is gap-and-reverse driven by the single name; the trend books' overnight entries are low quality.
- Definition: release dates = EDGAR 8-K item 2.02 accepted at or after 16:00 ET (a scheduled, ex-ante-known calendar item); entries from 16:00 ET of the release date until scope end (02:59 or 09:29 ET next calendar day) halved or skipped; names all ten or the six largest; eligibility >= 40 flagged clean rows.
- Data: EDGAR 8-K acceptance timestamps 2023-2026 (data/gap/edgar).
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (300 touched pair rows); flagged share per cell (clean rows): scopeA_HALF_ten 3.7%, scopeA_HALF_six 2.3%, scopeA_SKIP_ten 3.7%, scopeA_SKIP_six 2.3%, scopeB_HALF_ten 6.8%, scopeB_HALF_six 4.0%, scopeB_SKIP_ten 6.8%, scopeB_SKIP_six 4.0%; eligibility (declared): >= 40 flagged clean rows

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| scopeA_HALF_ten | -0.186 | +0.875 | -0.047 | -0.022 |
| scopeA_HALF_six **(selected)** | -0.086 | +0.435 | -0.021 | +0.007 |
| scopeA_SKIP_ten | -0.708 | +1.049 | +0.548 | -0.201 |
| scopeA_SKIP_six | -0.472 | +0.501 | +0.454 | -0.105 |
| scopeB_HALF_ten | -0.261 | +0.646 | +0.017 | -0.102 |
| scopeB_HALF_six | -0.184 | +0.147 | +0.139 | -0.069 |
| scopeB_SKIP_ten | -0.426 | +1.167 | +0.079 | -0.091 |
| scopeB_SKIP_six | -0.360 | +0.639 | +0.221 | -0.059 |

## Result for the carried cell: scopeA_HALF_six
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.37 | -0.086 | -0.126 |
| H1 | 2.83 | 3.26 | +0.435 | +0.295 |
| H2 | 2.48 | 2.46 | -0.021 | -0.084 |
| all | 1.90 | 1.90 | +0.007 | -0.064 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean -0.086 vs +0.112 / 0.56; H1 +0.435 vs +0.747 / 0.77; H2 -0.021 vs +0.340 / 0.73; all +0.007 vs +0.107 / 0.78
- bootstrap 90% CI of all-in uplift: [-0.157, +0.177]
- plateau: 0.00 of 3 neighbours keep >= 75% of the all-in uplift; neighbours: end-60 -0.049; end+60 -0.007; names swap -0.022; definitions {'end-60': "(120, 'HALF', 'six')", 'end+60': "(240, 'HALF', 'six')", 'names swap': "(180, 'HALF', 'ten')"}
- worst week (candidate vs pair): clean -81.9k vs -81.9k; H1 -78.3k vs -78.3k; H2 -82.5k vs -82.5k; all -82.5k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.983); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks -0.16; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift +0.088 -> HOLDS.
- Alternating months (select odd/read even, then reverse): select scopeA_HALF_six (-0.242) reads +0.112; select scopeB_HALF_six (+0.174) reads -0.450 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +0 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 1 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.37 | 2.61 | 4.72 | -78.9k | -78.1k | 265k | -81.9k | 43.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 3.26 | 6.98 | 4.58 | -77.6k | -66.0k | 152k | -78.3k | 35.7 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 2.46 | 4.94 | 3.53 | -81.1k | -79.2k | 232k | -82.5k | 38.9 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.90 | 3.71 | 10.42 | -79.3k | -78.3k | 265k | -82.5k | 41.7 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-18,595 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $9,600.
- Worst day: $-58,979 (pair $-59,109); worst week all-in: $-82,524 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: a hard-coded or file-based earnings calendar (date, after-close flag) for ten tickers; strategies skip or halve entries in the window.
Library: outputs/library/BK10_scopeA_HALF_six.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift -0.09 is the in-sample maximum of 8 eligible cells; out of sample it reads +0.43 on H1 and -0.02 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.56 (p95 +0.11) and the all-in uplift at 0.78 (p95 +0.11). Gates failed: uplift>=0.10 clean/H1/H2, own null all-in > p95 (and clean), bootstrap CI lo > 0, plateau >= 75%, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bk10/.

DONE BK10
