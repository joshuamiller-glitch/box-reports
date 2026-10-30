# DS3_ENSEMBLE - the weak-signal ensemble: every LEAD / CANDIDATE / CANDIDATE-RECENT rule since 10-27 voting with a shrunken trailing weight (agent ENSM, T-MISSED section 3 and 6), 2026-10-30
Research only; UNTOUCHED never read; no live/execution change. Prereg `autopilot/ENSEMBLE_prereg.md` (sha256 in DECISIONS.md; amendments A1 shrinkage centred on 0, A2 post-hoc 'MATCHED' lot re-matching, A3 post-hoc 'CAPPED' multipliers; all logged before the rows they define were read, headline rows are the preregistered ones). Own masks capped at 20260206: 2026 = 20260101..20260206 (**about 5 real weeks: read as a sign**), L6M = 20250801..20260206, HOLD = 20250701..20260206, PRE = 20240201..20250630, X' = 20230401..20240131 (the first 13 weeks of X' have no fit window and equal the stack as is); every frame filtered to label day <= 20260206; s48score.WINMASK / vs_lib.WINS never used.
Units: STACK $/week of the six lock-engine books ST HM WT KB SM PE at live lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6) through the exact engine of DS3_L2SET_JOINT (`ls_engine` / `de_engine.run_rows` + `lj_kernel.jrun`; busy rule and day/week locks re-applied on the modified rows); delta = ensemble minus the stack as it is on the same basis; (MDE80 = 2.8 x SD(weekly delta) / sqrt(weeks)) beside every number. **M** = measured fills (target-fill correction 1.4/1.5/4.2/4.3 pt charged on every target fill, an early market exit does not pay it); **N** = no target correction. PB DN MV MA have no lock engine and are not in the stack line.

## 0. The answer
**The sum of the small things is worth -18.0k $/wk out of sample on the last six months (MDE 67.8k) on the measured basis, -10.6k on HOLD (MDE 73.8k), -47.7k on the N basis (L6M, MDE 68.4k)** - for the preregistered ensemble of all 139 regenerable rules (weekly empirical-Bayes weights, trailing 3 months, closed trades only). That is not distinguishable from zero and the sign is negative; it is not 'zero because the rules are useless' but 'zero or negative because acting on them costs more than their noise earns'.
* Honest set only (rules identified on PRE-only data): L6M -16.9k (71.2k), HOLD -6.4k (76.0k), PRE -17.7k (29.0k); so the looked-data rules add nothing the honest ones lack.
* Shuffled-label placebo (the same decisions re-assigned to random trades of the same book and week, 20 draws): L6M placebo mean -20.5k (SD 2.7k) vs real -18.0k: rank 0.80. Random-rule-subset placebo (200 draws from the stored result tables, proxy without locks): L6M -18.2k real vs +27.4k (SD 51.1k), rank 0.17; N basis rank 0.33.
* Single best (rule, book) re-selected every month on trailing raw means: L6M -7.6k (58.4k), HOLD -0.7k (57.5k).
* Where the damage and the gain are (preregistered ensemble, M; N in the full table): multiplier side (filters/halve/double) -24.5k (67.0k) L6M, profit-exit side -3.1k (29.9k) (N -19.6k (30.5k): the take-at-70% family is the target-fill artefact), loss-exit side +14.0k (35.3k) (N +10.3k (36.0k)), entry side +12.7k (31.5k) (N +7.8k (22.7k)). Loss-exit + entry rules only: L6M +20.5k (47.6k), HOLD +18.5k (41.7k), 2026 +22.3k (201.9k) on M and +12.6k (40.6k) / +11.8k (36.8k) on N, **but PRE -9.6k (15.2k) (N -11.3k (20.5k))** - positive only in the windows in which its rules were found (post-hoc composition of attribution rows, CANDIDATE-RECENT at most).
* Why the full ensemble loses: with 139 rules, a positive shrunken weight is easy to get and the vote is a union; in the M run it exits 14,618 of 29,800 stack trades early, skips 10,748 of them and changes the size of 11,371. The shuffled placebo (same rates, random trades) loses almost the same amount, i.e. the loss is the cost of acting, the information content over chance is +2.5k $/wk (about 0.9 placebo SD).

## 1. Catalogue (out/missed/rule_catalogue.csv)
710 rows: program, cell id, side, book, session, honest vs looked-data flag, source report, how to regenerate, regenerated. **139 could be regenerated as per-trade rules on the six stack books (20%); 571 are catalogue-only**: reasons below. The expected 100-200 rules are met by the 139 regenerated ones.
| program | regenerated | catalogue-only |
|--|--|--|
| ABRC1 | 0 | 1 |
| ADDUW | 0 | 382 |
| DIPENTRY | 0 | 29 |
| EXP1 | 3 | 1 |
| L2EA | 26 | 0 |
| L2ENTRY_B | 0 | 49 |
| L2SE | 13 | 0 |
| L2SL | 13 | 0 |
| L2SP | 19 | 0 |
| SESSION2 | 0 | 107 |
| THL2 | 59 | 0 |
| THL_HM | 0 | 2 |
| THPC1 | 3 | 0 |
| THPC2 | 3 | 0 |
Catalogue-only reasons: DIPENTRY (29 CANDIDATE-RECENT cells) and ADDUW (382 B2 cells flagged cand_recent_full, WT 342+) are entry/add simulators whose cell tables store NET per trade but no exit second, so they cannot enter the lock engine (they stay in the proxy universe of the random-subset placebo through the L2SE grid that re-implements the same F1/F5 mechanics); L2ENTRY_B (49 cells) and SESSION2/T-OPEN (107 registered session/cluster cells) are separate trade-generating books, not rules on the six stack books (they belong to a book-set question); ABRC1 (bracket choice) needs path re-simulation of the new bracket; HM a30_w10 / a30_w20 (THL_HM) store dM/dN per HM trade but no exit second (hm9.npz) - the registered forward primary is therefore NOT in the ensemble; EXP1 vol_lo+ON take@50% lead is a post-look fixed-action stream not stored per trade. Honest vs looked counts of the regenerated rules: LOOKED-DATA 85, HONEST(PRE-identified) 54.

