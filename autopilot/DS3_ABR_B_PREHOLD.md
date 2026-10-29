# DS3_ABR_B_PREHOLD - fixed-bracket oracle selection on PRE only (IN-SAMPLE), written before HOLD / X were opened (ABRA, 2026-10-29)
Prereg l2vast/ds3/prereg/ABR_B_prereg.md (sha256 in DECISIONS.md). PRE = label days 2024-02-01..2025-06-30. Every number below is IN-SAMPLE (selection and evaluation on the same PRE entries; hindsight). HOLD and X not read. Basis M (measured fills, fees 0.242 pt), pts per lot, constant 10-lot stop slip (CL); RP = $ per entry at constant-$-risk lots; G = gross at touch (diagnostic).
Selection = highest PRE mean over the 990 brackets; gain = best - control C1 (60/60, no time exit) per entry, 95% CI and MDE80 = 2.8 SE (week-cluster SE); RC p = White reality check, best of 990, week-block bootstrap 2,000 draws; per-trade oracle = max over the 990 brackets per entry with hindsight, an UPPER BOUND, not a result.

## Pooled (HG0) IN-SAMPLE
| group | n PRE | best fixed bracket (CL) | mean best | mean C1 60/60 | mean LIVE | gain vs C1 [95% CI] | MDE80 | RC p (best of 990) | RP-selected | G-selected | per-trade oracle (UPPER BOUND) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ALL | 26022 | abs120|OR|none | 2.67 | 0.34 | 0.24 | +2.33 [-2.04, +6.70] | 6.24 | 0.663 | abs60|R3|none (p 0.791) | abs120|OR|none | 118.6 |

## Per book (HG1) IN-SAMPLE
| group | n PRE | best fixed bracket (CL) | mean best | mean C1 60/60 | mean LIVE | gain vs C1 [95% CI] | MDE80 | RC p (best of 990) | RP-selected | G-selected | per-trade oracle (UPPER BOUND) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ST | 3020 | abs75|R3|none | 2.11 | 0.43 | 0.40 | +1.68 [-3.05, +6.41] | 6.76 | 0.696 | abs50|R3|none (p 0.774) | abs75|R3|none | 121.1 |
| HM | 2285 | abs120|PD|sess | 3.40 | 0.42 | 0.43 | +2.98 [+0.32, +5.63] | 3.79 | 0.312 | abs75|NS|sess (p 0.605) | abs120|PD|sess | 117.7 |
| WT | 4265 | abs120|OR|none | 3.36 | -0.05 | -0.99 | +3.41 [-2.15, +8.97] | 7.94 | 0.247 | abs50|R3|none (p 0.471) | abs120|OR|none | 117.5 |
| KB | 3093 | abs75|R3|none | 4.11 | 1.14 | 1.17 | +2.97 [-0.50, +6.43] | 4.95 | 0.355 | abs60|R3|none (p 0.435) | abs75|R3|none | 121.2 |
| SM | 904 | abs120|OR|none | 5.97 | 2.25 | 2.41 | +3.71 [-2.96, +10.39] | 9.54 | 0.709 | abs30|OR|none (p 0.993) | abs120|OR|none | 120.4 |
| PE | 3049 | abs120|OR|none | 2.47 | -0.96 | -0.96 | +3.44 [-1.41, +8.29] | 6.93 | 0.194 | abs60|R3|none (p 0.268) | abs120|OR|none | 119.1 |
| PB | 2261 | a5m_2|R3|none | 4.81 | -1.50 | -1.51 | +6.31 [+1.93, +10.70] | 6.27 | 0.018 | abs90|OR|none (p 0.043) | a5m_2|R3|none | 117.4 |
| DN | 1762 | abs75|R3|none | 4.35 | 2.86 | 2.86 | +1.49 [-3.93, +6.92] | 7.75 | 0.967 | abs75|R3|none (p 0.998) | abs75|R3|none | 117.4 |
| MV | 2922 | abs120|VW|none | 2.77 | 0.85 | 0.79 | +1.92 [-2.68, +6.53] | 6.58 | 0.606 | abs50|R3|none (p 0.631) | abs120|VW|none | 121.8 |
| MA | 1093 | abs120|OR|none | 5.65 | 1.15 | 1.14 | +4.50 [-2.65, +11.65] | 10.21 | 0.852 | abs120|OR|none (p 0.986) | abs120|OR|none | 115.6 |
| CR | 1368 | abs120|R1.5|120m | 4.14 | -0.90 | 0.24 | +5.05 [+1.14, +8.95] | 5.58 | 0.182 | abs60|R3|120m (p 0.344) | abs120|R1.5|120m | 109.9 |

