# REPORT C1-F2 — allocation rule between the live pair and the V5 P1 five-book NQ ensemble
Cycle 1, AUTOPILOT. Pre-registered in `outputs/autopilot/PREREG_AUTOPILOT.md` (C1-F2) before the first run. Runtime 0.8 s (one process; the grid is 18 cells + a 4-shift null). Code `ap_c1_f2_run.py`, `ap_c1_f2_rep.py`; pickle `outputs/autopilot/c1/f2/f2.pkl`.

**Verdict: NO. The rule is not FOUND and is not even a new lead.** A trailing-statistic tilt around the 80/20 pair/ensemble blend does not beat the static blend, and the static blend is the already-known V5 P1 lead (which fails plateau/holdout there).

## Set-up (fill model and costs)
- Pair: live config B.Cfg(wk_floor=8, wk_loss_pb=None), 8/8, computed in a clean process (identical to V5's `pair_xp.npz`, max diff 0.0). Weekly Sharpe clean/H1/H2/all = 1.46 / 2.83 / 2.30 / 1.86. Robustness line vs `B.Cfg()` (1.35/1.65/2.26) below.
- Ensemble: the V5 P1 five cluster representatives (chosen there on clean only), equal clean risk, **rebuilt with 1 tick/side (0.5 pt round trip) via `vec_with_slip`**, the 5R/-2R rule re-applied after slippage. Market entries, 60/60 bracket, no sleeve-level locks, no netting with the pair. The ensemble is scaled to 100% of the pair's clean weekly volatility (`SK`); the 2x-slippage test keeps that position size and changes only P&L.
- Allocation: weekly weight w_t = 0.20·(1 + cap·u_t) on the ensemble, u_t in [-1,1] from a trailing statistic of weeks t-W..t-1 (centred and scaled with **clean-span** median/sd only). Rules: inverse-vol (log of pair/ensemble trailing vol), trailing-corr (-corr), trailing-Sharpe (ensemble minus pair). W in {13,26,52}, cap in {0.25,0.5} = 18 cells. Two framings: ADDITIVE (pair 8/8 + w_t·ensemble) and CONSTANT-RISK ((1-w_t)·pair + w_t·ensemble).
- Selection: top cell by clean (additive + constant-risk) Sharpe uplift vs the pair; H1/H2 read once afterwards. All 18 are reported.

## All 18 cells — Sharpe uplift vs the pair (clean-selected, H1/H2 untouched)
Static 80/20 blend (u = 0), for reference: additive +0.19 / +0.50 / +0.32 / +0.27; constant-risk +0.23 / +0.58 / +0.39 / +0.32 (clean / H1 / H2 / all).

| rule | W | cap | add clean | add H1 | add H2 | add all | cr clean | cr H1 | cr H2 | cr all | turnover (mean |dw|/w) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| invvol | 13 | 0.5 | +0.22 | +0.25 | +0.22 | +0.23 | +0.31 | +0.16 | +0.22 | +0.29 | 0.09 |
| corr | 13 | 0.5 | +0.22 | +0.40 | +0.31 | +0.27 | +0.29 | +0.41 | +0.33 | +0.33 | 0.10 |
| invvol | 13 | 0.25 | +0.21 | +0.38 | +0.27 | +0.25 | +0.28 | +0.38 | +0.31 | +0.31 | 0.05 |
| invvol | 26 | 0.5 | +0.20 | +0.36 | +0.22 | +0.24 | +0.27 | +0.25 | +0.29 | +0.28 | 0.05 |
| corr | 13 | 0.25 | +0.21 | +0.45 | +0.32 | +0.27 | +0.26 | +0.51 | +0.37 | +0.33 | 0.05 |
| invvol | 26 | 0.25 | +0.20 | +0.43 | +0.27 | +0.26 | +0.25 | +0.43 | +0.34 | +0.31 | 0.03 |
| corr | 26 | 0.5 | +0.22 | +0.34 | +0.37 | +0.28 | +0.22 | +0.38 | +0.48 | +0.30 | 0.07 |
| corr | 26 | 0.25 | +0.21 | +0.42 | +0.35 | +0.28 | +0.23 | +0.49 | +0.44 | +0.32 | 0.03 |
| corr | 52 | 0.5 | +0.21 | +0.65 | +0.44 | +0.33 | +0.23 | +0.75 | +0.54 | +0.36 | 0.03 |
| corr | 52 | 0.25 | +0.20 | +0.58 | +0.38 | +0.30 | +0.23 | +0.69 | +0.47 | +0.35 | 0.02 |
| invvol | 52 | 0.25 | +0.18 | +0.55 | +0.28 | +0.26 | +0.23 | +0.66 | +0.30 | +0.31 | 0.02 |
| invvol | 52 | 0.5 | +0.17 | +0.61 | +0.23 | +0.25 | +0.22 | +0.73 | +0.22 | +0.29 | 0.04 |
| sharpe | 52 | 0.25 | +0.17 | +0.38 | +0.27 | +0.23 | +0.17 | +0.43 | +0.27 | +0.24 | 0.05 |
| sharpe | 26 | 0.25 | +0.16 | +0.36 | +0.27 | +0.22 | +0.13 | +0.36 | +0.19 | +0.19 | 0.08 |
| sharpe | 13 | 0.25 | +0.15 | +0.39 | +0.32 | +0.23 | +0.10 | +0.43 | +0.28 | +0.20 | 0.07 |
| sharpe | 52 | 0.5 | +0.14 | +0.25 | +0.22 | +0.18 | +0.10 | +0.26 | +0.14 | +0.16 | 0.10 |
| sharpe | 26 | 0.5 | +0.13 | +0.21 | +0.21 | +0.16 | +0.02 | +0.14 | -0.03 | +0.05 | 0.15 |
| sharpe | 13 | 0.5 | +0.11 | +0.27 | +0.31 | +0.18 | -0.03 | +0.28 | +0.15 | +0.07 | 0.14 |

**Selected on clean: invvol, W=13, cap=0.5.**

## Selected cell vs the pair and vs the static blend (additive, share ~20%)
| span | ΔSharpe vs pair | net | worst week | CVaR5 | max DD | ΔSharpe vs STATIC blend |
|---|---|---|---|---|---|---|
| clean | +0.22 | +11.6% | -10.5% | -1.3% | -1.2% | +0.03 |
| H1 | +0.25 | +10.4% | +2.7% | +8.9% | +8.5% | -0.24 |
| H2 | +0.22 | +5.0% | -1.9% | -0.1% | +9.3% | -0.10 |
| all | +0.23 | +9.5% | -9.6% | -0.6% | -1.2% | -0.03 |

Constant-risk version: all-in net -9.0% vs the pair, worst week +12.7%, CVaR5 +18.8%, max DD +20.1%; vs the static constant-risk blend ΔSharpe +0.08 / -0.42 / -0.17 (clean/H1/H2).

The tilt adds Sharpe on clean (+0.03 over the static blend, in the span where it was selected) and **loses to the static blend on H1 (-0.24) and H2 (-0.10)**.

## FOUND gate checklist (selected cell, additive framing)
| gate | result | pass |
|---|---|---|
| 1 pre-registered | yes (PREREG_AUTOPILOT.md C1-F2, before first run) | PASS |
| 2 selection on clean only; H1/H2 read once; UNTOUCHED unread | yes | PASS |
| 3 ΔSharpe >= 0.10 on clean, H1, H2 | +0.22 / +0.25 / +0.22; worst week all-in -9.6% (limit -20%) | PASS (but the same as the static blend, see below) |
| 4 gating null (random tilts = circular shifts of u_t, same distribution/autocorrelation/turnover), p95 on the all-in Sharpe uplift | real +0.23 vs null p95 +0.31, rank 28%; per span (real/p95/rank): clean +0.22/+0.27/79%, H1 +0.25/+0.70/6%, H2 +0.22/+0.43/13% | FAIL |
| 4 bootstrap 90% CI of the all-in Sharpe uplift > 0 (vs pair) | [+0.03, +0.44] (this is the static blend's uplift again); **vs the static blend: [-0.12, +0.05]** | PASS vs pair / FAIL vs static (the incremental value of the rule) |
| 5 plateau (+-25% window and cap; 8 neighbours) keep >= 75% of the uplift on all spans | 38% of neighbours | FAIL |
| 5 survives 2x slippage (additive ΔSharpe, clean/H1/H2) | +0.15 / +0.19 / +0.14 (static blend: +0.12 / +0.42 / +0.22) | PASS for the blend; adds nothing over it |
| 6 worst-decile correlation of the ensemble contribution with the pair (17 worst weeks) | -0.02 (all-weeks corr -0.22) | PASS |
| 7 executable spec | needs a NEW NT8 NQ 5-minute strategy (5 books, market entries, 60/60 bracket, 18:05-16:40 ET) plus a weekly sizing script that reads trailing weekly P&L of both and sets the ensemble contract count; the pair itself is unchanged. NinjaTrader Brokerage: yes (NQ futures). Margin: ~$22k/NQ overnight assumed, ~3-4 NQ per book at 20% share. | spec only |

Other readings: 26-week rolling Sharpe of the rule vs the pair >= pair in 80% of windows (this is again the blend's effect). Weight path mean 0.193, range [0.100, 0.300] around 0.20.

## Robustness line vs the other pair definition B.Cfg() (1.35/1.65/2.26)
Pair Sharpe clean/H1/H2/all = 1.35 / 1.65 / 2.26 / 1.61. Selected additive uplift vs it: +0.22 / +0.25 / +0.20 / +0.22 (the ensemble dollars are added to the B.Cfg() pair series; no re-simulation of locks). Same conclusion: the gain is the blend's, not the rule's.

## Reading
- The ensemble is negatively correlated with the pair, so any fixed 20% blend lifts the pair's weekly Sharpe by about +0.2 to +0.5 in every span (static row above). That is the V5 P1 lead; this family asked whether a walk-forward tilt makes it better. It does not: the clean-selected tilt is worse than the static blend on H1 and H2, sits at the 28% percentile of random tilts with the same turnover, and fails plateau.
- Trailing statistics of weekly P&L are too noisy at 13-52 weeks (28 weeks in H1) to forecast the relative contribution; this agrees with D2 E8 (adaptive thresholds NO) and D1 F8 (re-fitting worse than static).
- Not run: rules conditioned on non-P&L regimes (VX etc., see C1-F6), 3 or more books, tilts on individual ensemble members.

## Status
NO / no new lead. CANDIDATES.md unchanged apart from the note that the static blend remains the only live lead from the 5-minute family (V5 P1, fails 2x slippage in its own run at the lowest passing share, plateau, pre-2023 holdout).

DONE C1_F2
