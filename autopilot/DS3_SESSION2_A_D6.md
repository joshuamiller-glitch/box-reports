# DS3_SESSION2_A_D6 - live-latency replay of the D6 legs (D3SA, DIRECTIVE_D6_PRIORITY item 2), 2026-10-28
Research only; no live/execution-server/chart change; UNTOUCHED (after 2026-02-06) never read. Prereg SSA_prereg.md sha256 73f0a1cab5b210ace5f503abf3b69e061ea24ccfc5468eca3736baa65cc8e762 + SSA_D6_addendum.md sha256 e9742d74c6c5cefe974f6d421bbc0fe8414054e9e9984f5ebb1c43fd3017d3cd (sizing-advice rule). Replay: ssa_direct.py on raw NQ mbp-10, 35 months 2023-04..2026-02 (pass 1) + 22 months pass 2 (PB7/TB4 entries), 2024-06 re-run once after a memguard kill (user-authorised). Data: l2vast/ds3/out/ssa/ (cs_scores.csv = all 351 replayed cell-sessions, d6_legs.csv, pairs_rescore.csv, verdict.md).

## 1. Verdict (plain)
- **Nothing in the IC / SF family survives live fills.** IF_30s_eb (ASIA and PREOPEN), IF_15s_eb (NY-AM), CRT_M15_M1_close_ib, CRT_M15_M1_close and CRT_H1_30s_close (LONDON) are all NEGATIVE on the MEASURED basis in HOLD: -1.3 to -3.9 pts/trade (stored +0.8 to +3.3); the 95% CI excludes zero for five of the six (PREOPEN is -1.29 [-3.22, +0.65], n=294); they are also negative at 1 s, on CONSERVATIVE and without the target correction. Reason: the stored rows book stop-outs at about -2.3 pts on a 6.5-pt stop (the P9 mapped stop credit, +4 pt in 2025-26, measured on 60-pt brackets), while a stop-market walking the displayed book loses the stop distance plus about 1 pt; about 80% of IF trades are stop-outs (IF_30s_eb ASIA PRE: replay stop exits average -8.0 pts vs stored -2.3). This is the IC family's own warning ("Mapped-fill dependence" in its spec) confirmed. The IF/CRT D6 legs should not run as specified.
- **ba2/HM_t75_s90 NY-AM survives (half size):** MEASURED HOLD +5.45 pts/trade (stored +9.25; n=197), H25 +1.59, H26 +20.6, 1-s delay +6.52, CONSERVATIVE +8.70, harsh +6.55, 2023 span +9.63. It is inside its MDE (15.2; 95% lower bound -5.6): a candidate, not a proven edge.
- **ba2/SM_t60_sst ASIA:** MEASURED HOLD +0.42 (stored +2.55) but H25 -0.66 (fails the gate) and 1-s delay -0.56: minimum. **ba2/KB_t60_s75 ASIA:** MEASURED HOLD -1.02 (stored +3.26; CONSERVATIVE +1.10): do not run on the measured basis.
- **PB7_PB5 ASIA** (fixed 60/60): MEASURED HOLD +1.42 (stored +4.78) but H26 -1.54: minimum. **TB4W** +0.34 (stored +2.73), H25 -1.81, 1-s +0.03: minimum. **TB4B** -9.02 (DEAD-IN-HOLD on stored too): do not run. **E1A_RENKOC5_A3_r48:** dynamic exit (3xATR14 stop, Renko-brick exit), NOT replayed; stored basis +11.86 only: minimum (monitoring size) until a measured series exists.
- **Pairs:** 19 of the 27 PAIR-PASS pairs are complete (both legs replayed); **0 have a positive HOLD add on MEASURED at 20% risk.** The other 8 (P06, P10, P12, P13, P14, P15, P26, P38) contain a non-replayed PRO1/d4a/E1C/S5 partner leg together with an IC/CRT leg that fails on its own measured basis, so the partner cannot be added to a failing leg to rescue the pair here. Carriers: not re-run (see 6).
- **94 clusters:** 56 of the 94 representatives were replayable; **3 of 56 survive on MEASURED** (5 at 1-s delay; all 3 also CONSERVATIVE-stress yes); 38 representatives (T-PB 12, TB4 variants, H4, TR1, e1, PRO...) have dynamic exits and are not replayed in this pass. Over every replayed cell-session 146 of 351 are MEASURED candidates (BA/TSO bracket cells; IC 5 of 99, SF 0 of 12). Best 5 in section 5.

