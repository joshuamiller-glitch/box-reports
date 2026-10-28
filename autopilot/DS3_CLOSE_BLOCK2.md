# DS3_CLOSE_BLOCK2 - T-CLOSE block 2 (3.4 range breaks, 3.5 dip-buy/overnight drift, 3.6 post-close, 3.7 levels) + UN-BLOCK baseline + RVW1 follow-ups - D3CL1, 2026-10-27
Research only. Shared harness open2 patched in-process (c3_patch.py, stop-entry support added); fees 4.84 RT NQ (proxy); verdict = lower tier of basis M / T; HARNESS best-of-N rule unchanged.

## Verdict
**Block 2: 0 PASS, 0 CANDIDATE, 184 DEAD** of 184 scored cells (18 signals x 12 brackets = 216 prereg'd; 32 empty: post-close cells (PC05, PC15, EARN05) have no valid F*/T1600/STRAIL/BE10/NOSTOP/VWAP/DAYHL exit after their 16:05-16:15 signal, LBRK/LBRKS/VWT VWAP/DAYHL targets with no valid trades). Prereg sha256 for CL10-CL18 and SIZE in DECISIONS.md before scoring. 26 of 368 cell-bases beat placebo (b) (64 draws; RSI2DS and RVW-type cells mostly), none of them also beats bracket beta (d) with the stack-add gates.
Combined T-CLOSE after blocks 1+2: **0 PASS, 1 CANDIDATE (RVW1|F30), 384 DEAD**.

## Un-block baseline (the question of 3.12; scored)
ST, HM, WT, KB (TE7_kelt3m_n14_m1.0), SM (TE6_st10m_n7_m3.0) entry rows were regenerated with the signal gate relaxed so entries 15:01-16:54 (flat 16:55 by the same time-block) occur; the new window rows run together with the existing rows under each book's exact per-book locks (WINMASK opened for the new rows), MAPPED basis (nominal 1-s path + 0.5 + year x exit-type P9 correction, asm_lib convention; the existing KB/SM rows are direct S10x1+XJ3 priced). **PB (PB3B_R5_P1) and PS were NOT regenerated** (different generator; PB is in the stack, so its window rows are missing: disclosed). 
Identity (regenerated rows OUTSIDE the window vs the existing rows, (entry bar, side) sets, 2023-02-10+): 0 only-old / 0 only-new for all five books.
| book | rows existing | rows regenerated outside window | only old / only new | window rows (entries 15:01-16:54) | window win rate (nominal pts>0) |
|---|---|---|---|---|---|
| ST | 8309 | 8309 | 0 / 0 | 727 | 0.46 |
| HM | 6311 | 6311 | 0 / 0 | 617 | 0.47 |
| WT | 11641 | 11641 | 0 / 0 | 1106 | 0.53 |
| KB | 8593 | 8593 | 0 / 0 | 832 | 0.47 |
| SM | 2397 | 2397 | 0 / 0 | 187 | 0.44 |
Stack with the block removed vs live stack (mean $/wk / Sharpe / maxDD; paired bootstrap CIs of the difference; per-book mean contribution $/wk):
| window | live | un-blocked | d mean 95% CI | d Sharpe 95% CI | per-book d mean |
|---|---|---|---|---|---|
| WFPRE | 40,840 / 2.28 / 460,184 | 37,793 / 2.09 / 497,105 | -4,966 .. -1,281 | -0.32 .. -0.09 | ST -263, HM -563, WT -1,895, KB -332, SM -446 |
| WF | 44,867 / 2.41 / 548,152 | 42,726 / 2.28 / 541,777 | -3,376 .. -789 | -0.21 .. -0.05 | ST -16, HM -248, WT -1,567, KB -82, SM -474 |
| HOLD | 48,649 / 2.52 / 548,152 | 47,538 / 2.46 / 541,777 | -2,760 .. 329 | -0.17 .. +0.02 | ST +256, HM +102, WT -1,182, KB +196, SM -498 |
| X | 23,281 / 1.62 / 465,189 | 20,252 / 1.44 / 481,542 | -5,472 .. -668 | -0.35 .. -0.02 | ST -63, HM -628, WT -1,868, KB -551, SM -161 |
**Answer: un-blocking the existing books 15:00-16:54 LOSES about $2.1k/wk (WF 44,867 -> 42,726; Sharpe 2.41 -> 2.28; 2023-24 -$3.0k; HOLD -$1.1k, CI includes 0), driven by WT (-$1.6k/wk); maxDD about unchanged (-$6k).** Any close book with a positive stack-add beats un-blocking, and RVW1|F30 (+$2,144/wk, Sharpe +0.12) beats it by about $4.3k/wk; but only RVW1 is a CANDIDATE at all.

## RVW1 follow-ups (lead order)
- Forward-register spec (parameter level, no-quote caveat): autopilot/DS3_SPEC_RVW1_F30.md; machine entry l2vast/ds3/out/tclose_b1/forward_entry_ds3_TCLOSE_RVW1_F30.json (+ daily series and expectation json). NOT copied into struct48/paper_all (lead's call).
- Placebo (b) repeat at **200 draws** (prereg TCLOSE_B2_REP200): RVW1|F30 PRE effect **+6.60 pts [2.95, 10.17] rank 1.00 (M); +5.10 [1.02, 8.98] rank 1.00 (T)**; BE10 +6.24 [1.50, 11.45] rank .995 (M), +3.82 [-0.87, 8.62] .985 (T); T1600 +8.81 (M) / +6.82 (T); RVW2 F30 +8.14 (M) / +6.94 (T), RVW2 BE10 +9.16 / +5.92, T1600 +11.71 / +9.06. HOLD effect (b): RVW1|F30 +3.39 [0.24, 6.90] (M), +1.31 [-2.26, 5.30] (T); 2023-24: +3.87 / +3.52. The 64-draw result stands; the effect roughly halves out of sample and is not significant on T in HOLD alone.
- Sizing (prereg SIZE; R6k = 10 lots for stop 30, identical to fixed-10): R12k doubles to 20 lots: RVW1|F30 M WF +$3,877/wk (SD 19.1k, maxDD 119k, worst week -48.9k), d Sharpe +0.21, d maxDD -11.3k, d mean CI [724, 7,125] vs MDE 4,498; T +3,039 [-312, 6,360] (d Sharpe +0.14). 2x-cost HOLD is negative at every size (M -1,378 fixed-10, -3,586 R12k). RVW1|BE10 R12k M: +6,212/wk, d Sharpe +0.34, HOLD +4.6k, but T HOLD -145 (T basis fails).
| cell | sizing | basis | lots | WF mean $/wk | WF SD | maxDD | worst wk | HOLD mean | 2x-cost HOLD | stack d mean [CI] | d Sharpe | d maxDD | MDE |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RVW1|F30 | fixed10 | M | 10 | +2,144 | 9,585 | 56,317 | -24,194 | +900 | -1,378 | +2,144 [560, 3,774] | +0.12 | -6,220 | 2,252 |
| RVW1|F30 | fixed10 | T | 10 | +1,725 | 10,270 | 69,769 | -24,394 | +577 | -223 | +1,725 [53, 3,393] | +0.09 | -3,614 | 2,413 |
| RVW1|F30 | R12k | M | 20 | +3,877 | 19,141 | 119,331 | -48,902 | +1,386 | -3,586 | +3,877 [724, 7,125] | +0.21 | -11,280 | 4,498 |
| RVW1|F30 | R12k | T | 20 | +3,039 | 20,518 | 150,100 | -49,302 | +740 | -1,275 | +3,039 [-312, 6,360] | +0.14 | -6,070 | 4,821 |
| RVW1|BE10 | fixed10 | M | 10 | +3,286 | 12,548 | 61,349 | -18,242 | +2,582 | +1,613 | +3,286 [1,332, 5,501] | +0.19 | -9,262 | 2,948 |
| RVW1|BE10 | fixed10 | T | 10 | +1,337 | 11,577 | 101,161 | -18,492 | +225 | -574 | +1,337 [-512, 3,264] | +0.06 | -3,173 | 2,720 |
| RVW1|BE10 | R12k | M | 20 | +6,212 | 24,573 | 155,821 | -37,128 | +4,628 | +2,296 | +6,212 [2,342, 10,356] | +0.34 | -17,365 | 5,774 |
| RVW1|BE10 | R12k | T | 20 | +2,233 | 22,933 | 212,248 | -37,628 | -145 | -2,141 | +2,233 [-1,553, 6,219] | +0.07 | -5,187 | 5,389 |
- Supplementary per-bracket-class best-of-N null (NOT a gate; classes FIX F15/F30/F60, STRUCT VWAP/DAYHL, TIME T1600/T1614/NOSTOP, OVN H1805/H0930, TRAIL STRAIL/BE10), block 1 pooled (all signals): FIX p95 26.6 (M) / 27.1 (T), TIME 36.5/34.2, TRAIL 19.9/20.6, STRUCT 72.7/89.1, OVN 114.7/116.2; excluding the five n<110 signals (RPIN RSTR R330 FAD1 FAD15): FIX 10.2/10.5, TIME 20.2/20.0, TRAIL 13.2/13.1. RVW1|F30 effect 6.84 (M) / 5.37 (T) is below every class p95 (FIX 10.2 even without low-n signals; rank of the class best about 0.83/0.66). Block 2 per class: M/FIX: best RSI2DS|F30 6.86 vs class p95 7.94; M/STRUCT: best PB3|DAYHL 9.96 vs class p95 12.95; M/TIME: best VSR|NOSTOP 8.77 vs class p95 12.79; M/OVN: best PB3|H0930 73.91 vs class p95 33.17; M/TRAIL: best VSR|STRAIL 7.16 vs class p95 8.1; T/FIX: best RSI2DS|F30 8.25 vs class p95 8.16; T/STRUCT: best RSI2DS|VWAP 9.57 vs class p95 13.22; T/TIME: best IBS55S|T1614 9.78 vs class p95 12.69; T/OVN: best PB3|H0930 74.78 vs class p95 33.04; T/TRAIL: best RSI2DS|STRAIL 7.39 vs class p95 8.52. The only cell exceeding its class p95 anywhere: RSI2DS|F30 on basis T (8.25 vs 8.16) and the overnight PB3|H0930 (74 vs 33; n=76), both DEAD on beta / stack-add. So the structural question (a per-class null) does not rescue RVW1.

## Per-cell verdicts block 2 (worst of M/T; b# = bases, of 2, that beat placebo (b) at 64 draws); full 368 cell-base rows in out/tclose_b1/cells_final_b2.csv
| signal | F15 | F30 | F60 | VWAP | DAYHL | T1600 | T1614 | H1805 | H0930 | STRAIL | BE10 | NOSTOP |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B1530 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| B1530S | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| B1550 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b1 | D/b0 | D/b0 |
| B1550S | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| EARN05 | empty | empty | empty | empty | empty | empty | D/b0 | D/b0 | D/b0 | empty | empty | empty |
| IBS55 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| IBS55S | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b2 | D/b0 | D/b0 | D/b0 |
| LBRK | D/b0 | D/b0 | D/b0 | empty | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| LBRKS | D/b0 | D/b0 | D/b0 | empty | empty | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| PB3 | D/b1 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b2 | D/b0 | D/b0 | D/b0 |
| PC05 | empty | empty | empty | empty | empty | empty | D/b0 | D/b0 | D/b0 | empty | empty | empty |
| PC15 | empty | empty | empty | empty | empty | empty | empty | D/b0 | D/b0 | empty | empty | empty |
| PCT | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| RSI25 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| RSI2D | D/b1 | D/b0 | D/b0 | D/b1 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| RSI2DS | D/b2 | D/b2 | D/b2 | D/b2 | D/b0 | D/b2 | D/b0 | D/b2 | D/b2 | D/b2 | D/b2 | D/b0 |
| VSR | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| VWT | D/b0 | D/b0 | D/b0 | empty | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
Gate failures over 368 cell-bases: beats_beta 366, stack_add_pre 365, best_of_N 364, beats_b 342, year_share 337, span2 308, hold 273, cost2x_pre 239, mean_up 185, neighbours 109, min_n 38.
Best-of-N (harness, block-2 family of 184 cells): best (b)-effect PB3|H0930 73.9 (M) / 74.8 (T) vs null p95 33.2 / 33.0 (n=76 overnight, fails beta, min_n, stack-add).

## Top 15 by stack-add Sharpe delta (WF, 142 weeks) regardless of verdict; every |d mean| is below or near its MDE; the largest are H0930 overnight cells (bracket beta: random-direction overnight holds earn a positive stack-add)
| cell | verdict | trades/wk | stack-add dSharpe (WF, min M/T) | d mean $/wk (M / T) | MDE (M) | fwd wk (M) | d maxDD (M) | HOLD mean (M) | 2023-24 mean (M) | failed gates (M ; T) |
|---|---|---|---|---|---|---|---|---|---|---|
| PC15|H0930 | DEAD | 3.93 | +0.22 | +6,638 / +5,886 | 9,794 | 309 | +46,691 | +8,063 | +940 | beats_b,beats_beta,stack_add_pre,year_share,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| RSI2DS|H0930 | DEAD | 1.09 | +0.22 | +6,101 / +5,841 | 6,634 | 168 | +24,097 | +7,906 | +665 | beats_beta,stack_add_pre,best_of_N ; beats_beta,stack_add_pre,year_share,best_of_N |
| PB3|H0930 | DEAD | 0.38 | +0.14 | +2,589 / +2,414 | 3,906 | 323 | +0 | +2,602 | +312 | min_n,beats_c,beats_beta ; min_n,beats_beta,stack_add_pre |
| RSI2D|H1805 | DEAD | 2.75 | +0.13 | +2,759 / +2,799 | 4,595 | 394 | -1,430 | +3,114 | -603 | beats_b,beats_beta,stack_add_pre,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N |
| RSI2DS|H1805 | DEAD | 1.09 | +0.12 | +2,624 / +2,354 | 3,645 | 274 | +14,856 | +2,489 | +1,180 | beats_beta,stack_add_pre,year_share,best_of_N ; beats_beta,stack_add_pre,year_share,best_of_N |
| VSR|NOSTOP | DEAD | 1.30 | +0.09 | +2,056 / +2,156 | 5,142 | 888 | -3,242 | +2,316 | -754 | beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,span2,best_of_N |
| B1530S|T1600 | DEAD | 3.65 | +0.09 | +967 / +973 | 3,860 | 2,263 | +15,623 | +261 | -1,744 | beats_b,beats_beta,stack_add_pre,cost2x_pre,hold,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,hold,span2,best_of_N |
| RSI2DS|T1614 | DEAD | 1.09 | +0.08 | +1,951 / +1,804 | 2,718 | 276 | +9,456 | +2,480 | +1,009 | beats_b,beats_beta,stack_add_pre,year_share,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| RSI2D|H0930 | DEAD | 2.75 | +0.07 | +4,351 / +3,873 | 9,043 | 613 | +29,052 | +7,031 | -5,810 | beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N |
| IBS55S|H0930 | DEAD | 0.40 | +0.07 | +1,197 / +1,931 | 3,286 | 1,069 | +12,048 | +152 | -121 | beats_beta,stack_add_pre,year_share,hold,span2 ; beats_beta,stack_add_pre,year_share,span2 |
| RSI2D|T1614 | DEAD | 2.75 | +0.07 | +1,715 / +1,786 | 3,558 | 611 | -1,780 | +2,593 | -1,176 | beats_b,beats_beta,stack_add_pre,cost2x_pre,year_share,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N |
| PC05|H0930 | DEAD | 3.58 | +0.07 | +6,493 / +5,963 | 10,431 | 366 | +43,434 | +5,396 | +1,604 | beats_b,beats_beta,stack_add_pre,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,best_of_N |
| B1530S|NOSTOP | DEAD | 3.65 | +0.06 | +1,025 / +1,286 | 3,917 | 2,072 | +15,623 | +203 | -1,502 | beats_b,beats_beta,stack_add_pre,cost2x_pre,year_share,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,year_share,span2,best_of_N |
| PCT|H0930 | DEAD | 0.66 | +0.05 | +1,789 / +1,840 | 4,591 | 935 | -18,547 | +626 | -2,544 | beats_b,beats_beta,stack_add_pre,hold,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,hold,span2,best_of_N |
| IBS55|H1805 | DEAD | 1.20 | +0.05 | +360 / +698 | 2,286 | 5,713 | +4,854 | -102 | -431 | beats_b,beats_beta,stack_add_pre,year_share,hold,span2,best_of_N ; beats_b,beats_beta,stack_add_pre,span2,best_of_N |

## Family read
- 3.4 range breaks (B1530/B1550/LBRK and the stop-entry straddles): all DEAD, 0 beat (b) except B1550|STRAIL on one basis; closing-range breaks do not continue after the 15:30/15:50 hand-offs, stop-entries (better price) change nothing.
- 3.5 dip-buy/rip-sell: IBS55, RSI25, PB3 DEAD; RSI2D and RSI2DS (daily RSI(2), with SMA200 filter) beat (b) on many brackets (RSI2DS b2 on 9 of 12) and are the most interesting new lead, but fail beta and stack-add (overnight: RSI2DS|H0930 M d Sharpe +0.25 PRE but d mean CI [-125, 9,096] includes 0, year share on T). RSI2T (live reference) is the sibling. n=215 for RSI2DS: underpowered for the overnight cells (MDE $6.6k/wk vs d $6.1k).
- 3.6 post-close (PC05, PC15, EARN05): only T1614/H1805/H0930 valid; positive raw overnight d mean (PC15|H0930 +$6.6k/wk) but rank vs (b) .77 and fails beta (overnight long bias) and year share. EARN05 n=93 (AMC flags, 10 of 15 tickers): nothing; calendar earnings end 2026-10-15.
- 3.7 levels (VWT, VSR, PCT): DEAD, 0 beat (b).
- Power: PRE counts 25 (PB3) to 300 (B1550S); per-trade MDEs 3-15 pts on 15-60 pt brackets (prereg tables).

## Deviations and disclosures
1. **Bug found and fixed:** the placebo-(b) clock shift was applied twice for the nine scan-type signals (B1530 B1550 LBRK B1530S B1550S LBRKS VWT VSR PCT), exposed by VSR|NOSTOP's absurd (b) draw mean (-142 pts). Real cells unaffected. The 9 pickles were moved to out/topen_b2/grp_TCLOSE_B2_dblshift_bak (no deletion), the signals fixed, rerun at the same prereg (same cells, 64 draws), pre/final redone; v1 files kept (tclose_b2_*_v1_dblshift.*). The holdout look per group had been logged and the HOLD columns of the real cells read in the v1 final stage (numbers identical for the real cells); nothing was selected on v1. Logged in DECISIONS.md. Block-1 signals do not have this bug (checked: t_sig and t0 are consistent).
2. Un-block: PB/PS not regenerated; mapped basis for the new rows; locks applied to the union (window rows can change a book's day state: included). The `stack with the block removed` comparator is therefore PB-less in the window.
3. Quote tape only 15:45-16:15: stop-entry fills and entries before 15:45 / after 16:15 use SC close fallback (stop-entry M = level +1 tick, T = max(level+1 tick, 1-s close)). Straddle stop-entry side = level touched first (exempt from the side as-of audit).
4. Order types beyond market and stop-entry straddle (resting limit, MOC-equivalent exit comparison, latency 5/50/150 ms) and bars other than 1-min/1-s: NOT done (block 3/4). Fixed 10 lots for the screen; R12k/R6k only for RVW1 (SIZE).
5. RSI(2) = Cutler (simple average of the last two changes), IBS/PB3/RSI25 definitions in the preregs. As-of audits: 12 non-scan signals x 60 days 0 mismatches, 6 scan signals per event day (30 each) 0 mismatches, positive controls flag all.
6. Holdout: ONE logged look per group CL10-CL18 (pre-holdout text sha256 ec6fc7b9e67d70686d682406c97825b9b0832d1cd547ee5cb13b517f560025b9 = the v1 text; v2 text overwrote tclose_b2_prehold.txt after the fix); ledger +216 cells (block 2) and the REP200/SIZE repeats are not new cells. Memory gate 32 GB (waited), corepool slots (12 workers), no kills/retries, no downloads, UNTOUCHED unread.

## Preregs (sha256 in DECISIONS.md before scoring)
- CL10: 0009fe9e33c347e8651d8803885bab3d19e4ff510c83d66b2371b42ba364b061
- CL11: 9be92c7ef59813e235f27a78c4c5c2cf6ba8f9b2072d6fd3074aa3332647ccc1
- CL12: 96e06cfe80e9626f1ced1bfb13c9360f2e64631335392b94821f696798818cca
- CL13: 5bb915be0f9bd219d611e92d929b7bbf81a43addd207a4b692e12c00a047c846
- CL14: 4830a582f9fcc28a239356bed0efcba7736d4841efb2fd08b5adeb06ea4e0bfa
- CL15: e76c41d9a77c5047c93f01b32a36ab0ff1366d243a62c514d19119bed6b2f2b1
- CL16: 1d319d13187c1b345ff88c068b41d2b7b550a698b4d56fca6f138fdbab5bc0ad
- CL17: d2b4d5ee3f9e29a4848abb4738803224eaeb33fd507e327a9ca82fbc8f246bb7
- CL18: 1221ae7cecd2b150381df3ad8352210aaec4d501b3ad1d9f1bbe21a05baa2b9a
- SIZE and REP200: l2vast/ds3/prereg/TCLOSE_B2_SIZE_prereg.md, TCLOSE_B2_REP200_prereg.md.
Code: l2vast/ds3/code/close3/ (c3_signals2, c3_prereg2, c3_run2, c3_final2, c3_b2_tables, c3_unblock, c3_classnull, c3_rep200, c3_size, c3_audit2/2b); results l2vast/ds3/out/tclose_b1/ (cells_final_b2.csv, tclose_b2_final.pkl, unblock_*.pkl/json, size_rvw1.csv, classnull*.json); variant pickles out/topen_b2/grp_TCLOSE_B2 and grp_TCLOSE_B2_RVW200.

## ETA for the remaining blocks
- Block 3 (3.8 cross-asset: ES/RTY/YM relative strength at the close, ZN 15:00, 6E; other instruments' own closes CL 14:30 / GC SI 13:30 / ZN 15:00-16:00 / 6E 17:00; 3.9 footprint 1-min/15-s into the close; 3.10 L2 mbp-10 at 15:50-16:00 and the 15:30 fill check for RVW1; fill-cost-by-second and capacity tables): about 6-8 h; needs a 15:25-16:20 NQ/ES tape+book extraction (existing tables, no purchase).
- Block 4 (full section-4 grid on the top 3 per family, bars x order types incl. resting limit / MOC-equivalent exit, learned classifier 3.11, robustness on the top 10 incl. RVW1/RVW2/RSI2DS, K4 overlap + margin step-up, closes sleeve, MOC-proxy validity, DS3_CLOSE_FINAL): about 8-10 h. Total about 14-18 h from now if slots/memory hold.
