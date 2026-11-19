# NEW_BOOK_BEATS_LIVE_NYAM - does a new book beat the live NY AM book(s) in the exact engine? (W-NYENG, order 0210Z), refreshed 2026-11-19 12:15Z

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
| L6a25b155 | long-only | RK7 | +302 / -880 / -1231 / -309 | +329 / -880 / -1231 / +74 | no |
| L6a25b155 | long-only | ADD | -192 / -19 / +225 / -685 | -343 / -19 / +225 / +15 | no |
| L6a25b155 | short-only | RK7 | +649 / -4126 / -2810 / +940 | +874 / -4126 / -2810 / +363 | no |
| L6a25b155 | short-only | ADD | -305 / -125 / +2395 / +786 | -539 / -125 / +2395 / +254 | yes |
| L01811caa | both sides | RK7 | -75 / +620 / +1857 / +1755 | -448 / +2462 / +2114 / +2609 | yes |
| L01811caa | both sides | ADD | -453 / +1209 / +3571 / +1117 | -870 / +4026 / +3571 / +1542 | yes |
| L01811caa | long-only | RK7 | +387 / -1959 / -1162 / +594 | +254 / -1959 / -1162 / +1639 | no |
| L01811caa | long-only | ADD | -112 / -11 / +1210 / +115 | -384 / +521 / +1210 / +843 | yes |
| L01811caa | short-only | RK7 | +721 / -725 / -1929 / +1227 | +988 / -725 / -1929 / +1253 | no |
| L01811caa | short-only | ADD | -252 / +2360 / +2360 / +806 | -452 / +2360 / +2360 / +487 | yes |
| L0f097450 | both sides | RK7 | -58 / -3120 / +1857 / +2291 | -504 / -3120 / +2281 / +2902 | yes |
| L0f097450 | both sides | ADD | -795 / -796 / +5375 / +1691 | -1573 / +95 / +6571 / +2075 | yes |
| L0f097450 | long-only | RK7 | +1429 / -5925 / -8593 / +46 | +1728 / -5925 / -8593 / +1303 | no |
| L0f097450 | long-only | ADD | +615 / -2710 / -5829 / -714 | +607 / -2710 / -5829 / -100 | no |
| L0f097450 | short-only | RK7 | +1364 / -5067 / -5499 / +1324 | +2130 / -5067 / -5499 / +405 | no |
| L0f097450 | short-only | ADD | +277 / -1616 / +1181 / +776 | +470 / -1616 / +1181 / -471 | no |
| L3701b464 | both sides | RK7 | -58 / -3120 / +1857 / +2291 | -504 / -3120 / +2281 / +2902 | yes |
| L3701b464 | both sides | ADD | -795 / -796 / +5375 / +1691 | -1573 / +95 / +6571 / +2075 | yes |
| L3701b464 | long-only | RK7 | +1429 / -5925 / -8593 / +46 | +1728 / -5925 / -8593 / +1303 | no |
| L3701b464 | long-only | ADD | +615 / -2710 / -5829 / -714 | +607 / -2710 / -5829 / -100 | no |
| L3701b464 | short-only | RK7 | +1364 / -5067 / -5499 / +1324 | +2130 / -5067 / -5499 / +405 | no |
| L3701b464 | short-only | ADD | +277 / -1616 / +1181 / +776 | +470 / -1616 / +1181 / -471 | no |

## ENGINE RULE B: prior-year gate, stack WITH the new book vs TODAY stack in the same year (order 1122Z)

**SIGN CONVENTION (explicit).** Rule B columns below are "% WORSE than today s stack" (positive = WORSE, negative = better): ulcer % = (new-ref)/ref; max DD % and worst week % = (ref-new)/|ref|; mean $/wk % = (ref-new)/|ref| (lower mean = positive = worse). The dollar columns elsewhere on this page: "d ulcer negative = better" (lower ulcer), "d worst week +1,631 = the worst week is $1,631 LESS bad than today s stack", "d max DD positive = less deep", "d mean positive = more $/wk". RED > 30% worse, AMBER 15-30%, GREEN otherwise; cell colour = worst of the four metrics; the verdict needs no RED year; a year with no engine rows yet = pending (not fail).

**Rule B = engine (REPLACE / ADD row vs TODAY s stack, same year).** Rule A (screen: bare stream, prior-year weekly R > 30% worse than the cell s own L6M) only orders the queue and is shown in its own column from the shortlist.

