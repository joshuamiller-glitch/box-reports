# SZ_L - Family L cooldowns / chop pauses (T-SIZER-EXHAUST ADDENDUM 1)  generated 2026-11-09T16:36:19Z

PRE-PROOF, post-hoc, Shadow only, no PASS claims. FIRST-ORDER only (sz_core Z.score, all-weeks maxDD, objective b equal-mean = global scale to Q1-A L6M mean). Cooldowns are simulated sequentially on the S1B-COMB trade list: only outcomes of TAKEN trades with exit <= signal second feed a state; chop detectors use NQ 5-min bars with end <= signal second. First-order is NOT the verdict: re-entries, locks and state-cut firing are not re-simulated; top-5 are queued for the exact engine (static M table keyed by signal second).

cells scored 3717 of 3866 grid cells (cells with no change after lot rounding dropped). Family WF of the picking procedure (lowest trailing 26-week maxDD, monthly, purged): WF maxDD cut vs ref 51.6% (wf_ok=True). Prereg line in DECISIONS.md.

"removed P&L" = base P&L of the removed lots (negative = the pause skipped net losers). "first-after" = first non-removed trade of the same book right after a removed one: its mean P&L (positive = the pause is followed by winners = it skipped the move start). Live columns use the frozen blind week (187 trades, 2026-11-01..05); the 11-08/09 v1.5 bug cuts are excluded; live P&L is at live lots.

## Top 25 by ROBUST equal-mean maxDD cut = min(L6M, PRE, X-prime) of the equal-mean cut, all cells
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_chop | H=30 M=1 N=2 cond=rng60_3.0 eff=0.0 post=1.0 scope=exKB | 21.2/-36.7/22.8/24.6 | 243982 (165224) | 29.7/31.2 | 2735 | 20.76 | 16.1 | 375432 | 2465 / 238 | 0.30 | 1.00 | -34030 | 15870 / 5730 / 60770 | LEAD PRE-PROOF |
| 2 | L_chop | H=30 M=1 N=2 cond=rng60_3.0 eff=0.0 post=1.0 scope=ALL | 17.1/-15.3/32.0/23.5 | 249996 (165224) | 26.1/39.3 | 2727 | 19.75 | 26.9 | 449906 | 3952 / 191 | 0.31 | 1.00 | -46975 | 15870 / 5730 / 79305 | LEAD PRE-PROOF |
| 3 | L_chop | H=30 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=exKB | 23.0/10.4/29.1/30.8 | 218501 (165224) | 25.6/31.6 | 799 | 19.61 | 14.8 | 233905 | 2035 / 288 | 0.11 | 1.00 | -24912 | 10863 / 1398 / 42608 | LEAD PRE-PROOF |
| 4 | L_chop | H=30 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=ALL | 21.4/17.0/28.3/31.2 | 217170 (165224) | 24.3/30.9 | 847 | 19.27 | 16.8 | 248517 | 2425 / 265 | 0.13 | 1.00 | -27128 | 10863 / 1398 / 46205 | LEAD PRE-PROOF |
| 5 | L_chop | H=0 M=3 N=1 cond=rng30_3.0 eff=0.5 post=1.0 scope=exKB | 37.7/13.3/35.4/26.5 | 203486 (165224) | 34.2/31.7 | -1175 | 21.58 | 23.8 | 392446 | 2290 / 119 | 0.17 | 1.00 | -24415 | 28436 / 2271 / 62492 | LEAD PRE-PROOF |
| 6 | L_chop | H=0 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=exKB | 19.0/7.6/28.3/28.5 | 220344 (165224) | 21.7/30.7 | 767 | 18.63 | 13.4 | 231149 | 1930 / 290 | 0.12 | 1.00 | -24912 | 10863 / 1398 / 42608 | LEAD PRE-PROOF |
| 7 | L_chop | H=30 M=3 N=1 cond=rng30_2.0 eff=0.5 post=1.0 scope=ALL | 19.9/17.2/25.7/23.0 | 214628 (165224) | 21.5/27.2 | 432 | 18.09 | 14.4 | 255086 | 2284 / 119 | 0.09 | 1.00 | -21702 | 18487 / 592 / 45019 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 8 | L_chop | H=30 M=3 N=2 cond=rng30_3.0 eff=0.5 post=1.0 scope=ALL | 30.4/27.2/43.6/32.5 | 171754 (165224) | 21.2/36.1 | -2565 | 18.02 | 25.3 | 459975 | 2962 / 114 | 0.10 | 1.00 | -23426 | 26514 / 2271 / 61287 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 9 | L_chop | H=0 M=3 N=1 cond=rng30_3.0 eff=0.5 post=0.5 scope=ALL | 47.5/43.9/45.9/56.8 | 126181 (165224) | 23.0/20.6 | -6796 | 18.03 | 39.1 | 718110 | 2242 / 94 | 0.05 | 1.00 | -37680 | 31875 / 2271 / 83574 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 10 | L_chop | H=30 M=3 N=1 cond=rng30_3.0 eff=0.5 post=0.5 scope=ALL | 47.5/43.9/45.9/56.8 | 126181 (165224) | 23.0/20.6 | -6796 | 18.03 | 39.1 | 715881 | 2241 / 96 | 0.03 | 1.00 | -37680 | 31875 / 2271 / 83574 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 11 | L_sessloss | eff=0.0 n=2 sess=[1] state=stack | 21.9/-31.8/46.5/15.1 | 129348 (165224) | 26.7/49.8 | 1537 | 20.80 | 14.8 | 226207 | 1360 / 86 | 0.47 | 1.00 | -7225 | 19165 / 7160 / 41640 | LEAD PRE-PROOF |
| 12 | L_chop | H=30 M=3 N=1 cond=rng30_3.0 eff=0.5 post=1.0 scope=exKB | 40.1/13.9/38.6/27.7 | 180864 (165224) | 34.0/32.3 | -2017 | 21.51 | 24.3 | 428402 | 2275 / 95 | 0.06 | 1.00 | -23712 | 29139 / 2271 / 62492 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 13 | L_chop | H=0 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=ALL | 17.5/13.4/27.4/27.4 | 220338 (165224) | 20.2/29.9 | 770 | 18.28 | 15.3 | 239121 | 2295 / 271 | 0.19 | 1.00 | -27128 | 10863 / 1398 / 46205 | LEAD PRE-PROOF |
| 14 | L_chop | H=0 M=3 N=1 cond=rng30_3.0 eff=0.5 post=0.5 scope=exKB | 43.4/45.1/41.6/52.1 | 129479 (165224) | 22.2/19.9 | -5797 | 17.86 | 34.3 | 617447 | 1436 / 105 | 0.12 | 1.00 | -37261 | 31875 / 2271 / 78777 | LEAD PRE-PROOF |
| 15 | L_chop | H=30 M=3 N=1 cond=rng30_3.0 eff=0.5 post=0.5 scope=exKB | 43.4/45.1/41.6/52.1 | 129479 (165224) | 22.2/19.9 | -5797 | 17.86 | 34.3 | 615218 | 1435 / 108 | 0.15 | 1.00 | -37261 | 31875 / 2271 / 78777 | LEAD PRE-PROOF |
| 16 | L_chop | H=0 M=1 N=1 cond=rng30_3.0 eff=0.5 post=0.5 scope=ALL | 46.0/43.9/44.3/56.8 | 128409 (165224) | 22.3/19.8 | -6517 | 17.87 | 39.0 | 706104 | 2245 / 102 | 0.10 | 1.00 | -37680 | 31875 / 2271 / 83574 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 17 | L_chop | H=0 M=3 N=1 cond=rng30_3.0 eff=0.5 post=1.0 scope=ALL | 42.4/13.9/38.9/25.4 | 202257 (165224) | 38.0/34.2 | -1683 | 24.75 | 27.7 | 473212 | 2978 / 117 | 0.10 | 1.00 | -25484 | 28436 / 2271 / 67290 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 18 | L_chop | H=30 M=1 N=1 cond=rng30_3.0 eff=0.5 post=0.5 scope=ALL | 47.5/43.9/44.3/56.8 | 127522 (165224) | 24.2/19.6 | -6552 | 18.33 | 39.0 | 701979 | 2242 / 103 | 0.05 | 1.00 | -37680 | 31875 / 2271 / 83574 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 19 | L_chop | H=30 M=3 N=2 cond=rng30_3.0 eff=0.5 post=1.0 scope=exKB | 26.7/26.7/40.1/34.7 | 176958 (165224) | 19.3/34.0 | -1992 | 17.60 | 21.7 | 386338 | 2329 / 108 | 0.11 | 1.00 | -21610 | 26514 / 2271 / 56490 | LEAD PRE-PROOF |
| 20 | L_sessloss | eff=0.0 n=3 sess=[1] state=stack | 16.9/-45.2/38.4/21.8 | 179491 (165224) | 19.1/40.1 | 652 | 18.83 | 11.0 | 97705 | 1030 / 42 | 0.43 | 1.00 | 2395 | 13765 / 4775 / 22445 | LEAD PRE-PROOF |
| 21 | L_chop | H=30 M=3 N=1 cond=rng30_3.0 eff=0.5 post=1.0 scope=ALL | 41.6/14.6/42.1/28.5 | 179636 (165224) | 33.8/34.4 | -2561 | 21.47 | 28.3 | 506086 | 2966 / 99 | 0.06 | 1.00 | -24782 | 29139 / 2271 / 67290 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 22 | L_chop | H=30 M=3 N=1 cond=rng30_2.5 eff=0.5 post=1.0 scope=ALL | 30.7/18.4/34.7/35.2 | 155010 (165224) | 18.8/23.5 | -3187 | 17.49 | 22.3 | 415083 | 2887 / 130 | 0.05 | 1.00 | -26221 | 24619 / 2271 / 60094 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 23 | L_chop | H=30 M=1 N=2 cond=er_0.15 eff=0.5 post=1.0 scope=exKB | 13.9/6.4/14.3/18.1 | 184533 (165224) | 18.7/19.0 | 1357 | 18.42 | 8.0 | -51272 | 1308 / 208 | 0.27 | 1.00 | -5299 | 9836 / -0 / 18601 | LEAD PRE-PROOF |
| 24 | L_chop | H=30 M=3 N=1 cond=rng30_2.0 eff=0.5 post=1.0 scope=exKB | 15.8/11.9/22.8/23.5 | 215103 (165224) | 18.7/25.5 | 785 | 17.47 | 12.1 | 218853 | 1840 / 111 | 0.15 | 1.00 | -21507 | 18487 / 592 / 42619 | LEAD PRE-PROOF |
| 25 | L_chop_book | H=0 M=3 N=2 cond=rng60_3.5 eff=0.0 post=1.0 scope=PE | 14.9/-32.3/33.2/32.7 | 209233 (165224) | 18.7/36.1 | 1026 | 17.94 | 8.3 | 284103 | 1152 / 408 | 0.30 | 1.00 | -61965 | 22445 / -0 / 90020 | LEAD PRE-PROOF |

