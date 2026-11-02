# DS3 ZONES LAYER vs SIZE - is the shipped HALF layer better than random halving at EQUAL RISK? (BASE-4, 2026-11-02T06:48Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Method: placebo layer = the shipped 7-line HALF mask (D20, half lots) replaced by a random half-lot mask with the same number of LIVE rows (A = same count per month, 100 draws; B = same count per month x book x session, 50 draws); OTE-62 B73, TH-L2 loss, profit lines, locks, sizer unchanged. Every placebo (and the references) has its WHOLE lot table scaled (engine lscale, integer-lot rounding) until the worst-20-weeks sum over ALL history equals the shipped layer's at scale 1 in the same frame (stop at |gap| <= 2.5% (<=5 engine runs); the residual gap is corrected linearly in mean, maxDD and ulcer: x target/achieved). Metrics per window: weekly mean ($k/wk), maxDD ($k, weekly cumulative), Calmar (mean/maxDD), ulcer (RMS of the weekly drawdown path, $k). RANK = share of placebo draws that are at least as GOOD as the shipped layer (higher mean / lower maxDD / higher Calmar / lower ulcer); small rank = the shipped layer beats random halving; ~0.5 = indistinguishable. Frames: lock none = per-book locks only (headline), 12R = + combined stack lock. Post-hoc.

## LOCK NONE (headline)

### A: same count per month: 93 draws; equal-risk lot scale of the placebo layers: median 1.011 [0.940, 1.089] (shipped = 1.000); residual risk gap max 6.3%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 22.5 | 22.3 [20.5,26.4] | 0.47 | 132.6 | 135.5 [101.3,174.7] | 0.42 | 0.170 / 0.166 | 0.43 | 54.1 / 56.5 | 0.41 |
| L3M | 16.1 | 14.2 [10.5,17.6] | 0.14 | 49.9 | 50.0 [38.5,67.5] | 0.49 | 0.324 / 0.289 | 0.34 | 27.1 / 26.4 | 0.55 |
| L6M | 26.9 | 26.3 [23.8,29.5] | 0.39 | 132.6 | 135.5 [101.3,174.7] | 0.42 | 0.202 / 0.193 | 0.39 | 61.4 / 64.3 | 0.42 |
| HOLD | 23.9 | 24.1 [21.7,28.2] | 0.57 | 132.6 | 136.3 [113.3,174.7] | 0.40 | 0.180 / 0.174 | 0.42 | 59.4 / 56.2 | 0.69 |
| MID | 10.9 | 11.9 [8.0,18.2] | 0.65 | 62.6 | 77.8 [60.1,94.1] | 0.10 | 0.174 / 0.154 | 0.39 | 25.7 / 28.1 | 0.20 |
| PRE | 10.0 | 7.8 [5.4,10.1] | 0.06 | 178.4 | 212.2 [168.0,293.8] | 0.11 | 0.056 / 0.036 | 0.05 | 81.3 / 95.7 | 0.13 |
| X' | -1.2 | -0.5 [-2.5,1.1] | 0.83 | 134.8 | 126.5 [91.2,177.3] | 0.62 | -0.009 / -0.004 | 0.81 | 66.6 / 56.0 | 0.69 |

