# DS3_P9_PB3B_R5_P1 - P9 robustness block on the single cell PB3B_R5_P1 (D3SPEC, 2026-10-27)

Research output; NOT a live recommendation. Cell: 5-min Supertrend(ATR10 x3) regime, 1-min EMA20 touch, extreme-break trigger, DS2 bracket 60/1.0R, 10 lots (spec: autopilot/DS3_SPEC_PB3B_R5_P1.md; prereg l2vast/ds3/prereg/PB3_PB3B_prereg.md; verdict CANDIDATE, DIRECT basis). No new prereg (an already-registered cell is stress-tested). Code: l2vast/ds3/code/p9_lib.py, p9_heavy.py (blocks a, d), p9_light.py (b, c, e, f), p9_addbook.py; outputs l2vast/ds3/out/p9_pb3b/ (p9_heavy.json, p9_light.json, random_trigger_draws.csv, addbook_PB3B_R5_P1.json). NO replay worker was started; block (d) re-prices the existing direct replay rows only. Heavy jobs ran single-process through corepool. Holdout disclosure: the add-to-DS3 and capacity calls re-read the holdout through ds3_addbook (5 logged looks, track D3SPEC_PB3B_R5_P1 / D3SPEC_PB3B_R5_P1_CAP in l2vast/ds3/ledger/addbook_looks.jsonl).

Windows (te_core.WIN_W): PRE 2024-02..2025-06 (75 wk), WF 2024-02.. (143 wk to 2026-10-23), HOLD 2025-07.. (69 wk), SPAN 2023-04..2024-01 (44 wk). Series: l2vast/ds3/out/SERIES/DS3_TPULLBACK3_PB3B_R5_P1.parquet (direct basis, 10 lots, exact per-book locks). Weekly SD of the cell about $50k; WF standard error of the mean about $4.2k.

## Summary of verdicts
| block | test | verdict | one line |
|---|---|---|---|
| a1 | mirror (regime sign flipped; trade side inverted) | HOLDS | both mirrors lose (-13.9k and -19.7k $/wk WF, mapped); real beats them by +25k / +31k per week, CIs exclude 0 |
| a2 | random-time trigger at the same take-rate | FAILS | 40 random-in-regime draws average 11.8k vs real 11.1k (mapped WF); real rank 0.40; paired real - random -0.8k/wk [-6.9k, +5.4k]: the pullback timing adds nothing detectable |
| b | day-block bootstrap maxDD / worst week | HOLDS | observed maxDD 361k sits at the 70th percentile of the bootstrap (median 309k, 5-95% 205k-521k); P(boot > observed) 0.30 |
| c | VIX terciles (as-of prior close) | HOLDS | positive in every tercile (low 18.4k, mid 10.2k, high 15.7k $/wk WF); differences not significant |
| d | fill sensitivity (existing direct replay) | WEAKENS | scored arm 15.2k; without XJ stop-join 13.1k; all-market EM arm 7.9k (-48%); mapped 11.1k; +1 s/+2 s delay arms do not exist |
| e | 1.5x / 2x cost | HOLDS | 12.4k / 10.9k $/wk WF; HOLD 15.8k / 13.1k; SPAN 5.7k / 4.8k |
| f | capacity to 42 lots, equal risk, 50-cap | WEAKENS beyond about 24 lots | equal-risk lots 11.5 give +2.9k/wk vs ST10; WF Sharpe falls 2.17 -> 1.24 at 42 lots, marginal DS3 Sharpe reaches 0 by 30 lots |
Net: the block weakens the case (a2, d, f); it does not break the cell as a long-regime bracket book, it breaks the claim that the pullback entry is the source of the edge.

