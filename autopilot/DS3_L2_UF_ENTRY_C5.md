# DS3_L2_UF_ENTRY_C5 - L2-UNTIL-FOUND cycle 5, ENTRY: INFORMATION of the order book at the PE 45-s three-bar confirmation and at the add touch (agent UF-ENTRY, 2026-10-31)
Research only; UNTOUCHED never read. Prereg autopilot/UF_ENTRY_C5_prereg.md sha256 6d417682a8f24ea90b8711ae1fedb6634d56ae09e8b8e28e5b723c033f32ea65 (DECISIONS.md, before any cycle-5 statistic); 496 cells, spec sha256 198db62cc0bdd42421110c831e5b937ba9933167be529c3c27f87562e19853d1; SEL (PRE u X') selection out/uf/entry_c5/pre_sel.json (copy autopilot/UF_ENTRY_C5_PRESEL.json) sha256 5adf43d5c8d4c7d03aa5b54af8b5afd786e69148e407c50e224dbc206bfb305e logged before the one recent look. Own masks (2026 = 20260101..0206, ~5 weeks, a sign only), every frame <= 20260206. Units: pts per planned lot = per contract of final position (the pattern cell is pure wait, F=0, one lot), $/trade at 1 lot = 20 x pts, day-block bootstrap CI, MDE = 2.8 SE; stack = lock engine (C.stack_line) at research lots. Families: A = book/tape/ES state at the confirming candle of the CF2 LEAD (cell tc|45s|R_three|b|near|3|W0, placed events on the 6 engine books n=21,390; PE 4,266); B = the first dip second of the split S (n=27,529) and base C (n=24,244).
Why this family (stated at start in MORNING.md): C2 G3 scored book flags only as binary conditions on catalogue cells; my cycle-2 hazard was a gate; INFO measured signal-second and in-trade states. Nothing measured IC with shuffled / time-shifted placebos on these two event populations.

## Page 1 - the verdict
1. **The order book carries no usable information at the confirming candle of the PE three-bar, and none at the add touch beyond structure.** Of 332 information cells (A 184, B 148), 88 passed the SEL-only criterion (same sign in PRE and X', CI excluding 0, above the within-day-shuffle 95th percentile and above the 60-s-shifted placebo on PRE u X'); in the last 6 months only 10 still pass on L6M and HOLD together (icA|PE|y_b:e_dlt60, icA|ALL6|y_b:n_imb_now, icA|ALL6|y_b:e_dlt60, icB|S:depth, icB|S:t_dlt10, icB|S:s_es_imb_pre, icB|C:depth, icB|C:rel, icB|C:t_dlt10, icB|C:t_dlt30). Their recent IC is 0.01-0.04 against PRE 0.03-0.05; at the confirming candle the largest recent |IC| is 0.04-0.08 with CIs that include 0 (PE n=830 L6M, MDE 0.09-0.12). The walk-forward ridge on all 46 features has IC +0.023 (PE) / -0.030 (all books) in L6M, AUC 0.507 / 0.482: no information, and its skip-worst rules lose (PE -0.2 .. -0.5, all books -1.1 .. -1.3 pts per contract, random-skip rank 0.0-0.46).
2. **At the add touch the only stable relation is STRUCTURE**: dip depth at the trigger second (IC -0.084 S / -0.135 C in L6M, same sign and size in PRE and X'): a deeper fill price is a better fill price. The cancel / refill / activity features (IC +0.03-0.04, PRE and X' alike) are regime proxies: the same features 60 s earlier have the same IC (time-shifted +0.02-0.04), so the gap to the placebo is <= 0.01. The book-imbalance quintiles at the touch (S: top 4.2 vs bottom 0.8 pts per added lot in L6M) reverse in PRE (-0.8 vs +1.3).
3. **The one rule that survives the SEL-only criterion is not a rule.** Prereg-selected `UF5|rule|ALL6|skip-hi20|n_imb_chg` (skip the 20% of confirming candles where NQ imbalance moved most toward the trade in the last 60 s): per contract of the kept trades L6M +0.78 [-0.29,+1.85] (MDE 1.53), HOLD +0.46, PRE +0.45, X' +0.89, 2026 +0.78: positive in all five windows, random-skip rank 0.83-0.98, but every CI includes 0 (the kept trades earn +4.71, the skipped ones +0.67 per contract in L6M: the skipped trades are still positive), and on the lock-engine stack it is -6219$/wk in L6M (-9262+-8962 for a random skip of the same volume): the volume lost costs more than the rate gain. Tier **BEST-AVAILABLE-NEGATIVE**. Cycle RC (max z of 156 rule cells under the random-skip null, 200 common draws): L6M p 0.000, HOLD 0.000, PRE 0.010, X' 0.000 (the maxima are DIFFERENT cells per window); cumulative-adjusted (N_cum = 2,839,696 + 496) p = 1.0.
4. **Post-hoc recent-only lead (looked-data, NOT selected)**: PE, skip the 20% of confirmations where the ES delta (30 s) has already run with the trade (`UF5|rule|PE|skip-hi20|e_dlt30`): per contract L6M +2.53 [+0.80,+4.27], HOLD +2.39, random-skip rank 1.00 / 1.00, PE stack +5371$/wk L6M vs random-skip -147+-1663; but PRE -0.32 and X' -0.91: the exhaustion read (the ES flow has already gone with the trade) is recent-only, the same shape as the other recent leads. Forward-watch only.
5. The pattern itself (not the book): the CF2 LEAD is +4.64 pts per contract (L6M, N; M +2.60; fill 88%) on the filled PE events, +3.93 (M +1.81) over the six books; the same fills entered at market at the SIGNAL earn -1.81 (PE) / -1.61 (all): the difference is the wait-and-fill selection (a limit fills only when price comes back), not book information. The per-planned-lot CF2 number (unfilled = 0) is +2.42 (MDE 3.2).
6. RECENT_WINS rows written (all promote_ok=False). UF_TRIALS +496. DEAD_CELLS +496 (UFE5).

## 1. The pattern cell per contract (population; N primary, M beside)
| arm (filled events, limit at body mid, N basis; M beside) | basis | 2026 (~5 wk) | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| pattern cell, PE | N | -0.47 [-8.58,+7.64] (MDE 11.59; $-9/trade at 1 lot; n=185) | +4.64 [+0.89,+8.39] (MDE 5.36; $+93/trade at 1 lot; n=830) | +4.31 [+0.83,+7.78] (MDE 4.97; $+86/trade at 1 lot; n=933) | +2.09 [-0.33,+4.50] (MDE 3.45; $+42/trade at 1 lot; n=2151) | +2.54 [-0.63,+5.72] (MDE 4.54; $+51/trade at 1 lot; n=849) |
| pattern cell, PE | M | -2.42 | +2.60 | +2.29 | +0.85 | +1.93 |
| fill rate PE | - | 0.89 | 0.90 | 0.91 | 0.92 | 0.94 |
| SAME fills entered at market at the SIGNAL, PE | N | -7.79 | -1.81 | -1.43 | -2.94 | -2.14 |
| pattern minus market-at-signal on the same fills, PE | N | +7.32 [+3.67,+10.98] | +6.45 [+4.62,+8.28] | +5.74 [+3.87,+7.62] | +5.02 [+3.79,+6.25] | +4.68 [+3.13,+6.24] |
| pattern cell, ALL6 | N | +3.44 [-2.45,+9.33] (MDE 8.41; $+69/trade at 1 lot; n=902) | +3.93 [+1.31,+6.55] (MDE 3.74; $+79/trade at 1 lot; n=3943) | +3.32 [+0.88,+5.76] (MDE 3.49; $+66/trade at 1 lot; n=4457) | +2.41 [+0.63,+4.19] (MDE 2.54; $+48/trade at 1 lot; n=10178) | +1.56 [-0.91,+4.04] (MDE 3.54; $+31/trade at 1 lot; n=4216) |
| pattern cell, ALL6 | M | +1.25 | +1.81 | +1.25 | +1.14 | +0.91 |
| fill rate ALL6 | - | 0.86 | 0.86 | 0.86 | 0.88 | 0.90 |
| SAME fills entered at market at the SIGNAL, ALL6 | N | -1.89 | -1.61 | -2.04 | -2.58 | -2.05 |
| pattern minus market-at-signal on the same fills, ALL6 | N | +5.33 [+3.04,+7.63] | +5.53 [+4.41,+6.66] | +5.36 [+4.22,+6.51] | +4.99 [+4.24,+5.73] | +3.61 [+2.70,+4.53] |

## 2. Information map (IC = Spearman, recent first; blocks)
| block | cells | SEL-informative | still informative in L6M+HOLD (same sign, CI excl. 0, > shuffle p95, > time-shifted) | mean abs IC PRE | mean abs IC L6M | mean abs IC HOLD |
|--|--|--|--|--|--|--|
| icA|ALL6|m30 | 46 | 4 | 0 | 0.012 | 0.013 | 0.012 |
| icA|ALL6|y_b | 46 | 8 | 2 | 0.013 | 0.019 | 0.017 |
| icA|PE|m30 | 46 | 7 | 0 | 0.028 | 0.024 | 0.024 |
| icA|PE|y_b | 46 | 8 | 1 | 0.022 | 0.025 | 0.026 |
| icB|C | 74 | 31 | 4 | 0.023 | 0.019 | 0.019 |
| icB|S | 74 | 30 | 3 | 0.020 | 0.012 | 0.013 |

Top by |IC| in L6M (SELECTED ON LOOKED DATA for the ordering; the SEL-only flag in the last column was fixed before the look):
PE, next 30-s move after the confirming candle:
| feature | Y26 | L6M | HOLD | PRE | X | L6M 95% CI (MDE) | shuffle p95 | time-shift IC | SEL-informative |
|--|--|--|--|--|--|--|--|--|--|--|--|
| g_p25 | -0.047 | -0.065 | -0.062 | -0.009 | -0.040 | [-0.146,+0.015] (0.115) | 0.032 | +0.057 | no |
| n_own_chg | -0.158 | -0.052 | -0.061 | +0.027 | +0.039 | [-0.113,+0.009] (0.087) | 0.044 | -0.016 | no |
| e_can_opp_pre | +0.180 | +0.047 | +0.045 | -0.023 | -0.002 | [-0.026,+0.121] (0.105) | 0.070 | +0.031 | no |
| g_pull | -0.056 | -0.046 | -0.048 | +0.002 | -0.005 | [-0.113,+0.021] (0.096) | 0.058 | +0.002 | no |
| n_can_own_pre | +0.168 | +0.045 | +0.044 | -0.033 | +0.026 | [-0.029,+0.118] (0.105) | 0.069 | +0.031 | no |
| e_can_own_pre | +0.169 | +0.043 | +0.043 | -0.029 | -0.002 | [-0.031,+0.116] (0.105) | 0.067 | +0.033 | no |

PE, trade outcome (pts per contract):
| feature | Y26 | L6M | HOLD | PRE | X | L6M 95% CI (MDE) | shuffle p95 | time-shift IC | SEL-informative |
|--|--|--|--|--|--|--|--|--|--|--|--|
| e_dlt60 | -0.062 | -0.078 | -0.073 | +0.042 | +0.030 | [-0.139,-0.017] (0.087) | 0.035 | -0.027 | no |
| g_imb10 | -0.089 | -0.070 | -0.062 | -0.024 | +0.007 | [-0.137,-0.003] (0.095) | 0.029 | -0.005 | no |
| e_dlt_pre | -0.081 | -0.068 | -0.057 | +0.047 | +0.036 | [-0.136,+0.000] (0.097) | 0.038 | -0.007 | no |
| e_imb_now | -0.077 | -0.058 | -0.035 | -0.007 | +0.008 | [-0.123,+0.007] (0.093) | 0.056 | -0.066 | no |
| n_imb_now | -0.023 | -0.052 | -0.042 | -0.025 | -0.046 | [-0.114,+0.010] (0.089) | 0.029 | -0.033 | no |
| g_rel_tot8 | -0.104 | -0.050 | -0.054 | -0.005 | +0.025 | [-0.121,+0.022] (0.102) | 0.037 | -0.012 | no |

All six books, trade outcome:
| feature | Y26 | L6M | HOLD | PRE | X | L6M 95% CI (MDE) | shuffle p95 | time-shift IC | SEL-informative |
|--|--|--|--|--|--|--|--|--|--|--|--|
| e_dlt_pre | -0.071 | -0.050 | -0.043 | +0.023 | +0.022 | [-0.093,-0.007] (0.061) | 0.029 | -0.009 | no |
| e_dlt60 | -0.044 | -0.048 | -0.042 | +0.020 | +0.003 | [-0.090,-0.005] (0.061) | 0.026 | -0.010 | no |
| n_imb_now | -0.016 | -0.044 | -0.042 | -0.007 | -0.033 | [-0.088,-0.001] (0.062) | 0.009 | +0.007 | no |
| esnq_div | +0.018 | +0.039 | +0.039 | +0.016 | +0.013 | [-0.003,+0.082] (0.061) | 0.040 | -0.007 | no |
| n_imb_chg | -0.026 | -0.038 | -0.030 | -0.001 | -0.038 | [-0.080,+0.004] (0.060) | 0.016 | +0.013 | no |
| g_imb10 | -0.031 | -0.038 | -0.037 | +0.005 | -0.025 | [-0.080,+0.005] (0.061) | 0.016 | +0.036 | no |

All six books, next 30-s move:
| feature | Y26 | L6M | HOLD | PRE | X | L6M 95% CI (MDE) | shuffle p95 | time-shift IC | SEL-informative |
|--|--|--|--|--|--|--|--|--|--|--|--|
| n_depth_chg | -0.024 | +0.029 | +0.019 | +0.007 | -0.005 | [-0.015,+0.073] (0.063) | 0.029 | +0.009 | no |
| e_dlt60 | -0.064 | -0.027 | -0.027 | -0.021 | -0.016 | [-0.066,+0.012] (0.055) | 0.021 | +0.007 | no |
| n_imb_chg | +0.007 | -0.026 | -0.018 | -0.002 | +0.024 | [-0.062,+0.010] (0.051) | 0.026 | -0.010 | no |
| e_dlt_pre | -0.078 | -0.026 | -0.023 | -0.008 | +0.013 | [-0.064,+0.012] (0.054) | 0.023 | +0.005 | no |
| g_pull | -0.015 | -0.025 | -0.027 | -0.001 | -0.004 | [-0.065,+0.015] (0.057) | 0.016 | +0.014 | no |
| n_imb_pre | +0.046 | +0.025 | +0.019 | -0.010 | -0.028 | [-0.015,+0.064] (0.057) | 0.016 | +0.043 | no |

Add touch, split S (outcome = marginal pts per added lot):
| feature | Y26 | L6M | HOLD | PRE | X | L6M 95% CI (MDE) | shuffle p95 | time-shift IC | SEL-informative |
|--|--|--|--|--|--|--|--|--|--|--|--|
| depth | -0.113 | -0.084 | -0.078 | -0.118 | -0.110 | [-0.114,-0.055] (0.042) | 0.022 | +nan | yes |
| t_dlt10 | -0.013 | -0.036 | -0.034 | -0.006 | -0.029 | [-0.067,-0.005] (0.044) | 0.018 | -0.013 | no |
| s_es_imb_pre | +0.026 | +0.035 | +0.029 | +0.009 | -0.007 | [+0.002,+0.068] (0.047) | 0.023 | +nan | no |
| te_imb_now | +0.043 | +0.023 | +0.022 | +0.012 | +0.005 | [-0.004,+0.051] (0.040) | 0.017 | +0.005 | no |
| te_can_own_now | +0.047 | +0.023 | +0.029 | +0.040 | +0.018 | [-0.012,+0.058] (0.051) | 0.012 | +0.015 | yes |
| te_imb_pre | +0.037 | +0.022 | +0.020 | -0.017 | -0.011 | [-0.012,+0.055] (0.047) | 0.018 | +0.006 | no |

Add touch, base C:
| feature | Y26 | L6M | HOLD | PRE | X | L6M 95% CI (MDE) | shuffle p95 | time-shift IC | SEL-informative |
|--|--|--|--|--|--|--|--|--|--|--|--|
| depth | -0.153 | -0.135 | -0.131 | -0.150 | -0.151 | [-0.166,-0.104] (0.045) | 0.021 | +nan | yes |
| t_dlt10 | -0.059 | -0.058 | -0.055 | -0.038 | -0.043 | [-0.086,-0.029] (0.041) | 0.013 | +0.006 | yes |
| t_dlt30 | +0.021 | -0.042 | -0.043 | -0.017 | -0.021 | [-0.072,-0.013] (0.042) | 0.013 | -0.019 | no |
| te_can_own_now | +0.082 | +0.038 | +0.042 | +0.041 | +0.015 | [-0.001,+0.077] (0.056) | 0.015 | +0.024 | yes |
| te_can_own_pre | +0.084 | +0.037 | +0.040 | +0.035 | +0.011 | [-0.001,+0.075] (0.055) | 0.013 | +0.032 | no |
| t_can_opp_pre | +0.083 | +0.036 | +0.038 | +0.040 | +0.032 | [-0.002,+0.074] (0.054) | 0.016 | +0.033 | no |

| add touch, quintile 1 vs quintile 5 of the feature: mean marginal pts per ADDED lot | L6M | HOLD | PRE | X' |
|--|--|--|--|--|
| S depth | -0.72 vs +3.80 (all +2.68) | -1.54 vs +4.03 (all +2.32) | +1.21 vs +2.95 (all +1.66) | -0.26 vs +1.10 (all +0.32) |
| S t_imb_now | +0.84 vs +4.17 (all +2.68) | -0.20 vs +4.29 (all +2.32) | +1.32 vs -0.78 (all +1.66) | -0.72 vs +3.32 (all +0.32) |
| S t_dlt10 | +1.66 vs -0.52 (all +2.68) | +1.80 vs -0.65 (all +2.32) | -0.01 vs +2.64 (all +1.66) | -1.40 vs -1.08 (all +0.32) |
| S te_can_own_now | +2.35 vs +1.22 (all +2.68) | +2.51 vs +1.04 (all +2.32) | +3.46 vs +3.74 (all +1.66) | +0.25 vs -2.01 (all +0.32) |
| S s_es_rfill_pre | +5.79 vs +0.01 (all +2.68) | +5.05 vs -0.04 (all +2.32) | +1.22 vs +2.36 (all +1.66) | +0.25 vs +0.03 (all +0.32) |
| C depth | -2.77 vs +2.17 (all +2.50) | -3.57 vs +2.58 (all +2.14) | +0.71 vs +1.55 (all +1.66) | +1.36 vs -0.40 (all +0.05) |
| C t_imb_now | +4.06 vs +3.23 (all +2.50) | +3.76 vs +3.54 (all +2.14) | +5.37 vs +0.26 (all +1.66) | -0.61 vs +0.10 (all +0.05) |
| C t_dlt10 | +1.74 vs -1.29 (all +2.50) | +0.81 vs -0.95 (all +2.14) | +0.59 vs +1.13 (all +1.66) | -2.40 vs +1.52 (all +0.05) |
| C te_can_own_now | +1.62 vs -0.67 (all +2.50) | -0.01 vs -0.27 (all +2.14) | +3.39 vs +3.07 (all +1.66) | +0.88 vs -2.39 (all +0.05) |
| C s_es_rfill_pre | +6.00 vs -2.66 (all +2.50) | +5.25 vs -1.04 (all +2.14) | +2.55 vs +2.11 (all +1.66) | +0.77 vs -2.01 (all +0.05) |

## 3. Walk-forward ridge (quarterly refit, trailing 12 months, 46 features)
| walk-forward ridge (46 features) | window | IC | AUC (y>0) | n | skip-worst delta per contract (rank vs random skip) |
|--|--|--|--|--|--|
| PE | Y26 | +0.091 | 0.536 | 185 | +2.03 (0.89) |
| PE | L6M | +0.023 | 0.507 | 830 | -0.20 (0.46) |
| PE | HOLD | +0.006 | 0.500 | 933 | -0.37 (0.36) |
| PE | PRE | -0.013 | 0.489 | 2151 | -0.20 (0.34) |
| PE | X | +0.016 | 0.533 | 329 | -0.77 (0.24) |
| ALL6 | Y26 | +0.055 | 0.525 | 902 | +0.34 (0.61) |
| ALL6 | L6M | -0.030 | 0.482 | 3943 | -1.33 (0.00) |
| ALL6 | HOLD | -0.028 | 0.484 | 4457 | -1.25 (0.00) |
| ALL6 | PRE | +0.009 | 0.501 | 10178 | -0.11 (0.35) |
| ALL6 | X | -0.034 | 0.476 | 1683 | -1.27 (0.03) |

## 4. Rules (skip) - per contract, kept vs skipped, random-skip placebo, stack
Prereg-selected first, then the looked-data best cells.
| rule (skip the tail of the feature at the confirming candle) | skipped | basis | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|--|
| UF5|rule|ALL6|skip-hi20|n_imb_chg | 20% | N | +0.78 [-1.04,+2.60] (MDE 2.60) | +0.78 [-0.29,+1.85] (MDE 1.53) | +0.46 [-0.53,+1.45] (MDE 1.42) | +0.45 [-0.33,+1.23] (MDE 1.11) | +0.89 [-0.11,+1.89] (MDE 1.43) |
| UF5|rule|ALL6|skip-hi20|n_imb_chg | 20% | M | +0.73 [-1.03,+2.49] (MDE 2.51) | +0.75 [-0.32,+1.81] (MDE 1.52) | +0.45 [-0.51,+1.41] (MDE 1.37) | +0.46 [-0.30,+1.23] (MDE 1.09) | +0.88 [-0.19,+1.95] (MDE 1.53) |
| ...random-skip rank (same strata, 200 draws) | | - | 0.83 | 0.98 | 0.90 | 0.94 | 0.98 |
| ...kept vs skipped mean per contract (L6M, N) | | N | kept +4.71 / skipped +0.67 | | | | |
| ...lock-engine stack delta of the rule on the pattern stack ($/wk research lots) vs random-skip line mean+-sd | | N | -22767 vs -10868+-15453 | -6219 vs -9262+-8962 | -5720 vs -7535+-8470 | -1283 vs -7749+-4556 | +6640 vs -4192+-5108 |
| UF5|rule|ALL6|skip-hi20|n_imb_now | 20% | N | +0.65 [-1.57,+2.87] (MDE 3.17) | +0.42 [-0.78,+1.61] (MDE 1.71) | +0.31 [-0.83,+1.45] (MDE 1.63) | +0.50 [-0.31,+1.30] (MDE 1.15) | +0.64 [-0.29,+1.57] (MDE 1.33) |
| UF5|rule|ALL6|skip-hi20|n_imb_now | 20% | M | +0.63 [-1.59,+2.85] (MDE 3.17) | +0.42 [-0.70,+1.53] (MDE 1.59) | +0.31 [-0.70,+1.33] (MDE 1.45) | +0.51 [-0.28,+1.29] (MDE 1.12) | +0.63 [-0.30,+1.57] (MDE 1.34) |
| ...random-skip rank (same strata, 200 draws) | | - | 0.82 | 0.85 | 0.82 | 0.95 | 0.91 |
| ...kept vs skipped mean per contract (L6M, N) | | N | kept +4.34 / skipped +2.41 | | | | |
| ...lock-engine stack delta of the rule on the pattern stack ($/wk research lots) vs random-skip line mean+-sd | | N | -9869 vs -24979+-17930 | -8244 vs -13149+-6610 | -5538 vs -10871+-6098 | -3584 vs -11163+-4466 | +6525 vs -2747+-5359 |
| UF5|rule|PE|skip-hi20|e_dlt30 | 19% | N | +0.17 [-3.83,+4.17] (MDE 5.72) | +2.53 [+0.80,+4.27] (MDE 2.47) | +2.39 [+0.80,+3.97] (MDE 2.27) | -0.32 [-1.46,+0.82] (MDE 1.63) | -0.91 [-2.58,+0.77] (MDE 2.39) |
| UF5|rule|PE|skip-hi20|e_dlt30 | 19% | M | +0.17 [-3.76,+4.11] (MDE 5.62) | +2.41 [+0.59,+4.24] (MDE 2.61) | +2.27 [+0.63,+3.91] (MDE 2.35) | -0.33 [-1.49,+0.82] (MDE 1.65) | -0.91 [-2.58,+0.75] (MDE 2.38) |
| ...random-skip rank (same strata, 200 draws) | | - | 0.44 | 1.00 | 1.00 | 0.32 | 0.35 |
| ...kept vs skipped mean per contract (L6M, N) | | N | kept +7.17 / skipped -7.23 | | | | |
| ...lock-engine stack delta of the rule on the pattern stack ($/wk research lots) vs random-skip line mean+-sd | | N | +967 vs +2273+-3425 | +5371 vs -147+-1663 | +4901 vs -175+-1760 | -1798 vs -1914+-1638 | -2044 vs -1468+-1303 |
| UF5|rule|PE|skip-lo20|n_ofi30 | 21% | N | +0.71 [-3.64,+5.05] (MDE 6.20) | +1.94 [-0.03,+3.91] (MDE 2.82) | +1.68 [-0.24,+3.59] (MDE 2.73) | +0.77 [-0.46,+2.00] (MDE 1.76) | +0.87 [-0.80,+2.54] (MDE 2.39) |
| UF5|rule|PE|skip-lo20|n_ofi30 | 21% | M | +0.70 [-3.59,+4.98] (MDE 6.13) | +1.88 [-0.10,+3.86] (MDE 2.83) | +1.62 [-0.16,+3.40] (MDE 2.55) | +0.78 [-0.36,+1.92] (MDE 1.63) | +0.87 [-0.87,+2.61] (MDE 2.48) |
| ...random-skip rank (same strata, 200 draws) | | - | 0.67 | 0.98 | 0.96 | 0.90 | 0.77 |
| ...kept vs skipped mean per contract (L6M, N) | | N | kept +6.58 / skipped -2.09 | | | | |
| ...lock-engine stack delta of the rule on the pattern stack ($/wk research lots) vs random-skip line mean+-sd | | N | -3469 vs -533+-5739 | +3140 vs -563+-2424 | +2351 vs -293+-2548 | -834 vs -942+-1220 | +324 vs -983+-1742 |
| UF5|rule|ALL6|skip-hi20|e_dlt30 | 18% | N | +1.14 [-0.70,+2.98] (MDE 2.63) | +1.45 [+0.40,+2.50] (MDE 1.50) | +1.39 [+0.48,+2.30] (MDE 1.30) | -0.13 [-0.83,+0.56] (MDE 0.99) | -0.58 [-1.64,+0.48] (MDE 1.51) |
| UF5|rule|ALL6|skip-hi20|e_dlt30 | 18% | M | +1.09 [-0.61,+2.79] (MDE 2.42) | +1.37 [+0.37,+2.38] (MDE 1.43) | +1.31 [+0.40,+2.23] (MDE 1.31) | -0.15 [-0.86,+0.55] (MDE 1.01) | -0.58 [-1.56,+0.39] (MDE 1.40) |
| ...random-skip rank (same strata, 200 draws) | | - | 0.61 | 1.00 | 1.00 | 0.28 | 0.02 |
| ...kept vs skipped mean per contract (L6M, N) | | N | kept +5.38 / skipped -3.70 | | | | |
| ...lock-engine stack delta of the rule on the pattern stack ($/wk research lots) vs random-skip line mean+-sd | | N | +1557 vs +1173+-9184 | +10784 vs -7063+-3264 | +11845 vs -7119+-3477 | -9352 vs -8110+-2992 | -11017 vs -4447+-3159 |
| UF5|rule|ALL6|skip-hi20|n_can_own_now | 20% | N | +2.10 [-0.57,+4.76] (MDE 3.80) | +1.28 [-0.15,+2.71] (MDE 2.04) | +1.07 [-0.22,+2.36] (MDE 1.85) | -0.55 [-1.33,+0.24] (MDE 1.13) | -0.02 [-1.16,+1.11] (MDE 1.62) |
| UF5|rule|ALL6|skip-hi20|n_can_own_now | 20% | M | +2.02 [-0.68,+4.72] (MDE 3.85) | +1.20 [-0.23,+2.63] (MDE 2.04) | +1.01 [-0.27,+2.29] (MDE 1.83) | -0.54 [-1.29,+0.20] (MDE 1.06) | -0.03 [-1.16,+1.10] (MDE 1.61) |
| ...random-skip rank (same strata, 200 draws) | | - | 0.94 | 1.00 | 1.00 | 0.04 | 0.59 |
| ...kept vs skipped mean per contract (L6M, N) | | N | kept +5.20 / skipped -0.05 | | | | |
| ...lock-engine stack delta of the rule on the pattern stack ($/wk research lots) vs random-skip line mean+-sd | | N | +8444 vs +3572+-9652 | +2095 vs -7554+-3473 | +1582 vs -9068+-2943 | -13140 vs -9024+-2633 | -8870 vs -7533+-3616 |

## 5. Reality checks
Max-z RC over the 156 skip-rule cells under the random-skip null (common draws): L6M maxz 4.07 p 0.000; HOLD 4.17 p 0.000; PRE 3.29 p 0.010; X' 3.50 p 0.000; cumulative-adjusted p 1.0 in every window (N_cum 2,839,696 + 496, per-cell scaling by 156 cells). The best cell is different in each window (recent best PE skip-hi20 e_dlt30 is PRE/X'-negative) so the window maxima do not agree.
## 6. What was learned
1. The pattern's per-contract value comes from waiting for the fill (selection), not from the book; the book at the confirming candle ranks the outcomes at IC <= 0.04 (recent) and the sign of the best features flips between PRE and the recent windows.
2. The add outcome depends on the fill price (dip depth) and on activity level, not on the book's direction at the touch; this closes the "book state at the add touch" question that cycle 2 asked with a gate: IC and quintiles agree with the hazard result.
3. Skip rules are positive per contract by construction-or-selection and lose volume; against the lot-matched random-skip line the prereg rule is +3.0k L6M but inside the placebo SD (9k).
4. Tier of everything: no rule; information map appended.
## 7. Caveats
Filled-only outcomes (conditioning on the limit fill) are selection-biased vs market-at-signal on the same trades; the within-filled skip deltas are not. IC with mean-imputation for NaN features (ES missing before 2023-08). Placebos: 200 shuffles within day, one 60-s shift. 2026 is ~5 weeks. Stack numbers replace all six books with the pattern cell (ALL6 rules) or PE only (PE rules): a hypothetical strategy, not the live stack; the rule is scored against the random-skip line of the same strategy. MBO order lifetimes not on disk (1-s add/cancel/refill aggregates used).
## 8. Files
code l2vast/ds3/code/uf/ufe5_build.py, ufe5_build_b.py, ufe5_cells.py, ufe5_stats.py, ufe5_select.py, ufe5_look.py, ufe5_final.py, ufe5_more.py, ufe5_report.py; outputs l2vast/ds3/out/uf/entry_c5/ (pop.parquet, pop_b_*.parquet, stats_A/B.pkl, icmap.pkl, final.pkl, more.pkl); cells l2vast/ds3/prereg/UF_ENTRY_C5_cells.csv.
