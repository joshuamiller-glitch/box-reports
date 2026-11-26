# Q5 SESSION STOPS SCALED WITH LOTS (STK8 Asia, STK7 NY AM, STK1 NY PM)

Generated 2026-11-26 20:04Z UTC by code/q_live/pages.py (W-QLIVE; reads finished engine months only, queues nothing; refreshed on each re-run of pages.py). Net of $4.84 per lot round trip, whole-stack engine runs, Globex trading date, weeks Monday-Sunday, one common calendar per session and window. Windows: L6M = 202605-202610 (lead), L3M = 202608-202610, 2023 (from 202304), 2024, 2025 (without 202511). Engine data ends 202610. Progress: 0 of 882 set-months landed. London has no STK in its live build (bare), so it is not in this test.

## ANSWER FIRST (L6M per-lot minus fixed-dollar, same lots; positive d max DD = shallower with per-lot)

Nothing landed yet.

## Asia: live STK = whole-stack day loss stop of $13,600 (fit basis 2 lots per full-weight book, i.e. $6,800 per lot)

At L lots per full-weight book (other books at their live weights, round-half-up, min 1): FIXED = the live dollar value unchanged; PER-LOT = $6,800 x L. At L=2 the two are the same set. L=6 FIXED is the live set itself. NO-STOP (L=6) is the reference with the session stop removed.

### L6M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $13,600 | n/a | n/a | n/a | n/a |
| 4 lots | fixed $13,600 | n/a | n/a | n/a | n/a |
| 4 lots | per lot $27,200 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $13,600 | 17,132 | -36,934 | -19,755 | 10,007 |
| 6 lots | per lot $40,800 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $13,600 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $54,400 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### L3M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $13,600 | n/a | n/a | n/a | n/a |
| 4 lots | fixed $13,600 | n/a | n/a | n/a | n/a |
| 4 lots | per lot $27,200 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $13,600 | 11,869 | -36,934 | -19,755 | 11,249 |
| 6 lots | per lot $40,800 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $13,600 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $54,400 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### 2023

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $13,600 | n/a | n/a | n/a | n/a |
| 4 lots | fixed $13,600 | n/a | n/a | n/a | n/a |
| 4 lots | per lot $27,200 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $13,600 | 2,020 | -33,442 | -10,668 | 11,537 |
| 6 lots | per lot $40,800 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $13,600 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $54,400 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### 2024

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $13,600 | n/a | n/a | n/a | n/a |
| 4 lots | fixed $13,600 | n/a | n/a | n/a | n/a |
| 4 lots | per lot $27,200 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $13,600 | 3,211 | -64,207 | -27,072 | 25,302 |
| 6 lots | per lot $40,800 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $13,600 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $54,400 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### 2025

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $13,600 | n/a | n/a | n/a | n/a |
| 4 lots | fixed $13,600 | n/a | n/a | n/a | n/a |
| 4 lots | per lot $27,200 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $13,600 | 3,032 | -67,941 | -37,409 | 21,399 |
| 6 lots | per lot $40,800 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $13,600 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $54,400 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

## NY AM: live STK = whole-stack day loss stop of $28,800 (fit basis 4 lots per full-weight book, i.e. $7,200 per lot)

At L lots per full-weight book (other books at their live weights, round-half-up, min 1): FIXED = the live dollar value unchanged; PER-LOT = $7,200 x L. At L=4 the two are the same set. L=6 FIXED is the live set itself. NO-STOP (L=6) is the reference with the session stop removed.

