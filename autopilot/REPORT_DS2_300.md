# REPORT DS2-300 (trackDS300)

Benchmark = corrected P9 14/14 (WF 12/3/3 OOS 2024-02..: weekly mean 24,978, SD 104,547, maxDD 401,641, worst -137,081, Sharpe 1.72, 35.9 trades/wk; L8W 34,209/109,428/267,133; IS 13,654). Pre-registration: l2vast/PREREG_DS2_300.md (+ AMEND-1..3). Fees $4.84/contract RT. Dollars in $k unless noted.

## 0. Verdict

Scored cells 419 across 13 blocks; F_P = 3,375 -> 3561 (+184 families frozen, +I10, +B12x). Gate a (WF mean AND maxDD): 71 cells; a+b: 27; a+b+c: 0; a-d: 0. **FOUND / gate a-d passers: 0.** Nothing is promoted to a shadow; no frozen leads JSON and no forward shadow script issued (section 4).

Item map (details and every DUP reference in PREREG_DS2_300.md section 3): CONTROL 1, DIAG 1, DUP 74, METHOD 20, NEW 182, NOTRUN 18, REPORT 3, SKIP 1.

## 0b. Per-block findings (verbatim from DECISIONS.md, one line per block)

- 2026-10-22T21:45:16Z trackDS300 BLOCK F (locks/risk, 38 cells, lockeng 1-s exact engine + P9 fixed table): 4 gate-a passers (F7 week-trail 10R, F16 Friday arm1.5/cap6, F19 slip-lock x2), 2 also pass L8W; none passes gate c (placebo-lock null rank on WF mean <=0.60; best placebo ranks F2 STonly 0.90, F10 0.93); F14 two-strikes cuts maxDD -104k (WF) at -8k/wk mean (fails gate a). Nothing to shadow.

- 2026-10-22T21:45:16Z trackDS300 BLOCK E (sizing, 41 cells): 15 gate-a / 7 gate-a+b (E5 ES15 agree, E6 stops->8, E11 ST14-HM8/HM10, ST10-HM10, E17 cap30k); none passes gate c (max rank pairs: E5 ES5m mean .98/dd .87; E7 wr .75/.99; E13 .81/.98); E11 static per-book grid null degenerate (constant per book) -> best-of-16 only; WF-chosen book lots (E11) -4.9k/wk, fails.

- 2026-10-22T21:45:16Z trackDS300 BLOCK C (bracket geometry, 68 regenerated cells, mapped P9): 5 gate-a, 1 a+b (C13 ST60-HM40); constant-parameter cells have no timing null (degenerate) -> not eligible for gate c, family-wise test only; plateau confirmed (benchmark 60/60 and per-session 60/60 reproduce exactly). No direct-replay candidate cleared.

- 2026-10-22T21:45:16Z trackDS300 BLOCK B (entry triggers, 22 cells + B12 pending the 1-s tables): 4 gate-a/a+b (B13 prev-closed<3/5min, B16 expanding>1.0, B14 limit-at-flip-close mapped optimistic); none passes gate c (B13 dd rank .99 but mean rank .58).

- 2026-10-22T21:53:00Z trackDS300 BLOCK G (time structure, 16 cells): 4 gate-a (G3 skip 09:30-11:30, G3 skip 14-15, G4 lunch, G9x after-14:00) but 0 pass L8W; no null rank >=0.95 on both mean and maxDD (G15 52w mean rank .99 / dd .39). G7 flatten-16:00 neutral (+0.7k, maxDD +39k).

- 2026-10-22T21:53:00Z trackDS300 BLOCK H (regime, 37 cells): 6 gate-a / 3 a+b (H16 zigzag60 size8_hi, H19 volfrac size8_hi, H20 printed-sec size8_hi); all three are 'size 8 in the top tercile' cells whose gain comes mostly from the S113 credit + lower exposure; best null ranks H16 date .87/.92, feat .81/.99 -> gate c fails; gate d fails (bootstrap lower bound <0).

- 2026-10-22T21:53:00Z trackDS300 BLOCK I (cross-asset, 35 cells): 10 gate-a / 3 a+b (I4 ZN rel- s8, I9 BTC-Asia s8, I19 gap-divergence NY perm); best null ranks I3 RTY/NQ s8 .98/.81 (date), I4 ZN rel- .90/.93; none passes gate c.

- 2026-10-22T21:53:00Z trackDS300 BLOCK J (calendar, 9 cells): 1 gate-a (J16 quarter-end size8 +1.2k/-20k), 0 a+b; null ranks <=.80; J2/J8/J14/J18 inert or negative; J20 month table in out/J20_month_table.csv.

- 2026-10-22T22:00:48Z trackDS300 BLOCK A (signal construction, 35 cells: 33 regenerated + 2 Donchian sleeves x3 weights): gate-a passers A11 18:00-anchor (+1.0k, fails L8W, boot lo -11k) and A17 flip-outside-prior-range (+0.1k, L8W -3k); no variant beats on mean AND maxDD in both windows. Best raw WF means (A12 swing anchor 33.1k, A6 chandelier 30.7k, A15 5-min EMA 29.3k) all raise maxDD by +50..+230k. A8 Donchian 20/55 sleeves add mean (+3.3k/+8.9k at w0.5) but also +57k/+42k maxDD, null rank dd .69/.58 -> no. NOTE: event-shift null for regenerated signal variants is weak (shifted entries are random-timing trades; rank 1.0 for A11/A17 is not evidence) - gate c cannot be passed by A cells; b/d fail anyway.

- 2026-10-22T22:01:59Z trackDS300 BLOCK D (information exits, 25 regenerated cells, mapped P9 via _TimeBlock deltas): 5 gate-a, 3 a+b: D9 exit 15 min before releases (+1.1k/-38k; L8W +1.6k/-13k), D15 RV15 x3 (+3.8k/-51k; L8W +6.4k/-17k), D16 +60min stall+5-min trend against (+2.2k/-35k; L8W +4.2k/-89k); all three fail gate d (bootstrap lower bound <0) and have NO valid timing null (entry-relative rules; null not defined) so cannot pass gate c; they are direct-replay candidates after V6 (mapping only so far). Array-type exits (ES, 5/15-min ST, volume spike, VWAP, YM/RTY, shocks) all lose (maxDD +0.3..+4M).

- 2026-10-22T22:04:33Z trackDS300 BLOCK M (portfolio, 12 scored rows: sleeves M2/M3/M4 at w0.25/0.5/1.0, M8, M13, M14, M20; M15 NOT RUN, M19 report): trade-level M8/M13 no gate c; sleeves ORB/overnight-break/15-min ST add mean but raise maxDD (see out/M_sleeves.csv); M20 pair 10/10 + K4-RX5 x1.75 beats benchmark on mean AND maxDD in WF (+14.3k/-31k) and L8W (+12.1k/-7.8k) and gate d, but random-date/shift nulls rank only .84/.84 and .88/.46; and pair 10/10 ALONE already gives 25.4k/362k (L8W 36.0k/259k) via the S113 size credit (known V3 lot-curve effect) - K4 sleeve itself was selected on overlapping data; not a find.

- 2026-10-22T22:04:33Z trackDS300 BLOCK K (L2/tape at signal, 40 cells + B12 4 cells): 8 gate-a / 3 a+b (K8 sweep impact size8, K9 sweeps skip_hi, K10 refills skip_hi); best null ranks K19 va-pos skip_lo .99/.61 (maxDD worse), K4 burst skip_hi date .84 / feat dd .96; none passes gate c or d. B12/B12x spread filters lose (frozen thresholds were degenerate, disclosed in AMEND-4). K11 NOT RUN (no MBO ids); K1-K3 DUP of P1a.

- 2026-10-22T22:07:49Z trackDS300 BLOCK L (ML/statistical, 20 cells + L13 GA pending): 4 gate-a, 0 a+b. LEAD-ish but FAILS gate b: L5 Bayesian-shrinkage session x book size-8 (prior k=100): WF +4.8k/wk, maxDD -101k, null ranks date .96/.97 feat .96/1.00, gate d passes (boot lo +0.7k) - but the rule never fires in L8W (delta exactly 0) and half2 = 0: all gain is in 2024-02..2025-04 (12 rows/month changed) -> regime-specific, below the best-of-F line, not a find. L20 adversarial AUC IS-vs-OOS 0.737 (drift detectable). L4/L18 NOT RUN, L7/L14/L15/L19 DUP.

- 2026-10-22T22:07:49Z trackDS300 BLOCK I10 (VX term slope, daily-only, free CBOE data): 3 cells, 0 gate a (skip_lo -5.7k mean/-93k maxDD, skip_hi -9.8k).

Caveats: (1) trade-level cells run on the benchmark's own rows with the exact corrected-P9 points and the exact 1-s lock engine (replay bias 0 by construction; size cells use the S113 surface, whose credit below 14 lots explains why almost every 8/10-lot cell lowers maxDD - pair 10/10 alone beats 14/14, the known V3 lot-curve effect). (2) Regenerated cells (A, C, D, G7, B3/B8/B14, K18) use the pooled-delta P9 mapping; replay below. (3) Constant-parameter cells (C13, C14, C19, E11, F-lock levels) have no timing null: degenerate nulls are shown as deg/n-a and these cells cannot pass gate c. Lock cells use placebo-lock nulls, A cells an event-shift null that is not discriminating (rank 1.0 is not evidence). (4) Gate c requires BOTH date and feature null ranks >= 0.95 on delta mean and delta maxDD.

## 0c. O2/O3/O6/O7 reruns on gate a+b trade-level cells (100 outcome-permutation reps)

| tag                            |   O2_tick1_dmean |   O2_tick1_dmaxdd |   O2_tick2_dmean |   O2_tick2_dmaxdd |   O2_tick3_dmean |   O2_tick3_dmaxdd |   O3_exroll_dmean |   O3_exroll_dmaxdd |   O6_mirror_dmean |   O6_mirror_dmaxdd |   O7_outcome_perm_rank_mean |   O7_outcome_perm_rank_dd |
|:-------------------------------|-----------------:|------------------:|-----------------:|------------------:|-----------------:|------------------:|------------------:|-------------------:|------------------:|-------------------:|----------------------------:|--------------------------:|
| B13|prev-closed<3min           |        -2780.53  |        -49790.5   |        -2406.1   |          1727.24  |        -1554.31  |          28575    |          -851.465 |            4540.31 |          1486.81  |           26012.7  |                        0.61 |                      0.74 |
| B13|prev-closed<5min           |        -4158.72  |        -46933.9   |        -2604.24  |         11246.7   |         -532.425 |         -41761.8  |          -209.565 |          -60153    |           840.375 |          179980    |                        0.66 |                      0.72 |
| B16|expanding>1.0              |        -2563.61  |         92741.2   |        -1058.61  |        136243     |         1722.08  |         137144    |          1517.9   |           57061.9  |         -6237.03  |          -46336.1  |                        0.56 |                      0.45 |
| E5|ES15m-agree14-else8         |        -2811.73  |        -37484.4   |        -1145.38  |        -34855     |         -499.23  |         -47410.1  |          -385.009 |           37958    |          2456.76  |           96606.2  |                        0.5  |                      0.53 |
| E6|stops2->8                   |        -1474.7   |         20298.8   |         -172.721 |         19397.1   |          248.481 |          -2907.89 |          1592.91  |          -28389.4  |          7121.33  |          -11275.9  |                        0.72 |                      0.39 |
| E6|stops3->8                   |        -2427.04  |         10130.6   |         -733.311 |         -9281.15  |          456.12  |         -37094.2  |          2184.52  |          -15567.4  |          7383.23  |          -19433.9  |                        0.71 |                      0.41 |
| E11|ST10-HM10                  |        -4981.13  |         40487.1   |        -1069.01  |         30076.8   |         1077.45  |           2734    |          1107.9   |           15607.9  |           383.776 |          -39197.9  |                        0.14 |                      0.18 |
| E11|ST14-HM8                   |         2159.33  |        -39130.8   |         3044.58  |         16479.9   |         -841.671 |          17073    |          7120.89  |          -49913.6  |         -2139.82  |           19244.5  |                        0.91 |                      0.45 |
| E11|ST14-HM10                  |         4857.42  |          1257.91  |         5544.58  |           701.748 |         1235.67  |         -34629    |          6366.43  |          -30827.3  |          3335.64  |           -1249.39 |                        0.89 |                      0.35 |
| E17|cap30k                     |        -1916.16  |         36708.2   |        -1412.05  |         63657.8   |           76.159 |          12885.2  |          5481.23  |          -45135.6  |          2578.14  |          -13854.1  |                        0.87 |                      0.48 |
| H16|zigzag60|size8_hi          |         -668.751 |         15473.2   |          222.291 |         17794.7   |         1316.98  |           7134.12 |          4831.47  |          -70713.1  |          1003.19  |           33704.9  |                        0.52 |                      0.3  |
| H19|volfrac|size8_hi           |         -260.899 |         36711.9   |         -272.186 |         20994.6   |         1012     |         -31405.9  |          2067.85  |          -63378.6  |           -69.588 |          -16403.3  |                        0.82 |                      0.58 |
| H20|printed-sec/30min|size8_hi |         -262.893 |         24948.6   |         1688.17  |        -26505.1   |         2261.3   |           4075.62 |          3589.07  |           81385.3  |          4835.97  |           93771.1  |                        0.91 |                      0.34 |
| I4|ZN|rel-|s8                  |         -549.306 |          -808.642 |          115.011 |          8558.03  |         2693.34  |         -18164.3  |          7180.94  |          -37151.5  |          1591.25  |          -26423.7  |                        0.85 |                      0.39 |
| I9|BTC-asia|s8                 |         -992.76  |        172610     |        -1591.12  |        205593     |           -5.14  |         190189    |          2494.46  |          -20697.2  |          2896.05  |          -41942    |                        0.5  |                      0.41 |
| I19|gapdiv-NY|perm             |          799.887 |         79284.5   |         1294.48  |         64982.7   |         1104.68  |          39089.1  |          2445.31  |           70737.8  |         -5364.01  |           40430.8  |                        0.83 |                      0.39 |
| K8|sweep-impact|size8_hi       |         -755.473 |         25241.3   |         -109.94  |        -10178.8   |          927.363 |          11718.2  |           595.424 |           13227.6  |          -268.43  |           97804.5  |                        0.45 |                      0.53 |
| K9|sweeps15|skip_hi            |        -3119.51  |         15626.1   |        -1652.72  |         -6273.17  |        -1886.15  |          52941.1  |          1254.17  |           97583.1  |        -10040.3   |          162245    |                        0.72 |                      0.5  |
| K10|refills30|skip_hi          |        -2642.8   |         50955.3   |         -530.459 |         40293.5   |           -3.545 |           9100.44 |          -261.093 |           95085.8  |         -1082.21  |            4920.28 |                        0.63 |                      0.48 |

### Rescore of gate a+b trade-level cells on top of the BEST5 benchmark (coordinator addition)
```
BEST5 benchmark (14/10/10 by session, no combined cap, give-back keep 67% after 2 closed trades, week floor 12R) reproduced in lockeng: WF 26,462/93,138/284,751, L8W 56,397 (coordinator target 25.5k/93.1k/287k, L8W 56.1k).
| tag                            |   WF_mean |   WF_sd |   WF_maxdd |   d_mean_vs_BEST5 |   d_maxdd_vs_BEST5 |   L8W_d_mean |   L8W_d_maxdd | beats_BEST5_both   |
|:-------------------------------|----------:|--------:|-----------:|------------------:|-------------------:|-------------:|--------------:|:-------------------|
| B13|prev-closed<3min           |     24069 |   92940 |     345959 |             -2393 |              61208 |          528 |        -15962 | False              |
| B13|prev-closed<5min           |     23688 |   92871 |     362700 |             -2774 |              77949 |        -6550 |         -5688 | False              |
| B16|expanding>1.0              |     27337 |   82187 |     378787 |               875 |              94036 |         2233 |          4116 | False              |
| E5|ES15m-agree14-else8         |     23784 |   94671 |     405245 |             -2678 |             120494 |       -31933 |         89191 | False              |
| E6|stops2->8                   |     21517 |   90390 |     319061 |             -4945 |              34310 |       -11759 |         78539 | False              |
| E6|stops3->8                   |     24666 |   93425 |     335968 |             -1795 |              51218 |         -218 |           354 | False              |
| E11|ST10-HM10                  |     22551 |   83713 |     320019 |             -3911 |              35269 |       -15329 |         58258 | False              |
| E11|ST14-HM8                   |     24105 |   84846 |     336109 |             -2357 |              51359 |       -10515 |         56285 | False              |
| E11|ST14-HM10                  |     25417 |   88380 |     346372 |             -1045 |              61621 |        -9229 |         30199 | False              |
| E17|cap30k                     |     24441 |   88569 |     288938 |             -2021 |               4187 |       -19573 |         65853 | False              |
| H16|zigzag60|size8_hi          |     25844 |   83163 |     277415 |              -618 |              -7336 |         2990 |        -46482 | False              |
| H19|volfrac|size8_hi           |     25648 |   90230 |     272097 |              -814 |             -12654 |         8762 |        -21612 | False              |
| H20|printed-sec/30min|size8_hi |     24908 |   90514 |     289592 |             -1554 |               4841 |         2198 |        -16036 | False              |
| I4|ZN|rel-|s8                  |     21964 |   83860 |     305855 |             -4498 |              21104 |       -15738 |        125519 | False              |
| I9|BTC-asia|s8                 |     24954 |   97189 |     558204 |             -1508 |             273453 |        -3388 |         99219 | False              |
| I19|gapdiv-NY|perm             |     24561 |   90678 |     364626 |             -1901 |              79875 |          221 |        -26257 | False              |
| K8|sweep-impact|size8_hi       |     25629 |   92919 |     329456 |              -833 |              44705 |         2357 |          -787 | False              |
| K9|sweeps15|skip_hi            |     20664 |   83469 |     447364 |             -5798 |             162613 |         5777 |        -51837 | False              |
| K10|refills30|skip_hi          |     21061 |   85916 |     337159 |             -5400 |              52408 |         8595 |        -39842 | False              |

```

### D15/D16 timing nulls (closest near-misses)
```
D15 date-shift null (500 reps, trigger series shifted by whole label days): rank delta-mean 0.88, rank delta-maxDD 0.97
D16 date-shift null (500 reps, trigger series shifted by whole label days): rank delta-mean 0.95, rank delta-maxDD 0.99

```

### Direct L2 replay of regenerated a+b cells (L8W months)
```
S14x1 entry arm + XJ stop-join exit (P9 policy) from DIRECT replay on the replayed months; other rows keep the mapping; L8W = 2026-W35..W42 (needs months 2026-08..10). Partial coverage: L8W months 2026-08..10 (all four cells) plus, where listed, 6 WF sample months (D15, D16).
ds300_C13_ST60_HM40: months 2026-08,2026-09,2026-10; replayed trades 1282; mean replay-minus-mapped pts per trade +0.12 (sd 9.05); L8W mapped: mean 66,799 maxDD 219,034 (d vs bench +32,589/-48,099); L8W replay-substituted: mean 68,820 maxDD 275,568 (d +34,611/+8,435); WF mapped d +2,282/-1,379 vs WF replay-substituted (only replayed months substituted) d +1,798/-1,379; beats bench both windows on replay: False (L8W) / True (WF)
ds300_D15: months 2024-04,2024-10,2025-03,2025-08,2025-12,2026-05,2026-08,2026-09,2026-10; replayed trades 3312; mean replay-minus-mapped pts per trade -0.14 (sd 8.95); L8W mapped: mean 40,646 maxDD 250,612 (d vs bench +6,437/-16,521); L8W replay-substituted: mean 48,379 maxDD 234,839 (d +14,170/-32,294); WF mapped d +3,795/-51,176 vs WF replay-substituted (only replayed months substituted) d +2,970/-47,390; beats bench both windows on replay: True (L8W) / True (WF)
ds300_D16: months 2024-04,2024-10,2025-03,2025-08,2025-12,2026-05,2026-08,2026-09,2026-10; replayed trades 3541; mean replay-minus-mapped pts per trade +0.01 (sd 7.71); L8W mapped: mean 38,407 maxDD 177,785 (d vs bench +4,197/-89,349); L8W replay-substituted: mean 48,137 maxDD 173,100 (d +13,928/-94,034); WF mapped d +2,201/-34,949 vs WF replay-substituted (only replayed months substituted) d +2,553/-35,911; beats bench both windows on replay: True (L8W) / True (WF)
ds300_D9: months 2026-08,2026-09,2026-10; replayed trades 1102; mean replay-minus-mapped pts per trade -0.10 (sd 8.41); L8W mapped: mean 35,815 maxDD 254,288 (d vs bench +1,606/-12,845); L8W replay-substituted: mean 48,934 maxDD 203,390 (d +14,725/-63,743); WF mapped d +1,058/-38,454 vs WF replay-substituted (only replayed months substituted) d +1,893/-38,454; beats bench both windows on replay: True (L8W) / True (WF)

```

### N18 cost model
```
N18 cost model: fees per trade 14 NQ $67.76 vs 10 NQ + 40 MNQ $119.60 (delta $51.84); at 35.9 trades/wk = $-1,862/wk; S113 clip credit upper bound $43/trade = $1,542/wk. Mapping only.

```

### L13 GA (report-only)
```
{
 "selected": [
  "L5|shrink-k100"
 ],
 "fit_sharpe": 0.28076166796033736,
 "fit_bench": 0.17987314863100518,
 "holdout_sharpe": 0.29671344167208547,
 "holdout_bench": 0.29671344167208547,
 "holdout_d_mean": 0.0
}
```

### M19 drawdown-matched weights (report-only)
```
sleeve,max_w_with_WF_maxdd_le_benchmark,WF_mean,WF_sd,WF_maxdd
K4_RX5,0.0,24978.248239458368,104546.66354391939,401641.1409522926
M2_60-60,0.0,24978.248239458368,104546.66354391939,401641.1409522926
M2_opp-side-1xrange,0.0,24978.248239458368,104546.66354391939,401641.1409522926
M3_60-60,0.0,24978.248239458368,104546.66354391939,401641.1409522926
M3_opp-side-1xrange,0.0,24978.248239458368,104546.66354391939,401641.1409522926
M4_ST15min,0.0,24978.248239458368,104546.66354391939,401641.1409522926

```

### L20 adversarial validation
```
adversarial validation AUC (IS vs OOS) on the trade feature table: 0.737

```

### J20 month-of-year benchmark P&L (report-only)
```
,sum,mean,count
1,413328.8075602779,6358.904731696583,65
2,472998.70095257944,6391.8743371970195,74
3,484490.8399427242,5633.614417938654,86
4,45079.34781222212,530.3452683790838,85
5,231822.25726392498,2604.7444636396067,89
6,373196.6545017422,4390.548876491085,85
7,821676.6713934275,9129.740793260306,90
8,-90968.9292064642,-1045.6198759363701,87
9,426804.48268822336,4962.842821956086,86
10,276525.0156280419,3456.5626953505234,80
11,495660.7905672375,7867.631596305357,63
12,306287.77083011967,4861.710648097138,63

```

Block N (execution variants N1-N12): NOT RUN as a sample-month raw replay in this pass (each variant needs a new exec_engine_l2 intent program; only the direct replays above were run); N18 is a cost-model result; see QUESTIONS Q15.

## 1. Per-block tables (all scored cells; IS / WF / L8W; deltas vs benchmark; gates a-d; null ranks = share of 100 nulls beaten on delta mean / delta maxDD)

### Block A (39 cells; gate a 2, a+b 0, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A1|HA-ST | 4.3 | 24.0 | 103.6 | 487.7 | -137.9 | 1.67 | 35.3 | n/a | -0.9 | 86.0 | 65.2 | 130.3 | 296.1 | -116.3 | 31.0 | 29.0 | - | - | - | - | deg | deg |
| A2|median-src | 1.8 | 25.4 | 109.0 | 435.5 | -144.7 | 1.68 | 36.3 | n/a | 0.5 | 33.9 | 43.4 | 81.8 | 183.9 | -91.4 | 9.2 | -83.2 | - | Y | - | - | deg | deg |
| A3|GK-vol | 2.2 | 23.8 | 100.5 | 501.7 | -136.9 | 1.71 | 36.4 | n/a | -1.2 | 100.1 | 32.6 | 108.6 | 290.9 | -102.6 | -1.6 | 23.8 | - | - | - | - | deg | deg |
| A3|PK-vol | 3.1 | 21.1 | 100.4 | 462.6 | -136.6 | 1.51 | 36.6 | n/a | -3.9 | 61.0 | 52.1 | 96.2 | 215.6 | -102.6 | 17.9 | -51.5 | - | Y | - | - | deg | deg |
| A4|fast30-1.5 | 12.8 | 23.6 | 101.1 | 362.2 | -136.9 | 1.68 | 35.6 | n/a | -1.4 | -39.5 | 30.4 | 108.0 | 283.6 | -98.6 | -3.9 | 16.4 | - | - | - | - | deg | deg |
| A4|fast60-2.0 | 11.9 | 20.4 | 101.1 | 460.4 | -137.3 | 1.45 | 35.1 | n/a | -4.6 | 58.8 | 32.9 | 123.9 | 359.2 | -134.9 | -1.3 | 92.0 | - | - | - | - | deg | deg |
| A5|mult-pct-a0.3 | -0.1 | 25.2 | 103.0 | 429.3 | -136.8 | 1.76 | 35.7 | n/a | 0.2 | 27.6 | 37.0 | 95.3 | 266.6 | -89.3 | 2.8 | -0.6 | - | Y | - | - | deg | deg |
| A5|mult-pct-a0.6 | 3.3 | 20.2 | 101.8 | 587.2 | -136.6 | 1.43 | 35.0 | n/a | -4.7 | 185.6 | 35.7 | 112.7 | 349.9 | -135.1 | 1.5 | 82.7 | - | - | - | - | deg | deg |
| A6|chandelier-m2.0 | -2.5 | 18.9 | 107.1 | 737.0 | -137.8 | 1.27 | 37.4 | n/a | -6.1 | 335.4 | 62.0 | 117.1 | 217.9 | -122.3 | 27.8 | -49.2 | - | Y | - | - | deg | deg |
| A6|chandelier-m3.0 | -3.0 | 30.7 | 103.5 | 452.7 | -144.1 | 2.14 | 37.2 | n/a | 5.7 | 51.0 | 37.7 | 94.7 | 292.5 | -134.4 | 3.5 | 25.4 | - | - | - | - | deg | deg |
| A7|keltner-m1.5 | -7.4 | 15.8 | 83.6 | 459.9 | -136.0 | 1.37 | 36.0 | n/a | -9.1 | 58.2 | 66.1 | 41.4 | 111.8 | 8.7 | 31.9 | -155.4 | - | Y | - | - | deg | deg |
| A7|keltner-m2.0 | -7.9 | 12.0 | 79.0 | 634.0 | -135.9 | 1.09 | 36.5 | n/a | -13.0 | 232.3 | 39.3 | 39.8 | 160.6 | 0.2 | 5.1 | -106.5 | - | Y | - | - | deg | deg |
| A7|keltner-m2.5 | -0.2 | 7.3 | 83.5 | 523.2 | -135.3 | 0.63 | 36.8 | n/a | -17.7 | 121.6 | 51.5 | 79.9 | 153.2 | -24.4 | 17.3 | -113.9 | - | Y | - | - | deg | deg |
| A8|donchian20|w0.25 | 9.5 | 26.6 | 114.4 | 414.5 | -188.3 | 1.68 | nan | n/a | 1.6 | 12.9 | 50.1 | 126.5 | 273.2 | -104.9 | 15.9 | 6.0 | - | - | - | - | deg | deg |
| A8|donchian20|w0.5 | 5.4 | 28.2 | 128.2 | 459.0 | -242.4 | 1.59 | nan | n/a | 3.3 | 57.4 | 66.0 | 145.4 | 294.5 | -119.5 | 31.8 | 27.4 | - | - | - | - | 0.98/0.69 | deg |
| A8|donchian20|w1.0 | -2.8 | 31.5 | 163.1 | 617.1 | -350.7 | 1.39 | nan | n/a | 6.5 | 215.5 | 97.7 | 186.1 | 354.9 | -148.6 | 63.5 | 87.8 | - | - | - | - | deg | deg |
| A8|donchian55|w0.25 | 11.4 | 29.4 | 113.5 | 401.8 | -182.3 | 1.87 | nan | n/a | 4.4 | 0.2 | 33.2 | 115.9 | 291.0 | -122.0 | -1.0 | 23.9 | - | - | - | Y | deg | deg |
| A8|donchian55|w0.5 | 9.2 | 33.8 | 125.5 | 443.8 | -229.7 | 1.94 | nan | n/a | 8.9 | 42.2 | 32.3 | 124.9 | 315.0 | -145.2 | -1.9 | 47.8 | - | - | - | Y | 0.93/0.58 | deg |
| A8|donchian55|w1.0 | 4.8 | 42.7 | 155.8 | 628.6 | -324.5 | 1.97 | nan | n/a | 17.7 | 226.9 | 30.3 | 148.4 | 380.9 | -191.4 | -3.9 | 113.7 | - | - | - | Y | deg | deg |
| A10|slope-k0.02 | 4.4 | 29.1 | 100.8 | 414.4 | -136.3 | 2.08 | 36.2 | n/a | 4.1 | 12.7 | 55.5 | 105.2 | 261.3 | -77.0 | 21.3 | -5.9 | - | Y | - | - | deg | deg |
| A10|slope-k0.05 | 2.7 | 27.1 | 105.8 | 421.4 | -136.6 | 1.85 | 36.3 | n/a | 2.2 | 19.7 | 58.3 | 134.5 | 266.2 | -116.5 | 24.0 | -0.9 | - | Y | - | - | deg | deg |
| A10|slope-k0.1 | 7.0 | 19.2 | 102.0 | 645.8 | -137.1 | 1.36 | 35.8 | n/a | -5.8 | 244.1 | 70.6 | 154.1 | 239.4 | -137.1 | 36.4 | -27.8 | - | Y | - | - | deg | deg |
| A11|anchor-09:30ET | 15.0 | 26.7 | 100.3 | 482.3 | -138.2 | 1.92 | 36.3 | n/a | 1.7 | 80.6 | 19.1 | 103.7 | 293.8 | -138.2 | -15.1 | 26.6 | - | - | - | - | deg | deg |
| A11|anchor-18:00ET | 9.0 | 26.0 | 101.1 | 399.1 | -137.0 | 1.86 | 36.5 | n/a | 1.0 | -2.5 | 44.7 | 96.0 | 267.7 | -99.7 | 10.5 | 0.6 | Y | - | Y | - | 1.00/1.00 | deg |
| A11|anchor-weekly | 24.5 | 25.0 | 101.8 | 538.0 | -138.2 | 1.77 | 36.3 | n/a | -0.0 | 136.4 | 20.4 | 114.7 | 349.8 | -138.2 | -13.8 | 82.6 | - | - | - | - | deg | deg |
| A12|swing-anchor-L30 | 4.8 | 33.1 | 99.4 | 632.8 | -144.2 | 2.41 | 36.5 | n/a | 8.2 | 231.1 | 28.0 | 124.7 | 344.2 | -135.0 | -6.2 | 77.1 | - | - | - | - | deg | deg |
| A12|swing-anchor-L60 | 3.9 | 21.9 | 102.8 | 392.0 | -136.6 | 1.54 | 35.8 | n/a | -3.1 | -9.6 | 27.9 | 143.1 | 279.9 | -135.9 | -6.4 | 12.8 | - | - | - | - | deg | deg |
| A13|vwap-slope15 | 14.8 | 22.5 | 106.1 | 813.8 | -137.2 | 1.53 | 33.9 | n/a | -2.5 | 412.2 | 42.1 | 84.1 | 164.3 | -120.9 | 7.9 | -102.8 | - | Y | - | - | deg | deg |
| A13|vwap-slope5 | 14.0 | 17.5 | 105.1 | 668.7 | -137.3 | 1.20 | 33.6 | n/a | -7.5 | 267.1 | 47.3 | 85.9 | 164.6 | -120.6 | 13.1 | -102.6 | - | Y | - | - | deg | deg |
| A15|ema5m-20 | 1.2 | 29.3 | 99.3 | 548.8 | -155.4 | 2.13 | 37.6 | n/a | 4.3 | 147.2 | 71.8 | 122.3 | 174.9 | -97.4 | 37.6 | -92.3 | - | Y | - | - | deg | deg |
| A15|ema5m-40 | 13.3 | 25.2 | 103.5 | 401.6 | -137.1 | 1.75 | 35.8 | n/a | 0.2 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| A15|ema5m-60 | 31.5 | 27.2 | 113.1 | 445.3 | -140.2 | 1.73 | 35.0 | n/a | 2.2 | 43.7 | 49.2 | 112.3 | 233.0 | -99.7 | 15.0 | -34.2 | - | Y | - | - | deg | deg |
| A16|slope-sign | -8.5 | -1.2 | 101.1 | 1003.4 | -136.3 | -0.09 | 27.5 | n/a | -26.2 | 601.7 | -92.8 | 64.0 | 742.3 | -136.1 | -127.0 | 475.1 | - | - | - | - | deg | deg |
| A16|slope-t>1 | -9.4 | -2.0 | 95.4 | 1077.3 | -136.3 | -0.15 | 24.0 | n/a | -27.0 | 675.6 | -94.5 | 59.4 | 755.9 | -135.6 | -128.7 | 488.8 | - | - | - | - | deg | deg |
| A17|flip-outside-prior-range | 11.5 | 25.1 | 100.3 | 362.6 | -137.2 | 1.80 | 35.2 | n/a | 0.1 | -39.1 | 31.0 | 110.0 | 239.5 | -137.2 | -3.2 | -27.6 | Y | - | Y | - | 1.00/1.00 | deg |
| A19|vol>1.0x | 7.6 | 17.8 | 103.7 | 628.4 | -136.2 | 1.24 | 34.7 | n/a | -7.2 | 226.8 | 31.9 | 117.1 | 375.4 | -135.0 | -2.3 | 108.3 | - | - | - | - | deg | deg |
| A19|vol>1.5x | 5.2 | 20.0 | 95.8 | 626.5 | -137.9 | 1.51 | 33.1 | n/a | -4.9 | 224.8 | 29.6 | 105.0 | 354.0 | -126.0 | -4.6 | 86.9 | - | - | - | - | deg | deg |
| A20|ST-2min | 1.9 | 23.1 | 101.5 | 479.9 | -137.0 | 1.64 | 35.1 | n/a | -1.9 | 78.2 | 60.6 | 89.8 | 162.8 | -134.9 | 26.4 | -104.3 | - | Y | - | - | deg | deg |
| A20|ST-3min | -6.6 | 16.8 | 101.7 | 499.3 | -152.5 | 1.19 | 35.0 | n/a | -8.1 | 97.7 | 86.5 | 93.2 | 95.5 | -88.7 | 52.3 | -171.7 | - | Y | - | - | deg | deg |

