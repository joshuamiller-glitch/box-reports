# DS3 T-PULLBACK widening (3) health of the pullback + (5) entry style / P5 execution ladder (D3PB2)

Generated 2026-10-27T10:48:11Z. Research only; no execution-server/chart/live change. 52 cells in 2 preregs: PB2 (28; sha256 406e6ae7c6e42596eaca2c73e626451eebd1741b1d7077fbd2658cc2c0d80a23, l2vast/ds3/prereg/PB2_prereg.md) and PB2B (24; sha256 1502eced498e52535405cc125209b8fd9963048aca47b735f00829f551c23eea). Ledger +52. Holdout looks: 1 per prereg (DS3_PB2, DS3_PB2B, pre-holdout texts autopilot/DS3_TPULLBACK2_PREHOLD.md and DS3_TPULLBACK2B_PREHOLD.md); ds3_addbook re-read the holdout twice (PB2_B1_S, PB2_B4_M_Hvol; ledger addbook_looks.jsonl). Rows: l2vast/ds3/rows/DS3_TPULLBACK2.json. Basis: MAPPED (1-s path bracket sim + corrected-P9 mapping, exact lock engine, 10 lots); DIRECT L2 replay of the top-10 M/S cells is running (section 8) and is NOT yet in the verdicts.

## 1. Verdict

**PB2/PB2B: 0 PASS, 2 CANDIDATE, 50 DEAD of 52 cells (mapped; best-of-52 stated).** Candidates: PB2_B1_S (stop-entry above the resumption high, ST10-trend + EMA20 pullback; fails only the WF CI) and PB2_B4_M_Hvol (EMA200-side trend + EMA20 pullback, market entry, retrace volume below the 20-bar median; fails only the placebo, rank 0.92). Neither is a clean result: both are best-of-52 picks, B4_M_Hvol does NOT beat the random-subset-of-base placebo (rank 0.82) and its base cell B4_M is itself positive on holdout (+$18k/wk) and negative on PRE, so most of its profit is the B4 base, not the health condition (paired vs the base cell +0.5 pt/trade [-0.3,+1.2]).

**Findings.** (1) Health conditions as entry conditions do not work reliably: the 12 single-condition health cells have delta-vs-base-cell weekly means of mixed sign (5 of 12 positive on PRE, 5 of 12 on WF), every CI includes 0, and the random-subset placebo (the right null for a condition) ranks the cells 0.1-1.0 with no consistent pattern; volume-below-median (Hvol) is the least bad (positive vs base in 2 of 4 bases on PRE and 3 of 4 on WF), cumulative-delta non-confirmation (Hcd) and absorption (Habs) do not add; the all-three conjunction leaves 0.6-1.3 trades/wk (LOW-FREQUENCY flag, not measurable forward). (2) Entry style: market on the resumption bar vs stop above the resumption high is a wash (S minus M: +1.0k, +2.4k, -0.7k, +5.0k PRE weekly on B1-B4; per-trade differences below MDE); the passive limit AT the level is worse than market in 3 of 4 bases on PRE and 4 of 4 on 2x-cost PRE, and the 3-rung ladder / single frozen limit / scale-in (PB2B) are DEAD in 24 of 24 (best PB2B_B2_SGL_T30_i62: PRE +$5.2k/wk with CI [-3.8k,+14.0k], then holdout -$6.2k, 2023 span -$0.8k, WF -$0.3k). (3) **Passive fills are adversely selected, measured.** Over all episodes (a run of armed bars, limit at the level, trade-through fill), the hypothetical MARKET trade entered at the episode start loses -4 to -7 points (raw, DS2 bracket) when the limit FILLS and wins +10 to +14 points when it does NOT fill: you are filled when the pullback goes through the level (continuing against you) and miss the ones that bounce at the level. Fill rate 50-63% of episodes (PB2 L cells) and 40-50% for the PB2B ladders. This is the same adverse selection as STRUCT48 T4 (block limit LB0 -0.46 pt/trade) and explains why every passive cell loses to market.

Power: standalone weekly MDE (2.8 x SE) is $8-13k/wk at 10 lots (WF 143 wk), per-trade MDE 2.2 pts for the base cells, 3.5-8 for Hvol/Hcd/Habs, >12 for Hall; the predicted effects (+1 pt/trade for health, +-0.5 for style) are below MDE for every cell, so all nulls below are 'could not have seen less than MDE', see the MDE column.

## 2. Method
Fixed DS2 bracket (60-pt stop, 1.0R, flat 16:55), 10 lots, P9 mapped, per-book locks, $4.84 RT; base cells B1-B4 declared in the prereg (own implementation: ST10m or EMA200(5m) regime x EMA20(5m)/VWAP/50%-of-swing pullback x first 1-min close back in trend direction after a touch within 30 min); health = Hvol (retrace mean volume < prior-20-bar median), Hcd (retrace delta not below -5% of volume), Habs (heavy bar at the level, opposing delta, close held); volume/delta from the 1-min aggregates of the 1-s/100-ms classified-trade tape (as-of completed bars; truncation audit pb2_trunc.py: 1,536,234 events compared, 0 mismatches). Styles: M, S (buy-stop high+1 tick, 5 bars, 1-s path fill), L (limit at the as-of level, trade-through 1 tick, never at touch, non-fill skipped). PB2B (P5): three rungs level / -5 / -10 pts, 1/3 each, frozen at the first armed bar, life 10/30 min, cancelled on invalidation (62% retrace, 1.5 ATR, prior swing), single-rung control and scale-in on the second touch; each filled rung has its own 60-pt/1R bracket. Caveat: the lock engine marks entries at the 1-min bar start, so intrabar fill timing is exact only in the bracket path sim. Regime columns: predicted-quiet if P_lgb(session RV below p40) >= 0.5 at session open (D3R l2vast/ds3/out/TA/pquiet_series.parquet), else wide. Windows: WF-PRE 2024-02..2025-06, holdout 2025-07+, second span 2023-04..2024-01. Verdict as T-ENTRY; prereg reading applied: placebo rank < 0.90 with no other failure is DEAD (0.90-0.95 counts as one failure). Placebos: timing-destroyed (40) and, for health cells, random subset of the base (40). Unknown/absent: the D3C random-library placebo pool.

## 3. PB2 (28 cells): health and entry style

