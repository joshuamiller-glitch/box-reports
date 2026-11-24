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

## RESULTS of the top-up screen (L6M, 2 lots, 720 rows landed 03:02Z)

Reference rows: BARE base stack L6M ulcer 6963 / max DD -21015 / worst wk -19862 / worst day -13215 / $20495 per wk; DELIVERED PICK BF2_JT19 stack L6M ulcer 2733 / -8694 / -3660 / -7635 / $9849 per wk (the whole-stack CGB2 of JT143 was in the JT143 joint: L6M 1,323 / -6,123 / -2,808 / -3,317 / $4,850 per lot). Each row below = ONE setting on ONE book; stack = the 5-book stack with that setting, book = that book alone (its own daily P&L, zero-filled on the stack days); changes in % vs the reference of the same base (negative ulcer / max DD = better; worst wk: negative = shallower). OK = ulcer lower and max DD / worst wk inside the 15 percent guards.

### The DEPTH BOOK L578701ed (MF5): every candidate that changes anything

| base setting | stack ulcer | stack max DD | stack worst wk | stack worst day | stack $/wk | stack L3M ulcer | book ulcer | book $/wk change | guard |
|---|---|---|---|---|---|---|---|---|---|
| bare CGMF5_2 | +29.0% | +43.9% | -7.2% | +34.6% | -6.7% | +46.5% | +74.1% | -1368 |  |
| bare CGMF5_3 | +1.6% | +0.6% | -6.1% | +42.5% | -4.0% | +0.8% | +3.4% | -815 |  |
| bare CGMF5_4 | -0.2% | +0.0% | +0.0% | +0.0% | -1.0% | +0.0% | +0.7% | -202 | OK |
| bare DSMF5_3_120 | -0.1% | +0.0% | -12.2% | +31.8% | -3.1% | +0.8% | +0.7% | -643 | OK |
| bare DSMF5_3_30 | +2.5% | +0.6% | -1.6% | +42.5% | -4.6% | +1.2% | +5.5% | -947 |  |
| bare DSMF5_3_60 | +6.0% | +10.0% | +16.4% | +42.5% | -2.6% | +0.8% | +10.4% | -530 |  |
| bare DSMF5_4_120 | -0.2% | +0.0% | +0.0% | +0.0% | -0.8% | +0.0% | -0.1% | -157 | OK |
| bare DSMF5_4_30 | -0.2% | +0.0% | +0.0% | +0.0% | -1.0% | +0.0% | +0.7% | -202 | OK |
| bare DSMF5_4_60 | -0.2% | +0.0% | +0.0% | +0.0% | -0.8% | +0.0% | -0.1% | -157 | OK |
| JT19 CGMF5_2 | +15.0% | +14.4% | +6.0% | +0.0% | -5.8% | +68.8% | +91.7% | -576 |  |
| JT19 CGMF5_3 | +2.0% | +1.9% | +0.0% | +0.0% | -1.8% | +4.6% | +4.1% | -250 |  |
| JT19 CGMF5_4 | +3.2% | +7.0% | +0.0% | +0.0% | -2.1% | +0.2% | +0.7% | -203 |  |
| JT19 DSMF5_3_120 | -0.4% | +1.9% | +0.0% | +0.0% | -1.5% | +0.1% | +2.3% | -193 | OK |
| JT19 DSMF5_3_30 | +0.0% | +0.0% | +0.0% | +0.0% | -1.0% | +0.0% | +1.6% | -132 |  |
| JT19 DSMF5_3_60 | -0.6% | +1.4% | +0.0% | +0.0% | -1.1% | +0.1% | +2.5% | -178 | OK |
| JT19 DSMF5_4_120 | +0.1% | +0.1% | +0.0% | +0.0% | -2.5% | +0.2% | +1.8% | -243 |  |
| JT19 DSMF5_4_30 | +3.2% | +7.0% | +0.0% | +0.0% | -2.1% | +0.2% | +0.7% | -203 |  |
| JT19 DSMF5_4_60 | +0.1% | +0.1% | +0.0% | +0.0% | -2.8% | +0.2% | +4.3% | -282 |  |

### Best candidates on any book (stack ulcer lower inside the guards)

| base setting | stack ulcer | stack max DD | stack worst wk | stack worst day | stack $/wk | stack L3M ulcer | book ulcer | book $/wk change | guard |
|---|---|---|---|---|---|---|---|---|---|
| JT19 DSMF1_3_30 | -2.3% | -7.4% | -21.6% | +0.0% | +0.3% | +0.0% | -1.3% | +29 | OK |
| bare CGMF1_2 | -2.2% | -5.5% | +0.0% | -0.4% | +2.1% | -2.0% | -10.5% | +437 | OK |
| bare CGMF4_2 | -1.2% | +0.0% | -12.2% | +0.0% | +0.4% | +0.0% | -4.1% | +89 | OK |
| JT19 DSMF5_3_60 | -0.6% | +1.4% | +0.0% | +0.0% | -1.1% | +0.1% | +2.5% | -178 | OK |
| JT19 DSMF5_3_120 | -0.4% | +1.9% | +0.0% | +0.0% | -1.5% | +0.1% | +2.3% | -193 | OK |

### VERDICT (drawdown first, pick on recent, 2 lots)

1. THE DEPTH BOOK L578701ed: NO per-book candidate helps. Skip after n same-side losses (CGB n = 2 / 3 / 4) and the per-side pause after 3 / 4 / 5 stops (30 / 60 / 120 min) change the 5-book stack ulcer by -0.6 to +29 percent (n = 2 is much WORSE: +29 percent on the bare base, +15 percent on the pick), and the book ALONE gets worse ulcer in nearly every cell and gives up $150-$1,400 per week; n = 5 never fires in L6M. Reason (from the trade list): after a run of same-side stops the book usually wins back inside the night (the 9 L6M runs cost -$42.7k in stops but the sessions only -$15.6k): stopping early forfeits the recovery. So nothing is delivered for L578701ed: it keeps its delivered settings; tonight's 7-stop run is a tail event and the L6M history shows no cure for it.
2. Other books: J502 (MF2), L92a90948 (MF3), L6b373671 (MF4) have no runs of 4 in their history: every n = 3 / 4 / 5 row reads +0.0 percent (the rule never fires). The only recurring signal is on Lb0e6dfa3 (MF1): CGB n = 2 gives stack ulcer -2.2 percent on the bare base and -6.8 percent on the pick (max DD -5.5 / -6.6 percent, dollars +2.1 / +2.5 percent; worst week 28.6 percent deeper on the pick) and the 30-min pause after 3 stops -2.3 percent on the pick with the worst week 21.6 percent shallower: SMALL, not tested on prior years yet: prior-year rows for those three (108 rows) are queued; walk-forward / null only if they hold.

No setting is delivered from this screen yet. Exact parameters of the candidates: CG = c_gov rule {sess [0,1,3,4], loss_same_ge n, noevid 1, act skip} with gov_book = [that book]; DS = dl_hooks consec_side {N, pause minutes} on that book (counter = consecutive Stop-named losing closes on the same side; any other close or a side change resets it; the pause blocks only that side of that book; it lifts at the pause end or the 18:00 ET roll).
