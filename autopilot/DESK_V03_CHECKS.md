# DESK_V03_CHECKS (W-DYNC, order 0322Z follow-up: three checks on the DK3 scorecard). Research only. No design change.
Source: exact-engine trade rows (runs_rf) of the DK3MAIN alone-bare sets (_A) against the book's fixed-bracket alone rows (fix_A) on the SAME entries (matched on entry time and side, 95-97% matched); income = gross - 4.84 per lot; every month DONE. 'Winner' = the fixed-bracket trade made money; the managed trade is 'cut short' when it made more than $1 less. NOTE: this is my own same-trade count on the _A rows; the relay's attribution page counts differently (it quotes 498 NY AM winners cut short, -$2.36M); my NY AM count is larger (1,014, -$4.40M) because I count every winner with any shortfall and sum over MF1/MF2/MF4/MF5.

## ANSWER FIRST
1. NOT A MISLABEL. The engine does not report the never-bend stop-at-entry fill as 'Target', and no desk-moved stop is filled as a target. The 'Target' trades that ended a few points from entry are trades where the DEFEND half was taken early (a loss-side action, rule DF) and the REMAINDER then reached the book's own target. The trade row has one exit_name (the last leg: Target) and one exit_px (the lot-weighted average of the two legs), so pts looks small or negative. Proof: NY AM MF4 (own stop 90, own target 30), 10 trades with exit_name Target and row pts between -11.7 and +10.5: every one has algo_npart = 1 and a logged 'part:DF' at open R -0.10 .. -0.59 (-9 .. -53 pts); the leg-1 price implied by (row average x lots - remainder lots x 30)/part lots equals the logged part price within 1-2 points in all 10 (e.g. row -6.75 pts, part R -0.47 = -42.3 pts, implied leg 1 -43.5 pts), gross = lots x pts x 20 exactly, and the trade's best_px shows +30.0 .. +30.7 points (the target). Over the four NY AM books: 431 Target exits with pts < 40% of the target, ALL 431 had a DEFEND half taken (npart >= 1); the 2,744 full-size Target exits (>= 90% of the target) had none. The never-bend stop-at-entry exits (98 trades with NB) are labelled 'Stop' with row pts between -38 and +4 (median +0.3): correct label. So the 'winners cut short' bucket that the attribution calls 'Target (book exit, not a desk rule)' is in fact the DEFEND half: the loss side's own collateral, not a book exit.
2. NY PM MF2 IDENTICAL IS CORRECT, THE PARAMETER IS APPLIED. The set files differ exactly where they should: stream events NP_MF2_own_dg vs NP_MF2_w15_dg (stop_pts median 120 vs 180; target 120 in both) and manager safety_mult 1.0 vs 1.5 (TL3_DX_NP_MF2_DK3MAIN_A.json vs _DK3W_A.json; same for NY MF5: 60 vs 90). The in-mix NP MF2 rows are identical in all 24 months because the stop is never reached: across the 395 managed MF2 trades in DK3MAIN_M the largest adverse excursion is 113.9 points, below even the own 120-point stop, so no trade ever hit a stop of either width: they all leave through the desk (ABORT 103, clock 136), EarlyCut 51 and the live layers (DayHalt 11), target 76; the 3 'Stop' exits are identical in both. NP MF3 (own stop 80, 1.5x = 120, max adverse excursion 80.6) differs between DK3MAIN and DK3W in 22 of 24 months, as it should. NY MF5 alone differs too. In the alone rows (_A) NP MF2 months also differ where a trade reached 120 points.
3. WHICH RULES CUT THE WINNERS (below; per session, alone-bare rows, matched same trades): the biggest bucket is the DEFEND half followed by the book target (NY AM 58% of the cut winners' count and 58% of the dollars; NY PM 44%; London 30%; Asia 18%): that is the LOSS side's collateral. ABORT is the biggest in Asia (29% / -$0.95M) and London (40% / -$1.12M). The bell clock cuts 26-48% by count. The never-bend stop at entry is small everywhere (3-6% of the cut winners, -$0.06M to -$0.13M per session).

## Table 1: same-trade classes per session (managed alone-bare vs the same entries on the book's bracket; n / $ difference)
| session | losers cut early | losers made worse | winners cut short | winners improved |
|---|---|---|---|---|
| Asia | 925 / 1,616,745 | 111 / -95,920 | 597 / -2,033,095 | 120 / 102,150 |
| London | 689 / 1,888,405 | 129 / -108,635 | 771 / -2,148,070 | 45 / 18,490 |
| NY AM | 1337 / 3,737,810 | 85 / -114,870 | 1014 / -4,403,930 | 49 / 55,760 |
| NY PM | 352 / 1,595,040 | 33 / -47,220 | 357 / -1,871,425 | 16 / 23,675 |

## Table 2: the winners cut short, by the rule that ended the managed trade (n, $ vs the bracket, share of the count)
| session | managed exit | n | $ vs bracket | share |
|---|---|---|---|---|
| Asia | ABORT out | 171 | -951,410 | 29% |
| Asia | clock | 286 | -492,130 | 48% |
| Asia | DEFEND half, then book target | 109 | -451,180 | 18% |
| Asia | stop at entry (never-bend) | 27 | -133,880 | 5% |
| Asia | DEFEND half, then RollFlat | 3 | -4,250 | 1% |
| Asia | clock (1 min left) | 1 | -245 | 0% |
| London | ABORT out | 307 | -1,118,995 | 40% |
| London | DEFEND half, then book target | 230 | -592,180 | 30% |
| London | clock | 198 | -327,420 | 26% |
| London | stop at entry (never-bend) | 33 | -109,110 | 4% |
| London | clock (1 min left) | 3 | -365 | 0% |
| NY AM | DEFEND half, then book target | 590 | -2,541,175 | 58% |
| NY AM | clock | 287 | -916,950 | 28% |
| NY AM | ABORT out | 69 | -590,375 | 7% |
| NY AM | stop at entry (never-bend) | 61 | -315,520 | 6% |
| NY AM | DayHalt | 2 | -24,385 | 0% |
| NY AM | DEFEND half, then Stop | 2 | -13,705 | 0% |
| NY AM | clock (1 min left) | 3 | -1,820 | 0% |
| NY PM | ABORT out | 79 | -664,415 | 22% |
| NY PM | DEFEND half, then book target | 157 | -632,600 | 44% |
| NY PM | clock | 109 | -510,170 | 31% |
| NY PM | stop at entry (never-bend) | 10 | -58,780 | 3% |
| NY PM | DEFEND half, then UWTime | 2 | -5,460 | 1% |

Labels: 'ABORT out' = exit ExAlgoAll_AB; 'clock' = ExAlgoAll_CL (the 30-minute clock rule) and 'clock (1 min left)' = ExAlgoAll_N3; 'stop at entry (never-bend)' = a Stop exit on a trade with an NB action in its log; 'DEFEND half, then book target' = a part taken by the DEFEND rule (DF) and the remainder exited by the book's Target; other combinations rare (RollFlat, UWTime, DayHalt, Stop after a DEFEND half). Not every 'DEFEND half, then book target' trade is a bad cut: the half was taken under water and the book target was reached later; it counts as a winner cut short because the same entry on the bracket kept the full lots to the target.
## Caveats
Alone-bare rows only (the in-mix rows add the live layers' interaction; the scorecard's mix rows are post-hoc sums). Match rates 95-97% of the managed entries to the bracket rows (the rest are entries one of the two streams did not take). Threshold of $1 for 'same'. The relay's own attribution page uses its own definition and may differ in counts; the mechanism (DEFEND half, ABORT, clock) is the same.
