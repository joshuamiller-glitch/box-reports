# DS3_REGIME_STRESS - what the Sunday composite earns if the 2025-26 market state fades (RE-4, 2026-10-31)

Research only; no live/execution change, no credentials, no purchases. Masks capped 20260206 (trade/label dates <= 2026-02-06, depth months <= 2026-01); UNTOUCHED never read. No new strategy search: every dollar series is a stored output of DS3_SUNDAY_DECISION (`l2vast/ds3/out/sundaydecision/res_{1.28,2.45}.pkl`, causal running-max locks, integer half-up min-1 lots, A6 = PB7, live lots, add slip +0.25) re-cut by week and regime state. Regime frame: RE-3 (`recentedge3/regime_*.csv`) rebuilt per day and per week with the bracket ratio added (`out/regimestress/regime_daily.csv`, `regime_weekly2.csv`). Code `l2vast/ds3/code/regimestress/`, outputs `l2vast/ds3/out/regimestress/`.

## PAGE 1 - the table and the sentence

**The composite** = the D6 composite as coded in DS3_SUNDAY_DECISION (d): ER sizer on all six books with running-max locks, 70/30 split (K6 1/1), PE pattern, first-stop cut, no-trade zones, A6 = PB7; stop = the A/B parity mix (odd day-of-month Native 1.28, even join 2.45 = what runs live). 'Level' = the whole stack's $k/wk with the composite on; 'delta' = composite minus the AS-IS stack (market entries, no rules, join 2.45, same live lots) = what the rules add. Pieces are leave-one-out contributions (composite minus composite without the piece; the NY-PM skip and K6 add are the differences described); pieces interact through the locks so they do not add up. Cell = mean $k/wk [95% week-bootstrap CI]; `~` = |mean| < MDE (2.8 x SE of the weekly mean; not distinguishable from zero). Regime terciles are of a STATE INDEX = mean percentile rank of six oriented variables (low book depth, high fill cost, high signals/day, high ES-NQ correlation, low 60-pt-bracket/range, high London share; % realised vol is shown separately), over the 148 weeks 2023-04-03..2026-01-30 that have all variables (the last week 02-02..06 has no depth); T3 = most like 2025-26, T1 = most like 2023-24.

| row | L6M (28 wk) | HOLD (32 wk) | NOW-like state, T3 (n=49) | middle, T2 (n=49) | 2023-24-like state, T1 (n=50) | actual 2023-24 weeks (n=91) | REGIME-NORMALISED to the 2023-24 state mix (all weeks reweighted, ESS 95 (boot p5 76)) | post-stratified to 2023-24 terciles |
|---|---|---|---|---|---|---|---|---|
| **D6 composite, stack level $k/wk** | +42.2 [+26.6, +57.8] | +39.3 [+22.0, +57.3] | +46.9 [+30.8, +62.8] | +11.8 [-1.1, +23.6]~ | +9.4 [-2.0, +20.6]~ | +14.1 [+4.9, +23.4] | +12.4 [+3.5, +20.9] | +13.6 [+5.5, +22.0] |
| **D6 composite, delta vs as-is stack** | +20.4 [+8.6, +32.1] | +17.4 [+6.5, +29.4] | +13.5 [+2.5, +24.6]~ | +8.8 [-2.3, +20.8]~ | +6.1 [-3.0, +15.5]~ | +9.5 [+2.4, +17.2]~ | +9.1 [+1.9, +16.5] | +7.8 [+1.1, +14.7] |
| piece: ER sizer on all six (running-max locks) | +13.4 [+3.0, +23.6]~ | +12.2 [+1.6, +22.7]~ | +10.7 [+1.8, +19.4]~ | +2.1 [-4.7, +9.5]~ | +2.1 [-3.5, +8.0]~ | +2.8 [-2.1, +7.5]~ | +2.5 [-2.3, +7.1] | +2.9 [-1.4, +6.9] |
| piece: PE pattern (P6) | +4.5 [-2.5, +11.8]~ | +4.7 [-2.0, +11.3]~ | +5.0 [-0.3, +10.0]~ | +0.4 [-4.5, +5.6]~ | -1.4 [-5.8, +2.5]~ | -0.9 [-4.1, +2.4]~ | -0.5 [-3.7, +2.6] | -0.2 [-3.1, +2.9] |
| piece: no-trade zones | +5.1 [-1.6, +11.7]~ | +3.1 [-3.9, +9.9]~ | +2.0 [-4.8, +9.0]~ | +4.1 [-3.7, +12.0]~ | +2.8 [-1.8, +7.7]~ | +3.9 [-1.0, +8.9]~ | +3.7 [-0.9, +8.1] | +3.2 [-0.6, +7.7] |
| piece: 70/30 split (K6 1/1, others 70/30) | +4.1 [+0.5, +8.0]~ | +3.9 [+0.7, +7.5]~ | +5.2 [+1.3, +9.3]~ | +0.6 [-1.8, +3.1]~ | -0.4 [-2.3, +1.5]~ | +0.2 [-1.8, +2.4]~ | +0.4 [-1.5, +2.5] | +0.4 [-1.0, +2.0] |
| piece: first-stop cut | -0.3 [-2.6, +1.7]~ | -1.1 [-3.8, +1.3]~ | +0.3 [-1.8, +2.3]~ | -0.6 [-2.2, +0.8]~ | -0.0 [-1.8, +1.4]~ | +0.4 [-0.7, +1.4]~ | +0.4 [-0.8, +1.5] | -0.2 [-1.4, +0.9] |
| piece: K6 add (split vs market) | +0.5 [-1.0, +2.1]~ | +0.2 [-1.2, +1.7]~ | +1.0 [-0.3, +2.3]~ | -0.0 [-0.7, +0.7]~ | -0.1 [-0.8, +0.6]~ | -0.1 [-0.6, +0.4]~ | -0.1 [-0.6, +0.5] | +0.0 [-0.4, +0.5] |
| piece: NY-PM end skip 14:40-15:00 (added) | +0.0 [-0.5, +0.5]~ | -0.0 [-0.5, +0.5]~ | -0.2 [-0.5, +0.2]~ | -0.1 [-0.5, +0.4]~ | +0.1 [-0.2, +0.4]~ | -0.0 [-0.3, +0.2]~ | -0.0 [-0.3, +0.3] | -0.0 [-0.2, +0.2] |
| Sunday CANDIDATE (P6+K6 sizer, K6 mkt, NY-PM skip) delta | +20.3 [+8.1, +32.1] | +17.3 [+6.4, +29.3] | +11.7 [+1.7, +21.8]~ | +7.5 [-2.8, +18.4]~ | +6.5 [-1.7, +15.0]~ | +8.7 [+2.1, +15.6]~ | +8.4 [+1.7, +15.1] | +7.4 [+1.2, +13.8] |
| as-is stack level (no rules) | +21.7 [+5.6, +38.4]~ | +21.9 [+3.5, +40.4]~ | +33.4 [+18.9, +48.7] | +3.0 [-9.7, +15.9]~ | +3.3 [-5.7, +12.7]~ | +4.6 [-3.5, +13.1]~ | | |

