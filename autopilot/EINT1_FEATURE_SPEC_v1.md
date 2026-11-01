# EINT1 FEATURE SPEC (EF-1, 2026-11-01): exact definitions of the ABR signal-strength and HTF features, the tercile rule, and D7 v1.0b vs the research code

Read-only on code and data. Masks capped 20260206 (aux_bar.npz and time_1m filtered ld<=20260206; no post-cap file or ts column opened). Verified by recomputation (section 6), not by names. Tie-out CSVs: `l2vast/ds3/out/eint1spec/tieout_30signals.csv` (14 features x 30) and `tieout_30signals_extra.csv` (atr_ratio, st5/st10 dist and age x 30).

## 1. MATCH / DIFFERS table (D7 v1.0b statement vs research code)

| # | D7 v1.0b says | Research code says (CORRECT value for v1.0c) | Verdict |
|---|---|---|---|
| 1 | Supertrend 1-min, ATR10, mult 3.0 | Supertrend(10,3.0), ATR = Wilder RMA (alpha 1/10, seed = SMA of first 10 TRs, TR includes gaps to prior close), on 1-min bars (st5/st10: same on 5/10-min bars) | MATCH |
| 2 | source hl2 | hl2 = (H+L)/2 for the basic bands; flips and ratchet use the CLOSE | MATCH |
| 3 | current-bar band | line = the current (just-closed) bar's FINAL band: lower band if dir=+1, upper band if dir=-1; flip test = this bar's close vs this bar's final band; ratchet tests the PRIOR close vs prior final band | MATCH |
| 4 | (distance normaliser, if D7 uses ATR10) | sig_st1_dist_atr = side*(E - line)/**ATR14 (Wilder, 1-min)**, NOT ATR10. E = entry price (not the bar close). Negative when the Supertrend is against the trade (27% of signals) | DIFFERS if D7 divides by ATR10 or uses the bar close |
| 5 | age = 0 when the Supertrend is against | sig_st1_age = number of 1-min bars since the Supertrend direction last flipped (0 on the flip bar), **independent of the signal side**. NOT 0 when against. st5/st10 age is also counted in 1-min bars (direction changes only at 5/10-min boundaries). Median 22 / 98 / 183, max 365 / 1,381 / 2,353 for st1/st5/st10 | DIFFERS |
| 6 | EMA20 slope over 5 bars / ATR14 | sig_slope = side*[(EMA20[i]-EMA20[i-5])/**5**]/ATR14, i = last closed 1-min bar; EMA20 of 1-min closes, alpha 2/21, seed = first close of the whole series (never reset). The divide-by-5 (per-bar slope) must be present | MATCH (check the /5) |
| 7 | Keltner EMA14 +/- 1.0 x ATR10 | sig_kelt1 = side*(E - EMA20)/ATR14 on 1-min bars: **EMA20, ATR14, no multiplier/band**, E not close. sig_kelt3 = side*(C3 - EMA14_3m)/ATR14_3m on completed 3-min bars (epoch-minute clock), C3 = close of the last completed 3-min bar, **ATR14 Wilder on 3-min bars**, no multiplier. D7's "EMA14 +/- 1.0 x ATR10" matches neither | DIFFERS (both) |
| 8 | HMA 9/21 / ATR14 | sig_hma_sp = side*(HMA9 - HMA21)/ATR14, HMA of 1-min closes. HMA(n)=WMA(2*WMA(n//2) - WMA(n), int(sqrt(n))): HMA9 = WMA4/WMA9/WMA3, HMA21 = WMA10/WMA21/WMA4. hma_slope (separate feature) = side*(HMA21[i]-HMA21[i-1])/ATR14 | MATCH |
| 9 | daily ATR = mean of the last 14 label-day ranges | daily ATR (atrd) = simple mean of (high - low) over 14 label days (ETH, 18:00-17:00 ET), min 5 days, using the days up to and including the PRIOR completed label day (the current day is excluded). Range, not true range | MATCH |
| 10 | label day 18:00 ET | label day rolls at 18:00 ET (Sun 18:00 -> Monday; weekend -> Monday). Day open = open of the first 1-min bar of the label day (18:00 ET). Week open = open of the first label day of the Mon-Fri week (Sun 18:00 ET on a normal week) | MATCH |
| 11 | all signed with the signal side | All sig_* and htf_* are side-signed EXCEPT: atr_ratio, atr_pts (unsigned); htf_pd_range_atr, htf_on_range_atr, htf_on_ratio, htf_fh_atr (unsigned). htf_pd_pos is side*(pos-0.5), centred, not 0..1 | MATCH with the listed unsigned exceptions |
| 12 | (ATR for sd_pd_*, htf_vwap) | sd_pd_hi_atr = side*(PDH - E)/ATR14(1-min), sd_pd_lo_atr = side*(PDL - E)/ATR14(1-min); htf_vwap_atr = side*(E - VWAP_ETH)/ATR14(1-min). They are NOT divided by the daily ATR. Only htf_d_open_atr, htf_wk_open_atr, htf_tr20/50, htf_gap_*, htf_on_range_atr, htf_pd_range_atr use the daily ATR | state explicitly in v1.0c |
| 13 | tercile cut (see section 5) | study = causal expanding per-book rank, min 100 prior signals; SHIPPED numeric thresholds in `eint1_policy_candidate.txt` = per-book quantiles of the trailing 12 months to 20260206 | DIFFERS from the study; v1.0c must say which |

Additional fixed facts D7 should hold: all bar features are as of the LAST COMPLETED 1-min bar before the entry minute (no forming bar); E is the entry price at the entry second; bars are the back-adjusted library series (offsets cancel in every ratio above except none uses an absolute level); one-bar warm-up NaN rules in section 4.

## 2. Bar basis and as-of rule (all features)

* Two bar sources, both 1-min, both back-adjusted library space (ds3_g2 / library), both complete bars at the as-of instant:
  * AUX bars (`/mnt/l2/l2vast/ds3_thp/aux/aux_bar.npz`, built by `code/abr/thp_aux.py:main` L190-250, `code/abr/abr_aux.py:make_new` L45): o,c from the g2 library arrays, h/l = max/min of 1-s path highs/lows over the minute. Feed ATR14, atr_ratio, EMA20/slope, Supertrend st1/st5/st10, kelt1, kelt3, hma_sp, sd_pd_*, VWAP/sd_vwap_*.
  * `time_1m` bars (`out/bars/time_1m.parquet`, tick-built, t_sig = bucket END = bar known complete, ticks*0.25 = points). Feed pb_speed, hma_slope, body_*, bar_vol_rel and the whole daily HTF table (day open/high/low/close, week open, daily ATR) in `code/eint1/ei_feat.py`.
  * The two bar sets agree on the close and differ by a tick or more in some o/h/l (ties: ATR 1e-6; pb_speed/hma_slope are computed on time_1m and tie only on time_1m, section 6).
* ABR build (`code/abr/abr_build.py:process_entry`): s0 = entry second, decision instant = START of the entry second; `m1 = s0//60 - 1; lc = last bar with MIN <= m1` (L130-131) = the last bar closed at or before the entry minute start. `bar_age_min` records the gap. So a signal at 10:00:30 uses the 09:59 bar (closes 10:00:00); the forming 10:00 bar is never used.
* EINT1 table (`ei_feat.py` L46): `bi = searchsorted(t_sig, entry_ts, 'right') - 1` = last bar with t_sig(END) <= entry second = same completed bar (bar_age_s = entry second - bar end, 0..59; recomputed 30/30 identical).
* Look-ahead guards: ABR audit (`abr_audit.py`) truncation / garbage-future test; EINT1 asserts label_day <= 20260206; prior-day values are `shift(1)` of the label-day table; atr_med20 is `shift(1)` of prior days' medians.
* Series are continuous (never reset at a session or day boundary): EMA, ATR, Supertrend, HMA state run through the whole back-adjusted 1-min history from 2023-02; bar windows (30-bar, 5-bar) count bars, not minutes, so gaps (empty minutes) are not padded.

## 3. Per-feature definitions

Notation: s = side (+1 long, -1 short), E = entry price (library space), lc = last closed 1-min bar, ATR14 = Wilder ATR14 of 1-min bars at lc (`thp_aux.py:wilder_atr` L29: seed SMA of first 14 TR, then (prev*13+TR)/14; TR = max(H-L, |H-prevC|, |L-prevC|)).

* **atr14 / atr_pts**: ATR14[lc], points. `abr_build.py` L142.
* **atr_ratio**: ATR14[lc] / atr_med20[lc]; atr_med20 = median of the 20 PRIOR label days' daily medians of 1-min ATR14 (`thp_aux.py` L205-211: groupby label day median, rolling(20, min_periods=3).median().shift(1)). Unsigned. `abr_build.py` L144.
* **sig_st1_dist_atr / sig_st5_dist_atr / sig_st10_dist_atr** (`abr_build.py` L191): s*(E - line)/ATR14[lc], line from `thp_aux.py:supertrend` L43-60 (`tf_state` L80). Algorithm: bu=hl2+3*ATR10, bl=hl2-3*ATR10; first valid bar: dir=+1 if C>=hl2 else -1; afterwards fu = bu if (bu<fu or prevClose>fu) else fu; fl = bl if (bl>fl or prevClose<fl) else fl; dir flips to -1 if dir=+1 and C<fl, to +1 if dir=-1 and C>fu; line = fl if dir=+1 else fu. st5/st10 run on epoch-aligned 5/10-min aggregates (MIN//g) and use the last completed group at each 1-min bar (group of lc if lc is its last minute else the previous group).
* **sig_st1_age / st5_age / st10_age** (`abr_aux.py:age_of` L16, `make_new` L66-68): per 1-min bar index, age[i] = age[i-1]+1 if dir[i]==dir[i-1] else 0; start 0. Side-independent. (A companion `sig_st1_rel` = dir*side exists; D7 can build "against" from it.)
* **sig_slope** (`thp_aux.py` L212-213, `abr_build.py` L187): s*((EMA20[lc]-EMA20[lc-5])/5)/ATR14[lc].
* **sig_kelt1** (`abr_build.py` L185): s*(E - EMA20[lc])/ATR14[lc].
* **sig_kelt3** (`abr_aux.py` L50-55): 3-min bars (MIN//3 groups), Wilder ATR14 and EMA14 (alpha 2/15, seeded at first 3-min close) on the 3-min series; value at the last completed 3-min group = (C3 - EMA14)/ATR14_3m, times s.
* **sig_hma_sp** (`abr_aux.py:hma` L30, L72-73; `make_new` L73): s*(HMA9-HMA21)/ATR14[lc]; NaN for the first n+int(sqrt n)-2 bars.
* **hma_slope** (`ei_feat.py` L27-30, L56): HMA21 of time_1m closes (points); s*(HMA21[bi]-HMA21[bi-1])/ATR14 (ABR atr14).
* **pb_speed** (`ei_feat.py` L21-26, L52-55): over the 30 time_1m bars ending at bi (inclusive): ext = max high (long) / min low (short); bs = bars since ext (first occurrence in the window, so ties give the older bar; bs=0 if ext is the last bar); pb_depth_atr = s*(ext - C[bi])/ATR14 (>=0 for a pullback); pb_speed = pb_depth_atr / max(bs,1). NaN for the first 29 bars. (sig_pb30_atr = same depth from the aux bars, no speed.)
* **htf daily table** (`ei_feat.py` L33-44): per label day from time_1m: open = first bar open, high/low = max/min over the whole ETH label day (18:00 ET prior evening to 17:00 ET), close = last bar close. atrd = rolling(14, min_periods=5).mean() of (high-low). p_* = previous label day row (`shift(1)`, so Monday uses Friday; holidays use the previous existing label day). For the day open the CURRENT label day's open (known at 18:00 ET).
* **htf_pd_pos**: s*((E - p_lo)/(p_hi - p_lo) - 0.5); prior day = previous ETH label day (18:00-17:00 ET), NOT the RTH session. `ei_feat.py` L65.
* **sd_pd_hi_atr / sd_pd_lo_atr**: s*(PDH - E)/ATR14, s*(PDL - E)/ATR14 (`abr_build.py` L170-180: structure level `sd_pd_hi` = s*(pdh-E); `ei_feat.py`: `sd_*_atr = sd_*/atr14`); PDH/PDL = previous label day ETH high/low (`abr_aux.py` L76-80). Positive = level lies in the profit direction. (Prior-day RTH 09:30-16:00 high/low are the separate sd_pdrth_*.)
* **htf_d_open_atr**: s*(E - day_open)/p_atrd (`ei_feat.py` L67).
* **htf_wk_open_atr**: s*(E - week_open)/p_atrd (L68); week = Mon-Fri block of the label-day dates, week_open = open of its first label day (Sunday 18:00 ET bar on a normal week); p_atrd = prior day's atrd as above.
* **htf_vwap_atr**: s*(E - VWAP_ETH[lc])/ATR14 (L69; `sd_vwap_eth` = s*(vwap-E)). VWAP_ETH = cumulative sum(vol*(H+L+C)/3)/cumulative sum(vol) from the label-day start (18:00 ET) to lc, vol = NQ 1-min traded volume from the L2 1-min table (`thp_aux.py:l2_minute_vol`; bars with no L2 volume get 0), NOT the exchange 1-min bar volume. Normaliser is 1-min ATR14, not daily ATR.

## 4. Missing / NaN handling

* Features are NaN (not imputed) when: fewer than the warm-up bars exist; the 30-bar/5-bar window spans a data gap (aux `okw`: window valid only if it spans <= w+10 minutes; used in rng/hi30/lo30/corr20, not in EMA/ATR/Supertrend/HMA); level or ATR missing; first hour range before 10:30; RTH gap before 09:30.
* In rules (`ei_cat.py:crank` L17-24): a NaN feature value gets rank NaN and is excluded from the history; masks T3/B3 are False for it, so the multiplier is 1 (signal kept, size unchanged).
* atrd NaN before 5 label days; atr_ratio NaN before 3 prior days.

## 5. TERCILE RULE: research vs shipped vs live chart

**Research (EINT1 group A/C catalogue, `code/eint1/ei_cat.py:crank` L17-24 and `feat_rules` L25-36).**
* Universe: the 47,131 library base-bracket trades of 11 books (`dipentry/trades_arm.parquet`, i.e. the THP trade index, label days 20230403..20260206, restricted to <=20260206). Sorted by (entry_ts, tid). These are each book's own stored standalone trades, NOT the lock-engine-filtered subset and not signals the book's own logic suppressed (not recorded). "Taken vs not taken" does not arise: every trade of the book counts, win or lose, including those the lock engine later would skip.
* Rank: for each trade, rank = bisect_left(prior sorted values of the SAME book, v) / n_prior = fraction of the book's earlier trades with a strictly smaller value. Computed only if n_prior >= 100 non-NaN values of that feature for that book (so the first 100 trades of a book get no cut and multiplier 1). Value is inserted into the history AFTER ranking (not including itself). Pooled over sides and sessions (per book only; no per-session or per-side split). Uses signal-time features only (no outcomes), so no label look-ahead.
* Cuts: B3 = rank < 1/3; T3 = rank >= 2/3; B10 < 0.1, T10 >= 0.9. skipBot3 -> multiplier 0 if B3; skipTop3 -> 0 if T3; sizeHi -> 1.5 if T3, 0.5 if B3, else 1 (lot-matched afterwards by dividing by the book's pre-20250630 mean multiplier).
* History BEGINS at the first trade of the universe (2023-04-03). The universe starts at the start of the X window; nothing earlier exists, so there is no pre-chart-start history other than what the research table holds: at 20260206 each book's history is its full 2023-04..2026-02 trades (HM 4,156, KB 5,500, PE 5,361).

**Shipped numeric thresholds (`out/missed/eint1_policy_candidate.txt`, `ei_policy.py:thr` L9-14).** NOT the expanding rank: np.nanquantile of the book's feature over the trailing 12 months (label_day >= cut minus 12 months .. cut) of ALL its trades in the universe, pooled over sides and sessions, NaN dropped, cut = 20260206. Verified by recomputation: HM sig_slope q33 = 0.0942 (shipped 0.09425, n=1,833); KB sig_st1_dist_atr q67 = 3.2988 (3.299, n=2,565); PE q33/q67 = 1.5216/2.649 (1.522/2.649, n=2,515); HM sig_st1_dist_atr q33 = 2.787 (shadow). For reference, full-history thresholds: HM slope q33 0.096, KB st1dist q67 3.296, PE 1.543/2.641, pre-HOLD (<=20250630): 0.0988, 3.298, 1.546/2.644. The thresholds are stable to ~1-3%, so which version D7 uses changes only the borderline signals.

**What a live chart can compute.** A chart sees only the signals it has itself recorded since its start (or a bundled history file). To reproduce the research it needs (a) the prior sorted history of the book's own signals, with the identical feature definitions (section 3), including signals the chart skipped or never traded (the rank must not depend on its own skip decisions: rank every signal the standalone book would take, before filtering), (b) n_prior >= 100 per book, else multiplier 1, (c) all sides and sessions pooled per book, (d) with no history at chart start, the first 100 signals are unranked. The shipped alternative (fixed thresholds from the 12-month window) needs only the three printed numbers per rule, no history. The two differ in what is cut at the margin, and they are NOT the same rule: the study scored the expanding rank. State in v1.0c which one is live; if the fixed numbers are used they must be refreshed (nightly refit `ei_nightly_refit.py`) and carry the cut date.

## 6. Verification by recomputation (tie-out)

30 random signals (random_state=7 sample of the 47,131 EINT1 feature rows, all <= 20260206). Independent re-implementation from the capped bars (aux_bar.npz for sig_*, atr, atr_ratio, sd_pd, VWAP; time_1m ld<=20260206 for pb_speed, hma_slope, daily HTF) using only the definitions above; compared to the stored values:

| feature | max abs diff | status |
|---|---|---|
| sig_st1_dist_atr | 1.0e-07 | TIES |
| sig_st1_age | 0 | TIES |
| sig_slope | 6.1e-09 | TIES |
| htf_d_open_atr | 0 | TIES |
| htf_wk_open_atr | 0 | TIES |
| sig_kelt1 | 1.1e-07 | TIES |
| sig_hma_sp | 5.6e-08 | TIES |
| atr14 | 9.5e-07 | TIES |
| htf_pd_pos | 0 | TIES |
| sd_pd_hi_atr | 2.6e-06 | TIES |
| htf_vwap_atr | 1.3e-06 | TIES |
| pb_speed | 8.2e-08 | TIES (on time_1m bars) |
| hma_slope | 4.5e-08 | TIES (on time_1m bars) |
| bar_age_s | 0 | TIES |
| atr_ratio (extra) | 2.0e-07 | TIES |
| sig_st5/st10 dist (extra) | 4.7e-07 | TIES |
| sig_st5/st10 age (extra) | 0 | TIES |

Not recomputed (code read only): **sig_kelt3 UNVERIFIED by recomputation** (3-min aggregation; definition from `abr_aux.py` L50-55), sd_pd_lo_atr (symmetric to sd_pd_hi_atr), htf_on_*, htf_gap_*, htf_fh_atr, htf_tr20/50. Note: pb_speed and hma_slope computed on the aux bars (instead of time_1m) differ by up to 0.12 and 0.02 in a few signals because the two bar sets differ in o/h/l by a tick or more; D7 must use tick-built 1-min bars for those two (or accept the difference).
The thresholds in section 5 were also recomputed from the table (4 rules, ties to the printed digits).

## 7. Caveats

* The sig_* "signal" features are generic proxies identical for all books (ABR comment: the engines' own internals are not on disk), so "Keltner" and "Supertrend" are the research's own generic definitions, not the live KB/PE/ST engine indicators; D7 must compute them as above, not read the engine's.
* The drawdown-first line at live lots on the one-convention engine (last item of the order) is not part of this spec task (EF-1 scope = feature definitions); not done here.
* Output location of the tie-out: `l2vast/ds3/out/eint1spec/` (the ds3 `out/` tree).
