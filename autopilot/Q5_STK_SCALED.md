# Q5 SESSION STOPS SCALED WITH LOTS (STK8 Asia, STK7 NY AM, STK1 NY PM)

Generated 2026-11-26 23:49Z UTC by code/q_live/pages.py (W-QLIVE; reads finished engine months only, queues nothing; refreshed on each re-run of pages.py). Net of $4.84 per lot round trip, whole-stack engine runs, Globex trading date, weeks Monday-Sunday, one common calendar per session and window. Windows: L6M = 202605-202610 (lead), L3M = 202608-202610, 2023 (from 202304), 2024, 2025 (without 202511). Engine data ends 202610. Progress: 882 of 882 set-months landed. London has no STK in its live build (bare), so it is not in this test.

## ANSWER FIRST (L6M per-lot minus fixed-dollar, same lots; positive d max DD = shallower with per-lot)

- Asia at 4 lots: per-lot minus fixed, L6M income +162 $/wk, max DD +0 (+ = shallower), worst week +0; prior years 2023/24/25 (d $/wk / d max DD) +0/+0 ; -50/-2676 ; +0/+0.
- Asia at 6 lots: per-lot minus fixed, L6M income +625 $/wk, max DD +6248 (+ = shallower), worst week +6248; prior years 2023/24/25 (d $/wk / d max DD) +0/+0 ; -322/-15939 ; +24/+8292.
- Asia at 8 lots: per-lot minus fixed, L6M income +3746 $/wk, max DD +12005 (+ = shallower), worst week +17383; prior years 2023/24/25 (d $/wk / d max DD) +0/+0 ; +49/-7479 ; +742/+24429.
- NY AM at 4 lots: per-lot minus fixed, L6M income +0 $/wk, max DD +0 (+ = shallower), worst week +0; prior years 2023/24/25 (d $/wk / d max DD) +0/+0 ; +0/+0 ; +0/+0.
- NY AM at 6 lots: per-lot minus fixed, L6M income -774 $/wk, max DD -13441 (+ = shallower), worst week -4880; prior years 2023/24/25 (d $/wk / d max DD) +423/+1955 ; -589/+45137 ; +224/+2934.
- NY AM at 8 lots: per-lot minus fixed, L6M income +9735 $/wk, max DD -6215 (+ = shallower), worst week +20203; prior years 2023/24/25 (d $/wk / d max DD) -1529/-11510 ; +1333/+64034 ; -1867/+10115.
- NY PM at 4 lots: per-lot minus fixed, L6M income +357 $/wk, max DD +0 (+ = shallower), worst week +0; prior years 2023/24/25 (d $/wk / d max DD) -5/+0 ; +120/-1286 ; -114/+1886.
- NY PM at 6 lots: per-lot minus fixed, L6M income +267 $/wk, max DD +0 (+ = shallower), worst week +4927; prior years 2023/24/25 (d $/wk / d max DD) -614/-4693 ; +617/+452 ; +1818/+23123.
- NY PM at 8 lots: per-lot minus fixed, L6M income +2203 $/wk, max DD +1885 (+ = shallower), worst week +7693; prior years 2023/24/25 (d $/wk / d max DD) -542/+5869 ; -271/-23462 ; +2980/+11474.

## Asia: live STK = whole-stack day loss stop of $13,600 (fit basis 2 lots per full-weight book, i.e. $6,800 per lot)

At L lots per full-weight book (other books at their live weights, round-half-up, min 1): FIXED = the live dollar value unchanged; PER-LOT = $6,800 x L. At L=2 the two are the same set. L=6 FIXED is the live set itself. NO-STOP (L=6) is the reference with the session stop removed.

### L6M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $13,600 | 7,316 | -10,523 | -5,182 | 2,886 |
| 4 lots | fixed $13,600 | 12,800 | -18,508 | -7,878 | 5,521 |
| 4 lots | per lot $27,200 | 12,962 | -18,508 | -7,878 | 5,406 |
| 6 lots | fixed $13,600 | 17,132 | -36,934 | -19,755 | 10,007 |
| 6 lots | per lot $40,800 | 17,757 | -30,686 | -13,507 | 9,396 |
| 8 lots | fixed $13,600 | 18,230 | -50,461 | -34,103 | 18,013 |
| 8 lots | per lot $54,400 | 21,977 | -38,456 | -16,720 | 13,347 |
| 6 lots | NO session stop | 17,757 | -30,686 | -13,507 | 9,396 |

