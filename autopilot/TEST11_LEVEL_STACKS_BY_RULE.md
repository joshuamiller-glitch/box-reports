# TEST 11: two-sided level books as a BUILDABLE stack, chosen by rule, with account layers, on stress fills

Written 2026-11-27 22:31Z by W-TEST11 (sub-agent of LEAD; order autopilot/DIRECTIVE_TEST11_0117Z.md, relay design under Josh's standing 18:22Z order, not Josh's words). Research and shadow only. Code code/th_test11 (t11_plan, t11_build, t11_quick, t11_live, t11_held, t11_page, t11_lib). Re-run: `python3 code/th_test11/t11_page.py` (re-scores whatever exact rows have landed).

## ANSWER FIRST
1. **STATUS: the exact stack rows are queued, not run.** 3,480 stacks, 25,442 rows (60 of the 100 chains per group; bare + layered; 6,490 Asia + 18,952 NY AM rows) were appended with queue_rows_safe.py at the END of pending_nyam_gating.txt (about 406k lines, 405k not DONE, were ahead; I did not reorder). Measured queue throughput 6.5k-11k rows per hour, so these rows start landing in about 40-60 h and finish about 2.5-4 h after that; section 4 and the stress numbers fill themselves when t11_page.py is re-run (a 3-hourly re-run loop is running). **Nothing below that is exact is exact stack evidence yet.** What exists now is the QUICK screen (bare, no layers), the exact live mixes, and the stress rescorer applied to the exact Test 8 held cells.
2. **STRESS RESCORER, first reading on the exact Test 8 held cells (MEASURED vs STRESS, 1 lot per held cell, all months of each hold, 2025-11 dropped):** NY AM $17,730/wk MEASURED -> 16,040 with fee $4.84 -> **12,930 STRESS (73% retained)**; Asia 3,372 -> 3,061 -> **2,604 (77%)**. Recent: NY AM L6M 12,778 -> 6,470 (51% retained), L3M 14,950 -> 12,632; Asia L6M 16,755 -> 13,268, L3M 14,724 -> 10,758. Stress keeps every year's sign the same (NY AM 2023 Q4 stays negative, -8,121 -> -11,525). The L6M NY AM drop is the largest, so the recent NY AM level books are the most exposed to the stop-fill assumption.
3. **A random rule-built level stack is NOT a lower-drawdown companion to the live mix on the quick screen.** Same weeks, bare 1-lot chains vs the exact live mix per base lot: Asia live mix $1,016/wk, max DD 10,791, worst week -6,117, against A4 chains median $982/wk with max DD 31,050 (A6 $1,222, 46,406; B4 $602, 55,695; B6 $839, 57,844). NY AM live mix $3,673/wk, max DD 26,287, worst week -18,204, against A4 $1,748, DD 101,857 (A6 $2,288, 140,377; B4 $1,126, 118,021; B6 $1,320, 167,420). Adding the bare chain beside the live mix lowered the DD in 0% of the 240 Asia chains and 0% of the 240 NY AM chains. Weekly correlation of the chains with the live mix is low in Asia (0.08-0.16) and moderate in NY AM (0.27-0.36). **Caveat that decides it: the chains here are bare; the live mix has its account layers and Trade Health. The layered exact rows (section 4) are the real test of this question and are not in yet.**
4. **Recent first (QUICK, bare, median over 60 chains):** Asia A4 L3M 1,246 / L6M 2,879, A6 1,934 / 4,057, B4 1,215 / 2,198, B6 3,426 / 4,095; NY AM A4 2,255 / 2,331, A6 2,212 / 1,774, B4 4,584 / 3,568, B6 7,669 / 2,600 (live mix per base lot: Asia 2,004 / 2,961, NY AM 8,939 / 9,330). The edge is in the second half: first half-span medians are small or negative for B (Asia B4 -59, NY AM B4 -517) and positive in the last half (Asia B4 1,250, NY AM B4 2,704); 2024-2023 Q4 are negative or flat for the B chains. B (spec-page and builder bar rows only) is weaker than A before 2025 and similar or higher in L3M/last half.
5. **How many qualifiers remain for B:** Asia has 0 on 3 of 13 dates (weeks 52, 91, 104: flat), 1-3 on 5 more (weeks 26, 65, 78, 130, 143), 5-15 on the last four (117, 156, 169, 182); NY AM B has 2-34 per date and only 1 level type on weeks 52 and 65. Level-type diversity is thin everywhere (Asia A 1-9 types, NY AM A 4-9), so size 6 is a relaxed or short draw on most dates: see the flag counts in the plan (code/th_test11/t11_plan.py output) and the 'distinct chains' table in section 0.
6. **E (A4, A5, N4, N5):** 0 of 42 months landed for all eight sets (bare and layered); the rows are in the queue at about line 217k from W-TEST8. Section 5 fills itself on re-run.
7. **Honesty:** the rule was found by looking at Tests 4-8 (hindsight). Quick numbers are bare and use the grid fill; the stress adjustment moves only the fee and `Stop` exits (market exits not re-priced), so STRESS is mild on exits that slip. Everything here is research; nothing was changed live.

