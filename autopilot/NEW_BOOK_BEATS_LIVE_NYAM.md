# NEW_BOOK_BEATS_LIVE_NYAM - does a new book beat the live NY AM book(s) in the exact engine? (W-NYENG, order 0210Z), refreshed 2026-11-19 13:30Z

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

## Date-shift controls (30 per row; L6M; vs TODAY stack; engine base lots)
Controls = the same events moved +-7..105 days (same weekday). Real beats a control when its d mean $/wk is higher AND its d ulcer lower. Sign: d ulcer negative = better; d mean positive = more $/wk.

| cell | variant | real d mean / d ulcer | controls landed (of 30) | controls beaten on mean | beaten on ulcer | beaten on both | best control d mean / d ulcer |
|---|---|---|---|---|---|---|---|
| L01811caa | RK7 | +1755 / -75 | 0 | pending | | | |
| L01811caa | ADD | +1117 / -453 | 0 | pending | | | |
| L0f097450 | RK7 | +2291 / -58 | 0 | pending | | | |
| L0f097450 | ADD | +1691 / -795 | 0 | pending | | | |
| L6a25b155 | RK7 | +919 / -178 | 0 | pending | | | |
| L6a25b155 | ADD | +460 / -436 | 0 | pending | | | |

## Candidates under the persistence >= 0.58 gate and the ADD-vs-REPLACE rule (order 1324Z)

