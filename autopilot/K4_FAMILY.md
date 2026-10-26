# K4 FAMILY - one-page evidence summary (worker I, 2026-10-17)

**What it is.** ONE signal: a daily walk-forward LightGBM (depth 2, 150 trees, retrained quarterly from 2016, target = next-day sign) on ES, NQ, RTY, YM with price, VIX-state (VIX percentile, VIX/VIX3M, VVIX, 5-day VIX change), COT and calendar features. Trade long when p >= 0.58, entry and exit at the 16:16 ET price, one ADR-dollar of risk per signal. Every "variant" below reuses the same features, the same panel and the same 2023-26 pair window. Promotion of any one counts for the family; evidence is not additive.

| Test (report) | Result | Reads as |
|---|---|---|
| K4 / K4v2 (REPORT_K4, K4V2) | additive 20% +0.18/+0.39/+0.19; drift-matched null p95 0.62 vs 1.43; alpha Sharpe 1.22 CI [0.41,1.91]; plateau 7/9; replication 1 of 3 | passes 9/9 gates; FOUND-PENDING |
| Selection-aware rank (K4V2) | real best beats 55% of 100 random-entry replicates of the 32-cell selection | clean winner not unusual vs best-of-grid noise |
| ERA walk-forward 2016-22 (all variants) | weekly Sharpe 0.27-0.42 net of cost, positive | modern-era-compatible, not new-regime-only |
| Beta-neutral vs ES (E7b, E7c) | alpha Sharpe -0.36 / -0.60, uplift negative | edge is index-direction timing, dies when ES-hedged |
| Shorts (E7a, RX7P) | short leg Sharpe -0.08 on 58 trades; long-short = long-only | long leg only |
| Equal-exposure buy-and-hold (RW1) | K4 Sharpe 1.43 vs 0.69, but paired CI of the difference [-0.24,+1.72] | timing skill plausible, not proven (bull sample) |
| Which features (RW2) | PRICE+VIX +0.276 vs FULL +0.287; PRICE alone +0.090; COT +0.008; calendar +0.111 | the VIX-state block carries it |
| Simple VIX rules, no ML (RY1) | best rule Sharpe 0.65 = buy-and-hold 0.65; CI [-0.73,+0.73] | the edge is NOT a simple VIX rule |
| Model class (RW3) | logit / ridge: clean +0.01, null not beaten | nonlinear interaction, tree-specific |
| Hold period (RW4) | 2-day and persistent holds worse than 1-day | 1-day |
| Retrain cadence (RY10) | monthly/quarterly/semiannual/annual all pass 6 gates; clean +0.22..+0.33 | not dependent on frequent retraining |
| Ensembles (RX5, RY6) | 5-seed mean: +0.28/+0.20/+0.33 (seeds 0-4); fresh seeds 10-14: +0.19/+0.24/+0.20, plateau 62% (needs 75%) | seed variance +-0.08 is real |
| Extended VIX-family features (RW12, RW12P) | +0.26/+0.65/+0.40 but plateau 22% across seeds, replication 1/3 | higher point estimate, less stable |
| Per-instrument (RY2) | each of ES/NQ/RTY/YM alone: Sharpe 1.1-1.7 vs own B&H 0.2-0.85; RW1 CI includes 0 (RTY only clears the CI) | no single instrument carries it; ES strongest |
| Other index (RY3, NKD) | rule 0.67 and US-trained transfer 1.06 vs NKD B&H 1.01 | no transfer to Nikkei (DAX not on disk) |
| Regime-conditional (RY4) | trade only when pair 8-13-week P&L is bad: 42 trades, null rank 0.37, wd corr +0.05 | not a hedge |
| Pair modulators (L2, RW5, RX10, RY8) | RW5 +0.25/+1.06/+0.62 LEAD (plateau and H0 fail); threshold agreement tilt NO; VIX-rule modulator NO | modulation carries K4's beta, not independent |
| Limit-order sleeve (RY5, FVG E1) | K4 scaling of E1 changes the all-in uplift by +0.008 [-0.02,+0.04] | neither helps nor hurts |
| Continuous sizing (RY9) | passes 7/7 gates, but 93% exposure and RW1 CI [-0.04,+1.03] | mostly scaled beta |
| Other asset classes (K8, L10) | GC/CL/ZN/6E/6J and Treasuries: NO | equity-index specific |
| Family-wise accounting (RY7) | 145 trial cells, mean correlation 0.44, effective independent trials ~3.9; DSR K4v2 0.64 (N=145) to 0.99 (N_eff=4), RX5 0.92 to 1.00, RW12P 0.97 to 1.00; PBO 0.22-0.47 | honest N lies between; PBO moderate |

**Replication status.** H0 (2023-02..07) is +0.02..+0.09 in every variant against 0.10-0.17 needed (fails); alternating-month select/read passes; a model trained on NQ+ES and traded on RTY+YM gives +0.08..+0.13 (just below the bar); newest-weeks replication is not possible (data ends 2026-10-13). Forward lines: K4V2, RW12P, RW5, RX5 in forward/PRED_EXTRA.json (predicted weekly uplift +$0.9k to +$5k with 90% CIs).

**Dependencies / caveats.** (1) One sample: the pair window is a rising market (always-long Sharpe 0.65) so beta timing and skill are separated only by the drift-matched null, the beta regression and the (inconclusive) RW1 test. (2) Features chosen after K4 (RW12, RX5 seeds) are not independent. (3) Retraining randomness moves the headline uplift by +-0.08. (4) Execution is simple (daily signal file, 16:16 ET market orders) but margin at 30% share on all four indices is about $172k of assumed initial margin. (5) Nothing here has seen a week after 2026-10-13.

**Verdict.** Family status: LEAD / FOUND-PENDING-REPLICATION as ONE lead (best vehicle RX5; most stable plateau K4 itself). Needs: forward weeks (forward/PRED_EXTRA.json), an independent market (not found: NKD no, other asset classes no), or the cross-instrument NQ+ES-to-RTY+YM bar. Do not count the 8 variants as 8 finds.
