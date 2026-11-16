# DS3_ALPHA - one combined forecast for NQ (W-AL1, T-ALPHA parts 1, 2, 4-NQ)

VERDICT (data ends 2026-10-30; FIRST PASS, NQ, test span 2023-10..2026-10-16 for the full feature set, 2023-04..2026-10-30 for price/intermarket/clock): the combined NQ forecast has a small real information coefficient at 5-15 minutes (average of ridge/GBM/MLP: IC +0.0103 at 5 min t +4.6, +0.0083 at 15 min t +2.5) that is carried by price and intermarket reversal in the thin hours (Asia), the same 200-input nonsense pipeline gives -0.0001 / -0.0018; at 30-120 min the IC (+0.0055 at 60 min) is not distinguishable from the nonsense null; the ~400 library/L2/L3/counting inputs add nothing over the 90 price/intermarket/clock inputs; on D7 (exact engine, L6M) the forecast as size, as half-size against re-entries, as target multiplier and as its own book are all within the spread of shuffled-forecast / random-side placebos (placebo sd about $55-75k per 6 months), so nothing is shown to help and nothing is recommended for live. Numbers are FIRST PASS, one run per cell.

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


- JOINT shift test of the full input set (ridge; all ~400 inputs shifted together by one decision step): IC at 5/15/30/60/120 min as built / inputs one step OLDER / inputs one step NEWER (future):
  - lag_0: +0.0112, +0.0052, +0.0050, +0.0058, +0.0097
  - lag_m1: +0.0018, +0.0039, +0.0015, +0.0034, +0.0089
  - lag_p1: +0.9499, +0.5130, +0.3600, +0.2455, +0.1608
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

## 3d. Longer horizons (AL-H6): 240 min, 480 min and return-to-session-close (>=20 min left), for D7 holds of hours
Same pipeline and walk-forward (test 2023-04-03..2026-10-30 for price/intermarket/clock = L_core; 2023-10-02..2026-10-16 for the full input set = L_full). Targets stay inside one trading day (no halt/weekend crossing), so 480-min targets exist for about 65% of decisions. Column c = session close. IC (t) | nonsense null where run.

| run | slice | 240 | 480 | c |
|---|---|---|---|
| core avg | all | -0.0046 (t -0.4) | -0.0110 (t -0.6) | +0.0080 (t +0.7) |
| core avg | sess_asia | -0.0021 (t -0.1) | -0.0089 (t -0.4) | -0.0104 (t -0.4) |
| core avg | sess_london | -0.0276 (t -1.4) | -0.0137 (t -0.5) | -0.0148 (t -0.7) |
| core avg | sess_nyam | +0.0410 (t +1.6) | +nan (t +nan) | +0.0279 (t +1.3) |
| core avg | sess_nypm | +0.0366 (t +1.2) | +nan (t +nan) | +0.0101 (t +0.4) |
| core avg | recent_since_2026-05 | +0.0298 (t +0.9) | +0.0359 (t +0.7) | -0.0461 (t -1.6) |

## 4. Which data carries it (block ablation)
IC of the ridge+GBM average with ONE BLOCK REMOVED (abl_<block>) or with ONLY that block (only_<block>), all sessions; blocks: price, inter (intermarket), clock, cf4ind (indicator library), cf5cal (calendar/session), l2, l3, cf6 (counting/ICT/analog). Share surviving = ablated IC / reference IC.

| run | 5m | 15m | 30m | 60m | 120m |
|---|---|---|---|---|---|
| abl_cf4ind | +0.0119 | +0.0095 | +0.0055 | +0.0037 | -0.0009 |
| abl_clock | +0.0111 | +0.0088 | +0.0055 | +0.0060 | +0.0054 |
| abl_inter | +0.0123 | +0.0106 | +0.0055 | +0.0047 | +0.0022 |
| abl_l2 | +0.0127 | +0.0081 | +0.0051 | +0.0040 | +0.0039 |
| abl_l3 | +0.0121 | +0.0103 | +0.0046 | +0.0046 | +0.0041 |
| abl_price | +0.0102 | +0.0091 | +0.0049 | +0.0067 | +0.0066 |
| REFERENCE full set (ridge+GBM avg) | +0.0115 | +0.0102 | +0.0040 | +0.0033 | +0.0007 |

Asia only:

