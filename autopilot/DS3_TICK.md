# DS3_TICK: NYSE TICK as day-type, filter and trigger tool (W-TK1 sections 1-6; W-TK2 section 7)

Verdict (2026-11-14 20:21Z): PART 1 (forecast): 0 of 502 feature-family x target x session cells pass the lead rule; TICK does not forecast NQ direction, continuation, trend/chop or remaining range beyond the price-only benchmark in any slice (best gains are about 1% of variance and inside the family null). PART 2 first order: 6768 cells, 194 pass the recent gate, 9 pass recent+older; best recent+older drawdown score 14.6 vs family-null q95 37.6 (best-of-family on TICK shifted 8-60 days), so no first-order cell is separable from the best-of-family noise; exact-engine status: 39 exact candidates; tier-1 (L6M) complete 39; recent-gate survivors 21; advanced 10; jobs outstanding 27 (section 4).

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

Identity gate (hook module at identity before any candidate): TL3_TK_ID 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL | TL3_TK_ID2 202610: 598 trades net 25943.82 vs JN05W2 598 net 25943.82 -> IDENTICAL

Candidates 39; jobs outstanding 27; tier-1 L6M complete 39; recent-gate survivors 21; advanced to older+placebo+delay 10.

Deltas are cell minus JN05W2 on the same months (exact engine, net of fees $4.84 RT, measured fills); maxDD cut % > 0 = smaller drawdown; ww = worst week; b5 = sum of the reference best-5 weeks (ref vs cell); wtl = reference winning weeks turned losing; stp = full stops per week.

