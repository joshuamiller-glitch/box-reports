
## LIVE-VS-MODEL COMPARISON - BLIND-W45 (ZL-1 compare_live_model.py, 2026-11-06T16:01Z)

BASE = sealed prediction file (BASE-4 engine, per-period config) vs live StratTrades_DS7_<acct>.csv sha d918fee4e83e1852. Live rows are slices aggregated to trades by (book, exit time, exit name, side); entry/exit times ET wall clock; net = pnlNet. Match key = signal second, +-2 s (per-book override {P6: 47}), same book and side. Realised closed-trade maxDD only (no open-trade MAE).

**the engine predicted +34879$ for the week; live made +104095$; the gap (+69216$) is explained by these contributions to live minus engine: trades live took that the engine did not (65) +70005$; different exit type on matched trades +34760$; trades the engine took that live did not (60) -29887$; fill/size differences on matched same-exit trades -5661$; the engine is NOT a faithful model of live D7 for this week (trade match below threshold, net gap above threshold, exit-type agreement below threshold, maxDD gap above threshold).**

### Totals and trade count

| | engine | live | delta (live-engine) |
|---|---|---|---|
| net $ | 34879 | 104095 | +69216 |
| trades | 182 | 187 | +5 |
| matched exact (+-tol) | 120 | | |
| matched near (<=120s, timing slip) | 2 | | |
| engine-only | 60 | | |
| live-only | 65 | | |
| matched / union | 49.4% | | |

Longs/shorts engine 82/100, live 85/102. Max lots in a trade: engine 7.0, live 10.0. Worst trade $: engine -5861, live -6510. Signal-second offset on matches: mean -0.72 s, median 0.00 s, max abs 63.0 s.

Match rate by tolerance on the signal second (same book and side, greedy nearest; live entryTime = FILL of the first slice, so +-2 s is expected to under-match): +-2 s: 120 pairs, matched/union 48.2%, share of engine trades 65.9%; +-60 s: 121 pairs, matched/union 48.8%, share of engine trades 66.5%; +-120 s: 122 pairs, matched/union 49.4%, share of engine trades 67.0%; +-300 s: 125 pairs, matched/union 51.2%, share of engine trades 68.7%; +-900 s: 128 pairs, matched/union 53.1%, share of engine trades 70.3%. +-300 and +-900 s are diagnostics only. The verdict criteria use the near tolerance (near_tol_sec = 120 s), as frozen.

### Per book

| book | n_pred | pred_net | pred_lots | n_live | live_net | live_lots | d_n | d_net |
|---|---|---|---|---|---|---|---|---|
| A7 | 18.0 | 9067.2 | 20.0 | 23 | -1415.0 | 23 | 5.0 | -10482.2 |
| H7 | 19.0 | 9266.2 | 46.0 | 3 | -770.0 | 4 | -16.0 | -10036.2 |
| K7 | 61.0 | 10319.1 | 70.0 | 64 | 16065.0 | 76 | 3.0 | 5745.9 |
| M7 | 29.0 | 2490.3 | 39.0 | 28 | 6015.0 | 37 | -1.0 | 3524.7 |
| O7 | 0.0 | 0.0 | 0.0 | 3 | 660.0 | 3 | 3.0 | 660.0 |
| P7 | 43.0 | 2403.6 | 206.0 | 53 | 86010.0 | 247 | 10.0 | 83606.4 |
| U7 | 7.0 | 6674.6 | 24.0 | 6 | -1755.0 | 19 | -1.0 | -8429.6 |
| X3 | 2.0 | -6215.4 | 4.0 | 3 | -905.0 | 6 | 1.0 | 5310.4 |
| X4 | 2.0 | -1517.4 | 4.0 | 2 | -170.0 | 4 | 0.0 | 1347.4 |
| X5 | 1.0 | 2390.3 | 2.0 | 2 | 360.0 | 4 | 1.0 | -2030.3 |

### Per day (ET calendar date of entry; Sun = Sun night)

| day | n_pred | pred_net | pred_lots | n_live | live_net | live_lots | d_n | d_net |
|---|---|---|---|---|---|---|---|---|
| Sun 11-01 | 5 | 2952.4 | 9.0 | 11 | 22400.0 | 32 | 6 | 19447.6 |
| Mon 11-02 | 26 | -20635.1 | 59.0 | 41 | 13965.0 | 85 | 15 | 34600.1 |
| Tue 11-03 | 65 | 22926.4 | 155.0 | 46 | 8675.0 | 116 | -19 | -14251.4 |
| Wed 11-04 | 59 | 31247.1 | 134.0 | 61 | 43615.0 | 118 | 2 | 12367.9 |
| Thu 11-05 | 27 | -1612.3 | 58.0 | 28 | 15440.0 | 72 | 1 | 17052.3 |

