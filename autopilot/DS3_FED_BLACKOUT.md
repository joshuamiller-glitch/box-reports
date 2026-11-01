# DS3_FED_BLACKOUT - the decisive test of the one L6M RISK-KEEP cell (skip all signals on Fed-blackout days). F2, 2026-11-01. Frozen definition, post-hoc lead, SHADOW ONLY, no PASS

Prereg `l2vast/ds3/prereg/FEDBLACKOUT_prereg.md` sha256 `4327d5c7cbfd74a144c1add733515b0481ab3702f0fd754e9d407d358dfed3b3` + ADDENDUM 1 `FEDBLACKOUT_prereg_ADDENDUM1.md` sha256 `954df3abc72e0a0acf7e92eb88e80b6cbe77a9a8c028de2fdcb72de1b74a2f1c`, both in DECISIONS.md before any risk statistic. dead_lookup first: frozen cell = EXACT F1DD; the other variants NOT FOUND (statement-day-only overlaps EINT2/NTE1 FOMC-day mean cells); 16 rows appended after scoring (program F2FB, tier PRICED; DEAD_CELLS never rebuilt). Code `l2vast/ds3/code/fedblackout/`, results `l2vast/ds3/out/fedblackout/`. Masks capped 20260206; no post-cap file opened; the FOMC calendar file was read with every row dated after the cap discarded at read time. 3 workers, OMP/MKL 1. **Integrity:** the cell was chosen by F1 after PRE+X' selection and one look at L3M/L6M/HOLD/ALL, so PRE/X' are in-sample for the choice and this is a consistency test, not a holdout. The L6M maxDD is one week.

## Verdict (first)

**RISK-KEEP by the user's definition (L6M maxDD cut >= 20%, mean inside MDE): YES, as F1 found (V1c: 22.9k -> 10.1k, -56%, mean -5.6k/wk vs MDE 14.6k). RISK-KEEP as a decisive hedge: NO.** Gates for the D6-implementable cell V1c (full flat on 185 calendar-complete days) / for F1's exact mask V1: G1 user definition pass/pass; G2 PRE and X' agree (cut >= 20% each, mean inside MDE) pass/pass; G3 beats the matched-block placebo at 95% in L6M, PRE, X' and ALL FAIL/FAIL (ranks 99% / 63% / 68% / 66%); G4 survives leave-one-episode-out (single removals and all five) FAIL/FAIL; G5 bootstrap CI of the maxDD change excludes zero in PRE and X' FAIL/FAIL; G6 frame consistency (as-is PRE not deeper; 12R-lock composite PRE and X' cut >= 10%) FAIL/FAIL (as-is PRE -14%; 12R lock PRE 0%, X' +3%). Failed gates for the decisive label: G3, G4, G5, G6. Shadow only; a policy line and NT8 spec are in section 9 for a paper log, not as a recommendation.

What the test shows in four lines. (i) Each window's maxDD cut is carried by ONE or TWO FOMC blocks (leave-one-meeting-out: PRE and ALL by the Sep-2024 block alone, X' by the Apr-May 2023 block alone, L6M by the Oct-2025 and Jan-2026 blocks). (ii) A random calendar of 23 eight-day blocks with the same weekday, era and signal volume cuts PRE by 16% on average and by 44% at the 95th percentile; the real 26% ranks 63rd percentile; 20% of such calendars pass F1's PRE+X' carry rule. (iii) The L6M cut is real against the placebo (rank 99%, p 0.013) but it is one week, and only 2.9% of placebo calendars cut L6M by 20%: after the family correction (8 variants) p = 0.10. (iv) Blackout days are not different days: signal mean $315 vs $316 per signal, hit rate 53.9% vs 54.0%, daily P&L SD 27.5k vs 26.1k; there is no mechanism visible beyond the volume cut (24% of live signals).

## Page 1 - the table (composite = Sunday composite at live lots, vs itself without the rule; maxDD $k before>after (cut) [95% stationary-bootstrap CI of the change, block 4, 4,000 resamples]; worst-20 $k (w5 = worst-5 in L3M/L6M/HOLD); mean change $k/wk (MDE) [CI]; equal-risk mean change $k/wk (MDE) at lot scale c; placebo rank = share of 1,000 matched-block draws (same volume +-10%, weekday, era, unrestricted position) with a smaller cut than the real one, p in brackets; recent first)

