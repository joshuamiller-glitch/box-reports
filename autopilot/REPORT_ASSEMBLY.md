# REPORT ASSEMBLY - ST10/HM10/WT7 in one account with per-book locks (jobs 1 and 2 of the 2026-10-25 "Three jobs"), AS agent

Research only (no execution-server/chart/live change, no credentials, no downloads, UNTOUCHED not read, no account number written; live files are cited by their data/live names). Prereg `l2vast/struct48/prereg/ASSEMBLY.md` sha256 `24c918d0bb3e49d554af6308ee11217dc413688d736d074f7e6786b4a804ff99` (15 cells, ledger appended: cumulative 28,538 trials; DECISIONS.md 15:02Z) frozen before any cell was scored. Pre-holdout text `autopilot/REPORT_ASSEMBLY_PREHOLD.md` (WF-PRE + IS only) sha256 `70d61683686df9b4c42002affa115037b5377538acd10c9805ab4942f9834ba1`, logged with `log_holdout_look('ASSEMBLY')` before the holdout was computed. **The holdout is a RE-READ** for the ST/HM components (Set A, Set B and the pair holdouts were printed in earlier reports); the assembled series themselves are new and first read here. Verdict machinery: `s48score.verdict(cell,"sizing-lock-session")`, CI of record = 8-week circular block bootstrap, 10,000 draws (iid-week CI as sensitivity).

## 0. Answer

- **Job 1 (assembly ST10/HM10/WT7, per-book locks): DEAD, both rows.** `ASM_10_10_7_PB`: WF mean +$860/wk vs Set A (block CI [-10,515, 11,748], MDE $15,811), but SD +$2,114 and maxDD **+$136,533 worse** (537,851 vs 401,318), holdout mean -$4,951, 2x cost -$5,512, neighbours disagree, placebo rank (maxDD) 0.73. `ASM_S141010_7_PB` (ST/HM 14/10/10, WT7): mean +$7,003/wk (block CI [-5,833, 19,328]), SD +$21,532 (CI excludes 0 the wrong way), maxDD +$192,210 worse, 1.5x/2x cost negative, placebo 0.72. Against Set B both are below it on mean (-$7.3k and -$1.1k/wk) and far worse on maxDD (+$218k and +$273k).
- **Nothing is registered**: no CANDIDATE or PASS, so no `paper_all/ASSEMBLY_ST10_HM10_WT7.json`, no FORWARD_REGISTER edit and no message for the FWD owner (the live W44 score against this expectation does not apply).
- **Job 2 (pair alone, one cell, per-book vs combined give-back): DEAD as a per-book rule.** PB minus COMB: mean -422/wk (block CI [-10,869, 10,166], MDE $15,092), SD +13,358 (CI [3,600, 22,847]), maxDD +158,496 (weekly-path CI [48,078, 428,222]): per-book give-back has the same income and **more** risk than one combined give-back. Read the other way round the combined give-back reduces SD and maxDD with CIs excluding 0 at equal mean (not pre-registered in that direction, reported as an observation, not a verdict).
- **WT10 parameter set**: "WT 7 lots at stop 45 / target 0.75R" is **NOT** WT10. WT10 = the 10-MINUTE Wilder trail book (ATR14 x 3.0, no EMA, bracket 60/60, TH off, 8 NQ native, a separate-account sleeve). The 45/0.75R book is the chart/live WT (WT_MODAL: 1-minute, ATR20 x 2.0, EMA100, TH-loss 10/2/30, 7 lots). Details in section 1. This assembly uses the chart/live WT.
- **WT adds almost nothing** on the mapped basis: WT7 alone with its own per-book locks WF +$1,438/wk (SD $27.7k, maxDD $244.8k, 38 trades/wk; t = 0.6); with no mapped cost correction +$5,599/wk. Per-book locks make the books additive, so assembly = pair + WT7 exactly.

## 1. Which WT is "WT10"?  (from code and live parameter files)

| | WT10 (research name; `refresh_wt10.py`, `wt/WT10_FORWARD_CONFIG.md`, `library/WT10.parquet`) | chart / live WT (WTStrat in DualStrat2; research name WT_MODAL; REPORT_LIVE_AUDIT2 section 7, `night/b3_refs.py` WT_MODAL, `insurance/books/WT_MODAL_fullspan_trades.parquet`, `library/WT_LIVE.parquet`) |
|---|---|---|
| bars / signal | 10-MINUTE time bars; Wilder (RMA) ATR **14**, multiplier **3.0**, close, ratchet-trail flip, **no EMA filter** | 1-MINUTE bars; Wilder ATR **20**, multiplier **2.0**, close, ratchet-trail flip, **EMA 100** filter |
| bracket | stop 60 pts, target 60 pts (1.0R), OCO, no trail | **stop 45 pts, target 0.75R = 33.75 pts** |
| Trade Health | **OFF** | loss-side TH on: MinPoints **10** / Required **2** / windows 30 s (momentum 30 s/4 pts, stall 30 s/pullback 4 pts, efficiency 30 s/0.35, eval 1 s) = the "10/2/30" |
| size | 8 NQ native in the research harness (1 NQ forward test); a separate account, own rules | default quantity 7 (live file: qty 7) |
| account | separate account sleeve, own 5R/-2R day rule, own day cap/give-back, own week floor | the third book of the DualStrat2 account (day profit/loss/week loss limits 31,500 / 12,600 / 37,800) |

