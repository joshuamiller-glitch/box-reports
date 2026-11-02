# DS3 ZONES LAYER vs SIZE - is the shipped HALF layer better than random halving at EQUAL RISK? (BASE-4, 2026-11-02T11:36Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Method: placebo layer = the shipped 7-line HALF mask (D20, half lots) replaced by a random half-lot mask with the same number of LIVE rows (A = same count per month, 100 draws; B = same count per month x book x session, 50 draws); OTE-62 B73, TH-L2 loss, profit lines, locks, sizer unchanged. Every placebo (and the references) has its WHOLE lot table scaled (engine lscale, integer-lot rounding) until the worst-20-weeks sum over ALL history equals the shipped layer's at scale 1 in the same frame (stop at |gap| <= 2.5% (<=5 engine runs); the residual gap is corrected linearly in mean, maxDD and ulcer: x target/achieved). Metrics per window: weekly mean ($k/wk), maxDD ($k, weekly cumulative), Calmar (mean/maxDD), ulcer (RMS of the weekly drawdown path, $k). RANK = share of placebo draws that are at least as GOOD as the shipped layer (higher mean / lower maxDD / higher Calmar / lower ulcer); small rank = the shipped layer beats random halving; ~0.5 = indistinguishable. Frames: lock none = per-book locks only (headline), 12R = + combined stack lock. Post-hoc.


## ANSWER ON V13Z (basis-N consistent; lock none = headline; compare V13X page DS3_ZONES_LAYER_VS_SIZE.md and V13Y page ..._V13Y.md)
**On V13Z the shipped HALF layer is better than random halving at equal risk only in PRE; in F9 / L6M / HOLD it is indistinguishable from random halving.** Lock none, 100 same-count random half-lot layers (+50 stratified), equal risk: F9 / L6M / HOLD equal-risk mean ranks 0.34 / 0.38 / 0.52, maxDD ranks 0.69 / 0.69 / 0.69, Calmar ranks 0.62 / 0.64 / 0.72 (shipped F9 maxDD 182.8k vs random median 164.7k: the layer is slightly worse than random on drawdown there); MID maxDD rank 0.12; PRE strongly better (mean 8.4k vs 4.4k, maxDD 173k vs 282k, Calmar 0.049 vs 0.016: ranks 0.00 / 0.01 / 0.00); X' no (0.39-0.47). 12R: F9-X' not better than random (ranks 0.31-0.96). PRE edge: all three PRE thirds on mean (ranks 0.04 / 0.04 / 0.03), maxDD only in thirds 2-3; books P7 (rank 0.00) and sessions Asia / NY-AM (0.00), vol tag 1 in F9 / L6M / HOLD / PRE (0.00) and tag 2 in PRE (0.03). Multiplicity: 8 of 42 PRE slices <= 0.05 vs 2.1 expected (share of random layers with >= 8: 0.00). Net: with the profit side on basis N the recent-year layer benefit that V13Y showed (ranks 0.1-0.2) disappears; the information in the lines shows in PRE only (as on V13X).

## LOCK NONE (headline)

### A: same count per month: 100 draws; equal-risk lot scale of the placebo layers: median 0.983 [0.917, 1.060] (shipped = 1.000); residual risk gap max 5.9%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 14.6 | 13.7 [11.8,16.9] | 0.34 | 182.8 | 164.7 [121.0,215.6] | 0.69 | 0.080 / 0.085 | 0.62 | 81.3 / 71.3 | 0.70 |
| L3M | 9.4 | 7.5 [5.3,10.9] | 0.15 | 51.8 | 50.6 [35.3,70.5] | 0.53 | 0.181 / 0.149 | 0.33 | 31.1 / 29.1 | 0.60 |
| L6M | 16.8 | 16.3 [14.2,19.2] | 0.38 | 182.8 | 164.7 [121.0,215.6] | 0.69 | 0.092 / 0.099 | 0.64 | 94.9 / 82.6 | 0.70 |
| HOLD | 14.9 | 15.0 [12.6,17.8] | 0.52 | 182.8 | 164.7 [125.7,215.6] | 0.69 | 0.082 / 0.093 | 0.72 | 79.9 / 70.1 | 0.77 |
| MID | 8.5 | 7.1 [4.3,11.5] | 0.32 | 50.6 | 61.4 [46.6,86.2] | 0.12 | 0.168 / 0.117 | 0.20 | 20.8 / 24.0 | 0.13 |
| PRE | 8.4 | 4.4 [2.9,7.2] | 0.00 | 172.9 | 281.6 [190.0,348.9] | 0.01 | 0.049 / 0.016 | 0.00 | 81.0 / 121.9 | 0.02 |
| X' | 1.2 | 0.9 [-0.4,2.3] | 0.39 | 88.5 | 92.3 [60.6,134.3] | 0.47 | 0.013 / 0.010 | 0.40 | 35.9 / 40.5 | 0.29 |