| cell | flag | verdict | tr/wk (WF) | win | PRE $/wk | HOLD | 2023 span | WF | WF CI | placebo (timing) | placebo (subset of base) | 2x cost WF | delta vs base cell WF $/wk [CI] | paired vs base pts/trade [CI] (MDE) | paired vs ST pts/trade [CI] (MDE, n) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| PB2_B1_M | NT8-bars | DEAD | 24.9 | 0.50 | 3,781 | 6,814 | 3,528 | 5,271 | [-4,374, 15,102] | 0.70 |  | 2,396 | 0 [0, 0] | +0.0 [+0.0,+0.0] (MDE 0.0, n 3561) | +8.3 [+5.4,+11.2] (MDE 4.2, n 770) |
| PB2_B1_M_Hvol | NT8-bars | DEAD | 19.3 | 0.51 | 2,859 | 12,971 | 6,197 | 7,758 | [-44, 15,568] | 0.72 | 0.80 | 4,420 | 2,488 [-5,324, 10,337] | +0.7 [-0.0,+1.4] (MDE 1.0, n 1291) | +8.4 [+4.7,+12.0] (MDE 5.3, n 377) |
| PB2_B1_M_Hcd | NT8-ticks | DEAD | 22.7 | 0.50 | -1,099 | 7,322 | 3,688 | 2,956 | [-5,967, 12,025] |  | 0.07 | -678 | -2,314 [-8,207, 4,097] | +0.1 [-0.7,+0.9] (MDE 1.1, n 1885) | +7.7 [+4.4,+11.0] (MDE 4.5, n 578) |
| PB2_B1_M_Habs | NT8-ticks | DEAD | 10.9 | 0.51 | 3,418 | 3,228 | -5,857 | 3,351 | [-2,536, 9,323] | 0.90 | 0.95 | 2,069 | -1,920 [-11,004, 7,197] | +0.6 [-0.7,+1.9] (MDE 1.8, n 624) | +10.3 [+4.9,+16.0] (MDE 7.7, n 231) |
| PB2_B1_M_Hall | NT8-ticks | DEAD | 1.2 LOW | 0.49 | 414 | -1,659 | 184 | -583 | [-2,351, 1,401] | 0.78 | 0.68 | -643 | -5,854 [-15,381, 4,000] | +1.6 [-1.9,+7.0] (MDE 6.9, n 46) | n=25 |
| PB2_B1_S | NT8-bars | CANDIDATE | 23.9 | 0.50 | 4,793 | 3,963 | 4,494 | 4,426 | [-4,896, 13,993] | 0.95 |  | 1,350 | -845 [-5,637, 3,639] | -2.0 [-2.6,-1.3] (MDE 0.9, n 2953) | +4.8 [+1.9,+7.6] (MDE 4.0, n 766) |
| PB2_B1_L | NT8-bars | DEAD | 26.9 | 0.50 | 370 | 386 | -9,644 | 380 | [-9,757, 10,811] | 0.68 |  | -2,530 | -4,891 [-11,375, 1,856] | +4.9 [+3.9,+5.9] (MDE 1.4, n 2652) | +19.2 [+15.5,+22.8] (MDE 5.2, n 721) |
| PB2_B2_M | NT8-bars | DEAD | 17.7 | 0.49 | -99 | -2,567 | 1 | -1,291 | [-9,699, 7,342] |  |  | -3,608 | 0 [0, 0] | +0.0 [+0.0,+0.0] (MDE 0.0, n 2525) | +10.1 [+6.1,+14.1] (MDE 5.8, n 485) |
| PB2_B2_M_Hvol | NT8-bars | DEAD | 11.3 | 0.52 | 5,546 | 4,573 | 7,177 | 5,115 | [-588, 11,552] | 0.88 | 0.97 | 3,114 | 6,406 [-979, 13,170] | +0.8 [-0.1,+1.9] (MDE 1.5, n 808) | +11.1 [+6.0,+15.9] (MDE 7.0, n 230) |
| PB2_B2_M_Hcd | NT8-ticks | DEAD | 14.9 | 0.49 | 3,461 | -4,798 | -3,200 | -500 | [-7,368, 7,145] | 0.80 | 0.85 | -2,506 | 791 [-4,961, 6,567] | +0.5 [-0.3,+1.3] (MDE 1.1, n 1398) | +9.8 [+5.4,+14.2] (MDE 6.2, n 371) |
| PB2_B2_M_Habs | NT8-ticks | DEAD | 7.4 | 0.48 | -3,572 | -2,439 | -2,098 | -3,050 | [-7,649, 1,594] |  | 0.12 | -3,597 | -1,760 [-8,945, 5,230] | +0.7 [-0.5,+2.0] (MDE 1.8, n 493) | +14.6 [+7.6,+21.7] (MDE 10.2, n 145) |
| PB2_B2_M_Hall | NT8-ticks | DEAD | 0.7 LOW | 0.56 | 898 | 926 | -57 | 918 | [-496, 2,720] | 0.90 | 0.82 | 829 | 2,208 [-6,593, 10,732] | n=27 | n=14 |
| PB2_B2_S | NT8-bars | DEAD | 17.1 | 0.50 | 2,318 | 1,384 | -526 | 1,883 | [-5,911, 10,152] | 0.78 |  | -1,271 | 3,174 [-120, 6,553] | -2.3 [-3.1,-1.6] (MDE 1.1, n 2177) | +7.7 [+3.8,+11.4] (MDE 5.3, n 477) |
| PB2_B2_L | NT8-bars | DEAD | 18.9 | 0.47 | -5,453 | -16,207 | -8,614 | -10,680 | [-17,914, -3,380] |  |  | -10,833 | -9,389 [-15,267, -3,398] | +4.9 [+3.7,+6.1] (MDE 1.7, n 1966) | +15.1 [+11.2,+19.1] (MDE 5.7, n 498) |
| PB2_B3_M | NT8-bars | DEAD | 23.5 | 0.50 | 3,360 | 5,294 | -5,100 | 4,316 | [-4,946, 13,509] | 0.80 |  | 1,099 | 0 [0, 0] | +0.0 [+0.0,+0.0] (MDE 0.0, n 3366) | +6.7 [+3.5,+9.8] (MDE 4.4, n 703) |
| PB2_B3_M_Hvol | NT8-bars | DEAD | 15.1 | 0.51 | -83 | 6,564 | 3,465 | 3,124 | [-3,731, 9,954] |  | 0.53 | 805 | -1,193 [-8,293, 6,289] | +0.4 [-0.6,+1.3] (MDE 1.3, n 1086) | +7.1 [+3.2,+11.0] (MDE 5.5, n 287) |
| PB2_B3_M_Hcd | NT8-ticks | DEAD | 19.5 | 0.50 | 679 | 5,325 | 453 | 2,926 | [-5,676, 12,256] | 0.60 | 0.65 | 339 | -1,391 [-8,285, 5,946] | +0.2 [-0.6,+1.0] (MDE 1.2, n 1697) | +7.8 [+4.1,+12.0] (MDE 5.5, n 490) |
| PB2_B3_M_Habs | NT8-ticks | DEAD | 9.1 | 0.50 | -2,016 | 2,758 | -5,595 | 273 | [-4,947, 5,874] |  | 0.42 | -412 | -4,043 [-12,131, 4,265] | +0.5 [-0.9,+2.0] (MDE 2.1, n 636) | +6.4 [+0.1,+12.4] (MDE 8.7, n 192) |
| PB2_B3_M_Hall | NT8-ticks | DEAD | 0.9 LOW | 0.48 | -863 | -86 | -942 | -494 | [-2,122, 1,243] |  | 0.35 | -569 | -4,811 [-13,971, 4,314] | +2.2 [-1.9,+7.8] (MDE 6.8, n 57) | n=17 |
| PB2_B3_S | NT8-bars | DEAD | 22.4 | 0.50 | 2,661 | 3,219 | -2,675 | 2,949 | [-5,509, 12,528] | 0.78 |  | -807 | -1,367 [-6,426, 3,559] | -2.3 [-3.0,-1.6] (MDE 1.1, n 2810) | +4.2 [+1.0,+7.1] (MDE 4.3, n 681) |
| PB2_B3_L | NT8-bars | DEAD | 26.1 | 0.51 | -551 | 10,171 | -3,468 | 4,619 | [-4,777, 14,357] |  |  | 576 | 303 [-6,077, 6,469] | +6.6 [+5.4,+7.8] (MDE 1.8, n 2535) | +15.9 [+12.4,+19.6] (MDE 5.0, n 734) |
| PB2_B4_M | NT8-bars | DEAD | 25.2 | 0.51 | -2,866 | 18,364 | -7,081 | 7,358 | [-709, 15,914] |  |  | 4,928 | 0 [0, 0] | +0.0 [+0.0,+0.0] (MDE 0.0, n 3602) | +9.2 [+5.9,+12.7] (MDE 4.8, n 685) |
| PB2_B4_M_Hvol | NT8-bars | CANDIDATE | 19.0 | 0.52 | 4,600 | 18,044 | 2,576 | 11,119 | [2,915, 18,850] | 0.93 | 0.82 | 8,705 | 3,762 [-3,235, 10,686] | +0.5 [-0.3,+1.2] (MDE 1.1, n 1220) | +10.1 [+5.7,+14.3] (MDE 6.2, n 336) |
| PB2_B4_M_Hcd | NT8-ticks | DEAD | 23.3 | 0.51 | 734 | 16,436 | 139 | 8,316 | [656, 16,955] | 0.60 | 0.53 | 4,503 | 958 [-4,918, 7,353] | -0.0 [-0.8,+0.8] (MDE 1.2, n 1870) | +8.0 [+4.7,+11.8] (MDE 5.1, n 528) |
| PB2_B4_M_Habs | NT8-ticks | DEAD | 11.1 | 0.51 | 2,592 | 4,797 | -406 | 3,674 | [-2,440, 9,999] | 0.78 | 0.78 | 2,513 | -3,684 [-12,105, 4,869] | -0.0 [-1.3,+1.3] (MDE 1.9, n 586) | +11.1 [+5.2,+16.8] (MDE 8.6, n 211) |
| PB2_B4_M_Hall | NT8-ticks | DEAD | 1.2 LOW | 0.50 | -468 | 227 | 619 | -136 | [-2,071, 1,968] |  | 0.35 | -256 | -7,494 [-16,034, 722] | +3.2 [+0.0,+9.6] (MDE 9.1, n 35) | n=20 |
| PB2_B4_S | NT8-bars | DEAD | 24.6 | 0.51 | 2,152 | 17,139 | -503 | 9,399 | [1,773, 18,026] | 0.72 |  | 6,117 | 2,041 [-2,261, 6,374] | -2.4 [-3.1,-1.7] (MDE 1.0, n 2977) | +6.2 [+3.2,+9.3] (MDE 4.3, n 684) |
| PB2_B4_L | NT8-bars | DEAD | 27.1 | 0.50 | -1,695 | 8,213 | -7,856 | 3,074 | [-6,232, 13,219] |  |  | 694 | -4,283 [-10,890, 2,019] | +4.5 [+3.4,+5.7] (MDE 1.6, n 2608) | +19.5 [+15.5,+23.5] (MDE 5.8, n 654) |

