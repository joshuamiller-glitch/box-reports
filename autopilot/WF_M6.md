# WF M6: family agreement (S1 live mixes, post-hoc on exact per-trade TRADES), W-WF56, 2026-11-27

## ANSWER FIRST
- **Asia is a PASS candidate at steps 4 and 13 (FAIL at step 2: 45/77 good = 58%); NY AM PASS at step 13 only; London and NY PM FAIL everywhere.** Primary = k = half of the book's near-twins (ceil), twin = same session, module, variant, bar type, with ONE neighbouring parameter step or adjacent bar size, same other params; twin "on the same side" = its latest signal in the same session (within 10 h, up to this entry) has the book's side. Books with no twin are left unfiltered. Structural rule, nothing fitted per step.
- Drawdown first, Asia: chained OOS max DD -52,572 vs untouched -67,941 (23% shallower) with chained income 905,455 vs 850,174 (+6%); 90% of trades kept (7.0 -> 6.3 per day). Step 4: 28 of 39 periods good (27 shallower), income +7.8%, plain p 0.007; step 13: 8 of 12 shallower, income +6.4%, p 0.19; step 2: 45 of 77 good, FAIL on the two-thirds rule. Versus a same-count random-skip null (200 draws): null chained DD mean -71,477 (null never as shallow, p 0.00), null income 795,601 (p 0.01): the effect is not a trade-count effect.
- NY AM: PASS only at step 13 (9/12 shallower, income -5.6%, chained DD -185,849 vs -200,647); null p 0.40 for chained DD: not distinguishable from random skipping. FAIL at steps 2 and 4.
- London: DD shallower only because 55% of trades are dropped (income -29%). NY PM: income -52 to -57%. Both FAIL.
- Re-fit variant (ref:kfit: k chosen among none / one / half / all by trailing 26-week income per drawdown at each step) FAILs everywhere: refitting k made it worse, so Josh's faster-refit idea does not help M6; the static half rule is the best version, and step 4 is the best step for Asia.
- Weak points to hold against the Asia result: (1) twin signals are regenerated from the grid's signal_fn on neighbour params/sizes, not stored events; self-signal match to the live trades is 100% for 11 of 17 books but only 53% / 28% / 28% / 27% / 69% / 84% / 86% for Asia MF2, Asia MF4, London MF3, NY AM MF2, MF8, London MF1, NY MF3 (those books' twin states are partly wrong). (2) Asia has 4 live books (1,963 / 638 / 2,602 / 908 trades) so a few books drive it. (3) In-sample books, post-hoc. Not run: S2, pessimistic re-score (Asia M6 step 4/13 should get it next, plus an exact engine run via filtered events).

