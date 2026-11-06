
## LIVE-VS-MODEL COMPARISON - BLIND-W45 POST-HOC PE-unthinned+cuts (pe_nb) (ZL-1 compare_live_model.py, 2026-11-06T17:01Z)

BASE = sealed prediction file (BASE-4 engine, per-period config) vs live StratTrades_DS7_<acct>.csv sha d918fee4e83e1852. Live rows are slices aggregated to trades by (book, exit time, exit name, side); entry/exit times ET wall clock; net = pnlNet. Match key = signal second, +-2 s (per-book override {P6: 47}), same book and side. Realised closed-trade maxDD only (no open-trade MAE).

**the engine predicted +69582$ for the week; live made +104095$; the gap (+34513$) is explained by these contributions to live minus engine: trades live took that the engine did not (56) +56260$; trades the engine took that live did not (71) -46495$; different exit type on matched trades +28544$; fill/size differences on matched same-exit trades -3796$; the engine is NOT a faithful model of live D7 for this week (trade match below threshold, net gap above threshold, exit-type agreement below threshold, maxDD gap above threshold).**

### Totals and trade count

| | engine | live | delta (live-engine) |
|---|---|---|---|
| net $ | 69582 | 104095 | +34513 |
| trades | 202 | 187 | -15 |
| matched exact (+-tol) | 129 | | |
| matched near (<=120s, timing slip) | 2 | | |
| engine-only | 71 | | |
| live-only | 56 | | |
| matched / union | 50.8% | | |

Longs/shorts engine 95/107, live 85/102. Max lots in a trade: engine 11.0, live 10.0. Worst trade $: engine -6843, live -6510. Signal-second offset on matches: mean -0.67 s, median 0.00 s, max abs 63.0 s.

Match rate by tolerance on the signal second (same book and side, greedy nearest; live entryTime = FILL of the first slice, so +-2 s is expected to under-match): +-2 s: 129 pairs, matched/union 49.6%, share of engine trades 63.9%; +-60 s: 130 pairs, matched/union 50.2%, share of engine trades 64.4%; +-120 s: 131 pairs, matched/union 50.8%, share of engine trades 64.9%; +-300 s: 134 pairs, matched/union 52.5%, share of engine trades 66.3%; +-900 s: 136 pairs, matched/union 53.8%, share of engine trades 67.3%. +-300 and +-900 s are diagnostics only. The verdict criteria use the near tolerance (near_tol_sec = 120 s), as frozen.

### Per book

| book | n_pred | pred_net | pred_lots | n_live | live_net | live_lots | d_n | d_net |
|---|---|---|---|---|---|---|---|---|
| A7 | 18.0 | 9067.2 | 20.0 | 23 | -1415.0 | 23 | 5.0 | -10482.2 |
| H7 | 19.0 | 9266.2 | 46.0 | 3 | -770.0 | 4 | -16.0 | -10036.2 |
| K7 | 61.0 | 10319.1 | 70.0 | 64 | 16065.0 | 76 | 3.0 | 5745.9 |
| M7 | 29.0 | 2490.3 | 39.0 | 28 | 6015.0 | 37 | -1.0 | 3524.7 |
| O7 | 0.0 | 0.0 | 0.0 | 3 | 660.0 | 3 | 3.0 | 660.0 |
| P7 | 63.0 | 37107.0 | 297.0 | 53 | 86010.0 | 247 | -10.0 | 48903.0 |
| U7 | 7.0 | 6674.6 | 24.0 | 6 | -1755.0 | 19 | -1.0 | -8429.6 |
| X3 | 2.0 | -6215.4 | 4.0 | 3 | -905.0 | 6 | 1.0 | 5310.4 |
| X4 | 2.0 | -1517.4 | 4.0 | 2 | -170.0 | 4 | 0.0 | 1347.4 |
| X5 | 1.0 | 2390.3 | 2.0 | 2 | 360.0 | 4 | 1.0 | -2030.3 |

### Per day (ET calendar date of entry; Sun = Sun night)

| day | n_pred | pred_net | pred_lots | n_live | live_net | live_lots | d_n | d_net |
|---|---|---|---|---|---|---|---|---|
| Sun 11-01 | 10 | 4500.1 | 39.0 | 11 | 22400.0 | 32 | 1 | 17899.9 |
| Mon 11-02 | 30 | -2687.8 | 73.0 | 41 | 13965.0 | 85 | 11 | 16652.8 |
| Tue 11-03 | 71 | 28299.0 | 185.0 | 46 | 8675.0 | 116 | -25 | -19624.0 |
| Wed 11-04 | 60 | 43526.6 | 135.0 | 61 | 43615.0 | 118 | 1 | 88.4 |
| Thu 11-05 | 31 | -4056.0 | 74.0 | 28 | 15440.0 | 72 | -3 | 19496.0 |

### Engine by config period at entry (P0 old panel, P1 Mon 08:50-13:30, P2 after)

| period | n_pred | pred_net |
|---|---|---|
| P0 | 24 | -6015.2 |
| P1 | 4 | -27.1 |
| P2 | 174 | 75624.2 |

Engine trades not closed by the span end: 0.

### Gap decomposition (live - engine, $)

