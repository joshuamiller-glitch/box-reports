# SZ_FGH_C1A5 - T-NEXT C1 (sizer/lot-side leads composed on the live-panel base, EXACT) and A5 (ES/RTY measures as NQ signal-second features); 2026-11-10 21:31Z

> Label: EXACT engine rows (ROLLFIX1) for every row marked EXACT, reference = LPB_BASE (live panel: P7 day cap 8,400 + P7 7,4,0,4,0,0 + P7 cut 40/5x/w5/p3, all layers ON; LPB_EMPTY where the SZ-CORE run is missing); the A5 first-order tables are FIRST-ORDER SCREEN ONLY. PRE-PROOF, post-hoc, Shadow only, no PASS claims. Prereg autopilot/SZ_FGH_C1A5_PREREG.md (sha in DECISIONS.md). Standing rules 1/2/2a: layers stay ON; the live setting (LPB) is the reference row; rule 2a PRE mean floor = 25% of the live-panel PRE mean. Inputs to DS3_JOINT_2.md.

## 1. C1 - sizer/lot-side leads composed on LPB (exact, 43 months each as they land)
Leads: A = ATR>=1.6x skip (P7), K = P7 lots cap min(lots,3) (rule layer), V = VT_S2 vol-target step (exact on S1b-COMB: L6M +49.4%, d mean +4,489), V1 = VT_S1 vol-target scale. Composition = multipliers multiply, one rounding, zone HALF last. The same compositions on JN04 are queued when SZ-IJK's rule-mode LPB_JN04 exists.

| stack | months done / common with LPB | cut % L1M / L3M / L6M / HOLD / PRE / X' | d mean $/wk L6M / PRE | eq-mean cut % L6M / PRE | worst-20 cut % L6M / PRE | rule 2a (floor 25% of the live PRE mean) |
|--|--|--|--|--|--|--|
| A (ATR>=1.6 P7 skip) | 43 / 43 | 30.0 / 0.5 / 0.5 / -8.3 / 16.0 / 13.3 | +945 / -222 | 5.3 / 20.1 | +61 / +10 | OK-PRIOR-UNKNOWN-WF (old OK-PRIOR-UNKNOWN-WF) |
| K (P7 lots cap 3) | 3 / 3 | 14.4 / 24.5 / n/a / n/a / n/a / n/a | +nan / +nan | nan / nan | +nan / +nan |  |
| V (VT_S2 vol-target step) | 3 / 3 | 86.6 / 31.7 / n/a / n/a / n/a / n/a | +nan / +nan | nan / nan | +nan / +nan |  |
| R (R11 re-entry any-N30 skip) | pending (0 months done) | - | - | - | - | - |
| F (flip-level skip R6_FL_LIVE) | pending (0 months done) | - | - | - | - | - |
| BO (P7 post-stop 30-min blackout (R5_BO_3)) | 12 / 12 | 12.5 / 2.2 / 2.2 / 4.2 / n/a / n/a | +1674 / +nan | 10.6 / nan | +44 / +nan |  |
| AK (ATR + cap3) | 4 / 4 | 28.7 / 40.6 / n/a / n/a / n/a / n/a | +nan / +nan | nan / nan | +nan / +nan |  |
| AV (ATR + VT_S2) | 4 / 4 | 95.2 / 26.8 / n/a / n/a / n/a / n/a | +nan / +nan | nan / nan | +nan / +nan |  |
| KV (cap3 + VT_S2) | 3 / 3 | 90.1 / 47.6 / n/a / n/a / n/a / n/a | +nan / +nan | nan / nan | +nan / +nan |  |
| AKV (ATR + cap3 + VT_S2) | 4 / 4 | 95.4 / 43.0 / n/a / n/a / n/a / n/a | +nan / +nan | nan / nan | +nan / +nan |  |
| V1 (VT_S1 vol-target scale) | 3 / 3 | 60.6 / 16.5 / n/a / n/a / n/a / n/a | +nan / +nan | nan / nan | +nan / +nan |  |
| AKV1 (ATR + cap3 + VT_S1) | 4 / 4 | 87.5 / 42.3 / n/a / n/a / n/a / n/a | +nan / +nan | nan / nan | +nan / +nan |  |
| ALL (ALL = A+K+V2+R11+FL on the blackout base) | pending (0 months done) | - | - | - | - | - |
| mA (ALL minus ATR skip) | pending (0 months done) | - | - | - | - | - |
| mK (ALL minus cap3) | pending (0 months done) | - | - | - | - | - |
| mV (ALL minus VT_S2) | pending (0 months done) | - | - | - | - | - |
| mR (ALL minus R11) | pending (0 months done) | - | - | - | - | - |
| mF (ALL minus flip skip) | pending (0 months done) | - | - | - | - | - |
| mBO (ALL minus blackout) | pending (0 months done) | - | - | - | - | - |

