# DS3_CONCENTRATION - concentration and dependence audit of the live stack (DIS-AF, CAL, 2026-11-04)
Descriptive report, no hypothesis tests, no PASS claims, nothing live. Scope note l2vast/ds3/prereg/DISAF_scope.md sha256 2fab636b4c245fd836066e3aa39923db12213e1633cd42de2a014dcd992d9b17 (DECISIONS.md, logged before any outcome). Code l2vast/ds3/code/discover/diaf.py, tables out/diaf_*.csv. ZL-2 (DIS-AE) owns TH/PE rule-level questions.

## Key readings (descriptive; every number is in the sections below)
1. **The stack is the PE book, mostly in Asia.** PE share of stack P&L: HOLD 53%, L6M 61%, PRE 61%, but -43% in X' (2023-24 window); by year 49 / 50 / 71 / 56% (2023..2026). Asia is 73% of P&L in L6M and HOLD (57% PRE, but nyam 44% in PRE: the 2024-25 PE edge was NY-AM, the 2026 edge is asia + london). Cells: PE-asia alone 41% of L6M and 32% of HOLD, PE-asia + PE-london + HM-asia = 78% of L6M. Without PE: HOLD mean 13.6k/wk (stack 29.1k) but maxDD 32.9k (stack 122.0k), Calmar 0.41 vs 0.24; L6M 17.6k / 32.9k = 0.53 vs 0.72; PRE 6.2k / 72.3k = 0.09 vs 0.21. PE is 104k of the 122k HOLD maxDD episode (weeks 202606-202609), 59k of 75k in the PRE episode, 34k of 62.6k in the latest L6M week (202644).
2. **Week concentration is moderate in 2026, absent in the ALL average, and extreme in X'.** Top 5 weeks = 58% of L6M P&L (block CI 39-75%), 40% of HOLD (27-65%), 37% of PRE (25-57%), 22% of ALL (15-32%); top 1 week 15% / 10% / 9%. Median weekly P&L is close to the mean (L6M 38.6k vs 45.3k; HOLD 30.2k vs 29.1k). Ex top 5 weeks the mean falls to 26.2k (L6M, CI 10-57k), 19.8k (HOLD, CI 6.5-36k), 11.0k (PRE). X' total is only +$43k: the top-5 share (258%) is not meaningful there. The five biggest HOLD weeks (202623, 202624, 202545, 202620, 202627) are all gains of 80-130k; the five worst HOLD weeks (202644, 202606, 202604, 202608, 202607) are 30-63k losses, all five led by PE.
3. **Effective independent bets: about 4-5 of 6 books and 7-10 of 14 active book-sessions, stable by year** (N_eff books 5.0 / 3.8 / 4.6 / 4.5 for 2023..2026; mean pair correlation 0.04 / 0.30 / 0.15 / 0.20), but P&L-weighted concentration is far worse than the count suggests because PE carries half of the weekly variance.
4. **Tail dependence is much higher than average correlation implies.** In the stack's worst 10% of weeks, 3.3-3.7 of the 6 books are in their own worst 20% (1.2 if independent). Diversification ratios (stack / sum of books): weekly sd 0.64-0.70, maxDD 0.37-0.54, so the stack maxDD is below the sum of the books' own maxDDs only because their individual drawdowns fall in different weeks; the joint worst weeks are shared (PE-HM co-exceedance 0.67, PE-PB 0.56, KB-MV 0.56 in HOLD).
5. **Calendar weeks: no stable event dependence.** 155 of 187 weeks contain at least one of FOMC / CPI / NFP / witching / roll / mega-cap earnings, so the event vs non-event contrast has little to contrast. FOMC weeks average 23.8k vs 11.6k (ALL; PE 16.7k vs 6.2k) but 27.0k vs 29.5k in HOLD; CPI and NFP weeks beat others in HOLD (40k, 44k vs 26k, 25k) and trail in PRE (9.8k, 11.0k vs 17.9k, 17.7k) and X' (negative). Roll weeks 20.8k vs 12.9k (14 weeks, SE 11.6k). Signs flip across windows.
6. **Leave-one-out and caveats.** No other book or session removal changes the picture as much as PE or asia (without asia: HOLD 7.9k/wk, L6M 12.1k/wk). Removing MV or London lowers maxDD (HOLD 108.7k / 75.7k) at little mean cost (MV) or 5.9k/wk (London). Leave-one-out is a subtraction of realised P&L, not a re-run of the lock engine; weekly numbers use label weeks; the last week 202644 is partial (to 2026-10-30).