Rules: REPLACE is the default. ADD only when (a) the whole stack is better with ADD than with REPLACE (ulcer first, then $/wk; last 6 months with last 3 months; no RED prior year) AND (b) removing K7 from the ADD stack makes L6M and L3M worse. REPLACE = the ADD stack with K7 switched off in the NY AM session, so the ADD stack WITHOUT K7 already exists as the REPLACE row: NO new "minus K7" engine set is needed (a K7-off-in-every-session set would only matter for K7's other sessions, which these rows leave untouched). Persistence = share of non-overlapping 2-week windows where the new stack is not worse than today's, POOLED over every month the set has run (last 6 months + prior years). Rule B colours from ny_ruleb (RED > 30% worse in a prior year). Stack columns are the whole stack (ulcer / max DD / worst week / mean $ per week, engine base lots, $4.84).

| cell | stack | window | ulcer | max DD | worst wk | mean $/wk | rule-B colour (worst %) |
|---|---|---|---|---|---|---|---|
| L01811caa | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L01811caa | REPLACE | L6M | 9342 | -29253 | -15108 | +20510 | n/a (recent window) (-1%) |
| L01811caa | ADD | L6M | 8963 | -27538 | -14519 | +19873 | n/a (recent window) (-5%) |
| L01811caa | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L01811caa | REPLACE | L3M | 10587 | -28995 | -13266 | +18707 | n/a (recent window) (-4%) |
| L01811caa | ADD | L3M | 10165 | -27538 | -11702 | +17640 | n/a (recent window) (-8%) |
| L01811caa | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L01811caa | REPLACE | Y2025 | 29382 | -83155 | -34691 | +7360 | GREEN (-8%) |
| L01811caa | ADD | Y2025 | 27815 | -78940 | -38025 | +7984 | GREEN (-2%) |
| L01811caa | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L01811caa | REPLACE | Y2024 | 24716 | -69388 | -39713 | +5169 | GREEN (+6%) |
| L01811caa | ADD | Y2024 | 25450 | -71363 | -38560 | +5073 | GREEN (+3%) |
| L01811caa | TODAY (JL3) | Y2023 | 18908 | -41848 | -17538 | +1797 | - |
| L01811caa | REPLACE | Y2023 | 15029 | -46397 | -21702 | +2254 | AMBER (+24%) |
| L01811caa | ADD | Y2023 | 16062 | -40960 | -18785 | +2944 | GREEN (+7%) |
| L6a25b155 | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L6a25b155 | REPLACE | L6M | 9238 | -29945 | -16733 | +19675 | n/a (recent window) (+6%) |
| L6a25b155 | ADD | L6M | 8981 | -28489 | -15872 | +19216 | n/a (recent window) (+1%) |
| L6a25b155 | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L6a25b155 | REPLACE | L3M | 10415 | -29945 | -16733 | +17400 | n/a (recent window) (+6%) |
| L6a25b155 | ADD | L3M | 10159 | -28489 | -15872 | +17034 | n/a (recent window) (+1%) |
| L6a25b155 | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L6a25b155 | REPLACE | Y2025 | 34575 | -93892 | -39081 | +7356 | GREEN (+3%) |
| L6a25b155 | ADD | Y2025 | 31437 | -91723 | -43606 | +8231 | GREEN (+12%) |
| L6a25b155 | TODAY (JL3) | Y2024 | 28814 | -72026 | -37355 | +4549 | - |
| L6a25b155 | REPLACE | Y2024 | 31815 | -69700 | -36113 | +5300 | GREEN (+10%) |
| L6a25b155 | ADD | Y2024 | 32304 | -71936 | -34960 | +5448 | GREEN (+12%) |
| L6a25b155 | TODAY (JL3) | Y2023 | 18908 | -41848 | -17538 | +1797 | - |
| L6a25b155 | REPLACE | Y2023 | 18087 | -48220 | -18408 | +2404 | AMBER (+15%) |
| L6a25b155 | ADD | Y2023 | 15491 | -42932 | -16215 | +3088 | GREEN (+3%) |
| L0f097450 | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L0f097450 | REPLACE | L6M | 9358 | -29253 | -18848 | +21047 | n/a (recent window) (+20%) |
| L0f097450 | ADD | L6M | 8621 | -25734 | -16524 | +20446 | n/a (recent window) (+5%) |
| L0f097450 | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L0f097450 | REPLACE | L3M | 10531 | -28828 | -18848 | +19000 | n/a (recent window) (+20%) |
| L0f097450 | ADD | L3M | 9463 | -24538 | -15633 | +18174 | n/a (recent window) (-1%) |
| L0f097450 | TODAY (JL3) | Y2025 | 33572 | -91441 | -38896 | +6846 | - |
| L0f097450 | REPLACE | Y2025 | 27735 | -77634 | -32511 | +6709 | GREEN (+2%) |
| L0f097450 | ADD | Y2025 | 26308 | -76028 | -34457 | +7579 | GREEN (-11%) |
| L0f097450 | TODAY (JL3) | Y2024 | 28856 | -72026 | -37355 | +4549 | - |
| L0f097450 | REPLACE | Y2024 | 26900 | -63077 | -38237 | +5219 | GREEN (+2%) |
| L0f097450 | ADD | Y2024 | 28023 | -66257 | -35122 | +5297 | GREEN (-3%) |
| L0f097450 | TODAY (JL3) | Y2023 | 19039 | -41848 | -17538 | +1797 | - |
| L0f097450 | REPLACE | Y2023 | 17341 | -46048 | -25258 | +1675 | RED (+44%) |
| L0f097450 | ADD | Y2023 | 16744 | -46713 | -19840 | +2334 | GREEN (+13%) |
| L3701b464 | TODAY (JL3) | L6M | 9416 | -31109 | -15728 | +18755 | - |
| L3701b464 | REPLACE | L6M | 9358 | -29253 | -18848 | +21047 | n/a (recent window) (+20%) |
| L3701b464 | ADD | L6M | 8621 | -25734 | -16524 | +20446 | n/a (recent window) (+5%) |
| L3701b464 | TODAY (JL3) | L3M | 11035 | -31109 | -15728 | +16098 | - |
| L3701b464 | REPLACE | L3M | 10531 | -28828 | -18848 | +19000 | n/a (recent window) (+20%) |
| L3701b464 | ADD | L3M | 9463 | -24538 | -15633 | +18174 | n/a (recent window) (-1%) |
| L3701b464 | all | Y2025 | pending | | | | |
| L3701b464 | all | Y2024 | pending | | | | |
| L3701b464 | all | Y2023 | pending | | | | |

| cell | pooled persistence REPLACE (months) | pooled persistence ADD (months) | RED years REPLACE / ADD | PICK | what is still needed |
|---|---|---|---|---|---|
| L01811caa | 0.59 (43 mo) | 0.60 (43 mo) | none / none | **ADD** (ADD better than REPLACE on L6M+L3M, K7 contributes) | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L6a25b155 | 0.59 (43 mo) | 0.65 (43 mo) | none / none | **ADD** (ADD better than REPLACE on L6M+L3M, K7 contributes) | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L0f097450 | 0.55 (43 mo) | 0.58 (43 mo) | Y2023 / none | **ADD** (ADD stack better than REPLACE on L6M and L3M (so K7 contributes), no RED year, persistence 0.58 >= 0.58) | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |
| L3701b464 | 0.54 (6 mo) | 0.69 (6 mo) | none / none | **none yet** (REPLACE: prior years pending (0/3); persistence 0.54 < 0.58 | ADD: prior years pending (0/3)) | 30 date-shift controls (queued; scored in the controls section), layers one at a time then joint (not started: ~1,068 set-months, layer-set builder manual), exit run 68 recipes + engine exit rows (families unbuilt) |

**Candidates passing recent months + no RED year + persistence >= 0.58:** L01811caa (ADD), L6a25b155 (ADD), L0f097450 (ADD).
**Dates:** 30 controls: queued at the front (landing as the fleet reaches them, ~06 hours at 2,000 sm/h); layers + exit run: the layer programme per candidate is ~1,068 set-months (about 0.5 h of fleet) but needs the automatic layer builder (not built, my ETA 2026-11-20 12:00Z) and the exit engine families (builder not started); so the earliest "through everything" date for L01811caa and L6a25b155 (they stay first) is 2026-11-21 ~12:00Z, later if the exit engine builder starts late. L0f097450 (= L3701b464, same stream) is judged by the same ADD/REPLACE rule.

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
| L3701b464 | long-only REPLACE K7 | 2023 | -14% | +3% | +29% | +1% | AMBER | 0.63 | see shortlist |
| L3701b464 | long-only REPLACE K7 | 2024 | -8% | -2% | -3% | -17% | GREEN | 0.58 | see shortlist |
| L3701b464 | long-only REPLACE K7 | 2025 | +11% | +12% | +17% | +10% | AMBER | 0.50 | see shortlist |
| L3701b464 | long-only ADD | 2023 | -19% | -14% | +5% | -35% | GREEN | 0.68 | see shortlist |
| L3701b464 | long-only ADD | 2024 | -6% | +3% | -6% | -17% | GREEN | 0.73 | see shortlist |
| L3701b464 | long-only ADD | 2025 | +5% | +12% | +25% | -1% | AMBER | 0.62 | see shortlist |
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
- L3701b464 long-only REPLACE K7: no RED year
- L3701b464 long-only ADD: no RED year
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

