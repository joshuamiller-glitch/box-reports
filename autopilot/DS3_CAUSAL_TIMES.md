# DS3_CAUSAL_TIMES - when is each day-level feature known (ET)? Spec for all future agents (LEAKAUDIT, 2026-10-30)

Read-only audit product. Source: code reading of l2vast/ds3/code/** (thp_dayreg.py, thp_build.py, abr_build.py, abr_aux.py, dv2a_labels.py, e2f_build.py, e2_rules.py, ei_feat.py, b_labels.py, b_lib.py, stk_a_lib.py, op_build.py) and the feature dictionary. No outcome data after 2026-02-06 was opened.

## 0. The one rule
A day-level number may be used as a gate, table key, feature, stratifier or scope for a trade (or session) ONLY if the trade's ENTRY SECOND (or the decision second for in-trade rules) is at or after the "known at" time below. Before that time use the PREVIOUS label day's value (or NaN). A tag that summarises the overnight range, the first hour, the RTH session or the day is NEVER a key for a trade that starts before the window it summarises is complete.

Label day D = 18:00 ET (D-1 calendar) .. 17:00 ET (D). Session of the entry minute (ET): ASIA 18:00-02:00, LONDON 02:00-08:30, PRE 08:30-09:30, NYAM 09:30-12:00, NYPM 12:00-15:00, CLOSE 15:00-16:54. "Bar-start minute m" completes at m+1:00 (a 1-min bar that starts 09:29 is complete at 09:30:00).

Correction to the UF-LOSS description: vol_tag_today / vol_tag_entry_day is NOT a summary of the regular session. thp_dayreg.py:41-44 builds it from the OVERNIGHT range (bar-start 18:00 .. 09:29) of the label day divided by the prior-20-day median overnight range (<0.85 lo, >1.15 hi). It is complete at 09:30:00 ET. It is therefore look-ahead for ALL of ASIA, LONDON and PRE, and worst for ASIA entries (48-100% of the summarised window is still in the future at entry; LONDON 6-48%; PRE up to 6%, and the entry hour itself is inside the window). The trade's own MFE/MAE path lies inside the tag window, so the leak is outcome-correlated by construction.

## 1. Causal recipe for the vol tag (use this, nothing else)
```
vol_tag_causal(entry_ts) = vol_tag_prev(label_day)  if entry minute-of-day (ET) < 09:30 or >= 18:00   (sessions asia, london, pre)
                         = vol_tag_today(label_day) if 09:30 <= entry minute < 18:00                 (nyam, nypm, close)
missing (-1) -> mid (1) as EXP1-loss / UF-LOSS C3-C4 do.   Session-code shortcut: sess_entry <= 2 -> prev, else today.
```
The THP/ABR feature store column `vol_tag` (data/dp*/ldp*/entry) already follows this (thp_build.py:161, abr_build.py:157) and is safe. The trade-level columns `vol_tag_entry_day` (trade_index.parquet, wf/c3/cache/tidx.parquet) are `vol_tag_today` aliases and are NOT safe for sess_entry <= 2. Known quirk: when the label day is missing from day_regime, thp_build.py:161 returns 0 (vol_lo) for rows at/after 09:30 instead of -1 (does not occur in 2023-04..2026-02).

Persistence check (day-level only, no P&L): over 737 label days with both tags defined (2023-04-03..2026-02-06), vol_tag_prev == vol_tag_today on only 42.3% of days; P(today lo | prev lo) = 0.45 vs unconditional P(lo) = 0.36. A causal key therefore re-assigns ~58% of days to a different cell; effects that live in the today-tag cells are expected to shrink toward zero.

## 2. Availability table - every day-level feature (ET)
Safe-from = earliest entry/decision time. "start" = label-day start 18:00 ET of D-1 (prior-day values are complete by 17:00).

### 2a. day_regime.parquet (code/thp/thp_dayreg.py; same file in code/abr/)
| column | definition | known at | safe for entries from | status |
|---|---|---|---|---|
| prior_rth_range | prior label day RTH 09:30-16:00 H-L | 16:00 D-1 | start | safe |
| prior_day_range | prior label day full H-L | 17:00 D-1 | start | safe |
| prior_rv_rth | prior day RTH 1-min log-ret std (bps) | 16:00 D-1 | start | safe |
| esnq_corr20d | corr of daily ES/NQ close-to-close returns, 20 label days, shift(1) | 17:00 D-1 | start | safe |
| esnq_corr_prev1m | prior day RTH 1-min ES/NQ corr | 16:00 D-1 | start | safe |
| vix_prev | VIX close of the calendar day before the label day's date | 16:15 D-1 | start | safe |
| vix_terc_exp | expanding tercile of vix_prev, prior days only, >=60 days else 'na' | 16:15 D-1 | start | safe |
| on_range_med20 | median of prior 20 label days' on_range (min 10) | 17:00 D-1 | start | safe |
| on_range | H-L of bars starting 18:00..09:29 | 09:30:00 D | 09:30 | unsafe before 09:30 |
| rv_on | std of 1-min log returns 18:00..09:29 | 09:30:00 D | 09:30 | unsafe before 09:30 |
| vol_tag_today (= trade_index.vol_tag_entry_day) | tercile of on_range / on_range_med20 | 09:30:00 D | 09:30 (nyam, nypm, close) | LOOK-AHEAD for asia, london, pre |
| vol_tag_prev | previous label day's vol_tag_today | 09:30:00 D-1 | start | safe |
| fh_range | 09:30-10:30 H-L | 10:30:00 D | 10:30 | unsafe before 10:30 |
| prev_daytype | previous label day type (trend/range/reversal) | 16:00 D-1 | start | safe |
| daytype_EXPOST | this day's own type (needs 16:00 close) | 16:00 D | never a feature | analysis label only |