Base: Q1-A ts2 stack at live lots, engine run cube (6 books x 6 sessions x 935 label days; cube sums to the stack core, $2.52M total), weekly P&L by label week (187 weeks, 202314..202644). Windows: L6M, HOLD, MID, PRE, X' with the corrected carrying weeks dropped (L6M/HOLD 202630-202637, PRE 202506-202509, X' 202321-202341 as in the harness), ALL = every week. Leave-one-out rows subtract the realised cube P&L of the book/session from the stack (the lock-engine interaction, e.g. the combined week lock, is not re-run: stated simplification). Weeks in window: L6M 19, HOLD 44, MID 12, PRE 71, X' 23, ALL 187.

## 1. Shares by book and session

**HOLD** (stack $1,279,443, mean $29,078/wk)

| book | pnl | share_pnl | share_gross | mean_wk |
|--|--|--|--|--|
| KB | 135892 | 11 | 11 | 3088 |
| PE | 680012 | 53 | 48 | 15455 |
| SM | 113315 | 9 | 11 | 2575 |
| HM | 322221 | 25 | 21 | 7323 |
| MV | 1752 | 0 | 5 | 40 |
| PB | 26252 | 2 | 4 | 597 |

**PRE** (stack $1,144,378, mean $16,118/wk)

| book | pnl | share_pnl | share_gross | mean_wk |
|--|--|--|--|--|
| KB | 154342 | 14 | 13 | 2174 |
| PE | 702419 | 61 | 50 | 9893 |
| SM | 79148 | 7 | 12 | 1115 |
| HM | 97637 | 8 | 11 | 1375 |
| MV | 32971 | 3 | 7 | 464 |
| PB | 77861 | 7 | 6 | 1097 |

**L6M** (stack $860,900, mean $45,311/wk)

| book | pnl | share_pnl | share_gross | mean_wk |
|--|--|--|--|--|
| KB | 124365 | 14 | 12 | 6546 |
| PE | 526777 | 61 | 53 | 27725 |
| SM | 40300 | 5 | 8 | 2121 |
| HM | 160227 | 19 | 18 | 8433 |
| MV | -1723 | -0 | 4 | -91 |
| PB | 10954 | 1 | 3 | 576 |

**X'** (stack $42,855, mean $1,863/wk)

| book | pnl | share_pnl | share_gross | mean_wk |
|--|--|--|--|--|
| KB | 9581 | 22 | 16 | 417 |
| PE | -18407 | -43 | 37 | -800 |
| SM | 43521 | 102 | 22 | 1892 |
| HM | -4383 | -10 | 11 | -191 |
| MV | -686 | -2 | 7 | -30 |
| PB | 13229 | 31 | 7 | 575 |

**MID** (stack $193,373, mean $16,114/wk)

| book | pnl | share_pnl | share_gross | mean_wk |
|--|--|--|--|--|
| KB | 7841 | 4 | 12 | 653 |
| PE | 74780 | 39 | 40 | 6232 |
| SM | 49738 | 26 | 17 | 4145 |
| HM | 38774 | 20 | 17 | 3231 |
| MV | 26382 | 14 | 11 | 2198 |
| PB | -4142 | -2 | 4 | -345 |

By year and book (share of the stack P&L, share of gross weekly gains; carry weeks NOT dropped here)

| book | 2023 | 2024 | 2025 | 2026 |
|--|--|--|--|--|
| HM | -30 | 12 | 13 | 24 |
| KB | -13 | 19 | 3 | 8 |
| MV | 7 | 5 | -5 | -2 |
| PB | 2 | 6 | 7 | 1 |
| PE | 49 | 50 | 71 | 56 |
| SM | 84 | 9 | 11 | 13 |

Gross-gain share:

| book | 2023 | 2024 | 2025 | 2026 |
|--|--|--|--|--|
| HM | 11 | 12 | 15 | 20 |
| KB | 12 | 16 | 11 | 11 |
| MV | 8 | 8 | 5 | 5 |
| PB | 5 | 6 | 6 | 4 |
| PE | 46 | 46 | 51 | 49 |
| SM | 17 | 13 | 12 | 12 |