| cell | what | window | d mean $/wk | maxDD cut % | maxDD cell/ref | worst wk cell/ref | b5 cell/ref | wtl | stops/wk cell/ref | n cell |
|---|---|---|---|---|---|---|---|---|---|---|
| TL3_TK_C01 | C|clast60|<=q33|skip|P7|asia | L3M | 5498 | 24.7 | 39316/52233 | -20501/-36371 | 234835/241079 | 0 | 10.73/10.35 | 1889 |
| TL3_TK_C01 | C|clast60|<=q33|skip|P7|asia | L6M | -542 | 24.7 | 39316/52233 | -20501/-36371 | 281043/316288 | 0 | 11.22/10.99 | 4069 |
| TL3_TK_C02 | C|clast30|<=q20|skip|ALL|asia | L3M | 183 | 21.2 | 41178/52233 | -21009/-36371 | 209005/241079 | 0 | 9.89/10.35 | 1843 |
| TL3_TK_C02 | C|clast30|<=q20|skip|ALL|asia | L6M | 1069 | 21.2 | 41178/52233 | -21009/-36371 | 286714/316288 | 0 | 10.77/10.99 | 4139 |
| TL3_TK_C02 | C|clast30|<=q20|skip|ALL|asia | HOLD | 122 | -23.1 | 113335/92044 | -38309/-55145 | 337229/340478 | 2 | 10.18/10.66 | 7364 |
| TL3_TK_C03 | C|cp30|<=q20|half|ALL|london | L3M | 389 | 6.4 | 48905/52233 | -33042/-36371 | 239431/241079 | 0 | 10.42/10.35 | 1903 |
| TL3_TK_C03 | C|cp30|<=q20|half|ALL|london | L6M | -58 | 6.4 | 48905/52233 | -33042/-36371 | 319176/316288 | 0 | 10.99/10.99 | 4198 |
| TL3_TK_C04 | C|clast30|<=q33|half|ALL|london | L3M | -285 | 6.4 | 48905/52233 | -33042/-36371 | 233441/241079 | 0 | 10.42/10.35 | 1907 |
| TL3_TK_C04 | C|clast30|<=q33|half|ALL|london | L6M | -45 | 6.4 | 48905/52233 | -33042/-36371 | 311002/316288 | 0 | 10.99/10.99 | 4212 |
| TL3_TK_C04 | C|clast30|<=q33|half|ALL|london | HOLD | -12 | 18.2 | 75328/92044 | -52133/-55145 | 335697/340478 | 1 | 10.64/10.66 | 7543 |
| TL3_TK_C04 | C|clast30|<=q33|half|ALL|london | PRE | -163 | 11.6 | 81556/92243 | -44558/-52547 | 305735/311185 | 1 | 9.43/9.43 | 7559 |
| TL3_TK_C04 | C|clast30|<=q33|half|ALL|london | XP | -83 | -2.9 | 78337/76154 | -21132/-21663 | 185653/189332 | 1 | 10.80/10.82 | 3155 |
| TL3_TK_C05 | C|cp30|<=q20|half|ALL|night | L3M | 547 | 19.9 | 41819/52233 | -26026/-36371 | 227127/241079 | 0 | 10.04/10.35 | 1921 |
| TL3_TK_C05 | C|cp30|<=q20|half|ALL|night | L6M | 1039 | 19.9 | 41819/52233 | -26026/-36371 | 308039/316288 | 0 | 10.73/10.99 | 4250 |
| TL3_TK_C05 | C|cp30|<=q20|half|ALL|night | HOLD | 740 | 8.5 | 84255/92044 | -46121/-55145 | 323276/340478 | 1 | 10.47/10.66 | 7623 |
| TL3_TK_C05 | C|cp30|<=q20|half|ALL|night | PRE | -377 | -8.3 | 99936/92243 | -45011/-52547 | 283045/311185 | 2 | 9.39/9.43 | 7643 |
| TL3_TK_C05 | C|cp30|<=q20|half|ALL|night | XP | 164 | 14.7 | 64940/76154 | -22693/-21663 | 173796/189332 | 3 | 10.75/10.82 | 3161 |
| TL3_TK_C06 | C|clast30|<=q20|half|ALL|night | L3M | 1559 | 20.3 | 41642/52233 | -25779/-36371 | 245686/241079 | 0 | 10.04/10.35 | 1911 |
| TL3_TK_C06 | C|clast30|<=q20|half|ALL|night | L6M | 1594 | 20.3 | 41642/52233 | -25779/-36371 | 313417/316288 | 0 | 10.77/10.99 | 4227 |
| TL3_TK_C06 | C|clast30|<=q20|half|ALL|night | HOLD | 1283 | 14.7 | 78469/92044 | -44188/-55145 | 343956/340478 | 1 | 10.51/10.66 | 7560 |
| TL3_TK_C06 | C|clast30|<=q20|half|ALL|night | PRE | -303 | -2.8 | 94867/92243 | -45567/-52547 | 273810/311185 | 1 | 9.39/9.43 | 7647 |
| TL3_TK_C06 | C|clast30|<=q20|half|ALL|night | XP | -126 | 1.9 | 74697/76154 | -20591/-21663 | 171398/189332 | 2 | 10.71/10.82 | 3158 |
| TL3_TK_C07 | E|cum|<=q33|skip|P7|nyam | L3M | 329 | 0.0 | 52233/52233 | -36371/-36371 | 246612/241079 | 0 | 10.35/10.35 | 1864 |
| TL3_TK_C07 | E|cum|<=q33|skip|P7|nyam | L6M | 52 | 0.0 | 52233/52233 | -36371/-36371 | 317519/316288 | 0 | 11.03/10.99 | 4153 |
| TL3_TK_C07 | E|cum|<=q33|skip|P7|nyam | HOLD | 148 | 2.5 | 89698/92044 | -55145/-55145 | 345829/340478 | 0 | 10.59/10.66 | 7405 |
| TL3_TK_C07 | E|cum|<=q33|skip|P7|nyam | PRE | -486 | 2.9 | 89581/92243 | -52547/-52547 | 295900/311185 | 0 | 9.32/9.43 | 7397 |
| TL3_TK_C07 | E|cum|<=q33|skip|P7|nyam | XP | 347 | 4.0 | 73110/76154 | -21111/-21663 | 183578/189332 | 2 | 10.66/10.82 | 3073 |
| TL3_TK_C08 | E|cum|<=q33|half|P7|nyam | L3M | -188 | 0.0 | 52233/52233 | -36371/-36371 | 243518/241079 | 0 | 10.35/10.35 | 1875 |
| TL3_TK_C08 | E|cum|<=q33|half|P7|nyam | L6M | -87 | 0.0 | 52233/52233 | -36371/-36371 | 317351/316288 | 0 | 10.99/10.99 | 4169 |
| TL3_TK_C09 | E|cum|<=q33|skip|P7|rth | L3M | 329 | 0.0 | 52233/52233 | -36371/-36371 | 246612/241079 | 0 | 10.35/10.35 | 1864 |
| TL3_TK_C09 | E|cum|<=q33|skip|P7|rth | L6M | 52 | 0.0 | 52233/52233 | -36371/-36371 | 317519/316288 | 0 | 11.03/10.99 | 4153 |
| TL3_TK_C09 | E|cum|<=q33|skip|P7|rth | HOLD | 148 | 2.5 | 89698/92044 | -55145/-55145 | 345829/340478 | 0 | 10.59/10.66 | 7405 |
| TL3_TK_C09 | E|cum|<=q33|skip|P7|rth | PRE | -486 | 2.9 | 89581/92243 | -52547/-52547 | 295900/311185 | 0 | 9.32/9.43 | 7397 |
| TL3_TK_C09 | E|cum|<=q33|skip|P7|rth | XP | 347 | 4.0 | 73110/76154 | -21111/-21663 | 183578/189332 | 2 | 10.66/10.82 | 3073 |
| TL3_TK_C10 | E|nhl8|<=q10|half|ALL|rth | L3M | 144 | 0.0 | 52233/52233 | -36371/-36371 | 242973/241079 | 0 | 10.35/10.35 | 1876 |
| TL3_TK_C10 | E|nhl8|<=q10|half|ALL|rth | L6M | 26 | 0.0 | 52233/52233 | -36371/-36371 | 316288/316288 | 0 | 10.99/10.99 | 4170 |
| TL3_TK_C10 | E|nhl8|<=q10|half|ALL|rth | HOLD | 44 | 0.7 | 91410/92044 | -55145/-55145 | 340478/340478 | 0 | 10.66/10.66 | 7457 |
| TL3_TK_C10 | E|nhl8|<=q10|half|ALL|rth | PRE | 112 | -1.6 | 93723/92243 | -52547/-52547 | 314655/311185 | 0 | 9.43/9.43 | 7528 |
| TL3_TK_C10 | E|nhl8|<=q10|half|ALL|rth | XP | -133 | 2.0 | 74667/76154 | -20975/-21663 | 186283/189332 | 1 | 10.82/10.82 | 3150 |
| TL3_TK_C11 | K|cum|>=q67|hold|K7|nyam | L3M | -9 | 0.0 | 52233/52233 | -36371/-36371 | 246202/241079 | 0 | 11.03/10.35 | 1866 |
| TL3_TK_C11 | K|cum|>=q67|hold|K7|nyam | L6M | -415 | 0.0 | 52233/52233 | -36371/-36371 | 312107/316288 | 0 | 11.91/10.99 | 4152 |
| TL3_TK_C12 | K|cum|>=q67|hold|ALL|nyam | L3M | -88 | 0.0 | 52233/52233 | -36371/-36371 | 248271/241079 | 0 | 11.57/10.35 | 1863 |
| TL3_TK_C12 | K|cum|>=q67|hold|ALL|nyam | L6M | -675 | 0.0 | 52233/52233 | -36371/-36371 | 307546/316288 | 0 | 12.82/10.99 | 4142 |
| TL3_TK_C13 | K|m60|>=q67|hold|K7|rth | L3M | -601 | 0.0 | 52233/52233 | -36371/-36371 | 238787/241079 | 0 | 10.96/10.35 | 1866 |
| TL3_TK_C13 | K|m60|>=q67|hold|K7|rth | L6M | -718 | 0.0 | 52233/52233 | -36371/-36371 | 308612/316288 | 0 | 11.91/10.99 | 4151 |
| TL3_TK_C14 | K|cum|>=q67|hold|K7|rth | L3M | -9 | 0.0 | 52233/52233 | -36371/-36371 | 246202/241079 | 0 | 11.03/10.35 | 1866 |
| TL3_TK_C14 | K|cum|>=q67|hold|K7|rth | L6M | -415 | 0.0 | 52233/52233 | -36371/-36371 | 312107/316288 | 0 | 11.91/10.99 | 4152 |
| TL3_TK_C15 | T|f60|t67_with|press|ALL|nyam | L3M | 267 | 0.0 | 52233/52233 | -36371/-36371 | 245506/241079 | 0 | 10.35/10.35 | 1876 |
| TL3_TK_C15 | T|f60|t67_with|press|ALL|nyam | L6M | 240 | 0.0 | 52233/52233 | -36371/-36371 | 315227/316288 | 0 | 10.99/10.99 | 4162 |
| TL3_TK_C15 | T|f60|t67_with|press|ALL|nyam | HOLD | -60 | 0.0 | 92044/92044 | -55145/-55145 | 339493/340478 | 0 | 10.64/10.66 | 7444 |
| TL3_TK_C16 | T|f30|t50_with|press|K7|nypm | L3M | 297 | 0.0 | 52233/52233 | -36371/-36371 | 242273/241079 | 0 | 10.35/10.35 | 1875 |
| TL3_TK_C16 | T|f30|t50_with|press|K7|nypm | L6M | 16 | 0.0 | 52233/52233 | -36371/-36371 | 317933/316288 | 0 | 11.03/10.99 | 4161 |
| TL3_TK_C16 | T|f30|t50_with|press|K7|nypm | HOLD | 30 | 0.0 | 92044/92044 | -55145/-55145 | 338476/340478 | 0 | 10.68/10.66 | 7436 |
| TL3_TK_C16 | T|f30|t50_with|press|K7|nypm | PRE | -50 | -1.0 | 93167/92243 | -52547/-52547 | 316800/311185 | 1 | 9.43/9.43 | 7505 |
| TL3_TK_C16 | T|f30|t50_with|press|K7|nypm | XP | -131 | 2.2 | 74460/76154 | -24817/-21663 | 191418/189332 | 0 | 10.82/10.82 | 3146 |
| TL3_TK_C17 | T|f30|t50_with|press|ALL|nypm | L3M | 297 | 0.0 | 52233/52233 | -36371/-36371 | 242273/241079 | 0 | 10.35/10.35 | 1875 |
| TL3_TK_C17 | T|f30|t50_with|press|ALL|nypm | L6M | 16 | 0.0 | 52233/52233 | -36371/-36371 | 317933/316288 | 0 | 11.03/10.99 | 4161 |
| TL3_TK_C17 | T|f30|t50_with|press|ALL|nypm | HOLD | 30 | 0.0 | 92044/92044 | -55145/-55145 | 338476/340478 | 0 | 10.68/10.66 | 7436 |
| TL3_TK_C18 | T|f30|t50_with_hold|hold|K7|rth | L3M | 261 | 0.0 | 52233/52233 | -36371/-36371 | 243880/241079 | 0 | 10.35/10.35 | 1873 |
| TL3_TK_C18 | T|f30|t50_with_hold|hold|K7|rth | L6M | 246 | 0.0 | 52233/52233 | -36371/-36371 | 323257/316288 | 0 | 10.99/10.99 | 4168 |
| TL3_TK_C18 | T|f30|t50_with_hold|hold|K7|rth | HOLD | 188 | 0.0 | 92044/92044 | -55145/-55145 | 345456/340478 | 0 | 10.66/10.66 | 7449 |
| TL3_TK_C18 | T|f30|t50_with_hold|hold|K7|rth | PRE | 175 | -0.9 | 93048/92243 | -52547/-52547 | 314685/311185 | 0 | 9.44/9.43 | 7510 |
| TL3_TK_C18 | T|f30|t50_with_hold|hold|K7|rth | XP | -38 | 0.0 | 76154/76154 | -21663/-21663 | 189332/189332 | 0 | 10.82/10.82 | 3148 |
| TL3_TK_C19 | T|f60|t67_with|press|ALL|rth | L3M | 358 | 0.0 | 52233/52233 | -36371/-36371 | 246700/241079 | 0 | 10.35/10.35 | 1876 |
| TL3_TK_C19 | T|f60|t67_with|press|ALL|rth | L6M | 73 | 0.0 | 52233/52233 | -36371/-36371 | 315227/316288 | 0 | 10.99/10.99 | 4158 |
| TL3_TK_C19 | T|f60|t67_with|press|ALL|rth | HOLD | -98 | 0.0 | 92044/92044 | -55145/-55145 | 338384/340478 | 0 | 10.64/10.66 | 7434 |
| TL3_TK_C20 | C|cday|>=q90|press|P7|asia | L3M | 1000 | 0.0 | 52233/52233 | -36371/-36371 | 246643/241079 | 0 | 10.27/10.35 | 1860 |
| TL3_TK_C20 | C|cday|>=q90|press|P7|asia | L6M | 559 | 0.0 | 52233/52233 | -36371/-36371 | 322292/316288 | 0 | 10.99/10.99 | 4152 |
| TL3_TK_C20 | C|cday|>=q90|press|P7|asia | HOLD | 730 | 12.8 | 80276/92044 | -65746/-55145 | 346482/340478 | 0 | 10.64/10.66 | 7420 |
| TL3_TK_C20 | C|cday|>=q90|press|P7|asia | PRE | 239 | 0.0 | 92243/92243 | -52547/-52547 | 306616/311185 | 1 | 9.41/9.43 | 7486 |
| TL3_TK_C20 | C|cday|>=q90|press|P7|asia | XP | 284 | 5.2 | 72162/76154 | -20807/-21663 | 197342/189332 | 2 | 10.80/10.82 | 3133 |
| TL3_TK_C21 | C|cday|>=q67|press|H7|night | L3M | -364 | 2.3 | 51034/52233 | -35172/-36371 | 241082/241079 | 0 | 10.35/10.35 | 1881 |
| TL3_TK_C21 | C|cday|>=q67|press|H7|night | L6M | -179 | 2.3 | 51034/52233 | -35172/-36371 | 317380/316288 | 0 | 10.99/10.99 | 4178 |
| TL3_TK_C22 | C|cday|>=q67|press|H7|asia | L3M | -364 | 2.3 | 51034/52233 | -35172/-36371 | 241082/241079 | 0 | 10.35/10.35 | 1881 |
| TL3_TK_C22 | C|cday|>=q67|press|H7|asia | L6M | -179 | 2.3 | 51034/52233 | -35172/-36371 | 317380/316288 | 0 | 10.99/10.99 | 4178 |
| TL3_TK_C23 | C|cf30|<=q10|skip|K7|asia | L3M | 635 | 0.0 | 52233/52233 | -36371/-36371 | 249126/241079 | 0 | 10.35/10.35 | 1869 |
| TL3_TK_C23 | C|cf30|<=q10|skip|K7|asia | L6M | 222 | 0.0 | 52233/52233 | -36371/-36371 | 311510/316288 | 0 | 11.03/10.99 | 4161 |
| TL3_TK_C23 | C|cf30|<=q10|skip|K7|asia | HOLD | -75 | 0.0 | 92044/92044 | -55145/-55145 | 340478/340478 | 1 | 10.68/10.66 | 7428 |
| TL3_TK_C24 | C|cf30|<=q10|half|K7|asia | L3M | 25 | 0.0 | 52233/52233 | -36371/-36371 | 241079/241079 | 0 | 10.35/10.35 | 1876 |
| TL3_TK_C24 | C|cf30|<=q10|half|K7|asia | L6M | -270 | 0.0 | 52233/52233 | -36371/-36371 | 308864/316288 | 0 | 10.99/10.99 | 4168 |
| TL3_TK_C25 | X|Z_flat_against_m30|K7P7 | L3M | -75 | 0.0 | 52233/52233 | -36371/-36371 | 243317/241079 | 0 | 10.35/10.35 | 1882 |
| TL3_TK_C25 | X|Z_flat_against_m30|K7P7 | L6M | -189 | 0.0 | 52233/52233 | -36371/-36371 | 317070/316288 | 0 | 10.99/10.99 | 4177 |
| TL3_TK_C26 | X|Z_both_against_m30|ALL | L3M | 154 | 0.0 | 52233/52233 | -36371/-36371 | 243195/241079 | 0 | 10.20/10.35 | 1882 |
| TL3_TK_C26 | X|Z_both_against_m30|ALL | L6M | -111 | 0.0 | 52233/52233 | -36371/-36371 | 319134/316288 | 0 | 10.77/10.99 | 4178 |
| TL3_TK_C27 | X|Z_flat_against_p30|K7P7 | L3M | 79 | 0.1 | 52181/52233 | -36318/-36371 | 243984/241079 | 0 | 10.35/10.35 | 1881 |
| TL3_TK_C27 | X|Z_flat_against_p30|K7P7 | L6M | 2 | 0.1 | 52181/52233 | -36318/-36371 | 319029/316288 | 0 | 10.99/10.99 | 4176 |
| TL3_TK_C27 | X|Z_flat_against_p30|K7P7 | HOLD | 129 | -2.0 | 93874/92044 | -55145/-55145 | 346631/340478 | 0 | 10.66/10.66 | 7474 |
| TL3_TK_C28 | X|H_both_m30q67|ALL | L3M | -787 | 0.0 | 52233/52233 | -36371/-36371 | 237662/241079 | 0 | 11.03/10.35 | 1867 |
| TL3_TK_C28 | X|H_both_m30q67|ALL | L6M | -509 | 0.0 | 52233/52233 | -36371/-36371 | 316702/316288 | 0 | 12.40/10.99 | 4155 |
| TL3_TK_C29 | X|TP_1000_f50|ALL | L3M | 0 | 0.0 | 52233/52233 | -36371/-36371 | 241079/241079 | 0 | 10.35/10.35 | 1875 |
| TL3_TK_C29 | X|TP_1000_f50|ALL | L6M | 0 | 0.0 | 52233/52233 | -36371/-36371 | 316288/316288 | 0 | 10.99/10.99 | 4169 |
| TL3_TK_C29 | X|TP_1000_f50|ALL | HOLD | 0 | 0.0 | 92044/92044 | -55145/-55145 | 340478/340478 | 0 | 10.66/10.66 | 7452 |
| TL3_TK_C30 | X|TP_800_f30|ALL | L3M | -23 | 0.0 | 52233/52233 | -36371/-36371 | 241560/241079 | 0 | 10.35/10.35 | 1876 |
| TL3_TK_C30 | X|TP_800_f30|ALL | L6M | -11 | 0.0 | 52233/52233 | -36371/-36371 | 316288/316288 | 0 | 10.99/10.99 | 4170 |
| TL3_TK_C30 | X|TP_800_f30|ALL | HOLD | 47 | 0.0 | 92044/92044 | -55145/-55145 | 340478/340478 | 0 | 10.66/10.66 | 7455 |
| TL3_TK_C30 | X|TP_800_f30|ALL | PRE | -240 | -0.4 | 92633/92243 | -52937/-52547 | 306579/311185 | 0 | 9.33/9.43 | 7591 |
| TL3_TK_C30 | X|TP_800_f30|ALL | XP | -68 | -22.2 | 93087/76154 | -25576/-21663 | 191612/189332 | 2 | 10.77/10.82 | 3259 |
| TL3_TK_C31 | X|TP_1000_f70|ALL | L3M | 0 | 0.0 | 52233/52233 | -36371/-36371 | 241079/241079 | 0 | 10.35/10.35 | 1875 |
| TL3_TK_C31 | X|TP_1000_f70|ALL | L6M | 0 | 0.0 | 52233/52233 | -36371/-36371 | 316288/316288 | 0 | 10.99/10.99 | 4169 |
| TL3_TK_C31 | X|TP_1000_f70|ALL | HOLD | 0 | 0.0 | 92044/92044 | -55145/-55145 | 340478/340478 | 0 | 10.66/10.66 | 7452 |
| TL3_TK_C32 | X|L_m30q80_km15|ALL | L3M | 0 | 0.0 | 52233/52233 | -36371/-36371 | 241079/241079 | 0 | 10.35/10.35 | 1875 |
| TL3_TK_C32 | X|L_m30q80_km15|ALL | L6M | 0 | 0.0 | 52233/52233 | -36371/-36371 | 316288/316288 | 0 | 10.99/10.99 | 4169 |
| TL3_TK_C32 | X|L_m30q80_km15|ALL | HOLD | -5 | 0.0 | 92044/92044 | -55145/-55145 | 340478/340478 | 0 | 10.66/10.66 | 7452 |
| TL3_TK_C33 | X|T30_t50_full|ALL | L3M | -525 | 0.0 | 52233/52233 | -36371/-36371 | 238765/241079 | 1 | 10.73/10.35 | 1840 |
| TL3_TK_C33 | X|T30_t50_full|ALL | L6M | -563 | 0.0 | 52233/52233 | -36371/-36371 | 314925/316288 | 1 | 11.30/10.99 | 4071 |
| TL3_TK_C34 | X|T60_t50_full|ALL | L3M | -1780 | 0.0 | 52233/52233 | -36371/-36371 | 229417/241079 | 0 | 10.50/10.35 | 1844 |
| TL3_TK_C34 | X|T60_t50_full|ALL | L6M | -561 | 0.0 | 52233/52233 | -36371/-36371 | 311783/316288 | 0 | 11.11/10.99 | 4104 |
| TL3_TK_C35 | X|T30_t67_relax|ALL | L3M | 0 | 0.0 | 52233/52233 | -36371/-36371 | 241079/241079 | 0 | 10.35/10.35 | 1875 |
| TL3_TK_C35 | X|T30_t67_relax|ALL | L6M | 0 | 0.0 | 52233/52233 | -36371/-36371 | 316288/316288 | 0 | 10.99/10.99 | 4169 |
| TL3_TK_C35 | X|T30_t67_relax|ALL | HOLD | 0 | 0.0 | 92044/92044 | -55145/-55145 | 340478/340478 | 0 | 10.66/10.66 | 7452 |
| TL3_TK_C36 | X|T30_t67_widen|ALL | L3M | -430 | 0.0 | 52233/52233 | -36371/-36371 | 238942/241079 | 0 | 10.42/10.35 | 1874 |
| TL3_TK_C36 | X|T30_t67_widen|ALL | L6M | 2 | 0.0 | 52233/52233 | -36371/-36371 | 320806/316288 | 0 | 11.03/10.99 | 4164 |
| TL3_TK_C36 | X|T30_t67_widen|ALL | HOLD | 24 | 0.0 | 92044/92044 | -55145/-55145 | 341980/340478 | 0 | 10.70/10.66 | 7438 |
| TL3_TK_C37 | R|m15|<=q50|skip|ALL|nyam | L3M | -641 | -0.9 | 52720/52233 | -36857/-36371 | 234660/241079 | 0 | 10.35/10.35 | 1810 |
| TL3_TK_C37 | R|m15|<=q50|skip|ALL|nyam | L6M | -581 | -0.9 | 52720/52233 | -36857/-36371 | 313378/316288 | 0 | 10.99/10.99 | 4017 |
| TL3_TK_C38 | R|m30|<=q50|skip|ALL|rth | L3M | 399 | -2.4 | 53479/52233 | -37617/-36371 | 244431/241079 | 0 | 10.35/10.35 | 1806 |
| TL3_TK_C38 | R|m30|<=q50|skip|ALL|rth | L6M | -1 | -2.4 | 53479/52233 | -37617/-36371 | 314912/316288 | 0 | 10.99/10.99 | 3998 |
| TL3_TK_C39 | R|cs30|<=q50|skip|ALL|rth | L3M | -407 | 1.4 | 51521/52233 | -35658/-36371 | 237267/241079 | 0 | 10.42/10.35 | 1809 |
| TL3_TK_C39 | R|cs30|<=q50|skip|ALL|rth | L6M | -254 | 1.4 | 51521/52233 | -35658/-36371 | 314912/316288 | 0 | 11.03/10.99 | 4005 |

