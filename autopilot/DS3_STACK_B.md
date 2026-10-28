# DS3_STACK_B - range-day rules on the live stack (T-STACK B, D3SKB, 2026-10-28)
Research only; no live / execution / chart change. Prereg `l2vast/ds3/prereg/STK_B_prereg.md` sha256 3393cdd663086347b900ccd71aa242d22aba24236f066fea4eb98037c8a9c753 (in DECISIONS.md and trials ledger before any rule was scored; no smoke-test numbers existed before it; PRE-only text `autopilot/DS3_STACK_B_PREHOLD.md`, look logged as track STK_B; HOLD and X read once, after it). Code `l2vast/ds3/code/stk_b/` (b_labels, b_lib, b_run, b_prehold, b_report); outputs `l2vast/ds3/out/stk_b/` (labels.parquet, pre_results.json, final_results.json, report_tables.md, **stk_b_pre_weekly.parquet** = PRE-only weekly delta series per cell, raw and lot-matched, plus the base, for the F combine).

## Verdict
**0 CONFIRMED, 0 CANDIDATE, 0 LEAD, 11 DEAD (11 cells scored; B11 not scored because no weekday / opex / month-end / holiday-eve group flagged on PRE). No ex-ante first-hour / overnight / flip-count range-day label lets the stack halve or stop its trend books on "range" days in a way that is distinguishable from zero or from shuffled labels.** The ex-post range-day knowledge is worth a lot (halving trend books from 10:30 on ex-post range days: +$11.5k/wk PRE, +$7.3k HOLD; stopping their entries +$23.1k PRE, +$14.5k HOLD, worst-20 weeks +$459k PRE) but the best ex-ante rule captures only 4-13% of the weekly $ of that reference (more of its worst-20 relief: 41-89% in single windows, see share table), and every cell's paired CI includes zero with the effect below its MDE.
- Labels chosen on PRE by the written stage-1 rule (Welch t of unflagged minus flagged post-10:30 trend-book P&L per day): none reaches t=2 (best ON_085 t=1.54, FLIP 1.43, FH60_07 0.50). L1 = ON_085 (overnight range < 0.85 x 20-day median, flags 36% of days), L2 = FLIP (>= 32 first-hour direction flips = PRE p75, 27%), L3 = FH60_07 (first-hour range < 0.7x median, 20%). The audit-style "first-hour narrow" label (FH60_07) is rank 3 with t=0.5, i.e. the 10:30 first-hour range is a weak ex-ante signal for this stack; OVL (overlap) t=0.23 and ES/NQ disagreement t=0.22 are weaker still; the 0.5x labels are below the 8% share floor; 5 of 12 candidates fail the eligibility rule (share below 8% or flagged-day mean not below unflagged). Note: the prereg text says "14 candidate labels"; the list is 12 (3x3 range labels + OVL + FLIP + ESDIS). Best-of-N therefore counts 12 cells + 12 label draws (24) in this section, F_total=60 for the program.
- Closest to a lead (unchanged verdict, DEAD under the gates): **ON_085 halve trend books, SM unchanged (B02)** and its stop-entries twin B03: the sign of the lot-matched weekly delta is positive in all three windows (B02 PRE +1,460, HOLD +2,289, X +3,974 per week; B03 +2,983 / +4,692 / +8,142) and the worst-20-weeks improve in every window (B02 +103k PRE, +40k HOLD, +55k X lot-matched), the control (1.5x on the same days, B12) has the opposite sign in all windows (so the direction is shown, not assumed). But HOLD CI [-5,714, +6,677] vs MDE 8,813, shuffled-label rank 0.91 / 0.89 / 0.96 (PRE/HOLD/X, needs 0.95 in PRE and HOLD), the 2023 span carries most of the gain (3,703/wk in 2023 vs 565 in 2024, 896 in 2025, -1,103 in 2026 on 6 weeks), HOLD worst week gets 2.8k worse lot-matched, X worst week worse, and HOLD best-of-60 p=0.358 (bar 0.00083). Failed gates for B02: G2,G3,G4,G5,G6,G8.
- Trend vs SM: B04 (stop ALL books incl. SM on ON_085 days) has the same sign as B03 and about the same size (HOLD LM +4,180 vs +4,692), so on these days SM is neither helped nor hurt measurably; the audit's SM exception is neither supported nor refuted (SM is 8% of trades).
- Trade-off line (B02, PRE, 74 weeks): in the stack's good weeks (top half by base $, 37 weeks) the rule gives up $150,582 raw (lot-matched: $35,584 given up); in the 14 worst PRE weeks it saves $116,562 raw ($76,401 lot-matched); over the 8 base-worst-20 weeks that fall in PRE it saves $132,091 raw / $103,106 LM; PRE-only worst-20 set (20 weeks, base -$2.33M): +$192,517 raw / +$146,828 LM. Net weekly mean +$514 raw (MDE 5,947). In HOLD: gives up $54,659 in good weeks (LM: +$12,349, i.e. LM gives up nothing), saves $73,171 in the 6 worst (LM $48,521). Lot-matched means exposure is rescaled to the base lot-seconds (c about 1.02), which is a slight up-sizing of everything.
- Selection for F: the PRE-selected rule I would carry is **B02** (the only cells passing G1, G3 and G7 in PRE are B01 and B02; B02 has the larger PRE LM mean, 0.91 vs 0.87 rank): flag = overnight range (18:00 to 09:29 ET) < 0.85 x median of the prior 20 label days; action = from 10:30 to 18:00 ET halve ST, HM, WT, KB, PE entries, SM unchanged. By F's stacking test (HOLD worst-20 improves, HOLD mean not down by more than MDE) B02 passes (HOLD worst-20 inside HOLD +40k LM, mean +955 raw), but it fails the section gates, so by the directive ("only cells that pass A-E individually") it is not eligible for F unless F relaxes to a lead tier. Flag to F: B02 is the section's best by the stacking test and DEAD by the section gates.

