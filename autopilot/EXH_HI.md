# EXH_HI - EX-PHI: profit families H (take) and I (tighten/trail), Stage 1 first order
Generated 2026-11-14 14:31Z. 1077 cells scored (all ledgered, agent PHI). Label: PRE-PROOF (entries not live-matched). Fills: market exit k+1 mid -+0.80, targets nominal, stops at level. Features exist per month from the EX-FEAT store (rows with no feature never fire). Causality test (noise after second 900 on path, high/low/last and all feature panels; 17,926 exits <= 900 s over 128 sampled cells x 2 months, both directions): 0 changed - all kernels use only data <= decision second. Placebos null_ver 2 (cells re-scored after the leak audit). Family p, walk-forward and the live week are in the FINALISTS table at the top (finalists only). Labels in the generic tables below are CAND-DD only (L6M maxDD lower, L6M mean delta >= 0, PRE maxDD <= 1.05 x never-cut); the page label in FINALISTS uses labels_df.

Ranking key: L6M maxDD (weekly, scope), then L6M worst-20, then Ulcer, then Calmar; filter nfire>=20, L6M mean >= never-cut. Delta mean columns are vs never-cut hold-to-bracket (the S1b-COMB live reference deltas are in the ledger columns *_dmean_c).
## FINALISTS (U2, Stage 1 first order; Stage 2 section below when complete)
| book kind | technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD PRE with / without | worst-20 L6M with / without | nfire | placebo p | family p | WF | live week USD | kernel leak test (checked/changed at <=900 s) | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 dd-first | H_thick | arm=0.5 feat=tot_rel_slow secs=1 thr=2.0 | +128 / -805 / +758 / +2 / -272 / -1807 / -410 / -224 | 10243 / 20902 | 23821 / 26707 | 22354 / 1791 | 1748 | 0.015 | 0.974 | neg (-137879) | +1984 (15 fired) | 125/0 | CANDIDATE-DD |
| P7 dd-first | H_gated | arm=0.7 feat=tot_rel_fast secs=1 thr=2 | +3680 / -4505 / +522 / +655 / +1007 / +4519 / -2499 / -1342 | 71485 / 133887 | 107157 / 109442 | 64089 / -29902 | 1028 | 0.092 | 0.962 | neg (-647399) | -1317 (8 fired) | 27/0 | CANDIDATE-DD |
| M7 dd-first | H_thick | arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | -72 / -3687 / -1015 / +219 / -180 / -472 / -744 / -1059 | 14461 / 44425 | 49060 / 50321 | -28224 / -68299 | 2923 | 0.046 | 0.323 | neg (-17582) | -2874 (20 fired) | 835/0 | CANDIDATE-DD |
| M7 recents | H_tip | pct=0 secs=600 | -175 / +60 / +981 / +480 / +343 / -125 / -781 / -630 | 30376 / 44425 | 49262 / 50321 | -41511 / -68299 | 2175 | 0.138 | 1.000 | ok (+6882) | +4544 (8 fired) | 251/0 | CANDIDATE-DD |
| U7 dd-first | H_pcthour | pct=0.3 window=ldn | +4858 / +1091 / +1509 / +153 / +464 / +1037 / -1294 / -919 | 8700 / 21561 | 42735 / 42226 | 3983 / 120 | 769 | 0.031 | 0.956 | neg (-50249) | +7540 (4 fired) | 208/0 | CANDIDATE-DD |
| A7 dd-first | H_pcthour | pct=0.4 window=asia | +788 / -536 / -75 / +427 / -45 / -810 / -289 / +43 | 3268 / 12461 | 6089 / 6089 | -1783 / -17069 | 680 | 0.015 | 0.547 | neg (-21380) | +665 (13 fired) | 120/0 | CANDIDATE-DD |
| H7 dd-first | H_mom | arm=0.25 feat=vel30<= secs=1 thr=0 | +1418 / +639 / +1607 / +137 / +535 / -570 / -975 / -504 | 5961 / 15477 | 10161 / 20667 | 2693 / -32750 | 847 | 0.015 | 0.545 | neg (-87704) | +2524 (3 fired) | 523/0 | CANDIDATE-DD |
| O7 dd-first | I_step | lag=1 step=10 | +1130 / +289 / +203 / +215 / -335 / -170 / -498 / +29 | 4420 / 7469 | 4995 / 5102 | -891 / -9532 | 406 | 0.092 | 0.962 | neg (-11633) | +1167 (3 fired) | 583/0 | CANDIDATE-DD |
| ALL dd-first | I_swing | arm=0.7 buf=2 swing=swag5m | +11689 / -4649 / -538 / +1202 / +1341 / +1692 / -4778 / -2186 | 81103 / 121381 | 137290 / 152455 | 131325 / 77580 | 3242 | 0.354 | 0.958 | neg (-4844) | -5874 (6 fired) | 0/0 | CANDIDATE-DD |
| ALL recents | I_swing | arm=0.5 buf=2 swing=swag5m | +11562 / -914 / +2521 / +4670 / -168 / -3104 / -7696 / -1784 | 83702 / 121381 | 136367 / 152455 | 127763 / 77580 | 5489 | 0.462 | 0.994 | neg (-4844) | +375 (14 fired) | 1/0 | CANDIDATE-DD |
| K7 stage2-able alt | I_bookarm | X=20 arm=0.25 feat=ice_ag_w30 secs=30 thr=3 | +396 / +1700 / +3068 / +267 / -1218 / -2179 / -1365 / +255 | 12342 / 20902 | 18862 / 26707 | 10147 / 1791 | 3536 | 0.400 | 1.000 | neg (-112394) | +619 (24 fired) | 200/0 | CANDIDATE-DD |
| P7 stage2-able alt | H_pcthour | pct=0.6 window=am | +3049 / -4417 / -614 / +654 / +116 / -1774 / -1051 / -554 | 103198 / 133887 | 85948 / 109442 | 36262 / -29902 | 1025 | 0.892 | 1.000 | neg (-250769) | -4320 (2 fired) | 100/0 | CANDIDATE-DD |