| run | 5m | 15m | 30m | 60m | 120m |
|---|---|---|---|---|---|
| abl_cf4ind | +0.0251 | +0.0316 | +0.0238 | +0.0202 | +0.0092 |
| abl_clock | +0.0228 | +0.0277 | +0.0198 | +0.0165 | +0.0181 |
| abl_inter | +0.0229 | +0.0280 | +0.0153 | +0.0146 | +0.0100 |
| abl_l2 | +0.0228 | +0.0219 | +0.0133 | +0.0126 | +0.0077 |
| abl_l3 | +0.0228 | +0.0274 | +0.0189 | +0.0120 | +0.0065 |
| abl_price | +0.0201 | +0.0254 | +0.0195 | +0.0215 | +0.0115 |
| REFERENCE full set (ridge+GBM avg) | +0.0232 | +0.0268 | +0.0157 | +0.0142 | +0.0054 |

Share of the reference IC surviving after removing the block (n/a where the reference IC is below 0.003):

| block removed | 5m | 15m | 30m | 60m | 120m |
|---|---|---|---|---|---|
| abl_cf4ind | 104% | 94% | 137% | 111% | n/a |
| abl_clock | 96% | 87% | 138% | 180% | n/a |
| abl_inter | 107% | 104% | 138% | 141% | n/a |
| abl_l2 | 111% | 79% | 128% | 121% | n/a |
| abl_l3 | 106% | 101% | 115% | 139% | n/a |
| abl_price | 89% | 90% | 124% | 203% | n/a |


Reading: no single block is necessary. Removing price, intermarket, clock or L2 leaves 80-110% of the 5-15 min IC (above 100% means the block was adding noise), because the short-term reversal information is redundant across blocks (the indicator library and intermarket inputs carry the same recent-return information as the price block). The IC is therefore a property of recent price action itself, not of L2, L3, options or the counting libraries; L3, CF6, CF4 and CF5 ablations follow in this section as they finish.
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

## 5b. Small-size items (user addendum A): micros, the 17:00-18:00 ET halt, holiday sessions, passive entries
IC of the core forecast (price+intermarket+clock, 2023-04..2026-10-30) in time windows around the halt and on early-close/holiday trading days (13:00 ET closes: Presidents Day, Memorial, Juneteenth, Independence, Labor, Thanksgiving Friday, Christmas Eve ...; 33 such days in the test span, so low power):

| window | 5m | 15m | 60m |
|---|---|---|---|
| 15:00-16:30 ET | -0.0005 (t -0.1, n 16,002, 889 d) | -0.0096 (t -0.8, n 16,002, 889 d) | -0.0525 (t -2.0, n 11,557, 889 d) |
| 18:30-20:00 ET | +0.0249 (t +3.1, n 16,668, 926 d) | +0.0074 (t +0.6, n 16,666, 926 d) | +0.0116 (t +0.6, n 16,657, 926 d) |
| all | +0.0106 (t +5.2, n 253,586, 927 d) | +0.0120 (t +3.7, n 251,732, 927 d) | +0.0076 (t +1.3, n 243,389, 927 d) |
| early-close / holiday trading days (76 days) | +0.0316 (t +2.8, n 7,419, 33 d) | -0.0071 (t -0.4, n 7,351, 33 d) | +0.0332 (t +1.1, n 7,045, 33 d) |
| first 30 min after the 18:00 ET reopen | +0.0230 (t +1.8, n 5,555, 926 d) | +0.0297 (t +1.7, n 5,555, 926 d) | +0.0318 (t +1.4, n 5,555, 926 d) |
| last 30 min before the 17:00 halt | +0.0048 (t +0.4, n 5,334, 889 d) | +0.0303 (t +1.2, n 3,556, 889 d) |  |

Reading: the first 30 minutes after the 18:00 ET reopen and 18:30-20:00 ET carry the same or stronger 5-min IC (0.023-0.025, t 1.8-3.1); the last 30 minutes before the halt are noise; 15:00-16:30 ET is zero to negative at 60 min (-0.05, t -2); early-close days: 5-min IC +0.032 (t 2.8) on only 33 days, not enough to say more.
Micros (MNQ: $2/pt, $1.78 RT fee per FEES.md, same 0.23 pt slippage, same lots count so $ are 1/10 of NQ): cost/gross is about 2x worse than NQ because the fee is a larger fraction of a $2 point: 15-min forecast cost/gross 0.55 (NQ) vs 1.08 (MNQ); 120-min Asia 0.51 vs 0.98. Micro market orders do not keep the edge; micros only work with passive entry and exit.

