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


## RESTATEMENT ON THE LIVE-WINDOW BASES (appended 2026-11-05; scale 1.0, block 10, 20,000 paths; the published tables above are base V0)
Bases (ZL-2, DS3_LIVE_WINDOWS_BASE.md; daily core series from out/dis_ba/bj_out.pkl): V0 = the engine as run (the base of every table above; ties to $2,520,149); V1 = 18:00-18:04 entries blocked (the Q3 answer); V2 = 09:30-09:59 and 18:00-18:04 blocked (the latest-statements reading). EVERY number below names its base. Ties: my window masks reproduce ZL-2's V1 and V2 daily series to 0.000 $.
In-sample record of each base (weekly cumulative):
| base | | total | mean per week | maxDD | worst week | worst day |
|---|---|---|---|---|---|---|
| V0 as run | in-sample | $2.52M | $13k | $122k | $-63k | $-38k |
| V1 18:00-18:04 blocked | in-sample | $2.59M | $14k | $103k | $-61k | $-38k |
| V2 09:30-09:59 + 18:00-18:04 blocked | in-sample | $2.46M | $13k | $94k | $-60k | $-37k |
Forward distribution (E1 sample as is, E3 zero edge, E4 resample 2024+), by base and horizon (weeks):
| base | scenario | weeks | maxDD p50 | p90 | p95 | p99 | P(>= 100k) | P(>= 122k) | P(>= 150k) | P(>= 200k) | P(year-end P&L < 0) | longest underwater p50 / p95 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V0 as run | E1 sample | 13 | $55k | $106k | $125k | $169k | 12.3% | 5.8% | 2.2% | 0.3% | 8.3% | 4 / 11 |
| V0 as run | E1 sample | 26 | $75k | $133k | $156k | $208k | 26.9% | 14.2% | 6.1% | 1.3% | 2.4% | 7 / 17 |
| V0 as run | E1 sample | 52 | $99k | $161k | $185k | $240k | 49.5% | 29.4% | 13.7% | 3.3% | 0.3% | 10 / 25 |
| V0 as run | E1 sample | 104 | $123k | $188k | $214k | $271k | 75.5% | 52.3% | 26.9% | 7.2% | 0.0% | 14 / 32 |
| V1 18:00-18:04 blocked | E1 sample | 13 | $50k | $99k | $116k | $155k | 9.4% | 3.8% | 1.2% | 0.2% | 7.0% | 4 / 10 |
| V1 18:00-18:04 blocked | E1 sample | 26 | $68k | $121k | $142k | $187k | 20.3% | 9.6% | 3.7% | 0.7% | 1.6% | 6 / 16 |
| V1 18:00-18:04 blocked | E1 sample | 52 | $90k | $144k | $166k | $215k | 38.4% | 19.3% | 8.4% | 1.7% | 0.1% | 9 / 22 |
| V1 18:00-18:04 blocked | E1 sample | 104 | $111k | $169k | $192k | $245k | 63.1% | 37.1% | 17.2% | 4.0% | 0.0% | 13 / 28 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E1 sample | 13 | $51k | $94k | $111k | $149k | 8.2% | 3.2% | 0.9% | 0.1% | 7.3% | 4 / 11 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E1 sample | 26 | $68k | $118k | $138k | $181k | 19.4% | 8.6% | 3.3% | 0.6% | 2.1% | 6 / 17 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E1 sample | 52 | $88k | $142k | $163k | $210k | 37.3% | 18.9% | 7.7% | 1.5% | 0.2% | 9 / 23 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E1 sample | 104 | $109k | $166k | $188k | $237k | 62.6% | 36.4% | 16.4% | 3.3% | 0.0% | 13 / 30 |
| V0 as run | E3 zero edge | 13 | $111k | $209k | $242k | $304k | 56.7% | 43.3% | 28.8% | 11.9% | 54.1% | 9 / 13 |
| V0 as run | E3 zero edge | 26 | $174k | $312k | $357k | $448k | 85.7% | 75.3% | 61.6% | 38.3% | 52.6% | 17 / 26 |
| V0 as run | E3 zero edge | 52 | $265k | $468k | $537k | $676k | 98.4% | 95.3% | 88.9% | 72.2% | 52.3% | 34 / 52 |
| V0 as run | E3 zero edge | 104 | $395k | $689k | $786k | $973k | 100.0% | 99.8% | 99.2% | 94.3% | 51.9% | 68 / 104 |
| V1 18:00-18:04 blocked | E3 zero edge | 13 | $106k | $197k | $225k | $285k | 54.4% | 40.0% | 25.3% | 9.3% | 53.9% | 9 / 13 |
| V1 18:00-18:04 blocked | E3 zero edge | 26 | $165k | $297k | $338k | $428k | 84.1% | 72.7% | 57.6% | 34.5% | 52.6% | 17 / 26 |
| V1 18:00-18:04 blocked | E3 zero edge | 52 | $251k | $443k | $510k | $635k | 98.2% | 94.4% | 86.6% | 68.3% | 51.9% | 34 / 52 |
| V1 18:00-18:04 blocked | E3 zero edge | 104 | $378k | $662k | $758k | $934k | 100.0% | 99.8% | 98.9% | 93.0% | 51.6% | 68 / 104 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E3 zero edge | 13 | $104k | $192k | $219k | $276k | 53.0% | 38.1% | 23.6% | 8.2% | 54.0% | 8 / 13 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E3 zero edge | 26 | $164k | $292k | $335k | $413k | 84.0% | 72.4% | 57.1% | 34.0% | 53.5% | 17 / 26 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E3 zero edge | 52 | $251k | $438k | $502k | $622k | 97.9% | 94.2% | 86.2% | 68.0% | 52.7% | 34 / 52 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E3 zero edge | 104 | $373k | $645k | $736k | $913k | 100.0% | 99.7% | 98.5% | 92.5% | 51.0% | 67 / 104 |
| V0 as run | E4 recent 2024+ | 13 | $54k | $105k | $123k | $164k | 11.9% | 5.5% | 1.8% | 0.2% | 5.3% | 4 / 10 |
| V0 as run | E4 recent 2024+ | 26 | $74k | $129k | $148k | $197k | 24.9% | 12.8% | 4.8% | 0.9% | 1.1% | 6 / 15 |
| V0 as run | E4 recent 2024+ | 52 | $96k | $154k | $176k | $228k | 45.8% | 26.5% | 11.2% | 2.2% | 0.0% | 8 / 20 |
| V0 as run | E4 recent 2024+ | 104 | $120k | $180k | $202k | $253k | 72.4% | 47.7% | 22.5% | 5.3% | 0.0% | 12 / 26 |
| V1 18:00-18:04 blocked | E4 recent 2024+ | 13 | $50k | $95k | $112k | $153k | 8.1% | 3.3% | 1.1% | 0.1% | 4.2% | 3 / 9 |
| V1 18:00-18:04 blocked | E4 recent 2024+ | 26 | $67k | $116k | $134k | $179k | 18.0% | 8.1% | 2.9% | 0.4% | 0.5% | 5 / 13 |
| V1 18:00-18:04 blocked | E4 recent 2024+ | 52 | $88k | $137k | $157k | $205k | 34.9% | 16.6% | 6.4% | 1.2% | 0.0% | 8 / 18 |
| V1 18:00-18:04 blocked | E4 recent 2024+ | 104 | $106k | $159k | $180k | $225k | 58.1% | 32.0% | 13.5% | 2.5% | 0.0% | 11 / 23 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E4 recent 2024+ | 13 | $51k | $92k | $108k | $146k | 7.4% | 2.7% | 0.8% | 0.1% | 4.2% | 3 / 9 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E4 recent 2024+ | 26 | $67k | $112k | $131k | $176k | 16.5% | 6.9% | 2.5% | 0.4% | 0.7% | 5 / 14 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E4 recent 2024+ | 52 | $84k | $133k | $152k | $200k | 31.6% | 14.5% | 5.3% | 1.0% | 0.0% | 8 / 19 |
| V2 09:30-09:59 + 18:00-18:04 blocked | E4 recent 2024+ | 104 | $104k | $154k | $175k | $220k | 55.4% | 29.6% | 11.5% | 2.1% | 0.0% | 11 / 23 |
Reading: the live windows lower the observed HOLD depth (V0 $122.0k -> V1 $103.3k -> V2 $94.0k) and the forward distribution with it: at 52 weeks, E1, the median year's maxDD is $99k (V0) / $90k (V1) / $88k (V2), P(>= $150k) 13.7% / 8.4% / 7.7%, P(>= $200k) 3.3% / 1.7% / 1.5%; the mean per week moves $13.5k / $13.9k / $13.2k. The zero-edge (E3) year barely changes ($265k / $251k / $251k median maxDD): the windows do not protect against a vanished edge. This restatement uses the same random seed stream in a new run, so V0 here differs from the published V0 by Monte Carlo noise (P(>= $122k) 29.4% vs 29.3%).

