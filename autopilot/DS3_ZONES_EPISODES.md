# DS3 ZONES EPISODES - drawdown episodes of the D7 v1.3 EXACT base (V13X, shipped layer), BASE-4

For each window and frame the top-3 episodes of the weekly-cumulative equity (ISO weeks, label-day weeks). Episode = peak week (last week at the old high) -> trough week -> recovery week (first week back at the high; "open" if not recovered inside the window). Depth in $k of the 11-book total. Carriers = the books / sessions (core 6 books; X1-X5 are shadow zero) with the largest loss summed over the weeks AFTER the peak up to and including the trough week. Windows restart the cumulative sum at the window start. Frames: lock none = per-book locks only (headline); 12R = + combined stack lock. Use the trough week to look up an agent's "carrying week".

## LOCK NONE (per-book locks only)

- **F9** (38 wk, total equity change +856k):   
    1. 202627 -> 202634 -> 202639: depth 132.6k over 7 wk; books P7 -86k, K7 -30k, A6 -11k; sessions asia -75k, london -30k, nypm -22k  
    2. 202611 -> 202613 -> 202614: depth 62.6k over 2 wk; books K7 -28k, U7 -26k, M7 -9k; sessions asia -42k, london -15k, nyam -4k  
    3. start -> 202607 -> 202609: depth 46.4k over 1 wk; books P7 -35k, H7 -9k, K7 -6k; sessions nyam -18k, asia -15k, london -11k

- **L3M** (13 wk, total equity change +210k):   
    1. start -> 202634 -> 202638: depth 49.9k over 3 wk; books H7 -21k, K7 -13k, M7 -13k; sessions london -24k, asia -20k, nyam -4k  
    2. 202640 -> 202641 -> 202642: depth 36.6k over 1 wk; books P7 -19k, K7 -8k, A6 -7k; sessions asia -26k, nyam -5k, nypm -4k  
    3. 202643 -> 202644 -> open: depth 33.4k over 1 wk; books P7 -22k, H7 -16k, K7 -11k; sessions asia -44k, nypm -4k, pre +0k

- **L6M** (27 wk, total equity change +725k):   
    1. 202627 -> 202634 -> 202639: depth 132.6k over 7 wk; books P7 -86k, K7 -30k, A6 -11k; sessions asia -75k, london -30k, nypm -22k  
    2. 202640 -> 202641 -> 202642: depth 36.6k over 1 wk; books P7 -19k, K7 -8k, A6 -7k; sessions asia -26k, nyam -5k, nypm -4k  
    3. 202643 -> 202644 -> open: depth 33.4k over 1 wk; books P7 -22k, H7 -16k, K7 -11k; sessions asia -44k, nypm -4k, pre +0k

- **HOLD** (52 wk, total equity change +1242k):   
    1. 202627 -> 202634 -> 202639: depth 132.6k over 7 wk; books P7 -86k, K7 -30k, A6 -11k; sessions asia -75k, london -30k, nypm -22k  
    2. 202605 -> 202607 -> 202616: depth 122.9k over 2 wk; books P7 -115k, M7 -12k, K7 -5k; sessions asia -65k, london -28k, nyam -25k  
    3. 202547 -> 202549 -> 202601: depth 95.3k over 2 wk; books P7 -80k, M7 -12k, U7 -10k; sessions london -64k, nyam -17k, asia -11k

- **MID** (12 wk, total equity change +131k):   
    1. 202611 -> 202613 -> 202614: depth 62.6k over 2 wk; books K7 -28k, U7 -26k, M7 -9k; sessions asia -42k, london -15k, nyam -4k  
    2. start -> 202607 -> 202609: depth 46.4k over 1 wk; books P7 -35k, H7 -9k, K7 -6k; sessions nyam -18k, asia -15k, london -11k  
    3. 202614 -> 202615 -> 202616: depth 16.8k over 1 wk; books P7 -30k, H7 -7k, A6 -2k; sessions asia -13k, nypm -4k, london -2k

- **PRE** (75 wk, total equity change +748k):   
    1. 202505 -> 202516 -> 202521: depth 178.4k over 11 wk; books M7 -61k, P7 -54k, H7 -35k; sessions london -220k, nyam -16k, pre +0k  
    2. 202434 -> 202445 -> 202452: depth 161.1k over 11 wk; books P7 -140k, H7 -27k, U7 -19k; sessions london -122k, nyam -19k, nypm -16k  
    3. 202410 -> 202415 -> 202421: depth 116.2k over 5 wk; books P7 -89k, M7 -19k, H7 -18k; sessions nyam -55k, london -43k, asia -10k