## HOW TO READ THIS PAGE
- **Labels.** QUICK = stored-grid trade level (gcore2x re-simulation, grid cost in, bare, no account layers, no stack rules). MEASURED = exact engine as run (fee $1.18 per lot round trip as the engine charges it). FEE = STRESS step 1 (fee raised to $4.84 per lot round trip). STRESS = FEE plus every exit named `Stop` filled worse by the measured real stop slippage of DS3_DN_STOPFILL (1 lot +0.85 pt; the study measured a 10-lot stop-market on DN, 1/5/8/10/13/14 lots = 0.85/1.18/1.34/1.44/1.57/1.61 pt; piecewise-linear in lots, so 6 lots = 1.18 + (1/3)(1.34 - 1.18) = 1.233 pt, 2 lots 0.93, 3 lots 1.02; the 1-lot stack books use 0.85; applied to the books of every session and to the live mixes although the study measured DN; slippage in the study drifts up with time, 2025-26 mean at 10 lots is 1.7, so the 0.85 is the mild end). Market-type exits other than `Stop` (EarlyCut, DayHalt, UWTime, RollFlat) are NOT re-priced, which understates STRESS. **STRESS is a label, not a gate; nothing is dropped.**
- **The rule.** At each of the 13 re-qualify dates (every 13 weeks from week 26, 2023-10-01 to 2026-10-25) the pool is the session's Test 8 primary qualifiers held at that date (t>=4, data before the date only; cells whose event file is empty in the window are dropped). Draw 4 and 6 books at random, at most one per level type (common8.ltype); where fewer types than k exist the draw relaxes to one per level module, then to any (flag counts below); where the pool is smaller than k the whole pool is held; hold to the next date. 100 chains were designed, **the first 60 of each group were built and queued** (same seeds as the 100), because 100 chains was 39.7k rows against a ~25k limit. 1 base lot per book, per-book Trade Health NOT applied (fitted per named book), account layers = Asia JT275 (STK8 SZW3 CGB1 DLA4 DLB14 DLC4) and NY AM JT162 (BL6 CAP6 STK7 SZW2 NTS2 CGB2) on the same bare stack, as th_q2/q2_build.py.
- **Version B** draws only from bar rows with a spec page AND a live builder class in D8Asia.cs: dchg, kagi (same bars as dchg), swing_atr/swing_pct, lbrk, frenko. Excluded: tsf (no page, no class), pnf (page, no class), urenko (no page), and the time/range/other bar families. Level modules mostly have no live code either (the SPEC_STACK pages mark most as NEW), so B is the nearest-to-codable, not buildable today.
- **Honesty.** These stacks are chosen by rule, but the rule (both-sides level books, t>=4 qualifier, 13-week re-pick, Test 8 primary) was found by looking at Tests 4-8 on the same data; hindsight label on every number. The Test 8 excess sits in the second half of the span (first 80 weeks about zero in Asia). Exact numbers carry the same weeks as the quick screen.
- Weeks 2025-11 are not in the fleet and are removed on every basis. Weekly bins = 7 days from 2023-04-02 by ET entry date. L3M = last 13 weeks, L6M = last 26 weeks of the span (to 2026-10-25). Median [5th, 95th percentile] over chains; $/wk and DD are for the whole stack (k books at 1 lot each) unless a row says per base lot.

