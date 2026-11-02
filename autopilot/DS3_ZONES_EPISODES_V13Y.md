# DS3 ZONES EPISODES - drawdown episodes of the D7 base (V13Y: v1.3 EXACT + add-fill ordering fix, shipped layer), BASE-4

For each window and frame the top-3 episodes of the weekly-cumulative equity (ISO weeks, label-day weeks). Episode = peak week (last week at the old high) -> trough week -> recovery week (first week back at the high; "open" if not recovered inside the window). Depth in $k of the 11-book total. Carriers = the books / sessions (core 6 books; X1-X5 are shadow zero) with the largest loss summed over the weeks AFTER the peak up to and including the trough week. Windows restart the cumulative sum at the window start. Frames: lock none = per-book locks only (headline); 12R = + combined stack lock. Use the trough week to look up an agent's "carrying week".

## LOCK NONE (per-book locks only)

- **F9** (38 wk, total equity change +973k):   
    1. 202627 -> 202632 -> 202638: depth 96.2k over 5 wk; books P7 -104k, K7 -21k, A6 -14k; sessions asia -63k, london -27k, nypm -18k  
    2. 202620 -> 202621 -> 202623: depth 32.9k over 1 wk; books A6 -10k, M7 -10k, P7 -8k; sessions asia -26k, nyam -8k, nypm -5k  
    3. 202611 -> 202613 -> 202614: depth 30.2k over 2 wk; books K7 -27k, U7 -18k, M7 -8k; sessions asia -14k, london -11k, nyam -4k

- **L3M** (13 wk, total equity change +256k):   
    1. start -> 202632 -> 202638: depth 31.1k over 1 wk; books P7 -20k, A6 -9k, H7 -3k; sessions asia -29k, london -14k, pre +0k  
    2. 202640 -> 202641 -> 202642: depth 27.3k over 1 wk; books H7 -14k, K7 -8k, A6 -7k; sessions asia -16k, nyam -6k, nypm -4k  
    3. 202643 -> 202644 -> open: depth 13.8k over 1 wk; books H7 -16k, K7 -10k, A6 -8k; sessions asia -44k, nypm -4k, pre +0k

- **L6M** (27 wk, total equity change +776k):   
    1. 202627 -> 202632 -> 202638: depth 96.2k over 5 wk; books P7 -104k, K7 -21k, A6 -14k; sessions asia -63k, london -27k, nypm -18k  
    2. 202620 -> 202621 -> 202623: depth 32.9k over 1 wk; books A6 -10k, M7 -10k, P7 -8k; sessions asia -26k, nyam -8k, nypm -5k  
    3. 202640 -> 202641 -> 202642: depth 27.3k over 1 wk; books H7 -14k, K7 -8k, A6 -7k; sessions asia -16k, nyam -6k, nypm -4k

- **HOLD** (52 wk, total equity change +1278k):   
    1. 202605 -> 202607 -> 202614: depth 103.0k over 2 wk; books P7 -98k, M7 -10k, K7 -6k; sessions asia -47k, london -45k, nyam -7k  
    2. 202627 -> 202632 -> 202638: depth 96.2k over 5 wk; books P7 -104k, K7 -21k, A6 -14k; sessions asia -63k, london -27k, nypm -18k  
    3. 202547 -> 202549 -> 202601: depth 72.5k over 2 wk; books P7 -64k, K7 -11k, M7 -11k; sessions london -61k, nyam -17k, nypm -4k

- **MID** (12 wk, total equity change +197k):   
    1. 202611 -> 202613 -> 202614: depth 30.2k over 2 wk; books K7 -27k, U7 -18k, M7 -8k; sessions asia -14k, london -11k, nyam -4k  
    2. start -> 202607 -> 202609: depth 29.3k over 1 wk; books P7 -22k, H7 -9k, K7 -6k; sessions london -17k, nyam -13k, nypm -3k  
    3. 202614 -> 202615 -> 202616: depth 18.0k over 1 wk; books P7 -30k, H7 -7k, A6 -2k; sessions asia -13k, nypm -4k, london -3k

- **PRE** (75 wk, total equity change +908k):   
    1. 202434 -> 202440 -> 202451: depth 129.7k over 6 wk; books P7 -84k, K7 -33k, H7 -18k; sessions london -82k, nyam -21k, nypm -16k  
    2. 202505 -> 202509 -> 202520: depth 124.1k over 4 wk; books P7 -84k, M7 -20k, K7 -16k; sessions london -82k, nyam -34k, nypm -8k  
    3. 202410 -> 202415 -> 202421: depth 116.1k over 5 wk; books P7 -89k, M7 -19k, H7 -8k; sessions nyam -54k, london -43k, asia -11k

