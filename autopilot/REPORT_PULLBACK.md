# REPORT PULLBACK - level-respect and pullback-entry study (NQ primary, ES and RTY confirmation)

**Verdict: NO FOUND, 1 weak LEAD. No pullback level is respected beyond a random-level null: 0 of 41 levels pass the pre-registered respect rule (only 1.1% of core (instrument, level, bar) cells have z >= 3 and +1.0 pp over the random-level null on clean, none persists in H1+H2). The real stage-1 best clean weekly Sharpe (1.58 over 3,280 cells; 2.01 after the 1,495-cell stage-2 expansion) does not beat what random-level worlds produce (best-of-search over the same 3,280-cell grid in 30 null worlds: mean 1.97, p95 2.32). All 12 clean-selected finalists decay (mean standalone Sharpe clean 1.81, H1 0.29, H2 0.05); 0 of 12 pass gate 3 at the 20% headline share (1 of 12 at 30% only); the closest (NQ 15-min PSAR touch-and-close-back, RTH, level-0.5 ATR stop, 1.5R) is a weak LEAD: additive 20% uplift +0.26 / +0.11 / +0.08, own nulls and bootstrap pass, wd-corr -0.55, but H2 < +0.10, plateau 4 of 6, 2x slippage H1/H2 +0.09/+0.07, ES/RTY replication negative, ERA negative pre-2023. Pair-side: re-timing the pair's entries as pullbacks (32 cells) 0 pass (mean all-in uplift -0.71), pullback-depth size tilt (12 cells) 0 pass.** FOUND 0, LEAD 1 (weak). Chance-pass: expected finalists passing gate 3 by chance 0.33 per study of 12 (null worlds 10/360 = 2.8% per top cell), observed 0.

Spec: PULLBACK_STUDY.md (verbatim), pre-registered in PREREG_PULLBACK.md (plus Amendment 1) before the first scored cell. Code: code/census/night_ins/ap_pb_core.py (data, levels, triggers, simulator), ap_pb_stage1.py, ap_pb_stage2.py, ap_pb_final.py, ap_pb_pair.py, ap_pb_respect_post.py, ap_pb_altmonth.py, ap_pb_nullworld.py, ap_pb_tables.py, ap_pb_report_data.py, ap_pb_esrty.py, ap_pb_lib.py. Data and results: outputs/autopilot/pb/.

## 1. What was run (cells, nulls, runtime)
| item | count |
|---|---|
| NQ strategy cells (stage 1 screen 41 levels x 5 bars x 4 core triggers x 2 stops x 2 targets) | 3,280 |
| NQ stage 2 (one-factor expansion around 24 bases: trigger, trend, stop, target, session; stop x target product around 8 bases) | 1,792 specified, 1,495 unique -> **4,775 unique NQ cells** (spec said about 4,000; counted, not hidden) |
| ES and RTY identical stage-1 screens (report-only confirmation) | 3,280 each = 6,560 |
| Random-level null worlds for the stage-1 grid (30 worlds x 3,280 NQ cells) | 98,400 cell simulations |
| Level-respect cells (3 instruments x 41 levels x 5 bars x 4 core triggers) each with 40 random-level and 20 timing-destroyed replicates | 2,460 (+805 post-selection H1+H2 / 2013-22 columns, 20 replicates each) |
| Finalists scored with the single H1/H2 read | 12 (each: 1,000 timing-destroyed draws, 100 random-level replicates, +/-25% neighbours, 2x slippage, ES, RTY, H0, 2013-26 ERA run, odd/even months) |
| Alternating-month whole-search replication | 4,775 cells x 2 selections |
| Pair-side cells | 32 (re-timed entries) + 12 (depth tilt) |
Runtime on 6 processes (box shared): stage 1 22 min (NQ+ES+RTY), stage 2 under 1 min, finalist scoring about 2 min, ES/RTY strategy screens 28 min, respect post columns 3 min, pair side about 4 min (2 processes), null-world gate-3 reads and alternating-month search a few minutes each.

**Fill model and costs.** Signal bars 1/3/5/15/60 min built from 1-minute bars (buckets aligned to the 18:00 ET session start); levels/indicators use information through the close of the signal bar (causality verified by a truncation test: every level, trigger, trend, stop and target is unchanged when later data are removed). Entry: market order at the open of the first 1-minute bar after the signal bar completes. Exit: stop-market (fills at min(stop, bar open) for longs), limit target, time exit or trail at the next open; stop is taken first when stop and target are both reachable inside one 1-minute bar; flat at the 16:55 ET open; one position at a time. Slippage 1 tick per side on every entry and exit (also limit targets) + $4.36 per contract round trip; 2x slippage test = 2 ticks per side. 1 contract (NQ $20/pt); sleeves scaled so the clean weekly sigma equals the pair's (100% share = pair-equivalent risk). Pair = B.Cfg(wk_floor=8, wk_loss_pb=None) computed in a clean process, reproduced 1.46 / 2.83 / 2.30 (asserted).

**Executability.** NinjaTrader Brokerage via Rithmic: every cell is a plain NT8 strategy on n-minute NQ series with market entry on the next bar and an OCO stop/limit bracket (or time/trail exit), flat before 17:00 ET; no cell needs sub-minute data. Intraday margin is small (about 3.3 / 5 / 8.3 NQ contracts for a 20 / 30 / 50% share; verify broker day margin).

## 2. LEVEL-RESPECT TABLE (the table the study was for)
Definition (pre-registered): core trigger touch-and-close-back (band 0.25 ATR, any touch) with the HTF EMA50-slope trend; outcome = does price reach +1 ATR in the trend direction before -1 ATR within 12 signal bars; bounce rate = wins / (wins + losses). Null A = same procedure on levels shifted by a random +/-[0.5, 2.0] ATR (40 replicates). Null B (timing-destroyed, random bars in the same trend direction, 20 replicates) gives the unconditional drift baseline (mean 0.50). Cells show excess over the random-level null in percentage points / z. RESPECTED = z >= 3 and +1.0 pp on at least 2 of 3 instruments at the same bar size, or on NQ at >= 3 of 5 bar sizes.

**Result: no level is respected.** Of 615 core (instrument, level, bar) cells, 7 reach z >= 3 and +1 pp on clean (a normal null predicts about 1); mean excess over the random-level null is -0.23 pp on clean (i.e. levels bounce slightly LESS than arbitrary depth), +0.30 pp in H1+H2 and -0.19 pp in NQ 2013-2022. The z of the same (instrument, level, bar) cell has correlation +0.04 between clean and H1+H2 and -0.05 between clean and 2013-22 (NQ): there is no persistent respect to find. Of the 8 cells with clean z >= 3, none keeps z >= 3 in H1+H2 (mean H1+H2 excess -0.33 pp). The levels with any clean hit on one instrument are EMA50, Keltner 1, ON_BRK, PIV_S1R1, CAM3 (NQ) and PD_OPP, ON_OPP (RTY): all fail the 2-instrument/3-bar rule.

