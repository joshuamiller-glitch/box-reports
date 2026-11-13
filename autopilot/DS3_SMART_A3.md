# DS3_SMART_A3 — T-SMART item A3: structure stops with equal-$ lots (W-SM3)

Generated 2026-11-13 04:39Z UTC. Exact engine, one set per job (TP engine), base JN05W2 = live panel + F3 + E1 + C22 + BR3S + FLAT45K (JN05W2J = same on JN04RM). Shadow only, no PASS claim.

**CAVEAT (every table):** the engine state cut fires in the engine but did NOT fire live on 2026-11-11 (autopilot/DS3_P7_CUT_FIDELITY.md). Rows marked **S0 = state cut OFF = the live-realistic case** are read first and compared with SMA3_REF_S0 (JN05W2 with every state cut switched off, K7 flat45 kept); **S1** rows keep the state cut and compare with JN05W2.

Hook th_smart/sm_hooks.py (copy of W-X ec_hooks, features fr1/fr3/fr5/fr15 = confirmed 2-2 fractal pivot of the 1/3/5/15-min bars, so = session open, sx = running session extreme, kc = Keltner mid EMA20 of 5-min closes, st = Supertrend, vwap = session VWAP): structure stop at the level - buf, exit filled 1.4 pt adverse (live native central; WORKED stop = market exit at the decision second, the native 60 and 80 catastrophe stops stay as backstops), lots x 60/se (se = distance to the stop clamped 25..60 pts, so up to x2.4) applied after the live sizers, then the day caps and locks apply to those lots. Prereg autopilot/SMART_A3_PREREG.md. Name SMA3_<feat><buf>_<books>_<S0|S1>[J].

Dead-cell lookup (loss|struct_stop_eq|<book>|<feat>, 32 specs): 0 hits; first-order evidence from W-X fo_a.parquet (LPB): only U7 kc buf2 (+17.7% L6M cut, +$717/wk) and K7 vwap buf6 (+9.4%, +$919) were positive; P7 / H7 / M7 / A7 structure stops were null or negative.

## 0. Trend-week clause first, then L6M / HOLD (a window appears only when all its months are present)

| set | months | reference | 5 best wks kept | winning wks turned losing | L6M cut % | L6M d mean/wk (all wks) | HOLD cut % | HOLD d mean/wk | PRE cut % | X' cut % | GAP cut % | WF cut / beat |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| SMA3_FR154_ALL_S0 | 6 | SMA3_REF_S0 | 99% ($299k of $302k) | 2 of 19 | -28.9 | -1922 | - | - | - | - | - | - |
| SMA3_FR154_K_S0 | 6 | SMA3_REF_S0 | 101% ($305k of $302k) | 0 of 19 | 2.2 | 114 | - | - | - | - | - | - |
| SMA3_FR154_K_S1 | 6 | JN05W2 | 100% ($315k of $316k) | 0 of 20 | -2.5 | 37 | - | - | - | - | - | - |
| SMA3_FR156_K_S0 | 5 | SMA3_REF_S0 | (running) ||||||||||
| SMA3_KC2_ALL_S0 | 6 | SMA3_REF_S0 | 91% ($276k of $302k) | 7 of 19 | -85.0 | -3976 | - | - | - | - | - | - |
| SMA3_KC2_U_S0 | 6 | SMA3_REF_S0 | 104% ($314k of $302k) | 0 of 19 | -14.3 | 1081 | - | - | - | - | - | - |
| SMA3_KC2_U_S1 | 6 | JN05W2 | 109% ($346k of $316k) | 1 of 20 | 1.1 | 712 | - | - | - | - | - | - |
| SMA3_KC4_U_S0 | 6 | SMA3_REF_S0 | 103% ($312k of $302k) | 0 of 19 | -6.4 | 379 | - | - | - | - | - | - |
| SMA3_KU_S0 | 6 | SMA3_REF_S0 | 103% ($310k of $302k) | 0 of 19 | -12.1 | 871 | - | - | - | - | - | - |
| SMA3_KU_S1 | 6 | JN05W2 | 109% ($346k of $316k) | 1 of 20 | -1.5 | 706 | - | - | - | - | - | - |
| SMA3_REF_S0 | 6 |  | (reference) ||||||||||

cut % = stack maxDD vs the reference (positive = shallower); d mean = all-weeks mean difference ($/wk, carry week kept); WF = bi-weekly re-pick walk-forward (only with all 43 months).

## 1. Per book, L6M (cell vs its reference): trades, mean lots, d net $/wk, full stops per wk, EarlyCut (structure-stop) exits per wk, StateCut exits per wk

**SMA3_FR154_ALL_S0** vs SMA3_REF_S0