## 0. HOW MANY QUALIFIERS REMAIN PER DATE (version A = all Test 8 primary qualifiers held at the date with events in the window; version B = the spec-page + live-builder bar rows only)
| session | version | wk 26 | wk 39 | wk 52 | wk 65 | wk 78 | wk 91 | wk 104 | wk 117 | wk 130 | wk 143 | wk 156 | wk 169 | wk 182 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Asia | A (books, level types) | 5, 4 | 13, 2 | 6, 2 | 7, 3 | 16, 5 | 1, 1 | 1, 1 | 11, 4 | 1, 1 | 4, 3 | 22, 5 | 58, 9 | 45, 8 |
| Asia | B (books, level types) | 1, 1 | 6, 1 | 0, 0 | 2, 1 | 3, 2 | 0, 0 | 0, 0 | 5, 3 | 1, 1 | 2, 2 | 8, 3 | 15, 5 | 15, 4 |
| NYAM | A (books, level types) | 48, 7 | 19, 5 | 19, 4 | 13, 5 | 37, 6 | 34, 4 | 43, 7 | 37, 7 | 48, 7 | 85, 9 | 74, 8 | 33, 7 | 19, 4 |
| NYAM | B (books, level types) | 10, 5 | 7, 3 | 8, 1 | 2, 1 | 15, 3 | 12, 3 | 15, 5 | 17, 5 | 23, 7 | 34, 7 | 33, 6 | 15, 4 | 9, 2 |

Distinct chains of the 60 (a chain is identical to another when every date draws the same books; thin pools force this) and distinct stacks:

| group | distinct chains of 60 | unique stacks over 60 chains |
|---|---|---|
| Asia A4 | 60 | 337 |
| Asia A6 | 60 | 327 |
| Asia B4 | 60 | 142 |
| Asia B6 | 60 | 120 |
| NYAM A4 | 60 | 719 |
| NYAM A6 | 60 | 757 |
| NYAM B4 | 60 | 565 |
| NYAM B6 | 60 | 526 |


## 1. QUICK SCREEN, bare (Asia, then NY AM; recent first = L3M, L6M, then years latest first)
Every chain is built from the same books/dates as the exact rows. The live-mix rows are EXACT (live set, per base lot = $ divided by 6), shown as the reference for the same weeks.

**Asia (QUICK)**

| row | chains | $/wk | max DD | worst week | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | first half | last half |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A4 bare QUICK | 60 | 982 [684, 1,448] | 31,050 [20,715, 46,060] | -19,654 [-23,889, -14,604] | 1,246 [-604, 5,643] | 2,879 [1,163, 5,005] | 3,225 [2,217, 4,583] | 4 [-290, 315] | 295 [-58, 824] | 24 [-58, 116] | 384 [144, 729] | 1,542 [963, 2,404] |
| A6 bare QUICK | 60 | 1,222 [875, 1,627] | 46,406 [34,142, 65,954] | -31,855 [-35,279, -25,080] | 1,934 [-718, 4,271] | 4,057 [2,302, 5,498] | 4,003 [3,025, 5,253] | -181 [-386, 31] | 473 [10, 955] | 489 [401, 574] | 593 [291, 900] | 1,904 [1,310, 2,574] |
| B4 bare QUICK | 60 | 602 [274, 783] | 55,695 [55,536, 55,695] | -27,056 [-29,354, -25,565] | 1,215 [-624, 2,958] | 2,198 [475, 3,054] | 2,286 [1,110, 2,933] | 79 [18, 79] | -29 [-145, 87] | -217 [-277, -157] | -59 [-127, 8] | 1,250 [644, 1,604] |
| B6 bare QUICK | 60 | 839 [681, 1,001] | 57,844 [57,844, 57,844] | -40,983 [-40,983, -40,983] | 3,426 [1,863, 5,051] | 4,095 [3,190, 5,146] | 3,304 [2,721, 3,903] | 19 [19, 19] | -100 [-100, -100] | -314 [-314, -314] | -124 [-124, -124] | 1,790 [1,477, 2,113] |
| live Asia mix per base lot, exact, MEASURED | 1 | 1,016 | 10,791 | -6,117 | 2,004 | 2,961 | 2,030 | 652 | 543 | 957 | 579 | 1,448 |
| live Asia mix per base lot, exact, FEE | 1 | 940 | 11,270 | -6,235 | 1,890 | 2,832 | 1,909 | 576 | 490 | 927 | 526 | 1,349 |
| live Asia mix per base lot, exact, STRESS | 1 | 819 | 12,446 | -6,488 | 1,668 | 2,578 | 1,678 | 455 | 428 | 921 | 465 | 1,169 |