### 2.1 NQ: excess over random-level null (pp) / z, by level and bar size (clean 2023-08..2025-07, core trigger)
| level | family | NQ1 | NQ3 | NQ5 | NQ15 | NQ60 | n_resp_NQ | n_resp_ES | n_resp_RTY | RESPECTED |
|---|---|---|---|---|---|---|---|---|---|---|
| EMA:9 | MA (EMA/SMA/HMA) | -0.9/-0.6 | -1.3/-0.5 | -1.6/-0.9 | +0.4/+0.3 | -1.0/-0.3 | 0 | 0 | 0 | no |
| EMA:20 | MA (EMA/SMA/HMA) | -0.1/-0.1 | -0.4/-0.6 | -1.3/-2.2 | +1.6/+1.7 | -0.3/-0.1 | 0 | 0 | 0 | no |
| EMA:21 | MA (EMA/SMA/HMA) | -0.0/-0.0 | -0.6/-0.7 | -1.7/-3.1 | +1.7/+1.9 | -0.9/-0.4 | 0 | 0 | 0 | no |
| EMA:34 | MA (EMA/SMA/HMA) | -0.3/-0.5 | -1.6/-3.3 | -0.2/-0.3 | +1.8/+2.7 | -0.7/-0.3 | 0 | 0 | 0 | no |
| EMA:50 | MA (EMA/SMA/HMA) | -0.7/-1.2 | -0.9/-1.5 | -0.1/-0.1 | +3.1/+3.7 | +0.6/+0.2 | 1 | 0 | 0 | no |
| EMA:100 | MA (EMA/SMA/HMA) | -0.4/-1.7 | +0.3/+0.3 | -0.1/-0.2 | +2.5/+2.1 | -0.7/-0.2 | 0 | 0 | 0 | no |
| EMA:200 | MA (EMA/SMA/HMA) | +0.1/+0.2 | +1.2/+1.1 | -0.5/-0.7 | +0.2/+0.1 | -1.1/-0.2 | 0 | 0 | 0 | no |
| SMA:20 | MA (EMA/SMA/HMA) | -0.2/-0.4 | -0.8/-1.2 | -0.6/-1.6 | +1.8/+2.3 | -1.6/-0.6 | 0 | 0 | 0 | no |
| SMA:50 | MA (EMA/SMA/HMA) | -0.8/-1.6 | -0.1/-0.1 | -0.5/-0.7 | -0.0/-0.0 | -1.2/-0.4 | 0 | 0 | 0 | no |
| SMA:100 | MA (EMA/SMA/HMA) | -0.4/-1.1 | -0.6/-1.5 | +0.1/+0.1 | -0.5/-0.3 | +1.6/+0.5 | 0 | 0 | 0 | no |
| SMA:200 | MA (EMA/SMA/HMA) | -0.1/-0.3 | -0.2/-0.3 | -0.7/-0.7 | +0.8/+0.6 | -4.0/-1.1 | 0 | 0 | 0 | no |
| HMA:20 | MA (EMA/SMA/HMA) | -0.2/-0.5 | +0.1/+0.0 | -0.1/-0.1 | -0.5/-0.4 | -2.5/-0.6 | 0 | 0 | 0 | no |
| HMA:55 | MA (EMA/SMA/HMA) | -0.1/-0.2 | +0.3/+0.7 | -0.1/-0.2 | -2.1/-1.7 | -1.7/-0.6 | 0 | 0 | 0 | no |
| VWAP_DAY | VWAP / anchored VWAP | -0.4/-0.8 | -0.7/-0.9 | -1.7/-2.8 | +0.7/+0.5 | -3.1/-1.0 | 0 | 0 | 0 | no |
| VWAP_RTH | VWAP / anchored VWAP | -0.6/-0.7 | -1.0/-1.3 | -2.4/-2.1 | -0.4/-0.2 | -0.5/-0.1 | 0 | 0 | 0 | no |
| AVWAP_WEEK | VWAP / anchored VWAP | -0.5/-0.6 | +0.5/+0.4 | +1.5/+1.6 | -0.0/-0.0 | -1.6/-1.0 | 0 | 0 | 0 | no |
| AVWAP_MONTH | VWAP / anchored VWAP | +0.8/+0.9 | +1.4/+0.7 | -0.1/-0.0 | -2.7/-0.8 | -5.3/-1.2 | 0 | 0 | 0 | no |
| AVWAP_SWING | VWAP / anchored VWAP | +0.2/+0.3 | -0.1/-0.1 | -0.7/-1.0 | +0.3/+0.7 | +2.0/+1.0 | 0 | 0 | 0 | no |
| BB:2 | Bands (Bollinger/Keltner) | +0.4/+0.3 | +0.6/+0.6 | +0.5/+0.3 | -3.3/-3.4 | -0.8/-0.2 | 0 | 0 | 0 | no |
| KC:1 | Bands (Bollinger/Keltner) | -0.7/-1.5 | +0.3/+0.5 | +2.0/+4.2 | -1.2/-1.2 | -4.0/-2.1 | 1 | 0 | 0 | no |
| KC:2 | Bands (Bollinger/Keltner) | +0.1/+0.1 | -0.1/-0.1 | -1.6/-1.8 | +1.7/+0.6 | +3.3/+1.0 | 0 | 0 | 0 | no |
| KIJUN:26 | Trend lines (Kijun/PSAR/Supertrend) | -0.2/-0.5 | -0.2/-0.5 | -0.2/-0.2 | +1.7/+2.2 | -1.7/-0.5 | 0 | 0 | 0 | no |
| PSAR | Trend lines (Kijun/PSAR/Supertrend) | +0.7/+0.8 | -2.0/-0.9 | -1.7/-1.1 | +0.0/+0.0 | -7.7/-1.2 | 0 | 0 | 0 | no |
| FIB:38.2 | Fibonacci | -0.1/-0.4 | -0.5/-0.4 | +0.1/+0.1 | -0.1/-0.1 | -5.2/-2.2 | 0 | 0 | 0 | no |
| FIB:50 | Fibonacci | -0.1/-0.4 | -1.2/-1.6 | -0.5/-0.4 | +3.6/+1.9 | -2.2/-0.8 | 0 | 0 | 0 | no |
| FIB:61.8 | Fibonacci | -0.1/-0.3 | -0.1/-0.2 | +0.7/+0.8 | +2.6/+1.5 | -0.9/-0.3 | 0 | 0 | 0 | no |
| PD_BRK | Prior-day / overnight extremes | +1.9/+1.3 | +1.2/+1.3 | +0.4/+0.4 | -1.0/-0.5 | -3.2/-0.6 | 0 | 0 | 0 | no |
| PD_OPP | Prior-day / overnight extremes | -0.7/-0.5 | -0.6/-0.2 | -1.6/-0.3 | -3.4/-1.1 | -6.3/-2.4 | 0 | 0 | 1 | no |
| ON_BRK | Prior-day / overnight extremes | -1.4/-1.5 | -1.3/-1.6 | -1.9/-1.8 | +2.2/+1.8 | +8.6/+4.7 | 1 | 0 | 0 | no |
| ON_OPP | Prior-day / overnight extremes | -2.0/-0.9 | -1.8/-0.7 | -0.9/-0.1 | -5.0/-1.0 | -0.6/-0.2 | 0 | 0 | 1 | no |
| PIV_PP | Pivots (classic/Camarilla) | +0.6/+0.4 | +0.5/+0.4 | +1.0/+1.3 | -0.9/-1.0 | -3.0/-1.2 | 0 | 0 | 0 | no |
| PIV_S1R1 | Pivots (classic/Camarilla) | +5.6/+4.0 | +3.3/+1.1 | +2.4/+0.9 | -2.5/-0.4 | +1.5/+0.4 | 1 | 0 | 0 | no |
| PIV_S2R2 | Pivots (classic/Camarilla) | -1.1/-0.3 | +2.2/+0.2 | +9.8/+1.8 | -10.5/-0.5 | -15.8/-1.3 | 0 | 0 | 0 | no |
| CAM:3 | Pivots (classic/Camarilla) | +0.2/+0.2 | -0.2/-0.1 | +4.1/+3.3 | +3.9/+1.4 | +1.2/+0.5 | 1 | 0 | 0 | no |
| CAM:4 | Pivots (classic/Camarilla) | +0.4/+0.2 | +5.9/+2.0 | +2.2/+0.7 | +0.7/+0.1 | -3.4/-1.0 | 0 | 0 | 0 | no |
| ROUND:50 | Round numbers | +0.0/+0.0 | -0.4/-0.6 | -1.9/-1.4 | -0.6/-0.6 | -2.9/-0.7 | 0 | 0 | 0 | no |
| ROUND:100 | Round numbers | +0.2/+0.2 | +0.6/+0.4 | +0.6/+0.4 | +0.9/+0.6 | -3.2/-1.6 | 0 | 0 | 0 | no |
| SUPERTREND | Trend lines (Kijun/PSAR/Supertrend) | -0.0/-0.0 | -1.8/-1.3 | +0.7/+0.2 | +0.7/+0.2 | +3.3/+0.7 | 0 | 0 | 0 | no |
| FVG_TOP | ICT (FVG/OB) | +0.7/+0.8 | +0.7/+0.6 | -0.2/-0.2 | +2.7/+1.7 | +2.3/+1.1 | 0 | 0 | 0 | no |
| FVG_MID | ICT (FVG/OB) | +0.6/+0.5 | +0.1/+0.0 | +0.1/+0.1 | +1.1/+0.6 | -3.1/-0.9 | 0 | 0 | 0 | no |
| OB_TOP | ICT (FVG/OB) | +0.3/+1.1 | +0.2/+0.2 | +1.2/+1.3 | +3.6/+1.8 | -7.7/-3.0 | 0 | 0 | 0 | no |

### 2.2 ES and RTY (same columns)
| level | ES1 | ES3 | ES5 | ES15 | ES60 | RTY1 | RTY3 | RTY5 | RTY15 | RTY60 |
|---|---|---|---|---|---|---|---|---|---|---|
| EMA:9 | -0.5/-0.7 | -1.1/-0.8 | -1.8/-1.8 | +1.2/+1.0 | -1.4/-0.3 | -0.1/-0.1 | -0.2/-0.3 | -0.4/-0.4 | +2.1/+1.2 | +1.9/+0.4 |
| EMA:20 | -0.2/-0.6 | -0.1/-0.3 | -0.2/-0.3 | -0.6/-0.7 | -2.4/-0.9 | -0.2/-0.3 | -0.0/-0.1 | -0.9/-1.4 | +1.6/+1.1 | -1.7/-1.1 |
| EMA:21 | -0.4/-1.0 | -0.4/-0.9 | -0.3/-0.5 | -0.4/-0.5 | -2.7/-0.9 | -0.4/-0.7 | -0.2/-0.6 | -0.8/-1.2 | +1.1/+0.7 | -1.4/-0.8 |
| EMA:34 | +0.3/+0.9 | -0.9/-2.0 | -0.3/-0.6 | +0.2/+0.2 | -1.7/-0.7 | -0.4/-0.8 | -0.2/-0.5 | +0.1/+0.2 | -1.8/-1.2 | -1.2/-0.5 |
| EMA:50 | +0.4/+1.6 | -0.1/-0.2 | -0.1/-0.2 | -1.0/-0.9 | -3.6/-1.5 | +0.1/+0.1 | -0.6/-1.4 | +0.7/+0.8 | -2.3/-2.7 | -3.2/-1.3 |
| EMA:100 | -0.6/-1.9 | -0.1/-0.2 | -0.4/-0.4 | +0.6/+1.0 | -2.2/-1.2 | -0.2/-0.3 | -0.5/-1.1 | +0.8/+0.8 | -0.7/-0.5 | +3.7/+1.1 |
| EMA:200 | +0.1/+0.2 | +0.1/+0.3 | +1.5/+1.8 | +0.2/+0.1 | -5.6/-0.7 | +0.0/+0.1 | -0.1/-0.1 | -0.5/-0.5 | +1.3/+0.7 | -4.6/-0.9 |
| SMA:20 | +0.1/+0.3 | +0.2/+0.3 | -0.3/-0.5 | +0.8/+1.0 | -3.8/-1.4 | -0.5/-0.9 | -0.6/-2.2 | -1.5/-3.1 | +2.1/+1.5 | -0.8/-0.4 |
| SMA:50 | +0.4/+1.7 | +0.1/+0.1 | -0.6/-0.8 | -0.3/-0.4 | -3.9/-1.2 | -0.2/-0.8 | -0.4/-0.7 | +1.2/+2.0 | +0.4/+0.3 | -2.8/-0.7 |
| SMA:100 | -0.1/-0.3 | -0.2/-0.4 | +0.6/+0.7 | -0.4/-0.4 | -0.4/-0.3 | -0.4/-1.1 | +0.2/+0.4 | +0.1/+0.1 | +1.3/+1.5 | -1.8/-0.5 |
| SMA:200 | -0.5/-0.7 | +1.2/+2.3 | -1.0/-0.9 | +0.5/+0.3 | -2.0/-0.6 | -0.5/-1.4 | -0.6/-0.4 | +0.5/+0.3 | -1.0/-0.9 | +1.7/+0.4 |
| HMA:20 | -0.3/-0.6 | +0.2/+0.5 | -0.8/-0.6 | -0.3/-0.2 | -5.7/-1.6 | +0.2/+0.2 | -0.1/-0.1 | +0.1/+0.1 | +2.2/+1.0 | +1.7/+0.5 |
| HMA:55 | -0.5/-2.3 | +0.5/+3.3 | -0.6/-1.1 | -1.3/-1.1 | +0.2/+0.1 | -0.6/-0.8 | +0.2/+0.4 | +0.4/+0.5 | +2.7/+1.4 | -0.1/-0.0 |
| VWAP_DAY | -0.1/-0.3 | -0.5/-0.8 | -0.0/-0.1 | +0.7/+0.8 | -2.9/-0.7 | +0.1/+0.3 | +0.6/+1.1 | +0.2/+0.2 | +0.3/+0.2 | -1.4/-0.3 |
| VWAP_RTH | -2.4/-3.3 | -1.5/-0.9 | -2.5/-1.3 | -0.4/-0.2 | +1.7/+0.3 | -0.0/-0.1 | -0.4/-0.5 | +0.5/+0.8 | +1.8/+0.9 | +5.4/+0.7 |
| AVWAP_WEEK | -0.9/-1.1 | -1.0/-1.3 | +1.4/+1.7 | -0.9/-0.7 | -1.4/-0.5 | -1.6/-1.4 | -2.7/-3.0 | -2.8/-2.9 | +0.2/+0.1 | +1.1/+0.3 |
| AVWAP_MONTH | +0.7/+0.5 | -2.3/-1.7 | -1.4/-0.8 | -0.5/-0.3 | -5.6/-1.0 | +0.3/+0.2 | -3.2/-1.6 | -3.3/-1.6 | -0.1/-0.0 | +5.6/+1.5 |
| AVWAP_SWING | -0.2/-0.9 | -0.1/-0.2 | -0.5/-0.6 | +0.8/+0.8 | -2.3/-1.0 | +0.1/+0.1 | -0.3/-0.8 | -1.4/-1.8 | +0.5/+0.9 | +0.3/+0.1 |
| BB:2 | +0.5/+0.5 | -0.4/-0.6 | -0.4/-0.4 | +0.8/+0.4 | -2.7/-0.9 | +0.2/+0.2 | +0.9/+0.8 | +0.1/+0.0 | -1.8/-0.9 | -2.7/-1.4 |
| KC:1 | +0.5/+1.7 | +0.6/+0.7 | +0.6/+0.7 | +1.1/+1.6 | -3.5/-1.6 | -0.0/-0.0 | -0.0/-0.0 | -0.0/-0.0 | -2.2/-2.5 | +1.3/+0.7 |
| KC:2 | +0.5/+0.8 | -1.3/-1.7 | +0.5/+0.2 | +0.5/+0.5 | +2.6/+0.8 | +0.1/+0.1 | +1.0/+1.2 | -0.8/-0.6 | +1.6/+0.9 | +0.8/+0.3 |
| KIJUN:26 | -0.2/-0.9 | -0.6/-1.0 | -0.2/-0.2 | +0.0/+0.0 | -2.3/-1.0 | -0.5/-0.8 | -0.4/-1.0 | -0.4/-0.7 | -0.6/-0.7 | -0.6/-0.2 |
| PSAR | -0.3/-0.7 | -0.5/-0.4 | -0.6/-0.3 | +1.5/+0.6 | -1.1/-0.2 | +0.5/+0.3 | -1.2/-0.6 | -0.5/-0.4 | -1.3/-0.8 | -0.6/-0.2 |
| FIB:38.2 | +0.2/+0.4 | -0.7/-0.4 | +0.2/+0.2 | +0.0/+0.0 | -2.1/-0.7 | +0.0/+0.1 | -0.9/-0.9 | -0.9/-0.9 | +1.8/+0.8 | +2.2/+0.8 |
| FIB:50 | -0.0/-0.1 | -0.9/-0.7 | -1.3/-1.5 | +1.0/+0.9 | -1.4/-0.4 | +0.5/+1.3 | -0.8/-1.0 | -0.0/-0.0 | +2.0/+1.6 | +0.5/+0.2 |
| FIB:61.8 | +0.2/+0.4 | -0.0/-0.0 | -1.1/-1.3 | +0.4/+0.5 | -4.1/-2.1 | +0.2/+0.5 | -0.4/-0.8 | -0.3/-0.6 | +0.2/+0.2 | +0.9/+0.3 |
| PD_BRK | -0.5/-0.4 | -2.3/-1.2 | -3.0/-3.2 | -2.0/-1.1 | -1.9/-0.5 | +1.1/+1.2 | +1.2/+1.4 | +0.3/+0.3 | +0.3/+0.2 | -1.3/-0.7 |
| PD_OPP | +0.7/+0.4 | -2.4/-1.1 | -3.3/-1.9 | +0.2/+0.1 | +1.4/+0.5 | +4.6/+4.6 | +5.9/+1.0 | +3.6/+0.6 | -6.4/-1.6 | +5.3/+1.8 |
| ON_BRK | -1.7/-2.5 | +0.1/+0.1 | +1.0/+0.6 | +1.0/+0.4 | +1.8/+0.3 | +1.4/+1.6 | +0.0/+0.0 | -0.8/-0.6 | +0.4/+0.3 | +7.4/+1.5 |
| ON_OPP | +0.6/+0.2 | -1.7/-0.5 | +3.0/+0.4 | -4.9/-0.9 | +1.5/+0.4 | +2.5/+1.7 | -2.3/-0.6 | -4.1/-0.9 | +6.1/+3.2 | +0.6/+0.3 |
| PIV_PP | -1.0/-1.2 | +0.9/+1.3 | +1.4/+1.1 | +1.0/+0.5 | -3.8/-2.1 | -0.2/-0.3 | -1.9/-1.8 | -2.2/-2.7 | -0.1/-0.0 | +0.5/+0.2 |
| PIV_S1R1 | +0.7/+0.4 | -3.4/-0.9 | -0.2/-0.1 | +6.6/+0.6 | -0.3/-0.1 | +0.6/+0.2 | +1.3/+0.3 | -2.7/-0.3 | +3.2/+0.4 | -0.1/-0.0 |
| PIV_S2R2 | +1.4/+0.6 | -5.8/-1.0 | +7.6/+1.0 | +27.9/+1.6 | -6.3/-1.1 | +2.4/+0.5 | -6.4/-0.4 | +7.8/+1.0 | -16.1/-1.0 | -3.6/-0.4 |
| CAM:3 | -0.8/-0.8 | -0.4/-0.2 | +2.7/+1.4 | +0.4/+0.3 | +0.3/+0.1 | -1.6/-1.0 | +1.8/+1.0 | +4.3/+1.5 | -0.0/-0.0 | -0.5/-0.2 |
| CAM:4 | -4.5/-1.7 | -2.4/-0.6 | -3.6/-0.9 | +1.7/+0.2 | -0.7/-0.2 | -1.0/-0.5 | +1.7/+0.3 | -8.4/-1.6 | -1.3/-0.2 | +3.0/+0.8 |
| ROUND:50 | +0.1/+0.1 | -1.6/-1.0 | -2.6/-1.4 | -0.6/-0.3 | -2.2/-0.7 | +1.4/+1.2 | +0.5/+0.2 | +2.1/+1.7 | +2.6/+1.1 | +0.8/+0.3 |
| ROUND:100 | +0.5/+0.2 | -4.1/-2.6 | -5.2/-1.6 | -0.2/-0.1 | -2.4/-0.6 | +1.4/+1.0 | -0.4/-0.2 | +1.8/+1.1 | +4.0/+1.4 | +4.9/+1.0 |
| SUPERTREND | -0.8/-0.9 | -2.3/-1.0 | -2.2/-0.9 | +0.7/+0.3 | -2.7/-0.4 | +1.1/+0.6 | +1.5/+0.7 | +0.9/+0.3 | -1.6/-0.6 | -1.4/-0.3 |
| FVG_TOP | +0.7/+1.4 | +1.3/+1.3 | +0.6/+1.0 | +0.7/+0.5 | +1.6/+0.5 | -0.0/-0.0 | -0.9/-1.9 | -0.5/-0.3 | +3.1/+2.2 | -1.5/-0.5 |
| FVG_MID | +0.0/+0.0 | +0.3/+0.2 | +0.2/+0.2 | +2.3/+1.5 | +1.4/+0.7 | -0.3/-0.5 | -0.0/-0.1 | -0.2/-0.1 | +1.2/+0.6 | -0.2/-0.1 |
| OB_TOP | -0.3/-0.9 | -0.7/-1.3 | -2.4/-2.4 | +1.5/+2.0 | +0.1/+0.0 | +0.6/+0.8 | -0.6/-0.6 | -1.6/-0.8 | +0.3/+0.2 | -3.7/-1.2 |

