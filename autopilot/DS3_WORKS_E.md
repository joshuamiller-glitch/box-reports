# DS3_WORKS_E - T-WORKS / P7 FIX, W-E (families E multi-timeframe trend health, F participation, G pullback anatomy, H leg anatomy), page 2026-11-11 22:43Z
Label: PRE-PROOF, post-hoc, Shadow only, no PASS claim. Prereg autopilot/WORKS_E_PREREG.md (sha in DECISIONS.md 19:19Z, logged before any cell was scored). Code code/th_works_e/ (e0_flow, e1_table, e2_screen, e3_full, e_hooks, e_sets, e_chain, e_score, e_page).

## What exists
1. The shared P7 signal feature table is /mnt/l2/l2vast/_th_works/p7_signal_features.parquet: 6212 P7 signals 2023-04-03..2026-11-05, key utc_epoch_s, taken flag, session, side, base lots (live table 7/4/4), entry price, trade net if taken, shadow base-lot net, the week flags (worst-20 weeks of the 3.5-year P7 net, L6M worst-5, live week) and 64 causal feature columns of families E, F, G, H. Taken = 5011 (LPB_BASE trades plus the 53 frozen live-week trades). Untaken = 1201. CAVEAT: the untaken rows are S1B-COMB P7 signals that LPB_BASE does not contain; they include engine-divergence differences (different re-entry paths between the two engine runs), not only blocks by the day cap, the blackout or the lock, so taken=0 does not always mean the live panel refused the signal.
2. All features are computed from the 1-min bars (NQ, roll-adjusted) that closed at or before the signal second, plus 1-min flow bars (volume, aggressor delta, prints of 10 or more contracts) built from the state-base tick arrays. Legs and pullbacks come from a causal zigzag at 1.0 ATR(5-min) (pushes inside a leg at 0.4 ATR). Features at every P7-session minute boundary and both sides (1.9 million rows) are in /mnt/l2/l2vast/_th_works/e/full_*.parquet so the exact engine can look up the feature at any re-entry second; a signal that falls a few seconds after the bar boundary uses the last closed bar, identical to the shared table (checked: 6,211 of 6,212 rows match to 1e-6).

## First-order screen (P7 only, equal-mean drawdown cut, skip and half, P7 Asia then all sessions)
Each family has 312 cells per scope (feature x tail x percentile x action). Objective = mean of the equal-mean maxDD cut in L6M and HOLD on weekly P7 P&L; a cell must keep a positive mean in both windows. Family null = 300 within-month-and-session permutations of the feature rows with fixed thresholds, max objective over the family; forward-only placebo = the feature of the signal k positions earlier, k = 1..40, max over k.

| scope | family | best observed objective | null median / 95th / 99th (permutation) | forward-lag placebo 95th | verdict |
|---|---|---|---|---|---|
| ASIA | E | 28.3 | 34.1 / 49.0 / 53.9 | 46.4 | inside the null |
| ASIA | F | 20.3 | 28.3 / 44.6 / 51.2 | 42.5 | inside the null |
| ASIA | G | 30.8 | 26.3 / 41.7 / 46.1 | 40.9 | inside the null |
| ASIA | H | 36.1 | 27.5 / 42.1 / 47.4 | 44.7 | inside the null |
| ALL | E | 34.4 | 37.6 / 52.1 / 62.3 | 49.8 | inside the null |
| ALL | F | 28.8 | 31.0 / 47.9 / 55.0 | 49.9 | inside the null |
| ALL | G | 32.8 | 29.4 / 46.8 / 57.9 | 42.1 | inside the null |
| ALL | H | 36.7 | 31.6 / 49.8 / 57.2 | 46.6 | inside the null |

Plain reading: in every family and both scopes the best cell is at or below the 95th percentile of what random feature assignments give as their best cell (the median of the null maximum is 26-38, the best observed is 20-37). First-order, none of the E, F, G, H features is distinguishable from noise as a skip/half rule on P7. The cells below are therefore registered and sent to exact only because the order requires it, not because they passed a null.