**NY AM (QUICK)**

| row | chains | $/wk | max DD | worst week | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | first half | last half |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A4 bare QUICK | 60 | 1,748 [553, 2,662] | 101,857 [58,572, 175,711] | -34,780 [-58,176, -27,295] | 2,255 [-1,812, 5,592] | 2,331 [-1,880, 4,970] | 1,461 [-1,211, 3,754] | 2,881 [1,009, 5,051] | 1,727 [420, 3,077] | -1,327 [-3,665, 1,203] | 1,198 [97, 2,173] | 2,131 [344, 3,849] |
| A6 bare QUICK | 60 | 2,288 [1,069, 3,432] | 140,377 [93,155, 214,957] | -47,794 [-72,763, -35,993] | 2,212 [416, 4,924] | 1,774 [-1,495, 5,470] | 1,202 [-1,839, 4,056] | 4,634 [2,341, 6,741] | 2,455 [1,669, 3,505] | -2,470 [-4,266, 531] | 1,798 [980, 2,689] | 2,855 [1,040, 4,721] |
| B4 bare QUICK | 60 | 1,126 [412, 1,841] | 118,021 [87,273, 166,403] | -40,622 [-68,537, -29,637] | 4,584 [1,990, 8,479] | 3,568 [86, 6,348] | 1,570 [-345, 3,882] | 3,505 [1,867, 4,891] | -775 [-1,099, -303] | -1,312 [-2,281, 107] | -517 [-855, -110] | 2,704 [1,421, 3,987] |
| B6 bare QUICK | 60 | 1,320 [573, 2,091] | 167,420 [127,093, 215,586] | -67,296 [-67,331, -63,682] | 7,669 [5,344, 10,047] | 2,600 [257, 4,827] | 1,291 [-662, 3,257] | 5,282 [4,082, 6,316] | -1,248 [-1,835, -634] | -1,692 [-2,106, -1,119] | -868 [-1,391, -433] | 3,565 [2,018, 4,784] |
| live NY AM mix per base lot, exact, MEASURED | 1 | 3,673 | 26,287 | -18,204 | 8,939 | 9,330 | 6,688 | 4,134 | 1,572 | 878 | 2,172 | 5,153 |
| live NY AM mix per base lot, exact, FEE | 1 | 3,488 | 27,270 | -18,355 | 8,722 | 9,085 | 6,448 | 3,952 | 1,414 | 751 | 2,014 | 4,943 |
| live NY AM mix per base lot, exact, STRESS | 1 | 3,214 | 29,158 | -18,738 | 8,404 | 8,704 | 6,056 | 3,683 | 1,195 | 614 | 1,798 | 4,613 |


## 2. D: AGAINST THE LIVE MIX, SAME WEEKS (hindsight-labelled reference)
Live Asia mix = TL3_SR_AS_STKd8da2eb47b_FSff6_PICKC (6 lots x 4 books, JT275), live NY AM mix = TL3_SR_NY_STKd8cd0279ff_FSff6_PICKC (6/6/6/6/3/6/2/2/3 lots, JT162), each divided by the base lot 6. The chain row is the QUICK bare chain at 1 lot per book (exact chain rows replace it as they land; section 4). "Beside" = live mix per base lot plus the chain, week by week.

**Asia**

| group | live alone DD | chain alone DD (median) | live + chain DD (median) | share of chains with lower DD beside | weekly corr with live (median [5,95]) | chain $/wk | live $/wk |
|---|---|---|---|---|---|---|---|
| A4 bare QUICK chain + live mix per base lot | 10,791 | 31,050 | 32,011 | 0% | 0.16 [0.07, 0.23] | 982 | 1,016 |
| A6 bare QUICK chain + live mix per base lot | 10,791 | 46,406 | 44,991 | 0% | 0.14 [0.08, 0.20] | 1,222 | 1,016 |
| B4 bare QUICK chain + live mix per base lot | 10,791 | 55,695 | 57,567 | 0% | 0.08 [0.02, 0.13] | 602 | 1,016 |
| B6 bare QUICK chain + live mix per base lot | 10,791 | 57,844 | 57,567 | 0% | 0.13 [0.10, 0.17] | 839 | 1,016 |


**NY AM**