Base cells (M) are the comparators; 'delta vs base' of a base cell is 0 by construction. LOW = < 3 trades/wk (never dropped).

### 3.1 Long / short (WF weekly $ at 10 lots, trades/wk)
| cell | long $/wk | long tr/wk | short $/wk | short tr/wk |
|--|--|--|--|--|
| PB2_B1_M | 1,414 | 15.7 | 4,444 | 14.7 |
| PB2_B1_M_Hvol | 2,278 | 10.7 | 3,821 | 10.5 |
| PB2_B1_M_Hcd | 830 | 13.3 | 3,507 | 13.0 |
| PB2_B1_M_Habs | 3,730 | 6.4 | -90 | 4.6 |
| PB2_B1_M_Hall | -688 | 0.7 | 105 | 0.5 |
| PB2_B1_S | 2,154 | 15.3 | 4,624 | 14.0 |
| PB2_B1_L | -784 | 16.7 | -583 | 15.9 |
| PB2_B2_M | -486 | 9.6 | -806 | 10.3 |
| PB2_B2_M_Hvol | 3,455 | 5.6 | 1,740 | 6.0 |
| PB2_B2_M_Hcd | -441 | 7.7 | -916 | 8.5 |
| PB2_B2_M_Habs | 572 | 4.1 | -3,439 | 3.4 |
| PB2_B2_M_Hall | 131 | 0.3 | 786 | 0.3 |
| PB2_B2_S | -517 | 9.1 | 2,090 | 9.8 |
| PB2_B2_L | -3,429 | 10.2 | -6,994 | 10.8 |
| PB2_B3_M | 3,228 | 13.8 | 2,871 | 13.7 |
| PB2_B3_M_Hvol | -3,639 | 7.6 | 5,406 | 8.1 |
| PB2_B3_M_Hcd | -1,499 | 10.8 | 5,264 | 10.8 |
| PB2_B3_M_Habs | 186 | 5.2 | 516 | 4.0 |
| PB2_B3_M_Hall | -1,394 | 0.5 | 900 | 0.4 |
| PB2_B3_S | 3,899 | 13.2 | 3,749 | 12.8 |
| PB2_B3_L | 2,716 | 15.2 | -1,156 | 15.0 |
| PB2_B4_M | 3,717 | 14.9 | 5,346 | 14.3 |
| PB2_B4_M_Hvol | 6,469 | 10.5 | 6,428 | 10.1 |
| PB2_B4_M_Hcd | 4,953 | 13.3 | 4,485 | 12.8 |
| PB2_B4_M_Habs | 2,901 | 6.7 | 1,274 | 4.6 |
| PB2_B4_M_Hall | -657 | 0.8 | 521 | 0.4 |
| PB2_B4_S | 3,964 | 14.5 | 6,224 | 13.5 |
| PB2_B4_L | 3,017 | 15.9 | -1,386 | 15.5 |

