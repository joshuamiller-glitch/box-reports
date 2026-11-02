# DS3 ZONES LAYER vs SIZE - is the shipped HALF layer better than random halving at EQUAL RISK? (BASE-4, 2026-11-02T07:21Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Method: placebo layer = the shipped 7-line HALF mask (D20, half lots) replaced by a random half-lot mask with the same number of LIVE rows (A = same count per month, 100 draws; B = same count per month x book x session, 50 draws); OTE-62 B73, TH-L2 loss, profit lines, locks, sizer unchanged. Every placebo (and the references) has its WHOLE lot table scaled (engine lscale, integer-lot rounding) until the worst-20-weeks sum over ALL history equals the shipped layer's at scale 1 in the same frame (stop at |gap| <= 2.5% (<=5 engine runs); the residual gap is corrected linearly in mean, maxDD and ulcer: x target/achieved). Metrics per window: weekly mean ($k/wk), maxDD ($k, weekly cumulative), Calmar (mean/maxDD), ulcer (RMS of the weekly drawdown path, $k). RANK = share of placebo draws that are at least as GOOD as the shipped layer (higher mean / lower maxDD / higher Calmar / lower ulcer); small rank = the shipped layer beats random halving; ~0.5 = indistinguishable. Frames: lock none = per-book locks only (headline), 12R = + combined stack lock. Post-hoc.


## ANSWER (one paragraph; lock none = headline)
**In the recent windows the shipped HALF layer is NOT better than random halving at equal risk; it is better only in PRE (and on MID drawdown), and it is clearly better than having no layer.** Lock none, 100 same-count-per-month random half-lot layers (and 50 stratified by month x book x session), each scaled in the integer-lot engine to the shipped layer's worst-20: in F9 / L6M / HOLD the shipped layer's equal-risk mean ranks 0.48 / 0.40 / 0.58 (A) and 0.42 / 0.30 / 0.50 (B), its maxDD 0.41 / 0.41 / 0.39 and Calmar 0.43 / 0.38 / 0.42 (rank ~0.5 = indistinguishable; shipped F9 mean 22.5k vs placebo median 22.3k, maxDD 132.6k vs 135.5k). Where it does beat random halving is PRE (mean 10.0k vs 7.8k, maxDD 178k vs 212k, Calmar 0.056 vs 0.036: ranks 0.06 / 0.10 / 0.05 in A, 0.06 / 0.04 / 0.04 in B) and MID drawdown (rank 0.02-0.10); in X' it is no better (ranks 0.59-0.81 worse). With the combined 12R lock the picture is different: F9 maxDD rank 0.13 and Calmar 0.21 (better than random), L3M better (0.12-0.24), but HOLD (0.74-0.79) and X' (0.74-1.00) are worse than random halving, PRE indistinguishable (0.44-0.53). Versus no layer scaled to the same worst-20 (scale 0.95, lock none): F9 mean 20.2k / maxDD 151.7k vs shipped 22.5k / 132.6k, PRE 5.2k / 318k vs 10.0k / 178k, so a layer of half-lot rows beats scaling every row down, but a RANDOM half-lot layer of the same size does about as well in F9-HOLD: what the layer buys in the recent year is the size effect of taking half lots on ~10-12% of signals (a convex haircut on big-exposure rows), not the information in the 8 lines; the line information shows only in PRE (and MID drawdown).

## LOCK NONE (headline)

