# REPORT BK1 - SINGLE-NAME SHOCK PAUSE (BACKLOG2 #59; D04 x M4/M7, H2-H3)
**Verdict: NO. FOUND 0. Selected thr6_W30_HALF (clean-only among 6 eligible of 8 cells): weekly Sharpe uplift +0.11 clean / -0.09 H1 / -0.04 H2 (needed +0.10 each); all-in +0.06; bootstrap 90% CI of all-in uplift [-0.06, +0.19]; own null (200 replicates) p95 clean +0.18 / all-in +0.14 (real rank clean 0.84, all-in 0.73); plateau 0.75 of 4.** Pre-registered in PREREG_AUTOPILOT.md / PREREG_BK.md 'BATCH BK' before the first scored run.

## Mechanism (one sentence) and set-up
- Mechanism: A >6-sigma 5-minute move in one of the ten mega-cap names (earnings, news, halts) makes the next 15-30 minutes of NQ headline-driven; the 1-minute trend books whipsaw there. Halve or skip pair entries for W minutes after the shock.
- Definition: z5 = ln(C_t/C_{t-5})/(sd1 x sqrt5) per name (sd1 = mean of the previous 20 sessions' 1-minute return sd), shock = max over ten names |z5| > thr at minutes 09:35-15:59; entries within W minutes after a shock minute are halved/skipped (entries outside RTH unaffected); grid thr {6,8} x W {15,30} x {HALF,SKIP}; cells whose clean flagged share is outside 1.5-45% are ineligible (thr8 W15: 1.0%).
- Data: XNAS.ITCH 1-minute (Nasdaq-venue prints) 2022-01..2026-10-13; prices raw (splits handled by using within-day returns only).
- Engine and fill model: live pair rows (ROWS_corrected_engine, 13,184 rows to 2026-10-16) replayed on 1-second bars (G11-C convention: rows closed externally keep their external exit) through the live account rules (per-book 5R/-2R, day lock, week floor 8R), baseline B.Cfg(wk_floor=8,wk_loss_pb=None) computed in a CLEAN process and reproduced: clean 1.46 / H1 2.83 / H2 2.48 (2.30 before the 2026-10-16 extension) / all-in 1.90. Fill: market at the entry bar, 1 tick/side + $34.88 per 8-lot round trip; 2x slippage = SLIP_PT 1.0 on baseline and variant. Skipped/halved rows still exist in the netting history (convention of all pair-conditioning families).
- small-sample flag: no (697 touched pair rows); flagged share per cell (clean rows): thr6_W15_HALF 2.8%, thr6_W15_SKIP 2.8%, thr6_W30_HALF 5.8%, thr6_W30_SKIP 5.8%, thr8_W15_HALF 1.0%, thr8_W15_SKIP 1.0%, thr8_W30_HALF 2.3%, thr8_W30_SKIP 2.3%; eligibility (declared): share 1.5-45%

## Grid, uplift per cell (weekly Sharpe vs the live pair; clean-only selection; other cells' H1/H2 printed for transparency, unused)
| cell | clean | H1 | H2 | all-in |
|---|---|---|---|---|
| thr6_W15_HALF | +0.033 | +0.025 | +0.037 | +0.037 |
| thr6_W15_SKIP | -0.014 | -0.126 | +0.092 | -0.006 |
| thr6_W30_HALF **(selected)** | +0.112 | -0.086 | -0.036 | +0.061 |
| thr6_W30_SKIP | +0.019 | -0.238 | +0.011 | -0.004 |
| thr8_W15_HALF | +0.018 | -0.085 | +0.014 | +0.007 |
| thr8_W15_SKIP | -0.022 | -0.145 | +0.028 | -0.024 |
| thr8_W30_HALF | +0.014 | -0.022 | +0.050 | +0.029 |
| thr8_W30_SKIP | -0.034 | -0.138 | +0.084 | -0.005 |

## Result for the carried cell: thr6_W30_HALF
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.57 | +0.112 | +0.108 |
| H1 | 2.83 | 2.74 | -0.086 | -0.117 |
| H2 | 2.48 | 2.45 | -0.036 | -0.056 |
| all | 1.90 | 1.96 | +0.061 | +0.048 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): PASS
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: PASS
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank, 200 replicates, feature permuted within book x month x session blocks, exact account re-runs): clean +0.112 vs +0.180 / 0.84; H1 -0.086 vs +0.381 / 0.23; H2 -0.036 vs +0.059 / 0.52; all +0.061 vs +0.143 / 0.73
- bootstrap 90% CI of all-in uplift: [-0.065, +0.190]
- plateau: 0.75 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: thr x0.75 +0.110; thr x1.25 +0.027; W x0.75 +0.066; W x1.25 +0.181; definitions {'thr x0.75': "(4.5, 30, 'HALF')", 'thr x1.25': "(7.5, 30, 'HALF')", 'W x0.75': "(6, 22, 'HALF')", 'W x1.25': "(6, 38, 'HALF')"}
- worst week (candidate vs pair): clean -81.9k vs -81.9k; H1 -77.8k vs -78.3k; H2 -81.2k vs -82.5k; all -81.9k vs -82.5k
- worst-decile correlation: overlay on the pair itself (weekly corr with pair 0.989); correlation of the candidate-minus-pair weekly difference with the pair in the pair's worst-decile weeks -0.53; no hedge claim, so the shift null is not a gate (not run).

