# SPEC_LONDON_RANGE_MP - exact live spec of the London range-used-up skip, M7 + P7 only (LS1_MP k=1, LS125_MP k=1.25)
Written 2026-11-16 13:31Z by W-LR for D7 v2.0 build prep (USER ORDER BUILD PREP item 1; deadline order: no engine time used, every number from finished runs and stored trades). Research only, nothing on the execution server changes. **FIRST PASS: not a PASS claim.**

**VERDICT (plain).** Recommend k = 1 (LS1_MP). On the live-equivalent base JN05W2JL2 (43 months, final) it adds about +1,657 / +895 $/wk base (L3M / L6M; x1.75 live +2,899 / +1,567) and +395 HOLD, +567 GAP, +524 PRE, -189 X', beating its three matched random-skip controls on mean in L3M, L6M, HOLD, PRE (not GAP, not X') and on DD in L3M, L6M, GAP, PRE (NOT HOLD). Strength: moderate on recent mean, weak on drawdown: the stack max DD is not reduced at a long horizon (FULL 43 months: -74.4k -> -78.2k, HOLD -74.4k -> -78.2k, because a skip frees the book: PATH EFFECT = FREED-BOOK REPLACEMENT, generic). It passes the T-RECENTS tolerant gate, fails the strict gate. **Fidelity warning (section 7): the engine compares a forecast in engine-price points with a range-so-far measured on a ratio-adjusted bar file that is 3-14% smaller; the unit-consistent re-score (cells TL3_LR_JL2_LS1_MPUC / LS125_MPUC) is built and queued but NOT run (LR engine quota is 0 until 20:00Z). Treat k as provisional until it is run.**

Labelling: every number below is on the live-equivalent base **JN05W2JL2** (W-EV, live-faithful ATR series, 43 months landed) unless marked "OLD BASE (JN05W2)". Dollars are base (box) lots; live = x1.75 shown beside headline rows; the raw engine charges $1.18/contract round trip, the "$4.84" column reprices to FEES.md $4.84.

**UPDATE (unit-consistent re-score, section 10, supersedes the k=1 recommendation below).** Measured in TRUE engine points (what live D7 will measure), k=1 LOSES the recent gain (L3M -161, L6M -195 $/wk base; recent DD 11.6% worse); k=1.25 keeps a small gain (+895 / +408 / +174 $/wk in L3M / L6M / HOLD, x1.75 live +1,566 / +714 / +305; DD flat in recent windows, GAP +641 with +21.2% DD). The old-unit k=1 numbers in sections 1-8 are OLD-UNIT (range 3-14% understated). **Do not build k=1 in true points. The live threshold must be at least k=1.25 in true points; the equivalent of the old-unit k=1 skip share is a true-point k of about 1.4 (interpolated, NOT run). No matched random control exists for the unit-consistent cells.** Off / Shadow only.

