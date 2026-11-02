# DS3 ZONES LAYER vs SIZE - is the shipped HALF layer better than random halving at EQUAL RISK? (BASE-4, 2026-11-02T09:52Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Method: placebo layer = the shipped 7-line HALF mask (D20, half lots) replaced by a random half-lot mask with the same number of LIVE rows (A = same count per month, 100 draws; B = same count per month x book x session, 50 draws); OTE-62 B73, TH-L2 loss, profit lines, locks, sizer unchanged. Every placebo (and the references) has its WHOLE lot table scaled (engine lscale, integer-lot rounding) until the worst-20-weeks sum over ALL history equals the shipped layer's at scale 1 in the same frame (stop at |gap| <= 2.5% (<=5 engine runs); the residual gap is corrected linearly in mean, maxDD and ulcer: x target/achieved). Metrics per window: weekly mean ($k/wk), maxDD ($k, weekly cumulative), Calmar (mean/maxDD), ulcer (RMS of the weekly drawdown path, $k). RANK = share of placebo draws that are at least as GOOD as the shipped layer (higher mean / lower maxDD / higher Calmar / lower ulcer); small rank = the shipped layer beats random halving; ~0.5 = indistinguishable. Frames: lock none = per-book locks only (headline), 12R = + combined stack lock. Post-hoc.


## ANSWER ON V13Y (add-fill ordering fixed; lock none = headline; supersedes the V13X conclusions in DS3_ZONES_LAYER_VS_SIZE.md)
**With the ordering fix the shipped HALF layer IS better than random halving at equal risk in PRE (strongly) and leans better in the recent windows, but the recent-window ranks are suggestive, not significant.** Lock none, 100 same-count-per-month random half-lot layers (+50 stratified), equal risk: PRE mean 12.1k vs placebo median 7.8k (rank 0.02), maxDD 129.7k vs 171.2k (rank 0.01), Calmar 0.093 vs 0.045 (rank 0.00); F9 / L6M / HOLD mean ranks 0.21 / 0.17 / 0.29, maxDD ranks 0.17 / 0.17 / 0.20, Calmar ranks 0.11 / 0.10 / 0.16 (shipped F9 mean 25.6k vs 23.8k, maxDD 96.2k vs 114.2k); MID maxDD rank 0.17; X' not better (0.50-0.80). With the 12R lock: F9 maxDD rank 0.01 but the mean rank 0.71, HOLD/PRE/X' not better. Attribution (lock none): the PRE edge is spread over the lines (every one of CRT4h, KCup4h, camH3, OTE705, OTE79 and OTE62 B73 carries +18..+41k of PRE maxDD protection when removed-vs-kept; no single line removal destroys it), it appears in all three PRE thirds (mean ranks 0.03 / 0.04 / 0.02), lives in book P7 (rank 0.00) and sessions Asia (0.00) and NY-AM (0.03), and is present in the middle vol tag (tag 1: F9 / L6M / HOLD / PRE ranks 0.00) -- in V13Y it is NOT confined to PRE (V13X conclusion changed). Multiplicity: 42 active book x session x vol-tag slices in PRE, 9 have rank <= 0.05 vs 2.1 expected for a random layer (90th percentile 4, max 6; share of random layers with >= 9: 0.00). Conclusion: on V13Y the lines carry information beyond the size effect (PRE clear, F9-HOLD at the 0.1-0.3 level); the size effect (halving ~10% of rows) still explains most of the recent-year gain.

## LOCK NONE (headline)

