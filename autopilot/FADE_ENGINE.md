# FADE ENGINE (T-FADE, BASE-4) - NQ, 1-s path + 1-min bars, causal

Code: l2vast/ds3/code/fade/fade_anchors.py (anchor library), fade_engine.py (triggers, shapes, simulator, presets).
Scripts/tests: /mnt/l2/l2vast/ds3_base4/ (fe_tie.py, fe_audit.py, fe_recon*.py, fe_zone.py, fe_worked.py).
Research cap 2026-10-31 (CUT_LD 20261031). Bars: back-adjusted NQX 1-min (to 2026-10-16) + tick-built NQ 1-s path (to 2026-10-30), same price frame. Levels leave the library as DISTANCES (stop_pts/tgt_pts), not absolute prices, because this frame differs from the library G2 frame by a constant offset.

## 1. Anchor library (FA.build / build_from_bars; ~109 arrays, value known at the bar close)
- Label day rolls 18:00 ET (weekend -> Monday). Sessions: asia 18:00-02:00, london 02:00-09:30, nyam 09:30-12:00, nypm 12:00-16:55.
- VWAP = sum(v*tp)/sum(v), tp=(h+l+c)/3. SIGMA = volume-weighted std of tp about the VWAP: sigma^2 = sum(v*tp^2)/sum(v) - vwap^2. Bands vwap_<s>+-1, +-1.5, +-2 (sigma units).
- VWAP convention: session-start VWAPs (asia, london, nyam, nypm) and day VWAP (from 18:00) are reset at session start, ET-aware. The library HM VWAP resets at a fixed UTC-4 boundary; kept as vwap_lib for comparison (differs in winter).
- Levels: prior-day H/L/close/mid (RTH pd_r_*, Globex pd_g_*), overnight on_hi/on_lo (18:00-09:30), asia_hi/lo, london_hi/lo, IB30/IB60 per session, OR5/15/30, session open/hi/lo/mid, prior-week pw_hi/lo, gap_open (09:30 gap edge; NaN before 09:30), rn_dn/rn_up (00/50 round numbers), atr60.
- rth_open was REMOVED from exports (look-ahead found by the truncation audit; see 5).
- Hook: FA.register_anchor(name, arr). Zone lines: FA.add_zone_lines(A, names) adds zl_<name> (level, last formed <= bar close, shifted into this frame) and zlf_<name> (1.0 if untouched at bar start) for kijun1h, PDmid, CRT4h, KCup4h, camH3, OTE705/OTE79/OTE62 from poi_store_redo/streams. CAVEAT: frame shift is (NQ tick close - library SC) at formation, approximate near rolls; Z1 to review.

## 2. Triggers (all return DataFrames ld, sec(=1-min close boundary), side, anchor, trigger, idx)
trig_break_reclaim(A,hi,lo,window,W,X) (generic wick-through then close back within W bars, excursion >= X; Mancini failed breakdown/breakout = W 15, X 5 etc.), trig_touch_reject (W=0, level as of PREVIOUS bar), trig_failed_break (close beyond, next close back), trig_exhaustion(N, prox_atr), trig_stretch(vwap, k ATR), trig_tod_stretch(sess,k,lookback=20 prior label days median), trig_external(A,sec,side,ext) = hook for S4b delta-divergence / L2-absorption triggers (supply sec/side; shapes/sim are shared).
Census (>= 2023-04, touch/other counts total/long): touch_reject vwap_nyam +-1s 1702/850; touch_reject prior RTH H/L 499/214; failed_break prior RTH 538/219; break_reclaim overnight W60 537/252; Mancini X5 W15 prior RTH 517/216; exhaustion N4 IB30 599/277; stretch k2 ATR 1616/794; tod_stretch k1 NY-AM 1002/505.

## 3. Trade shapes (make_trades)
stop = beyond signal-bar extreme + buf*ATR60 (0.25-1.0), stop_pts measured from the signal-bar close. Targets: vwap / mid / ib_opp / R (0.5-2). tstop_s 900/1800/3600/7200 capped at flat 16:55. half_pts scale-out at VWAP (scale_frac). One trade per (ld, session, anchor, side) (anchor_id = anchor|trigger). lots 1-2, risk_usd for equal-$-risk. Output schema = ZL-2 FadeHarness: sec, side, stop_pts, tgt_pts, half_pts, tstop_s, flat_et='16:55', anchor_id, instrument='NQ', lots, session, shape, ld. NOT built: break-even move after the half exit; absolute stop_px/tgt_px/half_px (distances from the first fill are what the harness converts; absolute option not emitted because of the frame offset).

