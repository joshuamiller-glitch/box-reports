# DS3_PRODUCTS_JOINT (FD-CORE, 2026-11-10 17:08Z). Post-hoc, Shadow only, no PASS claim. Standing rules 1 / 2 / 2a. STANDALONE bar (D8) and SEAT bar side by side; "fails the seat bar" is never a verdict on the product.

## 0. Data cost line
T-NEXT data top-up bought 2026-11-10 17:25Z: GLBX.MDP3 ohlcv-1m .v.0, YM GC CL ZN ZB 6E 6J MBT NKD to 2026-11-10 08:00Z (historical licence ends 08:59Z same day) and NQ ES RTY from 10-30; quote $1.007 (under the $100 authorisation), logged in SPEND.json: running total $7,328.94 of $8,000. Files data/ext_20261110/*_ohlcv1m_20261110.dbn.zst. Merge into the 1-min series / nol2 bars = CPU work deferred past the 21:30Z pause; until then L1M/L2M in this page end 2026-10-16 (30 for NQ/ES/RTY).

## 1. Bars. STANDALONE (D8): instrument's own dressed stack, equal-$-risk lots R=$1,200 capped (F.LOT_CAP), measured fills of the source screen, own calendar: L6M and L3M Calmar > 0, bi-weekly re-pick WF >= 60% of refit periods beating the naked setting, PRE under rule 2a with the naked own baseline (floor 25% of its own PRE mean; 0 when that mean is <= 0), timing placebo p <= .10 on L6M Calmar, family null p_fam <= .10 over the instrument's own search. SEAT: add / replace on the NQ stack at equal mean, corr <= .30.

## 2. NO-L2 products (FD-NOL2 finalists; first-order, NO-L2 STACK, price-path TH + structural zones)
| instrument | finalists | standalone clears | seat add cut L6M>0 and PRE>0 | corr<=.30 | best standalone (id, L6M Calmar, WF %) |
|--|--|--|--|--|--|
| 6E | 3 | 0 | 2 | 3 | 6E.15.21a4a7f2, 53.3, 15 |
| BTC | 9 | 0 | 4 | 9 | BTC.30.02e1038e, 11.5, 60 |
| CL | 15 | 0 | 6 | 15 | CL.T2FCL.1cff3bf8, 7.8, 66 |
| GC | 138 | 0 | 78 | 138 | GC.T2FGC.065984d2, 40.3, 2 |
| MBT | 20 | 0 | 7 | 20 | MBT.s0.bf528dd8, 17.3, 52 |
| YM | 46 | 0 | 17 | 46 | YM.T2FYM.8999b971, 28.2, 9 |

## 3. Finalists, both bars (top 40 by standalone L6M Calmar)
| id | sess | naked L6M / PRE mean | dressed L6M / L3M mean | L6M / L3M Calmar (dressed vs naked L6M) | maxDD L6M | bi-weekly WF (% beat / n / cut % / mean) | PRE rule 2a | placebo p | family p | STANDALONE | SEAT add cut L6M / PRE (corr) | SEAT replace-weakest inc L6M / PRE | carrier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 6E.15.21a4a7f2 | london | +135 / -133 | +123 / +95 | +53.3 / - (+60.9) | +120 | +15 / +52 / +7.1 / +13 | OK-PRIOR (old OK-PRIOR) | 0.02 | +1.00 | fails: wf_ge60,family_le10 | +0.2 / +0.2 (-0.00) | +0.2 / +0.2 | STK |
| GC.T2FGC.f80ca7a6 | nypm | +526 / +176 | +662 / +451 | +40.3 / - (+8.1) | +855 | +2 / +46 / +0.0 / -5 | OK-PRIOR (old OK-PRIOR) | 0.04 | +1.00 | fails: wf_ge60,family_le10 | +2.3 / +1.7 (0.21) | +2.6 / +1.4 | THP |
| GC.T2FGC.065984d2 | nypm | +526 / +176 | +662 / +451 | +40.3 / - (+8.1) | +855 | +2 / +46 / +0.0 / -5 | OK-PRIOR (old OK-PRIOR) | 0.04 | +1.00 | fails: wf_ge60,family_le10 | +2.3 / +1.7 (0.21) | +2.6 / +1.4 | THP |
| GC.T2FGC.53477fb1 | london | +955 / -418 | +834 / +1103 | +28.4 / +639.4 (+9.3) | +1528 | +42 / +57 / +49.2 / +3 | OK-PRIOR (old OK-PRIOR) | 0.02 | +1.00 | fails: wf_ge60,family_le10 | +0.9 / +1.2 (0.01) | +1.6 / +1.9 | ZON |
| YM.T2FYM.8999b971 | close | +109 / -245 | +219 / +549 | +28.2 / +70.5 (+1.7) | +405 | +9 / +46 / +2.2 / +9 | OK-PRIOR (old OK-PRIOR) | 0.01 | +1.00 | fails: wf_ge60,family_le10 | -0.3 / +0.2 (0.05) | +0.5 / +0.5 | ZON |
| 6E.15.167c0bee | london | +47 / -18 | +43 / +22 | +24.6 / +71.0 (+26.7) | +92 | +15 / +52 / -14.9 / +3 | OK-PRIOR (old OK-PRIOR) | 0.03 | +1.00 | fails: wf_ge60,family_le10 | +0.0 / +0.0 (0.04) | +0.1 / +0.1 | STK |
| GC.vwap_reject.e86771b9 | nypm | +1710 / -191 | +791 / -1 | +23.4 / -0.0 (+10.2) | +1754 | +67 / +72 / +71.4 / -185 | OK-PRIOR (old OK-PRIOR) | 0.02 | +1.00 | fails: l3m_calmar_pos,family_le10 | +1.3 / +0.9 (0.14) | +1.6 / +0.9 | ZON |
| YM.orb_fade.9fdaa654 | nyam | +1124 / -169 | +917 / +461 | +21.6 / +10.9 (+5.5) | +2202 | +61 / +72 / -9.4 / -86 | OK-PRIOR (old OK-PRIOR) | 0.02 | +1.00 | fails: family_le10 | +1.8 / +6.4 (-0.04) | +1.3 / +5.9 | THP |
| GC.donchian.1deefb1e | nyam | +3010 / -220 | +3186 / +1951 | +19.2 / +78.8 (+12.5) | +8645 | +61 / +72 / +50.4 / -244 | OK-PRIOR (old OK-PRIOR) | 0.05 | +1.00 | fails: family_le10 | +8.0 / +4.6 (-0.00) | +7.8 / +4.6 | STK |
| GC.T2FGC.7cbd7d38 | london | +1236 / +125 | +1177 / +2665 | +18.9 / +42.9 (+17.4) | +3234 | +70 / +63 / +19.1 / -249 | OK-PRIOR (old OK-PRIOR) | 0.15 | +1.00 | fails: placebo_le10,family_le10 | +2.8 / +2.7 (-0.02) | +2.6 / +2.5 | THP |
| GC.T2FGC.962b62f3 | nypm | +234 / +137 | +301 / +294 | +18.3 / +60.7 (+3.6) | +855 | +0 / +46 / +0.0 / -67 | OK-PRIOR (old OK-PRIOR) | 0.11 | +1.00 | fails: wf_ge60,placebo_le10,family_le10 | +1.3 / +0.7 (0.23) | +1.5 / +0.2 | THP |
| GC.T2FGC.cdeba74c | nypm | +234 / +137 | +301 / +294 | +18.3 / +60.7 (+3.6) | +855 | +0 / +46 / +0.0 / -67 | OK-PRIOR (old OK-PRIOR) | 0.11 | +1.00 | fails: wf_ge60,placebo_le10,family_le10 | +1.3 / +0.7 (0.23) | +1.5 / +0.2 | THP |
| GC.T2FGC.888590b0 | nypm | +1115 / +80 | +1138 / +1261 | +18.3 / +52.7 (+15.3) | +3239 | +9 / +46 / +0.0 / +5 | OK-PRIOR (old OK-PRIOR) | 0.05 | +1.00 | fails: wf_ge60,family_le10 | +1.3 / -0.4 (0.12) | +2.3 / +0.5 | THL |
| GC.donchian.b1e82932 | nyam | +1716 / -97 | +1147 / +226 | +18.1 / +3.6 (+11.3) | +3299 | +72 / +72 / +62.0 / -19 | OK-PRIOR (old OK-PRIOR) | 0.13 | +1.00 | fails: placebo_le10,family_le10 | +5.6 / +11.3 (0.02) | +4.7 / +10.3 | STK |
| MBT.s0.bf528dd8 | close | +238 / -29 | +226 / +164 | +17.3 / +13.9 (+2.9) | +678 | +52 / +54 / -37.2 / -73 | OK-PRIOR (old OK-PRIOR) | 0.06 | +1.00 | fails: wf_ge60,family_le10 | +0.1 / +0.1 (-0.08) | +0.4 / +0.3 | ZON |
| MBT.mom_h30_pre_q0.85_atr_3.0_None_s0.e66f84fe | pre | +170 / -48 | +332 / +58 | +16.9 / +2.9 (+1.9) | +1021 | +64 / +47 / +44.5 / +43 | OK-PRIOR (old OK-PRIOR) | 0.03 | +1.00 | fails: family_le10 | +0.3 / -0.3 (-0.02) | +0.6 / -0.1 | ZON |
| GC.T2FGC.f4821371 | nypm | +238 / +167 | +337 / +124 | +16.8 / +6.2 (+2.9) | +1040 | +0 / +46 / +0.0 / +0 | RECENT-ONLY (old OK-PRIOR) | 0.08 | +1.00 | fails: wf_ge60,prior_ok,family_le10 | +0.8 / +0.8 (0.17) | +1.0 / +1.0 | THP |
| GC.T2FGC.fc571d57 | nypm | +238 / +167 | +337 / +124 | +16.8 / +6.2 (+2.9) | +1040 | +0 / +46 / +0.0 / +0 | RECENT-ONLY (old OK-PRIOR) | 0.08 | +1.00 | fails: wf_ge60,prior_ok,family_le10 | +0.8 / +0.8 (0.17) | +1.0 / +1.0 | THP |
| GC.T2FGC.56c1e879 | nyam | +643 / -106 | +463 / +126 | +16.1 / - (+7.2) | +1490 | +52 / +63 / +73.1 / +84 | OK-PRIOR (old OK-PRIOR) | 0.05 | +1.00 | fails: wf_ge60,family_le10 | +0.7 / +0.5 (0.09) | +1.2 / +1.0 | STK |
| YM.orb_fade.76862175 | nyam | +1111 / -204 | +895 / +669 | +15.6 / +11.7 (+5.4) | +2979 | +60 / +72 / +12.4 / -70 | OK-PRIOR (old OK-PRIOR) | 0.04 | +1.00 | fails: wf_ge60,family_le10 | +1.3 / +4.7 (-0.07) | +0.9 / +4.3 | THP |
| YM.T2FYM.6aa7ce71 | close | +109 / -206 | +233 / +582 | +15.0 / +37.4 (+1.7) | +809 | +7 / +46 / +2.8 / +10 | OK-PRIOR (old OK-PRIOR) | 0.02 | +1.00 | fails: wf_ge60,family_le10 | -0.9 / +0.1 (0.09) | +0.7 / +0.7 | STK |
| MBT.s2.469fdc02 | close | +392 / +46 | +283 / +181 | +14.1 / - (+10.0) | +1046 | +37 / +51 / -47.3 / -160 | OK-PRIOR (old OK-PRIOR) | 0.13 | +1.00 | fails: wf_ge60,placebo_le10,family_le10 | +0.5 / +0.2 (0.04) | +0.8 / +0.4 | STK |
| GC.T2FGC.398a806e | nypm | +712 / -34 | +538 / +545 | +14.0 / +17.5 (+7.6) | +1998 | +51 / +67 / +48.9 / +9 | OK-PRIOR (old OK-PRIOR) | 0.06 | +1.00 | fails: wf_ge60,family_le10 | +1.7 / +1.8 (0.12) | +0.8 / +0.9 | STK |
| GC.T2FGC.fea033f9 | nypm | +712 / -34 | +538 / +545 | +14.0 / +17.5 (+7.6) | +1998 | +51 / +67 / +48.9 / +9 | OK-PRIOR (old OK-PRIOR) | 0.06 | +1.00 | fails: wf_ge60,family_le10 | +1.7 / +1.8 (0.12) | +0.8 / +0.9 | STK |
| MBT.s2.be457e72 | close | +380 / +29 | +268 / +181 | +13.3 / - (+9.7) | +1046 | +37 / +51 / -18.8 / -134 | OK-PRIOR (old OK-PRIOR) | 0.14 | +1.00 | fails: wf_ge60,placebo_le10,family_le10 | +0.5 / +0.2 (0.07) | +0.8 / +0.4 | STK |
| MBT.donchian.e7096026 | pre | +389 / -47 | +335 / +74 | +13.2 / +20.2 (+6.8) | +1325 | +68 / +72 / +64.3 / +129 | OK-PRIOR (old OK-PRIOR) | 0.04 | +1.00 | fails: family_le10 | +1.0 / +0.7 (-0.13) | +1.3 / +1.1 | STK |
| GC.T2FGC.69ed20b1 | london | +240 / -316 | +300 / +523 | +12.8 / - (+2.5) | +1215 | +32 / +57 / +31.3 / -50 | OK-PRIOR (old OK-PRIOR) | 0.07 | +1.00 | fails: wf_ge60,family_le10 | +0.7 / +2.1 (-0.04) | +1.0 / +2.4 | ZON |
| GC.donchian.575ad97f | nyam | +1344 / -34 | +1268 / +253 | +12.2 / +2.4 (+9.8) | +5408 | +57 / +72 / +32.7 / -197 | OK-PRIOR (old OK-PRIOR) | 0.11 | +1.00 | fails: wf_ge60,placebo_le10,family_le10 | +1.4 / +0.5 (0.12) | +3.9 / +0.9 | ZON |
| BTC.30.02e1038e | close | +1107 / -483 | +763 / -146 | +11.5 / -2.9 (+7.4) | +3440 | +60 / +72 / +54.7 / +136 | OK-PRIOR (old OK-PRIOR) | 0.08 | +1.00 | fails: l3m_calmar_pos,wf_ge60,family_le10 | +0.6 / +1.6 (0.09) | +0.7 / +1.7 | ZON |
| GC.donchian.67cdc99d | nyam | +176 / -151 | +1945 / +1231 | +11.5 / +8.6 (+0.5) | +8791 | +62 / +72 / -81.3 / -774 | OK-PRIOR (old OK-PRIOR) | 0.08 | +1.00 | fails: family_le10 | +3.1 / +4.3 (0.04) | +3.2 / +4.4 | STK |
| GC.T2FGC.d1f37823 | nypm | +573 / +123 | +521 / +877 | +11.5 / +25.4 (+7.8) | +2354 | +4 / +46 / +0.0 / +3 | OK-PRIOR (old OK-PRIOR) | 0.11 | +1.00 | fails: wf_ge60,placebo_le10,family_le10 | +0.6 / -1.2 (0.07) | +0.8 / -1.0 | SIZ |
| YM.T2FYM.eebd60c1 | close | +261 / -264 | +562 / -405 | +10.9 / -7.9 (+3.7) | +2676 | +59 / +71 / +51.9 / -109 | OK-PRIOR (old OK-PRIOR) | 0.08 | +1.00 | fails: l3m_calmar_pos,wf_ge60,family_le10 | +1.7 / +1.3 (0.04) | +2.2 / +1.5 | SIZ |
| BTC.60.fab5dd4f | close | +1163 / -68 | +727 / +59 | +10.8 / +1.4 (+51.9) | +3496 | +50 / +72 / -19.9 / -405 | OK-PRIOR (old OK-PRIOR) | 0.11 | +1.00 | fails: wf_ge60,placebo_le10,family_le10 | -0.1 / +1.1 (-0.00) | +0.8 / +1.2 | SIZ |
| MBT.mom_h60_pre_q0.7_atr_3.0_None_s1.9e80489f | pre | +201 / +28 | +200 / +87 | +10.1 / +5.8 (+2.2) | +1024 | +56 / +48 / +32.2 / +17 | OK-PRIOR (old OK-PRIOR) | 0.07 | +1.00 | fails: wf_ge60,family_le10 | +0.8 / +1.1 (0.06) | +0.7 / +1.2 | SIZ |
| GC.T2FGC.3f595fd7 | asia | +1259 / -204 | +750 / +85 | +10.1 / +1.1 (+10.1) | +3864 | +58 / +71 / +24.2 / -162 | OK-PRIOR (old OK-PRIOR) | 0.04 | +1.00 | fails: wf_ge60,family_le10 | +2.2 / +1.7 (-0.04) | +2.0 / +1.6 | SIZ |
| GC.T2FGC.064413f5 | asia | +189 / +6 | +43 / +0 | +10.0 / +0.0 (+8.1) | +225 | +0 / +36 / +0.0 / +0 | OK-PRIOR (old OK-PRIOR) | 0.09 | +1.00 | fails: l3m_calmar_pos,wf_ge60,family_le10 | -0.0 / -0.2 (0.15) | +0.2 / -0.0 | THL |
| GC.T2FGC.d0fd1884 | nypm | +94 / +27 | +436 / +344 | +9.8 / +7.8 (+1.0) | +2305 | +46 / +57 / +34.8 / +303 | OK-PRIOR (old OK-PRIOR) | 0.22 | +1.00 | fails: wf_ge60,placebo_le10,family_le10 | +1.2 / +1.0 (0.00) | +1.1 / +0.7 | THP |
| GC.T2FGC.23e6c972 | nypm | +94 / -39 | +436 / +344 | +9.8 / +7.8 (+0.8) | +2305 | +44 / +57 / +24.8 / +280 | OK-PRIOR (old OK-PRIOR) | 0.21 | +0.95 | fails: wf_ge60,placebo_le10,family_le10 | +1.2 / +1.0 (0.01) | +1.1 / +0.7 | THP |
| GC.T2FGC.feb85183 | nyam | +872 / -82 | +552 / +61 | +9.8 / +2.2 (+9.8) | +2934 | +52 / +63 / +65.2 / +104 | OK-PRIOR (old OK-PRIOR) | 0.14 | +1.00 | fails: wf_ge60,placebo_le10,family_le10 | +0.5 / +0.4 (0.01) | +1.2 / +1.1 | STK |
| YM.T2FYM.310e61c1 | nyam | +1015 / -302 | +542 / -117 | +9.1 / -5.0 (+13.7) | +3102 | +61 / +71 / +42.2 / -98 | OK-PRIOR (old OK-PRIOR) | 0.14 | +1.00 | fails: l3m_calmar_pos,placebo_le10,family_le10 | -0.4 / +1.2 (-0.05) | +1.6 / +1.7 | SIZ |

## 4. ES / RTY with L2 (FD-LIQ): see DS3_PRODUCTS_JOINT_ES.md and DS3_PRODUCTS_JOINT_RTY.md; zone-as-entry books (ZN-BOOK): DS3_PRODUCTS_ZONEBOOKS.md (ES/RTY naked: best pooled t 2.74 / 1.84 vs grid null, family p 1.0, bi-weekly WF 44% / 47%; no-L2 structural-zone versions not started - inputs: code/fd_nol2/feats.py InstFeats.fam on nol2/bars/*.npz).

## 5. One-line verdict per instrument
Written from section 2 when the standalone-clearing count is available for the instrument (ES/RTY from FD-LIQ's pages). Format: "<instr>: the book that works is X in session Y; standalone Calmar Z, WF W %; seat: corr c, yes/no; standalone: yes/no."

Not yet done: A4 discovery with the stack ON (random/Bayesian joint search over signal family x params x every layer) for the no-L2 products; A5 cross-instrument NQ features; D8 for ES/RTY finalists awaits FD-LIQ bw_* in its ledger; exact engine for ES/RTY awaits SZ-CORE's base.