## Top 15 with cut L6M, PRE >0 and X' > -3 (equal-mean) 
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_chop | H=30 M=1 N=2 cond=rng60_3.0 eff=0.0 post=1.0 scope=exKB | 21.2/-36.7/22.8/24.6 | 243982 (165224) | 29.7/31.2 | 2735 | 20.76 | 16.1 | 375432 | 2465 / 238 | 0.30 | 1.00 | -34030 | 15870 / 5730 / 60770 | LEAD PRE-PROOF |
| 2 | L_chop | H=30 M=1 N=2 cond=rng60_3.0 eff=0.0 post=1.0 scope=ALL | 17.1/-15.3/32.0/23.5 | 249996 (165224) | 26.1/39.3 | 2727 | 19.75 | 26.9 | 449906 | 3952 / 191 | 0.31 | 1.00 | -46975 | 15870 / 5730 / 79305 | LEAD PRE-PROOF |
| 3 | L_chop | H=30 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=exKB | 23.0/10.4/29.1/30.8 | 218501 (165224) | 25.6/31.6 | 799 | 19.61 | 14.8 | 233905 | 2035 / 288 | 0.11 | 1.00 | -24912 | 10863 / 1398 / 42608 | LEAD PRE-PROOF |
| 4 | L_chop | H=30 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=ALL | 21.4/17.0/28.3/31.2 | 217170 (165224) | 24.3/30.9 | 847 | 19.27 | 16.8 | 248517 | 2425 / 265 | 0.13 | 1.00 | -27128 | 10863 / 1398 / 46205 | LEAD PRE-PROOF |
| 5 | L_chop | H=0 M=3 N=1 cond=rng30_3.0 eff=0.5 post=1.0 scope=exKB | 37.7/13.3/35.4/26.5 | 203486 (165224) | 34.2/31.7 | -1175 | 21.58 | 23.8 | 392446 | 2290 / 119 | 0.17 | 1.00 | -24415 | 28436 / 2271 / 62492 | LEAD PRE-PROOF |
| 6 | L_chop | H=0 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=exKB | 19.0/7.6/28.3/28.5 | 220344 (165224) | 21.7/30.7 | 767 | 18.63 | 13.4 | 231149 | 1930 / 290 | 0.12 | 1.00 | -24912 | 10863 / 1398 / 42608 | LEAD PRE-PROOF |
| 7 | L_chop | H=30 M=3 N=1 cond=rng30_2.0 eff=0.5 post=1.0 scope=ALL | 19.9/17.2/25.7/23.0 | 214628 (165224) | 21.5/27.2 | 432 | 18.09 | 14.4 | 255086 | 2284 / 119 | 0.09 | 1.00 | -21702 | 18487 / 592 / 45019 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 8 | L_chop | H=30 M=3 N=2 cond=rng30_3.0 eff=0.5 post=1.0 scope=ALL | 30.4/27.2/43.6/32.5 | 171754 (165224) | 21.2/36.1 | -2565 | 18.02 | 25.3 | 459975 | 2962 / 114 | 0.10 | 1.00 | -23426 | 26514 / 2271 / 61287 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 9 | L_chop | H=30 M=3 N=1 cond=rng30_3.0 eff=0.5 post=0.5 scope=ALL | 47.5/43.9/45.9/56.8 | 126181 (165224) | 23.0/20.6 | -6796 | 18.03 | 39.1 | 715881 | 2241 / 96 | 0.03 | 1.00 | -37680 | 31875 / 2271 / 83574 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 10 | L_chop | H=0 M=3 N=1 cond=rng30_3.0 eff=0.5 post=0.5 scope=ALL | 47.5/43.9/45.9/56.8 | 126181 (165224) | 23.0/20.6 | -6796 | 18.03 | 39.1 | 718110 | 2242 / 94 | 0.05 | 1.00 | -37680 | 31875 / 2271 / 83574 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 11 | L_sessloss | eff=0.0 n=2 sess=[1] state=stack | 21.9/-31.8/46.5/15.1 | 129348 (165224) | 26.7/49.8 | 1537 | 20.80 | 14.8 | 226207 | 1360 / 86 | 0.47 | 1.00 | -7225 | 19165 / 7160 / 41640 | LEAD PRE-PROOF |
| 12 | L_chop | H=30 M=3 N=1 cond=rng30_3.0 eff=0.5 post=1.0 scope=exKB | 40.1/13.9/38.6/27.7 | 180864 (165224) | 34.0/32.3 | -2017 | 21.51 | 24.3 | 428402 | 2275 / 95 | 0.06 | 1.00 | -23712 | 29139 / 2271 / 62492 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 13 | L_chop | H=0 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=ALL | 17.5/13.4/27.4/27.4 | 220338 (165224) | 20.2/29.9 | 770 | 18.28 | 15.3 | 239121 | 2295 / 271 | 0.19 | 1.00 | -27128 | 10863 / 1398 / 46205 | LEAD PRE-PROOF |
| 14 | L_chop | H=0 M=3 N=1 cond=rng30_3.0 eff=0.5 post=0.5 scope=exKB | 43.4/45.1/41.6/52.1 | 129479 (165224) | 22.2/19.9 | -5797 | 17.86 | 34.3 | 617447 | 1436 / 105 | 0.12 | 1.00 | -37261 | 31875 / 2271 / 78777 | LEAD PRE-PROOF |
| 15 | L_chop | H=30 M=3 N=1 cond=rng30_3.0 eff=0.5 post=0.5 scope=exKB | 43.4/45.1/41.6/52.1 | 129479 (165224) | 22.2/19.9 | -5797 | 17.86 | 34.3 | 615218 | 1435 / 108 | 0.15 | 1.00 | -37261 | 31875 / 2271 / 78777 | LEAD PRE-PROOF |