| table | window | maxDD before>after (cut) [CI of change] | worst-20 | mean (MDE) [CI] | equal-risk mean (MDE) | matched-block placebo rank | LOEO survives | RISK-KEEP |
|---|---|---|---|---|---|---|---|---|
| composite V1c (full flat 185 d) | L3M | 21.4>10.1 (+53%) [-21.4, 0.0] | -40>-21 (w5) | +1.3 (18.3) [-7.9, +11.0] | -0.7 (22.0) c=1.17 | n/a |  |  |
| composite V1c (full flat 185 d) | L6M | 22.9>10.1 (+56%) [-34.2, 0.0] | -61>-17 (w5) | -5.6 (14.6) [-14.5, +3.0] | -6.0 (15.8) c=1.17 | 99% (p 0.013) |  |  |
| composite V1c (full flat 185 d) | HOLD | 97.0>68.0 (+30%) [-67.1, 0.0] | -189>-85 (w5) | -4.8 (15.2) [-13.2, +3.7] | -4.7 (15.8) c=1.17 | n/a |  |  |
| composite V1c (full flat 185 d) | PRE | 241.2>179.6 (+26%) [-128.8, 67.6] | -875>-733 (w20) | -7.6 (10.4) [-15.1, -0.8] | -8.2 (10.8) c=1.17 | 63% (p 0.372) |  |  |
| composite V1c (full flat 185 d) | X' | 120.5>81.7 (+32%) [-95.7, 50.6] | -420>-365 (w20) | -0.8 (7.3) [-5.6, +3.9] | -0.5 (7.7) c=1.17 | 68% (p 0.324) |  |  |
| composite V1c (full flat 185 d) | ALL | 241.2>179.6 (+26%) [-126.4, 53.5] | -1098>-942 (w20) | -5.1 (6.5) [-9.7, -0.7] | -5.3 (6.8) c=1.17 | 66% (p 0.345) | 5/6 removals; all-five NO (-3%) | user def YES / decisive NO |
| composite V1 (F1 mask, 183 d) | L3M | 21.4>10.1 (+53%) [-21.4, 0.0] | -40>-20 (w5) | +2.9 (19.0) [-5.1, +11.4] | +1.5 (23.0) c=1.14 | n/a |  |  |
| composite V1 (F1 mask, 183 d) | L6M | 22.9>10.1 (+56%) [-34.2, 0.0] | -61>-18 (w5) | -4.5 (14.8) [-13.7, +4.1] | -4.6 (16.0) c=1.14 | 99% (p 0.013) |  |  |
| composite V1 (F1 mask, 183 d) | HOLD | 97.0>68.0 (+30%) [-67.0, 0.0] | -189>-87 (w5) | -3.8 (15.3) [-12.5, +4.6] | -3.8 (16.2) c=1.14 | n/a |  |  |
| composite V1 (F1 mask, 183 d) | PRE | 241.2>172.3 (+29%) [-137.8, 79.4] | -875>-781 (w20) | -8.0 (10.3) [-15.3, -1.1] | -9.2 (10.8) c=1.14 | 77% (p 0.231) |  |  |
| composite V1 (F1 mask, 183 d) | X' | 120.5>81.8 (+32%) [-95.8, 45.2] | -420>-362 (w20) | -0.5 (7.0) [-5.0, +4.0] | -0.3 (7.5) c=1.14 | 65% (p 0.351) |  |  |
| composite V1 (F1 mask, 183 d) | ALL | 241.2>172.3 (+29%) [-135.4, 60.4] | -1098>-977 (w20) | -5.0 (6.5) [-9.5, -0.5] | -5.5 (6.8) c=1.14 | 79% (p 0.212) | 5/6 removals; all-five NO (-3%) | user def YES / decisive NO |
| as-is V1c | L3M | 88.0>30.8 (+65%) [-112.9, 0.0] | -185>-87 (w5) | +5.7 (22.6) [-3.9, +15.5] | +8.1 (23.2) c=1.14 | n/a |  |  |
| as-is V1c | L6M | 88.0>30.8 (+65%) [-94.7, 21.1] | -185>-107 (w5) | -1.5 (13.8) [-9.1, +6.5] | +1.3 (14.4) c=1.14 | 93% (p 0.067) |  |  |
| as-is V1c | HOLD | 144.2>108.6 (+25%) [-91.7, 14.2] | -263>-186 (w5) | -2.9 (14.6) [-10.7, +5.7] | -0.3 (14.8) c=1.14 | n/a |  |  |
| as-is V1c | PRE | 162.0>185.2 (-14%) [-55.2, 102.3] | -811>-683 (w20) | -7.5 (10.1) [-14.1, -1.5] | -5.9 (10.3) c=1.14 | 8% (p 0.921) |  |  |
| as-is V1c | X' | 316.5>226.6 (+28%) [-190.3, 104.6] | -572>-456 (w20) | -0.5 (6.6) [-6.2, +4.5] | -1.0 (6.8) c=1.14 | 55% (p 0.454) |  |  |
| as-is V1c | ALL | 316.5>226.6 (+28%) [-135.1, 110.0] | -1161>-1020 (w20) | -4.5 (6.3) [-8.8, -0.5] | -3.3 (6.4) c=1.14 | 57% (p 0.434) | 4/6 removals; all-five NO (+0%) | no (PRE deeper) |
| composite + 12R lock, V1c | L3M | 26.6>26.6 (+0%) [-15.4, 0.0] | -81>-51 (w5) | +4.3 (26.2) [-8.6, +20.5] | n/a | n/a |  |  |
| composite + 12R lock, V1c | L6M | 26.6>31.5 (-18%) [-16.6, 25.3] | -103>-96 (w5) | -5.3 (19.2) [-16.3, +6.9] | n/a | n/a |  |  |
| composite + 12R lock, V1c | HOLD | 35.3>35.3 (+0%) [-19.1, 24.5] | -109>-102 (w5) | -6.2 (17.6) [-16.4, +5.4] | n/a | n/a |  |  |
| composite + 12R lock, V1c | PRE | 232.6>232.3 (+0%) [-47.4, 161.0] | -608>-587 (w20) | -6.5 (8.7) [-11.5, -2.0] | n/a | n/a |  |  |
| composite + 12R lock, V1c | X' | 119.6>115.8 (+3%) [-157.3, 75.2] | -468>-391 (w20) | +2.0 (8.9) [-3.2, +7.0] | n/a | n/a |  |  |
| composite + 12R lock, V1c | ALL | 232.6>232.3 (+0%) [-87.4, 124.3] | -688>-661 (w20) | -4.0 (6.4) [-8.0, +0.1] | n/a | n/a | 0/6 removals; all-five NO (-40%) | no (adds nothing) |
| as-is + 12R lock, V1c | L3M | 104.9>47.2 (+55%) [-133.6, 25.4] | -146>-134 (w5) | +7.1 (24.7) [-6.1, +23.3] | n/a | n/a |  |  |
| as-is + 12R lock, V1c | L6M | 115.8>146.2 (-26%) [-103.6, 100.4] | -146>-146 (w5) | -0.9 (16.2) [-10.2, +10.3] | n/a | n/a |  |  |
| as-is + 12R lock, V1c | HOLD | 115.8>146.2 (-26%) [-107.0, 88.3] | -147>-147 (w5) | -2.6 (16.3) [-11.9, +8.8] | n/a | n/a |  |  |
| as-is + 12R lock, V1c | PRE | 276.0>320.9 (-16%) [-48.6, 134.7] | -585>-583 (w20) | -3.9 (8.4) [-9.1, +0.1] | n/a | n/a |  |  |
| as-is + 12R lock, V1c | X' | 436.3>294.9 (+32%) [-276.6, 131.2] | -584>-527 (w20) | +0.7 (8.5) [-5.7, +6.9] | n/a | n/a |  |  |
| as-is + 12R lock, V1c | ALL | 436.3>465.6 (-7%) [-193.5, 218.1] | -590>-587 (w20) | -2.3 (6.0) [-6.2, +1.4] | n/a | n/a | 0/6 removals; all-five NO (-16%) | no (deeper) |

