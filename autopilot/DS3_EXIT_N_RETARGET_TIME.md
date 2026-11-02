# DS3_EXIT_N_RETARGET_TIME - E4: RE-TARGET and TIME/SESSION exits on V13T_LIVE (ZL-2, 2026-11-02T14:37Z; Shadow only, no PASS)
Prereg ZL2_EXIT_N_E4_prereg.md sha256 6623cc0e6a53a199684f4200360c1bd0b25a136e90feba48b6089e935d2bea94 (logged in DECISIONS.md before any E4 statistic). Base = d7_v13t.run_v13t_live (xcost 0.80, stopcost 2.45, lines empty, lock none, cancel-on-exit), grid 1sh. Cost model in the injections: re-target exit = resting limit at the line, cost 0; time/session exits = market, cost 0.80 (BASE-4 inject API as is). Cuts: weekly-cumulative maxDD of the 11-book composite, positive = shallower; PA = mean over 9 lock-reset phases; band (V13Y, flip 2%; V13T band not yet published): L6M 15.5, HOLD 13.3, MID 26.8, PRE 11.5, X' 14.1. "drop" = PA cut with the carrying weeks removed from base and cell (L6M 2026 W27-38, PRE 2024 W34-51, X' 2023 W21-41).

## 1. Phase-averaged table (cells run through 9 phases)
| cell | n exits | PA L6M | HOLD | MID | PRE | X' | drop L6M / PRE / X' | d total $k |
|--|--|--|--|--|--|--|--|--|
| RT100_BTsess_ALL | 250 | +2.9 | +2.9 | -6.5 | +0.1 | +5.4 | +0.0 / -0.1 / +1.5 | +37 |
| RT100_BTswing_ALL | 1076 | +21.5 | +18.6 | -4.9 | +0.3 | +3.4 | +11.9 / +0.6 / +32.1 | +143 |
| RT100_BTswing_HM | 189 | +5.0 | +5.0 | -4.3 | +0.2 | +1.7 | +0.0 / +0.0 / +2.4 | +11 |
| RT100_BTswing_KB | 476 | +13.2 | +12.3 | -1.5 | -0.1 | +8.1 | +0.5 / +0.5 / +18.6 | +60 |
| RT100_BTswing_MV | 124 | +0.3 | +0.3 | +4.3 | +0.0 | +2.1 | +0.1 / +0.0 / +0.0 | +18 |
| RT100_BTswing_PE | 201 | +0.3 | +0.3 | -9.1 | -0.1 | -1.5 | +2.5 / -0.2 / +12.0 | +27 |
| RT100_BTswing_SM | 86 | +2.6 | +2.6 | +0.8 | +0.3 | +1.1 | +8.9 / +0.5 / +0.8 | +27 |
| RT100_POC_ALL | 439 | +8.1 | +8.1 | -20.4 | -2.4 | -8.4 | +2.8 / -1.0 / -11.3 | -70 |
| RT70_BTswing_ALL | 1076 | +19.6 | +18.8 | -0.4 | +0.7 | +9.0 | +14.1 / +0.5 / +29.2 | +105 |
| RT70_BTswing_HM | 189 | +4.3 | +4.3 | -1.4 | +0.4 | -0.2 | +0.0 / +0.0 / -0.2 | +9 |
| RT70_BTswing_KB | 476 | +12.0 | +11.6 | -0.9 | +0.3 | +8.4 | +0.6 / +0.6 / +17.0 | +55 |
| RT70_BTswing_MV | 124 | +0.2 | +0.2 | +4.9 | +0.0 | +2.2 | +0.1 / +0.0 / +0.0 | +17 |
| RT70_BTswing_PE | 201 | -0.6 | -0.6 | -5.6 | +0.2 | +0.9 | +3.5 / +0.1 / +13.3 | -2 |
| RT70_BTswing_SM | 86 | +4.1 | +4.1 | +1.3 | -0.2 | +1.2 | +9.9 / -0.2 / +0.9 | +26 |
| TM_F10_KB | 2788 | +8.7 | +8.4 | -9.7 | +3.0 | +16.3 | +1.0 / +2.5 / +18.0 | +32 |
| TM_F5_KB | 2781 | +9.9 | +9.7 | -0.4 | -0.4 | +18.4 | +4.3 / -0.9 / +17.0 | +12 |
| TM_MH240_ALL | 4985 | +15.9 | +15.7 | +0.3 | -12.1 | -47.3 | +0.0 / -12.0 / +47.4 | -448 |
| TM_MH240_KB | 1117 | +3.3 | +3.3 | -1.4 | +1.2 | +10.7 | +0.0 / +2.2 / +17.7 | -24 |
| TM_NY1130_MV | 473 | +1.0 | +1.0 | +0.0 | +0.3 | -0.8 | +2.3 / +0.1 / +4.2 | -12 |

