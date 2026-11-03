# DS3_SIZER_Q6 - Q1-A is the reference: is there any ER-based variant that improves it? (ZL-2, 2026-11-03T17:25Z; ledger; analysis only, the user decides)
Prereg SIZER_Q6_PREREG.md sha256 a6ab552dbcd778e79d96c4782ca5102250ceed788d777be83d639f8fa66cfdff (DECISIONS.md, before any Q6 statistic). **Frame: run_v13t_ts2 = V13T_LIVE costs (take lines off, market exits 0.80, stops 2.45 worse), LIVE lot order session -> A06 slot / B02 (one rounding) -> ER -> zone HALF last, lock R scaled only when mult > 1 (never for Q1-A), per-book locks only; stale/gap bars kept as live; weekly composite of the six live books.** Reference = Q1-A (ER(20) 5-min closes: x0.5 below .30, x1.0 at or above), live since 2026-11-02 19:30Z. Cut > 0 = shallower maxDD than Q1-A; "dropped" = 2026 W29-W39 removed from base and cell.

**ANSWER.** No ER-based variant improves Q1-A in a way that survives the checks. Of the 23 new ER-sizer cells (binary thresholds .20-.45, x0.5/x0.75/x1.0 tiers, continuous maps, ER windows 14/20/30 on 3m/5m bars), 20 are inside the mean tolerance and the best by the user's key (maxDD at same-or-better mean, L6M then PRE, W29-W39 dropped) is WIN_3m_30 with L6M-dropped cut +6.4% and PRE cut +3.6% (mean -4.9k / -2.4k per week vs Q1-A). In 100 shuffled-day worlds the best cell of the same family reaches that key in 83% of worlds and the number of flagged cells is 2 or more in 87% (median 7), so the family is not distinguishable from noise. Walk-forward on the choice: the choice was BIN_0.35 10, BIN_0.40 9, REF 9, TIER_0.30_0.40 6 over 2024-01..2026-10 and the out-of-sample result vs Q1-A is PRE +5.1%, L6M-dropped +0.0%, HOLD-dropped -2.4% maxDD with mean -1.3k / +0.0k / -0.1k per week. ER at the add (closes addendum 2.1): halving the add on a low ER at the add (ADD_H) or on an ER drop (ADD_D) changes nothing material (L6M cut +0.5% / +1.2%, PRE +2.5% / +2.5%); cancelling the add when ER at the add < .30 (ADD_C) cuts L6M maxDD +20.7% (+27.9% with W29-W39 dropped) but PRE -6.2% (worse) and costs -1.4k / -2.3k per week, outside the mean tolerance in PRE, so it is neither ranked nor flagged - the add cannot be filtered by ER. The old x1.5 ladder (history) is +36% worse in L6M maxDD and +67% worse in PRE than Q1-A for +10.6k / +4.8k per week. Recommendation in this ledger: leave Q1-A as is; no cell is flagged.

## 1. Reference Q1-A (ts2) and the old x0.5/x1.5 ladder as history
| window | Q1-A mean $k/wk | Q1-A maxDD $k | old ladder mean | old ladder maxDD | old minus Q1-A mean | maxDD |
|--|--|--|--|--|--|--|
| L6M | 27.0 | 104.8 | 37.6 | 142.6 | +10.6 | +37.8 |
| HOLD | 22.6 | 122.0 | 31.7 | 142.6 | +9.1 | +20.6 |
| MID | 16.9 | 59.7 | 23.7 | 43.3 | +6.8 | -16.4 |
| PRE | 13.2 | 88.2 | 18.0 | 147.6 | +4.8 | +59.5 |
| X' | 3.3 | 80.8 | 4.1 | 96.8 | +0.8 | +16.0 |
| F9 | 24.5 | 104.8 | 34.2 | 142.6 | +9.7 | +37.8 |