### L3M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $13,600 | 5,656 | -10,523 | -5,182 | 3,151 |
| 4 lots | fixed $13,600 | 9,961 | -18,508 | -7,715 | 5,596 |
| 4 lots | per lot $27,200 | 9,961 | -18,508 | -7,715 | 5,596 |
| 6 lots | fixed $13,600 | 11,869 | -36,934 | -19,755 | 11,249 |
| 6 lots | per lot $40,800 | 13,573 | -30,686 | -13,507 | 9,650 |
| 8 lots | fixed $13,600 | 14,654 | -42,611 | -20,875 | 13,830 |
| 8 lots | per lot $54,400 | 17,245 | -38,456 | -16,720 | 12,567 |
| 6 lots | NO session stop | 13,573 | -30,686 | -13,507 | 9,650 |

### 2023

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $13,600 | 815 | -10,634 | -3,586 | 3,687 |
| 4 lots | fixed $13,600 | 1,326 | -21,196 | -6,932 | 7,219 |
| 4 lots | per lot $27,200 | 1,326 | -21,196 | -6,932 | 7,219 |
| 6 lots | fixed $13,600 | 2,020 | -33,442 | -10,668 | 11,537 |
| 6 lots | per lot $40,800 | 2,020 | -33,442 | -10,668 | 11,537 |
| 8 lots | fixed $13,600 | 2,465 | -44,497 | -14,169 | 15,695 |
| 8 lots | per lot $54,400 | 2,465 | -44,497 | -14,169 | 15,695 |
| 6 lots | NO session stop | 2,020 | -33,442 | -10,668 | 11,537 |

### 2024

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $13,600 | 1,223 | -22,546 | -11,782 | 8,441 |
| 4 lots | fixed $13,600 | 1,947 | -48,612 | -20,069 | 19,856 |
| 4 lots | per lot $27,200 | 1,897 | -51,288 | -22,745 | 20,976 |
| 6 lots | fixed $13,600 | 3,211 | -64,207 | -27,072 | 25,302 |
| 6 lots | per lot $40,800 | 2,889 | -80,147 | -39,987 | 32,127 |
| 8 lots | fixed $13,600 | 3,361 | -110,033 | -36,946 | 44,372 |
| 8 lots | per lot $54,400 | 3,409 | -117,512 | -53,095 | 48,697 |
| 6 lots | NO session stop | 2,889 | -80,147 | -39,987 | 32,127 |

### 2025

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $13,600 | 1,309 | -20,086 | -13,135 | 6,696 |
| 4 lots | fixed $13,600 | 2,179 | -38,474 | -27,297 | 13,126 |
| 4 lots | per lot $27,200 | 2,179 | -38,474 | -27,297 | 13,126 |
| 6 lots | fixed $13,600 | 3,032 | -67,941 | -37,409 | 21,399 |
| 6 lots | per lot $40,800 | 3,056 | -59,650 | -42,408 | 20,418 |
| 8 lots | fixed $13,600 | 2,538 | -103,861 | -59,621 | 31,712 |
| 8 lots | per lot $54,400 | 3,280 | -79,432 | -56,774 | 28,943 |
| 6 lots | NO session stop | 3,056 | -59,650 | -42,408 | 20,418 |

## NY AM: live STK = whole-stack day loss stop of $28,800 (fit basis 4 lots per full-weight book, i.e. $7,200 per lot)

At L lots per full-weight book (other books at their live weights, round-half-up, min 1): FIXED = the live dollar value unchanged; PER-LOT = $7,200 x L. At L=4 the two are the same set. L=6 FIXED is the live set itself. NO-STOP (L=6) is the reference with the session stop removed.

