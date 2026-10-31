# DS3_SIXTY_BINS - the persistence score at >= 0.80 and >= 0.90, and every non-exit rule at >= 0.70 (SX-1, 2026-10-31). POST-HOC, no PASS claim
Research only. Masks capped 20260206, UNTOUCHED never read. Prereg `l2vast/ds3/prereg/SX1_prereg.md` sha256 d8c51a873dd5709d3ce31fd468717bd026f428d43c554e476d5a6bdfbfcbed05 (DECISIONS.md, before any scored cell). Code `l2vast/ds3/code/sx1/` (sx1_bins.py, sx1_bins2.py, sx1_lists.py, mk_bins_md.py), data `l2vast/ds3/out/sx1/` (bins_wf.csv, bins_list.csv, nonexit70_rules.csv). Score = RE-1 logistic (`persist`); lists = SIXTY-1 v2 (`sixty_list60.csv` 903 distinct reps, `sixty_list70.csv` 382 rules).

## PLAIN SENTENCES
**The list has 5 rules at >= 0.80 (list60; 6 in the 382-rule list70 file) and NONE at >= 0.90 (the maximum score on the list is 0.847).** The five are two EXP1 loss-stream exits (0.826, 0.826), two EQR lot-factor sizers (0.847, 0.812) and one EINT1 entry filter (0.845); none of the five is STRICT, TOLERANT-literal or a CANDIDATE (all DEAD tier); the sixth rule of the list70 file (rid 850, EINT1 skipTop3 sig_st1_dist_atr, KB, 0.830) is STRICT and tier CANDIDATE but not TOLERANT. **Both bins are far too thin to read as a hit rate on the list itself.** Out of sample, the only place the score reaches 0.80 with enough rows to count is RE-1's own study table (247,552 rule-months): >= 0.80 has 298 rule-months in 17 of 20 months and 25 program-month clusters, hit rate 94% (month-block CI 72%-97%), 87% of them exit-family rows (profit-protect exits), so it is a one-family bin: the exit rows alone hit 98% (CI 81%-100%, 258 rule-months, 11 months, 12 clusters) against a family-mix base rate of 45%; the non-exit remainder is 40 rule-months at 65% (CI 44%-84%) against a family-mix base of 51% and a family-stratified random pick of 50% (rank 0.95, at the 0.95 bar on the point estimate but with 40 rule-months and a CI that contains the base rate): not separable from its families' base rate. **>= 0.90: 12 rule-months in 5 months (hit 67%, CI 25%-100%): unreadable.** In the stream universe the score never reaches 0.90 and reaches 0.80 only on 43 EINT2 series-months in 3 months (hit 67%, one program): unreadable.

Read-across: the score's out-of-sample strength is a family effect. It selects profit-protect and loss exits (hit 93-99% from 0.60 up, family-mix base 51-52%) and almost nothing else reaches 0.80; for the non-exit families the walk-forward hit rate at >= 0.70 is 51% (CI 45-61%, 227 rule-months) against a 50% family-mix base, and the confirmation family (CF-COMBO, 336 of the 375 non-exit rules at >= 0.70) hits 4% at >= 0.60 in the study. Nothing here changes a size or a tier.

## 1. THE LIST, binned (counts as they stand today)
| list | score cut | rules | exit | non-exit | families | programs (top 8) | STRICT | TOLERANT (literal) | NOW-ONLY | tier CANDIDATE | streamed | D6/D7 runnable |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| list60 (903 distinct reps) | >= 0.70 | 362 | 5 | 357 | {"confirmation": 330, "entry filter": 15, "sizing": 8, "exit": 5, "regime": 4} | {"CF-COMBO POOL": 173, "CF-COMBO stage1ENG": 122, "CF-COMBO FOUR": 23, "CF-COMBO stage1B": 12, "EINT1": 9, "EQR lots_factor": 8, "ZONES-2": 4, "EINT2": 4} | 328 | 7 | 362 | 78 | 32 | 14 |
| list60 (903 distinct reps) | >= 0.80 | 5 | 2 | 3 | {"exit": 2, "sizing": 2, "entry filter": 1} | {"EXP1 loss per-stream fixed": 2, "EQR lots_factor": 2, "EINT1": 1} | 0 | 0 | 5 | 0 | 5 | 2 |
| list60 (903 distinct reps) | >= 0.90 | 0 | 0 | 0 | {} | {} | 0 | 0 | 0 | 0 | 0 | 0 |
| list70 file (382) | >= 0.70 | 382 | 7 | 375 | {"confirmation": 336, "entry filter": 24, "sizing": 10, "exit": 7, "regime": 5} | {"CF-COMBO POOL": 173, "CF-COMBO stage1ENG": 127, "CF-COMBO FOUR": 24, "CF-COMBO stage1B": 12, "EINT1": 10, "ZONES-2": 8, "EQR lots_factor": 8, "EINT2": 5} | 342 | 11 | 382 | 89 | 39 | 16 |
| list70 file (382) | >= 0.80 | 6 | 2 | 4 | {"entry filter": 2, "exit": 2, "sizing": 2} | {"EINT1": 2, "EXP1 loss per-stream fixed": 2, "EQR lots_factor": 2} | 1 | 0 | 6 | 1 | 6 | 2 |
| list70 file (382) | >= 0.90 | 0 | 0 | 0 | {} | {} | 0 | 0 | 0 | 0 | 0 | 0 |

The six rules at >= 0.80 (the five list60 reps plus rid 850 KB EINT1, which is in the list70 file only):
| rid | program | family | book / session | cell | persist | STRICT | TOLERANT | size (shrunk) | tier | streamed |
|---|---|---|---|---|---|---|---|---|---|---|
| 656 | EQR lots_factor | sizing | stack / all | `A¦B¦E¦N @ lots x1.432` | 0.847 | False | False | 0.69 | DEAD | streamed |
| 723 | EINT1 | entry filter | HM / ALL | `skipBot3_htf_d_open_atr¦HM` | 0.845 | False | False | 0.26 | DEAD | streamed |
| 850 | EINT1 | entry filter | KB / ALL | `skipTop3_sig_st1_dist_atr¦KB` | 0.830 | True | False | 0.26 | CANDIDATE | streamed |
| 9016 | EXP1 loss per-stream fixed | exit | D6_PB7_PB5_ASIA / ALL | `D6_PB7_PB5_ASIA¦L7m_m45_n5_b5` | 0.826 | False | False | 0.82 | DEAD | streamed |
| 10444 | EXP1 loss per-stream fixed | exit | SM / ALL | `SM¦L7m_m45_n5_b10` | 0.826 | False | False | 0.82 | DEAD | streamed |
| 657 | EQR lots_factor | sizing | stack / all | `A¦B¦EL¦N @ lots x1.385` | 0.812 | False | False | 0.63 | DEAD | streamed |

## 2. WALK-FORWARD hit rate of the bins (outcome: the rule's next 3 months sum positive; M = 2024-04..2025-11, score at M from data before M)
Hit rate pools rule- (or series-) months; CI = month-block bootstrap (2,000 draws, seed 20261031, so autocorrelated months are not counted as independent) with the Wilson row interval beside; **random-selection placebo** = 500 draws of the same count per month from the named pool; **family-mix base rate** = the hit rate of ALL active rows of the same family and month weighted by the bin's family counts (what the bin would hit if the score added nothing beyond the family); rank = share of placebo draws below the bin (0.95 is the bar). THIN flags follow the prereg rule (< 30 rule-months, < 6 months, < 10 clusters, or one family > 80%).

