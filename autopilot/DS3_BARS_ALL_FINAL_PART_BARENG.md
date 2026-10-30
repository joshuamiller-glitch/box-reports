# DS3_BARS_ALL_FINAL - BAR-ENG part (live books); full tables in DS3_ENGINES_ON_BARS.md
One line per setup (PRE+X' selection, one recent look, per contract vs the native 1-min engine; MDE in brackets):
* ST: no bar type beats 1-min (2% of types beat it in both PRE and X'); best HA 15-min +1.4/+1.5 pooled, not registered.
* HM: no bar type; best 5-min +0.5/+2.5 (z 0.7); G5 refit: HM on HA 2-min pre-open +19.8 PRE vs refit 1-min, recent negative.
* WT: best on HA 15-min NY-AM (+5.6/+4.7 PRE/X'; L6M +0.7 [16], HOLD -1.7 [15]) - not confirmed.
* KB: 1-min (3-min frame) is best; no type beats it in ALL sessions (0%); registered G3 cells are against a negative control.
* SM: 1-min/10-min frame is best on average; "SM is better on bars X in pre-open" cells come from a control sample of n~40 and fail RC.
* PE: best candidate - 2,000-contract volume bars in NY-PM: +3.8 pts per contract vs 1-min in L6M and +2.9 in HOLD (MDE 14), CANDIDATE-RECENT only (DSR 0.09, RW p 0.99, placebo not distinguishable).
* MV, PB, DN: no bar type beats 1-min (0-8% of types in both windows); DN on 2,500-volume bars pre-open fails recent.
* PB7: best candidate - on Heikin-Ashi 2-minute bars in London: +3.8 L6M, +6.4 HOLD (MDE 21), CANDIDATE-RECENT only (DSR 0.13, RW p 0.89, stack corr -0.28, stack $/wk still negative in L3M).
* CRT, iFVG, O6, D6 session cells: not run (see Open items). Quant-layer header columns missing for every row (capacity, regime, 200-draw placebo rank): nothing is promoted.
