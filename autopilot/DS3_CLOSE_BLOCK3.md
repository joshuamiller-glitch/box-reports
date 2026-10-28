# DS3_CLOSE_BLOCK3 - T-CLOSE block 3 (3.8 cross-asset and other closes, 3.9 footprint, 3.10 L2) + RVW1 execution realism + fill-cost and capacity - D3CL1, 2026-10-27
Research only. Shared harness open2 (patched in-process, c3_patch.py; harness files untouched). NQ fees 4.84 RT (proxy); non-NQ fees per FEES.md with WEAK labels; verdict = lower tier of M / T for NQ-traded cells.

## Verdict
**Block 3: 0 PASS, 0 CANDIDATE, 276 DEAD** of 276 scored cells: NQ-traded cross-asset / footprint / L2 cells 0 PASS, 0 CANDIDATE, 180 DEAD (15 signals x 12 brackets in 8 groups CL19-CL26; only 4 of 360 cell-bases beat placebo (b)), and other-instrument close books 0 PASS, 0 CANDIDATE, 96 DEAD (16 instrument-family signals x 6 R-unit brackets in 4 groups OI1-OI4; 21 of 96 cells beat (b), all of them the VWAP-reversion family on US equity indices). Cumulative T-CLOSE after blocks 1-3: **0 PASS, 1 CANDIDATE (RVW1|F30), 660 DEAD** of 661 scored cells.
Key new facts: (1) the VWAP-reversion-into-the-close effect is real across the US equity-index futures (ES, YM, RTY: 6 of 6 brackets each beat (b) at rank >= .98) but not in CL, GC, SI, ZN, 6E; (2) **RVW1|F30 is execution-fragile**: with a 1-second entry delay the mapped-basis edge turns negative on HOLD, and with real quotes at 15:30 the tape-direct basis HOLD edge falls to about zero (+$62/wk); (3) un-blocking the old books still loses $2.1k/wk (block 2).

