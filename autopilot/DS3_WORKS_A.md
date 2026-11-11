# DS3_WORKS_A - T-WORKS part A: generalised risk dials (W-A)
Refreshed 2026-11-11 14:26Z. Shadow only, no PASS claims, label PRE-PROOF (post-hoc). Prereg: autopilot/WORKS_A_PREREG.md (sha in DECISIONS.md). Code: outputs/code/th_works_a. Data: /mnt/l2/l2vast/_th_works_a.

## 0. Status
Exact sets with at least one complete window: 2. First-order cells scored: A1 35512, A2 2352, A3 7920 (each on two bases: LPB_BASE and JN04RM trade list; state is always the LPB_BASE shadow base-lot P&L). The harness reproduces LPB_EMPTY and JN04RM trade by trade (identity rows in DECISIONS.md).

## 1. Exact results, wave 1 (JN04RM plus one extra dial; cut = stack maxDD cut vs LPB_BASE, d mean = $/wk vs LPB_BASE; the JN04RM columns are the same set measured against JN04RM itself)
| set | dial | first-order (JN04 base) L6M cut / HOLD cut | placebo p (L6M / HOLD) | exact L6M | exact HOLD |
|--|--|--|--|--|--|
| WA_A1_01 | B:K7 calmar D15 thr0.5 stateless x0.0 | +5.0 / +30.4 | 0.40 / 0.21 | not yet | not yet |
| WA_A1_02 | B:K7 pf D15 thr1.3 firstwin x0.0 | +5.0 / +30.4 | 0.36 / 0.19 | not yet | not yet |
| WA_A1_03 | B:P7 sum D7 thr-3625.555 stateless x0.5 | +3.6 / +11.5 | 0.27 / 0.11 | not yet | not yet |
| WA_A1_04 | B:M7 ddpeak D7 thr6295.69 stateless x0.0 | +5.6 / +16.7 | 0.45 / 0.11 | not yet | not yet |
| WA_A1_05 | B:M7 winrate D5 thr0.3 firstwin x0.0 | +6.3 / +19.7 | 0.47 / 0.05 | not yet | not yet |
| WA_A1_06 | B:H7 calmar D10 thr1.0 stateless x0.5 | +1.3 / +2.6 | 0.48 / 0.54 | not yet | not yet |
| WA_A1_07 | STACK calmar D7 thr0.5 firstwin x0.5 | +18.1 / +27.7 | 0.09 / 0.11 | not yet | not yet |
| WA_A1_08 | STACK pf D15 thr1.3 stateless x0.5 | +15.5 / +18.7 | 0.11 / 0.28 | not yet | not yet |
| WA_A1_09 | STACK>P7 calmar D10 thr1.0 stateless x0.25 | +23.4 / +16.2 | 0.03 / 0.13 | not yet | not yet |
| WA_A1_10 | K7>P7 ddpeak D5 thr9012.105 firstwin x0.75 | +3.6 / +3.0 | 0.12 / 0.05 | not yet | not yet |
| WA_A1_11 | M7>P7 calmar D5 thr0.5 stateless x0.5 | +15.6 / +10.8 | 0.04 / 0.33 | not yet | not yet |
| WA_A1_12 | P7>K7 ddpeak D10 thr14502.218 firstwin x0.0 | +6.3 / +30.4 | 0.21 / 0.08 | not yet | not yet |
| WA_A1_13 | P7>ALLexP7 ddpeak D20 thr21753.327 firstwin x0.0 | +6.3 / +46.3 | 0.49 / 0.06 | not yet | not yet |
| WA_A1_14 | P7>ALLexP7 pf D10 thr0.8 firstwin x0.0 | +6.3 / +46.3 | 0.43 / 0.06 | not yet | not yet |
| WA_A1_15 | BS:P7:nyam pf D5 thr0.8 firstwin x0.0 | +2.3 / +9.0 | 0.44 / 0.27 | not yet | not yet |
| WA_A1_16 | BS:M7:london ddpeak D5 thr3443.199 firstwin x0.5 | +6.1 / +4.9 | 0.24 / 0.37 | not yet | not yet |
| WA_A1_17 | BS:M7:london ddpeak D5 thr3443.199 firstwin x0.25 | +6.1 / +4.9 | 0.24 / 0.37 | not yet | not yet |
| WA_A2_18 | ALL hi thr=1.2,m=0.0 | +20.5 / +45.6 | 0.34 / 0.14 | cut +32.8 / d mean +1579 (vs JN04RM: cut -24.4 / d mean +1417) | not yet |
| WA_A2_19 | ALL hi thr=1.1,m=0.0 | +37.1 / +43.8 | 0.19 / 0.17 | cut +49.1 / d mean -1529 (vs JN04RM: cut +5.8 / d mean -2067) | not yet |
| WA_A2_20 | exP7 hi thr=1.1,m=0.0 | +16.8 / +46.1 | 0.48 / 0.16 | not yet | not yet |
| WA_A2_21 | B:M7 hi thr=1.1,m=0.0 | +10.9 / +31.4 | 0.76 / 0.01 | not yet | not yet |
| WA_A2_22 | B:P7 hi thr=1.2,m=0.0 | +19.4 / +12.2 | 0.19 / 0.34 | not yet | not yet |
| WA_A2_23 | B:M7 hi thr=1.2,m=0.0 | +3.0 / +29.4 | 0.90 / 0.01 | not yet | not yet |
| WA_A2_24 | exP7 hi thr=1.2,m=0.0 | +1.1 / +39.0 | 0.67 / 0.22 | not yet | not yet |
| WA_A2_25 | ALL hi thr=1.2,m=0.25 | +18.0 / +2.5 | 0.13 / 0.86 | not yet | not yet |
| WA_A2_26 | exP7 lo thr=0.9,m=0.0 | +23.9 / +12.3 | 0.05 / 0.49 | not yet | not yet |
| WA_A2_27 | BS:K7:london lo thr=0.9,m=0.0 | +9.1 / +4.4 | 0.03 / 0.27 | not yet | not yet |
