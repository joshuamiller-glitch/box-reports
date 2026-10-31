# DS3_L2_UF_LOSS_C7 - L2-UNTIL-FOUND cycle 7, LOSS side: the L2 state of the STOPPED book at its stop second as information for the stack first-stop cut (agent UF-LOSS, 2026-10-31)
Research only. UNTOUCHED (> 2026-02-06) never read. Own masks: Y26 = 20260101..0206 (~5 weeks), L3M = 20251106.., L6M = 20250801.., HOLD = 20250701.., PRE = 20240201..20250630, X' = 20230401..20240131. Prereg `l2vast/ds3/prereg/UF_LOSS_C7_prereg.md` sha256 3e20f88b1b1dd3c1605098b7bf7176057983cd9fbc4e8442df702f3da731e96c (a feature-name typo d6_c_* -> d6_* was corrected before any statistic and logged; original sha 98a32101...). Selection `out/uf/loss7/selection_PRE_X.json` sha256 7f93179251dc2a6079e3c83f5ad35adcc6f9b8a3e1c39ef1fc90064418fdcd6f (PRE+X' only, basis N, logged before the single recent look). dead_lookup over the 168 specs: 0 hits (STACK2 has 202 catalogued cells, none with an L2 condition). Cumulative N = UF_TRIALS.json total at start 2,861,650 (all agents) + 168 = 2,861,818; n_effective 3.5; UF_TRIALS side loss, cycle 7. ONE recent look.
Method: S2 simulator + exact per-book lock engine (6 books ST HM WT KB SM PE, basis N, planned-lot R locks), event = first same-side book stops, action = market cut of 50% of every other open same-side row (S2 'cut P50', latency 0), bases MKT and S73. Condition = a feature of the STOPPED trade at its last book row at or before its stop second (own side = the stopped trade's supporting side; <= 10 s old; causal) against a threshold = 0.33 / 0.5 / 0.67 quantile over the PRE+X' stop events. 14 features x 2 directions x 3 quantiles x 2 bases = 168 cells. Units: stack $/wk at research lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6) AND at LIVE lots (K6=KB 2, P6=PE 7, U6=SM 4, H6=HM 4 Asia / 2 NY-AM shown as HM 4 / HM 2, ST and WT 0; mapping ASSUMED as in FOLLOWUP_BRIEF), per planned lot (pts), per contract of final position (pts), fires per week, and re-entry P&L separate (same trades / re-entry in / re-entry out).