MDE = 2.8 x SE of the paired weekly delta. Equal-risk: engine lot scale c so the ALL worst-20 matches the baseline's (secant, gap <= 4%). Placebo rank is n/a on the 12R rows (not run). The as-is rows are ranked against 1,000 as-is-frame block draws.

## 1. Per-episode table: top-10 drawdown episodes (ALL window, weekly cumulative, greedy peak to trough), blackout share of the loss

**Sunday composite.** All-sample P&L on blackout days 799.8k of 3316.5k = 24.1% (days: 185/745 = 24.8%; $/day blackout 4,323 vs other 4,494).

| # | dates | weeks | depth $k | blackout days / days | blackout-day P&L $k | other-day P&L $k | share of loss on blackout days | skip-series P&L same weeks $k |
|---|---|---|---|---|---|---|---|---|
| 1 | 2024-08-19 to 2024-10-04 | 7 | 241.2 | 8/35 (23%) | -63.1 | -178.1 | 26% | -178.1 |
| 2 | 2024-03-11 to 2024-04-12 | 5 | 156.4 | 8/25 (32%) | -20.2 | -136.2 | 13% | -136.2 |
| 3 | 2023-04-03 to 2023-05-19 | 7 | 120.5 | 8/35 (23%) | -41.4 | -79.1 | 34% | -75.6 |
| 4 | 2025-07-07 to 2025-07-25 | 3 | 97.0 | 5/15 (33%) | -67.1 | -29.9 | 69% | -29.9 |
| 5 | 2025-02-03 to 2025-02-28 | 4 | 95.7 | 0/20 (0%) | 0.0 | -95.7 | -0% | -95.7 |
| 6 | 2024-01-29 to 2024-02-16 | 3 | 79.6 | 3/15 (20%) | -9.6 | -70.0 | 12% | -70.0 |
| 7 | 2023-12-18 to 2023-12-22 | 1 | 65.7 | 0/5 (0%) | 0.0 | -65.7 | -0% | -65.7 |
| 8 | 2025-06-09 to 2025-06-13 | 1 | 57.9 | 5/5 (100%) | -57.9 | 0.0 | 100% | 0.0 |
| 9 | 2023-11-13 to 2023-11-24 | 2 | 56.5 | 0/10 (0%) | 0.0 | -56.5 | -0% | -56.5 |
| 10 | 2025-04-14 to 2025-04-18 | 1 | 50.2 | 0/5 (0%) | 0.0 | -50.2 | -0% | -50.2 |

Top-10 together: loss -1020.7k, of which on blackout days -259.3k = 25% against 22% of those episodes' days and 25% of all days.

**as-is stack.** All-sample P&L on blackout days 672.9k of 1945.9k = 34.6% (days: 185/745 = 24.8%; $/day blackout 3,637 vs other 2,273).

| # | dates | weeks | depth $k | blackout days / days | blackout-day P&L $k | other-day P&L $k | share of loss on blackout days | skip-series P&L same weeks $k |
|---|---|---|---|---|---|---|---|---|
| 1 | 2023-04-03 to 2023-12-01 | 35 | 316.5 | 40/175 (23%) | -89.9 | -226.6 | 28% | -226.6 |
| 2 | 2024-08-19 to 2024-10-11 | 8 | 162.0 | 8/40 (20%) | 23.2 | -185.2 | -14% | -185.2 |
| 3 | 2025-07-07 to 2025-07-25 | 3 | 144.2 | 5/15 (33%) | -35.6 | -108.6 | 25% | -108.6 |
| 4 | 2026-01-19 to 2026-01-23 | 1 | 88.0 | 5/5 (100%) | -88.0 | 0.0 | 100% | 0.0 |
| 5 | 2024-11-18 to 2024-11-22 | 1 | 87.8 | 0/5 (0%) | 0.0 | -87.8 | -0% | -87.8 |
| 6 | 2025-02-17 to 2025-03-07 | 3 | 64.5 | 0/15 (0%) | 0.0 | -64.5 | -0% | -64.5 |
| 7 | 2025-06-02 to 2025-06-13 | 2 | 58.5 | 5/10 (50%) | -54.6 | -3.9 | 93% | -3.9 |
| 8 | 2026-01-05 to 2026-01-09 | 1 | 30.8 | 0/5 (0%) | 0.0 | -30.8 | -0% | -30.8 |
| 9 | 2025-12-22 to 2025-12-26 | 1 | 27.7 | 0/5 (0%) | 0.0 | -27.7 | -0% | -27.7 |
| 10 | 2025-02-03 to 2025-02-07 | 1 | 23.5 | 0/5 (0%) | 0.0 | -23.5 | -0% | -23.5 |

