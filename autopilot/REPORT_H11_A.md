# REPORT H11-A - trend-vs-chop (path efficiency / run length) size tilt of the pair
**Verdict: NO. FOUND 0, LEAD 0. All 8 cells have NEGATIVE clean uplift (best RUN-CUT -0.056 clean; -0.51 H1; -0.10 H2).** Use-mode M8 sizing, horizons H1/H2 (30-60 min of 1-min path before each entry). Mechanism (pre-registered): efficient 30-60 min path = follow-through, chop = whipsaw, so cut size in chop / add in efficient tape.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine (13,089 rows) in a clean process; reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Per-entry multipliers renormalised to mean 1 over clean entries (risk-neutral). Features use only bars before the entry bar. Pool of 5, stage 1 about 1 min, stage 2 (200-replicate linear-screen null) about 15 min under box load. Pre-registered in PREREG_AUTOPILOT.md (H11 batch 2) before any state was joined to pair rows. Selection clean-only; H1/H2 read once. Executability: NT8 yes (size by state computed from 1-min bars), whole-lot rounding shown; margin unchanged on average. ERA flag: pair rows start 2023-08, pre-2023 n/a; H0 (2023-02-10..07-31) reported.

## Grid and result
Grid (8): feature {ER30, ER60, SER60 (side-aligned efficiency), RUN (signed same-direction 5-min step count)} x rule {CUT bottom-30% x0.5, ADD top-30% x1.5}. Clean uplifts: RUN-CUT -0.06, ER60-ADD -0.14, SER60-ADD -0.15, ER60-CUT -0.24, SER60-CUT -0.23, RUN-ADD -0.27, ER30-CUT -0.29, ER30-ADD -0.33. Both mechanism directions lose: the hypothesis that path efficiency at entry predicts the pair's edge is rejected on clean (efficiency at entry is not informative; the pair's flips fire in both states).
| span | pair | RUN-CUT | uplift | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.40 | -0.06 | -0.11 | +0.13 |
| H1 | 2.83 | 2.32 | -0.51 | -0.08 | -0.65 |
| H2 | 2.30 | 2.19 | -0.10 | -0.27 | -0.36 |
| all-in | 1.86 | 1.74 | -0.12 | -0.13 | -0.08 |

## Gate checklist
1 Pre-registered PASS. 2 Clean-only selection PASS. 3 Uplift >= +0.10 each span FAIL (-0.06/-0.51/-0.10). 4 Worst week not worse: clean -79.5k vs -81.9k pass, H1 -79.8k vs -78.3k FAIL, H2 pass. 5 Null (features permuted within year x book x hour, 200 whole-grid replicates, clean-only rule): mean(H1,H2) real +0.015 vs p95 +0.267, rank 0.60 FAIL. 6 Bootstrap 90% CI of all-in uplift [-0.49, +0.23] FAIL. 7 Plateau: tail share 22.5%/37.5% give identical result (RUN is integer valued, edges coincide), scale x0.75/x1.25 -0.09/-0.01 FAIL. 8 2x slippage H1 -0.65, H2 -0.36 FAIL. 9 Replication: H0 -0.24; alternating months odd-selected ER30-CUT +0.04 -> even -0.23, even-selected RUN-ADD +0.31 -> odd -0.08: 0 of 2 FAIL. 10 Worst-decile corr n/a. Overall NO.

## Insurance metrics (weekly)
| span | pair Sharpe | cand Sharpe | uplift | cand Sortino | cand MAR | cand CVaR5 | cand CVaR10 | cand maxDD | cand worst wk (pair) | %neg wk cand (pair) |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.40 | -0.06 | 2.69 | 3.60 | -78.2k | -77.8k | 370k | -79.5k (-81.9k) | 43.8 (42.9) |
| H1 | 2.83 | 2.32 | -0.51 | 4.87 | 3.05 | -78.6k | -75.3k | 175k | -79.8k (-78.3k) | 39.3 (39.3) |
| H2 | 2.30 | 2.19 | -0.10 | 4.88 | 3.52 | -78.4k | -77.8k | 229k | -78.5k (-82.5k) | 41.7 (44.4) |
| all | 1.86 | 1.74 | -0.12 | 3.47 | 7.22 | -78.4k | -77.9k | 370k | -79.8k (-82.5k) | 42.9 (42.9) |
Constant-risk: mean multiplier 1 on clean by construction; maxDD worse (370k vs 300k all-in); insurance verdict NO. Diagnostics (not used for selection): H1/H2 of the other cells swing between +1.16 and -1.73 with no sign pattern. Closes D11-H1/H2-M8 (NQ, efficiency/run-length states only). Code ap_h11_feat.py, ap_h11_run.py; outputs outputs/autopilot/h11/.

DONE H11-A
