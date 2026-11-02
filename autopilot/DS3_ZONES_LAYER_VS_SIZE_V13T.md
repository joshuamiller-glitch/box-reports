# DS3 ZONES LAYER vs SIZE - is the shipped HALF layer better than random halving at EQUAL RISK? (BASE-4, 2026-11-02T14:28Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Method: placebo layer = the shipped 7-line HALF mask (D20, half lots) replaced by a random half-lot mask with the same number of LIVE rows (A = same count per month, 100 draws; B = same count per month x book x session, 50 draws); OTE-62 B73, TH-L2 loss, profit lines, locks, sizer unchanged. Every placebo (and the references) has its WHOLE lot table scaled (engine lscale, integer-lot rounding) until the worst-20-weeks sum over ALL history equals the shipped layer's at scale 1 in the same frame (stop at |gap| <= 2.5% (<=5 engine runs); the residual gap is corrected linearly in mean, maxDD and ulcer: x target/achieved). Metrics per window: weekly mean ($k/wk), maxDD ($k, weekly cumulative), Calmar (mean/maxDD), ulcer (RMS of the weekly drawdown path, $k). RANK = share of placebo draws that are at least as GOOD as the shipped layer (higher mean / lower maxDD / higher Calmar / lower ulcer); small rank = the shipped layer beats random halving; ~0.5 = indistinguishable. Frames: lock none = per-book locks only (headline), 12R = + combined stack lock. Post-hoc.


## ANSWER ON V13T_LIVE (xcost 0.80, stopcost 2.45, lines empty, lock none = per-book locks; lock-12 frame = reference only)
**On the live-cost base the shipped HALF layer is indistinguishable from random halving at equal risk.** Lock none, 100 same-count random half-lot layers (+50 stratified), each scaled to the shipped worst-20: F9 / L6M / HOLD equal-risk mean ranks 0.27 / 0.25 / 0.52, maxDD ranks 0.59 / 0.59 / 0.56, Calmar ranks 0.53 / 0.51 / 0.55; MID maxDD 0.27; PRE mean rank 0.06 and Calmar 0.06 (maxDD 0.41); X' 0.47-0.85. The only slices where the layer beats random halving are book P7 in PRE (rank 0.00), vol tag 1 days (F9 / L6M / MID 0.00, HOLD 0.05) and a few session cells; multiplicity: 5 of 42 PRE book x session x vol-tag slices at rank <= 0.05 vs 2.1 expected (share of random layers with >= 5: 0.15) = inside chance. PRE thirds: mean edge only in the third (rank 0.05), maxDD in none. Shipped vs no layer (composite page): maxDD cut F9 / L6M / HOLD / PRE +7%, MID +25%, X' -16%, means within MDE. Net: on the true cost model the layer is a size effect (halving ~10% of rows), with no information edge that survives the multiplicity null; the V13Y edge (PRE and the recent windows) shrank on V13Z and is gone on V13T_LIVE. Episode carriers moved: F9 #1 is now ISO W28-W39 (depth 150.7k) carried by P7 -76k, K7 -64k, M7 -35k and sessions London -89k, Asia -32k (DS3_ZONES_EPISODES_V13T.md).

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


# ATTRIBUTION OF THE SHIPPED LAYER'S PRE EDGE (lock none, equal risk; BASE-4, 2026-11-02T14:44Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Equal risk = lot table scaled to the shipped layer's worst-20 (all history), residual gap corrected linearly. EDGE of a layer = its metric minus the median of random half-lot layers of the SAME live-row count per month (equal risk); contribution of a line = shipped edge minus the edge of the layer without that line (positive = the line carries edge). Post-hoc.

