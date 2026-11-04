# DS3 ZONES LAYER vs SIZE - is the shipped HALF layer better than random halving at EQUAL RISK? (BASE-4, 2026-11-04T01:35Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Method: placebo layer = the shipped 7-line HALF mask (D20, half lots) replaced by a random half-lot mask with the same number of LIVE rows (A = same count per month, 100 draws; B = same count per month x book x session, 50 draws); OTE-62 B73, TH-L2 loss, profit lines, locks, sizer unchanged. Every placebo (and the references) has its WHOLE lot table scaled (engine lscale, integer-lot rounding) until the worst-20-weeks sum over ALL history equals the shipped layer's at scale 1 in the same frame (stop at |gap| <= 2.5% (<=5 engine runs); the residual gap is corrected linearly in mean, maxDD and ulcer: x target/achieved). Metrics per window: weekly mean ($k/wk), maxDD ($k, weekly cumulative), Calmar (mean/maxDD), ulcer (RMS of the weekly drawdown path, $k). RANK = share of placebo draws that are at least as GOOD as the shipped layer (higher mean / lower maxDD / higher Calmar / lower ulcer); small rank = the shipped layer beats random halving; ~0.5 = indistinguishable. Frames: lock none = per-book locks only (headline), 12R = + combined stack lock. Post-hoc.

## LOCK NONE (headline)

### A: same count per month: 100 draws; equal-risk lot scale of the placebo layers: median 1.000 [0.947, 1.089] (shipped = 1.000); residual risk gap max 3.6%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 24.5 | 23.5 [22.1,26.0] | 0.29 | 104.8 | 106.2 [75.0,130.9] | 0.49 | 0.234 / 0.224 | 0.42 | 39.4 / 38.3 | 0.56 |
| L3M | 7.7 | 6.0 [3.5,8.0] | 0.09 | 63.9 | 73.9 [62.9,91.5] | 0.11 | 0.121 / 0.082 | 0.07 | 35.9 / 40.2 | 0.22 |
| L6M | 27.0 | 25.6 [23.6,28.4] | 0.25 | 104.8 | 106.2 [75.0,130.9] | 0.49 | 0.258 / 0.245 | 0.37 | 44.5 / 43.8 | 0.54 |
| HOLD | 22.6 | 21.9 [20.9,23.8] | 0.33 | 122.0 | 117.5 [107.3,132.9] | 0.65 | 0.185 / 0.187 | 0.61 | 44.7 / 42.7 | 0.69 |
| MID | 16.9 | 17.0 [14.7,19.9] | 0.55 | 59.7 | 49.6 [37.6,58.4] | 0.96 | 0.282 / 0.354 | 0.89 | 20.2 / 15.5 | 0.97 |
| PRE | 13.2 | 11.7 [10.4,12.8] | 0.01 | 88.2 | 91.6 [78.2,106.8] | 0.35 | 0.150 / 0.131 | 0.11 | 26.3 / 27.2 | 0.36 |
| X' | 3.3 | 2.8 [1.6,3.9] | 0.27 | 80.8 | 86.5 [65.0,115.1] | 0.35 | 0.041 / 0.033 | 0.20 | 27.9 / 32.5 | 0.14 |

