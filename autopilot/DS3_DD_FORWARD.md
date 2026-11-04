# DS3_DD_FORWARD - forward drawdown distribution and time under water of the live stack (DIS-Z3R, Z3, 2026-11-05)
Measurement for a risk-appetite statement, not a hypothesis test. No PASS claims, nothing live. Prereg l2vast/ds3/prereg/DIS_Z3R_prereg.md sha256 19e1d8336f0607105e7d9d9b032a7f3c2055f1fdf62634796501d4b56629d2f7 (DECISIONS.md, before any DIS-Z3R number; registered in MORNING.md before starting). Code l2vast/ds3/code/dis_z3r/ (z3r_series.py, z3r_run.py); data l2vast/ds3/out/dis_z3r/. Series: BASE-4 run_v13t_ts2 (Q1-A, live lock) daily P&L, 935 days / 187 weeks (2023-04..2026-10), engine re-runs for lot scales 0.5 / 1.5 / 2.0 (integer lots re-rounded, not linear). Method: stationary block bootstrap of days (mean block 10, sensitivity 5 / 20), 20,000 paths per cell, horizons 13 / 26 / 52 / 104 weeks; maxDD = peak-to-trough of the weekly cumulative path from 0; time under water = longest run of weeks without a new equity high.

## Plain sentences
1. If the 3.5-year record is representative (E1), a year at live lots has a median maxDD of $100k and a 95th percentile of $186k: the observed HOLD depth ($122.0k) is reached or exceeded in 29% of simulated years (6% of 13-week windows, 15% of 26-week, 52% of 104-week windows), $200k in 3.4% of years and $300k in 0.2%; the in-sample $122.0k is a typical, not an extreme, depth for a year.
2. Time under water is long even when things go well: the median longest spell without a new equity high is 10 weeks in a year (95th percentile 25 weeks, observed 11 weeks), and in 59% of simulated years the stack ends the year below its high.
3. If the edge is half of the sample's (E2) the year's median maxDD is $152k, P(>= $200k) = 26%, P(a losing year) = 10%; if the edge is gone (E3, zero mean) the median year has a $266k maxDD, P(>= $300k) = 40%, 53% of years lose money and the median longest spell is 34 weeks (95th percentile 52).
4. Lot scale moves all of this roughly proportionally: x0.5 gives a median year maxDD of $59k (P(>= $122k) = 3%), x1.5 gives $160k (P(>= $200k) = 27%), x2.0 gives $198k (P(>= $300k) = 13%); the observed in-sample maxDD is $84k / $122k / $213k / $245k at x0.5 / x1 / x1.5 / x2.
5. Calibration (fit on 2023-04..2024-12, predict the next 95 weeks): the realised maxDD ($122.0k) sat at the 55th-73rd percentile of the predicted distribution, the realised worst week (-$62.6k) was worse than 86-95% of simulated worst weeks, the realised longest spell (9 weeks) was longer than only 6-7% of simulations, and the realised total P&L ($1.71M) beat all 20,000 simulated paths: the model under-predicted the edge of 2025-26, not the depth of its drawdowns, and the worst week was harsher than the model.
6. Not in this distribution: a gap through the stops (DS3_TAIL_STRESS: SYNTHETIC $0.3M-$1.8M at 18 lots) or an outage with non-resting stops (DS3_OUTAGE): the bootstrap contains only the days that happened.

## 1. In-sample facts (weekly cumulative, harness week key, by lot scale)
| scale | maxDD | worst week | longest time under water (weeks) | drawdown episodes >= $60k | >= $100k | three deepest episodes (depth, ISO week of the peak, weeks to recover) |
|---|---|---|---|---|---|---|
| 0.5 | $84k | $-43k | 12 | 2 | 0 | $84k (wk 202630, 10 wk), $74k (wk 202606, 10 wk), $53k (wk 202528, 3 wk) |
| 1.0 | $122k | $-63k | 11 | 8 | 2 | $122k (wk 202606, 8 wk), $105k (wk 202630, 9 wk), $88k (wk 202506, 8 wk) |
| 1.5 | $213k | $-105k | 11 | 12 | 7 | $213k (wk 202630, 10 wk), $194k (wk 202606, 8 wk), $135k (wk 202506, 8 wk) |
| 2.0 | $245k | $-126k | 11 | 13 | 9 | $245k (wk 202606, 8 wk), $201k (wk 202630, 9 wk), $177k (wk 202506, 8 wk) |
At the end of the sample the stack is below its high at all scales (week 187 is 1 week from the last high).