### 2.3 By level family and instrument (mean over levels x bar sizes; frac_z3 = share of cells with z >= 3)
| fam | inst | cells | mean_excess_pp | mean_z | frac_z3 | frac_zneg3 |
|---|---|---|---|---|---|---|
| Bands (Bollinger/Keltner) | ES | 15 | -0.01 | 0.18 | 0.00 | 0.00 |
| Bands (Bollinger/Keltner) | NQ | 15 | -0.19 | -0.17 | 0.07 | 0.07 |
| Bands (Bollinger/Keltner) | RTY | 15 | -0.11 | -0.07 | 0.00 | 0.00 |
| Fibonacci | ES | 15 | -0.64 | -0.32 | 0.00 | 0.00 |
| Fibonacci | NQ | 15 | -0.27 | -0.17 | 0.00 | 0.00 |
| Fibonacci | RTY | 15 | 0.33 | 0.11 | 0.00 | 0.00 |
| ICT (FVG/OB) | ES | 15 | 0.47 | 0.33 | 0.00 | 0.00 |
| ICT (FVG/OB) | NQ | 15 | 0.18 | 0.38 | 0.00 | 0.00 |
| ICT (FVG/OB) | RTY | 15 | -0.30 | -0.14 | 0.00 | 0.00 |
| MA (EMA/SMA/HMA) | ES | 65 | -0.67 | -0.29 | 0.02 | 0.00 |
| MA (EMA/SMA/HMA) | NQ | 65 | -0.29 | -0.27 | 0.02 | 0.03 |
| MA (EMA/SMA/HMA) | RTY | 65 | -0.09 | -0.23 | 0.00 | 0.02 |
| Pivots (classic/Camarilla) | ES | 25 | 0.77 | -0.06 | 0.00 | 0.00 |
| Pivots (classic/Camarilla) | NQ | 25 | 0.32 | 0.52 | 0.08 | 0.00 |
| Pivots (classic/Camarilla) | RTY | 25 | -0.78 | -0.17 | 0.00 | 0.00 |
| Prior-day / overnight extremes | ES | 20 | -0.62 | -0.50 | 0.00 | 0.05 |
| Prior-day / overnight extremes | NQ | 20 | -0.86 | -0.21 | 0.05 | 0.00 |
| Prior-day / overnight extremes | RTY | 20 | 1.29 | 0.76 | 0.10 | 0.00 |
| Round numbers | ES | 10 | -1.83 | -0.79 | 0.00 | 0.00 |
| Round numbers | NQ | 10 | -0.67 | -0.32 | 0.00 | 0.00 |
| Round numbers | RTY | 10 | 1.91 | 0.87 | 0.00 | 0.00 |
| Trend lines (Kijun/PSAR/Supertrend) | ES | 15 | -0.77 | -0.47 | 0.00 | 0.00 |
| Trend lines (Kijun/PSAR/Supertrend) | NQ | 15 | -0.57 | -0.15 | 0.00 | 0.00 |
| Trend lines (Kijun/PSAR/Supertrend) | RTY | 15 | -0.34 | -0.29 | 0.00 | 0.00 |
| VWAP / anchored VWAP | ES | 25 | -0.89 | -0.55 | 0.00 | 0.04 |
| VWAP / anchored VWAP | NQ | 25 | -0.57 | -0.35 | 0.00 | 0.00 |
| VWAP / anchored VWAP | RTY | 25 | -0.01 | -0.27 | 0.00 | 0.00 |

### 2.4 By bar size (core trigger, all levels) with the drift baseline
| bar | inst | mean_excess_pp | mean_z | frac_z3 | mean_rate | mean_null | mean_tdest |
|---|---|---|---|---|---|---|---|
| 1 | ES | -0.21 | -0.28 | 0.00 | 0.49 | 0.49 | 0.49 |
| 1 | NQ | 0.01 | -0.13 | 0.02 | 0.50 | 0.50 | 0.50 |
| 1 | RTY | 0.26 | 0.12 | 0.02 | 0.50 | 0.49 | 0.50 |
| 3 | ES | -0.85 | -0.38 | 0.02 | 0.49 | 0.50 | 0.50 |
| 3 | NQ | 0.01 | -0.23 | 0.00 | 0.50 | 0.50 | 0.50 |
| 3 | RTY | -0.23 | -0.36 | 0.00 | 0.49 | 0.49 | 0.50 |
| 5 | ES | -0.38 | -0.37 | 0.00 | 0.50 | 0.50 | 0.50 |
| 5 | NQ | 0.12 | -0.16 | 0.05 | 0.51 | 0.50 | 0.50 |
| 5 | RTY | -0.24 | -0.27 | 0.00 | 0.50 | 0.50 | 0.50 |
| 15 | ES | 0.98 | 0.24 | 0.00 | 0.51 | 0.50 | 0.51 |
| 15 | NQ | 0.14 | 0.44 | 0.02 | 0.50 | 0.50 | 0.50 |
| 15 | RTY | 0.17 | 0.26 | 0.02 | 0.49 | 0.49 | 0.49 |
| 60 | ES | -1.77 | -0.57 | 0.00 | 0.48 | 0.50 | 0.50 |
| 60 | NQ | -1.79 | -0.45 | 0.02 | 0.49 | 0.50 | 0.50 |
| 60 | RTY | 0.35 | 0.04 | 0.00 | 0.49 | 0.49 | 0.50 |

### 2.5 By trigger (all levels and bar sizes)
| trig | inst | cells | mean_excess_pp | mean_z | frac_z3 |
|---|---|---|---|---|---|
| ENG:0.25:any | ES | 205 | -0.96 | -0.25 | 0.00 |
| ENG:0.25:any | NQ | 205 | -0.32 | -0.10 | 0.00 |
| ENG:0.25:any | RTY | 205 | 0.73 | -0.01 | 0.00 |
| PIN:50:0.25:any | ES | 205 | -0.46 | -0.20 | 0.00 |
| PIN:50:0.25:any | NQ | 205 | -0.79 | -0.16 | 0.00 |
| PIN:50:0.25:any | RTY | 205 | 0.04 | -0.13 | 0.01 |
| RSI:2:30 | ES | 205 | -0.00 | -0.02 | 0.00 |
| RSI:2:30 | NQ | 205 | 0.07 | 0.13 | 0.00 |
| RSI:2:30 | RTY | 205 | 0.45 | 0.12 | 0.01 |
| TCB:0.25:any | ES | 205 | -0.44 | -0.27 | 0.00 |
| TCB:0.25:any | NQ | 205 | -0.30 | -0.11 | 0.02 |
| TCB:0.25:any | RTY | 205 | 0.06 | -0.04 | 0.01 |