## RVW1|F30 execution realism (prereg TCLOSE_B3_EXEC, 11 cells; same events, fixed 10 lots; M = mapped conservative, T = tape-direct-style)
The quote tape was extended to 15:00-16:15 (from tables/NQ/1s, existing data) so the 15:30 entry now has real bid/ask/first-print (variant Q); the block-1 numbers used a no-quote fallback for T.
| variant | cell | basis | n valid | pts/trade (all signals) | WF own $/wk | HOLD own $/wk | 2023-24 $/wk | 2x-cost HOLD | stack d mean [CI] | d Sharpe | d maxDD | MDE |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fixed(block1) | F30 | M | 621 | +2.95 | +2,144 | +900 | +1,107 | -1,378 | +2,144 [560, 3,774] | +0.12 | -6,220 | 2,252 |
| fixed(block1) | F30 | T | 621 | +2.62 | +1,725 | +577 | +1,325 | -223 | +1,725 [53, 3,393] | +0.09 | -3,614 | 2,413 |
| fixed(block1) | BE10 | M | 621 | +4.14 | +3,286 | +2,582 | +1,415 | +1,613 | +3,286 [1,332, 5,501] | +0.19 | -9,262 | 2,948 |
| fixed(block1) | BE10 | T | 621 | +1.86 | +1,337 | +225 | +1,142 | -574 | +1,337 [-512, 3,264] | +0.06 | -3,173 | 2,720 |
| Q | F30 | M | 621 | +2.95 | +2,144 | +900 | +1,107 | -1,378 | +2,144 [560, 3,774] | +0.12 | -6,220 | 2,252 |
| Q | F30 | T | 621 | +2.23 | +1,396 | +62 | +1,292 | -738 | +1,396 [-238, 3,106] | +0.08 | -3,814 | 2,424 |
| Q | BE10 | M | 621 | +4.14 | +3,286 | +2,582 | +1,415 | +1,613 | +3,286 [1,332, 5,501] | +0.19 | -9,262 | 2,948 |
| Q | BE10 | T | 621 | +2.56 | +1,989 | +665 | +1,027 | -134 | +1,989 [-31, 4,089] | +0.12 | -3,423 | 2,926 |
| DELAY1s | F30 | M | 621 | +1.26 | +632 | -929 | +1,136 | -3,077 | +632 [-928, 2,237] | +0.04 | -224 | 2,323 |
| DELAY1s | F30 | T | 621 | +2.22 | +1,384 | +228 | +1,305 | -572 | +1,384 [-340, 3,115] | +0.07 | -3,664 | 2,474 |
| DELAY2s | F30 | M | 621 | +1.29 | +652 | -915 | +1,153 | -3,093 | +652 [-952, 2,299] | +0.03 | +26 | 2,338 |
| DELAY2s | F30 | T | 621 | +2.01 | +1,259 | -52 | +1,217 | -852 | +1,259 [-478, 2,948] | +0.07 | -3,114 | 2,459 |
| DELAY5s | F30 | M | 621 | +0.50 | +241 | -1,161 | +638 | -3,302 | +241 [-1,357, 1,764] | +0.01 | +526 | 2,277 |
| DELAY5s | F30 | T | 621 | +1.53 | +788 | -621 | +1,411 | -1,421 | +788 [-1,001, 2,497] | +0.05 | -3,214 | 2,409 |
| EXIT_155959 | F30X57599 | M | 621 | +2.99 | +2,130 | +852 | +1,245 | -1,434 | +2,130 [531, 3,766] | +0.12 | -6,665 | 2,245 |
| EXIT_155959 | F30X57599 | T | 621 | +2.31 | +1,424 | +80 | +1,410 | -720 | +1,424 [-242, 3,104] | +0.08 | -5,064 | 2,425 |
| EXIT_1600 | F30X57600 | M | 621 | +2.95 | +2,144 | +900 | +1,107 | -1,378 | +2,144 [560, 3,774] | +0.12 | -6,220 | 2,252 |
| EXIT_1600 | F30X57600 | T | 621 | +2.23 | +1,396 | +62 | +1,292 | -738 | +1,396 [-238, 3,106] | +0.08 | -3,814 | 2,424 |
| EXIT_160001 | F30X57601 | M | 621 | +3.17 | +2,219 | +919 | +1,428 | -1,359 | +2,219 [628, 3,851] | +0.12 | -7,420 | 2,248 |
| EXIT_160001 | F30X57601 | T | 621 | +2.53 | +1,532 | +131 | +1,646 | -669 | +1,532 [-131, 3,248] | +0.08 | -4,864 | 2,429 |
| EXIT_1614 | F30X58440 | M | 621 | +3.22 | +2,279 | +955 | +1,362 | -1,363 | +2,279 [682, 3,971] | +0.13 | -10,032 | 2,313 |
| EXIT_1614 | F30X58440 | T | 621 | +2.47 | +1,420 | -1 | +1,778 | -801 | +1,420 [-233, 3,109] | +0.08 | -6,414 | 2,432 |
| EXIT_161430 | F30X58470 | M | 621 | +3.14 | +2,259 | +922 | +1,211 | -1,397 | +2,259 [651, 3,952] | +0.13 | -9,732 | 2,315 |
| EXIT_161430 | F30X58470 | T | 621 | +2.41 | +1,406 | -7 | +1,651 | -807 | +1,406 [-266, 3,087] | +0.08 | -7,414 | 2,433 |
| LMT300 | F30 | M | 577 | +2.00 | +1,332 | +502 | +654 | -1,590 | +1,332 [-186, 2,836] | +0.08 | -11,471 | 2,116 |
| LMT300 | F30 | T | 577 | +3.32 | +2,270 | +1,597 | +986 | +856 | +2,270 [671, 3,896] | +0.13 | -15,311 | 2,282 |
Read: (a) with quotes (Q), basis M is unchanged by construction (entry at the bar open), basis T falls from +$1,725 to +$1,396/wk WF and **HOLD from +$577 to +$62/wk**, 2x-cost HOLD -$738; (b) **a 1-s delay costs basis M +$1.5k/wk WF and turns HOLD to -$929** (the M edge depends on filling at the 15:30:00 bar open; T already includes the 1-s delay, so it is flat in the delay), so the live NT8 market order at the 15:29 bar close (about 100-300 ms inside the next second) must fill at the open price to realise the M numbers; the directive's 5 / 50 / 150 ms are below the 1-s resolution of the path and are bounded by the 1-s result; (c) exit timing is irrelevant (15:59:59 / 16:00:00 / 16:00:01 / 16:14:00 / 16:14:30 settle all within +-$150/wk); (d) a resting limit at the touch (5 min, trade-through) fills 577 of 621 signals and gives M +$1,332 / T +$2,270/wk with HOLD +$502 / +$1,597 (adverse selection is small; the unfilled 44 are not random but the sample is the same weekly series). **Conclusion for the forward spec: use a resting limit at the touch with a 5-minute timeout (or a market order only if the 15:30:00 open fill is verified); the edge per trade is thin (+2.2 to +3.0 pts) and the 2x-cost HOLD mean is negative.**

