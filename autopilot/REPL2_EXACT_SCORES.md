# REPL2 EXACT SCORES (W-PLAN-AS, 28 Nov 2026): corrected-key replacements for the drift books, exact engine, all 588 rows DONE

**ANSWER FIRST.** The replacements add income but do not make any session smoother. The only mix that holds the drawdown is Asia Ma1 (drift book MF4 replaced by `tsf_5_400` mmove retest): income +15% over the drift-removed mix (1,044,530 vs 909,638), weekly max DD -62.7k vs -66.4k (about equal, 6% better), worst week -36.2k vs -35.5k (1.8% deeper), L6M +13%, L3M +24%, NQ-down weeks +11%, every year up. It still fails the smoothness scorecard (smoother quarters 1 of 15, years 0 of 4), so it is an income add with the same risk, not a smoother book. NY AM and NY PM mixes raise income 17-30% but deepen max DD 14-60% (NY Y4 -250k vs -158k weekly; NP Z2 -76k vs -44k). Where the DD stays close to the reference (NP Z1: -52.6k vs -43.6k, worst week -27.2k vs -32.0k, income +22%) it is still deeper. All 8 alone books are positive in total; 4 of the 8 have a negative calendar year (Asia a2 2024, Asia a4 2023, NY n1 2024, NY n2 2024). Verdict: none of the 14 sets passes the scorecard; do not put any into the live mix on smoothness grounds; Asia Ma1 and NP Z1 are the two to keep as income adds if the trader wants income and accepts the same-sized risk. These stand as the exact engine's result with live Trade Health deciding; nothing here is a quick screen.

Reference = the drift-removed mix of the same session (`TL3_DX_<S>_MIX_c`; the drift books deleted, nothing added). Dollars, 42 months, weekly figures from the daily series, NQ-down weeks = the 77 valid weeks with NQ close-to-close change <= 0.

## Per set (income, weekly max DD, worst week, L6M = May-Oct 2026, L3M = Aug-Oct 2026, income in NQ-down weeks, income by year; 2026 = Jan-Oct)
| set | income | max DD (weekly) | worst week | L6M | L3M | NQ-down weeks income | 2023 | 2024 | 2025 | 2026 |
|---|---|---|---|---|---|---|---|---|---|---|
| AS_MIX_c (REFERENCE drift-removed mix) | 909638 | -66365 | -35545 | 458635 | 141925 | 383162 (77 wk) | 57697 | 203905 | 139140 | 508896 |
| AS_REPL2_a1_A | 272297 | -20179 | -6464 | 138114 | 64131 | 121726 (77 wk) | 14348 | 27358 | 50190 | 180401 |
| AS_REPL2_a2_A | 207342 | -41014 | -17467 | 129207 | 26578 | 198596 (77 wk) | 4549 | -4346 | 37938 | 169200 |
| AS_REPL2_a3_A | 319452 | -42881 | -29769 | 170486 | 5953 | 217666 (77 wk) | 13458 | 70247 | 18022 | 217725 |
| AS_REPL2_a4_A | 272297 | -47513 | -20343 | 151770 | 18488 | 173982 (77 wk) | -1057 | 2658 | 116375 | 154320 |
| AS_REPL2_Ma1_M | 1044530 | -62710 | -36185 | 519179 | 175276 | 424928 (77 wk) | 66641 | 221696 | 172238 | 583954 |
| AS_REPL2_Ma2_M | 986202 | -68405 | -39729 | 480100 | 141952 | 437457 (77 wk) | 58700 | 205050 | 163993 | 558459 |
| NY_MIX_c (REFERENCE drift-removed mix) | 2234172 | -157774 | -92427 | 990095 | 339389 | 1256832 (77 wk) | 258657 | 328481 | 608070 | 1038964 |
| NY_REPL2_n1_A | 402692 | -86572 | -19053 | 138466 | 48845 | 150682 (77 wk) | 48922 | -1655 | 206159 | 149266 |
| NY_REPL2_n2_A | 354922 | -96908 | -21668 | 131772 | 39858 | 67115 (77 wk) | 35606 | -30525 | 210809 | 139032 |
| NY_REPL2_Y4_M | 2900791 | -249922 | -109984 | 1229625 | 396219 | 1482753 (77 wk) | 417075 | 338040 | 875063 | 1270612 |
| NY_REPL2_Y2_M | 2615925 | -220527 | -109676 | 1143262 | 373863 | 1323944 (77 wk) | 322361 | 303504 | 857321 | 1132739 |
| NP_MIX_c (REFERENCE drift-removed mix) | 928583 | -43625 | -32018 | 242779 | 135645 | 525487 (77 wk) | 163898 | 151982 | 307062 | 305640 |
| NP_REPL2_p1_A | 451014 | -73451 | -22161 | 140337 | 2806 | 230733 (77 wk) | 77138 | 24156 | 186175 | 163546 |
| NP_REPL2_p2_A | 477460 | -50096 | -32111 | 135897 | 19182 | 193908 (77 wk) | 81851 | 181110 | 73009 | 141490 |
| NP_REPL2_Z2_M | 1273021 | -75681 | -32806 | 343812 | 142116 | 712049 (77 wk) | 193215 | 262639 | 435241 | 381925 |
| NP_REPL2_Z1_M | 1133229 | -52602 | -27163 | 288148 | 123310 | 658186 (77 wk) | 200621 | 197338 | 392027 | 343244 |