### Block B (26 cells; gate a 4, a+b 4, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| B3|second-chance | 8.8 | 24.8 | 104.9 | 415.2 | -140.0 | 1.70 | 36.2 | n/a | -0.2 | 13.6 | 32.2 | 117.8 | 284.3 | -126.2 | -2.0 | 17.2 | - | - | - | - | deg | deg |
| B5|first-half | -5.6 | 21.5 | 100.8 | 353.0 | -148.8 | 1.54 | 32.1 | 52.1 | -3.5 | -48.6 | 0.8 | 117.2 | 242.1 | -135.6 | -33.4 | -25.0 | - | - | - | - | 0.43/0.92 | 0.53/0.94 |
| B6|noentry-last10min | 12.1 | 32.0 | 116.6 | 411.9 | -137.8 | 1.98 | 34.8 | 29.1 | 7.1 | 10.2 | 64.2 | 153.6 | 305.0 | -107.6 | 30.0 | 37.8 | - | - | - | - | 0.96/0.65 | 0.96/0.77 |
| B6|noentry-last5min | 20.8 | 28.8 | 113.9 | 543.7 | -136.7 | 1.82 | 35.3 | 16.4 | 3.8 | 142.1 | 52.7 | 138.2 | 243.5 | -101.2 | 18.5 | -23.6 | - | Y | - | - | deg | deg |
| B8|delay-5min-close | 0.4 | 28.5 | 106.3 | 683.2 | -137.1 | 1.93 | 36.5 | n/a | 3.5 | 281.6 | -7.8 | 108.0 | 424.1 | -135.8 | -42.0 | 157.0 | - | - | - | - | deg | deg |
| B9|ES-flip10 | 1.0 | 21.7 | 93.7 | 476.3 | -154.0 | 1.67 | 30.3 | 76.3 | -3.2 | 74.6 | 60.4 | 122.6 | 311.5 | -110.2 | 26.2 | 44.4 | - | - | - | - | 0.72/0.73 | 0.58/0.69 |
| B9|ES-flip20 | 3.4 | 21.1 | 97.4 | 529.6 | -139.2 | 1.56 | 32.4 | 65.8 | -3.9 | 128.0 | 60.6 | 129.6 | 360.3 | -135.8 | 26.3 | 93.1 | - | - | - | - | deg | deg |
| B10|rsi70 | 10.1 | 23.4 | 97.2 | 442.0 | -136.0 | 1.74 | 34.6 | 32.2 | -1.5 | 40.3 | 40.7 | 99.4 | 207.6 | -86.3 | 6.5 | -59.5 | - | Y | - | - | deg | deg |
| B10|rsi80 | 14.2 | 25.5 | 103.9 | 429.2 | -137.3 | 1.77 | 35.7 | 4.8 | 0.6 | 27.6 | 26.7 | 114.2 | 281.3 | -135.8 | -7.5 | 14.2 | - | - | - | - | 0.58/0.40 | 0.58/0.41 |
| B11|gap10 | 13.7 | 25.1 | 104.5 | 401.6 | -137.1 | 1.73 | 36.0 | 0.1 | 0.1 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | Y | deg | deg |
| B11|gap5 | 13.7 | 25.3 | 104.7 | 401.6 | -137.1 | 1.74 | 36.0 | 0.6 | 0.3 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | Y | 0.49/0.66 | 0.60/0.61 |
| B12x|spread>4ticks(p75/p90) | 11.8 | 24.6 | 101.7 | 483.1 | -136.8 | 1.75 | 33.7 | 49.4 | -0.3 | 81.5 | 36.5 | 115.8 | 253.5 | -134.6 | 2.3 | -13.7 | - | Y | - | - | deg | deg |
| B12x|spread>6ticks(p75/p90) | 13.9 | 26.1 | 105.5 | 421.2 | -150.8 | 1.78 | 34.8 | 21.9 | 1.1 | 19.5 | 24.2 | 116.6 | 247.5 | -108.7 | -10.1 | -19.6 | - | - | - | - | 0.72/0.66 | 0.69/0.65 |
| B12|spread>1tick | 4.8 | 1.5 | 20.9 | 128.5 | -70.9 | 0.51 | 1.5 | 155.3 | -23.5 | -273.1 | 10.5 | 12.4 | 0.0 | 0.0 | -23.8 | -267.1 | - | - | - | - | 0.35/1.00 | 0.65/0.92 |
| B12|spread>2tick | 11.0 | 2.8 | 74.9 | 629.1 | -140.9 | 0.27 | 18.5 | 123.8 | -22.2 | 227.5 | -17.2 | 96.1 | 270.4 | -135.9 | -51.5 | 3.3 | - | - | - | - | deg | deg |
| B13|prev-closed<3min | 10.2 | 25.7 | 104.3 | 319.0 | -136.7 | 1.78 | 34.9 | 14.6 | 0.7 | -82.6 | 41.1 | 109.3 | 256.7 | -98.1 | 6.9 | -10.4 | Y | Y | - | - | 0.58/0.99 | 0.56/1.00 |
| B13|prev-closed<5min | 6.5 | 25.8 | 104.0 | 322.7 | -136.7 | 1.79 | 34.4 | 20.1 | 0.8 | -78.9 | 34.8 | 106.3 | 250.0 | -109.5 | 0.6 | -17.1 | Y | Y | - | - | 0.59/0.94 | 0.62/0.99 |
| B14|limit-flip-close-3min | 13.7 | 27.3 | 102.9 | 376.7 | -136.7 | 1.91 | 36.0 | n/a | 2.4 | -25.0 | 40.6 | 107.0 | 250.0 | -99.9 | 6.4 | -17.2 | Y | Y | - | - | deg | deg |
| B15|coiled<0.5 | -0.3 | -0.1 | 1.4 | 16.8 | -16.8 | -0.61 | 0.0 | 157.9 | -25.1 | -384.9 | 0.0 | 0.0 | 0.0 | 0.0 | -34.2 | -267.1 | - | - | - | - | deg | deg |
| B15|coiled<1.0 | 4.0 | 12.0 | 84.1 | 596.5 | -139.0 | 1.03 | 22.8 | 108.7 | -13.0 | 194.8 | 47.5 | 133.3 | 183.0 | -136.3 | 13.3 | -84.2 | - | Y | - | - | 0.37/0.27 | 0.40/0.35 |
| B16|expanding>1.0 | 6.0 | 25.4 | 96.6 | 367.6 | -136.6 | 1.90 | 31.5 | 58.0 | 0.4 | -34.1 | 58.8 | 105.3 | 218.8 | -85.5 | 24.6 | -48.3 | Y | Y | - | - | 0.81/0.84 | 0.86/0.96 |
| B16|expanding>1.5 | 0.4 | 7.7 | 51.1 | 371.1 | -134.8 | 1.09 | 10.9 | 132.9 | -17.3 | -30.5 | 27.2 | 53.7 | 120.2 | -62.8 | -7.0 | -146.9 | - | - | - | - | deg | deg |
| B18|size8-against | 11.5 | 27.2 | 103.2 | 452.0 | -138.5 | 1.90 | 44.8 | 79.2 | 2.2 | 50.3 | 46.7 | 96.2 | 174.2 | -134.3 | 12.5 | -92.9 | - | Y | - | - | 0.54/0.28 | 0.51/0.37 |
| B18|skip-against | 12.4 | 12.9 | 94.2 | 674.5 | -151.4 | 0.99 | 25.3 | 83.9 | -12.0 | 272.9 | 53.5 | 99.2 | 134.6 | -134.6 | 19.3 | -132.5 | - | Y | - | - | deg | deg |
| B19|first-only | -3.5 | 8.9 | 81.7 | 885.2 | -136.0 | 0.78 | 22.6 | 87.5 | -16.1 | 483.6 | 16.1 | 83.6 | 287.8 | -134.9 | -18.1 | 20.7 | - | - | - | - | 0.02/0.00 | 0.25/0.09 |
| B20|skip-first | 7.5 | 21.6 | 92.6 | 653.1 | -136.3 | 1.68 | 28.6 | 85.3 | -3.4 | 251.5 | 31.6 | 103.3 | 268.8 | -134.5 | -2.6 | 1.7 | - | - | - | - | 0.97/0.32 | 0.59/0.18 |

### Block C (68 cells; gate a 5, a+b 1, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C1|med45 | -10.8 | 15.6 | 95.5 | 473.1 | -136.7 | 1.18 | 38.0 | n/a | -9.3 | 71.4 | 42.0 | 100.6 | 155.6 | -135.6 | 7.8 | -111.6 | - | Y | - | - | deg | deg |
| C1|med60 | -6.6 | 4.2 | 111.2 | 1127.7 | -139.6 | 0.27 | 23.5 | n/a | -20.8 | 726.1 | -26.7 | 132.7 | 336.1 | -136.0 | -60.9 | 68.9 | - | - | - | - | deg | deg |
| C1|med80 | -1.3 | -6.8 | 105.2 | 1689.7 | -138.3 | -0.47 | 15.8 | n/a | -31.8 | 1288.1 | -29.5 | 83.3 | 346.9 | -135.9 | -63.7 | 79.8 | - | - | - | - | deg | deg |
| C2|med45 | -10.8 | 18.7 | 110.6 | 821.7 | -141.0 | 1.22 | 53.3 | n/a | -6.3 | 420.1 | 20.3 | 108.6 | 334.3 | -134.4 | -13.9 | 67.1 | - | - | - | - | deg | deg |
| C2|med60 | 4.0 | 19.2 | 109.2 | 703.8 | -138.6 | 1.27 | 38.5 | n/a | -5.8 | 302.2 | 39.9 | 93.5 | 206.1 | -91.8 | 5.7 | -61.1 | - | Y | - | - | deg | deg |
| C2|med80 | 14.5 | 6.7 | 110.8 | 826.2 | -143.8 | 0.44 | 26.2 | n/a | -18.3 | 424.6 | 21.0 | 118.6 | 337.9 | -143.8 | -13.2 | 70.8 | - | - | - | - | deg | deg |
| C3|med45 | 2.0 | 16.2 | 107.1 | 648.3 | -142.4 | 1.09 | 41.4 | n/a | -8.8 | 246.6 | 68.0 | 125.1 | 213.9 | -139.7 | 33.8 | -53.2 | - | Y | - | - | deg | deg |
| C3|med60 | -18.6 | 19.2 | 115.2 | 617.8 | -143.5 | 1.20 | 29.9 | n/a | -5.8 | 216.1 | 73.0 | 142.1 | 276.3 | -137.4 | 38.8 | 9.1 | - | - | - | - | deg | deg |
| C3|med80 | 3.3 | 21.0 | 113.2 | 539.5 | -137.1 | 1.34 | 22.7 | n/a | -3.9 | 137.9 | -9.7 | 122.1 | 398.2 | -135.4 | -43.9 | 131.0 | - | - | - | - | deg | deg |
| C4|k1 | -10.3 | 8.0 | 107.0 | 1372.2 | -140.9 | 0.54 | 71.6 | n/a | -17.0 | 970.6 | 4.2 | 97.8 | 380.6 | -140.9 | -30.0 | 113.5 | - | - | - | - | deg | deg |
| C4|k2 | -6.0 | 18.7 | 106.1 | 666.9 | -137.9 | 1.27 | 64.3 | n/a | -6.3 | 265.2 | 52.1 | 93.9 | 227.4 | -43.7 | 17.9 | -39.8 | - | Y | - | - | deg | deg |
| C5|cap60 | 7.4 | 13.1 | 104.7 | 846.6 | -138.5 | 0.90 | 56.6 | n/a | -11.9 | 444.9 | 25.8 | 95.4 | 290.5 | -134.8 | -8.4 | 23.4 | - | - | - | - | deg | deg |
| C5|cap90 | 6.9 | 15.6 | 100.0 | 552.7 | -138.9 | 1.13 | 47.1 | n/a | -9.4 | 151.1 | -32.6 | 103.9 | 472.3 | -134.7 | -66.8 | 205.2 | - | - | - | - | deg | deg |
| C6|e0.5 | 14.1 | 14.3 | 102.6 | 593.0 | -139.7 | 1.01 | 34.3 | n/a | -10.7 | 191.4 | 26.0 | 118.9 | 388.8 | -135.7 | -8.2 | 121.7 | - | - | - | - | deg | deg |
| C6|e1.0 | 16.4 | 17.0 | 110.1 | 690.7 | -138.0 | 1.11 | 35.7 | n/a | -8.0 | 289.1 | 26.8 | 129.3 | 446.8 | -134.7 | -7.4 | 179.6 | - | - | - | - | deg | deg |
| C7|45/60/75 | -0.2 | 9.8 | 102.3 | 1008.8 | -137.8 | 0.69 | 36.5 | n/a | -15.2 | 607.1 | 5.8 | 102.0 | 357.6 | -134.7 | -28.5 | 90.5 | - | - | - | - | deg | deg |
| C7|75/60/45 | 8.1 | 27.9 | 109.8 | 473.2 | -182.8 | 1.83 | 41.4 | n/a | 2.9 | 71.6 | 9.5 | 108.6 | 358.3 | -134.6 | -24.7 | 91.2 | - | - | - | - | deg | deg |
| C8|dow | 17.7 | 23.9 | 102.2 | 640.3 | -147.2 | 1.69 | 35.8 | n/a | -1.1 | 238.7 | 36.7 | 86.9 | 233.8 | -84.3 | 2.5 | -33.3 | - | Y | - | - | deg | deg |
| C9|event-stop75 | 19.4 | 22.1 | 105.3 | 360.4 | -137.0 | 1.51 | 35.6 | n/a | -2.9 | -41.3 | 19.8 | 119.9 | 360.4 | -135.1 | -14.4 | 93.2 | - | - | - | - | deg | deg |
| C10|ES-vol-med60 | -3.9 | 22.6 | 105.2 | 605.8 | -136.9 | 1.55 | 32.5 | n/a | -2.4 | 204.2 | 73.3 | 111.5 | 136.9 | -136.9 | 39.1 | -130.2 | - | Y | - | - | deg | deg |
| C11|round100 | 14.1 | 24.5 | 103.3 | 373.0 | -138.3 | 1.71 | 35.8 | n/a | -0.5 | -28.6 | 35.3 | 112.2 | 270.8 | -123.7 | 1.0 | 3.7 | - | - | - | - | deg | deg |
| C12|prior-HL | 11.3 | 24.0 | 100.4 | 481.4 | -140.7 | 1.72 | 35.5 | n/a | -1.0 | 79.7 | 27.4 | 96.5 | 246.8 | -90.4 | -6.9 | -20.3 | - | - | - | - | deg | deg |
| C13|ST40-HM40 | 11.9 | 27.0 | 100.5 | 478.4 | -137.2 | 1.94 | 67.5 | n/a | 2.0 | 76.8 | 27.1 | 93.2 | 254.7 | -134.7 | -7.1 | -12.4 | - | - | - | - | deg | deg |
| C13|ST40-HM50 | -3.9 | 36.3 | 109.0 | 466.5 | -137.0 | 2.40 | 57.6 | n/a | 11.3 | 64.8 | 6.9 | 104.6 | 305.5 | -134.5 | -27.3 | 38.4 | - | - | - | - | deg | deg |
| C13|ST40-HM60 | 4.2 | 29.6 | 100.2 | 363.1 | -136.7 | 2.13 | 53.3 | n/a | 4.6 | -38.5 | 1.1 | 94.4 | 363.1 | -135.6 | -33.1 | 96.0 | Y | - | - | - | deg | deg |
| C13|ST40-HM70 | -1.8 | 19.4 | 96.1 | 642.1 | -138.9 | 1.46 | 48.6 | n/a | -5.6 | 240.5 | -15.3 | 86.6 | 305.3 | -135.3 | -49.5 | 38.2 | - | - | - | - | deg | deg |
| C13|ST40-HM80 | 1.5 | 19.3 | 102.6 | 579.3 | -140.0 | 1.36 | 45.8 | n/a | -5.6 | 177.6 | -13.2 | 119.3 | 327.9 | -135.8 | -47.4 | 60.8 | - | - | - | - | deg | deg |
| C13|ST50-HM40 | 18.6 | 20.2 | 97.2 | 692.0 | -137.0 | 1.50 | 56.5 | n/a | -4.8 | 290.4 | 64.2 | 114.7 | 203.6 | -50.5 | 29.9 | -63.5 | - | Y | - | - | deg | deg |
| C13|ST50-HM50 | 7.3 | 28.4 | 101.4 | 418.4 | -137.1 | 2.02 | 47.7 | n/a | 3.5 | 16.8 | 63.6 | 105.7 | 222.2 | -135.6 | 29.4 | -45.0 | - | Y | - | - | deg | deg |
| C13|ST50-HM60 | 13.5 | 28.4 | 100.5 | 429.0 | -137.4 | 2.03 | 43.3 | n/a | 3.4 | 27.3 | 55.6 | 87.0 | 195.7 | -80.4 | 21.4 | -71.5 | - | Y | - | - | deg | deg |
| C13|ST50-HM70 | 5.5 | 15.3 | 96.4 | 553.1 | -139.0 | 1.14 | 39.7 | n/a | -9.7 | 151.5 | 41.1 | 130.6 | 161.0 | -135.1 | 6.9 | -106.2 | - | Y | - | - | deg | deg |
| C13|ST50-HM80 | 8.7 | 15.4 | 98.6 | 568.1 | -136.1 | 1.13 | 36.5 | n/a | -9.6 | 166.4 | 46.3 | 148.9 | 268.5 | -134.6 | 12.1 | 1.4 | - | - | - | - | deg | deg |
| C13|ST60-HM40 | 19.4 | 27.3 | 99.3 | 400.3 | -136.2 | 1.98 | 50.4 | n/a | 2.3 | -1.4 | 66.8 | 108.1 | 219.0 | -67.4 | 32.6 | -48.1 | Y | Y | - | - | deg | deg |
| C13|ST60-HM50 | 6.6 | 26.5 | 104.4 | 622.5 | -139.7 | 1.83 | 41.2 | n/a | 1.5 | 220.9 | 51.8 | 122.3 | 342.7 | -135.2 | 17.6 | 75.5 | - | - | - | - | deg | deg |
| C13|ST60-HM60 | 13.7 | 25.0 | 104.5 | 401.6 | -137.1 | 1.72 | 35.9 | n/a | 0.0 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| C13|ST60-HM70 | 11.2 | 9.7 | 102.6 | 592.4 | -139.0 | 0.68 | 32.0 | n/a | -15.3 | 190.8 | 1.8 | 118.0 | 249.7 | -136.4 | -32.5 | -17.4 | - | - | - | - | deg | deg |
| C13|ST60-HM80 | 14.4 | 18.2 | 106.5 | 544.3 | -137.4 | 1.23 | 30.3 | n/a | -6.8 | 142.6 | -12.2 | 133.1 | 325.5 | -134.4 | -46.4 | 58.3 | - | - | - | - | deg | deg |
| C13|ST70-HM40 | 9.7 | 20.5 | 103.4 | 537.5 | -148.3 | 1.43 | 46.0 | n/a | -4.5 | 135.8 | 70.6 | 151.2 | 261.9 | -135.0 | 36.4 | -5.3 | - | Y | - | - | deg | deg |
| C13|ST70-HM50 | -2.2 | 19.4 | 103.7 | 704.5 | -165.0 | 1.35 | 36.5 | n/a | -5.6 | 302.9 | 12.4 | 87.0 | 286.8 | -134.9 | -21.8 | 19.7 | - | - | - | - | deg | deg |
| C13|ST70-HM60 | 1.4 | 11.5 | 103.3 | 772.3 | -163.3 | 0.81 | 31.2 | n/a | -13.4 | 370.6 | 28.0 | 106.0 | 262.9 | -135.5 | -6.2 | -4.3 | - | - | - | - | deg | deg |
| C13|ST70-HM70 | -6.1 | 3.1 | 101.7 | 881.3 | -158.7 | 0.22 | 27.4 | n/a | -21.8 | 479.7 | -3.7 | 116.9 | 239.9 | -139.1 | -37.9 | -27.2 | - | - | - | - | deg | deg |
| C13|ST70-HM80 | 1.2 | 7.5 | 101.9 | 885.3 | -138.3 | 0.53 | 25.7 | n/a | -17.5 | 483.7 | 2.4 | 145.0 | 331.2 | -135.4 | -31.8 | 64.1 | - | - | - | - | deg | deg |
| C13|ST80-HM40 | -0.6 | 15.0 | 92.7 | 553.3 | -135.2 | 1.17 | 43.3 | n/a | -9.9 | 151.6 | 76.1 | 110.1 | 203.4 | -47.2 | 41.9 | -63.7 | - | Y | - | - | deg | deg |
| C13|ST80-HM50 | -14.7 | 20.7 | 106.4 | 670.3 | -140.0 | 1.40 | 34.4 | n/a | -4.3 | 268.7 | 57.6 | 137.3 | 304.6 | -135.0 | 23.4 | 37.5 | - | - | - | - | deg | deg |
| C13|ST80-HM60 | -3.9 | 11.2 | 110.0 | 741.1 | -141.4 | 0.73 | 28.4 | n/a | -13.8 | 339.5 | 42.4 | 125.6 | 272.8 | -137.9 | 8.1 | 5.7 | - | - | - | - | deg | deg |
| C13|ST80-HM70 | -9.4 | 5.7 | 100.4 | 748.4 | -142.8 | 0.41 | 26.0 | n/a | -19.3 | 346.8 | 33.9 | 129.9 | 340.3 | -135.4 | -0.3 | 73.2 | - | - | - | - | deg | deg |
| C13|ST80-HM80 | -0.6 | 7.3 | 99.2 | 955.7 | -139.1 | 0.53 | 24.5 | n/a | -17.7 | 554.1 | 27.6 | 135.7 | 272.1 | -134.5 | -6.6 | 4.9 | - | - | - | - | deg | deg |
| C14|asia40-ny60 | 19.5 | 18.5 | 111.1 | 879.2 | -136.9 | 1.20 | 49.0 | n/a | -6.4 | 477.5 | 49.1 | 105.9 | 268.2 | -134.7 | 14.9 | 1.1 | - | - | - | - | deg | deg |
| C14|asia40-ny75 | 9.7 | 26.1 | 110.3 | 926.7 | -136.3 | 1.71 | 47.5 | n/a | 1.1 | 525.0 | 51.2 | 106.9 | 272.2 | -135.9 | 17.0 | 5.1 | - | - | - | - | deg | deg |
| C14|asia40-ny90 | 10.6 | 27.8 | 109.1 | 1035.2 | -136.9 | 1.83 | 46.7 | n/a | 2.8 | 633.6 | 54.8 | 94.6 | 231.2 | -73.8 | 20.6 | -36.0 | - | Y | - | - | deg | deg |
| C14|asia50-ny60 | 9.4 | 31.9 | 108.1 | 487.7 | -141.3 | 2.13 | 42.0 | n/a | 7.0 | 86.1 | 57.1 | 93.4 | 238.0 | -89.1 | 22.9 | -29.1 | - | Y | - | - | deg | deg |
| C14|asia50-ny75 | 2.2 | 33.0 | 108.0 | 602.6 | -137.0 | 2.20 | 40.1 | n/a | 8.0 | 200.9 | 64.7 | 99.1 | 201.3 | -100.8 | 30.5 | -65.8 | - | Y | - | - | deg | deg |
| C14|asia50-ny90 | 5.4 | 29.6 | 107.8 | 658.8 | -137.2 | 1.98 | 39.0 | n/a | 4.6 | 257.2 | 54.2 | 116.9 | 220.7 | -135.0 | 19.9 | -46.4 | - | Y | - | - | deg | deg |
| C14|asia60-ny60 | 13.7 | 25.0 | 104.5 | 401.6 | -137.1 | 1.72 | 35.9 | n/a | 0.0 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| C14|asia60-ny75 | 10.6 | 25.7 | 100.6 | 430.9 | -137.7 | 1.84 | 34.3 | n/a | 0.7 | 29.3 | 42.4 | 111.3 | 222.4 | -103.3 | 8.2 | -44.7 | - | Y | - | - | deg | deg |
| C14|asia60-ny90 | 15.7 | 24.4 | 104.0 | 422.7 | -141.8 | 1.69 | 33.6 | n/a | -0.6 | 21.1 | 53.0 | 111.7 | 202.5 | -111.1 | 18.8 | -64.6 | - | Y | - | - | deg | deg |
| C15|shrink10 | 8.2 | 19.6 | 96.5 | 469.9 | -135.9 | 1.46 | 65.6 | n/a | -5.4 | 68.3 | 34.4 | 115.6 | 191.9 | -89.1 | 0.2 | -75.2 | - | Y | - | - | deg | deg |
| C15|shrink5 | 11.3 | 30.8 | 103.5 | 340.8 | -138.9 | 2.14 | 53.8 | n/a | 5.8 | -60.8 | 30.9 | 97.6 | 257.0 | -75.5 | -3.3 | -10.1 | Y | - | - | - | deg | deg |
| C16|grow10 | 11.8 | 11.4 | 99.3 | 572.3 | -137.7 | 0.82 | 28.0 | n/a | -13.6 | 170.6 | -6.3 | 132.4 | 383.5 | -134.9 | -40.5 | 116.4 | - | - | - | - | deg | deg |
| C16|grow5 | 5.9 | 10.3 | 100.2 | 687.6 | -139.9 | 0.74 | 29.6 | n/a | -14.7 | 286.0 | 1.2 | 104.7 | 369.9 | -134.8 | -33.0 | 102.7 | - | - | - | - | deg | deg |
| C17|stop60-time120 | -10.1 | 20.0 | 120.4 | 1111.5 | -140.3 | 1.20 | 48.1 | n/a | -5.0 | 709.8 | 72.5 | 157.0 | 308.8 | -138.4 | 38.3 | 41.7 | - | - | - | - | deg | deg |
| C17|stop60-time30 | -61.6 | -9.4 | 97.6 | 2660.5 | -144.6 | -0.69 | 114.2 | n/a | -34.4 | 2258.8 | 62.8 | 94.5 | 177.6 | -133.9 | 28.6 | -89.5 | - | Y | - | - | deg | deg |
| C17|stop60-time60 | -43.7 | -1.0 | 108.2 | 2154.1 | -151.7 | -0.07 | 73.5 | n/a | -26.0 | 1752.4 | 64.4 | 84.2 | 167.5 | -75.5 | 30.2 | -99.7 | - | Y | - | - | deg | deg |
| C18|tgt60-time120 | -35.2 | -20.5 | 106.8 | 3862.4 | -180.1 | -1.38 | 48.1 | n/a | -45.4 | 3460.8 | 45.7 | 94.6 | 130.8 | -57.9 | 11.5 | -136.3 | - | Y | - | - | deg | deg |
| C18|tgt60-time30 | -80.6 | -51.2 | 87.9 | 7491.4 | -165.3 | -4.20 | 102.7 | n/a | -76.2 | 7089.7 | -1.0 | 84.4 | 259.5 | -134.7 | -35.2 | -7.7 | - | - | - | - | deg | deg |
| C18|tgt60-time60 | -53.8 | -35.1 | 100.6 | 5746.2 | -167.2 | -2.52 | 70.6 | n/a | -60.1 | 5344.6 | 67.3 | 115.8 | 224.8 | -136.0 | 33.1 | -42.4 | - | Y | - | - | deg | deg |
| C19|ratio0.9 | 11.6 | 25.4 | 111.8 | 382.3 | -137.0 | 1.64 | 39.5 | n/a | 0.5 | -19.3 | 54.3 | 126.6 | 360.0 | -134.7 | 20.0 | 92.8 | Y | - | - | - | deg | deg |
| C19|ratio1.1 | 9.1 | 30.2 | 98.9 | 382.9 | -135.6 | 2.20 | 34.0 | n/a | 5.2 | -18.7 | 25.0 | 102.7 | 290.3 | -105.0 | -9.2 | 23.2 | Y | - | - | - | deg | deg |

