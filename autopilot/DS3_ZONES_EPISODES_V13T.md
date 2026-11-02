# DS3 ZONES EPISODES - drawdown episodes of the D7 base (V13T: v1.3 EXACT with the ordering defect, shipped layer), BASE-4

For each window and frame the top-3 episodes of the weekly-cumulative equity (ISO weeks, label-day weeks). Episode = peak week (last week at the old high) -> trough week -> recovery week (first week back at the high; "open" if not recovered inside the window). Depth in $k of the 11-book total. Carriers = the books / sessions (core 6 books; X1-X5 are shadow zero) with the largest loss summed over the weeks AFTER the peak up to and including the trough week. Windows restart the cumulative sum at the window start. Frames: lock none = per-book locks only (headline); 12R = + combined stack lock. Use the trough week to look up an agent's "carrying week".

## LOCK NONE (per-book locks only)

- **F9** (38 wk, total equity change +1280k):   
    1. 202628 -> 202637 -> 202639: depth 150.7k over 9 wk; books P7 -76k, K7 -64k, M7 -35k; sessions london -89k, asia -32k, nyam -17k  
    2. 202643 -> 202644 -> open: depth 94.0k over 1 wk; books P7 -33k, H7 -20k, U7 -17k; sessions asia -71k, london -23k, nypm -5k  
    3. start -> 202608 -> 202609: depth 43.7k over 2 wk; books P7 -51k, H7 -10k, A6 -2k; sessions nyam -19k, asia -16k, london -13k

- **L3M** (13 wk, total equity change +192k):   
    1. 202643 -> 202644 -> open: depth 94.0k over 1 wk; books P7 -33k, H7 -20k, U7 -17k; sessions asia -71k, london -23k, nypm -5k  
    2. start -> 202637 -> 202638: depth 75.0k over 6 wk; books K7 -37k, M7 -31k, H7 -12k; sessions london -62k, asia -7k, nyam -4k  
    3. 202640 -> 202641 -> 202642: depth 32.7k over 1 wk; books H7 -17k, P7 -12k, K7 -9k; sessions asia -58k, nyam -5k, nypm -2k

- **L6M** (27 wk, total equity change +992k):   
    1. 202628 -> 202637 -> 202639: depth 150.7k over 9 wk; books P7 -76k, K7 -64k, M7 -35k; sessions london -89k, asia -32k, nyam -17k  
    2. 202643 -> 202644 -> open: depth 94.0k over 1 wk; books P7 -33k, H7 -20k, U7 -17k; sessions asia -71k, london -23k, nypm -5k  
    3. 202640 -> 202641 -> 202642: depth 32.7k over 1 wk; books H7 -17k, P7 -12k, K7 -9k; sessions asia -58k, nyam -5k, nypm -2k

- **HOLD** (52 wk, total equity change +1581k):   
    1. 202628 -> 202637 -> 202639: depth 150.7k over 9 wk; books P7 -76k, K7 -64k, M7 -35k; sessions london -89k, asia -32k, nyam -17k  
    2. 202605 -> 202608 -> 202611: depth 129.3k over 3 wk; books P7 -142k, A6 -10k, M7 +0k; sessions london -54k, asia -53k, nyam -23k  
    3. 202643 -> 202644 -> open: depth 94.0k over 1 wk; books P7 -33k, H7 -20k, U7 -17k; sessions asia -71k, london -23k, nypm -5k

- **MID** (12 wk, total equity change +288k):   
    1. start -> 202608 -> 202609: depth 43.7k over 2 wk; books P7 -51k, H7 -10k, A6 -2k; sessions nyam -19k, asia -16k, london -13k  
    2. 202612 -> 202613 -> 202614: depth 25.8k over 1 wk; books K7 -18k, U7 -10k, A6 -7k; sessions asia -35k, nypm -3k, nyam -0k  
    3. 202614 -> 202615 -> 202616: depth 10.2k over 1 wk; books P7 -19k, A6 -2k, H7 -2k; sessions london -9k, nypm -3k, nyam -2k

- **PRE** (75 wk, total equity change +1296k):   
    1. 202434 -> 202437 -> 202448: depth 166.2k over 3 wk; books P7 -97k, K7 -33k, H7 -30k; sessions london -73k, nyam -56k, asia -31k  
    2. 202505 -> 202509 -> 202519: depth 164.6k over 4 wk; books P7 -110k, M7 -32k, K7 -18k; sessions london -134k, nyam -29k, nypm -8k  
    3. 202412 -> 202415 -> 202422: depth 86.1k over 3 wk; books P7 -79k, M7 -17k, H7 -4k; sessions nyam -47k, asia -31k, london -6k

