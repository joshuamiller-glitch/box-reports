# R13_TRAIL_LIVE_REPLAY - held-out live-week replay on the PTR engine (REDO-R13, 2026-11-10 ~17:25Z; frozen file only; PRE-PROOF; depth-pollution caveat: the live book had ES/RTY levels, the replay reads the clean owned mbp-10 states)
API: `import r13_ptr_live as RL; D = RL.replay(lines, slips=(1.2, 0.57, 1.6)); S = RL.summarize(D, lines); RL.page(lines, out=path)` (code outputs/code/th_r13/r13_ptr_live.py; 38 features from th_ptr/ptr_feat.py over the 187 live trades, cache /mnt/l2/l2vast/_r13/trail/ptr_live/, 153 trades with a path >= 0.2 of target). Lines in the th_ptr grammar. $ per touched trade = lots x 20 x ((u_fire - slip) - live exit pts); the 86 live Targets (+$245.2k) and the 32 give-backs (-$48.3k) are from R13_TRAIL_LIVE_WEEK_PREP.md. Per-trade rows: /mnt/l2/l2vast/_r13/trail/live_week_replay_trades.csv.
Reading of the reference lines: a pct>=0.5 `take` fires on nearly every winner (it clips 25-30 of 31 K7 / 28 P7 targets), so the cost of clipping targets outweighs the give-backs saved for P7 and M7 (net negative at every slip) and is about break-even for K7 / A7; selective lines (ahead_rel >= 1.2 at pct >= 0.7) clip fewer targets. This is one week and 86 targets: placebo / null are not computed here.
clipped = fire before the live Target fill (cost = $ vs the live +target exit); caught = give-back trade (MFE >= 0.5 then exit below entry) where the line fires before the live exit (saved = $ vs the live exit); other = any other trade touched. slip = points vs the fill-second mid.
| line | slip | book_targets | targets_clipped | clip_cost_usd | book_giveback | giveback_usd | giveback_caught | saved_usd | other_trades | other_usd | net_usd |
|--|--|--|--|--|--|--|--|--|--|--|--|
| profit K7 * pct>=0.7 tot_rel>=1.2 tighten 30 win=5 persist=1 | 0.57 | 31 | 8 | -8383 | 13 | -11888 | 2 | 2182 | 1 | -246 | -6447 |
| profit K7 * pct>=0.7 tot_rel>=1.2 tighten 30 win=5 persist=1 | 1.20 | 31 | 8 | -8522 | 13 | -11888 | 2 | 2157 | 1 | -259 | -6624 |
| profit K7 * pct>=0.7 tot_rel>=1.2 tighten 30 win=5 persist=1 | 1.60 | 31 | 8 | -8610 | 13 | -11888 | 2 | 2141 | 1 | -267 | -6736 |
| profit P7 * pct>=0.5 ahead_rel>=1.5 take win=5 persist=1 | 0.57 | 28 | 25 | -55493 | 7 | -25059 | 5 | 39042 | 0 | 0 | -16451 |
| profit P7 * pct>=0.5 ahead_rel>=1.5 take win=5 persist=1 | 1.20 | 28 | 25 | -57005 | 7 | -25059 | 5 | 38702 | 0 | 0 | -18303 |
| profit P7 * pct>=0.5 ahead_rel>=1.5 take win=5 persist=1 | 1.60 | 28 | 25 | -57965 | 7 | -25059 | 5 | 38486 | 0 | 0 | -19479 |
| profit H7 * pct>=0.3 ahead_rel>=1.5 take win=5 persist=1 | 0.57 | 1 | 1 | -671 | 2 | -1974 | 2 | 3251 | 0 | 0 | 2579 |
| profit H7 * pct>=0.3 ahead_rel>=1.5 take win=5 persist=1 | 1.20 | 1 | 1 | -684 | 2 | -1974 | 2 | 3213 | 0 | 0 | 2529 |
| profit H7 * pct>=0.3 ahead_rel>=1.5 take win=5 persist=1 | 1.60 | 1 | 1 | -692 | 2 | -1974 | 2 | 3189 | 0 | 0 | 2497 |
| profit U7 * pct>=0.17 tot_rel>=1.5 take win=5 persist=1 | 0.57 | 3 | 1 | -809 | 0 | 0 | 0 | 0 | 2 | 9901 | 9092 |
| profit U7 * pct>=0.17 tot_rel>=1.5 take win=5 persist=1 | 1.20 | 3 | 1 | -822 | 0 | 0 | 0 | 0 | 2 | 9775 | 8953 |
| profit U7 * pct>=0.17 tot_rel>=1.5 take win=5 persist=1 | 1.60 | 3 | 1 | -830 | 0 | 0 | 0 | 0 | 2 | 9695 | 8865 |
| profit K7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1 | 0.57 | 31 | 24 | -8942 | 13 | -11888 | 4 | 6107 | 1 | 316 | -2519 |
| profit K7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1 | 1.20 | 31 | 24 | -9295 | 13 | -11888 | 4 | 6056 | 1 | 303 | -2935 |
| profit K7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1 | 1.60 | 31 | 24 | -9518 | 13 | -11888 | 4 | 6025 | 1 | 296 | -3198 |
| profit M7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1 | 0.57 | 13 | 9 | -3787 | 4 | -4682 | 2 | 3192 | 1 | 29 | -566 |
| profit M7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1 | 1.20 | 13 | 9 | -3938 | 4 | -4682 | 2 | 3167 | 1 | 16 | -755 |
| profit M7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1 | 1.60 | 13 | 9 | -4034 | 4 | -4682 | 2 | 3151 | 1 | 8 | -875 |
| profit P7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1 | 0.57 | 28 | 25 | -40735 | 7 | -25059 | 2 | 18435 | 0 | 0 | -22301 |
| profit P7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1 | 1.20 | 28 | 25 | -42248 | 7 | -25059 | 2 | 18296 | 0 | 0 | -23952 |
| profit P7 * pct>=0.7 ahead_rel>=1.2 take win=5 persist=1 | 1.60 | 28 | 25 | -43207 | 7 | -25059 | 2 | 18208 | 0 | 0 | -24999 |
| profit K7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 0.57 | 31 | 30 | -18969 | 13 | -11888 | 13 | 20934 | 1 | 1 | 1966 |
| profit K7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 1.20 | 31 | 30 | -19410 | 13 | -11888 | 13 | 20745 | 1 | -12 | 1323 |
| profit K7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 1.60 | 31 | 30 | -19690 | 13 | -11888 | 13 | 20625 | 1 | -20 | 916 |
| profit P7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 0.57 | 28 | 27 | -72896 | 7 | -25059 | 5 | 42012 | 0 | 0 | -30884 |
| profit P7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 1.20 | 28 | 27 | -74547 | 7 | -25059 | 5 | 41646 | 0 | 0 | -32900 |
| profit P7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 1.60 | 28 | 27 | -75594 | 7 | -25059 | 5 | 41414 | 0 | 0 | -34180 |
| profit M7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 0.57 | 13 | 13 | -9729 | 4 | -4682 | 4 | 8444 | 1 | -191 | -1476 |
| profit M7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 1.20 | 13 | 13 | -9943 | 4 | -4682 | 4 | 8368 | 1 | -204 | -1779 |
| profit M7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 1.60 | 13 | 13 | -10079 | 4 | -4682 | 4 | 8320 | 1 | -212 | -1971 |
| profit A7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 0.57 | 7 | 7 | -3725 | 4 | -2485 | 4 | 4879 | 1 | 104 | 1258 |
| profit A7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 1.20 | 7 | 7 | -3813 | 4 | -2485 | 4 | 4829 | 1 | 91 | 1107 |
| profit A7 * pct>=0.5 pulled_mult>=10 take win=5 persist=1 | 1.60 | 7 | 7 | -3869 | 4 | -2485 | 4 | 4797 | 1 | 83 | 1011 |
