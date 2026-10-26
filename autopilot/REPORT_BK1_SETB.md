# REPORT BK1 - Set B / BEST5 on the exact 1-s engine, full sequence (robustness backlog item, V2 sec 7; BK, 2026-10-24)

Research only. Prereg `l2vast/struct48/prereg/BK1.md` sha256 `f032026569bc750ebafbf94e671ef637ced6ed9375c6915a3a60b2d96cdc10fb` (12 cells, ledger appended: cumulative 28,523 trials; DECISIONS.md line 18:54Z). Pre-holdout text `autopilot/REPORT_BK1_PREHOLD.md` (WF-PRE + IS only) sha256-logged via `log_holdout_look('BK1')` before any holdout number was computed. **The holdout is a RE-READ**: Set B / PBDAY / BEST5 holdout numbers were already printed in REPORT_PBDAY, FWD_AB_SETS and NM-B (this run reproduces them to the dollar), so the holdout here is not blind.

## Engine and what "exact" means here
- Engine: `pairP2/firm/riskeng_pb.py`, the stateful 1-second simulator on the 1-s NQ tape (ds2 SS/SC arrays) with corrected-P9 per-signal points (L2 replay: S14x1 entries, stop-join exits at live cost 1.01 pt, $4.84 RT/contract). The sequence is simulated second by second: per-book day limits (-2R/+5R), combined cap (Set A: 8R flatten; Set B: off), give-back (arm 2R, keep 50%), week floor (Set A 8R, Set B 12R), session lots (Set A 14/14/14, Set B 14/10/10 Asia/London/NY), halts, scale-downs at the next printed second. Reproduction: Set A WF 24,978 (hard-lock engine 24,975), Set A at 2x cost 19,235 (hard-lock engine 19,265), Set B 33,109, maxDD 320,103 (= PBDAY/NM-B to the dollar), BEST5 25,536 / 93,150 / 287,297 (= V5/V6).
- 50-contract limit: not enforced inside riskeng; checked post hoc on the taken trades (upper bound over [entry, natural exit] ignoring lock exits): peak concurrent lots 28 for Set A, Set B, BEST5 and the neighbours (14 + 14); the limit cannot bind on the lock path. (Entry-side joins of the stop-join exit that put 56 on the books are an execution effect scored in T4, outside this sequence.)
- Costs: engine SLIP and commission constants multiplied in a copy of riskeng_pb (`out/BK1/bk1_riskeng_pb_m*.py`; the original untouched); Set A re-run at the same multiple on the same engine.
- Not a fresh L2 replay with the 10/14-lot sizes: fills per signal are the corrected-P9 points (queue effect of 10 vs 14 lots on the S14x1 / stop-join fills is not re-modelled; the size-impact credit is the `sizecost` switch, scored as a separate cell).

## Windows (mean / SD / maxDD (daily path) / worst week / trades per week, $, report scale 14/14)

| cell | WF (142 wk) | WF-PRE (75) | HOLD (68) | L8W | IS (52) |
|---|---|---|---|---|---|
| Set A (live) | 24,978 / 104,547 / 401,641 / -137,081 / 35.9 | 17,547 / 97,554 / 401,641 / -136,701 / 32.1 | 32,807 / 110,567 / 267,133 / -137,081 / 39.6 | 34,209 / 109,428 / 267,133 / -98,918 / 40.8 | 13,654 / 95,929 / 407,461 / -136,335 / 26.8 |
| Set B (cap off, wk floor 12R, 14/10/10) | 33,109 / 106,710 / 320,103 / -189,464 / 45.2 | 27,539 / 96,791 / 320,103 / -152,362 / 41.7 | 38,765 / 115,986 / 256,350 / -189,464 / 48.4 | 57,013 / 124,787 / 209,146 / -95,438 / 49.6 | 10,256 / 83,572 / 376,083 / -201,371 / 32.7 |
| BEST5 (Set B + give-back keep 67% after >=2 trades) | 25,536 / 93,150 / 287,297 / -184,816 / 41.2 | 18,265 / 89,944 / 287,128 / -154,608 / 38.3 | 33,180 / 95,546 / 287,297 / -184,816 / 43.8 | 56,141 / 106,066 / 182,556 / -82,257 / 42.6 | 13,183 / 83,325 / 304,880 / -131,153 / 31.2 |