- **X'** (44 wk, total equity change +211k):   
    1. 202341 -> 202347 -> 202404: depth 92.5k over 6 wk; books P7 -84k, M7 -21k, H7 -3k; sessions nyam -56k, asia -36k, nypm -1k  
    2. 202332 -> 202336 -> 202339: depth 66.2k over 4 wk; books H7 -35k, P7 -24k, K7 -17k; sessions asia -103k, london -15k, nypm -1k  
    3. start -> 202314 -> 202317: depth 46.3k over 1 wk; books P7 -31k, K7 -9k, U7 -4k; sessions london -29k, nyam -19k, nypm -3k

## 12R combined lock

- **F9** (38 wk, total equity change +1033k):   
    1. 202627 -> 202637 -> 202639: depth 151.0k over 10 wk; books P7 -54k, K7 -32k, H7 -28k; sessions london -68k, asia -67k, nyam -9k  
    2. 202619 -> 202621 -> 202623: depth 55.8k over 2 wk; books P7 -36k, U7 -11k, A6 -8k; sessions asia -46k, london -4k, nyam -4k  
    3. 202612 -> 202613 -> 202614: depth 44.2k over 1 wk; books U7 -16k, K7 -15k, A6 -6k; sessions asia -22k, london -19k, nypm -3k

- **L3M** (13 wk, total equity change +198k):   
    1. start -> 202637 -> 202638: depth 62.8k over 6 wk; books H7 -31k, K7 -18k, M7 -16k; sessions london -45k, asia -13k, nyam -4k  
    2. 202643 -> 202644 -> open: depth 26.1k over 1 wk; books P7 -8k, H7 -7k, A6 -4k; sessions asia -13k, london -12k, nyam -2k  
    3. 202639 -> 202641 -> 202642: depth 23.4k over 2 wk; books P7 -13k, H7 -8k, A6 -2k; sessions asia -23k, london +0k, pre +0k

- **L6M** (27 wk, total equity change +800k):   
    1. 202627 -> 202637 -> 202639: depth 151.0k over 10 wk; books P7 -54k, K7 -32k, H7 -28k; sessions london -68k, asia -67k, nyam -9k  
    2. 202619 -> 202621 -> 202623: depth 55.8k over 2 wk; books P7 -36k, U7 -11k, A6 -8k; sessions asia -46k, london -4k, nyam -4k  
    3. 202643 -> 202644 -> open: depth 26.1k over 1 wk; books P7 -8k, H7 -7k, A6 -4k; sessions asia -13k, london -12k, nyam -2k

- **HOLD** (52 wk, total equity change +1295k):   
    1. 202627 -> 202637 -> 202639: depth 151.0k over 10 wk; books P7 -54k, K7 -32k, H7 -28k; sessions london -68k, asia -67k, nyam -9k  
    2. 202603 -> 202608 -> 202610: depth 71.9k over 5 wk; books P7 -72k, A6 -5k, K7 -3k; sessions asia -36k, nyam -22k, london -13k  
    3. 202547 -> 202550 -> 202601: depth 57.9k over 3 wk; books P7 -61k, U7 -2k, A6 -0k; sessions asia -37k, nyam -9k, london -8k

- **MID** (12 wk, total equity change +233k):   
    1. 202612 -> 202613 -> 202614: depth 44.2k over 1 wk; books U7 -16k, K7 -15k, A6 -6k; sessions asia -22k, london -19k, nypm -3k  
    2. start -> 202608 -> 202609: depth 28.8k over 2 wk; books P7 -24k, H7 -14k, A6 -0k; sessions asia -22k, nyam -5k, london -2k  
    3. 202616 -> 202617 -> 202618: depth 22.1k over 1 wk; books H7 -9k, K7 -8k, U7 -7k; sessions asia -12k, london -10k, pre +0k

- **PRE** (75 wk, total equity change +712k):   
    1. 202432 -> 202440 -> 202450: depth 133.6k over 8 wk; books P7 -85k, H7 -23k, U7 -14k; sessions nyam -59k, london -35k, asia -34k  
    2. 202451 -> 202516 -> 202520: depth 117.0k over 17 wk; books M7 -52k, P7 -43k, U7 -15k; sessions london -178k, nypm -4k, pre +0k  
    3. 202412 -> 202428 -> 202430: depth 100.4k over 16 wk; books P7 -52k, U7 -50k, M7 -28k; sessions london -108k, asia -43k, pre +0k

- **X'** (44 wk, total equity change -197k):   
    1. start -> 202351 -> open: depth 229.4k over 38 wk; books P7 -187k, M7 -47k, K7 -20k; sessions london -165k, nyam -60k, asia -13k
