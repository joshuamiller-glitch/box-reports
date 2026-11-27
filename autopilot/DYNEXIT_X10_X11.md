# DYNEXIT X10 adaptive exit, X11 learned exit policy, X13 probability exit (W-DYNML)

QUICK SCREEN label on every number: 17 live books (Asia 3, NY AM 7, London 3, NY PM 4), the book own entries, 1 NQ lot, $20/pt, $4.84/lot cost, one position at a time, session total = sum of its books at 1 lot (S1 proxy, NOT the exact mix). Baseline = the book OWN FIXED BRACKET WITHOUT the live Trade Health (Trade Health is not modelled in the quick screen; the exact "bracket + TH" baseline from Q0 sets was not used). Entries not hindsight-free (live books chosen on the same weeks); Test 5 qualifier entries NOT yet run. Pessimistic stop-fill label NOT yet run.

## ANSWER FIRST

1. **No solution, no robust candidate.** FIXED RULES (committed 03:50Z before scoring, fixed_rules_ml.json): X10 fixed table is harmful (deeper chained drawdown and much lower income in every session); X11 frozen GBM and X13 frozen ridge shallower chained drawdown in only 8 and 5 of 17 books (5 and 2 with income within -10%), 0 books win at least 2 of 3 years AND both L6M and L3M. Session level: no fixed rule wins.
2. **WALK-FORWARD (2/4/13 weeks, 34 variants x 3 steps x 4 sessions = 408 session rows): 8 rows clear the per-period clause, and 62 of 408 have a sign-test p <= 0.05 against about 20 expected by chance because the rows are heavily correlated; none of the 8 holds across steps or recent windows.** The one that looks best: **Asia X11 joint th0.3, 13-week step: 10 of 12 periods shallower, chained max DD 27,858 -> 23,089, worst week -13,462 -> -11,968, income 158,285 -> 145,622 (-8%)**. It FAILS at the 2-week step (48/77, DD 27.9k -> 35.2k) and 4-week step (26/39 shallower, DD 27.9k -> 23.9k but worst week deeper), and its L6M/L3M drawdown is deeper (18.6k -> 20.8k, 11.3k -> 13.0k); its frozen no-refit version fails too. Treat as a weak first-clause hit, not a candidate (8 of 408 rows is chance level; Josh 2-week rhythm does not support it).
3. **Which is better, fixed or re-fit**: re-fitting adds a little for X11 (13-week walk-forward in Asia and NY AM clears the first clause at some settings where the frozen model does not) and nothing for X10 (adaptive switching loses roughly 10-70% of income at every step; the only shallower-drawdown rows at 4 and 13 weeks cost 25-40% income). The X13 explainable ridge barely fires (predictions shrink toward zero): th0.15 changes chained DD by -1% to -6% and income by -3% to -10%; th0.3 never fires. Faster re-picks (2 weeks) are worse than 13 weeks for every family, consistent with the other WF pages.
4. Honest limits: the baseline lacks Trade Health; per-period DD at 2 weeks is noisy; signals are shared across recipes, so trade counts rise when exits are earlier (policy rows take up to about 17% more trades than the baseline, so no random-skip null was needed; income gains/losses are not from taking fewer trades).

## Counts (luck charge)

Per book: X10 = 3 sides x 5 regime rules (HAR tercile, prior-session efficiency, combined 2x2, range-so-far vs forecast, none = family re-picked without regime) + 1 rich-pool = 16 per step; X13 = 3 sides x 3 thresholds; X11 = 3 sides x 3 thresholds; x 3 steps (2, 4, 13) = 102 variants per book, 1,734 book-variants, 408 session rows (scoreboard lines, methods DYNEXIT_X10 / X11 / X13, primary versions X10|joint|har3, X11|joint|th0.3, X13|joint|th0.3; all other rows marked reference), plus 3 fixed rules x (4 sessions + 17 books). Recipes recorded per book: about 149 (fixed brackets, X1 ATR/HAR, X4 trails, X5 staged, X6 time, 15 loss-only and 14 profit-only brackets). Walk-forward pick rule for X10: eligible = trailing 26 and 13 week income > 0 within the regime, >= 20 past trades; lowest ulcer over 52 weeks, then income; fallback own bracket.