### Block D (25 cells; gate a 5, a+b 3, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D1|ES-30min-extreme | -55.5 | -20.2 | 99.0 | 4463.3 | -145.2 | -1.47 | 101.3 | n/a | -45.1 | 4061.7 | 56.8 | 111.9 | 161.0 | -135.0 | 22.6 | -106.2 | - | Y | - | - | deg | deg |
| D1|ES-60min-extreme | -40.8 | -5.7 | 107.0 | 2449.3 | -138.4 | -0.38 | 73.8 | n/a | -30.7 | 2047.7 | 30.5 | 114.0 | 261.1 | -135.8 | -3.7 | -6.0 | - | - | - | - | deg | deg |
| D2|5min-ST-flip | -16.8 | 9.4 | 104.8 | 1091.1 | -151.2 | 0.65 | 62.5 | n/a | -15.6 | 689.5 | 23.1 | 102.7 | 336.1 | -135.1 | -11.2 | 68.9 | - | - | - | - | deg | deg |
| D3|volspike3x-against | -40.7 | -17.2 | 102.3 | 3409.2 | -144.4 | -1.21 | 95.2 | n/a | -42.2 | 3007.6 | -10.2 | 95.9 | 337.8 | -135.9 | -44.4 | 70.7 | - | - | - | - | deg | deg |
| D3|volspike5x-against | -2.6 | 2.6 | 99.5 | 1195.5 | -143.5 | 0.19 | 60.5 | n/a | -22.4 | 793.9 | 10.1 | 78.8 | 207.5 | -134.5 | -24.1 | -59.6 | - | - | - | - | deg | deg |
| D4|vwap-cross-slope | -14.5 | 19.0 | 103.4 | 693.5 | -140.4 | 1.32 | 51.3 | n/a | -6.0 | 291.8 | 36.5 | 103.3 | 307.2 | -84.5 | 2.3 | 40.0 | - | - | - | - | deg | deg |
| D6|cap2.0R | 2.6 | 17.1 | 93.8 | 675.7 | -136.7 | 1.32 | 29.8 | 27.3 | -7.8 | 274.1 | 45.5 | 93.1 | 232.7 | -79.0 | 11.3 | -34.4 | - | Y | - | - | deg | deg |
| D6|cap3.0R | 10.4 | 19.8 | 92.7 | 602.2 | -137.1 | 1.54 | 32.2 | 17.1 | -5.2 | 200.5 | 37.8 | 103.6 | 267.1 | -90.4 | 3.6 | 0.0 | - | - | - | - | deg | deg |
| D6|cap4.0R | 14.8 | 20.6 | 97.4 | 600.6 | -137.1 | 1.53 | 33.4 | 11.4 | -4.4 | 199.0 | 49.3 | 107.4 | 267.1 | -90.4 | 15.1 | 0.0 | - | - | - | - | deg | deg |
| D7|RTY-diverge | -70.7 | -10.4 | 93.4 | 3620.2 | -151.8 | -0.81 | 143.6 | n/a | -35.4 | 3218.5 | 39.2 | 50.4 | 139.4 | -18.4 | 5.0 | -127.7 | - | Y | - | - | deg | deg |
| D7|YM-diverge | -70.4 | -23.1 | 94.4 | 4572.9 | -151.5 | -1.77 | 154.2 | n/a | -48.1 | 4171.3 | 16.1 | 64.7 | 168.1 | -101.7 | -18.1 | -99.0 | - | - | - | - | deg | deg |
| D9|exit-15min-before-release | 9.0 | 26.0 | 102.4 | 363.2 | -137.1 | 1.83 | 37.1 | n/a | 1.1 | -38.5 | 35.8 | 107.3 | 254.3 | -90.4 | 1.6 | -12.8 | Y | Y | - | - | deg | deg |
| D9|exit-5min-before-release | 6.8 | 27.5 | 104.7 | 346.7 | -137.1 | 1.89 | 37.0 | n/a | 2.5 | -54.9 | 34.2 | 109.5 | 267.6 | -99.4 | -0.1 | 0.5 | Y | - | - | - | deg | deg |
| D10|6J-shock | 5.8 | 12.6 | 108.0 | 870.2 | -137.2 | 0.84 | 51.5 | n/a | -12.4 | 468.5 | 68.8 | 89.6 | 258.3 | -68.2 | 34.5 | -8.9 | - | Y | - | - | deg | deg |
| D10|CL-shock | -8.1 | 12.6 | 101.8 | 627.9 | -136.7 | 0.89 | 47.7 | n/a | -12.4 | 226.2 | 20.2 | 92.4 | 215.1 | -115.4 | -14.0 | -52.1 | - | - | - | - | deg | deg |
| D10|ZN-shock | -7.4 | 13.4 | 101.0 | 645.0 | -135.9 | 0.95 | 49.3 | n/a | -11.6 | 243.3 | 19.8 | 116.0 | 350.6 | -135.1 | -14.4 | 83.5 | - | - | - | - | deg | deg |
| D11|ttl-3h/3h/2h | -4.2 | 19.5 | 100.9 | 1023.7 | -141.9 | 1.39 | 51.5 | n/a | -5.5 | 622.1 | 41.4 | 100.8 | 257.8 | -135.3 | 7.2 | -9.4 | - | Y | - | - | deg | deg |
| D12|exit-on-opposite-book-entry | 10.8 | 21.2 | 101.6 | 586.8 | -140.6 | 1.51 | 36.9 | n/a | -3.8 | 185.2 | 35.7 | 104.3 | 182.7 | -133.9 | 1.5 | -84.5 | - | Y | - | - | deg | deg |
| D15|rv15x2 | 2.8 | 26.5 | 102.6 | 480.1 | -135.9 | 1.86 | 43.0 | n/a | 1.6 | 78.5 | 43.6 | 100.6 | 224.2 | -134.6 | 9.4 | -42.9 | - | Y | - | - | deg | deg |
| D15|rv15x3 | -1.1 | 28.8 | 103.1 | 350.5 | -138.6 | 2.01 | 38.5 | n/a | 3.8 | -51.2 | 40.6 | 101.1 | 250.6 | -76.7 | 6.4 | -16.5 | Y | Y | - | - | deg | deg |
| D16|t30-stall-5minAgainst | -9.0 | 24.9 | 105.8 | 657.0 | -136.4 | 1.70 | 41.6 | n/a | -0.1 | 255.3 | 38.6 | 89.0 | 250.3 | -85.0 | 4.4 | -16.8 | - | Y | - | - | deg | deg |
| D16|t60-stall-5minAgainst | -7.7 | 27.2 | 96.3 | 366.7 | -136.2 | 2.03 | 42.8 | n/a | 2.2 | -34.9 | 38.4 | 100.0 | 177.8 | -84.3 | 4.2 | -89.3 | Y | Y | - | - | deg | deg |
| D17|tgt40-after-2stops | 10.9 | 20.4 | 106.3 | 555.5 | -139.9 | 1.38 | 36.9 | n/a | -4.6 | 153.9 | 26.4 | 118.8 | 324.2 | -134.5 | -7.8 | 57.1 | - | - | - | - | deg | deg |
| D18|exit-HM-when-ST-stopped | 11.4 | 29.2 | 102.8 | 387.0 | -140.0 | 2.05 | 36.6 | n/a | 4.2 | -14.7 | 21.1 | 117.5 | 377.8 | -134.9 | -13.1 | 110.6 | Y | - | - | - | deg | deg |
| D19|15min-ST-flip | -1.3 | 30.8 | 106.3 | 651.0 | -137.2 | 2.09 | 44.0 | n/a | 5.8 | 249.4 | 4.7 | 127.4 | 439.9 | -134.8 | -29.6 | 172.7 | - | - | - | - | deg | deg |

### Block E (41 cells; gate a 15, a+b 7, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E1|T26w | 12.4 | 26.4 | 106.3 | 486.3 | -143.1 | 1.79 | 35.4 | 103.2 | 1.4 | 84.6 | 39.4 | 117.9 | 279.0 | -107.5 | 5.2 | 11.8 | - | - | - | - | deg | deg |
| E1|T52w | 12.7 | 29.8 | 107.4 | 704.0 | -139.5 | 2.00 | 34.8 | 106.7 | 4.8 | 302.4 | 51.5 | 107.7 | 218.7 | -100.2 | 17.3 | -48.5 | - | Y | - | - | 0.85/0.06 | 0.90/0.07 |
| E2|hi20lo8 | 15.5 | 26.7 | 104.0 | 577.0 | -138.8 | 1.85 | 35.2 | 114.9 | 1.7 | 175.4 | 22.1 | 113.3 | 330.7 | -135.3 | -12.2 | 63.5 | - | - | - | - | 0.59/0.26 | 0.76/0.25 |
| E2|hi8lo20 | -0.5 | 21.8 | 110.4 | 502.3 | -153.9 | 1.42 | 34.5 | 115.7 | -3.2 | 100.7 | 28.2 | 138.4 | 347.6 | -134.9 | -6.0 | 80.4 | - | - | - | - | deg | deg |
| E4|second8 | 11.8 | 23.2 | 110.4 | 602.5 | -138.3 | 1.51 | 47.0 | 85.2 | -1.8 | 200.9 | 51.8 | 113.0 | 274.2 | -73.2 | 17.5 | 7.1 | - | - | - | - | 0.12/0.01 | 0.07/0.02 |
| E5|ES15m-agree14-else8 | 15.7 | 26.0 | 106.4 | 335.8 | -137.6 | 1.76 | 39.2 | 39.7 | 1.0 | -65.8 | 34.7 | 93.0 | 246.8 | -87.4 | 0.5 | -20.3 | Y | Y | - | - | 0.31/0.95 | 0.50/0.98 |
| E5|ES5m-agree14-else8 | 11.5 | 31.5 | 104.4 | 368.9 | -137.2 | 2.18 | 37.6 | 17.4 | 6.5 | -32.7 | 32.7 | 102.5 | 284.4 | -93.6 | -1.5 | 17.3 | Y | - | - | Y | 0.98/0.87 | 0.98/0.84 |
| E6|stops2->8 | 15.0 | 28.6 | 104.5 | 370.9 | -137.1 | 1.98 | 40.6 | 41.6 | 3.7 | -30.8 | 37.1 | 102.6 | 252.0 | -72.7 | 2.9 | -15.2 | Y | Y | - | - | 0.63/0.73 | 0.59/0.78 |
| E6|stops3->8 | 12.9 | 27.0 | 104.1 | 383.7 | -136.9 | 1.87 | 37.7 | 18.5 | 2.0 | -17.9 | 40.9 | 108.0 | 240.3 | -90.2 | 6.7 | -26.9 | Y | Y | - | - | 0.53/0.59 | 0.61/0.74 |
| E7|wr10<.4->8 only | 15.0 | 25.7 | 101.4 | 354.1 | -142.4 | 1.83 | 39.2 | 28.9 | 0.7 | -47.5 | 21.6 | 119.7 | 279.2 | -136.9 | -12.6 | 12.1 | Y | - | - | - | 0.37/0.88 | 0.44/0.93 |
| E7|wr10<.4->8,>.6->20 | 12.4 | 28.4 | 105.6 | 296.6 | -136.5 | 1.94 | 35.3 | 77.1 | 3.5 | -105.0 | 16.9 | 115.3 | 287.7 | -133.7 | -17.3 | 20.5 | Y | - | - | - | 0.75/0.99 | 0.76/1.00 |
| E11|ST10-HM10 | 11.6 | 25.4 | 102.9 | 362.4 | -149.6 | 1.78 | 51.1 | 157.9 | 0.4 | -39.2 | 36.0 | 100.6 | 259.4 | -91.8 | 1.8 | -7.8 | Y | Y | - | - | deg | deg |
| E11|ST10-HM14 | 12.4 | 24.7 | 105.5 | 490.0 | -137.4 | 1.69 | 43.8 | 85.7 | -0.3 | 88.4 | 46.7 | 79.9 | 212.7 | -92.9 | 12.5 | -54.4 | - | Y | - | - | deg | deg |
| E11|ST10-HM20 | 10.0 | 23.3 | 113.0 | 481.8 | -139.4 | 1.48 | 35.8 | 157.9 | -1.7 | 80.1 | 46.5 | 135.7 | 284.3 | -135.1 | 12.3 | 17.1 | - | - | - | - | deg | deg |
| E11|ST10-HM8 | 7.8 | 28.3 | 96.7 | 386.8 | -136.9 | 2.11 | 55.4 | 157.9 | 3.3 | -14.9 | 47.4 | 117.1 | 284.4 | -120.5 | 13.2 | 17.2 | Y | - | - | - | deg | deg |
| E11|ST14-HM10 | 11.4 | 30.7 | 102.1 | 368.4 | -136.1 | 2.17 | 41.7 | 76.7 | 5.8 | -33.2 | 45.1 | 89.7 | 248.8 | -98.4 | 10.9 | -18.4 | Y | Y | - | - | deg | deg |
| E11|ST14-HM14 | 13.7 | 25.0 | 104.5 | 401.6 | -137.1 | 1.72 | 35.9 | 0.0 | 0.0 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| E11|ST14-HM20 | 19.2 | 23.5 | 112.4 | 380.6 | -142.4 | 1.51 | 30.3 | 88.2 | -1.5 | -21.0 | 35.7 | 147.6 | 380.6 | -136.5 | 1.5 | 113.5 | - | - | - | - | deg | deg |
| E11|ST14-HM8 | 8.1 | 31.0 | 101.6 | 332.3 | -136.4 | 2.20 | 44.6 | 77.4 | 6.0 | -69.4 | 61.7 | 110.8 | 233.4 | -97.9 | 27.5 | -33.7 | Y | Y | - | - | deg | deg |
| E11|ST20-HM10 | 14.3 | 21.3 | 100.9 | 480.7 | -144.3 | 1.52 | 32.1 | 157.9 | -3.7 | 79.0 | 19.0 | 102.8 | 247.0 | -134.5 | -15.3 | -20.1 | - | - | - | - | deg | deg |
| E11|ST20-HM14 | 14.0 | 20.4 | 111.1 | 499.6 | -138.3 | 1.32 | 28.6 | 94.9 | -4.6 | 98.0 | 27.8 | 110.6 | 241.3 | -134.3 | -6.4 | -25.8 | - | - | - | - | deg | deg |
| E11|ST20-HM20 | 13.3 | 23.7 | 105.9 | 524.0 | -144.3 | 1.61 | 24.8 | 157.9 | -1.3 | 122.4 | 31.3 | 122.4 | 266.4 | -135.0 | -2.9 | -0.8 | - | - | - | - | deg | deg |
| E11|ST20-HM8 | 11.6 | 23.6 | 104.9 | 567.1 | -138.4 | 1.62 | 35.2 | 157.9 | -1.3 | 165.5 | 24.4 | 143.0 | 240.0 | -134.7 | -9.8 | -27.1 | - | - | - | - | deg | deg |
| E11|ST8-HM10 | 11.7 | 27.2 | 93.4 | 414.7 | -135.5 | 2.10 | 56.6 | 157.9 | 2.2 | 13.1 | 33.0 | 106.9 | 299.8 | -114.5 | -1.3 | 32.6 | - | - | - | - | deg | deg |
| E11|ST8-HM14 | 9.8 | 23.2 | 106.3 | 497.1 | -138.7 | 1.57 | 48.3 | 85.9 | -1.8 | 95.5 | 47.8 | 82.4 | 208.6 | -87.0 | 13.6 | -58.5 | - | Y | - | - | deg | deg |
| E11|ST8-HM20 | 5.5 | 22.1 | 110.2 | 526.8 | -137.2 | 1.45 | 39.3 | 157.9 | -2.8 | 125.1 | 26.6 | 117.2 | 322.2 | -135.0 | -7.6 | 55.0 | - | - | - | - | deg | deg |
| E11|ST8-HM8 | 3.6 | 28.3 | 86.3 | 376.6 | -137.1 | 2.36 | 61.3 | 157.9 | 3.3 | -25.1 | 41.9 | 111.5 | 274.9 | -122.4 | 7.6 | 7.7 | Y | - | - | - | deg | deg |
| E11|WF-chosen | 13.7 | 20.0 | 98.8 | 432.8 | -173.1 | 1.46 | nan | n/a | -4.9 | 31.2 | 47.4 | 117.1 | 284.4 | -120.5 | 13.2 | 17.2 | - | - | - | - | deg | deg |
| E12|first30min->8 | 20.4 | 26.7 | 104.0 | 583.0 | -137.6 | 1.85 | 39.0 | 28.6 | 1.7 | 181.4 | 55.9 | 114.9 | 177.0 | -90.8 | 21.7 | -90.1 | - | Y | - | - | 0.58/0.11 | 0.56/0.02 |
| E12|first60min->8 | 14.2 | 25.8 | 103.4 | 500.9 | -136.6 | 1.80 | 40.9 | 47.1 | 0.9 | 99.3 | 46.3 | 96.5 | 185.2 | -91.3 | 12.1 | -82.0 | - | Y | - | - | deg | deg |
| E13|neg->8 | 5.3 | 28.7 | 96.9 | 311.0 | -143.6 | 2.14 | 44.5 | 49.3 | 3.7 | -90.6 | 26.5 | 102.0 | 311.0 | -98.6 | -7.8 | 43.9 | Y | - | - | - | 0.81/0.98 | 0.62/0.99 |
| E13|neg->8,pos->20 | 8.3 | 24.7 | 102.3 | 442.1 | -138.3 | 1.74 | 35.5 | 154.0 | -0.3 | 40.5 | 26.9 | 113.3 | 356.4 | -134.8 | -7.4 | 89.3 | - | - | - | - | deg | deg |
| E14|extended->8 | 7.0 | 28.7 | 101.8 | 343.6 | -136.0 | 2.03 | 43.5 | 56.4 | 3.7 | -58.0 | 29.8 | 115.6 | 276.8 | -105.2 | -4.4 | 9.6 | Y | - | - | - | 0.54/0.77 | 0.63/0.92 |
| E14|near->20 | 14.4 | 24.3 | 107.7 | 397.4 | -139.6 | 1.63 | 30.5 | 73.7 | -0.6 | -4.2 | 28.4 | 120.2 | 351.9 | -134.2 | -5.8 | 84.7 | - | - | - | - | deg | deg |
| E15|3rd+->10 | 10.3 | 28.7 | 104.8 | 337.9 | -137.7 | 1.97 | 47.6 | 125.5 | 3.7 | -63.7 | 28.0 | 105.1 | 269.4 | -82.2 | -6.2 | 2.3 | Y | - | - | - | 0.49/0.65 | 0.75/0.97 |
| E15|3rd+->8 | 4.8 | 23.8 | 95.6 | 411.2 | -138.5 | 1.80 | 54.1 | 125.4 | -1.1 | 9.6 | 11.7 | 116.6 | 339.3 | -134.5 | -22.5 | 72.2 | - | - | - | - | deg | deg |
| E17|cap20k | 9.0 | 19.1 | 89.5 | 388.0 | -135.4 | 1.54 | 55.9 | 87.3 | -5.8 | -13.6 | 65.9 | 121.7 | 286.7 | -74.1 | 31.7 | 19.5 | - | - | - | - | deg | deg |
| E17|cap25k | 13.3 | 22.6 | 104.7 | 358.8 | -136.9 | 1.56 | 50.8 | 86.7 | -2.4 | -42.9 | 67.6 | 131.5 | 264.0 | -84.7 | 33.4 | -3.1 | - | Y | - | - | deg | deg |
| E17|cap30k | 14.2 | 30.8 | 108.3 | 344.0 | -137.8 | 2.05 | 42.1 | 84.5 | 5.8 | -57.6 | 41.1 | 87.6 | 240.7 | -90.6 | 6.9 | -26.4 | Y | Y | - | - | 0.67/0.92 | 0.64/0.91 |
| E19|clip[0.5,1.5] | 14.3 | 24.1 | 101.7 | 366.0 | -136.8 | 1.71 | 38.9 | 157.9 | -0.9 | -35.6 | 40.8 | 117.4 | 340.2 | -134.6 | 6.6 | 73.0 | - | - | - | - | 0.32/0.76 | 0.17/0.78 |
| E19|clip[0.6,1.5] | 14.3 | 24.1 | 101.7 | 366.0 | -136.8 | 1.71 | 38.9 | 157.9 | -0.9 | -35.6 | 40.8 | 117.4 | 340.2 | -134.6 | 6.6 | 73.0 | - | - | - | - | deg | deg |

### Block F (38 cells; gate a 4, a+b 2, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1|add|arm1.0 | 8.3 | 16.0 | 88.1 | 473.4 | -137.0 | 1.31 | 30.2 | 33.6 | -9.0 | 71.7 | 29.7 | 79.7 | 129.7 | -104.7 | -4.6 | -137.4 | - | - | - | - | deg | deg |
| F1|add|arm1.5 | 12.3 | 23.2 | 95.1 | 485.1 | -137.1 | 1.76 | 33.5 | 16.1 | -1.8 | 83.5 | 42.7 | 97.2 | 154.3 | -111.9 | 8.5 | -112.9 | - | Y | - | - | deg | deg |
| F1|replace|arm1.0 | 8.3 | 17.7 | 93.4 | 480.0 | -137.0 | 1.36 | 31.1 | 34.2 | -7.3 | 78.4 | 30.4 | 77.4 | 129.7 | -96.9 | -3.8 | -137.4 | - | - | - | - | deg | deg |
| F1|replace|arm1.5 | 8.2 | 27.5 | 115.3 | 670.5 | -136.7 | 1.72 | 39.5 | 18.6 | 2.5 | 268.9 | 57.8 | 123.0 | 255.2 | -65.1 | 23.6 | -11.9 | - | Y | - | - | deg | deg |
| F1|replace|arm2.0 | 7.2 | 29.6 | 124.1 | 719.9 | -136.7 | 1.72 | 45.0 | 12.1 | 4.6 | 318.3 | 46.6 | 160.1 | 462.8 | -135.1 | 12.4 | 195.7 | - | - | - | - | deg | deg |
| F1|replace|arm3.0 | 2.2 | 38.7 | 134.2 | 661.5 | -136.7 | 2.08 | 51.7 | 8.7 | 13.8 | 259.8 | 80.6 | 187.4 | 515.2 | -135.1 | 46.4 | 248.0 | - | - | - | - | 0.80/0.80 | deg |
| F2|HMonly|arm2.0 | 5.7 | 30.7 | 131.0 | 854.0 | -144.5 | 1.69 | 51.0 | 9.6 | 5.7 | 452.4 | 50.1 | 160.0 | 461.0 | -135.1 | 15.9 | 193.9 | - | - | - | - | deg | deg |
| F2|HMonly|arm3.0 | 2.0 | 37.8 | 136.4 | 641.4 | -136.7 | 2.00 | 53.6 | 7.5 | 12.8 | 239.7 | 72.5 | 190.3 | 515.2 | -135.1 | 38.3 | 248.0 | - | - | - | - | deg | deg |
| F2|STonly|arm2.0 | 2.7 | 38.0 | 126.4 | 636.8 | -136.7 | 2.17 | 48.9 | 9.8 | 13.0 | 235.1 | 58.3 | 176.9 | 500.2 | -135.1 | 24.1 | 233.1 | - | - | - | Y | deg | deg |
| F2|STonly|arm3.0 | 1.5 | 40.9 | 134.2 | 641.2 | -136.7 | 2.20 | 52.6 | 8.9 | 15.9 | 239.6 | 76.8 | 184.1 | 498.4 | -135.1 | 42.6 | 231.3 | - | - | - | Y | 0.90/0.87 | deg |
| F4|tdd2.0h | -2.0 | 7.4 | 60.4 | 328.5 | -136.6 | 0.89 | 15.9 | 91.9 | -17.5 | -73.1 | -2.5 | 78.1 | 257.9 | -102.1 | -36.7 | -9.2 | - | - | - | - | deg | deg |
| F4|tdd4.0h | -0.2 | 14.5 | 78.6 | 357.4 | -135.1 | 1.33 | 20.8 | 72.3 | -10.5 | -44.2 | 20.5 | 112.3 | 251.6 | -134.7 | -13.7 | -15.5 | - | - | - | - | 0.39/0.89 | deg |
| F5|pnlvol0.2 | 13.5 | 15.5 | 84.9 | 375.5 | -136.0 | 1.31 | 29.6 | 59.4 | -9.5 | -26.1 | -0.1 | 118.7 | 363.5 | -135.1 | -34.3 | 96.3 | - | - | - | - | deg | deg |
| F5|pnlvol0.3 | 15.7 | 19.3 | 99.3 | 424.7 | -136.7 | 1.40 | 33.0 | 30.5 | -5.6 | 23.0 | -4.0 | 121.6 | 291.3 | -134.2 | -38.2 | 24.2 | - | - | - | - | 0.40/0.97 | deg |
| F7|wktrail10.0R | 15.4 | 25.6 | 104.0 | 370.5 | -168.1 | 1.77 | 36.3 | 2.4 | 0.6 | -31.1 | 38.9 | 103.5 | 229.5 | -90.4 | 4.7 | -37.6 | Y | Y | - | - | 0.54/1.00 | deg |
| F7|wktrail6.0R | 6.7 | 20.6 | 93.5 | 437.5 | -103.6 | 1.59 | 27.2 | 38.5 | -4.4 | 35.8 | 32.1 | 104.0 | 212.9 | -81.6 | -2.1 | -54.2 | - | - | - | - | deg | deg |
| F7|wktrail8.0R | 11.9 | 22.6 | 99.9 | 426.8 | -134.2 | 1.63 | 32.4 | 15.4 | -2.4 | 25.2 | 38.6 | 104.2 | 248.4 | -87.9 | 4.4 | -18.8 | - | Y | - | - | deg | deg |
| F8|month12.0R | 10.9 | 22.4 | 103.4 | 565.9 | -137.1 | 1.56 | 34.8 | 4.8 | -2.5 | 164.3 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| F8|month16.0R | 8.4 | 24.7 | 104.8 | 401.6 | -137.1 | 1.70 | 35.7 | 1.0 | -0.3 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| F8|month20.0R | 13.7 | 25.0 | 104.5 | 401.6 | -137.1 | 1.72 | 35.9 | 0.0 | 0.0 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | 0.30/1.00 | deg |
| F10|balance-scaled | 18.5 | 40.4 | 133.2 | 514.9 | -204.9 | 2.19 | 47.7 | 0.2 | 15.5 | 113.3 | 59.0 | 148.9 | 420.6 | -127.7 | 24.8 | 153.5 | - | - | - | Y | 0.93/0.97 | deg |
| F11|perside-2/2 | 11.8 | 17.9 | 108.6 | 447.6 | -149.4 | 1.19 | 34.7 | 26.0 | -7.1 | 45.9 | -27.8 | 144.9 | 447.6 | -136.1 | -62.0 | 180.4 | - | - | - | - | deg | deg |
| F11|perside-L2.5/S1.5 | 15.6 | 21.1 | 109.4 | 448.3 | -149.4 | 1.39 | 35.0 | 26.3 | -3.9 | 46.7 | -30.0 | 146.6 | 448.3 | -135.3 | -64.2 | 181.2 | - | - | - | - | 0.14/0.99 | deg |
| F12|nextsession | -3.3 | 40.9 | 135.6 | 680.2 | -136.9 | 2.17 | 46.3 | 26.4 | 15.9 | 278.6 | 65.7 | 144.0 | 292.4 | -134.4 | 31.4 | 25.3 | - | - | - | Y | 1.00/0.00 | deg |
| F13|cooldown1.0h/R | 13.1 | 22.5 | 104.0 | 408.0 | -137.4 | 1.56 | 44.9 | 0.0 | -2.5 | 6.4 | 29.9 | 107.9 | 272.6 | -102.9 | -4.3 | 5.5 | - | - | - | - | deg | deg |
| F13|cooldown2.0h/R | 12.2 | 23.3 | 104.4 | 407.7 | -137.1 | 1.61 | 41.0 | 0.0 | -1.6 | 6.1 | 32.0 | 108.6 | 271.1 | -100.2 | -2.3 | 4.0 | - | - | - | - | 0.80/0.93 | deg |
| F14|strike1-1h | 2.0 | 16.9 | 68.6 | 297.5 | -136.7 | 1.77 | 14.6 | 97.4 | -8.1 | -104.1 | 40.1 | 50.6 | 35.0 | -12.6 | 5.9 | -232.1 | - | Y | - | - | 0.12/1.00 | deg |
| F14|strike1-sess | -0.1 | 16.4 | 76.1 | 503.1 | -137.1 | 1.55 | 17.3 | 84.7 | -8.6 | 101.4 | 40.5 | 50.8 | 35.0 | -12.6 | 6.3 | -232.1 | - | Y | - | - | deg | deg |
| F15|events-nolocks | 8.3 | 25.3 | 112.8 | 419.9 | -158.6 | 1.62 | 39.8 | 0.0 | 0.3 | 18.3 | 27.7 | 148.8 | 363.1 | -131.1 | -6.5 | 95.9 | - | - | - | - | 0.26/1.00 | deg |
| F15|events-nolocks+nopb | 7.0 | 21.8 | 119.6 | 675.2 | -181.9 | 1.31 | 43.6 | 2.0 | -3.2 | 273.5 | 25.0 | 160.7 | 431.8 | -155.0 | -9.2 | 164.7 | - | - | - | - | deg | deg |
| F16|fri-arm1-cap4 | 6.5 | 22.1 | 98.6 | 367.8 | -137.1 | 1.61 | 33.6 | 10.3 | -2.9 | -33.9 | 37.6 | 87.6 | 167.9 | -90.4 | 3.4 | -99.3 | - | Y | - | - | deg | deg |
| F16|fri-arm1.5-cap6 | 11.9 | 25.8 | 99.8 | 359.0 | -137.1 | 1.86 | 34.5 | 6.3 | 0.8 | -42.6 | 42.1 | 93.3 | 162.7 | -90.4 | 7.9 | -104.4 | Y | Y | - | - | 0.46/1.00 | deg |
| F17|onepos | 4.5 | 17.5 | 92.7 | 450.3 | -136.3 | 1.36 | 34.4 | 61.8 | -7.4 | 48.7 | 24.5 | 113.9 | 354.1 | -134.6 | -9.7 | 87.0 | - | - | - | - | 0.01/1.00 | deg |
| F18|unreal0.5R | 16.1 | 23.2 | 103.2 | 387.6 | -139.7 | 1.62 | 34.7 | 8.5 | -1.7 | -14.0 | 42.1 | 98.4 | 178.7 | -90.4 | 7.9 | -88.4 | - | Y | - | - | deg | deg |
| F18|unreal0.75R | 16.0 | 24.8 | 104.2 | 366.3 | -137.1 | 1.71 | 35.9 | 2.7 | -0.2 | -35.3 | 33.8 | 107.7 | 254.1 | -98.9 | -0.5 | -13.1 | - | - | - | - | deg | deg |
| F18|unreal1.0R | 13.7 | 25.0 | 104.5 | 401.6 | -137.1 | 1.72 | 35.9 | 0.0 | 0.0 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | 0.30/1.00 | deg |
| F19|slip0.75 | 8.2 | 30.9 | 103.5 | 366.5 | -137.7 | 2.15 | 34.8 | 26.4 | 5.9 | -35.2 | 41.0 | 137.7 | 308.7 | -117.4 | 6.8 | 41.6 | Y | - | - | - | 0.60/1.00 | deg |
| F19|slip1.5 | 12.9 | 29.0 | 104.5 | 366.5 | -137.7 | 2.00 | 34.7 | 21.2 | 4.0 | -35.2 | 24.6 | 133.2 | 325.3 | -117.4 | -9.7 | 58.1 | Y | - | - | - | 0.47/1.00 | deg |

### Block G (16 cells; gate a 4, a+b 0, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| G1|skip-18:05-21:00 | 10.5 | 17.6 | 99.8 | 813.2 | -137.2 | 1.28 | 33.3 | 68.7 | -7.3 | 411.5 | 50.6 | 115.6 | 321.4 | -134.3 | 16.4 | 54.3 | - | - | - | - | deg | deg |
| G1|skip-21:00-02:00 | 13.6 | 18.5 | 104.0 | 599.2 | -144.0 | 1.28 | 34.9 | 42.5 | -6.5 | 197.5 | 57.3 | 118.4 | 204.4 | -90.1 | 23.1 | -62.8 | - | Y | - | - | 0.11/0.09 | 0.05/0.04 |
| G2|skip-02:00-04:00 | 5.5 | 26.2 | 108.5 | 506.0 | -137.9 | 1.74 | 36.0 | 19.8 | 1.2 | 104.4 | 41.7 | 113.0 | 253.0 | -94.6 | 7.5 | -14.1 | - | Y | - | - | deg | deg |
| G2|skip-04:00-09:30 | 1.1 | 28.7 | 105.3 | 436.3 | -139.9 | 1.96 | 34.2 | 35.5 | 3.7 | 34.6 | 9.4 | 114.7 | 312.1 | -135.2 | -24.8 | 45.0 | - | - | - | - | 0.89/0.58 | 0.89/0.80 |
| G3|skip-09:30-11:30 | 16.7 | 27.5 | 101.4 | 388.9 | -147.5 | 1.96 | 33.3 | 23.8 | 2.6 | -12.7 | 33.5 | 99.4 | 220.1 | -104.6 | -0.8 | -47.0 | Y | - | - | - | 0.87/0.77 | 0.76/0.96 |
| G3|skip-11:30-14:00 | 11.8 | 23.6 | 99.4 | 446.7 | -143.3 | 1.71 | 33.9 | 12.2 | -1.4 | 45.1 | 42.4 | 110.1 | 263.6 | -98.9 | 8.2 | -3.5 | - | Y | - | - | deg | deg |
| G3|skip-14:00-15:00 | 11.7 | 25.7 | 103.0 | 380.4 | -137.1 | 1.80 | 35.5 | 3.2 | 0.7 | -21.2 | 32.3 | 114.2 | 283.9 | -98.9 | -1.9 | 16.7 | Y | - | - | - | 0.65/0.89 | 0.54/0.76 |
| G4|skip-lunch12-13:30 | 12.7 | 26.5 | 100.6 | 385.7 | -139.1 | 1.90 | 35.1 | 6.3 | 1.5 | -15.9 | 38.0 | 114.4 | 270.3 | -98.9 | 3.8 | 3.2 | Y | - | - | - | 0.75/0.72 | 0.69/0.81 |
| G5|skip-20-21 | 12.8 | 20.3 | 100.5 | 451.0 | -137.1 | 1.46 | 35.4 | 26.7 | -4.7 | 49.4 | 28.4 | 113.5 | 451.0 | -135.2 | -5.9 | 183.9 | - | - | - | - | 0.11/0.56 | 0.08/0.31 |
| G6|only-03-05+09:30-11:30 | 1.4 | 16.9 | 84.4 | 513.4 | -145.9 | 1.44 | 21.3 | 124.2 | -8.1 | 111.8 | 33.5 | 114.0 | 176.5 | -102.0 | -0.7 | -90.6 | - | - | - | - | 0.90/0.64 | 0.88/0.59 |
| G7|flatten-16:00 | 13.6 | 25.6 | 103.8 | 440.3 | -136.7 | 1.78 | 36.2 | n/a | 0.7 | 38.7 | 34.5 | 108.4 | 268.0 | -98.9 | 0.3 | 0.8 | - | - | - | - | deg | deg |
| G9x|no-entries-after-13:00 | 9.6 | 24.9 | 103.6 | 435.5 | -136.8 | 1.73 | 34.7 | 7.3 | -0.1 | 33.8 | 35.8 | 121.2 | 283.9 | -98.9 | 1.5 | 16.7 | - | - | - | - | deg | deg |
| G9x|no-entries-after-14:00 | 11.7 | 25.7 | 103.0 | 380.4 | -137.1 | 1.80 | 35.5 | 3.2 | 0.7 | -21.2 | 32.3 | 114.2 | 283.9 | -98.9 | -1.9 | 16.7 | Y | - | - | - | 0.65/0.89 | 0.54/0.76 |
| G15|sess-on-if-trail26w>0 | -0.0 | 23.2 | 107.3 | 470.9 | -138.5 | 1.56 | 34.2 | 19.5 | -1.8 | 69.3 | 29.4 | 158.7 | 436.7 | -138.5 | -4.8 | 169.5 | - | - | - | - | deg | deg |
| G15|sess-on-if-trail52w>0 | -7.8 | 27.2 | 104.3 | 458.8 | -137.1 | 1.88 | 34.9 | 17.4 | 2.2 | 57.2 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | 0.99/0.39 | 0.77/0.55 |
| G20|skip-DST-weeks | 11.4 | 19.7 | 101.2 | 425.9 | -137.1 | 1.41 | 33.0 | 13.0 | -5.2 | 24.3 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | 0.04/0.23 | 0.05/0.56 |

