# DS3_PORTFOLIO_SOLVE - T-PORTFOLIO (D3PF, 2026-10-27). Research output only; no live change is recommended, the user decides.
Prereg l2vast/ds3/prereg/T-PORTFOLIO_prereg.md sha256 e97cd0164994d174319bf437adcc29a6334972123bc1e4233e996b8ea4223e23 (DECISIONS.md). Pre-holdout text autopilot/DS3_PORTFOLIO_PREHOLD.md; ONE holdout look logged (track DS3_PORTFOLIO). Code l2vast/ds3/code/pf/, outputs l2vast/ds3/out/portfolio/ (library.pkl, pre_*.json, final.json, alloc/*.json), rows l2vast/ds3/rows/DS3_TPORTFOLIO.json.

## Verdict lines (both objectives, both caps; primary book set ST HM KB SM PE MV MA DN CR_cons B3 RSI2T; no WT)
Format: WF-solved (SELECTION ON THE HOLDOUT, in-sample) | PRE-solved and tested on HOLD (OUT OF SAMPLE, the honest number). Deltas are weekly means vs DS2 10/10/7 (27 lots) and vs DS2+DS3 as running (D3SL, 50 lots); neither comparator is lot-matched to 30/20.

- **Portfolio (max mean s.t. maxDD<=$400k): best allocation under <=30 NQ-eq: {SM 7, PE 5, MV 4, DN 14}, mean $50,440/wk, maxDD $398,660, vs DS2 +24,600 [+9,834, +39,143] (MDE 21,131), vs DS2+DS3 +1,880 [-13,667, +17,395] (MDE 22,161); out-of-sample (PRE-solved {KB 14, MV 2, DN 14}, HOLD-tested): mean $54,932/wk (PRE $56,163), maxDD $713,863 (PRE $316,505), vs DS2 +27,084 [-2,027, +56,638] (MDE 42,133), vs DS2+DS3 +5,724 [-20,787, +33,314] (MDE 39,133); verdicts DEAD (vs DS2) / DEAD (vs DS2+DS3); OOS placebo rank 1.000; WF in-sample placebo rank 1.000 (trivial).**
- **Portfolio (min maxDD s.t. mean>=$30k): best allocation under <=30 NQ-eq: {KB 2, SM 7, MV 3, DN 4, CR_cons 2, B3 2, RSI2T 1}, mean $30,060/wk, maxDD $127,358, vs DS2 +4,220 [-11,153, +19,218] (MDE 21,917), vs DS2+DS3 -18,499 [-38,291, +987] (MDE 27,845); out-of-sample (PRE-solved {KB 6, SM 2, MV 2, MA 3, DN 4, CR_cons 6, B3 1, RSI2T 3}, HOLD-tested): mean $30,759/wk (PRE $30,019), maxDD $280,058 (PRE $105,088), vs DS2 +2,911 [-20,681, +27,574] (MDE 35,141), vs DS2+DS3 -18,448 [-47,011, +10,533] (MDE 41,339); verdicts DEAD (vs DS2) / DEAD (vs DS2+DS3); OOS placebo rank 0.351; WF in-sample placebo rank 1.000 (trivial).**
- **Portfolio (max mean s.t. maxDD<=$400k): best allocation under <=20 NQ-eq: {PE 4, MV 4, DN 12}, mean $38,503/wk, maxDD $397,775, vs DS2 +12,663 [-644, +25,714] (MDE 19,101), vs DS2+DS3 -10,056 [-26,383, +5,947] (MDE 23,115); out-of-sample (PRE-solved {KB 14, DN 6}, HOLD-tested): mean $31,700/wk (PRE $38,833), maxDD $571,907 (PRE $271,092), vs DS2 +3,852 [-21,478, +30,486] (MDE 37,388), vs DS2+DS3 -17,507 [-42,964, +9,378] (MDE 38,123); verdicts DEAD (vs DS2) / DEAD (vs DS2+DS3); OOS placebo rank 0.980; WF in-sample placebo rank 1.000 (trivial).**
- **Portfolio (min maxDD s.t. mean>=$30k): best allocation under <=20 NQ-eq: {KB 1, SM 9, MV 2, DN 8}, mean $30,180/wk, maxDD $178,071, vs DS2 +4,339 [-10,196, +18,699] (MDE 20,779), vs DS2+DS3 -18,380 [-36,494, -446] (MDE 25,733); out-of-sample (PRE-solved {KB 5, SM 1, MV 2, DN 9, CR_cons 3}, HOLD-tested): mean $31,598/wk (PRE $30,313), maxDD $343,536 (PRE $128,880), vs DS2 +3,750 [-17,339, +25,448] (MDE 30,701), vs DS2+DS3 -17,610 [-42,207, +7,711] (MDE 36,001); verdicts DEAD (vs DS2) / DEAD (vs DS2+DS3); OOS placebo rank 0.001; WF in-sample placebo rank 0.592 (trivial).**

Headline: nothing PASSes. Every PRE-solved allocation is DEAD against both comparators out of sample; the failing gates are listed below. The PRE-to-HOLD gap is large for objective A (HOLD maxDD breaks the $400k bound at both caps) and small for objective B (the mean constraint holds at 30 lots; B's HOLD maxDD roughly doubles to triples vs PRE).

## 1. Comparators (weekly; PRE 74 wks | HOLD 68 wks | WF 142 wks)
| comparator | lots | window | mean | SD | maxDD | worst wk | L8W | Sharpe |
|---|---|---|---|---|---|---|---|---|
| DS2 | 27 | WFPRE | 23,675 | 99,161 | 537,851 | -199,368 | 25,151 | 1.72 |
| DS2 | 27 | HOLD | 27,848 | 113,488 | 498,491 | -221,854 | 17,643 | 1.77 |
| DS2 | 27 | WF | 25,840 | 106,637 | 537,851 | -221,854 | 17,643 | 1.75 |
| DS2+DS3(D3SL) | 50 | WFPRE | 47,325 | 138,810 | 731,292 | -268,961 | 54,309 | 2.46 |
| DS2+DS3(D3SL) | 50 | HOLD | 49,207 | 145,400 | 559,583 | -270,040 | 64,555 | 2.44 |
| DS2+DS3(D3SL) | 50 | WF | 48,560 | 142,165 | 731,292 | -270,040 | 64,555 | 2.46 |
| DS2+KB10+SM10 | 47 | WFPRE | 52,717 | 134,927 | 591,503 | -232,119 | 53,242 | 2.82 |
| DS2+KB10+SM10 | 47 | HOLD | 50,044 | 157,093 | 582,743 | -275,336 | 73,477 | 2.30 |
| DS2+KB10+SM10 | 47 | WF | 51,808 | 145,962 | 591,503 | -275,336 | 73,477 | 2.56 |

D3SL stack identity reproduced: WF $48,560/wk, maxDD 731,292 (D3SL baseline $48,560 / 731,292). DS2+KB10+SM10 = DS2 + KB 10 + SM 10 lots (registered lots in DS3_LIVE_CONFIG.json, read only); the live config has no PB book.

## 2. PRE-solved allocations tested on HOLD (OUT OF SAMPLE) - primary set
| case | allocation (lots) | NQ-eq alloc / replay peak | PRE mean / maxDD | HOLD mean | SD | maxDD | worst | L8W | Sharpe | gap HOLD-PRE mean / maxDD |
|---|---|---|---|---|---|---|---|---|---|---|
| primary_A_cap30 | KB 14, MV 2, DN 14 | 30.0 / 32.0 | 56,163 / 316,505 | 54,932 | 151,199 | 713,863 | -257,014 | 131,294 | 2.62 | -1,231 / +397,358 |
| primary_B_cap30 | KB 6, SM 2, MV 2, MA 3, DN 4, CR_cons 6, B3 1, RSI2T 3 | 29.3 / 29.3 | 30,019 / 105,088 | 30,759 | 64,254 | 280,058 | -130,779 | 54,475 | 3.45 | +741 / +174,971 |
| primary_A_cap20 | KB 14, DN 6 | 20.0 / 20.0 | 38,833 / 271,092 | 31,700 | 112,424 | 571,907 | -208,660 | 85,264 | 2.03 | -7,133 / +300,815 |
| primary_B_cap20 | KB 5, SM 1, MV 2, DN 9, CR_cons 3 | 20.0 / 21.0 | 30,313 / 128,880 | 31,598 | 76,813 | 343,536 | -133,399 | 73,406 | 2.97 | +1,285 / +214,656 |

### Paired weekly delta of the PRE-solved allocation on HOLD (iid-week bootstrap 10,000, seed 9; MDE = 2.8 x SD(diff)/sqrt(68))
| case | vs DS2 | vs DS2+DS3 (D3SL) | vs DS2+KB10+SM10 | OOS placebo rank (A: mean; B: maxDD higher-than) |
|---|---|---|---|---|
| primary_A_cap30 | +27,084 [-2,027, +56,638] (MDE 42,133) | +5,724 [-20,787, +33,314] (MDE 39,133) | +4,887 [-18,694, +28,891] (MDE 34,239) | 1.000 (mean rank 1.000, dd rank 0.000; random alloc feasible share 0.98) |
| primary_B_cap30 | +2,911 [-20,681, +27,574] (MDE 35,141) | -18,448 [-47,011, +10,533] (MDE 41,339) | -19,285 [-48,231, +9,611] (MDE 41,928) | 0.351 (mean rank 0.024, dd rank 0.351; random alloc feasible share 0.98) |
| primary_A_cap20 | +3,852 [-21,478, +30,486] (MDE 37,388) | -17,507 [-42,964, +9,378] (MDE 38,123) | -18,344 [-41,760, +5,590] (MDE 34,058) | 0.980 (mean rank 0.980, dd rank 0.000; random alloc feasible share 1.00) |
| primary_B_cap20 | +3,750 [-17,339, +25,448] (MDE 30,701) | -17,610 [-42,207, +7,711] (MDE 36,001) | -18,446 [-44,231, +7,486] (MDE 37,187) | 0.001 (mean rank 0.978, dd rank 0.001; random alloc feasible share 0.07) |

### V2 verdict: 'the PRE-solved allocation beats the comparator out of sample' (gates never softened)
| case | comparator | verdict | failed gates |
|---|---|---|---|
| primary_A_cap30 | DS2 | **DEAD** | G1_hold_delta_CI_low>0, G2_constraint_oos, G3_not_worse_than_comparator |
| primary_A_cap30 | DS2+DS3(D3SL) | **DEAD** | G1_hold_delta_CI_low>0, G2_constraint_oos, G3_not_worse_than_comparator, G5_PRE_delta>0_and_year_share<=0.6 |
| primary_B_cap30 | DS2 | **DEAD** | G1_hold_delta_CI_low>0, G4_oos_placebo_rank>=0.95, G5_PRE_delta>0_and_year_share<=0.6 |
| primary_B_cap30 | DS2+DS3(D3SL) | **DEAD** | G1_hold_delta_CI_low>0, G3_not_worse_than_comparator, G4_oos_placebo_rank>=0.95, G5_PRE_delta>0_and_year_share<=0.6 |
| primary_A_cap20 | DS2 | **DEAD** | G1_hold_delta_CI_low>0, G2_constraint_oos, G3_not_worse_than_comparator |
| primary_A_cap20 | DS2+DS3(D3SL) | **DEAD** | G1_hold_delta_CI_low>0, G2_constraint_oos, G3_not_worse_than_comparator, G5_PRE_delta>0_and_year_share<=0.6 |
| primary_B_cap20 | DS2 | **DEAD** | G1_hold_delta_CI_low>0, G4_oos_placebo_rank>=0.95, G5_PRE_delta>0_and_year_share<=0.6 |
| primary_B_cap20 | DS2+DS3(D3SL) | **DEAD** | G1_hold_delta_CI_low>0, G3_not_worse_than_comparator, G4_oos_placebo_rank>=0.95, G5_PRE_delta>0_and_year_share<=0.6 |
Gates: G1 HOLD delta CI lower bound > 0; G2 constraint holds on HOLD (A maxDD<=400k, B mean>=30k); G3 not worse than the comparator on the constrained/objective side (A maxDD, B mean); G4 OOS placebo rank >= 0.95; G5 PRE delta > 0 and no calendar year > 60% of the PRE+HOLD gain; G6 solver gap <= 0.5%. PASS = all; CANDIDATE = one failure with G4 >= 0.90; else DEAD. Duplicates: PE/PE2 are one slot; no book is dropped for correlation. Equal-risk rule: no cell is DEAD for earning less than ST at equal lots - none of the failures above is that.

## 3. WF-solved allocations (SELECTION ON THE HOLDOUT - the WF window includes 2025-07+; in-sample, optimistic)
| case | allocation | WF mean | SD | maxDD | worst | L8W | Sharpe | vs DS2 | vs DS2+DS3 | solver gap / local search (mean, maxDD) | replay peak | HOLD part: mean / maxDD |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| primary_A_cap30 | SM 7, PE 5, MV 4, DN 14 | 50,440 | 107,408 | 398,660 | -187,985 | 111,617 | 3.39 | +24,600 [+9,834, +39,143] (MDE 21,131) | +1,880 [-13,667, +17,395] (MDE 22,161) | 0.0000% / 50,092, 399,768 | 35.0 | 57,641 / 398,660 |
| primary_B_cap30 | KB 2, SM 7, MV 3, DN 4, CR_cons 2, B3 2, RSI2T 1 | 30,060 | 51,230 | 127,358 | -81,522 | 53,680 | 4.23 | +4,220 [-11,153, +19,218] (MDE 21,917) | -18,499 [-38,291, +987] (MDE 27,845) | 0.0580% / 30,060, 127,358 | 26.6 | 34,713 / 127,358 |
| primary_A_cap20 | PE 4, MV 4, DN 12 | 38,503 | 88,601 | 397,775 | -184,383 | 90,733 | 3.13 | +12,663 [-644, +25,714] (MDE 19,101) | -10,056 [-26,383, +5,947] (MDE 23,115) | 0.0754% / 38,209, 397,300 | 28.0 | 44,602 / 397,775 |
| primary_B_cap20 | KB 1, SM 9, MV 2, DN 8 | 30,180 | 61,564 | 178,071 | -110,258 | 61,708 | 3.53 | +4,339 [-10,196, +18,699] (MDE 20,779) | -18,380 [-36,494, -446] (MDE 25,733) | 0.0000% / 30,218, 181,478 | 22.0 | 32,990 / 178,071 |
The WF solves differ from the PRE solves (e.g. A cap 30: PRE KB14/MV2/DN14, WF SM7/PE5/MV4/DN14): the optimum moves with the window, which is the in-sample selection problem. The WF solution is NOT validated by anything out of sample.

## 4. By year and by VIX tercile (weekly mean $; terciles = prior-close VIX at the first label day of the week, trailing-120 thresholds)
PRE-solved allocations on the WF path (PRE+HOLD weeks), then WF-solved allocations on WF:

| allocation | window | 2024 | 2025 | 2026 | VIX low | VIX mid | VIX high |
|---|---|---|---|---|---|---|---|
| DS2 | WF | 20,294 (n 49) | 32,509 (n 52) | 24,011 (n 41) | 34,194 (n 54) | 14,210 (n 39) | 25,890 (n 49) |
| DS2+DS3(D3SL) | WF | 41,271 (n 49) | 59,823 (n 52) | 42,986 (n 41) | 59,976 (n 54) | 37,070 (n 39) | 45,124 (n 49) |
| DS2+KB10+SM10 | WF | 46,468 (n 49) | 63,132 (n 52) | 43,828 (n 41) | 63,200 (n 54) | 45,458 (n 39) | 44,307 (n 49) |
| primary_A_cap30 (WF-solved) | WF | 42,783 (n 49) | 44,070 (n 52) | 67,671 (n 41) | 58,522 (n 54) | 40,104 (n 39) | 49,761 (n 49) |
| primary_B_cap30 (WF-solved) | WF | 25,483 (n 49) | 25,702 (n 52) | 41,059 (n 41) | 27,591 (n 54) | 33,518 (n 39) | 30,030 (n 49) |
| primary_A_cap20 (WF-solved) | WF | 31,968 (n 49) | 32,125 (n 52) | 54,404 (n 41) | 45,482 (n 54) | 27,749 (n 39) | 39,372 (n 49) |
| primary_B_cap20 (WF-solved) | WF | 28,186 (n 49) | 25,487 (n 52) | 38,514 (n 41) | 33,860 (n 54) | 27,762 (n 39) | 28,048 (n 49) |
| primary_A_cap30 (PRE-solved) | HOLD | - | 46,452 (n 27) | 60,516 (n 41) | 60,544 (n 35) | 79,490 (n 16) | 20,264 (n 17) |
| primary_B_cap30 (PRE-solved) | HOLD | - | 24,609 (n 27) | 34,810 (n 41) | 27,031 (n 35) | 42,367 (n 16) | 27,511 (n 17) |
| primary_A_cap20 (PRE-solved) | HOLD | - | 32,476 (n 27) | 31,189 (n 41) | 39,435 (n 35) | 43,831 (n 16) | 4,356 (n 17) |
| primary_B_cap20 (PRE-solved) | HOLD | - | 23,052 (n 27) | 37,226 (n 41) | 34,051 (n 35) | 44,326 (n 16) | 14,568 (n 17) |

## 5. Day-block bootstrap of maxDD (10,000 draws; block 5 days, blocks 1 and 10 in final.json)
| allocation | window | observed maxDD | bootstrap median | p05-p95 | P(boot > observed) |
|---|---|---|---|---|---|
| primary_A_cap30 WF-solved | WF | 398,660 | 466,208 | 320,737-746,530 | 0.74 |
| primary_B_cap30 WF-solved | WF | 127,358 | 201,244 | 144,656-308,751 | 0.99 |
| primary_A_cap20 WF-solved | WF | 397,775 | 398,383 | 270,770-639,333 | 0.50 |
| primary_B_cap20 WF-solved | WF | 178,071 | 267,409 | 185,604-423,040 | 0.97 |
| primary_A_cap30 PRE-solved | HOLD | 713,863 | 577,352 | 364,667-1,010,260 | 0.26 |
| primary_B_cap30 PRE-solved | HOLD | 280,058 | 229,748 | 147,342-389,675 | 0.27 |
| primary_A_cap20 PRE-solved | HOLD | 571,907 | 484,772 | 298,971-872,843 | 0.32 |
| primary_B_cap20 PRE-solved | HOLD | 343,536 | 271,418 | 174,050-470,300 | 0.23 |
(PRE-window bootstraps are in pre_primary.json: the observed PRE maxDDs sat in the lower tail of their own bootstrap, i.e. were optimistic.)

## 6. In-sample vs out-of-sample gap (the number to read)
- primary_A_cap30: PRE-solved, PRE mean 56,163 -> HOLD 54,932 (-1,231); PRE maxDD 316,505 -> HOLD 713,863 (+397,358).
- primary_B_cap30: PRE-solved, PRE mean 30,019 -> HOLD 30,759 (+741); PRE maxDD 105,088 -> HOLD 280,058 (+174,971).
- primary_A_cap20: PRE-solved, PRE mean 38,833 -> HOLD 31,700 (-7,133); PRE maxDD 271,092 -> HOLD 571,907 (+300,815).
- primary_B_cap20: PRE-solved, PRE mean 30,313 -> HOLD 31,598 (+1,285); PRE maxDD 128,880 -> HOLD 343,536 (+214,656).
Reading: weekly means are mostly retained (HOLD within about +/-$8k of PRE for A cap 30/20 and ~unchanged for B) but the drawdown is not: objective A cap 30 goes from $317k to $714k and cap 20 from $271k to $572k, breaking the $400k constraint out of sample (G2 fails); objective B keeps mean >= $30k at cap 30 and cap 20 on HOLD, with maxDD $280k / $344k vs $105k / $129k in PRE. The A solutions put 14 lots of KB and 6-14 of DN (a MAPPED book) at the lot cap; the maxDD constraint was non-binding in PRE, so the solver had no incentive to diversify - the constraint set was not informative in the window used.

## 7. Placebo and selection null
- Random allocations (10,000, same total NQ-eq, composition by random lot placement): in-sample ranks are ~1.0 for A mean and for B maxDD (trivial: the solver searches ~10^15 allocations). OOS (PRE-solved, scored on HOLD): A cap 30 mean rank 1.00, A cap 20 0.98, but the A allocations' HOLD maxDD ranks 0.00 (worse than every random allocation on drawdown); B cap 30 maxDD rank 0.35 (random allocations had lower HOLD maxDD in 65% of draws) and B cap 20 maxDD rank 0.001. The B solutions' HOLD mean ranks 0.02 (cap 30) / 0.98 (cap 20). **No allocation reaches OOS rank 0.95 on its own objective except A's mean (which is the lot-budget effect: KB+DN are the two best books by mean).**
- Selection null (LP optimum of objective A on WF with each book's path circularly shifted by an independent random number of weeks, 100 draws): cap 30 real 50,547 vs null median 59,992 (rank 0.00); cap 20 real 38,715 vs 40,964 (rank 0.00). The real books are MORE co-moving than timing-shuffled ones, so the maxDD bound costs the real portfolio mean that the shuffled one does not pay: the optimum is not exceptional relative to the null; the mean comes from the lot budget on the highest-mean books, not from timing structure.
- Best-of-N: 8 primary solves (+ 4 PRE-solve tests), variants descriptive; WF solves are N-way selection on the holdout. The OOS rank is the family-wise statement.

## 8. Variants (descriptive; PRE-solved, HOLD-tested; full numbers in final.json)
| variant | case | allocation | PRE mean / maxDD | HOLD mean / maxDD | vs DS2 HOLD | verdict vs DS2 / DS2+DS3 |
|---|---|---|---|---|---|---|
| WT | A_cap30 | KB 14, MV 2, DN 14 | 56,163 / 316,505 | 54,932 / 713,863 | +27,084 [-2,027, +56,638] (MDE 42,133) | DEAD / DEAD |
| WT | B_cap30 | KB 6, SM 2, MV 2, MA 3, DN 4, CR_cons 6, B3 1, RSI2T 3 | 30,019 / 105,088 | 30,759 / 280,058 | +2,911 [-20,681, +27,574] (MDE 35,141) | DEAD / DEAD |
| WT | A_cap20 | KB 14, DN 6 | 38,833 / 271,092 | 31,700 / 571,907 | +3,852 [-21,478, +30,486] (MDE 37,388) | DEAD / DEAD |
| WT | B_cap20 | KB 5, SM 1, MV 2, DN 9, CR_cons 3 | 30,313 / 128,880 | 31,598 / 343,536 | +3,750 [-17,339, +25,448] (MDE 30,701) | DEAD / DEAD |
| cap50 | A_cap50 | ST 1, KB 14, MV 8, DN 22, CR_cons 5 | 78,409 / 399,848 | 83,003 / 957,193 | +55,155 [+16,086, +94,047] (MDE 56,292) | DEAD / DEAD |
| cap50 | B_cap50 | KB 6, SM 1, MV 1, MA 4, DN 4, CR_cons 7, RSI2T 10 | 30,571 / 103,067 | 28,478 / 271,550 | +630 [-26,354, +29,051] (MDE 40,452) | DEAD / DEAD |
| CR | map_A_cap30 | KB 14, MV 2, DN 14 | 56,163 / 316,505 | 54,932 / 713,863 | +27,084 [-2,027, +56,638] (MDE 42,133) | DEAD / DEAD |
| CR | map_B_cap30 | KB 4, SM 1, MV 1, MA 3, DN 4, CR_map 11, RSI2T 6 | 30,365 / 81,705 | 33,953 / 209,273 | +6,105 [-19,851, +33,003] (MDE 38,464) | DEAD / DEAD |
| CR | map_A_cap20 | KB 14, DN 6 | 38,833 / 271,092 | 31,700 / 571,907 | +3,852 [-21,478, +30,486] (MDE 37,388) | DEAD / DEAD |
| CR | map_B_cap20 | ST 1, KB 5, MV 2, MA 1, DN 7, CR_map 4 | 30,422 / 111,869 | 33,190 / 304,400 | +5,342 [-15,041, +26,328] (MDE 29,592) | DEAD / DEAD |
- WT included: WT is chosen in no PRE or WF solve; allocations identical to the primary (the live comparator contains WT7 but the optimiser does not want it). PE2 and EM: not chosen in any PRE solve; identical to primary (pre_PE2.json, pre_EM.json). CR_map (plain mapped CR) is chosen heavily by B (11-13 lots) because its optimistic basis raises mean at low SD - flagged, not a result. Context-only total 50: the A solution (ST1 KB14 MV8 DN22 CR5) breaches the 50 cap in the replay (peak 58 > 50): its P&L is NOT cap-adjusted (no trade-level skip), so it is unattainable as stated.

## 9. NQ-equivalent conversion sensitivity (PRE re-solve, HOLD test)
Notional ratio (primary): ES/NQ 0.714, RTY/NQ 0.262 -> one B3 unit = 3.287 NQ-eq. Point-value ratio 2.5 (one unit = 13.94 NQ-eq) and the margin-assumption (3.357, ASSUMED margin ratios, no margin file exists) are sensitivities:
- pointvalue2.5_A_cap30: KB 14, MV 2, DN 14; PRE 56,163/316,505; HOLD 54,932/713,863.
- pointvalue2.5_B_cap30: KB 6, SM 1, MV 1, MA 3, DN 5, CR_cons 6, RSI2T 8; PRE 30,400/107,554; HOLD 28,769/268,374.
- pointvalue2.5_A_cap20: KB 14, DN 6; PRE 38,833/271,092; HOLD 31,700/571,907.
- pointvalue2.5_B_cap20: KB 5, SM 1, MV 2, DN 9, CR_cons 3; PRE 30,313/128,880; HOLD 31,598/343,536.
- margin_A_cap30: KB 14, MV 2, DN 14; PRE 56,163/316,505; HOLD 54,932/713,863.
- margin_B_cap30: KB 6, SM 2, MV 2, MA 3, DN 4, CR_cons 6, B3 1, RSI2T 3; PRE 30,019/105,088; HOLD 30,759/280,058.
- margin_A_cap20: KB 14, DN 6; PRE 38,833/271,092; HOLD 31,700/571,907.
- margin_B_cap20: KB 5, SM 1, MV 2, DN 9, CR_cons 3; PRE 30,313/128,880; HOLD 31,598/343,536.
A solutions are unchanged (they do not use B3). Under the 2.5 ratio B drops B3 and raises RSI2T (8 lots).

## 10. Method, validation, caps, coverage and honesty notes
- Lock engine: KB and SM re-run through the exact engine (te_core.run_rows -> firmlib.Ctx.run) at 3/20/30 lots vs 10: max |daily diff| <= 1e-10 $, identity to stored series 0.0 (lock_scaling_validation.json): locks scale exactly with R; size cost added with the s113 excess surface (equal_risk convention); B3 via measured per-trade direct nets. 10-lot slicing S10x1 is not re-run at other L.
- Optimiser: exact MILP (HiGHS, one-hot lot levels, running-peak drawdown variables). Final gaps <= 0.1% in every solve; the 200-restart local search never beat the MILP and matched it in most cases (differences listed in the table). Optimum robust across restarts in the sense that no restart exceeded the MILP incumbent.
- Cap replay: peak concurrent NQ-eq from interval event streams (lock-kept for KB/SM/EM/DN/CR; all signals for ST/HM/WT/PE/MV/MA = upper bound; MV/MA/PE intervals do not include the last week after 2026-10-09). Realised peak = 29.3-32.0 for the 30 cap and 20-21 for the 20 cap (slightly above the allocation because pre-lock intervals of one book can overlap by a minute); both far below 50, so the 50-cap never binds and no trade was skipped.
- Coverage after 2026-10-09 (raw L2 ends 2026-10-09; WF label days 10-12..10-16 = 5 days): KB 170 trades, SM 31, EM 31 after 10-09 20:00 UTC are all P9-MAPPED (0 direct); PE, MV, MA: the series have trades on the 5 label days (MV/MA 2026-10 direct share 86 of 248 trades) but the L2 replay stops at 10-09 so those are mapped; DN, CR, WT mapped throughout; ST/HM are P9-corrected through the pairP rows (EXT rows beyond use the mapped correction); B3/RSI2T are bar-based with book walk (1-2 trade days). This is ~1 week of 142 and not material to the results.
- Basis flags: DN MAPPED stop-entry; CR on the CONSERVATIVE mapped basis (WF about -$1.6k/wk standalone at 10 lots, PRE +$0.7k) in the primary and plain-mapped in the CR_map variant; MV/MA hybrid; WT mapped (variant only). Duplicates: PE vs PE2 one slot; KB/ST/MV/MA/DN share trend-entry families (not removed).
- DS2+DS3 (D3SL definition) exceeds the 30/20 budgets (50 lots) and DS2 is 27 lots; the comparison is not lot-matched. The solved allocations at 30 lots are closer to DS2's lot count but still use KB/DN-heavy mixes unlike DS2.
- Selection honesty: allocation search over WF is a selection on the holdout; the PRE-solved/HOLD-tested row is the honest one. The holdout is read once for the allocation tests (logged). All results are research; nothing here recommends a live change.