## ROLL-EXCL check (the 33 roll-second-bracket trades removed from rule and never-cut reference; key (book, signal second) = /mnt/l2/l2vast/_th_exh/hi/roll_bracket_trades.csv; SZ_BASE_PROOF section 9)
Re-scored cells (family *_RX). Columns: maxDD with / without and mean delta vs never-cut, before -> after exclusion. L6M is unchanged within noise; X' and HOLD move because the roll trades sit in those windows. Stage 2 (engine) numbers still carry the artifact in the engine base (reference and rule alike); not re-run.

| book | technique | params | L6M maxDD before / after | HOLD maxDD before / after | PRE maxDD before / after | X' maxDD before / after | X' mean delta before / after | L6M mean delta before / after |
|---|---|---|---|---|---|---|---|---|
| M7 | I_decay | X0=30 Xmin=5 arm=0.3 rate=1 | 21793/44425 -> 21793/44425 | 27534/44425 -> 27534/44425 | 52180/50321 -> 52180/50321 | 32209/23241 -> 32209/23241 | -847 -> -847 | +383 -> +383 |
| H7 | H_mom | arm=0.25 feat=vel30<= secs=1 thr=0 | 5961/15477 -> 5961/15477 | 31266/57397 -> 31266/57397 | 10161/20667 -> 10161/20667 | 15086/34807 -> 15086/34807 | -504 -> -504 | +137 -> +137 |
| ALL | I_swing | arm=0.7 buf=2 swing=swag5m | 81103/121381 -> 81103/121381 | 115350/153255 -> 109186/147091 | 137290/152455 -> 137290/152455 | 89284/165396 -> 101235/177347 | -2186 -> -2186 | +1202 -> +1202 |
| M7 | H_tip | pct=0 secs=600 | 30376/44425 -> 30376/44425 | 30376/44425 -> 30376/44425 | 49262/50321 -> 49262/50321 | 33527/23241 -> 33527/23241 | -630 -> -630 | +480 -> +480 |
| U7 | H_pcthour | pct=0.3 window=ldn | 8700/21561 -> 8700/21561 | 21365/21561 -> 21365/21561 | 42735/42226 -> 42735/42226 | 36073/24437 -> 38464/26827 | -919 -> -919 | +153 -> +153 |
| K7 | I_bookarm | X=20 arm=0.25 feat=ice_ag_w30 secs=30 thr=3 | 12342/20902 -> 12342/20007 | 65671/42831 -> 63227/41571 | 18862/26707 -> 18862/25532 | 27004/44364 -> 27004/44364 | +255 -> +255 | +267 -> +267 |
| A7 | H_pcthour | pct=0.4 window=asia | 3268/12461 -> 3268/12461 | 9772/14181 -> 9772/14181 | 6089/6089 -> 6458/6089 | 5702/13855 -> 5702/13855 | +43 -> +43 | +427 -> +427 |
| M7 | H_thick | arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | 14461/44425 -> 14461/44425 | 22287/44425 -> 22287/44425 | 49060/50321 -> 49060/50321 | 36297/23241 -> 36297/23241 | -1059 -> -1059 | +219 -> +219 |
| P7 | H_gated | arm=0.7 feat=tot_rel_fast secs=1 thr=2 | 71485/133887 -> 71485/133887 | 90195/144370 -> 85290/139466 | 107157/109442 -> 98498/109442 | 122544/135949 -> 126070/141816 | -1342 -> -1342 | +655 -> +655 |
| O7 | I_step | lag=1 step=10 | 4420/7469 -> 4420/7469 | 5050/7469 -> 5050/7469 | 4995/5102 -> 4995/5102 | 10283/14262 -> 10283/14262 | +29 -> +29 | +215 -> +215 |
| P7 | H_pcthour | pct=0.6 window=am | 103198/133887 -> 103198/133887 | 103198/144370 -> 103198/139466 | 85948/109442 -> 77289/109442 | 69324/135949 -> 72851/141816 | -554 -> -554 | +654 -> +654 |
| K7 | H_thick | arm=0.5 feat=tot_rel_slow secs=1 thr=2.0 | 10243/20902 -> 10243/20007 | 48459/42831 -> 47199/41571 | 23821/26707 -> 23821/25532 | 34302/44364 -> 35497/44364 | -224 -> -224 | +2 -> +2 |
| ALL | I_swing | arm=0.5 buf=2 swing=swag5m | 83702/121381 -> 83702/121381 | 151066/153255 -> 144902/147091 | 136367/152455 -> 136367/152455 | 103975/165396 -> 115728/177347 | -1784 -> -1784 | +4670 -> +4670 |