By session (all books), share of window P&L

| session | L6M | HOLD | PRE | X' |
|--|--|--|--|--|
| asia | 73 | 73 | 57 | 98 |
| close | 0 | 0 | 0 | 0 |
| london | 22 | 20 | -2 | -16 |
| nyam | 3 | 6 | 44 | 12 |
| nypm | 2 | 1 | 1 | 7 |
| pre | 0 | 0 | 0 | 0 |

Session share by year

| session | 2023 | 2024 | 2025 | 2026 |
|--|--|--|--|--|
| asia | -49 | 57 | 68 | 81 |
| london | 34 | 4 | -1 | 16 |
| pre | 0 | 0 | 0 | 0 |
| nyam | 112 | 35 | 34 | 3 |
| nypm | 3 | 4 | -1 | 0 |
| close | 0 | 0 | 0 | 0 |

Top / bottom book-session cells, L6M (share of stack P&L):

| cell | pnl | share |
|--|--|--|
| PE-asia | 350386 | 41 |
| PE-london | 176392 | 20 |
| HM-asia | 147062 | 17 |
| KB-asia | 77580 | 9 |
| SM-asia | 45597 | 5 |
| SM-london | -5297 | -1 |
| KB-nyam | -12217 | -1 |
| MV-london | -25913 | -3 |

Top / bottom book-session cells, HOLD (share of stack P&L):

| cell | pnl | share |
|--|--|--|
| PE-asia | 410594 | 32 |
| HM-asia | 293586 | 23 |
| PE-london | 217750 | 17 |
| KB-asia | 103417 | 8 |
| SM-asia | 97345 | 8 |
| PB-nyam | 0 | 0 |
| MV-london | -13984 | -1 |
| KB-nyam | -18259 | -1 |

Top / bottom book-session cells, PRE (share of stack P&L):

| cell | pnl | share |
|--|--|--|
| PE-asia | 375809 | 33 |
| PE-nyam | 349057 | 30 |
| SM-asia | 80831 | 7 |
| PB-asia | 77861 | 7 |
| KB-asia | 63447 | 6 |
| SM-london | -1683 | -0 |
| MV-london | -15475 | -1 |
| PE-london | -22447 | -2 |

Maxdd episode of the stack per window: weekly P&L inside the peak-to-trough span by book ($; the books sum to the episode P&L)

| window | maxdd | start_wk | trough_wk | weeks_in | episode_pnl | KB | PE | SM | HM | MV | PB |
|--|--|--|--|--|--|--|--|--|--|--|--|
| L6M | 62576 | 202644 | 202644 | 1 | -62576 | -3783 | -34396 | -11623 | -10337 | -655 | -1782 |
| HOLD | 122025 | 202606 | 202609 | 3 | -122025 | -5897 | -104424 | 192 | 7604 | -13359 | -6141 |
| MID | 59703 | 202607 | 202609 | 2 | -59703 | 1076 | -47528 | -1657 | -12226 | 925 | -293 |
| PRE | 75057 | 202411 | 202416 | 5 | -75057 | -6050 | -59435 | 2204 | -7206 | -12839 | 8270 |
| X' | 49417 | 202345 | 202348 | 3 | -49417 | -2850 | -33081 | 3143 | -12075 | -1951 | -2603 |

## 2. Top-k concentration (weekly, daily, trade level)

Weekly stack P&L: share of the window total in the top 1 / 5 / 10 weeks (%), median, 10%-trimmed mean, mean excluding the top 5 weeks; moving-block bootstrap CIs (4-week blocks, 2,000 draws)