### 3.2 Predicted-quiet / predicted-wide columns (WF 2024-02+, trade level, 10 lots; wk-equivalent = sum of net $ / WF weeks)
| cell | quiet n | quiet $/trade | quiet $/wk-eq | quiet paired vs ST | wide n | wide $/trade | wide $/wk-eq | wide paired vs ST |
|--|--|--|--|--|--|--|--|--|
| PB2_B1_M | 1205 | -11 | -93 | +10.1 [+5.6,+15.0] (MDE 6.6, n 256) | 2316 | 311 | 5,042 | +7.1 [+3.4,+10.7] (MDE 5.4, n 496) |
| PB2_B1_M_Hvol | 981 | 402 | 2,759 | +10.4 [+5.0,+16.4] (MDE 8.3, n 131) | 1750 | 397 | 4,862 | +7.1 [+2.1,+12.3] (MDE 7.1, n 238) |
| PB2_B1_M_Hcd | 1124 | -127 | -1,002 | +9.4 [+4.2,+14.5] (MDE 7.5, n 181) | 2083 | 282 | 4,115 | +6.9 [+3.0,+10.8] (MDE 5.6, n 383) |
| PB2_B1_M_Habs | 609 | 54 | 229 | +15.6 [+5.5,+28.5] (MDE 16.4, n 74) | 941 | 484 | 3,184 | +8.0 [+2.4,+14.8] (MDE 8.9, n 153) |
| PB2_B1_M_Hall | 75 | -274 | -144 | n=8 | 103 | -610 | -440 | n=16 |
| PB2_B1_S | 1174 | -23 | -189 | +5.3 [+1.4,+9.4] (MDE 5.7, n 264) | 2215 | 287 | 4,445 | +4.4 [+0.8,+8.0] (MDE 5.3, n 490) |
| PB2_B1_L | 1356 | -194 | -1,844 | +21.2 [+15.8,+26.8] (MDE 8.0, n 260) | 2438 | 114 | 1,937 | +18.3 [+13.3,+23.1] (MDE 7.0, n 442) |
| PB2_B2_M | 915 | -71 | -451 | +11.7 [+5.2,+18.3] (MDE 9.6, n 173) | 1583 | -83 | -920 | +9.0 [+3.7,+14.1] (MDE 7.3, n 307) |
| PB2_B2_M_Hvol | 591 | 48 | 198 | +7.1 [-0.3,+14.7] (MDE 10.7, n 83) | 1006 | 622 | 4,378 | +13.5 [+7.3,+20.1] (MDE 9.3, n 144) |
| PB2_B2_M_Hcd | 743 | -240 | -1,246 | +11.1 [+4.3,+18.4] (MDE 10.2, n 128) | 1368 | 46 | 444 | +9.3 [+3.3,+15.1] (MDE 8.3, n 238) |
| PB2_B2_M_Habs | 433 | -400 | -1,212 | +20.0 [+10.3,+31.2] (MDE 15.6, n 54) | 615 | -427 | -1,835 | +11.5 [+3.3,+20.5] (MDE 12.4, n 90) |
| PB2_B2_M_Hall | 40 | 3,043 | 851 | n=3 | 53 | -30 | -11 | n=11 |
| PB2_B2_S | 884 | -103 | -636 | +7.5 [+1.6,+14.1] (MDE 9.1, n 170) | 1535 | 209 | 2,244 | +7.6 [+3.1,+12.0] (MDE 6.4, n 302) |
| PB2_B2_L | 940 | -268 | -1,762 | +16.4 [+9.9,+22.9] (MDE 9.5, n 162) | 1740 | -716 | -8,709 | +14.3 [+9.2,+19.6] (MDE 7.6, n 331) |
| PB2_B3_M | 1197 | 108 | 908 | +5.1 [+0.2,+9.9] (MDE 7.0, n 239) | 2138 | 200 | 2,984 | +7.7 [+3.6,+11.6] (MDE 5.7, n 456) |
| PB2_B3_M_Hvol | 756 | 207 | 1,096 | +10.4 [+4.5,+16.7] (MDE 8.9, n 97) | 1379 | 189 | 1,818 | +5.5 [+0.5,+10.6] (MDE 7.3, n 189) |
| PB2_B3_M_Hcd | 967 | -110 | -746 | +9.1 [+3.6,+15.0] (MDE 8.1, n 163) | 1803 | 288 | 3,636 | +7.3 [+1.8,+12.5] (MDE 7.5, n 319) |
| PB2_B3_M_Habs | 511 | 139 | 495 | +10.7 [+3.5,+19.5] (MDE 11.6, n 64) | 784 | -40 | -219 | +4.3 [-4.3,+13.0] (MDE 12.2, n 126) |
| PB2_B3_M_Hall | 44 | 201 | 62 | n=3 | 86 | -795 | -478 | n=14 |
| PB2_B3_S | 1138 | 101 | 801 | +2.0 [-2.8,+6.7] (MDE 6.8, n 232) | 2040 | 156 | 2,231 | +5.4 [+1.3,+9.1] (MDE 5.5, n 440) |
| PB2_B3_L | 1302 | 121 | 1,098 | +17.4 [+11.1,+23.7] (MDE 8.8, n 251) | 2394 | 206 | 3,444 | +15.2 [+11.0,+19.3] (MDE 6.0, n 472) |
| PB2_B4_M | 1194 | -74 | -620 | +8.9 [+4.5,+13.8] (MDE 6.6, n 220) | 2376 | 456 | 7,577 | +9.3 [+4.9,+13.5] (MDE 6.1, n 456) |
| PB2_B4_M_Hvol | 954 | 333 | 2,224 | +10.4 [+4.4,+17.7] (MDE 9.4, n 114) | 1727 | 743 | 8,968 | +9.7 [+4.4,+15.3] (MDE 7.9, n 215) |
| PB2_B4_M_Hcd | 1136 | -104 | -830 | +9.1 [+3.3,+15.2] (MDE 8.4, n 165) | 2160 | 639 | 9,657 | +7.5 [+3.2,+12.2] (MDE 6.4, n 352) |
| PB2_B4_M_Habs | 600 | -37 | -155 | +14.9 [+3.6,+26.5] (MDE 17.2, n 65) | 974 | 583 | 3,970 | +9.6 [+2.5,+17.6] (MDE 11.0, n 142) |
| PB2_B4_M_Hall | 72 | 46 | 23 | n=7 | 98 | -232 | -159 | n=12 |
| PB2_B4_S | 1174 | 129 | 1,058 | +5.2 [+0.9,+9.5] (MDE 6.5, n 226) | 2312 | 523 | 8,463 | +6.7 [+2.7,+11.2] (MDE 6.0, n 451) |
| PB2_B4_L | 1334 | 152 | 1,417 | +20.5 [+15.1,+26.9] (MDE 8.7, n 225) | 2513 | 126 | 2,219 | +19.1 [+13.7,+24.3] (MDE 7.7, n 416) |
| PB2B_B1_LAD_T10_i62 | 2559 | 301 | 5,388 | +24.1 [+17.7,+31.1] (MDE 9.5, n 424) | 5279 | -97 | -3,578 | +19.5 [+15.0,+24.0] (MDE 6.5, n 951) |
| PB2B_B1_LAD_T30_i62 | 2740 | 115 | 2,201 | +21.3 [+14.9,+27.8] (MDE 9.2, n 446) | 5372 | -102 | -3,827 | +21.2 [+16.7,+25.8] (MDE 6.5, n 894) |
| PB2B_B1_LAD_T30_iATR | 3069 | 95 | 2,030 | +22.0 [+16.1,+27.8] (MDE 8.4, n 552) | 6071 | 91 | 3,864 | +19.6 [+15.0,+23.7] (MDE 6.0, n 1039) |
| PB2B_B1_LAD_T30_iSW | 3050 | 200 | 4,274 | +21.0 [+15.3,+27.2] (MDE 8.3, n 553) | 5939 | 61 | 2,534 | +21.1 [+16.8,+25.5] (MDE 6.3, n 1034) |
| PB2B_B1_SGL_T30_i62 | 1235 | -152 | -1,314 | +19.2 [+13.0,+25.3] (MDE 9.3, n 207) | 2195 | 101 | 1,550 | +17.7 [+13.6,+22.3] (MDE 6.4, n 378) |
| PB2B_B1_SC2_T30_i62 | 1761 | 32 | 399 | +19.8 [+13.5,+26.3] (MDE 9.2, n 288) | 3324 | 155 | 3,605 | +20.1 [+15.6,+24.9] (MDE 6.7, n 552) |
| PB2B_B2_LAD_T10_i62 | 1281 | 727 | 6,517 | +17.0 [+9.4,+25.6] (MDE 11.1, n 265) | 2701 | -195 | -3,687 | +16.0 [+9.9,+22.1] (MDE 9.0, n 566) |
| PB2B_B2_LAD_T30_i62 | 1437 | 241 | 2,419 | +16.0 [+8.6,+23.4] (MDE 10.4, n 263) | 2856 | -196 | -3,919 | +16.0 [+9.4,+23.4] (MDE 10.1, n 573) |
| PB2B_B2_LAD_T30_iATR | 2157 | -318 | -4,799 | +21.6 [+14.2,+29.2] (MDE 10.6, n 301) | 4224 | -501 | -14,809 | +18.1 [+12.4,+24.0] (MDE 8.3, n 652) |
| PB2B_B2_LAD_T30_iSW | 1882 | 257 | 3,376 | +19.7 [+12.9,+27.1] (MDE 10.0, n 347) | 3840 | -70 | -1,881 | +18.4 [+12.4,+24.8] (MDE 8.8, n 700) |
| PB2B_B2_SGL_T30_i62 | 704 | 502 | 2,471 | +13.3 [+6.5,+20.2] (MDE 9.7, n 132) | 1228 | -284 | -2,436 | +12.3 [+6.3,+18.6] (MDE 8.9, n 240) |
| PB2B_B2_SC2_T30_i62 | 960 | 572 | 3,842 | +14.4 [+8.0,+22.9] (MDE 10.5, n 182) | 1700 | -146 | -1,735 | +15.4 [+8.8,+22.1] (MDE 9.7, n 333) |
| PB2B_B3_LAD_T10_i62 | 2473 | 75 | 1,301 | +23.5 [+16.6,+30.6] (MDE 10.1, n 496) | 5287 | -185 | -6,824 | +16.3 [+11.4,+21.0] (MDE 6.9, n 1028) |
| PB2B_B3_LAD_T30_i62 | 2605 | 37 | 678 | +22.2 [+15.7,+29.2] (MDE 9.9, n 467) | 5330 | -93 | -3,482 | +18.5 [+14.2,+23.2] (MDE 6.4, n 1017) |
| PB2B_B3_LAD_T30_iATR | 2846 | -298 | -5,928 | +19.3 [+13.7,+25.2] (MDE 8.3, n 498) | 5659 | 6 | 235 | +17.6 [+13.5,+21.9] (MDE 6.1, n 1039) |
| PB2B_B3_LAD_T30_iSW | 2839 | -230 | -4,559 | +18.9 [+12.8,+24.9] (MDE 8.7, n 496) | 5651 | -6 | -232 | +17.6 [+13.3,+22.1] (MDE 6.3, n 1032) |
| PB2B_B3_SGL_T30_i62 | 1224 | -202 | -1,728 | +15.7 [+9.1,+22.8] (MDE 9.7, n 207) | 2219 | 284 | 4,403 | +14.6 [+10.6,+19.0] (MDE 6.1, n 428) |
| PB2B_B3_SC2_T30_i62 | 1773 | -212 | -2,627 | +18.5 [+12.2,+25.4] (MDE 9.2, n 313) | 3309 | -26 | -605 | +15.8 [+11.5,+20.3] (MDE 6.1, n 597) |
| PB2B_B4_LAD_T10_i62 | 2537 | 401 | 7,109 | +22.6 [+15.2,+29.9] (MDE 10.5, n 375) | 5218 | 119 | 4,325 | +19.6 [+14.8,+24.1] (MDE 7.0, n 900) |
| PB2B_B4_LAD_T30_i62 | 2698 | 325 | 6,138 | +20.6 [+13.9,+27.3] (MDE 9.9, n 414) | 5376 | 6 | 224 | +20.4 [+15.7,+25.4] (MDE 7.0, n 871) |
| PB2B_B4_LAD_T30_iATR | 3128 | 160 | 3,496 | +21.9 [+15.6,+28.0] (MDE 9.0, n 506) | 6203 | -51 | -2,225 | +21.6 [+17.0,+26.1] (MDE 6.2, n 1021) |
| PB2B_B4_LAD_T30_iSW | 3028 | 145 | 3,076 | +20.5 [+14.5,+26.5] (MDE 8.8, n 518) | 5828 | -24 | -988 | +22.9 [+18.6,+27.2] (MDE 6.3, n 1007) |
| PB2B_B4_SGL_T30_i62 | 1226 | 209 | 1,795 | +19.7 [+13.2,+26.5] (MDE 9.5, n 201) | 2227 | 284 | 4,427 | +19.0 [+14.7,+24.0] (MDE 6.7, n 378) |
| PB2B_B4_SC2_T30_i62 | 1753 | 195 | 2,385 | +22.4 [+15.9,+29.2] (MDE 9.5, n 277) | 3306 | 244 | 5,639 | +21.2 [+16.6,+25.8] (MDE 6.6, n 540) |

