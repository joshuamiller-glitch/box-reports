# DS3_THL2_A_FEATURES - L2 feature library (L2P, 2026-10-29)
Research only, UNTOUCHED never read (L2/tape reads filtered ts <= 2026-02-06 22:00 UTC; spine label days <= 2026-02-06). Everything is causal (book state = last 1-s snapshot with ts <= decision time; windows are (T-w, T]), side-signed where applicable (+ = with the trade), stored once per column in `l2vast/ds3/out/l2feat/` (= /mnt/l2/l2vast/ds3_l2feat), keyed (tid, ts) to the THPA tables row for row. Definitions: autopilot/DS3_L2_FEATURE_DEFS.md. Code: l2vast/ds3/code/l2feat/ (l2f_build, l2f_add_vpin, l2f_t2, l2f_t3, l2f_t4, l2f_gates, l2f_at). Source: NQ mbp-10 1-s tables (all 35 label months 2023-04..2026-02, one front contract stream per month), tape table (every trade record with aggressor and pre-trade touch), sweeps/vpin tables, ES and RTY 1-s tables. No MBO order-level replay was run (nothing new bought or downloaded).

## Counts and coverage
* Tranche 1 (profit dp1m/dp10s and loss ldp1m/ldp10s; 40,137 trades with profit rows, 3.25 M profit dp1m rows): 138 L2 columns + 5 VPIN columns. Tranche 2: 49. Tranche 3: 40. Tranche 4 (z and 60-s change of 162 continuous features): 324. Distinct raw features: ~232; with z/change variants 556 columns per dp1m row. Entry-side: `gates/` per-second market table (54 columns, both sides) and `features_at()` for any signal second.
* Grids: dp10s and dp1m (tranche 1), dp1m (tranches 2-4). Per-second (dp1s) is NOT materialised (400 M rows x 138 cols); the builder regenerates any subset. The 10-s grid hits every `ts % 10 == 0`; 10-s changes beyond the d_imb series are therefore available from consecutive dp10s rows.
* Share of in-trade seconds with a live book (snapshot age <= 3600 s): profit 99.86%, loss 100.00% (table_size.json); on the dp1m rows used here 100.0% (2023), 100.0% (2024), 99.55% (2025), 100.0% (2026). Gaps are concentrated in 2025 (0.45%). ES book: 57% of 2023 rows (ES tables start 2023-08), 99.5-100% from 2024. RTY same start. VPIN 100%. refill_t10_ms 85-91% (only when a refill event completed in the window). wall_tgt visible (target within the 10 levels, ladder contiguous): 0.09% (2023), 0.09% (2024), 0.10% (2025), 0.14% (2026) of profit rows; wall_stop visible: 0.00% of profit rows (stop is 33-60 pts away).
* The 10 visible levels are contiguous ticks on 99.0% of seconds (span = 9 ticks); the remaining 1% have gaps (walls there are NaN, tie rule in DEFS).

