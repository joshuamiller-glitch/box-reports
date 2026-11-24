# ASIA_DEPTH_REPEAT_STOPS - how often an Asia book takes 4+ / 6+ full stops in a row on the same side inside one session (order 0250Z, conditional)

Written 2026-11-24 02:47Z by W-LAYERS2 from the STORED fit trades (the truly-bare 5-book stack TL3_ALN_AS_STKd8106b26ef at the 2-LOT basis, set TL3_SR_AS_STKd8106b26ef_BF2_BASE, trades.parquet of every month 2023-04 .. 2026-10 except 2025-11; nothing queued for this table). Book tags: MF1 Lb0e6dfa3, MF2 L385f4f2e.J502, MF3 L92a90948, MF4 L6b373671, MF5 L578701ed (the depth book). Session = the Globex trading day (18:00 ET roll). RUN = consecutive trades of one book inside one session, all of them full-stop losses (exit name Stop, not StackCut, net P&L < 0) and all on the SAME side; any target / time / cut exit, a winner, or a side change ends the run. "run-stop cost" = the sum of the net P&L of the stops inside runs of >= 4; "session P&L" = the whole session P&L of that book on those sessions (the other trades of the night included). 2-lot dollars (6 lots live = x3).

CONDITION of the order: L578701ed is still in the pinned Asia stack (TL3_ALN_AS_STKd8106b26ef = Lb0e6dfa3 + L385f4f2e.J502 + L92a90948 + L6b373671.BRP60 + L578701ed.BRF30_90): YES (the recent-basis re-search on the full pool did not replace the pin). Step (d) (the Asia 2-lot joint) has already run, so the per-book candidates are a TOP-UP screen (see the end of this page).

## MF5 L578701ed.BRF30_90 (the depth book)

| window | sessions | trades | runs >= 4 (sessions) | runs >= 6 | longest run | run-stop cost $ | session P&L of those sessions $ |
|---|---|---|---|---|---|---|---|
| L6M | 131 | 864 | 9 (9) | 0 | 5 | -42725 | -15590 |
| L3M | 65 | 331 | 1 (1) | 0 | 4 | -4204 | -4179 |
| 2023 | 194 | 270 | 0 (0) | 0 | 0 | 0 | 0 |
| 2024 | 259 | 558 | 0 (0) | 0 | 0 | 0 | 0 |
| 2025 | 238 | 807 | 4 (4) | 1 | 6 | -20977 | -10436 |
| 2026 Jan-Apr | 85 | 384 | 2 (2) | 0 | 5 | -10894 | -1312 |

## MF1 Lb0e6dfa3.BRF40_80

| window | sessions | trades | runs >= 4 (sessions) | runs >= 6 | longest run | run-stop cost $ | session P&L of those sessions $ |
|---|---|---|---|---|---|---|---|
| L6M | 131 | 577 | 3 (3) | 0 | 4 | -18518 | -8595 |
| L3M | 65 | 247 | 1 (1) | 0 | 4 | -6324 | -6572 |
| 2023 | 194 | 234 | 1 (1) | 0 | 4 | -6349 | -6349 |
| 2024 | 259 | 450 | 0 (0) | 0 | 0 | 0 | 0 |
| 2025 | 238 | 584 | 1 (1) | 1 | 7 | -11162 | -11149 |
| 2026 Jan-Apr | 85 | 283 | 0 (0) | 0 | 0 | 0 | 0 |

## MF2 L385f4f2e.J502

| window | sessions | trades | runs >= 4 (sessions) | runs >= 6 | longest run | run-stop cost $ | session P&L of those sessions $ |
|---|---|---|---|---|---|---|---|
| L6M | 96 | 168 | 0 (0) | 0 | 0 | 0 | 0 |
| L3M | 49 | 78 | 0 (0) | 0 | 0 | 0 | 0 |
| 2023 | 75 | 76 | 0 (0) | 0 | 0 | 0 | 0 |
| 2024 | 130 | 141 | 0 (0) | 0 | 0 | 0 | 0 |
| 2025 | 152 | 186 | 0 (0) | 0 | 0 | 0 | 0 |
| 2026 Jan-Apr | 58 | 85 | 0 (0) | 0 | 0 | 0 | 0 |

