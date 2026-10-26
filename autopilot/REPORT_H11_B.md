# REPORT H11-B - whipsaw detector: halt the rest of the day after N fast stop-outs
**Verdict: NO (closest of the batch; recorded as a watch item, not a LEAD). Selected cell N2_X10_HALT (skip the rest of the label day's entries once 2 pair trades stopped out within 10 minutes of entry): weekly Sharpe uplift +0.20 clean / +0.47 H1 / +0.19 H2 (all >= +0.10), worst week equal on clean and H1, better on H2, bootstrap 90% CI of all-in uplift [+0.06, +0.47]; but plateau 0 of 4, matched random-halt null not beaten (mean(H1,H2) rank 0.94 vs p95 0.365; clean rank 0.38), H0 +0.01, alternating-month 1 of 2.** Use-mode M7 risk rule, horizons H1-H3. 12 cells, 97 fired days in the whole sample, 5.1% of clean raw entries halted; stage 1 + stage 2 + 100-draw null about 17 min under heavy box load, pool of 5.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine in a clean process (reproduced 1.46 / 2.83 / 2.30, all-in 1.86); pass1 with a state hook as in G0a (ap_g0_core.py, new hook in ap_h11_b.py). State uses only trades closed before the entry. Fill 1 tick/side + $34.88 per 8-lot RT; 2x slippage = SLIP_PT 1.0 in baseline and variant. Pre-registered in PREREG_AUTOPILOT.md (H11 batch 2) before the run. Selection clean-only among cells touching >= 5% of clean raw entries; H1/H2 read once. Pair-wide count (both books), pair day = label day. HALT skips, HALF trades 4 lots, so integer-lot executable. NT8: a day counter over closed trades (exit name Stop, life <= X min). ERA: engine rows start 2023-08, pre-2023 n/a; H0 2023-02-10..07-31 reported.
- Overlap with G0a: G0a halted after n consecutive stops of any duration and lost to the random-halt null (late-day truncation helps in clean). H11-B adds stop speed; the same null artefact is visible here (random-break null clean mean +0.23 vs real +0.20).

## Grid (clean uplift of every cell, all cells computed; selected = max among eligible)
N2/X10 HALT +0.20 (selected), N3/X40 HALT +0.18, N2/X10 HALF +0.17, N3/X20 HALT +0.12, N2/X20 HALF +0.08, N2/X40 HALF +0.06, N3/X40 HALF +0.02, N2/X20 HALT -0.02, N2/X40 HALT -0.01, N3/X10 HALT 0.00, N3/X10 HALF -0.01, N3/X20 HALF 0.00. Positive cells cluster at "very fast" (X10) or "large N" (N3 X40) but N2/X20 and N2/X40 HALT are about zero: the response surface is not smooth.

| span | pair | N2_X10_HALT | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.66 | +0.20 | +0.16 | +0.22 |
| H1 | 2.83 | 3.30 | +0.47 | +0.47 | +0.48 |
| H2 | 2.30 | 2.48 | +0.19 | +0.33 | +0.16 |
| all-in | 1.86 | 2.10 | +0.24 | +0.25 | +0.24 |
Net P&L changes +12% clean, +17% H1, +5% H2 (the halt removes net-losing entries; not a pure risk-neutral resize, so constant-risk framing is read from the insurance table).

## Gate checklist
1 Pre-registered PASS. 2 Clean-only selection, H1/H2 once PASS. 3 Uplift >= +0.10 each span PASS (+0.20/+0.47/+0.19). 4 Worst week not worse PASS (clean -81.9k = -81.9k, H1 -78.3k = -78.3k, H2 -79.7k vs -82.5k). 5 Own timing-destroyed null (random break point within each fired day, 100 replicates, same action): clean uplift rank 0.38 (null mean +0.23, p95 +0.35), H1 rank 0.81, H2 rank 0.91 (null mean -0.26), mean(H1,H2) real +0.33 vs p95 +0.365 (rank 0.94) FAIL. 6 Bootstrap CI all-in [+0.06, +0.47] PASS. 7 Plateau (N-1, N+1, X x0.75, X x1.25 all-in uplift): -0.00, +0.01, +0.08, +0.13 vs +0.24, 0 of 4 keep 75% FAIL. 8 2x slippage PASS (+0.22/+0.48/+0.16). 9 Replication (need 2 of): H0 +0.01 (fails); alternating months odd-selected N2_X10_HALT +0.13 -> even +0.22 (holds), even-selected N3_X40_HALT +0.22 -> odd +0.08 (36%, fails); newest weeks not separately available; ES/RTY n/a (pair is NQ) -> 1 of 2 FAIL. 10 Worst-decile corr n/a for a rule on the pair. Overall: NO (fails 5, 7, 9).

## Insurance metrics (weekly)
| span | pair Sharpe | cand Sharpe | uplift | cand Sortino | cand MAR | cand CVaR5 | cand CVaR10 | cand maxDD | cand worst wk (pair) | %neg wk cand (pair) |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.66 | +0.20 | 3.19 | 6.01 | -78.7k | -78.0k | 248k | -81.9k (-81.9k) | 41.9 (42.9) |
| H1 | 2.83 | 3.30 | +0.47 | 7.38 | 5.32 | -77.6k | -66.0k | 131k | -78.3k (-78.3k) | 35.7 (39.3) |
| H2 | 2.30 | 2.48 | +0.19 | 5.23 | 3.69 | -78.5k | -77.8k | 217k | -79.7k (-82.5k) | 41.7 (44.4) |
| all | 1.86 | 2.10 | +0.24 | 4.18 | 12.05 | -78.6k | -77.9k | 248k | -81.9k (-82.5k) | 41.1 (42.9) |
Tails: CVaR5 unchanged (weekly floor -8R dominates the worst weeks), maxDD -11.5% clean/all-in (better), worst week unchanged: INSURANCE verdict NO (not a tail cut; the gain is in mid-distribution weeks). 

## Reading
The only cell family of the batch with a positive sign in all three spans, and the 90% bootstrap excludes zero, but: (i) the response is a sharp point (X10 N2) with a flat or negative neighbourhood, (ii) a random-break halt of the same fired days gets +0.23 on clean (the clean sample rewards truncating late-day entries after bad mornings, the G0a artefact), (iii) H0 shows nothing. Cure/next test if anyone revisits: pre-register N2_X10 and N3_X40 as one "fast-stop halt" family on the NEXT out-of-sample weeks (live) rather than re-running the grid. Closes D11-H1/H2/H3-M7 NQ (fast-stop-count halt). Code ap_h11_b.py, ap_h11_b_sum.py; outputs outputs/autopilot/h11/B_all.pkl, B_summary.pkl.

DONE H11-B
