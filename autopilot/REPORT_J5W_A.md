# REPORT J5W_A - book-scoped halt: halt only the book(s) that whipsawed (A1 per-book count, A2 pair count but only contributing books)
**Verdict: NO. Selected cell A2_T2 (clean-only among 4 cells): weekly Sharpe uplift +0.05 clean / +0.30 H1 / +0.35 H2 (all-in +0.15); failed gates: 3 uplift>=0.10 each span; 5 null rank>=.95 (clean and mean H1H2); 6 bootstrap CI>0; 7 plateau>=75% nbrs; 8 2x slip clean>=+0.10 & all>0; 9a H0 holds (>=50% of clean uplift); 9b alt-month both ways (>=50%).** Variant of H11-B (parent: NO, +0.20/+0.47/+0.19, plateau 0/4, random-break null rank .94, H0 +0.01). Use-mode M7 (M8 for C), horizons H1-H3, NQ pair. Pool of 6, 16-cell family run (4 variants) about 26 min.

## Disclosure and set-up
- H1/H2 were read once for the parent H11-B and I read them when designing the variants: variant H1/H2 results are NON-VIRGIN evidence. Selection used clean 2023-08..2025-07 only; no cell, trigger or gate was changed after seeing H1/H2 (pre-registered in PREREG_AUTOPILOT.md, 'J5W batch', before the first run; code ap_j5w.py, summary ap_j5w_sum.py, outputs outputs/autopilot/j5w/). Replication sources actually available: H0 (2023-02-10..07-31) and alternating months; newest live weeks go to the WATCH updater (code/census/night_ins/watch_n2x10.py); ES/RTY n/a (pair is NQ); pre-2023 n/a (pair rows start 2023-08), ERA FLAG n/a.
- Mechanism: a whipsaw may be one book's; halting only that book keeps the other's edge. Fill: 1 tick/side + $34.88 per 8-lot RT; 2x slip = SLIP_PT 1.0 in both arms. Baseline B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process reproduced 1.46/2.83/2.30. State uses only trades closed before the entry. NT8: closed-trade day counter plus clock, integer lots (4 of 8 for half size). Executable at NinjaTrader Brokerage via Rithmic; margin unchanged (rule only removes or halves entries).

## Grid (clean / H1 / H2 uplift; share of clean raw entries touched; fired groups)
| cell | clean | H1 | H2 | touched | fired |
|---|---|---|---|---|---|
| A1_N2X10 | +0.00 | +0.37 | -0.48 | 2.8% | 75 |
| A1_N2X40 | -0.03 | +0.29 | -0.42 | 7.3% | 254 |
| A2_T1 | +0.03 | +0.28 | +0.13 | 4.5% | 124 |
| A2_T2 (selected) | +0.05 | +0.30 | +0.35 | 7.3% | 268 |

## Selected cell, weekly Sharpe
| span | pair | cell | uplift | cell vs B.Cfg()-free 2x slip uplift | net P&L change |
|---|---|---|---|---|---|
| clean | 1.46 | 1.51 | +0.05 | +0.07 | +3.1% |
| H1 | 2.83 | 3.13 | +0.30 | +0.32 | +8.4% |
| H2 | 2.30 | 2.64 | +0.35 | +0.36 | +13.8% |
| all | 1.86 | 2.01 | +0.15 | +0.17 | +7.3% |

## Gate checklist
1 Pre-registered before first run: PASS. 2 Clean-only selection, H1/H2 non-virgin (disclosed): PASS as procedure.
3 Uplift >= +0.10 on clean/H1/H2: FAIL (+0.05/+0.30/+0.35).
4 Worst week not worse: PASS (clean -81,874 vs -81,874; H1 -78,287 vs -78,287; H2 -79,653 vs -82,524).
5 Own matched random null (100 draws, same fired groups, same action, timing destroyed): clean rank 0.51 (null mean +0.04, p95 +0.17), H1 rank 0.42, H2 rank 0.84; mean(H1,H2) real +0.33 vs null mean +0.12 / p95 +0.52 (rank 0.73): FAIL (both ranks must be >= .95).
6 Bootstrap 90% CI of all-in uplift [-0.01, +0.32]: FAIL.
7 Plateau (1 of 4 neighbours keep >= 75% of all-in +0.15; N-1 +0.06, N+1 -0.03, X x0.75 +0.07, X x1.25 +0.17): FAIL.
8 2x slippage uplift clean +0.07, all-in +0.17: FAIL.
9 Replication (H0 -0.00 -> fails; alt-month odd-selected A2_T2 +0.05 -> even +0.18, even-selected A2_T2 +0.18 -> odd +0.05 -> fails): FAIL. Both needed (only two sources exist).
10 Worst-decile corr: n/a (rule on the pair). 11 NT8-codable: yes.

## Insurance metrics (weekly, cell vs pair)
| span | cell Sharpe (pair) | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week (pair) | %neg wk (pair) |
|---|---|---|---|---|---|---|---|---|
| clean | 1.51 (1.46) | 2.87 | 5.06 | -78.8k | -78.0k | 271k (280k) | -81.9k (-81.9k) | 42.9 (42.9) |
| H1 | 3.13 (2.83) | 6.93 | 5.05 | -77.6k | -66.0k | 127k (152k) | -78.3k (-78.3k) | 35.7 (39.3) |
| H2 | 2.64 (2.30) | 5.66 | 3.99 | -78.7k | -78.0k | 217k (217k) | -79.7k (-82.5k) | 36.1 (44.4) |
| all | 2.01 (1.86) | 3.97 | 10.64 | -78.7k | -78.0k | 271k (280k) | -81.9k (-82.5k) | 40.5 (42.9) |
Constant-risk framing: the rule only removes or halves entries; its net P&L change is in the table above, Sharpe is scale-free, so scaling to the pair's weekly risk leaves the uplift as read. Tails: worst week is the weekly -8R floor in all spans; INSURANCE verdict NO (no CVaR5 or worst-week cut of >= 25%).

## Reading
Book scoping removes most of the parent's effect on clean (+0.05 selected, best cell +0.05): the clean gain needs the pair-wide halt. H1/H2 gains (+0.30/+0.35) are non-virgin and the clean/H0/plateau/null do not support them.

Closes the J5W-A variant of D11-H1/H2/H3-M7 NQ. Code ap_j5w.py, ap_j5w_sum.py, ap_j5w_rep.py.

DONE J5W_A