So "10" in WT10 is the **timeframe in minutes** (the WT-10 = WT on 10-minute bars); it is neither 10 lots nor TH 10/2/30. TH 10/2/30 belongs to the chart WT (REPORT_TH_AUDIT: "WT 10/2/30"). **Confirm/refute: "WT 7 lots at 45/0.75R" REFUTED as WT10 (it matches the chart/live WT = WT_MODAL).** Live evidence: the 10 WTStrat rows in `StratTrades_DualStrat2_<acct>.csv` (all 2026-10-23, qty 7): the one WT_Target exit prints +33.7 pts (= 0.75 x 45) and the 7 WT_LossExit exits print -8.2 to -12.6 pts (TH cut at about 10 pts, never the 45-pt stop); two further WT_Target rows have entry time 0001-01-01/entry 0 (logger artefacts, $0). Caveat: DualStrat source/chart-saved values were not read (REPORT_LIVE_AUDIT2 reads SetDefaults); the match above is on file values and trade behaviour.

## 2. Engine, rows, WT pricing, and the reconciliation of the two lock engines

- **Engine used: the ds2lib lock engine** as ported in `firmlib.Ctx.run` (identity-checked by firmlib) and generalised in `struct48/code/asm_lib.py` to three books and per-group R (per-book realised day rule, then group stages on the 1-s tape: cap/give-back arm/floor on 1-s mark-to-market, open lots exited at the next printed second, entries after a trigger in the group skipped). R per group = book lots x stop x $20 (ST10/HM10 $12,000, WT7 $6,300; session variant ST/HM nominal 14-lot R $16,800); combined groups use $12,000 (one 10-lot 60-pt book, as Set B uses one 14-lot book R for the pair).
- **Reconciliation with `riskeng_pb.py`** (WF 142 weeks, corrected P9, $4.84):

| engine | Set A mean/wk | SD | maxDD | Set B mean/wk | maxDD |
|---|---|---|---|---|---|
| ds2lib.run (native $4.36 commission, as shipped) | 24,853 | 104,185 | 399,470 | 33,247 | 319,431 |
| ds2lib.run with $4.84 | 24,980 | 104,524 | 401,318 | 33,119 | 320,103 |
| asm_lib (this report) | 24,980 | 104,524 | 401,318 | 33,119 | 320,103 |
| riskeng_pb (BK1; stateful single pass) | 24,983 (BK1 print 24,978) | 104,547 | 401,666 | 33,109 | 320,103 |

asm_lib equals ds2lib to the dollar at $4.84; riskeng_pb differs by +$3/wk (Set A) and -$10/wk (Set B), i.e. 0.03%: ds2lib applies the stages in sequence (day stage on the whole day, then the week stage on the survivors), riskeng_pb runs one time loop with day/week/halt state together, so a week floor and a day lock that fire in the same second resolve in a different order, and halted-group bookkeeping differs. Neither moves any verdict here. The shipped ds2lib runs at $4.36 commission and on an as-built P9 table unless `set_pts` is called (WF 35,853 as-built); I set the corrected table and $4.84. Row set: the ROWS_bench3 file was extended to 14,620 rows on 10-25 05:16 (through 10-23) but the corrected P9 table has 14,486 rows (through 2026-10-16): the sample is those 14,486 rows / 953 days; rows 10-19..10-23 use year x exit-type mapped points and appear only in section 8.
- **WT rows (no L2 replay exists for WT): MAPPED basis.** Signals regenerated with `ap_wt_core.wt_signals(20,2.0,100,1)` (1-min bars), entry at the next 1-min open, stop 45 / target 33.75 resolved on the 1-second tape by `firmlib.sim_rrt` (stop checked first within a second, gap rule: worse of stop and previous 1-s close), flat 16:55, bench3 entry gate, one open trade, 11,641 raw signals to 2026-10-23 (60 per week before locks). Points = raw +0.5 plus the **year x exit-type mean of (corrected P9 minus raw+0.5)** measured on the 14,486 ST/HM rows (stop exits +2.9 pts on average, targets -3.3; 2025-26 larger: +4.0/-4.3) and applied at full 14-lot size to 7 lots (conservative). Raw WT averages +1.2 pt/trade; after mapping +0.8 pt/trade. TH (loss 10/2/30, on in the live chart) is not replayed. Consequently every WT number below is **mapped, not direct-replayed**; the variant `ASM_10_10_7_PB_WTnocorr` brackets it.