## 1. What the rule does (as scored)
1. **Scope.** Engine session 1 = London = entry time 02:00:00 <= t < 08:30:00 America/New_York. Asia (18:00-02:00), pre-market (08:30-09:30), NY AM (09:30-12:00) and NY PM are never gated (identity: slice delta 0.0 in Asia). Books: **M7 and P7 only** (K7, U7, H7, A7, O7 untouched; legacy X3/X4/X5 never gated).
2. **Which signals.** At every *fresh entry signal* of M7 or P7 (the engine calls try_entry with a non-zero signal while the book has no open trade, no armed order, no entry in progress and no exit pending) the hook runs BEFORE any other entry logic (before lot gates, caps, locks). If it skips, the signal is simply dropped (the function returns); the same book may signal again the next second and is tested again.
3. **What happens to an open trade.** NOTHING. The hook only acts in try_entry on fresh entries. An open M7/P7 trade keeps its own stop, target, cuts, trails and caps; no early exit, no resize. Skipped signals never create a position.
4. **Test.** F = forecast session range in points = pred x last 1-minute close. rem = F - R, R = range used so far (section 3). Target distance T = stop_pts x target_r = 60 x 1.0 = 60 points for M7 and for P7 (base values; the hook restores them before each test). **Skip if T > k x max(rem, 0)**, i.e. skip if rem <= 0, or rem > 0 but 60 > k x rem. k = 1: skip when rem < 60; k = 1.25: skip when rem < 48.
5. **When inactive (= JN05W2JL2 behaviour):** no forecast row for the Globex day, forecast not finite, or fref (expanding median of past forecasts, needs >= 30 forecasts) not finite or <= 0. First forecast 2023-07-21, first usable day 2023-09-01 (about 4 months of X' 2023-04..08 therefore unscored by the rule; stated).

## 2. The range forecast (the variant used by LS1_MP / LS125_MP): ATR-only daily ridge, walk-forward
(No UW data, no HAR, no CME. The HAR variant (W-R2, fc_r2_har) and the intraday own-bar variant (OS cells) were NOT used for these cells and are not specified here.)
- **Target y(d)** = ln(H/L) over the London session of Globex day d: 1-minute bars with 02:00:00 <= bar start < 08:30:00 ET, H = highest high, L = lowest low (needs >= 195 of 390 bars). **RTH(d)** = ln(H/L) over 09:30:00 <= start < 16:00:00 ET (>= 195 of 390 bars). Bars are the NQ continuous 1-minute series jump-adjusted for >1.2%/min moves (ur_panel convention).
- **Days** = all weekdays (holidays carry NaN). d-1 = previous weekday row.
- **Features known at 02:00 ET of day d** (all from days before d): x1 = y(d-1); x2 = mean of y(d-5..d-1) (needs >= 3 non-NaN); x3 = mean of y(d-20..d-1) (needs >= 10); x4 = y(d-1) (duplicate of x1, kept: ridge handles it); x5 = mean of y(d-14..d-1) (needs >= 7); x6 = mean of RTH(d-14..d-1) (needs >= 7). Missing -> training median.
- **Model.** pred(d) = intercept + sum_i coef_i x x_i (ln-range fraction, e.g. 0.0081 = 0.81%). Ridge, lambda = 10, on features standardised with the training mean and sd, intercept = training mean of y; NaN features replaced by the training median. **Walk-forward:** expanding window; first fit when 120 weekday rows exist; refit every 10 weekday rows (days k..k+9 use the fit trained on days < k with finite y). The table below is the raw-coefficient form (apply to RAW features) of the latest refit and two earlier refits (full file /mnt/l2/l2vast/_londonrange/atr_coefs.json; code code/th_londonrange/lr_fc.py, lr_coef.py).

**refit applying from day 20261106 (971 training days): intercept 0.001456**

| # | feature | raw coefficient | train mean | train sd | NaN fill (median) |
|---|---|---|---|---|---|
| 1 | y[d-1] | 0.141812 | 0.007079 | 0.004586 | 0.006061 |
| 2 | mean(y[d-5..d-1]) | 0.297504 | 0.007050 | 0.003315 | 0.006377 |
| 3 | mean(y[d-20..d-1]) | 0.093849 | 0.007049 | 0.002492 | 0.006439 |
| 4 | y[d-1] (duplicate column) | 0.141812 | 0.007079 | 0.004586 | 0.006061 |
| 5 | mean(y[d-14..d-1]) | -0.072288 | 0.007047 | 0.002679 | 0.006533 |
| 6 | mean(rth[d-14..d-1]) | 0.090870 | 0.014921 | 0.005388 | 0.013562 |

**refit applying from day 20260828 (921 training days): intercept 0.001377**

| # | feature | raw coefficient | train mean | train sd | NaN fill (median) |
|---|---|---|---|---|---|
| 1 | y[d-1] | 0.147008 | 0.007029 | 0.004648 | 0.005994 |
| 2 | mean(y[d-5..d-1]) | 0.294476 | 0.007012 | 0.003392 | 0.006256 |
| 3 | mean(y[d-20..d-1]) | 0.088100 | 0.007009 | 0.002552 | 0.006339 |
| 4 | y[d-1] (duplicate column) | 0.147008 | 0.007029 | 0.004648 | 0.005994 |
| 5 | mean(y[d-14..d-1]) | -0.104409 | 0.007008 | 0.002743 | 0.006361 |
| 6 | mean(rth[d-14..d-1]) | 0.107926 | 0.015073 | 0.005472 | 0.013663 |

**refit applying from day 20250314 (545 training days): intercept 0.001585**

| # | feature | raw coefficient | train mean | train sd | NaN fill (median) |
|---|---|---|---|---|---|
| 1 | y[d-1] | 0.101888 | 0.006267 | 0.003419 | 0.005643 |
| 2 | mean(y[d-5..d-1]) | 0.269129 | 0.006239 | 0.002262 | 0.005812 |
| 3 | mean(y[d-20..d-1]) | -0.125522 | 0.006190 | 0.001506 | 0.005915 |
| 4 | y[d-1] (duplicate column) | 0.101888 | 0.006267 | 0.003419 | 0.005643 |
| 5 | mean(y[d-14..d-1]) | -0.213653 | 0.006201 | 0.001695 | 0.005904 |
| 6 | mean(rth[d-14..d-1]) | 0.272767 | 0.014053 | 0.003472 | 0.013319 |

- **Forecast at the entry second:** F = pred(d) x P, P = close of the last COMPLETE 1-minute bar (the engine variable last1m_close, engine price). pred(d) is fixed for the whole London session (computed once before 02:00 ET from data through the 16:00 ET close of d-1); only P moves. Example: pred 0.008059 x P 30,563 = F 246.3.

## 3. How "range used" is measured
R = (highest high - lowest low) over the 1-minute bars with start time from **02:00:00 ET of the signal's calendar date (London start)** up to and including the bar that starts at (signal second - 60), i.e. all COMPLETE minutes; fewer than 2 bars -> R = 0. High/low are the bar highs/lows (not closes), not rolled/gap-adjusted, taken from the NQ 1-minute file (/mnt/l2/l2vast/uwbooks/min1_NQ.npz). The signal second is the engine's try_entry second (the entry fill follows 1 second later: entry second = signal second + 1 in all 285 matched trades).

## 4. Five worked examples (JL2 base, engine skip log TL3_LR_JL2_LS1_MP, L6M; k = 1, T = 60)
Columns: signal second (ET) / book side / complete bars since 02:00 / pred / F / R (file points) / rem = F - R / T vs k x rem / decision / what JN05W2JL2 did with that signal (base lots).

| # | signal second | book side | bars | pred | F (engine px 30,563 etc.) | R | rem | 60 > rem? | decision | outcome of that signal in JN05W2JL2 (skipped = would-be) |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 SKIPPED WINNER | 2026-09-17 05:55:00 | P7 long | 235 | 0.006087 | 180.0 | 224.00 | -44.0 | yes (rem < 0: range already above forecast) | SKIP | +4,800 (4 lots, Target) |
| 2 SKIPPED WINNER | 2026-09-15 08:00:00 | P7 long | 358 | 0.007598 | 221.3 | 196.25 | 25.1 | yes (60 > 25.1) | SKIP | +2,403 (2 lots, Target) |
| 3 SKIPPED LOSER | 2026-06-19 07:01:00 | P7 short | 301 | 0.008059 | 246.3 | 186.50 | 59.8 | yes (60 > 59.8, by 0.2 pt: marginal) | SKIP | -2,699 (4 lots, StateCut) |
| 4 SKIPPED LOSER | 2026-10-06 07:44:01 | P7 long | 344 | 0.006906 | 217.6 | 195.75 | 21.8 | yes (60 > 21.8) | SKIP | -2,539 (4 lots, StateCut) |
| 5 KEPT | 2026-08-03 02:40:01 | M7 short | 40 | 0.008687 | 248.6 (pred x entry px 28,619, +-0.1) | 51.00 | 197.6 | no (60 < 197.6) | KEEP (trade taken) | +1,199 (1 lot, Target) |

Unit check for the same five (section 7; engine price / file close ratio, R rescaled to engine points = R x ratio, unit-consistent rem): #1 ratio 1.1445, R 256.4, rem -76.4, skip; #2 ratio 1.1341, R 222.6, rem -1.3, skip; #3 ratio 1.1269, R 210.2, rem 36.1, skip; #4 ratio 1.1344, R 222.1, rem -4.5, skip; #5 ratio 1.1365, R 58.0, rem 190.7, keep. All five decisions are the same unit-consistent or not; what changes is how many borderline signals flip (not measured, see section 7).
Reproduce with: forecast row pred from /mnt/l2/l2vast/_londonrange/fc_lr.parquet (sess london, ld = Globex day), bars from min1_NQ.npz, skip log /mnt/l2/l2vast/_londonrange/skips/TL3_LR_JL2_LS1_MP.txt (columns: signal second, book, side, session key, F, R, T, k); example script /tmp copy: code/th_londonrange/lr_gap.py shows the matching. Check: the skip log lines for #1-#4 read "1789638900 P7 1 london 180.0 224.0 60.0 1.0", "1789473600 P7 1 london 221.3 196.2 60.0 1.0", "1781866860 P7 -1 london 246.3 186.5 60.0 1.0", "1791287041 P7 1 london 217.6 195.8 60.0 1.0".

## 5. Results on JN05W2JL2 (all six windows + FULL, drawdown first) - OLD-UNIT (range from the ratio-adjusted bar file)
Windows: L3M 2026-08..10, L6M 2026-05..10, HOLD 2025-11..2026-10, GAP 2025-07..10, PRE 2024-02..2025-06, X' 2023-04..2024-01 (rule inactive until 2023-09-01), FULL 43 months. Reference JN05W2JL2 max DD: L3M/L6M -22,565; HOLD -74,402; GAP -55,206; PRE -73,618; X' -34,877. Recent max DD is one week (2026-W44); the "W44 removed" column shows it.

**LS1_MP** (JL2 base, scope all)

| window | d mean $/wk base | x1.75 live | at $4.84 RT | max DD ref -> cell (cut) | d worst week | full stops/wk cell (ref) | best-5 weeks kept | winning weeks turned losing | DD cut with W44 removed |
|---|---|---|---|---|---|---|---|---|---|
| L3M | +1657 | +2899 | +1708 | -22565 -> -22508 (+0.2%) | +839 | 9.89 (10.27) | 91% | 0 | +0.0% |
| L6M | +895 | +1567 | +943 | -22565 -> -22508 (+0.2%) | +839 | 10.54 (10.88) | 102% | 0 | +0.0% |
| HOLD | +395 | +690 | +438 | -74402 -> -78185 (-5.1%) | -3540 | 10.36 (10.53) | 98% | 2 | -5.1% |
| GAP | +567 | +992 | +608 | -55206 -> -41653 (+24.5%) | +3138 | 8.88 (9.45) | 95% | 0 | - |
| PRE | +524 | +917 | +565 | -73618 -> -61535 (+16.4%) | +13241 | 8.71 (9.22) | 109% | 2 | - |
| X' | -189 | -331 | -172 | -34877 -> -34880 (-0.0%) | +0 | 9.97 (10.32) | 97% | 2 | - |
| FULL | +325 | +570 | +362 | -74402 -> -78185 (-5.1%) | +3138 | 9.48 (9.86) | 102% | 6 | -5.1% |

**LS1_MP London slice**

| window | d mean $/wk base | x1.75 live | at $4.84 RT | max DD ref -> cell (cut) | d worst week | full stops/wk cell (ref) | best-5 weeks kept | winning weeks turned losing | DD cut with W44 removed |
|---|---|---|---|---|---|---|---|---|---|
| L3M | +2692 | +4711 | +2744 | -64234 -> -47311 (+26.3%) | +6303 | 2.05 (2.59) | 98% | 0 | +26.3% |
| L6M | +1339 | +2344 | +1391 | -64234 -> -47311 (+26.3%) | +6303 | 2.28 (2.78) | 91% | 2 | +26.3% |
| HOLD | +905 | +1584 | +955 | -64234 -> -47311 (+26.3%) | +6303 | 2.34 (2.72) | 97% | 3 | +26.3% |
| GAP | +612 | +1072 | +659 | -30893 -> -21523 (+30.3%) | +1037 | 1.59 (2.22) | 65% | 1 | - |
| PRE | +428 | +748 | +478 | -97162 -> -77142 (+20.6%) | +1327 | 2.36 (3.11) | 69% | 5 | - |
| X' | -199 | -348 | -181 | -40008 -> -40008 (+0.0%) | +1350 | 1.99 (2.36) | 69% | 2 | - |
| FULL | +432 | +755 | +474 | -101006 -> -82052 (+18.8%) | +1327 | 2.20 (2.74) | 88% | 11 | +18.8% |

**LS125_MP** (JL2 base, scope all)

| window | d mean $/wk base | x1.75 live | at $4.84 RT | max DD ref -> cell (cut) | d worst week | full stops/wk cell (ref) | best-5 weeks kept | winning weeks turned losing | DD cut with W44 removed |
|---|---|---|---|---|---|---|---|---|---|
| L3M | +2205 | +3859 | +2247 | -22565 -> -22508 (+0.2%) | +839 | 9.97 (10.27) | 96% | 0 | +0.0% |
| L6M | +1200 | +2100 | +1240 | -22565 -> -22508 (+0.2%) | +839 | 10.58 (10.88) | 99% | 0 | +0.0% |
| HOLD | +555 | +971 | +593 | -74402 -> -80811 (-8.6%) | -6166 | 10.36 (10.53) | 96% | 2 | -8.6% |
| GAP | +220 | +385 | +255 | -55206 -> -48734 (+11.7%) | +1787 | 9.05 (9.45) | 98% | 0 | - |
| PRE | +863 | +1510 | +896 | -73618 -> -61196 (+16.9%) | +12313 | 8.84 (9.22) | 108% | 1 | - |
| X' | -82 | -143 | -66 | -34877 -> -35229 (-1.0%) | +0 | 10.02 (10.32) | 99% | 2 | - |
| FULL | +496 | +868 | +527 | -74402 -> -80811 (-8.6%) | +1787 | 9.56 (9.86) | 99% | 5 | -8.6% |

**LS125_MP London slice**

| window | d mean $/wk base | x1.75 live | at $4.84 RT | max DD ref -> cell (cut) | d worst week | full stops/wk cell (ref) | best-5 weeks kept | winning weeks turned losing | DD cut with W44 removed |
|---|---|---|---|---|---|---|---|---|---|
| L3M | +2467 | +4317 | +2512 | -64234 -> -44988 (+30.0%) | +7501 | 2.13 (2.59) | 91% | 0 | +30.0% |
| L6M | +1274 | +2230 | +1320 | -64234 -> -44988 (+30.0%) | +7501 | 2.32 (2.78) | 83% | 2 | +30.0% |
| HOLD | +878 | +1537 | +921 | -64234 -> -44988 (+30.0%) | +7501 | 2.38 (2.72) | 91% | 3 | +30.0% |
| GAP | +443 | +774 | +483 | -30893 -> -20324 (+34.2%) | -2409 | 1.76 (2.22) | 69% | 1 | - |
| PRE | +749 | +1311 | +791 | -97162 -> -62116 (+36.1%) | +1327 | 2.52 (3.11) | 74% | 3 | - |
| X' | -120 | -209 | -103 | -40008 -> -40008 (+0.0%) | +1350 | 2.06 (2.36) | 74% | 1 | - |
| FULL | +553 | +968 | +589 | -101006 -> -71213 (+29.5%) | +1327 | 2.30 (2.74) | 86% | 8 | +29.5% |

**Matched random controls (M7+P7 London only, JL2 base), scope all: d mean $/wk / DD cut %**

| window | LS1_MP | RKMP68 seed1 | seed2 | seed3 | LS125_MP | RKMP72 seed1 | seed2 | seed3 |
|---|---|---|---|---|---|---|---|---|
| L3M | +1657 / +0.2% | -1567 / -2.1% | -2759 / -24.0% | -1326 / -14.9% |  | +2205 / +0.2% | -1813 / -2.1% | -3025 / -24.0% | -1234 / -14.9% |
| L6M | +895 / +0.2% | -1541 / -2.1% | -2230 / -24.0% | -577 / -14.9% |  | +1200 / +0.2% | -1836 / -2.1% | -2290 / -24.0% | -361 / -14.9% |
| HOLD | +395 / -5.1% | -300 / +6.2% | -1097 / -3.7% | +299 / +8.3% |  | +555 / -8.6% | -524 / +10.2% | -1117 / +2.6% | n/a |
| GAP | +567 / +24.5% | +649 / +0.6% | +945 / +7.0% | +343 / +6.1% |  | +220 / +11.7% | +793 / +2.6% | +832 / -0.2% | +283 / +6.1% |
| PRE | +524 / +16.4% | +228 / -4.9% | -16 / -2.4% | +488 / -1.1% |  | +863 / +16.9% | +181 / -3.1% | +93 / -0.5% | +478 / -9.0% |
| X' | -189 / -0.0% | -137 / -9.2% | +123 / +0.0% | -43 / +0.0% |  | -82 / -1.0% | -212 / -9.2% | +201 / +0.0% | -22 / +0.0% |
| FULL | +325 / -5.1% | +35 / -3.8% | -195 / -3.7% | +298 / -0.1% |  | +496 / -8.6% | -50 / -2.0% | -150 / +0.5% | n/a |

Controls: random skips at the same keep share and scope (M7+P7 London, keep 0.68 for k=1, 0.72 for k=1.25; probability 0.32 / 0.28; 3 seeds). RKMP72 seed 3 has 42 of 43 months (HOLD row n/a). Reading: on mean the rule beats all three controls in L3M, L6M, HOLD (k=1: +395 vs -1097..+299), PRE (524 vs -16..+488, narrowly), but NOT in GAP (controls +343..+945 vs +567) or X' (controls -137..+123 vs -189). On DD cut the rule beats all three in L3M, L6M (the random skips make the recent DD 2-24% WORSE), GAP and PRE; it does NOT in HOLD (-5.1% vs controls -3.7..+8.3%).

Gate reading, k=1 (scope all): strict (every window DD cut >= 0, worst week not worse, mean >= 0): FAIL (HOLD DD -5.1% and worst week -3,540; X' mean -189). T-RECENTS tolerant (older DD <= 10% deeper, mean >= -5% of reference; recent clearly positive and beating placebos): PASS (X' mean -189 vs floor -202: margin 13 $/wk). k=1.25: strict FAIL (HOLD DD -8.6%, worst week -6,166; X' -82), tolerant PASS (HOLD DD -8.6% is close to the 10% edge).
OLD BASE (JN05W2, before the live-equivalent base; do not mix): LS1_MP L3M +1,936 / L6M +2,047 / HOLD +1,002 / GAP +433 $/wk (DD cut +0.2 / +0.2 / +17.2 / +21.2%); LS125_MP +2,027 / +2,149 / +1,097 / +240 (DD +0.2 / +0.2 / +12.3 / +12.0%); PRE/X' on the old base were never completed. On the old base the ALL-BOOKS version lost GAP (-2,343 / -1,839 $/wk) because it also skipped K7/U7 trend-continuation winners (+27.8k / +12.7k removed in GAP), the reason for the M7+P7-only gating.

### Winning JN05W2JL2 weeks turned losing (FULL, 43 months; date, JN05W2JL2 -> cell, entries the rule removed with their would-be P&L)

### LS1_MP

**FULL: 6 JN05W2 winning weeks turned losing** (of 128 winning weeks)

- week 2023-10-02/2023-10-08: JN05W2 +5308 -> cell -14097 (delta -19406); rule fired on 113 signals (M7, P7); ref trades removed: 10-02 04:28 P7 -1 lots 2: ref +2398; 10-02 05:02 M7 -1 lots 2: ref +2393; 10-02 05:04 M7 -1 lots 2: ref +2393; 10-02 06:10 M7 -1 lots 2: ref +2393; 10-02 06:30 P7 -1 lots 2: ref +2393; 10-03 05:40 M7 -1 lots 1: ref +1199; 10-03 07:44 P7 -1 lots 1: ref +1199; 10-03 08:16 M7 -1 lots 2: ref -1409; 10-04 02:40 M7 -1 lots 2: ref -1734; 10-04 03:28 P7 +1 lots 1: ref +1199; 10-04 04:09 M7 +1 lots 1: ref +1199; 10-04 06:25 M7 +1 lots 1: ref +1199; 10-04 07:39 P7 +1 lots 1: ref +1199; 10-04 08:16 M7 +1 lots 1: ref -697; 10-06 07:56 P7 -1 lots 1: ref +1199
- week 2023-11-27/2023-12-03: JN05W2 +151 -> cell -2909 (delta -3059); rule fired on 52 signals (M7, P7); ref trades removed: 11-27 07:01 P7 +1 lots 1: ref -622; 11-27 08:18 M7 +1 lots 1: ref +1199; 11-28 04:42 M7 +1 lots 1: ref -771; 11-29 04:47 M7 +1 lots 1: ref +1199; 11-29 04:47 P7 +1 lots 1: ref +1199
- week 2024-12-09/2024-12-15: JN05W2 +2552 -> cell -1505 (delta -4057); rule fired on 90 signals (M7, P7); ref trades removed: 12-09 04:34 M7 -1 lots 1: ref +1199; 12-09 04:36 M7 -1 lots 1: ref +1199; 12-09 06:43 P7 -1 lots 1: ref -627; 12-09 06:53 M7 -1 lots 1: ref -662; 12-09 08:11 P7 -1 lots 1: ref -685; 12-10 05:43 P7 +1 lots 2: ref +2403; 12-10 06:56 M7 +1 lots 1: ref +1199; 12-11 07:05 M7 -1 lots 1: ref -1172; 12-13 06:21 M7 +1 lots 2: ref +2403
- week 2025-05-26/2025-06-01: JN05W2 +7406 -> cell -1122 (delta -8527); rule fired on 65 signals (M7, P7); ref trades removed: 05-27 04:10 M7 +1 lots 1: ref -1221; 05-27 04:11 P7 +1 lots 1: ref -632; 05-27 05:37 P7 +1 lots 1: ref -665; 05-27 07:12 P7 -1 lots 1: ref +1199; 05-27 08:14 M7 -1 lots 2: ref +2398; 05-28 07:33 M7 +1 lots 2: ref +2403; 05-28 07:58 P7 +1 lots 2: ref +2398; 05-29 04:07 P7 +1 lots 2: ref -1274; 05-29 04:47 P7 -1 lots 1: ref -660; 05-29 06:05 M7 -1 lots 2: ref +2398; 05-29 07:47 M7 -1 lots 1: ref +1199; 05-29 07:49 M7 -1 lots 1: ref +1199; 05-29 07:49 P7 -1 lots 1: ref +1199; 05-30 08:11 M7 -1 lots 1: ref +1199; 05-30 08:23 M7 -1 lots 1: ref -852
- week 2025-11-17/2025-11-23: JN05W2 +3794 -> cell -2189 (delta -5983); rule fired on 70 signals (M7, P7); ref trades removed: 11-17 07:21 M7 -1 lots 1: ref +1199; 11-17 08:20 M7 -1 lots 1: ref +1199; 11-18 03:59 M7 +1 lots 1: ref -697; 11-18 04:54 M7 +1 lots 1: ref -647; 11-20 05:15 P7 -1 lots 1: ref -637; 11-20 06:06 M7 -1 lots 1: ref -767; 11-20 06:33 P7 +1 lots 2: ref +2403; 11-20 07:54 M7 +1 lots 1: ref +1199; 11-20 08:13 P7 +1 lots 1: ref -662; 11-21 07:11 M7 -1 lots 1: ref +1199; 11-21 07:29 M7 -1 lots 1: ref -1361; 11-21 07:38 M7 +1 lots 1: ref -682; 11-21 07:44 M7 +1 lots 1: ref +1199; 11-21 08:21 M7 +1 lots 1: ref -852
- week 2025-12-15/2025-12-21: JN05W2 +215 -> cell -1741 (delta -1956); rule fired on 51 signals (M7, P7); ref trades removed: 12-15 06:28 M7 +1 lots 1: ref +1199; 12-16 04:26 M7 +1 lots 1: ref -670; 12-16 04:34 P7 +1 lots 1: ref -620; 12-16 05:18 M7 +1 lots 1: ref +1199; 12-16 05:38 P7 +1 lots 1: ref +1199; 12-16 07:33 M7 +1 lots 2: ref -1324; 12-16 07:34 P7 +1 lots 2: ref -1424; 12-18 05:32 P7 +1 lots 1: ref +1199; 12-18 07:21 M7 +1 lots 1: ref +1199

### LS125_MP

**FULL: 5 JN05W2 winning weeks turned losing** (of 128 winning weeks)

- week 2023-10-02/2023-10-08: JN05W2 +5308 -> cell -9354 (delta -14662); rule fired on 90 signals (M7, P7); ref trades removed: 10-02 04:28 P7 -1 lots 2: ref +2398; 10-02 05:02 M7 -1 lots 2: ref +2393; 10-02 05:04 M7 -1 lots 2: ref +2393; 10-02 06:10 M7 -1 lots 2: ref +2393; 10-02 06:30 P7 -1 lots 2: ref +2393; 10-03 05:40 M7 -1 lots 1: ref +1199; 10-03 07:44 P7 -1 lots 1: ref +1199; 10-03 08:16 M7 -1 lots 2: ref -1409; 10-04 04:09 M7 +1 lots 1: ref +1199; 10-04 06:25 M7 +1 lots 1: ref +1199; 10-04 07:39 P7 +1 lots 1: ref +1199; 10-04 08:16 M7 +1 lots 1: ref -697; 10-06 07:56 P7 -1 lots 1: ref +1199
- week 2023-11-27/2023-12-03: JN05W2 +151 -> cell -2909 (delta -3059); rule fired on 52 signals (M7, P7); ref trades removed: 11-27 07:01 P7 +1 lots 1: ref -622; 11-27 08:18 M7 +1 lots 1: ref +1199; 11-28 04:42 M7 +1 lots 1: ref -771; 11-29 04:47 M7 +1 lots 1: ref +1199; 11-29 04:47 P7 +1 lots 1: ref +1199
- week 2024-06-03/2024-06-09: JN05W2 +5480 -> cell -161 (delta -5641); rule fired on 59 signals (M7, P7); ref trades removed: 06-03 08:10 P7 +1 lots 1: ref +1199; 06-03 08:14 M7 +1 lots 1: ref +1199; 06-04 02:56 P7 -1 lots 1: ref -615; 06-04 03:29 M7 -1 lots 2: ref -1404; 06-04 04:05 M7 -1 lots 1: ref +1199; 06-04 05:14 M7 -1 lots 1: ref -737; 06-04 05:16 M7 -1 lots 1: ref -737; 06-05 06:35 P7 +1 lots 4: ref +4800
- week 2025-11-17/2025-11-23: JN05W2 +3794 -> cell -991 (delta -4784); rule fired on 61 signals (M7, P7); ref trades removed: 11-17 08:20 M7 -1 lots 1: ref +1199; 11-18 03:59 M7 +1 lots 1: ref -697; 11-18 04:54 M7 +1 lots 1: ref -647; 11-20 05:15 P7 -1 lots 1: ref -637; 11-20 06:06 M7 -1 lots 1: ref -767; 11-20 06:33 P7 +1 lots 2: ref +2403; 11-20 07:54 M7 +1 lots 1: ref +1199; 11-20 08:13 P7 +1 lots 1: ref -662; 11-21 07:11 M7 -1 lots 1: ref +1199; 11-21 07:29 M7 -1 lots 1: ref -1361; 11-21 07:38 M7 +1 lots 1: ref -682; 11-21 07:44 M7 +1 lots 1: ref +1199; 11-21 08:21 M7 +1 lots 1: ref -852
- week 2025-12-15/2025-12-21: JN05W2 +215 -> cell -542 (delta -757); rule fired on 36 signals (M7, P7); ref trades removed: 12-15 06:28 M7 +1 lots 1: ref +1199; 12-16 04:26 M7 +1 lots 1: ref -670; 12-16 04:34 P7 +1 lots 1: ref -620; 12-16 05:18 M7 +1 lots 1: ref +1199; 12-16 05:38 P7 +1 lots 1: ref +1199; 12-16 07:33 M7 +1 lots 2: ref -1324; 12-16 07:34 P7 +1 lots 2: ref -1424; 12-18 07:21 M7 +1 lots 1: ref +1199

## 6. Recommendation as scored in OLD-UNIT: k = 1 (LS1_MP) - SUPERSEDED by section 10 (true points)
Reasons (drawdown first): (1) k=1 has the larger drawdown benefit where there is one: GAP +24.5% vs +11.7%, PRE +16.4% vs +16.9% (equal), and a smaller damage in HOLD (-5.1% vs -8.6%) and FULL (-5.1% vs -8.6%); worst week better in GAP/PRE for both, HOLD worse for both (-3,540 vs -6,166). (2) Recent windows are identical in DD (+0.2%), k=1.25 has the larger mean (L3M +2,205 vs +1,657, L6M +1,200 vs +895, HOLD +555 vs +395, PRE +863 vs +524, FULL +496 vs +325) but loses more in HOLD DD and gains less in GAP (+220 vs +567 mean). (3) Both beat the matched random controls on recent mean and recent DD; neither beats them in GAP/X' mean. (4) The more conservative threshold (skip fewer, k=1.25) trades drawdown for mean; since the headline need is drawdown and the HOLD window is the one with the 74k drawdown, k=1. **Plainly: the rule is a recent-mean gain with a mixed drawdown record; it does NOT reduce the HOLD drawdown (it adds 3.8k at k=1). Do not build it as a drawdown tool.** If built: Off / Shadow first, M7+P7, London, k=1, log every skipped signal.

## 7. Fidelity gap found while writing this (resolved in section 10: re-scored, result changes k)
The 1-minute file the hook uses for R (min1_NQ.npz) is a ratio-adjusted series: engine price / file close = 1.03 (2023-04) rising to 1.14 (2026-10). F is built from the ENGINE price (true points) while R comes from the file (range in file points, understated by 3-14%). The rule as scored therefore under-counts the range used by about the ratio (e.g. 11-14% in 2026), i.e. it skips a little LESS than a unit-consistent rule at the same k; a live D7 rule works in true points. pred (a ln-ratio) is unaffected. The unit-consistent re-score cells TL3_LR_JL2_LS1_MPUC and TL3_LR_JL2_LS125_MPUC (hook flag uc=1: R rescaled by engine price / file close at the signal minute) were run afterwards (LR quota 2); results in section 10. Until they run, k=1 as scored corresponds to roughly k = 0.88-0.97 in true points; the live threshold may need to be re-tuned. In the five examples above all decisions are identical either way.

## 8. Live computability line
D7 already holds everything needed: (a) 1-minute NQ bars (highs, lows, closes, true engine prices) for the running session range and the last complete close; (b) its own daily bars history to form y (London 02:00-08:30 ET ln range), RTH (09:30-16:00 ET ln range) and their 5/14/20-day means; (c) the forecast needs only a 6-number coefficient table plus intercept (tables in section 2), refreshed every 10 trading days from the same data (or frozen and re-fitted by the box and pasted in), no UW, CME or box-only feed; (d) the per-signal test is two subtractions and one comparison against the 60-point target. The box-only parts are the refit job and the coefficient file; the live gap to close is the unit/scale question in section 7 (live bars are true-price, so R is in true points automatically).

## 9. What is missing / late (stated plainly)
- Unit-consistent re-score: run for L3M, L6M, HOLD, GAP (section 10); PRE and X' rows as marked there; true-unit k = 1.5 and 2 NOT run.
- The intraday own-bar forecast (OS cells) and the HAR variant were not used for this spec; their JL2 numbers do not exist.
- Strict gate fails and HOLD/GAP matched-control reads are as stated; the random controls are 3 seeds (placebo shifts 11/23/37 days exist only on the old base).
- Numbers produced from the existing finished runs only (no engine time used for this document).

## 10. UNIT-CONSISTENT RE-SCORE (range used rescaled to TRUE engine-price points) - corrected numbers, JN05W2JL2 base

**Which numbers are which.** Sections 1-6 and 8 were scored with range-so-far measured in the ratio-adjusted bar-file points (OLD-UNIT, 3-14% too small against the engine-price forecast). THIS section is UNIT-CONSISTENT: R(true) = R(file) x (engine price / file close at the signal minute), the unit a live D7 will measure in, since live bars are true prices. Cells TL3_LR_JL2_LS1_MPUC (k=1) and TL3_LR_JL2_LS125_MPUC (k=1.25); identity cell TL3_LR_JL2_UCID (rule path active, rescale on, never fires) on 202610 = JN05W2JL2: 642 trades, net 27,487.58 = 642, 27,487.58 IDENTICAL. Everything else (forecast, M7+P7, London, 60-point target, tests) is unchanged.

**LS1_MPUC (k = 1, true points), scope all**

| window | d mean $/wk base | x1.75 live | at $4.84 RT | max DD ref -> cell (cut) | d worst week | full stops/wk cell (ref) | best-5 weeks kept | winning weeks turned losing | DD cut with W44 removed |
|---|---|---|---|---|---|---|---|---|---|
| L3M | -161 | -281 | -102 | -22565 -> -25189 (-11.6%) | -6017 | 9.89 (10.27) | 88% | 0 | -11.9% |
| L6M | -195 | -342 | -138 | -22565 -> -25189 (-11.6%) | -6017 | 10.50 (10.88) | 102% | 0 | -11.9% |
| HOLD | -375 | -656 | -321 | -74402 -> -72184 (+3.0%) | -2113 | 10.34 (10.53) | 97% | 1 | +3.0% |
| GAP | +619 | +1083 | +661 | -55206 -> -40984 (+25.8%) | +3807 | 8.88 (9.45) | 95% | 0 | - |
| PRE | not run / not complete when this was written | | | | | | | | |
| X' | not run / not complete when this was written | | | | | | | | |

**LS125_MPUC (k = 1.25, true points), scope all**

| window | d mean $/wk base | x1.75 live | at $4.84 RT | max DD ref -> cell (cut) | d worst week | full stops/wk cell (ref) | best-5 weeks kept | winning weeks turned losing | DD cut with W44 removed |
|---|---|---|---|---|---|---|---|---|---|
| L3M | +895 | +1566 | +949 | -22565 -> -22508 (+0.2%) | +839 | 9.89 (10.27) | 91% | 0 | +0.0% |
| L6M | +408 | +714 | +459 | -22565 -> -22508 (+0.2%) | +839 | 10.46 (10.88) | 102% | 0 | +0.0% |
| HOLD | +174 | +305 | +221 | -74402 -> -73823 (+0.8%) | -3540 | 10.32 (10.53) | 99% | 1 | +0.8% |
| GAP | +641 | +1121 | +680 | -55206 -> -43490 (+21.2%) | +3138 | 8.93 (9.45) | 96% | 0 | - |
| PRE | not run / not complete when this was written | | | | | | | | |
| X' | not run / not complete when this was written | | | | | | | | |

**Side by side (scope all, d mean $/wk base / DD cut; OLD-UNIT as scored vs UNIT-CONSISTENT)**

| window | k=1 OLD-UNIT | k=1 UNIT-CONSISTENT | k=1.25 OLD-UNIT | k=1.25 UNIT-CONSISTENT |
|---|---|---|---|---|
| L3M | +1657 / +0.2% | -161 / -11.6% | +2205 / +0.2% | +895 / +0.2% |
| L6M | +895 / +0.2% | -195 / -11.6% | +1200 / +0.2% | +408 / +0.2% |
| HOLD | +395 / -5.1% | -375 / +3.0% | +555 / -8.6% | +174 / +0.8% |
| GAP | +567 / +24.5% | +619 / +25.8% | +220 / +11.7% | +641 / +21.2% |
| PRE | +524 / +16.4% | n/a | +863 / +16.9% | n/a |
| X' | -189 / -0.0% | n/a | -82 / -1.0% | n/a |

M7+P7 London trade keep share (cell / JN05W2JL2): k=1 OLD-UNIT L6M 0.674, HOLD 0.650; k=1 UNIT-CONSISTENT 0.597 / 0.561; k=1.25 OLD-UNIT 0.717 / 0.697; k=1.25 UNIT-CONSISTENT 0.649 / 0.622.

**What changed (plain).** In true engine points the rule skips MORE at the same k (the file range was understated, so the old-unit rule skipped less than its k says). At k=1 the recent gain disappears (L3M -161, L6M -195 $/wk) and the recent max DD gets 11.6% deeper; the old-unit k=1 result (+1,657 / +895) was a rule that skips about as many M7+P7 London signals as a true-unit k of roughly 1.4-1.5 would (keep share 0.67 vs 0.60 at true k=1 and 0.65 at true k=1.25): **in true points the threshold must be larger, not k=1.** Unit-consistent k=1.25 keeps a smaller gain: +895 / +408 / +174 $/wk in L3M / L6M / HOLD (x1.75 live +1,566 / +714 / +305), DD cut +0.2 / +0.2 / +0.8% (flat), GAP +641 $/wk with +21.2% DD. It no longer has its matched random control (the RKMP controls were matched to the OLD-UNIT keep shares 0.68 / 0.72; the unit-consistent keep share is 0.65 / 0.62), so no placebo-beating claim can be made for the unit-consistent cells.

**Live threshold recommendation (provisional).** The live code MUST measure R in true engine points (live bars are true prices, so this is automatic) and compare with F = pred x last close in the same units. The scored evidence supports a true-unit k of at least 1.25 (not 1.0); k = 1.25 in true points is the smallest tested setting that is non-negative in all of L3M, L6M, HOLD and GAP, but its gain is small (+408 $/wk in L6M base) and not shown to beat a matched random skip. A true-unit k of 1.5 and 2 (closer to the old-unit k=1 skip share) are NOT run (engine quota); request: TL3_LR_JL2_LS15_MPUC and LS2_MPUC if the engine is available. Until they are run, Off / Shadow only; log every skipped signal with R(true), F, rem.

PRE / X' / GAP for the unit-consistent cells: shown above where complete; rows marked "not run / not complete" were not finished when this was written (LR quota until ~20:00Z; PRE/X' only if finished before 19:00Z).
