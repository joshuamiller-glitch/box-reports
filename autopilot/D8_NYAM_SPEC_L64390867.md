# D8_NYAM_SPEC_L64390867: hand-verified coding spec, NY AM book L64390867.BRF80_40 (time_m_20 bars, VWAP anchored at 08:30 ET, band break k = 1.0, LONG only, stop 80 / target 40 points)

Written 2026-11-24 by a relay sub-agent (not typed by Josh). Order: Josh 13:26 MT 2026-11-24 via autopilot/DIRECTIVE_20261124_2026Z_JOSH_NYAM_WEIGHTED_NINE_FIT_AND_CODE_NOW.md item 5 (inbox file 20261124_2026Z_Josh-NYAM-weighted-nine-fit-and-code-now.md). Information only: no engine file edited, nothing queued, nothing live, no spend, nothing deleted. This page is the hand-verified replacement for the generic block AUTO:BOOK:L64390867 in autopilot/D8_BUILD_SPEC.md (labelled "GENERIC AUTO BLOCK, not hand-verified"; that file was not edited). L64390867 is the NINTH member of the weighted stack STKd8cd0279ff (member list in section 0).

STATUS LINE. VERIFIED: bar rule (cited to code, checked on stored bars), trigger rule (re-implemented independently in pandas; identical to the engine module on the full stored series: 1,862 long and 1,701 short raw signals identical bar for bar), event pipeline (801 of 801 stored events identical in time), bracket, side, session window, anchor and warm-up constants. NOT VERIFIED / OPEN: TRADES for td 20261110 (engine month 202611 not landed); entry/fill/exit mechanics quoted from the engine description (not re-derived); stack lots and fitted layers; NT8 equivalence of the 20-minute session-restarting grid.

## 0. Book identity and the stack member list
- Weighted stack STKd8cd0279ff = engine set `TL3_ALN_NY_STKd8cd0279ff`, loop ny-own-w. Members (D8_BUILD_SPEC.md "weighted option ny-own-w", NYAM_FINAL_STATUS.md section 2; weights 1 / 1 / 1 / 1 / 0.5 / 1 / 0.25 / 0.25 / 0.5 = whole base lots 4 / 4 / 4 / 4 / 2 / 4 / 1 / 1 / 2): L43f0cbfb.BRS8U, B7bfd33b7, Bf428c4a1.BRS8U, Le4fede95.BRF90_30, Lf0346d55.BRP60, L8cfda948.BRF90_30, L4407508c.BRF120_60, L39287638.BRF80_40, L64390867.BRF80_40. That is NINE members: the seven in the order's item 5 (L43f0cbfb, B7bfd33b7, Bf428c4a1, Le4fede95, L4407508c, L39287638 and this ninth one) plus Lf0346d55 and L8cfda948, which are already in the live file. Hand-written blocks exist in D8_BUILD_SPEC.md (AUTO:BOOK blocks with VERIFICATION lines) for L43f0cbfb, B7bfd33b7, Bf428c4a1, Le4fede95, Lf0346d55, L8cfda948; the generic (not hand-verified) blocks are for L4407508c, L39287638, L64390867. No further member exists.
- This book: stack entry `L64390867.BRF80_40`, session NY AM, base set `TL3_ALN_NY_L64390867_R0BRF80_40` (bare R0, 1 lot), events file `/mnt/l2/l2vast/_brkt/ev/L64390867_R0_F80_40.parquet` (801 events, all side +1, stop 80.0, target 40.0, lots 1). Weight 0.5 = 2 base lots (D8_BUILD_SPEC.md table "lots (base) 2").
- Cell (brkt_build.find_cell): row `time_m_20`, module `trig_bands_avwap0830`, variant `break_0830_native`, params {"clk": 3, "k": 1.0}, own ladder bracket plain60/60, mode `long`. The stack uses the fixed bracket F80_40 on the same trigger events.