| h | session | instrument | gross_per_day | cost_per_day | net_per_day | cost_over_gross |
|---|---|---|---|---|---|---|
| 15 | all | NQ | 412.37 | 231.76 | 180.61 | 0.56 |
| 15 | all | MNQ | 41.24 | 44.57 | -3.33 | 1.08 |
| 15 | asia | NQ | 407.99 | 222.96 | 185.03 | 0.55 |
| 15 | asia | MNQ | 40.80 | 42.88 | -2.08 | 1.05 |
| 120 | all | NQ | 457.48 | 138.01 | 319.47 | 0.30 |
| 120 | all | MNQ | 45.75 | 26.54 | 19.21 | 0.58 |
| 120 | asia | NQ | 309.04 | 157.42 | 151.62 | 0.51 |
| 120 | asia | MNQ | 30.90 | 30.27 | 0.63 | 0.98 |

Passive entry for the Asia 5-min reversal (2,317 Asia decisions with |z5| >= 2, 2023-04..2026-10, per-second NQ tape and touch sizes; rest one order at the touch at the decision second, queue ahead = touch size, filled when the aggressor volume against us at an unchanged touch reaches the queue, or when the market trades through; cancel after N seconds; points, entry-side only; exit assumed at the 5-min mid for both so the comparison is entry-only). Mean touch spread in Asia is 1.18 pt; the signed 5-min mid move after the signal is +1.03 pt per decision; crossing the touch (market) keeps +0.44 pt; resting keeps +0.54..+0.62 pt per decision (fills 73% at 10 s, 82% at 30 s, 87% at 60 s). Adverse selection is visible: unfilled orders are the ones that moved +3 to +10 pt in our direction.

| N_sec | fill_rate | edge_pts_filled | uncond_move_of_filled | uncond_move_of_unfilled | edge_pts_per_decision | mkt_edge_pts_per_decision | n |
|---|---|---|---|---|---|---|---|
| 10 | 0.727 | 0.745 | 0.178 | 3.308 | 0.542 | 0.443 | 2317.000 |
| 30 | 0.820 | 0.752 | 0.185 | 4.880 | 0.616 | 0.443 | 2317.000 |
| 60 | 0.868 | 0.676 | 0.109 | 7.118 | 0.587 | 0.443 | 2317.000 |
| 120 | 0.903 | 0.646 | 0.077 | 9.951 | 0.583 | 0.443 | 2317.000 |

Minus the $4.84 fee (0.24 pt) the passive version nets about +0.3..+0.4 pt per decision (about $7 per NQ contract per trade, about 2.5 trades per day = under $20 per day per contract): real but small; it is not a standalone book, and queue-position uncertainty (cancels ahead ignored = conservative; hidden size = optimistic) is the main error. Capacity: 1-3 NQ lots at the touch (touch size 1-70 contracts, median in Asia about 10).
## 6. Part 2 - forecast on D7 (exact engine, tag AL, JN05W2 base lots, L6M = 2026-05..2026-10, every signal evaluated, none skipped)
Forecast used: core (price+intermarket+clock) avg_h from the walk-forward, mapped to each signal second (last 5-min decision <= signal second), a = side x z. Sets: S15/S60/S120 = size m = clip(1+0.35a, 0.5, 1.5) renormalised to mean 1; H60/H120 = half size when a < -0.5; T60 = target distance x clip(1+0.25a, 0.75, 1.25); PL120 and PLxx_n = same size table as S with the forecast SHUFFLED within book and month (placebo). Identity proven: TL3_AL_ID reproduces 598 trades / 25,943.82 on 202610.