## Per entry session (HG2) IN-SAMPLE
| group | n PRE | best fixed bracket (CL) | mean best | mean C1 60/60 | mean LIVE | gain vs C1 [95% CI] | MDE80 | RC p (best of 990) | RP-selected | G-selected | per-trade oracle (UPPER BOUND) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| asia | 6689 | abs120|VW|none | 4.28 | 2.09 | 1.99 | +2.19 [-5.08, +9.46] | 10.38 | 0.971 | abs50|R3|none (p 0.830) | abs120|VW|none | 135.1 |
| london | 5732 | abs60|R3|none | 0.17 | -1.52 | -1.41 | +1.69 [-3.30, +6.69] | 7.13 | 0.961 | abs60|R3|none (p 0.959) | abs60|R3|none | 127.6 |
| pre | 1600 | abs75|R3|none | 5.46 | -2.25 | -2.33 | +7.71 [-2.17, +17.59] | 14.12 | 0.733 | abs75|R3|none (p 0.699) | abs75|R3|none | 124.0 |
| nyam | 6850 | a5m_2|R3|none | 7.87 | 2.25 | 1.94 | +5.62 [-4.22, +15.47] | 14.06 | 0.765 | a5m_2|R3|none (p 0.519) | a5m_2|R3|none | 116.5 |
| nypm | 5074 | abs120|PD|sess | 4.69 | -1.37 | -1.41 | +6.06 [+0.66, +11.46] | 7.71 | 0.013 | a5m_2|R3|sess (p 0.073) | abs120|PD|sess | 89.0 |
| close | 77 | a1m_0.75|R3|60m | 1.97 | -16.57 | -16.95 | +18.55 [+8.80, +28.29] | 13.92 | 0.011 | a5m_0.5|OR|60m (p 0.157) | a1m_0.75|R3|60m | 50.9 |