### References (mean $k/wk / maxDD $k / Calmar / ulcer $k)
| layer | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| shipped layer, scale 1.00 | 22.5 / DD 132.6 / Cal 0.170 / U 54.1 | 16.1 / DD 49.9 / Cal 0.324 / U 27.1 | 26.9 / DD 132.6 / Cal 0.202 / U 61.4 | 23.9 / DD 132.6 / Cal 0.180 / U 59.4 | 10.9 / DD 62.6 / Cal 0.174 / U 25.7 | 10.0 / DD 178.4 / Cal 0.056 / U 81.3 | -1.2 / DD 134.8 / Cal -0.009 / U 66.6 |
| no layer, scale 0.950 (equal worst-20, gap 2.5%) | 20.2 / DD 151.7 / Cal 0.133 / U 61.9 | 11.9 / DD 49.5 / Cal 0.240 / U 25.8 | 23.3 / DD 151.7 / Cal 0.154 / U 71.0 | 21.2 / DD 151.7 / Cal 0.139 / U 60.8 | 11.4 / DD 65.8 / Cal 0.173 / U 24.8 | 5.2 / DD 317.9 / Cal 0.016 / U 145.7 | -1.6 / DD 151.0 / Cal -0.010 / U 77.4 |
| none layer, uniform lot scale 0.8 | 18.2 / DD 114.2 / Cal 0.159 / U 45.8 | 12.0 / DD 44.9 / Cal 0.268 / U 22.8 | 21.0 / DD 114.2 / Cal 0.184 / U 51.8 | 18.4 / DD 114.2 / Cal 0.161 / U 48.6 | 10.2 / DD 60.7 / Cal 0.168 / U 22.6 | 5.9 / DD 171.3 / Cal 0.035 / U 82.3 | -1.1 / DD 123.8 / Cal -0.009 / U 60.5 |
| shipped layer, uniform lot scale 0.8 | 18.0 / DD 109.3 / Cal 0.165 / U 43.0 | 12.9 / DD 43.0 / Cal 0.300 / U 21.7 | 20.3 / DD 109.3 / Cal 0.185 / U 49.4 | 18.7 / DD 109.3 / Cal 0.171 / U 47.4 | 11.4 / DD 40.3 / Cal 0.283 / U 17.3 | 7.3 / DD 135.0 / Cal 0.054 / U 58.0 | -1.4 / DD 115.4 / Cal -0.012 / U 61.5 |
| none layer, uniform lot scale 0.9 | 19.2 / DD 142.5 / Cal 0.135 / U 57.6 | 11.4 / DD 50.8 / Cal 0.224 / U 26.7 | 21.7 / DD 142.5 / Cal 0.153 / U 66.1 | 19.6 / DD 142.5 / Cal 0.138 / U 56.8 | 12.0 / DD 62.2 / Cal 0.192 / U 23.1 | 5.4 / DD 261.7 / Cal 0.021 / U 117.6 | -1.6 / DD 145.1 / Cal -0.011 / U 75.7 |
| shipped layer, uniform lot scale 0.9 | 18.8 / DD 122.5 / Cal 0.153 / U 49.0 | 12.4 / DD 47.4 / Cal 0.262 / U 25.6 | 21.4 / DD 122.5 / Cal 0.175 / U 56.0 | 19.7 / DD 122.5 / Cal 0.161 / U 53.6 | 11.3 / DD 50.2 / Cal 0.225 / U 21.6 | 7.2 / DD 167.2 / Cal 0.043 / U 74.4 | -1.5 / DD 126.9 / Cal -0.012 / U 68.3 |
| none layer, uniform lot scale 0.95 | 20.7 / DD 155.5 / Cal 0.133 / U 63.4 | 12.2 / DD 50.8 / Cal 0.240 / U 26.4 | 23.9 / DD 155.5 / Cal 0.154 / U 72.9 | 21.7 / DD 155.5 / Cal 0.139 / U 62.4 | 11.7 / DD 67.5 / Cal 0.173 / U 25.4 | 5.3 / DD 326.0 / Cal 0.016 / U 149.4 | -1.6 / DD 154.8 / Cal -0.010 / U 79.4 |
| shipped layer, uniform lot scale 0.95 | 20.7 / DD 128.5 / Cal 0.161 / U 51.1 | 13.4 / DD 47.3 / Cal 0.283 / U 24.9 | 23.5 / DD 128.5 / Cal 0.183 / U 58.6 | 22.1 / DD 128.5 / Cal 0.172 / U 56.1 | 12.4 / DD 45.0 / Cal 0.276 / U 20.8 | 7.8 / DD 181.0 / Cal 0.043 / U 83.4 | -1.7 / DD 135.7 / Cal -0.012 / U 75.2 |
| none layer, uniform lot scale 1.0 | 23.2 / DD 145.8 / Cal 0.159 / U 60.7 | 14.8 / DD 53.4 / Cal 0.278 / U 29.5 | 27.4 / DD 145.8 / Cal 0.188 / U 68.7 | 23.3 / DD 145.8 / Cal 0.160 / U 64.9 | 11.7 / DD 77.7 / Cal 0.150 / U 30.0 | 7.7 / DD 245.1 / Cal 0.031 / U 112.2 | -1.8 / DD 190.0 / Cal -0.009 / U 92.7 |

## 12R combined lock