## Method (what was built)

- Per-signal recorder (th_dynml/dml_rec.py): the gexit/sim_path kernel on every signal WITHOUT the one-position block (research copy of sim_path), then the block re-applied in python on the chosen recipe inside each forward period (dml_wf.py). Minute paths (close, favourable high, adverse low relative to entry) of the own fixed bracket for X11/X13.
- X10: regime from HAR forecast tercile / prior-session efficiency ratio / combination / range so far vs forecast; switch table re-picked at each decision date from past signals only (entry week < date). Loss-side pool = own target with stop varied (0.5-1.5x, ATR 1-3, HAR 0.06-0.15); profit-side pool = own stop with target varied (0.5-2x, ATR 1-4, HAR 0.1-0.3); joint pool = own, X1 ATR, X1 HAR bracket, X4 chandelier trail, X5 staged, X6 no-progress.
- X11: LightGBM regressor, 26 features (open profit in R, MFE/MAE in R, time in trade, session fraction left, ATR/own-bar range and HAR in R, 10-minute volatility and range, session range so far vs HAR, distance in R to session H/L, prior-day H/L/C, VWAP, overnight H/L, session open, hour, prior-session efficiency and direction), decision at the end of every minute in the trade; target = remaining move to the base exit in R (hold-to-exit expected gain), take when prediction < -theta R, tighten (stop 0.5R behind price) when < -theta/2; theta 0.15/0.3/0.5; loss side = acts only when open profit < 0, profit side only > 0. Walk-forward fit: trades exited >= 24 h before the decision (embargo; max observed hold per book up to 8 h, printed in res), last 104 weeks, 40k rows, 60 trees (lighter than the fixed rule 150 trees, for compute). No order-flow/depth features yet (price/bar/level only, as ordered; flow to be added from W-DYNOF inputs).
- X13: ridge on 8 explainable state terms (open R, open R^2, MFE, MAE, log time, open R x log time, ATR/R0, range vs HAR), same target and actions; theta 0.15/0.3/0.5. The hazard/survival version and the press (wider trail) action are NOT built (minute paths end at the base exit, so pressing beyond the target cannot be scored without new paths).

## FIXED RULE row (no re-fit; drawdown first; baseline = own bracket, no TH)