### B: same count per month x book x session: 50 draws; equal-risk lot scale of the placebo layers: median 0.990 [0.920, 1.043] (shipped = 1.000); residual risk gap max 3.3%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 14.6 | 13.4 [11.3,16.0] | 0.20 | 182.8 | 165.5 [128.2,221.6] | 0.68 | 0.080 / 0.080 | 0.50 | 81.3 / 73.3 | 0.66 |
| L3M | 9.4 | 7.4 [4.3,9.6] | 0.12 | 51.8 | 51.4 [38.2,67.9] | 0.54 | 0.181 / 0.142 | 0.26 | 31.1 / 30.3 | 0.58 |
| L6M | 16.8 | 15.8 [13.4,18.7] | 0.22 | 182.8 | 165.5 [128.2,221.6] | 0.68 | 0.092 / 0.094 | 0.56 | 94.9 / 84.5 | 0.68 |
| HOLD | 14.9 | 14.6 [12.4,16.8] | 0.36 | 182.8 | 165.5 [130.0,221.6] | 0.68 | 0.082 / 0.086 | 0.60 | 79.9 / 72.9 | 0.76 |
| MID | 8.5 | 7.2 [3.4,10.1] | 0.28 | 50.6 | 58.6 [47.2,80.9] | 0.16 | 0.168 / 0.127 | 0.20 | 20.8 / 24.1 | 0.10 |
| PRE | 8.4 | 4.6 [3.3,7.5] | 0.00 | 172.9 | 276.7 [189.4,333.6] | 0.02 | 0.049 / 0.016 | 0.02 | 81.0 / 114.8 | 0.02 |
| X' | 1.2 | 0.8 [-0.9,1.9] | 0.30 | 88.5 | 87.7 [64.8,115.1] | 0.52 | 0.013 / 0.009 | 0.30 | 35.9 / 37.2 | 0.44 |

