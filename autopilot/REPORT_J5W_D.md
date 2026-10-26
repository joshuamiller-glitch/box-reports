# REPORT J5W_D - late-day-truncation control: halt rest of day only if the Nth fast stop exited before 12:00 ET
**Verdict: NO. Selected cell D_T1 (clean-only among 2 cells): weekly Sharpe uplift +0.20 clean / +0.41 H1 / +0.16 H2 (all-in +0.22); failed gates: 5 null rank>=.95 (clean and mean H1H2); 7 plateau>=75% nbrs; 9a H0 holds (>=50% of clean uplift); 9b alt-month both ways (>=50%).** Variant of H11-B (parent: NO, +0.20/+0.47/+0.19, plateau 0/4, random-break null rank .94, H0 +0.01). Use-mode M7 (M8 for C), horizons H1-H3, NQ pair. Pool of 6, 16-cell family run (4 variants) about 26 min.

## Disclosure and set-up
- H1/H2 were read once for the parent H11-B and I read them when designing the variants: variant H1/H2 results are NON-VIRGIN evidence. Selection used clean 2023-08..2025-07 only; no cell, trigger or gate was changed after seeing H1/H2 (pre-registered in PREREG_AUTOPILOT.md, 'J5W batch', before the first run; code ap_j5w.py, summary ap_j5w_sum.py, outputs outputs/autopilot/j5w/). Replication sources actually available: H0 (2023-02-10..07-31) and alternating months; newest live weeks go to the WATCH updater (code/census/night_ins/watch_n2x10.py); ES/RTY n/a (pair is NQ); pre-2023 n/a (pair rows start 2023-08), ERA FLAG n/a.
- Mechanism: if the morning-only trigger keeps the gain and beats a morning-restricted random break, the effect is detection, else truncation. Fill: 1 tick/side + $34.88 per 8-lot RT; 2x slip = SLIP_PT 1.0 in both arms. Baseline B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process reproduced 1.46/2.83/2.30. State uses only trades closed before the entry. NT8: closed-trade day counter plus clock, integer lots (4 of 8 for half size). Executable at NinjaTrader Brokerage via Rithmic; margin unchanged (rule only removes or halves entries).

## Grid (clean / H1 / H2 uplift; share of clean raw entries touched; fired groups)
| cell | clean | H1 | H2 | touched | fired |
|---|---|---|---|---|---|
| D_T1 (selected) | +0.20 | +0.41 | +0.16 | 4.6% | 74 |
| D_T2 | +0.17 | +0.31 | +0.14 | 7.0% | 136 |

## Selected cell, weekly Sharpe
| span | pair | cell | uplift | cell vs B.Cfg()-free 2x slip uplift | net P&L change |
|---|---|---|---|---|---|
| clean | 1.46 | 1.66 | +0.20 | +0.22 | +11.9% |
| H1 | 2.83 | 3.23 | +0.41 | +0.42 | +12.5% |
| H2 | 2.30 | 2.46 | +0.16 | +0.14 | +4.9% |
| all | 1.86 | 2.08 | +0.22 | +0.23 | +10.1% |

## Gate checklist
1 Pre-registered before first run: PASS. 2 Clean-only selection, H1/H2 non-virgin (disclosed): PASS as procedure.
3 Uplift >= +0.10 on clean/H1/H2: PASS (+0.20/+0.41/+0.16).
4 Worst week not worse: PASS (clean -81,874 vs -81,874; H1 -78,287 vs -78,287; H2 -79,653 vs -82,524).
5 Own matched random null (100 draws, same fired groups, same action, timing destroyed): clean rank 0.03 (null mean +0.29, p95 +0.38), H1 rank 0.46, H2 rank 0.90; mean(H1,H2) real +0.28 vs null mean +0.08 / p95 +0.37 (rank 0.87): FAIL (both ranks must be >= .95).
6 Bootstrap 90% CI of all-in uplift [+0.04, +0.45]: PASS.
7 Plateau (2 of 6 neighbours keep >= 75% of all-in +0.22; N-1 +0.10, N+1 -0.02, X x0.75 +0.07, X x1.25 +0.12, cut 11 +0.17, cut 13 +0.22): FAIL.
8 2x slippage uplift clean +0.22, all-in +0.23: PASS.
9 Replication (H0 +0.01 -> fails; alt-month odd-selected D_T1 +0.09 -> even +0.23, even-selected D_T1 +0.23 -> odd +0.09 -> fails): FAIL. Both needed (only two sources exist).
10 Worst-decile corr: n/a (rule on the pair). 11 NT8-codable: yes.

## Insurance metrics (weekly, cell vs pair)
| span | cell Sharpe (pair) | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week (pair) | %neg wk (pair) |
|---|---|---|---|---|---|---|---|---|
| clean | 1.66 (1.46) | 3.19 | 6.01 | -78.7k | -78.0k | 248k (280k) | -81.9k (-81.9k) | 41.0 (42.9) |
| H1 | 3.23 (2.83) | 7.08 | 5.10 | -77.6k | -66.0k | 131k (152k) | -78.3k (-78.3k) | 35.7 (39.3) |
| H2 | 2.46 (2.30) | 5.19 | 3.67 | -78.5k | -77.8k | 217k (217k) | -79.7k (-82.5k) | 41.7 (44.4) |
| all | 2.08 (1.86) | 4.13 | 11.92 | -78.6k | -77.9k | 248k (280k) | -81.9k (-82.5k) | 40.5 (42.9) |
Constant-risk framing: the rule only removes or halves entries; its net P&L change is in the table above, Sharpe is scale-free, so scaling to the pair's weekly risk leaves the uplift as read. Tails: worst week is the weekly -8R floor in all spans; INSURANCE verdict NO (no CVaR5 or worst-week cut of >= 25%).

## Reading (control result)
The morning-only trigger keeps the parent's gain (clean +0.20, 2x-slip +0.22, bootstrap lower bound above zero), but a random break drawn among the same days' morning entries earns clean +0.29 on average (rank .03: the real trigger is BELOW the null). So the late-day truncation channel explains the clean gain; the fast-stop detector adds nothing identifiable over choosing a random morning cut-off. This is the cleanest statement of why H11-B failed its null.

Closes the J5W-D variant of D11-H1/H2/H3-M7 NQ. Code ap_j5w.py, ap_j5w_sum.py, ap_j5w_rep.py.

DONE J5W_D