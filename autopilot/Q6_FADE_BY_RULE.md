# Q6 A FADE IN EVERY SESSION, BY RULE

Generated 2026-11-26 23:49Z UTC by code/q_live/pages.py (W-QLIVE; reads finished engine months only, queues nothing; refreshed on each re-run of pages.py). Net of $4.84 per lot round trip, whole-stack engine runs, Globex trading date, weeks Monday-Sunday, one common calendar per session and window. Windows: L6M = 202605-202610 (lead), L3M = 202608-202610, 2023 (from 202304), 2024, 2025 (without 202511). Engine data ends 202610. Progress: 336 of 336 set-months landed. RULE: qualifiers = every cell the Test 5 PRIMARY rule (N>=100, t>=4, 13-week holds, picks_primary_test5.json) held at any date; fade-type = variant name containing fade / reject / false_break / revert / rev / rej_flow / fail; ranked by mean realised weekly points while held (all its held weeks); the LOWER MEDIAN (index (n-1)//2 ascending) is added to the session live mix at 0.5x and 1x of the full-weight book lots, with the stack-level rules (STK, daily-loss halts, c_gov) covering it and no per-book layers. The ranking uses realised held-week results (hindsight within the primary rule, not a forward pick) and the engine run spans all 42 months, so the fade is in the mix before the date at which the rule would have held it: label HINDSIGHT-CHOSEN-BY-RULE.


## ANSWER FIRST

- Asia + fade Wf8e3f7ad at 0.5x: L6M income +1543 $/wk, max DD +6523 (+ = shallower), worst week +6913; prior years 2023/24/25 (d $/wk / d max DD) +84/+378 / +585/+2030 / +132/+1429.
- Asia + fade Wf8e3f7ad at 1x: L6M income +2654 $/wk, max DD +4611 (+ = shallower), worst week +7388; prior years 2023/24/25 (d $/wk / d max DD) +87/+51 / +937/-389 / +305/+1457.
- London + fade Wc0b8deef at 0.5x: L6M income -265 $/wk, max DD -17162 (+ = shallower), worst week -8618; prior years 2023/24/25 (d $/wk / d max DD) +1065/-6668 / +2771/-2133 / -529/-57424.
- London + fade Wc0b8deef at 1x: L6M income -722 $/wk, max DD -44673 (+ = shallower), worst week -34758; prior years 2023/24/25 (d $/wk / d max DD) +1937/-14098 / +5311/-9883 / -2098/-153633.
- NY AM + fade W8c294722 at 0.5x: L6M income -4726 $/wk, max DD -8195 (+ = shallower), worst week -7157; prior years 2023/24/25 (d $/wk / d max DD) +701/+3036 / +577/-939 / +570/-15674.
- NY AM + fade W8c294722 at 1x: L6M income -6874 $/wk, max DD -5395 (+ = shallower), worst week -2656; prior years 2023/24/25 (d $/wk / d max DD) +1508/+6890 / +1443/-2429 / +1135/-23917.
- NY PM + fade W96aa0cfd at 0.5x: L6M income -929 $/wk, max DD -4322 (+ = shallower), worst week -1695; prior years 2023/24/25 (d $/wk / d max DD) +2392/-315 / -123/+8845 / -1655/-40731.
- NY PM + fade W96aa0cfd at 1x: L6M income -716 $/wk, max DD -8979 (+ = shallower), worst week -505; prior years 2023/24/25 (d $/wk / d max DD) +4331/-2844 / -1328/-6443 / -2582/-61602.

## Asia: fade Wf8e3f7ad (trig_levels_fib60 reject, fixed120/60, long, bars vol_6000; mean 2.8 pts/wk held; lower median of 195 fade qualifiers); lots 0.5x = 3, 1x = 6

### L6M

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 17,132 | - | -36,934 | - | -19,755 | - | 10,007 |
| 0.5x | 18,675 | +1,543 | -30,411 | +6,523 | -12,842 | +6,913 | 9,754 |
| 1x | 19,786 | +2,654 | -32,324 | +4,611 | -12,367 | +7,388 | 10,915 |

### L3M

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 11,869 | - | -36,934 | - | -19,755 | - | 11,249 |
| 0.5x | 13,450 | +1,580 | -30,411 | +6,523 | -12,842 | +6,913 | 10,763 |
| 1x | 14,152 | +2,283 | -30,254 | +6,680 | -12,215 | +7,540 | 11,336 |

### 2023

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 2,020 | - | -33,442 | - | -10,668 | - | 11,537 |
| 0.5x | 2,103 | +84 | -33,064 | +378 | -10,333 | +335 | 11,283 |
| 1x | 2,107 | +87 | -33,391 | +51 | -10,172 | +495 | 11,485 |

### 2024

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 3,211 | - | -64,207 | - | -27,072 | - | 25,302 |
| 0.5x | 3,797 | +585 | -62,178 | +2,030 | -31,291 | -4,219 | 23,237 |
| 1x | 4,148 | +937 | -64,596 | -389 | -34,441 | -7,369 | 24,050 |

### 2025

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 3,032 | - | -67,941 | - | -37,409 | - | 21,399 |
| 0.5x | 3,164 | +132 | -66,512 | +1,429 | -39,383 | -1,975 | 21,789 |
| 1x | 3,337 | +305 | -66,484 | +1,457 | -40,753 | -3,344 | 22,286 |

## London: fade Wc0b8deef (trig_bands_atrchan fade_ema, plain60/60, long, bars entropy_B080; mean -6.0 pts/wk held; lower median of 147 fade qualifiers); lots 0.5x = 4, 1x = 8

### L6M

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 19,562 | - | -39,760 | - | -20,695 | - | 13,228 |
| 0.5x | 19,297 | -265 | -56,921 | -17,162 | -29,313 | -8,618 | 17,226 |
| 1x | 18,840 | -722 | -84,433 | -44,673 | -55,453 | -34,758 | 24,223 |

### L3M

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 18,013 | - | -39,760 | - | -20,172 | - | 15,645 |
| 0.5x | 16,791 | -1,222 | -56,921 | -17,162 | -29,313 | -9,141 | 21,867 |
| 1x | 15,377 | -2,636 | -84,433 | -44,673 | -55,453 | -35,281 | 31,656 |

### 2023

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 2,789 | - | -73,097 | - | -49,327 | - | 30,689 |
| 0.5x | 3,854 | +1,065 | -79,765 | -6,668 | -54,309 | -4,982 | 29,928 |
| 1x | 4,726 | +1,937 | -87,195 | -14,098 | -59,531 | -10,204 | 30,112 |

### 2024

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 4,319 | - | -85,706 | - | -50,689 | - | 24,719 |
| 0.5x | 7,090 | +2,771 | -87,839 | -2,133 | -50,458 | +230 | 20,372 |
| 1x | 9,630 | +5,311 | -95,589 | -9,883 | -68,585 | -17,896 | 20,851 |

### 2025

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 1,221 | - | -224,333 | - | -107,350 | - | 145,224 |
| 0.5x | 692 | -529 | -281,757 | -57,424 | -140,939 | -33,589 | 191,224 |
| 1x | -877 | -2,098 | -377,966 | -153,633 | -176,053 | -68,703 | 263,695 |

## NY AM: fade W8c294722 (trig_levels_profile_nodes false_break_native, plain60/60, long, bars vnorm_150; mean -2.0 pts/wk held; lower median of 272 fade qualifiers); lots 0.5x = 3, 1x = 6

### L6M

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 54,201 | - | -69,974 | - | -35,029 | - | 20,538 |
| 0.5x | 49,475 | -4,726 | -78,169 | -8,195 | -42,186 | -7,157 | 24,245 |
| 1x | 47,326 | -6,874 | -75,369 | -5,395 | -37,685 | -2,656 | 25,318 |

### L3M

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 38,989 | - | -54,493 | - | -13,674 | - | 16,065 |
| 0.5x | 34,499 | -4,489 | -61,494 | -7,001 | -22,510 | -8,837 | 20,099 |
| 1x | 32,095 | -6,894 | -61,955 | -7,462 | -37,685 | -24,012 | 23,772 |

### 2023

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 9,630 | - | -133,152 | - | -48,142 | - | 56,497 |
| 0.5x | 10,331 | +701 | -130,116 | +3,036 | -56,272 | -8,131 | 55,540 |
| 1x | 11,138 | +1,508 | -126,262 | +6,890 | -69,710 | -21,568 | 51,033 |

### 2024

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 9,411 | - | -200,647 | - | -85,477 | - | 83,442 |
| 0.5x | 9,989 | +577 | -201,587 | -939 | -83,443 | +2,034 | 83,785 |
| 1x | 10,854 | +1,443 | -203,077 | -2,429 | -78,132 | +7,344 | 86,491 |

### 2025

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 21,019 | - | -150,989 | - | -86,221 | - | 40,227 |
| 0.5x | 21,589 | +570 | -166,664 | -15,674 | -88,414 | -2,193 | 43,266 |
| 1x | 22,154 | +1,135 | -174,906 | -23,917 | -86,992 | -771 | 45,675 |

## NY PM: fade W96aa0cfd (trig_levels_book_walls_loose reject_native, asym20u/10u, both, bars vol_350; mean -0.2 pts/wk held; lower median of 113 fade qualifiers); lots 0.5x = 3, 1x = 6

### L6M

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 14,299 | - | -30,613 | - | -23,047 | - | 9,301 |
| 0.5x | 13,370 | -929 | -34,935 | -4,322 | -24,742 | -1,695 | 11,466 |
| 1x | 13,583 | -716 | -39,592 | -8,979 | -23,551 | -505 | 11,967 |

### L3M

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 15,328 | - | -20,350 | - | -18,119 | - | 6,575 |
| 0.5x | 16,651 | +1,324 | -31,185 | -10,836 | -18,612 | -493 | 9,875 |
| 1x | 17,887 | +2,560 | -21,619 | -1,269 | -19,530 | -1,411 | 6,862 |

### 2023

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 4,965 | - | -30,973 | - | -25,790 | - | 13,183 |
| 0.5x | 7,358 | +2,392 | -31,288 | -315 | -24,823 | +967 | 11,753 |
| 1x | 9,296 | +4,331 | -33,817 | -2,844 | -28,040 | -2,250 | 12,341 |

### 2024

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 3,065 | - | -134,363 | - | -43,719 | - | 42,286 |
| 0.5x | 2,943 | -123 | -125,518 | +8,845 | -45,228 | -1,508 | 36,764 |
| 1x | 1,737 | -1,328 | -140,806 | -6,443 | -44,210 | -491 | 45,420 |

### 2025

| mix | $/wk | d $/wk | max DD | d max DD (+ = shallower) | worst week | d worst wk | ulcer |
|---|---|---|---|---|---|---|---|
| LIVE | 6,197 | - | -75,805 | - | -44,139 | - | 23,898 |
| 0.5x | 4,543 | -1,655 | -116,536 | -40,731 | -49,324 | -5,185 | 33,714 |
| 1x | 3,615 | -2,582 | -137,406 | -61,602 | -60,502 | -16,363 | 40,239 |
