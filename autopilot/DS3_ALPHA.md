# DS3_ALPHA - one combined forecast for NQ (W-AL1, T-ALPHA parts 1, 2, 4-NQ)

VERDICT (data ends 2026-10-30; FIRST PASS, NQ, test span 2023-10..2026-10-16 for the full feature set, 2023-04..2026-10-30 for price/intermarket/clock): the combined NQ forecast has a small real information coefficient at 5-15 minutes (average of ridge/GBM/MLP: IC +0.0103 at 5 min t +4.6, +0.0083 at 15 min t +2.5) that is carried by price and intermarket reversal in the thin hours (Asia), the same 200-input nonsense pipeline gives -0.0001 / -0.0018; at 30-120 min the IC (+0.0055 at 60 min) is not distinguishable from the nonsense null; the ~400 library/L2/L3/counting inputs add nothing over the 90 price/intermarket/clock inputs; on D7 the forecast as size is not separable from a shuffled-forecast placebo yet (see Part 2). Numbers are FIRST PASS, one run per cell.

## 0. What was built, and the rules
- Grid: 5-minute decision grid (bar end at :00, :05, ...), NQ 2018-01..2026-10-30, 623,287 decision rows; horizons 5/15/30/60/120 min; training target = return / (trailing 1-min sigma x sqrt(h)), clipped +-4 (vol-scaled); IC is scored against the raw point return (Spearman, pooled ranks, day-clustered standard errors).
- Walk-forward: refit every 14 days; train = last 3 years ending 3 calendar days before the test block (purge > longest horizon 120 min); no tuning on the test span; models ridge (alpha = 0.5 n), LightGBM (150 trees, 8 leaves, min 400/leaf, lambda 50, subsample 0.5), sklearn MLP (32-16, alpha 1, 25 epochs), and avg = mean of the three standardised forecasts. Code: code/th_alpha (data.py, audit.py, grid.py, assemble.py, wf.py, score.py, trades.py, run_wf_cfg.py).
- Inputs (blocks): price (own 1-min bars; returns, vol, range position, VWAP/EMA distance, volume, pressure), intermarket (ES/RTY/YM returns and beta-residuals), clock/calendar (time of day, dow, opex, month end, bars since roll), CF4 indicator library (150 cluster representatives out of 2,393 f_* columns), CF5 calendar/session blocks B16/B7/B9/B8 (60 reps), CF2 L2 book+tape (48 reps of 72 derived), CF2 L3 MBO (48 reps of 144 derived), CF6 counting/ICT/analog (50 reps of 185). Representatives chosen on the SELECTION WINDOW 2023-02..2023-08 only (monthly Spearman IC stability + greedy de-correlation at 0.85); first test block 2023-10-02.
- Not yet in this pass: CME/UW options block (feat1m J_*), macro block, other markets (W-AL2), horizons beyond 120 min.

## 1. Data audit (Part 4 item 15)
| market | rows | monotonic | dup ts | bad OHLC | gaps >5 min | gaps >1 h | max gap h | same-close runs >=10 | spike-revert bars | roll bars | abs ret at roll med/max | off-tick closes |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| NQ | 3,111,736 | True | 0 | 0 | 3260 | 2260 | 76.8 | 19 | 14 | 35 | 2.25 / 12.75 | 0% |
| ES | 3,111,625 | True | 0 | 0 | 3235 | 2232 | 76.8 | 134 | 845 | 35 | 0.50 / 2.50 | 0% |
| RTY | 2,971,937 | True | 0 | 0 | 5665 | 2258 | 76.8 | 23 | 9 | 35 | 0.20 / 1.60 | 0% |
| YM | 3,072,655 | True | 0 | 0 | 3420 | 2250 | 76.8 | 15 | 8 | 35 | 3.00 / 18.00 | 0% |

