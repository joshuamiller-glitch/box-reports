# DS3_ZONES_3_L2_TAPE_LP_AGAINST_V13T - FINAL: LP_AGAINST_25_4h_D40 = NOISE on the truth base V13T (ZL-2, 2026-11-02)
V13T = V13Z (nfix, ordering fix) with the five take lines OFF, lock none (ov nfix=True, lines='empty'; same config as base C of DS3_ZONES_3_L2_TAPE_LP_AGAINST_NFIX.md). The engine's own exit-cost model is used unchanged (the BASE-4 V13T_LIVE preset with xcost 0.80 / stopcost 2.45 was not yet available; cancel-on-exit is the V13Y/V13Z ordering fix).
## LP_AGAINST natural mask (2,081 rows, 513 taken)
saved $k lock none: L6M 9.8 / HOLD 2.7 / PRE 75.0 / X' -13.5 / ALL 64.1; per year 2023 -4.4, 2024 +20.6, 2025 +49.7, 2026 -1.8. 2,001-family null (same natural scan in the families): p(min L6M,HOLD,PRE) = 0.22, p(min with X') = 0.25, shuffled-day 0.43. Phase-averaged maxDD cut (9 phases): L6M -2.3 / HOLD -1.7 / MID +6.8 / PRE +4.3 / X' -16.3 (V13Y band for reference: L6M 15.5, PRE 11.5, X' 14.1; no V13T band published yet, but the cut is negative so the band is moot). FINAL LABEL: NOISE. Shadow logging optional; Shadow spec updated.
## Other ZL-2 tape leads on V13T (phase-averaged cut %, sd in brackets; d$k = total $ change vs V13T base in the window, phase 0)
| cell | L6M | HOLD | MID | PRE | X' | d$k L6M/HOLD/MID/PRE/X' |
|--|--|--|--|--|--|--|
| large prints any side (T25 4h, skip) | +11.8 (7.8) | +8.7 (7.5) | +2.3 (21.3) | +11.2 (6.8) | -19.3 (8.5) | +78 / +92 / -18 / -17 / -43 |
| TLQ asia half | +15.1 (6.9) | +3.9 (6.9) | -31.0 (24.5) | +4.5 (0.9) | +7.9 (3.8) | -14 / -56 / -24 / -23 / +20 |
| TCP hvn1_60d half | +10.3 (3.2) | +5.0 (3.6) | 0 | +0.4 (0.7) | +3.2 (3.4) | +22 / +17 / 0 / -23 / -10 |
| TCP hvn1_60d skip | -1.2 (7.4) | -0.2 (6.4) | 0 | -0.2 (1.4) | +7.9 (4.8) | -15 / -31 / 0 / -3 / +12 |
| TCD ext A30 half | +36.8 (7.7) | +26.7 (6.4) | -18.7 (64.1) | +11.4 (1.2) | -7.5 (6.5) | +31 / -66 / -37 / -210 / +21 |
Reading (V13Y band as reference, flip 2%: L6M 15.5, HOLD 13.3, MID 26.8, PRE 11.5, X' 14.1): only TCD ext A30 half clears L6M and HOLD, and it sits just under PRE (11.4 vs 11.5) with X' -7.5 and PRE dollars -210k: not a lead. No cell passes L6M and PRE-or-X' together with no-harm. No PASS; all Shadow only.
