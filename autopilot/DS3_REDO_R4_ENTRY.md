# DS3_REDO_R4_ENTRY - entry mechanics re-scored on the state base (REDO-R4, T-STACK-REDO)
**2026-11-09 18:04Z UTC. PRE-PROOF (entries not live-matched); post-hoc; Shadow only; no PASS claims; ROLL-EXCL: every trade alive across a contract-roll second is dropped from the reference AND from every cell before any number below (33 base trades, SZ_BASE_PROOF section 9); STANDING RULE: all-market, no-gate and no-confirmation rows are REFERENCE rows, never candidates.**

## 0. What the live entry really is (code, not description)
DS7.cs v1.4 L2Arm/L2Pump: L2SplitPct (70) of the session lots go at market in 1-lot slices every 2 s; the remainder is NOT a resting limit: it is a MARKET add fired when price is >= L2GateMinDipPts (3) against the signal price AND >= L2GateRequired (1) of 8 book confirmations hold (checked at most once per second), 1 stage, no time limit (L2GateMaxMinutes 0), cancelled on the stop level / time block / session-lots 0 / any exit. Stop at the original level, target re-based from the average. The engine (replica sim.py) implements exactly this. So "resting offset 1-6 pts" = min dip 1-6 pts (DIP family). A TRUE resting limit is a different order type, scored as the LIM family under a stated fill model: order live 0.5 s after the arm at arm_px -+ offset; fills at the limit when a print trades strictly through it, or when aggressor-against volume at the level reaches the lots (queue 0, optimistic) or lots + one median book level (queue 1); no L2 test, cancelled on the same rules. LIM rows are HYPOTHETICAL (optimistic fills, no live fill evidence) and are never a recommendation.
P7 PB3B 45-s confirm: P7 signals are held until a three-bar pattern prints on 45-s bars (sessions nyam, nypm only), then the split entry runs; engine = ITER14 replica 45-s bars built from the owned tape; other timeframes rebuild the series from the same prints.
Engine: exact replica (S1b tick bar close, TH-L2-S state cut COMB, Q1-A sizer), hooks code/th_sz_entry/entry_hooks.py (class swap, instance config; interface INTERFACE.md); EN_REG (the live setting) is regression-checked: all trade columns identical to S1b-COMB on 202610 (202305 pending). Fills: market orders walk the book 1.0 s after the decision (LAT_FILL, user-measured); per-variant fill statistics in section 4.