## 2. New ER-based sizer family vs Q1-A (23 cells), ranked by the key = min(L6M-dropped cut, PRE cut) among cells with mean >= Q1-A mean - MDE
| rank | cell | mean lots | L6M cut (dropped) | HOLD | MID | PRE | X' | d mean L6M (MDE) | d mean PRE (MDE) | equal-risk d mean $k L6M-dr / PRE | raw flag |
|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | WIN_3m_30 | 2.18 | -3.8% (+6.4%) | -9.3% | +9.6% | +3.6% | +0.3% | -3.4k (6.1k) | -2.4k (2.6k) | -1.4 / -2.4 | flag-raw |
| 2 | BIN_0.40 | 2.09 | +39.3% (+0.1%) | -2.4% | +7.2% | +8.6% | +6.0% | -2.0k (6.0k) | -1.6k (2.4k) | -5.5 / n/p | flag-raw |
| 3 | CONT_0.25_0.35 | 2.30 | +12.4% (-0.5%) | -0.4% | +3.0% | +0.6% | +0.2% | +0.3k (2.0k) | -0.5k (0.7k) | -1.2 / -0.0 |  |
| 4 | TIER_0.30_0.40 | 2.21 | +23.3% (-0.6%) | -1.2% | +5.3% | +6.4% | -3.9% | -1.2k (3.8k) | -1.4k (1.9k) | -3.9 / -1.1 |  |
| 5 | TIER_0.30_0.35 | 2.26 | +17.5% (-0.8%) | -4.2% | +2.6% | +2.6% | +4.7% | -0.4k (3.2k) | -0.8k (1.3k) | -2.5 / -0.4 |  |
| 6 | BIN_0.35 | 2.20 | +24.6% (-0.9%) | -6.7% | +1.4% | +1.5% | +6.4% | -1.2k (4.7k) | -1.1k (2.0k) | -3.7 / -0.6 |  |
| 7 | CONT_0.30_0.50 | 2.09 | +39.6% (-1.1%) | -5.1% | +3.3% | +12.4% | +3.9% | -2.8k (5.7k) | -2.1k (2.3k) | -7.0 / -0.7 |  |
| 8 | CONT_0.20_0.45 | 2.24 | +19.0% (-2.5%) | -5.9% | -0.7% | +5.0% | -9.3% | -1.4k (3.6k) | -1.7k (1.9k) | -4.6 / -0.5 |  |
| 9 | BIN_0.25 | 2.43 | -5.2% (-3.9%) | -8.3% | +3.7% | -0.3% | -12.0% | +0.4k (5.7k) | -0.7k (2.2k) | n/a |  |
| 10 | TIER_0.25_0.40 | 2.27 | +18.4% (-4.4%) | -1.0% | +5.5% | +8.0% | -11.5% | -0.0k (4.1k) | -1.4k (2.0k) | n/a |  |
| 11 | WIN_5m_30 | 2.13 | +6.6% (+15.7%) | -22.8% | -30.9% | -4.5% | +4.3% | -4.1k (8.3k) | -1.2k (2.7k) | n/a |  |
| 12 | CONT_0.20_0.40 | 2.30 | +25.5% (-5.4%) | +2.9% | +4.5% | +4.3% | -9.5% | -0.1k (3.3k) | -0.9k (1.7k) | n/a |  |
| 13 | TIER_0.25_0.35 | 2.32 | -0.9% (-5.9%) | -3.4% | +2.7% | +5.4% | -2.9% | -0.1k (4.4k) | -0.8k (1.9k) | n/a |  |
| 14 | WIN_3m_14 | 2.46 | +47.0% (+11.2%) | -25.4% | -39.0% | -6.7% | -18.3% | -1.5k (12.7k) | -2.5k (3.9k) | n/a |  |
| 15 | BIN_0.20 | 2.56 | +14.2% (-8.2%) | -18.4% | -1.2% | +0.2% | -28.8% | -1.9k (8.8k) | +0.5k (2.8k) | n/a |  |
| 16 | TIER_0.20_0.40 | 2.34 | +31.2% (-12.5%) | -6.0% | +4.5% | +9.5% | -10.3% | -0.6k (5.3k) | -0.6k (2.2k) | n/a |  |
| 17 | WIN_3m_20 | 2.34 | +43.0% (+7.5%) | -15.7% | -35.6% | -13.2% | +1.3% | -1.1k (9.1k) | -2.3k (3.8k) | n/a |  |
| 18 | TIER_0.20_0.35 | 2.39 | +13.6% (-14.0%) | -8.3% | +1.7% | +6.9% | -1.3% | -0.2k (5.0k) | +0.3k (1.8k) | n/a |  |
| 19 | TIER_0.20_0.45 | 2.30 | +31.2% (-15.2%) | -7.0% | +3.0% | +8.1% | -2.6% | -0.7k (5.7k) | -1.7k (2.6k) | n/a |  |
| 20 | WIN_5m_14 | 2.45 | +20.0% (-34.0%) | -22.5% | -19.9% | +0.2% | -18.5% | -1.4k (6.3k) | -0.6k (3.4k) | n/a |  |
| - | BIN_0.45 | 2.01 | +39.2% (-1.9%) | -9.9% | -8.1% | +9.1% | +14.9% | -2.6k (7.5k) | -3.1k (2.8k) | n/a |  |
| - | TIER_0.25_0.45 | 2.23 | +32.4% (-7.0%) | -2.0% | +4.0% | +6.6% | -3.9% | -0.4k (4.5k) | -2.4k (2.3k) | n/a |  |
| - | TIER_0.30_0.45 | 2.17 | +37.3% (-3.3%) | -2.3% | +3.9% | +14.1% | +3.7% | -1.4k (4.2k) | -2.3k (2.1k) | n/a |  |