### A: same count per month: 100 draws; equal-risk lot scale of the placebo layers: median 1.011 [0.939, 1.087] (shipped = 1.000); residual risk gap max 6.6%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 22.5 | 22.4 [20.5,26.2] | 0.48 | 132.6 | 135.6 [102.5,175.7] | 0.41 | 0.170 / 0.166 | 0.43 | 54.1 / 56.6 | 0.40 |
| L3M | 16.1 | 14.2 [10.4,17.3] | 0.13 | 49.9 | 49.9 [38.4,67.4] | 0.50 | 0.324 / 0.289 | 0.35 | 27.1 / 26.3 | 0.55 |
| L6M | 26.9 | 26.3 [23.8,29.5] | 0.40 | 132.6 | 135.6 [102.5,175.7] | 0.41 | 0.202 / 0.192 | 0.38 | 61.4 / 64.3 | 0.42 |
| HOLD | 23.9 | 24.1 [21.5,28.0] | 0.58 | 132.6 | 136.4 [113.3,175.7] | 0.39 | 0.180 / 0.174 | 0.42 | 59.4 / 56.2 | 0.69 |
| MID | 10.9 | 11.9 [8.0,18.2] | 0.66 | 62.6 | 77.7 [60.3,94.0] | 0.10 | 0.174 / 0.154 | 0.39 | 25.7 / 28.3 | 0.21 |
| PRE | 10.0 | 7.7 [5.4,10.0] | 0.06 | 178.4 | 212.9 [168.8,293.1] | 0.10 | 0.056 / 0.036 | 0.05 | 81.3 / 96.5 | 0.12 |
| X' | -1.2 | -0.5 [-2.7,1.1] | 0.81 | 134.8 | 127.7 [91.4,176.6] | 0.59 | -0.009 / -0.004 | 0.80 | 66.6 / 56.4 | 0.66 |

### B: same count per month x book x session: 50 draws; equal-risk lot scale of the placebo layers: median 1.011 [0.940, 1.090] (shipped = 1.000); residual risk gap max 6.5%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 22.5 | 22.1 [19.8,24.8] | 0.42 | 132.6 | 138.0 [110.1,170.3] | 0.40 | 0.170 / 0.165 | 0.40 | 54.1 / 57.5 | 0.36 |
| L3M | 16.1 | 13.6 [10.3,16.8] | 0.10 | 49.9 | 48.0 [41.0,64.5] | 0.62 | 0.324 / 0.260 | 0.26 | 27.1 / 27.6 | 0.48 |
| L6M | 26.9 | 26.1 [23.6,29.0] | 0.30 | 132.6 | 138.0 [110.1,170.3] | 0.40 | 0.202 / 0.188 | 0.38 | 61.4 / 64.7 | 0.36 |
| HOLD | 23.9 | 23.9 [21.4,26.4] | 0.50 | 132.6 | 141.0 [112.1,170.3] | 0.32 | 0.180 / 0.169 | 0.40 | 59.4 / 57.3 | 0.56 |
| MID | 10.9 | 12.2 [7.4,15.8] | 0.66 | 62.6 | 77.2 [64.1,92.9] | 0.02 | 0.174 / 0.162 | 0.34 | 25.7 / 29.2 | 0.10 |
| PRE | 10.0 | 7.7 [5.7,9.9] | 0.06 | 178.4 | 220.5 [181.8,267.5] | 0.04 | 0.056 / 0.034 | 0.04 | 81.3 / 94.2 | 0.08 |
| X' | -1.2 | -1.1 [-2.7,0.7] | 0.70 | 134.8 | 120.6 [92.5,168.2] | 0.68 | -0.009 / -0.008 | 0.64 | 66.6 / 58.7 | 0.66 |

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

