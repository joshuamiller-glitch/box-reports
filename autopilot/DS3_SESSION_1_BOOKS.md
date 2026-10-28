# DS3_SESSION_1_BOOKS - the live and Sim books, session by session (D3SS1, T-SESSION item 1, 2026-10-28)
Research only; nothing live. Prereg l2vast/ds3/prereg/SS1_prereg.md sha256 7a8777305548edb2d1765e8f613257787b720e8327936737385e2bb909ccb32c (DECISIONS.md); pre-holdout text autopilot/DS3_SESSION_1_PREHOLD.md sha256 1b03cbc32ed1f13dd1f4c9b4f969e5d6591db49d5794faeab7ec5b09b2e5048d, ONE logged look (tracks D3SS1, D3SS1_SPAN2) before any HOLD/X number. Code l2vast/ds3/code/ss1/ (ss_lib, ss_eng, ss_pre, ss_pre2, ss_final); outputs l2vast/ds3/out/ss1/ (final_book_session.csv, final_book_session_year.csv, final_b3_rsi2t.csv, final_cells.json, placebo_*.csv, trades_by_session.parquet). UNTOUCHED never read: all tables cut at label day 2026-02-06 (HOLD = 2025-07-01..2026-02-06, 32 weeks; the older 2025-07..2026-10 HOLD is not used).

## Verdict (plain)
- **No session block is supported.** 7 PRE-chosen block cells (one per book that has a losing session with >= 100 PRE trades); **0 SESSION-PASS, 0 SESSION-CANDIDATE** - none is PRE-significant (every PRE delta CI includes 0; deltas 0.5-2.2k/wk against MDE 3.3-7.2k) and 4 of 7 also lose in HOLD (PE LONDON -7.5k/wk, DN NY-PM -7.4k, PBS NY-PM -5.5k, CR LONDON -0.7k). The PRE-worst session regresses to the mean, as predicted.
- **Closest block: WT NY-PM (12:00-15:00 ET entries), stack books exact engine.** PRE +1,340/wk [-1,215, +3,863]; HOLD +4,422 [+1,286, +7,412] (MDE 4,445, 1.0x), X +714 [-1,721, +3,142], 2023 +825, 2024 +1,070, 2025 +2,537, 2026 +8,341 (all years +); ALL 149 wk +1,835 [+210, +3,407]; shifted-session placebo rank HOLD 0.965 (287 shifts, exact), X 0.80. It fails ONLY the PRE-significance condition, so by the directive's tier definition it is NOT-CONFIRMED (not SESSION-CANDIDATE); HOLD one-sided p 0.003 vs best-of-F threshold 0.05/66 = 0.00076 (not cleared; the label would be 'not best-of-F'). HOLD stack maxDD 601,016 -> 601,882 (no help), PRE 477,701 -> 472,641, worst-20-weeks (ALL) -3,534k -> -3,432k. 4.6 WT trades/wk removed. It is the one block worth a forward watch; it is not a scored recommendation.
- **Carrier cells (session books): 7 PRE-significant, 5 SESSION-CANDIDATE, 0 SESSION-PASS, 2 NOT-CONFIRMED.** SESSION-CANDIDATE: PE ASIA, DN ASIA, KB ASIA, KB NY-PM, MV NY-AM (HOLD > 0 and positive in both HOLD years); best-of-F (p <= 0.00076) cleared by none (best DN ASIA p 0.011, PE ASIA p 0.023). All five are NEGATIVE or ~0 on the 2023 span X except DN ASIA (+1,987), which is why they stay CANDIDATE with half lots. NOT-CONFIRMED: MV ASIA (HOLD -653, H2025 -3,585), DN NY-AM (HOLD -452, H2025 -638).
- Basis warnings: MV, MA, PBS rows are PRE-LOCK signal trades at pts x 200 - 100.13 (library locked series is lower for PBS: PRE 525/wk here vs 6,067/wk on the library PE2 series; MV 19,036 vs 17,221; MA 7,847 vs 8,330); DN and CR are the lock-kept mapped rows (PRE means match the library to the dollar: DN 17,358, CR 744). Sim-book numbers are standalone own-$ at 10 lots, not stack-weighted, and carry no stack-add claim.

## Windows, sessions, definitions
Sessions by ENTRY time ET: ASIA 18:00-02:00, LONDON 02:00-08:30, PRE 08:30-09:30, NY-AM 09:30-12:00, NY-PM 12:00-15:00, CLOSE 15:00-16:54, NY = NY-AM + NY-PM (descriptive). PRE 2024-02-01..2025-06-30 (75 wk), HOLD 32 wk, X 2023-04-01..2024-01-31 (44 wk), ALL 149 wk. Weekly sums of in-window label days; Sharpe annualised x sqrt(52); maxDD on the daily path; worst-20 share = session $ in the book's own 20 worst all-session weeks of the window / book $ in those weeks (negative share = the session was making money in the book's bad weeks); MDE = 2.8 SD/sqrt(weeks) on the session weekly mean. Stack books (ST, HM, WT, KB, SM, PE) are stack-weighted $ net of sweep cost from the D3D2A audit table (PE = the six-book stack's PB = PB3B_R5_P1; the directive's PB and PE are the same book there; PBS is the other pullback cell PB_ST10_SWZ_T3). CLOSE has 0 stack-book trades (live block 15:00-16:54); the 51 CLOSE and 16 'NONE' (16:55+) entries come from Sim books' own rule sets and are reported as is.