### Interaction table (pair cut minus the sum of the two single cuts; |interaction| > 10% of either single is flagged)
| pair | L6M: pair / single1 / single2 / interaction | PRE: pair / single1 / single2 / interaction | flag |
|--|--|--|--|--|
| A + K | nan / 0.5 / nan / +nan | nan / 16.0 / nan / +nan | n/a |
| A + V | nan / 0.5 / nan / +nan | nan / 16.0 / nan / +nan | n/a |
| K + V | nan / nan / nan / +nan | nan / nan / nan / +nan | n/a |

### Leave-one-out from ALL (A+K+V2+R11+FL on the blackout base): what each lead contributes inside the joint stack
| stack | L6M cut | PRE cut | d mean L6M | d mean PRE | contribution of the dropped lead (ALL minus this): L6M cut / PRE cut |
|--|--|--|--|--|--|
| ALL | nan | nan | +nan | +nan | - |
| drop ATR skip | nan | nan | +nan | +nan | +nan / +nan |
| drop cap3 | nan | nan | +nan | +nan | +nan / +nan |
| drop VT_S2 | nan | nan | +nan | +nan | +nan / +nan |
| drop R11 | nan | nan | +nan | +nan | +nan / +nan |
| drop flip skip | nan | nan | +nan | +nan | +nan / +nan |
| drop blackout | nan | nan | +nan | +nan | +nan / +nan |

### Leave-one-out from the triple (A+K+V)
| stack | L6M cut | PRE cut | d mean L6M | d mean PRE |
|--|--|--|--|--|
| A+K+V (all three) | nan | nan | +nan | +nan |
| drop A (K+V) | nan | nan | +nan | +nan |
| drop K (A+V) | nan | nan | +nan | +nan |
| drop V (A+K) | nan | nan | +nan | +nan |

Bi-weekly WF between the stacks: pending (common contiguous block of complete months < 12 so far).

