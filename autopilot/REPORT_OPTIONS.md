# REPORT OPTIONS - options positioning (GEX, zero-gamma, 0DTE share, skew, term slope) as pair size switch / tilt, plus ERA diagnostics
**Verdict: NO. 0 of 22 pre-registered selections pass the Sharpe gate (+0.10 on clean AND H1 AND H2); best single cell fails H2 by -0.28 to -0.64. No FOUND, no LEAD. Part 2: a slow positive-GEX regime goes with the good years (yearly rho +0.90 for NQ-quarterly GEX sign, n=8), but it is one negative year (2022) carrying it, it does not predict weeks (rho 0.04), and ES vs NQ versions disagree on the era test (shift-null p 0.04 vs 0.28).**
Cells: 11 variables x (22 switch + 8 tilt) = 330 cells, 22 selections (one per variable x kind) read on H1/H2. Runtime: scoring 4 s per pass; data build ~1.5 h wall (Databento 504s). Fill model: pair daily P&L from the corrected engine (B.Cfg(wk_floor=8, wk_loss_pb=None), clean process; weekly Sharpe clean/H1/H2/all 1.46/2.83/2.30/1.86 reproduced) scaled by the day's size (cost scaled linearly; 1 tick/side + commission already inside the pair P&L; 2x-slippage not run: no survivor). Spec in PREREG_AUTOPILOT.md 'OPTIONS' (+2 amendments logged before any P&L was scored).

## Data bought (OPTIONS item, cap $450; spent $414.44; program total now 6,932.13 of cap 8,000; ids OPT_* in SPEND.json)
| item | what | $ |
|---|---|---|
| ES.OPT def+stat+ohlcv-1d | GLBX 2019-01..2026-10-14 | 11.88+28.24+17.45 |
| NQ.OPT statistics | GLBX 2019-01.. | 23.70 (NQ.OPT definition + ohlcv-1d were already owned/P4; 2022/23/25 definition gaps re-fetched, 3.00) |
| NQ weekly/EOM families (Q1A-Q3D, QN1-QN4, QNE) def+stat | GLBX 2023-01..2026-10-14 | 97.83 |
| NDXP.OPT / NDX.OPT ohlcv-1d | OPRA 2019-01.. | 109.85 / 37.60 |
| NDX.OPT statistics (OI) | OPRA 2019-01.. (bought, NOT used: monthly/quarterly NDX OI is not in any pre-registered variable) | 84.89 |
Not bought (cap): NDXP statistics ($140), SPX/SPXW anything. Finding: parent NQ.OPT / ES.OPT hold only the quarterly cycle; weeklies and EOM are separate assets (Q1A..., QN1..., QNE, E1A..., EW...), which is why the weekly set was added for NQ (2023+). ES weeklies were not bought, so ES = quarterly only. 504 timeouts were retried; 2-3 weekly months may have been requested twice (<$6, not separately visible). Raw: data/autopilot/opts (+pq/ parquet); features: outputs/autopilot/opt/feat_{NQ,NQA,ES}.parquet, ndx_vol_daily.parquet.