## Table (S1, post-hoc; step 2 first inside each row)
| session | version | trades/day U -> T | chained OOS max DD U / T | chained income U / T | step 2 | step 4 | step 13 |
|---|---|---|---|---|---|---|---|
| Asia | primary | 7.0 -> 6.3 | -67941 / -52572 | 850174 / 905455 | FAIL 39/77 (good 45), inc +6%, p 0.137 | PASS 27/39 (good 28), inc +8%, p 0.007 | PASS 8/12 (good 8), inc +6%, p 0.194 |
| Asia | ref:k1 | 7.0 -> 7.0 | -67941 / -65196 | 850174 / 849835 | FAIL 6/77 (good 8), inc -0%, p 0.500 | FAIL 7/39 (good 9), inc -0%, p 0.172 | FAIL 5/12 (good 6), inc -0%, p 0.109 |
| Asia | ref:kall | 7.0 -> 2.3 | -67941 / -51295 | 850174 / 418242 | FAIL 69/77 (good 69), inc -50%, p 0.000 | FAIL 34/39 (good 34), inc -50%, p 0.000 | FAIL 11/12 (good 11), inc -51%, p 0.003 |
| Asia | ref:oppblock | 7.0 -> 7.0 | -67941 / -65198 | 850174 / 855003 | FAIL 9/77 (good 19), inc +1%, p 0.212 | FAIL 9/39 (good 14), inc +1%, p 0.212 | FAIL 4/12 (good 7), inc +0%, p 0.344 |
| Asia | ref:kfit | 7.0 -> 5.0 | -67941 / -69974 | 850174 / 599133 | FAIL 28/77 (good 31), inc -29%, p 0.156 | FAIL 19/39 (good 19), inc -12%, p 0.014 | FAIL 5/12 (good 5), inc -26%, p 0.363 |
| London | primary | 7.0 -> 3.2 | -224332 / -212904 | 784923 / 562172 | FAIL 54/77 (good 54), inc -29%, p 0.000 | FAIL 28/39 (good 28), inc -26%, p 0.005 | FAIL 9/12 (good 9), inc -29%, p 0.073 |
| London | ref:k1 | 7.0 -> 5.0 | -224332 / -220986 | 784923 / 454939 | FAIL 43/77 (good 43), inc -42%, p 0.124 | FAIL 24/39 (good 24), inc -40%, p 0.100 | FAIL 9/12 (good 9), inc -41%, p 0.073 |
| London | ref:kall | 7.0 -> 1.2 | -224332 / -202202 | 784923 / 46184 | FAIL 68/77 (good 68), inc -95%, p 0.000 | FAIL 35/39 (good 35), inc -94%, p 0.000 | FAIL 11/12 (good 11), inc -95%, p 0.003 |
| London | ref:oppblock | 7.0 -> 5.9 | -224332 / -211678 | 784923 / 726488 | FAIL 31/77 (good 34), inc -7%, p 0.298 | FAIL 21/39 (good 21), inc -4%, p 0.081 | FAIL 6/12 (good 6), inc -8%, p 0.613 |
| London | ref:kfit | 7.0 -> 4.5 | -224332 / -241416 | 784923 / 550158 | FAIL 39/77 (good 39), inc -29%, p 0.000 | FAIL 21/39 (good 21), inc -19%, p 0.001 | FAIL 7/12 (good 7), inc -18%, p 0.035 |
| NY AM | primary | 18.3 -> 16.2 | -200647 / -185849 | 3102035 / 2917887 | FAIL 51/77 (good 51), inc -6%, p 0.001 | FAIL 25/39 (good 25), inc -4%, p 0.024 | PASS 9/12 (good 9), inc -6%, p 0.073 |
| NY AM | ref:k1 | 18.3 -> 17.4 | -200647 / -198443 | 3102035 / 3040712 | FAIL 39/77 (good 44), inc -2%, p 0.088 | FAIL 22/39 (good 22), inc -0%, p 0.162 | PASS 8/12 (good 8), inc -2%, p 0.194 |
| NY AM | ref:kall | 18.3 -> 9.6 | -200647 / -201146 | 3102035 / 1185965 | FAIL 56/77 (good 56), inc -62%, p 0.000 | FAIL 30/39 (good 30), inc -62%, p 0.001 | FAIL 8/12 (good 8), inc -61%, p 0.194 |
| NY AM | ref:oppblock | 18.3 -> 17.6 | -200647 / -199734 | 3102035 / 3114917 | FAIL 36/77 (good 44), inc +1%, p 0.078 | FAIL 20/39 (good 21), inc +1%, p 0.250 | FAIL 6/12 (good 7), inc +1%, p 0.500 |
| NY AM | ref:kfit | 18.3 -> 17.2 | -200647 / -208970 | 3102035 / 2880760 | FAIL 22/77 (good 25), inc -7%, p 0.318 | FAIL 13/39 (good 13), inc -7%, p 0.339 | FAIL 4/12 (good 4), inc -8%, p 0.500 |
| NY PM | primary | 8.0 -> 6.2 | -134362 / -116216 | 940694 / 467351 | FAIL 44/77 (good 44), inc -52%, p 0.103 | FAIL 24/39 (good 24), inc -57%, p 0.100 | FAIL 5/12 (good 5), inc -52%, p 0.806 |
| NY PM | ref:k1 | 8.0 -> 7.4 | -134362 / -121571 | 940694 / 764606 | FAIL 38/77 (good 42), inc -18%, p 0.026 | FAIL 25/39 (good 26), inc -18%, p 0.014 | FAIL 7/12 (good 8), inc -18%, p 0.274 |
| NY PM | ref:kall | 8.0 -> 2.8 | -134362 / -92808 | 940694 / 210963 | FAIL 52/77 (good 52), inc -79%, p 0.001 | FAIL 29/39 (good 29), inc -82%, p 0.002 | FAIL 7/12 (good 7), inc -79%, p 0.387 |
| NY PM | ref:oppblock | 8.0 -> 7.5 | -134362 / -127291 | 940694 / 906237 | FAIL 31/77 (good 35), inc -4%, p 0.397 | FAIL 17/39 (good 20), inc -4%, p 0.568 | FAIL 7/12 (good 7), inc -5%, p 0.274 |
| NY PM | ref:kfit | 8.0 -> 7.7 | -134362 / -134362 | 940694 / 889717 | FAIL 15/77 (good 16), inc -4%, p 0.067 | FAIL 8/39 (good 8), inc -1%, p 0.291 | FAIL 1/12 (good 1), inc -6%, p 0.938 |

