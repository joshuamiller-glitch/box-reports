# DS3_REDO_R4_ENTRY - entry mechanics re-scored on the state base (REDO-R4, T-STACK-REDO)
**2026-11-09 23:07Z UTC. PRE-PROOF (entries not live-matched); post-hoc; Shadow only; no PASS claims; ROLL-EXCL: every trade alive across a contract-roll second is dropped from the reference AND from every cell before any number below (33 base trades, SZ_BASE_PROOF section 9); STANDING RULE: all-market, no-gate and no-confirmation rows are REFERENCE rows, never candidates.**

## 0. What the live entry really is (code, not description)
DS7.cs v1.4 L2Arm/L2Pump: L2SplitPct (70) of the session lots go at market in 1-lot slices every 2 s; the remainder is NOT a resting limit: it is a MARKET add fired when price is >= L2GateMinDipPts (3) against the signal price AND >= L2GateRequired (1) of 8 book confirmations hold (checked at most once per second), 1 stage, no time limit (L2GateMaxMinutes 0), cancelled on the stop level / time block / session-lots 0 / any exit. Stop at the original level, target re-based from the average. The engine (replica sim.py) implements exactly this. So "resting offset 1-6 pts" = min dip 1-6 pts (DIP family). A TRUE resting limit is a different order type, scored as the LIM family under a stated fill model: order live 0.5 s after the arm at arm_px -+ offset; fills at the limit when a print trades strictly through it, or when aggressor-against volume at the level reaches the lots (queue 0, optimistic) or lots + one median book level (queue 1); no L2 test, cancelled on the same rules. LIM rows are HYPOTHETICAL (optimistic fills, no live fill evidence) and are never a recommendation.
P7 PB3B 45-s confirm: P7 signals are held until a three-bar pattern prints on 45-s bars (sessions nyam, nypm only), then the split entry runs; engine = ITER14 replica 45-s bars built from the owned tape; other timeframes rebuild the series from the same prints.
Engine: exact replica (S1b tick bar close, TH-L2-S state cut COMB, Q1-A sizer), hooks code/th_sz_entry/entry_hooks.py (class swap, instance config; interface INTERFACE.md); EN_REG (the live setting) is regression-checked: all trade columns identical to S1b-COMB on 202610 (202305 pending). Fills: market orders walk the book 1.0 s after the decision (LAT_FILL, user-measured); per-variant fill statistics in section 4.

