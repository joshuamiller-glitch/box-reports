# DS3_BLOCKRULES - window / block rule changes on the DS2+DS3 stack (D3BK, directive item D), 2026-10-28
Research only; nothing live. Prereg sha256 34bdcd9bc28b76cc288f33b985f3e43e... (l2vast/ds3/prereg/BLOCKRULES_prereg.md, DECISIONS.md), 28 cells in 6 groups, one logged holdout look per group (DS3_BLOCKRULES_GA..GX, pre text WFPRE-only out/bk/bk_prehold.txt). Fees 4.84 RT NQ. Code l2vast/ds3/code/bk/ (bk_lib, bk_cells, bk_score); rows/series l2vast/ds3/out/bk/ (rows.pkl, series.pkl).

## Verdict
**No window change is supported: 0 SUPPORTED, 0 LEAD, 0 WEAK, 28 DEAD (not one cell has a WFPRE paired CI of d_mean above 0).** Single best-supported (prereg tie-break: most gates, then WFPRE d_Sharpe CI lower bound) = **E_fomc, the FOMC-day NY entry block (signal bar 09:30-15:30 ET on the 32 FOMC dates), all six books**: WF weekly deltas R basis mean +1,111 [95% CI -940, +3,414], SD -349, maxDD +0, worst week +0, Sharpe +0.065; S basis mean +1,239 [-520, +3,194], SD -130, maxDD +0, worst +0. Same sign in HOLD (+969), 2023-04..2024-01 (+959), 2024/2025/2026 (+1,166, +604, +1,632), 2x cost (+1,415); but it is 0.35 x MDE (+3,209), the CI includes 0, the effect lives on 21 FOMC days in WF (12 positive / 9 negative days, mean +8,377/day, day-bootstrap CI [-4,378, +20,635]) and the shifted-window placebo is not applicable in spirit (rank 0.68). It does not meet LEAD (g1, g2 and g4 fail) and is not a recommendation; ~703 forward weeks to settle on S, i.e. never in practice (21 events/2.7 y).

Headline answers to the directive's questions (all WF = 2024-02..2026-10-16, 142 weeks, paired by week vs the live windows; R = regenerated busy-correct rows, S = books.pkl rows with the mask changed):
- **(a) un-block 09:30-09:59, all books** (A_all6): R +3,084/wk [-4,395, +10,371], MDE 10,428, d_Sh +0.12, d_SD +2,478, d_maxDD +76,503, d_worst +47,425; S +5,844/wk, d_Sh +0.22, d_maxDD +23,231, d_worst +66,959; HOLD R +2,121, X R +4,638, years +3,091, +6,459, -1,328; placebo rank 0.97; tier DEAD
- **(a) same without WT** (A_all5): R +2,627/wk [-4,036, +9,072], MDE 9,313, d_Sh +0.10, d_SD +2,256, d_maxDD -9,407, d_worst +44,948; S +5,214/wk, d_Sh +0.20, d_maxDD +4,068, d_worst +66,959; HOLD R +723, X R +3,931, years +3,951, +5,207, -2,300; placebo rank 0.97; tier DEAD
- **(b) un-block 09:00-09:29** (B_all6): R -451/wk [-4,145, +3,192], MDE 5,230, d_Sh -0.05, d_SD +1,654, d_maxDD +4,511, d_worst +0; S -709/wk, d_Sh -0.08, d_maxDD +48,631, d_worst +21,646; HOLD R +611, X R +723, years -6,186, +4,046, +588; placebo rank 0.24; tier DEAD
- **(a+b) whole 09:00-09:59** (AB_all6): R +3,133/wk [-4,439, +10,922], MDE 11,238, d_Sh +0.06, d_SD +5,540, d_maxDD +148,402, d_worst +46,484; S +3,693/wk, d_Sh +0.05, d_maxDD +183,140, d_worst +69,782; HOLD R +1,738, X R +4,227, years +659, +8,866, -1,365; placebo rank 0.92; tier DEAD
- **(c) un-block 15:00-16:54 (flat 16:55)** (C_all5): R -2,354/wk [-5,053, +390], MDE 4,048, d_Sh -0.13, d_SD +138, d_maxDD -15,249, d_worst +216; no S basis (rows absent); HOLD R -106, X R -1,447, years -4,563, -1,865, -283; placebo rank 0.11; tier DEAD
- **(d) 18:00-18:04 block OFF, all books** (D_all6): R +1,325/wk [-5,906, +8,536], MDE 10,379, d_Sh -0.06, d_SD +7,542, d_maxDD +71,556, d_worst -16,051; S +1,610/wk, d_Sh -0.07, d_maxDD +95,257, d_worst -12,637; HOLD R -2,378, X R -4,504, years +4,274, +2,222, -3,311; placebo rank 0.97; tier DEAD
- **(e) FOMC-day NY block** (E_fomc): R +1,111/wk [-940, +3,414], MDE 3,209, d_Sh +0.07, d_SD -349, d_maxDD +0, d_worst +0; S +1,239/wk, d_Sh +0.07, d_maxDD +0, d_worst +0; HOLD R +969, X R +959, years +1,166, +604, +1,632; placebo rank 0.68; tier DEAD
- Reading: the open-harness +5.8k/wk for 09:30-09:59 reproduces exactly on the S basis (A_all6 S WF +5,844; live30 50,711 vs live 44,867) and the extra Sharpe (+0.22) is real in the point estimate, but the paired CI [-1.3k, +12.7k] contains 0 (MDE 10.4k), the R basis shows +3.1k, 2026 is negative (-1.3k R), and it buys extra SD (+4.5k) and maxDD (+23k S / +77k R); it is not supported at any gate that matters. Un-blocking 15:00-16:54 is a loss (R -2,354/wk, WT -1,520 and SM -1,004 individually significant: CI above/below 0), consistent with D3CL1 (-2,141). 09:00-09:29 alone is slightly negative (-451 R all six, -872 R five books; S -709). The 18:00-18:04 block: all-books off is +1.3k..+1.6k with SD +7.5k..+9.0k and Sharpe -0.06..-0.07: a noisy wash; per book the signs conflict (ST +2.8k R but -0.4k S, KB -2.3k).

