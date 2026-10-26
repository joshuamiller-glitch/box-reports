# REPORT Q20-ENS - equal-risk ensemble of the prior-close-distance fade family across ES, RTY, YM, GC (with CL, NQ controls)

**Verdict: NO. FOUND 0.** The Q20 RTY lead does not generalise as a family: the 24-cell ensemble (5/15-minute bars, fade at 0.5/0.75/1.0 x ADR20 from the prior trading day's close, holds 60/120/180/240 minutes, day session, no stop) has negative clean-span uplift on ES (-0.14), YM (+0.02), GC (-0.19), CL (-0.21), NQ (-0.07), +0.12 on RTY, and the four-market combined ensemble has additive uplift at 20% share of -0.03 / +0.21 / +0.34 on clean / H1 / H2 (clean fails the +0.10 gate; all-in +0.10; 2x slippage +0.04; bootstrap lower bound -0.05). The cross-market positives of the single RTY cell (ES +0.15, YM +0.12, GC +0.16) came from one parameter choice and one threshold; averaged over the neighbourhood they disappear in the clean span.

Pre-registered in PREREG_AUTOPILOT.md ('Q20-ENS') before the run; contaminated by design (the RTY cell's three spans were read in Q20). Fill model: next 1-minute open, 1 tick/side, $4.36 per contract RT, time exit, no stop; each cell scaled to unit clean weekly sigma, averaged, vol-matched to the pair's clean weekly sigma; baseline pair B.Cfg(wk_floor=8, wk_loss_pb=None).

| ensemble | standalone Sharpe clean / H1 / H2 | uplift@20% clean / H1 / H2 | all-in | wd corr | 2x-slip all-in | alt months odd / even | bootstrap lo @20% |
|---|---|---|---|---|---|---|---|
| ES | -0.87 / 0.16 / 0.20 | -0.14 / -0.25 / +0.14 | -0.07 | -0.26 | -0.17 | +0.02 / -0.24 | -0.31 |
| RTY | 0.86 / 0.15 / 2.07 | +0.12 / -0.05 / +0.67 | +0.21 | -0.62 | +0.16 | +0.22 / +0.13 | -0.00 |
| YM | -0.16 / 0.33 / 0.58 | +0.02 / -0.11 / +0.05 | +0.03 | -0.17 | -0.01 | -0.02 / +0.03 | -0.19 |
| GC | -1.11 / 1.63 / 0.75 | -0.19 / +0.70 / +0.11 | +0.03 | +0.08 | -0.02 | +0.18 / -0.16 | -0.27 |
| CL (control) | -0.98 / -0.94 / 1.00 | -0.21 / -0.06 / +0.23 | -0.08 | -0.20 | -0.18 | -0.10 / -0.17 | -0.32 |
| NQ (control) | -0.56 / -1.55 / 0.64 | -0.07 / -0.46 / +0.11 | -0.07 | -0.29 | -0.09 | +0.24 / -0.36 | -0.30 |
| COMBINED ES+RTY+YM+GC | -0.50 / 1.17 / 1.47 | -0.03 / +0.21 / +0.34 | +0.10 | -0.39 | +0.04 | +0.16 / -0.04 | -0.05 |

Combined ensemble uplift by share (clean / H1 / H2): 10% -0.01/+0.13/+0.19; 20% -0.03/+0.21/+0.34; 30% -0.05/+0.25/+0.47; 50% -0.12/+0.23/+0.61. Timing-destroyed ensemble null p95 -1.31 (rank 1.00; lenient because independent random books diversify). Worst-decile correlation of the combined ensemble -0.39 (hedge-like, 17 weeks; the circular-shift null would apply to a hedge claim and is not run since the clean gate fails).

Sizing (20% share, contracts per cell slot / maximum if all 24 slots held at once): ES 0.66 / 17, RTY 0.96 / 25, YM 0.80 / 21, GC 0.51 / 13; worst single trades per one contract in the Q20 RTY cell: -$3.3k.

Reading: H2 is positive for every ensemble (gold/index/small-cap moves away from the prior close revert in 2026) and H1 for GC only; clean is the span that the RTY cell was selected on and the family is flat to negative there. The family-level evidence is a regime-specific H2 reversion effect, not a stable structure. ERA flags for the underlying cells: RTY cell positive pre-2023, others see REPORT_Q20.md.

Code ap_q20e.py, ap_q20_ens.py (code/census/night_ins); data outputs/autopilot/l/q20e/.

DONE Q20_ENS