## Registered top-3 per family and scope (first-order; cut = P7 weekly maxDD cut %, d = mean change per week $)
| id | rule (P7 signal second) | action | obj | cut L6M | cut HOLD | acted | total P&L effect 3.5y $ | removed net in worst-20 weeks (n) | removed net other weeks (n) | live week acted n / removed net |
|---|---|---|---|---|---|---|---|---|---|---|
| E1A | e_ac1_120 >= 0.133 (ASIA) | skip | 28.3 | 24.7 | 23.3 | 225 | 80529 | -101372 (47) | 20844 (178) | 4 / 7818 |
| E2A | e_sw15_dist <= -0.0915 (ASIA) | skip | 19.4 | 15.7 | 15.7 | 224 | 23284 | -57058 (28) | 33774 (196) | 2 / 3351 |
| E3A | e_sw60_dist >= 9.23 (ASIA) | skip | 18.9 | 22.9 | 21.0 | 447 | -100549 | -103717 (58) | 204266 (389) | 6 / -3116 |
| F1A | f_leg_vpm_rel >= 1.78 (ASIA) | skip | 20.3 | 20.8 | 20.8 | 225 | -38926 | -74419 (37) | 113346 (188) | 0 / 0 |
| F2A | f_leg_delta_share <= -0.0114 (ASIA) | skip | 15.4 | 13.1 | 13.1 | 225 | -70837 | -38828 (29) | 109665 (196) | 1 / -2424 |
| F3A | f_leg_vpm_rel >= 1.78 (ASIA) | half | 14.1 | 13.4 | 13.4 | 225 | -14174 | -32516 (37) | 46690 (188) | 0 / 0 |
| G1A | g_push_min <= 3 (ASIA) | skip | 30.8 | 24.5 | 24.5 | 228 | -26305 | -20928 (28) | 47233 (200) | 0 / 0 |
| G2A | g_pb_vel_over_push_vel <= 0.188 (ASIA) | skip | 19.5 | 19.6 | 12.7 | 449 | -68265 | -109486 (73) | 177751 (376) | 7 / 26676 |
| G3A | g_push_min <= 5 (ASIA) | half | 17.5 | 18.6 | 18.6 | 488 | -34174 | -25908 (64) | 60082 (424) | 4 / 3132 |
| H1A | h_leg_age <= 3 (ASIA) | skip | 36.1 | 32.3 | 32.3 | 246 | -56394 | -28825 (33) | 85219 (213) | 2 / 16722 |
| H2A | h_leg_slope_atr_min >= 0.449 (ASIA) | skip | 34.0 | 22.6 | 22.6 | 225 | 33719 | -43357 (27) | 9637 (198) | 0 / 0 |
| H3A | h_leg_atr <= 1.43 (ASIA) | skip | 31.9 | 40.9 | 40.9 | 674 | -193636 | -92570 (82) | 286206 (592) | 13 / 10245 |
| E1L | e_vwap_sl60 >= 1.16 (ALL) | skip | 34.4 | 38.3 | 38.3 | 1487 | -182128 | -252322 (156) | 434450 (1331) | 7 / 147 |
| E2L | e_vr5_60 <= 0.736 (ALL) | half | 33.4 | 36.1 | 36.1 | 1487 | -83802 | -106729 (160) | 190530 (1327) | 16 / -2450 |
| E3L | e_ac1_120 >= 0.128 (ALL) | skip | 31.7 | 23.4 | 21.6 | 496 | 116065 | -126819 (67) | 10754 (429) | 5 / 7704 |
| F1L | f_lastpush_delta_share <= 0.0442 (ALL) | skip | 28.8 | 35.5 | 34.9 | 1487 | -170933 | -206689 (168) | 377622 (1319) | 16 / 16311 |
| F2L | f_lastpush_delta_share <= 0.0442 (ALL) | half | 22.2 | 22.7 | 22.7 | 1487 | -8577 | -101863 (168) | 110440 (1319) | 16 / 6550 |
| F3L | f_leg_delta_agree <= 0 (ALL) | skip | 22.2 | 23.4 | 23.4 | 629 | -140519 | -69999 (62) | 210519 (567) | 7 / -4766 |
| G1L | g_push_min <= 4 (ALL) | skip | 32.8 | 35.9 | 33.5 | 1012 | -144554 | -80650 (103) | 225204 (909) | 7 / 12160 |
| G2L | g_push_min <= 4 (ALL) | half | 22.6 | 20.5 | 20.5 | 1012 | -18374 | -35450 (103) | 53824 (909) | 7 / 4288 |
| G3L | g_pb_vel_over_push_vel <= 0.206 (ALL) | skip | 22.1 | 22.0 | 22.0 | 992 | -21184 | -169506 (123) | 190690 (869) | 9 / 22097 |
| H1L | h_leg_pts >= 59 (ALL) | skip | 36.7 | 52.7 | 7.5 | 1490 | -25251 | -166435 (185) | 191686 (1305) | 38 / 83230 |
| H2L | h_leg_push_min <= 4 (ALL) | skip | 32.8 | 35.9 | 33.5 | 1012 | -144554 | -80650 (103) | 225204 (909) | 7 / 12160 |
| H3L | h_leg_pts >= 59 (ALL) | half | 31.4 | 21.9 | 21.9 | 1490 | 36316 | -79032 (185) | 42715 (1305) | 38 / 36281 |