- Timestamp alignment to the second: ES bars present at 99.95% of NQ bar stamps, RTY 96.85%, YM 97.40% (missing = no print in that market-minute). Correlation of NQ and ES 1-min returns by lag (-2..+2 min): +0.004, +0.002, +0.915, -0.001, +0.003 (peak exactly at lag 0 for ES, RTY, YM: no clock offset).
- Two independent NQ sources (databento ohlcv-1m with my additive roll splice vs W-CF6's cf6_min1_NQ_long.npz): 1,267,708 common stamps, 1-min return difference median 0.0 and 99th pct 0.0, 0 differences > 1 point.
- Roll handling: continuous series is additively back-adjusted at each instrument-id change (35 rolls 2018-2026); returns in points are roll-free; 1-min return at the first bar after a roll is ordinary (median 2.25 pt for NQ, same as the overnight open). Absolute price levels are NOT comparable across years: every feature uses differences or ratios scaled by trailing 1-min volatility. Targets that would cross the 17:00-18:00 ET halt, a weekend or a gap > 3 min before the end-bar are dropped (no cross-session returns).
- Stale prints: NQ has 19 runs of 10+ identical closes (max 138 min, weekend/halt edges), ES 134 (max 316 min), RTY 23, YM 15; ES has 845 spike-and-revert bars (4x-median-style filter) mostly overnight; none removed (they are real thin-market prints, and a clip at +-4 sigma on the training target limits their effect). YM data on the box ends 2026-10-16.

- LOOK-AHEAD TEST (univariate, every one of the 90 price/intermarket/clock inputs, 2023-04..2026-10, IC vs next-5 and next-15 min vol-scaled return). Mean |IC| with the input taken one decision step OLDER / as built / one decision step NEWER (future information injected on purpose):

| horizon min | older (t-5 min) | as built | newer (t+5 min) |
|---|---|---|---|
| 5 | 0.0036 | 0.0073 | 0.2045 |
| 15 | 0.0044 | 0.0061 | 0.1175 |

  Max |IC| of any single input as built = 0.0223; max with one step of future injected = 0.999. The test is therefore sensitive (a one-bar leak would show as IC 0.1-1.0) and no input jumps: IC decays smoothly from newer to as-built to older. The full-library inputs come from other agents; their own builders were checked by them against stored signal-time values (0 differences); a joint shift test of the full set (run lag_m1/lag_p1) is in section 4 when finished.


- JOINT shift test (ridge, full set): as built +0.0112, +0.0052, +0.0050, +0.0058, +0.0097 ; inputs one step OLDER +0.0018, +0.0039, +0.0015, +0.0034, +0.0089 (IC falls, as it must if there is no leak; the one-step-NEWER run is pending).
## 2. Planted-edge check
A synthetic AR(1) signal (persistence 0.9 per decision step) was added to every vol-scaled training/test target with strength giving corr(signal, target) = 0.02, and appended as one extra input to the 90 core inputs; the whole walk-forward was rerun. Scored against the PLANTED target (ys), core-only run of the same inputs scored against the same planted target for the baseline:
| quantity | 5m | 15m | 30m | 60m | 120m |
|---|---|---|---|---|---|
| ridge: planted run IC | +0.0212 | +0.0126 | +0.0109 | +0.0117 | +0.0104 |
| ridge: same inputs without the planted one (core run) on the planted target | +0.0114 | +0.0031 | -0.0001 | -0.0027 | -0.0057 |
| ridge: RECOVERED = difference | +0.0098 (se ~0.0021) | +0.0095 (se ~0.0033) | +0.0109 (se ~0.0045) | +0.0144 (se ~0.0061) | +0.0160 (se ~0.0083) |
| avg: planted run IC | +0.0189 | +0.0152 | +0.0119 | +0.0122 | +0.0066 |
| avg: same inputs without the planted one (core run) on the planted target | +0.0110 | +0.0086 | +0.0008 | -0.0028 | -0.0114 |
| avg: RECOVERED = difference | +0.0079 (se ~0.0020) | +0.0066 (se ~0.0031) | +0.0111 (se ~0.0041) | +0.0150 (se ~0.0057) | +0.0180 (se ~0.0080) |
| planted signal alone vs planted target (what a perfect model would get) | +0.0208 | +0.0212 | +0.0224 | +0.0283 | +0.0337 |

Reading: the pipeline recovers the planted edge at the right sign and horizon-by-horizon about 45-70% of its size for ridge (+0.010 to +0.016 against the 0.02-0.03 present), i.e. it is sensitive to a 0.02 signal but shrinks it by the heavy regularisation; GBM and MLP recover less (see planted_ic.csv). A real 0.02 input would therefore show up as +0.01 to +0.015 in the forecast IC. Noise floor: se 0.002 at 5 min to 0.008 at 120 min, so a 0.01 gain is detectable at 5-60 min but not at 120 min.

## 3. Forecast information coefficient (walk-forward, cluster-robust by day; null = same pipeline, 200 nonsense inputs)
Format: IC (t day-clustered) | null IC of the nonsense run for the same cell. avg model (mean of ridge/GBM/MLP).

### 3a. Full input set (test 2023-10-02 .. 2026-10-16)
| slice | 5m | 15m | 30m | 60m | 120m |
|---|---|---|---|---|---|
| all | +0.0103 (t +4.6) | null -0.0001 | +0.0083 (t +2.5) | null -0.0018 | +0.0039 (t +0.9) | null -0.0062 | +0.0055 (t +0.9) | null -0.0077 | +0.0047 (t +0.5) | null -0.0087 |
| recent_since_2026-05 | +0.0122 (t +2.1) | null +0.0013 | +0.0134 (t +1.4) | null -0.0041 | +0.0098 (t +0.7) | null -0.0160 | +0.0225 (t +1.2) | null -0.0203 | +0.0203 (t +0.8) | null -0.0313 |
| sess_asia | +0.0216 (t +5.9) | null +0.0016 | +0.0246 (t +4.4) | null +0.0026 | +0.0171 (t +2.3) | null +0.0111 | +0.0152 (t +1.5) | null +0.0070 | +0.0107 (t +0.7) | null +0.0167 |
| sess_london | +0.0092 (t +2.3) | null +0.0015 | +0.0031 (t +0.6) | null -0.0008 | +0.0031 (t +0.4) | null -0.0119 | +0.0115 (t +1.2) | null -0.0154 | +0.0011 (t +0.1) | null -0.0077 |
| sess_pre | +0.0020 (t +0.2) | null +0.0095 | -0.0036 (t -0.3) | null -0.0070 | -0.0150 (t -1.1) | null -0.0257 | -0.0085 (t -0.5) | null -0.0457 | -0.0139 (t -0.5) | null -0.0589 |
| sess_nyam | -0.0026 (t -0.4) | null -0.0127 | -0.0028 (t -0.3) | null -0.0156 | -0.0154 (t -1.2) | null -0.0204 | -0.0290 (t -1.8) | null -0.0255 | -0.0266 (t -1.2) | null -0.0508 |
| sess_nypm | +0.0089 (t +1.7) | null -0.0009 | +0.0009 (t +0.1) | null -0.0005 | -0.0021 (t -0.2) | null -0.0103 | +0.0076 (t +0.6) | null +0.0028 | +0.0166 (t +0.9) | null -0.0079 |
| year_2023 | +0.0204 (t +2.9) | null -0.0016 | +0.0159 (t +1.2) | null -0.0057 | +0.0045 (t +0.3) | null +0.0049 | +0.0130 (t +0.7) | null +0.0016 | -0.0005 (t -0.0) | null -0.0010 |
| year_2024 | +0.0140 (t +3.4) | null +0.0005 | +0.0094 (t +1.6) | null +0.0018 | +0.0027 (t +0.4) | null -0.0016 | -0.0013 (t -0.1) | null -0.0044 | +0.0043 (t +0.3) | null -0.0021 |
| year_2025 | +0.0060 (t +1.6) | null -0.0013 | +0.0076 (t +1.3) | null -0.0059 | +0.0036 (t +0.5) | null -0.0089 | +0.0038 (t +0.4) | null -0.0074 | +0.0122 (t +0.8) | null -0.0064 |
| year_2026 | +0.0107 (t +2.4) | null -0.0013 | +0.0088 (t +1.3) | null -0.0020 | +0.0054 (t +0.6) | null -0.0130 | +0.0110 (t +0.8) | null -0.0150 | -0.0029 (t -0.2) | null -0.0195 |

### 3b. By model (all slices pooled), full input set
| model | 5m | 15m | 30m | 60m | 120m |
|---|---|---|---|---|---|
| avg | 0.0103 | 0.0083 | 0.0039 | 0.0055 | 0.0047 |
| gbm | 0.0075 | 0.0109 | 0.0008 | 0.0007 | -0.0084 |
| mlp | 0.0007 | 0.0015 | -0.0004 | 0.0021 | 0.0044 |
| ridge | 0.0112 | 0.0052 | 0.0050 | 0.0058 | 0.0097 |

Nonsense (200 inputs, identical pipeline):

| model | 5m | 15m | 30m | 60m | 120m |
|---|---|---|---|---|---|
| avg | -0.0001 | -0.0018 | -0.0062 | -0.0077 | -0.0087 |
| gbm | 0.0015 | -0.0009 | -0.0050 | -0.0071 | -0.0084 |
| mlp | -0.0013 | 0.0001 | -0.0012 | -0.0002 | 0.0002 |
| ridge | -0.0003 | -0.0030 | -0.0071 | -0.0068 | -0.0106 |

### 3c. Price + intermarket + clock only (90 inputs, test 2023-04-03 .. 2026-10-30, 43 months)
| slice | 5m | 15m | 30m | 60m | 120m |
|---|---|---|---|---|---|
| all | +0.0106 (t +5.2) | +0.0120 (t +3.7) | +0.0068 (t +1.6) | +0.0076 (t +1.3) | +0.0045 (t +0.5) |
| recent_since_2026-05 | +0.0056 (t +1.1) | +0.0244 (t +2.8) | +0.0187 (t +1.6) | +0.0325 (t +1.9) | +0.0259 (t +1.1) |
| sess_asia | +0.0198 (t +5.8) | +0.0159 (t +3.0) | +0.0076 (t +1.1) | +0.0032 (t +0.3) | -0.0006 (t -0.1) |
| sess_london | +0.0094 (t +2.4) | +0.0038 (t +0.7) | +0.0007 (t +0.1) | +0.0021 (t +0.2) | -0.0123 (t -0.8) |
| sess_pre | +0.0062 (t +0.8) | +0.0061 (t +0.6) | -0.0064 (t -0.5) | -0.0050 (t -0.3) | -0.0128 (t -0.5) |
| sess_nyam | -0.0010 (t -0.2) | +0.0114 (t +1.3) | +0.0069 (t +0.6) | +0.0109 (t +0.7) | +0.0159 (t +0.8) |
| sess_nypm | +0.0092 (t +1.8) | +0.0125 (t +1.7) | +0.0083 (t +0.8) | +0.0146 (t +1.1) | +0.0268 (t +1.3) |
| year_2023 | +0.0133 (t +3.0) | +0.0007 (t +0.1) | +0.0023 (t +0.2) | +0.0012 (t +0.1) | -0.0029 (t -0.2) |
| year_2024 | +0.0188 (t +5.0) | +0.0153 (t +2.6) | +0.0085 (t +1.1) | +0.0020 (t +0.2) | -0.0048 (t -0.3) |
| year_2025 | +0.0056 (t +1.4) | +0.0070 (t +1.2) | -0.0029 (t -0.3) | -0.0054 (t -0.5) | +0.0007 (t +0.0) |
| year_2026 | +0.0083 (t +2.0) | +0.0220 (t +3.2) | +0.0157 (t +1.8) | +0.0251 (t +2.0) | +0.0112 (t +0.6) |

Ridge only, same inputs:

| slice | 5m | 15m | 30m | 60m | 120m |
|---|---|---|---|---|---|
| all | +0.0107 (t +5.2) | +0.0069 (t +2.1) | +0.0069 (t +1.5) | +0.0073 (t +1.1) | +0.0125 (t +1.4) |
| recent_since_2026-05 | +0.0077 (t +1.5) | +0.0198 (t +2.2) | +0.0222 (t +1.7) | +0.0215 (t +1.1) | +0.0248 (t +1.0) |
| sess_asia | +0.0231 (t +7.0) | +0.0170 (t +3.2) | +0.0137 (t +1.8) | +0.0089 (t +0.9) | +0.0122 (t +0.9) |
| year_2023 | +0.0201 (t +3.9) | +0.0070 (t +0.9) | +0.0085 (t +0.8) | +0.0074 (t +0.5) | +0.0097 (t +0.5) |
| year_2024 | +0.0185 (t +4.8) | +0.0048 (t +0.8) | +0.0031 (t +0.4) | +0.0011 (t +0.1) | +0.0072 (t +0.4) |
| year_2025 | +0.0062 (t +1.7) | +0.0051 (t +0.8) | -0.0005 (t -0.1) | -0.0013 (t -0.1) | +0.0073 (t +0.4) |
| year_2026 | +0.0038 (t +0.9) | +0.0104 (t +1.5) | +0.0142 (t +1.4) | +0.0167 (t +1.2) | +0.0144 (t +0.7) |

Decay with horizon and stability: the IC is largest at 5 min and falls toward the null by 30-60 min; by year it is positive in every year at 5 min (t 1.6-3.4) and the recent months since 2026-05 are not weaker. Per-session: Asia carries the 5-30 min IC; NY AM is zero or negative at longer horizons (the full set is worse than price-only there).

## 4. Which data carries it (block ablation)
PENDING (runs queued in code/th_alpha/chain2.sh: abl_price, abl_inter, abl_clock, abl_cf4ind, abl_cf5cal, abl_l2, abl_l3, abl_cf6, only_l2, only_l3, only_price). What is already known: the 90-input price/intermarket/clock set alone gives IC 0.0106/0.0120 (5/15 min), the 400-input full set 0.0103/0.0083, so the library/L2/L3/counting blocks add nothing on average; they only shift where the IC sits (full set better in Asia 15-30 min, worse in NY AM).

## 5. Trades with costs inside (Part 1 item 5, NQ)
Rules: position = rounded z-score of the forecast (forecast / trailing 20-day std) up to 3 lots, enter when |z| >= band, hold until |z| < 0.3 band (hysteresis = no-trade band), flat when the next 5-min return is unknown (halt/gap); trades at the decision price with slippage 0.23 pt per side (measured entry) + fee $4.84 RT = $2.42/side, $20 per point; P&L over each 5-min step. gross/net are $ per trading day at up to 3 lots. FIRST PASS: no stop model, execution at the decision bar close.
### full set (2023-10..2026-10-16), band |z|>=2, market execution

| h | session | gross $/day | cost $/day | net $/day | contracts/day | avg hold min | net Sharpe (ann) |
|---|---|---|---|---|---|---|---|
| 5 | all | 566.9 | 348.2 | 218.7 | 49.6 | 18.1 | 0.5 |
| 5 | asia | 496.3 | 404.1 | 92.1 | 57.6 | 20.2 | 0.3 |
| 5 | london | 331.6 | 387.0 | -55.4 | 55.1 | 22.0 | -0.3 |
| 5 | nyam | 75.7 | 228.2 | -152.5 | 32.5 | 28.8 | -0.3 |
| 5 | nypm | 98.9 | 298.6 | -199.7 | 42.5 | 25.6 | -0.4 |
| 5 | asia+london | 567.6 | 412.5 | 155.1 | 58.8 | 18.4 | 0.5 |
| 15 | all | 579.2 | 317.1 | 262.2 | 45.2 | 24.0 | 0.6 |
| 15 | asia | 539.1 | 322.2 | 217.0 | 45.9 | 25.2 | 0.7 |
| 15 | london | 301.4 | 318.1 | -16.8 | 45.3 | 25.1 | -0.1 |
| 15 | nyam | 55.9 | 201.6 | -145.7 | 28.7 | 30.8 | -0.3 |
| 15 | nypm | -112.5 | 235.8 | -348.3 | 33.6 | 30.7 | -1.0 |
| 15 | asia+london | 604.8 | 342.9 | 261.9 | 48.9 | 23.6 | 0.9 |
| 60 | all | 456.7 | 248.9 | 207.9 | 35.5 | 40.4 | 0.4 |
| 60 | asia | 273.1 | 250.8 | 22.3 | 35.7 | 36.7 | 0.1 |
| 60 | london | 190.1 | 268.2 | -78.0 | 38.2 | 31.3 | -0.3 |
| 60 | nyam | -227.0 | 169.2 | -396.2 | 24.1 | 33.7 | -0.9 |
| 60 | nypm | -46.5 | 166.3 | -212.8 | 23.7 | 43.2 | -0.6 |
| 60 | asia+london | 221.4 | 278.0 | -56.6 | 39.6 | 35.6 | -0.2 |
| 120 | all | 339.0 | 205.5 | 133.5 | 29.3 | 63.6 | 0.3 |
| 120 | asia | 530.9 | 205.1 | 325.8 | 29.2 | 46.3 | 1.0 |
| 120 | london | 94.5 | 211.6 | -117.1 | 30.1 | 40.1 | -0.5 |
| 120 | nyam | 82.0 | 138.2 | -56.2 | 19.7 | 39.3 | -0.1 |
| 120 | nypm | -35.9 | 134.2 | -170.1 | 19.1 | 53.5 | -0.4 |
| 120 | asia+london | 301.9 | 220.7 | 81.2 | 31.4 | 49.7 | 0.3 |

Net $/day, market (slip 0.23 pt) vs passive-fill upper bound (slip 0, no queue/adverse-selection penalty):

| h | session | mkt_slip.23 | passive_slip0 |
|---|---|---|---|
| 15 | all | 262 | 470 |
| 15 | asia | 217 | 428 |
| 120 | all | 133 | 268 |
| 120 | asia | 326 | 460 |

### price+intermarket+clock (2023-04..2026-10-30), band |z|>=2, market execution

| h | session | gross $/day | cost $/day | net $/day | contracts/day | avg hold min | net Sharpe (ann) |
|---|---|---|---|---|---|---|---|
| 5 | all | 560.8 | 292.6 | 268.2 | 41.7 | 22.9 | 0.6 |
| 5 | asia | 412.7 | 292.6 | 120.1 | 41.7 | 23.1 | 0.4 |
| 5 | london | 136.6 | 349.9 | -213.3 | 49.8 | 22.9 | -1.0 |
| 5 | nyam | 59.4 | 192.7 | -133.3 | 27.5 | 31.0 | -0.3 |
| 5 | nypm | 182.2 | 235.2 | -53.1 | 33.5 | 29.6 | -0.2 |
| 5 | asia+london | 405.5 | 341.5 | 64.0 | 48.6 | 21.0 | 0.2 |
| 15 | all | 412.4 | 231.8 | 180.6 | 33.0 | 34.9 | 0.4 |
| 15 | asia | 408.0 | 223.0 | 185.0 | 31.8 | 33.4 | 0.7 |
| 15 | london | 78.0 | 274.3 | -196.2 | 39.1 | 28.3 | -0.9 |
| 15 | nyam | 111.7 | 160.0 | -48.3 | 22.8 | 35.2 | -0.1 |
| 15 | nypm | 385.3 | 145.1 | 240.2 | 20.7 | 42.9 | 0.7 |
| 15 | asia+london | 301.3 | 270.9 | 30.5 | 38.6 | 29.1 | 0.1 |
| 60 | all | 570.6 | 166.9 | 403.7 | 23.8 | 57.5 | 0.9 |
| 60 | asia | 270.8 | 185.2 | 85.6 | 26.4 | 48.9 | 0.3 |
| 60 | london | 148.2 | 209.9 | -61.7 | 29.9 | 38.0 | -0.3 |
| 60 | nyam | 162.8 | 136.1 | 26.7 | 19.4 | 39.8 | 0.1 |
| 60 | nypm | 262.8 | 108.9 | 153.9 | 15.5 | 64.6 | 0.5 |
| 60 | asia+london | 367.1 | 205.2 | 161.9 | 29.2 | 44.4 | 0.6 |
| 120 | all | 457.5 | 138.0 | 319.5 | 19.7 | 79.8 | 0.7 |
| 120 | asia | 309.0 | 157.4 | 151.6 | 22.4 | 62.8 | 0.5 |
| 120 | london | 34.0 | 177.6 | -143.6 | 25.3 | 45.8 | -0.6 |
| 120 | nyam | 96.3 | 130.8 | -34.4 | 18.6 | 42.5 | -0.1 |
| 120 | nypm | 319.7 | 93.9 | 225.8 | 13.4 | 80.6 | 0.6 |
| 120 | asia+london | 333.0 | 167.8 | 165.2 | 23.9 | 58.7 | 0.6 |

Net $/day, market (slip 0.23 pt) vs passive-fill upper bound (slip 0, no queue/adverse-selection penalty):

| h | session | mkt_slip.23 | passive_slip0 |
|---|---|---|---|
| 15 | all | 181 | 332 |
| 15 | asia | 185 | 331 |
| 120 | all | 319 | 410 |
| 120 | asia | 152 | 255 |

Reading: gross edge exists (the forecast direction is right slightly more often) but about 40-70% of gross is eaten by cost at market execution; net Sharpe stays below ~1 and is not statistically separable from zero over ~900 days. Asia 120-min and Asia+London 15-min are the best cells. Capacity: the edge is measured at <= 3 lots; at 5-50 lots the extra slippage (assume +0.02 pt per additional contract in Asia, NQ top-of-book 10-30 lots) removes the net quickly: 5 lots is the practical size here, 50 lots is not supported at market execution. Passive entry is the route to keep the 5-min reversal (needs queue-position data, W-AL2 part 4).

## 6. Part 2 - forecast on D7 (exact engine, tag AL, JN05W2 base lots, L6M = 2026-05..2026-10, every signal evaluated, none skipped)
Forecast used: core (price+intermarket+clock) avg_h from the walk-forward, mapped to each signal second (last 5-min decision <= signal second), a = side x z. Sets: S15/S60/S120 = size m = clip(1+0.35a, 0.5, 1.5) renormalised to mean 1; H60/H120 = half size when a < -0.5; T60 = target distance x clip(1+0.25a, 0.75, 1.25); PL120 and PLxx_n = same size table as S with the forecast SHUFFLED within book and month (placebo). Identity proven: TL3_AL_ID reproduces 598 trades / 25,943.82 on 202610.

| set | n | lots | tot | tot484 | maxdd | worst_wk | d_tot | d_dd | d_ww |
|---|---|---|---|---|---|---|---|---|---|
| JN05W2 | 4,169 | 7,741 | 660,702 | 632,370 | 52,233 | -36,371 | 0 | 0 | 0 |
| TL3_AL_S15 | 4,117 | 7,657 | 700,844 | 672,819 | 64,213 | -38,849 | 40,142 | 11,980 | -2,478 |
| TL3_AL_S60 | 4,117 | 7,642 | 656,187 | 628,217 | 60,996 | -40,406 | -4,515 | 8,763 | -4,035 |
| TL3_AL_S120 | 4,177 | 7,783 | 707,322 | 678,836 | 64,924 | -48,981 | 46,620 | 12,691 | -12,611 |
| TL3_AL_H60 | 4,191 | 7,289 | 649,588 | 622,911 | 52,999 | -36,053 | -11,114 | 766 | 318 |
| TL3_AL_H120 | 4,224 | 7,210 | 645,185 | 618,797 | 51,621 | -33,660 | -15,517 | -612 | 2,711 |
| TL3_AL_T60 | 4,015 | 7,465 | 646,985 | 619,663 | 59,574 | -42,974 | -13,717 | 7,341 | -6,604 |
| TL3_AL_PL120 | 4,116 | 7,773 | 582,318 | 553,868 | 68,945 | -52,300 | -78,384 | 16,712 | -15,930 |
| TL3_AL_PL15_11 | 4,052 | 7,700 | 688,385 | 660,203 | 45,149 | -31,301 | 27,684 | -7,084 | 5,070 |
| TL3_AL_PL15_12 | 4,122 | 7,809 | 625,769 | 597,188 | 57,890 | -41,243 | -34,932 | 5,657 | -4,872 |
| TL3_AL_PL15_13 | 4,162 | 7,805 | 635,902 | 607,336 | 52,242 | -35,752 | -24,800 | 8 | 619 |
| TL3_AL_PL15_14 | 4,126 | 7,771 | 746,242 | 717,800 | 63,142 | -47,676 | 85,540 | 10,909 | -11,305 |
| TL3_AL_PL120_11 | 4,054 | 7,686 | 694,454 | 666,323 | 49,499 | -30,796 | 33,752 | -2,735 | 5,575 |
| TL3_AL_PL120_12 | 4,031 | 7,664 | 581,769 | 553,719 | 41,785 | -24,571 | -78,932 | -10,448 | 11,799 |
| TL3_AL_PL120_13 | 4,066 | 7,639 | 570,930 | 542,972 | 57,832 | -40,156 | -89,771 | 5,599 | -3,786 |
| TL3_AL_PL120_14 | 4,109 | 7,722 | 736,195 | 707,932 | 60,747 | -41,838 | 75,493 | 8,514 | -5,468 |

- S15: change in 6-month total vs JN05W2 +40,142; 4 placebos (same size table, forecast shuffled within book and month) give +13,373 on average, sd 55,388, range -34,932..+85,540; max drawdown change +11,980 vs placebo mean +2,372 sd 7,717. z of real vs placebo = +0.48.
- S120: change in 6-month total vs JN05W2 +46,620; 5 placebos (same size table, forecast shuffled within book and month) give -27,569 on average, sd 76,602, range -89,771..+75,493; max drawdown change +12,691 vs placebo mean +3,528 sd 10,459. z of real vs placebo = +0.97.
- KEY FINDING for every sizing test: any re-sizing of the stack, even a meaningless one, moves the 6-month engine total by roughly +-$55-75k (sd, on a $660k base) and max drawdown by +-$8-10k through path effects (locks, caps, day-done rules). A forecast-sized book has to beat that placebo spread, not just the base; with this first-pass forecast it does not (z below 1). Sizing by forecast is NOT shown to help.
(LOT BASIS: base lots JN05W2, live x1.75, engine fee $1.18/contract vs FEES.md $4.84: column tot484 carries $4.84; live caps P7 14,700 vs engine 8,400.)

## 7. Honest summary: what we have, where it comes from, what would raise it
- We have: NQ combined-forecast IC about +0.010 at 5 min (t ~4.6) and +0.008-0.012 at 15 min on a pooled basis, +0.02 in Asia at 5-30 min (t 2-6); about 0 beyond 30 min. This is at the low edge of the 0.01-0.03 the user calls normal for one market.
- It comes from: short-term reversal and ES/YM-relative moves at 1-15 min in thin hours (the best single inputs are ret3, ret5, dist_ema20, rel_es5: all negative IC). That is a microstructure/mean-reversion effect, i.e. it is exactly the kind of edge that spread, fees and slippage consume at market execution.
- What did NOT help: the 2,393 CF4 indicators, CF5 calendar/session, CF6 counting/ICT/analog, L2 and L3 reps (on the selection-window stability criterion) added no IC beyond price once walk-forward and nonsense are applied; GBM and MLP are not better than ridge (low signal to noise: regularised linear wins).
- What would raise it: (1) breadth, the same pipeline across many markets (W-AL2) since a 0.01 IC across 10+ independent markets compounds like sqrt(N); (2) forecast horizons that match what D7 holds (minutes to 14 hours: 240/480-min targets not built yet); (3) passive execution so the 5-min reversal is not paid for at market; (4) the options/macro/positioning block (feat1m J_*, B15_*), not yet in this pass; (5) 1-min instead of 5-min decisions in Asia where the 5-min edge is strongest; (6) news/event-time conditioning.

## 8. Files
code/th_alpha/*.py; bulk /mnt/l2/l2vast/_alpha (panels, X_*.parquet feature blocks, Y_NQ.parquet, runs/*_pred.parquet and *_ic.csv, tables/ per-signal forecast tables, engine_part2_v1.csv, audit_v1.json, lookahead_univariate.csv).
