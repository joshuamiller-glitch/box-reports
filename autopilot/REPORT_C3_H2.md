# REPORT C3-H2 - the live ST/HM pair on NQ 2013-2022 (diagnostic, not a candidate)

Registered in PREREG_AUTOPILOT.md (CYCLE 3), no tuning. Parameters, session windows, EMA200 filters, 60/60 bracket, 8/8, live rules (per-book 5R/-2R, day lock cap 8R / arm 2R / 67% give-back / 0000, combined week floor -8R, per-book week rule off, TH off) and costs (1 tick/side + $34.88/trade equivalent) exactly as the live corrected engine.

## Method
- Data: purchased Databento GLBX.MDP3 ohlcv-1m continuous `NQ.v.0` (volume-front), 2013-01-02..2026-10-13, 4.73M one-minute bars. Back-adjustment: **difference adjustment at each instrument_id change** (55 rolls): gap = first open of the new contract minus last close of the old one, applied to all earlier bars (median |gap| 15 pt, max 318 pt; the gap includes the real move over the switch, so adjusted levels carry a random-walk error but all intra-trade point differences are unaffected). Signals use adjusted prices, P&L uses point differences.
- Engine: `d1_f4_core.py` (1-minute bars, no 1-second data, stop-first when a bar spans both levels, stop gaps filled at the open, entries at the next bar open, ET DST clock, 18:00-15:00 entries except 09:00-09:58, flat at the 16:55 bar open, two independent books, **no cross-book netting / orphan orders**) with the live rules applied on trade rows. ST = Supertrend ATR120 x2.0 on closes, EMA200; HM = HMA20 vs HMA55 of (close - session VWAP reset 00:00 UTC-4 fixed), slow-slope > 0, EMA200.
- Fidelity against the live 1-second corrected engine on the overlap (2023-02-10..2026-10-13):

| span             |           net_1m |         net_live |   sharpe_1m |   sharpe_live |   weekly_corr |   daily_corr |   weeks |
|:-----------------|-----------------:|-----------------:|------------:|--------------:|--------------:|-------------:|--------:|
| 2023-02..2023-12 | 158367           |  -9504.64        |       0.525 |        -0.029 |         0.858 |        0.912 |      47 |
| clean            |      1.49889e+06 |      1.32996e+06 |       1.653 |         1.46  |         0.902 |        0.931 |     105 |
| H1               | 599732           | 593797           |       2.597 |         2.828 |         0.912 |        0.921 |      28 |
| H2               | 717758           | 761254           |       2.035 |         2.295 |         0.825 |        0.843 |      36 |
| 2023-02..2026-10 |      2.95291e+06 |      2.81168e+06 |       1.779 |         1.721 |         0.884 |        0.904 |     193 |

  Entry match: 11,779 of 13,089 live entries (90.0%) have a same-book, same-side entry on the same ET minute in the 1-minute engine (live `et_in` is one minute before the entry-bar open). Weekly P&L correlation is 0.83-0.91 by span. The 1-minute engine is **more optimistic in 2023 (net +$158k vs live -$10k, Feb-Dec 2023)** and a little less in H2 (-6%); read pre-2023 absolute dollars with that +-15% fidelity caveat.

## By calendar year (live rules, 8/8, 1 tick/side)
| year                            |        net |   sharpe |   mar |     maxdd |   worst_week |   trades |   weeks |   adr_pct |   trend_eff |
|:--------------------------------|-----------:|---------:|------:|----------:|-------------:|---------:|--------:|----------:|------------:|
| 2013                            |    -48,236 |    -0.49 | -0.44 |   108,967 |      -45,589 |      493 |      51 |      0.52 |       0.198 |
| 2014                            |   -162,543 |    -1.09 | -0.84 |   194,245 |      -77,963 |      561 |      53 |      0.63 |       0.121 |
| 2015                            |    121,502 |     0.62 |  1.07 |   113,340 |      -77,399 |      674 |      53 |      0.82 |       0.043 |
| 2016                            |     22,104 |     0.13 |  0.16 |   137,756 |      -73,357 |      678 |      52 |      0.78 |       0.047 |
| 2017                            |     20,337 |     0.13 |  0.12 |   170,748 |      -50,019 |      597 |      52 |      0.56 |       0.21  |
| 2018                            |   -330,095 |    -1.18 | -0.73 |   454,555 |      -78,493 |     1214 |      53 |      1.25 |       0.015 |
| 2019                            |    -27,245 |    -0.09 | -0.06 |   423,844 |      -79,888 |      972 |      53 |      0.99 |       0.161 |
| 2020                            |   -613,942 |    -1.43 | -0.9  |   685,540 |      -80,246 |     2805 |      53 |      1.99 |       0.108 |
| 2021                            |   -287,991 |    -0.75 | -0.42 |   691,307 |      -78,167 |     2333 |      52 |      1.33 |       0.112 |
| 2022                            |   -921,111 |    -2.09 | -0.77 | 1,190,772 |      -78,868 |     3711 |      52 |      2.29 |       0.108 |
| 2023                            |     67,741 |     0.2  |  0.33 |   208,069 |      -78,573 |     2183 |      52 |      1.36 |       0.17  |
| 2024                            |  1,004,821 |     2.18 |  2.73 |   368,187 |      -77,768 |     2877 |      53 |      1.42 |       0.083 |
| 2025                            |  1,093,886 |     2.25 |  3.76 |   290,691 |      -78,823 |     3923 |      53 |      1.75 |       0.063 |
| 2026                            |    683,928 |     1.68 |  2.93 |   233,257 |      -78,132 |     4410 |      42 |      1.85 |       0.083 |
| 2013-2022                       | -2,227,220 |    -0.78 | -0.88 | 2,524,676 |      -80,246 |    14038 |     520 |    nan    |     nan     |
| 2013-2019                       |   -404,176 |    -0.29 | -0.69 |   582,972 |      -79,888 |     5189 |     364 |    nan    |     nan     |
| 2020-2022                       | -1,823,044 |    -1.45 | -0.88 | 2,068,184 |      -80,246 |     8849 |     157 |    nan    |     nan     |
| 2023-02..2026-10 (1-min engine) |  2,952,912 |     1.78 |  8.02 |   368,187 |      -78,823 |    13113 |     193 |    nan    |     nan     |

