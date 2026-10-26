# REPORT G11-C - stop placement relative to the recent swing (1-second re-simulation of the pair's brackets)
**Verdict: NO. FOUND 0, LEAD 0. All 32 cells lose on clean (-0.31 to -4.56 weekly Sharpe; best (60-bar extreme, clamp 45-75, target 60, risk-scaled lots) -0.31 clean / -1.83 H1 / -1.61 H2); bootstrap 90% CI of the all-in uplift [-1.38, -0.25]; every replicate of the stop-permutation null (100) does at least as well as the real best on clean.** 32 cells, stage 1 16 s, stage 2 (100-replicate null, neighbours, slippage) about 3 min, pool of 5. Pre-registered (PREREG_AUTOPILOT.md, G11-C) before the first re-simulation.

## Set-up and fill model
- Replay: all 13,089 pair rows are replayed from their actual market fill (open of the entry bar) on the 1-second bars (d2_e5 machinery: `nt8sim` data, stop tested before target within the same second, target needs touch). Stop distance sd = clamp(distance from the fill to the lowest low (longs) / highest high (shorts) of the last L 1-min bars + 2 pt, lo, hi); target 60 or = sd; sizing fixed lots or risk-scaled (weight 60/sd, fractional lots). Rows whose baseline exit was external (netting, FIFO-mixed order, time block: 41% of rows) keep their original exit price and bar, because their own bracket is not what closed them in the live account; only the 59% own-bracket rows move. This halves the test's power for the stop-distance question and is stated as a limitation, not a defence (the direction and size of the losses are far outside any power argument).
- Control gate: sd = td = 60 reproduces the live corrected-engine rows exactly (0 of 13,089 differ in points; 8 exit-bar differences of 1-30 bars at identical points are overwritten with the baseline bar) and the account 1.46 / 2.83 / 2.30 / 1.86. Account run: d1_core.setup (b11_nt8 reloaded on the new rows) with live rules; 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant.
- Grid: L {15, 30, 60, 120} x clamp {[30,90], [45,75]} x target {60, =sd} x sizing {fixed, risk-scaled} = 32. Own-stop exits are 18-25% and target exits 33-39% of all rows across cells (`g11/stage1_C.csv`).

## Result for the carried cell
| span | pair | cell | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.15 | -0.313 | +0.133 |
| H1 | 2.83 | 0.99 | -1.834 | -1.441 |
| H2 | 2.30 | 0.68 | -1.612 | -1.876 |
| all-in | 1.86 | 1.02 | -0.834 | -0.561 |
Diagnostic only (not used for selection): the H1/H2 uplifts of all 32 cells are negative except two H2 values (+0.92, +0.98) on cells that are -1.6 and -1.3 on H1 (`stage2_C.pkl`). H0 uplift -0.46.

## Gate checklist
1 pre-registered PASS; 2 clean-only selection PASS (process); 3 uplift >= +0.10: FAIL on all three spans; 4 worst week not worse: clean/H2/all pass (-80.9k / -81.4k vs -81.9k / -82.5k), H1 fails (-79.8k vs -78.3k) but moot; 5 own null (stop distances permuted across rows within book x year-month, whole 32-cell grid x 100 replicates, linear net swap with baseline locks): null best-clean mean -0.08, p95 +0.07; real best -0.31 lies BELOW all 100 replicates, i.e. the real swing information is worse than random stops; statistic mean(H1,H2): real -1.72 vs p95 +0.33: FAIL; 6 bootstrap CI [-1.38, -0.25]: FAIL (entirely negative); 7 plateau (L x0.75/x1.25, clamp x0.75/x1.25): all-in -0.62 / -0.82 / -0.54 / -0.85 vs -0.83: neighbours as bad: FAIL (nothing to keep); 8 2x slippage: FAIL (H1 -1.44, H2 -1.88); 9 replication: alternating months selected-on-odd -0.43 -> even -0.45, selected-on-even +0.35 -> odd -0.98: 0 of 2; 10 worst-decile n/a, ERA FLAG not testable (pair rows begin 2023-02); 11 executable in NT8 (swing stop = lookback low/high at entry, limit/stop pair) but not proposed. Overall: NO.

## Insurance metrics (weekly, candidate vs pair)
| span | pair Sharpe | cand Sharpe | cand Sortino | cand MAR | cand CVaR5 | cand maxDD | cand worst wk (pair) | %neg wk (pair) |
|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.15 | 2.12 | 3.00 | -79.8k | 357k | -80.9k (-81.9k) | 48.6 (42.9) |
| H1 | 2.83 | 0.99 | 1.61 | 1.45 | -78.9k | 166k | -79.8k (-78.3k) | 39.3 (39.3) |
| H2 | 2.30 | 0.68 | 1.19 | 1.09 | -80.4k | 226k | -81.4k (-82.5k) | 55.6 (44.4) |
| all | 1.86 | 1.02 | 1.81 | 4.36 | -79.9k | 357k | -81.4k (-82.5k) | 48.8 (42.9) |
Net vs pair: -20% clean, -60% H1, -68% H2, -42% all-in; CVaR5 -0.9%, worst week +1.3%, max DD -28% (worse). Constant-risk framing: risk-scaled lots (60/sd) hold dollars at risk per stop-out constant by design; it does not help (the best cell is risk-scaled but still -0.31). Insurance verdict NO.

## Reading
Every move of the bracket away from stop = target = 60 costs a lot, including the mildest (clamp 45-75 around the 60 default, which only perturbs stops by up to 15 pt) at -0.3 to -0.6: the live 60/60 bracket is sitting at a sharp optimum of the same kind D2 E6 found (single 48..72 brackets 0.4-1.8 all-in Sharpe vs 1.86 for 60), and a swing-based stop adds no information on top of it. With the target at sd (1R:1R) the losses are -1.0 to -4.6: shrinking the target to a short swing throws away the winners. No walk-forward or neighbourhood rescues this. Closes D11-H4-M5 and D00-H1-M5 NQ (swing-stop variant); D00/D11-H0-M5 closed by D2 E5 (execution and target-model variants on the same 1-second engine, 0 of 57 cells). D00/D11-H0-M4 (conditional sub-second execution switch) NOT tested: the L2/queue model (A5) is needed for a credible limit-fill model and is blocked on data. Code ap_g11_c_{core,run}.py; outputs outputs/autopilot/g11/{stage1_C.csv,stage2_C.pkl}.

DONE G11-C