### Placebos (TICK shifted 11/23/37 trading days) and delays (1/5/15 min) of advanced cells, L6M and HOLD windows

| cell | variant | window | d mean | maxDD cut % | ww cell/ref |
|---|---|---|---|---|---|
| TL3_TK_C06 | P11 | L6M | -2484 | -4.9 | -37970/-36371 |
| TL3_TK_C06 | P11 | HOLD | -1315 | 5.1 | -55210/-55145 |
| TL3_TK_C06 | P23 | L6M | -1435 | 16.7 | -25313/-36371 |
| TL3_TK_C06 | P23 | HOLD | -888 | -19.0 | -52541/-55145 |
| TL3_TK_C06 | P37 | L6M | -2554 | 1.3 | -35678/-36371 |
| TL3_TK_C06 | P37 | HOLD | -1442 | 8.5 | -42804/-55145 |
| TL3_TK_C06 | D1 | L6M | 1594 | 20.3 | -25779/-36371 |
| TL3_TK_C06 | D1 | HOLD | 1283 | 14.7 | -44188/-55145 |
| TL3_TK_C06 | D5 | L6M | 1594 | 20.3 | -25779/-36371 |
| TL3_TK_C06 | D5 | HOLD | 1283 | 14.7 | -44188/-55145 |
| TL3_TK_C06 | D15 | L6M | 1594 | 20.3 | -25779/-36371 |
| TL3_TK_C06 | D15 | HOLD | 1283 | 14.7 | -44188/-55145 |
| TL3_TK_C20 | P11 | L6M | 1232 | -6.4 | -39701/-36371 |
| TL3_TK_C20 | P11 | HOLD | 678 | -1.2 | -55145/-55145 |
| TL3_TK_C20 | P23 | L6M | 440 | -6.4 | -39701/-36371 |
| TL3_TK_C20 | P23 | HOLD | 328 | -8.0 | -53928/-55145 |
| TL3_TK_C20 | P37 | L6M | -398 | -2.9 | -37883/-36371 |
| TL3_TK_C20 | P37 | HOLD | 256 | -8.0 | -51923/-55145 |
| TL3_TK_C20 | D1 | L6M | 559 | 0.0 | -36371/-36371 |
| TL3_TK_C20 | D1 | HOLD | 730 | 12.8 | -65746/-55145 |
| TL3_TK_C20 | D5 | L6M | 559 | 0.0 | -36371/-36371 |
| TL3_TK_C20 | D5 | HOLD | 730 | 12.8 | -65746/-55145 |
| TL3_TK_C20 | D15 | L6M | 559 | 0.0 | -36371/-36371 |
| TL3_TK_C20 | D15 | HOLD | 730 | 12.8 | -65746/-55145 |
| TL3_TK_C04 | P11 | L6M | -1178 | 0.0 | -36371/-36371 |
| TL3_TK_C04 | P11 | HOLD | -786 | 12.3 | -57261/-55145 |
| TL3_TK_C04 | P23 | L6M | -713 | 6.4 | -33042/-36371 |
| TL3_TK_C04 | P23 | HOLD | -288 | 13.7 | -63698/-55145 |
| TL3_TK_C04 | P37 | L6M | -1016 | 0.3 | -36189/-36371 |
| TL3_TK_C04 | P37 | HOLD | -632 | 16.4 | -51457/-55145 |
| TL3_TK_C04 | D1 | L6M | -45 | 6.4 | -33042/-36371 |
| TL3_TK_C04 | D1 | HOLD | -12 | 18.2 | -52133/-55145 |
| TL3_TK_C04 | D5 | L6M | -45 | 6.4 | -33042/-36371 |
| TL3_TK_C04 | D5 | HOLD | -12 | 18.2 | -52133/-55145 |
| TL3_TK_C04 | D15 | L6M | -45 | 6.4 | -33042/-36371 |
| TL3_TK_C04 | D15 | HOLD | -12 | 18.2 | -52133/-55145 |
| TL3_TK_C05 | P11 | L6M | -3670 | -13.8 | -42621/-36371 |
| TL3_TK_C05 | P11 | HOLD | -1470 | -0.3 | -54030/-55145 |
| TL3_TK_C05 | P23 | L6M | -1475 | 25.8 | -21911/-36371 |
| TL3_TK_C05 | P23 | HOLD | -616 | -12.6 | -43184/-55145 |
| TL3_TK_C05 | P37 | L6M | -1919 | 4.6 | -33993/-36371 |
| TL3_TK_C05 | P37 | HOLD | -396 | 7.3 | -33993/-55145 |
| TL3_TK_C05 | D1 | L6M | 1039 | 19.9 | -26026/-36371 |
| TL3_TK_C05 | D1 | HOLD | 740 | 8.5 | -46121/-55145 |
| TL3_TK_C05 | D5 | L6M | 1039 | 19.9 | -26026/-36371 |
| TL3_TK_C05 | D5 | HOLD | 740 | 8.5 | -46121/-55145 |
| TL3_TK_C05 | D15 | L6M | 1039 | 19.9 | -26026/-36371 |
| TL3_TK_C05 | D15 | HOLD | 740 | 8.5 | -46121/-55145 |
| TL3_TK_C07 | P11 | L6M | -316 | 0.0 | -36371/-36371 |
| TL3_TK_C07 | P11 | HOLD | 0 | 8.5 | -55145/-55145 |
| TL3_TK_C07 | P23 | L6M | -172 | 0.0 | -36371/-36371 |
| TL3_TK_C07 | P23 | HOLD | -190 | 10.5 | -55145/-55145 |
| TL3_TK_C07 | P37 | L6M | -437 | 0.0 | -36371/-36371 |
| TL3_TK_C07 | P37 | HOLD | -503 | 2.0 | -55145/-55145 |
| TL3_TK_C07 | D1 | L6M | 68 | 0.0 | -36371/-36371 |
| TL3_TK_C07 | D1 | HOLD | 92 | 2.5 | -55145/-55145 |
| TL3_TK_C07 | D5 | L6M | -181 | 0.0 | -36371/-36371 |
| TL3_TK_C07 | D5 | HOLD | -64 | 2.5 | -55145/-55145 |
| TL3_TK_C07 | D15 | L6M | -198 | 0.0 | -36371/-36371 |
| TL3_TK_C07 | D15 | HOLD | -75 | 6.8 | -55145/-55145 |
| TL3_TK_C09 | P11 | L6M | -316 | 0.0 | -36371/-36371 |
| TL3_TK_C09 | P11 | HOLD | 0 | 8.5 | -55145/-55145 |
| TL3_TK_C09 | P23 | L6M | -172 | 0.0 | -36371/-36371 |
| TL3_TK_C09 | P23 | HOLD | -190 | 10.5 | -55145/-55145 |
| TL3_TK_C09 | P37 | L6M | -437 | 0.0 | -36371/-36371 |
| TL3_TK_C09 | P37 | HOLD | -503 | 2.0 | -55145/-55145 |
| TL3_TK_C09 | D1 | L6M | 68 | 0.0 | -36371/-36371 |
| TL3_TK_C09 | D1 | HOLD | 92 | 2.5 | -55145/-55145 |
| TL3_TK_C09 | D5 | L6M | -181 | 0.0 | -36371/-36371 |
| TL3_TK_C09 | D5 | HOLD | -64 | 2.5 | -55145/-55145 |
| TL3_TK_C09 | D15 | L6M | -198 | 0.0 | -36371/-36371 |
| TL3_TK_C09 | D15 | HOLD | -75 | 6.8 | -55145/-55145 |
| TL3_TK_C18 | P11 | L6M | -134 | 0.0 | -36371/-36371 |
| TL3_TK_C18 | P11 | HOLD | -81 | 0.0 | -55145/-55145 |
| TL3_TK_C18 | P23 | L6M | 46 | 0.0 | -36371/-36371 |
| TL3_TK_C18 | P23 | HOLD | 44 | 0.0 | -55145/-55145 |
| TL3_TK_C18 | P37 | L6M | 53 | 0.0 | -36371/-36371 |
| TL3_TK_C18 | P37 | HOLD | -22 | -1.6 | -55145/-55145 |
| TL3_TK_C18 | D1 | L6M | 246 | 0.0 | -36371/-36371 |
| TL3_TK_C18 | D1 | HOLD | 188 | 0.0 | -55145/-55145 |
| TL3_TK_C18 | D5 | L6M | 246 | 0.0 | -36371/-36371 |
| TL3_TK_C18 | D5 | HOLD | 188 | 0.0 | -55145/-55145 |
| TL3_TK_C18 | D15 | L6M | 246 | 0.0 | -36371/-36371 |
| TL3_TK_C18 | D15 | HOLD | 188 | 0.0 | -55145/-55145 |
| TL3_TK_C10 | P11 | L6M | 54 | 0.0 | -36371/-36371 |
| TL3_TK_C10 | P11 | HOLD | 64 | 0.0 | -55145/-55145 |
| TL3_TK_C10 | P23 | L6M | -316 | 0.0 | -36371/-36371 |
| TL3_TK_C10 | P23 | HOLD | -208 | 0.0 | -55145/-55145 |
| TL3_TK_C10 | P37 | L6M | -29 | 0.0 | -36371/-36371 |
| TL3_TK_C10 | P37 | HOLD | 189 | 0.7 | -55145/-55145 |
| TL3_TK_C10 | D1 | L6M | 26 | 0.0 | -36371/-36371 |
| TL3_TK_C10 | D1 | HOLD | 44 | 0.7 | -55145/-55145 |
| TL3_TK_C10 | D5 | L6M | 26 | 0.0 | -36371/-36371 |
| TL3_TK_C10 | D5 | HOLD | 44 | 0.7 | -55145/-55145 |
| TL3_TK_C10 | D15 | L6M | 26 | 0.0 | -36371/-36371 |
| TL3_TK_C10 | D15 | HOLD | 44 | 0.7 | -55145/-55145 |
| TL3_TK_C30 | P11 | L6M | 15 | 0.0 | -36371/-36371 |
| TL3_TK_C30 | P11 | HOLD | -20 | 7.3 | -55145/-55145 |
| TL3_TK_C30 | P23 | L6M | 67 | 0.0 | -36371/-36371 |
| TL3_TK_C30 | P23 | HOLD | 83 | -0.9 | -55145/-55145 |
| TL3_TK_C30 | P37 | L6M | -33 | 0.0 | -36371/-36371 |
| TL3_TK_C30 | P37 | HOLD | -62 | 2.7 | -55145/-55145 |
| TL3_TK_C30 | D1 | L6M | -11 | 0.0 | -36371/-36371 |
| TL3_TK_C30 | D1 | HOLD | 76 | 0.0 | -55145/-55145 |
| TL3_TK_C30 | D5 | L6M | -57 | 0.0 | -36371/-36371 |
| TL3_TK_C30 | D5 | HOLD | -26 | 0.0 | -55145/-55145 |
| TL3_TK_C30 | D15 | L6M | 50 | 0.0 | -36371/-36371 |
| TL3_TK_C30 | D15 | HOLD | 50 | 0.0 | -55145/-55145 |
| TL3_TK_C16 | P11 | L6M | -366 | 0.0 | -36371/-36371 |
| TL3_TK_C16 | P11 | HOLD | -180 | -1.0 | -55145/-55145 |
| TL3_TK_C16 | P23 | L6M | -37 | 0.0 | -36371/-36371 |
| TL3_TK_C16 | P23 | HOLD | -179 | -1.0 | -55145/-55145 |
| TL3_TK_C16 | P37 | L6M | -111 | 0.0 | -36371/-36371 |
| TL3_TK_C16 | P37 | HOLD | -174 | 0.3 | -55145/-55145 |


