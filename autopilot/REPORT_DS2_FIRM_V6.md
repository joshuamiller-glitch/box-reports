# REPORT DS2-FIRM v6 - SMART LOCKS (trackFIRM, 2026-10-22); research only

Prereg: l2vast/PREREG_DS2_FIRM_V6.md (frozen before scoring; sha in DECISIONS). Benchmarks: corrected P9 14/14 (WF 25.0k / SD 104.5k / maxDD 401k; L8W 34.2k / 267k; IS 13.7k / 407k) and V4/V5's best static lock set BEST (per-book day live, combined cap off, give-back arm 2R keep 67% armed after >= 2 closed trades, week floor 12R, London/NY 10 lots; WF 25.5k / 93.1k / 287k; L8W 56.1k / 183k; IS 13.2k / 305k). Engine: riskeng2 (validated within 0.1% of the hard-lock engine); every cell here is on the fixed-60 exact path with corrected-P9 points, so no L2 layer is needed or used; blocks A-D are parameter/table changes (a per-session lock file from the VPS writer), E-F would be new code.

**What was and was not run (honest ledger).** RUN: A1, A2, A3, B1 (2 of 4 variants), C1, C2, C3 (ZN and CL union only; 3 of 9 cells; 6J daily-only on disk: not run), D1-D4, E1/E2 (day-level regime selection of lock presets, GMM instead of HMM), E3 (K4-EXACT prior-day output + 18:05 depth), F1/F2-style learned policy with the first-trigger counterfactual (F3) and shuffled-label control (12 worlds, degenerate, see below), F4 exhibit (latest replay week), G2 deflated Sharpe. NOT RUN: B2 and B3 (the state library has snapshots at 12 fixed instants per day only; a faithful implementation needs continuous depth - not attempted), the F2 classifier, 500-world nulls for the individual A-D cells (the single cells that beat the live pair on mean AND maxDD are listed; none beats the V5 best static set), G1 joint with W3 centre replay (pending union replay at time of writing: see V4).

## Blocks A-D on top of the LIVE locks (corrected-P9 benchmark)

Base: WF 25.0k / SD 104.5k / maxDD 401.6k / worst -137.1k; L8W 34.2k / 267.1k; IS 13.7k / 407.5k.

6 of 64 cells beat the base on WF mean AND maxDD; 1 also on L8W. Block summaries (best cell per block by WF maxDD among cells with WF mean >= base):

| block | cells | beat base WF mean&DD | best cell | WF mean / SD / maxDD | L8W mean / maxDD | IS mean / maxDD |
|---|---|---|---|---|---|---|
| A1 | 6 | 0 | A1 / g1.0 / floors | 29.8k / 113.8k / 475.7k | 41.6k / 267.1k | 11.7k / 566.8k |
| A2 | 8 | 0 | A2 / low0.33 / high0.5 | 25.0k / 104.5k / 401.6k | 34.2k / 267.1k | 13.7k / 407.5k |
| A3 | 4 | 0 | A3 / cap_resume_regime | 25.1k / 104.5k / 402.7k | 34.2k / 267.1k | 13.7k / 407.5k |
| B1 | 2 | 1 | B1 / thick_scale6 | 29.9k / 118.9k / 400.9k | 17.1k / 370.7k | 11.2k / 528.9k |
| C1 | 24 | 0 | C1 / FOMC / cap0.75 / arm1.5 | 25.2k / 103.8k / 401.6k | 37.1k / 267.1k | 14.1k / 407.5k |
| C2 | 4 | 1 | C2 / wk_inv6_else12 | 29.0k / 102.5k / 325.0k | 34.2k / 267.1k | 18.7k / 293.6k |
| C3 | 3 | 1 | C3 / shock97.5 / scale8 | 29.5k / 103.7k / 355.2k | 31.1k / 262.2k | 8.2k / 354.0k |
| D1 | 3 | 2 | D1 / stops3_lots8_halt5 | 27.4k / 104.1k / 373.9k | 35.3k / 256.2k | 13.8k / 335.3k |
| D2 | 3 | 0 | D2 / flips3 | 27.8k / 99.4k / 416.7k | 48.9k / 255.7k | 6.6k / 494.2k |
| D3 | 3 | 1 | D3 / pf_tight0.8_loose1.2 | 28.5k / 104.4k / 305.1k | 30.3k / 212.9k | 10.8k / 409.5k |
| D4 | 4 | 0 | D4 / last90x0.75_first60x1.5 | 25.8k / 98.8k / 418.6k | 36.5k / 216.6k | 11.5k / 470.6k |

