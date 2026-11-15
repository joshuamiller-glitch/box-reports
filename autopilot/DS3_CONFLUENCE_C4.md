# DS3_CONFLUENCE_C4.md - C4 'the checklist as the signal' (W-CF6), 2026-11-15

**VERDICT (data ends 2026-10-30; grid-level screen, exact engine pending): no checklist-as-signal book is a lead except possibly Asia standard bracket k=5 (+1.39 pts = +$28 per contract-trade after 1 pt slippage and fees, 552 entries over 2024-10..2026-10, above all 50 shuffled-outcome reruns, 99th percentile of random-time books, all three shifted-session controls negative) and it has ZERO entries in L3M and L6M because the training-window clusters that carried it have faded (3 clusters kept in recent months, k=5 cannot fire); London, NY AM and NY PM are at or below the random-time and shuffle bars (NY PM std k=3 +0.41 pts pctl 0.84 / 0.82; NY PM forecast k=3 +1.76 pts pctl 0.69 / 0.76; London forecast k=5 +3.57 pts on 84 entries). The planted-edge check recovered the planted effect in London, NY AM and (partly) NY PM but NOT in Asia, so the Asia result cannot be treated as 'checked': the mechanism is a weak detector of a conjunctive edge (details below). No PASS claim.**

## What was built
Minute-grid panel (code/th_confl_cf6/c4_panel.py): at every minute of the four D7 session windows (Asia 18:00-02:00, London 02:00-08:30, NY AM 09:30-12:00, NY PM 12:00-15:00 ET; Jan-2023 on; 3,910 session-days x 150-480 minutes) the signed state of 120 public indicator conditions (W-CF2 block5 states on NQ, ES, RTY, YM x 1/5/15-min x EMA stack, hold-21, RSI, CCI, MACD, MACD rising, Supertrend, ADX/DI, VWAP side, squeeze momentum; completed bars only). Redundancy clusters (outcome-free, average-linkage on |corr| >= 0.5 of the sign series): 13 clusters (by instrument and family: 1-min MACD rising, 15-min MACD, 5-min oscillator group NQ/ES and RTY/YM, trend-level groups per index, ...). Cluster vote = mean member state >= +0.5 long / <= -0.5 short. NOTE: this panel holds indicator states only; the full W-CF3 library (21k conditions at signals) cannot be evaluated at arbitrary minutes (levels, profile, tape, L2, options, counting schools are signal-time columns). Counting-school states (ICT / DeMark / Brooks) and level states are the next additions.

