# BACKLOG_BOOTSTRAP (V2 sec 7 item 1; BK3, 2026-10-24)

Research only. Scope: every PASS and CANDIDATE row of the verdict of record (`lb2.load()` = rows/*.json + NM re-score + T3.10b robustness overlay; 18 PASS + 26 CANDIDATE = 44 rows; T4.2_Y4 is DEAD in that load and excluded; note the on-disk LEADERBOARD.md written 18:38Z still lists it as PASS, a stale line to be fixed by the LEAD). Code `l2vast/struct48/code/bk3_boot.py`; raw numbers `l2vast/struct48/out/BK3_bootstrap.json`.
Method: for each row the weekly WF difference vector is rebuilt from the stored series (sleeves: Set A + k x sleeve at the row's tested size, weekly difference = k x sleeve; NM-B: candidate minus benchmark series from out/NM_B/series.npz; COMB_c3_R from the 3-lot-capped scaled daily file), and **the original interval is reproduced to the cent before anything new is drawn: 44 of 44 rows match exactly** (1,000-draw iid-week seed 9 for T3/NM-E rows; NM-B rows used a 2,000-draw 8-week circular block bootstrap, seed 21, which is also reproduced exactly). Then 10,000 draws with the same resampling scheme and seed (seeds 101 and 2026 repeated to show Monte Carlo spread). The verdict is re-stated with `lb2.verdict_of` = `s48score.verdict` + the same overlays.

## Result

- Verdicts: 44 of 44 unchanged (26 CANDIDATE stay CANDIDATE, 18 PASS stay PASS). CI "excludes 0" status: 22 rows before, 22 rows after, no row flips at the seed of record.
- Why no change is possible for 34 of the 44 rows: the sleeve criterion in `s48score.verdict` (standalone holdout > 0, marginal Sharpe up, corr <= 0.5) does not use the CI; only the sizing/lock rows (10 NM-B cells) use it (branch b: mean up with CI > 0 and maxDD not worse; branch a: SD or maxDD down with CI).
- **Boundary rows (CI endpoint within Monte Carlo error of 0):** B01_SetB lower bound -84 / -147 / +117 across three seeds (block CI of the mean difference; iid-week 10k CI is [+1,032, +15,588], excludes 0); ORB_ASIA_30_v1__s60 at 0.25/0.5/1.0 lower bound -39 / +20 / +106 (x2 and x4 at the larger sizes). These endpoints sit at zero for the data we have; 10,000 draws do not resolve them (endpoint Monte Carlo error 100-500 dollars/wk; max |seed A - seed B| over rows 505 lower, 358 upper). Set B's CANDIDATE vs PASS status depends on the resampling scheme (8-week block = CANDIDATE, iid weeks = would meet branch b), not on the draw count.
- Detectable effect (80% power, 2.80 x SE of the mean difference from the 10k draws) is in the MDE column; every row whose effect is below its MDE is a result that "could not have seen less than" that value.

| track | cell | object | effect $/wk | old CI (draws) | 10k CI (seed of record) | 10k lower, seeds 2/3 | CI excl 0 old -> new | MDE $/wk | SD diff CI / maxDD diff CI (10k, NM-B) | verdict old -> new |
|---|---|---|---|---|---|---|---|---|---|---|
| T3.2 | ORB_ASIA_15_v1__s60@0.25 | sleeve | 4,069 | [388, 8,197] (1,000 iid) | [189, 8,064] | 297 / 158 | Y -> Y | 5,603 |  | PASS -> PASS |
| T3.2 | ORB_ASIA_15_v1__s60@0.5 | sleeve | 8,138 | [776, 16,394] (1,000 iid) | [378, 16,127] | 594 / 316 | Y -> Y | 11,206 |  | PASS -> PASS |
| T3.2 | ORB_ASIA_15_v1__s60@1.0 | sleeve | 16,276 | [1,553, 32,788] (1,000 iid) | [756, 32,254] | 1,188 / 632 | Y -> Y | 22,412 |  | PASS -> PASS |
| T3.2 | ORB_ASIA_15_v1__s75@0.25 | sleeve | 3,864 | [232, 7,528] (1,000 iid) | [167, 7,540] | 223 / 187 | Y -> Y | 5,307 |  | PASS -> PASS |
| T3.2 | ORB_ASIA_15_v1__s75@0.5 | sleeve | 7,727 | [463, 15,057] (1,000 iid) | [334, 15,080] | 446 / 375 | Y -> Y | 10,615 |  | PASS -> PASS |
| T3.2 | ORB_ASIA_15_v1__s75@1.0 | sleeve | 15,455 | [926, 30,113] (1,000 iid) | [667, 30,160] | 893 / 750 | Y -> Y | 21,229 |  | PASS -> PASS |
| T3.2 | ORB_ASIA_30_v1__s50@0.25 | sleeve | 2,867 | [-1,043, 6,843] (1,000 iid) | [-1,089, 6,907] | -1,026 / -982 | N -> N | 5,719 |  | CANDIDATE -> CANDIDATE |
| T3.2 | ORB_ASIA_30_v1__s50@0.5 | sleeve | 5,734 | [-2,085, 13,685] (1,000 iid) | [-2,177, 13,814] | -2,053 / -1,964 | N -> N | 11,437 |  | CANDIDATE -> CANDIDATE |
| T3.2 | ORB_ASIA_30_v1__s50@1.0 | sleeve | 11,468 | [-4,170, 27,370] (1,000 iid) | [-4,355, 27,629] | -4,106 / -3,927 | N -> N | 22,875 |  | CANDIDATE -> CANDIDATE |
| T3.2 | ORB_ASIA_30_v1__s60@0.25 | sleeve | 4,001 | [-116, 8,116] (1,000 iid) | [-39, 8,099] | 20 / 106 | N -> N | 5,815 |  | CANDIDATE -> CANDIDATE |
| T3.2 | ORB_ASIA_30_v1__s60@0.5 | sleeve | 8,001 | [-232, 16,232] (1,000 iid) | [-78, 16,198] | 39 / 213 | N -> N | 11,629 |  | CANDIDATE -> CANDIDATE |
| T3.2 | ORB_ASIA_30_v1__s60@1.0 | sleeve | 16,003 | [-464, 32,465] (1,000 iid) | [-156, 32,397] | 78 / 426 | N -> N | 23,258 |  | CANDIDATE -> CANDIDATE |
| T3.2 | ORB_ASIA_30_v1__s75@0.25 | sleeve | 3,598 | [-515, 7,694] (1,000 iid) | [-352, 7,590] | -226 / -366 | N -> N | 5,662 |  | CANDIDATE -> CANDIDATE |
| T3.2 | ORB_ASIA_30_v1__s75@0.5 | sleeve | 7,195 | [-1,030, 15,388] (1,000 iid) | [-704, 15,180] | -451 / -732 | N -> N | 11,324 |  | CANDIDATE -> CANDIDATE |
| T3.2 | ORB_ASIA_30_v1__s75@1.0 | sleeve | 14,390 | [-2,059, 30,776] (1,000 iid) | [-1,407, 30,360] | -902 / -1,464 | N -> N | 22,647 |  | CANDIDATE -> CANDIDATE |
| T3.6b1 | RSI2_t10 | sleeve | 10,197 | [1,961, 20,243] (1,000 iid) | [2,047, 19,237] | 1,973 / 1,951 | Y -> Y | 12,287 |  | PASS -> PASS |
| T3.6b1 | RSI2T_t10 | sleeve | 8,882 | [1,096, 19,045] (1,000 iid) | [668, 17,864] | 619 / 692 | Y -> Y | 12,287 |  | CANDIDATE -> CANDIDATE |
| T3.7b4 | IBS_t20_n1 | sleeve | 8,465 | [420, 18,131] (1,000 iid) | [307, 17,209] | 187 / 379 | Y -> Y | 12,287 |  | CANDIDATE -> CANDIDATE |
| T3.7rsi2c | RSI2C_s20 | sleeve | 10,568 | [2,294, 20,281] (1,000 iid) | [2,240, 19,335] | 2,133 / 2,133 | Y -> Y | 12,287 |  | PASS -> PASS |
| T3.7rsi2c | RSI2CC_s20 | sleeve | 2,646 | [574, 5,078] (1,000 iid) | [561, 4,841] | 534 / 534 | Y -> Y | 3,077 |  | PASS -> PASS |
| T3.8A | ES_RSI2_t10 | sleeve | 12,559 | [3,559, 22,101] (1,000 iid) | [3,990, 21,317] | 4,324 / 4,062 | Y -> Y | 12,287 |  | PASS -> PASS |
| T3.8A | YM_RSI2_t10 | sleeve | 8,274 | [-87, 17,321] (1,000 iid) | [-243, 16,846] | -225 / -218 | N -> N | 12,287 |  | CANDIDATE -> CANDIDATE |
| T3.8A | COMB_c3_R | sleeve | 2,831 | [307, 5,812] (1,000 iid) | [155, 5,528] | 153 / 132 | Y -> Y | 3,847 |  | CANDIDATE -> CANDIDATE |
| T3.8B | GSHORT_t90 | sleeve | 5,941 | [-2,995, 14,754] (1,000 iid) | [-2,628, 14,889] | -2,672 / -2,511 | N -> N | 12,287 |  | PASS -> PASS |
| NM_B | B01_SetB | sizing-lock-session | 8,131 | [-80, 16,029] (2,000 block) | [-84, 16,100] | -147 / 117 | N -> N | 11,536 | [-4,841, 8,599] / [-291,698, 89,882] | CANDIDATE -> CANDIDATE |
| NM_B | B05_SetB_pb3R_vsA | sizing-lock-session | 9,066 | [-1,773, 18,525] (2,000 block) | [-1,481, 18,862] | -1,500 / -1,389 | N -> N | 14,578 | [6,134, 22,895] / [-259,155, 201,192] | CANDIDATE -> CANDIDATE |
| NM_B | B05_SetB_pb4R_vsA | sizing-lock-session | 8,383 | [-2,578, 18,411] (2,000 block) | [-2,622, 18,559] | -2,810 / -2,538 | N -> N | 15,329 | [7,104, 27,770] / [-247,260, 242,484] | CANDIDATE -> CANDIDATE |
| NM_B | B05_SetB_pboff_vsA | sizing-lock-session | 10,507 | [-273, 20,378] (2,000 block) | [-233, 20,686] | -388 / -289 | N -> N | 15,018 | [6,940, 27,730] / [-243,467, 248,623] | CANDIDATE -> CANDIDATE |
| NM_B | B06_SetB_pb2R_noprofit_vsA | sizing-lock-session | 8,016 | [-522, 16,241] (2,000 block) | [-474, 16,427] | -552 / -309 | N -> N | 12,048 | [-4,717, 10,882] / [-289,135, 90,484] | CANDIDATE -> CANDIDATE |
| NM_B | B06_SetB_pb3R_noprofit_vsA | sizing-lock-session | 9,125 | [-1,522, 18,982] (2,000 block) | [-1,522, 19,260] | -1,666 / -1,569 | N -> N | 14,932 | [6,630, 25,335] / [-258,300, 202,686] | CANDIDATE -> CANDIDATE |
| NM_B | B06_SetB_pb4R_noprofit_vsA | sizing-lock-session | 8,442 | [-2,458, 18,693] (2,000 block) | [-2,693, 18,914] | -2,978 / -2,720 | N -> N | 15,577 | [7,652, 30,081] / [-245,770, 245,695] | CANDIDATE -> CANDIDATE |
| NM_B | B06_SetB_pboff_noprofit_vsA | sizing-lock-session | 10,566 | [-327, 20,628] (2,000 block) | [-390, 21,092] | -549 / -345 | N -> N | 15,298 | [7,341, 29,353] / [-243,143, 249,994] | CANDIDATE -> CANDIDATE |
| NM_B | B07_SetB_Rscaled_pb2R_vsA | sizing-lock-session | 6,902 | [-1,070, 14,596] (2,000 block) | [-955, 14,711] | -1,006 / -868 | N -> N | 11,128 | [-5,581, 11,226] / [-239,651, 107,924] | CANDIDATE -> CANDIDATE |
| NM_B | B07_SetB_Rscaled_pb4R_vsA | sizing-lock-session | 8,344 | [-1,554, 17,422] (2,000 block) | [-1,538, 17,434] | -1,610 / -1,444 | N -> N | 13,635 | [5,088, 23,951] / [-255,227, 202,705] | CANDIDATE -> CANDIDATE |
| NM_E | E:NQ_RSI2_t10 | sleeve | 5,099 | [980, 10,121] (1,000 iid) | [1,023, 9,618] | 986 / 976 | Y -> Y | 6,143 |  | PASS -> PASS |
| NM_E | E:NQ_RSI2T_t10 | sleeve | 4,441 | [548, 9,523] (1,000 iid) | [334, 8,932] | 309 / 346 | Y -> Y | 6,143 |  | CANDIDATE -> CANDIDATE |
| NM_E | E:NQ_RSI2C_s20 | sleeve | 5,284 | [1,147, 10,141] (1,000 iid) | [1,120, 9,667] | 1,066 / 1,067 | Y -> Y | 6,143 |  | PASS -> PASS |
| NM_E | E:NQ_RSI2CC_s20 | sleeve | 5,284 | [1,147, 10,141] (1,000 iid) | [1,120, 9,667] | 1,066 / 1,067 | Y -> Y | 6,143 |  | PASS -> PASS |
| NM_E | E:ES_RSI2_t10 | sleeve | 6,279 | [1,779, 11,051] (1,000 iid) | [1,995, 10,658] | 2,162 / 2,031 | Y -> Y | 6,143 |  | PASS -> PASS |
| NM_E | E:NQ_IBS_t20_n1 | sleeve | 4,232 | [210, 9,065] (1,000 iid) | [154, 8,605] | 94 / 190 | Y -> Y | 6,143 |  | CANDIDATE -> CANDIDATE |
| NM_E | E:COMB_c3_R | sleeve | 5,118 | [1,131, 9,760] (1,000 iid) | [970, 9,461] | 991 / 868 | Y -> Y | 6,143 |  | CANDIDATE -> CANDIDATE |
| NM_E | E:GSHORT_t90 | sleeve | 2,970 | [-1,498, 7,377] (1,000 iid) | [-1,314, 7,444] | -1,336 / -1,255 | N -> N | 6,143 |  | PASS -> PASS |
| NM_E | E:ORB_ASIA_15_v1_s60 | sleeve | 4,462 | [426, 8,988] (1,000 iid) | [207, 8,841] | 326 / 173 | Y -> Y | 6,143 |  | PASS -> PASS |
| NM_E | E:ORB_ASIA_15_v1_s75 | sleeve | 4,472 | [268, 8,714] (1,000 iid) | [193, 8,728] | 258 / 217 | Y -> Y | 6,143 |  | PASS -> PASS |

Notes: (1) the sleeve rows at several sizes (ORB_ASIA_*@0.25/0.5/1.0, E:* vs T3.* duplicates) are the same series scaled, so their CIs scale linearly and are not independent evidence. (2) The 10 NM-B sizing cells are one edge (Set B); their 10k SD-difference CI is above 0 for the day-loss-relaxed variants (SD worse) and includes 0 for Set B and the 2R variants; the maxDD-difference CI (weekly-path) includes 0 in all ten (MDE ~260k). (3) Nothing here changes a verdict of record, a registration in PAPER-ALL, or any live decision; no trials are appended (re-draws of existing cells, no new cell).