## 1. Page 1 - the answer
1. **Information:** the stopped book's L2 state carries almost no information about the value of cutting the other books. Event-level Spearman IC of the 14 features vs the cut value per lot is <= 0.10 in PRE and X' (n = 1,131 and 556 events; placebo SD 0.02-0.04) and flips sign across windows for most features (table section 4). The two features with a recent relation are the ES book at the stop second (c_es5 IC -0.14 Y26 / -0.10 L3M / -0.04 L6M / -0.02 HOLD / +0.01 PRE / +0.04 X') and its 60-s change (d6_es5 -0.14 / -0.10 / -0.07 / -0.07 / +0.03 / +0.06), plus stopped-book activity (pulled size c_p10 and volume c_vol10, IC about -0.08 to -0.10 in L6M and HOLD, ~0 in PRE and X'): recent only, absent in PRE.
2. **Selection (PRE+X' only) is a null:** 5 of 168 cells have a delta >= 0 vs the same base in both PRE and X' (MKT 2 of 84, S73 3 of 84), all inside their MDE (PRE +0.2k..+1.2k, X' +2.1k..+5.3k per week vs MDE 9k-13k). White RC over the 168 on PRE+X' days p = 0.90 (studentised 0.91), Romano-Wolf survivors 0, PBO 0.44, best-cell DSR 0.16, minimum backtest length for 168 trials 7.3 years.
3. **Recent look (the five carried cells):** two MKT cells - the ES book against the stopped trade at its stop second (c_es5 below its 0.33 quantile = +0.013, ES imbalance sided to the trade; cell 1) and its 60-s decline (d6_es5 below its 0.33 quantile = -0.041; cell 2) - are >= 0 in ALL six windows on N: cell 1 Y26 +29.4k, L3M +20.9k, L6M +15.6k, HOLD +11.7k, PRE +1.2k, X' +2.1k per week at research lots (L6M MDE 16.8k; live lots +4.0k L6M / +2.7k HOLD / +0.0k PRE / +1.2k X' with HM 4 lots); cell 2 +23.0k / +19.3k / +15.2k / +12.6k / +0.5k / +4.4k (live +4.1k L6M). They keep 65-68% of the unconditioned MKT cut's recent gain (L6M +23.0k) with 27% of its fires (3.9-4.0 per week vs 14.7) and **remove its PRE loss** (-8.2k -> +0.5k..+1.2k). Per planned lot +0.81 / +0.79 pts L6M, per contract of final position 3.81 vs 3.21 (rule vs base) in L6M. Random P50 cuts at the same fire rate and time-since-first-entry (100 draws): rank 0.99-1.00 in L3M/L6M/HOLD, 0.90 / 0.86 in PRE. Shuffled feature within day (40 draws): rank 1.00 / 0.95 L6M, 0.95 / 0.95 HOLD, 0.88 / 0.75 PRE. The three S73 cells are weaker (z10 high: L6M +9.2k, shuffled rank 0.88; d6_imb10: negative L6M/HOLD, DEAD; d6_es5 S73: L6M +5.2k, live -0.1k).
4. **Why this is NOT a pass:** (i) the conditions were chosen from 168 on PRE and X' and the RC / Romano-Wolf / DSR on that selection window fail (p 0.90, 0 survivors, DSR 0.16); single-cell L6M p about 0.005 but the cumulative-adjusted p is 1.00; (ii) **73% of the L6M gain is the lock-engine re-entry effect, not the cut itself**: decomposition of cell 1 in L6M: same trades +3.1k, re-entry in +11.2k, re-entry out +1.2k per week; in PRE the same trades are -1.1k and the re-entry +2.2k - the cut changes the day's P&L state and later library signals are admitted, exactly the STACK-2 finding; (iii) time-shifted placebo (feature 60 s before the stop): L6M still +7.3k / +10.5k and HOLD +6.7k / +8.8k but PRE -2.3k / -3.8k: about half of the recent gain does not depend on the stop-second state; (iv) the relation is recent: IC in PRE and X' is 0 +- 0.04, the carried cells were selected because their PRE and X' deltas happen to be >= 0.
5. **Tier: LEAD for the two MKT ES-book cells (CANDIDATE-RECENT: >= 0 in Y26, L6M, HOLD, PRE, X' on N, M and LIVE-cal; placebo ranks >= 0.9 in L6M and HOLD, 0.75-0.90 in PRE; MDE >= the effect; cumulative RC fails); the S73 cells z10 and d6_es5 are weaker CANDIDATE-RECENT (>= 0 in all windows, shuffled-feature rank 0.83-0.93, d6_es5 live L6M -0.1k); the S73 d6_imb10 cell is DEAD (negative L6M and HOLD).** Nothing is PASS and nothing is promoted.

## 2. Carried cells and references (recent first; basis N; stack $/wk research lots, MDE beside; live lots; per planned lot; per contract; fires/wk; re-entry decomposition)
| cell | Y26 | L3M | L6M | HOLD | PRE | X' | L6M MDE | live L6M | rand rank L6M/HOLD/PRE | shuffled-feature rank L6M/HOLD/PRE | single-cell p1 L6M | cumulative Bonferroni p | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| z10_ge_q0.67 S73 | +29,139 | +8,379 | +9,156 | +8,572 | +816 | +5,313 | +21,376 | +5,577 | 0.97/0.99/0.90 | 0.88/0.93/0.75 | 0.12 | 1.00 | CANDIDATE-RECENT |
| d6_es5_lt_q0.33 MKT | +22,994 | +19,321 | +15,186 | +12,591 | +523 | +4,373 | +16,445 | +4,103 | 1.00/0.99/0.86 | 0.95/0.95/0.75 | 0.00 | 1.00 | LEAD (>=0 all windows, placebos pass, RC fails) |
| d6_imb10_ge_q0.67 S73 | +12,240 | -292 | -1,760 | -2,109 | +249 | +4,629 | +13,476 | +275 | 0.33/0.33/0.79 | 0.20/0.15/0.93 | 0.64 | 1.00 | DEAD/NEGATIVE-RECENT |
| d6_es5_lt_q0.33 S73 | +7,883 | +2,737 | +5,182 | +5,073 | +600 | +3,087 | +12,834 | -101 | 0.88/0.89/0.86 | 0.82/0.90/0.75 | 0.13 | 1.00 | CANDIDATE-RECENT |
| c_es5_lt_q0.33 MKT | +29,406 | +20,932 | +15,575 | +11,651 | +1,174 | +2,086 | +16,800 | +3,955 | 0.99/0.98/0.90 | 1.00/0.95/0.88 | 0.00 | 1.00 | LEAD (>=0 all windows, placebos pass, RC fails) |
| REF unconditioned MKT | +69,066 | +35,745 | +22,975 | +19,319 | -8,219 | +676 | +28,540 | +8,589 | - | - | - | - | reference (S2) |
| REF unconditioned S73 | +49,158 | +16,001 | +6,617 | +4,615 | -6,458 | -448 | +26,834 | +2,801 | - | - | - | - | reference (S2) |
| REF Asia-stopped MKT | +36,167 | +17,464 | +20,243 | +16,499 | +916 | +3,706 | +26,285 | +8,209 | - | - | - | - | reference (S2) |
| REF Asia-stopped S73 | +42,829 | +11,874 | +13,191 | +11,391 | +2,005 | +2,818 | +23,119 | +7,470 | - | - | - | - | reference (S2) |

| cell | window | d $/wk research lots (MDE) | d $/wk LIVE lots (HM 4 / HM 2) | per planned lot d pts | per contract rule / base pts | fires/wk | same trades / re-entry in / re-entry out $/wk |
|---|---|---|---|---|---|---|---|
| z10_ge_q0.67 S73 | Y26 | +29,139 (+37,518) | +19,752 / +19,622 | +1.509 | +3.02 / +1.92 | 4.7 | +4,874 / +13,494 / +10,771 |
| z10_ge_q0.67 S73 | L3M | +8,379 (+23,848) | +6,133 / +6,305 | +0.440 | +1.86 / +1.64 | 4.7 | +2,668 / +1,094 / +4,617 |
| z10_ge_q0.67 S73 | L6M | +9,156 (+21,376) | +5,577 / +5,336 | +0.475 | +4.15 / +4.10 | 4.7 | +896 / +5,988 / +2,272 |
| z10_ge_q0.67 S73 | HOLD | +8,572 (+19,175) | +4,291 / +4,293 | +0.449 | +3.59 / +3.49 | 4.7 | +562 / +6,022 / +1,988 |
| z10_ge_q0.67 S73 | PRE | +816 (+9,562) | -1,022 / -1,445 | +0.042 | +3.06 / +3.20 | 4.7 | +2,494 / -997 / -681 |
| z10_ge_q0.67 S73 | X | +5,313 (+12,732) | +4,055 / +3,726 | +0.338 | +1.45 / +1.16 | 4.7 | +570 / +6,143 / -1,400 |
| d6_es5_lt_q0.33 MKT | Y26 | +22,994 (+33,311) | +2,617 / -1,029 | +1.210 | +1.99 / +1.00 | 4.0 | +5,460 / +20,542 / -3,008 |
| d6_es5_lt_q0.33 MKT | L3M | +19,321 (+26,962) | +4,458 / +1,786 | +1.030 | +1.49 / +0.59 | 4.0 | +3,567 / +14,004 / +1,750 |
| d6_es5_lt_q0.33 MKT | L6M | +15,186 (+16,445) | +4,103 / +2,877 | +0.792 | +3.74 / +3.21 | 4.0 | +2,620 / +11,691 / +875 |
| d6_es5_lt_q0.33 MKT | HOLD | +12,591 (+15,521) | +2,407 / +1,532 | +0.663 | +3.00 / +2.54 | 4.0 | +2,751 / +9,075 / +766 |
| d6_es5_lt_q0.33 MKT | PRE | +523 (+11,617) | +702 / +380 | +0.027 | +2.88 / +3.02 | 4.0 | -658 / +2,539 / -1,357 |
| d6_es5_lt_q0.33 MKT | X | +4,373 (+10,670) | +2,240 / +1,755 | +0.280 | +1.27 / +1.03 | 4.0 | +1,323 / +2,678 / +372 |
| d6_imb10_ge_q0.67 S73 | Y26 | +12,240 (+39,602) | +8,634 / +8,863 | +0.634 | +2.36 / +1.92 | 4.2 | -4,674 / +13,809 / +3,104 |
| d6_imb10_ge_q0.67 S73 | L3M | -292 (+22,188) | +2,255 / +2,858 | -0.015 | +1.54 / +1.64 | 4.2 | -3,098 / +3,283 / -477 |
| d6_imb10_ge_q0.67 S73 | L6M | -1,760 (+13,476) | +275 / +901 | -0.091 | +3.86 / +4.10 | 4.2 | -4,221 / +2,715 / -254 |
| d6_imb10_ge_q0.67 S73 | HOLD | -2,109 (+12,791) | -526 / +66 | -0.110 | +3.24 / +3.49 | 4.2 | -3,929 / +2,042 / -222 |
| d6_imb10_ge_q0.67 S73 | PRE | +249 (+9,070) | -1,001 / -759 | +0.013 | +3.07 / +3.20 | 4.2 | -1,112 / +452 / +908 |
| d6_imb10_ge_q0.67 S73 | X | +4,629 (+10,990) | +3,757 / +3,693 | +0.294 | +1.41 / +1.16 | 4.2 | +1,979 / +3,475 / -825 |
| d6_es5_lt_q0.33 S73 | Y26 | +7,883 (+27,456) | -1,899 / -3,070 | +0.408 | +2.17 / +1.92 | 4.0 | +4,298 / +1,390 / +2,195 |
| d6_es5_lt_q0.33 S73 | L3M | +2,737 (+18,505) | -349 / -1,056 | +0.144 | +1.68 / +1.64 | 4.0 | +502 / +3,103 / -867 |
| d6_es5_lt_q0.33 S73 | L6M | +5,182 (+12,834) | -101 / -253 | +0.269 | +4.14 / +4.10 | 4.0 | -56 / +6,049 / -811 |
| d6_es5_lt_q0.33 S73 | HOLD | +5,073 (+12,058) | -954 / -1,068 | +0.266 | +3.55 / +3.49 | 4.0 | +898 / +4,884 / -710 |
| d6_es5_lt_q0.33 S73 | PRE | +600 (+11,779) | +525 / +240 | +0.031 | +3.07 / +3.20 | 4.0 | -2,147 / +4,611 / -1,864 |
| d6_es5_lt_q0.33 S73 | X | +3,087 (+10,467) | +1,552 / +1,259 | +0.196 | +1.32 / +1.16 | 4.0 | +589 / +2,701 / -202 |
| c_es5_lt_q0.33 MKT | Y26 | +29,406 (+46,128) | +8,246 / +6,253 | +1.547 | +2.23 / +1.00 | 3.9 | +5,547 / +23,759 / +100 |
| c_es5_lt_q0.33 MKT | L3M | +20,932 (+31,067) | +6,551 / +4,924 | +1.115 | +1.56 / +0.59 | 3.9 | +3,645 / +15,016 / +2,271 |
| c_es5_lt_q0.33 MKT | L6M | +15,575 (+16,800) | +3,955 / +3,162 | +0.812 | +3.81 / +3.21 | 3.9 | +3,135 / +11,249 / +1,191 |
| c_es5_lt_q0.33 MKT | HOLD | +11,651 (+16,705) | +2,661 / +2,139 | +0.613 | +2.99 / +2.54 | 3.9 | +3,231 / +7,378 / +1,042 |
| c_es5_lt_q0.33 MKT | PRE | +1,174 (+10,386) | +7 / -423 | +0.061 | +2.93 / +3.02 | 3.9 | -1,143 / +2,232 / +85 |
| c_es5_lt_q0.33 MKT | X | +2,086 (+9,329) | +1,223 / +1,009 | +0.134 | +1.14 / +1.03 | 3.9 | -612 / +2,327 / +372 |
| REF unconditioned P50 MKT | Y26 | +69,066 (+53,956) | +27,921 / +23,976 | +3.633 | +3.66 / +1.00 | 14.7 | +16,522 / +44,282 / +8,262 |
| REF unconditioned P50 MKT | L3M | +35,745 (+44,314) | +17,041 / +13,421 | +1.905 | +2.05 / +0.59 | 14.7 | +10,228 / +19,771 / +5,745 |
| REF unconditioned P50 MKT | L6M | +22,975 (+28,540) | +8,589 / +6,430 | +1.198 | +3.75 / +3.21 | 14.7 | +3,355 / +17,437 / +2,183 |
| REF unconditioned P50 MKT | HOLD | +19,319 (+26,070) | +6,027 / +4,461 | +1.017 | +3.03 / +2.54 | 14.7 | +4,137 / +13,057 / +2,125 |
| REF unconditioned P50 MKT | PRE | -8,219 (+15,410) | -3,408 / -3,863 | -0.428 | +2.30 / +3.02 | 14.7 | -4,431 / -2,799 / -988 |
| REF unconditioned P50 MKT | X | +676 (+17,895) | +4,303 / +3,799 | +0.043 | +0.98 / +1.03 | 14.7 | -1,598 / +3,432 / -1,157 |
| REF unconditioned P50 S73 | Y26 | +49,158 (+34,677) | +26,052 / +24,238 | +2.546 | +3.71 / +1.92 | 14.6 | +18,528 / +19,796 / +10,834 |
| REF unconditioned P50 S73 | L3M | +16,001 (+35,134) | +9,738 / +8,533 | +0.841 | +2.07 / +1.64 | 14.6 | +10,542 / +1,713 / +3,746 |
| REF unconditioned P50 S73 | L6M | +6,617 (+26,834) | +2,801 / +2,399 | +0.343 | +3.83 / +4.10 | 14.6 | +244 / +4,419 / +1,954 |
| REF unconditioned P50 S73 | HOLD | +4,615 (+23,987) | +534 / +513 | +0.242 | +3.22 / +3.49 | 14.6 | +77 / +2,828 / +1,710 |
| REF unconditioned P50 S73 | PRE | -6,458 (+15,971) | -4,019 / -3,954 | -0.334 | +2.56 / +3.20 | 14.6 | -5,708 / +626 / -1,376 |
| REF unconditioned P50 S73 | X | -448 (+17,562) | +3,199 / +2,786 | -0.028 | +1.05 / +1.16 | 14.6 | -2,731 / +3,780 / -1,498 |
| REF Asia-stopped P50 MKT | Y26 | +36,167 (+63,634) | +13,191 / +11,771 | +1.902 | +2.33 / +1.00 | 5.2 | +5,877 / +28,231 / +2,059 |
| REF Asia-stopped P50 MKT | L3M | +17,464 (+37,769) | +8,068 / +5,280 | +0.931 | +1.26 / +0.59 | 5.2 | +2,807 / +11,310 / +3,347 |
| REF Asia-stopped P50 MKT | L6M | +20,243 (+26,285) | +8,209 / +5,767 | +1.056 | +3.69 / +3.21 | 5.2 | +3,116 / +16,307 / +820 |
| REF Asia-stopped P50 MKT | HOLD | +16,499 (+23,675) | +6,153 / +4,340 | +0.869 | +2.96 / +2.54 | 5.2 | +4,039 / +11,743 / +717 |
| REF Asia-stopped P50 MKT | PRE | +916 (+13,455) | -498 / -1,200 | +0.048 | +2.79 / +3.02 | 5.2 | +620 / +1,284 / -988 |
| REF Asia-stopped P50 MKT | X | +3,706 (+13,776) | +4,782 / +4,354 | +0.238 | +1.19 / +1.03 | 5.2 | -1,666 / +6,194 / -822 |
| REF Asia-stopped P50 S73 | Y26 | +42,829 (+33,445) | +22,896 / +22,106 | +2.218 | +3.45 / +1.92 | 5.2 | +6,606 / +25,389 / +10,834 |
| REF Asia-stopped P50 S73 | L3M | +11,874 (+29,023) | +9,092 / +7,797 | +0.624 | +1.92 / +1.64 | 5.2 | +3,141 / +5,917 / +2,816 |
| REF Asia-stopped P50 S73 | L6M | +13,191 (+23,119) | +7,470 / +6,193 | +0.685 | +4.20 / +4.10 | 5.2 | +2,523 / +9,308 / +1,360 |
| REF Asia-stopped P50 S73 | HOLD | +11,391 (+20,844) | +5,789 / +4,931 | +0.596 | +3.60 / +3.49 | 5.2 | +3,051 / +7,150 / +1,190 |
| REF Asia-stopped P50 S73 | PRE | +2,005 (+13,894) | -359 / -1,208 | +0.104 | +3.04 / +3.20 | 5.2 | +1,059 / +3,260 / -2,314 |
| REF Asia-stopped P50 S73 | X | +2,818 (+12,858) | +4,445 / +4,114 | +0.179 | +1.27 / +1.16 | 5.2 | -1,765 / +6,175 / -1,593 |

## 3. Robustness of the carried cells (stack d $/wk, research lots)
| carried cell | lag-60 s feature L6M / HOLD / PRE / X' | latency +2 s L6M / HOLD / PRE / X' | basis M L6M / HOLD / PRE / X' | basis LIVE-cal L6M / HOLD / PRE / X' |
|---|---|---|---|---|
| z10_ge_q0.67 S73 | +11,698 / +9,958 / -1,742 / +115 | +9,204 / +8,961 / +1,529 / +5,215 | +2,256 / +2,367 / +1,250 / +4,199 | +7,140 / +6,731 / +2,072 / +4,491 |
| d6_es5_lt_q0.33 MKT | +10,529 / +8,848 / -3,821 / +2,063 | +14,271 / +11,626 / -799 / +4,600 | +7,219 / +4,084 / +3,468 / +4,179 | +12,021 / +9,364 / +1,417 / +4,305 |
| d6_imb10_ge_q0.67 S73 | +6,921 / +5,970 / -1,199 / +402 | -1,831 / -2,149 / +849 / +4,789 | -2,309 / -2,141 / -1,364 / +4,105 | +109 / +561 / +319 / +5,530 |
| d6_es5_lt_q0.33 S73 | +3,377 / +2,604 / -6,796 / +909 | +4,999 / +4,881 / +365 / +3,426 | +2,857 / +2,693 / +92 / +3,252 | +5,683 / +5,728 / -425 / +3,624 |
| c_es5_lt_q0.33 MKT | +7,261 / +6,734 / -2,315 / +2,475 | +15,966 / +12,022 / +115 / +2,294 | +6,728 / +3,715 / +3,263 / +2,294 | +13,459 / +9,327 / +1,497 / +1,579 |
Latency +2 s does not hurt the ES cells (L6M +16.0k / +14.3k); basis M and LIVE-cal are >= 0 in all four windows for both MKT ES cells (LIVE-cal L6M +13.5k / +12.0k); the lag-60 s placebo keeps about half of the recent gain and loses PRE.

## 4. Event-level information map: IC of the stopped book's L2 features vs the value of the cut per lot (MKT, all windows; PRE and X' were the selection data, recent windows read once)
| feat       |    Y26 |    L3M |    L6M |   HOLD |    PRE |      X |
|:-----------|-------:|-------:|-------:|-------:|-------:|-------:|
| c_b12      | -0.1   | -0.053 | -0.068 | -0.096 | -0.061 | -0.091 |
| c_cb5      | -0.114 | -0.074 | -0.047 | -0.077 | -0.076 | -0.076 |
| c_cumbrel  |  0.05  | -0.002 |  0.006 | -0.011 |  0.001 | -0.063 |
| c_delta10  | -0.017 | -0.024 |  0.061 |  0.052 |  0.008 | -0.068 |
| c_es5      | -0.144 | -0.101 | -0.035 | -0.02  |  0.009 |  0.039 |
| c_imb10    |  0.102 | -0.022 |  0.02  |  0.028 | -0.028 | -0.018 |
| c_ofi10    |  0.05  | -0.034 |  0.058 |  0.039 | -0.005 | -0.048 |
| c_p10      | -0.231 | -0.085 | -0.083 | -0.073 | -0.009 |  0.012 |
| c_vol10    | -0.232 | -0.088 | -0.097 | -0.09  | -0.021 |  0.006 |
| d6_cumbrel |  0.051 | -0.011 |  0.002 |  0.009 |  0.013 | -0.061 |
| d6_es5     | -0.139 | -0.097 | -0.073 | -0.066 |  0.027 |  0.055 |
| d6_imb10   |  0.048 | -0.062 |  0.002 |  0.008 | -0.023 |  0.004 |
| depth_rel  |  0.052 |  0.004 | -0     | -0.026 |  0.022 | -0.078 |
| z10        | -0.131 | -0.027 | -0.003 |  0.044 |  0.051 |  0.062 |
Features with |IC| above their shuffled-within-day placebo at the 95% level (MKT events):
| win   | feat    |    n |     ic |   plc_sd |   plc_rank_abs |
|:------|:--------|-----:|-------:|---------:|---------------:|
| L6M   | c_p10   |  426 | -0.083 |    0.04  |           0.96 |
| L6M   | c_vol10 |  426 | -0.097 |    0.039 |           0.98 |
| HOLD  | c_p10   |  492 | -0.073 |    0.034 |           0.95 |
| HOLD  | c_vol10 |  492 | -0.09  |    0.034 |           0.98 |
| PRE   | c_cb5   | 1131 | -0.076 |    0.019 |           0.97 |
| PRE   | z10     | 1131 |  0.051 |    0.022 |           0.96 |
| X     | c_b12   |  556 | -0.091 |    0.036 |           0.99 |
| Y26   | c_p10   |  106 | -0.231 |    0.072 |           0.97 |
| Y26   | d6_es5  |  104 | -0.139 |    0.071 |           0.96 |
| Y26   | c_vol10 |  106 | -0.232 |    0.077 |           0.99 |
Reading: no feature has a stable sign across PRE, X', HOLD and L6M. The ES book at the stop second and its 60-s change are the only candidates that are 'against the trade -> cut pays' in the recent windows (IC -0.14 / -0.10 in Y26 / L3M), and activity at the stop (pulled, volume) is 'high activity -> cut pays less' recently; none of it exists in PRE, so it is a regime read (as in STACK-2) and not an information edge that survives selection. For INFO's map this means: 'the book at the first stop predicts the value of cutting the rest with IC |0.1| at best, recent only, the ES book the most consistent recent sign'.

## 5. What was learned / next
1. L2 state at the first stop does not rescue or kill the STACK-2 survivor; the ES-book condition re-selects the recent gain with a quarter of the fires and without the PRE loss, but the gain is re-entry-dominated and statistically unsupported after 168 trials; treat as a LEAD for the forward shadow (stopped-book ES imbalance below its 0.33 quantile, i.e. ES book leaning against the stopped trade).
2. The first-stop cut itself remains the only loss-side structure with a recent signal; its recent gain comes from the lock engine's re-entry state, not from the saved loss on the cut rows.
3. Next family (not yet covered, per the lead's list): (2) loss-side use of the ES-leads-NQ state (ES already moved against the open trade in the last 15-60 s) with 1-3 s delay realism, or (3) stop placement at a resting-wall structure vs the fixed 60 at entry (risk-matched). Note the ES-lead agent (ESLEAD) reported no ES information beyond NQ's own move on the entry/profit side; the loss-side ES state at the stop is the only place ES shows a recent sign here.

## 6. D6 / NEEDS
The condition needs the ES 5-level imbalance (sided to the stopped trade) at the stopped book's stop second; D6 does not compute es_imb5 (see DS3_THL2_NEEDS.md). The rule is a stack-level event rule (first same-side stop -> cut 50% of the others) and has no D6 group-05 vocabulary; it stays SHADOW.
Files: code/uf7/{cells7,feat7,engine7,stageB7,qv7,ic7,report7}.py; out/uf/loss7/{feat_tid.parquet,stageA7.pkl,stageA7_PRE_X.csv,selection_PRE_X.json,stageB7.pkl,ic_map.csv,qv7_PRE_X.json,tables7.json}; DEAD_CELLS.csv +168 (program UFL7); RECENT_WINS row out/recent_wins/UF-LOSS-C7.csv.