### 2.6 Single post-selection read: per level mean over bar sizes of excess pp / z, clean vs H1+H2 vs NQ 2013-22
| level | NQ clean | NQ H1+H2 | NQ 2013-22 | ES clean | ES H1+H2 | RTY clean | RTY H1+H2 |
|---|---|---|---|---|---|---|---|
| EMA:9 | -0.9/-0.4 | +1.1/+0.6 | -1.3/-0.8 | -0.7/-0.5 | -0.3/+0.2 | +0.7/+0.2 | +1.0/+0.4 |
| EMA:20 | -0.1/-0.3 | +1.1/+0.6 | -0.1/-0.3 | -0.7/-0.5 | +1.2/+1.1 | -0.2/-0.4 | +0.4/-0.2 |
| EMA:21 | -0.3/-0.5 | +1.0/+0.5 | -0.1/-0.3 | -0.8/-0.8 | +1.2/+1.3 | -0.3/-0.5 | +0.5/+0.0 |
| EMA:34 | -0.2/-0.3 | -1.0/-0.3 | -0.5/-1.0 | -0.5/-0.5 | +0.9/+1.2 | -0.7/-0.5 | +0.1/+0.2 |
| EMA:50 | +0.4/+0.2 | -0.3/+0.1 | -0.6/-0.9 | -0.9/-0.3 | +1.0/+0.3 | -1.1/-0.9 | +0.1/+0.1 |
| EMA:100 | +0.3/+0.1 | +0.6/+0.7 | -0.3/-0.4 | -0.6/-0.5 | -0.0/-0.4 | +0.7/+0.0 | +0.4/-0.2 |
| EMA:200 | -0.0/+0.1 | +0.9/+0.1 | +0.2/+0.4 | -0.8/+0.3 | +1.6/+0.4 | -0.8/-0.2 | -1.4/+0.0 |
| SMA:20 | -0.3/-0.3 | +0.2/+0.3 | -0.4/-0.7 | -0.6/-0.1 | +0.9/+0.8 | -0.3/-1.0 | +0.1/-0.6 |
| SMA:50 | -0.5/-0.6 | -0.4/+0.5 | -0.4/-1.0 | -0.9/-0.1 | -0.1/-0.4 | -0.4/+0.0 | -0.3/-0.6 |
| SMA:100 | +0.1/-0.5 | +1.3/+0.5 | -0.4/-0.5 | -0.1/-0.1 | +0.8/+0.6 | -0.1/+0.1 | +0.7/+0.3 |
| SMA:200 | -0.8/-0.3 | +0.3/+0.4 | -0.7/-0.9 | -0.3/+0.1 | +1.2/+0.6 | +0.0/-0.4 | -0.4/-0.2 |
| HMA:20 | -0.6/-0.3 | -0.2/+0.0 | -0.5/-0.1 | -1.4/-0.5 | -0.3/+0.0 | +0.8/+0.3 | +0.4/+0.3 |
| HMA:55 | -0.7/-0.4 | +1.4/+1.1 | -0.1/-0.0 | -0.4/-0.2 | +0.0/+1.1 | +0.5/+0.3 | +0.6/-0.0 |
| VWAP_DAY | -1.0/-1.0 | +0.5/+0.3 | -0.8/-1.0 | -0.6/-0.2 | +0.0/+0.4 | -0.0/+0.3 | +1.1/+1.0 |
| VWAP_RTH | -1.0/-0.9 | -0.7/-0.3 | -0.5/+0.1 | -1.0/-1.1 | -2.7/-0.0 | +1.5/+0.4 | -0.7/-0.6 |
| AVWAP_WEEK | -0.0/+0.1 | -0.2/-0.1 | -0.5/-0.7 | -0.6/-0.4 | +0.7/+0.3 | -1.2/-1.4 | +3.9/+2.4 |
| AVWAP_MONTH | -1.2/-0.1 | -0.5/-0.6 | -0.9/-1.0 | -1.8/-0.7 | -4.5/-1.7 | -0.1/-0.3 | +2.1/+1.0 |
| AVWAP_SWING | +0.4/+0.2 | +0.3/+0.5 | -0.1/-0.0 | -0.5/-0.4 | -0.4/-0.4 | -0.2/-0.3 | -0.0/-0.2 |
| BB:2 | -0.5/-0.5 | -0.3/-0.1 | +0.6/+0.8 | -0.5/-0.2 | +0.7/+0.4 | -0.7/-0.3 | +0.2/+0.3 |
| KC:1 | -0.7/-0.0 | +0.5/+0.5 | -0.1/+0.2 | -0.1/+0.6 | -1.0/-0.1 | -0.2/-0.4 | +0.2/-0.1 |
| KC:2 | +0.7/-0.0 | -0.8/-0.4 | +0.3/+0.6 | +0.6/+0.1 | -0.5/-0.2 | +0.5/+0.4 | -0.6/-0.5 |
| KIJUN:26 | -0.1/+0.1 | +0.4/-0.2 | +0.0/-0.1 | -0.6/-0.6 | +0.2/+0.0 | -0.5/-0.7 | +0.5/+0.1 |
| PSAR | -2.1/-0.5 | +0.8/+0.1 | +0.6/+0.7 | -0.2/-0.2 | +2.6/+0.9 | -0.6/-0.3 | +1.9/+0.6 |
| FIB:38.2 | -1.2/-0.6 | +0.5/+0.9 | -0.3/+0.2 | -0.5/-0.1 | -0.5/-0.2 | +0.4/-0.0 | +1.1/+0.4 |
| FIB:50 | -0.1/-0.2 | +0.5/+0.1 | -0.1/-0.1 | -0.5/-0.3 | -0.5/-0.2 | +0.5/+0.4 | -0.3/-0.7 |
| FIB:61.8 | +0.4/+0.3 | +1.1/+0.1 | +0.1/-0.0 | -0.9/-0.5 | +0.3/+0.8 | +0.1/-0.1 | -1.7/-0.9 |
| PD_BRK | -0.1/+0.4 | -0.4/+0.7 | -1.3/-1.8 | -1.9/-1.3 | +1.1/+1.2 | +0.3/+0.5 | -1.2/-0.2 |
| PD_OPP | -2.5/-0.9 | +2.9/+0.5 | -0.0/+0.2 | -0.7/-0.4 | +3.9/+1.5 | +2.6/+1.3 | +3.1/+0.8 |
| ON_BRK | +1.2/+0.3 | +0.7/+0.3 | -1.3/-1.0 | +0.4/-0.2 | -0.6/-1.9 | +1.7/+0.5 | +1.8/+0.8 |
| ON_OPP | -2.0/-0.6 | -1.2/+0.2 | +0.8/+0.6 | -0.3/-0.1 | +0.7/+0.1 | +0.6/+0.7 | +1.0/+0.3 |
| PIV_PP | -0.4/-0.0 | -1.4/-0.6 | +0.2/-0.3 | -0.3/-0.1 | +0.4/+0.1 | -0.8/-0.9 | +0.2/-0.6 |
| PIV_S1R1 | +2.0/+1.2 | +6.1/+1.0 | +0.7/+1.1 | +0.7/-0.0 | -4.7/-1.0 | +0.4/+0.1 | +3.9/+1.2 |
| PIV_S2R2 | -3.1/-0.0 | -10.1/-0.7 | +1.4/+0.4 | +5.0/+0.2 | -3.3/-0.3 | -3.2/-0.1 | -0.4/+0.2 |
| CAM:3 | +1.8/+1.1 | -1.7/-0.6 | -0.0/+0.1 | +0.4/+0.2 | +2.3/+1.1 | +0.8/+0.3 | -0.7/-0.8 |
| CAM:4 | +1.2/+0.4 | +7.2/+1.8 | -1.5/-1.1 | -1.9/-0.6 | -1.0/+0.2 | -1.2/-0.3 | -1.9/-0.3 |
| ROUND:50 | -1.1/-0.7 | +1.1/+0.3 | +0.1/-0.1 | -1.4/-0.7 | -0.1/+0.1 | +1.5/+0.9 | -1.3/+0.1 |
| ROUND:100 | -0.2/+0.0 | +0.6/+0.3 | -0.5/-0.8 | -2.3/-0.9 | -0.4/-0.3 | +2.3/+0.9 | -1.2/-0.5 |
| SUPERTREND | +0.6/-0.0 | -1.4/-0.3 | +0.7/+0.9 | -1.5/-0.6 | -1.4/-0.7 | +0.1/+0.1 | -0.6/-0.3 |
| FVG_TOP | +1.3/+0.8 | +2.5/+0.7 | na | +1.0/+0.9 | +0.4/+0.1 | +0.0/-0.1 | +0.7/+0.5 |
| FVG_MID | -0.2/+0.0 | +2.4/+1.1 | na | +0.8/+0.5 | +2.5/+1.2 | +0.1/-0.0 | +1.9/+0.3 |
| OB_TOP | -0.5/+0.3 | +2.7/+0.8 | na | -0.4/-0.5 | +1.3/+0.7 | -1.0/-0.3 | +0.8/+0.1 |


## 3. Standalone results by family, trigger, bar, session, trend, stop and target (clean span; 1 contract, after costs)
21% of the stage-1 NQ cells with >= 150 clean trades have positive clean Sharpe (median Sharpe is negative: 1 tick/side + commission on ATR-scale stops is the main hurdle, worst at 1-minute bars where only 13% are positive). In the 30 random-level null worlds 24% are positive. Cells at or above the finalist threshold (clean Sharpe >= 1.17, 3,280-cell stage 1): real 11, null worlds 29.9 per world. Search-adjusted: best real stage-1 clean Sharpe 1.58 vs best-of-search in null worlds mean 1.97, p95 2.32, max 2.57 (real exceeds 3% of null worlds); mean of the top-12 distinct bases: real 1.29 vs null 1.59. A real level is not better than a random offset of the same trigger/stop/target on clean.

Factor tables below summarise ALL unique cells (stage 1 + 2). Non-default values of a factor exist only around the 24 best stage-1 bases (a selected sample), so compare values inside a table only where the cell counts are comparable (stage-1 values: trend TR_E50, stops SATR:1.5/SLV:0.5, targets R:1.5/R:3, session ALL).

By level family:
| fam | cells | elig | median_sh | best_sh | share_pos |
|---|---|---|---|---|---|
| Bands (Bollinger/Keltner) | 240 | 228 | -0.87 | 0.96 | 0.08 |
| Fibonacci | 415 | 364 | -0.15 | 1.70 | 0.45 |
| ICT (FVG/OB) | 336 | 302 | -0.12 | 1.52 | 0.44 |
| MA (EMA/SMA/HMA) | 1426 | 1316 | -0.52 | 2.00 | 0.26 |
| Pivots (classic/Camarilla) | 720 | 392 | 0.35 | 2.01 | 0.68 |
| Prior-day / overnight extremes | 368 | 231 | -0.28 | 1.05 | 0.39 |
| Round numbers | 292 | 282 | -0.29 | 1.67 | 0.34 |
| Trend lines (Kijun/PSAR/Supertrend) | 384 | 322 | -0.57 | 1.64 | 0.32 |
| VWAP / anchored VWAP | 594 | 527 | -0.04 | 1.93 | 0.49 |