### References (mean $k/wk / maxDD $k / Calmar / ulcer $k)
| layer | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| shipped layer, scale 1.00 | 14.6 / DD 182.8 / Cal 0.080 / U 81.3 | 9.4 / DD 51.8 / Cal 0.181 / U 31.1 | 16.8 / DD 182.8 / Cal 0.092 / U 94.9 | 14.9 / DD 182.8 / Cal 0.082 / U 79.9 | 8.5 / DD 50.6 / Cal 0.168 / U 20.8 | 8.4 / DD 172.9 / Cal 0.049 / U 81.0 | 1.2 / DD 88.5 / Cal 0.013 / U 35.9 |
| no layer, scale 0.902 (equal worst-20, gap 2.5%) | 13.7 / DD 152.8 / Cal 0.090 / U 66.6 | 9.2 / DD 46.1 / Cal 0.199 / U 26.8 | 15.8 / DD 152.8 / Cal 0.104 / U 77.3 | 13.5 / DD 152.8 / Cal 0.088 / U 67.2 | 7.8 / DD 55.0 / Cal 0.142 / U 21.3 | 3.7 / DD 323.2 / Cal 0.011 / U 140.5 | 0.3 / DD 96.0 / Cal 0.004 / U 44.0 |
| none layer, uniform lot scale 0.8 | 12.1 / DD 148.9 / Cal 0.081 / U 66.7 | 8.3 / DD 42.3 / Cal 0.197 / U 24.6 | 14.2 / DD 148.9 / Cal 0.096 / U 77.5 | 12.1 / DD 148.9 / Cal 0.081 / U 66.9 | 6.3 / DD 52.2 / Cal 0.121 / U 20.6 | 4.5 / DD 201.4 / Cal 0.022 / U 91.3 | 0.7 / DD 82.3 / Cal 0.008 / U 34.2 |
| shipped layer, uniform lot scale 0.8 | 11.5 / DD 133.7 / Cal 0.086 / U 58.5 | 6.9 / DD 46.0 / Cal 0.149 / U 26.6 | 12.8 / DD 133.7 / Cal 0.096 / U 68.2 | 11.4 / DD 133.7 / Cal 0.085 / U 60.3 | 7.5 / DD 33.3 / Cal 0.227 / U 15.8 | 5.7 / DD 146.3 / Cal 0.039 / U 62.1 | 0.2 / DD 76.3 / Cal 0.003 / U 32.3 |
| none layer, uniform lot scale 0.9 | 13.3 / DD 149.1 / Cal 0.090 / U 65.0 | 8.7 / DD 45.0 / Cal 0.194 / U 26.2 | 15.3 / DD 149.1 / Cal 0.103 / U 75.4 | 13.1 / DD 149.1 / Cal 0.088 / U 65.5 | 7.7 / DD 52.9 / Cal 0.146 / U 20.5 | 3.6 / DD 312.1 / Cal 0.012 / U 136.0 | 0.3 / DD 93.6 / Cal 0.004 / U 42.9 |
| shipped layer, uniform lot scale 0.9 | 12.5 / DD 127.3 / Cal 0.098 / U 54.7 | 7.1 / DD 48.9 / Cal 0.144 / U 29.8 | 14.6 / DD 127.3 / Cal 0.115 / U 63.1 | 12.2 / DD 127.3 / Cal 0.096 / U 61.7 | 6.7 / DD 41.3 / Cal 0.163 / U 19.9 | 4.8 / DD 236.5 / Cal 0.020 / U 90.7 | -0.4 / DD 82.9 / Cal -0.005 / U 41.2 |
| none layer, uniform lot scale 0.95 | 15.2 / DD 142.1 / Cal 0.107 / U 60.4 | 9.9 / DD 44.2 / Cal 0.224 / U 24.9 | 18.1 / DD 142.1 / Cal 0.127 / U 69.7 | 15.3 / DD 142.1 / Cal 0.107 / U 64.3 | 7.4 / DD 57.1 / Cal 0.129 / U 22.3 | 3.9 / DD 345.3 / Cal 0.011 / U 154.5 | 0.4 / DD 102.5 / Cal 0.004 / U 47.1 |
| shipped layer, uniform lot scale 0.95 | 14.1 / DD 118.5 / Cal 0.119 / U 49.3 | 7.4 / DD 50.5 / Cal 0.146 / U 30.3 | 16.6 / DD 118.5 / Cal 0.140 / U 56.8 | 14.1 / DD 118.5 / Cal 0.119 / U 59.5 | 7.4 / DD 38.8 / Cal 0.191 / U 18.8 | 5.3 / DD 243.0 / Cal 0.022 / U 96.5 | -0.4 / DD 91.8 / Cal -0.004 / U 45.2 |
| none layer, uniform lot scale 1.0 | 15.2 / DD 208.4 / Cal 0.073 / U 95.7 | 11.5 / DD 44.1 / Cal 0.260 / U 26.3 | 18.5 / DD 208.4 / Cal 0.089 / U 111.4 | 15.5 / DD 208.4 / Cal 0.074 / U 94.6 | 6.5 / DD 64.0 / Cal 0.101 / U 27.6 | 6.9 / DD 226.7 / Cal 0.030 / U 111.9 | 1.2 / DD 107.9 / Cal 0.011 / U 43.6 |

## 12R combined lock

