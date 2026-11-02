# DS3 ZONES LAYER vs SIZE - is the shipped HALF layer better than random halving at EQUAL RISK? (BASE-4, 2026-11-02T14:28Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Method: placebo layer = the shipped 7-line HALF mask (D20, half lots) replaced by a random half-lot mask with the same number of LIVE rows (A = same count per month, 100 draws; B = same count per month x book x session, 50 draws); OTE-62 B73, TH-L2 loss, profit lines, locks, sizer unchanged. Every placebo (and the references) has its WHOLE lot table scaled (engine lscale, integer-lot rounding) until the worst-20-weeks sum over ALL history equals the shipped layer's at scale 1 in the same frame (stop at |gap| <= 2.5% (<=5 engine runs); the residual gap is corrected linearly in mean, maxDD and ulcer: x target/achieved). Metrics per window: weekly mean ($k/wk), maxDD ($k, weekly cumulative), Calmar (mean/maxDD), ulcer (RMS of the weekly drawdown path, $k). RANK = share of placebo draws that are at least as GOOD as the shipped layer (higher mean / lower maxDD / higher Calmar / lower ulcer); small rank = the shipped layer beats random halving; ~0.5 = indistinguishable. Frames: lock none = per-book locks only (headline), 12R = + combined stack lock. Post-hoc.

## LOCK NONE (headline)

### A: same count per month: 100 draws; equal-risk lot scale of the placebo layers: median 1.017 [0.979, 1.106] (shipped = 1.000); residual risk gap max 4.2%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 33.7 | 32.4 [29.6,36.5] | 0.27 | 150.7 | 146.3 [97.9,191.1] | 0.59 | 0.224 / 0.226 | 0.53 | 52.8 / 53.4 | 0.49 |
| L3M | 14.7 | 12.3 [8.6,16.7] | 0.14 | 94.0 | 91.1 [80.1,119.5] | 0.60 | 0.157 / 0.136 | 0.25 | 39.4 / 46.2 | 0.17 |
| L6M | 36.7 | 35.3 [31.8,39.4] | 0.25 | 150.7 | 146.3 [97.9,191.1] | 0.59 | 0.244 / 0.244 | 0.51 | 61.3 / 61.9 | 0.47 |
| HOLD | 30.4 | 30.5 [27.6,34.8] | 0.52 | 150.7 | 147.4 [113.3,191.1] | 0.56 | 0.202 / 0.207 | 0.55 | 54.2 / 52.6 | 0.63 |
| MID | 24.0 | 23.3 [19.3,28.5] | 0.42 | 43.7 | 48.8 [33.6,63.2] | 0.27 | 0.549 / 0.474 | 0.33 | 16.8 / 17.5 | 0.41 |
| PRE | 17.3 | 15.1 [12.4,17.4] | 0.06 | 166.2 | 167.9 [148.7,185.4] | 0.41 | 0.104 / 0.091 | 0.06 | 51.0 / 52.7 | 0.39 |
| X' | 4.8 | 4.7 [2.3,6.6] | 0.47 | 92.5 | 75.1 [53.7,108.5] | 0.85 | 0.052 / 0.064 | 0.71 | 36.9 / 33.1 | 0.81 |