## 4. Entry style: fill rate and the selection effect (all armed episodes, full sample)
Episode = run (<=60 bars) of armed bars; filled = some per-minute limit at the level trades through by 1 tick; mkt pts = raw points of a hypothetical market trade (DS2 bracket) entered at the first armed bar's next open. SE ~0.3-0.4 pt.
| base | episodes | fill rate | mkt pts, filled episodes | mkt pts, UNFILLED episodes | gap |
|--|--|--|--|--|--|
| B1 | 61,010 | 0.63 | -5.4 | +14.4 | +19.8 |
| B2 | 40,950 | 0.50 | -7.1 | +10.1 | +17.2 |
| B3 | 51,456 | 0.50 | -7.2 | +11.2 | +18.4 |
| B4 | 63,718 | 0.62 | -4.4 | +13.0 | +17.4 |

Per-trade cost view (raw points per trade before cost mapping, whole sample, DS2 bracket): market base cells earn +0.3..+1.4 raw pt/trade; PB2B rungs earn -1.8..+1.7 (see PB2B table); the entry-price improvement of a passive fill (up to 5-10 pts per rung) is more than consumed by the worse outcome of the fills.

## 5. PB2B P5 ladder (24 cells)
| cell | verdict | ep fill rate | rung tr/wk (WF) | PRE $/wk | HOLD | 2023 span | WF | WF CI | placebo | 2x cost WF | credited (-0.4 pt) WF | raw pt/rung | raw pt/trade M base | delta vs base M WF [CI] | paired vs base pts [CI] (MDE) | paired vs ST pts [CI] (MDE) |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| PB2B_B1_LAD_T10_i62 | DEAD | 0.21 | 55.5 | -3,242 | 4,406 | -2,370 | 426 | [-6,168, 7,600] |  | -904 | 1,729 | 1.27 | 1.43 | -4,845 [-13,147, 3,822] | +8.4 [+7.0,+9.8] (MDE 2.0, n 4162) | +21.0 [+17.4,+24.6] (MDE 5.3, n 1399) |
| PB2B_B1_LAD_T30_i62 | DEAD | 0.42 | 57.5 | -2,865 | 1,936 | -4,025 | -569 | [-6,924, 6,199] |  | -2,454 | 891 | 0.72 | 1.43 | -5,839 [-14,031, 1,607] | +10.9 [+9.3,+12.5] (MDE 2.4, n 3960) | +21.2 [+17.7,+24.7] (MDE 5.1, n 1366) |
| PB2B_B1_LAD_T30_iATR | DEAD | 0.43 | 64.7 | 269 | 3,774 | -2,707 | 1,962 | [-6,383, 10,842] | 0.70 | -952 | 3,547 | 1.17 | 1.43 | -3,309 [-11,078, 4,877] | +10.8 [+9.2,+12.4] (MDE 2.3, n 4947) | +20.3 [+17.2,+23.6] (MDE 4.6, n 1623) |
| PB2B_B1_LAD_T30_iSW | DEAD | 0.42 | 63.5 | 1,394 | 3,164 | -2,802 | 2,258 | [-5,258, 10,341] | 0.75 | -109 | 3,796 | 0.80 | 1.43 | -3,012 [-10,531, 4,792] | +11.1 [+9.6,+12.7] (MDE 2.3, n 4565) | +20.9 [+17.7,+24.3] (MDE 4.9, n 1619) |
| PB2B_B1_SGL_T30_i62 | DEAD | 0.42 | 24.2 | -3,533 | 4,857 | -3,360 | 491 | [-8,189, 9,437] |  | -2,320 | 2,017 | 0.90 | 1.43 | -4,780 [-11,815, 3,214] | +8.0 [+6.6,+9.4] (MDE 2.0, n 1824) | +18.3 [+14.7,+22.0] (MDE 5.2, n 597) |
| PB2B_B1_SC2_T30_i62 | DEAD | 0.42 | 36.0 | -314 | 4,845 | -3,115 | 2,173 | [-3,722, 8,596] |  | 107 | 3,564 | 1.01 | 1.43 | -3,098 [-10,492, 4,280] | +8.6 [+7.3,+10.2] (MDE 2.1, n 2506) | +19.9 [+16.3,+23.7] (MDE 5.3, n 858) |
| PB2B_B2_LAD_T10_i62 | DEAD | 0.28 | 28.2 | 3,919 | -2,588 | -1,985 | 806 | [-4,231, 5,486] | 0.88 | -134 | 1,522 | 0.82 | 0.34 | 2,097 [-5,784, 9,761] | +9.4 [+7.3,+11.5] (MDE 3.0, n 2232) | +16.3 [+11.1,+21.2] (MDE 7.4, n 843) |
| PB2B_B2_LAD_T30_i62 | DEAD | 0.50 | 30.4 | 4,125 | -5,858 | -4,603 | -663 | [-6,148, 4,386] | 0.97 | -1,442 | 163 | 0.11 | 0.34 | 628 [-7,152, 8,196] | +10.2 [+8.0,+12.4] (MDE 3.2, n 2268) | +15.9 [+10.7,+20.7] (MDE 6.8, n 846) |
| PB2B_B2_LAD_T30_iATR | DEAD | 0.42 | 45.1 | -3,114 | -10,766 | -8,252 | -6,828 | [-13,476, -54] |  | -8,495 | -5,596 | -1.85 | 0.34 | -5,538 [-12,272, 807] | +10.1 [+8.5,+11.6] (MDE 2.2, n 3901) | +19.1 [+14.4,+23.8] (MDE 6.8, n 963) |
| PB2B_B2_LAD_T30_iSW | DEAD | 0.46 | 40.4 | 5,455 | -5,453 | -5,040 | 230 | [-5,534, 6,217] | 0.93 | -1,059 | 1,198 | 0.04 | 0.34 | 1,520 [-5,140, 8,034] | +10.4 [+8.6,+12.1] (MDE 2.5, n 3349) | +18.8 [+14.0,+23.1] (MDE 6.6, n 1057) |
| PB2B_B2_SGL_T30_i62 | DEAD | 0.50 | 13.6 | 5,197 | -6,218 | -768 | -275 | [-6,124, 6,122] | 0.90 | -1,752 | 1,147 | 1.11 | 0.34 | 1,016 [-7,177, 8,491] | +6.1 [+4.2,+7.9] (MDE 2.6, n 1071) | +12.8 [+8.1,+17.7] (MDE 6.8, n 376) |
| PB2B_B2_SC2_T30_i62 | DEAD | 0.50 | 18.8 | 3,451 | -1,904 | 1,242 | 892 | [-3,757, 5,755] | 0.97 | 27 | 1,632 | 1.62 | 0.34 | 2,182 [-6,000, 9,789] | +6.9 [+5.0,+8.6] (MDE 2.6, n 1397) | +15.1 [+10.7,+20.1] (MDE 6.9, n 520) |
| PB2B_B3_LAD_T10_i62 | DEAD | 0.22 | 54.9 | -2,472 | -905 | -4,610 | -1,733 | [-7,769, 4,456] |  | -3,958 | -130 | 0.37 | 1.37 | -6,050 [-13,621, 1,249] | +10.1 [+8.6,+11.6] (MDE 2.2, n 4647) | +18.5 [+14.6,+22.4] (MDE 5.7, n 1549) |
| PB2B_B3_LAD_T30_i62 | DEAD | 0.41 | 56.2 | -725 | -1,300 | -4,504 | -1,008 | [-7,889, 5,971] |  | -3,138 | 231 | 0.56 | 1.37 | -5,324 [-12,677, 1,922] | +11.9 [+10.1,+13.5] (MDE 2.4, n 4359) | +19.4 [+16.1,+23.2] (MDE 5.2, n 1505) |
| PB2B_B3_LAD_T30_iATR | DEAD | 0.41 | 60.2 | -2,112 | -1,684 | -2,472 | -1,920 | [-9,099, 5,352] |  | -3,130 | -334 | 0.81 | 1.37 | -6,236 [-14,056, 888] | +12.0 [+10.2,+13.7] (MDE 2.4, n 4600) | +18.1 [+14.6,+21.7] (MDE 5.0, n 1560) |
| PB2B_B3_LAD_T30_iSW | DEAD | 0.41 | 60.1 | -1,938 | -1,304 | -2,260 | -1,646 | [-8,865, 5,864] |  | -2,776 | -200 | 0.76 | 1.37 | -5,962 [-13,337, 1,117] | +12.0 [+10.4,+13.7] (MDE 2.4, n 4585) | +17.9 [+14.5,+21.7] (MDE 5.1, n 1551) |
| PB2B_B3_SGL_T30_i62 | DEAD | 0.42 | 24.3 | -544 | 6,105 | -2,364 | 2,661 | [-6,136, 11,634] |  | -555 | 4,749 | 0.85 | 1.37 | -1,656 [-8,435, 4,741] | +8.4 [+7.1,+9.8] (MDE 1.9, n 2068) | +14.9 [+11.5,+18.5] (MDE 5.1, n 644) |
| PB2B_B3_SC2_T30_i62 | DEAD | 0.42 | 36.0 | -72 | -2,656 | -2,284 | -1,320 | [-8,398, 5,973] |  | -3,218 | 369 | 0.58 | 1.37 | -5,636 [-12,370, 915] | +8.7 [+7.3,+10.2] (MDE 2.0, n 2893) | +16.8 [+13.4,+20.6] (MDE 5.1, n 925) |
| PB2B_B4_LAD_T10_i62 | DEAD | 0.21 | 55.0 | -998 | 8,698 | -3,713 | 3,674 | [-3,094, 10,391] |  | 2,092 | 4,820 | 1.35 | 1.40 | -3,684 [-11,862, 3,771] | +8.4 [+6.9,+9.8] (MDE 2.1, n 3635) | +20.5 [+16.7,+24.8] (MDE 5.7, n 1303) |
| PB2B_B4_LAD_T30_i62 | DEAD | 0.42 | 57.3 | -707 | 5,295 | -2,033 | 2,184 | [-4,219, 8,480] |  | 359 | 3,832 | 1.00 | 1.40 | -5,173 [-12,416, 1,955] | +11.6 [+9.9,+13.3] (MDE 2.6, n 3463) | +20.3 [+16.4,+24.2] (MDE 5.5, n 1308) |
| PB2B_B4_LAD_T30_iATR | DEAD | 0.44 | 66.0 | -3,585 | 3,677 | 1,717 | -106 | [-7,469, 7,635] |  | -2,007 | 1,484 | 1.33 | 1.40 | -7,464 [-14,760, -778] | +9.8 [+8.4,+11.4] (MDE 2.1, n 4687) | +21.4 [+18.1,+25.1] (MDE 4.9, n 1556) |
| PB2B_B4_LAD_T30_iSW | DEAD | 0.43 | 62.9 | 79 | 1,433 | -585 | 733 | [-7,177, 8,314] | 0.60 | -1,015 | 2,087 | 0.83 | 1.40 | -6,624 [-13,819, -23] | +11.5 [+9.8,+13.1] (MDE 2.4, n 4034) | +21.8 [+18.2,+25.3] (MDE 5.1, n 1554) |
| PB2B_B4_SGL_T30_i62 | DEAD | 0.42 | 24.5 | 1,150 | 11,338 | 3,882 | 6,074 | [-2,581, 15,143] | 0.70 | 3,283 | 6,935 | 1.57 | 1.40 | -1,284 [-9,073, 5,754] | +8.3 [+6.9,+9.9] (MDE 2.2, n 1616) | +19.1 [+15.6,+22.8] (MDE 5.3, n 589) |
| PB2B_B4_SC2_T30_i62 | DEAD | 0.42 | 35.8 | -800 | 9,133 | 654 | 3,987 | [-2,349, 10,055] |  | 2,156 | 5,199 | 1.75 | 1.40 | -3,370 [-10,556, 3,848] | +9.2 [+7.6,+11.0] (MDE 2.3, n 2213) | +21.3 [+17.5,+25.5] (MDE 5.6, n 834) |

