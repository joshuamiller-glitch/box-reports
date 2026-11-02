# DS3_ZONES_3_HALF_FINAL_V13TLIVE - HALF vs SKIP vs OFF per line on V13T_LIVE (Z1; 2026-11-02 15:05Z)

Base V13T_LIVE (d7_v13t.run_v13t_live: take lines OFF, lock none, per-book locks, xcost 0.80, stopcost 2.45, resting 30% cancelled on exit, lockfix legs), cap 20261031. POST-HOC, no PASS, Shadow only. Prereg ZONES3_S1_addendum4 (sha d1e7ee34...) and addendum 3 (15ce2722...) in DECISIONS.md. Supersedes DS3_ZONES_3_HALF_FINAL_V13T.md (V13T xcost .995, linear equal-risk), which is left untouched. Equal-risk = real engine lot search (below).

## ANSWER
On V13T_LIVE (take lines off, lock none, xcost 0.80, stopcost 2.45, resting 30% cancelled on exit) no line is worth SKIP over HALF on PRE + L6M together, HALF D20 stays the better action, and NO line is worth keeping on drawdown grounds: the whole HALF layer is a VOLUME effect and every line is DEAD or FRAGILE. Numbers: HALF cuts maxDD L6M +7% / HOLD +7% / MID +25% / PRE +7% / X' -16% (phase-averaged cuts L6M +13%, PRE +4%, X' -14%), none beyond the Z3 PA9 flip-5% band (L6M .219, PRE .099, X' .182, MID .322), and its placebo ranks are chance (100 draws per kind: PRE 0.27 / 0.42 / 0.38, L6M 0.49 / 0.53 / 0.49, HOLD 0.47, MID 0.23-0.34, X' 0.85-0.95); the L6M cut is the one episode ISO 202629-202639 (dropped: +1%). SKIP is not better: whole-layer SKIP +9% L6M, +12% PRE (phase-avg +10%, marginally beyond the PRE band, rank 0.12 / 0.23 / 0.24), X' -34%, and lines SKIP-minus-HALF with the episode dropped are PRE / L6M kijun1h -1.4 / +1.9, PDmid -4.3 / -3.2, CRT4h -4.0 / -2.2, KCup4h +1.3 / -0.1, camH3 +10.1 / 0.0, OTE705 -2.7 / +0.1, OTE79 -0.5 / +2.7, OTE62 +2.6 / -12.7 pp: none passes the rule (> +3 pp in both). Real engine equal-risk (lot search, ALL worst-20 matched to NONE; c* 1.123 HALF, 1.150 SKIP, verified runs): HALF +4.5 (MDE 8.6) L6M, +1.8 (3.1) PRE, +0.6 (3.6) X', +1.7 (2.2) ALL; SKIP +3.5 (12.6) L6M, +3.1 (5.4) PRE, +1.5 (6.2) X', +2.4 (3.7) ALL: both slightly positive and inside MDE, i.e. the layer is about neutral at equal risk. Per-line labels (plain): kijun1h DEAD (PRE +4%, L6M -7%, cut at 0 of 5 D); PDmid DEAD; CRT4h FRAGILE (L6M +7% phase-averaged but -3% with the episode dropped, HOLD/MID cuts with X' -23%); KCup4h DEAD; camH3 DEAD (SKIP PRE +10 pp only, one window); OTE705 DEAD (PRE -8%); OTE79 DEAD; OTE-62 B73 D30 DEAD on this measure (vs the line left out: PRE -0.5%, L6M -0.2%, MID/X' +1.9%, mean -1.2k/wk L6M). By book the L6M carrying episode (W29-W39) sits in K7 (-33k) and M7 (-20k) with U7 positive (+52k); the line effects by book are single-digit $k except M7 (kijun1h SKIP +11k worse, OTE62 -6..-14k) and P7 (CRT4h HOLD -23k, OTE705 SKIP +23k PRE), none systematic. Not done: per-line SKIP-vs-HALF placebos on V13T_LIVE (the rule fails before the placebo step; the V13T xcost .995 run gave ranks 0.05-0.9, one single-window cell at 0.049).


## 1. Whole layer: NONE vs HALF vs SKIP (V13T_LIVE)
| window (weeks) | carrying episode of the HALF layer (ISO peak..trough, depth $k, recovered?) | NONE maxDD | HALF maxDD (cut) | SKIP maxDD (cut) | phase-avg maxDD NONE / HALF / SKIP | maxDD with the episode dropped: NONE / HALF / SKIP (cuts) | worst-20 NONE / HALF / SKIP | Calmar NONE / HALF / SKIP | mean $k/wk NONE / HALF / SKIP (HALF-NONE, SKIP-NONE MDE) | ulcer NONE / HALF / SKIP | CVaR5 NONE / HALF / SKIP | equal-risk mean d (~linear) HALF / SKIP |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1M (view) (5) | 202644..202644, 94, open | 95 | 94 (+1%) | 93 (+3%) | 93 / 89 / 87 | 9 / 33 (-270%) / 35 (-300%) | 86 / 65 / 63 * | 0.18 / 0.14 / 0.14 | 17.1 / 13.1 / 12.6 (-4.0, -4.5; 14.2) | 39 / 41 / 41 | -95 / -94 / -93 | -4.0 / -4.5 |
| L2M (view) (9) | 202644..202644, 94, open | 95 | 94 (+1%) | 93 (+3%) | 94 / 95 / 91 | 53 / 70 (-31%) / 66 (-24%) | 219 / 197 / 196 * | 0.26 / 0.23 / 0.24 | 24.3 / 21.9 / 21.8 (-2.5, -2.6; 10.5) | 37 / 40 / 39 | -95 / -94 / -93 | -2.5 / -2.6 |
| L3M (13) | 202644..202644, 94, open | 95 | 94 (+1%) | 93 (+3%) | 99 / 95 / 92 | 78 / 75 (+4%) / 71 (+9%) | 194 / 192 / 191 * | 0.16 / 0.16 / 0.16 | 14.9 / 14.7 / 14.7 (-0.2, -0.2; 8.0) | 45 / 39 / 41 | -95 / -94 / -93 | -0.2 / -0.2 |
| L6M (27) | 202629..202637, 151, recovered | 163 | 151 (+7%) | 148 (+9%) | 162 / 140 / 137 | 95 / 94 (+1%) / 93 (+3%) | 109 / 99 / 103 | 0.23 / 0.24 / 0.23 | 36.7 / 36.7 / 34.0 (+0.0, -2.7; 6.8) | 71 / 61 / 64 | -95 / -94 / -93 | +0.0 / -2.7 |
| HOLD (52) | 202629..202637, 151, recovered | 163 | 151 (+7%) | 148 (+9%) | 162 / 140 / 139 | 150 / 129 (+14%) / 137 (+9%) | -579 / -575 / -538 | 0.19 / 0.20 / 0.19 | 31.0 / 30.4 / 28.8 (-0.6, -2.2; 4.5) | 61 / 54 / 57 | -81 / -74 / -77 | -0.4 / -0.0 |
| MID (12) | 202607..202608, 44, recovered | 59 | 44 (+25%) | 52 (+11%) | 65 / 61 / 59 | 30 / 26 (+15%) / 19 (+36%) | 308 / 288 / 269 * | 0.44 / 0.55 / 0.43 | 25.7 / 24.0 / 22.5 (-1.7, -3.2; 9.7) | 19 / 17 / 19 | -38 / -31 / -39 | -1.7 / -3.2 |
| PRE (75) | 202435..202437, 166, recovered | 178 | 166 (+7%) | 157 (+12%) | 174 / 167 / 156 | 178 / 165 (+8%) / 156 (+13%) | -872 / -790 / -731 | 0.09 / 0.10 / 0.12 | 16.9 / 17.3 / 19.3 (+0.4, +2.5; 2.9) | 55 / 51 / 46 | -82 / -79 / -73 | +2.2 / +6.2 |
| X' (44) | 202342..202347, 92, recovered | 80 | 92 (-16%) | 107 (-34%) | 81 / 92 / 104 | 80 / 66 (+17%) / 50 (+37%) | -472 / -447 / -412 | 0.07 / 0.05 / 0.06 | 5.3 / 4.8 / 6.0 (-0.5, +0.7; 3.6) | 34 / 37 / 37 | -56 / -48 / -49 | -0.2 / +1.6 |

## 2. Real engine equal-risk (lot search, ALL worst-20 matched to NONE)
| window | NONE mean / maxDD / worst-20 / Calmar | HALF (c=1) mean / maxDD | HALF at c* = 1.123 (verified engine run): mean / maxDD / worst-20 / Calmar, equal-risk mean d vs NONE | SKIP (c=1) mean / maxDD | SKIP at c* = 1.150 (verified engine run): mean / maxDD / worst-20 / Calmar, equal-risk mean d vs NONE |
|---|---|---|---|---|---|
| L1M | 17.1 / 95 / 86 / 0.18 | 13.1 / 94 | 13.6 / 105 / 68 / 0.13, -3.5 (MDE 12.1) | 12.6 / 93 | 15.0 / 96 / 75 / 0.16, -2.1 (MDE 10.0) |
| L2M | 24.3 / 95 / 219 / 0.26 | 21.9 / 94 | 24.5 / 105 / 221 / 0.23, +0.2 (MDE 9.2) | 21.8 / 93 | 26.3 / 96 / 237 / 0.27, +1.9 (MDE 8.7) |
| L3M | 14.9 / 95 / 194 / 0.16 | 14.7 / 94 | 17.2 / 105 / 224 / 0.16, +2.3 (MDE 6.9) | 14.7 / 93 | 17.7 / 96 / 230 / 0.18, +2.8 (MDE 9.9) |
| L6M | 36.7 / 163 / 109 / 0.23 | 36.7 / 151 | 41.2 / 133 / 129 / 0.31, +4.5 (MDE 8.6) | 34.0 / 148 | 40.2 / 141 / 165 / 0.28, +3.5 (MDE 12.6) |
| HOLD | 31.0 / 163 / -579 / 0.19 | 30.4 / 151 | 33.6 / 133 / -576 / 0.25, +2.5 (MDE 5.6) | 28.8 / 148 | 33.0 / 141 / -533 / 0.23, +1.9 (MDE 8.8) |
| MID | 25.7 / 59 / 308 / 0.44 | 24.0 / 44 | 26.1 / 40 / 313 / 0.65, +0.4 (MDE 9.7) | 22.5 / 52 | 21.9 / 52 / 263 / 0.42, -3.7 (MDE 20.3) |
| PRE | 16.9 / 178 / -872 / 0.09 | 17.3 / 166 | 18.7 / 177 / -859 / 0.11, +1.8 (MDE 3.1) | 19.3 / 157 | 19.9 / 173 / -820 / 0.11, +3.1 (MDE 5.4) |
| X' | 5.3 / 80 / -472 / 0.07 | 4.8 / 92 | 5.9 / 76 / -457 / 0.08, +0.6 (MDE 3.6) | 6.0 / 107 | 6.8 / 89 / -439 / 0.08, +1.5 (MDE 6.2) |
| ALL | 18.8 / 178 / -1218 / 0.11 | 18.6 / 166 | 20.5 / 177 / -1188 / 0.12, +1.7 (MDE 2.2) | 19.4 / 157 | 21.3 / 173 / -1187 / 0.12, +2.4 (MDE 3.7) |

## 3. Against the Z3 PA9 noise band (DS3_ZONES_3_NOISE_V13T_FINAL.md)
| window | Z3 PA9 band (flip 2% / 5%) | HALF: single cut / phase-avg cut | beyond band? | SKIP: single / phase-avg | beyond band? | HALF with carrying episode dropped | SKIP with carrying episode dropped |
|---|---|---|---|---|---|---|---|
| L3M | 19.0% / 16.5% | +1% / +4% | no | +3% / +8% | no | +4% | +9% |
| L6M | 18.8% / 21.9% | +7% / +13% | no | +9% / +15% | no | +1% | +3% |
| HOLD | 18.2% / 20.5% | +7% / +13% | no | +9% / +14% | no | +14% | +9% |
| MID | 21.2% / 32.2% | +25% / +7% | no | +11% / +9% | no | +15% | +36% |
| PRE | 7.8% / 9.9% | +7% / +4% | no | +12% / +10% | YES | +8% | +13% |
| X' | 14.5% / 18.2% | -16% / -14% | no | -34% / -28% | no | +17% | +37% |

## 4. Whole-layer placebos on V13T_LIVE (100 draws per kind)
| context | maxDD cut PRE / L6M / HOLD / MID / X' | placebo rank A / B / C: PRE | L6M | HOLD | MID | X' (n) |
|---|---|---|---|---|---|---|
| HALF layer vs zone off | +7% / +7% / +7% / +25% / -16% | 0.267/0.416/0.376 | 0.485/0.525/0.485 | 0.465/0.475/0.446 | 0.228/0.317/0.337 | 0.911/0.851/0.950 (100/100/100) |
| SKIP layer vs zone off | +12% / +9% / +9% / +11% / -34% | 0.119/0.228/0.238 | 0.545/0.604/0.426 | 0.426/0.446/0.356 | 0.505/0.416/0.545 | 0.792/0.752/0.842 (100/100/100) |

## 5. Per line: HALF vs SKIP vs left out
| line | action | maxDD cut vs the line left out: PRE / L6M / HOLD / MID / X' | same, carrying episode dropped: PRE / L6M | phase-avg maxDD $k PRE / L6M | mean d vs left-out $k/wk (MDE) PRE / L6M | worst-20 PRE b>a |
|---|---|---|---|---|---|---|
| kijun1h | HALF | +4% / -12% / -12% / -2% / -4% | +0% / +1% | 167 / 140 | +0.3 (1.1) / -0.6 (2.3) | -812 > -790 |
| kijun1h | SKIP | +3% / -1% / -1% / -20% / -1% | -1% / +3% | 158 / 128 | +1.1 (2.3) / -1.0 (2.9) | -812 > -762 |
| PDmid | HALF | +0% / +4% / +4% / +0% / -38% | -0% / +0% | 167 / 140 | -0.0 (0.4) / -0.2 (1.5) | -793 > -790 |
| PDmid | SKIP | -3% / +9% / +9% / +6% / -61% | -4% / -3% | 165 / 135 | -0.4 (1.2) / -1.9 (5.7) | -793 > -791 |
| CRT4h | HALF | +1% / +7% / +7% / +35% / -22% | +0% / -3% | 167 / 140 | +0.5 (1.0) / -0.0 (1.6) | -786 > -790 |
| CRT4h | SKIP | -2% / +6% / +6% / -0% / -6% | -4% / -5% | 165 / 141 | +1.4 (1.9) / +0.0 (3.2) | -786 > -795 |
| KCup4h | HALF | +2% / +3% / +3% / +0% / -4% | +3% / +0% | 167 / 140 | +0.4 (1.5) / +0.2 (0.5) | -802 > -790 |
| KCup4h | SKIP | +2% / +5% / +5% / +0% / -11% | +4% / -0% | 164 / 137 | +0.3 (2.1) / +0.4 (1.3) | -802 > -780 |
| camH3 | HALF | +2% / +1% / +1% / -21% / -5% | +3% / +0% | 167 / 140 | -0.1 (1.0) / -0.2 (1.0) | -810 > -790 |
| camH3 | SKIP | +5% / -1% / -1% / -27% / -13% | +13% / +0% | 163 / 145 | +0.4 (2.4) / -0.4 (2.2) | -810 > -758 |
| OTE705 | HALF | -5% / +3% / +3% / -21% / +2% | -4% / +2% | 167 / 140 | +0.2 (1.0) / +0.1 (2.3) | -777 > -790 |
| OTE705 | SKIP | -7% / -3% / -3% / -28% / -4% | -7% / +2% | 165 / 149 | +0.5 (2.2) / +0.3 (3.6) | -777 > -749 |
| OTE79 | HALF | +0% / +2% / +2% / -12% / +4% | +1% / +1% | 167 / 140 | -0.1 (0.9) / +2.1 (5.2) | -776 > -790 |
| OTE79 | SKIP | -2% / -9% / -9% / -17% / -1% | +1% / +4% | 171 / 155 | +0.4 (2.1) / +1.4 (4.8) | -776 > -767 |
| OTE62 | HALF D20 | +1% / -18% / -18% / +15% / +1% | +1% / +8% | 164 / 165 | -0.3 (0.8) / -1.0 (2.5) | -792 > -784 |
| OTE62 | SKIP D20 | +1% / -26% / -26% / +16% / +16% | +4% / -4% | 167 / 176 | -0.5 (2.4) / -1.9 (4.7) | -792 > -806 |

## 6. SKIP instead of HALF per line (verdict rule)
| line | SKIP - HALF maxDD cut (pp), carrying episode dropped: PRE / L6M | not dropped: PRE / L6M / HOLD / MID / X' | mean d SKIP-HALF $k/wk (MDE) PRE / L6M | random-row skip placebo (same row count skipped instead; share of draws with at least this gain A / B (n)): PRE / L6M | worth SKIP? (rule: both PRE and L6M > +3 pp with the episode dropped, mean not below -0.5 MDE, placebo rank <= 0.10) |
|---|---|---|---|---|---|
| kijun1h | -1.4 / +1.9 | -0.5 / +9.5 / +9.5 / -17.3 / +2.2 | +0.5 (1.2) / -1.3 (2.5) | A - / - ; B - / - (0/0) | no |
| PDmid | -4.3 / -3.2 | -3.3 / +4.7 / +4.7 / +6.0 / -16.2 | -0.6 (0.9) / -3.2 (7.0) | A - / - ; B - / - (0/0) | no |
| CRT4h | -4.0 / -2.2 | -3.1 / -0.3 / -1.2 / -53.2 / +13.1 | +1.2 (1.6) / +0.1 (3.1) | A - / - ; B - / - (0/0) | no |
| KCup4h | +1.3 / -0.1 | +0.4 / +2.2 / +2.2 / +0.0 / -6.6 | -0.3 (1.6) / +0.0 (1.4) | A - / - ; B - / - (0/0) | no |
| camH3 | +10.1 / +0.0 | +2.4 / -1.7 / -1.7 / -4.8 / -7.3 | +0.3 (1.9) / +0.2 (1.7) | A - / - ; B - / - (0/0) | no |
| OTE705 | -2.7 / +0.1 | -1.8 / -6.3 / -6.3 / -5.8 / -6.2 | -0.0 (2.0) / +1.2 (3.1) | A - / - ; B - / - (0/0) | no |
| OTE79 | -0.5 / +2.7 | -2.2 / -11.5 / -11.5 / -4.6 / -5.5 | +0.2 (1.5) / -0.8 (2.6) | A - / - ; B - / - (0/0) | no |
| OTE62 | +2.6 / -12.7 | -0.2 / -6.8 / -6.8 / +1.5 / +15.0 | -0.1 (2.2) / -0.9 (4.9) | A - / - ; B - / - (0/0) | no |

## 7. Per book (K7 P7 U7 H7 M7 A6): maxDD change vs the line left out
| line | action | by book: maxDD change vs the line left out, PRE $k (K7 / P7 / U7 / H7 / M7 / A6) | L6M $k | L6M with the carrying episode (ISO 202629-202639) dropped $k | HOLD $k |
|---|---|---|---|---|---|
| kijun1h | HALF | -1 / -1 / -1 / +4 / +0 / +3 | +0 / +0 / -1 / -0 / +8 / +0 | -1 / +0 / -1 / -1 / +1 / +0 | +0 / +0 / -1 / -0 / +9 / +0 |
| kijun1h | SKIP | +1 / -0 / +1 / +4 / +0 / +0 | -8 / +0 / -1 / +1 / +11 / -3 | -2 / +0 / -1 / -1 / +4 / -3 | -8 / +0 / -1 / +1 / +15 / +0 |
| PDmid | HALF | +0 / +0 / +0 / -2 / -1 / +0 | -1 / +0 / +0 / +0 / +0 / -0 | +0 / +0 / +0 / +0 / +0 / +1 | -1 / +0 / +0 / +0 / +0 / +0 |
| PDmid | SKIP | +5 / +5 / +4 / -6 / -1 / +2 | +2 / +0 / +0 / -1 / -0 / -3 | +0 / +0 / +0 / +0 / +3 / -2 | +2 / +0 / +0 / -1 / -1 / +0 |
| CRT4h | HALF | -4 / -1 / -2 / -1 / +0 / +0 | -5 / -1 / +0 / -0 / +0 / -3 | +0 / +0 / +0 / +2 / +0 / +0 | -5 / -23 / +0 / -0 / -2 / -2 |
| CRT4h | SKIP | +2 / +1 / -1 / -4 / -2 / +0 | -3 / -2 / +0 / -1 / -4 / +0 | -1 / +0 / +0 / +6 / -4 / +0 | -3 / +4 / +0 / -1 / -11 / +0 |
| KCup4h | HALF | +0 / -13 / -1 / -0 / -1 / -2 | +0 / +0 / +0 / +0 / +0 / +0 | +0 / +0 / +0 / +0 / +0 / +0 | +0 / +0 / +0 / +0 / +0 / +0 |
| KCup4h | SKIP | +0 / +4 / -0 / +0 / -3 / -2 | +0 / +0 / +0 / +0 / -1 / +0 | +0 / +0 / +0 / +0 / -1 / +2 | +0 / +0 / +0 / +0 / +1 / +0 |
| camH3 | HALF | +0 / -4 / +0 / +1 / +1 / -1 | +1 / +2 / +0 / +2 / +1 / +1 | +0 / +0 / +0 / +0 / +2 / +1 | +1 / +0 / +0 / +2 / +1 / +1 |
| camH3 | SKIP | +15 / -15 / +0 / -3 / -3 / -3 | -3 / +5 / +0 / +7 / +2 / +0 | +0 / +0 / +0 / +0 / +6 / +0 | -3 / +0 / +0 / +7 / +4 / +1 |
| OTE705 | HALF | -2 / +5 / -1 / -1 / -1 / +0 | -7 / -2 / -1 / +2 / -1 / -1 | -1 / +0 / -1 / +0 / -1 / +0 | -7 / +8 / -1 / +2 / -1 / -1 |
| OTE705 | SKIP | +1 / +23 / -3 / -3 / -5 / +0 | -12 / +9 / -1 / +5 / -4 / -1 | +0 / +0 / -1 / -4 / -2 / -1 | -12 / +15 / -1 / +5 / -6 / -1 |
| OTE79 | HALF | +0 / -1 / -2 / -7 / -1 / +0 | +0 / -2 / +0 / -2 / +1 / +1 | +0 / -1 / +0 / +0 / +1 / +1 | +0 / +0 / +0 / -2 / +0 / -1 |
| OTE79 | SKIP | +2 / +5 / +1 / -11 / +4 / +0 | -7 / -5 / +0 / +12 / +3 / +6 | -1 / -3 / +0 / +0 / +2 / +3 | -7 / +0 / +0 / +12 / +2 / +3 |
| OTE62 | HALF | -1 / -1 / -1 / +4 / +0 / +0 | +5 / +4 / +2 / +0 / -6 / -4 | -6 / +2 / +2 / +0 / -6 / +1 | +4 / -3 / +2 / +0 / -5 / -2 |
| OTE62 | SKIP | -1 / -6 / +5 / +3 / -1 / +0 | +3 / +9 / +4 / +1 / -14 / +2 | +3 / +5 / +4 / +0 / -8 / +6 | +3 / -3 / +4 / +1 / -11 / +2 |

Carrying episodes on V13T_LIVE (largest drawdown episode of the shipped HALF layer, ISO peak..trough, depth $k): L1M 202644..202644 94; L2M 202644..202644 94; L3M 202644..202644 94; L6M 202629..202637 151; HOLD 202629..202637 151; MID 202607..202608 44; PRE 202435..202437 166; X' 202342..202347 92
Books in the L6M carrying episode (HALF layer, $k P&L inside the episode weeks): K7 -33, P7 +15, U7 +52, H7 -2, M7 -20, A6 +5

## 8. D sensitivity
| line | action | PRE cut vs left out at D = 10 / 15 / 20 / 25 / 30 | L6M cut at D = 10 / 15 / 20 / 25 / 30 | verdict |
|---|---|---|---|---|
| kijun1h | HALF | +0% / +4% / +4% / +4% / +7% | +1% / -11% / -12% / -13% / -20% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| kijun1h | SKIP | -2% / +5% / +3% / +0% / +10% | +4% / -3% / -1% / -8% / -16% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| PDmid | HALF | +0% / +0% / +0% / +0% / +4% | +3% / +4% / +4% / +4% / +2% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| PDmid | SKIP | -1% / -1% / -3% / -2% / +10% | +3% / +8% / +9% / +5% / +1% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| CRT4h | HALF | +0% / +1% / +1% / +1% / -1% | +2% / +9% / +7% / +8% / +5% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| CRT4h | SKIP | -0% / +0% / -2% / -2% / +0% | +1% / +10% / +6% / +15% / +14% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| KCup4h | HALF | +1% / +1% / +2% / +2% / +2% | +3% / +3% / +3% / +2% / +5% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| KCup4h | SKIP | +0% / +2% / +2% / +2% / +2% | +6% / +6% / +5% / +3% / +9% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| camH3 | HALF | +0% / +1% / +2% / +2% / +1% | +1% / +2% / +1% / +7% / +6% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| camH3 | SKIP | +0% / +1% / +5% / +5% / +3% | +1% / +4% / -1% / +5% / -8% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE705 | HALF | -1% / -5% / -5% / -11% / -11% | -2% / -5% / +3% / -1% / -11% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE705 | SKIP | -6% / -5% / -7% / -8% / -9% | -6% / -7% / -3% / -12% / -27% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE79 | HALF | -1% / -1% / +0% / -1% / -1% | -1% / -1% / +2% / +0% / -1% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE79 | SKIP | -7% / -5% / -2% / -4% / +0% | -0% / -5% / -9% / -10% / -13% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE62 | HALF | +0% / +1% / +1% / -5% / -5% | -4% / -11% / -18% / -18% / -19% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |
| OTE62 | SKIP | +1% / +0% / +1% / -6% / -9% | -7% / -15% / -26% / -34% / -26% | FRAGILE (PRE+L6M both >= 5% at 0 of 5 D) |

## 9. One-at-a-time
| line | alone vs zone off: HALF cut PRE / L6M / HOLD / MID / X' | SKIP cut PRE / L6M / HOLD / MID / X' |
|---|---|---|
| kijun1h | -0% / -8% / -8% / +8% / +3% | -2% / -2% / -2% / -2% / -5% |
| PDmid | +3% / +8% / +8% / +2% / -3% | -3% / +16% / +11% / +7% / -17% |
| CRT4h | -4% / +13% / +13% / +49% / +1% | -12% / +8% / +8% / +4% / +4% |
| KCup4h | +3% / +1% / +1% / +0% / +0% | +3% / +1% / +1% / +0% / +9% |
| camH3 | +8% / -3% / -3% / -9% / +4% | +12% / -14% / -14% / -15% / +4% |
| OTE705 | -6% / -2% / -2% / -5% / +12% | -10% / -9% / -9% / -7% / +13% |
| OTE79 | -3% / -0% / -0% / -3% / -4% | -4% / -13% / -13% / -10% / -3% |
| OTE62 | +4% / -25% / -25% / +10% / +12% | +1% / -34% / -34% / +13% / +14% |

## 10. Plain label per line
| line | PA PRE cut (episode dropped) | PA L6M cut (episode dropped) | D with PRE and L6M cut >= 5% (of 5) | label |
|---|---|---|---|---|
| kijun1h | +4% (+0%) | -7% (+1%) | 0 | DEAD |
| PDmid | -0% (-0%) | +4% (+0%) | 0 | DEAD |
| CRT4h | +1% (+0%) | +7% (-3%) | 0 | FRAGILE |
| KCup4h | +2% (+3%) | +4% (+0%) | 0 | DEAD |
| camH3 | +2% (+3%) | +1% (+0%) | 0 | DEAD |
| OTE705 | -8% (-4%) | +3% (+2%) | 0 | DEAD |
| OTE79 | -2% (+1%) | +4% (+1%) | 0 | DEAD |
| OTE62 | +1% (+1%) | -18% (+8%) | 0 | DEAD |