## 2. All cells, phase 0 (cut % / d mean $ per week in L6M and PRE; n exits)
| cell | n | cut L6M | cut HOLD | cut MID | cut PRE | cut X' | d$/wk L6M | d$/wk PRE |
|--|--|--|--|--|--|--|--|--|
| RT100_BTswing_ALL | 1076 | +30.0 | +17.5 | -0.8 | +0.3 | +18.1 | +3658 | +251 |
| RT70_BTswing_ALL | 1076 | +26.7 | +19.6 | +4.3 | +1.6 | +23.3 | +3788 | -170 |
| TM_MH240_ALL | 4985 | +19.3 | +17.3 | +2.2 | -13.8 | -42.1 | +945 | -3036 |
| TM_MH60_HM | 3059 | +18.0 | +15.4 | +5.8 | -1.6 | -2.4 | -1553 | -801 |
| TM_ASLDN_KB | 843 | +15.1 | +9.5 | -12.0 | -2.3 | +16.9 | +903 | -18 |
| TM_MH240_PE | 1167 | +12.9 | +12.9 | +0.3 | -12.7 | +23.4 | +438 | -2446 |
| RT100_POC_ALL | 439 | +12.6 | +12.6 | +1.1 | -3.4 | -3.4 | -851 | -129 |
| TM_MH120_KB | 2318 | +10.1 | +10.1 | -9.9 | -1.6 | +18.5 | +66 | -594 |
| TM_F10_KB | 2788 | +9.5 | +9.4 | -5.9 | +3.8 | +15.4 | +944 | +515 |
| TM_F5_KB | 2781 | +8.2 | +8.2 | +2.6 | +0.4 | +14.0 | +788 | +393 |
| TM_F5_MV | 2679 | +6.5 | +6.5 | -9.0 | -2.8 | -11.3 | +316 | -466 |
| RT70_POC_ALL | 439 | +6.1 | +6.1 | -1.7 | -4.1 | -4.5 | -1343 | -95 |
| TM_MH240_SM | 546 | +5.3 | +5.3 | -0.8 | -1.3 | -16.9 | +256 | -71 |
| TM_MH120_ALL | 9783 | +4.8 | +2.5 | -62.9 | -34.5 | -107.8 | -2589 | -6517 |
| TM_MH120_SM | 908 | +4.7 | +4.7 | -1.3 | -9.7 | -35.6 | -110 | -830 |
| TM_F5_SM | 1053 | +4.3 | +4.3 | +5.7 | -6.1 | -11.7 | -356 | -1233 |
| TM_F30_MV | 2526 | +4.2 | +4.2 | -10.3 | -1.9 | -11.0 | +262 | -223 |
| TM_MH240_KB | 1117 | +4.0 | +4.0 | -1.9 | +0.0 | +11.2 | +350 | -364 |
| RT70_BTsess_ALL | 250 | +4.0 | +4.0 | -3.6 | +0.8 | -0.5 | +233 | -273 |
| TM_F20_KB | 2677 | +3.8 | +3.8 | -12.9 | +0.6 | +14.8 | +579 | +559 |
| TM_F30_KB | 2634 | +3.6 | -0.6 | -46.4 | -1.3 | +15.9 | +320 | +7 |
| TM_ASLDN_SM | 387 | +3.1 | +3.1 | +7.9 | -3.0 | -9.6 | +95 | -1097 |
| RT100_BTsess_ALL | 250 | +3.1 | +3.1 | -8.5 | +0.5 | +0.3 | +116 | +326 |
| TM_MH60_SM | 1285 | +2.7 | +2.7 | -3.6 | -9.9 | -40.3 | -1329 | -1587 |
| TM_NY1130_MV | 473 | +2.2 | +2.2 | +0.0 | +0.8 | +5.1 | -28 | -77 |
| TM_F10_MV | 2637 | +2.0 | +2.0 | -11.1 | -2.8 | -6.1 | +195 | -566 |
| TM_NY1130_ALL | 1947 | +1.3 | +1.3 | -10.7 | +0.9 | -4.9 | -18 | -1951 |
| TM_F20_MV | 2558 | +1.1 | +1.1 | -13.2 | -2.6 | -7.1 | +356 | -527 |
| TM_F30_SM | 957 | +0.3 | +0.3 | -26.3 | -10.9 | -12.7 | +146 | -994 |
| TM_MH240_HM | 1032 | +0.0 | +0.0 | +4.7 | +0.1 | +9.7 | -127 | -88 |
| RT100_BTpd_ALL | 38 | +0.0 | +0.0 | -1.6 | +0.0 | +0.0 | -29 | +227 |
| RT70_BTpd_ALL | 38 | +0.0 | +0.0 | -1.2 | +0.0 | +0.0 | +9 | -177 |
| TM_ASLDN_MV | 820 | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 | +0 | +0 |
| TM_NY1130_SM | 117 | +0.0 | +0.0 | +0.0 | +0.0 | +0.0 | +0 | +0 |
| TM_NY1130_PE | 501 | +0.0 | +0.0 | -5.7 | +0.6 | +12.3 | +0 | -1241 |
| RT100_HVN_ALL | 198 | -0.1 | -0.1 | +0.0 | +0.0 | -1.1 | -542 | -723 |
| TM_MH60_KB | 3719 | -0.3 | -0.3 | +2.4 | +5.2 | +17.4 | -392 | -790 |
| TM_NY1130_HM | 344 | -0.4 | -0.4 | +0.0 | +0.5 | +3.8 | -93 | -323 |
| TM_NY1130_KB | 512 | -0.5 | -0.5 | -5.0 | -0.9 | +0.3 | +103 | -310 |
| TM_MH60_MV | 3515 | -1.2 | -1.2 | -1.6 | +1.0 | -4.4 | +773 | -645 |
| RT100_LP_ALL | 1413 | -1.9 | -1.9 | -13.2 | +3.1 | -5.5 | +643 | +982 |
| RT70_HVN_ALL | 198 | -2.0 | -2.0 | +0.0 | +0.0 | -0.8 | -457 | -651 |
| TM_MH120_HM | 2019 | -2.3 | -2.3 | +5.2 | -0.1 | +3.3 | +154 | -438 |
| TM_MH240_MV | 1123 | -2.9 | -2.9 | +0.0 | -1.8 | +1.7 | +27 | -95 |
| TM_MH120_MV | 2216 | -3.4 | -3.4 | -2.6 | -1.2 | -2.8 | -63 | -20 |
| TM_F10_SM | 997 | -3.7 | -3.7 | -5.6 | -10.0 | -17.0 | -597 | -1185 |
| TM_MH120_PE | 2322 | -4.3 | -4.3 | -54.4 | -19.3 | -45.5 | -2636 | -4664 |
| TM_F5_HM | 2299 | -6.9 | -6.9 | +6.1 | -0.7 | +7.2 | -1251 | +315 |
| TM_F20_SM | 968 | -7.1 | -7.1 | -16.8 | -8.6 | -15.6 | -194 | -1254 |
| TM_ASLDN_HM | 767 | -11.4 | -11.4 | +9.1 | -0.4 | +11.1 | -1687 | +519 |
| RT70_LP_ALL | 1413 | -11.7 | -11.7 | -9.3 | -2.6 | -20.7 | -351 | +694 |
| TM_F30_HM | 2161 | -13.2 | -13.2 | +7.4 | +0.2 | +17.3 | -2491 | +150 |
| TM_F10_HM | 2295 | -13.3 | -13.3 | +5.9 | +0.7 | +7.3 | -1773 | +417 |
| TM_MH60_ALL | 15230 | -15.7 | -15.7 | -81.3 | -171.0 | -4.5 | -11568 | -12957 |
| TM_MH60_PE | 3652 | -18.4 | -18.4 | -49.9 | -57.8 | +28.5 | -9068 | -9163 |
| TM_F20_HM | 2190 | -18.5 | -18.5 | +3.7 | +0.7 | +15.3 | -1859 | +349 |
| TM_ASLDN_ALL | 3660 | -20.6 | -20.6 | -14.8 | -6.7 | +12.8 | -5000 | -2827 |
| TM_F30_PE | 2589 | -21.4 | -21.4 | -27.4 | -2.5 | +27.0 | -5700 | -5281 |
| TM_F30_ALL | 10867 | -21.4 | -21.4 | -103.1 | -6.9 | -51.9 | -7463 | -6316 |
| TM_ASLDN_PE | 843 | -27.4 | -27.4 | -19.7 | -1.1 | +42.4 | -4311 | -2253 |
| TM_F5_ALL | 11643 | -34.8 | -34.8 | -73.0 | -3.1 | -51.1 | -5996 | -5561 |
| TM_F5_PE | 2831 | -47.0 | -47.0 | -78.5 | -7.3 | -4.6 | -5493 | -4593 |
| TM_F20_PE | 2685 | -55.4 | -55.4 | -32.9 | -2.5 | +2.8 | -4769 | -5520 |
| TM_F10_PE | 2770 | -67.8 | -67.8 | -50.3 | -7.1 | +2.0 | -7256 | -5029 |
| TM_F10_ALL | 11487 | -73.3 | -73.3 | -67.0 | -6.7 | -33.8 | -8487 | -5825 |
| TM_F20_ALL | 11078 | -76.1 | -76.1 | -72.0 | -6.3 | -43.7 | -5888 | -6371 |

