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


## NQ-ES TRANSFER MAP (ZL-2, 2026-11-05T20:32:53Z) - half 1 of the section-1 compute share; ES lead cells from Z1 are NOT yet available
Object: my grid (3,483 cells per base; same families, live sessions) run on ES 1-min bars (cache_te2/ES.npz, same back-adjust) in the SAME percent frame as NQ: brackets, slippage and fees scaled by raw_close/20,620, so ES percent distances equal the NQ ones, P&L in NQ-frame $ (not ES contract dollars; ES tick/slip not modelled; descriptive, not a verdict). Bases V0 and V2 as named. Files: out/dis_nq13/nq_es_transfer_{V0,V2}.csv; code scratchpad nq13_lib_es.py, nq13_run_es.py, es_xfer.py.
- Cell-ranking agreement NQ vs ES within the same year (Spearman across cells, mean over 2013-2026): V0 0.25, V2 0.26 (range 0.12-0.37 by book x session): positive but weak, so parameter quality is partly instrument-general (bracket and shape effects) and mostly instrument-specific.
- NQ pre-2023 top-5% cells applied to ES 2023-26: above the ES all-cell median in 9 of 14 pairs (V0), 7 of 14 (V2); median difference +19 (V0), 0 (V2) per week. Rank correlation of NQ-pre cell P&L with ES-post cell P&L: -0.44 to +0.36, mean about 0.1. Conclusion: a parameter set picked on NQ does not reliably transfer to ES; each instrument needs its own grid (as Z1 is doing), and NQ-derived parameters give no head start.
- NQ live cells on ES 2023-26 ($/wk, V0): KB nyam +254, KB others -114..-214, SM asia -94, PB asia +37, HM nyam +3, HM asia -119, MV -155/-653, PE asia +5: ES does not reproduce the NQ live-cell pattern.
- Section-1 hand-off: once Z1 reports its ES grid winners, I will map each winner onto the NQ-equivalent cell (same family/anchor, percent-frame bracket) and report its NQ 2023-26 P&L and its NQ cell percentile. Not done yet because no ES row exists. Registered in INSTR_NTESTED as an extra descriptive line (ES run of the same 3,483 cells x2 bases; no selection, not counted as a new search).
- Heavy workers this round: up to 3 (ES grid, 3 parallel); machine load was high, MemAvailable stayed above 40 GB.

## INTERIM 2 2026-11-05T20:39:30Z (ZL-2): ENGINE-IN-THE-LOOP bracket neighbourhood (T2_NQ13_ENG, scope sha256 5a7f2f40bb24cf2469c04453576c57dcf1e1f9ed33c26b9bc3ee3c76d35e016f, logged before any engine cell)
Object: the V13T engine itself (all components off, plain library signals, live cost frame, lots 1), bracket override stop x {0.75,1,1.25} and target x {0.75,1,1.25} of the library bracket, 9 cells x 14 live pairs = 126 cell-sessions (n_tested), 18 engine runs (V0 and V2; V2 = V0 + 09:30-09:59 and 18:00-18:04 entries skipped via extra_skip), 4 workers. This is the engine-true BRACKET dimension for all 14 pairs including the 7 that fail the 1-s object calibration; the signal-parameter dimension cannot be varied in the engine (precomputed signal library) and stays on the object. The live cell (1,1) reproduces the ALL_OFF cube exactly (max abs diff 0). 2023-04..2026-10, carrying weeks dropped. Files: out/dis_nq13/eng_bracket_{neighbours,wf}.csv.
Deviation from the scope note, stated: the cube has dollars, not trade counts, so the selector's minimum-sample rule uses active days (5/10/20 for T=6/12/24) instead of trades 10/20/40.
- Live cell is the best total bracket among the 9 across the whole book (V0 $409.9k vs next 320.3k stop x0.75; V2 $569.3k vs next 444.9k), but it is not the best cell in any single pair at V0 and in 1 of 14 at V2: neighbours beat it in-sample per pair, and only 1 of 112 (V0) / 1 of 112 (V2) neighbour cells has a CI above zero versus the live cell (4 have a CI below zero in each base).
- Walk-forward bracket selector (42 selectors = 14 pairs x T 6/12/24), mean selector-minus-live: V0 -5, V2 -38 $/wk; positive in 23 (V0) / 19 (V2) of 42; CI above zero: 0 (V0), 1 (V2: HM nyam T=12, diff +303, CI [+21,+589], P1 p .01). Family max-mean placebo p: V0 .84, V2 .18. Selector drawdown worse than live in 23 of 42 on both bases.
- Verdict: the family test fails on both bases (V2 .18 > .10, V0 .84), so no bracket-refit rule; the single V2 hit (HM nyam T=12) is best-of-42 and is NOT a lead. No params_policy.txt rule, consistent with interim 1.
- Remaining open: signal-parameter neighbourhoods for the 7 failing pairs stay object-only and descriptive; they would need the signal library regenerated per parameter, which I did not do (cost estimate: a library rebuild per cell, hours each).

