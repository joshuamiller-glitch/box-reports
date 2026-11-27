# WF_M3: session allocation by trailing income per drawdown

## ANSWER FIRST

**S1 combined (ALL): FAIL at every step.** Chained out-of-sample max DD (untouched -215,625): step 2 -327,221, step 4 -344,018, step 13 -345,465: concentrating lots on the best trailing income-per-drawdown session makes the chained drawdown WORSE. Income change -9% / -9% / -7%. One session row passes (NY AM at 13 weeks, 8 of 12 shallower, income -3.5%, still PASS on the pessimistic basis) but it is a consequence row (NY AM is given fewer lots), the chained NY AM curve gets deeper (-200,647 -> -280,211) and the combined mix fails; treat as noise. S2 PASS cells are in-sample quick-screen baskets.

Primary-version PASS cells (any step, any subject, any session row): S1 NY AM step 13  (8/12 good, income -4%, chained OOS DD -200,647 -> -280,211, pessimistic PASS); S2 Asia step 13  (10/12 good, income -6%, chained OOS DD -42,499 -> -42,513); S2 NY AM step 13  (8/12 good, income -2%, chained OOS DD -133,613 -> -75,133)

Method M3 (session allocation): total lots unchanged, floor 2 per session, session lots = 2 + rest x score / sum of scores, score = trailing 26-week income / max DD of the session at its live lots (negative income -> 0 score; all non-positive -> live lots), re-set at the stated step; within a session the live book proportions are kept (largest-remainder integers). The subject is the combined mix (ALL row); per-session rows are consequences of the reallocation, not separate subjects. Lots turnover per reset (lots moved, half the sum of absolute changes) is in the reference table; S2 turnover is 0 at the 13-week step only because the held set did not change within a period, and baskets hold up to ~250 cells.

## Step 2 weeks (Josh refit rhythm, first): S1 (four live mixes, post-hoc approx, exact per-trade P&L)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 36/77 (36 / 36) p=0.753 | -48,851 -> -55,526 | -6,675 | -4,750 | 36,504 -> 33,305 (-9%) | -215,625 -> -327,221 | -24,954/39,937/99,344 -> -23,670/36,513/88,088 | -30,675/44,148/100,297 -> -29,070/33,620/87,579 |
| Asia | **FAIL** | 38/77 (38 / 39) p=0.590 | -15,764 -> -16,991 | -1,227 | -372 | 5,537 -> 5,465 (-1%) | -67,941 -> -104,918 | -16,563/4,084/11,934 -> -23,673/5,922/16,698 | -18,614/1,096/15,460 -> -28,775/-2,999/19,019 |
| London | **FAIL** | 29/77 (29 / 40) p=0.989 | -24,151 -> -28,897 | -4,746 | -1,309 | 5,188 -> 4,792 (-8%) | -224,333 -> -283,652 | -23,428/2,569/18,615 -> -25,716/-460/17,696 | -21,900/1,708/17,963 -> -22,810/-1,540/16,810 |
| NY AM | **FAIL** | 52/77 (52 / 32) p=0.001 | -43,982 -> -38,868 | +5,115 | -453 | 19,825 -> 16,995 (-14%) | -200,647 -> -249,784 | -31,881/14,490/55,173 -> -23,970/8,428/39,683 | -38,750/13,101/53,912 -> -32,271/5,686/39,131 |
| NY PM | **FAIL** | 35/77 (34 / 39) p=0.819 | -20,215 -> -22,295 | -2,080 | -418 | 5,954 -> 6,053 (+2%) | -134,363 -> -110,600 | -14,529/1,693/13,621 -> -14,598/1,382/14,011 | -17,438/2,154/12,962 -> -15,343/1,925/12,619 |

