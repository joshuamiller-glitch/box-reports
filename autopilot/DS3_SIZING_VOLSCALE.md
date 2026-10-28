# DS3_SIZING_VOLSCALE - confirmation test of week-constant vol-scaled lots on the D3SL stack and the DS5 mix (D3VS, 2026-10-28). Research only; nothing live; no spec written (not CONFIRMED).
Prereg `l2vast/ds3/prereg/D3VS_prereg.md` sha256 455b6db1b1e62dec92119fa38a5e81853a5461954d67419a96b293c3bdcd7776 (DECISIONS.md 03:26Z, before any rule cell was scored), 21 cells in 2 groups (G1 STACK, G2 DS5), F = 21. Pre-holdout texts `autopilot/DS3_SIZING_VOLSCALE_G1_PREHOLD.md` / `_G2_PREHOLD.md` (PRE only, logged 4 looks: tracks D3VS_G1, D3VS_G1_SPAN2, D3VS_G2, D3VS_G2_SPAN2; HOLD and 2023-04..2024-01 read once per group, not re-read). Code `l2vast/ds3/code/vs/` (vs_build, vs_lib, vs_cells, vs_run, vs_gates, vs_report, vs_posthoc); outputs `l2vast/ds3/out/vs/` (base.pkl, pre_results.json, final_results.json, posthoc.json, report_tables.md).

## Verdict line
**DEAD. The pre-fixed 8-week rule (week-constant lots x clip(median-so-far trailing SD / current trailing SD, 0.5, 2), per book, 8-week lookback) on the D3SL stack (S_V8) and on the DS5 mix with DN on measured fills (D_V8) both fail G3 (maxDD / worst week), G6 (2023-04..2024-01) and G7 (mean-matched risk); D_V8 also fails G4-PRE and G5. The 4-week control is worse than the 8-week on every tail measure. Nothing to put live.** What the rule does is real but is leverage-after-calm, not risk reduction: lot-matched it earns more (S_V8 HOLD +4,737/wk [+949,+8,624], MDE 5,583, placebo rank 1.00, p 0.0073 which does not clear best-of-F 0.05/21 = 0.0024), but it pays for it with a larger weekly SD (+10,117), maxDD (+81,427) and worst week (-35,645) in HOLD, and the same signs in the second holdout (SD +16,026, maxDD +75,303, worst -21,416). At equal mean (mean-matched) the HOLD SD is +4,053, maxDD +54,039, worst -21,430 (all worse); unmatched, it is a trim (avg lots x0.88, WF mean -2,652, SD -12,170) that is worse on tails than a uniform trim to the same average lots (post-hoc: HOLD maxDD +73,687, worst -31,779 relative to uniform). The 8-week rule is "steadier" than the 4-week rule (HOLD maxDD +81k vs +124k, worst -36k vs -87k) but that is the only sense in which the D3SZR suspicion holds.
Tier table (prereg): CONFIRMED 0, LEAD 1 (D_V8_MV, a descriptive single-book cell: HOLD +21/wk, MDE 1,241, i.e. an exact null), DEAD 20. The group verdicts are those of the primary cells (S_V8 DEAD, D_V8 DEAD).

