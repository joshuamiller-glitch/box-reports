## DAILY-R6 (S4a, 2026-11-06): the FIND_DAILY 34-cell daily-horizon design on the 16 unscored outrights SI HG PL NG RB HO ZF ZT 6B 6A 6C ZC ZS ZW LE HE (IDEAS_ROUND2 R6)
Prereg l2vast/ds3/prereg/DAILY_R6_prereg.md sha256 fb13144effb0b24ed4820c152c333cd3eb8459074d2c558718a517191d776f1b (filed before any statistic; inherits FIND_DAILY bf1de6c6...; per the R5 finding the RANDOM-SIDE null governs trend cells, the shift null is a cross-check). Code l2vast/ds3/code/t2s4a/daily6_lib.py, daily6_run.py, daily6_analyze.py, daily6_follow.py; data /mnt/l2/l2vast/ds3_daily6/ (/mnt/l2 only). Ledger T2F_DAILY6_<SYM> (612 rows), n_tested + 612.
**Set.** The owned 26-outright 1-minute set (data_autopilot/ohlcv1m, .v.0 volume-front with instrument_id, 2013-01..2026-10-14) holds ES NQ RTY YM GC SI HG PL CL NG RB HO ZN ZB ZF ZT 6E 6J 6B 6A 6C ZC ZS ZW LE HE (+ NKD). Already scored in FIND_DAILY: ES RTY YM GC CL ZN ZB 6E 6J NKD; NQ is the live stack. **New: the 16 above; nothing else in the set was uncovered.** Overlap cited, not repeated: T4 Family A (outputs/t4, daily trend book Donchian 20/10-100/50, EMA 20/100, 50/200, 12-month TSMOM, Supertrend on these outrights, sleeve scoring vs the NQ pair), IDEAS50K N7 (weekly-range position, REPORT_N7.md: NO), N10 (cross-sectional daily rank books, candle patterns: 3 gate a-d passes, all one beta bet), N13 (cross-sectional momentum commodities: N13-CSMOM-COMMXX gate a-d True only under an invalid beta null); none of the 34 time-series cells per product is a repeat.
**Repair scan first (DATA_BAD_PRINTS rule).** Bad-bar share by product (max by year): 6A 1.37% (2013), 6C 1.07% (2013), 6B 1.06% (2013), all three below 0.05% from 2016 on (the same early-FX print problem as 6E / 6J, repaired); LE 0.36% (2015) and HE 0.23% (2014); ZW 0.13% (2022); the other ten products at most 0.05% every year. The repaired copy is used. Rolls (volume-front changes, 2013-2026): SI 71, HG 69, PL 55, NG 169, RB 222, HO 179, ZF 57, ZT 55, 6B / 6A / 6C 55 each, ZC 90, ZS 80, ZW 77, LE 121, HE 123.
**Anchors (ET; execution P = open of the anchor bar, signal inputs = bars before it; stated per product) and PROXY specs (not in FEES.md):** SI HG PL 13:25 (COMEX close 13:30; day open Q 08:20); NG RB HO 14:25 (settlement 14:30; Q 09:00); ZF ZT 14:55 (CBOT Treasuries day close 15:00; Q 08:20); 6B 6A 6C 15:55 (24-hour FX; Q 08:20); ZC ZS ZW 14:15 (grain close 14:20; Q 09:30); LE HE 14:00 (livestock close 14:05; Q 09:30). Point value / tick: SI 5000 / 0.005, HG 25000 / 0.0005, PL 50 / 0.1, NG 10000 / 0.001, RB HO 42000 / 0.0001, ZF 1000 / 1/128, ZT 2000 / 1/256, 6B 62500 / 0.0001, 6A 100000 / 0.0001, 6C 100000 / 0.00005, ZC ZS ZW 50 / 0.25, LE HE 400 / 0.025; fee $4.84 RT (PROXY-STD), 1 tick per market leg, roll = 2 slips + one RT fee per held lot. Thin products (PL, LE, HE, ZT) carry a liquidity caveat; margin not in the repository.
**Plain sentence: none of the 16 new outrights yields a daily book: of 578 cells (34 per product x 16 + the 16-product portfolio) 197 are net positive over 13 years, 41 also positive in at least 60% of years, 19 also pass the per-year MDE test and 14 the HOLD test (tolerant: HE 2, HG 1, HO 3, NG 4, SI 1, ZT 1, ZW 1, portfolio 1); the smallest family p of a tolerant cell is 0.78 in the new-set family and 0.92 in the joint family with the 11 earlier instruments (1,000 random-side worlds; the family-maximum null has median 2.90 / 3.03 and p95 3.53 / 3.68), no cell is a LEAD (labels NULL 464, REGIME 130, best-of-F 18 over 612 rows incl. PORT27), and eight of the 13 tolerant instrument cells survive a 1.5x cost stress.**
Funnel and nulls: new-set family 578 cells; random-side maximum z median 2.90, p95 3.53; forward-shift median 2.70, p95 3.47; joint family 1,020 cells (374 earlier + 544 new instrument cells + PORT11 / PORT16 / PORT27): random-side median 3.03, p95 3.68; shift median 2.91, p95 3.65. Truncation audit 0 of 1,296 mismatches.
### Tolerant cells (maxDD first; $ at stated lots, vol lots with 1-lot floor; HOLD $/wk carry-dropped)
| cell | maxDD $ | 13y net $ | years + | HOLD $/wk | z random-side | family p random-side A / B | family p shift A | walk-forward OOS (p) | corr to NQ stack (weekly) | survives 1.5x cost |
|--|--|--|--|--|--|--|--|--|--|--|
| NG MR_k5_th1.5 | 27453 | 69331 | 11/14 | 76 | 2.66 | 0.776 / 0.916 | 0.60 | 45061 (p 0.39) | 0.02 | yes |
| HO NIGHT_L | 56974 | 244468 | 10/14 | 1806 | 2.59 | 0.833 / 0.946 | 1.00 | 114324 (p 0.10) | 0.01 | yes |
| HG TSMOM_L252_vol | 87587 | 114230 | 9/14 | 291 | 1.40 | 1.000 / 1.000 | 1.00 | 33286 (p 0.05) | -0.14 | yes |
| NG TSMOM_L21_1lot | 42301 | 76886 | 9/14 | 102 | 1.30 | 1.000 / 1.000 | 1.00 | 6060 (p 0.49) | 0.00 | yes |
| ZT DON_N100_EX | 36046 | 84139 | 9/14 | 281 | 1.25 | 1.000 / 1.000 | 1.00 | 73591 (p 0.52) | 0.07 | yes |
| ZW MR_k3_th1.5 | 29398 | 8103 | 9/14 | 510 | 1.23 | 1.000 / 1.000 | 1.00 | 7002 (p 0.19) | 0.07 | no |
| HO NIGHT_MOM20 | 60092 | 113942 | 9/14 | 2224 | 1.19 | 1.000 / 1.000 | 1.00 | 114324 (p 0.10) | 0.15 | no |
| SI MR_k1_th1.5 | 69804 | 88594 | 9/14 | 2174 | 1.12 | 1.000 / 1.000 | 1.00 | 50877 (p 0.43) | 0.09 | no |
| NG MR_k2_th1 | 55442 | 35253 | 9/14 | 43 | 1.07 | 1.000 / 1.000 | 1.00 | 45061 (p 0.39) | 0.03 | no |
| NG MR_k3_th1 | 56052 | 26320 | 9/14 | 111 | 0.94 | 1.000 / 1.000 | 1.00 | 45061 (p 0.39) | 0.02 | yes |
| HE DON_N40_SAR | 76740 | 52799 | 9/14 | 158 | 0.92 | 1.000 / 1.000 | 1.00 | -41690 (p 0.68) | -0.04 | no |
| PORT16 MA_50_200 | 548873 | 289523 | 9/14 | 4181 | 0.86 | 1.000 / 1.000 | 1.00 | -167497 (p 0.73) | -0.09 | n/a |
| HE DON_N40_EX | 40490 | 39440 | 10/14 | 232 | 0.82 | 1.000 / 1.000 | 1.00 | -41690 (p 0.68) | -0.01 | yes |
| HO DON_N100_EX | 139808 | 87274 | 9/14 | 863 | 0.61 | 1.000 / 1.000 | 1.00 | 192586 (p 0.03) | -0.05 | yes |
The portfolio (PORT27 = 11 earlier + 16 new products) has 4 tolerant cells and the 16-product portfolio 1 (MA 50/200, 13-year net $290k, maxDD $549k); the best portfolio family p is 0.15 / 0.26 (PORT27 night long, whose 13-year net is -$4.2M: a cost-eaten leg, below).
### Cross-check with the forward-shift null
Only one of the 612 rows has a shift-null family p <= .10: HE night momentum (z 3.36, p 0.06), with a random-side p of 0.26 and not tolerant; among the tolerant cells the smallest shift p is 0.60. The 6E TSMOM-252 pattern (shift p .005, random-side 1.00) does not recur here, and the random-side null governs.
### Annual-refit walk-forward: 7 of 90 groups positive with p <= .10, none distinguishable from chance after the multiplicity
The 90 groups (16 products + PORT16 + PORT27 x 5 families) are expected to give about 9 with p <= .10; 7 are positive. The smallest p is 0.004, Bonferroni over 90 groups 0.36. Each is dominated by one or two years and has a family p of 1.00 for its cells: p_rand tests whether refit beats a RANDOM parameter pick (many parameter sets in each family lose), not whether the family earns.
| group | OOS total $ | p vs random pick | OOS maxDD $ | OOS Calmar | years + | best year $ | best year share of total | stack dCalmar HOLD / L6M | corr to NQ stack |
|--|--|--|--|--|--|--|--|--|--|
| SI F1 | 182686 | 0.005 | 261083 | 0.07 | 7/10 | 164089 | 0.90 | +0.021 / +0.019 | -0.07 |
| HG F1 | 33286 | 0.046 | 87587 | 0.04 | 6/10 | 35401 | 1.06 | +0.018 / +0.005 | -0.14 |
| NG F3 | 75836 | 0.007 | 61441 | 0.12 | 8/10 | 32283 | 0.43 | +0.000 / +0.000 | +0.05 |
| HO F2 | 192586 | 0.034 | 119920 | 0.16 | 6/10 | 151169 | 0.78 | +0.049 / +0.002 | -0.01 |
| ZF F1 | 93693 | 0.004 | 17482 | 0.54 | 6/10 | 46293 | 0.49 | +0.008 / +0.004 | +0.02 |
| ZT F1 | 86317 | 0.020 | 19691 | 0.44 | 6/10 | 52485 | 0.61 | +0.004 / +0.003 | -0.03 |
| 6B F2 | 6916 | 0.056 | 78300 | 0.01 | 5/10 | 34510 | 4.99 | +0.000 / +0.000 | +0.06 |
ZF and ZT momentum (OOS +$94k and +$86k, maxDD $17-20k, Calmar 0.5) are the best-looking: about half of each comes from 2022 (+$46k and +$52k, the rate sell-off) and 2023-2026 is flat to negative, so they are a one-regime result; SI +$183k is 90% 2025; HO +$193k is 78% 2026.
### Unconditional night / day legs: a real overnight drift in ZS, LE (and mirror cases in HE, 6C) that the costs eat
The random-side null is a gross-drift test for the six constant-sign leg cells (probability 0.5 for the sign). LE night long (z 5.0, family p < .001 in A and B), ZS night long (z 4.3, < .001), 6C night short (z 3.7, 0.03 / 0.06) and HE night long (z 3.4, 0.08 / 0.14) beat the family-maximum null, i.e. the direction of the overnight move is not random, but every one has a NEGATIVE 13-year net at one tick per leg (LE -$68k, ZS -$20k, HE -$107k, 6C -$31k), so none is tolerant. Gross vs net (13 years, vol lots):
| leg | gross $ | net at 1 tick / leg $ | net at 0.5 tick / leg $ (COSTCAL S1 proxy) | cost at 1 tick $ |
|--|--|--|--|--|
| ZS NIGHT_L | +199096 | -19631 | +71994 | +218727 |
| ZS NIGHT_S | -199096 | -417823 | -326198 | +218727 |
| ZS DAY_S | +94082 | -124645 | -33020 | +218727 |
| LE NIGHT_L | +144326 | -68354 | +17266 | +212680 |
| LE NIGHT_S | -144326 | -357006 | -271386 | +212680 |
| LE DAY_S | +92984 | -119696 | -34076 | +212680 |
| HE NIGHT_L | +99200 | -106773 | -23853 | +205973 |
| HE NIGHT_S | -99200 | -305173 | -222253 | +205973 |
| HE DAY_S | +176591 | -29382 | +53538 | +205973 |
| 6C NIGHT_L | -180065 | -391505 | -320265 | +211440 |
| 6C NIGHT_S | +180065 | -31376 | +39864 | +211440 |
| 6C DAY_S | -39440 | -250880 | -179640 | +211440 |
The day leg mirrors the night leg (ZS day short +$94k gross vs night long +$199k; LE +$93k vs +$144k; HE +$177k vs +$99k): the anchor-to-open interval earns, the open-to-anchor interval gives it back. At a half-tick per leg ZS night long would be +$72k over 13 years (about $5.5k a year at 1-2 lots) and LE +$17k: a product-session microstructure effect of a few dollars per lot per day against round-trip costs of $25-30, unmeasured spreads (no order-book table for ZS / LE / HE / 6C), with the ZS evening session as the likely source. Not a book; a candidate for a measured-spread look if 1-s tables for ZS / LE are ever owned.
Limits: costs and specs are PROXY; thin products (PL, LE, HE, ZT) have wider true spreads than one tick; no frames saved (no cell is a lead); the joint family reuses the earlier 1,000-world totals for the 11 instruments (ids 1000-1999, independent of the new ids 2000-2999).