| cell | variant | year | ulcer % worse | max DD % worse | worst wk % worse | mean $/wk % worse | colour | persistence (2-wk windows new stack not worse) | rule A (screen, queue order only) |
|---|---|---|---|---|---|---|---|---|---|
| L01811caa | both sides REPLACE K7 | 2023 | -21% | +11% | +24% | -25% | AMBER | 0.47 | see shortlist |
| L01811caa | both sides REPLACE K7 | 2024 | -14% | -4% | +6% | -14% | GREEN | 0.65 | see shortlist |
| L01811caa | both sides REPLACE K7 | 2025 | -12% | -9% | -11% | -8% | GREEN | 0.58 | see shortlist |
| L01811caa | both sides ADD | 2023 | -15% | -2% | +7% | -64% | GREEN | 0.58 | see shortlist |
| L01811caa | both sides ADD | 2024 | -12% | -1% | +3% | -12% | GREEN | 0.65 | see shortlist |
| L01811caa | both sides ADD | 2025 | -17% | -14% | -2% | -17% | GREEN | 0.77 | see shortlist |
| L01811caa | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L01811caa | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | both sides REPLACE K7 | 2023 | -9% | +10% | +44% | +7% | RED | 0.58 | see shortlist |
| L0f097450 | both sides REPLACE K7 | 2024 | -7% | -12% | +2% | -15% | GREEN | 0.62 | see shortlist |
| L0f097450 | both sides REPLACE K7 | 2025 | -17% | -15% | -16% | +2% | GREEN | 0.62 | see shortlist |
| L0f097450 | both sides ADD | 2023 | -12% | +12% | +13% | -30% | GREEN | 0.53 | see shortlist |
| L0f097450 | both sides ADD | 2024 | -3% | -8% | -6% | -16% | GREEN | 0.54 | see shortlist |
| L0f097450 | both sides ADD | 2025 | -22% | -17% | -11% | -11% | GREEN | 0.69 | see shortlist |
| L0f097450 | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L0f097450 | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L0f097450 | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L0f097450 | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L0f097450 | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L0f097450 | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
| L0f097450 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L0f097450 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | both sides ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L3701b464 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | both sides REPLACE K7 | 2023 | -4% | +15% | +5% | -34% | AMBER | 0.58 | see shortlist |
| L6a25b155 | both sides REPLACE K7 | 2024 | +10% | -3% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L6a25b155 | both sides REPLACE K7 | 2025 | +3% | +3% | +0% | -7% | GREEN | 0.58 | see shortlist |
| L6a25b155 | both sides ADD | 2023 | -18% | +3% | -8% | -72% | GREEN | 0.79 | see shortlist |
| L6a25b155 | both sides ADD | 2024 | +12% | -0% | -6% | -20% | GREEN | 0.54 | see shortlist |
| L6a25b155 | both sides ADD | 2025 | -6% | +0% | +12% | -20% | GREEN | 0.65 | see shortlist |
| L6a25b155 | long-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | long-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only REPLACE K7 | 2025 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2023 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2024 | pending | pending | pending | pending | pending | pending | n/a |
| L6a25b155 | short-only ADD | 2025 | pending | pending | pending | pending | pending | pending | n/a |

**Rule B verdict per row:**
- L01811caa both sides REPLACE K7: no RED year
- L01811caa both sides ADD: no RED year
- L01811caa long-only REPLACE K7: pending (no prior-year rows yet)
- L01811caa long-only ADD: pending (no prior-year rows yet)
- L01811caa short-only REPLACE K7: pending (no prior-year rows yet)
- L01811caa short-only ADD: pending (no prior-year rows yet)
- L0f097450 both sides REPLACE K7: RED year
- L0f097450 both sides ADD: no RED year
- L0f097450 long-only REPLACE K7: no RED year
- L0f097450 long-only ADD: no RED year
- L0f097450 short-only REPLACE K7: pending (no prior-year rows yet)
- L0f097450 short-only ADD: pending (no prior-year rows yet)
- L3701b464 both sides REPLACE K7: pending (no prior-year rows yet)
- L3701b464 both sides ADD: pending (no prior-year rows yet)
- L3701b464 long-only REPLACE K7: pending (no prior-year rows yet)
- L3701b464 long-only ADD: pending (no prior-year rows yet)
- L3701b464 short-only REPLACE K7: pending (no prior-year rows yet)
- L3701b464 short-only ADD: pending (no prior-year rows yet)
- L6a25b155 both sides REPLACE K7: no RED year
- L6a25b155 both sides ADD: no RED year
- L6a25b155 long-only REPLACE K7: pending (no prior-year rows yet)
- L6a25b155 long-only ADD: pending (no prior-year rows yet)
- L6a25b155 short-only REPLACE K7: pending (no prior-year rows yet)
- L6a25b155 short-only ADD: pending (no prior-year rows yet)

## D8 gate under the exit-run rule (order 0213Z)
Nothing enters D8 without the EXIT RUN (all 68 recipes, 7 families) on its own entries beside the fixed brackets. Candidate hand-over: autopilot/D8_CANDIDATES.txt (append-only; 187 cells with engine rows listed, one line per live book). Exit run progress: screen stage (68 recipes x params on real entries + null draws) NOT started by W-NYENG on these candidates yet (owner: the exit-screen stage; start order = D8_CANDIDATES.txt engine rank); engine families that cannot run a recipe yet and their build dates: autopilot/D8_EXIT_ENGINE_SUPPORT.md (per-entry stops/targets/time exits run now; opposite-signal exit 11-19 14:00Z; trailing / staged / SAR 11-19 18:00Z; order-flow exits 11-20 12:00Z). Engine cost after the exit screen per candidate: top 3 recipes x (ADD + REPLACE) x (6 last-6-month + 37 prior-year months) + 30 date-shift controls x 6 = 438 set-months; for the 4 candidates that beat a live book now = 1752 set-months = 1.9 h at 928 set-months/h (0.6 h at 2,894/h). D8 SPEC DATE: not before the exit-screen stage and the unbuilt engine families are done; earliest realistic 2026-11-20 12:00Z for the cells that beat a live book today if the exit screen starts by 11-19 06:00Z (cannot be firmer: the screen duration is not measured, the candidate list is still growing).

## All other cells: see the csv (verdict per live book: no / pending)