### Block H (37 cells; gate a 6, a+b 3, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H2|rv20/VXN|size8_hi | 7.2 | 26.4 | 95.3 | 318.3 | -137.1 | 2.00 | 48.8 | 77.7 | 1.5 | -83.4 | 29.5 | 116.1 | 286.6 | -133.3 | -4.7 | 19.5 | Y | - | - | - | 0.46/0.90 | 0.43/0.98 |
| H2|rv20/VXN|skip_hi | 6.7 | 18.3 | 78.9 | 263.3 | -137.0 | 1.67 | 18.5 | 77.7 | -6.7 | -138.3 | 33.7 | 108.8 | 188.4 | -90.4 | -0.5 | -78.8 | - | - | - | - | deg | deg |
| H2|rv20/VXN|skip_lo | 7.7 | 16.8 | 96.3 | 438.5 | -137.1 | 1.26 | 28.9 | 30.7 | -8.2 | 36.8 | 11.2 | 75.8 | 267.1 | -98.9 | -23.0 | 0.0 | - | - | - | - | deg | deg |
| H3|dVIX1|size8_hi | 14.4 | 24.8 | 96.1 | 485.0 | -137.6 | 1.86 | 46.1 | 51.4 | -0.1 | 83.3 | 33.0 | 97.7 | 218.9 | -90.4 | -1.2 | -48.3 | - | - | - | - | 0.26/0.15 | 0.25/0.30 |
| H3|dVIX1|skip_hi | 21.8 | 16.0 | 82.6 | 413.0 | -136.2 | 1.40 | 25.1 | 52.3 | -9.0 | 11.4 | 14.3 | 96.5 | 219.6 | -115.4 | -19.9 | -47.5 | - | - | - | - | deg | deg |
| H3|dVIX1|skip_lo | -0.7 | 20.1 | 90.4 | 393.3 | -154.2 | 1.60 | 22.8 | 61.5 | -4.9 | -8.3 | 14.8 | 83.3 | 164.8 | -126.8 | -19.4 | -102.4 | - | - | - | - | deg | deg |
| H6|on/rth-RV|size8_hi | 10.8 | 25.1 | 101.1 | 501.1 | -138.6 | 1.79 | 48.6 | 77.8 | 0.2 | 99.4 | 43.8 | 126.9 | 288.1 | -138.6 | 9.6 | 21.0 | - | - | - | - | 0.22/0.07 | 0.24/0.17 |
| H6|on/rth-RV|skip_hi | 10.8 | 14.3 | 79.7 | 438.2 | -139.0 | 1.29 | 19.0 | 78.4 | -10.7 | 36.6 | -0.3 | 64.1 | 100.3 | -100.3 | -34.5 | -166.8 | - | - | - | - | deg | deg |
| H6|on/rth-RV|skip_lo | 8.7 | 16.7 | 87.5 | 512.4 | -137.0 | 1.37 | 28.3 | 36.0 | -8.3 | 110.7 | 29.2 | 109.6 | 288.7 | -98.9 | -5.0 | 21.6 | - | - | - | - | deg | deg |
| H7|only-falling | 3.1 | 15.0 | 77.1 | 411.6 | -137.6 | 1.40 | 17.8 | 80.6 | -10.0 | 10.0 | 41.1 | 89.5 | 181.6 | -98.9 | 6.9 | -85.5 | - | Y | - | - | 0.72/0.54 | 0.51/0.91 |
| H7|only-rising | 6.6 | 12.0 | 73.4 | 282.1 | -136.3 | 1.18 | 18.7 | 77.5 | -13.0 | -119.6 | -6.9 | 63.4 | 195.8 | -90.4 | -41.1 | -71.3 | - | - | - | - | deg | deg |
| H8|cc/parkinson|size8_hi | 7.6 | 29.4 | 97.3 | 323.6 | -138.6 | 2.18 | 46.3 | 55.4 | 4.4 | -78.0 | 28.9 | 117.2 | 292.0 | -138.6 | -5.3 | 24.8 | Y | - | - | - | 0.83/0.86 | 0.68/0.94 |
| H8|cc/parkinson|skip_hi | 1.7 | 23.7 | 87.1 | 295.0 | -137.0 | 1.96 | 23.8 | 55.2 | -1.3 | -106.7 | 31.3 | 111.9 | 207.4 | -100.3 | -2.9 | -59.7 | - | - | - | - | deg | deg |
| H8|cc/parkinson|skip_lo | 7.7 | 8.3 | 81.4 | 607.2 | -137.2 | 0.74 | 22.2 | 60.5 | -16.6 | 205.5 | 19.1 | 56.4 | 181.6 | -98.9 | -15.1 | -85.5 | - | - | - | - | deg | deg |
| H9|volvol|size8_hi | 13.5 | 26.5 | 99.3 | 382.3 | -137.0 | 1.92 | 45.8 | 58.3 | 1.5 | -19.4 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | Y | - | - | - | 0.50/0.49 | 0.47/0.72 |
| H9|volvol|skip_hi | 6.4 | 16.4 | 83.7 | 407.8 | -137.0 | 1.41 | 23.2 | 58.6 | -8.6 | 6.1 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| H9|volvol|skip_lo | 9.1 | 16.4 | 89.3 | 362.5 | -137.6 | 1.32 | 24.3 | 51.5 | -8.6 | -39.2 | 10.3 | 29.2 | 0.0 | 0.0 | -23.9 | -267.1 | - | - | - | - | deg | deg |
| H10|hurst|only_mid | 1.3 | 7.8 | 63.7 | 585.8 | -135.1 | 0.88 | 12.5 | 105.4 | -17.2 | 184.1 | -1.6 | 55.9 | 179.4 | -83.8 | -35.9 | -87.7 | - | - | - | - | deg | deg |
| H10|hurst|skip_hi | 13.5 | 19.5 | 90.4 | 435.4 | -136.7 | 1.56 | 25.7 | 48.4 | -5.4 | 33.8 | 8.6 | 82.8 | 239.2 | -98.9 | -25.6 | -28.0 | - | - | - | - | 0.65/0.44 | 0.42/0.86 |
| H10|hurst|skip_lo | 1.9 | 14.1 | 85.6 | 612.4 | -135.3 | 1.19 | 23.3 | 57.4 | -10.9 | 210.7 | 24.0 | 90.3 | 192.1 | -83.8 | -10.2 | -75.0 | - | - | - | - | deg | deg |
| H11|VR5|only_mid | 1.0 | 3.8 | 61.0 | 626.5 | -137.4 | 0.45 | 11.5 | 110.5 | -21.2 | 224.9 | 20.1 | 31.5 | 50.3 | 0.0 | -14.1 | -216.8 | - | - | - | - | deg | deg |
| H11|VR5|skip_hi | 4.6 | 12.9 | 88.1 | 667.3 | -138.4 | 1.06 | 24.3 | 53.5 | -12.1 | 265.7 | 33.9 | 93.6 | 267.1 | -98.9 | -0.3 | 0.0 | - | - | - | - | deg | deg |
| H11|VR5|skip_lo | 10.1 | 16.2 | 85.1 | 473.2 | -137.4 | 1.37 | 23.5 | 57.1 | -8.8 | 71.6 | 20.4 | 65.0 | 134.6 | -90.4 | -13.8 | -132.5 | - | - | - | - | 0.63/0.26 | 0.20/0.73 |
| H12|ST-on-if-ac>0 | 3.1 | 13.4 | 91.4 | 464.5 | -142.2 | 1.06 | 29.2 | 50.2 | -11.6 | 62.9 | 11.1 | 63.6 | 219.2 | -88.2 | -23.1 | -47.9 | - | - | - | - | 0.02/0.36 | 0.08/0.65 |
| H12|both-on-if-ac>0 | 8.2 | 6.8 | 68.0 | 451.1 | -137.1 | 0.72 | 15.4 | 91.3 | -18.2 | 49.4 | 7.5 | 21.2 | 0.0 | 0.0 | -26.7 | -267.1 | - | - | - | - | deg | deg |
| H16|zigzag60|size8_hi | 6.5 | 30.3 | 97.3 | 316.4 | -137.1 | 2.24 | 50.6 | 79.6 | 5.3 | -85.2 | 43.9 | 87.4 | 209.5 | -47.0 | 9.7 | -57.6 | Y | Y | - | - | 0.87/0.92 | 0.81/0.99 |
| H16|zigzag60|skip_hi | 10.5 | 17.8 | 78.6 | 281.5 | -138.1 | 1.64 | 17.8 | 80.4 | -7.2 | -120.1 | 57.2 | 65.2 | 97.8 | -10.8 | 23.0 | -169.3 | - | Y | - | - | deg | deg |
| H16|zigzag60|skip_lo | 10.8 | 24.7 | 96.8 | 501.8 | -135.7 | 1.84 | 29.4 | 31.2 | -0.3 | 100.1 | 35.4 | 98.8 | 289.5 | -98.9 | 1.2 | 22.3 | - | - | - | - | deg | deg |
| H17|garch/rv5|size8_hi | 9.3 | 23.3 | 99.9 | 424.2 | -137.1 | 1.68 | 41.4 | 38.2 | -1.6 | 22.6 | 36.4 | 112.3 | 267.1 | -98.9 | 2.2 | 0.0 | - | - | - | - | 0.13/0.19 | 0.27/0.57 |
| H17|garch/rv5|skip_hi | 5.6 | 18.7 | 91.8 | 501.5 | -137.1 | 1.47 | 27.4 | 38.2 | -6.3 | 99.9 | 20.6 | 97.0 | 267.1 | -98.9 | -13.6 | 0.0 | - | - | - | - | deg | deg |
| H17|garch/rv5|skip_lo | 15.1 | 12.3 | 82.2 | 333.6 | -137.1 | 1.08 | 22.2 | 61.9 | -12.7 | -68.0 | 17.5 | 107.4 | 198.2 | -134.6 | -16.7 | -69.0 | - | - | - | - | deg | deg |
| H19|volfrac|size8_hi | 7.8 | 28.0 | 101.3 | 335.9 | -137.6 | 1.99 | 40.2 | 23.1 | 3.0 | -65.8 | 45.8 | 95.5 | 201.0 | -98.9 | 11.6 | -66.1 | Y | Y | - | - | 0.74/0.91 | 0.65/0.93 |
| H19|volfrac|skip_hi | 5.8 | 20.6 | 101.1 | 569.6 | -137.1 | 1.47 | 31.0 | 23.5 | -4.4 | 167.9 | 51.2 | 83.6 | 182.0 | -98.9 | 17.0 | -85.2 | - | Y | - | - | deg | deg |
| H19|volfrac|skip_lo | 7.9 | 12.3 | 68.1 | 311.0 | -154.2 | 1.30 | 15.2 | 95.2 | -12.7 | -90.6 | 7.8 | 79.1 | 134.6 | -109.4 | -26.5 | -132.5 | - | - | - | - | deg | deg |
| H20|printed-sec/30min|size8_hi | 13.9 | 28.3 | 102.7 | 398.8 | -135.8 | 1.99 | 37.5 | 21.9 | 3.3 | -2.8 | 36.7 | 109.5 | 265.7 | -108.2 | 2.5 | -1.4 | Y | Y | - | - | 0.75/0.51 | 0.70/0.73 |
| H20|printed-sec/30min|skip_hi | 18.6 | 25.1 | 99.0 | 494.4 | -143.5 | 1.83 | 32.3 | 22.5 | 0.1 | 92.7 | 50.9 | 108.9 | 260.1 | -98.5 | 16.7 | -7.0 | - | Y | - | - | deg | deg |
| H20|printed-sec/30min|skip_lo | 1.5 | 10.5 | 97.1 | 707.1 | -137.5 | 0.78 | 30.9 | 97.7 | -14.5 | 305.5 | 7.7 | 119.1 | 364.1 | -135.5 | -26.5 | 96.9 | - | - | - | - | deg | deg |

### Block I (38 cells; gate a 10, a+b 3, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I2|beta-drift|size8_hi | 16.6 | 20.5 | 107.2 | 497.9 | -145.9 | 1.38 | 44.1 | 68.7 | -4.4 | 96.3 | 48.7 | 152.0 | 284.8 | -134.8 | 14.5 | 17.7 | - | - | - | - | deg | deg |
| I2|beta-drift|skip_hi | 15.7 | 18.5 | 103.7 | 486.6 | -146.8 | 1.29 | 29.7 | 72.5 | -6.5 | 84.9 | 23.2 | 118.0 | 267.5 | -138.0 | -11.0 | 0.4 | - | - | - | - | deg | deg |
| I2|beta-drift|skip_lo | 1.9 | 25.3 | 101.6 | 460.1 | -137.0 | 1.80 | 32.2 | 55.3 | 0.4 | 58.4 | -2.9 | 105.7 | 394.2 | -135.4 | -37.1 | 127.1 | - | - | - | - | 0.81/0.80 | 0.83/0.75 |
| I3|RTY/NQ-mom|perm | 2.8 | 17.3 | 96.0 | 666.2 | -140.2 | 1.30 | 25.5 | 86.4 | -7.7 | 264.5 | 38.1 | 75.2 | 208.1 | -22.9 | 3.9 | -59.0 | - | Y | - | - | deg | deg |
| I3|RTY/NQ-mom|s8 | 5.2 | 34.7 | 104.1 | 366.6 | -136.5 | 2.40 | 45.3 | 81.6 | 9.7 | -35.0 | 33.3 | 91.9 | 251.8 | -75.6 | -0.9 | -15.3 | Y | - | - | Y | 0.98/0.81 | 0.98/0.72 |
| I4|ZN|rel+|perm | 3.2 | 22.7 | 102.0 | 461.2 | -136.4 | 1.61 | 28.4 | 73.5 | -2.3 | 59.6 | 56.5 | 137.6 | 209.1 | -63.9 | 22.3 | -58.1 | - | Y | - | - | deg | deg |
| I4|ZN|rel+|s8 | 10.5 | 26.7 | 98.6 | 411.6 | -136.4 | 1.95 | 43.7 | 69.3 | 1.7 | 9.9 | 30.5 | 89.5 | 162.8 | -79.7 | -3.7 | -104.3 | - | - | - | - | deg | deg |
| I4|ZN|rel-|perm | -1.1 | 14.0 | 88.3 | 536.2 | -136.1 | 1.14 | 28.3 | 77.1 | -11.0 | 134.5 | -11.3 | 105.5 | 371.3 | -135.2 | -45.5 | 104.2 | - | - | - | - | deg | deg |
| I4|ZN|rel-|s8 | 6.8 | 31.7 | 106.3 | 344.4 | -135.6 | 2.15 | 44.4 | 74.6 | 6.7 | -57.2 | 35.9 | 98.1 | 226.8 | -106.2 | 1.7 | -40.3 | Y | Y | - | - | 0.90/0.93 | 0.91/0.92 |
| I5|6E|rel+|perm | -1.8 | 24.9 | 97.7 | 555.9 | -135.8 | 1.83 | 29.0 | 74.8 | -0.1 | 154.2 | 66.5 | 75.1 | 209.0 | -70.6 | 32.3 | -58.1 | - | Y | - | - | deg | deg |
| I5|6E|rel+|s8 | 5.6 | 30.6 | 104.1 | 560.5 | -139.9 | 2.12 | 43.9 | 71.0 | 5.6 | 158.9 | 77.5 | 76.7 | 162.3 | -37.5 | 43.3 | -104.8 | - | Y | - | - | 0.86/0.03 | 0.77/0.11 |
| I5|6E|rel-|perm | 6.0 | 10.5 | 87.9 | 551.6 | -144.7 | 0.86 | 24.8 | 92.1 | -14.5 | 150.0 | 18.9 | 130.5 | 277.9 | -136.6 | -15.3 | 10.7 | - | - | - | - | deg | deg |
| I5|6E|rel-|s8 | 14.7 | 23.8 | 101.6 | 409.7 | -146.1 | 1.69 | 46.1 | 88.9 | -1.2 | 8.0 | 24.3 | 115.4 | 272.5 | -136.1 | -9.9 | 5.4 | - | - | - | - | deg | deg |
| I8|GC|rel+|perm | 9.6 | 21.1 | 97.5 | 631.8 | -137.3 | 1.56 | 29.1 | 74.7 | -3.9 | 230.2 | 23.4 | 117.8 | 337.7 | -135.6 | -10.8 | 70.5 | - | - | - | - | deg | deg |
| I8|GC|rel+|s8 | 10.1 | 27.4 | 101.8 | 381.1 | -135.8 | 1.94 | 44.3 | 69.8 | 2.4 | -20.6 | 30.4 | 92.5 | 283.4 | -61.6 | -3.9 | 16.3 | Y | - | - | - | 0.48/0.72 | 0.50/0.67 |
| I8|GC|rel-|perm | 4.0 | 5.7 | 83.7 | 558.1 | -138.0 | 0.49 | 25.2 | 94.2 | -19.3 | 156.5 | 3.5 | 74.1 | 264.6 | -109.0 | -30.7 | -2.5 | - | - | - | - | deg | deg |
| I8|GC|rel-|s8 | 16.0 | 22.5 | 101.9 | 486.5 | -137.7 | 1.59 | 47.0 | 92.5 | -2.5 | 84.8 | 23.2 | 94.9 | 257.5 | -134.9 | -11.0 | -9.6 | - | - | - | - | deg | deg |
| I9|BTC-asia|perm | 12.9 | 20.9 | 106.6 | 807.8 | -137.9 | 1.41 | 34.3 | 47.4 | -4.1 | 406.1 | 100.0 | 149.3 | 248.4 | -78.7 | 65.8 | -18.7 | - | Y | - | - | deg | deg |
| I9|BTC-asia|s8 | 13.0 | 27.5 | 111.6 | 387.7 | -138.4 | 1.78 | 39.3 | 40.8 | 2.6 | -13.9 | 49.3 | 93.3 | 244.7 | -98.7 | 15.1 | -22.5 | Y | Y | - | - | 0.79/0.83 | 0.60/0.66 |
| I10|VX-slope(F2/F1-1, daily-only)|size8_hi | 16.9 | 24.9 | 99.9 | 372.5 | -136.7 | 1.80 | 42.6 | 52.1 | -0.1 | -29.1 | 29.9 | 115.3 | 274.9 | -122.4 | -4.3 | 7.7 | - | - | - | - | 0.25/0.53 | 0.22/0.86 |
| I10|VX-slope(F2/F1-1, daily-only)|skip_hi | 17.3 | 15.2 | 90.2 | 400.1 | -137.2 | 1.21 | 24.0 | 52.6 | -9.8 | -1.5 | 42.1 | 87.6 | 134.6 | -90.4 | 7.9 | -132.5 | - | Y | - | - | deg | deg |
| I10|VX-slope(F2/F1-1, daily-only)|skip_lo | 11.1 | 19.3 | 81.2 | 308.9 | -137.1 | 1.71 | 23.7 | 56.1 | -5.7 | -92.8 | 42.5 | 93.4 | 267.1 | -98.9 | 8.3 | 0.0 | - | - | - | - | deg | deg |
| I11|fade-z1 | 12.0 | 12.9 | 92.5 | 548.8 | -138.6 | 1.00 | 28.8 | 71.9 | -12.1 | 147.2 | 21.1 | 108.4 | 209.3 | -134.5 | -13.1 | -57.8 | - | - | - | - | deg | deg |
| I11|fade-z2 | 4.0 | 20.8 | 101.6 | 477.7 | -137.1 | 1.47 | 34.1 | 22.7 | -4.2 | 76.0 | 27.3 | 92.7 | 230.5 | -91.5 | -6.9 | -36.6 | - | - | - | - | 0.21/0.34 | 0.09/0.32 |
| I12|resid-mom|perm | -3.6 | 21.6 | 96.5 | 479.8 | -137.7 | 1.61 | 31.8 | 57.0 | -3.4 | 78.2 | 42.0 | 81.3 | 166.4 | -92.8 | 7.7 | -100.7 | - | Y | - | - | deg | deg |
| I12|resid-mom|s8 | 13.3 | 27.4 | 101.9 | 431.2 | -137.4 | 1.94 | 40.8 | 54.0 | 2.4 | 29.5 | 30.9 | 89.2 | 180.4 | -92.6 | -3.3 | -86.7 | - | - | - | - | 0.53/0.51 | 0.50/0.53 |
| I16|meanabscorr|size20_lo | 16.8 | 25.6 | 106.9 | 398.9 | -144.3 | 1.73 | 32.7 | 56.1 | 0.7 | -2.7 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | Y | - | - | - | 0.66/0.94 | 0.65/0.84 |
| I16|meanabscorr|size8_hi | 7.5 | 27.6 | 102.4 | 379.0 | -137.1 | 1.95 | 46.3 | 55.2 | 2.6 | -22.7 | 46.3 | 105.5 | 267.1 | -98.9 | 12.1 | 0.0 | Y | - | - | - | 0.64/0.66 | 0.54/0.86 |
| I16|meanabscorr|skip_hi | 3.5 | 13.3 | 87.2 | 363.7 | -137.1 | 1.10 | 23.5 | 55.6 | -11.6 | -38.0 | -17.1 | 35.2 | 267.1 | -98.9 | -51.3 | 0.0 | - | - | - | - | deg | deg |
| I17|size8-if-corr>0 | 8.4 | 26.5 | 94.8 | 308.5 | -137.1 | 2.01 | 49.5 | 77.9 | 1.5 | -93.1 | 41.9 | 111.5 | 274.9 | -122.4 | 7.6 | 7.7 | Y | - | - | - | 0.44/0.89 | 0.54/0.97 |
| I17|skip-if-corr>0 | 3.3 | 12.8 | 71.3 | 308.5 | -137.1 | 1.29 | 18.3 | 77.9 | -12.2 | -93.1 | 0.0 | 0.0 | 0.0 | 0.0 | -34.2 | -267.1 | - | - | - | - | deg | deg |
| I18|NKD-london|perm | 9.3 | 25.6 | 99.1 | 429.6 | -138.5 | 1.86 | 34.8 | 25.5 | 0.6 | 27.9 | 22.5 | 125.9 | 312.8 | -134.8 | -11.7 | 45.7 | - | - | - | - | 0.66/0.55 | 0.63/0.65 |
| I18|NKD-london|s8 | 11.8 | 27.0 | 105.4 | 326.7 | -139.3 | 1.85 | 38.5 | 22.2 | 2.0 | -74.9 | 22.0 | 117.3 | 315.4 | -101.0 | -12.2 | 48.3 | Y | - | - | - | 0.52/0.98 | 0.61/1.00 |
| I19|gapdiv-NY|perm | 12.5 | 27.4 | 100.4 | 399.5 | -138.7 | 1.97 | 33.4 | 17.1 | 2.4 | -2.1 | 35.3 | 107.0 | 247.4 | -87.5 | 1.1 | -19.7 | Y | Y | - | - | 0.90/0.59 | 0.81/0.84 |
| I19|gapdiv-NY|s8 | 14.0 | 28.8 | 101.2 | 382.8 | -136.3 | 2.05 | 37.1 | 16.9 | 3.8 | -18.9 | 32.1 | 110.6 | 282.4 | -100.1 | -2.1 | 15.2 | Y | - | - | Y | 0.85/0.64 | 0.75/0.66 |
| I20|relvol|size8_hi | 4.9 | 27.5 | 107.0 | 552.6 | -139.5 | 1.86 | 48.5 | 93.3 | 2.5 | 150.9 | 82.3 | 118.1 | 284.1 | -130.2 | 48.1 | 17.0 | - | - | - | - | 0.66/0.14 | 0.53/0.08 |
| I20|relvol|skip_hi | 6.9 | 5.8 | 103.6 | 1000.6 | -138.9 | 0.40 | 31.3 | 98.5 | -19.2 | 599.0 | -4.4 | 118.4 | 351.7 | -135.0 | -38.6 | 84.6 | - | - | - | - | deg | deg |
| I20|relvol|skip_lo | 19.7 | 23.7 | 96.8 | 445.2 | -141.3 | 1.77 | 29.9 | 39.9 | -1.2 | 43.6 | 36.6 | 108.8 | 194.6 | -109.3 | 2.4 | -72.6 | - | Y | - | - | deg | deg |

### Block J (9 cells; gate a 1, a+b 0, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J2|skip-13-15 | 14.3 | 24.5 | 104.5 | 401.6 | -137.1 | 1.69 | 35.8 | 0.4 | -0.5 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | 0.19/0.17 | 0.36/0.48 |
| J2|skip-day | 17.5 | 22.2 | 104.3 | 401.9 | -137.1 | 1.53 | 35.1 | 4.6 | -2.8 | 0.2 | 32.0 | 112.4 | 267.1 | -107.8 | -2.2 | 0.0 | - | - | - | - | deg | deg |
| J8|thu-skip-07:30-10 | 16.7 | 21.9 | 102.6 | 395.9 | -137.1 | 1.54 | 35.5 | 4.7 | -3.1 | -5.7 | 16.2 | 124.5 | 377.8 | -134.2 | -18.0 | 110.7 | - | - | - | - | deg | deg |
| J8|thu-skip-08-09 | 14.5 | 26.0 | 106.2 | 418.4 | -137.1 | 1.77 | 35.8 | 2.2 | 1.0 | 16.7 | 30.0 | 111.9 | 283.9 | -98.9 | -4.2 | 16.7 | - | - | - | - | 0.76/0.25 | 0.64/0.39 |
| J14|qw-size8 | 13.6 | 24.6 | 104.3 | 401.6 | -137.1 | 1.70 | 36.2 | 3.2 | -0.4 | 0.0 | 32.2 | 107.6 | 267.1 | -98.9 | -2.0 | 0.0 | - | - | - | - | 0.35/0.54 | 0.33/0.50 |
| J14|qw-skip | 13.1 | 24.3 | 103.7 | 401.6 | -137.1 | 1.69 | 35.2 | 3.2 | -0.6 | 0.0 | 29.4 | 105.6 | 267.1 | -98.9 | -4.8 | 0.0 | - | - | - | - | deg | deg |
| J16|qend-size8 | 13.5 | 26.1 | 103.3 | 381.6 | -137.1 | 1.83 | 37.4 | 7.7 | 1.2 | -20.1 | 36.4 | 109.9 | 267.1 | -98.9 | 2.2 | 0.0 | Y | - | - | - | 0.80/0.67 | 0.59/0.54 |
| J16|qend-skip | 13.6 | 24.9 | 102.7 | 372.3 | -137.1 | 1.75 | 34.6 | 7.7 | -0.0 | -29.3 | 35.1 | 109.6 | 267.1 | -98.9 | 0.9 | 0.0 | - | - | - | - | deg | deg |
| J18|dec-rebalance-skip | 14.0 | 24.5 | 103.8 | 401.6 | -137.1 | 1.70 | 35.6 | 1.4 | -0.5 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | 0.31/0.15 | 0.32/0.55 |