Three-way style comparison per base on PRE weekly $ (M | S | L | best ladder | single | scale-in): see tables 3 and 5. Single frozen limit and scale-in on the second touch do not rescue the passive style; the 3-rung ladder lowers the adverse-selection loss per rung only by averaging into a deeper retrace, not by turning it positive.

## 6. DS3 mix (ds3_addbook, base KB+SM+EM, risk parity, per-book locks, 50-cap line; MAPPED series, locks from the lock engine at 10 lots; 2 holdout re-reads disclosed)
| cell | marginal Sharpe add-one WF-PRE / WF / HOLD | delta maxDD 27-contract WF / HOLD | delta maxDD 50-cap WF / HOLD | corr WF to ST / HM / DS2 |
|--|--|--|--|--|
| PB2_B1_S | -0.21 / -0.26 / -0.32 | 56,179 / 82,979 | 138,176 / 167,380 | 0.52 / 0.39 / 0.56 |
| PB2_B4_M_Hvol | +0.06 / +0.45 / +0.88 | -5,248 / -36,567 | 65,511 / 14,099 | 0.28 / 0.32 / 0.37 |

PB2_B1_S lowers the portfolio Sharpe (-0.26 WF, -0.32 HOLD) and raises maxDD: it is not a DS3 add. PB2_B4_M_Hvol raises it (+0.45 WF, +0.88 HOLD) with maxDD lower at the 27-contract line (-5k WF, -37k HOLD) and higher at the cap line (+66k WF, +14k HOLD); corr to DS2 0.37. Peak lots: nominal 10 (one position at a time); this is a best-of-52 candidate with a 0.82 subset-placebo rank, so the mix line is not evidence for the health condition.

