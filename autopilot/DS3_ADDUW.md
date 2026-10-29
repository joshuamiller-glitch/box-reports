# DS3_ADDUW - staged under-water-only adds on the existing entries of the live/D6 books (ADDUW, 2026-10-29)
Research only; UNTOUCHED (label day > 2026-02-06) never read; no live/execution change. Prereg `autopilot/ADDUW_prereg.md` sha256 30b6c95ebe3d6bc55b9ea1f0943e9bd8f02fff8fb3c41fca08a9d07798984404 (DECISIONS.md), amendment A1 (cost basis), looks #1 (B0), #2 (B2), #3 (B1) logged. Code `l2vast/ds3/code/adduw/`, outputs `l2vast/ds3/out/adduw/`. HOLD-mask audit: no vs_lib.WINS use; in-house windows capped at 20260206 and all rows filtered to <= 20260206 before simulation (two unmasked identity smoke tests printed aggregate sums only; disclosed).

## VERDICT (one line per book; recent windows first; PRE-selected cell; stack $ are the 10-lot stack scale)
Every set is **DEAD** on every cost basis (no PASS, no CANDIDATE, no LEAD): no cell clears G2 (HOLD CI), G3 (tail), G4 (placebo), G9 (best-of-F). Mean results are positive on the prereg-faithful basis B2 for several sets but all sit inside their MDE, are concentrated in 2025 and flip sign with the cost basis.
Format: set | selected cell | 2026 (6 wk, i.e. ~5 weeks, n trades, $/wk [MDE]) | last 6 m | HOLD | PRE | X'.
* **STACK (6 live books, lock engine)**: B2 cell #5 (50% initial + one add at -5 pt, no gate, target kept, risk-matched to the original stop): 2026 +857/wk [MDE 30,847] (n 1,326 trades, +0.17 pt/trade); last 6 m +6,772 [18,144]; HOLD +5,924 [16,024]; PRE +6,403 [14,877]; X' +4,726 [9,793] -> DEAD (fails G2, G3, G4, G5, G9). Mean is NOT supported (every CI contains 0); 2025 alone carries +636k against a 2024-26 total of +611k (2024 -30k).
* **ST**: B2 #5: 2026 -2,292 [32,280]; 6 m -484 [14,095]; HOLD -1,158 [12,396]; PRE +4,569; X' -193 -> DEAD (G1,G2,G3,G4,G6,G9).
* **HM**: B2 #145: 2026 -9,898 [27,864]; 6 m -7,212 [14,108]; HOLD -6,583 [13,646]; PRE +3,265; X' -6,214 -> DEAD (negative OOS everywhere).
* **WT**: B2 #221 (50% + one add at -20 pt, no gate, target kept, risk-matched): 2026 +20,924 [17,389] (+1.54 pt/trade, n 351); 6 m +4,387 [9,486]; HOLD +3,069 [8,485]; PRE +6,494 [7,319]; X' +316 [6,103] -> DEAD (G2,G3,G4,G9); the only book with positive recent windows; 342 of its 1,728 cells are CANDIDATE-RECENT (below). On the mixed basis B0 it is -819 in HOLD.
* **KB**: B2 #464: 2026 +1,345 [13,375]; 6 m -3,761 [7,659]; HOLD -2,523; PRE +2,333; X' -1,180 -> DEAD.
* **SM**: B2 #842 (33%/2 stages, X=20, no-pull-relative gate): 2026 -4,317 [15,181] (n 57 trades); 6 m +2,213 [10,748]; HOLD +2,375 [9,762]; PRE +1,727; X' -1,486 -> DEAD (G2..G7,G9). It beats the random-timing placebo (rank 0.975 PRE / 0.99 HOLD) and the shuffled-book placebo (0.99 / 0.90) but both placebo means are negative and the cell fails tails, years and X'.
* **PE (engine PB)**: B2 #218: 2026 +3,652 [43,845]; 6 m -6,176 [12,587]; HOLD -5,618 [11,296]; PRE +2,159; X' +663 -> DEAD.
* **D6-family trade-level (10 lots, no locks)**: PB #589: 2026 -10,342, 6 m -8,910, HOLD -2,860, PRE +9,833 (best-of-F RC p 0.038 in PRE only), X' +917 -> DEAD; DN #418: 2026 +11,871 [39,501], 6 m +2,081, HOLD +2,929, PRE -477 (no PRE-positive cell of 1,728), X' -5,256 -> DEAD; MV #365: 2026 -7,186, 6 m +10,041 [12,283], HOLD +8,505 [11,049] (HOLD CI excludes 0), PRE +5,486, X' -935 -> DEAD (G3..G7,G9); MA #5: 2026 -3,185, 6 m +1,090, HOLD +755, PRE +995, X' -621 -> DEAD. CR: not applicable (dynamic exit).

**Plain sentence on the gates:** no order-book gate picks the dips that recover. At the first add, P(target first | dip) is 0.41 ungated at X=10 pt (PRE) and every real gate is lower or equal (imb5>=0.2 0.400, imb5>=0.3 0.386, delta60 0.402, absorption 0.398, near-wall 0.369, relative no-pull 0.396); pooled over X=5..30 the ungated rate is 0.379/0.369/0.329 (HOLD/PRE/X') against 0.363/0.355/0.319 for imb5>=0.2, 0.363/0.354/0.319 for absorption, 0.371/0.363/0.325 for delta60 and 0.327/0.327/0.292 for the near wall; the strict no-pulled-size gate (pulled size exactly 0) fires on only 0.5-2% of dips (105-490 adds per window), its win rate (0.36/0.42/0.35) is inside noise and its pts per add flips sign by window (-6.2 / +2.9 / +4.3 at X=10). The no-gate rate matches the MAEMFE base map (ST PRE P(target | MAE>=10) 0.419, X=5 0.463 vs my 0.46 pooled), which is the sanity check.

## Structural fact tested (adds raise exposure on the trades that lose)
With the original stop and the remaining live size as adds, a staged entry LOSES LESS at the stop (initial 50% at E, add 50% at E-X: loss 60 - X/2 pt per lot) and wins MORE at a kept target (60 + X/2), but is half-size on the trades that never dip X; 98-99% of trades are under water by a tick, 92% by 5 pt, 85% by 10, 79% by 15, 73% by 20, 65% by 30 (ST PRE; same as MAEMFE), so the never-under-water case is rare (1.2-2.6% of trades never trade below entry; 9-15% never reach -5 pt) and the cost is a trade-off, not a free lunch. The stack tail therefore does NOT get worse for lot-matched stop-original cells: the stack's 20 worst weeks (FULL, base -3,534,170) change by +249,133 (+7.0%) for the B2 stack cell (+1,705,206 / +48% for the B1 PRE-best, +890,732 / +25% for the B0 least-bad cell), but PRE maxDD gets WORSE (+55,748 = +13.6% on 409,229; HOLD +4,176 = +0.7% on 578,442; X' -12,418 = -2.7%), PRE worst week -20,066 worse, and PRE worst-20 -27,563 (-1.8%): G3 fails. Risk-matched (cap-orig, total up to 2.0x live) is the tail-honest comparison and carries the same equal dollar loss at the original stop by construction; no set passes G1 (mean) and G3 (tail) together on B2; on B1 only MA does (PRE +874, HOLD +730, MDE 3,848) and its random-timing/shuffled placebos give ranks 0.66/0.92 (PRE) and 0.82/0.985 (HOLD): G4 fails, so it is DEAD, not LEAD.

