# DEPTH_BOOK_LOCK_INFO: why the depth book (L578701ed) was locked out, BookLock counts, screen rows, London book frequency

Written 2026-11-23 by W-LOCKINFO (order 0740Z; Josh: "why was depth book locked out?", "ask yes", "ALSO what is the trade frequency for the London book"). INFORMATION ONLY from results already on disk (landed set months, trades, bare events, screen/joint state): no new engine runs, no queue rows, no gate or rule change. Numbers are truly bare engine, 1-lot units of the lot basis shown, net of $4.84 per lot round trip; ulcer / max DD / worst week / $ per week unless stated.

## 0. The plain answer

On the first live night the lock fired inside ONE trade. BookLock BL2 = arm 1.5 R, give-back 50%, weekly floor -12 R, evaluated per book on day P&L (closed + open). For L578701ed (stop 30 pts, target 90 pts) R = 30 pts x $20 x base lots, so arming needs the book's DAY P&L to reach +45 pts-equivalent: a single winner running +49 pts arms it, and a pull-back to half the day peak (+24.5 pts) fires it: the open trade is closed (exit name BookLock) and the book is halted until the next Globex day roll (18:00 ET). With a 30 stop / 90 target the lock can arm and fire inside one trade, exactly as the relay described. That is the rule as tested and fitted (BL2 is in the delivered 4-lot pick BF4_JT1), not a bug.

How often (L578701ed, pinned stack + each lot basis's own joint pick; every number is from the landed trades, "first trade" = the BookLock exit was the book's first trade of that Globex night):

| lot basis (pick, its BL) | window | nights traded | BookLock exits (nights) | of which inside the FIRST trade of the night | later bare events per lock night | bare P&L of the book after the lock (same nights) |
|---|---|---|---|---|---|---|
| 1 lot (BF1_JT57, BL1 arm 1.5R give-back 33%) | L6 | 130 | 89 (89) | 44 (49% of lock nights, 34% of nights) | 15.9 | $+17952 |
| 1 lot (BF1_JT57, BL1 arm 1.5R give-back 33%) | L3 | 64 | 42 (42) | 24 (57% of lock nights, 38% of nights) | 14.2 | $+5610 |
| 1 lot (BF1_JT57, BL1 arm 1.5R give-back 33%) | 2023 | 194 | 31 (31) | 30 (97% of lock nights, 15% of nights) | 9.5 | $+2676 |
| 1 lot (BF1_JT57, BL1 arm 1.5R give-back 33%) | 2024 | 259 | 76 (76) | 57 (75% of lock nights, 22% of nights) | 11.7 | $-392 |
| 1 lot (BF1_JT57, BL1 arm 1.5R give-back 33%) | 2025 | 237 | 103 (103) | 63 (61% of lock nights, 27% of nights) | 14.7 | $-14205 |
| 2 lot (BF2_JT19, BL2 arm 1.5R give-back 50%) | L6 | 131 | 51 (51) | 3 (6% of lock nights, 2% of nights) | 12.9 | $-29980 |
| 2 lot (BF2_JT19, BL2 arm 1.5R give-back 50%) | L3 | 65 | 25 (25) | 1 (4% of lock nights, 2% of nights) | 11.5 | $-17159 |
| 2 lot (BF2_JT19, BL2 arm 1.5R give-back 50%) | 2023 | 194 | 11 (11) | 7 (64% of lock nights, 4% of nights) | 8.1 | $+1811 |
| 2 lot (BF2_JT19, BL2 arm 1.5R give-back 50%) | 2024 | 259 | 28 (28) | 3 (11% of lock nights, 1% of nights) | 8.7 | $-1903 |
| 2 lot (BF2_JT19, BL2 arm 1.5R give-back 50%) | 2025 | 238 | 35 (35) | 6 (17% of lock nights, 3% of nights) | 12.8 | $-12253 |
| 4 lot (BF4_JT1, BL2 arm 1.5R give-back 50%) | L6 | 131 | 59 (59) | 12 (20% of lock nights, 9% of nights) | 14.2 | $-35192 |
| 4 lot (BF4_JT1, BL2 arm 1.5R give-back 50%) | L3 | 65 | 26 (26) | 3 (12% of lock nights, 5% of nights) | 12.3 | $-30296 |
| 4 lot (BF4_JT1, BL2 arm 1.5R give-back 50%) | 2023 | 194 | 14 (14) | 12 (86% of lock nights, 6% of nights) | 8.9 | $+351 |
| 4 lot (BF4_JT1, BL2 arm 1.5R give-back 50%) | 2024 | 259 | 31 (31) | 11 (35% of lock nights, 4% of nights) | 12.5 | $+2731 |
| 4 lot (BF4_JT1, BL2 arm 1.5R give-back 50%) | 2025 | 238 | 50 (50) | 14 (28% of lock nights, 6% of nights) | 13.0 | $-7173 |

