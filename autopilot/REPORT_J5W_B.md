# REPORT J5W_B - expiring halt: skip entries for K min after the latest fast stop once count>=N (no end-of-day truncation)
**Verdict: NO. Selected cell B_T1_K120 (clean-only among 6 cells): weekly Sharpe uplift +0.18 clean / +0.57 H1 / -0.16 H2 (all-in +0.16); failed gates: 3 uplift>=0.10 each span; 5 null rank>=.95 (clean and mean H1H2); 6 bootstrap CI>0; 7 plateau>=75% nbrs; 9a H0 holds (>=50% of clean uplift); 9b alt-month both ways (>=50%).** Variant of H11-B (parent: NO, +0.20/+0.47/+0.19, plateau 0/4, random-break null rank .94, H0 +0.01). Use-mode M7 (M8 for C), horizons H1-H3, NQ pair. Pool of 6, 16-cell family run (4 variants) about 26 min.

## Disclosure and set-up
- H1/H2 were read once for the parent H11-B and I read them when designing the variants: variant H1/H2 results are NON-VIRGIN evidence. Selection used clean 2023-08..2025-07 only; no cell, trigger or gate was changed after seeing H1/H2 (pre-registered in PREREG_AUTOPILOT.md, 'J5W batch', before the first run; code ap_j5w.py, summary ap_j5w_sum.py, outputs outputs/autopilot/j5w/). Replication sources actually available: H0 (2023-02-10..07-31) and alternating months; newest live weeks go to the WATCH updater (code/census/night_ins/watch_n2x10.py); ES/RTY n/a (pair is NQ); pre-2023 n/a (pair rows start 2023-08), ERA FLAG n/a.
- Mechanism: whipsaws are bursts; a K-minute halt captures the burst with no end-of-day truncation. Fill: 1 tick/side + $34.88 per 8-lot RT; 2x slip = SLIP_PT 1.0 in both arms. Baseline B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process reproduced 1.46/2.83/2.30. State uses only trades closed before the entry. NT8: closed-trade day counter plus clock, integer lots (4 of 8 for half size). Executable at NinjaTrader Brokerage via Rithmic; margin unchanged (rule only removes or halves entries).

## Grid (clean / H1 / H2 uplift; share of clean raw entries touched; fired groups)
| cell | clean | H1 | H2 | touched | fired |
|---|---|---|---|---|---|
| B_T1_K60 | +0.17 | +0.33 | -0.32 | 1.9% | 88 |
| B_T1_K120 (selected) | +0.18 | +0.57 | -0.16 | 3.2% | 93 |
| B_T1_K180 | +0.16 | +0.64 | -0.12 | 3.8% | 96 |
| B_T2_K60 | +0.04 | +0.17 | -0.44 | 3.0% | 165 |
| B_T2_K120 | +0.00 | +0.22 | +0.19 | 4.5% | 179 |
| B_T2_K180 | +0.13 | +0.25 | +0.27 | 5.9% | 183 |

## Selected cell, weekly Sharpe
| span | pair | cell | uplift | cell vs B.Cfg()-free 2x slip uplift | net P&L change |
|---|---|---|---|---|---|
| clean | 1.46 | 1.64 | +0.18 | +0.17 | +10.2% |
| H1 | 2.83 | 3.40 | +0.57 | +0.55 | +19.4% |
| H2 | 2.30 | 2.14 | -0.16 | -0.16 | -4.7% |
| all | 1.86 | 2.02 | +0.16 | +0.15 | +8.0% |

## Gate checklist
1 Pre-registered before first run: PASS. 2 Clean-only selection, H1/H2 non-virgin (disclosed): PASS as procedure.
3 Uplift >= +0.10 on clean/H1/H2: FAIL (+0.18/+0.57/-0.16).
4 Worst week not worse: PASS (clean -81,874 vs -81,874; H1 -78,287 vs -78,287; H2 -79,653 vs -82,524).
5 Own matched random null (100 draws, same fired groups, same action, timing destroyed): clean rank 0.84 (null mean +0.08, p95 +0.24), H1 rank 0.99, H2 rank 0.59; mean(H1,H2) real +0.21 vs null mean -0.11 / p95 +0.17 (rank 0.96): FAIL (both ranks must be >= .95).
6 Bootstrap 90% CI of all-in uplift [-0.02, +0.37]: FAIL.
7 Plateau (2 of 6 neighbours keep >= 75% of all-in +0.16; N-1 -0.16, N+1 -0.08, X x0.75 +0.00, X x1.25 +0.14, K x0.75 +0.12, K x1.25 +0.19): FAIL.
8 2x slippage uplift clean +0.17, all-in +0.15: PASS.
9 Replication (H0 +0.06 -> fails; alt-month odd-selected B_T2_K180 +0.10 -> even +0.19, even-selected B_T2_K120 +0.24 -> odd -0.08 -> fails): FAIL. Both needed (only two sources exist).
10 Worst-decile corr: n/a (rule on the pair). 11 NT8-codable: yes.

## Insurance metrics (weekly, cell vs pair)
| span | cell Sharpe (pair) | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week (pair) | %neg wk (pair) |
|---|---|---|---|---|---|---|---|---|
| clean | 1.64 (1.46) | 3.14 | 5.30 | -78.7k | -78.0k | 276k (280k) | -81.9k (-81.9k) | 41.0 (42.9) |
| H1 | 3.40 (2.83) | 7.74 | 4.99 | -77.6k | -66.0k | 142k (152k) | -78.3k (-78.3k) | 35.7 (39.3) |
| H2 | 2.14 (2.30) | 4.20 | 3.34 | -79.2k | -78.5k | 217k (217k) | -79.7k (-82.5k) | 41.7 (44.4) |
| all | 2.02 (1.86) | 3.96 | 10.49 | -78.9k | -78.1k | 276k (280k) | -81.9k (-82.5k) | 40.5 (42.9) |
Constant-risk framing: the rule only removes or halves entries; its net P&L change is in the table above, Sharpe is scale-free, so scaling to the pair's weekly risk leaves the uplift as read. Tails: worst week is the weekly -8R floor in all spans; INSURANCE verdict NO (no CVaR5 or worst-week cut of >= 25%).

## Reading
Removing truncation (expiring halt) leaves a clean gain +0.18 and a large H1 gain but H2 turns negative (-0.16), and mean(H1,H2) ranks .96 against the random-window null only because the null itself is negative on H2; clean rank .84, plateau fails, H0 and alternating months do not hold. Not a time-of-day-neutral confirmation of whipsaw detection.

Closes the J5W-B variant of D11-H1/H2/H3-M7 NQ. Code ap_j5w.py, ap_j5w_sum.py, ap_j5w_rep.py.

DONE J5W_B