| session | rule | 2024 DD base->rule / income | 2025 | 2026 | L6M | L3M | ALL (from wk 52) |
|---|---|---|---|---|---|---|---|
| NY AM | X10F | 47906 -> 81345 / 96927 -> 68944 | 60427 -> 108211 / 183616 -> -7975 | 65938 -> 102505 / 187366 -> -11084 | 47677 -> 86059 / 219388 -> 383 | 47677 -> 86059 / 68274 -> -11523 | 67801 -> 110784 / 467910 -> 49884 |
| NY AM | X11F | 47906 -> 52683 / 96927 -> 92374 | 60427 -> 59359 / 183616 -> 137255 | 65938 -> 59626 / 187366 -> 150599 | 47677 -> 45521 / 219388 -> 174521 | 47677 -> 45521 / 68274 -> 32274 | 67801 -> 74368 / 467910 -> 380230 |
| NY AM | X13F | 47906 -> 60818 / 96927 -> 81461 | 60427 -> 61318 / 183616 -> 114544 | 65938 -> 60591 / 187366 -> 135929 | 47677 -> 38467 / 219388 -> 167899 | 47677 -> 38467 / 68274 -> 34457 | 67801 -> 83780 / 467910 -> 331935 |
| NY PM | X10F | 36030 -> 35512 / 27629 -> 8161 | 18654 -> 75705 / 105201 -> -1292 | 23045 -> 52779 / 84699 -> 14310 | 17265 -> 38436 / 97470 -> 28428 | 12919 -> 21221 / 37469 -> 39409 | 36030 -> 105398 / 217529 -> 21179 |
| NY PM | X11F | 36030 -> 31916 / 27629 -> 11074 | 18654 -> 15185 / 105201 -> 80543 | 23045 -> 30904 / 84699 -> 69061 | 17265 -> 12478 / 97470 -> 77306 | 12919 -> 10611 / 37469 -> 31085 | 36030 -> 32041 / 217529 -> 160679 |
| NY PM | X13F | 36030 -> 38130 / 27629 -> 25650 | 18654 -> 19519 / 105201 -> 90591 | 23045 -> 35067 / 84699 -> 46084 | 17265 -> 16243 / 97470 -> 66375 | 12919 -> 11293 / 37469 -> 25732 | 36030 -> 38428 / 217529 -> 162327 |
| Asia | X10F | 23429 -> 20338 / 41092 -> 67195 | 23437 -> 45184 / 42280 -> 3899 | 27858 -> 32352 / 53603 -> 62631 | 18647 -> 31179 / 52950 -> 73761 | 11325 -> 26653 / 15278 -> -87 | 27858 -> 45184 / 136976 -> 133726 |
| Asia | X11F | 23429 -> 23532 / 41092 -> 31734 | 23437 -> 25552 / 42280 -> 24131 | 27858 -> 22422 / 53603 -> 19792 | 18647 -> 19899 / 52950 -> 25432 | 11325 -> 19899 / 15278 -> -4328 | 27858 -> 32756 / 136976 -> 75658 |
| Asia | X13F | 23429 -> 23239 / 41092 -> 40944 | 23437 -> 24830 / 42280 -> 23046 | 27858 -> 27539 / 53603 -> 26282 | 18647 -> 25386 / 52950 -> 36076 | 11325 -> 14999 / 15278 -> 3397 | 27858 -> 30513 / 136976 -> 90273 |
| London | X10F | 12065 -> 71226 / 58288 -> -65025 | 50453 -> 73134 / 49143 -> -21108 | 25582 -> 45855 / 110857 -> 19068 | 15543 -> 45855 / 104269 -> 16784 | 15543 -> 24336 / 63273 -> 7397 | 50453 -> 116473 / 218288 -> -67065 |
| London | X11F | 12065 -> 13908 / 58288 -> 41921 | 50453 -> 56336 / 49143 -> 9079 | 25582 -> 27873 / 110857 -> 107702 | 15543 -> 17576 / 104269 -> 95386 | 15543 -> 17576 / 63273 -> 57999 | 50453 -> 56336 / 218288 -> 158703 |
| London | X13F | 12065 -> 12065 / 58288 -> 55650 | 50453 -> 55788 / 49143 -> 42093 | 25582 -> 25582 / 110857 -> 110857 | 15543 -> 15543 / 104269 -> 104269 | 15543 -> 15543 / 63273 -> 63273 | 50453 -> 55788 / 218288 -> 208601 |

Free settings: X10 fixed 0 (table written a priori), X13 fixed 1 (theta), X11 fixed 1 (theta). Verdict: all FAIL (no session wins 2 of 3 years with both recent windows).

## WALK-FORWARD, primary versions (chained out-of-sample max DD, worst week, income; baseline fixed bracket)