## Step 4 weeks: S1 (four live mixes, post-hoc approx, exact per-trade P&L)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 20/39 (20 / 18) p=0.500 | -70,551 -> -77,678 | -7,127 | -5,149 | 35,524 -> 32,183 (-9%) | -215,625 -> -344,018 | -34,805/2,004/99,344 -> -32,250/8,799/88,766 | -40,102/13,538/110,236 -> -37,492/14,137/94,150 |
| Asia | **FAIL** | 20/39 (20 / 16) p=0.500 | -23,319 -> -25,015 | -1,697 | -177 | 5,388 -> 5,063 (-6%) | -67,941 -> -136,681 | -18,825/105/11,934 -> -26,657/-605/16,392 | -20,191/-542/16,600 -> -35,239/-8,217/17,932 |
| London | **FAIL** | 15/39 (15 / 24) p=0.946 | -37,290 -> -47,212 | -9,922 | -5,027 | 5,393 -> 4,963 (-8%) | -224,333 -> -355,637 | -34,479/-11,753/18,615 -> -39,347/-15,912/18,334 | -30,567/-9,330/18,993 -> -33,018/-13,193/16,943 |
| NY AM | **FAIL** | 29/39 (29 / 16) p=0.002 | -62,580 -> -55,279 | +7,301 | +1,592 | 19,562 -> 16,701 (-15%) | -200,647 -> -249,731 | -48,897/-19,081/55,173 -> -37,736/-16,891/39,794 | -50,267/-6,092/60,959 -> -39,639/-5,249/45,888 |
| NY PM | **FAIL** | 18/39 (18 / 22) p=0.739 | -29,172 -> -31,226 | -2,054 | -904 | 5,181 -> 5,456 (+5%) | -134,363 -> -105,032 | -18,313/-6,215/13,621 -> -18,341/-6,464/14,246 | -21,780/-4,671/13,684 -> -18,827/-3,950/13,387 |

## Step 13 weeks: S1 (four live mixes, post-hoc approx, exact per-trade P&L)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 5/12 (5 / 7) p=0.806 | -100,275 -> -125,589 | -25,314 | -16,410 | 37,000 -> 34,527 (-7%) | -215,625 -> -345,465 | -38,773/-15,957/101,577 -> -36,294/-5,402/83,465 | -57,748/-38,407/100,297 -> -59,167/-41,968/95,415 |
| Asia | **FAIL** | 7/12 (7 / 6) p=0.387 | -38,271 -> -34,875 | +3,395 | +1,789 | 5,513 -> 6,204 (+13%) | -67,941 -> -88,766 | -23,953/-8,395/10,371 -> -35,444/-12,046/15,221 | -30,852/-21,127/15,460 -> -47,172/-33,222/24,493 |
| London | **FAIL** | 6/12 (6 / 7) p=0.613 | -65,753 -> -75,328 | -9,576 | -5,351 | 5,430 -> 4,067 (-25%) | -224,333 -> -324,163 | -39,760/-20,172/18,416 -> -31,123/-15,330/12,727 | -36,492/-20,434/17,963 -> -35,773/-22,247/16,642 |
| NY AM | **PASS** (stress PASS) | 8/12 (8 / 5) p=0.194 | -101,653 -> -95,903 | +5,750 | -1,019 | 20,215 -> 19,501 (-4%) | -200,647 -> -280,211 | -69,974/-35,029/60,454 -> -44,711/-23,224/39,683 | -68,773/-47,221/53,912 -> -62,170/-47,178/45,484 |
| NY PM | **FAIL** | 4/12 (4 / 6) p=0.927 | -49,090 -> -57,824 | -8,734 | -2,752 | 5,843 -> 4,755 (-19%) | -134,363 -> -162,621 | -26,269/-18,119/12,337 -> -35,031/-22,656/15,834 | -28,441/-20,583/12,962 -> -19,562/-11,937/8,796 |

