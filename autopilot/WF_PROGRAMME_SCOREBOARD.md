# WF programme scoreboard (W-SB, built 2026-11-27 04:33Z; feed /mnt/l2/l2vast/_wf/scoreboard_rows.jsonl)

## ANSWER FIRST

**NOTHING IS CALLED "WORKS".** Feed: 1718 lines read, 60 superseded M9 lines dropped (W-M9 supersedes_earlier_m9_lines), 90 further duplicate-key lines dropped, 0 unparseable; **1568 unique rows = 388 PRIMARY rows + 1180 REFERENCE rows**. Primaries tried K = 388 (methods x sessions x subjects x steps, as counted in the feed; DYNEXIT families counted as separate methods). Bonferroni: p_adj = min(1, plain p x 388).

- PRIMARY PASS rows: **26 of 388**; reference PASS rows: 86 of 1180. The pass rule is one-sided and loose (8/12 or 2/3 of periods) so ~15-30% of random rows pass by chance; 388 primaries at p~0.05 would give ~19 nominal hits with no effect.
- Smallest plain p among PRIMARY PASS rows: 5.8e-05 (M7 LO S2 step 4, post-hoc); after Bonferroni x388: 0.02.
- Primary rows with Bonferroni-adjusted p <= 0.05 (any verdict): **18**; smallest adjusted p over all primaries = <1e-12. **READ THIS CAREFULLY: 16 of these 18 are FAIL rows with income down 20-65%: the plain p is a sign test on drawdown-shallower only, and cutting size or dropping trades makes DD shallower by construction, so a tiny p there is not evidence of skill (the income clause of the PASS rule is what fails them).**
- Read: the PASSes are post-hoc approximations or quick screens, many on S2 (in-sample qualifiers), many at the 13-week step with 12 periods, and where a random-skip / random-factor null was reported the null often does as well. Candidates for the forward register at most; see "What has passed anything".
- M12 (bracket by UW range forecast): NO rows in the feed and no WF_M12.md page at build time. DYNEXIT X24 (steering) has a page (DYNEXIT_X24.md) but no feed rows; X10/X11/X13/X20..X23 rows are minimal or absent. They are not in the counts above.

### Headline table: per method (deduplicated)

| method | primary rows | primary PASS | ref rows | ref PASS | min plain p (primary) | min p_adj | PASS primary: S1 / S2 | exact basis rows |
|---|---|---|---|---|---|---|---|---|
| M1 | 32 | 2 | 64 | 5 | 0.345 | 1.000 | 1 / 1 | 0 |
| M2 | 30 | 3 | 90 | 7 | <1e-12 | <1e-12 | 0 / 3 | 0 |
| M3 | 30 | 3 | 90 | 7 | 0.001 | 0.543 | 1 / 2 | 0 |
| M4 | 24 | 0 | 144 | 5 | <1e-12 | <1e-12 | 0 / 0 | 0 |
| M5 | 12 | 1 | 60 | 3 | <1e-12 | <1e-12 | 1 / 0 | 0 |
| M6 | 12 | 3 | 48 | 1 | 3.0e-04 | 0.116 | 3 / 0 | 0 |
| M7 | 24 | 3 | 120 | 12 | 5.8e-05 | 0.023 | 0 / 3 | 0 |
| M8 | 24 | 5 | 96 | 17 | 7.0e-07 | 2.7e-04 | 2 / 3 | 0 |
| M9 | 30 | 3 | 30 | 7 | 0.003 | 1.000 | 0 / 3 | 0 |
| M10 | 32 | 0 | 128 | 0 | 0.245 | 1.000 | 0 / 0 | 0 |
| M11 | 30 | 3 | 120 | 18 | 0.085 | 1.000 | 2 / 1 | 0 |
| DYNEXIT | 15 | 0 | 75 | 3 | 0.002 | 0.663 | 0 / 0 | 0 |
| DYNEXIT_X12 | 15 | 0 | 0 | 0 | - | - | 0 / 0 | 0 |
| DYNEXIT_X12X18 | 15 | 0 | 45 | 0 | - | - | 0 / 0 | 0 |
| DYNEXIT_X14_X19 | 12 | 0 | 36 | 1 | - | - | 0 / 0 | 0 |
| DYNEXIT_X15 | 0 | 0 | 1 | 0 | - | - | 0 / 0 | 0 |
| DYNEXIT_X16 | 15 | 0 | 0 | 0 | - | - | 0 / 0 | 0 |
| DYNEXIT_X17 | 15 | 0 | 0 | 0 | - | - | 0 / 0 | 0 |
| DYNEXIT_X18 | 15 | 0 | 0 | 0 | - | - | 0 / 0 | 0 |
| DYNEXIT_X20 | 0 | 0 | 1 | 0 | - | - | 0 / 0 | 0 |
| DYNEXIT_X21 | 0 | 0 | 1 | 0 | - | - | 0 / 0 | 0 |
| DYNEXIT_X22 | 0 | 0 | 1 | 0 | - | - | 0 / 0 | 0 |
| DYNEXIT_X8 | 6 | 0 | 30 | 0 | 0.019 | 1.000 | 0 / 0 | 0 |

### Primary rows by step and verdict (all methods)

| step (weeks) | primary rows | PASS | FAIL |
|---|---|---|---|
| 1 | 16 | 0 | 16 |
| 2 | 124 | 3 | 121 |
| 4 | 124 | 11 | 113 |
| 13 | 124 | 12 | 112 |

basis: post-hoc=807, quick=761. No row is exact-engine on the full programme (live-layer re-run) : the exact basis in this feed is the exact per-trade TRADES re-weighted post-hoc.

## RUNNING COUNT of everything tried since Test 1 (order of magnitude; ESTIMATES unless marked FEED)

| block | count | label |
|---|---|---|
| WF programme M1-M11 rows in feed | 1270 unique rows (280 primaries) | FEED, exact count |
| DYNEXIT families rows in feed | 298 unique rows (108 primaries) | FEED, exact count |
| DYNEXIT recipes evaluated (X1-X6,X9 menu 287/book; X12/X16/X17/X18 407 recipes x 17 books = 6,900; X14/X19 315 real + 315 random-trigger recipes; X8 220; X23 ~4,700 recipe-books; X15/X21/X22 ~126; PLAN_NY 3,654 + 1,188 variants) | ~2 x 10^4 recipe-book evaluations (range 10^4 - 5 x 10^4) | ESTIMATE from MORNING.md notes 03:07-04:31Z 11-27; agents count differently (recipes vs recipe-books), not summed exactly |
| TRIALS_LEDGER.csv (autopilot; families through 2026-10-31 data end), sum of N_used_default | ~2.7 x 10^6 of which RB1_RAW 2.5 x 10^6 (replay cells, overlapping RB1 142k); without RB1_RAW ~2 x 10^5 | ESTIMATE; ledger counts come from directory names/pages, +-10-15%; across-family multiplicity not counted; 67 families |
| Engine set-months run (all Q-jobs, grids, ladder R0-R5, Tests 5-12) | order 10^6 (queues of 10^4-6 x 10^4 rows each; DYNEXIT_WF_EXACT 62k rows alone) | ESTIMATE, rough |
| Quick-screen cells (Test 5/6/8 grids, bar swaps, S1R columns 63,626 x refits, WF_M9 4,092 cells) | order 10^6 - 10^7 | ESTIMATE |
| Tests 1-12 (named programmes), Q5-Q14 and ~60 T-* / BASIC / FLAT programmes in MEMORY.md | ~70 named programmes; ~100-200 pages | ESTIMATE from memory index |
| WF primaries with the 2/4/13 steps (this scoreboard) | 388 | FEED |

All of this was tried on the same ~42 months (2023-04..2026-10, Nov 2025 excluded) that selected the live books; any best-of correction should be applied against 10^5 or more trials, not 388. The Bonferroni columns below use only the 388 programme primaries and are therefore LENIENT.

## What has passed anything (honest read)

- **M1**: 2 primary PASS of 32; steps {4: 2}; subjects {'S1': 1, 'S2': 1}; basis {'post-hoc': 1, 'quick': 1}.
- **M11**: 3 primary PASS of 30; steps {2: 1, 4: 2}; subjects {'S1': 2, 'S2': 1}; basis {'post-hoc': 2, 'quick': 1}.
- **M2**: 3 primary PASS of 30; steps {4: 2, 13: 1}; subjects {'S2': 3}; basis {'quick': 3}.
- **M3**: 3 primary PASS of 30; steps {13: 3}; subjects {'S1': 1, 'S2': 2}; basis {'post-hoc': 1, 'quick': 2}.
- **M5**: 1 primary PASS of 12; steps {4: 1}; subjects {'S1': 1}; basis {'post-hoc': 1}.
- **M6**: 3 primary PASS of 12; steps {4: 1, 13: 2}; subjects {'S1': 3}; basis {'post-hoc': 3}.
- **M7**: 3 primary PASS of 24; steps {13: 2, 4: 1}; subjects {'S2': 3}; basis {'post-hoc': 3}.
- **M8**: 5 primary PASS of 24; steps {13: 1, 2: 2, 4: 2}; subjects {'S1': 2, 'S2': 3}; basis {'post-hoc': 5}.
- **M9**: 3 primary PASS of 30; steps {13: 3}; subjects {'S2': 3}; basis {'quick': 3}.

Overall: (a) most PASS rows are S2 (the qualifier baskets were picked in-sample on the same weeks) or post-hoc size/filter methods (M2/M3/M5/M7/M8/M11) where the drawdown gain comes from taking less risk; several PASS rows carry a mean income change far below -10% (S2 quick baskets with near-zero baselines make the mean % unstable; the sign-test period counts, not the mean %, decided the verdict). (b) 13-week-step rows have 12 periods, so 8-of-12 shallower is cheap, and the M2/M3/M9 PASS rows are mostly 13-week S2. (c) Where a random-skip / random-factor null is in the notes (M5, M6, M7, M8, M11) read it beside the PASS (printed per row under flags). (d) Strongest-looking single group: M9 (bracket scaled to range) S2 at the 13-week step, LO/NY/NP: chained OOS DD about 40-70% shallower AND income up, but the quick-screen S2 baskets, 12 periods, 2- and 4-week steps do not carry it, the lots-only reference (size without bracket scaling) also PASSes at NY and NP (so part is size, not bracket), and the pessimistic fill re-score is not run. (e) No exit family (DYNEXIT X8, X12, X14/X19, X16-X18, X1-X6/X9 menu) has a PRIMARY PASS row; the random-timing nulls reach the same pick-rule PASS flags in 35-100% of null families (see DYNEXIT_*.md pages). DYNEXIT_X24 trail steering survives its random-steering null (30 draws) but fails walk-forward and gains only ~1-2.5% DD (page only). Verdict: **no method qualifies as "works"; PASS rows are candidates for the forward register at most, none has been pessimistic-fill re-scored, and nothing here is live-actionable.**

## Every PASS PRIMARY row with distrust flags (26)

cols: method | sess | subj | step | basis | per. shallower / good / income-higher of n | dDD mean (feed convention; + read as shallower) | income % | chained DD untreated -> treated | plain p | p_adj | flags

| method | sess | subj | step | basis | shallower/good/inc-higher of n | dDD mean | inc % | chained DD U -> T | p | p_adj | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M1 | NY | S1 | 4 | post-hoc | 26/26/13 of 39 | 7,841 | -8.5 | 200,647 -> 175,216 | 0.670 | 1.000 | post-hoc approx (account layers not re-run); short-period DD is noisy; plain p 0.670 > 0.05; p after Bonferroni x388 = 1.00; null: plain_p = permutation null (decision-block scales shuffled across blocks, 200 draws) share with >= observed fraction of better periods; pessimistic re-score not run |
| M1 | NY | S2 | 4 | quick | 27/28/15 of 39 | 162 | 0.6 | 22,269 -> 19,996 | 0.505 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; plain p 0.505 > 0.05; p after Bonferroni x388 = 1.00; null: plain_p = permutation null (decision-block scales shuffled across blocks, 200 draws) share with >= observed fraction of better periods; pessimistic re-score not run |
| M11 | AS | S1 | 2 | post-hoc | 23/27/14 of 32 | 5,693 | -2.6 | 57,585 -> 33,017 | 0.095 | 1.000 | post-hoc approx (account layers not re-run); short-period DD is noisy; plain p 0.095 > 0.05; p after Bonferroni x388 = 1.00; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 | AS | S1 | 4 | post-hoc | 12/15/9 of 16 | 7,807 | 0.2 | 57,585 -> 39,625 | 0.085 | 1.000 | post-hoc approx (account layers not re-run); short-period DD is noisy; plain p 0.085 > 0.05; p after Bonferroni x388 = 1.00; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 | LO | S2 | 4 | quick | 9/11/9 of 16 | 261 | 61.4 | 9,093 -> 5,858 | 0.525 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; plain p 0.525 > 0.05; p after Bonferroni x388 = 1.00; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M2 | AS | S2 | 4 | quick | 24/26/17 of 39 | 654 | -9.5 | 42,499 -> 39,609 | 0.027 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M2 | LO | S2 | 4 | quick | 26/28/22 of 39 | 1,025 | -8.1 | 113,538 -> 82,972 | 0.005 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M2 | LO | S2 | 13 | quick | 9/9/8 of 12 | 3,265 | -90.4 | 80,703 -> 72,671 | 0.073 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); income -90% (below -10%); plain p 0.073 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M3 | AS | S2 | 13 | quick | 10/10/4 of 12 | 7,226 | -5.9 | 42,499 -> 42,513 | 0.019 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); chained OOS DD DEEPER (42,513 vs 42,499); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M3 | NY | S1 | 13 | post-hoc | 8/8/5 of 12 | 5,750 | -3.5 | 200,647 -> 280,211 | 0.194 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); chained OOS DD DEEPER (280,211 vs 200,647); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic: PASS |
| M3 | NY | S2 | 13 | quick | 8/8/7 of 12 | 11,905 | -1.6 | 133,613 -> 75,133 | 0.194 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M5 | NY | S1 | 4 | post-hoc | 27/27/18 of 39 | 4,186 | -4.3 | 200,647 -> 175,742 | 0.012 | 1.000 | post-hoc approx (account layers not re-run); short-period DD is noisy; p after Bonferroni x388 = 1.00; null: random-skip null (200 draws, same count per book): chained DD null mean -191468 vs -175742, p(null as good DD)=0; pessimistic re-score not run |
| M6 | AS | S1 | 4 | post-hoc | 27/27/21 of 39 | 2,135 | 7.8 | 67,941 -> 52,572 | 0.007 | 1.000 | post-hoc approx (account layers not re-run); short-period DD is noisy; p after Bonferroni x388 = 1.00; null: random-skip null (200 draws): chained DD null mean -71321 vs -52572, p(null DD as good)=0; pessimistic re-score not run |
| M6 | AS | S1 | 13 | post-hoc | 8/8/7 of 12 | 3,520 | 6.4 | 67,941 -> 52,572 | 0.194 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; null: random-skip null (200 draws): chained DD null mean -72967 vs -52572, p(null DD as good)=0; pessimistic re-score not run |
| M6 | NY | S1 | 13 | post-hoc | 9/9/4 of 12 | 9,960 | -5.6 | 200,647 -> 185,849 | 0.073 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); plain p 0.073 > 0.05; p after Bonferroni x388 = 1.00; null: random-skip null (200 draws): chained DD null mean -194877 vs -185849, p(null DD as good)=0; pessimistic re-score not run |
| M7 | AS | S2 | 13 | post-hoc | 8/8/8 of 11 | 932 | 18.1 | 15,347 -> 10,003 | 0.113 | 1.000 | S2=in-sample qualifiers; post-hoc approx; 13-week step, <=12 periods (8/12 is cheap); plain p 0.113 > 0.05; p after Bonferroni x388 = 1.00; null: null_p=1; pessimistic re-score not run |
| M7 | LO | S2 | 4 | post-hoc | 31/31/22 of 38 | 763 | -122.7 | 14,505 -> 13,710 | 5.8e-05 | 0.023 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -123% (below -10%); null: null_p=0; pessimistic re-score not run |
| M7 | LO | S2 | 13 | post-hoc | 10/10/8 of 11 | 998 | -113.7 | 14,464 -> 13,465 | 0.006 | 1.000 | S2=in-sample qualifiers; post-hoc approx; 13-week step, <=12 periods (8/12 is cheap); income -114% (below -10%); p after Bonferroni x388 = 1.00; null: null_p=0; pessimistic re-score not run |
| M8 | LO | S2 | 2 | post-hoc | 53/53/40 of 76 | 384 | -34.1 | 14,554 -> 11,938 | 3.8e-04 | 0.148 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -34% (below -10%); p after Bonferroni x388 = 0.15; null: null_p=0; pessimistic re-score not run |
| M8 | LO | S2 | 4 | post-hoc | 31/31/20 of 38 | 761 | -48.9 | 14,505 -> 12,470 | 5.8e-05 | 0.023 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -49% (below -10%); null: null_p=0; pessimistic re-score not run |
| M8 | NP | S1 | 2 | post-hoc | 52/52/41 of 77 | 2,304 | -8.2 | 134,363 -> 152,013 | 0.001 | 0.543 | post-hoc approx (account layers not re-run); short-period DD is noisy; chained OOS DD DEEPER (152,013 vs 134,363); p after Bonferroni x388 = 0.54; null: null_p=0; pessimistic re-score not run |
| M8 | NP | S2 | 4 | post-hoc | 26/26/22 of 38 | 250 | -5.8 | 22,890 -> 14,443 | 0.017 | 1.000 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; p after Bonferroni x388 = 1.00; null: null_p=1; pessimistic re-score not run |
| M8 | NY | S1 | 13 | post-hoc | 10/10/6 of 12 | 14,460 | -2.1 | 200,647 -> 200,578 | 0.019 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; null: null_p=0; pessimistic re-score not run |
| M9 | LO | S2 | 13 | quick | 11/11/9 of 12 | 1,093 | 138.2 | 13,010 -> 8,024 | 0.003 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M9 | NP | S2 | 13 | quick | 9/9/7 of 12 | 1,694 | 42.8 | 20,989 -> 6,774 | 0.073 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); plain p 0.073 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M9 | NY | S2 | 13 | quick | 8/8/7 of 12 | 1,599 | 73.4 | 21,104 -> 6,347 | 0.194 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |

## PASS REFERENCE rows (86; reference rows are not counted in K, listed compactly)

| method/version | sess | subj | step | basis | shallower/good/inc-higher of n | dDD mean | inc % | chained DD U -> T | p | p_adj | flags |
|---|---|---|---|---|---|---|---|---|---|---|---|
| DYNEXIT ref:REFPOOL_fixed_bracket_repick | LO | S1 | 2 | quick | 22/22/20 of 49 | 421 | 0.3 | - -> - | 0.612 | 1.000 | quick screen, not exact engine; short-period DD is noisy; plain p 0.612 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| DYNEXIT ref:REFPOOL_fixed_bracket_repick | NP | S1 | 2 | quick | 35/35/32 of 60 | 17 | 23.0 | - -> - | 0.046 | 1.000 | quick screen, not exact engine; short-period DD is noisy; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| DYNEXIT ref:X3D | NY | S1 | 13 | quick | 6/6/4 of 13 | -1,033 | 3.1 | - -> - | 0.709 | 1.000 | quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); plain p 0.709 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| DYNEXIT_X14_X19 ref:profit-side(P) | NP | S1q | 13 | quick | 8/8/6 of 12 | -10 | -9.5 | - -> - | - | - | S1q quick-screen on live books; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); no plain p reported; pessimistic re-score not run |
| M1 ref:n8 | AS | S1 | 4 | post-hoc | 25/26/13 of 39 | 1,903 | -7.9 | 67,941 -> 66,991 | - | - | post-hoc approx (account layers not re-run); short-period DD is noisy; no plain p reported; pessimistic re-score not run |
| M1 ref:n8 | LO | S2 | 4 | quick | 28/29/23 of 39 | 283 | 39.1 | 13,451 -> 10,618 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; no plain p reported; pessimistic re-score not run |
| M1 ref:n8 | NP | S1 | 4 | post-hoc | 26/26/12 of 39 | 4,219 | -9.2 | 134,363 -> 108,694 | - | - | post-hoc approx (account layers not re-run); short-period DD is noisy; no plain p reported; pessimistic re-score not run |
| M1 ref:n8 | NY | S2 | 4 | quick | 31/33/19 of 39 | 295 | -4.8 | 22,269 -> 19,047 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; no plain p reported; pessimistic re-score not run |
| M1 ref:n8 | NY | S2 | 13 | quick | 11/11/4 of 12 | 200 | -4.9 | 22,269 -> 20,898 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); no plain p reported; pessimistic re-score not run |
| M11 ref:bench | LO | S2 | 4 | quick | 10/11/7 of 16 | 310 | 47.4 | 9,093 -> 5,858 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:bench | NY | S2 | 4 | quick | 12/12/7 of 16 | 951 | 460.7 | 21,801 -> 12,714 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:daytype_brk | AS | S1 | 2 | post-hoc | 23/23/14 of 32 | 5,827 | -9.7 | 57,585 -> 36,923 | - | - | post-hoc approx (account layers not re-run); short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:daytype_brk | AS | S1 | 4 | post-hoc | 13/13/7 of 16 | 8,212 | -7.4 | 57,585 -> 36,923 | - | - | post-hoc approx (account layers not re-run); short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:daytype_brk | AS | S1 | 13 | post-hoc | 5/5/0 of 5 | 15,260 | -7.6 | 57,585 -> 36,923 | - | - | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:daytype_brk | AS | S2 | 13 | quick | 3/4/3 of 5 | 1,005 | 7.4 | 7,083 -> 4,417 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:daytype_fade | NP | S2 | 4 | quick | 13/13/9 of 16 | 1,096 | 1.8 | 22,405 -> 12,826 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:daytype_fade | NP | S2 | 13 | quick | 5/5/2 of 5 | 2,890 | 86.0 | 23,091 -> 13,838 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:quintile | ALL | S2 | 4 | quick | 11/13/9 of 16 | 1,468 | -5.1 | 34,285 -> 23,138 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:quintile | ALL | S2 | 13 | quick | 5/5/2 of 5 | 5,467 | 4.9 | 34,757 -> 16,126 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:quintile | LO | S2 | 4 | quick | 12/13/9 of 16 | 418 | 67.9 | 9,093 -> 4,430 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:quintile | LO | S2 | 13 | quick | 4/4/3 of 5 | 1,524 | 80.9 | 6,616 -> 2,929 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:quintile | NP | S2 | 13 | quick | 4/4/2 of 5 | 3,043 | 6.5 | 23,091 -> 11,688 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:quintile | NY | S2 | 4 | quick | 11/11/5 of 16 | 1,023 | 74.9 | 21,801 -> 10,901 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:quintile | NY | S2 | 13 | quick | 5/5/3 of 5 | 2,919 | 31.0 | 22,269 -> 11,134 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:skip_outside | AS | S1 | 2 | post-hoc | 22/25/14 of 32 | 10,703 | -5.1 | 57,585 -> 28,284 | - | - | post-hoc approx (account layers not re-run); short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:skip_outside | AS | S1 | 4 | post-hoc | 11/14/9 of 16 | 12,744 | 0.3 | 57,585 -> 39,625 | - | - | post-hoc approx (account layers not re-run); short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M11 ref:skip_outside | LO | S2 | 4 | quick | 9/11/9 of 16 | 522 | 122.8 | 9,093 -> 5,858 | - | - | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; no plain p reported; UW group picked on the full-sample page (in-sample); pessimistic re-score not run |
| M2 ref:continuous_lots | LO | S2 | 4 | quick | 26/28/22 of 39 | 1,077 | -11.0 | 113,538 -> 82,077 | 0.005 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; income -11% (below -10%); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M2 ref:continuous_lots | LO | S2 | 13 | quick | 8/8/9 of 12 | 3,264 | -113.1 | 80,703 -> 73,029 | 0.194 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); income -113% (below -10%); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M2 ref:win13 | AS | S1 | 4 | post-hoc | 26/26/19 of 39 | 1,689 | -9.5 | 67,941 -> 66,575 | 0.027 | 1.000 | post-hoc approx (account layers not re-run); short-period DD is noisy; p after Bonferroni x388 = 1.00; pessimistic: PASS |
| M2 ref:win52 | AS | S2 | 13 | quick | 12/12/6 of 12 | 1,369 | -5.1 | 42,499 -> 39,076 | 2.0e-04 | 0.078 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 0.08; pessimistic re-score not run |
| M2 ref:win52 | LO | S2 | 4 | quick | 27/29/26 of 39 | 1,352 | -41.4 | 113,538 -> 78,232 | 0.002 | 0.660 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; income -41% (below -10%); p after Bonferroni x388 = 0.66; pessimistic re-score not run |
| M2 ref:win52 | LO | S2 | 13 | quick | 12/12/8 of 12 | 4,144 | -46.7 | 80,703 -> 70,561 | 2.0e-04 | 0.078 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); income -47% (below -10%); p after Bonferroni x388 = 0.08; pessimistic re-score not run |
| M2 ref:win52 | NP | S1 | 13 | post-hoc | 8/8/9 of 12 | 216 | 9.7 | 134,363 -> 137,375 | 0.194 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); chained OOS DD DEEPER (137,375 vs 134,363); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic: PASS |
| M3 ref:continuous_lots | AS | S1 | 13 | post-hoc | 8/8/5 of 12 | 4,040 | 9.2 | 67,941 -> 86,635 | 0.194 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); chained OOS DD DEEPER (86,635 vs 67,941); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic: PASS |
| M3 ref:continuous_lots | AS | S2 | 13 | quick | 10/10/4 of 12 | 7,306 | -5.5 | 42,499 -> 42,368 | 0.019 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M3 ref:continuous_lots | NY | S1 | 13 | post-hoc | 8/8/5 of 12 | 3,481 | -4.5 | 200,647 -> 290,587 | 0.194 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); chained OOS DD DEEPER (290,587 vs 200,647); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic: PASS |
| M3 ref:continuous_lots | NY | S2 | 13 | quick | 8/8/7 of 12 | 11,777 | -4.1 | 133,613 -> 76,139 | 0.194 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M3 ref:win13 | AS | S2 | 13 | quick | 10/10/6 of 12 | 7,829 | 36.3 | 42,499 -> 53,092 | 0.019 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); chained OOS DD DEEPER (53,092 vs 42,499); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M3 ref:win52 | ALL | S2 | 13 | quick | 8/8/8 of 12 | 4,497 | 19.1 | 70,645 -> 46,546 | 0.194 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M3 ref:win52 | NY | S2 | 13 | quick | 9/9/7 of 12 | 10,245 | 0.9 | 133,613 -> 74,978 | 0.073 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); plain p 0.073 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M4 ref:inverse_half_inside | LO | S2 | 13 | quick | 10/11/8 of 12 | 1,357 | - | 11,940 -> 7,795 | 0.019 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M4 ref:low_only_full | LO | S2 | 4 | quick | 31/33/23 of 39 | 539 | - | 17,452 -> 9,592 | 7.1e-06 | 0.003 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; pessimistic re-score not run |
| M4 ref:low_only_full | LO | S2 | 13 | quick | 12/12/8 of 12 | 1,690 | - | 11,940 -> 6,880 | 2.4e-04 | 0.095 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 0.09; pessimistic re-score not run |
| M4 ref:pct_range | LO | S2 | 13 | quick | 10/11/8 of 12 | 1,089 | - | 11,940 -> 8,738 | 0.019 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M4 ref:pct_range | NP | S2 | 13 | quick | 8/8/5 of 12 | 1,481 | 3.1 | 23,091 -> 13,687 | 0.194 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M5 ref:N10 | NY | S1 | 2 | post-hoc | 55/55/36 of 77 | 7,954 | -9.9 | 200,647 -> 169,871 | 1.0e-04 | 0.039 | post-hoc approx (account layers not re-run); short-period DD is noisy; pessimistic re-score not run |
| M5 ref:N60 | NY | S1 | 13 | post-hoc | 8/8/7 of 12 | 10,046 | 1.6 | 200,647 -> 141,773 | 0.194 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; null: random-skip null (200 draws, same count per book): chained DD null mean -185503 vs -141773, p(null as good DD)=0; pessimistic re-score not run |
| M5 ref:opp30block | LO | S1 | 13 | post-hoc | 9/9/4 of 12 | 11,254 | -7.2 | 224,333 -> 152,502 | 0.073 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); plain p 0.073 > 0.05; p after Bonferroni x388 = 1.00; null: random-skip null (200 draws, same count per book): chained DD null mean -202229 vs -152501, p(null as good DD)=0; pessimistic re-score not run |
| M6 ref:k1 | NY | S1 | 13 | post-hoc | 8/8/4 of 12 | 7,319 | -1.5 | 200,647 -> 198,444 | 0.194 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); plain p 0.194 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M7 ref:gap | LO | S2 | 2 | post-hoc | 59/59/46 of 76 | 488 | -130.6 | 14,554 -> 14,548 | 7.0e-07 | 2.7e-04 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -131% (below -10%); pessimistic re-score not run |
| M7 ref:gap | LO | S2 | 4 | post-hoc | 33/33/24 of 38 | 894 | -166.8 | 14,505 -> 10,439 | 2.1e-06 | 8.3e-04 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -167% (below -10%); pessimistic re-score not run |
| M7 ref:gap | LO | S2 | 13 | post-hoc | 11/11/8 of 11 | 1,224 | -125.4 | 14,464 -> 15,490 | 4.9e-04 | 0.189 | S2=in-sample qualifiers; post-hoc approx; 13-week step, <=12 periods (8/12 is cheap); chained OOS DD DEEPER (15,490 vs 14,464); income -125% (below -10%); p after Bonferroni x388 = 0.19; pessimistic re-score not run |
| M7 ref:noevent | AS | S2 | 13 | post-hoc | 8/8/8 of 11 | 932 | 18.1 | 15,347 -> 10,003 | 0.113 | 1.000 | S2=in-sample qualifiers; post-hoc approx; 13-week step, <=12 periods (8/12 is cheap); plain p 0.113 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M7 ref:noevent | LO | S2 | 4 | post-hoc | 31/31/22 of 38 | 763 | -122.7 | 14,505 -> 13,710 | 5.8e-05 | 0.023 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -123% (below -10%); pessimistic re-score not run |
| M7 ref:noevent | LO | S2 | 13 | post-hoc | 10/10/8 of 11 | 998 | -113.7 | 14,464 -> 13,465 | 0.006 | 1.000 | S2=in-sample qualifiers; post-hoc approx; 13-week step, <=12 periods (8/12 is cheap); income -114% (below -10%); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M7 ref:range | LO | S2 | 13 | post-hoc | 8/8/7 of 11 | 866 | -62.3 | 14,464 -> 13,126 | 0.113 | 1.000 | S2=in-sample qualifiers; post-hoc approx; 13-week step, <=12 periods (8/12 is cheap); income -62% (below -10%); plain p 0.113 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M7 ref:weekday | AS | S2 | 13 | post-hoc | 7/7/9 of 11 | 904 | 38.2 | 15,347 -> 10,003 | 0.274 | 1.000 | S2=in-sample qualifiers; post-hoc approx; 13-week step, <=12 periods (8/12 is cheap); plain p 0.274 > 0.05; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M7 ref:worst2 | AS | S2 | 2 | post-hoc | 57/57/35 of 76 | 548 | -7.1 | 15,347 -> 10,656 | 7.4e-06 | 0.003 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; pessimistic re-score not run |
| M7 ref:worst2 | LO | S2 | 2 | post-hoc | 62/62/37 of 76 | 625 | -109.7 | 14,554 -> 13,937 | 1.2e-08 | 4.5e-06 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -110% (below -10%); pessimistic re-score not run |
| M7 ref:worst2 | LO | S2 | 4 | post-hoc | 34/34/22 of 38 | 1,095 | -114.2 | 14,505 -> 12,656 | 3.0e-07 | 1.2e-04 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -114% (below -10%); pessimistic re-score not run |
| M7 ref:worst2 | LO | S2 | 13 | post-hoc | 11/11/7 of 11 | 1,939 | -178.1 | 14,464 -> 11,645 | 4.9e-04 | 0.189 | S2=in-sample qualifiers; post-hoc approx; 13-week step, <=12 periods (8/12 is cheap); income -178% (below -10%); p after Bonferroni x388 = 0.19; pessimistic re-score not run |
| M8 ref:26w | AS | S2 | 2 | post-hoc | 59/59/36 of 76 | 356 | 5.1 | 15,347 -> 10,858 | 7.0e-07 | 2.7e-04 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; pessimistic re-score not run |
| M8 ref:26w | LO | S2 | 2 | post-hoc | 51/51/38 of 76 | 374 | -10.3 | 14,554 -> 13,526 | 0.002 | 0.744 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -10% (below -10%); p after Bonferroni x388 = 0.74; pessimistic re-score not run |
| M8 ref:26w | NY | S1 | 13 | post-hoc | 11/11/6 of 12 | 18,268 | -0.0 | 200,647 -> 208,779 | 0.003 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); chained OOS DD DEEPER (208,779 vs 200,647); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M8 ref:26w | NY | S2 | 4 | post-hoc | 26/26/16 of 38 | 716 | 13.6 | 18,432 -> 14,735 | 0.017 | 1.000 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M8 ref:half | LO | S2 | 4 | post-hoc | 33/33/21 of 38 | 933 | -11.7 | 14,505 -> 14,436 | 2.1e-06 | 8.3e-04 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -12% (below -10%); pessimistic re-score not run |
| M8 ref:half | LO | S2 | 13 | post-hoc | 11/11/5 of 11 | 2,275 | -30.1 | 14,464 -> 9,899 | 4.9e-04 | 0.189 | S2=in-sample qualifiers; post-hoc approx; 13-week step, <=12 periods (8/12 is cheap); income -30% (below -10%); p after Bonferroni x388 = 0.19; pessimistic re-score not run |
| M8 ref:half | NP | S2 | 4 | post-hoc | 26/26/18 of 38 | 368 | 1.6 | 22,890 -> 13,695 | 0.017 | 1.000 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M8 ref:half | NY | S2 | 2 | post-hoc | 60/60/36 of 76 | 623 | 27.3 | 18,432 -> 13,670 | 1.9e-07 | 7.5e-05 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; pessimistic re-score not run |
| M8 ref:half | NY | S2 | 4 | post-hoc | 31/31/16 of 38 | 1,036 | 30.7 | 18,432 -> 13,670 | 5.8e-05 | 0.023 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; pessimistic re-score not run |
| M8 ref:meantrade | NY | S1 | 13 | post-hoc | 10/10/6 of 12 | 14,460 | -2.1 | 200,647 -> 200,578 | 0.019 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M8 ref:meantrade | NY | S2 | 4 | post-hoc | 27/27/17 of 38 | 671 | 11.5 | 18,432 -> 15,481 | 0.007 | 1.000 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M8 ref:quarter | AS | S1 | 2 | post-hoc | 52/52/44 of 77 | 2,206 | -9.9 | 67,941 -> 77,837 | 0.001 | 0.543 | post-hoc approx (account layers not re-run); short-period DD is noisy; chained OOS DD DEEPER (77,837 vs 67,941); p after Bonferroni x388 = 0.54; pessimistic re-score not run |
| M8 ref:quarter | AS | S2 | 13 | post-hoc | 9/9/5 of 11 | 491 | -1.0 | 15,347 -> 12,536 | 0.033 | 1.000 | S2=in-sample qualifiers; post-hoc approx; 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M8 ref:quarter | LO | S2 | 2 | post-hoc | 53/53/40 of 76 | 384 | -34.1 | 14,554 -> 11,938 | 3.8e-04 | 0.148 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -34% (below -10%); p after Bonferroni x388 = 0.15; pessimistic re-score not run |
| M8 ref:quarter | LO | S2 | 4 | post-hoc | 31/31/20 of 38 | 761 | -48.9 | 14,505 -> 12,470 | 5.8e-05 | 0.023 | S2=in-sample qualifiers; post-hoc approx; short-period DD is noisy; income -49% (below -10%); pessimistic re-score not run |
| M8 ref:quarter | NP | S1 | 2 | post-hoc | 52/52/41 of 77 | 2,304 | -8.2 | 134,363 -> 152,013 | 0.001 | 0.543 | post-hoc approx (account layers not re-run); short-period DD is noisy; chained OOS DD DEEPER (152,013 vs 134,363); p after Bonferroni x388 = 0.54; pessimistic re-score not run |
| M8 ref:quarter | NY | S1 | 13 | post-hoc | 10/10/6 of 12 | 14,460 | -2.1 | 200,647 -> 200,578 | 0.019 | 1.000 | post-hoc approx (account layers not re-run); 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M9 ref:lots_only_approx | ALL | S2 | 4 | quick | 26/30/21 of 39 | 653 | -6.6 | 31,746 -> 19,971 | 5.0e-04 | 0.194 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; p after Bonferroni x388 = 0.19; pessimistic re-score not run |
| M9 ref:lots_only_approx | ALL | S2 | 13 | quick | 11/11/7 of 12 | 2,105 | -5.7 | 33,036 -> 20,734 | 0.003 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M9 ref:lots_only_approx | LO | S2 | 4 | quick | 27/29/18 of 39 | 262 | 14.3 | 19,640 -> 14,871 | 0.002 | 0.660 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; p after Bonferroni x388 = 0.66; pessimistic re-score not run |
| M9 ref:lots_only_approx | NP | S2 | 4 | quick | 28/30/22 of 39 | 411 | -3.0 | 20,635 -> 13,950 | 5.0e-04 | 0.194 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; p after Bonferroni x388 = 0.19; pessimistic re-score not run |
| M9 ref:lots_only_approx | NP | S2 | 13 | quick | 10/10/6 of 12 | 1,247 | -4.4 | 20,989 -> 13,781 | 0.019 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; pessimistic re-score not run |
| M9 ref:lots_only_approx | NY | S2 | 4 | quick | 27/29/17 of 39 | 436 | 5.6 | 20,496 -> 12,772 | 0.002 | 0.660 | S2=in-sample qualifiers; quick screen, not exact engine; short-period DD is noisy; p after Bonferroni x388 = 0.66; pessimistic re-score not run |
| M9 ref:lots_only_approx | NY | S2 | 13 | quick | 11/11/6 of 12 | 1,290 | 10.4 | 21,104 -> 13,158 | 0.003 | 1.000 | S2=in-sample qualifiers; quick screen, not exact engine; 13-week step, <=12 periods (8/12 is cheap); p after Bonferroni x388 = 1.00; pessimistic re-score not run |

