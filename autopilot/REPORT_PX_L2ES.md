# REPORT PX_L2ES - L2 microstructure at NQ-pair flips, measured on the ES mbp-10 book

**ES PROXY ONLY. NQ IS DECISIVE.** Report-only: no pair gates run, nothing here is a FOUND/NO verdict for any backlog item. The NQ pair flip/entry/exit times (ROWS_corrected_engine.parquet, ET -> UTC) are mapped onto the ES book; NQ point distances (target/stop) are scaled by ES mid / NQ entry price. Snapshot: 21 months processed (2025-02 .. 2026-10-11), 7,949 pair trades; the pipeline (ap_pc_pipe.sh, 4 streams) continues down to 2023-08 and `python3 -I outputs/autopilot/ap_pc_agg.py` regenerates the tables below from whatever months are finished.

Method / caveats
- Raw monthly mbp-10 -> per-second features (ap_pa4_build) -> raw deleted (KEEP_LOG.md). Features at flips use the book 1 s before the entry (no look-ahead).
- Item 15 runs on ALL trades vs their original exit (4 pre-registered cells, PREREG_PA4_L2.md). Items 97/98 use a queue-model simulation on SAMPLED event windows (<=30 target trades + <=30 thin-hour stop trades per month; placement 45 s before the NQ exit time, a deviation from "rest from entry" to keep windows small). cancel_frac in {0, 0.5, 1} all reported; 0 and 1 are the bounds.
- Stop/target prices are ES-scaled proxies of NQ levels and the NQ exit timestamp is a 1-min-bar time, so stop trigger timing vs the ES tape is uncertain. Item 98 numbers in particular (mean stop-market slippage 8.7 ticks) look contaminated by that misalignment and must not be read as ES/NQ slippage.
- Selection: none. Everything is descriptive on the full span; the imbalance finding in B is exploratory (non-virgin), to be pre-registered on NQ before any use.


## A. Spread state at ST/HM flips (ES book at the NQ-pair entry time, lag 1 s)

| sp_state   |    n |   fwd30 |   fwd60 |   fwd300 |   nq_pts |   t_nq_pts |
|:-----------|-----:|--------:|--------:|---------:|---------:|-----------:|
| 1 tick     | 6558 |   0.053 |   0.08  |   -0.018 |    2.567 |      3.673 |
| >=2 ticks  | 1391 |   0.045 |   0.271 |    0.552 |    1.104 |      0.716 |

Share of flips with spread >1 tick: 0.175 vs unconditional random seconds 0.356; mean spread (ticks) at flips 1.187 vs 0.944. fwdH = side-aligned ES mid move after the flip in ES points (0.25 = 1 tick); nq_pts = NQ pair trade result in NQ points (ROWS_corrected_engine).

## B. Depth imbalance (EMA10 of top-5 imbalance, aligned with the flip direction) at flips

| imb_bin    |    n |    imb |   fwd30 |   fwd60 |   fwd300 |   nq_pts |
|:-----------|-----:|-------:|--------:|--------:|---------:|---------:|
| Q1 against | 1590 | -0.179 |   0.044 |   0.13  |   -0.077 |    4.952 |
| Q2         | 1590 | -0.061 |   0.072 |   0.182 |    0.199 |    5.888 |
| Q3         | 1589 | -0.008 |   0.088 |   0.13  |    0.095 |    2.172 |
| Q4         | 1590 |  0.039 |  -0.06  |  -0.032 |   -0.339 |   -1.132 |
| Q5 with    | 1590 |  0.137 |   0.116 |   0.157 |    0.528 |   -0.328 |

|    | split     | metric   |    n |   mean |      t |
|---:|:----------|:---------|-----:|-------:|-------:|
|  0 | imb_al>0  | fwd30    | 3685 |  0.051 |  1.521 |
|  1 | imb_al>0  | fwd60    | 3685 |  0.078 |  1.505 |
|  2 | imb_al>0  | fwd300   | 3685 |  0.093 |  0.79  |
|  3 | imb_al>0  | nq_pts   | 3685 | -0.439 | -0.466 |
|  4 | imb_al<=0 | fwd30    | 4264 |  0.052 |  1.639 |
|  5 | imb_al<=0 | fwd60    | 4264 |  0.144 |  3.562 |
|  6 | imb_al<=0 | fwd300   | 4264 |  0.072 |  0.814 |
|  7 | imb_al<=0 | nq_pts   | 4264 |  4.687 |  5.436 |

