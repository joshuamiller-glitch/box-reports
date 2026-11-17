# DS3_MAJOR_C_RISK - stack-level risk overlay on JL3 (W-MC, MAJOR programme part C, order 11-17 14:00Z)
FIVE-LINE SUMMARY (FIRST PASS 2026-11-17 14:01Z, data ends 2026-10-31):
1. TRIED: 62 single-policy cells + 3 joint overlays (65) on JL3 (trailing-drawdown and N-day-P&L size cut/press, volatility target, per-session loss stop, same-side cap beyond London) by path arithmetic with random-scale / random-halt controls matched on lots removed, then 12 exact-engine finalists (picked on 2023-04..2025-10 only) plus 3 joint cells with persistent engine controls queued only where a cell looks alive; DAY-DONE settings are W-DD's (pointer below).
2. HOLDS: so far nothing beats uniform trimming of lots: 0 of 65 screen cells reach LEAD/CONFIRMED (screen tiers use arithmetic controls); the best cell that keeps >= 95% of the mean cuts pooled ulcer by only -2.4% (SS_noAsia_T4000). Engine status: identity PASSED on 202610 and 202504, 0 of 12 finalists fully landed, 0 engine control draws landed.
3. DOES NOT: 2 of 65 screen cells give less ulcer per dollar than a uniform lot trim in L6M, HOLD and pooled at once (ND_press_N5_k1.5, SS_noAsia_T4000); median pooled ulcer-per-dollar excess over a uniform trim by family (percent; positive = worse than just trimming): DD +19; NDcut +10; NDpress +7; VT +7; SS +10; CAP +18; JOINT +24. Pressing after strong days (ND_press) earns more only by adding lots (its mean RC p is leverage, not skill). Rolling trailing-12-month pick on the screen (from 2024-04): pooled ulcer +9.7% / mean -9.2% vs JL3; frozen FIT pick VT_N10_q50_hi1.0.
4. NEEDS IN DS7: nothing is proposed. Any size scaling would need lots below the base unit (one base lot = 1.75 live lots; most JL3 orders are 1 base lot = 2 live lots, so a x0.5 cut can only be 2 -> 1 live lot) and a stack-level equity series in the live code; the existing day lock and London cap stay as they are.
5. NEXT: engine cells for the 12 finalists run L6M+HOLD first, then 2023-04..2025-10; controls are queued automatically for a family when its exact cell passes the gate (ulcer < JL3 and ulcer-per-dollar < 1 in L6M or HOLD); the page refreshes unattended every 30 minutes (loop pid _major_c/loop.pid).
VERDICT (FIRST PASS 2026-11-17 14:01Z; data ends 2026-10-31): 0 of 65 screen cells reach LEAD or CONFIRMED on arithmetic controls; exact-engine tiers: see section 2; every engine cell without 30 valid persistent controls is NOT FINISHED, never passing.

> VALIDATION (desk standard, W-MC, FIRST PASS 2026-11-17 14:01Z): trials counted = 65 screen cells (62 single + 3 joint) + 15 engine cells (12 picked on FIT, 3 joint by PREREG_MC_ADD2) + engine controls (families: none yet); correction = White RC / SPA on weekly mean change and a 4-week-block RC on ulcer over the 65 screen cells vs JL3 (pooled): mean RC p 0.00, SPA p 0.01, ulcer RC p 0.49 (best by mean ND_press_N20_k0.5 +2703 $/wk base; best by ulcer J2, 7780 ulcer-$ better than JL3 of 19183); PBO (CSCV, 65 cells + JL3) S=8/12/16: 8 0.59, 12 0.55, 16 0.52; in-sample = screen on 2023-04..2025-10 (finalist pick), walk-forward = frozen FIT pick and rolling trailing-12-month pick (PREREG_MC_ADD1), untouched = HOLD 2025-11..2026-04 and L6M 2026-05..2026-10 (finalists were picked without them; the screen output of all windows was read once before the prereg file was written, disclosed in PREREG_MC.md). Prereg sha lines in DECISIONS.md; hypothesis MC-H1; trial row MC in TRIALS_LEDGER.csv. All numbers are PATH ARITHMETIC (screen) or EXACT ENGINE (labelled).

Judging: ulcer index (RMS daily drawdown of cumulative P&L) is primary; "ulc" below = change vs JL3 in percent (negative = lower ulcer = better); "mean" = change in mean $/week; "eff" = (ulcer ratio)/(mean ratio) - 1 (negative = less ulcer per dollar than a uniform lot trim; a uniform trim has eff 0). Base lots, $1.18 RT unless a column says otherwise.

## 0. Identity and engine status
- Hook: code/th_mc/mc_hooks.py (outermost hook, overrides only sess_lots_at / ntz_check / try_entry, always calls super; scale / session-stop / same-side-cap). Identity cell TL3_MC_ID = all three rules active and inert.
  - TL3_MC_ID 202610: 691 trades net 37159.82 vs JL3 691 net 37159.82 -> IDENTICAL
  - TL3_MC_ID 202504: 637 trades net 41239.76 vs JL3 637 net 41239.76 -> IDENTICAL