## Table 1 - weekly mean $ by book x session (ALL 149 weeks | HOLD 32 weeks)
| book | ASIA | LONDON | PRE | NY-AM | NY-PM | CLOSE | NY | ALL |
|---|---|---|---|---|---|---|---|---|
| ST | 3,109 / 3,222 | 2,145 / 5,147 | 1,369 / -1,922 | 2,788 / 10,270 | 1,860 / 1,997 | 0 / 0 | 4,649 / 12,267 | 11,272 / 18,713 |
| HM | 5,664 / 12,117 | 1,641 / -1,484 | -1,223 / -415 | 815 / -839 | -813 / -3,699 | 0 / 0 | 2 / -4,539 | 6,067 / 5,629 |
| WT | 2,708 / 4,968 | 608 / -849 | 142 / 206 | 776 / 3,810 | -1,778 / -4,422 | 0 / 0 | -1,002 / -611 | 2,461 / 3,713 |
| KB | 2,561 / 2,810 | 1,673 / 3,287 | -87 / -536 | 2,033 / 2,418 | 2,045 / 569 | 0 / 0 | 4,079 / 2,987 | 8,215 / 8,534 |
| SM | 2,538 / 2,690 | 1,015 / 1,492 | 176 / -427 | 1,168 / -68 | -188 / 465 | 0 / 0 | 979 / 397 | 4,709 / 4,152 |
| PE | 2,843 / 6,078 | 567 / 4,426 | -328 / -707 | 2,540 / 3,266 | 1,218 / -1,356 | 0 / 0 | 3,758 / 1,910 | 6,840 / 11,708 |
| PBS | 4,335 / 15,907 | 2,869 / 9,802 | 458 / -1,272 | 2,933 / 4,212 | -447 / 5,521 | -198 / 366 | 2,487 / 9,733 | 9,950 / 34,535 |
| MV | 4,340 / -653 | 1,704 / 8,261 | -1,012 / -219 | 4,852 / 5,747 | -1,009 / 754 | -76 / -145 | 3,843 / 6,501 | 8,799 / 13,745 |
| MA | 2,369 / -2,471 | 3,464 / 9,362 | -856 / 784 | 2,939 / 4,157 | 1,334 / 5,064 | -78 / -202 | 4,273 / 9,221 | 9,173 / 16,695 |
| DN | 6,676 / 11,863 | 2,266 / 3,162 | 1,204 / 2,613 | 3,413 / -452 | 1,856 / 7,404 | 0 / 0 | 5,269 / 6,953 | 15,415 / 24,591 |
| CR | -496 / -4,834 | -433 / 724 | 785 / 469 | -1,879 / -3,379 | 570 / 287 | 0 / 0 | -1,310 / -3,092 | -1,453 / -6,734 |

