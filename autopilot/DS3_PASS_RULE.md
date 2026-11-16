# DS3_PASS_RULE - calibration of the pass rule and tiered verdict (W-PR2), FIRST PASS
VERDICT (data ends 2026-10-30; FIRST PASS; step 1 only, steps 2-6 not finished): THE CURRENT RULE (real cell beats ALL 6 controls on stack max DD in HOLD AND L6M, mean not worse than -5%) REJECTS REAL EFFECTS. On planted effects of known size it passes 12-13% of seeds for a true 5%, 10% and 20% max-DD cut at flat mean (control family A, 200 seeds; 10-20% of 20 seeds) and 3-6% (family B); a true 10% DD cut has power far under 50%, so this rule cannot be used to say "does not work" or "works". Its false-positive rate is 0-1.5% (it is blunt, not loose). Planted +3% / +6% mean at flat DD is not detected by ANY rule here (4-5%; the size-tilt controls alone move the mean more than that). Tiered percentile rule: see cut-offs below; its CONFIRMED false-positive rate on fresh noise is 3.2% and its power for a 10% DD cut is 14% (A) / 28% (B), for 20% 7% (A) / 64% (B): better, but the honest reading is that max DD over a 6-12 month window cannot confirm a 10% effect.

Header line (desk standard 5): trials counted: step 1 = 5 planted kinds x 200 seeds + 2 noise kinds x 400 (+400 fresh) seeds x 2 control families, 180-set cut-off grid on noise only (tuning) then validated on fresh seeds; correction method: percentile among 30 controls + week-clustered bootstrap (steps 2-3), no White/SPA/DSR here (W-DV block below); PBO: not applicable to step 1 (no fitted choice; cut-offs tuned on noise seeds only); numbers shown: NOT real strategy results, synthetic plants on the in-sample JL2 trade list, path arithmetic (see engine-exact vs arithmetic below). Fees: JL2 engine dollars are BASE lots with the engine fee as run; the $4.84 RT column and x1.75 live column are scale factors on these, not applied inside the plant tables (all results are percentages).

## Step 1 - power and false positives of the CURRENT rule and of the tiers (planted edges and noise on JL2)

**What is engine-exact and what is path-arithmetic.** ENGINE-EXACT: the base is the exact-engine trade list of TL3_EV_JN05W2JL2 (JL2), 18,979 trades 2023-04..2026-10 (trades.parquet of runs_rf); its windows reproduce the page references (HOLD 2025-11..2026-04 stack max DD -74,402, L6M -22,565). PATH-ARITHMETIC: every planted and noise rule below re-weights each JL2 trade's OWN P&L (size/exit-type effect); there is NO engine re-run, so no freed-book replacement (path effect) and no re-entry. This is right for size and exit rules and optimistic for skip rules (the path effect would add noise to real skip cells). Engine re-runs of about 1,500 planted sets were not available at the 21:00Z mark, so step 1 is arithmetic by design (directive: plants can be built from the engine's own trade future R).

