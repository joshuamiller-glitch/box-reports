# DS3 T-PULLBACK sub-minute (D3PB4): pullback and trigger on 15-s/30-s, tick, range, volume and Renko bars

Generated 2026-10-27T10:51Z. Research only; no execution-server/chart/live change. Owner scope: every NON-MINUTE pullback/trigger bar (the 1/2/3/5-min bars belong to D3PB/D3PB2/D3PB3).

## 1. Verdict

177 cells scored (150 first-pass in 5 preregs of 30 + 27 widening), ledger +177. MAPPED screen: 13 PASS, 15 CANDIDATE, 149 DEAD (first-pass only: 7 PASS, 10 CANDIDATE of 150; widening: 6 PASS, 5 CANDIDATE of 27). DIRECT L2 replay of the 21 first-pass + 11 widening non-DEAD/top-10 cells is RUNNING (orchestrators pb4_direct.py / pb4w_direct.py, ~15 h at the governed pace); every verdict below is MAPPED unless stated, so no cell here is a PASS for DS3 yet.

**Headline.** (1) Moving the pullback/trigger to faster bars does NOT improve the 1-min cell: over the 177 cells whose identical regime/level/trigger could be run on 1-min bars by the same engine, the sub-minute cell earns 1,723 $/wk less on WF (SE 369; sub-minute better in 38% of cells); the paired per-trade difference vs the 1-min cell has median +0.1 pt (MDE ~2.2 pt) so the timing gain is nil within power. (2) Transaction cost is the killer exactly as in T-K: median gross edge 167 $/trade, median cost 87 $/trade (10 lots), median WF $/wk 2,245 -> 1,124 at 1.5x cost -> -275 at 2x cost; 47% of cells keep a positive 2x-cost WF. (3) The 13 mapped PASS are mostly one cluster (11 of 13): ST-regime (3-15 min) + EMA20(1-min) pullback + T1/T2 trigger on volume-500/1000, 15-s/30-s and renko bars; the 3x3 widening around them keeps 11 of 27 neighbours PASS/CANDIDATE, but the same 1-min cell family is itself positive (mean 1-min base WF 4,964 $/wk), i.e. the cluster is the D3PB trend/EMA20-pullback beta, not a sub-minute timing effect. (4) Latency: +1 s entry delay leaves median WF at 2,221 (vs 2,245), +2 s at 1,979: NOT latency-fragile at the level of this mean (sign flips in 18 of 177 cells).

Power: every predicted effect (<= 0 vs the 1-min cell) is below the MDE (standalone weekly MDE ~$8-13k/wk on 143 WF weeks, ~$11-18k on PRE; per-trade ~3 pt; paired vs ST ~3-14 pt, vs the 1-min cell column 'MDE vs base'). Verdicts are screens: sign agreement across PRE/HOLD/2023-span, timing-destroyed placebo (30 draws) and cost stress; no cell is established by power.

## 2. Method (as preregistered; sha256 in autopilot/DECISIONS.md)