Reading (L578701ed): at 4 lots with BF4_JT1 (the pick the build uses) the lock ended the book's night on 59 of 131 nights in the last 6 months (45%), 26 of 59 with a positive exit; only 12 of those 59 were inside the first trade (9% of nights), 47 came after earlier trades the same night. Later signals dropped: about 14 per lock night (the depth book fires many events a night). On those nights the bare book (no lock, no other layer) would have lost $35,192 over the last 6 months after the lock point, so the lock saved money at 4 lots in L6M and L3M (-$30,296 over 26 nights); in 2023-2024 the dropped trades were about break-even (+$351 / +$2,731) and in 2025 -$7,173. At 1 lot (BF1_JT57, give-back 33%) the lock fires on 89 of 130 nights (68%), 44 inside the first trade, and the dropped bare trades were +$17,952 in L6M: there the lock cost money. At 2 lots (BF2_JT19) it fires on 51 of 131 nights, only 3 inside the first trade, dropped bare trades -$29,980 (lock helped). The "bare P&L after the lock" uses the lock-off, layer-free bare run (BF<lots>_BASE) trades entered after the lock exit on the same night: directional, not exact (other layers in the pick change the path).

Caveat on the live night: the live run was 2 lots with the BF4_JT1 settings; BF4_JT1 exists only as a 4-lot-basis run, so the 2-lot rows above use BF2_JT19 (the 2-lot pick, also BL2); the engine's lin form scales dollars with lots so R is the same in points.

## 1. L578701ed counts per lot basis and window: the table above. Nights traded and trades per window are in the same rows of lock2.json (scratchpad copy: code/th_lockinfo/lock2.json).

## 2. The other four books (BookLock exits on nights / first-trade; later events per lock night), L6M and 2025

**1 lot (BF1_JT57)**

- MF1 Lb0e6dfa3 (stop 40): L6M 70 exits on 70 of 130 nights, 26 inside the first trade, later events 6.5 per lock night, bare P&L after lock $+12255; L3M 33 exits (first-trade 16); 2025 47 exits (first-trade 16).
- MF2 L385f4f2e.J502 (stop 60): L6M 13 exits on 13 of 96 nights, 0 inside the first trade, later events 0.5 per lock night, bare P&L after lock $-2069; L3M 5 exits (first-trade 0); 2025 3 exits (first-trade 0).
- MF3 L92a90948 (stop 60): L6M 0 exits on 0 of 109 nights, 0 inside the first trade, later events 0.0 per lock night, bare P&L after lock $+0; L3M 0 exits (first-trade 0); 2025 0 exits (first-trade 0).
- MF4 L6b373671 (stop 60): L6M 20 exits on 20 of 120 nights, 0 inside the first trade, later events 3.9 per lock night, bare P&L after lock $+4468; L3M 8 exits (first-trade 0); 2025 8 exits (first-trade 0).