## Table 2 - full metrics, ALL window (149 weeks)
| book | session | trades/wk | weekly mean | SD | Sharpe | maxDD | worst-20 share | MDE | 2023 | 2024 | 2025 | 2026 | HOLD 2025H2 | HOLD 2026 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ST | ASIA | 8.04 | 3,109 | 33,063 | 0.68 | 278,008 | 0.41 | 7,584 | 3,663 | 1,545 | 4,007 | 4,349 | 2,852 | 4,349 |
| ST | LONDON | 4.66 | 2,145 | 26,456 | 0.58 | 261,213 | 0.19 | 6,069 | 1,081 | 674 | 4,857 | -2,619 | 6,682 | -2,619 |
| ST | PRE | 0.98 | 1,369 | 11,058 | 0.89 | 74,570 | 0.04 | 2,537 | 104 | 2,245 | 1,526 | 21 | -2,283 | 21 |
| ST | NY-AM | 5.33 | 2,788 | 26,013 | 0.77 | 131,766 | 0.27 | 5,967 | 858 | 993 | 4,593 | 14,328 | 8,988 | 14,328 |
| ST | NY-PM | 2.69 | 1,860 | 14,545 | 0.92 | 120,202 | 0.10 | 3,337 | 2,145 | 1,536 | 2,319 | -1,796 | 2,765 | -1,796 |
| ST | NY | 8.02 | 4,649 | 29,801 | 1.12 | 214,496 | 0.37 | 6,836 | 3,003 | 2,529 | 6,912 | 12,533 | 11,753 | 12,533 |
| ST | ALL | 21.70 | 11,272 | 49,304 | 1.65 | 281,937 | 1.00 | 11,310 | 7,851 | 6,993 | 17,302 | 14,284 | 19,004 | 14,284 |
| HM | ASIA | 7.50 | 5,664 | 30,406 | 1.34 | 284,179 | 0.32 | 6,975 | 1,421 | 708 | 12,546 | 14,351 | 11,171 | 14,351 |
| HM | LONDON | 4.56 | 1,641 | 24,776 | 0.48 | 173,718 | 0.32 | 5,683 | 4,245 | 2,178 | 1,266 | -17,267 | 2,078 | -17,267 |
| HM | PRE | 0.64 | -1,223 | 8,877 | -0.99 | 237,152 | 0.07 | 2,036 | -1,636 | -2,603 | 371 | -20 | -488 | -20 |
| HM | NY-AM | 3.79 | 815 | 20,076 | 0.29 | 189,051 | 0.20 | 4,605 | 788 | 3,114 | -1,529 | 1,127 | -1,245 | 1,127 |
| HM | NY-PM | 3.10 | -813 | 16,037 | -0.37 | 407,381 | 0.09 | 3,679 | -673 | 3,981 | -5,387 | -3,397 | -3,629 | -3,397 |
| HM | NY | 6.89 | 2 | 26,870 | 0.00 | 482,627 | 0.29 | 6,164 | 115 | 7,094 | -6,916 | -2,270 | -4,875 | -2,270 |
| HM | ALL | 19.62 | 6,067 | 47,972 | 0.91 | 250,458 | 1.00 | 11,004 | 4,130 | 7,369 | 7,237 | -5,206 | 7,828 | -5,206 |
| WT | ASIA | 11.70 | 2,708 | 16,207 | 1.20 | 82,238 | 0.33 | 3,718 | -66 | 3,006 | 3,610 | 9,233 | 3,836 | 9,233 |
| WT | LONDON | 8.82 | 608 | 13,749 | 0.32 | 115,451 | 0.32 | 3,154 | 1,327 | 1,010 | -618 | 3,027 | -1,679 | 3,027 |
| WT | PRE | 1.05 | 142 | 5,376 | 0.19 | 48,975 | -0.01 | 1,233 | -426 | 670 | -158 | 1,766 | -148 | 1,766 |
| WT | NY-AM | 5.72 | 776 | 11,279 | 0.50 | 120,691 | 0.18 | 2,587 | -856 | 74 | 2,147 | 5,218 | 3,356 | 5,218 |
| WT | NY-PM | 4.64 | -1,778 | 10,007 | -1.28 | 291,731 | 0.17 | 2,295 | -825 | -905 | -2,542 | -8,341 | -3,387 | -8,341 |
| WT | NY | 10.36 | -1,002 | 15,325 | -0.47 | 163,190 | 0.36 | 3,515 | -1,681 | -831 | -396 | -3,123 | -31 | -3,123 |
| WT | ALL | 31.96 | 2,461 | 27,224 | 0.65 | 168,412 | 1.00 | 6,245 | -846 | 3,862 | 2,445 | 10,903 | 1,978 | 10,903 |
| KB | ASIA | 8.55 | 2,561 | 17,968 | 1.03 | 200,236 | 0.50 | 4,122 | -1,238 | 3,297 | 3,716 | 9,713 | 1,172 | 9,713 |
| KB | LONDON | 4.78 | 1,673 | 12,940 | 0.93 | 87,093 | 0.20 | 2,968 | 338 | 2,516 | 1,762 | 1,572 | 3,546 | 1,572 |
| KB | PRE | 0.83 | -87 | 5,894 | -0.11 | 103,145 | 0.06 | 1,352 | 282 | -1,025 | 725 | -1,344 | -337 | -1,344 |
| KB | NY-AM | 5.50 | 2,033 | 13,271 | 1.10 | 116,610 | 0.17 | 3,044 | 1,122 | 2,280 | 2,790 | -1,591 | 3,220 | -1,591 |
| KB | NY-PM | 3.42 | 2,045 | 11,297 | 1.31 | 90,299 | 0.07 | 2,591 | -1,138 | 5,101 | 1,482 | 37 | 666 | 37 |
| KB | NY | 8.91 | 4,079 | 16,844 | 1.75 | 167,174 | 0.24 | 3,864 | -16 | 7,382 | 4,272 | -1,554 | 3,886 | -1,554 |
| KB | ALL | 23.11 | 8,215 | 28,255 | 2.10 | 216,950 | 1.00 | 6,481 | -634 | 12,155 | 10,457 | 8,387 | 8,251 | 8,387 |
| SM | ASIA | 3.15 | 2,538 | 16,143 | 1.13 | 106,031 | 0.35 | 3,703 | 1,121 | 2,188 | 3,926 | 1,746 | 2,800 | 1,746 |
| SM | LONDON | 3.15 | 1,015 | 15,766 | 0.46 | 89,690 | 0.32 | 3,617 | 1,382 | 1,205 | 525 | 928 | 1,562 | 928 |
| SM | PRE | 0.43 | 176 | 5,924 | 0.21 | 56,045 | 0.09 | 1,359 | 1,393 | -245 | -337 | 471 | -611 | 471 |
| SM | NY-AM | 1.74 | 1,168 | 10,528 | 0.80 | 75,868 | 0.18 | 2,415 | -191 | 2,922 | 555 | -480 | 26 | -480 |
| SM | NY-PM | 1.30 | -188 | 8,968 | -0.15 | 122,958 | 0.07 | 2,057 | -2,074 | 43 | 356 | 5,277 | -622 | 5,277 |
| SM | NY | 3.04 | 979 | 13,228 | 0.53 | 165,953 | 0.24 | 3,034 | -2,265 | 2,965 | 912 | 4,797 | -595 | 4,797 |
| SM | ALL | 9.78 | 4,709 | 24,077 | 1.41 | 178,087 | 1.00 | 5,523 | 1,632 | 6,112 | 5,026 | 7,943 | 3,155 | 7,943 |
| PE | ASIA | 8.01 | 2,843 | 17,392 | 1.18 | 145,753 | 0.21 | 3,990 | -2,364 | 2,962 | 6,188 | 5,134 | 6,062 | 5,134 |
| PE | LONDON | 4.84 | 567 | 14,399 | 0.28 | 221,278 | 0.26 | 3,303 | -656 | -1,057 | 3,009 | 1,106 | 5,000 | 1,106 |
| PE | PRE | 0.93 | -328 | 7,164 | -0.33 | 124,326 | 0.12 | 1,643 | 1,660 | -1,649 | -244 | -2,214 | -345 | -2,214 |
| PE | NY-AM | 4.62 | 2,540 | 14,203 | 1.29 | 71,459 | 0.23 | 3,258 | 3,042 | 1,728 | 2,044 | 9,970 | 1,656 | 9,970 |
| PE | NY-PM | 3.40 | 1,218 | 10,983 | 0.80 | 100,549 | 0.19 | 2,519 | 1,312 | 3,418 | -493 | -4,120 | -691 | -4,120 |
| PE | NY | 8.03 | 3,758 | 18,449 | 1.47 | 105,934 | 0.42 | 4,232 | 4,355 | 5,147 | 1,551 | 5,850 | 964 | 5,850 |
| PE | ALL | 21.80 | 6,840 | 28,047 | 1.76 | 158,786 | 1.00 | 6,434 | 2,994 | 5,403 | 10,504 | 9,876 | 11,681 | 9,876 |
| PBS | ASIA | 7.64 | 4,335 | 34,807 | 0.90 | 330,424 | 0.31 | 7,984 | 2,384 | -3,183 | 12,370 | 10,999 | 16,408 | 10,999 |
| PBS | LONDON | 5.56 | 2,869 | 27,080 | 0.76 | 315,921 | 0.21 | 6,212 | 4,250 | -452 | 5,246 | 1,282 | 11,333 | 1,282 |
| PBS | PRE | 1.51 | 458 | 14,743 | 0.22 | 158,303 | 0.02 | 3,382 | -1,457 | -612 | 2,083 | 7,833 | -3,248 | 7,833 |
| PBS | NY-AM | 7.00 | 2,933 | 27,748 | 0.76 | 199,412 | 0.27 | 6,365 | 4,340 | 1,565 | 2,077 | 12,457 | 2,223 | 12,457 |
| PBS | NY-PM | 5.40 | -447 | 21,148 | -0.15 | 351,870 | 0.19 | 4,851 | -2,830 | -1,057 | 1,311 | 5,066 | 5,418 | 5,066 |
| PBS | CLOSE | 0.07 | -198 | 2,994 | -0.48 | 41,351 | -0.00 | 687 | -931 | -92 | 221 | 0 | 433 | 0 |
| PBS | NY | 12.40 | 2,487 | 36,169 | 0.50 | 492,749 | 0.46 | 8,297 | 1,510 | 508 | 3,388 | 17,523 | 7,641 | 17,523 |
| PBS | ALL | 27.17 | 9,950 | 65,238 | 1.10 | 612,705 | 1.00 | 14,965 | 5,757 | -3,830 | 23,307 | 37,637 | 32,567 | 37,637 |
| MV | ASIA | 8.98 | 4,340 | 37,397 | 0.84 | 277,417 | 0.31 | 8,578 | -2,421 | 5,060 | 7,490 | 12,648 | -3,585 | 12,648 |
| MV | LONDON | 6.36 | 1,704 | 28,323 | 0.43 | 214,425 | 0.08 | 6,497 | -1,862 | 4,016 | 3,158 | -8,968 | 11,784 | -8,968 |
| MV | PRE | 2.18 | -1,012 | 17,159 | -0.43 | 395,615 | 0.13 | 3,936 | -100 | -4,310 | 660 | 7,766 | -1,985 | 7,766 |
| MV | NY-AM | 9.89 | 4,852 | 35,278 | 0.99 | 336,741 | 0.24 | 8,092 | -3,793 | 9,204 | 4,986 | 19,807 | 2,410 | 19,807 |
| MV | NY-PM | 7.26 | -1,009 | 25,866 | -0.28 | 367,827 | 0.25 | 5,933 | -6,026 | -438 | 591 | 12,757 | -1,942 | 12,757 |
| MV | CLOSE | 0.08 | -76 | 3,177 | -0.17 | 30,100 | -0.01 | 729 | -151 | -236 | 217 | -742 | -7 | -742 |
| MV | NY | 17.15 | 3,843 | 42,988 | 0.64 | 561,034 | 0.49 | 9,861 | -9,820 | 8,766 | 5,577 | 32,564 | 468 | 32,564 |
| MV | ALL | 34.74 | 8,799 | 62,572 | 1.01 | 666,701 | 1.00 | 14,353 | -14,354 | 13,297 | 17,103 | 43,269 | 6,675 | 43,269 |
| MA | ASIA | 4.58 | 2,369 | 26,438 | 0.65 | 233,507 | 0.40 | 6,065 | 2,558 | 2,212 | 1,264 | 11,499 | -5,484 | 11,499 |
| MA | LONDON | 3.11 | 3,464 | 20,980 | 1.19 | 138,108 | 0.11 | 4,812 | -877 | 2,758 | 7,450 | 1,549 | 10,751 | 1,549 |
| MA | PRE | 0.70 | -856 | 10,422 | -0.59 | 199,410 | 0.09 | 2,391 | -672 | -2,111 | 204 | -33 | 937 | -33 |
| MA | NY-AM | 3.12 | 2,939 | 21,686 | 0.98 | 124,308 | 0.22 | 4,974 | 2,212 | 4,689 | 1,804 | 1,250 | 4,650 | 1,250 |
| MA | NY-PM | 2.31 | 1,334 | 16,578 | 0.58 | 241,611 | 0.18 | 3,803 | 128 | 3,135 | 455 | 591 | 5,870 | 591 |
| MA | CLOSE | 0.17 | -78 | 4,477 | -0.12 | 72,801 | -0.00 | 1,027 | 865 | -269 | -586 | 0 | -239 | 0 |
| MA | NY | 5.43 | 4,273 | 27,313 | 1.13 | 275,665 | 0.40 | 6,265 | 2,340 | 7,824 | 2,260 | 1,841 | 10,520 | 1,841 |
| MA | ALL | 14.01 | 9,173 | 47,524 | 1.39 | 323,690 | 1.00 | 10,901 | 4,215 | 10,413 | 10,592 | 14,856 | 16,485 | 14,856 |
| DN | ASIA | 5.59 | 6,676 | 27,068 | 1.78 | 181,976 | 0.36 | 6,209 | -361 | 6,042 | 9,368 | 31,998 | 6,949 | 31,998 |
| DN | LONDON | 4.29 | 2,266 | 23,174 | 0.71 | 195,536 | 0.24 | 5,316 | 1,525 | 5,320 | -1,669 | 14,102 | 614 | 14,102 |
| DN | PRE | 1.11 | 1,204 | 11,477 | 0.76 | 235,187 | 0.04 | 2,633 | 288 | -1,732 | 4,450 | 4,029 | 2,202 | 4,029 |
| DN | NY-AM | 4.85 | 3,413 | 26,681 | 0.92 | 222,265 | 0.28 | 6,120 | 350 | 7,335 | 1,950 | 462 | -638 | 462 |
| DN | NY-PM | 2.15 | 1,856 | 15,319 | 0.87 | 222,586 | 0.08 | 3,514 | 1,662 | 748 | 2,670 | 5,102 | 7,641 | 5,102 |
| DN | NY | 6.99 | 5,269 | 30,399 | 1.25 | 183,253 | 0.36 | 6,973 | 2,012 | 8,083 | 4,620 | 5,564 | 7,004 | 5,564 |
| DN | ALL | 17.98 | 15,415 | 49,072 | 2.27 | 219,235 | 1.00 | 11,256 | 3,464 | 17,714 | 16,769 | 55,694 | 16,768 | 55,694 |
| CR | ASIA | 4.89 | -496 | 11,843 | -0.30 | 190,066 | 0.26 | 2,717 | 834 | -579 | -1,055 | -3,300 | -4,996 | -3,300 |
| CR | LONDON | 5.70 | -433 | 9,712 | -0.32 | 175,348 | 0.23 | 2,228 | 1,163 | -1,685 | 32 | -3,712 | 1,682 | -3,712 |
| CR | PRE | 1.56 | 785 | 7,937 | 0.71 | 51,285 | 0.03 | 1,821 | -109 | 740 | 1,774 | -1,996 | 1,000 | -1,996 |
| CR | NY-AM | 3.76 | -1,879 | 12,713 | -1.07 | 303,737 | 0.36 | 2,916 | -2,147 | -34 | -3,210 | -4,056 | -3,104 | -4,056 |
| CR | NY-PM | 2.17 | 570 | 11,237 | 0.37 | 140,042 | 0.12 | 2,578 | -644 | 2,268 | -501 | 2,719 | -264 | 2,719 |
| CR | NY | 5.93 | -1,310 | 17,317 | -0.55 | 266,773 | 0.48 | 3,972 | -2,791 | 2,234 | -3,711 | -1,337 | -3,368 | -1,337 |
| CR | ALL | 18.09 | -1,453 | 24,700 | -0.42 | 304,351 | 1.00 | 5,666 | -903 | 710 | -2,960 | -10,345 | -5,682 | -10,345 |