## Post-loss cooldowns (stop / cut / loss / N-loss streak; same side / both / session; book or stack; W 5-120 min)  (528 cells; best by robust equal-mean cut)
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_postloss | W=120 eff=0.5 n=2 scope=ALL target=both trig=nloss tscope=stack | 29.1/5.7/50.3/26.4 | 169036 (165224) | 21.3/44.8 | -2231 | 18.53 | 19.8 | 144281 | 2246 / 259 | 0.07 | 1.00 | -29415 | 22983 / 1679 / 59572 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 2 | L_postloss | W=30 eff=0.0 n=1 scope=PE target=side trig=loss tscope=book | 9.4/-7.9/15.8/2.3 | 231958 (165224) | 22.5/28.0 | 3955 | 19.66 | 1.9 | -78667 | 386 / 294 | 0.21 | 1.00 | -12740 | 12455 / -0 / 25195 | LEAD PRE-PROOF |
| 3 | L_postloss | W=60 eff=0.0 n=1 scope=ALL target=both trig=stop tscope=book | 16.0/-8.4/36.8/15.6 | 169978 (165224) | 16.6/37.2 | 181 | 18.52 | 9.3 | -145679 | 1645 / 107 | 0.07 | 1.00 | 0 | -0 / -0 / 0 | CANDIDATE (own-p only; family p 1.00) PRE-PROOF |
| 4 | L_postloss | W=15 eff=0.0 n=3 scope=ALL target=both trig=nloss tscope=stack | 12.4/-5.7/24.5/12.1 | 202084 (165224) | 16.4/28.0 | 1217 | 19.52 | 11.6 | -27521 | 2194 / 89 | 0.21 | 1.00 | -52700 | 7070 / 715 / 63615 | LEAD PRE-PROOF |
| 5 | L_postloss | W=30 eff=0.0 n=1 scope=PE target=side trig=stopcut tscope=book | 9.4/-7.9/15.8/2.3 | 231958 (165224) | 22.0/27.5 | 3785 | 19.54 | 1.9 | -74403 | 385 / 273 | 0.23 | 1.00 | -12740 | 12455 / -0 / 25195 | LEAD PRE-PROOF |
| 6 | L_postloss | W=60 eff=0.0 n=1 scope=ALL target=side trig=loss tscope=book | 17.4/-11.7/34.3/7.2 | 213698 (165224) | 24.6/40.0 | 2237 | 20.20 | 12.1 | 16996 | 2115 / 142 | 0.14 | 1.00 | -21395 | 21700 / -0 / 52825 | LEAD PRE-PROOF |
| 7 | L_postloss | W=60 eff=0.0 n=1 scope=ALL target=side trig=stopcut tscope=book | 17.4/-11.7/34.3/7.2 | 213698 (165224) | 23.9/39.5 | 2018 | 20.03 | 12.1 | 22458 | 2115 / 139 | 0.12 | 1.00 | -21395 | 21700 / -0 / 52825 | LEAD PRE-PROOF |
| 8 | L_postloss | W=60 eff=0.0 n=1 scope=PE target=side trig=loss tscope=book | 8.7/-32.7/36.7/4.5 | 222100 (165224) | 18.1/43.3 | 2709 | 18.61 | 2.9 | -27989 | 544 / 394 | 0.20 | 1.00 | -8325 | 21700 / -0 / 30025 | LEAD PRE-PROOF |