### B: same count per month x book x session: 50 draws; equal-risk lot scale of the placebo layers: median 1.006 [0.939, 1.048] (shipped = 1.000); residual risk gap max 5.2%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 24.5 | 23.5 [21.7,25.4] | 0.22 | 104.8 | 101.2 [76.3,128.2] | 0.60 | 0.234 / 0.236 | 0.52 | 39.4 / 35.6 | 0.74 |
| L3M | 7.7 | 6.0 [3.8,7.6] | 0.04 | 63.9 | 73.9 [63.4,89.8] | 0.06 | 0.121 / 0.080 | 0.04 | 35.9 / 40.0 | 0.18 |
| L6M | 27.0 | 25.5 [22.9,27.9] | 0.20 | 104.8 | 101.2 [76.3,128.2] | 0.60 | 0.258 / 0.255 | 0.42 | 44.5 / 40.5 | 0.72 |
| HOLD | 22.6 | 21.6 [20.2,23.0] | 0.16 | 122.0 | 122.2 [107.1,132.2] | 0.50 | 0.185 / 0.181 | 0.42 | 44.7 / 41.7 | 0.76 |
| MID | 16.9 | 17.2 [14.9,19.7] | 0.56 | 59.7 | 49.3 [38.3,60.1] | 0.92 | 0.282 / 0.360 | 0.76 | 20.2 / 15.4 | 0.96 |
| PRE | 13.2 | 11.8 [10.4,13.2] | 0.02 | 88.2 | 92.1 [74.2,106.7] | 0.36 | 0.150 / 0.125 | 0.14 | 26.3 / 27.8 | 0.32 |
| X' | 3.3 | 2.7 [1.4,3.7] | 0.18 | 80.8 | 85.1 [69.2,109.6] | 0.36 | 0.041 / 0.033 | 0.22 | 27.9 / 31.5 | 0.26 |

### References (mean $k/wk / maxDD $k / Calmar / ulcer $k)
| layer | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| shipped layer, scale 1.00 | 24.5 / DD 104.8 / Cal 0.234 / U 39.4 | 7.7 / DD 63.9 / Cal 0.121 / U 35.9 | 27.0 / DD 104.8 / Cal 0.258 / U 44.5 | 22.6 / DD 122.0 / Cal 0.185 / U 44.7 | 16.9 / DD 59.7 / Cal 0.282 / U 20.2 | 13.2 / DD 88.2 / Cal 0.150 / U 26.3 | 3.3 / DD 80.8 / Cal 0.041 / U 27.9 |
| no layer, scale 0.931 (equal worst-20, gap 2.5%) | 23.3 / DD 126.6 / Cal 0.185 / U 45.3 | 7.0 / DD 77.6 / Cal 0.090 / U 41.0 | 24.7 / DD 126.6 / Cal 0.195 / U 52.6 | 21.1 / DD 126.6 / Cal 0.167 / U 45.4 | 18.4 / DD 45.8 / Cal 0.401 / U 14.3 | 12.1 / DD 87.1 / Cal 0.138 / U 26.2 | 2.6 / DD 101.9 / Cal 0.026 / U 35.9 |
| none layer, uniform lot scale 0.8 | 19.2 / DD 136.4 / Cal 0.141 / U 47.6 | 5.6 / DD 85.6 / Cal 0.065 / U 42.4 | 19.9 / DD 136.4 / Cal 0.146 / U 55.6 | 17.8 / DD 136.4 / Cal 0.131 / U 46.7 | 16.1 / DD 37.3 / Cal 0.431 / U 11.9 | 10.8 / DD 85.4 / Cal 0.126 / U 23.6 | 1.6 / DD 89.3 / Cal 0.018 / U 32.6 |
| shipped layer, uniform lot scale 0.8 | 19.0 / DD 129.7 / Cal 0.147 / U 46.1 | 5.4 / DD 76.3 / Cal 0.071 / U 37.5 | 21.0 / DD 129.7 / Cal 0.162 / U 53.2 | 17.8 / DD 129.7 / Cal 0.137 / U 48.3 | 13.1 / DD 50.3 / Cal 0.260 / U 16.9 | 11.0 / DD 76.6 / Cal 0.144 / U 21.5 | 2.1 / DD 78.8 / Cal 0.026 / U 28.1 |
| none layer, uniform lot scale 0.9 | 21.9 / DD 103.8 / Cal 0.210 / U 33.6 | 6.1 / DD 89.8 / Cal 0.067 / U 45.1 | 23.2 / DD 103.8 / Cal 0.224 / U 38.8 | 20.2 / DD 103.8 / Cal 0.195 / U 36.1 | 17.0 / DD 37.7 / Cal 0.449 / U 12.3 | 11.2 / DD 89.4 / Cal 0.125 / U 26.6 | 2.4 / DD 85.6 / Cal 0.028 / U 30.9 |
| shipped layer, uniform lot scale 0.9 | 21.5 / DD 89.5 / Cal 0.240 / U 30.9 | 6.8 / DD 71.7 / Cal 0.095 / U 37.0 | 23.6 / DD 89.5 / Cal 0.264 / U 34.7 | 19.9 / DD 103.3 / Cal 0.193 / U 36.8 | 14.9 / DD 48.2 / Cal 0.309 / U 16.6 | 11.7 / DD 78.8 / Cal 0.149 / U 24.0 | 2.7 / DD 75.5 / Cal 0.036 / U 26.9 |
| none layer, uniform lot scale 0.95 | 24.1 / DD 134.3 / Cal 0.180 / U 48.3 | 7.1 / DD 80.9 / Cal 0.088 / U 42.8 | 25.7 / DD 134.3 / Cal 0.191 / U 56.2 | 22.3 / DD 134.3 / Cal 0.166 / U 47.9 | 18.6 / DD 46.9 / Cal 0.397 / U 14.7 | 12.5 / DD 91.2 / Cal 0.138 / U 27.2 | 2.8 / DD 101.5 / Cal 0.028 / U 36.0 |
| shipped layer, uniform lot scale 0.95 | 23.6 / DD 117.9 / Cal 0.200 / U 44.8 | 8.0 / DD 61.9 / Cal 0.130 / U 34.5 | 26.2 / DD 117.9 / Cal 0.223 / U 51.0 | 21.9 / DD 117.9 / Cal 0.186 / U 47.7 | 15.8 / DD 59.6 / Cal 0.265 / U 20.4 | 13.1 / DD 82.2 / Cal 0.159 / U 24.9 | 3.4 / DD 81.8 / Cal 0.041 / U 28.2 |
| none layer, uniform lot scale 1.0 | 24.5 / DD 122.3 / Cal 0.200 / U 43.5 | 6.8 / DD 82.7 / Cal 0.082 / U 44.1 | 26.0 / DD 122.3 / Cal 0.213 / U 50.3 | 22.5 / DD 122.3 / Cal 0.184 / U 45.2 | 18.9 / DD 50.0 / Cal 0.377 / U 15.5 | 12.8 / DD 98.3 / Cal 0.130 / U 28.5 | 2.8 / DD 98.5 / Cal 0.029 / U 34.8 |