"flag-raw" = beats Q1-A on maxDD in L6M and PRE with W29-W39 dropped and mean inside the MDE; it becomes a FLAG only if also placebo-clean (section 5). equal-risk column = exact lot scan lscale .8-1.6: mean of the cell minus Q1-A's at the same maxDD (points within +-7.5%; n/p = no point).

## 3. Best-of-N null (100 shuffled-day worlds; ER unrelated to outcomes; the 23 cells rebuilt and scored against the world's Q1-A; run on the ts base = zone before ER, as a chance proxy because one ts2 engine run takes 6 s after a 16-minute one-time setup per process)
| statistic | real | null median | null p90 | null max | share of worlds >= real |
|--|--|--|--|--|--|
| S1 best key | 3.6 | 10.3 | 20.4 | 37.6 | 0.83 |
| S3 number of raw-flag cells | 2 | 7 | 17 | 22 | 0.87 |

## 4. Walk-forward on the choice (top 6 cells by the key; trailing 12 months, last 2 label days purged; 2024-01..2026-10; exact engine run of the assembled multipliers)
Candidates: WIN_3m_30, BIN_0.40, CONT_0.25_0.35, TIER_0.30_0.40, TIER_0.30_0.35, BIN_0.35; months chosen: BIN_0.35 10, BIN_0.40 9, REF 9, TIER_0.30_0.40 6.
| window | WF cut vs Q1-A | WF mean vs Q1-A (MDE) | maxDD WF vs Q1-A |
|--|--|--|--|
| PRE | +5.1% | -1.3k (2.2k) | 83.7k vs 88.2k |
| L6M (W29-W39 dropped) | +0.0% | +0.0k (0.0k) | 62.6k vs 62.6k |
| HOLD (W29-W39 dropped) | -2.4% | -0.1k (1.2k) | 125.0k vs 122.0k |
| F9 (W29-W39 dropped) | +0.0% | -0.1k (1.0k) | 62.6k vs 62.6k |
| X' | +0.0% | +0.1k (0.5k) | 80.8k vs 80.8k |
| MID | +7.2% | -0.2k (2.2k) | 55.4k vs 59.7k |

## 5. Placebos for the top 3 cells (100 draws; multipliers permuted within book x session / shuffled-day / AR(1)-matched; rank = share of draws below the real cell)
| cell | kind | rank cut L6M | rank mean L6M | rank cut PRE | rank mean PRE |
|--|--|--|--|--|--|
| BIN_0.40 | ar1 | 0.30 | 0.89 | 0.44 | 0.84 |
| BIN_0.40 | dayshuf | 0.29 | 0.90 | 0.45 | 0.82 |
| BIN_0.40 | perm | 0.29 | 0.81 | 0.47 | 0.82 |
| CONT_0.25_0.35 | ar1 | 0.05 | 0.97 | 0.54 | 0.87 |
| CONT_0.25_0.35 | dayshuf | 0.03 | 0.91 | 0.45 | 0.89 |
| CONT_0.25_0.35 | perm | 0.05 | 0.89 | 0.48 | 0.83 |
| WIN_3m_30 | ar1 | 0.00 | 0.49 | 0.42 | 0.28 |
| WIN_3m_30 | dayshuf | 0.01 | 0.52 | 0.39 | 0.35 |
| WIN_3m_30 | perm | 0.04 | 0.56 | 0.39 | 0.16 |