## Per book x session (HG3, PRE n >= 150) IN-SAMPLE
| group | n PRE | best fixed bracket (CL) | mean best | mean C1 60/60 | mean LIVE | gain vs C1 [95% CI] | MDE80 | RC p (best of 990) | RP-selected | G-selected | per-trade oracle (UPPER BOUND) |
|--|--|--|--|--|--|--|--|--|--|--|--|
| ST|asia | 712 | abs50|PD|none | 4.74 | 2.39 | 2.39 | +2.34 [-1.75, +6.44] | 5.85 | 0.846 | abs50|PD|none (p 0.833) | abs50|PD|none | 133.6 |
| ST|london | 624 | a1m_0.75|VW|none | -0.90 | -3.50 | -3.46 | +2.59 [-1.62, +6.80] | 6.02 | 0.845 | abs120|OR|none (p 0.893) | a1m_0.75|VW|none | 127.6 |
| ST|pre | 203 | abs60|R1.25|120m | 4.19 | 0.61 | 0.44 | +3.58 [-0.06, +7.23] | 5.20 | 0.536 | abs30|R3|120m (p 0.589) | abs60|R1.25|120m | 119.8 |
| ST|nyam | 915 | abs120|R3|none | 7.95 | 2.54 | 2.50 | +5.41 [-7.36, +18.18] | 18.24 | 0.772 | abs60|R3|none (p 0.813) | abs120|R1.5|none | 123.4 |
| ST|nypm | 564 | abs120|PD|sess | 8.89 | -0.97 | -1.06 | +9.87 [+2.03, +17.70] | 11.19 | 0.182 | abs90|R3|sess (p 0.233) | abs120|PD|sess | 95.2 |
| HM|asia | 622 | abs90|R3|sess | 7.33 | 2.49 | 2.45 | +4.84 [-0.96, +10.63] | 8.28 | 0.531 | abs50|R3|sess (p 0.660) | abs90|R3|sess | 135.3 |
| HM|london | 490 | abs120|VW|none | 3.46 | 0.18 | 0.46 | +3.28 [-9.44, +16.00] | 18.17 | 0.868 | abs40|R1.5|none (p 0.877) | abs120|VW|none | 130.3 |
| HM|nyam | 558 | abs120|R0.75|none | 11.28 | 2.84 | 2.65 | +8.44 [+1.93, +14.95] | 9.30 | 0.212 | a5m_2|NS|120m (p 0.526) | abs120|R0.75|none | 113.9 |
| HM|nypm | 478 | abs120|R3|sess | 5.41 | -2.59 | -2.55 | +7.99 [+1.38, +14.61] | 9.45 | 0.067 | abs90|PD|sess (p 0.179) | abs120|R3|sess | 85.6 |
| WT|asia | 1082 | abs50|R3|none | 3.92 | 1.95 | 0.36 | +1.97 [-2.30, +6.24] | 6.10 | 0.879 | abs40|R1.5|sess (p 0.628) | abs50|R3|none | 134.5 |
| WT|london | 1026 | abs120|OR|none | 0.99 | -1.96 | -1.41 | +2.95 [-9.35, +15.24] | 17.56 | 0.683 | abs50|OR|none (p 0.873) | abs120|OR|none | 128.8 |
| WT|pre | 241 | abs75|R3|none | 11.39 | -3.39 | -4.56 | +14.77 [-1.06, +30.61] | 22.61 | 0.263 | abs75|R3|none (p 0.329) | abs75|R3|none | 127.9 |
| WT|nyam | 1054 | abs120|R2|none | 11.79 | 2.10 | -0.09 | +9.69 [-0.04, +19.42] | 13.90 | 0.274 | a5m_2|R3|none (p 0.330) | abs120|R1.5|none | 115.1 |
| WT|nypm | 858 | abs120|PD|sess | 4.01 | -1.92 | -2.18 | +5.93 [+0.18, +11.68] | 8.22 | 0.051 | abs60|R1.5|sess (p 0.068) | abs120|PD|sess | 82.9 |
| KB|asia | 779 | abs75|R3|none | 8.03 | 1.99 | 2.13 | +6.04 [-0.59, +12.67] | 9.47 | 0.557 | abs75|R3|none (p 0.754) | abs75|R3|none | 141.4 |
| KB|london | 586 | abs60|R3|none | 2.61 | -0.83 | -0.77 | +3.44 [-2.62, +9.50] | 8.65 | 0.819 | abs60|R3|none (p 0.944) | abs60|R3|none | 129.0 |
| KB|pre | 171 | abs120|R1.5|none | 0.83 | -4.91 | -4.68 | +5.73 [-9.63, +21.10] | 21.95 | 0.873 | abs120|R1.5|none (p 0.925) | abs120|R1.5|none | 123.2 |
| KB|nyam | 885 | abs120|NS|none | 10.38 | 3.34 | 3.29 | +7.04 [-0.81, +14.90] | 11.22 | 0.468 | abs30|R3|none (p 0.728) | abs120|NS|none | 118.1 |
| KB|nypm | 662 | a5m_2|PD|sess | 8.95 | 0.92 | 0.83 | +8.03 [-1.19, +17.25] | 13.17 | 0.139 | a5m_1.5|R3|30m (p 0.479) | a5m_2|PD|sess | 94.9 |
| SM|asia | 242 | abs120|OR|none | 20.29 | 7.32 | 7.58 | +12.97 [-1.25, +27.20] | 20.32 | 0.518 | a5m_1.5|OR|none (p 0.580) | abs120|OR|none | 140.3 |
| SM|london | 269 | abs90|R3|none | 5.19 | 0.16 | 0.73 | +5.03 [-8.99, +19.05] | 20.02 | 0.781 | abs90|R3|none (p 0.918) | abs90|R3|none | 127.6 |
| SM|nyam | 220 | abs75|R1.5|none | 8.55 | 3.12 | 2.90 | +5.43 [-2.63, +13.48] | 11.50 | 0.833 | abs60|R2|none (p 0.906) | abs75|R1.5|none | 110.0 |
| PE|asia | 755 | abs120|VW|none | 4.95 | 1.61 | 1.77 | +3.34 [-5.88, +12.57] | 13.18 | 0.896 | abs40|R3|none (p 0.517) | abs120|VW|none | 135.2 |
| PE|london | 607 | abs90|R3|none | 1.85 | -4.27 | -4.09 | +6.12 [-3.11, +15.34] | 13.18 | 0.655 | abs90|R3|none (p 0.716) | abs90|R3|none | 126.7 |
| PE|pre | 178 | abs90|R3|none | 4.93 | -2.73 | -2.74 | +7.66 [-12.22, +27.54] | 28.41 | 0.919 | abs90|R3|none (p 0.939) | abs90|R3|none | 118.0 |
| PE|nyam | 839 | a5m_2|R3|none | 8.69 | 0.60 | 0.44 | +8.09 [-4.86, +21.03] | 18.49 | 0.699 | a5m_1.5|R3|none (p 0.381) | a5m_2|R3|none | 119.6 |
| PE|nypm | 665 | abs120|R3|sess | 3.45 | -2.27 | -2.37 | +5.72 [-1.44, +12.87] | 10.22 | 0.258 | abs90|OR|none (p 0.319) | abs120|OR|none | 94.0 |
| PB|asia | 623 | abs120|R1|none | 3.54 | -1.21 | -1.27 | +4.75 [-4.24, +13.75] | 12.85 | 0.003 | abs50|PD|none (p 0.007) | abs120|R1|none | 133.0 |
| PB|london | 487 | abs50|OR|none | 2.04 | -2.79 | -2.45 | +4.83 [+1.18, +8.47] | 5.21 | 0.155 | abs50|OR|none (p 0.380) | abs50|OR|none | 124.6 |
| PB|nyam | 572 | a5m_2|R3|none | 17.29 | -0.43 | -0.55 | +17.71 [+5.51, +29.92] | 17.43 | 0.013 | a5m_2|R3|none (p 0.009) | a5m_2|R3|none | 118.6 |
| PB|nypm | 443 | a5m_2|R3|none | 8.62 | -3.22 | -3.36 | +11.83 [-2.61, +26.27] | 20.63 | 0.470 | a5m_2|PD|none (p 0.218) | a5m_2|R3|none | 84.2 |
| DN|asia | 424 | abs120|OR|none | 12.84 | 5.32 | 5.14 | +7.52 [-4.82, +19.86] | 17.63 | 0.792 | a1m_0.5|R3|sess (p 0.746) | abs120|OR|none | 136.3 |
| DN|london | 402 | abs60|R3|none | 4.45 | -0.37 | -0.26 | +4.83 [-3.29, +12.94] | 11.59 | 0.879 | abs60|R3|none (p 0.899) | abs60|R3|none | 127.9 |
| DN|nyam | 503 | abs120|R0.75|none | 8.60 | 6.63 | 6.64 | +1.97 [-5.43, +9.38] | 10.58 | 0.973 | abs40|R2|none (p 0.492) | abs120|R0.75|none | 112.0 |
| DN|nypm | 303 | a5m_1.5|PD|none | 8.27 | -1.37 | -1.22 | +9.63 [-2.33, +21.59] | 17.09 | 0.410 | abs30|R3|30m (p 0.482) | a5m_1.5|PD|none | 90.3 |
| MV|asia | 747 | abs120|R3|none | 6.47 | 3.45 | 3.21 | +3.02 [-12.49, +18.53] | 22.15 | 0.938 | abs50|R3|none (p 0.927) | abs120|R3|none | 137.1 |
| MV|london | 548 | abs60|R3|none | 2.18 | -1.27 | -1.21 | +3.45 [-3.00, +9.89] | 9.21 | 0.744 | abs60|R3|none (p 0.862) | abs60|R3|none | 132.1 |
| MV|pre | 192 | abs90|R3|none | 7.31 | -5.32 | -5.19 | +12.63 [-4.99, +30.24] | 25.16 | 0.230 | abs75|R3|none (p 0.262) | abs90|R3|none | 123.0 |
| MV|nyam | 797 | a5m_2|R3|none | 9.64 | 3.03 | 3.12 | +6.61 [-10.02, +23.23] | 23.75 | 0.862 | abs50|OR|none (p 0.760) | a5m_2|R3|none | 121.2 |
| MV|nypm | 633 | a5m_2|PD|sess | 8.15 | -1.16 | -1.34 | +9.31 [-1.88, +20.51] | 16.00 | 0.252 | a5m_2|PD|sess (p 0.354) | a5m_2|PD|sess | 95.6 |
| MA|asia | 333 | abs120|VW|none | 11.84 | 2.99 | 2.68 | +8.85 [-4.05, +21.75] | 18.42 | 0.768 | abs120|VW|none (p 0.956) | abs120|VW|none | 132.8 |
| MA|london | 264 | abs120|OR|none | 5.68 | 2.97 | 3.11 | +2.71 [-13.99, +19.42] | 23.87 | 0.985 | abs60|R1.5|none (p 0.999) | abs120|OR|none | 130.3 |
| MA|nyam | 237 | a1m_2|R3|none | 10.37 | 2.64 | 2.94 | +7.73 [-0.39, +15.85] | 11.60 | 0.493 | a1m_2|R3|none (p 0.108) | a1m_2|R3|none | 106.5 |
| MA|nypm | 187 | abs90|R3|sess | 9.03 | -1.14 | -1.37 | +10.17 [+0.65, +19.70] | 13.61 | 0.347 | abs50|R3|none (p 0.459) | abs90|R2|sess | 77.7 |
| CR|asia | 370 | abs120|R0.75|none | 7.28 | -2.60 | 0.42 | +9.88 [+2.33, +17.42] | 10.78 | 0.092 | abs90|R1.5|none (p 0.121) | abs120|R0.75|none | 123.2 |
| CR|london | 429 | abs90|R0.5|sess | 2.71 | -0.41 | -1.90 | +3.12 [-1.54, +7.78] | 6.66 | 0.649 | abs30|R1.5|sess (p 0.825) | abs90|R0.5|sess | 116.6 |
| CR|nyam | 270 | a5m_2|R3|sess | 3.19 | -3.65 | -1.86 | +6.84 [+0.59, +13.08] | 8.92 | 0.209 | a5m_2|R3|120m (p 0.240) | abs120|R1|sess | 94.0 |
| CR|nypm | 173 | abs120|R1.5|120m | 7.60 | 1.64 | 3.79 | +5.96 [-3.36, +15.28] | 13.31 | 0.552 | abs20|OR|120m (p 0.311) | abs120|R1.5|120m | 71.1 |