### References (mean $k/wk / maxDD $k / Calmar / ulcer $k)
| layer | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| shipped layer, scale 1.00 | 17.6 / DD 78.5 / Cal 0.224 / U 32.2 | 15.8 / DD 39.9 / Cal 0.395 / U 18.9 | 22.4 / DD 73.9 / Cal 0.303 / U 32.4 | 19.9 / DD 119.2 / Cal 0.167 / U 40.9 | 5.3 / DD 78.5 / Cal 0.068 / U 29.1 | 4.0 / DD 252.4 / Cal 0.016 / U 99.9 | -3.9 / DD 173.7 / Cal -0.023 / U 114.4 |
| no layer, scale 0.886 (equal worst-20, gap 1.3%) | 12.4 / DD 85.6 / Cal 0.144 / U 38.6 | 5.3 / DD 45.1 / Cal 0.118 / U 22.4 | 15.0 / DD 85.6 / Cal 0.175 / U 39.3 | 15.4 / DD 89.9 / Cal 0.172 / U 36.9 | 5.4 / DD 80.9 / Cal 0.067 / U 33.6 | 3.2 / DD 223.9 / Cal 0.014 / U 95.1 | -2.0 / DD 149.1 / Cal -0.014 / U 76.9 |
| none layer, uniform lot scale 0.8 | 11.6 / DD 75.6 / Cal 0.154 / U 29.2 | 5.7 / DD 32.1 / Cal 0.178 / U 18.3 | 14.5 / DD 57.9 / Cal 0.250 / U 27.4 | 14.9 / DD 85.9 / Cal 0.173 / U 29.4 | 4.3 / DD 75.6 / Cal 0.057 / U 30.5 | 3.8 / DD 172.0 / Cal 0.022 / U 67.0 | -1.8 / DD 120.5 / Cal -0.015 / U 61.2 |
| shipped layer, uniform lot scale 0.8 | 13.5 / DD 60.8 / Cal 0.222 / U 25.8 | 11.5 / DD 26.8 / Cal 0.429 / U 13.0 | 16.5 / DD 56.8 / Cal 0.290 / U 26.2 | 16.4 / DD 62.2 / Cal 0.264 / U 26.1 | 5.7 / DD 60.8 / Cal 0.094 / U 22.7 | 3.4 / DD 144.7 / Cal 0.024 / U 60.1 | -2.0 / DD 113.0 / Cal -0.018 / U 75.8 |
| none layer, uniform lot scale 0.9 | 12.0 / DD 86.2 / Cal 0.139 / U 39.0 | 5.2 / DD 45.2 / Cal 0.115 / U 22.2 | 14.6 / DD 86.2 / Cal 0.170 / U 39.8 | 15.1 / DD 90.3 / Cal 0.168 / U 36.9 | 5.1 / DD 81.7 / Cal 0.062 / U 33.9 | 2.9 / DD 237.7 / Cal 0.012 / U 96.6 | -2.1 / DD 150.7 / Cal -0.014 / U 77.9 |
| shipped layer, uniform lot scale 0.9 | 14.3 / DD 87.5 / Cal 0.163 / U 35.9 | 12.2 / DD 36.0 / Cal 0.338 / U 16.7 | 16.4 / DD 87.5 / Cal 0.188 / U 39.1 | 17.7 / DD 87.5 / Cal 0.203 / U 33.6 | 8.2 / DD 69.1 / Cal 0.119 / U 24.1 | 2.2 / DD 250.6 / Cal 0.009 / U 108.0 | -2.9 / DD 138.6 / Cal -0.021 / U 92.2 |
| none layer, uniform lot scale 0.95 | 13.2 / DD 97.1 / Cal 0.136 / U 41.4 | 5.6 / DD 46.3 / Cal 0.121 / U 24.6 | 16.8 / DD 89.9 / Cal 0.187 / U 39.9 | 16.8 / DD 112.0 / Cal 0.150 / U 41.0 | 3.8 / DD 97.1 / Cal 0.040 / U 41.4 | 1.5 / DD 309.7 / Cal 0.005 / U 141.3 | -1.8 / DD 145.5 / Cal -0.012 / U 74.6 |
| shipped layer, uniform lot scale 0.95 | 15.9 / DD 81.4 / Cal 0.195 / U 33.7 | 12.6 / DD 42.1 / Cal 0.298 / U 19.2 | 18.8 / DD 81.4 / Cal 0.231 / U 34.7 | 18.0 / DD 108.6 / Cal 0.166 / U 39.9 | 8.0 / DD 75.8 / Cal 0.106 / U 28.6 | 2.2 / DD 276.6 / Cal 0.008 / U 114.0 | -3.6 / DD 158.9 / Cal -0.023 / U 104.6 |
| none layer, uniform lot scale 1.0 | 15.6 / DD 95.1 / Cal 0.165 / U 36.5 | 7.4 / DD 54.0 / Cal 0.137 / U 27.3 | 19.6 / DD 72.3 / Cal 0.271 / U 33.9 | 19.1 / DD 118.3 / Cal 0.162 / U 39.2 | 5.4 / DD 95.1 / Cal 0.057 / U 39.1 | 2.2 / DD 329.1 / Cal 0.007 / U 140.8 | -1.6 / DD 144.8 / Cal -0.011 / U 71.8 |
