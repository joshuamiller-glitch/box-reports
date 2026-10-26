# REPORT BK3 - INTRA-NDX DISPERSION (SEMIS VS SOFTWARE) TILT (BACKLOG2 #58; D04 x M4/M8, H3-H4)
**Verdict: NO. FOUND 0. Selected VOL_HIGH_DOWN (clean-only among 6 eligible of 6 cells): weekly Sharpe uplift +0.21 clean / +0.02 H1 / -0.18 H2 (needed +0.10 each); all-in +0.11; bootstrap 90% CI of all-in uplift [-0.08, +0.34]; own null (200 replicates) p95 clean +0.21 / all-in +0.13 (real rank clean 0.95, all-in 0.92); plateau 0.75 of 4.** Pre-registered in PREREG_AUTOPILOT.md / PREREG_BK.md 'BATCH BK' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: When semis and software diverge intraday NQ carries a rotation, not a trend; the trend books' 1-min signals are relative-value noise.
- Definition: s_t = mean r(NVDA,AVGO,AMD) - mean r(MSFT,ADBE) per minute; ABS = |sum s over the last 60 min|/(sd_s sqrt60), VOL = ln(realised spread vol last 60 min / its trailing 20-session level); RTH entries 10:30-15:59; terciles frozen on clean; schemes HIGH_DOWN/HIGH_UP/TWO_V.
- Data: XNAS.ITCH 1-minute 2022-01..2026-10-13.
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (1553 touched pair rows); flagged share per cell (clean rows): ABS_HIGH_DOWN 12.2%, ABS_HIGH_UP 12.2%, ABS_TWO_V 24.3%, VOL_HIGH_DOWN 12.2%, VOL_HIGH_UP 12.2%, VOL_TWO_V 24.3%; eligibility (declared): none (regime partition)

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| ABS_HIGH_DOWN | +0.034 | -0.309 | -0.228 | -0.073 |
| ABS_HIGH_UP | -0.026 | -0.360 | +0.063 | -0.042 |
| ABS_TWO_V | -0.009 | -0.147 | -0.259 | -0.072 |
| VOL_HIGH_DOWN **(selected)** | +0.211 | +0.019 | -0.183 | +0.113 |
| VOL_HIGH_UP | -0.106 | +0.049 | +0.103 | -0.042 |
| VOL_TWO_V | -0.173 | +0.322 | -0.182 | -0.100 |

## Result for the carried cell: VOL_HIGH_DOWN
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.67 | +0.211 | +0.212 |
| H1 | 2.83 | 2.85 | +0.019 | +0.161 |
| H2 | 2.48 | 2.30 | -0.183 | -0.351 |
| all | 1.90 | 2.01 | +0.113 | +0.094 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: PASS
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean +0.211 vs +0.211 / 0.95; H1 +0.019 vs +0.392 / 0.41; H2 -0.183 vs +0.052 / 0.27; all +0.113 vs +0.130 / 0.92
- bootstrap 90% CI of all-in uplift: [-0.082, +0.343]
- plateau: 0.75 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: W45 +0.089; W75 +0.065; share25 +0.120; share42 +0.165; definitions {'W45': "('VOL', 45, 'HIGH_DOWN')", 'W75': "('VOL', 75, 'HIGH_DOWN')", 'share25': "('VOL', 60, 'HIGH_DOWN', 0.25)", 'share42': "('VOL', 60, 'HIGH_DOWN', 0.42)"}
- worst week (candidate vs pair): clean -81.9k vs -81.9k; H1 -78.7k vs -78.3k; H2 -79.7k vs -82.5k; all -81.9k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.973); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks +0.15; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift -0.195 -> does not hold.
- Alternating months (select odd/read even, then reverse): select VOL_HIGH_DOWN (+0.350) reads -0.017; select ABS_TWO_V (+0.089) reads -0.144 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair +0 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 0 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.67 | 3.22 | 6.13 | -78.4k | -77.8k | 242k | -81.9k | 43.8 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.85 | 6.88 | 3.85 | -78.5k | -65.2k | 168k | -78.7k | 39.3 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 2.30 | 4.62 | 3.48 | -78.5k | -77.8k | 217k | -79.7k | 41.7 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 2.01 | 4.01 | 11.93 | -78.6k | -77.9k | 242k | -81.9k | 42.9 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-18,595 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $9,600.
- Worst day: $-59,109 (pair $-59,109); worst week all-in: $-81,874 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: 5 Nasdaq equity 1-minute series (NVDA AVGO AMD MSFT ADBE); per-minute spread state; entry multiplier by tercile edges frozen from the clean span.
Library: outputs/library/BK3_VOL_HIGH_DOWN.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift +0.21 is the in-sample maximum of 6 eligible cells; out of sample it reads +0.02 on H1 and -0.18 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.95 (p95 +0.21) and the all-in uplift at 0.92 (p95 +0.13). Gates failed: uplift>=0.10 clean/H1/H2, own null all-in > p95 (and clean), bootstrap CI lo > 0, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bk3/.

DONE BK3
