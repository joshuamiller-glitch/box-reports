# QUALIFIER ROWS + LONDON SLEEVE, EXACT SCORES (W-PLAN-AS, 28 Nov 2026 13:11Z)

**ANSWER FIRST.** (1) London sleeve: ONE of three sleeves passes the rule I fixed before scoring: s4 (t3_dltor_B200 structure_breakout n10 45/45 added beside the unchanged live London mix): income 1,091,511 vs 913,621 (+19%), weekly max DD -195.3k vs -213.2k (8% shallower), worst week -100.2k vs -107.4k (better), L6M +9%, L3M +15%, every year up (2025 +182%). s1 and s2 (vrb_700 pullback_st arm10 / arm30 45/45) add +23% / +24% income and leave max DD equal (-210.9k / -214.0k) but the worst week is 5.3% deeper (-113.0k vs -107.4k), so they fail. Three variants were tried and s4 is the best of three, and s4's own screen evidence is the weakest of the three (short side z 1.9, below the stage-2 qualifier line), so it is a LEAD candidate with no chance cover, not a proven book; the W-DYNQ scorecard still says no (smoother quarters 2/15, years 0 to 1 of 4). (2) The 163 qualifier rows (alone, bare, 2 lots, best two brackets) mostly confirm the screen: of 161 scored, 146 pass the pre-registered survivor rule, so the rule does not separate winners from luck: the sets were chosen on the same history. What separates them is drawdown per income. (3) Queue: 2,646 more rows queued (mix 294 + g67a70/tr100 sisters 2,352); queue 8.8k lines after queueing.

Reference for the sleeves is the live London mix (TL3_SR_LO_STKd8w42lo_FSffb8_BARE). Rule (fixed before scoring, 3 variants declared): max DD and worst week not deeper by more than 5%, income higher, L6M and L3M not lower, no year lower.

| set | income | max DD (weekly) | worst week | L6M | L3M | NQ-down weeks | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|
| LIVE London mix (REFERENCE) | 913621 | -213180 | -107350 | 528187 | 234166 | -112020 | 108752 | 228921 | 59830 | 516117 |
| LO_SLV_s1_M | 1123572 | -210871 | -113000 | 621255 | 291775 | -12165 | 140866 | 276208 | 69174 | 637325 |
| LO_SLV_s2_M | 1131393 | -214046 | -113000 | 623071 | 290080 | 136 | 140566 | 277893 | 77789 | 635146 |
| LO_SLV_s4_M | 1091511 | -195269 | -100171 | 574782 | 270396 | -45695 | 116978 | 267891 | 168936 | 537707 |