| family | session | step | periods shallower | maxDD base -> var | worst week | income | verdict |
|---|---|---|---|---|---|---|---|
| X10|joint|har3 | Asia | 2 wk | 52/77 | 27858 -> 35200 | -13462 -> -13826 | 158285 -> 80084 | FAIL |
| X10|joint|har3 | Asia | 4 wk | 27/39 | 27858 -> 24244 | -13462 -> -9889 | 158285 -> 90327 | FAIL |
| X10|joint|har3 | Asia | 13 wk | 10/12 | 27858 -> 28253 | -13462 -> -9641 | 158285 -> 102932 | FAIL |
| X10|joint|har3 | NY AM | 2 wk | 42/77 | 67801 -> 78102 | -29241 -> -34603 | 549397 -> 301525 | FAIL |
| X10|joint|har3 | NY AM | 4 wk | 20/39 | 67801 -> 81716 | -29241 -> -34603 | 549397 -> 252699 | FAIL |
| X10|joint|har3 | NY AM | 13 wk | 5/12 | 67801 -> 75242 | -29241 -> -34603 | 549397 -> 309160 | FAIL |
| X10|joint|har3 | London | 2 wk | 35/77 | 50453 -> 44205 | -21136 -> -19648 | 265167 -> 159337 | FAIL |
| X10|joint|har3 | London | 4 wk | 11/39 | 50453 -> 44071 | -21136 -> -19648 | 265167 -> 119656 | FAIL |
| X10|joint|har3 | London | 13 wk | 5/12 | 50453 -> 53212 | -21136 -> -19648 | 265167 -> 81265 | FAIL |
| X10|joint|har3 | NY PM | 2 wk | 43/77 | 36030 -> 32258 | -12600 -> -23058 | 265060 -> 204644 | FAIL |
| X10|joint|har3 | NY PM | 4 wk | 20/39 | 36030 -> 34684 | -12600 -> -26791 | 265060 -> 236358 | FAIL |
| X10|joint|har3 | NY PM | 13 wk | 3/12 | 36030 -> 64632 | -12600 -> -23058 | 265060 -> 98378 | FAIL |
| X11|joint|th0.3 | Asia | 2 wk | 48/77 | 27858 -> 35231 | -13462 -> -14568 | 158285 -> 117512 | FAIL |
| X11|joint|th0.3 | Asia | 4 wk | 26/39 | 27858 -> 23855 | -13462 -> -14447 | 158285 -> 142401 | FAIL |
| X11|joint|th0.3 | Asia | 13 wk | 10/12 | 27858 -> 23089 | -13462 -> -11968 | 158285 -> 145622 | PASS |
| X11|joint|th0.3 | NY AM | 2 wk | 47/77 | 67801 -> 85207 | -29241 -> -27831 | 549397 -> 440176 | FAIL |
| X11|joint|th0.3 | NY AM | 4 wk | 23/39 | 67801 -> 66086 | -29241 -> -27831 | 549397 -> 432766 | FAIL |
| X11|joint|th0.3 | NY AM | 13 wk | 9/12 | 67801 -> 63888 | -29241 -> -27047 | 549397 -> 492195 | FAIL |
| X11|joint|th0.3 | London | 2 wk | 29/77 | 50453 -> 35678 | -21136 -> -19321 | 265167 -> 244682 | FAIL |
| X11|joint|th0.3 | London | 4 wk | 12/39 | 50453 -> 46744 | -21136 -> -19321 | 265167 -> 229148 | FAIL |
| X11|joint|th0.3 | London | 13 wk | 5/12 | 50453 -> 37503 | -21136 -> -18780 | 265167 -> 230178 | FAIL |
| X11|joint|th0.3 | NY PM | 2 wk | 41/77 | 36030 -> 35392 | -12600 -> -13646 | 265060 -> 255536 | FAIL |
| X11|joint|th0.3 | NY PM | 4 wk | 15/39 | 36030 -> 28592 | -12600 -> -13646 | 265060 -> 222606 | FAIL |
| X11|joint|th0.3 | NY PM | 13 wk | 5/12 | 36030 -> 46856 | -12600 -> -12305 | 265060 -> 198743 | FAIL |
| X13|joint|th0.3 | Asia | 2 wk | 6/77 | 27858 -> 27858 | -13462 -> -13462 | 158285 -> 161454 | FAIL |
| X13|joint|th0.3 | Asia | 4 wk | 5/39 | 27858 -> 27858 | -13462 -> -13462 | 158285 -> 162219 | FAIL |
| X13|joint|th0.3 | Asia | 13 wk | 2/12 | 27858 -> 27858 | -13462 -> -13462 | 158285 -> 156755 | FAIL |
| X13|joint|th0.3 | NY AM | 2 wk | 6/77 | 67801 -> 67801 | -29241 -> -29146 | 549397 -> 543102 | FAIL |
| X13|joint|th0.3 | NY AM | 4 wk | 4/39 | 67801 -> 67801 | -29241 -> -29146 | 549397 -> 541566 | FAIL |
| X13|joint|th0.3 | NY AM | 13 wk | 3/12 | 67801 -> 67801 | -29241 -> -28481 | 549397 -> 543147 | FAIL |
| X13|joint|th0.3 | London | 2 wk | 0/77 | 50453 -> 50453 | -21136 -> -21136 | 265167 -> 266087 | FAIL |
| X13|joint|th0.3 | London | 4 wk | 0/39 | 50453 -> 50453 | -21136 -> -21136 | 265167 -> 263073 | FAIL |
| X13|joint|th0.3 | London | 13 wk | 1/12 | 50453 -> 50453 | -21136 -> -21136 | 265167 -> 263343 | FAIL |
| X13|joint|th0.3 | NY PM | 2 wk | 3/77 | 36030 -> 36030 | -12600 -> -12600 | 265060 -> 267490 | FAIL |
| X13|joint|th0.3 | NY PM | 4 wk | 2/39 | 36030 -> 36030 | -12600 -> -12600 | 265060 -> 265913 | FAIL |
| X13|joint|th0.3 | NY PM | 13 wk | 1/12 | 36030 -> 36030 | -12600 -> -12600 | 265060 -> 253495 | FAIL |