- Engine finalists, months landed (of 43): DD_W250_T10000 0; DD_W60_T10000 0; ND_cut_N5_k1.0 0; ND_cut_N10_k0.5 0; ND_press_N5_k1.5 0; ND_press_N20_k1.0 0; VT_N10_q50_hi1.0 0; VT_N10_q75_hi1.0 0; SS_noAsia_T4000 0; SS_noAsia_T9000 0; CAP_nonlon_8 0; CAP_asia_8 0; J1 0; J2 0; J3 0
- Engine controls (30 valid draws needed per family top cell): none queued yet (gate not passed by any exact cell)
- Gate for queueing controls: DD_W250_T10000: not landed; DD_W60_T10000: not landed; ND_cut_N5_k1.0: not landed; ND_cut_N10_k0.5: not landed; ND_press_N5_k1.5: not landed; ND_press_N20_k1.0: not landed; VT_N10_q50_hi1.0: not landed; VT_N10_q75_hi1.0: not landed; SS_noAsia_T4000: not landed; SS_noAsia_T9000: not landed; CAP_nonlon_8: not landed; CAP_asia_8: not landed; J1: not landed; J2: not landed; J3: not landed
- Fidelity note: the engine works in BASE lots (1 base lot = 1.75 live lots). A x0.5 cut of a 1-base-lot order has no base-lot representation, so the exact cells use unbiased dithered rounding by (day, session, book) (floor(lots x m + u), u from a hash): expected lots equal the arithmetic, realised lots do not. The screen rounds at LIVE-lot level instead (2 live lots -> 1). Section 4 compares engine to screen.

## 1. Screen (path arithmetic on the JL3 trade list, live-lot rounding, own-path state): all 65 cells vs JL3
Percentiles pu / pm = share of the arithmetic controls (random scale / random halts matched on lots removed, up to 60 valid draws) the cell beats on ulcer / on mean in the window. FIT = 2023-04..2025-10 (selection window); L6M and HOLD untouched by the selection.