## 2. Bases (as preregistered) and what each number is
STORED = ledger mapped fills (same trades, net of $4.84). MEASURED V0 = market entry +1 tick at the cell's lot class (1/2/5/10 from $1,000 risk, exact shown), stop-market walking the 10 displayed levels at 5 ms latency (DS3_DN_STOPFILL method), limit target at touch + the year x Target P9 correction (-1.4 / -1.5 / -4.2 / -4.3 pts for 2023..2026, applied to every target exit); V1 = same with +1 s. CONSERVATIVE = +3 s, +1 tick entry, stop + 2 ticks, 1-tick trade-through target, no correction (as preregistered). 'Harsh' = CONSERVATIVE + P9 correction: a disclosed extra column (the preregistered CONSERVATIVE is not always harsher than MEASURED because it has no correction). Pts are net of $0.242/pt (4.84/20). $/wk = lots x net pts x 20 over the window's weeks, after the session-book lock (R=$1,000; lock-free beside it). Break-even slippage = the MEASURED mean net pts/trade (extra adverse pts per trade that zeroes it), PRE / HOLD. 'Clears 0 s / 1 s' = V0 / V1 HOLD mean > 0. Tier gates (HOLD mean, H25, H26 > 0) on MEASURED V0; advice per the addendum rule (do not run / minimum / half / full).

## 3. Per leg (HOLD = 2025-07-01..2026-02-06, one logged look)
| leg | session | lots (class / $1k exact) | n HOLD | stored HOLD pts | MEAS V0 HOLD pts [95% CI] | MDE | MEAS V1 HOLD | CONS HOLD | CONS+corr HOLD | MEAS HOLD $/wk (lock / no lock) | MEAS PRE pts | 2023 span (X) MEAS pts | break-even slip (pts) PRE / HOLD | clears 0 s / 1 s | survives stress (CONS / harsh) | advice |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IF_30s_eb | ASIA | 10 / 8.00 | 1756 | +2.19 | -2.73 [-3.57, -1.88] | 1.16 | -2.48 | -1.71 | -2.21 | -6,352 / -28,312 | -1.94 | -1.82 | -1.94 / -2.73 | no / no | no / no | **do not run** |
| IF_30s_eb | PREOPEN | 10 / 7.00 | 294 | +3.01 | -1.29 [-3.22, +0.65] | 2.66 | -1.39 | -1.01 | -1.57 | -1,480 / -2,339 | -1.05 | -1.36 | -1.05 / -1.29 | no / no | no / no | **do not run** |
| IF_15s_eb | NY-AM | 10 / 7.00 | 1493 | +3.27 | -2.20 [-3.36, -1.05] | 1.59 | -2.40 | -1.61 | -2.05 | -2,591 / -15,459 | -1.50 | -1.53 | -1.50 / -2.20 | no / no | no / no | **do not run** |
| CRT_M15_M1_close_ib | LONDON | 10 / 8.00 | 574 | +0.81 | -3.86 [-4.57, -3.15] | 0.97 | -3.94 | -2.49 | -3.65 | -7,299 / -10,128 | -2.49 | -2.37 | -2.49 / -3.86 | no / no | no / no | **do not run** |
| CRT_M15_M1_close | LONDON | 10 / 8.00 | 1399 | +1.31 | -3.55 [-3.92, -3.18] | 0.51 | -3.55 | -2.06 | -3.37 | -10,122 / -23,637 | -2.51 | -2.16 | -2.51 / -3.55 | no / no | no / no | **do not run** |
| CRT_H1_30s_close | LONDON | 10 / 9.00 | 399 | +2.30 | -3.18 [-3.98, -2.38] | 1.10 | -3.10 | -2.32 | -3.07 | -5,780 / -6,888 | -2.12 | -1.71 | -2.12 / -3.18 | no / no | no / no | **do not run** |
| ba2/KB_t60_s75 | ASIA | 1 / 1.00 | 318 | +3.26 | -1.02 [-7.99, +5.95] | 9.57 | -1.61 | +1.10 | -1.14 | -323 / -202 | +4.43 | -0.96 | +4.43 / -1.02 | no / no | yes / no | **do not run** |
| ba2/SM_t60_sst | ASIA | 2 / 2.00 | 123 | +2.55 | +0.42 [-6.35, +7.19] | 9.29 | -0.56 | +1.22 | -0.05 | 59 / 32 | +6.51 | +4.41 | +6.51 / +0.42 | yes / no | no / no | **minimum** |
| ba2/HM_t75_s90 | NY-AM | 1 / 1.00 | 197 | +9.25 | +5.45 [-5.65, +16.54] | 15.23 | +6.52 | +8.70 | +6.55 | 579 / 671 | +10.13 | +9.63 | +10.13 / +5.45 | yes / yes | yes / yes | **half** |
| PB7_PB5_depth_atr0.5_W15_s+0 | ASIA | 1 / 0.83 | 191 | +4.78 | +1.42 [-6.71, +9.56] | 11.17 | +1.36 | +3.02 | +0.80 | 107 / 170 | +9.74 | +4.68 | +9.74 / +1.42 | yes / yes | yes / no | **minimum** |
| E1A_RENKOC5_A3_r48 | ASIA | not replayed | - | stored HOLD +11.86 | - | - | - | - | - | - | stored PRE +11.96 | stored X +0.20 | - | - | - | **minimum** (stored basis only) |
| TB4W_03_time_15s_ST3_E20_1_T2_ntime14 | ASIA | 1 / 0.83 | 367 | +2.73 | +0.34 [-6.35, +7.04] | 9.19 | +0.03 | +2.37 | +0.19 | 421 / 78 | +3.95 | -1.00 | +3.95 / +0.34 | yes / yes | yes / no | **minimum** |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | ASIA | 1 / 0.83 | 200 | -5.04 | -9.02 [-17.45, -0.59] | 11.57 | -8.42 | -7.53 | -9.39 | -1,159 / -1,128 | +6.76 | +0.49 | +6.76 / -9.02 | no / no | no / no | **do not run** |

