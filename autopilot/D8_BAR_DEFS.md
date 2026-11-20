# D8_BAR_DEFS: bar construction rules and test vectors for every bar type used by an Asia or NY AM pool book (W-D8SPEC, order 1351Z section C items 1 and 3)

Written 2026-11-20 ~14:10Z. Research artefact only. Source of every rule below is the ENGINE CODE (read, never edited): `code/th_bars/kernels.py`, `code/th_bars/build_month.py`, `code/th_bars/common.py`, `code/th_bars/stats.py`, `code/th_swap/tbars.py` (+ `common.py`), `code/th_bars/b2_build.py`, `b2_lib.py`, `b2_kern.py`. Where `th_bars/spec.py` (the human-readable registry) disagrees with the code, the code is what produced every result and is what is written here; disagreements are listed in section 6.

Data end of the stored bars and tape: 2026-11-13 (trade tape holes: 2026-10-31 to 2026-11-04, nothing files for those days). Sample days: trading dates (td) **20261109, 20261110, 20261111** (td = Globex trading date = ET clock + 6 h; Asia td D runs 18:00 ET D-1 to 02:00 ET D). EST in force on all three days (DST ended 2026-11-01).

## 0. What was checked, and the headline findings

- Pool used (order: own-checks passers): 29 Asia books (`autopilot/ALL_NEW_STACK_ASIA_OWN_CHECKS.md` pool list) + 8 NY AM books (`ALL_NEW_STACK_NYAM_OWN_CHECKS.md`; the 8 are B2010fec9, B6f77f23d, L05350e98, L063a587d, L2176f633, L488784d8, L6547965c, L7cc56d99). Lbd4b5635 (stale, not in the pool) is left out. Each book's bar row, trigger, variant and parameters come from the `desc` column of `/mnt/l2/l2vast/_split/best_books_{asia,nyam}_full.csv`. The `aln_state.json` "passes" flag is a different, looser flag (270 cells) and was NOT used.
- 30 distinct bar rows are used (29 for Asia + NY AM combined, plus bmsgq). Table in section 1.
- **Verification:** for each bar row and each of the 3 sample days I rebuilt the session from the raw tape with the engine kernel (same code, same daily thresholds) and compared with the stored engine bars: open, high, low, close, volume, prints, delta, first/last/known timestamps. **96 of 96 (bar row x day x session) combinations are identical** (`d8_testvectors/bars/_rebuild_check.csv`). So the CSV test vectors are exactly what the engine built, and the rules below describe the code that built them.
- **Headline findings for the NT8 build (details in sections 4 to 6):**
  1. **tm420 (7-minute) and tm780 (13-minute) bars are epoch-aligned, not session-start-aligned.** Their boundaries are multiples of 420 s / 780 s from the Unix epoch, so the phase against an 18:00 ET session start changes every trading day (first bucket start 22:58, 23:00, 22:55 UTC on the three sample days for tm420; 22:57, 23:00, 22:50 for tm780). NT8 native Minute 7 / Minute 13 anchor at the session-template start (18:00 ET). Against an NT8-style 18:00-anchored grid, the engine's tm420 Asia bars are bar-for-bar identical on **1 of 3 sample days** (the day the phase is 0) and 0 bars identical on the other two; tm780 the same (1 of 3). Books affected: L973b5c8a (tm420, Asia), Lec335094 (tm780, Asia), L05350e98 (tm420, NY AM). The other epoch-aligned periods in the pool (45, 60, 120, 240, 300, 600 s) divide 3600, so they coincide with the NT8 clock grid on every day and through the DST change. This is a spec decision for the lead: either build a custom epoch-aligned 420 s / 780 s bar in D8, or re-run those three books on aligned 7/13-minute bars (time_m_7 / time_m_13 are in the W-BAR store, session-start anchored).
  2. **Event bars restart at every session boundary (02:00, 08:30, 09:30, 12:00, 16:00, 18:00 ET).** An NT8 continuous chart does not. Chart-free D8 must therefore build its own bar series inside the strategy and reset it at those six times. A bar in progress at a boundary is closed as a "truncated" bar (flag `part=1`, known at the last print) and never gives a signal.
  3. **Thresholds of most activity and price bars change every day** (daily scale from the trailing 20 trading days). D8 needs a nightly table; a 40-day table of the actual values and the inputs are provided.
  4. **Print granularity:** the engine tape is the exchange MBO trade-record stream (one record per resting-order fill: 14.8% of records on 2026-11-10 share a timestamp with the previous record). Tick-count bars (tick_500) and the imbalance and run bars (dib, vrb, drb: EWMAs updated per print) depend on this granularity; volume-based bars do not. Whether NT8's tick stream has the same granularity depends on Josh's data provider; this is an open item, not assumable.
  5. **bmsgq_B200 (NY AM book L063a587d) cannot be reproduced in NT8 bar for bar:** it counts quote messages from the full order-book message feed (adds, cancels, modifies) and uses the mid price of the top of book as O/H/L/C. NT8 receives price-level depth updates, not the order-level message stream. Treat the book as not buildable on NT8 data unless Josh's feed is Databento-style MBO.