NQ pair pts/trade difference (with-book minus against-book) = -5.13; by alternating month split:
|    | months   |    n |   dNQpts(with-against) |   dFwd60_ES(with-against) |
|---:|:---------|-----:|-----------------------:|--------------------------:|
|  0 | even     | 3922 |                 -3.435 |                    -0.054 |
|  1 | odd      | 4027 |                 -6.769 |                    -0.078 |

Per-month sign consistency of dNQpts: 4/21 months positive.
| book   |    n |   imb_al |   spread_gt1 |   fwd60 |
|:-------|-----:|---------:|-------------:|--------:|
| HM     | 3268 |   -0.012 |        0.166 |   0.155 |
| ST     | 4681 |   -0.016 |        0.182 |   0.084 |


## C. Item 15 - exit on L2 depth-imbalance flip (4 pre-registered cells), ES prices, vs original exit (target/stop/flip/time) with null

|    | cell          |    n |   frac_changed |   mean_d_all |   mean_d_changed |   null_mean_changed |   t_changed |   even |    odd |   d_target |   d_stop |   d_flip |   d_time |
|---:|:--------------|-----:|---------------:|-------------:|-----------------:|--------------------:|------------:|-------:|-------:|-----------:|---------:|---------:|---------:|
|  0 | span5/thr0.1  | 7949 |          0.97  |       -0.257 |           -0.265 |              -0.313 |      -2.036 | -0.252 | -0.262 |     -9.154 |    9.853 |    6.096 |    1.147 |
|  1 | span5/thr0.2  | 7949 |          0.859 |       -0.28  |           -0.326 |              -0.545 |      -2.393 | -0.285 | -0.275 |     -7.85  |    8.391 |    4.735 |    1.187 |
|  2 | span15/thr0.1 | 7949 |          0.933 |       -0.261 |           -0.28  |              -0.402 |      -2.124 | -0.237 | -0.285 |     -8.685 |    9.312 |    5.685 |    1.288 |
|  3 | span15/thr0.2 | 7949 |          0.716 |       -0.212 |           -0.296 |              -0.817 |      -2.054 | -0.227 | -0.197 |     -6.324 |    6.839 |    3.762 |    0.433 |

d = side*(new exit - original exit) in ES points per trade, new exit at the touch (mid -/+ half spread) one second after the signal; no extra slippage beyond the touch. Negative = early exit loses vs original. null = same trades exited at a uniformly random second in [entry+20s, original exit) (10 draws), same touch pricing.

## D. Item 97 - target as limit +1 tick improvement in high-depth states (sampled <=30 target trades/month)

|                            |   n |   n_high_depth |   mean_d_pts |   fill |   queue0 |
|:---------------------------|----:|---------------:|-------------:|-------:|---------:|
| ("{'timeout_s': 15}", 0.0) | 631 |            374 |       -0.103 |  0.135 |       14 |
| ("{'timeout_s': 15}", 0.5) | 631 |            374 |       -0.101 |  0.136 |       14 |
| ("{'timeout_s': 15}", 1.0) | 631 |            374 |       -0.1   |  0.138 |       14 |
| ("{'timeout_s': 30}", 0.0) | 631 |            374 |       -0.126 |  0.144 |       14 |
| ("{'timeout_s': 30}", 0.5) | 631 |            374 |       -0.125 |  0.146 |       14 |
| ("{'timeout_s': 30}", 1.0) | 631 |            374 |       -0.124 |  0.147 |       14 |
| ("{'timeout_s': 5}", 0.0)  | 631 |            374 |       -0.065 |  0.13  |       14 |
| ("{'timeout_s': 5}", 0.5)  | 631 |            374 |       -0.062 |  0.133 |       14 |
| ("{'timeout_s': 5}", 1.0)  | 631 |            374 |       -0.061 |  0.135 |       14 |

High-depth subset only (the only trades the rule changes):
|                            |   n |   mean_d_pts |   fill |      t |
|:---------------------------|----:|-------------:|-------:|-------:|
| ("{'timeout_s': 15}", 0.0) | 374 |       -0.174 |  0.227 | -2.161 |
| ("{'timeout_s': 15}", 0.5) | 374 |       -0.171 |  0.23  | -2.126 |
| ("{'timeout_s': 15}", 1.0) | 374 |       -0.169 |  0.233 | -2.101 |
| ("{'timeout_s': 30}", 0.0) | 374 |       -0.213 |  0.243 | -2.444 |
| ("{'timeout_s': 30}", 0.5) | 374 |       -0.211 |  0.246 | -2.411 |
| ("{'timeout_s': 30}", 1.0) | 374 |       -0.209 |  0.249 | -2.388 |
| ("{'timeout_s': 5}", 0.0)  | 374 |       -0.109 |  0.219 | -1.55  |
| ("{'timeout_s': 5}", 0.5)  | 374 |       -0.104 |  0.225 | -1.482 |
| ("{'timeout_s': 5}", 1.0)  | 374 |       -0.103 |  0.227 | -1.463 |