B3 (dip-buy basket F19, unit) and RSI2T enter 15:55-15:56 ET = 100% CLOSE (library locked daily series, exit-day attribution): B3 ALL +2,222/wk (SD 10,970, Sharpe 1.0, maxDD 103,511, 3.4 tr/wk, MDE 2,516; PRE +1,258, HOLD +4,866, X +1,840; years 2023 +2,218, 2024 +464, 2025 +3,332, 2026 +7,232); RSI2T ALL +484/wk (SD 2,669, 0.5 tr/wk, MDE 612; PRE +500, HOLD +949, X +98). No block cell for either (a block deletes the book). Their entire P&L sits in a session the stack does not trade.

## Plain line per book (which session carries, which loses, does blocking the loser help HOLD)
- **ST**: carries NY-AM (HOLD +10.3k) and ASIA (+3.1k all, W20 share 0.41); no session loses on PRE or ALL (min PRE-LONDON +1.2k); PRE session is thin (79 PRE trades). No block cell.
- **HM**: carried by ASIA (+5.7k ALL, +12.1k HOLD); loses PRE (-1.2k ALL, 0.64 tr/wk, <100 PRE trades) and NY-PM (-0.8k ALL, -3.7k HOLD). PRE-chosen block NY-PM (entries 12:00-15:00): PRE +471, HOLD +3,699 [-1,645, +8,803], X -738, 2024 -3,981; NOT-CONFIRMED (not PRE-significant); exact placebo rank 0.44 (first-order 0.99).
- **WT**: carried by ASIA (+2.7k); loses NY-PM (-1.8k ALL, Sharpe -1.28, -4.4k HOLD). Block NY-PM: the closest cell above (HOLD +4,422 [+1,286, +7,412], all four years +, placebo 0.965; fails PRE-significance only).
- **KB**: works across sessions: ASIA +2.6k (W20 share 0.50), NY-AM +2.0k, NY-PM +2.0k, LONDON +1.7k; no losing session on PRE or ALL (PRE -87 on 0.8 tr/wk). No block cell. Carrier KB ASIA and KB NY-PM are SESSION-CANDIDATE.
- **SM**: carried by ASIA (+2.5k) and NY-AM (+1.2k); NY-PM -188 (<100 PRE trades). No block cell (PRE-worst session PRE has 36 PRE trades).
- **PE**: carried by ASIA (+2.8k, HOLD +6.1k) and NY-AM (+2.5k); LONDON is PRE-worst (-900 PRE) but +567 ALL and +4.4k in HOLD, so blocking it HURTS HOLD (-7,455 [-12,761, -1,715]; placebo rank 0.15). NOT-CONFIRMED. Carrier PE ASIA is SESSION-CANDIDATE (HOLD +6,078 [+114, +12,012], p 0.023; X -1,985).
- **PBS**: (PB_ST10_SWZ_T3, pre-lock rows) earns ASIA/LONDON/NY-AM; NY-PM -447 ALL but +5.5k in HOLD, so blocking NY-PM costs -5,521 in HOLD (X +1,842, PRE +2,163). NOT-CONFIRMED; basis weak.
- **MV**: (TR1A, pre-lock) carried by NY-AM (+4.9k) and ASIA (+4.3k); loses PRE (-1.0k ALL, 2.2 tr/wk) and NY-PM (-1.0k). PRE-chosen block 08:30-09:30: PRE +1,854, HOLD +219 (2026 -7,766), X +107; NOT-CONFIRMED. Carrier MV NY-AM SESSION-CANDIDATE (HOLD +5,747, X -5,676).
- **MA**: (TR1C MAMA, pre-lock) positive in all but PRE (-856); no block cell (PRE-lowest session has only 61 PRE trades).
- **DN**: (TR3 Donchian, mapped) positive everywhere on ALL; carried by ASIA (+6.7k) and NY-AM (+3.4k). NY-PM is PRE-worst (-688) but +7.4k in HOLD: block costs -7,404 [-12,235, -2,385], rank 0.008. Carrier DN ASIA SESSION-CANDIDATE (HOLD +11,863 [+1,371, +22,370], p 0.011, X +1,987, 2023 -361).
- **CR**: (CRT, conservative mapped) loses overall (-1.5k/wk ALL); loses NY-AM (-1.9k, Sharpe -1.07) and ASIA/LONDON (-0.5k, -0.4k); only PRE (+785) and NY-PM (+570) earn. PRE-chosen block LONDON: PRE +1,506, HOLD -724, X -574; NOT-CONFIRMED.
- **Basket B3 / RSI2T**: 100% CLOSE; B3 +2.2k/wk, RSI2T +0.5k/wk.