## 4. Per leg, all bases: PRE / HOLD / halves / 2023 span / by year
| leg | session | basis | PRE pts | PRE $/wk (lock) | HOLD pts | HOLD $/wk (lock) | H25 pts | H26 pts | X pts | X $/wk (lock) | 2023 / 2024 / 2025 / 2026 pts | trades/wk (PRE) | missing share PRE / HOLD, months |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| IF_30s_eb | ASIA | STORED | 1.99 | 5,684 | 2.19 | 9,073 | 2.45 | 1.26 | -0.90 | -2,600 | -0.91 / +1.19 / +2.60 / +1.26 | 41.5 | 0.005 / 0.004 2023-06,2023-09,2023-12,2024-03,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| IF_30s_eb | ASIA | MEASURED V0 | -1.94 | -3,994 | -2.73 | -6,352 | -2.76 | -2.60 | -1.82 | -3,968 | -1.79 / -1.29 / -2.73 / -2.60 | 41.3 | 0.005 / 0.004 2023-06,2023-09,2023-12,2024-03,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| IF_30s_eb | ASIA | MEASURED V1 | -2.04 | -4,679 | -2.48 | -6,365 | -2.54 | -2.25 | -1.93 | -3,591 | -1.91 / -1.40 / -2.67 / -2.25 | 41.3 | 0.005 / 0.004 2023-06,2023-09,2023-12,2024-03,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| IF_30s_eb | ASIA | CONSERVATIVE | -1.36 | -3,805 | -1.71 | -5,634 | -1.73 | -1.66 | -1.65 | -2,603 | -1.63 / -0.83 / -1.86 / -1.66 | 41.3 | 0.005 / 0.004 2023-06,2023-09,2023-12,2024-03,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| IF_30s_eb | PREOPEN | STORED | 2.29 | 2,698 | 3.01 | 4,532 | 2.76 | 4.33 | -0.40 | -282 | -0.29 / +1.80 / +2.66 / +4.33 | 9.5 | 0.000 / 0.000 nan |
| IF_30s_eb | PREOPEN | MEASURED V0 | -1.05 | -1,368 | -1.29 | -1,480 | -1.51 | -0.13 | -1.36 | -1,542 | -0.86 / -0.46 / -2.19 / -0.13 | 9.5 | 0.000 / 0.000 nan |
| IF_30s_eb | PREOPEN | MEASURED V1 | -0.91 | -1,260 | -1.39 | -1,641 | -1.67 | 0.09 | -1.72 | -1,921 | -1.23 / -0.31 / -2.27 / +0.09 | 9.5 | 0.000 / 0.000 nan |
| IF_30s_eb | PREOPEN | CONSERVATIVE | -0.33 | -796 | -1.01 | -1,437 | -1.30 | 0.47 | -1.22 | -1,432 | -0.83 / +0.14 / -1.60 / +0.47 | 9.5 | 0.000 / 0.000 nan |
| IF_15s_eb | NY-AM | STORED | 2.49 | 7,555 | 3.27 | 9,003 | 3.54 | 1.79 | -0.38 | -117 | -0.62 / +2.04 / +3.36 / +1.79 | 40.7 | 0.000 / 0.000 nan |
| IF_15s_eb | NY-AM | MEASURED V0 | -1.50 | -894 | -2.20 | -2,591 | -2.15 | -2.50 | -1.53 | -1,830 | -1.49 / -0.92 / -2.36 / -2.50 | 40.7 | 0.000 / 0.000 nan |
| IF_15s_eb | NY-AM | MEASURED V1 | -1.67 | -1,278 | -2.40 | -4,036 | -2.01 | -4.62 | -1.42 | -1,284 | -1.46 / -1.15 / -2.24 / -4.62 | 40.7 | 0.000 / 0.000 nan |
| IF_15s_eb | NY-AM | CONSERVATIVE | -1.14 | -299 | -1.61 | -4,477 | -1.38 | -2.94 | -1.55 | -2,352 | -1.51 / -0.72 / -1.67 / -2.94 | 40.7 | 0.000 / 0.000 nan |
| CRT_M15_M1_close_ib | LONDON | STORED | 1.57 | 3,453 | 0.81 | 3,380 | 0.72 | 1.12 | -1.35 | -1,637 | -1.48 / +0.97 / +1.55 / +1.12 | 17.4 | 0.000 / 0.000 nan |
| CRT_M15_M1_close_ib | LONDON | MEASURED V0 | -2.49 | -4,645 | -3.86 | -7,299 | -3.66 | -4.53 | -2.37 | -2,869 | -2.27 / -1.95 / -3.35 / -4.53 | 17.4 | 0.000 / 0.000 nan |
| CRT_M15_M1_close_ib | LONDON | MEASURED V1 | -2.61 | -4,478 | -3.94 | -7,284 | -3.78 | -4.44 | -2.24 | -2,494 | -2.12 / -1.83 / -3.63 / -4.44 | 17.4 | 0.000 / 0.000 nan |
| CRT_M15_M1_close_ib | LONDON | CONSERVATIVE | -1.53 | -2,725 | -2.49 | -4,585 | -2.44 | -2.67 | -1.99 | -2,363 | -1.90 / -1.29 / -2.11 / -2.67 | 17.4 | 0.000 / 0.000 nan |
| CRT_M15_M1_close | LONDON | STORED | 1.11 | 5,715 | 1.31 | 8,840 | 1.26 | 1.50 | -0.91 | -2,008 | -1.10 / +0.44 / +1.66 / +1.50 | 41.8 | 0.000 / 0.000 nan |
| CRT_M15_M1_close | LONDON | MEASURED V0 | -2.51 | -7,665 | -3.55 | -10,122 | -3.52 | -3.67 | -2.16 | -5,327 | -2.22 / -2.14 / -3.22 / -3.67 | 41.8 | 0.000 / 0.000 nan |
| CRT_M15_M1_close | LONDON | MEASURED V1 | -2.57 | -7,656 | -3.55 | -9,814 | -3.55 | -3.57 | -2.13 | -5,349 | -2.18 / -2.08 / -3.35 / -3.57 | 41.8 | 0.000 / 0.000 nan |
| CRT_M15_M1_close | LONDON | CONSERVATIVE | -1.61 | -4,622 | -2.06 | -6,765 | -2.07 | -2.00 | -1.67 | -4,031 | -1.77 / -1.59 / -1.80 / -2.00 | 41.8 | 0.000 / 0.000 nan |
| CRT_H1_30s_close | LONDON | STORED | 1.95 | 4,321 | 2.30 | 3,877 | 2.83 | 0.38 | -0.13 | -83 | -0.32 / +1.02 / +2.98 / +0.38 | 11.9 | 0.000 / 0.000 nan |
| CRT_H1_30s_close | LONDON | MEASURED V0 | -2.12 | -2,921 | -3.18 | -5,780 | -2.86 | -4.35 | -1.71 | -1,831 | -1.87 / -1.64 / -2.71 / -4.35 | 11.9 | 0.000 / 0.000 nan |
| CRT_H1_30s_close | LONDON | MEASURED V1 | -2.32 | -3,209 | -3.10 | -5,603 | -2.82 | -4.14 | -1.62 | -1,790 | -1.83 / -1.71 / -2.87 / -4.14 | 11.9 | 0.000 / 0.000 nan |
| CRT_H1_30s_close | LONDON | CONSERVATIVE | -1.55 | -2,164 | -2.32 | -4,648 | -2.10 | -3.13 | -1.17 | -1,310 | -1.41 / -1.13 / -1.99 / -3.13 | 11.9 | 0.000 / 0.000 nan |
| ba2/KB_t60_s75 | ASIA | STORED | 7.48 | 1,160 | 3.26 | 396 | 2.73 | 5.03 | 0.68 | 47 | +3.56 / +5.82 / +5.21 / +5.03 | 9.4 | 0.009 / 0.009 2023-06,2023-09,2023-12,2024-03,2024-06,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| ba2/KB_t60_s75 | ASIA | MEASURED V0 | 4.43 | 741 | -1.02 | -323 | -1.85 | 1.71 | -0.96 | -129 | +1.85 / +3.78 / +0.92 / +1.71 | 9.3 | 0.009 / 0.009 2023-06,2023-09,2023-12,2024-03,2024-06,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| ba2/KB_t60_s75 | ASIA | MEASURED V1 | 4.03 | 645 | -1.61 | -449 | -2.34 | 0.80 | -1.62 | -199 | +1.12 / +3.63 / +0.32 / +0.80 | 9.3 | 0.009 / 0.009 2023-06,2023-09,2023-12,2024-03,2024-06,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| ba2/KB_t60_s75 | ASIA | CONSERVATIVE | 6.25 | 965 | 1.10 | 113 | 0.39 | 3.46 | -0.85 | -117 | +1.86 / +4.47 / +3.65 / +3.46 | 9.3 | 0.009 / 0.009 2023-06,2023-09,2023-12,2024-03,2024-06,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| ba2/SM_t60_sst | ASIA | STORED | 7.95 | 1,051 | 2.55 | 293 | 1.49 | 6.96 | 5.02 | 529 | +4.89 / +6.40 / +6.00 / +6.96 | 3.5 | 0.000 / 0.000 2023-06 |
| ba2/SM_t60_sst | ASIA | MEASURED V0 | 6.51 | 852 | 0.42 | 59 | -0.66 | 4.88 | 4.41 | 454 | +3.66 / +6.06 / +3.55 / +4.88 | 3.5 | 0.000 / 0.000 2023-06 |
| ba2/SM_t60_sst | ASIA | MEASURED V1 | 5.56 | 760 | -0.56 | -136 | -1.87 | 4.86 | 4.42 | 455 | +3.66 / +5.96 / +1.68 / +4.86 | 3.5 | 0.000 / 0.000 2023-06 |
| ba2/SM_t60_sst | ASIA | CONSERVATIVE | 5.94 | 805 | 1.22 | 113 | -0.09 | 6.66 | 3.89 | 389 | +3.13 / +6.19 / +2.89 / +6.66 | 3.5 | 0.000 / 0.000 2023-06 |
| ba2/HM_t75_s90 | NY-AM | STORED | 12.47 | 1,409 | 9.25 | 1,030 | 4.34 | 28.51 | 10.77 | 747 | +14.70 / +14.10 / +5.45 / +28.51 | 5.7 | 0.000 / 0.000 nan |
| ba2/HM_t75_s90 | NY-AM | MEASURED V0 | 10.13 | 1,145 | 5.45 | 579 | 1.59 | 20.60 | 9.63 | 668 | +13.50 / +12.26 / +2.58 / +20.60 | 5.7 | 0.000 / 0.000 nan |
| ba2/HM_t75_s90 | NY-AM | MEASURED V1 | 10.90 | 1,233 | 6.52 | 712 | 1.88 | 24.76 | 10.08 | 699 | +14.00 / +12.21 / +3.77 / +24.76 | 5.7 | 0.000 / 0.000 nan |
| ba2/HM_t75_s90 | NY-AM | CONSERVATIVE | 13.03 | 1,473 | 8.70 | 967 | 4.06 | 26.94 | 9.92 | 688 | +13.81 / +13.34 / +6.65 / +26.94 | 5.7 | 0.000 / 0.000 nan |
| PB7_PB5_depth_atr0.5_W15_s+0 | ASIA | STORED | 12.12 | 1,120 | 4.78 | 504 | 5.74 | 2.13 | 4.14 | 252 | +2.04 / +11.82 / +9.47 / +2.13 | 4.6 | 0.006 / 0.005 2023-06,2024-06,2025-06,2025-09 |
| PB7_PB5_depth_atr0.5_W15_s+0 | ASIA | MEASURED V0 | 9.74 | 899 | 1.42 | 107 | 2.50 | -1.54 | 4.68 | 283 | +2.77 / +9.68 / +6.61 / -1.54 | 4.5 | 0.006 / 0.005 2023-06,2024-06,2025-06,2025-09 |
| PB7_PB5_depth_atr0.5_W15_s+0 | ASIA | MEASURED V1 | 9.39 | 868 | 1.36 | 99 | 1.59 | 0.71 | 4.66 | 281 | +2.75 / +9.68 / +5.75 / +0.71 | 4.5 | 0.006 / 0.005 2023-06,2024-06,2025-06,2025-09 |
| PB7_PB5_depth_atr0.5_W15_s+0 | ASIA | CONSERVATIVE | 10.32 | 952 | 3.02 | 287 | 3.87 | 0.69 | 5.34 | 323 | +3.39 / +9.46 / +8.22 / +0.69 | 4.5 | 0.006 / 0.005 2023-06,2024-06,2025-06,2025-09 |
| E1A_RENKOC5_A3_r48 | ASIA | STORED | 11.96 |  | 11.86 |  | 8.55 | 21.01 | 0.20 |  | +0.01 / +12.51 / +10.37 / +21.01 | 5.7 | nan / nan nan |
| TB4W_03_time_15s_ST3_E20_1_T2_ntime14 | ASIA | STORED | 6.44 | 1,109 | 2.73 | 937 | 0.46 | 9.65 | -0.27 | -57 | +0.27 / +6.76 / +3.26 / +9.65 | 10.7 | 0.009 / 0.005 2023-06,2023-09,2023-12,2024-03,2024-06,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| TB4W_03_time_15s_ST3_E20_1_T2_ntime14 | ASIA | MEASURED V0 | 3.95 | 670 | 0.34 | 421 | -1.81 | 6.86 | -1.00 | -136 | -0.44 / +5.75 / -0.01 / +6.86 | 10.6 | 0.009 / 0.005 2023-06,2023-09,2023-12,2024-03,2024-06,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| TB4W_03_time_15s_ST3_E20_1_T2_ntime14 | ASIA | MEASURED V1 | 3.66 | 727 | 0.03 | 352 | -2.21 | 6.84 | -1.48 | -189 | -0.99 / +5.78 / -0.54 / +6.84 | 10.6 | 0.009 / 0.005 2023-06,2023-09,2023-12,2024-03,2024-06,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| TB4W_03_time_15s_ST3_E20_1_T2_ntime14 | ASIA | CONSERVATIVE | 4.61 | 890 | 2.37 | 822 | 0.04 | 9.44 | -1.00 | -137 | -0.51 / +5.52 / +1.70 / +9.44 | 10.6 | 0.009 / 0.005 2023-06,2023-09,2023-12,2024-03,2024-06,2024-09,2024-12,2025-03,2025-06,2025-09,2025-12 |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | ASIA | STORED | 9.47 | 1,169 | -5.04 | -667 | -6.10 | -0.24 | 0.49 | 42 | -0.47 / +8.26 / +3.23 / -0.24 | 6.0 | 0.000 / 0.000 nan |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | ASIA | MEASURED V0 | 6.76 | 846 | -9.02 | -1,159 | -10.42 | -2.64 | 0.49 | 42 | -0.33 / +6.55 / -0.86 / -2.64 | 6.0 | 0.000 / 0.000 nan |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | ASIA | MEASURED V1 | 6.48 | 813 | -8.42 | -1,084 | -9.69 | -2.63 | 0.51 | 43 | -0.33 / +6.13 / -0.54 / -2.63 | 6.0 | 0.000 / 0.000 nan |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | ASIA | CONSERVATIVE | 8.40 | 1,040 | -7.53 | -978 | -8.34 | -3.84 | 1.15 | 99 | +0.31 / +7.46 / +1.48 / -3.84 | 6.0 | 0.000 / 0.000 nan |