## 12R combined lock

### A: same count per month: 100 draws; equal-risk lot scale of the placebo layers: median 0.984 [0.858, 1.123] (shipped = 1.000); residual risk gap max 6.8%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 18.8 | 17.3 [14.0,20.6] | 0.24 | 97.8 | 122.7 [67.6,155.7] | 0.24 | 0.192 / 0.143 | 0.23 | 32.0 / 41.3 | 0.23 |
| L3M | 11.4 | 9.0 [6.4,11.1] | 0.04 | 53.9 | 67.1 [46.9,80.6] | 0.20 | 0.210 / 0.133 | 0.11 | 20.6 / 26.6 | 0.20 |
| L6M | 22.0 | 19.5 [15.9,23.3] | 0.14 | 97.8 | 122.7 [68.8,155.7] | 0.24 | 0.225 / 0.161 | 0.20 | 36.1 / 48.1 | 0.25 |
| HOLD | 19.1 | 17.9 [15.1,20.7] | 0.22 | 97.8 | 122.7 [67.6,155.7] | 0.24 | 0.195 / 0.148 | 0.23 | 29.8 / 36.9 | 0.25 |
| MID | 9.9 | 11.0 [7.4,15.5] | 0.61 | 34.7 | 44.1 [31.5,60.1] | 0.10 | 0.285 / 0.245 | 0.32 | 16.2 / 19.0 | 0.19 |
| PRE | 6.2 | 7.5 [5.6,9.1] | 0.88 | 93.0 | 101.8 [80.7,141.3] | 0.31 | 0.067 / 0.074 | 0.63 | 37.6 / 43.1 | 0.15 |
| X' | -2.6 | -1.2 [-3.0,0.6] | 0.87 | 160.9 | 136.1 [89.2,178.0] | 0.86 | -0.016 / -0.010 | 0.83 | 102.7 / 74.8 | 0.87 |

