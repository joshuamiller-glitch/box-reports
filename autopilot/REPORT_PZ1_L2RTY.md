# REPORT PZ1 L2 RTY (RTY PROXY ONLY - NQ pair, report-only)

**RTY PROXY ONLY (NQ pair). No pair-level verdict and no FOUND/NO claim: report-only evaluators of the RTY mbp-10 book at the live NQ pair's ST/HM flip times (ROWS_corrected_engine, ET->UTC), mapped through RTY ticks (0.10) as a proxy for NQ. Headline: spread state does not separate outcomes in a useful way; depth imbalance with the flip shows NO stable sign (with-minus-against = -0.25 NQ pts/trade; even months +1.42, odd months -1.93; 18/39 months positive), unlike the ES proxy (+5.1 pts); item 15 exits lose vs original in all 4 cells (t -1.6 to -3.3) and slightly worse than the random-exit null in 3/4; item 97 limit improvement loses (-0.16 to -0.18 pts in high-depth subset, fill ~46%); item 98 stop-limit costs -0.04/-0.05 pts vs stop-market.**

Data: Databento job GLBX-20261015-XDLHWMFQ3R (RTY mbp-10, state done, already paid; download free; no new purchase/job/resubmission). 39 monthly files 2023-08..2026-10 downloaded month by month (3 streams), reduced to per-second L2 features by ap_pz1_month.py (copy of the ES pipeline ap_pc_month.py with RTY tick 0.10: spread, half-spread, target rounding, queue tick), raw deleted after each success (disk guard: refuse download below 70 GB free; free never below ~150 GB). Footprint kept: pz1/rty (2.1 GB derived tables: *_sec.parquet, *_flip.parquet, *_i15_*, *_i97, *_i98, *_res.json). Log: pa4/KEEP_LOG.md. Pre-registered grids are those of PREREG_PA4_L2.md (items 15/97/98), unchanged. Aggregation: ap_pz1_agg.py (copy of ap_pd5_agg.py with RTY tick), tables in pz1/rty/agg_body.md.

Caveats: (1) RTY is a different book than NQ (thinner, 0.10 tick); the mapped prices use RTY mid/spread, trades are NQ pair trades with stop/target distances scaled by RTY_mid/NQ_entry. (2) 'fwd' columns are RTY points (0.10 tick) - the column header 'ES' in the table is a legacy label. (3) The unconditional mean spread (11 ticks) is inflated by thin Globex hours/outlier seconds, so the 'flips vs random seconds' spread comparison is not meaningful. (4) 97/98 are sampled trade windows (<=30/month), descriptive only. (5) Replication leg (ii) of the PX35 DIA prereg: RTY proxy sign for DIA (imb_al>0 worse than <=0) is NOT reproduced (difference -0.25, wrong sign vs ES proxy and unstable by parity), recorded for PX35.

## Results (full tables)

## A. Spread state at ST/HM flips (RTY book at the NQ-pair entry time, lag 1 s)

| sp_state   |     n |   fwd30 |   fwd60 |   fwd300 |   nq_pts |   t_nq_pts |
|:-----------|------:|--------:|--------:|---------:|---------:|-----------:|
| 1 tick     |  1910 |  -0.01  |   0.009 |   -0.004 |    3.731 |      3.003 |
| >=2 ticks  | 10113 |   0.026 |   0.05  |    0.084 |    2.084 |      3.716 |

Share of flips with spread >1 tick: 0.841 vs unconditional random seconds 0.874; mean spread (ticks) at flips 2.387 vs 11.046. fwdH = side-aligned ES mid move after the flip in RTY points (0.25 = 1 tick); nq_pts = NQ pair trade result in NQ points (ROWS_corrected_engine).

## B. Depth imbalance (EMA10 of top-5 imbalance, aligned with the flip direction) at flips