## 3. Job 1 results (WF = 142 weeks 2024-02+, includes the holdout; mean / SD / maxDD (daily path) / worst week / trades per week; $, report scale)

| cell | WF | WF-PRE (75 wk) | HOLD (68 wk) | L8W | IS (52 wk) |
|---|---|---|---|---|---|
| Set A (14/14, live locks; same engine) | 24,980 / 104,524 / 401,318 / -137,081 / 35.8 | 17,558 / 97,533 / 401,318 / -136,494 / 31.9 | 32,799 / 110,543 / 267,133 / -137,081 / 39.5 | 34,191 / 109,399 / 267,133 / -98,918 / 40.5 | 13,671 / 95,946 / 407,253 / -136,337 / 26.8 |
| Set B (cap off, week floor 12R, 14/10/10) | 33,119 / 106,716 / 320,103 / -189,464 / 45.0 | 27,557 / 96,754 / 320,103 / -152,362 / 41.5 | 38,766 / 116,034 / 256,350 / -189,464 / 48.2 | 57,013 / 124,787 / 209,146 / -95,438 / 49.6 | 10,287 / 83,559 / 375,875 / -201,163 / 32.6 |
| ASM ST10/HM10/WT7 per-book | 25,840 / 106,637 / 537,851 / -221,854 / 88.0 | 23,675 / 99,161 / 537,851 / -199,368 / 79.6 | 27,848 / 113,488 / 498,491 / -221,854 / 96.0 | 17,643 / 148,949 / 440,622 / -148,934 / 110.6 | 7,276 / 91,532 / 575,785 / -247,240 / 57.6 |
| ASM ST/HM 14/10/10 + WT7 per-book | 31,984 / 126,056 / 593,528 / -275,334 / 95.8 | 27,073 / 116,697 / 465,699 / -202,621 / 86.5 | 36,930 / 134,644 / 593,528 / -275,334 / 104.5 | 30,360 / 178,949 / 534,748 / -213,349 / 122.6 | 8,834 / 101,597 / 580,187 / -230,595 / 62.8 |
| variant: combined give-back (3 books) | 25,023 / 88,157 / 369,281 / -221,854 / 63.0 | 23,020 / 80,341 / 259,166 / -143,004 / 56.8 | 26,864 / 95,632 / 360,529 / -221,854 / 69.0 | 9,809 / 102,962 / 239,101 / -104,235 / 70.6 | 17,817 / 65,300 / 291,466 / -118,198 / 44.9 |
| variant: combined week floor | 24,355 / 106,730 / 527,067 / -145,491 / 83.8 | 19,858 / 102,279 / 527,067 / -144,889 / 74.3 | 28,956 / 110,415 / 511,272 / -145,491 / 93.0 | 16,045 / 150,749 / 453,403 / -144,095 / 107.5 | 7,240 / 89,861 / 473,275 / -144,730 / 56.6 |
| variant: WT raw +0.5 | 30,001 / 105,776 / 522,433 / -220,783 / 82.8 | 25,834 / 98,582 / 522,433 / -190,774 / 75.9 | 34,156 / 112,151 / 474,575 / -220,783 / 89.2 | 23,774 / 143,154 / 419,196 / -139,087 / 102.0 | 10,307 / 92,460 / 546,433 / -245,927 / 57.6 |
| pair 10/10 per-book | 24,402 / 92,858 / 390,605 / -167,778 / 49.9 | 21,665 / 88,316 / 362,271 / -167,778 / 44.7 | 27,062 / 96,936 / 390,605 / -165,142 / 54.9 | 31,000 / 130,687 / 337,267 / -118,104 / 65.9 | 5,894 / 72,792 / 459,707 / -176,018 / 32.7 |
| pair 10/10 combined give-back | 24,824 / 79,500 / 232,109 / -150,963 / 39.1 | 22,423 / 70,926 / 232,109 / -150,963 / 35.8 | 27,106 / 87,552 / 216,924 / -150,162 / 42.2 | 29,729 / 88,152 / 190,809 / -70,656 / 40.9 | 13,569 / 64,315 / 209,594 / -83,976 / 28.3 |
| WT7 alone (own per-book locks) | 1,438 / 27,750 / 244,807 / -66,053 / 38.2 | 2,010 / 27,380 / 244,807 / -60,743 / 34.9 | 786 / 28,027 / 225,128 / -66,053 / 41.1 | -13,357 / 22,800 / 149,534 / -45,169 / 44.8 | 1,381 / 28,586 / 160,585 / -71,222 / 25.0 |

Cell format: mean / SD / maxDD / worst week / trades per week.