2023 span (X, 2023-04..2024-01) and by-year are printed, never a gate. MDE = 2.8 x week-clustered SE of the per-trade mean. 2024-06 was re-run once and is present (the missing-share column shows the residual share of trades without a filled replay row, about 0-1%).

## 5. Survival counts and best clusters (all 351 replayed cell-sessions)
- 94 cluster representatives (best PRE-t cell of each cluster50): 56 replayed on the three bases, 38 not replayed (dynamic exits / no fixed bracket). MEASURED SESSION-CANDIDATE/PASS (V0): **3 of 56** replayed reps; at 1-s delay 5; with CONS stress yes: 3.
- clusters with ANY replayed cell that passes MEASURED: 9 of 57 clusters that have a replayed cell (the 94 clusters in total; the rest have no replayable cell).
- all replayed cell-sessions: 351; MEASURED candidates 146; at 1-s delay 149; CONS stress yes 144; harsh stress yes 131.

| family                  |   cell_sessions |   measured_candidate |   stress_yes |
|:------------------------|----------------:|---------------------:|-------------:|
| BA bracket-assign rows  |              21 |                    6 |           18 |
| BA bracket-assign rows2 |              79 |                   33 |           61 |
| BA bracket-assign rows3 |             119 |                   94 |          116 |
| G3 fam                  |               3 |                    1 |            2 |
| ICT-IC (IC blocks)      |              99 |                    5 |            8 |
| ICT-SF (silver/fvg SF)  |              12 |                    0 |            0 |
| SB (silver-bullet SB)   |               5 |                    3 |            4 |
| T-ENTRY pb4 (TB4)       |               2 |                    0 |            1 |
| T-PB (pullback/PBX TP)  |               1 |                    0 |            1 |
| TSO EM                  |               1 |                    0 |            0 |
| TSO HM10                |               5 |                    3 |            5 |
| TSO SM                  |               1 |                    0 |            1 |
| TSO ST10                |               3 |                    1 |            2 |

