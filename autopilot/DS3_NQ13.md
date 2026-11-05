# DS3_NQ13 - NQ 13-year parameter-regime map (ZL-2, T2_NQ13) - INTERIM 1, 2026-11-05T19:46:29Z
Append-only. Scope note (prereg): outputs/l2vast/ds3/prereg/T2_NQ13_scope.md, sha256 0678be426feeeb3279cba2fcf3bc95c6012eaa637b75f9d6c91eda58d827cb14 (logged in DECISIONS.md before any outcome statistic). n_tested = 9,855 cell-sessions (3,483 cells x live sessions, brackets stop {40,60,80} x target {40,60,90}). Ledger T2_NQ13.

## Plain sentence
No walk-forward parameter selector (trailing 6/12/24 months -> next month, per book x session) beats the fixed live parameters on 2023-26; so no params_policy.txt refit rule is proposed.

## Objects and calibration (read first)
- 1-min object (2013-2026, percent frame: brackets/slip/fees scaled by raw_close/20,620, P&L in 2023-26 point-equivalents x $20). Live-cell weekly correlation to the 1-s engine plain-signal series is 0.49-0.84, below the 0.90 rule: NO formal verdict from it. Pre-2023 results (E2) are descriptive only.
- 1-s path object (2023-04..2026-10, same 935 label days): calibration >= .90 for 7 of 14 pairs: KB asia/london/nypm, SM asia/london, HM asia, PB asia. Near misses: KB nyam .890, PE nyam .894, PE london .870, PE asia .853, HM nyam .844, MV nyam .851; MV london .591. Formal verdicts only for the 7 pairs, only on 2023-26.
- Bases named: V0 = engine as run (09:00-09:29 and 15:00-16:54 blocked); V2 = V0 + 09:30-09:59 and 18:00-18:04 blocked. Carrying weeks dropped (2023 W21-41, 2025 W06-09, 2026 W06-08, W29-39). Cap 2026-10-31.

## 13-year map (1-min, V0; same shape on V2)
- Live cell by year: negative in most years before 2023 and positive mainly 2024-25. Years with positive live $/wk in 2013-2022 (of 10): HM asia 4, HM nyam 8, KB asia 1, KB london 1, KB nyam 4, KB nypm 3, MV london 2, MV nyam 4, PB asia 3, PE asia 3, PE london 4, PE nyam 3, SM asia 6, SM london 4.
- Stability: mean year-to-year rank correlation of cell rankings 0.07 (pairs 0.0-0.15): which parameters paid does not persist. Live-cell neighbour sign agreement 0.66-0.88 (mean 0.78), i.e. mild plateau locally but the whole plateau flips sign across years.
- Static pre-2023 best cell -> 2023-26: mean rank correlation pre/post 0.12; best-pre cell has mean post percentile 0.63 and beats the live cell post in 10 of 14 pairs, but the live cell was chosen with hindsight on 2023-26, so this is not evidence for a selector.
- Full per-year x session x cell tables: out/dis_nq13/cell_year_usd_wk_{V0,V2}.csv, map_live_and_stability_{V0,V2}.csv, static_pre_to_post_selection.csv.

## Walk-forward selector (criterion = trailing net $; min trades 10/20/40 for T=6/12/24; fallback to live cell)
Evaluation E1 = 2023-04..2026-10 (formal, 1-s object); E2 = 2015-01..2023-03 (1-min, descriptive). Placebos: P1 random cell per month (forward-only), P2 stale window, family max-T over 42 selectors.
- 1-s E1, V0: 0 of 42 selectors with CI above zero; 29 of 42 below live; mean selector-minus-live -$183/wk-unit (formal 21: -$297, 81% negative); selector drawdown > live in 76% (formal 86%); family max-T p = .68.
- 1-s E1, V2: 0 of 42 CI above zero; 30 of 42 negative; mean diff -$162 (formal 21: -$276, 90% negative); drawdown worse in 74%; best single placebo p1 = .06 but family p = .73.
- 1-min E1 (descriptive): 0 of 42 win; mean diff -105 (V0), -110 (V2).
- 1-min E2 (descriptive): mean diff +108 (V0), +75 (V2); 2 of 42 with CI above zero; placebo p1<=.10 in 12 (V0) / 16 (V2); family max-T p .13 (V0), .08 (V2). Not formal (calibration fails) and does not carry into 2023-26 where the sign reverses.
- Win rule (positive with CI above zero on E1 and E2, placebo and family p <= .10, both bases, calibration passed): NOT met on any selector.