| group | live alone DD | chain alone DD (median) | live + chain DD (median) | share of chains with lower DD beside | weekly corr with live (median [5,95]) | chain $/wk | live $/wk |
|---|---|---|---|---|---|---|---|
| A4 bare QUICK chain + live mix per base lot | 26,287 | 101,857 | 87,244 | 0% | 0.33 [0.25, 0.43] | 1,748 | 3,673 |
| A6 bare QUICK chain + live mix per base lot | 26,287 | 140,377 | 116,990 | 0% | 0.36 [0.27, 0.42] | 2,288 | 3,673 |
| B4 bare QUICK chain + live mix per base lot | 26,287 | 118,021 | 93,924 | 0% | 0.27 [0.20, 0.33] | 1,126 | 3,673 |
| B6 bare QUICK chain + live mix per base lot | 26,287 | 167,420 | 125,079 | 0% | 0.27 [0.22, 0.31] | 1,320 | 3,673 |


## 3. HELD CELLS (Test 8 primary, exact, 1 lot per held cell): FIRST READING OF THE STRESS RESCORER
Corrected exact8 scoring (every month of each 13-week hold must be DONE; the end-months-only bug is fixed). Sum over the held cells of the week (zero when none held); STRESS rescored from the TRADES of the same exact runs.

| session | held blocks landed / total | basis | $/wk (sum of held 1-lot cells) | max DD | worst week | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | first half | last half |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NYAM | 329 / 336 | QUICK | 11,503 | 1,781,045 | -477,742 | 17,513 | 4,892 | 7,647 | 27,726 | 6,617 | -13,248 | 3,648 | 19,257 |
| NYAM | 329 / 336 | MEASURED | 17,730 | 1,687,041 | -484,904 | 14,950 | 12,778 | 17,289 | 36,030 | 8,505 | -8,121 | 6,922 | 28,399 |
| NYAM | 329 / 336 | FEE | 16,040 | 1,727,381 | -489,183 | 14,051 | 10,625 | 14,525 | 34,237 | 7,706 | -9,549 | 5,856 | 26,093 |
| NYAM | 329 / 336 | STRESS | 12,930 | 1,810,562 | -499,791 | 12,632 | 6,470 | 9,108 | 30,761 | 6,486 | -11,525 | 4,108 | 21,640 |
| NYAM | | retention STRESS / MEASURED | 73% |
| Asia | 137 / 144 | QUICK | 2,944 | 144,862 | -74,832 | 18,701 | 17,406 | 12,354 | -768 | -543 | 126 | -162 | 6,010 |
| Asia | 137 / 144 | MEASURED | 3,372 | 177,370 | -100,873 | 14,724 | 16,755 | 12,020 | -814 | 1,033 | 167 | 911 | 5,802 |
| Asia | 137 / 144 | FEE | 3,061 | 184,412 | -102,307 | 13,266 | 15,501 | 11,189 | -869 | 858 | 49 | 769 | 5,323 |
| Asia | 137 / 144 | STRESS | 2,604 | 197,502 | -105,707 | 10,758 | 13,268 | 9,730 | -906 | 742 | -70 | 669 | 4,515 |
| Asia | | retention STRESS / MEASURED | 77% |


## 4. EXACT STACK ROWS (A and B, bare and layered), MEASURED and STRESS
Landed 516 of 25442 queued rows. Rows were queued at the END of pending_nyam_gating.txt (about 406k rows were ahead; Q1 not reordered), newest date first, so recent windows land first. Landing by date:

| session | date (week) | rows landed / queued |
|---|---|---|
| Asia | 182 | 516 / 828 |
| Asia | 169 | 0 / 1704 |
| Asia | 156 | 0 / 1360 |
| Asia | 143 | 0 / 16 |
| Asia | 130 | 0 / 6 |
| Asia | 117 | 0 / 448 |
| Asia | 104 | 0 / 8 |
| Asia | 91 | 0 / 8 |
| Asia | 78 | 0 / 880 |
| Asia | 65 | 0 / 96 |
| Asia | 52 | 0 / 80 |
| Asia | 39 | 0 / 1032 |
| Asia | 26 | 0 / 24 |
| NYAM | 182 | 0 / 736 |
| NYAM | 169 | 0 / 1744 |
| NYAM | 156 | 0 / 1912 |
| NYAM | 143 | 0 / 1920 |
| NYAM | 130 | 0 / 1428 |
| NYAM | 117 | 0 / 1768 |
| NYAM | 104 | 0 / 1816 |
| NYAM | 91 | 0 / 1704 |
| NYAM | 78 | 0 / 1872 |
| NYAM | 65 | 0 / 712 |
| NYAM | 52 | 0 / 1288 |
| NYAM | 39 | 0 / 1008 |
| NYAM | 26 | 0 / 1044 |