## ALL 388 primary rows (drawdown first: L3M/L6M max DD U vs T, then income)

| method | sess | subj | step | basis | shallower/good/inc-higher of n | L3M maxDD U/T | L6M maxDD U/T | L6M worst-wk U/T | L6M income U/T | income % | chained DD U -> T | verdict | p | p_adj |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DYNEXIT | ALL | S1 | 2 | quick | 20/20/15 of 59 | 22,398/14,559 | 22,398/27,425 | 22,398/20,706 | 563,567/340,238 | -56.8 | - -> - | FAIL | 0.991 | 1.000 |
| DYNEXIT | ALL | S1 | 4 | quick | 12/12/9 of 39 | 22,398/14,559 | 22,398/23,541 | 22,398/23,541 | 559,165/331,025 | -51.6 | - -> - | FAIL | 0.988 | 1.000 |
| DYNEXIT | ALL | S1 | 13 | quick | 6/6/3 of 13 | 22,398/32,345 | 22,398/32,524 | 22,398/23,165 | 563,567/339,927 | -36.9 | - -> - | FAIL | 0.133 | 1.000 |
| DYNEXIT | AS | S1 | 2 | quick | 28/28/22 of 60 | 5,608/5,465 | 5,608/9,366 | 5,608/4,890 | 63,924/47,763 | -49.2 | - -> - | FAIL | 0.551 | 1.000 |
| DYNEXIT | AS | S1 | 4 | quick | 19/19/12 of 36 | 5,608/8,464 | 5,608/17,197 | 5,608/6,594 | 49,892/17,861 | -59.6 | - -> - | FAIL | 0.203 | 1.000 |
| DYNEXIT | AS | S1 | 13 | quick | 10/10/5 of 13 | 5,608/14,947 | 5,608/19,121 | 5,608/6,483 | 63,924/49,934 | -31.9 | - -> - | FAIL | 0.002 | 0.663 |
| DYNEXIT | LO | S1 | 2 | quick | 27/27/16 of 57 | 6,048/2,109 | 10,062/4,860 | 10,062/4,860 | 127,368/107,241 | -54.6 | - -> - | FAIL | 0.500 | 1.000 |
| DYNEXIT | LO | S1 | 4 | quick | 15/15/14 of 35 | 6,048/2,919 | 10,062/9,907 | 10,062/9,907 | 127,318/124,969 | -45.7 | - -> - | FAIL | 0.500 | 1.000 |
| DYNEXIT | LO | S1 | 13 | quick | 6/6/2 of 13 | 6,048/8,037 | 10,062/10,062 | 10,062/10,062 | 127,368/115,678 | -49.1 | - -> - | FAIL | 0.133 | 1.000 |
| DYNEXIT | NP | S1 | 2 | quick | 29/29/30 of 68 | 5,035/8,671 | 5,426/42,398 | 5,426/30,545 | 107,239/24,613 | -93.2 | - -> - | FAIL | 0.909 | 1.000 |
| DYNEXIT | NP | S1 | 4 | quick | 13/13/13 of 38 | 5,035/6,107 | 5,035/44,822 | 5,035/30,545 | 107,471/33,294 | -74.8 | - -> - | FAIL | 0.686 | 1.000 |
| DYNEXIT | NP | S1 | 13 | quick | 6/6/4 of 13 | 5,035/9,443 | 5,426/20,880 | 5,426/19,247 | 107,239/79,602 | -33.4 | - -> - | FAIL | 0.291 | 1.000 |
| DYNEXIT | NY | S1 | 2 | quick | 27/27/19 of 59 | 29,241/35,435 | 29,241/46,557 | 29,241/21,325 | 265,036/160,620 | -43.2 | - -> - | FAIL | 0.603 | 1.000 |
| DYNEXIT | NY | S1 | 4 | quick | 19/19/11 of 38 | 29,241/35,435 | 29,241/39,601 | 29,241/21,325 | 274,485/154,901 | -41.5 | - -> - | FAIL | 0.314 | 1.000 |
| DYNEXIT | NY | S1 | 13 | quick | 7/7/4 of 13 | 29,241/40,726 | 29,241/65,431 | 29,241/20,454 | 265,036/94,712 | -34.0 | - -> - | FAIL | 0.291 | 1.000 |
| DYNEXIT_X12 | ALL | S1q | 2 | quick | 17/17/24 of 46 | -22,398/-22,644 | -22,398/-22,644 | -22,398/-22,644 | 563,567/462,240 | -22.3 | 66,273 -> 73,970 | FAIL | - | - |
| DYNEXIT_X12 | ALL | S1q | 4 | quick | 11/11/8 of 33 | -22,398/-22,644 | -22,398/-22,644 | -22,398/-22,644 | 559,165/488,805 | -22.1 | 66,273 -> 71,955 | FAIL | - | - |
| DYNEXIT_X12 | ALL | S1q | 13 | quick | 9/8/2 of 12 | -22,398/-17,781 | -22,398/-17,781 | -22,398/-17,781 | 563,567/463,553 | -23.0 | 66,273 -> 72,672 | FAIL | - | - |
| DYNEXIT_X12 | AS | S1q | 2 | quick | 26/25/22 of 55 | -5,608/-5,608 | -5,608/-5,608 | -5,608/-5,608 | 63,924/62,494 | -8.1 | 21,572 -> 21,727 | FAIL | - | - |
| DYNEXIT_X12 | AS | S1q | 4 | quick | 17/15/10 of 34 | -5,608/-6,436 | -5,608/-6,436 | -5,608/-5,640 | 49,892/45,741 | -14.2 | 21,572 -> 25,014 | FAIL | - | - |
| DYNEXIT_X12 | AS | S1q | 13 | quick | 4/4/2 of 13 | -5,608/-5,608 | -5,608/-6,055 | -5,608/-5,608 | 63,924/63,642 | -2.5 | 21,572 -> 21,685 | FAIL | - | - |
| DYNEXIT_X12 | LO | S1q | 2 | quick | 20/19/25 of 52 | -6,048/-7,186 | -10,062/-8,684 | -10,062/-8,684 | 127,368/111,313 | -21.0 | 39,466 -> 28,513 | FAIL | - | - |
| DYNEXIT_X12 | LO | S1q | 4 | quick | 14/11/11 of 32 | -6,048/-6,798 | -10,062/-11,867 | -10,062/-10,062 | 127,318/112,215 | -26.5 | 39,466 -> 49,290 | FAIL | - | - |
| DYNEXIT_X12 | LO | S1q | 13 | quick | 5/5/2 of 13 | -6,048/-7,367 | -10,062/-10,062 | -10,062/-10,062 | 127,368/123,236 | -30.1 | 39,466 -> 29,050 | FAIL | - | - |
| DYNEXIT_X12 | NP | S1q | 2 | quick | 28/27/34 of 56 | -5,035/-9,659 | -5,426/-9,659 | -5,426/-7,539 | 107,239/50,009 | -39.1 | 33,512 -> 30,045 | FAIL | - | - |
| DYNEXIT_X12 | NP | S1q | 4 | quick | 18/18/13 of 36 | -5,035/-6,382 | -5,035/-6,382 | -5,035/-6,382 | 107,471/67,242 | -28.7 | 33,512 -> 27,010 | FAIL | - | - |
| DYNEXIT_X12 | NP | S1q | 13 | quick | 8/8/5 of 13 | -5,035/-5,249 | -5,426/-8,816 | -5,426/-7,539 | 107,239/77,036 | -19.2 | 33,512 -> 34,165 | FAIL | - | - |
| DYNEXIT_X12 | NY | S1q | 2 | quick | 27/25/27 of 56 | -29,241/-29,241 | -29,241/-29,241 | -29,241/-29,241 | 265,036/238,425 | -19.0 | 56,959 -> 60,438 | FAIL | - | - |
| DYNEXIT_X12 | NY | S1q | 4 | quick | 18/17/12 of 37 | -29,241/-29,241 | -29,241/-29,241 | -29,241/-29,241 | 274,485/263,607 | -19.2 | 56,959 -> 60,967 | FAIL | - | - |
| DYNEXIT_X12 | NY | S1q | 13 | quick | 10/9/5 of 13 | -29,241/-27,433 | -29,241/-27,433 | -29,241/-27,433 | 265,036/199,639 | -27.0 | 56,959 -> 48,478 | FAIL | - | - |
| DYNEXIT_X12X18 | ALL | S1q | 2 | quick | 21/21/18 of 49 | -22,398/-16,724 | -22,398/-16,724 | -22,398/-16,724 | 563,567/402,422 | -40.0 | 66,273 -> 82,729 | FAIL | - | - |
| DYNEXIT_X12X18 | ALL | S1q | 4 | quick | 17/17/9 of 33 | -22,398/-10,746 | -22,398/-12,878 | -22,398/-12,878 | 559,165/442,670 | -31.8 | 66,273 -> 79,605 | FAIL | - | - |
| DYNEXIT_X12X18 | ALL | S1q | 13 | quick | 11/10/1 of 12 | -22,398/-19,284 | -22,398/-19,284 | -22,398/-19,284 | 563,567/433,286 | -35.0 | 66,273 -> 64,525 | FAIL | - | - |
| DYNEXIT_X12X18 | AS | S1q | 2 | quick | 33/32/28 of 59 | -5,608/-9,265 | -5,608/-9,265 | -5,608/-6,897 | 63,924/61,407 | -30.3 | 21,572 -> 20,236 | FAIL | - | - |
| DYNEXIT_X12X18 | AS | S1q | 4 | quick | 24/23/17 of 37 | -5,608/-9,181 | -5,608/-9,181 | -5,608/-6,397 | 49,892/59,108 | -18.5 | 21,572 -> 20,685 | FAIL | - | - |
| DYNEXIT_X12X18 | AS | S1q | 13 | quick | 11/10/5 of 13 | -5,608/-4,668 | -5,608/-6,275 | -5,608/-4,431 | 63,924/67,367 | -17.2 | 21,572 -> 22,923 | FAIL | - | - |
| DYNEXIT_X12X18 | LO | S1q | 2 | quick | 30/28/22 of 59 | -6,048/-7,186 | -10,062/-10,320 | -10,062/-10,320 | 127,368/88,532 | -62.2 | 39,466 -> 51,922 | FAIL | - | - |
| DYNEXIT_X12X18 | LO | S1q | 4 | quick | 21/21/12 of 38 | -6,048/-6,798 | -10,062/-10,320 | -10,062/-10,320 | 127,318/102,061 | -49.8 | 39,466 -> 31,461 | FAIL | - | - |
| DYNEXIT_X12X18 | LO | S1q | 13 | quick | 8/7/2 of 13 | -6,048/-10,634 | -10,062/-11,483 | -10,062/-11,483 | 127,368/106,647 | -52.2 | 39,466 -> 28,353 | FAIL | - | - |
| DYNEXIT_X12X18 | NP | S1q | 2 | quick | 32/31/33 of 55 | -5,035/-10,444 | -5,426/-10,444 | -5,426/-6,508 | 107,239/51,642 | -39.3 | 33,512 -> 36,794 | FAIL | - | - |
| DYNEXIT_X12X18 | NP | S1q | 4 | quick | 21/19/14 of 35 | -5,035/-6,959 | -5,035/-9,520 | -5,035/-6,220 | 107,471/65,550 | -32.8 | 33,512 -> 39,621 | FAIL | - | - |
| DYNEXIT_X12X18 | NP | S1q | 13 | quick | 7/7/4 of 13 | -5,035/-5,150 | -5,426/-6,141 | -5,426/-6,141 | 107,239/73,406 | -28.5 | 33,512 -> 32,281 | FAIL | - | - |
| DYNEXIT_X12X18 | NY | S1q | 2 | quick | 37/36/27 of 58 | -29,241/-22,560 | -29,241/-22,560 | -29,241/-22,560 | 265,036/200,841 | -32.3 | 56,959 -> 83,565 | FAIL | - | - |
| DYNEXIT_X12X18 | NY | S1q | 4 | quick | 29/26/13 of 37 | -29,241/-22,560 | -29,241/-22,560 | -29,241/-22,560 | 274,485/215,950 | -26.3 | 56,959 -> 71,293 | FAIL | - | - |
| DYNEXIT_X12X18 | NY | S1q | 13 | quick | 10/10/4 of 13 | -29,241/-28,925 | -29,241/-28,925 | -29,241/-28,925 | 265,036/185,867 | -34.6 | 56,959 -> 47,855 | FAIL | - | - |
| DYNEXIT_X14_X19 | AS | S1q | 2 | quick | 29/29/28 of 77 | -/- | -/- | -/- | -/- | -29.4 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | AS | S1q | 4 | quick | 20/20/11 of 39 | -/- | -/- | -/- | -/- | -30.7 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | AS | S1q | 13 | quick | 7/7/0 of 12 | -/- | -/- | -/- | -/- | -39.0 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | LO | S1q | 2 | quick | 28/28/27 of 77 | -/- | -/- | -/- | -/- | -34.9 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | LO | S1q | 4 | quick | 22/22/17 of 39 | -/- | -/- | -/- | -/- | -44.2 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | LO | S1q | 13 | quick | 6/6/3 of 12 | -/- | -/- | -/- | -/- | -48.2 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | NP | S1q | 2 | quick | 39/39/34 of 77 | -/- | -/- | -/- | -/- | -55.6 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | NP | S1q | 4 | quick | 23/23/16 of 39 | -/- | -/- | -/- | -/- | -23.6 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | NP | S1q | 13 | quick | 10/10/8 of 12 | -/- | -/- | -/- | -/- | -26.6 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | NY | S1q | 2 | quick | 30/30/39 of 77 | -/- | -/- | -/- | -/- | -66.8 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | NY | S1q | 4 | quick | 17/17/20 of 39 | -/- | -/- | -/- | -/- | -42.5 | - -> - | FAIL | - | - |
| DYNEXIT_X14_X19 | NY | S1q | 13 | quick | 4/4/6 of 12 | -/- | -/- | -/- | -/- | -177.5 | - -> - | FAIL | - | - |
| DYNEXIT_X16 | ALL | S1q | 2 | quick | 21/21/19 of 46 | -22,398/-17,480 | -22,398/-17,480 | -22,398/-17,480 | 563,567/446,299 | -30.9 | 66,273 -> 65,567 | FAIL | - | - |
| DYNEXIT_X16 | ALL | S1q | 4 | quick | 18/18/12 of 33 | -22,398/-13,180 | -22,398/-15,080 | -22,398/-15,080 | 559,165/463,223 | -25.4 | 66,273 -> 66,792 | FAIL | - | - |
| DYNEXIT_X16 | ALL | S1q | 13 | quick | 9/8/2 of 12 | -22,398/-20,969 | -22,398/-20,969 | -22,398/-20,969 | 563,567/471,369 | -27.8 | 66,273 -> 77,189 | FAIL | - | - |
| DYNEXIT_X16 | AS | S1q | 2 | quick | 33/32/32 of 57 | -5,608/-4,431 | -5,608/-7,592 | -5,608/-5,458 | 63,924/66,223 | -18.4 | 21,572 -> 17,020 | FAIL | - | - |
| DYNEXIT_X16 | AS | S1q | 4 | quick | 26/25/14 of 37 | -5,608/-4,431 | -5,608/-4,431 | -5,608/-4,431 | 49,892/53,839 | -21.4 | 21,572 -> 22,565 | FAIL | - | - |
| DYNEXIT_X16 | AS | S1q | 13 | quick | 10/8/3 of 13 | -5,608/-6,140 | -5,608/-6,140 | -5,608/-6,140 | 63,924/66,023 | -10.8 | 21,572 -> 19,955 | FAIL | - | - |
| DYNEXIT_X16 | LO | S1q | 2 | quick | 31/31/23 of 55 | -6,048/-6,893 | -10,062/-9,576 | -10,062/-9,576 | 127,368/102,259 | -43.1 | 39,466 -> 22,735 | FAIL | - | - |
| DYNEXIT_X16 | LO | S1q | 4 | quick | 22/20/10 of 36 | -6,048/-6,893 | -10,062/-9,576 | -10,062/-9,576 | 127,318/100,101 | -47.4 | 39,466 -> 23,759 | FAIL | - | - |
| DYNEXIT_X16 | LO | S1q | 13 | quick | 8/8/2 of 13 | -6,048/-9,264 | -10,062/-11,483 | -10,062/-11,483 | 127,368/109,388 | -42.6 | 39,466 -> 26,146 | FAIL | - | - |
| DYNEXIT_X16 | NP | S1q | 2 | quick | 32/32/25 of 56 | -5,035/-8,766 | -5,426/-8,766 | -5,426/-7,368 | 107,239/53,250 | -34.8 | 33,512 -> 31,804 | FAIL | - | - |
| DYNEXIT_X16 | NP | S1q | 4 | quick | 19/19/16 of 37 | -5,035/-5,050 | -5,035/-9,951 | -5,035/-7,050 | 107,471/73,696 | -26.4 | 33,512 -> 29,297 | FAIL | - | - |
| DYNEXIT_X16 | NP | S1q | 13 | quick | 7/6/4 of 13 | -5,035/-7,786 | -5,426/-7,786 | -5,426/-7,246 | 107,239/70,077 | -29.4 | 33,512 -> 21,702 | FAIL | - | - |
| DYNEXIT_X16 | NY | S1q | 2 | quick | 33/31/29 of 57 | -29,241/-26,091 | -29,241/-26,091 | -29,241/-26,091 | 265,036/224,567 | -26.6 | 56,959 -> 69,920 | FAIL | - | - |
| DYNEXIT_X16 | NY | S1q | 4 | quick | 24/21/16 of 37 | -29,241/-26,091 | -29,241/-26,091 | -29,241/-26,091 | 274,485/235,587 | -15.5 | 56,959 -> 56,455 | FAIL | - | - |
| DYNEXIT_X16 | NY | S1q | 13 | quick | 9/9/3 of 13 | -29,241/-26,504 | -29,241/-26,504 | -29,241/-26,504 | 265,036/225,881 | -24.6 | 56,959 -> 86,073 | FAIL | - | - |
| DYNEXIT_X17 | ALL | S1q | 2 | quick | 26/24/30 of 43 | -22,398/-17,055 | -22,398/-17,055 | -22,398/-17,055 | 563,567/520,450 | -11.6 | 66,273 -> 66,311 | FAIL | - | - |
| DYNEXIT_X17 | ALL | S1q | 4 | quick | 17/16/12 of 30 | -22,398/-17,055 | -22,398/-17,055 | -22,398/-17,055 | 559,165/524,976 | -11.8 | 66,273 -> 68,931 | FAIL | - | - |
| DYNEXIT_X17 | ALL | S1q | 13 | quick | 8/7/4 of 12 | -22,398/-22,711 | -22,398/-22,711 | -22,398/-22,711 | 563,567/509,529 | -12.4 | 66,273 -> 60,777 | FAIL | - | - |
| DYNEXIT_X17 | AS | S1q | 2 | quick | 27/26/34 of 57 | -5,608/-6,160 | -5,608/-6,160 | -5,608/-5,671 | 63,924/55,723 | -9.5 | 21,572 -> 17,796 | FAIL | - | - |
| DYNEXIT_X17 | AS | S1q | 4 | quick | 22/18/18 of 36 | -5,608/-6,854 | -5,608/-6,854 | -5,608/-6,365 | 49,892/53,686 | -4.4 | 21,572 -> 17,581 | FAIL | - | - |
| DYNEXIT_X17 | AS | S1q | 13 | quick | 10/7/4 of 13 | -5,608/-4,668 | -5,608/-6,275 | -5,608/-4,431 | 63,924/67,367 | -3.1 | 21,572 -> 22,890 | FAIL | - | - |
| DYNEXIT_X17 | LO | S1q | 2 | quick | 21/21/26 of 51 | -6,048/-6,048 | -10,062/-10,062 | -10,062/-10,062 | 127,368/117,843 | -22.2 | 39,466 -> 28,009 | FAIL | - | - |
| DYNEXIT_X17 | LO | S1q | 4 | quick | 15/14/14 of 32 | -6,048/-6,048 | -10,062/-11,263 | -10,062/-11,263 | 127,318/119,047 | -22.6 | 39,466 -> 41,797 | FAIL | - | - |
| DYNEXIT_X17 | LO | S1q | 13 | quick | 10/9/3 of 13 | -6,048/-6,048 | -10,062/-11,165 | -10,062/-11,165 | 127,368/122,041 | -24.2 | 39,466 -> 28,398 | FAIL | - | - |
| DYNEXIT_X17 | NP | S1q | 2 | quick | 27/27/36 of 56 | -5,035/-6,533 | -5,426/-8,510 | -5,426/-6,533 | 107,239/89,290 | -9.0 | 33,512 -> 24,748 | FAIL | - | - |
| DYNEXIT_X17 | NP | S1q | 4 | quick | 18/17/17 of 36 | -5,035/-6,648 | -5,035/-7,162 | -5,035/-6,648 | 107,471/78,863 | -10.4 | 33,512 -> 27,291 | FAIL | - | - |
| DYNEXIT_X17 | NP | S1q | 13 | quick | 8/8/3 of 13 | -5,035/-9,225 | -5,426/-9,225 | -5,426/-6,257 | 107,239/85,993 | -21.2 | 33,512 -> 27,996 | FAIL | - | - |
| DYNEXIT_X17 | NY | S1q | 2 | quick | 34/34/32 of 55 | -29,241/-24,898 | -29,241/-24,898 | -29,241/-24,898 | 265,036/257,594 | -8.3 | 56,959 -> 62,133 | FAIL | - | - |
| DYNEXIT_X17 | NY | S1q | 4 | quick | 21/18/13 of 37 | -29,241/-24,898 | -29,241/-24,898 | -29,241/-24,898 | 274,485/273,380 | -9.2 | 56,959 -> 52,954 | FAIL | - | - |
| DYNEXIT_X17 | NY | S1q | 13 | quick | 8/7/4 of 13 | -29,241/-29,241 | -29,241/-29,241 | -29,241/-29,241 | 265,036/234,129 | -5.2 | 56,959 -> 55,163 | FAIL | - | - |
| DYNEXIT_X18 | ALL | S1q | 2 | quick | 19/19/26 of 42 | -22,398/-22,099 | -22,398/-22,099 | -22,398/-22,099 | 563,567/480,666 | -12.1 | 66,273 -> 82,345 | FAIL | - | - |
| DYNEXIT_X18 | ALL | S1q | 4 | quick | 17/17/13 of 31 | -22,398/-22,099 | -22,398/-22,099 | -22,398/-22,099 | 559,165/509,155 | -7.8 | 66,273 -> 83,408 | FAIL | - | - |
| DYNEXIT_X18 | ALL | S1q | 13 | quick | 8/7/3 of 12 | -22,398/-23,598 | -22,398/-23,598 | -22,398/-23,598 | 563,567/539,894 | -9.7 | 66,273 -> 58,830 | FAIL | - | - |
| DYNEXIT_X18 | AS | S1q | 2 | quick | 20/18/22 of 55 | -5,608/-5,608 | -5,608/-5,608 | -5,608/-5,608 | 63,924/64,860 | -4.1 | 21,572 -> 21,203 | FAIL | - | - |
| DYNEXIT_X18 | AS | S1q | 4 | quick | 15/14/14 of 34 | -5,608/-5,608 | -5,608/-5,608 | -5,608/-5,608 | 49,892/49,876 | -2.1 | 21,572 -> 19,068 | FAIL | - | - |
| DYNEXIT_X18 | AS | S1q | 13 | quick | 7/5/2 of 13 | -5,608/-5,608 | -5,608/-5,608 | -5,608/-5,608 | 63,924/62,864 | -19.2 | 21,572 -> 28,228 | FAIL | - | - |
| DYNEXIT_X18 | LO | S1q | 2 | quick | 25/24/25 of 52 | -6,048/-6,048 | -10,062/-11,083 | -10,062/-11,083 | 127,368/104,690 | -13.9 | 39,466 -> 26,444 | FAIL | - | - |
| DYNEXIT_X18 | LO | S1q | 4 | quick | 15/13/16 of 32 | -6,048/-6,048 | -10,062/-11,911 | -10,062/-11,911 | 127,318/116,029 | -5.3 | 39,466 -> 20,425 | FAIL | - | - |
| DYNEXIT_X18 | LO | S1q | 13 | quick | 7/6/7 of 13 | -6,048/-6,048 | -10,062/-10,062 | -10,062/-10,062 | 127,368/129,812 | -5.9 | 39,466 -> 32,319 | FAIL | - | - |
| DYNEXIT_X18 | NP | S1q | 2 | quick | 22/20/32 of 53 | -5,035/-6,992 | -5,426/-6,992 | -5,426/-6,992 | 107,239/82,268 | -15.7 | 33,512 -> 34,189 | FAIL | - | - |
| DYNEXIT_X18 | NP | S1q | 4 | quick | 14/12/18 of 36 | -5,035/-6,922 | -5,035/-6,931 | -5,035/-6,922 | 107,471/87,801 | -10.8 | 33,512 -> 33,177 | FAIL | - | - |
| DYNEXIT_X18 | NP | S1q | 13 | quick | 5/4/3 of 13 | -5,035/-5,035 | -5,426/-5,035 | -5,426/-5,035 | 107,239/106,778 | -8.1 | 33,512 -> 33,528 | FAIL | - | - |
| DYNEXIT_X18 | NY | S1q | 2 | quick | 17/17/25 of 55 | -29,241/-29,241 | -29,241/-29,241 | -29,241/-29,241 | 265,036/228,847 | -11.8 | 56,959 -> 83,846 | FAIL | - | - |
| DYNEXIT_X18 | NY | S1q | 4 | quick | 15/14/11 of 37 | -29,241/-29,241 | -29,241/-29,241 | -29,241/-29,241 | 274,485/255,448 | -9.1 | 56,959 -> 85,375 | FAIL | - | - |
| DYNEXIT_X18 | NY | S1q | 13 | quick | 5/5/4 of 13 | -29,241/-29,241 | -29,241/-29,241 | -29,241/-29,241 | 265,036/240,439 | -9.6 | 56,959 -> 64,869 | FAIL | - | - |
| DYNEXIT_X8 | AS | S1 | 2 | quick | 47/43/26 of 79 | -42,000/-54,119 | -59,718/-65,864 | -22,118/-23,188 | 502,053/398,178 | -26.1 | 87,991 -> 121,636 | FAIL | 0.057 | 1.000 |
| DYNEXIT_X8 | AS | S1 | 4 | quick | 27/22/14 of 40 | -42,000/-56,464 | -59,718/-68,209 | -22,118/-23,188 | 502,053/410,163 | -26.0 | 87,991 -> 110,801 | FAIL | 0.019 | 1.000 |
| DYNEXIT_X8 | AS | S1 | 13 | quick | 6/8/2 of 13 | -42,000/-56,464 | -59,718/-68,209 | -22,118/-20,828 | 502,053/390,608 | -20.9 | 87,991 -> 99,185 | FAIL | 0.709 | 1.000 |
| DYNEXIT_X8 | NY | S1 | 2 | quick | 39/35/32 of 78 | -101,654/-217,090 | -89,598/-217,090 | -49,561/-45,064 | 1,408,711/1,097,466 | -28.6 | 237,236 -> 261,659 | FAIL | 0.545 | 1.000 |
| DYNEXIT_X8 | NY | S1 | 4 | quick | 21/22/15 of 40 | -101,654/-196,600 | -89,598/-196,600 | -49,561/-45,064 | 1,408,711/1,099,951 | -27.6 | 237,236 -> 268,679 | FAIL | 0.437 | 1.000 |
| DYNEXIT_X8 | NY | S1 | 13 | quick | 6/8/3 of 13 | -101,654/-196,600 | -89,598/-196,600 | -49,561/-48,719 | 1,408,711/1,063,521 | -18.5 | 237,236 -> 263,604 | FAIL | 0.709 | 1.000 |
| M1 | AS | S1 | 1 | post-hoc | 76/83/54 of 152 | -23,953/-22,498 | -37,750/-44,272 | -33,859/-31,840 | 15,460/13,969 | -14.0 | 67,941 -> 71,713 | FAIL | 0.560 | 1.000 |
| M1 | AS | S1 | 2 | post-hoc | 43/46/23 of 77 | -23,953/-22,498 | -37,750/-53,949 | -33,859/-31,840 | 15,460/13,457 | -17.8 | 67,941 -> 74,831 | FAIL | 0.835 | 1.000 |
| M1 | AS | S1 | 4 | post-hoc | 20/21/9 of 39 | -23,953/-22,498 | -37,750/-45,823 | -33,859/-31,840 | 15,460/13,603 | -13.0 | 67,941 -> 68,950 | FAIL | 0.990 | 1.000 |
| M1 | AS | S1 | 13 | post-hoc | 7/7/2 of 12 | -23,953/-22,498 | -37,750/-45,328 | -33,859/-31,840 | 15,460/13,786 | -10.4 | 67,941 -> 63,577 | FAIL | 0.795 | 1.000 |
| M1 | AS | S2 | 1 | quick | 40/54/54 of 152 | -3,189/-3,202 | -3,999/-3,869 | -2,455/-2,367 | 618/566 | -10.0 | 7,083 -> 6,929 | FAIL | 0.990 | 1.000 |
| M1 | AS | S2 | 2 | quick | 28/32/27 of 77 | -3,189/-3,201 | -3,999/-3,929 | -2,455/-2,427 | 618/564 | -9.3 | 7,083 -> 6,820 | FAIL | 1.000 | 1.000 |
| M1 | AS | S2 | 4 | quick | 20/20/12 of 39 | -3,189/-3,201 | -3,999/-3,929 | -2,455/-2,427 | 618/581 | -6.3 | 7,083 -> 6,801 | FAIL | 1.000 | 1.000 |
| M1 | AS | S2 | 13 | quick | 4/4/2 of 12 | -3,189/-3,201 | -3,999/-3,974 | -2,455/-2,443 | 618/613 | -1.3 | 7,083 -> 6,959 | FAIL | 1.000 | 1.000 |
| M1 | LO | S1 | 1 | post-hoc | 58/58/25 of 152 | -39,760/-39,760 | -39,760/-39,760 | -20,695/-20,695 | 17,963/15,014 | -27.6 | 224,333 -> 221,199 | FAIL | 0.945 | 1.000 |
| M1 | LO | S1 | 2 | post-hoc | 33/33/14 of 77 | -39,760/-39,760 | -39,760/-39,760 | -20,695/-20,695 | 17,963/15,161 | -25.5 | 224,333 -> 208,547 | FAIL | 0.775 | 1.000 |
| M1 | LO | S1 | 4 | post-hoc | 17/17/6 of 39 | -39,760/-39,760 | -39,760/-39,760 | -20,695/-20,172 | 17,963/15,657 | -15.1 | 224,333 -> 170,046 | FAIL | 0.840 | 1.000 |
| M1 | LO | S1 | 13 | post-hoc | 7/7/3 of 12 | -39,760/-36,518 | -39,760/-36,518 | -20,695/-18,372 | 17,963/14,941 | -16.5 | 224,333 -> 174,724 | FAIL | 0.875 | 1.000 |
| M1 | LO | S2 | 1 | quick | 38/51/51 of 152 | -5,858/-5,711 | -5,858/-5,711 | -3,458/-3,300 | 126/101 | 5.1 | 13,451 -> 11,894 | FAIL | 0.445 | 1.000 |
| M1 | LO | S2 | 2 | quick | 28/30/25 of 77 | -5,858/-5,711 | -5,858/-5,711 | -3,458/-3,300 | 126/89 | 0.6 | 13,451 -> 12,922 | FAIL | 0.815 | 1.000 |
| M1 | LO | S2 | 4 | quick | 18/18/14 of 39 | -5,858/-5,711 | -5,858/-5,711 | -3,458/-3,300 | 126/89 | -1.1 | 13,451 -> 13,535 | FAIL | 0.740 | 1.000 |
| M1 | LO | S2 | 13 | quick | 2/2/2 of 12 | -5,858/-5,858 | -5,858/-5,858 | -3,458/-3,458 | 126/126 | 17.8 | 13,451 -> 12,302 | FAIL | 1.000 | 1.000 |
| M1 | NP | S1 | 1 | post-hoc | 75/75/45 of 152 | -26,269/-26,269 | -30,613/-28,796 | -23,047/-23,047 | 12,962/12,101 | -12.1 | 134,363 -> 119,084 | FAIL | 0.985 | 1.000 |
| M1 | NP | S1 | 2 | post-hoc | 41/41/22 of 77 | -26,269/-26,269 | -30,613/-28,796 | -23,047/-23,047 | 12,962/12,042 | -10.2 | 134,363 -> 119,239 | FAIL | 0.895 | 1.000 |
| M1 | NP | S1 | 4 | post-hoc | 21/21/11 of 39 | -26,269/-26,269 | -30,613/-28,796 | -23,047/-23,047 | 12,962/12,427 | -8.8 | 134,363 -> 128,411 | FAIL | 0.915 | 1.000 |
| M1 | NP | S1 | 13 | post-hoc | 8/8/1 of 12 | -26,269/-26,269 | -30,613/-28,796 | -23,047/-18,119 | 12,962/12,676 | -14.9 | 134,363 -> 130,279 | FAIL | 0.720 | 1.000 |
| M1 | NP | S2 | 1 | quick | 41/58/58 of 152 | -5,097/-5,321 | -13,868/-9,542 | -4,339/-4,273 | 125/163 | 3.7 | 23,091 -> 16,888 | FAIL | 0.345 | 1.000 |
| M1 | NP | S2 | 2 | quick | 32/35/29 of 77 | -5,097/-5,321 | -13,868/-9,717 | -4,339/-4,273 | 125/133 | 3.2 | 23,091 -> 16,814 | FAIL | 0.705 | 1.000 |
| M1 | NP | S2 | 4 | quick | 22/23/16 of 39 | -5,097/-5,162 | -13,868/-9,796 | -4,339/-4,114 | 125/136 | 2.7 | 23,091 -> 17,148 | FAIL | 0.555 | 1.000 |
| M1 | NP | S2 | 13 | quick | 4/4/2 of 12 | -5,097/-5,062 | -13,868/-11,703 | -4,339/-3,824 | 125/10 | -19.3 | 23,091 -> 20,676 | FAIL | 1.000 | 1.000 |
| M1 | NY | S1 | 1 | post-hoc | 83/84/56 of 152 | -69,974/-69,974 | -69,974/-69,974 | -59,414/-51,610 | 53,912/50,226 | -9.8 | 200,647 -> 157,041 | FAIL | 0.975 | 1.000 |
| M1 | NY | S1 | 2 | post-hoc | 44/44/25 of 77 | -69,974/-69,974 | -69,974/-69,974 | -59,414/-52,486 | 53,912/51,144 | -6.2 | 200,647 -> 157,041 | FAIL | 1.000 | 1.000 |
| M1 | NY | S1 | 4 | post-hoc | 26/26/13 of 39 | -69,974/-69,974 | -69,974/-86,130 | -59,414/-65,119 | 53,912/50,184 | -8.5 | 200,647 -> 175,216 | PASS | 0.670 | 1.000 |
| M1 | NY | S1 | 13 | post-hoc | 11/11/3 of 12 | -69,974/-68,232 | -69,974/-69,723 | -59,414/-52,486 | 53,912/48,232 | -17.1 | 200,647 -> 162,225 | FAIL | 0.355 | 1.000 |
| M1 | NY | S2 | 1 | quick | 53/64/64 of 152 | -4,696/-4,362 | -10,511/-9,301 | -3,134/-2,946 | -126/-125 | -1.6 | 22,269 -> 19,116 | FAIL | 0.895 | 1.000 |
| M1 | NY | S2 | 2 | quick | 39/42/30 of 77 | -4,696/-4,315 | -10,511/-9,321 | -3,134/-2,951 | -126/-133 | -2.9 | 22,269 -> 19,349 | FAIL | 0.910 | 1.000 |
| M1 | NY | S2 | 4 | quick | 27/28/15 of 39 | -4,696/-4,292 | -10,511/-9,791 | -3,134/-2,951 | -126/-117 | 0.6 | 22,269 -> 19,996 | PASS | 0.505 | 1.000 |
| M1 | NY | S2 | 13 | quick | 6/6/2 of 12 | -4,696/-4,412 | -10,511/-9,904 | -3,134/-2,968 | -126/-126 | -1.2 | 22,269 -> 21,249 | FAIL | 1.000 | 1.000 |
| M10 | AS | S1 | 1 | post-hoc | 41/41/15 of 152 | -23,953/-23,953 | -37,750/-38,370 | -33,859/-33,859 | 15,460/14,675 | -19.4 | 67,941 -> 75,362 | FAIL | 0.870 | 1.000 |
| M10 | AS | S1 | 2 | post-hoc | 21/21/9 of 77 | -23,953/-23,953 | -37,750/-34,639 | -33,859/-33,859 | 15,460/14,908 | -8.9 | 67,941 -> 71,631 | FAIL | 1.000 | 1.000 |
| M10 | AS | S1 | 4 | post-hoc | 10/10/2 of 39 | -23,953/-23,953 | -37,750/-37,229 | -33,859/-20,499 | 15,460/12,978 | -10.0 | 67,941 -> 70,713 | FAIL | 1.000 | 1.000 |
| M10 | AS | S1 | 13 | post-hoc | 1/1/0 of 12 | -23,953/-23,953 | -37,750/-37,750 | -33,859/-33,859 | 15,460/15,460 | -6.0 | 67,941 -> 64,207 | FAIL | 1.000 | 1.000 |
| M10 | AS | S2 | 1 | quick | 25/25/25 of 152 | -3,189/-2,796 | -3,999/-3,999 | -2,455/-2,455 | 618/518 | -19.8 | 7,083 -> 6,487 | FAIL | 0.805 | 1.000 |
| M10 | AS | S2 | 2 | quick | 21/21/13 of 77 | -3,189/-2,796 | -3,999/-3,999 | -2,455/-2,455 | 618/518 | -9.0 | 7,083 -> 5,934 | FAIL | 0.440 | 1.000 |
| M10 | AS | S2 | 4 | quick | 14/14/4 of 39 | -3,189/-3,189 | -3,999/-3,999 | -2,455/-2,455 | 618/441 | -21.0 | 7,083 -> 6,662 | FAIL | 0.805 | 1.000 |
| M10 | AS | S2 | 13 | quick | 5/5/0 of 12 | -3,189/-3,189 | -3,999/-3,189 | -2,455/-1,920 | 618/351 | -53.7 | 7,083 -> 7,083 | FAIL | 1.000 | 1.000 |
| M10 | LO | S1 | 1 | post-hoc | 41/41/15 of 152 | -39,760/-39,760 | -39,760/-39,760 | -20,695/-20,695 | 17,963/17,199 | -17.0 | 224,333 -> 213,492 | FAIL | 0.245 | 1.000 |
| M10 | LO | S1 | 2 | post-hoc | 21/21/6 of 77 | -39,760/-39,760 | -39,760/-39,760 | -20,695/-20,695 | 17,963/17,107 | -20.4 | 224,333 -> 232,222 | FAIL | 1.000 | 1.000 |
| M10 | LO | S1 | 4 | post-hoc | 10/10/3 of 39 | -39,760/-39,760 | -39,760/-39,760 | -20,695/-20,695 | 17,963/15,784 | -10.8 | 224,333 -> 150,993 | FAIL | 1.000 | 1.000 |
| M10 | LO | S1 | 13 | post-hoc | 2/2/2 of 12 | -39,760/-39,760 | -39,760/-39,760 | -20,695/-20,695 | 17,963/17,963 | 5.6 | 224,333 -> 156,282 | FAIL | 1.000 | 1.000 |
| M10 | LO | S2 | 1 | quick | 36/36/36 of 152 | -5,858/-5,858 | -5,858/-5,858 | -3,458/-3,458 | 126/35 | -23.7 | 13,451 -> 13,765 | FAIL | 0.590 | 1.000 |
| M10 | LO | S2 | 2 | quick | 28/28/21 of 77 | -5,858/-5,858 | -5,858/-5,858 | -3,458/-3,458 | 126/33 | -26.3 | 13,451 -> 14,315 | FAIL | 0.690 | 1.000 |
| M10 | LO | S2 | 4 | quick | 15/15/7 of 39 | -5,858/-5,858 | -5,858/-5,858 | -3,458/-3,458 | 126/42 | -4.6 | 13,451 -> 11,866 | FAIL | 0.975 | 1.000 |
| M10 | LO | S2 | 13 | quick | 5/5/3 of 12 | -5,858/-5,858 | -5,858/-5,858 | -3,458/-3,458 | 126/110 | 29.1 | 13,451 -> 9,906 | FAIL | 1.000 | 1.000 |
| M10 | NP | S1 | 1 | post-hoc | 40/40/18 of 152 | -26,269/-26,269 | -30,613/-30,613 | -23,047/-23,047 | 12,962/12,674 | -5.4 | 134,363 -> 75,564 | FAIL | 0.520 | 1.000 |
| M10 | NP | S1 | 2 | post-hoc | 20/20/7 of 77 | -26,269/-26,269 | -30,613/-30,613 | -23,047/-23,047 | 12,962/12,247 | -5.3 | 134,363 -> 97,424 | FAIL | 0.720 | 1.000 |
| M10 | NP | S1 | 4 | post-hoc | 10/10/3 of 39 | -26,269/-26,269 | -30,613/-30,613 | -23,047/-23,047 | 12,962/12,399 | -2.5 | 134,363 -> 112,825 | FAIL | 1.000 | 1.000 |
| M10 | NP | S1 | 13 | post-hoc | 3/3/0 of 12 | -26,269/-26,269 | -30,613/-26,269 | -23,047/-18,119 | 12,962/9,565 | -23.8 | 134,363 -> 134,363 | FAIL | 1.000 | 1.000 |
| M10 | NP | S2 | 1 | quick | 29/29/29 of 152 | -5,097/-4,659 | -13,868/-6,934 | -4,339/-4,339 | 125/237 | -24.3 | 23,091 -> 14,023 | FAIL | 0.930 | 1.000 |
| M10 | NP | S2 | 2 | quick | 23/23/14 of 77 | -5,097/-4,220 | -13,868/-6,934 | -4,339/-4,339 | 125/271 | -14.7 | 23,091 -> 14,751 | FAIL | 0.830 | 1.000 |
| M10 | NP | S2 | 4 | quick | 13/13/5 of 39 | -5,097/-5,097 | -13,868/-6,934 | -4,339/-4,339 | 125/281 | -23.8 | 23,091 -> 15,978 | FAIL | 0.985 | 1.000 |
| M10 | NP | S2 | 13 | quick | 3/3/2 of 12 | -5,097/-5,097 | -13,868/-6,934 | -4,339/-2,559 | 125/130 | 11.1 | 23,091 -> 12,942 | FAIL | 1.000 | 1.000 |
| M10 | NY | S1 | 1 | post-hoc | 32/32/10 of 152 | -69,974/-69,974 | -69,974/-69,974 | -59,414/-37,621 | 53,912/52,263 | -11.7 | 200,647 -> 174,622 | FAIL | 0.550 | 1.000 |
| M10 | NY | S1 | 2 | post-hoc | 18/18/6 of 77 | -69,974/-69,974 | -69,974/-69,974 | -59,414/-37,621 | 53,912/51,914 | -12.0 | 200,647 -> 174,622 | FAIL | 1.000 | 1.000 |
| M10 | NY | S1 | 4 | post-hoc | 9/9/3 of 39 | -69,974/-69,974 | -69,974/-69,974 | -59,414/-59,414 | 53,912/49,337 | -14.2 | 200,647 -> 173,715 | FAIL | 1.000 | 1.000 |
| M10 | NY | S1 | 13 | post-hoc | 2/2/0 of 12 | -69,974/-69,974 | -69,974/-69,974 | -59,414/-35,029 | 53,912/42,070 | -10.8 | 200,647 -> 184,763 | FAIL | 1.000 | 1.000 |
| M10 | NY | S2 | 1 | quick | 27/27/27 of 152 | -4,696/-3,558 | -10,511/-6,454 | -3,134/-2,501 | -126/-119 | -41.3 | 22,269 -> 14,146 | FAIL | 0.815 | 1.000 |
| M10 | NY | S2 | 2 | quick | 21/21/13 of 77 | -4,696/-4,696 | -10,511/-7,440 | -3,134/-2,501 | -126/-200 | -37.5 | 22,269 -> 15,132 | FAIL | 0.735 | 1.000 |
| M10 | NY | S2 | 4 | quick | 13/13/5 of 39 | -4,696/-4,696 | -10,511/-7,407 | -3,134/-2,501 | -126/-47 | -1.2 | 22,269 -> 15,099 | FAIL | 0.395 | 1.000 |
| M10 | NY | S2 | 13 | quick | 7/7/1 of 12 | -4,696/-2,348 | -10,511/-5,255 | -3,134/-1,567 | -126/-63 | -49.7 | 22,269 -> 18,063 | FAIL | 1.000 | 1.000 |
| M11 | ALL | S1 | 2 | post-hoc | 30/30/8 of 32 | -38,773/-35,906 | -76,723/-46,710 | -60,858/-40,865 | 100,297/61,611 | -35.8 | 215,625 -> 97,549 | FAIL | 0.650 | 1.000 |
| M11 | ALL | S1 | 4 | post-hoc | 16/16/2 of 16 | -38,773/-26,384 | -76,723/-46,710 | -60,858/-40,865 | 100,297/60,494 | -37.5 | 215,625 -> 96,513 | FAIL | 0.470 | 1.000 |
| M11 | ALL | S1 | 13 | post-hoc | 5/5/0 of 5 | -38,773/-26,384 | -76,723/-46,710 | -60,858/-40,865 | 100,297/55,592 | -40.6 | 215,625 -> 116,477 | FAIL | 0.935 | 1.000 |
| M11 | ALL | S2 | 2 | quick | 9/17/16 of 32 | -10,529/-7,798 | -11,188/-7,798 | -6,280/-4,521 | 863/477 | -56.1 | 34,757 -> 22,601 | FAIL | 0.265 | 1.000 |
| M11 | ALL | S2 | 4 | quick | 10/11/5 of 16 | -10,529/-8,234 | -10,529/-8,234 | -6,280/-4,521 | 881/403 | -71.0 | 34,285 -> 25,321 | FAIL | 0.490 | 1.000 |
| M11 | ALL | S2 | 13 | quick | 5/5/1 of 5 | -10,529/-7,304 | -11,188/-9,530 | -6,280/-3,916 | 743/390 | -63.7 | 34,757 -> 29,817 | FAIL | 0.645 | 1.000 |
| M11 | AS | S1 | 2 | post-hoc | 23/27/14 of 32 | -21,250/-14,428 | -37,750/-33,017 | -33,859/-16,929 | 15,460/14,182 | -2.6 | 57,585 -> 33,017 | PASS | 0.095 | 1.000 |
| M11 | AS | S1 | 4 | post-hoc | 12/15/9 of 16 | -21,250/-16,724 | -37,750/-33,017 | -33,859/-16,929 | 15,460/13,515 | 0.2 | 57,585 -> 39,625 | PASS | 0.085 | 1.000 |
| M11 | AS | S1 | 13 | post-hoc | 5/5/1 of 5 | -21,250/-18,502 | -37,750/-34,869 | -33,859/-16,929 | 15,460/9,043 | -32.3 | 57,585 -> 49,223 | FAIL | 0.445 | 1.000 |
| M11 | AS | S2 | 2 | quick | 7/11/9 of 32 | -3,189/-2,033 | -3,999/-2,771 | -2,455/-1,544 | 614/441 | -43.5 | 7,083 -> 6,560 | FAIL | 1.000 | 1.000 |
| M11 | AS | S2 | 4 | quick | 8/8/5 of 16 | -3,189/-2,033 | -3,999/-2,771 | -2,455/-1,544 | 628/448 | -43.6 | 7,083 -> 6,560 | FAIL | 0.855 | 1.000 |
| M11 | AS | S2 | 13 | quick | 4/4/1 of 5 | -3,189/-2,276 | -3,999/-2,771 | -2,455/-1,544 | 618/446 | -44.9 | 7,083 -> 7,083 | FAIL | 0.790 | 1.000 |
| M11 | LO | S1 | 2 | post-hoc | 28/28/10 of 32 | -39,760/-28,229 | -39,760/-28,229 | -20,695/-18,284 | 17,963/9,668 | -46.7 | 127,791 -> 63,895 | FAIL | 0.720 | 1.000 |
| M11 | LO | S1 | 4 | post-hoc | 13/13/2 of 16 | -39,760/-28,229 | -39,760/-28,229 | -20,695/-18,284 | 17,963/9,529 | -49.7 | 127,791 -> 63,895 | FAIL | 0.850 | 1.000 |
| M11 | LO | S1 | 13 | post-hoc | 4/4/2 of 5 | -39,760/-30,402 | -39,760/-30,402 | -20,695/-10,086 | 17,963/9,412 | -43.1 | 127,791 -> 63,895 | FAIL | 0.985 | 1.000 |
| M11 | LO | S2 | 2 | quick | 5/15/15 of 32 | -5,858/-5,858 | -5,858/-5,858 | -3,458/-3,458 | 133/98 | 80.4 | 8,389 -> 5,858 | FAIL | 0.205 | 1.000 |
| M11 | LO | S2 | 4 | quick | 9/11/9 of 16 | -5,858/-5,858 | -5,858/-5,858 | -3,458/-3,458 | 116/97 | 61.4 | 9,093 -> 5,858 | PASS | 0.525 | 1.000 |
| M11 | LO | S2 | 13 | quick | 1/2/2 of 5 | -5,858/-5,858 | -5,858/-5,858 | -3,458/-3,458 | 126/139 | 6.6 | 6,616 -> 5,869 | FAIL | 0.990 | 1.000 |
| M11 | NP | S1 | 2 | post-hoc | 25/26/10 of 32 | -26,269/-28,788 | -30,613/-28,788 | -23,047/-19,569 | 12,962/7,032 | -45.4 | 88,173 -> 72,831 | FAIL | 0.610 | 1.000 |
| M11 | NP | S1 | 4 | post-hoc | 12/13/5 of 16 | -26,269/-21,134 | -30,613/-21,134 | -23,047/-19,569 | 12,962/7,116 | -58.1 | 88,173 -> 62,926 | FAIL | 0.765 | 1.000 |
| M11 | NP | S1 | 13 | post-hoc | 3/3/1 of 5 | -26,269/-28,788 | -30,613/-28,788 | -23,047/-19,569 | 12,962/7,333 | -48.8 | 88,173 -> 62,380 | FAIL | 0.960 | 1.000 |
| M11 | NP | S2 | 2 | quick | 7/11/9 of 32 | -5,097/-5,030 | -12,126/-7,957 | -4,339/-2,559 | 189/-74 | -184.6 | 22,899 -> 17,426 | FAIL | 0.945 | 1.000 |
| M11 | NP | S2 | 4 | quick | 8/8/2 of 16 | -5,097/-5,465 | -10,865/-8,777 | -4,339/-3,442 | 245/-118 | -178.5 | 22,405 -> 19,118 | FAIL | 1.000 | 1.000 |
| M11 | NP | S2 | 13 | quick | 4/4/1 of 5 | -5,097/-2,906 | -12,126/-9,407 | -4,339/-3,442 | 125/-67 | -96.2 | 23,091 -> 15,032 | FAIL | 0.690 | 1.000 |
| M11 | NY | S1 | 2 | post-hoc | 29/29/8 of 32 | -69,974/-44,100 | -69,974/-44,100 | -59,414/-29,707 | 53,912/30,729 | -39.8 | 163,622 -> 83,497 | FAIL | 0.580 | 1.000 |
| M11 | NY | S1 | 4 | post-hoc | 15/15/4 of 16 | -69,974/-34,987 | -69,974/-34,987 | -59,414/-29,707 | 53,912/30,334 | -40.7 | 163,622 -> 83,497 | FAIL | 0.780 | 1.000 |
| M11 | NY | S1 | 13 | post-hoc | 5/5/1 of 5 | -69,974/-34,987 | -69,974/-34,987 | -59,414/-29,707 | 53,912/29,803 | -40.4 | 163,622 -> 82,044 | FAIL | 0.960 | 1.000 |
| M11 | NY | S2 | 2 | quick | 11/13/13 of 32 | -4,696/-2,348 | -9,115/-6,124 | -3,134/-3,134 | -73/12 | 30.8 | 20,874 -> 10,170 | FAIL | 0.540 | 1.000 |
| M11 | NY | S2 | 4 | quick | 10/10/5 of 16 | -4,696/-2,348 | -9,115/-6,590 | -3,172/-3,134 | -108/-24 | 297.5 | 21,801 -> 12,912 | FAIL | 0.550 | 1.000 |
| M11 | NY | S2 | 13 | quick | 2/2/1 of 5 | -4,696/-2,348 | -10,511/-8,766 | -3,134/-3,134 | -126/-128 | -65.7 | 22,269 -> 19,740 | FAIL | 0.995 | 1.000 |
| M2 | ALL | S1 | 2 | post-hoc | 47/47/28 of 77 | -24,954/-23,369 | -30,675/-28,756 | 44,148/35,659 | 100,297/84,325 | -11.4 | 215,625 -> 323,362 | FAIL | 0.034 | 1.000 |
| M2 | ALL | S1 | 4 | post-hoc | 25/25/14 of 39 | -34,805/-33,393 | -40,102/-36,229 | 13,538/11,969 | 110,236/91,391 | -11.3 | 215,625 -> 324,063 | FAIL | 0.054 | 1.000 |
| M2 | ALL | S1 | 13 | post-hoc | 5/5/3 of 12 | -38,773/-40,227 | -57,748/-63,955 | -38,407/-50,931 | 100,297/84,644 | -13.8 | 215,625 -> 305,548 | FAIL | 0.806 | 1.000 |
| M2 | ALL | S2 | 2 | quick | 33/38/30 of 77 | -4,650/-4,236 | -5,562/-4,670 | -3,828/-3,177 | 953/505 | -38.4 | 70,645 -> 61,531 | FAIL | 0.590 | 1.000 |
| M2 | ALL | S2 | 4 | quick | 22/22/11 of 39 | -9,300/-8,325 | -10,488/-8,707 | -7,821/-6,141 | 1,032/610 | -53.4 | 77,711 -> 65,487 | FAIL | 0.261 | 1.000 |
| M2 | ALL | S2 | 13 | quick | 10/10/3 of 12 | -17,456/-15,818 | -18,143/-15,801 | -11,131/-9,486 | 702/418 | -38.5 | 70,645 -> 62,585 | FAIL | 0.019 | 1.000 |
| M2 | AS | S1 | 2 | post-hoc | 42/42/31 of 77 | -16,563/-13,803 | -18,614/-15,230 | 1,096/1,019 | 15,460/13,306 | -14.0 | 67,941 -> 70,392 | FAIL | 0.247 | 1.000 |
| M2 | AS | S1 | 4 | post-hoc | 26/26/17 of 39 | -18,825/-15,693 | -20,191/-15,956 | -542/-960 | 16,600/13,780 | -14.6 | 67,941 -> 73,626 | FAIL | 0.027 | 1.000 |
| M2 | AS | S1 | 13 | post-hoc | 5/5/4 of 12 | -23,953/-18,198 | -30,852/-29,877 | -21,127/-18,333 | 15,460/14,867 | -14.8 | 67,941 -> 86,162 | FAIL | 0.806 | 1.000 |
| M2 | AS | S2 | 2 | quick | 37/43/37 of 77 | -5,154/-4,918 | -4,723/-4,353 | -247/-781 | 3,686/2,625 | -11.8 | 45,780 -> 41,323 | FAIL | 0.181 | 1.000 |
| M2 | AS | S2 | 4 | quick | 24/26/17 of 39 | -10,308/-9,674 | -10,233/-9,371 | -5,982/-5,519 | 3,138/2,529 | -9.5 | 42,499 -> 39,609 | PASS | 0.027 | 1.000 |
| M2 | AS | S2 | 13 | quick | 12/12/3 of 12 | -19,135/-17,009 | -21,563/-14,416 | -13,125/-9,466 | 3,710/2,581 | -19.1 | 42,499 -> 41,175 | FAIL | 2.0e-04 | 0.078 |
| M2 | LO | S1 | 2 | post-hoc | 32/32/39 of 77 | -23,428/-26,331 | -21,900/-25,041 | 1,708/-1,080 | 17,963/17,165 | -6.0 | 224,333 -> 233,977 | FAIL | 0.945 | 1.000 |
| M2 | LO | S1 | 4 | post-hoc | 16/16/20 of 39 | -34,479/-36,996 | -30,567/-35,286 | -9,330/-15,119 | 18,993/17,973 | -0.7 | 224,333 -> 233,977 | FAIL | 0.900 | 1.000 |
| M2 | LO | S1 | 13 | post-hoc | 4/4/7 of 12 | -39,760/-47,860 | -36,492/-41,813 | -20,434/-27,022 | 17,963/16,832 | 5.1 | 224,333 -> 222,040 | FAIL | 0.927 | 1.000 |
| M2 | LO | S2 | 2 | quick | 38/45/40 of 77 | -7,175/-6,349 | -5,599/-5,193 | -3,307/-3,390 | 796/133 | 0.2 | 76,946 -> 61,992 | FAIL | 0.086 | 1.000 |
| M2 | LO | S2 | 4 | quick | 26/28/22 of 39 | -14,349/-11,879 | -11,326/-10,110 | -6,563/-6,251 | 590/-167 | -8.1 | 113,538 -> 82,972 | PASS | 0.005 | 1.000 |
| M2 | LO | S2 | 13 | quick | 9/9/8 of 12 | -35,149/-26,703 | -27,221/-21,531 | -15,002/-13,139 | 755/621 | -90.4 | 80,703 -> 72,671 | PASS | 0.073 | 1.000 |
| M2 | NP | S1 | 2 | post-hoc | 42/42/39 of 77 | -14,529/-12,994 | -17,438/-15,714 | 2,154/3,728 | 12,962/13,536 | 10.0 | 134,363 -> 150,927 | FAIL | 0.247 | 1.000 |
| M2 | NP | S1 | 4 | post-hoc | 23/23/23 of 39 | -18,313/-14,858 | -21,780/-18,667 | -4,671/-1,440 | 13,684/14,444 | 14.2 | 134,363 -> 157,117 | FAIL | 0.168 | 1.000 |
| M2 | NP | S1 | 13 | post-hoc | 5/5/9 of 12 | -26,269/-27,854 | -28,441/-30,094 | -20,583/-14,110 | 12,962/13,107 | 13.9 | 134,363 -> 129,160 | FAIL | 0.806 | 1.000 |
| M2 | NP | S2 | 2 | quick | 39/42/32 of 77 | -9,889/-5,783 | -13,364/-5,350 | -9,009/-3,995 | 1,131/-631 | -69.8 | 137,396 -> 58,786 | FAIL | 0.247 | 1.000 |
| M2 | NP | S2 | 4 | quick | 23/25/17 of 39 | -16,540/-10,562 | -21,361/-9,657 | -15,413/-6,586 | 2,505/-444 | -85.7 | 134,431 -> 77,044 | FAIL | 0.054 | 1.000 |
| M2 | NP | S2 | 13 | quick | 8/8/3 of 12 | -30,581/-9,580 | -56,896/-20,731 | -20,694/-7,639 | 749/-292 | -76.9 | 138,549 -> 103,267 | FAIL | 0.194 | 1.000 |
| M2 | NY | S1 | 2 | post-hoc | 57/57/33 of 77 | -31,881/-27,753 | -38,750/-30,544 | 13,101/11,826 | 53,912/40,318 | -18.6 | 200,647 -> 175,857 | FAIL | <1e-12 | <1e-12 |
| M2 | NY | S1 | 4 | post-hoc | 31/31/11 of 39 | -48,897/-39,199 | -50,267/-39,604 | -6,092/-8,363 | 60,959/45,194 | -20.1 | 200,647 -> 188,100 | FAIL | 1.0e-04 | 0.039 |
| M2 | NY | S1 | 13 | post-hoc | 7/7/3 of 12 | -69,974/-59,539 | -68,773/-67,055 | -47,221/-44,421 | 53,912/39,837 | -26.6 | 200,647 -> 200,653 | FAIL | 0.387 | 1.000 |
| M2 | NY | S2 | 2 | quick | 34/37/27 of 77 | -9,280/-7,076 | -10,322/-7,527 | -7,841/-5,692 | -436/-695 | -49.6 | 125,241 -> 100,471 | FAIL | 0.676 | 1.000 |
| M2 | NY | S2 | 4 | quick | 17/17/13 of 39 | -18,560/-14,061 | -19,658/-14,337 | -13,459/-9,445 | -80/-470 | -69.1 | 130,809 -> 106,711 | FAIL | 0.832 | 1.000 |
| M2 | NY | S2 | 13 | quick | 9/9/4 of 12 | -28,174/-20,834 | -39,420/-28,287 | -16,902/-12,539 | -758/-967 | -53.5 | 133,613 -> 107,475 | FAIL | 0.073 | 1.000 |
| M3 | ALL | S1 | 2 | post-hoc | 36/36/36 of 77 | -24,954/-23,670 | -30,675/-29,070 | 44,148/33,620 | 100,297/87,579 | -8.8 | 215,625 -> 327,221 | FAIL | 0.753 | 1.000 |
| M3 | ALL | S1 | 4 | post-hoc | 20/20/18 of 39 | -34,805/-32,250 | -40,102/-37,492 | 13,538/14,137 | 110,236/94,150 | -9.4 | 215,625 -> 344,018 | FAIL | 0.500 | 1.000 |
| M3 | ALL | S1 | 13 | post-hoc | 5/5/7 of 12 | -38,773/-36,294 | -57,748/-59,167 | -38,407/-41,968 | 100,297/95,415 | -6.7 | 215,625 -> 345,465 | FAIL | 0.806 | 1.000 |
| M3 | ALL | S2 | 2 | quick | 29/35/34 of 77 | -4,650/-5,093 | -5,562/-4,392 | -3,828/-1,379 | 953/1,820 | -26.2 | 70,645 -> 48,770 | FAIL | 0.819 | 1.000 |
| M3 | ALL | S2 | 4 | quick | 19/19/20 of 39 | -9,300/-9,848 | -10,488/-9,284 | -7,821/-6,238 | 1,032/2,045 | -10.8 | 77,711 -> 58,579 | FAIL | 0.625 | 1.000 |
| M3 | ALL | S2 | 13 | quick | 7/7/8 of 12 | -17,456/-14,978 | -18,143/-16,114 | -11,131/-9,151 | 702/2,256 | 42.8 | 70,645 -> 51,471 | FAIL | 0.387 | 1.000 |
| M3 | AS | S1 | 2 | post-hoc | 38/38/39 of 77 | -16,563/-23,673 | -18,614/-28,775 | 1,096/-2,999 | 15,460/19,019 | -1.3 | 67,941 -> 104,918 | FAIL | 0.590 | 1.000 |
| M3 | AS | S1 | 4 | post-hoc | 20/20/16 of 39 | -18,825/-26,657 | -20,191/-35,239 | -542/-8,217 | 16,600/17,932 | -6.0 | 67,941 -> 136,681 | FAIL | 0.500 | 1.000 |
| M3 | AS | S1 | 13 | post-hoc | 7/7/6 of 12 | -23,953/-35,444 | -30,852/-47,172 | -21,127/-33,222 | 15,460/24,493 | 12.5 | 67,941 -> 88,766 | FAIL | 0.387 | 1.000 |
| M3 | AS | S2 | 2 | quick | 32/38/36 of 77 | -5,154/-2,191 | -4,723/-6,251 | -247/879 | 3,686/6,230 | 21.6 | 45,780 -> 73,367 | FAIL | 0.590 | 1.000 |
| M3 | AS | S2 | 4 | quick | 23/23/14 of 39 | -10,308/-4,757 | -10,233/-13,769 | -5,982/-9,103 | 3,138/5,800 | 6.3 | 42,499 -> 89,357 | FAIL | 0.168 | 1.000 |
| M3 | AS | S2 | 13 | quick | 10/10/4 of 12 | -19,135/-11,030 | -21,563/-26,771 | -13,125/-16,319 | 3,710/5,939 | -5.9 | 42,499 -> 42,513 | PASS | 0.019 | 1.000 |
| M3 | LO | S1 | 2 | post-hoc | 29/29/40 of 77 | -23,428/-25,716 | -21,900/-22,810 | 1,708/-1,540 | 17,963/16,810 | -7.6 | 224,333 -> 283,652 | FAIL | 0.989 | 1.000 |
| M3 | LO | S1 | 4 | post-hoc | 15/15/24 of 39 | -34,479/-39,347 | -30,567/-33,018 | -9,330/-13,193 | 18,993/16,943 | -8.0 | 224,333 -> 355,637 | FAIL | 0.946 | 1.000 |
| M3 | LO | S1 | 13 | post-hoc | 6/6/7 of 12 | -39,760/-31,123 | -36,492/-35,773 | -20,434/-22,247 | 17,963/16,642 | -25.1 | 224,333 -> 324,163 | FAIL | 0.613 | 1.000 |
| M3 | LO | S2 | 2 | quick | 13/26/38 of 77 | -7,175/-339,259 | -5,599/-215,402 | -3,307/-130,915 | 796/9,801 | 1,643.1 | 76,946 -> 1,707,853 | FAIL | 0.999 | 1.000 |
| M3 | LO | S2 | 4 | quick | 10/13/20 of 39 | -14,349/-672,950 | -11,326/-430,571 | -6,563/-256,327 | 590/17,807 | 529.2 | 113,538 -> 1,707,853 | FAIL | 0.988 | 1.000 |
| M3 | LO | S2 | 13 | quick | 4/4/8 of 12 | -35,149/-1,335,171 | -27,221/-939,308 | -15,002/-524,565 | 755/26,755 | -31.6 | 80,703 -> 1,335,171 | FAIL | 0.927 | 1.000 |
| M3 | NP | S1 | 2 | post-hoc | 34/35/39 of 77 | -14,529/-14,598 | -17,438/-15,343 | 2,154/1,925 | 12,962/12,619 | 1.7 | 134,363 -> 110,600 | FAIL | 0.819 | 1.000 |
| M3 | NP | S1 | 4 | post-hoc | 18/18/22 of 39 | -18,313/-18,341 | -21,780/-18,827 | -4,671/-3,950 | 13,684/13,387 | 5.3 | 134,363 -> 105,032 | FAIL | 0.739 | 1.000 |
| M3 | NP | S1 | 13 | post-hoc | 4/4/6 of 12 | -26,269/-35,031 | -28,441/-19,562 | -20,583/-11,937 | 12,962/8,796 | -18.6 | 134,363 -> 162,621 | FAIL | 0.927 | 1.000 |
| M3 | NP | S2 | 2 | quick | 8/25/34 of 77 | -9,889/-99,369 | -13,364/-51,301 | -9,009/-46,709 | 1,131/-15,578 | -736.5 | 137,396 -> 1,035,448 | FAIL | 0.999 | 1.000 |
| M3 | NP | S2 | 4 | quick | 6/9/18 of 39 | -16,540/-85,058 | -21,361/-42,747 | -15,413/-36,818 | 2,505/-6,397 | -229.2 | 134,431 -> 779,925 | FAIL | 1.000 | 1.000 |
| M3 | NP | S2 | 13 | quick | 0/0/9 of 12 | -30,581/-34,343 | -56,896/-60,942 | -20,694/-22,066 | 749/1,054 | 252.6 | 138,549 -> 293,520 | FAIL | 1.000 | 1.000 |
| M3 | NY | S1 | 2 | post-hoc | 52/52/32 of 77 | -31,881/-23,970 | -38,750/-32,271 | 13,101/5,686 | 53,912/39,131 | -14.3 | 200,647 -> 249,784 | FAIL | 0.001 | 0.543 |
| M3 | NY | S1 | 4 | post-hoc | 29/29/16 of 39 | -48,897/-37,736 | -50,267/-39,639 | -6,092/-5,249 | 60,959/45,888 | -14.6 | 200,647 -> 249,731 | FAIL | 0.002 | 0.660 |
| M3 | NY | S1 | 13 | post-hoc | 8/8/5 of 12 | -69,974/-44,711 | -68,773/-62,170 | -47,221/-47,178 | 53,912/45,484 | -3.5 | 200,647 -> 280,211 | PASS | 0.194 | 1.000 |
| M3 | NY | S2 | 2 | quick | 46/50/38 of 77 | -9,280/-4,139 | -10,322/-3,258 | -7,841/-2,036 | -436/-11 | -18.5 | 125,241 -> 68,041 | FAIL | 0.006 | 1.000 |
| M3 | NY | S2 | 4 | quick | 28/28/20 of 39 | -18,560/-8,577 | -19,658/-6,154 | -13,459/-4,477 | -80/162 | -18.5 | 130,809 -> 76,005 | FAIL | 0.005 | 1.000 |
| M3 | NY | S2 | 13 | quick | 8/8/7 of 12 | -28,174/-13,468 | -39,420/-13,032 | -16,902/-5,981 | -758/-21 | -1.6 | 133,613 -> 75,133 | PASS | 0.194 | 1.000 |
| M4 | AS | S1 | 2 | post-hoc | 75/75/27 of 77 | -/- | -/- | -/- | -/- | -48.1 | 67,941 -> 33,971 | FAIL | <1e-12 | <1e-12 |
| M4 | AS | S1 | 4 | post-hoc | 38/39/11 of 39 | -/- | -/- | -/- | -/- | -48.7 | 67,941 -> 33,971 | FAIL | 1.8e-12 | 7.1e-10 |
| M4 | AS | S1 | 13 | post-hoc | 11/11/1 of 12 | -/- | -/- | -/- | -/- | -49.4 | 67,941 -> 35,511 | FAIL | 0.003 | 1.000 |
| M4 | AS | S2 | 2 | quick | 21/26/19 of 77 | -/- | -/- | -/- | -/- | -48.3 | 7,630 -> 7,619 | FAIL | 0.999 | 1.000 |
| M4 | AS | S2 | 4 | quick | 19/19/5 of 39 | -/- | -/- | -/- | -/- | -34.9 | 7,083 -> 6,560 | FAIL | 0.625 | 1.000 |
| M4 | AS | S2 | 13 | quick | 6/7/3 of 12 | -/- | -/- | -/- | -/- | -16.7 | 7,083 -> 7,083 | FAIL | 0.613 | 1.000 |
| M4 | LO | S1 | 2 | post-hoc | 67/67/19 of 77 | -/- | -/- | -/- | -/- | -55.7 | 224,333 -> 118,415 | FAIL | 8.5e-12 | 3.3e-09 |
| M4 | LO | S1 | 4 | post-hoc | 33/34/10 of 39 | -/- | -/- | -/- | -/- | -47.3 | 224,333 -> 118,415 | FAIL | 1.2e-06 | 4.7e-04 |
| M4 | LO | S1 | 13 | post-hoc | 12/12/3 of 12 | -/- | -/- | -/- | -/- | -47.7 | 224,333 -> 118,415 | FAIL | 2.4e-04 | 0.095 |
| M4 | LO | S2 | 2 | quick | 13/27/26 of 77 | -/- | -/- | -/- | -/- | - | 12,211 -> 11,104 | FAIL | 0.997 | 1.000 |
| M4 | LO | S2 | 4 | quick | 17/17/14 of 39 | -/- | -/- | -/- | -/- | - | 17,452 -> 13,194 | FAIL | 0.832 | 1.000 |
| M4 | LO | S2 | 13 | quick | 6/6/3 of 12 | -/- | -/- | -/- | -/- | - | 11,940 -> 12,209 | FAIL | 0.613 | 1.000 |
| M4 | NP | S1 | 2 | post-hoc | 56/58/21 of 77 | -/- | -/- | -/- | -/- | -37.4 | 134,363 -> 77,909 | FAIL | 4.9e-06 | 0.002 |
| M4 | NP | S1 | 4 | post-hoc | 27/29/8 of 39 | -/- | -/- | -/- | -/- | -38.0 | 134,363 -> 67,181 | FAIL | 0.002 | 0.655 |
| M4 | NP | S1 | 13 | post-hoc | 9/9/2 of 12 | -/- | -/- | -/- | -/- | -45.4 | 134,363 -> 78,363 | FAIL | 0.073 | 1.000 |
| M4 | NP | S2 | 2 | quick | 31/40/32 of 77 | -/- | -/- | -/- | -/- | -51.5 | 22,899 -> 14,473 | FAIL | 0.410 | 1.000 |
| M4 | NP | S2 | 4 | quick | 28/29/14 of 39 | -/- | -/- | -/- | -/- | -65.3 | 22,405 -> 14,226 | FAIL | 0.002 | 0.655 |
| M4 | NP | S2 | 13 | quick | 10/10/4 of 12 | -/- | -/- | -/- | -/- | -55.2 | 23,091 -> 15,965 | FAIL | 0.019 | 1.000 |
| M4 | NY | S1 | 2 | post-hoc | 36/37/13 of 77 | -/- | -/- | -/- | -/- | -20.9 | 200,647 -> 163,622 | FAIL | 0.676 | 1.000 |
| M4 | NY | S1 | 4 | post-hoc | 20/21/6 of 39 | -/- | -/- | -/- | -/- | -22.2 | 200,647 -> 163,622 | FAIL | 0.375 | 1.000 |
| M4 | NY | S1 | 13 | post-hoc | 6/7/4 of 12 | -/- | -/- | -/- | -/- | -10.3 | 200,647 -> 163,622 | FAIL | 0.613 | 1.000 |
| M4 | NY | S2 | 2 | quick | 24/33/28 of 77 | -/- | -/- | -/- | -/- | -32.9 | 20,874 -> 12,250 | FAIL | 0.914 | 1.000 |
| M4 | NY | S2 | 4 | quick | 26/26/13 of 39 | -/- | -/- | -/- | -/- | -30.2 | 21,801 -> 12,714 | FAIL | 0.027 | 1.000 |
| M4 | NY | S2 | 13 | quick | 8/8/2 of 12 | -/- | -/- | -/- | -/- | -36.7 | 22,269 -> 18,063 | FAIL | 0.194 | 1.000 |
| M5 | AS | S1 | 2 | post-hoc | 69/69/29 of 77 | -/- | -/- | -/- | -/- | -63.5 | 67,941 -> 86,383 | FAIL | <1e-12 | <1e-12 |
| M5 | AS | S1 | 4 | post-hoc | 34/34/11 of 39 | -/- | -/- | -/- | -/- | -62.1 | 67,941 -> 86,383 | FAIL | <1e-12 | <1e-12 |
| M5 | AS | S1 | 13 | post-hoc | 12/12/2 of 12 | -/- | -/- | -/- | -/- | -62.2 | 67,941 -> 86,383 | FAIL | 2.0e-04 | 0.078 |
| M5 | LO | S1 | 2 | post-hoc | 66/66/23 of 77 | -/- | -/- | -/- | -/- | -62.2 | 224,333 -> 206,811 | FAIL | <1e-12 | <1e-12 |
| M5 | LO | S1 | 4 | post-hoc | 36/36/12 of 39 | -/- | -/- | -/- | -/- | -62.4 | 224,333 -> 206,811 | FAIL | <1e-12 | <1e-12 |
| M5 | LO | S1 | 13 | post-hoc | 10/10/3 of 12 | -/- | -/- | -/- | -/- | -64.3 | 224,333 -> 206,811 | FAIL | 0.019 | 1.000 |
| M5 | NP | S1 | 2 | post-hoc | 67/67/30 of 77 | -/- | -/- | -/- | -/- | -38.5 | 134,363 -> 56,216 | FAIL | <1e-12 | <1e-12 |
| M5 | NP | S1 | 4 | post-hoc | 35/35/15 of 39 | -/- | -/- | -/- | -/- | -35.4 | 134,363 -> 56,216 | FAIL | <1e-12 | <1e-12 |
| M5 | NP | S1 | 13 | post-hoc | 11/11/3 of 12 | -/- | -/- | -/- | -/- | -37.4 | 134,363 -> 56,216 | FAIL | 0.003 | 1.000 |
| M5 | NY | S1 | 2 | post-hoc | 46/46/37 of 77 | -/- | -/- | -/- | -/- | -5.5 | 200,647 -> 175,742 | FAIL | 0.055 | 1.000 |
| M5 | NY | S1 | 4 | post-hoc | 27/27/18 of 39 | -/- | -/- | -/- | -/- | -4.3 | 200,647 -> 175,742 | PASS | 0.012 | 1.000 |
| M5 | NY | S1 | 13 | post-hoc | 7/7/6 of 12 | -/- | -/- | -/- | -/- | -5.7 | 200,647 -> 175,742 | FAIL | 0.387 | 1.000 |
| M6 | AS | S1 | 2 | post-hoc | 39/39/43 of 77 | -/- | -/- | -/- | -/- | 5.8 | 67,941 -> 52,572 | FAIL | 0.138 | 1.000 |
| M6 | AS | S1 | 4 | post-hoc | 27/27/21 of 39 | -/- | -/- | -/- | -/- | 7.8 | 67,941 -> 52,572 | PASS | 0.007 | 1.000 |
| M6 | AS | S1 | 13 | post-hoc | 8/8/7 of 12 | -/- | -/- | -/- | -/- | 6.4 | 67,941 -> 52,572 | PASS | 0.194 | 1.000 |
| M6 | LO | S1 | 2 | post-hoc | 54/54/29 of 77 | -/- | -/- | -/- | -/- | -28.8 | 224,333 -> 212,905 | FAIL | 3.0e-04 | 0.116 |
| M6 | LO | S1 | 4 | post-hoc | 28/28/15 of 39 | -/- | -/- | -/- | -/- | -26.3 | 224,333 -> 212,905 | FAIL | 0.005 | 1.000 |
| M6 | LO | S1 | 13 | post-hoc | 9/9/4 of 12 | -/- | -/- | -/- | -/- | -28.6 | 224,333 -> 212,905 | FAIL | 0.073 | 1.000 |
| M6 | NP | S1 | 2 | post-hoc | 44/44/31 of 77 | -/- | -/- | -/- | -/- | -52.1 | 134,363 -> 116,217 | FAIL | 0.103 | 1.000 |
| M6 | NP | S1 | 4 | post-hoc | 24/24/12 of 39 | -/- | -/- | -/- | -/- | -56.7 | 134,363 -> 116,217 | FAIL | 0.100 | 1.000 |
| M6 | NP | S1 | 13 | post-hoc | 5/5/2 of 12 | -/- | -/- | -/- | -/- | -52.3 | 134,363 -> 116,217 | FAIL | 0.806 | 1.000 |
| M6 | NY | S1 | 2 | post-hoc | 51/51/36 of 77 | -/- | -/- | -/- | -/- | -5.7 | 200,647 -> 185,849 | FAIL | 0.001 | 0.466 |
| M6 | NY | S1 | 4 | post-hoc | 25/25/16 of 39 | -/- | -/- | -/- | -/- | -3.8 | 200,647 -> 185,849 | FAIL | 0.024 | 1.000 |
| M6 | NY | S1 | 13 | post-hoc | 9/9/4 of 12 | -/- | -/- | -/- | -/- | -5.6 | 200,647 -> 185,849 | PASS | 0.073 | 1.000 |
| M7 | AS | S1 | 2 | post-hoc | 36/36/24 of 77 | -/- | -/- | -/- | -/- | -26.5 | 67,941 -> 125,467 | FAIL | 0.753 | 1.000 |
| M7 | AS | S1 | 4 | post-hoc | 22/22/11 of 39 | -/- | -/- | -/- | -/- | -24.0 | 67,941 -> 101,035 | FAIL | 0.261 | 1.000 |
| M7 | AS | S1 | 13 | post-hoc | 8/8/3 of 12 | -/- | -/- | -/- | -/- | -22.1 | 67,941 -> 97,379 | FAIL | 0.194 | 1.000 |
| M7 | AS | S2 | 2 | post-hoc | 36/36/34 of 76 | -/- | -/- | -/- | -/- | -4.3 | 15,347 -> 10,750 | FAIL | 0.717 | 1.000 |
| M7 | AS | S2 | 4 | post-hoc | 19/19/18 of 38 | -/- | -/- | -/- | -/- | -4.2 | 15,347 -> 10,750 | FAIL | 0.564 | 1.000 |
| M7 | AS | S2 | 13 | post-hoc | 8/8/8 of 11 | -/- | -/- | -/- | -/- | 18.1 | 15,347 -> 10,003 | PASS | 0.113 | 1.000 |
| M7 | LO | S1 | 2 | post-hoc | 29/29/20 of 77 | -/- | -/- | -/- | -/- | -31.7 | 224,333 -> 180,503 | FAIL | 0.989 | 1.000 |
| M7 | LO | S1 | 4 | post-hoc | 17/17/11 of 39 | -/- | -/- | -/- | -/- | -32.2 | 224,333 -> 164,321 | FAIL | 0.832 | 1.000 |
| M7 | LO | S1 | 13 | post-hoc | 7/7/4 of 12 | -/- | -/- | -/- | -/- | -13.3 | 224,333 -> 124,548 | FAIL | 0.387 | 1.000 |
| M7 | LO | S2 | 2 | post-hoc | 50/50/38 of 76 | -/- | -/- | -/- | -/- | -78.2 | 14,554 -> 17,738 | FAIL | 0.004 | 1.000 |
| M7 | LO | S2 | 4 | post-hoc | 31/31/22 of 38 | -/- | -/- | -/- | -/- | -122.7 | 14,505 -> 13,710 | PASS | 5.8e-05 | 0.023 |
| M7 | LO | S2 | 13 | post-hoc | 10/10/8 of 11 | -/- | -/- | -/- | -/- | -113.7 | 14,464 -> 13,465 | PASS | 0.006 | 1.000 |
| M7 | NP | S1 | 2 | post-hoc | 35/35/28 of 77 | -/- | -/- | -/- | -/- | -8.6 | 134,363 -> 144,976 | FAIL | 0.819 | 1.000 |
| M7 | NP | S1 | 4 | post-hoc | 21/21/14 of 39 | -/- | -/- | -/- | -/- | -17.5 | 134,363 -> 152,910 | FAIL | 0.375 | 1.000 |
| M7 | NP | S1 | 13 | post-hoc | 6/6/1 of 12 | -/- | -/- | -/- | -/- | -25.8 | 134,363 -> 152,910 | FAIL | 0.613 | 1.000 |
| M7 | NP | S2 | 2 | post-hoc | 44/44/34 of 76 | -/- | -/- | -/- | -/- | -109.8 | 22,890 -> 24,873 | FAIL | 0.103 | 1.000 |
| M7 | NP | S2 | 4 | post-hoc | 24/24/14 of 38 | -/- | -/- | -/- | -/- | -105.4 | 22,890 -> 21,653 | FAIL | 0.072 | 1.000 |
| M7 | NP | S2 | 13 | post-hoc | 9/9/3 of 11 | -/- | -/- | -/- | -/- | -135.2 | 22,890 -> 26,783 | FAIL | 0.033 | 1.000 |
| M7 | NY | S1 | 2 | post-hoc | 30/30/26 of 77 | -/- | -/- | -/- | -/- | -6.6 | 200,647 -> 205,579 | FAIL | 0.980 | 1.000 |
| M7 | NY | S1 | 4 | post-hoc | 14/14/10 of 39 | -/- | -/- | -/- | -/- | -12.7 | 200,647 -> 205,579 | FAIL | 0.973 | 1.000 |
| M7 | NY | S1 | 13 | post-hoc | 4/4/3 of 12 | -/- | -/- | -/- | -/- | -17.5 | 200,647 -> 205,579 | FAIL | 0.927 | 1.000 |
| M7 | NY | S2 | 2 | post-hoc | 34/34/30 of 76 | -/- | -/- | -/- | -/- | 7.9 | 18,432 -> 13,101 | FAIL | 0.849 | 1.000 |
| M7 | NY | S2 | 4 | post-hoc | 18/18/18 of 38 | -/- | -/- | -/- | -/- | 9.0 | 18,432 -> 13,101 | FAIL | 0.686 | 1.000 |
| M7 | NY | S2 | 13 | post-hoc | 5/5/6 of 11 | -/- | -/- | -/- | -/- | 11.9 | 18,432 -> 13,101 | FAIL | 0.726 | 1.000 |
| M8 | AS | S1 | 2 | post-hoc | 58/58/38 of 77 | -/- | -/- | -/- | -/- | -21.2 | 67,941 -> 63,345 | FAIL | 4.9e-06 | 0.002 |
| M8 | AS | S1 | 4 | post-hoc | 31/31/19 of 39 | -/- | -/- | -/- | -/- | -20.0 | 67,941 -> 65,635 | FAIL | 1.5e-04 | 0.057 |
| M8 | AS | S1 | 13 | post-hoc | 8/8/3 of 12 | -/- | -/- | -/- | -/- | -22.7 | 67,941 -> 85,539 | FAIL | 0.194 | 1.000 |
| M8 | AS | S2 | 2 | post-hoc | 59/59/36 of 76 | -/- | -/- | -/- | -/- | -20.9 | 15,347 -> 12,049 | FAIL | 7.0e-07 | 2.7e-04 |
| M8 | AS | S2 | 4 | post-hoc | 31/31/19 of 38 | -/- | -/- | -/- | -/- | -26.8 | 15,347 -> 13,794 | FAIL | 5.8e-05 | 0.023 |
| M8 | AS | S2 | 13 | post-hoc | 9/9/4 of 11 | -/- | -/- | -/- | -/- | -19.4 | 15,347 -> 12,235 | FAIL | 0.033 | 1.000 |
| M8 | LO | S1 | 2 | post-hoc | 36/36/30 of 77 | -/- | -/- | -/- | -/- | -14.3 | 224,333 -> 211,942 | FAIL | 0.753 | 1.000 |
| M8 | LO | S1 | 4 | post-hoc | 20/20/15 of 39 | -/- | -/- | -/- | -/- | -20.9 | 224,333 -> 237,835 | FAIL | 0.500 | 1.000 |
| M8 | LO | S1 | 13 | post-hoc | 7/7/3 of 12 | -/- | -/- | -/- | -/- | -28.9 | 224,333 -> 265,830 | FAIL | 0.387 | 1.000 |
| M8 | LO | S2 | 2 | post-hoc | 53/53/40 of 76 | -/- | -/- | -/- | -/- | -34.1 | 14,554 -> 11,938 | PASS | 3.8e-04 | 0.148 |
| M8 | LO | S2 | 4 | post-hoc | 31/31/20 of 38 | -/- | -/- | -/- | -/- | -48.9 | 14,505 -> 12,470 | PASS | 5.8e-05 | 0.023 |
| M8 | LO | S2 | 13 | post-hoc | 9/9/4 of 11 | -/- | -/- | -/- | -/- | 46.4 | 14,464 -> 16,904 | FAIL | 0.033 | 1.000 |
| M8 | NP | S1 | 2 | post-hoc | 52/52/41 of 77 | -/- | -/- | -/- | -/- | -8.2 | 134,363 -> 152,013 | PASS | 0.001 | 0.543 |
| M8 | NP | S1 | 4 | post-hoc | 23/23/17 of 39 | -/- | -/- | -/- | -/- | -4.9 | 134,363 -> 152,013 | FAIL | 0.168 | 1.000 |
| M8 | NP | S1 | 13 | post-hoc | 7/7/4 of 12 | -/- | -/- | -/- | -/- | -14.1 | 134,363 -> 152,013 | FAIL | 0.387 | 1.000 |
| M8 | NP | S2 | 2 | post-hoc | 50/50/44 of 76 | -/- | -/- | -/- | -/- | -20.3 | 22,890 -> 13,159 | FAIL | 0.004 | 1.000 |
| M8 | NP | S2 | 4 | post-hoc | 26/26/22 of 38 | -/- | -/- | -/- | -/- | -5.8 | 22,890 -> 14,443 | PASS | 0.017 | 1.000 |
| M8 | NP | S2 | 13 | post-hoc | 5/5/5 of 11 | -/- | -/- | -/- | -/- | -14.9 | 22,890 -> 15,844 | FAIL | 0.726 | 1.000 |
| M8 | NY | S1 | 2 | post-hoc | 44/44/37 of 77 | -/- | -/- | -/- | -/- | -1.3 | 200,647 -> 200,578 | FAIL | 0.127 | 1.000 |
| M8 | NY | S1 | 4 | post-hoc | 25/25/20 of 39 | -/- | -/- | -/- | -/- | -1.9 | 200,647 -> 200,578 | FAIL | 0.054 | 1.000 |
| M8 | NY | S1 | 13 | post-hoc | 10/10/6 of 12 | -/- | -/- | -/- | -/- | -2.1 | 200,647 -> 200,578 | PASS | 0.019 | 1.000 |
| M8 | NY | S2 | 2 | post-hoc | 53/53/33 of 76 | -/- | -/- | -/- | -/- | -11.0 | 18,432 -> 17,718 | FAIL | 3.8e-04 | 0.148 |
| M8 | NY | S2 | 4 | post-hoc | 24/24/16 of 38 | -/- | -/- | -/- | -/- | -5.2 | 18,432 -> 17,830 | FAIL | 0.072 | 1.000 |
| M8 | NY | S2 | 13 | post-hoc | 7/7/6 of 11 | -/- | -/- | -/- | -/- | -17.2 | 18,432 -> 15,729 | FAIL | 0.274 | 1.000 |
| M9 | ALL | S1 | 2 | quick | 11/29/29 of 77 | -15,650/-36,091 | -15,650/-41,779 | -15,650/-21,427 | 501,747/185,737 | -33.2 | 60,062 -> 43,846 | FAIL | 0.989 | 1.000 |
| M9 | ALL | S1 | 4 | quick | 16/19/13 of 39 | -15,650/-36,091 | -15,650/-41,790 | -15,650/-21,427 | 501,747/183,066 | -34.3 | 60,062 -> 41,790 | FAIL | 0.625 | 1.000 |
| M9 | ALL | S1 | 13 | quick | 7/7/4 of 12 | -15,650/-36,091 | -15,650/-42,631 | -15,650/-21,427 | 501,747/187,932 | -32.3 | 60,062 -> 42,631 | FAIL | 0.387 | 1.000 |
| M9 | ALL | S2 | 2 | quick | 17/40/43 of 77 | -8,731/-5,700 | -9,692/-5,700 | -6,351/-4,831 | 21,456/29,948 | 50.4 | 33,036 -> 8,338 | FAIL | 0.410 | 1.000 |
| M9 | ALL | S2 | 4 | quick | 16/19/18 of 39 | -8,731/-5,648 | -8,731/-5,648 | -6,351/-4,831 | 22,746/28,734 | 64.2 | 31,746 -> 8,221 | FAIL | 0.625 | 1.000 |
| M9 | ALL | S2 | 13 | quick | 7/7/7 of 12 | -8,731/-5,684 | -9,692/-5,684 | -6,351/-4,831 | 17,601/29,713 | 48.9 | 33,036 -> 8,128 | FAIL | 0.387 | 1.000 |
| M9 | AS | S1 | 2 | quick | 13/30/27 of 77 | -4,003/-10,777 | -4,003/-18,450 | -3,575/-6,837 | 69,624/10,693 | -43.6 | 14,492 -> 18,450 | FAIL | 0.980 | 1.000 |
| M9 | AS | S1 | 4 | quick | 16/20/12 of 39 | -4,003/-10,794 | -4,003/-18,468 | -3,575/-6,837 | 69,624/10,624 | -46.0 | 14,492 -> 18,468 | FAIL | 0.500 | 1.000 |
| M9 | AS | S1 | 13 | quick | 5/5/3 of 12 | -4,003/-10,947 | -4,003/-18,621 | -3,575/-6,837 | 69,624/8,533 | -44.3 | 14,492 -> 18,621 | FAIL | 0.806 | 1.000 |
| M9 | AS | S2 | 2 | quick | 21/33/30 of 77 | -2,999/-2,147 | -4,116/-4,345 | -2,628/-2,912 | 15,001/8,182 | -14.7 | 7,177 -> 5,862 | FAIL | 0.914 | 1.000 |
| M9 | AS | S2 | 4 | quick | 18/20/18 of 39 | -2,999/-2,147 | -4,116/-4,345 | -2,628/-2,912 | 15,677/8,535 | -19.9 | 7,177 -> 5,872 | FAIL | 0.500 | 1.000 |
| M9 | AS | S2 | 13 | quick | 9/9/5 of 12 | -2,999/-2,146 | -4,116/-4,391 | -2,628/-2,947 | 15,040/7,428 | -18.6 | 7,177 -> 5,940 | FAIL | 0.073 | 1.000 |
| M9 | LO | S1 | 2 | quick | 17/39/32 of 77 | -7,379/-10,933 | -8,437/-10,933 | -8,437/-8,100 | 74,462/43,980 | -20.1 | 28,293 -> 16,918 | FAIL | 0.500 | 1.000 |
| M9 | LO | S1 | 4 | quick | 21/24/16 of 39 | -7,379/-10,918 | -8,437/-10,918 | -8,437/-8,099 | 74,462/43,083 | -20.6 | 28,293 -> 16,904 | FAIL | 0.100 | 1.000 |
| M9 | LO | S1 | 13 | quick | 7/7/7 of 12 | -7,379/-7,713 | -8,437/-7,713 | -8,437/-7,398 | 74,462/50,381 | -15.3 | 28,293 -> 15,910 | FAIL | 0.387 | 1.000 |
| M9 | LO | S2 | 2 | quick | 22/45/42 of 77 | -5,342/-2,135 | -5,342/-3,065 | -2,731/-1,259 | 4,665/6,431 | 109.8 | 12,620 -> 7,423 | FAIL | 0.086 | 1.000 |
| M9 | LO | S2 | 4 | quick | 21/22/21 of 39 | -5,342/-2,135 | -5,342/-3,065 | -2,731/-1,259 | 4,490/5,672 | 48.4 | 19,640 -> 12,903 | FAIL | 0.261 | 1.000 |
| M9 | LO | S2 | 13 | quick | 11/11/9 of 12 | -5,342/-2,151 | -5,342/-3,052 | -2,731/-1,257 | 4,592/7,494 | 138.2 | 13,010 -> 8,024 | PASS | 0.003 | 1.000 |
| M9 | NP | S1 | 2 | quick | 21/39/35 of 77 | -5,035/-1,320 | -5,035/-16,108 | -5,426/-14,248 | 97,471/51,107 | -36.2 | 33,512 -> 48,398 | FAIL | 0.500 | 1.000 |
| M9 | NP | S1 | 4 | quick | 21/22/17 of 39 | -5,035/-1,320 | -5,035/-16,106 | -5,426/-14,248 | 97,471/50,557 | -41.0 | 33,512 -> 48,386 | FAIL | 0.261 | 1.000 |
| M9 | NP | S1 | 13 | quick | 4/4/4 of 12 | -5,035/-1,320 | -5,035/-16,100 | -5,426/-14,248 | 97,471/49,310 | -34.7 | 33,512 -> 47,146 | FAIL | 0.927 | 1.000 |
| M9 | NP | S2 | 2 | quick | 29/42/40 of 77 | -2,871/-2,713 | -10,582/-3,323 | -4,221/-2,404 | 4,299/11,868 | 54.9 | 20,989 -> 6,800 | FAIL | 0.247 | 1.000 |
| M9 | NP | S2 | 4 | quick | 21/23/21 of 39 | -2,871/-2,709 | -9,978/-3,312 | -4,221/-2,393 | 6,001/11,544 | 108.2 | 20,635 -> 6,151 | FAIL | 0.168 | 1.000 |
| M9 | NP | S2 | 13 | quick | 9/9/7 of 12 | -2,871/-2,694 | -10,582/-3,531 | -4,221/-2,381 | 2,000/11,397 | 42.8 | 20,989 -> 6,774 | PASS | 0.073 | 1.000 |
| M9 | NY | S1 | 2 | quick | 20/37/37 of 77 | -25,303/-26,878 | -25,303/-26,878 | -25,303/-20,073 | 260,190/79,958 | -32.9 | 53,761 -> 33,948 | FAIL | 0.676 | 1.000 |
| M9 | NY | S1 | 4 | quick | 19/20/21 of 39 | -25,303/-26,878 | -25,303/-26,878 | -25,303/-20,073 | 260,190/78,802 | -32.4 | 53,761 -> 32,002 | FAIL | 0.500 | 1.000 |
| M9 | NY | S1 | 13 | quick | 7/7/6 of 12 | -25,303/-26,878 | -25,303/-26,878 | -25,303/-20,073 | 260,190/79,708 | -33.3 | 53,761 -> 32,177 | FAIL | 0.387 | 1.000 |
| M9 | NY | S2 | 2 | quick | 20/40/39 of 77 | -4,498/-3,264 | -7,851/-3,299 | -2,836/-2,630 | -2,509/3,467 | 66.6 | 19,583 -> 6,007 | FAIL | 0.410 | 1.000 |
| M9 | NY | S2 | 4 | quick | 18/21/21 of 39 | -4,498/-3,264 | -7,851/-3,277 | -3,223/-2,630 | -3,422/2,983 | 83.0 | 20,496 -> 6,539 | FAIL | 0.375 | 1.000 |
| M9 | NY | S2 | 13 | quick | 8/8/7 of 12 | -4,498/-3,264 | -9,372/-3,846 | -2,836/-2,630 | -4,030/3,394 | 73.4 | 21,104 -> 6,347 | PASS | 0.194 | 1.000 |

FAIL reference rows (1094) are in the feed only; count above. Conventions: U = untouched subject, T = treated; $ at the subject's own lots (S1) or 1 lot per cell (S2/quick), so $ across rows are not comparable. DYNEXIT l3m/l6m lists read as [treated, untouched]. Re-run: `cd <repo>/outputs && python3 code/wf_scoreboard/build.py`.

