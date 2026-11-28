# DESK_DESIGNS_COMPARED (generated 2026-11-28 15:17Z by code/th_algo/ar_designs.py; order 1408Z; research only)

One table of manager designs, same windows, same like-with-like references. Window per session = the months the DK22 sets have (Asia / London 37 months 2023-09..2026-10, NY AM / NY PM 24 months 2024-10..2026-10, Nov 2025 out); every design is cut to those months and the reference (the live mix as run for the mix rows, the book on its fixed bracket for alone rows) is cut to the same months and weeks. SESSION MIX row = live mix + sum of the per-book deltas of the books that design has finished (post-hoc additive, interaction neglected); books a design has not finished for the whole window are listed as not complete and left out. Floors: ACCEPTABLE = smoother (worst week not worse AND weekly st.dev. not larger) in >= 2/3 of quarters overall AND in NQ-up AND in NQ-down weeks, and income not more than 10 / 20 / 30% below the bracket; shown as YES / no (smooth = smoothness passed, income failed) / no. Give-backs: peak open profit from best_px in the trade rows (tape where the column is absent, marked), $ minus realised p484; largest single trade and the count of trades that gave back more than half of a peak of at least $500; managed = the managed books' own trades, bracket = the same books on the fixed bracket (fix_A, tape). Designs are read from code/th_algo/desk_designs.json (first tag with rows wins) and rows appear as the sets finish; the best single landscape code per book is the _M set named in autopilot/SUNDAY_LANDSCAPE.md.

DK4..DK9 set families found in runs_rf: DK4MAIN, DK4REF, DK5, DK6, DK7, DK8, DK9; NOT in desk_designs.json (add them): 

DESIGNS DONE (books with every window month DONE, per session): v0.2.2 Asia 3/3 books; v0.3 Asia 3/3 books; v0.4 ratchet-only Asia 3/3 books; v0.4-ceiling Asia 3/3 books; v0.5 bank half, run half Asia 3/3 books; v0.6 ratchet + ABORT Asia 3/3 books; v0.7 bracket + near-target guard Asia 3/3 books; v0.8 Asia 1/3 books; v0.9 Asia 1/3 books; v0.10 Asia 1/3 books; v0.11 Asia 0/3 books; v0.12 Asia 0/3 books; v0.13 Asia 0/3 books; v0.14 Asia 0/3 books; v0.15 Asia 0/3 books; A1 volatility stop at entry Asia 0/3 books; A2 structure stop at entry Asia 0/3 books; A3 chandelier trail Asia 0/3 books; A4 EMA21 trail once up 1 unit Asia 0/3 books; A5 parabolic-SAR trail Asia 0/3 books; B1 R-multiple ladder Asia 0/3 books; B2 exhaustion take Asia 0/3 books; B3 VWAP-band take Asia 0/3 books; C1 halve-and-hold Asia 0/3 books; C2 adverse-speed cut Asia 0/3 books; D1 pyramid into a winner Asia 0/3 books; D2 scale-in entry Asia 0/3 books; E1 continuation re-entry after a ratchet stop-out in profit Asia 0/3 books; E2 no same-direction re-entry 15 min after a full stop Asia 0/3 books; F1 calendar-aware Asia 0/3 books; F2 volatility regime Asia 0/3 books; F3 day-of-week / opex / month-end Asia 0/3 books; G1 DAY PROFIT RATCHET Asia 0/3 books; G2 same-direction crowd Asia 0/3 books; G3 opposite books may not add Asia 0/3 books; G4 loss-streak brake Asia 0/3 books; v0.16 Asia 0/3 books; v0.17 Asia 0/3 books; v0.18 Asia 0/3 books; v0.2.2 NY AM 4/4 books; v0.3 NY AM 4/4 books; v0.4 ratchet-only NY AM 4/4 books; v0.4-ceiling NY AM 4/4 books; v0.5 bank half, run half NY AM 4/4 books; v0.6 ratchet + ABORT NY AM 4/4 books; v0.7 bracket + near-target guard NY AM 4/4 books; v0.8 NY AM 0/4 books; v0.9 NY AM 0/4 books; v0.10 NY AM 0/4 books; v0.11 NY AM 0/4 books; v0.12 NY AM 0/4 books; v0.13 NY AM 0/4 books; v0.14 NY AM 0/4 books; v0.15 NY AM 0/4 books; A1 volatility stop at entry NY AM 0/4 books; A2 structure stop at entry NY AM 0/4 books; A3 chandelier trail NY AM 0/4 books; A4 EMA21 trail once up 1 unit NY AM 0/4 books; A5 parabolic-SAR trail NY AM 0/4 books; B1 R-multiple ladder NY AM 0/4 books; B2 exhaustion take NY AM 0/4 books; B3 VWAP-band take NY AM 0/4 books; C1 halve-and-hold NY AM 0/4 books; C2 adverse-speed cut NY AM 0/4 books; D1 pyramid into a winner NY AM 0/4 books; D2 scale-in entry NY AM 0/4 books; E1 continuation re-entry after a ratchet stop-out in profit NY AM 0/4 books; E2 no same-direction re-entry 15 min after a full stop NY AM 0/4 books; F1 calendar-aware NY AM 0/4 books; F2 volatility regime NY AM 0/4 books; F3 day-of-week / opex / month-end NY AM 0/4 books; G1 DAY PROFIT RATCHET NY AM 0/4 books; G2 same-direction crowd NY AM 0/4 books; G3 opposite books may not add NY AM 0/4 books; G4 loss-streak brake NY AM 0/4 books; v0.16 NY AM 0/4 books; v0.17 NY AM 0/4 books; v0.18 NY AM 0/4 books; v0.2.2 London 2/2 books; v0.3 London 2/2 books; v0.4 ratchet-only London 2/2 books; v0.4-ceiling London 2/2 books; v0.5 bank half, run half London 2/2 books; v0.6 ratchet + ABORT London 2/2 books; v0.7 bracket + near-target guard London 2/2 books; v0.8 London 0/2 books; v0.9 London 0/2 books; v0.10 London 0/2 books; v0.11 London 0/2 books; v0.12 London 0/2 books; v0.13 London 0/2 books; v0.14 London 0/2 books; v0.15 London 0/2 books; A1 volatility stop at entry London 0/2 books; A2 structure stop at entry London 0/2 books; A3 chandelier trail London 0/2 books; A4 EMA21 trail once up 1 unit London 0/2 books; A5 parabolic-SAR trail London 0/2 books; B1 R-multiple ladder London 0/2 books; B2 exhaustion take London 0/2 books; B3 VWAP-band take London 0/2 books; C1 halve-and-hold London 0/2 books; C2 adverse-speed cut London 0/2 books; D1 pyramid into a winner London 0/2 books; D2 scale-in entry London 0/2 books; E1 continuation re-entry after a ratchet stop-out in profit London 0/2 books; E2 no same-direction re-entry 15 min after a full stop London 0/2 books; F1 calendar-aware London 0/2 books; F2 volatility regime London 0/2 books; F3 day-of-week / opex / month-end London 0/2 books; G1 DAY PROFIT RATCHET London 0/2 books; G2 same-direction crowd London 0/2 books; G3 opposite books may not add London 0/2 books; G4 loss-streak brake London 0/2 books; v0.16 London 0/2 books; v0.17 London 0/2 books; v0.18 London 0/2 books; v0.2.2 NY PM 2/2 books; v0.3 NY PM 2/2 books; v0.4 ratchet-only NY PM 2/2 books; v0.4-ceiling NY PM 2/2 books; v0.5 bank half, run half NY PM 2/2 books; v0.6 ratchet + ABORT NY PM 2/2 books; v0.7 bracket + near-target guard NY PM 2/2 books; v0.8 NY PM 0/2 books; v0.9 NY PM 0/2 books; v0.10 NY PM 0/2 books; v0.11 NY PM 0/2 books; v0.12 NY PM 0/2 books; v0.13 NY PM 0/2 books; v0.14 NY PM 0/2 books; v0.15 NY PM 0/2 books; A1 volatility stop at entry NY PM 0/2 books; A2 structure stop at entry NY PM 0/2 books; A3 chandelier trail NY PM 0/2 books; A4 EMA21 trail once up 1 unit NY PM 0/2 books; A5 parabolic-SAR trail NY PM 0/2 books; B1 R-multiple ladder NY PM 0/2 books; B2 exhaustion take NY PM 0/2 books; B3 VWAP-band take NY PM 0/2 books; C1 halve-and-hold NY PM 0/2 books; C2 adverse-speed cut NY PM 0/2 books; D1 pyramid into a winner NY PM 0/2 books; D2 scale-in entry NY PM 0/2 books; E1 continuation re-entry after a ratchet stop-out in profit NY PM 0/2 books; E2 no same-direction re-entry 15 min after a full stop NY PM 0/2 books; F1 calendar-aware NY PM 0/2 books; F2 volatility regime NY PM 0/2 books; F3 day-of-week / opex / month-end NY PM 0/2 books; G1 DAY PROFIT RATCHET NY PM 0/2 books; G2 same-direction crowd NY PM 0/2 books; G3 opposite books may not add NY PM 0/2 books; G4 loss-streak brake NY PM 0/2 books; v0.16 NY PM 0/2 books; v0.17 NY PM 0/2 books; v0.18 NY PM 0/2 books