| universe | bin | rule-months | months | clusters | hit rate [month-block CI] | Wilson | family-mix base | random pick, all active (rank) | random pick, positive 3m+6m pool | random pick, family-stratified (rank) | families | READ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| study-wide (RE-1 predictions, all families) | S>=0.60 | 6,453 | 20 | 78 | 65% [48%-82%] | 64%-66% | 48% | 39% (1.00) | - | 48% (1.00) | exit 3131, sizing 1326, regime 1107, entry filter 711, entry structure 101, confirmation 77 | readable |
| study-wide (RE-1 predictions, all families) | S>=0.70 | 1,995 | 20 | 46 | 93% [81%-97%] | 92%-94% | 52% | 43% (1.00) | - | 52% (1.00) | exit 1768, sizing 170, entry filter 43, regime 8, entry structure 6 | ONE-FAMILY BIN (89% in one family): read the family subsets, not the pooled rate |
| study-wide (RE-1 predictions, all families) | band 0.70-0.80 | 1,697 | 20 | 41 | 93% [79%-97%] | 92%-94% | 53% | 43% (1.00) | - | 53% (1.00) | exit 1510, sizing 139, entry filter 34, regime 8, entry structure 6 | ONE-FAMILY BIN (89% in one family): read the family subsets, not the pooled rate |
| study-wide (RE-1 predictions, all families) | S>=0.80 | 298 | 17 | 25 | 94% [72%-97%] | 91%-96% | 46% | 40% (1.00) | - | 46% (1.00) | exit 258, sizing 31, entry filter 9 | ONE-FAMILY BIN (87% in one family): read the family subsets, not the pooled rate |
| study-wide (RE-1 predictions, all families) | band 0.80-0.90 | 286 | 16 | 23 | 95% [77%-98%] | 92%-97% | 46% | 40% (1.00) | - | 46% (1.00) | exit 255, sizing 25, entry filter 6 | ONE-FAMILY BIN (89% in one family): read the family subsets, not the pooled rate |
| study-wide (RE-1 predictions, all families) | S>=0.90 | 12 | 5 | 5 | 67% [25%-100%] | 39%-86% | 51% | 45% (0.89) | - | 51% (0.77) | sizing 6, exit 3, entry filter 3 | TOO THIN TO READ: 12 rule-months < 30; 5 months < 6; 5 clusters < 10 |
| study-wide, exit family removed | S>=0.70 non-exit | 227 | 20 | 29 | 51% [45%-61%] | 45%-58% | 50% | 38% (1.00) | - | 50% (0.56) | sizing 170, entry filter 43, regime 8, entry structure 6 | readable |
| study-wide, exit family removed | S>=0.80 non-exit | 40 | 13 | 13 | 65% [44%-84%] | 50%-78% | 51% | 44% (0.99) | - | 50% (0.95) | sizing 31, entry filter 9 | readable |
| study-wide, exit family removed | S>=0.90 non-exit | 9 | 3 | 3 | 56% [0%-100%] | 27%-81% | 52% | 48% (0.54) | - | 50% (0.51) | sizing 6, entry filter 3 | TOO THIN TO READ: 9 rule-months < 30; 3 months < 6; 3 clusters < 10 |
| study-wide, exit family only | S>=0.70 exit only | 1,768 | 13 | 17 | 99% [97%-100%] | 98%-99% | 52% | 44% (1.00) | - | 52% (1.00) | exit 1768 | readable (single-family subset) |
| study-wide, exit family only | S>=0.80 exit only | 258 | 11 | 12 | 98% [81%-100%] | 96%-99% | 45% | 39% (1.00) | - | 45% (1.00) | exit 258 | readable (single-family subset) |
| study-wide, exit family only | S>=0.90 exit only | 3 | 2 | 2 | 100% [100%-100%] | 44%-100% | 46% | 35% (0.95) | - | 46% (0.91) | exit 3 | TOO THIN TO READ: 3 rule-months < 30; 2 months < 6; 2 clusters < 10 |
| stream (sizing/entry filter/regime) | S>=0.60 | 1,773 | 20 | 91 | 51% [44%-57%] | 49%-53% | 36% | 34% (1.00) | 42% | 36% (1.00) | sizing 765, entry filter 548, regime 460 | readable |
| stream (sizing/entry filter/regime) | S>=0.70 | 113 | 11 | 11 | 73% [63%-84%] | 65%-81% | 36% | 32% (1.00) | 40% | 36% (1.00) | regime 110, sizing 2, entry filter 1 | ONE-FAMILY BIN (97% in one family): read the family subsets, not the pooled rate |
| stream (sizing/entry filter/regime) | S>=0.80 | 43 | 3 | 3 | 67% [59%-82%] | 53%-80% | 31% | 26% (1.00) | 36% | 31% (1.00) | regime 43 | TOO THIN TO READ: 3 months < 6; 3 clusters < 10; one family holds 100% |
| stream (sizing/entry filter/regime) | S>=0.90 | 0 | 0 | - | no rows (the score never gets there in this universe) | | | | | | | UNREADABLE (empty) |

Base rates: every active stream series 33% positive after 3 months; every rule-month in RE-1's study table 43%.

**What the table says, plainly.**
1. **>= 0.90 cannot be read anywhere.** The list has none; the study table has 12 rule-months (5 months, 5 clusters; 6 sizing, 3 exit, 3 entry-filter) at 67% with a CI of 25-100%; the stream universe has none. Any sentence about a 0.90 hit rate would be invented.
2. **>= 0.80 is an exit-family bin.** 87% of its 298 study rule-months are exit rows from the profit-protect and loss programs (H1_profit 245, H2_loss 13) in 11 months; they persisted (98%) because those exits persisted in 2025 for a structural reason (DS3_PERSISTENCE_SUNDAY.md), not because 0.80 is sharper than 0.70 (the 0.70-0.80 band hit 93%, the 0.80-0.90 band 95%: the same). Only five list rules sit in the bin and none of the five is a profit-protect exit (two are EXP1 loss exits).
3. **The non-exit part of >= 0.80 is 40 rule-months** (65%, CI 44%-84%, 13 months, 13 clusters, top family 78%): above the 51% family-mix base on the point estimate, rank 0.95 against a family-stratified pick (at the bar) and a CI that contains the base rate. LEAD at best; thin.
4. **The stream universe (the only one with weekly streams for list rules) cannot test 0.80:** its three families (sizing, entry filter, regime) reach 0.80 on 43 EINT2 series-months in 3 months (67%, one program, one family): unreadable. At >= 0.70 it reads 74% on 113 series-months, 110 of them one program (EINT2 day-type rules), i.e. one cluster per month (11 clusters), against a family-mix base of 36%: the score does add over the family there, from a small, correlated sample.
5. **The score's value is its family loading.** Without exit rows the study-wide >= 0.60 bin hits 39% (CI 31-53%) against a 44% family-mix base (rank 0.00), and the >= 0.70 non-exit bin 51% against 50%.

## 3. EVERY NON-EXIT RULE AT >= 0.70 (375 of the 382 in `sixty_list70.csv`; the 7 exit rules are not listed here)
Counts: 375 non-exit rules; 34 streamed (weekly stream, so a TOLERANT worst-20 and a portfolio line exist) and 341 ledger-only; D6/D7: 12 can be run or partly run, 363 cannot; STRICT 339; TOLERANT literal 9 yes / 25 evaluated-no (and 341 unevaluated because there is no weekly stream); NOW-ONLY 375 (all; that is the weakest column); tier CANDIDATE 89, DEAD 286. **None is LIVE-ELIGIBLE** (DS3_SIXTY_RUN tier rule); shrunk size `size` is SIXTY-1's `size_rec` (fraction of the rule's full size, 0 = family shrinkage <= 0).

| program | rules | family | score range | STRICT | tier CANDIDATE | streamed | D6/D7 runnable |
|---|---|---|---|---|---|---|---|
| ADDUW B2 | 1 | sizing | 0.714-0.714 | 1 | 1 | 1 | 0 |
| CF-COMBO FOUR | 24 | confirmation | 0.711-0.746 | 24 | 16 | 0 | 0 |
| CF-COMBO POOL | 173 | confirmation | 0.704-0.746 | 173 | 17 | 0 | 0 |
| CF-COMBO stage1B | 12 | confirmation | 0.746-0.746 | 0 | 0 | 0 | 0 |
| CF-COMBO stage1ENG | 127 | confirmation | 0.702-0.746 | 127 | 42 | 0 | 0 |
| EINT1 | 10 | entry filter | 0.701-0.845 | 3 | 3 | 10 | 0 |
| EINT2 | 5 | regime | 0.715-0.796 | 0 | 0 | 5 | 3 |
| EQR lots_factor | 8 | sizing | 0.701-0.847 | 1 | 0 | 8 | 8 |
| META FS1 | 2 | entry filter | 0.704-0.708 | 0 | 0 | 1 | 0 |
| META FS2 | 3 | entry filter | 0.708-0.755 | 1 | 1 | 0 | 0 |
| SPLIT 70/30 | 1 | sizing | 0.706-0.706 | 1 | 1 | 0 | 1 |
| UF-ENTRY c1 | 1 | entry filter | 0.709-0.709 | 1 | 1 | 1 | 0 |
| ZONES-2 | 8 | entry filter | 0.701-0.749 | 7 | 7 | 8 | 0 |

**Caveat on the 336 CF-COMBO rows (277 share the single value 0.7461):** their scores were recomputed by SIXTY-1 from a corrected per-contract gain with a large 6-month t, and sit at the logistic's ceiling (0.70-0.746); they are counterfactual confirmation combinations, ledger-only, with no weekly stream, and the study-wide confirmation family hit 4% at >= 0.60 (77 rule-months). They are listed because the ask was every rule, not because 336 independent bets exist.

