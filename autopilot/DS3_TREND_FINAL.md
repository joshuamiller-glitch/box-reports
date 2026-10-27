# DS3 TREND FINAL (TL) - PROVISIONAL until direct L2 replay
Written 2026-10-27T01:21Z. Basis: MAPPED for every cell (direct L2 replays for TR1/TR2 are held by the replay governor; TL started none). Nothing submitted to T-BRACKET-PM. No live recommendation.

## Verdict line
Trend: 12 PASS, 18 CANDIDATE. Best entry: TR3_KB20_S, paired vs ST +6.71 pts/trade [4.41,9.18], 28.7 trades/wk. Best exit on ST's own entries: none yet, paired n/a pts/trade . DS3 marginal Sharpe +0.56.

Counts exclude duplicates (34 queued lines = 30 distinct cells). Best exit: D3XT rows (DS3_TC1C2/TC3C4/TC5) do not exist yet (0/104 scored at the last progress line), so the exit half of the verdict line is open.

## What the trend tracks produced
- TR1 (R1,R6): 134 cells: 2 PASS, 6 CANDIDATE, 125 DEAD, 1 REPORT-ONLY. TR2 (R2,R3 + widening): 74 cells: 12 PASS, 14 CANDIDATE, 48 DEAD. TR4 (R5,R7): 58 cells, all DEAD (no cell with a positive paired CI; no direct replay). D3XT (R4): not scored. Trend cells scored: 266; ledger total across all tracks 43,190.
- Best-of-N: of 266 trend cells, 19 have a paired-vs-ST CI lower bound > 0, versus about 6.7 expected by chance (one-sided 2.5%). Placebo rank >= 0.95 in 50 of 231 cells (chance about 12). The placebo ranks 1.00 on nearly every PASS, so it does not discriminate in this family; do not read it as parameter-specific evidence.
- Most PASS cells are standalone-book PASSes (about 20-30 trades/wk) that are WORSE than ST per trade on the same days (paired vs ST negative, CI excluding 0 for most). Per the user order, no cell is DEAD solely for earning less than ST at equal lots. Re-verdict check: no DEAD cell in TR1/TR2 lists a vs-ST criterion among its failed gates (failures are WF_CI, HOLD, SPAN2, placebo, x2-cost, PRE), so 0 cells were re-verdicted. The equal-risk comparison is in the table (dEqRisk = $/wk at ST10's weekly SD minus ST10's $/wk).
- Only TR3_KB20_S (stop-entry KB20) and the Keltner n20/n30 RT15 cells beat ST per trade with a CI above 0 (KB20_S +6.71 pts [4.41,9.18]). KB20_S has a negative 2023 span (-4.5k/wk).

## Duplicates (not separate cells)
TR1B_reg1m_n60_t3_r0.5 = t2 (identical daily series). TRW_DON15m_n20_S = TR3_DON15_S (identical). TRW_kelt3m_n14_m1.0_RT15 = TR3_KB_RT15 (identical). TR2_KB_plain = the T-ENTRY KB book (TE7_kelt3m_n14_m1.0) plain, per the lead. TR1F ST k4 = k5 per the lead (not in the queue). Within TR2 the Keltner/Donchian stop-entry and retest variants are one family (KB RT5 correlates 0.50 with TE7 KB), so treat them as one mechanism with parameter variants, not 20 independent books.