Negative removed net = the rule removes losses (good); positive = removes profit. Total P&L effect = minus the sum removed over the 3.5 years (positive = the rule added P&L before any lot reallocation). The sign of the effect is mixed across cells and none survives its family null; the large-leg cell H1L (leg >= 59 pts, skip) cuts L6M drawdown by 53% but removes $83k of the frozen live week (the trend week).

## Which flag separates the frozen trend week from the worst weeks (taken P7, mean of the signed feature)
| feature | live week mean | worst-20 weeks mean | other weeks mean | live minus worst, in SD |
|---|---|---|---|---|
| h_leg_pts | 105.717 | 60.337 | 51.855 | 0.99 |
| g_pb_vol_share | 0.233 | 0.314 | 0.306 | -0.45 |
| g_aligned | 0.811 | 0.595 | 0.632 | 0.45 |
| g_pb_vel_over_push_vel | 1.183 | 0.741 | 0.838 | 0.44 |
| e_sw60_run | 0.792 | 1.321 | 1.014 | -0.38 |
| g_pb_depth_atr | 0.818 | 1.056 | 1.035 | -0.35 |
| e_sw15_run | 1.642 | 1.197 | 1.248 | 0.30 |
| e_sw60_dist | 1.003 | 3.397 | 3.385 | -0.29 |
| g_depth_max | 0.420 | 0.501 | 0.508 | -0.28 |
| h_leg_slope_atr_min | 0.190 | 0.246 | 0.248 | -0.27 |

(One live week against twenty bad weeks is one observation; this table says what differed, not what is predictive.)

## Exact promotion status
| set | ref | window | exact cut % | d mean/week | eq cut % |
|---|---|---|---|---|---|
| WEJ_E1A | JN04RM | L1M | 42.8 | 3859 | 47.6 |
| WEJ_E1A | JN04RM | L3M | 16.1 | 2096 | 23.2 |
| WEJ_E1A | JN04RM | L6M | 16.1 | 1615 | 23.2 |
| WEJ_E1A | LPB | L1M | 69.8 | -11941 | 68.2 |
| WEJ_E1A | LPB | L3M | 54.7 | -2334 | 52.3 |
| WEJ_E1A | LPB | L6M | 54.7 | -1087 | 52.3 |
| WEL_E1A | JN04RM | L1M | -36.2 | -307 | -34.9 |
| WEL_E1A | JN04RM | L3M | -35.8 | 1596 | -34.5 |
| WEL_E1A | JN04RM | L6M | -35.8 | 166 | -34.5 |
| WEL_E1A | LPB | L1M | 28.1 | 6854 | 23.4 |
| WEL_E1A | LPB | L3M | 26.7 | 2906 | 21.9 |
| WEL_E1A | LPB | L6M | 26.7 | -1151 | 21.9 |
| WEJ_E2A | JN04RM | L1M | 27.5 | 1066 | -63.6 |
| WEJ_E2A | LPB | L1M | 61.7 | -5820 | 13.6 |
| WEL_E2A | JN04RM | L1M | -54.5 | -3921 | -232.2 |
| WEL_E2A | LPB | L1M | 18.4 | 3241 | -75.6 |
| WEJ_H1A | JN04RM | L1M | -3.5 | -314 | nan |
| WEJ_H1A | LPB | L1M | 45.4 | -12066 | nan |

