# REPORT RZ5 - range dependence of the pair itself (report only; pre-registered in PREREG_AUTOPILOT.md BATCH RZ)

Net R per trade (R = $9,600, after cost, before the account locks) of (i) the live rows (corrected 1-second engine, 2023-02..2026-10, unruled f=1) and (ii) the 1-minute NQ engine rows with the fixed 60/60 bracket (2013-2026, p1 run_fixed_real; ~90% entry match, weekly corr 0.88 to the live engine), grouped by the REALISED RTH range / ADR20 of the entry label (terciles cut on the whole 2013-26 distribution: 0.61, 0.90) and by the CAUSAL pre-open forecast tercile (RZ3 score at entry time).

### LIVE rows, 2023-26, by realised range tercile

| tercile | trades | mean net R | se | total R |
|---|---|---|---|---|
| low | 3280 | -0.0492 | 0.0158 | -161 |
| mid | 4819 | +0.0058 | 0.0133 | +28 |
| high | 4975 | +0.0897 | 0.0134 | +446 |

### LIVE rows, 2023-26, by forecast tercile

| tercile | trades | mean net R | se | total R |
|---|---|---|---|---|
| low | 2449 | +0.0286 | 0.0182 | +70 |
| mid | 6660 | +0.0427 | 0.0113 | +285 |
| high | 3980 | -0.0115 | 0.0153 | -46 |

### ENGINE rows, 2013-22, by realised range tercile

| tercile | trades | mean net R | se | total R |
|---|---|---|---|---|
| low | 2741 | -0.0451 | 0.0142 | -124 |
| mid | 2944 | -0.0672 | 0.0149 | -198 |
| high | 3765 | +0.0238 | 0.0142 | +90 |

### ENGINE rows, 2013-22, by forecast tercile

| tercile | trades | mean net R | se | total R |
|---|---|---|---|---|
| low | 1894 | +0.0010 | 0.0171 | +2 |
| mid | 4298 | -0.0348 | 0.0127 | -150 |
| high | 2752 | -0.0277 | 0.0170 | -76 |

### ENGINE rows, 2023-26, by realised range tercile

| tercile | trades | mean net R | se | total R |
|---|---|---|---|---|
| low | 1910 | -0.0153 | 0.0215 | -29 |
| mid | 2580 | +0.0425 | 0.0188 | +110 |
| high | 2476 | +0.0921 | 0.0193 | +228 |

### ENGINE rows, 2023-26, by forecast tercile

| tercile | trades | mean net R | se | total R |
|---|---|---|---|---|
| low | 1590 | +0.0247 | 0.0236 | +39 |
| mid | 3640 | +0.0536 | 0.0158 | +195 |
| high | 1749 | +0.0398 | 0.0230 | +70 |

## High-minus-low forecast tercile (mean net R per trade, difference and se)
- engine 2013-22: -0.0287 R (se 0.0241, n 2752/1894), t = -1.2
- engine 2023-26: +0.0151 R (se 0.0329, n 1749/1590), t = +0.5
- live 2023-26: -0.0401 R (se 0.0237, n 3980/2449), t = -1.7

Reading: if mean net R per trade rises with the realised-range tercile in both eras, the pair is range-dependent like the FVG sleeve; a forecast tilt is possible without look-ahead only if the causal forecast tercile reproduces that ordering (compare the two tables; RZ4 tests the tilt with full gates).

DONE RZ5