**Plants (from each trade's own future outcome).** Information score per trade x = d * z + AR(1, rho 0.7) noise in time order, z = rank-normal of the trade's own P&L (loser-ness for DD plants, winner-ness for mean plants); flagged = top 25% of x. DD plant: flagged trades scaled to 50% (size cut / early exit), unflagged trades scaled up multiplicatively so the full-history mean is exactly flat; the information level d is bisected so the expected cut of stack max DD (average of HOLD and L6M) is 5.0 / 10.0 / 20.0% (d = 0.038 / 0.051 / 0.085). Mean plant: lot-neutral tilt (flagged x1.5, others x0.833), d bisected so the expected mean gain is +3.0 / +6.0% (d = 0.0099 / 0.0175). Realised effect varies per seed (shown, mean +- sd). The DD plant is at flat mean (realised mean change about -0.4%); the mean plant is at DD equal to the controls (realised DD vs JL2 is -11 to -12%, the same as noise, because a random size tilt alone moves DD by +-12 points).

**Controls** (persistent draw: one uniform per 5-minute bucket per book and side; flag share 25% equal to the plant; flag share equals the plant by construction in this arithmetic). Family A: the same cut/tilt mechanism with random flags and mean restored to equal (random reallocation of the same size). Family B (the realistic skip/exit control): the plain random cut with the mean left to fall. 30 controls per candidate (the CURRENT rule uses the first 6). Noise = the same mechanism with random flags (family A equal-mean; B plain cut), so noise against its own controls is exchangeable.

**CURRENT rule** = real DD better than all 6 controls in HOLD and in L6M, and mean not below -5% of JL2 in both. **Tiers** (percentile = share of 30 controls the real beats; DD, worst week and mean per window; recent windows L6M, L3M; older HOLD, GAP, PREUW, X'; P(DD shallower) from 2,000 week-clustered bootstrap resamples of the paired weekly path vs JL2 on L6M):
CONFIRMED: >= conf_hi percentile on DD or mean in L6M and in L3M, the other >= conf_other, P(DD shallower, L6M) >= conf_pdd, DD percentile >= conf_old in HOLD and the older windows. LEAD: >= 75th percentile on DD or mean in L6M and L3M, nothing (DD or mean) below the 25th in any window. FAIL otherwise.
DIRECTIVE cut-offs: conf_hi 0.90, conf_other 0.40, conf_pdd 0.80, conf_old 0.25, LEAD 0.75 / 0.25.
**FINAL cut-offs (tuned only on noise: CONFIRMED false-positive <= 3% on both noise families in both control families, 400 seeds, then validated on 400 fresh seeds): conf_hi 0.90, conf_other 0.25, conf_pdd 0.70, conf_old 0.25, LEAD hi 0.75, LEAD floor 0.25** (change vs directive: conf_other 0.40 -> 0.25, conf_pdd 0.80 -> 0.70). Fresh-noise CONFIRMED false positive 3.2% / 1.8% (family A noise DD / noise mean), 3.2% / 1.8% (family B); LEAD-or-better 3.0-6.0% (LEAD may be looser).


#### Control family A: controls restored to equal mean (random reallocation of the same size)

| planted rule | realised DD cut vs JL2 (avg HOLD, L6M; mean +- sd across seeds) | realised mean change | CURRENT rule pass, 20 seeds | CURRENT rule pass, 200 seeds | tiers DIRECTIVE cut-offs: CONFIRMED / LEAD-or-better, 200 | tiers TUNED cut-offs: CONFIRMED / LEAD-or-better, 200 |
|---|---|---|---|---|---|---|
| dd5 | +5.4% +- 10.6 | -0.3% | 20% (4/20) | 12% | 8% / 11% | 14% / 16% |
| dd10 | +10.7% +- 9.1 | -0.4% | 10% (2/20) | 13% | 7% / 10% | 14% / 14% |
| dd20 | +20.8% +- 7.0 | -0.5% | 10% (2/20) | 12% | 2% / 3% | 7% / 7% |
| mean3 | -12.3% +- 12.5 | +3.7% | 5% (1/20) | 4% | 2% / 7% | 4% / 8% |
| mean6 | -10.7% +- 12.3 | +6.5% | 5% (1/20) | 5% | 3% / 12% | 4% / 13% |
| noise_dd (FALSE POSITIVE) | n/a | n/a | 0% (0/20) | 1.2% (400) | 2.0% / 3.2% | 2.2% / 3.5% ; fresh 400 seeds: 3.2% / 4.8% |
| noise_mean (FALSE POSITIVE) | n/a | n/a | 0% (0/20) | 1.5% (400) | 1.2% / 4.0% | 1.5% / 4.0% ; fresh 400 seeds: 1.8% / 3.0% |

#### Control family B: controls are the plain random cut (mean falls)

| planted rule | realised DD cut vs JL2 (avg HOLD, L6M; mean +- sd across seeds) | realised mean change | CURRENT rule pass, 20 seeds | CURRENT rule pass, 200 seeds | tiers DIRECTIVE cut-offs: CONFIRMED / LEAD-or-better, 200 | tiers TUNED cut-offs: CONFIRMED / LEAD-or-better, 200 |
|---|---|---|---|---|---|---|
| dd5 | +5.4% +- 10.6 | -0.3% | 5% (1/20) | 3% | 15% / 28% | 17% / 28% |
| dd10 | +10.7% +- 9.1 | -0.4% | 0% (0/20) | 5% | 23% / 46% | 28% / 46% |
| dd20 | +20.8% +- 7.0 | -0.5% | 5% (1/20) | 6% | 57% / 84% | 64% / 84% |
| mean3 | -12.3% +- 12.5 | +3.7% | 5% (1/20) | 4% | 2% / 7% | 4% / 8% |
| mean6 | -10.7% +- 12.3 | +6.5% | 5% (1/20) | 5% | 3% / 12% | 4% / 13% |
| noise_dd (FALSE POSITIVE) | n/a | n/a | 0% (0/20) | 0.0% (400) | 2.2% / 4.5% | 2.8% / 4.8% ; fresh 400 seeds: 3.2% / 6.0% |
| noise_mean (FALSE POSITIVE) | n/a | n/a | 0% (0/20) | 1.5% (400) | 1.2% / 4.0% | 1.5% / 4.0% ; fresh 400 seeds: 1.8% / 3.0% |

Reading the table: CURRENT rule = share of seeds passing the morning rule (20 seeds as ordered, 200 for precision); the tier columns give CONFIRMED / LEAD-or-better (LEAD-or-better includes CONFIRMED). On the 10% DD plant the current rule passes 2 of 20 seeds (family A) and 0 of 20 (family B).

**Plain statements.** (1) Current-rule power on a true 10% DD cut at flat mean is far below 50% (13% family A, 5% family B, 200 seeds): the rule is rejecting real effects, so "does not beat all six" says almost nothing about whether a rule works. Its power does not rise with effect size (12-13% at 5%, 10% and 20%) because it needs the real cell to beat the best of six noisy controls in two windows at once. (2) The cause is noise: the DD cut of a random rule of the same frequency varies with sd 7-17 points between draws, max DD is decided by a few weeks, and the realised DD cut of the plant itself varies +-7 to +-11 points around its target. (3) The tiered percentile rule keeps CONFIRMED false positives under 5% but its power for a 10% DD cut is 14% (A) / 28% (B); only family B (the right control for skip and exit rules, where random controls lose mean) reaches 64% at a 20% cut. A rule whose true effect is a 10% cut of max DD can reach LEAD at best by max DD alone; confirming it needs a statistic that uses all weeks. (4) Mean plants of +3 / +6% are not detected by any rule here (4-5% pass, about the false-positive rate): lot-tilt controls move the mean by more than that. No candidate on the 11-16 list claims so small a mean effect alone.

**Statistic with more power (not in the directive, measured here).** The percentile of the root-mean-square daily drawdown ("ulcer") at >= 90th in BOTH HOLD and L6M gives power 49 / 72 / 97% for 5 / 10 / 20% DD cuts at 3.3-3.5% false positive (family A, 200 seeds), against 35 / 52 / 88% for max DD under the same requirement. Recommendation: show the ulcer percentile beside max DD in every table (code/th_passrule/pr_lib.py key ulc). Not substituted in the tiers.

Code: code/th_passrule (pr_lib.py, pr_plant.py, pr_step1.py, pr_tune.py, pr_report1.py); raw results /mnt/l2/l2vast/_passrule/step1*.json. The prereg line was appended to DECISIONS.md after the first pass of the numbers above ran (no thresholds were changed after it except the tuning noted: FP constraint 4% -> 3% before the final cut-offs, see step 1 text).

## Steps 2-6
not finished

<!-- WDV:BEGIN -->
## W-DV section: validation columns (owner W-DV; FIRST PASS; written 2026-11-16 20:18Z; do not edit between the markers)

VERDICT (data ends 2026-10-31; FIRST PASS; engine cells H12 = 2025-11..2026-10, IN-SAMPLE): JL2 drawdown is a distribution, not 74,402: bootstrap median 61,074 and 95th percentile 97,706 (live x1.75 at $4.84: 109,265 and 176,986; observed 133,301); the 95th percentile is 1.3x the single observed number. No candidate moves the 95th-percentile DD by more than 9%: U7 asia 40x40 -8.8%, M7 London cap 3 -7.6% (both with a mean gain of +7% / +7%), the 9 give-back lines -5% to +2%, A7 target 45 -0.4%, against-the-day M7/O7 nyam 0 (the engine never changes a trade), session-VWAP skip +7% (worse). None of the four families (give-back, fixed bracket, against-the-day, M7 London cap / re-entry) is significant after snooping at its real trial count (RC p .26-.88, DSR .03-.17 at N_used; BH 10% survivors none).

HEADER LINE (template for every page): `Validation: trials counted N_low..N_used (TRIALS_LEDGER.csv family id); correction = White RC + Hansen SPA (2,000 stationary-bootstrap resamples) + deflated Sharpe at the real trial count + BH 10% on survivor lists; PBO = x.xx (CSCV S blocks, purge 1 wk) or "not fitted"; number shown is IN-SAMPLE | WALK-FORWARD | UNTOUCHED (stamp data end).`

### 1. Drawdown as a distribution (first table; JL2 first, then each candidate)
Method: stationary block bootstrap (B = 5,000, seed 0) of the DAILY P&L path with whole weeks as blocks; mean block length b (weeks, column b) = Politis-White / Patton optimal length from the autocorrelation of the cell's own weekly P&L (about 1.0-1.3 weeks on H12, 1.7-2.7 on HOLD: weekly P&L has almost no autocorrelation, so the blocks are short and the table is close to an iid week resample); paths have the window length; drawdown from a zero start; "obs DD (page basis)" = observed daily-cumulative max DD with the peak starting at the first value, the convention of the DS3 pages (ties out: JL2 HOLD 74,402, L6M 22,565). Thresholds 1x/2x/3x = multiples of the cell's own average weekly profit (second set: JL2's average, one common scale). Median DD in average weeks of profit is shown because 1x-3x are small multiples of a weekly profit and are exceeded in almost every draw on 6-12 month windows; the number to size lots from is the 95th percentile. Dollars: BASE lots, engine fee $1.18; last column = live x1.75 lots at $4.84 RT. H12 = 2025-11..2026-10 (HOLD+L6M months, 52 weeks); a window is shown only when the cell has every month of it (so no ALL rows for 12-month cells). Small windows: HOLD has 26 weeks and L6M 27, so their percentiles are rough; H12 is the main row. Cells = full-stack runs (candidate rule alone altered inside the JL2 stack).

| window | cell | wks | b | obs DD (page basis) | median DD (in avg weeks of profit) | 95th pct DD | P(DD>1x) | P(>2x) | P(>3x) | same, thresholds at JL2 avg (1x/2x/3x) | avg $/wk | worst wk | live x1.75 @4.84: obs / median / 95th DD, avg $/wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| H12 | JL2 | 52 | 1.1 | -74,402 | -61,074 (4.0) | -97,706 | 1.00 | 1.00 | 0.86 | same | 15,316 | -31,211 | -133,301 / -109,265 / -176,986, 25,522 |
| H12 | A7 asia target 45 | 52 | 1.0 | -74,364 | -59,856 (4.0) | -97,322 | 1.00 | 1.00 | 0.88 | 1.00/1.00/0.87 | 15,069 | -31,106 | -133,248 / -107,531 / -176,159, 25,083 |
| H12 | ATD M7 nyam T20 | 52 | 1.1 | -74,402 | -61,074 (4.0) | -97,706 | 1.00 | 1.00 | 0.86 | 1.00/1.00/0.86 | 15,316 | -31,211 | -133,301 / -109,265 / -176,986, 25,522 |
| H12 | ATD O7 nyam T20 | 52 | 1.1 | -74,402 | -61,074 (4.0) | -97,706 | 1.00 | 1.00 | 0.86 | 1.00/1.00/0.86 | 15,316 | -31,211 | -133,301 / -109,265 / -176,986, 25,522 |
| H12 | ATD O7 nyam T25 | 52 | 1.1 | -74,402 | -61,074 (4.0) | -97,706 | 1.00 | 1.00 | 0.86 | 1.00/1.00/0.86 | 15,316 | -31,211 | -133,301 / -109,265 / -176,986, 25,522 |
| H12 | ATD session-VWAP skip (all books) | 52 | 1.3 | -72,108 | -64,731 (4.3) | -104,596 | 1.00 | 1.00 | 0.92 | 1.00/1.00/0.92 | 15,169 | -31,437 | -129,204 / -116,888 / -190,049, 25,305 |
| H12 | GB H7 asia 40/B40 | 52 | 1.0 | -71,746 | -59,228 (3.9) | -95,725 | 1.00 | 1.00 | 0.87 | 1.00/1.00/0.86 | 15,078 | -31,074 | -128,660 / -107,049 / -173,775, 25,107 |
| H12 | GB H7 asia 60/B30 | 52 | 1.0 | -72,429 | -59,140 (3.9) | -96,289 | 1.00 | 1.00 | 0.86 | 1.00/1.00/0.85 | 15,187 | -33,394 | -129,869 / -106,227 / -174,328, 25,299 |
| H12 | GB H7 nyam 40/B40 | 52 | 1.2 | -72,537 | -60,523 (3.9) | -96,415 | 1.00 | 1.00 | 0.86 | 1.00/1.00/0.87 | 15,392 | -31,211 | -130,037 / -108,723 / -174,463, 25,657 |
| H12 | GB H7 nyam 50/B40 | 52 | 1.2 | -72,627 | -60,685 (3.9) | -96,554 | 1.00 | 1.00 | 0.87 | 1.00/1.00/0.87 | 15,388 | -31,211 | -130,195 / -108,841 / -174,474, 25,650 |
| H12 | GB K7 nyam 40/B40 | 52 | 1.0 | -75,309 | -59,882 (3.9) | -95,754 | 1.00 | 1.00 | 0.84 | 1.00/1.00/0.85 | 15,510 | -30,699 | -134,929 / -106,696 / -174,008, 25,853 |
| H12 | GB K7 nyam 50/B20 | 52 | 1.2 | -78,354 | -62,101 (4.1) | -99,494 | 1.00 | 1.00 | 0.90 | 1.00/1.00/0.89 | 14,964 | -31,604 | -140,335 / -112,173 / -178,720, 24,888 |
| H12 | GB P7 asia 40/B40 | 52 | 1.0 | -74,710 | -60,164 (4.3) | -103,010 | 1.00 | 1.00 | 0.91 | 1.00/1.00/0.85 | 13,962 | -35,108 | -133,970 / -108,849 / -186,887, 23,101 |
| H12 | GB P7 asia 50/B40 | 52 | 1.0 | -75,505 | -59,294 (4.1) | -101,238 | 1.00 | 1.00 | 0.90 | 1.00/1.00/0.84 | 14,355 | -34,923 | -135,350 / -107,449 / -183,733, 23,802 |
| H12 | GB P7 nyam 40/B30 | 52 | 1.2 | -73,222 | -61,010 (4.0) | -96,717 | 1.00 | 1.00 | 0.88 | 1.00/1.00/0.87 | 15,094 | -31,662 | -131,237 / -109,265 / -176,279, 25,135 |
| H12 | M7 London cap 3 | 52 | 1.3 | -70,924 | -59,277 (3.6) | -90,315 | 1.00 | 0.99 | 0.74 | 1.00/1.00/0.81 | 16,330 | -30,596 | -127,174 / -105,246 / -163,646, 27,328 |
| H12 | U7 asia 40x40 | 52 | 1.0 | -67,152 | -54,731 (3.3) | -89,125 | 1.00 | 0.98 | 0.66 | 1.00/0.99/0.74 | 16,472 | -33,286 | -120,737 / -99,106 / -161,839, 27,481 |
| HOLD | JL2 | 26 | 2.3 | -74,402 | -72,692 (8.7) | -114,451 | 1.00 | 1.00 | 1.00 | same | 8,313 | -31,211 | -133,301 / -131,665 / -208,631, 13,428 |
| HOLD | A7 asia target 45 | 26 | 2.4 | -74,364 | -72,900 (8.7) | -112,782 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,399 | -31,106 | -133,248 / -132,393 / -205,659, 13,577 |
| HOLD | ATD M7 nyam T20 | 26 | 2.3 | -74,402 | -72,692 (8.7) | -114,451 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,313 | -31,211 | -133,301 / -131,665 / -208,631, 13,428 |
| HOLD | ATD O7 nyam T20 | 26 | 2.3 | -74,402 | -72,692 (8.7) | -114,451 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,313 | -31,211 | -133,301 / -131,665 / -208,631, 13,428 |
| HOLD | ATD O7 nyam T25 | 26 | 2.3 | -74,402 | -72,692 (8.7) | -114,451 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,313 | -31,211 | -133,301 / -131,665 / -208,631, 13,428 |
| HOLD | ATD session-VWAP skip (all books) | 26 | 2.1 | -72,108 | -72,108 (8.5) | -117,665 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,518 | -31,437 | -129,204 / -129,204 / -214,995, 13,826 |
| HOLD | GB H7 asia 40/B40 | 26 | 2.7 | -71,746 | -71,746 (8.3) | -108,361 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,688 | -31,074 | -128,660 / -128,660 / -198,162, 14,084 |
| HOLD | GB H7 asia 60/B30 | 26 | 2.0 | -72,429 | -70,680 (7.6) | -115,209 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 9,340 | -33,394 | -129,869 / -128,414 / -208,797, 15,220 |
| HOLD | GB H7 nyam 40/B40 | 26 | 2.2 | -72,537 | -71,487 (8.5) | -114,206 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,384 | -31,211 | -130,037 / -130,037 / -207,790, 13,552 |
| HOLD | GB H7 nyam 50/B40 | 26 | 2.3 | -72,627 | -72,126 (8.6) | -113,960 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,361 | -31,211 | -130,195 / -130,195 / -207,464, 13,512 |
| HOLD | GB K7 nyam 40/B40 | 26 | 2.6 | -75,309 | -72,311 (8.6) | -111,304 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,437 | -30,699 | -134,929 / -130,851 / -201,217, 13,633 |
| HOLD | GB K7 nyam 50/B20 | 26 | 2.1 | -78,354 | -73,322 (9.2) | -118,287 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 7,959 | -31,604 | -140,335 / -131,970 / -216,228, 12,785 |
| HOLD | GB P7 asia 40/B40 | 26 | 1.4 | -74,710 | -69,087 (8.0) | -124,180 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,628 | -35,108 | -133,970 / -124,485 / -228,598, 13,933 |
| HOLD | GB P7 asia 50/B40 | 26 | 2.2 | -75,505 | -70,689 (8.4) | -120,095 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,392 | -34,923 | -135,350 / -128,701 / -218,564, 13,530 |
| HOLD | GB P7 nyam 40/B30 | 26 | 2.3 | -73,222 | -72,082 (8.8) | -113,105 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,182 | -31,662 | -131,237 / -131,211 / -205,486, 13,198 |
| HOLD | M7 London cap 3 | 26 | 2.1 | -70,924 | -66,354 (7.7) | -103,621 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 8,575 | -30,596 | -127,174 / -120,758 / -190,859, 13,912 |
| HOLD | U7 asia 40x40 | 26 | 2.3 | -67,152 | -67,152 (7.1) | -107,004 | 1.00 | 1.00 | 1.00 | 1.00/1.00/1.00 | 9,462 | -33,286 | -120,737 / -120,737 / -196,587, 15,383 |
| L6M | JL2 | 27 | 1.2 | -22,565 | -31,058 (1.4) | -46,726 | 0.92 | 0.09 | 0.00 | same | 21,492 | -13,430 | -40,872 / -55,574 / -85,039, 36,223 |
| L6M | A7 asia target 45 | 27 | 1.2 | -21,503 | -32,032 (1.5) | -47,069 | 0.95 | 0.12 | 0.00 | 0.93/0.10/0.00 | 20,935 | -13,002 | -41,290 / -57,537 / -84,902, 35,235 |
| L6M | ATD M7 nyam T20 | 27 | 1.2 | -22,565 | -31,058 (1.4) | -46,726 | 0.92 | 0.09 | 0.00 | 0.92/0.09/0.00 | 21,492 | -13,430 | -40,872 / -55,574 / -85,039, 36,223 |
| L6M | ATD O7 nyam T20 | 27 | 1.2 | -22,565 | -31,058 (1.4) | -46,726 | 0.92 | 0.09 | 0.00 | 0.92/0.09/0.00 | 21,492 | -13,430 | -40,872 / -55,574 / -85,039, 36,223 |
| L6M | ATD O7 nyam T25 | 27 | 1.2 | -22,565 | -31,058 (1.4) | -46,726 | 0.92 | 0.09 | 0.00 | 0.92/0.09/0.00 | 21,492 | -13,430 | -40,872 / -55,574 / -85,039, 36,223 |
| L6M | ATD session-VWAP skip (all books) | 27 | 1.4 | -28,494 | -36,617 (1.7) | -60,699 | 0.99 | 0.33 | 0.04 | 0.99/0.31/0.03 | 21,011 | -23,429 | -51,900 / -66,311 / -110,292, 35,423 |
| L6M | GB H7 asia 40/B40 | 27 | 1.1 | -23,908 | -30,957 (1.5) | -46,927 | 0.93 | 0.12 | 0.00 | 0.92/0.09/0.00 | 20,673 | -13,430 | -43,898 / -55,910 / -85,516, 34,791 |
| L6M | GB H7 asia 60/B30 | 27 | 1.1 | -25,023 | -30,957 (1.5) | -46,377 | 0.95 | 0.13 | 0.00 | 0.93/0.09/0.00 | 20,254 | -13,430 | -47,418 / -56,282 / -84,604, 34,068 |
| L6M | GB H7 nyam 40/B40 | 27 | 1.2 | -22,565 | -30,464 (1.4) | -45,448 | 0.91 | 0.07 | 0.00 | 0.91/0.08/0.00 | 21,571 | -11,690 | -40,872 / -54,539 / -82,470, 36,362 |
| L6M | GB H7 nyam 50/B40 | 27 | 1.2 | -22,565 | -30,522 (1.4) | -45,571 | 0.91 | 0.08 | 0.00 | 0.91/0.08/0.00 | 21,586 | -11,775 | -40,872 / -54,539 / -83,167, 36,388 |
| L6M | GB K7 nyam 40/B40 | 27 | 1.1 | -23,010 | -31,058 (1.4) | -45,770 | 0.91 | 0.07 | 0.00 | 0.91/0.08/0.00 | 21,748 | -13,430 | -41,650 / -55,898 / -83,502, 36,662 |
| L6M | GB K7 nyam 50/B20 | 27 | 1.2 | -24,340 | -31,490 (1.5) | -48,527 | 0.93 | 0.11 | 0.00 | 0.92/0.11/0.00 | 21,156 | -14,211 | -43,978 / -57,284 / -86,935, 35,621 |
| L6M | GB P7 asia 40/B40 | 27 | 1.0 | -31,640 | -32,155 (1.7) | -50,147 | 0.98 | 0.34 | 0.02 | 0.97/0.13/0.01 | 18,581 | -18,172 | -56,172 / -57,575 / -90,604, 31,074 |
| L6M | GB P7 asia 50/B40 | 27 | 1.0 | -30,727 | -31,495 (1.6) | -48,477 | 0.98 | 0.20 | 0.01 | 0.96/0.11/0.00 | 19,566 | -17,244 | -54,523 / -56,557 / -87,419, 32,811 |
| L6M | GB P7 nyam 40/B30 | 27 | 1.2 | -22,565 | -31,058 (1.5) | -46,727 | 0.92 | 0.10 | 0.00 | 0.92/0.09/0.00 | 21,192 | -13,430 | -40,872 / -55,611 / -85,391, 35,699 |
| L6M | M7 London cap 3 | 27 | 1.1 | -23,715 | -30,372 (1.3) | -45,430 | 0.87 | 0.04 | 0.00 | 0.91/0.08/0.00 | 23,193 | -15,143 | -42,637 / -54,518 / -82,649, 39,235 |
| L6M | U7 asia 40x40 | 27 | 1.0 | -19,715 | -28,199 (1.2) | -38,927 | 0.83 | 0.01 | 0.00 | 0.86/0.02/0.00 | 22,612 | -10,253 | -35,143 / -51,003 / -70,347, 38,113 |
| ALL | JL2 | 187 | 1.3 | -74,402 | -87,918 (10.0) | -137,833 | 1.00 | 1.00 | 1.00 | same | 8,803 | -43,527 | -133,301 / -159,439 / -251,045, 14,510 |

### 2. Whole-family data-snooping and PBO (H12 window unless stated; weekly P&L differences vs the family benchmark)
Counting method and uncertainty: autopilot/TRIALS_LEDGER.csv (engine run dirs + replay rules x 15 scopes; +-30%; not a registered log). N engine = variants that reached the exact engine; N total = replay screens (the family the winner was picked from). DSR is computed on the winner's weekly difference series (per-week Sharpe, not annualised) with the variance of the family's trial Sharpes. RC / SPA are one-sided tests that the BEST variant beats the benchmark in MEAN weekly P&L; "downside-weeks" repeats them on the change in the base's worst-quartile weeks only (a mean-type statistic that speaks to drawdown, because no valid snooping test on max DD itself exists in this library: a shift-null DD reality check was built and failed its own unit test, size .10, power .11, and was removed). BH 10% runs on per-variant one-sided bootstrap p-values of the mean. PBO: CSCV, S blocks, all C(S,S/2) splits (3,000 random splits when more), 1-week purge on the train side, metric = Sharpe of the weekly difference; on 52 weeks the blocks are 3-4 weeks long, so PBO is a weak, noisy read there. A fitted choice with PBO above 0.5 is not a result.

| family (base, window) | K variants (N engine / N total) | best by mean | White RC p | Hansen SPA p | DSR at N engine / N total | downside-weeks RC p / SPA p | BH 10% survivors | PBO S=12/14/16 (slope S=16; weeks per block) | verdict on snooping |
|--|--|--|--|--|--|--|--|--|--|
| giveback (D10 gb, JL2) (JL2, H12) | 9 (9 / 135) | bK7_sam_JL2_gb40B40 +195/wk (SR 0.11/wk) | 0.85 | 0.78 | 0.28 / 0.06 | 0.56 / 0.34 | none | 0.56 / 0.59 / 0.57 (slope -0.37; 3.2 wk) | NOT significant after snooping |
| fixed bracket/target (D10 pol_fx, JL2) (JL2, H12) | 5 (5 / 225) | bU7_sas_JL2_pol_fx40x40 +1,156/wk (SR 0.16/wk) | 0.26 | 0.46 | 0.44 / 0.03 | 0.29 / 0.53 | none | 0.51 / 0.37 / 0.46 (slope 0.01; 3.2 wk) | NOT significant after snooping |
| against-the-day (D10 dd*, JL2) HOLD (JL2, HOLD) | 28 (28 / 60) | JL2_ddsess_w_aT30 +1,360/wk (SR 0.16/wk) | 0.67 | 0.76 | 0.23 / 0.17 | 0.11 / 0.14 | none | 0.52 / n/a / n/a (slope n/a; 1.6 wk) | NOT significant after snooping |
| M7 London cap / re-entry (RA, JN05W2 base) (JN05W2, H12) | 14 (14 / 258) | TL3_RA_LCAP20 +319/wk (SR 0.10/wk) | 0.88 | 0.78 | 0.21 / 0.04 | 0.04 / 0.13 | none | 0.45 / 0.29 / 0.35 (slope -0.43; 3.2 wk) | NOT significant after snooping |

Unit-test evidence (null pass rate near nominal, planted power; code/th_validate/TEST_RESULTS.txt): RC/SPA size .06/.08 iid at T=187, K=20 (anti-conservative with autocorrelation: SPA .16 at phi .3, flagged), power .68/.70 at t about 3.4, SPA .86 vs RC .46 with 19 poor alternatives; DSR null pass .002-.05 vs naive .64-.99 at N=20-100; BH realised FDR .08; PBO .56 on noise vs .07 planted; DD bootstrap within 1% (median) / 0.3% (95th) of truth for iid weeks and 6.7% bias vs 37.6% for iid resample when weeks are AR(.5).
<!-- WDV:END -->