### A: same count per month: 100 draws; equal-risk lot scale of the placebo layers: median 0.975 [0.908, 1.075] (shipped = 1.000); residual risk gap max 5.2%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 25.6 | 23.8 [21.0,28.6] | 0.21 | 96.2 | 114.2 [84.5,149.1] | 0.17 | 0.266 / 0.211 | 0.11 | 38.7 / 42.8 | 0.23 |
| L3M | 19.7 | 17.0 [14.2,21.2] | 0.11 | 31.1 | 35.3 [26.4,43.1] | 0.20 | 0.635 / 0.486 | 0.15 | 15.0 / 15.1 | 0.49 |
| L6M | 28.8 | 26.3 [23.5,30.8] | 0.17 | 96.2 | 114.2 [84.5,149.1] | 0.17 | 0.299 / 0.235 | 0.10 | 44.5 / 49.3 | 0.26 |
| HOLD | 24.6 | 23.6 [21.1,28.3] | 0.29 | 103.0 | 114.4 [94.6,149.1] | 0.20 | 0.239 / 0.208 | 0.16 | 43.5 / 44.0 | 0.42 |
| MID | 16.4 | 16.1 [12.3,21.0] | 0.43 | 30.2 | 42.0 [26.6,57.3] | 0.17 | 0.543 / 0.382 | 0.18 | 15.2 / 17.0 | 0.35 |
| PRE | 12.1 | 7.8 [6.4,11.2] | 0.02 | 129.7 | 171.2 [138.5,218.9] | 0.01 | 0.093 / 0.045 | 0.00 | 60.9 / 78.0 | 0.03 |
| X' | 1.6 | 2.4 [0.6,3.7] | 0.80 | 69.7 | 70.1 [49.2,111.8] | 0.50 | 0.024 / 0.030 | 0.73 | 28.4 / 29.4 | 0.44 |

### B: same count per month x book x session: 50 draws; equal-risk lot scale of the placebo layers: median 0.961 [0.908, 1.047] (shipped = 1.000); residual risk gap max 3.7%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 25.6 | 22.9 [21.0,26.4] | 0.14 | 96.2 | 116.6 [73.5,148.3] | 0.24 | 0.266 / 0.200 | 0.16 | 38.7 / 45.3 | 0.30 |
| L3M | 19.7 | 16.2 [13.2,19.7] | 0.06 | 31.1 | 35.3 [24.8,43.9] | 0.20 | 0.635 / 0.464 | 0.10 | 15.0 / 14.5 | 0.56 |
| L6M | 28.8 | 25.8 [22.8,29.4] | 0.16 | 96.2 | 116.6 [73.5,148.3] | 0.24 | 0.299 / 0.219 | 0.14 | 44.5 / 51.8 | 0.30 |
| HOLD | 24.6 | 23.0 [20.9,26.1] | 0.24 | 103.0 | 117.6 [87.7,148.3] | 0.20 | 0.239 / 0.199 | 0.20 | 43.5 / 45.4 | 0.34 |
| MID | 16.4 | 16.0 [12.2,19.1] | 0.40 | 30.2 | 40.4 [25.5,55.2] | 0.16 | 0.543 / 0.396 | 0.14 | 15.2 / 16.4 | 0.28 |
| PRE | 12.1 | 7.8 [6.8,11.2] | 0.00 | 129.7 | 177.8 [151.4,212.1] | 0.00 | 0.093 / 0.044 | 0.00 | 60.9 / 79.1 | 0.02 |
| X' | 1.6 | 2.0 [0.4,3.3] | 0.72 | 69.7 | 67.4 [50.2,91.5] | 0.54 | 0.024 / 0.032 | 0.64 | 28.4 / 27.2 | 0.52 |

