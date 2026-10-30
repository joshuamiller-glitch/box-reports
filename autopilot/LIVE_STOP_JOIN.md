# LIVE_STOP_JOIN - the stop-join leak (PLAN36 section 7). 2026-10-30. Tier: LEAD (live n small).

## PAGE 1 - RECOMMENDATION AND DOLLAR FIGURE

**One line: switch the ST and HM stop exit from JoinThenMarket (3 s) back to Native stop-market now; the live join costs 2.45 pts per stop vs 1.28 for Native, = about +$4.4k/wk at 10 lots (95% CI -$1.0k to +$9.9k, one-sided p 0.055), because the join fills 38% of the time (n=21, 95% CI 21-59%) and needs 64% to break even.**

| quantity | value | n | 95% CI | status |
|---|---|---|---|---|
| Join fill probability, 3 s, DualStrat2 ST+HM (REJ counted as not filled) | 0.38 (8 of 21) | 21 | 0.21 - 0.59 | MEASURED |
| same, all join-mode stops in the files (ST, HM, PB, K5, M5, M6, P6) | 0.40 (14 of 35) | 35 | 0.26 - 0.56 | MEASURED |
| Replay (P9) join fill probability | 0.78 | 4,330 | | prior report; live is below it |
| Stop cost vs nominal stop level, join (3 s), ST/HM | 2.45 pts | 21 | 1.04 - 3.86 | MEASURED |
| of which filled / fallback | -0.52 (8) / +4.46 (12) | | -1.21..+0.18 / +2.83..+6.09 | MEASURED |
| Stop cost vs nominal, Native stop-market (ST_Stop 3, WT_Stop 5) | 1.28 pts (SE 0.13) | 8 | 1.03 - 1.53 | MEASURED, different books (WT stop is 45 pts) |
| Join minus Native | +1.17 pts, SE 0.73, z 1.6 | 21 vs 8 | -0.26 .. +2.60 | not significant, direction consistent with the model |
| Break-even join fill probability vs Native | 0.64 | | | derived |