# Asia: window 202309-202610 (37 months)

## Asia: SESSION MIX

| design | books in the mix / not complete | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1, MF2, MF3 | -233,607 (-126%) | -308,325 / -67,941 | -44,293 / -37,409 | 10,045 / 18,895 | 35,774 / 15,529 | 1649 / 2345 | 11/14, 8/11, 6/12 | no / no / no |
| v0.3 (DK3 main) | MF1, MF2, MF3 | 399,861 (-55%) | -120,551 / -67,941 | -35,127 / -37,409 | 13,100 / 18,895 | 14,099 / 15,529 | 1976 / 2345 | 11/14, 9/11, 6/12 | no / no / no |
| v0.4 ratchet-only | MF1, MF2, MF3 | 394,913 (-56%) | -140,182 / -67,941 | -48,560 / -37,409 | 14,702 / 18,895 | 33,439 / 15,529 | 2337 / 2345 | 9/14, 8/11, 5/12 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF1, MF2, MF3 | 373,637 (-58%) | -160,074 / -67,941 | -39,958 / -37,409 | 13,112 / 18,895 | 13,269 / 15,529 | 2235 / 2345 | 10/14, 8/11, 6/12 | no / no / no |
| v0.5 bank half, run half | MF1, MF2, MF3 | 394,310 (-56%) | -147,721 / -67,941 | -46,360 / -37,409 | 13,947 / 18,895 | 33,439 / 15,529 | 2223 / 2345 | 9/14, 8/11, 6/12 | no / no / no |
| v0.6 ratchet + ABORT | MF1, MF2, MF3 | 388,183 (-57%) | -139,402 / -67,941 | -48,560 / -37,409 | 14,706 / 18,895 | 33,439 / 15,529 | 2337 / 2345 | 9/14, 8/11, 4/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF1, MF2, MF3 | 544,555 (-39%) | -100,130 / -67,941 | -40,563 / -37,409 | 14,742 / 18,895 | 13,269 / 15,529 | 2106 / 2345 | 9/14, 6/11, 6/12 | no / no / no |
| v0.8 (scale out in thirds) | none complete (MF2 not complete) | not run yet |||||||| 
| v0.9 (volatility-sized give-back) | none complete (MF2 not complete) | not run yet |||||||| 
| v0.10 (level-anchored stop) | none complete (MF2 not complete) | not run yet |||||||| 
| v0.11 (trend day vs range day) | none complete (MF1 not complete) | not run yet |||||||| 
| v0.12 (momentum roll-over) | none complete (MF1 not complete) | not run yet |||||||| 
| v0.13 (tape-led defence (Asia, London only)) | none complete (MF1 not complete) | not run yet |||||||| 
| v0.14 (time of session) | none complete (MF1 not complete) | not run yet |||||||| 
| v0.15 (per-book winner profile) | none complete (MF1, MF2 not complete) | not run yet |||||||| 
| A1 volatility stop at entry (2 x s5, same lots-risk, own target; compare in $ and DD, lots differ); post-result change 22 | none complete | not run yet |||||||| 
| A2 structure stop at entry (capped at own stop, own lots); post-result change 23 | none complete | not run yet |||||||| 
| A3 chandelier trail (3 x ATR5, no target); post-result change 24 | none complete | not run yet |||||||| 
| A4 EMA21 trail once up 1 unit (no target); post-result change 25 | none complete | not run yet |||||||| 
| A5 parabolic-SAR trail (no target); post-result change 26 | none complete | not run yet |||||||| 
| B1 R-multiple ladder (thirds at 1R/2R, ratchet runner); post-result change 27 | none complete | not run yet |||||||| 
| B2 exhaustion take (RSI14 80/20 turn, half); post-result change 28 | none complete | not run yet |||||||| 
| B3 VWAP-band take (+/-2 sd, half); post-result change 29 | none complete | not run yet |||||||| 
| C1 halve-and-hold (cut half at -50% of stop); post-result change 30 | none complete | not run yet |||||||| 
| C2 adverse-speed cut (1 unit in 60 s); post-result change 31 | none complete | not run yet |||||||| 
| D1 pyramid into a winner (+1R add half once, stop to entry, ratchet) | none complete | not run yet |||||||| 
| D2 scale-in entry (half first, add half if up 0.5 unit in median time) | none complete | not run yet |||||||| 
| E1 continuation re-entry after a ratchet stop-out in profit | none complete | not run yet |||||||| 
| E2 no same-direction re-entry 15 min after a full stop | none complete | not run yet |||||||| 
| F1 calendar-aware (ratchet 2 min before top-tier release, no entries -5/+5 min) | none complete | not run yet |||||||| 
| F2 volatility regime (high -> no target + ratchet; low -> bracket) | none complete | not run yet |||||||| 
| F3 day-of-week / opex / month-end (table first, one design only if it shows something) | none complete | not run yet |||||||| 
| G1 DAY PROFIT RATCHET (never give back half the session peak above 1.0x median winning day) | none complete | not run yet |||||||| 
| G2 same-direction crowd (3+ books in profit: bank the oldest, ratchet the rest) | none complete | not run yet |||||||| 
| G3 opposite books may not add | none complete | not run yet |||||||| 
| G4 loss-streak brake (after 3 full stops, half lots) | none complete | not run yet |||||||| 
| v0.16 (the screens set the leash; post-result change 19) | none complete | not run yet |||||||| 
| v0.17 (the screens choose the day; post-result change 20) | none complete | not run yet |||||||| 
| v0.18 (slow divergence at the highs; post-result change 21) | none complete | not run yet |||||||| 
| best single landscape code per book (MF1 tr100, MF2 so0, MF3 x7) | MF1, MF2, MF3 | 912,321 (+2%) | -89,603 / -67,941 | -39,207 / -37,409 | 20,610 / 18,895 | 19,244 / 15,529 | 2116 / 2345 | 5/14, 4/11, 4/12 | no / no / no |

## Asia: PER BOOK