| cell | lots removed | FIT ulc / mean | L6M ulc / mean (eff) | pu / pm L6M | HOLD ulc / mean (eff) | pu / pm HOLD | pooled ulc / mean (eff) | controls | screen tier |
|--|--|--|--|--|--|--|--|--|--|
| DD_W60_T10000 | 31.6% | -25.4% / -40.0% | -6.9% / -21.7% (+18.9) | 0.00 / 0.92 | -25.9% / -32.1% (+9.3) | 0.55 / 0.57 | -25.0% / -32.2% (+10.7) | 60 | FAIL |
| DD_W60_T20000 | 24.1% | -4.7% / -31.5% | +2.9% / -10.6% (+15.1) | 0.02 / 1.00 | -16.1% / -20.7% (+5.8) | 0.47 / 0.67 | -6.5% / -22.3% (+20.4) | 60 | FAIL |
| DD_W60_T30000 | 18.0% | -1.2% / -21.0% | +3.6% / -2.9% (+6.7) | 0.00 / 1.00 | -1.1% / -27.0% (+35.5) | 0.22 / 0.17 | -1.0% / -15.7% (+17.4) | 60 | FAIL |
| DD_W60_T45000 | 10.6% | +10.3% / -14.9% | +0.0% / +0.0% (+0.0) | 0.10 / 0.98 | +6.7% / -26.0% (+44.3) | 0.12 / 0.05 | +9.4% / -11.5% (+23.7) | 60 | FAIL |
| DD_W250_T10000 | 32.1% | -28.1% / -38.0% | -6.9% / -21.7% (+18.9) | 0.00 / 0.92 | -25.9% / -32.1% (+9.3) | 0.48 / 0.57 | -27.1% / -31.2% (+6.1) | 60 | FAIL |
| DD_W250_T20000 | 26.1% | -7.4% / -31.9% | +2.9% / -10.6% (+15.1) | 0.00 / 0.98 | -16.1% / -20.7% (+5.8) | 0.40 / 0.80 | -8.6% / -22.5% (+17.9) | 60 | FAIL |
| DD_W250_T30000 | 23.2% | +3.2% / -31.3% | +3.6% / -2.9% (+6.7) | 0.00 / 1.00 | -1.1% / -27.0% (+35.5) | 0.15 / 0.38 | +2.5% / -20.6% (+29.0) | 60 | FAIL |
| DD_W250_T45000 | 13.8% | +12.3% / -21.5% | +0.0% / +0.0% (+0.0) | 0.07 / 1.00 | +6.7% / -26.0% (+44.3) | 0.12 / 0.08 | +11.1% / -14.7% (+30.3) | 60 | FAIL |
| ND_cut_N5_k0.5 | 9.9% | +16.1% / -20.6% | -2.8% / -6.0% (+3.4) | 0.27 / 0.82 | +7.1% / -17.9% (+30.4) | 0.10 / 0.17 | +14.2% / -15.0% (+34.3) | 60 | FAIL |
| ND_press_N5_k0.5 | -23.9% | +43.8% / +6.5% | +29.3% / +25.7% (+2.8) | 0.45 / 0.52 | +29.4% / +37.2% (-5.7) | 0.40 / 0.82 | +41.0% / +18.6% (+18.9) | 60 | FAIL |
| ND_cut_N5_k1.0 | 3.7% | -0.3% / -4.5% | +1.2% / -2.4% (+3.7) | 0.13 / 0.77 | +7.6% / -9.8% (+19.3) | 0.07 / 0.12 | +1.2% / -4.6% (+6.2) | 60 | FAIL |
| ND_press_N5_k1.0 | -14.1% | +25.2% / +0.9% | +24.7% / +18.3% (+5.4) | 0.18 / 0.65 | +14.3% / +17.6% (-2.8) | 0.55 / 0.77 | +23.3% / +9.9% (+12.2) | 60 | FAIL |
| ND_cut_N5_k1.5 | 1.3% | -3.7% / +0.2% | +0.0% / +0.0% (+0.0) | 0.34 / 0.78 | +20.9% / -10.6% (+35.2) | 0.00 / 0.05 | +1.2% / -1.7% (+3.0) | 60 | FAIL |
| ND_press_N5_k1.5 | -8.0% | +6.8% / +0.5% | +6.6% / +17.3% (-9.2) | 0.63 / 0.98 | +2.7% / +9.8% (-6.4) | 0.72 / 0.63 | +6.1% / +8.0% (-1.8) | 60 | FAIL |
| ND_cut_N10_k0.5 | 7.2% | -0.5% / -10.4% | +3.6% / -2.9% (+6.7) | 0.03 / 0.87 | +7.0% / -13.6% (+23.9) | 0.12 / 0.13 | +0.9% / -8.3% (+10.1) | 60 | FAIL |
| ND_press_N10_k0.5 | -27.4% | +29.1% / +9.1% | +33.5% / +46.5% (-8.8) | 0.35 / 1.00 | +32.2% / +43.8% (-8.0) | 0.42 / 0.87 | +29.8% / +28.2% (+1.2) | 60 | FAIL |
| ND_cut_N10_k1.0 | 2.1% | +0.3% / -2.8% | +0.0% / +0.0% (+0.0) | 0.28 / 0.87 | -6.8% / -4.7% (-2.1) | 0.87 / 0.13 | -0.9% / -2.1% (+1.2) | 60 | FAIL |
| ND_press_N10_k1.0 | -17.3% | +19.0% / +2.4% | +29.1% / +18.3% (+9.1) | 0.13 / 0.42 | +30.7% / +36.0% (-3.8) | 0.23 / 0.97 | +21.5% / +13.8% (+6.8) | 60 | FAIL |
| ND_cut_N10_k1.5 | 0.9% | +9.4% / -3.1% | +0.0% / +0.0% (+0.0) | 0.32 / 0.71 | +4.6% / -2.7% (+7.5) | 0.03 / 0.17 | +8.3% / -1.9% (+10.5) | 60 | FAIL |
| ND_press_N10_k1.5 | -8.4% | +8.4% / -1.7% | +15.0% / +5.7% (+8.8) | 0.18 / 0.17 | +16.5% / +9.7% (+6.3) | 0.33 / 0.63 | +10.1% / +2.9% (+7.0) | 60 | FAIL |
| ND_cut_N20_k0.5 | 5.8% | +6.3% / -8.1% | +0.0% / +0.0% (+0.0) | 0.20 / 0.95 | +12.4% / -14.2% (+30.9) | 0.07 / 0.12 | +7.3% / -6.3% (+14.5) | 60 | FAIL |
| ND_press_N20_k0.5 | -29.9% | +38.1% / +24.6% | +50.7% / +47.6% (+2.1) | 0.00 / 0.98 | +62.3% / +31.3% (+23.6) | 0.07 / 0.53 | +43.0% / +33.8% (+6.9) | 60 | FAIL |
| ND_cut_N20_k1.0 | 2.7% | +18.6% / -8.7% | +0.0% / +0.0% (+0.0) | 0.28 / 0.85 | +7.1% / -5.9% (+13.8) | 0.05 / 0.17 | +16.2% / -5.1% (+22.5) | 60 | FAIL |
| ND_press_N20_k1.0 | -22.8% | +23.5% / +15.1% | +49.4% / +43.5% (+4.1) | 0.00 / 1.00 | +56.0% / +24.5% (+25.3) | 0.03 / 0.55 | +30.6% / +26.7% (+3.0) | 60 | FAIL |
| ND_cut_N20_k1.5 | 0.6% | +1.6% / -0.7% | +0.0% / +0.0% (+0.0) | 0.34 / 0.66 | +12.3% / -5.0% (+18.2) | 0.00 / 0.08 | +3.6% / -1.2% (+4.8) | 60 | FAIL |
| ND_press_N20_k1.5 | -14.6% | +13.6% / -0.5% | +42.8% / +24.4% (+14.9) | 0.00 / 0.92 | +38.5% / +11.2% (+24.6) | 0.08 / 0.40 | +19.2% / +10.3% (+8.1) | 60 | FAIL |
| VT_N10_q50_hi1.0 | 9.9% | -10.9% / -9.7% | -3.0% / -16.8% (+16.6) | 0.27 / 0.05 | +4.2% / -29.1% (+47.0) | 0.18 / 0.02 | -7.8% / -15.6% (+9.2) | 60 | FAIL |
| VT_N10_q50_hi1.5 | 7.0% | -3.4% / -3.1% | -2.1% / -12.3% (+11.6) | 0.33 / 0.12 | +27.5% / -34.1% (+93.3) | 0.00 / 0.00 | +2.9% / -11.7% (+16.5) | 60 | FAIL |
| VT_N10_q75_hi1.0 | 4.3% | -3.2% / -2.5% | -1.6% / -7.7% (+6.6) | 0.48 / 0.13 | +6.9% / -14.7% (+25.4) | 0.08 / 0.03 | -1.3% / -6.5% (+5.5) | 60 | FAIL |
| VT_N10_q75_hi1.5 | -3.1% | +8.0% / +3.1% | +17.6% / -4.0% (+22.4) | 0.00 / 0.00 | +35.0% / -24.3% (+78.3) | 0.00 / 0.00 | +13.6% / -4.1% (+18.4) | 60 | FAIL |
| VT_N20_q50_hi1.0 | 6.2% | -2.8% / -5.0% | -4.3% / -16.2% (+14.2) | 0.50 / 0.00 | -5.0% / -4.2% (-0.9) | 0.55 / 0.63 | -3.2% / -8.8% (+6.1) | 60 | FAIL |
| VT_N20_q50_hi1.5 | 3.6% | +0.1% / -1.0% | -5.4% / -15.0% (+11.3) | 0.82 / 0.00 | +2.6% / -10.0% (+14.0) | 0.18 / 0.12 | +0.5% / -7.5% (+8.6) | 60 | FAIL |
| VT_N20_q75_hi1.0 | 2.0% | +0.8% / -3.4% | -1.7% / -8.2% (+7.2) | 0.62 / 0.00 | -2.6% / -0.5% (-2.2) | 0.67 / 0.62 | +0.2% / -4.6% (+5.0) | 60 | FAIL |
| VT_N20_q75_hi1.5 | -3.4% | +7.3% / +3.7% | +2.0% / -7.4% (+10.2) | 0.57 / 0.00 | +6.3% / -0.6% (+6.9) | 0.45 / 0.33 | +7.0% / -1.0% (+8.0) | 60 | FAIL |
| VT_N40_q50_hi1.0 | 3.9% | -2.1% / -3.0% | -7.1% / -12.8% (+6.5) | 0.85 / 0.02 | -4.4% / -2.8% (-1.6) | 0.57 / 0.50 | -2.6% / -6.4% (+4.1) | 60 | FAIL |
| VT_N40_q50_hi1.5 | 2.3% | +2.5% / -1.7% | -6.4% / -12.8% (+7.2) | 0.90 / 0.00 | -7.1% / -4.0% (-3.2) | 0.85 / 0.17 | +0.7% / -6.0% (+7.1) | 60 | FAIL |
| VT_N40_q75_hi1.0 | 1.8% | -2.4% / +0.7% | -2.7% / -7.5% (+5.1) | 0.78 / 0.00 | -1.0% / -2.2% (+1.2) | 0.48 / 0.30 | -2.1% / -2.7% (+0.5) | 60 | FAIL |
| VT_N40_q75_hi1.5 | -1.3% | +3.3% / +4.7% | -2.4% / -7.4% (+5.4) | 1.00 / 0.00 | +0.6% / -2.7% (+3.4) | 0.47 / 0.12 | +2.7% / -0.8% (+3.5) | 60 | FAIL |
| SS_all_T2500 | 17.2% | +43.6% / -24.1% | +62.8% / -49.3% (+220.8) | 0.07 / 0.00 | -28.6% / -18.2% (-12.7) | 0.60 / 0.32 | +33.9% / -32.0% (+96.8) | 60 | FAIL |
| SS_noAsia_T2500 | 6.9% | +2.7% / -4.7% | -0.5% / -4.6% (+4.3) | 0.48 / 0.15 | -9.3% / +7.1% (-15.3) | 0.53 / 0.87 | +0.5% / -2.6% (+3.3) | 60 | FAIL |
| SS_all_T4000 | 9.6% | +28.9% / -16.3% | +37.1% / -30.3% (+96.7) | 0.07 / 0.00 | +1.5% / -21.6% (+29.5) | 0.17 / 0.12 | +24.5% / -22.1% (+60.0) | 60 | FAIL |
| SS_noAsia_T4000 | 2.8% | -1.7% / -6.0% | +1.5% / +3.2% (-1.7) | 0.30 / 0.80 | -6.0% / +2.3% (-8.1) | 0.65 / 0.68 | -2.4% / -1.3% (-1.1) | 60 | FAIL |
| SS_all_T6000 | 4.5% | +25.7% / -14.2% | +41.9% / -23.5% (+85.4) | 0.03 / 0.00 | +2.3% / -10.7% (+14.6) | 0.23 / 0.22 | +22.2% / -16.9% (+46.9) | 60 | FAIL |
| SS_noAsia_T6000 | 1.0% | +1.9% / -1.2% | +4.0% / +3.8% (+0.2) | 0.07 / 0.97 | -3.4% / +0.8% (-4.2) | 0.67 / 0.55 | +1.0% / +0.9% (+0.1) | 60 | FAIL |
| SS_all_T9000 | 1.0% | +2.4% / -2.2% | +60.5% / -10.7% (+79.8) | 0.00 / 0.00 | +24.1% / -16.4% (+48.4) | 0.00 / 0.00 | +8.0% / -7.7% (+17.0) | 60 | FAIL |
| SS_noAsia_T9000 | 0.1% | -0.4% / -0.9% | -0.4% / +0.8% (-1.2) | 0.93 / 0.97 | +0.0% / +0.0% (+0.0) | 0.35 / 0.46 | -0.3% / -0.2% (-0.1) | 60 | FAIL |
| CAP_asia_3 | 17.9% | -3.2% / -53.1% | -3.5% / -37.4% (+54.1) | 0.10 / 0.02 | -4.0% / -28.0% (+33.4) | 0.28 / 0.37 | -3.4% / -43.3% (+70.3) | 60 | FAIL |
| CAP_ny_3 | 0.7% | -0.3% / -2.7% | +0.3% / -0.1% (+0.4) | 0.27 / 0.63 | +0.4% / -3.3% (+3.8) | 0.28 / 0.03 | -0.1% / -1.9% (+1.8) | 60 | FAIL |
| CAP_nonlon_3 | 18.5% | -2.2% / -56.0% | -3.0% / -37.5% (+55.1) | 0.25 / 0.02 | -5.2% / -30.9% (+37.1) | 0.30 / 0.10 | -2.8% / -45.1% (+77.3) | 60 | FAIL |
| CAP_asia_4 | 12.5% | -6.5% / -43.0% | -4.2% / -25.1% (+28.0) | 0.23 / 0.13 | +1.9% / -22.1% (+30.7) | 0.27 / 0.27 | -4.9% / -33.1% (+42.2) | 60 | FAIL |
| CAP_ny_4 | 0.3% | -2.0% / -1.1% | +0.0% / +0.2% (-0.2) | 0.49 / 0.82 | -0.4% / -1.1% (+0.6) | 0.60 / 0.17 | -1.7% / -0.6% (-1.0) | 60 | FAIL |
| CAP_nonlon_4 | 12.7% | -7.1% / -44.0% | -4.2% / -25.0% (+27.7) | 0.45 / 0.02 | +1.5% / -23.1% (+32.1) | 0.23 / 0.12 | -5.5% / -33.7% (+42.6) | 60 | FAIL |
| CAP_asia_6 | 5.7% | -8.6% / -22.8% | -7.5% / -10.0% (+2.7) | 0.63 / 0.38 | +19.4% / -18.9% (+47.1) | 0.02 / 0.07 | -2.9% / -17.6% (+17.9) | 60 | FAIL |
| CAP_ny_6 | 0.1% | -0.4% / -0.3% | +0.0% / +0.0% (+0.0) | 0.47 / 0.57 | +0.0% / +0.0% (+0.0) | 0.53 / 0.52 | -0.3% / -0.1% (-0.2) | 60 | FAIL |
| CAP_nonlon_6 | 5.7% | -8.5% / -23.4% | -7.5% / -10.0% (+2.7) | 0.87 / 0.30 | +19.4% / -18.9% (+47.1) | 0.00 / 0.08 | -2.8% / -17.9% (+18.3) | 60 | FAIL |
| CAP_asia_8 | 2.4% | -6.4% / -11.0% | -0.7% / -4.6% (+4.1) | 0.33 / 0.28 | +15.0% / -11.1% (+29.4) | 0.00 / 0.05 | -2.1% / -8.8% (+7.4) | 60 | FAIL |
| CAP_ny_8 | 0.0% | -0.5% / -0.1% | +0.0% / +0.0% (+0.0) | 0.49 / 0.55 | +0.0% / +0.0% (+0.0) | 0.57 / 0.55 | -0.4% / -0.0% (-0.3) | 60 | FAIL |
| CAP_nonlon_8 | 2.4% | -6.7% / -11.3% | -0.7% / -4.6% (+4.1) | 0.43 / 0.28 | +15.0% / -11.1% (+29.4) | 0.00 / 0.12 | -2.3% / -8.9% (+7.3) | 60 | FAIL |
| CAPskip_nonlon_4 | 17.0% | -12.6% / -47.4% | +16.2% / -37.2% (+85.0) | 0.03 / 0.00 | -3.0% / -30.7% (+39.9) | 0.22 / 0.08 | -10.1% / -40.9% (+52.1) | 60 | FAIL |
| CAPskip_nonlon_6 | 8.7% | -6.0% / -27.8% | -13.6% / -10.1% (-4.0) | 1.00 / 0.60 | +10.5% / -15.9% (+31.5) | 0.10 / 0.28 | -2.9% / -19.5% (+20.6) | 60 | FAIL |
| J1 | 14.5% | -18.0% / -26.1% | -4.3% / -17.3% (+15.8) | 0.17 / 0.35 | +3.7% / -38.5% (+68.6) | 0.13 / 0.00 | -13.3% / -25.1% (+15.8) | 60 | FAIL |
| J2 | 41.1% | -35.8% / -58.7% | -15.5% / -33.8% (+27.6) | 0.00 / 0.90 | -35.6% / -44.9% (+16.8) | 0.42 / 0.35 | -35.2% / -47.6% (+23.6) | 60 | FAIL |
| J3 | 13.3% | -4.7% / -15.3% | -1.6% / -19.2% (+21.8) | 0.13 / 0.17 | +16.1% / -37.8% (+86.5) | 0.02 / 0.00 | -0.5% / -20.6% (+25.2) | 60 | FAIL |