| window | weeks | total | mean | median | trim10 | top1 | top5 | top10 | mean_ex_top5 | top5_CI | ex5_CI | median_CI | mean_CI |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| L6M | 19 | 860900 | 45310 | 38618 | 46682 | 15 | 58 | 91 | 26153 | [39, 75] | [10430, 57289] | [32432, 75257] | [30157, 74083] |
| HOLD | 44 | 1279443 | 29078 | 30168 | 29258 | 10 | 40 | 68 | 19758 | [27, 65] | [6517, 36435] | [15914, 44463] | [14090, 47116] |
| PRE | 71 | 1144378 | 16118 | 15188 | 14946 | 9 | 37 | 60 | 11000 | [25, 57] | [4493, 18367] | [7288, 23086] | [8742, 24120] |
| X' | 23 | 42855 | 1863 | 8390 | 2553 | 57 | 258 | 422 | -3769 | [53, 2204] | [-9322, 5386] | [-3754, 11907] | [-2893, 8899] |
| ALL | 187 | 2520149 | 13477 | 12430 | 11638 | 5 | 22 | 38 | 10831 | [15, 32] | [6020, 16585] | [8301, 18224] | [8410, 19705] |

Top 5 weeks in HOLD: 202623 $129876, 202624 $128120, 202545 $89378, 202620 $81583, 202627 $79908. Worst 5: 202644 $-62576, 202606 $-62322, 202604 $-48055, 202608 $-29860, 202607 $-29843

Daily stack P&L concentration

| window | days | total | top1d | top5d | top10d | median_day | pos_days |
|--|--|--|--|--|--|--|--|
| L6M | 91 | 833792 | 8 | 30 | 53 | 9820 | 66 |
| HOLD | 220 | 1279443 | 5 | 22 | 38 | 3521 | 57 |
| PRE | 348 | 1078306 | 6 | 28 | 50 | 417 | 51 |
| X' | 113 | 69279 | 43 | 180 | 300 | -627 | 46 |

Trade-level concentration on the no-lock paper track at live lots (17,396 trades, before the lock engine and Q1-A sizing; a descriptive proxy for the stack)

| span | trades | total | top1 | top10 | top1pct | top5pct | median_trade |
|--|--|--|--|--|--|--|--|
| 2026-05.. | 3843 | 708036 | 2 | 16 | 50 | 236 | -1135 |
| 2025-11.. | 6879 | 1096054 | 1 | 11 | 58 | 272 | -925 |
| 2024-02..2025-06 | 6475 | 1033190 | 2 | 13 | 62 | 275 | -654 |
| all | 17396 | 2526421 | 1 | 6 | 68 | 302 | -667 |

## 3. Effective number of independent bets (participation ratio of eigenvalues of the weekly correlation matrix)

| span | weeks | books | N_eff_books | top_eig_share_books | cells | N_eff_cells | top_eig_share_cells | mean_pair_corr_books |
|--|--|--|--|--|--|--|--|--|
| 2023 | 39 | 6 | 5.03 | 27.14 | 14 | 7.86 | 24.24 | 0.04 |
| 2024 | 52 | 6 | 3.84 | 42.78 | 14 | 8.37 | 22.64 | 0.30 |
| 2025 | 52 | 6 | 4.55 | 34.78 | 14 | 9.24 | 17.68 | 0.15 |
| 2026 | 44 | 6 | 4.47 | 35.19 | 13 | 8.88 | 18.74 | 0.20 |
| L6M | 19 | 6 | 3.96 | 39.02 | 13 | 6.51 | 25.73 | 0.21 |
| HOLD | 44 | 6 | 4.49 | 34.52 | 14 | 9.79 | 16.67 | 0.19 |
| MID | 12 | 6 | 3.98 | 38.38 | 13 | 6.27 | 26.41 | 0.11 |
| PRE | 71 | 6 | 4.55 | 35.73 | 14 | 9.62 | 17.87 | 0.21 |
| X' | 23 | 6 | 4.50 | 29.66 | 14 | 6.55 | 24.13 | 0.06 |

Weekly correlation of books, HOLD

|  | KB | PE | SM | HM | MV | PB |
|--|--|--|--|--|--|--|
| KB | 1.00 | 0.49 | 0.03 | 0.10 | 0.11 | -0.02 |
| PE | 0.49 | 1.00 | 0.13 | 0.48 | 0.15 | 0.36 |
| SM | 0.03 | 0.13 | 1.00 | 0.33 | 0.27 | 0.25 |
| HM | 0.10 | 0.48 | 0.33 | 1.00 | -0.05 | 0.30 |
| MV | 0.11 | 0.15 | 0.27 | -0.05 | 1.00 | -0.10 |
| PB | -0.02 | 0.36 | 0.25 | 0.30 | -0.10 | 1.00 |

Weekly correlation of books, PRE