Top-10 together: loss -1003.5k, of which on blackout days -244.9k = 24% against 22% of those episodes' days and 25% of all days.

Reading: the composite's top-10 episodes lose 25% of their money on blackout days on 24% of days, i.e. no concentration. Four episodes carry the cut: #1 (Aug-Oct 2024, 26% of the loss on 8 of 35 days, the Sep-2024 block lost 63k), #3 (Apr-May 2023, 34%), #4 (Jul 2025, 69%) and #8 (Jun 2025, 100%); four of the ten have no blackout day at all. In the as-is stack the 2024-09 block EARNED +23k inside its 162k PRE episode, which is why the rule deepens the as-is PRE (162k -> 185k, exactly that +23k removed).

## 2. Leave-one-episode-out (top-5 ALL episodes of the composite; peak..trough weeks removed from both series) and leave-one-MEETING-out

| removed | span | maxDD before>after $k | cut | worst-20 before>after $k | survives |
|---|---|---|---|---|---|
| none (ALL) |  | 241.2>179.6 | 26% | -1098>-942 | yes |
| ep1 depth 241k | wk 202434..202440 (7 wk) | 156.4>136.2 | 13% | -913>-791 | yes |
| ep2 depth 156k | wk 202411..202415 (5 wk) | 241.2>179.6 | 26% | -984>-865 | yes |
| ep3 depth 121k | wk 202314..202320 (7 wk) | 241.2>179.6 | 26% | -1059>-901 | yes |
| ep4 depth 97k | wk 202528..202530 (3 wk) | 241.2>179.6 | 26% | -1016>-896 | yes |
| ep5 depth 96k | wk 202506..202509 (4 wk) | 241.2>179.6 | 26% | -1082>-918 | yes |
| all top-5 |  | 79.6>81.7 | -3% | -603>-541 | no |

Removing ep2-ep5 leaves the ALL maxDD unchanged (ep1 still sets it), so those rows test only the tail; ep1 removed: 156k -> 136k (13%); all five removed: 79.6k -> 81.7k (the rule deepens the remaining drawdowns by 3%). L6M with its single worst episode removed (weeks [202543], 2025-10-20 to 2025-10-24): base 21.4k vs rule 10.1k (before removal 22.9k > 10.1k). The as-is L6M maxDD episode is 2026-01-19 to 2026-01-23: all five label days are inside the blackout (F1 counted four because its mask dropped the MLK session).

**Leave-one-meeting-out** (V1c with one FOMC block restored, composite; cut by window):

| meeting kept tradable | L6M | PRE | X' | ALL |
|---|---|---|---|---|
| 20230503 | +56% | +26% | +0% | +26% |
| 20240918 | +56% | -1% | +32% | -1% |
| 20251029 | +0% | +26% | +32% | +26% |
| 20260128 | +7% | +26% | +32% | +26% |