## Replication leg (Gate Amendment 2: >= 2 of 4 must hold with the same sign and >= 50% of the clean uplift)
- H0 2023-02-10..07-31: uplift +0.122 -> HOLDS.
- Alternating months (select odd/read even, then reverse): select thr6_W30_HALF (+0.026) reads +0.160; select thr6_W30_HALF (+0.160) reads +0.026 -> does not hold.
- Newest live weeks (2026-10-09..16, extension weeks): candidate minus pair -4,743 USD over the window (one week: report-only, no Sharpe).
- Cross-instrument ES/RTY: n/a (pair-row overlay; no ES/RTY pair rows with this state in the harness). Replications counted: 1 of 2 required.
- ERA FLAG: not testable (pair rows start 2023-02; state data start 2022-01; GEX features 2019+ but the pair has no earlier rows). Gross/net cost decomposition: overlay changes only size/skip/bracket of existing trades; cost per trade unchanged ($34.88 per 8 lots).

## Insurance metrics (weekly, USD at 8 contracts)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.57 | 3.00 | 5.13 | -78.7k | -78.0k | 278k | -81.9k | 41.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.74 | 6.11 | 4.38 | -77.5k | -67.5k | 139k | -77.8k | 39.3 |
| H2 pair | 2.48 | 5.08 | 3.77 | -81.1k | -79.2k | 217k | -82.5k | 41.7 |
| H2 cand | 2.45 | 4.97 | 3.72 | -79.4k | -78.3k | 217k | -81.2k | 41.7 |
| all pair | 1.90 | 3.71 | 9.79 | -79.2k | -78.2k | 280k | -82.5k | 42.3 |
| all cand | 1.96 | 3.85 | 10.22 | -78.7k | -78.0k | 278k | -81.9k | 41.7 |

## Sized dollars (8 NQ contracts, R = $9,600 per full 60-pt stop)
- Worst single trade, carried cell: $-18,595 (pair: $-18,595); largest possible stop loss at the cell's maximum multiplier x stop: $9,600.
- Worst day: $-59,109 (pair $-59,109); worst week all-in: $-81,874 (pair $-82,524).

## Causality check
- Every feature uses data labelled <= entry minute - 1 (entry fill at the open of bar ei, so only bars closed before it). Automated poison test: 25 sampled rows, all data from the entry minute onward replaced by noise / dropped from the tables, feature recomputed: 0 mismatches (PASS). Daily states use dates strictly before the entry's ET date. Selection used clean rows only; H1/H2 of unselected cells appear above for transparency and were not used.

## Executability
NT8: a 10-symbol Nasdaq-listed 1-minute data feed (AAPL...NFLX) in the same workspace; the strategy keeps a rolling 20-session 1-minute sd per name and a countdown of minutes since the last >thr shock; on entry, quantity x0.5 (or no entry) while countdown < W. Needs equity data entitlement; margin unchanged.
Library: outputs/library/BK1_thr6_W30_HALF.parquet (pair variant, PAIR_ACCT netting).

## Reading
The carried cell's clean uplift +0.11 is the in-sample maximum of 6 eligible cells; out of sample it reads -0.09 on H1 and -0.04 on H2. Against its own timing-destroyed null the clean uplift ranks at 0.84 (p95 +0.18) and the all-in uplift at 0.73 (p95 +0.14). Gates failed: uplift>=0.10 clean/H1/H2, own null all-in > p95 (and clean), bootstrap CI lo > 0, 2x slip uplift >= 0.10 each span, alt-month both directions hold.

Files: code/census/night_ins/ap_bk_data.py, ap_bk_run.py, ap_bk_rep.py; outputs/autopilot/bk/bk1/.

DONE BK1
