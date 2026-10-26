# REPORT H11-C - weekly range-compression / weekly-efficiency size tilt of the pair
**Verdict: NO. FOUND 0, LEAD 0. Clean-selected cell WR-HIGH x0.5 (halve size in weeks after an EXPANDED prior week; contra to the compression->expansion mechanism, as in G11-B): clean -0.015 / H1 -0.003 / H2 -0.52; all 8 cells have negative clean uplift (-0.02 to -0.63).** Use-mode M8, horizon H6 (state of the prior 1-9 weeks). Weekly state is low-power (about 100 clean weeks).

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine (13,089 rows) in a clean process; reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Per-entry multipliers renormalised to mean 1 over clean entries (risk-neutral). Features use only bars before the entry bar. Pool of 5, stage 1 about 1 min, stage 2 (200-replicate linear-screen null) about 15 min under box load. Pre-registered in PREREG_AUTOPILOT.md (H11 batch 2) before any state was joined to pair rows. Selection clean-only; H1/H2 read once. Executability: NT8 yes (size by state computed from 1-min bars), whole-lot rounding shown; margin unchanged on average. ERA flag: pair rows start 2023-08, pre-2023 n/a; H0 (2023-02-10..07-31) reported.

## Grid and result
Grid (8): feature {WR = prior-week range / mean of the 8 weeks before it, WER = efficiency ratio of 8 weekly closes} x tail {LOW, HIGH 33%} x a {0.5, 1.5}. Pre-registered mechanism cells (WR-LOW x1.5, WER-HIGH x1.5, WER-LOW x0.5) clean uplift -0.33 / -0.23 / -0.09: the mechanism is rejected on clean. Other clean uplifts: WR-HIGH x1.5 -0.45, WER-LOW x1.5 -0.38, WR-LOW x0.5 -0.33, WER-HIGH x0.5 -0.63.
| span | pair | WR-HIGH x0.5 | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.44 | -0.02 | +0.32 | +0.20 |
| H1 | 2.83 | 2.82 | -0.00 | +0.63 | +0.01 |
| H2 | 2.30 | 1.77 | -0.52 | -0.64 | -0.65 |
| all-in | 1.86 | 1.74 | -0.11 | +0.15 | -0.02 |

## Gate checklist
1 Pre-registered PASS. 2 Clean-only selection PASS. 3 Uplift >= +0.10 each span FAIL (all three below). 4 Worst week: clean -79.1k vs -81.9k pass, H1 -79.1k vs -78.3k FAIL, H2 pass. 5 Null (week labels permuted within year, 200 whole-grid replicates): mean(H1,H2) real -0.29 vs p95 +0.23, rank 0.17 FAIL. 6 Bootstrap CI all-in [-0.61, +0.38] FAIL. 7 Plateau (a-1 scaled x0.75/x1.25, tail 25%/42%): -0.31/-0.16/-0.16/-0.25, 0 of 4 FAIL. 8 2x slip H2 -0.65 FAIL. 9 Replication: H0 +0.78 (one window, holds), alternating months odd-selected +0.05 -> even -0.02; even-selected WER-HIGH x1.5 +0.41 -> odd -0.48: 1 of 3 only. 10 n/a. Overall NO.

## Insurance metrics (weekly)
| span | pair Sharpe | cand Sharpe | uplift | cand Sortino | cand MAR | cand CVaR5 | cand CVaR10 | cand maxDD | cand worst wk (pair) | %neg wk cand (pair) |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.44 | -0.02 | 2.66 | 3.74 | -78.5k | -78.0k | 354k | -79.1k (-81.9k) | 43.8 (42.9) |
| H1 | 2.83 | 2.82 | -0.00 | 6.08 | 5.10 | -78.8k | -78.4k | 133k | -79.1k (-78.3k) | 28.6 (39.3) |
| H2 | 2.30 | 1.77 | -0.52 | 3.85 | 2.41 | -80.2k | -78.8k | 302k | -80.8k (-82.5k) | 47.2 (44.4) |
| all | 1.86 | 1.74 | -0.11 | 3.42 | 7.70 | -79.0k | -78.3k | 354k | -80.8k (-82.5k) | 42.3 (42.9) |
Constant-risk: mean multiplier 1 on clean; maxDD worse clean/all-in (354k vs 300k); insurance NO. The weekly M7 week-floor variant claimed was not run (no M8 signal to condition on); cell D11-H6-M7 stays UNTESTED. Closes D11-H6-M8 NQ. Code ap_h11_feat.py (weekly table outputs/autopilot/h11/weektab.parquet), ap_h11_run.py.

DONE H11-C