| set | n | lots | tot | tot484 | maxdd | worst_wk | d_tot | d_dd | d_ww | wk175 |
|---|---|---|---|---|---|---|---|---|---|---|
| JN05W2 | 4,169 | 7,741 | 660,702 | 632,370 | 52,233 | -36,371 | 0 | 0 | 0 | 42,823 |
| TL3_AL_S15 | 4,117 | 7,657 | 700,844 | 672,819 | 64,213 | -38,849 | 40,142 | 11,980 | -2,478 | 45,425 |
| TL3_AL_S60 | 4,117 | 7,642 | 656,187 | 628,217 | 60,996 | -40,406 | -4,515 | 8,763 | -4,035 | 42,531 |
| TL3_AL_S120 | 4,177 | 7,783 | 707,322 | 678,836 | 64,924 | -48,981 | 46,620 | 12,691 | -12,611 | 45,845 |
| TL3_AL_H60 | 4,191 | 7,289 | 649,588 | 622,911 | 52,999 | -36,053 | -11,114 | 766 | 318 | 42,103 |
| TL3_AL_H120 | 4,224 | 7,210 | 645,185 | 618,797 | 51,621 | -33,660 | -15,517 | -612 | 2,711 | 41,818 |
| TL3_AL_T60 | 4,015 | 7,465 | 646,985 | 619,663 | 59,574 | -42,974 | -13,717 | 7,341 | -6,604 | 41,934 |
| TL3_AL_PL120 | 4,116 | 7,773 | 582,318 | 553,868 | 68,945 | -52,300 | -78,384 | 16,712 | -15,930 | 37,743 |
| TL3_AL_PL15_11 | 4,052 | 7,700 | 688,385 | 660,203 | 45,149 | -31,301 | 27,684 | -7,084 | 5,070 | 44,618 |
| TL3_AL_PL15_12 | 4,122 | 7,809 | 625,769 | 597,188 | 57,890 | -41,243 | -34,932 | 5,657 | -4,872 | 40,559 |
| TL3_AL_PL15_13 | 4,162 | 7,805 | 635,902 | 607,336 | 52,242 | -35,752 | -24,800 | 8 | 619 | 41,216 |
| TL3_AL_PL15_14 | 4,126 | 7,771 | 746,242 | 717,800 | 63,142 | -47,676 | 85,540 | 10,909 | -11,305 | 48,368 |
| TL3_AL_PL120_11 | 4,054 | 7,686 | 694,454 | 666,323 | 49,499 | -30,796 | 33,752 | -2,735 | 5,575 | 45,011 |
| TL3_AL_PL120_12 | 4,031 | 7,664 | 581,769 | 553,719 | 41,785 | -24,571 | -78,932 | -10,448 | 11,799 | 37,707 |
| TL3_AL_PL120_13 | 4,066 | 7,639 | 570,930 | 542,972 | 57,832 | -40,156 | -89,771 | 5,599 | -3,786 | 37,005 |
| TL3_AL_PL120_14 | 4,109 | 7,722 | 736,195 | 707,932 | 60,747 | -41,838 | 75,493 | 8,514 | -5,468 | 47,716 |
| TL3_AL_R1_60 | 4,182 | 7,473 | 683,812 | 656,461 | 53,091 | -32,644 | 23,110 | 858 | 3,727 | 44,321 |
| TL3_AL_R2_60 | 4,218 | 7,431 | 646,471 | 619,273 | 57,017 | -38,447 | -14,231 | 4,784 | -2,076 | 41,901 |
| TL3_AL_RB_60 | 4,213 | 7,330 | 645,072 | 618,244 | 58,134 | -38,041 | -15,630 | 5,901 | -1,670 | 41,810 |
| TL3_AL_RP1_21 | 4,170 | 7,469 | 585,077 | 557,741 | 48,688 | -34,659 | -75,624 | -3,545 | 1,712 | 37,922 |
| TL3_AL_RP1_22 | 4,179 | 7,483 | 610,144 | 582,756 | 63,252 | -43,553 | -50,558 | 11,019 | -7,183 | 39,546 |
| TL3_AL_RP1_23 | 4,154 | 7,467 | 661,732 | 634,403 | 43,629 | -30,545 | 1,030 | -8,604 | 5,825 | 42,890 |
| TL3_AL_RB_P21 | 4,207 | 7,331 | 598,738 | 571,906 | 51,396 | -34,316 | -61,964 | -837 | 2,055 | 38,807 |
| TL3_AL_RB_P22 | 4,173 | 7,328 | 613,791 | 586,970 | 53,942 | -35,408 | -46,911 | 1,709 | 963 | 39,783 |
| TL3_AL_RB_P23 | 4,188 | 7,333 | 620,643 | 593,804 | 49,867 | -33,008 | -40,059 | -2,367 | 3,362 | 40,227 |