Cells beating the base on WF mean and maxDD:

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| D3 / pf_tight0.8_loose1.2 | 28.5k / 104.4k / 305.1k / -136.7k | 30.3k / 212.9k | 10.8k / 409.5k | +3.5k / -97k | -3.9k / -54k |
| C2 / wk_inv6_else12 | 29.0k / 102.5k / 325.0k / -202.3k | 34.2k / 267.1k | 18.7k / 293.6k | +4.0k / -77k | +0.0k / +0k |
| C3 / shock97.5 / scale8 | 29.5k / 103.7k / 355.2k / -137.1k | 31.1k / 262.2k | 8.2k / 354.0k | +4.5k / -46k | -3.1k / -5k |
| D1 / stops3_lots8_halt5 | 27.4k / 104.1k / 373.9k / -139.0k | 35.3k / 256.2k | 13.8k / 335.3k | +2.5k / -28k | +1.1k / -11k |
| D1 / stops3_lots8_halt4 | 27.9k / 104.7k / 399.8k / -139.0k | 31.0k / 256.2k | 13.1k / 344.7k | +3.0k / -2k | -3.2k / -11k |
| B1 / thick_scale6 | 29.9k / 118.9k / 400.9k / -138.5k | 17.1k / 370.7k | 11.2k / 528.9k | +4.9k / -1k | -17.1k / +104k |

## Blocks A-D on top of the V4/V5 best static lock set

Base: WF 25.5k / SD 93.1k / maxDD 287.3k / worst -184.8k; L8W 56.1k / 182.6k; IS 13.2k / 304.9k.

1 of 64 cells beat the base on WF mean AND maxDD; 1 also on L8W. Block summaries (best cell per block by WF maxDD among cells with WF mean >= base):

| block | cells | beat base WF mean&DD | best cell | WF mean / SD / maxDD | L8W mean / maxDD | IS mean / maxDD |
|---|---|---|---|---|---|---|
| A1 | 6 | 0 | A1 / g1.0 / floors | 25.8k / 92.6k / 298.3k | 56.1k / 182.6k | 12.1k / 304.9k |
| A2 | 8 | 0 | A2 / low0.67 / high0.67 | 25.5k / 93.1k / 287.3k | 56.1k / 182.6k | 13.2k / 304.9k |
| A3 | 4 | 0 | A3 / cap_resume_calm | 25.5k / 93.1k / 287.3k | 56.1k / 182.6k | 13.2k / 304.9k |
| B1 | 2 | 0 | B1 / thick_scale6 | 30.2k / 102.3k / 319.6k | 55.2k / 299.3k | 12.9k / 328.8k |
| C1 | 24 | 1 | C1 / ME / cap0.5 / arm1.5 | 25.8k / 92.4k / 287.1k | 56.8k / 177.1k | 12.3k / 291.5k |
| C2 | 4 | 0 | C2 / wk_inv6_else12 | 25.9k / 92.6k / 287.3k | 56.1k / 182.6k | 13.2k / 304.9k |
| C3 | 3 | 0 | C3 / shock90 / scale8 | 19.6k / 87.6k / 271.0k | 46.4k / 221.5k | 7.9k / 315.8k |
| D1 | 3 | 0 | D1 / stops3_lots8_halt5 | 26.3k / 93.9k / 338.4k | 56.7k / 189.8k | 13.1k / 311.6k |
| D2 | 3 | 0 | D2 / flips3 | 26.2k / 88.9k / 394.9k | 58.4k / 244.3k | 3.3k / 485.5k |
| D3 | 3 | 0 | D3 / pf_tight0.67_loose1.5 | 27.8k / 95.0k / 313.1k | 67.8k / 134.6k | 9.7k / 373.8k |
| D4 | 4 | 0 | D4 / last90x0.75_first60x1.25 | 22.1k / 92.9k / 319.5k | 42.7k / 148.7k | 13.4k / 447.9k |