## Table 3 - the 7 PRE-chosen block cells (stack books: exact lock engine, stack $; Sim books: first-order, own $)
| book | blocked session (ET entry) | blocked tr/wk | PRE delta [CI] | HOLD delta [CI] | HOLD MDE | X delta | 2023/2024/2025/2026 | HOLD 2025H2 / 2026 | placebo rank HOLD (exact; first-order) | X rank | tier | failed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HM | NY-PM 12:00-15:00 | 3.10 | 471 [-3,288, 4,115] | 3,699 [-1,645, 8,803] | 7,690 | -738 | 673/-3,981/5,387/3,397 | 3,629 / 3,397 | 0.44; 0.99 | 0.73 | NOT-CONFIRMED | not PRE-significant |
| WT | NY-PM 12:00-15:00 | 4.64 | 1,340 [-1,215, 3,863] | 4,422 [1,286, 7,412] | 4,444 | 714 | 825/1,070/2,537/8,341 | 3,387 / 8,341 | 0.97; 1.00 | 0.80 | NOT-CONFIRMED | not PRE-significant |
| PE | LONDON 02:00-08:30 | 4.84 | -428 [-4,320, 3,369] | -7,455 [-12,761, -1,715] | 8,112 | 914 | 1,739/604/-5,571/-5,842 | -7,537 / -5,842 | 0.15; 0.18 | 0.96 | NOT-CONFIRMED | not PRE-significant, HOLD<=0, HOLD2025<=0, HOLD2026<=0 |
| MV | PRE 08:30-09:30 | 2.18 | 1,854 [-2,145, 5,884] | 219 [-6,487, 6,938] | 9,544 | 107 | 100/4,310/-660/-7,766 | 1,985 / -7,766 | 0.81; 0.81 | 0.29 | NOT-CONFIRMED | not PRE-significant, HOLD2026<=0 |
| DN | NY-PM 12:00-15:00 | 2.15 | 688 [-2,854, 4,141] | -7,404 [-12,235, -2,385] | 7,203 | -2,073 | -1,662/-748/-2,670/-5,102 | -7,641 / -5,102 | 0.01; 0.01 | 0.41 | NOT-CONFIRMED | not PRE-significant, HOLD<=0, HOLD2025<=0, HOLD2026<=0 |
| CR | LONDON 02:00-08:30 | 5.70 | 1,506 [-833, 3,704] | -724 [-4,613, 2,984] | 5,553 | -574 | -1,163/1,685/-32/3,712 | -1,682 / 3,712 | 0.11; 0.11 | 0.19 | NOT-CONFIRMED | not PRE-significant, HOLD<=0, HOLD2025<=0 |
| PBS | NY-PM 12:00-15:00 | 5.40 | 2,163 [-2,905, 7,138] | -5,521 [-12,650, 1,516] | 10,156 | 1,841 | 2,830/1,057/-1,311/-5,066 | -5,418 / -5,066 | 0.56; 0.56 | 0.77 | NOT-CONFIRMED | not PRE-significant, HOLD<=0, HOLD2025<=0, HOLD2026<=0 |