### 2b. dv2a/day_labels.parquet (code/dv2a/dv2a_labels.py; used by DV2A-D audits, audit_lib.day_labels)
| column | known at | note |
|---|---|---|
| ropen, rh, rl, rclose, day_move, day_rng, nrth | ropen 09:30; rclose/day_* 16:00 D | EX POST for any entry before 16:00 |
| fh_hi, fh_lo, fh_close, fh_rng, fh_move, fh_wide, fh_rev | 10:30 D | safe from 10:30 only (STK_A/B/D4 respect this) |
| on_move | 09:30 D | safe from 09:30 |
| daytype | 16:00 D | EX POST; do not gate on it (stk_b REFS and dv2a/c/d by_daytype tables use it descriptively only) |
| prev_daytype, med_absmove, med_fhrng, rv20 | start | safe |
| vix_prev | 16:15 D-1 | safe |
| vix_terc, rv_terc | start | terciles use FULL-WINDOW cut points (in-sample, descriptive). For gating use vix_terc_exp |
| fomc | schedule | list OK (23/23 match the verified calendar 2023-04..2026-02) |
| nfp, cpi, event | schedule in principle | PROXIES: nfp = first Friday; cpi = day with the largest 08:30-08:31 range (r830) among Tue-Thu 10th-16th. Against standS/event_calendar_core.csv (VERIFIED): CPI 27/34 proxy days correct (7 wrong, 6 missed); NFP 26/35 correct (9 wrong, 7 missed). The cpi proxy is chosen with the REALISED 08:30 range = look-ahead selection for asia/london/pre trades of that day. Use event_calendar_core.csv (as EINT2 and DV2C do) |
| r830 | 08:32 D | helper for the cpi proxy; never a feature |

### 2c. Feature-store entry/path columns (THP data/dp*, ldp*; ABR data/entry)
| column | known at | note |
|---|---|---|
| vol_tag | row time: prev before 09:30, today from 09:30 | safe (row-level) |
| on_ratio (ABR) | same rule as vol_tag | safe |
| on_ratio_sofar | each bar close, outside RTH only (NaN 09:30-18:00) | safe (running ETH range / prior-20 median) |
| on_ratio_prevday, rg_prior_*, rg_esnq_*, rg_vix_prev, rg_vix_terc, prev_daytype | start | safe |
| rg_rv_on | 09:30 | NaN before, safe |
| rg_fh_range, fh_range, fh_over_atr, htf_fh_atr | 10:30 | NaN before, safe |
| cal_wd/monthend/opexweek/opexday/fomc | schedule | safe |
| cal_nfp, cal_cpi, cal_event | schedule | proxies, see 2b (replace by verified calendar) |
| d_sess_ahead/behind, sd_sess_hi/lo | each bar close | running ETH extremes, safe |
| d_rth_*, sd_rth_*, z_vwap_rth | each bar close, from 09:30 | NaN before 09:30, safe |
| d_or_*, sd_or_* | opening range of the CURRENT session block (ASIA 18:00, LONDON 02:00, NY 09:30) complete 30 min after the block start | NaN until complete, safe |
| z_vwap_eth, sd_vwap_eth | each bar close | safe |
| pdh/pdl/prh/prl (sd_pd_*, sd_pdrth_*) | start | safe |
| atr_ratio, atr14, rng30_over_atr | bar close; medians of prior 20 days | safe |
| stk_real_day_pts, stk_n_exited_day, stk_n_entries_day, own_real_day_pts | each decision second (only exits already closed) | safe if exits are counted by closed_ts <= ts |
| mins_to_rel | clock | safe |

