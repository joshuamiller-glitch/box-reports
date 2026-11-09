## P7 cap (KCAP3) and P7 lot table 7/4/4: the worst-20 question (SZ-CORE, 2026-11-09 ~22:50Z)

**Answer: the worst-20 is BETTER, not worse.** The "-70.6% / -46%" printed in the earlier tables was a SIGN BUG in `Z.score` (`w20cut` was computed as (live - cell)/|live|; worst-20 is a SUM of the 20 worst weekly P&Ls, so a larger, less negative sum is better; the old sign printed improvements as negatives). Fixed in sz_core.py (+ = improvement now); the cached core rescores were flipped; owner ledgers use their own convention (FGH and IJK already had + = better).

**Definition used:** sum of the 20 smallest weekly P&Ls (ISO weeks of the label day, exit time with the 17:00 ET roll) over ALL weeks of the window, ROLL-EXCL (33 roll-alive trades weight 0), at live lots, exact-engine trade lists, windows L6M (26 weeks), PRE (75 weeks), X' (44 weeks). In L6M, 20 of 26 weeks are "the worst 20", so that sum is simply the window P&L without the 6 best weeks; PRE and X' are the meaningful worst-20 tests.

| set | window | worst-20 sum, live $ | worst-20 sum, cell $ | cell - live $ |
|--|--|--|--|--|
| KCAP3 (P7 cap 3 London+NYAM) | L6M | +165,224 | +281,833 | +116,609 |
| | PRE | -699,709 | -598,540 | +101,169 |
| | X' | -347,890 | -262,798 | +85,091 |
| P7 table 7/4/4 | L6M | +165,224 | +241,050 | +75,826 |
| | PRE | -699,709 | -610,106 | +89,604 |
| | X' | -347,890 | -303,020 | +44,870 |

**Which weeks (KCAP3, L6M; ISO week: live / cell $):** 202621 -62,941 / -58,422; 202644 -54,570 / -56,066; 202635 -45,879 / -27,944; 202630 -35,492 / -7,280; 202636 -34,029 / -21,681; 202643 -25,251 / +518; 202645 0 / 0; 202632 +1,102 / +26,827; 202631 +9,575 / -459; 202634 +20,525 / +33,965. The two worst weeks (202621, 202644) are unchanged or marginally worse for the cell (-58.4k, -56.1k vs -62.9k, -54.6k); the gain is in the next four weeks (202635, 202630, 202636, 202643) where the cell loses 8-35k less. PRE worst weeks (live / KCAP3): 202440 -96,574 / -84,230; 202515 -90,891 / -77,484; 202524 -66,457 / -52,624; 202516 -49,398 / -40,569; 202414 -49,296 / -38,775. X': 202331 -56,654 / -45,251; 202346 -47,212 / -39,195; 202326 -32,866 / -25,997. 7/4/4 shows the same pattern (L6M 202635 -29,511, 202630 -9,235, 202643 -2,372 vs live -45,879, -35,492, -25,251; but 202644 is -59,521 vs -54,570, a bit worse).

**What drives it (P7, the 10 worst live L6M weeks):** live P7 loses London -105.8k, NYAM -38.8k, Asia -44.0k. KCAP3: London -35.0k, NYAM +6.8k, Asia -44.0k (unchanged: Asia stays at 7 lots). 7/4/4: London -41.5k, NYAM -7.9k, Asia -44.0k. So the cap/table shrinks the 7-lot London and NYAM losing trades; the winners it also limits are small-win weeks, which only cost mean, not worst-20. The remaining deep weeks (202621, 202644, 202440, 202515) are P7 Asia and other-book weeks that the London/NYAM cap does not touch.

**Family p.** K1 cap grid (125 cells, saved placebo nulls, max-stat over the grid): the asia 7/london 3/nyam 3 cap (IJK b8c7a11b7c62) own placebo p 0.01 (L6M) / 0.01 (PRE), family p over the cap grid 0.059; its twin cell 8c1cd5ca26ef family p 0.168. P7 lot table (FGH, 124 cells): 7/4/4 own p 0.01, family p over the lot-table grid 0.79 (within-FGH max-stat; 53 of 124 cells have own p <= .10, so the table is a broad exposure effect on P7 rather than one special cell); 5/4/4 own p 0.02, grid family p 0.66. Whole-program max-stat (all families): IJK 0.84 for the cap, FGH 1.0 (earlier). I did not have saved nulls for the FGH lot-table cells in sz_core's null store, so the combined lot-table+cap family p is not computed (FGH's own sub-grid p is shown).

**HOLD exact:** queued (Q_KCAP3 and Q_P7_744 HOLD months 202511-202604, priority 1.45, right after tier 1).