## Step 2 weeks: S2 (equal-weight basket of Test 5 primary qualifiers, quick screen, $ per cell at 6 lots, weekly curve)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 35/77 (29 / 34) p=0.819 | -4,111 -> -3,623 | +488 | +456 | 716 -> 528 (-26%) | -70,645 -> -48,770 | -4,650/-2,117/279 -> -5,093/-3,214/-399 | -5,562/-3,828/953 -> -4,392/-1,379/1,820 |
| Asia | **FAIL** | 38/77 (32 / 36) p=0.590 | -4,321 -> -5,945 | -1,624 | -1,534 | 1,132 -> 1,376 (+22%) | -45,780 -> -73,367 | -5,154/-3,020/220 -> -2,191/-1,301/-22 | -4,723/-247/3,686 -> -6,251/879/6,230 |
| London | **FAIL** | 26/77 (13 / 38) p=0.999 | -4,795 -> -68,138 | -63,344 | -42,506 | -355 -> -6,194 (+1643%) | -76,946 -> -1,707,853 | -7,175/-3,508/414 -> -339,259/-184,173/-6,055 | -5,599/-3,307/796 -> -215,402/-130,915/9,801 |
| NY AM | **FAIL** | 50/77 (46 / 38) p=0.006 | -6,454 -> -3,290 | +3,164 | +2,186 | 841 -> 685 (-19%) | -125,241 -> -68,041 | -9,280/-4,081/412 -> -4,139/-1,572/426 | -10,322/-7,841/-436 -> -3,258/-2,036/-11 |
| NY PM | **FAIL** | 25/77 (8 / 34) p=0.999 | -7,367 -> -34,286 | -26,919 | -21,125 | 788 -> -5,018 (-736%) | -137,396 -> -1,035,448 | -9,889/-8,948/587 -> -99,369/-91,544/-31,206 | -13,364/-9,009/1,131 -> -51,301/-46,709/-15,578 |

## Step 4 weeks: S2 (equal-weight basket of Test 5 primary qualifiers, quick screen, $ per cell at 6 lots, weekly curve)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 19/39 (19 / 20) p=0.625 | -7,318 -> -7,282 | +35 | +444 | 649 -> 579 (-11%) | -77,711 -> -58,579 | -9,300/-6,085/279 -> -9,848/-6,652/-82 | -10,488/-7,821/1,032 -> -9,284/-6,238/2,045 |
| Asia | **FAIL** | 23/39 (23 / 14) p=0.168 | -7,772 -> -9,075 | -1,303 | -993 | 1,339 -> 1,424 (+6%) | -42,499 -> -89,357 | -10,308/-4,894/220 -> -4,757/-2,455/-175 | -10,233/-5,982/3,138 -> -13,769/-9,103/5,800 |
| London | **FAIL** | 13/39 (10 / 20) p=0.988 | -9,807 -> -126,029 | -116,222 | -76,995 | -604 -> -3,798 (+529%) | -113,538 -> -1,707,853 | -14,349/-8,996/414 -> -672,950/-418,472/13,914 | -11,326/-6,563/590 -> -430,571/-256,327/17,807 |
| NY AM | **FAIL** | 28/39 (28 / 20) p=0.005 | -11,639 -> -6,228 | +5,411 | +3,639 | 787 -> 641 (-19%) | -130,809 -> -76,005 | -18,560/-14,346/412 -> -8,577/-6,576/198 | -19,658/-13,459/-80 -> -6,154/-4,477/162 |
| NY PM | **FAIL** | 9/39 (6 / 18) p=1.000 | -13,757 -> -60,279 | -46,523 | -32,046 | 561 -> -725 (-229%) | -134,431 -> -779,925 | -16,540/-11,137/587 -> -85,058/-73,200/-13,276 | -21,361/-15,413/2,505 -> -42,747/-36,818/-6,397 |

## Step 13 weeks: S2 (equal-weight basket of Test 5 primary qualifiers, quick screen, $ per cell at 6 lots, weekly curve)