### 3a. Differences vs Set A and vs Set B, with intervals and the detectable effect (WF)

| cell | d mean vs A | 8-wk block CI (10k) | iid-week CI (10k) | P(d>0) | MDE mean (block, 80%) | d SD (block CI; MDE) | d maxDD daily path (weekly-path block CI; MDE) | d worst week | d mean vs Set B (block CI) | d maxDD vs Set B |
|---|---|---|---|---|---|---|---|---|---|---|
| ASM_10_10_7_PB | 860 | [-10,515, 11,748] | [-10,802, 12,510] | 0.56 | 15,811 | 2,114 [-9,008, 12,833]; 15,719 | 136,533 [-72,107, 496,166]; 391,259 | -84,774 | -7,278 [-19,931, 5,010] | 217,748 |
| ASM_S141010_7_PB | 7,003 | [-5,833, 19,328] | [-5,798, 19,797] | 0.86 | 18,087 | 21,532 [7,942, 34,394]; 18,918 | 192,210 [-48,567, 552,554]; 421,187 | -138,253 | -1,135 [-13,415, 10,637] | 273,425 |
| ASM_10_10_7_COMBGB | 43 | [-8,905, 9,443] | [-10,062, 10,591] | 0.50 | 13,325 | -16,366 [-24,873, -8,197]; 11,988 | -32,038 [-283,817, 170,704]; 328,615 | -84,774 | -8,095 [-17,887, 2,473] | 49,178 |
| ASM_10_10_7_PB_wkcomb | -626 | [-11,373, 9,969] | [-11,688, 10,324] | 0.46 | 15,256 | 2,206 [-7,414, 11,518]; 13,557 | 125,749 [-57,401, 454,959]; 362,836 | -8,410 | - | - |
| ASM_10_10_7_PB_WTnocorr | 5,021 | [-5,845, 15,686] | [-6,563, 16,535] | 0.82 | 15,440 | 1,252 [-9,722, 11,789]; 15,488 | 121,115 [-98,866, 391,547]; 336,496 | -83,703 | - | - |
| PAIR_10_10_PB | -579 | [-10,883, 9,238] | [-11,964, 10,904] | 0.46 | 14,351 | -11,665 [-21,570, -1,760]; 14,286 | -10,714 [-160,874, 282,834]; 308,313 | -30,697 | -8,717 [-19,495, 1,952] | 70,502 |
| PAIR_10_10_COMBGB | -157 | [-5,433, 5,678] | [-6,451, 6,668] | 0.47 | 7,968 | -25,023 [-29,541, -20,398]; 6,591 | -169,210 [-345,685, -29,615]; 228,344 | -13,883 | -8,295 [-15,251, -1,208] | -87,994 |

Detectable effect: the three cells of record have MDE $14-18k/wk (block), SD $16-19k, weekly-path maxDD $391-421k. The mean differences (+$0.9k, +$7.0k) are below the MDE: the test could neither confirm nor reject an income effect. The maxDD point estimates (+$137k, +$192k worse) are also below the weekly-path MDE ($391k, $421k): the *worsening* is not itself significant, and the verdict DEAD means "the lock/sizing criterion is not met" (it needs SD or maxDD **down** with CI, or mean up with CI > 0 and maxDD not worse), not "proved worse". Weekly-difference lag-1 autocorrelation 0.04 / 0.10.

### 3b. Windows: d vs Set A (mean / SD / maxDD), block CI of d mean (L8W has 8 weeks = one block, no CI)

| cell | WF-PRE | HOLD | L8W | IS |
|---|---|---|---|---|
| ASM_10_10_7_PB | 6,117 / 1,627 / 136,533 [-2,909, 14,856] | -4,951 / 2,946 / 231,358 [-25,255, 14,646] | -16,548 / 39,550 / 173,489 | -6,395 / -4,415 / 168,532 [-16,805, 4,250] |
| ASM_S141010_7_PB | 9,514 / 19,164 / 64,381 [-3,543, 22,759] | 4,131 / 24,102 / 326,395 [-17,679, 24,273] | -3,831 / 69,551 / 267,615 | -4,837 / 5,651 / 172,934 [-17,056, 6,569] |
| ASM_10_10_7_COMBGB | 5,462 / -17,193 / -142,152 [-6,626, 17,609] | -5,935 / -14,911 / 93,396 [-18,855, 8,851] | -24,382 / -6,437 / -28,032 | 4,146 / -30,647 / -115,787 [-12,728, 21,152] |
| PAIR_10_10_PB | 4,107 / -9,218 / -39,047 [-5,006, 12,162] | -5,737 / -13,607 / 123,472 [-23,617, 11,762] | -3,191 / 21,288 / 70,134 | -7,777 / -23,155 / 52,454 [-15,905, 455] |
| PAIR_10_10_COMBGB | 4,864 / -26,607 / -169,210 [-2,816, 13,547] | -5,693 / -22,991 / -50,210 [-11,636, 21] | -4,462 / -21,247 / -76,324 | -102 / -31,631 / -197,659 [-6,869, 7,100] |
| SETB | 9,999 / -779 / -81,216 [-3,600, 23,352] | 5,967 / 5,491 / -10,783 [-903, 13,330] | 22,821 / 15,388 / -57,987 | -3,384 / -12,387 / -31,378 [-9,893, 3,175] |