### A: same count per month: 100 draws; equal-risk lot scale of the placebo layers: median 1.018 [0.955, 1.089] (shipped = 1.000); residual risk gap max 5.9%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 9.3 | 10.4 [8.0,13.5] | 0.76 | 117.1 | 110.7 [87.0,134.4] | 0.65 | 0.079 / 0.091 | 0.80 | 46.2 / 47.2 | 0.39 |
| L3M | 6.4 | 4.8 [1.7,10.0] | 0.29 | 51.7 | 50.4 [36.3,66.5] | 0.55 | 0.124 / 0.094 | 0.36 | 24.2 / 24.9 | 0.42 |
| L6M | 12.7 | 13.3 [10.4,16.8] | 0.66 | 117.1 | 109.7 [78.8,134.4] | 0.67 | 0.108 / 0.120 | 0.75 | 50.7 / 48.3 | 0.66 |
| HOLD | 10.2 | 11.7 [9.0,14.2] | 0.79 | 122.1 | 131.4 [100.0,167.9] | 0.31 | 0.084 / 0.089 | 0.56 | 54.0 / 53.0 | 0.57 |
| MID | 0.8 | 2.6 [-1.8,7.1] | 0.74 | 70.3 | 91.2 [66.4,111.2] | 0.09 | 0.011 / 0.028 | 0.70 | 29.4 / 37.8 | 0.10 |
| PRE | 3.0 | 3.5 [1.3,5.2] | 0.62 | 362.9 | 318.8 [248.2,396.9] | 0.80 | 0.008 / 0.010 | 0.70 | 155.9 / 130.5 | 0.86 |
| X' | -2.5 | -0.6 [-3.0,1.5] | 0.85 | 139.0 | 116.2 [62.6,198.3] | 0.69 | -0.018 / -0.007 | 0.96 | 94.8 / 62.6 | 0.83 |

### B: same count per month x book x session: 50 draws; equal-risk lot scale of the placebo layers: median 1.021 [0.955, 1.088] (shipped = 1.000); residual risk gap max 6.4%

| window | shipped mean | placebo mean med [5,95] | rank mean | shipped maxDD | placebo maxDD med [5,95] | rank maxDD | Calmar ship / plc med | rank Calmar | ulcer ship / plc med | rank ulcer |
|---|---|---|---|---|---|---|---|---|---|---|
| F9 | 9.3 | 9.7 [7.8,12.6] | 0.62 | 117.1 | 109.3 [92.0,123.7] | 0.76 | 0.079 / 0.089 | 0.78 | 46.2 / 47.1 | 0.48 |
| L3M | 6.4 | 4.2 [1.5,7.5] | 0.18 | 51.7 | 50.0 [40.7,63.0] | 0.58 | 0.124 / 0.084 | 0.28 | 24.2 / 24.0 | 0.52 |
| L6M | 12.7 | 12.8 [9.8,16.0] | 0.56 | 117.1 | 108.5 [88.9,123.7] | 0.78 | 0.108 / 0.120 | 0.74 | 50.7 / 46.2 | 0.72 |
| HOLD | 10.2 | 11.0 [9.1,13.7] | 0.70 | 122.1 | 128.4 [110.6,166.5] | 0.34 | 0.084 / 0.085 | 0.52 | 54.0 / 52.6 | 0.56 |
| MID | 0.8 | 2.6 [-1.4,6.1] | 0.74 | 70.3 | 93.3 [74.8,112.2] | 0.04 | 0.011 / 0.027 | 0.70 | 29.4 / 40.6 | 0.04 |
| PRE | 3.0 | 3.5 [1.8,5.1] | 0.64 | 362.9 | 318.4 [244.1,384.1] | 0.86 | 0.008 / 0.011 | 0.70 | 155.9 / 127.7 | 0.88 |
| X' | -2.5 | -2.1 [-4.4,0.0] | 0.64 | 139.0 | 153.3 [76.9,230.6] | 0.40 | -0.018 / -0.014 | 0.74 | 94.8 / 96.1 | 0.48 |