## Stage 2: engine cascade of the Stage-2-able finalists (set phi_pb; re-entries, locks, stack gates, caps, measured fills)
Coverage: S2, 43 months run. Windows not fully covered are n/a. Reference = engine never-cut (base_b/NOCUT). Label PRE-PROOF.

| book | rule | stage-2 mean delta vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD HOLD with / without | maxDD PRE with / without |
|---|---|---|---|---|---|
| K7 | I_bookarm X=20 arm=0.25 feat=ice_ag_w30 secs=30 thr=3 | -1524 / +1709 / +808 / -1689 / -1839 / -663 / -719 / -296 | 23159 / 35969 | 50680 / 40365 | 19141 / 22188 |
| P7 | H_pcthour pct=0.6 window=am | -1772 / -392 / -786 / +236 / -39 / -3249 / +701 / +684 | 191674 / 203542 | 191674 / 203542 | 120861 / 122169 |
| M7 | H_tip pct=0 secs=600 | -2456 / -437 / +497 / -141 / -35 / +810 / -616 / -215 | 46661 / 48019 | 48834 / 48019 | 66091 / 44205 |
| U7 | H_pcthour pct=0.3 window=ldn | +1827 / +227 / +355 / -562 / -446 / +14 / -651 / -398 | 14388 / 17816 | 21115 / 20695 | 41634 / 39542 |
| A7 | H_pcthour pct=0.4 window=asia | -511 / -364 / -115 / -188 / +7 / +250 / -455 / -39 | 6023 / 9361 | 6023 / 9361 | 15274 / 8625 |
| H7 | H_mom arm=0.25 feat=vel30<= secs=1 thr=0 | -357 / -584 / +78 / -670 / -442 / -517 / -457 / +43 | 11897 / 16242 | 54775 / 47806 | 13803 / 18436 |
| O7 | I_step lag=1 step=10 | +1232 / +307 / +282 / +251 / -250 / -49 / -494 / -3 | 4210 / 6958 | 4685 / 6958 | 4720 / 4797 |

K7 profit, Stage 2: L6M maxDD 35969 -> 23159, L6M mean delta -1689 USD/wk; PRE maxDD 22188 -> 19141, mean delta -719. Does not hold in L6M through the engine (drawdown or mean worse than never-cut).
P7 profit, Stage 2: L6M maxDD 203542 -> 191674, L6M mean delta +236 USD/wk; PRE maxDD 122169 -> 120861, mean delta +701. Holds the drawdown and mean in L6M through the engine.
M7 profit, Stage 2: L6M maxDD 48019 -> 46661, L6M mean delta -141 USD/wk; PRE maxDD 44205 -> 66091, mean delta -616. Does not hold in L6M through the engine (drawdown or mean worse than never-cut).
U7 profit, Stage 2: L6M maxDD 17816 -> 14388, L6M mean delta -562 USD/wk; PRE maxDD 39542 -> 41634, mean delta -651. Does not hold in L6M through the engine (drawdown or mean worse than never-cut).
A7 profit, Stage 2: L6M maxDD 9361 -> 6023, L6M mean delta -188 USD/wk; PRE maxDD 8625 -> 15274, mean delta -455. Does not hold in L6M through the engine (drawdown or mean worse than never-cut).
H7 profit, Stage 2: L6M maxDD 16242 -> 11897, L6M mean delta -670 USD/wk; PRE maxDD 18436 -> 13803, mean delta -457. Does not hold in L6M through the engine (drawdown or mean worse than never-cut).
O7 profit, Stage 2: L6M maxDD 6958 -> 4210, L6M mean delta +251 USD/wk; PRE maxDD 4797 -> 4720, mean delta -494. Holds the drawdown and mean in L6M through the engine.

Stage 2 verdict: L6M maxDD is cut for every book here; the L6M mean stays at or above never-cut only for P7, O7. PRE mean is negative for K7, M7, U7, A7, H7, O7. maxDD with the rule is worse than never-cut in: K7 HOLD, M7 HOLD, M7 PRE, U7 HOLD, U7 PRE, A7 PRE, H7 HOLD. No book qualifies as ENTER; delivered as PRE-PROOF profit rules because every book must have one.