## Recent-first tables (all sets, three cost bases)
Bases: **B2** = prereg-faithful (V0 fills for the parent AND every add: market +1 tick, stop 1.01, time 0.995, target year correction 1.4/1.5/4.2/4.3 pt; baseline single on the same basis; PRIMARY). **B1** = stack-official mapped P9 correction for every fill (adds +0.25 tick). **B0** = parent P9-mapped, adds V0 (mixed; superseded by amendment A1, kept as sensitivity). The sign of the mean flips with the basis (stack PRE-selected cell: B2 HOLD +5.9k, B1 HOLD +2.5k and X' -27.7k, B0 HOLD -29.8k and negative in every window).

### Basis B2: PRE-selected cell per set, recent windows first (delta vs single, $/week at live lots, 10-lot stack scale for the stack; pts/trade per live lot net of 0.242 pt fee; MDE = 2.8 SD/sqrt(n weeks))

| set | cell (selected on PRE only) | 2026 (6 wk) $/wk [MDE] pts/tr | last 6 m (28 wk) $/wk [MDE] pts/tr | HOLD (32 wk) $/wk [MDE] pts/tr | PRE (74 wk) $/wk [MDE] | X' (43 wk) $/wk [MDE] | tier | failed gates |
|--|--|--|--|--|--|--|--|--|
| ST | #5 50%/1st X=5pt none tgt-orig stop-riskcap | -2292 [32280] +0.28 (n=245) | -484 [14095] +0.46 (n=1097) | -1158 [12396] +0.36 (n=1218) | +4569 [7998] | -193 [4472] | DEAD | G1,G2,G3,G4,G6,G9 |
| HM | #145 50%/1st X=15pt none tgt-reb stop-reb | -9898 [27864] -3.33 (n=183) | -7212 [14108] -2.21 (n=830) | -6583 [13646] -1.54 (n=923) | +3265 [9876] | -6214 [8041] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| WT | #221 50%/1st X=20pt none tgt-orig stop-riskcap | +20924 [17389] +1.54 (n=351) | +4387 [9486] +0.75 (n=1484) | +3069 [8485] +0.81 (n=1655) | +6494 [7319] | +316 [6103] | DEAD | G2,G3,G4,G9 |
| KB | #464 50%/1st X=0.5xstop wall tgt-orig stop-riskcap | +1345 [13375] -0.09 (n=254) | -3761 [7659] -0.45 (n=1123) | -2523 [6893] -0.19 (n=1231) | +2333 [6277] | -1180 [7525] | DEAD | G1,G2,G3,G4,G5,G6,G9 |
| SM | #842 33%/2st X=20pt nopull_rel tgt-orig stop-riskcap | -4317 [15181] -4.57 (n=57) | +2213 [10748] -0.17 (n=269) | +2375 [9762] -0.71 (n=308) | +1727 [5793] | -1486 [5887] | DEAD | G2,G3,G4,G5,G6,G7,G9 |
| PE(PB) | #218 50%/1st X=20pt none tgt-reb stop-riskcap | +3652 [43845] +3.71 (n=236) | -6176 [12587] +0.13 (n=1026) | -5618 [11296] +0.01 (n=1130) | +2159 [4956] | +663 [6727] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| STACK | #5 50%/1st X=5pt none tgt-orig stop-riskcap | +857 [30847] +0.17 (n=1326) | +6772 [18144] +0.39 (n=5829) | +5924 [16024] +0.34 (n=6465) | +6403 [14877] | +4726 [9793] | DEAD | G2,G3,G4,G5,G9 |
| D_PB | #589 33%/2st X=5pt imb5>=.2 tgt-orig stop-reb | -10342 [19719] -1.28 (n=195) | -8910 [13460] -1.34 (n=866) | -2860 [14315] -0.51 (n=965) | +9833 [8475] | +917 [7650] | DEAD | G1,G2,G4,G5,G6 |
| D_DN | #418 50%/1st X=0.25xstop delta60 tgt-orig stop-reb (PRE<=0, best of 1728 anyway) | +11871 [39501] +1.88 (n=146) | +2081 [15080] +0.62 (n=701) | +2929 [14037] +0.59 (n=782) | -477 [8361] | -5256 [7815] | DEAD | G1,G2,G3,G4,G5,G6,G9 |
| D_MV | #365 50%/1st X=0.25xstop none tgt-orig stop-riskcap | -7186 [14083] -0.77 (n=272) | +10041 [12283] +1.24 (n=1133) | +8505 [11049] +1.13 (n=1253) | +5486 [7988] | -935 [5592] | DEAD | G3,G4,G5,G6,G7,G9 |
| D_MA | #5 50%/1st X=5pt none tgt-orig stop-riskcap | -3185 [6330] -1.31 (n=87) | +1090 [3961] +0.37 (n=407) | +755 [3848] +0.30 (n=474) | +995 [1997] | -621 [2992] | DEAD | G2,G3,G4,G5,G6,G7,G9 |

### Basis B1: PRE-selected cell per set, recent windows first (delta vs single, $/week at live lots, 10-lot stack scale for the stack; pts/trade per live lot net of 0.242 pt fee; MDE = 2.8 SD/sqrt(n weeks))

| set | cell (selected on PRE only) | 2026 (6 wk) $/wk [MDE] pts/tr | last 6 m (28 wk) $/wk [MDE] pts/tr | HOLD (32 wk) $/wk [MDE] pts/tr | PRE (74 wk) $/wk [MDE] | X' (43 wk) $/wk [MDE] | tier | failed gates |
|--|--|--|--|--|--|--|--|--|
| ST | #1022 33%/2st X=0.5xstop imb5>=.2 tgt-orig stop-riskcap | -1008 [48943] -0.36 (n=245) | -11033 [17465] -0.82 (n=1097) | -9912 [16601] -0.80 (n=1218) | +10656 [12948] | -11879 [12157] | DEAD | G1,G2,G3,G4,G5,G6,G9 |
| HM | #649 33%/2st X=10pt none tgt-reb stop-reb | -4075 [37284] -3.06 (n=183) | -4940 [17950] -2.46 (n=830) | -4064 [16918] -1.95 (n=923) | +4279 [10048] | -7257 [9190] | DEAD | G1,G2,G3,G4,G5,G6,G9 |
| WT | #266 50%/1st X=20pt nopull_rel tgt-orig stop-riskcap | +14246 [26313] +0.56 (n=351) | +6657 [9490] +0.46 (n=1484) | +5628 [8770] +0.69 (n=1655) | +6449 [6185] | -30 [6475] | DEAD | G2,G3,G4,G6,G9 |
| KB | #1373 25%/3st X=20pt none tgt-orig stop-riskcap | -1405 [17646] +2.41 (n=254) | +2992 [9906] +2.06 (n=1123) | +3696 [8843] +2.62 (n=1231) | +3987 [8465] | -9405 [9453] | DEAD | G2,G3,G4,G5,G6,G9 |
| SM | #67 50%/1st X=5pt absorb tgt-orig stop-reb | -3793 [10384] -2.64 (n=57) | +1321 [5556] +0.83 (n=269) | +855 [4916] +0.36 (n=308) | +1263 [3630] | +589 [3161] | DEAD | G2,G3,G4,G5,G6,G7,G9 |
| PE(PB) | #281 50%/1st X=20pt absorb tgt-reb stop-riskcap | +4763 [46926] +3.64 (n=236) | -4410 [12866] +0.50 (n=1026) | -3298 [11433] +0.51 (n=1130) | +2877 [5089] | +256 [7020] | DEAD | G1,G2,G3,G4,G5,G6,G9 |
| STACK | #1022 33%/2st X=0.5xstop imb5>=.2 tgt-orig stop-riskcap | +14838 [82352] +0.90 (n=1326) | -2613 [35824] +0.60 (n=5829) | +2461 [36245] +0.72 (n=6465) | +22216 [28499] | -27737 [29949] | DEAD | G2,G3,G4,G5,G6,G9 |
| D_PB | #589 33%/2st X=5pt imb5>=.2 tgt-orig stop-reb | -12497 [19196] -1.60 (n=195) | -10751 [13189] -1.64 (n=866) | -4847 [13997] -0.84 (n=965) | +8022 [8180] | +193 [7638] | DEAD | G1,G2,G4,G5,G6,G9 |
| D_DN | #509 50%/1st X=0.75xstop none tgt-orig stop-riskcap | +28753 [56411] +4.93 (n=146) | +2634 [21175] +0.75 (n=701) | +2153 [19652] +0.48 (n=782) | +598 [11994] | -3725 [12809] | DEAD | G2,G3,G4,G5,G6,G8,G9 |
| D_MV | #941 33%/2st X=0.25xstop none tgt-orig stop-riskcap | +2128 [39675] +0.34 (n=272) | +15014 [19709] +2.00 (n=1133) | +12894 [18026] +1.70 (n=1253) | +11193 [13318] | -3907 [8299] | DEAD | G3,G4,G5,G6,G7,G9 |
| D_MA | #5 50%/1st X=5pt none tgt-orig stop-riskcap | -3132 [6397] -1.29 (n=87) | +1068 [3955] +0.37 (n=407) | +730 [3848] +0.29 (n=474) | +874 [2017] | -869 [2994] | DEAD | G2,G4,G5,G6,G7,G9 |

### Basis B0: PRE-selected cell per set, recent windows first (delta vs single, $/week at live lots, 10-lot stack scale for the stack; pts/trade per live lot net of 0.242 pt fee; MDE = 2.8 SD/sqrt(n weeks))

| set | cell (selected on PRE only) | 2026 (6 wk) $/wk [MDE] pts/tr | last 6 m (28 wk) $/wk [MDE] pts/tr | HOLD (32 wk) $/wk [MDE] pts/tr | PRE (74 wk) $/wk [MDE] | X' (43 wk) $/wk [MDE] | tier | failed gates |
|--|--|--|--|--|--|--|--|--|
| ST | #3 50%/1st X=5pt none tgt-orig stop-orig | -594 [28347] -1.13 (n=245) | -3116 [12373] -0.87 (n=1097) | -3343 [10890] -0.92 (n=1218) | +1545 [7963] | -3201 [6547] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| HM | #361 50%/1st X=0.25xstop none tgt-reb stop-reb | -20641 [28905] -4.67 (n=183) | -11347 [18424] -3.45 (n=830) | -9687 [17468] -2.81 (n=923) | +514 [9627] | -7314 [8075] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| WT | #266 50%/1st X=20pt nopull_rel tgt-orig stop-riskcap | +8939 [31091] -0.13 (n=351) | +73 [10668] -0.59 (n=1484) | -819 [9564] -0.40 (n=1655) | +2950 [6383] | -909 [6395] | DEAD | G1,G2,G3,G4,G5,G6,G9 |
| KB | #320 50%/1st X=30pt wall tgt-orig stop-riskcap (PRE<=0, best of 1728 anyway) | -1168 [20548] -1.35 (n=254) | -3928 [9165] -1.67 (n=1123) | -2522 [8240] -1.39 (n=1231) | -678 [7026] | -2185 [7556] | DEAD | G1,G2,G4,G5,G6,G8,G9 |
| SM | #842 33%/2st X=20pt nopull_rel tgt-orig stop-riskcap | -8324 [16770] -6.27 (n=57) | -1515 [10618] -1.90 (n=269) | -824 [9556] -2.40 (n=308) | +468 [6062] | -1913 [5905] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| PE(PB) | #218 50%/1st X=20pt none tgt-reb stop-riskcap | +4833 [42761] +2.11 (n=236) | -8503 [12694] -1.17 (n=1026) | -7712 [11386] -1.28 (n=1130) | +381 [5679] | -187 [6802] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| STACK | #291 50%/1st X=30pt none tgt-orig stop-orig (PRE<=0, best of 1728 anyway) | -26662 [45598] -1.32 (n=1326) | -32732 [28118] -1.23 (n=5829) | -29803 [27793] -1.13 (n=6465) | -10707 [19337] | -20669 [23304] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| D_PB | #85 50%/1st X=10pt imb5>=.2 tgt-orig stop-reb | -27948 [14912] -3.80 (n=195) | -20890 [12689] -3.30 (n=866) | -15043 [13695] -2.50 (n=965) | +3005 [7476] | -812 [7354] | DEAD | G1,G2,G3,G4,G5,G6,G8,G9 |
| D_DN | #202 50%/1st X=15pt delta60 tgt-orig stop-reb (PRE<=0, best of 1728 anyway) | +5417 [38829] +0.72 (n=146) | -4169 [14545] -0.61 (n=701) | -3220 [13537] -0.67 (n=782) | -4769 [8356] | -6237 [7786] | DEAD | G1,G2,G3,G4,G5,G6,G7,G8,G9 |
| D_MV | #941 33%/2st X=0.25xstop none tgt-orig stop-riskcap (PRE<=0, best of 1728 anyway) | -21479 [38616] -2.09 (n=272) | -4100 [20473] -0.36 (n=1133) | -5556 [18468] -0.64 (n=1253) | -1602 [11895] | -5602 [8393] | DEAD | G1,G2,G3,G4,G5,G6,G7,G8,G9 |
| D_MA | #50 50%/1st X=5pt nopull_rel tgt-orig stop-riskcap (PRE<=0, best of 1728 anyway) | +1322 [18864] +0.42 (n=87) | -2673 [6650] -0.84 (n=407) | -2563 [6549] -0.81 (n=474) | -765 [5741] | +434 [4852] | DEAD | G1,G2,G4,G5,G7,G8,G9 |

## Gates and tiers (stack, B2 cell #5; others in the table above)
G1 raw and exposure-matched (k fixed on PRE lot-seconds, k=1.01) d_mean>0 in PRE and HOLD: PASS (+7,043 / +6,683 LM). G2 HOLD iid CI lower > 0: FAIL ([-4,282, +18,024]). G3 d_maxDD<=0, d_worst>=0, worst quintile>=0 in PRE and HOLD: FAIL (PRE maxDD +55,748, worst week -20,066). G4 placebos (rank vs random-timing P1 / shuffled-book P2, 100 stack draws): FAIL (PRE 0.31 / 0.98, HOLD 0.39 / 0.69; an ungated cell has no timing skill, P1 equals the real cell). G5 by year: FAIL (2024 -30,084; 2025 +636,068 = 104% of the 2024-26 total +611,129). G6 X' d_mean>=0, d_maxDD<=0, d_worst>=0: PASS (+4,726, -12,418, +659). G7 worst-20 change >= 0 over FULL: PASS (+249,133). G8 2x cost (add slippage and commission doubled, trade-level adjustment) WF mean > 0: PASS (+2,542/wk). G9 best-of-F: FAIL (White RC on PRE p 0.766 over 1,728 cells). Tier DEAD.
Best-of-F reality check on PRE (studentised, stationary bootstrap 5,000): B2 ST 0.65, HM 0.94, WT 0.19, KB 0.88, SM 0.96, PE 0.80, STACK 0.77, D_PB 0.038 (the one set below 0.05, PRE only), D_DN 1.0, D_MV 0.56, D_MA 0.69; B1 STACK 0.31, WT 0.075; B0 STACK 1.0 (zero PRE-positive cells of 1,728).

## CANDIDATE-RECENT (label, not a V2 tier): cells positive in 2026 AND the last 6 months (B2; ranked by last 6 months, HOLD tie-break; cells are data-mined on the recent windows, so read as hypotheses, MDE stated)
Counts (cells of 1,728 positive in both; also HOLD>0, PRE>0, X'>=0): ST 43 (1), HM 350 (0), WT 707 (342), KB 88 (6), SM 592 (7), PE 13 (0), STACK 86 (3), D_PB 5 (5), D_DN 87 (0), D_MV 44 (15), D_MA 5 (3). Best by last 6 months (2026 / 6 m / HOLD / PRE / X' $ per week, 6 m MDE): STACK #4 (50%/1, X=5, no gate, target kept, stop rebased) +7,153 / +15,585 / +12,551 / -495 / +803 [18,322]; WT #1085 (33%/2, X=0.25 stop, no gate, target kept, risk-matched) +26,400 / +15,584 / +12,198 / -144 / -563 [15,763]; KB #284 (50%/1, X=20, absorption) +10,990 / +6,063 / +5,118 / -2,805 / -2,930 [6,569]; SM #1363 (25%/3, X=15, absorption, stop rebased) +1,605 / +7,019 / +5,735 / -866 / +83 [10,127]; D_MV #1373 (25%/3, X=20, no gate) +3,975 / +14,178 / +11,654 / +2,055 / -9,469 [27,510]. None of these is positive in PRE and X' together except D_PB #5 and a few WT/MV cells; the 6 m values are all inside their MDE. Full list: `recent_rank_B2.parquet`.

## Tail (stack, B2 cell #5; change vs the unchanged stack; $ at 10 lots)
| window | n wk | d mean $/wk | MDE | maxDD base -> change | worst week base -> change | worst-20 weeks base -> change |
|--|--|--|--|--|--|--|
| 2026 | 6 | +857 | 30,847 | 185,098 -> -48,403 (-26.2%) | -185,098 -> +48,403 | -185,098 (1 wk) -> +48,403 (+26.2%) |
| last 6 m | 28 | +6,772 | 18,144 | 204,132 -> -67,438 (-33.0%) | -204,132 -> +67,438 | -389,230 (2 wk) -> +168,430 (+43.3%) |
| HOLD | 32 | +5,924 | 16,024 | 578,442 -> +4,176 (+0.7%) | -318,557 -> +9,320 | -914,949 (4 wk) -> +184,962 (+20.2%) |
| PRE | 74 | +6,403 | 14,877 | 409,229 -> +55,748 (+13.6%) | -306,664 -> -20,066 | -1,490,274 (8 wk) -> -27,563 (-1.8%) |
| X' | 43 | +4,726 | 9,793 | 460,909 -> -12,418 (-2.7%) | -157,300 -> +659 | -1,128,947 (8 wk) -> +91,734 (+8.1%) |
| FULL | 149 | +5,816 | 8,582 [CI -321, +12,114] | 578,442 -> +4,176 (+0.7%) | -318,557 -> -8,173 | -3,534,170 (20 wk) -> +249,133 (+7.0%) |
(B1 PRE-selected cell #1022: worst-20 FULL +1,705,206 (+48.2%), PRE maxDD +123,511 (+30.2%), X' d_mean -27,737. B0 least-bad cell #291: worst-20 +890,732 (+25.2%) with FULL mean -17,683/wk [CI -27,085, -8,246].)

## Breakdown of the B2 stack cell (selected on PRE only)
By book ($/wk PRE / HOLD / X' / last 6 m / 2026): ST +4,569 / -1,158 / -193 / -484 / -2,292; HM +1,255 / -1,438 / -46 / -1,814 / +35; WT +3,391 / +5,378 / +1,954 / +6,050 / +10,573; KB -298 / -572 / -472 / -860 / -1,346; SM -921 / +2,664 / +331 / +2,885 / -2,556; PE -1,592 / +1,050 / +3,151 / +994 / -3,558. By year (stack weekly sums): 2023 span +255,504 (39 wk), 2024 -30,084 (52), 2025 +636,068 (52), 2026 +5,145 (6). By entry session (trade level, no locks, mean $ per trade PRE / HOLD / X'): ASIA -9.7 / +20.1 / +94.9; LONDON +71.4 / +81.2 / -53.3; PRE +153.7 / +27.2 / -68.9; NY-AM +11.8 / -0.8 / +26.2; NY-PM -5.4 / +116.7 / +20.4; CLOSE +152 / +155 / +119 (n 141 total). No session is positive in all three windows except CLOSE (tiny n) and LONDON fails X'.
Never under water (PRE): never below entry by a tick 1.2% ST / 1.2% HM / 2.6% WT / 1.7% KB / 2.5% SM / 1.4% PE; MAE>=5/10/15/20/30 pt: ST 92.2/85.1/78.5/73.5/65.1, HM 91.8/84.5/78.7/72.9/64.1, WT 86.5/76.7/68.6/62.4/51.8, KB 91.8/84.3/77.9/72.1/64.0, SM 89.8/83.8/77.9/72.9/62.9, PE 92.1/85.4/79.5/74.3/65.6. The cell #5 runs at the initial 50% size (no add) on 9.1% ST / 9.0% HM / 14.7% WT / 9.3% KB / 11.0% SM / 9.2% PE of trades.

## Walk-forward adaptive (monthly refit, trailing 3 months of CLOSED trades, per book re-selection among 1,728 cells + single, applied to entries of that month; OOS from 2024-02)
**B2 (primary)**
| mode | window | n wk | d $/wk | MDE | 95% CI | d maxDD | worst-20 chg ($, base) |
|--|--|--|--|--|--|--|--|
| perbook | Y2026 | 6 | +17498 | 84356 | [-34160, +68518] | -71364 (base 185098) | +71364 (-185098) |
| perbook | L6 | 28 | -13302 | 39710 | [-41185, +12883] | +93755 (base 204132) | +96310 (-389230) |
| perbook | HOLD | 32 | -11015 | 39580 | [-38922, +15910] | -168054 (base 578442) | +282353 (-914949) |
| perbook | PRE | 74 | -19408 | 26089 | [-37224, -2113] | +65586 (base 409229) | +746256 (-1490274) |
| perbook | WF | 106 | -16874 | 21704 | [-32315, -2159] | -103627 (base 578442) | +1028609 (-2405223) |
| pooled | Y2026 | 6 | +14562 | 82090 | [-37676, +65381] | -83988 (base 185098) | +83988 (-185098) |
| pooled | L6 | 28 | -8150 | 35288 | [-32702, +16042] | +125413 (base 204132) | +100569 (-389230) |
| pooled | HOLD | 32 | -11773 | 33839 | [-35921, +11706] | +24196 (base 578442) | +123109 (-914949) |
| pooled | PRE | 74 | -26071 | 24851 | [-43428, -8632] | +2801 (base 409229) | +327086 (-1490274) |
| pooled | WF | 106 | -21755 | 20125 | [-36296, -7816] | +24196 (base 578442) | +450195 (-2405223) |

**B1**
| mode | window | n wk | d $/wk | MDE | 95% CI | d maxDD | worst-20 chg ($, base) |
|--|--|--|--|--|--|--|--|
| perbook | Y2026 | 6 | +5572 | 103691 | [-62781, +69369] | -100450 (base 185098) | +100450 (-185098) |
| perbook | L6 | 28 | -1924 | 38446 | [-28887, +24595] | -86282 (base 204132) | +187591 (-389230) |
| perbook | HOLD | 32 | +2632 | 40215 | [-25472, +30408] | -283183 (base 578442) | +448208 (-914949) |
| perbook | PRE | 74 | -3415 | 30109 | [-24018, +17212] | +275747 (base 409229) | +837426 (-1490274) |
| perbook | WF | 106 | -1590 | 24181 | [-18733, +15391] | +106534 (base 578442) | +1285634 (-2405223) |
| pooled | Y2026 | 6 | +32511 | 84097 | [-22347, +83140] | -66922 (base 185098) | +66922 (-185098) |
| pooled | L6 | 28 | +6283 | 43990 | [-24808, +35485] | +50953 (base 204132) | +105224 (-389230) |
| pooled | HOLD | 32 | +13732 | 44644 | [-18111, +44256] | -323357 (base 578442) | +425746 (-914949) |
| pooled | PRE | 74 | +8527 | 26704 | [-8994, +27627] | +82637 (base 409229) | +784948 (-1490274) |
| pooled | WF | 106 | +10099 | 22895 | [-6117, +26418] | -86577 (base 578442) | +1210694 (-2405223) |

Years (stack weekly sums, perbook / pooled): B2 2024 -707,537 / -933,854, 2025 -1,186,116 / -1,459,528, 2026 +104,986 / +87,375; B1 2024 -1,131,170 / -615,582, 2025 +929,228 / +1,490,962, 2026 +33,431 / +195,067. The adaptive layer does not beat the fixed PRE cell: B2 loses 16.9k (per-book) / 21.8k (pooled) per week over the WF span; B1 pooled is +10.1k/wk [CI -6.1k, +26.4k, MDE 22.9k] with the 2024 year at -616k. The chosen cell jumps between X, stage count, gate, target and stop every month (below), a sign of noise fitting.

**Last re-fit in full (2026-02-01 entries, B2, per book / pooled):**
- perbook ST: cell 1294: 25%/3 st, X=10 pt, absorb, tgt half, stop reb
- perbook HM: cell 854: 33%/2 st, X=20 pt, delta60, tgt half, stop riskcap
- perbook WT: cell 1130: 33%/2 st, X=0.75x stop, nopull_rel, tgt orig, stop riskcap
- perbook KB: cell 824: 33%/2 st, X=20 pt, wall, tgt orig, stop riskcap
- perbook SM: cell 1396: 25%/3 st, X=20 pt, wall, tgt reb, stop reb
- perbook PE: cell 1274: 25%/3 st, X=10 pt, nopull_rel, tgt orig, stop riskcap
- pooled ST: cell 611: 33%/2 st, X=5 pt, wall, tgt half, stop riskcap
- pooled HM: cell 611: 33%/2 st, X=5 pt, wall, tgt half, stop riskcap
- pooled WT: cell 611: 33%/2 st, X=5 pt, wall, tgt half, stop riskcap
- pooled KB: cell 611: 33%/2 st, X=5 pt, wall, tgt half, stop riskcap
- pooled SM: cell 611: 33%/2 st, X=5 pt, wall, tgt half, stop riskcap
- pooled PE: cell 611: 33%/2 st, X=5 pt, wall, tgt half, stop riskcap

**B1 last re-fit:**
- perbook ST: cell 347: 50%/1 st, X=30 pt, delta60, tgt orig, stop riskcap
- perbook HM: cell 509: 50%/1 st, X=0.75x stop, none, tgt orig, stop riskcap
- perbook WT: cell 509: 50%/1 st, X=0.75x stop, none, tgt orig, stop riskcap
- perbook KB: cell 929: 33%/2 st, X=30 pt, absorb, tgt reb, stop riskcap
- perbook SM: cell 1376: 25%/3 st, X=20 pt, none, tgt half, stop riskcap
- perbook PE: cell 311: 50%/1 st, X=30 pt, imb5>=.3, tgt orig, stop riskcap
- pooled ST: cell 509: 50%/1 st, X=0.75x stop, none, tgt orig, stop riskcap
- pooled HM: cell 509: 50%/1 st, X=0.75x stop, none, tgt orig, stop riskcap
- pooled WT: cell 509: 50%/1 st, X=0.75x stop, none, tgt orig, stop riskcap
- pooled KB: cell 509: 50%/1 st, X=0.75x stop, none, tgt orig, stop riskcap
- pooled SM: cell 509: 50%/1 st, X=0.75x stop, none, tgt orig, stop riskcap
- pooled PE: cell 509: 50%/1 st, X=0.75x stop, none, tgt orig, stop riskcap

**Chosen cell per book by quarter, B2 per-book mode (most frequent of the 3 monthly refits; (k/3) when not unanimous)**
| quarter | HM | KB | PE | SM | ST | WT |
|--|--|--|--|--|--|--|
| 2024-Q1 | 33%/2 st, X=0.75x stop, wall, tgt orig, stop riskcap (1/3) | 25%/3 st, X=10 pt, wall, tgt orig, stop riskcap (1/3) | single (1/3) | 33%/2 st, X=15 pt, imb5>=.3, tgt orig, stop reb (1/3) | 33%/2 st, X=20 pt, wall, tgt orig, stop riskcap (1/3) | 25%/3 st, X=10 pt, absorb, tgt reb, stop riskcap (1/3) |
| 2024-Q2 | 50%/1 st, X=15 pt, delta60, tgt half, stop riskcap (1/3) | 33%/2 st, X=10 pt, imb5>=.3, tgt half, stop riskcap (1/3) | 50%/1 st, X=20 pt, nopull_rel, tgt reb, stop orig (1/3) | 50%/1 st, X=30 pt, delta60, tgt reb, stop riskcap (2/3) | 50%/1 st, X=0.75x stop, nopull_rel, tgt orig, stop riskcap (1/3) | 25%/3 st, X=0.25x stop, delta60, tgt reb, stop riskcap (1/3) |
| 2024-Q3 | 25%/3 st, X=5 pt, absorb, tgt reb, stop reb (2/3) | 50%/1 st, X=10 pt, imb5>=.2, tgt reb, stop riskcap (1/3) | 25%/3 st, X=15 pt, none, tgt reb, stop riskcap (1/3) | 33%/2 st, X=0.75x stop, absorb, tgt orig, stop riskcap (1/3) | 50%/1 st, X=5 pt, delta60, tgt orig, stop riskcap (1/3) | 33%/2 st, X=10 pt, none, tgt reb, stop reb (1/3) |
| 2024-Q4 | 50%/1 st, X=10 pt, imb5>=.3, tgt reb, stop riskcap (1/3) | single (1/3) | 50%/1 st, X=20 pt, imb5>=.3, tgt half, stop riskcap (1/3) | 50%/1 st, X=10 pt, imb5>=.2, tgt reb, stop reb (1/3) | 50%/1 st, X=5 pt, delta60, tgt reb, stop riskcap (1/3) | 25%/3 st, X=0.25x stop, none, tgt orig, stop riskcap (2/3) |
| 2025-Q1 | 33%/2 st, X=5 pt, nopull_rel, tgt half, stop reb (1/3) | 50%/1 st, X=20 pt, absorb, tgt half, stop reb (1/3) | 33%/2 st, X=5 pt, nopull_rel, tgt reb, stop riskcap (1/3) | 33%/2 st, X=20 pt, nopull_rel, tgt orig, stop riskcap (2/3) | 50%/1 st, X=10 pt, imb5>=.2, tgt orig, stop reb (1/3) | 50%/1 st, X=20 pt, nopull_rel, tgt orig, stop riskcap (1/3) |
| 2025-Q2 | 25%/3 st, X=0.75x stop, none, tgt reb, stop reb (2/3) | 25%/3 st, X=20 pt, none, tgt orig, stop riskcap (1/3) | 33%/2 st, X=20 pt, absorb, tgt orig, stop riskcap (1/3) | 33%/2 st, X=20 pt, nopull_rel, tgt orig, stop riskcap (1/3) | 25%/3 st, X=0.75x stop, none, tgt reb, stop reb (1/3) | 25%/3 st, X=0.75x stop, wall, tgt orig, stop riskcap (1/3) |
| 2025-Q3 | 25%/3 st, X=10 pt, imb5>=.2, tgt orig, stop reb (1/3) | 33%/2 st, X=20 pt, delta60, tgt orig, stop reb (1/3) | 25%/3 st, X=30 pt, wall, tgt half, stop reb (1/3) | 25%/3 st, X=30 pt, imb5>=.2, tgt orig, stop reb (1/3) | 50%/1 st, X=20 pt, none, tgt half, stop riskcap (1/3) | 25%/3 st, X=30 pt, wall, tgt half, stop reb (2/3) |
| 2025-Q4 | 33%/2 st, X=20 pt, wall, tgt orig, stop riskcap (1/3) | 25%/3 st, X=15 pt, none, tgt orig, stop riskcap (2/3) | 25%/3 st, X=15 pt, imb5>=.2, tgt reb, stop riskcap (1/3) | 33%/2 st, X=5 pt, imb5>=.2, tgt orig, stop reb (2/3) | 33%/2 st, X=5 pt, none, tgt reb, stop reb (2/3) | 25%/3 st, X=0.5x stop, none, tgt orig, stop reb (1/3) |
| 2026-Q1 | 33%/2 st, X=5 pt, imb5>=.2, tgt orig, stop riskcap (1/3) | 33%/2 st, X=0.75x stop, delta60, tgt orig, stop riskcap (1/3) | 25%/3 st, X=10 pt, nopull_rel, tgt orig, stop riskcap (2/3) | 25%/3 st, X=30 pt, absorb, tgt reb, stop reb (1/3) | 25%/3 st, X=5 pt, absorb, tgt reb, stop reb (1/3) | 33%/2 st, X=0.75x stop, nopull_rel, tgt orig, stop riskcap (2/3) |

**B1**
| quarter | HM | KB | PE | SM | ST | WT |
|--|--|--|--|--|--|--|
| 2024-Q1 | 50%/1 st, X=0.75x stop, imb5>=.3, tgt orig, stop riskcap (1/3) | 25%/3 st, X=10 pt, wall, tgt orig, stop riskcap (1/3) | single (1/3) | 33%/2 st, X=15 pt, imb5>=.3, tgt orig, stop reb (1/3) | 25%/3 st, X=20 pt, none, tgt orig, stop riskcap (1/3) | 50%/1 st, X=0.5x stop, imb5>=.2, tgt reb, stop riskcap (1/3) |
| 2024-Q2 | 50%/1 st, X=15 pt, delta60, tgt half, stop riskcap (1/3) | 33%/2 st, X=5 pt, none, tgt orig, stop riskcap (1/3) | 50%/1 st, X=20 pt, nopull_rel, tgt reb, stop riskcap (1/3) | 50%/1 st, X=30 pt, delta60, tgt reb, stop riskcap (2/3) | 50%/1 st, X=0.75x stop, imb5>=.2, tgt orig, stop riskcap (1/3) | 25%/3 st, X=0.25x stop, delta60, tgt reb, stop riskcap (1/3) |
| 2024-Q3 | 25%/3 st, X=5 pt, absorb, tgt reb, stop reb (2/3) | 50%/1 st, X=10 pt, imb5>=.2, tgt reb, stop riskcap (1/3) | 25%/3 st, X=15 pt, none, tgt reb, stop riskcap (1/3) | 33%/2 st, X=0.75x stop, absorb, tgt orig, stop riskcap (1/3) | 50%/1 st, X=5 pt, delta60, tgt orig, stop riskcap (1/3) | 33%/2 st, X=15 pt, imb5>=.2, tgt orig, stop riskcap (1/3) |
| 2024-Q4 | 50%/1 st, X=10 pt, imb5>=.3, tgt reb, stop riskcap (1/3) | single (1/3) | 50%/1 st, X=20 pt, imb5>=.3, tgt half, stop riskcap (1/3) | 50%/1 st, X=10 pt, imb5>=.2, tgt reb, stop reb (2/3) | 33%/2 st, X=20 pt, none, tgt orig, stop riskcap (1/3) | 25%/3 st, X=0.25x stop, none, tgt orig, stop riskcap (1/3) |
| 2025-Q1 | 33%/2 st, X=5 pt, nopull_rel, tgt half, stop reb (1/3) | 50%/1 st, X=0.75x stop, none, tgt half, stop riskcap (1/3) | 33%/2 st, X=5 pt, nopull_rel, tgt reb, stop riskcap (1/3) | 33%/2 st, X=20 pt, nopull_rel, tgt orig, stop riskcap (2/3) | 50%/1 st, X=10 pt, imb5>=.2, tgt orig, stop reb (1/3) | 25%/3 st, X=15 pt, imb5>=.2, tgt orig, stop riskcap (2/3) |
| 2025-Q2 | 25%/3 st, X=0.75x stop, none, tgt reb, stop reb (1/3) | 25%/3 st, X=20 pt, none, tgt orig, stop riskcap | 25%/3 st, X=20 pt, none, tgt orig, stop riskcap (2/3) | 25%/3 st, X=20 pt, none, tgt orig, stop riskcap (1/3) | 33%/2 st, X=30 pt, none, tgt orig, stop riskcap (2/3) | 25%/3 st, X=0.5x stop, none, tgt orig, stop riskcap |
| 2025-Q3 | 25%/3 st, X=20 pt, none, tgt reb, stop riskcap (2/3) | 25%/3 st, X=20 pt, none, tgt reb, stop riskcap (1/3) | 50%/1 st, X=30 pt, none, tgt reb, stop riskcap (2/3) | 50%/1 st, X=0.75x stop, imb5>=.2, tgt orig, stop riskcap (2/3) | 33%/2 st, X=30 pt, imb5>=.2, tgt orig, stop riskcap (1/3) | 25%/3 st, X=0.5x stop, none, tgt orig, stop riskcap (1/3) |
| 2025-Q4 | 50%/1 st, X=0.75x stop, none, tgt orig, stop riskcap (2/3) | 25%/3 st, X=15 pt, none, tgt orig, stop riskcap (2/3) | 25%/3 st, X=15 pt, absorb, tgt orig, stop riskcap (2/3) | 33%/2 st, X=5 pt, imb5>=.2, tgt orig, stop reb (2/3) | 50%/1 st, X=5 pt, none, tgt reb, stop reb (1/3) | 25%/3 st, X=5 pt, imb5>=.3, tgt reb, stop riskcap (1/3) |
| 2026-Q1 | 50%/1 st, X=0.75x stop, imb5>=.2, tgt orig, stop riskcap (1/3) | 50%/1 st, X=0.75x stop, delta60, tgt orig, stop riskcap (1/3) | 50%/1 st, X=30 pt, imb5>=.3, tgt orig, stop riskcap (2/3) | 25%/3 st, X=20 pt, none, tgt half, stop riskcap (2/3) | 33%/2 st, X=20 pt, imb5>=.2, tgt orig, stop riskcap (1/3) | 50%/1 st, X=0.75x stop, none, tgt orig, stop riskcap (2/3) |

Full monthly tables: `wf_assign_B2.csv`, `wf_assign_B1.csv`; stats `wf_stats_B2.csv`, `wf_stats_B1.csv`. The latest trailing-3-month best cells (as of 2026-02-06, in-sample for that window, NOT out of sample) are in `policy_add_refit_20260206.txt` (ST absorption 3 stages X=10; HM delta60 X=20; WT delta60 X=0.75 stop; KB wall X=20; SM imb5>=0.2 X=5; PE wall X=20, B2).

## Placebos (B2; 200 draws unless stated; rank = share of placebo window means below the actual)
| set / cell | P1 random-timing PRE / HOLD (placebo mean) | P2 shuffled-book PRE / HOLD (placebo mean) |
|--|--|--|
| WT #221 (no gate) | 0.27 / 0.82 (+6,499 / +3,070 vs actual +6,494 / +3,069) | 0.985 / 0.59 (+3,760 / +2,315) |
| SM #842 (no-pull rel) | 0.975 / 0.99 (-386 / -394) | 0.99 / 0.90 (-1,418 / +166) |
| STACK #5 (no gate, 100 draws) | 0.31 / 0.39 (+6,399 / +5,924) | 0.98 / 0.69 (-4,353 / -353) |
| D_MV #365 (no gate) | 0.45 / 0.32 (+5,486 / +8,507) | 0.935 / 0.87 (+927 / +4,892) |
Ungated cells: P1 equals the real cell (q=0.999) so G4 cannot be met, i.e. the benefit is the add geometry, not timing. Only the gated SM cell beats both placebos in both windows, but it is DEAD on tail/years/X'.

## Fill basis and costs (stated)
Each add is a MARKET order decided at the end of the trigger second (gate features have ts<=s+1) and filled at that second's close +1 tick adverse (V0, FEES.md fill basis; a resting limit at the level would fill better but has no queue model here). Costs: add tick 0.25 pt; exits stop 1.01 / time 0.995 / target year correction 1.4/1.5/4.2/4.3 pt (B2) or the stack P9-mapped correction (B1); commission $4.84 RT per contract per fill (0.242 pt per lot, on each add, via the lock engine's COMM); size-dependent sweep cost (equal_risk.excess) per order. The target correction is a fixed shortfall per target exit, so a rebased (nearer) target pays the same 4.2-4.3 pt on a smaller payoff in 2025-26 (it is the worst target mode in every basis).

## Method summary
Existing entries: 27,895 live-stack engine rows (ST 5,070, HM 4,008, WT 7,130, KB 5,236, SM 1,574, PE 4,877; label days <= 2026-02-06 after the live WINMASK; the prereg's 41,854 counted the same books before the date cut) through a copy of `sl_lib.run_book` (entry test on the parent; adds as child rows that follow the parent; day give-back arm and week floor flatten the whole position and cancel adds after the lock second; the copy reproduces `run_book` exactly: ST 1,931,297.70 over all rows) and 14,585 trade-index rows (PB, DN, MV, MA) at trade level. The 1-s sim reproduces the engine exit type for 99.99% of rows. Grid 3 sizings (50%/1, 33%/2, 25%/3) x 8 X (5/10/15/20/30 pt, 0.25/0.5/0.75 stop from the AVERAGE) x 8 gates (none, imb5>=0.2, imb5>=0.3, near-wall >= 2x trailing median, no-pull strict, no-pull relative, delta60>0, absorption >= 2x trailing median) x 3 targets (rebased, original, average+half) x 3 stops (original lot-matched, rebased lot-matched, risk-matched up to 2.0x live at the original stop) = 1,728 cells x 11 sets x 3 bases. Gate details and limits: the wall gate is the NEAR wall (8 ticks behind price vs its own trailing same-hour median) because mbp-10 does not show the stop 40-240 ticks away; 'no pulled size' is nearly never exactly zero so a relative version (<= trailing p25) is a second gate; a failed gate keeps the stage armed for 60 s. Stack deltas are added to the official audit weekly base (46,785/wk).
Limits: the stack-level numbers use the engine P&L of the same rows on the same basis for baseline and cell (paired), not the official P9 per-trade values; gate bits are available for 100% of dips of rows with a trade-index twin and for other rows through the (second, side) pool (bits identical across trades, 0 conflicts); D6 session/IF/CRT/TB4/E1A legs have no 1-s row set and are not covered; CR is not applicable.

## Files
Policy candidate (NOT for live; verdict DEAD): `l2vast/ds3/out/adduw/policy_add_candidate.txt` (written because stack cell #5 and WT #221 are >= 0 in HOLD and X' on B2); latest trailing-3-month cells `policy_add_refit_20260206.txt`; single-command nightly re-fit `l2vast/ds3/code/adduw/adduw_refit.sh` (gates -> pool -> 1,728-cell grid on 5 workers -> trailing-3-month re-selection -> policy lines; needs current ldp1s tables). MAEMFE sanity: no-gate first-add rates equal MAEMFE P(target | MAE>=X) (ST PRE 0.463/0.419/0.374/0.333/0.255 for X=5/10/15/20/30).