### References (mean $k/wk / maxDD $k / Calmar / ulcer $k)
| layer | F9 | L3M | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|---|
| shipped layer, scale 1.00 | 9.3 / DD 117.1 / Cal 0.079 / U 46.2 | 6.4 / DD 51.7 / Cal 0.124 / U 24.2 | 12.7 / DD 117.1 / Cal 0.108 / U 50.7 | 10.2 / DD 122.1 / Cal 0.084 / U 54.0 | 0.8 / DD 70.3 / Cal 0.011 / U 29.4 | 3.0 / DD 362.9 / Cal 0.008 / U 155.9 | -2.5 / DD 139.0 / Cal -0.018 / U 94.8 |
| no layer, scale 0.950 (equal worst-20, gap 0.8%) | 9.9 / DD 95.5 / Cal 0.104 / U 42.5 | 5.7 / DD 41.7 / Cal 0.137 / U 19.2 | 13.0 / DD 94.1 / Cal 0.138 / U 40.7 | 10.8 / DD 140.5 / Cal 0.077 / U 53.1 | 2.2 / DD 95.5 / Cal 0.023 / U 42.9 | 2.1 / DD 346.1 / Cal 0.006 / U 154.5 | 0.0 / DD 88.4 / Cal 0.000 / U 46.9 |
| none layer, uniform lot scale 0.8 | 8.7 / DD 80.2 / Cal 0.108 / U 34.9 | 4.7 / DD 35.2 / Cal 0.133 / U 15.5 | 10.8 / DD 80.2 / Cal 0.135 / U 34.8 | 9.5 / DD 106.9 / Cal 0.089 / U 40.7 | 3.1 / DD 77.7 / Cal 0.040 / U 32.3 | 3.1 / DD 217.2 / Cal 0.014 / U 88.0 | 0.9 / DD 50.5 / Cal 0.018 / U 24.3 |
| shipped layer, uniform lot scale 0.8 | 7.5 / DD 81.2 / Cal 0.093 / U 33.7 | 4.9 / DD 34.2 / Cal 0.143 / U 16.5 | 9.8 / DD 81.2 / Cal 0.121 / U 36.7 | 8.0 / DD 90.6 / Cal 0.088 / U 39.9 | 1.8 / DD 57.1 / Cal 0.031 / U 22.5 | 2.0 / DD 210.5 / Cal 0.010 / U 85.0 | -1.0 / DD 76.4 / Cal -0.013 / U 41.6 |
| none layer, uniform lot scale 0.9 | 9.0 / DD 87.2 / Cal 0.104 / U 38.2 | 5.5 / DD 37.7 / Cal 0.145 / U 17.6 | 11.4 / DD 87.2 / Cal 0.130 / U 38.2 | 9.1 / DD 117.0 / Cal 0.078 / U 46.1 | 3.1 / DD 80.5 / Cal 0.038 / U 35.2 | 3.3 / DD 235.8 / Cal 0.014 / U 99.8 | 0.9 / DD 54.9 / Cal 0.016 / U 27.9 |
| shipped layer, uniform lot scale 0.9 | 7.6 / DD 93.9 / Cal 0.081 / U 37.4 | 5.1 / DD 41.6 / Cal 0.122 / U 19.3 | 10.4 / DD 93.9 / Cal 0.110 / U 40.6 | 8.4 / DD 107.1 / Cal 0.078 / U 46.7 | 0.8 / DD 63.5 / Cal 0.012 / U 25.3 | 2.2 / DD 274.7 / Cal 0.008 / U 117.5 | -1.9 / DD 114.1 / Cal -0.016 / U 66.6 |
| none layer, uniform lot scale 0.95 | 9.8 / DD 94.7 / Cal 0.104 / U 42.1 | 5.7 / DD 41.4 / Cal 0.137 / U 19.1 | 12.9 / DD 93.3 / Cal 0.138 / U 40.4 | 10.7 / DD 139.4 / Cal 0.077 / U 52.7 | 2.2 / DD 94.7 / Cal 0.023 / U 42.6 | 2.1 / DD 343.3 / Cal 0.006 / U 153.2 | 0.0 / DD 87.7 / Cal 0.000 / U 46.5 |
| shipped layer, uniform lot scale 0.95 | 8.4 / DD 103.9 / Cal 0.081 / U 40.9 | 5.0 / DD 47.5 / Cal 0.106 / U 21.7 | 11.5 / DD 103.9 / Cal 0.110 / U 44.4 | 9.0 / DD 116.3 / Cal 0.077 / U 51.1 | 0.8 / DD 67.4 / Cal 0.012 / U 27.7 | 1.9 / DD 331.4 / Cal 0.006 / U 147.7 | -2.2 / DD 135.8 / Cal -0.016 / U 88.9 |
| none layer, uniform lot scale 1.0 | 10.6 / DD 108.1 / Cal 0.098 / U 49.1 | 6.3 / DD 45.7 / Cal 0.137 / U 21.5 | 14.2 / DD 108.1 / Cal 0.131 / U 46.4 | 10.9 / DD 159.3 / Cal 0.068 / U 60.3 | 1.8 / DD 108.1 / Cal 0.017 / U 51.0 | 1.9 / DD 415.7 / Cal 0.004 / U 190.6 | 0.1 / DD 111.9 / Cal 0.001 / U 55.5 |


