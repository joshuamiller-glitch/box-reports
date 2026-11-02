# DS3_V13T2_RESCORE - V13T2 (= V13T_LIVE + kfix: cuts AND injected exits re-based to the split-kernel exit) re-score of the exit and zone verdicts (BASE-4, 2026-11-02T18:39Z)

Frames: **T** = V13T_LIVE as published (lock none, xcost 0.80, stop 2.45, lines empty, ER ladder single rounding, old lock scaling); **T2** = the same + the table-vs-kernel exit reference fix (EXIT_API.md "V13T2" block: worked rows tie to an independent calculation). Same scorer as the audit (weekly-cumulative maxDD / mean of the 11-book total, windows L6M HOLD MID PRE X'). Every number below is computed in the same process for both frames. Band constants for the zone leads = V13T PA9 tl_band_final.csv (2% / 5% flip), NOT re-estimated on T2 (stated). Placebo ranks (100 draws) are not re-run: verdict columns are the band gate and no-harm rules of DS3_ZONES_3_SURVIVORS_V13T.md. Table only, no PASS claim.

## 1. The base itself (lock none; whole history T $3,482k -> T2 $3,461k)
| window | V13T mean / maxDD / worst-20 | V13T2 mean / maxDD / worst-20 | mean change | maxDD change |
|---|---|---|---|---|
| L6M | 36.7k / 150.7k / 99k | 35.9k / 146.7k / 131k | -0.84k | -4.0k |
| HOLD | 30.4k / 150.7k / -575k | 30.0k / 146.7k / -543k | -0.43k | -4.0k |
| MID | 24.0k / 43.7k / -70k | 22.6k / 43.9k / -71k | -1.39k | +0.2k |
| PRE | 17.3k / 166.2k / -790k | 17.0k / 173.5k / -821k | -0.28k | +7.4k |
| X' | 4.8k / 92.5k / -447k | 5.4k / 83.3k / -402k | +0.56k | -9.2k |

## 2. T-EXIT-N top cells (S4b audit list, 14 cells + their independent kernels)
maxDD cut vs the frame's own base (L6M / HOLD / MID / PRE / X', + = shallower), mean change vs the frame's base ($k/wk, L6M / PRE). Label: CUT = L6M cut >= 10% and PRE cut >= 10%; FREE = mean change >= 0 in both windows, PAID = below.
| family | cell | V13T cut L6M/HOLD/MID/PRE/X' | V13T mean chg | V13T2 cut L6M/HOLD/MID/PRE/X' | V13T2 mean chg | V13T label | V13T2 label | verdict |
|---|---|---|---|---|---|---|---|---|
| E1 | B flip SWP arm15 | +29% / +19% / -74% / +31% / -20% | -15.9 / -7.2 | +38% / +9% / -105% / +33% / -30% | -16.3 / -7.6 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| E1 | B flip K2 arm15 | +26% / +26% / +6% / +22% / -26% | -11.1 / -8.3 | +29% / +19% / -32% / +15% / -30% | -11.4 / -8.9 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| E3 | R3|pull|a0.5|thr1.0 | +39% / +26% / -68% / +9% / +22% | -10.3 / -9.6 | +37% / +26% / -75% / +7% / +20% | -12.4 / -10.7 | L6M-only cut, paid | L6M-only cut, paid | same |
| E3 | R3|pull|a0.5|thr1.25 | +40% / +23% / -59% / +5% / +17% | -8.4 / -9.3 | +35% / +22% / -69% / +18% / +22% | -10.6 / -9.8 | L6M-only cut, paid | CUT L6M+PRE, PAID (mean below base) | CHANGED |
| E3 | R3|delta|a0.5|T30 | +44% / -4% / -106% / -0% / +25% | -7.3 / -7.0 | +48% / +6% / -75% / +15% / +27% | -7.4 / -7.9 | L6M-only cut, paid | CUT L6M+PRE, PAID (mean below base) | CHANGED |
| E3 | R3v2|G14ice|a0.3|thr200 | +35% / -9% / -58% / +7% / -35% | +0.9 / -9.3 | +27% / +3% / -54% / +13% / -30% | +0.3 / -8.9 | L6M-only cut, free | CUT L6M+PRE, PAID (mean below base) | CHANGED |
| E3 | R3v2|G10delta|a0.3|T20 | +65% / -15% / -172% / -24% / -100% | -3.9 / -10.3 | +47% / -5% / -139% / -11% / -84% | -5.6 / -10.7 | L6M-only cut, paid | L6M-only cut, paid | same |
| E3 | R3v2|G14ice|a0.7|thr50 | +27% / +23% / +14% / +12% / +25% | -6.9 / -4.6 | +24% / +24% / -3% / +32% / +44% | -7.4 / -4.8 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| E3 | R3v2|G15sweep|a0.7 | +25% / +25% / -10% / +13% / +26% | -7.0 / -5.3 | +40% / +37% / +19% / +32% / +44% | -7.8 / -5.7 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| E3 | R3|delta|a0.3|T100 | +25% / -14% / -63% / +11% / -62% | -1.2 / -5.8 | +22% / -7% / -41% / +24% / -29% | -3.5 / -6.7 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| E4 | RT100_BTswing_ALL | +30% / +18% / -1% / +0% / +18% | +3.7 / +0.3 | +31% / +18% / -1% / +4% / +19% | +3.9 / +0.0 | L6M-only cut, free | L6M-only cut, free | same |
| E4 | RT70_BTswing_ALL | +27% / +20% / +4% / +2% / +23% | +3.8 / -0.2 | +28% / +20% / +4% / +5% / +21% | +4.0 / -0.3 | L6M-only cut, free | L6M-only cut, free | same |
| E2 | K7TR_P0.7_30_G1 | +5% / +5% / -21% / -3% / -1% | -1.5 / -0.1 | +2% / +2% / -20% / +5% / +2% | -1.2 / -0.4 | no L6M cut | no L6M cut | same |
| E3ind | IND ice a0.3 thr200 (own gate kernel) | +35% / -9% / -58% / +7% / -35% | +0.9 / -9.3 | +27% / +3% / -54% / +13% / -30% | +0.3 / -8.9 | L6M-only cut, free | CUT L6M+PRE, PAID (mean below base) | CHANGED |
| E3ind | IND ice a0.7 thr50 (own gate kernel) | +27% / +23% / +14% / +12% / +25% | -6.9 / -4.6 | +24% / +24% / -3% / +32% / +44% | -7.4 / -4.8 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |

## 3. Shipped TH-L2 cut vs no cut (cut = maxDD of the NO-CUT run minus the SHIPPED run, as % of no-cut; + = the shipped cut helps)
| frame | L6M | HOLD | MID | PRE | X' | mean change with the cut L6M / PRE $k/wk |
|---|---|---|---|---|---|---|
| T | +23.8% | +23.8% | +74.4% | +41.2% | +25.9% | +11.8 / +1.0 |
| T2 | +25.9% | +25.9% | +74.3% | +38.6% | +33.3% | +11.0 / +0.8 |

## 4. Zone leads on V13T vs V13T2 (PA over 9 lock-reset phases, cut vs the SHIPPED layer of the same frame and phase)
Band constants (PA9, % cut): 2% flip L6M 18.8, HOLD 18.2, MID 21.2, PRE 7.8, X' 14.5; 5% flip L6M 21.9, HOLD 20.5, MID 32.2, PRE 9.9, X' 18.2. Gate = PA L6M above band and (PRE or X') above band; no-harm = PRE, MID, X' not below minus band.
| lead | V13T PA cut L6M/HOLD/MID/PRE/X' | V13T mean chg L6M / PRE | V13T2 PA cut L6M/HOLD/MID/PRE/X' | V13T2 mean chg | V13T gate | V13T2 gate | verdict |
|---|---|---|---|---|---|---|---|
| CRT4h60 fw2 any | +24% / +23% / +3% / +0% / -1% | +1.7 / +0.3 | +24% / +20% / +1% / -1% / -3% | +1.5 / +0.4 | band2 fail/5 fail, no-harm ok | band2 fail/5 fail, no-harm ok | same |
| SWG f5L 3m D20 half | +28% / +26% / -12% / +9% / +18% | -2.8 / -4.2 | +27% / +27% / -19% / +12% / +23% | -1.1 / -3.7 | band2 PASS/5 fail, no-harm ok | band2 PASS/5 PASS, no-harm ok | CHANGED |
| FIB ret62 15m D20 skip | +21% / +21% / +19% / +2% / +29% | +2.7 / +1.5 | +20% / +20% / +2% / +6% / +24% | +2.6 / +1.5 | band2 PASS/5 fail, no-harm ok | band2 PASS/5 fail, no-harm ok | same |
| BT swing flip D40 skip | +14% / +13% / -9% / +7% / +8% | +4.3 / +1.0 | +11% / +11% / -26% / +10% / +1% | +4.5 / +0.9 | band2 fail/5 fail, no-harm ok | band2 fail/5 fail, NO-HARM FAIL | CHANGED |

## 5. Shipped zone layer vs none (PA9 cut of the shipped layer relative to the layer-off run; + = the layer helps)
| frame | L6M | HOLD | MID | PRE | X' | mean change with the layer L6M / PRE $k/wk |
|---|---|---|---|---|---|---|
| T | -2.7% | -2.7% | -15.1% | +11.2% | -1.3% | -0.5 / +0.2 |
| T2 | +0.4% | +0.4% | -8.9% | +10.1% | +1.6% | -1.0 / +0.4 |

## 6. Which verdicts change (6 of 19 rows change their label)
| item | V13T label | V13T2 label | verdict |
|---|---|---|---|
| B flip SWP arm15 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| B flip K2 arm15 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| R3|pull|a0.5|thr1.0 | L6M-only cut, paid | L6M-only cut, paid | same |
| R3|pull|a0.5|thr1.25 | L6M-only cut, paid | CUT L6M+PRE, PAID (mean below base) | CHANGED |
| R3|delta|a0.5|T30 | L6M-only cut, paid | CUT L6M+PRE, PAID (mean below base) | CHANGED |
| R3v2|G14ice|a0.3|thr200 | L6M-only cut, free | CUT L6M+PRE, PAID (mean below base) | CHANGED |
| R3v2|G10delta|a0.3|T20 | L6M-only cut, paid | L6M-only cut, paid | same |
| R3v2|G14ice|a0.7|thr50 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| R3v2|G15sweep|a0.7 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| R3|delta|a0.3|T100 | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| RT100_BTswing_ALL | L6M-only cut, free | L6M-only cut, free | same |
| RT70_BTswing_ALL | L6M-only cut, free | L6M-only cut, free | same |
| K7TR_P0.7_30_G1 | no L6M cut | no L6M cut | same |
| IND ice a0.3 thr200 (own gate kernel) | L6M-only cut, free | CUT L6M+PRE, PAID (mean below base) | CHANGED |
| IND ice a0.7 thr50 (own gate kernel) | CUT L6M+PRE, PAID (mean below base) | CUT L6M+PRE, PAID (mean below base) | same |
| CRT4h60 fw2 any | band2 fail/5 fail, no-harm ok | band2 fail/5 fail, no-harm ok | same |
| SWG f5L 3m D20 half | band2 PASS/5 fail, no-harm ok | band2 PASS/5 PASS, no-harm ok | CHANGED |
| FIB ret62 15m D20 skip | band2 PASS/5 fail, no-harm ok | band2 PASS/5 fail, no-harm ok | same |
| BT swing flip D40 skip | band2 fail/5 fail, no-harm ok | band2 fail/5 fail, NO-HARM FAIL | CHANGED |

## 7. Reading (BASE-4; table only, no PASS claim)
- The fix is small on the base (whole history -$21k, F9/L6M mean -0.8k/wk, L6M maxDD -4k, PRE maxDD +7k, X' maxDD -9k) and does not move the story of any family: no exit cell is a free lead in either frame; the only cells with a mean >= base are the E4 BT re-target cells (L6M-only cuts, PRE ~0) in BOTH frames.
- The 4 exit-cell label changes are threshold crossings on cells that were already PAID (a PRE cut moving from 5-9% to 13-18% across the 10% line): same cost (mean -7 to -9k/wk in PRE), no new free cut. G14ice a0.3 thr200 (the one cell with L6M mean >= base on V13T) now has PRE mean -8.9k/wk (V13T -9.3k) and L6M mean +0.3k (V13T +0.9k): PAID in PRE on both frames.
- Shipped TH-L2 cut vs no cut: helps in every window in both frames (+24% / +74% / +41% / +26% on V13T, +26% / +74% / +39% / +33% on V13T2), and raises the L6M mean by about +11k/wk (PRE +1k/wk).
- Zone leads: SWG f5L 3m D20 half passes the 5%-flip gate on V13T2 and not on V13T, but by a hair (V13T X' cut 18% vs band 18.2%): not a verdict change in substance, and no placebo (rank >= 0.95) was re-run. BT swing flip D40 skip fails no-harm on V13T2 (MID PA cut -26% vs band 21.2%); it already failed the L6M gate. CRT4h 60 fw2 and FIB ret62 15m D20 skip: unchanged (CRT fails both gates; FIB passes the 2% gate only). Shipped layer vs none: still no layer effect in L6M/HOLD/X' (-3% .. +2%), PRE +10..11%, MID -9..-15%.
- FIB ret62: this table scores the 11-book total like the Z3 survivor page; the S4b placebo page (core-6 books, .161 / .013 / .341) is a different scorer: do not compare the two.
- Limitations: band constants and the 100-draw placebos are NOT re-estimated on V13T2; OTE-62 rows keep the table convention; the carrying-week drops are not applied here.