### L6M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed $28,800 | 20,267 | -36,235 | -10,288 | 10,345 |
| 2 lots | per lot $14,400 | 21,233 | -29,623 | -10,288 | 7,596 |
| 4 lots | fixed = per lot $28,800 | 36,786 | -52,244 | -17,099 | 14,679 |
| 6 lots | fixed $28,800 | 54,201 | -69,974 | -35,029 | 20,538 |
| 6 lots | per lot $43,200 | 53,427 | -83,415 | -39,909 | 24,612 |
| 8 lots | fixed $28,800 | 60,357 | -103,513 | -69,021 | 29,827 |
| 8 lots | per lot $57,600 | 70,092 | -109,728 | -48,818 | 31,161 |
| 6 lots | NO session stop | 49,871 | -108,227 | -39,909 | 34,237 |

### L3M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed $28,800 | 14,438 | -36,235 | -6,518 | 11,294 |
| 2 lots | per lot $14,400 | 15,569 | -20,833 | -6,518 | 6,090 |
| 4 lots | fixed = per lot $28,800 | 25,497 | -46,899 | -8,939 | 13,086 |
| 6 lots | fixed $28,800 | 38,989 | -54,493 | -13,674 | 16,065 |
| 6 lots | per lot $43,200 | 37,114 | -74,562 | -13,674 | 21,231 |
| 8 lots | fixed $28,800 | 38,288 | -54,315 | -13,919 | 21,004 |
| 8 lots | per lot $57,600 | 50,409 | -90,000 | -13,919 | 25,264 |
| 6 lots | NO session stop | 34,398 | -108,227 | -13,674 | 37,481 |

### 2023

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed $28,800 | 4,406 | -43,618 | -21,935 | 17,424 |
| 2 lots | per lot $14,400 | 4,417 | -43,618 | -21,525 | 17,407 |
| 4 lots | fixed = per lot $28,800 | 6,909 | -84,093 | -33,928 | 35,167 |
| 6 lots | fixed $28,800 | 9,630 | -133,152 | -48,142 | 56,497 |
| 6 lots | per lot $43,200 | 10,053 | -131,197 | -52,049 | 54,791 |
| 8 lots | fixed $28,800 | 14,318 | -161,625 | -75,590 | 72,998 |
| 8 lots | per lot $57,600 | 12,789 | -173,135 | -70,751 | 73,891 |
| 6 lots | NO session stop | 10,053 | -131,197 | -52,049 | 54,791 |

### 2024

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed $28,800 | 3,967 | -48,868 | -25,667 | 16,968 |
| 2 lots | per lot $14,400 | 3,776 | -48,868 | -25,667 | 17,076 |
| 4 lots | fixed = per lot $28,800 | 6,267 | -107,079 | -58,238 | 39,114 |
| 6 lots | fixed $28,800 | 9,411 | -200,647 | -85,477 | 83,442 |
| 6 lots | per lot $43,200 | 8,822 | -155,510 | -85,477 | 62,495 |
| 8 lots | fixed $28,800 | 9,729 | -285,680 | -103,819 | 121,620 |
| 8 lots | per lot $57,600 | 11,062 | -221,646 | -117,677 | 89,189 |
| 6 lots | NO session stop | 9,107 | -155,510 | -85,477 | 62,532 |

### 2025

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed $28,800 | 8,304 | -48,742 | -39,555 | 12,778 |
| 2 lots | per lot $14,400 | 8,212 | -50,627 | -29,304 | 13,373 |
| 4 lots | fixed = per lot $28,800 | 14,198 | -94,622 | -51,042 | 25,988 |
| 6 lots | fixed $28,800 | 21,019 | -150,989 | -86,221 | 40,227 |
| 6 lots | per lot $43,200 | 21,243 | -148,055 | -79,782 | 39,914 |
| 8 lots | fixed $28,800 | 29,072 | -211,185 | -100,794 | 51,536 |
| 8 lots | per lot $57,600 | 27,205 | -201,069 | -105,582 | 54,564 |
| 6 lots | NO session stop | 20,505 | -148,055 | -111,919 | 40,115 |

## NY PM: live STK = whole-stack day PROFIT stop of $11,200 (fit basis 2 lots per full-weight book, i.e. $5,600 per lot)

At L lots per full-weight book (other books at their live weights, round-half-up, min 1): FIXED = the live dollar value unchanged; PER-LOT = $5,600 x L. At L=2 the two are the same set. L=6 FIXED is the live set itself. NO-STOP (L=6) is the reference with the session stop removed.