### A: same count per month: 100 draws; equal-risk lot scale of the placebo layers: median 0.992 [0.934, 1.055] (shipped = 1.000); residual risk gap max 5.2%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 17.6 | 17.3 [14.2,20.5] | 0.39 | 78.5 | 92.1 [68.4,108.7] | 0.13 | 0.224 / 0.187 | 0.21 | 32.2 / 33.3 | 0.38 |
| L3M | 15.8 | 11.6 [5.0,17.0] | 0.12 | 39.9 | 47.7 [33.3,62.3] | 0.24 | 0.395 / 0.240 | 0.14 | 18.9 / 22.3 | 0.26 |
| L6M | 22.4 | 20.4 [16.9,25.3] | 0.27 | 73.9 | 71.5 [49.9,100.6] | 0.56 | 0.303 / 0.289 | 0.45 | 32.4 / 31.6 | 0.55 |
| HOLD | 19.9 | 20.4 [17.0,23.5] | 0.56 | 119.2 | 96.9 [77.3,140.6] | 0.79 | 0.167 / 0.212 | 0.74 | 40.9 / 34.3 | 0.77 |
| MID | 5.3 | 7.4 [2.4,12.3] | 0.74 | 78.5 | 89.3 [62.9,107.8] | 0.21 | 0.068 / 0.086 | 0.65 | 29.1 / 33.6 | 0.17 |
| PRE | 4.0 | 3.8 [1.7,6.6] | 0.44 | 252.4 | 248.5 [178.0,327.2] | 0.53 | 0.016 / 0.015 | 0.45 | 99.9 / 100.9 | 0.49 |
| X' | -3.9 | -2.0 [-4.4,-0.1] | 0.92 | 173.7 | 137.2 [74.1,214.9] | 0.74 | -0.023 / -0.015 | 1.00 | 114.4 / 75.6 | 0.90 |

### B: same count per month x book x session: 50 draws; equal-risk lot scale of the placebo layers: median 0.990 [0.929, 1.058] (shipped = 1.000); residual risk gap max 6.9%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 17.6 | 16.9 [14.1,19.9] | 0.42 | 78.5 | 91.8 [78.2,101.6] | 0.06 | 0.224 / 0.186 | 0.12 | 32.2 / 34.4 | 0.28 |
| L3M | 15.8 | 12.4 [8.9,15.1] | 0.04 | 39.9 | 44.5 [36.2,58.0] | 0.24 | 0.395 / 0.259 | 0.04 | 18.9 / 21.4 | 0.20 |
| L6M | 22.4 | 20.6 [17.1,24.8] | 0.32 | 73.9 | 72.8 [52.1,95.1] | 0.56 | 0.303 / 0.280 | 0.40 | 32.4 / 32.7 | 0.48 |
| HOLD | 19.9 | 20.1 [16.7,22.7] | 0.54 | 119.2 | 106.0 [81.3,135.2] | 0.78 | 0.167 / 0.187 | 0.76 | 40.9 / 36.5 | 0.82 |
| MID | 5.3 | 6.5 [2.9,11.2] | 0.70 | 78.5 | 90.5 [64.7,101.4] | 0.12 | 0.068 / 0.075 | 0.54 | 29.1 / 34.7 | 0.10 |
| PRE | 4.0 | 4.2 [2.3,6.7] | 0.56 | 252.4 | 255.9 [175.7,340.3] | 0.42 | 0.016 / 0.016 | 0.54 | 99.9 / 103.6 | 0.44 |
| X' | -3.9 | -3.0 [-5.3,-1.0] | 0.72 | 173.7 | 169.7 [98.3,254.8] | 0.54 | -0.023 / -0.018 | 1.00 | 114.4 / 97.6 | 0.66 |

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


# ATTRIBUTION OF THE SHIPPED LAYER'S PRE EDGE (lock none, equal risk; BASE-4, 2026-11-02T07:53Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Equal risk = lot table scaled to the shipped layer's worst-20 (all history), residual gap corrected linearly. EDGE of a layer = its metric minus the median of random half-lot layers of the SAME live-row count per month (equal risk); contribution of a line = shipped edge minus the edge of the layer without that line (positive = the line carries edge). Post-hoc.