### B: same count per month x book x session: 50 draws; equal-risk lot scale of the placebo layers: median 1.023 [0.959, 1.087] (shipped = 1.000); residual risk gap max 3.0%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 33.7 | 32.0 [29.9,35.1] | 0.22 | 150.7 | 147.8 [107.1,193.2] | 0.52 | 0.224 / 0.221 | 0.48 | 52.8 / 53.6 | 0.48 |
| L3M | 14.7 | 12.0 [8.3,16.2] | 0.10 | 94.0 | 91.9 [76.7,126.8] | 0.58 | 0.157 / 0.133 | 0.22 | 39.4 / 46.0 | 0.14 |
| L6M | 36.7 | 35.1 [32.0,37.7] | 0.22 | 150.7 | 147.8 [107.1,193.2] | 0.52 | 0.244 / 0.237 | 0.48 | 61.3 / 61.4 | 0.50 |
| HOLD | 30.4 | 29.5 [28.0,32.7] | 0.34 | 150.7 | 152.8 [127.9,193.2] | 0.44 | 0.202 / 0.195 | 0.46 | 54.2 / 53.2 | 0.54 |
| MID | 24.0 | 23.0 [18.9,26.5] | 0.34 | 43.7 | 53.2 [35.3,69.6] | 0.24 | 0.549 / 0.426 | 0.26 | 16.8 / 18.9 | 0.30 |
| PRE | 17.3 | 14.9 [12.5,17.1] | 0.04 | 166.2 | 165.1 [146.1,194.7] | 0.56 | 0.104 / 0.091 | 0.16 | 51.0 / 54.2 | 0.30 |
| X' | 4.8 | 4.1 [2.2,6.4] | 0.32 | 92.5 | 77.9 [62.3,96.6] | 0.88 | 0.052 / 0.052 | 0.52 | 36.9 / 32.6 | 0.70 |

### References (mean $k/wk / maxDD $k / Calmar / ulcer $k)
| layer | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| shipped layer, scale 1.00 | 33.7 / DD 150.7 / Cal 0.224 / U 52.8 | 14.7 / DD 94.0 / Cal 0.157 / U 39.4 | 36.7 / DD 150.7 / Cal 0.244 / U 61.3 | 30.4 / DD 150.7 / Cal 0.202 / U 54.2 | 24.0 / DD 43.7 / Cal 0.549 / U 16.8 | 17.3 / DD 166.2 / Cal 0.104 / U 51.0 | 4.8 / DD 92.5 / Cal 0.052 / U 36.9 |
| no layer, scale 0.950 (equal worst-20, gap 0.9%) | 31.6 / DD 144.9 / Cal 0.218 / U 51.4 | 11.9 / DD 83.8 / Cal 0.142 / U 43.1 | 33.8 / DD 144.9 / Cal 0.233 / U 59.6 | 29.6 / DD 144.9 / Cal 0.204 / U 51.0 | 24.2 / DD 47.9 / Cal 0.505 / U 16.7 | 13.3 / DD 172.4 / Cal 0.077 / U 55.1 | 4.5 / DD 75.7 / Cal 0.059 / U 30.8 |
| none layer, uniform lot scale 0.8 | 26.5 / DD 100.5 / Cal 0.263 / U 39.3 | 11.3 / DD 71.1 / Cal 0.159 / U 37.1 | 28.6 / DD 100.5 / Cal 0.285 / U 45.1 | 24.5 / DD 118.2 / Cal 0.207 / U 42.1 | 19.5 / DD 47.8 / Cal 0.408 / U 15.9 | 12.2 / DD 126.2 / Cal 0.096 / U 40.0 | 4.1 / DD 57.1 / Cal 0.072 / U 24.2 |
| shipped layer, uniform lot scale 0.8 | 25.4 / DD 90.1 / Cal 0.281 / U 36.7 | 11.2 / DD 72.4 / Cal 0.155 / U 31.7 | 27.9 / DD 90.1 / Cal 0.310 / U 40.7 | 23.1 / DD 131.7 / Cal 0.175 / U 42.8 | 17.4 / DD 66.6 / Cal 0.261 / U 21.8 | 12.6 / DD 120.2 / Cal 0.105 / U 36.3 | 3.8 / DD 53.3 / Cal 0.071 / U 22.5 |
| none layer, uniform lot scale 0.9 | 27.8 / DD 144.6 / Cal 0.192 / U 52.0 | 10.4 / DD 81.9 / Cal 0.127 / U 43.4 | 29.8 / DD 144.6 / Cal 0.206 / U 60.4 | 26.0 / DD 144.6 / Cal 0.180 / U 51.4 | 21.0 / DD 44.9 / Cal 0.467 / U 16.1 | 12.3 / DD 164.3 / Cal 0.075 / U 52.2 | 3.9 / DD 78.2 / Cal 0.050 / U 30.1 |
| shipped layer, uniform lot scale 0.9 | 27.4 / DD 114.4 / Cal 0.239 / U 43.0 | 10.9 / DD 73.2 / Cal 0.149 / U 37.4 | 31.3 / DD 114.4 / Cal 0.273 / U 48.3 | 25.1 / DD 138.8 / Cal 0.181 / U 48.2 | 16.3 / DD 70.5 / Cal 0.231 / U 23.4 | 12.3 / DD 143.6 / Cal 0.085 / U 48.0 | 3.7 / DD 68.0 / Cal 0.055 / U 26.3 |
| none layer, uniform lot scale 0.95 | 31.9 / DD 146.2 / Cal 0.218 / U 51.8 | 12.0 / DD 84.5 / Cal 0.142 / U 43.5 | 34.1 / DD 146.2 / Cal 0.233 / U 60.1 | 29.9 / DD 146.2 / Cal 0.204 / U 51.5 | 24.4 / DD 48.3 / Cal 0.505 / U 16.8 | 13.4 / DD 173.9 / Cal 0.077 / U 55.6 | 4.5 / DD 76.4 / Cal 0.059 / U 31.1 |
| shipped layer, uniform lot scale 0.95 | 31.6 / DD 112.0 / Cal 0.282 / U 42.5 | 13.0 / DD 83.7 / Cal 0.155 / U 36.4 | 35.0 / DD 112.0 / Cal 0.312 / U 48.6 | 28.8 / DD 120.5 / Cal 0.239 / U 45.5 | 21.5 / DD 51.2 / Cal 0.419 / U 18.4 | 13.9 / DD 154.7 / Cal 0.090 / U 48.9 | 4.3 / DD 57.5 / Cal 0.074 / U 26.1 |
| none layer, uniform lot scale 1.0 | 34.2 / DD 162.6 / Cal 0.210 / U 61.3 | 14.9 / DD 95.4 / Cal 0.157 / U 44.7 | 36.7 / DD 162.6 / Cal 0.226 / U 71.2 | 31.0 / DD 162.6 / Cal 0.191 / U 61.3 | 25.7 / DD 58.5 / Cal 0.439 / U 19.3 | 16.9 / DD 178.1 / Cal 0.095 / U 54.6 | 5.3 / DD 79.5 / Cal 0.066 / U 33.9 |

