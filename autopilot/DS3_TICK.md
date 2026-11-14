# DS3_TICK: NYSE TICK as day-type, filter and trigger tool (W-TK1 sections 1-6; W-TK2 section 7)

Verdict (2026-11-14 02:21Z): PART 1 (forecast): 0 of 502 feature-family x target x session cells pass the lead rule; TICK does not forecast NQ direction, continuation, trend/chop or remaining range beyond the price-only benchmark in any slice (best gains are about 1% of variance and inside the family null). PART 2 first order: 6768 cells, 194 pass the recent gate, 9 pass recent+older; best recent+older drawdown score 14.6 vs family-null q95 37.6 (best-of-family on TICK shifted 8-60 days), so no first-order cell is separable from the best-of-family noise; exact-engine confirmation: see section 5.

Plain strength rule: a result is a LEAD only if it holds in the recent (L6M and HOLD) AND older (PRE and X') windows and beats the family null; no PASS claims; nothing here changes the execution server or any live chart. Page rebuilt every 3 h by tk_loop.sh.

## 1. Data check

- File <home>/... 14,148,456 bytes, 409,099 records; line breaks: carriage return only (CR=409,099, LF=0, CRLF=0), parsed on [\r\n]+; unparsable 0, duplicate timestamps 0, volume always 0 (nonzero 0).
- Range 2023-04-01 16:06:00 .. 2026-11-13 22:01:00 UTC (timestamps are bar END).
- Glitch bars (|value| > 2000): [['2024-01-20 18:58:00', 442417.0, 442417.0, 442417.0, 442417.0]] dropped; after that the largest print is 1594 / -1599.
- Stray prints dropped: 243 weekend prints (e.g. [['2023-04-01 16:06:00', 921.0], ['2023-04-22 20:55:00', -170.0], ['2023-04-30 02:25:00', 24.0]]), 54,866 bars outside 09:31-16:00 ET (of which 16:01-17:00 ET post-close bars, 61 per day x 908 days, plus a few stray overnight prints). The ~451 bars/day in the file = 390 RTH bars (09:31..16:00) + 61 post-close bars (16:01..17:00, stale/frozen values) which are not used.
- Bars per RTH day: median 390, 900 of 911 days have exactly 390; exceptions {'20230904': [1, 697, 697], '20240329': [1, 771, 771], '20251225': [1, 957, 957], '20260611': [378, 571, 960]} (3 one-bar stub days on holidays, 2026-06-11 has 378 bars with a 13-minute hole); intra-day gaps > 5 min on days {'20240719': 11, '20240802': 9, '20260611': 13}.
- DST: first RTH bar ends 13:31Z on 645 days (summer, UTC-4) and 14:31Z on 263 days (winter, UTC-5): every day starts at 09:31 ET, matching NQ (first NQ RTH bar starts 09:30 ET). UTC offsets seen: {'-4.0': [811, 1011, 647], '-5.0': [871, 1257, 264]}.
- Missing days vs NQ RTH calendar: ['20260223'] (NQ trades, no TICK); TICK-only days (holidays/half days where NQ had < 300 RTH bars): ['20230703', '20230904', '20231124', '20240329', '20240703', '20241129', '20241224', '20250703', '20251128', '20251224', '20251225', '20261113'].
- Bar usable at end time + 5 s everywhere. Clean series: 354,080 bars, 911 session days. Features: /mnt/l2/l2vast/_tick/tick_feat.parquet (72 columns; README.md there).

## 2. PART 1: does TICK forecast? (no trading)

Setup (prereg autopilot/TICK_P1_PREREG.md, addendum A): decision every 5 min 09:35-15:55 ET, slices S1 09:30-10:00, S2 10:00-12:00, S3 12:00-14:30, S4 14:30-16:00, and single readings after the first 15/30/60 min (R15/R30/R60). Targets: (a) rest-of-session efficiency ratio, close location, mean crossings; (b) rest-of-session ln range; (c) NQ return next 5/15/30/60 min; (d) continuation = sign(past move) x next move at 15/30/60. Benchmark = price-only ridge (NQ past returns 5/15/30/60, range so far, ER and ATR 15/30/60, 14-day range, time of day, event calendar flags, VIX level/change/term; the calendar and VIX exist only from 2024-09/10, so before that they are imputed and flagged, a handicap for the benchmark in PRE/X' that favours TICK). Gain = (benchmark SSE - benchmark+TICK SSE) / mean-only SSE, out of sample: walk-forward refit every 10 trading days (bi-weekly), expanding, 60-day warm-up; PRE and X' additionally by blocked chunk cross-validation (cv_*). Nulls: TICK shifted by k trading days (k=11/23/37 + 40 random draws 8-60, time of day kept); null q95 per cell and family q95 (max over all families x targets of the slice). abs = gain over the plain mean (absolute R2 of benchmark+TICK).

Cells scored: 502 (R15 divergence cells dropped: the divergence flags need 30 min of session, so they are constant at the 15-minute reading). Leads (WF gain > family q95, L6M>0, HOLD>0, cv PRE>0, cv X'>0): **0**.

### 2a. Best feature family per target class and session slice (best of WF gain + cv gain; gain over the price-only benchmark, fraction of variance)

| cls | sl | group | gain_full | gain_L3M | gain_L6M | gain_HOLD | cv_PRE | cv_XP | abs_full | null_q95 | fam_q95 | ci_lo |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| cont | R15 | first | -0.0017 | -0.0149 | -0.0027 | 0.0004 | -0.0058 | 0.0052 | -0.0508 | 0.0005 | 0.0056 | -0.0061 |
| cont | R30 | level | -0.0006 | -0.0290 | 0.0027 | 0.0113 | 0.0023 | -0.0084 | -0.0186 | -0.0041 | 0.0092 | -0.0086 |
| cont | R60 | first | 0.0091 | -0.0272 | -0.0110 | 0.0107 | 0.0227 | -0.0120 | 0.0077 | -0.0008 | 0.0087 | 0.0006 |
| cont | S1 | div | -0.0011 | 0.0003 | -0.0006 | -0.0003 | -0.0005 | -0.0012 | -0.0218 | 0.0003 | 0.0018 | -0.0022 |
| cont | S2 | cum | 0.0035 | -0.0083 | -0.0029 | 0.0006 | 0.0071 | -0.0027 | -0.0063 | -0.0012 | 0.0030 | 0.0008 |
| cont | S3 | level | 0.0011 | -0.0260 | -0.0074 | -0.0084 | 0.0039 | -0.0020 | -0.0257 | -0.0011 | 0.0021 | -0.0063 |
| cont | S4 | ext | 0.0004 | 0.0437 | 0.0395 | 0.0404 | 0.0528 | -0.1333 | -0.1025 | -0.0073 | 0.0009 | -0.0248 |
| fwd | R15 | level | 0.0060 | -0.0142 | -0.0062 | 0.0153 | 0.0021 | 0.0008 | -0.0151 | 0.0000 | 0.0056 | -0.0047 |
| fwd | R30 | level | 0.0019 | -0.0200 | 0.0137 | 0.0164 | -0.0031 | -0.0074 | -0.0232 | -0.0030 | 0.0092 | -0.0076 |
| fwd | R60 | first | 0.0117 | -0.0459 | -0.0140 | 0.0096 | 0.0283 | 0.0054 | -0.0191 | -0.0003 | 0.0087 | 0.0017 |
| fwd | S1 | level | -0.0009 | -0.0246 | -0.0036 | 0.0066 | 0.0094 | -0.0149 | -0.0914 | -0.0044 | 0.0018 | -0.0069 |
| fwd | S2 | ext | 0.0052 | -0.0095 | -0.0037 | 0.0043 | 0.0132 | -0.0112 | -0.0608 | -0.0049 | 0.0030 | -0.0073 |
| fwd | S3 | cum | -0.0006 | -0.0010 | -0.0009 | -0.0006 | -0.0002 | -0.0008 | -0.0059 | -0.0005 | 0.0021 | -0.0010 |
| fwd | S4 | div | -0.0003 | -0.0038 | 0.0061 | 0.0022 | 0.0015 | 0.0109 | -0.0979 | 0.0005 | 0.0009 | -0.0084 |
| rest_cext | R15 | cum | -0.0017 | -0.0001 | 0.0045 | -0.0037 | 0.0003 | -0.0016 | -0.0102 | 0.0008 | 0.0056 | -0.0056 |
| rest_cext | R30 | div | -0.0031 | 0.0002 | -0.0001 | -0.0014 | -0.0012 | -0.0072 | -0.0152 | 0.0009 | 0.0092 | -0.0053 |
| rest_cext | R60 | div | -0.0033 | 0.0049 | 0.0023 | 0.0005 | -0.0017 | -0.0076 | -0.0097 | 0.0023 | 0.0087 | -0.0082 |
| rest_cext | S1 | div | -0.0013 | -0.0003 | -0.0001 | -0.0003 | -0.0003 | -0.0014 | -0.0855 | -0.0004 | 0.0018 | -0.0025 |
| rest_cext | S2 | div | -0.0006 | 0.0003 | 0.0006 | 0.0003 | -0.0008 | -0.0020 | -0.1158 | -0.0001 | 0.0030 | -0.0020 |
| rest_cext | S3 | div | -0.0012 | 0.0001 | -0.0005 | 0.0001 | -0.0019 | 0.0001 | -0.0784 | 0.0002 | 0.0021 | -0.0031 |
| rest_cext | S4 | div | -0.0029 | -0.0004 | -0.0008 | -0.0000 | -0.0037 | -0.0000 | -0.0889 | -0.0010 | 0.0009 | -0.0059 |
| rest_cross | R15 | share | -0.0022 | -0.0029 | -0.0026 | -0.0019 | 0.0066 | -0.0114 | -0.0211 | 0.0030 | 0.0056 | -0.0083 |
| rest_cross | R30 | first | -0.0027 | 0.0010 | 0.0096 | 0.0038 | -0.0048 | -0.0000 | -0.0138 | 0.0090 | 0.0092 | -0.0087 |
| rest_cross | R60 | cum | -0.0018 | 0.0109 | 0.0026 | -0.0001 | 0.0076 | -0.0295 | -0.0242 | 0.0001 | 0.0087 | -0.0082 |
| rest_cross | S1 | div | -0.0014 | -0.0000 | -0.0001 | -0.0000 | -0.0006 | -0.0010 | -0.0414 | -0.0001 | 0.0018 | -0.0030 |
| rest_cross | S2 | div | -0.0009 | -0.0005 | -0.0003 | -0.0004 | -0.0005 | -0.0011 | -0.0173 | -0.0000 | 0.0030 | -0.0017 |
| rest_cross | S3 | div | -0.0009 | 0.0002 | -0.0001 | -0.0001 | -0.0007 | -0.0001 | -0.0219 | 0.0000 | 0.0021 | -0.0014 |
| rest_cross | S4 | div | -0.0001 | 0.0008 | 0.0002 | -0.0000 | -0.0001 | -0.0001 | 0.0362 | -0.0008 | 0.0009 | -0.0013 |
| rest_er | R15 | cum | -0.0038 | -0.0008 | -0.0011 | -0.0026 | -0.0018 | -0.0062 | -0.0198 | 0.0021 | 0.0056 | -0.0064 |
| rest_er | R30 | div | -0.0001 | -0.0033 | 0.0047 | 0.0027 | 0.0085 | -0.0070 | -0.0201 | 0.0012 | 0.0092 | -0.0045 |
| rest_er | R60 | div | -0.0018 | 0.0130 | 0.0121 | 0.0077 | -0.0064 | -0.0062 | -0.0232 | 0.0009 | 0.0087 | -0.0100 |
| rest_er | S1 | div | -0.0016 | -0.0011 | 0.0001 | -0.0001 | 0.0012 | -0.0010 | -0.0953 | -0.0003 | 0.0018 | -0.0046 |
| rest_er | S2 | div | -0.0017 | -0.0002 | -0.0001 | -0.0004 | -0.0009 | -0.0020 | -0.1556 | 0.0014 | 0.0030 | -0.0028 |
| rest_er | S3 | div | -0.0002 | 0.0008 | -0.0010 | -0.0001 | -0.0002 | 0.0012 | -0.1716 | 0.0011 | 0.0021 | -0.0023 |
| rest_er | S4 | div | -0.0016 | -0.0005 | -0.0003 | -0.0007 | -0.0013 | -0.0015 | 0.0727 | -0.0010 | 0.0009 | -0.0030 |
| rest_rng | R15 | cum | 0.0004 | 0.0176 | 0.0134 | 0.0108 | 0.0001 | -0.0153 | 0.3650 | 0.0001 | 0.0056 | -0.0019 |
| rest_rng | R30 | div | 0.0009 | 0.0004 | 0.0025 | 0.0082 | 0.0014 | -0.0208 | 0.3534 | 0.0003 | 0.0092 | -0.0033 |
| rest_rng | R60 | first | 0.0005 | 0.0123 | 0.0025 | 0.0008 | 0.0042 | -0.0683 | 0.2970 | 0.0009 | 0.0087 | -0.0052 |
| rest_rng | S1 | div | 0.0005 | -0.0017 | -0.0010 | 0.0011 | 0.0006 | -0.0039 | 0.3848 | -0.0001 | 0.0018 | -0.0007 |
| rest_rng | S2 | div | -0.0008 | 0.0006 | -0.0006 | -0.0001 | 0.0002 | -0.0165 | 0.2755 | 0.0004 | 0.0030 | -0.0015 |
| rest_rng | S3 | div | 0.0003 | 0.0010 | 0.0002 | 0.0001 | 0.0002 | -0.0001 | 0.3662 | 0.0000 | 0.0021 | -0.0001 |
| rest_rng | S4 | ext | 0.0086 | -0.0067 | 0.0057 | -0.0068 | 0.0044 | -0.0210 | 0.5481 | -0.0030 | 0.0009 | -0.0058 |

### 2b. Per TICK feature family: forecasts? (share of its cells that beat the shifted-time null q95, are positive in L6M+HOLD, are positive in PRE+X' by cv)

| group | cells | wf_gain_gt_null_q95 | recent_gain_pos | older_cv_pos | leads | best_wf_gain | median_wf_gain |
|---|---|---|---|---|---|---|---|
| ALL | 73 | 0.233 | 0.151 | 0.000 | 0 | 0.000 | -0.022 |
| cum | 73 | 0.274 | 0.192 | 0.014 | 0 | 0.010 | -0.003 |
| div | 64 | 0.188 | 0.250 | 0.031 | 0 | 0.006 | -0.001 |
| ext | 73 | 0.137 | 0.233 | 0.000 | 0 | 0.009 | -0.007 |
| first | 73 | 0.342 | 0.123 | 0.096 | 0 | 0.012 | -0.005 |
| level | 73 | 0.288 | 0.192 | 0.041 | 0 | 0.008 | -0.005 |
| share | 73 | 0.151 | 0.178 | 0.000 | 0 | 0.003 | -0.006 |

Plain statement per family:

- all families together: forecasts NO. Best cell S4 rest_rng: WF gain over benchmark 0.0000 (L6M -0.0138, HOLD -0.0187, cv PRE -0.0016, cv X' -0.0648) vs null q95 -0.0176, family q95 0.0009; median gain across its cells -0.0219.
- cumulative TICK since 09:30 and slopes: forecasts NO. Best cell R60 fwd30: WF gain over benchmark 0.0102 (L6M 0.0061, HOLD 0.0015, cv PRE 0.0198, cv X' -0.0041) vs null q95 0.0009, family q95 0.0087; median gain across its cells -0.0026.
- TICK-price divergence flags: forecasts NO. Best cell R60 cont60: WF gain over benchmark 0.0064 (L6M 0.0050, HOLD -0.0014, cv PRE 0.0213, cv X' -0.0045) vs null q95 0.0018, family q95 0.0087; median gain across its cells -0.0008.
- count/timing of +/-800,+/-1000 extremes, time since last opposite: forecasts NO. Best cell S4 rest_rng: WF gain over benchmark 0.0086 (L6M 0.0057, HOLD -0.0068, cv PRE 0.0044, cv X' -0.0210) vs null q95 -0.0030, family q95 0.0009; median gain across its cells -0.0071.
- first 15/30/60 min summaries: forecasts NO. Best cell R60 fwd60: WF gain over benchmark 0.0117 (L6M -0.0140, HOLD 0.0096, cv PRE 0.0283, cv X' 0.0054) vs null q95 -0.0003, family q95 0.0087; median gain across its cells -0.0049.
- last close/high/low and rolling mean/median 5/15/30/60: forecasts NO. Best cell R60 fwd30: WF gain over benchmark 0.0076 (L6M -0.0003, HOLD 0.0062, cv PRE 0.0198, cv X' -0.0160) vs null q95 -0.0017, family q95 0.0087; median gain across its cells -0.0047.
- share of last N min >0, >+600, <-600: forecasts NO. Best cell R60 fwd60: WF gain over benchmark 0.0035 (L6M -0.0015, HOLD 0.0103, cv PRE 0.0244, cv X' -0.0339) vs null q95 0.0009, family q95 0.0087; median gain across its cells -0.0055.

### 2c. Ten cells with the best worst-window gain (recent and older)

| sl | target | group | gain_full | gain_L6M | gain_HOLD | cv_PRE | cv_XP | null_q95 | fam_q95 | pl11_full | pl23_full | pl37_full |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S4 | fwd60 | div | -0.0003 | 0.0061 | 0.0022 | 0.0015 | 0.0109 | 0.0005 | 0.0009 | -0.0017 | -0.0052 | -0.0040 |
| S3 | rest_rng | div | 0.0003 | 0.0002 | 0.0001 | 0.0002 | -0.0001 | 0.0000 | 0.0021 | -0.0002 | -0.0015 | -0.0003 |
| S4 | rest_cross | div | -0.0001 | 0.0002 | -0.0000 | -0.0001 | -0.0001 | -0.0008 | 0.0009 | -0.0014 | -0.0008 | -0.0042 |
| S4 | cont60 | div | -0.0033 | -0.0001 | 0.0016 | 0.0002 | 0.0013 | 0.0004 | 0.0009 | -0.0004 | -0.0025 | -0.0047 |
| S2 | cont60 | div | 0.0000 | 0.0002 | 0.0003 | -0.0004 | 0.0001 | -0.0002 | 0.0030 | -0.0005 | -0.0010 | -0.0000 |
| S1 | fwd30 | div | -0.0008 | -0.0002 | 0.0000 | -0.0003 | -0.0005 | 0.0000 | 0.0018 | -0.0014 | -0.0007 | -0.0007 |
| S4 | rest_rng | div | -0.0004 | 0.0019 | -0.0005 | 0.0006 | -0.0002 | 0.0007 | 0.0009 | -0.0004 | 0.0008 | -0.0007 |
| S2 | cont30 | div | 0.0011 | 0.0010 | 0.0008 | 0.0021 | -0.0006 | -0.0004 | 0.0030 | -0.0009 | -0.0006 | -0.0007 |
| S3 | rest_cross | div | -0.0009 | -0.0001 | -0.0001 | -0.0007 | -0.0001 | 0.0000 | 0.0021 | -0.0002 | -0.0010 | -0.0009 |
| S2 | fwd60 | div | 0.0000 | 0.0000 | 0.0005 | -0.0007 | 0.0005 | -0.0004 | 0.0030 | -0.0011 | -0.0011 | -0.0013 |
| S3 | rest_cross | cum | -0.0010 | -0.0005 | -0.0008 | -0.0001 | 0.0005 | -0.0001 | 0.0021 | -0.0000 | -0.0006 | -0.0006 |
| S2 | cont15 | div | -0.0007 | 0.0003 | -0.0002 | 0.0002 | -0.0008 | -0.0001 | 0.0030 | -0.0007 | -0.0001 | -0.0002 |

Reading: gains are in fractions of the out-of-sample variance of the target (0.01 = 1%). A price-only benchmark that already has negative absolute R2 on short return targets means NQ direction is not forecastable from either source; the TICK gain over it that does appear is below the family null.

## 3. PART 2 first order: TICK dials on the JN05W2 exact trade table (43 months, all layers ON, 19,798 trades; RTH entries 6,047)

Cells = family x TICK state x action x book x session scope. Families: E entry (skip/half against a pinned TICK, press x1.5 with it), K hold at a state/flat cut when TICK supports the trade (gain = hold_pnl - pnl at the cut), R re-entry (block same-side re-entry after a same-book same-side loser in the session while TICK is against), T trend day (first 30/60 min trend; counter-trend entries skipped/halved, with-trend pressed or held through cuts), C carry (the RTH summary of the previous day as a prior for the Asia/London books). First order = delta pnl on the matched trades; the stop/cut-earlier, take-earlier, lock-later, widen-targets and relax-cap dials need the path and are exact-engine only (section 5). Gates: recent = L6M and HOLD mean > 0, L3M >= 0, maxDD and worst week not worse; older (tolerant) = PRE and X' maxDD not worse, mean > -25 $/wk. Placebo = same cells with TICK shifted 11/23/37 trading days; family null = best gated score over all cells on TICK shifted 8-60 days (40 draws).

Counts: cells 6768; recent gate 194; recent+older 9. Family null (shifted TICK): median recent-gate cells 141, median recent+older 8; best recent+older score q95 37.6 (real best 14.6). Score = sum of maxDD and worst-week improvements over HOLD, L6M, PRE, X' in $k.

### 3.E. Item 1 entry: best recent-gate cells (recent+older marked old=True)

| id | n_L6M | dm_L6M | dm_HOLD | dm_PRE | dm_XP | dd_L6M | dd_HOLD | dd_PRE | dd_XP | ww_L6M | ww_HOLD | b5_L6M | wtl_L6M | stp_L6M | score | pl11_score | pl23_score | pl37_score | old |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E|cum|<=q33|skip|P7|nyam | 29.0 | 363.7 | 241.5 | -310.2 | 344.3 | 0.0 | 596.9 | 2199.9 | 6267.1 | 0.0 | 0.0 | 2057.2 | 0 | 0.0 | 9.6 | -5.2 | 3.3 | 8.5 | False |
| E|cum|<=q33|skip|P7|rth | 29.0 | 363.7 | 241.5 | -310.2 | 344.3 | 0.0 | 596.9 | 2199.9 | 6267.1 | 0.0 | 0.0 | 2057.2 | 0 | 0.0 | 9.6 | -5.2 | 3.3 | 8.5 | False |
| E|nhl8|<=q10|half|ALL|rth | 30.0 | 26.1 | 2.6 | -468.2 | -356.4 | 0.0 | 2804.6 | -1871.1 | 3257.7 | 0.0 | 0.0 | 645.9 | 0 | 0.0 | 5.3 | -6.0 | -6.4 | 1.0 | False |
| E|cum|<=q33|half|P7|nyam | 29.0 | 181.8 | 120.8 | -155.1 | 172.2 | 0.0 | 298.5 | 1099.9 | 3133.6 | 0.0 | 0.0 | 1028.6 | 0 | 0.0 | 5.1 | -1.6 | 1.7 | 4.5 | False |
| E|cum|<=q33|half|P7|rth | 29.0 | 181.8 | 120.8 | -155.1 | 172.2 | 0.0 | 298.5 | 1099.9 | 3133.6 | 0.0 | 0.0 | 1028.6 | 0 | 0.0 | 5.1 | -1.6 | 1.7 | 4.5 | False |
| E|p30|<=q33|skip|M7|rth | 71.0 | 117.4 | 326.5 | -170.4 | 78.5 | 609.7 | 4071.4 | 397.9 | -3964.4 | 609.7 | 664.7 | 1311.6 | 0 | 0.1 | 3.5 | -14.2 | -4.8 | -5.8 | False |
| E|p30|<=q33|skip|M7|nyam | 71.0 | 117.4 | 326.5 | -170.4 | 78.5 | 609.7 | 4071.4 | 397.9 | -3964.4 | 609.7 | 664.7 | 1311.6 | 0 | 0.1 | 3.5 | -14.2 | -4.8 | -5.8 | False |
| E|cs15|<=q33|half|P7|nyam | 51.0 | 4.7 | 203.8 | 421.9 | -70.8 | 0.0 | 436.2 | 497.6 | 6971.1 | 0.0 | 0.0 | -3238.4 | 0 | 0.0 | 3.2 | 9.3 | 1.5 | -2.4 | False |

- best in session nyam: E|cum|<=q33|skip|P7|nyam: L6M 364 / HOLD 242 / PRE -310 / X' 344 $/wk, maxDD gain L6M 0 HOLD 597 PRE 2200 X' 6267, old-gate False, placebo scores -5.2/3.3/8.5 vs real 9.6.
- best in session rth: E|cum|<=q33|skip|P7|rth: L6M 364 / HOLD 242 / PRE -310 / X' 344 $/wk, maxDD gain L6M 0 HOLD 597 PRE 2200 X' 6267, old-gate False, placebo scores -5.2/3.3/8.5 vs real 9.6.

### 3.K. Item 2 hold at cut: best recent-gate cells (recent+older marked old=True)

| id | n_L6M | dm_L6M | dm_HOLD | dm_PRE | dm_XP | dd_L6M | dd_HOLD | dd_PRE | dd_XP | ww_L6M | ww_HOLD | b5_L6M | wtl_L6M | stp_L6M | score | pl11_score | pl23_score | pl37_score | old |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K|m60|>=q67|hold|K7|rth | 39.0 | 84.1 | 335.8 | 396.6 | 311.0 | 0.0 | 2819.9 | 2357.4 | 6028.4 | 0.0 | 0.0 | 2683.7 | 0 | 0.0 | 14.6 | 2.4 | 3.1 | 6.2 | True |
| K|cum|>=q67|hold|K7|rth | 33.0 | 122.5 | 208.6 | 442.0 | 168.6 | 0.0 | 3097.8 | 1729.0 | 4749.3 | 0.0 | 0.0 | 1124.0 | 0 | 0.0 | 10.6 | 5.7 | 9.9 | 6.7 | True |
| K|cum|>=q67|hold|K7|nyam | 22.0 | 12.6 | 108.5 | 241.1 | 77.2 | 0.0 | 3861.2 | 1729.0 | -1414.4 | 0.0 | 0.0 | 1644.6 | 0 | 0.0 | 5.2 | -0.8 | 2.1 | 1.8 | False |
| K|m30|>=q67|hold|K7|rth | 50.0 | 20.6 | 190.2 | 232.5 | 169.1 | 0.0 | 629.9 | -611.0 | 3378.1 | 0.0 | 0.0 | 5339.3 | 0 | 0.0 | 2.8 | 5.4 | 11.2 | 7.6 | False |
| K|p15|>=q67|hold|K7|rth | 65.0 | 252.9 | 234.4 | 20.5 | 108.0 | 0.0 | 82.1 | -2893.2 | 5112.8 | 0.0 | 0.0 | 7454.0 | 0 | 0.0 | 1.1 | 11.1 | 5.8 | 6.1 | False |
| K|cs30|>=q67|hold|K7|rth | 48.0 | 75.7 | 172.0 | 40.9 | 182.0 | 0.0 | 902.8 | -1399.4 | 1463.7 | 0.0 | 0.0 | 6022.1 | 0 | 0.0 | 0.4 | 8.3 | 6.1 | 8.3 | False |
| K|cum|>=q67|hold|ALL|rth | 67.0 | 233.2 | 599.9 | 1531.7 | 253.0 | 0.0 | 2307.1 | 6447.1 | -6022.5 | 0.0 | 0.0 | -1297.1 | 0 | 0.0 | -0.8 | 1.8 | 5.9 | 19.6 | False |
| K|cum|>=q67|hold|ALL|nyam | 54.0 | 71.4 | 249.6 | 1257.3 | 347.0 | 0.0 | 3070.6 | 6447.1 | -9147.4 | 0.0 | 0.0 | -776.5 | 0 | 0.0 | -3.2 | 0.6 | 3.4 | 15.0 | False |

- best in session nyam: K|cum|>=q67|hold|K7|nyam: L6M 13 / HOLD 108 / PRE 241 / X' 77 $/wk, maxDD gain L6M 0 HOLD 3861 PRE 1729 X' -1414, old-gate False, placebo scores -0.8/2.1/1.8 vs real 5.2.
- best in session rth: K|m60|>=q67|hold|K7|rth: L6M 84 / HOLD 336 / PRE 397 / X' 311 $/wk, maxDD gain L6M 0 HOLD 2820 PRE 2357 X' 6028, old-gate True, placebo scores 2.4/3.1/6.2 vs real 14.6.

### 3.R. Item 4 re-entry: best recent-gate cells (recent+older marked old=True)

| id | n_L6M | dm_L6M | dm_HOLD | dm_PRE | dm_XP | dd_L6M | dd_HOLD | dd_PRE | dd_XP | ww_L6M | ww_HOLD | b5_L6M | wtl_L6M | stp_L6M | score | pl11_score | pl23_score | pl37_score | old |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| R|m15|<=q50|skip|ALL|nyam | 77.0 | 145.2 | 247.3 | 166.4 | 68.9 | 0.0 | 5354.3 | -1198.8 | 1965.8 | 0.0 | 0.0 | 1210.1 | 0 | 0.1 | 6.1 | -2.8 | 3.9 | 2.4 | False |
| R|m30|<=q50|skip|ALL|rth | 97.0 | 29.6 | 522.9 | 86.4 | -34.6 | 0.0 | 6053.9 | -813.3 | 2274.9 | 0.0 | 0.0 | 1241.0 | 0 | 0.1 | 6.1 | 7.2 | -0.7 | 5.5 | False |
| R|cs30|<=q50|skip|ALL|rth | 96.0 | 82.6 | 491.0 | 117.9 | 4.9 | 0.0 | 5354.3 | -813.3 | 2274.9 | 0.0 | 0.0 | 1241.0 | 0 | 0.1 | 5.4 | 3.3 | -0.4 | 4.0 | False |
| R|cum|<=q50|skip|ALL|nyam | 68.0 | 118.9 | 201.1 | 289.7 | -163.8 | 0.0 | 5253.1 | -2397.6 | 2299.9 | 0.0 | 0.0 | 6029.1 | 0 | 0.1 | 5.1 | 3.5 | 1.5 | -0.0 | False |
| R|m60|<=q50|skip|ALL|rth | 91.0 | 180.7 | 303.2 | 119.6 | 30.6 | 0.0 | 5354.3 | -2012.1 | 3232.1 | 0.0 | 0.0 | 5547.5 | 0 | 0.1 | 5.1 | 0.0 | -0.5 | 2.3 | False |
| R|m30|<=q50|skip|ALL|nyam | 76.0 | 363.7 | 546.6 | 48.4 | -115.1 | 0.0 | 6053.9 | -1198.8 | 1342.7 | 0.0 | 0.0 | 2828.1 | 0 | 0.1 | 4.7 | 7.6 | 0.4 | 3.9 | False |
| R|m15|<=q33|skip|ALL|nyam | 43.0 | 74.3 | 200.7 | 198.2 | -1.1 | 0.0 | 3439.9 | 0.0 | 2237.4 | 0.0 | 0.0 | -965.8 | 0 | 0.0 | 4.2 | 2.5 | 1.8 | 0.4 | False |
| R|m60|<=q50|skip|K7|nyam | 22.0 | 70.3 | 119.0 | -163.5 | 39.0 | 0.0 | 3712.4 | 0.0 | 670.5 | 0.0 | 0.0 | 2518.6 | 0 | 0.0 | 4.1 | 4.0 | 4.1 | 2.3 | False |

- best in session nyam: R|m15|<=q50|skip|ALL|nyam: L6M 145 / HOLD 247 / PRE 166 / X' 69 $/wk, maxDD gain L6M 0 HOLD 5354 PRE -1199 X' 1966, old-gate False, placebo scores -2.8/3.9/2.4 vs real 6.1.
- best in session rth: R|m30|<=q50|skip|ALL|rth: L6M 30 / HOLD 523 / PRE 86 / X' -35 $/wk, maxDD gain L6M 0 HOLD 6054 PRE -813 X' 2275, old-gate False, placebo scores 7.2/-0.7/5.5 vs real 6.1.

### 3.T. Item 5 trend day: best recent-gate cells (recent+older marked old=True)

| id | n_L6M | dm_L6M | dm_HOLD | dm_PRE | dm_XP | dd_L6M | dd_HOLD | dd_PRE | dd_XP | ww_L6M | ww_HOLD | b5_L6M | wtl_L6M | stp_L6M | score | pl11_score | pl23_score | pl37_score | old |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| T|f60|t67_with|press|K7|rth | 17.0 | 317.3 | 165.9 | 158.4 | 274.7 | 0.0 | 0.0 | -900.9 | 3535.3 | 0.0 | 0.0 | 1940.3 | 0 | 0.0 | 2.9 | 2.3 | 2.0 | -9.0 | False |
| T|f30|t50_with_hold|hold|K7|rth | 22.0 | 60.0 | 175.6 | 421.7 | -47.5 | 0.0 | 2199.4 | 3090.9 | -2117.9 | 0.0 | 0.0 | 4244.6 | 0 | 0.0 | 2.3 | 6.1 | 6.4 | -4.3 | False |
| T|f30|t50_with|press|K7|nypm | 24.0 | 287.6 | 138.8 | 27.4 | 23.2 | 0.0 | 0.0 | 599.2 | 856.5 | 0.0 | 0.0 | 1399.6 | 0 | 0.0 | 1.1 | 1.2 | -2.3 | -3.3 | True |
| T|f30|t50_with|press|ALL|nypm | 24.0 | 287.6 | 138.8 | 27.4 | 23.2 | 0.0 | 0.0 | 599.2 | 856.5 | 0.0 | 0.0 | 1399.6 | 0 | 0.0 | 1.1 | 1.2 | -2.3 | -3.3 | True |
| T|f60|t67_with|press|ALL|rth | 37.0 | 762.0 | 252.7 | 297.9 | 390.4 | 0.0 | 0.0 | -2469.0 | 4305.1 | 0.0 | 0.0 | 6738.1 | 0 | 0.0 | 1.0 | 2.7 | 6.1 | -9.3 | False |
| T|f60|t67_with|press|ALL|nyam | 27.0 | 523.5 | 98.3 | 180.7 | 207.7 | 0.0 | 0.0 | -2014.1 | 2094.2 | 0.0 | 0.0 | 5541.8 | 0 | 0.0 | -0.8 | 0.9 | 7.6 | -4.8 | False |
| T|f30|t50_with_hold|hold|ALL|rth | 41.0 | 167.3 | 70.4 | 934.1 | 4.2 | 0.0 | 1408.7 | 8018.3 | -7758.6 | 0.0 | 0.0 | 3855.8 | 0 | 0.0 | -1.8 | -1.5 | 6.8 | 1.7 | False |

- best in session nyam: T|f60|t67_with|press|ALL|nyam: L6M 524 / HOLD 98 / PRE 181 / X' 208 $/wk, maxDD gain L6M 0 HOLD 0 PRE -2014 X' 2094, old-gate False, placebo scores 0.9/7.6/-4.8 vs real -0.8.
- best in session nypm: T|f30|t50_with|press|K7|nypm: L6M 288 / HOLD 139 / PRE 27 / X' 23 $/wk, maxDD gain L6M 0 HOLD 0 PRE 599 X' 857, old-gate True, placebo scores 1.2/-2.3/-3.3 vs real 1.1.
- best in session rth: T|f60|t67_with|press|K7|rth: L6M 317 / HOLD 166 / PRE 158 / X' 275 $/wk, maxDD gain L6M 0 HOLD 0 PRE -901 X' 3535, old-gate False, placebo scores 2.3/2.0/-9.0 vs real 2.9.

### 3.C. Item 6 carry: best recent-gate cells (recent+older marked old=True)

| id | n_L6M | dm_L6M | dm_HOLD | dm_PRE | dm_XP | dd_L6M | dd_HOLD | dd_PRE | dd_XP | ww_L6M | ww_HOLD | b5_L6M | wtl_L6M | stp_L6M | score | pl11_score | pl23_score | pl37_score | old |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C|clast60|<=q33|skip|P7|asia | 147.0 | 739.7 | 89.2 | -1157.4 | 414.5 | 18391.7 | 11320.9 | 11056.6 | 14610.4 | 17612.1 | 691.3 | -12246.0 | 0 | 0.0 | 82.4 | 1.8 | -40.6 | 7.9 | False |
| C|cp30|<=q20|half|ALL|night | 741.0 | 745.6 | 471.9 | -537.9 | -943.9 | 11124.2 | 18382.1 | -11130.9 | 12720.9 | 10344.6 | 12559.7 | -1488.1 | 0 | 0.0 | 59.2 | -23.3 | 30.7 | 34.1 | False |
| C|clast30|<=q20|skip|ALL|asia | 294.0 | 1983.4 | 640.1 | -1388.9 | -851.1 | 14936.1 | 4062.3 | -13650.2 | 21319.8 | 15905.2 | 15289.2 | -795.0 | 0 | 1.0 | 53.2 | -64.0 | -103.6 | -7.5 | False |
| C|clast60|<=q33|half|P7|asia | 147.0 | 369.9 | 44.6 | -578.7 | 207.2 | 13726.1 | 5660.4 | 5529.7 | 7305.2 | 13978.4 | 345.7 | -6123.0 | 0 | 0.0 | 51.2 | 11.1 | -8.8 | 6.9 | False |
| C|clast30|<=q20|half|ALL|night | 436.0 | 1066.3 | 738.1 | -633.6 | -937.4 | 11641.3 | 17322.3 | -9516.5 | 5451.5 | 11641.3 | 10719.5 | -1399.3 | 0 | 0.0 | 49.2 | -24.1 | -3.4 | 45.2 | False |
| C|clast30|<=q20|half|ALL|asia | 294.0 | 991.7 | 320.1 | -694.5 | -425.6 | 11003.7 | 2031.1 | -1809.5 | 12310.5 | 11003.7 | 7644.6 | -397.5 | 0 | 0.0 | 41.2 | -10.5 | -32.5 | 16.2 | False |
| C|cnhl|<=q20|skip|K7|night | 109.0 | 40.1 | 377.3 | -209.8 | 19.5 | 3238.7 | 7749.7 | 1952.4 | 17954.0 | 3238.7 | 3372.6 | -3988.6 | 0 | 0.1 | 37.7 | 13.7 | 26.1 | 21.4 | False |
| C|clast30|<=q20|skip|ALL|night | 436.0 | 2132.7 | 1476.2 | -1267.1 | -1874.8 | 14726.6 | 28861.6 | -47659.3 | 2518.1 | 13947.0 | 21439.1 | -2798.7 | 1 | 1.2 | 35.0 | -151.6 | -69.9 | 42.2 | False |

- best in session asia: C|clast60|<=q33|skip|P7|asia: L6M 740 / HOLD 89 / PRE -1157 / X' 414 $/wk, maxDD gain L6M 18392 HOLD 11321 PRE 11057 X' 14610, old-gate False, placebo scores 1.8/-40.6/7.9 vs real 82.4.
- best in session london: C|cp30|<=q20|half|ALL|london: L6M 650 / HOLD 539 / PRE 207 / X' -530 $/wk, maxDD gain L6M 638 HOLD 15011 PRE 9765 X' -7701, old-gate False, placebo scores -6.3/37.6/12.5 vs real 28.9.
- best in session night: C|cp30|<=q20|half|ALL|night: L6M 746 / HOLD 472 / PRE -538 / X' -944 $/wk, maxDD gain L6M 11124 HOLD 18382 PRE -11131 X' 12721, old-gate False, placebo scores -23.3/30.7/34.1 vs real 59.2.

### 3.D. Survivors (recent+older gate) with TICK delayed 1 / 5 / 15 min (same cells; score and L6M/HOLD mean)

| id | score | d1_score | d5_score | d15_score | dm_L6M | d1_dm6 | d5_dm6 | d15_dm6 | dm_HOLD | d1_dmH | d5_dmH | d15_dmH |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K|m60|>=q67|hold|K7|rth | 14.6 | 13.7 | 13.1 | 13.9 | 84.1 | 31.9 | 34.7 | 214.5 | 335.8 | 334.2 | 286.0 | 370.3 |
| C|cday|>=q90|press|P7|asia | 11.6 | 11.6 | 11.6 | 11.6 | 433.5 | 433.5 | 433.5 | 433.5 | 557.1 | 557.1 | 557.1 | 557.1 |
| K|cum|>=q67|hold|K7|rth | 10.6 | 11.4 | 10.8 | 14.7 | 122.5 | 96.8 | 195.0 | 103.5 | 208.6 | 217.0 | 309.6 | 246.9 |
| C|cday|>=q67|press|H7|night | 5.7 | 5.7 | 5.7 | 5.7 | 235.2 | 235.2 | 235.2 | 235.2 | 178.3 | 178.3 | 178.3 | 178.3 |
| C|cday|>=q67|press|H7|asia | 5.7 | 5.7 | 5.7 | 5.7 | 235.2 | 235.2 | 235.2 | 235.2 | 178.3 | 178.3 | 178.3 | 178.3 |
| C|cf30|<=q10|skip|K7|asia | 4.0 | 4.0 | 4.0 | 4.0 | 284.8 | 284.8 | 284.8 | 284.8 | 6.5 | 6.5 | 6.5 | 6.5 |
| C|cf30|<=q10|half|K7|asia | 2.3 | 2.3 | 2.3 | 2.3 | 142.4 | 142.4 | 142.4 | 142.4 | 3.2 | 3.2 | 3.2 | 3.2 |
| T|f30|t50_with|press|ALL|nypm | 1.1 | 1.1 | 1.1 | 1.1 | 287.6 | 287.6 | 287.6 | 287.6 | 138.8 | 138.8 | 138.8 | 138.8 |
| T|f30|t50_with|press|K7|nypm | 1.1 | 1.1 | 1.1 | 1.1 | 287.6 | 287.6 | 287.6 | 287.6 | 138.8 | 138.8 | 138.8 | 138.8 |

## 4. PART 2 exact-engine confirmation (separate hook module tk_hooks.py, identity first)

Not started.

## 5. Status



## 6. Delayed-TICK (real-time subscription) summary

See 3.D (first order) and section 4 (exact).


## 7. PART 3 new books (W-TK2): see autopilot/DS3_TICK_BOOKS.md

# DS3_TICK_BOOKS - new TICK books on NQ (W-TK2), research only, NO PASS claim. Built 2026-11-14 02:20 UTC

**VERDICT (plain):** Standalone NQ screen (5 books x 6 session units, 1,470-cell entry/stop/target/time grid, measured fills, real TICK vs TICK shifted 11/23/37 trading days): 9013 cells pass the both-window gate (L3M,L6M,HOLD,PRE,X' all > 0, enough trades) AND beat the same cell on the shifted-TICK placebos in recent and older windows; but these come from a 1.8M-cell search and only 2 of 22 book/unit families have a best cell above the best placebo-family cell, so the standalone evidence is WEAK (selection-dominated), and the literal directive book B1 at +/-1000 is too rare (<=20 trades/6 months) to pass any gate. Exact-engine injected stack numbers: not yet available (runs queued under admission tag TKB behind UW/UR/RU; box at worker cap).

Data: TICK 2023-04-03..2026-11-13, 911 sessions, 354,080 RTH bars; parse identical to W-TK1 tick_clean.parquet (max abs diff 0). Usable at bar end + 5 s. NQ 1-min price from the 1-s path. ES standalone only (hook NQ-only).

## 1. Books and generators (code/th_tickb/tkb_events.py; prereg sha in DECISIONS.md)
- B1 fade/follow TICK extremes, thr 600/800/1000, regime none / NQ ER(first 30 min)<0.30 / |mean TICK first 30 min|<100 / both.
- B2 persistent TICK (rolling mean L15/L30 >= 100/200/300 with share>0 >= 0.6), regime none or ER>=0.35, trigger onset or resumption (pullback of TICK back through 0); market/confirm entries only (no limit pullbacks: hook limit).
- B3 divergence: NQ new session high/low while TICK 10/20-min mean weak (<0 / <150), or no TICK extreme 400/600 in L minutes, or confirmed (C); fade and follow.
- B4 first-hour trend day: ER over first 30/60 min >= 0.30/0.45 (+ optional TICK confirm), market entry at the first pullback of 25%/40% of the move.
- Units: S1 09:30-10:00, S2 10:00-12:00, S3 12:00-14:30, S4 14:30-15:00 (live no-entry from 15:00), nyam, nypm. CLOCK baseline: every-day entries at 09:35/10:05/12:05/14:35.
- Selection (tolerant gate): L3M, L6M, HOLD > 0 standalone, n_L6M >= 15-20; both-window = PRE>0 and X'>0 too; edge = recents (L6M+HOLD)/2 minus the same cell on shifted TICK (mean of 3), edge_old likewise for (PRE+X')/2. Ranked by L6M Calmar (DD floor $1,200).

## 2. Best per book and per session (NQ standalone, harness; NOT the injected number)

| book | unit | tier | var | cell | dir | n_L6M | L3M | L6M | HOLD | PRE | X | dd_L6M | worst_L6M | edge_vs_placebo | rec_placebo | fam_null_max | beats_family_null | injectable |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B1 | S1 | both-window+placebo-edge | B1_t600_none_fade | Emkt_S90_T60_X120 | 0.0 | 27.0 | 219.0 | 304.0 | 69.0 | 129.0 | 159.0 | 3669.0 | -1814.0 | 150.0 | 36.0 | 1628.0 | False | True |
| B1 | S2 | both-window+placebo-edge | B1_t600_er_fade | Eb1_Sa2_T90_X30 | 0.0 | 20.0 | 343.0 | 721.0 | 542.0 | 104.0 | 5.0 | 749.0 | -749.0 | 679.0 | -47.0 | 1975.0 | False | True |
| B1 | S3 | both-window+placebo-edge | B1_t600_er_follow | Ep10_S60_T30_XSE | -1.0 | 26.0 | 379.0 | 314.0 | 16.0 | 69.0 | 21.0 | 1214.0 | -1214.0 | 136.0 | 29.0 | 927.0 | False | False |
| B1 | S4 | both-window+placebo-edge | B1_t600_none_fade | Emkt_Sa1_Tnone_X15 | 0.0 | 25.0 | 1301.0 | 816.0 | 168.0 | 213.0 | 179.0 | 1660.0 | -1571.0 | 526.0 | -34.0 | 254.0 | True | True |
| B1 | nyam | both-window+placebo-edge | B1_t600_er_fade | Eb1_Sa2_T90_X30 | 0.0 | 20.0 | 343.0 | 721.0 | 542.0 | 65.0 | 83.0 | 749.0 | -749.0 | 691.0 | -59.0 | 1975.0 | False | True |
| B1 | nypm | both-window+placebo-edge | B1_t600_er_follow | Ep10_S90_T30_X15 | -1.0 | 31.0 | 258.0 | 302.0 | 60.0 | 60.0 | 36.0 | 1187.0 | -907.0 | 195.0 | -14.0 | 863.0 | False | False |
| B2 | S1 | both-window+placebo-edge | B2_L15_t100_er_onset | Ep3_Sa1_Tnone_X60 | 0.0 | 22.0 | 1724.0 | 1183.0 | 908.0 | 405.0 | 90.0 | 3366.0 | -2250.0 | 1002.0 | 44.0 | 1061.0 | False | False |
| B2 | S2 | both-window+placebo-edge | B2_L30_t100_none_onset | Eb3_Sa1_T30_X30 | 0.0 | 50.0 | 1151.0 | 830.0 | 449.0 | 232.0 | 149.0 | 831.0 | -831.0 | 681.0 | -42.0 | 1599.0 | False | True |
| B2 | S3 | both-window+placebo-edge | B2_L15_t100_none_resume | Eb1_Sa2_Ta2_XSE | 0.0 | 50.0 | 868.0 | 833.0 | 316.0 | 200.0 | 228.0 | 2247.0 | -2247.0 | 643.0 | -69.0 | 2273.0 | False | True |
| B2 | S4 | recent-only | B2_L15_t100_none_onset | Eb3_Sa2_Ta2_X15 | 0.0 | 29.0 | 61.0 | 290.0 | 126.0 | -60.0 | -74.0 | 1411.0 | -1411.0 | 174.0 | 34.0 | 719.0 | False | True |
| B2 | nyam | both-window+placebo-edge | B2_L15_t100_er_onset | Eb5_Sa2_Tnone_XSE | 0.0 | 25.0 | 1228.0 | 1322.0 | 539.0 | 37.0 | 357.0 | 1492.0 | -1492.0 | 684.0 | 246.0 | 1929.0 | False | True |
| B2 | nypm | both-window+placebo-edge | B2_L15_t100_none_onset | Ep5_S60_Ta2_XSE | -1.0 | 101.0 | 850.0 | 1014.0 | 659.0 | 164.0 | 51.0 | 2400.0 | -2168.0 | 196.0 | 640.0 | 2270.0 | False | False |
| B3 | S1 | both-window+placebo-edge | B3_L10_Am0_fade | Emkt_Sa2_Ta2_XSE | 1.0 | 31.0 | 1179.0 | 1197.0 | 519.0 | 31.0 | 9.0 | 1940.0 | -1940.0 | 642.0 | 216.0 | 2474.0 | False | True |
| B3 | S2 | both-window+placebo-edge | B3_L20_Am0_fade | Eb3_S45_Ta2_X15 | -1.0 | 24.0 | 56.0 | 461.0 | 159.0 | 93.0 | 23.0 | 1233.0 | -1233.0 | 341.0 | -31.0 | 2461.0 | False | True |
| B3 | S3 | both-window+placebo-edge | B3_L20_Am150_follow | Emkt_S60_T30_X120 | 0.0 | 65.0 | 705.0 | 619.0 | 131.0 | 45.0 | 1.0 | 1686.0 | -1068.0 | 39.0 | 336.0 | 1240.0 | False | True |
| B3 | S4 | both-window+placebo-edge | B3_L20_Am150_fade | Emkt_S90_T90_X15 | 0.0 | 22.0 | 667.0 | 320.0 | 243.0 | 29.0 | 72.0 | 1814.0 | -1814.0 | 261.0 | 21.0 | 280.0 | True | True |
| B3 | nyam | both-window+placebo-edge | B3_L10_Am0_fade | Eb3_Sa2_Ta1_X15 | -1.0 | 36.0 | 508.0 | 541.0 | 278.0 | 6.0 | 65.0 | 825.0 | -716.0 | 385.0 | 25.0 | 2503.0 | False | True |
| B3 | nypm | both-window+placebo-edge | B3_L10_Cc150_fade | Ep3_S30_Ta1_X15 | 0.0 | 38.0 | 546.0 | 484.0 | 217.0 | 2.0 | 21.0 | 1968.0 | -1227.0 | 388.0 | -38.0 | 1093.0 | False | False |
| B4 | S2 | recent-only | B4_N30_er30_none_pf40 | Ep5_S60_T60_X120 | 1.0 | 15.0 | 549.0 | 267.0 | 126.0 | -55.0 | -131.0 | 2427.0 | -1214.0 | 0.0 | 196.0 | 299.0 | False | False |
| B4 | S3 | no gated cell |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| B4 | nyam | recent-only | B4_N30_er30_none_pf40 | Ep5_S60_T60_X120 | 1.0 | 15.0 | 549.0 | 267.0 | 126.0 | -55.0 | -131.0 | 2427.0 | -1214.0 | 0.0 | 196.0 | 299.0 | False | False |
| B4 | nypm | no gated cell |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


CLOCK baseline (every-day entry, best gated cell per unit; the TICK books must beat this, not zero):

| unit | dir | var | cell | n_L6M | mean_L3M | mean_L6M | mean_HOLD | mean_PRE | mean_X' | dd_L6M |
|---|---|---|---|---|---|---|---|---|---|---|
| nypm | -1 | CLOCK_c1205 | Ep5_Sa1_Ta1_XSE | 117.0 | 1872.0 | 1232.0 | 818.0 | -261.0 | -431.0 | 1664.0 |
| S3 | -1 | CLOCK_c1205 | Ep5_Sa1_Ta1_XSE | 117.0 | 1872.0 | 1232.0 | 818.0 | -261.0 | -431.0 | 1664.0 |
| nyam | 0 | CLOCK_c1005 | Emkt_Sa1_T90_X30 | 250.0 | 1314.0 | 1195.0 | 485.0 | -875.0 | -674.0 | 3241.0 |
| S2 | 0 | CLOCK_c1005 | Emkt_Sa1_T90_X30 | 250.0 | 1314.0 | 1195.0 | 485.0 | -875.0 | -674.0 | 3241.0 |
| S1 | 1 | CLOCK_c0935 | Emkt_S60_Ta2_X30 | 125.0 | 1397.0 | 1112.0 | 673.0 | -214.0 | -206.0 | 3981.0 |
| S4 | 1 | CLOCK_c1435 | Eb3_Sa2_Tnone_X15 | 58.0 | 518.0 | 619.0 | 54.0 | -149.0 | 152.0 | 2398.0 |


## 3. Delayed TICK 1/5/15 min (standalone, same cell as finalist)

| name | var | unit | cell | real_L6M | real_HOLD | real_PRE | real_X | d1_L6M | d1_HOLD | d1_PRE | d1_X | d5_L6M | d5_HOLD | d5_PRE | d5_X | d15_L6M | d15_HOLD | d15_PRE | d15_X |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1 | B2_L15_t100_er_onset | nyam | Eb5_Sa2_Tnone_XSE | 1322.0 | 539.0 | 37.0 | 357.0 | 972.0 | 304.0 | 63.0 | 230.0 | 555.0 | 48.0 | 191.0 | 157.0 | 148.0 | 81.0 | 252.0 | 316.0 |
| F2 | B2_L30_t100_none_onset | S2 | Eb3_Sa1_T30_X30 | 830.0 | 449.0 | 232.0 | 149.0 | 302.0 | 243.0 | 476.0 | 207.0 | 318.0 | 366.0 | -305.0 | 248.0 | 145.0 | 127.0 | -25.0 | -508.0 |
| F3 | B3_L10_Am0_fade | S1 | Emkt_Sa2_Tnone_XSE | 2843.0 | 1265.0 | 51.0 | 431.0 | 2968.0 | 1263.0 | -69.0 | 669.0 | 1483.0 | 305.0 | -196.0 | 86.0 | 761.0 | 453.0 | -596.0 | 91.0 |
| F4 | B1_t600_er_fade | S2 | Eb1_Sa2_T90_X30 | 721.0 | 542.0 | 104.0 | 5.0 | 288.0 | 308.0 | 162.0 | -85.0 | 92.0 | 40.0 | -160.0 | 189.0 | 296.0 | 161.0 | -265.0 | 14.0 |
| F5 | B2_L15_t100_none_resume | nypm | Eb1_Sa2_Ta2_XSE | 738.0 | 305.0 | 234.0 | 282.0 | 1105.0 | 575.0 | 93.0 | -319.0 | 731.0 | 157.0 | 247.0 | 162.0 | 999.0 | 547.0 | 194.0 | -111.0 |
| F6 | B1_t600_none_fade | S4 | Emkt_Sa1_Tnone_X15 | 816.0 | 168.0 | 213.0 | 179.0 | 165.0 | -135.0 | 244.0 | -12.0 | 221.0 | -79.0 | 203.0 | -227.0 | 64.0 | -60.0 | 49.0 | 339.0 |
| F7 | B3_L20_Am150_follow | S3 | Emkt_S60_T30_X120 | 619.0 | 131.0 | 45.0 | 1.0 | 619.0 | 120.0 | 39.0 | 25.0 | 641.0 | 114.0 | -45.0 | 115.0 | 462.0 | 33.0 | 108.0 | -90.0 |
| F8 | B4_N30_er30_none_pf25 | S2 | Emkt_Sa2_T30_X15 | 141.0 | 150.0 | -120.0 | 86.0 | 141.0 | 150.0 | -120.0 | 90.0 | 141.0 | 150.0 | -120.0 | 90.0 | 141.0 | 150.0 | -120.0 | 91.0 |


## 4. INJECTED STACK numbers (exact engine, JN05W2 base, all layers ON, hook uw_inject, tag TKB). Identity: TL3_TKB_ID must give 598 / 25943.82 for 202610.

No injected run finished yet.


Identity check: 


## 5. ES standalone (harness, 1 tick/side assumed)

| book | unit | tier | var | cell | dir | n_L6M | L3M | L6M | HOLD | PRE | X | dd_L6M | worst_L6M | edge_vs_placebo | rec_placebo | fam_null_max | beats_family_null | injectable |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B1 | S1 | both-window+placebo-edge | B1_t600_none_follow | Emkt_Sa2_Tnone_X15 | 0.0 | 27.0 | 242.0 | 119.0 | 60.0 | 219.0 | 73.0 | 6200.0 | -2068.0 | 2.0 | 88.0 | 1371.0 | False | True |
| B1 | S2 | both-window+placebo-edge | B1_t600_er_fade | Emkt_Sa2_Tnone_X120 | 0.0 | 34.0 | 44.0 | 264.0 | 243.0 | 17.0 | 73.0 | 2375.0 | -1510.0 | 67.0 | 187.0 | 1260.0 | False | True |
| B1 | S3 | both-window+placebo-edge | B1_t600_ercum_follow | Emkt_Sa2_T90_X120 | 0.0 | 32.0 | 488.0 | 270.0 | 105.0 | 188.0 | 64.0 | 3794.0 | -2350.0 | 529.0 | -341.0 | 759.0 | False | True |
| B1 | S4 | both-window+placebo-edge | B1_t600_none_fade | Emkt_S45_Ta1_XSE | 0.0 | 25.0 | 333.0 | 248.0 | 105.0 | 27.0 | 31.0 | 1345.0 | -1345.0 | 203.0 | -26.0 | 95.0 | True | True |
| B1 | nyam | recent-only | B1_t600_er_fade | Eb1_S45_T90_X120 | 0.0 | 17.0 | 456.0 | 647.0 | 673.0 | -436.0 | -26.0 | 1345.0 | -1345.0 | 643.0 | 17.0 | 1177.0 | False | True |
| B1 | nypm | both-window+placebo-edge | B1_t600_ercum_follow | Ep5_S30_Ta2_X60 | -1.0 | 22.0 | 715.0 | 334.0 | 122.0 | 69.0 | 16.0 | 3657.0 | -3657.0 | 363.0 | -136.0 | 723.0 | False | False |
| B2 | S1 | both-window+placebo-edge | B2_L15_t100_none_onset | Ep3_Sa1_Tnone_X120 | -1.0 | 25.0 | 1486.0 | 1228.0 | 561.0 | 35.0 | 9.0 | 7390.0 | -3649.0 | 621.0 | 273.0 | 1922.0 | False | False |
| B2 | S2 | both-window+placebo-edge | B2_L15_t100_none_resume | Emkt_S60_T45_X120 | 1.0 | 34.0 | 238.0 | 285.0 | 33.0 | 112.0 | 22.0 | 1626.0 | -1184.0 | 164.0 | -5.0 | 827.0 | False | True |
| B2 | S3 | both-window+placebo-edge | B2_L30_t100_none_resume | Emkt_S60_T45_X60 | 0.0 | 71.0 | 594.0 | 491.0 | 221.0 | 216.0 | 34.0 | 2208.0 | -1344.0 | 529.0 | -174.0 | 1342.0 | False | True |
| B2 | S4 | recent-only | B2_L15_t100_none_onset | Eb3_Sa1_Ta2_X120 | -1.0 | 19.0 | 170.0 | 208.0 | 64.0 | -111.0 | -478.0 | 1931.0 | -1407.0 | 70.0 | 66.0 | 347.0 | False | True |
| B2 | nyam | both-window+placebo-edge | B2_L30_t100_none_resume | Eb1_S60_Tnone_X120 | 0.0 | 31.0 | 516.0 | 380.0 | 137.0 | 88.0 | 204.0 | 2720.0 | -1444.0 | 361.0 | -103.0 | 1520.0 | False | True |
| B2 | nypm | both-window+placebo-edge | B2_L15_t100_none_resume | Emkt_Sa2_T45_X60 | -1.0 | 67.0 | 227.0 | 388.0 | 177.0 | 171.0 | 261.0 | 2658.0 | -1470.0 | 433.0 | -151.0 | 1260.0 | False | True |
| B3 | S1 | both-window+placebo-edge | B3_L10_Am150_follow | Eb5_S45_Tnone_X30 | 1.0 | 24.0 | 1113.0 | 984.0 | 512.0 | 460.0 | 114.0 | 2690.0 | -2635.0 | 181.0 | 567.0 | 1732.0 | False | True |
| B3 | S2 | both-window+placebo-edge | B3_L20_Bx600_follow | Eb5_S30_T90_X120 | 0.0 | 80.0 | 1519.0 | 2161.0 | 1344.0 | 432.0 | 61.0 | 3701.0 | -3657.0 | 42.0 | 1711.0 | 2565.0 | False | True |
| B3 | S3 | both-window+placebo-edge | B3_L10_Cc150_follow | Eb3_Sa2_Ta2_XSE | 0.0 | 20.0 | 383.0 | 416.0 | 62.0 | 146.0 | 68.0 | 1349.0 | -1349.0 | 208.0 | 31.0 | 1066.0 | False | True |
| B3 | S4 | recent-only | B3_L10_Bx600_follow | Ep3_S30_T30_X30 | 0.0 | 22.0 | 241.0 | 213.0 | 43.0 | -147.0 | -53.0 | 1219.0 | -1219.0 | 21.0 | 107.0 | 387.0 | False | False |
| B3 | nyam | both-window+placebo-edge | B3_L20_Am0_follow | Eb3_S60_T60_X120 | 1.0 | 25.0 | 342.0 | 472.0 | 312.0 | 77.0 | 66.0 | 1229.0 | -1184.0 | 185.0 | 207.0 | 2802.0 | False | True |
| B3 | nypm | both-window+placebo-edge | B3_L10_Cc150_fade | Eb3_S60_T45_X60 | 0.0 | 20.0 | 154.0 | 209.0 | 203.0 | 32.0 | 103.0 | 1010.0 | -1010.0 | 205.0 | 1.0 | 1074.0 | False | True |
| B4 | S2 | recent-only | B4_N30_er30_none_pf40 | Emkt_S90_Ta1_X60 | 0.0 | 24.0 | 336.0 | 144.0 | 54.0 | 20.0 | -99.0 | 1455.0 | -879.0 | 0.0 | 99.0 | 334.0 | False | True |
| B4 | S3 | no gated cell |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| B4 | nyam | recent-only | B4_N30_er30_none_pf40 | Emkt_S90_Ta1_X60 | 0.0 | 24.0 | 336.0 | 144.0 | 54.0 | 20.0 | -99.0 | 1455.0 | -879.0 | 0.0 | 99.0 | 334.0 | False | True |
| B4 | nypm | no gated cell |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |


## 6. Caveats
Grid-best cells from a 1.8M-cell search; the placebo columns show what the same cell earns on day-shifted TICK. Standalone profits shrink ~85% under live gates (DS3_UWBOOKS_B1 section 8): only section 4 counts. Delays use the real-time price with a stale TICK. Exact placebos (11/23/37) are run in the engine only for the finalists that pass L6M.
