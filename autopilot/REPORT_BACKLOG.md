# REPORT BACKLOG (BK, robustness backlog, RESEARCH V2 sec 7; 2026-10-24)

Research only: no execution-server / chart / live change, no credentials or account numbers printed, no downloads, UNTOUCHED never read, nothing deleted. Prereg BK1 (12 cells, sha256 `f032026569bc750ebafbf94e671ef637ced6ed9375c6915a3a60b2d96cdc10fb`) frozen in DECISIONS.md before scoring; holdout looks logged (`ledger/holdout_looks.jsonl`, track BK1, disclosed as RE-READS); ledger appended (cumulative 28,523 trials, +12). Jobs 2 and 3 re-draw/re-read existing cells and add no trial. Idle cores ran this instead of new hypotheses.

## One-paragraph result
(1) Set B on the exact 1-s sequence engine reproduces the candidate to the dollar (+8,131/wk, maxDD -81.5k) and stays a **CANDIDATE**: 10,000-draw 8-week block CI [-84, 16,100] (iid-week CI [1,032, 15,588] would clear zero: the tier depends on the resampling scheme), exact 1.5x/2x cost keeps the sign (+2.6k / +3.5k, not significant), the whole maxDD gain is pre-holdout and Set B alone does **not** worsen the holdout maxDD (-10.8k). BEST5 is DEAD. (2) The live join shortfall is a fill-rate composition effect (overnight stop exits), not a different exit quality; latency is not the cause; one live CSV trade is missing and the CSV clock is ET (JOIN_RECON.md). (3) At 10,000 draws all 44 PASS/CANDIDATE rows keep their verdicts (18 PASS, 26 CANDIDATE); two families sit on a CI endpoint at zero that no draw count resolves.

## Job 1 - Set B / BEST5 on the exact 1-s engine, full sequence (details: autopilot/REPORT_BK1_SETB.md)

Engine = riskeng_pb (second-by-second locks, give-back, week floor, session lots; peak concurrent lots 28 < 50-contract limit), corrected-P9 points, Set A re-run on the same engine at every cost multiple. 10,000-draw bootstrap, iid weeks and 8-week blocks. Detectable effect (80% power, WF, block SE x 2.80) is next to every result.

| tier | cell | object | d mean $/wk (block CI 10k) | d SD | d maxDD | holdout d mean / d maxDD | detectable effect (mean / SD / maxDD) | what fails |
|---|---|---|---|---|---|---|---|---|
| CANDIDATE | BK1_SETB (Set B: cap off, floor 12R, 14/10/10) | sizing-lock-session | +8,131 [-84, 16,100] | +2,163 | -81,538 | +5,959 / -10,783 | 11,536 / 9,665 / 262,547 | mean CI (block) includes 0 by $84/wk (iid CI excludes 0 -> PASS); SD and maxDD differences not significant; predicted +8.1k < detectable 11.5k |
| PASS (by the letter, watch-only) | BK1_SETB_sizecredit (same + size-impact refund for 10-lot sessions) | sizing-lock-session | +9,161 [929, 17,168] | +2,288 | -84,544 | +6,935 / -12,287 | 11,577 / 9,687 / 262,296 | rests on an unverified impact-refund model; treated as B01 for decisions; record `paper_all/BK1_SETB_sizecredit.json` (watch only) |
| CANDIDATE | BK1_SETB_nocredit (= BK1_SETB; 14/10/10 has no excess above 14) | sizing-lock-session | +8,131 [-84, 16,100] | +2,163 | -81,538 | +5,959 / -10,783 | 11,536 / 9,665 / 262,547 | as BK1_SETB |
| DEAD | BK1_BEST5 (Set B + give-back keep 67% after >=2 trades) | sizing-lock-session | +558 [-7,993, 8,541] | -11,397 | -114,344 | +373 / +20,164 | 11,875 / 9,541 / 245,489 | mean +558 with MDE 11.9k (null); SD -11.4k is significant [-17.8k, -4.5k] but holdout maxDD +20k, cost 1.5x/2x mean -3.7k/-2.0k, year share 316%, neighbours disagree |
| DEAD (stress cell of Set B) | BK1_SETB_1.5x | sizing-lock-session | +2,580 [-4,617, 9,203] | +3,226 | -61,603 | +5,954 / -13,728 | 9,873 / 9,990 / 229,072 | sign positive (+2.6k) but CI [-4.6k, 9.2k] includes 0; scorer DEAD (no neighbours at that cost, CI): informational, the tier of record is Set B CANDIDATE |
| DEAD (stress cell of Set B) | BK1_SETB_2x | sizing-lock-session | +3,459 [-4,268, 11,061] | +2,276 | -87,575 | +6,953 / -83,505 | 11,005 / 11,526 / 319,354 | sign positive (+3.5k) but CI [-4.3k, 11.1k] includes 0; informational |
| DEAD (stress cell) | BK1_BEST5_1.5x | sizing-lock-session | -3,654 [-12,048, 4,357] | -8,726 | -73,105 | +2,968 / +26,538 | 11,663 / 9,258 / 228,582 | mean negative (-3.7k) |
| DEAD (stress cell) | BK1_BEST5_2x | sizing-lock-session | -2,024 [-11,280, 6,986] | -9,905 | -67,859 | +4,769 / -34,177 | 12,978 / 9,923 / 332,840 | mean negative (-2.0k) |