## Method and limitations (read before using any number)
- Trade table, not a lock-engine re-run: halving multiplies a trade's P&L by 0.5 (the stack's lots are all <= 14 so sweep cost is 0 on every row; linear is exact up to lock feedback), blocking removes it. Removing a trade does not free the busy chain, the per-book 2R/5R day entry test or the give-back arm of that book, which the exact engine would do. Size cells (halve) are close to exact (the locks run in nominal-lot R); block cells (B03, B04, B07) are the most approximate. Because all 11 cells are DEAD with CIs spanning zero, I did not spend the engine on them; an engine re-run would only matter for B02/B03 if F relaxed to LEAD. Not done, disclosed.
- Window: the audit table runs to 2026-10-16; I dropped every trade after label day 2026-02-06 (UNTOUCHED never read; ES bars filtered by timestamp at read). Hence 149 weeks (X 43, PRE 74, HOLD 32 weeks to 2026-02-06; 2026 has 6 weeks), baseline mean 39,564/wk all, WF (2024-02..2026-02-06) 46,785/wk vs the audit's 45,947 (different end date). The worst-20 weeks fixed "on all weeks" = the 20 worst of these 149 weeks (base -$3.53M); the PRE-only worst-20 = -$2.33M. Per window the fixed set is restricted to the weeks in that window (PRE 8, HOLD 4, X 8 of them); the PRE-only set exists only in PRE, so G7 uses the fixed set in HOLD (documented deviation from the prereg wording "both sets in HOLD").
- Action window: entries with ET time in [10:30, 18:00) on the label day; the flag uses data complete by 10:30 (overnight range, 09:30-10:29 bars, ES 09:30-10:29). Trades held through 10:30 are untouched.
- Placebo: shuffled-label = flag vector permuted over the days of the same window (200 draws, count preserved, seeded) -- stricter than the prereg's pooled-within-year (disclosed deviation); shifted = flag moved by +-1..5 days (10 shifts), rank = share of shifts below the true value. MDE = 2.8 x SD(paired diff)/sqrt(weeks). Lot-matched = cell weekly x (base lot-seconds / cell lot-seconds) in that window.
- Not tested: (c) "raise the TH-loss threshold" needs the engine's day-entry test with feedback; no trade-table proxy is faithful, so no cell. Cell cap 12 and F (cells) = 11 scored.

## Stage-1 label screen (PRE; mean post-10:30 trend-book $ per day)
| label    |   share |   n_flag |   mean_flag |   mean_unflag |      t | eligible   |
|:---------|--------:|---------:|------------:|--------------:|-------:|:-----------|
| ON_085   |   0.357 |      130 |   -1088.13  |       3825.92 |  1.535 | True       |
| FLIP     |   0.269 |       98 |   -1552.42  |       3405.81 |  1.425 | True       |
| FH60_07  |   0.198 |       72 |     690.642 |       2411.24 |  0.497 | True       |
| FH30_05  |   0.058 |       21 |     374.002 |       2174.79 |  0.477 | False      |
| OVL      |   0.288 |      105 |    1505.25  |       2300.22 |  0.233 | True       |
| ESDIS    |   0.165 |       60 |    1290.27  |       2224.97 |  0.22  | True       |
| ON_05    |   0.047 |       17 |     868.699 |       2129.8  |  0.139 | False      |
| FH30_085 |   0.332 |      121 |    1799.39  |       2206.1  |  0.131 | True       |
| FH60_05  |   0.066 |       24 |    1835.62  |       2087.51 |  0.062 | False      |
| ON_07    |   0.198 |       72 |    2312.29  |       2011.38 | -0.074 | False      |
| FH60_085 |   0.332 |      121 |    2697.53  |       1758.88 | -0.302 | False      |
| FH30_07  |   0.214 |       78 |    3416.12  |       1704.02 | -0.513 | False      |

B11 group screen (PRE, 95% bootstrap by week of mean post-10:30 trend-book $/day; flags only if mean<0 and CI high<0 and n>=8): none flags (Mon -544 [-5,884, 5,179] is the lowest; hol_eve n=4).

## All cells (verdict, windows: raw weekly delta [95% CI] (MDE); LM = lot-matched delta)
Gates: G1 LM mean>0 PRE&HOLD; G2 HOLD CI low>0; G3 LM maxDD<=base & worst-week>=base PRE&HOLD; G4 shuffle AND shift rank>=0.95 PRE&HOLD; G5 >=2 of 2024/25/26 positive, no year>60%; G6 X span LM mean>=0, maxDD, worst; G7 worst-20 improves (fixed set PRE&HOLD, PRE-only set PRE); G8 HOLD p<=0.05/60.