## 1. BAR rule (time_m_20)
Code: `outputs/code/th_bars/build_month.py` `time_bars` lines 52-66, called at line 88 with P = 20 (GRID['time_m'] line 9) -> bucket 1,200 s. Session split `outputs/code/th_bars/common.py` lines 10-17 (ET: code 0 Asia 18:00-02:00, 1 London 02:00-08:30, 2 pre 08:30-09:30, 3 NY AM 09:30-12:00, 4 NY PM 12:00-16:00, 5 close 16:00-18:00; trading date td = ET + 6 h; session id = td x 10 + code).
1. Input = every trade record, no merge, no filter. Time bars are unaffected by the run-merge rule (D8_PRINT_RULE.md section 5, row time_m).
2. Segment = same session key and same instrument id (line 53); a new segment starts at every session boundary and at a contract roll. t_start = timestamp of the first print of the segment (line 54). NY AM: first print exactly 09:30:00.000 ET on both parity days (13:30:00.000Z 20261027, 14:30:00.000Z 20261110). The pre-market (code 2) segment has its own grid starting at its first print at or after 08:30 ET; it gives 3 bars of 20 minutes (08:30-09:30 ET).
3. bucket k = floor((ts - t_start)/1,200 s) (line 55); a bar exists only for buckets with prints.
4. open = first print, close = last print, high/low = extremes of print prices, volume = sum of `sz`.
5. Known time = t_start + (k+1) x 1,200 s (the bucket end, no wait for the next print). The last bucket of a segment is truncated: part = 1, known = the last print's time (line 62-63). NY AM = 8 bars: 7 full bars known at 09:50, 10:10, 10:30, 10:50, 11:10, 11:30, 11:50 ET, plus the truncated 11:50-12:00 ET bar with part = 1 (known at the last print, e.g. 16:59:59.904Z on 20261110). A part = 1 bar is never a signal bar.
6. Series seen by the trigger: all sessions, all history, concatenated in known-time order (D8_BAR_DEFS.md section 2; engine loader outputs/code/th_grid/gjob.py lines 33-49). The VWAP (section 2) only uses bars of the same trading date with session code >= 2.