## (1) Leave-one-line-out (the 8 shipped lines), shipped edge for reference: PRE: mean +2.2k, maxDD +2k better; F9: mean +1.3k, maxDD -4k better; L6M: mean +1.4k, maxDD -4k better
| line removed | live rows halved | scale c / gap | PRE | F9 | L6M |
|---|---|---|---|---|---|
| kijun1h | 3393 | 1.031/2.2% | mean 16.7 (edge +1.0, ranks 0.00/0.75); maxDD 169 (edge +6); line carries mean +1.2 / maxDD +8 | mean 34.8 (edge +3.0, ranks 0.00/0.00); maxDD 102 (edge -42); line carries mean -1.7 / maxDD -47 | mean 38.5 (edge +4.2, ranks 0.10/0.00); maxDD 102 (edge -42); line carries mean -2.8 / maxDD -47 |
| PDmid | 3687 | 1.041/0.2% | mean 17.5 (edge +2.8, ranks 0.00/0.55); maxDD 166 (edge +5); line carries mean -0.6 / maxDD +6 | mean 34.5 (edge +1.5, ranks 0.15/0.35); maxDD 133 (edge -7); line carries mean -0.2 / maxDD -11 | mean 38.1 (edge +2.6, ranks 0.10/0.35); maxDD 133 (edge -7); line carries mean -1.2 / maxDD -11 |
| CRT4h | 3390 | 1.059/0.0% | mean 16.7 (edge +1.8, ranks 0.10/0.55); maxDD 168 (edge +1); line carries mean +0.4 / maxDD +2 | mean 33.9 (edge +2.6, ranks 0.15/0.50); maxDD 139 (edge +4); line carries mean -1.3 / maxDD -1 | mean 37.9 (edge +3.1, ranks 0.10/0.50); maxDD 139 (edge +4); line carries mean -1.7 / maxDD -1 |
| KCup4h | 3565 | 1.017/1.0% | mean 16.6 (edge +2.9, ranks 0.00/0.25); maxDD 169 (edge -4); line carries mean -0.7 / maxDD -2 | mean 33.7 (edge +1.9, ranks 0.15/0.35); maxDD 137 (edge -7); line carries mean -0.6 / maxDD -11 | mean 36.9 (edge +2.4, ranks 0.20/0.35); maxDD 137 (edge -7); line carries mean -1.0 / maxDD -11 |
| camH3 | 3183 | 0.988/3.6% | mean 14.5 (edge +0.5, ranks 0.35/0.55); maxDD 173 (edge +5); line carries mean +1.7 / maxDD +7 | mean 33.8 (edge +1.0, ranks 0.30/0.50); maxDD 134 (edge -3); line carries mean +0.3 / maxDD -8 | mean 36.3 (edge +0.9, ranks 0.35/0.50); maxDD 134 (edge -3); line carries mean +0.5 / maxDD -8 |
| OTE705 | 3300 | 1.002/0.4% | mean 17.2 (edge +1.8, ranks 0.05/0.20); maxDD 159 (edge -14); line carries mean +0.4 / maxDD -12 | mean 33.8 (edge +1.5, ranks 0.10/0.70); maxDD 155 (edge +8); line carries mean -0.2 / maxDD +4 | mean 36.8 (edge +1.3, ranks 0.05/0.70); maxDD 155 (edge +8); line carries mean +0.1 / maxDD +4 |
| OTE79 | 3246 | 1.002/1.6% | mean 17.1 (edge +2.6, ranks 0.10/0.10); maxDD 164 (edge -8); line carries mean -0.4 / maxDD -6 | mean 31.8 (edge -1.1, ranks 0.70/0.65); maxDD 151 (edge +7); line carries mean +2.4 / maxDD +3 | mean 34.1 (edge -1.6, ranks 0.75/0.65); maxDD 151 (edge +7); line carries mean +3.0 / maxDD +3 |
| OTE62 B73 | 3824 | 1.049/1.7% | mean 17.1 (edge +2.2, ranks 0.05/0.25); maxDD 165 (edge -4); line carries mean +0.0 / maxDD -3 | mean 34.3 (edge +1.0, ranks 0.40/0.35); maxDD 131 (edge -4); line carries mean +0.3 / maxDD -9 | mean 38.0 (edge +1.6, ranks 0.25/0.35); maxDD 131 (edge -4); line carries mean -0.2 / maxDD -9 |