## (a) Cell-specific mirror and random-time trigger (MAPPED basis, same lock engine; real cell regenerated = library list, 8,339 raw trades, uid-identical)
Mapped basis is used for all three arms because no direct replay exists for the new trade lists (no replay workers). Real cell mapped WF 11,077 $/wk (direct 15,248).
| arm | raw trades | raw pts/trade (1-s path, before costs) | PRE | WF | HOLD | SPAN | paired real - arm, WF $/wk [95% CI] |
|---|---|---|---|---|---|---|---|
| real (mapped) | 8,339 | +1.47 | 7,559 | 11,077 | 14,741 | 605 | - |
| A: regime sign flipped (long rules in a regime-down, short rules in a regime-up; same touch/trigger) | 7,724 | -1.87 | -16,234 | -13,930 | -11,224 | -10,761 | +25,007 [9,304, 40,236] (PRE +23.8k, HOLD +26.0k, all CIs exclude 0) |
| B: same signals, opposite side (same bar, 60/1R) | 8,339 | -1.47 | -10,529 | -19,685 | -29,353 | -11,346 | +30,762 [15,901, 45,441] (PRE +18.1k [-3.3k, 40.0k], HOLD +44.1k) |
| C: random-time trigger, 40 draws (per regime side, each qualified 1-min bar fires with probability 5.1% = library events / bars in that regime side; same bracket/locks) | mean 9,119 | +1.36 | mean 8,434 (5-95%: 3,032-14,812) | mean 11,829 (6,506-17,219) | mean 15,348 (7,377-22,489) | 1,149 | real minus mean-of-draws: -752 [-6,921, 5,364] (PRE -875, HOLD -607); real rank among draws WF 0.40, PRE 0.375, HOLD 0.525 |
Reading: the direction of the 5-min Supertrend regime carries the P&L (both mirrors lose money, symmetrically so for the 60/60 bracket), but replacing the EMA20 pullback + extreme-break timing with a random minute inside the same regime direction at the same take-rate gives the same or slightly higher P&L (rank 0.40). The paired CI says the pullback timing is worth between -6.9k and +5.4k $/wk against random timing in the regime; the MDE of this paired weekly test is about 8.5k $/wk, so a small positive effect cannot be excluded either. This agrees with paired vs ST10 of -0.3 pts/trade [-2.4, 1.7]. Verdict: mirror HOLDS; random-time FAILS (no evidence the entry rule adds anything over the regime); block WEAKENS the entry-mechanism claim. The cell is a regime-direction book with a pullback label.

## (b) Day-block bootstrap of maxDD and worst week (direct series, WF 2024-02..2026-10-16 for both books, 701 days, 10,000 draws)
Moving blocks of b days (b = 1, 5, 10) concatenated to the sample length; maxDD from the daily equity path; worst week = worst non-overlapping 5-day chunk of the resampled path (observed worst = calendar week).
| book | observed maxDD | b | maxDD median | 5% - 95% | P(boot maxDD > observed) | worst-5d median | 5% - 95% | P(boot worst < observed) |
|---|---|---|---|---|---|---|---|---|
| PB3B_R5_P1 | 361,439 | 1 | 365,855 | 234,508 - 632,021 | 0.515 | -127,455 | -156,283 to -101,095 | 0.83 |
| | (obs worst week -110,301) | 5 | 308,530 | 204,985 - 521,069 | 0.296 | -109,962 | -124,051 to -91,455 | 0.34 |
| | | 10 | 297,068 | 197,322 - 495,211 | 0.252 | -109,962 | -124,051 to -89,284 | 0.34 |
| ST10 (DS2 true P9, 10 lots) | 263,432 | 5 | 346,391 | 226,914 - 589,994 | 0.847 | -116,186 | -127,730 to -91,189 | 0.94 |
| | (obs worst week -91,189) | 1 / 10 | 395,538 / 324,074 | 250,936-691,615 / 215,102-541,222 | 0.92 / 0.79 | | | |
Reading: the observed 361k maxDD of the cell is a typical outcome of its own bootstrap (P(exceed) 0.30 at b = 5; 0.52 for iid days), while ST10's observed 263k is at the 15th percentile of ST10's bootstrap (a lucky path). The bootstrap 95th percentile for planning is about 520k at 10 lots (about 590k for ST10), i.e. the 1.4x observed maxDD gap to ST10 is mostly path luck, not a larger tail. Block bootstraps understate regime clustering (the 2024 drawdown is one episode); MDE: with 701 days the bootstrap maxDD interval is +/-40% wide, so differences under about 40% between two books' drawdowns are not resolvable. Verdict: HOLDS.

## (c) VIX terciles (VIX close of the last date before the week's first label day, trailing 120-observation terciles, min 40; thresholds 12.9-21.8 over WF; file k4/state/vix.csv, last date 2026-10-16, weeks 10-19..23 use the 10-16 close; 0 unlabelled weeks)
| WF weeks by tercile | PB3B_R5_P1 weeks | mean $/wk | SD $/wk | Sharpe | ST10 weeks | mean | SD |
|---|---|---|---|---|---|---|---|
| low | 55 | 18,393 | 49,587 | 2.67 | 55 | 24,096 | 63,078 |
| mid | 38 | 10,212 | 52,157 | 1.41 | 38 | 4,523 | 54,803 |
| high | 50 | 15,677 | 49,134 | 2.30 | 49 | 11,003 | 51,650 |
By year (PB3B_R5_P1, mean $/wk, weeks): 2024 all 7,275 (49) = low 6,066 (17), mid 13,105 (14), high 3,883 (18); 2025 all 21,621 (52) = low 20,373 (20), mid 15,252 (12), high 26,692 (20); 2026 (to 10-23) all 16,731 (42) = low 27,834 (18), mid 1,797 (12), high 15,010 (12). MDE: with 38-55 weeks per tercile the standard error of a tercile mean is 7-8k and a difference between two terciles needs about 29k $/wk to be detectable (80% power); no tercile difference is detectable, and no tercile is negative. The weakest cell is mid-VIX in 2026 (+1.8k, 12 weeks, indistinguishable from the cell mean). Verdict: HOLDS (no regime-of-VIX dependence shown; no power to claim independence either).