## RECONCILIATION of the V2 depth ($94.0k here vs $91.2k at ZL-2 / BASE-4) (appended 2026-11-05)
The gap is a labelling difference, not an engine or window-edge difference. The 'maxDD' column of my in-sample table (and the 'observed HOLD depth' in my reading) is the maxDD of the WHOLE 187-week history; ZL-2 (DIS-BJ) and BASE-4 (DIS-BR) quote the maxDD of the HOLD WINDOW (2025-11-01..2026-10-31, weeks 2025 W45..2026 W44). For V0 and V1 the two coincide (the deepest drawdown of the history is the 2026 W05-W08 episode inside HOLD: $122,025 and $103,295). For V2 the deepest drawdown of the whole history is a different episode: $93,974, peak 2025 W05 to trough 2025 W09 (inside the PRE window, in the span the harness calls the PRE carrying weeks 202506-09), which is deeper than the HOLD-window episode (2026 W05 to W08), $91,168. Recomputed from my V2 series: HOLD window $91,168 (52 weeks, first week 202545, last 202644, no weeks dropped) = ZL-2 / BASE-4; all-history $93,974; PRE window $93,974 (the same episode); L6M $64,936; X' $77,536. Which edge/clock variants were NOT the cause: the 18:00-18:04 vs 18:05 edge and the signal-vs-fill clock for PE (my masks tie to ZL-2's V1 and V2 daily series to 0.000 $), and the carry-dropped weeks (none dropped in either number). WHICH NUMBER TO QUOTE: for 'the HOLD episode' under V2 quote $91.2k (HOLD window); for the in-sample maxDD that the bootstrap is compared with (the whole record) quote $94.0k and name it 'all-history maxDD'. Correction to the reading above: 'V0 $122.0k -> V1 $103.3k -> V2 $94.0k' is the all-history maxDD; the HOLD-window values are $122.0k -> $103.3k -> $91.2k.