| design | book (row type) | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1 (alone) | -198,618 (-123%) | -222,803 / -111,441 | -31,530 / -50,206 | 8,689 / 20,523 | 16,079 / 14,634 | 473 / 1054 | 11/14, 8/11, 7/12 | no / no / no |
| v0.2.2 (DK22 main) | MF2 (alone) | 74,687 (-82%) | -93,385 / -92,225 | -26,783 / -30,707 | 5,950 / 10,772 | 18,079 / 15,529 | 165 / 280 | 9/14, 7/11, 6/12 | no / no / no |
| v0.2.2 (DK22 main) | MF3 (alone) | -89,438 (-114%) | -239,545 / -103,232 | -41,929 / -39,659 | 11,983 / 16,561 | 35,774 / 12,119 | 1011 / 1011 | 10/14, 7/11, 10/12 | no / no / no |
| v0.3 (DK3 main) | MF1 (alone) | 460,151 (-48%) | -101,818 / -111,441 | -51,433 / -50,206 | 16,042 / 20,523 | 13,839 / 14,634 | 588 / 1054 | 10/14, 7/11, 6/12 | no / no / no |
| v0.3 (DK3 main) | MF2 (alone) | 210,720 (-49%) | -112,632 / -92,225 | -32,864 / -30,707 | 9,433 / 10,772 | 14,099 / 15,529 | 254 / 280 | 9/14, 6/11, 7/12 | no / no / no |
| v0.3 (DK3 main) | MF3 (alone) | 332,919 (-48%) | -115,728 / -103,232 | -37,207 / -39,659 | 15,138 / 16,561 | 10,899 / 12,119 | 1134 / 1011 | 9/14, 6/11, 8/12 | no / no / no |
| v0.4 ratchet-only | MF1 (alone) | 89,234 (-90%) | -97,032 / -111,441 | -33,340 / -50,206 | 11,055 / 20,523 | 16,079 / 14,634 | 734 / 1054 | 11/14, 8/11, 8/12 | no (smooth) / no (smooth) / no (smooth) |
| v0.4 ratchet-only | MF2 (alone) | 237,506 (-42%) | -95,808 / -92,225 | -26,596 / -30,707 | 8,327 / 10,772 | 13,269 / 15,529 | 255 / 280 | 9/14, 7/11, 5/12 | no / no / no |
| v0.4 ratchet-only | MF3 (alone) | 503,631 (-21%) | -113,282 / -103,232 | -55,780 / -39,659 | 17,416 / 16,561 | 33,439 / 12,119 | 1348 / 1011 | 6/14, 2/11, 6/12 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF1 (alone) | 83,415 (-91%) | -106,582 / -111,441 | -33,340 / -50,206 | 11,384 / 20,523 | 8,329 / 14,634 | 727 / 1054 | 11/14, 8/11, 8/12 | no (smooth) / no (smooth) / no (smooth) |
| v0.4-ceiling (own target as ceiling) | MF2 (alone) | 281,152 (-31%) | -83,578 / -92,225 | -26,596 / -30,707 | 8,237 / 10,772 | 13,269 / 15,529 | 224 / 280 | 10/14, 6/11, 7/12 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF3 (alone) | 400,477 (-37%) | -101,338 / -103,232 | -48,974 / -39,659 | 15,376 / 16,561 | 10,474 / 12,119 | 1284 / 1011 | 8/14, 3/11, 7/12 | no / no / no |
| v0.5 bank half, run half | MF1 (alone) | 89,129 (-90%) | -101,012 / -111,441 | -33,340 / -50,206 | 11,142 / 20,523 | 18,394 / 14,634 | 729 / 1054 | 11/14, 8/11, 8/12 | no (smooth) / no (smooth) / no (smooth) |
| v0.5 bank half, run half | MF2 (alone) | 263,941 (-36%) | -86,623 / -92,225 | -26,596 / -30,707 | 8,183 / 10,772 | 18,614 / 15,529 | 231 / 280 | 10/14, 7/11, 6/12 | no / no / no |
| v0.5 bank half, run half | MF3 (alone) | 469,827 (-26%) | -92,707 / -103,232 | -53,735 / -39,659 | 16,596 / 16,561 | 33,439 / 12,119 | 1263 / 1011 | 7/14, 3/11, 7/12 | no / no / no |
| v0.6 ratchet + ABORT | MF1 (alone) | 85,709 (-90%) | -94,717 / -111,441 | -33,340 / -50,206 | 11,042 / 20,523 | 16,079 / 14,634 | 734 / 1054 | 11/14, 8/11, 8/12 | no (smooth) / no (smooth) / no (smooth) |
| v0.6 ratchet + ABORT | MF2 (alone) | 234,166 (-43%) | -95,808 / -92,225 | -26,596 / -30,707 | 8,330 / 10,772 | 13,269 / 15,529 | 255 / 280 | 8/14, 7/11, 5/12 | no / no / no |
| v0.6 ratchet + ABORT | MF3 (alone) | 503,631 (-21%) | -113,282 / -103,232 | -55,780 / -39,659 | 17,416 / 16,561 | 33,439 / 12,119 | 1348 / 1011 | 6/14, 2/11, 6/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF1 (alone) | 340,241 (-61%) | -90,967 / -111,441 | -41,917 / -50,206 | 16,054 / 20,523 | 12,034 / 14,634 | 621 / 1054 | 11/14, 5/11, 8/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF2 (alone) | 236,523 (-42%) | -122,965 / -92,225 | -30,404 / -30,707 | 9,463 / 10,772 | 13,269 / 15,529 | 264 / 280 | 8/14, 5/11, 5/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF3 (alone) | 476,015 (-25%) | -94,930 / -103,232 | -46,561 / -39,659 | 16,421 / 16,561 | 10,474 / 12,119 | 1221 / 1011 | 8/14, 5/11, 7/12 | no / no / no |
| v0.8 (scale out in thirds) | MF1 (alone) | 64,569 (-93%) | -104,602 / -111,441 | -33,130 / -50,206 | 11,006 / 20,523 | 22,369 / 14,634 | 679 / 1054 | 11/14, 8/11, 8/12 | no (smooth) / no (smooth) / no (smooth) |
| v0.9 (volatility-sized give-back) | MF1 (alone) | 81,809 (-91%) | -143,428 / -111,441 | -36,221 / -50,206 | 13,763 / 20,523 | 19,409 / 14,634 | 892 / 1054 | 11/14, 8/11, 8/12 | no (smooth) / no (smooth) / no (smooth) |
| v0.10 (level-anchored stop) | MF1 (alone) | 114,851 (-87%) | -84,769 / -111,441 | -28,319 / -50,206 | 10,881 / 20,523 | 19,409 / 14,634 | 563 / 1054 | 12/14, 8/11, 8/12 | no (smooth) / no (smooth) / no (smooth) |
| best single landscape code per book (MF1 tr100, MF2 so0, MF3 x7) | MF1 (in mix) | 848,019 (-5%) | -79,568 / -67,941 | -39,838 / -37,409 | 18,453 / 18,895 | 9,229 / 14,634 | 990 / 1054 | 6/14, 4/11, 4/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF2 so0, MF3 x7) | MF2 (in mix) | 858,715 (-4%) | -71,310 / -67,941 | -37,409 / -37,409 | 19,562 / 18,895 | 19,244 / 15,529 | 286 / 280 | 6/14, 4/11, 8/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF2 so0, MF3 x7) | MF3 (in mix) | 992,929 (+11%) | -65,426 / -67,941 | -36,778 / -37,409 | 20,533 / 18,895 | 11,440 / 12,119 | 840 / 1011 | 7/14, 4/11, 7/12 | no / no / no |

# NY AM: window 202410-202610 (24 months)

## NY AM: SESSION MIX