## Rows that cleared the per-period clause (all variants; post-hoc best of 408)

| session | variant | step | shallower | maxDD | worst week | income | sign p |
|---|---|---|---|---|---|---|---|
| London | X11|loss|th0.5 | 13 | 4/12 | 50453 -> 46512 | -21136 -> -18850 | 265167 -> 270532 | 0.927 |
| NY AM | X10|prof|combo | 13 | 9/12 | 67801 -> 57498 | -29241 -> -31619 | 549397 -> 503722 | 0.073 |
| NY AM | X10|prof|har3 | 13 | 10/12 | 67801 -> 71939 | -29241 -> -27392 | 549397 -> 501731 | 0.019 |
| NY AM | X10|prof|none | 13 | 8/12 | 67801 -> 64005 | -29241 -> -31739 | 549397 -> 582027 | 0.194 |
| NY AM | X11|prof|th0.3 | 13 | 9/12 | 67801 -> 60239 | -29241 -> -27926 | 549397 -> 507895 | 0.073 |
| NY AM | X13|joint|th0.15 | 13 | 8/12 | 67801 -> 68950 | -29241 -> -26531 | 549397 -> 515756 | 0.194 |
| Asia | X11|joint|th0.3 | 13 | 10/12 | 27858 -> 23089 | -13462 -> -11968 | 158285 -> 145622 | 0.019 |
| Asia | X11|loss|th0.3 | 4 | 27/39 | 27858 -> 26131 | -13462 -> -13819 | 158285 -> 161113 | 0.012 |

Per-book rows and every variant: /mnt/l2/l2vast/_dynml/agg.json (session and book level), aggF.json (fixed). Scoreboard: 420 lines appended to /mnt/l2/l2vast/_wf/scoreboard_rows.jsonl. Code: code/th_dynml (dml_rec, dml_wf, dml_x10, dml_pol, dml_book, dml_fixed, dml_agg, dml_aggF).

## NEXT