# ATTRIBUTION OF THE SHIPPED LAYER'S PRE EDGE (lock none, equal risk; BASE-4, 2026-11-02T11:53Z)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Equal risk = lot table scaled to the shipped layer's worst-20 (all history), residual gap corrected linearly. EDGE of a layer = its metric minus the median of random half-lot layers of the SAME live-row count per month (equal risk); contribution of a line = shipped edge minus the edge of the layer without that line (positive = the line carries edge). Post-hoc.

## (1) Leave-one-line-out (the 8 shipped lines), shipped edge for reference: PRE: mean +4.0k, maxDD +109k better; F9: mean +0.9k, maxDD -18k better; L6M: mean +0.5k, maxDD -18k better
| line removed | live rows halved | scale c / gap | PRE | F9 | L6M |
|---|---|---|---|---|---|
| kijun1h | 3393 | 1.000/1.6% | mean 8.1 (edge +3.8, ranks 0.00/0.00); maxDD 165 (edge -116); line carries mean +0.1 / maxDD -7 | mean 14.9 (edge +1.3, ranks 0.10/0.60); maxDD 178 (edge +1); line carries mean -0.4 / maxDD -17 | mean 16.7 (edge +0.7, ranks 0.30/0.60); maxDD 178 (edge +1); line carries mean -0.3 / maxDD -17 |
| PDmid | 3687 | 1.025/0.4% | mean 8.3 (edge +4.3, ranks 0.00/0.00); maxDD 184 (edge -111); line carries mean -0.3 / maxDD -3 | mean 15.8 (edge +1.4, ranks 0.10/0.80); maxDD 174 (edge +28); line carries mean -0.6 / maxDD +10 | mean 18.4 (edge +1.5, ranks 0.05/0.80); maxDD 174 (edge +28); line carries mean -1.0 / maxDD +10 |
| CRT4h | 3390 | 1.037/1.4% | mean 7.9 (edge +3.7, ranks 0.00/0.00); maxDD 196 (edge -98); line carries mean +0.3 / maxDD +11 | mean 15.6 (edge +2.5, ranks 0.00/0.55); maxDD 178 (edge +3); line carries mean -1.6 / maxDD -16 | mean 17.7 (edge +2.4, ranks 0.10/0.55); maxDD 178 (edge +3); line carries mean -1.9 / maxDD -16 |
| KCup4h | 3565 | 1.033/1.9% | mean 8.4 (edge +4.1, ranks 0.00/0.05); maxDD 186 (edge -109); line carries mean -0.1 / maxDD -0 | mean 14.9 (edge +1.4, ranks 0.25/0.50); maxDD 180 (edge +2); line carries mean -0.5 / maxDD -16 | mean 17.1 (edge +1.0, ranks 0.25/0.50); maxDD 180 (edge +2); line carries mean -0.5 / maxDD -16 |
| camH3 | 3183 | 0.980/1.9% | mean 5.4 (edge +1.2, ranks 0.15/0.15); maxDD 246 (edge -51); line carries mean +2.7 / maxDD +58 | mean 14.8 (edge +0.8, ranks 0.35/0.00); maxDD 125 (edge -23); line carries mean +0.1 / maxDD -41 | mean 17.0 (edge +0.2, ranks 0.45/0.00); maxDD 125 (edge -23); line carries mean +0.2 / maxDD -41 |
| OTE705 | 3300 | 0.961/0.7% | mean 4.8 (edge +0.6, ranks 0.30/0.15); maxDD 239 (edge -70); line carries mean +3.4 / maxDD +39 | mean 13.3 (edge -0.6, ranks 0.80/0.35); maxDD 150 (edge -4); line carries mean +1.5 / maxDD -22 | mean 15.6 (edge -1.2, ranks 0.75/0.35); maxDD 150 (edge -4); line carries mean +1.6 / maxDD -22 |
| OTE79 | 3246 | 1.004/1.6% | mean 7.8 (edge +3.6, ranks 0.00/0.00); maxDD 179 (edge -122); line carries mean +0.4 / maxDD -13 | mean 15.3 (edge +1.4, ranks 0.15/0.60); maxDD 175 (edge +18); line carries mean -0.5 / maxDD -0 | mean 17.4 (edge +1.2, ranks 0.35/0.60); maxDD 175 (edge +18); line carries mean -0.7 / maxDD -0 |
| OTE62 B73 | 3824 | 1.007/0.7% | mean 8.5 (edge +3.8, ranks 0.00/0.00); maxDD 160 (edge -120); line carries mean +0.2 / maxDD -11 | mean 16.0 (edge +1.7, ranks 0.20/0.40); maxDD 162 (edge -2); line carries mean -0.8 / maxDD -20 | mean 18.6 (edge +1.2, ranks 0.25/0.40); maxDD 162 (edge -2); line carries mean -0.7 / maxDD -20 |