Best 5 clusters (best measured cell per cluster, by MEASURED HOLD $/wk after the session-book lock; $ at the lot class, session book alone):

| cell                  | sess   | family                  |   S_hold_mean |   M0_hold_mean |   M0_hold_mde |   M0_pre_mean |   M0_x_mean |   M0_hold_dwk |   M0_hold_dwk_lock |   C_hold_mean | survives_stress   |
|:----------------------|:-------|:------------------------|--------------:|---------------:|--------------:|--------------:|------------:|--------------:|-------------------:|--------------:|:------------------|
| IF_5m_tg_pd           | LONDON | ICT-IC (IC blocks)      |          8.72 |           2.55 |          7.83 |          1.96 |        0.41 |       1963.32 |            1697.68 |          3.18 | yes               |
| ba/A_t40_s75          | NY-AM  | BA bracket-assign rows  |          6.17 |           2.79 |          5.29 |          0.66 |        0.41 |       1369.14 |            1568.66 |          4.81 | yes               |
| ba2/HM_t120_sst       | NY-AM  | BA bracket-assign rows2 |         14.35 |          10.45 |         15.32 |          6.32 |        1.19 |       1676.42 |            1530.84 |         12.06 | yes               |
| ba/SS_HM_ASIA_t75_s60 | ASIA   | BA bracket-assign rows  |          7.65 |           4.96 |          8.52 |          2.96 |       -3.04 |        834.59 |             831.05 |          7.14 | yes               |
| ba2/KB_t90_s90        | NY-AM  | BA bracket-assign rows2 |          3.92 |           1.37 |         13.8  |          7.46 |        8.48 |        216.38 |             402.99 |          1.99 | yes               |