## 2. A5 - ES/RTY state-base measures as NQ signal-second features (FIRST-ORDER SCREEN on S1b-COMB, sz_core numbers, ROLL-EXCL) and the D7 EsLeadSize hook
Data: FD-LIQ table xfeat_ES_RTY.parquet (21,135 rows in Z.Base order, causal at the end of second sig-1, signed by trade side; pull/imbalance coverage about 95%, none before 2023-08 so X' is mostly untestable and shows ~0) + an emulation of the D7 EsLeadSize hook (ES last completed 1-min bar in ticks). ES sweep is not built. 2292 cells (163 UP-labelled, never promoted). Bar: recents key (mean equal-mean cut L6M/L3M/L1M) > 0, own placebo p <= .10 on the L6M cut, rule 2a label, family max-stat p, bi-weekly WF of the family. **Family WF (equal-mean picker, 74 refit periods): OOS maxDD cut -9.4%, d mean -5096 $/wk, beats live in 66% of periods -> the family does not pass as a PICKING procedure; individual cells below are leads only.** Family max-stat p (L6M cut) is about 1 for every cell over 2292 cells (labelled, not a kill).

### D7 EsLeadSize hook as shipped (Off by default; ES 1-min move >= 2 ticks WITH the signal x1.5, AGAINST x0.5) - reference row (UP-labelled)
| scope | cut L6M / PRE / X' % | d mean L6M $/wk | recents key | label |
|--|--|--|--|--|
| ALL | -13.3 / -47.3 / -36.0 | +8222 | 24.3 | RECENT-ONLY-UNKNOWN-WF |
| K7 | -4.8 / -11.4 / -6.1 | +2159 | 4.4 | OK-PRIOR-UNKNOWN-WF |
| P7 | 0.4 / -25.6 / -50.4 | +5208 | 23.6 | RECENT-ONLY-UNKNOWN-WF |
| M7 | -20.0 / -9.7 / 0.3 | -736 | -17.4 | OK-PRIOR-UNKNOWN-WF |
| U7 | 4.9 / -4.2 / 1.1 | +884 | 8.4 | OK-PRIOR-UNKNOWN-WF |
| A7 | -2.4 / 1.2 / -3.9 | +410 | -0.7 | OK-PRIOR-UNKNOWN-WF |
| H7 | 2.3 / 2.8 / 5.4 | +555 | 4.5 | OK-PRIOR-UNKNOWN-WF |
| O7 | 0.0 / -0.6 / -2.6 | +29 | 0.1 | OK-PRIOR-UNKNOWN-WF |

### Hook variants, down-only (with x1.0; against x0.5/0.25/0; min ticks 1-6), top 8 by recents key
| technique | params | scope | recents key | cut L6M / L3M / PRE / X' % | d mean L6M / PRE $/wk | label (2a) | own p L6M | chg share |
|--|--|--|--|--|--|--|--|--|
| hook | {"against": 0.0, "live_default": false, "min_ticks": 1, "with_": 1.0} | ALL | 19.6 | 22.2 / 22.2 / 12.7 / -4.4 | -2582 / -1639 | OK-PRIOR-UNKNOWN-WF | 0.13 | 0.17 |
| hook | {"against": 0.0, "live_default": false, "min_ticks": 1, "with_": 1.0} | P7 | 16.6 | 23.1 / 23.1 / 15.1 / -20.4 | -1772 / +284 | OK-PRIOR-UNKNOWN-WF | 0.04 | 0.03 |
| hook | {"against": 0.25, "live_default": false, "min_ticks": 1, "with_": 1.0} | ALL | 16.2 | 17.4 / 17.4 / 8.8 / 5.2 | -1292 / -690 | OK-PRIOR-UNKNOWN-WF | 0.06 | 0.07 |
| hook | {"against": 0.0, "live_default": false, "min_ticks": 6, "with_": 1.0} | P7 | 14.9 | 11.4 / 11.4 / -6.2 / -2.7 | +930 / -149 | OK-PRIOR-UNKNOWN-WF | 0.04 | 0.01 |
| hook | {"against": 0.0, "live_default": false, "min_ticks": 6, "with_": 1.0} | ALL | 13.5 | 10.4 / 10.4 / -6.5 / 2.4 | +268 / -481 | OK-PRIOR-UNKNOWN-WF | 0.06 | 0.04 |
| hook | {"against": 0.5, "live_default": false, "min_ticks": 1, "with_": 1.0} | ALL | 13.1 | 12.8 / 12.8 / 4.8 / 7.0 | -574 / -397 | OK-PRIOR-UNKNOWN-WF | 0.07 | 0.07 |
| hook | {"against": 0.25, "live_default": false, "min_ticks": 1, "with_": 1.0} | P7 | 10.6 | 15.0 / 15.0 / 9.5 / -14.6 | -1098 / +9 | OK-PRIOR-UNKNOWN-WF | 0.06 | 0.03 |
| hook | {"against": 0.25, "live_default": false, "min_ticks": 6, "with_": 1.0} | ALL | 9.7 | 8.4 / 8.4 / -5.8 / -0.1 | +323 / -246 | OK-PRIOR-UNKNOWN-WF | 0.03 | 0.01 |

### Lead / breadth / book-measure gates, down-only, mean cost <= $3k/wk on L6M, own p <= .10 (127 of 2129 down-only cells), top 12 by recents key
| technique | params | scope | recents key | cut L6M / L3M / PRE / X' % | d mean L6M / PRE $/wk | label (2a) | own p L6M | chg share |
|--|--|--|--|--|--|--|--|--|
| qgate | {"feat": "rty_ticks_sg", "m": 0, "q": 0.3, "tail": "low"} | ALL | 66.1 | 49.7 / 64.8 / -5.6 / 0.0 | -2513 / -5384 | RECENT-ONLY-UNKNOWN-WF | 0.01 | 0.28 |
| qgate | {"feat": "x_rty_pull_own5", "m": 0, "q": 0.5, "tail": "high"} | ALL | 57.7 | 48.7 / 48.7 / 46.8 / 0.0 | -874 / -7548 | RECENT-ONLY-UNKNOWN-WF | 0.08 | 0.49 |
| qgate | {"feat": "x_es_pull_net5", "m": 0, "q": 0.3, "tail": "low"} | ALL | 43.1 | 36.7 / 38.0 / 24.0 / 0.0 | -1250 / -6812 | RECENT-ONLY-UNKNOWN-WF | 0.02 | 0.31 |
| qgate | {"feat": "rty_ticks_sg", "m": 0, "q": 0.2, "tail": "low"} | P7 | 42.0 | 34.3 / 43.5 / -1.4 / 0.0 | +209 / -1707 | OK-PRIOR-UNKNOWN-WF | 0.01 | 0.05 |
| qgate | {"feat": "x_es_pull_net5", "m": 0, "q": 0.3, "tail": "low"} | P7 | 41.6 | 32.6 / 32.6 / 33.4 / 0.0 | +149 / -3532 | RECENT-ONLY-UNKNOWN-WF | 0.09 | 0.08 |
| qgate | {"feat": "es_ticks_sg", "m": 0, "q": 0.3, "tail": "low"} | P7 | 39.9 | 32.4 / 42.0 / 15.8 / 0.0 | -2195 / -1188 | OK-PRIOR-UNKNOWN-WF | 0.04 | 0.07 |
| qgate | {"feat": "x_leadR1", "m": 0, "q": 0.1, "tail": "low"} | ALL | 39.7 | 19.7 / 38.5 / -21.2 / 0.0 | +2342 / -3192 | RECENT-ONLY-UNKNOWN-WF | 0.05 | 0.08 |
| breadth | {"cond": "le1", "feat": "x_breadth15", "m": 0} | P7 | 37.8 | 28.2 / 48.0 / -0.0 / -44.7 | -1327 / -1143 | OK-PRIOR-UNKNOWN-WF | 0.09 | 0.06 |
| qgate | {"feat": "x_rty_pull_opp5", "m": 0, "q": 0.2, "tail": "low"} | P7 | 36.7 | 21.2 / 46.3 / -4.5 / 0.0 | -528 / -1739 | OK-PRIOR-UNKNOWN-WF | 0.04 | 0.03 |
| qgate | {"feat": "x_leadR5", "m": 0, "q": 0.2, "tail": "low"} | ALL | 36.6 | 31.8 / 33.5 / -4.0 / 0.0 | +1605 / -2526 | OK-PRIOR-UNKNOWN-WF | 0.02 | 0.18 |
| qgate | {"feat": "x_lead5", "m": 0, "q": 0.1, "tail": "low"} | ALL | 36.4 | 23.7 / 23.7 / 6.4 / 0.0 | +2784 / -1248 | OK-PRIOR-UNKNOWN-WF | 0.01 | 0.09 |
| qgate | {"feat": "x_es_pull_opp15", "m": 0.5, "q": 0.5, "tail": "high"} | ALL | 36.1 | 25.1 / 25.1 / 40.6 / 0.0 | +836 / -1173 | OK-PRIOR-UNKNOWN-WF | 0.05 | 0.17 |

### EXACT on the live-panel base (reference LPB)
| set | what | cut L6M / PRE / X' / HOLD | d mean L6M / PRE | label |
|--|--|--|--|--|
| LPB_A5_HLIVE | D7 EsLeadSize hook as shipped (2 ticks, with x1.5, against x0.5; UP-labelled reference) | pending (0 months) | | |
| LPB_A5_H1 | A5 ES hook min1 with1.0 against0.5 | n/a / n/a / n/a / n/a | +nan / +nan |  |
| LPB_A5_H0 | A5 ES hook min1 with1.0 against0 | n/a / n/a / n/a / n/a | +nan / +nan |  |
| LPB_A5_R1 | A5 RTY last-1-min against skip (P7, q.2) | n/a / n/a / n/a / n/a | +nan / +nan |  |

Plain sentences are added with the exact rows when they land.