**2 lot (BF2_JT19)**

- MF1 Lb0e6dfa3 (stop 40): L6M 29 exits on 29 of 130 nights, 5 inside the first trade, later events 5.3 per lock night, bare P&L after lock $+28717; L3M 13 exits (first-trade 3); 2025 14 exits (first-trade 8).
- MF2 L385f4f2e.J502 (stop 60): L6M 1 exits on 1 of 96 nights, 0 inside the first trade, later events 0.0 per lock night, bare P&L after lock $+0; L3M 0 exits (first-trade 0); 2025 1 exits (first-trade 0).
- MF3 L92a90948 (stop 60): L6M 0 exits on 0 of 123 nights, 0 inside the first trade, later events 0.0 per lock night, bare P&L after lock $+0; L3M 0 exits (first-trade 0); 2025 0 exits (first-trade 0).
- MF4 L6b373671 (stop 60): L6M 6 exits on 6 of 120 nights, 0 inside the first trade, later events 5.2 per lock night, bare P&L after lock $+3740; L3M 1 exits (first-trade 0); 2025 4 exits (first-trade 0).

**4 lot (BF4_JT1)**

- MF1 Lb0e6dfa3 (stop 40): L6M 46 exits on 46 of 131 nights, 12 inside the first trade, later events 5.7 per lock night, bare P&L after lock $+15778; L3M 19 exits (first-trade 6); 2025 23 exits (first-trade 10).
- MF2 L385f4f2e.J502 (stop 60): L6M 0 exits on 0 of 96 nights, 0 inside the first trade, later events 0.0 per lock night, bare P&L after lock $+0; L3M 0 exits (first-trade 0); 2025 1 exits (first-trade 0).
- MF3 L92a90948 (stop 60): L6M 1 exits on 1 of 103 nights, 0 inside the first trade, later events 0.0 per lock night, bare P&L after lock $+0; L3M 1 exits (first-trade 0); 2025 0 exits (first-trade 0).
- MF4 L6b373671 (stop 60): L6M 5 exits on 5 of 120 nights, 0 inside the first trade, later events 5.8 per lock night, bare P&L after lock $-2502; L3M 1 exits (first-trade 0); 2025 2 exits (first-trade 0).

A single trade arms the lock less often on the 40/60-point books (R = $800 or $1,200 per lot): MF1 (stop 40, target 80) is the only other book that is locked regularly (29-70 L6M exits depending on the lot basis); MF2 (J502) and MF3 almost never; MF4 a few times, mostly with a losing exit.

## 3. Screen rows: BookLock off, BL2 and the later-arming levels (BL4-BL9 = arm 2 R and 3 R), L6M, truly bare, ALL FIVE books carry the same BL level in each row

Cells: ulcer / max DD / worst week / $ per week. "stack" = the five-book stack; "L578701ed" = that book's own P&L inside the same row (books are independent in the bare stack, so a book's own numbers are exact for that BL level).

**1 lot per book**