(all 23 meetings were run: the full-rule cut is L6M +56%, PRE +26%, X' +32%, ALL +26%; only the rows above move it; every other meeting leaves all four unchanged, +-0). The cut in each window is one or two blocks: Sep-2024 for PRE/ALL (without it -1%), Apr-May 2023 for X' (without it 0%), Oct-2025 and Jan-2026 for L6M.

## 3. Matched placebos, 1,000 draws each (composite; rank = share of draws with a smaller cut than the real; p = (1+#draws with cut >= real)/1001)

| family | frame | real | n days / live signals | L6M rank (p) | PRE rank (p) | X' rank (p) | ALL rank (p) | ALL worst-20 rank | draws with L6M cut >= 20% | PRE+X' both >= 20% | all three >= 20% |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U1 block, unrestricted position (primary) | C | V1c | 185 / 4409 (real 4386) | 98.8% (0.013) | 62.9% (0.372) | 67.7% (0.324) | 65.6% (0.345) | 72% | 2.9% | 20.5% | 0.4% |
| U1, real = F1 mask | C | V1 | 185 / 4409 (real 4386) | 98.8% (0.013) | 77.0% (0.231) | 65.0% (0.351) | 78.9% (0.212) | 58% | 2.9% | 20.5% | 0.4% |
| P1 block, disjoint from real days | C | V1c | 185 / 4385 (real 4386) | 100.0% (0.001) | 72.7% (0.274) | 89.9% (0.102) | 73.5% (0.266) | 69% | 0.0% | 10.9% | 0.0% |
| P2 each FOMC date shifted +-1..8 weeks | C | V1c | 165 / 4001 (real 4386) | 99.8% (0.003) | 67.8% (0.323) | 81.6% (0.185) | 69.6% (0.305) | 79% | 1.0% | 11.9% | 0.2% |
| P3 183 single days, weekday+era matched | C | V1c | 185 / 4497 (real 4386) | 100.0% (0.001) | 66.7% (0.334) | 77.0% (0.231) | 69.8% (0.303) | 97% | 0.0% | 16.2% | 0.0% |
| U1 block, as-is frame | A | V1c | 185 / 4409 (real 4386) | 93.4% (0.067) | 7.9% (0.921) | 54.7% (0.454) | 56.7% (0.434) | 66% | 25.9% | 15.1% | 4.5% |

The P1 (disjoint) L6M rank of 100% is by construction (a placebo disjoint from the real days can never remove the composite's L6M maxDD week, 2025-10-20..24, which is inside the 2025-10-29 block); the unrestricted U1 is the primary and is what G3 uses. Placebo cut means/p95: U1 L6M -31%/+18%, PRE +16%/+44%, X' +11%/+50%, ALL +15%/+44%. Common-shift scan (every meeting moved together, composite, cut L6M/PRE/X'/ALL): -10w +0%/+36%/+37%/+36%; -8w -13%/+41%/-45%/+28%; -5w -103%/+13%/+50%/+13%; -1w +18%/+33%/+32%/+33%; +0w +56%/+26%/+32%/+26%; +1w -103%/+10%/-1%/+10%; +6w +18%/+39%/+0%/+39%; +10w +0%/+31%/+0%/+31%. Shifted calendars give PRE cuts of +30-40% as often as not.

## 4. Stationary-bootstrap 95% CIs of the CHANGE (after minus before; block 4 weeks, 4,000 resamples; block-8 maxDD CI in the last column)

| table | window | dMaxDD $k [CI] P(better) | dWorst (w20/w5) $k [CI] | dSD $k [CI] | dCalmar [CI] | dMaxDD CI block 8 |
|---|---|---|---|---|---|---|
| composite V1c | L6M | -12.8 [-34.2, 0.0] 0.94 | 44.3 [-4.9, 85.9] | -3.3 [-11.1, 3.8] | +1.730 [-0.630, +9.859] | [-22.9, -5.0] |
| composite V1c | HOLD | -29.0 [-67.1, 0.0] 0.80 | 104.4 [18.5, 197.2] | -9.2 [-19.5, 1.5] | +0.099 [-0.160, +8.136] | [-63.0, 0.0] |
| composite V1c | PRE | -61.6 [-128.8, 67.6] 0.67 | 142.1 [-19.2, 304.9] | -9.2 [-14.3, -4.4] | -0.010 [-0.131, +0.030] | [-125.9, 46.1] |
| composite V1c | X' | -38.8 [-95.7, 50.6] 0.62 | 54.2 [-68.6, 141.8] | -1.8 [-3.4, 0.1] | +0.022 [-0.098, +0.100] | [-99.5, 39.8] |
| composite V1c | ALL | -61.6 [-126.4, 53.5] 0.76 | 156.4 [14.6, 315.3] | -7.7 [-11.6, -3.8] | +0.003 [-0.082, +0.047] | [-124.7, 31.3] |
| composite V1 | L6M | -12.8 [-34.2, 0.0] 0.94 | 43.7 [-5.6, 88.0] | -3.9 [-11.9, 3.6] | +1.832 [-0.607, +12.092] | [-22.9, -5.0] |
| composite V1 | HOLD | -29.0 [-67.0, 0.0] 0.80 | 102.8 [17.5, 196.5] | -9.5 [-19.7, 1.2] | +0.113 [-0.147, +8.525] | [-63.0, 0.0] |
| composite V1 | PRE | -68.9 [-137.8, 79.4] 0.65 | 94.3 [-97.5, 285.4] | -8.3 [-13.5, -3.3] | -0.008 [-0.141, +0.028] | [-137.4, 53.4] |
| composite V1 | X' | -38.7 [-95.8, 45.2] 0.63 | 57.2 [-53.8, 141.5] | -1.8 [-3.4, -0.1] | +0.025 [-0.090, +0.106] | [-100.1, 34.5] |
| composite V1 | ALL | -68.9 [-135.4, 60.4] 0.75 | 121.1 [-39.6, 292.0] | -7.2 [-11.1, -3.5] | +0.008 [-0.084, +0.049] | [-131.7, 32.2] |
| as-is V1c | L6M | -57.3 [-94.7, 21.1] 0.72 | 78.2 [-10.5, 219.1] | -4.9 [-14.3, 1.6] | +0.411 [-0.774, +0.766] | [-78.0, 16.1] |
| as-is V1c | HOLD | -35.6 [-91.7, 14.2] 0.81 | 76.8 [0.0, 187.4] | -9.4 [-19.7, 0.6] | +0.023 [-0.283, +0.590] | [-73.9, 10.7] |
| as-is V1c | PRE | 23.2 [-55.2, 102.3] 0.22 | 127.8 [-31.0, 320.5] | -9.6 [-16.4, -4.2] | -0.055 [-0.144, +0.018] | [-46.1, 96.7] |
| as-is V1c | X' | -89.9 [-190.3, 104.6] 0.72 | 116.1 [22.1, 205.5] | -4.6 [-9.5, -0.3] | -0.006 [-0.041, +0.011] | [-194.3, 84.4] |
| as-is V1c | ALL | -89.9 [-135.1, 110.0] 0.60 | 140.6 [19.8, 302.9] | -8.7 [-13.2, -4.6] | -0.004 [-0.062, +0.020] | [-166.9, 90.9] |

Every maxDD interval contains zero in PRE, X' and ALL (the upper bound of the L6M/HOLD intervals is 0.0 because the rule cannot lengthen a drawdown in a resample that never touches a blackout week). The weekly SD interval is below zero in PRE and ALL (a 24% volume cut shrinks the SD 14%: 50.3k -> 43.1k ALL V1); Calmar intervals contain zero everywhere.

## 5. What the rule costs

Mean change (composite V1c, paired weekly delta, $k/wk): L6M -5.6 (MDE 14.6) [-14.5, +3.0], PRE -7.6 (MDE 10.4) [-15.1, -0.8], X' -0.8, ALL -5.1 (MDE 6.5) [-9.7, -0.7]: the ALL mean falls from 22.3k to 17.2k per week (-23%), the PRE and ALL intervals exclude zero. Equal-risk (lots x1.17 so the ALL worst-20 matches): L6M -6.0k (MDE 15.8), PRE -8.2k (10.8), ALL -5.3k (6.8): the rule does not beat running the composite at the lot scale that has the same tail. The skipped 22-24% of the days earned $800k of the $3,317k sample P&L ($4,323/day vs $4,494/day on other days; 15 of 23 blocks positive, 8 negative: the 23 blocks net +800k, mean 35k per block); skipping costs that money and saves the money of the 8 losing blocks (-63k Sep-2024, -51k Jun-2025, -51k Dec-2025, -41k Apr-2023, -36k Jun-2023 ...).

## 6. Variant family (8 cells; Bonferroni bar p <= 0.05/8 = 0.00625; composite; unrestricted block placebo of the variant's own structure)

| variant | action | days / live signals | L6M cut (rank, p) | PRE cut (rank, p) | X' cut (rank, p) | ALL cut (rank, p) | ALL worst-20 rank | mean L6M (MDE) | mean ALL (MDE) | best p x8 |
|---|---|---|---|---|---|---|---|---|---|---|
| V1 F1 mask (skip) | skip | 183 / n/a | +56% (99%, 0.013) | +29% (77%, 0.231) | +32% (65%, 0.351) | +29% (79%, 0.212) | 58% | -4.5 (14.8) | -5.0 (6.5) | 0.10 |
| V1f full flat, same 183 days | skip | 183 / n/a | +56% (99%, 0.013) | +26% (63%, 0.372) | +32% (68%, 0.324) | +26% (66%, 0.345) | 56% | -4.7 (15.2) | -5.4 (6.7) | 0.10 |
| V1c full flat 185 days | skip | 185 / 4386 | +56% (99%, 0.013) | +26% (63%, 0.372) | +32% (68%, 0.324) | +26% (66%, 0.345) | 72% | -5.6 (14.6) | -5.1 (6.5) | 0.10 |
| V2 pre-statement 7 days only | skip | 162 / 3925 | +56% (99%, 0.014) | +22% (68%, 0.323) | +27% (70%, 0.302) | +22% (69%, 0.308) | 87% | -4.9 (10.2) | -5.2 (6.0) | 0.11 |
| V3 statement day only | skip | 23 / 461 | +0% (33%, 0.666) | +5% (68%, 0.324) | +13% (60%, 0.400) | +5% (68%, 0.324) | 38% | -0.6 (7.0) | +0.4 (2.4) | 1.00 |
| V4 blackout +-1 day (231 d) | skip | 231 / 5692 | +41% (95%, 0.049) | +30% (72%, 0.286) | +31% (75%, 0.248) | +30% (75%, 0.254) | 76% | -10.4 (14.9) | -7.6 (7.8) | 0.39 |
| V5 HALVE blackout (185 d) | halve | 185 / 4386 | +56% (98%, 0.017) | +15% (53%, 0.470) | +10% (42%, 0.583) | +15% (53%, 0.470) | 76% | -1.9 (7.0) | -2.0 (3.3) | 0.14 |
| V6 statement day +-1 (69 d) | skip | 69 / 1724 | +0% (44%, 0.564) | -5% (38%, 0.624) | +33% (92%, 0.080) | -5% (38%, 0.622) | 18% | -3.8 (11.9) | -2.7 (5.7) | 0.64 |

No variant has a PRE, X' or ALL placebo rank above 95%; the best single p (L6M) is 0.013 for V1c, 0.014 for V2, 0.017 for V5, 0.049 for V4, none below the corrected 0.00625. Statement-day-only (V3) and statement +-1 (V6) do nothing for L6M and PRE: the cut comes from the seven days BEFORE the statement (V2 reproduces V1c: L6M +56%, PRE +22%, X' +27%). Halving (V5, the engine multiplier route) keeps the L6M cut (+56%) and half of the PRE/X' cut (+15%/+10%) at less than half the mean cost (ALL -2.0k vs -5.1k per week) - it is the more implementable form if a D6 owner wants a softer line, but it fails the same gates (PRE rank 53%).

## 7. As-is stack and the 12R-lock version

As-is stack V1c: L6M +65% (88.0k > 30.8k, the 2026-01-19 week, rank 93% vs 1,000 as-is block draws; 26% of random as-is block calendars also cut L6M by >= 20%), HOLD +25%, PRE -14% (162.0k > 185.2k, placebo rank 8%), X' +28% (the 35-week 2023 episode, rank 55%), ALL +28%. Why PRE deepens: the as-is PRE episode (2024-08-19 to 2024-10-11, 162k) contains the 2024-09-18 blackout block, which EARNED +23.2k in the as-is stack (it lost 63.1k in the composite; B1 traced the composite's 2024-08..09 path to the ER sizer and PE confirm, which the as-is stack lacks); skipping it removes a gain inside a drawdown. The composite and the as-is stack disagree on the sign of the one block that carries the PRE cut.

12R combined week lock (rule and baseline both run with the lock): composite ALL 232.6k > 232.3k (+0%), PRE +0%, X' +3%, L6M 26.6k > 31.5k (-18%), worst-20 ALL -688 > -661; as-is + 12R: ALL -7%, PRE -16%, L6M -26%. The lock already removes the Sep-2024 and 2023 drawdowns' depth, so the blackout rule has nothing left to cut and deepens L6M.

## 8. Mechanism: is the blackout a low-information, pre-event chop?

**Composite (stack $ per live taken signal, dollars = engine P&L x lots x $20).** Day-cluster bootstrap CI of the blackout-minus-other difference; p = circular block-shift permutation of the blackout flags over the 745 days (4,000).

| subset | n blackout / other | mean $/signal blackout vs other | hit rate | difference [CI] | p shift (two-sided) |
|---|---|---|---|---|---|
| all signals | 2536 / 7973 | 315 vs 316 | 53.9% vs 54.0% | -0 [-320, +320] | 0.999 |
| outside top-10 episode weeks | 2090 / 6424 | 507 vs 510 | 55.7% vs 55.6% | -4 [-349, +341] | 0.975 |
| book HM | 358 / 1136 | 169 vs 279 | 53.6% vs 55.3% | -109 [-597, +371] | 0.556 |
| book KB | 803 / 2584 | 203 vs 106 | 55.3% vs 52.8% | +97 [-103, +298] | 0.459 |
| book MV | 461 / 1492 | -99 vs 119 | 50.3% vs 54.2% | -219 [-480, +39] | 0.035 |
| book PB | 162 / 436 | 362 vs 273 | 57.4% vs 54.1% | +89 [-301, +454] | 0.610 |
| book PE | 586 / 1861 | 819 vs 775 | 53.8% vs 53.8% | +44 [-861, +927] | 0.893 |
| book SM | 166 / 464 | 503 vs 403 | 55.4% vs 56.7% | +100 [-901, +1,136] | 0.835 |
| session asia | 913 / 2794 | 793 vs 365 | 57.3% vs 54.1% | +428 [-181, +1,042] | 0.141 |
| session london | 556 / 1925 | -255 vs 219 | 48.6% vs 54.1% | -474 [-1,183, +252] | 0.066 |
| session nyam | 887 / 2773 | 190 vs 401 | 52.9% vs 54.7% | -211 [-660, +251] | 0.283 |
| session nypm | 180 / 481 | 274 vs -77 | 58.9% vs 48.4% | +351 [-15, +730] | 0.281 |

**As-is.** Day-cluster bootstrap CI of the blackout-minus-other difference; p = circular block-shift permutation of the blackout flags over the 745 days (4,000).

| subset | n blackout / other | mean $/signal blackout vs other | hit rate | difference [CI] | p shift (two-sided) |
|---|---|---|---|---|---|
| all signals | 2837 / 8510 | 237 vs 150 | 53.5% vs 52.5% | +88 [-200, +357] | 0.582 |
| outside top-10 episode weeks | 1969 / 5492 | 466 vs 370 | 55.8% vs 55.0% | +96 [-218, +420] | 0.559 |
| book HM | 502 / 1516 | 105 vs 180 | 51.6% vs 53.2% | -75 [-459, +303] | 0.685 |
| book KB | 799 / 2322 | 202 vs 93 | 54.6% vs 52.1% | +109 [-72, +298] | 0.388 |
| book MV | 464 / 1487 | -11 vs 75 | 50.2% vs 52.0% | -86 [-332, +162] | 0.323 |
| book PB | 180 / 504 | 222 vs 116 | 60.0% vs 55.4% | +106 [-116, +311] | 0.279 |
| book PE | 652 / 1994 | 558 vs 210 | 54.0% vs 51.4% | +348 [-447, +1,116] | 0.446 |
| book SM | 240 / 687 | 252 vs 285 | 53.8% vs 54.1% | -33 [-763, +696] | 0.905 |
| session asia | 1170 / 3598 | 422 vs 114 | 56.0% vs 52.4% | +308 [-126, +766] | 0.368 |
| session london | 579 / 1992 | -116 vs 176 | 48.7% vs 53.3% | -291 [-884, +289] | 0.219 |
| session nyam | 961 / 2650 | 199 vs 185 | 52.7% vs 52.2% | +14 [-401, +427] | 0.939 |
| session nypm | 127 / 270 | 434 vs 83 | 58.3% vs 50.4% | +350 [-106, +812] | 0.317 |

Signals per day 13.7 (blackout) vs 14.2; exit-type shares identical (52.7%/44.0%/3.2% vs 52.3%/44.3%/3.4%); daily P&L mean $4,323 vs $4,494 (Welch p 0.94), SD $27.5k vs $26.1k (Levene p 0.49), 5th percentile -$35.4k vs -$37.0k. Outside the weeks of the ten deepest composite episodes the blackout signals earn $507 vs $510 per signal, hit rate 55.7% vs 55.6%: no difference. The only subsets near significance are MV book (-99 vs +119, p 0.035) and the London session (-255 vs +219, p 0.066 two-sided) among 12 looked, i.e. chance; the Asia session is better on blackout days (+428), the opposite sign. There is no mechanism: the blackout days are ordinary days that happen to contain 4 of the composite's bad weeks, and the maxDD cut is the volume cut (24% fewer signals) landing on those weeks.

## 9. Calendar, exact rule, D6 policy line and NT8 spec (Shadow only)

**Exact rule.** Blackout day = CME trading day (session date: 18:00 ET the evening before to 17:00 ET, the engine's label day) from the second Saturday before the FIRST day of a scheduled FOMC meeting through the statement day, inclusive; first day = statement date minus one (every meeting in the sample is two days; the 2024-11-07 Thursday statement gives a 9-day block). 23 blocks of 8 days (one of 9) = 185 days of 745 in 2023-04-03..2026-02-06, including the Globex holiday sessions 2025-01-20 and 2026-01-19. Source: `l2vast/standS/event_calendar_core.csv` FOMC rows (provenance VERIFIED, 'federalreserve.gov FOMC calendars (saved 2026-09-18)'); only rows dated <= 2026-02-06 were retained at read time. The saved Fed page is NOT on disk, so the file cannot be machine-checked against the Fed; the 25 capped statement dates (2023-02-01, 03-22, 05-03, 06-14, 07-26, 09-20, 11-01, 12-13; 2024-01-31, 03-20, 05-01, 06-12, 07-31, 09-18, 11-07, 12-18; 2025-01-29, 03-19, 05-07, 06-18, 07-30, 09-17, 10-29, 12-10; 2026-01-28) were compared with the published Fed schedule from memory and all agree; this is a recollection check, flagged as not verified against a file on disk. Nothing after the cap was read, so the 2026 dates are NOT in the dates file; the live file must be built from federalreserve.gov with the same rule. Dates file (capped part): `out/fedblackout/fed_blackout_dates.csv` (185 rows: date, fomc_statement, offset, in_F1_mask), meeting list `fomc_dates_used.csv`. Not modelled: unscheduled meetings, the Fed's own end-of-blackout (midnight after the day after the meeting; the rule ends at the statement day), speaker days.

**D6 policy line (calendar).** `CAL-FED: flat on Fed-blackout days - no new entries by any D6 book (K6, P6, U6, H6, M6, A6) on a CME session date listed in fed_blackout_dates.csv; open positions run to their own exits; no discretion, no halving.` Halving variant (V5) is the softer alternative: engine multiplier 0.5 on the same dates.

**NT8 spec.** Strategy parameter `FedBlackoutFile` (CSV, column `date` as yyyyMMdd, session date). On start load into a `HashSet<int>`. In `OnBarUpdate`, before any entry order for a signal: `int td = SessionIterator.GetTradingDay(Time[0]).ToString("yyyyMMdd")` (the CME session date, so the Sunday 18:00 ET Asia session carries Monday's date); `if (blackout.Contains(td)) { Print("FEDBLACKOUT skip "+signalId); return; }`. Exits, stops and trailing of positions already open are not touched. Log one line per skipped signal (book, session, time, side, planned lots) for the paper log. The file must be regenerated from the Fed's published calendar each January.

**Shadow paper log and STOP rule (optional: the decisive label is NO, so this is a cost-free record, not a promotion).** Log the hypothetical P&L of every skipped signal (the signals are generated anyway) and compare per block with matched non-blackout days. STOP the line (retire it) when, after at least 8 logged FOMC blocks (about one year), the cumulative hypothetical P&L of the skipped signals is positive and larger than one block-MDE (2.8 x the standard error of the block P&L, computed from the logged blocks at that time) i.e. the line has only been paying its cost, OR when two consecutive blocks show a skipped-signal loss smaller than the block-average of the same signals outside the blackout. It is a rolling criterion, not a P&L stop. Re-test with the same code when 8 blocks are in.

## 10. Integrity and what is not claimed

- The L6M maxDD is one week in each frame: composite 22.9k = the week of 2025-10-20 (Oct-2025 FOMC block; F1 named 2026-01-19, which is the AS-IS frame's 88.0k week); with the composite's Oct-2025 week removed the base L6M maxDD is 21.4k (the 2026-01-19 week) against 10.1k with the rule; the placebo rank in L6M (99%) measures how often a random block calendar covers that week and cuts it, not an out-of-sample hedge. PRE/X' are in-sample for the choice; HOLD/L6M/ALL were read once by F1.
- F1's frozen mask is not a full flat: it omits the two MLK Globex sessions and 162 taken PB-asia signals (X' era); F1's -56%/-29%/-32% reproduce exactly with the F1 mask (V1) and move to -56%/-26%/-32% with the full flat (V1c). The F1 note that 4 of the 5 L6M label days are inside the blackout is 5 of 5 once the holiday session is counted.
- The first placebo design (P1, disjoint from the real days) makes the L6M rank 100% by construction; it was replaced as primary by the unrestricted U1 before the variant placebos ran (P1 kept beside). The choice was made after seeing P1's L6M rank, before seeing any U1 number.
- Eight cells, one headline: family-wise p (best, L6M) = 0.10 for V1c. No PASS, no promotion; DEAD_CELLS +16 (program F2FB).