### Asia

**Asia, MEASURED (engine fee $1.18/lot RT, fills as run)**

Full-chain rows (every one of the 13 dates landed) and the recent-window rows (L3M / L6M computed from the landed recent dates only, so they exist before the full chain does):

| row | chains | $/wk | max DD | worst week | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | first half | last half |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |

Recent windows (median over chains with the dates 156/169/182 landed): none landed yet

**Asia, STRESS (fee $4.84 + stop exits worse, interpolated)**

Full-chain rows (every one of the 13 dates landed) and the recent-window rows (L3M / L6M computed from the landed recent dates only, so they exist before the full chain does):

| row | chains | $/wk | max DD | worst week | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | first half | last half |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |

Recent windows (median over chains with the dates 156/169/182 landed): none landed yet

**Asia, FEE only (fee $4.84, STRESS step 1)**

Full-chain rows (every one of the 13 dates landed) and the recent-window rows (L3M / L6M computed from the landed recent dates only, so they exist before the full chain does):

| row | chains | $/wk | max DD | worst week | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | first half | last half |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |

Recent windows (median over chains with the dates 156/169/182 landed): none landed yet


### NY AM

**NYAM, MEASURED (engine fee $1.18/lot RT, fills as run)**

Full-chain rows (every one of the 13 dates landed) and the recent-window rows (L3M / L6M computed from the landed recent dates only, so they exist before the full chain does):

| row | chains | $/wk | max DD | worst week | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | first half | last half |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |

Recent windows (median over chains with the dates 156/169/182 landed): none landed yet

**NYAM, STRESS (fee $4.84 + stop exits worse, interpolated)**

Full-chain rows (every one of the 13 dates landed) and the recent-window rows (L3M / L6M computed from the landed recent dates only, so they exist before the full chain does):

| row | chains | $/wk | max DD | worst week | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | first half | last half |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |

Recent windows (median over chains with the dates 156/169/182 landed): none landed yet

**NYAM, FEE only (fee $4.84, STRESS step 1)**

Full-chain rows (every one of the 13 dates landed) and the recent-window rows (L3M / L6M computed from the landed recent dates only, so they exist before the full chain does):

| row | chains | $/wk | max DD | worst week | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | first half | last half |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| A6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B4 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 layers (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| B6 bare (exact) | 0 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |

Recent windows (median over chains with the dates 156/169/182 landed): none landed yet


## 5. E: A4, A5, N4, N5 (TL3_SR_<AS|NY>_T8<k>_BARE / _LY)
| set | months landed | basis | $/wk (6 books x 1 lot) | max DD | worst week | L3M | L6M | 2026 | 2025 | 2024 | 2023 Q4 | first half | last half |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TL3_SR_NY_T8N4_LY | 0 / 42 | not landed | | | | | | | | | | | |
| TL3_SR_NY_T8N4_BARE | 0 / 42 | not landed | | | | | | | | | | | |
| TL3_SR_NY_T8N5_LY | 0 / 42 | not landed | | | | | | | | | | | |
| TL3_SR_NY_T8N5_BARE | 0 / 42 | not landed | | | | | | | | | | | |
| TL3_SR_AS_T8A4_LY | 0 / 42 | not landed | | | | | | | | | | | |
| TL3_SR_AS_T8A4_BARE | 0 / 42 | not landed | | | | | | | | | | | |
| TL3_SR_AS_T8A5_LY | 0 / 42 | not landed | | | | | | | | | | | |
| TL3_SR_AS_T8A5_BARE | 0 / 42 | not landed | | | | | | | | | | | |

Rows for the missing sets are in the queue (queued by W-TEST8 at pending_nyam_gating.txt lines ~217k, 3,295 rows given, 374 appended on 11-26). **Re-run when they land: `cd <repo>/outputs && python3 code/th_test11/t11_page.py`** (this section fills itself; no other step). Check DONE: `ls /mnt/l2/l2vast/_th_sz/ijk/exact/runs_rf/TL3_SR_AS_T8A4_BARE/*/DONE | wc -l` (42 needed).