| imb_bin    |    n |    imb |   fwd30 |   fwd60 |   fwd300 |   nq_pts |
|:-----------|-----:|-------:|--------:|--------:|---------:|---------:|
| Q1 against | 2405 | -0.153 |   0.025 |   0.039 |    0.055 |    3.799 |
| Q2         | 2404 | -0.041 |   0.016 |   0.085 |    0.145 |    1.995 |
| Q3         | 2405 |  0.009 |   0.005 |   0.001 |   -0.039 |    2.438 |
| Q4         | 2404 |  0.06  |   0.005 |   0.026 |    0.055 |    3.653 |
| Q5 with    | 2405 |  0.171 |   0.048 |   0.065 |    0.135 |   -0.156 |

|    | split     | metric   |    n |   mean |     t |
|---:|:----------|:---------|-----:|-------:|------:|
|  0 | imb_al>0  | fwd30    | 6492 |  0.023 | 1.82  |
|  1 | imb_al>0  | fwd60    | 6492 |  0.033 | 1.788 |
|  2 | imb_al>0  | fwd300   | 6492 |  0.065 | 1.608 |
|  3 | imb_al>0  | nq_pts   | 6492 |  2.229 | 3.197 |
|  4 | imb_al<=0 | fwd30    | 5531 |  0.016 | 1.055 |
|  5 | imb_al<=0 | fwd60    | 5531 |  0.055 | 2.713 |
|  6 | imb_al<=0 | fwd300   | 5531 |  0.076 | 1.863 |
|  7 | imb_al<=0 | nq_pts   | 5531 |  2.483 | 3.301 |

NQ pair pts/trade difference (with-book minus against-book) = -0.25; by alternating month split:
|    | months   |    n |   dNQpts(with-against) |   dFwd60_ES(with-against) |
|---:|:---------|-----:|-----------------------:|--------------------------:|
|  0 | even     | 5983 |                  1.424 |                     0.003 |
|  1 | odd      | 6040 |                 -1.933 |                    -0.045 |

Per-month sign consistency of dNQpts: 18/39 months positive.
| book   |    n |   imb_al |   spread_gt1 |   fwd60 |
|:-------|-----:|---------:|-------------:|--------:|
| HM     | 4975 |    0.016 |        0.835 |   0.079 |
| ST     | 7048 |    0.005 |        0.845 |   0.018 |


## C. Item 15 - exit on L2 depth-imbalance flip (4 pre-registered cells), RTY prices, vs original exit (target/stop/flip/time) with null

|    | cell          |     n |   frac_changed |   mean_d_all |   mean_d_changed |   null_mean_changed |   t_changed |   even |    odd |   d_target |   d_stop |   d_flip |   d_time |
|---:|:--------------|------:|---------------:|-------------:|-----------------:|--------------------:|------------:|-------:|-------:|-----------:|---------:|---------:|---------:|
|  0 | span5/thr0.1  | 12023 |          0.966 |       -0.181 |           -0.188 |              -0.133 |      -2.956 | -0.166 | -0.196 |     -4.082 |    4.349 |    2.595 |   -0.311 |
|  1 | span5/thr0.2  | 12023 |          0.829 |       -0.143 |           -0.173 |              -0.131 |      -2.548 | -0.125 | -0.162 |     -3.306 |    3.495 |    2.156 |   -0.039 |
|  2 | span15/thr0.1 | 12023 |          0.907 |       -0.195 |           -0.215 |              -0.113 |      -3.309 | -0.183 | -0.208 |     -3.756 |    3.932 |    2.417 |   -0.425 |
|  3 | span15/thr0.2 | 12023 |          0.667 |       -0.082 |           -0.123 |              -0.145 |      -1.603 | -0.077 | -0.087 |     -2.541 |    2.746 |    1.764 |   -0.117 |

d = side*(new exit - original exit) in RTY points per trade, new exit at the touch (mid -/+ half spread) one second after the signal; no extra slippage beyond the touch. Negative = early exit loses vs original. null = same trades exited at a uniformly random second in [entry+20s, original exit) (10 draws), same touch pricing.