## (1) Leave-one-line-out (the 8 shipped lines), shipped edge for reference: PRE: mean +2.3k, maxDD +34k better; F9: mean +0.2k, maxDD +3k better; L6M: mean +0.5k, maxDD +3k better
| line removed | live rows halved | scale c / gap | PRE | F9 | L6M |
|---|---|---|---|---|---|
| kijun1h | 3393 | 1.000/1.6% | mean 9.9 (edge +3.1, ranks 0.05/0.05); maxDD 167 (edge -46); line carries mean -0.8 / maxDD -12 | mean 22.6 (edge -0.2, ranks 0.55/0.25); maxDD 132 (edge -13); line carries mean +0.4 / maxDD -10 | mean 26.6 (edge +0.3, ranks 0.40/0.25); maxDD 132 (edge -13); line carries mean +0.2 / maxDD -10 |
| PDmid | 3687 | 1.063/2.5% | mean 9.7 (edge +3.3, ranks 0.00/0.15); maxDD 193 (edge -30); line carries mean -1.0 / maxDD +4 | mean 23.9 (edge +0.6, ranks 0.25/0.65); maxDD 143 (edge +11); line carries mean -0.4 / maxDD +14 | mean 27.9 (edge +0.7, ranks 0.20/0.65); maxDD 143 (edge +11); line carries mean -0.2 / maxDD +14 |
| CRT4h | 3390 | 1.093/0.9% | mean 9.6 (edge +2.7, ranks 0.05/0.20); maxDD 193 (edge -34); line carries mean -0.5 / maxDD +1 | mean 24.9 (edge +2.5, ranks 0.10/0.75); maxDD 152 (edge +20); line carries mean -2.4 / maxDD +23 | mean 28.3 (edge +2.3, ranks 0.15/0.75); maxDD 152 (edge +20); line carries mean -1.8 / maxDD +23 |
| KCup4h | 3565 | 1.029/1.1% | mean 10.0 (edge +2.5, ranks 0.00/0.05); maxDD 179 (edge -42); line carries mean -0.2 / maxDD -7 | mean 22.6 (edge -0.3, ranks 0.65/0.40); maxDD 134 (edge -11); line carries mean +0.5 / maxDD -8 | mean 25.9 (edge -1.0, ranks 0.60/0.40); maxDD 134 (edge -11); line carries mean +1.5 / maxDD -8 |
| camH3 | 3183 | 1.010/2.9% | mean 9.9 (edge +2.1, ranks 0.00/0.00); maxDD 175 (edge -39); line carries mean +0.2 / maxDD -5 | mean 22.8 (edge +0.0, ranks 0.45/0.20); maxDD 128 (edge -11); line carries mean +0.1 / maxDD -8 | mean 26.3 (edge -0.4, ranks 0.55/0.20); maxDD 128 (edge -11); line carries mean +0.9 / maxDD -8 |
| OTE705 | 3300 | 1.038/2.5% | mean 9.6 (edge +2.1, ranks 0.10/0.00); maxDD 178 (edge -53); line carries mean +0.2 / maxDD -19 | mean 23.0 (edge +0.3, ranks 0.40/0.30); maxDD 135 (edge -7); line carries mean -0.1 / maxDD -4 | mean 26.6 (edge +0.2, ranks 0.45/0.30); maxDD 135 (edge -7); line carries mean +0.3 / maxDD -4 |
| OTE79 | 3246 | 1.040/1.5% | mean 9.5 (edge +2.0, ranks 0.00/0.30); maxDD 206 (edge -15); line carries mean +0.3 / maxDD +19 | mean 23.4 (edge +0.7, ranks 0.35/0.50); maxDD 141 (edge +2); line carries mean -0.5 / maxDD +5 | mean 26.9 (edge +0.6, ranks 0.35/0.50); maxDD 141 (edge +2); line carries mean -0.1 / maxDD +5 |
| OTE62 B73 | 3824 | 1.030/4.3% | mean 9.0 (edge +3.0, ranks 0.00/0.05); maxDD 183 (edge -61); line carries mean -0.7 / maxDD -26 | mean 21.3 (edge +0.3, ranks 0.40/0.30); maxDD 130 (edge -9); line carries mean -0.2 / maxDD -6 | mean 24.7 (edge +0.2, ranks 0.45/0.30); maxDD 130 (edge -9); line carries mean +0.3 / maxDD -6 |

"ranks a/b" = share of the 20 matched-count random layers at least as good on mean / maxDD (small = the layer without the line still beats random). "line carries" = shipped edge minus the without-line edge in $k/wk (mean, positive = the line adds mean) and maxDD $k reduction attributable (positive = the line adds protection).