## 1. The bar rows in the pool, who uses them, data needed, and bar rate

Session column: A = Asia pool book, N = NY AM pool book. "Rate" = bars per hour from the scorecard (best_books `bph`). Data need legend: **T** = trades only (price, size, time, from the Last stream); **T+side** = trades plus aggressor side (needs bid/ask classification at each trade, i.e. Level 1 quotes alongside, or an exchange aggressor flag); **Q** = needs the order-book message stream (depth/MBO).

| bar row | what it is | books (sess) | rate /h | data need | custom NT8 code needed |
|---|---|---|---|---|---|
| tm45 | time bar 45 s, epoch-aligned | B6f77f23d (N) | 80 | T | no (clock grid is NT8-aligned; but see close rule, section 3.1) |
| tm60 | time 60 s, epoch-aligned | L7f41b347, Lcbc8a7ec (A) | 60 | T | no |
| tm120 | time 120 s | L15f14deb (A) | 30 | T | no |
| tm240 | time 240 s | L1756b913 (A) | 15 | T | no |
| tm300 | time 300 s | L1edb9fab (A) | 12 | T | no |
| tm420 | time 420 s, epoch-aligned (NOT NT8 aligned) | L973b5c8a (A), L05350e98 (N) | 8.6 / 8.8 | T | YES (epoch-aligned period) |
| tm600 | time 600 s | Lb68a132d (A) | 6 | T | no |
| tm780 | time 780 s, epoch-aligned (NOT NT8 aligned) | Lec335094 (A) | 4.6 | T | YES |
| time_m_1 | time 1 min, anchored at first print of the session | L578701ed, Lff52ec0c (A) | 60 | T | no for Asia (see 3.2) |
| time_m_3 | time 3 min, same | M7423c0d9 (A) | 20 | T | no |
| time_m_5 | time 5 min, same | L7c368a4f, L9aa7805c (A) | 12 | T | no |
| vol_350 / 750 / 1100 | volume bar, scaled | L11152f7a / Lda55d973 / Lcae177ba (A) | 23.6 / 11.1 / 7.6 | T | yes (daily threshold; closing print not split) |
| vol_6000 | volume bar, scaled | B2010fec9 (N) | 16.6 | T | yes |
| tick_500 | tick-count bar, scaled | Lc4584864 (A) | 10.9 | T (print granularity matters) | yes |
| vsess_50 / 80 / 120 / 600 | session-volume clock | Lbe5ac95b / L29b1bc3f, La6f6f7ad / L40bde9ea / Lfb608c7b (A) | 6.9 / 11.0 / 16.4 / 80.9 | T | yes (session-median table) |
| dlt_70 | delta bar: abs cumulative delta from bar open | Lc849eb8c (A) | 16.3 | T+side | yes |
| cdr_100 | cumulative-delta-range bar | Ldcdb0b6e, L7ea48296 (A) | 14.2 | T+side | yes |
| dib_3500 | dollar-imbalance bar (López de Prado) | M3f6f752c (A), L2176f633 (N) | 22.9 (A) / 242 (N) | T+side (print granularity matters) | yes, stateful |
| vrb_700 | volume-run bar | L86781ac0 (A) | 15.9 | T+side (print granularity) | yes, stateful |
| drb_700 | dollar-run bar | Le9bd7276 (A) | 10.7 | T+side (print granularity) | yes, stateful |
| mrenko_20 | median Renko, scaled brick | L3faac8df (A) | 13.5 | T | yes (daily brick) |
| lbrk_3_40 | three-line break, scaled box | L7cc56d99 (N) | 9.5 | T | yes (variant, see 3.9) |
| swing_pct_8 | zig-zag swing, reversal = 8 bps of price | L6547965c (N) | 34 | T | yes |
| swing_atr_0.25 | zig-zag swing, reversal = 0.25 x (daily-range-derived "ATR") | L488784d8 (N) | 121 | T | yes |
| bmsgq_B200 | quote-message-clock bar on mid price | L063a587d (N) | 83 | **Q** (order-book messages) | not reproducible on NT8 depth data |