## 5. Status



## 6. Delayed-TICK (real-time subscription) summary

See 3.D (first order) and section 4 (exact).


## 7. PART 3 new books (W-TK2): see autopilot/DS3_TICK_BOOKS.md

# DS3_TICK_BOOKS - new TICK books on NQ (W-TK2), research only, NO PASS claim. Built 2026-11-14 19:07 UTC

**VERDICT (plain):** Standalone NQ screen (5 books x 6 session units, 1,470-cell entry/stop/target/time grid, measured fills, real TICK vs TICK shifted 11/23/37 trading days): 9013 cells pass the both-window gate (L3M,L6M,HOLD,PRE,X' all > 0, enough trades) AND beat the same cell on the shifted-TICK placebos in recent and older windows; but these come from a 1.8M-cell search and only 2 of 22 book/unit families have a best cell above the best placebo-family cell, so the standalone evidence is WEAK (selection-dominated), and the literal directive book B1 at +/-1000 is too rare (<=20 trades/6 months) to pass any gate. 8 of 8 finalists have exact-engine L6M injected stack numbers so far; see section 4. Best injected L6M delta mean +865 $/wk (TL3_TKB_F3_real), max DD change -695.

**READING (W-TK2, updated 2026-11-14 after lead order; exact engine, JN05W2 base, all layers ON, 3 exact placebo draws per window for F2 and F6):** No TICK book is a lead by the user's rule; strength weak. Best is F2 = B2 follow persistent TICK (30-min mean >= +/-100, share>0 >= 0.6, onset trigger), NQ 10:00-12:00, confirm entry +3 min, 1x ATR stop, 30-pt target, 30-min time stop, both sides. Injected delta mean $/wk vs the three exact placebos (shifts 11/23/37): L3M +994 vs -967..+56; L6M +581 vs -563..-38; HOLD +454 vs -43..+80; PRE +125 vs -427..+16; X' +39 vs -410..+211 (BELOW two of three placebos). So F2 is above all three placebos in L3M, L6M, HOLD and PRE but NOT in X'. The gain is small outside the recent window (about 1% of the stack in PRE/X') and concentrated: best 5 weeks = 56% and best 4 months = 74% of the book's total profit; removing the -55.1k stack week (2026-06) changes nothing (+203 vs +202 $/wk), so the gain is independent of that week. Max DD is not improved (PRE +3,018, X' -6,696, recent unchanged; placebo DD changes range -1,289..+2,835 in PRE, -1,985..+142 in X', i.e. DD moves are within placebo noise). Delayed TICK (exact): L6M +368 (1 min) / +84 (5) / -446 (15); HOLD +345 / +345 / +33; PRE +383 / -55 / -155; X' -76 / +368 / (15 min incomplete): positive in recents at 1-5 min, not stable in older windows, fails at 15 min in L6M. Bi-weekly walk-forward over the whole grid (standalone harness) is NEGATIVE for the real F2 var (OOS mean -312 $/wk, DD 68.5k) and no better than shifted TICK (-229..+199): the cell choice does not survive walk-forward; best-of-grid on real TICK (recents 1,130, older 439) exceeds the shifted-TICK best-of (159-608; 107-445) only partly. F6 (B1 fade TICK extreme >= +/-600, 14:30-15:00): L3M +365, L6M +501, HOLD +260 vs placebos -79..+77, PRE -30 (placebos -330..-117, i.e. above them but negative), X' +89 (above -621..-166); 10 trades per 6 months, profit concentration > 100% of total (losing months exist); weak. The literal +/-1000 fade threshold has no gated cell; B4 none; F1, F3, F7 not TICK effects (placebo equal or higher). ES: standalone only, injection not possible (the hook adds an NQ book inside the NQ-only engine; an ES version is an engine change that was not attempted).

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

