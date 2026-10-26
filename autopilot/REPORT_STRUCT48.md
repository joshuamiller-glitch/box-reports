# REPORT STRUCT48 (RESEARCH V2 rules) - written 2026-10-26T12:34Z by S48-LEAD

Research only. No spec, no live recommendation: anything the user decides to run goes through the user's own test-then-score rule. Benchmark Set A (corrected P9, live cost, 14/14, locks on): WF $24,975/wk, SD 104,523, maxDD 401,293. Full cell list with effect, CI, MDE, placebo, holdout, verdict, DSR and caveats: autopilot/LEADERBOARD.md. Per-track reports: autopilot/REPORT_STRUCT48_T<n>.md, REPORT_STRUCT48_HB.md, T3_10b.

## Verdict

Passing structural rules: none (PASS). CANDIDATE: Set B / PBDAY lock set (block bootstrap; one exposure incl. modelling variants) and T14_S_s50_t1.5_n14 (shorts-only 50-stop / 1.5R, CANDIDATE by user ruling 2026-10-25; the scorer reads it DEAD). Passing diversifiers: GSHORT, ORB Asia, dip-buy RSI2 family (sleeves; execution: T4 re-verdicted with the MDE-based criterion = 0 PASS / 1 CANDIDATE (T4.2_Y4, +0.050 pt/trade on the full replay, year share >60%) / 13 DEAD; NM's partial-replay PASS (+0.093) is superseded). Combined vs Set A (the pre-registered no_Y4 variant of the single scored run; add about +$0.5k/wk for Y4 at its full-replay +0.050 pt/trade = 0.050 x $280 x 36 trades/wk): +$15,880/wk, maxDD -$42,747, SD -$-5,608 (SD rose, not fell), CI [7,795, 24,468], holdout + (+$16,290/wk; holdout maxDD +24,295). The primary scored stack that also included Y4 (Y4 at the partial-replay +0.0927 pt/trade; Y4 is now CANDIDATE at +0.050) gave +$16,808/wk, maxDD -$44,538, CI [8,735, 25,426], holdout +$17,315/wk.

Verdict counts on the leaderboard: {'DEAD': 659, 'PASS': 18, 'CANDIDATE': 29, 'PENDING': 10} (cells include duplicate re-scores of the same series; independent PASS exposures: GSHORT, ORB Asia, dip-buy RSI2 family).

## Every PASS

| track | cell | object | effect | MDE | placebo | holdout | exposure | caveat |
|---|---|---|---|---|---|---|---|---|
| NM_E | E:GSHORT_t90 | sleeve | 2,970 | 6,140 | 0.9566 | 3,931 | GSHORT | only ~31 trades; portfolio maxDD +28.9% |
| T3.8B | GSHORT_t90 | sleeve | 5,941 | 12,686 | 0.9566 | 7,862 | GSHORT | only ~31 trades; portfolio maxDD +28.9% |
| NM_E | E:ORB_ASIA_15_v1_s60 | sleeve | 4,462 | 6,140 | 0.958 | 6,713 | ORB Asia | negative in IS; ORB_ASIA_15_v1 s60/s75 implies 14-68 extra NQ lots on top of Set A's 28 and worsens portfolio maxDD by 9-102% (sleeve criter |
| NM_E | E:ORB_ASIA_15_v1_s75 | sleeve | 4,472 | 6,140 | 0.962 | 8,496 | ORB Asia | negative in IS; ORB_ASIA_15_v1 s60/s75 implies 14-68 extra NQ lots on top of Set A's 28 and worsens portfolio maxDD by 9-102% (sleeve criter |
| T3.2 | ORB_ASIA_15_v1__s60@0.25 | sleeve | 4,069 | 5,581 | 0.958 | 6,123 | ORB Asia | negative in IS; ORB_ASIA_15_v1 s60/s75 implies 14-68 extra NQ lots on top of Set A's 28 and worsens portfolio maxDD by 9-102% (sleeve criter |
| T3.2 | ORB_ASIA_15_v1__s60@0.5 | sleeve | 8,138 | 11,162 | 0.958 | 12,245 | ORB Asia | negative in IS; ORB_ASIA_15_v1 s60/s75 implies 14-68 extra NQ lots on top of Set A's 28 and worsens portfolio maxDD by 9-102% (sleeve criter |
| T3.2 | ORB_ASIA_15_v1__s60@1.0 | sleeve | 16,276 | 22,324 | 0.958 | 24,491 | ORB Asia | negative in IS; ORB_ASIA_15_v1 s60/s75 implies 14-68 extra NQ lots on top of Set A's 28 and worsens portfolio maxDD by 9-102% (sleeve criter |
| T3.2 | ORB_ASIA_15_v1__s75@0.25 | sleeve | 3,864 | 5,215 | 0.962 | 7,340 | ORB Asia | negative in IS; ORB_ASIA_15_v1 s60/s75 implies 14-68 extra NQ lots on top of Set A's 28 and worsens portfolio maxDD by 9-102% (sleeve criter |
| T3.2 | ORB_ASIA_15_v1__s75@0.5 | sleeve | 7,727 | 10,430 | 0.962 | 14,680 | ORB Asia | negative in IS; ORB_ASIA_15_v1 s60/s75 implies 14-68 extra NQ lots on top of Set A's 28 and worsens portfolio maxDD by 9-102% (sleeve criter |
| T3.2 | ORB_ASIA_15_v1__s75@1.0 | sleeve | 15,455 | 20,860 | 0.962 | 29,359 | ORB Asia | negative in IS; ORB_ASIA_15_v1 s60/s75 implies 14-68 extra NQ lots on top of Set A's 28 and worsens portfolio maxDD by 9-102% (sleeve criter |
| NM_E | E:ES_RSI2_t10 | sleeve | 6,279 | 6,140 | 0.9618 | 7,257 | dip-buy RSI2 family | ONE correlated exposure (NQ-ES weekly corr 0.73); post-selection from many sleeve cells |
| NM_E | E:NQ_RSI2CC_s20 | sleeve | 5,284 | 6,140 | 0.984 | 6,383 | dip-buy RSI2 family | ONE correlated exposure (NQ-ES weekly corr 0.73); post-selection from many sleeve cells |
| NM_E | E:NQ_RSI2C_s20 | sleeve | 5,284 | 6,140 | 0.978 | 6,383 | dip-buy RSI2 family | ONE correlated exposure (NQ-ES weekly corr 0.73); post-selection from many sleeve cells |
| NM_E | E:NQ_RSI2_t10 | sleeve | 5,099 | 6,140 | 0.976 | 5,496 | dip-buy RSI2 family | ONE correlated exposure (NQ-ES weekly corr 0.73); post-selection from many sleeve cells |
| T3.8A | ES_RSI2_t10 | sleeve | 12,559 | 13,252 | 0.9618 | 14,513 | dip-buy RSI2 family | ONE correlated exposure (NQ-ES weekly corr 0.73); post-selection from many sleeve cells |
| T3.7rsi2c | RSI2CC_s20 | sleeve | 2,646 | 3,219 | 0.984 | 3,196 | dip-buy RSI2 family | ONE correlated exposure (NQ-ES weekly corr 0.73); post-selection from many sleeve cells |
| T3.7rsi2c | RSI2C_s20 | sleeve | 10,568 | 12,856 | 0.978 | 12,766 | dip-buy RSI2 family | ONE correlated exposure (NQ-ES weekly corr 0.73); post-selection from many sleeve cells |
| T3.6b1 | RSI2_t10 | sleeve | 10,197 | 13,066 | 0.976 | 10,991 | dip-buy RSI2 family | ONE correlated exposure (NQ-ES weekly corr 0.73); post-selection from many sleeve cells |

## CANDIDATE (registered in PAPER-ALL; forward-scored)

| track | cell | object | effect | placebo | exposure | failed condition |
|---|---|---|---|---|---|---|
| NM_E | E:NQ_IBS_t20_n1 | sleeve | 4,232 | 0.9316 | IBS | placebo<0.95; placebo of record = min(5000-draw WF, 5000-draw pre-2024 fresh seed) = 0.932 |
| T3.7b4 | IBS_t20_n1 | sleeve | 8,465 | 0.9316 | IBS | placebo<0.95; placebo of record = min(5000-draw WF, 5000-draw pre-2024 fresh seed) = 0.932 |
| T3.2 | ORB_ASIA_30_v1__s50@0.25 | sleeve | 2,867 | 0.952 | ORB Asia | year_share>60% |
| T3.2 | ORB_ASIA_30_v1__s50@0.5 | sleeve | 5,734 | 0.952 | ORB Asia | year_share>60% |
| T3.2 | ORB_ASIA_30_v1__s50@1.0 | sleeve | 11,468 | 0.952 | ORB Asia | year_share>60% |
| T3.2 | ORB_ASIA_30_v1__s60@0.25 | sleeve | 4,001 | 0.976 | ORB Asia | worst of 1.5x/2x/1-s tape stress (T3.10b) = CANDIDATE; was PASS |
| T3.2 | ORB_ASIA_30_v1__s60@0.5 | sleeve | 8,001 | 0.976 | ORB Asia | worst of 1.5x/2x/1-s tape stress (T3.10b) = CANDIDATE; was PASS |
| T3.2 | ORB_ASIA_30_v1__s60@1.0 | sleeve | 16,003 | 0.976 | ORB Asia | worst of 1.5x/2x/1-s tape stress (T3.10b) = CANDIDATE; was PASS |
| T3.2 | ORB_ASIA_30_v1__s75@0.25 | sleeve | 3,598 | 0.964 | ORB Asia | year_share>60% |
| T3.2 | ORB_ASIA_30_v1__s75@0.5 | sleeve | 7,195 | 0.964 | ORB Asia | year_share>60% |
| T3.2 | ORB_ASIA_30_v1__s75@1.0 | sleeve | 14,390 | 0.964 | ORB Asia | year_share>60% |
| NM_B | B01_SetB | sizing-lock-session | 8,131 | 1.0 | Set B / PBDAY lock variants | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse |
| NM_B | B05_SetB_pb3R_vsA | sizing-lock-session | 9,066 | 1.0 | Set B / PBDAY lock variants | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse |
| NM_B | B05_SetB_pb4R_vsA | sizing-lock-session | 8,383 | 1.0 | Set B / PBDAY lock variants | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse |
| NM_B | B05_SetB_pboff_vsA | sizing-lock-session | 10,507 | 1.0 | Set B / PBDAY lock variants | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse |
| NM_B | B06_SetB_pb2R_noprofit_vsA | sizing-lock-session | 8,016 | 1.0 | Set B / PBDAY lock variants | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse |
| NM_B | B06_SetB_pb3R_noprofit_vsA | sizing-lock-session | 9,125 | 1.0 | Set B / PBDAY lock variants | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse |
| NM_B | B06_SetB_pb4R_noprofit_vsA | sizing-lock-session | 8,442 | 1.0 | Set B / PBDAY lock variants | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse |
| NM_B | B06_SetB_pboff_noprofit_vsA | sizing-lock-session | 10,566 | 1.0 | Set B / PBDAY lock variants | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse |
| NM_B | B07_SetB_Rscaled_pb2R_vsA | sizing-lock-session | 6,902 | 1.0 | Set B / PBDAY lock variants | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse |
| NM_B | B07_SetB_Rscaled_pb4R_vsA | sizing-lock-session | 8,344 | 1.0 | Set B / PBDAY lock variants | mean_not_down&(SD|maxDD down with CI) OR mean_up&maxDD_not_worse |
| T1 | T14_S_s50_t1.5_n14 | trade-modifier | 7,914 | 0.912 | T14_S_s50_t1.5_n14 | CANDIDATE by user ruling 2026-10-25 (scorer reads DEAD: paired CI includes 0, year share 68%, maxDD +5.7k, placebo 0.912; user registered it |
| NM_D | T14_S_s50_t1.5_n14 | trade-modifier | 8,016 | 0.912 | T14_S_s50_t1.5_n14 | CANDIDATE by user ruling 2026-10-25 (scorer reads DEAD: paired CI includes 0, year share 68%, maxDD +5.7k, placebo 0.912; user registered it |
| T4 | T4.2_Y4 | execution | 179 | 0.206 | T4.2_Y4 touch-join | year_share>60% |
| T3.8A | COMB_c3_R | sleeve | 2,831 | 0.9658 | dip-buy RSI2 family | placebo of record = min(5000-draw WF, 5000-draw pre-2024 fresh seed) = 0.966; worst of 1.5x/2x/1-s tape stress (T3.10b) = CANDIDATE; was PAS |
| NM_E | E:COMB_c3_R | sleeve | 5,118 | 0.9658 | dip-buy RSI2 family | placebo of record = min(5000-draw WF, 5000-draw pre-2024 fresh seed) = 0.966; worst of 1.5x/2x/1-s tape stress (T3.10b) = CANDIDATE; was PAS |
| NM_E | E:NQ_RSI2T_t10 | sleeve | 4,441 | 0.9112 | dip-buy RSI2 family | placebo<0.95; placebo of record = min(5000-draw WF, 5000-draw pre-2024 fresh seed) = 0.911; was PASS |
| T3.6b1 | RSI2T_t10 | sleeve | 8,882 | 0.9112 | dip-buy RSI2 family | placebo<0.95; placebo of record = min(5000-draw WF, 5000-draw pre-2024 fresh seed) = 0.911; was PASS |
| T3.8A | YM_RSI2_t10 | sleeve | 8,274 | 0.9514 | dip-buy RSI2 family | year_share>60%; placebo of record = min(5000-draw WF, 5000-draw pre-2024 fresh seed) = 0.951; was DEAD |

## DEAD: 659 cells listed once on the leaderboard with the failed condition (by track: {'T3': 314, 'T4': 13, 'T1': 150, 'T2': 74, 'HB': 28, 'NM': 80}). Null results state the detectable effect in the MDE column (weekly WF test cannot see less than $24,574/wk for an independent candidate; paired tests 0.03-2.5 pt/trade depending on the cell).

## Combined system (scored ONCE; prereg autopilot/DECISIONS.md + l2vast/struct48/prereg/COMBINED_prereg.md incl. amendments 1-2, sha256 in COMBINED_prereg.sha256, 9 trials)
Stack: Set B (CANDIDATE) as the D2 base + T4.2_Y4 in the primary run only (+0.0927 pt/trade; superseded and DEAD after the T4 full replay: excluded from the headline, see no_Y4) + one representative per independent sleeve exposure at a total sleeve risk budget of 0.5 x Set A SD: ORB_ASIA_15_v1__s60, RSI2C_s20, GSHORT_t90 (groups: ORB Asia; index dip-buy incl. IBS; GSHORT). Frozen sleeve set (14 series): COMB_c3_R, ES_RSI2_t10, GSHORT_t90, IBS_t20_n1, ORB_ASIA_15_v1__s60, ORB_ASIA_15_v1__s75, ORB_ASIA_30_v1__s50, ORB_ASIA_30_v1__s60, ORB_ASIA_30_v1__s75, RSI2CC_s20, RSI2C_s20, RSI2T_t10, RSI2_t10, YM_RSI2_t10.

| window | mean $/wk | d mean | SD | d SD | maxDD | d maxDD | worst week |
|---|---|---|---|---|---|---|---|
| WF | 41,783 | 16,808 | 110,255 | 5,732 | 356,755 | -44,538 | -202,750 |
| WFPRE | 33,673 | 16,124 | 106,202 | 8,670 | 356,755 | -44,538 | -159,173 |
| HOLD | 50,114 | 17,315 | 114,133 | 3,591 | 289,118 | 21,985 | -202,750 |
| L8W | 60,400 | 26,209 | 130,942 | 21,543 | 200,777 | -66,356 | -94,452 |
| IS | 9,335 | -4,336 | 85,046 | -10,900 | 372,066 | -35,187 | -164,908 |

Week-block bootstrap CI of the weekly WF difference (1,000 draws): [8,735, 25,426]; weekly corr (sleeves vs Set A) 0.02; annualised Sharpe Set A 1.72 -> combined 2.73 (marginal Sharpe up: True); deflated Sharpe of the combined weekly series 0.862 at 28,520 cumulative trials (post-selection: the sleeves come from many cells; the DSR is the corrected figure); placebo (independent circular shifts of each sleeve; informational, mean rank 0.99, Sharpe rank 0.972, maxDD rank 0.212).

Sensitivities (WF d mean $/wk; HOLD d mean): eq_weight: 16,807/17,884; budget0.25: 12,935/12,153; budget1.0: 24,554/27,639; NM_families_IBS_separate: 16,679/17,077; sleeves_only_on_SetA: 7,746/10,324; no_Y4: 15,880/16,290; rules_only_SetB_Y4: 9,062/6,991; PASS_only: 8,674/11,349; cost2x: 7,688 (sleeves only on Set A, 2x sleeve+D2 cost).

Honest reading: about half of the +$16.8k/wk is Set B (rules only: +$9.1k/wk WF, +$7.0k holdout; CI of Set B alone includes 0) and about $8k/wk is the sleeves on Set A (+$7.7k WF, +$10.3k holdout); Y4 adds ~$0.9k/wk. The holdout maxDD of the combined stack is $22k WORSE than Set A's (the WF maxDD gain comes from Set B and the pre-holdout window); SD rises $5.7k. The sleeve criterion is Sharpe-based; ORB Asia at this budget implies about 11 extra NQ lots and earlier sized variants worsen portfolio maxDD by 9-102% (a size/risk decision for the user). Sequence test: D2 locks, give-back, week floor and 50-contract limit act inside the D2 book unchanged; sleeves are separate books that do not feed them; peak-lot check is partial (ORB 14 lots/unit known; dip-buy/GSHORT lots-per-unit not in the manifest). Dip-buys have only 56-139 trades in WF; BRK and ON_none are DEAD after robustness (cost / drift-matched placebo).

## Landed after the 10-25 03:43Z edition (not re-scored into the combined system)
- **T2-SO2 scale-out** (autopilot/REPORT_STRUCT48_T2_SO2.md, rows/T2SO2_*.json): full two-leg direct L2 replay, shape-level placebo, 50-contract rule: 8 cells, 0 PASS / 0 CANDIDATE / 8 DEAD. Paired effect -0.24 to -0.03 pts/trade on 5,027 WF trades, every CI includes 0, holdout negative in all 8, MDE 0.41-0.76 pts/trade (a gain of +0.5 pts/trade or more is excluded for the f50 cells). Shape-level placebo ranks 0.97-1.00 (that condition is met; the base conditions fail).
- **REPORT_ASSEMBLY** (ST10/HM10/WT7 in one account with per-book locks; prereg sha 24c918d0..., 15 cells): both assembly rows DEAD (ASM_10_10_7_PB mean +$860/wk, maxDD +$136.5k worse, holdout -$4.95k; ASM_S141010_7_PB mean +$7.0k, SD +$21.5k, maxDD +$192k worse). The pair per-book vs combined give-back: DEAD as a per-book rule (same income, SD +$13.4k, maxDD +$158k). WT10 finding: "WT 7 lots at 45/0.75R" is NOT WT10 (WT10 = the 10-minute Wilder-trail book, a separate-account sleeve); it is the chart/live WT_MODAL. WT7 alone adds about +$1.4k/wk (t = 0.6).
- **REPORT_BACKLOG / BK1** (Set B on the exact 1-s sequence engine, 12 cells): Set B reproduces to the dollar (+$8,131/wk, maxDD -$81.5k) and stays CANDIDATE: 10,000-draw 8-week block CI [-84, 16,100] versus iid-week CI [1,032, 15,588] (the tier depends on the resampling scheme; per the user ruling Set B is judged by the block bootstrap); exact 1.5x/2x cost keeps the sign (+$2.6k / +$3.5k); the whole maxDD gain is pre-holdout and Set B alone does not worsen the holdout maxDD (-$10.8k). BEST5 DEAD. BK1_SETB_sizecredit scores PASS on an unverified size-impact-refund model and is merged into the Set B exposure (not counted). At 10,000 draws the PASS/CANDIDATE rows kept their verdicts.
- **JOIN_RECON** (section 5 replays every live attempt with the 10-19..10-23 tape): the live-vs-replay stop-exit gap is a fill-rate effect, not an exit-quality effect. Live join rate 8/17 = 0.47 [0.23, 0.72]; the replay rate depends on time of day (0.83-0.85 in 08:00-18:00 ET, 0.57-0.68 overnight), so reweighted to the live mix the expected rate is 0.65-0.69 and P(<= 8/17) is 0.05-0.09, not 0.005. Latency is not the cause. This lowers the weight to put on the replay-based execution cells (T4).
- **REPORT_EXT_1019_1024**: the week 10-19..10-24 L2 extension was bought for $35.59 (cap $40). **REPORT_FORWARD_TH**: 50 ST loss-side TH cuts replayed on direct mbp-10: paired +$893/trade, CI [-$1,897, +$3,611], P(d>0) 0.74; detectable effect $3.9k/trade = about $108k/week, so the null is uninformative; the sequence view (cuts buy extra attempts that lose) is roughly zero or negative.
- **T4 re-verdict under the user's MDE-based execution rule** (2026-10-25): T4.2_Y4 becomes CANDIDATE (+0.050 pt/trade [+0.017, +0.084] vs MDE 0.048; year share > 60% is its one failure). T4.4_W5 does NOT become CANDIDATE (effect 1.2x MDE passes the MDE condition, but neighbours disagree, the 2x-cost sign is negative and the year share is > 60%). T4.2_Lm2 does NOT (effect 0.54 x MDE, paired CI includes 0), nor T4.2_L0 (0.57 x MDE). T4 now stands at 0 PASS / 1 CANDIDATE / 13 DEAD.
- **User rulings 2026-10-25 applied**: T14_S_s50_t1.5_n14 is CANDIDATE by user ruling (the scorer reads it DEAD: CI includes 0, year share 68%, maxDD +$5.7k); Set B stays CANDIDATE; modelling-only variants are one exposure; placebo in [0.90, 0.95) is the one allowed secondary failure.
- **Effect on the combined stack (qualitative, NOT re-scored; it was scored once):** Y4 is now CANDIDATE at +0.050 pt/trade, about half of the +0.093 the primary run used (so the primary run overstates Y4 by roughly $0.4k/wk; the no_Y4 headline is unaffected, adding Y4 at its true size would add about +$0.5k/wk); T14_S (CANDIDATE by ruling, shorts-only bracket on D2) was not part of the stack and would modify D2 itself, so its interaction with Set B is untested; the sleeve set was frozen with the 10-24 T3.10b verdicts and is unaffected.
- **Per-track reports:** REPORT_STRUCT48_T1.md (10-24 16:00Z; T1_PREHOLD), _T2.md (17:50Z) and _T2_SO.md / _T2_SO2.md, _T3.md (15:17Z) with _T3_1.._T3_9 and _T3_10b addenda, _T4.md (17:35Z) with _T4_PREHOLD, _HB.md. All five tracks have reports; later addenda are listed above.

## Process notes
- Verdict function of record: s48score.verdict (placebo in [0.90,0.95) is the one allowed secondary failure; sizing branch needs mean CI > 0); NM interim verdicts reproduced with 0 differences (autopilot/NEARMISS_RESCORE_LEAD_CHECK.md). Placebo of record for sleeves = min(5,000-draw WF rank, 5,000-draw pre-2024 fresh-seed rank) where stored.
- Single-failure DEADs ruled by the letter (E5S placebo 0.894 etc.); cells with no stored placebo counted as failed; T14_L_s50_t2.0_n10 and T14_C never received their direction-shuffle placebo, so they stay DEAD (open, listed as such).
- Tier-count reconciliation: the 12:27Z LEADERBOARD.md (661 DEAD / 19 PASS / 26 CANDIDATE / 10 PENDING) was written by a loop process still running pre-ruling code (it lacked the user ruling on T14_S, the MDE-based execution rule that makes T4.2_Y4 CANDIDATE, and the forward-column parser). After restarting the loop at 12:34Z the leaderboard, MORNING block and this report agree: 659 DEAD / 18 PASS / 29 CANDIDATE / 10 PENDING cell rows (duplicates of the same series included). Independent exposures: PASS = dip-buy RSI2 family, ORB Asia, GSHORT; CANDIDATE = IBS, Set B / PBDAY (one exposure), T4.2_Y4, T14_S_s50_t1.5_n14 (by user ruling), plus the CANDIDATE members of the dip-buy and ORB Asia families.
- Holdout: one look for the COMBINED track (ledger/holdout_looks.jsonl).