F for best-of-F = 11 books x 6 sessions = 66 (threshold p <= 0.05/66 = 0.00076, a LABEL, not a gate). Placebo = 287 five-minute circular shifts of the whole six-window grid, each re-selected on PRE by the same rule (valid draws 123-287 per book; neighbouring shifts are correlated). Stack-book delta SD/maxDD/worst-week (HOLD, base -> cell): HM NY-PM SD 151,891 -> 149,583, maxDD 601,016 -> 574,002, worst -318,557 -> -298,087; WT NY-PM 151,891 -> 151,633, 601,016 -> 601,882, -318,557 -> -326,760; PE LONDON 151,891 -> 147,673, 601,016 -> 579,763, -318,557 -> -316,137 (but the mean falls 7.5k). Worst-20 weeks $ fixed on PRE (PRE window): HM -2,305k -> -2,201k, WT -2,305k -> -2,176k, PE -2,305k -> -2,271k. Trade-off line (WT NY-PM, ALL): +1,835/wk mean; blocking gives up the good-week NY-PM entries and saves the bad-week ones; net worst-20 +102k over 149 weeks.

## Table 4 - the 7 carrier cells (PRE-significant session; own $ for MV/DN, stack $ for KB/PE)
| book | session | PRE mean [CI] | PRE MDE | HOLD mean [CI] | HOLD MDE | HOLD p(<=0) | X (2023 span) | 2023/2024/2025/2026 | HOLD 2025H2 / 2026 | tier (best-of-F label) |
|---|---|---|---|---|---|---|---|---|---|---|
| KB | ASIA 18:00-02:00 | 4,272 [184, 8,550] | 5,953 | 2,810 [-1,751, 7,571] | 6,916 | 0.112 | -652 [-6,377, 4,858] | -1,238/3,297/3,716/9,713 | 1,172 / 9,713 | SESSION-CANDIDATE (not best-of-F) |
| KB | NY-PM 12:00-15:00 | 3,608 [1,295, 5,983] | 3,412 | 569 [-2,360, 3,425] | 4,099 | 0.343 | 363 [-3,611, 4,524] | -1,138/5,101/1,482/37 | 666 / 37 | SESSION-CANDIDATE (not best-of-F) |
| PE | ASIA 18:00-02:00 | 4,219 [246, 8,331] | 5,837 | 6,078 [114, 12,012] | 8,672 | 0.023 | -1,985 [-6,356, 2,342] | -2,364/2,962/6,188/5,134 | 6,062 / 5,134 | SESSION-CANDIDATE (not best-of-F) |
| MV | ASIA 18:00-02:00 | 9,877 [1,638, 18,126] | 11,786 | -653 [-17,073, 15,672] | 24,076 | 0.530 | -1,664 [-9,520, 6,058] | -2,421/5,060/7,490/12,648 | -3,585 / 12,648 | NOT-CONFIRMED (HOLD<=0, HOLD2025<=0) |
| MV | NY-AM 09:30-12:00 | 10,517 [1,819, 18,919] | 12,242 | 5,747 [-7,440, 17,569] | 18,164 | 0.176 | -5,676 [-13,383, 2,122] | -3,793/9,204/4,986/19,807 | 2,410 / 19,807 | SESSION-CANDIDATE (not best-of-F) |
| DN | ASIA 18:00-02:00 | 7,035 [1,169, 13,065] | 8,629 | 11,863 [1,371, 22,370] | 15,196 | 0.011 | 1,987 [-5,225, 8,747] | -361/6,042/9,368/31,998 | 6,949 / 31,998 | SESSION-CANDIDATE (not best-of-F) |
| DN | NY-AM 09:30-12:00 | 7,520 [1,787, 13,137] | 8,167 | -452 [-10,289, 9,671] | 14,512 | 0.536 | -933 [-8,359, 6,869] | 350/7,335/1,950/462 | -638 / 462 | NOT-CONFIRMED (HOLD<=0, HOLD2025<=0) |