## Profit rule for the FINAL page (per book, best Stage-2-able CANDIDATE-DD; PRE-PROOF; no ENTER)
| book | rule | Stage 1 L6M maxDD with/without | Stage 2 L6M maxDD with/without | Stage 2 L6M mean delta |
|---|---|---|---|---|
| K7 | I_bookarm X=20 arm=0.25 feat=ice_ag_w30 secs=30 thr=3 | see FINALISTS | 23159 / 35969 | -1689 |
| P7 | H_pcthour pct=0.6 window=am | see FINALISTS | 191674 / 203542 | +236 |
| M7 | H_tip pct=0 secs=600 | see FINALISTS | 46661 / 48019 | -141 |
| U7 | H_pcthour pct=0.3 window=ldn | see FINALISTS | 14388 / 17816 | -562 |
| A7 | H_pcthour pct=0.4 window=asia | see FINALISTS | 6023 / 9361 | -188 |
| H7 | H_mom arm=0.25 feat=vel30<= secs=1 thr=0 | see FINALISTS | 11897 / 16242 | -670 |
| O7 | I_step lag=1 step=10 | see FINALISTS | 4210 / 6958 | +251 |

K7 equality check (202610, Stage 1 kernel vs engine ExhCut): 92 of 92 matched exits equal in second (+-1 s) and price; U7 2 of 2. Unmatched Stage 1 fires are engine re-entry/lock/stack-gate differences.

## Stage 2: engine cascade of the thick-book finalists (K7, P7, M7 first choices; slot-baseline panel now computed in the engine, identical to the feature store: max abs diff 0 over 48,000 values) (set phi_thick; re-entries, locks, stack gates, caps, measured fills)
Coverage: S2, 43 months run. Windows not fully covered are n/a. Reference = engine never-cut (base_b/NOCUT). Label PRE-PROOF.

| book | rule | stage-2 mean delta vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' | maxDD L6M with / without | maxDD HOLD with / without | maxDD PRE with / without |
|---|---|---|---|---|---|
| K7 | H_thick arm=0.5 feat=tot_rel_slow secs=1 thr=2.0 | +4400 / +1759 / +1560 / +656 / +102 / -1713 / -17 / -519 | 20056 / 35969 | 41589 / 40365 | 29349 / 22188 |
| P7 | H_gated arm=0.7 feat=tot_rel_fast secs=1 thr=2 | +2393 / -657 / +842 / +295 / +145 / +827 / -163 / -417 | 186789 / 203542 | 186789 / 203542 | 121413 / 122169 |
| M7 | H_thick arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | -219 / -412 / -1232 / -389 / -154 / +368 / -577 / -611 | 30068 / 48019 | 49598 / 48019 | 67688 / 44205 |

K7 profit, Stage 2: L6M maxDD 35969 -> 20056, L6M mean delta +656 USD/wk; PRE maxDD 22188 -> 29349, mean delta -17. Holds the drawdown and mean in L6M through the engine.
P7 profit, Stage 2: L6M maxDD 203542 -> 186789, L6M mean delta +295 USD/wk; PRE maxDD 122169 -> 121413, mean delta -163. Holds the drawdown and mean in L6M through the engine.
M7 profit, Stage 2: L6M maxDD 48019 -> 30068, L6M mean delta -389 USD/wk; PRE maxDD 44205 -> 67688, mean delta -577. Does not hold in L6M through the engine (drawdown or mean worse than never-cut).

Stage 2 verdict: L6M maxDD is cut for every book here; the L6M mean stays at or above never-cut only for K7, P7. PRE mean is negative for K7, P7, M7. maxDD with the rule is worse than never-cut in: K7 HOLD, K7 PRE, M7 HOLD, M7 PRE. No book qualifies as ENTER; delivered as PRE-PROOF profit rules because every book must have one.

## Profit rule for the FINAL page (per book, best Stage-2-able CANDIDATE-DD; PRE-PROOF; no ENTER)
| book | rule | Stage 1 L6M maxDD with/without | Stage 2 L6M maxDD with/without | Stage 2 L6M mean delta |
|---|---|---|---|---|
| K7 | H_thick arm=0.5 feat=tot_rel_slow secs=1 thr=2.0 | see FINALISTS | 20056 / 35969 | +656 |
| P7 | H_gated arm=0.7 feat=tot_rel_fast secs=1 thr=2 | see FINALISTS | 186789 / 203542 | +295 |
| M7 | H_thick arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | see FINALISTS | 30068 / 48019 | -389 |

K7 equality check (202610, Stage 1 kernel vs engine ExhCut): 92 of 92 matched exits equal in second (+-1 s) and price; U7 2 of 2. Unmatched Stage 1 fires are engine re-entry/lock/stack-gate differences.

## Plain sentences per book (profit)
K7 profit: H_thick (arm=0.5 feat=tot_rel_slow secs=1 thr=2.0) (pooled sessions). Against plain 60/60 hold-to-bracket (= never-cut) it moves L6M maxDD 20902 -> 10243 and PRE maxDD 26707 -> 23821, L6M mean +2 USD/wk, PRE mean -410. Placebo p 0.015, family (Westfall-Young) p 0.974, purged walk-forward does not hold (negative) (-137879), live week +1984 USD over 15 fired trades. Label CANDIDATE-DD. It is not shown to hold out of sample (walk-forward negative or unavailable, family p not significant); it is delivered as the book's profit rule because every book must have one, not as an ENTER.