### References (mean $k/wk / maxDD $k / Calmar / ulcer $k)
| layer | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| shipped layer, scale 1.00 | 25.6 / DD 96.2 / Cal 0.266 / U 38.7 | 19.7 / DD 31.1 / Cal 0.635 / U 15.0 | 28.8 / DD 96.2 / Cal 0.299 / U 44.5 | 24.6 / DD 103.0 / Cal 0.239 / U 43.5 | 16.4 / DD 30.2 / Cal 0.543 / U 15.2 | 12.1 / DD 129.7 / Cal 0.093 / U 60.9 | 1.6 / DD 69.7 / Cal 0.024 / U 28.4 |
| no layer, scale 0.901 (equal worst-20, gap 2.8%) | 23.7 / DD 112.9 / Cal 0.210 / U 40.9 | 18.0 / DD 37.9 / Cal 0.476 / U 13.5 | 25.8 / DD 112.9 / Cal 0.229 / U 47.3 | 22.6 / DD 112.9 / Cal 0.200 / U 42.9 | 16.8 / DD 37.1 / Cal 0.453 / U 14.5 | 7.4 / DD 170.5 / Cal 0.043 / U 82.8 | 1.8 / DD 69.0 / Cal 0.027 / U 28.4 |
| none layer, uniform lot scale 0.8 | 21.2 / DD 89.7 / Cal 0.236 / U 32.7 | 16.6 / DD 33.9 / Cal 0.491 / U 12.1 | 23.6 / DD 89.7 / Cal 0.263 / U 37.3 | 20.4 / DD 95.0 / Cal 0.214 / U 36.8 | 14.0 / DD 35.4 / Cal 0.395 / U 14.5 | 7.7 / DD 123.8 / Cal 0.062 / U 57.0 | 1.9 / DD 63.3 / Cal 0.029 / U 23.8 |
| shipped layer, uniform lot scale 0.8 | 19.8 / DD 79.3 / Cal 0.249 / U 30.0 | 14.8 / DD 31.5 / Cal 0.471 / U 13.7 | 21.5 / DD 79.3 / Cal 0.271 / U 34.5 | 18.9 / DD 92.1 / Cal 0.205 / U 36.7 | 14.3 / DD 27.0 / Cal 0.529 / U 12.0 | 8.6 / DD 95.5 / Cal 0.091 / U 45.4 | 1.3 / DD 61.5 / Cal 0.021 / U 24.3 |
| none layer, uniform lot scale 0.9 | 23.0 / DD 109.7 / Cal 0.210 / U 39.8 | 17.5 / DD 36.8 / Cal 0.476 / U 13.2 | 25.1 / DD 109.7 / Cal 0.229 / U 46.0 | 22.0 / DD 109.7 / Cal 0.201 / U 41.7 | 16.4 / DD 35.4 / Cal 0.464 / U 14.0 | 7.2 / DD 165.1 / Cal 0.044 / U 80.1 | 1.8 / DD 67.0 / Cal 0.027 / U 27.6 |
| shipped layer, uniform lot scale 0.9 | 21.2 / DD 91.3 / Cal 0.232 / U 34.3 | 15.5 / DD 34.7 / Cal 0.446 / U 15.1 | 23.2 / DD 91.3 / Cal 0.254 / U 39.3 | 20.2 / DD 101.2 / Cal 0.200 / U 41.3 | 15.0 / DD 32.2 / Cal 0.466 / U 14.5 | 8.0 / DD 169.1 / Cal 0.047 / U 65.8 | 1.5 / DD 64.4 / Cal 0.023 / U 26.8 |
| none layer, uniform lot scale 0.95 | 24.6 / DD 123.5 / Cal 0.199 / U 46.6 | 18.7 / DD 34.5 / Cal 0.543 / U 12.6 | 27.2 / DD 123.5 / Cal 0.220 / U 53.9 | 24.0 / DD 123.5 / Cal 0.195 / U 47.3 | 16.5 / DD 38.1 / Cal 0.434 / U 15.8 | 7.5 / DD 214.2 / Cal 0.035 / U 101.0 | 2.1 / DD 74.5 / Cal 0.028 / U 30.9 |
| shipped layer, uniform lot scale 0.95 | 22.9 / DD 99.4 / Cal 0.230 / U 38.5 | 16.4 / DD 33.3 / Cal 0.491 / U 15.3 | 25.0 / DD 99.4 / Cal 0.251 / U 44.5 | 22.3 / DD 99.4 / Cal 0.224 / U 44.5 | 16.4 / DD 30.1 / Cal 0.544 / U 13.8 | 8.7 / DD 167.1 / Cal 0.052 / U 72.9 | 0.8 / DD 70.8 / Cal 0.012 / U 30.3 |
| none layer, uniform lot scale 1.0 | 27.4 / DD 127.6 / Cal 0.215 / U 49.5 | 22.1 / DD 33.9 / Cal 0.652 / U 12.2 | 30.7 / DD 127.6 / Cal 0.241 / U 57.2 | 26.1 / DD 127.6 / Cal 0.205 / U 50.9 | 17.7 / DD 43.6 / Cal 0.406 / U 17.7 | 10.8 / DD 168.4 / Cal 0.064 / U 76.0 | 2.9 / DD 79.8 / Cal 0.036 / U 29.9 |

## 12R combined lock