Finalists (rule frozen on FIT only): DD: DD_W250_T10000 (FIT eff 1.159), DD_W60_T10000 (FIT eff 1.244); NDcut: ND_cut_N5_k1.0 (FIT eff 1.044), ND_cut_N10_k0.5 (FIT eff 1.110); NDpress: ND_press_N5_k1.5 [not eligible: reference] (FIT eff 1.062), ND_press_N20_k1.0 [not eligible: reference] (FIT eff 1.073); VT: VT_N10_q50_hi1.0 (FIT eff 0.988), VT_N10_q75_hi1.0 (FIT eff 0.993); SS: SS_noAsia_T4000 (FIT eff 1.046), SS_noAsia_T9000 [not eligible: reference] (FIT eff 1.006); CAP: CAP_nonlon_8 (FIT eff 1.052), CAP_asia_8 (FIT eff 1.052)

## 2. Exact engine: the 12 finalists and 3 joint cells vs JL3 (windows fully landed only; engine base lots)
Columns: base lots $1.18 RT | $4.84 RT | x1.75 live lots. ulc / mean change vs JL3. P(ulcer lower) = week-clustered bootstrap (2,000) vs JL3.

| cell | months | window | ulc base / 4.84 / live | mean change $/wk base / 4.84 / live | max DD JL3 -> cell | worst week JL3 -> cell | P(ulc lower) | engine controls: pct ulc / pct mean (valid) | tier |
|--|--|--|--|--|--|--|--|--|--|
| DD_W250_T10000 | 0 | not landed | | | | | | | |
| DD_W60_T10000 | 0 | not landed | | | | | | | |
| ND_cut_N5_k1.0 | 0 | not landed | | | | | | | |
| ND_cut_N10_k0.5 | 0 | not landed | | | | | | | |
| ND_press_N5_k1.5 | 0 | not landed | | | | | | | |
| ND_press_N20_k1.0 | 0 | not landed | | | | | | | |
| VT_N10_q50_hi1.0 | 0 | not landed | | | | | | | |
| VT_N10_q75_hi1.0 | 0 | not landed | | | | | | | |
| SS_noAsia_T4000 | 0 | not landed | | | | | | | |
| SS_noAsia_T9000 | 0 | not landed | | | | | | | |
| CAP_nonlon_8 | 0 | not landed | | | | | | | |
| CAP_asia_8 | 0 | not landed | | | | | | | |
| J1 | 0 | not landed | | | | | | | |
| J2 | 0 | not landed | | | | | | | |
| J3 | 0 | not landed | | | | | | | |