P7 profit: H_gated (arm=0.7 feat=tot_rel_fast secs=1 thr=2) (pooled sessions). Against plain 60/60 hold-to-bracket (= never-cut) it moves L6M maxDD 133887 -> 71485 and PRE maxDD 109442 -> 107157, L6M mean +655 USD/wk, PRE mean -2499. Placebo p 0.092, family (Westfall-Young) p 0.962, purged walk-forward does not hold (negative) (-647399), live week -1317 USD over 8 fired trades. Label CANDIDATE-DD. It is not shown to hold out of sample (walk-forward negative or unavailable, family p not significant); it is delivered as the book's profit rule because every book must have one, not as an ENTER.

M7 profit: H_thick (arm=0.1 feat=tot_rel_slow secs=1 thr=1.3) (pooled sessions). Against plain 60/60 hold-to-bracket (= never-cut) it moves L6M maxDD 44425 -> 14461 and PRE maxDD 50321 -> 49060, L6M mean +219 USD/wk, PRE mean -744. Placebo p 0.046, family (Westfall-Young) p 0.323, purged walk-forward does not hold (negative) (-17582), live week -2874 USD over 20 fired trades. Label CANDIDATE-DD. It is not shown to hold out of sample (walk-forward negative or unavailable, family p not significant); it is delivered as the book's profit rule because every book must have one, not as an ENTER.

U7 profit: H_pcthour (pct=0.3 window=ldn) (pooled sessions). Against plain 60/60 hold-to-bracket (= never-cut) it moves L6M maxDD 21561 -> 8700 and PRE maxDD 42226 -> 42735, L6M mean +153 USD/wk, PRE mean -1294. Placebo p 0.031, family (Westfall-Young) p 0.956, purged walk-forward does not hold (negative) (-50249), live week +7540 USD over 4 fired trades. Label CANDIDATE-DD. It is not shown to hold out of sample (walk-forward negative or unavailable, family p not significant); it is delivered as the book's profit rule because every book must have one, not as an ENTER.

A7 profit: H_pcthour (pct=0.4 window=asia) (pooled sessions). Against plain 60/60 hold-to-bracket (= never-cut) it moves L6M maxDD 12461 -> 3268 and PRE maxDD 6089 -> 6089, L6M mean +427 USD/wk, PRE mean -289. Placebo p 0.015, family (Westfall-Young) p 0.547, purged walk-forward does not hold (negative) (-21380), live week +665 USD over 13 fired trades. Label CANDIDATE-DD. It is not shown to hold out of sample (walk-forward negative or unavailable, family p not significant); it is delivered as the book's profit rule because every book must have one, not as an ENTER.

H7 profit: H_mom (arm=0.25 feat=vel30<= secs=1 thr=0) (pooled sessions). Against plain 60/60 hold-to-bracket (= never-cut) it moves L6M maxDD 15477 -> 5961 and PRE maxDD 20667 -> 10161, L6M mean +137 USD/wk, PRE mean -975. Placebo p 0.015, family (Westfall-Young) p 0.545, purged walk-forward does not hold (negative) (-87704), live week +2524 USD over 3 fired trades. Label CANDIDATE-DD. It is not shown to hold out of sample (walk-forward negative or unavailable, family p not significant); it is delivered as the book's profit rule because every book must have one, not as an ENTER.

O7 profit: I_step (lag=1 step=10) (pooled sessions). Against plain 60/60 hold-to-bracket (= never-cut) it moves L6M maxDD 7469 -> 4420 and PRE maxDD 5102 -> 4995, L6M mean +215 USD/wk, PRE mean -498. Placebo p 0.092, family (Westfall-Young) p 0.962, purged walk-forward does not hold (negative) (-11633), live week +1167 USD over 3 fired trades. Label CANDIDATE-DD. It is not shown to hold out of sample (walk-forward negative or unavailable, family p not significant); it is delivered as the book's profit rule because every book must have one, not as an ENTER.

ALL profit: I_swing (arm=0.7 buf=2 swing=swag5m) (pooled sessions). Against plain 60/60 hold-to-bracket (= never-cut) it moves L6M maxDD 121381 -> 81103 and PRE maxDD 152455 -> 137290, L6M mean +1202 USD/wk, PRE mean -4778. Placebo p 0.354, family (Westfall-Young) p 0.958, purged walk-forward does not hold (negative) (-4844), live week -5874 USD over 6 fired trades. Label CANDIDATE-DD. It is not shown to hold out of sample (walk-forward negative or unavailable, family p not significant); it is delivered as the book's profit rule because every book must have one, not as an ENTER.

## Best drawdown-first cell per book (Stage-1 screen, sessions pooled)
K7 profit: the technique that lowers L6M drawdown most is H_gated (arm=0.5 feat=ice_ag_w30 secs=1 thr=4); stack-scope maxDD 9694 vs 20902 never-cut, L6M mean delta +180 USD/wk, PRE maxDD 29792 vs 26707; placebo p 0.138; does not qualify as CANDIDATE-DD.

