# INSTR2 CROSS-OWNER REPRODUCTION AUDIT (CAL, 2026-11-05T20:11:40Z) - measurement only; evaluator md5 cc29db32ff6f2de7ab39a66e73abbb2f
Method: for each owner's best 3 tolerant stage-2 cells (CL ZL-1, RTY and YM Z2, GC S4a; ordering: tolerant first, then HOLD mean), take the cell's stored daily $ series and RECOMPUTE with the shared evaluator, in a fresh process (code/instr2/repro_audit.py): window table (8 windows x carry kept/dropped: mean, maxDD, Calmar), correlation to V0 and V2 (daily, weekly), k*, and dCalmar at k* (HOLD, L6M). Disagreement threshold 2% relative (corr 0.02 absolute, dCalmar 0.002).
Limit: owners did not save trade lists, so this reproduces the evaluator output from the stored daily series (it proves the window/stack/correlation arithmetic and the stored results are consistent), NOT the trade simulation upstream. Same-trade-list reproduction needs each owner to save the trade frame of its finalists (request: write trades_<cell>.parquet next to stage2.pkl). Placebo p-values were not recomputed (random worlds).
Result: 660 checks, 0 disagreements > 2%.
- CL #1 {'book': 'CL pullback_band', 'session': 'pre', 'anchor': "{'regime_k': 10, 'st_m': 2.0, 'ema_n': 30}", 'trigge | tolerant=True n=818 | AGREES (<=2%)
- CL #2 {'book': 'CL momentum_vote', 'session': 'pre', 'anchor': "{'k': 5, 'thr': 3, 'windows': (6, 12, 24)}", 'trigge | tolerant=True n=669 | AGREES (<=2%)
- CL #3 {'book': 'CL keltner_flip', 'session': 'pre', 'anchor': "{'k': 5, 'n': 14, 'n_atr': 14, 'mult': 0.5}", 'trigge | tolerant=True n=856 | AGREES (<=2%)
- RTY #1 {'book': 'RTY K|b3|ema34|atr10|m0.5', 'session': 'london', 'anchor': 'K|b3|ema34|atr10|m0.5', 'trigger': 'orie | tolerant=True n=6144 | AGREES (<=2%)
- RTY #2 {'book': 'RTY K|b10|ema8|atr14|m2.0', 'session': 'nyam', 'anchor': 'K|b10|ema8|atr14|m2.0', 'trigger': 'orient | tolerant=True n=1615 | AGREES (<=2%)
- RTY #3 {'book': 'RTY K|b10|ema8|atr14|m2.0', 'session': 'nyam', 'anchor': 'K|b10|ema8|atr14|m2.0', 'trigger': 'orient | tolerant=True n=1615 | AGREES (<=2%)
- YM #1 {'book': 'YM K|b1|ema13|atr7|m1.0', 'session': 'nyam', 'anchor': 'K|b1|ema13|atr7|m1.0', 'trigger': 'orient 1' | tolerant=True n=3789 | AGREES (<=2%)
- YM #2 {'book': 'YM K|b1|ema13|atr7|m1.0', 'session': 'nyam', 'anchor': 'K|b1|ema13|atr7|m1.0', 'trigger': 'orient 1' | tolerant=True n=3789 | AGREES (<=2%)
- YM #3 {'book': 'YM K|b1|ema13|atr7|m1.0', 'session': 'nyam', 'anchor': 'K|b1|ema13|atr7|m1.0', 'trigger': 'orient 1' | tolerant=True n=3789 | AGREES (<=2%)
- GC #1 {'book': 'GC PB', 'session': 'asia', 'anchor': '{"b": 2, "e": 34, "m": 1.0}', 'trigger': 'PB', 'shape': 'stop  | tolerant=True n=2649 | AGREES (<=2%)
- GC #2 {'book': 'GC HMAV', 'session': 'nyam', 'anchor': '{"b": 5, "n": 34}', 'trigger': 'HMAV', 'shape': 'stop usd120 | tolerant=True n=1006 | AGREES (<=2%)
- GC #3 {'book': 'GC PB', 'session': 'asia', 'anchor': '{"b": 2, "e": 34, "m": 1.0}', 'trigger': 'PB', 'shape': 'stop  | tolerant=True n=2668 | AGREES (<=2%)
checks 660 disagreements 0
Notes: RTY #2/#3 and YM #1-#3 are the same book at different brackets/targets (stage-2 shape variants), GC #1 and #3 likewise. ES, ZN, ZB, 6E, 6J, NKD, BTC, MBT have no stage-2 pickle yet; re-run at the next merge.