Engine tiers: none (no cell landed)

### 2b. Freed-book effects (exact engine, trades only in JL3 = skipped, only in the cell = gained, common-trade change = path / lot effect), base-lot dollars
- not landed yet (first engine cells in L6M/HOLD months are queued ahead of everything older).

## 3. Walk-forward (arithmetic screen)
Frozen FIT pick (rule of PREREG_MC.md, best FIT efficiency over all 65): **VT_N10_q50_hi1.0**. Rolling trailing-12-month pick (PREREG_MC_ADD1; "none" when no eligible cell has ulcer ratio / mean ratio < 1): picks by month 202404 VT_N10_q50_hi1.5, 202405 SS_all_T4000, 202406 SS_all_T4000, 202407 SS_all_T4000, 202408 SS_all_T4000, 202409 SS_all_T4000, 202410 SS_all_T4000, 202411 SS_all_T4000, 202412 SS_all_T4000, 202501 SS_all_T4000, 202502 SS_all_T4000, 202503 ND_cut_N5_k1.0, 202504 VT_N10_q50_hi1.5, 202505 VT_N10_q50_hi1.5, 202506 VT_N10_q50_hi1.5, 202507 VT_N10_q50_hi1.5, 202508 ND_cut_N10_k0.5, 202509 ND_cut_N10_k1.0, 202510 ND_cut_N10_k0.5, 202511 ND_cut_N10_k0.5, 202512 ND_cut_N10_k0.5, 202601 ND_cut_N10_k1.0, 202602 ND_cut_N10_k1.0, 202603 SS_noAsia_T2500, 202604 SS_noAsia_T2500, 202605 SS_noAsia_T2500, 202606 SS_noAsia_T2500, 202607 SS_noAsia_T2500, 202608 SS_noAsia_T2500, 202609 SS_noAsia_T2500, 202610 SS_noAsia_T2500.