## 3. Placebos (same cost model; a = random rows same count per day, b = same count per book x session, c = per-day counts shuffled; rank = share of draws whose phase-0 cut is below the real cut, high = real beats placebo)
| cell | kind | draws | rank L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|
| RT100_BTswing_ALL | a | 100 | 0.96 | 0.96 | 0.68 | 0.83 | 0.87 |
| RT100_BTswing_ALL | b | 100 | 0.80 | 0.87 | 0.65 | 0.47 | 0.85 |
| RT100_BTswing_ALL | c | 100 | 0.91 | 0.92 | 0.58 | 0.57 | 0.69 |
| RT70_BTswing_ALL | a | 100 | 0.92 | 0.95 | 0.72 | 0.91 | 0.95 |
| RT70_BTswing_ALL | b | 100 | 0.80 | 0.88 | 0.65 | 0.66 | 0.96 |
| RT70_BTswing_ALL | c | 100 | 0.91 | 0.95 | 0.71 | 0.73 | 0.92 |
| RT100_POC_ALL | a | 100 | 0.87 | 0.91 | 0.90 | 0.13 | 0.45 |
| RT100_POC_ALL | b | 100 | 0.65 | 0.80 | 0.65 | 0.38 | 0.33 |
| RT100_POC_ALL | c | 100 | 0.78 | 0.86 | 0.58 | 0.35 | 0.23 |
| TM_F10_KB | a | 100 | 0.88 | 0.93 | 0.69 | 0.99 | 0.98 |
| TM_F10_KB | b | 100 | 0.94 | 0.98 | 0.69 | 1.00 | 0.95 |
| TM_F10_KB | c | 100 | 0.92 | 0.95 | 0.70 | 1.00 | 0.98 |