## 6. The 27 PAIR-PASS pairs re-scored (20% risk of stack PRE SD, per-leg session-book lock, scale fixed on PRE of each basis)
| pair | HOLD add $/wk STORED | MEASURED | CONSERVATIVE | HOLD MDE (MEAS) | add in stack's 20 worst weeks STORED / MEASURED |
|---|---|---|---|---|---|
| P00 IF_30s_eb[ASIA] + CRT_M15_M1_close_ib[LONDON] | 23,477 | -45,764 | -30,759 | 10,578 | 173,999 / -664,008 |
| P01 IF_15s_eb[ASIA] + CRT_M15_M1_close_ib[LONDON] | 29,006 | -46,287 | -29,612 | 7,981 | 351,675 / -372,318 |
| P02 IF_30s_eb[ASIA] + CRT_H1_30s_close[LONDON] | 21,217 | -31,812 | -25,737 | 9,125 | 117,267 / -559,434 |
| P03 IF_30s_ea[ASIA] + CRT_H1_30s_close[LONDON] | 23,313 | -37,364 | -28,428 | 9,417 | 133,604 / -549,839 |
| P05 IF_30s_eb[ASIA] + IF_3m_ea[PREOPEN] | 16,822 | -14,155 | -10,588 | 13,326 | 177,859 / -178,727 |
| P08 IF_30s_eb[ASIA] + IF_15s_eb[NY-AM] | 23,046 | -18,185 | -19,150 | 13,040 | 148,188 / -374,906 |
| P09 IF_30s_ea[ASIA] + IF_15s_eb[NY-AM] | 25,352 | -18,315 | -17,811 | 11,836 | 166,156 / -280,417 |
| P11 CRT_M30_M1_close[ASIA] + IF_15s_ea[NY-AM] | 32,148 | -38,265 | -21,077 | 13,382 | 120,084 / -477,519 |
| P16 CRT_M15_M1_close_ib[LONDON] + IF_30s_eb[PREOPEN] | 20,281 | -36,075 | -22,533 | 11,591 | 233,289 / -359,887 |
| P18 CRT_H1_30s_close[LONDON] + IF_30s_eb[PREOPEN] | 17,894 | -23,743 | -19,874 | 9,593 | 178,446 / -278,958 |
| P19 CRT_H1_30s_close[LONDON] + IF_3m_ea[PREOPEN] | 14,612 | -20,291 | -14,748 | 9,207 | 165,466 / -137,498 |
| P20 CRT_M15_M1_close_ib[LONDON] + IF_15s_eb[NY-AM] | 22,618 | -40,687 | -26,051 | 11,266 | 181,788 / -458,390 |
| P21 CRT_M15_M1_close[LONDON] + IF_15s_eb[NY-AM] | 29,479 | -58,028 | -32,710 | 10,227 | 137,656 / -921,764 |
| P22 CRT_M15_M1_close_ib[LONDON] + IF_15s_ea[NY-AM] | 24,078 | -41,129 | -25,539 | 10,900 | 182,031 / -423,976 |
| P23 CRT_M15_M1_close[LONDON] + IF_15s_ea[NY-AM] | 30,616 | -60,969 | -33,077 | 10,187 | 132,038 / -917,899 |
| P28 IF_30s_eb[PREOPEN] + IF_15s_eb[NY-AM] | 22,284 | -8,979 | -11,244 | 13,184 | 236,242 / -67,495 |
| P29 IF_3m_eb[PREOPEN] + IF_15s_eb[NY-AM] | 17,471 | -6,708 | -9,246 | 11,718 | 163,075 / 24,215 |
| P30 IF_30s_eb[PREOPEN] + IF_15s_ea[NY-AM] | 21,322 | -10,691 | -9,790 | 12,685 | 214,522 / -51,816 |
| P31 IF_3m_eb[PREOPEN] + IF_15s_ea[NY-AM] | 17,665 | -9,992 | -8,382 | 11,580 | 153,928 / 34,071 |