|  | KB | PE | SM | HM | MV | PB |
|--|--|--|--|--|--|--|
| KB | 1.00 | 0.32 | 0.15 | 0.44 | 0.17 | 0.36 |
| PE | 0.32 | 1.00 | -0.00 | 0.25 | 0.16 | 0.37 |
| SM | 0.15 | -0.00 | 1.00 | 0.08 | 0.24 | 0.13 |
| HM | 0.44 | 0.25 | 0.08 | 1.00 | 0.08 | 0.41 |
| MV | 0.17 | 0.16 | 0.24 | 0.08 | 1.00 | -0.07 |
| PB | 0.36 | 0.37 | 0.13 | 0.41 | -0.07 | 1.00 |

## 4. Leave-one-out (P&L change is mechanical subtraction of the realised cube; mean $/wk, maxDD $, Calmar)

**HOLD**

| case | mean | maxdd | calmar |
|--|--|--|--|
| STACK | 29078 | 122025 | 0.24 |
| without KB | 25990 | 116128 | 0.22 |
| without PE | 13623 | 32922 | 0.41 |
| without SM | 26503 | 122217 | 0.22 |
| without HM | 21755 | 129629 | 0.17 |
| without MV | 29038 | 108666 | 0.27 |
| without PB | 28482 | 115884 | 0.25 |
| without session asia | 7915 | 95000 | 0.08 |
| without session london | 23203 | 75738 | 0.31 |
| without session pre | 29078 | 122025 | 0.24 |
| without session nyam | 27311 | 98294 | 0.28 |
| without session nypm | 28806 | 117221 | 0.25 |
| without session close | 29078 | 122025 | 0.24 |
| without top 1 weeks (own window) | 26734 | 122025 | 0.22 |
| without top 3 weeks (own window) | 22733 | 122025 | 0.19 |
| without top 5 weeks (own window) | 19758 | 122025 | 0.16 |

**PRE**

| case | mean | maxdd | calmar |
|--|--|--|--|
| STACK | 16118 | 75057 | 0.21 |
| without KB | 13944 | 69042 | 0.20 |
| without PE | 6225 | 72287 | 0.09 |
| without SM | 15003 | 79434 | 0.19 |
| without HM | 14743 | 68093 | 0.22 |
| without MV | 15654 | 71668 | 0.22 |
| without PB | 15021 | 83326 | 0.18 |
| without session asia | 6972 | 69682 | 0.10 |
| without session london | 16383 | 65145 | 0.25 |
| without session pre | 16118 | 75057 | 0.21 |
| without session nyam | 9073 | 63745 | 0.14 |
| without session nypm | 15926 | 73753 | 0.22 |
| without session close | 16118 | 75057 | 0.21 |
| without top 1 weeks (own window) | 14915 | 84684 | 0.18 |
| without top 3 weeks (own window) | 12877 | 84684 | 0.15 |
| without top 5 weeks (own window) | 11000 | 84684 | 0.13 |

**L6M**

| case | mean | maxdd | calmar |
|--|--|--|--|
| STACK | 45311 | 62576 | 0.72 |
| without KB | 38765 | 58792 | 0.66 |
| without PE | 17585 | 32922 | 0.53 |
| without SM | 43190 | 50953 | 0.85 |
| without HM | 36878 | 52239 | 0.71 |
| without MV | 45401 | 61920 | 0.73 |
| without PB | 44734 | 60794 | 0.74 |
| without session asia | 12070 | 51745 | 0.23 |
| without session london | 35424 | 45809 | 0.77 |
| without session pre | 45311 | 62576 | 0.72 |
| without session nyam | 43987 | 67314 | 0.65 |
| without session nypm | 44451 | 61898 | 0.72 |
| without session close | 45311 | 62576 | 0.72 |
| without top 1 weeks (own window) | 40612 | 62576 | 0.65 |
| without top 3 weeks (own window) | 32583 | 62576 | 0.52 |
| without top 5 weeks (own window) | 26153 | 62576 | 0.42 |

Leave-one-book-session-out, ordered by HOLD share (top 8 and bottom 3)