Rank on the mean $ change per week (same placebo draws; share of draws below the real cell):
| cell | kind | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| RT100_BTswing_ALL | a | 0.99 | 0.99 | 0.70 | 0.93 |
| RT100_BTswing_ALL | b | 0.98 | 0.98 | 0.78 | 0.96 |
| RT100_BTswing_ALL | c | 0.99 | 1.00 | 0.60 | 0.66 |
| RT70_BTswing_ALL | a | 1.00 | 0.94 | 0.46 | 0.91 |
| RT70_BTswing_ALL | b | 0.98 | 0.94 | 0.79 | 0.95 |
| RT70_BTswing_ALL | c | 0.98 | 0.96 | 0.65 | 0.88 |
| RT100_POC_ALL | a | 0.21 | 0.28 | 0.35 | 0.54 |
| RT100_POC_ALL | b | 0.49 | 0.61 | 0.71 | 0.51 |
| RT100_POC_ALL | c | 0.43 | 0.50 | 0.48 | 0.23 |
| TM_F10_KB | a | 1.00 | 0.97 | 1.00 | 1.00 |
| TM_F10_KB | b | 1.00 | 1.00 | 1.00 | 0.99 |
| TM_F10_KB | c | 1.00 | 0.98 | 1.00 | 1.00 |