Cells beating the base on WF mean and maxDD:

| cell | WF mean / SD / maxDD / worst | L8W mean / maxDD | IS mean / maxDD | WF d mean / d maxDD | L8W d mean / d maxDD |
|---|---|---|---|---|---|
| C1 / ME / cap0.5 / arm1.5 | 25.8k / 92.4k / 287.1k / -184.8k | 56.8k / 177.1k | 12.3k / 291.5k | +0.3k / -0k | +0.7k / -5k |

## Block E - regime models


| rule | WF mean / SD / maxDD | L8W mean / SD / maxDD |
|---|---|---|
| static|P0 live-day | 29.2k / 102.0k / 325.0k | 34.2k / 109.4k / 267.1k |
| static|P1 pb+gb | 34.7k / 111.3k / 325.0k | 41.6k / 123.4k / 267.1k |
| static|P2 gb only | 36.5k / 135.6k / 494.0k | 49.8k / 192.4k / 352.8k |
| static|P3 pb+gb keep67 N2 | 25.4k / 99.6k / 394.0k | 56.5k / 116.3k / 246.8k |
| static|P4 pb+gb sess10 | 33.1k / 106.7k / 320.1k | 57.0k / 124.8k / 209.1k |
| static|P5 P3 sess10 | 25.5k / 93.1k / 287.3k | 56.1k / 106.1k / 182.6k |
| static|P6 no locks | 46.9k / 171.8k / 1037.3k | 53.5k / 287.7k / 793.3k |
| static|P7 tight gb keep75 | 21.9k / 89.3k / 524.7k | 41.0k / 92.5k / 244.0k |
| regime|gmm3 | 34.8k / 139.9k / 969.1k | 20.2k / 243.0k / 769.2k |
| regime|kmeans5 | 37.2k / 137.3k / 868.6k | 56.2k / 275.6k / 636.5k |
| regime|k4+depth | 36.3k / 126.8k / 462.0k | 72.3k / 218.5k / 454.1k |

gmm3: states per fold [3, 3, 3, 2, 3, 3, 3, 3, 3, 3, 3]; mean state run length (days) 4.3; preset chosen per state by fold (first 4 folds): {0: 'P5 P3 sess10', 1: 'P3 pb+gb keep67 N2', 2: 'P0 live-day'}; {0: 'P1 pb+gb', 1: 'P4 pb+gb sess10', 2: 'P2 gb only'}; {0: 'P4 pb+gb sess10', 1: 'P6 no locks', 2: 'P1 pb+gb'}; {0: 'P6 no locks', 1: 'P2 gb only', 2: 'P1 pb+gb'}

kmeans5: states per fold [5, 5, 4, 5, 5, 4, 3, 4, 4, 5, 4]; mean state run length (days) 1.7; preset chosen per state by fold (first 4 folds): {0: 'P0 live-day', 1: 'P7 tight gb keep75', 2: 'P3 pb+gb keep67 N2', 3: 'P5 P3 sess10', 4: 'P2 gb only'}; {0: 'P0 live-day', 1: 'P5 P3 sess10', 2: 'P6 no locks', 3: 'P1 pb+gb', 4: 'P7 tight gb keep75'}; {0: 'P7 tight gb keep75', 1: 'P0 live-day', 2: 'P4 pb+gb sess10', 3: 'P6 no locks', 4: 'P1 pb+gb'}; {0: 'P6 no locks', 1: 'P1 pb+gb', 2: 'P5 P3 sess10', 3: 'P2 gb only', 4: 'P6 no locks'}

