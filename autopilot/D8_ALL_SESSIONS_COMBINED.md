# D8 ALL SESSIONS COMBINED (W-COMBINED; order 0745Z; Josh: "do we have combined #s now that we have all books by ny pm? like weekly DD/prfit?")

Generated 2026-11-25 06:40Z UTC by code/d8_combined/combine.py (reads finished engine sets only; queues and edits nothing; refreshed by cron every 2 h). Information only: no new runs.

**Basis.** Every D8 row is TRULY BARE (R0): trigger + own bracket + scheduled session-end exit, no D7 account layers, no stack rules, no sizer, no zones/TH; 1 lot per book, dollars NET of $4.84 per lot round trip. Daily P&L is by Globex trading date; all series are put on ONE common trading-day calendar (union of every series' trading dates in the window, zero-filled), weeks are Monday-Sunday. $ per week = mean weekly P&L; ulcer = root-mean-square of the daily drawdown from the running peak; max DD = worst peak-to-trough on the daily cumulative; trades per day = trades per common trading day. Windows: L6M = 202605-202610, L3M = 202608-202610, prior years 2023 (from 202304), 2024, 2025 (without 202511).

**Data end (per series, last trade date):** Asia D8 20261030; Asia D7 20261030; NY AM D8 20261030; NY AM D7 20261030; London D8 20261030; London D7 20261030; NY PM D8 20261030; NY PM D7 20261030. The engine sets run to month 202610 (the November tape hole 11-02..04 and later days are not in them); the newest live-week data (td 20261113) is NOT in these series.

**How each D8 session stack is built here (all truly bare, 1 lot per book):** Asia = the bare run of the pinned 5-book stack `TL3_SR_AS_STKd8106b26ef_BF1_BASE` (Lb0e6dfa3.BRF40_80, L385f4f2e.J502, L92a90948, L6b373671.BRP60, L578701ed.BRF30_90). NY AM = bare run of `TL3_SR_NY_STKd8b76ecd35_BF1_BASE` (L8cfda948, Lf0346d55, L7cc56d99, Lbb254083, L8f11883e). London = the single book L19201dfc.BRF90_30 (`TL3_ALN_LO_L19201dfc_R0BRF90_30`, R0 base; recent-basis FINAL on the complete pool; exits pending). NY PM = the 4-book FINAL (L52359bf4.BRP30, L8e0bf58c.BRS8U, L4bdd521a.BRF80_40, L2c6916a5.BRP60), bare stack run `TL3_SR_NP_STKd893133bd8_BF1_BASE` (stack identity STKd893133bd8; it equals the sum of the four members' own bare R0 sets, as books do not interact when bare). BARE D7 = the bare D7 stack of that session at 1 lot per book: Asia A7+H7+K7+P7+U7 `TL3_ALN_AS_STKLIVE_BARE`, NY AM `TL3_ALN_NY_STKLIVE_BARE`, London `TL3_ALN_LO_STKLIVE_BARE`, NY PM = K7 alone `TL3_ALN_NP_STKLIVE_BARER0` (see BARE_D7_YARDSTICK.md).

## 2-LOT REFRESH: combined profit and drawdown as tonight's D8 file runs (2 lots per book, plain 2-lot dollars)

Refreshed 2026-11-25 06:40Z UTC by combine.py (cron every 2 h; re-resolves the NY PM pick each run). Directive: DIRECTIVE_COMBINED_REFRESH_20261123_2010Z.md. Reporting only.

**NY PM = the STC-free pick `TL3_SR_NP_STKd893133bd8_BF2_JT209` (rank 0.002 run, W-LAYERS2): runnable in the file.**

Merged run = the four daily series added by trading date on one common calendar (true combined drawdown, not a sum of session drawdowns). Asia = BF2_JT19, NY AM = BF2_JT68, London = L19201dfc bare (BF2_BASE), NY PM as above. Dollars net of $4.84 per lot round trip, 2 lots per book, whole-stack plain 2-lot dollars (what the NinjaTrader panel shows with 2 in the lots field). Columns: $ per week = mean Monday-Sunday week; max DD = worst peak-to-trough of the daily cumulative; worst wk; worst day; ulcer = RMS daily drawdown.

**Series end (last trade date in the sets used):** Asia 20261030; NY AM 20261030; London 20261030; NY PM 20261030; bare Asia 20261030; bare NY AM 20261030; bare NY PM 20261030. Engine sets stop at month 202610; November and the live weeks are NOT in them. Base: landed series only.

### L6M (202605-202610) with L3M (202608-202610) beside

| row | L6M $/wk | max DD | worst wk | worst day | ulcer | L3M $/wk | max DD | worst wk | worst day | ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| Asia alone (BF2_JT19) | 9,849 | -8,694 | -3,660 | -7,635 | 2,733 | 8,862 | -6,429 | 847 | -4,676 | 2,013 |
| NY AM alone (BF2_JT68) | 6,076 | -10,218 | -4,550 | -5,504 | 3,507 | 4,029 | -10,218 | -4,550 | -5,504 | 4,181 |
| London alone (bare) | 3,265 | -7,836 | -5,371 | -6,629 | 2,673 | 2,737 | -7,836 | -4,903 | -6,629 | 3,034 |
| NY PM alone (JT209) | 5,871 | -9,660 | -7,288 | -6,769 | 2,894 | 6,063 | -7,740 | -7,288 | -5,329 | 1,931 |
| Asia + NY AM | 15,926 | -14,863 | -641 | -8,794 | 3,793 | 12,891 | -11,475 | 2,221 | -8,794 | 4,247 |
| Asia + NY AM + London | 19,190 | -13,321 | -106 | -10,013 | 3,766 | 15,628 | -12,390 | 1,826 | -10,013 | 4,154 |
| **ALL FOUR, as tonight's file runs (merged run)** | 25,061 | -11,986 | 226 | -10,871 | 3,397 | 21,691 | -11,986 | 6,747 | -8,454 | 3,437 |
| reference only: all four truly BARE at 2 lots | 46,618 | -37,484 | -8,049 | -22,329 | 8,296 | 44,199 | -37,484 | 3,698 | -22,329 | 9,609 |
| NY PM, all four sessions WITHOUT L8e0bf58c | not computable from landed series (see below) | | | | | | | | | |

### 2023

| row | $/wk | max DD | worst wk | worst day | ulcer |
|---|---|---|---|---|---|
| Asia alone (BF2_JT19) | 316 | -19,901 | -10,935 | -9,187 | 9,688 |
| NY AM alone (BF2_JT68) | 1,738 | -40,383 | -16,292 | -10,894 | 14,949 |
| London alone (bare) | 539 | -10,495 | -5,119 | -3,600 | 3,828 |
| NY PM alone (JT209) | 1,745 | -17,616 | -12,403 | -6,227 | 6,217 |
| Asia + NY AM | 2,054 | -38,824 | -10,095 | -8,717 | 12,125 |
| Asia + NY AM + London | 2,593 | -36,495 | -12,979 | -9,699 | 11,804 |
| **ALL FOUR, as tonight's file runs (merged run)** | 4,337 | -29,997 | -21,128 | -9,531 | 11,163 |
| reference only: all four truly BARE at 2 lots | 9,891 | -36,758 | -30,525 | -20,343 | 10,522 |
| NY PM, all four sessions WITHOUT L8e0bf58c | not computable from landed series | | | | |

### 2024

| row | $/wk | max DD | worst wk | worst day | ulcer |
|---|---|---|---|---|---|
| Asia alone (BF2_JT19) | 1,703 | -24,692 | -10,803 | -7,672 | 8,900 |
| NY AM alone (BF2_JT68) | 2,532 | -22,333 | -14,148 | -8,492 | 8,653 |
| London alone (bare) | 494 | -23,644 | -11,627 | -8,353 | 8,832 |
| NY PM alone (JT209) | 2,064 | -35,972 | -14,610 | -11,310 | 11,157 |
| Asia + NY AM | 4,235 | -39,295 | -20,373 | -10,409 | 11,670 |
| Asia + NY AM + London | 4,728 | -44,903 | -28,871 | -11,520 | 12,198 |
| **ALL FOUR, as tonight's file runs (merged run)** | 6,792 | -41,160 | -27,382 | -13,959 | 10,977 |
| reference only: all four truly BARE at 2 lots | 11,114 | -66,922 | -43,454 | -36,048 | 19,118 |
| NY PM, all four sessions WITHOUT L8e0bf58c | not computable from landed series | | | | |

### 2025 (without 202511)

| row | $/wk | max DD | worst wk | worst day | ulcer |
|---|---|---|---|---|---|
| Asia alone (BF2_JT19) | 532 | -48,777 | -21,341 | -11,348 | 21,958 |
| NY AM alone (BF2_JT68) | 3,372 | -52,524 | -25,712 | -19,192 | 14,728 |
| London alone (bare) | 323 | -25,810 | -9,017 | -6,024 | 10,764 |
| NY PM alone (JT209) | 3,113 | -18,848 | -13,805 | -14,872 | 6,203 |
| Asia + NY AM | 3,904 | -69,829 | -29,338 | -20,128 | 20,480 |
| Asia + NY AM + London | 4,227 | -65,565 | -31,915 | -17,384 | 20,002 |
| **ALL FOUR, as tonight's file runs (merged run)** | 7,340 | -52,270 | -28,427 | -21,813 | 14,507 |
| reference only: all four truly BARE at 2 lots | 15,014 | -92,073 | -43,644 | -46,465 | 25,383 |
| NY PM, all four sessions WITHOUT L8e0bf58c | not computable from landed series | | | | |

### the 42 months (202304-202610)

| row | $/wk | max DD | worst wk | worst day | ulcer |
|---|---|---|---|---|---|
| Asia alone (BF2_JT19) | 2,281 | -48,777 | -21,341 | -17,452 | 14,295 |
| NY AM alone (BF2_JT68) | 2,929 | -52,524 | -25,712 | -19,192 | 13,291 |
| London alone (bare) | 793 | -25,810 | -13,076 | -8,353 | 9,020 |
| NY PM alone (JT209) | 2,882 | -35,972 | -14,610 | -14,872 | 9,020 |
| Asia + NY AM | 5,210 | -76,177 | -29,338 | -20,128 | 16,556 |
| Asia + NY AM + London | 6,003 | -81,092 | -31,915 | -20,988 | 17,293 |
| **ALL FOUR, as tonight's file runs (merged run)** | 8,885 | -67,972 | -31,699 | -21,813 | 13,865 |
| reference only: all four truly BARE at 2 lots | 16,797 | -151,187 | -71,361 | -46,465 | 26,355 |
| NY PM, all four sessions WITHOUT L8e0bf58c | not computable from landed series | | | | |

**In plain words:** over the last 6 months the fits cut the all-four max drawdown from -37,484 to -11,986 and the worst week from -8,049 to 226, and they changed the profit from 46,618 to 25,061 dollars per week (-21556 dollars per week; 2 lots per book).

**NY PM "without L8e0bf58c" row: NOT BUILT.** The NY PM file tonight runs 3 books (L52359bf4, L4bdd521a, L2c6916a5; L8e0bf58c coded but OFF). The merged 2-lot sets (BF2_BASE, BF2_JT*) are whole-stack runs of all 4 books with stack rules and sizer acting across books, so L8e0bf58c cannot be subtracted, and the per-book bare 2-lot sets (TL3_ALN_NP_<book>_R0*_BF2S) have only 1 of 42 months landed. NEW ENGINE ROWS NEEDED, NOT QUEUED: 42 month-rows for the 3-book stack at the chosen pick (one set x 42 months, after the STC-free pick is named), plus 42 more for its bare 3-book reference (84 total). ETA once leased: at the current fleet rate of about 1,100 JT2xx rows per hour that is about 5 minutes of fleet throughput; wall time is set by when the rows are leased (needs an explicit order).

---

## Headline (last 6 months, 1 lot per book, truly bare, net of $4.84 per lot)

- **Asia + NY AM (launch set)**: bare D8 18,329 $/wk, max DD -17,237, worst week -4,596 (bare D7 5,055 $/wk, max DD -41,510, worst week -41,510)
- **Asia + NY AM + London**: bare D8 20,097 $/wk, max DD -18,172, worst week -4,326 (bare D7 5,253 $/wk, max DD -60,089, worst week -44,615)
- **all four**: bare D8 24,726 $/wk, max DD -17,437, worst week -3,975 (bare D7 5,205 $/wk, max DD -69,232, worst week -44,348)
- Reading: in the last 6 months the combined bare D8 book had few losing weeks (see section 2); over all 42 months the whole history is much rougher (max DD and worst week in the all-months table). Bare D7 at the same 1 lot per book is far weaker and rougher on every window. Every window shorter than the whole history is a recent-conditions view.

## AS THE D8 FILE RUNS AT 2 LOTS PER BOOK (fitted picks where they exist; whole-stack dollars at 2 lots per book, NOT per lot)

Josh (order 1725Z): "i want the numbers with the fittings - not bare - so i have an idea". Each row states its basis. **Asia** = the 5-book stack with its 2-lot joint pick `TL3_SR_AS_STKd8106b26ef_BF2_JT19`; **NY AM** = the 5-book stack with its 2-lot joint pick `TL3_SR_NY_STKd8b76ecd35_BF2_JT68`; **London** = L19201dfc BARE at 2 lots (`TL3_SR_LO_L19201dfc_R0BRF90_30_BF2_BASE`; London's fitted pick is not used here, not yet delivered); **NY PM** = the 4-book FINAL BARE at 2 lots (`TL3_SR_NP_STKd893133bd8_BF2_BASE`; a real 2-lot bare run exists, so no 1 lot x 2 stand-in is needed). Bare D8 rows are shown beside the fitted ones; bare D7 is NOT on this table (never fitted D8 beside bare D7).

**Status of each fitted pick (read before the numbers):**
- **Asia 2-lot pick TL3_SR_AS_STKd8106b26ef_BF2_JT19**: label WEAK-BUT-POSITIVE / BEST-AVAILABLE-NOT-PROVEN. Rolling walk-forward vs bare 0.850 over 80 periods (floor 0.58, passes); fixed-pick persistence 0.817; year bands vs bare (equal-risk $/wk) RED / RED / RED; search-aware null FAILED (on the 5-book stack's 1-lot screen the real pick beats 3 of 5 null draws; gate 4 of 5). 29 of 30 date-shift controls (shown, not a gate).
- **NY AM 2-lot pick TL3_SR_NY_STKd8b76ecd35_BF2_JT68**: walk-forward vs bare 0.838 over 80 periods (passes); persistence 0.914; year bands vs bare RED / GREEN / GREEN; null PENDING (not yet run); not yet labelled proven.
- **London** and **NY PM** rows are BARE (no delivered pick; London's and NY PM's null and fit picks are pending).
- **Asia on the 4-lot pick's settings (BF4_JT1, the NinjaTrader file's Asia defaults) run at 2 lots: NO such set exists.** The joint stage builds its levels per lot basis, so none of the 80 combos of the 2-lot joint carries the 4-lot pick's settings (checked on the joint state files). No new run under this item.

### last 6 months (2 lots per book, whole-stack dollars)

| row | basis | $/wk | max DD | worst wk | worst day | losing wks | ulcer |
|---|---|---|---|---|---|---|---|
| all four, as the D8 file runs (Asia FITTED + NY AM FITTED + London bare + NY PM bare) | fitted + bare mix | 27,926 | -15,280 | -1,447 | -14,841 | 4% | 4,759 |
| Asia + NY AM + London (Asia FITTED + NY AM FITTED + London bare) | fitted + bare mix | 19,190 | -13,321 | -106 | -10,013 | 4% | 3,766 |
| Asia + NY AM only (both FITTED) | fitted + bare mix | 15,926 | -14,863 | -641 | -8,794 | 4% | 3,793 |
| Asia FITTED (BF2_JT19) alone | fitted + bare mix | 9,849 | -8,694 | -3,660 | -7,635 | 7% | 2,733 |
| NY AM FITTED (BF2_JT68) alone | fitted + bare mix | 6,076 | -10,218 | -4,550 | -5,504 | 19% | 3,507 |
| London bare alone | bare (R0) | 3,265 | -7,836 | -5,371 | -6,629 | 22% | 2,673 |
| NY PM bare alone | bare (R0) | 8,736 | -24,257 | -8,566 | -16,735 | 19% | 5,573 |
| reference: all four, ALL BARE at 2 lots | bare (R0) | 46,618 | -37,484 | -8,049 | -22,329 | 7% | 8,296 |
| reference: Asia + NY AM, both BARE at 2 lots | bare (R0) | 34,617 | -37,019 | -14,493 | -22,726 | 11% | 9,007 |
| reference: Asia BARE alone | bare (R0) | 20,495 | -21,015 | -19,862 | -13,215 | 11% | 6,963 |
| reference: NY AM BARE alone | bare (R0) | 14,123 | -34,859 | -33,890 | -15,819 | 22% | 9,184 |

### last 3 months (2 lots per book, whole-stack dollars)

| row | basis | $/wk | max DD | worst wk | worst day | losing wks | ulcer |
|---|---|---|---|---|---|---|---|
| all four, as the D8 file runs (Asia FITTED + NY AM FITTED + London bare + NY PM bare) | fitted + bare mix | 24,346 | -13,892 | -1,447 | -9,513 | 8% | 4,619 |
| Asia + NY AM + London (Asia FITTED + NY AM FITTED + London bare) | fitted + bare mix | 15,628 | -12,390 | 1,826 | -10,013 | 0% | 4,154 |
| Asia + NY AM only (both FITTED) | fitted + bare mix | 12,891 | -11,475 | 2,221 | -8,794 | 0% | 4,247 |
| Asia FITTED (BF2_JT19) alone | fitted + bare mix | 8,862 | -6,429 | 847 | -4,676 | 0% | 2,013 |
| NY AM FITTED (BF2_JT68) alone | fitted + bare mix | 4,029 | -10,218 | -4,550 | -5,504 | 31% | 4,181 |
| London bare alone | bare (R0) | 2,737 | -7,836 | -4,903 | -6,629 | 38% | 3,034 |
| NY PM bare alone | bare (R0) | 8,718 | -14,543 | -8,566 | -8,737 | 23% | 4,143 |
| reference: all four, ALL BARE at 2 lots | bare (R0) | 44,199 | -37,484 | 3,698 | -22,329 | 0% | 9,609 |
| reference: Asia + NY AM, both BARE at 2 lots | bare (R0) | 32,744 | -37,019 | -1,645 | -22,726 | 8% | 10,389 |
| reference: Asia BARE alone | bare (R0) | 20,067 | -21,015 | -6,171 | -13,215 | 8% | 7,361 |
| reference: NY AM BARE alone | bare (R0) | 12,677 | -19,455 | -6,945 | -14,238 | 23% | 7,270 |

### 2023 (2 lots per book, whole-stack dollars)

| row | basis | $/wk | max DD | worst wk | worst day | losing wks | ulcer |
|---|---|---|---|---|---|---|---|
| all four, as the D8 file runs (Asia FITTED + NY AM FITTED + London bare + NY PM bare) | fitted + bare mix | 6,008 | -33,600 | -26,944 | -12,415 | 23% | 9,757 |
| Asia + NY AM + London (Asia FITTED + NY AM FITTED + London bare) | fitted + bare mix | 2,593 | -36,495 | -12,979 | -9,699 | 33% | 11,804 |
| Asia + NY AM only (both FITTED) | fitted + bare mix | 2,054 | -38,824 | -10,095 | -8,717 | 36% | 12,125 |
| Asia FITTED (BF2_JT19) alone | fitted + bare mix | 316 | -19,901 | -10,935 | -9,187 | 46% | 9,688 |
| NY AM FITTED (BF2_JT68) alone | fitted + bare mix | 1,738 | -40,383 | -16,292 | -10,894 | 38% | 14,949 |
| London bare alone | bare (R0) | 539 | -10,495 | -5,119 | -3,600 | 46% | 3,828 |
| NY PM bare alone | bare (R0) | 3,415 | -31,725 | -17,024 | -13,106 | 31% | 8,111 |
| reference: all four, ALL BARE at 2 lots | bare (R0) | 9,891 | -36,758 | -30,525 | -20,343 | 28% | 10,522 |
| reference: Asia + NY AM, both BARE at 2 lots | bare (R0) | 5,937 | -52,194 | -19,485 | -17,628 | 36% | 14,990 |
| reference: Asia BARE alone | bare (R0) | 2,030 | -22,507 | -15,616 | -9,477 | 36% | 10,614 |
| reference: NY AM BARE alone | bare (R0) | 3,907 | -62,813 | -26,310 | -24,950 | 38% | 22,251 |

### 2024 (2 lots per book, whole-stack dollars)

| row | basis | $/wk | max DD | worst wk | worst day | losing wks | ulcer |
|---|---|---|---|---|---|---|---|
| all four, as the D8 file runs (Asia FITTED + NY AM FITTED + London bare + NY PM bare) | fitted + bare mix | 7,244 | -43,862 | -29,799 | -28,803 | 36% | 13,929 |
| Asia + NY AM + London (Asia FITTED + NY AM FITTED + London bare) | fitted + bare mix | 4,728 | -44,903 | -28,871 | -11,520 | 36% | 12,198 |
| Asia + NY AM only (both FITTED) | fitted + bare mix | 4,235 | -39,295 | -20,373 | -10,409 | 42% | 11,670 |
| Asia FITTED (BF2_JT19) alone | fitted + bare mix | 1,703 | -24,692 | -10,803 | -7,672 | 43% | 8,900 |
| NY AM FITTED (BF2_JT68) alone | fitted + bare mix | 2,532 | -22,333 | -14,148 | -8,492 | 43% | 8,653 |
| London bare alone | bare (R0) | 494 | -23,644 | -11,627 | -8,353 | 40% | 8,832 |
| NY PM bare alone | bare (R0) | 2,516 | -58,752 | -21,635 | -26,155 | 40% | 21,638 |
| reference: all four, ALL BARE at 2 lots | bare (R0) | 11,114 | -66,922 | -43,454 | -36,048 | 38% | 19,118 |
| reference: Asia + NY AM, both BARE at 2 lots | bare (R0) | 8,104 | -82,114 | -59,593 | -28,667 | 36% | 24,283 |
| reference: Asia BARE alone | bare (R0) | 3,565 | -37,462 | -20,786 | -17,860 | 38% | 10,096 |
| reference: NY AM BARE alone | bare (R0) | 4,539 | -65,834 | -38,807 | -21,624 | 47% | 22,575 |

### 2025 (2 lots per book, whole-stack dollars)

| row | basis | $/wk | max DD | worst wk | worst day | losing wks | ulcer |
|---|---|---|---|---|---|---|---|
| all four, as the D8 file runs (Asia FITTED + NY AM FITTED + London bare + NY PM bare) | fitted + bare mix | 8,450 | -57,508 | -29,244 | -32,697 | 27% | 14,723 |
| Asia + NY AM + London (Asia FITTED + NY AM FITTED + London bare) | fitted + bare mix | 4,227 | -65,565 | -31,915 | -17,384 | 33% | 20,002 |
| Asia + NY AM only (both FITTED) | fitted + bare mix | 3,904 | -69,829 | -29,338 | -20,128 | 29% | 20,480 |
| Asia FITTED (BF2_JT19) alone | fitted + bare mix | 532 | -48,777 | -21,341 | -11,348 | 47% | 21,958 |
| NY AM FITTED (BF2_JT68) alone | fitted + bare mix | 3,372 | -52,524 | -25,712 | -19,192 | 27% | 14,728 |
| London bare alone | bare (R0) | 323 | -25,810 | -9,017 | -6,024 | 39% | 10,764 |
| NY PM bare alone | bare (R0) | 4,223 | -35,977 | -22,882 | -25,756 | 41% | 12,157 |
| reference: all four, ALL BARE at 2 lots | bare (R0) | 15,014 | -92,073 | -43,644 | -46,465 | 33% | 25,383 |
| reference: Asia + NY AM, both BARE at 2 lots | bare (R0) | 10,468 | -112,119 | -43,737 | -46,136 | 37% | 32,582 |
| reference: Asia BARE alone | bare (R0) | 3,516 | -37,467 | -23,895 | -24,160 | 47% | 13,729 |
| reference: NY AM BARE alone | bare (R0) | 6,952 | -119,229 | -60,727 | -34,541 | 35% | 31,164 |

### all 42 months (2 lots per book, whole-stack dollars)

| row | basis | $/wk | max DD | worst wk | worst day | losing wks | ulcer |
|---|---|---|---|---|---|---|---|
| all four, as the D8 file runs (Asia FITTED + NY AM FITTED + London bare + NY PM bare) | fitted + bare mix | 10,045 | -78,147 | -36,884 | -32,697 | 27% | 15,391 |
| Asia + NY AM + London (Asia FITTED + NY AM FITTED + London bare) | fitted + bare mix | 6,003 | -81,092 | -31,915 | -20,988 | 30% | 17,293 |
| Asia + NY AM only (both FITTED) | fitted + bare mix | 5,210 | -76,177 | -29,338 | -20,128 | 30% | 16,556 |
| Asia FITTED (BF2_JT19) alone | fitted + bare mix | 2,281 | -48,777 | -21,341 | -17,452 | 40% | 14,295 |
| NY AM FITTED (BF2_JT68) alone | fitted + bare mix | 2,929 | -52,524 | -25,712 | -19,192 | 35% | 13,291 |
| London bare alone | bare (R0) | 793 | -25,810 | -13,076 | -8,353 | 39% | 9,020 |
| NY PM bare alone | bare (R0) | 4,042 | -58,752 | -22,882 | -26,155 | 35% | 16,553 |
| reference: all four, ALL BARE at 2 lots | bare (R0) | 16,797 | -151,187 | -71,361 | -46,465 | 30% | 26,355 |
| reference: Asia + NY AM, both BARE at 2 lots | bare (R0) | 11,963 | -146,857 | -70,088 | -46,136 | 33% | 30,275 |
| reference: Asia BARE alone | bare (R0) | 5,895 | -67,097 | -34,076 | -24,160 | 36% | 14,134 |
| reference: NY AM BARE alone | bare (R0) | 6,068 | -119,229 | -60,727 | -34,541 | 38% | 26,127 |

Reading guide: the first row is what the D8 file runs at 2 lots per book if Asia and NY AM carry their joint picks and London and NY PM run bare; the "reference" rows are the same books bare, so the cost or gain of the fittings is the difference. Prior-year and all-month rows show how the picks behave outside the last 6 months (the Asia pick is RED there).

## 1. The four session stacks, bare D8 beside bare D7 (1 lot per book)

Columns: $/wk | ulcer | max DD | worst week | worst day | losing weeks | trades per day.

### L6M (131 trading days)

| session | basis | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day |
|---|---|---|---|---|---|---|---|---|
| Asia | bare D8 | 10,834 | 3,046 | -9,450 | -4,971 | -6,578 | 11% | 17.2 |
| Asia | bare D7 | 5,654 | 13,133 | -32,277 | -21,126 | -13,837 | 26% | 14.9 |
| NY AM | bare D8 | 7,495 | 4,355 | -15,007 | -14,493 | -7,608 | 22% | 12.5 |
| NY AM | bare D7 | -599 | 33,655 | -60,055 | -25,697 | -14,302 | 48% | 12.5 |
| London | bare D8 | 1,768 | 1,273 | -3,809 | -2,673 | -3,310 | 19% | 1.9 |
| London | bare D7 | 198 | 26,504 | -54,522 | -24,897 | -17,708 | 44% | 13.1 |
| NY PM | bare D8 | 4,629 | 2,723 | -12,121 | -4,238 | -8,343 | 15% | 10.2 |
| NY PM | bare D7 | -48 | 10,771 | -22,593 | -6,658 | -3,610 | 48% | 2.9 |

### L3M (65 trading days)

| session | basis | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day |
|---|---|---|---|---|---|---|---|---|
| Asia | bare D8 | 10,600 | 3,375 | -9,283 | -1,858 | -6,578 | 8% | 14.2 |
| Asia | bare D7 | 3,191 | 12,212 | -27,920 | -17,823 | -13,837 | 38% | 12.9 |
| NY AM | bare D8 | 6,747 | 3,540 | -9,765 | -3,445 | -7,157 | 23% | 10.8 |
| NY AM | bare D7 | -1,039 | 24,692 | -44,363 | -17,385 | -8,413 | 54% | 11.4 |
| London | bare D8 | 1,643 | 1,406 | -3,402 | -2,449 | -3,310 | 31% | 1.8 |
| London | bare D7 | 1,307 | 18,796 | -38,763 | -24,897 | -11,648 | 46% | 12.1 |
| NY PM | bare D8 | 4,340 | 2,089 | -7,269 | -4,238 | -4,389 | 23% | 9.1 |
| NY PM | bare D7 | -943 | 13,886 | -21,422 | -6,658 | -3,555 | 62% | 2.4 |

### Prior years ($ per week / max DD)

| session | basis | 2023 | 2024 | 2025 | all 42 months ($/wk / ulcer / max DD) |
|---|---|---|---|---|---|
| Asia | bare D8 | 1,042 / -11,178 | 1,917 / -16,311 | 1,982 / -17,403 | 3,169 / 6,751 / -33,033 |
| Asia | bare D7 | -160 / -33,434 | 1,386 / -25,668 | 1,273 / -38,603 | 1,767 / 17,010 / -46,288 |
| NY AM | bare D8 | 2,016 / -31,342 | 2,349 / -31,020 | 3,561 / -59,504 | 3,172 / 12,864 / -59,504 |
| NY AM | bare D7 | 2,077 / -43,707 | 2,238 / -36,886 | 995 / -71,352 | 1,128 / 47,814 / -124,942 |
| London | bare D8 | 273 / -5,238 | 251 / -11,780 | 183 / -12,803 | 453 / 4,115 / -12,803 |
| London | bare D7 | 363 / -40,399 | -1,972 / -134,401 | -369 / -59,694 | -600 / 113,197 / -180,657 |
| NY PM | bare D8 | 1,725 / -15,835 | 1,325 / -29,188 | 2,157 / -17,976 | 2,103 / 8,106 / -29,188 |
| NY PM | bare D7 | -505 / -26,816 | 677 / -26,604 | -298 / -33,310 | -176 / 33,627 / -75,929 |

## 2. The COMBINED book (four daily series added by trading date, 1 lot per book)

### L6M

| combination | basis | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day |
|---|---|---|---|---|---|---|---|---|
| Asia + NY AM (launch set) | bare D8 | 18,329 | 4,037 | -17,237 | -4,596 | -11,311 | 7% | 29.8 |
| Asia + NY AM (launch set) | bare D7 | 5,055 | 16,768 | -41,510 | -41,510 | -19,024 | 30% | 27.4 |
| Asia + NY AM + London | bare D8 | 20,097 | 4,086 | -18,172 | -4,326 | -11,448 | 11% | 31.6 |
| Asia + NY AM + London | bare D7 | 5,253 | 23,492 | -60,089 | -44,615 | -25,561 | 33% | 40.5 |
| all four (Asia + NY AM + London + NY PM) | bare D8 | 24,726 | 3,658 | -17,437 | -3,975 | -11,109 | 4% | 41.9 |
| all four (Asia + NY AM + London + NY PM) | bare D7 | 5,205 | 24,498 | -69,232 | -44,348 | -23,843 | 33% | 43.4 |

### L3M

| combination | basis | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day |
|---|---|---|---|---|---|---|---|---|
| Asia + NY AM (launch set) | bare D8 | 17,347 | 4,855 | -17,237 | 437 | -11,311 | 0% | 25.0 |
| Asia + NY AM (launch set) | bare D7 | 2,152 | 19,119 | -41,232 | -22,501 | -17,224 | 46% | 24.2 |
| Asia + NY AM + London | bare D8 | 18,990 | 4,957 | -18,172 | -497 | -11,311 | 8% | 26.8 |
| Asia + NY AM + London | bare D7 | 3,459 | 26,008 | -60,089 | -27,066 | -19,221 | 46% | 36.3 |
| all four (Asia + NY AM + London + NY PM) | bare D8 | 23,330 | 4,384 | -17,437 | 3,734 | -11,109 | 0% | 35.9 |
| all four (Asia + NY AM + London + NY PM) | bare D7 | 2,515 | 30,421 | -69,232 | -33,724 | -21,560 | 46% | 38.8 |

### Combined, prior years ($ per week / max DD) and all 42 months

| combination | basis | 2023 | 2024 | 2025 | all 42 months ($/wk / ulcer / max DD / worst wk) |
|---|---|---|---|---|---|
| Asia + NY AM (launch set) | bare D8 | 3,058 / -25,837 | 4,266 / -38,555 | 5,543 / -53,652 | 6,340 / 14,460 / -72,611 / -34,774 |
| Asia + NY AM (launch set) | bare D7 | 1,918 / -32,500 | 3,624 / -34,658 | 2,267 / -91,394 | 2,895 / 31,875 / -127,466 / -46,942 |
| Asia + NY AM + London | bare D8 | 3,330 / -23,961 | 4,517 / -40,724 | 5,726 / -54,449 | 6,794 / 14,422 / -73,373 / -33,603 |
| Asia + NY AM + London | bare D7 | 2,281 / -61,000 | 1,652 / -64,746 | 1,899 / -112,919 | 2,295 / 46,612 / -147,843 / -46,879 |
| all four (Asia + NY AM + London + NY PM) | bare D8 | 5,056 / -18,202 | 5,841 / -30,819 | 7,883 / -43,609 | 8,897 / 12,631 / -74,669 / -35,385 |
| all four (Asia + NY AM + London + NY PM) | bare D7 | 1,775 / -67,286 | 2,329 / -49,485 | 1,600 / -111,625 | 2,119 / 54,371 / -189,730 / -44,348 |

### Correlation, co-losses and worst days: bare D8, last 6 months (131 trading days)

Daily correlation / weekly correlation:

| | Asia | NY AM | London | NY PM |
|---|---|---|---|---|
| Asia | 1.00 / 1.00 | 0.02 / 0.07 | 0.03 / -0.14 | -0.06 / 0.41 |
| NY AM | 0.02 / 0.07 | 1.00 / 1.00 | 0.03 / -0.14 | -0.02 / 0.09 |
| London | 0.03 / -0.14 | 0.03 / -0.14 | 1.00 / 1.00 | -0.07 / -0.04 |
| NY PM | -0.06 / 0.41 | -0.02 / 0.09 | -0.07 / -0.04 | 1.00 / 1.00 |

Days with 2 or more sessions losing on the same day: **49 of 131 (37%)** (3 or more: 11; all four: 4; days with at least one losing session: 104). Weeks with 2 or more sessions losing: 4 of 27.

10 worst combined days (all four, bare D8, 1 lot per book):

| trading date | combined | Asia | NY AM | London | NY PM |
|---|---|---|---|---|---|
| 20260807 | -11,109 | -6,578 | -4,733 | 0 | 201 |
| 20260518 | -9,789 | -499 | -17 | -930 | -8,343 |
| 20260706 | -7,531 | -6,325 | -3,713 | -1,410 | 3,918 |
| 20260714 | -7,052 | 170 | -6,733 | -1,800 | 1,311 |
| 20260701 | -6,860 | -3,768 | -1,424 | -175 | -1,493 |
| 20260925 | -5,938 | 867 | -7,157 | 595 | -244 |
| 20260716 | -5,648 | -626 | -804 | -25 | -4,192 |
| 20260603 | -5,314 | 742 | -5,563 | 595 | -1,089 |
| 20261008 | -4,819 | 2,032 | -2,634 | -3,310 | -907 |
| 20260811 | -4,316 | -718 | -304 | -1,529 | -1,764 |

5 worst combined weeks (the first and last week of a window can be partial; in the last 6 months only about 1 week in 27 was a losing week, so this list includes weeks that were still positive):

| week | combined | Asia | NY AM | London | NY PM |
|---|---|---|---|---|---|
| 2026-04-27/2026-05-03 | -3,975 | -4,449 | -148 | 270 | 351 |
| 2026-05-18/2026-05-24 | 1,315 | -4,971 | 2,635 | 992 | 2,660 |
| 2026-08-10/2026-08-16 | 3,734 | -1,858 | 2,296 | -934 | 4,230 |
| 2026-10-05/2026-10-11 | 5,387 | 1,748 | 6,551 | -2,449 | -463 |
| 2026-10-12/2026-10-18 | 6,695 | 4,326 | -3,445 | 3,191 | 2,623 |

### Correlation, co-losses and worst days: bare D8, all 42 months (907 trading days)

Daily correlation / weekly correlation:

| | Asia | NY AM | London | NY PM |
|---|---|---|---|---|
| Asia | 1.00 / 1.00 | 0.05 / 0.10 | -0.01 / 0.15 | -0.01 / 0.22 |
| NY AM | 0.05 / 0.10 | 1.00 / 1.00 | -0.07 / -0.06 | -0.05 / 0.00 |
| London | -0.01 / 0.15 | -0.07 / -0.06 | 1.00 / 1.00 | -0.05 / 0.03 |
| NY PM | -0.01 / 0.22 | -0.05 / 0.00 | -0.05 / 0.03 | 1.00 / 1.00 |

Days with 2 or more sessions losing on the same day: **492 of 907 (54%)** (3 or more: 169; all four: 14; days with at least one losing session: 800). Weeks with 2 or more sessions losing: 90 of 183.

10 worst combined days (all four, bare D8, 1 lot per book):

| trading date | combined | Asia | NY AM | London | NY PM |
|---|---|---|---|---|---|
| 20250227 | -23,202 | 5,847 | -16,111 | 0 | -12,938 |
| 20250305 | -20,417 | -7,003 | -16,175 | 665 | 2,096 |
| 20250114 | -18,786 | -2,069 | -13,643 | 595 | -3,669 |
| 20240809 | -17,939 | -8,853 | -5,403 | 0 | -3,683 |
| 20260323 | -17,348 | -11,077 | -10,032 | 576 | 3,186 |
| 20260120 | -15,411 | -12,072 | -857 | -4,104 | 1,622 |
| 20260114 | -14,615 | -1,589 | -9,768 | 1,190 | -4,449 |
| 20240807 | -14,553 | -547 | -10,792 | 0 | -3,214 |
| 20240718 | -14,109 | -299 | -1,313 | 595 | -13,092 |
| 20250403 | -13,979 | -11,445 | 7,564 | -2,989 | -7,108 |

5 worst combined weeks (the first and last week of a window can be partial):

| week | combined | Asia | NY AM | London | NY PM |
|---|---|---|---|---|---|
| 2026-03-23/2026-03-29 | -35,385 | -15,211 | -19,563 | 1,171 | -1,782 |
| 2025-03-03/2025-03-09 | -19,817 | -9,888 | -10,039 | -1,268 | 1,378 |
| 2024-08-19/2024-08-25 | -19,467 | -8,171 | -19,393 | 240 | 7,857 |
| 2026-01-19/2026-01-25 | -17,808 | -16,911 | 10,870 | -5,878 | -5,889 |
| 2023-04-10/2023-04-16 | -15,190 | 168 | -5,703 | -2,530 | -7,125 |

## 3. The same at 2 and 4 lots per book (bare D8 only; size-dependent fills, so NOT 1-lot x N)

Only sessions whose bare run at that size is on disk are shown. Asia and NY AM: full history. London and NY PM: bare runs at 2 and 4 lots are on disk for all 42 months (from their bare all-layers fits). "per lot" = raw / lots per book.

### 2 lots per book, L6M

| set | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day | per lot: $/wk / ulcer / max DD |
|---|---|---|---|---|---|---|---|---|
| Asia | 20,495 | 6,963 | -21,015 | -19,862 | -13,215 | 11% | 17.3 | 10,247 / 3,481 / -10,508 |
| NY AM | 14,123 | 9,184 | -34,859 | -33,890 | -15,819 | 22% | 12.5 | 7,061 / 4,592 / -17,430 |
| London | 3,265 | 2,673 | -7,836 | -5,371 | -6,629 | 22% | 1.9 | 1,632 / 1,336 / -3,918 |
| NY PM | 8,736 | 5,573 | -24,257 | -8,566 | -16,735 | 19% | 10.2 | 4,368 / 2,787 / -12,129 |
| Asia + NY AM | 34,617 | 9,007 | -37,019 | -14,493 | -22,726 | 11% | 29.8 | 17,309 / 4,504 / -18,510 |
| Asia + NY AM + London | 37,882 | 9,078 | -38,898 | -12,520 | -23,091 | 11% | 31.7 | 18,941 / 4,539 / -19,449 |
| all four | 46,618 | 8,296 | -37,484 | -8,049 | -22,329 | 7% | 41.9 | 23,309 / 4,148 / -18,742 |

### 2 lots per book, L3M

| set | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day | per lot: $/wk / ulcer / max DD |
|---|---|---|---|---|---|---|---|---|
| Asia | 20,067 | 7,361 | -21,015 | -6,171 | -13,215 | 8% | 14.2 | 10,033 / 3,680 / -10,508 |
| NY AM | 12,677 | 7,270 | -19,455 | -6,945 | -14,238 | 23% | 10.8 | 6,339 / 3,635 / -9,728 |
| London | 2,737 | 3,034 | -7,836 | -4,903 | -6,629 | 38% | 1.8 | 1,368 / 1,517 / -3,918 |
| NY PM | 8,718 | 4,143 | -14,543 | -8,566 | -8,737 | 23% | 9.1 | 4,359 / 2,072 / -7,272 |
| Asia + NY AM | 32,744 | 10,389 | -37,019 | -1,645 | -22,726 | 8% | 25.0 | 16,372 / 5,194 / -18,510 |
| Asia + NY AM + London | 35,481 | 10,691 | -38,898 | -3,523 | -22,726 | 8% | 26.8 | 17,740 / 5,345 / -19,449 |
| all four | 44,199 | 9,609 | -37,484 | 3,698 | -22,329 | 0% | 35.9 | 22,100 / 4,804 / -18,742 |

### 2 lots per book, ALL

| set | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day | per lot: $/wk / ulcer / max DD |
|---|---|---|---|---|---|---|---|---|
| Asia | 5,895 | 14,134 | -67,097 | -34,076 | -24,160 | 36% | 8.7 | 2,947 / 7,067 / -33,548 |
| NY AM | 6,068 | 26,127 | -119,229 | -60,727 | -34,541 | 38% | 10.6 | 3,034 / 13,064 / -59,614 |
| London | 793 | 9,020 | -25,810 | -13,076 | -8,353 | 39% | 1.3 | 396 / 4,510 / -12,905 |
| NY PM | 4,042 | 16,553 | -58,752 | -22,882 | -26,155 | 35% | 8.4 | 2,021 / 8,276 / -29,376 |
| Asia + NY AM | 11,963 | 30,275 | -146,857 | -70,088 | -46,136 | 33% | 19.3 | 5,981 / 15,138 / -73,429 |
| Asia + NY AM + London | 12,755 | 30,210 | -148,386 | -67,766 | -44,805 | 34% | 20.5 | 6,378 / 15,105 / -74,193 |
| all four | 16,797 | 26,355 | -151,187 | -71,361 | -46,465 | 30% | 28.9 | 8,399 / 13,178 / -75,594 |

### 4 lots per book, L6M

| set | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day | per lot: $/wk / ulcer / max DD |
|---|---|---|---|---|---|---|---|---|
| Asia | 38,613 | 15,687 | -52,366 | -40,859 | -32,739 | 15% | 17.2 | 9,653 / 3,922 / -13,091 |
| NY AM | 25,731 | 19,480 | -77,843 | -68,225 | -32,003 | 22% | 12.5 | 6,433 / 4,870 / -19,461 |
| London | 6,476 | 5,468 | -15,722 | -9,901 | -13,314 | 22% | 1.9 | 1,619 / 1,367 / -3,931 |
| NY PM | 16,377 | 11,340 | -48,755 | -17,930 | -33,600 | 19% | 10.2 | 4,094 / 2,835 / -12,189 |
| Asia + NY AM | 64,344 | 19,728 | -84,294 | -30,806 | -45,398 | 11% | 29.8 | 16,086 / 4,932 / -21,073 |
| Asia + NY AM + London | 70,820 | 19,875 | -88,116 | -26,940 | -46,437 | 11% | 31.6 | 17,705 / 4,969 / -22,029 |
| all four | 87,197 | 18,298 | -85,523 | -16,640 | -44,668 | 11% | 41.9 | 21,799 / 4,574 / -21,381 |

### 4 lots per book, L3M

| set | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day | per lot: $/wk / ulcer / max DD |
|---|---|---|---|---|---|---|---|---|
| Asia | 39,296 | 16,860 | -52,366 | -22,627 | -26,585 | 15% | 14.2 | 9,824 / 4,215 / -13,091 |
| NY AM | 25,076 | 14,653 | -39,186 | -14,470 | -28,677 | 23% | 10.8 | 6,269 / 3,663 / -9,796 |
| London | 5,408 | 6,144 | -15,722 | -9,901 | -13,314 | 38% | 1.8 | 1,352 / 1,536 / -3,931 |
| NY PM | 17,226 | 8,376 | -29,391 | -17,417 | -17,580 | 23% | 9.1 | 4,306 / 2,094 / -7,348 |
| Asia + NY AM | 64,371 | 23,215 | -84,294 | -13,765 | -45,398 | 8% | 25.0 | 16,093 / 5,804 / -21,073 |
| Asia + NY AM + London | 69,780 | 23,984 | -88,116 | -17,587 | -45,398 | 8% | 26.8 | 17,445 / 5,996 / -22,029 |
| all four | 87,005 | 21,712 | -85,523 | -3,359 | -44,668 | 8% | 35.9 | 21,751 / 5,428 / -21,381 |

### 4 lots per book, ALL

| set | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day | per lot: $/wk / ulcer / max DD |
|---|---|---|---|---|---|---|---|---|
| Asia | 10,661 | 29,898 | -135,873 | -67,043 | -48,597 | 37% | 8.7 | 2,665 / 7,475 / -33,968 |
| NY AM | 11,205 | 53,834 | -239,127 | -121,983 | -68,998 | 39% | 10.6 | 2,801 / 13,458 / -59,782 |
| London | 1,545 | 18,354 | -52,146 | -26,147 | -16,881 | 39% | 1.3 | 386 / 4,588 / -13,036 |
| NY PM | 7,640 | 34,240 | -113,869 | -45,419 | -52,444 | 36% | 8.4 | 1,910 / 8,560 / -28,467 |
| Asia + NY AM | 21,866 | 63,903 | -297,233 | -144,211 | -92,766 | 33% | 19.3 | 5,467 / 15,976 / -74,308 |
| Asia + NY AM + London | 23,411 | 63,658 | -300,951 | -139,582 | -90,110 | 34% | 20.5 | 5,853 / 15,914 / -75,238 |
| all four | 31,052 | 56,633 | -311,512 | -146,905 | -93,424 | 31% | 28.9 | 7,763 / 14,158 / -77,878 |

## 4. Yardstick at equal risk: bare D7 scaled to the bare D8 combined max drawdown (last 6 months, 1 lot)

One factor k per row scales the whole bare D7 combination so its L6M max DD equals the bare D8 one (a linear stand-in; fills are not linear, so read it as the approved yardstick, not a tradable size). Bare D8 next to bare D7 only.

| combination | bare D8 $/wk | bare D8 max DD | bare D7 $/wk | bare D7 max DD | k | bare D7 x k: $/wk | bare D7 x k: worst wk | bare D8 worst wk |
|---|---|---|---|---|---|---|---|---|
| Asia | 10,834 | -9,450 | 5,654 | -32,277 | 0.293 | 1,655 | -6,185 | -4,971 |
| NY AM | 7,495 | -15,007 | -599 | -60,055 | 0.250 | -150 | -6,421 | -14,493 |
| London | 1,768 | -3,809 | 198 | -54,522 | 0.070 | 14 | -1,739 | -2,673 |
| NY PM | 4,629 | -12,121 | -48 | -22,593 | 0.537 | -26 | -3,572 | -4,238 |
| Asia + NY AM (launch set) | 18,329 | -17,237 | 5,055 | -41,510 | 0.415 | 2,099 | -17,237 | -4,596 |
| Asia + NY AM + London | 20,097 | -18,172 | 5,253 | -60,089 | 0.302 | 1,589 | -13,492 | -4,326 |
| all four (Asia + NY AM + London + NY PM) | 24,726 | -17,437 | 5,205 | -69,232 | 0.252 | 1,311 | -11,170 | -3,975 |

## 5. FITTED where available (Asia all-layers joint pick; every other session is still the bare row)

Status of each fitted series: **Asia 5-book**: best joint pick of the truly bare all-layers fit (1 lot `TL3_SR_AS_STKd8106b26ef_BF1_JT57`, 2 lots `TL3_SR_AS_STKd8106b26ef_BF2_JT19`, 4 lots `TL3_SR_AS_STKd8106b26ef_BF4_JT1`; keys in D8_LAYER_KEYS.md / D8_LAYER_DEFAULTS_ASIA.md): label WEAK-BUT-POSITIVE / BEST-AVAILABLE-NOT-PROVEN: walk-forward vs bare 0.60 / 0.85 / 0.91 at 1 / 2 / 4 lots, year bands vs bare RED/RED/RED, search-aware null FAILED (beats 3 of 5 draws, gate 4), 29 of 30 date-shift controls. **NY AM / London / NY PM**: no fitted series yet (NY AM joint, London fit and the NY PM fit are queued or running): their rows below are the BARE rows. The fitted pick is the weak option; the tested-and-proven state is bare (layers OFF).

### L6M: fitted Asia + bare others (1 lot per book)

| combination | basis | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day |
|---|---|---|---|---|---|---|---|---|
| Asia alone | bare (R0) | 10,834 | 3,046 | -9,450 | -4,971 | -6,578 | 11% | 17.2 |
| Asia alone | Asia FITTED (BF1 joint pick) + bare others | 7,645 | 1,827 | -5,422 | -1,892 | -5,259 | 11% | 12.7 |
| Asia + NY AM (launch set) | bare (R0) | 18,329 | 4,037 | -17,237 | -4,596 | -11,311 | 7% | 29.8 |
| Asia + NY AM (launch set) | Asia FITTED (BF1 joint pick) + bare others | 15,140 | 3,703 | -15,639 | -2,328 | -9,187 | 7% | 25.2 |
| Asia + NY AM + London | bare (R0) | 20,097 | 4,086 | -18,172 | -4,326 | -11,448 | 11% | 31.6 |
| Asia + NY AM + London | Asia FITTED (BF1 joint pick) + bare others | 16,908 | 3,458 | -15,019 | -2,967 | -10,783 | 7% | 27.1 |
| all four (Asia + NY AM + London + NY PM) | bare (R0) | 24,726 | 3,658 | -17,437 | -3,975 | -11,109 | 4% | 41.9 |
| all four (Asia + NY AM + London + NY PM) | Asia FITTED (BF1 joint pick) + bare others | 21,537 | 3,760 | -15,316 | -4,780 | -9,472 | 7% | 37.3 |

### L3M: fitted Asia + bare others (1 lot per book)

| combination | basis | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day |
|---|---|---|---|---|---|---|---|---|
| Asia alone | bare (R0) | 10,600 | 3,375 | -9,283 | -1,858 | -6,578 | 8% | 14.2 |
| Asia alone | Asia FITTED (BF1 joint pick) + bare others | 6,646 | 1,715 | -5,422 | -463 | -4,244 | 8% | 11.3 |
| Asia + NY AM (launch set) | bare (R0) | 17,347 | 4,855 | -17,237 | 437 | -11,311 | 0% | 25.0 |
| Asia + NY AM (launch set) | Asia FITTED (BF1 joint pick) + bare others | 13,393 | 3,485 | -13,121 | -2,328 | -9,187 | 8% | 22.1 |
| Asia + NY AM + London | bare (R0) | 18,990 | 4,957 | -18,172 | -497 | -11,311 | 8% | 26.8 |
| Asia + NY AM + London | Asia FITTED (BF1 joint pick) + bare others | 15,036 | 3,236 | -12,436 | -2,967 | -8,591 | 8% | 23.9 |
| all four (Asia + NY AM + London + NY PM) | bare (R0) | 23,330 | 4,384 | -17,437 | 3,734 | -11,109 | 0% | 35.9 |
| all four (Asia + NY AM + London + NY PM) | Asia FITTED (BF1 joint pick) + bare others | 19,376 | 4,007 | -15,316 | -4,780 | -8,835 | 8% | 33.0 |

### ALL: fitted Asia + bare others (1 lot per book)

| combination | basis | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day |
|---|---|---|---|---|---|---|---|---|
| Asia alone | bare (R0) | 3,169 | 6,751 | -33,033 | -16,911 | -12,072 | 36% | 8.7 |
| Asia alone | Asia FITTED (BF1 joint pick) + bare others | 1,761 | 12,755 | -51,773 | -15,120 | -9,151 | 37% | 7.4 |
| Asia + NY AM (launch set) | bare (R0) | 6,340 | 14,460 | -72,611 | -34,774 | -23,178 | 32% | 19.3 |
| Asia + NY AM (launch set) | Asia FITTED (BF1 joint pick) + bare others | 4,933 | 14,939 | -64,951 | -34,683 | -22,380 | 32% | 18.0 |
| Asia + NY AM + London | bare (R0) | 6,794 | 14,422 | -73,373 | -33,603 | -22,512 | 33% | 20.5 |
| Asia + NY AM + London | Asia FITTED (BF1 joint pick) + bare others | 5,386 | 14,928 | -63,050 | -33,512 | -21,715 | 33% | 19.2 |
| all four (Asia + NY AM + London + NY PM) | bare (R0) | 8,897 | 12,631 | -74,669 | -35,385 | -23,202 | 28% | 28.9 |
| all four (Asia + NY AM + London + NY PM) | Asia FITTED (BF1 joint pick) + bare others | 7,489 | 13,054 | -64,345 | -35,295 | -27,678 | 28% | 27.6 |

Fitted at 2 and 4 lots per book (Asia alone, last 6 months, truly bare vs joint pick):

| lots | basis | $/wk | ulcer | max DD | worst wk | worst day | losing wks | trades/day |
|---|---|---|---|---|---|---|---|---|
| 2 | bare | 20,495 | 6,963 | -21,015 | -19,862 | -13,215 | 11% | 17.3 |
| 2 | FITTED JT19 | 9,849 | 2,733 | -8,694 | -3,660 | -7,635 | 7% | 17.0 |
| 4 | bare | 38,613 | 15,687 | -52,366 | -40,859 | -32,739 | 15% | 17.2 |
| 4 | FITTED JT1 | 21,392 | 6,313 | -18,314 | -10,031 | -17,505 | 15% | 14.7 |

## 6. Caveats (one line each)

- DATA END: these series stop at month 202610 (last trade dates listed at the top); the live week td 20261113 and later days are not in the engine sets.
- LONDON: single book, recent-basis FINAL on the complete pool; its exit verdict and the all-layers fit pick are pending (the bare 2- and 4-lot runs are on disk).
- NY PM: the 4-book FINAL is the stack identity STKd893133bd8 (bare stack runs at 1, 2 and 4 lots); its exit verdict and fitted pick are pending; here it is bare.
- R0 vs R1: every D8 row here is truly bare R0; the stack searches' own FINAL pages (ALL_NEW_STACK_*) carry today's D7 account layers (R1) and are NOT these numbers.
- BARE D7 is built from the same raw trigger calls as the D8 books with the live layers removed (1 lot per book, plain 60/60 brackets, O7 40/90); NY PM D7 is K7 alone; compare bare with bare only.
- NO FITTED D7 beside bare D8 and no fitted D8 beside bare D7 anywhere on this page; section 5 compares the fitted Asia row only with the bare D8 rows.
- ALL-MONTHS NOTE: the fitted Asia pick looks worse than bare over all 42 months (higher ulcer and lower $/wk in the all-months table), which is the RED prior-year band of its fit page; it is a recent-window improvement only.
- FILLS: 2- and 4-lot series are real engine runs (size-dependent fills), not multiples of the 1-lot series.
- NEW BOOKS IN THE LIVE FILE: the Asia stack is the first one live; no live P&L is in this page.

_Generated in 12 s._