| book | trades cell / ref | mean lots cell / ref | d net $/wk | full stops/wk cell / ref | structure exits/wk | StateCut/wk |
|---|---|---|---|---|---|---|
| K7 | 1498 / 1509 | 1.19 / 1.15 | +426 | 0.46 / 0.50 | 27.82 | 0.00 |
| P7 | 779 / 807 | 3.87 / 3.64 | -2626 | 12.26 / 13.98 | 1.57 | 0.00 |
| U7 | 275 / 273 | 2.75 / 2.74 | +27 | 4.25 / 4.21 | 0.08 | 0.15 |
| H7 | 174 / 175 | 2.03 / 1.86 | -228 | 1.53 / 1.84 | 0.61 | 0.84 |
| M7 | 634 / 622 | 1.22 / 1.21 | +522 | 11.30 / 11.95 | 0.69 | 0.00 |
| A7 | 347 / 346 | 1.00 / 1.00 | -47 | 4.75 / 4.75 | 0.08 | 0.00 |

**SMA3_FR154_K_S0** vs SMA3_REF_S0

| book | trades cell / ref | mean lots cell / ref | d net $/wk | full stops/wk cell / ref | structure exits/wk | StateCut/wk |
|---|---|---|---|---|---|---|
| K7 | 1497 / 1509 | 1.19 / 1.15 | +137 | 0.46 / 0.50 | 27.82 | 0.00 |
| P7 | 805 / 807 | 3.65 / 3.64 | -36 | 13.95 / 13.98 | 0.00 | 0.00 |
| U7 | 273 / 273 | 2.74 / 2.74 | +0 | 4.21 / 4.21 | 0.00 | 0.15 |
| H7 | 174 / 175 | 1.86 / 1.86 | -46 | 1.84 / 1.84 | 0.00 | 1.07 |
| M7 | 618 / 622 | 1.21 / 1.21 | +96 | 11.84 / 11.95 | 0.00 | 0.00 |
| A7 | 346 / 346 | 1.00 / 1.00 | +0 | 4.75 / 4.75 | 0.00 | 0.00 |

**SMA3_FR154_K_S1** vs JN05W2

| book | trades cell / ref | mean lots cell / ref | d net $/wk | full stops/wk cell / ref | structure exits/wk | StateCut/wk |
|---|---|---|---|---|---|---|
| K7 | 1544 / 1553 | 1.19 / 1.14 | -58 | 0.42 / 0.46 | 19.77 | 11.42 |
| P7 | 1036 / 1037 | 3.50 / 3.50 | +135 | 0.50 / 0.50 | 0.00 | 21.95 |
| U7 | 270 / 271 | 2.73 / 2.73 | -46 | 3.45 / 3.45 | 0.00 | 1.57 |
| H7 | 176 / 176 | 1.86 / 1.86 | +0 | 0.84 / 0.84 | 0.00 | 2.64 |
| M7 | 730 / 733 | 1.19 / 1.19 | +0 | 1.26 / 1.26 | 0.00 | 15.44 |
| A7 | 353 / 353 | 1.00 / 1.00 | +0 | 3.98 / 3.98 | 0.00 | 2.15 |

**SMA3_KC2_ALL_S0** vs SMA3_REF_S0

| book | trades cell / ref | mean lots cell / ref | d net $/wk | full stops/wk cell / ref | structure exits/wk | StateCut/wk |
|---|---|---|---|---|---|---|
| K7 | 1634 / 1509 | 1.66 / 1.15 | -4227 | 0.04 / 0.50 | 45.33 | 0.00 |
| P7 | 971 / 807 | 5.83 / 3.64 | +808 | 3.41 / 13.98 | 21.49 | 0.00 |
| U7 | 263 / 273 | 3.52 / 2.74 | +1222 | 1.34 / 4.21 | 4.25 | 0.11 |
| H7 | 183 / 175 | 2.95 / 1.86 | -474 | 0.61 / 1.84 | 3.60 | 0.42 |
| M7 | 636 / 622 | 1.62 / 1.21 | -16 | 3.22 / 11.95 | 13.26 | 0.00 |
| A7 | 383 / 346 | 1.00 / 1.00 | -489 | 2.84 / 4.75 | 5.86 | 0.00 |

**SMA3_KC2_U_S0** vs SMA3_REF_S0

| book | trades cell / ref | mean lots cell / ref | d net $/wk | full stops/wk cell / ref | structure exits/wk | StateCut/wk |
|---|---|---|---|---|---|---|
| K7 | 1511 / 1509 | 1.14 / 1.15 | -50 | 0.50 / 0.50 | 27.78 | 0.00 |
| P7 | 794 / 807 | 3.66 / 3.64 | -335 | 13.79 / 13.98 | 0.00 | 0.00 |
| U7 | 278 / 273 | 3.50 / 2.74 | +1320 | 1.23 / 4.21 | 4.71 | 0.11 |
| H7 | 176 / 175 | 1.85 / 1.86 | +7 | 1.88 / 1.84 | 0.00 | 1.07 |
| M7 | 621 / 622 | 1.21 / 1.21 | +231 | 11.84 / 11.95 | 0.00 | 0.00 |
| A7 | 345 / 346 | 1.00 / 1.00 | -159 | 4.94 / 4.75 | 0.00 | 0.00 |