## Set B vs Set A: effect, interval, detectable effect

| window | d mean $/wk | d SD | d maxDD | d worst week |
|---|---|---|---|---|
| WF | +8,131 | +2,163 | -81,538 | -52,384 |
| WFPRE | +9,992 | -763 | -81,538 | -15,660 |
| HOLD | +5,959 | +5,420 | -10,783 | -52,384 |
| L8W | +22,803 | +15,359 | -57,987 | +3,480 |
| IS | -3,398 | -12,357 | -31,378 | -65,036 |

- 10,000-draw bootstrap of the WF weekly mean difference: **8-week circular block CI [-84, 16,100]** (the NM-B convention, verdict of record), **iid-week CI [1,032, 15,588]** (the s48score `boot_ci` convention). P(bootstrap mean difference > 0) = 0.973 (block). Holdout-only block CI [-945, 13,194], iid [-3,340, 15,515] (68 weeks).
- SD difference CI (block, 10k) [-4,841, 8,599]; weekly-path maxDD difference CI [-291,698, 89,882] (includes 0).
- **Detectable effect (80% power, 2.80 x block SE, WF): mean $11,536/wk, SD $9,665, weekly-path maxDD $262,547.** The predicted +$8.1k/wk is below the detectable mean effect; the observed maxDD gain (-$81.5k) is far below the detectable maxDD effect: the test could neither confirm nor reject Set B, and could not have seen a mean effect smaller than $11.5k/wk or a maxDD effect smaller than $263k.

## Verdict under V2 sec 3 (sizing / lock rule), s48score.verdict of record

- Criterion: weekly mean not down and (SD or maxDD down with CI) OR mean up and maxDD not worse (scorer reads 'mean up' as mean up with CI > 0, open question 3 in LEADERBOARD.md). Branch a: mean up, but SD +2,163 (up) and the maxDD difference CI includes 0 -> not met. Branch b: mean +8,131, maxDD -81,538 (not worse), mean CI lower bound -84 (block) -> **not met by $84/wk at the block CI; met under the iid-week CI (lower bound 1,032)**; the lower bound is a coin flip across Monte Carlo seeds (-84 / -147 / +117 at three 10k seeds).
- Other conditions: holdout d mean +5,959 (agrees); placebo inherited 1.00 (V5 lock-timing maxDD rank 1.00, mean rank 0.42; size placebo 0.98/1.00; no Set-B-specific placebo exists and none was run); neighbours (week floor 8R +3,420, 16R +8,131 (identical to 12R: the floor does not bind above 12R), lots 14/12/12 +10,366, 14/8/8 +3,656) all positive; exact 2x cost: d mean +3,459 (positive); largest year share 48% (2024-02..12) -> OK.
- **Set B = CANDIDATE (block CI of record, as in NM-B); it would be PASS under the iid-week CI (PASS).** The tier depends on the resampling scheme (weekly difference lag-1 autocorrelation 0.09), not on the draw count; flagged for the user as a structural question (MORNING).
- BEST5 = **DEAD**: d mean +558 (CI block [-7,993, 8,541], MDE 11,875), SD -11,397 with CI [-17,804, -4,479] (excludes 0: the only significant effect in the family), maxDD -114,344; fails: holdout maxDD +20,164 (worse than A), 2x/1.5x cost mean -2,024 / -3,654, year share 316%, neighbours disagree (NM-B). BEST5 is worse than Set B by -7,573/wk (CI block [-14,900, -490] excludes 0): the keep-67%-after-2-trades give-back costs income and is the part of the family that reduces SD and maxDD.
- Sensitivity cell BK1_SETB_sizecredit (size-impact refund for 10-lot sessions, `sizecost`): d mean +9,161, block CI [929, 17,168], maxDD -84,544 -> scorer gives **PASS**; this rests on an unverified impact-refund model (nothing live shows 10-lot fills cost less per contract); not registered, not a basis for a decision. BK1_SETB_nocredit = BK1_SETB (14/10/10 has no excess above 14).