## 6. ER at the add under Q1-A (closes addendum 2.1: "no feature tells which adds to drop")
| cell | definition | L6M cut (dropped) | PRE cut | HOLD | MID | X' | d mean L6M (MDE) | d mean PRE (MDE) | equal-risk d mean L6M-dr / PRE |
|--|--|--|--|--|--|--|--|--|--|
| ADD_H | add x0.5 if ER at the add < .30 | +0.5% (+0.0%) | +2.5% | +1.7% | +3.5% | +2.7% | -0.1k (0.3k) | -0.3k (0.5k) | -0.6 / -0.0 |
| ADD_C | add cancelled if ER at the add < .30 | +20.7% (+27.9%) | -6.2% | +15.1% | +24.9% | +26.3% | -1.4k (4.3k) | -2.3k (2.2k) | +21.2 / -2.9 |
| ADD_D | add x0.5 if ER fell > 0.1 since the signal | +1.2% (+0.0%) | +2.5% | +2.3% | +3.5% | +1.0% | +0.1k (0.4k) | -0.3k (0.5k) | -0.6 / -0.5 |

## 7. The Q2/Q3 cells as "what it adds to Q1-A" (top 12 by the key; the x1.5 tiers are up-sizes over x1.0)
| cell | L6M cut (dropped) | PRE cut | HOLD | MID | X' | d mean L6M (MDE) | d mean PRE (MDE) | mean ok |
|--|--|--|--|--|--|--|--|--|
| W_3m_30_A | -3.8% (+6.4%) | +3.6% | -9.3% | +9.6% | +0.3% | -3.4k (6.1k) | -2.4k (2.6k) | yes |
| W_5m_30_A | +6.6% (+15.7%) | -4.5% | -22.8% | -30.9% | +4.3% | -4.1k (8.3k) | -1.2k (2.7k) | yes |
| W_3m_14_A | +47.0% (+11.2%) | -6.7% | -25.4% | -39.0% | -18.3% | -1.5k (12.7k) | -2.5k (3.9k) | yes |
| T_0.30_0.60 | +34.0% (-10.5%) | -9.2% | -7.1% | -8.8% | +19.9% | +4.3k (5.0k) | +1.2k (2.0k) | yes |
| W_3m_20_A | +43.0% (+7.5%) | -13.2% | -15.7% | -35.6% | +1.3% | -1.1k (9.1k) | -2.3k (3.8k) | yes |
| T_0.25_0.60 | +31.7% (-14.4%) | -6.1% | -19.4% | -5.1% | +7.8% | +5.5k (8.3k) | +0.5k (2.8k) | yes |
| S_NY | -9.3% (+3.0%) | -14.4% | +6.1% | +10.4% | +19.9% | -0.8k (2.1k) | +2.7k (2.6k) | yes |
| T_0.20_0.60 | +28.5% (-19.8%) | -7.6% | -29.9% | -11.0% | -4.9% | +2.7k (10.5k) | +1.4k (3.2k) | yes |
| CAPB_3 | -23.2% (-22.4%) | -20.8% | -5.8% | +34.3% | -10.6% | +0.8k (4.9k) | +1.2k (2.1k) | yes |
| CAPB_2 | -23.2% (-22.4%) | -20.8% | -5.8% | +34.3% | -10.6% | +0.8k (4.9k) | +1.2k (2.1k) | yes |
| W_5m_14_A | +20.0% (-34.0%) | +0.2% | -22.5% | -19.9% | -18.5% | -1.4k (6.3k) | -0.6k (3.4k) | yes |
| T_0.30_0.45 | +19.7% (-34.4%) | -30.4% | -17.1% | +0.0% | +23.2% | +9.0k (10.3k) | +1.9k (4.1k) | yes |
(Cells that add x1.5 tiers such as T_0.25_0.60, T_0.30_0.60, K_PE, PE_S_asia now raise lots over Q1-A and deepen maxDD; the size-down cells W_*_A are Q1-A with another ER window.)