## 12R combined lock

### A: same count per month: 100 draws; equal-risk lot scale of the placebo layers: median 0.992 [0.913, 1.066] (shipped = 1.000); residual risk gap max 5.1%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 27.2 | 23.9 [21.0,28.5] | 0.07 | 151.0 | 143.6 [105.7,173.9] | 0.68 | 0.180 / 0.169 | 0.34 | 52.7 / 50.8 | 0.64 |
| L3M | 15.2 | 11.4 [7.2,20.4] | 0.30 | 62.8 | 69.1 [46.0,91.5] | 0.37 | 0.242 / 0.189 | 0.30 | 25.0 / 27.7 | 0.31 |
| L6M | 29.6 | 26.7 [22.3,31.8] | 0.19 | 151.0 | 143.6 [105.7,173.9] | 0.68 | 0.196 / 0.186 | 0.40 | 61.2 / 58.4 | 0.67 |
| HOLD | 24.9 | 24.0 [20.8,27.7] | 0.28 | 151.0 | 143.6 [105.7,173.9] | 0.68 | 0.165 / 0.171 | 0.57 | 49.0 / 47.0 | 0.74 |
| MID | 19.5 | 16.5 [10.2,21.9] | 0.20 | 44.2 | 49.7 [38.1,68.4] | 0.30 | 0.440 / 0.344 | 0.20 | 16.6 / 19.1 | 0.20 |
| PRE | 9.5 | 8.7 [6.2,11.8] | 0.36 | 133.6 | 159.8 [128.1,206.7] | 0.11 | 0.071 / 0.056 | 0.17 | 55.7 / 69.3 | 0.07 |
| X' | -4.5 | -2.3 [-5.3,0.4] | 0.89 | 229.4 | 168.6 [96.8,262.6] | 0.85 | -0.020 / -0.013 | 0.80 | 131.5 / 93.0 | 0.84 |