| cell   | rule                                         | tier   | failed                  | gates   | PRE dRaw [CI] (MDE)           |   PRE dLM | HOLD dRaw [CI] (MDE)            |   HOLD dLM | X dRaw [CI] (MDE)              |   X dLM |
|:-------|:---------------------------------------------|:-------|:------------------------|:--------|:------------------------------|----------:|:--------------------------------|-----------:|:-------------------------------|--------:|
| B01    | ON_085 halve ALL                             | DEAD   | G2,G3,G4,G5,G6,G8       | 2/8     | -23 [-4,632,4,547] (6,399)    |       997 | 649 [-5,858,6,510] (8,836)      |      2,037 | 3,624 [-2,099,9,444] (8,381)   |   4,276 |
| B02    | ON_085 halve trend books, SM unchanged       | DEAD   | G2,G3,G4,G5,G6,G8       | 2/8     | 514 [-3,845,4,766] (5,947)    |     1,460 | 955 [-5,714,6,677] (8,813)      |      2,289 | 3,377 [-2,063,8,796] (7,873)   |   3,974 |
| B03    | ON_085 stop trend-book entries               | DEAD   | G2,G3,G4,G5,G6,G8       | 2/8     | 1,028 [-7,690,9,533] (11,893) |     2,983 | 1,909 [-11,428,13,355] (17,626) |      4,692 | 6,755 [-4,126,17,593] (15,746) |   8,142 |
| B04    | ON_085 stop ALL entries                      | DEAD   | G2,G3,G4,G5,G6,G8       | 2/8     | -47 [-9,264,9,095] (12,797)   |     2,041 | 1,298 [-11,715,13,020] (17,672) |      4,180 | 7,249 [-4,199,18,888] (16,763) |   8,777 |
| B05    | FLIP halve ALL                               | DEAD   | G2,G3,G4,G8             | 4/8     | 1,295 [-2,208,4,981] (5,303)  |     1,930 | -633 [-7,875,5,296] (9,211)     |        213 | 2,548 [-2,251,7,433] (7,102)   |   2,928 |
| B06    | FLIP halve trend books                       | DEAD   | G1,G2,G3,G4,G5,G8       | 2/8     | 1,065 [-2,451,4,597] (5,114)  |     1,657 | -865 [-7,705,4,328] (8,658)     |        -60 | 2,334 [-1,712,6,609] (6,044)   |   2,682 |
| B07    | FLIP stop trend-book entries                 | DEAD   | G1,G2,G3,G4,G5,G8       | 2/8     | 2,130 [-4,903,9,193] (10,227) |     3,357 | -1,730 [-15,410,8,656] (17,316) |       -121 | 4,668 [-3,423,13,218] (12,088) |   5,443 |
| B08    | ON_085 OR FLIP halve trend books             | DEAD   | G2,G3,G4,G5,G6,G8       | 2/8     | -57 [-4,789,4,719] (6,831)    |     1,230 | -874 [-9,395,5,964] (11,134)    |        809 | 3,925 [-2,362,10,178] (9,115)  |   4,779 |
| B09    | >=2 of ON_085,FLIP,FH60_07 halve trend books | DEAD   | G2,G3,G4,G8             | 4/8     | 1,160 [-2,097,4,571] (4,778)  |     1,769 | 445 [-4,911,4,666] (6,786)      |      1,246 | 2,041 [-1,232,5,329] (4,747)   |   2,280 |
| B10    | ON_085 0.25x trend books                     | DEAD   | G2,G3,G4,G5,G6,G8       | 2/8     | 771 [-5,767,7,149] (8,920)    |     2,213 | 1,432 [-8,571,10,016] (13,219)  |      3,475 | 5,066 [-3,095,13,195] (11,809) |   6,033 |
| B12    | ON_085 CONTROL 1.5x trend books              | DEAD   | G1,G2,G3,G4,G5,G6,G7,G8 | 0/8     | -514 [-4,766,3,845] (5,947)   |    -1,400 | -955 [-6,677,5,714] (8,813)     |     -2,182 | -3,377 [-8,796,2,063] (7,873)  |  -3,794 |



## Top cells regardless of verdict (fewest failed gates): B05 FLIP halve ALL and B09 vote-of-3 halve trend books (4/8 pass; both fail G2 CI, G3 maxDD/worst, G4 placebo, G8). By effect size the best are B03/B04/B10 (ON_085 stop/quarter lots), HOLD LM +4,692/+4,180/+3,475, all inside their MDE (17,626/17,672/13,219).