| window | JL3 ulcer / mean $/wk | frozen FIT pick ulc / mean (eff) | rolling pick ulc / mean (eff) | lots removed (rolling) |
|--|--|--|--|--|
| L3M | 10841 / 16721 | -1.1% / -10.3% (+10.2) | -0.1% / -4.3% (+4.3) | 5.8% |
| L6M | 9176 / 20109 | -3.0% / -16.8% (+16.6) | -0.5% / -4.6% (+4.3) | 5.8% |
| HOLD | 27872 / 9996 | +4.2% / -29.1% (+47.0) | +0.3% / +3.7% (-3.3) | 5.8% |
| GAP | 17546 / 8970 | -1.8% / -16.3% (+17.4) | +40.8% / -34.5% (+114.8) | 5.8% |
| PRE | 31421 / 6359 | -16.1% / -0.7% (-15.5) | +7.2% / -26.7% (+46.1) | 5.8% |
| X' (partial: from 2024-04) | 22483 / 3241 | -5.3% / -16.0% (+12.7) | +19.4% / -6.8% (+28.1) | 5.8% |
| pooled | 24344 / 8022 | -7.8% / -15.6% (+9.2) | +9.7% / -9.2% (+20.9) | 5.8% |

## 4. Arithmetic vs engine (landed months)
| cell | months | lots ratio engine / arithmetic (cell vs JL3) | P&L landed months: engine / arithmetic / JL3 | daily corr engine-arith / engine-JL3 |
|--|--|--|--|--|
| not landed yet | | | | |