- **X'** (44 wk, total equity change +72k):   
    1. 202321 -> 202333 -> 202341: depth 69.7k over 12 wk; books P7 -80k, A6 -2k, M7 -2k; sessions nyam -76k, asia -18k, pre +0k  
    2. start -> 202314 -> 202316: depth 46.1k over 1 wk; books P7 -31k, K7 -9k, U7 -4k; sessions london -29k, nyam -19k, nypm -3k  
    3. 202348 -> 202351 -> open: depth 40.8k over 3 wk; books P7 -68k, K7 -6k, H7 -5k; sessions nyam -35k, asia -7k, nypm -3k

## 12R combined lock

- **F9** (38 wk, total equity change +653k):   
    1. 202627 -> 202635 -> 202638: depth 52.8k over 8 wk; books P7 -26k, M7 -17k, K7 -11k; sessions london -24k, asia -19k, nypm -13k  
    2. 202609 -> 202613 -> 202614: depth 52.3k over 4 wk; books K7 -40k, U7 -17k, M7 -5k; sessions asia -40k, nyam -7k, nypm -5k  
    3. 202619 -> 202621 -> 202623: depth 52.2k over 2 wk; books P7 -39k, A6 -9k, U7 -5k; sessions asia -43k, london -4k, nyam -3k

- **L3M** (13 wk, total equity change +179k):   
    1. start -> 202635 -> 202638: depth 26.5k over 4 wk; books H7 -20k, M7 -16k, K7 -9k; sessions london -29k, nyam -5k, nypm -3k  
    2. 202640 -> 202642 -> 202643: depth 22.2k over 2 wk; books H7 -8k, P7 -7k, M7 -5k; sessions london -24k, nyam -2k, nypm -2k  
    3. 202643 -> 202644 -> open: depth 13.8k over 1 wk; books H7 -16k, K7 -10k, A6 -8k; sessions asia -44k, nypm -4k, pre +0k

- **L6M** (27 wk, total equity change +573k):   
    1. 202627 -> 202635 -> 202638: depth 52.8k over 8 wk; books P7 -26k, M7 -17k, K7 -11k; sessions london -24k, asia -19k, nypm -13k  
    2. 202619 -> 202621 -> 202623: depth 52.2k over 2 wk; books P7 -39k, A6 -9k, U7 -5k; sessions asia -43k, london -4k, nyam -3k  
    3. 202640 -> 202642 -> 202643: depth 22.2k over 2 wk; books H7 -8k, P7 -7k, M7 -5k; sessions london -24k, nyam -2k, nypm -2k

- **HOLD** (52 wk, total equity change +853k):   
    1. 202603 -> 202608 -> 202614: depth 90.4k over 5 wk; books P7 -93k, A6 -10k, K7 -7k; sessions nyam -49k, london -48k, pre +0k  
    2. 202547 -> 202550 -> 202601: depth 64.0k over 3 wk; books P7 -60k, K7 -4k, M7 -4k; sessions asia -40k, london -20k, nypm -4k  
    3. 202627 -> 202635 -> 202638: depth 52.8k over 8 wk; books P7 -26k, M7 -17k, K7 -11k; sessions london -24k, asia -19k, nypm -13k

- **MID** (12 wk, total equity change +80k):   
    1. 202609 -> 202613 -> 202614: depth 52.3k over 4 wk; books K7 -40k, U7 -17k, M7 -5k; sessions asia -40k, nyam -7k, nypm -5k  
    2. start -> 202608 -> 202609: depth 39.2k over 2 wk; books P7 -43k, A6 -5k, K7 -2k; sessions nyam -38k, london -28k, pre +0k  
    3. 202616 -> 202617 -> 202618: depth 22.0k over 1 wk; books K7 -13k, H7 -7k, M7 -3k; sessions london -30k, nyam -5k, nypm -2k

- **PRE** (75 wk, total equity change +441k):   
    1. 202434 -> 202516 -> 202522: depth 282.2k over 34 wk; books P7 -209k, U7 -48k, K7 -30k; sessions london -205k, nyam -52k, asia -13k  
    2. start -> 202409 -> 202410: depth 77.0k over 5 wk; books P7 -33k, U7 -17k, A6 -9k; sessions london -41k, asia -19k, nyam -17k  
    3. 202424 -> 202428 -> 202430: depth 59.8k over 4 wk; books P7 -44k, M7 -10k, A6 -3k; sessions asia -30k, london -28k, nyam -3k

- **X'** (44 wk, total equity change -49k):   
    1. start -> 202323 -> open: depth 131.5k over 10 wk; books P7 -121k, M7 -15k, H7 -8k; sessions nyam -65k, london -51k, asia -14k