## 2. Stack lines, recent first (M and N, MDE beside every number)
Preregistered rows first; every row below the line 'sensitivity / post-hoc' is labelled and tier-capped at CANDIDATE-RECENT. Tier: PASS needs L6M HOLD PRE X' > 0 on M and N, CI(PRE) lower > 0, placebo (a) and (b) rank >= 0.95, and beating the single best monthly rule; a gate whose test was not run counts as failed.
| variant | 2026 (~5 wk) M | L6M M | HOLD M | PRE M | X' M | L6M N | HOLD N | PRE N | tier | failed gates |
|--|--|--|--|--|--|--|--|--|--|--|
| ALL | +20.7k (215.7k) | -18.0k (67.8k) | -10.6k (73.8k) | -19.9k (32.9k) | -8.2k (28.4k) | -47.7k (68.4k) | -33.5k (70.3k) | -39.8k (36.4k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) rank 0.80, placebo(b) rank 0.17, beats single-best(L6M), beats single-best(HOLD) |
| HONEST | +19.4k (213.3k) | -16.9k (71.2k) | -6.4k (76.0k) | -17.7k (29.0k) | +1.0k (26.5k) | -48.2k (71.5k) | -34.1k (74.8k) | -32.9k (33.1k) | DEAD | L6M(M), HOLD(M), PRE(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) rank 0.90, placebo(b) rank 0.15, beats single-best(L6M), beats single-best(HOLD) |
| ALL_PRUNED | +20.7k (215.7k) | -17.2k (64.2k) | -11.8k (70.4k) | -15.7k (29.4k) | -8.1k (26.7k) | -43.5k (68.5k) | -29.2k (69.6k) | -37.1k (35.8k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| HONEST_PRUNED | +14.1k (210.1k) | -4.6k (65.4k) | +2.1k (70.4k) | -13.8k (26.3k) | -0.5k (25.8k) | -36.9k (69.0k) | -22.8k (71.0k) | -29.5k (30.3k) | DEAD | L6M(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| *sensitivity / post-hoc (tier capped)* | | | | | | | | | | |
| looked-data rules only (85 rules) | +44.3k (225.8k) | +4.5k (67.3k) | +5.4k (67.9k) | -11.7k (31.2k) | -14.0k (25.7k) | -8.3k (65.3k) | -1.6k (57.8k) | -29.6k (33.4k) | CANDIDATE-RECENT | PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| ALL, original var-about-mean shrinkage (EBVAR) | +20.7k (215.7k) | -18.1k (68.1k) | -9.7k (70.0k) | -17.3k (29.3k) | -2.5k (26.8k) | -39.0k (71.0k) | -26.4k (72.3k) | -31.5k (32.0k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| ALL, quorum 50% aggregation | +20.7k (215.7k) | -19.3k (68.0k) | -11.5k (70.1k) | -8.7k (26.3k) | -4.4k (25.4k) | -47.4k (71.8k) | -33.2k (72.8k) | -24.3k (27.4k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| ALL, causal lot re-matching (A2) | +20.7k (215.7k) | -18.4k (69.3k) | -10.7k (74.5k) | -22.5k (37.1k) | -3.4k (35.0k) | -52.8k (73.1k) | -38.8k (74.1k) | -42.8k (37.5k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) rank 0.40, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| HONEST, causal lot re-matching (A2) | +23.3k (223.4k) | -15.4k (74.6k) | -4.0k (78.6k) | -13.3k (30.9k) | +4.2k (32.5k) | -43.5k (78.0k) | -28.4k (78.8k) | -30.1k (33.8k) | DEAD | L6M(M), HOLD(M), PRE(M), L6M(N), HOLD(N), PRE(N), CI(PRE lo>0), placebo(a) rank 0.85, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| ALL, multipliers capped 2x (A3) | +42.0k (215.1k) | +15.0k (58.7k) | +7.7k (62.2k) | -22.2k (28.5k) | -13.9k (23.7k) | -18.6k (76.2k) | -19.8k (70.1k) | -38.8k (35.3k) | CANDIDATE-RECENT | PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(b) n/r |
| HONEST, multipliers capped 2x (A3) | +23.0k (176.4k) | +3.2k (53.1k) | -1.1k (56.2k) | -21.0k (23.9k) | -8.4k (22.5k) | -3.2k (52.5k) | -5.5k (52.6k) | -23.1k (27.6k) | CANDIDATE-RECENT | HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(b) n/r, beats single-best(HOLD) |
| ALL capped, threshold 0.5 pt | +27.9k (129.8k) | +2.5k (38.5k) | -4.5k (42.9k) | -4.6k (18.8k) | -3.5k (12.0k) | +9.1k (43.2k) | +7.0k (37.9k) | -18.1k (24.0k) | CANDIDATE-RECENT | HOLD(M), PRE(M), X(M), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(HOLD) |
| HONEST capped, threshold 0.5 pt | +28.9k (121.4k) | -6.2k (41.6k) | -11.1k (44.5k) | -5.9k (19.4k) | -1.8k (8.8k) | +4.4k (36.2k) | +2.6k (31.8k) | -7.6k (20.2k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(HOLD) |
| ALL capped, threshold 1 pt | +22.7k (77.3k) | +3.7k (23.3k) | -1.3k (36.6k) | -5.7k (16.7k) | -0.9k (8.2k) | -1.0k (27.9k) | -2.1k (24.6k) | -17.3k (20.1k) | CANDIDATE-RECENT | HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(HOLD) |
| HONEST capped, threshold 1 pt | -23.1k (34.6k) | -13.1k (25.9k) | -13.3k (32.2k) | -7.6k (17.2k) | +1.0k (6.6k) | -5.5k (23.5k) | -4.8k (20.5k) | -11.1k (15.3k) | DEAD | L6M(M), HOLD(M), PRE(M), L6M(N), HOLD(N), PRE(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| ALL without the multiplier side | +42.0k (215.1k) | +13.6k (55.3k) | +6.5k (59.7k) | -17.2k (27.0k) | -9.7k (20.4k) | -2.9k (49.8k) | -1.8k (44.5k) | -35.0k (30.3k) | CANDIDATE-RECENT | PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| HONEST without the multiplier side | +23.0k (176.4k) | +6.0k (46.6k) | +3.0k (48.5k) | -14.9k (23.5k) | -4.5k (17.2k) | +2.8k (43.9k) | +4.9k (40.2k) | -27.5k (27.3k) | CANDIDATE-RECENT | PRE(M), X(M), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| ALL loss-exit + entry only | +22.3k (201.9k) | +20.5k (47.6k) | +18.5k (41.7k) | -9.6k (15.2k) | +4.9k (17.3k) | +12.6k (40.6k) | +11.8k (36.8k) | -11.3k (20.5k) | CANDIDATE-RECENT | PRE(M), PRE(N), CI(PRE lo>0), placebo(b) n/r |
| HONEST loss-exit + entry only | +24.5k (155.7k) | +14.0k (40.2k) | +12.7k (35.5k) | -8.5k (15.5k) | +4.8k (15.8k) | +6.9k (42.1k) | +8.5k (38.7k) | -9.1k (20.2k) | CANDIDATE-RECENT | PRE(M), PRE(N), CI(PRE lo>0), placebo(b) n/r |
| ALL loss-exit + entry only, pruned w>=0.1 | +22.7k (202.2k) | +20.4k (44.9k) | +17.2k (39.4k) | -11.0k (14.7k) | +2.6k (17.2k) | +16.4k (36.6k) | +15.3k (32.9k) | -11.3k (18.7k) | CANDIDATE-RECENT | PRE(M), PRE(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| HONEST loss-exit + entry only, pruned w>=0.1 | +25.5k (153.0k) | +14.2k (38.9k) | +12.1k (34.2k) | -10.3k (14.2k) | +3.2k (16.4k) | +13.0k (39.1k) | +14.1k (35.6k) | -11.8k (18.8k) | CANDIDATE-RECENT | PRE(M), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| *attribution by side (ALL, one side at a time)* | | | | | | | | | | |
| ALL_profit | +10.6k (110.6k) | -3.1k (29.9k) | -9.1k (42.5k) | -15.8k (25.5k) | -11.9k (15.1k) | -19.6k (30.5k) | -17.1k (26.9k) | -38.0k (29.9k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(HOLD) |
| ALL_loss | +15.8k (137.7k) | +14.0k (35.3k) | +12.2k (30.9k) | -9.1k (15.0k) | +5.9k (16.7k) | +10.3k (36.0k) | +9.0k (31.5k) | -11.1k (20.2k) | CANDIDATE-RECENT | PRE(M), PRE(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| ALL_exit | +19.0k (182.3k) | +5.3k (47.5k) | -1.8k (53.6k) | -15.6k (26.7k) | -9.5k (20.3k) | -8.4k (46.0k) | -7.3k (40.2k) | -35.3k (30.5k) | CANDIDATE-RECENT | HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(HOLD) |
| ALL_entry | +15.1k (130.7k) | +12.7k (31.5k) | +11.7k (27.6k) | -0.3k (3.5k) | -2.1k (4.4k) | +7.8k (22.7k) | +7.6k (22.1k) | +0.8k (3.9k) | CANDIDATE-RECENT | PRE(M), X(M), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| ALL_mult | +20.7k (215.7k) | -24.5k (67.0k) | -15.9k (69.3k) | -2.9k (22.1k) | -2.9k (23.3k) | -36.4k (64.9k) | -25.0k (67.0k) | -5.9k (23.4k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| ALL_mult_MATCHED | +24.1k (222.7k) | -23.2k (70.7k) | -15.0k (72.3k) | -5.4k (29.3k) | +10.2k (33.7k) | -36.1k (69.0k) | -26.2k (70.2k) | -13.5k (30.8k) | DEAD | L6M(M), HOLD(M), PRE(M), L6M(N), HOLD(N), PRE(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| ALL_mult_CAPPED | +0.0k (0.0k) | -7.6k (30.3k) | -12.6k (35.7k) | -10.3k (14.1k) | +1.3k (13.5k) | -21.9k (53.9k) | -23.6k (50.9k) | -21.6k (26.0k) | DEAD | L6M(M), HOLD(M), PRE(M), L6M(N), HOLD(N), PRE(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| HONEST_exit | +12.8k (156.5k) | -1.6k (43.1k) | -3.9k (45.1k) | -14.5k (23.3k) | -5.4k (18.4k) | -1.6k (45.7k) | -1.4k (39.9k) | -29.2k (26.9k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(HOLD) |
| HONEST_entry | -2.4k (52.2k) | +8.3k (17.9k) | +7.7k (16.4k) | +0.0k (3.3k) | -1.1k (3.1k) | +10.7k (20.4k) | +11.8k (21.4k) | +1.9k (3.6k) | DEAD | X(M), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| HONEST_mult | +11.2k (202.7k) | -22.0k (66.2k) | -12.9k (69.2k) | -2.2k (18.5k) | -2.8k (24.0k) | -32.5k (63.0k) | -21.8k (67.8k) | -3.2k (19.3k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| *weight threshold curve (sensitivity, NOT selected: a rule acts only if its shrunken weight exceeds the threshold in pts per fired trade)* | | | | | | | | | | |
| ALL threshold 0.25 pt | +20.7k (215.7k) | -13.2k (61.1k) | -8.1k (67.9k) | -16.6k (30.3k) | -8.9k (25.9k) | -39.2k (65.3k) | -28.4k (65.7k) | -33.8k (35.6k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| HONEST threshold 0.25 pt | +14.5k (210.2k) | -10.2k (61.2k) | -3.2k (66.4k) | -10.0k (25.2k) | -4.6k (27.3k) | -27.4k (65.4k) | -18.3k (65.6k) | -23.5k (28.8k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r, beats single-best(L6M), beats single-best(HOLD) |
| ALL threshold 0.5 pt | +21.8k (218.0k) | -6.2k (61.7k) | -0.5k (65.6k) | -9.1k (27.1k) | -7.5k (22.3k) | -33.2k (63.5k) | -20.0k (63.7k) | -21.9k (31.1k) | DEAD | L6M(M), HOLD(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| HONEST threshold 0.5 pt | +11.1k (200.4k) | -1.7k (59.6k) | +4.8k (59.7k) | -5.9k (26.9k) | -3.7k (25.7k) | -16.3k (59.1k) | -6.8k (56.1k) | -13.9k (27.3k) | DEAD | L6M(M), PRE(M), X(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| ALL threshold 1 pt | +18.7k (216.3k) | +7.8k (54.1k) | +7.0k (56.6k) | -5.8k (26.0k) | +0.6k (24.6k) | -8.5k (59.4k) | -5.3k (53.5k) | -19.9k (29.2k) | CANDIDATE-RECENT | PRE(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| HONEST threshold 1 pt | +9.8k (198.5k) | +8.1k (51.2k) | +7.6k (50.5k) | -8.3k (24.4k) | +0.2k (25.5k) | -2.0k (53.4k) | -3.5k (47.2k) | -14.9k (24.0k) | CANDIDATE-RECENT | PRE(M), L6M(N), HOLD(N), PRE(N), X(N), CI(PRE lo>0), placebo(a) n/r, placebo(b) n/r |
| ALL threshold 2 pt | +4.6k (214.6k) | +8.2k (49.7k) | +7.0k (46.4k) | -4.4k (21.1k) | +1.7k (20.9k) | +1.3k (45.9k) | +3.4k (40.2k) | -7.2k (23.1k) | CANDIDATE-RECENT | PRE(M), PRE(N), X(N), CI(PRE lo>0), placebo(a) rank 0.65, placebo(b) n/r |
| HONEST threshold 2 pt | +19.3k (197.1k) | +10.2k (50.0k) | +9.2k (46.4k) | -4.0k (17.3k) | -2.8k (19.3k) | +2.7k (50.1k) | +2.4k (43.8k) | -4.9k (17.6k) | CANDIDATE-RECENT | PRE(M), X(M), PRE(N), X(N), CI(PRE lo>0), placebo(a) rank 0.70, placebo(b) n/r |
| *benchmark* | | | | | | | | | | |
| single best (rule, book) re-selected monthly | +20.3k (173.8k) | -7.6k (58.4k) | -0.7k (57.5k) | -16.5k (28.2k) | -7.5k (18.9k) | -29.2k (62.9k) | -20.7k (60.0k) | -29.7k (29.9k) | benchmark | |

## 3. Placebos
(a) Shuffled-label: decisions (skip, multiplier, entry cell, exit at the same hold-fraction with a 0.995 pt market cost) re-assigned to random trades of the same book and entry week, 20 draws, exact engine. Mean delta of the placebo draws and the rank of the real value (fraction of draws below it):
| variant | basis | window | real | placebo mean (SD) | rank |
|--|--|--|--|--|--|
| ALL | M | L6M | -18.0k | -20.5k (2.7k) | 0.80 |
| ALL | M | HOLD | -10.6k | -13.2k (2.5k) | 0.85 |
| ALL | M | PRE | -19.9k | -42.8k (6.1k) | 1.00 |
| ALL | N | L6M | -47.7k | -50.3k (5.3k) | 0.70 |
| ALL | N | HOLD | -33.5k | -36.7k (4.9k) | 0.75 |
| ALL | N | PRE | -39.8k | -59.6k (4.4k) | 1.00 |
| HONEST | M | L6M | -16.9k | -21.3k (4.1k) | 0.90 |
| HONEST | M | HOLD | -6.4k | -13.3k (4.1k) | 0.95 |
| HONEST | M | PRE | -17.7k | -37.9k (5.1k) | 1.00 |
| HONEST | N | L6M | -48.2k | -43.7k (5.8k) | 0.20 |
| HONEST | N | HOLD | -34.1k | -31.6k (5.3k) | 0.30 |
| HONEST | N | PRE | -32.9k | -43.6k (4.4k) | 1.00 |
| ALL_CAPPED | M | L6M | +15.0k | -10.5k (6.9k) | 1.00 |
| ALL_CAPPED | M | HOLD | +7.7k | -13.3k (6.2k) | 1.00 |
| ALL_CAPPED | M | PRE | -22.2k | -42.2k (4.0k) | 1.00 |
| ALL_CAPPED | N | L6M | -18.6k | -38.7k (8.6k) | 1.00 |
| ALL_CAPPED | N | HOLD | -19.8k | -37.8k (7.6k) | 1.00 |
| ALL_CAPPED | N | PRE | -38.8k | -51.5k (3.2k) | 1.00 |
| HONEST_CAPPED | M | L6M | +3.2k | -12.9k (7.5k) | 1.00 |
| HONEST_CAPPED | M | HOLD | -1.1k | -15.3k (7.1k) | 1.00 |
| HONEST_CAPPED | M | PRE | -21.0k | -39.4k (4.6k) | 1.00 |
| HONEST_CAPPED | N | L6M | -3.2k | -23.2k (11.3k) | 0.95 |
| HONEST_CAPPED | N | HOLD | -5.5k | -23.1k (9.9k) | 0.90 |
| HONEST_CAPPED | N | PRE | -23.1k | -40.2k (4.8k) | 1.00 |
| ALL_loss_entry | M | L6M | +20.5k | +2.6k (5.7k) | 1.00 |
| ALL_loss_entry | M | HOLD | +18.5k | +2.8k (5.0k) | 1.00 |
| ALL_loss_entry | M | PRE | -9.6k | -21.0k (3.3k) | 1.00 |
| ALL_loss_entry | N | L6M | +12.6k | -18.6k (9.2k) | 1.00 |
| ALL_loss_entry | N | HOLD | +11.8k | -15.5k (8.1k) | 1.00 |
| ALL_loss_entry | N | PRE | -11.3k | -26.1k (4.5k) | 1.00 |
| HONEST_loss_entry | M | L6M | +14.0k | -2.8k (7.2k) | 1.00 |
| HONEST_loss_entry | M | HOLD | +12.7k | -2.0k (6.3k) | 1.00 |
| HONEST_loss_entry | M | PRE | -8.5k | -16.0k (3.7k) | 1.00 |
| HONEST_loss_entry | N | L6M | +6.9k | -11.0k (8.7k) | 1.00 |
| HONEST_loss_entry | N | HOLD | +8.5k | -7.2k (7.6k) | 1.00 |
| HONEST_loss_entry | N | PRE | -9.1k | -21.5k (4.0k) | 1.00 |
| ALL_thr2.0 | M | L6M | +8.2k | +6.4k (5.5k) | 0.65 |
| ALL_thr2.0 | M | HOLD | +7.0k | -1.6k (5.8k) | 0.95 |
| ALL_thr2.0 | M | PRE | -4.4k | -13.0k (3.7k) | 1.00 |
| ALL_thr2.0 | N | L6M | +1.3k | -4.0k (6.0k) | 0.80 |
| ALL_thr2.0 | N | HOLD | +3.4k | -4.4k (5.8k) | 0.90 |
| ALL_thr2.0 | N | PRE | -7.2k | -13.2k (3.7k) | 0.90 |
| HONEST_thr2.0 | M | L6M | +10.2k | +6.9k (4.5k) | 0.70 |
| HONEST_thr2.0 | M | HOLD | +9.2k | +1.8k (4.1k) | 1.00 |
| HONEST_thr2.0 | M | PRE | -4.0k | -8.7k (2.3k) | 0.95 |
| HONEST_thr2.0 | N | L6M | +2.7k | -1.5k (5.9k) | 0.80 |
| HONEST_thr2.0 | N | HOLD | +2.4k | -1.3k (5.1k) | 0.80 |
| HONEST_thr2.0 | N | PRE | -4.9k | -7.2k (2.5k) | 0.80 |
(b) Random-rule-subset: per program the same number of rules is drawn from that program's stored result table (L2SL 7,840 cells, L2SP 23,773, THL2 448, L2SE entry 2,167, L2EA catalogue 240; THP/EXP1 rules kept fixed), scope all six books, same weekly empirical-Bayes walk-forward, scored on the PROXY (sum of the chosen rule effects x lots x $20, max-weight rule per trade, no locks); the real ensemble is scored on the same proxy. Proxy deltas are not engine deltas (no lock/busy effects, additive sides): only the rank is meaningful.
| set | basis | window | real (proxy $/wk) | random subsets mean (SD) | rank (n draws) |
|--|--|--|--|--|--|
| ALL | M | 2026 (~5 wk) | -48.0k | -26.9k (72.0k) | 0.41 (200) |
| ALL | M | L6M | -18.2k | +27.4k (51.1k) | 0.17 (200) |
| ALL | M | HOLD | +17.0k | +50.1k (49.9k) | 0.24 (200) |
| ALL | M | PRE | +61.9k | +25.5k (22.6k) | 0.95 (200) |
| ALL | M | X' | -13.0k | -9.1k (11.0k) | 0.32 (200) |
| ALL | N | 2026 (~5 wk) | -134.0k | -53.2k (92.7k) | 0.28 (200) |
| ALL | N | L6M | -74.7k | -61.6k (36.5k) | 0.33 (200) |
| ALL | N | HOLD | -57.9k | -46.6k (33.4k) | 0.35 (200) |
| ALL | N | PRE | -25.0k | -54.8k (20.8k) | 0.93 (200) |
| ALL | N | X' | -22.3k | -19.5k (11.7k) | 0.37 (200) |
| HONEST | M | 2026 (~5 wk) | -53.3k | -26.9k (72.0k) | 0.35 (200) |
| HONEST | M | L6M | -23.3k | +27.4k (51.1k) | 0.15 (200) |
| HONEST | M | HOLD | +11.5k | +50.1k (49.9k) | 0.20 (200) |
| HONEST | M | PRE | +37.1k | +25.5k (22.6k) | 0.67 (200) |
| HONEST | M | X' | -15.4k | -9.1k (11.0k) | 0.28 (200) |
| HONEST | N | 2026 (~5 wk) | -143.7k | -53.2k (92.7k) | 0.12 (200) |
| HONEST | N | L6M | -83.8k | -61.6k (36.5k) | 0.26 (200) |
| HONEST | N | HOLD | -64.2k | -46.6k (33.4k) | 0.28 (200) |
| HONEST | N | PRE | -31.4k | -54.8k (20.8k) | 0.86 (200) |
| HONEST | N | X' | -24.5k | -19.5k (11.7k) | 0.26 (200) |

## 4. Rule list and weights at the last re-fit (2026-02-02; trailing window 2025-11-02..2026-02-01 of closed trades)
**M basis**: 356 of 612 (rule, book) pairs carry a positive weight: entry 8, filter 65, profit 266, size 17; pruned (w >= 0.1): 81.
**N basis**: 81 of 612 (rule, book) pairs carry a positive weight: filter 64, size 17; pruned (w >= 0.1): 77.
Top 25 weights (M basis; MDE = 2.8 SE of the in-window mean, pts per fired trade):
| rule | program | side | honest | book | n fired | mean | MDE | weight M | weight N |
|--|--|--|--|--|--|--|--|--|--|
| L2EA:thinAhThickBh_keep | L2EA | filter | honest | WT | 889 | +17.10 | 31.83 | 8.23 | 7.39 |
| L2EA:agree_keep0.3 | L2EA | filter | honest | SM | 160 | +62.74 | 83.88 | 7.39 | 7.73 |
| L2EA:thinAhThickBh_keep | L2EA | filter | honest | HM | 476 | +28.53 | 57.17 | 6.37 | 6.10 |
| L2EA:thinAhThickBh_keep | L2EA | filter | honest | PE | 666 | +45.24 | 79.91 | 5.80 | 5.65 |
| L2EA:agree_keep0.3 | L2EA | filter | honest | KB | 680 | +12.22 | 33.03 | 5.65 | 6.04 |
| L2EA:agree_keep0.3 | L2EA | filter | honest | ST | 668 | +12.63 | 46.10 | 3.87 | 4.18 |
| L2EA:skipTop3_depth_rel | L2EA | filter | looked | SM | 160 | +4.13 | 8.35 | 3.85 | 4.01 |
| L2EA:skipBot10_rel_ahead8 | L2EA | filter | honest | SM | 160 | +3.78 | 4.50 | 3.70 | 3.80 |
| L2EA:skipBot10_rel_tot8 | L2EA | filter | honest | SM | 160 | +2.94 | 4.70 | 2.87 | 2.98 |
| L2EA:agree_keep0.3 | L2EA | filter | honest | HM | 476 | +7.71 | 42.86 | 2.61 | 3.16 |
| L2EA:skipTop3_depth_rel | L2EA | filter | looked | HM | 476 | +2.63 | 4.61 | 2.57 | 2.71 |
| L2EA:skipTop3_spread_t | L2EA | filter | looked | PE | 666 | +2.63 | 5.02 | 2.57 | 2.56 |
| L2EA:skipBot3_depth_rel | L2EA | filter | looked | PE | 666 | +2.44 | 4.63 | 2.39 | 2.45 |
| L2EA:skipTop3_pulled_sup10 | L2EA | filter | looked | PE | 666 | +2.28 | 3.90 | 2.25 | 2.06 |
| L2EA:skipTop3_intens_rel | L2EA | filter | looked | ST | 668 | +2.20 | 3.56 | 2.17 | 2.23 |
| L2EA:skipTop3_spread_t | L2EA | filter | looked | HM | 476 | +2.16 | 5.34 | 2.10 | 2.07 |
| L2EA:skipTop3_pulled_opp10 | L2EA | filter | looked | PE | 666 | +2.13 | 3.69 | 2.10 | 1.92 |
| L2EA:thinAhThickBh_keep | L2EA | filter | honest | KB | 680 | +17.88 | 86.25 | 2.00 | 2.05 |
| L2EA:skipTop3_rnd100_ahead | L2EA | filter | looked | HM | 476 | +2.02 | 4.89 | 1.97 | 1.99 |
| L2EA:skipBot10_maxlv_ahead_rel | L2EA | filter | looked | HM | 476 | +1.98 | 2.97 | 1.96 | 2.02 |
| L2EA:skipTop3_imb10 | L2EA | filter | looked | SM | 160 | +2.14 | 9.61 | 1.95 | 1.93 |
| L2EA:skipBot3_depth_rel | L2EA | filter | looked | KB | 680 | +1.83 | 5.77 | 1.77 | 1.87 |
| L2EA:agree_keep0.2 | L2EA | filter | looked | PE | 666 | +2.44 | 19.57 | 1.73 | 1.96 |
| L2EA:skipTop3_rnd100_ahead | L2EA | filter | looked | KB | 680 | +1.76 | 4.45 | 1.73 | 1.76 |
| L2EA:skipBot10_maxlv_ahead_rel | L2EA | filter | looked | ST | 668 | +1.68 | 3.04 | 1.66 | 1.52 |
Weights at the same re-fit with every multiplier capped at 2x (post-hoc A3). The preregistered weights above for the L2EA rules are measured at the uncapped lot-matched multiplier (W up to ~9 for rules that keep ~11% of trades), which is why their means are tens of points; the capped table is the realistic scale. Top 15 (M basis):
| rule | side | honest | book | n fired | mean | MDE | weight M | weight N |
|--|--|--|--|--|--|--|--|--|
| L2SE:fam=F1|X=5|b=ii|M=10|prof=dflt|N=3|veto=v4 | entry | honest | KB | 680 | +3.39 | 3.70 | 0.17 | 0.00 |
| L2SE:fam=F1|X=8|b=ii|M=10|prof=dflt|N=3|veto=v4 | entry | looked | KB | 680 | +3.18 | 4.02 | 0.13 | 0.00 |
| L2SE:fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | entry | honest | PE | 666 | +0.20 | 1.21 | 0.07 | 0.00 |
| L2SE:fam=F5|F=0.3|X=10|N=1|chase=none|veto=v4 | entry | looked | SM | 160 | +1.54 | 6.16 | 0.03 | 0.00 |
| L2SE:fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | entry | honest | SM | 160 | +0.22 | 2.31 | 0.03 | 0.00 |
| L2SE:fam=F5|F=0.5|X=15|N=2|chase=none|veto=v4 | entry | looked | PE | 666 | +0.32 | 2.96 | 0.02 | 0.00 |
| L2SE:fam=F2|gate=PRINT50|X=5|b=iii|veto=v4 | entry | looked | HM | 476 | +0.93 | 7.01 | 0.01 | -0.00 |
| L2H:H7P|pct0.7|with10|n3|take | profit | honest | WT | 485 | +2.59 | 2.59 | 0.01 | -0.00 |
| L2SP:P|sess_ahead_ge1.2|armpts15|d30|trail20|p70always | profit | looked | WT | 566 | +3.08 | 2.91 | 0.01 | -0.00 |
| L2SP:P|sess_tot_ge1.2|armpct0.7|d10|trail30|p70always | profit | looked | WT | 532 | +2.24 | 2.56 | 0.01 | -0.00 |
| L2SP:P|sess_tot_ge1.2|armpct0.7|d10|take|p70always | profit | looked | WT | 534 | +2.39 | 2.68 | 0.01 | -0.00 |
| L2H:H7P|pct0.7|with30|n3|take | profit | looked | WT | 515 | +2.19 | 2.58 | 0.01 | -0.00 |
| L2H:H7P|pct0.7|with10|n1|take | profit | looked | WT | 523 | +2.16 | 2.65 | 0.01 | -0.00 |
| L2SP:P|sess_ahead_ge1.2|armpct0.7|d30|take|p70always | profit | looked | WT | 530 | +2.17 | 2.67 | 0.01 | -0.00 |
| L2SP:REF|p70_take_always | profit | honest | WT | 525 | +2.06 | 2.65 | 0.01 | -0.00 |
Capped fit, positive-weight pairs at this re-fit: M 274, N 0; by side (M): profit 266, loss 0, entry 8, filter 0, size 0
Full rule list (139 rules; max weight over books; 'books active' = number of books with weight > 0; full per-book table: out/missed/ensemble_weights_last_refit.csv):
| rule | program | side | honest | books in scope | max weight M | max weight N | books active M |
|--|--|--|--|--|--|--|--|
| L2SE:fam=F1|X=5|b=ii|M=10|prof=dflt|N=3|veto=v4 | L2SE | entry | honest | 1 | 0.17 | 0.00 | 1 |
| L2SE:fam=F1|X=8|b=ii|M=10|prof=dflt|N=3|veto=v4 | L2SE | entry | looked | 1 | 0.13 | 0.00 | 1 |
| L2SE:fam=F5|F=0.7|X=3|N=1|chase=none|veto=v4 | L2SE | entry | honest | 6 | 0.07 | -0.00 | 2 |
| L2SE:fam=F5|F=0.3|X=10|N=1|chase=none|veto=v4 | L2SE | entry | looked | 1 | 0.03 | 0.00 | 1 |
| L2SE:fam=F5|F=0.5|X=15|N=2|chase=none|veto=v4 | L2SE | entry | looked | 1 | 0.02 | 0.00 | 1 |
| L2SE:fam=F2|gate=PRINT50|X=5|b=iii|veto=v4 | L2SE | entry | looked | 1 | 0.01 | -0.00 | 1 |
| L2SE:fam=F1|X=3|b=iii|prof=dflt|N=4|veto=v3 | L2SE | entry | honest | 1 | 0.00 | -0.00 | 1 |
| L2SE:fam=F1|X=15|b=iii|prof=dflt|N=2|veto=none | L2SE | entry | honest | 1 | 0.00 | -0.00 | 0 |
| L2SE:fam=F1|X=3|b=i|prof=dflt|N=1|veto=v3 | L2SE | entry | looked | 1 | 0.00 | -0.00 | 0 |
| L2SE:fam=F4|X=10|N=1|chase=imb8|stop=orig|veto=v4 | L2SE | entry | honest | 1 | 0.00 | -0.00 | 0 |
| L2SE:fam=F4|X=5|N=3|chase=dlt3|stop=orig|veto=v4 | L2SE | entry | looked | 1 | 0.00 | -0.00 | 0 |
| L2SE:fam=F5|F=0.3|X=10|N=3|chase=px10|veto=v4 | L2SE | entry | honest | 1 | 0.00 | -0.00 | 0 |
| L2SE:fam=F5|F=0.7|X=5|N=0|chase=px5|veto=v4 | L2SE | entry | honest | 1 | 0.00 | -0.00 | 0 |
| L2EA:thinAhThickBh_keep | L2EA | filter | honest | 6 | 8.23 | 7.39 | 5 |
| L2EA:agree_keep0.3 | L2EA | filter | honest | 6 | 7.39 | 7.73 | 4 |
| L2EA:skipTop3_depth_rel | L2EA | filter | looked | 2 | 3.85 | 4.01 | 2 |
| L2EA:skipBot10_rel_ahead8 | L2EA | filter | honest | 6 | 3.70 | 3.80 | 5 |
| L2EA:skipBot10_rel_tot8 | L2EA | filter | honest | 6 | 2.87 | 2.98 | 4 |
| L2EA:skipTop3_spread_t | L2EA | filter | looked | 6 | 2.57 | 2.56 | 5 |
| L2EA:skipBot3_depth_rel | L2EA | filter | looked | 6 | 2.39 | 2.45 | 4 |
| L2EA:skipTop3_pulled_sup10 | L2EA | filter | looked | 6 | 2.25 | 2.06 | 5 |
| L2EA:skipTop3_intens_rel | L2EA | filter | looked | 1 | 2.17 | 2.23 | 1 |
| L2EA:skipTop3_pulled_opp10 | L2EA | filter | looked | 6 | 2.10 | 1.92 | 4 |
| L2EA:skipTop3_rnd100_ahead | L2EA | filter | looked | 6 | 1.97 | 1.99 | 4 |
| L2EA:skipBot10_maxlv_ahead_rel | L2EA | filter | looked | 6 | 1.96 | 2.02 | 5 |
| L2EA:skipTop3_imb10 | L2EA | filter | looked | 2 | 1.95 | 1.93 | 2 |
| L2EA:agree_keep0.2 | L2EA | filter | looked | 1 | 1.73 | 1.96 | 1 |
| L2EA:skipBot10_maxlv_behind_rel | L2EA | filter | looked | 6 | 1.07 | 0.97 | 5 |
| L2EA:skipBot10_rel_behind8 | L2EA | filter | honest | 6 | 1.02 | 1.19 | 3 |
| L2EA:skipBot3_es_imb5 | L2EA | filter | looked | 1 | 1.00 | 0.94 | 1 |
| L2EA:skipBot3_rel_behind8 | L2EA | filter | honest | 6 | 0.83 | 0.95 | 3 |
| L2EA:skipTop10_pulled_opp10 | L2EA | filter | looked | 1 | 0.73 | 0.56 | 1 |
| L2EA:skipBot3_pulled_sup10 | L2EA | filter | looked | 1 | 0.45 | 0.56 | 1 |
| L2SL:1110 | L2SL | loss | looked | 1 | 0.00 | 0.00 | 0 |
| L2SL:1323 | L2SL | loss | looked | 1 | 0.00 | 0.00 | 0 |
| L2SL:144 | L2SL | loss | looked | 1 | 0.00 | 0.00 | 0 |
| L2SL:2774 | L2SL | loss | honest | 1 | -0.00 | -0.00 | 0 |
| L2SL:2779 | L2SL | loss | honest | 1 | -0.00 | -0.00 | 0 |
| L2SL:296 | L2SL | loss | looked | 6 | 0.00 | 0.00 | 0 |
| L2SL:3254 | L2SL | loss | looked | 1 | 0.00 | 0.00 | 0 |
| L2SL:3791 | L2SL | loss | looked | 1 | 0.00 | 0.00 | 0 |
| L2SL:4267 | L2SL | loss | honest | 1 | -0.00 | -0.00 | 0 |
| L2SL:4407 | L2SL | loss | honest | 1 | 0.00 | 0.00 | 0 |
| L2SL:628 | L2SL | loss | honest | 6 | 0.00 | 0.00 | 0 |
| L2SL:6870 | L2SL | loss | honest | 1 | 0.00 | 0.00 | 0 |
| L2SL:72 | L2SL | loss | looked | 1 | 0.00 | 0.00 | 0 |
| L2H:H11|mfe30|d0|T30|path | THL2 | loss | honest | 6 | 0.00 | 0.00 | 0 |
| L2H:H11|mfe30|d10|T120|book | THL2 | loss | looked | 6 | -0.00 | -0.00 | 0 |
| L2H:H11|mfe30|d10|T120|path | THL2 | loss | looked | 6 | 0.00 | 0.00 | 0 |
| L2H:H11|mfe30|d10|T300|book | THL2 | loss | looked | 6 | -0.00 | -0.00 | 0 |
| L2H:H11|mfe30|d10|T60|book | THL2 | loss | looked | 6 | 0.00 | -0.00 | 0 |
| L2H:H11|mfe30|d5|T300|book | THL2 | loss | honest | 6 | -0.00 | -0.00 | 0 |
| L2H:H12L|veto|es0.1 | THL2 | loss | honest | 6 | 0.00 | 0.00 | 0 |
| L2H:H2L|behind8|k1.5 | THL2 | loss | honest | 6 | 0.00 | 0.00 | 0 |
| L2H:H3L|mae20|imb0.5|T10|tt6 | THL2 | loss | honest | 6 | -0.00 | -0.00 | 0 |
| L2H:H4L|mae20|cons15|refill2|cut | THL2 | loss | honest | 6 | 0.00 | 0.00 | 0 |
| L2H:H5L|with-veto | THL2 | loss | honest | 6 | 0.00 | 0.00 | 0 |
| L2H:H6L|mae20|pul500|tt6 | THL2 | loss | honest | 6 | 0.00 | 0.00 | 0 |
| L2H:H7L|mae20|against30|n1|cut | THL2 | loss | honest | 6 | 0.00 | -0.00 | 0 |
| L2H:H8L|thickveto1.25 | THL2 | loss | honest | 6 | 0.00 | 0.00 | 0 |
| L2H:H9L|mae20|m0|flip3|cut | THL2 | loss | honest | 6 | 0.00 | -0.00 | 0 |
| THP:c1:meta|W12m|S1w|c0.995|tight | THPC1 | loss | looked | 6 | 0.00 | 0.00 | 0 |
| THP:exp1:all|cell|6m|m0.5 | EXP1 | profit | looked | 6 | 0.00 | 0.00 | 6 |
| THP:exp1:tight|cell|6m|m0.5 | EXP1 | profit | looked | 6 | 0.00 | 0.00 | 5 |
| THP:exp1:all|cell|6m|m1.0 | EXP1 | profit | looked | 6 | 0.00 | 0.00 | 6 |
| L2SP:P|sess_ahead_ge1.2|armpts15|d30|trail20|p70always | L2SP | profit | looked | 1 | 0.01 | -0.00 | 1 |
| L2SP:P|sess_tot_ge1.2|armpct0.7|d10|trail30|p70always | L2SP | profit | looked | 6 | 0.01 | 0.00 | 6 |
| L2SP:P|sess_tot_ge1.2|armpct0.7|d10|take|p70always | L2SP | profit | looked | 6 | 0.01 | 0.00 | 6 |
| L2SP:P|sess_ahead_ge1.2|armpct0.7|d30|take|p70always | L2SP | profit | looked | 6 | 0.01 | 0.00 | 6 |
| L2SP:REF|p70_take_always | L2SP | profit | honest | 6 | 0.01 | 0.00 | 6 |
| L2SP:P|sess_ahead_ge3.0|armpts20|d0|lock5|p70always | L2SP | profit | looked | 1 | 0.00 | 0.00 | 1 |
| L2SP:I|z_ahead_le-1.0|d0|skip_p70_if_thin | L2SP | profit | honest | 1 | 0.00 | -0.00 | 1 |
| L2SP:P|t60_ahead_ge2.0|armpct0.7|d0|trail30|p70always | L2SP | profit | looked | 1 | 0.00 | 0.00 | 1 |
| L2SP:P|t60_ahead_ge1.2|armpts30|d0|take|p70never | L2SP | profit | honest | 1 | 0.00 | -0.00 | 1 |
| L2SP:P|sess_ahead_ge1.5|armpct0.3|d10|take|p70always | L2SP | profit | looked | 1 | 0.00 | -0.00 | 1 |
| L2SP:I|hour_ahead_le0.5|d0|skip_p70_if_thin | L2SP | profit | honest | 2 | 0.00 | -0.00 | 2 |
| L2SP:P|hour_ahead_ge1.5|armpts30|d30|take|p70always | L2SP | profit | looked | 1 | 0.00 | -0.00 | 1 |
| L2SP:P|hour_ahead_ge2.0|armpts10|d30|take|p70always | L2SP | profit | honest | 1 | 0.00 | -0.00 | 1 |
| L2SP:P|t60_ahead_ge3.0|armpct0.7|d0|lock10|p70never | L2SP | profit | honest | 6 | 0.00 | 0.00 | 2 |
| L2SP:P|sess_tot_ge1.2|armpct0.3|d0|trail5|p70thickonly | L2SP | profit | looked | 1 | 0.00 | 0.00 | 1 |
| L2SP:P|t60_tot_ge2.0|armpct0.7|d0|lock0|p70never | L2SP | profit | honest | 1 | 0.00 | 0.00 | 1 |
| L2SP:P|z_ahead_ge1.5|armpct0.7|d30|lock10|p70never | L2SP | profit | honest | 1 | 0.00 | 0.00 | 1 |
| L2SP:P|t60_ahead_ge1.5|armpts40|d30|lock10|p70never | L2SP | profit | honest | 1 | 0.00 | 0.00 | 0 |
| L2SP:P|t60_ahead_ge3.0|armpts30|d0|trail10|p70never | L2SP | profit | honest | 1 | 0.00 | -0.00 | 0 |
| L2H:H7P|pct0.7|with10|n3|take | THL2 | profit | honest | 6 | 0.01 | -0.00 | 6 |
| L2H:H7P|pct0.7|with30|n3|take | THL2 | profit | looked | 6 | 0.01 | -0.00 | 6 |
| L2H:H7P|pct0.7|with10|n1|take | THL2 | profit | looked | 6 | 0.01 | 0.00 | 6 |
| L2H:H7P|pct0.7|with30|n1|take | THL2 | profit | looked | 6 | 0.01 | 0.00 | 6 |
| L2H:H6P|mfe20|pul500|take | THL2 | profit | honest | 6 | 0.00 | -0.00 | 6 |
| L2H:H7P|pct0.7|with10|n3|tr4 | THL2 | profit | looked | 6 | 0.00 | 0.00 | 5 |
| L2H:H7P|pct0.5|with10|n3|take | THL2 | profit | looked | 6 | 0.00 | -0.00 | 6 |
| L2H:H12P|mfe20|es0.1|take | THL2 | profit | honest | 6 | 0.00 | -0.00 | 5 |
| L2H:H7P|pct0.5|with30|n3|take | THL2 | profit | looked | 6 | 0.00 | -0.00 | 6 |
| L2H:H6P|mfe20|pul150|take | THL2 | profit | looked | 6 | 0.00 | -0.00 | 6 |
| L2H:H7P|pct0.7|with10|n1|tr4 | THL2 | profit | looked | 6 | 0.00 | 0.00 | 5 |
| L2H:H7P|pct0.7|with30|n1|tr4 | THL2 | profit | looked | 6 | 0.00 | 0.00 | 5 |
| L2H:H5P|against|mfe20|take | THL2 | profit | honest | 6 | 0.00 | -0.00 | 6 |
| L2H:H7P|pct0.5|with10|n1|take | THL2 | profit | looked | 6 | 0.00 | -0.00 | 6 |
| L2H:H7P|pct0.5|with30|n1|take | THL2 | profit | looked | 6 | 0.00 | -0.00 | 6 |
| L2H:H7P|pct0.7|with30|n3|tr4 | THL2 | profit | looked | 6 | 0.00 | -0.00 | 5 |
| L2H:H8P|thin0.5|pct0.25|take | THL2 | profit | looked | 6 | 0.00 | -0.00 | 5 |
| L2H:H8P|thin0.5|pct0.25|tr8 | THL2 | profit | looked | 6 | 0.00 | 0.00 | 5 |
| L2H:H8P|thin0.7|pct0.5|take | THL2 | profit | honest | 6 | 0.00 | -0.00 | 6 |
| L2H:H6P|mfe20|pul500|tr4 | THL2 | profit | looked | 6 | 0.00 | 0.00 | 6 |
| L2H:H9P|mfe20|m100|take | THL2 | profit | honest | 6 | 0.00 | -0.00 | 6 |
| L2H:H8P|thin0.5|pct0.25|tr4 | THL2 | profit | looked | 6 | 0.00 | -0.00 | 5 |
| L2H:H10P|mfe20|trail4|micro | THL2 | profit | honest | 6 | 0.00 | -0.00 | 5 |
| L2H:H7P|pct0.5|with30|n3|tr4 | THL2 | profit | looked | 6 | 0.00 | -0.00 | 5 |
| L2H:H8P|thin0.7|pct0.5|tr4 | THL2 | profit | looked | 6 | 0.00 | -0.00 | 6 |
| L2H:H8P|thin0.7|pct0.25|take | THL2 | profit | looked | 6 | 0.00 | -0.00 | 5 |
| L2H:H8P|thin0.7|pct0.5|tr8 | THL2 | profit | looked | 6 | 0.00 | -0.00 | 6 |
| L2H:H1P|pct0.5|k2|take | THL2 | profit | looked | 6 | 0.00 | 0.00 | 4 |
| L2H:H1P|pct0.7|k2|take | THL2 | profit | honest | 6 | 0.00 | 0.00 | 6 |
| L2H:H8P|thin0.5|pct0.5|tr4 | THL2 | profit | looked | 6 | 0.00 | -0.00 | 4 |
| L2H:H8P|thin0.5|pct0.5|take | THL2 | profit | looked | 6 | 0.00 | -0.00 | 4 |
| L2H:H8P|thin0.5|pct0.5|tr8 | THL2 | profit | looked | 6 | 0.00 | -0.00 | 4 |
| L2H:H2P|behind8|k1.5 | THL2 | profit | honest | 6 | 0.00 | -0.00 | 3 |
| L2H:H4P|mfe20|cons15|refill4|take | THL2 | profit | looked | 6 | 0.00 | -0.00 | 2 |
| L2H:H4P|mfe10|cons15|refill4|take | THL2 | profit | looked | 6 | 0.00 | 0.00 | 4 |
| L2H:H4P|mfe10|cons15|refill4|tr4 | THL2 | profit | looked | 6 | 0.00 | 0.00 | 3 |
| L2H:H3P|mfe20|imb0.3|T10|take | THL2 | profit | honest | 6 | 0.00 | -0.00 | 2 |
| L2H:H1P|pct0.5|k5|take | THL2 | profit | looked | 6 | 0.00 | 0.00 | 1 |
| L2H:H1P|pct0.5|k5|tr4 | THL2 | profit | looked | 6 | 0.00 | 0.00 | 0 |
| L2H:H3P|mfe20|imb0.5|T30|take | THL2 | profit | looked | 6 | 0.00 | 0.00 | 0 |
| L2H:H4P|mfe10|cons8|refill2|take | THL2 | profit | looked | 6 | 0.00 | 0.00 | 0 |
| L2H:H4P|mfe10|cons8|refill2|tr4 | THL2 | profit | looked | 6 | 0.00 | 0.00 | 0 |
| L2H:H4P|mfe20|cons8|refill2|take | THL2 | profit | looked | 6 | 0.00 | 0.00 | 0 |
| L2H:H4P|mfe20|cons8|refill2|tr4 | THL2 | profit | honest | 6 | 0.00 | 0.00 | 0 |
| THP:c1:logit|W3m|Sid|c0.995|tight | THPC1 | profit | looked | 6 | 0.00 | 0.00 | 5 |
| THP:c1:logit|W3m|Sid|c0.995|take | THPC1 | profit | looked | 6 | 0.00 | 0.00 | 4 |
| THP:c2:qr|3m|Sintra|reg | THPC2 | profit | looked | 6 | 0.00 | -0.00 | 3 |
| THP:c2:qr|6m|Sintra|reg | THPC2 | profit | honest | 6 | 0.00 | -0.00 | 4 |
| THP:c2:qr|12m|Sintra|reg | THPC2 | profit | looked | 6 | 0.00 | -0.00 | 6 |
| L2EA:doubleTop3_es_imb5 | L2EA | size | looked | 1 | 1.37 | 1.46 | 1 |
| L2EA:halveTop3_pulled_sup10 | L2EA | size | looked | 6 | 0.90 | 0.82 | 5 |
| L2EA:halveTop3_rnd100_ahead | L2EA | size | looked | 6 | 0.81 | 0.82 | 4 |
| L2EA:doubleBot3_rnd100_ahead | L2EA | size | honest | 6 | 0.74 | 0.81 | 2 |
| L2EA:doubleTop3_rel_behind8 | L2EA | size | honest | 6 | 0.57 | 0.61 | 2 |
| L2EA:doubleTop3_rel_tot8 | L2EA | size | looked | 6 | 0.56 | 0.56 | 3 |

## 5. Drift by quarter (weights and delta)
Mean total weight (sum over (rule, book) pairs, pts) and mean number of active pairs per side group, by quarter of the weekly re-fits, M basis; and the preregistered ensemble's stack delta by quarter.
| quarter | profit: total weight / active | loss | entry | mult | ALL delta M $/wk | ALL delta N $/wk |
|--|--|--|--|--|--|--|
| 2023Q3 | 65.9 / 49 | 12.9 / 28 | 0.6 / 2 | 63.9 / 54 | -19.4k | -32.9k |
| 2023Q4 | 11.2 / 34 | 11.5 / 17 | 0.0 / 0 | 8.4 / 11 | +10.3k | -11.8k |
| 2024Q1 | 9.1 / 45 | 16.9 / 16 | 0.0 / 0 | 24.1 / 22 | -22.9k | -40.5k |
| 2024Q2 | 52.7 / 100 | 6.3 / 21 | 0.0 / 1 | 41.9 / 34 | +17.2k | +18.9k |
| 2024Q3 | 2.7 / 16 | 3.5 / 7 | 0.0 / 0 | 9.8 / 9 | -18.1k | -30.0k |
| 2024Q4 | 16.4 / 62 | 4.4 / 12 | 0.0 / 0 | 27.1 / 25 | -59.6k | -56.6k |
| 2025Q1 | 155.1 / 134 | 107.7 / 52 | 0.0 / 0 | 5.2 / 5 | -36.2k | -81.2k |
| 2025Q2 | 84.2 / 140 | 2.3 / 7 | 1.2 / 3 | 0.0 / 0 | -4.7k | -45.1k |
| 2025Q3 | 56.1 / 80 | 0.8 / 2 | 1.8 / 8 | 15.6 / 33 | -17.9k | -32.7k |
| 2025Q4 | 36.5 / 51 | 53.8 / 40 | 2.2 / 6 | 76.3 / 65 | -15.2k | -36.6k |
| 2026Q1 | 39.2 / 153 | 41.0 / 50 | 1.8 / 8 | 122.8 / 88 | +20.7k | -16.9k |
Weight by program per quarter and basis: out/missed/ensemble_weights_drift_by_quarter.csv. Reading: the weights are unstable by construction (3-month window, weekly); the profit-exit weights switch on in the weeks after a run of good take-at-70% trades (the target-fill correction on M) and the multiplier weights track whichever filter happened to be positive in the window.

## 6. Per book and D6 session cells (section 6)
Per book, preregistered ALL, M basis (delta $/wk, MDE): 
| book | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| ST | -4.0k (96.6k) | -11.8k (32.2k) | -9.2k (32.5k) | -7.1k (14.4k) | -2.9k (15.8k) |
| HM | +10.6k (54.1k) | -9.1k (21.8k) | -5.1k (21.3k) | -0.3k (12.9k) | -3.1k (11.1k) |
| WT | -2.2k (32.8k) | +0.7k (14.6k) | +2.6k (15.3k) | -0.2k (7.8k) | -1.5k (9.4k) |
| KB | +4.8k (25.3k) | +3.7k (11.2k) | +4.7k (13.1k) | -4.2k (7.3k) | +0.7k (7.1k) |
| SM | +1.6k (38.5k) | +0.4k (11.7k) | -1.6k (10.6k) | -5.7k (6.5k) | -2.1k (6.6k) |
| PE | +9.9k (41.4k) | -1.8k (13.5k) | -2.0k (13.8k) | -2.4k (8.1k) | +0.7k (7.3k) |
D6 session cells (KB Asia, PE London, HM Asia and NY-AM, SM Asia and London; MV has no lock engine and is not scored). Computed on the PROXY (per-trade effect x lots x $20, no locks) inside each cell, $/wk (MDE) and n trades, reported and registered as session variants, never killed by the pooled number:
| variant | basis | cell | 2026 | L6M | HOLD | PRE | X' | n L6M |
|--|--|--|--|--|--|--|--|--|
| ALL | M | KB|asia | -9.0k (30.6k) | +1.7k (10.9k) | +4.2k (11.4k) | +1.7k (5.2k) | -1.3k (4.3k) | 335 |
| ALL | M | PE|london | +7.4k (11.6k) | -3.0k (7.3k) | -2.7k (6.9k) | +4.9k (4.5k) | -1.7k (3.8k) | 221 |
| ALL | M | HM|asia | -19.6k (42.8k) | -9.0k (13.7k) | -7.5k (13.2k) | +0.0k (10.1k) | -1.8k (5.8k) | 259 |
| ALL | M | HM|nyam | -23.7k (42.0k) | -12.4k (17.1k) | -7.9k (16.1k) | -4.7k (9.0k) | +0.6k (7.1k) | 223 |
| ALL | M | SM|asia | +3.1k (25.0k) | -0.1k (8.3k) | +0.1k (7.8k) | -0.1k (3.2k) | +1.1k (2.9k) | 96 |
| ALL | M | SM|london | -0.4k (15.7k) | +0.6k (6.6k) | +0.6k (6.4k) | -0.1k (3.9k) | -0.9k (4.4k) | 84 |
| ALL | N | KB|asia | -12.6k (32.6k) | -4.4k (10.6k) | -3.8k (9.7k) | -2.8k (4.5k) | -2.2k (4.5k) | 335 |
| ALL | N | PE|london | +5.3k (10.9k) | -4.7k (6.2k) | -4.8k (5.6k) | +3.6k (5.5k) | -2.1k (4.0k) | 221 |
| ALL | N | HM|asia | -24.7k (45.4k) | -13.3k (15.2k) | -12.4k (14.1k) | -5.1k (10.7k) | -0.1k (5.9k) | 259 |
| ALL | N | HM|nyam | -28.0k (44.3k) | -14.8k (18.2k) | -10.8k (16.9k) | -7.0k (9.2k) | +0.1k (8.1k) | 223 |
| ALL | N | SM|asia | +1.9k (25.5k) | -1.0k (8.7k) | -0.9k (7.8k) | -1.4k (3.2k) | +0.7k (3.0k) | 96 |
| ALL | N | SM|london | -1.2k (16.4k) | -0.2k (7.1k) | +0.9k (6.6k) | -1.6k (4.5k) | -0.9k (4.3k) | 84 |
| ALL_loss_entry | M | KB|asia | -21.3k (30.0k) | -5.0k (8.4k) | -4.3k (7.4k) | -3.3k (3.1k) | -1.0k (2.9k) | 335 |
| ALL_loss_entry | M | PE|london | -2.0k (4.6k) | -2.7k (4.9k) | -2.7k (4.3k) | -0.7k (3.3k) | -0.3k (1.0k) | 221 |
| ALL_loss_entry | M | HM|asia | -19.0k (41.2k) | -9.0k (14.0k) | -7.6k (12.4k) | -8.3k (7.1k) | +0.1k (3.4k) | 259 |
| ALL_loss_entry | M | HM|nyam | -30.2k (63.0k) | -9.7k (17.8k) | -8.6k (15.6k) | -5.4k (6.8k) | -1.4k (3.3k) | 223 |
| ALL_loss_entry | M | SM|asia | +1.4k (24.9k) | +1.6k (6.3k) | +1.4k (5.5k) | -0.8k (1.3k) | -0.0k (2.1k) | 96 |
| ALL_loss_entry | M | SM|london | -4.0k (14.0k) | +0.8k (5.1k) | +0.7k (4.5k) | -1.7k (2.6k) | -0.6k (2.4k) | 84 |
| ALL_loss_entry | N | KB|asia | -18.1k (29.5k) | -5.9k (8.4k) | -5.0k (7.4k) | -2.7k (2.9k) | -1.1k (2.9k) | 335 |
| ALL_loss_entry | N | PE|london | -0.2k (9.1k) | -2.0k (4.4k) | -1.8k (3.9k) | +0.3k (2.8k) | -0.4k (1.1k) | 221 |
| ALL_loss_entry | N | HM|asia | -12.4k (12.1k) | -3.6k (9.9k) | -3.1k (8.7k) | -8.5k (7.4k) | +1.0k (2.7k) | 259 |
| ALL_loss_entry | N | HM|nyam | -13.2k (33.0k) | -6.2k (9.8k) | -5.0k (9.0k) | -5.9k (6.9k) | +0.2k (2.8k) | 223 |
| ALL_loss_entry | N | SM|asia | -0.6k (22.5k) | -0.4k (6.8k) | -0.3k (5.9k) | -1.3k (1.9k) | +0.5k (1.5k) | 96 |
| ALL_loss_entry | N | SM|london | -6.2k (14.2k) | +0.2k (5.6k) | +0.2k (4.9k) | -2.2k (3.4k) | -0.3k (2.1k) | 84 |
| HONEST_loss_entry | M | KB|asia | -12.5k (31.6k) | -2.4k (7.4k) | -2.1k (6.5k) | -3.3k (3.2k) | -0.9k (3.0k) | 335 |
| HONEST_loss_entry | M | PE|london | -5.2k (6.3k) | -3.8k (4.1k) | -3.2k (3.7k) | -0.2k (3.3k) | -0.2k (0.9k) | 221 |
| HONEST_loss_entry | M | HM|asia | -14.6k (39.0k) | -5.3k (10.7k) | -4.4k (9.4k) | -7.3k (6.2k) | -0.1k (3.4k) | 259 |
| HONEST_loss_entry | M | HM|nyam | -19.4k (62.1k) | -7.2k (14.5k) | -6.4k (12.7k) | -4.2k (5.5k) | -1.4k (3.3k) | 223 |
| HONEST_loss_entry | M | SM|asia | +3.1k (17.8k) | +1.4k (4.1k) | +1.2k (3.6k) | -0.4k (1.1k) | -0.1k (2.1k) | 96 |
| HONEST_loss_entry | M | SM|london | -4.3k (12.3k) | +0.1k (4.7k) | +0.1k (4.1k) | -1.8k (2.6k) | -0.3k (2.3k) | 84 |
| HONEST_loss_entry | N | KB|asia | -7.8k (27.0k) | -3.2k (6.8k) | -2.6k (6.0k) | -2.7k (3.1k) | -0.9k (2.9k) | 335 |
| HONEST_loss_entry | N | PE|london | -0.7k (11.2k) | -1.5k (4.3k) | -1.2k (3.8k) | +0.3k (2.5k) | -0.4k (1.1k) | 221 |
| HONEST_loss_entry | N | HM|asia | -14.0k (14.6k) | -5.4k (7.4k) | -4.7k (6.6k) | -7.6k (6.8k) | +0.9k (2.7k) | 259 |
| HONEST_loss_entry | N | HM|nyam | -8.3k (32.4k) | -4.7k (9.1k) | -3.6k (8.4k) | -5.2k (6.4k) | +0.2k (2.8k) | 223 |
| HONEST_loss_entry | N | SM|asia | +2.7k (18.5k) | +0.6k (4.4k) | +0.5k (3.8k) | -0.8k (1.7k) | +0.4k (1.5k) | 96 |
| HONEST_loss_entry | N | SM|london | -4.7k (13.5k) | +0.5k (4.3k) | +0.5k (3.7k) | -1.8k (3.2k) | +0.3k (2.0k) | 84 |
| HONEST_thr2.0 | M | KB|asia | -11.0k (20.7k) | -3.3k (5.6k) | -3.2k (4.9k) | -0.8k (3.1k) | -0.7k (3.1k) | 335 |
| HONEST_thr2.0 | M | PE|london | +7.4k (11.6k) | -0.0k (3.7k) | -0.2k (3.3k) | +1.1k (1.6k) | -0.1k (0.2k) | 221 |
| HONEST_thr2.0 | M | HM|asia | -19.6k (42.8k) | -8.8k (10.8k) | -7.7k (9.5k) | -3.2k (5.3k) | -0.6k (1.9k) | 259 |
| HONEST_thr2.0 | M | HM|nyam | -20.1k (37.6k) | -4.5k (12.8k) | -3.9k (11.2k) | -3.6k (5.6k) | +0.6k (2.3k) | 223 |
| HONEST_thr2.0 | M | SM|asia | +3.1k (25.0k) | +1.8k (6.7k) | +1.6k (5.8k) | +0.2k (1.4k) | -0.2k (1.8k) | 96 |
| HONEST_thr2.0 | M | SM|london | +2.4k (17.8k) | +0.3k (3.9k) | +0.2k (3.4k) | +0.0k (2.1k) | +0.1k (1.8k) | 84 |
| HONEST_thr2.0 | N | KB|asia | -13.8k (23.0k) | -3.6k (6.1k) | -3.1k (5.3k) | -0.1k (2.2k) | -1.0k (3.2k) | 335 |
| HONEST_thr2.0 | N | PE|london | +5.3k (10.9k) | -0.8k (3.7k) | -0.7k (3.2k) | +1.3k (1.5k) | +0.0k (0.0k) | 221 |
| HONEST_thr2.0 | N | HM|asia | -24.7k (45.4k) | -11.0k (12.0k) | -9.7k (10.7k) | -3.1k (4.9k) | +0.3k (0.6k) | 259 |
| HONEST_thr2.0 | N | HM|nyam | -24.1k (39.5k) | -6.3k (13.5k) | -5.5k (11.8k) | -3.6k (6.0k) | -0.3k (1.1k) | 223 |
| HONEST_thr2.0 | N | SM|asia | +1.9k (25.5k) | +1.5k (6.8k) | +1.3k (6.0k) | +0.3k (1.4k) | -0.2k (1.9k) | 96 |
| HONEST_thr2.0 | N | SM|london | +1.7k (18.7k) | +0.1k (4.1k) | +0.1k (3.6k) | +0.0k (2.2k) | +0.6k (1.4k) | 84 |

## 7. Pruned version and retained gain
* ALL: pruned (weights < 0.1 pt dropped) vs full - M L6M -17.2k vs -18.0k, HOLD -11.8k vs -10.6k, PRE -15.7k vs -19.9k; N L6M -43.5k vs -47.7k. Retained gain in L6M: n/a (the full version is negative: pruning removes +0.7k of the loss, i.e. the tiny weights are where the damage is).
* HONEST: pruned (weights < 0.1 pt dropped) vs full - M L6M -4.6k vs -16.9k, HOLD +2.1k vs -6.4k, PRE -13.8k vs -17.7k; N L6M -36.9k vs -48.2k. Retained gain in L6M: n/a (the full version is negative: pruning removes +12.3k of the loss, i.e. the tiny weights are where the damage is).
* ALL loss-exit + entry: pruned (weights < 0.1 pt dropped) vs full - M L6M +20.4k vs +20.5k, HOLD +17.2k vs +18.5k, PRE -11.0k vs -9.6k; N L6M +16.4k vs +12.6k. Retained gain in L6M: 100%.
* HONEST loss-exit + entry: pruned (weights < 0.1 pt dropped) vs full - M L6M +14.2k vs +14.0k, HOLD +12.1k vs +12.7k, PRE -10.3k vs -8.5k; N L6M +13.0k vs +6.9k. Retained gain in L6M: 102%.

## 8. Policy candidate and nightly re-fit
Anything >= 0 in L6M and HOLD on the stack on both bases: loss-exit + entry only (ALL and HONEST), the multiplier-free and threshold >= 2 pt variants; all are POST-HOC compositions / sensitivities (CANDIDATE-RECENT at best, PRE negative). The preregistered full ensemble is not a candidate. `out/missed/ensemble_policy_candidate.txt` is written in THP_POLICY text format from the last re-fit (HONEST, threshold 2 pt, both bases); at that re-fit the rules above threshold are L2EA multiplier rules only (no D6 transliteration, '# NEEDS' rows), so there is nothing legal to run today; they are also NON-EXEC (uncapped lot-matched multipliers up to ~9x) and with every multiplier capped at 2x the nightly capped file (`ensemble_policy_candidate_nightly_capped.txt`) holds 0 lines: no rule keeps a positive weight on the N basis at the last re-fit. One-command nightly re-fit: `bash l2vast/ds3/code/ensemble/ens_refit.sh` (writes out/missed/ensemble_weights_nightly.csv and ensemble_policy_candidate_nightly.txt).

## 9. Honest limits
* Every rule was found on looked data; the 'honest' flag means identified from PRE-only data, but the recent windows were looked at by the programs that produced them, and X'/PRE are in-sample for the honest rules too. The walk-forward removes only the weighting look-ahead, not the selection of the 139 rules.
* 3-month windows contain 5-20 fired trades per (rule, book) for many exit rules; the in-window MDE is mostly 3-10 pts per fired trade, so shrinkage removes most weights most weeks (on the M basis the profit-exit group has a positive weight in 59 of 136 weekly re-fits, loss-exit 61, entry 29, multiplier 58; the rest of the weeks the group is silent).
* Exit rules are scored on the entry clock of their own report and combined as earliest valid exit; the interaction of two exits is not modelled by the weights (each is measured alone). Entry cells use the L2SJ composition (rule exit price of the baseline path on moved entries is an approximation, stated there).
* The proxy used for the random-subset placebo ignores locks and busy rules; the entry-N proxy ignores the lots multiplier on the target correction of split fills.
* One look per group (looks.jsonl); amendments A1-A3 are disclosed in the prereg; headline rows are the preregistered ones.