## 1. Status
Sets with data: 12; with all L6M months: 12; window used for ranking: L1M. Reported windows appear only when every month of the window is exact-run. Stage B (PRE, X', HOLD for the top-5 + reference rows) starts when stage A is complete.

## 2. Noise floor (engine chaos)
NULL probes not yet complete (queue first group). Until then ONE month showed +-30k swings from tiny changes (202610): treat every single-month number as noise.

## 3. Variant table (L1M, ROLL-EXCL, vs exact live S1b-COMB; sorted by maxDD cut)
| set         | family                                       |   months | ref   |   mean_L1M |   dmean_L1M |   dd_L1M |   cut_L1M |   w20cut_L1M |   eq_cut_L1M | desc                                  | label                      |
|:------------|:---------------------------------------------|---------:|:------|-----------:|------------:|---------:|----------:|-------------:|-------------:|:--------------------------------------|:---------------------------|
| EN_LIM3_Q0  | true resting limit (hypothetical order type) |        1 | False |     9402.5 |      1875.6 |  50958.8 |      36.2 |      -1211   |       -371.7 | resting limit 3 pts queue 0           | LEAD (L6M only, PRE-PROOF) |
| EN_DIP4     | resting offset / min dip                     |        1 | False |     5658.6 |     -1868.3 |  57203.2 |      28.3 |       -971.8 |       -466.4 | min dip 4 pts                         | LEAD (L6M only, PRE-PROOF) |
| EN_DIP6     | resting offset / min dip                     |        1 | False |     6572.8 |      -954.1 |  57667   |      27.8 |      -1108.9 |       -503.1 | min dip 6 pts                         | LEAD (L6M only, PRE-PROOF) |
| EN_CF_EN_60 | P7 PB3B confirm                              |        1 | False |     2865.5 |     -4661.4 |  59460.9 |      25.5 |       -577.6 |       -970.1 |                                       | LEAD (L6M only, PRE-PROOF) |
| EN_SP50     | split                                        |        1 | False |     2952.8 |     -4574.1 |  63757.6 |      20.1 |       -367.4 |       -892   | split 50% at market                   | LEAD (L6M only, PRE-PROOF) |
| EN_SLALL    | slice                                        |        1 | False |      652.3 |     -6874.6 |  68678.7 |      14   |       -149.4 |      -1038.6 | all at once                           | LEAD (L6M only, PRE-PROOF) |
| EN_DIP1     | resting offset / min dip                     |        1 | False |   -23174.5 |      3432.3 |  69523.6 |      12.9 |       1050   |      -4526.8 | min dip 1 pts                         | LEAD (L6M only, PRE-PROOF) |
| EN_REG      | live reference                               |        1 | True  |   -26606.8 |         0   |  79820.5 |       0   |          0   |      -1071.3 | live setting (regression vs S1b-COMB) | REFERENCE                  |
| EN_STG2     | stages                                       |        1 | False |     6750.8 |      -776.1 |  84415.1 |      -5.8 |        232.3 |      -1739.8 | stages 2 step 10                      | no                         |
| EN_PERSIST  | add survives exit                            |        1 | False |   -29882   |     -3275.2 |  89646.1 |     -12.3 |       1162.6 |        nan   | reserve survives flat                 | no                         |
| EN_SP0      | split                                        |        1 | False |    14802.6 |     -2497.4 |  96689.5 |     -21.1 |       1445.7 |        nan   | split 0% at market                    | no                         |
| EN_DIP2     | resting offset / min dip                     |        1 | False |   -32564.6 |     -5957.8 |  97693.8 |     -22.4 |       1249.7 |      -6950.6 | min dip 2 pts                         | no                         |

## 4. Fills measured per variant (owned tape; first-fill and add slippage vs the signal price, points, gate books only)
| set         |   ntr |   lots |   with_add |   slip1_pts |   addslip_pts |   avgfill_vs_sig |       net |
|:------------|------:|-------:|-----------:|------------:|--------------:|-----------------:|----------:|
| EN_REG      |   823 |   2.12 |       0.41 |        1.16 |         -0.03 |             0.69 |  45346.9  |
| EN_SP50     |   813 |   2.1  |       0.4  |        1.23 |         -0.41 |             0.56 |  42769.7  |
| EN_SP0      |   754 |   2.13 |       0.39 |       -2.82 |         -3.2  |            -2.85 | -45440.1  |
| EN_DIP1     |   854 |   2    |       0.43 |        1.27 |          1.21 |             1.01 |   9998.74 |
| EN_DIP2     |   837 |   2.09 |       0.42 |        1.1  |          0.55 |             0.76 |   9220.16 |
| EN_DIP4     |   805 |   2.13 |       0.4  |        1.07 |         -0.72 |             0.48 |  67204.4  |
| EN_DIP6     |   825 |   2.13 |       0.39 |        1.15 |         -1.38 |             0.32 |  63629.5  |
| EN_LIM3_Q0  |   816 |   2.13 |       0.4  |        1.21 |         -0.16 |             0.7  |  71889.9  |
| EN_SLALL    |   798 |   2.08 |       0.36 |        1.13 |         -2.62 |             0.63 |  40138.1  |
| EN_STG2     |   823 |   2.1  |       0.41 |        1.18 |         -0.37 |             0.58 |  30532.3  |
| EN_PERSIST  |   806 |   2.1  |       0.4  |        1.08 |         -0.02 |             0.63 |  -4715.18 |
| EN_CF_EN_60 |   821 |   2.12 |       0.41 |        1.2  |          0.3  |             0.71 |  36975.9  |

## 5. Summary block: setting | live value | best on the state base | holds OOS? | change recommended | panel field
| setting | live value | best on the state base | holds OOS? | change recommended | panel field |
|--|--|--|--|--|--|
| split | 70/30 | SP50 (L1M cut 20.1%, dmean -4574) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | L2SplitPct |
| resting offset (min dip) | 3 pts | DIP4 (L1M cut 28.3%, dmean -1868) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | L2GateMinDipPts |
| confirmations required | 1 of 8 | (pending) | pending | no (pending) | L2GateRequired |
| which confirmation (alone) | all 8, 1 needed | (pending) | pending | no (pending) | code (GATE list); no panel field |
| stages | 1 | STG2 (L1M cut -5.8%, dmean -776) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | L2GateStages / L2GateStageStepPts |
| max minutes | 0 (never) | (pending) | pending | no (pending) | L2GateMaxMinutes |
| slice size / cadence | 1 lot / 2 s | SLALL (L1M cut 14.0%, dmean -6875) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | code constant (no panel field) |
| true resting limit | not used (market add) | LIM3_Q0 (L1M cut 36.2%, dmean 1876) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | new order type, code change |
| add cancelled on exit | cancelled | PERSIST (L1M cut -12.3%, dmean -3275) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | code (L2Disarm) |
| P7 PB3B confirm (pattern / tf / sessions / dip / minutes) | three-bar, 45 s, nyam+nypm, dip 0, 0 min | CF_60 (L1M cut 25.5%, dmean -4661) | pending stage B (PRE/X'/HOLD) | no until stage B + walk-forward; live stays | ConfirmPatternA, ConfirmTfSecsA, ConfirmSessionsA, ConfirmMinDip, ConfirmMaxMinutes |

## 6. Per-book / session P&L deltas of the leaders
See /mnt/l2/l2vast/_th_sz/entry/en_book.csv (L6M window months; net by book x session per set).