### B: same count per month x book x session: 50 draws; equal-risk lot scale of the placebo layers: median 1.006 [0.877, 1.172] (shipped = 1.000); residual risk gap max 4.5%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 18.8 | 17.7 [14.4,19.4] | 0.20 | 97.8 | 120.0 [94.5,155.9] | 0.16 | 0.192 / 0.142 | 0.12 | 32.0 / 40.0 | 0.10 |
| L3M | 11.4 | 9.1 [6.9,10.7] | 0.00 | 53.9 | 66.4 [52.4,82.3] | 0.12 | 0.210 / 0.132 | 0.06 | 20.6 / 26.8 | 0.04 |
| L6M | 22.0 | 19.8 [15.5,22.1] | 0.06 | 97.8 | 120.0 [94.5,155.9] | 0.16 | 0.225 / 0.153 | 0.06 | 36.1 / 46.2 | 0.12 |
| HOLD | 19.1 | 18.3 [15.6,19.8] | 0.12 | 97.8 | 120.0 [94.5,155.9] | 0.16 | 0.195 / 0.145 | 0.08 | 29.8 / 36.1 | 0.10 |
| MID | 9.9 | 11.7 [7.1,15.8] | 0.68 | 34.7 | 46.4 [33.1,61.4] | 0.10 | 0.285 / 0.255 | 0.38 | 16.2 / 19.6 | 0.20 |
| PRE | 6.2 | 7.6 [6.2,9.2] | 0.94 | 93.0 | 102.8 [83.9,133.8] | 0.18 | 0.067 / 0.071 | 0.62 | 37.6 / 46.3 | 0.10 |
| X' | -2.6 | -2.3 [-3.9,-0.5] | 0.68 | 160.9 | 145.7 [112.0,191.8] | 0.76 | -0.016 / -0.016 | 0.48 | 102.7 / 89.9 | 0.84 |

