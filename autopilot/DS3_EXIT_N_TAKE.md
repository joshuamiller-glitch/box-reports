# DS3_EXIT_N_TAKE - E3 (TAKE) of T-EXIT-N: take rules on the true fill basis (Z2, first table 2026-11-02 ~14:45Z). POST-HOC, Shadow only, no PASS
Prereg `l2vast/ds3/prereg/EXITN_E3_TAKE_prereg.md` sha256 515756fef33888cf230c59f47c7201d1e0d684f978b0dbe75d2163195f1940fe (in DECISIONS.md before any E3 statistic). Base = V13T_LIVE (d7_v13t.run_v13t_live: lines empty, lock none = per-book locks, xcost 0.80, stopcost 2.45, tshort 0, resting add cancelled on every exit), 1-s grid, windows L3M L6M HOLD MID PRE X'. Exits injected through V13T.inject (delta per lot = side*(px - exit_px_lib) - xcost + fill_cost*(original exit not the target)). Code `l2vast/ds3/code/zones3/s2/e3lib.py, e3_run.py, rep_e3.py`; data `l2vast/ds3/out/zones3/s2/e3/`.
## Page 1 - plain sentences
**The five erased THP_POLICY_D7 lines on the true fill basis lose: L6M mean -18.8k/wk (MDE 21.9k), PRE -11.0k/wk, maxDD L6M 150.7 -> 163.8k, PRE 166 -> 223k; no window cut.** The plain-pct take is no better: pct 0.3 -23.1k/wk L6M (PRE maxDD +84% worse), 0.5 -11.3k (L6M maxDD cut +36% but PRE -12%, MID/PRE/X' Calmar -42..-97%), 0.7 -7.5k (L6M cut +21%, ONE-WEEK). Answer to 'does the take pay when the alternative outcome is a stop at 2.45?': no on any window and any book x session pooled; the per-book x session cube shows isolated positive cells (K6 Asia L6M +1.1k/wk, M6 London +0.6..1.2k/wk) swamped by P6 Asia/London and H6 Asia losses (-4k to -8k/wk).
**Flow-gated takes (delta-turn against, large print against, pulled-support ratio, iceberg refill) do not rescue it:** of 28 gated cells none is STRICT or TOLERANT; four are NOW-ONLY with TOL-B (delta-turn <= -100 contracts at pct 0.5 and 0.7, delta <= -60 at pct 0.7, zone take with ahead_rel >= 1.2): L6M mean +0.3..+2.5k/wk (MDE 4-6k, inside), L6M maxDD cut +6..+13%, but PRE mean -0.6..-1.8k/wk and X' -0.4..-1.2k/wk, PRE Calmar -2..-6%; two of the four are ONE-WEEK. Gate firing is not selective: a gate that is true at any second of a 4-h trade fires on 25-60% of trades, so the deltas are close to the ungated take.
**'Take at a line' (zone take):** price reaching the nearest fresh set line ahead with the book thick there (ahead_rel >= 1.2): 3,712 fires, L6M maxDD 150.7 -> 138.7k (-8%), L6M mean +0.9k (inside MDE), ONE-WEEK, PRE mean -1.2k/wk, MID Calmar +27%; ahead_rel >= 1.5 is negative; with no book gate (>= 0) the L6M cut is +22% and MID Calmar +64% but PRE Calmar -19% and X' -29%. No cell passes the two-window test (L6M and PRE).
**THP_POLICY_D7 recommendation from E3: none of the take lines or gates pass on N; publish the empty header.**
Pending: three placebos (>= 100 draws, same cost model) for the four NOW-ONLY(B) cells, equal-risk, phase-average band on V13T, two-episode rule.
## Table (vs control = V13T_LIVE with no exits; fires = number of injected exits; mean change in $ per week; MDE = 2.8 x SE of the paired weekly delta, L6M)
Control (V13T_LIVE, no exits): L6M 36.7k/wk, maxDD L6M 150.7k, HOLD 150.7k, MID 43.7k, PRE 166.2k, X' 92.5k, mean PRE 17.3k, X' 4.8k

| row | fires | maxDD $k L6M / HOLD / MID / PRE / X' | maxDD cut L6M / PRE / X' | Calmar gain L6M / HOLD / MID / PRE / X' | mean d $/wk L6M / PRE / X' (L6M MDE) | S/T/N (B, nc) | ONE-WEEK | LOMO |
|---|---|---|---|---|---|---|---|---|
| R1|exact5 | 46657 | 163.8 / 177.5 / 107.3 / 222.9 / 80.5 | -9% / -34% / +13% | -55% / -66% / -99% / -73% / -30% | -18769 / -11008 / -1864 (21936) | -/-/- (-) | no | 2/7 |
| R2|plain0.3 | 47883 | 144.4 / 144.4 / 97.9 / 305.9 / 168.1 | +4% / -84% / -82% | -61% / -68% / -97% / -86% / -114% | -23088 / -12721 / -6018 (31446) | -/-/- (-) | ONE-WEEK | 6/7 |
| R2|plain0.3+PB | 50223 | 144.4 / 144.4 / 97.9 / 305.9 / 168.1 | +4% / -84% / -82% | -61% / -68% / -97% / -86% / -114% | -23088 / -12721 / -6018 (31446) | -/-/- (-) | ONE-WEEK | 6/7 |
| R2|plain0.5 | 48059 | 97.0 / 142.4 / 105.8 / 186.3 / 75.2 | +36% / -12% / +19% | +8% / -42% / -97% / -63% / -32% | -11331 / -10117 / -2139 (21906) | -/-/- (-) | no | 7/7 |
| R2|plain0.5+PB | 50367 | 97.0 / 142.4 / 105.8 / 186.3 / 75.2 | +36% / -12% / +19% | +8% / -42% / -97% / -63% / -32% | -11331 / -10117 / -2139 (21906) | -/-/- (-) | no | 7/7 |
| R2|plain0.7 | 48021 | 118.4 / 118.4 / 48.0 / 145.5 / 64.2 | +21% / +12% / +31% | +1% / +4% / -33% / -22% / +45% | -7473 / -5550 / +28 (17463) | -/-/- (-) | ONE-WEEK | 6/7 |
| R2|plain0.7+PB | 50266 | 118.4 / 118.4 / 48.0 / 145.5 / 64.2 | +21% / +12% / +31% | +1% / +4% / -33% / -22% / +45% | -7473 / -5550 / +28 (17463) | -/-/- (-) | ONE-WEEK | 6/7 |
| R3|delta|a0.3|T100 | 13167 | 113.0 / 171.6 / 71.1 / 148.2 / 149.5 | +25% / +11% / -62% | +29% / -23% / -60% / -26% / -101% | -1240 / -5842 / -4880 (9020) | -/-/- (-) | no | 6/7 |
| R3|delta|a0.3|T30 | 25896 | 234.9 / 234.9 / 111.5 / 284.6 / 164.5 | -56% / -71% / -78% | -70% / -75% / -100% / -86% / -111% | -19711 / -13162 / -5753 (22996) | -/-/- (-) | no | 0/7 |
| R3|delta|a0.3|T60 | 19774 | 85.0 / 174.8 / 112.3 / 189.0 / 183.0 | +44% / -14% / -98% | +46% / -35% / -96% / -59% / -108% | -6436 / -9165 / -5599 (15606) | -/-/- (-) | no | 7/7 |
| R3|delta|a0.5|T100 | 9420 | 133.5 / 133.5 / 45.0 / 154.0 / 66.0 | +11% / +7% / +29% | +17% / +12% / -12% / -4% / +17% | +1437 / -1833 / -805 (6181) | -/-/N (B) | ONE-WEEK | 6/7 |
| R3|delta|a0.5|T30 | 21295 | 83.9 / 156.5 / 90.2 / 166.3 / 69.8 | +44% / -0% / +25% | +44% / -34% / -79% / -40% / -23% | -7300 / -6953 / -2024 (17890) | -/-/- (-) | no | 7/7 |
| R3|delta|a0.5|T60 | 15232 | 130.9 / 130.9 / 62.7 / 147.9 / 89.7 | +13% / +11% / +3% | +5% / -4% / -74% / -19% / -46% | -3270 / -4845 / -2280 (10664) | -/-/- (-) | no | 6/7 |
| R3|delta|a0.7|T100 | 5093 | 142.0 / 142.0 / 43.3 / 171.2 / 104.4 | +6% / -3% / -13% | +14% / +5% / -3% / -6% / -34% | +2535 / -596 / -1231 (4126) | -/-/N (B) | no | 7/7 |
| R3|delta|a0.7|T30 | 15283 | 175.1 / 175.1 / 53.5 / 151.9 / 75.7 | -16% / +9% / +18% | -28% / -25% / -48% / -12% / -22% | -5915 / -3322 / -1728 (11996) | -/-/- (-) | no | 1/7 |
| R3|delta|a0.7|T60 | 9668 | 141.7 / 141.7 / 47.9 / 161.2 / 86.6 | +6% / +3% / +6% | +7% / +7% / -14% / -2% / -2% | +276 / -781 / -404 (4885) | -/-/N (B) | ONE-WEEK | 5/7 |
| R3|ice|a0.3 | 2701 | 142.3 / 142.3 / 46.0 / 167.9 / 62.8 | +6% / -1% / +32% | +7% / +7% / +0% / -13% / +12% | +415 / -2001 / -1134 (2500) | -/-/- (-) | no | 6/7 |
| R3|ice|a0.5 | 1576 | 147.7 / 147.7 / 46.0 / 178.6 / 75.0 | +2% / -7% / +19% | +1% / +1% / -2% / -18% / +44% | -249 / -1962 / +821 (1091) | -/-/- (-) | no | 6/7 |
| R3|ice|a0.7 | 745 | 153.7 / 153.7 / 43.7 / 167.7 / 70.9 | -2% / -1% / +23% | -3% / -3% / -1% / -4% / +46% | -301 / -612 / +575 (586) | -/-/- (-) | no | 0/7 |
| R3|print|a0.3 | 16762 | 156.3 / 218.0 / 113.6 / 173.7 / 181.5 | -4% / -5% / -96% | -13% / -55% / -90% / -52% / -107% | -3518 / -8556 / -5496 (11571) | -/-/- (-) | no | 2/7 |
| R3|print|a0.5 | 13233 | 114.0 / 148.5 / 52.4 / 192.1 / 97.9 | +24% / -16% / -6% | +28% / -18% / -57% / -47% / -66% | -1089 / -6742 / -3053 (10588) | -/-/- (-) | no | 6/7 |
| R3|print|a0.7 | 9271 | 127.0 / 137.3 / 49.6 / 183.9 / 63.8 | +16% / -11% / +31% | +21% / +1% / -26% / -21% / +31% | +838 / -2229 / -475 (5142) | -/-/- (-) | no | 7/7 |
| R3|pull|a0.3|thr0.65 | 28634 | 171.7 / 178.7 / 131.1 / 229.9 / 160.9 | -14% / -38% / -74% | -62% / -74% / -100% / -81% / -121% | -20876 / -12765 / -6571 (30050) | -/-/- (-) | no | 1/7 |
| R3|pull|a0.3|thr1.0 | 27627 | 112.5 / 223.8 / 168.5 / 222.1 / 133.3 | +25% / -34% / -44% | -36% / -80% / -104% / -80% / -105% | -19080 / -12576 / -5115 (30458) | -/-/- (-) | no | 7/7 |
| R3|pull|a0.3|thr1.25 | 26158 | 131.8 / 173.7 / 125.1 / 197.2 / 145.5 | +13% / -19% / -57% | -40% / -67% / -103% / -77% / -97% | -17592 / -12506 / -4576 (27573) | -/-/- (-) | ONE-WEEK | 6/7 |
| R3|pull|a0.5|thr0.65 | 24623 | 110.0 / 128.3 / 92.9 / 178.2 / 64.7 | +27% / -7% / +30% | -7% / -35% / -97% / -62% / -18% | -11770 / -10177 / -2059 (19990) | -/-/- (-) | no | 7/7 |
| R3|pull|a0.5|thr1.0 | 23471 | 91.7 / 111.8 / 73.6 / 151.5 / 71.8 | +39% / +9% / +22% | +18% / -19% / -83% / -51% / -19% | -10329 / -9567 / -1786 (20248) | -/-/- (-) | no | 7/7 |
| R3|pull|a0.5|thr1.25 | 21734 | 90.3 / 115.8 / 69.5 / 157.7 / 76.8 | +40% / +5% / +17% | +29% / -20% / -84% / -51% / -26% | -8372 / -9324 / -1865 (18867) | -/-/- (-) | no | 7/7 |
| R3|pull|a0.7|thr0.65 | 20723 | 178.6 / 178.6 / 51.1 / 137.2 / 72.5 | -18% / +17% / +22% | -42% / -41% / -58% / -16% / -51% | -11641 / -5347 / -2972 (15868) | -/-/- (-) | no | 0/7 |
| R3|pull|a0.7|thr1.0 | 18785 | 158.8 / 158.8 / 49.7 / 150.6 / 74.5 | -5% / +9% / +19% | -37% / -36% / -57% / -26% / -25% | -12256 / -5636 / -1880 (15011) | -/-/- (-) | no | 1/7 |
| R3|pull|a0.7|thr1.25 | 16351 | 151.0 / 151.0 / 48.8 / 160.1 / 88.3 | -0% / +4% / +5% | -38% / -31% / -47% / -31% / -32% | -13820 / -5736 / -1663 (13828) | -/-/- (-) | no | 1/7 |
| R4|zone|ahead0.0 | 8624 | 117.1 / 117.1 / 29.5 / 171.2 / 129.0 | +22% / -3% / -39% | +23% / +25% / +64% / -19% / -29% | -1602 / -2838 / -45 (9546) | -/-/- (-) | no | 6/7 |
| R4|zone|ahead1.2 | 3712 | 138.7 / 138.7 / 34.2 / 159.7 / 112.7 | +8% / +4% / -22% | +11% / +10% / +27% / -3% / -21% | +912 / -1177 / -177 (5797) | -/-/N (B) | ONE-WEEK | 6/7 |
| R4|zone|ahead1.5 | 1801 | 171.2 / 171.2 / 44.2 / 171.9 / 115.3 | -14% / -3% / -25% | -14% / -15% / -9% / -5% / -21% | -962 / -370 / -43 (4931) | -/-/- (-) | no | 1/7 |

## Per book x session (change vs control; $ per week and maxDD k$) for the record rows and the best gated cells

#### R1|exact5: change vs control by book x session ($ per week mean and maxDD, k$; L6M / PRE / X')

| book | session | d mean L6M | d mean PRE | d mean X' | d maxDD L6M | d maxDD PRE | d maxDD X' |
|---|---|---|---|---|---|---|---|
| K6 | asia | +1060 | +149 | -61 | -20.2 | +0.1 | -4.6 |
| K6 | london | -244 | -158 | -342 | -7.4 | -5.5 | +3.6 |
| K6 | nyam | -448 | -52 | +111 | +14.4 | -2.6 | -1.6 |
| K6 | nypm | -905 | +313 | +715 | +17.9 | -14.0 | -6.7 |
| P6 | asia | -7747 | -4354 | +1093 | +40.5 | +26.8 | -63.2 |
| P6 | london | -1021 | -2864 | -923 | -31.4 | +150.1 | -23.2 |
| P6 | nyam | +0 | -1827 | -1156 | +0.0 | +24.5 | -6.4 |
| U6 | asia | -2588 | -1298 | -1496 | +2.1 | -20.3 | +2.9 |
| U6 | london | -1189 | -26 | -624 | +4.9 | -2.8 | +7.9 |
| H6 | asia | -6254 | -439 | +252 | +3.0 | -18.4 | -20.4 |
| H6 | nyam | +175 | -224 | +89 | +6.0 | -0.8 | -6.5 |
| M6 | london | +587 | +35 | +235 | -16.2 | -1.8 | -9.3 |
| M6 | nyam | -196 | -263 | +244 | -3.5 | -2.9 | -9.8 |
| A6 | asia | +0 | +0 | +0 | +0.0 | +0.0 | +0.0 |

#### R2|plain0.5: change vs control by book x session ($ per week mean and maxDD, k$; L6M / PRE / X')

| book | session | d mean L6M | d mean PRE | d mean X' | d maxDD L6M | d maxDD PRE | d maxDD X' |
|---|---|---|---|---|---|---|---|
| K6 | asia | +460 | -327 | +360 | -42.0 | +0.8 | -12.4 |
| K6 | london | -634 | -290 | -326 | -10.1 | +26.0 | +6.3 |
| K6 | nyam | +6 | -493 | +117 | +6.8 | +4.5 | -3.3 |
| K6 | nypm | +657 | +355 | +296 | -3.3 | -23.6 | -10.3 |
| P6 | asia | -4943 | -4420 | +1971 | +16.7 | +17.1 | -77.6 |
| P6 | london | -2325 | -2198 | -2187 | -2.2 | +117.3 | +27.3 |
| P6 | nyam | +0 | -1754 | -2128 | +0.0 | +4.4 | +15.9 |
| U6 | asia | -387 | -915 | -1089 | -1.6 | -9.5 | -2.9 |
| U6 | london | -561 | +141 | +222 | -13.1 | -2.4 | -2.0 |
| H6 | asia | -4782 | +367 | +634 | +3.6 | -18.8 | -20.4 |
| H6 | nyam | +264 | -360 | +214 | +3.1 | +5.9 | -11.2 |
| M6 | london | +1236 | -61 | -301 | -20.8 | -0.4 | -8.1 |
| M6 | nyam | -322 | -161 | +78 | +5.7 | +0.8 | -5.6 |
| A6 | asia | +0 | +0 | +0 | +0.0 | +0.0 | +0.0 |

#### R2|plain0.7: change vs control by book x session ($ per week mean and maxDD, k$; L6M / PRE / X')

| book | session | d mean L6M | d mean PRE | d mean X' | d maxDD L6M | d maxDD PRE | d maxDD X' |
|---|---|---|---|---|---|---|---|
| K6 | asia | +836 | -92 | +74 | -24.8 | +10.2 | -6.7 |
| K6 | london | -1218 | -451 | -198 | -6.4 | +24.1 | +0.6 |
| K6 | nyam | -271 | -11 | +46 | +13.1 | -5.5 | -0.0 |
| K6 | nypm | +829 | +325 | +318 | -6.8 | -12.9 | -6.0 |
| P6 | asia | -843 | -2661 | +1542 | +15.3 | +15.0 | -57.5 |
| P6 | london | -4090 | -2476 | -1590 | +16.9 | +159.1 | -13.2 |
| P6 | nyam | +0 | +628 | -930 | +0.0 | -8.2 | -7.4 |
| U6 | asia | +677 | -848 | -716 | +1.5 | +3.3 | +11.0 |
| U6 | london | -76 | +352 | +744 | -18.8 | -20.8 | -0.4 |
| H6 | asia | -3899 | +122 | +417 | -2.2 | +1.0 | -9.7 |
| H6 | nyam | +5 | -142 | -133 | -0.2 | -0.9 | -2.0 |
| M6 | london | +1005 | -52 | +190 | -25.0 | +5.4 | -8.9 |
| M6 | nyam | -429 | -245 | +265 | +5.5 | -3.0 | -10.3 |
| A6 | asia | +0 | +0 | +0 | +0.0 | +0.0 | +0.0 |

#### R3|delta|a0.7|T100: change vs control by book x session ($ per week mean and maxDD, k$; L6M / PRE / X')

| book | session | d mean L6M | d mean PRE | d mean X' | d maxDD L6M | d maxDD PRE | d maxDD X' |
|---|---|---|---|---|---|---|---|
| K6 | asia | -42 | -25 | -16 | +0.0 | +0.0 | -1.9 |
| K6 | london | +126 | -88 | +26 | +0.0 | -2.3 | -0.4 |
| K6 | nyam | +302 | -203 | +13 | -2.1 | +0.3 | -1.1 |
| K6 | nypm | +367 | +216 | +340 | +1.4 | -13.2 | -9.2 |
| P6 | asia | +1163 | +159 | -162 | -4.9 | -0.5 | -17.8 |
| P6 | london | +58 | -758 | -684 | -6.3 | +37.1 | -8.6 |
| P6 | nyam | +0 | +578 | -845 | +0.0 | +4.2 | +3.8 |
| U6 | asia | +544 | -211 | -76 | +0.0 | +9.2 | +1.4 |
| U6 | london | +0 | -46 | +139 | +0.0 | -2.7 | +0.8 |
| H6 | asia | +6 | -155 | +155 | +0.0 | +0.6 | -4.2 |
| H6 | nyam | +68 | -111 | -119 | +0.3 | +0.1 | -1.9 |
| M6 | london | +22 | +98 | +43 | -1.0 | +2.3 | -6.1 |
| M6 | nyam | -79 | -47 | -45 | -4.1 | +0.1 | -0.2 |
| A6 | asia | +0 | +0 | +0 | +0.0 | +0.0 | +0.0 |

#### R4|zone|ahead1.2: change vs control by book x session ($ per week mean and maxDD, k$; L6M / PRE / X')

| book | session | d mean L6M | d mean PRE | d mean X' | d maxDD L6M | d maxDD PRE | d maxDD X' |
|---|---|---|---|---|---|---|---|
| K6 | asia | +517 | +247 | +17 | -4.8 | -2.0 | -0.6 |
| K6 | london | +703 | -66 | -173 | -1.2 | +5.6 | -4.7 |
| K6 | nyam | +99 | +89 | -71 | +1.9 | -0.7 | -1.9 |
| K6 | nypm | +20 | +254 | -93 | +0.0 | -10.0 | -1.6 |
| P6 | asia | +573 | -466 | +279 | +0.1 | +10.3 | -8.0 |
| P6 | london | -667 | -435 | -208 | +5.3 | +36.3 | -2.5 |
| P6 | nyam | +0 | -202 | +789 | +0.0 | -9.4 | +10.9 |
| U6 | asia | -228 | -255 | -662 | +2.0 | -2.5 | +12.1 |
| U6 | london | -115 | -206 | -85 | -2.7 | +2.3 | +8.2 |
| H6 | asia | -117 | -306 | -92 | +4.3 | -11.8 | +1.1 |
| H6 | nyam | +223 | +257 | -91 | +1.5 | -4.3 | -1.8 |
| M6 | london | +2 | -191 | +60 | +4.8 | +18.2 | -5.4 |
| M6 | nyam | -97 | +103 | +154 | -4.1 | -1.6 | -1.2 |
| A6 | asia | +0 | +0 | +0 | +0.0 | +0.0 | +0.0 |