## Day-loss -> rest of day  (20 cells; best by robust equal-mean cut)
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_dayloss | Runit=1200.0 dayX=6 dscope=book eff=0.5 scope=ALL | 3.7/-4.9/1.4/-3.1 | 159690 (165224) | 1.3/-1.1 | -528 | 14.39 | 3.0 | 56652 | 380 / 261 | 0.72 | 1.00 | -5398 | 1804 / -0 / 7202 | LEAD PRE-PROOF |
| 2 | L_dayloss | Runit=1200.0 dayX=6 dscope=book eff=0.5 scope=PE | 3.7/-6.0/1.4/-3.1 | 158501 (165224) | 1.1/-1.3 | -575 | 14.36 | 3.0 | 57736 | 371 / 227 | 0.69 | 1.00 | -5398 | 1804 / -0 / 7202 | LEAD PRE-PROOF |
| 3 | L_dayloss | Runit=1200.0 dayX=6 dscope=book eff=0.0 scope=ALL | 36.6/-20.0/12.3/-16.0 | 192138 (165224) | 37.0/12.8 | 128 | 22.55 | 5.5 | 118023 | 307 / 342 | 0.73 | 1.00 | -16975 | 31025 / -0 / 48000 | LEAD PRE-PROOF |
| 4 | L_dayloss | Runit=1200.0 dayX=6 dscope=book eff=0.0 scope=PE | 33.7/-22.4/12.3/-16.0 | 190959 (165224) | 33.9/12.6 | 81 | 21.49 | 5.4 | 126039 | 296 / 275 | 0.69 | 1.00 | -16975 | 31025 / -0 / 48000 | LEAD PRE-PROOF |
| 5 | L_dayloss | Runit=1200.0 dayX=4 dscope=book eff=0.5 scope=PE | 5.1/-6.4/-1.2/-9.9 | 162343 (165224) | -1.1/-7.8 | -1712 | 18.01 | 4.7 | 105138 | 522 / 188 | 0.88 | 1.00 | -9490 | 2507 / -0 / 11997 | no |
| 6 | L_dayloss | Runit=1200.0 dayX=4 dscope=book eff=0.5 scope=ALL | 5.1/-6.5/-2.1/-8.9 | 155950 (165224) | -2.4/-10.2 | -2064 | 17.77 | 4.9 | 118221 | 561 / 252 | 0.91 | 1.00 | -9490 | 2507 / -0 / 11997 | no |
| 7 | L_dayloss | Runit=1200.0 dayX=3 dscope=book eff=0.5 scope=ALL | 3.2/-11.9/-3.8/-25.6 | 148788 (165224) | -2.7/-10.2 | -1341 | 14.84 | 6.6 | 164608 | 750 / 253 | 0.97 | 1.00 | -7255 | 4742 / -0 / 11997 | no |
| 8 | L_dayloss | Runit=1200.0 dayX=3 dscope=book eff=0.5 scope=PE | 3.7/-7.0/-2.9/-28.6 | 154660 (165224) | -0.9/-7.9 | -1073 | 15.10 | 6.1 | 144238 | 651 / 220 | 0.93 | 1.00 | -7255 | 4742 / -0 / 11997 | no |

## Chop detector pause, stack/exKB  (2592 cells; best by robust equal-mean cut)
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_chop | H=30 M=1 N=2 cond=rng60_3.0 eff=0.0 post=1.0 scope=exKB | 21.2/-36.7/22.8/24.6 | 243982 (165224) | 29.7/31.2 | 2735 | 20.76 | 16.1 | 375432 | 2465 / 238 | 0.30 | 1.00 | -34030 | 15870 / 5730 / 60770 | LEAD PRE-PROOF |
| 2 | L_chop | H=30 M=1 N=2 cond=rng60_3.0 eff=0.0 post=1.0 scope=ALL | 17.1/-15.3/32.0/23.5 | 249996 (165224) | 26.1/39.3 | 2727 | 19.75 | 26.9 | 449906 | 3952 / 191 | 0.31 | 1.00 | -46975 | 15870 / 5730 / 79305 | LEAD PRE-PROOF |
| 3 | L_chop | H=30 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=exKB | 23.0/10.4/29.1/30.8 | 218501 (165224) | 25.6/31.6 | 799 | 19.61 | 14.8 | 233905 | 2035 / 288 | 0.11 | 1.00 | -24912 | 10863 / 1398 / 42608 | LEAD PRE-PROOF |
| 4 | L_chop | H=30 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=ALL | 21.4/17.0/28.3/31.2 | 217170 (165224) | 24.3/30.9 | 847 | 19.27 | 16.8 | 248517 | 2425 / 265 | 0.13 | 1.00 | -27128 | 10863 / 1398 / 46205 | LEAD PRE-PROOF |
| 5 | L_chop | H=0 M=3 N=1 cond=rng30_3.0 eff=0.5 post=1.0 scope=exKB | 37.7/13.3/35.4/26.5 | 203486 (165224) | 34.2/31.7 | -1175 | 21.58 | 23.8 | 392446 | 2290 / 119 | 0.17 | 1.00 | -24415 | 28436 / 2271 / 62492 | LEAD PRE-PROOF |
| 6 | L_chop | H=0 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=exKB | 19.0/7.6/28.3/28.5 | 220344 (165224) | 21.7/30.7 | 767 | 18.63 | 13.4 | 231149 | 1930 / 290 | 0.12 | 1.00 | -24912 | 10863 / 1398 / 42608 | LEAD PRE-PROOF |
| 7 | L_chop | H=30 M=3 N=1 cond=rng30_2.0 eff=0.5 post=1.0 scope=ALL | 19.9/17.2/25.7/23.0 | 214628 (165224) | 21.5/27.2 | 432 | 18.09 | 14.4 | 255086 | 2284 / 119 | 0.09 | 1.00 | -21702 | 18487 / 592 / 45019 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 8 | L_chop | H=30 M=3 N=2 cond=rng30_3.0 eff=0.5 post=1.0 scope=ALL | 30.4/27.2/43.6/32.5 | 171754 (165224) | 21.2/36.1 | -2565 | 18.02 | 25.3 | 459975 | 2962 / 114 | 0.10 | 1.00 | -23426 | 26514 / 2271 / 61287 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |

## Chop detector pause per book  (312 cells; best by robust equal-mean cut)
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_chop_book | H=0 M=3 N=2 cond=rng60_3.5 eff=0.0 post=1.0 scope=PE | 14.9/-32.3/33.2/32.7 | 209233 (165224) | 18.7/36.1 | 1026 | 17.94 | 8.3 | 284103 | 1152 / 408 | 0.30 | 1.00 | -61965 | 22445 / -0 / 90020 | LEAD PRE-PROOF |
| 2 | L_chop_book | H=0 M=3 N=2 cond=rng60_3.5 eff=0.5 post=1.0 scope=PE | 8.7/-1.9/16.8/29.9 | 223168 (165224) | 14.5/22.2 | 1529 | 17.07 | 7.5 | 80314 | 1105 / 405 | 0.34 | 1.00 | -26540 | 10863 / -0 / 40208 | LEAD PRE-PROOF |
| 3 | L_chop_book | H=0 M=3 N=2 cond=rng30_3.0 eff=0.5 post=1.0 scope=PE | 12.2/19.1/32.4/27.8 | 170166 (165224) | 4.7/26.6 | -1719 | 14.90 | 13.8 | 230833 | 1322 / 217 | 0.47 | 1.00 | -23570 | 26514 / -0 / 52890 | LEAD PRE-PROOF |
| 4 | L_chop_book | H=0 M=3 N=2 cond=er_0.25 eff=0.0 post=1.0 scope=SM | 7.6/-4.1/4.4/29.4 | 179878 (165224) | 7.5/4.3 | -25 | 18.91 | 3.7 | 74384 | 331 / 253 | 0.94 | 1.00 | -2280 | -0 / -0 / 3600 | LEAD PRE-PROOF |
| 5 | L_chop_book | H=0 M=3 N=2 cond=twap_3 eff=0.0 post=1.0 scope=SM | 1.6/-2.4/2.7/8.4 | 180054 (165224) | 4.1/5.2 | 578 | 15.18 | 1.0 | 38542 | 172 / 292 | 0.52 | 1.00 | 0 | -0 / -0 / 0 | LEAD PRE-PROOF |
| 6 | L_chop_book | H=0 M=3 N=2 cond=rng60_3.0 eff=0.5 post=1.0 scope=PE | 2.2/1.8/11.4/18.3 | 186203 (165224) | 2.9/12.0 | 153 | 15.03 | 3.9 | 62974 | 688 / 368 | 0.40 | 1.00 | -12663 | 8175 / -0 / 22211 | LEAD PRE-PROOF |
| 7 | L_chop_book | H=0 M=3 N=2 cond=fb_7 eff=0.0 post=1.0 scope=SM | 5.4/-4.6/1.5/5.1 | 170913 (165224) | 5.9/2.1 | 132 | 15.86 | 0.4 | 30681 | 86 / -261 | 0.48 | 1.00 | 1485 | -0 / -0 / 2405 | LEAD PRE-PROOF |
| 8 | L_chop_book | H=0 M=3 N=2 cond=er_0.20 eff=0.0 post=1.0 scope=SM | 10.6/-2.4/5.6/25.9 | 178849 (165224) | 7.2/2.0 | -986 | 18.81 | 3.0 | 12490 | 350 / 431 | 0.80 | 1.00 | -2280 | -0 / -0 / 3600 | LEAD PRE-PROOF |

## Whipsaw (direction flips) pause  (72 cells; best by robust equal-mean cut)
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_whip | H=15 W=30 eff=0.0 k=1 scope=exKB | 0.1/-0.5/0.2/7.1 | 172040 (165224) | 6.6/6.8 | 1703 | 16.94 | 2.3 | -105024 | 444 / 17 | 0.63 | 1.00 | -225 | 90 / 2155 / 6005 | LEAD PRE-PROOF |
| 2 | L_whip | H=15 W=30 eff=0.0 k=1 scope=ALL | 0.5/-1.7/-2.8/9.1 | 174878 (165224) | 7.8/4.8 | 1930 | 17.16 | 3.3 | -89256 | 634 / 8 | 0.82 | 1.00 | 1715 | 90 / 2155 / 7205 | no |
| 3 | L_whip | H=0 W=30 eff=0.0 k=1 scope=exKB | -0.7/-0.5/-1.9/8.5 | 193038 (165224) | 5.0/3.9 | 1406 | 16.02 | 2.0 | -105287 | 383 / -7 | 0.69 | 1.00 | -1225 | -0 / 1365 / 4805 | no |
| 4 | L_whip | H=30 W=30 eff=0.0 k=1 scope=exKB | 0.1/1.5/-3.5/3.5 | 161615 (165224) | 6.6/3.3 | 1708 | 16.94 | 3.0 | -67824 | 537 / 104 | 0.85 | 1.00 | -225 | 90 / 2155 / 6005 | no |
| 5 | L_whip | H=60 W=60 eff=0.0 k=2 scope=ALL | 9.6/-8.9/23.6/2.1 | 148347 (165224) | 10.4/24.3 | 211 | 16.70 | 3.0 | 62137 | 431 / 210 | 0.09 | 1.00 | -3185 | -0 / -0 / 4800 | LEAD PRE-PROOF |
| 6 | L_whip | H=0 W=30 eff=0.0 k=1 scope=ALL | 1.2/-1.7/-4.9/9.5 | 195080 (165224) | 6.9/1.2 | 1445 | 16.35 | 2.8 | -90465 | 554 / -8 | 0.89 | 1.00 | 90 | -0 / 1365 / 6005 | no |
| 7 | L_whip | H=15 W=30 eff=0.5 k=1 scope=exKB | 0.7/0.0/-1.7/1.3 | 167709 (165224) | 3.4/1.1 | 682 | 16.38 | 0.8 | -45358 | 161 / -180 | 0.82 | 1.00 | -507 | 36 / -0 / 1202 | no |
| 8 | L_whip | H=15 W=30 eff=0.5 k=1 scope=ALL | 0.7/0.0/-1.7/1.3 | 167659 (165224) | 3.4/1.1 | 680 | 16.38 | 0.8 | -38930 | 170 / -156 | 0.83 | 1.00 | -507 | 36 / -0 / 1202 | no |