## (d) Fill sensitivity from the existing direct replay (no new workers; 97.9% of trades have replayed fills, the rest mapped)
Per-trade pts re-priced through the same lock engine (l2vast/ds3/code/p9_heavy.py). Arms available in the replay: S10x1_g2 (10 x 1-lot market slices 2 s apart), EM (all-market 10 lots), XJ (stop-join gain on stop exits, a pts delta over the S10x1 base). Mapped = path-table mapping.
| arm | PRE | WF | HOLD | SPAN | mean pts/trade | WF at 2x execution+commission |
|---|---|---|---|---|---|---|
| scored: S10x1_g2 + XJ3 gain (+0.5) | 11,859 | 15,248 | 18,711 | 5,996 | 1.73 | 10,908 |
| S10x1_g2 without XJ gain | 11,738 | 13,083 | 14,355 | 2,648 | 1.32 | 8,259 |
| EM (all-market) without XJ | 6,601 | 7,907 | 9,212 | 982 | 0.31 | -398 |
| EM plus the XJ gain (upper bound; XJ was measured on the S10x1 base) | 7,403 | 7,929 | 8,385 | 5,885 | - | - |
| MAPPED (path table) | 7,559 | 11,077 | 14,741 | 605 | 1.64 | 9,553 |
XJ3 gain: +0.41 pts/trade on average (14% of the WF headline; 2,165 $/wk). Market slicing instead of the 2-s passive-ish S10x1 costs a further 1.0 pts/trade (5.2k $/wk). +1 s / +2 s delay arms DO NOT EXIST in the replay output (arms are only EM, S10x1_g2, XJ); not tested. Bound instead: one extra point of adverse slippage per trade costs 10 lots x $20 x 27 trades/wk = about $5.5k/wk, so the scored WF mean is exhausted at about 2.8 pts/trade of extra slippage over the scored fills; the all-market arm already uses up 1.4 pts. The cell stays positive in WF under every arm at 1x, but under the all-market arm it halves and is zero at 2x cost; the 2023-04..2024-01 span is about zero under EM, mapped and no-XJ. MDE: the arms re-price the same trades, so differences are deterministic given the fills; the uncertainty is the fill model itself (not sampled), and no CI is given for an arm difference. Verdict: WEAKENS (the headline depends on S10x1 + XJ3, both unvalidated live; the XJ part alone is 14%).

## (e) Cost 1.5x and 2x (series columns pnl_1p5x / pnl_2x: execution excess x1.5 / x2 and commission scaled; direct basis)
| cost | PRE mean / SD / maxDD | WF mean / SD / Sharpe / maxDD / worst | HOLD mean / SD | SPAN mean / SD |
|---|---|---|---|---|
| 1x | 11,859 / 51,292 / 361k | 15,248 / 49,890 / 2.20 / 361k / -110k | 18,711 / 48,205 | 5,996 / 38,133 |
| 1.5x | 9,158 / 49,712 / 466k | 12,424 / 49,176 / 1.82 / 466k / -109k | 15,794 / 48,488 | 5,716 / 36,686 |
| 2x | 8,771 / 47,745 / 446k | 10,908 / 48,554 / 1.62 / 446k / -89k | 13,072 / 49,585 | 4,806 / 36,298 |
(ST10 is not re-scaled here.) At 2x the WF mean is 72% of 1x (t = 10.9k / (48.6k/sqrt(143)) = 2.7). MDE: 80% power on WF needs a mean of about 11.4k; the 2x WF mean (10.9k) is at the detection limit, the HOLD 2x mean (13.1k on 69 weeks) is not individually significant (SE 6.0k). Verdict: HOLDS (positive in every window and cost, Sharpe 1.6 at 2x).

