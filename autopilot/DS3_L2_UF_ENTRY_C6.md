# DS3_L2_UF_ENTRY_C6 - L2-UNTIL-FOUND cycle 6, ENTRY: the SIGNAL-second book against the trade outcome, per contract (agent UF-ENTRY, 2026-10-31)
Research only; UNTOUCHED never read. Prereg autopilot/UF_ENTRY_C6_prereg.md sha256 2b4a4f28d5fc8fcd04aa194b8378091d4e77676effcd7dcc703786893082bdf9 (before any statistic); 313 cells (300 IC + 13 WF ridge), cells hash 305c97ffadf29572437b51bcefa436d1ef3cbe880dc91a8d14a56e500968015a; SEL-only flag file out/uf/entry_c6/pre_sel.json sha256 fab5c3ed53318cb67ed4ade5d91d3d8b613117b11227fcfc97c6b4d6dd2e1677 (copy autopilot/UF_ENTRY_C6_FLAGS.json) logged before the one recent look. Population: every engine-book signal entered at market at the signal with its book bracket (29,800 signals; ST 5,390 HM 4,156 WT 7,685 KB 5,500 SM 1,708 PE 5,361). Outcome per contract (1 lot; $/trade = 20 x pts). Features: 20 sided book/tape/ES features at the signal second (+ the same 60 s earlier as the time-shift placebo). Why this family: INFO measured signed moves, L2EA scored skip/size rules; nobody measured the IC against the bracket outcome itself by book and by D6 session. This closes the signal-second state for ENTRY.

