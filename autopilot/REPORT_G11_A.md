# REPORT G11-A - entry-location conditioning of the live pair's flips (prior-day / overnight / VWAP position as skip or half-size)
**Verdict: NO. FOUND 0, LEAD 0. Clean-selected cell A3-low-half (halve entries whose side-signed position inside the overnight range is in the clean bottom 30%): weekly Sharpe uplift +0.005 clean / +1.14 H1 / -0.41 H2 (needed +0.10 on each); bootstrap 90% CI of the all-in uplift [-0.35, +0.52]; plateau 1 of 2; 2x slippage H2 -0.63.** 16 cells (4 features x 2 tails x skip/half), stage 1 about 2 min, stage 2 (H1/H2 once, neighbours, slippage, 200-replicate null, alternating months) about 4 min, pool of 5. Pre-registered in PREREG_AUTOPILOT.md (section G11-A) before the first feature was joined to pair rows.

## Set-up and fill model
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) from ROWS_corrected_engine via b11_nt8 in a clean process; baseline reproduced 1.46 / 2.83 / 2.30 (all-in 1.86). Per-entry multiplier (0 = skip, 0.5 = half) through B.Cfg.sizefn, so per-book 5R/-2R, day lock and week floor stay fixed in dollars as live. Fill model: unchanged live fills (no new fills simulated), 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant.
- Features (all causal: only 1-min bars with index below the entry bar, entry price = open of the entry bar; truncation test with later bars randomised at 30/60/85% of the series: 0 mismatches over 18,500 compared entries, `g11/causality.txt`): A1 position in the prior-day RTH range (side-signed), A2 room to the prior-day extreme ahead in 60-pt stops, A3 position in the Globex overnight range (side-signed), A4 side-signed distance to session VWAP in ADR20. Tail edges (30th/70th percentile of clean entries) frozen for H1/H2.
- Selection on clean only. Clean uplifts (exact account runs): A3-low-half +0.005 (carried), A3-high-half -0.21, A4-high-half -0.28, A2-high-half -0.30, A1-low-half -0.42, A1-low-skip -0.43, A3-low-skip -0.44 and 9 more between -0.51 and -1.47. All four skip cells at the 30% cut cost 0.4-1.5 Sharpe on clean: cutting 30-35% of the entries removes the winners that fund the day cap and week floor; random skips of that size do the same (B14 saw -0.28 to -0.39 at 10-20%).

## Result for the carried cell A3-low-half (weekly Sharpe)
| span | pair | A3-low-half | uplift | vs B.Cfg() uplift | 2x slip uplift |
|---|---|---|---|---|---|
| clean | 1.46 | 1.46 | +0.005 | -0.059 | +0.276 |
| H1 | 2.83 | 3.97 | +1.142 | +1.229 | +1.162 |
| H2 | 2.30 | 1.89 | -0.408 | -0.109 | -0.630 |
| all-in | 1.86 | 1.92 | +0.067 | +0.144 | +0.186 |
H0 (2023-02-10..07-31) uplift -0.22. The H1 gain is one half-year (28 weeks) and reverses on H2: the cell is non-stationary, not a stable conditioning variable.

## Gate checklist
1. Pre-registered before first run: PASS.
2. Clean-only selection, H1/H2 read once: PASS (process).
3. Uplift >= +0.10 clean / H1 / H2: FAIL (clean +0.005, H2 -0.41).
4. Worst week not worse: clean -79.5k vs -81.9k and H2 -79.4k vs -82.5k pass; H1 -78.6k vs -78.3k is 0.4% worse (inside the 'candidate risk share' allowance only if one reads it loosely): FAIL under the strict reading.
5. Own timing-destroyed null (feature permuted within year x book x ET hour, whole 16-cell grid re-run with the clean-only rule, 200 replicates, linear re-weighting screen): statistic = selected cell's mean(H1,H2) uplift: real +0.18 vs null p95 +0.43 (rank 0.89): FAIL. 99.5% of null replicates reach the real clean uplift at the best-of-16 level.
6. Bootstrap 90% CI of the all-in uplift (3000 weekly draws): [-0.35, +0.52]: FAIL.
7. Plateau (tail share 30% -> 22.5% / 37.5%): all-in +0.104 / -0.091 vs +0.067: FAIL (1 of 2 neighbours keeps 75% of the uplift; the other changes sign).
8. 2x slippage >= +0.10 each span: FAIL (H2 -0.63).
9. Replication (need 2 of): H0 -0.22 (sign flips): no; alternating months (re-select on odd, read on even and reverse): selected on odd A3-low-half +0.095, even read -0.037; selected on even A4-low-half +0.296, odd read -0.52: no; newest weeks: none yet. 0 of 2 available.
10. Worst-decile correlation: not applicable (pair modification). ERA FLAG: not testable (the pair has no rows before 2023-02; features exist only from the bars on disk).
11. Executable: yes (NT8 bar rule: Globex-session high/low since 18:00 ET, side-signed position; halve contracts when below the clean 30th-percentile edge), but not proposed.
Overall: NO.

## Insurance metrics (candidate vs pair, weekly)
| span | pair Sharpe | cand Sharpe | uplift | cand Sortino | cand MAR | cand CVaR5 | cand CVaR10 | cand maxDD | cand worst wk (pair) | %neg wk cand (pair) |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.46 | +0.00 | 2.50 | 4.27 | -78.7k | -78.2k | 281k | -79.5k (-81.9k) | 40.0 (42.9) |
| H1 | 2.83 | 3.97 | +1.14 | 8.87 | 6.48 | -77.8k | -63.7k | 120k | -78.6k (-78.3k) | 28.6 (39.3) |
| H2 | 2.30 | 1.89 | -0.41 | 3.74 | 3.16 | -78.6k | -78.0k | 209k | -79.4k (-82.5k) | 44.4 (44.4) |
| all | 1.86 | 1.92 | +0.07 | 3.52 | 9.40 | -78.7k | -78.1k | 281k | -79.5k (-82.5k) | 39.3 (42.9) |
Net P&L vs pair: -9.9% clean, +31% H1, -13% H2, -1.8% all-in. Constant-risk framing: halving 30% of entries lowers average size (about -15%), so the cell is a risk-reducer, not constant-risk; INSURANCE (>= 25% CVaR5/worst-week or >= 20% max-DD better with cost <= 5%) fails: CVaR5 +0.7%, worst week +3.7%, max-DD -0.2% all-in; the H1-only flag (DD +21%) does not hold on clean or H2. Insurance verdict NO.
## Reading
Position inside the overnight range is the only feature with a non-negative clean uplift, and it is zero; the other three features and all skip cells are clearly negative. Nothing says a flip's quality depends on where it sits relative to prior-day or overnight levels or VWAP once the live locks are in force. The +1.14 on H1 is the kind of single-half-year swing the null reproduces (null p95 of the H1+H2 mean is +0.43).
Closes cells: D11-H1-M4, D11-H5-M4 (daily-level features), D00-H1-M4 (entry-state conditioning only) NQ. Code: code/census/night_ins/ap_g11_{feat,core,run,caus,rep,tab}.py; outputs: outputs/autopilot/g11/ (feat.parquet, stage1_A.csv, stage2_A.pkl).

DONE G11-A