## Risk by window (SD, maxDD, worst week; base vs cell vs lot-matched)
| cell   | win   |   n |   base_mean |   cell_mean |   expo_ratio |   c_LM |   sd_base |   sd_cell |   dd_base |   dd_cell |   dd_LM |   worst_base |   worst_cell |   worst_LM |
|:-------|:------|----:|------------:|------------:|-------------:|-------:|----------:|----------:|----------:|----------:|--------:|-------------:|-------------:|-----------:|
| B01    | PRE   |  74 |      43,808 |      43,784 |        0.977 |  1.023 |   132,383 |   127,731 |   409,229 |   336,518 | 344,359 |     -306,664 |     -298,786 |   -305,748 |
| B01    | HOLD  |  32 |      53,670 |      54,319 |        0.975 |  1.026 |   153,219 |   148,581 |   578,442 |   570,265 | 584,831 |     -318,557 |     -317,425 |   -325,533 |
| B01    | X     |  43 |      21,762 |      25,386 |        0.975 |  1.026 |   113,859 |   108,972 |   460,909 |   501,594 | 514,467 |     -157,300 |     -174,460 |   -178,938 |
| B01    | WF    | 106 |      46,785 |      46,965 |        0.977 |  1.024 |   138,333 |   133,733 |   578,442 |   570,265 | 583,917 |     -318,557 |     -317,425 |   -325,025 |
| B02    | PRE   |  74 |      43,808 |      44,322 |        0.979 |  1.021 |   132,383 |   128,095 |   409,229 |   340,383 | 347,647 |     -306,664 |     -298,786 |   -305,163 |
| B02    | HOLD  |  32 |      53,670 |      54,625 |        0.976 |  1.024 |   153,219 |   148,208 |   578,442 |   563,288 | 577,042 |     -318,557 |     -313,738 |   -321,399 |
| B02    | X     |  43 |      21,762 |      25,139 |        0.977 |  1.024 |   113,859 |   109,601 |   460,909 |   509,777 | 521,879 |     -157,300 |     -178,064 |   -182,291 |
| B02    | WF    | 106 |      46,785 |      47,432 |        0.978 |  1.022 |   138,333 |   133,849 |   578,442 |   563,288 | 575,803 |     -318,557 |     -313,738 |   -320,709 |
| B03    | PRE   |  74 |      43,808 |      44,835 |        0.958 |  1.044 |   132,383 |   126,329 |   409,229 |   407,145 | 424,901 |     -306,664 |     -290,909 |   -303,597 |
| B03    | HOLD  |  32 |      53,670 |      55,579 |        0.952 |  1.05  |   153,219 |   145,222 |   578,442 |   548,133 | 575,572 |     -318,557 |     -308,918 |   -324,383 |
| B03    | X     |  43 |      21,762 |      28,517 |        0.954 |  1.049 |   113,859 |   108,356 |   460,909 |   558,645 | 585,815 |     -157,300 |     -206,651 |   -216,701 |
| B03    | WF    | 106 |      46,785 |      48,079 |        0.957 |  1.045 |   138,333 |   131,705 |   578,442 |   548,133 | 573,045 |     -318,557 |     -308,918 |   -322,958 |
| B04    | PRE   |  74 |      43,808 |      43,761 |        0.954 |  1.048 |   132,383 |   126,009 |   409,229 |   399,416 | 418,473 |     -306,664 |     -290,909 |   -304,789 |
| B04    | HOLD  |  32 |      53,670 |      54,968 |        0.95  |  1.052 |   153,219 |   145,993 |   578,442 |   562,088 | 591,555 |     -318,557 |     -316,293 |   -332,875 |
| B04    | X     |  43 |      21,762 |      29,010 |        0.95  |  1.053 |   113,859 |   107,501 |   460,909 |   542,280 | 570,846 |     -157,300 |     -199,444 |   -209,950 |
| B04    | WF    | 106 |      46,785 |      47,144 |        0.953 |  1.049 |   138,333 |   131,752 |   578,442 |   562,088 | 589,661 |     -318,557 |     -316,293 |   -331,809 |
| B05    | PRE   |  74 |      43,808 |      45,103 |        0.986 |  1.014 |   132,383 |   129,426 |   409,229 |   414,663 | 420,498 |     -306,664 |     -298,348 |   -302,546 |
| B05    | HOLD  |  32 |      53,670 |      53,037 |        0.984 |  1.016 |   153,219 |   148,457 |   578,442 |   567,647 | 576,698 |     -318,557 |     -318,557 |   -323,637 |
| B05    | X     |  43 |      21,762 |      24,309 |        0.985 |  1.016 |   113,859 |   112,105 |   460,909 |   396,659 | 402,872 |     -157,300 |     -146,353 |   -148,645 |
| B05    | WF    | 106 |      46,785 |      47,498 |        0.986 |  1.015 |   138,333 |   134,783 |   578,442 |   567,647 | 575,938 |     -318,557 |     -318,557 |   -323,210 |
| B06    | PRE   |  74 |      43,808 |      44,873 |        0.987 |  1.013 |   132,383 |   129,193 |   409,229 |   425,724 | 431,337 |     -306,664 |     -298,348 |   -302,282 |
| B06    | HOLD  |  32 |      53,670 |      52,805 |        0.985 |  1.015 |   153,219 |   148,188 |   578,442 |   567,647 | 576,306 |     -318,557 |     -318,557 |   -323,417 |
| B06    | X     |  43 |      21,762 |      24,096 |        0.986 |  1.014 |   113,859 |   111,663 |   460,909 |   412,234 | 418,187 |     -157,300 |     -146,353 |   -148,466 |
| B06    | WF    | 106 |      46,785 |      47,267 |        0.986 |  1.014 |   138,333 |   134,539 |   578,442 |   567,647 | 575,467 |     -318,557 |     -318,557 |   -322,946 |
| B07    | PRE   |  74 |      43,808 |      45,938 |        0.974 |  1.027 |   132,383 |   127,867 |   409,229 |   442,219 | 454,036 |     -306,664 |     -290,033 |   -297,783 |
| B07    | HOLD  |  32 |      53,670 |      51,940 |        0.97  |  1.031 |   153,219 |   145,105 |   578,442 |   556,852 | 574,104 |     -318,557 |     -318,557 |   -328,427 |
| B07    | X     |  43 |      21,762 |      26,430 |        0.972 |  1.029 |   113,859 |   111,239 |   460,909 |   366,877 | 377,628 |     -157,300 |     -149,047 |   -153,415 |
| B07    | WF    | 106 |      46,785 |      47,750 |        0.973 |  1.028 |   138,333 |   132,631 |   578,442 |   556,852 | 572,408 |     -318,557 |     -318,557 |   -327,457 |
| B08    | PRE   |  74 |      43,808 |      43,751 |        0.971 |  1.029 |   132,383 |   125,532 |   409,229 |   364,936 | 375,672 |     -306,664 |     -290,471 |   -299,017 |
| B08    | HOLD  |  32 |      53,670 |      52,797 |        0.969 |  1.032 |   153,219 |   146,483 |   578,442 |   553,283 | 570,911 |     -318,557 |     -313,738 |   -323,734 |
| B08    | X     |  43 |      21,762 |      25,686 |        0.968 |  1.033 |   113,859 |   109,840 |   460,909 |   485,149 | 501,280 |     -157,300 |     -150,348 |   -155,347 |
| B08    | WF    | 106 |      46,785 |      46,482 |        0.971 |  1.03  |   138,333 |   131,560 |   578,442 |   553,283 | 569,946 |     -318,557 |     -313,738 |   -323,186 |
| B09    | PRE   |  74 |      43,808 |      44,968 |        0.987 |  1.014 |   132,383 |   130,469 |   409,229 |   395,790 | 401,148 |     -306,664 |     -306,664 |   -310,815 |
| B09    | HOLD  |  32 |      53,670 |      54,115 |        0.985 |  1.015 |   153,219 |   149,840 |   578,442 |   574,313 | 582,815 |     -318,557 |     -315,218 |   -319,885 |
| B09    | X     |  43 |      21,762 |      23,802 |        0.99  |  1.01  |   113,859 |   110,847 |   460,909 |   436,862 | 441,246 |     -157,300 |     -150,231 |   -151,739 |
| B09    | WF    | 106 |      46,785 |      47,729 |        0.986 |  1.014 |   138,333 |   135,945 |   578,442 |   574,313 | 582,295 |     -318,557 |     -315,218 |   -319,599 |
| B10    | PRE   |  74 |      43,808 |      44,578 |        0.969 |  1.032 |   132,383 |   126,887 |   409,229 |   373,764 | 385,857 |     -306,664 |     -294,848 |   -304,388 |
| B10    | HOLD  |  32 |      53,670 |      55,102 |        0.964 |  1.037 |   153,219 |   146,452 |   578,442 |   555,710 | 576,317 |     -318,557 |     -311,328 |   -322,872 |
| B10    | X     |  43 |      21,762 |      26,828 |        0.965 |  1.036 |   113,859 |   108,590 |   460,909 |   534,211 | 553,463 |     -157,300 |     -192,357 |   -199,289 |
| B10    | WF    | 106 |      46,785 |      47,755 |        0.967 |  1.034 |   138,333 |   132,474 |   578,442 |   555,710 | 574,440 |     -318,557 |     -311,328 |   -321,821 |
| B12    | PRE   |  74 |      43,808 |      43,294 |        1.021 |  0.98  |   132,383 |   138,960 |   409,229 |   482,696 | 472,817 |     -306,664 |     -314,541 |   -308,103 |
| B12    | HOLD  |  32 |      53,670 |      52,715 |        1.024 |  0.977 |   153,219 |   160,064 |   578,442 |   593,597 | 579,777 |     -318,557 |     -323,377 |   -315,848 |
| B12    | X     |  43 |      21,762 |      18,384 |        1.023 |  0.977 |   113,859 |   120,811 |   460,909 |   485,675 | 474,667 |     -157,300 |     -189,241 |   -184,952 |
| B12    | WF    | 106 |      46,785 |      46,138 |        1.022 |  0.979 |   138,333 |   144,941 |   578,442 |   593,597 | 580,969 |     -318,557 |     -323,377 |   -316,497 |