## Catalogue status (yes / proxy / not possible), directive THL2 CATALOGUE items
| group | item | status | note |
|---|---|---|---|
| 1 book state | best bid/ask size, L1 imbalance, imbalance 2/3/5/10 | yes | imb1/2/3/5/10, ahead_L1/behind_L1 |
| | imbalance 20 levels; cumulative depth 20 levels | not possible | mbp-10 shows 10 levels |
| | depth pressure log(B/A) 5/10 | yes | depth_press5/10 (t2) |
| | cumulative depth each side 5/10 vs session median | yes | cum_ahead/behind5/10, cum_*10_rel, depth_rel, rel_tot8/ahead8/behind8 (vs prior-20-day same-minute median) |
| | book slope, convexity, gaps top 10, largest level (size, distance), concentration, entropy, liquidity gaps (first level >= k) | yes | bslope_s/aslope_s, convex_*, gap_*, maxlv_*(_k,_rel), size_hhi, book_entropy, gapk10/25 |
| | spread ticks and duration | yes / proxy | spread_t yes; duration = proxy spread_max10 (max spread in last 10 s) |
| | microprice and microprice-mid bias | yes | micro_off_t |
| 2 walls | resting size at target, stop | yes (visible 0.1%) | wall_tgt/wall_stop (+_vis); NOT visible otherwise (mbp-10 horizon) |
| | at entry price, current price, each tick between price and target/stop | yes (10 levels) / proxy beyond | wall profile ahead_L1..10, behind_L1..10, cum_to_tgt, cum_to_stop; entry-price size = proxy vap_entry_since (volume traded at the entry price since entry) |
| | wall ahead/behind (largest, distance, median-level units), target/stop on/inside wall | yes / proxy | maxlv_*_rel; "target inside wall" only when wall_tgt_vis |
| | round numbers x00/x50 within +/-40 pts and size | yes / proxy | rnd50/100_ahead/behind (distance); size at the round number = vp_max_* (volume profile), book size there not visible |
| | liquidity sandwich, nearest wall each side | proxy | vp_max_ahead40/behind40 (volume-at-price walls within 40 pts) |
| | level AGE and stability at target/stop (MBO) | not possible | needs MBO at the target price; request in DS3_THL2_NEEDS.md |
| 3 queue | consumption at best (hit/s vs added/s), net queue change, refill ratio | yes | cons_ahead/behind10, refill_ratio_*, can_*, added_* |
| | time-to-exhaust best | proxy | best size / cons rate computable from ahead_L1 and cons_ahead10 |
| | refills/iceberg at best (consumed >= 2x displayed) | yes / proxy | iceberg_ahead/behind10 ratio (1-s aggregate, so the 2x flag fires on 63% of seconds; flag threshold 10x); at target/stop: not possible |
| | hidden liquidity (executed minus displayed) | proxy | iceberg ratio |
| | cancellation rate per side 10/30/60 s, pulled and added size 5/10/30 s | yes | cancel_sup/opp{10,30,60}, pulled_*, added_* |
| | cancel/replace bursts (<1 s), fleeting-order share (<500 ms, <2 s), order lifetime, spoofing-shape flag, queue position of a hypothetical limit | not possible at library scale | need MBO order ids; events_L13 holds levels 0-2 only for RTH; no MBO replay run. otr60 (order-to-trade) yes, int_ratio_book (Hawkes-style event rate vs 60-s baseline) proxy |
| 4 flow | aggressor delta 5/10/30/60/120 s + acceleration; 300 s | yes (300 s via CVD) | delta5..120, delta_acc; cvd_entry, cvd_sess (since entry / session open), cvd_div_entry |
| | OFI 1/10/30/60 s; multi-level OFI (Kolm) 1-5 / 1-10 | yes / proxy | ofi1_w, ofi5_w; levels 1-10 not available (proxy ofi5) |
| | event-count OBI (net adds minus cancels by side), lifetime/modification filters | yes / proxy | eobi10/30/60 (counts); lifetime filter not possible |
| | intensity vs session median + gates, large prints >= 25/50/100 count and net, largest print 60 s, time since last large print, last-5-prints sign sum | yes | intens_rel, cnt/net 25/50/100_30, big_max60(+side), t_since_big_*, last5_sign/sizeW (tape table) |
| | sweeps by side and time since; absorption/exhaustion; imbalance momentum; concordance | yes | sweep_*, absorb in THPA (absorb10_s), imb5_minus_ema10, d_imb*, concord |
| | VWAP(5/60 s)-mid; VPIN 50 buckets; PIN-style toxicity | yes / proxy | vwap5/60_mid, vpin50/20, svpin; PIN proxy = vpin |
| | Kyle lambda 60 s; square-root impact for own exit size; realised/effective spread of last 20 prints; resiliency after sweep | yes / proxy | kyle60 (proxy: mid change per 100 contracts net flow), exit_slip10/30 (walk-the-book slippage ticks), eff_spread20, real_spread20 (5-print horizon), refill_n10/refill_t10_ms |
| 5 footprint | delta per price level (current / previous bar), stacked imbalances (>= 300%, 3+ levels) with distance, unfinished auctions, bar POC, delta divergence, bar delta vs range, volume at entry price, largest-volume level between price and target/stop | yes | fp_* (1-min bar), fp5_* (trailing 5 min), fp_prev_*; volume at entry price: vap_entry_since; largest-volume level within 40 pts ahead/behind: vp_max_*; between price and the far target/stop is out of the 40-pt window |
| | session POC, migration, value area high/low and inside | yes / proxy | sess_poc_dist, sess_poc_mig30, sess_vah/val_dist, sess_inside_va (VA is the symmetric 70% interval around the POC, proxy for the standard VA expansion) |
| 6 cross-market | ES imbalance 1/5/10 (book on disk), ES OFI + delta, ES-NQ imbalance divergence, ES-NQ CVD agreement, lead-lag 10 s, ES micro, RTY same | yes | es_imb5/10, es_ofi5_30, es_delta30, esnq_imb5_div, esnq_delta_agree, esnq_cvd_agree30, es_lead10/rty_lead10, es_micro_off, rty_* ; ES/RTY book from 2023-08 |
| 7 context | minute-of-day median and MAD for every feature | yes (z, 30-min ET bucket, causal from prior months) | tranche 4: z_<f> (z vs prior-month rows of the same 30-min bucket, <= 300 sampled rows per month-bucket) and d60_<f> |
| 8 | raw / z / 10-s and 60-s change / side-signed | raw+side yes; z for 162 continuous features; 60-s change on dp1m (d60_), 10-s change from consecutive dp10s rows and the d_imb* series | |

## Entry-side (L2EA / L2EB / DIPENTRY)
`gates/YYYY-MM.parquet`: D6-LIVE gate inputs and booleans g1..g8 (both sides), rel_tot8, imb5 min over 30 s, veto; `features_at(ts, side, label_day)` returns ~136 side-signed columns including rel_tot8/ahead8/behind8, depth_rel, imb5/10, spread, intens_rel, vpin50, pulled_sup10/opp10, maxlv_*_rel, rnd50/100, es_imb5, ob_live. Gate frequencies on 2024-03 (per 1-s row, long): g1 absorption ~0.00%, g2 iceberg 0.3%, g3 imb5 flip 7.4%, g4 delta 13.1%, g5 depth 10.3%, g6 microprice 37.3%, g7 sweep+reclaim 13.8%, g8 print>=25 0.7%; >= 3 of 8 on 4.2% of rows, >= 2 of 8 on 19.6%.

## Three best single-feature readings per family
From L2H's descriptive map (DS3_THL2_B_MAP.md, pooled, recent first) - not re-derived here. L2P's own reading is model-based: importance by quarter and the family ablations in DS3_THL2_C_POLICIES.md (no family adds to the path out of sample).
