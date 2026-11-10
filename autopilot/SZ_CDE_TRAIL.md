# SZ_CDE_TRAIL - T-TRAIL-L2 profit-state lines for M7, A7, O7 (SZ-CDE) - 2026-11-10 20:25Z

> **Label: PRE-PROOF; post-hoc; Shadow only; no PASS claims. FIRST-ORDER SCREEN on the shared PTR engine (REDO-R5, LPB_BASE trade list, slip 1.2 central, equal lots, stack = LPB_BASE with the book's fired trades replaced; re-entries / locks / follow-on trades not re-simulated, so ranking only; exact promotion by SZ-IJK from /mnt/l2/l2vast/_th_ptr/top20_<book>.txt). Prereg: autopilot/SZ_CDE_TRAIL_PREREG.md. Windows L1M / L3M / L6M / HOLD / PRE / X-prime, carrying week dropped from means only; Rule 2a label via Z.prior_info (PRE mean floor = 25% of the live PRE mean; old fixed-floor label beside), bi-weekly WF = the line vs LPB_BASE (26 weeks train, 2 weeks test).**

Screened per book: stage 1 = the whole take grid (arm 0.2..0.9 x persist 1/2/3/5/10 x win 2..15 x every feature threshold of the directive, 9,400 cells per book); stage 2 = actions tighten 5/10/20/40, lock 0/2/5/10, step 5/10/20, scale 0.25/0.5/0.75 (lots >= 2 only) on the best 250 + 15 per family take cells, 8 pure-arm lines, and AND / OR pairs among the 20 best conditions (take, tighten 10). Stage 2b (done): the FULL action cross - every stage-1 cell x every non-take action (A7 67k, O7 54k, M7 95k cells) - gave no better recents-first key than the stage-2 selection (A7 8.8 vs 8.8, O7 4.14 vs 4.31, M7 27.7 vs 28.2), so the top-20 stand. NOT SCREENED (needs the exact engine or code beyond this screen): state-adaptive trail X = X0 g(ahead_rel), the loss-cut mirror cell at a new favourable extreme, behind_rel conditions, arms below 0.2 (cache starts at 0.2 x target); the live-week replay (REDO-R13).


## M7 (momentum vote, London + NY-AM)

### Best by recents-first drawdown (early-take lines included)

**M7, best drawdown line: `profit M7 * pct>=0.2 sweep_against>=3 take win=8 persist=2 wall_ticks=8`; fires on 3349 trades, clips 1850 winners (-1994073 $) and catches 1499 non-winners (+1899430 $); stack maxDD L6M / HOLD / PRE / X-prime +32.7 / +17.4 / -2.0 / -23.6 % (positive = shallower); at EQUAL MEAN the L6M / PRE cut is +30.3 / -5.6 %; d mean -636 / -674 $/wk (L6M / PRE); placebo p own L6M 0.01, PRE 0.68; WF beats live in 41% of periods; Rule 2a OK-PRIOR [old OK-PRIOR].**

### Best SELECTIVE line (condition fires on < 30% of the armed trades; a state-conditioned protection, not a smaller target)

**M7, best selective line: `profit M7 * pct>=0.3 tot_rel>=2 step 10 win=0 persist=2 wall_ticks=8`; fires on 850 trades, clips 557 winners (-469735 $) and catches 293 non-winners (+437019 $); stack maxDD L6M / HOLD / PRE / X-prime +15.3 / +6.3 / -4.8 / -14.8 % (positive = shallower); at EQUAL MEAN the L6M / PRE cut is +17.6 / -1.9 %; d mean +473 / -624 $/wk (L6M / PRE); placebo p own L6M 0.02, PRE 0.69; WF beats live in 25% of periods; Rule 2a OK-PRIOR [old OK-PRIOR].**

### Reference rows: no rule (= LPB_BASE, cut 0 / d mean 0 by definition) and the live tighten line re-expressed in the grammar (LPB_BASE already contains the live ThL2 profit branch, so these rows are comparisons, not additions)

| # | line | nfire (of armed) | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN cut L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | clipped winners n / $ | non-winners caught n / $ | placebo p own L6M / PRE | family p (this set / top-300 lines) | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit M7 * pct>=0.333 tot_rel>=1.5 tighten 15 win=5 persist=10 wall_ticks=8` | 562 | +3.3 / +3.3 / +8.3 | +2.9 | -0.1 | -16.5 | +4.6 / +1.3 | +238 / -300 | +6.4 | 373 / -315241 | 189 / +290005 | na / na | na / na | 32 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit M7 * pct>=0.333 tot_rel_slow>=1.5 tighten 15 win=5 persist=10 wall_ticks=8` | 647 | +3.7 / +3.7 / +6.9 | +2.9 | -0.8 | -17.3 | +6.2 / +1.9 | +440 / -477 | +11.5 | 436 / -357714 | 211 / +324688 | na / na | na / na | 27 | OK-PRIOR [OK-PRIOR] |

### Selective lines (promoted for exact via sel_M7.txt)

| # | line | nfire (of armed) | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN cut L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | clipped winners n / $ | non-winners caught n / $ | placebo p own L6M / PRE | family p (this set / top-300 lines) | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit M7 * pct>=0.3 tot_rel>=2 step 10 win=0 persist=2 wall_ticks=8` | 850 | +15.3 / +15.3 / +4.2 | +6.3 | -4.8 | -14.8 | +17.6 / -1.9 | +473 / -624 | +10.1 | 557 / -469735 | 293 / +437019 | 0.02 / 0.69 | 1.00 / na | 25 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit M7 * pct>=0.3 tot_rel>=2 tighten 20 win=0 persist=2 wall_ticks=8` | 764 | +14.0 / +14.0 / +3.2 | +6.4 | -5.7 | -11.3 | +15.6 / -3.8 | +326 / -608 | +5.7 | 472 / -444888 | 292 / +406557 | 0.01 / 0.80 | 1.00 / na | 27 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit M7 * pct>=0.3 dd>=20 tighten 40 win=0 persist=1 wall_ticks=8` | 919 | +10.4 / +10.4 / +10.7 | +7.8 | -2.9 | -0.3 | +9.8 / -3.5 | -122 / -743 | +5.2 | 444 / -567232 | 475 / +501423 | 0.06 / 0.71 | 1.00 / na | 28 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit M7 * pct>=0.3 tot_rel>=2 lock 10 win=0 persist=2 wall_ticks=8` | 594 | +12.4 / +12.4 / +5.0 | +4.2 | -5.4 | -8.5 | +14.0 / -3.5 | +339 / -485 | +6.9 | 303 / -369029 | 291 / +344102 | 0.03 / 0.88 | 1.00 / na | 24 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit M7 * pct>=0.3 tot_rel>=2 step 20 win=0 persist=2 wall_ticks=8` | 625 | +10.3 / +10.3 / +4.9 | +5.7 | -7.7 | -7.3 | +12.1 / -5.6 | +367 / -610 | +3.8 | 334 / -385230 | 291 / +340152 | 0.02 / 0.95 | 1.00 / na | 27 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit M7 * pct>=0.5 pulled_mult>=3 pulled_against_mult>=5 tighten 10 win=2 persist=3 wall_ticks=8` | 730 | +4.4 / +4.4 / +6.0 | +6.3 | -0.3 | -1.3 | +4.6 / -0.0 | +48 / -431 | +12.1 | 546 / -338264 | 184 / +315757 | 0.32 / 0.47 | 0.97 / na | 18 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit M7 * pct>=0.2 delta_mult>=20 lock 2 win=10 persist=5 wall_ticks=8` | 980 | +11.7 / +11.7 / +5.4 | +2.2 | -8.6 | -12.4 | +14.1 / -5.7 | +590 / -421 | +6.9 | 422 / -579664 | 558 / +524367 | 0.25 / 0.93 | 1.00 / na | 30 | OK-PRIOR [OK-PRIOR] |

### Top-20 by recents-first drawdown (promoted for exact via top20_M7.txt)

| # | line | nfire (of armed) | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN cut L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | clipped winners n / $ | non-winners caught n / $ | placebo p own L6M / PRE | family p (this set / top-300 lines) | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit M7 * pct>=0.2 sweep_against>=3 take win=8 persist=2 wall_ticks=8` | 3349 | +32.7 / +32.7 / +10.2 | +17.4 | -2.0 | -23.6 | +30.3 / -5.6 | -636 / -674 | +20.6 | 1850 / -1994073 | 1499 / +1899430 | 0.01 / 0.68 | 1.00 / 1.00 | 41 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8` | 3320 | +32.1 / +32.1 / +11.0 | +13.1 | -2.1 | -24.0 | +30.1 / -5.1 | -521 / -694 | +22.2 | 1847 / -1979595 | 1473 / +1879525 | 0.02 / 0.72 | 1.00 / 1.00 | 39 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit M7 * pct>=0.2 pulled_mult>=3 tighten 5 win=5 persist=3 wall_ticks=8` | 3312 | +31.7 / +31.7 / +11.8 | +11.5 | -4.7 | -24.8 | +29.7 / -7.7 | -520 / -760 | +20.4 | 1839 / -1954447 | 1473 / +1847995 | 0.01 / 0.95 | 1.00 / 1.00 | 37 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit M7 * pct>=0.2 sweep_against>=4 take win=8 persist=2 wall_ticks=8` | 3323 | +31.9 / +31.9 / +10.9 | +17.5 | -0.9 | -22.8 | +29.5 / -4.4 | -630 / -662 | +18.8 | 1850 / -1979373 | 1473 / +1873722 | 0.01 / 0.44 | 1.00 / 1.00 | 41 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit M7 * pct>=0.2 pulled_against_mult>=10 take win=5 persist=2 wall_ticks=8` | 3304 | +31.6 / +31.6 / +10.5 | +16.6 | -1.2 | -19.4 | +29.3 / -4.7 | -627 / -630 | +19.3 | 1840 / -1952849 | 1464 / +1865955 | 0.01 / 0.43 | 1.00 / 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit M7 * pct>=0.2 pulled_against_mult>=20 tighten 5 win=15 persist=2 wall_ticks=8` | 3307 | +31.3 / +31.3 / +10.5 | +14.0 | -4.8 | -22.6 | +28.8 / -8.6 | -656 / -793 | +17.7 | 1838 / -1939946 | 1469 / +1825553 | 0.01 / 0.96 | 1.00 / 1.00 | 34 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit M7 * pct>=0.2 imb10<=-0.1 tighten 5 win=0 persist=1 wall_ticks=8` | 3347 | +30.0 / +30.0 / +12.0 | +15.6 | -2.8 | -25.2 | +27.7 / -6.2 | -603 / -818 | +21.1 | 1843 / -1975445 | 1504 / +1867672 | 0.03 / 0.77 | 1.00 / 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit M7 * pct>=0.2 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | 3261 | +30.2 / +30.2 / +8.6 | +15.1 | -0.2 | -24.4 | +27.9 / -3.6 | -614 / -570 | +21.4 | 1843 / -1931315 | 1418 / +1836096 | 0.05 / 0.42 | 1.00 / 1.00 | 39 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit M7 * pct>=0.6 ice_against>=1 tighten 20 win=30 persist=1 wall_ticks=8` | 1263 | +14.5 / +14.5 / +8.4 | +8.7 | -14.1 | -8.8 | +16.8 / -11.1 | +528 / -1085 | +2.1 | 849 / -679262 | 414 / +616949 | 0.04 / 1.00 | 1.00 / na | 37 | OK-PRIOR [RECENT-ONLY] |
| 10 | `profit M7 * pct>=0.5 dd>=3 step 20 win=0 persist=5 wall_ticks=8` | 1250 | +13.0 / +13.0 / +13.7 | +8.6 | -2.0 | -14.9 | +14.0 / -0.8 | +261 / -617 | +12.8 | 693 / -744464 | 557 / +693498 | 0.01 / 0.49 | 1.00 / na | 37 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit M7 * pct>=0.6 ice_against>=1 tighten 20 win=30 persist=2 wall_ticks=8` | 1235 | +14.9 / +14.9 / +6.0 | +8.7 | -14.1 | -7.9 | +16.6 / -11.8 | +396 / -1087 | -0.8 | 839 / -665803 | 396 / +597962 | 0.03 / 0.99 | 1.00 / na | 38 | OK-PRIOR [RECENT-ONLY] |
| 12 | `profit M7 * pct>=0.5 dd>=5 take win=0 persist=1 wall_ticks=8` | 2289 | +12.8 / +12.8 / +12.1 | +7.8 | +5.1 | -20.3 | +13.4 / +5.8 | +158 / -755 | +19.5 | 1727 / -1026194 | 562 / +981799 | 0.01 / 0.01 | 0.12 / na | 46 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit M7 * pct>=0.2 imb5<=-0.1 lock 5 win=0 persist=2 wall_ticks=8` | 2588 | +25.8 / +25.8 / +3.5 | +13.6 | -3.3 | -27.3 | +25.5 / -3.7 | -81 / -302 | +20.3 | 1172 / -1552446 | 1416 / +1465469 | 0.18 / 0.62 | 1.00 / na | 29 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit M7 * pct>=0.2 imb10<=-0.1 lock 10 win=0 persist=3 wall_ticks=8` | 2604 | +23.7 / +23.7 / +11.0 | +11.7 | -1.7 | -24.0 | +25.5 / +0.6 | +439 / -409 | +11.6 | 1315 / -1585155 | 1289 / +1505037 | 0.36 / 0.55 | 1.00 / na | 30 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit M7 * pct>=0.2 ahead_rel_slow>=1.5 lock 10 win=0 persist=1 wall_ticks=8` | 2540 | +22.2 / +22.2 / +11.2 | +10.3 | -5.0 | -28.4 | +23.0 / -3.9 | +201 / -894 | +6.8 | 1297 / -1553651 | 1243 / +1439561 | 0.40 / 0.77 | 1.00 / na | 32 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit M7 * pct>=0.2 ahead_rel>=1.5 lock 10 win=0 persist=1 wall_ticks=8` | 2638 | +21.0 / +21.0 / +12.8 | +11.3 | -3.5 | -22.6 | +21.7 / -2.6 | +167 / -800 | +8.8 | 1340 / -1605208 | 1298 / +1501471 | 0.54 / 0.67 | 1.00 / na | 32 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit M7 * pct>=0.2 sweep_against>=3 tighten 5 win=8 persist=2 wall_ticks=8` | 3342 | +31.7 / +31.7 / +10.5 | +14.6 | -4.1 | -24.7 | +29.4 / -7.6 | -592 / -779 | +17.9 | 1843 / -1968585 | 1499 / +1860083 | 0.01 / 0.89 | 1.00 / 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit M7 * pct>=0.2 sweep_against>=3 lock 10 win=8 persist=2 wall_ticks=8` | 3013 | +28.5 / +28.5 / +9.2 | +14.1 | -1.8 | -23.5 | +25.8 / -5.7 | -686 / -453 | +8.8 | 1514 / -1805821 | 1499 / +1724305 | 0.17 / 0.55 | 1.00 / na | 30 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit M7 * pct>=0.2 pulled_mult>=3 step 5 win=5 persist=3 wall_ticks=8` | 3299 | +30.6 / +30.6 / +12.2 | +11.8 | -1.8 | -24.9 | +27.7 / -6.0 | -741 / -754 | +16.4 | 1826 / -1930932 | 1473 / +1820202 | 0.02 / 0.62 | 1.00 / 1.00 | 34 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit M7 * pct>=0.2 sweep_against>=4 scale 0.5 win=8 persist=2 wall_ticks=8` | 0 | +9.7 / +9.7 / +0.2 | +8.1 | +4.7 | -3.2 | +10.1 / +5.1 | +77 / +5 | +8.3 | 0 / +0 | 0 / +0 | 1.00 / 0.03 | 1.00 / na | 51 | OK-PRIOR [OK-PRIOR] |
| 21 | `profit M7 * pct>=0.2 sweep_against>=4 take win=10 persist=2 wall_ticks=8` | 3329 | +31.6 / +31.6 / +10.7 | +17.2 | -0.4 | -22.1 | +28.7 / -4.6 | -759 / -676 | +17.2 | 1851 / -1984851 | 1478 / +1876959 | 0.01 / 0.36 | 1.00 / 1.00 | 41 | OK-PRIOR [OK-PRIOR] |
| 22 | `profit M7 * pct>=0.2 tighten 5` | 3415 | +28.8 / +28.8 / +13.2 | +16.8 | -5.7 | -23.8 | +26.8 / -8.7 | -524 / -754 | +24.0 | 1848 / -2022058 | 1567 / +1907055 | 0.01 / 1.00 | 1.00 / 1.00 | 35 | OK-PRIOR [OK-PRIOR] |


Per entry session (rule applied to that session only), L6M stack maxDD cut, top 5: #1 s1 +26.5 / s3 +3.0; #2 s1 +24.8 / s3 +3.5; #3 s1 +25.5 / s3 +3.8; #4 s1 +26.5 / s3 +3.1; #5 s1 +25.8 / s3 +3.5


## A7 (Asia, 1 lot)

### Best by recents-first drawdown (early-take lines included)

**A7, best drawdown line: `profit A7 * pct>=0.3 delta_mult>=2 tighten 5 win=2 persist=2 wall_ticks=8`; fires on 872 trades, clips 588 winners (-460677 $) and catches 284 non-winners (+390368 $); stack maxDD L6M / HOLD / PRE / X-prime +9.9 / +1.7 / +1.7 / -3.6 % (positive = shallower); at EQUAL MEAN the L6M / PRE cut is +5.4 / -3.3 %; d mean -841 / -346 $/wk (L6M / PRE); placebo p own L6M 0.02, PRE 0.01; WF beats live in 43% of periods; Rule 2a OK-PRIOR [old OK-PRIOR].**

### Best SELECTIVE line (condition fires on < 30% of the armed trades; a state-conditioned protection, not a smaller target)

**A7, best selective line: `profit A7 * pct>=0.3 pulled_against_mult>=50 pulled_mult>=30 take win=15 persist=1 wall_ticks=8`; fires on 253 trades, clips 184 winners (-118074 $) and catches 69 non-winners (+97463 $); stack maxDD L6M / HOLD / PRE / X-prime +10.3 / +3.0 / -1.8 / -0.5 % (positive = shallower); at EQUAL MEAN the L6M / PRE cut is +9.0 / -3.3 %; d mean -299 / -178 $/wk (L6M / PRE); placebo p own L6M 0.01, PRE 0.82; WF beats live in 10% of periods; Rule 2a OK-PRIOR [old OK-PRIOR].**

### Reference rows: no rule (= LPB_BASE, cut 0 / d mean 0 by definition) and the live tighten line re-expressed in the grammar (LPB_BASE already contains the live ThL2 profit branch, so these rows are comparisons, not additions)

| # | line | nfire (of armed) | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN cut L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | clipped winners n / $ | non-winners caught n / $ | placebo p own L6M / PRE | family p (this set / top-300 lines) | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit A7 * pct>=0.333 tot_rel>=1.5 tighten 15 win=5 persist=10 wall_ticks=8` | 334 | -1.8 / -1.8 / +1.4 | -0.9 | -0.5 | -4.6 | -3.4 / -2.1 | -261 / -104 | -4.8 | 242 / -169391 | 92 / +128111 | na / na | na / na | 18 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit A7 * pct>=0.333 tot_rel_slow>=1.5 tighten 15 win=5 persist=10 wall_ticks=8` | 359 | -4.2 / -4.2 / -0.1 | -2.1 | -2.0 | -5.1 | -8.1 / -5.7 | -612 / -47 | -12.5 | 258 / -183526 | 101 / +138255 | na / na | na / na | 27 | OK-PRIOR [OK-PRIOR] |

### Selective lines (promoted for exact via sel_A7.txt)

| # | line | nfire (of armed) | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN cut L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | clipped winners n / $ | non-winners caught n / $ | placebo p own L6M / PRE | family p (this set / top-300 lines) | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit A7 * pct>=0.3 pulled_against_mult>=50 pulled_mult>=30 take win=15 persist=1 wall_ticks=8` | 253 | +10.3 / +10.3 / -5.0 | +3.0 | -1.8 | -0.5 | +9.0 / -3.3 | -299 / -178 | +3.6 | 184 / -118074 | 69 / +97463 | 0.01 / 0.82 | 1.00 / 1.00 | 10 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit A7 * pct>=0.2 pulled_mult>=50 lock 5 win=15 persist=2 wall_ticks=8` | 264 | +9.8 / +9.8 / -3.1 | +0.5 | -1.8 | -1.9 | +8.4 / -3.4 | -283 / -73 | +8.5 | 131 / -150021 | 133 / +135951 | 0.04 / 0.81 | 1.00 / 1.00 | 19 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit A7 * pct>=0.3 pulled_against_mult>=10 tighten 20 win=2 persist=3 wall_ticks=8` | 235 | +9.3 / +9.3 / -4.1 | -0.3 | -2.0 | -1.6 | +9.2 / -2.1 | -8 / -46 | +12.0 | 162 / -124376 | 73 / +96525 | 0.02 / 0.88 | 1.00 / na | 3 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit A7 * pct>=0.2 pulled_mult>=50 lock 2 win=15 persist=2 wall_ticks=8` | 246 | +8.7 / +8.7 / -3.3 | -0.2 | -2.0 | -1.0 | +8.2 / -2.5 | -97 / -68 | +12.0 | 113 / -136336 | 133 / +127671 | 0.04 / 0.82 | 1.00 / na | 8 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit A7 * pct>=0.3 pulled_against_mult>=10 step 10 win=2 persist=3 wall_ticks=8` | 260 | +9.4 / +9.4 / -3.2 | +0.6 | -2.4 | -1.4 | +9.4 / -2.4 | -0 / -126 | +12.5 | 187 / -129472 | 73 / +102737 | 0.08 / 0.90 | 1.00 / na | 10 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit A7 * pct>=0.3 pulled_against_mult>=10 sweep_against>=6 take win=3 persist=3 wall_ticks=8` | 181 | +6.5 / +6.5 / +2.5 | +2.4 | -2.4 | -0.4 | +7.0 / -1.9 | +105 / -86 | +8.0 | 136 / -77429 | 45 / +66589 | 0.05 / 0.87 | 1.00 / na | 9 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit A7 * pct>=0.3 pulled_against_mult>=50 pulled_mult>=30 tighten 10 win=15 persist=1 wall_ticks=8` | 232 | +9.2 / +9.2 / -7.4 | +2.3 | -0.9 | -0.5 | +7.3 / -3.0 | -404 / -168 | -0.0 | 163 / -115684 | 69 / +91951 | 0.02 / 0.76 | 1.00 / na | 10 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit A7 * pct>=0.3 pulled_against_mult>=10 lock 10 win=2 persist=3 wall_ticks=8` | 170 | +7.8 / +7.8 / -1.0 | +0.1 | -2.1 | -2.7 | +7.7 / -2.2 | -21 / -71 | +11.3 | 97 / -101218 | 73 / +82742 | 0.04 / 0.92 | 1.00 / na | 11 | OK-PRIOR [OK-PRIOR] |

### Top-20 by recents-first drawdown (promoted for exact via top20_A7.txt)

| # | line | nfire (of armed) | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN cut L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | clipped winners n / $ | non-winners caught n / $ | placebo p own L6M / PRE | family p (this set / top-300 lines) | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit A7 * pct>=0.3 delta_mult>=2 tighten 5 win=2 persist=2 wall_ticks=8` | 872 | +9.9 / +9.9 / +4.3 | +1.7 | +1.7 | -3.6 | +5.4 / -3.3 | -841 / -346 | -3.5 | 588 / -460677 | 284 / +390368 | 0.02 / 0.01 | 0.37 / 0.96 | 43 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit A7 * pct>=0.3 pulled_against_mult>=30 or pulled_mult>=20 take win=10 persist=3 wall_ticks=8` | 811 | +10.3 / +10.3 / +2.0 | +1.6 | +1.8 | -3.5 | +9.1 / +0.5 | -221 / -122 | -2.0 | 556 / -409096 | 255 / +359446 | 0.07 / 0.06 | 0.66 / 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8` | 571 | +10.0 / +10.0 / +2.7 | +2.4 | -2.1 | -2.3 | +11.1 / -0.9 | +206 / -198 | +10.9 | 387 / -280857 | 184 / +246829 | 0.09 / 0.77 | 1.00 / 1.00 | 24 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit A7 * pct>=0.3 pulled_mult>=30 sweep_against>=6 take win=15 persist=1 wall_ticks=8` | 760 | +10.1 / +10.1 / +1.9 | +4.4 | +1.7 | -0.4 | +8.8 / +0.3 | -237 / -128 | -3.5 | 521 / -386313 | 239 / +340760 | 0.11 / 0.16 | 0.84 / 1.00 | 35 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit A7 * pct>=0.2 pulled_against_mult>=50 take win=15 persist=2 wall_ticks=8` | 438 | +10.4 / +10.4 / +0.3 | +3.1 | -0.8 | -0.6 | +9.2 / -2.3 | -289 / -92 | +9.7 | 293 / -214374 | 145 / +195087 | 0.01 / 0.64 | 1.00 / 1.00 | 16 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit A7 * pct>=0.3 pulled_mult>=30 take win=15 persist=2 wall_ticks=8` | 772 | +9.8 / +9.8 / +2.1 | +4.4 | +0.0 | -1.4 | +8.1 / -1.9 | -308 / -136 | -3.7 | 532 / -387913 | 240 / +341558 | 0.12 / 0.50 | 1.00 / 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit A7 * pct>=0.3 pulled_mult>=30 take win=15 persist=1 wall_ticks=8` | 784 | +9.9 / +9.9 / +1.8 | +4.2 | +1.9 | -2.5 | +8.6 / +0.4 | -234 / -141 | -2.8 | 537 / -399348 | 247 / +350065 | 0.08 / 0.08 | 0.78 / 1.00 | 42 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit A7 * pct>=0.2 sweep_against>=6 step 10 win=5 persist=10 wall_ticks=8` | 552 | +9.1 / +9.1 / +4.6 | +3.2 | +0.6 | -2.0 | +9.2 / +0.7 | +21 / -261 | +4.5 | 371 / -289692 | 181 / +236009 | 0.05 / 0.43 | 1.00 / 1.00 | 27 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit A7 * pct>=0.5 take` | 787 | +6.4 / +6.4 / +1.3 | +1.8 | -0.3 | -6.8 | +6.2 / -0.5 | -43 / -180 | +4.0 | 590 / -355732 | 197 / +307323 | 1.00 / 1.00 | 1.00 / na | 28 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit A7 * pct>=0.5 tighten 5` | 780 | +6.4 / +6.4 / +0.5 | +1.7 | +0.0 | -5.7 | +4.4 / -2.1 | -369 / -209 | +6.1 | 583 / -352261 | 197 / +301475 | 0.17 / 0.08 | 1.00 / na | 35 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit A7 * pct>=0.5 wall_ahead_mult>=5 step 10 win=0 persist=3 wall_ticks=4` | 404 | +3.8 / +3.8 / -1.5 | -0.1 | -3.4 | -4.0 | +0.2 / -7.2 | -629 / -381 | -4.2 | 309 / -192164 | 95 / +142332 | 0.41 / 0.97 | 1.00 / na | 11 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit A7 * pct>=0.5 wall_ahead_mult>=5 tighten 5 win=0 persist=3 wall_ticks=4` | 504 | +3.5 / +3.5 / -1.2 | +0.5 | -2.6 | -3.6 | +0.2 / -6.2 | -586 / -338 | -4.1 | 409 / -199030 | 95 / +154587 | 0.51 / 0.95 | 1.00 / na | 16 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit A7 * pct>=0.2 sweep_against>=4 take win=8 persist=10 wall_ticks=8` | 912 | +8.8 / +8.8 / +5.6 | +2.6 | -0.1 | -0.5 | +8.3 / -0.6 | -89 / -405 | +4.7 | 590 / -499862 | 322 / +426834 | 0.01 / 0.31 | 0.99 / 1.00 | 38 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit A7 * pct>=0.3 delta_mult>=2 take win=5 persist=1 wall_ticks=8` | 893 | +8.9 / +8.9 / +2.4 | +2.6 | +0.8 | -5.4 | +8.4 / +0.3 | -97 / -376 | +1.7 | 592 / -479867 | 301 / +413125 | 0.03 / 0.02 | 0.83 / 1.00 | 44 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit A7 * pct>=0.4 dd>=5 take win=0 persist=1 wall_ticks=8` | 787 | +6.4 / +6.4 / +3.8 | +1.7 | -0.7 | -4.5 | +6.6 / -0.5 | +49 / -251 | +6.3 | 584 / -362976 | 203 / +308515 | 0.04 / 0.94 | 1.00 / na | 33 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit A7 * pct>=0.4 dd>=5 tighten 5 win=0 persist=1 wall_ticks=8` | 787 | +6.4 / +6.4 / +3.8 | +1.7 | -0.7 | -4.5 | +6.6 / -0.5 | +49 / -251 | +6.3 | 584 / -362976 | 203 / +308515 | 0.04 / 0.94 | 1.00 / na | 33 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit A7 * pct>=0.2 pulled_against_mult>=30 tighten 5 win=10 persist=5 wall_ticks=8` | 564 | +9.6 / +9.6 / +2.6 | +2.1 | -1.8 | -2.4 | +10.3 / -1.0 | +135 / -194 | +9.4 | 380 / -280831 | 184 / +245062 | 0.09 / 0.81 | 1.00 / 1.00 | 25 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit A7 * pct>=0.2 sweep_against>=4 lock 10 win=8 persist=10 wall_ticks=8` | 759 | +7.2 / +7.2 / +7.4 | +1.9 | -0.9 | +1.2 | +5.6 / -2.6 | -269 / -371 | +0.5 | 437 / -453067 | 322 / +373759 | 0.09 / 0.68 | 1.00 / 1.00 | 39 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit A7 * pct>=0.3 delta_mult>=2 step 5 win=2 persist=2 wall_ticks=8` | 867 | +9.3 / +9.3 / +3.3 | +1.9 | +1.9 | -3.0 | +4.4 / -3.4 | -888 / -363 | -4.6 | 583 / -458563 | 284 / +384541 | 0.09 / 0.02 | 0.88 / 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit A7 * pct>=0.3 sweep_against>=6 pulled_mult>=10 take win=3 persist=1 wall_ticks=8` | 832 | +10.1 / +10.1 / +1.9 | +1.7 | +2.0 | -5.2 | +8.9 / +0.7 | -206 / -184 | -1.0 | 573 / -421737 | 259 / +364267 | 0.06 / 0.02 | 0.83 / 1.00 | 43 | OK-PRIOR [OK-PRIOR] |
| 21 | `profit A7 * pct>=0.2 imb10<=-0.2 tighten 10 win=0 persist=2 wall_ticks=8` | 893 | +9.7 / +9.7 / +1.1 | +1.4 | +0.7 | -3.3 | +6.4 / -2.9 | -580 / -534 | -7.2 | 569 / -504534 | 324 / +399911 | 0.01 / 0.14 | 0.81 / 1.00 | 47 | OK-PRIOR [OK-PRIOR] |


## O7 (opening drive, own 40/90 bracket, 16:00 time exit)

### Best by recents-first drawdown (early-take lines included)

**O7, best drawdown line: `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8`; fires on 255 trades, clips 178 winners (-150166 $) and catches 77 non-winners (+105319 $); stack maxDD L6M / HOLD / PRE / X-prime +4.8 / +1.5 / -1.0 / +2.9 % (positive = shallower); at EQUAL MEAN the L6M / PRE cut is +6.0 / +0.2 %; d mean +218 / -459 $/wk (L6M / PRE); placebo p own L6M 0.01, PRE 0.97; WF beats live in 19% of periods; Rule 2a OK-PRIOR [old OK-PRIOR].**

### Best SELECTIVE line (condition fires on < 30% of the armed trades; a state-conditioned protection, not a smaller target)

**O7, best selective line: `profit O7 * pct>=0.3 pulled_mult>=30 lock 2 win=10 persist=5 wall_ticks=8`; fires on 87 trades, clips 31 winners (-49445 $) and catches 56 non-winners (+36730 $); stack maxDD L6M / HOLD / PRE / X-prime +2.1 / +0.6 / -1.8 / -0.2 % (positive = shallower); at EQUAL MEAN the L6M / PRE cut is +2.4 / -1.5 %; d mean +55 / -31 $/wk (L6M / PRE); placebo p own L6M 0.22, PRE 0.98; WF beats live in 19% of periods; Rule 2a OK-PRIOR [old OK-PRIOR].**

### Reference rows: no rule (= LPB_BASE, cut 0 / d mean 0 by definition) and the live tighten line re-expressed in the grammar (LPB_BASE already contains the live ThL2 profit branch, so these rows are comparisons, not additions)

| # | line | nfire (of armed) | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN cut L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | clipped winners n / $ | non-winners caught n / $ | placebo p own L6M / PRE | family p (this set / top-300 lines) | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit O7 * pct>=0.222 tot_rel>=1.5 tighten 15 win=5 persist=10 wall_ticks=8` | 24 | +0.0 / +0.0 / +0.0 | +0.0 | +0.0 | +1.1 | +0.0 / +0.0 | +0 / -29 | +0.0 | 19 / -10083 | 5 / +7277 | na / na | na / na | 1 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit O7 * pct>=0.222 tot_rel_slow>=1.5 tighten 15 win=5 persist=10 wall_ticks=8` | 30 | +0.0 / +0.0 / +0.0 | +0.0 | +0.0 | +0.5 | +0.0 / +0.0 | +0 / -8 | +1.6 | 23 / -13194 | 7 / +10105 | na / na | na / na | 1 | OK-PRIOR [OK-PRIOR] |

### Selective lines (promoted for exact via sel_O7.txt)

| # | line | nfire (of armed) | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN cut L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | clipped winners n / $ | non-winners caught n / $ | placebo p own L6M / PRE | family p (this set / top-300 lines) | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit O7 * pct>=0.3 pulled_mult>=30 lock 2 win=10 persist=5 wall_ticks=8` | 87 | +2.1 / +2.1 / +0.5 | +0.6 | -1.8 | -0.2 | +2.4 / -1.5 | +55 / -31 | -1.6 | 31 / -49445 | 56 / +36730 | 0.22 / 0.98 | 1.00 / na | 19 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit O7 * pct>=0.3 pulled_mult>=50 lock 2 win=15 persist=1 wall_ticks=8` | 80 | +2.1 / +2.1 / +0.5 | +1.6 | -1.8 | +1.3 | +2.4 / -1.5 | +55 / -17 | -1.6 | 26 / -41932 | 54 / +34935 | 0.09 / 0.98 | 1.00 / na | 14 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit O7 * pct>=0.7 dd>=12 delta_mult>=20 tighten 10 win=10 persist=3 wall_ticks=8` | 47 | +0.6 / +0.6 / +0.0 | +0.0 | +0.0 | -0.4 | +0.3 / -0.4 | -67 / -36 | +0.8 | 46 / -4615 | 1 / +1920 | 0.01 / 0.34 | 0.76 / na | 5 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit O7 * pct>=0.3 pulled_mult>=30 lock 0 win=10 persist=5 wall_ticks=8` | 85 | +1.8 / +1.8 / +0.5 | +0.6 | -1.9 | -0.3 | +2.4 / -1.3 | +103 / -53 | -0.4 | 29 / -47110 | 56 / +33868 | 0.12 / 0.98 | 1.00 / na | 20 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit O7 * pct>=0.9 step 20` | 35 | +0.4 / +0.4 / +0.0 | +0.0 | +0.0 | +0.0 | +0.4 / +0.0 | +3 / +1 | -0.6 | 34 / +807 | 1 / +1871 | 0.19 / 0.56 | 0.96 / na | 9 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit O7 * pct>=0.7 dd>=12 delta_mult>=20 take win=10 persist=3 wall_ticks=8` | 47 | +0.6 / +0.6 / +0.0 | +0.0 | +0.0 | -0.4 | +0.3 / -0.4 | -67 / -36 | +0.8 | 46 / -4615 | 1 / +1920 | 0.01 / 0.34 | 0.76 / na | 5 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit O7 * pct>=0.7 imb5<=-0.1 dd>=12 take win=5 persist=3 wall_ticks=8` | 41 | +0.6 / +0.6 / +0.0 | +0.0 | +0.0 | -0.9 | +0.7 / +0.1 | +19 / -64 | -0.1 | 41 / -6229 | 0 / +0 | 0.01 / 0.49 | 0.99 / na | 4 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit O7 * pct>=0.3 pulled_mult>=50 lock 0 win=15 persist=1 wall_ticks=8` | 78 | +1.8 / +1.8 / +0.5 | +1.4 | -1.9 | +1.2 | +2.4 / -1.3 | +101 / -39 | -0.5 | 24 / -39061 | 54 / +31945 | 0.17 / 0.98 | 1.00 / na | 15 | OK-PRIOR [OK-PRIOR] |

### Top-20 by recents-first drawdown (promoted for exact via top20_O7.txt)

| # | line | nfire (of armed) | stack maxDD cut L6M / L3M / L1M | HOLD | PRE | X' | equal-MEAN cut L6M / PRE | d mean L6M / PRE $/wk | worst-20 cut L6M | clipped winners n / $ | non-winners caught n / $ | placebo p own L6M / PRE | family p (this set / top-300 lines) | WF beats % | Rule 2a [old] |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| 1 | `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8` | 255 | +4.8 / +4.8 / +2.4 | +1.5 | -1.0 | +2.9 | +6.0 / +0.2 | +218 / -459 | +4.0 | 178 / -150166 | 77 / +105319 | 0.01 / 0.97 | 1.00 / 1.00 | 19 | OK-PRIOR [OK-PRIOR] |
| 2 | `profit O7 * pct>=0.2 delta_mult>=5 take win=10 persist=10 wall_ticks=8` | 273 | +4.6 / +4.6 / +2.3 | +1.5 | -1.4 | +4.9 | +4.8 / -1.2 | +35 / -592 | -1.0 | 181 / -176436 | 92 / +114046 | 0.01 / 1.00 | 1.00 / 1.00 | 13 | OK-PRIOR [OK-PRIOR] |
| 3 | `profit O7 * pct>=0.4 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | 257 | +5.2 / +5.2 / +0.0 | +1.9 | +0.5 | +0.7 | +4.7 / +0.0 | -98 / -381 | -0.7 | 185 / -150145 | 72 / +106057 | 0.01 / 0.94 | 1.00 / 1.00 | 20 | OK-PRIOR [OK-PRIOR] |
| 4 | `profit O7 * pct>=0.3 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | 282 | +5.0 / +5.0 / +0.0 | +3.1 | +0.6 | +4.2 | +3.6 / -0.8 | -283 / -469 | -4.1 | 186 / -180962 | 96 / +125347 | 0.01 / 0.97 | 1.00 / 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 5 | `profit O7 * pct>=0.3 delta_mult>=5 imb5<=-0.1 take win=10 persist=1 wall_ticks=8` | 273 | +4.0 / +4.0 / +2.4 | +2.9 | -2.4 | +4.0 | +3.0 / -3.4 | -201 / -497 | -2.2 | 186 / -172620 | 87 / +114531 | 0.06 / 1.00 | 1.00 / 1.00 | 9 | OK-PRIOR [OK-PRIOR] |
| 6 | `profit O7 * pct>=0.3 pulled_against_mult>=20 step 10 win=10 persist=5 wall_ticks=8` | 267 | +4.1 / +4.1 / +1.9 | +3.2 | -0.4 | +2.6 | +4.5 / +0.1 | +83 / -456 | -0.3 | 174 / -164910 | 93 / +113714 | 0.11 / 1.00 | 1.00 / 1.00 | 13 | OK-PRIOR [OK-PRIOR] |
| 7 | `profit O7 * pct>=0.3 imb10<=-0.2 step 10 win=0 persist=1 wall_ticks=8` | 273 | +4.1 / +4.1 / +1.9 | +3.2 | +1.2 | +4.4 | +4.1 / +1.2 | +7 / -504 | -2.1 | 176 / -174523 | 97 / +116087 | 0.06 / 0.90 | 1.00 / 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 8 | `profit O7 * pct>=0.2 dd>=12 step 10 win=0 persist=10 wall_ticks=8` | 242 | +4.1 / +4.1 / +1.7 | +1.9 | -1.1 | +3.8 | +5.0 / -0.2 | +148 / -411 | +1.5 | 160 / -146613 | 82 / +101142 | 0.01 / 1.00 | 1.00 / 1.00 | 15 | OK-PRIOR [OK-PRIOR] |
| 9 | `profit O7 * pct>=0.9 take` | 167 | +1.0 / +1.0 / +0.0 | +0.0 | -0.4 | -1.3 | +0.6 / -0.9 | -84 / -94 | -0.5 | 166 / -7989 | 1 / +2183 | 1.00 / 1.00 | 1.00 / na | 8 | OK-PRIOR [OK-PRIOR] |
| 10 | `profit O7 * pct>=0.7 imb5<=-0.1 or pulled_against_mult>=10 take win=2 persist=3 wall_ticks=8` | 182 | +0.9 / +0.9 / +0.0 | +0.0 | -0.5 | +0.2 | +0.1 / -1.3 | -141 / -252 | -1.5 | 170 / -48177 | 12 / +24632 | 0.01 / 0.14 | 0.70 / na | 6 | OK-PRIOR [OK-PRIOR] |
| 11 | `profit O7 * pct>=0.8 take` | 192 | +0.8 / +0.8 / +0.0 | +0.0 | -0.5 | -2.4 | -0.0 / -1.4 | -159 / -146 | -1.4 | 183 / -37447 | 9 / +19235 | 1.00 / 1.00 | 1.00 / na | 6 | OK-PRIOR [OK-PRIOR] |
| 12 | `profit O7 * pct>=0.3 wall_ahead_mult>=5 step 10 win=0 persist=1 wall_ticks=8` | 267 | +4.1 / +4.1 / +1.7 | +3.2 | +0.2 | +3.6 | +4.6 / +0.7 | +89 / -553 | -0.2 | 176 / -170086 | 91 / +112016 | 0.11 / 1.00 | 1.00 / 1.00 | 19 | OK-PRIOR [OK-PRIOR] |
| 13 | `profit O7 * pct>=0.3 wall_ahead_mult>=5 step 10 win=0 persist=1 wall_ticks=20` | 269 | +4.1 / +4.1 / +1.7 | +3.2 | -0.4 | +3.6 | +4.3 / -0.2 | +27 / -587 | -1.7 | 177 / -174793 | 92 / +111912 | 0.07 / 0.99 | 1.00 / 1.00 | 13 | OK-PRIOR [OK-PRIOR] |
| 14 | `profit O7 * pct>=0.3 pulled_against_mult>=5 step 10 win=3 persist=5 wall_ticks=8` | 262 | +4.1 / +4.1 / +1.6 | +3.2 | -0.4 | +3.5 | +4.4 / -0.1 | +49 / -453 | -1.1 | 174 / -163520 | 88 / +109262 | 0.06 / 1.00 | 1.00 / 1.00 | 11 | OK-PRIOR [OK-PRIOR] |
| 15 | `profit O7 * pct>=0.4 imb10<=-0.1 step 10 win=0 persist=1 wall_ticks=8` | 254 | +4.1 / +4.1 / +1.6 | +1.9 | +1.2 | +2.1 | +4.3 / +1.4 | +33 / -395 | -1.5 | 174 / -156553 | 80 / +102855 | 0.08 / 0.18 | 0.93 / 1.00 | 18 | OK-PRIOR [OK-PRIOR] |
| 16 | `profit O7 * pct>=0.3 delta_mult>=2 tighten 5 win=10 persist=10 wall_ticks=8` | 254 | +4.6 / +4.6 / +2.1 | +2.1 | -1.0 | +2.7 | +5.8 / +0.2 | +213 / -455 | +3.8 | 177 / -150001 | 77 / +105711 | 0.01 / 1.00 | 1.00 / 1.00 | 19 | OK-PRIOR [OK-PRIOR] |
| 17 | `profit O7 * pct>=0.2 wall_ahead_mult>=5 lock 10 win=0 persist=1 wall_ticks=4` | 186 | +2.8 / +2.8 / +0.7 | +2.0 | -0.6 | +6.4 | +3.5 / +0.0 | +118 / -312 | -1.1 | 82 / -119903 | 104 / +86413 | 0.06 / 0.90 | 1.00 / na | 22 | OK-PRIOR [OK-PRIOR] |
| 18 | `profit O7 * pct>=0.3 delta_mult>=2 step 5 win=10 persist=10 wall_ticks=8` | 253 | +4.6 / +4.6 / +2.3 | +2.1 | -1.0 | +3.4 | +5.6 / +0.1 | +196 / -451 | +3.4 | 176 / -149283 | 77 / +105034 | 0.01 / 1.00 | 1.00 / 1.00 | 19 | OK-PRIOR [OK-PRIOR] |
| 19 | `profit O7 * pct>=0.2 delta_mult>=2 take win=8 persist=10 wall_ticks=8` | 278 | +4.6 / +4.6 / +2.2 | +2.7 | -1.4 | +4.6 | +4.7 / -1.3 | +10 / -608 | -0.5 | 182 / -180589 | 96 / +117515 | 0.01 / 1.00 | 1.00 / 1.00 | 9 | OK-PRIOR [OK-PRIOR] |
| 20 | `profit O7 * pct>=0.3 pulled_mult>=30 take win=15 persist=10 wall_ticks=8` | 239 | +3.9 / +3.9 / +2.4 | +2.1 | -1.7 | +2.5 | +3.4 / -2.3 | -98 / -400 | +0.1 | 168 / -137204 | 71 / +100288 | 0.11 / 1.00 | 1.00 / 1.00 | 16 | OK-PRIOR [OK-PRIOR] |


## Reading
- M7 / A7 / O7 profit lines that win on drawdown are early-take lines: arm 0.2-0.3 x target plus a market-pressure condition that is true on most trades after arming (sweep / pulled / delta), so they cut drawdown by realising small profits early and give up mean (M7 about -$0.6k per week on L6M); the equal-MEAN column shows how much of the cut survives when each line lots are rescaled to the live L6M mean (it is the honest comparison). The placebo (random exit at the same arm and count) shows whether the CONDITION adds anything beyond the early take: own p L6M is low for M7 but PRE own p is high; no line reaches family p <= .10 on PRE.
- Nothing here is a CANDIDATE: first-order only, WF below 60% on every line, and the exact rows are queued with SZ-IJK (PTR_<book>_<nn>).


## EXACT rows (SZ-IJK, ROLLFIX1 exact engine at slip 0.8, LPB base; ex_* = exact, FO = first-order screen; windows only where all months are present; equal-mean uses the LPB_BASE L6M mean 21495 $/wk)

### M7

| set | line | FO L6M cut | exact L6M cut / d mean / equal-mean | exact L3M cut / L1M cut | exact HOLD cut / d mean | PRE months | status |
|--|--|--|--|--|--|--|--|
| PTR_M7_01 | `profit M7 * pct>=0.2 sweep_against>=3 take win=8 persist=2 wall_ticks=8` | +32.7 | -24.9 / -1583 / -34.8 | +25.4 / -43.5 | -33.1 / -944 | 10/17 | PARTIAL |
| PTR_M7_02 | `profit M7 * pct>=0.2 pulled_mult>=3 take win=5 persist=3 wall_ticks=8` | +32.1 | -31.5 / -781 / -36.4 | +28.2 / -33.2 | -34.7 / -958 | 7/17 | PARTIAL |
| PTR_M7_03 | `profit M7 * pct>=0.2 pulled_mult>=3 tighten 5 win=5 persist=3 wall_ticks=8` | +31.7 | -14.7 / -1318 / -22.1 | +42.9 / -1.0 | na / na | nan | PARTIAL |
| PTR_M7_04 | `profit M7 * pct>=0.2 sweep_against>=4 take win=8 persist=2 wall_ticks=8` | +31.9 | -32.5 / -799 / -37.7 | +18.1 / -35.6 | na / na | nan | PARTIAL |
| PTR_M7_05 | `profit M7 * pct>=0.2 pulled_against_mult>=10 take win=5 persist=2 wall_ticks=8` | +31.6 | -17.4 / -1420 / -25.7 | +37.0 / -38.7 | na / na | nan | PARTIAL |
| PTR_M7_06 | `profit M7 * pct>=0.2 pulled_against_mult>=20 tighten 5 win=15 persist=2 wall_ticks=8` | +31.3 | na / na / na | na / -0.0 | na / na | nan | PARTIAL |
| PTR_M7_07 | `profit M7 * pct>=0.2 imb10<=-0.1 tighten 5 win=0 persist=1 wall_ticks=8` | +30.0 | na / na / na | na / +12.3 | na / na | nan | PARTIAL |
| PTR_M7_08 | `profit M7 * pct>=0.2 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | +30.2 | na / na / na | na / -16.9 | na / na | nan | PARTIAL |
| PTR_M7_09 | `profit M7 * pct>=0.6 ice_against>=1 tighten 20 win=30 persist=1 wall_ticks=8` | +14.5 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_10 | `profit M7 * pct>=0.5 dd>=3 step 20 win=0 persist=5 wall_ticks=8` | +13.0 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_11 | `profit M7 * pct>=0.6 ice_against>=1 tighten 20 win=30 persist=2 wall_ticks=8` | +14.9 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_12 | `profit M7 * pct>=0.5 dd>=5 take win=0 persist=1 wall_ticks=8` | +12.8 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_13 | `profit M7 * pct>=0.2 imb5<=-0.1 lock 5 win=0 persist=2 wall_ticks=8` | +25.8 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_14 | `profit M7 * pct>=0.2 imb10<=-0.1 lock 10 win=0 persist=3 wall_ticks=8` | +23.7 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_15 | `profit M7 * pct>=0.2 ahead_rel_slow>=1.5 lock 10 win=0 persist=1 wall_ticks=8` | +22.2 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_16 | `profit M7 * pct>=0.2 ahead_rel>=1.5 lock 10 win=0 persist=1 wall_ticks=8` | +21.0 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_17 | `profit M7 * pct>=0.2 sweep_against>=3 tighten 5 win=8 persist=2 wall_ticks=8` | +31.7 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_18 | `profit M7 * pct>=0.2 sweep_against>=3 lock 10 win=8 persist=2 wall_ticks=8` | +28.5 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_19 | `profit M7 * pct>=0.2 pulled_mult>=3 step 5 win=5 persist=3 wall_ticks=8` | +30.6 | na / na / na | na / na | na / na | nan | NONE |
| PTR_M7_20 | `profit M7 * pct>=0.2 sweep_against>=4 scale 0.5 win=8 persist=2 wall_ticks=8` | +9.7 | na / na / na | na / na | na / na | nan | NONE |

### A7

| set | line | FO L6M cut | exact L6M cut / d mean / equal-mean | exact L3M cut / L1M cut | exact HOLD cut / d mean | PRE months | status |
|--|--|--|--|--|--|--|--|
| PTR_A7_01 | `profit A7 * pct>=0.3 delta_mult>=2 tighten 5 win=2 persist=2 wall_ticks=8` | +9.9 | +28.7 / -146 / +28.2 | +4.1 / +31.8 | +4.1 / -58 | 12/17 | PARTIAL |
| PTR_A7_02 | `profit A7 * pct>=0.3 pulled_against_mult>=30 or pulled_mult>=20 take win=10 persist=3 wall_ticks=8` | +10.3 | +35.5 / -18 / +35.4 | +44.9 / +55.2 | +36.2 / +150 | 11/17 | PARTIAL |
| PTR_A7_03 | `profit A7 * pct>=0.2 pulled_against_mult>=30 take win=10 persist=5 wall_ticks=8` | +10.0 | +24.6 / +340 / +25.7 | +9.0 / +50.9 | na / na | nan | PARTIAL |
| PTR_A7_04 | `profit A7 * pct>=0.3 pulled_mult>=30 sweep_against>=6 take win=15 persist=1 wall_ticks=8` | +10.1 | +28.9 / +3 / +28.9 | +64.4 / +74.8 | na / na | nan | PARTIAL |
| PTR_A7_05 | `profit A7 * pct>=0.2 pulled_against_mult>=50 take win=15 persist=2 wall_ticks=8` | +10.4 | +30.2 / +97 / +30.5 | +16.2 / +38.5 | na / na | nan | PARTIAL |
| PTR_A7_06 | `profit A7 * pct>=0.3 pulled_mult>=30 take win=15 persist=2 wall_ticks=8` | +9.8 | +39.2 / +4 / +39.3 | +52.9 / +48.8 | na / na | nan | PARTIAL |
| PTR_A7_07 | `profit A7 * pct>=0.3 pulled_mult>=30 take win=15 persist=1 wall_ticks=8` | +9.9 | +32.3 / +44 / +32.4 | +64.4 / +75.3 | na / na | nan | PARTIAL |
| PTR_A7_08 | `profit A7 * pct>=0.2 sweep_against>=6 step 10 win=5 persist=10 wall_ticks=8` | +9.1 | -7.4 / -75 / -7.7 | -23.7 / +14.4 | na / na | nan | PARTIAL |
| PTR_A7_09 | `profit A7 * pct>=0.5 take` | +6.4 | +46.6 / -14 / +46.6 | +67.3 / +100.0 | na / na | nan | PARTIAL |
| PTR_A7_10 | `profit A7 * pct>=0.5 tighten 5` | +6.4 | +44.1 / +242 / +44.7 | +55.1 / +100.0 | na / na | nan | PARTIAL |
| PTR_A7_11 | `profit A7 * pct>=0.5 wall_ahead_mult>=5 step 10 win=0 persist=3 wall_ticks=4` | +3.8 | na / na / na | +59.4 / +69.4 | na / na | nan | PARTIAL |
| PTR_A7_12 | `profit A7 * pct>=0.5 wall_ahead_mult>=5 tighten 5 win=0 persist=3 wall_ticks=4` | +3.5 | na / na / na | +66.8 / +89.2 | na / na | nan | PARTIAL |
| PTR_A7_13 | `profit A7 * pct>=0.2 sweep_against>=4 take win=8 persist=10 wall_ticks=8` | +8.8 | na / na / na | +34.6 / +59.1 | na / na | nan | PARTIAL |
| PTR_A7_14 | `profit A7 * pct>=0.3 delta_mult>=2 take win=5 persist=1 wall_ticks=8` | +8.9 | na / na / na | na / +3.3 | na / na | nan | PARTIAL |
| PTR_A7_15 | `profit A7 * pct>=0.4 dd>=5 take win=0 persist=1 wall_ticks=8` | +6.4 | na / na / na | na / +100.0 | na / na | nan | PARTIAL |
| PTR_A7_16 | `profit A7 * pct>=0.4 dd>=5 tighten 5 win=0 persist=1 wall_ticks=8` | +6.4 | na / na / na | na / +100.0 | na / na | nan | PARTIAL |
| PTR_A7_17 | `profit A7 * pct>=0.2 pulled_against_mult>=30 tighten 5 win=10 persist=5 wall_ticks=8` | +9.6 | na / na / na | na / +39.6 | na / na | nan | PARTIAL |
| PTR_A7_18 | `profit A7 * pct>=0.2 sweep_against>=4 lock 10 win=8 persist=10 wall_ticks=8` | +7.2 | na / na / na | na / +48.7 | na / na | nan | PARTIAL |
| PTR_A7_19 | `profit A7 * pct>=0.3 delta_mult>=2 step 5 win=2 persist=2 wall_ticks=8` | +9.3 | na / na / na | na / +45.2 | na / na | nan | PARTIAL |
| PTR_A7_20 | `profit A7 * pct>=0.3 sweep_against>=6 pulled_mult>=10 take win=3 persist=1 wall_ticks=8` | +10.1 | na / na / na | na / +49.4 | na / na | nan | PARTIAL |

### O7

| set | line | FO L6M cut | exact L6M cut / d mean / equal-mean | exact L3M cut / L1M cut | exact HOLD cut / d mean | PRE months | status |
|--|--|--|--|--|--|--|--|
| PTR_O7_01 | `profit O7 * pct>=0.3 delta_mult>=2 take win=10 persist=10 wall_ticks=8` | +4.8 | +17.4 / +30 / +17.5 | +58.3 / +63.1 | +17.4 / -127 | 6/17 | PARTIAL |
| PTR_O7_02 | `profit O7 * pct>=0.2 delta_mult>=5 take win=10 persist=10 wall_ticks=8` | +4.6 | -2.1 / +48 / -1.8 | +47.5 / +61.8 | -2.1 / -197 | 2/17 | PARTIAL |
| PTR_O7_03 | `profit O7 * pct>=0.4 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | +5.2 | +23.5 / -99 / +23.2 | +39.9 / +36.2 | na / na | nan | PARTIAL |
| PTR_O7_04 | `profit O7 * pct>=0.3 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` | +5.0 | +11.0 / -276 / +9.9 | +57.1 / +62.2 | na / na | nan | PARTIAL |
| PTR_O7_05 | `profit O7 * pct>=0.3 delta_mult>=5 imb5<=-0.1 take win=10 persist=1 wall_ticks=8` | +4.0 | +8.4 / -228 / +7.4 | +57.3 / +63.7 | na / na | nan | PARTIAL |
| PTR_O7_06 | `profit O7 * pct>=0.3 pulled_against_mult>=20 step 10 win=10 persist=5 wall_ticks=8` | +4.1 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_07 | `profit O7 * pct>=0.3 imb10<=-0.2 step 10 win=0 persist=1 wall_ticks=8` | +4.1 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_08 | `profit O7 * pct>=0.2 dd>=12 step 10 win=0 persist=10 wall_ticks=8` | +4.1 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_09 | `profit O7 * pct>=0.9 take` | +1.0 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_10 | `profit O7 * pct>=0.7 imb5<=-0.1 or pulled_against_mult>=10 take win=2 persist=3 wall_ticks=8` | +0.9 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_11 | `profit O7 * pct>=0.8 take` | +0.8 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_12 | `profit O7 * pct>=0.3 wall_ahead_mult>=5 step 10 win=0 persist=1 wall_ticks=8` | +4.1 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_13 | `profit O7 * pct>=0.3 wall_ahead_mult>=5 step 10 win=0 persist=1 wall_ticks=20` | +4.1 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_14 | `profit O7 * pct>=0.3 pulled_against_mult>=5 step 10 win=3 persist=5 wall_ticks=8` | +4.1 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_15 | `profit O7 * pct>=0.4 imb10<=-0.1 step 10 win=0 persist=1 wall_ticks=8` | +4.1 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_16 | `profit O7 * pct>=0.3 delta_mult>=2 tighten 5 win=10 persist=10 wall_ticks=8` | +4.6 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_17 | `profit O7 * pct>=0.2 wall_ahead_mult>=5 lock 10 win=0 persist=1 wall_ticks=4` | +2.8 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_18 | `profit O7 * pct>=0.3 delta_mult>=2 step 5 win=10 persist=10 wall_ticks=8` | +4.6 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_19 | `profit O7 * pct>=0.2 delta_mult>=2 take win=8 persist=10 wall_ticks=8` | +4.6 | na / na / na | na / na | na / na | nan | NONE |
| PTR_O7_20 | `profit O7 * pct>=0.3 pulled_mult>=30 take win=15 persist=10 wall_ticks=8` | +3.9 | na / na / na | na / na | na / na | nan | NONE |


Best exact line per book so far (by exact L6M cut): M7 `profit M7 * pct>=0.2 pulled_mult>=3 tighten 5 win=5 persist=3 wall_ticks=8` exact L6M -14.7 / HOLD na / equal-mean -22.1; A7 `profit A7 * pct>=0.5 take` exact L6M +46.6 / HOLD na / equal-mean +46.6; O7 `profit O7 * pct>=0.4 imb5<=-0.1 take win=0 persist=2 wall_ticks=8` exact L6M +23.5 / HOLD na / equal-mean +23.2


**Exact vs first-order:** wherever exact windows exist, the exact engine (re-entries, locks, slice fills, the live ThL2 branch) disagrees with the first-order screen for the early-take lines: a line that cuts the stack maxDD in the screen can be DEEPER in the engine because the book re-enters after the early exit. Only the exact columns carry a verdict; the first-order tables above are rankings. Rule 2a labels need exact PRE and are therefore pending for the exact rows.