### Block K (40 cells; gate a 8, a+b 3, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K4|msg-burst|size8_hi | 9.7 | 20.7 | 105.2 | 499.1 | -144.0 | 1.42 | 42.5 | 63.9 | -4.2 | 97.5 | 39.3 | 117.8 | 161.1 | -135.5 | 5.1 | -106.0 | - | Y | - | - | deg | deg |
| K4|msg-burst|skip_hi | 4.8 | 24.9 | 91.2 | 368.9 | -137.1 | 1.97 | 31.9 | 68.6 | -0.0 | -32.7 | 48.2 | 124.6 | 226.7 | -134.5 | 14.0 | -40.4 | - | Y | - | - | 0.84/0.94 | 0.70/0.96 |
| K4|msg-burst|skip_lo | 2.2 | 17.8 | 98.1 | 441.8 | -136.8 | 1.31 | 32.2 | 39.5 | -7.2 | 40.2 | 39.9 | 76.1 | 233.6 | -92.7 | 5.7 | -33.6 | - | Y | - | - | deg | deg |
| K7|eff-spread15|size8_hi | 3.4 | 27.9 | 103.0 | 502.7 | -137.7 | 1.95 | 53.8 | 106.3 | 2.9 | 101.0 | 47.9 | 115.0 | 253.0 | -136.1 | 13.7 | -14.1 | - | Y | - | - | 0.66/0.21 | 0.56/0.26 |
| K7|eff-spread15|skip_hi | -1.4 | 20.4 | 88.5 | 729.1 | -136.5 | 1.67 | 24.4 | 108.7 | -4.5 | 327.4 | 12.3 | 127.3 | 437.4 | -136.1 | -21.9 | 170.3 | - | - | - | - | deg | deg |
| K7|eff-spread15|skip_lo | 11.7 | 20.3 | 101.1 | 598.8 | -136.3 | 1.45 | 33.7 | 21.7 | -4.7 | 197.1 | 23.9 | 88.4 | 267.9 | -59.0 | -10.4 | 0.8 | - | - | - | - | deg | deg |
| K8|sweep-impact|size8_hi | 10.7 | 25.4 | 104.4 | 388.3 | -136.7 | 1.76 | 37.9 | 23.0 | 0.4 | -13.4 | 45.2 | 109.0 | 237.4 | -90.4 | 11.0 | -29.7 | Y | Y | - | - | 0.26/0.54 | 0.34/0.67 |
| K8|sweep-impact|skip_hi | 6.3 | 21.7 | 100.7 | 449.6 | -142.4 | 1.55 | 34.7 | 24.9 | -3.3 | 48.0 | 39.2 | 109.6 | 226.1 | -90.4 | 5.0 | -41.0 | - | Y | - | - | deg | deg |
| K8|sweep-impact|skip_lo | 22.9 | 23.0 | 98.0 | 478.6 | -143.1 | 1.70 | 33.0 | 27.0 | -1.9 | 77.0 | 37.5 | 104.6 | 251.2 | -102.9 | 3.3 | -15.9 | - | Y | - | - | deg | deg |
| K9|sweeps15|size8_hi | 16.5 | 27.9 | 100.4 | 404.6 | -137.8 | 2.00 | 38.1 | 29.3 | 2.9 | 3.0 | 34.3 | 105.4 | 267.5 | -100.1 | 0.1 | 0.3 | - | - | - | - | deg | deg |
| K9|sweeps15|skip_hi | 20.0 | 26.2 | 91.9 | 377.4 | -138.6 | 2.05 | 31.5 | 29.7 | 1.2 | -24.2 | 38.4 | 98.2 | 236.8 | -73.3 | 4.2 | -30.3 | Y | Y | - | - | 0.80/0.78 | 0.84/0.94 |
| K9|sweeps15|skip_lo | 1.0 | 11.5 | 99.2 | 579.7 | -144.9 | 0.84 | 31.0 | 87.1 | -13.5 | 178.0 | 10.4 | 130.0 | 425.6 | -134.6 | -23.8 | 158.4 | - | - | - | - | deg | deg |
| K10|refills30|size8_hi | 14.2 | 29.5 | 101.0 | 388.2 | -140.0 | 2.11 | 37.8 | 23.9 | 4.5 | -13.5 | 38.2 | 109.4 | 267.5 | -100.1 | 4.0 | 0.3 | Y | - | - | Y | 0.90/0.52 | 0.73/0.66 |
| K10|refills30|skip_hi | 14.7 | 25.9 | 96.4 | 391.2 | -136.2 | 1.94 | 32.3 | 24.2 | 1.0 | -10.4 | 49.5 | 108.8 | 253.6 | -90.0 | 15.3 | -13.6 | Y | Y | - | - | 0.80/0.78 | 0.80/0.92 |
| K10|refills30|skip_lo | 1.5 | 8.5 | 97.1 | 1120.8 | -137.5 | 0.63 | 30.2 | 103.0 | -16.5 | 719.1 | 17.3 | 147.8 | 410.0 | -134.9 | -16.9 | 142.9 | - | - | - | - | deg | deg |
| K12|depth-slope-consumed|size8_hi | 14.6 | 26.0 | 105.1 | 371.6 | -136.2 | 1.78 | 36.7 | 16.7 | 1.0 | -30.1 | 36.5 | 107.9 | 281.0 | -98.9 | 2.2 | 13.9 | Y | - | - | - | 0.38/0.75 | 0.38/0.68 |
| K12|depth-slope-consumed|skip_hi | 10.4 | 24.8 | 102.9 | 396.2 | -138.2 | 1.74 | 33.8 | 16.1 | -0.1 | -5.4 | 45.4 | 127.1 | 349.8 | -117.9 | 11.1 | 82.7 | - | - | - | - | deg | deg |
| K12|depth-slope-consumed|skip_lo | 1.0 | 18.1 | 89.5 | 777.9 | -135.9 | 1.46 | 25.5 | 104.1 | -6.8 | 376.3 | 29.1 | 109.7 | 268.4 | -135.9 | -5.1 | 1.3 | - | - | - | - | deg | deg |
| K13|cancel-ratio|size8_hi | 10.8 | 27.9 | 102.0 | 536.6 | -141.1 | 1.98 | 38.2 | 28.6 | 3.0 | 135.0 | 27.4 | 113.5 | 330.3 | -134.8 | -6.8 | 63.1 | - | - | - | - | deg | deg |
| K13|cancel-ratio|skip_hi | 12.4 | 24.3 | 97.4 | 466.2 | -136.4 | 1.80 | 30.9 | 29.1 | -0.7 | 64.6 | 34.2 | 102.5 | 283.1 | -135.5 | -0.0 | 16.0 | - | - | - | - | deg | deg |
| K13|cancel-ratio|skip_lo | 15.5 | 27.8 | 100.1 | 881.1 | -141.5 | 2.00 | 30.3 | 88.5 | 2.8 | 479.5 | 47.7 | 116.8 | 273.2 | -134.9 | 13.5 | 6.1 | - | - | - | - | 0.96/0.03 | 0.97/0.06 |
| K14|imb-persist|size8_hi | 8.9 | 29.3 | 102.3 | 360.0 | -140.2 | 2.07 | 42.9 | 49.5 | 4.3 | -41.6 | 43.0 | 133.4 | 284.4 | -92.0 | 8.8 | 17.3 | Y | - | - | - | 0.69/0.85 | 0.78/0.90 |
| K14|imb-persist|skip_hi | -2.6 | 12.9 | 96.7 | 638.4 | -139.4 | 0.96 | 32.7 | 57.2 | -12.0 | 236.8 | 57.6 | 143.6 | 355.6 | -134.5 | 23.4 | 88.4 | - | - | - | - | deg | deg |
| K14|imb-persist|skip_lo | 10.5 | 17.8 | 98.8 | 713.2 | -136.8 | 1.30 | 31.3 | 54.6 | -7.2 | 311.5 | 56.0 | 99.3 | 171.3 | -113.0 | 21.8 | -95.9 | - | Y | - | - | deg | deg |
| K15|through15|size8_hi | 14.9 | 27.6 | 100.5 | 399.2 | -137.8 | 1.98 | 37.9 | 29.2 | 2.6 | -2.5 | 36.9 | 108.4 | 267.5 | -100.1 | 2.7 | 0.3 | Y | - | - | - | 0.66/0.40 | 0.61/0.69 |
| K15|through15|skip_hi | 17.1 | 25.2 | 94.5 | 460.0 | -138.6 | 1.92 | 31.4 | 29.7 | 0.2 | 58.4 | 42.3 | 106.9 | 253.6 | -90.0 | 8.1 | -13.6 | - | Y | - | - | deg | deg |
| K15|through15|skip_lo | -2.4 | 10.1 | 92.8 | 538.4 | -138.1 | 0.79 | 31.5 | 87.8 | -14.8 | 136.8 | 3.2 | 131.9 | 336.7 | -134.8 | -31.0 | 69.6 | - | - | - | - | deg | deg |
| K16|micro-mid|size8_lo | 11.7 | 25.2 | 105.9 | 537.8 | -137.0 | 1.72 | 41.3 | 52.2 | 0.2 | 136.2 | 52.1 | 93.8 | 246.0 | -79.1 | 17.9 | -21.1 | - | Y | - | - | deg | deg |
| K16|micro-mid|skip_hi | 8.6 | 6.7 | 94.2 | 813.5 | -136.1 | 0.51 | 32.5 | 55.7 | -18.3 | 411.9 | 49.4 | 114.7 | 248.4 | -134.9 | 15.2 | -18.8 | - | Y | - | - | deg | deg |
| K16|micro-mid|skip_lo | 5.0 | 22.9 | 94.9 | 509.4 | -137.2 | 1.74 | 32.3 | 55.3 | -2.0 | 107.8 | 41.6 | 131.7 | 297.0 | -118.8 | 7.4 | 29.9 | - | - | - | - | 0.63/0.53 | 0.70/0.57 |
| K17|poc-dist|size8_hi | -4.0 | 26.0 | 104.5 | 355.5 | -139.9 | 1.79 | 38.5 | 20.4 | 1.0 | -46.1 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | Y | - | - | - | 0.53/0.93 | 0.53/0.85 |
| K17|poc-dist|skip_hi | -2.2 | 20.3 | 102.7 | 569.0 | -136.3 | 1.43 | 35.9 | 22.1 | -4.6 | 167.4 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| K17|poc-dist|skip_lo | 18.8 | 14.5 | 81.2 | 379.0 | -149.5 | 1.29 | 16.7 | 93.9 | -10.5 | -22.7 | -2.2 | 19.5 | 51.8 | -18.3 | -36.4 | -215.3 | - | - | - | - | deg | deg |
| K18|LVN-target | 13.7 | 22.7 | 105.9 | 401.6 | -137.8 | 1.54 | 37.0 | n/a | -2.3 | 0.0 | 63.1 | 120.8 | 259.5 | -109.8 | 28.8 | -7.6 | - | Y | - | - | deg | deg |
| K19|va-pos|size8_hi | 7.2 | 24.3 | 102.7 | 368.8 | -136.1 | 1.71 | 39.7 | 36.5 | -0.7 | -32.8 | 34.9 | 108.5 | 261.7 | -93.8 | 0.7 | -5.4 | - | Y | - | - | deg | deg |
| K19|va-pos|skip_hi | -5.8 | 14.3 | 100.0 | 580.0 | -141.0 | 1.03 | 33.7 | 40.0 | -10.7 | 178.4 | 33.7 | 110.2 | 271.3 | -103.6 | -0.5 | 4.1 | - | - | - | - | deg | deg |
| K19|va-pos|skip_lo | 10.4 | 32.7 | 102.3 | 458.2 | -136.5 | 2.31 | 33.7 | 39.4 | 7.7 | 56.6 | 77.2 | 90.4 | 133.6 | -89.4 | 43.0 | -133.6 | - | Y | - | - | 0.99/0.71 | 0.97/0.61 |
| K20|or-skew|size8_hi | 15.0 | 24.5 | 104.3 | 467.4 | -137.1 | 1.70 | 36.4 | 9.5 | -0.5 | 65.7 | 35.9 | 111.6 | 248.8 | -98.9 | 1.7 | -18.4 | - | Y | - | - | deg | deg |
| K20|or-skew|skip_hi | 15.7 | 24.1 | 102.8 | 547.6 | -137.4 | 1.69 | 34.0 | 9.6 | -0.9 | 146.0 | 40.5 | 114.8 | 234.8 | -110.4 | 6.3 | -32.4 | - | Y | - | - | deg | deg |
| K20|or-skew|skip_lo | 10.9 | 26.4 | 100.6 | 517.4 | -138.6 | 1.89 | 34.3 | 8.8 | 1.4 | 115.8 | 22.2 | 122.7 | 366.5 | -134.6 | -12.0 | 99.4 | - | - | - | - | 0.79/0.06 | 0.64/0.34 |

### Block L (20 cells; gate a 4, a+b 0, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1|size8-below-p40 | 14.2 | 21.8 | 107.7 | 387.0 | -138.5 | 1.46 | 40.4 | 45.0 | -3.2 | -14.7 | 23.8 | 104.4 | 221.6 | -89.8 | -10.4 | -45.5 | - | - | - | - | 0.12/0.65 | 0.08/0.78 |
| L1|skip-below-p35 | 12.8 | 14.6 | 101.7 | 505.3 | -136.9 | 1.04 | 33.1 | 41.1 | -10.3 | 103.7 | 56.1 | 81.1 | 197.7 | -42.1 | 21.9 | -69.4 | - | Y | - | - | deg | deg |
| L2|iso-p<.45->8,>.55->20 | 9.2 | 26.0 | 103.7 | 433.5 | -137.1 | 1.81 | 35.5 | 11.4 | 1.0 | 31.9 | 33.5 | 110.0 | 272.9 | -98.9 | -0.7 | 5.8 | - | - | - | - | 0.61/0.27 | 0.55/0.44 |
| L3|size8-if-q50<0 | 8.5 | 28.9 | 105.9 | 353.5 | -141.1 | 1.97 | 42.5 | 49.4 | 3.9 | -48.1 | 32.6 | 108.1 | 255.2 | -98.9 | -1.6 | -11.9 | Y | - | - | - | 0.70/0.92 | 0.68/0.87 |
| L3|skip-if-q20<0 | -4.6 | 0.0 | 0.0 | 0.0 | 0.0 | nan | 0.0 | 157.9 | -25.0 | -401.6 | 0.0 | 0.0 | 0.0 | 0.0 | -34.2 | -267.1 | - | - | - | - | deg | deg |
| L5|shrink-k100 | 6.1 | 29.8 | 102.9 | 300.2 | -137.1 | 2.08 | 37.5 | 11.7 | 4.8 | -101.4 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | Y | - | Y | Y | 0.96/0.97 | 0.96/1.00 |
| L5|shrink-k30 | 7.9 | 29.1 | 102.2 | 296.9 | -137.1 | 2.05 | 37.5 | 12.7 | 4.1 | -104.8 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | Y | - | - | - | 0.88/0.98 | 0.90/1.00 |
| L6|online-RLS-skip<0 | -0.4 | 20.2 | 105.0 | 454.8 | -137.1 | 1.39 | 32.8 | 34.5 | -4.8 | 53.1 | 26.0 | 117.8 | 352.1 | -135.2 | -8.2 | 85.0 | - | - | - | - | 0.49/0.66 | 0.29/0.52 |
| L8|bocpd>0.5->8 | 11.4 | 25.8 | 104.7 | 401.6 | -137.1 | 1.78 | 36.4 | 2.8 | 0.8 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | 0.68/0.11 | 0.58/0.58 |
| L8|bocpd>0.8->8 | 14.6 | 25.0 | 104.5 | 401.6 | -137.1 | 1.72 | 35.9 | 0.0 | 0.0 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| L9|kernel-h0.5-skip<0 | -0.9 | 15.9 | 92.6 | 646.9 | -147.0 | 1.24 | 33.1 | 38.7 | -9.0 | 245.3 | 25.5 | 104.2 | 308.8 | -86.4 | -8.7 | 41.7 | - | - | - | - | deg | deg |
| L9|kernel-h1.0-skip<0 | -5.3 | 27.1 | 107.5 | 379.1 | -137.1 | 1.82 | 34.4 | 15.4 | 2.1 | -22.5 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | Y | - | - | - | 0.98/0.80 | 0.80/0.77 |
| L10|rf-pnl-regime<.45->8 | 13.7 | 25.0 | 104.5 | 401.6 | -137.1 | 1.72 | 35.9 | 0.0 | 0.0 | 0.0 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| L11|PC1-skip_lo | 3.8 | 10.2 | 86.8 | 567.8 | -137.2 | 0.85 | 27.0 | 97.6 | -14.7 | 166.1 | 43.6 | 120.8 | 285.3 | -134.7 | 9.4 | 18.2 | - | - | - | - | deg | deg |
| L11|PC2-skip_lo | 11.0 | 17.8 | 99.7 | 479.1 | -138.7 | 1.29 | 29.1 | 62.8 | -7.2 | 77.5 | 16.2 | 134.8 | 369.9 | -135.2 | -18.0 | 102.8 | - | - | - | - | 0.29/0.56 | 0.32/0.69 |
| L11|PC3-skip_lo | 5.5 | 14.7 | 96.1 | 581.4 | -136.3 | 1.11 | 30.0 | 59.7 | -10.2 | 179.7 | 4.3 | 130.0 | 436.3 | -134.4 | -29.9 | 169.2 | - | - | - | - | deg | deg |
| L12|kmeans12-skip-neg | -3.3 | 25.2 | 100.5 | 501.0 | -137.1 | 1.81 | 31.8 | 40.4 | 0.2 | 99.4 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | 0.88/0.45 | 0.73/0.51 |
| L12|kmeans6-skip-neg | -1.0 | 21.5 | 103.6 | 608.0 | -137.2 | 1.50 | 34.1 | 18.0 | -3.4 | 206.4 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | deg | deg |
| L16|conformal-width-top3rd->8 | 16.3 | 28.1 | 107.5 | 408.8 | -136.3 | 1.88 | 37.6 | 18.7 | 3.1 | 7.1 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | - | - | - | - | 0.73/0.44 | 0.71/0.53 |
| L17|gmm-low-mean-regime->8 | 9.7 | 22.3 | 99.6 | 405.3 | -137.4 | 1.62 | 44.5 | 54.3 | -2.7 | 3.6 | 37.0 | 115.8 | 269.2 | -98.9 | 2.8 | 2.1 | - | - | - | - | 0.03/0.28 | 0.07/0.62 |

### Block M (22 cells; gate a 3, a+b 1, a+b+c 0)

| cell | IS mean | WF mean | WF SD | WF maxDD | WF worst | WF Sh | tr/wk | fire/mo | dWF mean | dWF maxDD | L8W mean | L8W SD | L8W maxDD | L8W worst | dL8W mean | dL8W maxDD | a | b | c | d | null date m/dd | null feat m/dd |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M2|60/60|w0.25 | 8.8 | 22.4 | 105.8 | 441.1 | -152.3 | 1.53 | nan | n/a | -2.6 | 39.5 | 34.7 | 110.7 | 267.2 | -103.1 | 0.5 | 0.0 | - | - | - | - | deg | deg |
| M2|60/60|w0.5 | 4.0 | 19.9 | 107.4 | 480.6 | -169.2 | 1.33 | nan | n/a | -5.1 | 79.0 | 35.2 | 112.1 | 268.6 | -107.3 | 1.0 | 1.5 | - | - | - | - | 1.00/0.46 | deg |
| M2|60/60|w1.0 | -5.6 | 14.7 | 111.1 | 559.6 | -202.9 | 0.96 | nan | n/a | -10.2 | 158.0 | 36.2 | 115.4 | 285.4 | -115.7 | 2.0 | 18.2 | - | - | - | - | deg | deg |
| M2|opp-side/1xrange|w0.25 | 5.4 | 13.5 | 106.2 | 478.9 | -162.6 | 0.92 | nan | n/a | -11.5 | 77.3 | 22.5 | 117.0 | 308.4 | -129.8 | -11.7 | 41.3 | - | - | - | - | deg | deg |
| M2|opp-side/1xrange|w0.5 | -2.9 | 2.1 | 108.7 | 607.7 | -189.7 | 0.14 | nan | n/a | -22.9 | 206.0 | 10.9 | 125.3 | 349.7 | -160.8 | -23.4 | 82.6 | - | - | - | - | 0.19/0.88 | deg |
| M2|opp-side/1xrange|w1.0 | -19.5 | -20.9 | 115.8 | 3280.6 | -244.1 | -1.30 | nan | n/a | -45.8 | 2879.0 | -12.5 | 143.2 | 451.4 | -222.6 | -46.7 | 184.2 | - | - | - | - | deg | deg |
| M3|60/60|w0.25 | 12.8 | 24.8 | 105.3 | 437.8 | -145.2 | 1.70 | nan | n/a | -0.1 | 36.2 | 32.4 | 112.0 | 284.8 | -101.1 | -1.8 | 17.6 | - | - | - | - | deg | deg |
| M3|60/60|w0.5 | 12.0 | 24.7 | 106.7 | 474.0 | -153.6 | 1.67 | nan | n/a | -0.3 | 72.4 | 30.6 | 115.1 | 302.4 | -103.3 | -3.6 | 35.3 | - | - | - | - | 0.48/0.17 | deg |
| M3|60/60|w1.0 | 10.3 | 24.4 | 110.8 | 546.4 | -170.5 | 1.59 | nan | n/a | -0.6 | 144.7 | 27.0 | 122.4 | 337.6 | -107.6 | -7.2 | 70.5 | - | - | - | - | deg | deg |
| M3|opp-side/1xrange|w0.25 | 12.6 | 24.7 | 112.4 | 504.2 | -187.4 | 1.58 | nan | n/a | -0.3 | 102.5 | 31.1 | 122.9 | 279.1 | -112.8 | -3.1 | 11.9 | - | - | - | - | deg | deg |
| M3|opp-side/1xrange|w0.5 | 11.6 | 24.4 | 122.6 | 606.7 | -240.7 | 1.43 | nan | n/a | -0.6 | 205.1 | 28.0 | 139.2 | 291.0 | -126.6 | -6.2 | 23.8 | - | - | - | - | 0.58/0.01 | deg |
| M3|opp-side/1xrange|w1.0 | 9.5 | 23.7 | 148.0 | 811.8 | -347.4 | 1.16 | nan | n/a | -1.2 | 410.2 | 21.8 | 177.2 | 333.2 | -154.4 | -12.4 | 66.1 | - | - | - | - | deg | deg |
| M4|ST15min|w0.25 | 13.0 | 26.9 | 106.7 | 447.7 | -164.8 | 1.82 | nan | n/a | 2.0 | 46.0 | 24.9 | 115.6 | 293.9 | -116.7 | -9.3 | 26.7 | - | - | - | Y | deg | deg |
| M4|ST15min|w0.5 | 12.3 | 28.9 | 110.6 | 493.7 | -192.6 | 1.88 | nan | n/a | 3.9 | 92.1 | 15.5 | 122.6 | 320.6 | -134.6 | -18.7 | 53.5 | - | - | - | Y | 0.75/0.15 | deg |
| M4|ST15min|w1.0 | 10.9 | 32.8 | 122.9 | 627.7 | -248.2 | 1.92 | nan | n/a | 7.8 | 226.1 | -3.1 | 138.6 | 385.2 | -170.2 | -37.3 | 118.1 | - | - | - | Y | deg | deg |
| M8|invsd-L40 | 10.6 | 29.0 | 110.0 | 429.7 | -139.4 | 1.90 | 36.9 | 157.9 | 4.0 | 28.0 | 19.5 | 125.8 | 351.1 | -136.1 | -14.7 | 84.0 | - | - | - | - | 0.94/0.48 | 0.90/0.68 |
| M8|invsd-L65 | 11.4 | 24.2 | 104.9 | 426.8 | -141.0 | 1.66 | 36.6 | 157.9 | -0.8 | 25.2 | 30.3 | 102.6 | 229.9 | -120.1 | -3.9 | -37.2 | - | - | - | - | deg | deg |
| M13|corr>0.6->10 | 10.8 | 26.0 | 104.8 | 390.3 | -137.0 | 1.79 | 39.7 | 39.8 | 1.0 | -11.3 | 27.1 | 107.0 | 288.5 | -98.9 | -7.1 | 21.4 | Y | - | - | - | 0.54/0.52 | 0.30/0.52 |
| M13|corr>0.8->10 | 13.9 | 25.2 | 104.4 | 373.3 | -137.1 | 1.74 | 36.0 | 1.9 | 0.2 | -28.3 | 34.2 | 109.4 | 267.1 | -98.9 | 0.0 | 0.0 | Y | - | - | - | 0.58/0.95 | 0.44/0.77 |
| M14|K4-RX5-risk0.25 | 16.0 | 31.4 | 108.4 | 434.7 | -162.3 | 2.09 | nan | n/a | 6.5 | 33.1 | 39.0 | 106.7 | 267.1 | -98.9 | 4.8 | 0.0 | - | - | - | Y | 0.81/0.00 | deg |
| M14|K4-RX5-risk0.5 | 18.4 | 37.9 | 118.0 | 467.8 | -188.2 | 2.32 | nan | n/a | 12.9 | 66.2 | 43.8 | 106.9 | 267.1 | -98.9 | 9.6 | 0.0 | - | - | - | Y | 0.81/0.00 | deg |
| M20|pair10/10+K4x1.75 | 16.7 | 39.2 | 118.2 | 370.4 | -149.6 | 2.39 | nan | n/a | 14.3 | -31.3 | 46.4 | 97.7 | 259.4 | -91.8 | 12.1 | -7.8 | Y | Y | - | Y | deg | deg |

## 2. Pareto shortlist (WF weekly mean up, SD down, maxDD down; non-dominated cells of the whole screen)

| cell | WF mean | WF SD | WF maxDD | L8W mean | L8W maxDD | a | b |
|---|---|---|---|---|---|---|---|
| A8|donchian55|w1.0 | 42.7 | 155.8 | 628.6 | 30.3 | 380.9 | - | - |
| F12|nextsession | 40.9 | 135.6 | 680.2 | 65.7 | 292.4 | - | - |
| F2|STonly|arm3.0 | 40.9 | 134.2 | 641.2 | 76.8 | 498.4 | - | - |
| F10|balance-scaled | 40.4 | 133.2 | 514.9 | 59.0 | 420.6 | - | - |
| M20|pair10/10+K4x1.75 | 39.2 | 118.2 | 370.4 | 46.4 | 259.4 | Y | Y |
| M14|K4-RX5-risk0.5 | 37.9 | 118.0 | 467.8 | 43.8 | 267.1 | - | - |
| C13|ST40-HM50 | 36.3 | 109.0 | 466.5 | 6.9 | 305.5 | - | - |
| I3|RTY/NQ-mom|s8 | 34.7 | 104.1 | 366.6 | 33.3 | 251.8 | Y | - |
| A12|swing-anchor-L30 | 33.1 | 99.4 | 632.8 | 28.0 | 344.2 | - | - |
| K19|va-pos|skip_lo | 32.7 | 102.3 | 458.2 | 77.2 | 133.6 | - | Y |
| I4|ZN|rel-|s8 | 31.7 | 106.3 | 344.4 | 35.9 | 226.8 | Y | Y |
| E11|ST14-HM8 | 31.0 | 101.6 | 332.3 | 61.7 | 233.4 | Y | Y |
| H16|zigzag60|size8_hi | 30.3 | 97.3 | 316.4 | 43.9 | 209.5 | Y | Y |
| L5|shrink-k100 | 29.8 | 102.9 | 300.2 | 34.2 | 267.1 | Y | - |
| L5|shrink-k30 | 29.1 | 102.2 | 296.9 | 34.2 | 267.1 | Y | - |
| E13|neg->8 | 28.7 | 96.9 | 311.0 | 26.5 | 311.0 | Y | - |
| E7|wr10<.4->8,>.6->20 | 28.4 | 105.6 | 296.6 | 16.9 | 287.7 | Y | - |
| E11|ST8-HM8 | 28.3 | 86.3 | 376.6 | 41.9 | 274.9 | Y | - |
| D16|t60-stall-5minAgainst | 27.2 | 96.3 | 366.7 | 38.4 | 177.8 | Y | Y |
| I17|size8-if-corr>0 | 26.5 | 94.8 | 308.5 | 41.9 | 274.9 | Y | - |
| K4|msg-burst|skip_hi | 24.9 | 91.2 | 368.9 | 48.2 | 226.7 | - | Y |
| H8|cc/parkinson|skip_hi | 23.7 | 87.1 | 295.0 | 31.3 | 207.4 | - | - |
| I10|VX-slope(F2/F1-1, daily-only)|skip_lo | 19.3 | 81.2 | 308.9 | 42.5 | 267.1 | - | - |
| H2|rv20/VXN|skip_hi | 18.3 | 78.9 | 263.3 | 33.7 | 188.4 | - | - |
| H16|zigzag60|skip_hi | 17.8 | 78.6 | 281.5 | 57.2 | 97.8 | - | Y |
| F14|strike1-1h | 16.9 | 68.6 | 297.5 | 40.1 | 35.0 | - | Y |
| H19|volfrac|skip_lo | 12.3 | 68.1 | 311.0 | 7.8 | 134.6 | - | - |
| H7|only-rising | 12.0 | 73.4 | 282.1 | -6.9 | 195.8 | - | - |
| H10|hurst|only_mid | 7.8 | 63.7 | 585.8 | -1.6 | 179.4 | - | - |
| B16|expanding>1.5 | 7.7 | 51.1 | 371.1 | 27.2 | 120.2 | - | - |
| F4|tdd2.0h | 7.4 | 60.4 | 328.5 | -2.5 | 257.9 | - | - |
| B12|spread>1tick | 1.5 | 20.9 | 128.5 | 10.5 | 0.0 | - | - |
| L3|skip-if-q20<0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | - | - |

## 3. Best 10 configurations as DualStrat2 parameter sheets (cells that beat on mean AND maxDD in WF and L8W, ranked by deflated Sharpe; honest noise probability)

**1. H16|zigzag60|size8_hi** (block H) - rule: number of 60-pt zigzag swings in the prior label day: skip_lo / skip_hi / size8_hi

- DualStrat2 sheet: ST 14 / HM 14 lots unless the rule says otherwise; windows 18:00-18:05 and 15:00-16:54 no new entries; per-book day -2R/+5R; combined cap 8R; give-back arm 2R keep 50% (1-s clock); week floor 8R; R = $16.8k at 14/14; **change = the rule above with cell parameters in the tag**.
- WF mean 30.3k (d 5.3k), SD 97.3k, maxDD 316.4k (d -85.2k), worst -137.1k, Sharpe 2.24; L8W 43.9k / maxDD 209.5k (d 9.7k / -57.6k); IS 6.5k.
- deflated Sharpe (N=3561 trials, SR0 0.446): 0.054; per-cell joint-null tail probability 0.020; honest probability the result is noise (P[at least one of 182 independent items shows a null-world cell this good]) : 0.97; gate c N, gate d N.

**2. E11|ST14-HM8** (block E) - rule: static per-book lots ST x HM in {8,10,14,20}^2 (14,14 = benchmark) =16 plus 1 walk-forward-chosen cell per 12/3/3 fold on fit Sharpe

- DualStrat2 sheet: ST 14 / HM 14 lots unless the rule says otherwise; windows 18:00-18:05 and 15:00-16:54 no new entries; per-book day -2R/+5R; combined cap 8R; give-back arm 2R keep 50% (1-s clock); week floor 8R; R = $16.8k at 14/14; **change = the rule above with cell parameters in the tag**.
- WF mean 31.0k (d 6.0k), SD 101.6k, maxDD 332.3k (d -69.4k), worst -136.4k, Sharpe 2.20; L8W 61.7k / maxDD 233.4k (d 27.5k / -33.7k); IS 8.1k.
- deflated Sharpe (N=3561 trials, SR0 0.446): 0.046; per-cell joint-null tail probability 1.000; honest probability the result is noise (P[at least one of 182 independent items shows a null-world cell this good]) : 1.00; gate c N, gate d N.

**3. E11|ST14-HM10** (block E) - rule: static per-book lots ST x HM in {8,10,14,20}^2 (14,14 = benchmark) =16 plus 1 walk-forward-chosen cell per 12/3/3 fold on fit Sharpe

- DualStrat2 sheet: ST 14 / HM 14 lots unless the rule says otherwise; windows 18:00-18:05 and 15:00-16:54 no new entries; per-book day -2R/+5R; combined cap 8R; give-back arm 2R keep 50% (1-s clock); week floor 8R; R = $16.8k at 14/14; **change = the rule above with cell parameters in the tag**.
- WF mean 30.7k (d 5.8k), SD 102.1k, maxDD 368.4k (d -33.2k), worst -136.1k, Sharpe 2.17; L8W 45.1k / maxDD 248.8k (d 10.9k / -18.4k); IS 11.4k.
- deflated Sharpe (N=3561 trials, SR0 0.446): 0.042; per-cell joint-null tail probability 1.000; honest probability the result is noise (P[at least one of 182 independent items shows a null-world cell this good]) : 1.00; gate c N, gate d N.

**4. I4|ZN|rel-|s8** (block I) - rule: ZN 60-min return sign; relation + (ZN up = long) and - : perm x2 , s8 x2

- DualStrat2 sheet: ST 14 / HM 14 lots unless the rule says otherwise; windows 18:00-18:05 and 15:00-16:54 no new entries; per-book day -2R/+5R; combined cap 8R; give-back arm 2R keep 50% (1-s clock); week floor 8R; R = $16.8k at 14/14; **change = the rule above with cell parameters in the tag**.
- WF mean 31.7k (d 6.7k), SD 106.3k, maxDD 344.4k (d -57.2k), worst -135.6k, Sharpe 2.15; L8W 35.9k / maxDD 226.8k (d 1.7k / -40.3k); IS 6.8k.
- deflated Sharpe (N=3561 trials, SR0 0.446): 0.037; per-cell joint-null tail probability 0.030; honest probability the result is noise (P[at least one of 182 independent items shows a null-world cell this good]) : 1.00; gate c N, gate d N.

**5. K9|sweeps15|skip_hi** (block K) - rule: sweep count (swp_n buy+sell) last 15 min: skip_lo / skip_hi / size8_hi

- DualStrat2 sheet: ST 14 / HM 14 lots unless the rule says otherwise; windows 18:00-18:05 and 15:00-16:54 no new entries; per-book day -2R/+5R; combined cap 8R; give-back arm 2R keep 50% (1-s clock); week floor 8R; R = $16.8k at 14/14; **change = the rule above with cell parameters in the tag**.
- WF mean 26.2k (d 1.2k), SD 91.9k, maxDD 377.4k (d -24.2k), worst -138.6k, Sharpe 2.05; L8W 38.4k / maxDD 236.8k (d 4.2k / -30.3k); IS 20.0k.
- deflated Sharpe (N=3561 trials, SR0 0.446): 0.029; per-cell joint-null tail probability 0.090; honest probability the result is noise (P[at least one of 182 independent items shows a null-world cell this good]) : 1.00; gate c N, gate d N.

**6. D16|t60-stall-5minAgainst** (block D) - rule: at +t min if unrealized < +10 pts and 5-min ST direction against the position: exit; t in {30,60}