### L6M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $11,200 | 5,606 | -10,368 | -5,033 | 3,173 |
| 4 lots | fixed $11,200 | 9,449 | -20,185 | -12,801 | 6,385 |
| 4 lots | per lot $22,400 | 9,806 | -20,185 | -12,801 | 6,343 |
| 6 lots | fixed $11,200 | 14,299 | -30,613 | -23,047 | 9,301 |
| 6 lots | per lot $33,600 | 14,566 | -30,613 | -18,119 | 8,939 |
| 8 lots | fixed $11,200 | 17,166 | -42,396 | -33,706 | 14,295 |
| 8 lots | per lot $44,800 | 19,369 | -40,511 | -26,013 | 12,119 |
| 6 lots | NO session stop | 14,566 | -30,613 | -18,119 | 8,939 |

### L3M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $11,200 | 5,718 | -6,041 | -5,033 | 2,114 |
| 4 lots | fixed $11,200 | 9,813 | -14,148 | -12,801 | 4,394 |
| 4 lots | per lot $22,400 | 10,456 | -14,148 | -12,801 | 4,396 |
| 6 lots | fixed $11,200 | 15,328 | -20,350 | -18,119 | 6,575 |
| 6 lots | per lot $33,600 | 15,648 | -20,350 | -18,119 | 6,580 |
| 8 lots | fixed $11,200 | 21,351 | -28,591 | -26,013 | 9,031 |
| 8 lots | per lot $44,800 | 21,178 | -28,591 | -26,013 | 9,090 |
| 6 lots | NO session stop | 15,648 | -20,350 | -18,119 | 6,580 |

### 2023

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $11,200 | 1,718 | -11,779 | -8,513 | 4,839 |
| 4 lots | fixed $11,200 | 3,193 | -23,760 | -17,162 | 9,472 |
| 4 lots | per lot $22,400 | 3,188 | -23,760 | -17,162 | 9,472 |
| 6 lots | fixed $11,200 | 4,965 | -30,973 | -25,790 | 13,183 |
| 6 lots | per lot $33,600 | 4,351 | -35,666 | -25,790 | 14,447 |
| 8 lots | fixed $11,200 | 6,228 | -53,725 | -34,583 | 20,653 |
| 8 lots | per lot $44,800 | 5,686 | -47,856 | -34,583 | 19,810 |
| 6 lots | NO session stop | 4,351 | -35,666 | -25,790 | 14,447 |

### 2024

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $11,200 | 1,576 | -45,528 | -15,474 | 14,194 |
| 4 lots | fixed $11,200 | 2,824 | -86,580 | -28,070 | 27,111 |
| 4 lots | per lot $22,400 | 2,944 | -87,866 | -28,070 | 27,597 |
| 6 lots | fixed $11,200 | 3,065 | -134,363 | -43,719 | 42,286 |
| 6 lots | per lot $33,600 | 3,682 | -133,911 | -43,719 | 42,836 |
| 8 lots | fixed $11,200 | 5,113 | -152,210 | -56,430 | 48,886 |
| 8 lots | per lot $44,800 | 4,843 | -175,671 | -56,430 | 56,464 |
| 6 lots | NO session stop | 3,682 | -133,911 | -43,719 | 42,836 |

### 2025

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $11,200 | 2,907 | -17,873 | -14,215 | 6,802 |
| 4 lots | fixed $11,200 | 5,518 | -37,617 | -25,797 | 13,193 |
| 4 lots | per lot $22,400 | 5,404 | -35,731 | -25,761 | 13,554 |
| 6 lots | fixed $11,200 | 6,197 | -75,805 | -44,139 | 23,898 |
| 6 lots | per lot $33,600 | 8,016 | -52,682 | -40,096 | 20,144 |
| 8 lots | fixed $11,200 | 6,744 | -83,645 | -59,696 | 29,358 |
| 8 lots | per lot $44,800 | 9,724 | -72,171 | -53,276 | 27,572 |
| 6 lots | NO session stop | 8,310 | -52,682 | -40,096 | 20,144 |