Exact sets: 23 registered cells (H2L duplicates G1L) x 2 references = 46 sets (WEJ_* on JN04RM, WEL_* on LPB_EMPTY), one set per job through state_sizer_ijk jbjobs with the e_hooks signal-second lookup applied in trend_size before the JN04 dials. Months DONE so far: 19. Chain scheduler (restart-safe, launches when MemAvailable >= 62 GB, at most 3 W-E jobs, runs until 2026-11-12 12:00Z): pids 2274304 2274470; W-E jobs running now 4; log /mnt/l2/l2vast/_th_works/e/logs/chain.log. A set continues past L6M only if its exact L6M cut is positive (e_gate.csv).

## Behavioural scorecard (standing principle 2026-11-11 19:45Z)
A cell counts only if full stops, give-backs and same-side repeats each fall by at least half in L6M without skipping trend-week winners. On first-order numbers H1L fails the trend-week test (it removes $83k of the frozen live week) and most other registered cells act on live-week trades; the registered E-H cells carry no stop, give-back or repeat logic of their own (they are entry filters), so the scorecard is expected to show little change in full stops and give-backs. W-Q tool code/th_works_q/behavior_scorecard.py is run per promoted set once its L6M is complete; output below.
### WEJ_E1A
```
WEJ_E1A L6M (stack, per week): full stops 25.4/wk $-38085; give-backs 10.0/wk (9.8 round-trips) realised $-11406, forgone vs target $28215; same-side losing runs max 13, p95 6, $-42040 lost on 3rd-and-later; no-new-evidence re-entries 42.6/wk $2165; recoveries cut 14.9/wk $38698, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $9077/wk, losers avoided $10648/wk, net +634 $/wk; pnl $20418/wk.
WEJ_E1A HOLD: months missing (6 of 12), window not scored
WEJ_E1A PRE: months missing (17 of 17), window not scored
WEJ_E1A X': months missing (10 of 10), window not scored

```
### WEL_E1A
```
WEL_E1A L6M (stack, per week): full stops 24.5/wk $-40052; give-backs 9.2/wk (9.1 round-trips) realised $-14152, forgone vs target $35325; same-side losing runs max 12, p95 6, $-51441 lost on 3rd-and-later; no-new-evidence re-entries 37.8/wk $396; recoveries cut 13.8/wk $47391, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $6099/wk, losers avoided $6833/wk, net +1193 $/wk; pnl $20976/wk.
WEL_E1A HOLD: months missing (6 of 12), window not scored
WEL_E1A PRE: months missing (17 of 17), window not scored
WEL_E1A X': months missing (10 of 10), window not scored

```

## Throughput
W-E adopted the W-T shared-memory month cache (TP_ENGINE=1 via tp_launch, launch gate lowered from 62 to 25 GB, tp_admit request WORKS_JN05, at most 3 workers). Identity check on my own driver: WEJ_H1A 202610 under TP_ENGINE=1 vs the recorded run, 845 vs 845 trades, trade-for-trade IDENTICAL. Before adoption W-E finished 1 cell-month in the first hour (the gate at 62 GB never opened). Box-wide rate now: window 3.0 h: 501 cell-months finished = 167.0 /h total; mean engine secs per cell 131 {'PTR': 198, 'WB': 188, 'ZJ': 28, 'WM': 17, 'WA': 17, 'WI': 14, 'WG': 12, 'WEL': 9, 'WEJ': 8, 'EC': 7, 'WC': 3}

## Not done yet
Asymmetric-bracket cells (60/45, 60/90 by flag) and the late-entry swing stop (D7) are exact-only and are queued after the skip/half stage; the flag separation by persistence across weeks, and the "trend weeks" comparison beyond the live week, wait for more exact output. DS3_WORKS_E.md is regenerated by code/th_works_e/e_page.py every 4 hours from 23:00Z until the final at 2026-11-12 12:00Z.