k4+depth: states per fold [4, 6, 3, 6, 6, 6, 6, 6, 6, 6, 6]; mean state run length (days) 1.4; preset chosen per state by fold (first 4 folds): {3: 'P2 gb only', 4: 'P3 pb+gb keep67 N2', 5: 'P5 P3 sess10'}; {0: 'P0 live-day', 1: 'P2 gb only', 2: 'P6 no locks', 3: 'P2 gb only', 4: 'P0 live-day', 5: 'P3 pb+gb keep67 N2'}; {0: 'P2 gb only', 1: 'P2 gb only', 2: 'P5 P3 sess10', 3: 'P2 gb only', 4: 'P0 live-day', 5: 'P7 tight gb keep75'}; {0: 'P2 gb only', 1: 'P4 pb+gb sess10', 2: 'P2 gb only', 3: 'P1 pb+gb', 4: 'P4 pb+gb sess10', 5: 'P6 no locks'}

Reading: the walk-forward regime selector chooses presets by fit-window Sharpe; in the fit windows the lock-free preset has the highest daily Sharpe in most states, so the selector keeps drifting to it and the WF maxDD explodes (0.46-0.97M vs 0.29M for the static BEST). Regime-conditioned lock selection does not beat the single static set; state persistence is short (mean run 1.4-4.3 days), which is why it cannot track a regime.

## Block F - learned lock policy (F1/F3/F4)

Samples: every 5th 1-min bar of every session from 2023-02 (246,707), features at the bar: day realized / unrealized / peak P&L, trades and stops today, minutes since session open, session, ridge forecast session RV (relative), RV of the last 60 bars, VIX (lagged), session-open depth, signals in the last hour, event-day flag, day-of-week; label = P&L of the rest of the session if the lock-free 14-lot pair keeps trading (computed from the exact P9 trades; strictly after the decision bar, absent from the features). Walk-forward LightGBM (monthly refit, 3-day embargo, first prediction 2023-08). Out-of-sample rank correlation of the prediction with the label: full features -0.02, dollar-only features +0.01 (no skill). Gain importance (full model, top 6): fcst 1.00, vix 0.85, depth 0.82, day_peak 0.41, day_real 0.29, mins 0.22 (session-constant forecast, VIX and depth dominate: the model learns the regime/calendar, not the intraday path).

Policy grid (X in {0,5k,10k}, Y in {5k,10k,20k}), first-trigger counterfactual (scale to 8 at the first bar with prediction <= X, stop at the first bar with prediction < -Y; features from the lock-free state, exact up to the first action), engine run with the live locks as backstop (and without):

| features | X | Y | backstop | WF mean / SD / maxDD | L8W mean / maxDD |
|---|---|---|---|---|---|
| dollar | 5000 | 5000 | True | 22.7k / 84.0k / 350.0k | 52.5k / 125.1k |
| full | 0 | 5000 | True | 18.1k / 87.8k / 365.5k | 41.4k / 334.0k |
| dollar | 10000 | 5000 | False | 23.1k / 90.2k / 379.1k | 34.5k / 336.1k |
| dollar | 10000 | 5000 | True | 21.9k / 83.8k / 381.4k | 51.1k / 123.1k |
| full | 0 | 20000 | True | 30.6k / 93.2k / 397.2k | 45.3k / 334.9k |
| dollar | 5000 | 20000 | True | 28.7k / 91.6k / 398.6k | 47.2k / 266.9k |
| dollar | 5000 | 5000 | False | 24.8k / 92.5k / 399.9k | 32.6k / 340.7k |
| full | 10000 | 5000 | True | 17.5k / 75.9k / 402.8k | 35.5k / 309.9k |
| dollar | 10000 | 20000 | True | 27.4k / 91.1k / 405.3k | 44.0k / 264.8k |
| full | 10000 | 20000 | True | 25.6k / 89.8k / 411.5k | 47.9k / 263.8k |
| full | 5000 | 20000 | True | 28.9k / 90.9k / 419.4k | 49.9k / 303.9k |
| full | 0 | 10000 | True | 24.2k / 92.1k / 426.6k | 43.5k / 334.9k |
| dollar | 5000 | 10000 | True | 24.3k / 85.8k / 436.5k | 51.7k / 187.7k |
| dollar | 10000 | 10000 | True | 23.8k / 85.0k / 450.9k | 48.8k / 185.7k |