## MF3 L92a90948

| window | sessions | trades | runs >= 4 (sessions) | runs >= 6 | longest run | run-stop cost $ | session P&L of those sessions $ |
|---|---|---|---|---|---|---|---|
| L6M | 123 | 208 | 0 (0) | 0 | 0 | 0 | 0 |
| L3M | 61 | 94 | 0 (0) | 0 | 0 | 0 | 0 |
| 2023 | 87 | 90 | 0 (0) | 0 | 0 | 0 | 0 |
| 2024 | 146 | 162 | 0 (0) | 0 | 0 | 0 | 0 |
| 2025 | 171 | 210 | 0 (0) | 0 | 0 | 0 | 0 |
| 2026 Jan-Apr | 71 | 112 | 0 (0) | 0 | 0 | 0 | 0 |

## MF4 L6b373671.BRP60

| window | sessions | trades | runs >= 4 (sessions) | runs >= 6 | longest run | run-stop cost $ | session P&L of those sessions $ |
|---|---|---|---|---|---|---|---|
| L6M | 120 | 444 | 0 (0) | 0 | 0 | 0 | 0 |
| L3M | 59 | 174 | 0 (0) | 0 | 0 | 0 | 0 |
| 2023 | 133 | 141 | 0 (0) | 0 | 0 | 0 | 0 |
| 2024 | 192 | 265 | 0 (0) | 0 | 0 | 0 | 0 |
| 2025 | 196 | 366 | 0 (0) | 0 | 0 | 0 | 0 |
| 2026 Jan-Apr | 69 | 207 | 0 (0) | 0 | 0 | 0 | 0 |

## Reading (SPEC from the table; trade-level engine, one book at a time)

- The depth book (MF5) is the ONLY Asia member with repeated same-side stop runs in its history except Lb0e6dfa3 (MF1: 5 runs of >= 4 in 3.5 years, one of 7 in 2025); L385f4f2e.J502, L92a90948 and L6b373671 never had a run of 4 in any window.
- MF5: L6M 9 sessions out of 131 (7%) had a run of 4-5 same-side stops (longest 5, none >= 6), the run stops alone cost $42.7k at 2 lots but the whole sessions only -$15.6k (other trades recovered about two thirds); L3M 1 (4 stops, -$4.2k); 2023 and 2024: none; 2025: 4 runs, one of 6; Jan-Apr 2026: 2 runs (longest 5). So the runs are NEW: none in the first 20 months, 4 in 2025, 11 in the last 10 months.
- Tonight (7 long full stops in a row, 15 trades for about -$10,260 on 6 lots) is LONGER than anything in the stored history of the book (longest 6 in 2025, 5 in L6M) = a tail event in length, but the frequency of runs of 4+ in the last 6 months (9 in 131 sessions) says repeated stops on this book are not rare any more.
- Caveat: the engine tape used here is the 2-lot truly-bare run (no layers); a live book with the delivered layers (LK6, NRT2, day loss -6R) may stop a run earlier or later; NY books are not in this table.

## Candidates (top-up screen, queued after this table)
TOP-UP, 2 lots only, standing rules: per-book candidates for each of the 5 Asia books alone: (1) CGB per book n = 2 / 3 / 4 (skip after n same-side losing closes with no new session extreme, governed book = that one book), (2) DLC-by-side per book: after n = 3 / 4 / 5 same-side full stops in a row, pause THAT SIDE of THAT BOOK for 30 / 60 / 120 min ("or until a new session extreme in the trade direction" = not coded: needs the session-extreme feed in the hook, OPEN); reference rows: the delivered pick (BF2_JT19) and the whole-stack CGB2 of JT143. Results (L6M + L3M, $/wk, max DD, worst week, worst day, ulcer, book alone and stack, prior years, walk-forward, null) are appended below when they land.
