# REPORT X1-REP (X1 replication plan, coordinator request)

> **UPDATE 2026-10-16: compression-breakout results (X1, Y6, B2-D) are NOT CONFIRMED under path-resolved 30-min execution (REPORT_Z1.md); the daily-bar fill model resolved 52% of triggers (both-touch days) incorrectly. Lead withdrawn.**

**NO - the clean-only-selected X1 cell does not reproduce the pair uplift: cell X1_h2_k2_SCR (clean-only selection), capped scale k=0.84 (uncapped 1.79); additive uplift at 20% share 0.09/-0.05/0.00 on clean/H1/H2 (all-in 0.05), own-null rank 0.94 (<0.95), block-bootstrap 90% CI of the all-in uplift [-0.05, 0.14]. The STANDALONE edge does replicate in split-sample (test-half Sharpe 1.52-1.58 vs null p95 <= 0.10). Status of X1 stays LEAD (standalone replicated, pair uplift not). Not FOUND, not FOUND-PENDING.**

Plan pre-registered in PREREG_AUTOPILOT.md ("X1 REPLICATION PLAN", 2026-10-16T14:28Z) before it was run; 8 frozen X1 cells, no new cells except the 4 screen thresholds in the split-sample selection set. Code ap_x1_rep.py, data outputs/autopilot/b2356/X1_rep.pkl. Fill model, slippage and baseline as REPORT_X1.md (B.Cfg(wk_floor=8,wk_loss_pb=None)).

## (a) Clean-only selection and worst-week-capped sizing
Standalone clean weekly Sharpe of the 8 cells: h1_k2_SCR 0.67, h1_k2_ALL26 0.63, h1_k3_SCR 0.72, h1_k3_ALL26 0.64, h2_k2_SCR 0.97, h2_k2_ALL26 0.27, h2_k3_SCR 0.96, h2_k3_ALL26 0.23. Selected (highest clean Sharpe, 2013-22 ignored): **X1_h2_k2_SCR**. Scale to the pair's clean weekly vol gives k=1.79, but the sleeve's clean worst week at that scale is $173,841 vs the pair's $81,874, so k is capped to 0.84 (sleeve worst clean week = pair worst clean week). Worst-decile corr -0.03, overall corr -0.03.

Additive (pair unchanged, sleeve at the share of pair risk, capped scale):
| share | dSh clean | H1 | H2 | all-in | worst week chg % | boot 90% lo | shift-null rank |
|---|---|---|---|---|---|---|---|
| 10% | 0.05 | -0.02 | 0.00 | 0.03 | 3 | -0.02 | 0.67 |
| 20% | 0.09 | -0.05 | 0.00 | 0.05 | 12 | -0.05 | 0.67 |
| 30% | 0.13 | -0.10 | 0.00 | 0.06 | 21 | -0.08 | 0.67 |
| 50% | 0.19 | -0.22 | -0.01 | 0.09 | 39 | -0.14 | 0.67 |

Constant-risk:
| share | net % | worst-week impr % | CVaR5 impr % | maxDD impr % | clean ww/cvar | H1 ww/cvar |
|---|---|---|---|---|---|---|
| 10% | -8.6 | 6.7 | 8.6 | 12.1 | 6/8 | 12/11 |
| 20% | -17.3 | 7.0 | 16.6 | 24.2 | 6/15 | 23/23 |
| 30% | -25.9 | 7.3 | 24.1 | 35.8 | 7/21 | 34/34 |
| 50% | -43.2 | 7.9 | 36.2 | 27.3 | 7/31 | 48/51 |

Reading: capping the worst week removes about half the size and with it the uplift; H1 and H2 are not positive for this cell (the 2-day-hold variants have much larger worst weeks than the 1-day cell of REPORT_X1). The constant-risk framing costs 9-43% of net for a 7-8% worst-week gain: not INSURANCE.

## (b) 2x slippage and plateau (same capped k, 20% share)
2x slippage uplift clean/H1/H2/all: 0.06/-0.09/-0.02/0.02. Plateau neighbours (hold, stop, screen threshold; share keeping >= 75% of base all-in uplift 0.05: 1.00):
| neighbour | clean | H1 | H2 | all |
|---|---|---|---|---|
| k1.5 | 0.10 | -0.03 | -0.03 | 0.05 |
| k2.5 | 0.08 | -0.08 | 0.00 | 0.04 |
| th0.0225 | 0.06 | -0.04 | 0.04 | 0.04 |
| th0.0375 | 0.09 | -0.00 | 0.03 | 0.06 |

## (c) Split-sample replication on 2013-22 (odd years <-> even years)
Selection set: 8 cells + 4 screen thresholds on the h1/k2 cell (12 cells); also market-level selection (markets with positive selection-half Sharpe).

| split     | cell_selected   |   sel_half_sh |   test_half_sh |   markets_kept |   mk_sel_sh |   mk_test_sh |   full_ALL26_test |   screened_test |
|:----------|:----------------|--------------:|---------------:|---------------:|------------:|-------------:|------------------:|----------------:|
| odd->even | th0.05          |          1.52 |           1.58 |             19 |        1.91 |         1.35 |              1.17 |            1.4  |
| even->odd | th0.05          |          1.58 |           1.52 |             20 |        1.81 |         1.24 |              1.18 |            1.28 |

Own random-entry null p95 of the test-half Sharpe for the h2/k2 SCR cell: even years 0.10, odd years -0.01. The half-sample selected cell (loosest screen, 0.05) and the market-selected book both beat the null by >12x on the held-out years, and the un-selected full ALL26 book also earns 1.17-1.18 on the test halves. So the breakout effect itself is not an artefact of the choice of markets or of the three patterns. (Caveat: the 2013-22 halves are interleaved years, so serial dependence leaks across them; this is a weaker test than forward data.)

## (d) Block bootstrap of the uplift
4-week circular blocks, 5,000 draws, pair window, 20% share, capped k: all-in uplift 0.05, median 0.05, 90% CI [-0.05, 0.14] (includes zero).

## (e) False-discovery accounting
Cells examined by this worker: B2D 36, B2M 36, B3 48, B5 9, B6 128, X1 8, X2 32, X3 12, X4 3, X5 16 = 328, plus 12 in this plan = 340. Chance-pass rate: of 210 random-entry null replicates of the selected cell (same trade count per instrument per year, same hold/stop, random side), scaled with the same clean-vol and worst-week-cap rule, 0 reach +0.10 on clean, H1 and H2 simultaneously at 20% share (0.0%; 95% upper bound 3/210 = 1.4%) and 0 also on all-in. Null mean uplift -0.05/-0.03/-0.04, p95 0.06/0.22/0.14. Expected false passes over 340 cells <= 340 x 0.014 = 4.9 (upper bound); point estimate 0. Actual FOUND in this worker's output: 0.

## Verdict
Not FOUND, not FOUND-PENDING. X1 is a real standalone breakout effect (split-sample and null both support it) that raises the pair only marginally and inconsistently once the sleeve is clean-selected and size-capped. Next evidence: new weeks via the weekly extension (re-score the original X1_h1_k2_SCR and this cell).

DONE X1-REP