**SMA3_KC2_U_S1** vs JN05W2

| book | trades cell / ref | mean lots cell / ref | d net $/wk | full stops/wk cell / ref | structure exits/wk | StateCut/wk |
|---|---|---|---|---|---|---|
| K7 | 1540 / 1553 | 1.14 / 1.14 | -263 | 0.46 / 0.46 | 18.74 | 12.26 |
| P7 | 1036 / 1037 | 3.50 / 3.50 | -48 | 0.50 / 0.50 | 0.00 | 22.07 |
| U7 | 278 / 271 | 3.49 / 2.73 | +1153 | 0.96 / 3.45 | 4.44 | 0.96 |
| H7 | 176 / 176 | 1.86 / 1.86 | +0 | 0.84 / 0.84 | 0.00 | 2.64 |
| M7 | 728 / 733 | 1.19 / 1.19 | -180 | 1.30 / 1.26 | 0.00 | 15.44 |
| A7 | 353 / 353 | 1.00 / 1.00 | -17 | 4.18 / 3.98 | 0.00 | 2.18 |

**SMA3_KC4_U_S0** vs SMA3_REF_S0

| book | trades cell / ref | mean lots cell / ref | d net $/wk | full stops/wk cell / ref | structure exits/wk | StateCut/wk |
|---|---|---|---|---|---|---|
| K7 | 1512 / 1509 | 1.14 / 1.15 | -4 | 0.50 / 0.50 | 27.78 | 0.00 |
| P7 | 797 / 807 | 3.66 / 3.64 | -636 | 13.87 / 13.98 | 0.00 | 0.00 |
| U7 | 279 / 273 | 3.36 / 2.74 | +733 | 1.38 / 4.21 | 4.56 | 0.11 |
| H7 | 176 / 175 | 1.85 / 1.86 | +7 | 1.88 / 1.84 | 0.00 | 1.07 |
| M7 | 623 / 622 | 1.21 / 1.21 | +187 | 11.88 / 11.95 | 0.00 | 0.00 |
| A7 | 345 / 346 | 1.00 / 1.00 | -159 | 4.94 / 4.75 | 0.00 | 0.00 |

**SMA3_KU_S0** vs SMA3_REF_S0

| book | trades cell / ref | mean lots cell / ref | d net $/wk | full stops/wk cell / ref | structure exits/wk | StateCut/wk |
|---|---|---|---|---|---|---|
| K7 | 1502 / 1509 | 1.19 / 1.15 | -43 | 0.46 / 0.50 | 28.01 | 0.00 |
| P7 | 792 / 807 | 3.67 / 3.64 | -519 | 13.79 / 13.98 | 0.00 | 0.00 |
| U7 | 278 / 273 | 3.50 / 2.74 | +1320 | 1.23 / 4.21 | 4.71 | 0.11 |
| H7 | 175 / 175 | 1.86 / 1.86 | -39 | 1.88 / 1.84 | 0.00 | 1.07 |
| M7 | 618 / 622 | 1.21 / 1.21 | +282 | 11.76 / 11.95 | 0.00 | 0.00 |
| A7 | 345 / 346 | 1.00 / 1.00 | -159 | 4.94 / 4.75 | 0.00 | 0.00 |

**SMA3_KU_S1** vs JN05W2

| book | trades cell / ref | mean lots cell / ref | d net $/wk | full stops/wk cell / ref | structure exits/wk | StateCut/wk |
|---|---|---|---|---|---|---|
| K7 | 1520 / 1553 | 1.19 / 1.14 | -46 | 0.42 / 0.46 | 19.58 | 11.11 |
| P7 | 1029 / 1037 | 3.51 / 3.50 | -91 | 0.50 / 0.50 | 0.00 | 21.88 |
| U7 | 277 / 271 | 3.49 / 2.73 | +969 | 0.96 / 3.45 | 4.44 | 0.96 |
| H7 | 176 / 176 | 1.86 / 1.86 | +0 | 0.84 / 0.84 | 0.00 | 2.64 |
| M7 | 720 / 733 | 1.19 / 1.19 | -78 | 1.30 / 1.26 | 0.00 | 15.21 |
| A7 | 351 / 353 | 1.00 / 1.00 | -109 | 4.18 / 3.98 | 0.00 | 2.18 |

## 2. acceptance_p7 (L6M only, fail on > 2 of 20) for complete L6M cells with L6M cut >= 5%


## 3. Transfer to the user lots (K7 4, M7 4, U7 7, P7 12/7/7, H7 7, A7 2; caps x1.75)

The structure-stop lots rule is a ratio (60/se, se 25..60), so the equal-$ risk property is lot-independent; at the user lots the rounding matters less (cell lots K7/M7/A7 are 1-3, so x2.4 rounds up to 2-7) and every day cap / lock scales x1.75 with the lots, so the cap-binding days move with it. R is the book stop x $20 x lots (60 pt x $20 = $1,200 per lot). These pages are at the cell lots; a user-lots rerun is queued only for cells that survive (stage 2).