Per the user's rule none of the pooled all-hours verdicts is applied to these cells; best-of-F is printed beside the tier. CANDIDATE lots = half of PASS lots in any portfolio line. HOLD 2026 is 5-6 weeks (noisy). MDEs exceed most effects: HOLD is 32 weeks.

## Live-eligible block lines
**None.** No block cell reached SESSION-CANDIDATE (all fail PRE-significance; the stack-book cells that have HOLD > 0 are HM NY-PM and WT NY-PM). For the record, the lines that would apply if the user chose to carry the nearest cell anyway (NOT a scored result, listed so the choice is explicit):
- WT only: no new WT entries with entry time 12:00:00-14:59:59 ET (entry bar 11:59-14:58). HOLD +4,422/wk, placebo 0.965 (passes the 0.95 line), best-of-F not cleared, PRE-insignificant. Sizing: half lots equivalent.
- Registered as watch only; nothing for ST, KB, SM, PE, MV, MA, DN, CR, PBS.
Session-book candidates (restrict a book to its session; SESSION-CANDIDATE, half lots, forward-register eligible regardless of best-of-F): PE entry 18:00-02:00 ET (flat per the existing bracket); DN entry 18:00-02:00 ET; KB entry 18:00-02:00 ET; KB entry 12:00-15:00 ET; MV entry 09:30-12:00 ET. Note these restrict the book to the carrier window and remove the rest of the book; the other sessions of KB/PE/DN/MV were not negative, so the restriction is not supported by this table as an improvement of the book, only as 'this session earned on PRE and HOLD'.