## Worst-20 weeks and the trade-off line (given up in the base's good weeks vs saved in its bad weeks; w20F = base-worst-20 fixed on all 149 weeks, restricted to the window; w20P = PRE-only 20 worst)
| cell   | win   |   w20F_n |   w20F_base |   w20F_dRaw |   w20F_dLM |   w20P_n |   w20P_base |   w20P_dRaw |   w20P_dLM |   good_given_raw |   bad_saved_raw |   good_given_LM |   bad_saved_LM |   n_bad |
|:-------|:------|---------:|------------:|------------:|-----------:|---------:|------------:|------------:|-----------:|-----------------:|----------------:|----------------:|---------------:|--------:|
| B01    | PRE   |        8 |  -1,490,274 |     145,054 |    113,711 |       20 |  -2,333,434 |     192,747 |    142,869 |         -187,743 |         122,475 |         -63,054 |         78,765 |      14 |
| B01    | HOLD  |        4 |    -914,949 |      56,447 |     34,518 |        0 |           0 |           0 |          0 |          -55,356 |          72,993 |          14,718 |         47,204 |       6 |
| B01    | X     |        8 |  -1,128,947 |      87,493 |     60,767 |        0 |           0 |           0 |          0 |          -37,181 |          87,493 |          27,517 |         60,767 |       8 |
| B02    | PRE   |        8 |  -1,490,274 |     132,091 |    103,106 |       20 |  -2,333,434 |     192,517 |    146,828 |         -150,582 |         116,562 |         -35,584 |         76,401 |      14 |
| B02    | HOLD  |        4 |    -914,949 |      61,289 |     40,444 |        0 |           0 |           0 |          0 |          -54,659 |          73,171 |          12,349 |         48,521 |       6 |
| B02    | X     |        8 |  -1,128,947 |      79,868 |     54,963 |        0 |           0 |           0 |          0 |          -30,132 |          79,868 |          29,887 |         54,963 |       8 |
| B03    | PRE   |        8 |  -1,490,274 |     264,183 |    210,709 |       20 |  -2,333,434 |     385,034 |    300,059 |         -301,163 |         233,124 |         -72,720 |        156,134 |      14 |
| B03    | HOLD  |        4 |    -914,949 |     122,578 |     82,912 |        0 |           0 |           0 |          0 |         -109,318 |         146,343 |          25,316 |         99,472 |       6 |
| B03    | X     |        8 |  -1,128,947 |     159,736 |    112,599 |        0 |           0 |           0 |          0 |          -60,263 |         159,736 |          61,227 |        112,599 |       8 |
| B04    | PRE   |        8 |  -1,490,274 |     290,109 |    232,847 |       20 |  -2,333,434 |     385,495 |    292,554 |         -375,486 |         244,950 |        -129,117 |        161,288 |      14 |
| B04    | HOLD  |        4 |    -914,949 |     112,893 |     70,846 |        0 |           0 |           0 |          0 |         -110,712 |         145,985 |          30,208 |         96,882 |       6 |
| B04    | X     |        8 |  -1,128,947 |     174,986 |    124,734 |        0 |           0 |           0 |          0 |          -74,361 |         174,986 |          56,483 |        124,734 |       8 |
| B05    | PRE   |        8 |  -1,490,274 |     101,901 |     82,365 |       20 |  -2,333,434 |      56,358 |     24,318 |         -146,949 |          67,003 |         -71,075 |         39,826 |      14 |
| B05    | HOLD  |        4 |    -914,949 |      26,326 |     12,157 |        0 |           0 |           0 |          0 |          -82,336 |          61,672 |         -39,023 |         45,393 |       6 |
| B05    | X     |        8 |  -1,128,947 |     108,541 |     92,559 |        0 |           0 |           0 |          0 |           10,982 |         108,541 |          51,223 |         92,559 |       8 |
| B06    | PRE   |        8 |  -1,490,274 |      94,769 |     76,371 |       20 |  -2,333,434 |      51,005 |     20,913 |         -155,273 |          57,263 |         -84,291 |         31,670 |      14 |
| B06    | HOLD  |        4 |    -914,949 |      23,040 |      9,434 |        0 |           0 |           0 |          0 |          -82,970 |          53,722 |         -41,542 |         38,027 |       6 |
| B06    | X     |        8 |  -1,128,947 |     100,683 |     85,835 |        0 |           0 |           0 |          0 |           -1,238 |         100,683 |          35,686 |         85,835 |       8 |
| B07    | PRE   |        8 |  -1,490,274 |     189,539 |    154,782 |       20 |  -2,333,434 |     102,011 |     42,385 |         -310,546 |         114,525 |        -170,834 |         64,186 |      14 |
| B07    | HOLD  |        4 |    -914,949 |      46,080 |     19,161 |        0 |           0 |           0 |          0 |         -165,940 |         107,445 |         -84,372 |         77,232 |       6 |
| B07    | X     |        8 |  -1,128,947 |     201,366 |    174,185 |        0 |           0 |           0 |          0 |           -2,476 |         201,366 |          72,417 |        174,185 |       8 |
| B08    | PRE   |        8 |  -1,490,274 |     147,989 |    108,500 |       20 |  -2,333,434 |     211,223 |    148,790 |         -317,725 |         138,169 |        -164,115 |         83,442 |      14 |
| B08    | HOLD  |        4 |    -914,949 |      61,289 |     34,090 |        0 |           0 |           0 |          0 |         -105,558 |          75,400 |         -19,749 |         43,307 |       6 |
| B08    | X     |        8 |  -1,128,947 |     122,725 |     89,270 |        0 |           0 |           0 |          0 |          -17,773 |         122,725 |          66,695 |         89,270 |       8 |
| B09    | PRE   |        8 |  -1,490,274 |     102,872 |     84,091 |       20 |  -2,333,434 |      66,630 |     35,945 |          -70,439 |          62,179 |           3,589 |         35,968 |      14 |
| B09    | HOLD  |        4 |    -914,949 |      26,379 |     13,225 |        0 |           0 |           0 |          0 |          -37,142 |          57,087 |           3,740 |         41,904 |       6 |
| B09    | X     |        8 |  -1,128,947 |      55,220 |     44,446 |        0 |           0 |           0 |          0 |          -27,641 |          55,220 |          -2,247 |         44,446 |       8 |
| B10    | PRE   |        8 |  -1,490,274 |     198,137 |    156,328 |       20 |  -2,333,434 |     288,775 |    222,617 |         -225,872 |         174,843 |         -53,951 |        115,838 |      14 |
| B10    | HOLD  |        4 |    -914,949 |      91,934 |     61,415 |        0 |           0 |           0 |          0 |          -81,988 |         109,757 |          18,752 |         73,682 |       6 |
| B10    | X     |        8 |  -1,128,947 |     119,802 |     83,435 |        0 |           0 |           0 |          0 |          -45,197 |         119,802 |          45,369 |         83,435 |       8 |
| B12    | PRE   |        8 |  -1,490,274 |    -132,091 |    -98,886 |       20 |  -2,333,434 |    -192,517 |   -140,817 |          150,582 |        -116,562 |          34,127 |        -73,274 |      14 |
| B12    | HOLD  |        4 |    -914,949 |     -61,289 |    -38,560 |        0 |           0 |           0 |          0 |           54,659 |         -73,171 |         -11,774 |        -46,262 |       6 |
| B12    | X     |        8 |  -1,128,947 |     -79,868 |    -52,472 |        0 |           0 |           0 |          0 |           30,132 |         -79,868 |         -28,532 |        -52,472 |       8 |