### A: same count per month: 100 draws; equal-risk lot scale of the placebo layers: median 1.025 [0.970, 1.111] (shipped = 1.000); residual risk gap max 5.5%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 17.2 | 18.6 [15.2,22.2] | 0.71 | 52.8 | 80.7 [60.0,104.1] | 0.01 | 0.325 / 0.227 | 0.07 | 26.0 / 30.8 | 0.15 |
| L3M | 13.8 | 11.7 [8.8,18.7] | 0.31 | 26.5 | 37.2 [24.9,46.6] | 0.08 | 0.519 / 0.313 | 0.15 | 13.6 / 17.2 | 0.18 |
| L6M | 21.2 | 22.2 [18.1,26.2] | 0.66 | 52.8 | 59.8 [50.0,92.4] | 0.16 | 0.402 / 0.367 | 0.35 | 26.3 / 27.2 | 0.44 |
| HOLD | 16.4 | 18.9 [15.4,21.9] | 0.88 | 90.4 | 112.2 [80.8,151.1] | 0.21 | 0.182 / 0.162 | 0.44 | 34.3 / 39.5 | 0.24 |
| MID | 6.7 | 8.3 [3.8,13.5] | 0.72 | 52.3 | 75.9 [58.8,100.0] | 0.01 | 0.127 / 0.111 | 0.35 | 23.3 / 32.2 | 0.03 |
| PRE | 5.9 | 6.0 [3.6,7.8] | 0.60 | 282.2 | 236.5 [171.2,323.6] | 0.80 | 0.021 / 0.026 | 0.70 | 120.4 / 90.6 | 0.85 |
| X' | -1.1 | 0.3 [-2.3,2.8] | 0.80 | 131.5 | 105.6 [55.7,178.8] | 0.79 | -0.008 / 0.002 | 0.77 | 69.3 / 51.5 | 0.77 |

### B: same count per month x book x session: 50 draws; equal-risk lot scale of the placebo layers: median 1.020 [0.950, 1.116] (shipped = 1.000); residual risk gap max 4.9%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 17.2 | 17.9 [14.2,21.4] | 0.60 | 52.8 | 80.3 [64.0,94.2] | 0.00 | 0.325 / 0.229 | 0.00 | 26.0 / 31.1 | 0.08 |
| L3M | 13.8 | 11.6 [7.5,17.3] | 0.22 | 26.5 | 35.8 [24.4,43.7] | 0.12 | 0.519 / 0.322 | 0.10 | 13.6 / 17.2 | 0.12 |
| L6M | 21.2 | 21.2 [17.3,26.1] | 0.48 | 52.8 | 58.8 [52.2,92.7] | 0.06 | 0.402 / 0.353 | 0.26 | 26.3 / 28.7 | 0.30 |
| HOLD | 16.4 | 18.1 [14.7,21.6] | 0.82 | 90.4 | 114.1 [78.0,135.7] | 0.18 | 0.182 / 0.163 | 0.36 | 34.3 / 40.3 | 0.20 |
| MID | 6.7 | 8.1 [3.9,11.5] | 0.72 | 52.3 | 77.6 [63.2,90.8] | 0.00 | 0.127 / 0.104 | 0.32 | 23.3 / 32.7 | 0.02 |
| PRE | 5.9 | 6.3 [4.0,8.2] | 0.60 | 282.2 | 249.3 [181.3,322.9] | 0.80 | 0.021 / 0.025 | 0.72 | 120.4 / 95.2 | 0.86 |
| X' | -1.1 | -1.2 [-3.5,1.2] | 0.48 | 131.5 | 129.5 [61.2,213.8] | 0.50 | -0.008 / -0.008 | 0.52 | 69.3 / 71.5 | 0.50 |