1. Test 5 qualifier entries (non-hindsight sample) for the same rules; 2. exact Trade Health baseline from Q0 rows; 3. add flow/depth features to X11 from W-DYNOF/W-DYNX8 when ready; 4. X13 hazard version and press action (needs paths beyond the target); 5. pessimistic fill rescore of any survivor; 6. X10 finalist pool swapped for the other agents finalists once /mnt/l2/l2vast/_dynexit/ candidate files exist (placeholders used).

## ROUND 2 (0349Z), item 2 first: is anything predictable inside a trade? (price/bar/level features, purged walk-forward, 13-week refit, 17 live books)

Target = remaining move to the base exit in R (clipped +-4), rows = every minute of every trade of the own fixed bracket, test rows = forward periods from week 26 on, models fitted only on trades exited >= 24 h before each decision. Out-of-sample, per book then averaged over 17 books:
- LightGBM: R2 vs mean -0.12 (every book negative, range -0.06 to -0.20), row correlation about 0.00 (8 of 17 positive), per-trade correlation -0.09 (0 of 17 positive), AUC for target-before-stop 0.44 (below 0.5 in every book).
- Ridge (X13): R2 -0.017 (0 of 17 positive), correlation -0.01, AUC 0.51.
ANSWER: with price, bar-volatility, MAE/MFE, time and level-distance features there is NO out-of-sample predictability of the remaining move inside a trade on these 17 books; the GBM is worse than predicting the mean (it overfits and ranks backwards). This matches the attribution result. Flow/depth feature version NOT yet run (needs th_dynof code and per-trade depth snapshots). Items 1 (hazard, press), 3 (real finalists), 4 (Test 5 entries), 5 (London/NY PM stores) not yet done.

### Round 2 item 2b and positive control
Positive control (same pipeline): next-15-minute realised range in R, out-of-sample R2 0.40 (0.30-0.49, 17/17 books), correlation 0.63; log minutes left to base exit R2 0.32 (corr 0.69). So the pipeline works; volatility and duration are forecastable inside a trade.
Flow/depth features (16, from the 1-s tables, window ends 1 s before the decision: 60-s and 300-s delta share, OFI share and z, trade-rate ratio, sweep share, big-print share, bid/ask cancel and add imbalance at the touch, spread, microprice minus mid, 10-level depth imbalance, EMA depth imbalance, total depth, depletion imbalance), LightGBM, purged 13-week walk-forward, 17 books, target = remaining move to the base exit in R:
| feature set | R2 | corr | AUC |
|---|---|---|---|
| price/level only | -0.1245 | -0.001 | 0.441 |
| price + flow/depth | -0.1229 | +0.004 | 0.442 |
| flow/depth only | -0.0218 | -0.003 | 0.503 |
Flow adds nothing out of sample (R2 negative in 17/17 books in every set; flow-only AUC 0.503, 9 of 17 books above 0.5). ANSWER: nothing we can measure (price, levels, order flow, 10-level depth) predicts the outcome of the rest of an open trade on these books; only volatility and duration are predictable. Not yet run: London/NY PM stores, Test 5 entries, X13 hazard/press, X10 on real finalists. (Tape only through 10 levels; MBO-based features not built.)

## ROUND 3 (quick screen, server C, defaults committed in autopilot/fixed_rules_ml_r3.json at 06:15Z before scoring)
1. USING WHAT IS PREDICTABLE. The frozen entry-time forecasts do work out of sample (next-60-min range: squared log correlation 0.37; hold time: correlation 0.46), but as exit inputs they do not beat the fixed bracket.
 - VOLSCALE (bracket x clip(forecast/median, 0.5, 2)): shallower chained DD than the own bracket in 6 of 17 books (5 with income within -10%); shuffled-forecast null p about 0.56 (indistinguishable). Sessions: London wins 2025 and both L6M/L3M (L6M DD 15.5k -> 15.2k, income +34%) but loses 2024 and 2026 (DD 12.1k -> 18.0k, 25.6k -> 40.4k); Asia, NY AM, NY PM deeper in L6M (Asia 18.6k -> 42.6k, NY AM 47.7k -> 64.4k, NY PM 17.3k -> 50.9k).
 - TIMESTOP (exit when time in trade > 1.5 x predicted hold): shallower in 5 of 17 books (5 with income ok), null p about 0.51. Asia ties (ALL DD 27.9k -> 27.7k, income +2%, L6M 18.6k -> 18.5k, won 2024 and 2026), NY AM wins L6M/L3M (47.7k -> 41.0k) but loses 2024 and 2025 and costs 19% of ALL income; London and NY PM worse.
 - Verdict: no candidate. Knowing the volatility or duration does not make the stop/target better than the fixed bracket on these books.