## 2. Scale 1.0, block 10: forward distribution by scenario and horizon
E1 = the sample as is; E2 = mean shrunk to 50%; E3 = ZERO edge (mean removed); E4 = resample only 2024-01..2026-10. P(...) are shares of 20,000 paths (Monte Carlo SE <= 0.4 points; parameter uncertainty is only in the E2 / E3 scenarios and the block sensitivity).
| scenario | weeks | maxDD p50 | p90 | p95 | p99 | P(>= 100k) | P(>= 122k) | P(>= 200k) | P(>= 300k) | P(year-end P&L < 0) | longest underwater p50 / p95 (weeks) | P(below the high at the end) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E1 sample | 13 | $55k | $108k | $127k | $173k | 12.9% | 6.0% | 0.3% | 0.0% | 8.7% | 4 / 11 | 58.7% |
| E1 sample | 26 | $76k | $134k | $157k | $209k | 27.1% | 14.6% | 1.4% | 0.1% | 2.5% | 7 / 17 | 58.8% |
| E1 sample | 52 | $100k | $161k | $186k | $244k | 49.9% | 29.3% | 3.4% | 0.2% | 0.2% | 10 / 25 | 58.5% |
| E1 sample | 104 | $123k | $189k | $216k | $278k | 75.6% | 52.2% | 7.5% | 0.6% | 0.0% | 14 / 32 | 58.7% |
| E2 half edge | 13 | $76k | $148k | $174k | $232k | 31.2% | 18.8% | 2.5% | 0.1% | 27.3% | 6 / 13 | 73.1% |
| E2 half edge | 26 | $111k | $200k | $235k | $312k | 58.9% | 42.1% | 9.9% | 1.3% | 18.7% | 11 / 25 | 76.5% |
| E2 half edge | 52 | $152k | $264k | $310k | $400k | 85.0% | 70.8% | 25.8% | 5.8% | 10.0% | 18 / 45 | 77.9% |
| E2 half edge | 104 | $197k | $326k | $380k | $492k | 98.0% | 92.2% | 48.6% | 14.0% | 3.3% | 29 / 74 | 78.6% |
| E3 zero edge | 13 | $109k | $207k | $239k | $297k | 56.4% | 42.1% | 11.5% | 0.9% | 53.1% | 9 / 13 | 86.2% |
| E3 zero edge | 26 | $174k | $311k | $356k | $445k | 86.1% | 75.6% | 39.4% | 11.7% | 53.6% | 17 / 26 | 90.3% |
| E3 zero edge | 52 | $266k | $471k | $539k | $667k | 98.3% | 95.2% | 72.0% | 39.9% | 52.8% | 34 / 52 | 93.1% |
| E3 zero edge | 104 | $395k | $687k | $785k | $981k | 100.0% | 99.8% | 94.3% | 73.2% | 51.5% | 68 / 104 | 95.1% |
| E4 recent 2024+ | 13 | $54k | $105k | $124k | $166k | 11.5% | 5.6% | 0.3% | 0.0% | 5.4% | 4 / 10 | 52.6% |
| E4 recent 2024+ | 26 | $74k | $130k | $149k | $200k | 25.1% | 12.9% | 1.0% | 0.0% | 1.0% | 6 / 15 | 53.0% |
| E4 recent 2024+ | 52 | $97k | $155k | $177k | $229k | 46.5% | 27.0% | 2.5% | 0.1% | 0.0% | 8 / 20 | 53.0% |
| E4 recent 2024+ | 104 | $119k | $178k | $201k | $258k | 71.5% | 46.5% | 5.1% | 0.3% | 0.0% | 12 / 25 | 53.2% |