"ranks a/b" = share of the 20 matched-count random layers at least as good on mean / maxDD (small = the layer without the line still beats random). "line carries" = shipped edge minus the without-line edge in $k/wk (mean, positive = the line adds mean) and maxDD $k reduction attributable (positive = the line adds protection).

## (3) PRE split in thirds (shipped vs the 100 same-count equal-risk random layers; cumulative restarts in each third)
| segment | mean ship / placebo med | rank mean | maxDD ship / med | rank maxDD | Calmar ship / med | rank Calmar |
|---|---|---|---|---|---|---|
| third 1: ISO 202405..202429 (25 wk) | 6.2 / 3.3 | 0.04 | 124 / 105 | 0.89 | 0.050 / 0.032 | 0.13 |
| third 2: ISO 202430..202502 (25 wk) | 11.7 / 7.1 | 0.04 | 143 / 180 | 0.04 | 0.081 / 0.041 | 0.03 |
| third 3: ISO 202503..202527 (25 wk) | 7.3 / 2.9 | 0.03 | 173 / 228 | 0.07 | 0.042 / 0.012 | 0.04 |


## (2a) PRE edge by book and session (40 equal-risk random layers with cubes; own-series PRE mean $k/wk shipped / placebo median, rank = share of placebos at least as good; own maxDD $k)
| unit | PRE mean ship / plc | rank mean | PRE maxDD ship / plc | rank maxDD |
|---|---|---|---|---|
| book K7 | +1.3 / +0.7 | 0.10 | 41 / 55 | 0.12 |
| book P7 | +6.2 / +3.6 | 0.00 | 141 / 186 | 0.05 |
| book U7 | -0.1 / -0.3 | 0.05 | 83 / 99 | 0.12 |
| book H7 | -0.2 / -0.2 | 0.55 | 65 / 72 | 0.23 |
| book M7 | -0.1 / -0.2 | 0.28 | 77 / 77 | 0.47 |
| book A6 | +1.3 / +1.0 | 0.25 | 17 / 7 | 1.00 |
| session asia | +6.4 / +3.8 | 0.00 | 71 / 85 | 0.17 |
| session london | -5.8 / -5.5 | 0.82 | 486 / 466 | 0.70 |
| session nyam | +7.7 / +6.1 | 0.00 | 69 / 60 | 0.70 |
| session nypm | +0.1 / -0.0 | 0.25 | 37 / 45 | 0.17 |


## (2b) The PRE episode ISO 2025-W05..W16 (shipped maxDD 178k, London carries -220k): sum of PRE P&L over those weeks by book / session, $k (shipped vs equal-risk random layers; rank = share of placebos at least as good)
Total episode P&L: shipped -123k vs placebo median -194k [-236,-141], rank 0.03.
| unit | shipped | placebo median [5,95] | rank |
|---|---|---|---|
| book K7 | -9 | -17 [-39,-0] | 0.23 |
| book P7 | +27 | -39 [-64,+25] | 0.05 |
| book U7 | -52 | -52 [-62,-43] | 0.55 |
| book H7 | -26 | -31 [-37,-20] | 0.20 |
| book M7 | -71 | -70 [-80,-63] | 0.53 |
| book A6 | +7 | +8 [+5,+10] | 0.75 |
| session asia | +81 | +15 [-24,+54] | 0.00 |
| session london | -217 | -221 [-240,-192] | 0.40 |
| session pre | +0 | +0 [+0,+0] | 1.00 |
| session nyam | +20 | +27 [-3,+49] | 0.78 |
| session nypm | -7 | -12 [-23,-1] | 0.20 |
| session close | +0 | +0 [+0,+0] | 1.00 |