Dollar figure: ST+HM stops per week from the exact per-book lock engine, L6M (20250801-20260206, 28 weeks): ST 10.25 + HM 8.68 = 18.93 stops/wk. Live-lot mapping: lock-engine live lots ST 10, HM 10 (the stack's convention, NQ $20/pt/contract), so $3,786 per pt-per-stop per week. The live fills show qty 10-14 on these stops (median 14): at 14 lots multiply every dollar figure by 1.4 (+$6.2k/wk, CI -$1.4k to +$13.8k). The 18.9/wk is the engine's rate; the live files show 21 ST/HM stops in 8 trading days (about 13/wk), so the engine rate may be high by up to 40% (lower the dollars proportionally).

Reading: the replay promised the join earns +0.85 to +1.0 pt per stop over market (about +$3k/wk). Live it is at best a wash and probably a cost, because live fills are half the replay rate. It is a LEAD, not a PASS: the Native comparison is n=8 from other books, and the join sample is 21 stops in 8 trading days, 18 of them with 1-s path.

## What is measured and what is modelled

| item | measured (live) | modelled (tape, labelled) |
|---|---|---|
| join 1 s, 2 s, 3 s fill probability | yes: fill-time CDF of the live 3 s join (the timer cancels at about 3 s, so fills by 1 or 2 s are exactly what a 1 s or 2 s join would have got) | |
| join 4 s, 5 s | NO (lower bound only) | yes |
| market-leg cost after a shorter or longer wait | path-based for 1-3 s (validated: rule gives 4.14 vs realised 4.25, n=9) | yes for 5 and 8 s |
| by session | counts only (asia 8 of 26, london 5 of 5, nyam 0 of 2, nypm 1 of 2; asia is 74% of the sample) | yes (n=1,497 events) |
| by distance past the stop at placement | 18 path-covered stops, 3 coarse bins | yes |
| Native | 8 live stops | tape-based paired comparison |

## Join fill probability by join seconds

| join s | MEASURED P(fill) [95% CI], n=18 path-covered | MEASURED hybrid cost, pts/stop (SE) | MODELLED P(fill) [95% CI] (n=1,497) | MODELLED band over the 6 models consistent with live | MODELLED E[cost] join, pts | MODELLED join minus Native, pts (SE) |
|---|---|---|---|---|---|---|
| 1 | 0.33 [0.16,0.56] | 1.71 (0.73) | 0.29 [0.27,0.31] | 0.28-0.42 | 1.81 | +0.81 (0.15) |
| 2 | 0.39 [0.20,0.61] | 1.56 (0.73) | 0.42 [0.40,0.45] | 0.42-0.54 | 1.93 | +0.93 (0.15) |
| 3 | 0.39 [0.20,0.61] | 1.84 (0.86) | 0.51 [0.48,0.53] | 0.49-0.61 | 2.03 | +1.03 (0.17) |
| 5 | not measured | not measured | 0.58 [0.56,0.61] | 0.58-0.69 | 2.16 | +1.16 (0.18) |
| 8 (extra) | not measured | not measured | 0.66 | 0.65-0.75 | 2.17 | +1.16 (0.19) |

Native for comparison: 1.28 live (n=8), 1.01 basis M, 1.00 in the tape model (exit-side best at the end of the trigger second, a pessimistic native). Live 3 s join, all: 2.45 (n=21).

Model definition (queue-position model, NOT measured): the stop events are the engine's ST/HM stops 2025-01 to 2026-02-06 (n=1,497 after dropping 86 with no tape alignment; trigger row found at the expected row in 93%); tape levels are put on the tape basis by the per-event entry-to-tape offset (rolling median, so contract rolls are handled). The join is a limit at the own-side best, placed L=1 s after the trigger second, filled if the tape trades q=6 ticks (1.5 pts) through the limit within the join window, else market at the window end plus the live-measured fallback slip (+0.86 vs path). L and q are fitted to four live numbers (fill at 1 s and 3 s, fallback cost 4.46, total 2.45; chi2 2.1 for 4 numbers): two fitted parameters, so the model SHAPE by join seconds is informative, its LEVEL is not independent evidence. The pure touch-fill queue (q=0) gives 83% at 3 s, close to the replay's 78%: the live gap to the replay is the queue/latency, and q=6 is a heavy queue.

Result by join seconds: every variant is more expensive than Native in the calibrated model (+0.8 to +1.2 pts); shorter is better (1 s is the cheapest join) because the fill probability barely rises with time while the fallback leg pays for the extra drift (about +1 pt per extra second waited in the model's fallback leg). Measured hybrid at 1/2/3 s (1.71 / 1.56 / 1.84) is flat within its SE of 0.7; the join-seconds choice does not rescue the join, only the choice join vs Native matters.

## By session (MODELLED, join 3 s; live counts above)

| session | n events | P(fill) | E cost join | join minus Native |
|---|---|---|---|---|
| asia | 170 | 0.35 | 3.27 | +1.94 (0.43) |
| london | 279 | 0.46 | 2.66 | +1.07 (0.55) |
| NY-AM | 569 | 0.58 | 1.26 | +0.76 (0.24) |
| NY-PM | 366 | 0.48 | 2.50 | +1.09 (0.31) |

Live: asia 8 of 26 (0.31), london 5 of 5 (n=5), NY 1 of 4. The model and the live both put the worst join in Asia (thin book), which is also where most live stops occur (26 of 35). Session order is consistent between model and live but the live cells are tiny.

## By distance the price had already run past the stop at placement

| distance at placement | MEASURED (live, 3 s join, n=18) P(fill) | MODELLED P(fill) 1 s / 3 s / 5 s | MODELLED join minus Native, 1 s / 3 s |
|---|---|---|---|
| <= 0.5 pt (66% of events) | 0.50 (3 of 6) | 0.26 / 0.49 / 0.56 | -0.38 (0.16) / -0.22 (0.17) |
| 0.5 - 3 pt (21%) | 0.50 (3 of 6) for 0.5-1.5; 0.33 (2 of 6) for >1.5 | 0.20-0.30 / 0.46-0.50 / 0.53-0.60 | +2.01 (0.19) / +2.26 (0.22) |
| > 3 pt (12%, gap stops) | n/a | 0.54 / 0.67 / 0.76 | +5.2 (0.65) / +5.7 (0.82) |

The distance at placement is the one clean decision variable: when price has not run beyond the stop (within a half point) the join is cheaper than Native in the model (about -0.4 pt at 1 s); when it has, the join is worse (+2 to +6 pts), as the fallback then chases a moving market. The model's number of events behind the three bins is large; the live bins (3 of 6, 3 of 6, 2 of 6) carry no power (any difference is within noise). This is a post-hoc finding from the tape, selected by looking at the distance bins: LEAD (modelled only).

Conditional rule (MODELLED, post-hoc-selected, one look, not a recommendation to ship): join for 1 s only if the own-side best is within 0.5 pt of the stop at placement, otherwise Native. Gain vs always-Native = 0.66 x 0.38 = about 0.25 pt per stop = about $0.9k/wk at 10 lots (about 1/5 of the size of the Native-vs-live-join difference). Needs the Phase 1 Sim A/B before any live use.

## Expected stop cost under Native vs JoinThenMarket (pts per stop, vs nominal stop level; $/wk at 10 lots x 18.93 stops/wk)

| arm | pts (SE) | $/wk | basis |
|---|---|---|---|
| Native stop-market, live | 1.28 (0.13) | 4,846 | measured n=8 |
| Native, basis M | 1.01 | 3,824 | replay |
| JoinThenMarket 3 s, live | 2.45 (0.72) | 9,276 | measured n=21 |
| JoinThenMarket 1 s / 2 s / 3 s, measured hybrid (n=18) | 1.71 / 1.56 / 1.84 (0.7-0.9) | 6.5k / 5.9k / 7.0k | measured fills + path market leg |
| JoinThenMarket 1 / 2 / 3 / 5 s, queue model | 1.81 / 1.93 / 2.03 / 2.16 (0.25) | 6.9k / 7.3k / 7.7k / 8.2k | modelled |

Ranking by cost: Native, then a 1-2 s join, then 3 s, then 5 s. The hypothetical Native on the same 18 path-covered join stops (market at the path last of the trigger second + 1.01) is 2.20, which would put the join ahead by 0.36; that reference is the end-of-second price (the real stop fires at the first print, earlier), so it overstates Native. The three Native views (live 1.28, M 1.01, same-sample path 2.20) bracket the answer: the join is better than Native only against the weakest Native reference. That is why this is a LEAD with the live Native n=8 as the main caveat.

## What is needed to decide (for the Phase 1/2 Sim A/B in P9_NT8_SPEC)

At the live rate (13 to 19 ST/HM stops/wk) 40 Native stops arrive in 2.5 to 3 weeks. For the Native-vs-join difference of 1.2 pts with a per-stop SD near 3 pts, n=40 per arm gives SE 0.67 (z 1.8); n=80 per arm is needed for a clean call. The cheapest test is to keep the current join on one book and run Native on the other for two weeks (live fill rate ST 5 of 11, HM 3 of 10: not distinguishable).

## Scope and data handling

Only the sanctioned live cost calibration was used: real-account exit fills from 2026-10-20 (the DualStrat2/DS3/DS5/DS6/DualStrat strategy files, columns strategy, exit name, side, qty, entry/exit time, entry/exit price; no account id column, no P&L columns, no nt8log, no order-level text, no earlier dates). Outputs are aggregated tables only (no raw rows). Historical data used by the model is capped at 2026-02-06 (the 1-s parquet is read with a timestamp filter at the cut); nothing after is loaded. The live path (1-s) ends 2026-10-23 21:00 UTC, so only 18 of the 22 known-level join stops have timing; the rest have outcome and price only. Join-seconds as run live: one value (3 s); the placement time and the distance at placement are not logged in the fills, so the distance is the last print of the trigger second against the stop level (a proxy) and is path-limited.

## Known weaknesses

* Join sample: 21 ST/HM stops in 8 trading days; all join-mode stops (n=35) fill probability by ET day is 0.29, 0.33, 0.40, 1.00 (10-23, n=3), 0.00 (10-25, n=3), 0.30, 1.00, 0.50: no trend but wide spread. The 10-26..30 half has p 0.43 (n=14) with 6 rejects in DS5/DS6 (a different engine, outside the 21).
* "Rejected" is counted as not filled (1 of 21 in ST/HM, 6 of 13 in DS5/DS6: a separate bug-like failure mode in the DS5/DS6 join orders, worth the platform owner's look).
* Native sample n=8: 3 ST_Stop (DualStrat, a different account strategy file) + 5 WT_Stop (45-pt stop level taken from the engine table); the SE of 0.13 is small, but the sample is not the ST/HM population. Same books native would need to be run to close the gap.
* The model is calibrated to the live fill numbers, so it cannot independently confirm the live level; its added value is the shape in join seconds, session and distance, which is consistent with live direction in each case where live has any power.
* No multiplicity: 4 join-second values, 4 sessions, 4 distance bins; none selected on a PRE/HOLD split (live and tape are different data); the distance rule is post-hoc.

Code: l2vast/ds3/code/stopjoin/ (sj_common.py, sj_live.py, sj_hybrid.py, sj_model.py, sj_analyze.py, sj_stops.py). Outputs: l2vast/ds3/out/stopjoin/ (LIVE_STOPJOIN_AGG.md, HYBRID_J.md, MODEL_TABLES.md, stack_stops_per_week.csv, JSON summaries).