### 3c. Conditions of the verdict of record (s48score.verdict, sizing-lock-session)

| cell | verdict | passed | failed |
|---|---|---|---|
| ASM_10_10_7_PB | **DEAD** | mean_up | holdout_sign_agrees, placebo>=0.90, neighbours_agree, mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse, 2x_cost_sign, year_share>60% |
| ASM_S141010_7_PB | **DEAD** | mean_up, holdout_sign_agrees, neighbours_agree | placebo>=0.90, mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse, 2x_cost_sign, year_share>60% |
| job 2: PAIR_10_10_PB vs PAIR_10_10_COMBGB | **DEAD** | placebo>=0.90, neighbours_agree | mean_up, holdout_sign_agrees, mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse, 2x_cost_sign, year_share>60%, placebo<0.95 |

Notes on the conditions: holdout d mean = -4,951 (ASM_10_10_7_PB) / 4,131 (session variant); placebo of record = rank on the maxDD difference against 500 random-timing lock rules (give-back replaced by a random second inside each (day,book) group at the measured fire rate, 28% / 22% of groups; the week floor fired in 0 of 582 groups, so there is nothing to randomise there): rank 0.726 / 0.720 (mean-rank 0.00 / 0.00: random-timing locks earn **more** than the real give-back, median placebo d mean +$15.2k / +$18.5k/wk, because they cut fewer winners); neighbours (ST/HM 8 and 12 lots): d mean -4,021 / +5,740 (disagree) for 10/10/7, +6,230 / +8,563 (agree) for the session variant; 1.5x / 2x exact re-runs d mean: -4,530 / -5,512 and -1,172 / -3,090; the year-share ratio is meaningless when the WF gain is ~0 (10/10/7: 2025 = 515% of a +$0.9k gain) and for the session variant 2025 = 104% (fails 60%). Placebo and neighbour results are failures by themselves; the verdict is DEAD under any reading of the pass rule (no CI or sign condition can be rescued: maxDD worse in WF, HOLD and IS).

### 3d. Per-book and per-session split (WF, $/wk and trades/wk; book net attributed to the entry row)

| cell | ST | HM | WT | Asia | London | NY | total tr/wk |
|---|---|---|---|---|---|---|---|
| Set A | 11,535 (18.8) | 13,445 (17.0) | 0 (0.0) | 18,221 (17.3) | 2,503 (10.2) | 4,257 (8.3) | 35.8 |
| Set B | 15,131 (24.0) | 17,988 (21.1) | 0 (0.0) | 18,814 (18.3) | 6,941 (12.7) | 7,364 (14.1) | 45.0 |
| ASM 10/10/7 PB | 14,350 (26.0) | 10,052 (23.9) | 1,438 (38.2) | 17,662 (35.5) | 850 (27.7) | 7,328 (24.8) | 88.0 |
| ASM 14/10/10+7 PB | 16,960 (30.6) | 13,586 (27.1) | 1,438 (38.2) | 23,264 (35.5) | 64 (29.2) | 8,656 (31.0) | 95.8 |
| ASM 10/10/7 combined GB | 10,031 (18.2) | 11,682 (16.8) | 3,310 (28.0) | 16,454 (31.2) | 2,397 (17.9) | 6,172 (14.0) | 63.0 |
| pair PB | 14,350 (26.0) | 10,052 (23.9) | 0 (0.0) | 14,005 (19.7) | 2,232 (15.2) | 8,165 (15.0) | 49.9 |
| pair COMB | 11,472 (20.4) | 13,352 (18.8) | 0 (0.0) | 13,200 (18.3) | 4,356 (11.3) | 7,268 (9.6) | 39.1 |
| WT7 alone | 0 (0.0) | 0 (0.0) | 1,438 (38.2) | 3,657 (15.8) | -1,382 (12.5) | -837 (9.8) | 38.2 |

Per-book P&L is additive under per-book locks (no cap, per-book day rule/give-back/floor): ASM_10_10_7_PB = PAIR_10_10_PB + WT7 alone (24,402 + 1,438 = 25,840). WT contributes 38 trades/wk and 1.4k/wk with SD 27.7k and a standalone maxDD of 245k: WT7 is a high-turnover, near-zero-edge book on the mapped basis (raw mean +1.2 pt/trade, 0.8 after mapping), so the assembly's extra trades (88 vs Set A's 36 per week) are mostly WT and per-book re-entries.