## Cells (28), WF unless noted. Delta vs live; R = regenerated rows, S = books.pkl masks. CI = paired weekly bootstrap (1000 draws). MDE = 2.8 SD(weekly diff)/sqrt(142).
| cell | R WFPRE d_mean | R WF d_mean [CI] | MDE | R d_SD | R d_maxDD | R d_worst | R d_Sh | R HOLD | R X(2023-04..24-01) | R 2024 / 2025 / 2026 | R 2x-cost | S WF [HOLD] | placebo rank (WFPRE / WF) | gates passed | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_ST | +1,966 | +1,780 [-2,122, +6,141] | +5,817 | +4,032 | -2,820 | +18,005 | +0.022 | +1,549 | +346 | +5,359 / -2,146 / +2,476 | +1,278 | +3,121 [+1,196] | 0.95 / 0.89 | 4 | DEAD |
| A_HM | +1,796 | +1,197 [-1,595, +3,646] | +3,912 | -578 | +2,719 | +12,187 | +0.074 | +520 | -318 | -704 / +6,309 / -3,092 | +1,620 | +1,777 [+1,377] | 0.74 / 0.79 | 4 | DEAD |
| A_KB | +379 | -623 [-2,528, +1,057] | +2,493 | -1,539 | +16,687 | +2,281 | -0.006 | -1,718 | +1,434 | -916 / -746 / -96 | -675 | +93 [-1,163] | 0.53 / 0.37 | 3 | DEAD |
| A_SM | +123 | +849 [-418, +2,218] | +2,028 | -214 | -33,901 | +9,180 | +0.049 | +1,636 | +1,028 | +140 / +2,087 / +72 | +883 | +800 [+1,636] | 0.24 / 0.53 | 5 | DEAD |
| A_PB | +53 | -577 [-2,534, +1,662] | +2,891 | -755 | -5,767 | +5,771 | -0.017 | -1,263 | +1,443 | +72 / -297 / -1,659 | -1,510 | -577 [-1,263] | 0.26 / 0.26 | 1 | DEAD |
| A_all5 | +4,317 | +2,627 [-4,036, +9,072] | +9,313 | +2,256 | -9,407 | +44,948 | +0.097 | +723 | +3,931 | +3,951 / +5,207 / -2,300 | +1,596 | +5,214 [+1,783] | 0.97 / 0.97 | 5 | DEAD |
| A_all6 | +3,917 | +3,084 [-4,395, +10,371] | +10,428 | +2,478 | +76,503 | +47,425 | +0.117 | +2,121 | +4,638 | +3,091 / +6,459 / -1,328 | +2,139 | +5,844 [+3,682] | 0.97 / 0.97 | 5 | DEAD |
| B_all5 | -1,525 | -872 [-4,275, +2,534] | +4,779 | +1,261 | +4,511 | +0 | -0.068 | -139 | +573 | -5,405 / +2,850 / -239 | -1,048 | -969 [-1,300] | 0.21 / 0.21 | 1 | DEAD |
| B_all6 | -1,407 | -451 [-4,145, +3,192] | +5,230 | +1,654 | +4,511 | +0 | -0.053 | +611 | +723 | -6,186 / +4,046 / +588 | -647 | -709 [-675] | 0.21 / 0.24 | 2 | DEAD |
| AB_all5 | +4,547 | +2,828 [-4,097, +9,731] | +9,980 | +4,891 | +19,808 | +37,531 | +0.060 | +890 | +5,107 | +1,852 / +7,390 / -1,926 | +2,233 | +3,199 [-630] | 0.95 / 0.89 | 4 | DEAD |
| AB_all6 | +4,356 | +3,133 [-4,439, +10,922] | +11,238 | +5,540 | +148,402 | +46,484 | +0.064 | +1,738 | +4,227 | +659 / +8,866 / -1,365 | +2,736 | +3,693 [+559] | 0.95 / 0.92 | 4 | DEAD |
| C_ST | +204 | +334 [-796, +1,538] | +1,816 | +446 | -13,554 | +3,180 | +0.010 | +473 | +1,126 | +222 / +887 / -248 | +131 | n/a | 0.33 / 0.22 | 4 | DEAD |
| C_HM | -1,335 | -417 [-1,736, +841] | +1,946 | -246 | -1,542 | +1,047 | -0.018 | +601 | -1,770 | -1,829 / -543 / +1,409 | -679 | n/a | 0.22 / 0.22 | 2 | DEAD |
| C_WT | -2,372 | -1,520 [-2,444, -649] | +1,239 | -560 | +384 | -1,787 | -0.071 | -559 | -122 | -2,867 / -1,055 / -465 | -1,446 | n/a | 0.11 / 0.11 | 0 | DEAD |
| C_KB | -245 | +252 [-447, +945] | +996 | -31 | +0 | +0 | +0.014 | +797 | -256 | -127 / +145 / +819 | +55 | n/a | 0.22 / 0.22 | 3 | DEAD |
| C_SM | -615 | -1,004 [-1,911, -44] | +1,364 | +200 | -538 | -1,484 | -0.057 | -1,418 | -424 | +38 / -1,299 / -1,799 | -1,163 | n/a | 0.22 / 0.11 | 1 | DEAD |
| C_all5 | -4,362 | -2,354 [-5,053, +390] | +4,048 | +138 | -15,249 | +216 | -0.127 | -106 | -1,447 | -4,563 / -1,865 / -283 | -3,100 | n/a | 0.11 / 0.11 | 1 | DEAD |
| D_ST | +2,955 | +2,793 [-1,492, +7,381] | +6,429 | +1,401 | +48,267 | -1,565 | +0.122 | +2,574 | +1,029 | +3,886 / +510 / +4,267 | +2,414 | -364 [-3,502] | 1.00 / 0.30 | 6 | DEAD |
| D_HM | +1,384 | +233 [-3,247, +3,564] | +4,799 | +3,638 | +990 | -34,242 | -0.051 | -1,039 | -3,459 | +2,369 / -9 / -1,963 | +812 | +1,695 [+2,298] | 0.90 / 1.00 | 2 | DEAD |
| D_WT | +1,502 | +617 [-1,469, +2,898] | +3,043 | -192 | +7,539 | -10,185 | +0.036 | -368 | +521 | -993 / +3,800 / -1,550 | +215 | +1,335 [+574] | 1.00 / 0.95 | 4 | DEAD |
| D_KB | -1,712 | -2,285 [-4,772, +24] | +3,569 | +734 | +14,807 | -16,203 | -0.133 | -2,884 | -840 | -752 / -2,721 / -3,416 | -2,468 | -1,022 [-2,527] | 0.60 / 0.05 | 1 | DEAD |
| D_PB | +536 | -34 [-1,788, +1,839] | +2,558 | +1,122 | -48 | +48 | -0.022 | -661 | -1,757 | -237 / +643 / -649 | -251 | -34 [-661] | 0.65 / 0.47 | 0 | DEAD |
| D_all6 | +4,664 | +1,325 [-5,906, +8,536] | +10,379 | +7,542 | +71,556 | -16,051 | -0.061 | -2,378 | -4,504 | +4,274 / +2,222 / -3,311 | +722 | +1,610 [-3,818] | 1.00 / 0.97 | 4 | DEAD |
| E_fomc | +1,225 | +1,111 [-940, +3,414] | +3,209 | -349 | +0 | +0 | +0.065 | +969 | +959 | +1,166 / +604 / +1,632 | +1,415 | +1,239 [+1,387] | 0.47 / 0.68 | 6 | DEAD |
| E_fomc_pm | -43 | +14 [-1,434, +1,422] | +2,036 | -891 | +0 | +0 | +0.017 | +77 | +559 | +54 / -719 / +891 | +235 | +164 [+354] | 0.24 / 0.37 | 5 | DEAD |
| E_fomc_2d | +562 | -348 [-2,516, +1,589] | +2,956 | -2,493 | +0 | +0 | +0.027 | -1,347 | -257 | +462 / -1,651 / +367 | -17 | -208 [-826] | 0.37 / 0.32 | 1 | DEAD |
| X_A6_D | +6,981 | +3,869 [-6,391, +14,378] | +14,266 | +8,871 | +60,701 | +8,573 | +0.044 | +380 | -2,921 | +5,460 / +6,807 / -1,879 | +803 | +6,544 [+93] | 0.97 / 0.97 | 4 | DEAD |
| X_AB6_D | +6,156 | +3,074 [-7,702, +14,560] | +15,114 | +10,965 | +59,878 | +1,156 | -0.030 | -370 | -4,311 | +3,228 / +5,259 / -8 | +1,333 | +4,174 [-1,724] | 0.97 / 0.92 | 3 | DEAD |