By trigger kind:
| tk | cells | elig | median_sh | best_sh | share_pos |
|---|---|---|---|---|---|
| CNT | 66 | 33 | 0.24 | 1.48 | 0.67 |
| ENG | 1150 | 845 | -0.41 | 1.93 | 0.34 |
| PIN | 1025 | 813 | -0.42 | 1.99 | 0.31 |
| RSI | 1148 | 1018 | -0.40 | 2.01 | 0.32 |
| STO | 22 | 8 | 0.17 | 1.40 | 0.62 |
| TCB | 1364 | 1247 | -0.09 | 2.00 | 0.45 |

By signal bar (minutes):
| bar | cells | elig | median_sh | best_sh | share_pos |
|---|---|---|---|---|---|
| 1.00 | 752.00 | 663.00 | -2.28 | 2.01 | 0.13 |
| 3.00 | 994.00 | 848.00 | -0.37 | 1.93 | 0.38 |
| 5.00 | 880.00 | 760.00 | -0.37 | 1.99 | 0.33 |
| 15.00 | 1301.00 | 1099.00 | -0.08 | 1.70 | 0.46 |
| 60.00 | 848.00 | 594.00 | 0.00 | 2.00 | 0.50 |

By session (kill zones are stage-2 cells around the best bases only):
| session | cells | elig | median_sh | best_sh | share_pos |
|---|---|---|---|---|---|
| ALL | 4607 | 3897.00 | -0.34 | 2.01 | 0.36 |
| ASIA | 24 | nan | nan | nan | nan |
| GLOBEX | 24 | 17.00 | 0.48 | 1.38 | 0.76 |
| LDNCLOSE | 24 | 8.00 | 1.25 | 1.99 | 1.00 |
| LONDON | 24 | 7.00 | -0.35 | -0.17 | 0.00 |
| NYAM | 24 | 8.00 | 0.59 | 1.42 | 0.62 |
| NYPM | 24 | 7.00 | 0.12 | 0.95 | 0.71 |
| RTH | 24 | 20.00 | 1.16 | 1.79 | 1.00 |

By trend filter:
| trend | cells | elig | median_sh | best_sh | share_pos |
|---|---|---|---|---|---|
| TR0 | 24 | 24 | 0.67 | 1.02 | 0.67 |
| TR_ADX:15 | 24 | 22 | 1.10 | 1.55 | 1.00 |
| TR_ADX:20 | 24 | 20 | 1.10 | 1.67 | 1.00 |
| TR_ADX:25 | 24 | 16 | 0.76 | 1.47 | 1.00 |
| TR_E200 | 24 | 22 | 0.45 | 1.00 | 0.86 |
| TR_E50 | 4535 | 3771 | -0.36 | 2.01 | 0.35 |
| TR_LVL | 24 | 13 | 0.19 | 1.14 | 0.62 |
| TR_PAGREE | 24 | 14 | -0.12 | 0.87 | 0.43 |
| TR_PHM | 24 | 18 | 0.05 | 1.04 | 0.50 |
| TR_PST | 24 | 20 | 0.18 | 1.38 | 0.65 |
| TR_ST | 24 | 24 | 0.71 | 1.34 | 0.92 |

By stop:
| stop | cells | elig | median_sh | best_sh | share_pos |
|---|---|---|---|---|---|
| SATR:1 | 103 | 101 | 0.41 | 2.01 | 0.81 |
| SATR:1.5 | 2300 | 1888 | -0.35 | 2.00 | 0.35 |
| SATR:2 | 103 | 98 | 0.55 | 1.72 | 0.86 |
| SLV:0.25 | 103 | 100 | 0.38 | 1.64 | 0.65 |
| SLV:0.5 | 2063 | 1679 | -0.54 | 1.84 | 0.29 |
| SPB | 103 | 98 | 0.61 | 1.95 | 0.88 |

By target:
| target | cells | elig | median_sh | best_sh | share_pos |
|---|---|---|---|---|---|
| HTFLV | 63 | 54 | 0.22 | 1.93 | 0.67 |
| R:1 | 63 | 63 | 0.51 | 1.95 | 0.81 |
| R:1.5 | 2306 | 1847 | -0.44 | 2.01 | 0.32 |
| R:2 | 63 | 63 | 0.77 | 1.48 | 0.95 |
| R:3 | 1902 | 1582 | -0.48 | 1.67 | 0.28 |
| SWING | 63 | 55 | 0.29 | 1.55 | 0.65 |
| TM:120 | 63 | 62 | 0.53 | 1.62 | 0.87 |
| TM:30 | 63 | 63 | 0.44 | 1.72 | 0.78 |
| TM:60 | 63 | 63 | 0.84 | 2.00 | 0.83 |
| TRAIL | 63 | 63 | 0.45 | 1.34 | 0.76 |
| VWAPB | 63 | 49 | 0.20 | 1.13 | 0.65 |


**Best clean cell per family / trigger kind / bar with the single H1/H2 read** (standalone, 1 NQ contract; selection on clean only):
| group | value | cell | clean_sh | clean_n | H1_sh | H1_n | H2_sh | H2_n |
|---|---|---|---|---|---|---|---|---|
| fam | Bands (Bollinger/Keltner) | 3/KC:2/ENG:0.25:any/TR_E50/SLV:0.5/R:1.5/ALL | 0.96 | 877 | -1.55 | 207 | -2.79 | 288 |
| fam | Fibonacci | 15/FIB:61.8/TCB:0.5:first/TR_E50/SATR:1.5/R:1.5/ALL | 1.70 | 476 | 1.15 | 121 | -0.52 | 165 |
| fam | ICT (FVG/OB) | 3/FVG_TOP/TCB:0.25:any/TR_E50/SATR:1.5/R:3/RTH | 1.52 | 1833 | 1.73 | 437 | -1.23 | 615 |
| fam | MA (EMA/SMA/HMA) | 60/EMA:50/TCB:0.25:any/TR_E50/SATR:1.5/TM:60/ALL | 2.00 | 596 | -1.01 | 145 | -1.09 | 226 |
| fam | Pivots (classic/Camarilla) | 1/PIV_S1R1/RSI:2:30/TR_E50/SATR:1/R:1.5/ALL | 2.01 | 449 | -0.86 | 140 | 0.08 | 163 |
| fam | Prior-day / overnight extremes | 15/ON_BRK/ENG:0.25:any/TR_ADX:15/SATR:1.5/R:3/ALL | 1.05 | 175 | -0.34 | 39 | 0.90 | 50 |
| fam | Round numbers | 15/ROUND:100/TCB:0.25:any/TR_ADX:20/SATR:1.5/R:3/ALL | 1.67 | 1204 | -0.22 | 320 | 0.34 | 497 |
| fam | Trend lines (Kijun/PSAR/Supertrend) | 15/PSAR/TCB:0.25:any/TR_E50/SLV:0.5/R:1.5/RTH | 1.64 | 606 | 1.19 | 159 | 0.78 | 173 |
| fam | VWAP / anchored VWAP | 3/AVWAP_WEEK/ENG:0.25:any/TR_E50/SATR:1.5/HTFLV/ALL | 1.93 | 476 | 1.95 | 117 | 0.14 | 157 |
| tk | CNT | 15/HMA:20/CNT:3/TR_E50/SATR:1.5/R:1.5/ALL | 1.48 | 399 | -0.91 | 91 | -1.36 | 144 |
| tk | ENG | 3/AVWAP_WEEK/ENG:0.25:any/TR_E50/SATR:1.5/HTFLV/ALL | 1.93 | 476 | 1.95 | 117 | 0.14 | 157 |
| tk | PIN | 5/EMA:200/PIN:50:0.25:any/TR_E50/SATR:1.5/R:1.5/LDNCLOSE | 1.99 | 245 | -0.19 | 45 | 1.66 | 62 |
| tk | RSI | 1/PIV_S1R1/RSI:2:30/TR_E50/SATR:1/R:1.5/ALL | 2.01 | 449 | -0.86 | 140 | 0.08 | 163 |
| tk | STO | 15/HMA:20/STO/TR_E50/SATR:1.5/R:1.5/ALL | 1.40 | 507 | 1.37 | 125 | 1.12 | 167 |
| tk | TCB | 60/EMA:50/TCB:0.25:any/TR_E50/SATR:1.5/TM:60/ALL | 2.00 | 596 | -1.01 | 145 | -1.09 | 226 |
| bar | 1 | 1/PIV_S1R1/RSI:2:30/TR_E50/SATR:1/R:1.5/ALL | 2.01 | 449 | -0.86 | 140 | 0.08 | 163 |
| bar | 3 | 3/AVWAP_WEEK/ENG:0.25:any/TR_E50/SATR:1.5/HTFLV/ALL | 1.93 | 476 | 1.95 | 117 | 0.14 | 157 |
| bar | 5 | 5/EMA:200/PIN:50:0.25:any/TR_E50/SATR:1.5/R:1.5/LDNCLOSE | 1.99 | 245 | -0.19 | 45 | 1.66 | 62 |
| bar | 15 | 15/FIB:61.8/TCB:0.5:first/TR_E50/SATR:1.5/R:1.5/ALL | 1.70 | 476 | 1.15 | 121 | -0.52 | 165 |
| bar | 60 | 60/EMA:50/TCB:0.25:any/TR_E50/SATR:1.5/TM:60/ALL | 2.00 | 596 | -1.01 | 145 | -1.09 | 226 |

The picture is the same everywhere: strong clean Sharpe (1.0-2.0) collapses to about 0 +/- 1 in H1/H2.

## 4. Finalists (top 12 distinct (bar, level, trigger) bases by clean weekly Sharpe, >= 150 clean trades; list frozen in pb/FINALISTS_frozen.json before the H1/H2 read)
Standalone (1 NQ contract) and additive 20% uplift of weekly Sharpe vs the live pair (ww_chg = worst-week change, limit +20%):
| i | cell | n_pairwin | sa_clean | sa_H1 | sa_H2 | sa_all | up_clean | up_H1 | up_H2 | up_all | ww_chg |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | b1/PIV_S1R1/RSI:2:30/TR_E50/SATR:1/R:1.5/ALL | 752 | 2.01 | -0.86 | 0.08 | 0.86 | +0.24 | -0.16 | -0.24 | +0.05 | +21.7% |
| 1 | b60/EMA:50/TCB:0.25:any/TR_E50/SATR:1.5/TM:60/ALL | 967 | 2.00 | -1.01 | -1.09 | 0.56 | +0.37 | -0.27 | -0.50 | +0.08 | +25.5% |
| 2 | b5/EMA:200/PIN:50:0.25:any/TR_E50/SATR:1.5/R:1.5/LDNCLOSE | 352 | 1.99 | -0.19 | 1.66 | 1.59 | +0.36 | -0.15 | +0.33 | +0.29 | +21.3% |
| 3 | b5/CAM:3/TCB:0.25:any/TR_E50/SPB/R:1/ALL | 536 | 1.95 | 1.05 | -0.74 | 1.12 | +0.31 | +0.04 | -0.23 | +0.16 | +18.5% |
| 4 | b3/AVWAP_WEEK/ENG:0.25:any/TR_E50/SATR:1.5/HTFLV/ALL | 750 | 1.93 | 1.95 | 0.14 | 1.40 | +0.32 | +0.72 | -0.16 | +0.25 | +31.1% |
| 5 | b5/CAM:3/TCB:0.5:any/TR_E50/SLV:0.5/R:1.5/ALL | 760 | 1.84 | 1.15 | 0.35 | 1.32 | +0.31 | +0.11 | +0.00 | +0.22 | +25.2% |
| 6 | b15/FIB:61.8/TCB:0.5:first/TR_E50/SATR:1.5/R:1.5/ALL | 762 | 1.70 | 1.15 | -0.52 | 1.00 | +0.28 | -0.02 | -0.34 | +0.10 | +28.4% |
| 7 | b15/FIB:61.8/TCB:0.25:first/TR_E50/SATR:1.5/R:1.5/ALL | 699 | 1.69 | -0.47 | -0.38 | 0.79 | +0.25 | -0.28 | -0.36 | +0.04 | +34.0% |
| 8 | b15/ROUND:100/TCB:0.25:any/TR_ADX:20/SATR:1.5/R:3/ALL | 2021 | 1.67 | -0.22 | 0.34 | 1.01 | +0.23 | +0.03 | -0.16 | +0.10 | +6.1% |
| 9 | b1/PIV_S1R1/RSI:7:50/TR_E50/SATR:1.5/R:1.5/ALL | 542 | 1.67 | -1.44 | -0.61 | 0.53 | +0.24 | -0.41 | -0.30 | +0.02 | +56.2% |
| 10 | b15/PSAR/TCB:0.25:any/TR_E50/SLV:0.5/R:1.5/RTH | 938 | 1.64 | 1.19 | 0.78 | 1.41 | +0.26 | +0.11 | +0.08 | +0.20 | +9.9% |
| 11 | b5/CAM:3/RSI:2:30/TR_ADX:20/SLV:0.5/R:1.5/ALL | 348 | 1.59 | 1.17 | 0.59 | 1.32 | +0.27 | -0.03 | +0.01 | +0.18 | +13.7% |