## What was fixed in advance (summary; full text in the prereg)
- Stack = D3SL: ST10 + HM10 + WT7 + KB/SM/PB at 10 x W_k(t) (frozen monthly inverse-26w-SD weights, DS3 peak 23 lots), rows regenerated with the busy-correct chain (DS3_BLOCKRULES), PB from books.pkl, exact per-book 1-s locks; baseline WF 45,947/wk (identical to the BLOCKRULES regenerated live baseline). DS5 = KB5 DN8 SM7 PE5 MV4, DN on the MB basis (bracket on the actual fill, measured 10-level walk; DS3_DN_STOPFILL).
- Exactness: lock engine homogeneity (lots x1.5 and R x1.5 vs 1.5 x daily: max abs diff 2.9e-11 $, all six books) and every lock group (day, week) lies in one label week (0 of 193 multi-week), so a week-constant multiplier scales that week's locked P&L exactly. Size-dependent cost: s113 equal_risk.excess surface; DN: measured MB lot grid Q = 5/8/10/13/14.
- Comparisons paired by week against the unscaled base: raw; LOT-MATCHED (c = 1/PRE lot-weighted mean multiplier, fixed on PRE); MEAN-MATCHED (c solved so the PRE weekly mean equals the base's, cost model re-evaluated, fixed on PRE). Placebo: 150 shifted + 150 permuted week-label draws (all books jointly), matching repeated per draw. Gates G1-G5 as D3SZR (unchanged) plus G6 (2023-04..2024-01: LM mean >= 0, maxDD <= 0, worst >= 0) and G7 (mean-matched SD, maxDD <= 0, worst >= 0 in PRE and HOLD): stricter, none softened. MDE = 2.8 SD_diff/sqrt(n) beside every estimate.

## Baselines (unscaled, weekly $; maxDD on the daily path)
| target | window | wk | mean | SD | maxDD | worst |
|---|---|---|---|---|---|---|
| STACK (D3SL) | PRE | 75 | 44,127 | 131,184 | 477,701 | -306,664 |
| STACK | HOLD | 68 | 47,279 | 140,987 | 601,016 | -318,557 |
| STACK | 2023-04..2024-01 | 44 | 20,616 | 112,784 | 553,090 | -157,300 |
| STACK | WF | 142 | 45,947 | 136,281 | 601,016 | -318,557 |
| DS5 (DN MB) | PRE | 75 | 39,156 | 90,848 | 318,164 | -221,819 |
| DS5 | HOLD | 68 | 43,538 | 101,055 | 424,659 | -188,005 |
| DS5 | 2023-04..2024-01 | 44 | 3,609 | 71,272 | 436,812 | -178,268 |
| DS5 | WF | 142 | 41,530 | 95,708 | 424,659 | -221,819 |
DS5 WF is 41.5k here vs 46.7k in D3SZR: DN priced on measured fills (MB) instead of the mapped stop-price basis, KB/SM on regenerated rows. The DS5 mix has the lower SD and drawdown per dollar than the D3SL stack (WF Sharpe 3.13 vs 2.43) but the 2023 span is near flat (+3.6k/wk).

## Reading
1. G3 is the failure, and it is the same one as D3SZR. Lot-matched, the rule runs ~13.6% more lots than its raw multiplier in calm weeks to keep average lots; in PRE this is harmless (maxDD -33k, SD -0.8k, worst -13k) but in HOLD and in the 2023 span the weeks after a calm stretch are the weeks that hurt: HOLD d_SD +10.1k (CI [+4.9k,+15.3k]), d_maxDD +81k, d_worst -36k; placebo ranks for the risk measures are 0.01-0.10 (the rule is worse on tails than shifted/permuted timing at the same lots), while the mean rank is 0.99-1.00. So the mean edge is a timing effect (calm persists on average) and the cost is a fat left tail when it does not.
2. Mean-matching does not rescue it. At equal PRE mean the PRE risk numbers look good (SD -6.0k [-10.2k,-1.7k], maxDD -51k, worst -0.6k) but HOLD flips (SD +4.1k, maxDD +54k, worst -21k) and the 2023 span as well (SD +10.9k, maxDD +50k). Single-path maxDD and worst week are one path / one week each (68 weeks): the sign flip between PRE and HOLD is the information, not the size.
3. Unmatched (raw, avg lots x0.88): WF mean -2,652 (CI [-5,648,+262], MDE 4,215), SD -12,170, maxDD -354, worst +6,801; PRE and HOLD both trim SD (-16.4k / -8.0k). It is a de-risking at a cost of income, and against a uniform trim to the same average lots it adds mean (+3.9k HOLD) but also +8.8k SD, +73.7k maxDD, -31.8k worst (post-hoc, posthoc.json). Not a reason to prefer it.
4. 8-week vs 4-week (control): S_V4 lot-matched PRE +4,411 / HOLD +3,136 [-1,946,+8,004] / X +6,533, HOLD d_maxDD +123,574, d_worst -87,377, mean-matched HOLD d_mean -1,471 (G2, G4, G5, G6, G7 fail). The 8-week is the steadier sibling, but still fails G3; the post-HOLD reading in D3SZR was right in direction and wrong in conclusion.
5. One account-level multiplier (S_V8_AGG) is better on worst week (HOLD -19k LM, +5k MM) and mean-matched maxDD (+10k) than per-book scaling, with PRE d_mean +3,431 [+452,+6,320] and placebo 0.98/0.98, but still fails G3 (HOLD maxDD +57,843), G6, G7 (SD +6,448). It is the least bad variant, not a pass.
6. By book (descriptive): ST, HM, WT, PB, KB and SM individually add +46 to +1,068/wk HOLD (all inside their MDEs 1.2k-2.2k, only WT and KB have CIs above 0) with maxDD +3.6k to +30.6k; KB is negative in PRE (-1,135, placebo 0.20): the rule is not a per-book property. In DS5, MV (-17k maxDD, +11k worst) is the only risk-side cell and its mean delta is +21/wk (rank 0.80): no evidence.
7. DS5 on measured fills: D_V8 PRE +808 [-1,467,+3,212] (MDE 3,351, placebo 0.71), HOLD +3,484 [+418,+6,621] (MDE 4,549, rank 0.99), d_SD +6,411, d_maxDD +42,928, d_worst -15,705; mean-matched HOLD SD +4,194, maxDD +33,624. The PRE placebo (0.71) fails G4 in addition. DN alone (D_V8_DN): PRE +416, HOLD +386, MDEs 1.9-2.1k: nothing. The cost model does not matter here (see deviations 3-4).
8. Years (WF, LM summed weekly deltas, S_V8): 2024 +155,607 (49 wk), 2025 +218,573 (52), 2026 +86,285 (41): all positive, none above 60% of the total (G5 passes); D_V8 2024 +55,398, 2025 +227,640, 2026 +14,494 (2025 = 77% of the total, G5 fails). Mean-matched S_V8: +71,152 / +97,003 / +11,996; D_V8 +13,122 / +184,779 / -22,070. By year the gain is a 2025 phenomenon in DS5.
9. 2023: nothing here fixes the 2023-04..2024-01 span either (the rule is inactive for its first ~12 weeks of the span): X LM d_mean +3,597 (S_V8) / +1,315 (D_V8), inside MDE 7,270 / 5,175, with SD +16.0k / +11.8k.
10. Detectability: S_V8 HOLD MDE 5,583/wk vs effect +4,737; the best-of-F threshold p <= 0.00238 is not reached (0.0073). At the HOLD point effect about 95 weeks (164 at the WF effect +3,243, MDE 3,483) would be needed to detect the mean edge at 80% power, so the mean edge is borderline detectable forward; the tail cost is the finding that matters.

## All 21 cells (lot-matched = LM, mean-matched = MM; weekly $; HOLD = 2025-07..2026-10, 68 wk)

| cell | tier | gates failed | raw avg lots x | LM d_mean PRE / HOLD / X | HOLD CI iid (MDE) | HOLD p(boot<=0) | LM placebo rank PRE/HOLD | HOLD LM d_SD | HOLD LM d_maxDD | HOLD LM d_worst | HOLD MM d_mean | HOLD MM d_SD | HOLD MM d_maxDD | HOLD MM d_worst |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S_V8 | DEAD | G3,G6,G7 | 0.880 | +1,845 / +4,737 / +3,597 | [+949,+8,624] (5,583) | 0.0073 | 0.95/1.00 | +10,117 | +81,427 | -35,645 | +2,649 | +4,053 | +54,039 | -21,430 |
| S_V4 | DEAD | G2,G3,G4,G5,G6,G7 | 0.899 | +4,411 / +3,136 / +6,533 | [-1,946,+8,004] (7,058) | 0.1066 | 0.99/0.95 | +12,275 | +123,574 | -87,377 | -1,471 | -1,752 | +57,167 | -50,146 |
| S_V8_c0 | DEAD | G3,G4,G6,G7 | 0.880 | +1,845 / +4,737 / +3,597 | [+949,+8,624] (5,583) | 0.0073 | 0.92/1.00 | +10,117 | +81,427 | -35,645 | +2,649 | +4,053 | +54,039 | -21,430 |
| S_V8_c2 | DEAD | G3,G4,G6,G7 | 0.880 | +1,845 / +4,737 / +3,597 | [+949,+8,624] (5,583) | 0.0073 | 0.94/1.00 | +10,117 | +81,427 | -35,645 | +2,649 | +4,053 | +54,039 | -21,430 |
| S_V8_AGG | DEAD | G3,G6,G7 | 0.897 | +3,431 / +6,055 / +6,467 | [+229,+12,712] (9,098) | 0.0217 | 0.98/0.98 | +17,889 | +57,843 | -19,335 | +2,219 | +6,448 | +10,310 | +5,042 |
| S_V8_ST | DEAD | G2,G3,G4,G5,G6,G7 | 0.976 | +979 / +478 / +881 | [-1,079,+2,033] (2,224) | 0.2731 | 0.96/0.77 | +1,501 | +30,554 | -14,225 | -558 | -1,590 | +16,853 | -7,005 |
| S_V8_HM | DEAD | G2,G3,G6 | 0.969 | +1,010 / +941 / +492 | [-143,+2,044] (1,566) | 0.0433 | 0.97/0.99 | +839 | +3,610 | -399 | -138 | -2,334 | -9,918 | +6,738 |
| S_V8_WT | DEAD | G3,G4,G6,G7 | 0.987 | +455 / +835 / +443 | [+48,+1,674] (1,183) | 0.0182 | 0.77/0.89 | +934 | +5,459 | -2,577 | +344 | -513 | -727 | +698 |
| S_V8_KB | DEAD | G1,G3,G4,G5,G6,G7 | 0.980 | -1,135 / +1,068 / +543 | [+142,+2,029] (1,374) | 0.0122 | 0.20/1.00 | +1,850 | +12,371 | -4,576 | +2,345 | +5,621 | +28,563 | -13,106 |
| S_V8_SM | DEAD | G2,G3,G4,G5,G6,G7 | 0.987 | +256 / +46 / +283 | [-898,+1,022] (1,376) | 0.4608 | 0.70/0.26 | +1,689 | +7,917 | -4,721 | -226 | +867 | +4,411 | -2,860 |
| S_V8_PB | DEAD | G2,G3,G4,G6,G7 | 0.981 | +103 / +891 / +592 | [-10,+1,813] (1,302) | 0.0263 | 0.73/1.00 | +2,119 | +13,269 | -5,517 | +779 | +1,784 | +11,834 | -4,760 |
| D_V8 | DEAD | G3,G4,G5,G6,G7 | 0.871 | +808 / +3,484 / +1,315 | [+418,+6,621] (4,549) | 0.0137 | 0.71/0.99 | +6,411 | +42,928 | -15,705 | +2,586 | +4,194 | +33,624 | -11,436 |
| D_V4 | DEAD | G2,G3,G4,G6,G7 | 0.886 | +1,481 / +3,370 / +2,821 | [-583,+7,161] (5,648) | 0.0490 | 0.81/0.95 | +6,573 | +76,809 | -45,799 | +1,577 | +2,571 | +58,519 | -36,911 |
| D_V8_c0 | DEAD | G3,G4,G5,G6,G7 | 0.871 | +714 / +3,382 / +1,355 | [+328,+6,525] (4,514) | 0.0154 | 0.76/0.97 | +6,387 | +46,228 | -15,509 | +2,542 | +4,462 | +37,792 | -11,864 |
| D_V8_c2 | DEAD | G3,G4,G5,G6,G7 | 0.871 | +902 / +3,586 / +1,274 | [+452,+6,750] (4,614) | 0.0129 | 0.70/0.98 | +6,446 | +39,628 | -15,900 | +2,641 | +3,927 | +29,526 | -10,966 |
| D_V8_AGG | DEAD | G3,G4,G5,G6,G7 | 0.865 | +958 / +4,933 / +2,675 | [+81,+10,096] (7,257) | 0.0232 | 0.74/0.91 | +15,136 | +108,059 | -3,271 | +3,771 | +12,228 | +91,390 | +1,424 |
| D_V8_KB | DEAD | G1,G3,G4,G5,G6,G7 | 0.971 | -814 / +1,355 / +203 | [+234,+2,517] (1,634) | 0.0083 | 0.24/1.00 | +1,229 | +12,608 | -3,619 | +2,242 | +3,395 | +21,398 | -7,643 |
| D_V8_SM | DEAD | G2,G3,G4,G5,G6,G7 | 0.980 | +484 / +215 / +50 | [-701,+1,167] (1,345) | 0.3238 | 0.68/0.25 | +1,235 | +10,864 | -4,381 | -284 | -12 | +5,815 | -2,055 |
| D_V8_PE | DEAD | G3,G4,G6,G7 | 0.972 | +383 / +1,120 / +253 | [+220,+2,050] (1,305) | 0.0072 | 0.83/1.00 | +2,461 | +12,403 | -4,685 | +716 | +1,459 | +8,382 | -2,836 |
| D_V8_MV | LEAD | G2,G4,G5,G6 | 0.982 | +445 / +21 / +76 | [-868,+872] (1,241) | 0.4762 | 0.96/0.80 | -82 | -16,970 | +11,494 | -435 | -1,214 | -21,303 | +13,457 |
| D_V8_DN | DEAD | G2,G3,G4,G5,G6,G7 | 0.966 | +416 / +386 / +602 | [-1,127,+1,795] (2,138) | 0.3020 | 0.47/0.52 | +1,077 | +20,926 | -13,029 | -72 | -9 | +16,246 | -10,821 |

## Full tables, primary cells and controls


**S_V8** (c_LM 1.136, c_MM 1.091, raw average lots x0.880). Base = unscaled target; weekly $.

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD [CI] | d maxDD | d worst | d Sharpe | placebo rank mean / SD / maxDD / worst (pooled; shift, perm for mean) |
|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -3,664 [-8,308,+896] (6,612) | -16,424 [-21,127,-11,437] | -86,639 | +24,923 | +0.117 |  |
|  |  |  | LM | +1,845 [-1,126,+4,806] (4,208) | -799 [-4,951,+3,379] | -33,396 | -13,436 | +0.117 | 0.95 / 0.68 / 0.80 / 0.31 (0.97, 0.94) |
|  |  |  | MM | -0 [-3,211,+3,096] (4,553) | -6,031 [-10,166,-1,715] | -51,226 | -590 | +0.117 | 0.37 / 0.95 / 0.90 / 0.53 (0.34, 0.40) |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -1,497 [-4,974,+1,850] (4,940) | -7,990 [-12,253,-3,436] | -354 | +6,801 | +0.064 |  |
|  |  |  | LM | +4,737 [+949,+8,624] (5,583) | +10,117 [+4,890,+15,328] | +81,427 | -35,645 | +0.064 | 1.00 / 0.01 / 0.05 / 0.10 (0.99, 1.00) |
|  |  |  | MM | +2,649 [-478,+5,817] (4,526) | +4,053 [-601,+8,909] | +54,039 | -21,430 | +0.064 | 0.87 / 0.26 / 0.14 / 0.26 (0.85, 0.89) |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | +696 [-986,+2,425] (2,509) | +591 [-1,789,+3,209] | +0 | +0 | +0.037 |  |
|  |  |  | LM | +3,597 [-1,320,+8,735] (7,270) | +16,026 [+11,947,+20,050] | +75,303 | -21,416 | +0.037 | 0.99 / 0.01 / 0.01 / 0.05 (0.98, 1.00) |
|  |  |  | MM | +2,626 [-896,+6,394] (5,273) | +10,857 [+7,484,+14,344] | +50,085 | -14,244 | +0.037 | 0.95 / 0.14 / 0.63 / 0.64 (0.95, 0.96) |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -2,652 [-5,648,+262] (4,215) | -12,170 [-15,649,-8,586] | -354 | +6,801 | +0.084 |  |
|  |  |  | LM | +3,243 [+785,+5,769] (3,483) | +4,728 [+988,+8,469] | +81,427 | -35,645 | +0.084 | 1.00 / 0.03 / 0.05 / 0.14 (1.00, 1.00) |
|  |  |  | MM | +1,269 [-1,051,+3,556] (3,241) | -931 [-4,471,+2,653] | +54,039 | -21,430 | +0.084 | 0.87 / 0.69 / 0.14 / 0.36 (0.85, 0.89) |

By year (summed weekly deltas; weeks): LM {2024: +155,607 (49 wk), 2025: +218,573 (52 wk), 2026: +86,285 (41 wk)}; MM {2024: +71,152, 2025: +97,003, 2026: +11,996}; 2023 X weeks: LM +95,910 (39 wk).


**S_V4** (c_LM 1.112, c_MM 1.010, raw average lots x0.899). Base = unscaled target; weekly $.

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD [CI] | d maxDD | d worst | d Sharpe | placebo rank mean / SD / maxDD / worst (pooled; shift, perm for mean) |
|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -449 [-5,625,+4,827] (7,538) | -13,106 [-19,591,-6,080] | -95,941 | +32,505 | +0.242 |  |
|  |  |  | LM | +4,411 [-21,+9,118] (6,552) | +95 [-6,214,+6,708] | -53,126 | +1,758 | +0.241 | 0.99 / 0.57 / 0.92 / 0.62 (1.00, 0.98) |
|  |  |  | MM | +0 [-5,036,+5,129] (7,350) | -11,888 [-18,300,-4,876] | -91,998 | +29,673 | +0.242 | 0.72 / 0.98 / 0.98 / 0.85 (0.71, 0.74) |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | -1,939 [-5,896,+1,804] (5,513) | -3,175 [-9,060,+2,867] | +50,439 | -46,376 | -0.046 |  |
|  |  |  | LM | +3,136 [-1,946,+8,004] (7,058) | +12,275 [+4,809,+19,988] | +123,574 | -87,377 | -0.046 | 0.95 / 0.00 / 0.03 / 0.04 (0.94, 0.95) |
|  |  |  | MM | -1,471 [-5,394,+2,230] (5,466) | -1,752 [-7,756,+4,364] | +57,167 | -50,146 | -0.046 | 0.35 / 0.67 / 0.17 / 0.13 (0.39, 0.31) |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | +3,831 [-313,+8,620] (6,365) | +3,646 [-3,727,+11,396] | +0 | -5,507 | +0.196 |  |
|  |  |  | LM | +6,533 [+414,+13,702] (9,576) | +16,662 [+8,075,+25,825] | +62,030 | -23,766 | +0.194 | 1.00 / 0.02 / 0.00 / 0.16 (1.00, 1.00) |
|  |  |  | MM | +4,081 [-103,+8,985] (6,536) | +4,846 [-2,627,+12,699] | +5,713 | -7,188 | +0.196 | 0.96 / 0.44 / 0.90 / 0.83 (0.95, 0.96) |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -1,165 [-4,520,+2,149] (4,766) | -8,023 [-12,867,-3,203] | +50,439 | -46,376 | +0.087 |  |
|  |  |  | LM | +3,832 [+494,+7,342] (4,842) | +6,338 [+914,+11,787] | +123,574 | -87,377 | +0.086 | 1.00 / 0.03 / 0.03 / 0.05 (1.00, 1.00) |
|  |  |  | MM | -704 [-3,977,+2,548] (4,673) | -6,700 [-11,580,-1,828] | +57,167 | -50,146 | +0.087 | 0.35 / 0.88 / 0.19 / 0.22 (0.39, 0.31) |

By year (summed weekly deltas; weeks): LM {2024: +364,438 (49 wk), 2025: +129,027 (52 wk), 2026: +50,617 (41 wk)}; MM {2024: +154,949, 2025: -139,381, 2026: -115,602}; 2023 X weeks: LM +177,183 (39 wk).


**S_V8_AGG** (c_LM 1.115, c_MM 1.034, raw average lots x0.897). Base = unscaled target; weekly $.

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD [CI] | d maxDD | d worst | d Sharpe | placebo rank mean / SD / maxDD / worst (pooled; shift, perm for mean) |
|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 44,127 / 131,184 / 477,701 / -306,664 | raw | -1,470 [-5,654,+2,594] (5,945) | -13,703 [-18,099,-9,146] | -93,374 | +39,501 | +0.193 |  |
|  |  |  | LM | +3,431 [+452,+6,320] (4,187) | -206 [-4,139,+3,559] | -49,218 | +8,806 | +0.193 | 0.98 / 0.63 / 0.88 / 0.66 (1.00, 0.97) |
|  |  |  | MM | -0 [-3,639,+3,442] (5,100) | -9,655 [-13,791,-5,466] | -80,131 | +30,294 | +0.193 | 0.40 / 0.99 / 0.95 / 0.85 (0.42, 0.38) |
| HOLD | 68 | 47,279 / 140,987 / 601,016 / -318,557 | raw | +571 [-3,713,+5,174] (6,452) | +1,539 [-5,677,+8,985] | -10,054 | +15,486 | +0.003 |  |
|  |  |  | LM | +6,055 [+229,+12,712] (9,098) | +17,889 [+9,242,+26,531] | +57,843 | -19,335 | +0.003 | 0.98 / 0.02 / 0.20 / 0.29 (0.97, 0.99) |
|  |  |  | MM | +2,219 [-2,267,+7,197] (6,896) | +6,448 [-1,103,+14,138] | +10,310 | +5,042 | +0.003 | 0.69 / 0.28 / 0.45 / 0.52 (0.67, 0.70) |
| 2023-04..2024-01 | 44 | 20,616 / 112,784 / 553,090 / -157,300 | raw | +3,688 [+92,+8,429] (6,138) | +7,589 [+1,615,+15,026] | +0 | +0 | +0.138 |  |
|  |  |  | LM | +6,467 [-336,+14,237] (10,579) | +21,395 [+13,831,+30,231] | +63,546 | -18,073 | +0.137 | 0.99 / 0.00 / 0.01 / 0.14 (0.99, 1.00) |
|  |  |  | MM | +4,526 [+104,+10,030] (7,274) | +11,737 [+5,371,+19,619] | +19,059 | -5,420 | +0.138 | 0.98 / 0.12 / 0.57 / 0.65 (0.96, 1.00) |
| WF | 142 | 45,947 / 136,281 / 601,016 / -318,557 | raw | -503 [-3,493,+2,592] (4,401) | -5,977 [-10,755,-925] | -10,054 | +15,486 | +0.084 |  |
|  |  |  | LM | +4,712 [+1,467,+8,237] (4,877) | +8,981 [+3,689,+14,591] | +57,843 | -19,335 | +0.084 | 1.00 / 0.03 / 0.20 / 0.47 (1.00, 1.00) |
|  |  |  | MM | +1,062 [-1,779,+4,084] (4,256) | -1,488 [-6,380,+3,651] | +10,310 | +5,042 | +0.084 | 0.69 / 0.70 / 0.45 / 0.73 (0.67, 0.70) |

By year (summed weekly deltas; weeks): LM {2024: +190,668 (49 wk), 2025: +326,015 (52 wk), 2026: +152,403 (41 wk)}; MM {2024: +36,313, 2025: +100,463, 2026: +14,083}; 2023 X weeks: LM +195,315 (39 wk).


**D_V8** (c_LM 1.149, c_MM 1.125, raw average lots x0.871). Base = unscaled target; weekly $.

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD [CI] | d maxDD | d worst | d Sharpe | placebo rank mean / SD / maxDD / worst (pooled; shift, perm for mean) |
|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 39,156 / 90,848 / 318,164 / -221,819 | raw | -4,172 [-7,676,-739] (4,975) | -12,027 [-15,626,-7,993] | -49,338 | +36,163 | +0.093 |  |
|  |  |  | LM | +808 [-1,467,+3,212] (3,351) | +149 [-3,085,+3,908] | +659 | -1,335 | +0.059 | 0.71 / 0.61 / 0.43 / 0.49 (0.74, 0.67) |
|  |  |  | MM | -0 [-2,314,+2,387] (3,359) | -1,827 [-4,975,+1,905] | -7,568 | +4,878 | +0.064 | 0.26 / 0.73 / 0.52 / 0.53 (0.29, 0.23) |
| HOLD | 68 | 43,538 / 101,055 / 424,659 / -188,005 | raw | -2,338 [-5,701,+593] (4,554) | -7,175 [-11,640,-3,052] | -15,146 | +10,787 | +0.058 |  |
|  |  |  | LM | +3,484 [+418,+6,621] (4,549) | +6,411 [+2,084,+10,540] | +42,928 | -15,705 | +0.048 | 0.99 / 0.11 / 0.16 / 0.21 (0.99, 0.99) |
|  |  |  | MM | +2,586 [-276,+5,465] (4,214) | +4,194 [-86,+8,271] | +33,624 | -11,436 | +0.053 | 0.86 / 0.27 / 0.24 / 0.27 (0.79, 0.94) |
| 2023-04..2024-01 | 44 | 3,609 / 71,272 / 436,812 / -178,268 | raw | +710 [-178,+1,747] (1,411) | +1,016 [-441,+2,527] | +4,999 | +0 | +0.066 |  |
|  |  |  | LM | +1,315 [-2,173,+4,922] (5,175) | +11,775 [+8,599,+14,522] | +72,042 | -26,574 | +0.062 | 0.99 / 0.02 / 0.07 / 0.01 (0.98, 1.00) |
|  |  |  | MM | +1,218 [-1,784,+4,366] (4,472) | +10,041 [+7,194,+12,510] | +61,216 | -22,293 | +0.063 | 0.99 / 0.06 / 0.24 / 0.25 (0.98, 0.99) |
| WF | 142 | 41,530 / 95,708 / 424,659 / -221,819 | raw | -3,323 [-5,751,-1,025] (3,409) | -9,508 [-12,540,-6,517] | -15,146 | +36,163 | +0.067 |  |
|  |  |  | LM | +2,095 [+171,+4,088] (2,809) | +3,335 [+520,+6,257] | +42,928 | -1,335 | +0.047 | 0.98 / 0.12 / 0.16 / 0.50 (0.98, 0.99) |
|  |  |  | MM | +1,238 [-638,+3,129] (2,691) | +1,245 [-1,548,+4,137] | +33,624 | +4,878 | +0.052 | 0.86 / 0.46 / 0.24 / 0.54 (0.79, 0.94) |

By year (summed weekly deltas; weeks): LM {2024: +55,398 (49 wk), 2025: +227,640 (52 wk), 2026: +14,494 (41 wk)}; MM {2024: +13,122, 2025: +184,779, 2026: -22,070}; 2023 X weeks: LM +13,397 (39 wk).


**D_V4** (c_LM 1.129, c_MM 1.086, raw average lots x0.886). Base = unscaled target; weekly $.

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD [CI] | d maxDD | d worst | d Sharpe | placebo rank mean / SD / maxDD / worst (pooled; shift, perm for mean) |
|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 39,156 / 90,848 / 318,164 / -221,819 | raw | -3,018 [-7,073,+1,050] (5,839) | -11,787 [-16,791,-6,774] | -47,443 | +58,593 | +0.188 |  |
|  |  |  | LM | +1,481 [-1,841,+4,798] (4,702) | -1,397 [-5,743,+3,006] | -6,869 | +31,968 | +0.168 | 0.81 / 0.83 / 0.49 / 0.77 (0.78, 0.84) |
|  |  |  | MM | -0 [-3,439,+3,412] (4,866) | -4,836 [-9,300,-331] | -20,486 | +40,950 | +0.175 | 0.24 / 0.93 / 0.58 / 0.82 (0.22, 0.27) |
| HOLD | 68 | 43,538 / 101,055 / 424,659 / -188,005 | raw | -1,986 [-5,817,+1,517] (5,263) | -5,538 [-11,177,-276] | +21,286 | -19,034 | +0.030 |  |
|  |  |  | LM | +3,370 [-583,+7,161] (5,648) | +6,573 [+765,+12,212] | +76,809 | -45,799 | +0.036 | 0.95 / 0.12 / 0.06 / 0.03 (0.95, 0.95) |
|  |  |  | MM | +1,577 [-2,102,+5,034] (5,173) | +2,571 [-3,126,+7,996] | +58,519 | -36,911 | +0.033 | 0.69 / 0.43 / 0.13 / 0.07 (0.67, 0.71) |
| 2023-04..2024-01 | 44 | 3,609 / 71,272 / 436,812 / -178,268 | raw | +2,118 [+297,+4,289] (2,941) | +3,639 [+765,+6,660] | -5,521 | -1,475 | +0.186 |  |
|  |  |  | LM | +2,821 [-1,229,+7,253] (6,211) | +13,291 [+8,937,+17,308] | +51,211 | -24,675 | +0.183 | 1.00 / 0.00 / 0.20 / 0.15 (1.00, 1.00) |
|  |  |  | MM | +2,589 [-601,+6,160] (4,995) | +10,085 [+6,282,+13,692] | +32,305 | -16,970 | +0.184 | 0.99 / 0.07 / 0.29 / 0.26 (0.99, 0.99) |
| WF | 142 | 41,530 / 95,708 / 424,659 / -221,819 | raw | -2,545 [-5,337,+175] (3,970) | -8,576 [-12,572,-4,830] | +21,286 | +14,779 | +0.097 |  |
|  |  |  | LM | +2,396 [-140,+4,940] (3,658) | +2,648 [-1,227,+6,399] | +76,809 | -11,986 | +0.091 | 0.97 / 0.24 / 0.07 / 0.31 (0.97, 0.97) |
|  |  |  | MM | +755 [-1,689,+3,181] (3,557) | -1,064 [-4,882,+2,648] | +58,519 | -3,097 | +0.093 | 0.69 / 0.67 / 0.13 / 0.45 (0.67, 0.71) |

By year (summed weekly deltas; weeks): LM {2024: +111,026 (49 wk), 2025: +203,228 (52 wk), 2026: +25,964 (41 wk)}; MM {2024: +33,221, 2025: +126,439, 2026: -52,442}; 2023 X weeks: LM +59,643 (39 wk).


**D_V8_AGG** (c_LM 1.156, c_MM 1.128, raw average lots x0.865). Base = unscaled target; weekly $.

| window | wk | base mean / SD / maxDD / worst | basis | d mean [CI iid] (MDE) | d SD [CI] | d maxDD | d worst | d Sharpe | placebo rank mean / SD / maxDD / worst (pooled; shift, perm for mean) |
|---|---|---|---|---|---|---|---|---|---|
| PRE | 75 | 39,156 / 90,848 / 318,164 / -221,819 | raw | -4,267 [-7,852,-665] (5,152) | -11,868 [-15,823,-7,833] | -48,827 | +44,773 | +0.077 |  |
|  |  |  | LM | +958 [-1,560,+3,550] (3,661) | +908 [-2,800,+4,548] | +4,187 | +6,299 | +0.045 | 0.74 / 0.39 / 0.33 / 0.42 (0.75, 0.73) |
|  |  |  | MM | -0 [-2,535,+2,493] (3,635) | -1,426 [-5,035,+2,186] | -5,650 | +13,495 | +0.050 | 0.09 / 0.62 / 0.45 / 0.52 (0.10, 0.09) |
| HOLD | 68 | 43,538 / 101,055 / 424,659 / -188,005 | raw | -1,283 [-4,449,+2,014] (4,559) | -970 [-5,651,+3,858] | +11,391 | +22,606 | -0.062 |  |
|  |  |  | LM | +4,933 [+81,+10,096] (7,257) | +15,136 [+9,517,+20,499] | +108,059 | -3,271 | -0.099 | 0.91 / 0.03 / 0.02 / 0.39 (0.83, 0.99) |
|  |  |  | MM | +3,771 [-557,+8,389] (6,509) | +12,228 [+6,831,+17,453] | +91,390 | +1,424 | -0.095 | 0.85 / 0.08 / 0.07 / 0.48 (0.79, 0.91) |
| 2023-04..2024-01 | 44 | 3,609 / 71,272 / 436,812 / -178,268 | raw | +1,862 [+205,+3,849] (2,686) | +2,240 [-639,+5,332] | +2,986 | +0 | +0.172 |  |
|  |  |  | LM | +2,675 [-1,548,+7,201] (6,388) | +13,709 [+9,158,+17,952] | +72,933 | -27,851 | +0.168 | 1.00 / 0.00 / 0.07 / 0.03 (1.00, 1.00) |
|  |  |  | MM | +2,528 [-1,165,+6,547] (5,588) | +11,628 [+7,435,+15,586] | +60,211 | -22,798 | +0.169 | 1.00 / 0.05 / 0.16 / 0.12 (1.00, 1.00) |
| WF | 142 | 41,530 / 95,708 / 424,659 / -221,819 | raw | -2,868 [-5,313,-446] (3,492) | -6,129 [-9,506,-2,656] | +11,391 | +44,773 | -0.017 |  |
|  |  |  | LM | +2,868 [+153,+5,679] (3,990) | +8,316 [+4,616,+12,095] | +108,059 | +6,299 | -0.051 | 0.95 / 0.04 / 0.02 / 0.52 (0.91, 0.99) |
|  |  |  | MM | +1,806 [-680,+4,382] (3,674) | +5,694 [+2,130,+9,388] | +91,390 | +13,495 | -0.047 | 0.85 / 0.17 / 0.07 / 0.64 (0.79, 0.91) |

By year (summed weekly deltas; weeks): LM {2024: +20,057 (49 wk), 2025: +254,877 (52 wk), 2026: +132,362 (41 wk)}; MM {2024: -28,376, 2025: +203,235, 2026: +81,582}; 2023 X weeks: LM +77,832 (39 wk).

## Deviations and caveats (none soften a gate)
1. Per-book exact locks only: the DS2/DS3 stack definition has no cross-book lock (the "shared lock" is the shared 2R/50%/12R parameter set); lock interplay across books is therefore not modelled beyond that. The multiplier scaling uses lock homogeneity and week containment (verified, not re-run per week). Fractional lots; live rounding not modelled.
2. The s113 sweep-cost surface starts at 14 lots (clamped below) and no book exceeds 14 lots under the rule (max raw HOLD lots: ST 11.9, HM 10.9, WT 8.1, KB 5.3, SM 9.4, PB 6.8; DS5 DN 9.1), so the size-dependent cost is INACTIVE on STACK: S_V8, S_V8_c0, S_V8_c2 are identical to the dollar (their placebo ranks differ only because some placebo draws exceed 14 lots). Post-hoc (not gated, not in the prereg) the surface was linearly extrapolated below 14 lots (14->21 slope): S_V8 HOLD LM d_mean +4,300 (vs +4,737), maxDD +84,460, worst -36,269; no verdict moves.
3. DS5: KB/SM/PE sizes use the same surface (inactive); only DN carries a lot-dependent cost, the measured MB lot grid (clamped to 5-14 lots). The MB series are the D3DN outputs, whose slippage tables pool all trades including the HOLD window (no cell selected on them).
4. Cost sensitivities c0/c2 therefore say little (DS5: c0 HOLD +3,382, c2 +3,586 vs +3,484); the lever the lead asked for (size-dependent cost) does not bind at these sizes. A real 1-lot walk costs +0.85 pt (DS3_DN_STOPFILL), i.e. part of the fill cost is lot-independent and is already inside every series.
5. Mean-matched = my reading of "mean-matched (average lots)": the rule scaled so its PRE weekly mean equals the base's; reported next to lot-matched (average lots equal) and raw. d_Sharpe is scale-invariant, so it is identical across the three bases.
6. G6 and G7 are additional gates in the prereg (stricter than D3SZR's G1-G5). Best-of-F uses F = 21 (all cells, including descriptive per-book ones).
7. Looks: PRE-stage printed d_mean (WFPRE) for all 21 cells; a plumbing test with a random (non-registered) multiplier path printed S_V8 WFPRE numbers (not rule results). Four holdout logs were written (two per group, HOLD and SPAN2) and HOLD/X/WF were computed once, in one run, after them. The prereg's MDE field for each cell is an order-of-magnitude statement from D3SZR (not computed). The prereg tier text says "CONFIRMED ... labelled best-of-F"; no cell reached CONFIRMED.
8. Days before 2023-04-01 have <8 weeks of weight history (weight = 1 x c, ~25,000x) and were overwritten with the first valid weight vector; they enter no window or rule history except the AGG signal. The vol-scale signal uses unweighted nominal-lot book P&L (not the weighted contribution), a prereg choice.
9. Prior holdout contact (disclosed): the regenerated KB/SM/ST/HM/WT/PB rows and the DN MB series were already scored on HOLD by D3BK, D3DN and D3SL, no parameter here was chosen on them; the rule parameters (8 and 4 weeks, 0.5-2 clip, 20-week warm-up) come from D3SZR, whose HOLD read selected nothing for the 8-week (post-HOLD reading, now tested out of that sample only to the extent that the PRE window and the 2023 span are, and 2023-04..2024-01 was in D3SZR's diagnostic use). The 2023 span is therefore only a weak second holdout for the 8-week rule (about a quarter of the span is warm-up).
10. Not run: the exact lock engine with per-row fractional lots on every week (replaced by the verified homogeneity identity); direct L2 replay (this is a sizing track on existing rows); corepool slots (single-process jobs of about 1 minute each, no multi-worker load).
11. UNTOUCHED data not read; no downloads; no deletions; no credentials or account numbers in any new file.

