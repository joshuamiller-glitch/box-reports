# TH-STATE validation criteria (fixed 2026-11-08 BEFORE the full run)
Builder code/th_state/th_state.py (clock ts_event running-max, book = last record per second, T records = prints, MedLevel EWMA 0.001 per row, window = previous trading day + day, reset at instrument change).
(a) Blind week vs MBO-derived book (code/mbo_book, 50 ms grid on ts_event clock sampled at whole seconds): 3 windows >= 10 min on 3 different label days; PASS if >= 99.5% of second ends have all 10 levels (px and sz, both sides) equal and the best bid/ask px+sz equal in >= 99.9%; every residual class reported.
(b) cancelled_bid/ask vs brute-force pure-Python recomputation from raw records (independent code path, dict books per second) on 2 random days (seed 20261108): PASS if 0 mismatching rows in both arrays (all rows).
(c) Determinism: 3 days regenerated with a different block start (different warm-up/chunk seams): sha256 of the day files identical.
(d) Per-day: traded records (action T) in raw == stored prints, all days (trade_mismatch == 0); plus one month recounted by an independent pandas path (tz labels).
(e) Coverage: days present vs expected weekdays; holidays; roll days flagged; RTH record gaps > 60 s listed; crossed-book and late-ts_event counts reported.
No criterion is tuned after seeing results; failures are reported as failures.