## NQ-ES WINNERS MAP, status 2026-11-05T20:39:59Z (ZL-2)
Z1's ES stage-1 interim (DS3_INSTR2_ES.md, scope sha 8898fc1c...) reports 0 lead candidates: 486,864 cells evaluated, 8,149 tolerant, best family p .64; all 30 finalists fail (family p 1.00 or tolerant gate). The ES top-25 tolerant table is dominated by sessions that are not live NQ sessions and by 'against' (fade) orientation: close x12, pre x6, nyam x3, nypm x3 (rest PB pre), so there is no like-for-like NQ-equivalent cell for most rows (my NQ object only holds live sessions with the live trigger orientation). The few overlapping rows are Keltner/Supertrend nyam/nypm 'with' (K ema21 atr14/atr10 m2.5 nyam; S b15 atr10 m2.5 and S b10 atr5 m3.0 nypm); their ES shapes are R-based (D600/D1200/A3) and are not in the NQ-live percent-frame bracket grid, so no numeric map is produced. Combined with the weak NQ-ES parameter transfer above (rank corr .25; NQ-top cells above ES median in 9/14 and 7/14), the ES lead the coordinator hoped for does not exist at stage 1, and an NQ-derived head start on ES is not supported. No further compute spent here; will map any ES finalist Z1 promotes after stage 2.

## INTERIM 3 2026-11-05T20:41:20Z (ZL-2): signal-library regeneration per parameter cell - NOT run, reason (no numbers produced, no prereg consumed)
The coordinator asked for the engine library to be rebuilt per signal-parameter cell. I traced the engine inputs: d7lib.X()['d'] comes from s2_lib.setup -> the research trade universe (tid-keyed trade table with per-row kin, entry price, library stop/target, flat index) joined to per-tid stores (trendgate chart_5m ER, zone-line fire masks from zl, PE 'R_three' 45-s confirmation events keyed by ek, L2SE 70/30 kernel outputs o73). A different Keltner / Supertrend / HM / MV / PE / PB parameter produces a different trade universe, so every per-tid store (ER, zones, PE events, o73) would have to be regenerated and tie-out-tested against the live run for each cell; that is a multi-day pipeline with no existing builder, not hours per cell, and a shortcut (swapping rows into d without those joins) would give numbers that look engine-true and are not. I did not do it, and I register no cells for it.
What stands instead: (a) engine-true bracket neighbourhood, all 14 pairs, V0 and V2 (interim 2); (b) signal-parameter neighbourhoods on the 1-s object, formal for the 7 pairs that pass calibration, descriptive for the rest (interim 1). The hindsight bias of the live cell (chosen on 2023-26) is stated against every E1 comparison; the E2 (2015-2023) rows carry no such bias but are 1-min and descriptive.
ZB: not taken. Z3 has stage A and B done and finalist workers running (MORNING 2026-11-05T20:38Z; DECISIONS lists stage-B list, finalists 1 and 2, 13-year check), so a ZB grid from me would duplicate its cells; I did not start it.

## INTERIM 4 2026-11-06T00:22Z (CHAR-C, T2_NQ13_C; scope l2vast/ds3/prereg/T2_NQ13_C_scope.md sha256 in DECISIONS.md, filed before any statistic): calibration 1-min vs 1-s, live-neighbourhood regime table, Calmar parameter selector vs live
Objects are ZL-2's unchanged (1-min percent-frame object 2013-2026 and 1-s path object 2023-04..2026-10; copies in /mnt/l2/l2vast/find_c/nq13/; code l2vast/ds3/code/find_c/nq13c.py, nq13c_md.py). Bases: V0 = engine as run (09:00-09:29 and 15:00-16:54 blocked), V2 = V0 + 09:30-09:59 and 18:00-18:04 blocked. Carrying weeks dropped. NQ is clean in the bad-print audit (<= 0.11% bars any year), no repair.