| design | books in the mix / not complete | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1, MF2, MF4, MF5 | 1,683,301 (-41%) | -130,615 / -163,622 | -64,328 / -110,130 | 37,994 / 54,746 | 29,234 / 29,179 | 3019 / 2433 | 4/9, 3/7, 4/7 | no / no / no |
| v0.3 (DK3 main) | MF1, MF2, MF4, MF5 | 2,177,072 (-24%) | -166,714 / -163,622 | -88,687 / -110,130 | 44,961 / 54,746 | 27,254 / 29,179 | 3039 / 2433 | 6/9, 2/7, 5/7 | no / no / no |
| v0.4 ratchet-only | MF1, MF2, MF4, MF5 | 1,627,105 (-43%) | -173,260 / -163,622 | -86,466 / -110,130 | 41,983 / 54,746 | 98,349 / 29,179 | 4094 / 2433 | 4/9, 2/7, 3/7 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF1, MF2, MF4, MF5 | 1,943,713 (-32%) | -151,921 / -163,622 | -126,600 / -110,130 | 48,377 / 54,746 | 23,004 / 29,179 | 3205 / 2433 | 3/9, 2/7, 3/7 | no / no / no |
| v0.5 bank half, run half | MF1, MF2, MF4, MF5 | 1,547,570 (-46%) | -185,105 / -163,622 | -88,521 / -110,130 | 41,112 / 54,746 | 139,489 / 29,179 | 3937 / 2433 | 5/9, 2/7, 3/7 | no / no / no |
| v0.6 ratchet + ABORT | MF1, MF2, MF4, MF5 | 1,620,381 (-43%) | -173,260 / -163,622 | -86,466 / -110,130 | 41,929 / 54,746 | 98,349 / 29,179 | 4095 / 2433 | 4/9, 2/7, 3/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF1, MF2, MF4, MF5 | 2,297,634 (-19%) | -354,064 / -163,622 | -112,604 / -110,130 | 52,243 / 54,746 | 26,679 / 29,179 | 2980 / 2433 | 5/9, 4/7, 4/7 | no / no / no |
| v0.8 (scale out in thirds) | none complete | not run yet |||||||| 
| v0.9 (volatility-sized give-back) | none complete | not run yet |||||||| 
| v0.10 (level-anchored stop) | none complete | not run yet |||||||| 
| v0.11 (trend day vs range day) | none complete (MF5 not complete) | not run yet |||||||| 
| v0.12 (momentum roll-over) | none complete | not run yet |||||||| 
| v0.13 (tape-led defence (Asia, London only)) | none complete | not run yet |||||||| 
| v0.14 (time of session) | none complete | not run yet |||||||| 
| v0.15 (per-book winner profile) | none complete | not run yet |||||||| 
| A1 volatility stop at entry (2 x s5, same lots-risk, own target; compare in $ and DD, lots differ); post-result change 22 | none complete | not run yet |||||||| 
| A2 structure stop at entry (capped at own stop, own lots); post-result change 23 | none complete | not run yet |||||||| 
| A3 chandelier trail (3 x ATR5, no target); post-result change 24 | none complete | not run yet |||||||| 
| A4 EMA21 trail once up 1 unit (no target); post-result change 25 | none complete | not run yet |||||||| 
| A5 parabolic-SAR trail (no target); post-result change 26 | none complete | not run yet |||||||| 
| B1 R-multiple ladder (thirds at 1R/2R, ratchet runner); post-result change 27 | none complete | not run yet |||||||| 
| B2 exhaustion take (RSI14 80/20 turn, half); post-result change 28 | none complete | not run yet |||||||| 
| B3 VWAP-band take (+/-2 sd, half); post-result change 29 | none complete | not run yet |||||||| 
| C1 halve-and-hold (cut half at -50% of stop); post-result change 30 | none complete | not run yet |||||||| 
| C2 adverse-speed cut (1 unit in 60 s); post-result change 31 | none complete | not run yet |||||||| 
| D1 pyramid into a winner (+1R add half once, stop to entry, ratchet) | none complete | not run yet |||||||| 
| D2 scale-in entry (half first, add half if up 0.5 unit in median time) | none complete | not run yet |||||||| 
| E1 continuation re-entry after a ratchet stop-out in profit | none complete | not run yet |||||||| 
| E2 no same-direction re-entry 15 min after a full stop | none complete | not run yet |||||||| 
| F1 calendar-aware (ratchet 2 min before top-tier release, no entries -5/+5 min) | none complete | not run yet |||||||| 
| F2 volatility regime (high -> no target + ratchet; low -> bracket) | none complete | not run yet |||||||| 
| F3 day-of-week / opex / month-end (table first, one design only if it shows something) | none complete | not run yet |||||||| 
| G1 DAY PROFIT RATCHET (never give back half the session peak above 1.0x median winning day) | none complete | not run yet |||||||| 
| G2 same-direction crowd (3+ books in profit: bank the oldest, ratchet the rest) | none complete | not run yet |||||||| 
| G3 opposite books may not add | none complete | not run yet |||||||| 
| G4 loss-streak brake (after 3 full stops, half lots) | none complete | not run yet |||||||| 
| v0.16 (the screens set the leash; post-result change 19) | none complete | not run yet |||||||| 
| v0.17 (the screens choose the day; post-result change 20) | none complete | not run yet |||||||| 
| v0.18 (slow divergence at the highs; post-result change 21) | none complete | not run yet |||||||| 
| best single landscape code per book (MF1 g75a30, MF2 tr50, MF4 g67a70, MF5 x7) | MF1, MF2, MF4, MF5 | 2,634,979 (-7%) | -160,142 / -163,622 | -107,874 / -110,130 | 46,092 / 54,746 | 18,624 / 29,179 | 2485 / 2433 | 5/9, 4/7, 4/7 | no / no / no |

## NY AM: PER BOOK

