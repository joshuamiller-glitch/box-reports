# DS3_CONFLUENCE - combinations, controls, frontier (W-CF3) - FIRST PAGE, PARTIAL

VERDICT (as of the v1 entry table, 19,798 taken JN05W2 signals, categories A B C D E K L + U only): the user's pre-registered USER_SET_V0 is better than the average entry but is not a drawdown fix stack-wide; no searched checklist has passed step 5 yet (search run on the partial table in progress). Strength: weak to moderate for USER_SET_V0 in two cells, nothing else established. No PASS claim.

Basis: exact-engine taken trades JN05W2, base lots, engine fee $1.18/contract (pnl) - the $4.84 column pnl484 is carried in the table; skipped signals are not in the table yet (taken only); all numbers are in-sample FULL HISTORY for the pre-registered list (nothing tuned, so no search bias; 45 book-session x rule cells were looked at, so about 0.1 passes by chance are expected at the 5 % level on both tests). Code code/th_confl_cf3; data /mnt/l2/l2vast/_confl/cf3/.

## 1. USER_SET_V0 (step 4d, untuned, registered DECISIONS.md sha 13e2d06bd31c20a1; columns c_U_1..c_U_5 by W-CF1, unknown = 0)
Stack-wide, full history (matched-count control: 500 random subsets of the same size within book/session/month; percentile = share of random subsets the checklist beats; DD percentile = share with a WORSE max drawdown):

| rule | trades kept | per day | $/trade | all trades $/trade | max DD | all-trades DD | expectancy pctl | DD pctl | bootstrap 95 % interval of $/trade |
|--|--|--|--|--|--|--|--|--|--|
| all 5 | 4,457 | 4.8 | 152 | 106 | 58,726 | 92,243 | 0.99 | 0.68 | 72 .. 232 |
| at least 4 | 11,206 | 12.1 | 141 | 106 | 112,370 | 92,243 | 1.00 | 0.13 | 86 .. 192 |
| at least 3 | 15,321 | 16.5 | 125 | 106 | 98,040 | 92,243 | 0.99 | 0.37 | 80 .. 169 |

Reading: the list picks better-than-average entries (expectancy percentile 0.99-1.00 against equal-count random subsets), but the drawdown is NOT better than random subsets of the same size (DD percentile 0.68 / 0.13 / 0.37 versus the 0.95 required), so by the step 5 rule it is "fewer trades, a better average, no drawdown protection" stack-wide. It stays above the 3 trades/day floor at every k. Recent windows: all-5 at L3M/L6M has 233/234 $/trade versus 134/159 for all entries but max DD equal to the all-trades DD (52,670 vs 52,233, the 2026-W44 week); older windows X' (2023-04..2024-01) is the exception: 19 vs 50 $/trade.