| session | verdict | good periods (shallower / income-higher) | max DD per period U -> T | mean dDD | mean dWorstWk | $/wk U -> T (%) | chained OOS max DD U -> T | L3M maxDD/worst/inc U -> T | L6M maxDD/worst/inc U -> T |
|---|---|---|---|---|---|---|---|---|---|
| ALL four | **FAIL** | 7/12 (7 / 8) p=0.387 | -18,095 -> -15,496 | +2,600 | +1,245 | 697 -> 995 (+43%) | -70,645 -> -51,471 | -17,456/-11,686/1,122 -> -14,978/-8,341/1,131 | -18,143/-11,131/702 -> -16,114/-9,151/2,256 |
| Asia | **PASS** | 10/12 (10 / 4) p=0.019 | -17,602 -> -10,376 | +7,226 | +4,700 | 1,234 -> 1,161 (-6%) | -42,499 -> -42,513 | -19,135/-11,522/1,001 -> -11,030/-6,397/573 | -21,563/-13,125/3,710 -> -26,771/-16,319/5,939 |
| London | **FAIL** | 4/12 (4 / 8) p=0.927 | -22,876 -> -266,703 | -243,827 | -134,701 | -360 -> -246 (-32%) | -80,703 -> -1,335,171 | -35,149/-20,750/1,120 -> -1,335,171/-788,440/42,498 | -27,221/-15,002/755 -> -939,308/-524,565/26,755 |
| NY AM | **PASS** | 8/12 (8 / 7) p=0.194 | -26,288 -> -14,383 | +11,905 | +6,521 | 834 -> 821 (-2%) | -133,613 -> -75,133 | -28,174/-15,004/1,413 -> -13,468/-7,354/697 | -39,420/-16,902/-758 -> -13,032/-5,981/-21 |
| NY PM | **FAIL** | 0/12 (0 / 9) p=1.000 | -32,685 -> -102,892 | -70,207 | -44,150 | 810 -> 2,856 (+253%) | -138,549 -> -293,520 | -30,581/-15,353/1,624 -> -34,343/-17,066/1,800 | -56,896/-20,694/749 -> -60,942/-22,066/1,054 |

## Reference versions (ALL row), S1

| step | version | ALL verdict | good/n | mean dDD | $/wk change | chained OOS DD U -> T | lots turnover per reset |
|---|---|---|---|---|---|---|---|
| 2 wk | primary | FAIL | 36/77 | -6,675 | -9% | -215,625 -> -327,221 | 10.1 |
| 2 wk | ref:win13 | FAIL | 27/77 | -11,612 | -10% | -215,625 -> -465,076 | 18.1 |
| 2 wk | ref:win52 | FAIL | 33/77 | -1,493 | -3% | -215,625 -> -236,504 | 5.3 |
| 2 wk | ref:continuous_lots | FAIL | 38/77 | -7,291 | -9% | -215,625 -> -301,517 | 10.0 |
| 4 wk | primary | FAIL | 20/39 | -7,127 | -9% | -215,625 -> -344,018 | 15.5 |
| 4 wk | ref:win13 | FAIL | 21/39 | -17,135 | -6% | -215,625 -> -580,335 | 25.0 |
| 4 wk | ref:win52 | FAIL | 15/39 | -5,193 | -3% | -215,625 -> -243,354 | 7.4 |
| 4 wk | ref:continuous_lots | FAIL | 22/39 | -8,846 | -11% | -215,625 -> -360,661 | 15.3 |
| 13 wk | primary | FAIL | 5/12 | -25,314 | -7% | -215,625 -> -345,465 | 31.0 |
| 13 wk | ref:win13 | FAIL | 6/12 | -52,831 | -11% | -215,625 -> -575,271 | 42.9 |
| 13 wk | ref:win52 | FAIL | 3/12 | -17,338 | -6% | -215,625 -> -267,936 | 17.5 |
| 13 wk | ref:continuous_lots | FAIL | 5/12 | -26,632 | -8% | -215,625 -> -328,516 | 30.9 |

## Reference versions (ALL row), S2