- S15: change in 6-month total vs JN05W2 +40,142; 4 placebos (same size table, forecast shuffled within book and month) give +13,373 on average, sd 55,388, range -34,932..+85,540; max drawdown change +11,980 vs placebo mean +2,372 sd 7,717. z of real vs placebo = +0.48.
- S120: change in 6-month total vs JN05W2 +46,620; 5 placebos (same size table, forecast shuffled within book and month) give -27,569 on average, sd 76,602, range -89,771..+75,493; max drawdown change +12,691 vs placebo mean +3,528 sd 10,459. z of real vs placebo = +0.97.
- R1_60: change in 6-month total vs JN05W2 +23,110; 3 placebos (same size table, forecast shuffled within book and month) give -41,717 on average, sd 39,084, range -75,624..+1,030; max drawdown change +858 vs placebo mean -377 sd 10,188. z of real vs placebo = +1.66.
- RB_60: change in 6-month total vs JN05W2 -15,630; 3 placebos (same size table, forecast shuffled within book and month) give -49,645 on average, sd 11,205, range -61,964..-40,059; max drawdown change +5,901 vs placebo mean -498 sd 2,059. z of real vs placebo = +3.04.
- KEY FINDING for every sizing test: any re-sizing of the stack, even a meaningless one, moves the 6-month engine total by roughly +-$55-75k (sd, on a $660k base) and max drawdown by +-$8-10k through path effects (locks, caps, day-done rules). A forecast-sized book has to beat that placebo spread, not just the base; with this first-pass forecast it does not (z below 1). Sizing by forecast is NOT shown to help.

### 6b. Fault 1 (re-entry against the trend) - forecast defines "trend has turned against this book"
Definition: a = side x z of the walk-forward forecast (60 or 120 min) at the signal; R1 = a prior same-side LOSING trade (any book) closed earlier in the same session instance AND a < -0.5; R2 = two or more prior same-side losers in the session AND a < 0. Action is SIZE (x0.5), never skip. First-order on the 43-month taken trades (signals_all pnl, 20 worst Globex weeks of the post-mortem definition), placebo = same number of random taken trades within book x month (300 draws):

| rule | n | n_worst | pnl_flag_in_worst | pnl_flag_elsewhere | pnl_flag_all | placebo_in_worst_mean | z_vs_placebo |
|---|---|---|---|---|---|---|---|
| against forecast a60<-0.5 | 5,019 | 602 | -124,056 | 532,410 | 408,354 | -184,741 | 1 |
| R1: prior same-side loser in session and a60<-0.5 | 1,882 | 243 | -46,259 | 190,628 | 144,369 | -70,407 | 1 |
| R2: 2+ prior same-side losers in session and a60<0 | 1,731 | 237 | 2,552 | 262,513 | 265,066 | -65,205 | 2 |
| against forecast a120<-0.5 | 5,399 | 622 | -95,609 | 630,862 | 535,252 | -198,794 | 2 |
| R1: prior same-side loser in session and a120<-0.5 | 2,069 | 256 | -20,331 | 273,716 | 253,385 | -75,811 | 2 |
| R2: 2+ prior same-side losers in session and a120<0 | 1,808 | 247 | -18,557 | 315,757 | 297,200 | -67,739 | 2 |

Reading: the flagged trades lose LESS than random trades inside the 20 worst weeks (positive z = flagged are better than the placebo there) and are net positive over the whole history, so halving them would give up profit and would not remove the worst-week loss. The forecast does not identify the re-entries that hurt. Exact-engine size cells R1_60 / R2_60 / RB_60 (union) and their forecast-shuffled placebos are in the table above.

### 6c. The forecast as its own book (item 9): injection hook uw_inject, tag AL1, flat at session end, 2 lots, stop 40 pts (AB1: 120-min forecast |z|>=2, all sessions, first trigger per session) / 30 pts (AB2: 15-min forecast |z|>=2.5, Asia+London), market entry, engine fills, $1.18 fee; L6M. RS = same entry times with RANDOM sides (placebo). corr = correlation of daily P&L of the AL1 book with the daily P&L of the live JN05W2 stack; stack changes are the whole-stack change when the book is added.