2. X13 HAZARD/STATE TABLE (P(trade ends in profit | 5-min time bucket x 0.5R open bucket), frozen on first 52 weeks; take when open>0 and p<0.35, cut when open<0 and p<0.25): shallower DD in 6 of 17 books (3 with income ok); sessions lose 35-55% of income (NY AM ALL 468k -> 291k with DD 67.8k -> 109k). FAIL. PRESS (trail wider when EV rises) is NOT scored: minute paths end at the base exit, so it needs a trail-kernel re-run; not done.
3. Predictability check on London and NY PM: those are already inside the 17 live books (London 3, NY PM 4: GBM R2 negative in every one). The W-PLAN-LO store and W-PLAN-NP exact entries table (/mnt/l2/l2vast/_plan_np/np_entries.parquet, exact trades with S0/T0) are NOT yet run through it (different data model; needs tape-path extraction from entry_ns).
4. Test 5 qualifier entries (non-hindsight): 200 randomly sampled primary-pick cells (50 per session, seed 3) are running through the same lean recorder + purged walk-forward (/mnt/l2/l2vast/_dynml/oos_t5, slow because of CPU share). First 16 Asia cells: GBM R2 -0.077 to -0.200 (all negative), ridge R2 -0.04 to +0.01, GBM AUC 0.43 (0.38-0.49): same null as the hindsight live books.

## ROUND 4 (defaults committed 07:30Z in autopilot/fixed_rules_ml_r4.json before scoring; quick screen, 17 live books, baseline own bracket without Trade Health)
Stuck-trade exit gated by forecasts (exit when under water and best excursion < 0.25 R after a minute threshold): STUCK0 = 45 min (reproduction of the shared default), STUCK_G = max(15, predicted hold), STUCK_H = 45 x clip(median HAR / HAR, 0.5, 2). Pessimistic fill = every base stop exit and every policy market exit 2 ticks worse (shown second).
| rule | normal: books DD shallower / and income ok | pessimistic | null (same count random exits): books with p(DD)<0.1 |
|---|---|---|---|
| STUCK0 | 8 / 8 | 9 / 6 | 3 of 17 (1.7 expected by chance) |
| STUCK_G (hold-time gate) | 7 / 5 | 8 / 5 | 3 of 17 |
| STUCK_H (HAR gate) | 9 / 4 | 7 / 4 | 3 of 17 |
Sessions (ALL from wk 52, normal; maxDD base -> rule / income base -> rule): STUCK0 London 50.5k -> 33.9k / 218k -> 192k (2025 and ALL win, 2024 and L6M/L3M lose: L6M 15.5k -> 19.9k), NY AM 67.8k -> 67.9k / 468k -> 477k (flat), Asia 27.9k -> 28.5k / 137k -> 119k (2024 wins, later years lose), NY PM 36.0k -> 40.9k / 218k -> 177k (loses). The gates do not improve it: STUCK_G is flat to slightly better only in NY AM (ALL DD 67.8k -> 62.3k, income -9%, L6M/L3M 47.7k -> 43.5k) and worse elsewhere; STUCK_H helps Asia 2024/L6M but deepens Asia 2026 and L3M, and costs London 40% of income. Verdict: neither the predicted hold time nor the range forecast is a useful gate; the reproduced stuck exit itself is mixed in this quick screen (8 of 17 books shallower, session level only London clearly), so it is not carried by these gates. Pessimistic fills change no verdict.
Test 5 qualifier cells (non-hindsight): 19 Asia cells finished of the 200-cell sample (the rest still running at low CPU share): GBM R2 mean -0.146 (0 of 18 positive), AUC 0.42 (0 of 18 above 0.5); ridge R2 -0.013 (1 of 18 positive), AUC 0.53 (13 of 18 above 0.5 but R2 not positive). Same null as the live books.