Three-book Asia stack: Ldcdb0b6e = cdr_100; L578701ed = time_m_1; Lfb608c7b = vsess_600. NY AM Stack A: L7cc56d99 = lbrk_3_40; L488784d8 = swing_atr_0.25.

Load on NT8 (item 3): everything except cdr, dlt, imbalance/run bars and bmsgq needs only the trade stream (Last events, price/size/timestamp). The highest-rate trade-only items are swing_atr_0.25 and vsess_600 (about 120 and 80 bars per hour; each bar is just a few comparisons per print). The price-bar and time-bar types need no per-print state beyond a few numbers. cdr, dlt and the imbalance/run bars need the aggressor side of each trade, so the strategy must also take Level 1 (best bid/ask) or an aggressor flag; they keep one or two running sums and, for dib/vrb/drb, five EWMA numbers. Nothing in the pool except bmsgq needs depth. No type needs drawing objects or a chart: all of it is arithmetic on the tick stream.

## 2. Conventions common to all event bars (engine code)

- **Input tape:** one row per exchange trade record (`action == 'T'` of the MBO feed): ts (ns), price in ticks of 0.25 pt, size, aggressor side (+1 buy aggressor, -1 sell aggressor, 0 none), instrument id. Extracted by `th_bars/extract_trades.py`. Prices below are in ticks (0.25 pt) unless said "pts". 0.25 pt = 1 tick = $5.
- **Sessions** (ET clock, `th_bars/common.py sessionize` and `th_swap/tbars.py sess_of`): minute-of-day m; code 0 Asia 18:00-02:00; 1 London 02:00-08:30; 2 pre 08:30-09:30; 3 NY AM 09:30-12:00; 4 NY PM 12:00-16:00; 5 close 16:00-18:00 (17:00-18:00 is the halt, no trades). td = (ET + 6 h) calendar date. Session id of a bar = td*10 + code.
- **Reset:** every event-bar kernel (`k_cum`, `k_range`, `k_imb`, `k_cdr`, `k_renko`, `k_dchg`, `k_lbrk`, ...) closes/discards its state when the session key changes OR the instrument id changes (contract roll), and starts a fresh bar series with index 0 at the next print. Scale thresholds are fixed at the session's td for the whole session (no intra-session update).
- **Truncated last bar:** `k_cum`, `k_cdr`, `k_imb`, `k_range`, `k_mom` and the time bars emit the unfinished last bar at the session end with `part = 1` and known time = its last print. The harness drops signals on `part = 1` bars. The Renko, line-break, swing (`k_dchg`) and P&F kernels emit nothing for an unfinished brick or leg at the session end.
- **Closing print:** for threshold (cum) bars the print that reaches the threshold belongs entirely to the bar it closes (no split across bars; NT8 native Volume bars split the closing print: measured on the engine store 28% of vol bars overshoot by about 1 contract on average, `autopilot/NT8_FIDELITY.csv`). For Renko and line break, the breaching print's volume goes to the FIRST brick that print completes; a print that breaches several bricks emits several bricks at the same timestamp, the extra ones with zero volume and zero prints.
- **Known time (`t_close` / `known_ts`)** = timestamp of the closing print for every event bar (this is when a signal on that bar exists); the next bar opens at the next print (for Renko/line-break/swing bars the next bar's first-print time equals the breaching print's time, because the breaching print is also the opener of the next bar).
- **Series seen by the signal code:** all sessions concatenated in time order as one continuous series (bars of London, pre, NY AM, NY PM, close are in the same series as Asia; `part = 1` bars stay in the series); a signal is accepted only if the signal bar's session is the book's session and `part == 0`. Indicator state therefore runs across session breaks. (Trigger details: `D8_TRIGGER_DEFS.md`.)
- **Scale factors** (used by every "scaled" row): `stats_day` row per td (all instruments' T records of the Globex day): vol = contracts, n = prints, rng = (max over instruments of high-low)/4 in points, dol, rv. For day i the trailing value is `tr[i] = median of the previous up to 20 rows (rows with value > 0) of the table (not calendar days; rows before i)`; if fewer than 5 rows, tr = r0. `r0 = median of the first 60 rows` (2023-04-03 .. 2023-06-23). Scale `s = tr / r0`. Constants: **r0_vol = 610702, r0_n = 373169, r0_rng = 191.5 pts, r0_dol = 1.69605053025e11**. Session volume table for the volume clock: per session code, `x = session volume of that code per td (stats_sess)`; `sess_vol[code][i]` = median of the previous up to 20 values > 0 (needs >= 5 else backfilled/forward-filled). The actual values for the last 60 td are in `d8_testvectors/bars/_scale_inputs_last60td.csv`; the thresholds each pool bar used on each of the last 40 td are in `_daily_thresholds_last40td.csv`.
- Note: the table skips days without tape. Because the median is over rows (not calendar days), the hole 2026-10-31..11-04 does not enter the 20-row window; a live system with all days would differ slightly in those weeks only.

## 3. Rules per bar type (from the engine code), with parameters as used and sample thresholds

Files: `autopilot/d8_testvectors/bars/<row>_td<YYYYMMDD>_s<0|3>.csv` (s0 = Asia session of that td, s3 = NY AM). Columns for event bars: bar_idx, t_first_print_utc, t_last_print_utc, t_close_known_utc, o, h, l, c (points), volume, prints (trade records), delta (buy-aggressor minus sell-aggressor contracts), part_truncated_session_end. For swing bars `t_last_print_utc` is the time of the leg's extreme (not the confirming print). Time stamps are UTC to the nanosecond. Prices in points.

### 3.1 tm<P> time bars (rows tm45, tm60, tm120, tm240, tm300, tm420, tm600, tm780) (`th_swap/tbars.py time_bars`)
- Bucket = floor(ts / P) with ts in ns since the Unix epoch, P in ns (epoch-aligned). A bar exists only if at least one print falls in its bucket (no empty bars). O/H/L/C from the first/max/min/last print of the bucket, volume = sum of sizes, delta = sum(side x size).
- **Close rule:** nominal end = (bucket + 1) x P. The bar is **known at max(nominal end, timestamp of the first print of the next existing bucket)**, i.e. when the next bar's first print arrives (NT8 behaviour, "engine evidence: Asia sig_ts is 2-14 s after the boundary when prints are sparse"). A signal from this bar is timed then. In active sessions the lag is milliseconds (sample: 14:31:00.008 for a 14:31:00 end).
- **No session reset** (built on the continuous tape; roll ignored). A bar is assigned to the session of its **nominal END time**, so a bar ending exactly at 02:00:00 ET is London, the bar ending 18:00:00 is Asia, and an Asia-session count is 479 one-minute bars (not 480): the bar 01:59-02:00 is London's. A bar that straddles the NY open (e.g. tm420 first NY AM bar ends 14:31 UTC) contains pre-open prints.
- Epoch alignment: for P dividing 3600 (45, 60, 120, 240, 300, 600 s) all boundaries fall on the clock grid of a whole-hour-offset time zone and equal the NT8 session-start grid on every day. For **420 and 780** they do not (section 0, finding 1); phase table `_tm_phase_vs_session_start.csv` (rows are NT8 anchor minus engine grid in seconds, by td).
- Test vectors: `tm*_td*_s0.csv` / `_s3.csv` with columns bar_idx_in_session, bucket_start_utc, bucket_end_utc, t_close_known_utc, first_print_utc, last_print_utc, o, h, l, c, volume, delta, prints. Counts per session on the sample days: tm60 479, tm120 239, tm240 119, tm300 95, tm600 47, tm420 68/68/69 (Asia), 21/22/21 (NY AM), tm780 37/36/37, tm45 200 (NY AM).
- Data: trades only.

### 3.2 time_m_<N> time bars (rows time_m_1, time_m_3, time_m_5) (`build_month.time_bars`, W-BAR store)
- Per **session segment** (restarts at each session boundary and at a roll): t_start = timestamp of the first print of the segment; bucket = floor((ts - t_start) / (N x 60 s)); bar exists only if it has a print. Known time = bucket end (t_start + (k+1) x N min) exactly, **no wait for the next print**; the last bucket of a segment is truncated (`part = 1`, known at its last print).
- For Asia the first print of the session is at 18:00:00.000 ET (verified: offset 0 on the 3 sample days and on 98 of the last 100 Asia sessions; the exceptions were 2026-09-04, 10.6 ms late, and 2026-06-23, 2 h late), so the grid equals the NT8 session-start grid for N = 1, 3, 5: on the three sample days **480 / 160 / 96 bars, all identical in OHLCV** to a grid anchored on exactly 18:00:00 ET. If a day's first print is late the whole grid shifts by that offset (up to 10 ms in the one case seen), which can move boundary prints. For sessions other than Asia the grid starts at the first print after 02:00, 08:30, 09:30 etc.
- The close rule differs from tm: time_m bars are known at the clock boundary; tm bars are known at the next print. Signals therefore carry different timestamps by milliseconds-to-seconds. (Ambiguity: which one NT8 would do is not for the engine to say; NT8 raises OnBarUpdate on the first tick of the next bar.)
- Test vectors: `time_m_{1,3,5}_td*_s0.csv`.
- Data: trades only.

### 3.3 vol_<N> volume bars (`k_cum`, mode 0, metric = size)
- Threshold `thr = N x s_vol` (contracts, float, fixed for the session). Bar closes at the print for which cumulative bar volume >= thr. Closing print stays in the bar (no split). Examples: vol_350: 384.9 / 388.9 / 387.0 contracts on the three sample days; vol_750 824.8 / 833.3 / 829.2; vol_1100 1209.7 / 1222.1 / 1216.2; vol_6000 (NY AM) 6598.6 / 6666.2 / 6633.9. Sample bars: 285/166/196 (vol_350 Asia), 133/78/92 (vol_750), 91/53/63 (vol_1100), 46/44/37 (vol_6000 NY AM).
- Data: trades only.

### 3.4 tick_<N> (`k_cum`, metric = 1)
- thr = N x s_n prints (record count). tick_500: 656.0 / 670.2 / 680.4 prints. Counts 137 / 77 / 87 Asia bars. Prints are MBO trade records (see section 0 finding 4).
- Data: trades only (print granularity open).

### 3.5 vsess_<N> session-volume clock (`k_cum`, mode 0, metric = size)
- thr = max(sess_vol[code] / N, 1) contracts, where sess_vol[code] is the trailing 20-session median volume of that session code (Asia code 0, NY AM code 3). Asia sample medians: 77936 (td 20261109), 85212 (20261110 and 20261111). Thresholds: vsess_50 1558.7 / 1704.2 / 1704.2; vsess_80 974.2 / 1065.2 / 1065.2; vsess_120 649.5 / 710.1 / 710.1; vsess_600 129.9 / 142.0 / 142.0 contracts. Bars: vsess_600 840 / 448 / 527 (Asia), vsess_120 169 / 91 / 107, vsess_80 113 / 61 / 72, vsess_50 71 / 38 / 45.
- Session volume of the **current** session is not used (trailing only). The first 5 sessions of history use back/forward fill (irrelevant for live).
- Data: trades only.

### 3.6 dlt_<N> delta bar (`k_cum`, mode 1)
- cum += side x size (side 0 adds 0); bar closes when |cum| >= thr = N x s_vol (dlt_70: 77.0 / 77.8 / 77.4 contracts). cum restarts at 0 at each bar open. Closing print stays in the bar. Counts: 152 / 83 / 132 Asia bars.
- Data: trades + aggressor side.

### 3.7 cdr_<N> cumulative-delta-range bar (`k_cdr`)
- State per bar: running delta `dlt` (sum of side x size since bar open, starts 0); `cmx`, `cmn` = running max and min of `dlt`, both initialised to 0 at bar open. After each print update dlt, cmx, cmn. Close when **cmx - cmn >= thr**, thr = N x s_vol (cdr_100: 110.0 / 111.1 / 110.6 contracts on the 3 sample days). Closing print stays in the bar. The bar's delta column is the end-of-bar `dlt`, not the range.
- Counts 135 / 80 / 114 Asia bars (bph 14.2). Books Ldcdb0b6e (stack) and L7ea48296.
- Data: trades + aggressor side.

### 3.8 mrenko_<N> median Renko (`k_renko`, O = B//2, R = B + B//2, wick off)
- Brick B = max(2, round(N x s_rng)) ticks, numpy rounding (round half to even). mrenko_20: B = 59 / 61 / 61 ticks (14.75 / 15.25 / 15.25 pts), reversal distance R = 88 / 91 / 91, reversal offset O = 29 / 30 / 30.
- State: bo (reference open), bc (last brick close), d (direction 0 initial, +1, -1). First print of the session sets bo = bc = print price. While d = 0: first brick when p >= bo + B (up) or p <= bo - B (down): brick [bo, bo +/- B]. Trend continuation (d = +1): p >= bc + B emits brick [bc, bc + B]; reversal (d = +1): p <= bc - R emits a brick that opens at bc - O and closes at bc - R (height B, direction flips). Mirror for d = -1. All with the current brick size of that print (constant within the session). A loop re-tests the same print so one print can emit several bricks. OHLC of a brick = (open, max(open, close), min(open, close), close); no wicks. Volume/prints/delta since the previous brick go to the first brick emitted; t_first = ts of the first print after the previous brick (equal to the previous brick's known time).
- Counts 411 / 98 / 80 Asia bricks per td session on the sample days (a 1378-point range day on 11-09 produced the 411).
- Sample: td 20261110 brick 0 o 28064.00 c 28079.25; brick 1 o 28071.75 (= 28079.25 - 7.5) c 28056.50 (= 28079.25 - 22.75).
- Check against Josh's NT8 median-Renko type: the engine's reversal rule (needs 1.5 bricks from the last close, new brick opens halfway) may differ in detail from a third-party MedianRenko; the test vectors decide.
- Data: trades only.

### 3.9 lbrk_3_40 three-line break on a scaled box (`k_lbrk`, NL = 3)
- Box B = max(2, round(40 x s_rng)) ticks: 117 / 122 / 122 ticks (29.25 / 30.5 / 30.5 pts) on the sample NY AM sessions.
- State: lc (last line close), direction d, store of the last lines' highs and lows (ring of 8), count. First print sets lc = print. Line rules (loop per print, may emit several lines): d = 0: up line [lc, lc + B] when p >= lc + B; down line when p <= lc - B. d = +1: another up line [lc, lc + B] when p >= lc + B; **reversal** when p < the lowest low of the last min(count, 3) lines and lc (strict): down line from lc to **(that lowest low - 1 tick)**. d = -1 mirror: down line [lc, lc - B] when p <= lc - B; reversal when p > highest high of the last 3 lines and lc: up line from lc to (that highest high + 1 tick). After each line lc = its close, d = its direction.
- Note the continuation rule is a **fixed box from the last line close** (not "above the previous line's high" as in classic line break), and the reversal line closes 1 tick beyond the extreme of the last three lines. This is the engine's definition; a native NT8 LineBreak bar will differ (the registry says "native LineBreak (3 lines; N-line custom)"). Must be a custom bar type.
- Counts: 31 / 33 / 21 lines in the NY AM session on the sample days (bph 9.5).
- Data: trades only.

### 3.10 swing_pct_8 and swing_atr_0.25 swing legs (`k_dchg`)
- A bar = a leg between two confirmed swing extremes ("directional change"). Reversal size theta in ticks: swing_pct_8: theta = max(2, round(8 x px / 10000)) where px is the price in ticks of the **current print** (recomputed per print: 87 to 92 ticks (about 22 pts) around 28000), i.e. 8 basis points of price. swing_atr_0.25: theta = max(2, round(0.25 x ATR)) with ATR = max(1, 4 x tr_rng / 10), tr_rng = trailing-20-row median of the daily range in points (`abs_rng`: 583.75 on 11-10; ATR 233.5 "ticks"; theta 56 / 58 / 58 ticks = 14 / 14.5 / 14.5 pts). The "ATR" is NOT an ATR of intraday bars: it is one tenth of the trailing median daily range expressed in ticks (the registry text says "ATR of 5-min ranges trailing"; the code does not do that).
- State (reset per session): d = 0 start: track running high ehi / low elo from the first print; the first leg is decided when price is theta above the low (leg up from that low, st = elo) or theta below the high. d = +1: ext = running high; if p > ext then ext = p (and remember its time te); else if ext - p >= theta: **emit leg bar** o = st, h = ext, l = st, c = ext (volume/prints/delta since the leg's confirmation of the previous leg), t_first = ts of the previous confirming print, t_last (column) = te (time of the extreme), **known = ts of this confirming print**; then st = ext, d = -1, ext = p. d = -1 mirror (bar o = st, h = st, l = ext, c = ext).
- The bar is therefore known only theta ticks after the extreme was made; its close is the extreme, not the price at the confirming print; the open of the next leg is that extreme. Volume etc. accumulate from the previous confirming print to this confirming print.
- Counts: swing_pct_8 126 / 198 / 94; swing_atr_0.25 308 / 448 / 236 legs in NY AM.
- Data: trades only.

### 3.11 dib_3500 dollar-imbalance, vrb_700 volume-run, drb_700 dollar-run (`k_imb`)
- Not a fixed threshold: the bar length adapts (López de Prado). Parameters: wmode (weights w per print: dib 2 = dollar: w = px_ticks x 5 x size / 1e6 (= price in points x $20 x size / $1e6 for NQ); vrb 1: w = size; drb 2: w = px x 5 x size / 1e6), run flag (0 imbalance bars dib, 1 run bars vrb/drb), T0 = max(10, N x s_n) prints (dib_3500: 4592 / 4691 / 4763 on the sample days; vrb_700 and drb_700: 918.4 / 938.3 / 952.6).
- Per print: b = aggressor side; if side 0, b = +1 if px > previous px, -1 if lower (same segment), else the previous b. At session start (and after a roll) the state is initialised: E[T] = T0, ebw = 0, eabs = 1, pb = 0.5, ewb = 1, ews = 1, b_prev = 1. alpha = 1 / max(T0, 10). Update: ebw += alpha (b w - ebw); eabs += alpha (w - eabs).
  - **Imbalance bar (run = 0):** th += b w; threshold = E[T] x max(|ebw|, eabs / sqrt(E[T])); close when |th| >= threshold.
  - **Run bar (run = 1):** if b > 0: thb += w, ewb += alpha (w - ewb), pb += alpha (1 - pb); else ths += w, ews += alpha (w - ews), pb += alpha (0 - pb); threshold = E[T] x max(pb x ewb, (1 - pb) x ews); close when max(thb, ths) >= threshold.
  - On close: E[T] = 0.8 E[T] + 0.2 x (prints in this bar); clamp E[T] to [0.25 T0, 4 T0]; th, thb, ths reset to 0 at the next bar open; **ebw, eabs, pb, ewb, ews persist across bars** within the session and reset only at session start / roll. Closing print stays in the bar.
- Counts: dib_3500 Asia 274 / 168 / 183, NY AM 693 / 716 / 536; vrb_700 Asia 240 / 83 / 97; drb_700 123 / 58 / 65. These are the most state-dependent bars in the pool (an error in any one print's size or side shifts every later bar of the session). With any difference in print granularity the bars will not match.
- Data: trades + aggressor side; print granularity critical.

### 3.12 bmsgq_B200 quote-message-clock bar (`b2_build.py build_one`, `b2_lib.py`)
- Built from the book-event table (MBO feed reduced to top of book + message counters per packet), not from the trade tape. Per session (NY AM 09:30-12:00 ET): quote states = packet-end book states with valid bid and ask whose mid (bpx + apx) differs from the previous kept state. Counter `cumq` = running count of add + cancel + modify messages. N = max(1, round(trailing-20-session median of the session's quote messages / 200)): 43452 / 44761 / 45660 messages per bar on the three sample days (medians 8.69 M / 8.95 M / 9.13 M). Bucket = (cumq - cumq_first_kept_state) // N after normalising the first kept state to 1; a bar ends at the last kept state before the bucket index changes; **known = timestamp of the first kept state of the next bucket**. O/H/L/C = the mid price in 1/8 pt units (half-tick grid) of the kept states; volume and delta columns are trade volume and delta in (t0, t1] attached afterwards; `quote_states_in_bar` is the number of kept states.
- Counts 211 / 255 / 166 bars in NY AM on the sample days. Verified identical to stored bars (rebuilt with the engine functions from the day's book table `/mnt/l2/l2vast/_bars/book/<day>.parquet`).
- Test vectors: `bmsgq_B200_td*_s3.csv` (columns o_mid... in points).
- Data: order-book message stream (MBO). The count of add/cancel/modify **messages** is an exchange-feed property that NT8 level-2 callbacks (price-level updates) do not reproduce. OPEN: no NT8 equivalent without an MBO feed in D8.

## 4. Summary table: what must be written as custom code for D8

| item | NT8 native possible? | note |
|---|---|---|
| tm45/60/120/240/300/600, time_m_1/3/5 (Asia) | native Second/Minute bars give the same bars (grid) | tm bars close at the next print; time_m at the boundary; both off by at most the print gap |
| tm420, tm780 | no | epoch-aligned phase; custom, or change the book to time_m_7 / time_m_13 and re-test |
| vol_N | not exactly (NT8 splits the closing print) | scaled threshold daily, custom |
| tick_500 | native Tick bar with daily value, if print granularity matches | threshold changes daily |
| vsess, dlt, cdr, mrenko, lbrk, swing, dib, vrb, drb | custom | state machines above, all reset per session, thresholds daily |
| bmsgq | no | needs MBO message counts |

## 5. Test vector index (all under `autopilot/d8_testvectors/bars/`)

- `_rebuild_check.csv`: 96 rows (bar row x td x session): engine-kernel rebuild equals stored bars (all True).
- One CSV per (bar row, td, session) as listed in section 3 (92 files).
- `_daily_thresholds_last40td.csv`: threshold actually used per bar row, td (last 40) and session.
- `_scale_inputs_last60td.csv`: trailing medians and scale factors, plus the own-day vol, prints, range values, so a nightly NT8 computation can be checked against the engine.
- `_tm_phase_vs_session_start.csv`: phase of the 420/780 s epoch grid versus an 18:00 ET anchor for the last 15 td.

## 6. Ambiguities and mismatches between spec text and code (stated, not guessed)

1. `th_bars/spec.py` says swing_atr uses "ATR of 5-min ranges trailing"; the code uses `4 x (trailing-20 median daily range in pts) / 10` ticks. Code used.
2. `spec.py` says time bars "reset at each of our session breaks" for time_m (true) and says nothing about tm (th_swap, epoch aligned, no reset). Two different time-bar builders exist and the pool uses both.
3. `spec.py` describes lbrk as "line break on a base box"; the exact continuation rule (fixed box from last close) and the 1-tick reversal close are only in `k_lbrk`.
4. The `dib`/`drb` "dollar" weight is notional in $ million assuming a 20 USD/point multiplier (px_ticks x 5 = points x 20); the spec writes "price x 20 x size". Same thing.
5. Roll handling: tm bars ignore a contract roll (a roll print shares the bucket); event bars end the bar at a roll. No roll falls inside the 3 sample days (next quarterly roll mid-December; not tested here).
6. The Oct 31 to Nov 4 tape hole is skipped in the scale medians (see section 2).
7. Print granularity vs NT8 (section 0 finding 4) and aggressor classification (MBO aggressor flag versus NT8 bid/ask comparison) are not testable from the stored data; they decide whether cdr, dlt, dib, vrb, drb, tick bars match bar for bar in NT8. The test vectors let Josh check that on a recorded day.
8. bmsgq: the only book on this row (L063a587d) cannot be tested in NT8 unless an MBO feed is available.

## 7. Not done / open
- Samples cover only 3 days (order asked 3), all in EST; no roll day and no DST-change day. A roll-day and DST-day vector can be added on request.
- Rate of non-Asia sessions: only Asia (code 0) vectors for Asia books and NY AM (code 3) for NY books; other sessions are in the store but not exported.
- Trigger definitions and signal test vectors are in `autopilot/D8_TRIGGER_DEFS.md` (written by the trigger part of this task).