| level | meaning | stack L6M | L578701ed L6M | stack L3M |
|---|---|---|---|---|
| OFF | lock off (reference) | 3046 / -9450 / -4971 / 10834 | 3357 / -9315 / -5427 / 2909 | 3374 / -9282 / -1858 / 10600 |
| BL1 | arm 1.5R give-back 33% | 1866 / -7830 / -3064 / 9544 | 3230 / -11258 / -6656 / 2205 | 1597 / -5942 / -1324 / 10278 |
| BL2 | arm 1.5R give-back 50% | 2134 / -8600 / -3405 / 9643 | 3170 / -10668 / -6066 / 2500 | 1784 / -6137 / -1799 / 10633 |
| BL3 | arm 1.5R give-back 67% | 2493 / -9270 / -6315 / 9634 | 3297 / -10668 / -6066 / 2500 | 2158 / -6511 / -2718 / 10478 |
| BL4 | arm 2R give-back 33% | 2456 / -8109 / -3064 / 10364 | 2986 / -10733 / -6131 / 3046 | 2964 / -8109 / -1023 / 10369 |
| BL5 | arm 2R give-back 50% (today's D7) | 2586 / -8519 / -3344 / 10883 | 2920 / -10668 / -6066 / 3224 | 3071 / -8519 / -928 / 11125 |
| BL6 | arm 2R give-back 67% | 2820 / -8859 / -4153 / 10359 | 3038 / -10668 / -6066 / 3025 | 3313 / -8859 / -1268 / 10850 |
| BL7 | arm 3R give-back 33% | 2832 / -9282 / -4448 / 10400 | 3065 / -8613 / -3982 / 2830 | 3256 / -9282 / -1858 / 10884 |
| BL8 | arm 3R give-back 50% | 2830 / -8819 / -4448 / 11029 | 3164 / -10668 / -6066 / 3051 | 3201 / -8819 / -1228 / 11347 |
| BL9 | arm 3R give-back 67% | 2914 / -8819 / -4448 / 10858 | 3199 / -10668 / -6066 / 2989 | 3179 / -8819 / -1228 / 11432 |
| BL10 | arm 2R 50%, weekly floor -8R | 2586 / -8519 / -3344 / 10413 | 2556 / -8343 / -4237 / 2754 | 3072 / -8519 / -928 / 10150 |
| BL11 | arm 2R 50%, weekly floor -12R | 2586 / -8519 / -3344 / 10883 | 2920 / -10668 / -6066 / 3224 | 3071 / -8519 / -928 / 11125 |
| BL12 | arm 2R 50%, weekly floor -16R | 2644 / -8982 / -3344 / 10920 | 2755 / -9665 / -4434 / 3261 | 3170 / -8982 / -1558 / 11202 |

**2 lot per book**

| level | meaning | stack L6M | L578701ed L6M | stack L3M |
|---|---|---|---|---|
| OFF | lock off (reference) | 6962 / -21015 / -19862 / 20494 | 7868 / -21429 / -20570 / 5283 | 7360 / -21015 / -6171 / 20066 |
| BL1 | arm 1.5R give-back 33% | 4240 / -15885 / -6173 / 18608 | 6543 / -22686 / -13363 / 4346 | 4141 / -12015 / -5043 / 19839 |
| BL2 | arm 1.5R give-back 50% | 4858 / -17340 / -7091 / 18752 | 6421 / -21491 / -12168 / 4977 | 4765 / -12405 / -5997 / 20528 |
| BL3 | arm 1.5R give-back 67% | 5247 / -18765 / -12895 / 18556 | 6682 / -21476 / -12153 / 4830 | 4761 / -12928 / -7822 / 19866 |
| BL4 | arm 2R give-back 33% | 5337 / -18593 / -6173 / 20388 | 6039 / -21631 / -12308 / 6006 | 6582 / -18593 / -4442 / 19937 |
| BL5 | arm 2R give-back 50% (today's D7) | 5580 / -19418 / -6733 / 21322 | 5900 / -21491 / -12168 / 6313 | 6788 / -19418 / -4825 / 21272 |
| BL6 | arm 2R give-back 67% | 6040 / -20077 / -8597 / 20170 | 6143 / -21476 / -12153 / 5877 | 7262 / -20077 / -5975 / 20611 |
| BL7 | arm 3R give-back 33% | 6330 / -20032 / -12442 / 19289 | 7933 / -21769 / -14029 / 4827 | 6925 / -20032 / -4867 / 20175 |
| BL8 | arm 3R give-back 50% | 6385 / -20032 / -13362 / 20841 | 7341 / -21491 / -14069 / 5539 | 6989 / -20032 / -4867 / 21554 |
| BL9 | arm 3R give-back 67% | 6601 / -20032 / -14144 / 20406 | 7021 / -21476 / -13971 / 5346 | 6950 / -20032 / -4867 / 21690 |
| BL10 | arm 2R 50%, weekly floor -8R | 5776 / -19418 / -6733 / 20036 | 5146 / -16717 / -8519 / 5372 | 6784 / -19418 / -4252 / 19318 |
| BL11 | arm 2R 50%, weekly floor -12R | 5580 / -19418 / -6733 / 21322 | 5900 / -21491 / -12168 / 6313 | 6788 / -19418 / -4825 / 21272 |
| BL12 | arm 2R 50%, weekly floor -16R | 5712 / -20400 / -6733 / 21390 | 5615 / -19676 / -9049 / 6380 | 7006 / -20400 / -5556 / 21411 |

**4 lot per book**

| level | meaning | stack L6M | L578701ed L6M | stack L3M |
|---|---|---|---|---|
| OFF | lock off (reference) | 15687 / -52365 / -40859 / 38612 | 16198 / -43328 / -41505 / 9959 | 16860 / -52365 / -22627 / 39295 |
| BL1 | arm 1.5R give-back 33% | 8966 / -31345 / -12401 / 35622 | 13216 / -45628 / -26772 / 8262 | 8513 / -24340 / -10621 / 38630 |
| BL2 | arm 1.5R give-back 50% | 10486 / -34425 / -15213 / 35264 | 12886 / -43202 / -24347 / 9459 | 10017 / -25130 / -13806 / 39903 |
| BL3 | arm 1.5R give-back 67% | 11148 / -37115 / -26702 / 35473 | 13436 / -43223 / -24367 / 9222 | 9632 / -26171 / -17226 / 39491 |
| BL4 | arm 2R give-back 33% | 12957 / -50205 / -21929 / 38631 | 12146 / -43527 / -24672 / 11701 | 16399 / -50205 / -21929 / 38517 |
| BL5 | arm 2R give-back 50% (today's D7) | 12986 / -50205 / -19914 / 40330 | 11855 / -43202 / -24347 / 12279 | 16084 / -50205 / -19914 / 41546 |
| BL6 | arm 2R give-back 67% | 13595 / -50205 / -19914 / 38167 | 12233 / -43223 / -24367 / 11425 | 16469 / -50205 / -19914 / 40425 |
| BL7 | arm 3R give-back 33% | 14437 / -50205 / -25530 / 35716 | 16116 / -43553 / -28024 / 8586 | 16180 / -50205 / -19914 / 39563 |
| BL8 | arm 3R give-back 50% | 14396 / -50205 / -27084 / 38680 | 15224 / -43202 / -27817 / 9854 | 16021 / -50205 / -19914 / 42298 |
| BL9 | arm 3R give-back 67% | 15034 / -50205 / -28834 / 38061 | 14526 / -43223 / -27777 / 9708 | 15957 / -50205 / -19914 / 42565 |
| BL10 | arm 2R 50%, weekly floor -8R | 13407 / -50205 / -19914 / 37786 | 10335 / -33575 / -17084 / 10414 | 16078 / -50205 / -19914 / 37672 |
| BL11 | arm 2R 50%, weekly floor -12R | 12986 / -50205 / -19914 / 40330 | 11855 / -43202 / -24347 / 12279 | 16084 / -50205 / -19914 / 41546 |
| BL12 | arm 2R 50%, weekly floor -16R | 13342 / -52365 / -22627 / 40570 | 10615 / -36727 / -16318 / 12518 | 16661 / -52365 / -22627 / 42044 |

Per-book effect of BL1 / BL2 vs off on each book (L6M, ulcer / max DD / $ per week), from the same rows:

| lots | book | off | BL1 | BL2 |
|---|---|---|---|---|
| 1 | MF1 | 2642/-8614/2968 | 2619/-8166/2275 | 2806/-8811/2215 |
| 1 | MF2 | 492/-1914/2122 | 491/-1914/2182 | 491/-1914/2131 |
| 1 | MF3 | 2687/-6973/612 | 2896/-7908/649 | 2893/-7693/659 |
| 1 | MF4 | 2390/-8707/2305 | 2213/-8707/2317 | 2298/-8707/2219 |
| 1 | MF5 | 3357/-9315/2909 | 3230/-11258/2205 | 3170/-10668/2500 |
| 2 | MF1 | 5548/-18813/5760 | 5525/-16836/4442 | 5810/-17903/4235 |
| 2 | MF2 | 1060/-3844/4142 | 1059/-3844/4264 | 1059/-3844/4163 |
| 2 | MF3 | 5645/-13976/1051 | 5928/-15916/1125 | 5946/-15481/1148 |
| 2 | MF4 | 4843/-17529/4419 | 4477/-17529/4599 | 4648/-17529/4390 |
| 2 | MF5 | 7868/-21429/5283 | 6543/-22686/4346 | 6421/-21491/4977 |
| 4 | MF1 | 13829/-47711/10672 | 11355/-34976/8611 | 12143/-36324/8158 |
| 4 | MF2 | 2139/-7758/8421 | 2139/-7758/8355 | 2141/-7758/8245 |
| 4 | MF3 | 13509/-29823/1701 | 14419/-32192/1690 | 14519/-31332/1773 |
| 4 | MF4 | 9979/-35344/8160 | 9283/-35344/9037 | 9727/-35344/7920 |
| 4 | MF5 | 16198/-43328/9959 | 13216/-45628/8262 | 12886/-43202/9459 |

Reading: for L578701ed alone the lock is mild at 2-4 lots (BL2: ulcer -18% / -20%, dollars -6% / -5%, max DD about equal) and costs more at 1 lot (BL2: dollars -14%, max DD 15% worse; BL1 -24% dollars). The big stack-level cut comes from the other books, mainly MF1 (4 lots: max DD -24%, ulcer -12%, dollars -24% with BL2). BL1 (give-back 33%) is the strongest stack risk cut on the screen (1 lot ulcer 3,046 -> 1,866).

**Was BookLock scored per book?** No. In the screen and in the joint BL is ONE stack-wide factor: the same BL level (BL1..BL12) is applied to all five books (mf_multi reads a single lin.bl tuple for every book in CFG). The joint carries only the two best screen levels of the factor plus off (BL1 and BL2 in all three lot bases; 27 / 27 / 26 combos), so the arm-2R / arm-3R levels (BL4-BL9) never entered the joint. A per-book BL level needs: (a) a hook change, not an engine edit: a check_book_lock override in the layer-hook layer (as dl_hooks.py does for open P&L) that reads a per-tag [arm, give-back, floor] table, or a one-line change of the single BLP tuple to a dict by tag in mf_multi.check_book_lock (engine file: needs the rows-in-flight caution); (b) new factors BL.MF1..BL.MF5 (12 levels each) in barefit_gen / barefit_joint plus new screen rows (about 5 x 12 x 3 lot bases of 6-month rows = 540) and a joint re-run. In the TRULY BARE stack the books are independent, so a per-book combination can also be composed exactly from the existing rows above with no new run; once StackCut / CAP / STK are in the pick the books interact and exact rows are needed.

## 4. Engine rule for the D8 port (read from code/replica/sim.py check_book_lock and code/th_combo/mf_multi.py check_book_lock, lin form)

- Open (unrealised) P&L counts: day = day_pnl + unreal(px); week = week_pnl + unreal(px); the day peak gb_peak = max over the Globex day of day. CONFIRMED.
- Evaluation: NOT at every price update: it runs at most every 2 seconds (sim.py: if now - last_lock >= 2 s) on the last print price, for every book that is not already locked, whether or not it is in a trade (a flat book has unreal = 0). While a book holds a position that is the moment the lock can fire. For the port: evaluate on the mark price at least every 2 s. CONFIRMED with this correction of "every price update".
- R = base lots x max(1, size_mult) x the book's own stop pts x $20 (b.base_qty is the configured base lot count of the book); the ER-sizer halving (size_mult < 1) and the no-trade-set halving do NOT shrink R. CONFIRMED.
- Rules: weekly floor first: week <= floor x R (floor -12, stored negative) -> book locked for the day AND the week; else give-back lock: day peak >= arm x R and day <= peak x (1 - give-back) -> book locked for the day; the open position exits at market (exit name BookLock).
- Halt duration: the lock sets day_halt; it is cleared at the next Globex session roll (the first 1-minute bar whose session key changes: the key changes at 18:00 ET), so the halt lasts to the next 18:00 ET roll, i.e. the rest of the trading day, not only the 02:00 ET Asia session end. A weekly-floor halt (week_halt) lasts until the first bar of the next week (Monday). gb_peak and gb_locked reset at the roll. CONFIRMED (the relay's "to the end of the session" = to the 18:00 ET Globex roll).

## 5. London book L19201dfc.BRF90_30 (bare, trend_20 + CL "against" trigger, bracket stop 90 / target 30, London window 02:00-08:30 ET)

Source: the landed bare set TL3_ALN_LO_L19201dfc_R0BRF90_30 (42 months 2023-04..2026-10 are on disk and DONE, 1,141 trades, 1 lot, one-position rule, session-end exit UWTime) and the engine event file (1,768 events). "Session" = a weekday (Mon-Fri) in the window; holidays are not removed (so the zero-trade share is slightly overstated). Events = signals; trades = filled positions; the one-position rule (a signal while a position is open) accounts for most of the difference.

| window | sessions | trades | mean trades per session | median | sessions with 0 trades | busiest session | events per session | events not traded per session |
|---|---|---|---|---|---|---|---|---|
| L6M (2026-05..10) | 131 | 247 | 1.89 | 1 | 17.6% | 8 (2026-05-06) | 2.41 | 0.53 |
| L3M (2026-08..10) | 65 | 116 | 1.78 | 2 | 20.0% | 6 (2026-08-25) | 2.34 | 0.55 |
| 2023 (Apr-Dec) | 195 | 186 | 0.95 | 1 | 25.6% | 3 (2023-05-30) | 1.58 | 0.63 |
| 2024 | 262 | 260 | 0.99 | 1 | 33.2% | 7 (2024-08-05) | 1.64 | 0.65 |
| 2025 (Jan-Oct, Dec) | 241 | 301 | 1.25 | 1 | 27.0% | 11 (2025-04-04) | 1.80 | 0.56 |

Distribution of trades per session, L6M: 0 trades 23 sessions, 1 trade 43, 2 trades 24, 3 trades 24, 4 trades 8, 5 trades 5, 6+ trades 4. Exit mix over all 1,141 trades: Target 682 (60%), UWTime session-end 345 (30%), Stop 114 (10%). London trade frequency has risen: about 1 trade per session in 2023-2024, 1.25 in 2025 and about 1.8-1.9 in the last 6 months.

## 6. Is BL a joint family in the Asia joint re-run with the daily-loss family?

Yes as a STACK-WIDE factor with only its two best screen levels (BL1, BL2) plus off (the existing joint: 27 / 27 / 26 combos each). The re-run uses the same top-2-per-factor rule (barefit_joint.rank), so the arm level will vary only over BL1 / BL2 (arm 1.5 R, give-back 33% / 50%); the later-arming levels BL4-BL9 are screened but not carried. Letting the joint carry more BL levels (top-3 / top-4, or the arm-2R / arm-3R pair) is an orthogonal-array size change in barefit_joint.py, not a free option: ask W-LAYERS2 if wanted. Not changed here.

No recommendation; Josh decides what, if anything, to test next.
