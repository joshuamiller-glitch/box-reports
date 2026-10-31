# DS3_PERSISTENCE_SUNDAY (agent PS-1, 2026-10-31): is any Sunday piece among the persisting rules, and the honest Sunday number at persistence-shrunk size

Research only; no live/execution/chart change. Own masks capped 20260206 (L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131); UNTOUCHED never read. Nothing is re-selected: the six Sunday pieces are exactly as coded; only their SIZE changes, by the RE-1 study (DS3_PERSISTENCE.md, family x 6-month-t factors). Engine = the common engine `l2vast/ds3/code/sundaystack2/ss2_lib.py` (8 books, causal running-max locks, live lots K6 2 / P6 7 / U6 4 / H6 4-2 / M6 2 / A6 1, Native 1.28 vs join 2.45, integer half-up min-1 ER lots, integer 70/30 lots with a +0.25 pt add slip, N basis). **Tie-out first:** with all six pieces at full size the engine returns the SS-2 fractional headline +18.5k / +16.2k / +4.7k / +12.5k (L6M / HOLD / PRE / X') and the stored SS-2 integer line to a maximum daily difference of 0.0; the all-off run equals the stored "stack as it is" to 0.0. Code `l2vast/ds3/code/persistsunday/` (ps1_set, ps2_pieces, ps2b_table, ps3_composite, ps3b_extra, ps4_doc; library psl.py), outputs `l2vast/ds3/out/persistsunday/`. A6 is the engine's PB book (the SS-2 mapping, not yet PB7; the D1 agent re-states with PB7; A6 is 1 lot, below 0.3k in every number here).

## PAGE 1 - THE PLAIN ANSWER

**Is any Sunday piece among the persisting rules? Only the Native stop, and it is there because it is a measured cost, not a trading rule.** The rules that stayed positive 70% (6-month t 3-4) to 94% (t >= 4) of the time are, after removing numerical artifacts, almost all one structural family: the profit-protect exits that sit on the take-at-70% leg (`p70always`: 97.6% persistence, about 0.59 of the recent per-exposure magnitude kept), plus a few sizing / entry-filter cells (sizing t >= 3 keeps 0.30). **Five of Sunday's six pieces (70/30 split, PE 45-s confirmation, ER sizer, 8-line zone skip, Asia-stopped cut50) have a 6-month t between 0.3 and 2.6 on the common engine (HOLD -0.4 to 2.4); none reaches 3 and none is in the persisting set.** In the study's t 1-3 buckets their family factors are entry structure -0.78, confirmation -1.12, stack -2.16, entry filter -0.00, sizing +0.07: the shrunk expectation is <= 0 for the split, PE, cut and zone (OFF) and about +1k for the ER sizer (size 0.03). **The sixth, the Native stop, has t = 5.5 (L6M) / 6.1 (HOLD), is an exit item (exit t >= 3 factor +0.70, persistence score 0.71, size 0.81).** Caution: that t is an engine unit effect (a 1.17 pt/stop saving times the stop count); the live evidence for the 1.17 pt is z = 1.6 (join n=21 vs Native n=8, LIVE_STOP_JOIN.md), so it is a measured execution saving whose size is unproven, not evidence of a persisting edge.

**THE HONEST SUNDAY NUMBER (shrunk-size composite: Native 0.81, ER 0.03, split / PE / zone / cut OFF): +2.2k per week L6M (MDE 0.6k), +2.2k HOLD, +2.3k PRE, +1.8k X', +2.1k L3M, against the stack as it is.** The as-coded integer composite is +22.8k L6M / +19.3k / +7.4k / +12.9k; at persistence-shrunk size 90% of it is gone, and 99% of what remains is the Native stop (the ER sizer at 0.03 rounds to no lot change at live lots). The ER sizer is the one item to decide by hand: with ER at full size on top of the shrunk composite the line is +10.4k L6M / +9.6k HOLD / +0.9k PRE / +5.6k X'.

### The honest-number table ($k/wk, delta vs the stack as it is; MDE = 2.8 x week-clustered SE in brackets; live lots, running-max locks, integer half-up min-1 lots, Native 1.28, N basis)

| composite | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| AS-CODED: all six pieces full size, K6 1/1 split (add slip +0.25) | +25.0 (22.6) | +22.8 (17.6) | +19.3 (17.3) | +7.4 (13.0) | +12.9 (15.0) |
| AS-CODED, K6 at market / others 70/30 (decision line b) | +22.7 (21.3) | +22.1 (17.1) | +18.9 (16.8) | +6.8 (13.0) | +13.0 (14.4) |
| AS-CODED, add slip +0.45 (stress) | +24.6 (22.5) | +22.2 (17.4) | +18.8 (17.2) | +7.1 (13.0) | +12.7 (15.0) |
| **SHRUNK-SIZE composite = the honest Sunday number** (split 0, PE 0, zone 0, cut 0, ER 0.03, Native 0.81) | +2.1 (0.8) | +2.2 (0.6) | +2.2 (0.5) | +2.3 (1.9) | +1.8 (0.2) |
| SHRUNK, K6 at market (same line: the split is OFF) | +2.1 (0.8) | +2.2 (0.6) | +2.2 (0.5) | +2.3 (1.9) | +1.8 (0.2) |
| SHRUNK with the study factor itself as the size (ER 0.07, Native 0.70) | -0.4 (10.4) | +1.3 (6.1) | +0.8 (5.7) | +1.9 (4.1) | +3.5 (5.4) |
| SHRUNK, Native stop at 100% | +2.6 (0.9) | +2.7 (0.6) | +2.7 (0.5) | +2.7 (1.9) | +2.3 (0.3) |
| SHRUNK, Native stop OFF (join 2.45) | -0.1 (0.5) | +0.0 (0.5) | +0.0 (0.4) | +0.3 (2.1) | +0.0 (0.1) |
| SHRUNK + ER sizer at 100% | +9.7 (16.5) | +10.4 (9.6) | +9.6 (9.6) | +0.9 (10.7) | +5.6 (13.9) |
| BEST-CASE strata (most favourable applicable study stratum per piece; ER 0.36 through the sizing t >= 3 stratum although its t is 2.5) | +0.3 (10.6) | +3.0 (7.0) | +2.4 (6.6) | +2.5 (6.6) | +4.2 (7.2) |
| Benchmark only: every piece at 50% (12 random draws) | +13.5 (13.6) | +13.9 (9.8) | +11.8 (9.4) | +2.7 (8.2) | +8.0 (9.4) |

Stack levels for orientation ($k/wk, L3M / L6M / HOLD / PRE / X'): as it is 13.8 / 24.0 / 23.7 / 17.7 / -3.6; as-coded composite 38.9 / 46.8 / 43.0 / 25.1 / 9.3; shrunk composite 15.9 / 26.2 / 25.9 / 20.0 / -1.7.

**Reading.** (1) The shrunk line is small but its MDE is small too, because the Native stop is a steady per-stop saving: positive in all five windows and above its MDE in every one (+2.1 (0.4) PRE, +1.8 (0.2) X'). The as-coded line is above its MDE in L3M, L6M and HOLD and inside it in PRE (7.4k vs 13.0k) and X' (12.9k vs 15.0k). (2) The gap shrunk minus as-coded is -20.6k L6M against a paired MDE of 17.5k, -17.1k HOLD (17.2k), -5.1k PRE (13.0k), -11.1k X' (14.9k): the gap is just outside its paired MDE in L3M and L6M and inside it in HOLD, PRE and X'; the shrinkage is a statement about the next quarters, not about the sample. (3) Nothing is turned OFF on in-sample numbers: in the leave-one-out every piece is positive in L6M and the cut is the only one negative in HOLD (-0.6k). The OFF comes only from the persistence study's family factors (section 2). A reader who rejects the factors has the as-coded line; the 50% benchmark is the middle (+13.9k L6M). (4) The study's own warning applies to the whole page: positive in L3M and L6M raised the chance of a positive next quarter by nothing over the family base rate (DS3_PERSISTENCE.md, page 1), and the RE-2 walk-forward found that running recent edges at the shrunk size would have been -5.5k/wk (DS3_RECENT_PORTFOLIO.md). The honest number is a forecast under that finding; it is not a statement that the pieces are bad.

---

## 1. The rules that DO persist (6-month t >= 3), and what 'persist' means

**Definition.** A (rule, scope) series is SELECTED at month M if its sum over M-3..M-1 and M-6..M-1 is positive and it fired >= 10 times; it PERSISTS if its sum over the next three months M..M+2 is positive (the share of positive next quarters, a SIGN statement; the magnitude kept is a separate column). t = 6-month sum / sqrt(sum of squares) at selection (per trade for per-trade programs, per day for lock-engine stack programs). The study frame is 450,016 series; 50,000 sampled; t >= 3 holds 7991 selected rule-months (1,504 series / 1,431 distinct rule names in the clean set, 2,292 / 2,213 raw).

**Two artifacts removed here (not removed in DS3_PERSISTENCE.md, which stays as published).** (i) 3116 of the 7991 t >= 3 rule-months are 788 day-type / clock (EINT2 regime) rules whose stored daily delta is float noise ($0.06 in total over 740 days: filters that never fire, all with the same z of 4.5 and P = 75%); they carry the regime-family '75%' and are not rules with any magnitude. (ii) 53 rule-months of `netOneORACLE`, the non-causal oracle of the EINT1 map (leader sized by future followers). Clean set: 4822 rule-months, 1431 distinct rules.

| t bucket (6-month) | raw rule-months | raw P(persist) | clean rule-months | clean P(persist) | clean distinct rules |
|---|---|---|---|---|---|
| 3-4 | 2616 | 70% | 2587 | 70% | 1280 |
| >= 4 | 5375 | 83% | 2235 | 94% | 595 |
| >= 3 | 7991 | 79% | 4822 | 81% | 1431 |

The published 70% / 83% are the raw figures; cleaned they are 70% / 94% (the artifact pulled the >= 4 bucket down, the 3-4 bucket is almost unchanged).

### 1.1 By family and source (clean t >= 3 set; units are per planned lot per exposure in points except where stated)

| family | source (program) | distinct rules | rule-months | selection months | P(persist) | median t | fire rate | recent (IS) per exposure | next-3m (OOS) per exposure | OOS/IS kept |
|---|---|---|---|---|---|---|---|---|---|---|
| confirmation | confirmation cells (H3_cfeng) | 3 | 5 | 5 | 0% | 3.1 | 78% | +1.00 | -0.36 | -0.36 |
| confirmation | confirmation cells (H4_c2G1) | 18 | 25 | 12 | 20% | 3.2 | 100% | +1.42 | -0.31 | -0.22 |
| confirmation | confirmation cells (H4_c2G2) | 3 | 4 | 3 | 50% | 3.1 | 43% | +3.77 | -0.16 | -0.04 |
| confirmation | confirmation cells (H4_c2G3) | 3 | 3 | 2 | 0% | 3.4 | 100% | +2.08 | -0.73 | -0.35 |
| confirmation | confirmation cells (H4_c2G4) | 13 | 21 | 7 | 48% | 3.2 | 100% | +1.45 | -0.71 | -0.49 |
| confirmation | confirmation cells (H4_c2G5) | 1 | 1 | 1 | 100% | 3.1 | 100% | +2.04 | +0.48 | +0.24 |
| entry filter | EINT1 map (filters and row-multiplier sizers) | 50 | 142 | 25 | 58% | 3.4 | 100% | +1.29 | +0.11 | +0.08 |
| entry structure | alt-bar engines | 14 | 24 | 9 | 54% | 3.1 | 100% | +12.28 | -0.65 | -0.05 |
| entry structure | entry grids (L2SE, dipentry) | 224 | 366 | 18 | 35% | 3.2 | 73% | +1.76 | -0.71 | -0.41 |
| exit | profit-protect exits (L2SP, delta vs hold-to-bracket) | 836 | 3426 | 16 | 94% | 4.2 | 55% | +1.44 | +0.80 | +0.55 |
| exit | loss exits (UF-LOSS D2/D3/D6/D6q/D_main) | 179 | 522 | 26 | 56% | 3.5 | 7% | +0.47 | +0.01 | +0.03 |
| regime | EINT2 day-type (stack $/day) | 8 | 12 | 6 | 33% | 3.1 | 98% | +3304.29 ($/day) | -753.99 ($/day) | -0.23 |
| sizing | EINT1 map (filters and row-multiplier sizers) | 79 | 271 | 26 | 57% | 3.5 | 100% | +0.88 | +0.08 | +0.09 |

Units: points per planned lot per base trade (x $20 x lots for dollars); the EINT2 row is 8 rules / 12 rule-months left after the artifact filter, not interpretable. Persistence = the P column. **The family answer:** exits persist (88% of 3,948 exit rule-months with t >= 3; profit exits 94%, loss exits 56%; the next quarter keeps 0.54 of the recent per-exposure size), sizing 57% (keeps 0.09), entry filters 58% (keeps 0.08), entry structure 36% (keeps -0.39) and confirmation 31% (keeps -0.31). A t >= 3 entry-structure or confirmation rule is NOT more likely than a coin to stay positive and its next-quarter magnitude is negative. Even for exits the persistence is a 2025 phenomenon: of the 3,948 exit rule-months, 3,328 are selected in 2025-06..2025-11 (96% persist) and 620 earlier (46% persist).

### 1.2 The persisting exit family, in detail (what the 70-83% is)

| rule type (name pattern P\|trigger\|arm\|delay\|action\|p70mode) | distinct rules | rule-months | selection months | P(persist) | median t | fire rate | recent per exposure | next-3m per exposure | kept |
|---|---|---|---|---|---|---|---|---|---|
| profit-protect exit: trail (p70always) | 276 | 1295 | 7 | 98% | 4.3 | 56% | +1.48 | +0.87 | +0.59 |
| profit-protect exit: lock (p70always) | 154 | 719 | 7 | 97% | 4.4 | 56% | +1.52 | +0.92 | +0.60 |
| profit-protect exit: half (p70always) | 113 | 526 | 7 | 98% | 4.4 | 56% | +1.51 | +0.89 | +0.59 |
| profit-protect exit: take (p70always) | 60 | 275 | 7 | 98% | 4.3 | 56% | +1.53 | +0.93 | +0.61 |
| profit-protect exit: trail (p70thickonly) | 61 | 187 | 13 | 83% | 3.5 | 33% | +1.26 | +0.20 | +0.16 |
| loss exit: D3 | 62 | 186 | 24 | 58% | 3.5 | 3% | +0.33 | +0.06 | +0.18 |
| profit-protect exit: lock (p70thickonly) | 42 | 154 | 8 | 83% | 3.5 | 31% | +1.19 | +0.23 | +0.19 |
| profit-protect exit: half (p70thickonly) | 38 | 126 | 11 | 90% | 3.5 | 33% | +1.26 | +0.21 | +0.17 |
| loss exit: D_main | 27 | 87 | 25 | 51% | 3.5 | 5% | +0.25 | -0.02 | -0.06 |
| loss exit: D2 | 28 | 76 | 18 | 53% | 3.6 | 53% | +1.31 | -0.04 | -0.03 |
| loss exit: D6q | 18 | 75 | 18 | 63% | 3.9 | 14% | +0.38 | +0.00 | +0.01 |
| loss exit: D6 | 20 | 43 | 15 | 56% | 3.6 | 45% | +0.99 | -0.06 | -0.06 |
| profit-protect exit: take (p70thickonly) | 14 | 42 | 10 | 71% | 3.5 | 30% | +1.07 | +0.20 | +0.18 |
| profit-protect exit: trail (p70never) | 32 | 38 | 5 | 16% | 3.3 | 19% | +0.69 | -0.34 | -0.49 |

**What the persisting set is.** `p70always` profit-protect exits (trail / lock / half / take after an armed gain of N pts or 0.5-0.7 of the target, with the take-at-70% leg applied always): 603 rule names, 2,815 rule-months, 97.6% persistence, recent +1.5 and next-quarter +0.9 pts per planned lot per exposure (0.59 kept), fire rate 56% of base trades, only two scopes (pooled and WT). The four actions have the same recent (+1.48 to +1.53) and next (+0.87 to +0.93) numbers, so the common component is the 70% take that every `p70always` variant shares, not the trail / lock / half action; the `p70never` variants (no 70% take) persist 30% (102 rule-months, -0.31 pt next quarter) and `p70thickonly` 84% with 0.2 pt (0.16-0.19 kept). In D6 terms this is the live THP_POLICY profit group (pct >= 0.7 take), already implemented per the ledger's tag; it is not one of Sunday's six.

**Sample and independence (how many exposures).** 603 distinct `p70always` rule names (590 persisting rules over all families after the filter P >= 0.7, >= 4 selection months and positive next-quarter magnitude: 572 exits, 8 sizing, 5 entry filter, 5 entry structure), but they are parameter variants of one trade set: 1,424 distinct monthly vectors in 1,504 series, yet only the pooled scope and WT carry the t >= 3 profit rules. The selection months are concentrated: 3,328 of the 3,948 exit rule-months are selected in 2025-06..2025-11 (96% persist; the 620 earlier ones persist 46%), and the six after-windows (Jun-Aug .. Nov-Jan) cover two non-overlapping quarters. Per selection month the `p70always` persistence is 100% / 98% / 94% / 100% / 100% / 100% for 2025-06..2025-11 against 11% (n=27) for the one earlier selection month (2023-10). The non-overlapping-block P over all clean t >= 3 rule-months (three offsets, 8-9 blocks each) is 80-82%. So the independent evidence is roughly two quarters x one structural mechanism, and '70-83%' is a statement about that mechanism in 2025, with month-block CIs (pooled, raw) of 49-77% (t 3-4) and 37-97% (t >= 4) in the study (section 3.3 there).

### 1.3 Individual t >= 3 rules outside the exit family that persist (P >= 0.7, >= 4 selection months, positive next-quarter magnitude)

| rule | family | scopes | selection months | P | median t | fire | recent/exposure | next-3m/exposure |
|---|---|---|---|---|---|---|---|---|
| l2se_main/145 | entry structure | 1 | 4 | 75% | 3.2 | 100% | +2.42 | +1.90 |
| skipTop3_htf_pd_range_atr | entry filter | 3 | 9 | 75% | 4.2 | 100% | +1.95 | +1.20 |
| skipBot3_htf_gap_eth | entry filter | 4 | 8 | 88% | 4.4 | 100% | +2.35 | +1.08 |
| dipentry_g1/29 | entry structure | 1 | 4 | 100% | 3.5 | 96% | +1.10 | +0.73 |
| sizeHi_htf_gap_eth | sizing | 6 | 10 | 70% | 4.5 | 100% | +1.50 | +0.63 |
| doubleTop3_htf_gap_eth | sizing | 4 | 11 | 80% | 4.5 | 100% | +1.07 | +0.63 |
| sizeLo_htf_pd_range_atr | sizing | 2 | 9 | 82% | 3.9 | 100% | +0.99 | +0.49 |
| halveTop3_htf_pd_range_atr | sizing | 3 | 9 | 75% | 4.2 | 100% | +0.78 | +0.48 |
| halveBot3_htf_gap_eth | sizing | 4 | 8 | 88% | 4.4 | 100% | +0.94 | +0.43 |
| skipTop3_htf_on_ratio | entry filter | 1 | 4 | 100% | 3.9 | 100% | +1.32 | +0.40 |
| dipentry_g1/865 | entry structure | 2 | 6 | 100% | 3.8 | 77% | +1.07 | +0.38 |
| doubleTop3_htf_wk_open_atr | sizing | 1 | 8 | 88% | 4.1 | 100% | +0.91 | +0.33 |
| dipentry_g1/1307 | entry structure | 1 | 5 | 80% | 3.4 | 68% | +1.49 | +0.33 |
| skipBot10_htf_on_pos | entry filter | 1 | 4 | 100% | 3.5 | 100% | +0.92 | +0.32 |
| dipentry_g1/857 | entry structure | 1 | 5 | 80% | 3.5 | 85% | +0.74 | +0.21 |
| halveTop3_htf_on_ratio | sizing | 1 | 4 | 100% | 3.9 | 100% | +0.59 | +0.18 |
| skipTop10_htf_fh_atr | entry filter | 2 | 6 | 71% | 4.3 | 100% | +0.56 | +0.15 |
| sizeLo_sd_pd_lo_atr | sizing | 1 | 7 | 71% | 3.6 | 100% | +0.75 | +0.07 |

Top exit examples (all `p70always`, magnitude next quarter per exposure in points per planned lot, fire rate 55%): `P|sess_ahead_ge1.2|armpts15|d30|lock0|p70always` (5 months, 100%, +2.38); `P|z_ahead_ge1.5|armpct0.7|d0|half20|p70always` (5 months, 100%, +2.17); `P|sess_ahead_ge1.5|armpts15|d0|trail30|p70always` (5 months, 100%, +2.14); `P|sess_tot_ge1.2|armpct0.7|d0|trail20|p70always` (5 months, 100%, +2.13); `P|z_tot_ge2.0|armpct0.7|d0|trail15|p70always` (5 months, 100%, +2.12); `P|z_tot_ge1.0|armpct0.7|d0|trail20|p70always` (5 months, 100%, +2.12); `P|t60_ahead_ge1.5|armpct0.7|d0|lock0|p70always` (6 months, 100%, +2.11); `P|hour_tot_ge1.2|armpct0.7|d0|lock10|p70always` (5 months, 100%, +2.09). The full list of 590 rules is `out/persistsunday/tge3_persisting_rules.csv`; every t >= 3 rule is in `tge3_rules.csv`.

**Caveats.** (a) 'Persist' is the sign of the next-quarter sum; for the non-exit rows magnitudes are small (0.1-0.7 pts) and each rule has 4-12 selection months, so the per-rule P is a noisy count (4 of 4 = 100%). (b) The rules are selected by the programs on L6M / HOLD before they enter the frame, so they are the survivors of 450,000 series: the 94% is conditional on being a t >= 4 rule, not on being a rule. (c) Mostly structural exits: the exit geometry (take 70%, protect the remainder) is why they persist, not the market of the recent quarter; entry structure and confirmation, the families the 70/30 split and the PE confirmation belong to, do not persist at any t bucket (t >= 3: 35% and 26%). (d) Everything at the study's units: pts per planned lot per trade; dollars on the stack need the lock engine (section 3).

---

## 2. Sunday's six pieces: t, family, persistence, shrinkage, shrunk expectation

Pieces as coded (SS-2): 70/30 split (integer live lots, add slip +0.25), 8-line zone skip (D = 20), ER(20) sizer x1.5 / x0.5 at 0.30 with running-max locks, PE 45-s three-bar confirmation (NY-AM / NY-PM, market at the candle close, then the split), Asia-stopped first-stop cut50, Native stop 1.28 (vs join 2.45). In-sample value = the piece's **leave-one-out contribution** to the as-coded integer composite (full composite minus the composite without that piece; alone-vs-as-is is in the second table), $/wk, live lots, N basis. 6-month t = delta / SE of the week-clustered paired delta (MDE = 2.8 SE) in L6M and HOLD; z6 (daily) is the study's metric (sum / root-sum-square of the daily deltas over L6M) used to pick the bucket. Family mapping per the order: split = entry structure, PE = confirmation, ER = sizing, Asia cut = stack, zone skip = entry filter, Native stop = execution / exit. Shrinkage = out-of-sample / in-sample from shrinkage_strata.csv for the family and the z6 bucket (1-2, 2-3, >= 3), the L6M-denominated column (OOS next 3 months over the last 6 months); persistence score = the study's walk-forward logistic P(next 3 months > 0 | positive L3M and L6M) with the piece's family, z6, fire rate, PRE sign and monthly streak (set where the piece has them). Size = the ledger rule mu_s^2 / (mu_s^2 + SE^2 + (mu x se_factor)^2) with mu_s = factor x in-sample L6M, zero where mu_s <= 0 (RECENT_WINS.md, 'SIZE x normal').

| piece | family | 6M t (L6M / HOLD) | z6 daily | in persisting set (t >= 3)? | fire rate | persistence score | stratum used | shrinkage factor (L6M-based) | in-sample L3M / L6M / HOLD / PRE / X' | shrunk expectation L6M / HOLD | size |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 70/30 split | entry structure | 2.2 / 2.4 | 1.9 | no | 81% | 0.44 | entry structure/t-stat(6m) 1-2 | -0.78 | +8.0 / +4.3 / +4.1 / +1.3 / +0.6 | -3.3k / -3.2k | 0.00 |
| PE 45-s confirmation | confirmation | 1.1 / 1.3 | 1.1 | no | 61% | 0.34 | confirmation/t-stat(6m) 1-2 | -1.12 | +7.4 / +4.0 / +4.3 / +0.4 / -0.8 | -4.5k / -4.8k | 0.00 |
| ER(20) sizer | sizing | 2.6 / 2.3 | 2.5 | no | 100% | 0.60 | sizing/t-stat(6m) 2-3 | +0.07 | +16.7 / +14.2 / +12.8 / +4.7 / +1.7 | +1.0k / +0.9k | 0.03 |
| Asia-stopped cut50 | stack | 0.3 / -0.4 | 0.3 | no | 4% | 0.17 | stack/t-stat(6m) 1-2 | -2.16 | +0.3 / +0.3 / -0.6 / +0.9 / +1.4 | -0.7k / n/a (in-sample <= 0) | 0.00 |
| 8-line zone skip | entry filter | 1.0 / 0.4 | 0.7 | no | 15% | 0.49 | entry filter/t-stat(6m) 1-2 | -0.00 | +4.3 / +3.3 / +1.3 / +2.6 / +3.7 | -0.0k / -0.0k | 0.00 |
| Native stop 1.28 | exit (execution) | 5.5 / 6.1 | 5.3 | YES | 44% | 0.71 | exit/t-stat(6m) >=3 | +0.70 | +2.6 / +2.4 / +2.3 / +2.8 / +1.8 | +1.7k / +1.6k | 0.81 |

Fire rate = share of base trades the piece touches (split: add filled; PE: NY-AM / NY-PM PE signals confirmed, of 2681; ER: every trade carries a multiplier; cut: stop events over taken trades; zone: share of rows on a fired line; Native: share of stops, of 44370 engine rows). Shrunk expectation = factor x in-sample; negative means the piece is expected to LOSE in the next quarter given the study's family and bucket, hence OFF. The HOLD column is the same factor on HOLD; for the cut the HOLD in-sample is already <= 0, so no expectation is formed.

**Required keep-ratio for a size of 0.5** (factor at which the ledger size rule would give half size: SE / in-sample): split 0.46, PE 0.88, ER 0.39, cut 2.9, zone 1.01, Native 0.18. The study's factors for these families at t 1-3 are 0.07 or below; only exits at t >= 3 (0.70) and sizing at t >= 3 (0.30) get close.

**Each piece alone against the stack as it is** (same engine, ALONE column; the Sunday composite is not additive: the ER sizer, the lock multiplier and the stops interact; MDE in brackets, $k/wk):

| piece alone | L3M | L6M | HOLD | PRE | X' | 6M t (L6M / HOLD) | size from this reading |
|---|---|---|---|---|---|---|---|
| 70/30 split | -1.3 (15.1) | -0.7 (8.8) | -0.5 (7.9) | -0.8 (3.7) | +2.3 (3.9) | -0.2 / -0.2 | 0.00 |
| PE 45-s confirmation | +2.0 (9.1) | +1.6 (6.4) | +1.3 (5.8) | +0.5 (3.6) | +1.4 (4.9) | 0.7 / 0.6 | 0.00 |
| ER(20) sizer | +7.6 (16.5) | +7.7 (9.7) | +7.0 (9.7) | -1.8 (10.6) | +3.3 (14.0) | 2.2 / 2.0 | 0.01 |
| Asia-stopped cut50 | +1.0 (10.3) | +2.2 (6.9) | +1.5 (6.1) | +1.1 (3.4) | +3.9 (3.7) | 0.9 / 0.7 | 0.00 |
| 8-line zone skip | -2.1 (14.0) | +3.1 (10.0) | +2.2 (11.0) | +0.5 (8.1) | +5.5 (8.3) | 0.9 / 0.6 | 0.00 |
| Native stop 1.28 | +2.7 (0.7) | +2.7 (0.5) | +2.7 (0.4) | +2.7 (0.4) | +2.4 (0.5) | 15.3 / 17.9 | 0.85 |

Cross-check with the RE-1 ledger rows (RECENT_WINS.md), which use per-program units and L3M: SPLIT 70/30 stack row P(next 3m > 0) 0.57, size 0.00; L2SE entry rows 0.35-0.45, size 0.00; CONFIRM-BARS PE 45-s three-bar rows 0.40-0.54, size 0.00-0.20; SPLIT-2 ER sizer 0.58 and STACK-2 ER20 >= 0.4 0.24; SPLIT-2 first-stop cut50 0.58; ZONES-2 8-line coded set 0.53-0.59, size 0.00; no ledger row exists for the Native stop. The ledger agrees with the table above on the zero sizes for the split, zone and (L3M-based) PE rows.

---

## 3. The shrunk-size composite

**Size mapping (how each piece is run at size s on the D6-faithful engine).** Split: with probability s per trade the integer 70/30 (K6 1/1, U6 3/1, H6 3/1 or 1/1, P6 5/2 at +0.25 pt per add lot) is used, else market; PE confirmation: with probability s on the NY-AM / NY-PM PE signals (confirmed trades follow the trade's split draw); zone skip: each fired line skips with probability s; the Asia-stopped cut: cut fraction 0.5 x s of the other books' same-side lots; ER sizer: multipliers 1 + s (m - 1) (1.5 -> 1 + 0.5 s, 0.5 -> 1 - 0.5 s), lots = max(1, floor(session lots x mult + 0.5)), the running-max lock multiplier uses the unrounded shrunk multiplier; Native stop: stop cost 2.45 - s (2.45 - 1.28). Random pieces are averaged over 12 common-random-number draws (the draw SD of the L6M delta is 0 when only deterministic pieces are active and 3.2k in the all-at-50% benchmark). Sizes: split 0, PE 0, zone 0, cut 0 (shrunk expectation <= 0 -> OFF), ER 0.031, Native 0.808. At live lots the ER sizer at 0.03 changes no integer lot (K6 2 x 1.015 -> 2, P6 7 x 1.015 -> 7), only the lock multiplier by 1.5%, which is why 'ER 0.03' adds 14 $/wk over 'Native 0.81 only'.

Full table, $k/wk vs the stack as it is, MDE in brackets, and the gap to the as-coded composite (paired MDE):

| composite | sizes (split / PE / zone / cut / ER / Native) | L3M | L6M | HOLD | PRE | X' | vs as-coded L6M (MDE) | vs as-coded HOLD (MDE) |
|---|---|---|---|---|---|---|---|---|
| AS-CODED integer lots (slip .25, K6 1/1 split) | 1.00 / 1.00 / 1.00 / 1.00 / 1.00 / 1.00 | +25.0 (22.6) | +22.8 (17.6) | +19.3 (17.3) | +7.4 (13.0) | +12.9 (15.0) | +0.0 (0.0) | +0.0 (0.0) |
| AS-CODED, K6 at market (others 70/30) | 1.00 / 1.00 / 1.00 / 1.00 / 1.00 / 1.00 | +22.7 (21.3) | +22.1 (17.1) | +18.9 (16.8) | +6.8 (13.0) | +13.0 (14.4) | -0.7 (2.4) | -0.4 (2.2) |
| AS-CODED, add slip 0.45 (stress) | 1.00 / 1.00 / 1.00 / 1.00 / 1.00 / 1.00 | +24.6 (22.5) | +22.2 (17.4) | +18.8 (17.2) | +7.1 (13.0) | +12.7 (15.0) | -0.6 (0.5) | -0.5 (0.5) |
| SHRUNK (ledger sizes) = HONEST | 0.00 / 0.00 / 0.00 / 0.00 / 0.03 / 0.81 | +2.1 (0.8) | +2.2 (0.6) | +2.2 (0.5) | +2.3 (1.9) | +1.8 (0.2) | -20.6 (17.5) | -17.1 (17.2) |
| SHRUNK, K6 at market | 0.00 / 0.00 / 0.00 / 0.00 / 0.03 / 0.81 | +2.1 (0.8) | +2.2 (0.6) | +2.2 (0.5) | +2.3 (1.9) | +1.8 (0.2) | -20.6 (17.5) | -17.1 (17.2) |
| SHRUNK (factor-as-size) | 0.00 / 0.00 / 0.00 / 0.00 / 0.07 / 0.70 | -0.4 (10.4) | +1.3 (6.1) | +0.8 (5.7) | +1.9 (4.1) | +3.5 (5.4) | -21.4 (19.3) | -18.5 (18.3) |
| SHRUNK, Native 100% (others shrunk) | 0.00 / 0.00 / 0.00 / 0.00 / 0.03 / 1.00 | +2.6 (0.9) | +2.7 (0.6) | +2.7 (0.5) | +2.7 (1.9) | +2.3 (0.3) | -20.1 (17.5) | -16.6 (17.2) |
| SHRUNK, Native 0% | 0.00 / 0.00 / 0.00 / 0.00 / 0.03 / 0.00 | -0.1 (0.5) | +0.0 (0.5) | +0.0 (0.4) | +0.3 (2.1) | +0.0 (0.1) | -22.7 (17.7) | -19.3 (17.4) |
| Native 81% only (ER off) | 0.00 / 0.00 / 0.00 / 0.00 / 0.00 / 0.81 | +2.2 (0.6) | +2.2 (0.4) | +2.2 (0.4) | +2.1 (0.4) | +1.8 (0.2) | n/a | n/a |
| SHRUNK, Native 100% + ER 100% | 0.00 / 0.00 / 0.00 / 0.00 / 1.00 / 1.00 | +10.6 (16.6) | +11.3 (9.7) | +10.5 (9.7) | +1.6 (10.7) | +6.0 (13.9) | -11.5 (14.5) | -8.8 (14.6) |
| SHRUNK + split at 100% (others shrunk) | 1.00 / 0.00 / 0.00 / 0.00 / 0.03 / 0.81 | -1.0 (10.9) | +0.7 (7.3) | +1.0 (6.5) | +2.2 (3.6) | +4.1 (3.8) | -22.1 (16.3) | -18.3 (16.1) |
| SHRUNK + pe at 100% (others shrunk) | 0.00 / 1.00 / 0.00 / 0.00 / 0.03 / 0.81 | +5.1 (9.2) | +4.8 (6.8) | +4.3 (6.1) | +1.8 (3.9) | +3.2 (5.0) | -18.0 (15.6) | -15.0 (15.3) |
| SHRUNK + er at 100% (others shrunk) | 0.00 / 0.00 / 0.00 / 0.00 / 1.00 / 0.81 | +9.7 (16.5) | +10.4 (9.6) | +9.6 (9.6) | +0.9 (10.7) | +5.6 (13.9) | -12.4 (14.7) | -9.7 (14.8) |
| SHRUNK + cut at 100% (others shrunk) | 0.00 / 0.00 / 0.00 / 1.00 / 0.03 / 0.81 | +2.8 (10.7) | +4.9 (7.6) | +4.4 (6.7) | +1.8 (4.1) | +6.1 (4.3) | -17.9 (18.1) | -14.9 (17.6) |
| SHRUNK + zone at 100% (others shrunk) | 0.00 / 0.00 / 1.00 / 0.00 / 0.03 / 0.81 | -0.4 (14.4) | +4.9 (10.2) | +3.9 (11.2) | +2.7 (8.3) | +7.0 (8.2) | -17.9 (17.8) | -15.4 (17.6) |
| BEST-CASE strata (most favourable applicable stratum per piece) | 0.01 / 0.00 / 0.00 / 0.00 / 0.36 / 0.81 | +0.3 (10.6) | +3.0 (7.0) | +2.4 (6.6) | +2.5 (6.6) | +4.2 (7.2) | n/a | n/a |
| every piece at 50% (benchmark) | 0.50 / 0.50 / 0.50 / 0.50 / 0.50 / 0.50 | +13.5 (13.6) | +13.9 (9.8) | +11.8 (9.4) | +2.7 (8.2) | +8.0 (9.4) | -8.9 (13.2) | -7.5 (12.7) |

Best-case strata used (study factor vs L6M, the most favourable applicable stratum per piece): 70/30 split PRE positive & placebo beaten +0.06 -> size 0.01; PE 45-s confirmation t-stat(6m) 2-3 -0.23 -> size 0.00; ER(20) sizer t-stat(6m) >=3 +0.30 -> size 0.36; Asia-stopped cut50 PRE positive -0.39 -> size 0.00; 8-line zone skip PRE positive +0.01 -> size 0.00; Native stop 1.28 t-stat(6m) >=3 +0.70 -> size 0.81. Even there the line is +3.0k L6M against an MDE of 7.0k (the MDE is wide because the ER sizer at 0.36 is active).

**Piece-added-back (each at 100% on top of the shrunk composite):** split -1.5k L6M, PE +2.6k, ER +8.2k, cut +2.7k, zone +2.7k (the split alone, without ER, is a net negative at live lots; its value in the as-coded composite comes with the sizer and the confirmation: +4.3k leave-one-out). The sum of the shrunk expectations of the pieces with a positive expectation (ER +1.0k + Native +1.7k = +2.7k L6M) is the linear cross-check of the engine line +2.2k (the ER 0.03 is lost to integer rounding, hence slightly higher).

## 4. Caveats and questions

* The persistence factors are for rules SELECTED because they were positive in the last 3 and 6 months out of a catalogue dominated by rules that lose to their floor (DS3_PERSISTENCE.md section 8); the Sunday pieces were chosen by the programs on L6M / HOLD too (the 8-line set is post-hoc selected), so the selection assumption fits, but a prior that the structure of the 70/30 split or the PE pattern is real is not in the factors (their PRE and X' leave-one-out values are positive but inside MDE: split +1.3k / +0.6k, PE +0.4k / -0.8k, cut +0.9k / +1.4k). The family factors at t 1-3 are also not tight: entry structure -0.47 (CI -0.66..-0.17 vs L3M), confirmation -0.71; sizing +0.07.
* The study uses its own units; the stack-level families (the cut, the sizer in the lock engine) have the weakest evidence in the study (stack n = 5,680, 17% persistence, factor -1.36); the table's cut row inherits it.
* The Native stop's engine t (5.5) is a unit effect; the evidence for the saving is z = 1.6. If the Native stop is scored with its evidence t (1-2 bucket, exit factor -0.32 to -0.47) it too would be OFF: the honest range for the 'honest number' is therefore +0.0k (Native OFF) to +2.2k (Native 0.81) to +2.7k (Native 100%). The Monday 11-02 stop A/B is the test that settles it.
* Fractional sizes are modelled as probabilities / fractions; D6 has no fractional switches, so the honest number is a forecast of a policy mixture, not a D6 setting. A6 = PB (SS-2 mapping), not PB7. Slip +0.25 per add lot (stress +0.45 in the table). Sunday question, if any, is in MORNING.md only.
* Files: `out/persistsunday/` pieces.pkl (daily $ per book, 8 x 745, for FULL / LOO / ALONE), pieces_table.csv, composite_table.csv / composite_extra.csv / composite.pkl, tge3_*.csv (t >= 3 set), fire_rates.json, bestcase.json, levels.json.