- DualStrat2 sheet: ST 14 / HM 14 lots unless the rule says otherwise; windows 18:00-18:05 and 15:00-16:54 no new entries; per-book day -2R/+5R; combined cap 8R; give-back arm 2R keep 50% (1-s clock); week floor 8R; R = $16.8k at 14/14; **change = the rule above with cell parameters in the tag**.
- WF mean 27.2k (d 2.2k), SD 96.3k, maxDD 366.7k (d -34.9k), worst -136.2k, Sharpe 2.03; L8W 38.4k / maxDD 177.8k (d 4.2k / -89.3k); IS -7.7k.
- deflated Sharpe (N=3561 trials, SR0 0.446): 0.027; per-cell joint-null tail probability nan; honest probability the result is noise (P[at least one of 182 independent items shows a null-world cell this good]) : nan; gate c N, gate d N.

**7. E17|cap30k** (block E) - rule: combined open risk cap $C: second entry sized floor((C - open risk)/(bracket*$20)) lots, C in {20k,25k,30k} (14/14 open risk = 33.6k)

- DualStrat2 sheet: ST 14 / HM 14 lots unless the rule says otherwise; windows 18:00-18:05 and 15:00-16:54 no new entries; per-book day -2R/+5R; combined cap 8R; give-back arm 2R keep 50% (1-s clock); week floor 8R; R = $16.8k at 14/14; **change = the rule above with cell parameters in the tag**.
- WF mean 30.8k (d 5.8k), SD 108.3k, maxDD 344.0k (d -57.6k), worst -137.8k, Sharpe 2.05; L8W 41.1k / maxDD 240.7k (d 6.9k / -26.4k); IS 14.2k.
- deflated Sharpe (N=3561 trials, SR0 0.446): 0.025; per-cell joint-null tail probability 0.050; honest probability the result is noise (P[at least one of 182 independent items shows a null-world cell this good]) : 1.00; gate c N, gate d N.

**8. D15|rv15x3** (block D) - rule: exit when RV15 (15 one-min squared returns) > m x RV15 at entry, m in {2,3}

- DualStrat2 sheet: ST 14 / HM 14 lots unless the rule says otherwise; windows 18:00-18:05 and 15:00-16:54 no new entries; per-book day -2R/+5R; combined cap 8R; give-back arm 2R keep 50% (1-s clock); week floor 8R; R = $16.8k at 14/14; **change = the rule above with cell parameters in the tag**.
- WF mean 28.8k (d 3.8k), SD 103.1k, maxDD 350.5k (d -51.2k), worst -138.6k, Sharpe 2.01; L8W 40.6k / maxDD 250.6k (d 6.4k / -16.5k); IS -1.1k.
- deflated Sharpe (N=3561 trials, SR0 0.446): 0.023; per-cell joint-null tail probability nan; honest probability the result is noise (P[at least one of 182 independent items shows a null-world cell this good]) : nan; gate c N, gate d N.

**9. H20|printed-sec/30min|size8_hi** (block H) - rule: tick-activity proxy: printed seconds per minute (1-s tape), trailing 30 min at the signal: skip_lo / skip_hi / size8_hi

- DualStrat2 sheet: ST 14 / HM 14 lots unless the rule says otherwise; windows 18:00-18:05 and 15:00-16:54 no new entries; per-book day -2R/+5R; combined cap 8R; give-back arm 2R keep 50% (1-s clock); week floor 8R; R = $16.8k at 14/14; **change = the rule above with cell parameters in the tag**.
- WF mean 28.3k (d 3.3k), SD 102.7k, maxDD 398.8k (d -2.8k), worst -135.8k, Sharpe 1.99; L8W 36.7k / maxDD 265.7k (d 2.5k / -1.4k); IS 13.9k.
- deflated Sharpe (N=3561 trials, SR0 0.446): 0.022; per-cell joint-null tail probability 0.210; honest probability the result is noise (P[at least one of 182 independent items shows a null-world cell this good]) : 1.00; gate c N, gate d N.

**10. H19|volfrac|size8_hi** (block H) - rule: fraction of prior-day 1-min bars with volume > rolling-390 median: skip_lo / skip_hi / size8_hi

- DualStrat2 sheet: ST 14 / HM 14 lots unless the rule says otherwise; windows 18:00-18:05 and 15:00-16:54 no new entries; per-book day -2R/+5R; combined cap 8R; give-back arm 2R keep 50% (1-s clock); week floor 8R; R = $16.8k at 14/14; **change = the rule above with cell parameters in the tag**.
- WF mean 28.0k (d 3.0k), SD 101.3k, maxDD 335.9k (d -65.8k), worst -137.6k, Sharpe 1.99; L8W 45.8k / maxDD 201.0k (d 11.6k / -66.1k); IS 7.8k.
- deflated Sharpe (N=3561 trials, SR0 0.446): 0.022; per-cell joint-null tail probability 0.030; honest probability the result is noise (P[at least one of 182 independent items shows a null-world cell this good]) : 1.00; gate c N, gate d N.

## 4. Gate a-d passers

None.

## 5. O-methodology on finalists (top 20 per block + all a+b)