| design | book (row type) | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1 (alone) | 622,071 (-51%) | -113,982 / -158,282 | -46,763 / -81,412 | 26,565 / 38,170 | 26,764 / 29,179 | 779 / 543 | 7/9, 5/7, 5/7 | no (smooth) / no (smooth) / no (smooth) |
| v0.2.2 (DK22 main) | MF2 (alone) | 6,145 (-96%) | -177,004 / -263,422 | -60,375 / -59,825 | 17,091 / 23,724 | 25,944 / 15,369 | 713 / 629 | 6/9, 5/7, 5/7 | no (smooth) / no (smooth) / no (smooth) |
| v0.2.2 (DK22 main) | MF4 (alone) | 242,885 (-44%) | -145,799 / -199,315 | -89,332 / -73,124 | 24,565 / 28,083 | 29,234 / 16,454 | 843 / 549 | 5/9, 4/7, 4/7 | no / no / no |
| v0.2.2 (DK22 main) | MF5 (alone) | 45,191 (-82%) | -84,752 / -103,673 | -21,271 / -50,861 | 8,705 / 13,987 | 12,960 / 8,125 | 684 / 712 | 6/9, 3/7, 4/7 | no / no / no |
| v0.3 (DK3 main) | MF1 (alone) | 758,672 (-40%) | -136,263 / -158,282 | -64,062 / -81,412 | 28,463 / 38,170 | 27,254 / 29,179 | 640 / 543 | 5/9, 5/7, 3/7 | no / no / no |
| v0.3 (DK3 main) | MF2 (alone) | 6,153 (-96%) | -252,359 / -263,422 | -49,914 / -59,825 | 21,275 / 23,724 | 14,354 / 15,369 | 745 / 629 | 4/9, 3/7, 3/7 | no / no / no |
| v0.3 (DK3 main) | MF4 (alone) | 204,524 (-53%) | -202,867 / -199,315 | -62,974 / -73,124 | 24,182 / 28,083 | 14,544 / 16,454 | 814 / 549 | 5/9, 2/7, 6/7 | no / no / no |
| v0.3 (DK3 main) | MF5 (alone) | 166,326 (-35%) | -91,139 / -103,673 | -34,616 / -50,861 | 11,744 / 13,987 | 7,125 / 8,125 | 840 / 712 | 7/9, 3/7, 4/7 | no / no / no |
| v0.4 ratchet-only | MF1 (alone) | 864,251 (-32%) | -178,982 / -158,282 | -68,385 / -81,412 | 32,504 / 38,170 | 98,349 / 29,179 | 638 / 543 | 4/9, 4/7, 2/7 | no / no / no |
| v0.4 ratchet-only | MF2 (alone) | -301,186 (-277%) | -353,806 / -263,422 | -70,723 / -59,825 | 22,839 / 23,724 | 42,274 / 15,369 | 1075 / 629 | 1/9, 1/7, 2/7 | no / no / no |
| v0.4 ratchet-only | MF4 (alone) | 253,380 (-41%) | -171,492 / -199,315 | -61,995 / -73,124 | 29,638 / 28,083 | 39,134 / 16,454 | 1227 / 549 | 2/9, 1/7, 4/7 | no / no / no |
| v0.4 ratchet-only | MF5 (alone) | 204,975 (-20%) | -140,141 / -103,673 | -43,523 / -50,861 | 12,234 / 13,987 | 20,385 / 8,125 | 1154 / 712 | 4/9, 3/7, 4/7 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF1 (alone) | 971,599 (-23%) | -164,535 / -158,282 | -68,385 / -81,412 | 35,963 / 38,170 | 23,004 / 29,179 | 663 / 543 | 5/9, 4/7, 3/7 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF2 (alone) | -118,782 (-170%) | -251,555 / -263,422 | -56,195 / -59,825 | 21,510 / 23,724 | 14,339 / 15,369 | 945 / 629 | 3/9, 3/7, 3/7 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF4 (alone) | 295,470 (-32%) | -200,157 / -199,315 | -70,645 / -73,124 | 27,271 / 28,083 | 14,544 / 16,454 | 570 / 549 | 4/9, 1/7, 3/7 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF5 (alone) | 218,871 (-15%) | -143,969 / -103,673 | -41,523 / -50,861 | 11,972 / 13,987 | 7,030 / 8,125 | 1027 / 712 | 8/9, 3/7, 5/7 | no / no / no |
| v0.5 bank half, run half | MF1 (alone) | 768,319 (-39%) | -169,627 / -158,282 | -68,385 / -81,412 | 31,186 / 38,170 | 139,489 / 29,179 | 616 / 543 | 4/9, 4/7, 2/7 | no / no / no |
| v0.5 bank half, run half | MF2 (alone) | -321,214 (-289%) | -343,624 / -263,422 | -68,033 / -59,825 | 21,373 / 23,724 | 52,554 / 15,369 | 965 / 629 | 2/9, 3/7, 2/7 | no / no / no |
| v0.5 bank half, run half | MF4 (alone) | 291,816 (-33%) | -157,740 / -199,315 | -54,481 / -73,124 | 25,793 / 28,083 | 64,734 / 16,454 | 1325 / 549 | 4/9, 2/7, 3/7 | no / no / no |
| v0.5 bank half, run half | MF5 (alone) | 199,841 (-22%) | -132,406 / -103,673 | -43,523 / -50,861 | 11,445 / 13,987 | 32,755 / 8,125 | 1031 / 712 | 5/9, 3/7, 4/7 | no / no / no |
| v0.6 ratchet + ABORT | MF1 (alone) | 850,757 (-33%) | -178,982 / -158,282 | -68,385 / -81,412 | 32,671 / 38,170 | 98,349 / 29,179 | 639 / 543 | 4/9, 4/7, 2/7 | no / no / no |
| v0.6 ratchet + ABORT | MF2 (alone) | -301,186 (-277%) | -353,806 / -263,422 | -70,723 / -59,825 | 22,839 / 23,724 | 42,274 / 15,369 | 1075 / 629 | 1/9, 1/7, 2/7 | no / no / no |
| v0.6 ratchet + ABORT | MF4 (alone) | 253,380 (-41%) | -171,492 / -199,315 | -61,995 / -73,124 | 29,638 / 28,083 | 39,134 / 16,454 | 1227 / 549 | 2/9, 1/7, 4/7 | no / no / no |
| v0.6 ratchet + ABORT | MF5 (alone) | 204,975 (-20%) | -140,141 / -103,673 | -43,523 / -50,861 | 12,234 / 13,987 | 20,385 / 8,125 | 1154 / 712 | 4/9, 3/7, 4/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF1 (alone) | 759,841 (-40%) | -204,279 / -158,282 | -63,486 / -81,412 | 35,771 / 38,170 | 26,679 / 29,179 | 579 / 543 | 4/9, 2/7, 2/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF2 (alone) | 85,197 (-50%) | -287,371 / -263,422 | -63,777 / -59,825 | 22,480 / 23,724 | 14,354 / 15,369 | 741 / 629 | 3/9, 4/7, 3/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF4 (alone) | 408,239 (-6%) | -218,081 / -199,315 | -64,591 / -73,124 | 27,773 / 28,083 | 14,544 / 16,454 | 827 / 549 | 3/9, 0/7, 4/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF5 (alone) | 297,756 (+16%) | -102,212 / -103,673 | -47,174 / -50,861 | 12,622 / 13,987 | 7,145 / 8,125 | 833 / 712 | 5/9, 2/7, 4/7 | no / no / no |
| best single landscape code per book (MF1 g75a30, MF2 tr50, MF4 g67a70, MF5 x7) | MF1 (in mix) | 2,920,493 (+3%) | -148,601 / -163,622 | -103,227 / -110,130 | 51,954 / 54,746 | 18,624 / 29,179 | 504 / 543 | 6/9, 3/7, 4/7 | no / no / no |
| best single landscape code per book (MF1 g75a30, MF2 tr50, MF4 g67a70, MF5 x7) | MF2 (in mix) | 2,554,880 (-10%) | -167,136 / -163,622 | -104,639 / -110,130 | 50,928 / 54,746 | 10,724 / 15,369 | 1053 / 629 | 3/9, 1/7, 2/7 | no / no / no |
| best single landscape code per book (MF1 g75a30, MF2 tr50, MF4 g67a70, MF5 x7) | MF4 (in mix) | 2,850,996 (+0%) | -158,564 / -163,622 | -118,756 / -110,130 | 52,064 / 54,746 | 13,189 / 16,454 | 389 / 549 | 4/9, 3/7, 5/7 | no / no / no |
| best single landscape code per book (MF1 g75a30, MF2 tr50, MF4 g67a70, MF5 x7) | MF5 (in mix) | 2,850,593 (+0%) | -167,262 / -163,622 | -100,355 / -110,130 | 54,321 / 54,746 | 6,100 / 8,125 | 539 / 712 | 3/9, 2/7, 5/7 | no / no / no |

# London: window 202309-202610 (37 months)

## London: SESSION MIX