Gates (20% share; g3 = uplift >= +0.10 on clean, H1 and H2 and worst week within share; g4 = standalone all-in Sharpe above p95 of BOTH the timing-destroyed and the random-level null AND bootstrap 90% CI > 0; g5 = plateau >= 75% of exact +/-25% neighbours keep >= 75% of uplift AND 2x-slippage uplift >= +0.10 on each span; g6 = worst-decile-week correlation <= +0.30; ES / RTY / H0 = all-in additive 20% uplift of the same rule on ES, RTY and on 2023-02-10..2023-07-31; nrep = number of {ES, RTY, H0} with the same sign and >= 50% of the NQ uplift):
| i | boot | nul_t | nul_l | plat | sl2 | wd | ES | RTY | H0 | era | g3 | g4 | g5 | g6 | nrep |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 0 | [-0.14,+0.25] | 0.86 vs -0.09 | 0.67 | 0.17 (6) | +0.17/-0.28/-0.31 | 0.09 | -0.45 | -0.26 | -0.07 | negative pre-2023 | False | False | False | True | 0 |
| 1 | [-0.14,+0.32] | 0.56 vs 0.76 | 0.53 | 0.25 (8) | +0.34/-0.31/-0.54 | -0.25 | -0.31 | -0.24 | +0.17 | positive pre-2023 | False | False | False | True | 1 |
| 2 | [+0.10,+0.49] | 1.59 vs 0.80 | 0.78 | 0.40 (10) | +0.34/-0.17/+0.32 | -0.56 | +0.06 | +0.08 | -0.31 | negative pre-2023 | False | True | False | True | 0 |
| 3 | [-0.03,+0.34] | 1.12 vs 0.50 | 0.77 | 1.00 (4) | +0.29/+0.02/-0.26 | -0.47 | -0.06 | +0.08 | +0.02 | positive pre-2023 | False | False | False | True | 0 |
| 4 | [+0.03,+0.49] | 1.40 vs 0.42 | 0.65 | 0.50 (4) | +0.27/+0.67/-0.20 | -0.11 | -0.08 | -0.15 | -0.26 | negative pre-2023 | False | True | False | True | 0 |
| 5 | [+0.03,+0.44] | 1.32 vs 0.31 | 0.52 | 0.67 (6) | +0.27/+0.08/-0.03 | -0.41 | -0.02 | +0.01 | +0.01 | gross-positive, cost-negative pre-2023 | False | True | False | True | 0 |
| 6 | [-0.10,+0.30] | 1.00 vs 0.81 | 0.39 | 0.25 (8) | +0.25/-0.04/-0.37 | -0.33 | +0.03 | -0.27 | -0.14 | negative pre-2023 | False | False | False | True | 0 |
| 7 | [-0.15,+0.23] | 0.79 vs 0.79 | 0.27 | 0.12 (8) | +0.22/-0.31/-0.39 | -0.21 | +0.04 | -0.13 | -0.15 | negative pre-2023 | False | False | False | True | 1 |
| 8 | [-0.09,+0.28] | 1.01 vs 0.77 | 0.25 | 0.20 (10) | +0.20/-0.01/-0.19 | -0.54 | -0.10 | -0.05 | -0.21 | gross-positive, cost-negative pre-2023 | False | False | False | True | 0 |
| 9 | [-0.19,+0.22] | 0.53 vs 0.17 | 0.84 | 0.10 (10) | +0.20/-0.48/-0.34 | -0.16 | -0.30 | -0.14 | +0.19 | negative pre-2023 | False | False | False | True | 1 |
| 10 | [+0.05,+0.35] | 1.41 vs 0.62 | 0.37 | 0.67 (6) | +0.23/+0.09/+0.07 | -0.55 | -0.13 | -0.14 | +0.05 | negative pre-2023 | False | True | False | True | 0 |
| 11 | [-0.00,+0.38] | 1.32 vs 0.73 | 0.92 | 0.50 (8) | +0.26/-0.05/-0.01 | -0.65 | -0.09 | -0.01 | +0.04 | negative pre-2023 | False | False | False | True | 0 |

Summary: g3 0/12 at 20% (1/12 at 30%), g4 4/12, g5 0/12, g6 12/12 (every sleeve is negatively or weakly correlated with the pair in its worst weeks; that is not the problem), replication (>= 2 of 3): 0/12. The nulls pass for 4 finalists because the all-in window contains the selection span; the nulls are per-cell, not search-adjusted (see sections 1 and 6).

Constant-risk framing: all 12 finalists are NO (no INSURANCE verdict at 10/20/30/50%); the PSAR lead has the best profile (30% share, all-in: Sharpe 1.86 -> 2.18, worst week -82.5k -> -74.2k, CVaR5 +19.6%, max DD -34%, net -7.7%), but its clean/H1 CVaR5 and DD are not uniformly better and the standard INSURANCE test (rep_common / t3 verdict: >= 20% worst-week or CVaR5 gain with non-negative clean and H1 gains) is not met.

### 4.1 The lead: NQ 15-min Parabolic-SAR pullback (finalist 10)
Rule (pre-registered cell NQ|b15|PSAR|TCB:0.25:any|TR_E50|SLV:0.5|R:1.5|RTH): 15-minute bars; long when the HTF (60-min) EMA50 slope is up, the previous 15-min close was above the SAR in force, the bar's low reached SAR + 0.25 ATR(14) and the bar closed above the SAR (mirror for shorts); entry market at the next 1-minute open, only if that minute is within 09:30-16:00 ET; stop = SAR - 0.5 ATR(14) (0.5 ATR beyond the level), target 1.5R, flat at 16:55, one position. 938 trades in the pair window (about 6.5 per 10 days), standalone 1 contract: clean / H1 / H2 / all-in weekly Sharpe 1.64 / 1.19 / 0.78 / 1.41, net $89.6k / $17.8k / $12.4k.
All shares (additive and constant-risk):
| framing | share | clean | H1 | H2 | all_in | ww_chg | cvar5_impr | dd_impr | net_pct | boot | shift_p95 | verdict |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| add | 10 | 0.14 | 0.08 | 0.05 | 0.11 | 1.80 | -2.00 | 3.18 | 7.43 | [+0.03,+0.19] | 0.15 | NO |
| add | 20 | 0.26 | 0.11 | 0.08 | 0.20 | 9.92 | -5.83 | 6.36 | 14.87 | [+0.05,+0.35] | 0.29 | NO |
| add | 30 | 0.35 | 0.11 | 0.10 | 0.27 | 18.04 | -9.75 | 9.54 | 22.30 | [+0.05,+0.49] | 0.40 | NO |
| add | 50 | 0.49 | 0.04 | 0.10 | 0.35 | 34.28 | -17.60 | 3.59 | 37.17 | [+0.03,+0.69] | 0.55 | NO |
| const | 10 | 0.15 | 0.08 | 0.05 | 0.12 | -7.57 | 7.87 | 13.18 | -2.57 | [+0.03,+0.21] | 0.17 | NO |
| const | 20 | 0.31 | 0.12 | 0.09 | 0.24 | -8.81 | 13.77 | 26.36 | -5.13 | [+0.05,+0.42] | 0.34 | NO |
| const | 30 | 0.45 | 0.08 | 0.11 | 0.33 | -10.06 | 19.64 | 34.39 | -7.70 | [+0.04,+0.63] | 0.51 | NO |
| const | 50 | 0.61 | -0.26 | -0.05 | 0.35 | -12.56 | 27.31 | 42.40 | -12.83 | [-0.18,+0.92] | 0.61 | NO |

Gates at 20%: gate 3 **fails** (H2 +0.08 < +0.10). At 30% gate 3 passes narrowly (clean +0.35 / H1 +0.11 / H2 +0.10, worst week +18% within the 30% limit; the circular-shift null p95 0.40 vs all-in uplift +0.27 is not passed, reported only) - the only finalist/share combination that does - but at 30% the plateau is again 4 of 6 and the 2x-slippage uplift is +0.32 / +0.08 / +0.08, so gates 3 and 5 are not met together at any share. Own nulls PASS (all-in Sharpe 1.41 vs timing-destroyed p95 0.62 and random-level p95 0.37); bootstrap 90% CI [+0.05, +0.35] PASS; worst-decile correlation -0.55 PASS; plateau **4 of 6** exact neighbours (67% < 75%) FAIL; 2x slippage uplift +0.23 / +0.09 / +0.07 (standalone all-in 1.30) FAIL on H1/H2; replication **fails** (ES all-in uplift -0.13, RTY -0.14; H0 window +0.05 = 25% of +0.20; no ES/RTY edge: standalone all-in ES -0.25, RTY -0.51; odd/even month diagnostics +0.19/+0.23 but that is in-sample for the clean selection). ERA flag: **negative pre-2023** (2013-2022: 2,829 trades, gross -$6/trade, net -$20.5 fixed-cost, -$11.0 price-scaled, weekly Sharpe -0.58; 2023-2026 gross +$146/trade): the rule earns only in the post-2023 regime (2025: $80k per contract). Mechanism in one sentence: in the trending 2023-26 tape a first dip to the SAR of the 15-min trend inside RTH was followed by continuation. It plausibly depends on current structure (positive persistence of intraday trends since 2023), not on anything level-specific: the same trigger/stop/target on randomly shifted levels earns a median -0.12 Sharpe but the best 5% of shifted levels reach +0.37, and the null-world best-of-search exceeds the real best, so the SAR is not shown to be special.
Plateau detail:
| neighbour | tag | trades | up_clean | up_H1 | up_H2 | up_all | keeps75 |
|---|---|---|---|---|---|---|---|
| NQ/b15/PSAR/TCB:0.1875:any/TR_E50/SLV:0.5/R:1.5/RTH | trig0.75 | 870 | 0.26 | 0.06 | 0.14 | 0.21 | True |
| NQ/b15/PSAR/TCB:0.25:any/TR_E50/SLV:0.375/R:1.5/RTH | stop0.75 | 973 | 0.15 | 0.05 | 0.09 | 0.12 | False |
| NQ/b15/PSAR/TCB:0.25:any/TR_E50/SLV:0.5/R:1.125/RTH | tgt0.75 | 983 | 0.13 | 0.01 | 0.02 | 0.09 | False |
| NQ/b15/PSAR/TCB:0.3125:any/TR_E50/SLV:0.5/R:1.5/RTH | trig1.25 | 1007 | 0.27 | 0.13 | 0.09 | 0.21 | True |
| NQ/b15/PSAR/TCB:0.25:any/TR_E50/SLV:0.625/R:1.5/RTH | stop1.25 | 916 | 0.27 | 0.13 | 0.05 | 0.20 | True |
| NQ/b15/PSAR/TCB:0.25:any/TR_E50/SLV:0.5/R:1.875/RTH | tgt1.25 | 904 | 0.26 | 0.05 | 0.09 | 0.19 | True |