Cells where a rule beats both 95th-percentile tests (n >= 150 full history), of 45 cell-rule combinations:
- K7 Asia (K7|0), at least 4: 1,116 of 2,596 trades, $174 vs $89 per trade, max DD 16,126 vs 26,763 (-40 %); expectancy pctl 1.00, DD pctl 0.95. Windows: L3M 221 vs 86 (DD 6,891 vs 9,732), L6M 188 vs 88, HOLD 213 vs 111, PRE 174 vs 78, GAP 112 vs 83; X' 11 vs 24 (fails). 
- K7 Asia, at least 3: 1,590 trades, $131 vs $89, DD 18,458 vs 26,763 (-31 %); pctl 0.98 / 0.96; positive in all six windows including X' (81 vs 24).
- P7 Asia (P7|0), all 5: 352 of 2,161 trades, $1,032 vs $424 per trade, DD 29,674 vs 75,069 (-60 %), pctl 1.00 / 0.97; but only 96 trades in L6M and 45 in L3M (floor 40 met in L6M), X' fails (-44 vs 122), GAP weak (111 vs 494). P7 has the heavy tail (7-lot stops): the R-based rerun is queued.
- Not yet done for these: walk-forward consistency is trivial for a fixed list (nothing is refit) so the evidence is the window table above; W44-removed and the $4.84 column are in user_set_v0.csv (K7 Asia at least 4 with W44 removed: $180 per trade, DD unchanged because the W44 week is outside this cell's drawdown); the exact-engine verdict (take/skip gate on top of the live stack, all layers ON) is pending the hook identity run (TL3_CF_ID).
- Tolerant programme gate (DD cut > -2 %, mean $/wk not lower than -3 %) mostly FAILS for a skip rule because $/wk falls when trades are skipped; it passes for K7 Asia at least 4 only in L3M. The gate was written for sizing dials; for a gate on entries the relevant tests are expectancy and DD per the order.

Full table: /mnt/l2/l2vast/_confl/cf3/user_set_v0.csv (every book-session cell, three rules, seven windows).


## 1b. The three USER_SET_V0 leads re-checked (R units, fixed list in 2-week blocks, heavy tail, leave-one-month-out; output /mnt/l2/l2vast/_confl/cf3/userset_leads.txt)
The list is fixed, so nothing is chosen on a trailing window; "walk-forward" here is the out-of-sample behaviour by time slice.

| lead | R per trade kept vs all | max DD in R kept vs all | matched-count pctl in R: expectancy / drawdown | 2-week blocks kept beats all | by year kept vs all $/trade (n kept) | mean without the top 10 wins | leave-one-month-out $/trade |
|--|--|--|--|--|--|--|--|
| K7 Asia, at least 4 | 0.106 vs 0.053 | 12.3 vs 16.7 | 0.997 / 0.85 | 51 of 92 (55 %) | 2023 -79 vs 5 (90); 2024 159 vs 72 (208); 2025 215 vs 71 (333); 2026 200 vs 126 (485) | 154 | 157 .. 185 |
| K7 Asia, at least 3 | 0.073 vs 0.053 | 13.9 vs 16.7 | 0.93 / 0.82 | 59 of 93 (63 %) | 2023 47 vs 5; 2024 106 vs 72; 2025 117 vs 71; 2026 168 vs 126 | 117 | 117 .. 142 |
| P7 Asia, all 5 | 0.200 vs 0.077 | 4.0 vs 12.3 | 0.998 / 0.997 | 32 of 55 (58 %) | 2023 -100 vs 94 (22); 2024 1,112 vs 452 (69); 2025 1,243 vs 504 (113); 2026 1,002 vs 436 (148) | 816 | 907 .. 1,083 |

Reading. In $ the K7 Asia at least 4 pass both 95th-percentile tests (drawdown pctl 0.951); in R the drawdown percentile falls to 0.85, so K7 Asia is a better-expectancy filter with a drawdown benefit that is only borderline: lead, not confirmed. P7 Asia all-5 passes in both units (R drawdown 4.0 vs 12.3 R, pctl 0.997), is not a tail artefact (mean 816 without its top 10 wins, 907-1,083 leaving any one month out, top 5 wins are 12 % of its total), the exit mix is not different (Target 49 % vs 44 %), and it is positive in 2024, 2025, 2026 but NEGATIVE in 2023 (X', 22 trades, -$100 vs +$94): the older window does not hold, so under the rule "must hold in recent AND older windows" it is a RECENT-ONLY lead (2.5 years, 330 trades). The per-block hit rate (55-63 %) says the gain arrives as many modest edges rather than a few blocks. Floors: K7 Asia L6M 340 / 467 trades, P7 L6M 96, full history 1,116 / 1,590 / 352 (all above 40 and 150). Next: exact-engine take/skip gate on the live stack (needs TL3_CF_ID identity first).

## 1c. Search-level control bar versus library size (bit-light search, code cf3_big.py; in-sample best lift-t, greedy must-have list or best-k score; shuffled = outcomes permuted within book/session/month)
K7 Asia, 10 shuffles (the 50-shuffle run and STACK run are in progress): library 50 conditions: real 4.8, shuffled median 5.1, 95th pctl 5.7; 150 conditions: real 8.7, shuffled 6.9 / 7.3; 330 conditions: real 9.4, shuffled 8.0 / 9.0 (max 9.0). The bar rises with the library as the order expects, and the real best only clears it at 150 and 330 columns. Files bar_*.csv.

## 4. The joined library (all column sets) - stack-wide search, shuffled-outcome bar by library size, walk-forward (W-CF3, 2026-11-15)
Library: 21,094 yes/no conditions on the 19,798 TAKEN signals (engine $ outcomes), from W-CF1 (A B C D E K L S T U and M 5,537), W-CF4 (osc 3,047, trend 3,221, smc 1,858, irl 273, ml 216, vol 441), W-CF5 (named systems 4,200), W-CF6 (1,314), W-CF2 (F-J and other-market states 626); columns with fewer than 50 yes or 50 no dropped. Raw v_* values are not conditions. Skipped-signal rows are NOT used in any result (hypothetical points only as a screen, none run yet). Redundancy clusters (outcome-free, random-projection correlation, |phi| >= 0.85): 16,330 clusters (13,204 singletons, largest 28; 1,323 clusters span more than one block), so most columns are NOT near-duplicates at this threshold. The search runs on one leader per cluster (16,330) chosen without looking at outcomes.

**Search-level control bar by library size** (in-sample best lift-t of greedy must-have list or best-k score, STACK, 50 shuffles of outcomes within book/session/month; file bigbar_STACK_0.85_pnl.csv):

| library (random leaders) | real best | shuffled median | shuffled 95th | shuffled max | share of shuffles >= real |
|--|--|--|--|--|--|
| 50 | 10.9 | 7.7 | 8.5 | 8.6 | 0.00 |
| 150 | 12.3 | 9.5 | 11.5 | 12.7 | 0.02 |
| 330 | 13.6 | 12.6 | 14.8 | 16.0 | 0.26 |
| 1,000 | 21.5 | 19.2 | 22.8 | 23.1 | 0.14 |
| 3,000 | 25.0 | 23.8 | 26.8 | 29.3 | 0.32 |
| 16,330 (all) | 28.5 | 29.2 | 32.8 | 34.3 | 0.62 |

Reading: the bar rises steeply with the library, and from 330 conditions up the best checklist found on real outcomes is no better than what the same search finds on shuffled outcomes. The small-library rows pass only because a few columns (book / session / state conditions) carry a real but small effect; adding the other 20,000 conditions adds search power for noise, not signal. Nothing found by search on the full library beats its own shuffled bar.

**Walk-forward of the whole library, stack-wide** (trailing 52 weeks, 2-week refits, first test 2023-10-16, greedy over leaders, minimum kept share of the training window = strictness; matched-count control 1,000 subsets; files wfbig_*.json):

| strictness (min kept share) | OOS trades kept (per day) | $/trade kept vs all | max DD kept vs all | expectancy / DD percentile | item stability across refits | 95 % bootstrap of $/trade |
|--|--|--|--|--|--|--|
| minimum 60 trades | 240 (0.3) | 334 vs 117 | 30,589 vs 92,243 | 0.83 / 0.59 | 0.15 | -113 .. 800 |
| 10 % | 1,691 (2.2) | 152 vs 117 | 72,020 vs 92,243 | 0.31 / 0.15 | 0.13 | -3 .. 302 |
| 20 % | 3,329 (4.2) | 235 vs 117 | 122,156 vs 92,243 | 0.99 / 0.01 | 0.17 | 122 .. 345 |
| 40 % | 6,823 (8.7) | 152 vs 117 | 137,032 vs 92,243 | 0.90 / 0.01 | 0.18 | 71 .. 228 |

Reading: no strictness passes. The loosest versions raise expectancy but make the drawdown WORSE than random subsets of the same size (DD percentile 0.01); the tightest has too few trades (0.3 per day, below the 3 per day floor) and a bootstrap interval spanning zero; the chosen items change at almost every refit (Jaccard 0.13-0.18, i.e. noise). Verdict for the stack-wide search on the full library: fewer trades, no drawdown protection, unstable items. No exact-engine run is justified for it. Next: the same by book and session (cells), the per-block importance table (running: blocks_STACK.csv, real minus shuffled 95th percentile for each block alone and added to the base blocks), and 50 shuffled walk-forward reruns for any cell with a lead. Reminder: universe-wide significance counts are not findings.

## 5. Pre-specified small lists (registered before scoring: autopilot/CONFLUENCE_SMALL_LISTS_PREREG.md, sha256[:16] 1c1580364fd5b5f4, DECISIONS.md)
One item per family (trend, level, VWAP, volume/tape, momentum), plain standard item, chosen by definition not by outcomes. Same controls as USER_SET_V0 (matched-count 500 draws; full-history in-sample; results /mnt/l2/l2vast/_confl/cf3/lists_SL*.csv). Stack-wide none passes (drawdown percentiles 0.03-0.74). Cells passing both 95th tests, of 48 cell-rule combinations per list: SL1 0; SL3 0; SL2 (slower: 60-min trend, monthly open, weekly VWAP, 15-min relative volume >= 1, 60-min efficiency ratio >= 0.3 with the trade) 2: P7 Asia at least 4 (707 of 2,161 trades, $839 vs $424 per trade, max DD 36,080 vs 75,069, pctl 1.00 / 0.99) and K7 NY AM all 5 (119 trades, below the 150 floor, ignored). SL3 has 70 % unknown items in the overnight sessions (opening-range and RTH VWAP exist only in RTH), so it is not a fair test outside RTH.
Reading: P7 Asia improves under two independent pre-specified lists (USER_SET_V0 all-5, SL2 at least 4), which is a better sign than either alone, but the lists overlap in what they say (trend / VWAP side), the cell is the one with the 7-lot heavy tail, and the older window of USER_SET_V0 (2023) was negative; both are in-sample on full history. Exact-engine sets TL3_CF_U3 (V0 all-5) and TL3_CF_U6 (SL2 at least 4) with 3 random-skip placebos each are running; the engine, not the table, decides.

## 2. Machinery and its validation (steps 4-5)
Built and tested on a stand-in table: planted +$800/+$1,500 edge recovered by greedy and by the 2-week walk-forward (905 vs 219 $/trade OOS, DD cut 6x, matched-count controls pass); shuffled outcomes rejected; a leak (open-trade results in 'previous trade' columns) produced a fake 3x OOS edge and was removed (W-CF1 informed; v1 table defines L columns over closed trades only).
First run of the searched families on the PARTIAL table (A, E, L categories only, 271 conditions), stack-wide walk-forward (trailing 52 weeks, 2-week refits, first test 2023-10-16): score on positive-alone items 7.3 trades/day $184 vs $117 per trade but max DD 75k vs 92k and DD percentile 0.33; one-per-category 0.70; cluster score 0.09; greedy must-have list 0.57 trades/day $527 vs $117, DD percentile 0.87, items change on most refits (stability 0.34); gradient boosting (upper bound) 9 trades/day $175, DD worse than all trades. None passes the matched-count test on drawdown. The full run on the v1 table (with U) is in progress; the 50 shuffled-outcome search reruns and the per-block importance table follow once the M, F-J and Block 2-5 columns are in.

<!--ENG-->
## 3b. Engine numbers for the USER_SET_V0 leads (exact engine, JN05W2 base, all layers ON, hook cf_hooks as a skip gate on top; engine fee $1.18; base lots; official weekly basis of jv_score; reference JN05W2)

Skip rule applies to the signals in the entry table (taken JN05W2 signals); signals that appear only because a skipped one freed the book pass through UNGATED, so the engine result is the honest effect of "skip these", not of "run the checklist on every signal". Placebos = same number of skips drawn at random within book/session/month (PB1-3).

### L1M

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 4 | 25918 | 36371 | 28.7 | - | yes | -25918 | 10453 | 578 | 95.3 | 566 | 16.7, 27.4, 22.8 | -3301, -2001, -2959 | - |
| K7 Asia >=3 | 4 | 26182 | 36371 | 28.0 | - | yes | -26182 | 10188 | 583 | 96.1 | 569 | 19.3, 31.5, 20.3 | -1258, -1064, -1069 | - |
| P7 Asia all5 | 4 | 34516 | 36371 | 5.1 | - | no | -34516 | 1855 | -4152 | -684.8 | -4159 | -6.2, -9.2, 22.3 | -2499, -4251, -553 | - |
| stack >=4 gate | 4 | 35584 | 36371 | 2.2 | - | no | -35584 | 787 | -2044 | -337.2 | -2045 | -7.6, -7.9, 57.8 | -471, -7133, 176 | - |
| K7 Asia >=4 + P7 Asia all5 | 4 | 22160 | 36371 | 39.1 | - | no | -22160 | 14211 | -1768 | -291.7 | -1780 | 50.3, 56.3, 16.6 | -2101, -2676, -5953 | - |
| P7 Asia SL2 >=4 | 4 | 32520 | 36371 | 10.6 | - | no | -32520 | 3851 | -1824 | -300.9 | -1831 | 66.5, 34.8, 21.0 | 4565, -1818, -2455 | - |

### L3M

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 13 | 29877 | 36371 | 17.9 | 2.1 | yes | -25918 | 10453 | -279 | -1.7 | -273 | 11.5, 27.4, 22.8 | -1955, -667, -986 | 29.2 / 16 |
| K7 Asia >=3 | 13 | 26962 | 36371 | 25.9 | 11.7 | yes | -26182 | 10188 | 426 | 2.7 | 426 | 19.3, 14.5, 20.3 | -17, -1093, -374 | 21.2 / 17 |
| P7 Asia all5 | 13 | 64194 | 36371 | -76.5 | -110.2 | no | -42821 | -6450 | -7040 | -44.0 | -6998 | -62.1, -61.7, -63.0 | -6953, -7816, -5642 | 67.8 / -63 |
| stack >=4 gate | 13 | 88768 | 36371 | -144.1 | -190.7 | no | -55749 | -19379 | -6508 | -40.6 | -6437 | -53.9, -106.8, -2.8 | -10024, -13344, -1780 | -32.4 / -10 |
| K7 Asia >=4 + P7 Asia all5 | 13 | 63479 | 36371 | -74.5 | -107.9 | no | -40963 | -4593 | -6701 | -41.8 | -6652 | -57.3, -12.6, -71.9 | -6851, -6381, -9972 | - |
| P7 Asia SL2 >=4 | 13 | 68124 | 36371 | -87.3 | -123.1 | no | -44624 | -8254 | -6273 | -39.2 | -6240 | -60.5, -38.7, -77.1 | -2239, -3387, -9401 | - |

### L6M

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 26 | 29877 | 36371 | 17.9 | 2.1 | yes | -25918 | 10453 | 774 | 3.1 | 783 | 11.5, 27.4, 22.8 | -3349, 349, -2084 | 53.7 / -8 |
| K7 Asia >=3 | 26 | 26962 | 36371 | 25.9 | 11.7 | yes | -26640 | 9731 | -285 | -1.1 | -272 | 19.3, 14.5, 20.3 | -890, 36, 378 | 39.3 / -4 |
| P7 Asia all5 | 26 | 64194 | 36371 | -76.5 | -110.2 | no | -42821 | -6450 | -6154 | -24.5 | -6095 | -62.1, -61.7, -63.0 | -7209, -8162, -6821 | 67.8 / -64 |
| stack >=4 gate | 26 | 88768 | 36371 | -144.1 | -190.7 | no | -55749 | -19379 | -7006 | -27.9 | -6895 | -53.9, -106.8, -13.4 | -6373, -11562, -8601 | -32.4 / -18 |
| K7 Asia >=4 + P7 Asia all5 | 26 | 63479 | 36371 | -74.5 | -107.9 | no | -40963 | -4593 | -5601 | -22.3 | -5528 | -57.3, -17.5, -71.9 | -9020, -6166, -9638 | - |
| P7 Asia SL2 >=4 | 26 | 68124 | 36371 | -87.3 | -123.1 | no | -44624 | -8254 | -5806 | -23.1 | -5764 | - | - | - |

### HOLD

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 52 | 59657 | 63185 | 5.6 | 5.6 | yes | -52768 | 2378 | 208 | 1.2 | 209 | 7.1, 9.8, -8.5 | -2286, -107, -1564 | 46.9 / -16 |
| K7 Asia >=3 | 52 | 60776 | 63185 | 3.8 | 3.8 | yes | -54669 | 476 | -190 | -1.1 | -187 | -14.5, -3.3, -2.0 | -452, -366, -26 | 20.7 / -16 |
| P7 Asia all5 | 52 | 64194 | 63185 | -1.6 | -1.6 | no | -52050 | 3095 | -3880 | -22.2 | -3845 | -6.2, -39.0, -42.8 | -4626, -5770, -3853 | 82.1 / -57 |
| stack >=4 gate | 52 | 88768 | 63185 | -40.5 | -40.5 | no | -61944 | -6799 | -3510 | -20.1 | -3419 | -7.4, -19.1, 18.4 | -3541, -6432, -4578 | 24.9 / -22 |
| K7 Asia >=4 + P7 Asia all5 | 52 | 63479 | 63185 | -0.5 | -0.5 | no | -51949 | 3196 | -4625 | -26.4 | -4578 | -43.0, -19.7, -38.3 | -5415, -4158, -5395 | - |
| P7 Asia SL2 >=4 | 52 | 77232 | 63185 | -22.2 | -22.2 | no | -46871 | 8274 | -3798 | -21.7 | -3767 | - | - | - |

### PRE

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 75 | 71043 | 76186 | 6.8 | - | yes | -52547 | 0 | 59 | 0.6 | 63 | - | - | 38.1 / -5 |
| K7 Asia >=3 | 75 | 85605 | 76186 | -12.4 | - | no | -52547 | 0 | 131 | 1.3 | 136 | - | - | 34.2 / -1 |
| P7 Asia all5 | 75 | 102865 | 76186 | -35.0 | - | no | -56155 | -3608 | -2289 | -22.5 | -2271 | - | - | 45.3 / -52 |
| stack >=4 gate | 75 | 89892 | 76186 | -18.0 | - | no | -40933 | 11614 | -691 | -6.8 | -625 | - | - | -21.8 / -25 |
| K7 Asia >=4 + P7 Asia all5 | 75 | 97401 | 76186 | -27.8 | - | no | -56155 | -3608 | -1885 | -18.5 | -1866 | - | - | - |

### X'

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 44 | 51268 | 55326 | 7.3 | - | no | -26516 | -4853 | -198 | -5.5 | -196 | - | - | 46.4 / -83 |
| K7 Asia >=3 | 44 | 55895 | 55326 | -1.0 | - | yes | -26504 | -4840 | -79 | -2.2 | -78 | - | - | 42.4 / 86 |
| P7 Asia all5 | 44 | 71918 | 55326 | -30.0 | - | no | -30158 | -8494 | 813 | 22.7 | 812 | - | - | 61.5 / -104 |
| stack >=4 gate | 44 | 56512 | 55326 | -2.1 | - | no | -33434 | -11770 | -1394 | -38.9 | -1358 | - | - | 23.4 / -28 |
| K7 Asia >=4 + P7 Asia all5 | 44 | 67328 | 55326 | -21.7 | - | no | -30989 | -9325 | 763 | 21.3 | 763 | - | - | - |

### GAP

| rule | weeks | engine maxDD | JN05W2 | engine DD cut % | DD cut % W44 removed | tolerant gate (DD cut > -2 %, mean >= -3 %) | worst wk | d worst wk | d mean $/wk | d mean % | d mean @4.84 | placebo DD cut % (3 draws) | placebo d mean | table-level DD cut % / d $/wk % |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| K7 Asia >=4 | 18 | 67001 | 68947 | 2.8 | - | yes | -67001 | 1946 | 439 | 3.5 | 435 | - | - | 53.0 / -36 |
| K7 Asia >=3 | 18 | 69339 | 68947 | -0.6 | - | yes | -69339 | -392 | -339 | -2.7 | -343 | - | - | 23.9 / -32 |
| P7 Asia all5 | 18 | 89715 | 68947 | -30.1 | - | no | -71195 | -2249 | -1875 | -15.1 | -1855 | - | - | 29.0 / -96 |
| stack >=4 gate | 18 | 87831 | 68947 | -27.4 | - | no | -67714 | 1233 | 194 | 1.6 | 253 | - | - | 34.8 / -31 |
| K7 Asia >=4 + P7 Asia all5 | 18 | 86902 | 68947 | -26.0 | - | no | -69250 | -303 | -1774 | -14.3 | -1757 | - | - | - |

<!--/ENG-->

## 3. Open items (what runs next)
CF hook identity PROVEN: TL3_CF_ID 202610 = 598 trades / 25,943.82, row-identical to JN05W2. Skip side-effect check TL3_CF_SK1 (3 signals skipped, 1 halved, all in 202610): trade count stays 598 but total moves to 28,574.50 because a skipped signal frees the book and a later signal of the same book is taken instead (5 trades dropped, 5 new, 3 resized): a table-level skip rule overstates or understates what the live stack does, so every finalist needs its exact-engine run. Skipped-signal rows, $/R double controls, frontier per book/session, size by score, redundancy clusters across 3,144 + 3,652 indicator columns, USER_SET controls on R: pending.

For the build list (W-JV): USER_SET_V0 needs only D7's own 5-min and 15-min bars and the session / prior-day levels and prior-day profile D7 already keeps (CCI 14, EMA 8/21, Bollinger-Keltner squeeze, session opens/highs/lows, prior-day POC and value area); no new feed. The 'no high-volume node between entry and target' part of item 3 needs the prior-day profile only. 