### L6M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed $28,800 | n/a | n/a | n/a | n/a |
| 2 lots | per lot $14,400 | n/a | n/a | n/a | n/a |
| 4 lots | fixed = per lot $28,800 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $28,800 | 54,201 | -69,974 | -35,029 | 20,538 |
| 6 lots | per lot $43,200 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $28,800 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $57,600 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### L3M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed $28,800 | n/a | n/a | n/a | n/a |
| 2 lots | per lot $14,400 | n/a | n/a | n/a | n/a |
| 4 lots | fixed = per lot $28,800 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $28,800 | 38,989 | -54,493 | -13,674 | 16,065 |
| 6 lots | per lot $43,200 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $28,800 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $57,600 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### 2023

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed $28,800 | n/a | n/a | n/a | n/a |
| 2 lots | per lot $14,400 | n/a | n/a | n/a | n/a |
| 4 lots | fixed = per lot $28,800 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $28,800 | 9,630 | -133,152 | -48,142 | 56,497 |
| 6 lots | per lot $43,200 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $28,800 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $57,600 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### 2024

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed $28,800 | n/a | n/a | n/a | n/a |
| 2 lots | per lot $14,400 | n/a | n/a | n/a | n/a |
| 4 lots | fixed = per lot $28,800 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $28,800 | 9,411 | -200,647 | -85,477 | 83,442 |
| 6 lots | per lot $43,200 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $28,800 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $57,600 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### 2025

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed $28,800 | n/a | n/a | n/a | n/a |
| 2 lots | per lot $14,400 | n/a | n/a | n/a | n/a |
| 4 lots | fixed = per lot $28,800 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $28,800 | 21,019 | -150,989 | -86,221 | 40,227 |
| 6 lots | per lot $43,200 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $28,800 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $57,600 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

## NY PM: live STK = whole-stack day PROFIT stop of $11,200 (fit basis 2 lots per full-weight book, i.e. $5,600 per lot)

At L lots per full-weight book (other books at their live weights, round-half-up, min 1): FIXED = the live dollar value unchanged; PER-LOT = $5,600 x L. At L=2 the two are the same set. L=6 FIXED is the live set itself. NO-STOP (L=6) is the reference with the session stop removed.

### L6M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $11,200 | n/a | n/a | n/a | n/a |
| 4 lots | fixed $11,200 | n/a | n/a | n/a | n/a |
| 4 lots | per lot $22,400 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $11,200 | 14,299 | -30,613 | -23,047 | 9,301 |
| 6 lots | per lot $33,600 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $11,200 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $44,800 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### L3M

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $11,200 | n/a | n/a | n/a | n/a |
| 4 lots | fixed $11,200 | n/a | n/a | n/a | n/a |
| 4 lots | per lot $22,400 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $11,200 | 15,328 | -20,350 | -18,119 | 6,575 |
| 6 lots | per lot $33,600 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $11,200 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $44,800 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### 2023

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $11,200 | n/a | n/a | n/a | n/a |
| 4 lots | fixed $11,200 | n/a | n/a | n/a | n/a |
| 4 lots | per lot $22,400 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $11,200 | 4,965 | -30,973 | -25,790 | 13,183 |
| 6 lots | per lot $33,600 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $11,200 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $44,800 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### 2024

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $11,200 | n/a | n/a | n/a | n/a |
| 4 lots | fixed $11,200 | n/a | n/a | n/a | n/a |
| 4 lots | per lot $22,400 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $11,200 | 3,065 | -134,363 | -43,719 | 42,286 |
| 6 lots | per lot $33,600 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $11,200 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $44,800 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |

### 2025

| lots | stop | $/wk | max DD | worst week | ulcer |
|---|---|---|---|---|---|
| 2 lots | fixed = per lot $11,200 | n/a | n/a | n/a | n/a |
| 4 lots | fixed $11,200 | n/a | n/a | n/a | n/a |
| 4 lots | per lot $22,400 | n/a | n/a | n/a | n/a |
| 6 lots | fixed $11,200 | 6,197 | -75,805 | -44,139 | 23,898 |
| 6 lots | per lot $33,600 | n/a | n/a | n/a | n/a |
| 8 lots | fixed $11,200 | n/a | n/a | n/a | n/a |
| 8 lots | per lot $44,800 | n/a | n/a | n/a | n/a |
| 6 lots | NO session stop | n/a | n/a | n/a | n/a |