| set | window | coverage | weeks | ref_mean | inj_mean | d_mean | ref_dd | inj_dd | ref_worst | inj_worst | ref_stops_wk | inj_stops_wk | best5_kept | win_turned_losing | tkb_mean | tkb_n |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TL3_TKB_F1_pl11 | L3M | 0.8 | 11 | 16819.4 | 17439.8 | 620.4 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.5 | 1.0 | 0 | 620.4 | 5 |
| TL3_TKB_F1_pl11 | L6M | 0.9 | 25 | 23240.9 | 23892.1 | 651.3 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | 651.3 | 11 |
| TL3_TKB_F1_pl11 | HOLD | 0.5 | 27 | 24470.4 | 24907.2 | 436.8 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.9 | 1.0 | 0 | 436.8 | 14 |
| TL3_TKB_F1_pl23 | L3M | 0.8 | 11 | 16819.4 | 16958.9 | 139.4 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 139.4 | 1 |
| TL3_TKB_F1_pl23 | L6M | 0.9 | 25 | 23240.9 | 23740.8 | 499.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.5 | 1.0 | 0 | 497.3 | 7 |
| TL3_TKB_F1_pl23 | HOLD | 0.5 | 27 | 24470.4 | 24874.6 | 404.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.7 | 1.0 | 0 | 401.7 | 8 |
| TL3_TKB_F1_pl37 | L3M | 0.8 | 11 | 16819.4 | 17304.5 | 485.0 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 485.0 | 4 |
| TL3_TKB_F1_pl37 | L6M | 0.9 | 25 | 23240.9 | 23787.3 | 546.5 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | 543.8 | 12 |
| TL3_TKB_F1_pl37 | HOLD | 0.5 | 27 | 24470.4 | 24950.7 | 480.3 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.9 | 1.0 | 0 | 477.8 | 16 |
| TL3_TKB_F1_real | L3M | 0.8 | 11 | 16819.4 | 17083.4 | 264.0 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.5 | 1.0 | 0 | 264.0 | 5 |
| TL3_TKB_F1_real | L6M | 0.9 | 25 | 23240.9 | 23883.5 | 642.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.7 | 1.0 | 0 | 642.6 | 13 |
| TL3_TKB_F1_real | HOLD | 0.9 | 51 | 17639.8 | 17774.2 | 134.4 | 63185.1 | 64791.3 | -55145.4 | -55476.9 | 10.6 | 10.9 | 1.0 | 0 | 86.0 | 36 |
| TL3_TKB_F2_dly1 | L3M | 0.8 | 11 | 16819.4 | 17730.9 | 911.5 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.5 | 1.0 | 0 | 911.5 | 20 |
| TL3_TKB_F2_dly1 | L6M | 0.9 | 25 | 23240.9 | 23609.0 | 368.2 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.8 | 1.0 | 0 | 368.2 | 32 |
| TL3_TKB_F2_dly1 | HOLD | 0.9 | 51 | 17639.8 | 17984.5 | 344.7 | 63185.1 | 64091.3 | -55145.4 | -55145.4 | 10.6 | 11.1 | 1.0 | 0 | 238.4 | 82 |
| TL3_TKB_F2_dly1 | PRE | 1.0 | 75 | 10167.9 | 10550.6 | 382.7 | 76186.1 | 83734.4 | -52547.4 | -54814.5 | 9.3 | 10.2 | 1.0 | 0 | 384.1 | 203 |
| TL3_TKB_F2_dly1 | X' | 1.0 | 44 | 3585.1 | 3509.5 | -75.6 | 55325.6 | 44202.1 | -21663.5 | -20672.0 | 10.8 | 12.0 | 1.0 | 0 | -80.4 | 140 |
| TL3_TKB_F2_dly15 | L3M | 0.8 | 11 | 16819.4 | 15992.2 | -827.2 | 36370.5 | 39224.9 | -36370.5 | -36370.5 | 11.3 | 11.8 | 1.0 | 0 | -345.9 | 14 |
| TL3_TKB_F2_dly15 | L6M | 0.9 | 25 | 23240.9 | 22795.0 | -445.9 | 36370.5 | 39224.9 | -36370.5 | -36370.5 | 10.5 | 10.9 | 1.0 | 0 | -234.1 | 29 |
| TL3_TKB_F2_dly15 | HOLD | 0.9 | 51 | 17639.8 | 17673.2 | 33.4 | 63185.1 | 63185.1 | -55145.4 | -55145.4 | 10.6 | 11.0 | 1.0 | 0 | -20.4 | 65 |
| TL3_TKB_F2_dly15 | PRE | 1.0 | 75 | 10167.9 | 10012.6 | -155.2 | 76186.1 | 79081.7 | -52547.4 | -54307.1 | 9.3 | 10.3 | 1.0 | 0 | -97.8 | 187 |
| TL3_TKB_F2_dly15 | X' | 0.2 | 10 | 12420.7 | 12009.4 | -411.3 | 11071.0 | 10952.8 | -11071.0 | -10952.8 | 8.5 | 9.7 | 1.0 | 0 | -411.3 | 30 |
| TL3_TKB_F2_dly5 | L3M | 0.8 | 11 | 16819.4 | 16783.7 | -35.7 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 12.0 | 1.0 | 0 | -35.7 | 19 |
| TL3_TKB_F2_dly5 | L6M | 0.9 | 25 | 23240.9 | 23325.0 | 84.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 11.0 | 1.0 | 0 | 84.1 | 37 |
| TL3_TKB_F2_dly5 | HOLD | 0.9 | 51 | 17639.8 | 17984.5 | 344.7 | 63185.1 | 63432.5 | -55145.4 | -55145.4 | 10.6 | 11.0 | 1.0 | 0 | 309.5 | 77 |
| TL3_TKB_F2_dly5 | PRE | 1.0 | 75 | 10167.9 | 10113.0 | -54.9 | 76186.1 | 80236.1 | -52547.4 | -53135.6 | 9.3 | 10.3 | 1.0 | 1 | 45.3 | 203 |
| TL3_TKB_F2_dly5 | X' | 1.0 | 44 | 3585.1 | 3953.5 | 368.5 | 55325.6 | 47613.2 | -21663.5 | -20174.6 | 10.8 | 11.7 | 1.0 | 1 | 342.2 | 130 |
| TL3_TKB_F2_pl11 | L3M | 0.8 | 11 | 16819.4 | 16875.0 | 55.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.5 | 1.0 | 0 | 55.6 | 14 |
| TL3_TKB_F2_pl11 | L6M | 0.9 | 25 | 23240.9 | 23202.9 | -38.0 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.8 | 1.0 | 0 | 26.4 | 30 |
| TL3_TKB_F2_pl11 | HOLD | 0.9 | 51 | 17639.8 | 17720.0 | 80.2 | 63185.1 | 61982.5 | -55145.4 | -55145.4 | 10.6 | 11.1 | 1.0 | 0 | -14.9 | 80 |
| TL3_TKB_F2_pl11 | PRE | 1.0 | 75 | 10167.9 | 10107.8 | -60.1 | 76186.1 | 77365.5 | -52547.4 | -51930.9 | 9.3 | 10.1 | 1.0 | 0 | 26.8 | 164 |
| TL3_TKB_F2_pl11 | X' | 1.0 | 44 | 3585.1 | 3691.6 | 106.5 | 55325.6 | 53341.1 | -21663.5 | -25675.6 | 10.8 | 11.8 | 1.0 | 0 | 133.8 | 107 |
| TL3_TKB_F2_pl23 | L3M | 0.8 | 11 | 16819.4 | 15852.0 | -967.4 | 36370.5 | 38136.4 | -36370.5 | -36370.5 | 11.3 | 12.0 | 1.0 | 0 | -486.1 | 13 |
| TL3_TKB_F2_pl23 | L6M | 0.9 | 25 | 23240.9 | 22678.2 | -562.7 | 36370.5 | 38136.4 | -36370.5 | -36370.5 | 10.5 | 11.1 | 1.0 | 0 | -350.9 | 26 |
| TL3_TKB_F2_pl23 | HOLD | 0.9 | 51 | 17639.8 | 17641.7 | 1.9 | 63185.1 | 63078.6 | -55145.4 | -55145.4 | 10.6 | 11.1 | 1.0 | 0 | 27.9 | 74 |
| TL3_TKB_F2_pl23 | PRE | 1.0 | 75 | 10167.9 | 10183.6 | 15.7 | 76186.1 | 79020.9 | -52547.4 | -50643.3 | 9.3 | 10.0 | 1.0 | 0 | 70.7 | 165 |
| TL3_TKB_F2_pl23 | X' | 1.0 | 44 | 3585.1 | 3174.9 | -410.2 | 55325.6 | 53689.9 | -21663.5 | -25431.8 | 10.8 | 11.9 | 1.0 | 0 | -387.7 | 103 |
| TL3_TKB_F2_pl37 | L3M | 0.8 | 11 | 16819.4 | 16547.7 | -271.8 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.8 | 1.0 | 0 | -305.5 | 11 |
| TL3_TKB_F2_pl37 | L6M | 0.9 | 25 | 23240.9 | 22979.3 | -261.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 11.0 | 1.0 | 0 | -312.1 | 24 |
| TL3_TKB_F2_pl37 | HOLD | 0.9 | 51 | 17639.8 | 17597.0 | -42.9 | 63185.1 | 63185.1 | -55145.4 | -55145.4 | 10.6 | 11.1 | 1.0 | 0 | -121.1 | 62 |
| TL3_TKB_F2_pl37 | PRE | 1.0 | 75 | 10167.9 | 9740.8 | -427.1 | 76186.1 | 74896.7 | -52547.4 | -52361.8 | 9.3 | 10.3 | 1.0 | 0 | -346.1 | 168 |
| TL3_TKB_F2_pl37 | X' | 1.0 | 44 | 3585.1 | 3796.2 | 211.1 | 55325.6 | 55468.0 | -21663.5 | -21511.9 | 10.8 | 11.5 | 1.0 | 1 | 206.3 | 99 |
| TL3_TKB_F2_real | L3M | 0.8 | 11 | 16819.4 | 17813.8 | 994.4 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 994.4 | 14 |
| TL3_TKB_F2_real | L6M | 0.9 | 25 | 23240.9 | 23822.0 | 581.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | 581.1 | 26 |
| TL3_TKB_F2_real | HOLD | 0.9 | 51 | 17639.8 | 18093.4 | 453.6 | 63185.1 | 63185.1 | -55145.4 | -55145.4 | 10.6 | 10.9 | 1.0 | 0 | 375.3 | 67 |
| TL3_TKB_F2_real | PRE | 1.0 | 75 | 10167.9 | 10292.4 | 124.6 | 76186.1 | 79204.1 | -52547.4 | -53845.9 | 9.3 | 9.9 | 1.0 | 0 | 210.3 | 151 |
| TL3_TKB_F2_real | X' | 1.0 | 44 | 3585.1 | 3624.1 | 39.0 | 55325.6 | 48629.9 | -21663.5 | -22042.3 | 10.8 | 11.8 | 1.0 | 1 | 12.8 | 116 |
| TL3_TKB_F3_pl11 | L3M | 0.8 | 11 | 16819.4 | 17097.2 | 277.7 | 36370.5 | 36184.8 | -36370.5 | -36184.8 | 11.3 | 12.2 | 1.0 | 0 | 747.9 | 20 |
| TL3_TKB_F3_pl11 | L6M | 0.9 | 25 | 23240.9 | 23750.8 | 510.0 | 36370.5 | 36184.8 | -36370.5 | -36184.8 | 10.5 | 11.6 | 1.0 | 0 | 701.9 | 49 |
| TL3_TKB_F3_pl11 | HOLD | 0.5 | 27 | 24470.4 | 24988.6 | 518.1 | 36370.5 | 36184.8 | -36370.5 | -36184.8 | 10.7 | 11.8 | 1.0 | 0 | 695.8 | 53 |
| TL3_TKB_F3_pl23 | L3M | 0.8 | 11 | 16819.4 | 16315.2 | -504.3 | 36370.5 | 36731.4 | -36370.5 | -36370.5 | 11.3 | 12.3 | 1.0 | 0 | 86.0 | 20 |
| TL3_TKB_F3_pl23 | L6M | 0.9 | 25 | 23240.9 | 23111.0 | -129.8 | 36370.5 | 36731.4 | -36370.5 | -36370.5 | 10.5 | 11.6 | 1.0 | 0 | -120.6 | 46 |
| TL3_TKB_F3_pl23 | HOLD | 0.5 | 27 | 24470.4 | 24108.8 | -361.6 | 36370.5 | 36731.4 | -36370.5 | -36370.5 | 10.7 | 12.0 | 1.0 | 0 | -353.1 | 53 |
| TL3_TKB_F3_pl37 | L3M | 0.8 | 11 | 16819.4 | 18597.9 | 1778.5 | 36370.5 | 30351.0 | -36370.5 | -30351.0 | 11.3 | 12.1 | 1.0 | 0 | 1658.3 | 20 |
| TL3_TKB_F3_pl37 | L6M | 0.9 | 25 | 23240.9 | 25535.4 | 2294.6 | 36370.5 | 30351.0 | -36370.5 | -30351.0 | 10.5 | 11.3 | 1.1 | 0 | 1991.2 | 46 |
| TL3_TKB_F3_pl37 | HOLD | 0.5 | 27 | 24470.4 | 26631.8 | 2161.4 | 36370.5 | 30351.0 | -36370.5 | -30351.0 | 10.7 | 11.5 | 1.1 | 0 | 1880.5 | 51 |
| TL3_TKB_F3_real | L3M | 0.8 | 11 | 16819.4 | 16870.2 | 50.7 | 36370.5 | 35675.2 | -36370.5 | -30876.5 | 11.3 | 12.2 | 1.0 | 0 | 641.0 | 20 |
| TL3_TKB_F3_real | L6M | 0.9 | 25 | 23240.9 | 24105.7 | 864.8 | 36370.5 | 35675.2 | -36370.5 | -30876.5 | 10.5 | 11.3 | 1.0 | 0 | 1017.8 | 39 |
| TL3_TKB_F3_real | HOLD | 0.9 | 51 | 17639.8 | 18079.8 | 440.0 | 63185.1 | 63185.1 | -55145.4 | -55741.9 | 10.6 | 11.7 | 1.0 | 0 | 494.0 | 95 |
| TL3_TKB_F3_real | PRE | 1.0 | 75 | 10167.9 | 10019.0 | -148.9 | 76186.1 | 82524.3 | -52547.4 | -52547.4 | 9.3 | 10.5 | 1.0 | 0 | -83.3 | 157 |
| TL3_TKB_F4_real | L3M | 0.8 | 11 | 16819.4 | 16938.2 | 118.8 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 118.8 | 3 |
| TL3_TKB_F4_real | L6M | 0.9 | 25 | 23240.9 | 23525.4 | 284.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.5 | 1.0 | 0 | 284.6 | 9 |
| TL3_TKB_F4_real | HOLD | 0.5 | 27 | 24470.4 | 24733.9 | 263.5 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.7 | 1.0 | 0 | 263.5 | 9 |
| TL3_TKB_F5_real | L3M | 0.8 | 11 | 16819.4 | 16789.5 | -29.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.6 | 1.0 | 0 | -29.9 | 14 |
| TL3_TKB_F5_real | L6M | 0.9 | 25 | 23240.9 | 23103.6 | -137.3 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.9 | 1.0 | 0 | -137.3 | 25 |
| TL3_TKB_F5_real | HOLD | 0.5 | 27 | 24470.4 | 24471.0 | 0.5 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 11.0 | 1.0 | 0 | 0.5 | 28 |
| TL3_TKB_F6_dly1 | L3M | 0.8 | 11 | 16819.4 | 16854.6 | 35.2 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.4 | 1.0 | 0 | 35.2 | 4 |
| TL3_TKB_F6_dly1 | L6M | 0.9 | 25 | 23240.9 | 23323.9 | 83.0 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.7 | 1.0 | 0 | 83.0 | 11 |
| TL3_TKB_F6_dly1 | HOLD | 0.9 | 51 | 17639.8 | 17695.5 | 55.7 | 63185.1 | 60034.8 | -55145.4 | -55145.4 | 10.6 | 10.9 | 1.0 | 0 | 55.7 | 33 |
| TL3_TKB_F6_dly1 | PRE | 1.0 | 75 | 10167.9 | 10167.3 | -0.6 | 76186.1 | 77892.6 | -52547.4 | -52547.4 | 9.3 | 9.7 | 1.0 | 0 | 15.4 | 135 |
| TL3_TKB_F6_dly1 | X' | 1.0 | 44 | 3585.1 | 3509.1 | -76.0 | 55325.6 | 55490.4 | -21663.5 | -21964.4 | 10.8 | 11.7 | 1.0 | 1 | -76.0 | 139 |
| TL3_TKB_F6_dly15 | L3M | 0.8 | 11 | 16819.4 | 16716.7 | -102.7 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | -102.7 | 3 |
| TL3_TKB_F6_dly15 | L6M | 0.9 | 25 | 23240.9 | 23288.0 | 47.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.5 | 1.0 | 0 | 47.1 | 7 |
| TL3_TKB_F6_dly15 | HOLD | 0.9 | 51 | 17639.8 | 17724.4 | 84.6 | 63185.1 | 62273.4 | -55145.4 | -55145.4 | 10.6 | 10.7 | 1.0 | 0 | 84.6 | 30 |
| TL3_TKB_F6_dly15 | PRE | 1.0 | 75 | 10167.9 | 10061.2 | -106.7 | 76186.1 | 74337.6 | -52547.4 | -53832.1 | 9.3 | 9.9 | 1.0 | 0 | -90.7 | 140 |
| TL3_TKB_F6_dly5 | L3M | 0.8 | 11 | 16819.4 | 16871.0 | 51.5 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.4 | 1.0 | 0 | 51.5 | 4 |
| TL3_TKB_F6_dly5 | L6M | 0.9 | 25 | 23240.9 | 23493.6 | 252.7 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | 252.7 | 9 |
| TL3_TKB_F6_dly5 | HOLD | 0.9 | 51 | 17639.8 | 17738.0 | 98.2 | 63185.1 | 59819.8 | -55145.4 | -55145.4 | 10.6 | 10.8 | 1.0 | 0 | 98.2 | 26 |
| TL3_TKB_F6_dly5 | PRE | 1.0 | 75 | 10167.9 | 10046.0 | -121.9 | 76186.1 | 71555.3 | -52547.4 | -52547.4 | 9.3 | 9.8 | 1.0 | 0 | -105.9 | 131 |
| TL3_TKB_F6_dly5 | X' | 1.0 | 44 | 3585.1 | 3483.7 | -101.3 | 55325.6 | 62938.9 | -21663.5 | -24824.7 | 10.8 | 11.8 | 1.0 | 1 | -101.3 | 137 |
| TL3_TKB_F6_pl11 | L3M | 0.8 | 11 | 16819.4 | 16864.6 | 45.1 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 45.1 | 2 |
| TL3_TKB_F6_pl11 | L6M | 0.9 | 25 | 23240.9 | 23216.0 | -24.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | -24.9 | 8 |
| TL3_TKB_F6_pl11 | HOLD | 0.9 | 51 | 17639.8 | 17716.9 | 77.1 | 63185.1 | 62554.8 | -55145.4 | -55145.4 | 10.6 | 10.7 | 1.0 | 0 | 77.1 | 38 |
| TL3_TKB_F6_pl11 | PRE | 1.0 | 75 | 10167.9 | 9889.8 | -278.1 | 76186.1 | 75899.3 | -52547.4 | -52260.6 | 9.3 | 9.9 | 1.0 | 0 | -262.2 | 144 |
| TL3_TKB_F6_pl11 | X' | 1.0 | 44 | 3585.1 | 3161.0 | -424.1 | 55325.6 | 51359.2 | -21663.5 | -21950.6 | 10.8 | 11.7 | 1.0 | 0 | -424.1 | 127 |
| TL3_TKB_F6_pl23 | L3M | 0.8 | 11 | 16819.4 | 16776.6 | -42.9 | 36370.5 | 37284.1 | -36370.5 | -37284.1 | 11.3 | 11.4 | 1.0 | 0 | -42.9 | 5 |
| TL3_TKB_F6_pl23 | L6M | 0.9 | 25 | 23240.9 | 23301.5 | 60.7 | 36370.5 | 37284.1 | -36370.5 | -37284.1 | 10.5 | 10.6 | 1.0 | 0 | 60.7 | 10 |
| TL3_TKB_F6_pl23 | HOLD | 0.9 | 51 | 17639.8 | 17560.9 | -78.9 | 63185.1 | 63185.1 | -55145.4 | -55145.4 | 10.6 | 10.7 | 1.0 | 0 | -78.9 | 41 |
| TL3_TKB_F6_pl23 | PRE | 1.0 | 75 | 10167.9 | 9838.1 | -329.8 | 76186.1 | 78952.9 | -52547.4 | -53854.5 | 9.3 | 9.9 | 1.0 | 0 | -329.8 | 149 |
| TL3_TKB_F6_pl23 | X' | 1.0 | 44 | 3585.1 | 3418.7 | -166.4 | 55325.6 | 55048.5 | -21663.5 | -21157.0 | 10.8 | 11.6 | 1.0 | 1 | -171.2 | 124 |
| TL3_TKB_F6_pl37 | L3M | 0.8 | 11 | 16819.4 | 16946.3 | 126.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.4 | 1.0 | 0 | 126.9 | 3 |
| TL3_TKB_F6_pl37 | L6M | 0.9 | 25 | 23240.9 | 23226.2 | -14.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | -14.6 | 9 |
| TL3_TKB_F6_pl37 | HOLD | 0.9 | 51 | 17639.8 | 17715.6 | 75.8 | 63185.1 | 63124.8 | -55145.4 | -55145.4 | 10.6 | 10.7 | 1.0 | 0 | 75.8 | 46 |
| TL3_TKB_F6_pl37 | PRE | 1.0 | 75 | 10167.9 | 10051.0 | -116.8 | 76186.1 | 75196.7 | -52547.4 | -52547.4 | 9.3 | 9.8 | 1.0 | 0 | -116.8 | 149 |
| TL3_TKB_F6_pl37 | X' | 1.0 | 44 | 3585.1 | 2963.6 | -621.4 | 55325.6 | 56685.8 | -21663.5 | -21823.1 | 10.8 | 11.6 | 1.0 | 2 | -626.2 | 111 |
| TL3_TKB_F6_real | L3M | 0.8 | 11 | 16819.4 | 17184.0 | 364.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.3 | 1.0 | 0 | 364.6 | 4 |
| TL3_TKB_F6_real | L6M | 0.9 | 25 | 23240.9 | 23742.0 | 501.2 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.6 | 1.0 | 0 | 501.2 | 10 |
| TL3_TKB_F6_real | HOLD | 0.9 | 51 | 17639.8 | 17899.5 | 259.7 | 63185.1 | 60986.0 | -55145.4 | -55145.4 | 10.6 | 10.8 | 1.0 | 0 | 259.7 | 31 |
| TL3_TKB_F6_real | PRE | 1.0 | 75 | 10167.9 | 10137.7 | -30.2 | 76186.1 | 78132.3 | -52547.4 | -52547.4 | 9.3 | 9.8 | 1.0 | 0 | -14.2 | 137 |
| TL3_TKB_F6_real | X' | 1.0 | 44 | 3585.1 | 3674.4 | 89.3 | 55325.6 | 53121.3 | -21663.5 | -21759.4 | 10.8 | 11.6 | 1.0 | 0 | 89.3 | 140 |
| TL3_TKB_F7_pl11 | L3M | 0.8 | 11 | 16819.4 | 17068.5 | 249.1 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 11.3 | 11.5 | 1.0 | 0 | 249.1 | 17 |
| TL3_TKB_F7_pl11 | L6M | 0.9 | 25 | 23240.9 | 23689.4 | 448.5 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.5 | 10.8 | 1.0 | 0 | 448.5 | 40 |
| TL3_TKB_F7_pl11 | HOLD | 0.5 | 27 | 24470.4 | 24820.5 | 350.0 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.7 | 11.0 | 1.0 | 0 | 350.0 | 46 |
| TL3_TKB_F7_pl23 | L3M | 0.8 | 11 | 16819.4 | 17068.5 | 249.1 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 11.3 | 11.5 | 1.0 | 0 | 249.1 | 17 |
| TL3_TKB_F7_pl23 | L6M | 0.9 | 25 | 23240.9 | 23689.4 | 448.5 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.5 | 10.8 | 1.0 | 0 | 448.5 | 40 |
| TL3_TKB_F7_pl23 | HOLD | 0.5 | 27 | 24470.4 | 24820.5 | 350.0 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.7 | 11.0 | 1.0 | 0 | 350.0 | 46 |
| TL3_TKB_F7_pl37 | L3M | 0.8 | 11 | 16819.4 | 17068.5 | 249.1 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 11.3 | 11.5 | 1.0 | 0 | 249.1 | 17 |
| TL3_TKB_F7_pl37 | L6M | 0.9 | 25 | 23240.9 | 23737.0 | 496.2 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.5 | 10.7 | 1.0 | 0 | 496.2 | 39 |
| TL3_TKB_F7_pl37 | HOLD | 0.5 | 27 | 24470.4 | 24864.6 | 394.1 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.7 | 11.0 | 1.0 | 0 | 394.1 | 45 |
| TL3_TKB_F7_real | L3M | 0.8 | 11 | 16819.4 | 17177.7 | 358.3 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 11.3 | 11.5 | 1.0 | 0 | 358.3 | 16 |
| TL3_TKB_F7_real | L6M | 0.9 | 25 | 23240.9 | 23784.1 | 543.2 | 36370.5 | 37561.7 | -36370.5 | -37561.7 | 10.5 | 10.7 | 1.0 | 0 | 543.2 | 38 |
| TL3_TKB_F7_real | HOLD | 0.9 | 51 | 17639.8 | 17703.2 | 63.4 | 63185.1 | 63787.5 | -55145.4 | -55145.4 | 10.6 | 11.0 | 1.0 | 0 | 115.3 | 84 |
| TL3_TKB_F8_real | L3M | 0.8 | 11 | 16819.4 | 16883.1 | 63.6 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 11.3 | 11.4 | 1.0 | 0 | -20.6 | 6 |
| TL3_TKB_F8_real | L6M | 0.9 | 25 | 23240.9 | 23096.9 | -143.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.5 | 10.7 | 1.0 | 0 | -216.7 | 15 |
| TL3_TKB_F8_real | HOLD | 0.5 | 27 | 24470.4 | 24301.5 | -168.9 | 36370.5 | 36370.5 | -36370.5 | -36370.5 | 10.7 | 10.9 | 1.0 | 0 | -236.3 | 17 |