## Cost stress (exact re-runs, Set A re-run at the same multiple)

| cost | Set A WF mean | Set B WF mean | d mean | block CI 10k | d maxDD | HOLD d mean | HOLD d maxDD |
|---|---|---|---|---|---|---|---|
| 1x | 24,978 | 33,109 | +8,131 | [-84, 16,100] | -81,538 | +5,959 | -10,783 |
| 1.5x | 25,491 | 28,072 | +2,580 | [-4,617, 9,203] | -61,603 | +5,954 | -13,728 |
| 2x | 19,235 | 22,694 | +3,459 | [-4,268, 11,061] | -87,575 | +6,953 | -83,505 |

Reading: Set B keeps a positive but smaller and non-significant mean edge at 1.5x (+2.6k) and 2x (+3.5k) and its maxDD is lower at every multiple (-62k .. -88k); it takes about 9 more trades per week than Set A (45.2 vs 35.9). Set A itself is non-monotone in cost (24,978 at 1x, 25,491 at 1.5x, 19,235 at 2x): the locks re-time when costs shift the intraday P&L path, so a single cost multiple moves either arm by +-$0.5-6k/wk through lock path dependence alone - an uncertainty of the same size as the Set B edge, which is why no cost cell here can confirm or reject it.

## By year (weekly mean $, WF years; IS = 2023-02..2024-01)

| period | weeks | Set A | Set B | d mean | d total $ | d maxDD (own path) |
|---|---|---|---|---|---|---|
| IS 2023-02..2024-01 | 52 | 13,654 | 10,256 | -3,398 | -176,695 | -31,378 |
| 2024-02..12 | 49 | 14,648 | 25,852 | +11,205 | +549,022 | -81,538 |
| 2025 | 53 | 21,152 | 28,960 | +7,808 | +413,838 | -3,125 |
| 2026 | 42 | 40,669 | 45,234 | +4,565 | +191,719 | -20,521 |

Set B is positive in all three WF calendar periods (2024-02..12 +11,205, 2025 +7,808, 2026 +4,565) and negative in IS (-3,398/wk over 52 weeks); the gain per week falls year by year (11.2k -> 7.8k -> 4.6k).

## By session (net $/wk and trades/wk, rows by entry session; Asia 18:00-02:00, London 02:00-09:30, NY 09:30-18:00 ET)

| window | session | Set A $/wk (trades) | Set B $/wk (trades) | d $/wk | BEST5 $/wk |
|---|---|---|---|---|---|
| WF | Asia | 18,232 (17.3) | 18,813 (18.3) | +581 | 18,189 |
| WF | London | 2,501 (10.3) | 6,941 (12.7) | +4,439 | 2,532 |
| WF | NY | 4,245 (8.4) | 7,356 (14.2) | +3,111 | 4,815 |
| WFPRE | Asia | 11,618 (14.0) | 13,310 (15.0) | +1,692 | 14,038 |
| WFPRE | London | -74 (9.6) | 3,369 (12.1) | +3,443 | -3,188 |
| WFPRE | NY | 6,003 (8.4) | 10,860 (14.6) | +4,858 | 7,415 |
| HOLD | Asia | 25,259 (20.6) | 24,605 (21.7) | -654 | 22,501 |
| HOLD | London | 5,304 (10.8) | 10,778 (13.2) | +5,473 | 8,803 |
| HOLD | NY | 2,243 (8.2) | 3,382 (13.5) | +1,139 | 1,876 |