## (3) PRE split in thirds (shipped vs the 100 same-count equal-risk random layers; cumulative restarts in each third)
| segment | mean ship / placebo med | rank mean | maxDD ship / med | rank maxDD | Calmar ship / med | rank Calmar |
|---|---|---|---|---|---|---|
| third 1: ISO 202405..202429 (25 wk) | 8.4 / 5.7 | 0.06 | 116 / 100 | 0.84 | 0.072 / 0.059 | 0.28 |
| third 2: ISO 202430..202502 (25 wk) | 12.0 / 9.3 | 0.09 | 161 / 179 | 0.28 | 0.074 / 0.050 | 0.15 |
| third 3: ISO 202503..202527 (25 wk) | 9.6 / 7.5 | 0.13 | 178 / 203 | 0.28 | 0.054 / 0.037 | 0.19 |


## (2a) PRE edge by book and session (40 equal-risk random layers with cubes; own-series PRE mean $k/wk shipped / placebo median, rank = share of placebos at least as good; own maxDD $k)
| unit | PRE mean ship / plc | rank mean | PRE maxDD ship / plc | rank maxDD |
|---|---|---|---|---|
| book K7 | +1.5 / +1.4 | 0.42 | 42 / 44 | 0.47 |
| book P7 | +6.9 / +4.8 | 0.00 | 152 / 186 | 0.05 |
| book U7 | +0.4 / +0.4 | 0.42 | 62 / 62 | 0.50 |
| book H7 | -0.1 / -0.1 | 0.47 | 61 / 65 | 0.33 |
| book M7 | -0.1 / -0.2 | 0.23 | 78 / 80 | 0.30 |
| book A6 | +1.3 / +1.4 | 0.57 | 17 / 13 | 0.93 |
| session asia | +7.7 / +5.9 | 0.00 | 79 / 86 | 0.20 |
| session london | -5.2 / -4.9 | 0.72 | 448 / 431 | 0.70 |
| session nyam | +7.2 / +6.6 | 0.15 | 69 / 67 | 0.62 |
| session nypm | +0.2 / +0.2 | 0.45 | 33 / 39 | 0.17 |


## (2b) The PRE episode ISO 2025-W05..W16 (shipped maxDD 178k, London carries -220k): sum of PRE P&L over those weeks by book / session, $k (shipped vs equal-risk random layers; rank = share of placebos at least as good)
Total episode P&L: shipped -115k vs placebo median -148k [-203,-91], rank 0.10.
| unit | shipped | placebo median [5,95] | rank |
|---|---|---|---|
| book K7 | +6 | -3 [-23,+13] | 0.23 |
| book P7 | +7 | -8 [-56,+50] | 0.33 |
| book U7 | -33 | -37 [-46,-30] | 0.30 |
| book H7 | -36 | -37 [-48,-28] | 0.45 |
| book M7 | -66 | -69 [-76,-62] | 0.28 |
| book A6 | +7 | +7 [+2,+11] | 0.45 |
| session asia | +106 | +60 [+27,+93] | 0.00 |
| session london | -204 | -211 [-232,-190] | 0.28 |
| session pre | +0 | +0 [+0,+0] | 1.00 |
| session nyam | -18 | +17 [-29,+41] | 0.85 |
| session nypm | +1 | -4 [-16,+8] | 0.15 |
| session close | +0 | +0 [+0,+0] | 1.00 |


## (2c) PRE edge by day vol tercile (day_regime vol_tag_today): PRE mean $k/wk contributed by days of each tag, shipped vs equal-risk random layers
| tag | days | shipped | placebo median | rank |
|---|---|---|---|---|
| vol tag 0.0 | 130 | -2.2 | -1.9 | 0.75 |
| vol tag 1.0 | 96 | -3.8 | -3.7 | 0.55 |
| vol tag 2.0 | 138 | +15.9 | +13.3 | 0.00 |
