# DS3_REDO_R4_ENTRY - entry mechanics re-scored on the state base (REDO-R4, T-STACK-REDO)
**2026-11-09 20:24Z UTC. PRE-PROOF (entries not live-matched); post-hoc; Shadow only; no PASS claims; ROLL-EXCL: every trade alive across a contract-roll second is dropped from the reference AND from every cell before any number below (33 base trades, SZ_BASE_PROOF section 9); STANDING RULE: all-market, no-gate and no-confirmation rows are REFERENCE rows, never candidates.**

## 0. What the live entry really is (code, not description)
DS7.cs v1.4 L2Arm/L2Pump: L2SplitPct (70) of the session lots go at market in 1-lot slices every 2 s; the remainder is NOT a resting limit: it is a MARKET add fired when price is >= L2GateMinDipPts (3) against the signal price AND >= L2GateRequired (1) of 8 book confirmations hold (checked at most once per second), 1 stage, no time limit (L2GateMaxMinutes 0), cancelled on the stop level / time block / session-lots 0 / any exit. Stop at the original level, target re-based from the average. The engine (replica sim.py) implements exactly this. So "resting offset 1-6 pts" = min dip 1-6 pts (DIP family). A TRUE resting limit is a different order type, scored as the LIM family under a stated fill model: order live 0.5 s after the arm at arm_px -+ offset; fills at the limit when a print trades strictly through it, or when aggressor-against volume at the level reaches the lots (queue 0, optimistic) or lots + one median book level (queue 1); no L2 test, cancelled on the same rules. LIM rows are HYPOTHETICAL (optimistic fills, no live fill evidence) and are never a recommendation.
P7 PB3B 45-s confirm: P7 signals are held until a three-bar pattern prints on 45-s bars (sessions nyam, nypm only), then the split entry runs; engine = ITER14 replica 45-s bars built from the owned tape; other timeframes rebuild the series from the same prints.
Engine: exact replica (S1b tick bar close, TH-L2-S state cut COMB, Q1-A sizer), hooks code/th_sz_entry/entry_hooks.py (class swap, instance config; interface INTERFACE.md); EN_REG (the live setting) is regression-checked: all trade columns identical to S1b-COMB on 202610 (202305 pending). Fills: market orders walk the book 1.0 s after the decision (LAT_FILL, user-measured); per-variant fill statistics in section 4.