## Per-book contribution to the stack delta (WF, R basis, $/wk)
- A_all6: ST +1,780, HM +1,197, WT +458, KB -1,463, SM +1,177, PB -1,499
- B_all6: ST -677, HM -276, WT +421, KB -1,089, SM -159, PB +1,129
- AB_all6: ST +1,177, HM +1,446, WT +305, KB -1,875, SM +1,104, PB -365
- C_all5: ST +334, HM -417, WT -1,520, KB +723, SM -1,655, PB +0
- D_all6: ST +2,793, HM +233, WT +617, KB -5,680, SM +0, PB -9
- E_fomc: ST +456, HM +272, WT +236, KB +150, SM +582, PB -413

## Placebo = shifted windows (S basis; contribution of the live entries inside each same-length window at other times of day, WFPRE $/wk)
- length 5 min, 40 windows: mean +177, SD 776, p95 +1,295, max +1,729, min -1,688
- length 30 min, 38 windows: mean +1,163, SD 3,130, p95 +4,542, max +12,571, min -7,625
- length 114 min, 9 windows: mean +3,775, SD 5,710, p95 +11,303, max +11,394, min -5,377
- Reading: the 09:30-09:59 window's gain (WFPRE S basis +8.3k all-5, rank 0.97) is the top of the 30-min distribution but not above it by more than one window in 38 (the 18:05-18:35 window is +12.6k); the 5-min 18:00-18:04 gain ranks 1.00 only because 5-min windows contribute +-1.7k at most. Caveat: NY-open windows have higher volatility than most placebo windows, so rank 0.97 is not evidence of timing skill; and shifted-window ranks compare a window's total contribution, not an incremental edge test.

