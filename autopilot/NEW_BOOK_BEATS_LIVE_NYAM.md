# NEW_BOOK_BEATS_LIVE_NYAM - does a new book beat the live NY AM book(s) in the exact engine? (W-NYENG, order 0210Z), refreshed 2026-11-19 10:45Z

**vs TODAY's stack (JL3, today's DAY-DONE); provisional until Asia and London are decided; label BETTER = calibration pending, NOT calibrated.** Rule: REPLACE row (the new book switched on, the named live book's NY AM entries switched OFF) beats that live book when, DRAWDOWN FIRST, the stack ulcer change is < 0 AND the mean $/week change is >= 0 on BOTH the last 6 and last 3 months (engine base lots, $4.84 RT proxy); then prior years must show no RED (> 30% worse on ulcer / max DD / mean) where run; persistence > 0.60 and the 30 date-shift controls are still PENDING for every row below (shown as counts). Bare R0/R3 only orders the engine queue. Live books of this session: K7, P7, M7, H7. verdict yes / no / pending (not run or months not landed). Sorted by the best last-6-month stack-ulcer change of any REPLACE row (most negative first). Full table of every cell: /mnt/l2/l2vast/_nye/beats_NYAM.csv.

**Counts:** cells with any engine row 187; cells with a finished REPLACE verdict (L6M+L3M landed) 122; cells that beat at least one live book on L6M+L3M (BETTER, calibration pending) 4.

## Cells that beat a live book (yes), drawdown first
| rank | cell | REPLACE K7 | REPLACE P7 | REPLACE M7 | REPLACE H7 | ADD | prior years run | controls |
|---|---|---|---|---|---|---|---|---|
| 178 | drb_2000 / book_ofi.follow_native {"L": 3600, "z": 2.0} / sym15u / both | yes (L6M du -178 dm +919 | L3M du -620 dm +1301) | not run | not run | not run | yes (L6M du -436 dm +460 | L3M du -876 dm +936) | K7:3,P7:0,M7:0,H7:0 | 0 of 30 |
| 107 | tick_8000 / levels_open_range.break_native {"n": 3, "k": 0.25} / plain60/60 / both | yes (L6M du -75 dm +1755 | L3M du -448 dm +2609) | not run | not run | not run | yes (L6M du -453 dm +1117 | L3M du -870 dm +1542) | K7:3,P7:0,M7:0,H7:0 | 0 of 30 |
| 76 | wrenko_20 / levels_profile_va.break_native {"n": 1, "k": 0.0} / sym15u / long | yes (L6M du -58 dm +2291 | L3M du -504 dm +2902) | not run | not run | not run | yes (L6M du -795 dm +1691 | L3M du -1573 dm +2075) | K7:3,P7:0,M7:0,H7:0 | 0 of 30 |
| 229 | wrenko_20 / levels_profile_va.break {"n": 1, "k": 0.0} / sym15u / long | yes (L6M du -58 dm +2291 | L3M du -504 dm +2902) | not run | not run | not run | yes (L6M du -795 dm +1691 | L3M du -1573 dm +2075) | K7:0,P7:0,M7:0,H7:0 | 0 of 30 |

## Both-side / long-only / short-only rows side by side (order 1014Z; both-side sets are VALID engine results for the both-side book; LO / SO = mode-correct sets, engine-tested separately; replace K7 and ADD; vs the live stack, engine base lots; d = change vs JL3, ulcer first)
| cell (id) | row | variant | L6M d ulcer / d worst wk / d max DD / d mean $/wk | L3M d ulcer / d worst / d max DD / d mean | beats K7 (yes/no/pending) |
|---|---|---|---|---|---|
| L6a25b155 | both sides | RK7 | -178 / -1005 / +1164 / +919 | -620 / -1005 / +1164 / +1301 | yes |
| L6a25b155 | both sides | ADD | -436 / -144 / +2621 / +460 | -876 / -144 / +2621 / +936 | yes |
| L01811caa | both sides | RK7 | -75 / +620 / +1857 / +1755 | -448 / +2462 / +2114 / +2609 | yes |
| L01811caa | both sides | ADD | -453 / +1209 / +3571 / +1117 | -870 / +4026 / +3571 / +1542 | yes |
| L0f097450 | both sides | RK7 | -58 / -3120 / +1857 / +2291 | -504 / -3120 / +2281 / +2902 | yes |
| L0f097450 | both sides | ADD | -795 / -796 / +5375 / +1691 | -1573 / +95 / +6571 / +2075 | yes |
| L0f097450 | long-only | RK7 | +1429 / -5925 / -8593 / +46 | +1728 / -5925 / -8593 / +1303 | no |
| L0f097450 | long-only | ADD | +615 / -2710 / -5829 / -714 | +607 / -2710 / -5829 / -100 | no |
| L0f097450 (long) | short-only | RK7 | not run yet | | |
| L0f097450 (long) | short-only | ADD | not run yet | | |
| L3701b464 | both sides | RK7 | -58 / -3120 / +1857 / +2291 | -504 / -3120 / +2281 / +2902 | yes |
| L3701b464 | both sides | ADD | -795 / -796 / +5375 / +1691 | -1573 / +95 / +6571 / +2075 | yes |
| L3701b464 | long-only | RK7 | +nan / +nan / +nan / +nan | +1728 / -5925 / -8593 / +1303 | pending |
| L3701b464 | long-only | ADD | +615 / -2710 / -5829 / -714 | +607 / -2710 / -5829 / -100 | no |
| L3701b464 (long) | short-only | RK7 | not run yet | | |
| L3701b464 (long) | short-only | ADD | not run yet | | |

## D8 gate under the exit-run rule (order 0213Z)
Nothing enters D8 without the EXIT RUN (all 68 recipes, 7 families) on its own entries beside the fixed brackets. Candidate hand-over: autopilot/D8_CANDIDATES.txt (append-only; 187 cells with engine rows listed, one line per live book). Exit run progress: screen stage (68 recipes x params on real entries + null draws) NOT started by W-NYENG on these candidates yet (owner: the exit-screen stage; start order = D8_CANDIDATES.txt engine rank); engine families that cannot run a recipe yet and their build dates: autopilot/D8_EXIT_ENGINE_SUPPORT.md (per-entry stops/targets/time exits run now; opposite-signal exit 11-19 14:00Z; trailing / staged / SAR 11-19 18:00Z; order-flow exits 11-20 12:00Z). Engine cost after the exit screen per candidate: top 3 recipes x (ADD + REPLACE) x (6 last-6-month + 37 prior-year months) + 30 date-shift controls x 6 = 438 set-months; for the 4 candidates that beat a live book now = 1752 set-months = 1.9 h at 928 set-months/h (0.6 h at 2,894/h). D8 SPEC DATE: not before the exit-screen stage and the unbuilt engine families are done; earliest realistic 2026-11-20 12:00Z for the cells that beat a live book today if the exit screen starts by 11-19 06:00Z (cannot be firmer: the screen duration is not measured, the candidate list is still growing).

## All other cells: see the csv (verdict per live book: no / pending)