## R8 robustness on the MAPPED basis (code l2vast/ds3/code/tl_r8.py, results l2vast/ds3/out/TL_R8.json)
Done: equal-risk and capacity (D3BL equal_risk, sweep cost), cost 1x/1.5x/2x ($250 per round trip at 10 lots), by-year (WF window), VIX tercile (prior-day VIXCLS terciles over WF), day-block bootstrap of maxDD (1000 iid day draws), same-group neighbours, correlations (in the rows' corr_* fields). DS3 marginal Sharpe and peak lots against the 50 cap are the owner agents' own mapped mix lines; TL did NOT call ds3_addbook, so no extra holdout look.
NOT done (needs the direct stage): fill-model and latency (trade-through/queue/touch, 5/50/150 ms), interval-replay peak lots, a true counter-trend mirror re-simulation, holding time (trade tables carry entry time and exit bar index only), D3X identity tests and specs. The mapped mirror (-net - 2 x cost per trade) is near-tautological for a symmetric bracket, so it is NOT the required mirror test; every cell is mirror-UNTESTED.

Columns: WF $/wk at 10 lots; equal-risk lots (ST10 weekly SD); $/wk at equal risk; dEqRisk vs ST10; capacity (lots where the mean hits 0; none<300 = never within 300); $/wk at cost 1.5x and 2x; WF by-year sums in $k (2023/2024/2025+); VIX tercile low/mid/high $/wk; maxDD observed / day-bootstrap p95 ($k); 2023-span $/wk; duplicate.

| cell | verdict | trigger | exec | tr/wk | WF $/wk | vs ST pts [CI] | eq-lots $/wk | eq-risk lots | eq-risk $/wk | dEqRisk | capacity | cost 1.5x | cost 2x | by-year $k | VIX L/M/H | maxDD obs / p95 k | 2023 span | dup |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TR1A_ens_s0.5_k4 | CANDIDATE | {"lbs": [15, 30, 60, 120, 24 | DELIVERABLE | 29.6 | 18113 | -2.87 [-5.09,-0.81] | 17950 | 9.6 | 17300 | +2950 | 118 | 14248 | 10547 | 867/418/1264 | 23091/5553/25769 | 310 / 599 | -6843 |  |
| TR1A_ens_s1.0_k3 | PASS | {"lbs": [15, 30, 60, 120, 24 | DELIVERABLE | 28.7 | 12148 | -5.19 [-7.93,-2.36] | 11942 | 10.4 | 12443 | -1907 | 79 | 8357 | 4773 | 449/714/533 | 14631/1545/20008 | 384 / 745 | 2389 |  |
| TR1B_reg1m_n60_t2_r0.5 | CANDIDATE | {"k": 1, "n": 60, "T": 2, "r | DELIVERABLE | 27.4 | 12107 | 1.35 [-2.44,4.52] | 12331 | 10.9 | 13462 | -888 | 86 | 8905 | 5479 | 857/-59/953 | 20341/4935/12094 | 613 / 708 | -6551 |  |
| TR1B_reg1m_n60_t3_r0.5 | CANDIDATE | {"k": 1, "n": 60, "T": 3, "r | DELIVERABLE | 27.4 | 12107 | 1.35 [-2.44,4.52] | 12331 | 10.9 | 13462 | -888 | 86 | 8905 | 5479 | 857/-59/953 | 20341/4935/12094 | 613 / 668 | -6551 | TR1B_reg1m_n60_t2_r0.5 |
| TR1C_MAMA_10m_flip | PASS | {"name": "MAMA", "k": 10, "m | DELIVERABLE | 15.1 | 8760 | 3.67 [-1.08,8.72] | 9458 | 13.0 | 12334 | -2016 | 123 | 7576 | 5694 | 517/449/377 | 11553/6716/10437 | 292 / 529 | 4607 |  |
| TR1D_HP_10m_slope | CANDIDATE | {"name": "HP", "k": 10, "mod | DELIVERABLE | 16.9 | 5084 | 3.85 [-1.06,9.00] | 5280 | 12.0 | 6319 | -8031 | 58 | 3175 | 1070 | 450/388/-87 | 10288/6120/-379 | 354 / 756 | 1696 |  |
| TR1E_retest_15m_c3 | CANDIDATE | {"k": 15, "s": 3, "mode": 1} | DELIVERABLE | 3.3 | 1595 | -1.84 [-7.45,3.81] | 1610 | 28.4 | 3238 | -11112 | 94 | 1199 | 789 | 63/100/66 | -390/6050/-722 | 114 / 380 | 1864 |  |
| TR1F_vote_TSM_k3 | CANDIDATE | {"kind": "TSM", "k": 3, "siz | DELIVERABLE | 23.5 | 8052 | -1.10 [-4.74,2.77] | 7756 | 11.7 | 9108 | -5242 | 61 | 4820 | 1884 | 37/742/323 | 11959/2861/8686 | 411 / 774 | 30 |  |
| TR2_KB_plain | PASS | KB/M | DELIVERABLE-bars/ticks | 29.5 | 16232 | -5.76 [-8.37,-3.18] | 16202 | 9.7 | 15662 | +1312 | 106 | 12516 | 8830 | 770/1042/489 | 22306/426/26336 | 378 / 641 | 176 | T-ENTRY KB (TE7_kelt3m_n14_m1.0) plain |
| TR2_KB_NR4 | PASS | KB/M | DELIVERABLE-bars/ticks | 22.1 | 11801 | -5.84 [-9.72,-1.87] | 12404 | 10.3 | 12804 | -1546 | 109 | 9647 | 6890 | 629/711/421 | 12433/13436/11829 | 305 / 563 | 5530 |  |
| TR2_DON15_LV2 | PASS | DON15/M | DELIVERABLE-bars/ticks | 3.4 | 3245 | -5.24 [-13.89,3.51] | 3034 | 29.0 | 7356 | -6994 | 179 | 2613 | 2192 | 261/65/105 | 6436/259/2486 | 104 / 301 | 3537 |  |
| TR3_KB_S | CANDIDATE | KB/S | DELIVERABLE-bars/ticks | 29.9 | 21094 | 3.08 [0.57,5.34] | 21166 | 9.7 | 20525 | +6175 | 139 | 17431 | 13696 | 903/1177/925 | 25723/8251/30207 | 287 / 534 | -3780 |  |
| TR3_KB_RT5 | PASS | KB/RT5 | DELIVERABLE-bars/ticks | 28.4 | 11378 | 0.58 [-1.90,3.25] | 11369 | 10.1 | 11519 | -2831 | 76 | 7823 | 4277 | 791/804/20 | 19299/-7184/22236 | 446 / 725 | 2783 |  |
| TR3_KB_RT15 | PASS | KB/RT15 | DELIVERABLE-bars/ticks | 29.7 | 9890 | 1.47 [-1.03,3.92] | 9743 | 9.6 | 9351 | -4999 | 61 | 6034 | 2324 | 550/671/162 | 17496/-6190/18129 | 503 / 856 | 2126 |  |
| TR3_KB_RTH5 | CANDIDATE | KB/RTH5 | DELIVERABLE-bars/ticks | 27.0 | 7671 | -3.83 [-6.64,-0.95] | 7543 | 10.3 | 7781 | -6569 | 51 | 4191 | 839 | 857/228/-14 | 21967/-9964/10704 | 620 / 826 | 7237 |  |
| TR3_KB_PART | CANDIDATE | KB/PART | DELIVERABLE-bars/ticks | 59.3 | 13061 | -5.09 [-7.50,-2.72] | 12973 | 11.1 | 14364 | +14 | 40 | 5577 | -1818 | 660/857/326 | 19901/-2882/22232 | 372 / 587 | 1151 |  |
| TR3_KB_REST | CANDIDATE | KB/REST | DELIVERABLE-bars/ticks | 27.8 | 14841 | -4.02 [-6.66,-1.57] | 14437 | 10.2 | 14661 | +311 | 100 | 10972 | 7506 | 282/1052/716 | 7849/16013/20047 | 327 / 624 | 4702 |  |
| TR3_DON15_S | PASS | DON15/S | DELIVERABLE-bars/ticks | 21.3 | 20063 | -8.23 [-11.84,-4.76] | 20196 | 10.8 | 21718 | +7368 | 189 | 17538 | 14879 | 866/889/1113 | 16987/19999/24391 | 219 / 455 | 4729 |  |
| TR3_DON15_RTH15 | CANDIDATE | DON15/RTH15 | DELIVERABLE-bars/ticks | 11.8 | 5102 | 2.23 [-2.64,7.01] | 4899 | 14.6 | 7044 | -7306 | 79 | 3426 | 1952 | 391/121/183 | 9047/-1210/6980 | 275 / 612 | 15 |  |
| TR3_KB20_M | CANDIDATE | KB20/M | DELIVERABLE-bars/ticks | 28.6 | 17501 | -3.10 [-5.59,-0.27] | 17712 | 9.9 | 17571 | +3221 | 121 | 14137 | 10562 | 1010/771/733 | 17122/15727/20952 | 295 / 555 | -7874 |  |
| TR3_KB20_S | CANDIDATE | KB20/S | DELIVERABLE-bars/ticks | 28.7 | 22958 | 6.71 [4.41,9.18] | 22799 | 9.3 | 21291 | +6941 | 157 | 19217 | 15634 | 1662/461/1114 | 31256/7090/30758 | 282 / 492 | -4539 |  |
| TRW_DON10m_n14_S | CANDIDATE | DONG_10_14/S | DELIVERABLE-bars/ticks | 25.2 | 13402 | -4.87 [-7.83,-1.75] | 13615 | 10.7 | 14595 | +245 | 104 | 10463 | 7311 | 489/327/1118 | 18216/5670/17396 | 358 / 622 | -1815 |  |
| TRW_DON15m_n14_S | CANDIDATE | DONG_15_14/S | DELIVERABLE-bars/ticks | 23.0 | 19137 | -6.33 [-9.75,-2.75] | 19657 | 9.9 | 19425 | +5075 | 170 | 16789 | 13921 | 814/858/1120 | 16591/19052/24091 | 299 / 450 | -6792 |  |
| TRW_DON30m_n14_S | PASS | DONG_30_14/S | DELIVERABLE-bars/ticks | 18.5 | 10643 | -2.79 [-6.82,1.68] | 10653 | 11.1 | 11852 | -2498 | 113 | 8355 | 6058 | 635/427/450 | 4654/6813/20895 | 295 / 603 | 3676 |  |
| TRW_DON10m_n20_S | CANDIDATE | DONG_10_20/S | DELIVERABLE-bars/ticks | 24.0 | 16976 | -5.65 [-8.48,-2.61] | 17215 | 9.6 | 16531 | +2181 | 141 | 14212 | 11210 | 662/671/1112 | 18404/7673/26143 | 327 / 519 | -3109 |  |
| TRW_DON15m_n20_S | PASS | DONG_15_20/S | DELIVERABLE-bars/ticks | 21.3 | 20063 | -8.23 [-11.84,-4.76] | 20196 | 10.8 | 21718 | +7368 | 189 | 17538 | 14879 | 866/889/1113 | 16987/19999/24391 | 219 / 441 | 4729 | TR3_DON15_S |
| TRW_DON30m_n20_S | PASS | DONG_30_20/S | DELIVERABLE-bars/ticks | 17.3 | 9928 | -6.12 [-10.33,-1.61] | 10009 | 11.5 | 11515 | -2835 | 112 | 7848 | 5687 | 489/667/266 | 2485/8239/19707 | 276 / 592 | 4454 |  |
| TRW_DON10m_n30_S | PASS | DONG_10_30/S | DELIVERABLE-bars/ticks | 22.3 | 19570 | -7.31 [-10.74,-4.00] | 19201 | 10.6 | 20368 | +6018 | 171 | 16415 | 13629 | 765/762/1200 | 16483/11293/30509 | 264 / 477 | 8089 |  |
| TRW_DON15m_n30_S | PASS | DONG_15_30/S | DELIVERABLE-bars/ticks | 20.1 | 12503 | -6.94 [-11.15,-2.87] | 12839 | 10.6 | 13662 | -688 | 125 | 10327 | 7816 | 823/501/499 | 14467/6943/17543 | 308 / 566 | 1758 |  |
| TRW_DON30m_n30_S | PASS | DONG_30_30/S | DELIVERABLE-bars/ticks | 15.2 | 9427 | -3.06 [-7.49,2.01] | 9109 | 13.6 | 12422 | -1928 | 117 | 7216 | 5322 | 427/668/198 | 8306/5309/14034 | 206 / 538 | 3990 |  |
| TRW_kelt3m_n14_m1.0_RT15 | CANDIDATE | KBG_14_1.0/RT15 | DELIVERABLE-bars/ticks | 29.7 | 9890 | 1.47 [-1.03,3.92] | 9743 | 9.6 | 9351 | -4999 | 61 | 6034 | 2324 | 550/671/162 | 17496/-6190/18129 | 503 / 859 | 2126 | TR3_KB_RT15 |
| TRW_kelt3m_n14_m2.0_RT15 | CANDIDATE | KBG_14_2.0/RT15 | DELIVERABLE-bars/ticks | 22.4 | 9714 | -5.94 [-9.81,-2.10] | 9494 | 12.1 | 11441 | -2909 | 80 | 6692 | 3890 | 497/228/623 | 15675/4782/8323 | 497 / 667 | 482 |  |
| TRW_kelt3m_n20_m1.0_RT15 | CANDIDATE | KBG_20_1.0/RT15 | DELIVERABLE-bars/ticks | 27.9 | 11375 | 5.30 [2.59,8.18] | 11507 | 10.2 | 11758 | -2592 | 78 | 8018 | 4529 | 563/479/593 | 17200/8908/8808 | 342 / 702 | -9860 |  |
| TRW_kelt3m_n30_m1.0_RT15 | CANDIDATE | KBG_30_1.0/RT15 | DELIVERABLE-bars/ticks | 26.8 | 12414 | 4.34 [1.40,7.30] | 12508 | 10.8 | 13536 | -814 | 90 | 9168 | 5829 | 152/973/651 | 12509/17244/8293 | 361 / 624 | -8496 |  |

## Survivors for the lead (mapped basis; need direct replay)
Strict screen (non-duplicate; dEqRisk > 0; 2x-cost > 0; 2023 span > 0; holdout > 0; every WF year > 0; positive in every VIX tercile; DS3 marginal Sharpe WF >= 0):
1. TR3_DON15_S (== TRW_DON15m_n20_S): Donchian 15-min n=20 stop-entry. 21 trades/wk, WF $20.1k/wk, equal-risk $21.7k/wk (+$7.4k vs ST10), holdout +$22.7k/wk, DS3 marginal Sharpe WF +0.48, maxDD 219k (bootstrap p95 441k), paired vs ST -8.23 pts/trade [-11.8,-4.8] (worse per trade, wins on frequency).
2. TRW_DON10m_n30_S: Donchian 10-min n=30 stop-entry. 22 trades/wk, $19.2k/wk, equal-risk +$6.0k vs ST10, holdout +$22.5k/wk, paired vs ST -7.31 [-10.7,-4.0].
3. TR3_KB_REST: Keltner base, style REST. 28 trades/wk, $14.4k/wk, equal-risk +$0.3k vs ST (marginal), DS3 marginal Sharpe +0.10.
Near-survivors failing only the 2023-span gate: TR3_KB20_S (best per-trade edge, +6.71 pts [4.41,9.18]; $22.8k/wk; dEqRisk +$6.9k; marginal Sharpe +0.56; negative in the never-scored 2023 span), TR3_KB_S (+3.08 pts, marginal +0.42), TR3_KB20_M, TR1A_ens_s0.5_k4 (marginal +0.26, dEqRisk +$3.0k), TRW_DON15m_n14_S, TRW_DON10m_n14_S, TRW_DON10m_n20_S.
TR1 momentum/MAMA/HP/regression cells all fail equal risk except TR1A_ens_s0.5_k4; none survive the strict screen.
Stop-entry cells (suffix S) depend on a fill rule (ATI stop order, trade-through), which is an execution-server question and untested here.

## Caveats
The earlier FIRM direct replay showed the mapped basis overstating the mean by 4-7k/wk and understating maxDD by 115-245k, so every dollar above is an upper bound until direct. The breakouts are a correlated family, so the PASS count overstates independent evidence. D3X specs and identity tests should be requested for the survivors after direct. paper_all registration is owned by the agents; TL did not register.