## 7. Executability
M and S with Hvol or no health condition: NT8-bars (1-min bars, volume per bar, a buy-stop order for S). Hcd and Habs: NT8-ticks (cumulative delta / absorption need bid-ask-classified ticks via OnMarketData or Tick Replay; no L2 depth at runtime; not computable from OHLCV bars). L, ladder, single and scale-in: resting limit orders are placeable in NT8 (bars + limit orders); their fills are an execution-server/queue question (this study uses the conservative 1-tick trade-through rule), and all are DEAD anyway. The two candidates: PB2_B1_S = NT8-bars (10-min Supertrend from 1-min series, 5-min EMA20, buy-stop); PB2_B4_M_Hvol = NT8-bars (5-min EMA200/EMA20, 1-min volume). EMA20/EMA200/Supertrend/volume are reproducible from chart data; no identity test run (not PASS).

## 8. Direct L2 replay status
Top-10 M/S cells by PRE (PB2_B2_M_Hvol, B1_S, B4_M_Hvol, B1_M, B2_M_Hcd, B1_M_Habs, B3_M, B3_S, B4_M_Habs, B2_S; 31,184 unique trades, S10x1 + XJ3, arms EM and S10x1_g2) are queued through corepool/replay governor (orchestrator pb2_direct.py orch, outputs /mnt/l2/l2vast/ds3_pb2/, rows out/pb2/direct_rows.parquet, tabs direct_tabs.pkl). Not finished at the time of this report: all verdicts above are MAPPED. L/ladder cells are MAPPED-only (the replay harness has market arms only; a resting-order replay with the queue model was not built) - declared, and they are DEAD on the mapped basis, which is the optimistic side for passive fills only if the trade-through rule is too strict (it is conservative vs queue fills, but the episode analysis uses the same rule; a queue-model fill at touch would raise the fill rate and lower the adverse selection, not remove it).

## 9. Best-of-N, nearest cells, caveats
Best-of-52: with 52 cells and a per-cell placebo of 0.95 the expected number of chance CANDIDATEs is several; observing 2 CANDIDATE and 0 PASS is chance-level. Nearest scored cells: REPORT_PULLBACK (0 of 41 levels respected), T4.2 L0/Lm2/LB0 (passive limit at flip level: +0.07/+0.07/-0.46 pt/trade) - PB2 reproduces the sign of the T4 block-limit result. B4 (EMA200 regime) is a high-holdout base with negative PRE: window dependence, not a stable pullback edge. The base cells here are D3PB2's own declarations and are not the D3PB/D3PB3/D3PB4 top cells; the health/style conditions were not re-run on those cells (see PULLBACK_LEADERBOARD.md for their rankings); the code takes any (regime, level) pair so it is a drop-in.

Deliverables: autopilot/DS3_TPULLBACK2.md (this), l2vast/ds3/rows/DS3_TPULLBACK2.json, SERIES l2vast/ds3/out/SERIES/PB2_B1_S.parquet, PB2_B4_M_Hvol.parquet, code l2vast/ds3/code/te/pb2_*.py, results l2vast/ds3/out/pb2/.