P7 profit: the technique that lowers L6M drawdown most is H_gated (arm=0.7 feat=tot_rel_fast secs=1 thr=2); stack-scope maxDD 71485 vs 133887 never-cut, L6M mean delta +655 USD/wk, PRE maxDD 107157 vs 109442; placebo p 0.092; CANDIDATE-DD.

M7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.1 feat=tot_rel_slow secs=1 thr=1.3); stack-scope maxDD 14461 vs 44425 never-cut, L6M mean delta +219 USD/wk, PRE maxDD 49060 vs 50321; placebo p 0.046; CANDIDATE-DD.

U7 profit: the technique that lowers L6M drawdown most is H_pcthour (pct=0.3 window=ldn); stack-scope maxDD 8700 vs 21561 never-cut, L6M mean delta +153 USD/wk, PRE maxDD 42735 vs 42226; placebo p 0.031; CANDIDATE-DD.

A7 profit: the technique that lowers L6M drawdown most is H_pcthour (pct=0.4 window=asia); stack-scope maxDD 3268 vs 12461 never-cut, L6M mean delta +427 USD/wk, PRE maxDD 6089 vs 6089; placebo p 0.015; CANDIDATE-DD.

H7 profit: the technique that lowers L6M drawdown most is H_mom (arm=0.25 feat=vel30<= secs=1 thr=0); stack-scope maxDD 5961 vs 15477 never-cut, L6M mean delta +137 USD/wk, PRE maxDD 10161 vs 20667; placebo p 0.015; CANDIDATE-DD.

O7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.1 feat=ahead_rel_slow secs=1 thr=1.3); stack-scope maxDD 2825 vs 7469 never-cut, L6M mean delta +122 USD/wk, PRE maxDD 6213 vs 5102; placebo p 0.015; does not qualify as CANDIDATE-DD.

ALL profit: the technique that lowers L6M drawdown most is I_trail (X=30 arm=0.7); stack-scope maxDD 39556 vs 121381 never-cut, L6M mean delta +4034 USD/wk, PRE maxDD 100321 vs 152455; placebo p 0.015; CANDIDATE-DD.

## Tables

### K7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.5 feat=ice_ag_w30 secs=1 thr=4 | +1176 / -1211 / +978 / +180 / -1173 / -2234 / -1175 / -103 | 9694 / 20902 | 29792 / 26707 | 22808 / 1791 | 4094 | 0.138 | pers 0.75 |  |
| I_bookarm | X=20 arm=0.5 feat=ice_ag_w30 secs=30 thr=3 | -378 / -936 / +1557 / +209 / -826 / -1726 / -483 / -197 | 9899 / 20902 | 20040 / 26707 | 35611 / 1791 | 2239 | 0.046 | pers 0.50 | CAND-DD |
| H_thick | arm=0.5 feat=tot_rel_slow secs=1 thr=2.0 | +128 / -805 / +758 / +2 / -272 / -1807 / -410 / -224 | 10243 / 20902 | 23821 / 26707 | 22354 / 1791 | 1748 | 0.015 | pers 0.75 | CAND-DD |
| H_thick | arm=0.1 feat=tot_rel_slow secs=3 thr=2.0 | +496 / -386 / +663 / +19 / -925 / -1587 / -1108 / +222 | 11309 / 20902 | 33872 / 26707 | 4348 / 1791 | 2049 | 0.200 | pers 0.75 |  |
| I_bookarm | X=5 arm=0.5 feat=ice_ag_w30 secs=10 thr=3 | +2058 / -1026 / +1421 / +232 / -1128 / -2951 / -718 / -318 | 11655 / 20902 | 29861 / 26707 | 20430 / 1791 | 3850 | 0.323 | pers 0.75 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_swing | arm=0.5 buf=0 swing=swag1m | +1385 / +1106 / +2784 / +1276 / -315 / -1177 / -1337 / +9 | 21480 / 20902 | 33516 / 26707 | 20446 / 1791 | 2732 | 0.877 | pers 1.00 |  |

### P7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.7 feat=tot_rel_fast secs=1 thr=2 | +3680 / -4505 / +522 / +655 / +1007 / +4519 / -2499 / -1342 | 71485 / 133887 | 107157 / 109442 | 64089 / -29902 | 1028 | 0.092 | pers 0.75 | CAND-DD |
| NT_retarget | k=8 | +2611 / -2261 / +535 / +1658 / +2001 / -1154 / -358 / -498 | 77449 / 133887 | 111128 / 109442 | 59878 / -29902 | 1857 | 0.031 | pers 0.75 | CAND-DD |
| I_trail | X=15 arm=0.9 | -5654 / -1939 / +757 / +1179 / +135 / -3353 / -2422 / -579 | 78294 / 133887 | 127068 / 109442 | 28267 / -29902 | 646 | 0.015 | pers 0.50 |  |
| H_gated | arm=0.8 feat=tot_rel_fast secs=1 thr=2 | -2786 / -3368 / -173 / +525 / +399 / -2576 / -1154 / -622 | 82220 / 133887 | 110881 / 109442 | 34321 / -29902 | 725 | 0.154 | pers 0.25 | CAND-DD |
| I_trail | X=20 arm=0.9 | -6900 / -2706 / +46 / +961 / +1159 / -6301 / -2499 / -884 | 84167 / 133887 | 125763 / 109442 | 23738 / -29902 | 529 | 0.108 | pers 0.50 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_step | lag=2 step=20 | -4653 / -3269 / +209 / +3816 / +1314 / -1026 / -3374 / -443 | 103981 / 133887 | 101168 / 109442 | 67869 / -29902 | 869 | 0.800 | pers 0.50 | CAND-DD |