## 5. Selection nulls and planted-edge check
Shifted-label nulls (the policy's multiplier series moved 11 / 23 / 37 days; screen path; pooled ALL43; ulc / mean vs JL3 and the real policy):

| cell | real | shift 11 | shift 23 | shift 37 |
|--|--|--|--|--|
| DD_W250_T10000 | -27.1% / -31.2% | -22.3% / -23.8% | -13.5% / -30.2% | -13.8% / -34.6% |
| DD_W60_T10000 | -25.0% / -32.2% | -22.1% / -22.2% | -13.5% / -28.7% | -13.8% / -32.5% |
| ND_cut_N5_k1.0 | +1.2% / -4.6% | +17.4% / -5.3% | +3.3% / -4.1% | +3.1% / -2.5% |
| ND_cut_N10_k0.5 | +0.9% / -8.3% | +6.9% / -5.5% | +14.7% / -8.7% | -5.0% / -0.4% |
| ND_press_N5_k1.5 | +6.1% / +8.0% | +11.2% / +9.0% | +10.7% / +14.0% | +10.5% / +13.2% |
| ND_press_N20_k1.0 | +30.6% / +26.7% | +52.1% / +25.1% | +44.1% / +24.0% | +20.2% / +22.7% |
| VT_N10_q50_hi1.0 | -7.8% / -15.6% | -8.5% / -12.0% | -6.7% / -11.9% | -8.8% / -8.9% |
| VT_N10_q75_hi1.0 | -1.3% / -6.5% | -3.7% / -7.6% | -5.4% / -4.2% | -1.3% / -5.7% |

Planted edge (the days after a ND_cut_N10_k0.5 trigger made 60% worse per trade: a real, causal, forward edge of the kind these policies claim to exploit; policy state recomputed on the planted path). Planted JL3 pooled mean -4,216 $/wk, ulcer 901084; policies on the planted path (ulc change / mean change in $/wk):
- ND_cut_N10_k0.5: lots removed 15.2%, ulc -60.1%, mean +4,421 $/wk -> detected: YES (ulcer down and mean up)
- ND_cut_N5_k0.5: lots removed 15.4%, ulc -56.6%, mean +4,188 $/wk -> detected: YES (ulcer down and mean up)
- ND_cut_N10_k1.0: lots removed 12.2%, ulc -56.5%, mean +4,111 $/wk -> detected: YES (ulcer down and mean up)
- DD_W60_T20000: lots removed 33.4%, ulc -54.2%, mean +3,555 $/wk -> detected: YES (ulcer down and mean up)
- VT_N20_q50_hi1.0: lots removed 5.1%, ulc +0.4%, mean -222 $/wk -> detected: partly / no

## 6. What the policies would have done: 2025-11-17..12-10 drawdown and October 2026 (screen arithmetic; engine where landed)
**2025-11-17..2025-12-10**: JL3 P&L -68,698, in-window max drawdown -82,017 (base lots). Finalists and the frozen pick:

| cell | P&L (change) | window max DD | mean multiplier / days cut | engine P&L / DD |
|--|--|--|--|--|
| DD_W250_T10000 | -42,303 (+26,395) | -49,150 | 0.58 / 15 of 18 | not landed |
| DD_W60_T10000 | -42,303 (+26,395) | -49,150 | 0.58 / 15 of 18 | not landed |
| ND_cut_N5_k1.0 | -64,830 (+3,868) | -78,149 | 0.81 / 7 of 18 | not landed |
| ND_cut_N10_k0.5 | -56,034 (+12,664) | -69,353 | 0.78 / 8 of 18 | not landed |
| ND_press_N5_k1.5 | -68,698 (+0) | -82,017 | 1.00 / 0 of 18 | not landed |
| ND_press_N20_k1.0 | -86,744 (-18,046) | -106,910 | 1.28 / 0 of 18 | not landed |
| VT_N10_q50_hi1.0 | -68,339 (+359) | -81,658 | 0.98 / 9 of 18 | not landed |
| VT_N10_q75_hi1.0 | -68,698 (+0) | -82,017 | 1.00 / 0 of 18 | not landed |
| SS_noAsia_T4000 | -65,297 (+3,401) | -78,616 | session/cap rule | not landed |
| SS_noAsia_T9000 | -68,698 (+0) | -82,017 | session/cap rule | not landed |
| CAP_nonlon_8 | -63,460 (+5,238) | -76,779 | session/cap rule | not landed |
| CAP_asia_8 | -63,460 (+5,238) | -76,779 | session/cap rule | not landed |
| VT_N10_q50_hi1.0 | -68,339 (+359) | -81,658 | 0.98 / 9 of 18 | not landed |

Over all 65 cells the in-window drawdown ranged from -108,711 (ND_press_N20_k0.5) to -42,730 (J2); P&L change ranged -19,847 to +32,439.

**October 2026 (to 10-31; W44 2026-10-26..31 inside)**: JL3 P&L +37,160, in-window max drawdown -24,103 (base lots). Finalists and the frozen pick:

| cell | P&L (change) | window max DD | mean multiplier / days cut | engine P&L / DD |
|--|--|--|--|--|
| DD_W250_T10000 | +34,925 (-2,235) | -18,027 | 0.84 / 7 of 22 | not landed |
| DD_W60_T10000 | +34,925 (-2,235) | -18,027 | 0.84 / 7 of 22 | not landed |
| ND_cut_N5_k1.0 | +37,160 (+0) | -24,103 | 1.00 / 0 of 22 | not landed |
| ND_cut_N10_k0.5 | +37,160 (+0) | -24,103 | 1.00 / 0 of 22 | not landed |
| ND_press_N5_k1.5 | +40,270 (+3,110) | -24,103 | 1.02 / 0 of 22 | not landed |
| ND_press_N20_k1.0 | +58,325 (+21,165) | -36,493 | 1.43 / 0 of 22 | not landed |
| VT_N10_q50_hi1.0 | +37,621 (+461) | -25,216 | 0.86 / 19 of 22 | not landed |
| VT_N10_q75_hi1.0 | +37,615 (+456) | -23,628 | 0.95 / 10 of 22 | not landed |
| SS_noAsia_T4000 | +55,611 (+18,451) | -22,469 | session/cap rule | not landed |
| SS_noAsia_T9000 | +38,732 (+1,572) | -24,103 | session/cap rule | not landed |
| CAP_nonlon_8 | +41,687 (+4,528) | -24,103 | session/cap rule | not landed |
| CAP_asia_8 | +41,687 (+4,528) | -24,103 | session/cap rule | not landed |
| VT_N10_q50_hi1.0 | +37,621 (+461) | -25,216 | 0.86 / 19 of 22 | not landed |

Over all 65 cells the in-window drawdown ranged from -36,493 (ND_press_N20_k1.0) to -12,469 (SS_all_T2500); P&L change ranged -12,787 to +24,791.

## 7. DAY-DONE settings: pointer (W-DD owns them, order 1331Z)
Not rebuilt here. Page autopilot/DS3_DAYDONE_VARIANTS.md (sets TL3_DD_*, queue _dd/pending.txt). Queue action taken by W-MC: the real JL3 cells for L6M+HOLD were moved to the front of _dd/pending.txt (backup pending.txt.bak_mc_1400, order only, file valid) and the _dd queue line in QUEUES.txt now sits right after the W-MC line. W-DD page, verbatim status and verdict lines (at 14:01Z):
> VERDICT (data ends 2026-10-31; FIRST PASS 2026-11-17 13:45Z; OFF landed 0 of 43 months; ulcer index primary; tiers use the calibrated cut-offs): no variant has a scored tier yet (controls or windows missing = NOT FINISHED, never passing). No removal of the live rule is implied; this is a search for a better SETTING of the same layer.
> > VALIDATION (desk standard, W-DD, FIRST PASS, 2026-11-17 13:45Z): trials counted = 37 settings on JL3 (7 named variants LATCH BE BT C D2 D4 F + 30 grid cells = closes {18,22,26,30} x live loss {3,000 4,200 6,000 8,000} for the eval form and for the session-boundary form, minus the two cells that equal REF and C), plus the references REF / OFF and JL2 OFF; controls = 6 families x 30 persistent random-day-halt draws (A day-reset, B open-P&L, C session, D2, D4, F per-book); correction = percentile among the controls of the matching family on the calibrated tiers, and over the 37 settings White RC / Hansen SPA / DSR / BH on weekly P&L deltas vs REF (mean) plus a block-bootstrap reality check on the ulcer statistic and PBO (CSCV, weekly P&L of the 37 + REF); in-sample on the 43 months (no fitted choice; recent windows L6M/L3M and older HOLD/GAP/PRE/X' are the walk-forward-style split); FIRST
> - IDENTITY gate (inert / re-implemented cell = TL3_EV_JL3 trade for trade on 202610 and 202504): pending
> - JL3 months landed (of 43): REF 43; LATCH 0; BE 0; BT 0; C 0; D2 0; D4 0; F 0; OFF 0; grid cells: 0 of 30 with all 43 months, 0 with any month. Inert-month copies written by the prefilter: 0 (a month in which the rule condition never holds on the OFF trade list cannot change anything; verification runs: see section 9).
> - Controls: not built yet: the controls are calibrated on the OFF path once all 43 OFF months have landed (analytic halted-share match; sets pre-listed in the queue). A cell with fewer than 10 valid controls in a window is NOT FINISHED, never passing.

W-DD Table 1 as it stands:
Ulcer = RMS of daily drawdown on cumulative P&L. P(lower) = week-clustered bootstrap (2,000) that the variant ulcer < OFF ulcer. Percentiles: Table 2. Days halted = label days with a trip on the cell's own closed-trade list (open-P&L cells approximate).

| setting | months | L6M | HOLD | GAP | PRE | X' | pooled | P(ulcer lower) L6M / HOLD / pooled | halted days L6M / pooled | halted share of sessions | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|
| a. DAY-DONE as in the engine (22 / live -4,200, eval at entry, until reset) = JL3 | 0 | not landed | | | | | | | | | |
| a2. live rule latched at the 22nd close, until reset | 0 | not landed | | | | | | | | | |
| b1. open P&L counted, checked at entry, until reset | 0 | not landed | | | | | | | | | |
| b2. open P&L counted, checked at each close, latched to reset | 0 | not landed | | | | | | | | | |
| c. halt to next session boundary (22 / -4,200) | 0 | not landed | | | | | | | | | |
| d. halt 2 h | 0 | not landed | | | | | | | | | |
| d. halt 4 h | 0 | not landed | | | | | | | | | |
| f. per-book (books net negative on the day stop) | 0 | not landed | | | | | | | | | |

Same, vs REF (the live setting; ulcer + = lower than live):

| setting | L6M | HOLD | GAP | PRE | X' | pooled |
|--|--|--|--|--|--|--|


## 8. Which survive (per item; FIRST PASS, nothing CONFIRMED)
- **DD** (size x0.5 below a trailing-drawdown threshold, x1 on recovery): finalists DD_W250_T10000, DD_W60_T10000; screen tier FAIL, FAIL; exact-engine tier not landed, not landed. Pooled screen: DD_W250_T10000 ulc -27.1% mean -31.2%; DD_W60_T10000 ulc -25.0% mean -32.2%.
- **NDcut** (size x0.5 after a weak trailing N days): finalists ND_cut_N5_k1.0, ND_cut_N10_k0.5; screen tier FAIL, FAIL; exact-engine tier not landed, not landed. Pooled screen: ND_cut_N5_k1.0 ulc +1.2% mean -4.6%; ND_cut_N10_k0.5 ulc +0.9% mean -8.3%.
- **NDpress** (press x1.5 after a strong trailing N days): finalists ND_press_N5_k1.5, ND_press_N20_k1.0; screen tier FAIL, FAIL; exact-engine tier not landed, not landed. Pooled screen: ND_press_N5_k1.5 ulc +6.1% mean +8.0%; ND_press_N20_k1.0 ulc +30.6% mean +26.7%.
- **VT** (stack volatility targeting): finalists VT_N10_q50_hi1.0, VT_N10_q75_hi1.0; screen tier FAIL, FAIL; exact-engine tier not landed, not landed. Pooled screen: VT_N10_q50_hi1.0 ulc -7.8% mean -15.6%; VT_N10_q75_hi1.0 ulc -1.3% mean -6.5%.
- **SS** (per-session loss stop): finalists SS_noAsia_T4000, SS_noAsia_T9000; screen tier FAIL, FAIL; exact-engine tier not landed, not landed. Pooled screen: SS_noAsia_T4000 ulc -2.4% mean -1.3%; SS_noAsia_T9000 ulc -0.3% mean -0.2%.
- **CAP** (same-direction exposure cap by session beyond London): finalists CAP_nonlon_8, CAP_asia_8; screen tier FAIL, FAIL; exact-engine tier not landed, not landed. Pooled screen: CAP_nonlon_8 ulc -2.3% mean -8.9%; CAP_asia_8 ulc -2.1% mean -8.8%.
- **JOINT** (top VT + SS + CAP = J1; + DD = J2; NDcut + VT = J3; PREREG_MC_ADD2): screen tier FAIL, FAIL, FAIL; exact-engine tier not landed, not landed, not landed. Pooled screen: J1 ulc -13.3% mean -25.1%; J2 ulc -35.2% mean -47.6%; J3 ulc -0.5% mean -20.6%.
- Earlier one-layer studies (old bases; DS3_SIZING_VOLSCALE: DEAD, leverage-after-calm; DS3_SIZING_RECENT: DEAD; DS3_RISK_OFF: hold the stop; DS3_QUIT*: no usable quit rule; DS3_HALT*: performance halts do not beat random halts) are the prior; this page re-runs them jointly on JL3 (existing live layers, incl. the London cap and the day lock, stay ON in every cell).

Reference rows: JL3 itself (no overlay) is the reference for every comparison; a policy that removes nothing is not a result. Nothing here removes a live protection.