## D. Item 97 - target as limit +1 tick improvement in high-depth states (sampled <=30 target trades/month)

|                            |    n |   n_high_depth |   mean_d_pts |   fill |   queue0 |
|:---------------------------|-----:|---------------:|-------------:|-------:|---------:|
| ("{'timeout_s': 15}", 0.0) | 1171 |            551 |       -0.082 |  0.217 |        0 |
| ("{'timeout_s': 15}", 0.5) | 1171 |            551 |       -0.081 |  0.219 |        0 |
| ("{'timeout_s': 15}", 1.0) | 1171 |            551 |       -0.079 |  0.219 |        0 |
| ("{'timeout_s': 30}", 0.0) | 1171 |            551 |       -0.079 |  0.223 |        0 |
| ("{'timeout_s': 30}", 0.5) | 1171 |            551 |       -0.076 |  0.224 |        0 |
| ("{'timeout_s': 30}", 1.0) | 1171 |            551 |       -0.073 |  0.225 |        0 |
| ("{'timeout_s': 5}", 0.0)  | 1171 |            551 |       -0.077 |  0.213 |        0 |
| ("{'timeout_s': 5}", 0.5)  | 1171 |            551 |       -0.076 |  0.216 |        0 |
| ("{'timeout_s': 5}", 1.0)  | 1171 |            551 |       -0.074 |  0.217 |        0 |

High-depth subset only (the only trades the rule changes):
|                            |   n |   mean_d_pts |   fill |      t |
|:---------------------------|----:|-------------:|-------:|-------:|
| ("{'timeout_s': 15}", 0.0) | 551 |       -0.175 |  0.461 | -4.813 |
| ("{'timeout_s': 15}", 0.5) | 551 |       -0.172 |  0.465 | -4.725 |
| ("{'timeout_s': 15}", 1.0) | 551 |       -0.167 |  0.466 | -4.578 |
| ("{'timeout_s': 30}", 0.0) | 551 |       -0.167 |  0.474 | -4.33  |
| ("{'timeout_s': 30}", 0.5) | 551 |       -0.162 |  0.475 | -4.211 |
| ("{'timeout_s': 30}", 1.0) | 551 |       -0.156 |  0.477 | -4.039 |
| ("{'timeout_s': 5}", 0.0)  | 551 |       -0.164 |  0.454 | -4.885 |
| ("{'timeout_s': 5}", 0.5)  | 551 |       -0.162 |  0.459 | -4.823 |
| ("{'timeout_s': 5}", 1.0)  | 551 |       -0.157 |  0.461 | -4.658 |


## E. Item 98 - stop-limit vs stop-market, thin Globex hours (sampled <=30 thin-hour stop trades/month)

|                     |   n |   slip_mkt_mean |   slip_mkt_p95 |   slip_lim_mean |   slip_lim_p95 |   d_pts |   worst5 |
|:--------------------|----:|----------------:|---------------:|----------------:|---------------:|--------:|---------:|
| ("{'off': 2}", 0.0) | 449 |          23.768 |             81 |          24.223 |             80 |  -0.045 |     -0.5 |
| ("{'off': 2}", 0.5) | 449 |          23.768 |             81 |          24.223 |             80 |  -0.045 |     -0.5 |
| ("{'off': 2}", 1.0) | 449 |          23.768 |             81 |          24.223 |             80 |  -0.045 |     -0.5 |
| ("{'off': 4}", 0.0) | 449 |          23.768 |             81 |          24.169 |             80 |  -0.04  |     -0.4 |
| ("{'off': 4}", 0.5) | 449 |          23.768 |             81 |          24.147 |             80 |  -0.038 |     -0.4 |
| ("{'off': 4}", 1.0) | 449 |          23.768 |             81 |          24.147 |             80 |  -0.038 |     -0.4 |

DONE PZ1