(adr_pct = mean daily range as % of the close; trend_eff = |net move| / sum of |daily changes| over the year; weekly Sharpe from weekly sums; MAR = net / max DD.)

Per-book net by year ($):
|   lout |      HM |      ST |
|-------:|--------:|--------:|
|   2013 |  -11220 |  -37015 |
|   2014 |   -9057 | -153486 |
|   2015 |   10009 |  111494 |
|   2016 |  -44356 |   66460 |
|   2017 |   44041 |  -23704 |
|   2018 | -168844 | -161251 |
|   2019 |  -34404 |    7158 |
|   2020 | -398100 | -215842 |
|   2021 | -375683 |   87691 |
|   2022 | -468124 | -452987 |
|   2023 | -197811 |  265552 |
|   2024 |  403734 |  601087 |
|   2025 |  510383 |  583503 |
|   2026 |  557383 |  126545 |

## Sensitivity: bracket scaled to the 20-day range (not the registered cell)
The fixed 60-pt bracket means different things at NQ 3,000 and NQ 25,000. Sensitivity: bracket = k x ADR20 with k = 60 / median(ADR20 over clean) = 0.211 (set from the live window's range, not from performance), R = $9,600 per full stop on every year, same rules. It does not rescue the pre-2023 period: 2013-2022 net -6,255,531, weekly Sharpe -1.57; 2023-02..2026-10 Sharpe +1.13 (1.78 with the fixed bracket).

| year             |               net |   sharpe |            maxdd |   worst_week |   trades |
|:-----------------|------------------:|---------:|-----------------:|-------------:|---------:|
| 2013             |      -1.53002e+06 |    -3.82 |      1.55535e+06 |     -82813.1 |     2566 |
| 2014             | -955654           |    -2.66 | 990870           |     -79745.9 |     2738 |
| 2015             | -997314           |    -2.47 |      1.1156e+06  |     -83454.9 |     2812 |
| 2016             | -757970           |    -1.79 |      1.29219e+06 |     -85401.2 |     2872 |
| 2017             | -475382           |    -1.13 | 688065           |     -81986   |     2684 |
| 2018             |  -55751           |    -0.15 | 501222           |     -79017   |     2970 |
| 2019             | -842369           |    -2.4  | 970179           |     -80572.2 |     2693 |
| 2020             | -342465           |    -0.91 | 586030           |     -80051.2 |     3108 |
| 2021             |  -49842.5         |    -0.12 | 525856           |     -78946.6 |     2953 |
| 2022             | -248763           |    -0.57 | 571561           |     -79754.5 |     2731 |
| 2023             | -201944           |    -0.54 | 404781           |     -80010.3 |     2644 |
| 2024             |  926018           |     2.11 | 371075           |     -77608.2 |     2773 |
| 2025             |  639856           |     1.42 | 218514           |     -78040.9 |     2791 |
| 2026             |  395017           |     0.97 | 220260           |     -81371.2 |     2386 |
| 2013-2022        |      -6.25553e+06 |    -1.57 |      6.42015e+06 |     -85401.2 |    28127 |
| 2023-02..2026-10 |       1.83585e+06 |     1.13 | 371075           |     -81371.2 |    10297 |

## Verdict
**The live ST/HM pair has no edge on NQ 2013-2022 under frozen parameters.** Net -$2.2M and weekly Sharpe -0.78 over 2013-2022 on the 1-minute engine (fixed 60/60); -$6.3M with a range-scaled bracket. 7 of 10 years lose (2015-2017 are marginally positive; 2013-2014, 2018-2019 and 2020-2022 are negative); the loss is concentrated in 2018 and 2020-2022 (high-range years with 2,800-3,700 trades and trend efficiency ~0.1). The profitable years are 2024-2026 (Sharpe 1.7-2.3, partial 2026) with 2023 near flat (+0.20; the live 1-second engine has 2023-02..12 at -$10k).
Regime dependence: the pair earned only in 2024-2026, the years NQ rose from 17k to 31k (NQ also rose strongly in 2013, 2016-2017 and 2019-2021 when the pair lost, so uptrend alone does not explain it); it lost in the earlier regimes in both calm (2013-2017, ADR 0.5-0.8%) and volatile (2018, 2020-2022, ADR 1.25-2.29%) markets. Frozen parameters were chosen on 2023-2026, so 2013-2022 is a true out-of-sample test and it fails. Do not read this as a forecast, but it removes the argument that the pair is a structural, regime-independent edge: its evidence is the last 3 years. Caveat: 1-minute engine, +-15% fidelity vs the 1-second engine (weekly corr 0.88), approximated back-adjustment, and the 2013-2022 NQ tick size/liquidity differ.

DONE C3_H2