## (f) Capacity to 42 lots, equal risk, 50-lot cap (equal_risk.py, sweep-cost surface riskS5/results/s113_NQ.csv: 4.6 excess ticks/lot RT at 10-14 lots, 5.9 at 20, 7.7 at 30, 9.4 at 42; series trades column for the charge; WF calendar of s48score = 142 weeks to 2026-10-16)
| lots | WF mean $/wk | WF SD | WF Sharpe | WF maxDD | worst week | HOLD mean | mean as % of linear | marginal DS3 Sharpe (base KB+SM+EM) WF / HOLD (PRE) |
|---|---|---|---|---|---|---|---|---|
| 10 | 15,062 | 50,017 | 2.17 | 361k | -110k | 18,374 | 100% | +0.26 / +0.45 (+0.09) |
| 11.5 (equal-risk to ST10) | 17,322 | 57,519 | 2.17 | 416k | -127k | 21,131 | 100% | - |
| 14 | 21,088 | 70,024 | 2.17 | 506k | -154k | 25,724 | 100% | - |
| 20 | 26,628 | 99,841 | 1.92 | 804k | -223k | 32,909 | 88% | +0.16 / +0.33 (0.00) |
| 24 | 29,438 | 119,678 | 1.77 | 1.02M | -269k | 36,729 | 81% | - |
| 30 | 32,622 | 149,389 | 1.57 | 1.38M | -339k | 41,326 | 72% | +0.01 / +0.16 (-0.13) |
| 42 | 36,027 | 208,703 | 1.24 | 2.15M | -481k | 47,268 | 57% | -0.13 / +0.01 (-0.25) |
Equal risk vs ST10 (same WF weekly SD 57,331): 11.46 lots, 17,265 $/wk vs ST10 14,350: +2,915 $/wk (this difference is not distinguishable from 0: the weekly difference at equal lots has CI [-8.3k, +8.7k]). Zero-mean capacity 107 lots, zero-delta-vs-ST10 119 lots, practical ceiling (mean >= 80% of linear) 24 lots. The marginal DS3 Sharpe is computed on the series with the sweep cost at each lot count (risk-parity weights make it scale-free except for the cost); it falls from +0.26 to +0.01 (WF) between 10 and 30 lots and is negative at 42.
50-lot cap: DS2 books ST10/HM10/WT7 are 10/10/7 = 27 lots at worst; the cell is one position at a time, so nominal peak = its lots: 27 + L <= 50 requires L <= 23 (so 42 lots is not feasible beside DS2; at the equal-risk 11.5 lots the worst case is 38.5). From the per-trade replay intervals (pre-lock, direct S10x1_g2 entries/exits) the peak concurrent lots are 2x nominal because 163 of 8,161 trades (2.0%) overlap the next entry by minutes (replay exit later than the library bar exit): peak 23 at 11.5 lots, so worst case with DS2 = 50, exactly at the cap; this overlap is a replay-timing artefact the lock engine would normally absorb, but it is the number the cap check should use. MDE: lots scaling is deterministic given the sweep surface; the surface is measured on market sweeps and extrapolated linearly above 56 lots (not used here), S10x1/XJ fills are conservative relative to it. Verdict: HOLDS to about 12-14 lots at constant Sharpe, WEAKENS from 20 lots (Sharpe 1.9, maxDD 0.8M), and the DS3 diversification value is gone by 30 lots; 42 lots is not a sensible size.

## Recommendation (one paragraph)
PB3B_R5_P1 remains a CANDIDATE and the P9 block weakens the case rather than strengthening it. What the evidence supports: a positive 5-min-Supertrend-direction bracket book with 27 trades/wk, +15.2k $/wk WF at 10 lots on the direct basis (HOLD +18.7k, span +6.0k), positive under both mirror and cost stress (mirrors lose; 2x cost still +10.9k), positive in each VIX tercile, a maxDD (361k) that is a typical draw of its own bootstrap (planning figure 520k at 10 lots), and at equal risk to ST10 a +2.9k $/wk higher mean with a positive DS3 add-one Sharpe in the holdout (+0.45 with KB+SM+EM, +0.48 with KB+SM; WF-PRE negative with KB+SM). What it does not support: (1) that the pullback entry is the source of the edge: a random minute inside the same regime direction at the same take-rate does as well (rank 0.40), and paired vs ST10 is -0.3 pts/trade [-2.4, 1.7] (MDE 3.0), so the entry rule is not distinguishable from ST's flip entry or from random timing; (2) that the P&L is robust to execution: 14% of the headline is the XJ3 stop-join, the all-market arm halves it, and S10x1 slicing and XJ3 are unvalidated live; (3) any size above about 12-14 lots: Sharpe and the DS3 marginal fall as lots rise and the 50-lot cap with DS2 allows at most 23; (4) a statistically proven edge: V2 gates are not softened, the verdict stays CANDIDATE (not PASS) because the paired-vs-ST criterion and the maxDD-not-worse criterion fail. The case for including it, if any, is dollar-for-dollar at equal risk (+2.9k $/wk, not significant) and its DS3 marginal Sharpe, both of which come from the shared regime with ST10 rather than from the pullback. Forward evidence cannot settle it quickly: at 50k weekly SD a mean of 15k needs about 85 weeks for 80% power versus zero.