## Method, identities, bases
- Regeneration (R): ST, HM, WT, KB(TE7_kelt3m_n14_m1.0), SM(TE6_st10m_n7_m3.0) entry rows regenerated on the 1-s path (firmlib.sim_rrt, same sources as asm_lib/te_core/c3_unblock) with a blocked-entry set per config and a correct busy chain. IDENTITY: the config reproducing the old signal gate gives (entry bar, side) sets identical to books.pkl, 0 only-old / 0 only-new for all five books (8309/6311/11641/8593/2397 rows); the lock engine on those rows reproduces the books-live daily series with max abs diff 0.0; S-basis live / live30 / unblocked reproduce the published WF 44,867 / 50,711 / 48,560 exactly.
- Shadowing finding: the published live baseline (books.pkl rows with a post-hoc mask) lets a masked 09:xx / 15:xx / 18:00 trade keep the generator busy, so later live-legal signals are missing. Regenerating with a correct chain gives live R WF 45,947 (+1,080 vs 44,867; ST -3.5k, KB +3.5k, HM +1.7k, WT +1.0k per book vs the masked books, SM and PE 0). Paired deltas use R(cell)-R(live); S(cell)-S(live) is shown beside every cell. Rows whose (entry bar, side) already exist keep their direct / P9 P; new rows are MAPPED (share of rows with existing P by book 89-100%).
- PE (PB3B_R5_P1) was NOT regenerated (no generator in this pipeline): window rows come from books.pkl by mask (09:00-09:59 and 18:00-18:04 rows exist; 15:00-16:54 rows do not exist, so C cells exclude PE), shadowing for PE is uncorrected. WT is mapped (no direct replay). SM has no 18:00-18:04 entries.
- Stack: ST10+HM10+WT7 + frozen monthly inverse-26w-SD weights on KB/SM/PE (a changed book never changes the weights); per-book exact locks (pb win 5R / loss 2R, give-back 2R keep 50%, week floor 12R).
- Replay R4 (direct repricing): NOT run. Reasons: no cell is supported, so there is no best-supported window to reprice; R1 (DN stop-fill) had just started at this writing so R4 is not yet in order; and for A, B, D and E the S basis already uses the books' direct-priced rows (ST/HM P9, KB/SM/PE direct S10x1+XJ3, cover 98-100%), so a replay would only reprice the mapped regen rows. Only the 15:00-16:54 rows are absent from the books (D3CL1 regenerated, mapped).
- Reused, not redone: open harness un-block 09:30-09:59 +5.8k/wk (README_OPEN2) and D3O3 09:30-10:30 +8.4k/wk with worse Sharpe/maxDD (reproduced here on S: +5,844 for 09:30-09:59); D3CL1 15:01-16:54 un-block (-2.1k/wk, WT-driven; here -2.35k with PB not regenerated, WT -1.5k).

## Deviations / limits (disclosed)
- The g9p column in out/bk/bk_prehold.txt (2x cost on WFPRE) is a pre-stage convenience, not a prereg gate; the ranking of the best cell excludes it (prereg g1-g9 only).
- Pre-holdout text and looks as prereg'd; WF windows were not printed before the looks (the pre text has WFPRE only). The series file contains all days; HOLD columns were first read after the log line in DECISIONS.md.
- FOMC list is the maintained 32-date list (DS3_SPEC_TF1); unscheduled meetings are not in it; the filter blocks entries only (open positions managed normally); no entry shadow correction for PE.
- GC S basis not recomputed (rows absent); D3CL1's table is the S-basis reference. C placebo uses 114-min windows (9 windows), a weak distribution.
- Power: weekly MDE for a stack delta is 2.0k (single small book) to 15k/wk (all books); A_all6 needs ~440 forward weeks (S) / ~1,600 (R) to settle; nothing here is detectable in 142 weeks except the losses of C_WT and C_SM.
- Memory/slots: corepool 8 slots, ~110 s for 712 series; no replay workers launched, no worker kills.