## ALGO LOOP C (learned loop on action values; 13:05Z/13:07Z orders) - first result, Asia MF1 only, QUICK SCREEN
Dataset (/mnt/l2/l2vast/_dynml/algo/*_ds.npz, 17 live books built): every signal replayed second by second on the NQ 1-s series with a SAFETY STOP ONLY (1.5 x own stop, no target); state every 60 s; labels = advantage over holding for take-all, tighten (stop 0.5R behind price), part (half off), trail (1R trail), computed by policy evaluation on the replayed rest of the path. Features: open R, MFE/MAE, time in trade, time to session end, own R0, HAR/ATR/hour/prior-session efficiency, NQ returns 60/300/900 s, ES/RTY/CL/ZN returns 60/300 s, ES-NQ gap (flow/depth features: builder ready, not yet in the fit). Four LightGBM regressors, purged walk-forward refit 2/4/13 weeks, policy = best action if predicted advantage > theta (0.1/0.2/0.3 R), replay second by second, decisions each 60 s.
Asia MF1 (Lb0e6dfa3, long, own 40/80), weeks 52-181 chained forward, vs own bracket (normal fills): loss-side loop theta 0.2: 13-wk step DD 18.6k -> 6.7k, income 62.9k -> 202.6k, 11/12 periods shallower; 4-wk 32/39, DD 7.5k, 181k; 2-wk 61/77, DD 6.1k, 184k; L6M DD 18.6k -> 5.1k, income 26k -> 77k. Profit-side loop FAILS (DD 20k, income 59k); joint passes (DD 8.3k, 145k). Pessimistic (decision executes 5 s later, 0.5 pt extra on every market exit and stop fill, applied to the bracket baseline too): loss loop theta 0.2: DD 19.3k -> 8.2k, income 55k -> 186k (13-wk 11/12, 4-wk 31/39, 2-wk 55/77). Random-management null (predictions permuted within each forward period, 30 draws, 13-wk): real loss loop income 192.8k / DD 6.7k vs null mean 47k (p95 68k) / DD 17.7k: beats every draw; joint real 138k vs null -29k. Out-of-sample R2 of the advantage labels is negative (-0.03 to -0.14), so the model ranks actions but does not predict their size; the earlier null on 'remaining move' is not contradicted.
CAVEATS: one book; quick screen; blocking one position at a time (loop frees entries: 1,362 trades vs 1,256 for the bracket); winners run to session end (no target) in a rising NQ sample; entries hindsight-tuned; no Trade Health; not the exact engine; rest of the 16 books (Asia and NY AM first) fitting on C now.

## ALGO LOOP C: WITHDRAWN (2026-11-27 19:30Z / 20:05Z)
The Asia MF1 loop C 'pass' was produced by a fill bug in my quick screen (a trail stop set above the market under water was filled at the stop level, not at the market). Exact engine: alone bare income -62%, DD -228k vs -111k; mix -34% income. Per-trade diagnosis and corrected quick screen (no variant passes, DD 18.6k -> 18.8k, income 62.9k -> 22.3k at 13 weeks) are in MORNING.md (19:30Z, 20:05Z). All loop C sections above this one (first result, stress, null, per-book table, hook bundles, v2 plan) are void. Buggy artefacts kept under server C /mnt/l2/l2vast/_dynml/algo_buggy.