## (2c) PRE edge by day vol tercile (day_regime vol_tag_today): PRE mean $k/wk contributed by days of each tag, shipped vs equal-risk random layers
| tag | days | shipped | placebo median | rank |
|---|---|---|---|---|
| vol tag 0.0 | 130 | -2.2 | -2.1 | 0.65 |
| vol tag 1.0 | 96 | -3.2 | -4.1 | 0.00 |
| vol tag 2.0 | 138 | +13.7 | +10.4 | 0.03 |


# CONSISTENCY AND MULTIPLICITY OF THE PRE EDGE (BASE-4, 2026-11-02T11:53Z; lock none, equal risk; 40 random half-lot layers with cubes)

Episodes lookup: autopilot/DS3_ZONES_EPISODES.md. Heat table: cell = shipped minus random-layer MEDIAN of the slice's mean contribution ($k/wk) and, in brackets, the rank = share of the random layers with a contribution at least as high (small = the shipped layer beats random halving in that slice; PRE column is where the slices were found; the other columns are out-of-selection checks).

## (1) Heat table: slice x window
| slice | F9 | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|
| book K7 | +0.5 (0.12) | +0.6 (0.17) | +0.3 (0.15) | +0.2 (0.33) | +0.5 (0.10) | +0.0 (0.50) |
| book P7 | +0.8 (0.35) | +0.8 (0.35) | +0.0 (0.50) | +0.2 (0.47) | +2.7 (0.00) | -0.3 (0.75) |
| book U7 | +0.0 (0.45) | -0.2 (0.80) | -0.0 (0.53) | +0.5 (0.15) | +0.3 (0.05) | -0.1 (0.57) |
| book H7 | +0.3 (0.23) | -0.1 (0.57) | +0.2 (0.30) | +1.1 (0.00) | -0.0 (0.55) | +0.2 (0.20) |
| book M7 | -0.4 (0.97) | -0.4 (0.90) | -0.4 (0.97) | -0.2 (0.62) | +0.1 (0.28) | +0.2 (0.12) |
| book A6 | -0.1 (0.78) | +0.1 (0.25) | +0.3 (0.17) | -0.5 (0.93) | +0.3 (0.25) | +0.3 (0.00) |
| sess asia | +1.2 (0.17) | +1.2 (0.30) | +0.8 (0.28) | +1.5 (0.17) | +2.6 (0.00) | +0.6 (0.12) |
| sess london | -0.2 (0.62) | -0.1 (0.60) | -0.7 (0.85) | -1.1 (0.75) | -0.3 (0.82) | -0.3 (0.80) |
| sess nyam | +0.1 (0.28) | +0.1 (0.35) | +0.2 (0.33) | +0.0 (0.45) | +1.6 (0.00) | +0.1 (0.40) |
| sess nypm | -0.1 (0.65) | -0.4 (0.90) | -0.2 (0.88) | +0.7 (0.00) | +0.1 (0.25) | -0.2 (0.93) |
| vol 0 | -1.0 (0.93) | -0.5 (0.85) | -1.3 (0.97) | -2.3 (0.97) | -0.1 (0.65) | -0.2 (0.68) |
| vol 1 | +2.1 (0.00) | +2.4 (0.00) | +1.5 (0.00) | +1.2 (0.15) | +0.9 (0.00) | -0.1 (0.60) |
| vol 2 | +0.1 (0.47) | -1.3 (0.68) | -0.2 (0.55) | +2.6 (0.07) | +3.4 (0.03) | +0.5 (0.23) |


## (2) Multiplicity: 42 active book x session x vol-tag slices in PRE (6 books x 4 sessions x 3 tags, empty cells dropped)
Shipped layer: 8 slices with rank <= 0.05 (better than random halving) and 2 with rank >= 0.95 (worse). NULL (each of the 40 random layers ranked against the other 39): slices with rank <= 0.05 per random layer: mean 2.1, median 2, 90th pct 4, max 6; rank >= 0.95: mean 2.1. Share of random layers with at least as many <=0.05 slices as the shipped layer: 0.00. (Resolution of a rank with 39-40 comparators is 0.025, so rank <= 0.05 means at most 2 random layers are as good.)