Neighbours (inputs, not tiered): floor 8R +3,420, floor 16R +8,131 (= 12R), lots 14/12/12 +10,366 (block CI [3,129, 17,612]), lots 14/8/8 +3,656. BEST5 - Set B = -7,573/wk (block CI [-14,900, -490]).

Requested sub-results:
- **Sizing/lock judgement (V2 sec 3):** mean up, maxDD not worse, SD not down with CI (+2,163) -> only the 'mean up with maxDD not worse' branch can carry it, and it needs the mean CI to exclude 0 (open question 3 in LEADERBOARD.md): it does under iid weeks, not under 8-week blocks (lower bound -84 / -147 / +117 over three 10k seeds). Verdict of record stays CANDIDATE.
- **By year:** 2024-02..12 +11.2k, 2025 +7.8k, 2026 +4.6k per week (all positive, decaying); IS (2023-02..2024-01) -3.4k/wk. **By session (WF):** London +4.4k/wk, NY +3.1k, Asia +0.6k; holdout London +5.5k, NY +1.1k, Asia -0.7k.
- **Worst week / L8W:** worst week -189,464 vs -137,081 (week floor removed: -52k); L8W 57,013 vs 34,209 per week, maxDD 209,146 vs 267,133.
- **Pre-holdout vs holdout maxDD:** the -81.5k WF gain is entirely in 2024 (Set A trough 2024-02-22 -> 05-13 = 401,641; Set B 2024-08-07 -> 08-27 = 320,103). Holdout own path: A 267,133 vs B 256,350 (-10,783). Set B alone is not worse in the holdout; the combined-system holdout maxDD that was +$22k worse comes from the sleeve layer.
- **Forward evidence:** W43 informational only: live Set A -184,580 (39 trades) / -189,750 (all csv rows); Set B not replayable (tape ends 10-16); dry-run W42 B-A -21,207; 0 official weeks complete. 4 weeks cannot decide anything (weekly SD 105k vs an 8k edge). The live CSV is missing one ST trade (10-21 04:00, about -$17.7k), so the live net is understated.

## Job 2 - live-vs-replay join reconciliation (details: autopilot/JOIN_RECON.md; calibration, no tier)

- Per-attempt table for the 18 CSV stop exits (17 attempts + 1 broker-rejected) plus the bypassed 19th; 11 have an NT8 order-level trace (10-21..23), 7 (10-20) are CSV-only; replay = struct48 T4 stop-join machinery on the only L2 on disk next to the live days, W42 (10-12..16, 55 stop exits, XJ3 queue / trade-through). Live days 10-20..23 have no L2: not replayed, nothing fabricated.
- Gap decomposition: outcome-conditional exit quality is the same live vs replay (filled +0.52 vs +0.52; failed -> market -4.25 vs -4.26); so the -2.01 vs -0.52 slip gap is the fill rate. Fill rate: live 0.47 [0.23, 0.72]; replay 0.78 headline, 0.62-0.64 in the matched week, 0.65-0.69 reweighted to the live time-of-day mix (14 of 17 attempts were 18:00-08:00 ET, where the replay fills 0.57-0.68 vs 0.83 in RTH); P(<=8/17) = 0.05-0.09 (mix), 0.15 (W42). Not significant at 5% on the trade-through rule; live 3/9 in 18-22 ET vs 0.64-0.68 is the only residual (post hoc, P 0.04-0.06).
- Mechanism of failures: price runs away (5/5 traced non-fills ended 2.8-10.0 pts beyond the limit; replay 14 of 17-21 failures have zero tape at/through the limit in 3 s). Latency is contradicted (replay fill rate rises 0.64 -> 0.76-0.80 with 100-500 ms). No wrong-side or mispriced join. One position-limit rejection (10-20 23:55). One bypass (10-21 04:34: CancelAllOrders + Position.Close 31 ms after the join was created).
- Findings for the owners of LIVE_RECON.md / FORWARD_REGISTER.md / live_vs_replay_p9.py: CSV and trace clocks are Eastern, not Central (they add +1 h); the live CSV omits the 10-21 04:00 ST trade; the join-rate denominator with the bypass is 8/18 = 0.44.
- Detectable effect for the nulls here: a live-vs-replay fill-rate comparison at n=17 has binomial SD 0.12 and cannot see a gap smaller than about 0.3 at 80% power; the slip comparison (live -2.01, CI [-3.65, -0.37] on n=18) cannot exclude the replay-at-live-mix expectation (-0.96).
- Minimum data to settle it: NQ mbp-10 for 2026-10-20..10-23 (blocked on the user: Databento key not in env / Saturday extension), the 10-20 NT8 trace, the strategy ExecLogCsv (bid/ask at join), and about 90 attempts (about 5 weeks) for a +-0.10 fill-rate interval.