| design | books in the mix / not complete | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1, MF3 | 284,800 (-68%) | -336,126 / -224,333 | -82,790 / -107,350 | 19,661 / 23,472 | 22,529 / 19,919 | 1484 / 923 | 6/14, 5/11, 4/12 | no / no / no |
| v0.3 (DK3 main) | MF1, MF3 | 449,142 (-49%) | -274,932 / -224,333 | -67,484 / -107,350 | 19,410 / 23,472 | 17,239 / 19,919 | 1398 / 923 | 6/14, 2/11, 4/12 | no / no / no |
| v0.4 ratchet-only | MF1, MF3 | 639,210 (-27%) | -333,975 / -224,333 | -127,907 / -107,350 | 25,654 / 23,472 | 26,819 / 19,919 | 1306 / 923 | 1/14, 2/11, 0/12 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF1, MF3 | 883,652 (+0%) | -244,175 / -224,333 | -106,687 / -107,350 | 23,197 / 23,472 | 19,179 / 19,919 | 966 / 923 | 8/14, 5/11, 8/12 | no / no / no |
| v0.5 bank half, run half | MF1, MF3 | 727,136 (-17%) | -267,977 / -224,333 | -111,256 / -107,350 | 23,365 / 23,472 | 30,414 / 19,919 | 1215 / 923 | 1/14, 3/11, 0/12 | no / no / no |
| v0.6 ratchet + ABORT | MF1, MF3 | 625,315 (-29%) | -348,763 / -224,333 | -117,276 / -107,350 | 25,413 / 23,472 | 26,819 / 19,919 | 1316 / 923 | 2/14, 2/11, 1/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF1, MF3 | 575,916 (-35%) | -272,902 / -224,333 | -104,866 / -107,350 | 23,409 / 23,472 | 18,039 / 19,919 | 1411 / 923 | 6/14, 2/11, 3/12 | no / no / no |
| v0.8 (scale out in thirds) | none complete | not run yet |||||||| 
| v0.9 (volatility-sized give-back) | none complete | not run yet |||||||| 
| v0.10 (level-anchored stop) | none complete | not run yet |||||||| 
| v0.11 (trend day vs range day) | none complete | not run yet |||||||| 
| v0.12 (momentum roll-over) | none complete | not run yet |||||||| 
| v0.13 (tape-led defence (Asia, London only)) | none complete | not run yet |||||||| 
| v0.14 (time of session) | none complete | not run yet |||||||| 
| v0.15 (per-book winner profile) | none complete | not run yet |||||||| 
| A1 volatility stop at entry (2 x s5, same lots-risk, own target; compare in $ and DD, lots differ); post-result change 22 | none complete | not run yet |||||||| 
| A2 structure stop at entry (capped at own stop, own lots); post-result change 23 | none complete | not run yet |||||||| 
| A3 chandelier trail (3 x ATR5, no target); post-result change 24 | none complete | not run yet |||||||| 
| A4 EMA21 trail once up 1 unit (no target); post-result change 25 | none complete | not run yet |||||||| 
| A5 parabolic-SAR trail (no target); post-result change 26 | none complete | not run yet |||||||| 
| B1 R-multiple ladder (thirds at 1R/2R, ratchet runner); post-result change 27 | none complete | not run yet |||||||| 
| B2 exhaustion take (RSI14 80/20 turn, half); post-result change 28 | none complete | not run yet |||||||| 
| B3 VWAP-band take (+/-2 sd, half); post-result change 29 | none complete | not run yet |||||||| 
| C1 halve-and-hold (cut half at -50% of stop); post-result change 30 | none complete | not run yet |||||||| 
| C2 adverse-speed cut (1 unit in 60 s); post-result change 31 | none complete | not run yet |||||||| 
| D1 pyramid into a winner (+1R add half once, stop to entry, ratchet) | none complete | not run yet |||||||| 
| D2 scale-in entry (half first, add half if up 0.5 unit in median time) | none complete | not run yet |||||||| 
| E1 continuation re-entry after a ratchet stop-out in profit | none complete | not run yet |||||||| 
| E2 no same-direction re-entry 15 min after a full stop | none complete | not run yet |||||||| 
| F1 calendar-aware (ratchet 2 min before top-tier release, no entries -5/+5 min) | none complete | not run yet |||||||| 
| F2 volatility regime (high -> no target + ratchet; low -> bracket) | none complete | not run yet |||||||| 
| F3 day-of-week / opex / month-end (table first, one design only if it shows something) | none complete | not run yet |||||||| 
| G1 DAY PROFIT RATCHET (never give back half the session peak above 1.0x median winning day) | none complete | not run yet |||||||| 
| G2 same-direction crowd (3+ books in profit: bank the oldest, ratchet the rest) | none complete | not run yet |||||||| 
| G3 opposite books may not add | none complete | not run yet |||||||| 
| G4 loss-streak brake (after 3 full stops, half lots) | none complete | not run yet |||||||| 
| v0.16 (the screens set the leash; post-result change 19) | none complete | not run yet |||||||| 
| v0.17 (the screens choose the day; post-result change 20) | none complete | not run yet |||||||| 
| v0.18 (slow divergence at the highs; post-result change 21) | none complete | not run yet |||||||| 
| best single landscape code per book (MF1 tr100, MF3 so0) | MF1, MF3 | 778,909 (-12%) | -319,212 / -224,333 | -76,627 / -107,350 | 25,852 / 23,472 | 20,265 / 19,919 | 999 / 923 | 3/14, 2/11, 3/12 | no / no / no |

## London: PER BOOK

| design | book (row type) | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF1 (alone) | 198,554 (-61%) | -213,104 / -107,192 | -40,155 / -52,798 | 12,176 / 16,123 | 22,529 / 19,919 | 548 / 321 | 9/14, 7/11, 7/12 | no / no / no |
| v0.2.2 (DK22 main) | MF3 (alone) | -98,813 (-153%) | -153,491 / -47,177 | -13,866 / -23,120 | 4,755 / 6,993 | 8,310 / 7,190 | 936 / 602 | 8/14, 6/11, 7/12 | no / no / no |
| v0.3 (DK3 main) | MF1 (alone) | 222,264 (-56%) | -156,679 / -107,192 | -36,382 / -52,798 | 11,948 / 16,123 | 17,239 / 19,919 | 531 / 321 | 9/14, 7/11, 7/12 | no / no / no |
| v0.3 (DK3 main) | MF3 (alone) | 41,819 (-77%) | -47,513 / -47,177 | -16,070 / -23,120 | 5,809 / 6,993 | 6,755 / 7,190 | 867 / 602 | 7/14, 4/11, 4/12 | no / no / no |
| v0.4 ratchet-only | MF1 (alone) | 336,401 (-34%) | -238,574 / -107,192 | -61,368 / -52,798 | 17,726 / 16,123 | 26,819 / 19,919 | 590 / 321 | 1/14, 3/11, 2/12 | no / no / no |
| v0.4 ratchet-only | MF3 (alone) | 117,749 (-36%) | -68,905 / -47,177 | -27,550 / -23,120 | 6,784 / 6,993 | 9,010 / 7,190 | 716 / 602 | 6/14, 6/11, 3/12 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF1 (alone) | 505,442 (-1%) | -103,322 / -107,192 | -46,887 / -52,798 | 16,210 / 16,123 | 19,179 / 19,919 | 341 / 321 | 8/14, 8/11, 8/12 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF3 (alone) | 193,150 (+4%) | -54,519 / -47,177 | -23,030 / -23,120 | 7,160 / 6,993 | 7,155 / 7,190 | 625 / 602 | 9/14, 6/11, 10/12 | no / no / no |
| v0.5 bank half, run half | MF1 (alone) | 424,262 (-17%) | -150,243 / -107,192 | -55,033 / -52,798 | 15,705 / 16,123 | 30,414 / 19,919 | 594 / 321 | 4/14, 5/11, 2/12 | no / no / no |
| v0.5 bank half, run half | MF3 (alone) | 117,814 (-36%) | -64,812 / -47,177 | -27,395 / -23,120 | 6,528 / 6,993 | 19,690 / 7,190 | 621 / 602 | 9/14, 6/11, 4/12 | no / no / no |
| v0.6 ratchet + ABORT | MF1 (alone) | 319,553 (-37%) | -255,421 / -107,192 | -61,368 / -52,798 | 17,789 / 16,123 | 26,819 / 19,919 | 591 / 321 | 1/14, 3/11, 2/12 | no / no / no |
| v0.6 ratchet + ABORT | MF3 (alone) | 120,702 (-35%) | -68,727 / -47,177 | -27,550 / -23,120 | 6,733 / 6,993 | 9,010 / 7,190 | 725 / 602 | 8/14, 6/11, 4/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF1 (alone) | 350,922 (-31%) | -176,966 / -107,192 | -51,855 / -52,798 | 15,954 / 16,123 | 18,039 / 19,919 | 539 / 321 | 5/14, 4/11, 6/12 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF3 (alone) | 39,935 (-78%) | -90,945 / -47,177 | -27,950 / -23,120 | 7,272 / 6,993 | 6,640 / 7,190 | 872 / 602 | 2/14, 2/11, 4/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF3 so0) | MF1 (in mix) | 784,656 (-11%) | -371,371 / -224,333 | -71,741 / -107,350 | 26,303 / 23,472 | 16,919 / 19,919 | 504 / 321 | 5/14, 1/11, 4/12 | no / no / no |
| best single landscape code per book (MF1 tr100, MF3 so0) | MF3 (in mix) | 875,308 (-1%) | -193,751 / -224,333 | -111,154 / -107,350 | 23,561 / 23,472 | 20,265 / 7,190 | 495 / 602 | 3/14, 6/11, 2/12 | no / no / no |