### 1. Calibration 1-min object vs 1-s object (weekly P&L correlation 2023-04..2026-10, carry dropped; gate >= .90), with the engine tie of the 1-s object from interim 1
| book | session | base | 1-min vs 1-s, live cell | median over the 9 live-parameter brackets | median over ALL grid cells | share of cells >= .90 | 1-s vs ENGINE (interim 1) | 1-min total $k | 1-s total $k |
|--|--|--|--|--|--|--|--|--|--|
| KB | asia | V0 | 0.722 | 0.778 | 0.803 | 0.0% | 0.905 | 38.5 | 60.0 |
| KB | london | V0 | 0.694 | 0.663 | 0.644 | 0.0% | 0.907 | 2.8 | -1.8 |
| KB | nyam | V0 | 0.781 | 0.790 | 0.786 | 0.2% | 0.890 (fails) | -22.3 | -47.4 |
| KB | nypm | V0 | 0.743 | 0.743 | 0.780 | 0.7% | 0.914 | 44.4 | -8.4 |
| PE | asia | V0 | 0.746 | 0.806 | 0.812 | 0.0% | 0.853 (fails) | 46.2 | 55.1 |
| PE | london | V0 | 0.670 | 0.720 | 0.710 | 0.0% | 0.870 (fails) | 2.5 | -5.9 |
| PE | nyam | V0 | 0.840 | 0.840 | 0.830 | 1.5% | 0.894 (fails) | -4.1 | -41.4 |
| SM | asia | V0 | 0.853 | 0.833 | 0.827 | 2.6% | 0.917 | 48.4 | 56.6 |
| SM | london | V0 | 0.759 | 0.768 | 0.764 | 0.2% | 0.907 | 19.4 | 12.5 |
| HM | asia | V0 | 0.791 | 0.790 | 0.799 | 0.0% | 0.922 | 96.3 | 86.5 |
| HM | nyam | V0 | 0.787 | 0.782 | 0.819 | 0.0% | 0.844 (fails) | 66.8 | 61.5 |
| MV | london | V0 | 0.774 | 0.789 | 0.803 | 0.0% | 0.591 (fails) | -37.8 | -78.6 |
| MV | nyam | V0 | 0.823 | 0.809 | 0.818 | 0.0% | 0.851 (fails) | 62.0 | 36.2 |
| PB | asia | V0 | 0.896 | 0.858 | 0.837 | 0.2% | 0.941 | 114.1 | 104.8 |
| KB | asia | V2 | 0.720 | 0.793 | 0.807 | 0.2% | 0.905 | 67.9 | 109.7 |
| KB | london | V2 | 0.659 | 0.659 | 0.648 | 0.0% | 0.907 | 8.8 | -1.9 |
| KB | nyam | V2 | 0.838 | 0.831 | 0.815 | 1.9% | 0.890 (fails) | 31.6 | 6.1 |
| KB | nypm | V2 | 0.764 | 0.758 | 0.780 | 0.8% | 0.914 | 40.4 | 5.8 |
| PE | asia | V2 | 0.763 | 0.800 | 0.821 | 0.0% | 0.853 (fails) | 71.1 | 93.2 |
| PE | london | V2 | 0.677 | 0.690 | 0.703 | 0.0% | 0.870 (fails) | 0.5 | 3.5 |
| PE | nyam | V2 | 0.864 | 0.864 | 0.845 | 0.8% | 0.894 (fails) | -41.0 | -17.4 |
| SM | asia | V2 | 0.853 | 0.833 | 0.827 | 2.6% | 0.917 | 48.4 | 56.6 |
| SM | london | V2 | 0.759 | 0.768 | 0.764 | 0.2% | 0.907 | 19.4 | 12.5 |
| HM | asia | V2 | 0.826 | 0.781 | 0.799 | 0.0% | 0.922 | 94.8 | 79.1 |
| HM | nyam | V2 | 0.841 | 0.837 | 0.841 | 2.1% | 0.844 (fails) | 20.9 | 6.0 |
| MV | london | V2 | 0.774 | 0.789 | 0.803 | 0.0% | 0.591 (fails) | -37.8 | -78.6 |
| MV | nyam | V2 | 0.872 | 0.860 | 0.848 | 2.1% | 0.851 (fails) | 40.0 | 44.2 |
| PB | asia | V2 | 0.893 | 0.853 | 0.838 | 0.0% | 0.941 | 124.0 | 112.4 |

Reading: 0 of 14 pairs (either base) reach .90 between the 1-min and the 1-s object (live-cell range 0.66-0.90, best PB asia 0.896); at most 2.6% of grid cells of any pair do. Therefore the 13-year 1-min object is DESCRIPTIVE for all 14 pairs, including the 7 that were already below .90 against the engine (KB nyam, PE asia/london/nyam, HM nyam, MV london/nyam), and nothing before 2023-04 can carry a formal verdict. FORMAL status exists only for the 2023-04..2026-10 1-s object and only for the 7 pairs whose 1-s object ties to the engine at >= .90 (KB asia/london/nypm, SM asia/london, HM asia, PB asia).

### 2. Percent-frame yearly regime table, live parameter neighbourhood (1-min object; descriptive; $/week at 1 lot; neighbourhood = cells that differ by one grid step in exactly one signal parameter at the live bracket 60/60: KB 8-ish, SM, PB, HM, MV, PE as in the grids)