## E. Item 98 - stop-limit vs stop-market, thin Globex hours (sampled <=30 thin-hour stop trades/month)

|                     |   n |   slip_mkt_mean |   slip_mkt_p95 |   slip_lim_mean |   slip_lim_p95 |   d_pts |   worst5 |
|:--------------------|----:|----------------:|---------------:|----------------:|---------------:|--------:|---------:|
| ("{'off': 2}", 0.0) | 142 |           8.662 |          16.95 |           8.62  |          18.95 |   0.011 |    -0.25 |
| ("{'off': 2}", 0.5) | 142 |           8.662 |          16.95 |           8.62  |          18.95 |   0.011 |    -0.25 |
| ("{'off': 2}", 1.0) | 142 |           8.662 |          16.95 |           8.62  |          18.95 |   0.011 |    -0.25 |
| ("{'off': 4}", 0.0) | 142 |           8.662 |          16.95 |           8.683 |          18.95 |  -0.005 |    -0.25 |
| ("{'off': 4}", 0.5) | 142 |           8.662 |          16.95 |           8.683 |          18.95 |  -0.005 |    -0.25 |
| ("{'off': 4}", 1.0) | 142 |           8.662 |          16.95 |           8.683 |          18.95 |  -0.005 |    -0.25 |

## Reading
1. Spread state (A): only 17.5% of flips happen with ES spread >1 tick (random-second baseline 35.6% is inflated by illiquid/maintenance-break seconds, so use as context only). Wide-spread flips have a bigger 60/300 s ES drift in the flip direction (0.27/0.55 pt vs 0.08/-0.02) but NQ pair pts/trade is lower and insignificant (1.1, t 0.7 vs 2.6, t 3.7). No evidence that a spread>1 tick skip would help; n=1,391.
2. Depth imbalance at flips (B): the book leaning WITH the flip direction does not help; the pair did better when the EMA10 top-5 imbalance leaned AGAINST the flip (NQ pts/trade +4.69, t 5.4 vs -0.44, t -0.5; difference -5.13 pts/trade, same sign in both alternating-month halves (-3.4 even, -6.8 odd) and positive in only 4/21 months of "with minus against"). ES forward drift shows no matching asymmetry at 30-300 s. So this is a contrarian/absorption pattern in the NQ pair outcome, not an ES price-drift signal. Candidate for an E38-type PRE-REGISTRATION on the NQ book (inverted sign vs the written E38 'skip if <0'), not a result.
3. Item 15 (C): early exit on imbalance flip is negative in all 4 cells (mean -0.21 to -0.28 ES pts/trade over all trades, t about -2 on changed trades); it beats its random-time-exit null modestly in cells with thr 0.2 (-0.33 vs -0.55, -0.30 vs -0.82) but is still a loss vs keeping the original exit; sign is the same in even and odd months. It cuts stop losses (+7 to +10 pts) and forfeits targets (-6 to -9 pts) almost one for one. Prior stands: NO-leaning.
4. Item 97 (D): limit +1 tick above target in high-depth states fills only 22-25% of the time (median queue ahead 14 lots); mean effect -0.10 to -0.21 pts/trade on the 374 changed trades (t -1.5 to -2.4), identical within noise at cancel_frac 0, 0.5, 1 (the bounds do not change the sign). Missed-target cost exceeds the 1-tick gain. NO-leaning on ES proxy.
5. Item 98 (E): stop-limit vs stop-market differences are ~0 (+0.011 pt at 2 ticks, -0.005 at 4 ticks, n=142 sampled stops), p95 slip slightly worse with stop-limit (18.95 vs 16.95 ticks). Inconclusive: see the timing caveat; needs NQ with true stop timing.

Jobs: NQ GLBX-20261013-Y3PCQ4MKV3 and RTY GLBX-20261015-XDLHWMFQ3R were still "processing" at the last check (see pa4/JOBCHECK.log, hourly). Download of the paid ES job: no extra charge observed (no billing endpoint in the API; see SPEND.json notes).

Files: outputs/autopilot/pa4/px/ (ES_YYYY-MM_{sec,flip,i15_*,i97,i98,res}.parquet/json, agg_body.md), code ap_pc_month.py, ap_pc_pipe.sh, ap_pc_agg.py, ap_pc_db.py.

DONE PX_L2ES (snapshot, 21/39 months)