## 1. Status
Sets with data: 21; with all L6M months: 12; window used for ranking: L6M. Reported windows appear only when every month of the window is exact-run. Stage B (PRE, X', HOLD for the top-5 + reference rows) starts when stage A is complete.

## 2. Noise floor (engine chaos)
NULL0-3 (fill latency +-2..5%) reproduced the live row to the dollar-per-week (the engine fills at book-at-time; the jitter is too weak to move a fill): no information. NULL4-6 are tiny REAL entry changes (slice cadence 1.9 / 2.1 s, min dip 3.1): their L6M maxDD cut vs live is -8.3, -3.8, -7.7% and mean delta 138 to 1236 $/wk. So any |maxDD cut| below about 8% and any |mean delta| below about 1236 $/wk is NOT distinguishable from path-dependence (every tiny change worsened maxDD: the live row is a favourable point of its own neighbourhood, which also warns about selection on one window).

## 3. Variant table (L6M, ROLL-EXCL, vs exact live S1b-COMB; sorted by maxDD cut)
| set      | family                   |   months | ref   |   dmean_L6M |   dd_L6M |   cut_L6M |   w20cut_L6M |   eq_cut_L6M | desc                                                               | label     |
|:---------|:-------------------------|---------:|:------|------------:|---------:|----------:|-------------:|-------------:|:-------------------------------------------------------------------|:----------|
| EN_NULL0 | noise probe              |        6 | True  |         0   |  79907.3 |       0   |          0   |          0   | NOISE PROBE: LAT_FILL 0.98 s (engine chaos floor, not a candidate) | REFERENCE |
| EN_NULL3 | noise probe              |        6 | True  |        -0.4 |  79907.3 |       0   |         -0.3 |         -0   | NOISE PROBE: LAT_FILL 0.95 s (engine chaos floor, not a candidate) | REFERENCE |
| EN_NULL2 | noise probe              |        6 | True  |        -0.2 |  79907.3 |       0   |          0   |         -0   | NOISE PROBE: LAT_FILL 1.05 s (engine chaos floor, not a candidate) | REFERENCE |
| EN_NULL1 | noise probe              |        6 | True  |         0.2 |  79907.3 |       0   |          0   |          0   | NOISE PROBE: LAT_FILL 1.02 s (engine chaos floor, not a candidate) | REFERENCE |
| EN_SP50  | split                    |        6 | False |      3994.3 |  80480.8 |      -0.7 |        -27.9 |         14   | split 50% at market                                                | no        |
| EN_NULL5 | noise probe              |        6 | True  |       296.8 |  82981.1 |      -3.8 |          5.7 |         -2.8 | NOISE PROBE: slice cadence 1.9 s                                   | REFERENCE |
| EN_DIP4  | resting offset / min dip |        6 | False |      2839.2 |  85151.3 |      -6.6 |        -18.5 |          5   | min dip 4 pts                                                      | no        |
| EN_NULL6 | noise probe              |        6 | True  |      1235.6 |  86055.9 |      -7.7 |        -30.1 |         -3   | NOISE PROBE: min dip 3.1 pts (one-tick-ish)                        | REFERENCE |
| EN_NULL4 | noise probe              |        6 | True  |       138.4 |  86509.2 |      -8.3 |          3.2 |         -7.6 | NOISE PROBE: slice cadence 2.1 s (tiny real change)                | REFERENCE |
| EN_DIP6  | resting offset / min dip |        6 | False |      -708.4 |  88027.8 |     -10.2 |         -8.9 |        -13.2 | min dip 6 pts                                                      | no        |
| EN_SP0   | split                    |        6 | False |       356.5 |  96689.5 |     -21   |         45.4 |        -19.1 | split 0% at market                                                 | no        |
| EN_DIP2  | resting offset / min dip |        6 | False |     -3053.3 |  97693.8 |     -22.3 |         55.7 |        -40.6 | min dip 2 pts                                                      | no        |

## 4. Fills measured per variant (owned tape; first-fill and add slippage vs the signal price, points, gate books only)
| set         |   ntr |   lots |   with_add |   slip1_pts |   addslip_pts |   avgfill_vs_sig |       net |
|:------------|------:|-------:|-----------:|------------:|--------------:|-----------------:|----------:|
| EN_CF_EN_60 |   821 |   2.12 |       0.41 |        1.2  |          0.3  |             0.71 |  36975.9  |
| EN_DIP1     |  1541 |   2.02 |       0.45 |        0.85 |          0.65 |             0.65 | 174930    |
| EN_DIP2     |  4908 |   2.1  |       0.43 |        1.01 |          0.27 |             0.67 | 537299    |
| EN_DIP4     |  4801 |   2.14 |       0.42 |        0.97 |         -0.84 |             0.37 | 683181    |
| EN_DIP6     |  4842 |   2.14 |       0.41 |        0.97 |         -1.8  |             0.1  | 659224    |
| EN_LIM3_Q0  |   816 |   2.13 |       0.4  |        1.21 |         -0.16 |             0.7  |  71889.9  |
| EN_MAXM15   |   836 |   2.07 |       0.4  |        1.19 |          0.13 |             0.75 |  22084.9  |
| EN_NULL0    |  4846 |   2.13 |       0.42 |        0.99 |         -0.31 |             0.52 | 645139    |
| EN_NULL1    |  4846 |   2.13 |       0.42 |        0.99 |         -0.31 |             0.52 | 645149    |
| EN_NULL2    |  4846 |   2.13 |       0.42 |        0.99 |         -0.31 |             0.52 | 645149    |
| EN_NULL3    |  4845 |   2.13 |       0.42 |        0.99 |         -0.31 |             0.52 | 645644    |
| EN_NULL4    |  4849 |   2.13 |       0.42 |        1    |         -0.3  |             0.53 | 657861    |
| EN_NULL5    |  4854 |   2.13 |       0.42 |        1    |         -0.28 |             0.53 | 635886    |
| EN_NULL6    |  4820 |   2.13 |       0.42 |        1    |         -0.39 |             0.5  | 689217    |
| EN_PERSIST  |   806 |   2.1  |       0.4  |        1.08 |         -0.02 |             0.63 |  -4715.18 |
| EN_REG      |   823 |   2.12 |       0.41 |        1.16 |         -0.03 |             0.69 |  45346.9  |
| EN_REQ2     |   805 |   2.16 |       0.4  |        1.04 |         -0.29 |             0.48 |  48651.3  |
| EN_SLALL    |   798 |   2.08 |       0.36 |        1.13 |         -2.62 |             0.63 |  40138.1  |
| EN_SP0      |  4477 |   2.16 |       0.42 |       -2.87 |         -2.9  |            -2.85 | 651470    |
| EN_SP50     |  4807 |   2.11 |       0.42 |        1    |         -0.92 |             0.29 | 713868    |
| EN_STG2     |   823 |   2.1  |       0.41 |        1.18 |         -0.37 |             0.58 |  30532.3  |

## 5. Summary block: setting | live value | best on the state base | holds OOS? | change recommended | panel field
| setting | live value | best on the state base | holds OOS? | change recommended | panel field |
|--|--|--|--|--|--|
| split | 70/30 | SP50 (L6M cut -0.7%, dmean 3994) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | L2SplitPct |
| resting offset (min dip) | 3 pts | DIP4 (L6M cut -6.6%, dmean 2839) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | L2GateMinDipPts |
| confirmations required | 1 of 8 | (pending) | pending | no (pending) | L2GateRequired |
| which confirmation (alone) | all 8, 1 needed | (pending) | pending | no (pending) | code (GATE list); no panel field |
| stages | 1 | (pending) | pending | no (pending) | L2GateStages / L2GateStageStepPts |
| max minutes | 0 (never) | (pending) | pending | no (pending) | L2GateMaxMinutes |
| slice size / cadence | 1 lot / 2 s | (pending) | pending | no (pending) | code constant (no panel field) |
| true resting limit | not used (market add) | (pending) | pending | no (pending) | new order type, code change |
| add cancelled on exit | cancelled | (pending) | pending | no (pending) | code (L2Disarm) |
| P7 PB3B confirm (pattern / tf / sessions / dip / minutes) | three-bar, 45 s, nyam+nypm, dip 0, 0 min | (pending) | pending | no (pending) | ConfirmPatternA, ConfirmTfSecsA, ConfirmSessionsA, ConfirmMinDip, ConfirmMaxMinutes |

## 6. Per-book / session P&L deltas of the leaders
See /mnt/l2/l2vast/_th_sz/entry/en_book.csv (L6M window months; net by book x session per set).