### Engine by config period at entry (P0 old panel, P1 Mon 08:50-13:30, P2 after)

| period | n_pred | pred_net |
|---|---|---|
| P0 | 17 | -10600.7 |
| P1 | 4 | -27.1 |
| P2 | 161 | 45506.4 |

Engine trades not closed by the span end: 0.

### Gap decomposition (live - engine, $)

| component | $ |
|---|---|
| live-only trades | +70005 |
| engine-only trades (sign flipped) | -29887 |
| matched, different exit type | +34760 |
| matched, same exit type (fills/size) | -5661 |
| total | +69216 |

### Exit-type match (matched pairs; rows = engine, cols = live); agreement 64.5% on 121 pairs whose engine exit type is known (engine type other excluded)

| exit_type | target | thl2_cut | policy_cut | lock | stop | flatten | other |
|---|---|---|---|---|---|---|---|
| target | 46 | 3 | 4 | 0 | 0 | 0 | 0 |
| thl2_cut | 5 | 32 | 20 | 1 | 2 | 0 | 0 |
| policy_cut | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| lock | 1 | 1 | 0 | 0 | 0 | 0 | 1 |
| stop | 0 | 3 | 2 | 0 | 0 | 0 | 0 |
| flatten | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| other | 0 | 0 | 0 | 0 | 0 | 0 | 1 |

Exit counts all trades: engine {'target': 84, 'thl2_cut': 85, 'lock': 4, 'stop': 7, 'other': 2}; live {'target': 86, 'thl2_cut': 53, 'policy_cut': 39, 'lock': 3, 'stop': 2, 'other': 4}.

### Fill / slippage deltas on matched pairs by engine exit type (adverse + = live worse)

| type | n | d_net_mean | d_net_per_lot | d_net_sum | d_lots | entry_adv_pts | exit_adv_pts |
|---|---|---|---|---|---|---|---|
| target | 53 | -329.9 | -252.6 | -17485.6 | -0.1 | 3.3 | 10.8 |
| thl2_cut | 60 | 661.5 | 108.8 | 39688.2 | -0.1 | 3.9 | -5.0 |
| lock | 3 | 747.8 | 747.8 | 2243.4 | -0.3 | 3.3 | -33.8 |
| stop | 5 | 893.4 | 617.3 | 4466.9 | 0.0 | 0.6 | -29.7 |
| other | 1 | 186.0 | 186.0 | 186.0 | 0.0 | 6.0 | -12.0 |

### maxDD path (realised, by exit time)

engine maxDD 25893$ (trough Tue 11-03 06:30Z); live maxDD 14490$ (trough Wed 11-04 01:03Z); gap 44.0%.
 Equity-curve correlation on a 49-point grid 0.901; largest |engine-live| 69216$ at Thu 11-05 16:05Z.


### Unmatched trades (by signal second; first 25 each)

engine-only:

| signal_sec | book | side | lots | exit_type | net |
|---|---|---|---|---|---|
| Sun 11-01 23:41Z | H7 | 1 | 3.0 | other | 1378.8 |
| Mon 11-02 03:36Z | K7 | 1 | 1.0 | thl2_cut | -721.1 |
| Mon 11-02 05:53Z | P7 | 1 | 4.0 | thl2_cut | -2659.1 |
| Mon 11-02 07:17Z | X4 | -1 | 2.0 | target | 1590.3 |
| Mon 11-02 07:36Z | K7 | -1 | 3.0 | thl2_cut | -1716.2 |
| Mon 11-02 08:28Z | X5 | -1 | 2.0 | target | 2390.3 |
| Mon 11-02 13:43Z | X3 | 1 | 2.0 | stop | -3107.7 |
| Mon 11-02 16:17Z | M7 | -1 | 1.0 | target | 1232.3 |
| Mon 11-02 16:28Z | H7 | -1 | 1.0 | thl2_cut | -676.2 |
| Tue 11-03 00:15Z | H7 | -1 | 2.0 | thl2_cut | -1238.7 |
| Tue 11-03 01:33Z | H7 | 1 | 2.0 | thl2_cut | -1288.6 |
| Tue 11-03 04:14Z | P7 | -1 | 7.0 | thl2_cut | -3819.3 |
| Tue 11-03 05:57Z | H7 | -1 | 2.0 | thl2_cut | -1103.6 |
| Tue 11-03 05:58Z | P7 | -1 | 4.0 | thl2_cut | 7715.8 |
| Tue 11-03 07:48Z | K7 | 1 | 1.0 | target | 1102.2 |
| Tue 11-03 07:56Z | M7 | 1 | 1.0 | thl2_cut | -563.1 |
| Tue 11-03 08:07Z | P7 | 1 | 4.0 | thl2_cut | -2207.5 |
| Tue 11-03 09:10Z | U7 | 1 | 2.0 | target | 2419.1 |
| Tue 11-03 09:38Z | P7 | 1 | 4.0 | target | 4876.7 |
| Tue 11-03 09:39Z | K7 | 1 | 1.0 | target | 1226.7 |
| Tue 11-03 09:44Z | M7 | 1 | 1.0 | target | 1226.7 |
| Tue 11-03 10:18Z | P7 | 1 | 4.0 | thl2_cut | -2447.3 |
| Tue 11-03 10:23Z | M7 | 1 | 2.0 | thl2_cut | -1372.7 |
| Tue 11-03 11:21Z | K7 | -1 | 1.0 | target | 1037.7 |
| Tue 11-03 11:54Z | M7 | -1 | 2.0 | target | 2464.7 |

live-only:

| entry_ts | book | side | lots | exit_type | net |
|---|---|---|---|---|---|
| Sun 11-01 23:36Z | P7 | 1 | 4 | target | 4805.0 |
| Sun 11-01 23:42Z | K7 | 1 | 3 | target | 3600.0 |
| Mon 11-02 00:11Z | P7 | 1 | 10 | target | 12010.0 |
| Mon 11-02 01:45Z | P7 | 1 | 4 | target | 4810.0 |
| Mon 11-02 03:13Z | A7 | 1 | 1 | lock | -395.0 |
| Mon 11-02 03:48Z | K7 | 1 | 3 | thl2_cut | -1900.0 |
| Mon 11-02 03:50Z | H7 | 1 | 2 | thl2_cut | -1370.0 |
| Mon 11-02 04:03Z | P7 | 1 | 2 | thl2_cut | -1405.0 |
| Mon 11-02 06:45Z | K7 | -1 | 1 | target | 1200.0 |
| Mon 11-02 07:21Z | X4 | -1 | 2 | target | 1600.0 |
| Mon 11-02 09:00Z | X5 | -1 | 2 | thl2_cut | -1405.0 |
| Mon 11-02 10:01Z | P7 | -1 | 3 | target | 3605.0 |
| Mon 11-02 11:58Z | M7 | -1 | 1 | other | 840.0 |
| Mon 11-02 12:20Z | X5 | -1 | 2 | other | 1765.0 |
| Mon 11-02 12:54Z | K7 | -1 | 1 | thl2_cut | -640.0 |
| Mon 11-02 13:20Z | M7 | -1 | 3 | policy_cut | -1775.0 |
| Mon 11-02 13:37Z | X3 | 1 | 2 | target | 2005.0 |
| Mon 11-02 13:38Z | X3 | -1 | 2 | thl2_cut | -1225.0 |
| Mon 11-02 15:02Z | M7 | -1 | 1 | thl2_cut | -575.0 |
| Mon 11-02 15:02Z | P7 | -1 | 4 | policy_cut | -2865.0 |
| Mon 11-02 15:25Z | H7 | 1 | 1 | policy_cut | -600.0 |
| Mon 11-02 15:36Z | K7 | 1 | 1 | policy_cut | -625.0 |
| Mon 11-02 15:54Z | K7 | -1 | 1 | target | 1200.0 |
| Mon 11-02 16:10Z | H7 | -1 | 1 | target | 1200.0 |
| Mon 11-02 16:12Z | K7 | -1 | 1 | target | 1200.0 |


Criteria (pre-stated in blind_cmp_config.json): {"min_matched_frac_of_union": 0.85, "max_abs_net_gap_frac": 0.15, "min_exit_type_agree": 0.8, "max_maxdd_gap_frac": 0.25}. Checks: {'matched': False, 'net': False, 'exits': False, 'dd': False}.