Outcomes on the grid (both sides, every minute): entry at the open of the next 1-min bar, stop first when both levels fall in one minute, time stop 120 min or window end, no entries in the last 15 min of a window, cost 1.0 pt + $4.84 per contract. Two brackets: STANDARD stop 30 / target 60 pts; FORECAST-SCALED stop 0.3 F / target 0.6 F with F = session-range forecast (T-RANGE2 fc_r2_har, read at the session open, pred x price) clipped to 15-80 / 30-160 pts. (W-D10's trade-horizon coefficient table is a different object, per-trade horizon ranges, not wired yet: use of T-RANGE2 forecasts is the stated stand-in.)

Walk-forward rule per session and test month (2024-10 .. 2026-10, 25 months): TRAINING = trailing 12 months only. For each cluster: mean outcome of 'enter the side the cluster votes' at its agreement minutes (every 5th minute from minute 15 of the window), day-clustered t; keep |t| >= 2 with >= 200 samples; direction = sign of the mean (a negative mean makes the cluster a contrarian vote). ENTRY = first minute (not before minute 15, score >= k on 5 consecutive minutes) per side per session window and day at which at least k kept clusters agree on a side (k = 3 / 4 / 5); one entry per side per window. The kept set refits monthly; consecutive-month overlap of the kept (cluster, direction) sets is 0.90 Asia, 0.83 London, 0.71 NY AM, 0.63 NY PM (Jaccard).

## Results, ALL months (2024-10..2026-10), standard and forecast brackets, 1 contract. pctl = share of controls the real book beats (>= 0.95 needed on BOTH random-time and shuffle). Shifted = the same entry minutes scored against the outcomes of the day 11/23/37 sessions later (mean pts).

| session   | bracket   |   k |   entries |   mean pts |   mean $ |   win rate |   random-time mean pts |   pctl random |   pctl shuffle (50) |   pctl shuffle total |   shift 11 |   shift 23 |   shift 37 |   mean pts no W44 |
|:----------|:----------|----:|----------:|-----------:|---------:|-----------:|-----------------------:|--------------:|--------------------:|---------------------:|-----------:|-----------:|-----------:|------------------:|
| asia      | std       |   3 |      1023 |      -0.53 |   -10.52 |       0.41 |                  -1.07 |          0.72 |                0.9  |                 0.92 |       0.43 |      -1.19 |      -0.71 |             -0.36 |
| asia      | std       |   4 |       713 |       0.44 |     8.74 |       0.46 |                  -1.44 |          0.96 |                1    |                 0.96 |       0.41 |      -1.64 |      -1.51 |              0.44 |
| asia      | std       |   5 |       552 |       1.39 |    27.71 |       0.47 |                  -1.13 |          0.99 |                1    |                 1    |      -0.52 |      -2.09 |      -1.2  |              1.39 |
| asia      | fc        |   3 |       958 |      -0.05 |    -0.93 |       0.46 |                  -1.02 |          0.75 |                0.84 |                 0.84 |      -0.54 |      -0.78 |      -2.8  |              0.29 |
| asia      | fc        |   4 |         0 |            |          |            |                        |               |                     |                      |            |            |            |                   |
| asia      | fc        |   5 |         0 |            |          |            |                        |               |                     |                      |            |            |            |                   |
| london    | std       |   3 |      1076 |      -0.81 |   -16.13 |       0.39 |                  -1.23 |          0.66 |                0.7  |                 0.7  |      -1.03 |      -0.43 |      -1.13 |             -0.69 |
| london    | std       |   4 |      1046 |      -2.04 |   -40.76 |       0.39 |                  -1.25 |          0.22 |                0.14 |                 0.08 |      -0.65 |      -0.15 |      -0.63 |             -1.84 |
| london    | std       |   5 |       906 |      -0.25 |    -5.1  |       0.41 |                  -1.31 |          0.82 |                0.82 |                 0.8  |      -0.25 |      -0.38 |       0.95 |             -0.25 |
| london    | fc        |   3 |       438 |      -3.42 |   -68.5  |       0.42 |                  -0.99 |          0.16 |                0.08 |                 0.16 |      -1.12 |       1.09 |      -4    |             -3.42 |
| london    | fc        |   4 |       190 |       1.26 |    25.23 |       0.46 |                  -1.28 |          0.8  |                0.82 |                 0.8  |      -3.3  |       3.47 |      -1.79 |              1.26 |
| london    | fc        |   5 |        84 |       3.57 |    71.5  |       0.51 |                  -0.71 |          0.89 |                0.94 |                 0.86 |      -5.29 |      -3.98 |       2.99 |              3.57 |
| nyam      | std       |   3 |       375 |      -2.21 |   -44.21 |       0.34 |                  -1.47 |          0.38 |                0.18 |                 0.38 |      -3.54 |      -2.29 |      -0.06 |             -2.21 |
| nyam      | std       |   4 |       224 |      -2.94 |   -58.72 |       0.33 |                  -1.7  |          0.32 |                0.16 |                 0.42 |      -2.2  |      -3.75 |       0.63 |             -2.94 |
| nyam      | std       |   5 |       133 |      -5.5  |  -109.92 |       0.32 |                  -1.42 |          0.1  |                0.14 |                 0.3  |      -6.98 |      -7.51 |      -1.04 |             -5.5  |
| nyam      | fc        |   3 |         0 |            |          |            |                        |               |                     |                      |            |            |            |                   |
| nyam      | fc        |   4 |         0 |            |          |            |                        |               |                     |                      |            |            |            |                   |
| nyam      | fc        |   5 |         0 |            |          |            |                        |               |                     |                      |            |            |            |                   |
| nypm      | std       |   3 |       478 |       0.41 |     8.28 |       0.38 |                  -1.37 |          0.84 |                0.82 |                 0.84 |      -0.33 |       0.47 |      -0.17 |              0.32 |
| nypm      | std       |   4 |       421 |      -1.91 |   -38.17 |       0.35 |                  -1.61 |          0.41 |                0.28 |                 0.26 |      -0.67 |       0.24 |      -0.81 |             -2.14 |
| nypm      | std       |   5 |       367 |      -2.3  |   -45.98 |       0.34 |                  -1.31 |          0.3  |                0.32 |                 0.2  |       0.94 |       0.54 |      -5.4  |             -2.58 |
| nypm      | fc        |   3 |       257 |       1.76 |    35.23 |       0.45 |                  -0.77 |          0.69 |                0.76 |                 0.88 |      -6.27 |      -8.06 |       2.96 |              2.09 |
| nypm      | fc        |   4 |       173 |      -0.94 |   -18.88 |       0.43 |                  -0.87 |          0.48 |                0.7  |                 0.56 |      -1.33 |      -3.18 |      -2.17 |             -0.94 |
| nypm      | fc        |   5 |        79 |      -9.75 |  -194.94 |       0.34 |                  -0.11 |          0.14 |                0.04 |                 0.08 |      -9.42 |       3.55 |      -6.09 |             -9.75 |

### The one candidate: Asia, standard bracket, windows (recent first)

|   k | win   |   n |   mean_pts |   mean_usd |   wr |   rand_mean_pts |   pctl_vs_random_mean |
|----:|:------|----:|-----------:|-----------:|-----:|----------------:|----------------------:|
|   4 | ALL   | 713 |       0.44 |       8.74 | 0.46 |           -1.44 |                  0.96 |
|   4 | L3M   |   0 |            |            |      |                 |                       |
|   4 | L6M   |   0 |            |            |      |                 |                       |
|   4 | PRE   | 383 |       0.23 |       4.56 | 0.45 |           -1.61 |                  0.91 |
|   4 | GAP   | 178 |      -0.16 |      -3.24 | 0.48 |           -1.07 |                  0.67 |
|   4 | HOLD  | 152 |       1.66 |      33.28 | 0.43 |           -0.93 |                  0.83 |
|   5 | ALL   | 552 |       1.39 |      27.71 | 0.47 |           -1.13 |                  0.99 |
|   5 | L3M   |   0 |            |            |      |                 |                       |
|   5 | L6M   |   0 |            |            |      |                 |                       |
|   5 | PRE   | 248 |       1.62 |      32.32 | 0.47 |           -1.75 |                  0.96 |
|   5 | GAP   | 178 |       1.53 |      30.69 | 0.49 |           -1.07 |                  0.92 |
|   5 | HOLD  | 126 |       0.72 |      14.41 | 0.45 |           -0.9  |                  0.74 |

L3M / L6M have no entries: the kept-cluster set shrank from 7-8 (2025) to 3 (2026), below k.

## Planted-edge check (H1/A6), grid level

Plant +0.3 R (9 pts on the 30-pt stop) on the outcome of side s at every minute where THREE chosen conditions (NQ 5-min Supertrend, RTY 5-min ADX/DI, YM 15-min MACD; clusters 2, 4, 5 in 0-based numbering) all agree with s, rerun the whole walk-forward at k = 3. 'diff' = mean pts of the entries minus the mean of the same entries scored on other days (same minute-of-window, 28 shifts); the planted edge should add to diff.

| session | k | diff without plant | diff with plant | gain from the plant |
|---|---|---|---|---|
| asia | 3 | +0.26 | -0.04 | -0.30 (NOT recovered) |
| asia | 4 | +1.41 | +0.68 | -0.73 |
| asia | 5 | +2.44 | +2.22 | -0.22 |
| london | 3 | -0.05 | +1.26 | +1.31 |
| london | 4 | -1.44 | +0.96 | +2.40 |
| london | 5 | +0.08 | +2.32 | +2.24 |
| nyam | 3 | -1.26 | +1.40 | +2.66 |
| nyam | 4 | -2.10 | +1.89 | +3.99 |
| nyam | 5 | -4.62 | +1.37 | +5.99 |
| nypm | 3 | +1.27 | +2.02 | +0.75 |
| nypm | 4 | -0.71 | -0.93 | -0.22 |
| nypm | 5 | -1.22 | +1.14 | +2.36 |

Reading: the pipeline selects the planted clusters (their training t-stats are 4-8), but a k-of-13 vote is a diffuse detector of a three-way conjunction: entries gain only +1 to +6 pts of the +9 planted and in Asia nothing. Per the order: where it does not recover, the pipeline is still wrong for that session; Asia results above are therefore NOT a 'nothing' and NOT a lead. A first version with entry at the FIRST minute of agreement (no warm-up, no persistence) fell on the opposite side (entries piled up in minutes 0-9 with stale states and the planted trio was LESS likely at the entry than at a random minute); the rule above (minute >= 15, 5-minute persistence) was changed BEFORE any of the results reported here and the change is logged in DECISIONS.

## Exact engine (injection hook uw_inject, market entry, 120-min time stop, flat by window end)
Events exported by code/th_confl_cf6/c4_events.py to /mnt/l2/l2vast/_uwbooks/inject/ (C4_ASIA_K5: 552 events; C4_NYAM_K3_PL / _UN: planted vs plain pipeline, NY AM k=3). Sets TL3_UW_C4_ASIA_K5, TL3_UW_C4_NYAM_PL, TL3_UW_C4_NYAM_UN are queued (25 + 6 + 6 months) and waiting behind the TP admission queue; results will be appended when they land. Engine planted-edge check plan: add +0.3 R x risk post hoc to engine trades whose entry bar had the planted trio true, in both the planted and the plain run, and require the scoring chain to recover the difference (A6 method).

## Exact engine, NY AM planted vs plain (L6M 2026-05..10, hook uw_inject, JN05W2 stack, 2026-11-15 results; data end 2026-10-30)

**ENGINE PLANTED-EDGE CHECK (H1), NY AM k=3, standard bracket 30/60, 2 lots: PASSES the chain, with a stated limit.** (a) The pipeline fed planted outcomes selects the planted clusters and trades: 129 engine trades in L6M (22/24/21/23/22/17 per month) against 11 trades (one month) when run on the unplanted outcomes, because the unplanted training window kept too few clusters. (b) Post-hoc +0.3 R x risk ($ = lots x 30 x 20) on the engine trades whose entry event had the trio (NQ 5-min Supertrend, RTY 5-min ADX/DI, YM 15-min MACD) agreeing with the side: 29 of 129 trades flagged (22 pct), total $3,946 -> $14,026 (+$10,080 = exactly 0.3 x $600 x 2 lots x 28-29 trades), mean $31 -> $109 per trade; every event matched to its engine trade (100 pct). So events -> hook -> engine -> trade matching -> scoring reproduce a known planted effect exactly. (c) Limit: the plant is post hoc on engine trades and in the grid outcomes; the engine itself does not see it. In the raw engine the trio-true trades earned +$355 (29 trades) against -$64 for the others (100 trades) with no plant at all, i.e. the trio is a real trend-state enrichment in L6M for this entry rule, so the PL run is not a pure null. (d) Raw engine result of the planted-pipeline book without any post-hoc plant: 129 trades, +$3,946 in six months (mean $31, win 43 pct): not a result about the checklist idea, the pipeline saw the planted outcomes.

The plain pipeline (UN) traded only August 2026 (11 trades, +$5,719, win 55 pct, trio share 27 pct): in the other five L6M months its training window kept fewer than 3 clusters, so the NY AM book is silent in the recent months: NO engine evidence for a NY AM checklist book. Asia k=5 (TL3_UW_C4_ASIA_K5, 552 events 2024-10..2026-10, no L3M/L6M events) is running as a STACK-EFFECT measurement only (10 of 25 months done at the time of writing); its recent-window verdict is empty by construction. Code c4_engine_score.py.