### References (mean $k/wk / maxDD $k / Calmar / ulcer $k)
| layer | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| shipped layer, scale 1.00 | 17.2 / DD 52.8 / Cal 0.325 / U 26.0 | 13.8 / DD 26.5 / Cal 0.519 / U 13.6 | 21.2 / DD 52.8 / Cal 0.402 / U 26.3 | 16.4 / DD 90.4 / Cal 0.182 / U 34.3 | 6.7 / DD 52.3 / Cal 0.127 / U 23.3 | 5.9 / DD 282.2 / Cal 0.021 / U 120.4 | -1.1 / DD 131.5 / Cal -0.008 / U 69.3 |
| no layer, scale 0.950 (equal worst-20, gap 1.5%) | 15.9 / DD 76.7 / Cal 0.207 / U 30.2 | 10.9 / DD 35.4 / Cal 0.307 / U 15.7 | 19.4 / DD 59.6 / Cal 0.326 / U 26.6 | 16.3 / DD 124.7 / Cal 0.130 / U 43.6 | 6.5 / DD 76.7 / Cal 0.085 / U 34.9 | 4.1 / DD 277.7 / Cal 0.015 / U 122.7 | 1.3 / DD 68.6 / Cal 0.019 / U 31.3 |
| none layer, uniform lot scale 0.8 | 14.5 / DD 64.2 / Cal 0.226 / U 23.6 | 10.0 / DD 26.1 / Cal 0.383 / U 12.2 | 17.6 / DD 41.9 / Cal 0.420 / U 20.1 | 15.0 / DD 100.2 / Cal 0.150 / U 33.4 | 6.3 / DD 64.2 / Cal 0.098 / U 28.1 | 5.6 / DD 142.6 / Cal 0.039 / U 54.9 | 1.8 / DD 42.8 / Cal 0.042 / U 18.7 |
| shipped layer, uniform lot scale 0.8 | 13.4 / DD 42.0 / Cal 0.320 / U 21.0 | 9.3 / DD 26.6 / Cal 0.349 / U 11.2 | 16.2 / DD 42.0 / Cal 0.385 / U 21.7 | 13.0 / DD 74.3 / Cal 0.174 / U 29.7 | 6.2 / DD 39.3 / Cal 0.157 / U 17.9 | 4.2 / DD 136.8 / Cal 0.031 / U 57.4 | -0.6 / DD 91.4 / Cal -0.006 / U 48.4 |
| none layer, uniform lot scale 0.9 | 15.8 / DD 66.2 / Cal 0.238 / U 29.8 | 10.9 / DD 29.4 / Cal 0.371 / U 13.2 | 18.9 / DD 60.9 / Cal 0.310 / U 28.5 | 16.0 / DD 106.0 / Cal 0.151 / U 39.1 | 7.5 / DD 66.2 / Cal 0.113 / U 30.1 | 4.9 / DD 204.5 / Cal 0.024 / U 80.8 | 1.9 / DD 50.2 / Cal 0.039 / U 22.5 |
| shipped layer, uniform lot scale 0.9 | 14.7 / DD 58.1 / Cal 0.252 / U 26.5 | 10.8 / DD 23.0 / Cal 0.468 / U 11.8 | 17.5 / DD 58.1 / Cal 0.301 / U 28.6 | 15.0 / DD 76.1 / Cal 0.196 / U 32.9 | 7.1 / DD 45.7 / Cal 0.155 / U 18.6 | 3.7 / DD 251.3 / Cal 0.015 / U 99.6 | -0.6 / DD 100.5 / Cal -0.005 / U 53.4 |
| none layer, uniform lot scale 0.95 | 16.1 / DD 77.9 / Cal 0.207 / U 30.7 | 11.0 / DD 36.0 / Cal 0.307 / U 15.9 | 19.7 / DD 60.5 / Cal 0.326 / U 27.0 | 16.5 / DD 126.6 / Cal 0.130 / U 44.2 | 6.6 / DD 77.9 / Cal 0.085 / U 35.5 | 4.2 / DD 282.0 / Cal 0.015 / U 124.5 | 1.3 / DD 69.7 / Cal 0.019 / U 31.8 |
| shipped layer, uniform lot scale 0.95 | 15.9 / DD 60.1 / Cal 0.264 / U 26.9 | 11.1 / DD 28.1 / Cal 0.395 / U 13.7 | 19.3 / DD 60.1 / Cal 0.321 / U 27.9 | 16.2 / DD 88.0 / Cal 0.184 / U 36.4 | 6.8 / DD 47.9 / Cal 0.142 / U 22.1 | 3.7 / DD 283.0 / Cal 0.013 / U 126.4 | -1.5 / DD 132.9 / Cal -0.011 / U 76.4 |
| none layer, uniform lot scale 1.0 | 19.6 / DD 80.0 / Cal 0.245 / U 28.8 | 13.5 / DD 30.9 / Cal 0.438 / U 15.3 | 23.9 / DD 52.2 / Cal 0.459 / U 23.6 | 19.3 / DD 125.3 / Cal 0.154 / U 41.3 | 8.2 / DD 80.0 / Cal 0.103 / U 35.9 | 5.2 / DD 316.0 / Cal 0.016 / U 137.8 | 2.2 / DD 65.6 / Cal 0.034 / U 27.6 |


