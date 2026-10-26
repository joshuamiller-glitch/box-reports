# REPORT K12 - PER-SESSION BRACKETS Globex {45,60,75} x RTH {60,75,90}, live pair
**Verdict: NO. FOUND 0. Every one of the 8 session-bracket cells changes weekly Sharpe by -0.24 to -2.4 on all-in; selected Globex 60 / RTH 90 (the mildest): uplift -0.236 clean / +0.275 H1 / -1.150 H2 (needed +0.10 each); all-in -0.371; bootstrap CI [-0.90, +0.11]; best-of-grid null p95 clean +0.26**

## Set-up and fill model
- Replay: all 13,089 pair rows from their actual market fill on the 1-second bars (ap_g11_c_core.rs machinery, stop tested before target within the same second). Bracket stop = target = width, set by entry time: RTH 09:30-16:00 ET (44% of rows) vs Globex. Control (60,60) reproduces the live rows exactly (0 of 13,089 differ in points) and the account 1.46/2.83/2.30. Rows closed externally by netting / other lot's order / time block (41%) keep their external exit (G11-C convention), so the wider/narrower bracket acts only on rows that exit on their own bracket. Fixed lots; 1 tick/side + $34.88 per 8 lots; 2x slippage SLIP_PT 1.0.
- Grid (8): Globex width {45,60,75} x RTH width {60,75,90}, the 60/60 control excluded. Selection clean-only. Null: session labels permuted across rows within book x year-month, whole 8-cell grid per replicate, 100 draws, linear net swap, best-of-grid statistic. Plateau: each width x0.75 / x1.25 (4 neighbours). Constant-risk framing: risk-scaled lots 60/width.

## Grid, uplift per cell (weekly Sharpe vs the live pair; all spans printed for transparency, only the clean-selected cell was read for H1/H2)
| cell | clean | H1 | H2 | all-in | trades / stop% / target% |
|---|---|---|---|---|---|
| (45, 60) | -1.841 | -1.956 | -3.284 | -2.180 | 7928 / 22 / 37 |
| (45, 75) | -2.026 | -1.351 | -3.843 | -2.304 | 7642 / 21 / 35 |
| (45, 90) | -2.012 | -1.050 | -4.418 | -2.386 | 7425 / 21 / 34 |
| (60, 75) | -0.289 | +0.745 | -0.880 | -0.304 | 7017 / 21 / 36 |
| (60, 90) **(selected)** | -0.236 | +0.275 | -1.150 | -0.371 | 6924 / 21 / 35 |
| (75, 60) | -0.699 | -1.091 | -0.181 | -0.596 | 6331 / 22 / 36 |
| (75, 75) | -0.686 | -0.896 | -0.596 | -0.655 | 6144 / 22 / 35 |
| (75, 90) | -0.356 | -1.181 | -0.653 | -0.526 | 6058 / 21 / 34 |

## Result for the carried cell: (60, 90)
| span | pair | candidate | uplift | 2x slip uplift |
|---|---|---|---|---|
| clean | 1.46 | 1.22 | -0.236 | -0.053 |
| H1 | 2.83 | 3.10 | +0.275 | +0.588 |
| H2 | 2.30 | 1.15 | -1.150 | -0.981 |
| all | 1.86 | 1.48 | -0.371 | -0.171 |

## Gate checklist
- uplift>=0.10 clean/H1/H2: FAIL
- worst week not worse (all-in): FAIL
- own null all-in > p95 (and clean): FAIL
- bootstrap CI lo > 0: FAIL
- plateau >= 75%: FAIL
- 2x slip uplift >= 0.10 each span: FAIL
- alt-month both directions hold: FAIL
- null detail (uplift vs null p95 / rank): clean -0.236 vs +0.259 / 0.00; H1 +0.275 vs +0.197 / 0.96; H2 -1.150 vs +0.407 / 0.01; all -0.371 vs +0.121 / 0.00
- bootstrap 90% CI of all-in uplift: [-0.903, +0.108]
- plateau: 0.00 of 4 neighbours keep >= 75% of the all-in uplift; neighbours: g x0.75 -2.386; g x1.25 -0.526; r x0.75 -0.033; r x1.25 -0.404
- alternating-month split (pre-registered): select (60, 90) (-0.094) reads -0.265 on the other half; select (60, 90) (-0.265) reads -0.094 on the other half
- H0 (2023-02-10..07-31) uplift: -0.427; replications counted (alt-month, H0): 0 of 2 needed (newest live weeks and ES/RTY not available / not applicable for this pair-row family)
- worst-week (candidate vs pair): clean -81.9k vs -81.9k; H1 -77.7k vs -78.3k; H2 -83.4k vs -82.5k; all -83.4k vs -82.5k; weekly corr with pair 0.861 (pair change, no hedge claim; worst-decile corr n/a)

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.22 | 2.27 | 2.33 | -79.1k | -78.5k | 534k | -81.9k | 47.6 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 3.10 | 7.54 | 5.29 | -77.7k | -68.0k | 139k | -77.7k | 42.9 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 1.15 | 2.07 | 1.66 | -81.4k | -79.8k | 261k | -83.4k | 50.0 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 1.48 | 2.80 | 4.53 | -79.5k | -78.7k | 534k | -83.4k | 47.0 |

## Reading
Widening only the RTH bracket (60/90) is the least bad cell and its sign is unstable: +0.27 on H1, -0.24 on clean, -1.15 on H2. Narrowing the Globex bracket to 45 costs -1.8 to -2.4 clean in all three RTH pairings, and widening Globex to 75 costs -0.4 to -0.7: the live 60-pt Globex bracket is a sharp optimum, in line with D2 E6 (single brackets 48..72 all lose to 60) and G11-C (swing stops all lose). Risk-scaled lots (constant-risk framing) for the selected cell: +0.16/+1.14/-1.08 (clean/H1/H2), still not clearing +0.10 on all spans. The best-of-grid null p95 (clean +0.26) shows that a random re-labelling of sessions finds a better cell than the real session split does, i.e. the session split carries no information about where the optimum width is.
Caveat on the null: it uses the linear net swap (fixed lots and locks of the baseline account), which reproduces the account for large changes (cell (45,60): linear -1.75 vs account -1.84 on clean) but not for small ones (selected cell: linear +0.38/-0.04/-0.82 vs account -0.24/+0.28/-1.15), so the null is noisier than the real account run; the verdict does not depend on it (the uplift gate fails first).

## Executability / era / replication
NT8: DualStrat already takes stop/target ticks; a per-session pair of widths would be two parameters switched by clock; not recommended. Era: pair rows start 2023-02 so pre-2023 is n/a (ERA flag n/a); H0 (2023-02..07) is reported above. Replication not met (alt-month split fails, H0 negative). Mechanism does not depend on current structure beyond bracket widths. Files: code/census/night_ins/ap_k12.py, ap_k12_rep.py, ap_k_lib.py; outputs/autopilot/k12/.

DONE K12