| cell | hold_mean | hold_maxdd | hold_calmar | pre_mean | pre_calmar | hold_share |
|--|--|--|--|--|--|--|
| PE-asia | 19747 | 80770 | 0.24 | 10825 | 0.12 | 32 |
| HM-asia | 22406 | 127614 | 0.18 | 15394 | 0.23 | 23 |
| PE-london | 24129 | 81839 | 0.29 | 16434 | 0.26 | 17 |
| KB-asia | 26728 | 127942 | 0.21 | 15224 | 0.20 | 8 |
| SM-asia | 26866 | 117796 | 0.23 | 14980 | 0.19 | 8 |
| PE-nyam | 27904 | 99478 | 0.28 | 11202 | 0.21 | 4 |
| KB-london | 28197 | 115725 | 0.24 | 15825 | 0.20 | 3 |
| HM-nyam | 28427 | 124039 | 0.23 | 15467 | 0.20 | 2 |
| PB-nyam | 29078 | 122025 | 0.24 | 16118 | 0.21 | 0 |
| MV-london | 29396 | 111154 | 0.26 | 16336 | 0.23 | -1 |
| KB-nyam | 29493 | 121315 | 0.24 | 15323 | 0.18 | -1 |

## 5. Calendar-week dependence (descriptive)

Weeks containing the event vs other weeks (mean weekly $, share of the span total from those weeks; SE = naive standard error of the in-event mean)

| span | event | weeks_in | stack_mean_in | stack_mean_out | stack_share_pnl | PE_mean_in | PE_mean_out | PE_share | stack_se_in |
|--|--|--|--|--|--|--|--|--|--|
| ALL | FOMC | 29 | 23779 | 11586 | 27 | 16658 | 6210 | 33 | 6464 |
| ALL | CPI | 42 | 14455 | 13193 | 24 | 6863 | 8110 | 20 | 4926 |
| ALL | NFP | 42 | 13775 | 13390 | 23 | 8787 | 7553 | 25 | 6981 |
| ALL | WITCHING (quarterly opex) | 14 | 25055 | 12540 | 14 | 15598 | 7202 | 15 | 7445 |
| ALL | MONTH/QUARTER END | 48 | 16566 | 12410 | 32 | 11433 | 6586 | 38 | 5323 |
| ALL | ROLL WEEK | 14 | 20756 | 12888 | 12 | 11232 | 7555 | 11 | 11578 |
| ALL | EARNINGS (top-8 mega-cap AMC/BMO) | 117 | 12145 | 15702 | 56 | 6822 | 9516 | 54 | 3414 |
| ALL | ANY of FOMC/CPI/NFP/witching/roll/earnings | 155 | 14245 | 9755 | 88 | 8229 | 5899 | 87 | 2888 |
| HOLD | FOMC | 7 | 27022 | 29467 | 15 | 16512 | 15255 | 17 | 18875 |
| HOLD | CPI | 9 | 40140 | 26234 | 28 | 16920 | 15078 | 22 | 15035 |
| HOLD | NFP | 10 | 44398 | 24572 | 35 | 25081 | 12624 | 37 | 14612 |
| HOLD | WITCHING (quarterly opex) | 4 | 44716 | 27514 | 14 | 24908 | 14510 | 15 | 18139 |
| HOLD | MONTH/QUARTER END | 10 | 33974 | 27638 | 27 | 21478 | 13683 | 32 | 13843 |
| HOLD | ROLL WEEK | 3 | 57408 | 27005 | 14 | 23656 | 14855 | 10 | 35691 |
| HOLD | EARNINGS (top-8 mega-cap AMC/BMO) | 26 | 26872 | 32265 | 55 | 15434 | 15485 | 59 | 9645 |
| HOLD | ANY of FOMC/CPI/NFP/witching/roll/earnings | 37 | 32803 | 9388 | 95 | 17388 | 5236 | 95 | 7394 |
| PRE | FOMC | 12 | 25458 | 14218 | 27 | 19264 | 7987 | 33 | 8806 |
| PRE | CPI | 16 | 9829 | 17947 | 14 | 4636 | 11422 | 11 | 7147 |
| PRE | NFP | 17 | 10975 | 17737 | 16 | 7728 | 10575 | 19 | 10751 |
| PRE | WITCHING (quarterly opex) | 6 | 19868 | 15772 | 10 | 13363 | 9573 | 11 | 11147 |
| PRE | MONTH/QUARTER END | 20 | 17776 | 15468 | 31 | 11804 | 9144 | 34 | 7881 |
| PRE | ROLL WEEK | 6 | 19955 | 15764 | 10 | 11513 | 9744 | 10 | 18178 |
| PRE | EARNINGS (top-8 mega-cap AMC/BMO) | 43 | 17731 | 13641 | 67 | 9985 | 9753 | 61 | 5175 |
| PRE | ANY of FOMC/CPI/NFP/witching/roll/earnings | 59 | 16488 | 14298 | 85 | 10674 | 6054 | 90 | 4285 |
| X' | FOMC | 4 | -2682 | 2820 | -25 | 3312 | -1666 | -72 | 10283 |
| X' | CPI | 5 | -1010 | 2661 | -12 | -4099 | 116 | 111 | 9600 |
| X' | NFP | 6 | -3962 | 3919 | -56 | -2727 | -120 | 89 | 8448 |
| X' | MONTH/QUARTER END | 5 | 5597 | 826 | 65 | 9962 | -3790 | -271 | 8597 |
| X' | EARNINGS (top-8 mega-cap AMC/BMO) | 14 | 2721 | 530 | 89 | 547 | -2896 | -42 | 4699 |
| X' | ANY of FOMC/CPI/NFP/witching/roll/earnings | 18 | 1085 | 4665 | 46 | -1720 | 2513 | 168 | 4335 |