### 3e. By year (WF, $/wk; d vs Set A)

| cell | 2024 (49 wk) | 2025 (53 wk) | 2026 (42 wk) |
|---|---|---|---|
| Set A | 14,672 | 21,155 | 40,644 |
| SETB | 25,860 (+11188) | 28,960 (+7805) | 45,257 (+4613) |
| ASM_10_10_7_PB | 18,871 (+4199) | 33,012 (+11857) | 23,690 (-16954) |
| ASM_S141010_7_PB | 19,228 (+4556) | 40,660 (+19504) | 34,394 (-6250) |
| ASM_10_10_7_COMBGB | 23,624 (+8952) | 15,798 (-5357) | 37,106 (-3538) |

### 3f. Peak-lot accounting vs the 50-contract limit (maximum concurrent lots over the whole 953-day sample, planned lots of taken trades; lock exits cannot raise it)

| cell | peak concurrent lots | by book | headroom to 50 |
|---|---|---|---|
| SETA | 28 | ST 14, HM 14 | 22 |
| SETB | 28 | ST 14, HM 14 | 22 |
| ASM_10_10_7_PB | 27 | ST 10, HM 10, WT 7 | 23 |
| ASM_S141010_7_PB | 35 | ST 14, HM 14, WT 7 | 15 |
| PAIR_10_10_PB | 20 | ST 10, HM 10 | 30 |

ST10+HM10+WT7 = 27 lots at most (all three books open at once happens); with session lots 14+14+7 = 35. The limit cannot bind on the planned lots. It is a planned-lot count: the stop-join exit orders (an entry-side join effect, scored in T4) are outside this sequence, as in BK1 where they put 56 lots on the books for Set A.

### 3g. Cost stress (exact engine re-runs of both arms at the same multiple; WF d mean vs Set A / d maxDD)

| cell | 1x | 1.5x | 2x | d maxDD at 2x |
|---|---|---|---|---|
| SETB | 8,138 | 2,577 | 3,362 | -87,575 |
| ASM_10_10_7_PB | 860 | -4,530 | -5,512 | 257,240 |
| ASM_S141010_7_PB | 7,003 | -1,172 | -3,090 | 303,724 |
| ASM_10_10_7_COMBGB | 43 | -2,728 | -1,533 | 23,984 |
| PAIR_10_10_PB | -579 | -3,925 | -3,157 | 62,864 |
| PAIR_10_10_COMBGB | -157 | -2,326 | -51 | -114,678 |

Set A itself moves with cost through lock-path dependence (BK1: 24,978 at 1x, 25,491 at 1.5x, 19,235 at 2x on riskeng); differences of a few $k/wk are inside that noise.

## 4. Job 2 - pair alone: ST10/HM10 per-book vs combined give-back (one cell, same caps/floors/day locks)

Cell: `PAIR_10_10_PB` (arm 2R keep 50% per book, R=$12,000 each) minus `PAIR_10_10_COMBGB` (arm 2R keep 50% on the pair equity, R=$12,000); cap off, per-book day -2R/+5R, per-book 12R week floor in both (the floor never fires: 0 of 388 weeks-by-book groups). Everything else identical (same rows, same sizing).

| window | d mean | block CI (10k) | iid CI | MDE (block) | d SD (block CI) | d maxDD daily path (weekly-path CI) | d worst week |
|---|---|---|---|---|---|---|---|
| WF | -422 | [-10,869, 10,166] | [-10,810, 9,811] | 15,092 | 13,358 [3,600, 22,847] | 158,496 [48,078, 428,222] | -16,814 |
| WFPRE | -758 | [-11,868, 9,480] | [-14,317, 12,848] | 15,230 | 17,390 [3,105, 32,385] | 130,162 [-35,854, 343,774] | -16,814 |
| HOLD | -45 | [-17,658, 17,640] | [-15,086, 14,556] | 25,500 | 9,384 [-3,652, 21,168] | 173,681 [53,916, 403,456] | -14,980 |
| IS | -7,675 | [-15,890, -53] | [-16,697, 1,325] | 11,297 | 8,476 [-2,031, 19,014] | 250,113 [3,575, 573,434] | -92,041 |

Own levels (WF): per-book WF 24,402 / 92,858 / 390,605 / -167,778 / 49.9; combined WF 24,824 / 79,500 / 232,109 / -150,963 / 39.1. Cost: d mean 1x/1.5x/2x = -422 / -1,599 / -3,106. By year d mean: 2024 -4,253; 2025 11,664; 2026 -11,182. Per-book split (WF $/wk, trades/wk): PB ST 14,350 (26.0) HM 10,052 (23.9); COMB ST 11,472 (20.4) HM 13,352 (18.8). Placebo (per-book random-timing vs COMB): rank maxDD 0.92, mean-rank 0.00; neighbours (8/8, 12/12): -337 / -506 (agree). Fire rate: per-book arm fired in 504 of 1,908 (day,book) groups, the combined arm in 463 of 958 days.

