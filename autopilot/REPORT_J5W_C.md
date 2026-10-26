# REPORT J5W_C - smooth size cut: 0.5x for the next M entries after the trigger, then full size
**Verdict: NO. Selected cell C_T1_M4 (clean-only among 4 cells): weekly Sharpe uplift +0.15 clean / +0.37 H1 / -0.16 H2 (all-in +0.11); failed gates: 3 uplift>=0.10 each span; 5 null rank>=.95 (clean and mean H1H2); 6 bootstrap CI>0; 7 plateau>=75% nbrs; 9a H0 holds (>=50% of clean uplift); 9b alt-month both ways (>=50%).** Variant of H11-B (parent: NO, +0.20/+0.47/+0.19, plateau 0/4, random-break null rank .94, H0 +0.01). Use-mode M7 (M8 for C), horizons H1-H3, NQ pair. Pool of 6, 16-cell family run (4 variants) about 26 min.

## Disclosure and set-up
- H1/H2 were read once for the parent H11-B and I read them when designing the variants: variant H1/H2 results are NON-VIRGIN evidence. Selection used clean 2023-08..2025-07 only; no cell, trigger or gate was changed after seeing H1/H2 (pre-registered in PREREG_AUTOPILOT.md, 'J5W batch', before the first run; code ap_j5w.py, summary ap_j5w_sum.py, outputs outputs/autopilot/j5w/). Replication sources actually available: H0 (2023-02-10..07-31) and alternating months; newest live weeks go to the WATCH updater (code/census/night_ins/watch_n2x10.py); ES/RTY n/a (pair is NQ); pre-2023 n/a (pair rows start 2023-08), ERA FLAG n/a.
- Mechanism: effect may be monotone; a 0.5x cut for M entries is smooth and cannot truncate the day. Fill: 1 tick/side + $34.88 per 8-lot RT; 2x slip = SLIP_PT 1.0 in both arms. Baseline B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process reproduced 1.46/2.83/2.30. State uses only trades closed before the entry. NT8: closed-trade day counter plus clock, integer lots (4 of 8 for half size). Executable at NinjaTrader Brokerage via Rithmic; margin unchanged (rule only removes or halves entries).

## Grid (clean / H1 / H2 uplift; share of clean raw entries touched; fired groups)
| cell | clean | H1 | H2 | touched | fired |
|---|---|---|---|---|---|
| C_T1_M2 | +0.14 | +0.29 | +0.03 | 1.2% | 97 |
| C_T1_M4 (selected) | +0.15 | +0.37 | -0.16 | 2.3% | 97 |
| C_T2_M2 | +0.02 | +0.02 | -0.04 | 2.1% | 185 |
| C_T2_M4 | +0.03 | +0.18 | -0.09 | 3.4% | 185 |

## Selected cell, weekly Sharpe
| span | pair | cell | uplift | cell vs B.Cfg()-free 2x slip uplift | net P&L change |
|---|---|---|---|---|---|
| clean | 1.46 | 1.61 | +0.15 | +0.16 | +8.9% |
| H1 | 2.83 | 3.20 | +0.37 | +0.35 | +10.7% |
| H2 | 2.30 | 2.13 | -0.16 | -0.20 | -4.0% |
| all | 1.86 | 1.97 | +0.11 | +0.10 | +5.6% |

## Gate checklist
1 Pre-registered before first run: PASS. 2 Clean-only selection, H1/H2 non-virgin (disclosed): PASS as procedure.
3 Uplift >= +0.10 on clean/H1/H2: FAIL (+0.15/+0.37/-0.16).
4 Worst week not worse: PASS (clean -81,874 vs -81,874; H1 -78,287 vs -78,287; H2 -79,653 vs -82,524).
5 Own matched random null (100 draws, same fired groups, same action, timing destroyed): clean rank 0.74 (null mean +0.09, p95 +0.24), H1 rank 0.94, H2 rank 0.46; mean(H1,H2) real +0.10 vs null mean -0.08 / p95 +0.12 (rank 0.93): FAIL (both ranks must be >= .95).
6 Bootstrap 90% CI of all-in uplift [-0.06, +0.31]: FAIL.
7 Plateau (1 of 6 neighbours keep >= 75% of all-in +0.11; N-1 -0.13, N+1 -0.08, X x0.75 -0.01, X x1.25 -0.04, M-1 +0.08, M+1 +0.11): FAIL.
8 2x slippage uplift clean +0.16, all-in +0.10: PASS.
9 Replication (H0 +0.00 -> fails; alt-month odd-selected C_T1_M2 +0.08 -> even +0.13, even-selected C_T1_M4 +0.14 -> odd +0.01 -> fails): FAIL. Both needed (only two sources exist).
10 Worst-decile corr: n/a (rule on the pair). 11 NT8-codable: yes.

## Insurance metrics (weekly, cell vs pair)
| span | cell Sharpe (pair) | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week (pair) | %neg wk (pair) |
|---|---|---|---|---|---|---|---|---|
| clean | 1.61 (1.46) | 3.10 | 5.21 | -78.7k | -78.0k | 278k (280k) | -81.9k (-81.9k) | 41.9 (42.9) |
| H1 | 3.20 (2.83) | 7.12 | 4.65 | -77.6k | -66.0k | 141k (152k) | -78.3k (-78.3k) | 35.7 (39.3) |
| H2 | 2.13 (2.30) | 4.20 | 3.36 | -78.9k | -78.2k | 217k (217k) | -79.7k (-82.5k) | 41.7 (44.4) |
| all | 1.97 (1.86) | 3.86 | 10.21 | -78.8k | -78.0k | 278k (280k) | -81.9k (-82.5k) | 41.1 (42.9) |
Constant-risk framing: the rule only removes or halves entries; its net P&L change is in the table above, Sharpe is scale-free, so scaling to the pair's weekly risk leaves the uplift as read. Tails: worst week is the weekly -8R floor in all spans; INSURANCE verdict NO (no CVaR5 or worst-week cut of >= 25%).

## Reading
Smooth 0.5x for the next M entries: +0.15 clean, +0.37 H1, -0.16 H2; weaker than the binary parent, plateau 1 of 6, null not beaten. The sign flip on H2 means the 'monotone effect' premise is not supported.

Closes the J5W-C variant of D11-H1/H2/H3-M7 NQ. Code ap_j5w.py, ap_j5w_sum.py, ap_j5w_rep.py.

DONE J5W_C