## 6. Tail dependence and diversification in drawdowns

Joint worst weeks and diversification ratios (ratio stack/sum of books: 1.00 = no diversification; the mean ratio is 1.00 by construction)

| window | weeks | worst_weeks | avg_books_in_own_worst20 | expected_if_indep | mean_corr_all | mean_corr_worst30pct | sd_ratio_stack_over_sum | maxdd_ratio_stack_over_sum | stack_maxdd | sum_book_maxdd | mean_ratio |
|--|--|--|--|--|--|--|--|--|--|--|--|
| HOLD | 44 | 4 | 3.50 | 1.20 | 0.19 | -0.01 | 0.68 | 0.51 | 122024.73 | 237709.70 | 1.00 |
| PRE | 71 | 7 | 3.71 | 1.20 | 0.21 | -0.03 | 0.64 | 0.39 | 75056.65 | 190732.27 | 1.00 |
| L6M | 19 | 2 | 3.50 | 1.20 | 0.21 | 0.06 | 0.70 | 0.54 | 62575.63 | 116601.09 | 1.00 |
| X' | 23 | 2 | 2.00 | 1.20 | 0.06 | -0.14 | 0.50 | 0.39 | 49417.24 | 126627.52 | 1.00 |
| ALL | 187 | 19 | 3.32 | 1.20 | 0.19 | -0.02 | 0.65 | 0.37 | 122024.73 | 329431.90 | 1.00 |

Co-exceedance in HOLD: P(book column in its own worst 20% | book row in its own worst 20%); independence = 0.20

|  | KB | PE | SM | HM | MV | PB |
|--|--|--|--|--|--|--|
| KB | 1.00 | 0.33 | 0.00 | 0.22 | 0.56 | 0.11 |
| PE | 0.33 | 1.00 | 0.22 | 0.67 | 0.33 | 0.56 |
| SM | 0.00 | 0.22 | 1.00 | 0.22 | 0.22 | 0.33 |
| HM | 0.22 | 0.67 | 0.22 | 1.00 | 0.00 | 0.33 |
| MV | 0.56 | 0.33 | 0.22 | 0.00 | 1.00 | 0.22 |
| PB | 0.11 | 0.56 | 0.33 | 0.33 | 0.22 | 1.00 |

Five worst HOLD weeks by book ($):

| week | stack | KB | PE | SM | HM | MV | PB |
|--|--|--|--|--|--|--|--|
| 202644 | -62576 | -3783 | -34396 | -11623 | -10337 | -655 | -1782 |
| 202606 | -62322 | -6973 | -56897 | 1849 | 19830 | -14284 | -5848 |
| 202604 | -48055 | -65 | -40100 | -2938 | -4563 | 2236 | -2625 |
| 202608 | -29860 | 3222 | -27234 | 3477 | -4901 | -663 | -3762 |
| 202607 | -29843 | -2146 | -20294 | -5134 | -7325 | 1588 | 3468 |