## 4. Plain sentences and labels
RE-TARGET to a fresh BT swing flip level (RT100 / RT70, limit at the line, cost 0): on true fills it cuts the PA maxDD in L6M from base by 21.5% / 19.6% and HOLD 18.6% / 18.8% (V13Y band 15.5 / 13.3) at +$143k / +$105k total over 2023-04..2026-10 (mean +$3.7k / week in L6M), and the L6M cut survives the carrying-week drop (+11.9 / +14.1); but PRE is flat (+0.3 / +0.7, band 11.5), X' is below band (+3.4 / +9.0), and placebo ranks are 0.80-0.96 (random lines at the same distance get most of it). Label: PARTIAL, L6M/HOLD only, FAILS PRE + X': not a line for THP_POLICY_D7.txt; per book the cut is KB (+13.2 / +12.0 L6M, X' +8.1) and nowhere else. Shadow only.
RE-TARGET to the other line sets (broken prior-day H/L, broken Asia/London H/L, POC day, HVN 60d, fresh large prints): no cut above band in any window (best BTsess +2.9 L6M; POC +8.1 L6M but PRE -2.4 and X' -8.4 with -$70k; HVN and LP negative). NOISE.
TIME / SESSION exits (flatten N min before the session end, NY-AM at 11:30, Asia at London open, max hold 60/120/240): on true fills with 0.80 pt per market exit they lose money and deepen maxDD almost everywhere (all-books F10 -$8.5k/wk L6M, MH60 -$11.6k/wk). Only book KB is positive: F10 PA L6M +8.7 / PRE +3.0 / X' +16.3 (band 15.5 / 11.5 / 14.1), F5 +9.9 / -0.4 / +18.4; carrying week dropped L6M +1.0 / +4.3; placebo ranks 0.88-0.94 (L6M), 0.99-1.00 (PRE) but L6M below band. Label: NOISE for L6M (below band, carried by the single episode); KB flatten-before-close is X'-only, not a THP line. No time/session exit passes on N. No RISK-KEEP (no cell is positive in L6M AND PRE with the carrying week dropped).
Caveats: V13T band not yet published (V13Y band used); injection deltas use the BASE-4 API unchanged (library fill cost on non-target exits, exit price at the line); BT levels from ZL-1 streams as formed (knowable index ek); lock-12R frame not run (reference only).

## UPDATE: re-key to V13T PA9 band and KB-only BT re-target
See DS3_ZONES_3_L2_TAPE_V13T_REKEY.md sections 3-4: no E4 verdict flips; KB-only BT swing re-target NOT a lead (L6M +13.2 below the 17.9 band, PRE flat, X' carried by one month).