"ranks a/b" = share of the 20 matched-count random layers at least as good on mean / maxDD (small = the layer without the line still beats random). "line carries" = shipped edge minus the without-line edge in $k/wk (mean, positive = the line adds mean) and maxDD $k reduction attributable (positive = the line adds protection).

## (3) PRE split in thirds (shipped vs the 100 same-count equal-risk random layers; cumulative restarts in each third)
| segment | mean ship / placebo med | rank mean | maxDD ship / med | rank maxDD | Calmar ship / med | rank Calmar |
|---|---|---|---|---|---|---|
| third 1: ISO 202405..202429 (25 wk) | 12.9 / 11.7 | 0.24 | 86 / 79 | 0.67 | 0.150 / 0.151 | 0.51 |
| third 2: ISO 202430..202502 (25 wk) | 22.8 / 20.8 | 0.22 | 166 / 157 | 0.73 | 0.137 / 0.135 | 0.46 |
| third 3: ISO 202503..202527 (25 wk) | 16.1 / 12.5 | 0.05 | 165 / 159 | 0.58 | 0.098 / 0.077 | 0.17 |


## (2a) PRE edge by book and session (40 equal-risk random layers with cubes; own-series PRE mean $k/wk shipped / placebo median, rank = share of placebos at least as good; own maxDD $k)
| unit | PRE mean ship / plc | rank mean | PRE maxDD ship / plc | rank maxDD |
|---|---|---|---|---|
| book K7 | +1.2 / +1.7 | 0.85 | 40 / 42 | 0.47 |
| book P7 | +12.7 / +10.0 | 0.00 | 110 / 114 | 0.38 |
| book U7 | +1.4 / +1.4 | 0.47 | 62 / 62 | 0.57 |
| book H7 | +0.7 / +0.9 | 0.68 | 64 / 66 | 0.38 |
| book M7 | +0.0 / +0.1 | 0.68 | 88 / 86 | 0.60 |
| book A6 | +1.3 / +1.4 | 0.78 | 18 / 14 | 0.90 |
| session asia | +11.2 / +9.9 | 0.03 | 64 / 66 | 0.42 |
| session london | -2.8 / -2.7 | 0.60 | 326 / 323 | 0.50 |
| session nyam | +8.9 / +8.0 | 0.12 | 57 / 61 | 0.30 |
| session nypm | -0.0 / +0.1 | 0.90 | 43 / 44 | 0.47 |


## (2b) The PRE episode ISO 2025-W05..W16 (shipped maxDD 178k, London carries -220k): sum of PRE P&L over those weeks by book / session, $k (shipped vs equal-risk random layers; rank = share of placebos at least as good)
Total episode P&L: shipped -1k vs placebo median -39k [-100,+18], rank 0.15.
| unit | shipped | placebo median [5,95] | rank |
|---|---|---|---|
| book K7 | -13 | -11 [-24,+1] | 0.60 |
| book P7 | +117 | +86 [+17,+158] | 0.20 |
| book U7 | -21 | -34 [-45,-24] | 0.00 |
| book H7 | -17 | -14 [-23,-4] | 0.72 |
| book M7 | -72 | -71 [-78,-66] | 0.62 |
| book A6 | +6 | +6 [+1,+11] | 0.42 |
| session asia | +180 | +149 [+114,+183] | 0.07 |
| session london | -201 | -206 [-233,-180] | 0.40 |
| session pre | +0 | +0 [+0,+0] | 1.00 |
| session nyam | +35 | +38 [+3,+71] | 0.53 |
| session nypm | -15 | -15 [-25,-8] | 0.53 |
| session close | +0 | +0 [+0,+0] | 1.00 |