| book | n | lots | net | net_per_trade | win | corr_daily_vs_stack | stack_tot_change | stack_dd_change | worst_wk_change |
|---|---|---|---|---|---|---|---|---|---|
| AB1 | 178.00 | 337.00 | 47,177.34 | 265.04 | 0.47 | 0.27 | 55,440.42 | -2,100.94 | 9,574.14 |
| AB2 | 93.00 | 178.00 | -9,090.04 | -97.74 | 0.32 | 0.15 | -44,833.94 | 2,416.22 | -2,416.22 |
| AB1_RS1 | 190.00 | 366.00 | 37,958.12 | 199.78 | 0.44 | 0.16 | 28,141.18 | -5,788.90 | 1,411.22 |
| AB1_RS2 | 170.00 | 324.00 | 55,352.68 | 325.60 | 0.49 | 0.22 | 53,329.88 | -1,672.04 | 862.68 |
| AB2_RS1 | 90.00 | 177.00 | 4,206.14 | 46.73 | 0.42 | 0.03 | -24,621.98 | -5,197.60 | 5,197.60 |
| AB2_RS2 | 90.00 | 176.00 | 17,067.32 | 189.64 | 0.47 | 0.20 | -4,551.22 | -2,837.60 | 2,837.60 |

Reading: the real-side book AB1 earns about the same as its random-side twins (AB1_RS1/RS2), so the P&L is exposure/drift timing in this 6-month window, not forecast skill; AB2 (the strongest short-horizon edge, Asia) loses or is flat and is not separable from random sides either. Correlation with the live stack is low (0.0-0.3), so such a book would diversify, but there is nothing here yet worth adding. No PASS claim.
LIVE-CAP FRAMING: every dollar figure in this section (tot, tot484, maxdd, worst_wk, d_tot, d_dd, d_ww) is at BASE lots of JN05W2 (engine P7 cap 8,400). Live is x1.75 (P7 14,700): multiply each dollar column by 1.75 (live 6-month JN05W2 total $660,702 base = $1,156,229 live-scaled; max drawdown $52,233 = $91,408; worst week -$36,371 = -$63,649; the placebo sd of $55-75k per 6 months becomes $96-131k); wk175 = live-scaled average weekly total. Ratios and z-scores are unchanged by the scaling.
(LOT BASIS: base lots JN05W2, live x1.75, engine fee $1.18/contract vs FEES.md $4.84: column tot484 carries $4.84; live caps P7 14,700 vs engine 8,400.)

## 7. Honest summary: what we have, where it comes from, what would raise it
- We have: NQ combined-forecast IC about +0.010 at 5 min (t ~4.6) and +0.008-0.012 at 15 min on a pooled basis, +0.02 in Asia at 5-30 min (t 2-6); about 0 beyond 30 min. This is at the low edge of the 0.01-0.03 the user calls normal for one market.
- It comes from: short-term reversal and ES/YM-relative moves at 1-15 min in thin hours (the best single inputs are ret3, ret5, dist_ema20, rel_es5: all negative IC). That is a microstructure/mean-reversion effect, i.e. it is exactly the kind of edge that spread, fees and slippage consume at market execution.
- What did NOT help: the 2,393 CF4 indicators, CF5 calendar/session, CF6 counting/ICT/analog, L2 and L3 reps (on the selection-window stability criterion) added no IC beyond price once walk-forward and nonsense are applied; GBM and MLP are not better than ridge (low signal to noise: regularised linear wins).
- What would raise it: (1) breadth, the same pipeline across many markets (W-AL2) since a 0.01 IC across 10+ independent markets compounds like sqrt(N); (2) forecast horizons that match what D7 holds (minutes to 14 hours: 240/480-min targets not built yet); (3) passive execution so the 5-min reversal is not paid for at market; (4) the options/macro/positioning block (feat1m J_*, B15_*), not yet in this pass; (5) 1-min instead of 5-min decisions in Asia where the 5-min edge is strongest; (6) news/event-time conditioning.

## 8. Files
code/th_alpha/*.py; bulk /mnt/l2/l2vast/_alpha (panels, X_*.parquet feature blocks, Y_NQ.parquet, runs/*_pred.parquet and *_ic.csv, tables/ per-signal forecast tables, engine_part2_v1.csv, audit_v1.json, lookahead_univariate.csv).