**The sentence.** If the 2025-26 state fades back to the 2023-24 one, Sunday's composite earns about **+12.4 [+3.5, +20.9] $k/wk** at stack level (state-matched estimate; the weeks that actually looked like 2023-24 earned +9.4 [-2.0, +20.6]~) against **+42.2 [+26.6, +57.8] now (L6M)**; the part the composite ADDS to the as-is stack is **+20.4 [+8.6, +32.1] now vs +9.1 [+1.9, +16.5] in the 2023-24 mix**, and that added part is inside its MDE in the 2023-24-like state (T1 +6.1 [-3.0, +15.5]~, actual 2023-24 weeks +9.5 [+2.4, +17.2]~) while clearing it in L6M. These are 28-91 correlated weeks, post-hoc pieces, and the range over weighting choices is wider than the CI (section E: from about -13 to +28 $k/wk of delta); read it as "roughly a third of the current level, and an add-on that is not distinguishable from zero".

**Which regime carries the gain.** (1) The LEVEL is a state story: the as-is stack itself earns +33.4 [+18.9, +48.7] now vs +3.3 [-5.7, +12.7]~ in the 2023-24-like weeks; T3 minus T1 level = +37.6 [+17.7, +57.6] $k/wk. (2) The composite's ADD-ON is only mildly state-dependent: T3 minus T1 delta = +7.4 [-7.1, +22.3] (all weeks), +13.3 [-4.4, +31.4] (2024-02 on); the Spearman rho of weekly delta with the state index is +0.10 over all weeks (+0.33 within HOLD, 32 weeks) and about 0 with depth alone. The add-on by calendar half-year is lumpy and NOT monotone in the state: 23H1 +14.7, 23H2 +0.9, 24H1 +17.3, 24H2 -2.9, 25H1 +8.3, 25H2 +21.4 $k/wk (section F), so part of the L6M gain is simply a good half-year. (3) By piece: P6 and the ER sizer carry it (P6 book delta +11.8 [+3.1, +20.1]~ in T3 vs +5.2 [-1.8, +12.4]~ in T1; sizer +10.7 [+1.8, +19.4]~ vs +2.1 [-3.5, +8.0]~), and the PE pattern is a T3-only piece (+5.0 [-0.3, +10.0]~ T3, -1.4 [-5.8, +2.5]~ T1); the no-trade zones earn about the same in both states (+2.8 [-1.8, +7.7]~ T1, +2.0 [-4.8, +9.0]~ T3, both inside MDE), so they are the only piece that does not need the 2025-26 state; the first-stop cut, K6 add, NY-PM skip are ~0 everywhere. (4) Depth alone is a weak sorter: the thinnest-book tercile has level +31.4 vs +16.0 for the deepest and delta +10.7 vs +6.4, direction right but inside the CIs (section B); fill cost and the state index sort the LEVEL (rho +0.4).

**Honest labels.** Every piece is post-hoc selected (SS-2/ER-1/SD-1: thresholds and the piece list were chosen after looking at L6M/HOLD/L3M); the composite in PRE (+4.8) and in X' (+11.0) is inside MDE; the terciles, the importance weights and the 'now' windows overlap in time (the T3 tercile is 16 L6M weeks + 32 PRE weeks + 1 July-2025 week, and T1 is 32 X' weeks + 17 PRE weeks), so none of this is out-of-sample evidence about the future state; the regime state is a bundle (depth, fill, signals/day, correlation, brackets) that moved together, so the table cannot say WHICH variable matters. Nothing here changes a D6 setting.

---

## A. The state variables and the terciles