| tag                                        | block   |     DSR |   SR0 |   WF_weekly_SR |   HO_mean |   HO_d_mean |   HO_maxdd |   HO_d_maxdd |   HO_weeks | ci_dmean             | ci_dsharpe     | ci_dmaxdd              |   O16_max_year_share | O16_flag   |   O17_wf_trades | O17_pass   |   O18_tpw |   O18_comm_per_wk |   O19_worst_day | O19_NAM_ok   |
|:-------------------------------------------|:--------|--------:|------:|---------------:|----------:|------------:|-----------:|-------------:|-----------:|:---------------------|:---------------|:-----------------------|---------------------:|:-----------|----------------:|:-----------|----------:|------------------:|----------------:|:-------------|
| A12|swing-anchor-L30                       | A       |   0.099 | 0.446 |          0.334 |  40839.4  |    8032.69  |     344236 |    77103     |         68 | [-2423.0, 19224.0]   | [-0.08, 1.55]  | [-227845.0, 325808.0]  |                0.349 | False      |            5182 | True       |    36.493 |          2472.76  |       -100447   | False        |
| A6|chandelier-m3.0                         | A       |   0.041 | 0.446 |          0.297 |  44448.9  |   11642.3   |     292491 |    25357.4   |         68 | [-8074.0, 17589.0]   | [-0.55, 1.27]  | [-220635.0, 363811.0]  |                0.573 | False      |            5276 | True       |    37.155 |          2517.62  |        -99804.7 | False        |
| A15|ema5m-20                               | A       |   0.038 | 0.446 |          0.295 |  44871.1  |   12064.4   |     274399 |     7266.13  |         68 | [-9731.0, 15321.0]   | [-0.59, 1.26]  | [-279407.0, 364816.0]  |                0.397 | False      |            5345 | True       |    37.641 |          2550.54  |       -101132   | False        |
| A10|slope-k0.02                            | A       |   0.034 | 0.446 |          0.289 |  27176.1  |   -5630.61  |     330906 |    63773.1   |         68 | [-3208.0, 10443.0]   | [-0.17, 0.83]  | [-212152.0, 102461.0]  |                0.454 | False      |            5141 | True       |    36.204 |          2453.2   |       -100922   | False        |
| A11|anchor-09:30ET                         | A       |   0.018 | 0.446 |          0.267 |  32740.9  |     -65.765 |     299477 |    32343.5   |         68 | [-5672.0, 9516.0]    | [-0.37, 0.82]  | [-256628.0, 163074.0]  |                0.535 | False      |            5157 | True       |    36.317 |          2460.83  |       -100332   | False        |
| A11|anchor-18:00ET                         | A       |   0.013 | 0.446 |          0.257 |  26035.7  |   -6770.98  |     361002 |    93869.4   |         68 | [-10581.0, 11714.0]  | [-0.66, 0.88]  | [-246873.0, 258530.0]  |                0.561 | False      |            5180 | True       |    36.479 |          2471.81  |       -100517   | False        |
| A10|slope-k0.05                            | A       |   0.012 | 0.446 |          0.257 |  31761.8  |   -1044.87  |     379092 |   111959     |         68 | [-6911.0, 11199.0]   | [-0.45, 0.7]   | [-118336.0, 329428.0]  |                0.822 | True       |            5154 | True       |    36.296 |          2459.4   |       -101253   | False        |
| A17|flip-outside-prior-range               | A       |   0.011 | 0.446 |          0.25  |  28590.4  |   -4216.26  |     246308 |   -20825.4   |         68 | [-5965.0, 6636.0]    | [-0.31, 0.53]  | [-216557.0, 125264.0]  |                0.493 | False      |            4997 | True       |    35.19  |          2384.48  |       -100752   | False        |
| A11|anchor-weekly                          | A       |   0.009 | 0.446 |          0.245 |  32071.1  |    -735.59  |     349781 |    82647.5   |         68 | [-6157.0, 6395.0]    | [-0.41, 0.55]  | [-182757.0, 145639.0]  |                0.499 | False      |            5153 | True       |    36.289 |          2458.93  |       -100332   | False        |
| A5|mult-pct-a0.3                           | A       |   0.008 | 0.446 |          0.244 |  38395.8  |    5589.08  |     266573 |     -559.639 |         68 | [-6447.0, 5860.0]    | [-0.39, 0.37]  | [-153384.0, 91256.0]   |                0.48  | False      |            5073 | True       |    35.725 |          2420.75  |       -100752   | False        |
| A15|ema5m-40                               | A       |   0.008 | 0.446 |          0.243 |  34430.1  |    1623.46  |     267133 |        0     |         68 | [-2136.0, 2112.0]    | [-0.12, 0.16]  | [-59247.0, 23731.0]    |                0.524 | False      |            5089 | True       |    35.838 |          2428.39  |       -100752   | False        |
| A15|ema5m-60                               | A       |   0.006 | 0.446 |          0.24  |  37403.2  |    4596.53  |     437374 |   170241     |         68 | [-7568.0, 10616.0]   | [-0.64, 0.59]  | [-118420.0, 323169.0]  |                0.571 | False      |            4977 | True       |    35.049 |          2374.94  |       -100672   | False        |
| A3|GK-vol                                  | A       |   0.007 | 0.446 |          0.237 |  29975.8  |   -2830.9   |     312125 |    44992.2   |         68 | [-6353.0, 3459.0]    | [-0.36, 0.32]  | [-81045.0, 194354.0]   |                0.405 | False      |            5171 | True       |    36.415 |          2467.51  |       -100752   | False        |
| A2|median-src                              | A       |   0.006 | 0.446 |          0.234 |  32106    |    -700.7   |     270778 |     3644.96  |         68 | [-6624.0, 6875.0]    | [-0.52, 0.36]  | [-134173.0, 171956.0]  |                0.643 | False      |            5150 | True       |    36.268 |          2457.49  |       -100947   | False        |
| A4|fast30-1.5                              | A       |   0.006 | 0.446 |          0.233 |  28753.6  |   -4053.13  |     283575 |    16442.2   |         68 | [-4599.0, 1681.0]    | [-0.22, 0.14]  | [-107391.0, 65576.0]   |                0.649 | False      |            5057 | True       |    35.613 |          2413.11  |       -100752   | False        |
| A1|HA-ST                                   | A       |   0.005 | 0.446 |          0.232 |  35192.5  |    2385.79  |     296105 |    28972.4   |         68 | [-11816.0, 8222.0]   | [-0.8, 0.55]   | [-205851.0, 369425.0]  |                0.599 | False      |            5013 | True       |    35.303 |          2392.12  |        -99796.6 | False        |
| A20|ST-2min                                | A       |   0.005 | 0.446 |          0.227 |  37565.5  |    4758.8   |     243047 |   -24085.6   |         68 | [-12852.0, 7065.0]   | [-0.8, 0.49]   | [-139498.0, 362452.0]  |                0.426 | False      |            4983 | True       |    35.092 |          2377.8   |       -103052   | False        |
| A12|swing-anchor-L60                       | A       |   0.003 | 0.446 |          0.213 |  24652.3  |   -8154.36  |     391992 |   124859     |         68 | [-13142.0, 6076.0]   | [-0.87, 0.43]  | [-174252.0, 357151.0]  |                0.651 | False      |            5089 | True       |    35.838 |          2428.39  |        -99866.6 | False        |
| A13|vwap-slope15                           | A       |   0.003 | 0.446 |          0.212 |  37808.1  |    5001.39  |     248793 |   -18340.5   |         68 | [-10657.0, 6076.0]   | [-0.76, 0.41]  | [-86822.0, 477132.0]   |                0.505 | False      |            4808 | True       |    33.859 |          2294.3   |        -98677.2 | False        |
| A3|PK-vol                                  | A       |   0.003 | 0.446 |          0.21  |  27756.1  |   -5050.62  |     323983 |    56850     |         68 | [-9997.0, 708.0]     | [-0.64, 0.12]  | [-72043.0, 212586.0]   |                0.711 | True       |            5199 | True       |    36.613 |          2480.88  |       -100752   | False        |
| B6|noentry-last10min                       | B       |   0.019 | 0.446 |          0.275 |  45036.2  |   12229.6   |     411868 |   144735     |         68 | [-1120.0, 14657.0]   | [-0.25, 0.7]   | [-168927.0, 281170.0]  |                0.79  | True       |            4941 | True       |    34.796 |          2357.76  |        -98608.1 | False        |
| B8|delay-5min-close                        | B       |   0.015 | 0.446 |          0.268 |  37142.3  |    4335.59  |     424120 |   156987     |         68 | [-8983.0, 18759.0]   | [-0.59, 1.18]  | [-219094.0, 412261.0]  |                0.809 | True       |            5177 | True       |    36.458 |          2470.38  |        -98721.6 | False        |
| B14|limit-flip-close-3min                  | B       |   0.017 | 0.446 |          0.265 |  35061    |    2254.32  |     265316 |    -1817.36  |         68 | [-928.0, 5790.0]     | [-0.04, 0.46]  | [-130291.0, 48658.0]   |                0.629 | False      |            5111 | True       |    35.993 |          2438.88  |       -100752   | False        |
| B18|size8-against                          | B       |   0.014 | 0.446 |          0.263 |  38891.1  |    6084.39  |     431223 |   164090     |         68 | [-4899.0, 9601.0]    | [-0.33, 0.7]   | [-187512.0, 237642.0]  |                0.599 | False      |            6364 | True       |    44.817 |          2398.94  |        -96681.1 | False        |
| B16|expanding>1.0                          | B       |   0.014 | 0.446 |          0.263 |  28263.6  |   -4543.09  |     318707 |    51573.7   |         68 | [-10296.0, 10156.0]  | [-0.57, 0.84]  | [-231191.0, 219861.0]  |                0.521 | False      |            4471 | True       |    31.486 |          2133.49  |       -100417   | False        |
| B6|noentry-last5min                        | B       |   0.01  | 0.446 |          0.253 |  42201.8  |    9395.09  |     440427 |   173294     |         68 | [-4045.0, 11961.0]   | [-0.42, 0.62]  | [-133006.0, 352357.0]  |                0.751 | True       |            5015 | True       |    35.317 |          2393.07  |       -100332   | False        |
| B13|prev-closed<5min                       | B       |   0.009 | 0.446 |          0.248 |  29319.5  |   -3487.22  |     297843 |    30710.2   |         68 | [-3927.0, 6266.0]    | [-0.28, 0.46]  | [-184858.0, 146349.0]  |                0.59  | False      |            4887 | True       |    34.415 |          2331.99  |       -100752   | False        |
| B12x|spread>6ticks(p75/p90)                | B       |   0.009 | 0.446 |          0.247 |  33837.3  |    1030.63  |     328861 |    61728     |         68 | [-6014.0, 8984.0]    | [-0.4, 0.57]   | [-140485.0, 313579.0]  |                0.342 | False      |            4938 | True       |    34.775 |          2356.33  |       -100752   | False        |
| B13|prev-closed<3min                       | B       |   0.008 | 0.446 |          0.246 |  34435.1  |    1628.42  |     257858 |    -9274.88  |         68 | [-3118.0, 4746.0]    | [-0.21, 0.34]  | [-133529.0, 134088.0]  |                0.35  | False      |            4956 | True       |    34.901 |          2364.92  |       -100752   | False        |
| B10|rsi80                                  | B       |   0.009 | 0.446 |          0.246 |  33941.7  |    1134.99  |     281300 |    14167.1   |         68 | [-2525.0, 4174.0]    | [-0.16, 0.31]  | [-170922.0, 75384.0]   |                0.736 | True       |            5066 | True       |    35.676 |          2417.41  |       -100752   | False        |
| B12x|spread>4ticks(p75/p90)                | B       |   0.009 | 0.446 |          0.242 |  18441.3  |  -14365.4   |     414252 |   147119     |         68 | [-10668.0, 9372.0]   | [-0.67, 0.72]  | [-152451.0, 369966.0]  |                0.516 | False      |            4782 | True       |    33.676 |          2281.89  |       -100752   | False        |
| B11|gap5                                   | B       |   0.007 | 0.446 |          0.242 |  32853.2  |      46.486 |     267133 |        0     |         68 | [48.0, 657.0]        | [0.0, 0.04]    | [-15070.0, 1019.0]     |                0.609 | False      |            5108 | True       |    35.972 |          2437.45  |       -100752   | False        |
| B10|rsi70                                  | B       |   0.008 | 0.446 |          0.241 |  24259.3  |   -8547.39  |     441967 |   174833     |         68 | [-11438.0, 7971.0]   | [-0.69, 0.71]  | [-255850.0, 246126.0]  |                0.432 | False      |            4907 | True       |    34.556 |          2341.54  |       -100752   | False        |
| B11|gap10                                  | B       |   0.007 | 0.446 |          0.24  |  32892.1  |      85.467 |     267133 |        0     |         68 | [2.0, 258.0]         | [0.0, 0.02]    | [-629.0, 0.0]          |                0.641 | False      |            5105 | True       |    35.951 |          2436.02  |       -100752   | False        |
| B3|second-chance                           | B       |   0.007 | 0.446 |          0.236 |  32860.9  |      54.244 |     287726 |    20592.8   |         68 | [-5523.0, 5330.0]    | [-0.4, 0.39]   | [-123098.0, 200597.0]  |                0.559 | False      |            5137 | True       |    36.176 |          2451.29  |       -100752   | False        |
| B20|skip-first                             | B       |   0.005 | 0.446 |          0.233 |  43839.9  |   11033.2   |     312087 |    44953.5   |         68 | [-15967.0, 8194.0]   | [-0.97, 0.79]  | [-212711.0, 392652.0]  |                0.714 | True       |            4057 | True       |    28.57  |          1935.93  |       -100682   | False        |
| B9|ES-flip10                               | B       |   0.005 | 0.446 |          0.232 |  19096.6  |  -13710.1   |     449238 |   182105     |         68 | [-15056.0, 7797.0]   | [-0.92, 0.82]  | [-238746.0, 390987.0]  |                0.392 | False      |            4307 | True       |    30.331 |          2055.23  |       -101577   | False        |
| B9|ES-flip20                               | B       |   0.003 | 0.446 |          0.216 |  23895.9  |   -8910.79  |     529645 |   262512     |         68 | [-15953.0, 6422.0]   | [-1.05, 0.63]  | [-196614.0, 430440.0]  |                0.852 | True       |            4596 | True       |    32.366 |          2193.13  |       -100426   | False        |
| B5|first-half                              | B       |   0.002 | 0.446 |          0.213 |  22512.9  |  -10293.7   |     314671 |    47537.6   |         68 | [-13141.0, 6472.0]   | [-0.88, 0.54]  | [-235176.0, 279191.0]  |                0.641 | False      |            4558 | True       |    32.099 |          2175     |       -101492   | False        |
| B16|expanding>1.5                          | B       |   0     | 0.446 |          0.151 |   9868.96 |  -22937.7   |     371108 |   103975     |         68 | [-28136.0, -8002.0]  | [-1.73, 0.27]  | [-324921.0, 319266.0]  |                0.52  | False      |            1547 | True       |    10.894 |           738.202 |        -83361.6 | True         |
| C13|ST40-HM50                              | C       |   0.085 | 0.446 |          0.333 |  44132.1  |   11325.4   |     317527 |    50394.3   |         68 | [-1457.0, 24682.0]   | [-0.19, 1.6]   | [-297108.0, 245338.0]  |                0.64  | False      |            8186 | True       |    57.648 |          3906.22  |        -87443.4 | False        |
| C19|ratio1.1                               | C       |   0.052 | 0.446 |          0.305 |  39467.7  |    6661.02  |     306144 |    39010.8   |         68 | [-1955.0, 12200.0]   | [0.0, 0.97]    | [-268427.0, 131504.0]  |                0.57  | False      |            4835 | True       |    34.049 |          2307.18  |       -100752   | False        |
| C14|asia50-ny75                            | C       |   0.044 | 0.446 |          0.305 |  47763.1  |   14956.4   |     339069 |    71935.6   |         68 | [-5028.0, 19446.0]   | [-0.38, 1.23]  | [-218916.0, 312417.0]  |                0.757 | True       |            5690 | True       |    40.07  |          2715.17  |       -104752   | False        |
| C15|shrink5                                | C       |   0.038 | 0.446 |          0.297 |  34324.3  |    1517.65  |     257031 |   -10101.7   |         68 | [-3985.0, 17085.0]   | [-0.24, 1.12]  | [-243391.0, 180440.0]  |                0.647 | False      |            7633 | True       |    53.754 |          3642.34  |        -87536.6 | False        |
| C14|asia50-ny60                            | C       |   0.037 | 0.446 |          0.295 |  44578.7  |   11772     |     339791 |    72657.5   |         68 | [-4858.0, 18263.0]   | [-0.36, 1.13]  | [-191158.0, 283079.0]  |                0.701 | True       |            5965 | True       |    42.007 |          2846.4   |        -98136.6 | False        |
| C13|ST40-HM60                              | C       |   0.037 | 0.446 |          0.295 |  35720.6  |    2913.9   |     363134 |    96000.5   |         68 | [-4902.0, 15674.0]   | [-0.27, 1.18]  | [-297250.0, 196779.0]  |                0.407 | False      |            7563 | True       |    53.261 |          3608.94  |        -95629.3 | False        |
| C13|ST50-HM60                              | C       |   0.026 | 0.446 |          0.282 |  35550.5  |    2743.79  |     269901 |     2767.48  |         68 | [-5359.0, 12352.0]   | [-0.29, 0.98]  | [-289583.0, 188857.0]  |                0.852 | True       |            6142 | True       |    43.254 |          2930.86  |        -97337.9 | False        |
| C13|ST50-HM50                              | C       |   0.024 | 0.446 |          0.28  |  37871.6  |    5064.95  |     274261 |     7127.62  |         68 | [-9328.0, 15489.0]   | [-0.6, 1.1]    | [-299717.0, 271675.0]  |                0.419 | False      |            6774 | True       |    47.704 |          3232.44  |        -91460.4 | False        |
| C13|ST60-HM40                              | C       |   0.019 | 0.446 |          0.275 |  28643.1  |   -4163.61  |     388091 |   120958     |         68 | [-10348.0, 14037.0]  | [-0.62, 1.06]  | [-228067.0, 286178.0]  |                0.674 | False      |            7157 | True       |    50.401 |          3415.2   |        -95363.7 | False        |
| C14|asia50-ny90                            | C       |   0.02  | 0.446 |          0.274 |  40628.7  |    7821.99  |     406792 |   139659     |         68 | [-8206.0, 16199.0]   | [-0.59, 1.02]  | [-175464.0, 387575.0]  |                0.698 | False      |            5544 | True       |    39.042 |          2645.5   |       -113152   | False        |
| C13|ST40-HM40                              | C       |   0.017 | 0.446 |          0.269 |  31719.5  |   -1087.17  |     359420 |    92286.9   |         68 | [-11503.0, 15011.0]  | [-0.76, 1.15]  | [-245717.0, 408100.0]  |                0.5   | False      |            9580 | True       |    67.465 |          4571.41  |        -88445.2 | False        |
| C14|asia60-ny75                            | C       |   0.013 | 0.446 |          0.256 |  34257.9  |    1451.22  |     260031 |    -7102.36  |         68 | [-4612.0, 6380.0]    | [-0.25, 0.52]  | [-168995.0, 137248.0]  |                0.664 | False      |            4869 | True       |    34.289 |          2323.41  |       -104322   | False        |
| C14|asia40-ny90                            | C       |   0.012 | 0.446 |          0.254 |  32705.9  |    -100.768 |     604837 |   337704     |         68 | [-12298.0, 17535.0]  | [-0.89, 1.1]   | [-84607.0, 843098.0]   |                0.428 | False      |            6632 | True       |    46.704 |          3164.68  |       -109582   | False        |
| C7|75/60/45                                | C       |   0.01  | 0.446 |          0.254 |  31381.7  |   -1425     |     444579 |   177446     |         68 | [-8309.0, 14622.0]   | [-0.65, 0.9]   | [-194864.0, 414583.0]  |                0.68  | False      |            5883 | True       |    41.43  |          2807.27  |       -100752   | False        |
| C13|ST60-HM50                              | C       |   0.011 | 0.446 |          0.253 |  37551.9  |    4745.22  |     414902 |   147769     |         68 | [-12648.0, 13920.0]  | [-0.87, 1.01]  | [-177873.0, 459087.0]  |                0.637 | False      |            5855 | True       |    41.232 |          2793.91  |        -93511.6 | False        |
| C13|ST60-HM60                              | C       |   0.007 | 0.446 |          0.239 |  32806.7  |       0     |     267133 |        0     |         68 | [-0.0, 0.0]          | [0.0, 0.0]     | [-0.0, 0.0]            |                0.722 | True       |            5101 | True       |    35.923 |          2434.11  |       -100752   | False        |
| C14|asia60-ny60                            | C       |   0.007 | 0.446 |          0.239 |  32806.7  |       0     |     267133 |        0     |         68 | [-0.0, 0.0]          | [0.0, 0.0]     | [-0.0, 0.0]            |                0.722 | True       |            5101 | True       |    35.923 |          2434.11  |       -100752   | False        |
| C12|prior-HL                               | C       |   0.007 | 0.446 |          0.239 |  33020.8  |     214.099 |     264396 |    -2737.36  |         68 | [-6077.0, 4724.0]    | [-0.35, 0.39]  | [-160428.0, 183560.0]  |                0.404 | False      |            5038 | True       |    35.479 |          2404.05  |       -100752   | False        |
| C11|round100                               | C       |   0.007 | 0.446 |          0.237 |  28994.9  |   -3811.75  |     270845 |     3712.24  |         68 | [-4405.0, 3177.0]    | [-0.27, 0.24]  | [-87157.0, 82765.0]    |                0.542 | False      |            5088 | True       |    35.831 |          2427.91  |       -100752   | False        |
| C14|asia40-ny75                            | C       |   0.006 | 0.446 |          0.237 |  31604.6  |   -1202.07  |     484397 |   217264     |         68 | [-13186.0, 14678.0]  | [-0.97, 0.86]  | [-104360.0, 770917.0]  |                0.456 | False      |            6748 | True       |    47.521 |          3220.03  |       -107377   | False        |
| D19|15min-ST-flip                          | D       |   0.031 | 0.446 |          0.289 |  29216.2  |   -3590.5   |     650993 |   383860     |         68 | [-5465.0, 17041.0]   | [-0.45, 1.16]  | [-217758.0, 346060.0]  |                0.53  | False      |            6244 | True       |    43.972 |          2979.53  |        -97684.3 | False        |
| D18|exit-HM-when-ST-stopped                | D       |   0.028 | 0.446 |          0.284 |  33911.8  |    1105.15  |     377770 |   110637     |         68 | [-75.0, 9259.0]      | [0.01, 0.71]   | [-210224.0, 106978.0]  |                0.671 | False      |            5191 | True       |    36.556 |          2477.06  |        -99129.3 | False        |
| D16|t60-stall-5minAgainst                  | D       |   0.027 | 0.446 |          0.282 |  28681.2  |   -4125.5   |     366692 |    99559     |         68 | [-6677.0, 10991.0]   | [-0.34, 0.96]  | [-256392.0, 178446.0]  |                0.636 | False      |            6072 | True       |    42.761 |          2897.46  |        -98728.1 | False        |
| D15|rv15x3                                 | D       |   0.023 | 0.446 |          0.279 |  35242.5  |    2435.86  |     252619 |   -14514     |         68 | [-2205.0, 10459.0]   | [-0.16, 0.78]  | [-319792.0, 62573.0]   |                0.684 | False      |            5469 | True       |    38.514 |          2609.71  |        -98312.6 | False        |
| D9|exit-5min-before-release                | D       |   0.014 | 0.446 |          0.263 |  33630.5  |     823.804 |     267603 |      469.998 |         68 | [-1006.0, 6353.0]    | [-0.09, 0.46]  | [-245203.0, 44662.0]   |                0.849 | True       |            5254 | True       |    37     |          2507.12  |       -100802   | False        |
| D15|rv15x2                                 | D       |   0.011 | 0.446 |          0.259 |  39445.2  |    6638.54  |     330371 |    63237.6   |         68 | [-8710.0, 12885.0]   | [-0.62, 0.97]  | [-223711.0, 345776.0]  |                0.626 | False      |            6110 | True       |    43.028 |          2915.59  |        -97882.1 | False        |
| D9|exit-15min-before-release               | D       |   0.011 | 0.446 |          0.254 |  32382.8  |    -423.834 |     263346 |    -3787.36  |         68 | [-2572.0, 4822.0]    | [-0.16, 0.4]   | [-252998.0, 47439.0]   |                0.623 | False      |            5269 | True       |    37.106 |          2514.28  |       -100752   | False        |
| D16|t30-stall-5minAgainst                  | D       |   0.005 | 0.446 |          0.236 |  38629.4  |    5822.73  |     314060 |    46926.9   |         68 | [-9419.0, 7512.0]    | [-0.62, 0.44]  | [-140546.0, 382311.0]  |                0.504 | False      |            5905 | True       |    41.585 |          2817.77  |        -98130.1 | False        |
| D6|cap3.0R                                 | D       |   0.003 | 0.446 |          0.214 |  27954.6  |   -4852.06  |     277523 |    10389.8   |         68 | [-11928.0, 543.0]    | [-0.61, 0.2]   | [-103510.0, 248132.0]  |                0.487 | False      |            4568 | True       |    32.169 |          2179.77  |       -100752   | False        |
| D6|cap4.0R                                 | D       |   0.003 | 0.446 |          0.211 |  29629.5  |   -3177.23  |     267133 |        0     |         68 | [-10469.0, 569.0]    | [-0.56, 0.1]   | [-72639.0, 226693.0]   |                0.741 | True       |            4741 | True       |    33.387 |          2262.32  |       -100752   | False        |
| D12|exit-on-opposite-book-entry            | D       |   0.002 | 0.446 |          0.209 |  21887.4  |  -10919.3   |     425884 |   158751     |         68 | [-11302.0, 3462.0]   | [-0.73, 0.3]   | [-86074.0, 374493.0]   |                0.75  | True       |            5237 | True       |    36.88  |          2499.01  |        -97591.6 | False        |
| D11|ttl-3h/3h/2h                           | D       |   0.001 | 0.446 |          0.193 |  30774    |   -2032.63  |     600996 |   333863     |         68 | [-19033.0, 6319.0]   | [-1.29, 0.51]  | [-53307.0, 793624.0]   |                0.763 | True       |            7307 | True       |    51.458 |          3486.78  |        -97045.9 | False        |
| D17|tgt40-after-2stops                     | D       |   0.001 | 0.446 |          0.192 |  28630.5  |   -4176.17  |     324211 |    57077.9   |         68 | [-10819.0, 1499.0]   | [-0.75, 0.05]  | [-57196.0, 238251.0]   |                0.443 | False      |            5234 | True       |    36.859 |          2497.58  |       -100752   | False        |
| D4|vwap-cross-slope                        | D       |   0.001 | 0.446 |          0.184 |  29031.2  |   -3775.48  |     426411 |   159278     |         68 | [-16368.0, 4642.0]   | [-1.09, 0.3]   | [-62565.0, 666863.0]   |                0.729 | True       |            7285 | True       |    51.303 |          3476.28  |       -103612   | False        |
| D6|cap2.0R                                 | D       |   0.001 | 0.446 |          0.183 |  24988.4  |   -7818.26  |     265316 |    -1817.36  |         68 | [-16088.0, -1095.0]  | [-0.94, 0.05]  | [-90795.0, 334812.0]   |                0.494 | False      |            4237 | True       |    29.838 |          2021.83  |       -100752   | False        |
| D10|ZN-shock                               | D       |   0     | 0.446 |          0.132 |  19856    |  -12950.7   |     394017 |   126884     |         68 | [-21681.0, -1896.0]  | [-1.52, -0.05] | [-133608.0, 625226.0]  |                0.35  | False      |            7005 | True       |    49.331 |          3342.67  |       -100752   | False        |
| D10|CL-shock                               | D       |   0     | 0.446 |          0.124 |  14527.5  |  -18279.1   |     488980 |   221847     |         68 | [-23026.0, -1682.0]  | [-1.61, -0.03] | [-84047.0, 835635.0]   |                0.461 | False      |            6770 | True       |    47.676 |          3230.53  |        -97256.6 | False        |
| D10|6J-shock                               | D       |   0     | 0.446 |          0.117 |  26941.8  |   -5864.9   |     384304 |   117171     |         68 | [-27657.0, -375.0]   | [-1.93, -0.05] | [10203.0, 1120707.0]   |                0.788 | True       |            7318 | True       |    51.535 |          3492.03  |        -98483.6 | False        |
| D2|5min-ST-flip                            | D       |   0     | 0.446 |          0.09  |  17402.8  |  -15403.8   |     529468 |   262335     |         68 | [-29786.0, -2434.0]  | [-2.09, -0.2]  | [4634.0, 1292286.0]    |                0.93  | True       |            8875 | True       |    62.5   |          4235     |        -97256.6 | False        |
| D3|volspike5x-against                      | D       |   0     | 0.446 |          0.026 |   5681.97 |  -27124.7   |     656146 |   389013     |         68 | [-35391.0, -10628.0] | [-2.51, -0.72] | [173440.0, 1798046.0]  |                0.546 | False      |            8592 | True       |    60.507 |          4099.96  |        -97091.9 | False        |
| E11|ST8-HM8                                | E       |   0.08  | 0.446 |          0.328 |  39652.6  |    6845.95  |     306509 |    39375.7   |         68 | [-5942.0, 11104.0]   | [-0.05, 1.26]  | [-353967.0, 104013.0]  |                0.616 | False      |            8700 | True       |    61.268 |          2372.28  |        -79455.8 | True         |
| E11|ST14-HM8                               | E       |   0.046 | 0.446 |          0.305 |  40380.4  |    7573.72  |     322075 |    54941.9   |         68 | [-2147.0, 12928.0]   | [-0.09, 0.97]  | [-238551.0, 149787.0]  |                0.52  | False      |            6338 | True       |    44.634 |          2358.31  |        -89891.3 | False        |
| E5|ES5m-agree14-else8                      | E       |   0.043 | 0.446 |          0.302 |  35083.1  |    2276.41  |     284430 |    17296.6   |         68 | [1310.0, 12377.0]    | [0.1, 0.85]    | [-251483.0, 48293.0]   |                0.743 | True       |            5334 | True       |    37.563 |          2442.43  |       -100752   | False        |
| E11|ST14-HM10                              | E       |   0.042 | 0.446 |          0.301 |  34835.2  |    2028.55  |     368439 |   101306     |         68 | [-479.0, 11280.0]    | [0.01, 0.83]   | [-205814.0, 116932.0]  |                0.795 | True       |            5923 | True       |    41.711 |          2425.39  |        -93989.4 | False        |
| E13|neg->8                                 | E       |   0.04  | 0.446 |          0.297 |  33010    |     203.319 |     311004 |    43870.7   |         68 | [-1191.0, 8935.0]    | [0.03, 0.84]   | [-262130.0, 59359.0]   |                0.722 | True       |            6320 | True       |    44.507 |          2459.54  |       -100752   | False        |
| E11|ST10-HM8                               | E       |   0.031 | 0.446 |          0.292 |  45721.1  |   12914.4   |     335533 |    68400.1   |         68 | [-5516.0, 10529.0]   | [-0.2, 0.85]   | [-231598.0, 150480.0]  |                0.646 | False      |            7865 | True       |    55.387 |          2432.34  |        -85708.7 | False        |
| E11|ST8-HM10                               | E       |   0.031 | 0.446 |          0.291 |  41150.2  |    8343.55  |     414727 |   147594     |         68 | [-7174.0, 10173.0]   | [-0.3, 0.94]   | [-242268.0, 198254.0]  |                0.948 | True       |            8034 | True       |    56.577 |          2425.45  |        -82128.8 | True         |
| E17|cap30k                                 | E       |   0.025 | 0.446 |          0.285 |  41643.5  |    8836.78  |     296215 |    29081.6   |         68 | [-1101.0, 12942.0]   | [-0.1, 0.76]   | [-193404.0, 130457.0]  |                0.493 | False      |            5979 | True       |    42.106 |          2534.97  |        -94602.2 | False        |
| E14|extended->8                            | E       |   0.025 | 0.446 |          0.282 |  36766.2  |    3959.51  |     325621 |    58488.3   |         68 | [-3628.0, 10974.0]   | [-0.21, 0.85]  | [-240069.0, 102743.0]  |                0.396 | False      |            6179 | True       |    43.514 |          2506.98  |        -98312.6 | False        |
| E1|T52w                                    | E       |   0.022 | 0.446 |          0.277 |  28682.5  |   -4124.14  |     704013 |   436879     |         68 | [-6904.0, 15943.0]   | [-0.52, 1.11]  | [-173086.0, 482583.0]  |                0.852 | True       |            4942 | True       |    34.803 |          2443.93  |       -111927   | False        |
| E6|stops2->8                               | E       |   0.018 | 0.446 |          0.274 |  40199.2  |    7392.5   |     327249 |    60115.5   |         68 | [-3184.0, 10415.0]   | [-0.22, 0.73]  | [-208276.0, 148092.0]  |                0.651 | False      |            5765 | True       |    40.599 |          2466.29  |        -87009.6 | False        |
| E15|3rd+->10                               | E       |   0.017 | 0.446 |          0.273 |  36365.6  |    3558.89  |     286022 |    18888.5   |         68 | [-3150.0, 10372.0]   | [-0.18, 0.66]  | [-219873.0, 118716.0]  |                0.572 | False      |            6753 | True       |    47.556 |          2447.2   |        -86424.2 | False        |
| E7|wr10<.4->8,>.6->20                      | E       |   0.017 | 0.446 |          0.269 |  30198.4  |   -2608.32  |     296614 |    29481.1   |         68 | [-5036.0, 12341.0]   | [-0.34, 0.77]  | [-212506.0, 165208.0]  |                0.413 | False      |            5008 | True       |    35.268 |          2409.78  |       -100774   | False        |
| E6|stops3->8                               | E       |   0.013 | 0.446 |          0.259 |  36833.1  |    4026.38  |     267171 |       38.011 |         68 | [-2721.0, 6632.0]    | [-0.18, 0.48]  | [-140887.0, 94155.0]   |                0.597 | False      |            5358 | True       |    37.732 |          2442.02  |        -93699.4 | False        |
| E12|first30min->8                          | E       |   0.012 | 0.446 |          0.257 |  43205.2  |   10398.6   |     302675 |    35541.8   |         68 | [-6160.0, 9092.0]    | [-0.44, 0.68]  | [-139589.0, 381918.0]  |                0.561 | False      |            5544 | True       |    39.042 |          2477.4   |       -100752   | False        |
| E2|hi20lo8                                 | E       |   0.013 | 0.446 |          0.257 |  26294.4  |   -6512.3   |     577018 |   309885     |         68 | [-9378.0, 12514.0]   | [-0.63, 0.89]  | [-178537.0, 447744.0]  |                0.595 | False      |            5000 | True       |    35.211 |          2341.74  |       -107149   | False        |
| E7|wr10<.4->8 only                         | E       |   0.011 | 0.446 |          0.253 |  29154.6  |   -3652.08  |     354116 |    86982.6   |         68 | [-4937.0, 6674.0]    | [-0.32, 0.56]  | [-211651.0, 165628.0]  |                0.497 | False      |            5570 | True       |    39.225 |          2448.29  |       -100752   | False        |
| E12|first60min->8                          | E       |   0.008 | 0.446 |          0.25  |  36423.8  |    3617.16  |     307887 |    40753.7   |         68 | [-7867.0, 9060.0]    | [-0.5, 0.61]   | [-152049.0, 311126.0]  |                0.554 | False      |            5809 | True       |    40.908 |          2473.17  |        -92538.7 | False        |
| E15|3rd+->8                                | E       |   0.009 | 0.446 |          0.249 |  31941.8  |    -864.853 |     339313 |    72180.3   |         68 | [-9122.0, 7144.0]    | [-0.46, 0.64]  | [-228050.0, 167507.0]  |                0.475 | False      |            7689 | True       |    54.148 |          2317.68  |        -82244.3 | True         |
| E1|T26w                                    | E       |   0.009 | 0.446 |          0.248 |  27434.3  |   -5372.36  |     486275 |   219142     |         68 | [-8623.0, 12233.0]   | [-0.61, 0.81]  | [-175403.0, 474052.0]  |                0.418 | False      |            5025 | True       |    35.387 |          2435.07  |       -105229   | False        |
| F2|STonly|arm3.0                           | F       |   0.044 | 0.446 |          0.305 |  50394.9  |   17588.2   |     560203 |   293070     |         68 | [913.0, 29051.0]     | [-0.29, 1.1]   | [-40515.0, 579921.0]   |                0.79  | True       |            7472 | True       |    52.62  |          3565.51  |       -100752   | False        |
| F10|balance-scaled                         | F       |   0.043 | 0.446 |          0.304 |  57524.4  |   24717.8   |     514892 |   247759     |         68 | [4544.0, 24366.0]    | [-0.1, 0.9]    | [-123494.0, 367782.0]  |                0.481 | False      |            6767 | True       |    47.655 |          3229.1   |       -100752   | False        |
| F12|nextsession                            | F       |   0.035 | 0.446 |          0.301 |  57805.2  |   24998.5   |     413648 |   146515     |         68 | [3207.0, 28865.0]    | [-0.2, 1.03]   | [-75986.0, 427072.0]   |                0.545 | False      |            6569 | True       |    46.261 |          3134.62  |       -100752   | False        |
| F2|STonly|arm2.0                           | F       |   0.041 | 0.446 |          0.301 |  48926.6  |   16119.9   |     538917 |   271784     |         68 | [14.0, 24716.0]      | [-0.27, 1.06]  | [-85680.0, 509230.0]   |                0.771 | True       |            6942 | True       |    48.887 |          3312.61  |       -100752   | False        |
| F19|slip0.75                               | F       |   0.037 | 0.446 |          0.298 |  39269.6  |    6462.91  |     308706 |    41573.1   |         68 | [-1817.0, 12890.0]   | [-0.08, 0.94]  | [-284660.0, 205067.0]  |                0.421 | False      |            4942 | True       |    34.803 |          2358.24  |       -100752   | False        |
| F1|replace|arm3.0                          | F       |   0.028 | 0.446 |          0.289 |  47427.3  |   14620.7   |     558409 |   291276     |         68 | [-1290.0, 26977.0]   | [-0.41, 0.98]  | [-31882.0, 623378.0]   |                0.865 | True       |            7340 | True       |    51.69  |          3502.52  |       -100752   | False        |
| F19|slip1.5                                | F       |   0.021 | 0.446 |          0.277 |  36640.8  |    3834.09  |     325274 |    58140.9   |         68 | [-3970.0, 11881.0]   | [-0.26, 0.85]  | [-254043.0, 236452.0]  |                0.483 | False      |            4924 | True       |    34.676 |          2349.65  |       -100752   | False        |
| F2|HMonly|arm3.0                           | F       |   0.019 | 0.446 |          0.277 |  47878.4  |   15071.7   |     591434 |   324301     |         68 | [-1542.0, 25857.0]   | [-0.47, 0.9]   | [-6566.0, 635596.0]    |                0.928 | True       |            7605 | True       |    53.556 |          3628.98  |       -100752   | False        |
| F16|fri-arm1.5-cap6                        | F       |   0.014 | 0.446 |          0.258 |  34409.3  |    1602.57  |     263346 |    -3787.36  |         68 | [-2988.0, 5084.0]    | [-0.12, 0.44]  | [-146625.0, 63897.0]   |                0.409 | False      |            4899 | True       |    34.5   |          2337.72  |       -100752   | False        |
| F14|strike1-1h                             | F       |   0.011 | 0.446 |          0.246 |  23737.3  |   -9069.34  |     218004 |   -49129.5   |         68 | [-17560.0, 649.0]    | [-0.75, 0.81]  | [-267558.0, 159313.0]  |                0.573 | False      |            2075 | True       |    14.613 |           990.155 |       -100752   | False        |
| F7|wktrail10.0R                            | F       |   0.009 | 0.446 |          0.246 |  33889.4  |    1082.72  |     286153 |    19020.2   |         68 | [-2465.0, 4685.0]    | [-0.2, 0.38]   | [-137058.0, 71910.0]   |                0.399 | False      |            5149 | True       |    36.261 |          2457.02  |       -100752   | False        |
| F1|add|arm1.5                              | F       |   0.009 | 0.446 |          0.244 |  30010.4  |   -2796.28  |     243187 |   -23945.8   |         68 | [-7424.0, 4692.0]    | [-0.35, 0.52]  | [-150274.0, 165489.0]  |                0.454 | False      |            4754 | True       |    33.479 |          2268.53  |       -100752   | False        |
| F18|unreal1.0R                             | F       |   0.007 | 0.446 |          0.239 |  32806.7  |       0     |     267133 |        0     |         68 | [-0.0, 0.0]          | [0.0, 0.0]     | [-0.0, 0.0]            |                0.722 | True       |            5101 | True       |    35.923 |          2434.11  |       -100752   | False        |
| F8|month20.0R                              | F       |   0.007 | 0.446 |          0.239 |  32806.7  |       0     |     267133 |        0     |         68 | [-0.0, 0.0]          | [0.0, 0.0]     | [-0.0, 0.0]            |                0.722 | True       |            5101 | True       |    35.923 |          2434.11  |       -100752   | False        |
| F1|replace|arm2.0                          | F       |   0.006 | 0.446 |          0.238 |  37143.7  |    4337.05  |     514788 |   247655     |         68 | [-8718.0, 16698.0]   | [-0.75, 0.62]  | [-42500.0, 640666.0]   |                0.686 | False      |            6386 | True       |    44.972 |          3047.29  |       -100752   | False        |
| F1|replace|arm1.5                          | F       |   0.006 | 0.446 |          0.238 |  36304.2  |    3497.53  |     415989 |   148856     |         68 | [-7360.0, 12810.0]   | [-0.63, 0.6]   | [-85281.0, 463933.0]   |                0.716 | True       |            5610 | True       |    39.507 |          2677     |       -100752   | False        |
| F18|unreal0.75R                            | F       |   0.006 | 0.446 |          0.238 |  32714.1  |     -92.531 |     263346 |    -3787.36  |         68 | [-1425.0, 1083.0]    | [-0.08, 0.06]  | [-38678.0, 39245.0]    |                0.516 | False      |            5100 | True       |    35.915 |          2433.63  |       -100552   | False        |
| F8|month16.0R                              | F       |   0.006 | 0.446 |          0.236 |  32806.7  |       0     |     267133 |        0     |         68 | [-793.0, 0.0]        | [-0.07, 0.0]   | [-0.0, 37524.0]        |                1     | True       |            5070 | True       |    35.704 |          2419.32  |       -100752   | False        |
| F2|HMonly|arm2.0                           | F       |   0.005 | 0.446 |          0.234 |  37859.1  |    5052.44  |     504231 |   237098     |         68 | [-7899.0, 18354.0]   | [-0.75, 0.59]  | [12970.0, 731117.0]    |                0.699 | False      |            7240 | True       |    50.986 |          3454.81  |       -100752   | False        |
| F7|wktrail8.0R                             | F       |   0.003 | 0.446 |          0.226 |  29288.5  |   -3518.22  |     270677 |     3544.38  |         68 | [-7286.0, 2078.0]    | [-0.47, 0.26]  | [-156937.0, 156873.0]  |                0.653 | False      |            4604 | True       |    32.423 |          2196.95  |       -100752   | False        |
| G2|skip-04:00-09:30                        | G       |   0.02  | 0.446 |          0.272 |  22354.8  |  -10451.9   |     312145 |    45011.9   |         68 | [-5298.0, 13720.0]   | [-0.38, 0.93]  | [-293208.0, 259128.0]  |                0.382 | False      |            4856 | True       |    34.197 |          2317.2   |       -101407   | False        |
| G3|skip-09:30-11:30                        | G       |   0.019 | 0.446 |          0.272 |  36635.2  |    3828.57  |     250536 |   -16597.4   |         68 | [-3187.0, 8608.0]    | [-0.17, 0.69]  | [-140371.0, 158426.0]  |                0.655 | False      |            4724 | True       |    33.268 |          2254.21  |       -100752   | False        |
| G4|skip-lunch12-13:30                      | G       |   0.015 | 0.446 |          0.263 |  34883.1  |    2076.4   |     271371 |     4237.68  |         68 | [-2416.0, 5817.0]    | [-0.12, 0.52]  | [-147331.0, 98367.0]   |                0.564 | False      |            4982 | True       |    35.085 |          2377.33  |       -100752   | False        |
| G15|sess-on-if-trail52w>0                  | G       |   0.013 | 0.446 |          0.261 |  32806.7  |       0     |     267133 |        0     |         68 | [-3806.0, 8696.0]    | [-0.28, 0.62]  | [-253880.0, 228253.0]  |                0.824 | True       |            4962 | True       |    34.944 |          2367.78  |       -100752   | False        |
| G9x|no-entries-after-14:00                 | G       |   0.01  | 0.446 |          0.25  |  34139.8  |    1333.12  |     283865 |    16732.2   |         68 | [-1277.0, 3356.0]    | [-0.09, 0.3]   | [-138439.0, 28633.0]   |                0.564 | False      |            5045 | True       |    35.528 |          2407.39  |       -100752   | False        |
| G3|skip-14:00-15:00                        | G       |   0.01  | 0.446 |          0.25  |  34139.8  |    1333.12  |     283865 |    16732.2   |         68 | [-1277.0, 3356.0]    | [-0.09, 0.3]   | [-138439.0, 28633.0]   |                0.564 | False      |            5045 | True       |    35.528 |          2407.39  |       -100752   | False        |
| G7|flatten-16:00                           | G       |   0.009 | 0.446 |          0.247 |  34459.2  |    1652.55  |     267973 |      840     |         68 | [-955.0, 2757.0]     | [-0.07, 0.23]  | [-108356.0, 49086.0]   |                0.701 | True       |            5134 | True       |    36.155 |          2449.86  |       -100752   | False        |
| G2|skip-02:00-04:00                        | G       |   0.007 | 0.446 |          0.241 |  37370.8  |    4564.11  |     292005 |    24871.9   |         68 | [-6616.0, 9163.0]    | [-0.53, 0.57]  | [-166083.0, 276295.0]  |                0.527 | False      |            5117 | True       |    36.035 |          2441.75  |        -99417.1 | False        |
| G9x|no-entries-after-13:00                 | G       |   0.007 | 0.446 |          0.24  |  32751.6  |     -55.128 |     283865 |    16732.2   |         68 | [-3716.0, 3821.0]    | [-0.27, 0.33]  | [-153764.0, 153996.0]  |                0.472 | False      |            4933 | True       |    34.739 |          2353.94  |       -100752   | False        |
| G3|skip-11:30-14:00                        | G       |   0.007 | 0.446 |          0.238 |  33297.9  |     491.217 |     263931 |    -3202     |         68 | [-5932.0, 3412.0]    | [-0.35, 0.36]  | [-120522.0, 192017.0]  |                0.748 | True       |            4808 | True       |    33.859 |          2294.3   |       -100752   | False        |
| G15|sess-on-if-trail26w>0                  | G       |   0.003 | 0.446 |          0.216 |  30337.8  |   -2468.9   |     436676 |   169543     |         68 | [-9278.0, 5093.0]    | [-0.69, 0.32]  | [-188536.0, 300017.0]  |                0.518 | False      |            4858 | True       |    34.211 |          2318.16  |       -100752   | False        |
| G5|skip-20-21                              | G       |   0.002 | 0.446 |          0.202 |  26344.3  |   -6462.33  |     450999 |   183866     |         68 | [-11978.0, 1626.0]   | [-0.76, 0.17]  | [-90161.0, 281398.0]   |                0.703 | True       |            5021 | True       |    35.359 |          2395.94  |       -100752   | False        |
| G6|only-03-05+09:30-11:30                  | G       |   0.001 | 0.446 |          0.2   |  20614.5  |  -12192.2   |     271168 |     4034.55  |         68 | [-18988.0, 3503.0]   | [-1.11, 0.64]  | [-305426.0, 286361.0]  |                0.464 | False      |            3024 | True       |    21.296 |          1443     |       -101632   | False        |
| G20|skip-DST-weeks                         | G       |   0.001 | 0.446 |          0.195 |  27198.7  |   -5608.01  |     297823 |    30689.6   |         68 | [-10574.0, -904.0]   | [-0.67, -0.03] | [-50306.0, 249114.0]   |                0.63  | False      |            4682 | True       |    32.972 |          2234.17  |       -100752   | False        |
| G1|skip-21:00-02:00                        | G       |   0.001 | 0.446 |          0.178 |  26005.1  |   -6801.56  |     351103 |    83969.6   |         68 | [-16312.0, 1246.0]   | [-1.12, 0.11]  | [-119988.0, 453545.0]  |                0.721 | True       |            4957 | True       |    34.908 |          2365.4   |       -100552   | False        |
| G1|skip-18:05-21:00                        | G       |   0.001 | 0.446 |          0.177 |  34227.4  |    1420.69  |     490279 |   223146     |         68 | [-21656.0, 5125.0]   | [-1.45, 0.42]  | [-28185.0, 978892.0]   |                0.552 | False      |            4732 | True       |    33.324 |          2258.03  |        -99851.6 | False        |
| H16|zigzag60|size8_hi                      | H       |   0.054 | 0.446 |          0.311 |  39616.7  |    6810.02  |     316411 |    49277.6   |         68 | [-1366.0, 11839.0]   | [0.08, 0.96]   | [-333733.0, 32250.0]   |                0.732 | True       |            7182 | True       |    50.577 |          2477.81  |       -100752   | False        |
| H8|cc/parkinson|size8_hi                   | H       |   0.044 | 0.446 |          0.302 |  35216    |    2409.36  |     323595 |    56462     |         68 | [-470.0, 9443.0]     | [0.1, 0.85]    | [-347504.0, 30591.0]   |                0.482 | False      |            6581 | True       |    46.345 |          2484.69  |       -100752   | False        |
| H2|rv20/VXN|size8_hi                       | H       |   0.021 | 0.446 |          0.278 |  31875.3  |    -931.361 |     318267 |    51134.3   |         68 | [-4335.0, 7505.0]    | [-0.14, 0.75]  | [-330946.0, 49432.0]   |                0.673 | False      |            6933 | True       |    48.824 |          2422.8   |        -97591.6 | False        |
| H19|volfrac|size8_hi                       | H       |   0.022 | 0.446 |          0.276 |  32588.5  |    -218.162 |     334993 |    67860.1   |         68 | [-1691.0, 7359.0]    | [-0.08, 0.59]  | [-215115.0, 83603.0]   |                0.587 | False      |            5708 | True       |    40.197 |          2459.74  |       -100752   | False        |
| H20|printed-sec/30min|size8_hi             | H       |   0.022 | 0.446 |          0.276 |  34734.2  |    1927.47  |     265742 |    -1391.18  |         68 | [-34.0, 7050.0]      | [0.03, 0.54]   | [-162561.0, 50814.0]   |                0.638 | False      |            5323 | True       |    37.486 |          2374.19  |       -100752   | False        |
| H8|cc/parkinson|skip_hi                    | H       |   0.016 | 0.446 |          0.272 |  28878.6  |   -3928.06  |     263346 |    -3787.36  |         68 | [-8700.0, 5802.0]    | [-0.27, 0.79]  | [-361645.0, 68740.0]   |                0.586 | False      |            3386 | True       |    23.845 |          1615.74  |       -100752   | False        |
| H9|volvol|size8_hi                         | H       |   0.016 | 0.446 |          0.266 |  35297.6  |    2490.92  |     267133 |        0     |         68 | [-3738.0, 6892.0]    | [-0.16, 0.61]  | [-250528.0, 49086.0]   |                0.81  | True       |            6500 | True       |    45.775 |          2442.16  |       -100752   | False        |
| H3|dVIX1|size8_hi                          | H       |   0.013 | 0.446 |          0.259 |  34733.3  |    1926.64  |     484964 |   217831     |         68 | [-6551.0, 5833.0]    | [-0.31, 0.58]  | [-186333.0, 220308.0]  |                0.491 | False      |            6546 | True       |    46.099 |          2515.64  |       -100752   | False        |
| H16|zigzag60|skip_lo                       | H       |   0.011 | 0.446 |          0.255 |  34554    |    1747.37  |     289464 |    22331.2   |         68 | [-6555.0, 5945.0]    | [-0.38, 0.61]  | [-209718.0, 184365.0]  |                0.413 | False      |            4177 | True       |    29.415 |          1993.19  |       -100332   | False        |
| H20|printed-sec/30min|skip_hi              | H       |   0.011 | 0.446 |          0.253 |  34974.6  |    2167.9   |     260129 |    -7003.99  |         68 | [-5363.0, 5772.0]    | [-0.29, 0.52]  | [-144168.0, 152851.0]  |                0.487 | False      |            4590 | True       |    32.324 |          2190.27  |       -100752   | False        |
| H6|on/rth-RV|size8_hi                      | H       |   0.008 | 0.446 |          0.249 |  31260.3  |   -1546.33  |     456498 |   189365     |         68 | [-6631.0, 6801.0]    | [-0.41, 0.51]  | [-140658.0, 237215.0]  |                0.523 | False      |            6896 | True       |    48.563 |          2425.59  |        -97872.1 | False        |
| H17|garch/rv5|size8_hi                     | H       |   0.006 | 0.446 |          0.234 |  27684.9  |   -5121.77  |     331735 |    64601.9   |         68 | [-5929.0, 3316.0]    | [-0.3, 0.28]   | [-158540.0, 127612.0]  |                0.734 | True       |            5885 | True       |    41.444 |          2399.21  |       -100332   | False        |
| H2|rv20/VXN|skip_hi                        | H       |   0.003 | 0.446 |          0.232 |  23083.6  |   -9723.09  |     263346 |    -3787.36  |         68 | [-15313.0, 1816.0]   | [-0.68, 0.62]  | [-359722.0, 90214.0]   |                0.405 | False      |            2623 | True       |    18.472 |          1251.65  |        -97591.6 | False        |
| H16|zigzag60|skip_hi                       | H       |   0.004 | 0.446 |          0.227 |  23313.1  |   -9493.62  |     224138 |   -42995.5   |         68 | [-16561.0, 1843.0]   | [-0.84, 0.59]  | [-270849.0, 165863.0]  |                0.453 | False      |            2524 | True       |    17.775 |          1204.41  |       -100752   | False        |
| H3|dVIX1|skip_lo                           | H       |   0.004 | 0.446 |          0.222 |  29634.6  |   -3172.11  |     254007 |   -13126.2   |         68 | [-13210.0, 3688.0]   | [-0.77, 0.55]  | [-204677.0, 288953.0]  |                0.835 | True       |            3240 | True       |    22.817 |          1546.07  |       -100752   | False        |
| H10|hurst|skip_hi                          | H       |   0.002 | 0.446 |          0.216 |  25735.1  |   -7071.57  |     239153 |   -27979.7   |         68 | [-13957.0, 2931.0]   | [-0.8, 0.45]   | [-240081.0, 209410.0]  |                0.585 | False      |            3644 | True       |    25.662 |          1738.86  |       -100752   | False        |
| H19|volfrac|skip_hi                        | H       |   0.002 | 0.446 |          0.204 |  28174.7  |   -4631.98  |     317462 |    50328.9   |         68 | [-10906.0, 136.0]    | [-0.73, 0.06]  | [-114262.0, 352348.0]  |                0.509 | False      |            4399 | True       |    30.979 |          2099.13  |       -100752   | False        |
| H17|garch/rv5|skip_hi                      | H       |   0.002 | 0.446 |          0.204 |  21205.5  |  -11601.2   |     315757 |    48624.3   |         68 | [-11773.0, 440.0]    | [-0.67, 0.28]  | [-213003.0, 207399.0]  |                0.666 | False      |            3896 | True       |    27.437 |          1859.11  |       -100332   | False        |
| H9|volvol|skip_hi                          | H       |   0.001 | 0.446 |          0.196 |  28701.1  |   -4105.59  |     276893 |     9759.73  |         68 | [-16605.0, -1257.0]  | [-0.84, 0.21]  | [-230382.0, 147827.0]  |                0.642 | False      |            3299 | True       |    23.232 |          1574.23  |       -100752   | False        |
| H7|only-falling                            | H       |   0.001 | 0.446 |          0.194 |  24516.4  |   -8290.24  |     227528 |   -39605     |         68 | [-17341.0, -2165.0]  | [-0.88, 0.33]  | [-217048.0, 246273.0]  |                0.501 | False      |            2523 | True       |    17.768 |          1203.93  |       -100752   | False        |
| I3|RTY/NQ-mom|s8                           | I       |   0.092 | 0.446 |          0.333 |  43931.2  |   11124.5   |     344405 |    77271.7   |         68 | [2847.0, 17043.0]    | [0.21, 1.2]    | [-226305.0, 98043.0]   |                0.428 | False      |            6429 | True       |    45.275 |          2419.52  |        -93504.7 | False        |
| I4|ZN|rel-|s8                              | I       |   0.038 | 0.446 |          0.298 |  38658.8  |    5852.09  |     298216 |    31083.1   |         68 | [-158.0, 13850.0]    | [-0.04, 0.9]   | [-249000.0, 117671.0]  |                0.532 | False      |            6306 | True       |    44.408 |          2417.07  |        -96681.1 | False        |
| I5|6E|rel+|s8                              | I       |   0.033 | 0.446 |          0.294 |  44888.1  |   12081.5   |     303693 |    36560.1   |         68 | [-3571.0, 13157.0]   | [-0.27, 0.89]  | [-201878.0, 264860.0]  |                0.614 | False      |            6230 | True       |    43.873 |          2425.59  |       -102018   | False        |
| I19|gapdiv-NY|s8                           | I       |   0.028 | 0.446 |          0.284 |  36008.3  |    3201.64  |     282382 |    15249     |         68 | [357.0, 7651.0]      | [0.08, 0.63]   | [-169630.0, 49004.0]   |                0.393 | False      |            5271 | True       |    37.12  |          2393.35  |       -100752   | False        |
| I17|size8-if-corr>0                        | I       |   0.024 | 0.446 |          0.279 |  31272.9  |   -1533.79  |     306509 |    39375.7   |         68 | [-5451.0, 7102.0]    | [-0.22, 0.72]  | [-261168.0, 112811.0]  |                0.641 | False      |            7031 | True       |    49.514 |          2447.47  |       -100752   | False        |
| I19|gapdiv-NY|perm                         | I       |   0.02  | 0.446 |          0.273 |  35801.6  |    2994.96  |     276133 |     9000.27  |         68 | [-2322.0, 7567.0]    | [-0.1, 0.62]   | [-140333.0, 144346.0]  |                0.664 | False      |            4741 | True       |    33.387 |          2262.32  |       -100752   | False        |
| I4|ZN|rel+|s8                              | I       |   0.016 | 0.446 |          0.271 |  37566.2  |    4759.53  |     368167 |   101034     |         68 | [-5573.0, 11002.0]   | [-0.24, 0.81]  | [-221491.0, 164818.0]  |                0.651 | False      |            6209 | True       |    43.725 |          2414.95  |        -95281.7 | False        |
| I16|meanabscorr|size8_hi                   | I       |   0.018 | 0.446 |          0.27  |  34118.2  |    1311.5   |     307658 |    40525.1   |         68 | [-2867.0, 6952.0]    | [-0.15, 0.49]  | [-100615.0, 118395.0]  |                0.692 | False      |            6574 | True       |    46.296 |          2471.95  |       -100332   | False        |
| I8|GC|rel+|s8                              | I       |   0.018 | 0.446 |          0.269 |  39248.4  |    6441.77  |     343641 |    76508.2   |         68 | [-4776.0, 9925.0]    | [-0.26, 0.68]  | [-201307.0, 159662.0]  |                0.791 | True       |            6286 | True       |    44.268 |          2448.02  |        -94713.7 | False        |
| I12|resid-mom|s8                           | I       |   0.018 | 0.446 |          0.268 |  28638    |   -4168.65  |     431167 |   164034     |         68 | [-4848.0, 9849.0]    | [-0.26, 0.69]  | [-168716.0, 268062.0]  |                0.719 | True       |            5795 | True       |    40.81  |          2391.03  |        -94569.4 | False        |
| I18|NKD-london|perm                        | I       |   0.014 | 0.446 |          0.258 |  25141.6  |   -7665.1   |     312834 |    45700.8   |         68 | [-7981.0, 9394.0]    | [-0.49, 0.82]  | [-288188.0, 219565.0]  |                0.468 | False      |            4944 | True       |    34.817 |          2359.19  |        -98121.6 | False        |
| I20|relvol|size8_hi                        | I       |   0.011 | 0.446 |          0.257 |  44463.9  |   11657.3   |     472334 |   205201     |         68 | [-10355.0, 12818.0]  | [-0.69, 0.75]  | [-134789.0, 452754.0]  |                0.55  | False      |            6893 | True       |    48.542 |          2596.35  |        -93876.4 | False        |
| I18|NKD-london|s8                          | I       |   0.012 | 0.446 |          0.256 |  29777.5  |   -3029.18  |     315435 |    48302.4   |         68 | [-3601.0, 8661.0]    | [-0.27, 0.59]  | [-219818.0, 103893.0]  |                0.576 | False      |            5464 | True       |    38.479 |          2457.63  |        -99587.1 | False        |
| I5|6E|rel+|perm                            | I       |   0.01  | 0.446 |          0.254 |  35802    |    2995.31  |     386156 |   119023     |         68 | [-13117.0, 12222.0]  | [-0.86, 1.03]  | [-154176.0, 569752.0]  |                0.513 | False      |            4123 | True       |    29.035 |          1967.43  |       -102385   | False        |
| I10|VX-slope(F2/F1-1, daily-only)|size8_hi | I       |   0.01  | 0.446 |          0.249 |  31421.4  |   -1385.27  |     306509 |    39375.7   |         68 | [-5899.0, 5850.0]    | [-0.32, 0.49]  | [-175802.0, 174839.0]  |                0.506 | False      |            6053 | True       |    42.627 |          2350.33  |       -100752   | False        |
| I2|beta-drift|skip_lo                      | I       |   0.009 | 0.446 |          0.249 |  33348.7  |     541.999 |     410668 |   143535     |         68 | [-11533.0, 13618.0]  | [-0.75, 1.0]   | [-215243.0, 408414.0]  |                0.584 | False      |            4578 | True       |    32.239 |          2184.54  |       -100937   | False        |
| I9|BTC-asia|s8                             | I       |   0.008 | 0.446 |          0.247 |  41531    |    8724.33  |     332873 |    65739.5   |         68 | [-6235.0, 10435.0]   | [-0.52, 0.56]  | [-136831.0, 243388.0]  |                0.445 | False      |            5583 | True       |    39.317 |          2452.86  |       -100752   | False        |
| I20|relvol|skip_lo                         | I       |   0.009 | 0.446 |          0.245 |  26254.2  |   -6552.49  |     245324 |   -21809.1   |         68 | [-8983.0, 6845.0]    | [-0.54, 0.68]  | [-269895.0, 209362.0]  |                0.361 | False      |            4245 | True       |    29.894 |          2025.64  |       -100752   | False        |
| I16|meanabscorr|size20_lo                  | I       |   0.008 | 0.446 |          0.24  |  29201.2  |   -3605.52  |     267133 |        0     |         68 | [-5045.0, 6577.0]    | [-0.37, 0.39]  | [-161310.0, 167024.0]  |                0.429 | False      |            4640 | True       |    32.676 |          2490.21  |       -114374   | False        |
| I10|VX-slope(F2/F1-1, daily-only)|skip_lo  | I       |   0.005 | 0.446 |          0.238 |  29468.6  |   -3338.11  |     267133 |        0     |         68 | [-14384.0, 1558.0]   | [-0.67, 0.51]  | [-332169.0, 106377.0]  |                0.648 | False      |            3367 | True       |    23.711 |          1606.67  |       -100752   | False        |
| J16|qend-size8                             | J       |   0.011 | 0.446 |          0.253 |  36654.3  |    3847.67  |     267133 |        0     |         68 | [-1721.0, 4660.0]    | [-0.11, 0.37]  | [-136863.0, 44706.0]   |                0.709 | True       |            5316 | True       |    37.437 |          2454.9   |       -100752   | False        |
| J8|thu-skip-08-09                          | J       |   0.008 | 0.446 |          0.245 |  30721.6  |   -2085.06  |     283865 |    16732.2   |         68 | [-1118.0, 3444.0]    | [-0.1, 0.2]    | [-73187.0, 49531.0]    |                0.7   | True       |            5086 | True       |    35.817 |          2426.95  |       -100752   | False        |
| J16|qend-skip                              | J       |   0.007 | 0.446 |          0.243 |  35568.2  |    2761.52  |     267133 |        0     |         68 | [-4121.0, 4682.0]    | [-0.26, 0.38]  | [-136495.0, 92316.0]   |                0.508 | False      |            4916 | True       |    34.62  |          2345.83  |       -100752   | False        |
| J18|dec-rebalance-skip                     | J       |   0.006 | 0.446 |          0.236 |  33236.1  |     429.432 |     267133 |        0     |         68 | [-2015.0, 562.0]     | [-0.08, 0.02]  | [-15058.0, 0.0]        |                0.774 | True       |            5057 | True       |    35.613 |          2413.11  |       -100752   | False        |
| J14|qw-size8                               | J       |   0.006 | 0.446 |          0.235 |  32989.8  |     183.128 |     267133 |        0     |         68 | [-1321.0, 456.0]     | [-0.08, 0.02]  | [-8654.0, 34758.0]     |                0.508 | False      |            5134 | True       |    36.155 |          2422.25  |       -100752   | False        |
| J14|qw-skip                                | J       |   0.006 | 0.446 |          0.235 |  32340.3  |    -466.355 |     267133 |        0     |         68 | [-2901.0, 1330.0]    | [-0.15, 0.08]  | [-33320.0, 56287.0]    |                0.417 | False      |            4999 | True       |    35.204 |          2385.44  |       -100752   | False        |
| J2|skip-13-15                              | J       |   0.006 | 0.446 |          0.234 |  32335.5  |    -471.194 |     267133 |        0     |         68 | [-1165.0, 55.0]      | [-0.08, 0.0]   | [-248.0, 33464.0]      |                0.525 | False      |            5088 | True       |    35.831 |          2427.91  |       -100752   | False        |
| J8|thu-skip-07:30-10                       | J       |   0.003 | 0.446 |          0.213 |  25041.3  |   -7765.37  |     377801 |   110668     |         68 | [-6637.0, 54.0]      | [-0.44, 0.03]  | [-42609.0, 165732.0]   |                0.723 | True       |            5034 | True       |    35.451 |          2402.14  |       -100752   | False        |
| J2|skip-day                                | J       |   0.003 | 0.446 |          0.213 |  30456.6  |   -2350.05  |     267133 |        0     |         68 | [-5474.0, -512.0]    | [-0.42, -0.01] | [-30605.0, 123983.0]   |                0.538 | False      |            4985 | True       |    35.106 |          2378.76  |       -100752   | False        |
| K19|va-pos|skip_lo                         | K       |   0.068 | 0.446 |          0.32  |  46899.9  |   14093.2   |     270141 |     3007.72  |         68 | [-1853.0, 18277.0]   | [-0.08, 1.36]  | [-269988.0, 221558.0]  |                0.605 | False      |            4784 | True       |    33.69  |          2282.84  |       -101217   | False        |
| K10|refills30|size8_hi                     | K       |   0.035 | 0.446 |          0.292 |  38243.7  |    5437.01  |     267463 |      330.047 |         68 | [329.0, 9102.0]      | [0.07, 0.73]   | [-207915.0, 39951.0]   |                0.552 | False      |            5370 | True       |    37.817 |          2382.51  |       -100752   | False        |
| K14|imb-persist|size8_hi                   | K       |   0.025 | 0.446 |          0.286 |  37905.4  |    5098.67  |     359991 |    92858.1   |         68 | [-4135.0, 12694.0]   | [-0.2, 0.88]   | [-258936.0, 116478.0]  |                0.527 | False      |            6087 | True       |    42.866 |          2549.39  |       -100752   | False        |
| K9|sweeps15|skip_hi                        | K       |   0.029 | 0.446 |          0.285 |  37170.1  |    4363.37  |     250536 |   -16597.4   |         68 | [-4933.0, 8076.0]    | [-0.11, 0.88]  | [-273219.0, 98561.0]   |                0.428 | False      |            4475 | True       |    31.514 |          2135.39  |       -100752   | False        |
| K9|sweeps15|size8_hi                       | K       |   0.023 | 0.446 |          0.278 |  36726.4  |    3919.77  |     267463 |      330.047 |         68 | [-1190.0, 7267.0]    | [-0.01, 0.62]  | [-212797.0, 49170.0]   |                0.543 | False      |            5416 | True       |    38.141 |          2360.69  |       -100752   | False        |
| K13|cancel-ratio|skip_lo                   | K       |   0.02  | 0.446 |          0.277 |  47520.3  |   14713.7   |     385513 |   118380     |         68 | [-11353.0, 16560.0]  | [-0.71, 1.21]  | [-206990.0, 457224.0]  |                0.615 | False      |            4307 | True       |    30.331 |          2055.23  |        -99851.6 | False        |
| K15|through15|size8_hi                     | K       |   0.021 | 0.446 |          0.275 |  35501.9  |    2695.26  |     267463 |      330.047 |         68 | [-2113.0, 7380.0]    | [-0.09, 0.62]  | [-207074.0, 74926.0]   |                0.456 | False      |            5386 | True       |    37.93  |          2351.9   |       -100752   | False        |
| K13|cancel-ratio|size8_hi                  | K       |   0.02  | 0.446 |          0.274 |  35760    |    2953.29  |     330254 |    63120.6   |         68 | [-1962.0, 7668.0]    | [-0.13, 0.62]  | [-196729.0, 148098.0]  |                0.613 | False      |            5421 | True       |    38.176 |          2358.17  |       -100752   | False        |
| K4|msg-burst|skip_hi                       | K       |   0.02  | 0.446 |          0.273 |  36090.3  |    3283.64  |     298782 |    31649.3   |         68 | [-9812.0, 9905.0]    | [-0.42, 0.97]  | [-273276.0, 186870.0]  |                0.487 | False      |            4523 | True       |    31.852 |          2158.3   |       -101372   | False        |
| K7|eff-spread15|size8_hi                   | K       |   0.018 | 0.446 |          0.271 |  33037.6  |     230.94  |     433828 |   166695     |         68 | [-7519.0, 11594.0]   | [-0.47, 0.82]  | [-221829.0, 266370.0]  |                0.666 | False      |            7639 | True       |    53.796 |          2623.07  |        -93096.7 | False        |
| K10|refills30|skip_hi                      | K       |   0.019 | 0.446 |          0.269 |  37733.3  |    4926.65  |     253556 |   -13576.7   |         68 | [-5007.0, 7051.0]    | [-0.22, 0.67]  | [-180779.0, 113806.0]  |                0.465 | False      |            4587 | True       |    32.303 |          2188.84  |       -100752   | False        |
| K15|through15|skip_hi                      | K       |   0.018 | 0.446 |          0.266 |  35984.4  |    3177.68  |     253556 |   -13576.7   |         68 | [-6552.0, 7571.0]    | [-0.29, 0.77]  | [-225791.0, 158196.0]  |                0.534 | False      |            4463 | True       |    31.43  |          2129.67  |       -100752   | False        |
| K20|or-skew|skip_lo                        | K       |   0.015 | 0.446 |          0.263 |  32882.1  |      75.451 |     366527 |    99393.6   |         68 | [-2802.0, 6351.0]    | [-0.14, 0.56]  | [-173561.0, 126464.0]  |                0.615 | False      |            4872 | True       |    34.31  |          2324.84  |       -100752   | False        |
| K13|cancel-ratio|skip_hi                   | K       |   0.009 | 0.446 |          0.25  |  37572.1  |    4765.44  |     283128 |    15994.6   |         68 | [-7294.0, 5428.0]    | [-0.4, 0.52]   | [-232131.0, 117964.0]  |                0.476 | False      |            4387 | True       |    30.894 |          2093.4   |       -100752   | False        |
| K17|poc-dist|size8_hi                      | K       |   0.009 | 0.446 |          0.249 |  32186.6  |    -620.103 |     355492 |    88358.7   |         68 | [-4250.0, 6079.0]    | [-0.31, 0.43]  | [-194174.0, 108790.0]  |                0.752 | True       |            5467 | True       |    38.5   |          2485.03  |       -100332   | False        |
| K12|depth-slope-consumed|size8_hi          | K       |   0.009 | 0.446 |          0.247 |  33280.4  |     473.742 |     281014 |    13880.5   |         68 | [-3066.0, 4793.0]    | [-0.24, 0.34]  | [-121801.0, 135102.0]  |                0.734 | True       |            5216 | True       |    36.732 |          2377.53  |       -100752   | False        |
| K8|sweep-impact|size8_hi                   | K       |   0.008 | 0.446 |          0.244 |  35439.7  |    2633     |     388288 |   121155     |         68 | [-4619.0, 5630.0]    | [-0.31, 0.4]   | [-130433.0, 146447.0]  |                0.659 | False      |            5375 | True       |    37.852 |          2412.09  |       -100752   | False        |
| K16|micro-mid|skip_lo                      | K       |   0.006 | 0.446 |          0.242 |  33463.7  |     657.004 |     309382 |    42249.4   |         68 | [-13419.0, 8338.0]   | [-0.8, 0.74]   | [-176851.0, 396081.0]  |                0.769 | True       |            4590 | True       |    32.324 |          2190.27  |        -99597.2 | False        |
| K12|depth-slope-consumed|skip_hi           | K       |   0.007 | 0.446 |          0.241 |  26846.7  |   -5959.95  |     349849 |    82716     |         68 | [-6576.0, 5145.0]    | [-0.45, 0.38]  | [-152954.0, 129460.0]  |                0.532 | False      |            4799 | True       |    33.796 |          2290     |       -100752   | False        |
| K16|micro-mid|size8_lo                     | K       |   0.006 | 0.446 |          0.238 |  35674.2  |    2867.53  |     537825 |   270692     |         68 | [-8462.0, 7789.0]    | [-0.58, 0.48]  | [-114577.0, 374595.0]  |                0.468 | False      |            5866 | True       |    41.31  |          2427.16  |        -94283.9 | False        |
| L5|shrink-k100                             | L       |   0.032 | 0.446 |          0.289 |  32806.7  |       0     |     267133 |        0     |         68 | [772.0, 9454.0]      | [0.05, 0.72]   | [-308168.0, 25297.0]   |                0.97  | True       |            5325 | True       |    37.5   |          2452.04  |       -100752   | False        |
| L5|shrink-k30                              | L       |   0.028 | 0.446 |          0.284 |  32806.7  |       0     |     267133 |        0     |         68 | [-172.0, 8797.0]     | [0.01, 0.7]    | [-305471.0, 27146.0]   |                0.934 | True       |            5322 | True       |    37.479 |          2444.47  |       -100752   | False        |
| L3|size8-if-q50<0                          | L       |   0.019 | 0.446 |          0.273 |  36260.5  |    3453.8   |     340635 |    73501.4   |         68 | [-2403.0, 10708.0]   | [-0.16, 0.69]  | [-202684.0, 180707.0]  |                0.465 | False      |            6031 | True       |    42.472 |          2466.01  |       -100332   | False        |
| L16|conformal-width-top3rd->8              | L       |   0.014 | 0.446 |          0.261 |  36049    |    3242.34  |     378371 |   111238     |         68 | [-1531.0, 8272.0]    | [-0.16, 0.51]  | [-110743.0, 155753.0]  |                0.587 | False      |            5336 | True       |    37.577 |          2424.16  |       -100752   | False        |
| L9|kernel-h1.0-skip<0                      | L       |   0.009 | 0.446 |          0.252 |  33593.4  |     786.765 |     267133 |        0     |         68 | [-2809.0, 6872.0]    | [-0.24, 0.41]  | [-122321.0, 203774.0]  |                0.863 | True       |            4881 | True       |    34.373 |          2329.13  |       -100752   | False        |
| L12|kmeans12-skip-neg                      | L       |   0.009 | 0.446 |          0.251 |  35839.6  |    3032.93  |     287937 |    20804.1   |         68 | [-10358.0, 9637.0]   | [-0.66, 0.75]  | [-262516.0, 253463.0]  |                0.472 | False      |            4514 | True       |    31.789 |          2154.01  |       -100332   | False        |
| L2|iso-p<.45->8,>.55->20                   | L       |   0.01  | 0.446 |          0.251 |  33554.4  |     747.765 |     272931 |     5798.2   |         68 | [-2975.0, 5019.0]    | [-0.2, 0.39]   | [-178136.0, 111385.0]  |                0.682 | False      |            5047 | True       |    35.542 |          2444.54  |       -100752   | False        |
| L8|bocpd>0.5->8                            | L       |   0.009 | 0.446 |          0.246 |  32806.7  |       0     |     267133 |        0     |         68 | [0.0, 1486.0]        | [0.0, 0.09]    | [-34006.0, 0.0]        |                1     | True       |            5169 | True       |    36.401 |          2434.25  |       -100752   | False        |
| L8|bocpd>0.8->8                            | L       |   0.007 | 0.446 |          0.239 |  32806.7  |       0     |     267133 |        0     |         68 | [-0.0, 0.0]          | [0.0, 0.0]     | [-0.0, 0.0]            |                0.722 | True       |            5101 | True       |    35.923 |          2434.11  |       -100752   | False        |
| L10|rf-pnl-regime<.45->8                   | L       |   0.007 | 0.446 |          0.239 |  32806.7  |       0     |     267133 |        0     |         68 | [-0.0, 0.0]          | [0.0, 0.0]     | [-0.0, 0.0]            |                0.722 | True       |            5101 | True       |    35.923 |          2434.11  |       -100752   | False        |
| L17|gmm-low-mean-regime->8                 | L       |   0.004 | 0.446 |          0.224 |  28041.8  |   -4764.85  |     360560 |    93427.2   |         68 | [-8336.0, 2953.0]    | [-0.53, 0.34]  | [-196136.0, 198127.0]  |                0.515 | False      |            6321 | True       |    44.514 |          2408.28  |       -100752   | False        |
| L12|kmeans6-skip-neg                       | L       |   0.002 | 0.446 |          0.208 |  33212    |     405.31  |     267133 |        0     |         68 | [-9627.0, 1238.0]    | [-0.65, 0.1]   | [-109001.0, 303483.0]  |                0.949 | True       |            4846 | True       |    34.127 |          2312.43  |       -100752   | False        |
| L1|size8-below-p40                         | L       |   0.002 | 0.446 |          0.202 |  27854.8  |   -4951.86  |     255864 |   -11269.5   |         68 | [-10942.0, 3944.0]   | [-0.78, 0.18]  | [-132866.0, 271521.0]  |                0.811 | True       |            5736 | True       |    40.394 |          2424.02  |        -98179.3 | False        |
| L6|online-RLS-skip<0                       | L       |   0.001 | 0.446 |          0.192 |  21358.2  |  -11448.5   |     454765 |   187632     |         68 | [-13649.0, 4952.0]   | [-0.98, 0.35]  | [-165193.0, 462876.0]  |                0.551 | False      |            4657 | True       |    32.796 |          2222.24  |       -100857   | False        |
| L11|PC2-skip_lo                            | L       |   0.001 | 0.446 |          0.179 |  29695.4  |   -3111.27  |     406505 |   139372     |         68 | [-16824.0, 2571.0]   | [-1.13, 0.31]  | [-137919.0, 474655.0]  |                0.585 | False      |            4134 | True       |    29.113 |          1972.67  |        -98561.6 | False        |
| L9|kernel-h0.5-skip<0                      | L       |   0.001 | 0.446 |          0.172 |  25530.2  |   -7276.44  |     308808 |    41675.2   |         68 | [-16548.0, -2455.0]  | [-1.06, 0.06]  | [-87258.0, 448212.0]   |                0.707 | True       |            4695 | True       |    33.063 |          2240.38  |       -100752   | False        |
| L11|PC3-skip_lo                            | L       |   0     | 0.446 |          0.153 |   9799.3  |  -23007.4   |     572329 |   305196     |         68 | [-22572.0, 664.0]    | [-1.52, 0.22]  | [-66344.0, 803933.0]   |                0.78  | True       |            4259 | True       |    29.993 |          2032.32  |        -98547.1 | False        |
| L1|skip-below-p35                          | L       |   0     | 0.446 |          0.144 |  19726.8  |  -13079.9   |     385844 |   118711     |         68 | [-19847.0, -2542.0]  | [-1.36, -0.11] | [-97789.0, 499599.0]   |                0.484 | False      |            4697 | True       |    33.077 |          2241.33  |       -100832   | False        |
| L11|PC1-skip_lo                            | L       |   0     | 0.446 |          0.118 |   9919.63 |  -22887.1   |     462734 |   195601     |         68 | [-27875.0, -4456.0]  | [-1.89, -0.04] | [-42301.0, 1017546.0]  |                0.477 | False      |            3841 | True       |    27.049 |          1832.86  |       -100752   | False        |
| L3|skip-if-q20<0                           | L       | nan     | 0.446 |        nan     |      0    |  -32806.7   |          0 |  -267133     |         68 | [-35924.0, -14844.0] | [nan, nan]     | [-686200.0, -275089.0] |                0.482 | False      |               0 | False      |     0     |             0     |        -79106   | True         |
| M8|invsd-L40                               | M       |   0.015 | 0.446 |          0.263 |  37246.7  |    4439.99  |     351136 |    84003.1   |         68 | [-1482.0, 10427.0]   | [-0.16, 0.59]  | [-121538.0, 201837.0]  |                0.784 | True       |            5240 | True       |    36.901 |          2471.17  |        -99328.9 | False        |
| M13|corr>0.6->10                           | M       |   0.009 | 0.446 |          0.248 |  34278.9  |    1472.23  |     288489 |    21355.6   |         68 | [-1619.0, 3441.0]    | [-0.11, 0.21]  | [-102729.0, 37033.0]   |                0.543 | False      |            5631 | True       |    39.655 |          2439.84  |       -100752   | False        |
| M13|corr>0.8->10                           | M       |   0.007 | 0.446 |          0.241 |  32806.7  |       0     |     267133 |        0     |         68 | [0.0, 503.0]         | [0.0, 0.04]    | [-28328.0, 0.0]        |                1     | True       |            5116 | True       |    36.028 |          2431.04  |       -100752   | False        |
| M8|invsd-L65                               | M       |   0.006 | 0.446 |          0.231 |  30028.1  |   -2778.55  |     310030 |    42897     |         68 | [-6020.0, 5230.0]    | [-0.41, 0.35]  | [-93463.0, 217985.0]   |                0.444 | False      |            5191 | True       |    36.556 |          2450.03  |        -97136   | False        |
| E5|ES15m-agree14-else8                     | E       |   0.007 | 0.446 |          0.244 |  30873.9  |   -1932.82  |     299485 |    32351.5   |         68 | [-6547.0, 8512.0]    | [-0.42, 0.52]  | [-222056.0, 122795.0]  |                0.446 | False      |            5573 | True       |    39.246 |          2404.93  |        -98502.4 | False        |
| E11|ST10-HM10                              | E       |   0.008 | 0.446 |          0.246 |  37233.3  |    4426.63  |     362443 |    95310.1   |         68 | [-7765.0, 7128.0]    | [-0.48, 0.48]  | [-163523.0, 219618.0]  |                0.562 | False      |            7255 | True       |    51.092 |          2472.83  |        -83854   | True         |