# ATTRIBUTION OF THE SHIPPED LAYER'S PRE EDGE (lock none, equal risk; BASE-4, 2026-11-02T10:07Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Equal risk = lot table scaled to the shipped layer's worst-20 (all history), residual gap corrected linearly. EDGE of a layer = its metric minus the median of random half-lot layers of the SAME live-row count per month (equal risk); contribution of a line = shipped edge minus the edge of the layer without that line (positive = the line carries edge). Post-hoc.

## (1) Leave-one-line-out (the 8 shipped lines), shipped edge for reference: PRE: mean +4.3k, maxDD +42k better; F9: mean +1.9k, maxDD +18k better; L6M: mean +2.4k, maxDD +18k better
| line removed | live rows halved | scale c / gap | PRE | F9 | L6M |
|---|---|---|---|---|---|
| kijun1h | 3393 | 1.000/1.7% | mean 11.7 (edge +4.1, ranks 0.00/0.10); maxDD 138 (edge -42); line carries mean +0.1 / maxDD -1 | mean 25.7 (edge +2.2, ranks 0.25/0.10); maxDD 95 (edge -27); line carries mean -0.4 / maxDD -9 | mean 28.5 (edge +1.8, ranks 0.15/0.10); maxDD 95 (edge -27); line carries mean +0.6 / maxDD -9 |
| PDmid | 3687 | 1.023/2.4% | mean 12.7 (edge +5.4, ranks 0.00/0.05); maxDD 131 (edge -52); line carries mean -1.1 / maxDD -10 | mean 27.4 (edge +3.8, ranks 0.00/0.40); maxDD 103 (edge -12); line carries mean -2.0 / maxDD +6 | mean 30.2 (edge +4.4, ranks 0.00/0.40); maxDD 103 (edge -12); line carries mean -2.0 / maxDD +6 |
| CRT4h | 3390 | 0.968/1.5% | mean 8.6 (edge +1.2, ranks 0.10/0.50); maxDD 183 (edge -0); line carries mean +3.1 / maxDD +41 | mean 23.6 (edge +0.4, ranks 0.40/0.00); maxDD 86 (edge -21); line carries mean +1.4 / maxDD -3 | mean 25.9 (edge +0.6, ranks 0.40/0.00); maxDD 86 (edge -21); line carries mean +1.8 / maxDD -3 |
| KCup4h | 3565 | 0.982/1.0% | mean 9.0 (edge +1.4, ranks 0.20/0.40); maxDD 165 (edge -8); line carries mean +2.9 / maxDD +33 | mean 23.0 (edge -0.3, ranks 0.60/0.20); maxDD 89 (edge -27); line carries mean +2.2 / maxDD -9 | mean 25.4 (edge -0.4, ranks 0.65/0.20); maxDD 89 (edge -27); line carries mean +2.8 / maxDD -9 |
| camH3 | 3183 | 0.980/0.3% | mean 8.7 (edge +0.9, ranks 0.30/0.50); maxDD 174 (edge -1); line carries mean +3.4 / maxDD +40 | mean 23.6 (edge -1.0, ranks 0.75/0.00); maxDD 84 (edge -30); line carries mean +2.9 / maxDD -12 | mean 25.8 (edge -1.7, ranks 0.75/0.00); maxDD 84 (edge -30); line carries mean +4.1 / maxDD -12 |
| OTE705 | 3300 | 0.928/0.4% | mean 8.6 (edge +1.0, ranks 0.35/0.35); maxDD 165 (edge -23); line carries mean +3.3 / maxDD +18 | mean 22.7 (edge -1.7, ranks 0.80/0.70); maxDD 127 (edge +15); line carries mean +3.6 / maxDD +33 | mean 24.8 (edge -2.4, ranks 0.85/0.70); maxDD 127 (edge +15); line carries mean +4.8 / maxDD +33 |
| OTE79 | 3246 | 0.957/1.8% | mean 8.5 (edge +0.8, ranks 0.30/0.35); maxDD 164 (edge -20); line carries mean +3.5 / maxDD +22 | mean 23.3 (edge +0.1, ranks 0.50/0.25); maxDD 113 (edge -6); line carries mean +1.8 / maxDD +12 | mean 25.2 (edge -0.5, ranks 0.55/0.25); maxDD 113 (edge -6); line carries mean +2.9 / maxDD +12 |
| OTE62 B73 | 3824 | 0.961/1.5% | mean 8.8 (edge +0.9, ranks 0.30/0.50); maxDD 167 (edge -3); line carries mean +3.4 / maxDD +39 | mean 23.8 (edge -1.4, ranks 0.85/0.50); maxDD 107 (edge +0); line carries mean +3.2 / maxDD +18 | mean 26.0 (edge -1.6, ranks 0.85/0.50); maxDD 107 (edge +0); line carries mean +4.0 / maxDD +18 |