### 3a. The 39 non-CF-COMBO rules (full detail)

| rid | program | family | book / session | cell | score | D6/D7 mapping (group / property / value) | STRICT | TOLERANT (literal) | NOW-ONLY | size | tier | stream | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 656 | EQR lots_factor | sizing | stack / all | `A¦B¦E¦N @ lots x1.432` | 0.847 | PARTLY: D6 per-book lots property (size property of each book); value: lots multiplier x1.432 on every book of the set (stack scaler, not a per-trade rule) | n | not TOLERANT | Y | 0.69 | DEAD | streamed | L3M<=MDE;PRE/X'<=0;unit-inflated (equal-risk lot factor credits extra lots) |
| 723 | EINT1 | entry filter | HM / ALL | `skipBot3_htf_d_open_atr¦HM` | 0.845 | not runnable: needs engine feature (htf_d_open_atr) computed in NT8 and a filter/sizer slot; only ER(20) sizer exists (shadow) | n | not TOLERANT | Y | 0.26 | DEAD | streamed | PRE/X'<=0;PRE/X' beyond -0.5MDE;placebo rank missing |
| 850 | EINT1 | entry filter | KB / ALL | `skipTop3_sig_st1_dist_atr¦KB` | 0.830 | not runnable: needs engine feature (sig_st1_dist_atr) computed in NT8 and a filter/sizer slot; only ER(20) sizer exists (shadow) | Y | not TOLERANT | Y | 0.26 | CANDIDATE | streamed | placebo rank missing |
| 657 | EQR lots_factor | sizing | stack / all | `A¦B¦EL¦N @ lots x1.385` | 0.812 | PARTLY: D6 per-book lots property (size property of each book); value: lots multiplier x1.385 on every book of the set (stack scaler, not a per-trade rule) | n | not TOLERANT | Y | 0.63 | DEAD | streamed | L3M<=MDE;PRE/X'<=0;unit-inflated (equal-risk lot factor credits extra lots) |
| 703 | EINT2 | regime | HM / ALL | `f.exclfirst90.all¦HM` | 0.796 | RUNS (parameter differs): D7 group 12 rule (a) skip first N min of each session (ships OFF); value: N=90 min (shipped slot value 60; N=90 needs a slot change); books/session as the cell | n | not TOLERANT | Y | 0.00 | DEAD | streamed | PRE/X'<=0;placebo<0.95 |
| 659 | EQR lots_factor | sizing | stack / all | `A¦B¦E¦M @ lots x1.367` | 0.766 | PARTLY: D6 per-book lots property (size property of each book); value: lots multiplier x1.367 on every book of the set (stack scaler, not a per-trade rule) | n | not TOLERANT | Y | 0.55 | DEAD | streamed | L3M<=MDE;PRE/X'<=0;unit-inflated (equal-risk lot factor credits extra lots) |
| 3379 | EINT2 | regime | WT / ALL | `d1.1000g.post30.up1.5¦WT` | 0.763 | not runnable: day-type/calendar rule; needs an NT8 day-type module (not in D6 v2.3b/D7 v1.0) | n | not TOLERANT | Y | 0.00 | DEAD | streamed | PRE/X'<=0;PRE/X' beyond -0.5MDE;placebo<0.95 |
| 752 | EINT2 | regime | HM¦asia / asia | `f.exclfirst90.all¦HM¦asia` | 0.757 | RUNS (parameter differs): D7 group 12 rule (a) skip first N min of each session (ships OFF); value: N=90 min (shipped slot value 60; N=90 needs a slot change); books/session as the cell | n | not TOLERANT | Y | 0.00 | DEAD | streamed | PRE/X'<=0;placebo<0.95 |
| 895 | META FS2 | entry filter | nyam / nyam | `H3_ENS¦P2¦nyam¦cfg436` | 0.755 | not runnable: model-scored filter (needs a scoring module) | n | TOLERANT unevaluated (no weekly stream) | Y | 0.23 | DEAD | ledger-only | PRE/X'<=0;placebo<0.95;no recomputable stream (ledger value only) |
| 4463 | ZONES-2 | entry filter | ALL / ALL | `entry¦zones2¦ahead¦FIB¦ote62_up¦15m¦var=fresh¦d=40pts¦act=b73¦base=MKT` | 0.749 | not runnable: needs zone engine (levels/FIB/ichimoku) and an entry-assign slot; D7 has no zone slots | Y | TOLERANT | Y | 0.23 | CANDIDATE | streamed | L3M<=MDE;placebo rank missing;stream not tied out to ledger (zones, per-contract ledger vs stack stream) |
| 21 | EINT1 | entry filter | HM / ALL | `skipBot3_htf_wk_open_atr¦HM` | 0.749 | not runnable: needs engine feature (htf_wk_open_atr) computed in NT8 and a filter/sizer slot; only ER(20) sizer exists (shadow) | Y | not TOLERANT | Y | 0.23 | CANDIDATE | streamed | placebo rank missing |
| 878 | EQR lots_factor | sizing | stack / all | `C¦F¦A06+B02 @ lots x1.228` | 0.746 | PARTLY: D6 per-book lots property (size property of each book); value: lots multiplier x1.228 on every book of the set (stack scaler, not a per-trade rule) | n | TOLERANT | Y | 0.52 | DEAD | streamed | L3M<=MDE;PRE/X'<=0;placebo<0.95;unit-inflated (equal-risk lot factor credits extra lots) |
| 1127 | EINT1 | entry filter | KB / ALL | `sizeLo_sig_st1_dist_atr¦KB` | 0.745 | not runnable: needs engine feature (sig_st1_dist_atr) computed in NT8 and a filter/sizer slot; only ER(20) sizer exists (shadow) | n | not TOLERANT | Y | 0.23 | DEAD | streamed | PRE/X'<=0;placebo rank missing |
| 4497 | ZONES-2 | entry filter | ALL / ALL | `entry¦zones2¦ahead¦FIB¦ote62_up¦15m¦var=fresh¦d=75pct¦act=b73¦base=MKT` | 0.745 | not runnable: needs zone engine (levels/FIB/ichimoku) and an entry-assign slot; D7 has no zone slots | Y | TOLERANT | Y | 0.23 | CANDIDATE | streamed | L3M<=MDE;placebo rank missing;stream not tied out to ledger (zones, per-contract ledger vs stack stream) |
| 660 | EQR lots_factor | sizing | stack / all | `A¦B¦EL¦M @ lots x1.346` | 0.744 | PARTLY: D6 per-book lots property (size property of each book); value: lots multiplier x1.346 on every book of the set (stack scaler, not a per-trade rule) | n | not TOLERANT | Y | 0.51 | DEAD | streamed | L3M<=MDE;PRE/X'<=0;unit-inflated (equal-risk lot factor credits extra lots) |
| 1882 | META FS2 | entry filter | KB-asia / KB-asia | `H1_3m¦P5¦KB-asia¦cfg574` | 0.732 | not runnable: model-scored filter (needs a scoring module) | n | TOLERANT unevaluated (no weekly stream) | Y | 0.22 | DEAD | ledger-only | PRE/X'<=0;PRE/X' beyond -0.5MDE;no recomputable stream (ledger value only) |
| 4353 | ZONES-2 | entry filter | ALL / ALL | `entry¦zones2¦ahead¦FIB¦ote62_up¦15m¦var=fresh¦d=20pts¦act=wt¦base=SPL` | 0.727 | not runnable: needs zone engine (levels/FIB/ichimoku) and an entry-assign slot; D7 has no zone slots | Y | TOLERANT | Y | 0.22 | CANDIDATE | streamed | L3M<=MDE;placebo rank missing;stream not tied out to ledger (zones, per-contract ledger vs stack stream) |
| 874 | EINT1 | entry filter | KB / ALL | `skipBot3_sig_st1_age¦KB` | 0.725 | not runnable: needs engine feature (sig_st1_age) computed in NT8 and a filter/sizer slot; only ER(20) sizer exists (shadow) | n | not TOLERANT | Y | 0.22 | DEAD | streamed | PRE/X'<=0;placebo rank missing |
| 664 | EINT2 | regime | STACK6 / ALL | `f.exclfirst90.all¦STACK6` | 0.722 | RUNS (parameter differs): D7 group 12 rule (a) skip first N min of each session (ships OFF); value: N=90 min (shipped slot value 60; N=90 needs a slot change); books/session as the cell | n | not TOLERANT | Y | 0.00 | DEAD | streamed | PRE/X'<=0;PRE/X' beyond -0.5MDE;placebo<0.95 |
| 51 | EINT1 | entry filter | KB / ALL | `skipTop3_htf_tr20¦KB` | 0.719 | not runnable: needs engine feature (htf_tr20) computed in NT8 and a filter/sizer slot; only ER(20) sizer exists (shadow) | n | not TOLERANT | Y | 0.21 | DEAD | streamed | PRE/X'<=0;placebo rank missing |
| 4466 | ZONES-2 | entry filter | ALL / ALL | `entry¦zones2¦ahead¦FIB¦ote62_up¦15m¦var=any¦d=40pts¦act=b73¦base=MKT` | 0.718 | not runnable: needs zone engine (levels/FIB/ichimoku) and an entry-assign slot; D7 has no zone slots | Y | TOLERANT | Y | 0.21 | CANDIDATE | streamed | L3M<=MDE;placebo rank missing;stream not tied out to ledger (zones, per-contract ledger vs stack stream) |
| 4496 | ZONES-2 | entry filter | ALL / ALL | `entry¦zones2¦ahead¦FIB¦ote62_up¦15m¦var=fresh¦d=30pts¦act=b73¦base=SPL` | 0.717 | not runnable: needs zone engine (levels/FIB/ichimoku) and an entry-assign slot; D7 has no zone slots | Y | TOLERANT | Y | 0.21 | CANDIDATE | streamed | L3M<=MDE;placebo rank missing;stream not tied out to ledger (zones, per-contract ledger vs stack stream) |
| 4504 | ZONES-2 | entry filter | ALL / ALL | `entry¦zones2¦ahead¦FIB¦ote62_up¦15m¦var=fresh¦d=50pct¦act=b73¦base=SPL` | 0.717 | not runnable: needs zone engine (levels/FIB/ichimoku) and an entry-assign slot; D7 has no zone slots | Y | TOLERANT | Y | 0.21 | CANDIDATE | streamed | L3M<=MDE;placebo rank missing;stream not tied out to ledger (zones, per-contract ledger vs stack stream) |
| 207 | EQR lots_factor | sizing | stack / all | `E¦SL¦WT¦NY¦P2 @ lots x1.016` | 0.716 | PARTLY: D6 per-book lots property (size property of each book); value: lots multiplier x1.016 on every book of the set (stack scaler, not a per-trade rule) | Y | not TOLERANT | Y | 0.45 | DEAD | streamed | L3M<=MDE;placebo<0.95;unit-inflated (equal-risk lot factor credits extra lots) |
| 2693 | EINT2 | regime | WT / ALL | `wf_lot.onvix.A3¦WT` | 0.715 | not runnable: day-type/calendar rule; needs an NT8 day-type module (not in D6 v2.3b/D7 v1.0) | n | not TOLERANT | Y | 0.00 | DEAD | streamed | PRE/X'<=0;placebo rank missing |
| 1272 | ADDUW B2 | sizing | WT / all | `WT ci=23 enter 50% of size, add the rest in 1 stage(s) when under water by 5 pt, add-gate=imb5>=.3, target=kept at origi` | 0.714 | not runnable: scale-in/add module with add-gate; policy_add_candidate.txt exists, not wired in D6 v2.3b | Y | TOLERANT | Y | 0.45 | CANDIDATE | streamed | placebo rank missing |
| 6250 | EINT1 | entry filter | HM / ALL | `skipBot3_htf_pd_pos¦HM` | 0.713 | not runnable: needs engine feature (htf_pd_pos) computed in NT8 and a filter/sizer slot; only ER(20) sizer exists (shadow) | n | not TOLERANT | Y | 0.21 | DEAD | streamed | PRE/X'<=0;PRE/X' beyond -0.5MDE;placebo rank missing |
| 6457 | EINT1 | entry filter | KB / ALL | `skipTop3_sig_slope¦KB` | 0.711 | not runnable: needs engine feature (sig_slope) computed in NT8 and a filter/sizer slot; only ER(20) sizer exists (shadow) | n | not TOLERANT | Y | 0.21 | DEAD | streamed | PRE/X'<=0;PRE/X' beyond -0.5MDE;placebo rank missing |
| 6256 | UF-ENTRY c1 | entry filter | all 6 engine books (ST HM WT KB SM PE, pooled lock engine) / all | `UF1¦G2¦F=0.7¦X=3¦ev=IMBF20 ¦ ref=market` | 0.709 | not runnable: not assessed against D6/D7 by SIXTY-1: entry-side UF cell (imbalance-flush confirmed split entry) needing L2 state features and an entry-assign slot; D6 group 05 has the 70/30 split only | Y | not TOLERANT | Y | 0.21 | CANDIDATE | streamed | L3M<=MDE;placebo rank missing |
| 1532 | META FS1 | entry filter | nyam / nyam | `H4_3m¦P1¦nyam¦cfg440` | 0.708 | not runnable: model-scored filter (needs a scoring module) | n | not TOLERANT | Y | 0.21 | DEAD | streamed | L3M<=MDE;PRE/X'<=0;placebo<0.95 |
| 940 | META FS2 | entry filter | HM-asia / HM-asia | `H2_ENS¦P3¦HM-asia¦cfg797` | 0.708 | not runnable: model-scored filter (needs a scoring module) | Y | TOLERANT unevaluated (no weekly stream) | Y | 0.21 | CANDIDATE | ledger-only | no recomputable stream (ledger value only) |
| 137 | EINT1 | entry filter | KB / ALL | `sizeHi_sd_pd_hi_atr¦KB` | 0.708 | not runnable: needs engine feature (sd_pd_hi_atr) computed in NT8 and a filter/sizer slot; only ER(20) sizer exists (shadow) | Y | TOLERANT | Y | 0.21 | CANDIDATE | streamed | placebo rank missing |
| 4362 | ZONES-2 | entry filter | ALL / ALL | `entry¦zones2¦ahead¦FIB¦ote62_up¦15m¦var=fresh¦d=20pts¦act=wt¦base=MKT` | 0.706 | not runnable: needs zone engine (levels/FIB/ichimoku) and an entry-assign slot; D7 has no zone slots | Y | not TOLERANT | Y | 0.20 | CANDIDATE | streamed | L3M<=MDE;placebo rank missing;stream not tied out to ledger (zones, per-contract ledger vs stack stream) |
| 6087 | SPLIT 70/30 | sizing | STACK / all | `fam=F5¦F=0.7¦X=10¦N=2¦chase=none¦veto=v4 [STACK]` | 0.706 | RUNS (partly): D6 entry group 05 split_F (panel setting); value: split_F=0.7 (X=10, N=2 are not panel properties) | Y | TOLERANT unevaluated (no weekly stream) | Y | 0.43 | CANDIDATE | ledger-only | placebo rank missing;no recomputable stream (ledger value only) |
| 2623 | META FS1 | entry filter | nypm / nypm | `H3_3m¦P2¦nypm¦cfg516` | 0.704 | not runnable: model-scored filter (needs a scoring module) | n | TOLERANT unevaluated (no weekly stream) | Y | 0.20 | DEAD | ledger-only | PRE/X'<=0;PRE/X' beyond -0.5MDE;M-basis gain is a target-fill artefact / N-basis L3M<=0;no recomputable stream (ledger v |
| 828 | EINT1 | entry filter | HM / ALL | `skipBot3_htf_on_ratio¦HM` | 0.701 | not runnable: needs engine feature (htf_on_ratio) computed in NT8 and a filter/sizer slot; only ER(20) sizer exists (shadow) | n | not TOLERANT | Y | 0.20 | DEAD | streamed | PRE/X'<=0;placebo rank missing |
| 13786 | ZONES-2 | entry filter | ALL / ALL | `entry¦zones2¦stacked¦SET¦var=any¦d=50pct¦act=wt¦base=MKT` | 0.701 | not runnable: needs zone engine (levels/FIB/ichimoku) and an entry-assign slot; D7 has no zone slots | n | not TOLERANT | Y | 0.20 | DEAD | streamed | L3M<=MDE;PRE/X'<=0;placebo rank missing;stream not tied out to ledger (zones, per-contract ledger vs stack stream) |
| 658 | EQR lots_factor | sizing | stack / all | `A¦B¦EPL¦M @ lots x1.388` | 0.701 | PARTLY: D6 per-book lots property (size property of each book); value: lots multiplier x1.388 on every book of the set (stack scaler, not a per-trade rule) | n | not TOLERANT | Y | 0.42 | DEAD | streamed | L3M<=MDE;PRE/X'<=0;unit-inflated (equal-risk lot factor credits extra lots) |
| 746 | EQR lots_factor | sizing | stack / all | `C¦A¦A04 @ lots x1.287` | 0.701 | PARTLY: D6 per-book lots property (size property of each book); value: lots multiplier x1.287 on every book of the set (stack scaler, not a per-trade rule) | n | not TOLERANT | Y | 0.42 | DEAD | streamed | L3M<=MDE;PRE/X'<=0;placebo<0.95;unit-inflated (equal-risk lot factor credits extra lots) |

### 3b. The 336 CF-COMBO rules (ledger-only; D6/D7: not runnable, counterfactual combination, not assessed)

| rid | program | book / session | mechanic and cell | score | STRICT | TOLERANT (literal) | NOW-ONLY | size | tier |
|---|---|---|---|---|---|---|---|---|---|
| 100764 | CF-COMBO FOUR | DN / ALL | `AND(CFA:vwap¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100763 | CF-COMBO FOUR | DN / ALL | `AND(CFA:vwap¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100767 | CF-COMBO FOUR | DN / ALL | `AND(CFA:vwap¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100765 | CF-COMBO FOUR | DN / ALL | `AND(CFA:vwap¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100768 | CF-COMBO FOUR | DN / ALL | `AND(CFA:vwap¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100766 | CF-COMBO FOUR | DN / ALL | `AND(CFA:vwap¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ b_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100751 | CF-COMBO FOUR | DN / ALL | `AND(pd50¦5m+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100759 | CF-COMBO FOUR | DN / ALL | `AND(pd50¦5m+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100758 | CF-COMBO FOUR | DN / ALL | `AND(pd50¦5m+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100752 | CF-COMBO FOUR | DN / ALL | `AND(pd50¦5m+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100741 | CF-COMBO FOUR | DN / ALL | `AND(ote705¦2m+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100750 | CF-COMBO FOUR | DN / ALL | `AND(ote705¦2m+MOM:RSI7<30¦1m+FLOW:thick_q33) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100749 | CF-COMBO FOUR | DN / ALL | `AND(ote705¦2m+MOM:RSI7<30¦1m+FLOW:thick_q33) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100742 | CF-COMBO FOUR | DN / ALL | `AND(ote705¦2m+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100711 | CF-COMBO FOUR | SM / ALL | `AND(OB¦30s+MOM:RSI7<30¦1m+FLOW:imb5_ge_q20) ¦ b_mid¦F0.7` | 0.729 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100755 | CF-COMBO FOUR | DN / ALL | `AND(CFA:b1¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ c2_mid¦F0.7` | 0.728 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100756 | CF-COMBO FOUR | DN / ALL | `AND(CFA:b1¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ c2_near¦F0.7` | 0.728 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100757 | CF-COMBO FOUR | DN / ALL | `AND(CFA:b1¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ c2_far¦F0.7` | 0.728 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100761 | CF-COMBO FOUR | DN / ALL | `AND(CFA:b1¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ b_mid¦F0.7` | 0.727 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100762 | CF-COMBO FOUR | DN / ALL | `AND(CFA:b1¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ b_near¦F0.7` | 0.727 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100760 | CF-COMBO FOUR | DN / ALL | `AND(CFA:b1¦avwap+MOM:RSI2<10¦1m+FLOW:thick_q33) ¦ b_far¦F0.7` | 0.727 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100712 | CF-COMBO FOUR | SM / ALL | `AND(OB¦30s+MOM:RSI7<30¦1m+FLOW:imb5_ge_q20) ¦ c2_mid¦F0.7` | 0.724 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100715 | CF-COMBO FOUR | SM / ALL | `AND(OB¦30s+MOM:RSI7<30¦1m+FLOW:imb5_ge_q20) ¦ b_near¦F0.7` | 0.712 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100716 | CF-COMBO FOUR | SM / ALL | `AND(OB¦30s+MOM:RSI7<30¦1m+FLOW:imb5_ge_q20) ¦ c2_near¦F0.7` | 0.711 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100520 | CF-COMBO POOL | PE / ALL | `AND(OB¦1m+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100572 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+CFA:vwap¦day) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100566 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+CFA:vwap¦day+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100570 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+OB¦1m+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100565 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+OB¦1m+CFA:vwap¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100554 | CF-COMBO POOL | ST / ALL | `AND(OB¦1m+pd50¦5m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100546 | CF-COMBO POOL | ST / ALL | `AND(OB¦1m+pd50¦5m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100555 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+pd50¦5m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100568 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+OB¦1m+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100670 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:vwap¦avwap) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100538 | CF-COMBO POOL | PE / ALL | `AND(iplFVG¦30s+CFA:vah¦sw15) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100687 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+CFA:b1¦avwap) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100582 | CF-COMBO POOL | MV / ALL | `AND(iFVG¦1m+rnd50) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100525 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:val¦sw15) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100535 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:vah¦sw15) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100527 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:vah¦sw15) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100541 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:vah¦sw15) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100530 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:poc¦sw15) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100533 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:poc¦sw15) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100579 | CF-COMBO POOL | MV / ALL | `AND(OB¦1m+rnd50) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100543 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:poc¦sw15) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100593 | CF-COMBO POOL | MV / ALL | `AND(iplFVG¦1m+rnd50) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100583 | CF-COMBO POOL | MV / ALL | `AND(iplFVG¦1m+rnd50) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100531 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:vah¦sw15) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100519 | CF-COMBO POOL | PE / ALL | `AND(OB¦1m+CFA:vwap¦avwap+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100562 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+CFA:vwap¦avwap+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100564 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+CFA:vwap¦avwap+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100563 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+CFA:vwap¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100575 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+CFA:b1¦avwap) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100569 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100692 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+CFA:b1¦avwap) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100549 | CF-COMBO POOL | ST / ALL | `AND(OB¦1m+pd50¦5m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100558 | CF-COMBO POOL | ST / ALL | `AND(OB¦1m+pd50¦5m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100545 | CF-COMBO POOL | PE / ALL | `AND(iplFVG¦30s+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100539 | CF-COMBO POOL | PE / ALL | `AND(iplFVG¦30s+CFA:vah¦sw15) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100686 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+CFA:vwap¦avwap) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100690 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+CFA:vwap¦avwap) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100680 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+CFA:vwap¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100581 | CF-COMBO POOL | MV / ALL | `AND(iplFVG¦1m+rnd50) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100681 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:b1¦avwap) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100669 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:b1¦avwap) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100685 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+C2:ha¦30s¦HA_nolow2) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100666 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:vwap¦day) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100673 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:vwap¦day) ¦ b_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100684 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+CFA:vwap¦day) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100682 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+CFA:vwap¦day) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100674 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100435 | CF-COMBO POOL | DN / ALL | `AND(FVG¦15s+pd50¦5m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100441 | CF-COMBO POOL | DN / ALL | `AND(FVG¦15s+pd50¦5m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100446 | CF-COMBO POOL | DN / ALL | `AND(FVG¦15s+ote705¦2m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100452 | CF-COMBO POOL | DN / ALL | `AND(FVG¦15s+ote705¦2m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100437 | CF-COMBO POOL | DN / ALL | `AND(iFVG¦2m+ote705¦2m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100428 | CF-COMBO POOL | DN / ALL | `AND(OB¦1m+pd50¦5m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100426 | CF-COMBO POOL | DN / ALL | `AND(OB¦1m+pd50¦5m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100453 | CF-COMBO POOL | DN / ALL | `AND(FVG¦15s+ote705¦2m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100447 | CF-COMBO POOL | DN / ALL | `AND(FVG¦15s+ote705¦2m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100439 | CF-COMBO POOL | DN / ALL | `AND(CFA:b2¦avwap+ote705¦2m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100438 | CF-COMBO POOL | DN / ALL | `AND(CFA:b2¦avwap+ote705¦2m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100448 | CF-COMBO POOL | DN / ALL | `AND(OB¦1m+ote705¦2m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100450 | CF-COMBO POOL | DN / ALL | `AND(OB¦1m+ote705¦2m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100444 | CF-COMBO POOL | DN / ALL | `AND(iFVG¦2m+ote705¦2m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100445 | CF-COMBO POOL | DN / ALL | `AND(iFVG¦2m+ote705¦2m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100436 | CF-COMBO POOL | DN / ALL | `AND(iFVG¦2m+ote705¦2m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100468 | CF-COMBO POOL | HM / ALL | `AND(OB¦45s+OB¦1m+ote79¦15s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100474 | CF-COMBO POOL | HM / ALL | `AND(OB¦45s+FVG¦15s+ote79¦15s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100584 | CF-COMBO POOL | MV / ALL | `AND(FVG¦45s+rnd50) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100587 | CF-COMBO POOL | MV / ALL | `AND(FVG¦45s+rnd50) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100602 | CF-COMBO POOL | MV / ALL | `AND(FVG¦45s+rnd50) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100642 | CF-COMBO POOL | MA / ALL | `AND(FVG¦15s+ote705¦1m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100648 | CF-COMBO POOL | MA / ALL | `AND(FVG¦15s+ote705¦1m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100460 | CF-COMBO POOL | HM / ALL | `AND(FVG¦45s+ote79¦15s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100461 | CF-COMBO POOL | HM / ALL | `AND(FVG¦45s+ote79¦15s) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100427 | CF-COMBO POOL | DN / ALL | `AND(OB¦1m+pd50¦5m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100429 | CF-COMBO POOL | DN / ALL | `AND(OB¦1m+pd50¦5m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100451 | CF-COMBO POOL | DN / ALL | `AND(OB¦1m+ote705¦2m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100449 | CF-COMBO POOL | DN / ALL | `AND(OB¦1m+ote705¦2m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100646 | CF-COMBO POOL | MA / ALL | `AND(FVG¦15s+ote705¦1m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100440 | CF-COMBO POOL | DN / ALL | `AND(FVG¦15s+pd50¦5m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100434 | CF-COMBO POOL | DN / ALL | `AND(FVG¦15s+pd50¦5m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100547 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+pd50¦5m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100641 | CF-COMBO POOL | MA / ALL | `AND(CFA:b2¦day+ote79¦2m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100640 | CF-COMBO POOL | MA / ALL | `AND(CFA:b2¦day+ote79¦2m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100639 | CF-COMBO POOL | MA / ALL | `AND(CFA:b2¦day+ote79¦2m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100652 | CF-COMBO POOL | MA / ALL | `AND(CFA:b2¦avwap+ote705¦1m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100653 | CF-COMBO POOL | MA / ALL | `AND(CFA:b2¦avwap+ote705¦1m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100490 | CF-COMBO POOL | KB / ALL | `AND(iFVG¦15s+CFA:vwap¦day) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100431 | CF-COMBO POOL | DN / ALL | `AND(iFVG¦2m+pd50¦5m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100600 | CF-COMBO POOL | MV / ALL | `AND(FVG¦45s+rnd50) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100487 | CF-COMBO POOL | KB / ALL | `AND(iFVG¦15s+CFA:vwap¦avwap+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100508 | CF-COMBO POOL | KB / ALL | `AND(iFVG¦15s+CFA:vwap¦avwap) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100492 | CF-COMBO POOL | KB / ALL | `AND(iFVG¦15s+CFA:vwap¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100509 | CF-COMBO POOL | KB / ALL | `AND(iFVG¦15s+CFA:b1¦day) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100499 | CF-COMBO POOL | KB / ALL | `AND(iFVG¦15s+CFA:b1¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100513 | CF-COMBO POOL | KB / ALL | `AND(iFVG¦15s+CFA:b1¦avwap) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100643 | CF-COMBO POOL | MA / ALL | `AND(FVG¦15s+ote705¦1m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100595 | CF-COMBO POOL | MV / ALL | `AND(OB¦1m+rnd50) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100598 | CF-COMBO POOL | MV / ALL | `AND(iplFVG¦1m+rnd50) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100590 | CF-COMBO POOL | MV / ALL | `AND(iFVG¦1m+rnd50) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100580 | CF-COMBO POOL | MV / ALL | `AND(iFVG¦1m+rnd50) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100551 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+pd50¦5m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100594 | CF-COMBO POOL | MV / ALL | `AND(iFVG¦1m+rnd50) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100592 | CF-COMBO POOL | MV / ALL | `AND(OB¦30s+rnd50) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100576 | CF-COMBO POOL | MV / ALL | `AND(OB¦30s+rnd50) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100578 | CF-COMBO POOL | MV / ALL | `AND(OB¦30s+rnd50) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100552 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+pd50¦5m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100591 | CF-COMBO POOL | MV / ALL | `AND(OB¦1m+rnd50) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100577 | CF-COMBO POOL | MV / ALL | `AND(OB¦1m+rnd50) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100567 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100678 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:b1¦avwap) ¦ b_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100553 | CF-COMBO POOL | ST / ALL | `AND(iplFVG¦30s+pd50¦5m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100548 | CF-COMBO POOL | ST / ALL | `AND(iplFVG¦30s+pd50¦5m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100557 | CF-COMBO POOL | ST / ALL | `AND(iplFVG¦30s+pd50¦5m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100556 | CF-COMBO POOL | ST / ALL | `AND(iplFVG¦30s+pd50¦5m) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100596 | CF-COMBO POOL | MV / ALL | `AND(OB¦30s+rnd50) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100480 | CF-COMBO POOL | HM / ALL | `AND(OB¦30s+ote79¦15s) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100464 | CF-COMBO POOL | HM / ALL | `AND(OB¦30s+ote79¦15s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100466 | CF-COMBO POOL | HM / ALL | `AND(OB¦30s+ote79¦15s) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100482 | CF-COMBO POOL | HM / ALL | `AND(OB¦30s+ote79¦15s) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100504 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+CFA:vwap¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100497 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100481 | CF-COMBO POOL | HM / ALL | `AND(OB¦1m+ote79¦15s) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100463 | CF-COMBO POOL | HM / ALL | `AND(OB¦1m+ote79¦15s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100638 | CF-COMBO POOL | MA / ALL | `AND(CFA:b2¦day+ote79¦2m) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100483 | CF-COMBO POOL | HM / ALL | `AND(OB¦1m+ote79¦15s) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100473 | CF-COMBO POOL | HM / ALL | `AND(OB¦1m+FVG¦15s+ote79¦15s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100477 | CF-COMBO POOL | HM / ALL | `AND(FVG¦45s+ote79¦15s) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100484 | CF-COMBO POOL | HM / ALL | `AND(iFVG¦30s+ote79¦15s) ¦ c1¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100475 | CF-COMBO POOL | HM / ALL | `AND(iFVG¦30s+ote79¦15s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100478 | CF-COMBO POOL | HM / ALL | `AND(FVG¦45s+ote79¦15s) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100462 | CF-COMBO POOL | HM / ALL | `AND(BRK¦30s+ote79¦15s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100430 | CF-COMBO POOL | DN / ALL | `AND(iFVG¦2m+pd50¦5m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100465 | CF-COMBO POOL | HM / ALL | `AND(OB¦1m+ote79¦15s) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100507 | CF-COMBO POOL | KB / ALL | `AND(iFVG¦15s+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100486 | CF-COMBO POOL | KB / ALL | `AND(OB¦45s+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100501 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+iFVG¦15s+CFA:vwap¦day) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100503 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+iFVG¦15s+CFA:vwap¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100505 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+OB¦45s+CFA:vwap¦day) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100500 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+CFA:vwap¦day) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100488 | CF-COMBO POOL | KB / ALL | `AND(iFVG¦15s+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100491 | CF-COMBO POOL | KB / ALL | `AND(iFVG¦15s+CFA:vwap¦avwap+CFA:vwap¦day) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100485 | CF-COMBO POOL | HM / ALL | `AND(iFVG¦30s+ote79¦15s) ¦ a¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100521 | CF-COMBO POOL | PE / ALL | `AND(OB¦1m+CFA:vwap¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100516 | CF-COMBO POOL | PE / ALL | `AND(OB¦1m+CFA:val¦sw15) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100517 | CF-COMBO POOL | PE / ALL | `AND(OB¦1m+CFA:vah¦sw15) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100518 | CF-COMBO POOL | PE / ALL | `AND(OB¦1m+CFA:poc¦sw15) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100523 | CF-COMBO POOL | PE / ALL | `AND(OB¦1m+CFA:b1¦avwap+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100544 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100529 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:val¦sw15) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100476 | CF-COMBO POOL | HM / ALL | `AND(iFVG¦30s+ote79¦15s) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100522 | CF-COMBO POOL | PE / ALL | `AND(OB¦1m+CFA:vwap¦avwap+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100511 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+iFVG¦15s+CFA:vwap¦avwap) ¦ c2_mid¦F0.7` | 0.744 | Y | unevaluated | Y | 0.27 | DEAD |
| 100574 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+OB¦1m+CFA:vwap¦day) ¦ b_far¦F0.7` | 0.742 | Y | unevaluated | Y | 0.27 | DEAD |
| 100694 | CF-COMBO POOL | WT / ALL | `AND(iplFVG¦30s+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.741 | Y | unevaluated | Y | 0.27 | DEAD |
| 100512 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+CFA:vwap¦avwap) ¦ c2_mid¦F0.7` | 0.741 | Y | unevaluated | Y | 0.27 | DEAD |
| 100683 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:vwap¦avwap) ¦ b_mid¦F0.7` | 0.740 | Y | unevaluated | Y | 0.27 | DEAD |
| 100514 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+CFA:b1¦avwap) ¦ c2_mid¦F0.7` | 0.740 | Y | unevaluated | Y | 0.27 | DEAD |
| 100496 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+CFA:b1¦day) ¦ c2_far¦F0.7` | 0.738 | Y | unevaluated | Y | 0.27 | DEAD |
| 100679 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:vwap¦avwap) ¦ c2_near¦F0.7` | 0.734 | Y | unevaluated | Y | 0.27 | DEAD |
| 100515 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+OB¦45s+CFA:vwap¦avwap) ¦ c2_mid¦F0.7` | 0.725 | Y | unevaluated | Y | 0.26 | DEAD |
| 100677 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.724 | Y | unevaluated | Y | 0.26 | DEAD |
| 100528 | CF-COMBO POOL | PE / ALL | `AND(iplFVG¦30s+CFA:vah¦sw15) ¦ c2_near¦F0.7` | 0.722 | Y | unevaluated | Y | 0.26 | DEAD |
| 100526 | CF-COMBO POOL | PE / ALL | `AND(FVG¦15s+CFA:val¦sw15) ¦ c2_mid¦F0.7` | 0.722 | Y | unevaluated | Y | 0.26 | DEAD |
| 100668 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:vwap¦day) ¦ c2_far¦F0.7` | 0.721 | Y | unevaluated | Y | 0.26 | DEAD |
| 100672 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:vwap¦day) ¦ c2_near¦F0.7` | 0.719 | Y | unevaluated | Y | 0.26 | DEAD |
| 100695 | CF-COMBO POOL | WT / ALL | `AND(OB¦45s+CFA:b1¦avwap) ¦ b_near¦F0.7` | 0.718 | Y | unevaluated | Y | 0.26 | DEAD |
| 100691 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:b1¦avwap) ¦ b_near¦F0.7` | 0.715 | Y | unevaluated | Y | 0.26 | DEAD |
| 100494 | CF-COMBO POOL | KB / ALL | `AND(FVG¦2m+CFA:vwap¦avwap) ¦ c2_far¦F0.7` | 0.712 | Y | unevaluated | Y | 0.26 | DEAD |
| 100667 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:b1¦avwap) ¦ c2_far¦F0.7` | 0.711 | Y | unevaluated | Y | 0.26 | DEAD |
| 100671 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:vwap¦avwap) ¦ c2_far¦F0.7` | 0.710 | Y | unevaluated | Y | 0.26 | DEAD |
| 100493 | CF-COMBO POOL | KB / ALL | `AND(FVG¦2m+CFA:b1¦day) ¦ c2_far¦F0.7` | 0.707 | Y | unevaluated | Y | 0.26 | DEAD |
| 100510 | CF-COMBO POOL | KB / ALL | `AND(FVG¦15s+CFA:b1¦day) ¦ c2_mid¦F0.7` | 0.707 | Y | unevaluated | Y | 0.26 | DEAD |
| 100573 | CF-COMBO POOL | ST / ALL | `AND(OB¦30s+CFA:vwap¦day) ¦ b_far¦F0.7` | 0.705 | Y | unevaluated | Y | 0.26 | DEAD |
| 100689 | CF-COMBO POOL | WT / ALL | `AND(OB¦1m+CFA:vwap¦avwap) ¦ b_near¦F0.7` | 0.704 | Y | unevaluated | Y | 0.26 | DEAD |
| 100008 | CF-COMBO stage1B | KB / ALL | `AND(ote705¦45s+ote705¦1m) ¦ c2_near¦F0.0` | 0.746 | n | unevaluated | Y | 0.29 | DEAD |
| 100009 | CF-COMBO stage1B | KB / ALL | `AND(ote705¦45s+ote705¦1m) ¦ b_near¦F0.0` | 0.746 | n | unevaluated | Y | 0.29 | DEAD |
| 100003 | CF-COMBO stage1B | KB / ALL | `AND(ote79¦45s+ote79¦1m) ¦ a¦F0.0` | 0.746 | n | unevaluated | Y | 0.29 | DEAD |
| 100036 | CF-COMBO stage1B | KB / ALL | `AND(ote62¦1m+ote62¦30s) ¦ c1¦F0.0` | 0.746 | n | unevaluated | Y | 0.30 | DEAD |
| 100030 | CF-COMBO stage1B | KB / ALL | `AND(ote62¦1m+ote62¦30s) ¦ c2_near¦F0.0` | 0.746 | n | unevaluated | Y | 0.30 | DEAD |
| 100037 | CF-COMBO stage1B | KB / ALL | `AND(ote62¦1m+ote62¦30s) ¦ a¦F0.0` | 0.746 | n | unevaluated | Y | 0.30 | DEAD |
| 100031 | CF-COMBO stage1B | KB / ALL | `AND(ote62¦1m+ote62¦30s) ¦ b_near¦F0.0` | 0.746 | n | unevaluated | Y | 0.30 | DEAD |
| 100020 | CF-COMBO stage1B | KB / ALL | `AND(ote705¦30s+ote705¦45s) ¦ c1¦F0.0` | 0.746 | n | unevaluated | Y | 0.30 | DEAD |
| 100018 | CF-COMBO stage1B | KB / ALL | `AND(ote705¦30s+ote705¦45s) ¦ c2_near¦F0.0` | 0.746 | n | unevaluated | Y | 0.30 | DEAD |
| 100019 | CF-COMBO stage1B | KB / ALL | `AND(ote705¦30s+ote705¦45s) ¦ b_near¦F0.0` | 0.746 | n | unevaluated | Y | 0.30 | DEAD |
| 100021 | CF-COMBO stage1B | KB / ALL | `AND(ote705¦30s+ote705¦45s) ¦ a¦F0.0` | 0.746 | n | unevaluated | Y | 0.30 | DEAD |
| 100002 | CF-COMBO stage1B | KB / ALL | `AND(ote79¦45s+ote79¦1m) ¦ c1¦F0.0` | 0.746 | n | unevaluated | Y | 0.29 | DEAD |
| 100089 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(FVG¦15s+FVG¦2m) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100092 | CF-COMBO stage1ENG | KB / ALL | `AND(OB¦30s+iplFVG¦15s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100093 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(FVG¦15s+OB¦45s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100088 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(FVG¦15s+FVG¦2m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100083 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iplFVG¦30s+FVG¦2m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100090 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iplFVG¦30s+FVG¦2m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100098 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iplFVG¦30s+FVG¦2m) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100122 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iFVG¦15s+FVG¦15s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100106 | CF-COMBO stage1ENG | KB / ALL | `AND(OB¦30s+iFVG¦1m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100105 | CF-COMBO stage1ENG | KB / ALL | `AND(OB¦30s+OB¦15s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100101 | CF-COMBO stage1ENG | KB / ALL | `AND(OB¦30s+FVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100077 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iFVG¦15s+FVG¦2m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100080 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iFVG¦15s+FVG¦2m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100081 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iFVG¦15s+FVG¦2m) ¦ b_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100085 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iFVG¦15s+FVG¦2m) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100192 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(iplFVG¦30s+OB¦30s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100188 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(iplFVG¦30s+OB¦30s) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100199 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(iFVG¦30s+OB¦30s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100079 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(FVG¦15s+FVG¦2m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100086 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(FVG¦15s+FVG¦2m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100082 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(FVG¦15s+FVG¦2m) ¦ b_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100110 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iFVG¦15s+FVG¦15s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100076 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(FVG¦15s+OB¦45s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100176 | CF-COMBO stage1ENG | ST / ALL | `AND(OB¦30s+iplFVG¦15s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100185 | CF-COMBO stage1ENG | ST / ALL | `AND(OB¦15s+iFVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100184 | CF-COMBO stage1ENG | ST / ALL | `AND(OB¦15s+FVG¦15s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100148 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iplFVG¦30s+OB¦1m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100139 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iplFVG¦30s+OB¦1m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100162 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦30s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100372 | CF-COMBO stage1ENG | MA / ALL | `THEN60s(iFVG¦30s+FVG¦3m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100246 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+BRK¦15s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100196 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(iFVG¦30s+OB¦30s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100190 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(iFVG¦30s+OB¦30s) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100213 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(FVG¦15s+iFVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100204 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(FVG¦15s+OB¦45s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100262 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+iplFVG¦15s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100258 | CF-COMBO stage1ENG | WT / ALL | `AND(FVG¦45s+iFVG¦45s) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100257 | CF-COMBO stage1ENG | WT / ALL | `AND(FVG¦45s+FVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100261 | CF-COMBO stage1ENG | WT / ALL | `AND(FVG¦45s+FVG¦30s) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100174 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦30s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100250 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+iFVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100252 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+iFVG¦1m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100163 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦30s) ¦ b_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100161 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦30s) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100181 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100169 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100156 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100182 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100251 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+FVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100158 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | CANDIDATE |
| 100280 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100253 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+OB¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100263 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+FVG¦30s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100293 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iFVG¦1m+FVG¦15s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100291 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(FVG¦15s+OB¦1m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100278 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(FVG¦15s+OB¦1m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100102 | CF-COMBO stage1ENG | KB / ALL | `AND(OB¦30s+FVG¦1m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100200 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(iplFVG¦30s+iFVG¦30s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100194 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(iplFVG¦30s+iFVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100301 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+FVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100302 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iFVG¦1m+FVG¦15s) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100300 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iFVG¦1m+FVG¦15s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100286 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+iplFVG¦5m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100294 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+iFVG¦2m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.30 | DEAD |
| 100284 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ b_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100296 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+iFVG¦2m) ¦ b_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100298 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+iFVG¦2m) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100279 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100277 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100289 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ b_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100299 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+iFVG¦2m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100353 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦1m+OB¦30s) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100346 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iFVG¦1m+OB¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100260 | CF-COMBO stage1ENG | WT / ALL | `AND(FVG¦45s+iplFVG¦15s) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100345 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦1m+OB¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100350 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦30s+FVG¦3m) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100357 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦45s+FVG¦3m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100343 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦30s+FVG¦3m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100364 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦45s+FVG¦3m) ¦ b_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100129 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iFVG¦30s+OB¦1m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100155 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(FVG¦15s+iplFVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100132 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(FVG¦15s+OB¦1m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100150 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(FVG¦15s+FVG¦2m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100264 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+OB¦30s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100112 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iplFVG¦45s+iFVG¦15s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100091 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iplFVG¦45s+iFVG¦15s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100352 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦30s+OB¦30s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100349 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦30s+OB¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100358 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦30s+OB¦30s) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | CANDIDATE |
| 100341 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦30s+OB¦1m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100344 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦30s+OB¦1m) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100131 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iplFVG¦30s+OB¦1m) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100247 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+iplFVG¦15s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100285 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | DEAD |
| 100130 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iplFVG¦30s+OB¦1m) ¦ b_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.29 | CANDIDATE |
| 100145 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iplFVG¦30s+FVG¦15s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100147 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iplFVG¦30s+FVG¦2m) ¦ c2_near¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100142 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iplFVG¦30s+FVG¦2m) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.27 | DEAD |
| 100149 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iplFVG¦1m+iplFVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100151 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iFVG¦30s+iplFVG¦30s) ¦ c2_far¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100266 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+iFVG¦15s) ¦ c2_mid¦F0.7` | 0.746 | Y | unevaluated | Y | 0.28 | DEAD |
| 100095 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iplFVG¦1m+iFVG¦15s) ¦ c2_far¦F0.7` | 0.745 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100186 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(iplFVG¦30s+OB¦30s) ¦ c2_far¦F0.7` | 0.736 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100087 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iplFVG¦30s+FVG¦2m) ¦ b_mid¦F0.7` | 0.735 | Y | unevaluated | Y | 0.27 | CANDIDATE |
| 100288 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+iplFVG¦5m) ¦ b_far¦F0.7` | 0.735 | Y | unevaluated | Y | 0.27 | DEAD |
| 100272 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+FVG¦30s) ¦ c2_near¦F0.7` | 0.730 | Y | unevaluated | Y | 0.26 | DEAD |
| 100191 | CF-COMBO stage1ENG | HM / ALL | `THEN60s(BRK¦15s+OB¦30s) ¦ c2_far¦F0.7` | 0.729 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100268 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+iplFVG¦15s) ¦ c2_near¦F0.7` | 0.729 | Y | unevaluated | Y | 0.26 | DEAD |
| 100267 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+BRK¦15s) ¦ c2_near¦F0.7` | 0.729 | Y | unevaluated | Y | 0.26 | DEAD |
| 100274 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+iFVG¦45s) ¦ c2_near¦F0.7` | 0.728 | Y | unevaluated | Y | 0.26 | DEAD |
| 100269 | CF-COMBO stage1ENG | WT / ALL | `AND(OB¦15s+OB¦30s) ¦ c2_near¦F0.7` | 0.728 | Y | unevaluated | Y | 0.26 | DEAD |
| 100172 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ b_mid¦F0.7` | 0.728 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100121 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iplFVG¦30s+FVG¦15s) ¦ c2_mid¦F0.7` | 0.724 | Y | unevaluated | Y | 0.26 | DEAD |
| 100157 | CF-COMBO stage1ENG | ST / ALL | `THEN60s(iplFVG¦15s+OB¦1m) ¦ b_far¦F0.7` | 0.724 | Y | unevaluated | Y | 0.26 | DEAD |
| 100140 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(FVG¦15s+FVG¦2m) ¦ c2_far¦F0.7` | 0.722 | Y | unevaluated | Y | 0.26 | DEAD |
| 100195 | CF-COMBO stage1ENG | HM / ALL | `THEN300s(iFVG¦30s+OB¦30s) ¦ c2_far¦F0.7` | 0.718 | Y | unevaluated | Y | 0.26 | CANDIDATE |
| 100137 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iFVG¦30s+FVG¦2m) ¦ c2_far¦F0.7` | 0.714 | Y | unevaluated | Y | 0.26 | DEAD |
| 100337 | CF-COMBO stage1ENG | MV / ALL | `THEN60s(iplFVG¦1m+OB¦1m) ¦ c2_far¦F0.7` | 0.713 | Y | unevaluated | Y | 0.26 | DEAD |
| 100173 | CF-COMBO stage1ENG | ST / ALL | `THEN300s(iFVG¦1m+OB¦30s) ¦ c2_far¦F0.7` | 0.712 | Y | unevaluated | Y | 0.26 | DEAD |
| 100303 | CF-COMBO stage1ENG | DN / ALL | `THEN60s(iplFVG¦15s+iFVG¦2m) ¦ c2_near¦F0.7` | 0.710 | Y | unevaluated | Y | 0.26 | DEAD |
| 100126 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(FVG¦15s+FVG¦10m) ¦ c2_mid¦F0.7` | 0.707 | Y | unevaluated | Y | 0.26 | DEAD |
| 100143 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iplFVG¦30s+FVG¦2m) ¦ c2_far¦F0.7` | 0.706 | Y | unevaluated | Y | 0.26 | DEAD |
| 100138 | CF-COMBO stage1ENG | PE / ALL | `THEN60s(iFVG¦30s+FVG¦2m) ¦ c2_mid¦F0.7` | 0.706 | Y | unevaluated | Y | 0.26 | DEAD |
| 100117 | CF-COMBO stage1ENG | KB / ALL | `THEN60s(iplFVG¦30s+FVG¦15s) ¦ c2_far¦F0.7` | 0.705 | Y | unevaluated | Y | 0.26 | DEAD |
| 100215 | CF-COMBO stage1ENG | HM / ALL | `AND(OB¦30s+iplFVG¦45s) ¦ c2_far¦F0.7` | 0.703 | Y | unevaluated | Y | 0.26 | DEAD |
| 100203 | CF-COMBO stage1ENG | HM / ALL | `THEN300s(FVG¦15s+OB¦30s) ¦ c2_far¦F0.7` | 0.702 | Y | unevaluated | Y | 0.26 | DEAD |
| 100125 | CF-COMBO stage1ENG | KB / ALL | `AND(FVG¦15s+BRK¦30s) ¦ c2_mid¦F0.7` | 0.702 | Y | unevaluated | Y | 0.26 | DEAD |

## Notes and honest limits
* Hit rates are on the rule-month grain and the same rule appears in many months: clusters (program x month) are the honest unit and are shown; month-block CIs already treat a month as one draw.
* The stream-universe score is the s5_walkforward re-implementation of the RE-1 logistic (features computable at M; fire-rate and correlation neutral), the study table is RE-1's own prediction (no rule ids, so it cannot be joined to the list); the list `persist` for most rows uses a proxy z6 = sqrt(2) x z3 (DS3_SIXTY.md 2d).
* Walk-forward stops at 2025-11 (outcome needs 3 further months inside the 20260206 cap); the list bins are today's scores, so the two are different populations.
* Everything is POST-HOC; no PASS; nothing changes live.