# WF_M2: size by risk (inverse trailing drawdown per lot)

## ANSWER FIRST

**S1 combined (ALL): FAIL at every step (2/4/13 weeks).** Mean DD change per period and chained out-of-sample max DD (untouched -215,625): step 2 -323,362, step 4 -324,063, step 13 -305,548; the chained treated curve is deeper in every step. Income change -11% / -11% / -14%. Sessions: all FAIL on S1. S2 quick-screen: PASS cells listed below are all on in-sample baskets (one London basket loses money on average, so its income test is vacuous). Nothing is called works.

Primary-version PASS cells (any step, any subject, any session row): S2 Asia step 4  (26/39 good, income -10%, chained OOS DD -42,499 -> -39,609); S2 London step 4  (28/39 good, income -8%, chained OOS DD -113,538 -> -82,972); S2 London step 13  (9/12 good, income -90%, chained OOS DD -80,703 -> -72,671)

Method M2 (size by risk): per book lots proportional to 1 / trailing max drawdown per lot (daily curve of the book's trades, trailing 26 weeks, floor on missing/zero DD = session median), session total lots unchanged, re-set at the stated step. Subject S1/S2 as in WF_PROGRAMME_COMMON.md. U = untouched, T = treated. PASS rules: step 13 as the directive; steps 2 and 4: shallower DD, or higher income with no deeper DD, in >= 2/3 of periods, income not lower by > 10%.

## Step 2 weeks (Josh refit rhythm, first): S1 (four live mixes, post-hoc approx, exact per-trade P&L)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 47/77 (47 / 28) p=0.034 | -48,851 -> -45,975 | +2,876 | +693 | 36,504 -> 32,332 (-11%) | -215,625 -> -323,362 | -24,954/39,937/99,344 -> -23,369/34,528/83,871 | -30,675/44,148/100,297 -> -28,756/35,659/84,325 |
| Asia | **FAIL** | 42/77 (42 / 31) p=0.247 | -15,764 -> -15,131 | +633 | +29 | 5,537 -> 4,760 (-14%) | -67,941 -> -70,392 | -16,563/4,084/11,934 -> -13,803/4,958/13,048 | -18,614/1,096/15,460 -> -15,230/1,019/13,306 |
| London | **FAIL** | 32/77 (32 / 39) p=0.945 | -24,151 -> -26,995 | -2,844 | -1,094 | 5,188 -> 4,875 (-6%) | -224,333 -> -233,977 | -23,428/2,569/18,615 -> -26,331/264/18,403 | -21,900/1,708/17,963 -> -25,041/-1,080/17,165 |
| NY AM | **FAIL** | 57/77 (57 / 33) p=0.000 | -43,982 -> -36,806 | +7,177 | +3,013 | 19,825 -> 16,146 (-19%) | -200,647 -> -175,857 | -31,881/14,490/55,173 -> -27,753/9,477/38,620 | -38,750/13,101/53,912 -> -30,544/11,826/40,318 |
| NY PM | **FAIL** | 42/77 (42 / 39) p=0.247 | -20,215 -> -20,047 | +167 | +1,448 | 5,954 -> 6,551 (+10%) | -134,363 -> -150,927 | -14,529/1,693/13,621 -> -12,994/1,872/13,800 | -17,438/2,154/12,962 -> -15,714/3,728/13,536 |

## Step 4 weeks: S1 (four live mixes, post-hoc approx, exact per-trade P&L)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 25/39 (25 / 14) p=0.054 | -70,551 -> -65,574 | +4,977 | +4,072 | 35,524 -> 31,508 (-11%) | -215,625 -> -324,063 | -34,805/2,004/99,344 -> -33,393/-1,615/82,409 | -40,102/13,538/110,236 -> -36,229/11,969/91,391 |
| Asia | **FAIL** | 26/39 (26 / 17) p=0.027 | -23,319 -> -22,647 | +671 | +577 | 5,388 -> 4,600 (-15%) | -67,941 -> -73,626 | -18,825/105/11,934 -> -15,693/-400/13,010 | -20,191/-542/16,600 -> -15,956/-960/13,780 |
| London | **FAIL** | 16/39 (16 / 20) p=0.900 | -37,290 -> -41,145 | -3,855 | -2,046 | 5,393 -> 5,356 (-1%) | -224,333 -> -233,977 | -34,479/-11,753/18,615 -> -36,996/-15,606/18,110 | -30,567/-9,330/18,993 -> -35,286/-15,119/17,973 |
| NY AM | **FAIL** | 31/39 (31 / 11) p=0.000 | -62,580 -> -52,304 | +10,277 | +6,397 | 19,562 -> 15,636 (-20%) | -200,647 -> -188,100 | -48,897/-19,081/55,173 -> -39,199/-24,672/37,490 | -50,267/-6,092/60,959 -> -39,604/-8,363/45,194 |
| NY PM | **FAIL** | 23/39 (23 / 23) p=0.168 | -29,172 -> -28,956 | +216 | +1,587 | 5,181 -> 5,916 (+14%) | -134,363 -> -157,117 | -18,313/-6,215/13,621 -> -14,858/-5,533/13,800 | -21,780/-4,671/13,684 -> -18,667/-1,440/14,444 |

## Step 13 weeks: S1 (four live mixes, post-hoc approx, exact per-trade P&L)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 5/12 (5 / 3) p=0.806 | -100,275 -> -100,844 | -570 | -185 | 37,000 -> 31,887 (-14%) | -215,625 -> -305,548 | -38,773/-15,957/101,577 -> -40,227/-23,100/82,541 | -57,748/-38,407/100,297 -> -63,955/-50,931/84,644 |
| Asia | **FAIL** | 5/12 (5 / 4) p=0.806 | -38,271 -> -40,691 | -2,421 | +553 | 5,513 -> 4,696 (-15%) | -67,941 -> -86,162 | -23,953/-8,395/10,371 -> -18,198/-4,558/11,281 | -30,852/-21,127/15,460 -> -29,877/-18,333/14,867 |
| London | **FAIL** | 4/12 (4 / 7) p=0.927 | -65,753 -> -66,666 | -913 | -2,749 | 5,430 -> 5,706 (+5%) | -224,333 -> -222,040 | -39,760/-20,172/18,416 -> -47,860/-23,318/16,846 | -36,492/-20,434/17,963 -> -41,813/-27,022/16,832 |
| NY AM | **FAIL** | 7/12 (7 / 3) p=0.387 | -101,653 -> -87,189 | +14,464 | +7,113 | 20,215 -> 14,831 (-27%) | -200,647 -> -200,653 | -69,974/-35,029/60,454 -> -59,539/-32,371/42,161 | -68,773/-47,221/53,912 -> -67,055/-44,421/39,837 |
| NY PM | **FAIL** | 5/12 (5 / 9) p=0.806 | -49,090 -> -49,393 | -303 | +951 | 5,843 -> 6,654 (+14%) | -134,363 -> -129,160 | -26,269/-18,119/12,337 -> -27,854/-12,355/12,253 | -28,441/-20,583/12,962 -> -30,094/-14,110/13,107 |

## Step 2 weeks: S2 (equal-weight basket of Test 5 primary qualifiers, quick screen, $ per cell at 6 lots, weekly curve)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 38/77 (33 / 30) p=0.590 | -4,111 -> -3,683 | +429 | +189 | 716 -> 441 (-38%) | -70,645 -> -61,531 | -4,650/-2,117/279 -> -4,236/-1,969/-8 | -5,562/-3,828/953 -> -4,670/-3,177/505 |
| Asia | **FAIL** | 43/77 (37 / 37) p=0.181 | -4,321 -> -3,956 | +365 | +125 | 1,132 -> 998 (-12%) | -45,780 -> -41,323 | -5,154/-3,020/220 -> -4,918/-3,015/152 | -4,723/-247/3,686 -> -4,353/-781/2,625 |
| London | **FAIL** | 45/77 (38 / 40) p=0.086 | -4,795 -> -4,388 | +406 | +244 | -355 -> -356 (+0%) | -76,946 -> -61,992 | -7,175/-3,508/414 -> -6,349/-3,735/-607 | -5,599/-3,307/796 -> -5,193/-3,390/133 |
| NY AM | **FAIL** | 37/77 (34 / 27) p=0.676 | -6,454 -> -5,706 | +748 | +496 | 841 -> 424 (-50%) | -125,241 -> -100,471 | -9,280/-4,081/412 -> -7,076/-3,101/-337 | -10,322/-7,841/-436 -> -7,527/-5,692/-695 |
| NY PM | **FAIL** | 42/77 (39 / 32) p=0.247 | -7,367 -> -5,499 | +1,868 | +958 | 788 -> 238 (-70%) | -137,396 -> -58,786 | -9,889/-8,948/587 -> -5,783/-5,396/-1,218 | -13,364/-9,009/1,131 -> -5,350/-3,995/-631 |

## Step 4 weeks: S2 (equal-weight basket of Test 5 primary qualifiers, quick screen, $ per cell at 6 lots, weekly curve)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 22/39 (22 / 11) p=0.261 | -7,318 -> -6,651 | +667 | +384 | 649 -> 302 (-53%) | -77,711 -> -65,487 | -9,300/-6,085/279 -> -8,325/-4,698/-26 | -10,488/-7,821/1,032 -> -8,707/-6,141/610 |
| Asia | **PASS** | 26/39 (24 / 17) p=0.027 | -7,772 -> -7,118 | +654 | +369 | 1,339 -> 1,212 (-10%) | -42,499 -> -39,609 | -10,308/-4,894/220 -> -9,674/-4,537/111 | -10,233/-5,982/3,138 -> -9,371/-5,519/2,529 |
| London | **PASS** | 28/39 (26 / 22) p=0.005 | -9,807 -> -8,781 | +1,025 | +695 | -604 -> -555 (-8%) | -113,538 -> -82,972 | -14,349/-8,996/414 -> -11,879/-7,533/-703 | -11,326/-6,563/590 -> -10,110/-6,251/-167 |
| NY AM | **FAIL** | 17/39 (17 / 13) p=0.832 | -11,639 -> -10,579 | +1,060 | +821 | 787 -> 243 (-69%) | -130,809 -> -106,711 | -18,560/-14,346/412 -> -14,061/-10,024/-282 | -19,658/-13,459/-80 -> -14,337/-9,445/-470 |
| NY PM | **FAIL** | 25/39 (23 / 17) p=0.054 | -13,757 -> -11,371 | +2,386 | +1,762 | 561 -> 80 (-86%) | -134,431 -> -77,044 | -16,540/-11,137/587 -> -10,562/-7,941/-1,462 | -21,361/-15,413/2,505 -> -9,657/-6,586/-444 |

## Step 13 weeks: S2 (equal-weight basket of Test 5 primary qualifiers, quick screen, $ per cell at 6 lots, weekly curve)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 10/12 (10 / 3) p=0.019 | -18,095 -> -16,655 | +1,441 | +835 | 697 -> 428 (-39%) | -70,645 -> -62,585 | -17,456/-11,686/1,122 -> -15,818/-9,851/658 | -18,143/-11,131/702 -> -15,801/-9,486/418 |
| Asia | **FAIL** | 12/12 (12 / 3) p=0.000 | -17,602 -> -14,946 | +2,656 | +1,325 | 1,234 -> 998 (-19%) | -42,499 -> -41,175 | -19,135/-11,522/1,001 -> -17,009/-10,119/923 | -21,563/-13,125/3,710 -> -14,416/-9,466/2,581 |
| London | **PASS** | 9/12 (9 / 8) p=0.073 | -22,876 -> -19,611 | +3,265 | +914 | -360 -> -35 (-90%) | -80,703 -> -72,671 | -35,149/-20,750/1,120 -> -26,703/-17,164/692 | -27,221/-15,002/755 -> -21,531/-13,139/621 |
| NY AM | **FAIL** | 9/12 (9 / 4) p=0.073 | -26,288 -> -22,956 | +3,332 | +1,504 | 834 -> 388 (-54%) | -133,613 -> -107,475 | -28,174/-15,004/1,413 -> -20,834/-10,511/-11 | -39,420/-16,902/-758 -> -28,287/-12,539/-967 |
| NY PM | **FAIL** | 8/12 (8 / 3) p=0.194 | -32,685 -> -25,952 | +6,733 | +3,802 | 810 -> 187 (-77%) | -138,549 -> -103,267 | -30,581/-15,353/1,624 -> -9,580/-7,299/124 | -56,896/-20,694/749 -> -20,731/-7,639/-292 |

## Reference versions (ALL row), S1

| step | version | ALL verdict | good/n | mean dDD | $/wk change | chained OOS DD U -> T | lots turnover per reset |
|---|---|---|---|---|---|---|---|
| 2 wk | primary | FAIL | 47/77 | +2,876 | -11% | -215,625 -> -323,362 | 3.3 |
| 2 wk | ref:win13 | FAIL | 38/77 | +971 | -13% | -215,625 -> -336,706 | 6.5 |
| 2 wk | ref:win52 | FAIL | 43/77 | +2,926 | -10% | -215,625 -> -292,833 | 1.6 |
| 2 wk | ref:continuous_lots | FAIL | 43/77 | +2,422 | -13% | -215,625 -> -343,784 | 4.2 |
| 4 wk | primary | FAIL | 25/39 | +4,977 | -11% | -215,625 -> -324,063 | 5.7 |
| 4 wk | ref:win13 | FAIL | 22/39 | +801 | -12% | -215,625 -> -329,960 | 10.6 |
| 4 wk | ref:win52 | FAIL | 23/39 | +4,516 | -9% | -215,625 -> -276,292 | 3.1 |
| 4 wk | ref:continuous_lots | FAIL | 23/39 | +4,007 | -13% | -215,625 -> -329,963 | 7.3 |
| 13 wk | primary | FAIL | 5/12 | -570 | -14% | -215,625 -> -305,548 | 12.1 |
| 13 wk | ref:win13 | FAIL | 5/12 | -4,412 | -16% | -215,625 -> -297,013 | 19.6 |
| 13 wk | ref:win52 | FAIL | 6/12 | +5,157 | -11% | -215,625 -> -259,717 | 7.2 |
| 13 wk | ref:continuous_lots | FAIL | 4/12 | -2,370 | -17% | -215,625 -> -319,301 | 15.5 |

## Reference versions (ALL row), S2

| step | version | ALL verdict | good/n | mean dDD | $/wk change | chained OOS DD U -> T | lots turnover per reset |
|---|---|---|---|---|---|---|---|
| 2 wk | primary | FAIL | 38/77 | +429 | -38% | -70,645 -> -61,531 | 238.7 |
| 2 wk | ref:win13 | FAIL | 46/77 | +719 | -2% | -70,645 -> -50,548 | 622.5 |
| 2 wk | ref:win52 | FAIL | 39/77 | +505 | -19% | -70,645 -> -56,837 | 138.3 |
| 2 wk | ref:continuous_lots | FAIL | 39/77 | +500 | -46% | -70,645 -> -59,817 | 287.5 |
| 4 wk | primary | FAIL | 22/39 | +667 | -53% | -77,711 -> -65,487 | 374.0 |
| 4 wk | ref:win13 | FAIL | 23/39 | -295 | -100% | -77,711 -> -97,030 | 855.5 |
| 4 wk | ref:win52 | FAIL | 23/39 | +852 | -19% | -77,711 -> -63,449 | 237.1 |
| 4 wk | ref:continuous_lots | FAIL | 23/39 | +760 | -64% | -77,711 -> -63,383 | 449.7 |
| 13 wk | primary | FAIL | 10/12 | +1,441 | -39% | -70,645 -> -62,585 | 0.0 |
| 13 wk | ref:win13 | FAIL | 8/12 | +4,055 | -41% | -70,645 -> -43,457 | 0.0 |
| 13 wk | ref:win52 | FAIL | 10/12 | +1,822 | -17% | -70,645 -> -58,487 | 0.0 |
| 13 wk | ref:continuous_lots | FAIL | 9/12 | +1,666 | -47% | -70,645 -> -61,022 | 0.0 |

## Caveats (read before trusting anything)
- S1 is post-hoc approx: each trade's exact engine P&L ($4.84/lot fee in) is multiplied by new book lots / live book lots. The engine's account layers (stack caps, daily-loss halts, sizer, partial-exit rounding, fill queue) are NOT re-run at the changed lots, so a book given more lots can hit caps the post-hoc number ignores. Engine rows were not queued (cost: every chosen lot vector is its own set; 4 sessions x about 4 months x 12 periods = ~190 set-months at 13 weeks, ~1,000+ at 2 weeks; not cheap, nothing queued).
- The four live mixes were chosen on the same weeks (including the forward ones), so the untouched subject is flattered in every period; S2 qualifiers are in-sample chosen cells.
- Lots base: live set lots (Asia 6/6/6/6 = 24, London 8/4/2 = 14, NY AM 6/6/6/6/3/6/2/2/3 = 40, NY PM 6/6/6/6 = 24; total 102 or as the sets run). S2 base 6 lots per held cell. Integers: largest-remainder rounding, min 1 lot per book where feasible (else 0); one reference row uses fractional lots.
- Drawdown over short forward periods is noisy; the chained out-of-sample curve (all forward periods joined) is shown next to the per-period counts. Nov 2025 weeks excluded; 2-week step = 77 usable periods, 4-week 39, 13-week 12.
- 78 primaries x 4 steps already tried programme-wide; the plain p is a sign test on periods and is not corrected.

## Reading notes
- Mean dDD / dWorstWk: positive = treated is shallower / better. Many session rows are shallower in 2/3 of periods only because the treatment lowers that session's lots, and then fail the income test (e.g. NY AM: shallower in 52-57 of 77 periods at 2 weeks, p~0.001, but income -14% to -19%): that is de-risking, not edge. Fixed-lots-equivalent comparison (equal-mean frontier) was not done here.
- Code: /mnt/l2/l2vast/_wf/m2m3 (s1.py, s2.py, drive.py, pages.py). Scoreboard lines (240) appended to /mnt/l2/l2vast/_wf/scoreboard_rows.jsonl with field step_weeks.