| component | $ |
|---|---|
| live-only trades | +56260 |
| engine-only trades (sign flipped) | -46495 |
| matched, different exit type | +28544 |
| matched, same exit type (fills/size) | -3796 |
| total | +34513 |

### Exit-type match (matched pairs; rows = engine, cols = live); agreement 65.4% on 130 pairs whose engine exit type is known (engine type other excluded)

| exit_type | target | thl2_cut | policy_cut | lock | stop | flatten | other |
|---|---|---|---|---|---|---|---|
| target | 50 | 3 | 4 | 0 | 0 | 0 | 0 |
| thl2_cut | 5 | 34 | 23 | 0 | 2 | 0 | 0 |
| policy_cut | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| lock | 1 | 1 | 0 | 1 | 0 | 0 | 1 |
| stop | 0 | 3 | 2 | 0 | 0 | 0 | 0 |
| flatten | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| other | 0 | 0 | 0 | 0 | 0 | 0 | 1 |

Exit counts all trades: engine {'target': 94, 'thl2_cut': 90, 'lock': 5, 'stop': 7, 'other': 6}; live {'target': 86, 'thl2_cut': 53, 'policy_cut': 39, 'lock': 3, 'stop': 2, 'other': 4}.

### Fill / slippage deltas on matched pairs by engine exit type (adverse + = live worse)

| type | n | d_net_mean | d_net_per_lot | d_net_sum | d_lots | entry_adv_pts | exit_adv_pts |
|---|---|---|---|---|---|---|---|
| target | 57 | -312.4 | -235.8 | -17807.1 | -0.1 | 3.3 | 9.9 |
| thl2_cut | 64 | 517.8 | 83.0 | 33138.4 | -0.0 | 3.8 | -3.8 |
| lock | 4 | 1191.0 | 686.9 | 4764.0 | -0.8 | 3.1 | -29.2 |
| stop | 5 | 893.4 | 617.3 | 4466.9 | 0.0 | 0.6 | -29.7 |
| other | 1 | 186.0 | 186.0 | 186.0 | 0.0 | 6.0 | -12.0 |

### maxDD path (realised, by exit time)

engine maxDD 24106$ (trough Tue 11-03 03:36Z); live maxDD 14490$ (trough Wed 11-04 01:03Z); gap 39.9%.
 Equity-curve correlation on a 49-point grid 0.961; largest |engine-live| 37657$ at Tue 11-03 08:47Z.


### Unmatched trades (by signal second; first 25 each)

engine-only:

| signal_sec | book | side | lots | exit_type | net |
|---|---|---|---|---|---|
| Sun 11-01 23:41Z | H7 | 1 | 3.0 | other | 1378.8 |
| Sun 11-01 23:51Z | P7 | 1 | 11.0 | other | 3929.0 |
| Mon 11-02 00:28Z | P7 | 1 | 11.0 | thl2_cut | -6842.8 |
| Mon 11-02 00:46Z | P7 | 1 | 2.0 | other | 463.8 |
| Mon 11-02 01:01Z | P7 | 1 | 2.0 | target | 2421.6 |
| Mon 11-02 02:31Z | P7 | 1 | 4.0 | other | 1576.1 |
| Mon 11-02 03:36Z | K7 | 1 | 1.0 | thl2_cut | -721.1 |
| Mon 11-02 05:13Z | P7 | 1 | 4.0 | other | 389.5 |
| Mon 11-02 07:17Z | X4 | -1 | 2.0 | target | 1590.3 |
| Mon 11-02 07:36Z | K7 | -1 | 3.0 | thl2_cut | -1716.2 |
| Mon 11-02 08:28Z | X5 | -1 | 2.0 | target | 2390.3 |
| Mon 11-02 09:04Z | P7 | -1 | 4.0 | thl2_cut | -2470.2 |
| Mon 11-02 11:48Z | P7 | -1 | 2.0 | target | 2459.4 |
| Mon 11-02 13:43Z | X3 | 1 | 2.0 | stop | -3107.7 |
| Mon 11-02 16:17Z | M7 | -1 | 1.0 | target | 1232.3 |
| Mon 11-02 16:28Z | H7 | -1 | 1.0 | thl2_cut | -676.2 |
| Tue 11-03 00:15Z | H7 | -1 | 2.0 | thl2_cut | -1238.7 |
| Tue 11-03 01:33Z | H7 | 1 | 2.0 | thl2_cut | -1288.6 |
| Tue 11-03 05:57Z | H7 | -1 | 2.0 | thl2_cut | -1103.6 |
| Tue 11-03 07:16Z | P7 | -1 | 4.0 | thl2_cut | -2556.4 |
| Tue 11-03 07:48Z | K7 | 1 | 1.0 | target | 1102.2 |
| Tue 11-03 07:56Z | M7 | 1 | 1.0 | thl2_cut | -563.1 |
| Tue 11-03 08:07Z | P7 | 1 | 4.0 | thl2_cut | -2207.5 |
| Tue 11-03 09:03Z | P7 | 1 | 4.0 | target | 4869.9 |
| Tue 11-03 09:10Z | U7 | 1 | 2.0 | target | 2419.1 |

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