## Caveats
Percent-frame 1-min object is not the live stack; E2 descriptive only; live cell picked with hindsight on 2023-26 (biases E1 toward live); 1-s object uses fixed-point brackets and a shorter usable window range per T; 7 of 14 pairs only formal. Cross-check against BASE-4 E.walk_forward not yet done. Next interim in 6 h.

## INTERIM 1 ADDENDUM 2026-11-05T20:11:50Z (ZL-2): E.walk_forward cross-check, widening status, live-cell 13-year record

### Cross-check with BASE-4 E.walk_forward, base V0 (1-s object, 7 calibrated pairs, variants = grid cells at live bracket 60/60, daily P&L as one pseudo-trade/day, R=1200, trailing 6 and 12 mo, 2024-01..2026-10, purge 2 d, 500 random draws)

Evaluator selector is BELOW the fixed live cell in 11 of 14 pair x lookback rows (mean diff -172 \$/wk); random-choice p <= .10 in 1 rows; evaluator selector below the best fixed cell in 14 rows. Same conclusion as my own selector: no win. File: out/dis_nq13/wf_crosscheck_E_V0.csv. (Criterion differs: E uses trailing Calmar, mine trailing net \$.)

### Cross-check with BASE-4 E.walk_forward, base V2 (1-s object, 7 calibrated pairs, variants = grid cells at live bracket 60/60, daily P&L as one pseudo-trade/day, R=1200, trailing 6 and 12 mo, 2024-01..2026-10, purge 2 d, 500 random draws)

Evaluator selector is BELOW the fixed live cell in 11 of 14 pair x lookback rows (mean diff -259 \$/wk); random-choice p <= .10 in 1 rows; evaluator selector below the best fixed cell in 13 rows. Same conclusion as my own selector: no win. File: out/dis_nq13/wf_crosscheck_E_V2.csv. (Criterion differs: E uses trailing Calmar, mine trailing net \$.)

### Widening to the other pairs
Not rebuilt this round. The 7 failing pairs are shortfalls of the engine-vs-object match (KB nyam .890, PE nyam .894, PE london .870, PE asia .853, MV nyam .851, HM nyam .844, MV london .591), caused by engine-side mechanics the plain bar-close object does not carry (PE/HM/MV shape handling, session-lot sizing). Tuning the object until the correlation reaches .90 would be fitting the calibration to the target, so the honest route is to run the real V13T engine (run_v13t with CFG spec overrides) per cell; that is about 10^2-10^3 engine runs per pair and is queued as the next worker batch (3 workers). SM nyam/nypm, HM london/nypm, PB other sessions are not live sessions (not in scope note) and are not mapped. Their 1-min E2 results stay descriptive.

### Live cell $/week by year, 1-min percent-frame object, base V0 (trades/yr, hit rate in parentheses; descriptive, calibration < .90 so no formal verdict)