Where the edge comes from (WF): London +4.4k/wk and NY +3.1k/wk (the sessions that run at 10 lots and lose the combined cap/floor interference), Asia +0.6k/wk (unchanged size). Set B takes more trades in every session because the removed cap/floor stop halting the day. In the holdout the London gain is +5.5k/wk, NY +1.1k/wk and Asia -0.7k/wk. (Net by entry session; lock scale-downs are attributed to the entry row.)

## Where the Set B maxDD gain sits (pre-holdout vs holdout)

| path | Set A maxDD | trough (peak -> trough) | Set B maxDD | trough | difference |
|---|---|---|---|---|---|
| WF continuous (142 wk) | 401,641 | 20240222 -> 20240513 | 320,103 | 20240807 -> 20240827 | -81,538 |
| WF-PRE own path (2024-02..2025-06) | 401,641 | same | 320,103 | same | -81,538 |
| HOLD own path (2025-07+) | 267,133 | 20260826 -> 20260909 | 256,350 | 20250708 -> 20250728 | -10,783 |

- **All of the -$81.5k WF maxDD gain is pre-holdout**: Set A's 401,641 drawdown is the 2024-02-22 -> 2024-05-13 episode, Set B's WF maxDD (320,103) is the 2024-08-07 -> 2024-08-27 episode; both troughs are inside WF-PRE, and the continuous-path drawdown restricted to troughs in the holdout is 267,133 (A) vs 256,350 (B), i.e. the holdout contributes no WF-level maxDD at all. Set B's own-path holdout maxDD is -10,783 vs Set A (slightly lower, not worse): **Set B alone does not worsen the holdout maxDD.** The combined-system holdout maxDD that was $22k worse than Set A therefore comes from the sleeve layer (ORB/dip-buy/GSHORT at the tested budget), not from the Set B base.
- Cumulative gain vs Set A: +749,401 by 2025-06-30 (75 weeks, 9,992/wk), +405,178 in the holdout (68 weeks, 5,959/wk): the mean gain is smaller in the holdout (6.0k vs 10.0k/wk) and the L8W gain is larger (+22.8k/wk over 8 weeks).
- Worst week: Set B -189,464 (week 202528) vs Set A -137,081 (202550): the removed week floor is the cost (-52k). L8W: Set B 57,013/wk (maxDD 209,146) vs Set A 34,209/wk (267,133).

## Forward evidence available

- W43 (2026-10-19..23, informational): live Set A realised -184,580 (39 trades, FORWARD_REGISTER) / -189,750 (49 csv rows incl. WT); **Set B cannot be replayed**: the 1-s tape ends 2026-10-16 20:59 UTC (FWD_AB_SETS: A/B PENDING). The last pre-forward week W42 (dry run, P9 points): A 125,895, B 104,688 (B-A -21,207) - one week of Set A beating Set B, within weekly noise (SD 105k). Official forward weeks W44-W47: 0 complete. 4 weeks cannot decide anything (weekly SD 105k vs the edge 8k).
- Note for the forward comparison: the live CSV omits one ST trade (10-21 04:00, -$17.7k at 14 lots; see JOIN_RECON.md), so the live W43 net is understated by that amount.

## Detectable effect next to every null / caveat

- Every Set A vs Set B/BEST5 mean comparison here: MDE $11,536-12,978/wk (block bootstrap, 142 weeks); SD $9,665; weekly-path maxDD $262,547-319,354. A null at the weekly level means 'could not have seen less than that'.
- The engine reproduces earlier numbers to the dollar (that is the point of the run) but is the same engine; this is a re-score with 10k draws, costs and splits, not independent data. Selection multiplicity: Set B came from a 23,040-cell screen (DSR 0.975 at n=3,601 in PBDAY; 0.66 for BEST5).
- Files: `l2vast/struct48/out/BK1/BK1_final.json`, `BK1_pre.json`, `series_m{1,1.5,2}.npz`; code `l2vast/struct48/code/bk1_engine.py`, `bk1_score.py`; logs `l2vast/struct48/logs/bk1_*.log`.