## Fill cost by second and capacity (NQ mbp-10 book columns, medians over all days; strict RT cost in points = spread + ask impact + bid impact; program cost-index convention beside it)
Strict round-trip points (spread + both-side impact; impact steps 0.5 / 1.5 / 3 / 6 / 12 ticks by liquidity within 1 / 2 / 4 / 8 ticks):
| lots | 15:30:00 | 15:50:00 | 15:58:00 | 16:00:00 | 16:00:01 | 16:05:00 | 16:10:00 |
|---|---|---|---|---|---|---|---|
| 1 | 0.75 | 1.00 | 0.75 | 0.75 | 0.75 | 0.75 | 0.75 |
| 5 | 0.75 | 1.25 | 0.75 | 0.75 | 0.75 | 0.75 | 0.75 |
| 10 | 1.00 | 2.25 | 1.00 | 1.25 | 1.25 | 1.38 | 1.38 |
| 20 | 2.00 | 4.00 | 2.00 | 2.00 | 2.00 | 2.25 | 2.25 |
| 40 | 3.50 | 6.75 | 3.50 | 3.50 | 3.50 | 3.50 | 3.50 |
Program cost-index convention (spread + side-average impact), points:
| lots | 15:30:00 | 15:50:00 | 15:58:00 | 16:00:00 | 16:00:01 | 16:05:00 | 16:10:00 |
|---|---|---|---|---|---|---|---|
| 1 | 0.62 | 0.88 | 0.62 | 0.62 | 0.62 | 0.62 | 0.62 |
| 5 | 0.62 | 1.12 | 0.62 | 0.62 | 0.62 | 0.62 | 0.62 |
| 10 | 0.75 | 1.56 | 0.75 | 0.81 | 0.81 | 0.94 | 1.00 |
| 20 | 1.25 | 2.50 | 1.25 | 1.25 | 1.25 | 1.41 | 1.50 |
| 40 | 2.00 | 3.75 | 2.00 | 2.00 | 2.00 | 2.00 | 2.00 |
Reading: the touch spread is about 0.25 pt (1 tick) at 15:30, 15:58 and after 16:00; **15:50:00 is the thin/expensive second (10 lots cost 2.25 pts RT, 40 lots 6.75)** because the book thins around the NYSE publication. The 16:00:01-16:10 book is NOT thinner than 15:58 in the medians (the closing book keeps its depth in this table; p90 values in fillcost_by_second.csv). Capacity (largest clip in {1,5,10,20,40} whose extra RT cost over 1 lot stays below half the RVW1|F30 edge): 20 lots at 15:30 and 16:00 with the M edge (2.95 pts), 10 lots with the T-quote edge (2.23 pts); 16:05 10 lots. So R12k sizing (20 lots) sits at the capacity limit.