## 3. Lot-scale sensitivity at 52 weeks (block 10)
E1 (sample as is):
| scale | maxDD p50 | p95 | p99 | P(>= 100k) | P(>= 122k) | P(>= 200k) | P(>= 300k) | P(P&L < 0) |
|---|---|---|---|---|---|---|---|---|
| 0.5 | $59k | $112k | $145k | 8.9% | 3.2% | 0.1% | 0.0% | 0.4% |
| 1.0 | $100k | $186k | $244k | 49.9% | 29.3% | 3.4% | 0.2% | 0.2% |
| 1.5 | $160k | $298k | $387k | 89.3% | 75.8% | 27.0% | 4.8% | 0.3% |
| 2.0 | $198k | $370k | $480k | 96.9% | 90.3% | 49.0% | 13.2% | 0.2% |
E3 (zero edge):
| scale | maxDD p50 | p95 | p99 | P(>= 100k) | P(>= 122k) | P(>= 200k) | P(>= 300k) | P(P&L < 0) |
|---|---|---|---|---|---|---|---|---|
| 0.5 | $146k | $299k | $374k | 79.0% | 64.9% | 25.5% | 4.9% | 51.3% |
| 1.0 | $266k | $539k | $667k | 98.3% | 95.2% | 72.0% | 39.9% | 52.8% |
| 1.5 | $408k | $833k | $1031k | 100.0% | 99.6% | 93.8% | 74.1% | 52.2% |
| 2.0 | $526k | $1064k | $1330k | 100.0% | 100.0% | 98.2% | 88.3% | 52.2% |
Block-length sensitivity (E1, 52 weeks, scale 1): 
| mean block | maxDD p50 | p95 | P(>= 122k) | longest underwater p95 | P(P&L < 0) |
|---|---|---|---|---|---|
| 5 | $101k | $195k | 31.2% | 24 | 0.3% |
| 10 | $100k | $186k | 29.3% | 25 | 0.2% |
| 20 | $99k | $173k | 26.7% | 24 | 0.3% |
Longer blocks (more serial dependence kept) lower the deep tail slightly (p95 $195k at block 5, $173k at block 20).

## 4. Calibration check (the only out-of-sample element)
Bootstrap from 2023-04..2024-12, simulate 96 weeks, compare with the realised 2025-01..2026-10 (percentile = share of simulated paths with a smaller value):
| mean block | weeks | realised maxDD | pct | realised worst week | pct | realised longest underwater | pct | realised total P&L | pct | predicted maxDD p50 / p95 |
|---|---|---|---|---|---|---|---|---|---|---|
| 5 | 96 | $122k | 55% | $-63k | 14% | 9 | 7% | $1714k | 100% | $117k / $215k |
| 10 | 96 | $122k | 62% | $-63k | 9% | 9 | 7% | $1714k | 100% | $110k / $199k |
| 20 | 96 | $122k | 73% | $-63k | 5% | 9 | 6% | $1714k | 100% | $100k / $173k |

## 5. Reading and limits
For a risk-appetite decision the table says that a year at live lots should be expected to contain a drawdown of $100k (median) and has roughly a 3-in-10 chance of equalling the HOLD episode, a 1-in-30 chance of $200k, with spells of 10 weeks or more below the high as the norm; the answer is highly sensitive to the edge being real (E3) and moves in proportion to the lot scale. Limits: one 3.5-year realisation; block resampling assumes exchangeability within blocks and no regime change (the 2023 vs 2024-26 difference is visible in the calibration); weekly paths are consecutive 5-day groups, not calendar weeks; the engine record has no gap tail beyond what happened. Nothing here is a PASS or a recommendation to change lots.

Cross-reference (added after the Lead's note): ZL-2's DIS-V (autopilot/DS3_FWD_DD.md) is an independent forward-drawdown bootstrap of the same record (52-week maxDD median / p90 / p99 $92k / $149k / $218k); this page's E1 gives $100k / $161k / $244k at the same horizon (block 10), i.e. the two agree within about 10%, which is a useful independent check; DS3_FWD_DD.md was not read before this page was written.
(Precision for the cross-reference above: ratio of this page's E1 to DS3_FWD_DD.md at 52 weeks is 1.09 / 1.08 / 1.12 for p50 / p90 / p99, so 'within about 12%'.)