# NY PM: window 202410-202610 (24 months)

## NY PM: SESSION MIX

| design | books in the mix / not complete | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF2, MF3 | 158,436 (-76%) | -110,164 / -134,363 | -42,993 / -44,139 | 16,414 / 20,021 | 24,499 / 28,539 | 744 / 454 | 6/9, 6/7, 1/7 | no / no / no |
| v0.3 (DK3 main) | MF2, MF3 | 422,023 (-36%) | -112,257 / -134,363 | -35,926 / -44,139 | 18,062 / 20,021 | 25,779 / 28,539 | 678 / 454 | 6/9, 5/7, 2/7 | no / no / no |
| v0.4 ratchet-only | MF2, MF3 | 726,210 (+10%) | -99,650 / -134,363 | -44,469 / -44,139 | 21,881 / 20,021 | 21,829 / 28,539 | 629 / 454 | 2/9, 1/7, 3/7 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF2, MF3 | 605,915 (-8%) | -109,320 / -134,363 | -44,139 / -44,139 | 19,947 / 20,021 | 21,829 / 28,539 | 458 / 454 | 2/9, 0/7, 5/7 | no / no / no |
| v0.5 bank half, run half | MF2, MF3 | 681,839 (+4%) | -101,387 / -134,363 | -43,934 / -44,139 | 21,500 / 20,021 | 22,819 / 28,539 | 488 / 454 | 1/9, 0/7, 3/7 | no / no / no |
| v0.6 ratchet + ABORT | MF2, MF3 | 727,261 (+11%) | -99,650 / -134,363 | -44,469 / -44,139 | 21,905 / 20,021 | 21,829 / 28,539 | 630 / 454 | 2/9, 1/7, 3/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF2, MF3 | 553,095 (-16%) | -133,019 / -134,363 | -45,519 / -44,139 | 19,285 / 20,021 | 25,309 / 28,539 | 558 / 454 | 1/9, 0/7, 3/7 | no / no / no |
| v0.8 (scale out in thirds) | none complete (MF3 not complete) | not run yet |||||||| 
| v0.9 (volatility-sized give-back) | none complete | not run yet |||||||| 
| v0.10 (level-anchored stop) | none complete | not run yet |||||||| 
| v0.11 (trend day vs range day) | none complete | not run yet |||||||| 
| v0.12 (momentum roll-over) | none complete | not run yet |||||||| 
| v0.13 (tape-led defence (Asia, London only)) | none complete | not run yet |||||||| 
| v0.14 (time of session) | none complete | not run yet |||||||| 
| v0.15 (per-book winner profile) | none complete (MF2 not complete) | not run yet |||||||| 
| A1 volatility stop at entry (2 x s5, same lots-risk, own target; compare in $ and DD, lots differ); post-result change 22 | none complete | not run yet |||||||| 
| A2 structure stop at entry (capped at own stop, own lots); post-result change 23 | none complete | not run yet |||||||| 
| A3 chandelier trail (3 x ATR5, no target); post-result change 24 | none complete | not run yet |||||||| 
| A4 EMA21 trail once up 1 unit (no target); post-result change 25 | none complete | not run yet |||||||| 
| A5 parabolic-SAR trail (no target); post-result change 26 | none complete | not run yet |||||||| 
| B1 R-multiple ladder (thirds at 1R/2R, ratchet runner); post-result change 27 | none complete | not run yet |||||||| 
| B2 exhaustion take (RSI14 80/20 turn, half); post-result change 28 | none complete | not run yet |||||||| 
| B3 VWAP-band take (+/-2 sd, half); post-result change 29 | none complete | not run yet |||||||| 
| C1 halve-and-hold (cut half at -50% of stop); post-result change 30 | none complete | not run yet |||||||| 
| C2 adverse-speed cut (1 unit in 60 s); post-result change 31 | none complete | not run yet |||||||| 
| D1 pyramid into a winner (+1R add half once, stop to entry, ratchet) | none complete | not run yet |||||||| 
| D2 scale-in entry (half first, add half if up 0.5 unit in median time) | none complete | not run yet |||||||| 
| E1 continuation re-entry after a ratchet stop-out in profit | none complete | not run yet |||||||| 
| E2 no same-direction re-entry 15 min after a full stop | none complete | not run yet |||||||| 
| F1 calendar-aware (ratchet 2 min before top-tier release, no entries -5/+5 min) | none complete | not run yet |||||||| 
| F2 volatility regime (high -> no target + ratchet; low -> bracket) | none complete | not run yet |||||||| 
| F3 day-of-week / opex / month-end (table first, one design only if it shows something) | none complete | not run yet |||||||| 
| G1 DAY PROFIT RATCHET (never give back half the session peak above 1.0x median winning day) | none complete | not run yet |||||||| 
| G2 same-direction crowd (3+ books in profit: bank the oldest, ratchet the rest) | none complete | not run yet |||||||| 
| G3 opposite books may not add | none complete | not run yet |||||||| 
| G4 loss-streak brake (after 3 full stops, half lots) | none complete | not run yet |||||||| 
| v0.16 (the screens set the leash; post-result change 19) | none complete | not run yet |||||||| 
| v0.17 (the screens choose the day; post-result change 20) | none complete | not run yet |||||||| 
| v0.18 (slow divergence at the highs; post-result change 21) | none complete | not run yet |||||||| 
| best single landscape code per book (MF2 xi15all, MF3 x7) | MF2, MF3 | 543,807 (-17%) | -79,217 / -134,363 | -47,044 / -44,139 | 19,579 / 20,021 | 18,575 / 28,539 | 336 / 454 | 3/9, 0/7, 3/7 | no / no / no |

## NY PM: PER BOOK