Insurance metric set (pair vs additive/constant-risk 20% and 30%; $):
| span | book | sharpe | sortino | mar | maxdd | worst_week | cvar5 | cvar10 | neg_wk_pct | net |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | 280110 | -81874 | -78736 | -78009 | 42.86 | 1329959 |
| clean | add 20% | 1.71 | 3.40 | 6.21 | 262288 | -90712 | -83294 | -80299 | 40.00 | 1628542 |
| clean | add 30% | 1.81 | 3.68 | 7.02 | 253377 | -97413 | -86246 | -81483 | 40.00 | 1777834 |
| clean | const 20% | 1.77 | 3.54 | 6.61 | 206266 | -75250 | -67816 | -64713 | 40.00 | 1362550 |
| clean | const 30% | 1.91 | 3.99 | 8.14 | 169344 | -74220 | -63029 | -58104 | 42.86 | 1378846 |
| H1 | pair | 2.83 | 6.09 | 3.91 | 151713 | -78287 | -77610 | -66030 | 39.29 | 593797 |
| H1 | add 20% | 2.94 | 6.22 | 4.14 | 157777 | -82082 | -81867 | -73046 | 35.71 | 653149 |
| H1 | add 30% | 2.94 | 6.23 | 4.25 | 160810 | -84013 | -83996 | -76720 | 39.29 | 682824 |
| H1 | const 20% | 2.94 | 6.23 | 4.19 | 127435 | -66424 | -66345 | -59906 | 35.71 | 534389 |
| H1 | const 30% | 2.90 | 6.21 | 4.38 | 115296 | -60933 | -60713 | -57011 | 35.71 | 504685 |
| H2 | pair | 2.30 | 4.69 | 3.50 | 217425 | -82524 | -81089 | -79185 | 44.44 | 761254 |
| H2 | add 20% | 2.38 | 5.08 | 3.37 | 238475 | -89939 | -84745 | -75589 | 41.67 | 802516 |
| H2 | add 30% | 2.40 | 5.17 | 3.31 | 249000 | -96200 | -87850 | -77068 | 38.89 | 823147 |
| H2 | const 20% | 2.39 | 5.13 | 3.33 | 194990 | -74455 | -69038 | -61063 | 44.44 | 650265 |
| H2 | const 30% | 2.40 | 5.18 | 3.24 | 183773 | -72975 | -64289 | -56682 | 38.89 | 594770 |
| all | pair | 1.86 | 3.63 | 9.59 | 280110 | -82524 | -79220 | -78243 | 42.86 | 2685011 |
| all | add 20% | 2.05 | 4.16 | 11.76 | 262288 | -90712 | -83835 | -79659 | 39.88 | 3084206 |
| all | add 30% | 2.12 | 4.37 | 12.96 | 253377 | -97413 | -86945 | -80899 | 39.88 | 3283804 |
| all | const 20% | 2.09 | 4.27 | 12.35 | 206266 | -75250 | -68312 | -64217 | 40.48 | 2547204 |
| all | const 30% | 2.18 | 4.58 | 13.49 | 183773 | -74220 | -63660 | -58125 | 41.07 | 2478301 |

ERA (2013-2026 NQ long series; costs fixed vs scaled by price/ price at entry / 21912):
| period | trades | gross | net_fixed | net_scaled |
|---|---|---|---|---|
| 2013-2022 | 2829 | -6.14 | -20.50 | -10.96 |
| 2023-2026 | 1109 | 145.66 | 131.30 | 132.32 |
| 2013-2026 | 3938 | 36.61 | 22.25 | 29.39 |

| year | trades | net_fixed | net_scaled |
|---|---|---|---|
| 2013.00 | 301.00 | -5746.45 | -2027.75 |
| 2014.00 | 289.00 | 1028.09 | 4449.16 |
| 2015.00 | 293.00 | -727.06 | 2628.60 |
| 2016.00 | 264.00 | -4850.88 | -1849.49 |
| 2017.00 | 272.00 | -3592.85 | -710.13 |
| 2018.00 | 288.00 | -5364.78 | -2555.09 |
| 2019.00 | 266.00 | -10729.08 | -8238.73 |
| 2020.00 | 299.00 | -7783.14 | -5497.57 |
| 2021.00 | 266.00 | -15841.67 | -14538.01 |
| 2022.00 | 291.00 | -4389.22 | -2654.80 |
| 2023.00 | 308.00 | 20794.76 | 22335.42 |
| 2024.00 | 295.00 | 20293.35 | 20810.70 |
| 2025.00 | 311.00 | 80343.33 | 80174.84 |
| 2026.00 | 195.00 | 24175.24 | 23421.27 |

NT8 spec: NinjaTrader 8, NQ continuous (roll at the pair's roll dates), 15-minute series + 60-minute series; indicators Parabolic SAR (0.02, 0.2) with the value in force into the bar (verify NT8's ParabolicSAR[1] vs [0] alignment against pb core `_psar`), EMA(50) on the 60-minute series (slope sign of the last completed 60-min bar), ATR(14) on the 15-min series; orders: EnterLong/Short at the next 1-minute open (Calculate.OnBarClose on the 15-min series, entry on the next primary-series tick/minute), SetStopLoss / SetProfitTarget with prices computed at signal time; time filter 09:30-16:00 entry, ExitOnClose at 16:55. Sizing: sleeve scale factor 16.7 NQ contracts per 100% pair-risk share (3.3 contracts at 20%). Needs its own account (nets against ST/HM on NQ; net class NQ_INTRADAY). Not recommended for live use: it fails plateau, 2x slippage, replication and ERA; carried only as a lead for the live-weeks forward test.

## 5. Pair-side results
### 5.1 (a) The pair's own entries re-timed as pullbacks (32 cells)
Setup: for each of the 13,089 live pair rows the market entry at the flip is replaced by a resting limit at min(original entry price, prevailing level) (long; max for short) with level in {EMA9(1m), EMA20(1m), EMA20(5m), session VWAP} updated each minute, cancelled (trade skipped) if not filled within N in {5, 15, 30, 60} minutes; X_ABS = the original absolute stop/target prices and the original exit (pathwise exact: the new fill sits on the same price path, so the trade exits where the original did, P&L = side x (original exit price - fill)); X_REB = a fresh +/-60-point bracket from the fill re-simulated on 1-minute bars (stop first on ties; exit-bar match with the recorded exits at N=0 is 90%, sign match 98%, so X_REB is approximate; mark-to-market for the day/week locks uses the fill price). The patched rows run through B.run with the live rules; the identity patch reproduces the baseline exactly (asserted), baseline 1.46 / 2.83 / 2.30.
Uplift of weekly Sharpe vs the live pair (clean / H1 / H2 / all-in); ww_chg = all-in worst-week change %:
| level | N_min | exit | trades | up_clean | up_H1 | up_H2 | up_all | ww_chg_pct |
|---|---|---|---|---|---|---|---|---|
| EMA20 | 5 | ABS | 4548 | -0.02 | -1.07 | -0.51 | -0.27 | -5.31 |
| EMA20 | 5 | REB | 4387 | +0.18 | -0.60 | -2.23 | -0.47 | -3.53 |
| EMA20 | 15 | ABS | 6333 | -0.38 | +0.98 | -0.73 | -0.23 | -2.20 |
| EMA20 | 15 | REB | 6030 | -0.39 | -0.44 | -0.58 | -0.40 | -4.24 |
| EMA20 | 30 | ABS | 6668 | -0.27 | +1.75 | -0.61 | -0.04 | -2.02 |
| EMA20 | 30 | REB | 6380 | -0.23 | +0.36 | -0.94 | -0.26 | -2.52 |
| EMA20 | 60 | ABS | 6745 | -0.09 | +0.88 | -0.24 | +0.02 | -2.02 |
| EMA20 | 60 | REB | 6437 | +0.04 | -0.35 | -0.82 | -0.20 | -2.17 |
| EMA20_5m | 5 | ABS | 2083 | -0.15 | -1.75 | -1.85 | -0.81 | -4.26 |
| EMA20_5m | 5 | REB | 2055 | -0.30 | -1.70 | -0.85 | -0.63 | -4.76 |
| EMA20_5m | 15 | ABS | 3356 | +0.07 | -1.23 | -1.60 | -0.55 | -6.38 |
| EMA20_5m | 15 | REB | 3285 | -0.71 | -1.86 | -0.79 | -0.88 | -4.19 |
| EMA20_5m | 30 | ABS | 4508 | -1.08 | -1.91 | -0.95 | -1.15 | -4.61 |
| EMA20_5m | 30 | REB | 4365 | -1.40 | -1.72 | -0.18 | -1.14 | -2.15 |
| EMA20_5m | 60 | ABS | 5560 | -0.60 | -3.02 | -1.01 | -1.03 | -2.87 |
| EMA20_5m | 60 | REB | 5336 | -0.55 | -2.90 | -2.48 | -1.41 | -2.76 |
| EMA9 | 5 | ABS | 5848 | -0.48 | -0.62 | +0.28 | -0.27 | -2.42 |
| EMA9 | 5 | REB | 5661 | +0.27 | -0.88 | +0.54 | +0.17 | -2.95 |
| EMA9 | 15 | ABS | 6735 | -0.44 | +0.94 | +0.68 | +0.06 | -0.61 |
| EMA9 | 15 | REB | 6475 | +0.04 | +0.40 | -0.42 | +0.03 | -2.84 |
| EMA9 | 30 | ABS | 6924 | -0.13 | +1.25 | -0.21 | +0.08 | -4.37 |
| EMA9 | 30 | REB | 6554 | +0.05 | +0.53 | -1.43 | -0.17 | -2.44 |
| EMA9 | 60 | ABS | 6915 | -0.12 | +0.67 | -0.07 | +0.04 | -4.57 |
| EMA9 | 60 | REB | 6476 | -0.04 | +0.13 | -1.57 | -0.34 | 3.11 |
| VWAP | 5 | ABS | 2191 | -1.05 | -0.80 | -3.55 | -1.64 | 3.59 |
| VWAP | 5 | REB | 2141 | -0.61 | -1.47 | -3.50 | -1.43 | 13.98 |
| VWAP | 15 | ABS | 2840 | -1.00 | -1.84 | -2.70 | -1.53 | 3.59 |
| VWAP | 15 | REB | 2744 | -0.60 | -2.66 | -3.15 | -1.47 | 3.45 |
| VWAP | 30 | ABS | 3328 | -0.88 | -2.31 | -2.52 | -1.50 | -5.34 |
| VWAP | 30 | REB | 3179 | -0.43 | -2.98 | -3.91 | -1.60 | -4.34 |
| VWAP | 60 | ABS | 3800 | -0.99 | -2.48 | -2.65 | -1.62 | -0.32 |
| VWAP | 60 | REB | 3671 | -1.05 | -2.70 | -4.72 | -2.08 | -4.27 |

