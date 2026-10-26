# REPORT B19 - DYNAMIC ST/HM BOOK TILT (Q-5)

**Verdict: NO. FOUND 0, LEAD 0.** Best clean cell (L8 pnl reverse-tilt, 12/4..4/12) lifts clean weekly Sharpe +0.65 (1.46 -> 2.11) but H1 -0.16, H2 -1.06; all 3 advanced cells fail gate 1 (H1/H2), the matched random-tilt null (clean only beats it), bootstrap CI (all-in lo -0.26..-0.49), plateau and 2x slippage. Runtime 139 s selection + 4710 s gates (4 workers, shared box). Fill model: b11_nt8 corrected NT8-faithful engine, 1 tick/side + $34.88 per 8 lots (2x slippage = 1.0 pt RT), ET clock, $700k; baseline B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (reproduced 1.46/2.83/2.30).

## What was run (pre-registered in PREREG_AUTOPILOT.md 'B19 BOOK-TILT' before the first run)
- Weekly causal tilt of ST:HM contracts at constant 16 total, from the trailing L=8 or 13 weeks of the shadow 8/8 per-book weekly P&L (P&L or Sharpe metric), momentum (tilt to the recently better book) or reverse, mode B2/B4 (binary +-2/+-4 contracts, i.e. up to 12/4..4/12) or P4 (proportional by t-stat). 24 cells; selection on clean only (eligible = clean uplift >= +0.10; top 3 advance); H1/H2 read once for those 3.
- Finding in selection: all 12 momentum cells lose (-0.11 to -0.84 clean Sharpe); 7 reverse cells exceed +0.10. Reverse = tilt toward the book that did WORSE recently (books' edge mean-reverts at 8-13 weeks), consistent with S5 rho -1, but it did not hold out of sample (H2 uplift -1.06/-1.15/-0.49).
- Interaction note: sizes change how often the dollar day/week rules fire, so the surface is nonlinear (same jaggedness as D1 F3).

## Gate summary (3 advanced cells)
| gate | L8_pnl_rev_B4 | L13_sharpe_rev_B4 | L8_pnl_rev_P4 |
|---|---|---|---|
| 1 uplift >= +0.10 clean/H1/H2 | no (+0.65/-0.16/-1.06) | no (+0.55/-0.10/-1.15) | no (+0.54/-0.04/-0.49) |
| 1b vs B.Cfg() | no (H2 -0.24) | no (H2 -0.29) | yes (+0.43/+0.51/+0.22) |
| 2 worst week not worse | no (clean -85k vs -82k) | no | yes |
| 3 random-tilt null p95 (clean,H1,H2,all) | clean yes, H1/H2/all no | clean yes, others no | clean yes, others no |
| 4 bootstrap lo>0 (all-in) | no [-0.37,+0.68] | no [-0.49,+0.61] | no [-0.26,+0.72] |
| 5 plateau | no | no | no |
| 6 2x slippage | no | no | no |
| 7 insurance / NT8 spec | reported below | | |

Comparison with static D1 F3 split and static 8/8: static 4:12 all-in Sharpe 2.02 (clean 1.39, H1 3.31, H2 2.86) and 5:11 2.06 beat the dynamic cells in H1/H2 because they simply overweight HM which out-earned ST in H1/H2; the dynamic reverse-tilt does the opposite in those spans (tilts to ST after ST's bad stretch) and loses. The dynamic cells have lower max DD all-in only for L8_pnl_rev_B4 (270k vs 280k); static 4:12 DD 480k. Neither static nor dynamic tilt clears the gates; the static HM-heavy lead from D1 F3 stays a hindsight regime tilt.

Executability: weekly contract-quantity change per book set from realised per-book P&L (DualStrat per-book quantity parameter, integer contracts, 16 total, margin unchanged). Moot: not FOUND. No correlation gate for a re-weighting; worst-decile-week correlation with baseline reported per cell.

## Selection (clean only, 24 cells)
| cell | clean Sharpe | clean uplift | eligible |
|---|---|---|---|
| L8_pnl_rev_B4 | 2.11 | +0.65 | True |
| L13_sharpe_rev_B4 | 2.01 | +0.55 | True |
| L8_pnl_rev_P4 | 2.00 | +0.54 | True |
| L8_sharpe_rev_B4 | 1.81 | +0.35 | True |
| L13_pnl_rev_B4 | 1.71 | +0.25 | True |
| L8_sharpe_rev_P4 | 1.66 | +0.20 | True |
| L8_pnl_rev_B2 | 1.64 | +0.18 | True |
| L13_pnl_rev_P4 | 1.48 | +0.02 | False |
| L13_sharpe_rev_B2 | 1.48 | +0.02 | False |
| L13_sharpe_rev_P4 | 1.37 | -0.09 | False |
| L8_sharpe_rev_B2 | 1.36 | -0.10 | False |
| L8_sharpe_mom_P4 | 1.35 | -0.11 | False |
| L13_pnl_rev_B2 | 1.33 | -0.13 | False |
| L13_pnl_mom_B2 | 1.24 | -0.22 | False |
| L8_sharpe_mom_B2 | 1.20 | -0.26 | False |
| L8_pnl_mom_P4 | 1.18 | -0.28 | False |
| L13_sharpe_mom_P4 | 1.16 | -0.30 | False |
| L13_sharpe_mom_B2 | 1.08 | -0.38 | False |
| L13_pnl_mom_P4 | 1.08 | -0.38 | False |
| L13_pnl_mom_B4 | 1.08 | -0.38 | False |
| L8_sharpe_mom_B4 | 0.97 | -0.49 | False |
| L8_pnl_mom_B2 | 0.91 | -0.55 | False |
| L13_sharpe_mom_B4 | 0.78 | -0.68 | False |
| L8_pnl_mom_B4 | 0.62 | -0.84 | False |

## Advanced cells (H1/H2 read once)

### L8_pnl_rev_B4
- Tilt: tau mean|.|=3.83 contracts; share of weeks tilted to HM 0.41, to ST 0.55.
- Weekly Sharpe cand / base / uplift: clean 2.11 / 1.46 / +0.65; H1 2.67 / 2.83 / -0.16; H2 1.24 / 2.30 / -1.06; all 2.01 / 1.86 / +0.15
- Uplift vs B.Cfg() pair: clean +0.68; H1 +0.32; H2 -0.24; all +0.42
- Random-tilt null (200 sims of the cell's own tilt sequence permuted across weeks) p95 Sharpe / share of draws >= real: clean 1.78 / 0.01; H1 3.80 / 0.49; H2 2.82 / 0.75; all 2.06 / 0.08
- Bootstrap 90% CI of all-in Sharpe uplift: [-0.37, +0.68]. Circular-shift null (100) share of draws >= real Sharpe (reported): clean 0.00; H1 0.48; H2 0.74; all 0.03
- Plateau neighbours (L x0.75, L x1.25, tilt x0.75, tilt x1.25) all-in uplift: +0.16, -0.10, +0.10, +0.07 vs 75% of +0.15
- 2x slippage uplift: clean +0.68; H1 -0.34; H2 -1.18; all +0.11
- Worst week cand / base: clean -85k / -82k; H1 -78k / -78k; H2 -79k / -83k; all -85k / -83k; correlation with baseline in baseline worst-decile weeks +0.33

| span | cvar5 | cvar10 | maxdd | worst_week | sortino | sharpe | mar | neg_wk |
|---|---|---|---|---|---|---|---|---|
| clean cand | -80,328 | -78,874 | 270,439 | -85,039 | 4.35 | 2.11 | 7.82 | 44.76 |
| clean base | -78,736 | -78,009 | 280,110 | -81,874 | 2.78 | 1.46 | 4.75 | 42.86 |
| H1 cand | -77,665 | -77,518 | 157,483 | -77,837 | 5.23 | 2.67 | 3.85 | 35.71 |
| H1 base | -77,610 | -66,030 | 151,713 | -78,287 | 6.09 | 2.83 | 3.91 | 39.29 |
| H2 cand | -78,932 | -78,633 | 162,308 | -79,060 | 2.25 | 1.24 | 2.71 | 47.22 |
| H2 base | -81,089 | -79,185 | 217,425 | -82,524 | 4.69 | 2.30 | 3.50 | 44.44 |
| all cand | -79,916 | -78,754 | 270,439 | -85,039 | 3.96 | 2.01 | 11.70 | 44.05 |
| all base | -79,220 | -78,243 | 280,110 | -82,524 | 3.63 | 1.86 | 9.59 | 42.86 |
- Net clean/H1/H2/all: 2,116k vs 1,330k, 607k vs 594k, 440k vs 761k, 3,163k vs 2,685k
- Gates:
  - [ ] 1 uplift>=+0.10 clean/H1/H2 vs B.Cfg(wk_floor=8)
  - [ ] 1b same vs B.Cfg() (reported)
  - [ ] 2 worst week not worse (all, clean, H1, H2)
  - [ ] 3 above random-tilt null p95 (all 4 spans)
  - [ ] 4 bootstrap 90% CI lo>0
  - [ ] 5 plateau (>=3 of 4 nbrs keep 75%)
  - [ ] 6 2x slippage uplift>=+0.10 clean/H1/H2
  - [ ] FOUND (all of 1-6)

### L13_sharpe_rev_B4
- Tilt: tau mean|.|=3.73 contracts; share of weeks tilted to HM 0.35, to ST 0.58.
- Weekly Sharpe cand / base / uplift: clean 2.01 / 1.46 / +0.55; H1 2.72 / 2.83 / -0.10; H2 1.15 / 2.30 / -1.15; all 1.92 / 1.86 / +0.06
- Uplift vs B.Cfg() pair: clean +0.81; H1 +0.36; H2 -0.29; all +0.50
- Random-tilt null (200 sims of the cell's own tilt sequence permuted across weeks) p95 Sharpe / share of draws >= real: clean 1.79 / 0.01; H1 3.66 / 0.43; H2 2.48 / 0.76; all 2.01 / 0.10
- Bootstrap 90% CI of all-in Sharpe uplift: [-0.49, +0.61]. Circular-shift null (100) share of draws >= real Sharpe (reported): clean 0.00; H1 0.43; H2 0.70; all 0.03
- Plateau neighbours (L x0.75, L x1.25, tilt x0.75, tilt x1.25) all-in uplift: +0.12, -0.13, +0.16, -0.08 vs 75% of +0.06
- 2x slippage uplift: clean +0.54; H1 -0.27; H2 -1.06; all +0.06
- Worst week cand / base: clean -85k / -82k; H1 -78k / -78k; H2 -79k / -83k; all -85k / -83k; correlation with baseline in baseline worst-decile weeks +0.29

| span | cvar5 | cvar10 | maxdd | worst_week | sortino | sharpe | mar | neg_wk |
|---|---|---|---|---|---|---|---|---|
| clean cand | -79,599 | -78,494 | 302,334 | -85,039 | 4.06 | 2.01 | 6.38 | 43.81 |
| clean base | -78,736 | -78,009 | 280,110 | -81,874 | 2.78 | 1.46 | 4.75 | 42.86 |
| H1 cand | -77,665 | -77,518 | 157,483 | -77,837 | 5.36 | 2.72 | 3.91 | 35.71 |
| H1 base | -77,610 | -66,030 | 151,713 | -78,287 | 6.09 | 2.83 | 3.91 | 39.29 |
| H2 cand | -78,902 | -78,618 | 218,098 | -78,998 | 2.09 | 1.15 | 1.93 | 47.22 |
| H2 base | -81,089 | -79,185 | 217,425 | -82,524 | 4.69 | 2.30 | 3.50 | 44.44 |
| all cand | -79,381 | -78,494 | 302,334 | -85,039 | 3.74 | 1.92 | 9.81 | 43.45 |
| all base | -79,220 | -78,243 | 280,110 | -82,524 | 3.63 | 1.86 | 9.59 | 42.86 |
- Net clean/H1/H2/all: 1,929k vs 1,330k, 616k vs 594k, 421k vs 761k, 2,966k vs 2,685k
- Gates:
  - [ ] 1 uplift>=+0.10 clean/H1/H2 vs B.Cfg(wk_floor=8)
  - [ ] 1b same vs B.Cfg() (reported)
  - [ ] 2 worst week not worse (all, clean, H1, H2)
  - [ ] 3 above random-tilt null p95 (all 4 spans)
  - [ ] 4 bootstrap 90% CI lo>0
  - [ ] 5 plateau (>=3 of 4 nbrs keep 75%)
  - [ ] 6 2x slippage uplift>=+0.10 clean/H1/H2
  - [ ] FOUND (all of 1-6)

### L8_pnl_rev_P4
- Tilt: tau mean|.|=1.67 contracts; share of weeks tilted to HM 0.29, to ST 0.46.
- Weekly Sharpe cand / base / uplift: clean 2.00 / 1.46 / +0.54; H1 2.79 / 2.83 / -0.04; H2 1.80 / 2.30 / -0.49; all 2.07 / 1.86 / +0.21
- Uplift vs B.Cfg() pair: clean +0.43; H1 +0.51; H2 +0.22; all +0.40
- Random-tilt null (200 sims of the cell's own tilt sequence permuted across weeks) p95 Sharpe / share of draws >= real: clean 1.73 / 0.00; H1 3.73 / 0.51; H2 2.65 / 0.58; all 1.99 / 0.03
- Bootstrap 90% CI of all-in Sharpe uplift: [-0.26, +0.72]. Circular-shift null (100) share of draws >= real Sharpe (reported): clean 0.00; H1 0.50; H2 0.67; all 0.03
- Plateau neighbours (L x0.75, L x1.25, tilt x0.75, tilt x1.25) all-in uplift: +0.16, +0.10, +0.05, +0.24 vs 75% of +0.21
- 2x slippage uplift: clean +0.37; H1 -0.28; H2 -0.53; all +0.07
- Worst week cand / base: clean -80k / -82k; H1 -78k / -78k; H2 -80k / -83k; all -80k / -83k; correlation with baseline in baseline worst-decile weeks +0.10

| span | cvar5 | cvar10 | maxdd | worst_week | sortino | sharpe | mar | neg_wk |
|---|---|---|---|---|---|---|---|---|
| clean cand | -78,255 | -77,771 | 313,799 | -79,868 | 3.97 | 2.00 | 5.98 | 40.95 |
| clean base | -78,736 | -78,009 | 280,110 | -81,874 | 2.78 | 1.46 | 4.75 | 42.86 |
| H1 cand | -77,907 | -67,599 | 134,227 | -78,099 | 5.80 | 2.79 | 4.34 | 32.14 |
| H1 base | -77,610 | -66,030 | 151,713 | -78,287 | 6.09 | 2.83 | 3.91 | 39.29 |
| H2 cand | -79,997 | -79,170 | 201,076 | -80,319 | 3.52 | 1.80 | 3.27 | 41.67 |
| H2 base | -81,089 | -79,185 | 217,425 | -82,524 | 4.69 | 2.30 | 3.50 | 44.44 |
| all cand | -78,794 | -78,145 | 313,799 | -80,319 | 4.09 | 2.07 | 9.93 | 39.88 |
| all base | -79,220 | -78,243 | 280,110 | -82,524 | 3.63 | 1.86 | 9.59 | 42.86 |
- Net clean/H1/H2/all: 1,876k vs 1,330k, 582k vs 594k, 658k vs 761k, 3,117k vs 2,685k
- Gates:
  - [ ] 1 uplift>=+0.10 clean/H1/H2 vs B.Cfg(wk_floor=8)
  - [x] 1b same vs B.Cfg() (reported)
  - [x] 2 worst week not worse (all, clean, H1, H2)
  - [ ] 3 above random-tilt null p95 (all 4 spans)
  - [ ] 4 bootstrap 90% CI lo>0
  - [ ] 5 plateau (>=3 of 4 nbrs keep 75%)
  - [ ] 6 2x slippage uplift>=+0.10 clean/H1/H2
  - [ ] FOUND (all of 1-6)

## Static references vs dynamic (constant 16 contracts)
| row | clean Sh | H1 Sh | H2 Sh | all Sh | worst wk all | maxDD all |
|---|---|---|---|---|---|---|
| static 4:12 | 1.39 | 3.31 | 2.86 | 2.02 | -85k | 480k |
| static 3:13 | 1.14 | 3.30 | 2.99 | 1.89 | -86k | 496k |
| static 5:11 | 1.56 | 4.09 | 2.07 | 2.06 | -81k | 327k |
| static 8:8 | 1.46 | 2.83 | 2.30 | 1.86 | -83k | 280k |
| dynamic L8_pnl_rev_B4 | 2.11 | 2.67 | 1.24 | 2.01 | -85k | 270k |
| dynamic L13_sharpe_rev_B4 | 2.01 | 2.72 | 1.15 | 1.92 | -85k | 302k |
| dynamic L8_pnl_rev_P4 | 2.00 | 2.79 | 1.80 | 2.07 | -80k | 314k |


Code: code/census/night_ins/ap_b19_core.py, ap_b19_sel.py, ap_b19_gate.py, ap_b19_rep.py. Data: outputs/autopilot/b19/ (sel.pkl, gate.pkl).

DONE B19
