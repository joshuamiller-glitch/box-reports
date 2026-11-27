# TEST 12: CAN A QUALIFIED BOOK REPLACE A LIVE BOOK AND LOWER THE MIX MAX DRAWDOWN (walk-forward, replace never add)

Generated 2026-11-27 02:35Z UTC by /mnt/l2/l2vast/_test12/code/t12_eval.py (W-TEST12). Progress: 0 of 52 forward periods have finished exact rows (221 set-months queued, class 2 right behind Q0).

## ANSWER FIRST (drawdown first; U = unswapped live mix, S = swapped; exact engine, live layers and live lots; PASS per session = shallower forward DD in >= 8 of 12 periods AND forward $/wk not lower by more than 10%)

- Asia: PENDING (0 of 12 periods finished). L3M: n/a (rows not finished). L6M: n/a (rows not finished). All 12: n/a (rows not finished)
- NY AM: PENDING (0 of 12 periods finished). L3M: n/a (rows not finished). L6M: n/a (rows not finished). All 12: n/a (rows not finished)
- NY PM: PENDING (0 of 12 periods finished). L3M: n/a (rows not finished). L6M: n/a (rows not finished). All 12: n/a (rows not finished)
- London: PENDING (0 of 12 periods finished). L3M: n/a (rows not finished). L6M: n/a (rows not finished). All 12: n/a (rows not finished)

## HOW IT WAS DONE (read before trusting any number)