### Injected delta mean $/wk: real vs exact placebos (TICK shifted 11/23/37 trading days through the same engine)

| name | window | dly1 | dly15 | dly5 | pl11 | pl23 | pl37 | real |
|---|---|---|---|---|---|---|---|---|
| F1 | HOLD |  |  |  | 437.0 | 404.0 | 480.0 | 134.0 |
| F1 | L3M |  |  |  | 620.0 | 139.0 | 485.0 | 264.0 |
| F1 | L6M |  |  |  | 651.0 | 500.0 | 546.0 | 643.0 |
| F2 | HOLD | 345.0 | 33.0 | 345.0 | 80.0 | 2.0 | -43.0 | 454.0 |
| F2 | L3M | 911.0 | -827.0 | -36.0 | 56.0 | -967.0 | -272.0 | 994.0 |
| F2 | L6M | 368.0 | -446.0 | 84.0 | -38.0 | -563.0 | -262.0 | 581.0 |
| F2 | PRE | 383.0 | -155.0 | -55.0 | -60.0 | 16.0 | -427.0 | 125.0 |
| F2 | X' | -76.0 | -411.0 | 368.0 | 107.0 | -410.0 | 211.0 | 39.0 |
| F3 | HOLD |  |  |  | 518.0 | -362.0 | 2161.0 | 440.0 |
| F3 | L3M |  |  |  | 278.0 | -504.0 | 1778.0 | 51.0 |
| F3 | L6M |  |  |  | 510.0 | -130.0 | 2295.0 | 865.0 |
| F3 | PRE |  |  |  |  |  |  | -149.0 |
| F4 | HOLD |  |  |  |  |  |  | 263.0 |
| F4 | L3M |  |  |  |  |  |  | 119.0 |
| F4 | L6M |  |  |  |  |  |  | 285.0 |
| F5 | HOLD |  |  |  |  |  |  | 1.0 |
| F5 | L3M |  |  |  |  |  |  | -30.0 |
| F5 | L6M |  |  |  |  |  |  | -137.0 |
| F6 | HOLD | 56.0 | 85.0 | 98.0 | 77.0 | -79.0 | 76.0 | 260.0 |
| F6 | L3M | 35.0 | -103.0 | 52.0 | 45.0 | -43.0 | 127.0 | 365.0 |
| F6 | L6M | 83.0 | 47.0 | 253.0 | -25.0 | 61.0 | -15.0 | 501.0 |
| F6 | PRE | -1.0 | -107.0 | -122.0 | -278.0 | -330.0 | -117.0 | -30.0 |
| F6 | X' | -76.0 |  | -101.0 | -424.0 | -166.0 | -621.0 | 89.0 |
| F7 | HOLD |  |  |  | 350.0 | 350.0 | 394.0 | 63.0 |
| F7 | L3M |  |  |  | 249.0 | 249.0 | 249.0 | 358.0 |
| F7 | L6M |  |  |  | 449.0 | 449.0 | 496.0 | 543.0 |
| F8 | HOLD |  |  |  |  |  |  | -169.0 |
| F8 | L3M |  |  |  |  |  |  | 64.0 |
| F8 | L6M |  |  |  |  |  |  | -144.0 |