### B: same count per month x book x session: 50 draws; equal-risk lot scale of the placebo layers: median 1.016 [0.978, 1.088] (shipped = 1.000); residual risk gap max 5.8%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 27.2 | 24.0 [19.4,29.5] | 0.14 | 151.0 | 149.9 [125.8,176.0] | 0.54 | 0.180 / 0.162 | 0.24 | 52.7 / 51.7 | 0.56 |
| L3M | 15.2 | 11.5 [6.9,19.8] | 0.30 | 62.8 | 74.1 [51.5,93.1] | 0.22 | 0.242 / 0.171 | 0.20 | 25.0 / 30.4 | 0.16 |
| L6M | 29.6 | 27.2 [21.4,32.6] | 0.20 | 151.0 | 149.9 [125.8,176.0] | 0.54 | 0.196 / 0.182 | 0.30 | 61.2 / 59.7 | 0.58 |
| HOLD | 24.9 | 23.8 [19.5,27.5] | 0.28 | 151.0 | 149.9 [125.8,176.0] | 0.54 | 0.165 / 0.162 | 0.42 | 49.0 / 48.0 | 0.64 |
| MID | 19.5 | 15.3 [10.6,21.1] | 0.14 | 44.2 | 50.5 [41.1,68.3] | 0.16 | 0.440 / 0.319 | 0.12 | 16.6 / 21.4 | 0.08 |
| PRE | 9.5 | 9.4 [6.0,11.5] | 0.46 | 133.6 | 173.0 [133.1,216.2] | 0.08 | 0.071 / 0.053 | 0.20 | 55.7 / 71.1 | 0.04 |
| X' | -4.5 | -3.8 [-7.1,-1.0] | 0.62 | 229.4 | 211.5 [112.1,344.9] | 0.56 | -0.020 / -0.018 | 0.62 | 131.5 / 133.0 | 0.46 |