## Page 1 - the verdict
1. **The signal-second order book does not predict the trade outcome.** 280 IC cells (13 populations): 12 pass the SEL-only criterion (PRE u X'), 8 pass in L6M and HOLD together, 5 of those 8 keep the sign in PRE and X'; none of them is both SEL-flagged and recent except ALL6 `e_imb_now` vs the next 60-s move. Largest |IC| in L6M by population: ALL6 0.030, ST 0.060, WT 0.058, KB 0.049, PE 0.073, HM 0.052, SM 0.136 (n=314, MDE 0.16), asia 0.072, london 0.067, nyam 0.046, nypm 0.046; the median MDE per cell is 0.04-0.18, i.e. every IC is inside its MDE except the ALL6 ES-imbalance one. Walk-forward ridge on 46 features: IC +0.004 / +0.005 (L6M / HOLD, all books; AUC 0.510), PRE -0.007; per book L6M ST +0.025, WT +0.033, KB +0.037, PE +0.018, HM -0.060, SM -0.072 (negative AUC 0.46-0.47): no model beats chance out of sample, and HM / SM are below chance in the recent months (AUC 0.46-0.47, about 2 SE: the past fit reverses).
2. **The one consistent relation is small and contrarian**: the ES book leaning with the trade at the signal (sided ES imb5, ALL6) predicts a slightly ADVERSE next 60-s NQ move: IC -0.026 (L6M) / -0.027 (HOLD) / -0.021 (PRE) / -0.020 (X'), above the shuffle and time-shift placebos, same sign in every window; top vs bottom quintile of the next-60-s move: -0.68 pt (L6M), -0.76 (HOLD), -0.56 (PRE), -0.21 (X'), +0.0 (2026). Per contract after costs this is NOT enough to act on: the trades in the top quintile still earn +1.91 (L6M, N) / +1.27 (LIVE-CAL) per contract, so skipping them loses volume, and fading the signal would have to beat a ~1.0-1.5 pt round-trip cost with a 0.7 pt/60-s expectation.
3. Market entry at the signal per contract (the base arm, structure of the fill basis): N basis +2.39 L6M, LIVE-CAL +1.76; its level is the target-fill basis plus the signal books' own edge (SD of one trade 54 pts, so the IC of any book feature of 0.03 is worth 0.03 x 54 = 1.6 pts per SD of the feature at most).
4. No rule is published from this cycle. UF_TRIALS +292; DEAD_CELLS +292 (UFE6; 313 registered, the 21 'close'-session cells have n<100 and were not scored).

## 1. Base arm per contract
| market entry at the signal, ALL6, per contract | 2026 (~5 wk) | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| N basis | +2.94 [-1.36,+7.24] (MDE 6.14; $+59/trade at 1 lot) | +2.39 [+0.14,+4.64] (MDE 3.21; $+48/trade at 1 lot) | +1.90 [-0.19,+3.99] (MDE 2.99; $+38/trade at 1 lot) | +1.48 [+0.00,+2.95] (MDE 2.10; $+30/trade at 1 lot) | +0.70 [-1.31,+2.70] (MDE 2.86; $+14/trade at 1 lot) |
| LIVE-CAL (stop exits 2.45 pt) | +2.31 [-1.96,+6.58] (MDE 6.10; $+46/trade at 1 lot) | +1.76 [-0.35,+3.87] (MDE 3.01; $+35/trade at 1 lot) | +1.27 [-1.00,+3.54] (MDE 3.24; $+25/trade at 1 lot) | +0.83 [-0.57,+2.24] (MDE 2.00; $+17/trade at 1 lot) | +0.09 [-2.03,+2.21] (MDE 3.03; $+2/trade at 1 lot) |

## 2. Information map summary (IC vs outcome, SEL-flag fixed before the look)
| population | outcome | cells | SEL-informative | still informative in L6M+HOLD | max abs IC L6M | median MDE L6M | WF ridge IC L6M / HOLD / PRE (AUC L6M) |
|--|--|--|--|--|--|--|--|
| ALL6 | m60 | 20 | 2 | 1 | 0.026 | 0.037 | - |
| ALL6 | y_L | 20 | 1 | 0 | 0.030 | 0.039 | - |
| ALL6 | y_N | 20 | 1 | 0 | 0.030 | 0.038 | +0.004 / +0.005 / -0.007 (0.510) |
| HM | y_N | 20 | 0 | 0 | 0.052 | 0.088 | -0.060 / -0.061 / -0.004 (0.467) |
| KB | y_N | 20 | 1 | 0 | 0.049 | 0.079 | +0.037 / +0.028 / -0.009 (0.527) |
| PE | y_N | 20 | 1 | 1 | 0.073 | 0.079 | +0.018 / +0.015 / +0.017 (0.510) |
| SM | y_N | 20 | 1 | 1 | 0.136 | 0.157 | -0.072 / -0.068 / -0.017 (0.464) |
| ST | y_N | 20 | 1 | 1 | 0.060 | 0.072 | +0.025 / +0.016 / +0.010 (0.511) |
| WT | y_N | 20 | 2 | 1 | 0.058 | 0.069 | +0.033 / +0.019 / +0.021 (0.507) |
| asia | y_N | 20 | 0 | 1 | 0.072 | 0.076 | +0.058 / +0.037 / -0.011 (0.532) |
| london | y_N | 20 | 0 | 2 | 0.067 | 0.081 | +0.016 / +0.019 / -0.012 (0.501) |
| nyam | y_N | 20 | 2 | 0 | 0.046 | 0.072 | -0.031 / -0.025 / +0.018 (0.485) |
| nypm | y_N | 20 | 0 | 0 | 0.046 | 0.098 | -0.004 / -0.000 / -0.005 (0.492) |
| pre | y_N | 20 | 0 | 0 | 0.121 | 0.178 | +0.000 / -0.016 / -0.010 (0.488) |

Largest |IC| in L6M (ordered on looked data; the SEL flag in the last column was fixed beforehand):
| population | outcome | feature | 2026 | L6M [CI] (MDE) | HOLD | PRE | X' | shuffle p95 | time-shift IC | SEL-flag |
|--|--|--|--|--|--|--|--|--|--|--|
| SM | y_N | g_micro | +nan | +0.136 [+0.009,+0.262] (0.181) | +0.093 | -0.043 | +0.010 | 0.139 | +0.002 | no |
| SM | y_N | g_d5 | +nan | -0.134 [-0.266,-0.001] (0.190) | -0.131 | +0.014 | +0.088 | -0.016 | +0.142 | no |
| SM | y_N | n_dlt30 | +nan | -0.129 [-0.232,-0.025] (0.148) | -0.129 | -0.016 | -0.008 | 0.007 | +0.092 | no |
| pre | y_N | g_micro | +nan | +0.121 [-0.004,+0.246] (0.178) | +0.105 | +0.002 | -0.043 | 0.130 | +0.226 | no |
| SM | y_N | n_imb_now | +nan | +0.120 [+0.012,+0.229] (0.155) | +0.098 | -0.046 | -0.103 | 0.115 | +0.087 | no |
| SM | y_N | n_ofi30 | +nan | -0.106 [-0.211,-0.002] (0.149) | -0.096 | -0.062 | -0.005 | 0.043 | +0.057 | no |
| SM | y_N | n_imb_chg | +nan | +0.102 [-0.002,+0.207] (0.149) | +0.105 | -0.034 | -0.052 | 0.122 | +0.189 | no |
| SM | y_N | esnq_div | +nan | -0.093 [-0.209,+0.022] (0.166) | -0.078 | +0.074 | +0.006 | 0.064 | -0.074 | yes |
| SM | y_N | n_dlt60 | +nan | -0.087 [-0.202,+0.029] (0.165) | -0.090 | +0.022 | +0.017 | 0.040 | +0.072 | no |
| pre | y_N | g_imbmin30 | +nan | +0.079 [-0.062,+0.219] (0.201) | +0.044 | +0.011 | -0.025 | 0.166 | +0.153 | no |
| SM | y_N | n_own_chg | +nan | +0.075 [-0.029,+0.180] (0.149) | +0.066 | -0.040 | +0.081 | 0.132 | +0.141 | no |
| PE | y_N | g_absr | -0.012 | -0.073 [-0.127,-0.019] (0.077) | -0.063 | -0.001 | +0.048 | 0.034 | -0.093 | no |
| SM | y_N | n_rfail_pre | +nan | +0.072 [-0.035,+0.179] (0.153) | +0.061 | +0.017 | -0.064 | 0.092 | -0.038 | no |
| asia | y_N | g_rel_tot8 | +0.055 | +0.072 [+0.011,+0.133] (0.087) | +0.057 | -0.009 | -0.004 | 0.066 | +0.020 | no |

Cells that pass in L6M and HOLD together (same sign, CI excluding 0, above shuffle p95 and time-shift):
| population | outcome | feature | L6M | HOLD | PRE | X' | SEL-flag |
|--|--|--|--|--|--|--|--|
| ALL6 | m60 | e_imb_now | -0.026 | -0.027 | -0.021 | -0.020 | yes |
| ST | y_N | n_imb_now | -0.060 | -0.060 | -0.013 | +0.074 | no |
| WT | y_N | g_micro | +0.058 | +0.047 | +0.003 | +0.062 | no |
| SM | y_N | n_dlt30 | -0.129 | -0.129 | -0.016 | -0.008 | no |
| PE | y_N | g_rel_tot8 | +0.066 | +0.066 | +0.021 | -0.007 | no |
| asia | y_N | g_rel_tot8 | +0.072 | +0.057 | -0.009 | -0.004 | no |
| london | y_N | n_ofi30 | -0.062 | -0.058 | -0.021 | -0.005 | no |
| london | y_N | e_imb_now | +0.067 | +0.072 | +0.027 | +0.044 | no |

## 3. The ES-imbalance relation (quintiles; ALL6 signals with an ES book, i.e. from 2023-08)
| ES imbalance (sided) at the signal, quintile 1 (against) vs 5 (with); ALL6 with ES | window | n | next-60-s move Q1 / Q5 | trade pts per contract N Q1 / Q5 | LIVE-CAL Q1 / Q5 | all |
|--|--|--|--|--|--|--|
| e_imb_now | Y26 | 1529 | -0.01 / -0.11 | +0.95 / +1.11 | +0.30 / +0.44 | +2.94 |
| e_imb_now | L6M | 6636 | +0.34 / -0.34 | +2.66 / +1.91 | +2.02 / +1.27 | +2.39 |
| e_imb_now | HOLD | 7331 | +0.34 / -0.42 | +2.06 / +1.27 | +1.42 / +0.62 | +1.90 |
| e_imb_now | PRE | 16616 | -0.09 / -0.65 | +2.91 / +2.16 | +2.29 / +1.52 | +1.48 |
| e_imb_now | X | 3714 | +0.25 / +0.04 | +3.67 / -0.42 | +3.09 / -1.06 | +1.24 |

## 4. What was learned
1. Together with cycle 5: neither at the signal second (outcome IC <= 0.03 pooled, <= 0.07 per book / session) nor at the pattern confirmation nor at the add touch does the NQ/ES book carry information above 0.01-0.02 IC over its placebos; the touch (imb1 / micro offset, INFO) is the only L1 relation and is below the cost of acting.
2. Per-book recent IC of the ridge is negative for HM / SM (-0.06 / -0.07, AUC 0.46): any book-state rule fitted on the past is worse than random for those two books now.
3. Sessions are not different: Asia / London IC are not larger (0.07 / 0.07 vs MDE 0.08).
## 5. Caveats
Pooled IC across books uses per-population ranks (book bracket differences absorbed by the rank). ES features NaN before 2023-08 (mean-imputed in ranks). 2026 is 5 weeks. Close session (n<100 per window) not scored. The ridge trains on trades entered before refit-3 days (closing-time leakage limited to <=2 days). No rule cells: skip/size rules on book state were scored in L2EA, cycles 2 and 5.
## 6. Files
code l2vast/ds3/code/uf/ufe6_build.py, ufe6_stats.py, ufe6_flags.py, ufe6_look.py, ufe6_report.py; outputs l2vast/ds3/out/uf/entry_c6/.