### M7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | -72 / -3687 / -1015 / +219 / -180 / -472 / -744 / -1059 | 14461 / 44425 | 49060 / 50321 | -28224 / -68299 | 2923 | 0.046 | pers 0.25 | CAND-DD |
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.5 | +1398 / -2880 / -238 / +299 / -93 / -327 / -728 / -1113 | 19927 / 44425 | 52736 / 50321 | -22948 / -68299 | 2978 | 0.277 | pers 0.50 | CAND-DD |
| I_decay | X0=40 Xmin=5 arm=0.3 rate=2 | -220 / -62 / +655 / +370 / -175 / +137 / -738 / -968 | 21098 / 44425 | 58862 / 50321 | -30842 / -68299 | 2624 | 0.046 | pers 0.50 |  |
| I_decay | X0=30 Xmin=5 arm=0.3 rate=1 | -331 / -282 / +464 / +383 / -85 / +424 / -673 / -847 | 21793 / 44425 | 52180 / 50321 | -24876 / -68299 | 2622 | 0.046 | pers 0.50 | CAND-DD |
| I_decay | X0=40 Xmin=10 arm=0.3 rate=2 | -144 / -289 / +480 / +283 / -178 / +324 / -751 / -886 | 21883 / 44425 | 59500 / 50321 | -32131 / -68299 | 2585 | 0.108 | pers 0.50 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_swing | arm=0.3 buf=2 swing=swag5m | -670 / -375 / +17 / +917 / +395 / -116 / -1062 / -1231 | 29095 / 44425 | 90967 / 50321 | -47053 / -68299 | 1464 | 0.046 | pers 0.50 |  |

### U7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_pcthour | pct=0.3 window=ldn | +4858 / +1091 / +1509 / +153 / +464 / +1037 / -1294 / -919 | 8700 / 21561 | 42735 / 42226 | 3983 / 120 | 769 | 0.031 | pers 1.00 | CAND-DD |
| I_bookarm | X=20 arm=0.25 feat=ice_ag_w30 secs=3 thr=3 | +5854 / +1301 / -86 / +296 / -113 / -1172 / -1779 / -1030 | 10015 / 21561 | 65213 / 42226 | 15471 / 120 | 904 | 0.369 | pers 0.75 |  |
| I_trail | X=25 arm=0.7 | +4988 / -480 / +1950 / +1154 / +899 / -376 / -243 / -608 | 10126 / 21561 | 33544 / 42226 | 37905 / 120 | 387 | 0.062 | pers 0.75 | CAND-DD |
| I_chand | arm=0.7 atr=atr5m k=1 | +5809 / -604 / +1967 / +1036 / +891 / -1280 / -318 / -463 | 10146 / 21561 | 35510 / 42226 | 38825 / 120 | 527 | 0.046 | pers 0.75 | CAND-DD |
| I_lock | X=20 arm=0.7 | +5370 / +74 / +2240 / +1598 / +1119 / -197 / -248 / -532 | 11031 / 21561 | 35820 / 42226 | 45962 / 120 | 342 | 0.400 | pers 1.00 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_lock | X=2 arm=0.7 | +3489 / -584 / +932 / +1634 / +815 / +72 / -348 / -417 | 14576 / 21561 | 28407 / 42226 | 30137 / 120 | 235 | 0.923 | pers 0.75 | CAND-DD |

### A7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_pcthour | pct=0.4 window=asia | +788 / -536 / -75 / +427 / -45 / -810 / -289 / +43 | 3268 / 12461 | 6089 / 6089 | -1783 / -17069 | 680 | 0.015 | pers 0.50 | CAND-DD |
| H_pcthour | pct=0.4 window=all | +788 / -806 / -30 / +374 / +106 / -546 / -183 / +12 | 3268 / 12461 | 4461 / 6089 | -2128 / -17069 | 892 | 0.015 | pers 0.50 | CAND-DD |
| H_gated | arm=0.25 feat=pr_e001_own_w10 secs=1 thr=20 | +422 / -731 / +229 / +328 / +62 / -681 / -246 / -116 | 3723 / 12461 | 4568 / 6089 | 1459 / -17069 | 905 | 0.015 | pers 0.75 | CAND-DD |
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=20 | +574 / -1177 / +165 / +587 / +22 / -968 / -148 / -176 | 3733 / 12461 | 4455 / 6089 | 6397 / -17069 | 754 | 0.015 | pers 0.75 | CAND-DD |
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=10 | +519 / -582 / +173 / +272 / +35 / -694 / -431 / +16 | 3750 / 12461 | 5327 / 6089 | 1017 / -17069 | 939 | 0.015 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=20 | +574 / -1177 / +165 / +587 / +22 / -968 / -148 / -176 | 3733 / 12461 | 4455 / 6089 | 6397 / -17069 | 754 | 0.015 | pers 0.75 | CAND-DD |