## Session-level: losses in session -> rest of session  (32 cells; best by robust equal-mean cut)
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_sessloss | eff=0.0 n=2 sess=[1] state=stack | 21.9/-31.8/46.5/15.1 | 129348 (165224) | 26.7/49.8 | 1537 | 20.80 | 14.8 | 226207 | 1360 / 86 | 0.47 | 1.00 | -7225 | 19165 / 7160 / 41640 | LEAD PRE-PROOF |
| 2 | L_sessloss | eff=0.0 n=3 sess=[1] state=stack | 16.9/-45.2/38.4/21.8 | 179491 (165224) | 19.1/40.1 | 652 | 18.83 | 11.0 | 97705 | 1030 / 42 | 0.43 | 1.00 | 2395 | 13765 / 4775 / 22445 | LEAD PRE-PROOF |
| 3 | L_sessloss | eff=0.5 n=3 sess=[1] state=stack | 8.5/-10.1/26.4/8.8 | 183950 (165224) | 14.1/31.0 | 1534 | 17.74 | 5.0 | 27570 | 668 / 110 | 0.22 | 1.00 | 4818 | 6553 / 592 / 3602 | LEAD PRE-PROOF |
| 4 | L_sessloss | eff=0.5 n=2 sess=[1] state=stack | 15.2/-9.1/27.4/5.2 | 161234 (165224) | 17.5/29.3 | 638 | 18.46 | 6.7 | 77822 | 905 / 134 | 0.13 | 1.00 | 507 | 9253 / 1464 / 11486 | LEAD PRE-PROOF |
| 5 | L_sessloss | eff=0.0 n=3 sess=[1] state=book | 12.2/-11.8/28.1/0.0 | 189577 (165224) | 17.1/32.1 | 1269 | 16.76 | 2.8 | -14585 | 281 / -42 | 0.02 | 1.00 | -6205 | 1875 / 735 / 9600 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 6 | L_sessloss | eff=0.5 n=2 sess=[3] state=stack | 1.4/1.4/4.4/5.5 | 191054 (165224) | 4.5/7.3 | 752 | 16.17 | 1.8 | -68414 | 295 / 304 | 0.39 | 1.00 | -4202 | -0 / -0 / 4202 | LEAD PRE-PROOF |
| 7 | L_sessloss | eff=0.0 n=3 sess=[3] state=stack | 1.2/1.2/2.8/-1.6 | 201693 (165224) | 5.5/7.0 | 1011 | 15.41 | 6.2 | -87431 | 869 / 111 | 0.58 | 1.00 | -14355 | -0 / -0 / 15605 | LEAD PRE-PROOF |
| 8 | L_sessloss | eff=0.5 n=3 sess=[3] state=stack | 0.8/1.4/2.5/2.5 | 184211 (165224) | 2.4/4.1 | 432 | 17.65 | 1.1 | -40874 | 194 / 306 | 0.33 | 1.00 | -4202 | -0 / -0 / 4202 | LEAD PRE-PROOF |

## Session carry by P&L (Asia->London, London->NYAM ...)  (24 cells; best by robust equal-mean cut)
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_carry_pnl | R=1200.0 X=2 a=3 b=4 eff=0.0 | 6.1/-2.4/1.9/3.4 | 170456 (165224) | 8.3/4.2 | 559 | 16.85 | 2.3 | 7982 | 245 / 24 | 0.34 | 1.00 | 0 | -0 / -0 / 0 | LEAD PRE-PROOF |
| 2 | L_carry_pnl | R=1200.0 X=1 a=1 b=3 eff=0.0 | 16.6/17.5/11.5/0.8 | 193673 (165224) | 17.9/12.9 | 362 | 17.77 | 11.2 | 16543 | 1237 / 74 | 0.17 | 1.00 | -14325 | -0 / 1290 / 20400 | LEAD PRE-PROOF |
| 3 | L_carry_pnl | R=1200.0 X=1 a=3 b=4 eff=0.0 | 5.6/-2.4/1.3/0.6 | 169711 (165224) | 7.1/2.9 | 380 | 16.62 | 2.8 | 21215 | 294 / 71 | 0.52 | 1.00 | 0 | -0 / -0 / 0 | LEAD PRE-PROOF |
| 4 | L_carry_pnl | R=1200.0 X=3 a=3 b=4 eff=0.0 | 1.5/-2.4/0.5/0.5 | 158871 (165224) | 2.1/1.1 | 144 | 15.78 | 1.8 | 7325 | 185 / -36 | 0.49 | 1.00 | 0 | -0 / -0 / 0 | LEAD PRE-PROOF |
| 5 | L_carry_pnl | R=1200.0 X=2 a=3 b=4 eff=0.5 | 0.1/-1.2/0.4/2.4 | 165036 (165224) | 0.2/0.5 | 17 | 15.82 | 0.4 | 10479 | 68 / 209 | 0.39 | 1.00 | 0 | -0 / -0 / 0 | LEAD PRE-PROOF |
| 6 | L_carry_pnl | R=1200.0 X=1 a=3 b=4 eff=0.5 | 0.1/-1.2/0.4/1.4 | 165036 (165224) | -0.0/0.3 | -31 | 15.79 | 0.4 | 12508 | 80 / 278 | 0.42 | 1.00 | 0 | -0 / -0 / 0 | LEAD PRE-PROOF |
| 7 | L_carry_pnl | R=1200.0 X=1 a=1 b=3 eff=0.5 | 11.9/10.6/6.7/-1.9 | 193459 (165224) | 13.0/7.9 | 345 | 20.10 | 2.0 | -34007 | 274 / -72 | 0.04 | 1.00 | -4567 | -0 / -0 / 6000 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 8 | L_carry_pnl | R=1200.0 X=2 a=1 b=3 eff=0.5 | 11.9/10.6/6.7/-2.5 | 193459 (165224) | 13.0/7.9 | 345 | 20.10 | 1.8 | -63495 | 248 / -90 | 0.04 | 1.00 | -4567 | -0 / -0 / 6000 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |

## Session carry by chop share  (65 cells; best by robust equal-mean cut)
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_carry_chop | a=1 b=3 cond=adx_20 eff=0.5 th=0.4 | 4.1/0.9/2.4/9.6 | 198646 (165224) | 7.0/5.3 | 811 | 18.52 | 1.8 | -7377 | 258 / 214 | 0.42 | 1.00 | 232 | -0 / -0 / 1200 | LEAD PRE-PROOF |
| 2 | L_carry_chop | a=1 b=3 cond=er_0.20 eff=0.5 th=0.4 | 13.5/5.6/2.6/24.1 | 210210 (165224) | 15.9/5.3 | 755 | 20.48 | 3.9 | -21245 | 539 / 498 | 0.77 | 1.00 | -6197 | -0 / -0 / 9002 | LEAD PRE-PROOF |
| 3 | L_carry_chop | a=3 b=4 cond=adx_20 eff=0.0 th=0.4 | 2.1/-2.4/4.5/4.1 | 175108 (165224) | 3.8/6.2 | 394 | 14.77 | 1.5 | -14571 | 155 / 109 | 0.10 | 1.00 | 0 | -0 / -0 / 0 | CANDIDATE (own-p only; family p 1.00) PRE-PROOF |
| 4 | L_carry_chop | a=0 b=3 cond=adx_20 eff=0.0 th=0.4 | 8.6/10.4/0.6/21.4 | 222825 (165224) | 10.3/2.4 | 500 | 19.21 | 12.6 | 44854 | 1416 / 210 | 0.86 | 1.00 | 0 | -0 / -0 / 0 | LEAD PRE-PROOF |
| 5 | L_carry_chop | a=1 b=3 cond=er_0.20 eff=0.5 th=0.6 | 2.8/0.0/2.0/13.4 | 180543 (165224) | 3.0/2.3 | 69 | 17.76 | 1.4 | 28419 | 208 / 563 | 0.45 | 1.00 | 232 | -0 / -0 / 1200 | LEAD PRE-PROOF |
| 6 | L_carry_chop | a=0 b=3 cond=adx_20 eff=0.5 th=0.4 | 3.4/6.0/-0.4/13.0 | 191443 (165224) | 5.6/1.8 | 568 | 16.78 | 2.3 | -27321 | 335 / 374 | 0.94 | 1.00 | 0 | -0 / -0 / 0 | no |
| 7 | L_carry_chop | a=3 b=4 cond=adx_20 eff=0.0 th=0.6 | -0.5/-2.4/2.5/3.8 | 175702 (165224) | 1.4/4.3 | 418 | 14.41 | 0.8 | -8945 | 80 / 75 | 0.59 | 1.00 | 0 | -0 / -0 / 0 | no |
| 8 | L_carry_chop | a=0 b=3 cond=adx_20 eff=0.0 th=0.6 | -1.6/12.8/-4.0/12.9 | 231167 (165224) | 3.1/0.8 | 1177 | 16.34 | 6.1 | -4579 | 712 / 128 | 0.91 | 1.00 | 0 | -0 / -0 / 0 | no |

## Cross-book (>=k losses of one book in 60 min -> other books cool down)  (72 cells; best by robust equal-mean cut)
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_cross | W=60 eff=0.0 k=2 target=['KB', 'PE', 'SM', 'HM', 'MV', 'OD'] trig=PB | 1.2/0.0/8.8/0.0 | 191222 (165224) | 7.0/14.1 | 1317 | 14.93 | 0.3 | -33506 | 45 / 1141 | 0.10 | 1.00 | -8890 | 19420 / 660 / 36010 | CANDIDATE (own-p only; family p 1.00) FAILS-LIVE-WEEK PRE-PROOF |
| 2 | L_cross | W=60 eff=0.0 k=2 target=['PE', 'SM', 'MV'] trig=PB | 0.0/0.0/7.2/0.0 | 186157 (165224) | 4.2/11.2 | 945 | 14.50 | 0.2 | -20302 | 22 / 1700 | 0.57 | 1.00 | -9520 | 19420 / 660 / 31215 | no |
| 3 | L_cross | W=30 eff=0.0 k=2 target=['PE', 'SM', 'HM', 'MV', 'PB', 'OD'] trig=KB | 0.3/0.4/13.9/-3.6 | 185088 (165224) | 7.5/20.1 | 1822 | 16.47 | 2.6 | -49432 | 457 / 283 | 0.36 | 1.00 | -12125 | -0 / -0 / 14395 | LEAD PRE-PROOF |
| 4 | L_cross | W=60 eff=0.0 k=2 target=['PE', 'SM'] trig=MV | 5.5/-13.2/2.4/1.1 | 207146 (165224) | 6.8/3.8 | 382 | 18.77 | 1.3 | 24690 | 211 / -97 | 0.68 | 1.00 | 1875 | 1875 / -0 / 0 | LEAD PRE-PROOF |
| 5 | L_cross | W=30 eff=0.0 k=3 target=['PE', 'SM', 'MV'] trig=KB | 0.0/0.0/6.6/-0.2 | 170485 (165224) | 2.1/8.5 | 508 | 15.57 | 0.3 | -9861 | 56 / 294 | 0.57 | 1.00 | -1200 | -0 / -0 / 1200 | no |
| 6 | L_cross | W=60 eff=0.5 k=2 target=['PE', 'SM', 'MV'] trig=PB | 0.0/0.0/2.5/0.0 | 175084 (165224) | 2.0/4.4 | 426 | 14.17 | 0.1 | -8629 | 18 / 1659 | 0.68 | 1.00 | -5202 | 8690 / -0 / 13892 | no |
| 7 | L_cross | W=60 eff=0.5 k=2 target=['KB', 'PE', 'SM', 'HM', 'MV', 'OD'] trig=PB | 0.0/0.0/2.5/0.0 | 174370 (165224) | 1.9/4.4 | 419 | 14.16 | 0.1 | -8453 | 21 / 1491 | 0.60 | 1.00 | -5717 | 8690 / -0 / 15090 | no |
| 8 | L_cross | W=30 eff=0.0 k=2 target=['SM', 'MV'] trig=PE | 10.5/0.6/15.6/2.5 | 169433 (165224) | 9.0/14.2 | -448 | 19.76 | 0.7 | -49855 | 119 / 329 | 0.01 | 0.52 | -2400 | -0 / -0 / 2400 | CANDIDATE (own-p only; family p 0.52) FAILS-LIVE-WEEK PRE-PROOF |

## Exact-engine queue (top-5 by robust equal-mean cut, max 2 per kind; sets L_1..L_5, queued in L6M, PRE, X', HOLD order)
| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_chop | H=30 M=1 N=2 cond=rng60_3.0 eff=0.0 post=1.0 scope=exKB | 21.2/-36.7/22.8/24.6 | 243982 (165224) | 29.7/31.2 | 2735 | 20.76 | 16.1 | 375432 | 2465 / 238 | 0.30 | 1.00 | -34030 | 15870 / 5730 / 60770 | LEAD PRE-PROOF |
| 2 | L_chop | H=30 M=1 N=2 cond=rng60_3.0 eff=0.0 post=1.0 scope=ALL | 17.1/-15.3/32.0/23.5 | 249996 (165224) | 26.1/39.3 | 2727 | 19.75 | 26.9 | 449906 | 3952 / 191 | 0.31 | 1.00 | -46975 | 15870 / 5730 / 79305 | LEAD PRE-PROOF |
| 3 | L_sessloss | eff=0.0 n=2 sess=[1] state=stack | 21.9/-31.8/46.5/15.1 | 129348 (165224) | 26.7/49.8 | 1537 | 20.80 | 14.8 | 226207 | 1360 / 86 | 0.47 | 1.00 | -7225 | 19165 / 7160 / 41640 | LEAD PRE-PROOF |
| 4 | L_sessloss | eff=0.0 n=3 sess=[1] state=stack | 16.9/-45.2/38.4/21.8 | 179491 (165224) | 19.1/40.1 | 652 | 18.83 | 11.0 | 97705 | 1030 / 42 | 0.43 | 1.00 | 2395 | 13765 / 4775 / 22445 | LEAD PRE-PROOF |
| 5 | L_chop_book | H=0 M=3 N=2 cond=rng60_3.5 eff=0.0 post=1.0 scope=PE | 14.9/-32.3/33.2/32.7 | 209233 (165224) | 18.7/36.1 | 1026 | 17.94 | 8.3 | 284103 | 1152 / 408 | 0.30 | 1.00 | -61965 | 22445 / -0 / 90020 | LEAD PRE-PROOF |