## 8. Lots distribution and worst-day exposure: Q1-A, the best new cells, T_0.25_0.60 and K_PE (engine run of each cell; positions open at signal seconds; stack risk = lots x stop pts x $20)
| cell | mean lots | max lots | worst net signed lots (day) | worst stack risk $ (day) |
|--|--|--|--|--|
| REF | 2.31 | 7 | 18 (20240401) | 21,600 (20230623) |
| WIN_3m_30 | 2.18 | 7 | 18 (20240401) | 21,600 (20230529) |
| BIN_0.40 | 2.09 | 7 | 18 (20240925) | 21,600 (20240925) |
| CONT_0.25_0.35 | 2.30 | 7 | 18 (20240401) | 21,600 (20230623) |
| TIER_0.30_0.40 | 2.22 | 7 | 18 (20240925) | 21,600 (20240925) |
| TIER_0.30_0.35 | 2.26 | 7 | 18 (20240401) | 21,600 (20230623) |
| BIN_0.35 | 2.20 | 7 | 18 (20240401) | 21,600 (20230623) |
| Q2_K_PE | 2.69 | 11 | 22 (20240401) | 26,400 (20230623) |
| Q2_T_0.25_0.60 | 2.51 | 11 | 25 (20241125) | 31,200 (20231214) |

Mean / max lots per book x session (REF = Q1-A; first four cells of the table above):
| book | sess | n | REF mean | REF max | WIN_3m_30 mean | WIN_3m_30 max | BIN_0.40 mean | BIN_0.40 max | CONT_0.25_0.35 mean | CONT_0.25_0.35 max | TIER_0.30_0.40 mean | TIER_0.30_0.40 max |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| HM | asia | 1802 | 2.35 | 4.00 | 2.22 | 4.00 | 2.12 | 4.00 | 2.36 | 4.00 | 2.26 | 4.00 |
| HM | nyam | 681 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| KB | asia | 2224 | 1.24 | 2.00 | 1.20 | 2.00 | 1.14 | 2.00 | 1.24 | 2.00 | 1.24 | 2.00 |
| KB | london | 1488 | 1.20 | 2.00 | 1.18 | 2.00 | 1.12 | 2.00 | 1.20 | 2.00 | 1.20 | 2.00 |
| KB | nyam | 1160 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| KB | nypm | 976 | 1.18 | 2.00 | 1.17 | 2.00 | 1.13 | 2.00 | 1.18 | 2.00 | 1.19 | 2.00 |
| MV | london | 1541 | 1.43 | 2.00 | 1.31 | 2.00 | 1.26 | 2.00 | 1.43 | 2.00 | 1.43 | 2.00 |
| MV | nyam | 1377 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| PB | asia | 1072 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 | 1.00 |
| PE | asia | 2138 | 4.97 | 7.00 | 4.68 | 7.00 | 4.47 | 7.00 | 4.93 | 7.00 | 4.64 | 7.00 |
| PE | london | 1488 | 4.82 | 7.00 | 4.42 | 7.00 | 4.28 | 7.00 | 4.78 | 7.00 | 4.47 | 7.00 |
| PE | nyam | 884 | 4.57 | 7.00 | 4.32 | 7.00 | 4.19 | 7.00 | 4.55 | 7.00 | 4.32 | 7.00 |
| SM | asia | 690 | 2.85 | 4.00 | 2.60 | 4.00 | 2.46 | 4.00 | 2.86 | 4.00 | 2.69 | 4.00 |
| SM | london | 680 | 2.54 | 4.00 | 2.19 | 4.00 | 2.08 | 4.00 | 2.55 | 4.00 | 2.35 | 4.00 |

## 9. Flags
Raw flags (sec. 2): BIN_0.40, WIN_3m_30. Placebo-clean flags: none. => no ***FLAG*** block is written unless a raw-flag cell is also placebo-clean and survives the null; the user decides.