| step | version | ALL verdict | good/n | mean dDD | $/wk change | chained OOS DD U -> T | lots turnover per reset |
|---|---|---|---|---|---|---|---|
| 2 wk | primary | FAIL | 35/77 | +488 | -26% | -70,645 -> -48,770 | 430.0 |
| 2 wk | ref:win13 | FAIL | 35/77 | +3 | -15% | -70,645 -> -70,206 | 566.2 |
| 2 wk | ref:win52 | FAIL | 38/77 | +688 | -22% | -70,645 -> -46,370 | 288.0 |
| 2 wk | ref:continuous_lots | FAIL | 33/77 | +474 | -27% | -70,645 -> -48,827 | 430.0 |
| 4 wk | primary | FAIL | 19/39 | +35 | -11% | -77,711 -> -58,579 | 598.7 |
| 4 wk | ref:win13 | FAIL | 18/39 | -2,027 | -51% | -77,711 -> -105,754 | 735.8 |
| 4 wk | ref:win52 | FAIL | 21/39 | +616 | -9% | -77,711 -> -57,282 | 441.8 |
| 4 wk | ref:continuous_lots | FAIL | 19/39 | +25 | -12% | -77,711 -> -58,633 | 598.7 |
| 13 wk | primary | FAIL | 7/12 | +2,600 | +43% | -70,645 -> -51,471 | 0.0 |
| 13 wk | ref:win13 | FAIL | 6/12 | -1,702 | +82% | -70,645 -> -82,937 | 0.0 |
| 13 wk | ref:win52 | PASS | 8/12 | +4,497 | +19% | -70,645 -> -46,546 | 0.0 |
| 13 wk | ref:continuous_lots | FAIL | 7/12 | +2,533 | +42% | -70,645 -> -51,995 | 0.0 |

## Caveats (read before trusting anything)
- S1 is post-hoc approx: each trade's exact engine P&L ($4.84/lot fee in) is multiplied by new book lots / live book lots. The engine's account layers (stack caps, daily-loss halts, sizer, partial-exit rounding, fill queue) are NOT re-run at the changed lots, so a book given more lots can hit caps the post-hoc number ignores. Engine rows were not queued (cost: every chosen lot vector is its own set; 4 sessions x about 4 months x 12 periods = ~190 set-months at 13 weeks, ~1,000+ at 2 weeks; not cheap, nothing queued).
- The four live mixes were chosen on the same weeks (including the forward ones), so the untouched subject is flattered in every period; S2 qualifiers are in-sample chosen cells.
- Lots base: live set lots (Asia 6/6/6/6 = 24, London 8/4/2 = 14, NY AM 6/6/6/6/3/6/2/2/3 = 40, NY PM 6/6/6/6 = 24; total 102 or as the sets run). S2 base 6 lots per held cell. Integers: largest-remainder rounding, min 1 lot per book where feasible (else 0); one reference row uses fractional lots.
- Drawdown over short forward periods is noisy; the chained out-of-sample curve (all forward periods joined) is shown next to the per-period counts. Nov 2025 weeks excluded; 2-week step = 77 usable periods, 4-week 39, 13-week 12.
- 78 primaries x 4 steps already tried programme-wide; the plain p is a sign test on periods and is not corrected.

## Reading notes
- Mean dDD / dWorstWk: positive = treated is shallower / better. Many session rows are shallower in 2/3 of periods only because the treatment lowers that session's lots, and then fail the income test (e.g. NY AM: shallower in 52-57 of 77 periods at 2 weeks, p~0.001, but income -14% to -19%): that is de-risking, not edge. Fixed-lots-equivalent comparison (equal-mean frontier) was not done here.
- Code: /mnt/l2/l2vast/_wf/m2m3 (s1.py, s2.py, drive.py, pages.py). Scoreboard lines (240) appended to /mnt/l2/l2vast/_wf/scoreboard_rows.jsonl with field step_weeks.