The STORED column reproduces the D3SS3 HOLD adds (11-32k), which validates the series construction. Stack-add at 10% and 30%, weekly SD, maxDD, correlation and the worst-20-weeks $ for every pair and basis are in out/ssa/pairs_rescore.csv (|correlation| to the stack is at most 0.42 in HOLD, 0.34 in PRE, 0.31 over the full span; most are near 0). Carriers (PE ASIA, DN ASIA, KB ASIA, KB NY-PM, MV NY-AM) are live-book trades from the stack tables, not cells of the ledger: they were not re-run in this pass. For DN the measured retention is already known (DS3_DN_STOPFILL: 54-68% of the mapped mean with book-walk fills); KB ba2 60/75 ASIA, measured -1.02 here, is the nearest replayed analogue.

## 7. Caveats that matter
1. IC / SF entries are resting limits in the source (gap midpoint / zone retest); here every entry is a MARKET +1 tick at the stored minute END stamp (the user's live-latency rule), which can be up to 59 s after the stored limit fill. A limit-at-zone replay with a queue model would be a different (better-entry) test and is not possible from the stored rows (raw entry prices are not stored). The stop-credit finding does not depend on it: stop-outs are priced at the stop plus the walk.
2. The P9 Target correction (-4.3 pt in 2026) is calibrated on 60-pt brackets and is applied as defined to 20-50 pt IC targets; the no-correction variant (M0nc in cs_scores.csv) leaves IC/SF negative (e.g. IF_30s_eb ASIA HOLD -2.2).
3. The session-book lock is the session book alone, not the live stack's lock. Lots are the nearest of 1/2/5/10; 'sst' stops vary per trade, so lots vary per trade.
4. 38 of the 94 representatives are dynamic-exit cells and are not part of this replay. HM / KB / SM ba2 cells are the live engines with only the bracket changed (D3SSE2).

## 8. Sim spec for survivors (D6 container)
- **ba2/HM_t75_s90, NY-AM (half size):** session window 09:30-12:00 ET by entry time; live HM engine entries, market entry at the signal bar, bracket from the fill: target 75 pt limit / stop 90 pt stop-market (OCO), flat 16:55 ET; lots at $1,000 risk = 1000/(90 x 20) = 0.56 -> 1 lot (class 1) and half size means monitor/1 lot only; costs $4.84 RT per contract; session-book lock -2R/+5R with R = $1,000; assume 0-1 s delay. Spec: DS3_SPEC_ba2_HM_t75_s90_SESSION.md.
- **ba2/SM_t60_sst ASIA, PB7_PB5_depth_atr0.5_W15_s+0 ASIA, TB4W_03_time_15s_ST3_E20_1_T2 ASIA (minimum size, 1 lot):** window 18:00-02:00 ET; rules in DS3_SPEC_ba2_SM_t60_sst_SESSION.md (target 60, structure stop 20-120 pt), DS3_SPEC_PB7_PB5_depth_atr0.5_W15_s+0_SESSION.md (60/60), DS3_SPEC_TB4W_03_time_15s_ST3_E20_1_T2_SESSION.md (240/240 ticks); market entries, flat 16:55 ET, costs $4.84 RT. Measured-positive but inside the MDE and each fails one HOLD half: monitoring size only.
- Not for the container on the measured basis: IF_30s_eb (ASIA, PRE), IF_15s_eb, CRT_M15_M1_close(_ib), CRT_H1_30s_close, ba2/KB_t60_s75 ASIA, TB4B.