## 2. TRIGGER rule (every constant)
Code: `outputs/code/th_grid/trig_bands_avwap0830.py` lines 45-52 (`_bands`), `outputs/code/th_grid/bandlib_wgrida.py` lines 9-12 (parse), 16-21 (spb_ref, clk_to_len), 44-47 (warm), 53-68 (events), 75-87 (make), 89-104 (anchored_vwap), `outputs/code/th_grid/ind.py` line 199 (edge). Variant `break_0830_native` -> kind break, sub 0830, native = True; params clk = 3 (minutes), k = 1.0. Input lines: bar high, low, close (points) and bar volume (contracts).
1. ANCHOR: the trading day's VWAP starts at the FIRST bar of each trading date td whose session code is >= 2, i.e. the first pre-market bar (08:30 ET grid start) (anchored_vwap with anchor_code 2 because sub == '0830': bandlib lines 89-95; code >= 2 means codes 2, 3, 4, 5; the Asia and London bars of the trading date have codes 0 and 1 and are NOT in it). It runs to the end of that trading date (through NY PM and the 16:00-18:00 ET close session); a new td restarts it.
2. Per bar j (bar volume v_j, typical price tp_j = (high_j + low_j + close_j)/3, all of the 20-minute bar, in points): V = sum of v from the anchor bar to j INCLUDING j; w_j = sum(tp x v)/V; sd_j = sqrt(max(sum(tp^2 x v)/V - w_j^2, 0)) = volume-weighted POPULATION standard deviation of the bars' typical prices around w_j (bandlib lines 96-102). cnt_j = number of bars since the anchor including bar j (anchor bar = 1).
3. Activity gate: bands are defined only when cnt_j >= mb, with mb = max(clk_to_len(clk = 3, sref) // 2, 3). clk_to_len = clip(round(3 x 60 / sref), 3, 600) where sref = median seconds per bar of the first 2,000 bars of the series (1,199.96 s for time_m_20) -> round(0.15) = 0 -> clipped to 3; 3 // 2 = 1; mb = max(1, 3) = 3. So the bands exist from the 3rd bar after the anchor (the last pre-market bar, 09:10-09:30 ET), i.e. every NY AM bar has bands. (For a TIME bar family no brick-size floor on sd applies: trig_bands_avwap0830.py line 49 acts only for family 'price'.)
4. up_j = w_j + 1.0 x sd_j; lo_j = w_j - 1.0 x sd_j (k = 1.0, in points).
5. LONG event at bar j: close_j > up_j AND NOT (close_{j-1} > up_{j-1}) -- an EDGE: the first close above the upper band after a bar that was not above it (the previous bar counts as not above when its band was undefined, e.g. the first bar of a day, or when it belonged to a different trading date). Strict greater. SHORT mirrored (close below lo, edge); the short side is discarded by the book (cell mode long; 1,701 raw shorts exist in the series, none traded). A bar both long and short is dropped.
6. No signals before bar index 2,000 of the series (2023-05-11, `warm` line 46: native variants); irrelevant live.
7. Computed at the bar close (known time).

## 3. From signal to order (events pipeline, engine code)
`outputs/code/th_brkt/brkt_build.py` raw_events lines 34-42, make lines 43-48: keep a signal only if its bar has part == 0 and session code == 3 (lines 38-39); order time ts = floor(bar known time to whole seconds) + 2 s (line 42); exit_ts = 12:00 ET end of the session; drop ts >= exit_ts; keep side +1 only (line 47); stop 80.0 / target 40.0 (SHAPES F80_40, line 19, applied line 44); lots 1; cap_exit.cap_events (th_fakefill/cap_exit.py lines 20-39: last print before the scheduled exit if no print within 120 s). Verified: independent re-implementation gives 801 events whose times equal the 801 stored events (side +1).
Note the effect of the edge rule on the session window: the VWAP bands are carried from the pre-market, so the first NY AM bar (known 09:50 ET) can already signal; a bar of the pre-market session is not tradable (session code 2).

## 4. SIDES, BRACKET, UNITS
LONG only. STOP 80 points and TARGET 40 points from the fill price, in NQ POINTS (1 point = 4 ticks of 0.25 = $20 per contract; stop 320 ticks = $1,600, target 160 ticks = $800 per contract). Fixed points, no unit rule (the cell's own plain60/60 is NOT used). Verified in the events file (all 801 are 80.0 / 40.0) and in the 20261027 trade (target exit +40.0 exactly). Session-end exit at 12:00 ET.

## 5. OTHER-MARKET OR LEVEL INPUTS
None from outside. The only level is the book's own 20-minute-bar VWAP and its volume-weighted standard deviation, built from this book's bars of the trading date (high, low, close, volume) as in section 2. No other market, no stored line files (unlike the _levels_ family).

## 6. ONE-POSITION RULE, SESSION WINDOW
One position per book (D8_BUILD_SPEC.md (b2)): an event while in a trade / exit pending / entry in flight is dropped; no other re-entry rule. NY AM bars only: first possible signal bar known 09:50 ET (order 09:50:02 ET), last possible the 11:50 ET bar (order 11:50:02 ET); flat at 12:00 ET. One event per day on both parity days.

## 7. Entry, fill and exit mechanics (quoted, not re-derived)
As in the hand-written blocks of D8_BUILD_SPEC.md (b2): market order at ts, filled 1.0 s later walking the 10-level book; stop order at fill - 80 pts, limit target at fill + 40 pts, UWTime flat at 12:00 ET executed 1.0 s later (last print before it if no print within 120 s). Check on the 20261027 trade: entry 14:30:03.000Z = order 14:30:02Z + 1.000 s; target exit at entry + 40.00 exactly.

## 8. Parity data, td 20261027 (EDT, NY AM 13:30-16:00Z) and td 20261110 (EST, NY AM 14:30-17:00Z)
BARS = the 8 NY AM time_m_20 bars of the engine store (/mnt/l2/l2vast/_bars/time_m_20/202610.parquet, 202611.parquet); last row part = 1. SIGNALS = stored events rows of that td. INPUTS = all bars of the trading date from the anchor (pre-market, 3 bars) through the last NY AM bar (11 rows) with the VWAP quantities I computed (equal to the engine module's at every signal bar). TRADES = engine exact-set bare 1-lot run.

### 8.1 td 20261027
BARS (8 rows)
```csv
known_utc,first_print_utc,open,high,low,close,volume,session_code,part
2026-10-27T13:50:00.000Z,2026-10-27T13:30:00.000Z,29561.25,29687.75,29541.25,29552.75,57816,3,0
2026-10-27T14:10:00.000Z,2026-10-27T13:50:00.002Z,29552.25,29586.75,29523.75,29540.5,36092,3,0
2026-10-27T14:30:00.000Z,2026-10-27T14:10:00.024Z,29540.25,29611,29494.5,29610.25,31830,3,0
2026-10-27T14:50:00.000Z,2026-10-27T14:30:00.001Z,29610.25,29679.25,29606.75,29663.75,32262,3,0
2026-10-27T15:10:00.000Z,2026-10-27T14:50:00.006Z,29664.5,29743,29661,29718,23939,3,0
2026-10-27T15:30:00.000Z,2026-10-27T15:10:00.013Z,29718.25,29775.5,29711,29767,20218,3,0
2026-10-27T15:50:00.000Z,2026-10-27T15:30:00.001Z,29767.25,29822.75,29739.5,29818.5,19007,3,0
2026-10-27T15:59:59.903Z,2026-10-27T15:50:00.004Z,29818.5,29845.25,29815.5,29842.25,8774,3,1
```
SIGNALS (1 row)
```csv
signal_bar_known_utc,engine_order_time_utc,side,stop_pts,target_pts,lots,session_end_exit_utc
2026-10-27T14:30:00.000Z,2026-10-27T14:30:02.000Z,1,80,40,1,2026-10-27T16:00:00.000Z
```
TRADES
```csv
entry_utc,entry_price,exit_utc,exit_price,exit_reason,side,lots,points,gross_usd
2026-10-27T14:30:03.000Z,29614.25,2026-10-27T14:33:46.780Z,29654.25,Target,1,1,40,800
```
INPUTS (11 rows)
```csv
known_utc,session_code,part,high,low,close,volume,bars_since_anchor,avwap,vw_sd,upper_k1,lower_k1,long_event,short_event_not_traded
2026-10-27T12:50:00.444Z,2,0,29621.5,29579,29604.25,5615,1,29601.5833333,0,,,0,0
2026-10-27T13:10:00.444Z,2,0,29618.25,29546,29546.25,10453,2,29581.145294,14.9793730453,,,0,0
2026-10-27T13:29:59.917Z,2,1,29570.75,29532.25,29560.25,7504,3,29572.6364012,17.5493842596,29590.1857855,29555.087017,0,0
2026-10-27T13:50:00.000Z,3,0,29687.75,29541.25,29552.75,57816,4,29587.7533697,13.5044190053,29601.2577887,29574.2489507,0,1
2026-10-27T14:10:00.000Z,3,0,29586.75,29523.75,29540.5,36092,5,29576.2572516,20.6001594827,29596.8574111,29555.6570921,0,0
2026-10-27T14:30:00.000Z,3,0,29611,29494.5,29610.25,31830,6,29575.331923,18.3591958382,29593.6911188,29556.9727271,1,0
2026-10-27T14:50:00.000Z,3,0,29679.25,29606.75,29663.75,32262,7,29588.5842581,33.0146685587,29621.5989267,29555.5695896,0,0
2026-10-27T15:10:00.000Z,3,0,29743,29661,29718,23939,8,29602.4167737,49.135150892,29651.5519246,29553.2816228,0,0
2026-10-27T15:30:00.000Z,3,0,29775.5,29711,29767,20218,9,29615.7399415,63.2640208641,29679.0039623,29552.4759206,0,0
2026-10-27T15:50:00.000Z,3,0,29822.75,29739.5,29818.5,19007,10,29629.5518423,77.1821770613,29706.7340193,29552.3696652,0,0
2026-10-27T15:59:59.903Z,3,1,29845.25,29815.5,29842.25,8774,11,29636.6393449,84.5699110308,29721.209256,29552.0694339,0,0
```

### 8.2 td 20261110
BARS (8 rows)
```csv
known_utc,first_print_utc,open,high,low,close,volume,session_code,part
2026-11-10T14:50:00.000Z,2026-11-10T14:30:00.000Z,27743,27863.5,27637.25,27803.75,66700,3,0
2026-11-10T15:10:00.000Z,2026-11-10T14:50:00.005Z,27803.5,28090,27784,28047,60567,3,0
2026-11-10T15:30:00.000Z,2026-11-10T15:10:00.010Z,28047,28058,27878,27909.5,38396,3,0
2026-11-10T15:50:00.000Z,2026-11-10T15:30:00.004Z,27910,27978.5,27760,27778.75,35064,3,0
2026-11-10T16:10:00.000Z,2026-11-10T15:50:00.001Z,27779,27852.75,27699.25,27830.5,35662,3,0
2026-11-10T16:30:00.000Z,2026-11-10T16:10:00.144Z,27828.25,27851.25,27728,27776.5,24993,3,0
2026-11-10T16:50:00.000Z,2026-11-10T16:30:00.002Z,27776.75,27811.5,27650.5,27666.75,21873,3,0
2026-11-10T16:59:59.904Z,2026-11-10T16:50:00.007Z,27666.75,27692.5,27617,27631.75,9421,3,1
```
SIGNALS (1 row)
```csv
signal_bar_known_utc,engine_order_time_utc,side,stop_pts,target_pts,lots,session_end_exit_utc
2026-11-10T14:50:00.000Z,2026-11-10T14:50:02.000Z,1,80,40,1,2026-11-10T17:00:00.000Z
```
TRADES
OPEN (not verified): the engine month 202611 is not landed for base set `TL3_ALN_NY_L64390867_R0BRF80_40` (runs_rf/TL3_ALN_NY_L64390867_R0BRF80_40 has months up to 202610 only). No TRADES values are given; none invented.
INPUTS (11 rows)
```csv
known_utc,session_code,part,high,low,close,volume,bars_since_anchor,avwap,vw_sd,upper_k1,lower_k1,long_event,short_event_not_traded
2026-11-10T13:50:00.137Z,2,0,27997.5,27590,27726.25,29775,1,27771.25,0,,,0,0
2026-11-10T14:10:00.137Z,2,0,27738.5,27644.75,27725,12138,2,27751.4124078,31.0700016097,,,0,0
2026-11-10T14:29:59.998Z,2,1,27761.5,27697.75,27743.75,10881,3,27747.8923599,28.532664712,27776.4250246,27719.3596952,0,0
2026-11-10T14:50:00.000Z,3,0,27863.5,27637.25,27803.75,66700,4,27759.2092148,21.472211159,27780.681426,27737.7370037,1,0
2026-11-10T15:10:00.000Z,3,0,28090,27784,28047,60567,5,27831.3461267,102.822833294,27934.16896,27728.5232934,0,0
2026-11-10T15:30:00.000Z,3,0,28058,27878,27909.5,38396,6,27851.9370902,103.453514937,27955.3906052,27748.4835753,0,0
2026-11-10T15:50:00.000Z,3,0,27978.5,27760,27778.75,35064,7,27850.1593119,96.1356350741,27946.294947,27754.0236768,0,0
2026-11-10T16:10:00.000Z,3,0,27852.75,27699.25,27830.5,35662,8,27843.2543081,91.8764459581,27935.1307541,27751.3778622,0,0
2026-11-10T16:30:00.000Z,3,0,27851.25,27728,27776.5,24993,9,27838.6400102,89.5328250886,27928.1728353,27749.1071851,0,0
2026-11-10T16:50:00.000Z,3,0,27811.5,27650.5,27666.75,21873,10,27830.239876,92.2382700862,27922.4781461,27738.0016059,0,1
2026-11-10T16:59:59.904Z,3,1,27692.5,27617,27631.75,9421,11,27825.2451795,95.7379319072,27920.9831114,27729.5072476,0,0
```

## 9. Open points (stated, not guessed)
1. TRADES for 20261110: engine month 202611 not landed for TL3_ALN_NY_L64390867_R0BRF80_40 (months to 202610 only; 202511 also absent). Nothing queued.
2. Stack layers, weights as whole lots (0.5 = 2 base lots of the x4 basis; the live file runs 6 lots per book) and the weighted joint fit are open (NYAM_FINAL_STATUS.md section 4: no joint fit for STKd8cd0279ff).
3. Fill walk and slippage are engine mechanics, not re-derived. NT8: the engine's 20-minute grid restarts at each session's first print (pre-market grid from ~08:30, NY AM grid from 09:30); equivalence with an NT8 session template, and an NT8 anchored-VWAP indicator's definition of sd, were not tested; implement section 2 literally.
4. Exit verdict: stack_exit_state: no recipe passes stage 1 for L64390867.BRF80_40 (NYAM_FINAL_STATUS.md section 3): no exit kept.
5. Volume source: bar `volume` is the sum of `sz` of all print rows; a 20-minute bar from another feed (e.g. NT8 volume) may differ slightly; not tested.

Files read or run: the directive/inbox file; D8_BUILD_SPEC.md; D8_BAR_DEFS.md; D8_PRINT_RULE.md; NYAM_FINAL_STATUS.md; D8_PARITY_L64390867_20261027.md / _20261110.md (bars and signals identical to the blocks above); code th_bars/{build_month,common}.py, th_grid/{trig_bands_avwap0830,bandlib_wgrida,ind,gjob}.py, th_brkt/brkt_build.py, th_fakefill/cap_exit.py; stores _bars/time_m_20, _brkt/ev, runs_rf.

## Relay questions 2026-11-24 21:25Z (answers added by W-NYAMSPEC2; engine files untouched)
Q3a. VWAP and volume-weighted sd of the bars' typical prices (h+l+c)/3, weighted by bar volume, restart at the first bar of the trading date with session code >= 2 (the pre-market grid, first trade at or after 08:30 ET) and run through NY AM, NY PM and the close session to the end of the trading date: CORRECT (anchored_vwap, bandlib_wgrida.py lines 89-104). sd is the volume-weighted POPULATION sd around the running VWAP.
Q3b. Bands exist when cnt >= 3 where cnt counts the anchor bar as 1: the bands first exist ON the 3rd pre-market bar (09:10-09:30 ET, known 09:30 ET, 0-based index 2 of the day). If you mean 1-based bar 3, correct; if 0-based index >= 3, you are one bar late. No NY AM bar is affected (all have bands), but the 3rd pre bar's above/below flag is the "previous bar" of the first NY AM bar's edge test.
Q3c. LONG = edge: close_j > vwap_j + 1.0 sd_j AND NOT (close_{j-1} > its own band_{j-1}); so every new excursion above the band fires on its first close (not only the first of the day); previous bar with undefined band counts as not above. Strict >. Own band at each bar, bands move with the running VWAP. Short side discarded.
Q3d. clk 3 resolves for time_m_20 to: sref = median seconds per bar of the first 2,000 bars = 1,199.96 s; clk_to_len = clip(round(3 x 60 / 1199.96), 3, 600) = clip(round(0.15) = 0, 3, 600) = 3 bars; mb = max(3 // 2, 3) = 3 bars since the anchor. clk is NOT a lookback length in this book; it only sets mb = 3. (The trigger uses no rolling window: cumulative from the anchor.)