| design | book (row type) | income managed (vs bracket) | max DD managed / bracket | worst week managed / bracket | weekly st.dev. managed / bracket | largest single give-back $ managed / bracket | trades giving back > 50% of a peak >= $500, managed / bracket | smoother quarters all, up, down | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|
| v0.2.2 (DK22 main) | MF2 (alone) | -36,355 (-115%) | -113,521 / -165,629 | -23,729 / -41,926 | 8,485 / 18,229 | 24,499 / 28,539 | 357 / 239 | 8/9, 7/7, 6/7 | no (smooth) / no (smooth) / no (smooth) |
| v0.2.2 (DK22 main) | MF3 (alone) | 52,793 (-87%) | -106,151 / -75,125 | -28,499 / -28,888 | 8,526 / 14,432 | 18,829 / 14,494 | 387 / 215 | 6/9, 4/7, 3/7 | no / no / no |
| v0.3 (DK3 main) | MF2 (alone) | 70,585 (-70%) | -86,179 / -165,629 | -29,665 / -41,926 | 12,631 / 18,229 | 25,779 / 28,539 | 309 / 239 | 7/9, 6/7, 5/7 | no (smooth) / no (smooth) / no (smooth) |
| v0.3 (DK3 main) | MF3 (alone) | 221,462 (-47%) | -70,389 / -75,125 | -29,739 / -28,888 | 10,095 / 14,432 | 14,044 / 14,494 | 369 / 215 | 6/9, 4/7, 3/7 | no / no / no |
| v0.4 ratchet-only | MF2 (alone) | 392,175 (+67%) | -134,559 / -165,629 | -43,148 / -41,926 | 20,046 / 18,229 | 21,829 / 28,539 | 240 / 239 | 2/9, 4/7, 1/7 | no / no / no |
| v0.4 ratchet-only | MF3 (alone) | 512,234 (+23%) | -75,185 / -75,125 | -30,643 / -28,888 | 16,126 / 14,432 | 16,889 / 14,494 | 389 / 215 | 2/9, 1/7, 1/7 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF2 (alone) | 274,861 (+17%) | -156,572 / -165,629 | -43,148 / -41,926 | 19,145 / 18,229 | 21,829 / 28,539 | 235 / 239 | 6/9, 4/7, 4/7 | no / no / no |
| v0.4-ceiling (own target as ceiling) | MF3 (alone) | 412,114 (-1%) | -67,280 / -75,125 | -30,263 / -28,888 | 14,457 / 14,432 | 14,084 / 14,494 | 223 / 215 | 4/9, 3/7, 2/7 | no / no / no |
| v0.5 bank half, run half | MF2 (alone) | 353,325 (+50%) | -140,869 / -165,629 | -43,148 / -41,926 | 19,151 / 18,229 | 22,029 / 28,539 | 232 / 239 | 4/9, 4/7, 2/7 | no / no / no |
| v0.5 bank half, run half | MF3 (alone) | 460,498 (+11%) | -67,275 / -75,125 | -31,734 / -28,888 | 14,682 / 14,432 | 22,819 / 14,494 | 256 / 215 | 2/9, 1/7, 1/7 | no / no / no |
| v0.6 ratchet + ABORT | MF2 (alone) | 386,555 (+64%) | -134,559 / -165,629 | -43,148 / -41,926 | 19,967 / 18,229 | 21,829 / 28,539 | 241 / 239 | 2/9, 4/7, 1/7 | no / no / no |
| v0.6 ratchet + ABORT | MF3 (alone) | 512,234 (+23%) | -75,185 / -75,125 | -30,643 / -28,888 | 16,126 / 14,432 | 16,889 / 14,494 | 389 / 215 | 2/9, 1/7, 1/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF2 (alone) | 113,645 (-52%) | -167,293 / -165,629 | -41,926 / -41,926 | 17,979 / 18,229 | 25,309 / 28,539 | 252 / 239 | 7/9, 5/7, 4/7 | no / no / no |
| v0.7 bracket + near-target guard (pl70k50) | MF3 (alone) | 364,881 (-12%) | -67,969 / -75,125 | -30,263 / -28,888 | 13,325 / 14,432 | 14,084 / 14,494 | 306 / 215 | 3/9, 2/7, 3/7 | no / no / no |
| best single landscape code per book (MF2 xi15all, MF3 x7) | MF2 (in mix) | 633,457 (-4%) | -94,366 / -134,363 | -44,139 / -44,139 | 19,669 / 20,021 | 18,575 / 28,539 | 191 / 239 | 1/9, 1/7, 3/7 | no / no / no |
| best single landscape code per book (MF2 xi15all, MF3 x7) | MF3 (in mix) | 568,406 (-14%) | -103,870 / -134,363 | -47,239 / -44,139 | 20,271 / 20,021 | 12,119 / 14,494 | 145 / 215 | 1/9, 0/7, 3/7 | no / no / no |

## G. DESK-LEVEL ROWS (whole-mix sets TL3_DX_<S>_G<n>_M vs the live mix as run, same windows; G1 first)

| row | session | window | income managed / live (change) | max DD managed / live | worst DAY managed / live | worst week managed / live | weekly st.dev. | largest single DAY give-back (peak minus end of day, managed) | rule fired (days / entries) | floors 10 / 20 / 30% |
|---|---|---|---|---|---|---|---|---|---|---|
| G1 | Asia | | not built yet |||||||||
| G1 | NY AM | | not built yet |||||||||
| G1 | London | | not built yet |||||||||
| G1 | NY PM | | not built yet |||||||||
| G2 | Asia | | not built yet |||||||||
| G2 | NY AM | | not built yet |||||||||
| G2 | London | | not built yet |||||||||
| G2 | NY PM | | not built yet |||||||||
| G3 | Asia | | not built yet |||||||||
| G3 | NY AM | | not built yet |||||||||
| G3 | London | | not built yet |||||||||
| G3 | NY PM | | not built yet |||||||||
| G4 | Asia | | not built yet |||||||||
| G4 | NY AM | | not built yet |||||||||
| G4 | London | | not built yet |||||||||
| G4 | NY PM | | not built yet |||||||||

G3 (opposite books may not add): the cost / saving is the net of the live mix trades at the blocked entry times (kind g3 records: t, tag, side); matched list to be added when the first G3 rows exist (this generator reports the whole-mix result and the block counts). Rows are shown per session as the sets finish; ZZDEFG* smoke sets are not scored.

## CONTEXT DESIGNS v0.16 - v0.18 (post-result changes 19-21): availability and how often the context changed the action

Availability file: present, first lines: book,window,n,v16_avail,v16_loose,v16_mixed,v16_tight,v16_na,v17_avail,v17_UP,v17_DOWN,v17_MIXED,v17_NA,v18_avail / Asia MF1,window,150,0.92,0.11333333333333333,0.8,0.006666666666666667,0.08,0.9466666666666667,0.02,0.013333333333333334,0.9133333333333333,0.05333333333333334,0.41333333333333333 / Asia MF2,window,150,0.92,0.31333333333333335,0.6,0.006666666666666667,0.08,0.8266666666666667,0.006666666666666667,0.013333333333333334,0.8066666666666666,0.17333333333333334,0.16666666666666666 / Asia MF3,window,150,0.8533333333333334,0.16,0.6266666666666667,0.06666666666666667,0.14666666666666667,0.88,0.013333333333333334,0.013333333333333334,0.8533333333333334,0.12,0.15333333333333332 / NY AM MF1,window,150,1.0,0.2,0.6866666666666666,0.11333333333333333,0.0,0.9933333333333333,0.02,0.02,0.9533333333333334,0.006666666666666667,0.9866666666666667 / NY AM MF1,pre-2024-10,150,1.0,0.14,0.68,0.18,0.0,0.74,0.0,0.0,0.74,0.26,0.0

| design | session | trades with a context rule id (TR / HL / DV / LP) or AGR:L/M/T in the log, share (of trades, books complete) |
|---|---|---|
| v0.16 (the screens set the leash; post-result change 19) | Asia | no complete rows yet |
| v0.16 (the screens set the leash; post-result change 19) | NY AM | no complete rows yet |
| v0.16 (the screens set the leash; post-result change 19) | London | no complete rows yet |
| v0.16 (the screens set the leash; post-result change 19) | NY PM | no complete rows yet |
| v0.17 (the screens choose the day; post-result change 20) | Asia | no complete rows yet |
| v0.17 (the screens choose the day; post-result change 20) | NY AM | no complete rows yet |
| v0.17 (the screens choose the day; post-result change 20) | London | no complete rows yet |
| v0.17 (the screens choose the day; post-result change 20) | NY PM | no complete rows yet |
| v0.18 (slow divergence at the highs; post-result change 21) | Asia | no complete rows yet |
| v0.18 (slow divergence at the highs; post-result change 21) | NY AM | no complete rows yet |
| v0.18 (slow divergence at the highs; post-result change 21) | London | no complete rows yet |
| v0.18 (slow divergence at the highs; post-result change 21) | NY PM | no complete rows yet |