"ranks a/b" = share of the 20 matched-count random layers at least as good on mean / maxDD (small = the layer without the line still beats random). "line carries" = shipped edge minus the without-line edge in $k/wk (mean, positive = the line adds mean) and maxDD $k reduction attributable (positive = the line adds protection).

## (3) PRE split in thirds (shipped vs the 100 same-count equal-risk random layers; cumulative restarts in each third)
| segment | mean ship / placebo med | rank mean | maxDD ship / med | rank maxDD | Calmar ship / med | rank Calmar |
|---|---|---|---|---|---|---|
| third 1: ISO 202405..202429 (25 wk) | 7.9 / 5.0 | 0.03 | 116 / 98 | 0.89 | 0.068 / 0.052 | 0.20 |
| third 2: ISO 202430..202502 (25 wk) | 13.7 / 9.3 | 0.04 | 130 / 154 | 0.09 | 0.105 / 0.059 | 0.04 |
| third 3: ISO 202503..202527 (25 wk) | 14.8 / 9.8 | 0.02 | 124 / 156 | 0.06 | 0.119 / 0.063 | 0.02 |


## (2a) PRE edge by book and session (40 equal-risk random layers with cubes; own-series PRE mean $k/wk shipped / placebo median, rank = share of placebos at least as good; own maxDD $k)
| unit | PRE mean ship / plc | rank mean | PRE maxDD ship / plc | rank maxDD |
|---|---|---|---|---|
| book K7 | +1.4 / +0.8 | 0.12 | 41 / 53 | 0.15 |
| book P7 | +8.5 / +5.5 | 0.00 | 126 / 154 | 0.05 |
| book U7 | +0.4 / +0.1 | 0.05 | 64 / 73 | 0.10 |
| book H7 | +0.3 / +0.3 | 0.47 | 52 / 48 | 0.78 |
| book M7 | +0.2 / +0.0 | 0.20 | 71 / 72 | 0.42 |
| book A6 | +1.3 / +1.0 | 0.28 | 17 / 7 | 1.00 |
| session asia | +8.1 / +5.4 | 0.00 | 63 / 66 | 0.35 |
| session london | -4.7 / -4.4 | 0.82 | 428 / 402 | 0.72 |
| session nyam | +8.6 / +6.7 | 0.03 | 68 / 60 | 0.68 |
| session nypm | +0.1 / -0.0 | 0.30 | 37 / 44 | 0.12 |


## (2b) The PRE episode ISO 2025-W05..W16 (shipped maxDD 178k, London carries -220k): sum of PRE P&L over those weeks by book / session, $k (shipped vs equal-risk random layers; rank = share of placebos at least as good)
Total episode P&L: shipped -40k vs placebo median -119k [-164,-61], rank 0.05.
| unit | shipped | placebo median [5,95] | rank |
|---|---|---|---|
| book K7 | -6 | -17 [-32,+3] | 0.20 |
| book P7 | +81 | +14 [-17,+75] | 0.05 |
| book U7 | -43 | -42 [-53,-35] | 0.55 |
| book H7 | -15 | -21 [-28,-11] | 0.23 |
| book M7 | -64 | -66 [-74,-58] | 0.40 |
| book A6 | +7 | +8 [+5,+10] | 0.75 |
| session asia | +120 | +54 [+8,+101] | 0.00 |
| session london | -187 | -192 [-215,-170] | 0.35 |
| session pre | +0 | +0 [+0,+0] | 1.00 |
| session nyam | +33 | +35 [+2,+61] | 0.55 |
| session nypm | -7 | -12 [-25,-2] | 0.20 |
| session close | +0 | +0 [+0,+0] | 1.00 |


