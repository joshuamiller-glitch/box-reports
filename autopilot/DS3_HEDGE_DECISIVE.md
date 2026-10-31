# DS3_HEDGE_DECISIVE - the decisive test of the two hedge leads (C3, 2026-11-01 overnight). Frozen definitions, post-hoc leads, SHADOW ONLY, no PASS

Prereg `l2vast/ds3/prereg/HEDGE_DECISIVE_prereg.md` sha256 `4a9bcb8b27eefef25f7fdb484741c826fbbc22117807c41164943860c2a3e456` (in DECISIONS.md before scoring; dead_lookup: S1 = EXACT HEDGE1 cell, i.e. a frozen-definition re-test of an already-scored post-hoc lead, not a new cell). Code `l2vast/ds3/code/hedge_decisive/` (imports C1's `code/hedge/` unchanged), results `l2vast/ds3/out/hedge_decisive/`. Masks capped 20260206, UNTOUCHED never read. Stack = Sunday composite COMP|off (one-convention engine, live lots, 149 weeks; ALL maxDD 241.2k is the single PRE episode). Units $k unless stated; M = measured fills. **Integrity:** C1 chose both candidates after seeing PRE, X', ALL and L6M; L6M and HOLD were already read, so they are a consistency look here, NOT a fresh holdout; PRE+X' is the selection window and every PRE/X' number is in-sample for the choice. Nothing here is a PASS.

## Page 1 - the table

| sleeve | stack maxDD $k before→after by window [95% stationary-bootstrap CI of the change] | stack worst-20 $k before→after (PRE · X' · ALL [CI ALL]) | matched-placebo rank (1,000 draws): dMaxDD ALL · PRE · X' / dWorst20 ALL | LOEO survives (top-5 episodes) | RISK-KEEP | D7 spec |
|---|---|---|---|---|---|---|
| S1 prior-VA 80% rule (E: X40, target opposite edge), 3 NQ lots | L6M 22.9→22.9 [-2.9, 2.6] · HOLD 97.0→95.3 [-3.8, 1.0] · PRE 241.2→226.3 [-39.8, 11.3] · X' 120.5→106.9 [-28.3, 9.5] · ALL 241.2→226.3 [-36.8, 8.3] | -875.2→-868.8 · -419.6→-414.9 · -1098.1→-1089.3 [-32.3, 42.6] | 84% · 84% · 94% / 90%  (OL-matched 73% · 73% · 82% / 70%) | 0/5 (sign kept 5/5; cut and tail kept 3/5) | **NO** (fails G1; G4; G5; G6; G7; G8) | section 8 (S1) |
| S2 chop-day regime stack (tag 10:30; trend books x0.5 after 10:30 + B z1.5 market fade T30/S30 at 3 lots) | L6M 22.9→22.9 [-1.8, 0.6] · HOLD 97.0→97.0 [-1.8, 0.6] · PRE 241.2→231.6 [-22.3, 8.7] · X' 120.5→123.0 [-8.4, 6.7] · ALL 241.2→231.6 [-19.0, 7.7] | -875.2→-870.0 · -419.6→-414.9 · -1098.1→-1085.8 [-0.4, 25.5] | 87% · 87% · 43% / 84% | 0/5 (sign kept 4/5; cut and tail kept 4/5) | **NO** (fails G1; G4; G5; G6; G7; G8) | section 8 (S2) |

Reading the table: the CI is the 95% interval of the CHANGE (after minus before; negative = maxDD cut) from a stationary bootstrap over weeks (mean block 4 weeks, 4,000 resamples, same weeks in both series); every maxDD CI spans zero (section 3). Worst-20 CI is for ALL. Placebo rank = share of 1,000 matched random-day draws (same trade count, direction mix, weekday x vol tercile, entry bar; S2: random tags in the same strata with the halving re-run through the engine) whose change is WORSE than the real one; the bar is 95%. Gates that fail are named in section 7.

**Plain sentence.** Neither lead is a hedge. The prior-VA 80% rule cuts the stack's PRE maxDD 6.2% and X' 11.3% at 3 lots (ALL 241.2→226.3k), far below the 20% bar; the bootstrap CI of that change is [-39.8, 11.3] in PRE and [-28.3, 9.5] in X', both containing zero; against 1,000 matched random days the real change ranks 84% (ALL/PRE) and 94% (X'), under 95%; the ALL hedge is PRE's single episode. The chop-day regime stack cuts ALL maxDD 4.0% (241.2→231.6k) but deepens X' by 2.0%, ranks 87% against 1,000 matched random tags, and its tail improvement is 12.3k on 1,098k. With the deepest episode removed, S1's cut is 6.7% of the 156k remainder and S2 deepens it 0.9%; with all five top episodes removed both sleeves deepen the maxDD. The one conditional result that survives a selection correction is the S2 fade being better in the stack's worst weeks (section 5), but its size is 12k on a 1,098k tail and 0.6-2.8k on maxDD at 1-5 lots.

## 1. Frozen definitions (as C1 had them; nothing re-tuned)
- **S1** = C1 cell `E|va80|X40|tgedge` (DS3_HEDGE_SIDE section 6, spec E): prior RTH-day 70% value area, open outside it, first 1-min close back inside (09:35-13:00), market toward the opposite edge, stop 40 beyond the re-entry edge, target the opposite edge (min 8 pts), flat 15:50; 235 filled trades on the 149 engine weeks; 3 NQ lots.
- **S2** = C1 chop-day book: tag at 10:30 (first-hour range < 0.6 x 20-day median AND 5-min ER < 0.3; 52 tag days), trend rows entering at or after 10:30 on tag days get the engine ER multiplier x0.5, plus the B z1.5 market VWAP-band fade (T30/S30, flat 15:50) at 3 lots on tag days only. The post-hoc LOOSE tag is not tested.
- Both are measured against COMP|off, M fills; LIVE-CAL repeated where it differs. Selection window PRE+X'; HOLD/L6M are a consistency look (already seen by C1).

## 2. Stricter placebo (b): random days matched on weekday x vol tercile (+ same entry bar, side, stop/target distance, exit bar)
Rank = share of draws whose change is worse than the real one (bar 95%). Draws: 1,000 for the M headline and for LIVE-CAL; S2 1,000 (engine re-run each draw). `excess w20` = change in worst-20 minus what the sleeve's own all-weeks mean would give alone (3 lots x 20 x weekly mean).

| sleeve / placebo | basis | n trades | dMaxDD ALL (=PRE) | dMaxDD X' | dMaxDD L6M | dW20 ALL | dW20 PRE | dW20 X' | excess W20 ALL | excess W20 PRE | excess W20 X' | own mean ALL (rank) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S1 matched random day | M | 235 | 84% (real -14.9k; plc mean 0.8k) | 94% (real -13.6k; plc mean 4.3k) | 64% (real 0.0k; plc mean 2.0k) | 90% (real 8.8k; plc mean -17.1k) | 80% (real 6.4k; plc mean -11.0k) | 83% (real 4.8k; plc mean -10.7k) | 66% | 38% | 75% | 99% |
| S1 OL-matched (opens outside VA, same side) | M | 235 | 73% (real -14.9k; plc mean -7.0k) | 82% (real -13.6k; plc mean -4.7k) | 72% (real 0.0k; plc mean 2.4k) | 70% (real 8.8k; plc mean -1.6k) | 51% (real 6.4k; plc mean 6.2k) | 79% (real 4.8k; plc mean -7.5k) | 43% | 19% | 77% | 96% |
| S1 matched random day | LIVE-CAL | 235 | 84% (real -14.4k; plc mean 1.5k) | 94% (real -13.3k; plc mean 5.0k) | 65% (real 0.0k; plc mean 2.1k) | 91% (real 7.2k; plc mean -19.0k) | 80% (real 4.8k; plc mean -12.8k) | 83% (real 3.5k; plc mean -12.3k) | 65% | 39% | 75% | 99% |
| S1 OL-matched | LIVE-CAL | 235 | 73% (real -14.4k; plc mean -6.5k) | 83% (real -13.3k; plc mean -4.2k) | 72% (real 0.0k; plc mean 2.5k) | 71% (real 7.2k; plc mean -3.4k) | 50% (real 4.8k; plc mean 4.6k) | 79% (real 3.5k; plc mean -8.9k) | 43% | 18% | 77% | 96% |
| S2 random tag, same count, weekday x vol-tercile strata of the real tag days (1000 draws) | M (=LC) | 52 tag days | 87% (real -9.6k; plc mean -0.4k, 5-95% -15.8..14.4k) | 43% (real 2.5k; plc mean 2.4k, 5-95% -10.4..15.9k) | 24% (real 0.0k; plc mean 0.7k, 5-95% -1.5..7.6k) | 84% (real 12.3k; plc mean -0.1k, 5-95% -22.8..21.2k) | 60% (real 5.2k; plc mean 3.2k, 5-95% -15.8..25.9k) | 66% (real 4.7k; plc mean -2.5k, 5-95% -29.1..17.7k) | n/a | n/a | n/a | 81% |

Reading: against the stricter placebo the real S1 change ranks below 95% on every maxDD column and on the excess worst-20 (the part not explained by the sleeve's own mean); its OWN MEAN does rank high (the sleeve earns more than a same-size same-direction same-time trade on a random day), which is the positive-mean lead C1 already reported, not a hedge. Requiring the open-location (OL-matched) lowers the ranks further, so the location is not what carries the PRE/X' cut. For S2 the real ALL change ranks 87% on maxDD and 84% on worst-20 (X' maxDD 43%); the placebo tags are drawn inside the same weekday x vol-tercile strata (the real tag days are all in the lowest vol tercile), so 13% of random low-vol tags with the same halving and a 3-lot VWAP-band fade cut the ALL maxDD at least as much. 

## 3. Stationary-bootstrap CIs (c): change after minus before, 3 lots; block 4 weeks (block 8 in the second line)
Worst-20 for PRE, X', ALL; worst-5 for L6M and HOLD (fewer than 20 losing weeks). P(better) = share of resamples in which the change is on the hedge side.
**S1 prior-VA 80% (3 lots)**

| window | dMaxDD [CI] P(better) | dMaxDD % [CI] | dWorst (20 or 5) [CI] P(better) | dSD [CI] | dCalmar [CI] | CI block 8: dMaxDD · dWorst |
|---|---|---|---|---|---|---|
| PRE (w20) | -14.9 [-39.8, 11.3] 83% | -6.2% [-15%, 8%] | 6.4 [-31.8, 55.5] 72% | -0.13 [-1.3, 1.2] | +0.011 [-0.011, +0.043] | [-34.8, 8.0] · [-28.9, 54.6] |
| X' (w20) | -13.6 [-28.3, 9.5] 77% | -11.3% [-18%, 11%] | 4.8 [-24.3, 29.7] 63% | 0.15 [-0.6, 1.0] | +0.011 [-0.016, +0.028] | [-29.2, 6.7] · [-23.4, 27.0] |
| HOLD (w5) | -1.7 [-3.8, 1.0] 71% | -1.7% [-8%, 2%] | 2.8 [-5.8, 6.8] 74% | 0.55 [-1.5, 2.4] | +0.021 [-0.031, +0.192] | [-2.8, 0.4] · [-6.1, 5.9] |
| L6M (w5) | 0.0 [-2.9, 2.6] 35% | 0.0% [-11%, 10%] | 1.7 [-7.9, 14.4] 60% | -0.20 [-2.6, 2.3] | +0.040 [-0.119, +0.378] | [-2.1, 0.6] · [-8.2, 11.9] |
| ALL (w20) | -14.9 [-36.8, 8.3] 87% | -6.2% [-15%, 6%] | 8.8 [-32.3, 42.6] 67% | 0.12 [-0.8, 1.1] | +0.010 [-0.004, +0.033] | [-37.1, 4.2] · [-33.1, 42.5] |

**S2 chop-day regime stack (3-lot fade)**

| window | dMaxDD [CI] P(better) | dMaxDD % [CI] | dWorst (20 or 5) [CI] P(better) | dSD [CI] | dCalmar [CI] | CI block 8: dMaxDD · dWorst |
|---|---|---|---|---|---|---|
| PRE (w20) | -9.6 [-22.3, 8.7] 53% | -4.0% [-9%, 5%] | 5.2 [-11.7, 22.2] 71% | -0.08 [-0.4, 0.2] | +0.005 [-0.008, +0.015] | [-22.7, 6.3] · [-8.4, 20.1] |
| X' (w20) | 2.5 [-8.4, 6.7] 42% | 2.0% [-8%, 6%] | 4.7 [-10.0, 20.0] 74% | -0.32 [-0.9, 0.2] | -0.001 [-0.006, +0.016] | [-6.9, 7.3] · [-8.9, 18.8] |
| HOLD (w5) | 0.0 [-1.8, 0.6] 4% | 0.0% [-2%, 1%] | 1.8 [-1.2, 3.6] 46% | -0.28 [-0.7, 0.1] | -0.006 [-0.048, +0.002] | [-0.0, 0.0] · [-1.2, 3.6] |
| L6M (w5) | 0.0 [-1.8, 0.6] 9% | 0.0% [-18%, 2%] | 1.2 [-1.2, 5.4] 67% | -0.51 [-0.9, -0.2] | -0.033 [-0.072, +0.753] | [-1.8, 0.0] · [-1.2, 4.7] |
| ALL (w20) | -9.6 [-19.0, 7.7] 51% | -4.0% [-8%, 4%] | 12.3 [-0.4, 25.5] 97% | -0.21 [-0.5, 0.0] | +0.004 [-0.007, +0.011] | [-19.1, 6.4] · [-0.8, 25.5] |

No maxDD interval excludes zero, in any window, for either sleeve or block length. The closest is S2's ALL worst-20 gain (CI just under zero at the low end, P(better) 97%), which is the fade's 8 chop-days inside 7 episodes; S2's L6M weekly SD interval is below zero (smaller SD, from the halving). Calmar intervals all contain zero.

## 4. Leave-one-episode-out (d): remove each of the stack's five deepest drawdown episodes (peak to trough weeks deleted from both series)
Episodes of the composite ALL weekly curve (depth $k, peak..trough ISO week): ep1 241k wk 202434..202440; ep2 156k wk 202411..202415; ep3 121k wk 202314..202320; ep4 97k wk 202528..202530; ep5 96k wk 202506..202509. Survives = maxDD cut and worst-20 improved and the cut is >= 10% of that removal's baseline.
**S1 prior-VA 80% (3 lots)**

| removed | span | maxDD before→after $k | cut % | worst-20 before→after $k | survives |
|---|---|---|---|---|---|
| none (ALL) |  | 241.2→226.3 | 6.2% | -1098.1→-1089.3 | no |
| ep1 depth 241k | wk 202434..202440 (7 wk) | 156.4→146.0 | 6.7% | -913.1→-911.7 | no |
| ep2 depth 156k | wk 202411..202415 (5 wk) | 241.2→226.3 | 6.2% | -984.4→-991.0 | no |
| ep3 depth 121k | wk 202314..202320 (7 wk) | 241.2→226.3 | 6.2% | -1059.0→-1053.9 | no |
| ep4 depth 97k | wk 202528..202530 (3 wk) | 241.2→226.3 | 6.2% | -1016.2→-1010.2 | no |
| ep5 depth 96k | wk 202506..202509 (4 wk) | 241.2→226.3 | 6.2% | -1082.2→-1082.5 | no |
| all top-5 |  | 79.6→88.1 | -10.7% | -602.6→-632.3 | no |

**S2 chop-day regime stack (3-lot fade)**

| removed | span | maxDD before→after $k | cut % | worst-20 before→after $k | survives |
|---|---|---|---|---|---|
| none (ALL) |  | 241.2→231.6 | 4.0% | -1098.1→-1085.8 | no |
| ep1 depth 241k | wk 202434..202440 (7 wk) | 156.4→157.8 | -0.9% | -913.1→-900.2 | no |
| ep2 depth 156k | wk 202411..202415 (5 wk) | 241.2→231.6 | 4.0% | -984.4→-970.1 | no |
| ep3 depth 121k | wk 202314..202320 (7 wk) | 241.2→231.6 | 4.0% | -1059.0→-1046.6 | no |
| ep4 depth 97k | wk 202528..202530 (3 wk) | 241.2→231.6 | 4.0% | -1016.2→-1003.9 | no |
| ep5 depth 96k | wk 202506..202509 (4 wk) | 241.2→231.6 | 4.0% | -1082.2→-1071.6 | no |
| all top-5 |  | 79.6→85.9 | -7.8% | -602.6→-589.9 | no |

Reading: ALL maxDD is ep1 (the PRE episode). When ep2-ep5 are removed the headline number is unchanged (the deepest episode still sets it), so those rows only test the tail. When ep1 itself is removed the remainder is a 156k drawdown and the cut shrinks (S1 6.7% with the tail +1.3k; S2 deeper by 0.9%). Removing all five leaves a 79.6k stack on which both sleeves DEEPEN maxDD (S1 +8.5k, S2 +6.2k) and worsen the worst-20.

## 5. Conditional (e): the sleeve in the stack's 20 worst weeks vs the others (ALL)
S1 per lot; S2 = the regime delta (stack with halving + 3-lot fade minus stack), weekly $. Independent episodes = clusters of the 20 worst weeks (gap > 2 weeks starts a new one). Circular-shift permutation: the sleeve's weekly series is rotated against the stack 10,000 times (keeps its autocorrelation); episode versions weight each episode once.

| sleeve | $/wk in worst-20 | $/wk elsewhere | difference [95% resample CI] | independent episodes (sizes) | p circular-shift (weeks) | p circular-shift (episode-weighted) | p episode-block placement | corr all / inside w20 | top week share of w20 P&L |
|---|---|---|---|---|---|---|---|---|---|
| S1 per lot | +343 | +294 | +49 [-703, +716] | 14 (1,1,1,1,1,4,1,2,1,1,2,1,1,2) | 0.339 | 0.507 | 0.510 | -0.06 / -0.04 | 44% |
| S2 regime delta (3-lot fade + halving) | +614 | -123 | +737 [+83, +1431] | 14 (1,1,1,1,1,4,1,2,1,1,2,1,1,2) | 0.075 | 0.040 | 0.028 | -0.13 / +0.08 | 35% |
| S2 fade alone, 3 lots on tag days | +238 | -21 | +259 [+110, +422] | 14 (1,1,1,1,1,4,1,2,1,1,2,1,1,2) | 0.000 | 0.000 | 0.002 | -0.06 / +0.41 | 25% |

**Selection correction (prereg addendum 1, Westfall-Young max-statistic over the cells C1 chose among).** Standardised statistic z = (sleeve mean in worst-20 minus elsewhere) / SE; same random circular shifts applied to all cells. S2 fade: the B z1.5 market T30 cell has z = 2.75, rank 1 of 18 B/C/D cells, unadjusted p 0.0000, **adjusted p 0.025** (all eight VWAP-band variants score z 2.2-2.75, so it is the state, not the cell; IB-edge and failed-breakout fades score 0.2-1.9). S1: E va80 X40 tgedge z = 0.08, rank 7 of 8 E cells, unadjusted p 0.34, adjusted p 0.89.

S1 is not better when the stack is worst (episode-weighted difference negative, p 0.5): its tail help is its own positive mean. S2 is different. The FADE ALONE is better in the stack's worst weeks (difference +259/wk, circular-shift p < 0.001, within-worst-20 corr +0.41, selection-corrected p 0.025 over the 18 cells, 14 independent episodes), and the tag itself is the user's own pre-set definition, not mined. That is a real conditional effect, and it is the first evidence in the hedge-side work that a sleeve pays when the stack loses. But its dollar size is small (52 trades in 3 years, 8 inside the worst-20 weeks, +14k at 3 lots on a 1,098k tail), the combined regime delta (halving + fade) has a week-level p of 0.075 because the halving costs P&L in the good chop days, and the prereg gate G8 (week-level circular-shift p < 0.05 for the regime stack) is not met. The evidence base is 8 days in 7 episodes.

**S1 prior-VA 80% (M fills)**

| lots | dMaxDD ALL (cut %) | dMaxDD PRE (cut %) | dMaxDD X' (cut %) | dMaxDD L6M | dMaxDD HOLD | dW20 ALL | dW20 per lot ALL | dMaxDD per lot ALL | dSD ALL | dCalmar ALL | dMean ALL $k/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | -5.0 (2.1%) | -5.0 (2.1%) | -4.5 (3.8%) | 0.0 | -0.6 | 5.0 | 5.0 | -5.0 | -0.10 | +0.0032 | +0.30 |
| 2 | -9.9 (4.1%) | -9.9 (4.1%) | -9.1 (7.5%) | 0.0 | -1.1 | 8.2 | 4.1 | -5.0 | -0.06 | +0.0066 | +0.60 |
| 3 | -14.9 (6.2%) | -14.9 (6.2%) | -13.6 (11.3%) | 0.0 | -1.7 | 8.8 | 2.9 | -5.0 | +0.12 | +0.0101 | +0.90 |
| 5 | -23.0 (9.5%) | -23.0 (9.5%) | -22.7 (18.8%) | 0.0 | -2.8 | -0.5 | -0.1 | -4.6 | +0.91 | +0.0166 | +1.50 |
| 10 | -36.3 (15.0%) | -36.3 (15.0%) | -45.3 (37.6%) | 0.0 | -5.6 | -40.1 | -4.0 | -3.6 | +5.16 | +0.0310 | +3.01 |

**S1 prior-VA 80% (LIVE-CAL fills)**

| lots | dMaxDD ALL (cut %) | dMaxDD PRE (cut %) | dMaxDD X' (cut %) | dMaxDD L6M | dMaxDD HOLD | dW20 ALL | dW20 per lot ALL | dMaxDD per lot ALL | dSD ALL | dCalmar ALL | dMean ALL $k/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | -4.8 (2.0%) | -4.8 (2.0%) | -4.4 (3.7%) | 0.0 | -0.5 | 4.5 | 4.5 | -4.8 | -0.10 | +0.0030 | +0.28 |
| 2 | -9.6 (4.0%) | -9.6 (4.0%) | -8.8 (7.3%) | 0.0 | -0.9 | 7.1 | 3.6 | -4.8 | -0.06 | +0.0062 | +0.55 |
| 3 | -14.4 (6.0%) | -14.4 (6.0%) | -13.3 (11.0%) | 0.0 | -1.4 | 7.2 | 2.4 | -4.8 | +0.12 | +0.0095 | +0.83 |
| 5 | -22.1 (9.2%) | -22.1 (9.2%) | -22.1 (18.3%) | 0.0 | -2.3 | -3.5 | -0.7 | -4.4 | +0.92 | +0.0156 | +1.38 |
| 10 | -34.5 (14.3%) | -34.5 (14.3%) | -44.2 (36.7%) | 0.0 | -4.5 | -46.9 | -4.7 | -3.4 | +5.19 | +0.0287 | +2.75 |

**S2 chop-day regime stack: lots of the fade, halving always on**

| lots | dMaxDD ALL (cut %) | dMaxDD PRE (cut %) | dMaxDD X' (cut %) | dMaxDD L6M | dMaxDD HOLD | dW20 ALL | dW20 per lot ALL | dMaxDD per lot ALL | dSD ALL | dCalmar ALL | dMean ALL $k/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | -8.5 (3.5%) | -8.5 (3.5%) | 3.3 (-2.7%) | 0.0 | 0.0 | 2.8 | 2.8 | -8.5 | -0.18 | +0.0032 | -0.05 |
| 2 | -9.1 (3.8%) | -9.1 (3.8%) | 2.9 (-2.4%) | 0.0 | 0.0 | 7.5 | 3.8 | -4.5 | -0.20 | +0.0034 | -0.04 |
| 3 | -9.6 (4.0%) | -9.6 (4.0%) | 2.5 (-2.0%) | 0.0 | 0.0 | 12.3 | 4.1 | -3.2 | -0.21 | +0.0037 | -0.02 |
| 5 | -10.7 (4.5%) | -10.7 (4.5%) | 1.6 (-1.4%) | 0.0 | 0.0 | 21.5 | 4.3 | -2.1 | -0.23 | +0.0043 | +0.00 |
| 10 | -13.5 (5.6%) | -13.5 (5.6%) | 1.1 (-0.9%) | 0.0 | 0.0 | 31.1 | 3.1 | -1.4 | -0.21 | +0.0058 | +0.07 |

**S2 fade alone (no halving), lots on tag days**

| lots | dMaxDD ALL (cut %) | dMaxDD PRE (cut %) | dMaxDD X' (cut %) | dMaxDD L6M | dMaxDD HOLD | dW20 ALL | dW20 per lot ALL | dMaxDD per lot ALL | dSD ALL | dCalmar ALL | dMean ALL $k/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | -0.6 (0.2%) | -0.6 (0.2%) | -0.4 (0.3%) | 0.0 | 0.0 | 4.8 | 4.8 | -0.6 | -0.02 | +0.0003 | +0.01 |
| 2 | -1.1 (0.5%) | -1.1 (0.5%) | -0.8 (0.7%) | 0.0 | 0.0 | 9.5 | 4.8 | -0.6 | -0.04 | +0.0005 | +0.03 |
| 3 | -1.7 (0.7%) | -1.7 (0.7%) | -1.2 (1.0%) | 0.0 | 0.0 | 14.3 | 4.8 | -0.6 | -0.05 | +0.0008 | +0.04 |
| 5 | -2.8 (1.2%) | -2.8 (1.2%) | -2.1 (1.7%) | 0.0 | 0.0 | 23.0 | 4.6 | -0.6 | -0.07 | +0.0014 | +0.07 |
| 10 | -5.6 (2.3%) | -5.6 (2.3%) | -4.2 (3.4%) | 0.0 | 0.0 | 31.7 | 3.2 | -0.6 | -0.07 | +0.0028 | +0.14 |

**Fade alone, linear extrapolation to size** (flagged: 52 trades scaled up; tail of the sleeve itself unmeasured beyond the sample, capacity of NQ 40+ lots at 10:30-15:50 not verified):

| fade lots on tag days | ALL dMaxDD (cut %) | PRE · X' cut % | L6M dMaxDD | dW20 ALL | sleeve alone ALL maxDD | dMean ALL $k/wk |
|---|---|---|---|---|---|---|
| 10 | -5.6 (2.3%) | 2.3% · 3.4% | 0.0 | 31.7 | 32.9 | +0.14 |
| 20 | -11.2 (4.6%) | 4.6% · 1.9% | 0.0 | 27.5 | 65.9 | +0.27 |
| 40 | -22.4 (9.3%) | 9.3% · -1.7% | 6.5 | -5.0 | 131.7 | +0.54 |
| 80 | -17.7 (7.3%) | 7.3% · -8.9% | 43.7 | -235.2 | 263.5 | +1.08 |

The fade does not scale: its ALL worst-20 gain peaks near 10 lots, its ALL cut reaches 9% only at 40 lots with X' deepening and L6M worsening, and at 80 lots its own tail dominates (sleeve alone maxDD 264k). Sizing up an 8-day pattern is not a route to a 20% cut.

**Equal-risk lots.** The lot at which the sleeve ALONE has the stack's ALL weekly SD (L_sd) or the stack's ALL maxDD (L_mdd), and the lot (grid 0.5-40) with the largest ALL maxDD cut (linear scaling of the daily series; beyond ~10 lots the sleeve's own tail takes over in L6M, see the lots tables).

| sleeve | L_sd | L_mdd | lot with largest ALL cut | that cut $k | L6M maxDD at that lot (before 22.9k) |
|---|---|---|---|---|---|
| S1 (M) | 19 | 16 | 29.0 | -55.9 | 181.4 |
| S1 (LIVE-CAL) | 19 | 15 | 29.0 | -51.0 | 188.8 |
| S2 (fade lots, halving on) | 128 | 73 | 40.0 | -30.3 | 28.1 |

**Equal-risk mean** (stack + 3 lots, scaled by c so the ALL worst-20 equals the stack's; linear): 

| sleeve | c | dMean at c: L3M · L6M · HOLD · PRE · X' · ALL ($k/wk) |
|---|---|---|
| S1 (M) | 1.008 | +3.23 · +1.25 · +1.62 · +1.27 · +0.34 · +1.09 |
| S1 (LIVE-CAL) | 1.007 | +3.12 · +1.11 · +1.48 · +1.16 · +0.26 · +0.98 |
| S2 | 1.011 | -0.04 · -0.29 · -0.17 · +0.45 · +0.13 · +0.23 |

The equal-risk lot that makes the sleeve a meaningful offset (L_sd 19 for S1, 128 for the S2 fade) is not executable at NQ size with a 3-lot-scale edge (S1's L6M maxDD is unchanged up to 10 lots but is 181k, against 22.9k, at its 29-lot best-cut point); at the 3-5 lots that are executable S1's weekly SD is 0.16-0.27 of the stack's (3-5 lots) and the S2 fade's is smaller.

## 7. Execution (g) and the RISK-KEEP decision (h)
Passive-fill / miss sweep at 3 lots (both sleeves enter at MARKET, so the 'fill' share is the share of signals actually taken): fills kept 100/80/60/40%; NEUTRAL = random subset (20 draws averaged), ADVERSE = the best (1-f) share of trades by P&L is the ones missed (C1's convention); +-1 tick = 0.25 pt added to entry slippage, stop cost and exit slip.

**S1 prior-VA 80% rule**

| basis | fills | mode | ALL dMaxDD $k (cut %) at -1 / 0 / +1 tick | PRE cut % at 0 tick | X' cut % at 0 tick | ALL dW20 $k at 0 tick | sleeve own mean $/lot-wk at 0 tick |
|---|---|---|---|---|---|---|---|
| M | 100% | full | -15.1 (6.3%) / -14.9 (6.2%) / -14.7 (6.1%) | 6.2% | 11.3% | 8.8 | 301 |
| M | 80% | neutral | -14.8 (6.1%) / -14.6 (6.1%) / -14.5 (6.0%) | 6.1% | 9.3% | 9.0 | 243 |
| M | 80% | adverse | 19.7 (-8.2%) / 19.9 (-8.2%) / 20.1 (-8.3%) | -8.2% | 3.2% | -19.8 | -548 |
| M | 60% | neutral | -11.5 (4.8%) / -11.4 (4.7%) / -11.3 (4.7%) | 4.7% | 6.2% | 6.4 | 149 |
| M | 60% | adverse | 20.2 (-8.4%) / 20.4 (-8.4%) / 20.5 (-8.5%) | -8.4% | -9.8% | -47.3 | -860 |
| M | 40% | neutral | -6.2 (2.6%) / -6.1 (2.5%) / -6.0 (2.5%) | 2.5% | 3.0% | 4.0 | 100 |
| M | 40% | adverse | 17.5 (-7.3%) / 17.7 (-7.3%) / 17.8 (-7.4%) | -7.3% | -4.6% | -32.9 | -583 |
| LIVE-CAL | 100% | full | -14.6 (6.0%) / -14.4 (6.0%) / -14.2 (5.9%) | 6.0% | 11.0% | 7.2 | 275 |
| LIVE-CAL | 80% | neutral | -14.4 (6.0%) / -14.2 (5.9%) / -14.0 (5.8%) | 5.9% | 9.1% | 7.7 | 222 |
| LIVE-CAL | 80% | adverse | 20.2 (-8.4%) / 20.4 (-8.5%) / 20.6 (-8.5%) | -8.5% | 2.7% | -25.6 | -573 |
| LIVE-CAL | 60% | neutral | -11.2 (4.6%) / -11.1 (4.6%) / -11.0 (4.5%) | 4.6% | 6.0% | 5.4 | 133 |
| LIVE-CAL | 60% | adverse | 20.7 (-8.6%) / 20.9 (-8.7%) / 21.1 (-8.7%) | -8.7% | -10.3% | -48.6 | -884 |
| LIVE-CAL | 40% | neutral | -5.9 (2.5%) / -5.8 (2.4%) / -5.7 (2.4%) | 2.4% | 2.8% | 3.4 | 89 |
| LIVE-CAL | 40% | adverse | 18.0 (-7.4%) / 18.1 (-7.5%) / 18.3 (-7.6%) | -7.5% | -4.7% | -33.9 | -592 |

**S2 fade inside the regime stack (halving fixed)**

| basis | fills | mode | ALL dMaxDD $k (cut %) at -1 / 0 / +1 tick | PRE cut % at 0 tick | X' cut % at 0 tick | ALL dW20 $k at 0 tick | sleeve own mean $/lot-wk at 0 tick |
|---|---|---|---|---|---|---|---|
| M | 100% | full | -9.6 (4.0%) / -9.6 (4.0%) / -9.6 (4.0%) | 4.0% | -2.0% | 12.3 | 14 |
| M | 80% | neutral | -8.8 (3.7%) / -8.8 (3.7%) / -8.8 (3.7%) | 3.7% | -2.0% | 10.0 | 15 |
| M | 80% | adverse | -6.1 (2.5%) / -6.1 (2.5%) / -6.0 (2.5%) | 2.5% | -5.0% | 5.1 | -46 |
| M | 60% | neutral | -8.7 (3.6%) / -8.7 (3.6%) / -8.7 (3.6%) | 3.6% | -2.2% | 7.4 | 13 |
| M | 60% | adverse | -6.1 (2.5%) / -6.1 (2.5%) / -6.0 (2.5%) | 2.5% | -5.0% | 1.6 | -78 |
| M | 40% | neutral | -8.6 (3.6%) / -8.6 (3.6%) / -8.6 (3.6%) | 3.6% | -2.8% | 4.1 | 7 |
| M | 40% | adverse | -7.9 (3.3%) / -7.9 (3.3%) / -7.9 (3.3%) | 3.3% | -4.6% | -2.0 | -63 |
| LIVE-CAL | 100% | full | -9.6 (4.0%) / -9.6 (4.0%) / -9.5 (4.0%) | 4.0% | -2.1% | 12.3 | 10 |
| LIVE-CAL | 80% | neutral | -8.8 (3.6%) / -8.8 (3.6%) / -8.8 (3.6%) | 3.6% | -2.1% | 10.0 | 12 |
| LIVE-CAL | 80% | adverse | -6.0 (2.5%) / -6.0 (2.5%) / -6.0 (2.5%) | 2.5% | -5.1% | 6.9 | -46 |
| LIVE-CAL | 60% | neutral | -8.6 (3.6%) / -8.6 (3.6%) / -8.6 (3.6%) | 3.6% | -2.3% | 7.4 | 10 |
| LIVE-CAL | 60% | adverse | -6.0 (2.5%) / -6.0 (2.5%) / -6.0 (2.5%) | 2.5% | -5.1% | -0.2 | -86 |
| LIVE-CAL | 40% | neutral | -8.6 (3.6%) / -8.6 (3.6%) / -8.6 (3.5%) | 3.6% | -2.8% | 4.1 | 5 |
| LIVE-CAL | 40% | adverse | -6.0 (2.5%) / -6.0 (2.5%) / -6.0 (2.5%) | 2.5% | -4.7% | -2.0 | -61 |

Reading (S1): ticks matter little at 3 lots (+-1 tick moves the ALL cut by about 0.2k because the sleeve trades 1.6 times a week); the share of signals taken matters more because the cut is the sleeve's mean (60% neutral keeps 4.7% of PRE's 6.2%); and the ADVERSE miss (the best trades are the ones not taken) turns S1 into a maxDD INCREASE of 17-21k (about +8%) and a 20-48k worse tail. The edge sits in a minority of winners, so the S1 cut is not robust to selective misses. S2 is insensitive to fills (the ALL cut stays 2.5-4.0% at every setting) because 7.9k of its 9.6k cut is the halving, which is not a fill; the fade's own mean is only +13/lot-week, and its ADVERSE miss at 60% still keeps a 2.5% ALL cut but takes the worst-20 gain to about 0 (-0.2k to +1.6k vs +12.3k) and X' deeper (5%).

**RISK-KEEP gate table** (all eight must pass at the 3-lot M row; every failure named):

| gate | S1 prior-VA 80% | S2 chop-day regime stack |
|---|---|---|
| G1 maxDD cut >=20% in ALL, PRE and X' | FAIL | FAIL |
| G2 L6M maxDD not deepened >5% | PASS | PASS |
| G3 ALL mean not below -MDE | PASS | PASS |
| G4 matched-placebo rank >=95% (dMaxDD ALL, PRE, X') | FAIL | FAIL |
| G5 bootstrap 95% CI of dMaxDD < 0 in PRE and X' | FAIL | FAIL |
| G6 LOEO survives all five removals | FAIL | FAIL |
| G7 execution (60% fills, +1 tick): dMaxDD ALL<0 and PRE/X' cuts >=10% | FAIL | FAIL |
| G8 conditional circular-shift p<0.05 | FAIL | FAIL |
| numbers behind G1 | cut ALL 6.2% · PRE 6.2% · X' 11.3% | cut ALL 4.0% · PRE 4.0% · X' -2.0% |
| numbers behind G3 (ALL mean $k/wk, MDE) | S1 3 lots +0.90 (1.85) | regime delta -0.024 (0.45) |
| 5 lots (M): cut ALL · PRE · X' · L6M dMaxDD | 9.5% · 9.5% · 18.8% · 0.0k | 4.5% · 4.5% · -1.4% · 0.0k |

**RISK-KEEP: NO for S1 and NO for S2.** S1 fails G1 (6.2% / 11.3% vs 20%), G4 (84% / 94%, bar 95%), G5, G6, G7 (at 60% fills +1 tick the PRE/X' cuts are 4.7% / 6.1%, under 10%), G8; it passes G2 and G3. S2 fails G1 (ALL 4.0%, X' deepened 2.0%), G4, G5, G6, G7 (PRE cut 3.6% at 60% fills), G8 (week-level p 0.075) and passes G2 and G3. The unmet piece is the size of the effect, not its sign: both are small positive-mean-side leads with a 241k single-episode stack drawdown that 3-5 lots cannot move by 20%; at 10 lots S1 reaches a 15% ALL cut with X' -37% but the sleeve's own L6M tail grows at larger size (181k at its 29-lot best-cut point) and the placebo ranks stay near 85-95%. Verdict: keep both as **Shadow logs** (no stack change, no Sunday action); the S2 fade's conditional effect in the worst weeks (selection-corrected p 0.025) is the one result worth watching forward, as a Shadow log.

## 8. D7 / D6 specs (Shadow only; NT8, NQ 1-minute bars, OnBarClose, ET; nothing live) and the monitor STOP rule
**S1 prior-VA 80% rule (D7 sleeve slot 1, 1 lot shadow).** Chart: NQ 1-minute, Time zone ET, session template RTH 09:30-16:00, Calculate = OnBarClose, one trade per day. Daily at 09:29:59 compute the previous RTH day's (09:30-15:59) 70% value area: 1-point bins of typical price (H+L+C)/3 weighted by bar volume, start at the POC bin and add the larger neighbouring bin until 70% of volume is reached; VAH = top of the upper bin, VAL = bottom of the lower bin. Setup: today's 09:30 open > VAH (side SHORT) or < VAL (side LONG). Trigger: the FIRST 1-min bar close from the 09:35 bar through the 12:59 bar that is back INSIDE the value area (close < VAH for short, > VAL for long); the signal bar is the bar whose close triggers. Entry: MARKET order at the open of the next bar. Stop: 40 points beyond the re-entry edge (VAH+40 for short, VAL-40 for long), placed as a stop-market with the entry (OCO). Target: the opposite edge (VAL for short, VAH for long), limit; if the target is less than 8 points from the entry price, use 8 points. Flatten: MARKET at the 15:49 bar close (exit 15:50:00). Skip half days. Same-bar stop and target: assume the stop. Log: trigger bar time, VAH, VAL, POC, open, fill price, exit price and reason, and the composite's P&L for the same week.

**S2 chop-day regime (D6 policy flag + D7 fade).** (1) At 10:30:00 ET compute first-hour range R = max(H) - min(L) of the 09:30-10:29 bars and the median of R over the previous 20 trading days; compute ER = |close(10:29) - open(09:30)| / sum of |step| over the 12 five-minute closes of 09:30..10:30 (steps between consecutive 5-min closes, first step from the 09:30 open). TAG = R < 0.6 x median AND ER < 0.3 (52 days in 3 years, 7%). (2) D6 policy line (SHADOW LOG ONLY, not applied): on a tag day log every trend-book signal entered at or after 10:30 together with the lots it would have had under the x0.5 ER multiplier (integer, half-up, min 1). (3) D7 fade sleeve, tag days only, 3 lots (shadow 1 lot): chart NQ 1-minute OnBarClose ET; VWAP = cumulative sum(typical price x volume) / cumulative volume from 09:30, dev = close - VWAP, sigma = expanding population standard deviation of dev since 09:30, z = dev / sigma. From the 10:30 bar close to the 14:29 bar close the FIRST bar with |z| >= 1.5 fires: MARKET order toward VWAP (long if z <= -1.5) at the next bar open; OCO target +30 pts and stop -30 pts from the fill; flatten MARKET at 15:49 bar close; one trade per tag day.

**Monitor STOP rule (Shadow log; evaluated every Friday close; rules fixed now).** Log per week: stack P&L (composite shadow), sleeve P&L at 1 lot, sleeve P&L x 3. S1 backtest per-lot weekly SD 2682 $, per-lot maxDD (sleeve alone, ALL) 15.1k, 1.6 trades a week. S2 fade backtest: 52 trades in 3 years. STOP (retire the shadow, do not size) when ANY of: (a) HEDGE FAILURE: over the first four weeks in which the composite loses more than 1.5 x its weekly SD (50k, i.e. a week below -75k), the sleeve x 3 (S2: regime delta) loses money in 3 or more of them; (b) BLEED: after at least 26 weeks (S1) / 12 tag days (S2) the sleeve's cumulative P&L per lot is below zero AND below minus 1.0 x its weekly SD x sqrt(weeks) [S1]; (c) DRAWDOWN: the sleeve's own 1-lot drawdown exceeds 1.5 x its backtest maxDD (22.6k for S1); (d) MISS: signal-taken share below 60% or the shadow fills average worse than M + 1 tick over 20 trades. PROMOTE (a Sunday decision, never automatic) only after 52 weeks of shadow in which the forward stack maxDD cut at 3-5 lots reaches 20% with a bootstrap CI below zero and the gates G1-G8 are re-run on the forward weeks.

## 9. Caveats and files
- Selection: both candidates came from C1's 40-cell + 18-cell search read on PX, so PRE/X' are in-sample for the choice; L6M and HOLD were read by C1, so 'unchanged in L6M' is not independent confirmation. The permutation p's and CIs are conditional on the cell having been picked.
- Effective N: ALL maxDD is one episode (ep1, 241k); the 14 independent worst-week episodes and 52 tag days are the real sample sizes for the conditional claims.
- LIVE-CAL equals M for the market-entry sleeves except for slippage/stop cost (about 0.2k on the cut); there is no limit-fill haircut in these two sleeves, so the sweep uses the share of signals taken.
- Code: `l2vast/ds3/code/hedge_decisive/` (dec_lib, dec_s1_plc, dec_s2_plc, dec_s2_rank, dec_main, dec_report, dec_report2). Results: `l2vast/ds3/out/hedge_decisive/` (main.pkl, plc_s1.pkl, plc_s2_matched_m1000.pkl, csv tables). Prereg sha256 in DECISIONS.md.