**0 of 32 pass gate 3** (best all-in uplift +0.17; mean -0.71; only 6 cells are positive on clean). Mechanism check: ST/HM flips are momentum entries; waiting for a retrace skips the fast continuation trades that carry the P&L while the retrace fills are adverse-selected; VWAP and 5-minute EMA20 retraces (rare, deep) are the worst (-0.5 to -2.1). Consistent with E5 (limit entries NO). No null run (no cell passes gate 3).
### 5.2 (b) Pullback-depth size tilt (12 cells)
Depth = side-signed distance of the entry price from the level in ATR(1m) units; multiplier 1 + sg x a x (2u - 1) from the expanding percentile u of prior entries (first 100 entries x1), a in {0.25, 0.5}, sg in {+1 bigger when extended, -1 bigger when pulled back}.
| depth_level | a | sign | trades | up_clean | up_H1 | up_H2 | up_all | ww_chg_pct |
|---|---|---|---|---|---|---|---|---|
| EMA20 | 0.25 | 1 | 7196 | -0.33 | +0.63 | -0.28 | -0.17 | -4.14 |
| EMA20 | 0.25 | -1 | 7303 | -0.22 | -0.26 | -0.65 | -0.31 | 1.06 |
| EMA20 | 0.50 | 1 | 7121 | -0.22 | +0.09 | -0.51 | -0.25 | 2.72 |
| EMA20 | 0.50 | -1 | 7089 | -0.50 | -2.19 | -0.70 | -0.80 | -0.05 |
| EMA20_5m | 0.25 | 1 | 7127 | -0.08 | +0.58 | -0.25 | +0.02 | 2.09 |
| EMA20_5m | 0.25 | -1 | 7358 | -0.44 | -0.31 | -0.66 | -0.47 | -1.49 |
| EMA20_5m | 0.50 | 1 | 7079 | -0.11 | +0.88 | +0.95 | +0.33 | 4.96 |
| EMA20_5m | 0.50 | -1 | 7361 | -0.52 | -1.24 | -0.99 | -0.72 | -1.62 |
| VWAP | 0.25 | 1 | 7356 | -0.03 | +0.32 | -0.15 | +0.01 | 1.08 |
| VWAP | 0.25 | -1 | 7172 | -0.33 | +0.19 | -0.74 | -0.35 | -1.74 |
| VWAP | 0.50 | 1 | 7141 | -0.73 | -0.52 | +0.64 | -0.32 | -2.52 |
| VWAP | 0.50 | -1 | 7147 | -0.09 | -0.54 | -1.51 | -0.50 | 2.26 |

**0 of 12 pass gate 3** (best all-in +0.33, mean -0.30); the sign-flipped tilts are all negative, and the best (5-min EMA20, a=0.5, bigger when extended) is clean -0.11.
### 5.3 (c) ES and RTY confirmation
Respect: ES and RTY show the same null picture (section 2.2; mean excess -0.4 pp ES, 0.0 pp RTY on the core trigger). Strategy screens with the identical 3,280-cell grid (report-only): ES best clean Sharpe 1.16 (null-world best-of-search mean 1.50, p95 1.82), RTY 1.08 (null mean 1.11, p95 1.37); only 5% (ES) and 4% (RTY) of eligible cells are positive on clean. NQ finalists on ES / RTY (identical parameters, additive 20% uplift all-in): ES positive in 3 of 12 (max +0.06), RTY positive in 3 of 12 (max +0.08), 0 of 12 reach 50% of the NQ uplift. Camarilla L3 (CAM:3) appears in the top clean cells of NQ, ES and RTY alike but fades in H2 on all three.

**ES top clean cells (identical grid, report-only), with the single H1/H2 read**

| inst | cell | n_clean | clean_sh | H1_sh | H2_sh |
|---|---|---|---|---|---|
| ES | 3/CAM:3/TCB:0.25:any/SATR:1.5/R:3 | 358 | 1.16 | 0.83 | -0.72 |
| ES | 5/ROUND:100/ENG:0.25:any/SLV:0.5/R:3 | 199 | 1.03 | 1.12 | 1.81 |
| ES | 15/ON_BRK/ENG:0.25:any/SATR:1.5/R:3 | 209 | 0.95 | -2.59 | -0.76 |
| ES | 15/AVWAP_WEEK/ENG:0.25:any/SLV:0.5/R:1.5 | 415 | 0.90 | -1.71 | -1.01 |
| ES | 60/CAM:3/TCB:0.25:any/SATR:1.5/R:3 | 306 | 0.88 | -0.04 | -0.06 |
| ES | 5/CAM:3/RSI:2:30/SATR:1.5/R:3 | 268 | 0.86 | 0.19 | -1.65 |


ES by level family (stage-1 cells with >= 150 clean trades): 

| fam | size | median | max |
|---|---|---|---|
| Bands (Bollinger/Keltner) | 232 | -2.26 | 0.39 |
| Fibonacci | 216 | -2.71 | 0.44 |
| ICT (FVG/OB) | 228 | -2.48 | 0.34 |
| MA (EMA/SMA/HMA) | 1005 | -2.62 | 0.69 |
| Pivots (classic/Camarilla) | 190 | -0.73 | 1.16 |
| Prior-day / overnight extremes | 213 | -1.30 | 0.95 |
| Round numbers | 148 | -0.97 | 1.03 |
| Trend lines (Kijun/PSAR/Supertrend) | 218 | -2.25 | 0.81 |
| VWAP / anchored VWAP | 384 | -1.38 | 0.90 |


**RTY top clean cells (identical grid, report-only), with the single H1/H2 read**

| inst | cell | n_clean | clean_sh | H1_sh | H2_sh |
|---|---|---|---|---|---|
| RTY | 1/PD_OPP/ENG:0.25:any/SATR:1.5/R:3 | 229 | 1.08 | -2.28 | -1.13 |
| RTY | 5/ROUND:50/ENG:0.25:any/SLV:0.5/R:1.5 | 213 | 0.94 | -1.06 | 1.18 |
| RTY | 1/CAM:3/ENG:0.25:any/SLV:0.5/R:3 | 317 | 0.92 | 1.22 | 0.18 |
| RTY | 5/ROUND:50/PIN:50:0.25:any/SLV:0.5/R:3 | 425 | 0.89 | -1.33 | -2.55 |
| RTY | 5/CAM:3/RSI:2:30/SATR:1.5/R:3 | 247 | 0.87 | 1.56 | -1.37 |
| RTY | 3/ROUND:50/ENG:0.25:any/SLV:0.5/R:1.5 | 238 | 0.85 | -1.58 | -0.35 |


RTY by level family (stage-1 cells with >= 150 clean trades): 

| fam | size | median | max |
|---|---|---|---|
| Bands (Bollinger/Keltner) | 228 | -2.42 | -0.24 |
| Fibonacci | 216 | -2.80 | 0.40 |
| ICT (FVG/OB) | 228 | -2.08 | 0.58 |
| MA (EMA/SMA/HMA) | 1006 | -2.36 | 0.53 |
| Pivots (classic/Camarilla) | 166 | -1.14 | 0.92 |
| Prior-day / overnight extremes | 208 | -0.96 | 1.08 |
| Round numbers | 131 | -0.74 | 0.94 |
| Trend lines (Kijun/PSAR/Supertrend) | 214 | -2.07 | 0.45 |
| VWAP / anchored VWAP | 388 | -1.30 | 0.43 |



## 6. False-discovery accounting
- Cells: 4,775 unique NQ cells (stage 1 3,280 + stage 2 1,495) with clean-only selection; 12 finalists.
- Null worlds (random-level, 30 x 3,280 cells): best-of-search clean weekly Sharpe mean 1.97, p95 2.32, max 2.57; the real stage-1 best is 1.58 (real exceeds 3% of the null worlds). Cells above the finalist threshold per world: 29.9 (null) vs 11 (real).
- Gate-3 read of the top-12 distinct bases of each null world on H1/H2 (360 cells): clean uplift +0.25, H1 -0.13, H2 -0.27, mean standalone all-in Sharpe 0.71; **10 of 360 (2.8%) pass gate 3**. The real finalists: clean +0.29, H1 -0.03, H2 -0.16, standalone all-in 1.08; 0 of 12 pass gate 3; 33% have >= 2 of 3 spans at +0.10 vs 30% in null worlds. The real finalists are statistically indistinguishable from the best cells of a world where the level carries no information.
- Expected chance gate-3 passes for 12 finalists = 0.33 (observed 0); gate 3 is only the first of seven; the nulls, bootstrap, plateau, 2x slippage and replication gates were not run on the null-world cells (only gate 3 was), so the full-gate chance rate is bounded above by this gate-3 rate (about 0.3 false FOUNDs per study of this size before the remaining gates, which the real lead fails three of). Note the null-world rate is at the 20% share; allowing any of 10/20/30/50% roughly doubles-to-quadruples the gate-3 chance rate. Alt-month whole-search replication: odd-month-selected best cell b60|AVWAP_MONTH|TCB:0.25:any|TR_E50|SATR:1.5|R:3|ALL (sel Sharpe 2.14, odd uplift +0.37) reads -0.02 on even months (FAIL); even-selected best b15|ROUND:100|TCB:0.25:any|TR_PST|SATR:1.5|R:1.5|ALL (2.28, +0.38) reads -0.06 on odd months (FAIL). Of the top 25 cells selected on one half, 4 (odd->even) and 1 (even->odd) keep a positive read-half uplift of >= 50% of their selection-half uplift (about what luck gives); among cells with selection Sharpe >= 1 the mean read-half Sharpe is +0.14 (odd->even, 162 cells) and -0.15 (even->odd, 255 cells) against 1.28 in selection.

## 7. Checklist for the best cell (finalist 10) and the study
| gate | result |
|---|---|
| 1 pre-registered before any scored cell | PASS (PREREG_PULLBACK.md + Amendment 1, definitions only) |
| 2 clean-only selection, H1/H2 read once | PASS (FINALISTS_frozen.json before the read; family/trigger/bar representatives, ES/RTY screens and respect post columns are descriptive single reads) |
| 3 uplift >= +0.10 clean/H1/H2, worst week within share | **FAIL** at 20% (+0.26/+0.11/+0.08); passes only at 30% (+0.35/+0.11/+0.10); no other finalist passes at any share |
| 4 own nulls p95 (timing-destroyed, random-level) and bootstrap CI > 0 | PASS for this cell (not search-adjusted; search-adjusted it fails, section 6) |
| 5 plateau exact +/-25% and 2x slippage | **FAIL** (4/6 at 20% and at 30%; 2x slippage H1/H2 +0.09/+0.07 at 20%, +0.08/+0.08 at 30%) |
| 6 worst-decile correlation <= +0.30 | PASS (-0.55) |
| 7 NT8 spec and margin | spec written (section 4.1) |
| ERA flag | negative pre-2023 (reported, not gating) |
| replication (>= 2 of ES, RTY, H0, alt-month, newest weeks) | **FAIL** (0 of 3 of ES, RTY, H0; alt-month whole search fails) |
Library: 12 finalist books saved (outputs/library/PB_*), tagged NQ_INTRADAY (cannot share an account with ST/HM).

## 8. Honest limits
Levels are my mechanical definitions (FVG/OB simple; the ICT worker's definitions are a robustness check not yet used); bounce rate is a symmetric +/-1 ATR measure and is not a trade P&L; sub-minute order of events inside a 1-minute bar is conservative (stop first); entries are next-minute market orders (a resting limit at the level would fill better but needs trade-through assumptions, and the pair-side E5/(a) tests suggest limits do not help); X_REB re-simulation is approximate (90% exit-bar match); ES/RTY trend states use the NQ pair; 2013-2022 pair-state cells could not be run (ERA N/A for TR_P*). A null in this study means: no tested definition of these levels shows respect or an edge net of 1 tick/side costs in 2023-2026, not that no discretionary trader could find one.

DONE PULLBACK