## By year (raw weekly delta; 2026 = 6 weeks to 2026-02-06; 2023 span = X window)
| cell   | 2023 dRaw/wk (n)   | 2024 dRaw/wk (n)   | 2025 dRaw/wk (n)   | 2026 dRaw/wk (n)   |
|:-------|:-------------------|:-------------------|:-------------------|:-------------------|
| B01    | 3,976 (39)         | 359 (52)           | 245 (52)           | -1,929 (6)         |
| B02    | 3,703 (39)         | 565 (52)           | 896 (52)           | -1,103 (6)         |
| B03    | 7,407 (39)         | 1,130 (52)         | 1,793 (52)         | -2,205 (6)         |
| B04    | 7,951 (39)         | 718 (52)           | 491 (52)           | -3,858 (6)         |
| B05    | 2,442 (39)         | 935 (52)           | 704 (52)           | 780 (6)            |
| B06    | 2,300 (39)         | 71 (52)            | 932 (52)           | 1,606 (6)          |
| B07    | 4,600 (39)         | 142 (52)           | 1,864 (52)         | 3,213 (6)          |
| B08    | 4,095 (39)         | -1,675 (52)        | 1,145 (52)         | 740 (6)            |
| B09    | 2,189 (39)         | 994 (52)           | 1,004 (52)         | -236 (6)           |
| B10    | 5,555 (39)         | 847 (52)           | 1,345 (52)         | -1,654 (6)         |
| B12    | -3,703 (39)        | -565 (52)          | -896 (52)          | 1,103 (6)          |