## NQ-traded cross-asset (3.8), footprint (3.9), L2 (3.10): all DEAD
Per-cell verdict matrix (worst of M/T; b# = bases, of 2, beating placebo (b) at 64 draws):
| signal | F15 | F30 | F60 | VWAP | DAYHL | T1600 | T1614 | H1805 | H0930 | STRAIL | BE10 | NOSTOP |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F1 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| F2 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| F3 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| L1 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| L2 | D/b0 | D/b0 | D/b0 | D/b1 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| L3 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| L4 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| X6E | D/b0 | D/b0 | D/b0 | D/b2 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| X6M | D/b1 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| XAG0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| XAG3 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| XRL | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| XRS | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| XZN | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
| XZS | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 | D/b0 |
- 3.8: XRS/XRL (NQ vs ES relative strength 15:00-15:29), XAG3/XAG0 (NQ day move with/without ES-RTY-YM agreement), XZN/XZS (ZN 15:00 bond-close pivot), X6E/X6M (6E drift): only X6E|VWAP (2 bases) and X6M|F15 (1 base) beat (b); nothing else; all fail beta and stack-add. The bond-equity hand-off at 15:00 and index leadership carry no tradable edge in the last hour at these thresholds. XAG0 n=49 (the directive's 0-of-3 gives 9).
- 3.9 footprint (F1/F2 20-min aggressor-delta share into 15:50, F3 1-s delta after 15:50:00, L4 sweep imbalance): nothing beats (b); the overnight F2|H0930 has the largest raw stack-add (+$5.8k/wk, d Sharpe +0.20) but is bracket-beta and loses (b) (rank .70).
- 3.10 L2 (L1 book imbalance at 15:50:00-15:50:29, L2 depth asymmetry 15:55-15:58, L3 pulled liquidity): nothing beats (b) except L2|VWAP on one basis; L2/L3 as confirmation columns on MOC5/MOC10 (PRE, descriptive, side-adjusted move 15:50:30 -> 16:00, pts):
| base | confirmation | group | n | mean signed move 15:50:30->16:00 (pts) [95% CI] |
|---|---|---|---|---|
| MOC5 | L1 | agree | 38 | +3.40 [-9.0, +15.8] |
| MOC5 | L1 | disagree | 29 | +4.85 [-11.4, +21.1] |
| MOC5 | L1 | no signal | 181 | +6.84 [+1.2, +12.5] |
| MOC5 | L4 | agree | 63 | +3.63 [-5.9, +13.1] |
| MOC5 | L4 | disagree | 4 | +26.25 [+15.6, +36.9] |
| MOC5 | L4 | no signal | 181 | +6.49 [+0.6, +12.3] |
| MOC5 | F3 | agree | 61 | +3.83 [-6.1, +13.8] |
| MOC5 | F3 | no signal | 187 | +6.81 [+1.2, +12.5] |
| MOC10 | L1 | agree | 19 | +13.13 [-3.8, +30.0] |
| MOC10 | L1 | disagree | 18 | +12.06 [-10.0, +34.1] |
| MOC10 | L1 | no signal | 113 | +9.29 [+1.3, +17.3] |
| MOC10 | L4 | agree | 40 | +6.64 [-7.4, +20.7] |
| MOC10 | L4 | no signal | 109 | +11.16 [+3.2, +19.1] |
| MOC10 | F3 | agree | 44 | +6.72 [-6.6, +20.1] |
| MOC10 | F3 | no signal | 106 | +11.52 [+3.5, +19.5] |
The book/footprint confirmations do NOT improve the MOC-reaction continuation (agreeing subsets are no better than the no-signal subset; CIs overlap broadly). EXEC-ONLY flags: L1-L3 need mbp-10 at runtime; L4 / F3 need NT8 ticks (aggressor + sweep); F1/F2 need 1-min bid/ask volume.
Best-of-N (harness) block-3 NQ family: best (b)-effect F3|H0930 +18.2 pts vs null p95 36.4 (M) / 37.6 (T): none clears. Supplementary per-bracket-class null (not a gate): M/FIX: XRL|F60 3.95 vs p95 10.97; M/STRUCT: X6E|VWAP 11.91 vs p95 33.62; M/TIME: XZS|NOSTOP 11.35 vs p95 15.67; M/OVN: F3|H0930 18.2 vs p95 29.99; M/TRAIL: XRL|STRAIL 5.63 vs p95 10.82.

## Other instruments at their own closes (traded in that instrument; conservative 1-min-bar basis; R6k sizing; no lock engine)
| instrument | family | n signals | trades/wk | brackets (of 6) beating placebo (b) | best d mean $/wk (WF) | best d Sharpe (WF) | best PRE own mean $/wk | fee grade |
|---|---|---|---|---|---|---|---|---|
| 6E | CN | 412 | 2.25 | 0 | -102 | -0.01 | -66 | 6E addendum (exchange fee WEAK); T-ASIM 1 tick/side |
| 6E | RV | 561 | 2.91 | 0 | -771 | -0.04 | -510 | 6E addendum (exchange fee WEAK); T-ASIM 1 tick/side |
| CL | CN | 447 | 2.39 | 0 | -31 | -0.00 | -55 | WEAK PROXY (ES value; no CL row, MCL row is the micro 2.08) |
| CL | RV | 610 | 3.12 | 2 | +267 | +0.01 | +1,158 | WEAK PROXY (ES value; no CL row, MCL row is the micro 2.08) |
| ES | CN | 438 | 2.39 | 0 | -26 | -0.00 | +19 | NT-published |
| ES | RV | 630 | 3.31 | 6 | +1,155 | +0.05 | +764 | NT-published |
| GC | CN | 446 | 2.36 | 0 | -54 | -0.00 | -134 | WEAK PROXY (ES value; no GC row) |
| GC | RV | 563 | 2.9 | 0 | -32 | +0.02 | -273 | WEAK PROXY (ES value; no GC row) |
| RTY | CN | 434 | 2.33 | 0 | +32 | +0.00 | +76 | WEAK PROXY (ES value; M2K row is the micro, not RTY) |
| RTY | RV | 608 | 3.13 | 6 | +448 | +0.02 | +967 | WEAK PROXY (ES value; M2K row is the micro, not RTY) |
| SI | CN | 441 | 2.37 | 0 | -189 | -0.01 | -171 | WEAK PROXY (ES value; no SI row; 2 ticks slip - thin 1-min volume) |
| SI | RV | 561 | 2.88 | 0 | -127 | -0.02 | -1,271 | WEAK PROXY (ES value; no SI row; 2 ticks slip - thin 1-min volume) |
| YM | CN | 439 | 2.42 | 0 | +91 | +0.00 | +175 | WEAK PROXY (ES value; no YM row) |
| YM | RV | 593 | 3.08 | 6 | +1,243 | +0.06 | +1,673 | WEAK PROXY (ES value; no YM row) |
| ZN | CN | 438 | 2.37 | 1 | -131 | -0.01 | +45 | WEAK PROXY (ES value; no ZN row; 1 tick = 1/64 pt) |
| ZN | RV | 596 | 3.09 | 0 | -3,247 | -0.18 | -3,500 | WEAK PROXY (ES value; no ZN row; 1 tick = 1/64 pt) |
Top equity-index VWAP-reversion cells (stack line vs LIVE stack; R-unit (b) effect; M-only concept does not apply, single conservative basis):
| cell | verdict | failed gates | trades/wk | PRE own $/wk | WF d mean $/wk | MDE $/wk | WF d Sharpe | WF d maxDD | (b) effect R / rank | HOLD $/wk | 2023-24 $/wk |
|---|---|---|---|---|---|---|---|---|---|---|---|
| YM-RV|B10 | DEAD | year_share,span2,best_of_N | 3.08 | +1,673 | +1,243 | 1,653 | +0.06 | +6,424 | +0.15 / 1.00 | +750 | -917 |
| YM-RV|TM | DEAD | beats_c,beats_beta,span2,best_of_N | 3.08 | +1,266 | +1,102 | 1,272 | +0.06 | +3,222 | +0.17 / 1.00 | +906 | -591 |
| ES-RV|TM | DEAD | beats_c,beats_beta,stack_add_pre,year_share,span2,best_of_N | 3.31 | +764 | +1,155 | 1,331 | +0.05 | +1,561 | +0.15 / 0.98 | +1,569 | -536 |
| YM-RV|B15 | DEAD | beats_beta,stack_add_pre,span2,best_of_N | 3.08 | +1,162 | +976 | 1,177 | +0.05 | +3,222 | +0.15 / 1.00 | +757 | -504 |
| YM-RV|VW | DEAD | beats_c,beats_beta,stack_add_pre,span2,best_of_N | 2.77 | +894 | +735 | 1,432 | +0.04 | +4,811 | +0.11 / 1.00 | +550 | -631 |
| ES-RV|B10 | DEAD | beats_c,stack_add_pre,cost2x_pre,year_share,span2,best_of_N | 3.31 | +674 | +931 | 1,632 | +0.04 | +2,055 | +0.12 / 1.00 | +1,200 | -627 |
| ES-RV|B15 | DEAD | beats_c,beats_beta,stack_add_pre,year_share,span2,best_of_N | 3.31 | +606 | +978 | 1,241 | +0.04 | +1,561 | +0.12 / 0.98 | +1,373 | -516 |
| ES-RV|VW | DEAD | beats_c,beats_beta,stack_add_pre,cost2x_pre,year_share,span2,best_of_N | 3.11 | +556 | +939 | 1,552 | +0.04 | +7,439 | +0.11 / 0.98 | +1,347 | -430 |
- Every equity-index RV cell beats (b) and mostly also (c)/(d) but dies on year share, 2023-04..2024-01 (negative for ES/YM/RTY: -$0.4k to -$0.9k/wk), stack-add CI and best-of-N. ES / YM / RTY RV weekly series correlate 0.55-0.70 with each other and 0.29-0.50 with NQ RVW1|F30: they are mostly the same factor, not independent evidence.
- Pooled equity-index closes sleeve (NQ RVW1|F30 M + ES + RTY + YM RV|B10 at R6k): stack-add WF +$4.26k/wk [CI 356, 8,404], d Sharpe +0.19, d maxDD +20.4k (worse), PRE +$6.3k, HOLD +$2.0k [CI -3,120, 6,808], 2023-24 -$0.7k; MDE $5.7k/wk: within noise and the drawdown is worse; this is a preview of the FINAL sleeve item, not a verdict. ES+RTY+YM only: +$2.1k/wk, d Sharpe +0.08.
- CL, GC, SI, ZN, 6E RV and CN: no edge (best d Sharpe <= +0.02; ZN RV is the worst, -$3.2k/wk). Continuation (CN) at the instrument close: nothing anywhere (YM CN d mean +$91/wk).
- Fee grades: RTY, YM, CL, GC, SI, ZN use the ES value 4.84 (WEAK PROXY, no FEES.md row); 6E 5.30 (exchange fee WEAK). A verdict on those would be capped at CANDIDATE; none reached it.

## Deviations and disclosures
1. The harness `o2_run.cell_gates` gained a `min_n` gate (>= 30 PRE trades) during the program (added by another agent; not by me). Block 1 was scored before it; block 2 and 3 include it. It can only remove CANDIDATEs; RVW1 (PRE trades > 200) is unaffected.
2. Prereg text for CL19-CL26 states "168 cells" in the best-of-N sentence; the actual family is 15 signals x 12 = 180 cells (ledger +180). Counting slip in the prereg text only.
3. Tape-conditioned signals (F3, L1-L4): placebo (b) anchors uniform 11:00-11:50 (the book tape exists only for 11:00-12:00 and 15:00-16:15); (b) entries use the fallback fill while the real entries use quote fills (T basis slightly different cost model). L2 thresholds (0.054 / 0.048 / 0.035 / 0.38) are the 70th percentile of |x| over all days (distribution only, no outcome).
4. Other-instrument books: conservative 1-min-bar fills (no tick/book data for these series), NO lock engine (one trade/day), R6k sizing, placebo comparisons in R units, (d) = (c) construction; the stack line adds the instrument's dollars to the live stack (no margin/concurrency model; the 50-contract cap does not bind because the stack is flat 15:00-16:54 but is not checked for 6E/CL cells at other clocks).
5. The time-tape for entries 15:00-15:45 (fallback in blocks 1-2) is replaced by real quotes only in the EXEC cells (variant Q); all block 1-3 screening results retain the declared fallback for 15:00-15:45 entries.
6. Latency 5 / 50 / 150 ms cannot be resolved on the 1-s path (the 100 ms tables were not used): bounded by the 1 s / 2 s / 5 s delays. Resting-limit and MOC-equivalent exits done for RVW1 only, not for every family.
7. As-of audits: block-3 NQ signals 15 x 60 days, 0 mismatches, controls flag all (audit_asof_b3.csv; other-instrument bars and 1-s tape arrays randomised at / after t_sig). The other-instrument books use only bars with index < anchor for the trigger by construction (the trigger reads index anchor-1); a poison audit was NOT run for c3_xi.
8. Holdout: one logged look per group CL19-26 (pre-holdout sha256 a1c9a2ef171f723f973667d90cb6d5737680f01bb2b68c8bae4009503693ad18) and OI1-4; HOLD read only after. Memory gate 32 GB respected, corepool slots, no kills/retries, no downloads, UNTOUCHED unread. The new extraction (tape_feat.npz) reads existing tables/NQ/1s only.

## Preregs (sha256 in DECISIONS.md before scoring)
- CL19: 26538403c7a16051031c21bfce55e2c4316cf250422575afc4dbc6fb1515aa01
- CL20: 56ad1e3cb17c49c02233bae146ce8bdd2eb5e9a2f82fd9ba7bf3a1790704b183
- CL21: 6d3f02951d34c30b59f879e2f7dbaafe26a6e5e5377534885f6189cee7f8af95
- CL22: aa5e26d631d7620fff4c551130c9a701b8b142aadf0436b5ce62eee087dd9da2
- CL23: 3d8a3f3e30d09d43e35efd42d95843497917bf2abc8073cd0f30e5838a5e9e33
- CL24: b9b0138bd8ac2264f60234d5c194571b1194e11be1952e8c43f8687d0af1a034
- CL25: 0b65c6235296954312512c8883ad5f86d87efb92a1a4d280d42d4a859979bcfc
- CL26: 93f26f762d8f11db70d950b384d6a884e1205419454fcb68589c4c375f987997
- OI1: 7277e0b95cb39a296ef40c01f2f843a6fe46960f2cc57a1a7e2dee899f9de6fb
- OI2: ae42b9e332bde41a9c04dbc86e1500f66da9d7e387b7866c0165c6b6fe40a5d9
- OI3: c2305c4ed9c319ed1334b0779e7b74354a98a024fbc577defbc94a159705414a
- OI4: a08e480a2201ae559cdcb87a994ee06529681de0184c9d495e9fcc7e7e02e04a
- EXEC: l2vast/ds3/prereg/TCLOSE_B3_EXEC_prereg.md (sha in .sha256 and DECISIONS.md).
Code: l2vast/ds3/code/close3/ (c3_extract, c3_signals3, c3_audit3, c3_prereg3, c3_run3, c3_final3, c3_b3_tables, c3_xi, c3_prereg_oi, c3_xi_run, c3_xi_fin, c3_exec, c3_fillcost, c3_conf); results l2vast/ds3/out/tclose_b1/ (cells_final_b3.csv, cells_oi_final.csv, exec_rvw1_*.csv, fillcost_by_second.csv, conf_columns_pre.csv, tape_feat.npz, xi/*.pkl); variant pickles out/topen_b2/grp_TCLOSE_B3.

## ETA for block 4 and DS3_CLOSE_FINAL
Block 4 = full section-4 grid (target x stop surface, structural targets, negative-R shapes) on the top 3 per family (candidates: RVW1/RVW2, RSI2DS, ES/YM RV), bars x order types on the top 5 (5-s / 15-s / 5-min / tick / range / Renko / volume bars need bar builders; resting-limit variants beyond RVW1), the learned close classifier 3.11 at 15:30 / 15:50, the robustness block on the top 10 (full surface, day-block bootstrap maxDD, VIX terciles, year split, fill sensitivity, cost sweep, capacity, mirror, correlation to every live book and to K4, concurrency stack line), K4 overlap + overnight margin step-up, the closes sleeve, the MOC-proxy validity table, then DS3_CLOSE_FINAL.md and DS3_SPEC_<recommended close book>.md: about 8-10 h of agent time (jobs are minutes each once slots are free).
