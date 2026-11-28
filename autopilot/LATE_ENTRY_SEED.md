# LATE ENTRY SEED (W-SUNDAY-MX)  pools of winners' holding times, from the engine data as used by the late50 / late75 rule

DEFINITIONS (exactly what the code does; code/th_dynexit/dx_build15.py late(), copy sun_joint_mix.py holds()/late_ev())
- Pool: for each book (stem + tag) the trades of THAT book in the LIVE MIX AS RUN (set TL3_SR_<S>_..., all 42 engine months, Nov 2025 absent), one pool per book (each book has its own winners; books are not mixed). NP-CONF = tag MF5 of TL3_DX_NP_CONF_fix_M (the live NY PM mix with CONF added). REPL2 pools = the stream whose events file is REPL2_* in the REPL2 `_M` set of that name (note: the late rule was never applied to REPL2 streams in the tests; these pools are only seeds).
- Winner: trade with gross > 0 (gross dollars from the engine trades.parquet BEFORE the 4.84/lot fee). Includes any exit type (target, policy take, time exit, stop that closed green).
- Holding time: exit_ns - entry_ns of the engine trade = exit FILL time minus entry FILL time, in seconds as a float (nanosecond clock / 1e9). Lists below are rounded to milliseconds (the tested code uses the full float).
- ORDER: NOT closing order. The code sorts the winners by ENTRY second (entry_ns // 10^9, the fill second; pandas sort_values, default quicksort, so ties inside the same second have an arbitrary but fixed order). Each book's second line gives the entry seconds so the live code can reload and sort identically. The tested decision at a signal ts uses the winners with entry second strictly before ts (index i = searchsorted(entry_seconds, ts, 'left') - 1, i.e. the first i+1 winners of this order), including winners still open at ts (their realised hold is known only afterwards: the small look-ahead). A live version that appends winners in closing order would differ from the tested one on under 0.6% of decisions (LATE_ENTRY_SPEC.md).
- Percentile method: pandas Series.expanding(min_periods=30).quantile(q) with q = 0.50 / 0.75, default interpolation = 'linear', which equals numpy.percentile(x, 100*q) with the default method='linear' (position (n-1)*q, linear interpolation between neighbours); checked equal to 1e-9 on every pool and for the check vectors below. Not nearest-rank. NaN (no halving) until 30 winners exist.
- Rule: late if (exit_ts - ts) < threshold, where ts = signal second, exit_ts = planned exit (bell). late50/late75 halve lots: max(1, lots // 2). The two quantiles are applied alone (late50 uses q = 0.50, late75 uses q = 0.75), not together.
- Pool end: the end of the engine data = Oct 2026 (last entry second per book is printed).

WHICH ROW THE LOWEST-DRAWDOWN CHOICE USES (SUNDAY_JOINT_MIXES.md, 42 months; NY PM 37)
| session | lowest max DD row | late row used |
|---|---|---|
| NY AM | drift removed + node | none (no late) |
| Asia | replacement Ma1 + vwap + late50 | late50 |
| NY PM | drift removed + late50 | late50 |
| London | drift at 1 lot + late75 | late75 |
Best-income rows: NY AM live + node (no late); Asia replacement + vwap (no late); NY PM replacement + znconf (no late); London live + late50 (late50).

POOL SUMMARY
| session | book | winners | p50 s | p75 s | last entry second |
|---|---|---|---|---|---|
| AS | AS-NR7 [AS MF1] | 931 | 10317.0 | 25198.0 | 1793337363 |
| AS | AS-RSI [AS MF2] | 334 | 5209.0 | 15268.5 | 1793238353 |
| AS | AS-VWAPBRK [AS MF3] | 1625 | 1398.4 | 4152.4 | 1793334892 |
| AS | AS MF4 (drift) [AS MF4] | 524 | 1167.6 | 3337.3 | 1793322425 |
| LO | LO-CRUDE [LO MF1] | 754 | 1820.5 | 5144.4 | 1793353927 |
| LO | LO MF2 (drift) [LO MF2] | 1572 | 2721.3 | 6803.9 | 1793360728 |
| LO | LO-ZB [LO MF3] | 1082 | 5601.8 | 15440.0 | 1793348434 |
| NY | NY-FIB [NY MF1] | 903 | 3215.4 | 6628.5 | 1793288158 |
| NY | NY-VALUE [NY MF2] | 1009 | 898.4 | 2128.1 | 1793199391 |
| NY | NY MF3 (drift) [NY MF3] | 527 | 3467.0 | 8597.0 | 1793367006 |
| NY | NY-NODE [NY MF4] | 2383 | 309.6 | 861.2 | 1793285788 |
| NY | NY-OFI [NY MF5] | 1364 | 1033.7 | 2368.3 | 1793374205 |
| NY | NY MF6 (drift) [NY MF6] | 2097 | 435.0 | 1197.3 | 1793288155 |
| NY | NY MF7 (drift) [NY MF7] | 554 | 1798.0 | 3888.9 | 1793288163 |
| NY | NY MF8 (drift) [NY MF8] | 627 | 618.5 | 1606.8 | 1793373192 |
| NY | NY MF9 (drift) [NY MF9] | 447 | 1085.2 | 2450.9 | 1793286603 |
| NP | NP MF1 (drift) [NP MF1] | 1958 | 761.7 | 1674.1 | 1793387883 |
| NP | NP-ZN [NP MF2] | 314 | 6639.9 | 11541.5 | 1793215029 |
| NP | NP-YM [NP MF3] | 735 | 1798.0 | 3787.0 | 1793386803 |
| NP | NP MF4 (drift) [NP MF4] | 890 | 2187.0 | 5030.2 | 1793382408 |
| NP | NP-CONF [NP MF5, set TL3_DX_NP_CONF_fix_M] | 499 | 4678.0 | 8098.0 | 1793289963 |
| AS | REPL2 Ma1 [AS MF4, set TL3_DX_AS_REPL2_Ma1_M] | 533 | 6948.0 | 15492.0 | 1793321171 |
| AS | REPL2 Ma2 [AS MF4, set TL3_DX_AS_REPL2_Ma2_M] | 493 | 21298.0 | 27984.0 | 1793225046 |
| NP | REPL2 Z1 [NP MF1, set TL3_DX_NP_REPL2_Z1_M] | 678 | 8880.0 | 13440.0 | 1793377261 |
| NP | REPL2 Z2 [NP MF1, set TL3_DX_NP_REPL2_Z2_M] | 653 | 9096.4 | 13440.0 | 1793377261 |
| NY | REPL2 Y2 [NY MF3, set TL3_DX_NY_REPL2_Y2_M] | 553 | 3524.3 | 7294.0 | 1793195657 |
| NY | REPL2 Y2 [NY MF6, set TL3_DX_NY_REPL2_Y2_M] | 532 | 3522.0 | 7362.5 | 1793194660 |
| NY | REPL2 Y4 [NY MF3, set TL3_DX_NY_REPL2_Y4_M] | 553 | 3524.3 | 7294.0 | 1793195657 |
| NY | REPL2 Y4 [NY MF6, set TL3_DX_NY_REPL2_Y4_M] | 532 | 3522.0 | 7362.5 | 1793194660 |

## CHECK VECTORS (verify the relay percentile against these)
### AS-VWAPBRK [AS MF3] check vector: first 40 winners (hold seconds, entry order)
15519.000000,19690.000000,9058.000000,3395.499005,22535.000000,1060.000000,19523.797500,11025.089220,4676.569048,5919.103067,4743.201916,21958.000000,20629.000000,21509.280043,8591.750201,6072.000000,11075.818769,9708.422093,20633.000000,24985.483941,2858.673294,6212.414169,19298.054297,18822.000000,3608.256889,2488.008851,8247.000000,13720.350876,23088.000000,22609.000000,8458.525254,26663.000000,8506.156967,13579.652188,7910.000000,6078.104162,5026.622979,15171.000000,270.565068,5626.170413

after 35 winners: p50 = 11025.089220, p75 = 20159.500000 (numpy linear on first 35)
after 36 winners: p50 = 10366.755657, p75 = 19924.750000 (numpy linear on first 36)
after 37 winners: p50 = 9708.422093, p75 = 19690.000000 (numpy linear on first 37)
after 38 winners: p50 = 10366.755657, p75 = 19648.449375 (numpy linear on first 38)
after 39 winners: p50 = 9708.422093, p75 = 19606.898750 (numpy linear on first 39)
after 40 winners: p50 = 9383.211046, p75 = 19565.348125 (numpy linear on first 40)

### NY-NODE [NY MF4] check vector: first 40 winners (hold seconds, entry order)
474.003980,5739.142798,3690.028141,1734.704156,515.863238,1331.145037,3038.187999,4101.007978,894.535331,1382.678659,245.284410,1759.490144,504.516874,6223.000000,329.503892,486.172596,598.811451,813.262015,5199.000000,4071.677116,3138.474447,1658.000000,1233.170312,4452.871172,657.098250,1407.505987,1220.993068,520.641252,140.486043,4836.246681,224.466747,3572.476245,971.000000,2409.929582,2181.352176,2707.168665,375.438463,343.834928,2307.036337,3446.000000

after 35 winners: p50 = 1382.678659, p75 = 3355.475346 (numpy linear on first 35)
after 36 winners: p50 = 1395.092323, p75 = 3246.974896 (numpy linear on first 36)
after 37 winners: p50 = 1382.678659, p75 = 3138.474447 (numpy linear on first 37)
after 38 winners: p50 = 1356.911848, p75 = 3113.402835 (numpy linear on first 38)
after 39 winners: p50 = 1382.678659, p75 = 3088.331223 (numpy linear on first 39)
after 40 winners: p50 = 1395.092323, p75 = 3215.355835 (numpy linear on first 40)

### NP-ZN [NP MF2] check vector: first 40 winners (hold seconds, entry order)
6349.000000,4265.000000,2019.000000,530.000000,13092.000000,10446.000000,13839.000000,2912.000000,10831.000000,6089.000000,4842.000000,12668.000000,5472.000000,13182.669997,148.000000,12504.000000,578.000000,9634.335704,11036.000000,13532.444869,10902.000000,4691.000000,14193.000000,9523.955822,1212.023990,4582.001098,6253.000000,11317.000000,11651.000000,11430.000000,9969.961664,8224.277102,453.000000,1830.000000,11697.194871,6066.001884,4025.000000,1564.000000,10909.000000,10787.140064

after 35 winners: p50 = 9523.955822, p75 = 11540.500000 (numpy linear on first 35)
after 36 winners: p50 = 8874.116462, p75 = 11485.250000 (numpy linear on first 36)
after 37 winners: p50 = 8224.277102, p75 = 11430.000000 (numpy linear on first 37)
after 38 winners: p50 = 7286.638551, p75 = 11401.750000 (numpy linear on first 38)
after 39 winners: p50 = 8224.277102, p75 = 11373.500000 (numpy linear on first 39)
after 40 winners: p50 = 8874.116462, p75 = 11345.250000 (numpy linear on first 40)

The full pools are split by session: LATE_ENTRY_SEED_AS.md, LATE_ENTRY_SEED_LO.md, LATE_ENTRY_SEED_NY.md, LATE_ENTRY_SEED_NP.md (same directory).