- **X'** (44 wk, total equity change -54k):   
    1. start -> 202337 -> open: depth 134.8k over 24 wk; books P7 -156k, H7 -6k, A6 +3k; sessions asia -121k, london -51k, pre +0k

## 12R combined lock

- **F9** (38 wk, total equity change +668k):   
    1. 202609 -> 202613 -> 202614: depth 78.5k over 4 wk; books K7 -41k, U7 -27k, P7 -16k; sessions asia -62k, nypm -7k, london -6k  
    2. 202627 -> 202637 -> 202638: depth 73.9k over 10 wk; books P7 -40k, M7 -24k, H7 -15k; sessions london -37k, asia -18k, nypm -10k  
    3. 202619 -> 202621 -> 202623: depth 49.4k over 2 wk; books P7 -39k, A6 -9k, U7 -5k; sessions asia -43k, london -4k, nypm -2k

- **L3M** (13 wk, total equity change +205k):   
    1. 202633 -> 202637 -> 202638: depth 39.9k over 4 wk; books M7 -17k, H7 -17k, P7 -10k; sessions london -54k, nyam -10k, nypm -4k  
    2. 202639 -> 202641 -> 202642: depth 23.5k over 2 wk; books P7 -14k, H7 -9k, A6 -2k; sessions asia -24k, london +0k, pre +0k  
    3. start -> 202632 -> 202633: depth 17.6k over 1 wk; books P7 -11k, H7 -4k, M7 -3k; sessions london -9k, asia -9k, nyam -1k

- **L6M** (27 wk, total equity change +605k):   
    1. 202627 -> 202637 -> 202638: depth 73.9k over 10 wk; books P7 -40k, M7 -24k, H7 -15k; sessions london -37k, asia -18k, nypm -10k  
    2. 202619 -> 202621 -> 202623: depth 49.4k over 2 wk; books P7 -39k, A6 -9k, U7 -5k; sessions asia -43k, london -4k, nypm -2k  
    3. 202639 -> 202641 -> 202642: depth 23.5k over 2 wk; books P7 -14k, H7 -9k, A6 -2k; sessions asia -24k, london +0k, pre +0k

- **HOLD** (52 wk, total equity change +1033k):   
    1. 202603 -> 202613 -> 202617: depth 119.2k over 10 wk; books P7 -63k, K7 -43k, A6 -12k; sessions asia -48k, nyam -41k, london -27k  
    2. 202627 -> 202637 -> 202638: depth 73.9k over 10 wk; books P7 -40k, M7 -24k, H7 -15k; sessions london -37k, asia -18k, nypm -10k  
    3. 202547 -> 202550 -> 202601: depth 61.3k over 3 wk; books P7 -60k, K7 -4k, M7 -3k; sessions asia -38k, london -20k, nypm -4k

- **MID** (12 wk, total equity change +64k):   
    1. 202609 -> 202613 -> 202614: depth 78.5k over 4 wk; books K7 -41k, U7 -27k, P7 -16k; sessions asia -62k, nypm -7k, london -6k  
    2. start -> 202608 -> 202609: depth 39.1k over 2 wk; books P7 -43k, A6 -5k, K7 -2k; sessions nyam -38k, london -28k, pre +0k  
    3. 202614 -> 202615 -> 202616: depth 17.6k over 1 wk; books P7 -30k, H7 -7k, A6 +0k; sessions asia -9k, london -7k, nypm -3k

- **PRE** (75 wk, total equity change +297k):   
    1. 202434 -> 202516 -> 202522: depth 252.4k over 34 wk; books P7 -168k, U7 -32k, K7 -25k; sessions london -151k, asia -41k, nyam -40k  
    2. 202405 -> 202409 -> 202410: depth 59.9k over 4 wk; books P7 -20k, U7 -17k, A6 -9k; sessions london -34k, asia -13k, nyam -13k  
    3. 202424 -> 202428 -> 202432: depth 59.5k over 4 wk; books P7 -44k, M7 -10k, A6 -3k; sessions asia -30k, london -28k, nyam -2k

- **X'** (44 wk, total equity change -174k):   
    1. start -> 202405 -> open: depth 173.7k over 44 wk; books P7 -162k, M7 -25k, H7 -16k; sessions london -147k, asia -59k, pre +0k

SUPERSEDED 2026-11-02 (BASE-4): the episodes of the V13Y base (add-fill ordering fixed) are in DS3_ZONES_EPISODES_V13Y.md; this file is the V13X (defect) base.