## (2c) PRE edge by day vol tercile (day_regime vol_tag_today): PRE mean $k/wk contributed by days of each tag, shipped vs equal-risk random layers
| tag | days | shipped | placebo median | rank |
|---|---|---|---|---|
| vol tag 0.0 | 130 | -1.0 | -0.9 | 0.62 |
| vol tag 1.0 | 96 | -2.2 | -3.2 | 0.00 |
| vol tag 2.0 | 138 | +15.3 | +11.6 | 0.00 |


# CONSISTENCY AND MULTIPLICITY OF THE PRE EDGE (BASE-4, 2026-11-02T10:07Z; lock none, equal risk; 40 random half-lot layers with cubes)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Heat table: cell = shipped minus random-layer MEDIAN of the slice's mean contribution ($k/wk) and, in brackets, the rank = share of the random layers with a contribution at least as high (small = the shipped layer beats random halving in that slice; PRE column is where the slices were found; the other columns are out-of-selection checks).

## (1) Heat table: slice x window
| slice | F9 | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|
| book K7 | +0.3 (0.30) | +0.4 (0.35) | +0.2 (0.38) | +0.2 (0.47) | +0.6 (0.12) | -0.0 (0.53) |
| book P7 | +2.0 (0.12) | +2.6 (0.17) | +0.6 (0.28) | +0.5 (0.38) | +2.9 (0.00) | -1.2 (0.93) |
| book U7 | +0.0 (0.45) | -0.2 (0.70) | -0.1 (0.57) | +0.5 (0.17) | +0.3 (0.05) | -0.0 (0.55) |
| book H7 | +0.0 (0.47) | +0.1 (0.42) | +0.1 (0.38) | -0.1 (0.53) | +0.0 (0.47) | +0.2 (0.15) |
| book M7 | -0.5 (0.93) | -0.6 (0.95) | -0.4 (0.90) | -0.1 (0.55) | +0.1 (0.20) | +0.3 (0.12) |
| book A6 | -0.1 (0.70) | +0.1 (0.30) | +0.3 (0.17) | -0.4 (0.95) | +0.3 (0.28) | +0.3 (0.00) |
| sess asia | +1.1 (0.23) | +1.4 (0.20) | +0.8 (0.30) | +1.1 (0.20) | +2.6 (0.00) | +0.8 (0.07) |
| sess london | +0.7 (0.30) | +1.4 (0.20) | +0.1 (0.50) | -0.9 (0.72) | -0.3 (0.82) | -0.6 (0.93) |
| sess nyam | -0.0 (0.50) | +0.1 (0.35) | -0.1 (0.68) | -0.3 (0.62) | +2.0 (0.03) | -0.7 (0.82) |
| sess nypm | -0.2 (0.78) | -0.5 (0.97) | -0.2 (0.90) | +0.5 (0.03) | +0.1 (0.30) | -0.2 (0.93) |
| vol 0 | -1.0 (0.95) | -0.6 (0.82) | -1.4 (0.97) | -2.2 (0.93) | -0.1 (0.62) | -0.2 (0.62) |
| vol 1 | +2.3 (0.00) | +2.7 (0.00) | +1.7 (0.00) | +1.2 (0.05) | +1.0 (0.00) | -0.1 (0.57) |
| vol 2 | +0.4 (0.40) | -0.0 (0.50) | +0.5 (0.40) | +1.1 (0.28) | +3.6 (0.00) | -0.3 (0.75) |


## (2) Multiplicity: 42 active book x session x vol-tag slices in PRE (6 books x 4 sessions x 3 tags, empty cells dropped)
Shipped layer: 9 slices with rank <= 0.05 (better than random halving) and 3 with rank >= 0.95 (worse). NULL (each of the 40 random layers ranked against the other 39): slices with rank <= 0.05 per random layer: mean 2.1, median 2, 90th pct 4, max 6; rank >= 0.95: mean 2.1. Share of random layers with at least as many <=0.05 slices as the shipped layer: 0.00. (Resolution of a rank with 39-40 comparators is 0.025, so rank <= 0.05 means at most 2 random layers are as good.)