## (2c) PRE edge by day vol tercile (day_regime vol_tag_today): PRE mean $k/wk contributed by days of each tag, shipped vs equal-risk random layers
| tag | days | shipped | placebo median | rank |
|---|---|---|---|---|
| vol tag 0.0 | 130 | -2.6 | -2.9 | 0.17 |
| vol tag 1.0 | 96 | -1.1 | -1.3 | 0.38 |
| vol tag 2.0 | 138 | +21.0 | +19.8 | 0.07 |


# CONSISTENCY AND MULTIPLICITY OF THE PRE EDGE (BASE-4, 2026-11-02T14:44Z; lock none, equal risk; 40 random half-lot layers with cubes)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Heat table: cell = shipped minus random-layer MEDIAN of the slice's mean contribution ($k/wk) and, in brackets, the rank = share of the random layers with a contribution at least as high (small = the shipped layer beats random halving in that slice; PRE column is where the slices were found; the other columns are out-of-selection checks).

## (1) Heat table: slice x window
| slice | F9 | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|
| book K7 | +0.3 (0.33) | +0.2 (0.30) | -0.0 (0.57) | +0.2 (0.33) | -0.5 (0.85) | -0.3 (0.88) |
| book P7 | +1.3 (0.15) | +1.3 (0.25) | +0.7 (0.35) | +1.7 (0.15) | +2.7 (0.00) | -0.1 (0.57) |
| book U7 | -0.3 (0.72) | +0.1 (0.42) | -0.5 (0.90) | -0.9 (0.88) | +0.0 (0.47) | +0.4 (0.10) |
| book H7 | -0.2 (0.62) | -0.2 (0.57) | -0.1 (0.68) | -0.1 (0.57) | -0.1 (0.68) | -0.3 (0.78) |
| book M7 | -0.3 (0.88) | -0.6 (1.00) | -0.2 (0.85) | +0.4 (0.12) | -0.1 (0.68) | +0.0 (0.42) |
| book A6 | -0.2 (0.90) | -0.2 (0.68) | -0.2 (0.72) | -0.5 (0.80) | -0.1 (0.78) | +0.3 (0.05) |
| sess asia | -1.1 (0.72) | +0.0 (0.50) | -0.9 (0.78) | -2.2 (0.90) | +1.3 (0.03) | +0.7 (0.23) |
| sess london | +1.0 (0.17) | +1.1 (0.25) | +0.6 (0.28) | +0.7 (0.23) | -0.1 (0.60) | -0.3 (0.70) |
| sess nyam | +0.5 (0.12) | -0.3 (0.75) | -0.2 (0.62) | +2.2 (0.03) | +0.9 (0.12) | -0.1 (0.55) |
| sess nypm | +0.4 (0.07) | +0.5 (0.07) | +0.1 (0.23) | +0.2 (0.17) | -0.1 (0.90) | -0.3 (0.97) |
| vol 0 | -1.1 (0.93) | +0.2 (0.45) | -1.5 (0.97) | -3.7 (1.00) | +0.4 (0.17) | -0.2 (0.78) |
| vol 1 | +2.1 (0.00) | +1.9 (0.00) | +1.2 (0.05) | +2.3 (0.00) | +0.2 (0.38) | +0.1 (0.40) |
| vol 2 | +0.1 (0.50) | -1.3 (0.62) | -0.1 (0.53) | +2.0 (0.05) | +1.2 (0.07) | +0.2 (0.35) |


## (2) Multiplicity: 42 active book x session x vol-tag slices in PRE (6 books x 4 sessions x 3 tags, empty cells dropped)
Shipped layer: 5 slices with rank <= 0.05 (better than random halving) and 2 with rank >= 0.95 (worse). NULL (each of the 40 random layers ranked against the other 39): slices with rank <= 0.05 per random layer: mean 2.1, median 2, 90th pct 5, max 6; rank >= 0.95: mean 2.1. Share of random layers with at least as many <=0.05 slices as the shipped layer: 0.15. (Resolution of a rank with 39-40 comparators is 0.025, so rank <= 0.05 means at most 2 random layers are as good.)