### Injected max-DD change $ (inj - ref): real vs placebos

| name | window | dly1 | dly15 | dly5 | pl11 | pl23 | pl37 | real |
|---|---|---|---|---|---|---|---|---|
| F1 | HOLD |  |  |  | 0.0 | 0.0 | 0.0 | 1606.0 |
| F1 | L3M |  |  |  | 0.0 | 0.0 | 0.0 | 0.0 |
| F1 | L6M |  |  |  | 0.0 | 0.0 | 0.0 | 0.0 |
| F2 | HOLD | 906.0 | 0.0 | 247.0 | -1203.0 | -106.0 | 0.0 | 0.0 |
| F2 | L3M | 0.0 | 2854.0 | 0.0 | -0.0 | 1766.0 | -0.0 | -0.0 |
| F2 | L6M | 0.0 | 2854.0 | 0.0 | 0.0 | 1766.0 | 0.0 | 0.0 |
| F2 | PRE | 7548.0 | 2896.0 | 4050.0 | 1179.0 | 2835.0 | -1289.0 | 3018.0 |
| F2 | X' | -11124.0 | -118.0 | -7712.0 | -1985.0 | -1636.0 | 142.0 | -6696.0 |
| F3 | HOLD |  |  |  | -186.0 | 361.0 | -6020.0 | 0.0 |
| F3 | L3M |  |  |  | -186.0 | 361.0 | -6019.0 | -695.0 |
| F3 | L6M |  |  |  | -186.0 | 361.0 | -6020.0 | -695.0 |
| F3 | PRE |  |  |  |  |  |  | 6338.0 |
| F4 | HOLD |  |  |  |  |  |  | 0.0 |
| F4 | L3M |  |  |  |  |  |  | 0.0 |
| F4 | L6M |  |  |  |  |  |  | 0.0 |
| F5 | HOLD |  |  |  |  |  |  | 0.0 |
| F5 | L3M |  |  |  |  |  |  | 0.0 |
| F5 | L6M |  |  |  |  |  |  | 0.0 |
| F6 | HOLD | -3150.0 | -912.0 | -3365.0 | -630.0 | 0.0 | -60.0 | -2199.0 |
| F6 | L3M | 0.0 | 0.0 | 0.0 | 0.0 | 914.0 | -0.0 | 0.0 |
| F6 | L6M | 0.0 | 0.0 | 0.0 | 0.0 | 914.0 | 0.0 | 0.0 |
| F6 | PRE | 1707.0 | -1848.0 | -4631.0 | -287.0 | 2767.0 | -989.0 | 1946.0 |
| F6 | X' | 165.0 |  | 7613.0 | -3966.0 | -277.0 | 1360.0 | -2204.0 |
| F7 | HOLD |  |  |  | 1191.0 | 1191.0 | 1191.0 | 602.0 |
| F7 | L3M |  |  |  | 1191.0 | 1191.0 | 1191.0 | 1191.0 |
| F7 | L6M |  |  |  | 1191.0 | 1191.0 | 1191.0 | 1191.0 |
| F8 | HOLD |  |  |  |  |  |  | 0.0 |
| F8 | L3M |  |  |  |  |  |  | -0.0 |
| F8 | L6M |  |  |  |  |  |  | 0.0 |