**Verdict (sizing/lock rule, per-book as the candidate): DEAD.** Mean is not up (-$422/wk, block CI [-10,869, 10,166], MDE $15,092: no income difference is detectable or present), the SD and maxDD are **up** (+$13,358 with CI [3,600, 22,847], maxDD +$158,496 with weekly-path CI [48,078, 428,222]: both exclude 0 on the wrong side for the per-book arm), holdout mean -$45, 2x cost -$3,106. Per-book vs combined is a risk difference, not an income difference: with per-book give-backs the second book keeps trading after the first book has locked (trades/wk 49.9 vs 39.1), and on correlated losing days (ST and HM stopped in the same direction) both books lose their full day allowance instead of the pair being halted once at 2R of *combined* equity.

**What this cell cannot see.** (1) Income: MDE is $15k/wk against a difference under $1k - the cell cannot tell whether either give-back scope earns more; only the risk side (SD, maxDD) has a detectable difference. (2) The maxDD result is path-dependent (the weekly-path CI [48k, 428k] is wide); the pre-holdout (WF-PRE) difference +130k and holdout +174k agree in sign, IS +250k also. (3) A *different* per-book parameterisation (arm at 3R/4R, keep 67%, different R for the combined arm) - one point of a grid only; the combined arm's R ($12,000, one book) and arm level were fixed in the prereg, not optimised. (4) Real-time lock behaviour: 1-s mark-to-market proxy for tick, no live ComboLock latency, no queue effect of 10-lot vs 14-lot exits (P9 points are 14-lot fills), no TH, no join misses (live join rate 0.47 vs replay 0.83 per JOIN_RECON). (5) Operational feasibility: the live DualStrat2 implements the give-back as a combined lock; per-book give-back is not a setting that exists in the live chart as far as the parameter notes show (ComboGiveBackArmR/Pct are combined) - this is a replay-only comparison. (6) Cross-book dependence beyond two books: with WT7 added (section 3) the same per-book arm is again worse on risk (ASM_10_10_7_PB vs the combined-give-back variant: SD +18.5k, maxDD +169k WF).

## 5. Three tiers (V2)

- PASS: none.
- CANDIDATE: none.
- DEAD: `ASM_10_10_7_PB` (mean +860, maxDD +136,533, holdout -4,951, neighbours disagree, placebo 0.73, 2x -5,512); `ASM_S141010_7_PB` (mean +7,003, SD +21,532, maxDD +192,210, 1.5x/2x negative, placebo 0.72, year share 104%); job 2 `PAIR_10_10_PB` vs `PAIR_10_10_COMBGB` (no income difference, per-book has more SD/maxDD). Modelling variants (wkcomb, WTnocorr, COMBGB) and neighbours carry no separate verdict (ruling 2026-10-25 item 2) and none would change the tier: the variant with a combined give-back (`ASM_10_10_7_COMBGB`: WF 25,023/wk, SD 88,157, maxDD 369,281, d mean 43 vs Set A, SD -16,366, maxDD -32,038, holdout d mean -5,935) is a risk reduction at equal income that fails the holdout-sign and year-share conditions; it is *not* the user's per-book design and is not registered.

## 6. Effect of the WT mapping and of WT in the assembly

WT7 alone (own per-book locks, TH off, mapped): WF +$1,438/wk, SD $27,750, maxDD $244,807, worst -$66,053, 38.2 trades/wk; WF-PRE +$2,010, HOLD +$786, IS +$1,381. Without the mapped correction (raw +0.5): +$5,599/wk in the assembly (+$4,161 more) and the assembly WF mean +$5,021 vs Set A (block CI [-5,845, 15,686]) - still maxDD +$121k worse, still DEAD. The WT book cannot rescue the assembly in either pricing; the maxDD problem comes from the per-book lock design, not from WT (PAIR_10_10_PB alone: maxDD 390,605 vs the combined-give-back pair 232,109).

## 7. What these cells cannot see (assembly)

1. WT is on a mapped basis (not L2-replayed); a direct WT replay with TH-loss 10/2/30 (live) was not possible without the tick TH port. 2. P9 fills are 14-lot; 10/7-lot queue effects not modelled (BK1 caveat). 3. The 8-week-block MDEs ($15-18k/wk mean, $390-420k weekly-path maxDD) exceed every effect measured, so neither the mean difference nor the maxDD worsening is statistically established; DEAD is the criterion verdict, not a proof. 4. Per-book "week floor 12R_b" never fires (0 groups): it is vacuous per book; a combined 12R floor on the account (variant) fires in 21 week-groups and lowers the worst week by $76k at -$626/wk. 5. Ext rows (10-19..10-23) have no L2 P9 points and are mapped; they are not in any verdict. 6. The holdout is a re-read for the ST/HM components.