|   year | ('KB', 'asia')   | ('KB', 'london')   | ('KB', 'nyam')   | ('KB', 'nypm')   | ('PE', 'asia')   | ('PE', 'london')   | ('PE', 'nyam')    | ('SM', 'asia')   | ('SM', 'london')   | ('HM', 'asia')   | ('HM', 'nyam')   | ('MV', 'london')   | ('MV', 'nyam')   | ('PB', 'asia')   |
|-------:|:-----------------|:-------------------|:-----------------|:-----------------|:-----------------|:-------------------|:------------------|:-----------------|:-------------------|:-----------------|:-----------------|:-------------------|:-----------------|:-----------------|
|   2013 | -640 (315, 46%)  | -320 (187, 47%)    | -524 (458, 45%)  | -494 (288, 34%)  | -568 (311, 46%)  | -140 (178, 48%)    | -993 (447, 42%)   | +39 (183, 51%)   | -324 (117, 43%)    | -207 (289, 48%)  | +339 (330, 48%)  | -384 (389, 48%)    | +38 (408, 48%)   | -642 (198, 42%)  |
|   2014 | -659 (307, 45%)  | -446 (211, 45%)    | -403 (511, 46%)  | -28 (312, 41%)   | -140 (301, 48%)  | +44 (211, 51%)     | -384 (477, 45%)   | +104 (145, 51%)  | -170 (141, 46%)    | +80 (293, 50%)   | -367 (379, 45%)  | -344 (409, 48%)    | -40 (475, 47%)   | -161 (178, 48%)  |
|   2015 | -130 (435, 50%)  | +413 (393, 52%)    | -537 (593, 47%)  | -185 (415, 44%)  | -450 (427, 48%)  | -522 (416, 48%)    | -758 (558, 46%)   | -0 (166, 51%)    | -402 (185, 45%)    | -761 (380, 46%)  | +48 (424, 48%)   | -1205 (607, 46%)   | -136 (529, 48%)  | +26 (235, 51%)   |
|   2016 | -366 (499, 49%)  | -64 (428, 50%)     | -242 (538, 47%)  | +100 (386, 43%)  | +294 (497, 52%)  | -497 (360, 48%)    | +453 (533, 49%)   | -610 (191, 43%)  | -288 (157, 46%)    | +441 (420, 52%)  | +95 (389, 47%)   | -150 (608, 50%)    | +97 (502, 47%)   | -147 (310, 49%)  |
|   2017 | +33 (315, 48%)   | -138 (114, 46%)    | -533 (338, 40%)  | +196 (175, 30%)  | +158 (313, 48%)  | +204 (119, 52%)    | -442 (317, 41%)   | +207 (138, 50%)  | +171 (132, 48%)    | +678 (308, 51%)  | +230 (253, 44%)  | +42 (331, 47%)     | -166 (309, 43%)  | +357 (192, 51%)  |
|   2018 | -542 (613, 49%)  | -330 (499, 49%)    | +568 (761, 51%)  | -361 (569, 46%)  | -517 (571, 49%)  | -374 (490, 49%)    | -371 (699, 48%)   | -579 (167, 43%)  | +44 (189, 51%)     | +389 (488, 52%)  | +325 (491, 50%)  | +104 (639, 51%)    | -121 (674, 49%)  | +132 (261, 51%)  |
|   2019 | -451 (506, 48%)  | -728 (377, 46%)    | +579 (542, 51%)  | -56 (335, 41%)   | -222 (494, 49%)  | +119 (362, 51%)    | -203 (532, 47%)   | +124 (174, 52%)  | +296 (166, 54%)    | -303 (442, 49%)  | +244 (404, 49%)  | -608 (558, 47%)    | -33 (500, 47%)   | -666 (270, 45%)  |
|   2020 | -565 (1102, 50%) | -995 (944, 49%)    | +618 (893, 52%)  | +494 (729, 50%)  | -662 (1038, 49%) | -602 (911, 50%)    | +111 (885, 51%)   | +106 (206, 52%)  | +153 (239, 53%)    | -281 (773, 50%)  | +302 (546, 51%)  | -1003 (1058, 49%)  | +623 (835, 52%)  | -776 (480, 47%)  |
|   2021 | -237 (546, 50%)  | -561 (459, 48%)    | +347 (714, 50%)  | -1004 (441, 41%) | +531 (526, 52%)  | +202 (457, 51%)    | +2 (656, 49%)     | +25 (165, 50%)   | -109 (185, 49%)    | -593 (468, 48%)  | -426 (477, 46%)  | -165 (630, 49%)    | +192 (638, 50%)  | -193 (268, 49%)  |
|   2022 | -1226 (886, 48%) | -1365 (1048, 48%)  | -226 (1104, 50%) | -258 (884, 49%)  | -1813 (832, 46%) | -860 (1013, 49%)   | -1125 (1079, 48%) | -359 (206, 47%)  | -882 (292, 44%)    | -2051 (659, 44%) | +214 (638, 51%)  | -1351 (1126, 48%)  | -787 (1009, 49%) | -750 (311, 46%)  |
|   2023 | -232 (411, 49%)  | -65 (376, 50%)     | -454 (774, 49%)  | +411 (499, 47%)  | -273 (420, 49%)  | +365 (376, 53%)    | +593 (705, 52%)   | +284 (144, 54%)  | -326 (199, 47%)    | +65 (372, 51%)   | -425 (477, 48%)  | +15 (584, 50%)     | -811 (662, 48%)  | +313 (184, 54%)  |
|   2024 | +385 (469, 52%)  | +496 (329, 54%)    | +701 (652, 52%)  | +866 (412, 48%)  | +90 (440, 51%)   | -148 (333, 50%)    | +340 (604, 51%)   | +348 (168, 55%)  | +78 (185, 51%)     | +361 (392, 52%)  | +858 (440, 54%)  | -344 (517, 49%)    | +906 (552, 53%)  | +662 (234, 56%)  |
|   2025 | +24 (615, 51%)   | +7 (463, 50%)      | -34 (689, 49%)   | -63 (498, 45%)   | +516 (597, 53%)  | -203 (472, 50%)    | -169 (647, 48%)   | +443 (176, 56%)  | +23 (176, 50%)     | +1219 (481, 56%) | +457 (436, 50%)  | -466 (639, 49%)    | +1097 (614, 52%) | +866 (284, 57%)  |
|   2026 | +446 (648, 52%)  | -990 (459, 47%)    | -1432 (612, 46%) | -521 (365, 42%)  | +410 (631, 52%)  | -135 (446, 50%)    | -998 (606, 47%)   | -274 (212, 49%)  | +205 (171, 53%)    | +18 (513, 51%)   | -109 (415, 48%)  | -155 (567, 50%)    | -602 (553, 48%)  | -41 (396, 51%)   |