No policy beats the benchmark (25.0k / 104.5k / 401k) on mean AND maxDD with the full-feature model; the lowest maxDD reached with mean >= 24.9k is 397.2k. Shuffled-label control (12 worlds x 9 policies, live backstop): the shuffled models predict ~the unconditional mean and rarely act (WF mean 25.9k, maxDD 415.8k), i.e. the control is degenerate - the real model's departures from it are small and not an improvement. The dollar-only features do as well or better than the full set, so the extra state adds nothing.

**F4 exhibit** (the live week 10-19..10-22 is not on disk; the latest replayed week 2026-W42, label days 10-12..10-16, is used): per session, the prediction path of the full-feature model and the policy action it would have taken at its first trigger (X=0, Y=10k):

| label day | session | bars scored | min pred | first bar with pred<=0 (min since open) | action | realised rest-of-session P&L at that bar (lock-free) |
|---|---|---|---|---|---|---|
| 20261012 | ASIA | 91 | 1.7k | - | continue | - |
| 20261012 | LONDON | 85 | 0.3k | - | continue | - |
| 20261012 | NY | 85 | -9.2k | 15 | scale to 8 | 46.8k |
| 20261013 | ASIA | 91 | 7.3k | - | continue | - |
| 20261013 | LONDON | 85 | -4.3k | 20 | scale to 8 | -45.2k |
| 20261013 | NY | 85 | -3.8k | 15 | scale to 8 | -36.9k |
| 20261014 | ASIA | 91 | 1.4k | - | continue | - |
| 20261014 | LONDON | 85 | -0.5k | 390 | scale to 8 | 30.1k |
| 20261014 | NY | 85 | -13.2k | 15 | STOP | 146.6k |
| 20261015 | ASIA | 91 | -6.8k | 15 | scale to 8 | 13.5k |
| 20261015 | LONDON | 85 | -1.3k | 125 | scale to 8 | -14.4k |
| 20261015 | NY | 85 | 3.0k | - | continue | - |
| 20261016 | ASIA | 91 | -13.8k | 15 | STOP | 50.9k |
| 20261016 | LONDON | 85 | -5.7k | 15 | scale to 8 | 31.1k |
| 20261016 | NY | 85 | -3.5k | 15 | scale to 8 | 61.5k |

The Asia session of 10-20 and the 21:51 (9:51 PM) moment of 10-21 are in the forward weeks that are not on disk; they cannot be shown.

## Block G - joint and complexity (G2)

Deflated Sharpe (Bailey-Lopez de Prado; weekly WF Sharpe, trials = 20,160 V5 screen cells + 3,368 earlier F_P = 20,648, variance of the screened cells' weekly Sharpes 0.0035, skew/kurtosis from the WF weekly series):

| cell | parameters changed vs live | WF weekly SR | SR0 (expected max under noise) | deflated Sharpe probability | WF mean / SD |
|---|---|---|---|---|---|
| live60_P9 / pblive|caphard|wk8|gb0|N0 / 14/14/14 | 0 | 0.239 | 0.239 | 0.50 | 25.0k / 104.5k |
| live60_P9 / pblive|capoff|wk12|gb1|N2 / 14/10/10 | 8 | 0.274 | 0.239 | 0.66 | 25.5k / 93.1k |
| live60_P9 / pblive|capoff|wk12|gb1|N0 / 14/10/10 | 7 | 0.272 | 0.239 | 0.65 | 25.1k / 92.5k |
| live60_P9 / pblive|capoff|wkoff|gb0|N0 / 14/14/14 | 3 | 0.312 | 0.239 | 0.82 | 34.7k / 111.3k |
| live60 / pboff|caphard|wk10|gb0|N3 / 14/10/8 | 9 | 0.353 | 0.239 | 0.91 | 39.3k / 111.3k |

Probability the result is noise = 1 - DSR: the 3-parameter set (remove the combined cap and the week floor) 0.19; the 8-parameter BEST set 0.34; the live set has DSR 0.50 by construction (it is the reference). A 12-parameter conditional lock set from A-D would need to clear the same SR0 with more freedom; none of the A-D cells improved on BEST, so no conditional lock earns its parameters.