### H7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_mom | arm=0.25 feat=vel30<= secs=1 thr=0 | +1418 / +639 / +1607 / +137 / +535 / -570 / -975 / -504 | 5961 / 15477 | 10161 / 20667 | 2693 / -32750 | 847 | 0.015 | pers 1.00 | CAND-DD |
| H_gated | arm=0.4 feat=imb_ag5 secs=1 thr=0.2 | +1263 / +524 / +1252 / +301 / +589 / -348 / -634 / -225 | 5992 / 15477 | 10534 / 20667 | -533 / -32750 | 791 | 0.015 | pers 1.00 | CAND-DD |
| H_mom | arm=0.25 feat=vel30<= secs=1 thr=1 | +1236 / +414 / +1458 / +116 / +583 / -357 / -675 / -477 | 6016 / 15477 | 8137 / 20667 | 2354 / -32750 | 853 | 0.015 | pers 1.00 | CAND-DD |
| H_mom | arm=0.25 feat=vel30<= secs=1 thr=2 | +1250 / +397 / +1417 / +74 / +579 / -383 / -654 / -523 | 6241 / 15477 | 8042 / 20667 | 399 / -32750 | 856 | 0.015 | pers 1.00 | CAND-DD |
| H_gated | arm=0.4 feat=pr_e001_own_w10 secs=1 thr=10 | +1765 / +715 / +1285 / +194 / +631 / +13 / -800 / -86 | 6390 / 15477 | 14345 / 20667 | -1620 / -32750 | 796 | 0.015 | pers 1.00 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_chand | arm=0.7 atr=atr5m k=2 | +1874 / +207 / +699 / +1387 / +860 / +122 / -496 / +14 | 9348 / 15477 | 21288 / 20667 | -2391 / -32750 | 253 | 0.015 | pers 1.00 | CAND-DD |

### O7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.3 | +801 / +192 / +111 / +122 / -388 / +46 / -650 / +47 | 2825 / 7469 | 6213 / 5102 | -258 / -9532 | 367 | 0.015 | pers 1.00 |  |
| H_thick | arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | +1212 / +454 / +267 / +30 / -274 / +141 / -582 / +73 | 3243 / 7469 | 6193 / 5102 | 454 / -9532 | 354 | 0.031 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.5 | +1132 / +404 / +244 / +37 / -339 / +11 / -638 / +68 | 3243 / 7469 | 7956 / 5102 | 276 / -9532 | 354 | 0.031 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=2.0 | +1361 / +363 / +214 / +310 / -234 / -54 / -465 / +122 | 3243 / 7469 | 7322 / 5102 | -1205 / -9532 | 312 | 0.015 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=2.5 | +1056 / +316 / -55 / +18 / -197 / +195 / -264 / +80 | 3426 / 7469 | 9051 / 5102 | -1438 / -9532 | 243 | 0.015 | pers 0.75 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_chand | arm=0.5 atr=atr1m k=1 | +1217 / +525 / +557 / +459 / -31 / -446 / -409 / +24 | 5522 / 7469 | 6816 / 5102 | -5261 / -9532 | 221 | 0.031 | pers 1.00 |  |

### ALL - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_trail | X=30 arm=0.7 | +1706 / +1072 / +7978 / +4034 / +2252 / -954 / -5322 / -430 | 39556 / 121381 | 100321 / 152455 | 180274 / 77580 | 4534 | 0.015 | pers 1.00 | CAND-DD |
| I_lock | X=10 arm=0.7 | -1007 / -1221 / +5479 / +4513 / +2280 / -1383 / -3986 / -402 | 41951 / 121381 | 117200 / 152455 | 184415 / 77580 | 3622 | 0.015 | pers 0.50 | CAND-DD |
| I_trail | X=40 arm=0.7 | +309 / -1625 / +5664 / +3347 / +939 / +1735 / -4779 / -125 | 45635 / 121381 | 119526 / 152455 | 163943 / 77580 | 3683 | 0.015 | pers 0.75 | CAND-DD |
| H_gated | arm=0.5 feat=pr_e001_own_w10 secs=1 thr=35 | -15557 / -4245 / +4473 / +1653 / -3027 / -8993 / -2702 / +602 | 47569 / 121381 | 95799 / 152455 | 173355 / 77580 | 6199 | 0.123 | pers 0.50 | CAND-DD |
| H_gated | arm=0.6 feat=pr_e001_own_w10 secs=1 thr=35 | -7129 / -165 / +5754 / +1473 / -1863 / -6673 / -2930 / -994 | 48072 / 121381 | 137331 / 152455 | 149728 / 77580 | 4908 | 0.015 | pers 0.50 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_lock | X=0 arm=0.6 | -11256 / -9624 / +1333 / +5440 / +471 / -5457 / -5507 / -299 | 73489 / 121381 | 121459 / 152455 | 237076 / 77580 | 4333 | 0.015 | pers 0.50 | CAND-DD |