## Random-skip null (200 draws; primary)
- AS step 2: chained DD -52572 vs null mean -71477 (p 0.00); income 905455 vs null 795601 (p 0.01); ratio p 0.00; periods shallower 39 vs null 39.0 (p 0.56); null PASS rate 0.03
- AS step 4: chained DD -52572 vs null mean -71321 (p 0.00); income 905455 vs null 795513 (p 0.01); ratio p 0.00; periods shallower 27 vs null 22.0 (p 0.03); null PASS rate 0.17
- AS step 13: chained DD -52572 vs null mean -72967 (p 0.00); income 905455 vs null 786887 (p 0.01); ratio p 0.00; periods shallower 8 vs null 7.3 (p 0.46); null PASS rate 0.34
- LO step 2: chained DD -212904 vs null mean -160190 (p 0.93); income 562172 vs null 549507 (p 0.45); ratio p 0.82; periods shallower 54 vs null 50.6 (p 0.18); null PASS rate 0.04
- LO step 4: chained DD -212904 vs null mean -158003 (p 0.93); income 562172 vs null 550803 (p 0.48); ratio p 0.81; periods shallower 28 vs null 26.2 (p 0.26); null PASS rate 0.03
- LO step 13: chained DD -212904 vs null mean -154855 (p 0.95); income 562172 vs null 560623 (p 0.48); ratio p 0.85; periods shallower 9 vs null 9.3 (p 0.79); null PASS rate 0.04
- NY step 2: chained DD -185849 vs null mean -197933 (p 0.37); income 2917887 vs null 2787742 (p 0.18); ratio p 0.28; periods shallower 51 vs null 44.8 (p 0.05); null PASS rate 0.03
- NY step 4: chained DD -185849 vs null mean -193434 (p 0.40); income 2917887 vs null 2756860 (p 0.12); ratio p 0.29; periods shallower 25 vs null 22.7 (p 0.30); null PASS rate 0.12
- NY step 13: chained DD -185849 vs null mean -194877 (p 0.40); income 2917887 vs null 2771362 (p 0.14); ratio p 0.29; periods shallower 9 vs null 7.0 (p 0.17); null PASS rate 0.18
- NP step 2: chained DD -116216 vs null mean -132798 (p 0.29); income 467351 vs null 572063 (p 0.89); ratio p 0.56; periods shallower 44 vs null 44.4 (p 0.60); null PASS rate 0.00
- NP step 4: chained DD -116216 vs null mean -132209 (p 0.23); income 467351 vs null 565048 (p 0.87); ratio p 0.62; periods shallower 24 vs null 22.7 (p 0.38); null PASS rate 0.00
- NP step 13: chained DD -116216 vs null mean -134552 (p 0.26); income 467351 vs null 543453 (p 0.76); ratio p 0.54; periods shallower 5 vs null 7.3 (p 0.96); null PASS rate 0.01

## Method and caveats
- Same subject, periods, P&L and post-hoc handling as WF_M5.md (removing a trade can unblock another of the same book; account layers not re-simulated: POST-HOC APPROX).
- Book id mapping: MFk -> cell id was fixed by matching the regenerated signals to each book's sig_ns (NP set has four books: MF1 L52359bf4, MF2 L8e0bf58c, MF3 L4bdd521a, MF4 unidentified so unfiltered). Twin counts per book: Asia 4/3/4/3, London 4/3/3, NY AM 4/4/1/5/2/2/5/3/4, NY PM 4/2/5/0. Twin signal pickles (53 MB) were not kept on the full box 1; regenerate with twin_gen.py in /mnt/l2/l2vast/_wf/M6/.
- twin_ids.csv / id_twins.csv (identical-signal twins from the W-ROT audit) were not needed: identical-event twins are not near-neighbours in the sense of this rule and the catalog twins used here were regenerated from the module grids (neighbour = adjacent value of one param key in the module's own GRID, or adjacent bar size of the same type among rows with grid results).
- References: k1 (any one twin), kall (all twins), opposite-majority block, kfit (re-fit per step).