## Placebos (200 shuffled-label draws within the window, 10 shifted labels; rank = share of null below the true LM delta; best-of-60 HOLD p in last column)
| cell   | win   |   true_dLM |   null_mean |   null_p95 |   rank_shuffle |   shift_mean |   rank_shift |   HOLD_p |
|:-------|:------|-----------:|------------:|-----------:|---------------:|-------------:|-------------:|---------:|
| B01    | PRE   |        997 |      -1,274 |      1,912 |          0.87  |         -919 |          0.7 |          |
| B01    | HOLD  |      2,037 |         574 |      3,797 |          0.76  |        1,528 |          0.6 |    0.403 |
| B01    | X     |      4,276 |        -488 |      4,370 |          0.935 |         -942 |          1   |          |
| B02    | PRE   |      1,460 |      -1,139 |      1,835 |          0.91  |         -712 |          0.9 |          |
| B02    | HOLD  |      2,289 |         144 |      3,437 |          0.885 |        1,247 |          0.8 |    0.358 |
| B02    | X     |      3,974 |        -587 |      3,539 |          0.96  |       -1,014 |          1   |          |
| B03    | PRE   |      2,983 |      -2,227 |      3,392 |          0.93  |       -1,455 |          0.9 |          |
| B03    | HOLD  |      4,692 |       1,374 |      8,350 |          0.79  |        2,544 |          0.8 |    0.358 |
| B03    | X     |      8,142 |      -1,669 |      7,002 |          0.97  |       -2,078 |          1   |          |
| B04    | PRE   |      2,041 |      -2,936 |      3,038 |          0.89  |       -1,880 |          0.7 |          |
| B04    | HOLD  |      4,180 |         640 |      7,768 |          0.75  |        3,122 |          0.6 |    0.403 |
| B04    | X     |      8,777 |      -1,103 |      8,965 |          0.945 |       -1,935 |          1   |          |
| B05    | PRE   |      1,930 |        -829 |      2,286 |          0.925 |         -530 |          0.7 |          |
| B05    | HOLD  |        213 |         159 |      3,695 |          0.49  |       -1,001 |          0.7 |    0.546 |
| B05    | X     |      2,928 |        -215 |      3,891 |          0.905 |       -1,985 |          1   |          |
| B06    | PRE   |      1,657 |        -971 |      1,739 |          0.945 |         -263 |          0.7 |          |
| B06    | HOLD  |        -60 |         393 |      3,452 |          0.43  |       -1,417 |          0.9 |    0.574 |
| B06    | X     |      2,682 |        -578 |      3,508 |          0.915 |       -2,074 |          1   |          |
| B07    | PRE   |      3,357 |      -1,264 |      4,322 |          0.905 |         -532 |          0.7 |          |
| B07    | HOLD  |       -121 |         560 |      6,647 |          0.44  |       -2,883 |          0.9 |    0.574 |
| B07    | X     |      5,443 |      -1,567 |      5,905 |          0.945 |       -4,214 |          1   |          |
| B08    | PRE   |      1,230 |      -1,724 |      1,123 |          0.95  |         -835 |          0.8 |          |
| B08    | HOLD  |        809 |         317 |      4,191 |          0.565 |          138 |          0.6 |    0.556 |
| B08    | X     |      4,779 |        -904 |      3,557 |          0.98  |       -2,439 |          1   |          |
| B09    | PRE   |      1,769 |        -740 |      1,630 |          0.955 |         -766 |          1   |          |
| B09    | HOLD  |      1,246 |         305 |      3,513 |          0.665 |        1,077 |          0.6 |    0.382 |
| B09    | X     |      2,280 |        -602 |      3,269 |          0.89  |         -381 |          0.9 |          |
| B10    | PRE   |      2,213 |      -1,613 |      2,631 |          0.915 |       -1,079 |          0.9 |          |
| B10    | HOLD  |      3,475 |         665 |      6,199 |          0.845 |        1,889 |          0.8 |    0.358 |
| B10    | X     |      6,033 |      -1,141 |      6,511 |          0.94  |       -1,540 |          1   |          |
| B12    | PRE   |     -1,400 |         970 |      3,990 |          0.085 |          683 |          0.1 |          |
| B12    | HOLD  |     -2,182 |        -212 |      3,092 |          0.175 |       -1,199 |          0.2 |    0.641 |
| B12    | X     |     -3,794 |         547 |      4,253 |          0.055 |          966 |          0   |          |