Daily and weekly frames are in `out/regimestress/regime_daily.csv` / `regime_weekly2.csv` (weeks Mon-Fri by label day, wk 0 = 2023-04-03 .. wk 148 = 2026-02-02). Variables: book depth within 10 levels (median of the 1-minute dp1m features over the week; **not available for the last week 2026-02-02..06, so that week is excluded from every tercile/weighting that uses depth: 148 weeks**), per-trade fill cost (store `fill_cost_pts`, mean over the week's signals), signals per day (all 10 books, 44k signals), ES-NQ 20-minute correlation at the signal second, % realised vol (NQ daily sqrt(sum of squared 5-min log returns), weekly mean), bracket-to-range = 60 pts / NQ daily range (weekly mean of the daily ratios; low = the bracket is narrow vs the day), London share of signals. Median of each variable by state-index tercile (all weeks):

| tercile   |   depth10 |   fill |   sig_day |   corr |   bracket |   london |   rv5 |
|:----------|----------:|-------:|----------:|-------:|----------:|---------:|------:|
| T1        |       120 |  1.204 |      38.8 |  0.847 |     0.307 |    0.144 | 0.836 |
| T2        |        95 |  1.268 |      53.6 |  0.894 |     0.232 |    0.188 | 0.9   |
| T3        |        66 |  2.64  |      78.8 |  0.932 |     0.171 |    0.226 | 1.215 |

Weeks per tercile by era (the terciles are largely eras - the confound the reweighting has to live with):

| idx6   |   HOLD<L6M (2025-07) |   L6M (2025-08..2026-02) |   PRE (2024-02..2025-06) |   X (2023-04..2024-01) |
|:-------|---------------------:|-------------------------:|-------------------------:|-----------------------:|
| T1     |                    1 |                        0 |                       17 |                     32 |
| T2     |                    2 |                       10 |                       25 |                     12 |
| T3     |                    1 |                       16 |                       32 |                      0 |


## B. Composite by tercile of each state variable (T1 = lowest value of the variable, T3 = highest; all weeks / 2024-02-on weeks)


**stack level $k/wk, all 148-149 weeks**

| variable | T1 (low) | T2 | T3 (high) | n per tercile |
|---|---|---|---|---|
| book depth<=10 lvls | +31.4 [+14.7, +47.9] | +20.3 [+8.0, +33.7] | +16.0 [+5.2, +27.6]~ | 50 |
| fill cost/trade | -5.3 [-15.8, +4.6]~ | +29.0 [+14.7, +42.5] | +43.9 [+30.4, +57.4] | 50 |
| signals/day | +12.4 [+1.5, +23.6]~ | +17.6 [+4.5, +30.3]~ | +37.3 [+19.9, +53.6] | 50 |
| ES-NQ corr | +6.8 [-4.8, +18.5]~ | +22.2 [+9.9, +35.4] | +38.3 [+22.0, +54.2] | 50 |
| 60pt/range | +41.6 [+25.5, +57.3] | +15.5 [+1.4, +29.1]~ | +10.2 [-1.6, +21.5]~ | 50 |
| London share | +6.6 [-4.8, +17.5]~ | +20.9 [+6.5, +36.3] | +39.9 [+26.4, +55.2] | 50 |
| % realised vol | +17.1 [+4.4, +29.7]~ | +21.3 [+9.5, +34.3] | +29.0 [+13.5, +44.9] | 50 |
| state index (7 vars) | +11.0 [+0.6, +22.2]~ | +12.3 [-0.3, +25.0]~ | +44.8 [+27.6, +61.4] | 50 |
| state index (6 vars, no vol) | +9.4 [-2.0, +20.6]~ | +11.8 [-1.1, +23.6]~ | +46.9 [+30.8, +62.8] | 50 |

**stack level $k/wk, weeks from 2024-02 (WF window; removes the 2023 era from T1)**

| variable | T1 (low) | T2 | T3 (high) | n per tercile |
|---|---|---|---|---|
| book depth<=10 lvls | +34.9 [+12.6, +57.2] | +30.3 [+14.4, +46.7] | +20.6 [+5.2, +35.4]~ | 35 |
| fill cost/trade | +4.6 [-12.4, +20.9]~ | +21.9 [+3.9, +39.0]~ | +59.1 [+43.5, +74.2] | 36 |
| signals/day | +18.0 [+3.9, +31.7]~ | +28.2 [+11.4, +46.2] | +39.1 [+17.7, +60.3] | 36 |
| ES-NQ corr | +11.6 [-2.3, +25.2]~ | +32.5 [+11.3, +52.6] | +41.3 [+23.8, +58.4] | 36 |
| 60pt/range | +50.8 [+34.0, +68.2] | +12.5 [-8.7, +32.6]~ | +21.0 [+6.5, +34.6] | 36 |
| London share | +11.5 [-3.9, +27.0]~ | +31.3 [+10.5, +52.1] | +42.7 [+25.6, +61.5] | 36 |
| % realised vol | +23.4 [+10.0, +37.9] | +28.6 [+12.3, +45.4] | +33.1 [+10.6, +55.5] | 36 |
| state index (7 vars) | +8.6 [-6.5, +24.2]~ | +31.2 [+13.3, +47.7] | +45.9 [+26.2, +65.5] | 35 |
| state index (6 vars, no vol) | +8.0 [-7.4, +24.2]~ | +27.6 [+10.4, +44.2] | +50.2 [+31.3, +69.8] | 35 |

**stack level $k/wk, HOLD weeks only (2025-07 on, ~31 weeks; ~10 per tercile)**

| variable | T1 (low) | T2 | T3 (high) | n per tercile |
|---|---|---|---|---|
| book depth<=10 lvls | +59.2 [+33.0, +85.5] | +33.7 [-2.7, +71.2]~ | +26.1 [-1.3, +53.7]~ | 11 |
| fill cost/trade | +1.3 [-23.5, +23.5]~ | +45.7 [+23.0, +67.0] | +70.8 [+40.9, +99.2] | 11 |
| signals/day | +29.1 [-0.2, +61.1]~ | +28.5 [-2.5, +59.3]~ | +58.6 [+31.6, +85.8] | 11 |
| ES-NQ corr | +27.6 [+1.5, +51.8]~ | +36.5 [-3.4, +75.0]~ | +52.8 [+26.5, +78.5] | 11 |
| 60pt/range | +68.2 [+41.9, +91.7] | +30.0 [+2.0, +62.9]~ | +18.2 [-13.1, +43.5]~ | 11 |
| London share | +9.5 [-18.5, +38.3]~ | +53.0 [+23.9, +81.5] | +55.9 [+30.0, +82.3] | 11 |
| % realised vol | +13.8 [-16.1, +39.1]~ | +44.5 [+17.3, +75.7]~ | +59.4 [+31.5, +87.7] | 11 |
| state index (7 vars) | +17.8 [-12.7, +42.8]~ | +38.6 [+9.0, +71.6]~ | +66.7 [+38.6, +91.7] | 11 |
| state index (6 vars, no vol) | +12.7 [-17.4, +37.9]~ | +49.7 [+21.8, +79.8] | +61.1 [+29.7, +92.0] | 11 |

**delta vs as-is $k/wk, all 148-149 weeks**

| variable | T1 (low) | T2 | T3 (high) | n per tercile |
|---|---|---|---|---|
| book depth<=10 lvls | +10.7 [-1.4, +21.7]~ | +11.2 [-0.3, +22.6]~ | +6.4 [-2.8, +15.2]~ | 50 |
| fill cost/trade | +6.4 [-3.5, +17.2]~ | +12.7 [+2.4, +22.9]~ | +9.1 [-2.0, +20.0]~ | 50 |
| signals/day | +3.9 [-4.7, +12.9]~ | +10.4 [-0.3, +20.8]~ | +13.9 [+2.3, +25.2]~ | 50 |
| ES-NQ corr | +2.6 [-6.0, +11.3]~ | +10.2 [-0.3, +20.9]~ | +15.5 [+4.6, +26.7]~ | 50 |
| 60pt/range | +13.7 [+2.0, +25.9]~ | +7.3 [-3.4, +18.4]~ | +7.2 [-1.7, +15.8]~ | 50 |
| London share | +6.7 [-3.6, +17.2]~ | +8.8 [-1.4, +18.7]~ | +12.8 [+2.5, +23.7]~ | 50 |
| % realised vol | +3.5 [-5.2, +11.7]~ | +10.0 [-0.8, +20.0]~ | +14.8 [+3.0, +27.6]~ | 50 |
| state index (7 vars) | +7.0 [-1.9, +16.5]~ | +3.5 [-6.9, +14.2]~ | +17.8 [+6.4, +29.5] | 50 |
| state index (6 vars, no vol) | +6.1 [-3.0, +15.5]~ | +8.8 [-2.3, +20.8]~ | +13.5 [+2.5, +24.6]~ | 50 |

**delta vs as-is $k/wk, weeks from 2024-02 (WF window; removes the 2023 era from T1)**

| variable | T1 (low) | T2 | T3 (high) | n per tercile |
|---|---|---|---|---|
| book depth<=10 lvls | +6.9 [-7.3, +21.1]~ | +9.1 [-3.7, +21.7]~ | +10.1 [-0.9, +22.7]~ | 35 |
| fill cost/trade | +7.0 [-6.3, +21.3]~ | +6.4 [-3.7, +16.5]~ | +12.7 [-2.0, +27.3]~ | 36 |
| signals/day | +5.4 [-4.7, +16.7]~ | +5.1 [-8.3, +18.3]~ | +15.6 [+1.7, +30.8]~ | 36 |
| ES-NQ corr | -3.0 [-13.8, +8.4]~ | +16.4 [+2.5, +30.2]~ | +12.9 [-0.3, +25.9]~ | 36 |
| 60pt/range | +14.8 [+1.4, +28.2]~ | +9.2 [-4.4, +23.5]~ | +1.8 [-9.2, +11.7]~ | 36 |
| London share | +3.5 [-8.6, +15.6]~ | +5.1 [-6.6, +17.1]~ | +17.6 [+3.8, +32.8]~ | 36 |
| % realised vol | +4.2 [-4.1, +12.7]~ | +5.6 [-7.2, +17.7]~ | +16.3 [+1.0, +33.5]~ | 36 |
| state index (7 vars) | +1.4 [-8.7, +11.8]~ | +10.2 [-3.1, +23.8]~ | +14.6 [+1.2, +28.4]~ | 35 |
| state index (6 vars, no vol) | +2.4 [-8.9, +14.7]~ | +8.1 [-5.1, +21.5]~ | +15.7 [+2.4, +30.0]~ | 35 |

**delta vs as-is $k/wk, HOLD weeks only (2025-07 on, ~31 weeks; ~10 per tercile)**

| variable | T1 (low) | T2 | T3 (high) | n per tercile |
|---|---|---|---|---|
| book depth<=10 lvls | +21.7 [-0.1, +43.2]~ | +19.9 [+0.0, +39.4]~ | +11.4 [-10.2, +33.4]~ | 11 |
| fill cost/trade | +17.6 [+0.5, +34.4]~ | +25.6 [+2.1, +48.9]~ | +9.6 [-10.2, +30.5]~ | 11 |
| signals/day | +4.6 [-15.3, +24.5]~ | +13.7 [-4.0, +34.5]~ | +33.4 [+14.2, +52.0] | 11 |
| ES-NQ corr | +8.4 [-12.8, +29.1]~ | +19.9 [+5.8, +37.3]~ | +24.0 [+1.9, +45.3]~ | 11 |
| 60pt/range | +22.2 [-2.4, +45.7]~ | +20.5 [+3.1, +40.9]~ | +9.6 [-8.2, +28.2]~ | 11 |
| London share | -1.1 [-14.9, +11.7]~ | +38.9 [+21.5, +55.5] | +16.1 [-6.2, +39.2]~ | 11 |
| % realised vol | +10.5 [-7.0, +29.2]~ | +1.0 [-15.9, +17.3]~ | +39.0 [+17.4, +58.7] | 11 |
| state index (7 vars) | +9.8 [-7.7, +27.6]~ | +13.7 [-6.8, +35.3]~ | +30.6 [+5.8, +53.7]~ | 11 |
| state index (6 vars, no vol) | +2.7 [-17.2, +23.3]~ | +22.6 [+8.0, +38.3]~ | +29.6 [+4.4, +53.2]~ | 11 |

## C. Pieces: leave-one-out contribution by state tercile, and by half of L6M / HOLD ($k/wk [CI]; `~` inside MDE)

| piece / book | L6M H1 | L6M H2 | HOLD H1 | HOLD H2 | state T3 (all weeks) | T2 | T1 | T3 (2024-02-on) | T1 (2024-02-on) |
|---|---|---|---|---|---|---|---|---|---|
| **D6 composite, stack level $k/wk** | +39.7 [+19.5, +59.8] | +44.6 [+20.4, +69.0] | +35.0 [+8.0, +61.4]~ | +43.6 [+20.3, +67.3] | +46.9 [+30.8, +62.8] | +11.8 [-1.1, +23.6]~ | +9.4 [-2.0, +20.6]~ | +50.2 [+31.3, +69.8] | +8.0 [-7.4, +24.2]~ |
| **D6 composite, delta vs as-is stack** | +17.7 [-1.6, +35.8]~ | +23.2 [+8.5, +38.0] | +12.8 [-5.7, +31.4]~ | +22.0 [+7.6, +36.6] | +13.5 [+2.5, +24.6]~ | +8.8 [-2.3, +20.8]~ | +6.1 [-3.0, +15.5]~ | +15.7 [+2.4, +30.0]~ | +2.4 [-8.9, +14.7]~ |
| piece: ER sizer on all six (running-max locks) | +10.7 [-2.1, +23.5]~ | +16.0 [-0.3, +32.8]~ | +10.9 [-4.5, +25.1]~ | +13.5 [-2.0, +27.8]~ | +10.7 [+1.8, +19.4]~ | +2.1 [-4.7, +9.5]~ | +2.1 [-3.5, +8.0]~ | +12.0 [+2.0, +21.6]~ | +1.0 [-6.2, +8.2]~ |
| piece: PE pattern (P6) | +0.0 [-7.3, +7.7]~ | +8.9 [-2.4, +19.3]~ | +1.4 [-6.8, +9.6]~ | +8.0 [-1.5, +17.3]~ | +5.0 [-0.3, +10.0]~ | +0.4 [-4.5, +5.6]~ | -1.4 [-5.8, +2.5]~ | +5.9 [-0.8, +12.9]~ | +2.8 [-2.3, +8.2]~ |
| piece: no-trade zones | +4.4 [-6.0, +15.7]~ | +5.8 [-1.7, +13.8]~ | +1.2 [-11.0, +13.2]~ | +5.0 [-1.8, +12.1]~ | +2.0 [-4.8, +9.0]~ | +4.1 [-3.7, +12.0]~ | +2.8 [-1.8, +7.7]~ | +4.2 [-3.1, +11.7]~ | +4.0 [-2.6, +10.7]~ |
| piece: 70/30 split (K6 1/1, others 70/30) | +1.3 [-3.0, +5.5]~ | +6.8 [+1.3, +13.0]~ | +1.5 [-2.2, +5.4]~ | +6.3 [+1.3, +12.1]~ | +5.2 [+1.3, +9.3]~ | +0.6 [-1.8, +3.1]~ | -0.4 [-2.3, +1.5]~ | +5.1 [+0.4, +10.3]~ | -1.2 [-2.9, +0.4]~ |
| piece: first-stop cut | -1.1 [-4.8, +2.4]~ | +0.6 [-1.5, +2.7]~ | -3.6 [-8.4, +0.2]~ | +1.4 [-0.8, +3.8]~ | +0.3 [-1.8, +2.3]~ | -0.6 [-2.2, +0.8]~ | -0.0 [-1.8, +1.4]~ | -0.1 [-2.9, +2.5]~ | -0.9 [-3.3, +0.9]~ |
| piece: K6 add (split vs market) | -0.9 [-3.0, +0.7]~ | +1.9 [+0.0, +4.2]~ | -1.3 [-3.3, +0.3]~ | +1.8 [+0.1, +3.8]~ | +1.0 [-0.3, +2.3]~ | -0.0 [-0.7, +0.7]~ | -0.1 [-0.8, +0.6]~ | +1.6 [-0.1, +3.3]~ | -0.1 [-0.9, +0.8]~ |
| piece: NY-PM end skip 14:40-15:00 (added) | -0.1 [-0.9, +0.7]~ | +0.1 [-0.7, +0.8]~ | -0.1 [-0.7, +0.6]~ | +0.1 [-0.6, +0.8]~ | -0.2 [-0.5, +0.2]~ | -0.1 [-0.5, +0.4]~ | +0.1 [-0.2, +0.4]~ | -0.3 [-0.8, +0.2]~ | -0.1 [-0.5, +0.2]~ |
| Sunday CANDIDATE (P6+K6 sizer, K6 mkt, NY-PM skip) delta | +20.1 [+1.9, +36.3]~ | +20.6 [+4.8, +36.2]~ | +13.7 [-3.8, +30.2]~ | +20.9 [+5.9, +36.0]~ | +11.7 [+1.7, +21.8]~ | +7.5 [-2.8, +18.4]~ | +6.5 [-1.7, +15.0]~ | +12.5 [+0.8, +24.9]~ | +2.8 [-7.4, +14.4]~ |
| sizer on P6 | +11.3 [+2.3, +19.5]~ | +11.7 [-0.5, +24.6]~ | +10.6 [-0.1, +19.9]~ | +10.4 [-1.4, +22.8]~ | +9.1 [+2.4, +15.9]~ | +0.9 [-5.1, +6.8]~ | +2.0 [-2.2, +6.3]~ | +9.3 [+2.4, +16.7]~ | +2.3 [-3.7, +8.2]~ |
| sizer on K6 | +1.0 [-3.4, +6.0]~ | +3.7 [-0.6, +7.7]~ | -0.0 [-4.2, +4.3]~ | +3.7 [-0.3, +7.2]~ | +0.7 [-1.9, +3.5]~ | +0.0 [-1.7, +1.6]~ | +0.3 [-1.0, +1.5]~ | +1.0 [-2.0, +4.0]~ | -0.9 [-2.3, +0.6]~ |
| sizer on A6 | +0.7 [-0.2, +1.6]~ | +1.4 [+0.1, +2.8]~ | +0.5 [-0.3, +1.3]~ | +1.5 [+0.2, +2.7]~ | +0.7 [+0.0, +1.4]~ | +0.5 [-0.0, +1.0]~ | +0.4 [-0.0, +0.8]~ | +0.7 [-0.2, +1.6]~ | +0.5 [-0.0, +1.0]~ |
| sizer on H6 | -0.4 [-3.2, +3.0]~ | +0.6 [-3.4, +4.9]~ | +0.1 [-2.7, +3.2]~ | +0.0 [-3.9, +3.6]~ | +0.8 [-1.7, +3.5]~ | -0.3 [-1.8, +1.2]~ | -0.5 [-1.7, +0.7]~ | +1.0 [-2.3, +4.5]~ | -0.6 [-2.1, +1.0]~ |
| sizer on M6 | -1.0 [-3.2, +1.1]~ | -0.3 [-3.0, +2.5]~ | -0.4 [-2.5, +1.6]~ | -0.9 [-3.5, +1.8]~ | -0.7 [-2.4, +0.9]~ | +0.8 [-0.4, +2.0]~ | +0.3 [-0.9, +1.4]~ | -0.7 [-2.9, +1.3]~ | -0.4 [-2.1, +1.2]~ |
| sizer on U6 | -0.9 [-3.0, +1.2]~ | -1.1 [-4.5, +2.2]~ | +0.1 [-2.0, +2.0]~ | -1.2 [-4.1, +1.7]~ | -0.1 [-1.7, +1.5]~ | +0.3 [-1.1, +1.5]~ | -0.4 [-1.5, +0.7]~ | +0.4 [-1.6, +2.4]~ | +0.1 [-1.5, +1.6]~ |
| book P6 delta vs as-is | +16.0 [+2.0, +28.5]~ | +14.6 [-1.4, +30.5]~ | +12.2 [-1.1, +24.2]~ | +14.0 [-0.9, +28.5]~ | +11.8 [+3.1, +20.1]~ | +6.2 [-2.1, +15.0]~ | +5.2 [-1.8, +12.4]~ | +12.6 [+1.9, +23.5]~ | +4.1 [-5.4, +14.7]~ |
| book H6 delta vs as-is | +4.1 [-3.2, +12.2]~ | +3.8 [-0.3, +8.1]~ | +3.1 [-3.6, +9.9]~ | +3.5 [-0.0, +7.3]~ | +0.8 [-2.9, +4.5]~ | +1.3 [-1.8, +4.6]~ | -0.7 [-3.2, +1.6]~ | +1.1 [-3.4, +6.0]~ | -0.8 [-4.1, +2.3]~ |
| book K6 delta vs as-is | -1.0 [-6.0, +4.4]~ | +5.0 [+0.4, +10.7]~ | -1.6 [-6.2, +3.5]~ | +4.7 [+0.7, +9.9]~ | +1.7 [-1.6, +5.1]~ | -1.1 [-3.4, +1.1]~ | +0.7 [-1.7, +2.9]~ | +2.6 [-1.2, +6.8]~ | -1.5 [-4.1, +1.2]~ |
| book A6 delta vs as-is | +0.5 [-0.5, +1.7]~ | +1.4 [-0.2, +3.1]~ | +0.4 [-0.5, +1.3]~ | +1.5 [+0.0, +3.1]~ | +0.6 [-0.1, +1.3]~ | +0.5 [-0.1, +1.1]~ | +0.6 [+0.1, +1.0]~ | +0.6 [-0.4, +1.5]~ | +0.7 [+0.2, +1.2]~ |
| book M6 delta vs as-is | -1.2 [-3.9, +1.3]~ | +0.2 [-2.8, +3.3]~ | -0.8 [-3.5, +1.8]~ | -0.3 [-2.9, +2.5]~ | -0.8 [-2.5, +1.0]~ | +1.1 [-0.4, +2.5]~ | +0.2 [-1.2, +1.5]~ | -0.9 [-3.0, +1.1]~ | -0.7 [-2.5, +1.0]~ |
| book U6 delta vs as-is | -0.6 [-5.4, +4.3]~ | -1.8 [-6.9, +3.2]~ | -0.4 [-5.6, +5.1]~ | -1.5 [-6.0, +3.4]~ | -0.6 [-3.2, +1.9]~ | +0.9 [-2.0, +4.0]~ | +0.1 [-2.4, +2.6]~ | -0.3 [-3.3, +2.5]~ | +0.6 [-2.8, +4.1]~ |

Reading: the gain does not fade inside L6M or HOLD (second half larger than the first: +23.2 vs +17.7 L6M, +22.0 vs +12.8 HOLD) but the first half of L6M is weaker mostly because the PE pattern was ~0 then (0.0 vs +8.9). 'sizer on X' = the ER sizer's contribution when switched on for book X alone inside the all-six composite (LOO of the all6 list); 'book X delta' = that book's composite P&L minus its as-is P&L (rules + sizing + split on that book).


## D. Stop basis sensitivity (delta vs as-is, $k/wk)

| series | L6M | HOLD | T3 | T1 (2023-24-like) | actual 2023-24 weeks |
|---|---|---|---|---|---|
| Native 1.28 (A) composite delta | +21.8 [+9.9, +33.6] | +18.7 [+7.7, +30.8] | +15.1 [+4.1, +26.1]~ | +6.8 [-2.3, +16.2]~ | +10.5 [+3.3, +18.1]~ |
| join 2.45 (B, live-cal) composite delta | +19.5 [+7.9, +31.2] | +16.4 [+5.6, +28.3]~ | +12.0 [+1.1, +23.0]~ | +5.4 [-3.8, +14.7]~ | +8.6 [+1.5, +16.2]~ |
| A/B parity mix (headline) | +20.4 [+8.6, +32.1] | +17.4 [+6.5, +29.4] | +13.5 [+2.5, +24.6]~ | +6.1 [-3.0, +15.5]~ | +9.5 [+2.4, +17.2]~ |

## E. Regime-normalisation scenario: importance weights on the state variables (method, ESS, sensitivity)

Target = the 91 weeks of 2023-04..2024-12 (wk 0-90). Weights = odds from a ridge-logistic classifier of target vs source weeks on the standardised state variables (depth, fill, log signals/day, corr, log bracket ratio, London share, log % vol), w = p/(1-p) x n_source/n_target; estimate = weighted mean of the weekly series; 95% CI = 1,000 bootstrap resamples of source and target weeks with the classifier REFIT each time (so the CI includes weight-estimation noise, not the model-choice noise). ESS = Kish (sum w)^2 / sum w^2. The headline column uses source = ALL 148 weeks (ESS ~90: the reweighting only tilts the sample toward the 2023-24 state; it contains the 2023-24 weeks themselves, so it is close to the actual 2023-24 mean by construction). The informative-but-fragile versions use only 2025-26 weeks as the source (the composite's response in the 2025-26 state evaluated at the 2023-24 state mix); there the overlap is poor and ESS falls to 4-7 as the ridge penalty is relaxed, so those numbers are extrapolations.

| scenario | composite level $k/wk [CI] | composite delta $k/wk [CI] | ESS (boot p5) | unweighted source delta | n src |
|---|---|---|---|---|---|
| A: 7 vars, ridge C=0.3, src=2025-26 (wk>=91) | +0.9 [-16.9, +27.3] | +1.9 [-9.6, +17.5] | 18 (15) | +9.3 | 57 |
| A2: 7 vars, ridge C=0.05 (heavier shrinkage) | +14.4 [-2.3, +33.5] | +5.7 [-4.4, +17.2] | 33 (27) | +9.3 | 57 |
| B: 1-D state index, src=2025-26 | +8.5 [-14.7, +35.0] | +3.5 [-10.3, +17.0] | 16 (10) | +9.3 | 57 |
| C: 7 vars C=0.3, src=L6M weeks only | +33.6 [+20.4, +51.1] | +22.4 [+10.9, +32.6] | 20 (17) | +20.1 | 27 |
| D: 1-D state index, src=L6M weeks only | +32.0 [+14.8, +52.2] | +14.4 [+3.8, +22.8] | 12 (8) | +20.1 | 27 |
| E: 6 state vars (no vol) C=0.3, src=2025-26 | -4.2 [-24.2, +26.4] | +2.3 [-10.4, +18.8] | 15 (12) | +9.3 | 57 |
| A3: 7 vars, C=3 (light ridge) | -15.4 [-34.6, +20.8] | -6.3 [-17.0, +18.8] | 7 (6) | +9.3 | 57 |
| A4: 7 vars, C=30 (near unregularised) | -25.2 [-50.1, +17.7] | -12.8 [-22.9, +19.0] | 4 (3) | +9.3 | 57 |
| C3: 7 vars C=3, src=L6M | +27.7 [+16.6, +45.3] | +25.5 [+13.9, +35.0] | 14 (13) | +20.1 | 27 |
| C4: 7 vars C=30, src=L6M | +21.2 [+12.6, +40.5] | +28.2 [+16.0, +36.5] | 9 (8) | +20.1 | 27 |
| G: 7 vars C=0.3, src=ALL weeks (incl. 2023-24) | +12.4 [+3.5, +20.9] | +9.1 [+1.9, +16.5] | 95 (76) | +9.4 | 148 |
| G1: 1-D index, src=ALL weeks | +14.8 [+7.0, +23.0] | +6.9 [+0.7, +12.9] | 114 (92) | +9.4 | 148 |
| F: depth10 alone, src=2025-26 | +31.6 [+16.3, +49.3] | +9.5 [-1.1, +20.7] | 28 (21) | +9.3 | 57 |
| F: fill alone, src=2025-26 | -15.9 [-43.2, +20.2] | +0.4 [-12.0, +16.4] | 8 (6) | +9.3 | 57 |
| F: sig_day alone, src=2025-26 | +20.7 [+0.8, +42.2] | +3.9 [-8.6, +14.7] | 22 (13) | +9.3 | 57 |
| F: corr alone, src=2025-26 | +7.2 [-17.8, +37.7] | -0.8 [-16.0, +18.8] | 14 (9) | +9.3 | 57 |
| F: bracket alone, src=2025-26 | +17.0 [-0.5, +36.6] | +7.3 [-4.3, +15.8] | 17 (9) | +9.3 | 57 |
| F: london alone, src=2025-26 | +25.8 [+11.1, +40.9] | +4.6 [-6.6, +14.6] | 37 (26) | +9.3 | 57 |
| F: rv5 alone, src=2025-26 | +32.7 [+19.7, +46.8] | +8.2 [-0.7, +17.6] | 52 (41) | +9.3 | 57 |

Points: (i) weights built on the 2025-26 weeks only are all over the place (+28 to -13 $k/wk of delta) consistent with the 2025H1 weeks that resemble 2023-24 having earned little and the L6M weeks that resemble 2023-24 having earned a lot: with 27-57 source weeks and ESS 4-20 the scenario is not identified; (ii) weights from all weeks and the post-stratified estimate agree with the actual 2023-24 weeks (+9 to +10 delta, +12 to +14 level); (iii) a single variable does not explain the era gap in level (fill cost alone reweights the 2025-26 level to -16, depth alone to +32).


Weighted pieces under the headline scenario (G) vs unweighted all-weeks source, $k/wk [CI]:

| series | regime-normalised (G) | post-stratified | actual 2023-24 weeks | L6M |
|---|---|---|---|---|
| **D6 composite, delta vs as-is stack** | +9.1 [+1.9, +16.5] | +7.8 [+1.1, +14.7] | +9.5 [+2.4, +17.2]~ | +20.4 [+8.6, +32.1] |
| piece: ER sizer on all six (running-max locks) | +2.5 [-2.3, +7.1] | +2.9 [-1.4, +6.9] | +2.8 [-2.1, +7.5]~ | +13.4 [+3.0, +23.6]~ |
| piece: PE pattern (P6) | -0.5 [-3.7, +2.6] | -0.2 [-3.1, +2.9] | -0.9 [-4.1, +2.4]~ | +4.5 [-2.5, +11.8]~ |
| piece: no-trade zones | +3.7 [-0.9, +8.1] | +3.2 [-0.6, +7.7] | +3.9 [-1.0, +8.9]~ | +5.1 [-1.6, +11.7]~ |
| piece: 70/30 split (K6 1/1, others 70/30) | +0.4 [-1.5, +2.5] | +0.4 [-1.0, +2.0] | +0.2 [-1.8, +2.4]~ | +4.1 [+0.5, +8.0]~ |
| piece: first-stop cut | +0.4 [-0.8, +1.5] | -0.2 [-1.4, +0.9] | +0.4 [-0.7, +1.4]~ | -0.3 [-2.6, +1.7]~ |
| piece: K6 add (split vs market) | -0.1 [-0.6, +0.5] | +0.0 [-0.4, +0.5] | -0.1 [-0.6, +0.4]~ | +0.5 [-1.0, +2.1]~ |
| piece: NY-PM end skip 14:40-15:00 (added) | -0.0 [-0.3, +0.3] | -0.0 [-0.2, +0.2] | -0.0 [-0.3, +0.2]~ | +0.0 [-0.5, +0.5]~ |
| Sunday CANDIDATE (P6+K6 sizer, K6 mkt, NY-PM skip) delta | +8.4 [+1.7, +15.1] | +7.4 [+1.2, +13.8] | +8.7 [+2.1, +15.6]~ | +20.3 [+8.1, +32.1] |
| sizer on P6 | +1.6 [-2.1, +5.2] | +2.2 [-1.1, +5.4] | +1.7 [-2.3, +5.3]~ | +11.5 [+3.9, +19.1] |
| sizer on K6 | +0.1 [-1.2, +1.2] | +0.2 [-0.7, +1.2] | +0.0 [-1.1, +1.3]~ | +2.3 [-0.9, +5.6]~ |
| sizer on A6 | +0.3 [-0.0, +0.7] | +0.5 [+0.2, +0.8] | +0.4 [+0.0, +0.8]~ | +1.1 [+0.2, +1.9]~ |
| sizer on H6 | -0.1 [-1.0, +1.0] | -0.3 [-1.2, +0.5] | +0.0 [-1.0, +1.1]~ | +0.1 [-2.5, +2.7]~ |
| sizer on M6 | +0.7 [-0.2, +1.7] | +0.4 [-0.4, +1.2] | +0.8 [-0.1, +1.8]~ | -0.6 [-2.3, +1.1]~ |
| sizer on U6 | -0.2 [-1.1, +0.7] | -0.1 [-0.9, +0.8] | -0.1 [-1.1, +0.7]~ | -1.0 [-2.9, +0.9]~ |
| book P6 delta vs as-is | +7.1 [+1.5, +12.5] | +6.2 [+0.9, +11.5] | +7.4 [+1.8, +13.1]~ | +15.3 [+4.8, +25.5] |
| book H6 delta vs as-is | +0.3 [-1.7, +2.4] | +0.2 [-1.6, +1.9] | +0.3 [-1.7, +2.4]~ | +3.9 [-0.4, +8.6]~ |
| book K6 delta vs as-is | +0.1 [-1.8, +1.7] | +0.1 [-1.4, +1.7] | +0.0 [-1.8, +1.8]~ | +2.0 [-1.6, +5.9]~ |
| book A6 delta vs as-is | +0.4 [+0.1, +0.9] | +0.5 [+0.2, +0.9] | +0.5 [+0.1, +0.9]~ | +0.9 [-0.1, +2.0]~ |
| book M6 delta vs as-is | +0.7 [-0.4, +1.8] | +0.4 [-0.5, +1.4] | +0.7 [-0.4, +1.8]~ | -0.5 [-2.4, +1.5]~ |
| book U6 delta vs as-is | +0.6 [-1.4, +2.4] | +0.3 [-1.4, +2.1] | +0.6 [-1.3, +2.6]~ | -1.2 [-4.6, +2.2]~ |

## F. Calendar half-years (week means, $k/wk; ER sizer, PE, zones are LOO contributions)

| half                   |   asis_level |   composite_level |   composite_delta |   piece: ER sizer (running-max locks) |   piece: PE pattern (P6 reading) |   piece: no-trade zones |   book P6 delta vs as-is |   depth10 |   fill |   sig_day |
|:-----------------------|-------------:|------------------:|------------------:|--------------------------------------:|---------------------------------:|------------------------:|-------------------------:|----------:|-------:|----------:|
| 23H1 (Apr-Sep 23)      |        -10.5 |               4.2 |              14.7 |                                   6.4 |                              0.7 |                     2.9 |                     10.6 |       114 |   1.19 |        41 |
| 23H2                   |          9.5 |              10.4 |               0.9 |                                  -2.5 |                             -1.1 |                     1.4 |                     -0.2 |       129 |   1.22 |        42 |
| 24H1                   |          6.9 |              24.2 |              17.3 |                                   5.9 |                             -0.1 |                     8.5 |                     16   |        91 |   1.26 |        61 |
| 24H2                   |         26.3 |              23.4 |              -2.9 |                                   0.9 |                             -0.3 |                     2.7 |                     -2.4 |        84 |   1.94 |        69 |
| 25H1                   |         26.2 |              34.5 |               8.3 |                                   8.2 |                              2.5 |                    -2.2 |                      9.3 |        73 |   2.62 |        72 |
| 25H2 (Oct 25-Feb 6 26) |         22.5 |              44   |              21.4 |                                  12.8 |                              6.3 |                     5.7 |                     14.5 |        74 |   2.7  |        80 |

## G. Disclosures and limits

- The weekly composite delta has lag-1 autocorrelation -0.05 and an SD of 38k $/wk, so iid week bootstraps are used; windows are overlapping in the sense that HOLD contains L6M and the terciles mix eras. Partial first weeks of a window follow the engine convention (window days only) in the L6M/HOLD columns; tercile columns use whole Monday-Friday weeks.
- The 'actual 2023-24' column is the composite over wk 0-90 (2023-04-03..2024-12-29) with its own week-bootstrap CI, which is NOT the same set as X' (2023-04..2024-01, delta +11.0) or PRE (2024-02..2025-06, +4.8) in the Sunday table.
- Order of the state index: percentile ranks over all weeks; so a tercile is relative to 2023-26, not an absolute level. A 'faded' state in the future could be below the 2023 values (thicker book) or in between; the scenario only covers the observed 2023-24 mix.
- Pieces are LOO inside the composite on the same engine (res_*.pkl); K6 market and the CANDIDATE come from the same run set. Nothing was re-run on the engine; no post-cut data was read; no new rule was searched (the 7 + 6 state variables and the tercile/era definitions were fixed before the tables were read; the set size is: 9 state-variable cuts x 3 samples x 21 series reported, so multiplicity is large and the CIs are not family-wise).
- Files: `out/regimestress/` rs_stats.csv (every window/half/tercile cell), rs_rho.csv, rs_reweight.csv, rs_poststrat.csv, weekly_series.csv, regime_weekly_idx.csv, index_tercile_by_era.csv, series.pkl.