### References (mean $k/wk / maxDD $k / Calmar / ulcer $k)
| layer | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| shipped layer, scale 1.00 | 18.8 / DD 97.8 / Cal 0.192 / U 32.0 | 11.4 / DD 53.9 / Cal 0.210 / U 20.6 | 22.0 / DD 97.8 / Cal 0.225 / U 36.1 | 19.1 / DD 97.8 / Cal 0.195 / U 29.8 | 9.9 / DD 34.7 / Cal 0.285 / U 16.2 | 6.2 / DD 93.0 / Cal 0.067 / U 37.6 | -2.6 / DD 160.9 / Cal -0.016 / U 102.7 |
| no layer, scale 0.873 (equal worst-20, gap 0.2%) | 15.9 / DD 92.5 / Cal 0.172 / U 27.9 | 7.8 / DD 79.1 / Cal 0.099 / U 31.8 | 17.7 / DD 92.5 / Cal 0.191 / U 30.6 | 15.9 / DD 92.5 / Cal 0.172 / U 26.2 | 10.6 / DD 41.1 / Cal 0.258 / U 17.8 | 7.2 / DD 108.1 / Cal 0.066 / U 48.9 | -2.0 / DD 152.3 / Cal -0.013 / U 96.1 |
| none layer, uniform lot scale 0.8 | 14.3 / DD 161.0 / Cal 0.089 / U 56.6 | 7.6 / DD 79.4 / Cal 0.096 / U 31.9 | 15.4 / DD 161.0 / Cal 0.096 / U 65.8 | 14.6 / DD 161.0 / Cal 0.091 / U 49.7 | 10.8 / DD 38.3 / Cal 0.281 / U 17.1 | 6.6 / DD 97.7 / Cal 0.068 / U 45.8 | -2.0 / DD 156.1 / Cal -0.013 / U 97.6 |
| shipped layer, uniform lot scale 0.8 | 14.4 / DD 143.7 / Cal 0.100 / U 51.8 | 8.1 / DD 62.4 / Cal 0.130 / U 24.6 | 16.3 / DD 143.7 / Cal 0.113 / U 59.7 | 14.9 / DD 143.7 / Cal 0.104 / U 46.2 | 9.1 / DD 41.8 / Cal 0.217 / U 19.4 | 6.7 / DD 87.5 / Cal 0.076 / U 36.1 | -2.2 / DD 161.7 / Cal -0.014 / U 98.9 |
| none layer, uniform lot scale 0.9 | 17.6 / DD 83.2 / Cal 0.212 / U 24.1 | 8.7 / DD 78.0 / Cal 0.112 / U 31.2 | 19.1 / DD 83.2 / Cal 0.230 / U 26.9 | 17.6 / DD 83.2 / Cal 0.211 / U 22.8 | 12.8 / DD 34.1 / Cal 0.374 / U 13.5 | 7.5 / DD 104.5 / Cal 0.072 / U 49.2 | -2.5 / DD 135.4 / Cal -0.019 / U 86.1 |
| shipped layer, uniform lot scale 0.9 | 17.0 / DD 86.1 / Cal 0.198 / U 27.2 | 9.8 / DD 56.8 / Cal 0.172 / U 22.0 | 19.1 / DD 86.1 / Cal 0.222 / U 30.7 | 17.2 / DD 86.1 / Cal 0.199 / U 25.7 | 11.0 / DD 38.1 / Cal 0.288 / U 13.7 | 7.1 / DD 89.5 / Cal 0.080 / U 39.2 | -0.4 / DD 143.1 / Cal -0.003 / U 72.2 |
| none layer, uniform lot scale 0.95 | 16.9 / DD 163.6 / Cal 0.104 / U 56.9 | 10.1 / DD 79.5 / Cal 0.127 / U 31.2 | 19.4 / DD 163.6 / Cal 0.119 / U 66.1 | 17.4 / DD 163.6 / Cal 0.106 / U 49.9 | 10.0 / DD 39.4 / Cal 0.254 / U 18.0 | 7.4 / DD 98.7 / Cal 0.075 / U 47.0 | -2.0 / DD 135.8 / Cal -0.015 / U 78.7 |
| shipped layer, uniform lot scale 0.95 | 18.4 / DD 97.8 / Cal 0.188 / U 31.9 | 11.4 / DD 53.9 / Cal 0.211 / U 20.6 | 21.8 / DD 97.8 / Cal 0.223 / U 36.1 | 18.4 / DD 97.8 / Cal 0.188 / U 29.9 | 9.2 / DD 34.9 / Cal 0.263 / U 15.9 | 6.0 / DD 91.6 / Cal 0.065 / U 36.3 | -2.9 / DD 174.4 / Cal -0.016 / U 114.4 |
| none layer, uniform lot scale 1.0 | 17.1 / DD 163.4 / Cal 0.105 / U 57.0 | 10.0 / DD 79.3 / Cal 0.126 / U 31.2 | 19.5 / DD 163.4 / Cal 0.119 / U 66.1 | 17.8 / DD 163.4 / Cal 0.109 / U 49.9 | 10.3 / DD 40.2 / Cal 0.257 / U 18.2 | 7.9 / DD 100.4 / Cal 0.078 / U 47.5 | -2.1 / DD 135.8 / Cal -0.015 / U 80.1 |