### 2d. EINT1 htf_* (code/eint1/ei_feat.py) - verified causal at the signal second
| column | known at | note |
|---|---|---|
| htf_tr20, htf_tr50, htf_pd_pos(_raw), htf_pd_range_atr | start (prior label day, shift(1) incl. ATRd) | safe |
| htf_d_open_atr | first trade of the label day (18:00:0x) | safe; entry price vs label-day open |
| htf_wk_open_atr | Sunday 18:00 open of the label week | safe |
| htf_gap_eth = side*(label-day open - prior close)/ATRd | first bar of the label day (18:00:0x) | safe for all sessions: it uses the 18:00 Globex open, not the 09:30 open |
| htf_gap_rth = side*(09:30 open - prior 16:00 close)/ATRd | 09:30:00 (open print) | masked to NaN unless entry minute >= 09:31 (ei_feat.py:72-77) - safe |
| htf_on_range_atr, htf_on_pos | running ON range, frozen at 09:30 | safe (cummax capped at bars ending <= 09:30) |
| htf_vwap_atr, htf_on_ratio, htf_fh_atr | bar close / running / 10:30 | safe |

### 2e. EINT2 day table (code/eint2/e2f_build.py; gating in e2_rules.derive)
| column | known at | gating in code |
|---|---|---|
| on_ratio | 09:30 | NaN unless mod >= 571 (09:31) |
| gap_r (09:30 open - prior 16:00 close)/med20 RTH range | 09:30 | NaN unless mod >= 571 |
| or30_ratio, t_or30_ratio, esag30 | 10:00 | mod >= 601 |
| or60_ratio, t_or60_ratio, fhd_r, esag60 | 10:30 (bar 10:29 close) | mod >= 631 |
| vix_terc (expanding), t_corr, prev_dt | start | none needed |
| wd, monthend(3), monthstart, opexday, quadday, opexweek, quadweek, hol_*, early_close, ev_fomc/cpi/nfp/any, ev_post_* | schedule (events from verified standS/event_calendar_core.csv; early_close/hol derived from the bar store but schedule-known) | none needed |

### 2f. Stack / session / sizing day-flags
| flag | known at | applied to | status |
|---|---|---|---|
| STK_B FH60_x, FH30_x, OVL, FLIP, ESDIS (b_labels.py) | 10:30 | entries 10:30-18:00 only (b_lib 'post') | safe (B02, A/B/F rules) |
| STK_B ON_05/07/085 (overnight range < x * prior-20 median) | 09:30 | entries 10:30-18:00 only (B02 = ON_085) | safe (SZR and STK_F reuse the same mask) |
| STK_A range-day flag (first-hour range < thr x prior-20 median) | 10:30 | entries 10:30-17:59 use today; entries 18:00-10:29 use previous day (stk_a_lib.row_mask) | safe |
| DV2D D4 days (first hour opposes overnight move, > m x median) | 10:30 | trades start 10:30 (bar_at(ld,630)) | safe |
| P_quiet (TA/pquiet_series.parquet), per session s = 0 ASIA 18:00, 1 LONDON, 2 NY 09:30 | the session's open minute (t_open_min) | ta_lib/ta_tb/tr4/tr1/pro2/pb4/pb2: mapped per bar/session | safe (truncation audit 120 checks, 0 mismatches); sz_lib.pq_series takes only s == 2 and applies it to the WHOLE label day: UNSAFE for asia/london/pre P&L of that day (D3SZR A-cells) |
| T-OPEN preopen_0929 table (asia_dir, london_dir, on_range_atr, gap_pre_close_atr, pq_*) | 09:29 | NY-open programs (trades from 09:30) | safe |
| T-OPEN/T-CLOSE morning_1430 table (daytype dt14, range_rel, gap_atr, vwap_rel_1429 ...) | 14:30 | T-CLOSE (trades from 14:30) | safe; 'daytype' there is the 14:30 as-of type, not the full-day type |

## 3. Banned / handle-with-care list
* vol_tag_today, vol_tag_entry_day, rv_on, on_range, fh_range, fh_*, day_rng, day_move, rclose, daytype, daytype_EXPOST, r830, vix_terc (day_labels, full-window cuts) as keys for earlier sessions.
* Any "tercile of the full sample" cut point (day_labels vix_terc/rv_terc; ls_sel.vol_tercile cut fixed on <=20250630 trades; tl_r8/equal_risk WF-window VIX cuts): descriptive only.
* Day-level multiplier from a forecast made at the NY open applied to P&L earned before it (sz_lib.pq_series, s == 2).

## 4. How to prove it (add to every program with a day key)
1. Key-time unit test: for each trade assert key_available_time(key) <= entry_ts; log the share of trades whose key would be a day-level value from a later time.
2. Day-table truncation test: the THP/ABR leak_test (thp_audit.py: 346 cuts, 46,364 feature checks, 0 mismatches) noises BAR data after the cut but loads day_regime.parquet unmodified (thp_build.py: `dr = C.DR.loc[...]`), so it cannot catch a mis-gated day column. Add: recompute the day table from bars truncated at the cut and compare every day-derived column of every trade entered before the cut.
3. Shuffled-key placebo: permute the day key across label days within the same session; a real causal effect survives only if the real key beats the shuffles; a leaky key beats them by construction.