## Job 3 - 10,000-draw bootstraps for every CANDIDATE / PASS row (details: autopilot/BACKLOG_BOOTSTRAP.md)

44 rows re-drawn (18 PASS, 26 CANDIDATE of the verdict of record); the original 1,000-draw (T3 / NM-E, iid weeks) and 2,000-draw (NM-B, 8-week blocks) intervals were reproduced exactly before re-drawing; **0 verdict changes, 0 CI-excludes-zero flips** (22 / 22). Sleeve verdicts do not depend on the CI (criterion = standalone holdout, marginal Sharpe, corr); the 10 NM-B sizing cells do and keep CANDIDATE. Boundary cases at zero: B01_SetB lower bound -84/-147/+117 (three seeds) and ORB_ASIA_30_v1__s60 (-39/+20/+106 at the 0.25 size): 10,000 draws do not move them, only the resampling scheme (blocks vs iid) does. Detectable effects per row are in the table (MDE $3.1k/wk for RSI2CC at its size to $23.3k/wk for ORB_ASIA_30_s60@1.0; Set B family $11.1-15.6k).

## All three tiers (this backlog)

- **PASS (18 rows, unchanged):** ORB Asia 15 s60/s75 (6 sized rows), RSI2_t10, ES_RSI2_t10, RSI2C_s20, RSI2CC_s20, E:NQ_RSI2/RSI2C/RSI2CC/ES_RSI2, E:ORB_ASIA_15 s60/s75, GSHORT_t90 (T3.8B and E:), plus BK1_SETB_sizecredit by the letter (watch-only, not independent). Independent exposures are unchanged: GSHORT, ORB Asia, the dip-buy RSI2 family. GSHORT's CI includes zero in both versions (sleeve criterion needs no CI).
- **CANDIDATE (26 rows + BK1_SETB, unchanged):** the 10 Set B / PBDAY cells (one edge), ORB Asia 30 (s50/s60/s75, 9 sized rows), IBS_t20_n1 (T3.7b4, E:), RSI2T_t10 (T3.6b1, E:), YM_RSI2_t10, COMB_c3_R (T3.8A, E:).
- **DEAD:** BK1_BEST5 and the BEST5 / Set B stress cells above; nothing else was re-run (630 DEAD cells untouched, no reopen).

## Questions for the user (structural, in MORNING terms; the queue was not paused)

1. Set B resampling: 8-week block bootstrap (CI lower bound -$84/wk, CANDIDATE) or iid weeks as every sleeve row is scored (+$1,032, PASS)? The weekly difference has lag-1 autocorrelation 0.09, so the choice moves the tier by $1k of CI. The directive text says "week-block bootstrap".
2. Should a variant that differs only by a modelling assumption (size-impact refund) be registered as a separate PAPER-ALL PASS? Registered watch-only here, not a decision input.
3. Databento extension for 2026-10-20..23 (about 3 GB) would let BK2 replay each live join at its true millisecond trigger; otherwise the live-vs-replay question cannot be closed with the data on disk.

Files: autopilot/REPORT_BK1_SETB.md, autopilot/JOIN_RECON.md, autopilot/BACKLOG_BOOTSTRAP.md, autopilot/REPORT_BK1_PREHOLD.md, autopilot/join_recon/ (scripts + join_attempts.csv), l2vast/struct48/{prereg/BK1.md, code/bk1_*.py, code/bk3_boot.py, out/BK1/, out/BK2/, out/BK3_bootstrap.json, paper_all/BK1_SETB_sizecredit.json}.