- DATA TO DATE ONLY. Dates = the Test 5 re-qualify dates, grid weeks 26,39,...,169 (Monday-start weeks from 2023-04-03; week 26 = 2023-10-02, week 169 = 2026-06-29), 12 forward periods of 13 weeks each; a 13th 4-week tail (week 182 to 2026-10-25) is listed apart and is NOT in the 12. L3M = the last full period (wk 169-181, Jun 29 to Sep 27 2026), L6M = the last two (wk 156-181). The four Nov 2025 weeks have no engine months (202511 is missing) and are left out of every table.
- CANDIDATES at a date: the cells the Test 5 PRIMARY rule (N>=100, t>=4, trailing 26 weeks profitable, 13-week re-qualify) held at that date (walk5_s*.pkl log, r=5), bare R0 events (one lot, rescaled to the slot's live lots), all book types incl. two-sided level books. Candidate cells are chosen on the same weeks their t-stat is computed from, so their PAST looks very good by construction: the selection step below therefore sees inflated candidate pasts; the forward period is the only honest test.
- QUICK-SCREEN MIX (selection only): swapped weekly mix = EXACT weekly $ of the Q3 leave-one-out set for that slot (live layers and the other books' hooks included, from exact engine months) + candidate grid weekly points x $20 x the slot's live lots (grid cost in; no per-book hooks; no account layers or size nonlinearity on the candidate). Weekly-point max DD and mean $/wk over valid weeks before the date. Unswapped = exact live mix on the same weeks. PRIMARY choice: the single (slot, candidate) swap with the shallowest quick-screen max DD among those with income to date >= 90% of unswapped and DD at least 10% shallower; if none, no swap (none of the 52 dates ended with no swap).
- EXACT ROWS for the chosen swaps only: live set with the slot's events replaced by the candidate's at the same lots, the slot's per-book hooks (zone, scratch/flat, take/lock, shave) stripped, account layers (STK caps, c_gov, daily-loss, sizer) kept on the new book; sets TL3_SR_<S>_<stack>_T12S<slot>_<cell>. Forward months only (engine rows are independent set-months and the unswapped live mix exists for all 42), not 42 months; forward stats are daily on the exact calendar, cut to the forward weeks.
- HINDSIGHT CAVEATS: the live books themselves were picked on the same weeks (including the forward ones), so the unswapped mix is flattered in every period and a swap is judged against a mix that already knows the future; the Asia 0.5x fade cell was chosen as lower median of cells held at ANY date (Q6), not point in time. Hooks on the candidate are not fitted (bare). Candidate set per date uses re-qualify-date holds, a book can be picked several dates in a row.

## Asia

Live mix TL3_SR_AS_STKd8da2eb47b_FSff6_PICKC (lots 6/6/6/6). Replaced most often: MF3 x9, MF1 x3, MF2 x1. Kinds of replacing book (module, bracket, side): manual_macd fixed90/30 long x2; levels_prior_day sym30u both x1; levels_prior_day asym15u/30u both x1; levels_prior_day sym15u both x1; levels_prior_day sym30u long x1; levels_fib60 fixed120/60 long x1.

| date wk (start) | replaced | candidate (module bracket side) | quick-screen at date: DD to date U -> swap, inc U -> swap | FWD max DD U | FWD max DD swap | d DD (+ shallower) | worst wk U | worst wk swap | $/wk U | $/wk swap | $/wk+DD with 0.5x fade |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-29 | MF3 (6L) | bands_envelope fixed30/90 long | -67,617 -> -35,247, 4,396 -> 5,172 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2026-03-30 | MF3 (6L) | bands_atrchan plain60/60 short | -67,617 -> -34,325, 3,015 -> 3,517 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-12-29 | MF3 (6L) | levels_profile_nodes fixed120/60 both | -67,617 -> -31,113, 2,856 -> 4,996 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-09-29 | MF3 (6L) | manual_macd fixed90/30 long | -67,617 -> -25,200, 2,883 -> 4,505 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-06-30 | MF3 (6L) | manual_macd fixed90/30 long | -67,617 -> -25,200, 3,061 -> 4,763 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-03-31 | MF3 (6L) | book_cancel fixed90/90 both | -58,590 -> -21,102, 2,446 -> 5,944 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-12-30 | MF2 (6L) | momentum_roc fixed90/30 long | -58,590 -> -26,801, 2,671 -> 3,695 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-09-30 | MF3 (6L) | levels_fib60 fixed120/60 long | -27,665 -> -13,390, 3,304 -> 4,163 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-07-01 | MF3 (6L) | levels_prior_day sym30u long | -27,665 -> -11,198, 2,547 -> 5,423 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-04-01 | MF1 (6L) | levels_prior_day sym15u both | -25,648 -> -11,274, 3,057 -> 5,597 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-01-01 | MF1 (6L) | levels_prior_day asym15u/30u both | -25,648 -> -8,374, 2,020 -> 5,102 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2023-10-02 | MF1 (6L) | levels_prior_day sym30u both | -25,648 -> -6,745, 385 -> 4,803 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2026-09-28 (4wk tail) | MF3 (6L) | bands_envelope fixed30/90 long | -67,617 -> -35,247, 4,832 -> 5,719 | n/a | n/a | n/a | n/a | n/a | n/a | n/a | n/a |

Reference row, Asia only, the same swaps with the Q6 0.5x fade (cell Wf8e3f7ad, 3 lots) added: n/a (rows not finished)

## NY AM

Live mix TL3_SR_NY_STKd8cd0279ff_FSff6_PICKC (lots 6/6/6/6/3/6/2/2/3). Replaced most often: MF3 x6, MF4 x6, MF2 x1. Kinds of replacing book (module, bracket, side): levels_vwap fixed80/40 both x2; book_ofi fixed80/40 both x1; levels_vwap fixed80/40 long x1; levels_vwap asym10u/20u both x1; levels_piv_floor fixed30/90 both x1; levels_piv_floor fixed60/120 both x1.

| date wk (start) | replaced | candidate (module bracket side) | quick-screen at date: DD to date U -> swap, inc U -> swap | FWD max DD U | FWD max DD swap | d DD (+ shallower) | worst wk U | worst wk swap | $/wk U | $/wk swap |
|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-29 | MF4 (6L) | barnative_run sym15u long | -163,622 -> -90,551, 15,757 -> 17,138 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2026-03-30 | MF4 (6L) | confluence_user sym15u short | -143,938 -> -94,826, 13,053 -> 14,709 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-12-29 | MF4 (6L) | barnative_profile plain60/60 long | -143,938 -> -82,684, 13,551 -> 15,604 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-09-29 | MF3 (6L) | levels_channel sym8u both | -143,938 -> -90,764, 13,599 -> 20,764 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-06-30 | MF4 (6L) | structure_level fixed60/120 long | -143,938 -> -87,358, 12,738 -> 15,070 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-03-31 | MF3 (6L) | levels_piv_floor fixed60/120 both | -143,938 -> -76,636, 12,144 -> 19,541 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-12-30 | MF3 (6L) | levels_piv_floor fixed30/90 both | -143,938 -> -70,479, 9,871 -> 18,050 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-09-30 | MF2 (6L) | levels_vwap asym10u/20u both | -143,938 -> -59,926, 9,530 -> 17,351 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-07-01 | MF4 (6L) | levels_vwap fixed80/40 both | -143,938 -> -51,995, 5,667 -> 13,385 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-04-01 | MF3 (6L) | levels_vwap fixed80/40 both | -140,296 -> -44,047, 5,878 -> 15,425 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-01-01 | MF3 (6L) | levels_vwap fixed80/40 long | -131,661 -> -47,793, 9,630 -> 15,185 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2023-10-02 | MF3 (6L) | book_ofi fixed80/40 both | -131,661 -> -37,622, 10,914 -> 18,880 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2026-09-28 (4wk tail) | MF4 (6L) | levels_piv_floor fixed60/120 both | -163,622 -> -99,248, 19,021 -> 20,947 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |

## NY PM

Live mix TL3_SR_NP_STKd893133bd8_FSf46_PICKC (lots 6/6/6/6). Replaced most often: MF4 x8, MF1 x5. Kinds of replacing book (module, bracket, side): book_cancel fixed90/90 both x1; levels_fvg5 fixed45/45 both x1; levels_trendline sym8u both x1; levels_fvg15 fixed40/80 long x1; levels_fvg5 asym20u/10u long x1; levels_piv_floor plain60/60 both x1.

| date wk (start) | replaced | candidate (module bracket side) | quick-screen at date: DD to date U -> swap, inc U -> swap | FWD max DD U | FWD max DD swap | d DD (+ shallower) | worst wk U | worst wk swap | $/wk U | $/wk swap |
|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-29 | MF4 (6L) | levels_week_month plain60/60 both | -126,828 -> -50,018, 5,368 -> 8,452 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2026-03-30 | MF4 (6L) | levels_fibr_ib fixed90/30 both | -126,828 -> -58,050, 4,665 -> 6,938 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-12-29 | MF4 (6L) | levels_fvg5 fixed30/90 both | -126,828 -> -50,273, 4,820 -> 9,353 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-09-29 | MF4 (6L) | levels_trendline fixed90/90 both | -126,828 -> -56,487, 5,658 -> 13,492 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-06-30 | MF4 (6L) | levels_trendline fixed120/60 both | -126,828 -> -49,156, 5,620 -> 14,001 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-03-31 | MF4 (6L) | levels_sdx3 plain60/60 both | -126,828 -> -40,773, 5,240 -> 8,176 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-12-30 | MF1 (6L) | levels_piv_floor plain60/60 both | -126,828 -> -40,996, 3,603 -> 11,343 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-09-30 | MF4 (6L) | levels_fvg5 asym20u/10u long | -43,608 -> -22,355, 5,444 -> 8,672 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-07-01 | MF1 (6L) | levels_fvg15 fixed40/80 long | -26,975 -> -19,579, 6,210 -> 10,441 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-04-01 | MF1 (6L) | levels_trendline sym8u both | -26,975 -> -16,543, 4,977 -> 12,910 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-01-01 | MF1 (6L) | levels_fvg5 fixed45/45 both | -26,975 -> -13,658, 4,965 -> 10,348 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2023-10-02 | MF1 (6L) | book_cancel fixed90/90 both | -26,975 -> -2,345, 4,054 -> 16,052 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2026-09-28 (4wk tail) | MF4 (6L) | levels_fibr_ib fixed90/30 both | -126,828 -> -58,050, 5,877 -> 7,546 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |

## London

Live mix TL3_SR_LO_STKd8w42lo_FSffb8_BARE (lots 8/4/2). Replaced most often: MF1 x7, MF2 x6. Kinds of replacing book (module, bracket, side): tape_delta sym15u both x2; levels_fib5 asym10u/20u both x1; bands_atrchan fixed90/30 both x1; levels_fvg15 sym8u short x1; levels_swsr15 fixed90/30 both x1; xmarket_nkd asym15u/30u long x1.

| date wk (start) | replaced | candidate (module bracket side) | quick-screen at date: DD to date U -> swap, inc U -> swap | FWD max DD U | FWD max DD swap | d DD (+ shallower) | worst wk U | worst wk swap | $/wk U | $/wk swap |
|---|---|---|---|---|---|---|---|---|---|---|
| 2026-06-29 | MF2 (4L) | levels_piv_floor fixed120/60 both | -213,180 -> -93,323, 3,437 -> 5,930 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2026-03-30 | MF1 (8L) | tape_block sym15u long | -213,180 -> -100,146, 2,233 -> 3,053 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-12-29 | MF2 (4L) | tape_run fixed90/30 both | -213,180 -> -79,563, 2,895 -> 4,702 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-09-29 | MF2 (4L) | levels_fibr_or sym15u both | -213,180 -> -71,884, 2,020 -> 3,939 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-06-30 | MF2 (4L) | tape_delta sym15u both | -209,916 -> -62,619, 2,293 -> 4,758 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2025-03-31 | MF1 (8L) | tape_delta sym15u both | -102,566 -> -38,721, 3,176 -> 5,971 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-12-30 | MF2 (4L) | levels_fib5 fixed45/45 both | -65,388 -> -41,796, 3,990 -> 7,135 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-09-30 | MF1 (8L) | xmarket_nkd asym15u/30u long | -65,388 -> -44,310, 3,979 -> 6,549 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-07-01 | MF1 (8L) | levels_swsr15 fixed90/30 both | -65,388 -> -32,638, 4,498 -> 8,192 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-04-01 | MF1 (8L) | levels_fvg15 sym8u short | -65,388 -> -20,365, 3,465 -> 5,662 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2024-01-01 | MF1 (8L) | bands_atrchan fixed90/30 both | -65,388 -> -13,522, 2,789 -> 11,257 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2023-10-02 | MF1 (8L) | levels_fib5 asym10u/20u both | -65,388 -> -4,950, 828 -> 9,876 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
| 2026-09-28 (4wk tail) | MF2 (4L) | levels_trendline fixed90/90 long | -213,180 -> -101,789, 4,531 -> 6,330 | n/a | n/a | n/a | n/a | n/a | n/a | n/a |