**Base V0 - live cell $/wk by year** (neighbourhood mean in brackets; share of neighbours with the live cell's sign in the last line of each pair is omitted for width, see nq13c regime.pkl)

| pair | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 | years+ 2013-22 (live / nbr mean) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| KB asia | -640 (-443) | -659 (-506) | -130 (-536) | -366 (-389) | +33 (+68) | -542 (-516) | -451 (-491) | -565 (-153) | -237 (-459) | -1226 (-1198) | -232 (-359) | +385 (+417) | +24 (+120) | +446 (+495) | 1 / 1 |
| KB london | -320 (-86) | -446 (-214) | +413 (+454) | -64 (-288) | -138 (-19) | -330 (-343) | -728 (-607) | -995 (-800) | -561 (-467) | -1365 (-1203) | -65 (-20) | +496 (+264) | +7 (+192) | -990 (-342) | 1 / 1 |
| KB nyam | -524 (-213) | -403 (-329) | -537 (-386) | -242 (+115) | -533 (-233) | +568 (+196) | +579 (+399) | +618 (+433) | +347 (+100) | -226 (-235) | -454 (-7) | +701 (+721) | -34 (-78) | -1432 (-1317) | 4 / 5 |
| KB nypm | -494 (-265) | -28 (+284) | -185 (+157) | +100 (+139) | +196 (+123) | -361 (-342) | -56 (-374) | +494 (+129) | -1004 (-802) | -258 (-495) | +411 (+293) | +866 (+334) | -63 (-223) | -521 (-511) | 3 / 5 |
| PE asia | -568 (-690) | -140 (-134) | -450 (-321) | +294 (+308) | +158 (-25) | -517 (-419) | -222 (-222) | -662 (-789) | +531 (+336) | -1813 (-1809) | -273 (-88) | +90 (+135) | +516 (+683) | +410 (+271) | 3 / 2 |
| PE london | -140 (-125) | +44 (+32) | -522 (-450) | -497 (-443) | +204 (+131) | -374 (-351) | +119 (-101) | -602 (-567) | +202 (+181) | -860 (-1221) | +365 (+121) | -148 (-116) | -203 (-43) | -135 (-203) | 4 / 3 |
| PE nyam | -993 (-751) | -384 (-253) | -758 (-474) | +453 (+325) | -442 (-404) | -371 (-2) | -203 (-241) | +111 (+282) | +2 (+194) | -1125 (-929) | +593 (+384) | +340 (+694) | -169 (-149) | -998 (-872) | 3 / 3 |
| SM asia | +39 (-87) | +104 (-355) | -0 (-137) | -610 (-404) | +207 (+204) | -579 (-416) | +124 (-126) | +106 (-105) | +25 (-116) | -359 (-219) | +284 (+21) | +348 (+128) | +443 (+193) | -274 (-253) | 6 / 1 |
| SM london | -324 (-185) | -170 (-84) | -402 (-543) | -288 (-214) | +171 (-131) | +44 (+185) | +296 (+173) | +153 (-201) | -109 (+52) | -882 (-598) | -326 (-450) | +78 (+98) | +23 (-40) | +205 (-33) | 4 / 3 |
| HM asia | -207 (-141) | +80 (-352) | -761 (-559) | +441 (+339) | +678 (+341) | +389 (+70) | -303 (-234) | -281 (-111) | -593 (-375) | -2051 (-1595) | +65 (-298) | +361 (+427) | +1219 (+1096) | +18 (+195) | 4 / 3 |
| HM nyam | +339 (+193) | -367 (-329) | +48 (-165) | +95 (-24) | +230 (+251) | +325 (+484) | +244 (+257) | +302 (+378) | -426 (-448) | +214 (-252) | -425 (-466) | +858 (+665) | +457 (+179) | -109 (-66) | 8 / 5 |
| MV london | -384 (-559) | -344 (-490) | -1205 (-649) | -150 (-365) | +42 (+124) | +104 (-146) | -608 (-424) | -1003 (-971) | -165 (-359) | -1351 (-1521) | +15 (+108) | -344 (-194) | -466 (-467) | -155 (+329) | 2 / 1 |
| MV nyam | +38 (-152) | -40 (-101) | -136 (-110) | +97 (-9) | -166 (+149) | -121 (-315) | -33 (+83) | +623 (+419) | +192 (+433) | -787 (-302) | -811 (-941) | +906 (+365) | +1097 (+352) | -602 (-1003) | 4 / 4 |
| PB asia | -642 (-488) | -161 (-205) | +26 (-16) | -147 (-161) | +357 (+311) | +132 (-99) | -666 (-567) | -776 (-678) | -193 (-123) | -750 (-701) | +313 (+137) | +662 (+538) | +866 (+713) | -41 (-91) | 3 / 1 |

**Base V0 - three session blocks pooled** (sum over the pairs of the block: live cells | neighbourhood means | mean share of neighbours with the live sign | mean share of all grid cells positive)

| block (pairs) | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ASIA (5) | -2018 / -1849 / 0.80 / 0.16 | -775 / -1552 / 0.63 / 0.10 | -1316 / -1569 / 0.78 / 0.20 | -388 / -306 / 0.82 / 0.43 | +1433 / +900 / 0.77 / 0.65 | -1116 / -1381 / 0.78 / 0.20 | -1517 / -1640 / 0.72 / 0.28 | -2177 / -1836 / 0.78 / 0.19 | -468 / -738 / 0.87 / 0.43 | -6198 / -5523 / 0.97 / 0.05 | +157 / -588 / 0.66 / 0.37 | +1848 / +1645 / 0.92 / 0.85 | +3069 / +2804 / 0.92 / 0.86 | +559 / +617 / 0.80 / 0.54 |
| LONDON (4) | -1168 / -954 / 0.91 / 0.25 | -917 / -757 / 0.83 / 0.33 | -1715 / -1187 / 1.00 / 0.12 | -998 / -1310 / 0.89 / 0.16 | +279 / +105 / 0.48 / 0.52 | -557 / -655 / 0.84 / 0.44 | -921 / -959 / 0.82 / 0.25 | -2448 / -2539 / 0.79 / 0.19 | -633 / -593 / 0.81 / 0.38 | -4459 / -4542 / 1.00 / 0.00 | -11 / -241 / 0.73 / 0.37 | +83 / +51 / 0.70 / 0.43 | -638 / -359 / 0.57 / 0.44 | -1076 / -249 / 0.57 / 0.47 |
| NY (nyam+nypm) (5) | -1634 / -1187 / 0.76 / 0.37 | -1223 / -728 / 0.71 / 0.42 | -1569 / -979 / 0.53 / 0.39 | +503 / +547 / 0.57 / 0.56 | -716 / -115 / 0.68 / 0.58 | +40 / +21 / 0.80 / 0.64 | +531 / +124 / 0.77 / 0.44 | +2147 / +1641 / 0.79 / 0.74 | -890 / -524 / 0.87 / 0.52 | -2182 / -2212 / 0.58 / 0.28 | -686 / -736 / 0.82 / 0.40 | +3671 / +2780 / 0.92 / 0.89 | +1288 / +80 / 0.73 / 0.52 | -3662 / -3769 / 0.90 / 0.18 |

**Base V2 - live cell $/wk by year** (neighbourhood mean in brackets; share of neighbours with the live cell's sign in the last line of each pair is omitted for width, see nq13c regime.pkl)

| pair | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 | years+ 2013-22 (live / nbr mean) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| KB asia | -417 (-336) | -624 (-519) | +10 (-447) | -386 (-382) | +12 (-49) | -904 (-630) | -540 (-390) | -578 (-289) | +149 (-388) | -1489 (-1554) | +93 (-182) | +601 (+551) | +366 (+457) | +961 (+845) | 3 / 0 |
| KB london | -137 (-100) | -419 (-149) | +443 (+328) | +78 (-195) | -60 (-45) | -401 (-353) | -705 (-568) | -858 (-798) | -539 (-427) | -1295 (-1173) | -162 (-115) | +610 (+270) | +87 (+258) | -1072 (-381) | 2 / 1 |
| KB nyam | -247 (-44) | +47 (+124) | +17 (+84) | -360 (-347) | +356 (+343) | +783 (+201) | +36 (+121) | +313 (+441) | +881 (+422) | -547 (-238) | +270 (+178) | +551 (+270) | +309 (-107) | -1027 (-799) | 7 / 7 |
| KB nypm | -307 (-237) | +5 (+336) | -186 (+182) | -150 (+16) | +113 (+166) | -381 (-320) | -74 (-367) | +497 (+172) | -898 (-750) | -259 (-497) | +196 (+202) | +974 (+323) | -131 (-227) | -512 (-493) | 3 / 5 |
| PE asia | -698 (-738) | -250 (-251) | -567 (-413) | +394 (+337) | -15 (-79) | -856 (-602) | -445 (-377) | -265 (-426) | +507 (+273) | -2017 (-1951) | -314 (-124) | +459 (+366) | +588 (+660) | +446 (+416) | 2 / 2 |
| PE london | -278 (-265) | +161 (+113) | -407 (-375) | -431 (-399) | +229 (+172) | -376 (-341) | +104 (-60) | -557 (-519) | +203 (+203) | -791 (-1218) | +340 (+95) | -261 (-142) | -145 (-21) | +65 (-104) | 4 / 3 |
| PE nyam | -600 (-487) | +71 (+176) | -477 (-353) | -101 (-141) | -119 (-43) | -336 (-104) | -149 (-165) | +322 (+504) | -94 (+91) | -647 (-613) | +653 (+449) | +76 (+408) | -458 (-299) | -1275 (-1056) | 2 / 3 |
| SM asia | +39 (-87) | +104 (-355) | -0 (-137) | -610 (-404) | +207 (+204) | -579 (-416) | +124 (-126) | +106 (-105) | +25 (-116) | -359 (-219) | +284 (+21) | +348 (+128) | +443 (+193) | -274 (-253) | 6 / 1 |
| SM london | -324 (-185) | -170 (-84) | -402 (-543) | -288 (-214) | +171 (-131) | +44 (+185) | +296 (+173) | +153 (-201) | -109 (+52) | -882 (-598) | -326 (-450) | +78 (+98) | +23 (-40) | +205 (-33) | 4 / 3 |
| HM asia | -13 (-61) | +83 (-299) | -644 (-480) | +423 (+351) | +542 (+272) | +368 (+35) | -27 (-38) | -388 (-130) | -555 (-351) | -2372 (-1763) | +377 (-223) | +386 (+414) | +1178 (+1079) | -7 (+341) | 4 / 3 |
| HM nyam | -130 (-112) | -96 (-57) | -150 (-236) | +533 (+256) | +296 (+423) | +258 (+448) | +305 (+340) | +457 (+383) | -148 (-327) | -3 (-249) | -520 (-399) | +378 (+480) | -250 (-118) | -92 (-1) | 5 / 5 |
| MV london | -384 (-559) | -344 (-490) | -1205 (-649) | -150 (-365) | +42 (+124) | +104 (-146) | -608 (-424) | -1003 (-971) | -165 (-359) | -1351 (-1521) | +15 (+108) | -344 (-194) | -466 (-467) | -155 (+329) | 2 / 1 |
| MV nyam | -95 (-153) | +343 (+275) | +177 (+82) | -83 (-221) | -102 (+174) | -80 (-106) | -170 (+28) | +643 (+458) | +218 (+616) | -536 (-280) | -347 (-583) | +540 (+247) | +709 (-19) | -424 (-649) | 4 / 6 |
| PB asia | -526 (-433) | -183 (-219) | +26 (+4) | -288 (-238) | +302 (+265) | +173 (-77) | -598 (-514) | -658 (-580) | -286 (-188) | -771 (-695) | +313 (+149) | +732 (+592) | +890 (+713) | +105 (+16) | 3 / 2 |

**Base V2 - three session blocks pooled** (sum over the pairs of the block: live cells | neighbourhood means | mean share of neighbours with the live sign | mean share of all grid cells positive)

| block (pairs) | 2013 | 2014 | 2015 | 2016 | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 | 2024 | 2025 | 2026 |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ASIA (5) | -1614 / -1654 / 0.74 / 0.20 | -870 / -1644 / 0.63 / 0.07 | -1175 / -1473 / 0.66 / 0.21 | -467 / -337 / 0.83 / 0.42 | +1047 / +613 / 0.79 / 0.66 | -1798 / -1690 / 0.81 / 0.20 | -1485 / -1445 / 0.72 / 0.28 | -1783 / -1530 / 0.68 / 0.21 | -161 / -769 / 0.66 / 0.42 | -7008 / -6182 / 0.97 / 0.05 | +753 / -359 / 0.53 / 0.40 | +2527 / +2050 / 0.94 / 0.88 | +3465 / +3103 / 0.97 / 0.84 | +1232 / +1365 / 0.74 / 0.59 |
| LONDON (4) | -1123 / -1109 / 0.94 / 0.22 | -773 / -610 / 0.90 / 0.35 | -1571 / -1238 / 0.97 / 0.11 | -790 / -1173 / 0.73 / 0.17 | +382 / +120 / 0.51 / 0.56 | -630 / -655 / 0.84 / 0.47 | -913 / -879 / 0.82 / 0.25 | -2265 / -2488 / 0.79 / 0.18 | -611 / -531 / 0.81 / 0.38 | -4319 / -4510 / 1.00 / 0.00 | -133 / -362 / 0.79 / 0.35 | +84 / +32 / 0.73 / 0.41 | -500 / -270 / 0.64 / 0.45 | -957 / -189 / 0.48 / 0.49 |
| NY (nyam+nypm) (5) | -1379 / -1033 / 0.80 / 0.25 | +370 / +854 / 0.78 / 0.79 | -619 / -240 / 0.70 / 0.45 | -160 / -436 / 0.73 / 0.36 | +544 / +1063 / 0.80 / 0.75 | +245 / +118 / 0.77 / 0.67 | -52 / -43 / 0.72 / 0.47 | +2232 / +1958 / 0.87 / 0.78 | -41 / +52 / 0.87 / 0.61 | -1993 / -1877 / 0.78 / 0.27 | +252 / -153 / 0.84 / 0.44 | +2520 / +1728 / 0.83 / 0.85 | +179 / -770 / 0.62 / 0.41 | -3329 / -2998 / 0.90 / 0.13 |

Reading: in 2013-2022 the live cell is positive in 3.6 of 10 years on average (V0; per pair 1-8), the neighbourhood mean in 2.7; the whole grid flips sign together (mean share of grid cells positive by year ranges 0.00-1.00; ASIA/LONDON/NY blocks are net negative in most pre-2023 years and net positive in 2024-2025), so the live settings sit on a locally smooth plateau (neighbour sign agreement mean 0.78) that is a regime, not a stable edge. Descriptive: calibration < .90.

### 3. Walk-forward PARAMETER selector (trailing Calmar, purged) vs the live parameters, equal risk
Selectors per pair: S6 (monthly, trailing 6 months), S12 (monthly, trailing 12 months), Q12 (quarterly refit, trailing 12 months); candidates = the pair's parameter cells at the live bracket 60/60 (live cell held when fewer than 20/40 trades or no history); purge = window ends the previous month-end (intraday, flat 16:55). Statistic: weekly $ selector minus live on the same weeks, 4-week block bootstrap 95% CI, equal-risk difference (selector rescaled to the live cell's maxDD), P1 = random-parameter selector (1000 worlds), family p = max-t over all 42 selectors of the object/base in the P1 worlds. Bases named V0 / V2.

| object / era | base | selectors | mean diff $/wk (all) | mean diff, formal pairs | equal-risk diff (all) | diff > 0 | CI > 0 | CI < 0 | P1 p <= .10 | family p <= .10 | smallest family p |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1-min object, E1 (cross-check) | V0 | 42 | -17 | -132 (n 21) | +23 | 17 | 2 | 2 | 5 | 0 | 0.28 |
| 1-min object, E1 (cross-check) | V2 | 42 | -57 | -205 (n 21) | -67 | 14 | 0 | 1 | 5 | 0 | 0.84 |
| 1-min object, E2 2015-01..2023-03 (descriptive) | V0 | 42 | +15 | +34 (n 21) | +86 | 22 | 1 | 0 | 6 | 0 | 0.44 |
| 1-min object, E2 2015-01..2023-03 (descriptive) | V2 | 42 | +9 | +17 (n 21) | +21 | 21 | 0 | 0 | 2 | 0 | 0.58 |
| 1-s object, E1 2023-04..2026-10 (FORMAL for 7 pairs) | V0 | 42 | -139 | -253 (n 21) | -151 | 17 | 0 | 6 | 3 | 0 | 0.98 |
| 1-s object, E1 2023-04..2026-10 (FORMAL for 7 pairs) | V2 | 42 | -109 | -244 (n 21) | -126 | 18 | 0 | 5 | 4 | 0 | 0.81 |

Formal pairs, 1-s object, E1 (V0 | V2 mean weekly diff, equal-risk diff, P1 p, family p):

| pair | selector | live $/wk V0 | selector $/wk V0 | diff V0 [CI] | eq-risk diff V0 | P1 p V0 | family p V0 | diff V2 [CI] | eq-risk diff V2 | P1 p V2 | family p V2 | Calmar live / sel (V0) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| HM asia | S6 | +631 | +281 | -350 [-830,+110] | -484 | 0.95 | 1.00 | -175 [-720,+326] | -190 | 0.88 | 1.00 | 3.82 / 0.89 |
| HM asia | S12 | +781 | +466 | -315 [-837,+228] | -522 | 0.79 | 1.00 | -168 [-777,+370] | -331 | 0.82 | 1.00 | 3.92 / 1.30 |
| HM asia | Q12 | +781 | +447 | -334 [-1150,+404] | -512 | 0.81 | 1.00 | -126 [-655,+398] | -227 | 0.79 | 1.00 | 3.92 / 1.35 |
| KB asia | S6 | +500 | +239 | -261 [-911,+421] | -289 | 0.77 | 1.00 | -438 [-1049,+145] | -506 | 0.68 | 1.00 | 2.22 / 0.94 |
| KB asia | S12 | +603 | +313 | -290 [-1228,+630] | -383 | 0.71 | 1.00 | -740 [-1610,+113] | -823 | 0.91 | 1.00 | 2.22 / 0.81 |
| KB asia | Q12 | +603 | +218 | -386 [-1526,+683] | -401 | 0.78 | 1.00 | -1020 [-1889,-231] | -918 | 0.99 | 1.00 | 2.22 / 0.75 |
| KB london | S6 | +18 | -74 | -92 [-589,+449] | -80 | 0.68 | 1.00 | -86 [-600,+462] | -89 | 0.68 | 1.00 | 0.08 / -0.28 |
| KB london | S12 | +12 | -141 | -153 [-712,+390] | -136 | 0.75 | 1.00 | +241 [-283,+757] | +259 | 0.16 | 1.00 | 0.04 / -0.47 |
| KB london | Q12 | +12 | -233 | -244 [-952,+454] | -183 | 0.82 | 1.00 | +241 [-440,+959] | +214 | 0.17 | 1.00 | 0.04 / -0.64 |
| KB nypm | S6 | -25 | -64 | -39 [-604,+533] | -79 | 0.22 | 1.00 | -235 [-759,+320] | -254 | 0.41 | 1.00 | -0.06 / -0.26 |
| KB nypm | S12 | +8 | -468 | -475 [-1113,+125] | -444 | 0.83 | 1.00 | -444 [-1033,+95] | -427 | 0.78 | 1.00 | 0.02 / -0.89 |
| KB nypm | Q12 | +8 | -260 | -268 [-850,+351] | -300 | 0.56 | 1.00 | -93 [-693,+503] | -97 | 0.15 | 1.00 | 0.02 / -0.60 |
| PB asia | S6 | +739 | +712 | -26 [-395,+338] | -302 | 0.12 | 1.00 | +13 [-361,+378] | -311 | 0.04 | 1.00 | 12.45 / 7.37 |
| PB asia | S12 | +721 | +413 | -308 [-651,+3] | -525 | 0.88 | 1.00 | -147 [-462,+145] | -171 | 0.37 | 1.00 | 10.09 / 2.75 |
| PB asia | Q12 | +721 | +512 | -210 [-573,+129] | -472 | 0.66 | 1.00 | -392 [-863,-31] | -606 | 0.96 | 1.00 | 10.09 / 3.50 |
| SM asia | S6 | +380 | +74 | -305 [-706,+71] | -329 | 0.76 | 1.00 | -305 [-707,+73] | -329 | 0.74 | 1.00 | 4.24 / 0.56 |
| SM asia | S12 | +415 | +419 | +5 [-405,+394] | +16 | 0.11 | 1.00 | +5 [-418,+411] | +16 | 0.11 | 1.00 | 3.84 / 3.99 |
| SM asia | Q12 | +415 | +420 | +6 [-423,+396] | +16 | 0.10 | 1.00 | +6 [-409,+385] | +16 | 0.11 | 1.00 | 3.84 / 3.99 |
| SM london | S6 | +88 | -534 | -622 [-953,-292] | -173 | 0.99 | 1.00 | -622 [-960,-291] | -173 | 1.00 | 1.00 | 1.03 / -0.99 |
| SM london | S12 | +92 | -199 | -291 [-628,+65] | -166 | 0.59 | 1.00 | -291 [-636,+57] | -166 | 0.65 | 1.00 | 0.89 / -0.72 |
| SM london | Q12 | +92 | -260 | -352 [-679,-22] | -189 | 0.70 | 1.00 | -352 [-680,-43] | -189 | 0.71 | 1.00 | 0.89 / -0.93 |

Best single selector on the formal object (smallest P1 p, V0 / V2): V0 ('SM', 'asia') Q12 p1 0.097 fam 1.00 diff +6; V2 ('PB', 'asia') S6 p1 0.036 fam 1.00 diff +13

Win rule (pre-stated): positive equal-risk difference with CI above zero, per-selector P1 p <= .10 and family p <= .10 on BOTH V0 and V2, formal pair: met by NO selector or refit (formal 1-s object: 0 of 42 with CI above zero, 0 with family p <= .10). No refit rule is proposed for params_policy.txt.

**Plain paragraph (CHAR-C): On the NQ books the live parameters do not lose to any way of re-choosing them. The 13-year 1-minute map cannot carry a formal statement (1-min vs 1-s weekly correlation .66-.90, none reaching .90), so before 2023 the live cell is just a regime marker: positive in a minority of the ten years 2013-2022 and positive in 2024-25, with its whole parameter neighbourhood and nearly all grid cells flipping sign together. On the 1-s object for 2023-04..2026-10, the only formal evidence, a monthly or quarterly parameter chooser that picks the best trailing-6- or 12-month Calmar cell earns about $253 (V0) and $244 (V2) per week LESS than simply holding the live parameters, averaged over the 7 calibrated pairs (also less at equal risk), no selector has a confidence interval above zero, the smallest family p is 1.00, and in the 1-minute cross-check and the 2015-2023 descriptive era the differences are small and not distinguishable from the random-parameter placebo. So there is no refit rule for params_policy.txt: the evidence is that which settings paid in one year does not persist to the next, and the live settings are the settings that happened to pay in 2023-26.**Caveats of interim 4 (CHAR-C): (1) the live cell was chosen with hindsight on 2023-26, which biases the E1 comparison toward live; E2 (2015-2023, no such bias) is 1-min and descriptive, where the selectors are within noise of live (mean difference +15 V0 / +9 V2 per week, 1 of 42 CI above zero, family p .44 / .58); (2) the 1-s object only holds 2023-04 onward, so S6 starts testing in 2023-10 and S12/Q12 in 2024-04 (117-141 weeks); (3) the selector searches parameters at the live bracket only (brackets: ZL-2 interim 2, engine-true, also no refit rule); (4) engine-in-the-loop signal-parameter variation remains undone (multi-day library rebuild, ZL-2 interim 3), so 'formal' means the 1-s object tied to the engine at >= .90, not the engine itself.

## INTERIM 5 2026-11-06 (BASE-4, T2_NQ13_LOOP; scope l2vast/ds3/prereg/NQ13_ENGINE_LOOP_scope.md sha256 29fed921... logged in DECISIONS.md before any neighbour cell): ENGINE-IN-THE-LOOP signal-parameter neighbourhoods
Object: the V13T engine itself, all components off, lots 1, live cost frame; the signal library of ONE book is regenerated per parameter cell (rows -> raw events -> trade_index -> trades_arm -> universe/ER -> POI -> masks -> engine; 26 cell runs, about 2 min each). 22 neighbour cells (KB 6, SM 6, HM 6, PB 4) x pair sessions = 40 cell-sessions; first 935 label days 2023-04-03..2026-10-30, carrying weeks dropped. Cell cubes: /mnt/l2/l2vast/ds3_base4/nq13/<tag>.npz (keys cube_V0, cube_V2 shape 11x6x939, names, DAYS, WKd). Code: l2vast/ds3/code/blind/{cell_run,run_cells,nq13_loop,nq13_loop_an}.py. Outputs: l2vast/ds3/out/nq13_loop/{selector,plateau}.csv.
Tie-out (rule met before any neighbour was reported): live-parameter replications of KB, SM, HM, PB through the cell pipeline give the blind-tree live cube with max abs cell-day difference 0.0 on V0 and V2 (all four books). Deviation stated: for changed-signal cells the old-vs-new stored-array tie-outs inside the chain scripts (old tids as a sub-sequence of new, old flow columns) cannot apply and were disabled in the derived copies only; the live replications keep them. HM cells used the parameterised copy (hm_variant), which reproduces ev_A HM rows 20,484/20,484 below the old cap (ZL-2 check).
Selector (DS3_NQ13: trailing T = 6/12/24 months, total net $, min active days 5/10/20, fallback live, purged by month, 5,000-draw iid week bootstrap 90% CI, P1 = 2,000 random-cell-per-month worlds, family max-t over 21 selectors per base = 7 pairs x 3 T):
- V0: mean selector-minus-live -150 $/wk-unit; diff > 0 in 6 of 21; CI above zero in 1, CI below zero in 3; P1 p <= .10 in 1; family max t 1.83, family p .41.
- V2: mean -149 $/wk-unit; diff > 0 in 7 of 21; CI above zero in 1, below zero in 2; P1 p <= .10 in 1; family max t 1.83, family p .35.
- The one CI-above-zero selector on both bases is KB nypm T=24 (diff +348 $/wk, CI [+68,+671] V0, P1 p .099 V0 / .092 V2) on only 68 weeks, family p .41 / .35, and live nypm KB is itself negative (-188 $/wk in that window); NOT a lead. HM asia T=6 V0 (+319, CI -40..+677) and PB asia T=12 (+77, CI -8..+163) are positive without a CI above zero.
- Win rule (positive, CI above zero, P1 and family p <= .10 on both V0 and V2, tie-out passed): met by NO selector. No parameter-refit rule; params_policy.txt unchanged. Same conclusion as interims 1, 2 and 4, now with the signal-parameter dimension engine-true for the 7 formal pairs.
Plateau (description, not a test; neighbour mean weekly $ vs live, all non-carry weeks; V0 | V2 live / neighbour mean / share of neighbours below live): KB asia 226 / 350 / .33 | 316 / 328 / .50; KB london 146 / -20 / .83 both; KB nypm 88 / -64 / .67 both; SM asia 614 / 404 / 1.00 both (live above all six neighbours); SM london 55 / -117 / .83 both; HM asia 512 / 635 / .17 | 502 / 605 / .17 (live below 5 of 6 neighbours; bias note: live was chosen with hindsight); PB asia 1,024 / 929 / .50 | 1,092 / 968 / .50. The live cell is a local top in SM (both sessions), KB london/nypm and is not a ridge in HM and KB asia; per-year ranking of the live cell is unstable (neighbours above live by year in KB nypm: 6,0,5,4 of 6).
Approximations (stated): all-off object, so ER/zones/L2 stores of the changed book are rebuilt but do not enter P&L; 1 lot per row (no equal-risk scaling); the formal 7 pairs only; live cell chosen with hindsight biases every comparison toward live. Ledger: 40 rows T2_NQ13_LOOP appended to DEAD_CELLS.csv (val_HOLD = V0, val_X = V2 neighbour-minus-live $/wk). Blind-tree guard md5s unchanged after every batch; no data/live file read.