Identity check: IDENTITY 202610 598 25943.82 vs 598 25943.82 IDENTICAL



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


## 7. Extra evidence for F2/F6 (lead order 2026-11-14)

### 7a. Bi-weekly walk-forward (trail 26 weeks, re-pick every 2 weeks over the whole 1,470-cell grid, flat if trailing mean <= 0) and best-of null, standalone harness, both sides

| book | mode | wf_mean | wf_dd | wf_worst | wf_picks | wf_pct_pos | bestof_recents | bestof_older |
|---|---|---|---|---|---|---|---|---|
| F2 | real | -312.0 | 68512.0 | -5028.0 | 82 | 0.0 | 1130.0 | 439.0 |
| F2 | pl11 | -38.0 | 30638.0 | -4372.0 | 81 | 1.0 | 424.0 | 107.0 |
| F2 | pl23 | 199.0 | 21844.0 | -4765.0 | 80 | 0.0 | 608.0 | 317.0 |
| F2 | pl37 | -229.0 | 45297.0 | -7380.0 | 78 | 0.0 | 159.0 | 445.0 |
| F6 | real | -71.0 | 24493.0 | -3918.0 | 82 | 0.0 | 495.0 | 324.0 |
| F6 | pl11 | -55.0 | 10574.0 | -1909.0 | 81 | 0.0 | 79.0 | 92.0 |
| F6 | pl23 | -14.0 | 11090.0 | -2906.0 | 79 | 0.0 | 174.0 | 121.0 |
| F6 | pl37 | 12.0 | 10713.0 | -2554.0 | 78 | 0.0 | 198.0 | 101.0 |

wf_* = OOS weekly $ of the walk-forward chain; bestof_* = max over all 1,470 cells of (L6M+HOLD)/2 and (PRE+X')/2 for that var/unit: real vs shifted TICK is the family null for the cell choice.


### 7b. Concentration of the injected gain and stack without the worst reference week (all months present for the set)

| book | months | weeks | tkb_total | best5wk_share | best4mo_share | weeks_pos | weeks_neg | worst_ref_week | worst_ref | delta_mean_all | delta_mean_ex_worst | dd_ref_ex | dd_inj_ex | pl11_delta_all | pl11_delta_ex | pl11_dd_chg_ex | pl23_delta_all | pl23_delta_ex | pl23_dd_chg_ex | pl37_delta_all | pl37_delta_ex | pl37_dd_chg_ex | dd_chg_ex_real |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F2 | 39 | 170 | 35678.88 | 0.56 | 0.74 | 86 | 62 | 202606 | -55145.44 | 202.32 | 203.51 | 76186.06 | 79204.08 | 23.41 | 23.55 | 1179.48 | -114.12 | -114.8 | 2834.82 | -110.58 | -111.23 | -1289.32 | 3018.02 |
| F6 | 39 | 170 | 16695.24 | 1.3 | 1.19 | 72 | 55 | 202606 | -55145.44 | 91.16 | 91.69 | 76186.06 | 78132.3 | -207.08 | -208.31 | -286.74 | -215.71 | -216.99 | 2766.86 | -194.3 | -195.45 | -989.38 | 1946.24 |

ES injection: NOT possible. uw_inject only registers an NQ book inside the NQ-only JN05W2 engine; generalising to ES needs an ES price path and book walk in the engine, which is a separate engine change with its own identity proof and was not attempted. ES is standalone harness only (section 5).


## 6. Caveats
Grid-best cells from a 1.8M-cell search; the placebo columns show what the same cell earns on day-shifted TICK. Standalone profits shrink ~85% under live gates (DS3_UWBOOKS_B1 section 8): only section 4 counts. Delays use the real-time price with a stale TICK. Exact placebos (11/23/37) are run in the engine only for the finalists that pass L6M.