Sleeve rows: all 126 DONE. Qualifier rows: 6,846 of 6,846 DONE (2 of 163 sets have no daily series: zero trades). Scorer code/th_planas/score_q.py (alone sets, writes /mnt/l2/l2vast/_dynexit/Q_scores.csv with every set's income, DD, worst week, L6M, L3M, side incomes, by year) and score_slv.py.

## Survivor rule (fixed before scoring) and result by session
Both sides income > 0, L6M > 0, L3M > 0, at least 3 of 4 calendar years positive, weekly max DD <= 35% of income. Survivors: Asia 96 of 109, London 5 of 5, NY PM 20 of 22, NY AM 25 of 25. 160 of 161 have positive income. The best by income per unit of weekly drawdown (the selection used for the next rows): London QLO005 (vrb_700 arm30 45/45), QLO001 (dol_2600); NY AM QNY003 (dchg_20 book_cancel ratio_follow 120/120, 693k, DD -52k), QNY016, QNY023, QNY009, QNY025, QNY006, QNY007, QNY014; NY PM QNP001 (cusum_10 vwap retest 30/30, 469k, DD -21.5k), QNP008, QNP009, QNP010, QNP003, QNP005; Asia QAS005, QAS034, QAS078, QAS023, QAS025, QAS079, QAS037, QAS011, QAS022, QAS006, QAS013, QAS076 (profile_nodes and piv_floor break families dominate). Full table in Q_scores.csv; the manifest of cells is Q_manifest.tsv.

## Queued next (28 Nov ~13:11Z): 2,646 rows
- Mixes (survivors in place of the drift slots, same layout as REPL2): NY AM Qy5 (5 slots), Qy3, Qy1; NY PM Qz2, Qz1; Asia Qa1, Qa3: 7 sets, 294 rows (rows_c0_q2_mix.txt).
- Sister rows for the 28 selected survivors: g67a70 and tr100 (no target, own stop, ratchet exits as built by W-SUNDAY-LS, tr trails 1.0 x stop distance) as alone bare sets: 56 sets, 2,352 rows (rows_c0_q2_ls_1, _2).
- Item 4 (widened London search) not started: London needs new event files for other bar sizes (only vrb_700 has pullback_st events in the library) before a wider search is possible; the corrected pool already holds every stage-1 passer.

## PROVEN LIST (28 Nov 13:30Z): passes survivor rule AND same-day null (>= 0.90 per side) AND exact engine

Counts (scored sets): Asia 109 scored, 96 survive, 68 same-day, **64 proven**; London 5, 5, 2, **2 proven**; NY AM 25, 25, 25, **25 proven**; NY PM 22, 20, 12, **12 proven**. Total 103 of 161. Same-day null = real signals vs the same bell/day with random time and permuted sides (from cand_sameday_r). Caveat: the same-day null was run on stage-2 qualifiers, so "25 of 25" for NY AM means every NY AM qualifier beat it, not that the null is easy. Not yet charged: the 3.2 / 4.8 / 4.2 / 7.8 qualifiers expected by chance per session (so about 3%, 96%, 12%, 34% of the sets in Asia, London, NY AM, NY PM may be luck: London 5 vs 4.8 expected, i.e. London proven is not above chance).

Top picks per session (ranked by income / |weekly max DD|, one per cell family, proven only):

| session | set | cell | bracket | income | weekly max DD | worst week | L6M | L3M | same-day L / S |
|---|---|---|---|---|---|---|---|---|---|
| LO | QLO001 | dol_2600\|trig_structure_inside\|outside\|{"cf": 0.75, "filt": 20} | 10/60 | 86476 | -12973 | -6548 | 20619 | 6967 | 0.99 / 1.00 |
| LO | QLO004 | vrb_700\|trig_pullback_st\|st\|{"arm": 30, "ema": 30, "st_mult": 3.0} | 20/20 | 134745 | -21017 | -7442 | 57702 | 44157 | 1.00 / 0.95 |
| NY | QNY003 | dchg_20\|trig_book_cancel\|ratio_follow\|{"L": 200, "z": 1.0} | 120/120 | 693449 | -52417 | -34500 | 195031 | 18891 | 1.00 / 1.00 |
| NY | QNY016 | tib_10000\|trig_levels_trendline\|reject_native\|{"conf": "close", "tol": 0.0} | 30/30 | 258309 | -21229 | -11100 | 84456 | 33222 | 0.98 / 0.98 |
| NY | QNY023 | vrb_40000\|trig_levels_fibr_or\|break_native\|{"k": 0.25, "n": 3} | 60/60 | 244004 | -23156 | -9473 | 82073 | 22832 | 1.00 / 0.99 |
| NY | QNY009 | nbtop_NYAM\|drb_25000\|trig_levels_round\|break_native\|{"k": 0.5, "n": 2} | 10/90 | 97327 | -10664 | -6419 | 31633 | 13765 | 1.00 / 1.00 |
| NY | QNY025 | vrb_40000\|trig_levels_fibr_or\|break\|{"k": 0.5, "n": 3} | 60/30 | 174349 | -24189 | -7498 | 45051 | 20965 | 1.00 / 0.96 |
| NP | QNP009 | nbtop_NYPM\|kal_rngor_B080\|trig_momentum_stoch\|revert_native\|{"len": 14, "lvl": 15} | 30/30 | 192681 | -10302 | -4885 | 43782 | 12265 | 1.00 / 0.97 |
| NP | QNP010 | nbtop_NYPM\|vsess_80\|trig_structure_level\|round_reject\|{"buf": 0.5, "grid": 50} | 10/60 | 99098 | -6544 | -4722 | 19081 | 6913 | 1.00 / 0.96 |
| NP | QNP003 | dlt_30\|trig_levels_trendline\|break\|{"k": 0.5, "n": 3} | 90/30 | 345291 | -33028 | -19992 | 96796 | 5465 | 1.00 / 0.92 |
| NP | QNP007 | dol_750\|trig_levels_trendline\|reject_native\|{"conf": "body", "tol": 0.5} | 90/90 | 477460 | -50096 | -32111 | 135897 | 19182 | 1.00 / 0.99 |
| NP | QNP016 | tm60\|trig_levels_trendline\|reject_native\|{"conf": "body", "tol": 1.0} | 120/120 | 490579 | -59237 | -22161 | 135062 | 1661 | 1.00 / 1.00 |
| AS | QAS005 | cusum_80\|trig_levels_profile_nodes\|break_native\|{"k": 0.0, "n": 1} | 10/60 | 242529 | -5765 | -5664 | 99244 | 24198 | 1.00 / 1.00 |
| AS | QAS034 | rng_80\|trig_levels_profile_nodes\|break_native\|{"k": 0.0, "n": 1} | 10/60 | 241159 | -6698 | -6450 | 98956 | 24838 | 1.00 / 1.00 |
| AS | QAS078 | urenko_56\|trig_levels_profile_nodes\|break_native\|{"k": 0.0, "n": 1} | 45/45 | 406773 | -11698 | -10737 | 160911 | 70023 | 1.00 / 1.00 |
| AS | QAS023 | mom_56\|trig_levels_piv_floor\|break\|{"k": 0.5, "n": 1} | 80/40 | 463263 | -14473 | -11956 | 182905 | 51921 | 1.00 / 0.91 |
| AS | QAS079 | urenko_56\|trig_levels_profile_nodes\|break\|{"k": 0.25, "n": 1} | 45/45 | 397786 | -15528 | -10638 | 158744 | 62670 | 1.00 / 0.99 |
| AS | QAS037 | rng_80\|trig_levels_profile_nodes\|break\|{"k": 0.5, "n": 1} | 10/60 | 240758 | -10050 | -10050 | 106719 | 22250 | 1.00 / 1.00 |
| LO | **s4 SLEEVE** (add t3_dltor_B200 breakout n10 45/45 beside live London) | | 45/45 | +178k over live (1,091,511 vs 913,621) | -195.3k vs -213.2k | -100.2k vs -107.4k | +9% | +15% | not a qualifier: **LEAD WITHOUT CHANCE COVER** |

## SURVIVORS IN THE MIX + SISTER ROWS (28 Nov, exact, vs the drift-removed mix of each session)
Mixes (reference TL3_DX_<S>_MIX_c): income / weekly max DD / worst week / L6M / L3M / year income in thousands 2023-2026.
- **NY PM Qz2** (MF1 <- QNP001 cusum_10 vwap retest 30/30, MF4 <- QNP008 mrenko_14 fib15 retest 30/30): 1,346,195 vs 928,583 (+45%); weekly DD -37.9k vs -43.6k (13% shallower); worst week -25.6k vs -32.0k (20% better); L6M +44%; L3M +28%; years 237/259/422/428 vs 164/152/307/306 (all up). Scorecard: max DD equal, smoother quarters 3/15, ACCEPTABLE no. **But both books FAIL the same-day null on the short side (QNP001 0.50, QNP008 0.74): lead without chance cover.** Qz1 (MF1 <- QNP001 only): 1,135,567 (+22%), DD -43.9k equal, worst week -24.2k (24% better), same flag.
- **NY AM Qy5 / Qy3 / Qy1** (drift slots <- QNY003, 016, 023, 009, 025 ...; all proven): income +35% / +27% / +13% (3,024,290 / 2,828,895 / 2,517,866 vs 2,234,172), worst week better (-84.8k / -80.4k / -77.1k vs -92.4k) but weekly max DD 20-24% deeper (-195k / -191k / -190k vs -158k): fail drawdown.
- **Asia Qa1** (MF4 <- QAS005 profile_nodes 10/60; Qa3 is identical to Qa1: Asia has one drift slot): income +15% (1,045,187), DD -63.3k vs -66.4k (5% better), worst week -38.5k vs -35.5k (8% deeper): fails by the 5% rule.
- **Proven-only NP mixes queued**: Qp2 (QNP009 + QNP003), Qp1 (QNP009): 84 rows.
Sister rows (g67a70 and tr100, no target, own stop, 55 of the 56 sets scored; "win" = DD and worst week not more than 5% deeper, income >= 90%, L6M and L3M > 0): g67a70 wins 6 of 27 (Asia 2 of 12, NY AM 2 of 7, NY PM 2 of 6, London 0 of 2), tr100 wins 3 of 28; median DD with g67a70 is shallower in Asia (-13.6k vs -14.2k), NY PM (-19.4k vs -23.7k) and NY AM (-21.0k vs -23.2k) but deeper in London; tr100 makes DD deeper in all four sessions (NY AM -44.7k vs -23.7k). No ratchet rule is a robust improvement; g67a70 is the only one that helps drawdown on average. Table: /mnt/l2/l2vast/_dynexit/Q2_ls_scores.csv. The remaining proven books (80 sets, 6,720 sister rows) are queued.