## By session for the top-5 (removed % of that session's trades / removed P&L $)
| technique | params | asia | london | nyam | nypm |
|---|---|---|---|---|---|
| L_chop | H=30 M=1 N=2 cond=rng60_3.0 eff=0.0 post=1.0 scope=exKB | 12.8% / 278383 | 19.3% / -41409 | 0.0% / 0 | 20.2% / 138458 |
| L_chop | H=30 M=1 N=2 cond=rng60_3.0 eff=0.0 post=1.0 scope=ALL | 21.8% / 317749 | 27.2% / -22264 | 0.0% / 0 | 30.1% / 160997 |
| L_chop | H=30 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=exKB | 18.1% / 238072 | 18.8% / 67885 | 0.0% / 0 | 9.3% / -72052 |
| L_chop | H=30 M=3 N=1 cond=rng60_3.5 eff=0.5 post=1.0 scope=ALL | 20.6% / 255271 | 20.4% / 56093 | 0.0% / 0 | 9.3% / -72052 |
| L_chop | H=0 M=3 N=1 cond=rng30_3.0 eff=0.5 post=1.0 scope=exKB | 29.6% / 362256 | 30.8% / 81898 | 0.0% / 0 | 13.6% / -51708 |
## Live week (frozen blind week) - did any cooldown remove the P7 Asia/London losses and the M7 cuts without removing the winners?
Frozen-week totals: P7 Asia+London losing trades -67980 $, M7 cut losers -13615 $, all winners +243690 $. Cells below are the ten with the best live d$ among those that remove any P7 Asia/London loss.

| rank | technique | params | cut L6M/HOLD/PRE/X' % | w20 L6M (ref) | eq-mean cut L6M/PRE % | d mean $/wk L6M | Calmar | removed % | removed P&L $ (neg = losers skipped) | first-after n / mean $ | placebo p | p_fam | live d$ | live P7 A/L loss removed $ / M7 cut removed $ / winners removed $ | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | L_carry_chop | a=0 b=1 cond=er_0.20 eff=0.0 th=0.4 | -1.7/-71.2/34.0/-17.8 | 185816 (165224) | 1.2/35.9 | 709 | 15.91 | 15.7 | 268383 | 1379 / 190 | 0.95 | 1.00 | 7680 | 3400 / 4195 / 4445 | no |
| 2 | L_carry_chop | a=0 b=1 cond=rng30_2.0 eff=0.0 th=0.4 | 5.3/0.0/0.0/-45.3 | 159743 (165224) | 9.7/4.7 | 1187 | 17.41 | 3.4 | 104864 | 345 / 243 | 0.87 | 1.00 | 7680 | 3400 / 4195 / 4445 | no |
| 3 | L_chop | H=30 M=1 N=2 cond=fb_7 eff=0.0 post=1.0 scope=ALL | -36.9/-10.0/12.9/-25.1 | 96248 (165224) | -54.1/2.0 | -2643 | 10.03 | 8.8 | 285583 | 1539 / 24 | 0.99 | 1.00 | 6480 | 4545 / -0 / 7750 | no |
| 4 | L_chop | H=30 M=3 N=2 cond=fb_7 eff=0.0 post=1.0 scope=ALL | -35.6/-8.9/16.5/-14.2 | 93129 (165224) | -58.5/2.5 | -3426 | 9.75 | 9.9 | 355838 | 1678 / 8 | 1.00 | 1.00 | 5975 | 4545 / -0 / 8255 | no |
| 5 | L_sessloss | eff=0.5 n=3 sess=[1] state=stack | 8.5/-10.1/26.4/8.8 | 183950 (165224) | 14.1/31.0 | 1534 | 17.74 | 5.0 | 27570 | 668 / 110 | 0.22 | 1.00 | 4818 | 6553 / 592 / 3602 | LEAD PRE-PROOF |
| 6 | L_chop | H=30 M=1 N=2 cond=fb_7 eff=0.0 post=1.0 scope=exKB | -20.7/3.1/15.9/-27.1 | 105543 (165224) | -35.1/5.8 | -2538 | 11.43 | 6.1 | 271857 | 1072 / -6 | 0.95 | 1.00 | 4710 | 4545 / -0 / 7210 | no |
| 7 | L_chop | H=30 M=1 N=4 cond=fb_6 eff=0.0 post=1.0 scope=ALL | -29.4/-3.9/23.5/-11.1 | 62110 (165224) | -58.3/6.3 | -4341 | 9.76 | 12.9 | 462164 | 2175 / -26 | 0.96 | 1.00 | 4595 | 4545 / 750 / 10655 | no |
| 8 | L_chop | H=30 M=3 N=2 cond=fb_7 eff=0.0 post=1.0 scope=exKB | -22.2/1.8/19.6/-17.7 | 102777 (165224) | -42.6/6.2 | -3388 | 10.84 | 6.9 | 326401 | 1170 / -31 | 0.93 | 1.00 | 4205 | 4545 / -0 / 7715 | no |
| 9 | L_postloss | W=15 eff=0.0 n=1 scope=PE target=side trig=loss tscope=book | 5.2/-7.6/18.0/5.1 | 194086 (165224) | 11.9/23.8 | 1656 | 16.12 | 0.9 | -21373 | 193 / -218 | 0.17 | 1.00 | 4045 | 12455 / -0 / 8410 | LEAD PRE-PROOF |
| 10 | L_postloss | W=15 eff=0.0 n=1 scope=PE target=side trig=cut tscope=book | 2.6/-7.6/11.0/1.5 | 191522 (165224) | 7.8/15.7 | 1227 | 15.40 | 0.8 | -1923 | 167 / -273 | 0.16 | 1.00 | 4045 | 12455 / -0 / 8410 | LEAD PRE-PROOF |

Plain sentence: NO cell removes at least half of both the P7 Asia/London loss $ and the M7 cut loss $ while giving up less than 25% of the live winners $. Cells that skip those losers also skip winners (see removed-winner column).

## Not done first-order
- chop x state cut (wider arm / longer persistence) needs the exact engine state rules; not in this first table. Chop x sizer (x0.5 instead of off) is included as eff=0.5 (note 1-lot books do not halve after integer rounding).