Preregs: l2vast/ds3/prereg/TP4_TB4A_time, TB4B_tick, TB4C_range, TB4D_volume, TB4E_renko (30 cells each, stratified by bar x regime bar; regime types ST(10,3.0)/EMA200/HMA55/PSD on 3/5/10/15/30/60-min bars; levels VWAP/EMA20-1m/EMA20-5m/38-50-62% of the 60-min range/flip level; triggers T1/T2/T3), TP4_TB4W1 (27 widening cells). Bars: time bars 15 s/30 s and tick 250/2000, range 60 (15 pt), volume 2000 built by this track from the tick tape (code pb4_bars.py, D3BAR's NT8-convention engine e1_bars.py; D3BAR already had tick 500/1000, range 20/40/80 (5/10/20 pt), volume 500/1000, Renko 20/40 ticks (5/10 pt) which are reused: D3BAR should add tick_250, tick_2000, range_60, volume_2000, time_15s, time_30s to its catalogue, files in l2vast/ds3/out/bars/). Signal on the X-bar close (OnBarClose), entry at the first second at/after the close at the close-tick price (time bars: last print of the bucket), on the 1-s path via e1_sim (stop checked before target within a second), DS2 bracket 60 pt / 1.0R, flat 16:55, signals blocked 15:00-17:59, one trade at a time, 10 lots, mapped corrected-P9 (year x exit type; measured on 1-min market entries, hence DIRECT replay for finalists), exact per-book lock engine (day -2R/+5R, give-back 2R keep 50%, week floor 12R, R=$12,000, $4.84 RT). Windows: WF-PRE 2024-02..2025-06; holdout 2025-07+ (ONE logged look DS3_TP4 covering all declared cells, text l2vast/ds3/out/pb4/PB4_PREHOLDOUT.md); second holdout 2023-04..2024-01. Verdict: tpw>=3, PRE>0, WF week-block CI>0, HOLD>0, SPAN2>0, placebo rank PRE>=0.95, 2x-cost WF>0; PASS = all, CANDIDATE = all but one. Caveats: 1-min reference series (VWAP, EMA20, swing range) come from the library 1-min file with volume from the 1-s tape (VWAP uses typical price x minute volume); only 2 days of warm-up before 2023-02-10, so 30/60-min regime states are partly cold in the 2023 span; the 'base 1-min cell' is the same rule on 1-min bars from THIS engine, not D3PB's own base cells (whose definitions differ in detail; D3PB's 1-min results are in DS3_TPULLBACK.md).

## 3. By bar family (mapped)

| family | cells | PRE>0 | HOLD>0 | SPAN2>0 | mean WF $/wk | mean same-rule 1-min WF | mean tr/wk | median cost $/trade | PASS | CAND |
|--|--|--|--|--|--|--|--|--|--|--|
| WIDEN | 27 | 0.78 | 0.89 | 0.59 | 7,768 | 10,844 | 27.6 | 28 | 6 | 5 |
| range | 30 | 0.27 | 0.73 | 0.20 | 1,505 | 4,114 | 22.3 | 90 | 0 | 3 |
| renko | 30 | 0.60 | 0.57 | 0.47 | 2,514 | 4,230 | 22.8 | 77 | 1 | 3 |
| tick | 30 | 0.60 | 0.57 | 0.33 | 2,101 | 4,293 | 21.6 | 120 | 1 | 1 |
| time | 30 | 0.50 | 0.90 | 0.30 | 3,753 | 3,655 | 24.4 | 90 | 2 | 2 |
| volume | 30 | 0.53 | 0.70 | 0.47 | 2,254 | 3,236 | 21.2 | 115 | 3 | 1 |

No cell is LOW-FREQUENCY (< 3 trades/wk): minimum trades/wk = 6.1, median 25.3 (sub-minute bars raise trade counts to 20-30/wk; the one-trade-at-a-time bracket caps them).

## 4. PASS / CANDIDATE cells and top 10

Columns: WF/HOLD/SPAN2/PRE = weekly mean $ at 10 lots (MAPPED); dir = DIRECT verdict (pending = replay running); quiet/wide = WF $/wk from predicted-quiet (P>=0.6) / predicted-wide sessions (post-hoc trade split); L/S = long / short WF $/wk (separate one-trade-at-a-time runs); d1/d2 = WF with +1 s / +2 s entry delay; x1.5/x2 = WF at 1.5x / 2x cost; gross/cost = $ per trade at 10 lots; vsST = paired pts/trade vs ST10 [MDE]; vs1m = paired pts/trade vs the same rule on 1-min bars [MDE]; NT8 bar = exact BarsPeriod.

| cell | mapped | dir | top10 | NT8 bar (OnBarClose) | regime | level/trig | tr/wk | PRE | HOLD | SPAN2 | WF | WF CI lo | quiet/wide | L / S | d1 / d2 | x1.5 / x2 | gross / cost $/tr | vsST [MDE] | vs1m [MDE] | placebo | failed |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| TB4A_time_00_time_15s_EMA20010_E20_1_T1 | CANDIDATE | pending |  | BarsPeriodType.Second, Value 15 | EMA20010 | E20_1/T1 | 30.1 | 6,299 | 16,622 | 6,448 | 11,324 | 458 | 1,797 / 8,019 | 8,596 / 4,690 | 11,022 / 11,009 | 8,950 / 6,108 | 449 / 110 | 6.9 [3.3] | 2.3 [1.0] | 0.9 | plc>=.95 |
| TB4C_range_21_range_80_HMA555_E20_1_T2 | CANDIDATE | pending |  | BarsPeriodType.Range, Value 80 ticks (20 pt) | HMA555 | E20_1/T2 | 25.4 | 9,433 | 13,916 | -7,238 | 11,662 | 2,960 | 526 / 8,211 | 3,915 / 3,131 | 9,891 / 7,814 | 9,784 / 8,295 | 294 / -23 | -5.0 [4.1] | -4.4 [3.1] | 1.0 | SPAN2>0 |
| TB4A_time_11_time_15s_ST5_SW50_T3 | CANDIDATE | pending |  | BarsPeriodType.Second, Value 15 | ST5 | SW50/T3 | 29.6 | 7,641 | 13,635 | -3,161 | 10,587 | 2,335 | 1,043 / 6,445 | 1,829 / 7,022 | 11,767 / 14,106 | 7,672 / 6,608 | 326 / 35 | 9.1 [3.8] | -4.5 [1.4] | 1.0 | SPAN2>0 |
| TB4W_01_time_15s_ST5_SW38_T2_ntime03 | CANDIDATE | pending |  | BarsPeriodType.Second, Value 15 | ST5 | SW38/T2 | 28.3 | 7,670 | 13,421 | -7,062 | 10,498 | 1,467 | -486 / 8,833 | 4,148 / 5,185 | 10,662 / 9,141 | 7,334 / 4,748 | 233 / 0 | 1.6 [3.0] | 6.1 [1.7] | 1.0 | SPAN2>0 |
| TB4W_03_time_15s_ST3_E20_1_T2_ntime14 | CANDIDATE | pending |  | BarsPeriodType.Second, Value 15 | ST3 | E20_1/T2 | 30.6 | 15,661 | 13,189 | -46 | 14,578 | 5,035 | 4,608 / 6,799 | 3,011 / 3,384 | 12,560 / 12,466 | 12,546 / 11,297 | 303 / -67 | 4.6 [2.6] | 5.2 [1.6] | 1.0 | SPAN2>0 |
| TB4W_02_time_30s_ST5_SW38_T2_ntime03 | CANDIDATE | pending |  | BarsPeriodType.Second, Value 30 | ST5 | SW38/T2 | 28.3 | 12,310 | 12,678 | -7,109 | 12,574 | 4,377 | 616 / 9,348 | 1,106 / 6,193 | 12,896 / 12,566 | 10,512 / 8,094 | 250 / -62 | -2.0 [3.1] | 3.1 [1.3] | 1.0 | SPAN2>0 |
| TB4E_renko_14_renko_20_HMA555_E20_1_T2 | CANDIDATE | pending |  | BarsPeriodType.Renko, brick 20 ticks (5 pt) | HMA555 | E20_1/T2 | 30.3 | 17,325 | 11,090 | -3,242 | 14,438 | 4,884 | 3,938 / 9,943 | 2,113 / 1,358 | 12,677 / 13,465 | 12,620 / 9,108 | 322 / -37 | 4.2 [3.0] | 7.0 [2.0] | 1.0 | SPAN2>0 |
| TB4W_07_tick_250_ST5_SW62_T2_ntick26 | CANDIDATE | pending |  | BarsPeriodType.Tick, Value 250 | ST5 | SW62/T2 | 24.7 | 7,289 | 9,688 | 3,773 | 8,498 | 312 | 1,164 / 5,543 | 3,949 / 6,084 | 8,523 / 9,757 | 6,496 / 4,916 | 327 / 4 | 1.0 [4.2] | 1.5 [2.1] | 0.9 | plc>=.95 |
| TB4E_renko_07_renko_20_HMA555_E20_1_T1 | CANDIDATE | pending |  | BarsPeriodType.Renko, brick 20 ticks (5 pt) | HMA555 | E20_1/T1 | 30.5 | 12,233 | 9,241 | -10,403 | 10,875 | 1,148 | 2,970 / 6,244 | -428 / 5,811 | 9,108 / 10,213 | 10,341 / 7,708 | 200 / 35 | 7.1 [3.0] | 2.1 [1.6] | 1.0 | SPAN2>0 |
| TB4C_range_00_range_40_ST3_E20_1_T1 | CANDIDATE | pending |  | BarsPeriodType.Range, Value 40 ticks (10 pt) | ST3 | E20_1/T1 | 31.1 | 15,732 | 8,057 | -598 | 12,139 | 2,348 | 4,953 / 3,429 | 3,467 / 5,847 | 13,049 / 12,882 | 12,101 / 9,757 | 240 / -37 | 6.8 [3.1] | 0.5 [1.3] | 1.0 | SPAN2>0 |
| TB4B_tick_10_tick_250_ST60_SW38_T3 | CANDIDATE | pending |  | BarsPeriodType.Tick, Value 250 | ST60 | SW38/T3 | 28.0 | 9,920 | 7,244 | 2,281 | 8,698 | -576 | 1,538 / 5,804 | 5,561 / 2,388 | 7,324 / 6,747 | 6,979 / 5,394 | 372 / 73 | 9.7 [5.6] | -1.5 [2.4] | 1.0 | WF_CI>0 |
| TB4W_09_tick_500_ST5_SW62_T2_ntick26 | CANDIDATE | pending |  | BarsPeriodType.Tick, Value 500 | ST5 | SW62/T2 | 22.5 | 10,087 | 7,223 | -5,591 | 8,776 | 1,174 | 296 / 7,806 | 1,721 / 4,367 | 7,513 / 8,250 | 6,610 / 4,602 | 328 / 88 | -3.1 [5.7] | -2.5 [2.8] | 1.0 | SPAN2>0 |
| TB4C_range_24_range_80_ST5_SW38_T1 | CANDIDATE | pending |  | BarsPeriodType.Range, Value 80 ticks (20 pt) | ST5 | SW38/T1 | 28.0 | 12,922 | 6,863 | -500 | 10,089 | 1,165 | -2,058 / 9,863 | 2,959 / 1,479 | 10,617 / 8,454 | 9,060 / 8,188 | 267 / -22 | -0.1 [3.4] | -1.6 [2.0] | 1.0 | SPAN2>0 |
| TB4D_volume_11_volume_500_ST60_SW50_T3 | CANDIDATE | pending |  | BarsPeriodType.Volume, Value 500 | ST60 | SW50/T3 | 26.3 | 10,212 | 3,075 | 8,621 | 6,840 | -2,494 | 962 / 5,209 | 3,846 / 4,117 | 5,730 / 3,421 | 5,505 / 4,097 | 336 / 19 | 15.7 [6.1] | 0.4 [2.4] | 1.0 | WF_CI>0 |
| TB4E_renko_01_renko_20_EMA2003_VWAP_T1 | CANDIDATE | pending |  | BarsPeriodType.Renko, brick 20 ticks (5 pt) | EMA2003 | VWAP/T1 | 18.1 | 4,703 | 3,046 | 2,486 | 3,937 | -2,736 | 2,937 / 2,597 | 2,777 / 2,918 | 3,017 / 4,019 | 2,739 / 1,824 | 352 / 111 | 13.6 [6.3] | 4.0 [2.0] | 1.0 | WF_CI>0 |
| TB4A_time_21_time_30s_ST10_E20_1_T2 | DEAD | pending | Y | BarsPeriodType.Second, Value 30 | ST10 | E20_1/T2 | 29.5 | 4,869 | 18,579 | -1,351 | 11,518 | 1,898 | -187 / 9,952 | 5,417 / 6,077 | 9,799 / 11,640 | 9,173 / 8,388 | 370 / 95 | 0.9 [2.7] | 3.5 [1.4] | 0.9 | SPAN2>0,plc>=.95 |
| TB4W_18_volume_500_ST10_E20_1_T2_nvolume21 | DEAD | pending | Y | BarsPeriodType.Volume, Value 500 | ST10 | E20_1/T2 | 29.1 | 1,647 | 17,299 | 1,771 | 9,211 | -1,518 | -2,000 / 8,809 | 3,847 / 3,440 | 8,547 / 10,403 | 7,695 / 5,976 | 341 / 95 | -4.6 [3.4] | -0.9 [2.5] | 0.8 | WF_CI>0,plc>=.95 |
| TB4B_tick_18_tick_250_ST5_SW50_T1 | DEAD | pending | Y | BarsPeriodType.Tick, Value 250 | ST5 | SW50/T1 | 28.2 | 4,676 | 17,069 | -319 | 10,688 | 2,623 | -1,366 / 8,204 | 4,916 / 6,431 | 11,262 / 11,763 | 8,799 / 6,575 | 339 / 2 | 4.7 [3.3] | 0.0 [1.5] | 0.9 | SPAN2>0,plc>=.95 |
| TB4B_tick_11_tick_2000_ST10_SW50_T3 | DEAD | pending | Y | BarsPeriodType.Tick, Value 2000 | ST10 | SW50/T3 | 18.8 | 1,737 | 11,644 | -12,954 | 6,529 | -1,094 | -502 / 6,782 | 4,419 / 472 | 7,390 / 5,200 | 5,460 / 4,304 | 322 / 222 | 23.1 [7.3] | 10.6 [3.8] | 0.7 | WF_CI>0,SPAN2>0,plc>=.95 |
| TB4D_volume_00_volume_1000_ST15_E20_1_T1 | PASS | pending | Y | BarsPeriodType.Volume, Value 1000 | ST15 | E20_1/T1 | 29.9 | 13,780 | 22,621 | 12,406 | 18,143 | 8,395 | 1,452 / 13,873 | 5,651 / 11,414 | 15,939 / 15,505 | 15,105 / 12,292 | 434 / -139 | 1.8 [3.3] | -2.1 [2.1] | 1.0 |  |
| TB4A_time_14_time_30s_ST5_E20_1_T2 | PASS | pending | Y | BarsPeriodType.Second, Value 30 | ST5 | E20_1/T2 | 30.4 | 12,490 | 20,405 | 149 | 16,396 | 8,183 | 4,728 / 7,487 | 3,009 / 8,555 | 15,432 / 15,767 | 14,749 / 13,308 | 365 / -75 | 2.0 [2.5] | 3.9 [1.4] | 1.0 |  |
| TB4D_volume_07_volume_500_ST15_E20_1_T1 | PASS | pending | Y | BarsPeriodType.Volume, Value 500 | ST15 | E20_1/T1 | 31.0 | 12,616 | 18,702 | 6,704 | 15,641 | 5,702 | 2,127 / 11,287 | 5,440 / 7,899 | 14,451 / 14,457 | 14,336 / 12,200 | 428 / 10 | 2.7 [3.0] | -1.4 [1.7] | 1.0 |  |
| TB4W_06_time_30s_ST3_E20_1_T2_ntime14 | PASS | pending | Y | BarsPeriodType.Second, Value 30 | ST3 | E20_1/T2 | 30.8 | 16,828 | 18,295 | 612 | 17,654 | 8,309 | 6,582 / 7,109 | 7,489 / 4,342 | 16,419 / 15,489 | 17,291 / 15,997 | 415 / -57 | 2.0 [2.4] | 3.6 [1.4] | 1.0 |  |
| TB4W_04_time_15s_ST5_E20_1_T2_ntime14 | PASS | pending | Y | BarsPeriodType.Second, Value 15 | ST5 | E20_1/T2 | 30.7 | 14,988 | 18,175 | 2,048 | 16,630 | 7,917 | 2,001 / 11,877 | 3,995 / 8,763 | 15,622 / 14,677 | 13,323 / 12,112 | 330 / -120 | 4.4 [2.5] | 5.2 [1.7] | 1.0 |  |
| TB4W_12_volume_1000_ST10_E20_1_T1_nvolume00 | PASS | pending | Y | BarsPeriodType.Volume, Value 1000 | ST10 | E20_1/T1 | 29.9 | 11,689 | 17,776 | 10,500 | 14,708 | 3,952 | -897 / 13,399 | 4,827 / 13,167 | 13,299 / 13,384 | 11,874 / 9,697 | 452 / -27 | -0.2 [3.3] | -2.8 [2.2] | 1.0 |  |
| TB4W_10_volume_500_ST10_E20_1_T1_nvolume00 | PASS | pending |  | BarsPeriodType.Volume, Value 500 | ST10 | E20_1/T1 | 30.6 | 16,246 | 17,381 | 2,231 | 16,907 | 6,845 | 1,269 / 13,065 | 8,852 / 9,964 | 16,898 / 15,681 | 14,911 / 12,197 | 408 / -23 | 2.8 [2.9] | -0.5 [1.6] | 1.0 |  |
| TB4W_05_time_15s_ST10_E20_1_T2_ntime14 | PASS | pending |  | BarsPeriodType.Second, Value 15 | ST10 | E20_1/T2 | 30.2 | 8,432 | 17,349 | 846 | 12,793 | 1,314 | 1,091 / 10,550 | 2,974 / 7,966 | 12,154 / 10,520 | 9,805 / 9,122 | 331 / 10 | 3.8 [2.8] | 6.0 [1.7] | 1.0 |  |
| TB4E_renko_28_renko_20_ST15_E20_1_T3 | PASS | pending |  | BarsPeriodType.Renko, brick 20 ticks (5 pt) | ST15 | E20_1/T3 | 30.4 | 11,263 | 14,502 | 6,336 | 12,905 | 2,352 | 5,281 / 5,154 | 5,972 / 2,052 | 9,611 / 7,913 | 10,708 / 7,300 | 349 / -54 | 8.6 [4.5] | -0.4 [2.1] | 1.0 |  |
| TB4D_volume_21_volume_500_ST5_E20_1_T2 | PASS | pending |  | BarsPeriodType.Volume, Value 500 | ST5 | E20_1/T2 | 29.0 | 13,832 | 12,840 | 4,182 | 13,450 | 3,809 | -714 / 11,139 | 5,140 / 2,620 | 10,982 / 12,376 | 10,934 / 8,928 | 302 / -92 | -3.6 [3.4] | -1.4 [2.4] | 1.0 |  |
| TB4W_19_volume_1000_ST3_E20_1_T2_nvolume21 | PASS | pending |  | BarsPeriodType.Volume, Value 1000 | ST3 | E20_1/T2 | 27.0 | 7,653 | 10,490 | 2,992 | 9,075 | 51 | -1,719 / 8,588 | 3,037 / 804 | 7,674 / 7,646 | 7,757 / 7,109 | 287 / -9 | -4.3 [4.1] | -2.6 [3.4] | 1.0 |  |
| TB4A_time_03_time_30s_ST3_SW38_T2 | PASS | pending |  | BarsPeriodType.Second, Value 30 | ST3 | SW38/T2 | 28.3 | 15,288 | 4,774 | 2,661 | 10,322 | 1,025 | 1,922 / 4,947 | 4,055 / 271 | 10,993 / 9,674 | 8,639 / 7,163 | 251 / -82 | -0.1 [3.2] | 3.9 [1.3] | 1.0 |  |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | PASS | pending |  | BarsPeriodType.Tick, Value 250 | ST3 | SW62/T2 | 23.0 | 14,893 | 4,469 | 3,058 | 9,967 | 3,091 | 1,920 / 5,872 | 2,138 / 2,984 | 8,772 / 7,015 | 7,891 / 6,567 | 392 / 30 | 3.6 [4.5] | 0.6 [2.1] | 1.0 |  |

Executability: all cells are NT8-native bar types evaluated OnBarClose (see the NT8 bar column); the 1-min regime/level references are built in the strategy from AddDataSeries(Minute 1/3/5/10/15/30/60). Sim-leader spec must name: primary series = the NT8 bar type in the table; secondary series = regime minute bar; orders sent on the close tick of the primary bar (market, then DS2 bracket). Range/Renko/Volume bar conventions were implemented by D3BAR from the NT8 documentation; D3X identity test against a real NT8 export is REQUIRED before any PASS enters DS3 and has not been run. exec_status: DELIVERABLE-PENDING-IDENTITY.

## 5. DIRECT L2 basis

PENDING: pb4_direct.py (first-pass, 21 cells, 138k unique trades) and pb4w_direct.py (widening, 11 cells, 64k trades) orchestrators are running through corepool/the replay governor (45 months each). Finish with: `PB4SUF= python3 pb4_final.py; PB4SUF=w python3 pb4_final.py` (each from l2vast/ds3/code/pb4, via corepool 1 slot), then `python3 pb4_post.py` / `PB4SUF=w python3 pb4_post.py` (equal-risk + DS3 marginal Sharpe + SERIES files for D3L), then `python3 pb4_report.py`. The script regenerates this report and the rows file.

## 6. Best-of-N and multiplicity

N = 177 cells in this track (150 first-pass + 27 widening; ledger +177). Placebo rank >= 0.95 on PRE: 37 of 96 cells with a computed placebo (PRE>0 only); chance level ~5%. Cells with PRE>0: 54%, HOLD>0: 72%, SPAN2>0: 39%: the holdout and PRE are dominated by the 2024-26 trend/bracket beta (the 1-min base cells are positive in the same proportion), while the 2023 span is the discriminating window (as in T-ENTRY). With 13 PASS in a stratified draw of 150 where only 13 clusters in one region, the best-of-N reading is: the region 'ST regime 3-15 min x EMA20-1m pullback x T1/T2' is positive on bars from 15 s to volume-1000, but (see headline) it is no better than on 1-min bars. DSR/n_trials not computed (screen); the full-ledger trial count (~35k+) puts any single cell at CONFIRMED-tier near 0.

## 7. Cost per trade vs edge per trade

| grp    |   gross_pt |   cost_pt |   net_pt |
|:-------|-----------:|----------:|---------:|
| WIDEN  |        287 |        28 |      249 |
| range  |         84 |        90 |      -20 |
| renko  |        120 |        77 |       76 |
| tick   |        169 |       120 |       79 |
| time   |        187 |        90 |      100 |
| volume |        153 |       115 |        2 |

(median $ per trade at 10 lots; cost = gross raw bracket P&L minus mapped net after execution and commission; WF+HOLD sample.) Sub-minute does not reduce cost per trade (same market entry and bracket), and raises trades per week, so total cost per week is similar to the 1-min cells while the edge per trade is lower.

## 8. Holdout and looks

One logged holdout look for the track (DS3_TP4; pre-holdout text l2vast/ds3/out/pb4/PB4_PREHOLDOUT.md) covering all 150 first-pass cells and, as a pre-declared widening, the 27 neighbours (disclosed). Add-book (DS3 marginal Sharpe) looks: none yet (direct series pending). The second holdout 2023-04..2024-01 was read in the same pass.

## 9. Files

Code l2vast/ds3/code/pb4/ (pb4_sig.py signal engine, pb4_cells.py, pb4_widen.py, pb4_run.py, pb4_collect.py, pb4_dsel*.py, pb4_direct.py, pb4w_direct.py, pb4_final.py, pb4_post.py, pb4_report.py); results l2vast/ds3/out/pb4/ (TB4*.json, *_daily.parquet, *_trades.parquet, table.csv); rows l2vast/ds3/rows/DS3_TPULLBACK4.json; progress l2vast/ds3/out/TPULLBACK4_PROGRESS.md.