## 8. What the live W43 data say (informational, never counted; official forward weeks start W44)

The live file `StratTrades_DualStrat2_<acct>.csv` starts at the first push, **exits from 2026-10-20 14:33 ET**, so it covers W43 only from Tuesday afternoon (Mon 10-19 and Tue morning are not in it). Live exits 10-20 14:33..10-23 16:45: ST -94,105 (24 trades), HM -90,475 (15), WT -5,170 (10 rows: 8 real trades + 2 zero-dollar logger rows) = **-189,750** at lots 14/14/7. The file also carries ST/HM LossExit/ProfitExit rows with qty 8 (TH-type exits) alongside the stop-join exits. Replay of the same week on the 1-s tape (TH off; ext-row points are year x exit-type mapped, not L2 P9; label days = 18:00 ET start; in no verdict):

| replay | Mon 10-19 | Tue 10-20 | Wed 10-21 | Thu 10-22 | Fri 10-23 | 10-20..10-23 | full W43 | ST / HM / WT (full W43) | trades |
|---|---|---|---|---|---|---|---|---|---|
| Set A (ST/HM 14/14) | 36,469 | -79,700 | -48,657 | 17,801 | -62,957 | -173,514 | -137,044 | -59,605 / -77,439 / 0 | 57 |
| Set B | 36,469 | -61,612 | -34,955 | 17,801 | -86,227 | -164,993 | -128,524 | -55,769 / -72,755 / 0 | 71 |
| ASM 10/10/7 per-book | 39,629 | -6,622 | -47,913 | 64,185 | -36,077 | -26,427 | 13,202 | 37,494 / -26,953 / 2,661 | 114 |
| ASM 14/10/10+7 per-book | 50,249 | -11,806 | -48,113 | 87,216 | -104,372 | -77,075 | -26,825 | - | - |
| variant combined give-back | 13,074 | 15,981 | -47,913 | 12,372 | -86,284 | -105,844 | -92,770 | -27,812 / -63,524 / -1,434 | 80 |
| pair per-book | 26,550 | -13,158 | -34,755 | 49,837 | -17,932 | -16,009 | 10,541 | 37,494 / -26,953 / 0 | 71 |
| pair combined | 26,050 | -56,929 | -34,755 | 12,715 | -68,140 | -147,108 | -121,059 | -65,745 / -55,313 / 0 | 71 |
| WT7 alone | 13,080 | 6,536 | -13,158 | 14,348 | -18,145 | -10,419 | 2,661 | 0 / 0 / 2,661 | 43 |

Reading: Set A replayed 10-20..10-23 = -173,514 against live -189,750 from 10-20 14:33 (the live file is missing the morning of 10-20, and per JOIN_RECON omits the 10-21 04:00 ST trade of -$17.7k; live join rate 0.47 vs 0.83 in replay): same sign and size, as the weekly replay-vs-live checks show. The assembly designs differ from Set A on W43 by $50-150k in either direction purely by path (per-book give-backs let the assembly end the week at +$13k, the combined-give-back variant at -$93k, Set A at -$137k): one week, weekly SD of the difference ~$60-70k, uninformative for the design. WT: live WT started 10-23 10:31; the TH-off replay of its 6 entries from 10:31 on is -$14.8k (4 stops, 2 targets) against live -$5.2k (8 entries: 7 TH cuts at -8..-13 pts, 1 target +33.7): consistent with TH shortening losers on a down day, one day, no information on the design question. Per-trade join/slip reconciliation for W43 is JOIN_RECON.md (EXT agent).

## 9. Files and reproduction

Code: `l2vast/struct48/code/asm_lib.py` (engine + WT rows), `asm_run.py` (all series, cost multiples, placebos; corepool), `asm_score.py`, `asm_pre.py`, `asm_final.py`, `asm_w43.py`, `asm_report.py`, `asm_prereg.py`. Outputs: `out/ASM/series.pkl`, `placebos.pkl`, `final_rows.pkl`, `pre_rows.json`, `w43.pkl`. Prereg `prereg/ASSEMBLY.md` (+`.sha256`, `ASSEMBLY_cells.json`). Ledger line track ASSEMBLY (15 cells). Run time of the whole panel with 500 placebos x 3 sets: 33 s on 6 workers (the engine replays a cell in 0.2 s). Structural question for MORNING.md (not pausing anything): the per-book give-back is the harmful ingredient; the data say a combined give-back with Set-B sizing already holds the risk benefit (PAIR_10_10_COMBGB: SD -25k, maxDD -169k vs Set A at equal mean) - does the user want a three-book combined-lock assembly scored as a new cell (it would be a new prereg; it is not the per-book design asked for)?