## Mixes against the drift-removed mix, W-DYNQ smoothness scorecard (`ar_score`; managed vs reference)
| subject | stream (managed vs reference) | worst week | winning weeks | st.dev. weekly income | biggest give-back | trades giving back > 50% of peak (all / peak >= $1k) | max DD | income | smoother quarters: all / NQ-up / NQ-down | smoother years: all / up / down | ACCEPTABLE at floor 10% / 20% / 30% | slot effects: entries only in the managed run (n, net $) / only in the bracket run (n, net $) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AS | TL3_DX_AS_REPL2_Ma1_M vs TL3_DX_AS_MIX_c | -36,185 / -35,545 | 62% / 63% | 17,955 / 17,233 | 12,029 / 13,124 [best_px (engine MFE) / 1-s tape] | 3038 / 1158  vs  2686 / 1304 | -66,418 / -66,365 | 1,020,055 / 887,515 | 1/15, 3/13, 1/13 | 0/4, 0/4, 0/4 | no / no / no | 952 (156,061) / 19 (12,255) |
| AS | TL3_DX_AS_REPL2_Ma2_M vs TL3_DX_AS_MIX_c | -39,729 / -35,545 | 62% / 63% | 18,779 / 17,233 | 12,029 / 13,124 [best_px (engine MFE) / 1-s tape] | 3098 / 1256  vs  2686 / 1304 | -80,907 / -66,365 | 975,332 / 887,515 | 2/15, 3/13, 2/13 | 0/4, 1/4, 0/4 | no / no / no | 948 (113,223) / 27 (26,215) |
| NY | TL3_DX_NY_REPL2_Y4_M vs TL3_DX_NY_MIX_c | -109,984 / -92,427 | 63% / 62% | 47,619 / 41,747 | 28,674 / 30,988 [best_px (engine MFE) / 1-s tape] | 6100 / 3039  vs  4348 / 2619 | -309,356 / -217,943 | 2,888,897 / 2,230,401 | 1/15, 3/13, 1/13 | 0/4, 0/4, 0/4 | no / no / no | 3680 (705,585) / 73 (8,832) |
| NY | TL3_DX_NY_REPL2_Y2_M vs TL3_DX_NY_MIX_c | -109,676 / -92,427 | 63% / 62% | 45,938 / 41,747 | 28,674 / 30,988 [best_px (engine MFE) / 1-s tape] | 5223 / 2880  vs  4348 / 2619 | -277,159 / -217,943 | 2,602,817 / 2,230,401 | 2/15, 2/13, 3/13 | 0/4, 0/4, 0/4 | no / no / no | 1984 (403,348) / 61 (-3,620) |
| NP | TL3_DX_NP_REPL2_Z2_M vs TL3_DX_NP_MIX_c | -32,806 / -32,018 | 67% / 66% | 14,415 / 12,308 | 24,155 / 25,005 [best_px (engine MFE) / 1-s tape] | 2325 / 1023  vs  842 / 551 | -89,367 / -55,701 | 1,244,130 / 903,401 | 1/15, 2/13, 2/13 | 0/4, 0/4, 1/4 | no / no / no | 2762 (380,454) / 119 (47,284) |
| NP | TL3_DX_NP_REPL2_Z1_M vs TL3_DX_NP_MIX_c | -27,163 / -32,018 | 69% / 66% | 13,014 / 12,308 | 24,155 / 25,005 [best_px (engine MFE) / 1-s tape] | 1502 / 753  vs  842 / 551 | -73,880 / -55,701 | 1,110,541 / 903,401 | 2/15, 3/13, 2/13 | 0/4, 1/4, 1/4 | no / no / no | 1272 (241,320) / 88 (41,024) |

Read: "smoother quarters all/up/down" counts quarters where the set has the smaller drawdown than the reference (of 15/13/13); "ACCEPTABLE" = no at every floor. The slot-effect column shows the mixes add 950-3,700 entries that exist only in the replacement run: that is the income, and the extra drawdown comes with it.

## Notes
- Events: `REPL2_*` files; sets `TL3_DX_{AS,NY,NP}_REPL2_*`; scorer `code/th_planas/score_repl2.py`.
- Earlier REPLACE_CANDIDATES.md and REPL_EXACT_SCORES.md are for merged streams (wrong key); this page is for the corrected key.
- Luck: net-of-chance counts (Asia 134, NY AM 34, NY PM 15, London 0) apply to the pool; these 8 picks were the best of their session by the same-day filter, so some selection bias remains in the ranking (not in the exact numbers).