### References (mean $k/wk / maxDD $k / Calmar / ulcer $k)
| layer | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| shipped layer, scale 1.00 | 27.2 / DD 151.0 / Cal 0.180 / U 52.7 | 15.2 / DD 62.8 / Cal 0.242 / U 25.0 | 29.6 / DD 151.0 / Cal 0.196 / U 61.2 | 24.9 / DD 151.0 / Cal 0.165 / U 49.0 | 19.5 / DD 44.2 / Cal 0.440 / U 16.6 | 9.5 / DD 133.6 / Cal 0.071 / U 55.7 | -4.5 / DD 229.4 / Cal -0.020 / U 131.5 |
| no layer, scale 0.916 (equal worst-20, gap 2.4%) | 23.0 / DD 144.2 / Cal 0.159 / U 49.1 | 9.7 / DD 70.1 / Cal 0.139 / U 27.9 | 23.8 / DD 144.2 / Cal 0.165 / U 57.0 | 22.0 / DD 144.2 / Cal 0.152 / U 44.9 | 19.3 / DD 41.1 / Cal 0.471 / U 15.4 | 9.5 / DD 141.1 / Cal 0.067 / U 58.6 | -2.1 / DD 159.9 / Cal -0.013 / U 89.9 |
| none layer, uniform lot scale 0.8 | 20.0 / DD 121.8 / Cal 0.164 / U 40.9 | 8.0 / DD 64.6 / Cal 0.124 / U 26.2 | 20.9 / DD 121.8 / Cal 0.172 / U 47.4 | 20.7 / DD 121.8 / Cal 0.170 / U 36.4 | 16.0 / DD 36.6 / Cal 0.439 / U 13.8 | 8.0 / DD 157.8 / Cal 0.050 / U 64.2 | -3.2 / DD 160.5 / Cal -0.020 / U 84.7 |
| shipped layer, uniform lot scale 0.8 | 19.5 / DD 105.7 / Cal 0.185 / U 37.5 | 9.2 / DD 47.0 / Cal 0.196 / U 20.7 | 21.0 / DD 105.7 / Cal 0.198 / U 43.4 | 18.4 / DD 105.7 / Cal 0.174 / U 36.5 | 14.7 / DD 34.5 / Cal 0.426 / U 12.9 | 6.4 / DD 126.6 / Cal 0.050 / U 55.6 | -3.9 / DD 199.2 / Cal -0.020 / U 114.8 |
| none layer, uniform lot scale 0.9 | 21.4 / DD 142.8 / Cal 0.150 / U 48.9 | 9.0 / DD 71.4 / Cal 0.126 / U 28.9 | 22.4 / DD 142.8 / Cal 0.157 / U 56.7 | 21.0 / DD 142.8 / Cal 0.147 / U 44.6 | 17.4 / DD 42.2 / Cal 0.413 / U 15.5 | 8.0 / DD 160.2 / Cal 0.050 / U 69.2 | -1.6 / DD 129.4 / Cal -0.012 / U 72.5 |
| shipped layer, uniform lot scale 0.9 | 21.5 / DD 129.9 / Cal 0.165 / U 44.8 | 10.7 / DD 57.9 / Cal 0.185 / U 23.0 | 23.6 / DD 129.9 / Cal 0.182 / U 52.0 | 20.4 / DD 129.9 / Cal 0.157 / U 42.5 | 14.9 / DD 38.6 / Cal 0.386 / U 14.7 | 6.1 / DD 131.6 / Cal 0.046 / U 55.3 | -2.5 / DD 134.1 / Cal -0.019 / U 87.2 |
| none layer, uniform lot scale 0.95 | 24.1 / DD 151.9 / Cal 0.159 / U 51.5 | 10.3 / DD 76.2 / Cal 0.135 / U 30.5 | 25.3 / DD 151.9 / Cal 0.167 / U 59.8 | 23.6 / DD 151.9 / Cal 0.156 / U 47.2 | 19.4 / DD 42.1 / Cal 0.460 / U 16.4 | 9.5 / DD 169.5 / Cal 0.056 / U 68.6 | -3.6 / DD 215.5 / Cal -0.017 / U 129.2 |
| shipped layer, uniform lot scale 0.95 | 24.5 / DD 134.1 / Cal 0.183 / U 46.4 | 12.5 / DD 57.6 / Cal 0.217 / U 22.8 | 26.6 / DD 134.1 / Cal 0.198 / U 53.8 | 22.1 / DD 134.1 / Cal 0.165 / U 44.9 | 17.8 / DD 41.0 / Cal 0.433 / U 15.5 | 7.2 / DD 129.6 / Cal 0.056 / U 56.1 | -3.8 / DD 196.7 / Cal -0.019 / U 120.4 |
| none layer, uniform lot scale 1.0 | 26.6 / DD 166.0 / Cal 0.160 / U 56.9 | 12.6 / DD 83.4 / Cal 0.151 / U 33.7 | 28.6 / DD 166.0 / Cal 0.172 / U 65.4 | 24.9 / DD 166.0 / Cal 0.150 / U 52.6 | 19.7 / DD 53.5 / Cal 0.369 / U 23.1 | 11.4 / DD 182.2 / Cal 0.063 / U 76.7 | -5.4 / DD 294.8 / Cal -0.018 / U 175.3 |
