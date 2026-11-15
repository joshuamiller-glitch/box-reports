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

## 2. Machinery and its validation (steps 4-5)
Built and tested on a stand-in table: planted +$800/+$1,500 edge recovered by greedy and by the 2-week walk-forward (905 vs 219 $/trade OOS, DD cut 6x, matched-count controls pass); shuffled outcomes rejected; a leak (open-trade results in 'previous trade' columns) produced a fake 3x OOS edge and was removed (W-CF1 informed; v1 table defines L columns over closed trades only).
First run of the searched families on the PARTIAL table (A, E, L categories only, 271 conditions), stack-wide walk-forward (trailing 52 weeks, 2-week refits, first test 2023-10-16): score on positive-alone items 7.3 trades/day $184 vs $117 per trade but max DD 75k vs 92k and DD percentile 0.33; one-per-category 0.70; cluster score 0.09; greedy must-have list 0.57 trades/day $527 vs $117, DD percentile 0.87, items change on most refits (stability 0.34); gradient boosting (upper bound) 9 trades/day $175, DD worse than all trades. None passes the matched-count test on drawdown. The full run on the v1 table (with U) is in progress; the 50 shuffled-outcome search reruns and the per-block importance table follow once the M, F-J and Block 2-5 columns are in.

<!--ENG-->
## 3b. Engine numbers for the USER_SET_V0 leads (exact engine, JN05W2 base, all layers ON, hook cf_hooks as a skip gate on top; engine fee $1.18; base lots; official weekly basis of jv_score; reference JN05W2)

Skip rule applies to the signals in the entry table (taken JN05W2 signals); signals that appear only because a skipped one freed the book pass through UNGATED, so the engine result is the honest effect of "skip these", not of "run the checklist on every signal". Placebos = same number of skips drawn at random within book/session/month (PB1-3).

<!--/ENG-->

## 3. Open items (what runs next)
CF hook identity PROVEN: TL3_CF_ID 202610 = 598 trades / 25,943.82, row-identical to JN05W2. Skip side-effect check TL3_CF_SK1 (3 signals skipped, 1 halved, all in 202610): trade count stays 598 but total moves to 28,574.50 because a skipped signal frees the book and a later signal of the same book is taken instead (5 trades dropped, 5 new, 3 resized): a table-level skip rule overstates or understates what the live stack does, so every finalist needs its exact-engine run. Skipped-signal rows, $/R double controls, frontier per book/session, size by score, redundancy clusters across 3,144 + 3,652 indicator columns, USER_SET controls on R: pending.

For the build list (W-JV): USER_SET_V0 needs only D7's own 5-min and 15-min bars and the session / prior-day levels and prior-day profile D7 already keeps (CCI 14, EMA 8/21, Bollinger-Keltner squeeze, session opens/highs/lows, prior-day POC and value area); no new feed. The 'no high-volume node between entry and target' part of item 3 needs the prior-day profile only. 