## Not scored / no trade rows
PB as a separate book: the directive's PB equals the stack's PE (PB3B_R5_P1); the other pullback cell PBS is scored on pre-lock mapped rows. B3 and RSI2T: daily library series only (no per-trade P&L rows loaded; entries all 15:55-15:56 ET). MV, MA, PBS trade rows are pre-lock (lock engine not re-run for them), CR is on the conservative mapped basis (plain-mapped CR_map is the optimistic reference, not scored). The 'basket' means B3_F19 (NQ+ES+RTY).

## Disclosures
- Smoke tests before the prereg printed only structure, row counts, engine run times and session ENTRY COUNTS (audit table vs engine rows: the engine counts are ~4% higher because the engine window starts 2023-02-10 vs the audit's 2023-04-03); no session P&L was seen. The audit trade table was read in full (it extends to 2026-10-16) and cut at 2026-02-06 at load; nothing after the cut was summarised.
- 'Effect vs own placebo' for carrier PRE-significance is the weekly-bootstrap CI of the session mean in net $ (not a random-direction placebo; stack trades have no replayable direction flip); the shifted-session placebo is applied to the block cells only.
- Exact vs first-order: for HM the exact and first-order HOLD deltas coincide (+3,699) but the exact placebo rank (0.44) differs from the first-order rank (0.99) because the shifted windows interact with the busy chain; the exact rank is primary.
- Week bucket straddles (2024-01-29 and 2025-06-30) count only in-window days, as in the vs_lib convention. 32 HOLD weeks cap power.