## 4. Simulator and live fill model
simulate(tr,P,mode='harness') replicates ZL-2 MultiHarness NQ model: signal at 1-min close B, fills from kfirst = last print second <= B+1s, 1 lot per 2 s averaged, resting stop (slip 2.45) first, target nominal (needs k>k0), time exit 0.80, fee 0.242/side-lot. Legacy simulate_lib kept (close of decision second + 1 tick). Reconciliation vs FadeHarness: exit type 99.86%, net 99.9% identical (plain), 100% (scale-out). The legacy convention disagreed (90.9% exit type, mean -0.62 pt) so it is NOT the default.

## 5. Tests
- Tie-out vs CAL nyam_books.py (presets preset_VWAPF / preset_ONRTH / preset_ORBF; same trades): VWAPF 100%, ONRTH 98.7%, ORBF 98.4% of the study lists; residual = roll-day/frame effects and dates after 2026-10-16 (beyond NQX bars).
- Causality truncation audit (100 rows, truncate bars at the decision bar, recompute, compare ~11,000 values): first run 65/100 mismatching (rth_open look-ahead) -> removed -> 0 mismatches.
- Worked rows (independent recompute from raw bars):
- label 20231020 SHORT signal bar closes 09:37 ET: independent NY-AM VWAP 14085.50, sigma 9.80, band 14095.30; bar high/low/close 14095.75/14085.50/14093.25 -> touch-and-reject yes; stop = extreme +/- 0.5 ATR(60) = 6.58 pt, target = distance to the (bar-included) VWAP 6.97 pt; engine stop 6.58 / target 6.97; simulated: first fill 14096.00, exit type 0 (0 stop 1 target 2 time) at 09:37:18 ET, net -9.27 pt -> **MATCH**
- label 20230817 LONG signal bar closes 09:44 ET: independent NY-AM VWAP 14425.54, sigma 13.10, band 14412.44; bar high/low/close 14425.75/14408.50/14413.75 -> touch-and-reject yes; stop = extreme +/- 0.5 ATR(60) = 8.82 pt, target = distance to the (bar-included) VWAP 11.22 pt; engine stop 8.82 / target 11.22; simulated: first fill 14409.00, exit type 0 (0 stop 1 target 2 time) at 09:44:22 ET, net -11.51 pt -> **MATCH**
- label 20250624 SHORT signal bar closes 09:40 ET: independent NY-AM VWAP 19868.93, sigma 9.56, band 19878.49; bar high/low/close 19881.25/19866.00/19878.00 -> touch-and-reject yes; stop = extreme +/- 0.5 ATR(60) = 8.22 pt, target = distance to the (bar-included) VWAP 8.72 pt; engine stop 8.22 / target 8.72; simulated: first fill 19883.25, exit type 0 (0 stop 1 target 2 time) at 09:41:11 ET, net -10.91 pt -> **MATCH**
- ALL worked rows MATCH

## 6. Known limits
No break-even after half exit; one-per-anchor logic tested on presets only (harness reentry='once' not exercised); exhaustion, Mancini, tod_stretch, failed_break validated by causality audit and census only, no tie-out reference; zone-line frame offset approximate; no PASS claims, no edge claim: this is tooling.

## 7. Gap closing (2026-11-04 follow-up)
- Break-even after the half exit: make_trades(scale_vwap=True, be_after_half=True) writes be_half=1.0; the simulator moves the remaining leg's stop to E1 from the second after the half limit fills (stop slip still applies). Test: 253 scaled trades, 91 changed exits, mean net of scaled trades 13.09 -> 13.25 pt; unscaled rows identical. FadeHarness does NOT have it yet (ZL-2: queued, will add a be_half column; until then harness scale-out is no-BE).
- one_per_anchor and reentry='once' tested in FadeHarness against an independent re-implementation of its rule: exact (469/469 and 472/472, same sets). Harness key pools both sides; make_trades(anchor_side=True) appends |L or |S to anchor_id.
- Frame: harness SC is the library G2 frame, 3700-3732 pt above the NQ tick path (22 distinct per-contract-segment offsets). FE.frame_offset(sec) and FE.to_harness_frame(tr) emit stop_px/tgt_px/half_px in the harness frame (offset at B+1 s). px mode runs through derive_levels; 5 of 480 rows already through are dropped; exit type differs from pts mode on 7% (structural levels vs distances from first fill). Default remains pts.
- O7: MultiHarness honours per-row tstop_s (NQ path multi_harness.py lines 97-98; flat cap line 77; non-NQ lines 121-122) per ZL-2.
- Census: autopilot/FADE_CENSUS.md.
- UPDATE (ZL-2, same day): be_half is now live in FadeHarness (NQ only; set be_half=1.0 together with half_pts or half_px). ZL-2's tie-out to this engine is exact on 600/600 rows at 1 lot, with and without BE (84 exit types change). At 2 or more lots the harness fills both half legs at the first fill with no 2-s slice drift, so it is about +0.20 pt per trade more favourable than this engine (8.64 vs 8.44 scaled pts): compare at 1 lot. fh.anchor_shift_placebo(build, n, lo=10, hi=80) is also available. I did not re-run this tie-out myself.
