# DIS_B_PREREG: DIS-B GLOBEX PRE-MARKET STRUCTURE BOOKS (S4a, 2026-11-04; written and hashed BEFORE any outcome statistic of any DIS-B cell)
Research only (Shadow), no PASS claims. Directive: lead 'DIS-B' (USER STANDING RULE: next untested proposal). Cap 2026-10-31 (label days <= 20261030 in the minute table). New windows only (L1M, L3M, L6M, HOLD, MID, PRE, X').
Code (hashed): code/disb/disb_events.py sha256 eeacf6290e04b421ac3704536f07299d20cb47b621a4d1f06ce2a7d41c134d4c ; code/disb/disb_lib.py sha256 36dd91d4fe7ffe4b640452e609a9a6326e4e152f1d1db8c4bd5b1e98b10a8c5d. Events: /mnt/l2/l2vast/ds3_disb/events.parquet (42287 events, 61 variants, 944 label days) built only from /mnt/l2/l2vast/ds3_fade/minute.parquet (NQ 1-min back-adjusted bars with volume, ATR14 of the last closed 5-min bar). dead_lookup before: grep premarket / pre_market / pmh / pm_hi / pm_range / release0830 -> no hits in DEAD_CELLS.csv (only two ZONES3S1 'B1_GlobexOpen' zone-line cells, a different object).
## Books
Pre-market (PM) = 04:00-09:30 ET (label day, bar-open minute 240-569). PMH/PML/PM mid = extremes of PM bars; PM VWAP = volume-weighted typical price from 04:00 (running for pre-market entries, final value at 09:30 for NY-AM entries); relvol = PM volume / median of the previous 20 label days (>= 10 earlier days), relrng likewise for the PM range; imb = sum(sign(close-open) x volume) / sum(volume) over PM (1-min bar-sign volume imbalance, a stated proxy: no aggressor data used); gap = 09:30 open - prior RTH close (bar 15:59 close of the previous label day); release move = close of the 08:34 bar - close of the 08:29 bar (08:30 data release, 5-minute reaction). Every value is known at the signal bar close; relvol, relrng, imb, final PM VWAP exist ONLY for entries at or after 09:30 and are NaN for pre-market entries.
Two separate session families: N = entries after 09:30 (session label nyam, signals 09:31-10:30), P = pre-market entries (session label pre, signals 05:00-09:20 as listed; every position flat by 09:25 ET via the per-row time stop cap). Signal = 1-min bar close; first fill about 1 s later; slices 1 lot / 2 s; stops and targets resting; LIVE costs (stop 2.45 pt worse, market exit 0.80, fee 0.242 pt per lot round trip) = FadeHarness / MultiHarness live fill model.
## Event variants (61; thresholds fixed here, none tuned)
- N_BRK_x0.0_w30
- N_BRK_x0.0_w60
- N_BRK_x0.25_w30
- N_BRK_x0.25_w60
- N_GAPFILL_t31_g0.5_any
- N_GAPFILL_t31_g0.5_hi
- N_GAPFILL_t31_g0.5_lo
- N_GAPFILL_t31_g1.0_any
- N_GAPFILL_t31_g1.0_hi
- N_GAPFILL_t31_g1.0_lo
- N_GAPFILL_t35_g0.5_any
- N_GAPFILL_t35_g0.5_hi
- N_GAPFILL_t35_g0.5_lo
- N_GAPFILL_t35_g1.0_any
- N_GAPFILL_t35_g1.0_hi
- N_GAPFILL_t35_g1.0_lo
- N_GAPGO_t31_g0.5_any
- N_GAPGO_t31_g0.5_hi
- N_GAPGO_t31_g0.5_lo
- N_GAPGO_t31_g1.0_any
- N_GAPGO_t31_g1.0_hi
- N_GAPGO_t31_g1.0_lo
- N_GAPGO_t35_g0.5_any
- N_GAPGO_t35_g0.5_hi
- N_GAPGO_t35_g0.5_lo
- N_GAPGO_t35_g1.0_any
- N_GAPGO_t35_g1.0_hi
- N_GAPGO_t35_g1.0_lo
- N_IMB_cont_th0.1
- N_IMB_cont_th0.2
- N_IMB_rev_th0.1
- N_IMB_rev_th0.2
- N_PMV_cont_a0.5
- N_PMV_cont_a1.0
- N_PMV_rev_a0.5
- N_PMV_rev_a1.0
- N_PO_brk
- N_PO_fade
- N_RCL_W10
- N_RCL_W20
- N_REL_cont_m0.5
- N_REL_cont_m1.0
- N_REL_rev_m0.5
- N_REL_rev_m1.0
- N_VWAPF_k1.0
- N_VWAPF_k1.5
- N_VWAPF_k2.0
- P_BRK_x0.0
- P_BRK_x0.25
- P_LON_brk
- P_LON_fade
- P_PO_brk
- P_PO_fade
- P_RCL_W10
- P_RCL_W20
- P_REL_cont_m0.5
- P_REL_cont_m1.0
- P_REL_rev_m0.5
- P_REL_rev_m1.0
- P_VWAPF_k1.5
- P_VWAPF_k2.0
Definitions in code: N_BRK x w = first 1-min close beyond the final PMH+x ATR (long) / PML-x ATR (short) within w minutes of 09:30 (trend, one per side per day); N_RCL W = bar high >= PMH+0.1 ATR (low <= PML-0.1 ATR) then a close back inside within W bars, entry at the reclaim close (fade, stop beyond the excursion extreme, one per side); N_VWAPF k = close >= PM VWAP + k ATR (<= -k), 09:35-10:30, fade toward the PM VWAP; N_GAPGO / N_GAPFILL = gap >= g ATR at the 09:31 (t31) or 09:35 (t35) close, with relvol condition any / >= 1 (hi) / < 1 (lo), trade with the gap (trend) or against it with the prior RTH close as the vwap-type target (fade); N_IMB cont/rev = |imb| >= th at 09:31; N_PMV cont/rev = |PM VWAP - prior RTH close| >= a ATR at 09:31; N_REL cont/rev = |release move| >= m x ATR(08:30) at 09:31; N_PO brk/fade = 09:15-09:30 range break (trend) or failed break (fade) within 09:30-10:00/10:30; P_BRK x = first close beyond the running PM extreme of EARLIER bars (+x ATR), 05:00-09:20, trend; P_RCL W = failed break of the running extreme, fade; P_REL cont/rev m = 08:34-bar close signal; P_PO brk/fade = 09:00-09:15 range, entries 09:15-09:20; P_VWAPF k = fade of a >= k ATR stretch from the running PM VWAP, 06:00-09:20; P_LON brk/fade = London 02:00-04:00 range break / failed break during 04:00-09:20.
## Shapes (per event variant; trades_of in disb_lib.py)
fade events: target in {PM VWAP (or prior RTH close for gap-fill) , PM mid, R1} x stop buffer {0.25, 0.5, 1.0} ATR beyond the signal-bar/excursion extreme x time stop {30, 60, 120} min; trend events: target in {R1, R2} x same buffers x time stops (stop at the broken level - buffer). Filters: stop distance between 0.3 and 3.0 ATR; target >= 0.5 stop for vwap/mid; one trade at a time per book (harness no-overlap); lots = min(2,400 / (stop x 0), 6). Cells = variant x shape = 61 variants -> 1,386 cells; cells need >= 100 trades to be ranked.
## Procedure and rules
Stage 1: all cells valued with MultiHarness (live fill model), pooled windows L1M, L3M, L6M, HOLD (with HOLD_dropH shown separately), MID, PRE, X'. Stage 2 (candidates = n >= 100, L3M > 0, L6M > 0, HOLD > 0): 100 placebos per cell (random side, random time, shuffled day by the harness), regime switch R_F40 (CAL) with the same switch in 2023-25, stack marginal at 0.5x and 1x with the carrying weeks dropped (gate_v3 constants, PRE weeks 2025 W06-09), fade_row rows. Family test over ALL cells tried (max-T, >= 100 worlds, random-side and shuffled-day, stats HOLD mean and L6M Calmar) and BH q; n_tested registered in FADE_NTESTED (slice FADE_DISB). Labels: TOLERANT / NOW-ONLY / REGIME / CONDITIONAL as in FADE rows; LEAD requires family p <= 0.10 (max-T) and a positive stack gain carry-dropped; anything else is REGIME, CONDITIONAL or FRAGILE. Nothing is a lead on one week or one month. Ledger program DIS_B (dead_lookup append after); rows autopilot/FADE_ROWS_DISB.md; interim tables in autopilot/DS3_DISCOVER2.md section DIS-B.
Pre-market anchors (pm_hi, pm_lo, pm_mid, pm_vwap, relvol, relrng, imb, pdc_rth per label day) are saved in /mnt/l2/l2vast/ds3_disb/pm_anchors.parquet and registered with FA.register_anchor for the fade engine (arrays aligned to the minute table rows).
