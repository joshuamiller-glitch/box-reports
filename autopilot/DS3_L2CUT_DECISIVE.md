# DS3_L2CUT_DECISIVE - frozen-definition decisive test of A1's 39 as-is-frame RISK-KEEPs: the L2SL loss cuts, the UF-PROFIT trails and target chooser, and the live loss cut THL L6_a30_r3_w10 (A5, 2026-11-01T07:02Z). SHADOW / NEEDS only, no PASS

Prereg `l2vast/ds3/prereg/L2CUT_prereg.md` sha256 `8b6d1ee468b145d79f2becb32924b8f3301b61024838804e8cc0787287d09ef3` (cells file `out/l2cut/cells_frozen.csv` sha256 `50d56f2570433736fcbfea75736e4ceebda8ed8b11ed63b57eb5e4ee84f35792`) + ADDENDUM 1 sha256 `de3b9b700612a61c49279c0eaf12d0460dd8dfb600af67350d4d59b821418629` + ADDENDUM 2 sha256 `645fb0ee7f409b3b4f738c498ddc826b8555ca756603df9c8f04c5bdd5b444e1`, all in DECISIONS.md (the prereg and ADDENDUM 1 before any statistic; ADDENDUM 2 after the headline cell's PL-M and 350 PL-T draws had been seen, as it discloses). dead_lookup first (`out/l2cut/dead_lookup_before.csv`), append_cells after (program L2CUT; DEAD_CELLS never rebuilt). Code `l2vast/ds3/code/l2cut/`, results `l2vast/ds3/out/l2cut/`. Masks capped 20260206; no post-cap file opened (stack*_daily.npz in uf/loss1 and the 953-day adduw grid not touched). 3 workers, OMP/MKL=1. **Integrity:** PRE and X' were A1's selection windows and A1 already looked at L3M/L6M/HOLD, so this is a CONSISTENCY test on the same data, not a holdout; the statistics were produced once from the frozen spec.

## Verdict (first)

**No cell is a decisive drawdown hedge: 0 of 27 tested cells pass G1-G8 (R1, R2 are reference cells, not candidates) (RISK-KEEP decisive = NO for all). 13 of the 15 primary cells meet the user definition (G1+G2: L6M maxDD cut >= 20% with the mean inside MDE, and PRE and X' agree) in the exact as-is frame, which reproduces A1 to the dollar; none passes the leave-episode-out (all five removed) or the bootstrap in PRE and X', and no L2SL cut beats every placebo in L6M, PRE and X' together.** Shadow / NEEDS only; every failed gate is named per cell in section 9 and on page 1.

Five findings carry the verdict.
1. **For the strongest cells the -45 pt arm does most of the work, and the L2 condition beats a plain cut only in the one L6M week.** The headline cell H fires on 98% of the engine-taken trades that reach -45 pts (5157 of 5283; S5 90%): it is a -45 pt stop tightening on 60-pt-stop trades. Against random trades cut at the plain arm crossing (PL-M) H ranks L6M 100% / PRE 69% / X' 1%, and against random trades cut at the same time-since-arm as the real fires (PL-A, ADDENDUM 2) 100% / 62% / 30%; only the nulls that cut LATER and deeper than the arm (PL-T absolute time-in-trade 100/98/100%, PL-S random row 100/94/100%) are beaten, which only says that cutting at -45 beats cutting deeper. The arm-only reference R2 (cut at -45, no L2 condition) gives X' maxDD +48% and ALL +48% against H's +41%; in X' a random -45 cut does better than H. S1-S3 and S5 show the same pattern (section 3).
2. **The gain is a lock-engine effect, not a trade P&L effect.** The cut changes the trade P&L by -0.37 pts per fired trade (first-order -0.2k/wk, forfeited targets cost as much as the losses saved), but the exact engine gain is 4.1k/wk: the engine admits 1603 extra trades (12759 vs 11347 kept, 191 dropped). With the 12R combined week lock (D6 as coded) the same cut gives different numbers (section 6). Holding the same per-trade pts change but NOT moving the exit time gives mean 0.4k/wk instead of 4.1k (PRE cut +29%, X' +22%): the earlier exit (busy filter, day lock, re-entries) carries the mean gain, so the benefit depends on how the live system accounts the cut exit in its R locks and on a position being free for the next signal.
3. **The L6M drawdown cut is one week.** The as-is L6M maxDD is the single week 2026-01-19..23 (base -88.0k, rule -23.6k for H); with that week removed H still cuts 25% (30.8k to 23.2k) but the 5-episode leave-out in ALL turns the cut to -16%; the bootstrap CI of the L6M maxDD change is [-101.9, -0.5]k, PRE [-161.9, 37.4], X' [-299.2, 25.6] (PRE and X' include zero).
4. **Execution and the stop-cost basis move the answer.** H keeps its L6M/PRE/X' cuts at +1 s and +3 s, but the benefit shrinks when the cut is priced like a join stop (cost 2.45 instead of the measured 0.995: ALL mean 0.1k/wk, PRE cut +19%) and when the baseline stops are priced at 1.28 (PRE cut +27%, ALL mean 1.9k/wk). In the composite frame H deepens L6M by 40% (A1: no composite keep). Every L2 cell needs book features D6 does not compute (section 8); D6 can run only the price-only cells (R1, R2, the THL L6 family).

5. **The UF-PROFIT trails and target chooser are exposure cuts, not hedges.** T1-T5 and C1-C2 meet the user definition and T1-T5 pass G3 against the only null defined for them (stratum-matched random reassignment of the same deltas, rank 98-100%; a weak null: it scatters the rule's profit-giving exits over random trades), but all fail G4 and G5, their ALL mean change is -4.9 to 0.9k/wk (T1 -4.5k vs MDE 6.1k), and none is D6-feasible (section 8). C1 and C2 fail G3 in X' (R rank 68% and 56%).

**Your live loss cut.** THL L6_a30_r3_w10 is a PRICE-PATH rule (adverse >= 30 pts, 3 of 3 path conditions: secs_ext, recov, eff120; window 10 s), not an L2 rule; D6 already runs it as coded (loss H6 line, HM only). HM scope (the live line): L6M maxDD +15%, PRE +16%, X' -10%, ALL mean 1.0k/wk (MDE 1.6k): not a drawdown keep (G1 fails). POOL6 (A1's scope): L6M -25%, PRE -7%, X' +26%, mean -0.9k/wk, reproducing A1. Its one-step neighbours do not rescue it (section 1b). The '-30 / 5 s / 30x' rule is not a verbatim ledger cell; U1-U4 (A=30, 5 s, pulled multiple 20/100, newext 0/1) are the nearest: U1 (20x, no new-extreme condition) meets the user definition (L6M +31%, PRE +33%, X' +36%) but fires on 98% of the trades that reach -30, has ALL mean -2.6k/wk and is beaten by random -30 cuts (PL-M rank L6M/PRE/X' 22/3/0%); U2-U4 fail G1/G2.

## Page 1 - the table (as-is frame, exact lock engine at live lots, vs the same frame without the rule; maxDD $k before>after (cut) [95% stationary-bootstrap CI of the change, block 4 weeks, 4,000 resamples]; worst-20 weeks (PRE, X', ALL) or worst-5 (L3M, L6M, HOLD) $k before>after [CI of the change]; mean change $k/wk (MDE = 2.8 x SE of the paired weekly delta) [CI]; equal-risk mean change at the engine lot scale c where the rule's ALL worst-20 equals the baseline's; matched-placebo rank = share of 1,000 engine-exact draws with a smaller maxDD cut than the real (M matched trades at the plain arm cut, A random exit time since the arm crossing, T random exit time-in-trade, S same trades random row, R stratum-matched reassignment); recent first)

| cell | window | as-is maxDD before>after (cut) [CI of change] | worst-20 / worst-5 [CI] | mean change (MDE) [CI] | equal-risk mean (MDE) | matched placebo rank | LOEO | live-feasible in D6 (Y/N + gap) | RISK-KEEP |
|---|---|---|---|---|---|---|---|---|---|
| S1 L2SL A45 z10>=2 ne0 ICE | L3M | 88.0>34.0 (+61%) [-94.1, 14.2] | -185>-109 (w5) [-19.9, 163.7] | 5.2 (20.9) [-8.0, 17.8] | 6.5 (21.5) c=1.07 | M 99% / A 100% / T 100% / S 100% |  |  |  |
|  | L6M | 88.0>34.0 (+61%) [-83.8, 14.2] | -185>-113 (w5) [-17.3, 182.4] | 1.4 (14.0) [-6.6, 10.2] | 3.0 (14.3) c=1.07 | M 99% / A 100% / T 100% / S 100% |  |  |  |
|  | HOLD | 144.2>142.7 (+1%) [-67.6, 15.3] | -263>-213 (w5) [-28.6, 160.9] | 1.5 (12.3) [-6.3, 9.4] | 3.1 (12.7) c=1.07 | M 29% / A 51% / T 62% / S 72% |  |  |  |
|  | PRE | 162.0>105.6 (+35%) [-134.6, 58.4] | -811>-809 (w20) [-189.5, 207.8] | 1.9 (6.4) [-2.9, 6.8] | 3.4 (6.7) c=1.07 | M 88% / A 91% / T 93% / S 65% |  |  |  |
|  | X' | 316.5>218.0 (+31%) [-245.6, 32.0] | -572>-560 (w20) [-150.1, 164.9] | 6.2 (8.6) [1.4, 11.4] | 6.4 (9.1) c=1.07 | M 39% / A 77% / T 86% / S 100% |  |  |  |
|  | ALL | 316.5>218.0 (+31%) [-205.8, 43.6] | -1161>-1084 (w20) [-125.0, 298.2] | 3.1 (4.9) [-0.2, 6.7] | 4.3 (5.1) c=1.07 | M 39% / A 77% / T 86% / S 100% | 4/5 single removals; all-five NO (-21%); L6M worst wk removed -11% | N: pulled_sup10 z-score vs 15-min ET bucket (prior-month log-mean/sd table), icebergAgainst (best-level traded >=10x displayed, 10 s) | user-def YES / decisive NO: G3 placebo, G4 LOEO, G5 CI |
| S2 L2SL A45 z10>=2 ne0 ICESWP | L3M | 88.0>34.0 (+61%) [-95.6, 14.2] | -185>-110 (w5) [-19.6, 164.9] | 6.3 (20.8) [-7.6, 19.3] | 7.4 (21.3) c=1.06 | M 100% / A 99% (n=500) |  |  |  |
|  | L6M | 88.0>34.0 (+61%) [-84.1, 14.2] | -185>-113 (w5) [-16.9, 180.5] | 1.8 (14.0) [-6.5, 11.1] | 3.2 (14.2) c=1.06 | M 100% / A 100% (n=500) |  |  |  |
|  | HOLD | 144.2>154.0 (-7%) [-60.2, 24.0] | -263>-223 (w5) [-38.3, 155.5] | 1.4 (12.3) [-6.6, 9.7] | 2.8 (12.6) c=1.06 | M 9% / A 26% (n=500) |  |  |  |
|  | PRE | 162.0>104.0 (+36%) [-131.3, 56.3] | -811>-811 (w20) [-187.0, 201.3] | 2.2 (6.3) [-2.4, 7.0] | 3.4 (6.5) c=1.06 | M 88% / A 92% (n=500) |  |  |  |
|  | X' | 316.5>214.8 (+32%) [-248.6, 29.5] | -572>-563 (w20) [-153.7, 162.6] | 6.3 (8.6) [1.5, 11.3] | 6.4 (9.0) c=1.06 | M 42% / A 80% (n=500) |  |  |  |
|  | ALL | 316.5>214.8 (+32%) [-206.8, 42.0] | -1161>-1097 (w20) [-136.4, 282.8] | 3.3 (4.8) [-0.1, 6.9] | 4.2 (5.0) c=1.06 | M 42% / A 80% (n=500) | 3/5 single removals; all-five NO (-19%); L6M worst wk removed -11% | N: pulled_sup10 z-score vs 15-min bucket, icebergAgainst AND sweepAgainst10>=1 | user-def YES / decisive NO: G3 placebo, G4 LOEO, G5 CI |
| S3 L2SL A45 z10>=2 ne0 K2 | L3M | 88.0>34.0 (+61%) [-96.2, 14.2] | -185>-109 (w5) [-19.6, 166.6] | 6.2 (20.9) [-7.6, 19.2] | 7.4 (21.4) c=1.07 | M 99% / A 100% (n=500) |  |  |  |
|  | L6M | 88.0>34.0 (+61%) [-84.7, 14.2] | -185>-113 (w5) [-16.6, 182.2] | 1.7 (14.0) [-6.4, 10.8] | 3.3 (14.2) c=1.07 | M 99% / A 100% (n=500) |  |  |  |
|  | HOLD | 144.2>146.9 (-2%) [-64.8, 17.0] | -263>-215 (w5) [-31.5, 159.1] | 1.6 (12.3) [-6.4, 9.9] | 3.1 (12.6) c=1.07 | M 18% / A 36% (n=500) |  |  |  |
|  | PRE | 162.0>104.0 (+36%) [-130.2, 56.4] | -811>-819 (w20) [-200.9, 196.9] | 2.1 (6.4) [-2.5, 7.0] | 3.5 (6.6) c=1.07 | M 85% / A 94% (n=500) |  |  |  |
|  | X' | 316.5>214.2 (+32%) [-241.3, 35.8] | -572>-563 (w20) [-152.6, 162.7] | 5.9 (8.2) [1.1, 11.0] | 6.1 (8.8) c=1.07 | M 43% / A 84% (n=500) |  |  |  |
|  | ALL | 316.5>214.2 (+32%) [-205.4, 42.3] | -1161>-1089 (w20) [-125.5, 289.2] | 3.2 (4.8) [-0.2, 6.8] | 4.2 (5.0) c=1.07 | M 43% / A 84% (n=500) | 3/5 single removals; all-five NO (-19%); L6M worst wk removed -11% | N: pulled_sup10 z-score vs 15-min bucket, K2 = 2 of {icebergAgainst, sweepAgainst10>=1, ownDepth10Rel<=0.5, imb10<=-0.3} (ice, sweep, ownDepth10Rel missing; imb10 present) | user-def YES / decisive NO: G3 placebo, G4 LOEO, G5 CI |
| S4 L2SL A30 z5>=3 none | L3M | 88.0>64.8 (+26%) [-46.5, 6.1] | -185>-158 (w5) [-7.5, 79.5] | 0.9 (10.6) [-5.1, 6.8] | 1.1 (10.5) c=1.01 | M 59% / A 79% / T 84% / S 3% |  |  |  |
|  | L6M | 88.0>64.8 (+26%) [-41.6, 10.6] | -185>-162 (w5) [-16.6, 66.7] | -2.4 (6.9) [-6.8, 2.2] | -2.2 (6.9) c=1.01 | M 60% / A 79% / T 84% / S 3% |  |  |  |
|  | HOLD | 144.2>197.8 (-37%) [-24.7, 104.9] | -263>-296 (w5) [-95.8, 68.1] | -4.1 (6.9) [-9.3, 0.9] | -3.9 (6.9) c=1.01 | M 0% / A 0% / T 0% / S 1% |  |  |  |
|  | PRE | 162.0>113.9 (+30%) [-112.3, 60.7] | -811>-819 (w20) [-165.1, 149.9] | -0.5 (5.1) [-4.5, 3.8] | -0.2 (5.1) c=1.01 | M 86% / A 95% / T 98% / S 15% |  |  |  |
|  | X' | 316.5>252.1 (+20%) [-194.7, 27.1] | -572>-550 (w20) [-82.0, 132.5] | 4.1 (5.3) [0.7, 7.6] | 4.1 (5.3) c=1.01 | M 60% / A 95% / T 92% / S 5% |  |  |  |
|  | ALL | 316.5>252.1 (+20%) [-135.1, 85.2] | -1161>-1146 (w20) [-131.5, 170.8] | 0.1 (3.4) [-2.8, 3.0] | 0.3 (3.4) c=1.01 | M 60% / A 95% / T 92% / S 5% | 2/5 single removals; all-five NO (-31%); L6M worst wk removed -10% | N: pulled_sup5 (5-s cancel size) z-score vs 15-min bucket; A=30 pct<=-0.5 | user-def YES / decisive NO: G3 placebo, G4 LOEO, G5 CI, G6 execution |
| S5 L2SL A45 mult100@30 ne1 ICE | L3M | 88.0>26.3 (+70%) [-102.9, 24.9] | -185>-93 (w5) [-10.9, 198.3] | 8.9 (25.6) [-8.7, 27.0] | 12.9 (28.3) c=1.19 | M 100% / A 100% / T 100% / S 100% |  |  |  |
|  | L6M | 88.0>26.3 (+70%) [-96.4, 0.9] | -185>-93 (w5) [4.0, 207.0] | 3.4 (16.8) [-6.8, 15.7] | 8.1 (17.9) c=1.19 | M 100% / A 100% / T 100% / S 100% |  |  |  |
|  | HOLD | 144.2>141.1 (+2%) [-76.0, 12.2] | -263>-194 (w5) [-12.8, 185.1] | 3.3 (14.7) [-6.3, 14.6] | 8.1 (16.4) c=1.19 | M 8% / A 22% / T 59% / S 24% |  |  |  |
|  | PRE | 162.0>99.2 (+39%) [-167.9, 32.4] | -811>-711 (w20) [-93.0, 316.8] | 3.3 (7.1) [-1.8, 8.5] | 7.5 (7.8) c=1.19 | M 74% / A 74% / T 93% / S 81% |  |  |  |
|  | X' | 316.5>161.3 (+49%) [-335.7, 7.7] | -572>-478 (w20) [-105.4, 271.3] | 7.7 (9.1) [3.3, 11.8] | 8.5 (10.7) c=1.19 | M 43% / A 86% / T 100% / S 100% |  |  |  |
|  | ALL | 316.5>161.3 (+49%) [-257.3, 12.8] | -1161>-975 (w20) [-15.9, 414.2] | 4.6 (5.4) [0.8, 8.7] | 8.0 (6.1) c=1.19 | M 43% / A 86% / T 100% / S 100% | 5/5 single removals; all-five NO (-14%); L6M worst wk removed +15% | N: pulled_sup30 >= 100 x medOwnLevel, newAdvExt30, icebergAgainst | user-def YES / decisive NO: G3 placebo, G4 LOEO, G5 CI |
| H L2SL A45 mult20@30 ne1 ICE (headline) | L3M | 88.0>24.5 (+72%) [-106.9, 20.0] | -185>-85 (w5) [-4.1, 209.9] | 10.6 (25.8) [-7.5, 29.4] | 13.7 (27.6) c=1.14 | M 100% / A 100% / T 100% / S 100% |  |  |  |
|  | L6M | 88.0>23.6 (+73%) [-101.9, -0.5] | -185>-85 (w5) [10.0, 216.0] | 4.6 (16.6) [-5.8, 17.3] | 8.2 (17.4) c=1.14 | M 100% / A 100% / T 100% / S 100% |  |  |  |
|  | HOLD | 144.2>125.1 (+13%) [-84.6, 1.8] | -263>-180 (w5) [2.6, 199.6] | 4.9 (14.6) [-5.2, 16.5] | 8.7 (15.7) c=1.14 | M 83% / A 86% / T 100% / S 100% |  |  |  |
|  | PRE | 162.0>101.0 (+38%) [-161.9, 37.4] | -811>-733 (w20) [-109.4, 279.2] | 2.6 (7.5) [-3.1, 8.6] | 5.5 (7.9) c=1.14 | M 69% / A 62% / T 98% / S 94% |  |  |  |
|  | X' | 316.5>185.2 (+41%) [-299.2, 25.6] | -572>-502 (w20) [-137.4, 252.5] | 6.0 (9.7) [1.3, 10.2] | 6.4 (10.9) c=1.14 | M 1% / A 30% / T 100% / S 100% |  |  |  |
|  | ALL | 316.5>185.2 (+41%) [-242.5, 19.4] | -1161>-1019 (w20) [-65.3, 385.7] | 4.1 (5.7) [0.1, 8.3] | 6.5 (6.1) c=1.14 | M 1% / A 30% / T 100% / S 100% | 5/5 single removals; all-five NO (-16%); L6M worst wk removed +25% | N: pulled_sup30 >= 20 x medOwnLevel, newAdvExt30 (new MAE extreme in 30 s), icebergAgainst | user-def YES / decisive NO: G3 placebo, G4 LOEO, G5 CI, G8 family-wise p |
| T1 UFP1 F3 icege10 ext10 trail20 | L3M | 88.0>39.7 (+55%) [-86.3, 20.6] | -185>-111 (w5) [-17.9, 147.9] | -4.4 (21.2) [-14.2, 5.9] | -3.0 (21.1) c=1.18 | R 100% |  |  |  |
|  | L6M | 88.0>39.7 (+55%) [-77.0, 21.0] | -185>-133 (w5) [-35.5, 150.8] | -7.3 (12.9) [-14.4, 0.5] | -4.7 (12.7) c=1.18 | R 100% |  |  |  |
|  | HOLD | 144.2>136.3 (+5%) [-59.4, 34.6] | -263>-227 (w5) [-42.4, 126.8] | -7.6 (11.7) [-13.8, -1.3] | -5.1 (11.7) c=1.18 | R 66% |  |  |  |
|  | PRE | 162.0>101.7 (+37%) [-141.3, 80.1] | -811>-796 (w20) [-205.0, 236.0] | -8.0 (8.9) [-13.7, -1.6] | -6.1 (9.2) c=1.18 | R 100% |  |  |  |
|  | X' | 316.5>110.6 (+65%) [-378.4, 26.5] | -572>-420 (w20) [-35.7, 330.0] | 4.0 (10.8) [-3.7, 11.9] | 4.2 (11.6) c=1.18 | R 100% |  |  |  |
|  | ALL | 316.5>136.3 (+57%) [-241.6, 61.8] | -1161>-985 (w20) [1.6, 369.5] | -4.5 (6.1) [-9.0, 0.3] | -2.9 (6.3) c=1.18 | R 100% | 5/5 single removals; all-five NO (-17%); L6M worst wk removed -1% | N: icebergAhead10>=10 (iceberg against at the NQ extreme) + ext (<=10 s since MFE) | user-def YES / decisive NO: G4 LOEO, G5 CI, G8 family-wise p |
| T2 UFP1 F3 icege10 ext30 trail20 | L3M | 88.0>39.7 (+55%) [-86.3, 27.2] | -185>-116 (w5) [-26.9, 147.0] | -4.9 (21.5) [-14.5, 5.7] | -3.6 (21.6) c=1.18 | R 100% (n=500) |  |  |  |
|  | L6M | 88.0>39.7 (+55%) [-77.0, 26.1] | -185>-139 (w5) [-45.6, 144.9] | -7.5 (13.0) [-14.6, 0.1] | -5.0 (12.9) c=1.18 | R 100% (n=500) |  |  |  |
|  | HOLD | 144.2>139.3 (+3%) [-56.6, 39.9] | -263>-233 (w5) [-52.3, 124.3] | -7.9 (11.7) [-14.1, -1.7] | -5.4 (11.8) c=1.18 | R 61% (n=500) |  |  |  |
|  | PRE | 162.0>101.7 (+37%) [-141.3, 77.3] | -811>-790 (w20) [-197.8, 241.7] | -8.0 (9.0) [-13.7, -1.6] | -6.1 (9.2) c=1.18 | R 100% (n=500) |  |  |  |
|  | X' | 316.5>110.6 (+65%) [-376.2, 34.4] | -572>-420 (w20) [-36.4, 329.3] | 3.7 (11.0) [-4.0, 11.6] | 3.7 (11.8) c=1.18 | R 100% (n=500) |  |  |  |
|  | ALL | 316.5>139.3 (+56%) [-240.5, 65.9] | -1161>-985 (w20) [2.7, 369.7] | -4.6 (6.2) [-9.2, 0.1] | -3.1 (6.4) c=1.18 | R 100% (n=500) | 5/5 single removals; all-five NO (-17%); L6M worst wk removed -21% | N: icebergAhead10>=10 + ext30 | user-def YES / decisive NO: G4 LOEO, G5 CI, G8 family-wise p |
| T3 UFP1 F5 d5q20 acc dl30 trail20 | L3M | 88.0>40.6 (+54%) [-92.3, 38.8] | -185>-114 (w5) [-19.6, 170.5] | -4.6 (22.4) [-14.9, 6.1] | -3.2 (22.1) c=1.19 | R 100% |  |  |  |
|  | L6M | 88.0>40.6 (+54%) [-81.7, 32.7] | -185>-122 (w5) [-25.5, 179.4] | -7.5 (13.0) [-15.4, 0.8] | -4.8 (12.7) c=1.19 | R 100% |  |  |  |
|  | HOLD | 144.2>148.7 (-3%) [-56.7, 51.1] | -263>-221 (w5) [-51.6, 145.8] | -8.3 (11.7) [-14.7, -1.7] | -5.7 (11.7) c=1.19 | R 44% |  |  |  |
|  | PRE | 162.0>104.3 (+36%) [-142.8, 87.3] | -811>-793 (w20) [-254.1, 265.2] | -8.5 (9.1) [-14.9, -1.6] | -6.5 (9.3) c=1.19 | R 100% |  |  |  |
|  | X' | 316.5>99.3 (+69%) [-381.2, 36.2] | -572>-440 (w20) [-52.1, 310.3] | 3.7 (11.0) [-3.9, 11.5] | 3.8 (11.9) c=1.19 | R 100% |  |  |  |
|  | ALL | 316.5>148.7 (+53%) [-248.3, 73.5] | -1161>-974 (w20) [-36.8, 410.3] | -4.9 (6.2) [-9.8, 0.0] | -3.4 (6.4) c=1.19 | R 100% | 4/5 single removals; all-five NO (-20%); L6M worst wk removed -32% | N: 60-s change of imb5 (d_imb5_60<=q20) + delta30/delta_acc (D6 has imb5, delta60 only) | user-def YES / decisive NO: G4 LOEO, G5 CI, G8 family-wise p |
| T4 UFP1 F1 Wc80 Tb I1 trail20 | L3M | 88.0>46.2 (+48%) [-77.4, 30.5] | -185>-149 (w5) [-44.5, 118.3] | -3.6 (15.7) [-9.5, 3.4] | -2.6 (15.3) c=1.11 | R 99% |  |  |  |
|  | L6M | 88.0>46.2 (+48%) [-63.1, 23.2] | -185>-156 (w5) [-40.1, 125.9] | -4.2 (10.0) [-9.6, 1.2] | -2.3 (9.9) c=1.11 | R 99% |  |  |  |
|  | HOLD | 144.2>131.8 (+9%) [-59.9, 23.9] | -263>-246 (w5) [-54.0, 103.1] | -4.2 (9.6) [-8.9, 0.6] | -2.2 (9.6) c=1.11 | R 64% |  |  |  |
|  | PRE | 162.0>109.8 (+32%) [-147.0, 75.2] | -811>-810 (w20) [-249.0, 240.7] | -4.8 (8.2) [-10.4, 1.3] | -3.3 (8.4) c=1.11 | R 100% |  |  |  |
|  | X' | 316.5>119.5 (+62%) [-324.7, 39.8] | -572>-444 (w20) [-31.3, 278.9] | 3.5 (8.5) [-2.1, 9.2] | 3.5 (8.9) c=1.11 | R 100% |  |  |  |
|  | ALL | 316.5>131.8 (+58%) [-232.4, 56.7] | -1161>-1045 (w20) [-80.8, 318.2] | -2.3 (5.3) [-6.2, 1.5] | -1.1 (5.4) c=1.11 | R 100% | 5/5 single removals; all-five NO (-26%); L6M worst wk removed -31% | N: wall ahead (cum_ahead10_rel>=q80), tape turn (delta_acc<=q20 & delta30<0), intensity z | user-def YES / decisive NO: G4 LOEO, G5 CI, G8 family-wise p |
| T5 UFP1 F1 Wc80 Tb I1 trail40 | L3M | 88.0>54.0 (+39%) [-54.3, 17.2] | -185>-149 (w5) [-25.1, 90.8] | -5.6 (13.2) [-10.2, -1.2] | -5.2 (12.4) c=1.07 | R 98% |  |  |  |
|  | L6M | 88.0>54.0 (+39%) [-39.5, 18.8] | -185>-158 (w5) [-30.8, 106.9] | -5.4 (8.2) [-8.7, -1.8] | -4.1 (8.2) c=1.07 | R 98% |  |  |  |
|  | HOLD | 144.2>159.9 (-11%) [-36.4, 45.5] | -263>-264 (w5) [-90.3, 84.8] | -5.8 (8.1) [-8.8, -2.7] | -4.6 (8.2) c=1.07 | R 28% |  |  |  |
|  | PRE | 162.0>106.3 (+34%) [-154.3, 54.7] | -811>-765 (w20) [-148.0, 269.7] | -3.9 (6.9) [-9.2, 2.2] | -2.8 (6.9) c=1.07 | R 100% |  |  |  |
|  | X' | 316.5>211.6 (+33%) [-246.1, 127.9] | -572>-530 (w20) [-114.8, 194.5] | 1.3 (8.1) [-4.7, 7.3] | 1.1 (8.4) c=1.07 | R 99% |  |  |  |
|  | ALL | 316.5>211.6 (+33%) [-181.9, 102.0] | -1161>-1081 (w20) [-93.2, 279.1] | -2.8 (4.6) [-6.4, 0.9] | -2.1 (4.6) c=1.07 | R 100% | 4/5 single removals; all-five NO (-22%); L6M worst wk removed +8% | N: as T4 | user-def YES / decisive NO: G4 LOEO, G5 CI |
| C1 UFP5 dlt_a m0.5 | L3M | 88.0>47.8 (+46%) [-78.1, 9.1] | -185>-117 (w5) [9.0, 113.3] | -2.7 (19.1) [-13.1, 6.4] | -1.4 (18.8) c=1.14 | R 99% |  |  |  |
|  | L6M | 88.0>47.8 (+46%) [-65.2, 6.3] | -185>-117 (w5) [18.4, 127.6] | -5.0 (11.0) [-11.2, 1.1] | -2.7 (11.1) c=1.14 | R 99% |  |  |  |
|  | HOLD | 144.2>122.0 (+15%) [-62.5, 5.8] | -263>-206 (w5) [18.2, 129.7] | -3.6 (9.8) [-9.7, 2.0] | -1.1 (9.8) c=1.14 | R 71% |  |  |  |
|  | PRE | 162.0>93.9 (+42%) [-140.1, 43.1] | -811>-770 (w20) [-123.8, 208.6] | -2.1 (6.7) [-7.4, 2.9] | 0.2 (7.1) c=1.14 | R 100% |  |  |  |
|  | X' | 316.5>197.5 (+38%) [-224.2, 36.3] | -572>-488 (w20) [-30.1, 202.6] | 2.8 (6.8) [-1.5, 7.5] | 2.7 (7.2) c=1.14 | R 68% |  |  |  |
|  | ALL | 316.5>197.5 (+38%) [-186.9, 45.5] | -1161>-1021 (w20) [-3.4, 296.3] | -1.0 (4.5) [-4.4, 2.3] | 0.7 (4.7) c=1.14 | R 87% | 5/5 single removals; all-five NO (-8%); L6M worst wk removed -19% | N (action): delta60<=q30 is available but "shorten the target to 0.5x at entry" is not a THP action (vocabulary take|cut|tighten) | user-def YES / decisive NO: G3 placebo, G4 LOEO, G5 CI |
| C2 UFP5 dlt_a m0.67 | L3M | 88.0>53.0 (+40%) [-66.9, 19.3] | -185>-163 (w5) [-31.7, 85.1] | -3.4 (15.3) [-10.2, 2.9] | -2.2 (14.9) c=1.14 | R 97% |  |  |  |
|  | L6M | 88.0>53.0 (+40%) [-46.1, 15.8] | -185>-163 (w5) [-28.8, 90.9] | -2.5 (9.1) [-8.0, 3.5] | 0.1 (9.4) c=1.14 | R 97% |  |  |  |
|  | HOLD | 144.2>132.1 (+8%) [-47.5, 14.0] | -263>-226 (w5) [-17.1, 98.1] | -1.6 (8.3) [-6.4, 3.6] | 1.2 (8.7) c=1.14 | R 52% |  |  |  |
|  | PRE | 162.0>89.6 (+45%) [-138.6, 13.8] | -811>-742 (w20) [-50.7, 189.4] | 1.2 (5.3) [-2.7, 6.0] | 4.0 (5.8) c=1.14 | R 100% |  |  |  |
|  | X' | 316.5>212.2 (+33%) [-211.3, 44.8] | -572>-489 (w20) [-23.7, 203.0] | 2.3 (6.0) [-1.5, 6.1] | 2.1 (6.3) c=1.14 | R 56% |  |  |  |
|  | ALL | 316.5>212.2 (+33%) [-171.2, 32.7] | -1161>-1020 (w20) [28.3, 281.5] | 0.9 (3.7) [-1.7, 3.8] | 2.9 (4.0) c=1.14 | R 68% | 5/5 single removals; all-five NO (-3%); L6M worst wk removed -27% | N (action): as C1, multiple 0.67 | user-def YES / decisive NO: G3 placebo, G4 LOEO, G5 CI |
| L1 THL L6_a30_r3_w10 HM (live line) | L3M | 88.0>74.5 (+15%) [-27.0, 8.6] | -185>-165 (w5) [-10.5, 52.8] | 1.6 (7.1) [-2.0, 5.1] | 2.0 (6.8) c=1.03 | M 51% / A 85% / T 68% |  |  |  |
|  | L6M | 88.0>74.5 (+15%) [-24.5, 8.6] | -185>-178 (w5) [-19.6, 45.4] | 1.6 (4.2) [-0.5, 3.8] | 2.3 (4.2) c=1.03 | M 51% / A 85% / T 68% |  |  |  |
|  | HOLD | 144.2>142.7 (+1%) [-23.5, 8.6] | -263>-253 (w5) [-16.6, 46.3] | 1.6 (3.7) [-0.3, 3.6] | 2.3 (3.7) c=1.03 | M 48% / A 73% / T 74% |  |  |  |
|  | PRE | 162.0>136.5 (+16%) [-46.3, 20.4] | -811>-825 (w20) [-79.6, 47.0] | 1.4 (2.4) [-0.4, 3.5] | 2.0 (2.5) c=1.03 | M 84% / A 95% / T 97% |  |  |  |
|  | X' | 316.5>347.1 (-10%) [-54.3, 78.1] | -572>-578 (w20) [-60.0, 47.7] | -0.2 (2.1) [-2.2, 1.8] | -0.3 (2.1) c=1.03 | M 4% / A 55% / T 48% |  |  |  |
|  | ALL | 316.5>347.1 (-10%) [-61.2, 40.9] | -1161>-1129 (w20) [-13.7, 83.4] | 1.0 (1.6) [-0.2, 2.3] | 1.4 (1.6) c=1.03 | M 4% / A 55% / T 48% | 1/5 single removals; all-five NO (-2%); L6M worst wk removed -18% | Y: price-path only (pct, secs_ext, recov, eff120 as coded: loss H6 line) | user-def no / decisive NO: G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| L1 THL L6_a30_r3_w10 POOL6 | L3M | 88.0>110.0 (-25%) [-73.5, 139.1] | -185>-175 (w5) [-122.3, 124.8] | -3.7 (26.1) [-24.5, 14.4] | -3.3 (26.8) c=1.05 | M 11% / A 42% / T 59% |  |  |  |
|  | L6M | 88.0>110.0 (-25%) [-54.7, 113.3] | -185>-186 (w5) [-111.3, 122.5] | -2.3 (13.9) [-12.9, 7.5] | -1.4 (14.3) c=1.05 | M 9% / A 39% / T 56% |  |  |  |
|  | HOLD | 144.2>142.1 (+1%) [-55.4, 109.2] | -263>-255 (w5) [-120.9, 144.7] | -1.9 (13.0) [-12.6, 7.6] | -1.0 (13.4) c=1.05 | M 20% / A 71% / T 77% |  |  |  |
|  | PRE | 162.0>172.6 (-7%) [-97.2, 161.4] | -811>-862 (w20) [-298.3, 166.0] | -4.6 (8.8) [-13.6, 3.4] | -3.9 (9.0) c=1.05 | M 1% / A 49% / T 59% |  |  |  |
|  | X' | 316.5>235.3 (+26%) [-249.9, 21.8] | -572>-441 (w20) [-25.4, 291.6] | 6.1 (8.8) [2.0, 10.0] | 6.2 (9.0) c=1.05 | M 53% / A 100% / T 100% |  |  |  |
|  | ALL | 316.5>235.3 (+26%) [-170.1, 135.1] | -1161>-1109 (w20) [-180.8, 277.7] | -0.9 (5.9) [-6.4, 4.0] | -0.3 (6.0) c=1.05 | M 54% / A 100% / T 100% | 3/5 single removals; all-five NO (-98%); L6M worst wk removed -257% | Y: price-path only (as coded for HM; other books have no loss line) | user-def no / decisive NO: G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |

Placebo draws completed: 28 of 61 placebo sets at 1,000; total 44500 draws. 'not run' = not reached yet in the queue. Columns for the neighbour / reference cells (L2-L5, U1-U4, R1-R2) are in section 1b.

## 1. Per-episode table: top-10 drawdown episodes of the AS-IS stack (ALL window, weekly cumulative, greedy peak to trough) and what each rule does inside them

Baseline P&L inside the span equals minus the depth (a greedy episode runs peak to trough). Cells show the rule's P&L change inside the span, $k (rule span P&L minus base span P&L); negative = the rule loses more in that episode than the as-is stack. Full per-cell tables: `out/l2cut/episodes_<cid>.csv`.

| # | dates | weeks | depth $k | H | S1 | S5 | S4 | T1 | T4 | C1 | L1HM | L1POOL6 | R2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 20230403 to 20231201 | 35 | 316.5 | +194.0 | +252.2 | +252.5 | +137.2 | +339.0 | +213.3 | +180.0 | -30.6 | +216.6 | +205.5 |
| 2 | 20240819 to 20241011 | 8 | 162.0 | +150.9 | +125.0 | +160.3 | +109.1 | +65.0 | +116.4 | +100.4 | +37.2 | +128.6 | +168.0 |
| 3 | 20250707 to 20250725 | 3 | 144.2 | +19.0 | +1.5 | +3.1 | -53.6 | +7.9 | +12.4 | +22.2 | +1.5 | +2.0 | +14.5 |
| 4 | 20260119 to 20260123 | 1 | 88.0 | +64.4 | +55.0 | +62.0 | +23.3 | +48.4 | +41.9 | +40.3 | +13.5 | +42.7 | +29.0 |
| 5 | 20241118 to 20241122 | 1 | 87.8 | +16.6 | +0.9 | +40.5 | -3.8 | +0.3 | +26.5 | -1.2 | +2.2 | -28.6 | +22.0 |
| 6 | 20250217 to 20250307 | 3 | 64.5 | -23.4 | -35.2 | -30.1 | -49.4 | +27.5 | +33.3 | +9.1 | -15.3 | -108.1 | -35.1 |
| 7 | 20250602 to 20250613 | 2 | 58.5 | -4.6 | -23.8 | -18.6 | -9.6 | -17.4 | -9.2 | +56.7 | +11.6 | -1.0 | +7.0 |
| 8 | 20260105 to 20260109 | 1 | 30.8 | +59.7 | +21.2 | +55.3 | -3.1 | +28.6 | +21.3 | -5.8 | +7.6 | +32.2 | +40.5 |
| 9 | 20251222 to 20251226 | 1 | 27.7 | +4.5 | +1.9 | +1.4 | +0.0 | +8.2 | -12.5 | +13.7 | -8.6 | -23.6 | +7.6 |
| 10 | 20250203 to 20250207 | 1 | 23.5 | -32.4 | -23.0 | -23.8 | +6.1 | -11.5 | +6.0 | +19.9 | -5.7 | +17.7 | -31.4 |
| top-10 total | | | 1003.5 | +448.5 | +375.7 | +502.6 | +156.1 | +495.8 | +449.3 | +435.2 | +13.5 | +278.5 | +427.5 |
| rule maxDD inside the span of #1 / #2 / #4 | | | | 185.2/63.8/23.6 | 218.0/82.0/33.0 | 161.3/60.5/26.0 | 252.1/92.2/64.8 | 110.6/99.6/39.7 | 119.5/94.6/46.2 | 197.5/80.9/47.8 | 347.1/136.5/74.5 | 235.3/91.8/45.3 | 164.6/60.0/59.1 |

Reading. Episode 1 (2023-04-03 to 2023-12-01, 35 weeks, 316.5k) and episode 2 (2024-08-19 to 2024-10-11) carry most of H's gain (+194k and +151k); the L6M maxDD week (episode 4, 2026-01-19..23, 88.0k) is cut to 23.6k (+64k); episodes 6, 7 and 10 get WORSE under H (-23k, -5k, -32k): the cut is not uniformly protective.  Every cell in the table gains in episodes 1, 2 and 4 (the three largest drawdowns and the L6M week), including the arm-only reference R2 and the profit trails T1/T4, so a gain inside the baseline's own worst episodes is what any volume- or exposure-reducing change produces (the baseline's worst weeks are selected for being bad); the placebo of section 3 is the test of whether the L2 rule does better than that.

### 1b. Live-cut neighbours and references (same columns, key windows; full rows in `out/l2cut/analysis.pkl`)

| cell | L6M maxDD cut [CI] | PRE cut [CI] | X' cut [CI] | ALL cut | mean change ALL (MDE) / L6M (MDE) | equal-risk mean ALL (MDE) | placebo rank L6M / PRE / X' | decisive fails |
|---|---|---|---|---|---|---|---|---|
| L1 THL L6_a30_r3_w10 HM (live line) | +15% [-24.5, 8.6] | +16% [-46.3, 20.4] | -10% [-54.3, 78.1] | -10% | 1.0 (1.6) / 1.6 (4.2) | 1.4 (1.6) | M 51% / A 85% / T 68% / M 84% / A 95% / T 97% / M 4% / A 55% / T 48% | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| L1 THL L6_a30_r3_w10 POOL6 | -25% [-54.7, 113.3] | -7% [-97.2, 161.4] | +26% [-249.9, 21.8] | +26% | -0.9 (5.9) / -2.3 (13.9) | -0.3 (6.0) | M 9% / A 39% / T 56% / M 1% / A 49% / T 59% / M 53% / A 100% / T 100% | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| L2 THL L6_a25_r3_w10 HM | +11% [-17.7, 11.3] | +18% [-49.8, 20.3] | -8% [-57.1, 74.0] | -8% | 0.9 (1.5) / 1.3 (3.9) | 1.3 (1.6) | M 23% / A 48% (n=500) / M 87% / A 97% (n=500) / M 12% / A 74% (n=500) | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| L2 THL L6_a25_r3_w10 POOL6 | -23% [-63.2, 121.1] | +8% [-136.5, 114.7] | +21% [-244.8, 45.0] | +21% | -1.0 (6.6) / -3.4 (15.6) | -0.1 (6.8) | M 3% / A 29% (n=500) / M 18% / A 90% (n=500) / M 19% / A 99% (n=500) | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| L3 THL L6_a30_r2_w10 HM | +16% [-30.6, 7.6] | +13% [-57.6, 18.7] | -3% [-80.0, 54.7] | -3% | 0.8 (2.1) / 2.4 (5.6) | 1.9 (2.3) | M 54% / A 47% (n=500) / M 72% / A 73% (n=500) / M 2% / A 3% (n=500) | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| L3 THL L6_a30_r2_w10 POOL6 | -10% [-47.9, 152.0] | -59% [-158.5, 242.7] | +43% [-337.2, 24.0] | +18% | -2.6 (8.9) / -11.7 (18.2) | 0.2 (10.0) | M 10% / A 11% (n=500) / M 0% / A 0% (n=500) / M 43% / A 49% (n=500) | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| L4 THL L6_a30_r3_w30 HM | +20% [-30.9, 10.9] | +7% [-53.1, 14.6] | +2% [-92.5, 25.0] | +2% | 1.7 (1.9) / 2.1 (5.4) | 2.8 (2.1) | M 84% / A 98% (n=500) / M 31% / A 65% (n=500) / M 37% / A 94% (n=500) | G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| L4 THL L6_a30_r3_w30 POOL6 | -26% [-60.2, 145.2] | +10% [-176.1, 88.3] | +41% [-373.6, 21.2] | +41% | 0.4 (7.4) / -7.3 (17.3) | 3.8 (8.2) | M 12% / A 72% (n=500) / M 6% / A 71% (n=500) / M 57% / A 100% (n=500) | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| L5 THL L6_a15_r3_w30 HM | +15% [-26.3, 10.5] | +13% [-57.8, 26.9] | -7% [-97.0, 83.3] | -7% | 0.2 (2.3) / -0.4 (6.5) | 0.8 (2.4) | M 42% / A 57% (n=500) / M 23% / A 78% (n=500) / M 63% / A 99% (n=500) | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| L5 THL L6_a15_r3_w30 POOL6 | -46% [-50.0, 170.4] | -146% [-112.3, 539.8] | +59% [-388.8, 4.6] | -26% | -6.5 (9.4) / -15.7 (19.6) | -6.0 (9.7) | M 12% / A 94% (n=500) / M 0% / A 78% (n=500) / M 88% / A 100% (n=500) | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| U1 L2SL A30 mult20@5 ne0 none | +31% [-46.9, 44.7] | +33% [-181.1, 67.0] | +36% [-307.3, 31.7] | +36% | -2.6 (7.4) / -6.0 (17.3) | 0.1 (8.1) | M 22% / A 85% (n=500) / M 3% / A 39% (n=500) / M 0% / A 66% (n=500) | G3 placebo, G4 LOEO, G5 CI, G8 family-wise p |
| U2 L2SL A30 mult20@5 ne1 none | +26% [-42.8, 49.0] | +6% [-164.4, 95.0] | +33% [-313.2, 18.9] | +33% | -0.4 (6.9) / -3.9 (16.8) | 2.3 (7.6) | M 13% / A 74% (n=500) / M 0% / A 1% (n=500) / M 1% / A 75% (n=500) | G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| U3 L2SL A30 mult100@5 ne0 none | +10% [-28.3, 44.1] | +13% [-122.9, 89.1] | +38% [-261.4, 8.9] | +38% | -0.3 (5.4) / -6.3 (17.2) | 0.7 (5.6) | M 13% / A 41% (n=500) / M 7% / A 56% (n=500) / M 74% / A 100% (n=500) | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| U4 L2SL A30 mult100@5 ne1 none | +18% [-34.5, 26.9] | +16% [-88.0, 56.7] | +5% [-168.7, 78.3] | +5% | -0.4 (4.9) / -4.1 (14.7) | -0.2 (5.0) | M 18% / A 38% (n=500) / M 18% / A 50% (n=500) / M 14% / A 68% (n=500) | G1 user def, G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |
| R1 arm-only A30 (no L2) | +26% [-46.1, 52.2] | +42% [-183.3, 58.1] | +49% [-351.3, 10.0] | +49% | -2.9 (7.6) / -6.7 (17.0) | -0.0 (8.4) | M 0% / A 0% (n=500) / M 100% / A 100% (n=500) / M 0% / A 0% (n=500) | G3 placebo, G4 LOEO, G5 CI, G8 family-wise p |
| R2 arm-only A45 (no L2) | +33% [-59.7, 16.7] | +19% [-163.4, 61.3] | +48% [-311.9, 24.1] | +48% | 3.5 (5.5) / 0.9 (15.5) | 5.3 (5.8) | M 100% / A 99% (n=500) / M 0% / A 0% (n=500) / M 0% / A 0% (n=500) | G2 PRE/X' agree, G3 placebo, G4 LOEO, G5 CI, G6 execution, G8 family-wise p |

## 2. Leave-one-episode-out (top-5 ALL episodes of the as-is stack: peak..trough weeks removed from both series; maxDD $k before>after (cut); survives = cut >= 10%, worst-20 not worse)

| cell | none | ep1 | ep2 | ep3 | ep4 | ep5 | all five | L6M worst week removed (2026-01-19) | other windows' worst episode removed: L3M / HOLD / PRE / X' |
|---|---|---|---|---|---|---|---|---|---|
| S1 L2SL A45 z10>=2 ne0 ICE | 316.5>218.0 (+31%) | 162.0>142.7 (+12%) | 316.5>218.0 (+31%) x | 316.5>218.0 (+31%) | 316.5>218.0 (+31%) | 316.5>218.0 (+31%) | 87.1>105.6 (-21%) x | 30.8>34.0 (-11%) | 30.8>34.0 (-11%) / 88.0>34.0 (+61%) / 87.8>105.6 (-20%) / 12.4>7.2 (+42%) |
| S2 L2SL A45 z10>=2 ne0 ICESWP | 316.5>214.8 (+32%) | 162.0>154.0 (+5%) x | 316.5>214.8 (+32%) x | 316.5>214.8 (+32%) | 316.5>214.8 (+32%) | 316.5>214.8 (+32%) | 87.1>104.0 (-19%) x | 30.8>34.0 (-11%) | 30.8>34.0 (-11%) / 88.0>34.0 (+61%) / 87.8>104.0 (-18%) / 12.4>7.2 (+42%) |
| S3 L2SL A45 z10>=2 ne0 K2 | 316.5>214.2 (+32%) | 162.0>146.9 (+9%) x | 316.5>214.2 (+32%) x | 316.5>214.2 (+32%) | 316.5>214.2 (+32%) | 316.5>214.2 (+32%) | 87.1>104.0 (-19%) x | 30.8>34.0 (-11%) | 30.8>34.0 (-11%) / 88.0>34.0 (+61%) / 87.8>104.0 (-18%) / 12.4>7.2 (+42%) |
| S4 L2SL A30 z5>=3 none | 316.5>252.1 (+20%) | 162.0>197.8 (-22%) x | 316.5>252.1 (+20%) x | 316.5>252.1 (+20%) | 316.5>252.1 (+20%) x | 316.5>252.1 (+20%) | 87.1>113.9 (-31%) x | 30.8>33.8 (-10%) | 30.8>33.8 (-10%) / 88.0>64.8 (+26%) / 87.8>113.9 (-30%) / 12.4>6.9 (+44%) |
| S5 L2SL A45 mult100@30 ne1 ICE | 316.5>161.3 (+49%) | 162.0>141.1 (+13%) | 316.5>161.3 (+49%) | 316.5>161.3 (+49%) | 316.5>161.3 (+49%) | 316.5>161.3 (+49%) | 87.1>99.2 (-14%) x | 30.8>26.3 (+15%) | 30.8>26.3 (+15%) / 88.0>26.3 (+70%) / 87.8>99.2 (-13%) / 12.4>0.0 (+100%) |
| H L2SL A45 mult20@30 ne1 ICE (headline) | 316.5>185.2 (+41%) | 162.0>125.1 (+23%) | 316.5>185.2 (+41%) | 316.5>185.2 (+41%) | 316.5>185.2 (+41%) | 316.5>185.2 (+41%) | 87.1>101.0 (-16%) x | 30.8>23.2 (+25%) | 30.8>24.5 (+20%) / 88.0>23.6 (+73%) / 87.8>101.0 (-15%) / 12.4>5.2 (+58%) |
| T1 UFP1 F3 icege10 ext10 trail20 | 316.5>136.3 (+57%) | 162.0>136.3 (+16%) | 316.5>136.3 (+57%) | 316.5>110.6 (+65%) | 316.5>136.3 (+57%) | 316.5>136.3 (+57%) | 87.1>101.7 (-17%) x | 30.8>31.2 (-1%) | 30.8>31.2 (-1%) / 88.0>39.7 (+55%) / 87.8>101.7 (-16%) / 12.4>35.7 (-189%) |
| T2 UFP1 F3 icege10 ext30 trail20 | 316.5>139.3 (+56%) | 162.0>139.3 (+14%) | 316.5>139.3 (+56%) | 316.5>110.6 (+65%) | 316.5>139.3 (+56%) | 316.5>139.3 (+56%) | 87.1>101.7 (-17%) x | 30.8>37.1 (-21%) | 30.8>37.1 (-21%) / 88.0>39.7 (+55%) / 87.8>101.7 (-16%) / 12.4>35.7 (-189%) |
| T3 UFP1 F5 d5q20 acc dl30 trail20 | 316.5>148.7 (+53%) | 162.0>148.7 (+8%) x | 316.5>148.7 (+53%) | 316.5>104.3 (+67%) | 316.5>148.7 (+53%) | 316.5>148.7 (+53%) | 87.1>104.3 (-20%) x | 30.8>40.6 (-32%) | 30.8>40.6 (-32%) / 88.0>40.6 (+54%) / 87.8>104.3 (-19%) / 12.4>33.9 (-174%) |
| T4 UFP1 F1 Wc80 Tb I1 trail20 | 316.5>131.8 (+58%) | 162.0>131.8 (+19%) | 316.5>131.8 (+58%) | 316.5>119.5 (+62%) | 316.5>131.8 (+58%) | 316.5>131.8 (+58%) | 87.1>109.8 (-26%) x | 30.8>40.1 (-31%) | 30.8>40.1 (-31%) / 88.0>46.2 (+48%) / 87.8>109.8 (-25%) / 12.4>16.5 (-33%) |
| T5 UFP1 F1 Wc80 Tb I1 trail40 | 316.5>211.6 (+33%) | 162.0>159.9 (+1%) x | 316.5>211.6 (+33%) | 316.5>211.6 (+33%) | 316.5>211.6 (+33%) | 316.5>211.6 (+33%) | 87.1>106.3 (-22%) x | 30.8>28.4 (+8%) | 30.8>28.4 (+8%) / 88.0>54.0 (+39%) / 87.8>106.3 (-21%) / 12.4>17.0 (-38%) |
| C1 UFP5 dlt_a m0.5 | 316.5>197.5 (+38%) | 162.0>122.0 (+25%) | 316.5>197.5 (+38%) | 316.5>197.5 (+38%) | 316.5>197.5 (+38%) | 316.5>197.5 (+38%) | 87.1>93.9 (-8%) x | 30.8>36.6 (-19%) | 30.8>36.6 (-19%) / 88.0>47.8 (+46%) / 87.8>93.9 (-7%) / 12.4>20.9 (-69%) |
| C2 UFP5 dlt_a m0.67 | 316.5>212.2 (+33%) | 162.0>132.1 (+18%) | 316.5>212.2 (+33%) | 316.5>212.2 (+33%) | 316.5>212.2 (+33%) | 316.5>212.2 (+33%) | 87.1>89.4 (-3%) x | 30.8>39.0 (-27%) | 30.8>39.0 (-27%) / 88.0>53.0 (+40%) / 87.8>89.4 (-2%) / 12.4>14.9 (-21%) |
| L1 THL L6_a30_r3_w10 HM (live line) | 316.5>347.1 (-10%) x | 162.0>142.7 (+12%) | 316.5>347.1 (-10%) x | 316.5>347.1 (-10%) x | 316.5>347.1 (-10%) x | 316.5>347.1 (-10%) x | 87.1>89.0 (-2%) x | 30.8>36.3 (-18%) | 30.8>36.3 (-18%) / 88.0>74.5 (+15%) / 87.8>89.0 (-1%) / 12.4>11.1 (+10%) |
| L1 THL L6_a30_r3_w10 POOL6 | 316.5>235.3 (+26%) | 162.0>172.6 (-7%) x | 316.5>235.3 (+26%) x | 316.5>235.3 (+26%) | 316.5>235.3 (+26%) | 316.5>235.3 (+26%) | 87.1>172.6 (-98%) x | 30.8>110.0 (-257%) | 30.8>110.0 (-257%) / 88.0>110.0 (-25%) / 87.8>172.6 (-97%) / 12.4>6.3 (+49%) |
| L2 THL L6_a25_r3_w10 HM | 316.5>342.2 (-8%) x | 162.0>141.6 (+13%) | 316.5>342.2 (-8%) x | 316.5>342.2 (-8%) x | 316.5>342.2 (-8%) x | 316.5>342.2 (-8%) x | 87.1>92.2 (-6%) x | 30.8>36.3 (-18%) | 30.8>36.3 (-18%) / 88.0>78.0 (+11%) / 87.8>92.2 (-5%) / 12.4>11.1 (+10%) |
| L2 THL L6_a25_r3_w10 POOL6 | 316.5>248.7 (+21%) | 162.0>148.4 (+8%) x | 316.5>248.7 (+21%) x | 316.5>248.7 (+21%) | 316.5>248.7 (+21%) | 316.5>248.7 (+21%) | 87.1>148.4 (-70%) x | 30.8>108.0 (-251%) | 30.8>108.0 (-251%) / 88.0>108.0 (-23%) / 87.8>148.4 (-69%) / 12.4>5.1 (+58%) |
| L3 THL L6_a30_r2_w10 HM | 316.5>326.5 (-3%) x | 162.0>145.6 (+10%) | 316.5>326.5 (-3%) x | 316.5>326.5 (-3%) x | 316.5>326.5 (-3%) x | 316.5>326.5 (-3%) x | 87.1>93.9 (-8%) x | 30.8>27.3 (+11%) | 30.8>27.3 (+11%) / 88.0>73.8 (+16%) / 87.8>93.9 (-7%) / 12.4>11.1 (+10%) |
| L3 THL L6_a30_r2_w10 POOL6 | 316.5>258.2 (+18%) | 162.0>258.2 (-59%) x | 316.5>258.2 (+18%) | 316.5>258.2 (+18%) | 316.5>258.2 (+18%) | 316.5>258.2 (+18%) | 87.1>258.2 (-196%) x | 30.8>96.5 (-214%) | 30.8>90.5 (-194%) / 88.0>96.5 (-10%) / 87.8>258.2 (-194%) / 12.4>0.0 (+100%) |
| L4 THL L6_a30_r3_w30 HM | 316.5>309.3 (+2%) x | 162.0>151.4 (+7%) x | 316.5>309.3 (+2%) x | 316.5>309.3 (+2%) x | 316.5>309.3 (+2%) x | 316.5>309.3 (+2%) x | 87.1>87.9 (-1%) x | 30.8>30.1 (+2%) | 30.8>30.1 (+2%) / 88.0>70.2 (+20%) / 87.8>87.9 (-0%) / 12.4>11.1 (+10%) |
| L4 THL L6_a30_r3_w30 POOL6 | 316.5>187.4 (+41%) | 162.0>146.5 (+10%) x | 316.5>187.4 (+41%) | 316.5>187.4 (+41%) | 316.5>187.4 (+41%) | 316.5>187.4 (+41%) | 87.1>146.5 (-68%) x | 30.8>110.9 (-260%) | 30.8>110.9 (-260%) / 88.0>110.9 (-26%) / 87.8>146.5 (-67%) / 12.4>2.4 (+81%) |
| L5 THL L6_a15_r3_w30 HM | 316.5>339.2 (-7%) x | 162.0>141.3 (+13%) | 316.5>339.2 (-7%) x | 316.5>339.2 (-7%) x | 316.5>339.2 (-7%) x | 316.5>339.2 (-7%) x | 87.1>98.5 (-13%) x | 30.8>29.6 (+4%) | 30.8>29.6 (+4%) / 88.0>74.9 (+15%) / 87.8>98.5 (-12%) / 12.4>16.4 (-33%) |
| L5 THL L6_a15_r3_w30 POOL6 | 316.5>398.5 (-26%) x | 162.0>398.5 (-146%) x | 316.5>398.5 (-26%) x | 316.5>398.5 (-26%) x | 316.5>398.5 (-26%) x | 316.5>398.5 (-26%) x | 87.1>398.5 (-358%) x | 30.8>128.7 (-318%) | 30.8>128.7 (-318%) / 88.0>128.7 (-46%) / 87.8>398.5 (-354%) / 12.4>0.8 (+94%) |
| U1 L2SL A30 mult20@5 ne0 none | 316.5>203.6 (+36%) | 162.0>123.7 (+24%) | 316.5>203.6 (+36%) | 316.5>203.6 (+36%) | 316.5>203.6 (+36%) | 316.5>203.6 (+36%) | 87.1>109.3 (-26%) x | 30.8>43.2 (-40%) | 30.8>43.2 (-40%) / 88.0>60.9 (+31%) / 87.8>109.3 (-24%) / 12.4>0.0 (+100%) |
| U2 L2SL A30 mult20@5 ne1 none | 316.5>211.5 (+33%) | 162.0>152.2 (+6%) x | 316.5>211.5 (+33%) | 316.5>211.5 (+33%) | 316.5>211.5 (+33%) | 316.5>211.5 (+33%) | 87.1>152.2 (-75%) x | 30.8>45.7 (-49%) | 30.8>45.7 (-49%) / 88.0>65.2 (+26%) / 87.8>152.2 (-73%) / 12.4>0.0 (+100%) |
| U3 L2SL A30 mult100@5 ne0 none | 316.5>196.6 (+38%) | 162.0>154.7 (+4%) x | 316.5>196.6 (+38%) | 316.5>196.6 (+38%) | 316.5>196.6 (+38%) | 316.5>196.6 (+38%) | 87.1>141.3 (-62%) x | 30.8>43.8 (-43%) | 30.8>43.8 (-43%) / 88.0>78.9 (+10%) / 87.8>141.3 (-61%) / 12.4>7.5 (+39%) |
| U4 L2SL A30 mult100@5 ne1 none | 316.5>301.2 (+5%) x | 162.0>167.6 (-4%) x | 316.5>301.2 (+5%) x | 316.5>301.2 (+5%) x | 316.5>301.2 (+5%) x | 316.5>301.2 (+5%) x | 87.1>84.0 (+4%) x | 30.8>30.8 (-0%) | 30.8>30.8 (-0%) / 88.0>72.5 (+18%) / 87.8>84.0 (+4%) / 12.4>17.3 (-40%) |
| R1 arm-only A30 (no L2) | 316.5>161.7 (+49%) | 162.0>113.4 (+30%) | 316.5>161.7 (+49%) | 316.5>161.7 (+49%) | 316.5>161.7 (+49%) | 316.5>161.7 (+49%) | 87.1>93.5 (-7%) x | 30.8>47.5 (-54%) | 30.8>41.3 (-34%) / 88.0>65.0 (+26%) / 87.8>93.5 (-7%) / 12.4>0.0 (+100%) |
| R2 arm-only A45 (no L2) | 316.5>164.6 (+48%) | 162.0>131.9 (+19%) | 316.5>164.6 (+48%) | 316.5>164.6 (+48%) | 316.5>164.6 (+48%) | 316.5>164.6 (+48%) | 87.1>131.9 (-52%) x | 30.8>35.8 (-16%) | 30.8>21.8 (+29%) / 88.0>59.1 (+33%) / 87.8>131.9 (-50%) / 12.4>3.3 (+73%) |

'x' = does not survive. Removing ep2-ep5 leaves the ALL maxDD set by ep1 (2023), so those columns test only the rest of the tail; ep1 removed shows what is left once the 316.5k episode is gone; all five removed is the strict test (as in DS3_FED_BLACKOUT).

## 3. Matched placebos, 1,000 engine-exact draws each (rank = share of draws with a SMALLER maxDD cut than the real cell; p = (1+#draws >= real)/(n+1); the placebo is run through the same lock engine, so the lock channel is in the null)

Universe = engine-taken trades (as-is final size > 0) that reached the arm; strata = book x side x session x hold-time quartile; the real fired count per stratum is kept. **M** = random trades at their first arm-qualified decision row (the plain arm cut, no L2 condition); **T** = random trades, cut at the arm-qualified row nearest an ABSOLUTE time-in-trade drawn from the real fires of the stratum (the L2 condition replaced by a random same-share condition at the same time-in-trade; prereg definition); **A** = as T but the drawn time is time SINCE THE ARM crossing (ADDENDUM 2, added because T pushes the cut later than the arm crossing for rules that fire at the crossing); **S** = the real fired trades cut at a random arm-qualified row; **R** (UFP trails / target chooser) = the real deltas reassigned to random stratum-matched trades at the same fraction of their hold.

| cell | set | n draws | L6M real / placebo mean [p5, p95] / rank (p) | PRE | X' | ALL | draws with L6M cut >= 20% | PRE and X' both >= 20% | all three |
|---|---|---|---|---|---|---|---|---|---|
| S1 L2SL A45 z10>=2 ne0 ICE | M | 1000 | +61% / +32% [+10%, +56%] / 99% (0.007) | +35% / +25% [+12%, +39%] / 88% (0.117) | +31% / +35% [+14%, +55%] / 39% (0.614) | +31% / +35% [+14%, +54%] / 39% (0.614) | 82% | 65% | 54% |
| S1 L2SL A45 z10>=2 ne0 ICE | A | 1000 | +61% / +25% [-3%, +50%] / 100% (0.003) | +35% / +22% [+7%, +37%] / 91% (0.092) | +31% / +21% [-1%, +43%] / 77% (0.232) | +31% / +21% [-1%, +43%] / 77% (0.232) | 63% | 31% | 21% |
| S1 L2SL A45 z10>=2 ne0 ICE | T | 1000 | +61% / +19% [-7%, +45%] / 100% (0.001) | +35% / +19% [+1%, +36%] / 93% (0.067) | +31% / +16% [-8%, +38%] / 86% (0.141) | +31% / +16% [-8%, +38%] / 86% (0.141) | 47% | 19% | 9% |
| S1 L2SL A45 z10>=2 ne0 ICE | S | 1000 | +61% / +41% [+23%, +53%] / 100% (0.001) | +35% / +33% [+28%, +38%] / 65% (0.347) | +31% / +23% [+17%, +27%] / 100% (0.001) | +31% / +23% [+17%, +27%] / 100% (0.001) | 100% | 89% | 89% |
| S2 L2SL A45 z10>=2 ne0 ICESWP | M | 500 | +61% / +31% [+10%, +54%] / 100% (0.004) | +36% / +26% [+12%, +40%] / 88% (0.118) | +32% / +34% [+12%, +56%] / 42% (0.583) | +32% / +34% [+12%, +54%] / 42% (0.583) | 81% | 65% | 52% |
| S2 L2SL A45 z10>=2 ne0 ICESWP | A | 500 | +61% / +25% [-2%, +51%] / 100% (0.004) | +36% / +22% [+6%, +37%] / 92% (0.080) | +32% / +20% [-2%, +41%] / 80% (0.198) | +32% / +20% [-2%, +41%] / 80% (0.198) | 61% | 30% | 17% |
| S3 L2SL A45 z10>=2 ne0 K2 | M | 500 | +61% / +32% [+9%, +55%] / 99% (0.008) | +36% / +26% [+12%, +41%] / 85% (0.156) | +32% / +34% [+12%, +57%] / 43% (0.569) | +32% / +34% [+12%, +54%] / 43% (0.569) | 84% | 63% | 53% |
| S3 L2SL A45 z10>=2 ne0 K2 | A | 500 | +61% / +26% [-4%, +52%] / 100% (0.002) | +36% / +23% [+5%, +37%] / 94% (0.064) | +32% / +19% [-5%, +42%] / 84% (0.160) | +32% / +19% [-5%, +42%] / 84% (0.160) | 65% | 32% | 20% |
| S4 L2SL A30 z5>=3 none | M | 1000 | +26% / +22% [-4%, +49%] / 60% (0.406) | +30% / +9% [-28%, +35%] / 86% (0.137) | +20% / +15% [-14%, +42%] / 60% (0.400) | +20% / +15% [-14%, +41%] / 60% (0.398) | 54% | 13% | 7% |
| S4 L2SL A30 z5>=3 none | A | 1000 | +26% / +12% [-16%, +39%] / 79% (0.207) | +30% / -1% [-40%, +29%] / 95% (0.047) | +20% / -10% [-41%, +20%] / 95% (0.050) | +20% / -10% [-41%, +19%] / 95% (0.049) | 32% | 1% | 0% |
| S4 L2SL A30 z5>=3 none | T | 1000 | +26% / +10% [-20%, +36%] / 84% (0.160) | +30% / -5% [-45%, +27%] / 98% (0.022) | +20% / -5% [-35%, +24%] / 92% (0.082) | +20% / -5% [-35%, +24%] / 92% (0.079) | 27% | 1% | 0% |
| S4 L2SL A30 z5>=3 none | S | 1000 | +26% / +34% [+29%, +37%] / 3% (0.972) | +30% / +32% [+27%, +39%] / 15% (0.852) | +20% / +24% [+20%, +28%] / 5% (0.946) | +20% / +24% [+20%, +28%] / 5% (0.946) | 98% | 96% | 94% |
| S5 L2SL A45 mult100@30 ne1 ICE | M | 1000 | +70% / +38% [+20%, +56%] / 100% (0.001) | +39% / +35% [+26%, +47%] / 74% (0.260) | +49% / +50% [+36%, +63%] / 43% (0.574) | +49% / +50% [+36%, +60%] / 43% (0.573) | 95% | 100% | 95% |
| S5 L2SL A45 mult100@30 ne1 ICE | A | 1000 | +70% / +32% [+7%, +52%] / 100% (0.001) | +39% / +34% [+22%, +46%] / 74% (0.265) | +49% / +39% [+22%, +54%] / 86% (0.141) | +49% / +39% [+22%, +53%] / 86% (0.139) | 82% | 95% | 78% |
| S5 L2SL A45 mult100@30 ne1 ICE | T | 1000 | +70% / +19% [-4%, +41%] / 100% (0.001) | +39% / +25% [+7%, +40%] / 93% (0.074) | +49% / +15% [-5%, +35%] / 100% (0.002) | +49% / +15% [-5%, +35%] / 100% (0.002) | 46% | 24% | 10% |
| S5 L2SL A45 mult100@30 ne1 ICE | S | 1000 | +70% / +48% [+44%, +57%] / 100% (0.001) | +39% / +34% [+28%, +43%] / 81% (0.195) | +49% / +34% [+26%, +40%] / 100% (0.001) | +49% / +34% [+26%, +40%] / 100% (0.001) | 100% | 99% | 99% |
| H L2SL A45 mult20@30 ne1 ICE (headline) | M | 1000 | +73% / +32% [+26%, +40%] / 100% (0.001) | +38% / +36% [+29%, +48%] / 69% (0.312) | +41% / +52% [+48%, +56%] / 1% (0.991) | +41% / +52% [+48%, +56%] / 1% (0.991) | 100% | 100% | 100% |
| H L2SL A45 mult20@30 ne1 ICE (headline) | A | 1000 | +73% / +29% [+21%, +38%] / 100% (0.001) | +38% / +36% [+25%, +47%] / 62% (0.378) | +41% / +43% [+34%, +50%] / 30% (0.695) | +41% / +43% [+34%, +50%] / 30% (0.695) | 95% | 100% | 95% |
| H L2SL A45 mult20@30 ne1 ICE (headline) | T | 1000 | +73% / +15% [-2%, +27%] / 100% (0.001) | +38% / +24% [+13%, +36%] / 98% (0.024) | +41% / +17% [+5%, +29%] / 100% (0.001) | +41% / +17% [+5%, +29%] / 100% (0.001) | 46% | 25% | 12% |
| H L2SL A45 mult20@30 ne1 ICE (headline) | S | 1000 | +73% / +49% [+45%, +52%] / 100% (0.001) | +38% / +33% [+28%, +38%] / 94% (0.065) | +41% / +9% [+3%, +14%] / 100% (0.001) | +41% / +9% [+3%, +14%] / 100% (0.001) | 100% | 0% | 0% |
| T1 UFP1 F3 icege10 ext10 trail20 | R | 1000 | +55% / -40% [-113%, +20%] / 100% (0.002) | +37% / -58% [-124%, +2%] / 100% (0.001) | +65% / -3% [-53%, +43%] / 100% (0.001) | +57% / -10% [-53%, +28%] / 100% (0.001) | 5% | 0% | 0% |
| T2 UFP1 F3 icege10 ext30 trail20 | R | 500 | +55% / -39% [-120%, +19%] / 100% (0.002) | +37% / -56% [-121%, -0%] / 100% (0.002) | +65% / -6% [-55%, +42%] / 100% (0.004) | +56% / -11% [-56%, +28%] / 100% (0.002) | 4% | 0% | 0% |
| T3 UFP1 F5 d5q20 acc dl30 trail20 | R | 1000 | +54% / -31% [-96%, +23%] / 100% (0.001) | +36% / -50% [-114%, +4%] / 100% (0.001) | +69% / -5% [-57%, +41%] / 100% (0.001) | +53% / -10% [-57%, +27%] / 100% (0.001) | 6% | 0% | 0% |
| T4 UFP1 F1 Wc80 Tb I1 trail20 | R | 1000 | +48% / -6% [-44%, +29%] / 99% (0.008) | +32% / -32% [-77%, +15%] / 100% (0.004) | +62% / -5% [-42%, +33%] / 100% (0.003) | +58% / -6% [-42%, +27%] / 100% (0.001) | 12% | 0% | 0% |
| T5 UFP1 F1 Wc80 Tb I1 trail40 | R | 1000 | +39% / -4% [-41%, +31%] / 98% (0.023) | +34% / -24% [-67%, +15%] / 100% (0.002) | +33% / -16% [-56%, +20%] / 99% (0.009) | +33% / -17% [-56%, +20%] / 100% (0.002) | 13% | 0% | 0% |
| C1 UFP5 dlt_a m0.5 | R | 1000 | +46% / -8% [-51%, +29%] / 99% (0.009) | +42% / -29% [-77%, +16%] / 100% (0.002) | +38% / +27% [-7%, +58%] / 68% (0.324) | +38% / +20% [-8%, +44%] / 87% (0.132) | 10% | 2% | 0% |
| C2 UFP5 dlt_a m0.67 | R | 1000 | +40% / +1% [-26%, +35%] / 97% (0.031) | +45% / -17% [-58%, +21%] / 100% (0.002) | +33% / +30% [+1%, +57%] / 56% (0.440) | +33% / +25% [+1%, +46%] / 68% (0.317) | 16% | 4% | 1% |
| L1 THL L6_a30_r3_w10 HM (live line) | M | 1000 | +15% / +15% [+4%, +24%] / 51% (0.492) | +16% / +8% [-5%, +21%] / 84% (0.164) | -10% / +2% [-9%, +14%] / 4% (0.957) | -10% / +2% [-9%, +14%] / 4% (0.957) | 23% | 0% | 0% |
| L1 THL L6_a30_r3_w10 HM (live line) | A | 1000 | +15% / +9% [-1%, +17%] / 85% (0.148) | +16% / +1% [-14%, +15%] / 95% (0.049) | -10% / -11% [-23%, +1%] / 55% (0.455) | -10% / -11% [-23%, +1%] / 55% (0.455) | 1% | 0% | 0% |
| L1 THL L6_a30_r3_w10 HM (live line) | T | 1000 | +15% / +12% [+1%, +20%] / 68% (0.318) | +16% / -0% [-15%, +14%] / 97% (0.034) | -10% / -10% [-22%, +2%] / 48% (0.521) | -10% / -10% [-22%, +2%] / 48% (0.521) | 5% | 0% | 0% |
| L1 THL L6_a30_r3_w10 POOL6 | M | 1000 | -25% / +16% [-39%, +50%] / 9% (0.908) | -7% / +29% [+5%, +47%] / 1% (0.987) | +26% / +23% [-9%, +54%] / 53% (0.467) | +26% / +23% [-9%, +52%] / 54% (0.466) | 52% | 43% | 23% |
| L1 THL L6_a30_r3_w10 POOL6 | A | 1000 | -25% / -20% [-82%, +25%] / 39% (0.611) | -7% / -7% [-44%, +24%] / 49% (0.513) | +26% / -39% [-80%, +1%] / 100% (0.004) | +26% / -40% [-81%, +1%] / 100% (0.004) | 8% | 0% | 0% |
| L1 THL L6_a30_r3_w10 POOL6 | T | 1000 | -25% / -34% [-101%, +17%] / 56% (0.441) | -7% / -14% [-53%, +18%] / 59% (0.415) | +26% / -35% [-77%, +4%] / 100% (0.004) | +26% / -36% [-80%, +4%] / 100% (0.004) | 4% | 0% | 0% |
| L2 THL L6_a25_r3_w10 HM | M | 500 | +11% / +16% [+4%, +25%] / 23% (0.772) | +18% / +9% [-4%, +22%] / 87% (0.132) | -8% / +1% [-13%, +13%] / 12% (0.882) | -8% / +1% [-13%, +13%] / 12% (0.882) | 33% | 0% | 0% |
| L2 THL L6_a25_r3_w10 HM | A | 500 | +11% / +11% [+1%, +19%] / 48% (0.521) | +18% / +3% [-12%, +16%] / 97% (0.028) | -8% / -13% [-26%, -1%] / 74% (0.265) | -8% / -13% [-26%, -1%] / 74% (0.265) | 4% | 0% | 0% |
| L2 THL L6_a25_r3_w10 POOL6 | M | 500 | -23% / +29% [-11%, +58%] / 3% (0.972) | +8% / +21% [-6%, +44%] / 18% (0.818) | +21% / +37% [+4%, +62%] / 19% (0.814) | +21% / +36% [+4%, +58%] / 19% (0.814) | 71% | 49% | 35% |
| L2 THL L6_a25_r3_w10 POOL6 | A | 500 | -23% / -11% [-74%, +32%] / 29% (0.713) | +8% / -24% [-74%, +14%] / 90% (0.102) | +21% / -28% [-74%, +7%] / 99% (0.012) | +21% / -33% [-83%, +3%] / 100% (0.006) | 15% | 0% | 0% |
| L3 THL L6_a30_r2_w10 HM | M | 500 | +16% / +17% [+12%, +25%] / 54% (0.459) | +13% / +10% [+3%, +18%] / 72% (0.285) | -3% / +7% [-1%, +16%] / 2% (0.982) | -3% / +7% [-1%, +16%] / 2% (0.982) | 11% | 0% | 0% |
| L3 THL L6_a30_r2_w10 HM | A | 500 | +16% / +17% [+12%, +25%] / 47% (0.527) | +13% / +10% [+2%, +18%] / 73% (0.275) | -3% / +7% [-2%, +16%] / 3% (0.972) | -3% / +7% [-2%, +16%] / 3% (0.972) | 15% | 0% | 0% |
| L3 THL L6_a30_r2_w10 POOL6 | M | 500 | -10% / +15% [-20%, +38%] / 10% (0.902) | -59% / +34% [+15%, +50%] / 0% (1.000) | +43% / +45% [+27%, +62%] / 43% (0.571) | +18% / +45% [+27%, +60%] / 1% (0.988) | 48% | 88% | 42% |
| L3 THL L6_a30_r2_w10 POOL6 | A | 500 | -10% / +14% [-19%, +40%] / 11% (0.890) | -59% / +31% [+12%, +49%] / 0% (1.000) | +43% / +43% [+24%, +60%] / 49% (0.515) | +18% / +43% [+24%, +59%] / 2% (0.980) | 44% | 81% | 34% |
| L4 THL L6_a30_r3_w30 HM | M | 500 | +20% / +15% [+6%, +24%] / 84% (0.164) | +7% / +10% [-1%, +20%] / 31% (0.695) | +2% / +5% [-6%, +16%] / 37% (0.627) | +2% / +5% [-6%, +16%] / 37% (0.627) | 18% | 0% | 0% |
| L4 THL L6_a30_r3_w30 HM | A | 500 | +20% / +9% [-1%, +19%] / 98% (0.022) | +7% / +3% [-9%, +15%] / 65% (0.351) | +2% / -9% [-20%, +3%] / 94% (0.060) | +2% / -9% [-20%, +3%] / 94% (0.060) | 2% | 0% | 0% |
| L4 THL L6_a30_r3_w30 POOL6 | M | 500 | -26% / +5% [-42%, +42%] / 12% (0.876) | +10% / +28% [+7%, +46%] / 6% (0.938) | +41% / +37% [+13%, +61%] / 57% (0.433) | +41% / +37% [+13%, +58%] / 57% (0.431) | 33% | 70% | 22% |
| L4 THL L6_a30_r3_w30 POOL6 | A | 500 | -26% / -56% [-137%, +7%] / 72% (0.277) | +10% / +0% [-28%, +23%] / 71% (0.293) | +41% / -15% [-49%, +15%] / 100% (0.004) | +41% / -15% [-49%, +15%] / 100% (0.002) | 1% | 0% | 0% |
| L5 THL L6_a15_r3_w30 HM | M | 500 | +15% / +16% [+5%, +27%] / 42% (0.579) | +13% / +17% [+5%, +28%] / 23% (0.766) | -7% / -10% [-25%, +5%] / 63% (0.373) | -7% / -10% [-25%, +5%] / 63% (0.373) | 25% | 0% | 0% |
| L5 THL L6_a15_r3_w30 HM | A | 500 | +15% / +14% [+3%, +25%] / 57% (0.429) | +13% / +6% [-7%, +18%] / 78% (0.220) | -7% / -30% [-45%, -16%] / 99% (0.012) | -7% / -30% [-45%, -16%] / 99% (0.012) | 18% | 0% | 0% |
| L5 THL L6_a15_r3_w30 POOL6 | M | 500 | -46% / -3% [-73%, +43%] / 12% (0.884) | -146% / +11% [-29%, +39%] / 0% (1.000) | +59% / +40% [+8%, +63%] / 88% (0.120) | -26% / +37% [+8%, +57%] / 0% (0.998) | 31% | 34% | 10% |
| L5 THL L6_a15_r3_w30 POOL6 | A | 500 | -46% / -173% [-324%, -40%] / 94% (0.064) | -146% / -208% [-336%, -86%] / 78% (0.224) | +59% / -57% [-105%, -12%] / 100% (0.002) | -26% / -236% [-323%, -141%] / 100% (0.002) | 0% | 0% | 0% |
| U1 L2SL A30 mult20@5 ne0 none | M | 500 | +31% / +34% [+26%, +47%] / 22% (0.780) | +33% / +40% [+34%, +50%] / 3% (0.974) | +36% / +52% [+45%, +60%] / 0% (1.000) | +36% / +52% [+45%, +60%] / 0% (1.000) | 99% | 100% | 98% |
| U1 L2SL A30 mult20@5 ne0 none | A | 500 | +31% / +23% [+12%, +36%] / 85% (0.154) | +33% / +34% [+24%, +45%] / 39% (0.609) | +36% / +33% [+24%, +45%] / 66% (0.341) | +36% / +33% [+24%, +45%] / 66% (0.341) | 63% | 97% | 61% |
| U2 L2SL A30 mult20@5 ne1 none | M | 500 | +26% / +35% [+20%, +52%] / 13% (0.872) | +6% / +39% [+25%, +51%] / 0% (1.000) | +33% / +51% [+38%, +62%] / 1% (0.994) | +33% / +51% [+38%, +62%] / 1% (0.994) | 95% | 98% | 94% |
| U2 L2SL A30 mult20@5 ne1 none | A | 500 | +26% / +17% [-8%, +38%] / 74% (0.259) | +6% / +29% [+17%, +42%] / 1% (0.994) | +33% / +27% [+11%, +43%] / 75% (0.255) | +33% / +27% [+11%, +43%] / 75% (0.255) | 41% | 67% | 27% |
| U3 L2SL A30 mult100@5 ne0 none | M | 500 | +10% / +32% [-9%, +57%] / 13% (0.870) | +13% / +35% [+10%, +52%] / 7% (0.932) | +38% / +26% [-5%, +53%] / 74% (0.265) | +38% / +26% [-5%, +52%] / 74% (0.265) | 78% | 55% | 45% |
| U3 L2SL A30 mult100@5 ne0 none | A | 500 | +10% / +12% [-33%, +43%] / 41% (0.589) | +13% / +10% [-24%, +36%] / 56% (0.437) | +38% / -22% [-54%, +13%] / 100% (0.002) | +38% / -22% [-54%, +13%] / 100% (0.002) | 42% | 1% | 1% |
| U4 L2SL A30 mult100@5 ne1 none | M | 500 | +18% / +33% [+2%, +58%] / 18% (0.822) | +16% / +30% [+2%, +49%] / 18% (0.824) | +5% / +23% [-7%, +49%] / 14% (0.862) | +5% / +23% [-7%, +49%] / 14% (0.862) | 80% | 45% | 36% |
| U4 L2SL A30 mult100@5 ne1 none | A | 500 | +18% / +21% [-9%, +48%] / 38% (0.617) | +16% / +14% [-16%, +40%] / 50% (0.503) | +5% / -5% [-36%, +25%] / 68% (0.319) | +5% / -5% [-36%, +25%] / 68% (0.319) | 57% | 3% | 2% |
| R1 arm-only A30 (no L2) | M | 500 | +26% / +33% [+33%, +33%] / 0% (1.000) | +42% / +39% [+39%, +39%] / 100% (0.002) | +49% / +54% [+54%, +54%] / 0% (1.000) | +49% / +54% [+54%, +54%] / 0% (1.000) | 100% | 100% | 100% |
| R1 arm-only A30 (no L2) | A | 500 | +26% / +33% [+33%, +33%] / 0% (1.000) | +42% / +39% [+39%, +39%] / 100% (0.002) | +49% / +54% [+54%, +54%] / 0% (1.000) | +49% / +54% [+54%, +54%] / 0% (1.000) | 100% | 100% | 100% |
| R2 arm-only A45 (no L2) | M | 500 | +33% / +31% [+31%, +31%] / 100% (0.002) | +19% / +37% [+37%, +37%] / 0% (1.000) | +48% / +54% [+54%, +54%] / 0% (1.000) | +48% / +54% [+54%, +54%] / 0% (1.000) | 100% | 100% | 100% |
| R2 arm-only A45 (no L2) | A | 500 | +33% / +32% [+31%, +32%] / 99% (0.016) | +19% / +37% [+37%, +37%] / 0% (1.000) | +48% / +54% [+54%, +54%] / 0% (1.000) | +48% / +54% [+54%, +54%] / 0% (1.000) | 100% | 100% | 100% |

Reading. A cell passes G3 only if its real cut ranks >= 95% in L6M, PRE and X' under every placebo that applies. A rank near 100% in L6M together with a low rank in X' is the signature of one lucky week plus a stop-tightening effect; a placebo that already satisfies the 20% cut in PRE and X' in a large share of draws means those windows do not discriminate (the 'draws with PRE and X' both >= 20%' column).

## 4. Stationary-bootstrap 95% CIs of the CHANGE (after minus before; paired weekly series, mean block 4 weeks, 4,000 resamples, seed 20261101; block-8 maxDD CI in the last column)

| cell | window | dMaxDD $k [CI] P(better) | dWorst (w20/w5) $k [CI] | dSD $k [CI] | dCalmar [CI] | dMaxDD CI block 8 |
|---|---|---|---|---|---|---|
| S1 L2SL A45 z10>=2 ne0 ICE | L3M | -54.0 [-94.1, 14.2] 0.81 | 75.2 [-19.9, 163.7] | -4.0 [-14.9, 9.9] | +0.373 [-0.336, +0.680] | [-82.9, 14.2] |
|  | L6M | -54.0 [-83.8, 14.2] 0.81 | 72.8 [-17.3, 182.4] | -5.3 [-12.0, 2.4] | +0.433 [-0.563, +0.837] | [-73.3, 14.2] |
|  | HOLD | -1.5 [-67.6, 15.3] 0.83 | 50.2 [-28.6, 160.9] | -3.2 [-9.6, 2.7] | +0.012 [-0.262, +0.591] | [-55.0, 13.2] |
|  | PRE | -56.3 [-134.6, 58.4] 0.66 | 2.0 [-189.5, 207.8] | -1.2 [-5.4, 3.2] | +0.079 [-0.075, +0.142] | [-132.6, 45.2] |
|  | X' | -98.5 [-245.6, 32.0] 0.89 | 11.7 [-150.1, 164.9] | 5.3 [-0.4, 11.8] | +0.024 [+0.001, +0.098] | [-246.5, 19.6] |
|  | ALL | -98.5 [-205.8, 43.6] 0.84 | 77.1 [-125.0, 298.2] | -0.7 [-3.9, 2.5] | +0.033 [-0.010, +0.083] | [-249.5, 26.3] |
| S2 L2SL A45 z10>=2 ne0 ICESWP | L3M | -54.0 [-95.6, 14.2] 0.81 | 74.5 [-19.6, 164.9] | -3.8 [-14.1, 9.5] | +0.405 [-0.313, +0.721] | [-82.3, 14.2] |
|  | L6M | -54.0 [-84.1, 14.2] 0.81 | 72.2 [-16.9, 180.5] | -5.3 [-11.8, 2.1] | +0.446 [-0.557, +0.868] | [-72.7, 14.2] |
|  | HOLD | 9.8 [-60.2, 24.0] 0.44 | 40.1 [-38.3, 155.5] | -2.7 [-9.2, 3.0] | -0.000 [-0.260, +0.607] | [-54.0, 18.6] |
|  | PRE | -58.0 [-131.3, 56.3] 0.66 | -0.0 [-187.0, 201.3] | -0.9 [-5.1, 3.5] | +0.085 [-0.072, +0.141] | [-130.4, 43.6] |
|  | X' | -101.7 [-248.6, 29.5] 0.90 | 8.8 [-153.7, 162.6] | 5.4 [-0.4, 12.0] | +0.024 [+0.001, +0.098] | [-248.9, 15.9] |
|  | ALL | -101.7 [-206.8, 42.0] 0.80 | 64.1 [-136.4, 282.8] | -0.5 [-3.6, 2.7] | +0.035 [-0.010, +0.083] | [-253.8, 27.9] |
| S3 L2SL A45 z10>=2 ne0 K2 | L3M | -54.0 [-96.2, 14.2] 0.81 | 75.1 [-19.6, 166.6] | -3.8 [-14.2, 9.5] | +0.402 [-0.320, +0.733] | [-82.9, 14.2] |
|  | L6M | -54.0 [-84.7, 14.2] 0.81 | 72.8 [-16.6, 182.2] | -5.4 [-11.8, 2.1] | +0.442 [-0.560, +0.881] | [-73.3, 14.2] |
|  | HOLD | 2.7 [-64.8, 17.0] 0.49 | 47.7 [-31.5, 159.1] | -3.1 [-9.3, 2.5] | +0.008 [-0.265, +0.606] | [-55.0, 14.2] |
|  | PRE | -58.0 [-130.2, 56.4] 0.66 | -8.3 [-200.9, 196.9] | -0.7 [-5.0, 3.7] | +0.084 [-0.073, +0.140] | [-129.9, 43.8] |
|  | X' | -102.3 [-241.3, 35.8] 0.89 | 9.4 [-152.6, 162.7] | 4.8 [-0.4, 10.5] | +0.023 [+0.001, +0.097] | [-244.6, 19.5] |
|  | ALL | -102.3 [-205.4, 42.3] 0.81 | 72.3 [-125.5, 289.2] | -0.6 [-3.6, 2.5] | +0.034 [-0.010, +0.083] | [-252.6, 26.6] |
| S4 L2SL A30 z5>=3 none | L3M | -23.3 [-46.5, 6.1] 0.81 | 26.7 [-7.5, 79.5] | -5.4 [-9.8, -0.8] | +0.064 [-0.182, +0.187] | [-41.6, 3.1] |
|  | L6M | -23.3 [-41.6, 10.6] 0.75 | 23.3 [-16.6, 66.7] | -3.3 [-6.9, -0.2] | +0.051 [-0.425, +0.157] | [-28.5, 6.8] |
|  | HOLD | 53.6 [-24.7, 104.9] 0.23 | -33.4 [-95.8, 68.1] | -0.9 [-4.9, 2.4] | -0.062 [-0.322, +0.103] | [-23.3, 87.5] |
|  | PRE | -48.1 [-112.3, 60.7] 0.59 | -8.8 [-165.1, 149.9] | -2.4 [-6.2, 1.4] | +0.045 [-0.096, +0.106] | [-113.9, 57.6] |
|  | X' | -64.4 [-194.7, 27.1] 0.88 | 22.2 [-82.0, 132.5] | 2.0 [-1.8, 6.2] | +0.013 [+0.000, +0.067] | [-177.1, 16.1] |
|  | ALL | -64.4 [-135.1, 85.2] 0.53 | 14.8 [-131.5, 170.8] | -1.7 [-4.1, 0.7] | +0.011 [-0.039, +0.044] | [-142.4, 69.0] |
| S5 L2SL A45 mult100@30 ne1 ICE | L3M | -61.7 [-102.9, 24.9] 0.86 | 91.4 [-10.9, 198.3] | -2.1 [-12.9, 9.3] | +0.662 [-0.442, +1.266] | [-85.3, 20.9] |
|  | L6M | -61.7 [-96.4, 0.9] 0.94 | 92.2 [4.0, 207.0] | -6.3 [-12.3, 0.8] | +0.707 [-0.298, +1.091] | [-85.3, 0.9] |
|  | HOLD | -3.1 [-76.0, 12.2] 0.89 | 68.9 [-12.8, 185.1] | -2.4 [-9.5, 3.6] | +0.027 [-0.153, +0.929] | [-63.4, 6.0] |
|  | PRE | -62.7 [-167.9, 32.4] 0.85 | 99.6 [-93.0, 316.8] | -4.0 [-8.5, 0.3] | +0.106 [-0.049, +0.231] | [-157.4, 31.8] |
|  | X' | -155.2 [-335.7, 7.7] 0.96 | 94.3 [-105.4, 271.3] | 4.1 [-3.0, 12.6] | +0.037 [+0.004, +0.117] | [-326.9, -2.6] |
|  | ALL | -155.2 [-257.3, 12.8] 0.95 | 185.9 [-15.9, 414.2] | -2.4 [-5.7, 1.0] | +0.068 [+0.007, +0.129] | [-295.6, 4.1] |
| H L2SL A45 mult20@30 ne1 ICE (headline) | L3M | -63.6 [-106.9, 20.0] 0.88 | 99.7 [-4.1, 209.9] | -1.9 [-12.5, 8.9] | +0.791 [-0.396, +1.521] | [-88.0, 18.3] |
|  | L6M | -64.4 [-101.9, -0.5] 0.98 | 100.6 [10.0, 216.0] | -6.0 [-12.0, 1.0] | +0.866 [-0.193, +1.297] | [-88.0, -0.5] |
|  | HOLD | -19.0 [-84.6, 1.8] 0.96 | 83.5 [2.6, 199.6] | -2.4 [-9.3, 3.4] | +0.062 [-0.068, +1.118] | [-68.6, 0.2] |
|  | PRE | -60.9 [-161.9, 37.4] 0.78 | 78.0 [-109.4, 279.2] | -3.8 [-8.4, 0.7] | +0.095 [-0.059, +0.208] | [-153.3, 33.9] |
|  | X' | -131.3 [-299.2, 25.6] 0.92 | 70.2 [-137.4, 252.5] | 3.9 [-4.0, 12.8] | +0.025 [+0.001, +0.092] | [-294.5, 13.8] |
|  | ALL | -131.3 [-242.5, 19.4] 0.93 | 142.3 [-65.3, 385.7] | -2.1 [-5.6, 1.5] | +0.052 [+0.000, +0.116] | [-276.0, 13.2] |
| T1 UFP1 F3 icege10 ext10 trail20 | L3M | -48.4 [-86.3, 20.6] 0.85 | 74.0 [-17.9, 147.9] | -13.1 [-25.9, 1.0] | +0.058 [-0.543, +0.239] | [-77.0, 11.8] |
|  | L6M | -48.4 [-77.0, 21.0] 0.81 | 52.2 [-35.5, 150.8] | -11.5 [-19.9, -0.1] | +0.118 [-0.892, +0.243] | [-58.5, 13.9] |
|  | HOLD | -7.9 [-59.4, 34.6] 0.78 | 36.3 [-42.4, 126.8] | -9.2 [-17.8, -1.8] | -0.047 [-0.456, +0.208] | [-51.8, 22.7] |
|  | PRE | -60.3 [-141.3, 80.1] 0.62 | 14.2 [-205.0, 236.0] | -8.8 [-13.9, -3.3] | -0.010 [-0.167, +0.051] | [-123.9, 56.8] |
|  | X' | -205.9 [-378.4, 26.5] 0.95 | 152.2 [-35.7, 330.0] | -4.5 [-10.1, 1.2] | +0.016 [-0.024, +0.108] | [-379.9, 14.6] |
|  | ALL | -180.2 [-241.6, 61.8] 0.84 | 175.8 [1.6, 369.5] | -8.4 [-12.1, -4.8] | +0.022 [-0.066, +0.039] | [-299.8, 32.4] |
| T2 UFP1 F3 icege10 ext30 trail20 | L3M | -48.4 [-86.3, 27.2] 0.84 | 68.1 [-26.9, 147.0] | -12.6 [-25.6, 2.1] | +0.045 [-0.575, +0.230] | [-73.7, 18.3] |
|  | L6M | -48.4 [-77.0, 26.1] 0.81 | 46.3 [-45.6, 144.9] | -11.2 [-19.9, 0.5] | +0.112 [-0.935, +0.232] | [-58.5, 17.9] |
|  | HOLD | -4.8 [-56.6, 39.9] 0.76 | 30.4 [-52.3, 124.3] | -9.1 [-17.8, -1.4] | -0.052 [-0.481, +0.199] | [-48.8, 25.5] |
|  | PRE | -60.3 [-141.3, 77.3] 0.63 | 20.8 [-197.8, 241.7] | -9.1 [-14.0, -3.7] | -0.010 [-0.167, +0.052] | [-125.0, 55.7] |
|  | X' | -205.9 [-376.2, 34.4] 0.94 | 152.2 [-36.4, 329.3] | -4.6 [-10.1, 1.1] | +0.013 [-0.027, +0.097] | [-379.9, 17.6] |
|  | ALL | -177.2 [-240.5, 65.9] 0.83 | 176.5 [2.7, 369.7] | -8.5 [-12.1, -4.9] | +0.019 [-0.068, +0.036] | [-292.7, 35.6] |
| T3 UFP1 F5 d5q20 acc dl30 trail20 | L3M | -47.4 [-92.3, 38.8] 0.79 | 70.7 [-19.6, 170.5] | -15.4 [-27.2, -1.4] | +0.047 [-0.622, +0.305] | [-78.2, 33.2] |
|  | L6M | -47.4 [-81.7, 32.7] 0.75 | 63.9 [-25.5, 179.4] | -12.4 [-20.8, -1.8] | +0.102 [-1.004, +0.328] | [-65.7, 26.2] |
|  | HOLD | 4.5 [-56.7, 51.1] 0.34 | 41.7 [-51.6, 145.8] | -9.6 [-18.0, -2.2] | -0.060 [-0.632, +0.193] | [-50.7, 38.5] |
|  | PRE | -57.7 [-142.8, 87.3] 0.61 | 17.9 [-254.1, 265.2] | -9.7 [-14.2, -4.2] | -0.018 [-0.184, +0.047] | [-125.2, 61.0] |
|  | X' | -217.2 [-381.2, 36.2] 0.93 | 132.0 [-52.1, 310.3] | -3.5 [-9.0, 2.2] | +0.014 [-0.027, +0.086] | [-391.0, 17.2] |
|  | ALL | -167.8 [-248.3, 73.5] 0.80 | 186.8 [-36.8, 410.3] | -8.8 [-12.3, -5.3] | +0.013 [-0.074, +0.036] | [-314.2, 34.7] |
| T4 UFP1 F1 Wc80 Tb I1 trail20 | L3M | -41.9 [-77.4, 30.5] 0.77 | 36.0 [-44.5, 118.3] | -9.4 [-20.4, 3.8] | +0.047 [-0.466, +0.153] | [-63.1, 18.5] |
|  | L6M | -41.9 [-63.1, 23.2] 0.72 | 29.2 [-40.1, 125.9] | -7.1 [-14.4, 2.7] | +0.132 [-0.678, +0.217] | [-48.3, 17.7] |
|  | HOLD | -12.4 [-59.9, 23.9] 0.77 | 16.8 [-54.0, 103.1] | -6.8 [-13.1, -0.8] | -0.018 [-0.468, +0.194] | [-47.3, 17.0] |
|  | PRE | -52.1 [-147.0, 75.2] 0.62 | 1.0 [-249.0, 240.7] | -5.0 [-10.2, 0.1] | +0.011 [-0.144, +0.087] | [-130.6, 62.9] |
|  | X' | -197.0 [-324.7, 39.8] 0.92 | 127.8 [-31.3, 278.9] | -3.2 [-8.1, 1.9] | +0.012 [-0.013, +0.064] | [-341.5, 20.5] |
|  | ALL | -184.7 [-232.4, 56.7] 0.84 | 116.4 [-80.8, 318.2] | -5.3 [-8.7, -1.9] | +0.040 [-0.048, +0.048] | [-284.3, 26.4] |
| T5 UFP1 F1 Wc80 Tb I1 trail40 | L3M | -34.1 [-54.3, 17.2] 0.85 | 35.3 [-25.1, 90.8] | -10.9 [-19.9, 0.0] | -0.017 [-0.398, +0.036] | [-39.2, 10.3] |
|  | L6M | -34.1 [-39.5, 18.8] 0.77 | 27.6 [-30.8, 106.9] | -5.0 [-12.2, 2.4] | +0.056 [-0.670, +0.118] | [-38.2, 11.4] |
|  | HOLD | 15.8 [-36.4, 45.5] 0.35 | -0.8 [-90.3, 84.8] | -3.6 [-10.5, 2.2] | -0.051 [-0.471, +0.081] | [-34.1, 40.2] |
|  | PRE | -55.6 [-154.3, 54.7] 0.68 | 45.8 [-148.0, 269.7] | -6.3 [-10.8, -2.1] | +0.023 [-0.124, +0.103] | [-143.5, 52.6] |
|  | X' | -104.9 [-246.1, 127.9] 0.70 | 41.8 [-114.8, 194.5] | -0.6 [-5.6, 4.8] | +0.001 [-0.027, +0.039] | [-251.7, 110.1] |
|  | ALL | -104.9 [-181.9, 102.0] 0.65 | 79.9 [-93.2, 279.1] | -4.5 [-7.7, -1.5] | +0.007 [-0.058, +0.033] | [-199.7, 77.3] |
| C1 UFP5 dlt_a m0.5 | L3M | -40.3 [-78.1, 9.1] 0.87 | 67.2 [9.0, 113.3] | -12.3 [-19.1, -4.0] | +0.060 [-0.419, +0.204] | [-63.3, 5.8] |
|  | L6M | -40.3 [-65.2, 6.3] 0.89 | 68.0 [18.4, 127.6] | -7.2 [-14.1, -2.0] | +0.103 [-0.409, +0.880] | [-58.6, 5.8] |
|  | HOLD | -22.2 [-62.5, 5.8] 0.94 | 56.6 [18.2, 129.7] | -6.8 [-11.2, -2.8] | -0.002 [-0.224, +0.283] | [-52.1, 5.8] |
|  | PRE | -68.0 [-140.1, 43.1] 0.76 | 40.8 [-123.8, 208.6] | -3.5 [-8.1, 1.5] | +0.061 [-0.097, +0.120] | [-134.1, 36.6] |
|  | X' | -119.0 [-224.2, 36.3] 0.88 | 84.0 [-30.1, 202.6] | -2.2 [-7.4, 3.0] | +0.008 [-0.008, +0.059] | [-235.6, 21.8] |
|  | ALL | -119.0 [-186.9, 45.5] 0.85 | 140.0 [-3.4, 296.3] | -3.9 [-6.8, -0.9] | +0.020 [-0.030, +0.058] | [-235.2, 21.9] |
| C2 UFP5 dlt_a m0.67 | L3M | -35.1 [-66.9, 19.3] 0.79 | 22.1 [-31.7, 85.1] | -8.9 [-17.3, 1.8] | +0.027 [-0.405, +0.112] | [-45.7, 14.6] |
|  | L6M | -35.1 [-46.1, 15.8] 0.77 | 22.9 [-28.8, 90.9] | -4.2 [-11.2, 1.1] | +0.115 [-0.442, +0.229] | [-39.2, 8.9] |
|  | HOLD | -12.1 [-47.5, 14.0] 0.85 | 36.9 [-17.1, 98.1] | -3.7 [-8.7, 0.7] | +0.002 [-0.234, +0.224] | [-39.2, 8.2] |
|  | PRE | -72.4 [-138.6, 13.8] 0.89 | 68.4 [-50.7, 189.4] | -2.4 [-5.6, 1.3] | +0.107 [-0.030, +0.170] | [-126.2, 11.4] |
|  | X' | -104.3 [-211.3, 44.8] 0.87 | 83.6 [-23.7, 203.0] | -2.7 [-6.7, 1.4] | +0.005 [-0.008, +0.045] | [-213.8, 31.1] |
|  | ALL | -104.3 [-171.2, 32.7] 0.88 | 141.3 [28.3, 281.5] | -2.5 [-5.0, 0.0] | +0.025 [-0.014, +0.068] | [-194.4, 17.1] |
| L1 THL L6_a30_r3_w10 HM (live line) | L3M | -13.5 [-27.0, 8.6] 0.80 | 19.3 [-10.5, 52.8] | -4.3 [-7.7, 0.6] | +0.046 [-0.155, +0.170] | [-24.0, 8.6] |
|  | L6M | -13.5 [-24.5, 8.6] 0.76 | 7.6 [-19.6, 45.4] | -1.4 [-5.4, 1.7] | +0.066 [-0.186, +0.305] | [-21.1, 8.6] |
|  | HOLD | -1.5 [-23.5, 8.6] 0.82 | 9.5 [-16.6, 46.3] | -0.6 [-3.8, 1.7] | +0.013 [-0.097, +0.105] | [-15.0, 7.1] |
|  | PRE | -25.5 [-46.3, 20.4] 0.76 | -14.3 [-79.6, 47.0] | 0.4 [-1.2, 2.3] | +0.032 [-0.023, +0.056] | [-48.3, 15.4] |
|  | X' | 30.6 [-54.3, 78.1] 0.41 | -5.7 [-60.0, 47.7] | -0.2 [-1.3, 0.9] | +0.000 [-0.012, +0.009] | [-58.1, 77.8] |
|  | ALL | 30.6 [-61.2, 40.9] 0.67 | 32.2 [-13.7, 83.4] | 0.2 [-1.1, 1.4] | -0.001 [-0.010, +0.028] | [-59.6, 54.7] |
| L1 THL L6_a30_r3_w10 POOL6 | L3M | 21.9 [-73.5, 139.1] 0.40 | 9.3 [-122.3, 124.8] | 0.5 [-7.4, 9.6] | -0.061 [-0.766, +0.395] | [-51.3, 123.6] |
|  | L6M | 21.9 [-54.7, 113.3] 0.39 | -0.7 [-111.3, 122.5] | 1.2 [-4.6, 6.7] | -0.070 [-0.977, +0.388] | [-42.7, 94.8] |
|  | HOLD | -2.0 [-55.4, 109.2] 0.54 | 7.8 [-120.9, 144.7] | 1.5 [-3.6, 6.8] | -0.011 [-0.712, +0.215] | [-40.0, 87.8] |
|  | PRE | 10.6 [-97.2, 161.4] 0.37 | -51.0 [-298.3, 166.0] | -1.6 [-8.3, 4.8] | -0.034 [-0.196, +0.064] | [-94.7, 142.5] |
|  | X' | -81.2 [-249.9, 21.8] 0.93 | 130.9 [-25.4, 291.6] | 1.4 [-5.5, 8.7] | +0.022 [+0.001, +0.124] | [-230.4, 17.6] |
|  | ALL | -81.2 [-170.1, 135.1] 0.57 | 51.7 [-180.8, 277.7] | -0.8 [-4.8, 2.9] | +0.010 [-0.065, +0.045] | [-198.7, 108.0] |

The upper bound of an L6M/HOLD/L3M maxDD interval is near 0.0 when a resample never touches the cut week; the maxDD intervals of PRE, X' and ALL contain zero for every cell whose cut is carried by a few weeks.

## 5. What the rule does to the mean and at equal risk

| cell | ALL mean base>rule $k/wk | ALL change (MDE) [CI] | equal-risk lot scale c | equal-risk change ALL / L6M / PRE / X' (MDE) | first-order $/wk ALL (trade-level pts x size) | exact $/wk ALL | corr first-order vs exact daily |
|---|---|---|---|---|---|---|---|
| S1 L2SL A45 z10>=2 ne0 ICE | 13.1>16.2 | 3.1 (4.9) [-0.2, 6.7] | 1.071 | 4.3 (5.1) / 3.0 (14.3) / 3.4 (6.7) / 6.4 (9.1) | 1.0 | 3.1 | 0.63 |
| S2 L2SL A45 z10>=2 ne0 ICESWP | 13.1>16.3 | 3.3 (4.8) [-0.1, 6.9] | 1.058 | 4.2 (5.0) / 3.2 (14.2) / 3.4 (6.5) / 6.4 (9.0) | 1.0 | 3.3 | 0.63 |
| S3 L2SL A45 z10>=2 ne0 K2 | 13.1>16.2 | 3.2 (4.8) [-0.2, 6.8] | 1.066 | 4.2 (5.0) / 3.3 (14.2) / 3.5 (6.6) / 6.1 (8.8) | 0.8 | 3.2 | 0.63 |
| S4 L2SL A30 z5>=3 none | 13.1>13.1 | 0.1 (3.4) [-2.8, 3.0] | 1.013 | 0.3 (3.4) / -2.2 (6.9) / -0.2 (5.1) / 4.1 (5.3) | 0.3 | 0.1 | 0.71 |
| S5 L2SL A45 mult100@30 ne1 ICE | 13.1>17.7 | 4.6 (5.4) [0.8, 8.7] | 1.191 | 8.0 (6.1) / 8.1 (17.9) / 7.5 (7.8) / 8.5 (10.7) | 0.3 | 4.6 | 0.72 |
| H L2SL A45 mult20@30 ne1 ICE (headline) | 13.1>17.2 | 4.1 (5.7) [0.1, 8.3] | 1.140 | 6.5 (6.1) / 8.2 (17.4) / 5.5 (7.9) / 6.4 (10.9) | -0.2 | 4.1 | 0.74 |
| T1 UFP1 F3 icege10 ext10 trail20 | 13.1>8.6 | -4.5 (6.1) [-9.0, 0.3] | 1.178 | -2.9 (6.3) / -4.7 (12.7) / -6.1 (9.2) / 4.2 (11.6) | -5.2 | -4.5 | 0.82 |
| T2 UFP1 F3 icege10 ext30 trail20 | 13.1>8.4 | -4.6 (6.2) [-9.2, 0.1] | 1.179 | -3.1 (6.4) / -5.0 (12.9) / -6.1 (9.2) / 3.7 (11.8) | -5.3 | -4.6 | 0.82 |
| T3 UFP1 F5 d5q20 acc dl30 trail20 | 13.1>8.1 | -4.9 (6.2) [-9.8, 0.0] | 1.192 | -3.4 (6.4) / -4.8 (12.7) / -6.5 (9.3) / 3.8 (11.9) | -4.8 | -4.9 | 0.82 |
| T4 UFP1 F1 Wc80 Tb I1 trail20 | 13.1>10.8 | -2.3 (5.3) [-6.2, 1.5] | 1.111 | -1.1 (5.4) / -2.3 (9.9) / -3.3 (8.4) / 3.5 (8.9) | -2.9 | -2.3 | 0.82 |
| T5 UFP1 F1 Wc80 Tb I1 trail40 | 13.1>10.2 | -2.8 (4.6) [-6.4, 0.9] | 1.074 | -2.1 (4.6) / -4.1 (8.2) / -2.8 (6.9) / 1.1 (8.4) | -2.6 | -2.8 | 0.85 |
| C1 UFP5 dlt_a m0.5 | 13.1>12.1 | -1.0 (4.5) [-4.4, 2.3] | 1.137 | 0.7 (4.7) / -2.7 (11.1) / 0.2 (7.1) / 2.7 (7.2) | -1.1 | -1.0 | 0.84 |
| C2 UFP5 dlt_a m0.67 | 13.1>14.0 | 0.9 (3.7) [-1.7, 3.8] | 1.139 | 2.9 (4.0) / 0.1 (9.4) / 4.0 (5.8) / 2.1 (6.3) | -0.1 | 0.9 | 0.85 |
| L1 THL L6_a30_r3_w10 HM (live line) | 13.1>14.1 | 1.0 (1.6) [-0.2, 2.3] | 1.029 | 1.4 (1.6) / 2.3 (4.2) / 2.0 (2.5) / -0.3 (2.1) | 0.3 | 1.0 | 0.86 |
| L1 THL L6_a30_r3_w10 POOL6 | 13.1>12.1 | -0.9 (5.9) [-6.4, 4.0] | 1.047 | -0.3 (6.0) / -1.4 (14.3) / -3.9 (9.0) / 6.2 (9.0) | -3.2 | -0.9 | 0.78 |
| L2 THL L6_a25_r3_w10 HM | 13.1>14.0 | 0.9 (1.5) [-0.2, 2.2] | 1.026 | 1.3 (1.6) / 1.9 (4.0) / 1.8 (2.4) / -0.0 (2.3) | 0.3 | 0.9 | 0.89 |
| L2 THL L6_a25_r3_w10 POOL6 | 13.1>12.0 | -1.0 (6.6) [-7.1, 4.7] | 1.075 | -0.1 (6.8) / -2.0 (16.2) / -3.4 (9.8) / 6.8 (11.1) | -3.6 | -1.0 | 0.80 |
| L3 THL L6_a30_r2_w10 HM | 13.1>13.9 | 0.8 (2.1) [-0.7, 2.3] | 1.078 | 1.9 (2.3) / 4.3 (5.8) / 1.7 (3.5) / 0.5 (3.2) | 0.1 | 0.8 | 0.94 |
| L3 THL L6_a30_r2_w10 POOL6 | 13.1>10.5 | -2.6 (8.9) [-11.1, 5.5] | 1.258 | 0.2 (10.0) / -9.1 (20.5) / -3.6 (15.4) / 11.1 (15.5) | -3.8 | -2.6 | 0.86 |
| L4 THL L6_a30_r3_w30 HM | 13.1>14.7 | 1.7 (1.9) [0.5, 2.9] | 1.079 | 2.8 (2.1) / 4.0 (5.7) / 3.4 (3.1) / 0.7 (2.4) | 0.8 | 1.7 | 0.92 |
| L4 THL L6_a30_r3_w30 POOL6 | 13.1>13.5 | 0.4 (7.4) [-5.9, 6.6] | 1.249 | 3.8 (8.2) / -3.7 (19.9) / 2.1 (12.2) / 10.4 (12.8) | -1.9 | 0.4 | 0.82 |
| L5 THL L6_a15_r3_w30 HM | 13.1>13.2 | 0.2 (2.3) [-1.4, 1.8] | 1.051 | 0.8 (2.4) / 0.6 (6.6) / 1.1 (3.4) / 0.2 (3.8) | -0.4 | 0.2 | 0.95 |
| L5 THL L6_a15_r3_w30 POOL6 | 13.1>6.6 | -6.5 (9.4) [-15.6, 1.8] | 1.068 | -6.0 (9.7) / -15.3 (20.0) / -10.7 (15.0) / 7.9 (14.2) | -6.6 | -6.5 | 0.89 |
| U1 L2SL A30 mult20@5 ne0 none | 13.1>10.5 | -2.6 (7.4) [-8.7, 3.0] | 1.258 | 0.1 (8.1) / -1.9 (19.5) / -2.9 (11.9) / 5.8 (13.2) | -2.9 | -2.6 | 0.86 |
| U2 L2SL A30 mult20@5 ne1 none | 13.1>12.7 | -0.4 (6.9) [-6.3, 5.0] | 1.215 | 2.3 (7.6) / -0.1 (19.1) / -1.0 (11.0) / 8.8 (12.1) | -1.4 | -0.4 | 0.85 |
| U3 L2SL A30 mult100@5 ne0 none | 13.1>12.7 | -0.3 (5.4) [-4.7, 3.9] | 1.078 | 0.7 (5.6) / -5.1 (17.8) / 0.8 (7.0) / 4.2 (8.7) | -1.3 | -0.3 | 0.82 |
| U4 L2SL A30 mult100@5 ne1 none | 13.1>12.7 | -0.4 (4.9) [-4.0, 3.1] | 1.012 | -0.2 (5.0) / -3.9 (14.7) / -0.3 (6.4) / 2.6 (8.4) | -0.3 | -0.4 | 0.82 |
| R1 arm-only A30 (no L2) | 13.1>10.1 | -2.9 (7.6) [-9.3, 2.9] | 1.287 | -0.0 (8.4) / -2.4 (19.6) / -4.1 (12.4) / 8.0 (13.6) | -3.2 | -2.9 | 0.87 |
| R2 arm-only A45 (no L2) | 13.1>16.6 | 3.5 (5.5) [-0.5, 7.8] | 1.107 | 5.3 (5.8) / 3.3 (16.3) / 5.0 (7.8) / 6.5 (10.2) | -0.4 | 3.5 | 0.75 |

Equal-risk = the engine lot scale c (all planned lots, the governor R and the integer half-up rounding move together) at which the rule's ALL worst-20 weeks equal the as-is stack's; the change is mean(rule at c) minus mean(as-is). A c above 1 means the rule lowered the tail and the book may be run bigger. For the A=45 cells the first-order trade P&L is about zero while the exact engine gain is +3.5 to +4.6k/wk: the difference is the trades the lock engine admits once losses are cut shorter (kept-trade counts in section 6).

## 6. Execution realism (as-is frame, exact engine): market fill after the trigger, cut cost, stop-cost basis, frames

Base case = fill at the 1-s path close of the trigger second at cost 0.995 pt (measured market exit), baseline stops at 2.45 (live join basis). Delay +1 s / +3 s = the exit executes later at the later 1-s close (and the exit second moves with it). Cost 1.28 / 2.45 = the forced exit pays a Native / join stop cost instead of 0.995. 'base stop 1.28' = baseline AND rule on the N-basis stop cost. 'A12' = as-is with the 12R combined week lock (D6 as coded; informational). Cells: maxDD cut L6M / PRE / X' ; ALL mean change $k/wk (ALL cut).

| cell | base case | +1 s | +3 s | cost 1.28 | cost 2.45 (stress) | +3 s and 2.45 (stress) | base stop 1.28 | composite frame | A12 (12R lock) |
|---|---|---|---|---|---|---|---|---|---|
| S1 L2SL A45 z10>=2 ne0 ICE | +61% / +35% / +31% ; 3.1 (+31%) | +62% / +34% / +32% ; 3.5 (+32%) | +61% / +35% / +33% ; 3.5 (+33%) | +61% / +34% / +30% ; 2.8 (+30%) | +57% / +31% / +25% ; 0.6 (+25%) | +59% / +31% / +27% ; 1.7 (+27%) | +55% / +25% / +29% ; 2.0 (+29%) | +36% / +24% / +9% ; 1.3 (+24%) | -1% / +41% / +9% ; 2.4 (+9%) |
| S2 L2SL A45 z10>=2 ne0 ICESWP | +61% / +36% / +32% ; 3.3 (+32%) | +62% / +35% / +32% ; 3.5 (+32%) | +61% / +37% / +31% ; 3.6 (+31%) | +61% / +35% / +29% ; 2.9 (+29%) | +56% / +33% / +24% ; 0.8 (+24%) | +59% / +34% / +25% ; 1.7 (+25%) | +54% / +26% / +30% ; 2.2 (+30%) | +36% / +24% / +8% ; 1.3 (+24%) | -1% / +41% / +8% ; 2.6 (+8%) |
| S3 L2SL A45 z10>=2 ne0 K2 | +61% / +36% / +32% ; 3.2 (+32%) | +62% / +35% / +32% ; 3.4 (+32%) | +61% / +37% / +31% ; 3.5 (+31%) | +61% / +35% / +29% ; 2.8 (+29%) | +57% / +33% / +24% ; 0.7 (+24%) | +59% / +33% / +25% ; 1.6 (+25%) | +54% / +26% / +30% ; 2.1 (+30%) | +36% / +24% / +8% ; 1.2 (+24%) | -1% / +41% / +9% ; 2.6 (+9%) |
| S4 L2SL A30 z5>=3 none | +26% / +30% / +20% ; 0.1 (+20%) | +26% / +29% / +21% ; -0.1 (+21%) | +26% / +25% / +21% ; -0.0 (+21%) | +26% / +29% / +20% ; -0.1 (+20%) | +25% / +28% / +20% ; -0.8 (+20%) | +24% / +29% / +22% ; -0.7 (+22%) | +28% / +21% / +19% ; -0.2 (+19%) | -18% / +6% / -3% ; -0.1 (+6%) | -1% / -50% / +16% ; -0.5 (-2%) |
| S5 L2SL A45 mult100@30 ne1 ICE | +70% / +39% / +49% ; 4.6 (+49%) | +70% / +36% / +47% ; 4.9 (+47%) | +72% / +38% / +49% ; 5.1 (+49%) | +69% / +36% / +44% ; 4.0 (+44%) | +63% / +21% / +30% ; 1.1 (+30%) | +65% / +23% / +31% ; 1.5 (+31%) | +70% / +29% / +43% ; 2.6 (+43%) | -39% / +40% / +33% ; -1.3 (+40%) | +24% / +40% / +34% ; 4.7 (+34%) |
| H L2SL A45 mult20@30 ne1 ICE (headline) | +73% / +38% / +41% ; 4.1 (+41%) | +73% / +34% / +41% ; 4.4 (+41%) | +75% / +36% / +45% ; 4.6 (+45%) | +71% / +35% / +37% ; 3.4 (+37%) | +65% / +19% / +20% ; 0.1 (+20%) | +67% / +20% / +24% ; 0.7 (+24%) | +73% / +27% / +31% ; 1.9 (+31%) | -40% / +40% / -7% ; -1.4 (+40%) | +25% / +29% / +11% ; 4.2 (+11%) |
| T1 UFP1 F3 icege10 ext10 trail20 | +55% / +37% / +65% ; -4.5 (+57%) | +54% / +37% / +65% ; -3.8 (+57%) | +54% / +38% / +65% ; -4.2 (+57%) | n/a | n/a | n/a | +48% / +30% / +64% ; -4.3 (+51%) | -42% / +0% / +29% ; -4.1 (+0%) | +24% / -6% / +30% ; -2.8 (+12%) |
| T2 UFP1 F3 icege10 ext30 trail20 | +55% / +37% / +65% ; -4.6 (+56%) | +54% / +37% / +65% ; -4.0 (+56%) | +54% / +38% / +65% ; -4.3 (+56%) | n/a | n/a | n/a | +48% / +30% / +64% ; -4.5 (+50%) | -42% / +0% / +29% ; -4.3 (+0%) | +24% / -6% / +20% ; -3.1 (+2%) |
| T3 UFP1 F5 d5q20 acc dl30 trail20 | +54% / +36% / +69% ; -4.9 (+53%) | +54% / +36% / +68% ; -4.6 (+53%) | +61% / +36% / +68% ; -4.2 (+54%) | n/a | n/a | n/a | +60% / +28% / +69% ; -4.9 (+47%) | -59% / +12% / +26% ; -4.0 (+12%) | +25% / +6% / +18% ; -3.2 (+6%) |
| T4 UFP1 F1 Wc80 Tb I1 trail20 | +48% / +32% / +62% ; -2.3 (+58%) | +48% / +33% / +63% ; -2.3 (+59%) | +47% / +33% / +64% ; -2.3 (+59%) | n/a | n/a | n/a | +51% / +25% / +62% ; -2.3 (+53%) | -66% / +18% / +40% ; -1.4 (+18%) | -1% / +21% / +27% ; -1.0 (+27%) |
| T5 UFP1 F1 Wc80 Tb I1 trail40 | +39% / +34% / +33% ; -2.8 (+33%) | +39% / +36% / +30% ; -2.9 (+30%) | +39% / +35% / +29% ; -2.6 (+29%) | n/a | n/a | n/a | +41% / +29% / +39% ; -3.1 (+39%) | -11% / +35% / +10% ; -0.8 (+35%) | +0% / +49% / +11% ; -1.8 (+11%) |
| C1 UFP5 dlt_a m0.5 | +46% / +42% / +38% ; -1.0 (+38%) | +50% / +46% / +49% ; 2.3 (+49%) | +50% / +45% / +50% ; 2.4 (+50%) | n/a | n/a | n/a | +48% / +36% / +42% ; -1.1 (+42%) | +2% / +33% / +25% ; 0.4 (+33%) | -1% / +49% / +19% ; -0.5 (+19%) |
| C2 UFP5 dlt_a m0.67 | +40% / +45% / +33% ; 0.9 (+33%) | +57% / +48% / +44% ; 3.9 (+44%) | +57% / +48% / +45% ; 4.0 (+45%) | n/a | n/a | n/a | +42% / +39% / +36% ; 1.2 (+36%) | -18% / +15% / +30% ; 1.0 (+15%) | -1% / +18% / +12% ; 1.9 (+12%) |
| L1 THL L6_a30_r3_w10 HM (live line) | +15% / +16% / -10% ; 1.0 (-10%) | +15% / +15% / -12% ; 0.8 (-12%) | +15% / +15% / -11% ; 0.8 (-11%) | +15% / +16% / -10% ; 0.9 (-10%) | +15% / +15% / -13% ; 0.7 (-13%) | +14% / +14% / -14% ; 0.4 (-14%) | +15% / +6% / -1% ; 0.8 (-1%) | -10% / +2% / +5% ; -0.0 (+2%) | +0% / +40% / -17% ; 1.2 (-17%) |
| L1 THL L6_a30_r3_w10 POOL6 | -25% / -7% / +26% ; -0.9 (+26%) | -39% / -9% / +11% ; -3.1 (+11%) | -31% / -9% / +11% ; -3.1 (+11%) | -28% / -5% / +23% ; -1.5 (+23%) | -40% / -11% / +8% ; -3.7 (+8%) | -42% / -15% / -3% ; -5.3 (-3%) | -21% / -29% / +19% ; -2.2 (+19%) | -228% / -12% / +2% ; -6.0 (-12%) | -1% / +34% / +25% ; 0.9 (+25%) |
| L2 THL L6_a25_r3_w10 HM | +11% / +18% / -8% ; 0.9 (-8%) | +11% / +18% / -10% ; 0.7 (-10%) | +11% / +17% / -10% ; 0.6 (-10%) | +11% / +18% / -9% ; 0.9 (-9%) | +11% / +17% / -11% ; 0.6 (-11%) | +10% / +16% / -13% ; 0.3 (-13%) | +11% / +9% / +0% ; 0.7 (+0%) | +3% / +5% / +1% ; 0.1 (+5%) | +0% / +41% / -14% ; 1.2 (-14%) |
| L2 THL L6_a25_r3_w10 POOL6 | -23% / +8% / +21% ; -1.0 (+21%) | -40% / -3% / +10% ; -3.6 (+10%) | -22% / -3% / +10% ; -3.3 (+10%) | -25% / +5% / +19% ; -1.7 (+19%) | -44% / -5% / +5% ; -4.1 (+5%) | -55% / -17% / -5% ; -5.9 (-5%) | +1% / -6% / +17% ; -2.2 (+17%) | -199% / +9% / -35% ; -7.1 (+9%) | +0% / +35% / +22% ; 0.5 (+22%) |
| L3 THL L6_a30_r2_w10 HM | +16% / +13% / -3% ; 0.8 (-3%) | +16% / +11% / -5% ; 0.6 (-5%) | +16% / +12% / -4% ; 0.7 (-4%) | +16% / +12% / -4% ; 0.7 (-4%) | +15% / +11% / -9% ; 0.2 (-9%) | +15% / +10% / -9% ; 0.1 (-9%) | +16% / +1% / +5% ; 0.5 (+5%) | -55% / +2% / +12% ; -0.0 (+2%) | +2% / +37% / -23% ; 1.2 (-23%) |
| L3 THL L6_a30_r2_w10 POOL6 | -10% / -59% / +43% ; -2.6 (+18%) | -22% / -78% / +38% ; -4.1 (+9%) | -25% / -76% / +41% ; -3.7 (+10%) | -17% / -70% / +39% ; -3.4 (+13%) | -45% / -109% / +22% ; -6.6 (-7%) | -54% / -102% / +17% ; -8.0 (-3%) | -12% / -82% / +37% ; -4.3 (+7%) | -102% / +30% / +9% ; -8.8 (+30%) | -44% / +24% / +54% ; -0.9 (+52%) |
| L4 THL L6_a30_r3_w30 HM | +20% / +7% / +2% ; 1.7 (+2%) | +20% / +5% / -0% ; 1.3 (-0%) | +20% / +5% / -0% ; 1.3 (-0%) | +20% / +6% / +1% ; 1.6 (+1%) | +20% / +5% / -2% ; 1.1 (-2%) | +20% / +4% / -5% ; 0.8 (-5%) | +21% / -5% / +8% ; 1.4 (+8%) | -50% / +1% / +7% ; 0.7 (+1%) | -0% / +40% / -26% ; 0.8 (-26%) |
| L4 THL L6_a30_r3_w30 POOL6 | -26% / +10% / +41% ; 0.4 (+41%) | -39% / +1% / +29% ; -2.7 (+29%) | -39% / +6% / +28% ; -2.2 (+28%) | -28% / +8% / +37% ; -0.3 (+37%) | -47% / -4% / +26% ; -4.1 (+26%) | -77% / -17% / +10% ; -6.1 (+10%) | -24% / -4% / +34% ; -1.1 (+34%) | -143% / +28% / +37% ; -3.8 (+28%) | -16% / +26% / +50% ; 0.2 (+50%) |
| L5 THL L6_a15_r3_w30 HM | +15% / +13% / -7% ; 0.2 (-7%) | +14% / +11% / -11% ; -0.2 (-11%) | +14% / +11% / -10% ; -0.2 (-10%) | +15% / +12% / -8% ; 0.0 (-8%) | +14% / +11% / -13% ; -0.5 (-13%) | +13% / +10% / -16% ; -0.9 (-16%) | +15% / +3% / +0% ; -0.1 (+0%) | -52% / +10% / +13% ; -0.2 (+10%) | -1% / +33% / -31% ; 0.3 (-31%) |
| L5 THL L6_a15_r3_w30 POOL6 | -46% / -146% / +59% ; -6.5 (-26%) | -74% / -196% / +42% ; -10.2 (-51%) | -86% / -185% / +44% ; -10.0 (-46%) | -48% / -153% / +54% ; -7.3 (-30%) | -77% / -201% / +36% ; -11.2 (-54%) | -129% / -239% / +16% ; -14.4 (-73%) | -13% / -168% / +54% ; -8.0 (-38%) | -196% / -30% / +39% ; -11.1 (-30%) | -52% / +2% / +62% ; -3.3 (+38%) |
| U1 L2SL A30 mult20@5 ne0 none | +31% / +33% / +36% ; -2.6 (+36%) | +27% / +31% / +34% ; -2.5 (+34%) | +25% / +21% / +37% ; -2.4 (+37%) | +29% / +21% / +30% ; -3.7 (+30%) | +7% / -19% / +8% ; -8.2 (+8%) | +0% / -27% / +12% ; -7.8 (+12%) | +28% / +20% / +24% ; -5.0 (+24%) | -225% / +33% / -4% ; -11.1 (+33%) | +22% / +25% / +30% ; -1.7 (+30%) |
| U2 L2SL A30 mult20@5 ne1 none | +26% / +6% / +33% ; -0.4 (+33%) | +22% / +2% / +29% ; -0.2 (+29%) | +20% / +4% / +33% ; 0.0 (+33%) | +24% / +2% / +26% ; -1.4 (+26%) | +8% / -11% / +5% ; -5.5 (+5%) | +2% / -15% / +5% ; -5.2 (+5%) | +23% / -11% / +23% ; -2.7 (+23%) | -251% / +24% / +8% ; -10.1 (+24%) | +22% / +42% / +23% ; 0.7 (+23%) |
| U3 L2SL A30 mult100@5 ne0 none | +10% / +13% / +38% ; -0.3 (+38%) | +11% / +11% / +37% ; -0.6 (+37%) | +10% / +9% / +40% ; -0.0 (+40%) | +9% / +16% / +35% ; -1.0 (+35%) | +6% / +12% / +25% ; -3.5 (+25%) | +5% / +1% / +28% ; -3.1 (+28%) | +8% / -2% / +35% ; -1.5 (+35%) | -33% / +2% / +0% ; -7.1 (+2%) | -18% / -21% / +34% ; -2.0 (+15%) |
| U4 L2SL A30 mult100@5 ne1 none | +18% / +16% / +5% ; -0.4 (+5%) | +18% / +15% / +4% ; -0.4 (+4%) | +17% / +16% / +8% ; -0.0 (+8%) | +17% / +12% / +3% ; -0.9 (+3%) | +14% / +9% / -5% ; -2.7 (-5%) | +13% / +8% / -1% ; -2.2 (-1%) | +17% / +4% / -3% ; -1.2 (-3%) | -44% / -5% / -46% ; -7.1 (-5%) | -20% / -7% / +31% ; -0.5 (+22%) |
| R1 arm-only A30 (no L2) | +26% / +42% / +49% ; -2.9 (+49%) | +27% / +40% / +49% ; -2.6 (+49%) | +26% / +40% / +50% ; -2.5 (+50%) | +24% / +40% / +44% ; -3.9 (+44%) | -1% / -2% / +21% ; -8.4 (+21%) | -5% / -25% / +23% ; -8.2 (+23%) | +23% / +32% / +39% ; -5.3 (+39%) | -219% / +33% / -18% ; -11.3 (+33%) | +23% / -21% / +31% ; -2.1 (+23%) |
| R2 arm-only A45 (no L2) | +33% / +19% / +48% ; 3.5 (+48%) | +30% / +17% / +48% ; 3.6 (+48%) | +35% / +21% / +51% ; 3.8 (+51%) | +31% / +16% / +44% ; 2.9 (+44%) | +28% / +5% / +25% ; -0.2 (+25%) | +31% / +6% / +29% ; -0.1 (+29%) | +31% / +4% / +39% ; 1.3 (+39%) | -13% / +36% / +4% ; -2.4 (+36%) | -9% / +28% / +14% ; 3.0 (+14%) |

Engine-kept trades (as-is 11,347; as-is+12R 7878): newly kept / dropped when the rule is added: S1 1322/132; S2 1323/122; S3 1326/126; S4 603/90; S5 1573/171; H 1603/191; T1 1260/199; T2 1278/200; T3 1217/207; T4 619/116; T5 438/115; C1 666/201; C2 476/129; L1HM 112/0; L1POOL6 1296/242; L2HM 113/3; L2POOL6 1446/243; L3HM 144/9; L3POOL6 1910/304; L4HM 128/5; L4POOL6 1629/276; L5HM 155/4; L5POOL6 2083/193; U1 2379/234; U2 2325/237; U3 1453/198; U4 1182/167; R1 2382/237; R2 1634/222.

Is the data available at the trigger second? The L2 features are built on the 10-s book table (state at the END of the 10-s bin; windows end at the decision second), the fill in the base case is the 1-s close of that same second, i.e. zero latency; +1 s / +3 s are the realistic cases. For the L2 cells the live feed must supply, at the trigger second, the features of section 8: D6 as coded does not compute them (D6 computes pct, imb5, imb10, delta60, curDepthRel, pulled_sup10 and the price-path set), so the rule cannot be evaluated live today.

### 6b. Where the mean gain comes from: same per-trade pts change, exit time NOT moved (the lock engine sees the old exit second)

| cell | exact (exit moved): ALL mean / L6M cut / PRE cut / X' cut | pts only (exit unchanged): ALL mean / L6M cut / PRE cut / X' cut |
|---|---|---|
| H L2SL A45 mult20@30 ne1 ICE (headline) | 4.1 / +73% / +38% / +41% | 0.4 / +65% / +29% / +22% |
| S1 L2SL A45 z10>=2 ne0 ICE | 3.1 / +61% / +35% / +31% | 0.9 / +58% / +32% / +26% |
| S5 L2SL A45 mult100@30 ne1 ICE | 4.6 / +70% / +39% / +49% | 1.1 / +63% / +27% / +32% |
| S4 L2SL A30 z5>=3 none | 0.1 / +26% / +30% / +20% | -0.9 / +26% / +29% / +20% |
| R2 arm-only A45 (no L2) | 3.5 / +33% / +19% / +48% | 0.0 / +29% / +21% / +29% |
| R1 arm-only A30 (no L2) | -2.9 / +26% / +42% / +49% | -7.6 / +26% / +19% / +33% |
| L1 THL L6_a30_r3_w10 HM (live line) | 1.0 / +15% / +16% / -10% | 0.7 / +15% / +15% / -12% |
| L1 THL L6_a30_r3_w10 POOL6 | -0.9 / -25% / -7% / +26% | -3.8 / -41% / -5% / +8% |
| T1 UFP1 F3 icege10 ext10 trail20 | -4.5 / +55% / +37% / +65% | -9.0 / +49% / +7% / +57% |
| C1 UFP5 dlt_a m0.5 | -1.0 / +46% / +42% / +38% | -3.5 / +40% / +36% / +27% |

For the A=45 cells the mean gain (+3.5 to +4.6k/wk exact) falls to about zero when the exit second is not moved; a maxDD cut of 20-30% in PRE and X' remains, which is what a 25% tighter stop does mechanically. The -45 pt cut therefore buys a smaller loss per losing trade (and the busy-filter/lock release that follows), at constant trade-level expectancy.

## 7. The target-forfeit side (the trades the cut closes that would have recovered)

Per cell, ALL window, engine-taken fired trades: forfeited = cut worse than hold (delta < 0); 'hit target' = of the forfeited, trades whose hold outcome was a target (hold pts > 0); $ at live sizes (first-order: pts x as-is final size x $/pt) saved / forfeited / net; mean pts saved and forfeited per trade.

| cell | fired | forfeited (% of fired) | of which hold would hit the target | $k saved | $k forfeited | net $k | mean pts saved / forfeited | L6M: fired / forfeited / net $k |
|---|---|---|---|---|---|---|---|---|
| S1 L2SL A45 z10>=2 ne0 ICE | 2481 | 252 (10%) | 217 | 1892.2 | -1743.2 | 149.0 | +10.9 / -91.6 | 518 / 51 / 11.7 |
| S2 L2SL A45 z10>=2 ne0 ICESWP | 2446 | 249 (10%) | 213 | 1850.9 | -1707.5 | 143.4 | +10.8 / -91.1 | 504 / 50 / 4.9 |
| S3 L2SL A45 z10>=2 ne0 K2 | 2462 | 253 (10%) | 217 | 1862.3 | -1738.9 | 123.4 | +10.8 / -91.3 | 509 / 52 / -0.8 |
| S4 L2SL A30 z5>=3 none | 1025 | 202 (20%) | 160 | 1129.8 | -1087.5 | 42.3 | +18.0 / -75.1 | 155 / 32 / -30.5 |
| S5 L2SL A45 mult100@30 ne1 ICE | 4759 | 547 (11%) | 477 | 3532.2 | -3490.5 | 41.6 | +11.7 / -92.3 | 992 / 124 / -94.6 |
| H L2SL A45 mult20@30 ne1 ICE (headline) | 5157 | 619 (12%) | 541 | 4039.9 | -4072.1 | -32.2 | +12.2 / -92.6 | 1042 / 128 / -62.8 |
| T1 UFP1 F3 icege10 ext10 trail20 | 3455 | 2542 (74%) | 2542 | 5301.0 | -6074.4 | -773.3 | +79.5 / -32.4 | 701 / 537 / -261.1 |
| T2 UFP1 F3 icege10 ext30 trail20 | 3463 | 2549 (74%) | 2549 | 5307.5 | -6095.2 | -787.7 | +79.5 / -32.4 | 702 / 538 / -263.7 |
| T3 UFP1 F5 d5q20 acc dl30 trail20 | 3307 | 2405 (73%) | 2405 | 5155.2 | -5875.2 | -720.0 | +78.4 / -33.0 | 662 / 502 / -228.9 |
| T4 UFP1 F1 Wc80 Tb I1 trail20 | 1647 | 1155 (70%) | 1155 | 2640.4 | -3074.0 | -433.6 | +71.1 / -34.3 | 262 / 193 / -124.8 |
| T5 UFP1 F1 Wc80 Tb I1 trail40 | 1116 | 653 (59%) | 653 | 2144.5 | -2532.6 | -388.1 | +61.3 / -48.9 | 188 / 121 / -145.0 |
| C1 UFP5 dlt_a m0.5 | 2249 | 1686 (75%) | 1686 | 3299.7 | -3469.4 | -169.7 | +83.5 / -29.9 | 500 / 394 / -210.4 |
| C2 UFP5 dlt_a m0.67 | 2030 | 1679 (83%) | 1679 | 2265.1 | -2287.4 | -22.3 | +90.3 / -19.8 | 451 / 394 / -133.0 |
| L1 THL L6_a30_r3_w10 HM (live line) | 592 | 123 (21%) | 105 | 631.1 | -590.7 | 40.4 | +22.0 / -79.1 | 110 / 24 / 9.5 |
| L1 THL L6_a30_r3_w10 POOL6 | 3473 | 798 (23%) | 721 | 4374.2 | -4843.7 | -469.4 | +22.6 / -84.3 | 674 / 158 / -104.2 |
| L2 THL L6_a25_r3_w10 HM | 644 | 152 (24%) | 134 | 767.6 | -729.2 | 38.4 | +26.0 / -78.1 | 125 / 31 / 0.0 |
| L2 THL L6_a25_r3_w10 POOL6 | 3814 | 995 (26%) | 918 | 5417.5 | -5961.0 | -543.5 | +26.4 / -82.0 | 736 / 195 / -98.4 |
| L3 THL L6_a30_r2_w10 HM | 932 | 257 (28%) | 235 | 1394.9 | -1387.3 | 7.6 | +30.8 / -80.4 | 177 / 48 / 17.6 |
| L3 THL L6_a30_r2_w10 POOL6 | 5298 | 1526 (29%) | 1417 | 8855.6 | -9422.8 | -567.2 | +30.8 / -82.2 | 1030 / 313 / -294.5 |
| L4 THL L6_a30_r3_w30 HM | 783 | 170 (22%) | 149 | 1021.8 | -906.9 | 114.9 | +24.9 / -80.4 | 147 / 34 / 5.5 |
| L4 THL L6_a30_r3_w30 POOL6 | 4471 | 1079 (24%) | 979 | 6467.0 | -6746.0 | -279.1 | +25.0 / -83.7 | 848 / 217 / -196.0 |
| L5 THL L6_a15_r3_w30 HM | 998 | 339 (34%) | 322 | 1608.8 | -1675.6 | -66.8 | +36.9 / -74.0 | 202 / 74 / -59.1 |
| L5 THL L6_a15_r3_w30 POOL6 | 5710 | 2041 (36%) | 1954 | 10441.9 | -11427.0 | -985.1 | +37.5 / -74.6 | 1116 / 416 / -413.7 |
| U1 L2SL A30 mult20@5 ne0 none | 6422 | 1643 (26%) | 1518 | 9275.3 | -9705.9 | -430.6 | +26.7 / -83.0 | 1314 / 351 / -161.6 |
| U2 L2SL A30 mult20@5 ne1 none | 6211 | 1496 (24%) | 1375 | 8586.0 | -8798.1 | -212.1 | +25.2 / -83.4 | 1284 / 325 / -125.3 |
| U3 L2SL A30 mult100@5 ne0 none | 3933 | 889 (23%) | 801 | 4709.5 | -4898.4 | -188.9 | +22.6 / -82.7 | 861 / 209 / -150.1 |
| U4 L2SL A30 mult100@5 ne1 none | 3221 | 654 (20%) | 596 | 3529.6 | -3574.7 | -45.1 | +20.6 / -84.3 | 724 / 156 / -92.2 |
| R1 arm-only A30 (no L2) | 6522 | 1725 (26%) | 1599 | 9737.0 | -10216.6 | -479.6 | +27.8 / -82.5 | 1330 / 365 / -194.9 |
| R2 arm-only A45 (no L2) | 5283 | 673 (13%) | 593 | 4409.3 | -4468.7 | -59.4 | +13.0 / -92.7 | 1072 / 142 / -78.1 |

For H the saved and forfeited dollars nearly cancel: 4538 of 5157 closed trades would have stopped out or lost more (saving +12.2 pts each, 4039.9k) and 619 (12%) would have recovered (losing -92.6 pts each, -4072.1k), 541 of them to the target; net -32.2k over 149 weeks. The cut is a risk-for-reward trade at about constant trade-level expectancy; the engine P&L change comes from the extra trades it admits (section 6).

## 8. Can D6 / D7 see it? The exact feature gap, and the D6 mapping (THP L2 policy line = NEEDS)

D6 as coded computes (DS3_THL2_NEEDS.md): pct (adverse as a fraction of the target), imb5, imb10, delta60, curDepthRel (rel_tot8), pulled_sup10 (size cancelled on the supporting side, levels 1-10, last 10 s) and the price-path set (secs_ext, recov, eff120, MAE...). D7 (group-12 filters, DS3_D7_FILTERS) adds ES-tape and calendar filters, no book-depth features. The L2 cells need, at the trigger second (all windows end at the decision second, side = supporting side of the trade):

| feature needed | definition | in D6? | cells |
|---|---|---|---|
| pulled_sup5 / pulled_sup30 | size cancelled over supporting-side levels 1-10 in the last 5 / 30 s (window other than D6's 10 s) | NO | S4, U1-U4 (5 s); S5, H (30 s) |
| pulled z-score | log1p(pulled_supW) standardised against the same 15-minute ET bucket over PRIOR calendar months (min 2,000 samples) | NO | S1, S2, S3, S4 |
| medOwnLevel / pulledShare | median own-side L1..L10 size at the second; pulled / (pulled + own L1..L10 size) | NO | S5, H, U1-U4 (medOwnLevel) |
| newAdvExt5/10/30 | 1 if the 1-s adverse excursion in the last w s set a new running MAE maximum of the trade | NO (D6 keeps MAE but not the time of the last extreme) | H, S5, U2, U4 |
| icebergAgainst | size traded at the best AHEAD level in 10 s >= 10 x displayed best size, refilled (l2feat iceberg_flag_ahead) | NO | S1, S2, S5, H |
| sweepAgainst10 | count of trade-driven touch clears (>= 2 levels) by the adverse aggressor in the last 10 s | NO | S2 |
| ownDepth10Rel | own-side L1..L10 size / median of the same quantity at the same ET hour over the prior 20 label days | NO | S3 (K2 combo) |
| imb10 <= -0.3 | | YES | S3 (part of K2) |
| UFP trails: icebergAhead10 >= 10 (+ <= 10/30 s since MFE); wall ahead cum_ahead10_rel >= q80; tape turn delta_acc / delta30 / ofi5_30; intensity z; 60-s change of imb5 | | NO (D6 has imb5 and delta60 only) | T1-T5 |
| UFP5 target chooser: delta60 sided <= q30 at entry | feature present; the ACTION 'target = m x nominal at entry' is not in the THP vocabulary (take / cut / tighten) | feature YES, action NO | C1, C2 |
| price-only | pct, secs_ext, recov, eff120 | YES | L1-L5 (THL L6 family), R1, R2 |

Latency / cadence: the book table behind every L2 cell is the 10-s mbp-10 bin; the base-case fill is the 1-s close of the trigger second (zero latency). Section 6 gives +1 s and +3 s. The data are causal (windows end at the decision second) but the iceberg and sweep flags are computed from the mbp-10 print table and the z-score needs a per-bucket table maintained from prior months, which D6 does not carry.

**Policy lines (Shadow / NEEDS only; none activated; format of THP_POLICY.txt; pct = adverse points / 60-pt target, so -45 pts = -0.75 and -30 pts = -0.5):**

```
# NEEDS (L2CUT H, Shadow log only)  : loss * * pct <= -0.750 pulled_sup30 >= 20*medOwnLevel newAdvExt30 == 1 icebergAgainst == 1 cut
# NEEDS (L2CUT S5, Shadow log only) : loss * * pct <= -0.750 pulled_sup30 >= 100*medOwnLevel newAdvExt30 == 1 icebergAgainst == 1 cut
# NEEDS (L2CUT S1, Shadow log only) : loss * * pct <= -0.750 pulledZ10 >= 2 icebergAgainst == 1 cut      # S2 adds sweepAgainst10 >= 1; S3 = 2 of {icebergAgainst, sweepAgainst10>=1, ownDepth10Rel<=0.5, imb10<=-0.3}
# NEEDS (L2CUT S4, Shadow log only) : loss * * pct <= -0.500 pulledZ5 >= 3 cut
# NEEDS (L2CUT T1-T5)               : profit trails need icebergAhead10 / wall-ahead / tape features; C1, C2 need a 'target multiple' action: no D6 line can express them
# LIVE as coded (not an L2 rule)    : loss H6 * pct <= -0.5 secs_ext >= 10 recov <= 4 eff120 < 0.35 cut    # = THL L6_a30_r3_w10 on HM, unchanged by this test
# price-only reference (R2)         : loss * * pct <= -0.75 cut   # a -45 pt stop tightening, D6-feasible today, NOT activated: its engine gain is the lock channel
```

## 9. Gate matrix (AS-IS frame, exact engine, base case; G1-G8 as frozen in the prereg; every failed gate named)

| cell | G1 L6M cut>=20% & mean in MDE | G2 PRE and X' agree | G3 placebo >= 95% (L6M, PRE, X') | G4 LOEO (5 singles + all-five + L6M worst week) | G5 bootstrap CI excludes 0 (L6M, PRE, X') | G6 +3 s, cost 1.28, base stop 1.28 | G7 equal-risk mean >= -MDE | G8 family-wise p <= 0.05 | user-def | decisive |
|---|---|---|---|---|---|---|---|---|---|---|
| S1 L2SL A45 z10>=2 ne0 ICE | pass | pass | FAIL (A:PRE=91%, A:X=77%, M:PRE=88%, M:X=39%, S:PRE=65%, T:PRE=93%, T:X=86%) | FAIL | FAIL | pass | pass | pass (p 0.010) | YES | NO |
| S2 L2SL A45 z10>=2 ne0 ICESWP | pass | pass | FAIL (A:PRE=92%, A:X=80%, M:PRE=88%, M:X=42%) | FAIL | FAIL | pass | pass | pass (p 0.010) | YES | NO |
| S3 L2SL A45 z10>=2 ne0 K2 | pass | pass | FAIL (A:PRE=94%, A:X=84%, M:PRE=85%, M:X=43%) | FAIL | FAIL | pass | pass | pass (p 0.010) | YES | NO |
| S4 L2SL A30 z5>=3 none | pass | pass | FAIL (A:L6M=79%, M:L6M=60%, M:PRE=86%, M:X=60%, S:L6M=3%, S:PRE=15%, S:X=5%, T:L6M=84%, T:X=92%) | FAIL | FAIL | FAIL | pass | pass (p 0.030) | YES | NO |
| S5 L2SL A45 mult100@30 ne1 ICE | pass | pass | FAIL (A:PRE=74%, A:X=86%, M:PRE=74%, M:X=43%, S:PRE=81%, T:PRE=93%) | FAIL | FAIL | pass | pass | pass (p 0.040) | YES | NO |
| H L2SL A45 mult20@30 ne1 ICE (headline) | pass | pass | FAIL (A:PRE=62%, A:X=30%, M:PRE=69%, M:X=1%, S:PRE=94%) | FAIL | FAIL | pass | pass | FAIL (p 0.060) | YES | NO |
| T1 UFP1 F3 icege10 ext10 trail20 | pass | pass | pass | FAIL | FAIL | pass | pass | FAIL (p 0.060) | YES | NO |
| T2 UFP1 F3 icege10 ext30 trail20 | pass | pass | pass | FAIL | FAIL | pass | pass | FAIL (p 0.060) | YES | NO |
| T3 UFP1 F5 d5q20 acc dl30 trail20 | pass | pass | pass | FAIL | FAIL | pass | pass | FAIL (p 0.065) | YES | NO |
| T4 UFP1 F1 Wc80 Tb I1 trail20 | pass | pass | pass | FAIL | FAIL | pass | pass | FAIL (p 0.065) | YES | NO |
| T5 UFP1 F1 Wc80 Tb I1 trail40 | pass | pass | pass | FAIL | FAIL | pass | pass | pass (p 0.035) | YES | NO |
| C1 UFP5 dlt_a m0.5 | pass | pass | FAIL (R:X=68%) | FAIL | FAIL | pass | pass | pass (p 0.045) | YES | NO |
| C2 UFP5 dlt_a m0.67 | pass | pass | FAIL (R:X=56%) | FAIL | FAIL | pass | pass | pass (p 0.015) | YES | NO |
| L1 THL L6_a30_r3_w10 HM (live line) | FAIL | FAIL | FAIL (A:L6M=85%, A:X=55%, M:L6M=51%, M:PRE=84%, M:X=4%, T:L6M=68%, T:X=48%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| L1 THL L6_a30_r3_w10 POOL6 | FAIL | FAIL | FAIL (A:L6M=39%, A:PRE=49%, M:L6M=9%, M:PRE=1%, M:X=53%, T:L6M=56%, T:PRE=59%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| L2 THL L6_a25_r3_w10 HM | FAIL | FAIL | FAIL (A:L6M=48%, A:X=74%, M:L6M=23%, M:PRE=87%, M:X=12%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| L2 THL L6_a25_r3_w10 POOL6 | FAIL | FAIL | FAIL (A:L6M=29%, A:PRE=90%, M:L6M=3%, M:PRE=18%, M:X=19%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| L3 THL L6_a30_r2_w10 HM | FAIL | FAIL | FAIL (A:L6M=47%, A:PRE=73%, A:X=3%, M:L6M=54%, M:PRE=72%, M:X=2%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| L3 THL L6_a30_r2_w10 POOL6 | FAIL | FAIL | FAIL (A:L6M=11%, A:PRE=0%, A:X=49%, M:L6M=10%, M:PRE=0%, M:X=43%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| L4 THL L6_a30_r3_w30 HM | pass | FAIL | FAIL (A:PRE=65%, A:X=94%, M:L6M=84%, M:PRE=31%, M:X=37%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| L4 THL L6_a30_r3_w30 POOL6 | FAIL | FAIL | FAIL (A:L6M=72%, A:PRE=71%, M:L6M=12%, M:PRE=6%, M:X=57%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| L5 THL L6_a15_r3_w30 HM | FAIL | FAIL | FAIL (A:L6M=57%, A:PRE=78%, M:L6M=42%, M:PRE=23%, M:X=63%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| L5 THL L6_a15_r3_w30 POOL6 | FAIL | FAIL | FAIL (A:L6M=94%, A:PRE=78%, M:L6M=12%, M:PRE=0%, M:X=88%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| U1 L2SL A30 mult20@5 ne0 none | pass | pass | FAIL (A:L6M=85%, A:PRE=39%, A:X=66%, M:L6M=22%, M:PRE=3%, M:X=0%) | FAIL | FAIL | pass | pass | FAIL | YES | NO |
| U2 L2SL A30 mult20@5 ne1 none | pass | FAIL | FAIL (A:L6M=74%, A:PRE=1%, A:X=75%, M:L6M=13%, M:PRE=0%, M:X=1%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| U3 L2SL A30 mult100@5 ne0 none | FAIL | FAIL | FAIL (A:L6M=41%, A:PRE=56%, M:L6M=13%, M:PRE=7%, M:X=74%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| U4 L2SL A30 mult100@5 ne1 none | FAIL | FAIL | FAIL (A:L6M=38%, A:PRE=50%, A:X=68%, M:L6M=18%, M:PRE=18%, M:X=14%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |
| R1 arm-only A30 (no L2) | pass | pass | FAIL (A:L6M=0%, A:X=0%, M:L6M=0%, M:X=0%) | FAIL | FAIL | pass | pass | FAIL | YES | NO |
| R2 arm-only A45 (no L2) | pass | FAIL | FAIL (A:PRE=0%, A:X=0%, M:PRE=0%, M:X=0%) | FAIL | FAIL | FAIL | pass | FAIL | no | NO |

Cells failing each gate (of 27 candidates; R1/R2 excluded: their placebo draws are the real cell by construction): G1 11, G2 13, G3 22, G4 27, G5 27, G6 14, G7 0, G8 19. G3 'not run' counts as not passed. G9 (live-feasible in D6) is column 'live-feasible' on page 1 and section 8: L2 cells N, price-only cells Y.

## 10. Shadow monitor and STOP rule (nothing is activated; the decisive label is NO, so this is a record, not a promotion)

**What is logged (D6 / NT8 side).** For every trigger of the Shadow line (a trade at or beyond the arm, and the L2 condition true at a 10-s decision second): book, trade id, trigger second, side, planned lots, MAE so far, every feature of the line, the market mid and the touch at +0, +1, +3 s, and later the realised hold outcome of the same trade (its own stop / target / time exit). Nothing is sent to the market. L2 cells cannot be logged by D6 as coded (section 8); the logger needs the NEEDS features first. For R2 (price-only) the log is possible today.

**STOP rule.** Evaluate at the first checkpoint with >= 200 logged triggers and at least 8 calendar weeks (H: about 35 triggers a week on the six live books, so 8 weeks; S1-S3: about 17 a week, 12 weeks), then every 4 weeks. STOP the line (retire it, write it to DEAD_CELLS) if ANY of: (a) the mean hypothetical net per trigger at +3 s (cut at the +3 s mid less 0.995 pt, minus the hold outcome, in pts, day-cluster bootstrap) has a point estimate <= +0.5 pt (the in-sample first-order edge is -0.4 to +0.5 pt per trigger, i.e. nil); (b) the share of triggers whose hold outcome was a target exceeds 12% (the in-sample rate: forfeits are what a cut costs) in two consecutive 4-week blocks; (c) an engine replay of the logged exits through the one-convention lock engine (monthly) does not show at least 40% of the in-sample extra-kept-trade gain (H: +1,603 trades / 3.2 years = about 10 per week) or shows a negative 8-week P&L change; (d) the feature feed misses > 2% of triggers (cannot be evaluated). Re-test with the same code (`code/l2cut/`) when the checkpoint is reached. No lot, stop or risk limit changes on any outcome of this log.

## 11. Integrity and what is not claimed

- **Consistency, not holdout.** PRE and X' were A1's selection windows; A1 had already read L3M/L6M/HOLD of the same exact series. The numbers here reproduce A1's exact figures (H: L6M 73.2%, PRE 37.6%, X' 41.5%, HOLD 13.2%, mean +4.1k/wk ALL, MDE 5.7k ALL; the brief's 'MDE 5.7k' is the ALL-window MDE, the L6M MDE is 16.6k). One recent look: no cell was re-tuned after the statistics.
- **Frozen cells.** The top-5 L2SL cells by A1's family-wise p are three nearly identical z10>=2 ICE-family cells (S1-S3), one A=30 z5>=3 cell (S4) and S5; the headline cell H (p 0.060) is listed beside them as the cell A1 named strongest by maxDD. S1-S3 differ only in the lead condition and carry almost the same fires.
- **Placebos run through the engine.** The first-order trade-level null (A1's) cannot be used here: it ignores the lock engine, where the A=45 gain lives (first-order mean about 0 vs exact +3.5 to +4.6k/wk). The engine-exact null keeps the lock channel in the null. The PL-T nearest-row rule picks the 10-s decision row closest in time-in-trade to a random real fire time of the stratum, among rows that satisfy the arm. The UFP reassignment placebo (R) keeps the real delta and the fraction of the hold elapsed; it does not re-run the trail rule on other trades (the trail rule is not stored), so it tests matched-volume luck, not the rule's mechanism.
- **Cost/latency model.** Delay and cost variants shift the exit by the 1-s path move and change the exit second; they do not model queue position, partial fills or the 10-s feature delay. The A12 frame (12R lock, D6 as coded) and the composite are informational and do not enter the gates.
- **THL L6 is a price-path rule.** 'Your live L2 loss cut' is not an L2 rule (conditions: adverse points, secs_ext, recov, eff120). The live line is HM only; POOL6 is A1's pooled scope and is shown because A1 scored it.
- **Reading of A1's UF-PROFIT labels.** The 5 UFP1 trails and 2 UFP5 target-chooser cells meet the RISK-KEEP drawdown definition (they shrink exposure; L6M mean -5 to -7.5k/wk within a 11-13k MDE) while their means are negative or nil; they are volume cuts, which is what the user-def passes measure. They fail the same later gates.
- No PASS is claimed. DEAD_CELLS +rows (program L2CUT, append only). Shadow / NEEDS only.
