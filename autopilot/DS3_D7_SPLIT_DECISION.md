# DS3_D7_SPLIT_DECISION - one decision table for the user: shipped 70/30 split vs market entry (and per-book choices) on V13T_LIVE (ZL-3, 2026-11-02)
Base V13T_LIVE: lines off, lock none (per-book locks), resting add cancelled on any exit, market exits 0.80, stops 2.45 worse, targets nominal; label days 2023-04-03..2026-10-30 (43 months). All numbers are engine runs (shipped split = base; 'market' = F = 1 for the five split books, PB already market). Research only; the user decides.
## 1. Who gains, who loses (market entry minus shipped split)
| period | split P&L $k | market P&L $k | market - split $k |
|---|---|---|---|
| 2023 (Apr-Dec) | 92 | 68 | -23 |
| 2024 | 1001 | 1075 | +74 |
| 2025 | 1059 | 1195 | +136 |
| 2026 (Jan-Oct) | 1330 | 1301 | -29 |
| all | 3482 | 3640 | +158 |

Market minus split over the 43 months: **+$158k (+4.5%)**, monthly-block bootstrap 90% CI **[-$115k, +$429k]**, P(>0) 0.83 (month mean +$3.7k, SD $25.6k). Market earns more in 2024 (+$74k) and 2025 (+$136k) and less in 2023 (-$23k) and 2026 (-$29k).
## 2. Per episode drawdown (the three deepest non-overlapping drawdowns of the split's weekly equity)
| episode | split depth $k | market depth $k (same weeks) | market P&L - split P&L over the episode $k |
|---|---|---|---|
| ISO week 202434 -> trough 202437 (14 weeks) | 166 | 151 | +49 |
| ISO week 202505 -> trough 202509 (14 weeks) | 165 | 131 | +108 |
| ISO week 202628 -> trough 202637 (11 weeks) | 151 | 122 | +55 |

In all three of the split's deepest episodes market entry was SHALLOWER (151 vs 166, 131 vs 165, 122 vs 151) and earned more ($+49k, +108k, +55k). The whole-sample maxDD is nevertheless 198k for market entry vs 166k: the market-entry maxDD occurs in a DIFFERENT episode (2024-08..2025-01, section 4 of DS3_D7_SPLIT_V13Y.md: market 200k vs 166k) - the split protects one episode and costs three.
## 3. Per book (market entry for ONE book, others shipped), total P&L and maxDD
| variant | total $k | maxDD $k (weekly, all) | L6M maxDD | PRE maxDD | MID maxDD |
|---|---|---|---|---|---|
| shipped split (all books) | 3482 | 166 | 151 | 166 | 44 |
| market entry, all books | 3640 | 198 | 122 | 198 | 89 |
| market entry for KB only | 3667 | 162 | 142 | 162 | 41 |
| market entry for PE only | 3396 | 200 | 142 | 200 | 86 |
| market entry for SM only | 3472 | 166 | 145 | 166 | 43 |
| market entry for HM only | 3550 | 166 | 142 | 166 | 40 |
| market entry for MV only | 3480 | 163 | 153 | 163 | 46 |
| split only for PE (P7), others market | 3726 | 161 | 131 | 161 | 39 |
| split only for PE + KB, others market | 3540 | 161 | 139 | 161 | 42 |
| market entry at equal risk (lscale 0.98, w20 gap 4%) | 3179 | 192 | 106 | 192 | 77 |
* **PE (P7) is the book that needs the split** (market entry for PE alone: -$86k and maxDD 200k vs 166k). **KB (K7) gains most from market entry** (+$185k and a LOWER maxDD 162k); HM +$69k; SM and MV are neutral (-$9k, -$1k).
* **'Split only for PE, everything else market'** (hindsight): total $3.726M (+$244k, +7.0%), maxDD 161k (vs 166k), L6M 131k (vs 151k), MID 39k (vs 44k): better than the shipped design on every row. It is chosen in-sample.
* Equal risk (lots scaled until the worst-20 sum of ALL equals the shipped one): market entry for all books needs lscale 0.98 and then yields $3.179M (-8.7%) with the same worst-20, maxDD 192k.
## 4. Purged walk-forward of the per-book choice and the multiplicity null (2024-01..2026-10)
Each month, per book (five), market if its trailing-12-month P&L was higher than the split's, applied to the next month. Totals (additive across books, exact in lock none: tie-out 0.0):
| design | total $k | maxDD $k |
|---|---|---|
| shipped (split everywhere) | 3,390 | 166 |
| market everywhere | 3,572 | 198 |
| **walk-forward per-book choice** | **3,616** | **161** |
| split only for PE, others market (hindsight) | 3,632 | 161 |
The walk-forward chooses market 68% of the time (KB 100%, HM 79%, MV 62%, SM 59%, PE 41%). Against 500 random choice sets with the same market share (total mean $3,516k, maxDD mean 186k): total rank 0.06, maxDD rank 0.16. Multiplicity (sign-flip null on the 43 monthly differences of each book, 20,000 draws, max over the five books): the best book (KB, +$185k) has P(max >= observed) = 0.067 (95th percentile of the null maximum $202k); the worst (PE, -$86k) has P(min <= observed) = 0.29. So the KB gain is borderline after best-of-five selection and the PE protection is not statistically distinguishable from noise; the walk-forward is above random choice at the 6% / 16% level.
## 5. What it would cost / gain to switch (expected values, not guarantees)
* Market entry everywhere: expected +$4.5k per month (+$158k over 43 months, CI spans zero), but maxDD +19% (198k vs 166k) in a single 2024-25 episode and PRE/MID drawdowns much worse; at equal risk it is -8.7%.
* Split only for PE (others market): expected +$244k in-sample; walk-forward per-book choice +$226k over 2024-01..2026-10 (rank 0.06 vs random) with maxDD 161k vs 166k. The cleanest, least risky change on this evidence, but it rests on one book's protection (PE) that the sign-flip null cannot separate from noise.
* Execution risk (DS3_D7_SPLIT_V13Y.md s8-9): friction on the add costs the split mean (-2.8k/wk per 1 tick + 3 s); market entry has no add to slip.
Decision aid: if the user wants to minimise drawdown in the one episode that matters (2024-08..2025-01) keep the split for PE; K7 (and H7) are candidates for market entry. Nothing here is tested on a held-out period.