### Live cell $/week by year, 1-min percent-frame object, base V2 (trades/yr, hit rate in parentheses; descriptive, calibration < .90 so no formal verdict)

|   year | ('KB', 'asia')   | ('KB', 'london')   | ('KB', 'nyam')   | ('KB', 'nypm')   | ('PE', 'asia')   | ('PE', 'london')   | ('PE', 'nyam')   | ('SM', 'asia')   | ('SM', 'london')   | ('HM', 'asia')   | ('HM', 'nyam')   | ('MV', 'london')   | ('MV', 'nyam')   | ('PB', 'asia')   |
|-------:|:-----------------|:-------------------|:-----------------|:-----------------|:-----------------|:-------------------|:-----------------|:-----------------|:-------------------|:-----------------|:-----------------|:-------------------|:-----------------|:-----------------|
|   2013 | -417 (307, 48%)  | -137 (187, 49%)    | -247 (377, 45%)  | -307 (272, 36%)  | -698 (306, 45%)  | -278 (178, 46%)    | -600 (375, 43%)  | +39 (183, 51%)   | -324 (117, 43%)    | -13 (286, 50%)   | -130 (261, 43%)  | -384 (389, 48%)    | -95 (341, 47%)   | -526 (195, 44%)  |
|   2014 | -624 (303, 45%)  | -419 (203, 46%)    | +47 (397, 47%)   | +5 (310, 41%)    | -250 (302, 47%)  | +161 (206, 52%)    | +71 (386, 46%)   | +104 (145, 51%)  | -170 (141, 46%)    | +83 (293, 50%)   | -96 (291, 45%)   | -344 (409, 48%)    | +343 (366, 48%)  | -183 (175, 47%)  |
|   2015 | +10 (428, 50%)   | +443 (395, 53%)    | +17 (444, 48%)   | -186 (419, 44%)  | -567 (423, 47%)  | -407 (415, 48%)    | -477 (453, 46%)  | -0 (166, 51%)    | -402 (185, 45%)    | -644 (373, 47%)  | -150 (305, 47%)  | -1205 (607, 46%)   | +177 (398, 49%)  | +26 (233, 51%)   |
|   2016 | -386 (488, 49%)  | +78 (424, 51%)     | -360 (412, 45%)  | -150 (388, 42%)  | +394 (492, 52%)  | -431 (371, 48%)    | -101 (415, 46%)  | -610 (191, 43%)  | -288 (157, 46%)    | +423 (412, 52%)  | +533 (287, 49%)  | -150 (608, 50%)    | -83 (393, 46%)   | -288 (310, 48%)  |
|   2017 | +12 (310, 47%)   | -60 (114, 47%)     | +356 (267, 44%)  | +113 (174, 29%)  | -15 (310, 47%)   | +229 (115, 53%)    | -119 (263, 41%)  | +207 (138, 50%)  | +171 (132, 48%)    | +542 (306, 50%)  | +296 (193, 44%)  | +42 (331, 47%)     | -102 (248, 42%)  | +302 (189, 50%)  |
|   2018 | -904 (597, 47%)  | -401 (504, 49%)    | +783 (556, 52%)  | -381 (572, 46%)  | -856 (573, 47%)  | -376 (496, 49%)    | -336 (526, 48%)  | -579 (167, 43%)  | +44 (189, 51%)     | +368 (483, 52%)  | +258 (355, 50%)  | +104 (639, 51%)    | -80 (517, 49%)   | +173 (255, 52%)  |
|   2019 | -540 (493, 48%)  | -705 (376, 46%)    | +36 (413, 48%)   | -74 (341, 41%)   | -445 (495, 48%)  | +104 (360, 51%)    | -149 (426, 46%)  | +124 (174, 52%)  | +296 (166, 54%)    | -27 (438, 50%)   | +305 (303, 49%)  | -608 (558, 47%)    | -170 (382, 45%)  | -598 (262, 45%)  |
|   2020 | -578 (1048, 50%) | -858 (944, 49%)    | +313 (636, 51%)  | +497 (725, 51%)  | -265 (1019, 50%) | -557 (913, 50%)    | +322 (661, 51%)  | +106 (206, 52%)  | +153 (239, 53%)    | -388 (752, 50%)  | +457 (370, 52%)  | -1003 (1058, 49%)  | +643 (615, 53%)  | -658 (471, 48%)  |
|   2021 | +149 (541, 51%)  | -539 (464, 48%)    | +881 (524, 52%)  | -898 (435, 41%)  | +507 (521, 53%)  | +203 (455, 51%)    | -94 (501, 48%)   | +25 (165, 50%)   | -109 (185, 49%)    | -555 (459, 48%)  | -148 (340, 46%)  | -165 (630, 49%)    | +218 (477, 49%)  | -286 (266, 48%)  |
|   2022 | -1489 (840, 47%) | -1295 (1049, 48%)  | -547 (748, 49%)  | -259 (883, 49%)  | -2017 (817, 46%) | -791 (1014, 49%)   | -647 (758, 49%)  | -359 (206, 47%)  | -882 (292, 44%)    | -2372 (645, 43%) | -3 (434, 50%)    | -1351 (1126, 48%)  | -536 (684, 49%)  | -771 (306, 45%)  |
|   2023 | +93 (391, 50%)   | -162 (385, 50%)    | +270 (558, 51%)  | +196 (501, 46%)  | -314 (406, 48%)  | +340 (381, 52%)    | +653 (545, 53%)  | +284 (144, 54%)  | -326 (199, 47%)    | +377 (365, 53%)  | -520 (352, 45%)  | +15 (584, 50%)     | -347 (489, 49%)  | +313 (182, 54%)  |
|   2024 | +601 (454, 53%)  | +610 (330, 55%)    | +551 (494, 51%)  | +974 (411, 48%)  | +459 (434, 53%)  | -261 (339, 49%)    | +76 (478, 50%)   | +348 (168, 55%)  | +78 (185, 51%)     | +386 (387, 52%)  | +378 (329, 52%)  | -344 (517, 49%)    | +540 (430, 52%)  | +732 (231, 57%)  |
|   2025 | +366 (579, 52%)  | +87 (463, 51%)     | +309 (508, 49%)  | -131 (492, 44%)  | +588 (590, 53%)  | -145 (474, 50%)    | -458 (489, 46%)  | +443 (176, 56%)  | +23 (176, 50%)     | +1178 (467, 56%) | -250 (324, 45%)  | -466 (639, 49%)    | +709 (449, 51%)  | +890 (283, 57%)  |
|   2026 | +961 (626, 53%)  | -1072 (453, 47%)   | -1027 (446, 45%) | -512 (362, 42%)  | +446 (616, 52%)  | +65 (451, 51%)     | -1275 (438, 44%) | -274 (212, 49%)  | +205 (171, 53%)    | -7 (504, 51%)    | -92 (276, 47%)   | -155 (567, 50%)    | -424 (387, 47%)  | +105 (393, 51%)  |