## Construction (all causal)
Settlement (stat 3, ts_ref = trade date t, published ~16:20 ET) and OI (stat 9) are used only if ts_event <= t 21:45 UTC. OI published for t arrives ~21:10 ET (after the pair's next session label opens at 18:00 ET), so the OI in the value of t is OI of t-1 close (conservative; empirically verified on NQ stat records). The value of trade date t sizes the NEXT label only (b11_nt8 label = session from 18:00 ET; Friday value sizes Monday; checked with a unit test). Walk-forward percentile rank u_t is expanding (>= 120 obs), size 1.0 before that.
GEX: Black-76, r = 0, F from put-call parity per (expiry, underlying), IV inverted per strike from the OTM option settlement, dealers LONG calls / SHORT puts (customers sell covered calls, buy protective puts) so GEX = sum_calls G - sum_puts G, G = gamma x F^2 x 0.01 x $20 x OI. zero-gamma: total GEX re-priced on a +-10% spot grid (fixed IV), root nearest spot; zgd = (F - flip)/F, capped +-0.10. 0DTE share = NDXP+NDX contracts expiring on the trade date / all contracts traded (OPRA ohlcv-1d, expiry parsed from the OSI symbol; this is volume of all capacities, not signed). Skew = (IV 25d put - IV 25d call)/ATM IV on the expiry nearest 30 DTE; term = ATM IV near/far (set A: 7 DTE / 35 DTE; set Q: first expiry / next quarterly).
Sets: Q = quarterly/monthly NQ.OPT, 2019-2026 (OI-weighted gamma misses weekly/0DTE flow, so it is a long-dated-gamma proxy); A = Q + all weekly/daily/EOM NQ options, 2023-01+ (about 196 expiries a year, 4,100 instruments a day vs 1,500). ES quarterly analogues used as second-instrument check.
Yearly means (NQ-Q GEX sign): 2019 +0.14, 2020 +0.02, 2021 +0.06, 2022 -0.16, 2023 +0.07, 2024 +0.18, 2025 +0.15, 2026 +0.08 (plausible: dealers short gamma in the 2022 bear). 0DTE share of NDX-family volume: 12% (2019), 24% (2021), 43% (2023), 71% (2025), 76% (2026): secular, monotone.

## Part 1 - size switches and tilts (day-level scaling of the pair; clean 2023-08..2025-07 selection; H1/H2 read once)
Weekly Sharpe uplift vs always-on (gate +0.10 on all three), selected cell per variable x kind (dir +1 = reduce when the variable's rank is low; cell = (q0,q50) switch or k tilt):
| var | kind | cell | mean size | clean | H1 | H2 | all-in | null p95 (clean) | boot p5 (all) | plateau | gates passed of 5* |
|---|---|---|---|---|---|---|---|---|---|---|---|
| gex_sign_Q | switch | +,(.1,.4) | .86 | +0.09 | +0.35 | -0.64 | -0.02 | 0.27 | -0.30 | 0.13 | 1 |
| gex_sign_Q | tilt | -,.25 | .93 | -0.00 | -0.23 | +0.09 | -0.03 | 0.16 | -0.16 | 0.50 | 0 |
| gex_lvl_Q | switch | +,(.1,.4) | .86 | +0.21 | +0.33 | -0.64 | +0.05 | 0.26 | -0.20 | 0.13 | 1 |
| gex_lvl_Q | tilt | +,.25 | 1.05 | +0.01 | +0.21 | -0.22 | -0.00 | 0.13 | -0.11 | 1.00 | 1 |
| zgd_Q | switch | -,(.1,.2) | .73 | +0.16 | -0.55 | -0.71 | -0.16 | 0.37 | -0.59 | 0.63 | 0 |
| zgd_Q | tilt | -,.5 | .87 | +0.04 | -0.47 | -0.05 | -0.08 | 0.28 | -0.33 | 0.50 | 0 |
| skew_Q | switch | +,(0,.2) | .83 | +0.05 | +0.15 | -0.11 | +0.06 | 0.26 | -0.18 | 0.63 | 1 |
| skew_Q | tilt | +,.5 | .86 | +0.02 | -0.19 | +0.19 | +0.08 | 0.23 | -0.15 | 0.50 | 0 |
| term_Q | switch | +,(.1,.3) | .80 | +0.22 | -1.14 | +0.17 | +0.01 | 0.30 | -0.30 | 0.75 | 2 |
| term_Q | tilt | +,.5 | .95 | +0.03 | -0.85 | +0.09 | -0.11 | 0.25 | -0.33 | 0.50 | 0 |
| share0 | switch | +,(0,.2) | .99 | +0.03 | 0.00 | 0.00 | +0.02 | 0.11 | -0.05 | 1.00 | 2 |
| share0 | tilt | +,.75 | 1.62 | +0.03 | +0.08 | +0.02 | +0.05 | 0.16 | -0.08 | 1.00 | 1 |
| gex_sign_A | switch | -,(0,.3) | .85 | +0.10 | -0.26 | -0.05 | +0.01 | 0.26 | -0.24 | 0.25 | 0 |
| gex_sign_A | tilt | -,.25 | 1.00 | -0.00 | -0.21 | +0.18 | +0.00 | 0.16 | -0.12 | 0.50 | 0 |
| gex_lvl_A | switch | +,(.1,.2) | .88 | +0.02 | +0.69 | -0.35 | +0.02 | 0.25 | -0.23 | 0.38 | 1 |
| gex_lvl_A | tilt | -,.25 | 1.01 | +0.02 | -0.26 | +0.10 | -0.01 | 0.13 | -0.11 | 1.00 | 1 |
| zgd_A | switch | -,(0,.3) | .85 | +0.21 | -0.13 | +0.04 | +0.12 | 0.25 | -0.13 | 0.25 | 1 |
| zgd_A | tilt | -,.25 | 1.00 | +0.03 | -0.17 | +0.21 | +0.02 | 0.15 | -0.10 | 1.00 | 1 |
| skew_A | switch | +,(.1,.2) | .86 | +0.35 | +0.26 | -0.54 | +0.14 | 0.33 | -0.18 | 0.88 | 3 |
| skew_A | tilt | +,.25 | 1.04 | -0.00 | +0.21 | -0.16 | +0.00 | 0.16 | -0.13 | 0.50 | 0 |
| term_A | switch | +,(.2,.4) | .69 | +0.54 | +0.13 | -0.28 | +0.30 | 0.35 | -0.18 | 0.63 | 1 |
| term_A | tilt | +,1.0 | .98 | +0.29 | -0.18 | -0.56 | +0.04 | 0.38 | -0.42 | 1.00 | 1 |
*gates counted: Sharpe-3-periods, worst week not worse, own-null p95, bootstrap CI > 0, plateau. (share0 tilt mean size 1.62 = a leverage artefact of a trending variable, not a timing effect.)
No cell clears the Sharpe gate; the two most striking (term_A switch clean +0.54, skew_A switch +0.35/+0.26) turn -0.28/-0.54 in H2 and both beat their clean random-mask p95 (term_A +0.54 vs 0.35; skew_A +0.35 vs 0.33) but the bootstrap p5 of the all-in uplift is -0.18 for both, plateau 0.63 (term_A) / 0.88 (skew_A), alternating-month odd->even +0.17 but even->odd -0.65). Clean "uplifts" are what the best of 30 cells gives by chance (whole-procedure null: mean best-cell clean uplift under block-permuted variables is +0.09..+0.24 for switches).
**False-discovery accounting** (400 block-permuted replicates of the entire select-on-clean + H1/H2 procedure): chance a selection passes the three Sharpe gates = 0.0-7.0% (switches 1.8-7.0%, tilts 1.5-3.2%); expected false Sharpe-gate passes over the 22 selections = 0.69 (0.41 with worst-week not worse). Observed: 0.
Replication (only meaningful for a selection that passes; reported anyway): H0 (2023-02..07, set Q only) uplift of the selected cells ranges -0.32..+0.75 with 17-53% of H0 days affected; alternating-month split same-sign-and-half-uplift both ways: 2 of 22 (term_Q tilt trivially, gex_lvl_A switch with tiny uplift); ES-analogue same cell (20 cells with an ES series): positive in 6, >= half the uplift in 6. ERA 2019-22 (1-min historical engine, selected cell applied walk-forward, reported only): +0.30, +0.00, +0.34, +0.03, +0.17, -0.04, -0.07, +0.11, +0.11, -0.08, 0, -0.09 for the Q/share0 cells (A undefined before 2023): mixed sign, small.
Insurance set (all-in 2023-08..): base net $2.685M, maxDD $280k, CVaR5 -$79k, worst week -$82.5k, Sortino 3.63, MAR 9.6, 42.9% negative weeks. No selected cell is flagged INSURANCE (needs cost >= -5% and CVaR5 or worst-week >= 25% or maxDD >= 20% better): best maxDD gain is gex_lvl_A switch -12% maxDD (247.6k) at -4% net and -0.35 H2 Sharpe. Full table: outputs/autopilot/opt/sel_insurance.csv, selected-cell table sel_Q.csv, sel_A.csv.
Worst-decile correlation: not applicable to a size overlay (the overlay is a multiple of the pair's own P&L; correlation of increment with the pair is +1 by construction on active days).

## Part 2 - ERA diagnostics (descriptive; 16 series, no multiplicity correction; pair GROSS weekly P&L, 1-min engine with live rules, 2019-2026, outputs/autopilot/p1/run_fixed_gross.pkl)
Previous-Friday value vs next-week gross P&L (Spearman), rolling 26-week correlation (mean / share of windows > 0 / range), 26-week-block rho (non-overlapping, n = 15), era AUC (2024-26 vs 2019-23 weeks), circular-shift permutation p of the AUC (all shifts >= 26 weeks; iid-permutation p is anti-conservative with this autocorrelation and not used), yearly Spearman with the pair's yearly gross Sharpe (n = 8; exact permutation p):
| var | weekly rho | roll26 mean | % >0 | roll26 range | block26 rho | AUC | Cohen d | shift p | yearly rho (p) |
|---|---|---|---|---|---|---|---|---|---|
| gex_sign_Q | +0.04 | -0.05 | 36 | -0.46..+0.51 | +0.56 | 0.66 | 0.55 | 0.28 | +0.90 (0.005) |
| gex_lvl_Q | +0.05 | -0.03 | 38 | -0.38..+0.49 | +0.62 | 0.62 | 0.30 | 0.37 | +0.71 (0.058) |
| zgd_Q | +0.03 | -0.05 | 34 | -0.40..+0.51 | +0.52 | 0.65 | 0.61 | 0.31 | +0.88 (0.007) |
| skew_Q | -0.02 | +0.09 | 65 | -0.35..+0.56 | -0.27 | 0.34 | -0.48 | 0.68 | -0.45 (0.27) |
| term_Q | -0.05 | -0.01 | 49 | -0.51..+0.40 | -0.34 | 0.46 | -0.11 | 0.58 | -0.33 (0.43) |
| share0 | +0.15 | +0.04 | 54 | -0.57..+0.60 | +0.66 | 0.99 | 3.66 | 0.000 | +0.71 (0.058) |
| gex_sign_ES | +0.06 | -0.02 | 42 | -0.46..+0.39 | +0.61 | 0.68 | 0.63 | 0.048 | +0.50 (0.22) |
| gex_lvl_ES | +0.06 | -0.00 | 45 | -0.41..+0.44 | +0.40 | 0.67 | 0.46 | 0.047 | +0.55 (0.17) |
| zgd_ES | +0.04 | -0.04 | 40 | -0.47..+0.34 | +0.54 | 0.67 | 0.63 | 0.040 | +0.50 (0.22) |
| skew_ES / term_ES | -0.01 / -0.02 | +0.10 / -0.01 | 69 / 45 | | -0.26 / -0.16 | 0.34 / 0.52 | -0.53 / +0.04 | 0.55 / 0.73 | -0.33 / -0.26 |
| A-set (2023-26 only: 2023 vs 2024-26, 197 wks) | -0.03..+0.09 | -0.06..+0.12 | 35-63 | | | 0.43-0.69 | | skew_A 0.014, others >= 0.23 | not estimable (4 yrs) |
(Rolling-correlation yearly means: gex_sign_Q -0.04, +0.04, -0.02, -0.08, -0.05, -0.07, -0.18, +0.07 for 2019-2026; sign flips, no stable relation; full tables part2_table.csv, part2_roll26.csv.)
Reading:
1. At the year frequency the pair's gross Sharpe tracks the NQ GEX sign / zero-gamma distance (yearly rho +0.90 / +0.88, exact p 0.005 / 0.007; 16 series x 1 test, Bonferroni ~0.08 / 0.11). The pattern is 2022 (dealers short gamma, pair -1.9) vs 2024-26 (long gamma, pair +2.2..+3.1): essentially one bad year and one regime. The same series do NOT separate the eras under the honest shift null for NQ-Q (p 0.28-0.37, AUC 0.62-0.66) and only marginally for ES (p 0.04-0.05); NQ-Q and ES carry the same mechanism and disagree, so the era evidence is fragile. Versus the 21 price statistics of C8-Q1 (best |rho| 0.45, perm p 0.11): the GEX family is the first set that lines up with the pair's yearly Sharpe at nominal significance, but not robustly and not at the weekly level (weekly predictive rho 0.04, rolling 26-week correlation averages -0.05 with a -0.46..+0.51 range).
2. 0DTE share "separates" the eras (AUC 0.99, d 3.7) only because it is a secular trend (12% -> 76%): any trending variable would. It does not predict weeks (rho 0.15) and its walk-forward switch is inert (rank is almost always high).
3. Skew and term slope do not separate eras (|AUC-0.5| <= 0.16, p >= 0.55 in Q/ES), and the weekly-set skew_A p 0.014 compares only 2023 with 2024-26.
4. Consequence for trading: a slow regime flag exists (GEX sign) but sizing the pair on its expanding-rank cannot capture it (cell gex_sign_Q switch: clean +0.09, H1 +0.35, H2 -0.64). A hypothesis to carry (not tested here, not pre-registered): quarterly GEX sign as a monthly/quarterly stand-down flag; would need its own pre-registration and the new live weeks.

## Gates checklist (every one of the 22 selections)
| gate | result |
|---|---|
| pre-registered before first run | yes (PREREG 'OPTIONS', 2026-10-16T16:18Z; 2 amendments before any P&L) |
| selection clean only; H1/H2 once | yes (22 selections; Q/share0 scored first, A after data arrived) |
| Sharpe uplift >= +0.10 on clean, H1, H2 | FAIL for all 22 (0 of 22; best min over periods -0.28 term_A switch) |
| worst week not worse (clean, H1, H2) | passes for 8 of 22 (mostly cells that rarely change size) |
| own mask null p95 / bootstrap CI > 0 | null passes 2 of 22 (skew_A switch, term_A switch); bootstrap p5 > 0: 0 of 22 |
| plateau (+-25%) | passes 8 of 22 |
| 2x slippage | not run (no survivor) |
| wd corr | n/a for size overlay |
| NT8 spec | none (nothing survives) |
| replication (>= 2 of H0 / alt-month / ES / live) | not reached; reported above |
| false-discovery: expected false Sharpe-gate passes 0.69 vs observed 0 | consistent with no effect |

## Part 3 - implementation note (no switch survives; template only)
Nothing to publish. If a variable were ever adopted: variable = rank u_t of term_A / skew_A / GEX; update = once per trading day after the CME option settlement (about 16:20 ET) with OI of the previous close; the execution server would publish `{"asof_trade_date":"2026-10-15","applies_to_label":"2026-10-16","var":"gex_sign_Q","value":0.07,"rank_u":0.31,"size_mult":0.5,"oi_asof":"2026-10-14","source":"GLBX NQ.OPT stat3/stat9","schema":1}` before 18:00 ET and DualStrat would multiply order quantity by size_mult for that label. Feed need: daily Databento (or CME settlement + OI file) pull of NQ.OPT plus the 17 weekly/EOM parents, about 1 minute of compute; not available intraday.

## Caveats
Day-level scaling is an approximation of the locked engine (daily/weekly locks are non-linear); none of the 22 survives so the exact re-run was not needed. Set-Q gamma is quarterly-cycle only; set A has 3.5 years of history (warm-up to mid-2023), so the A switches see fewer clean days with a defined rank. ES weeklies, NDXP/SPX OI and signed (customer-side) volume were not bought; dealer positioning is the usual OI-sign convention, not observed. The IV inversion uses r = 0 and settlement prices (quote-level IV would differ).
Code: code/census/night_ins/ap_opt_{common,dl*,conv,feat,vol,vars,score,sel,fd,ins,part2,base}.py. Data/outputs: outputs/autopilot/opt/.

DONE OPTIONS