## 6. Not run / duplicate list

- B1 NOTRUN: not meaningful live already enters at the open of the bar after the flip bar = the flip-bar close print; no distinct alternative
- D8 NOTRUN: data gap VIX 1-min not on disk (CBOE daily only; no VX/VIX intraday); Q14
- D14 NOTRUN: not meaningful live flattens at 16:55 before the 17:00 break; nothing open at the break
- F20 NOTRUN: data gap broker rejection counts: live-only, no log on disk
- I10 NOTRUN: data gap VX futures curve not on disk
- J10 NOTRUN: data gap Fed-speaker calendar not on disk
- K11 NOTRUN: data gap resting-order age needs order-level (MBO) ids; 1-s tables carry state staleness only
- L4 NOTRUN: not meaningful symmetric bracket: time-to-event adds nothing for sizing beyond L1/L2 probability; exits are bracket-only
- L18 NOTRUN: dependency needs the V6-F1 learned policy; revisit after V6
- M16 NOTRUN: data gap VX short-vol book: no VX
- M17 NOTRUN: data gap long-vol tail hedge cost: no VX/VIX options on disk
- N13 NOTRUN: live-only reject handling: no reject model in the replay
- N14 NOTRUN: operational orphan-order sweep: infrastructure, not a P&L rule
- N15 NOTRUN: operational heartbeat: infrastructure
- N16 NOTRUN: live-only broker latency monitor: live ack times not on disk
- N17 NOTRUN: live-only Rithmic OCO vs NT8-simulated OCO: not replayable
- N19 NOTRUN: operational second connection: infrastructure
- N20 NOTRUN: operational DAY vs GTC brackets: positions are flat before 17:00
- M18 SKIP: directive "cash-equity overlay? no - skip"
- J20 REPORT:  Jan-effect / month-of-year P&L table for the benchmark (report only, no trading cell)
- L13 REPORT: F-penalized GA over subsets of the top-12 filter cells of this directive, fit on <=2025-06, scored on 2025-07..2026-10; report-only
- M19 REPORT:  drawdown-matched portfolio weights of benchmark + best sleeves; report-only table
- L20 DIAG:  adversarial validation AUC (IS vs OOS months) on the trade feature table: diagnostic only
- D20 CONTROL:  no exit rules except bracket and session flatten = the benchmark itself (reproduction row)

DUPLICATES (scored earlier, not re-run): A9<-50#1; A14<-V4-W3 / V5-E1; A18<-15#7; B2<-15#7; B4<-V2-5.3 / 15#15; B7<-S-C3; B17<-50#6; C20<-P9 arms (EM vs S14x1); D5<-15#13; D13<-L2-L7; E3<-15#14; E8<-V2 part 3 / V3-V2; E9<-S-C8; E10<-50#21; E16<-V3-V4 (fractional via MNQ); E18<-E17 / M12; E20<-V2 part 4 / V6-F; F3<-V6-D1 / 50#40 / S-C1; F6<-V5-A3; F9<-50#48; G8<-15#13; G10<-50#27; G11<-S-C7; G12<-S-C7; G13<-50#26; G14<-50#20 / V5-D1; G16<-50#44; G17<-C1 / V3-V5 session k; G18<-50#26; G19<-50#26; H1<-S-A3 / S-A4; H4<-50#30 / S-A2; H5<-50#29; H13<-50#16; H14<-50#16; H15<-50#18; H18<-V6-E1; I1<-50#33; I6<-50#34; I7<-50#34; I13<-15#5; I14<-50#8; I15<-D7; J1<-50#23; J3<-50#23 / S-C4; J4<-50#23 / S-C4; J5<-50#24 / S-C4; J6<-50#24; J7<-50#24; J9<-50#24; J11<-50#25; J12<-S-C4; J13<-50#22; J15<-50#22; J17<-S-C4 / 50#28; J19<-50#26; K1<-P1a; K2<-P1a; K3<-P1a; K5<-P1b / L2-L14; K6<-L2-L5 (queue model); L7<-V4-W3c / V5-E2; L14<-V5-D1; L15<-V4 / V5-E2; L19<-V6-F3; M1<-50#45; M5<-50#47 / V2-5.1; M6<-50#47; M7<-N18; M9<-50#43; M10<-F17; M11<-15#4; M12<-S-C5; N8<-L2-L3 / A3

## 7. Block N (execution variants; added after the lead approved the sample-month replay)
Addendum PREREG_DS2_300_N.md (own sha in DECISIONS.md, frozen before scoring). Paired entry-program replays on the raw NQ mbp-10 book (exec_engine_l2, same engine/queue model as P9, 5 ms latency) on the same benchmark trades, against the P9 entry S14x1 replayed in the same run. EXECUTION cells: no gates c/d (no timing null exists for an execution program), not eligible for FOUND; weekly deltas are PARTIAL coverage (replayed months only, no lock interplay).

Months replayed (18): 2023-08, 2023-11, 2024-02, 2024-04, 2024-07, 2024-10, 2025-01, 2025-03, 2025-05, 2025-08, 2025-10, 2025-12, 2026-02, 2026-05, 2026-07, 2026-08, 2026-09, 2026-10. Paired vs P9 S14x1 on the same trades; entry excess in ticks per lot (adverse>0, full-size fills only); dpts = net $ per trade difference (pts x lots x $20, plus saved fees for lots not traded); CI = day-block bootstrap 90%; dweekly = mean $/week over covered weeks (PARTIAL coverage, no lock interplay).

| arm   |   months |   trades_base |   share_traded |   share_full_size |   entry_excess_ticks_mean |   entry_excess_ticks_median |   dpts_usd_per_trade |   ci90_lo |   ci90_hi |   dweekly_usd_covered_weeks |   weeks |   base_pts_per_trade_usd |
|:------|---------:|--------------:|---------------:|------------------:|--------------------------:|----------------------------:|---------------------:|----------:|----------:|----------------------------:|--------:|-------------------------:|
| N1    |       18 |          6416 |          1     |             1     |                    -0.026 |                       0     |                -5.45 |    -17.15 |      6.14 |                        -393 |      89 |                    548.7 |
| N2    |       18 |          6416 |          1     |             1     |                     0.308 |                       0.286 |               -46.15 |    -74.65 |    -17.41 |                       -3327 |      89 |                    548.7 |
| N3    |       18 |          6416 |          1     |             1     |                    -0.045 |                      -0.143 |                 3.92 |      0.2  |      7.66 |                         292 |      86 |                    548.7 |
| N4a   |       18 |          6416 |          1     |             0.719 |                     0     |                       0     |                28.52 |    -85.99 |    148.55 |                        2127 |      86 |                    548.7 |
| N4b   |       18 |          6416 |          1     |             0.839 |                     0     |                       0     |                23.41 |    -55.93 |    101.48 |                        1854 |      81 |                    548.7 |
| N6    |       18 |          6416 |          0.059 |             1     |                     1.799 |                       2.286 |              -518.81 |   -801.68 |   -232.54 |                      -49158 |       4 |                   2014.6 |
| N10   |       18 |          6416 |          1     |             1     |                     0.762 |                       1.429 |              -205.7  |   -280.1  |   -129.03 |                      -14829 |      89 |                    548.7 |

Reading: entry excess is in ticks per lot, adverse > 0 (a positive number = worse fill than S14x1). N4/N6 trade fewer lots or miss trades by design, so their dollar column includes the foregone trade P&L; N6 share_traded is the stop-limit fill rate.

N18 cost model: N18 cost model: fees per trade 14 NQ $67.76 vs 10 NQ + 40 MNQ $119.60 (delta $51.84); at 35.9 trades/wk = $-1,862/wk; S113 clip credit upper bound $43/trade = $1,542/wk. Mapping only.

### Updated NOT RUN list (Block N)
- N5 not meaningful (the 26 s entry sits inside the entry minute, the 1-min state cannot change); N7 engine lacks a per-60-s target ratchet; N9 engine has only the 240-tick bracket stop (the 20-pt catastrophe is an exit-arm policy, not a parameter); N11 no sliced session flatten; N12 no netting/reversal model; N8 DUP of L2-L3; N13-N17, N19, N20 live-only/operational.
- Elsewhere unchanged: D8, F20, I10 intraday, J10 and PPI part of J3, K11, L4, L18, M15-M17, O1, O4, O8 (see section 6); I10 ran DAILY-ONLY.
- Data inventory for the 1-min series: l2vast/data_free/PROVENANCE.md (YM, ZN, CL, 6J, GC, 6E, NKD, BTC are all on disk, 2023-02..2026-10-16; YM was never missing).