## Ex-post reference (what perfect range-day knowledge would be worth; label = audit 'range' daytype, needs the 16:00 close)
| ref              | win   |   dRaw |    MDE |    dLM |   w20F_dRaw |   w20P_dRaw |   dmaxDD |   dworst |
|:-----------------|:------|-------:|-------:|-------:|------------:|------------:|---------:|---------:|
| R_halve          | PRE   | 11,525 |  5,719 | 12,885 |     229,505 |     410,799 | -110,880 |    8,315 |
| R_halve          | HOLD  |  7,253 |  6,883 |  8,917 |      69,201 |           0 |  -25,094 |   15,661 |
| R_halve          | X     | 15,203 |  7,103 | 16,319 |     181,432 |           0 |  -72,893 |    3,346 |
| R_halve          | WF    | 10,235 |  4,515 | 11,681 |     298,706 |     410,799 |  -25,094 |   15,661 |
| R_stop           | PRE   | 23,050 | 11,438 | 26,419 |     459,010 |     821,597 | -119,196 |   16,630 |
| R_stop           | HOLD  | 14,506 | 13,767 | 18,334 |     138,403 |           0 |  -50,188 |   31,321 |
| R_stop           | X     | 30,405 | 14,206 | 33,656 |     362,864 |           0 | -115,535 |    3,346 |
| R_stop           | WF    | 20,470 |  9,030 | 23,970 |     597,412 |     821,597 |  -50,188 |   28,524 |
| R_all_halve      | PRE   | 11,710 |  6,287 | 13,207 |     257,787 |     423,330 | -110,880 |    8,315 |
| R_all_halve      | HOLD  |  8,458 |  7,054 | 10,294 |      60,350 |           0 |  -18,117 |   11,973 |
| R_all_halve      | X     | 15,949 |  7,692 | 17,235 |     194,805 |           0 |  -77,811 |    3,346 |
| R_all_halve      | WF    | 10,728 |  4,877 | 12,322 |     318,137 |     423,330 |  -18,117 |   11,973 |
| R_halve_wholeday | PRE   | 12,394 | 14,695 | 27,983 |     564,975 |   1,020,653 | -188,341 |   85,776 |
| R_halve_wholeday | HOLD  |  8,106 | 21,804 | 25,043 |     330,773 |           0 | -271,362 |  152,630 |
| R_halve_wholeday | X     | 16,781 | 15,808 | 28,587 |     400,898 |           0 | -120,797 |    3,346 |
| R_halve_wholeday | WF    | 11,099 | 12,144 | 27,102 |     895,747 |   1,020,653 | -271,362 |   97,670 |



## Ex-ante rules as a share of the reference (same action)
| cell   | ref         | win   |   cell_dRaw |   ref_dRaw | share_raw   |   cell_w20F |   ref_w20F | share_w20   |
|:-------|:------------|:------|------------:|-----------:|:------------|------------:|-----------:|:------------|
| B02    | R_halve     | PRE   |         514 |     11,525 | 4.5%        |     132,091 |    229,505 | 57.6%       |
| B02    | R_halve     | HOLD  |         955 |      7,253 | 13.2%       |      61,289 |     69,201 | 88.6%       |
| B06    | R_halve     | PRE   |       1,065 |     11,525 | 9.2%        |      94,769 |    229,505 | 41.3%       |
| B06    | R_halve     | HOLD  |        -865 |      7,253 | -11.9%      |      23,040 |     69,201 | 33.3%       |
| B08    | R_halve     | PRE   |         -57 |     11,525 | -0.5%       |     147,989 |    229,505 | 64.5%       |
| B08    | R_halve     | HOLD  |        -874 |      7,253 | -12.0%      |      61,289 |     69,201 | 88.6%       |
| B09    | R_halve     | PRE   |       1,160 |     11,525 | 10.1%       |     102,872 |    229,505 | 44.8%       |
| B09    | R_halve     | HOLD  |         445 |      7,253 | 6.1%        |      26,379 |     69,201 | 38.1%       |
| B03    | R_stop      | PRE   |       1,028 |     23,050 | 4.5%        |     264,183 |    459,010 | 57.6%       |
| B03    | R_stop      | HOLD  |       1,909 |     14,506 | 13.2%       |     122,578 |    138,403 | 88.6%       |
| B07    | R_stop      | PRE   |       2,130 |     23,050 | 9.2%        |     189,539 |    459,010 | 41.3%       |
| B07    | R_stop      | HOLD  |      -1,730 |     14,506 | -11.9%      |      46,080 |    138,403 | 33.3%       |
| B01    | R_all_halve | PRE   |         -23 |     11,710 | -0.2%       |     145,054 |    257,787 | 56.3%       |
| B01    | R_all_halve | HOLD  |         649 |      8,458 | 7.7%        |      56,447 |     60,350 | 93.5%       |
| B05    | R_all_halve | PRE   |       1,295 |     11,710 | 11.1%       |     101,901 |    257,787 | 39.5%       |
| B05    | R_all_halve | HOLD  |        -633 |      8,458 | -7.5%       |      26,326 |     60,350 | 43.6%       |

## G spec note (nothing survives)
No rule is live-eligible. For the record the closest rule (B02, DEAD) would read: on a day whose 18:00-09:29 ET NQ high-low range is below 0.85x the median of the previous 20 label days, from 10:30 to 18:00 ET enter ST, HM, WT, KB and PE at 0.5x lots, SM unchanged; applicability DualStrat2 (ST/HM/WT) and DS3/DS5 books alike would need the overnight-range feed; not recommended on this evidence.