## 1. Status
Sets with data: 30; with all L6M months: 26; window used for ranking: L6M. Reported windows appear only when every month of the window is exact-run. Stage B (PRE, X', HOLD for the top-5 + reference rows) starts when stage A is complete.

## 2. Noise floor (engine chaos)
NULL0-3 (fill latency +-2..5%) reproduced the live row to the dollar-per-week (the engine fills at book-at-time; the jitter is too weak to move a fill): no information. NULL4-6 are tiny REAL entry changes (slice cadence 1.9 / 2.1 s, min dip 3.1): their L6M maxDD cut vs live is -8.3, -3.8, -7.7% and mean delta 138 to 1236 $/wk. So any |maxDD cut| below about 8% and any |mean delta| below about 1236 $/wk is NOT distinguishable from path-dependence (every tiny change worsened maxDD: the live row is a favourable point of its own neighbourhood, which also warns about selection on one window).

## 3. Variant table (L6M, ROLL-EXCL, vs exact live S1b-COMB; sorted by maxDD cut)
maxDD cut: positive = shallower than live. w20gain_L6M: % change of the sum of the 20 worst weeks vs live, positive = better (on a 26-week window this is nearly the mean). dmean = $/wk vs live (carrying week dropped). eq_cut = maxDD cut at equal L6M mean. wf2w_* = bi-weekly WF (section 5b).

| set                | family                   |   months | ref   |   dmean_L6M |   dd_L6M |   cut_L6M |   w20gain_L6M |   eq_cut_L6M |   wf2w_beat_pct |   wf2w_cut |   wf2w_mean |   wf2w_n |   wf2w_switch | prior         | desc                                                               | label                         |
|:-------------------|:-------------------------|---------:|:------|------------:|---------:|----------:|--------------:|-------------:|----------------:|-----------:|------------:|---------:|--------------:|:--------------|:-------------------------------------------------------------------|:------------------------------|
| EN_CF_EN_45        | P7 PB3B confirm          |        6 | False |      1735.5 |  69086.7 |      13.5 |          41   |         19.3 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN |                                                                    | LEAD (L6M only, PRE-PROOF)    |
| EN_CF_EN_90        | P7 PB3B confirm          |        6 | False |       169.3 |  79741.9 |       0.2 |          34.5 |          0.9 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN |                                                                    | LEAD (L6M only, inside noise) |
| EN_NULL3           | noise probe              |        6 | True  |        -0.4 |  79907.3 |       0   |           0.3 |         -0   |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | NOISE PROBE: LAT_FILL 0.95 s (engine chaos floor, not a candidate) | REFERENCE                     |
| EN_NULL2           | noise probe              |        6 | True  |        -0.2 |  79907.3 |       0   |           0   |         -0   |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | NOISE PROBE: LAT_FILL 1.05 s (engine chaos floor, not a candidate) | REFERENCE                     |
| EN_NULL1           | noise probe              |        6 | True  |         0.2 |  79907.3 |       0   |           0   |          0   |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | NOISE PROBE: LAT_FILL 1.02 s (engine chaos floor, not a candidate) | REFERENCE                     |
| EN_NULL0           | noise probe              |        6 | True  |         0   |  79907.3 |       0   |           0   |          0   |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | NOISE PROBE: LAT_FILL 0.98 s (engine chaos floor, not a candidate) | REFERENCE                     |
| EN_SLALL           | slice                    |        7 | False |      1466.4 |  79928.5 |      -0   |          -2.3 |          6.3 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | all at once                                                        | no                            |
| EN_SP50            | split                    |        7 | False |      3994.3 |  80480.8 |      -0.7 |          27.9 |         14   |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | split 50% at market                                                | no                            |
| EN_CF_EN_30        | P7 PB3B confirm          |        6 | False |       643.8 |  80508   |      -0.8 |          42.7 |          1.9 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN |                                                                    | no                            |
| EN_SL2x1           | slice                    |        6 | False |      1653.1 |  82183.3 |      -2.8 |           9.7 |          4.4 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | 2 lots / 1 s                                                       | no                            |
| EN_NULL5           | noise probe              |        6 | True  |       296.8 |  82981.1 |      -3.8 |          -5.7 |         -2.8 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | NOISE PROBE: slice cadence 1.9 s                                   | REFERENCE                     |
| EN_REQ2            | L2 required              |        6 | False |       470.1 |  82988.9 |      -3.9 |          -8.5 |         -1.7 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | required 2 of 8                                                    | no                            |
| EN_ONLY_absorption | single confirmation      |        6 | False |      1524.8 |  83318.1 |      -4.3 |          41.1 |          1.4 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | only absorption                                                    | no                            |
| EN_MAXM15          | max minutes              |        6 | False |      -306.7 |  83432.6 |      -4.4 |         -17.4 |         -5.8 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | max 15 min                                                         | no                            |
| EN_STG2            | stages                   |        6 | False |     -1696.4 |  84415.1 |      -5.6 |          -9.6 |        -13.2 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | stages 2 step 10                                                   | no                            |
| EN_DIP4            | resting offset / min dip |        7 | False |      2839.2 |  85151.3 |      -6.6 |          18.5 |          5   |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | min dip 4 pts                                                      | no                            |
| EN_CF_TB_60        | P7 PB3B confirm          |        6 | False |       517.6 |  85699.6 |      -7.2 |          17.6 |         -4.8 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | P7 three-bar 60 s                                                  | no                            |
| EN_NULL6           | noise probe              |        6 | True  |      1235.6 |  86055.9 |      -7.7 |          30.1 |         -3   |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | NOISE PROBE: min dip 3.1 pts (one-tick-ish)                        | REFERENCE                     |
| EN_ONLY_delta      | single confirmation      |        6 | False |      1324   |  86498.2 |      -8.2 |          -3.9 |         -2.1 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | only delta                                                         | no                            |
| EN_NULL4           | noise probe              |        6 | True  |       138.4 |  86509.2 |      -8.3 |          -3.2 |         -7.6 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | NOISE PROBE: slice cadence 2.1 s (tiny real change)                | REFERENCE                     |
| EN_DIP6            | resting offset / min dip |        6 | False |      -708.4 |  88027.8 |     -10.2 |           8.9 |        -13.2 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | min dip 6 pts                                                      | no                            |
| EN_CF_EN_60        | P7 PB3B confirm          |        6 | False |     -3212.9 |  96061.7 |     -20.2 |         -14.2 |        -36.9 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN |                                                                    | no                            |
| EN_SP0             | split                    |        6 | False |       356.5 |  96689.5 |     -21   |         -45.4 |        -19.1 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | split 0% at market                                                 | no                            |
| EN_DIP2            | resting offset / min dip |        6 | False |     -3053.3 |  97693.8 |     -22.3 |         -55.7 |        -40.6 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | min dip 2 pts                                                      | no                            |
| EN_SL1x4           | slice                    |        6 | False |     -2296.7 |  99951.1 |     -25.1 |         -32.6 |        -39.8 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | 1 lot / 4 s                                                        | no                            |
| EN_CF_S_ALLS       | P7 PB3B confirm          |        6 | False |    -10577.5 | 106841   |     -33.7 |        -168.8 |       -138.2 |             nan |        nan |         nan |      nan |           nan | PRIOR-UNKNOWN | P7 confirm sessions ALLS                                           | no                            |

## 4. Fills measured per variant (owned tape; first-fill and add slippage vs the signal price, points, gate books only)
| set                |   ntr |   lots |   with_add |   slip1_pts |   addslip_pts |   avgfill_vs_sig |       net |
|:-------------------|------:|-------:|-----------:|------------:|--------------:|-----------------:|----------:|
| EN_CF_EN_30        |  4823 |   2.12 |       0.42 |        0.91 |         -0.3  |             0.45 | 721859    |
| EN_CF_EN_45        |  4814 |   2.12 |       0.42 |        1.06 |          0.04 |             0.61 | 715004    |
| EN_CF_EN_60        |  4800 |   2.12 |       0.42 |        1.33 |          0.54 |             0.88 | 624244    |
| EN_CF_EN_90        |  4781 |   2.11 |       0.42 |        1.16 |          0.2  |             0.71 | 686746    |
| EN_CF_S_ALLS       |  4795 |   1.99 |       0.42 |        1.71 |          0.68 |             1.03 | 317059    |
| EN_CF_TB_60        |  4832 |   2.13 |       0.42 |        0.79 |         -0.6  |             0.34 | 662575    |
| EN_DIP1            |  1541 |   2.02 |       0.45 |        0.85 |          0.65 |             0.65 | 174930    |
| EN_DIP2            |  4908 |   2.1  |       0.43 |        1.01 |          0.27 |             0.67 | 537299    |
| EN_DIP4            |  5440 |   2.13 |       0.41 |        0.96 |         -0.83 |             0.35 | 794011    |
| EN_DIP6            |  4842 |   2.14 |       0.41 |        0.97 |         -1.8  |             0.1  | 659224    |
| EN_LIM3_Q0         |   816 |   2.13 |       0.4  |        1.21 |         -0.16 |             0.7  |  71889.9  |
| EN_MAXM15          |  4885 |   2.1  |       0.41 |        1.02 |         -0.24 |             0.56 | 619681    |
| EN_NULL0           |  4846 |   2.13 |       0.42 |        0.99 |         -0.31 |             0.52 | 645139    |
| EN_NULL1           |  4846 |   2.13 |       0.42 |        0.99 |         -0.31 |             0.52 | 645149    |
| EN_NULL2           |  4846 |   2.13 |       0.42 |        0.99 |         -0.31 |             0.52 | 645149    |
| EN_NULL3           |  4845 |   2.13 |       0.42 |        0.99 |         -0.31 |             0.52 | 645644    |
| EN_NULL4           |  4849 |   2.13 |       0.42 |        1    |         -0.3  |             0.53 | 657861    |
| EN_NULL5           |  4854 |   2.13 |       0.42 |        1    |         -0.28 |             0.53 | 635886    |
| EN_NULL6           |  4820 |   2.13 |       0.42 |        1    |         -0.39 |             0.5  | 689217    |
| EN_ONLY_absorption |  4824 |   2.14 |       0.41 |        0.99 |         -0.9  |             0.36 | 706767    |
| EN_ONLY_delta      |  4760 |   2.14 |       0.41 |        0.93 |         -1.9  |             0.06 | 649483    |
| EN_PERSIST         |   806 |   2.1  |       0.4  |        1.08 |         -0.02 |             0.63 |  -4715.18 |
| EN_REG             |   823 |   2.12 |       0.41 |        1.16 |         -0.03 |             0.69 |  45346.9  |
| EN_REQ2            |  4811 |   2.15 |       0.42 |        0.94 |         -0.8  |             0.35 | 629281    |
| EN_SL1x4           |  4845 |   2.13 |       0.42 |        0.96 |         -0.34 |             0.5  | 551407    |
| EN_SL2x1           |  4769 |   2.1  |       0.41 |        0.98 |         -0.63 |             0.48 | 647746    |
| EN_SLALL           |  5402 |   2.1  |       0.39 |        0.99 |         -2.68 |             0.47 | 772202    |
| EN_SP0             |  4477 |   2.16 |       0.42 |       -2.87 |         -2.9  |            -2.85 | 651470    |
| EN_SP50            |  5449 |   2.1  |       0.42 |        0.99 |         -0.92 |             0.28 | 827582    |
| EN_STG2            |  4855 |   2.12 |       0.42 |        1.02 |         -0.61 |             0.42 | 597525    |

## 5. Summary block: setting | live value | best on the state base | holds OOS? | change recommended | panel field
| setting | live value | best on the state base | holds OOS? | change recommended | panel field |
|--|--|--|--|--|--|
| split | 70/30 | SP50 (L6M cut -0.7%, dmean 3994) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | L2SplitPct |
| resting offset (min dip) | 3 pts | DIP4 (L6M cut -6.6%, dmean 2839) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | L2GateMinDipPts |
| confirmations required | 1 of 8 | REQ2 (L6M cut -3.9%, dmean 470) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | L2GateRequired |
| which confirmation (alone) | all 8, 1 needed | ONLY_absorption (L6M cut -4.3%, dmean 1525) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | code (GATE list); no panel field |
| stages | 1 | STG2 (L6M cut -5.6%, dmean -1696) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | L2GateStages / L2GateStageStepPts |
| max minutes | 0 (never) | MAXM15 (L6M cut -4.4%, dmean -307) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | L2GateMaxMinutes |
| slice size / cadence | 1 lot / 2 s | SLALL (L6M cut -0.0%, dmean 1466) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | code constant (no panel field) |
| true resting limit | not used (market add) | (pending) | pending | no (pending) | new order type, code change |
| add cancelled on exit | cancelled | (pending) | pending | no (pending) | code (L2Disarm) |
| P7 PB3B confirm (pattern / tf / sessions / dip / minutes) | three-bar, 45 s, nyam+nypm, dip 0, 0 min | CF_45 (L6M cut 13.5%, dmean 1735) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | ConfirmPatternA, ConfirmTfSecsA, ConfirmSessionsA, ConfirmMinDip, ConfirmMaxMinutes |

## 5b. Bi-weekly re-pick walk-forward (PRIMARY OOS; trailing 26 wk -> next 2 wk, purged 7 d; the picker switches away from live only when the trailing maxDD cut is >= 8% = the entry noise floor)
Computed per candidate against live over the 12 contiguous exact months 2025-11..2026-10 (first refit 2026-05-18, ~12 refit periods); columns wf2w_* in section 3 (NaN = the candidate has no exact HOLD months yet). PRE label per STANDING RULE 2a via Z.prior_info (OK-PRIOR / RECENT-ONLY, -UNKNOWN-WF suffix when the WF is missing).

## 5c. REFIT 2026-11-22
Settings the bi-weekly procedure would pick today: **live setting for every entry layer** (L2SplitPct 70, L2GateMinDipPts 3, L2GateRequired 1, L2GateStages 1, L2GateMaxMinutes 0, slices 1 lot / 2 s, PB3B three-bar 45 s nyam+nypm) unless a row above shows a trailing maxDD cut >= the floor AND wf2w_beat_pct >= 50. Rows meeting both today: none.

## 6. Per-book / session P&L deltas of the leaders
See /mnt/l2/l2vast/_th_sz/entry/en_book.csv (L6M window months; net by book x session per set).