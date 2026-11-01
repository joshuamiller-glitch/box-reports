# DS3_BETTER_S3A - T-BETTER section 3 part 1: new books ADDED to the base (S3a). POST-HOC / SEARCH, rank not kill, no PASS claim, Shadow/paper only
Written 2026-11-01 15:21Z. Prereg `l2vast/ds3/prereg/BETTER_S3A_prereg.md` sha256 `6ce604f7ef2612ef540b612b7239e16e8a77ff32993ec6c84b745286bb6007d8` (logged in DECISIONS.md before any add-a-book statistic; two disclosures logged there: three files that extend past the cap were opened with .head(3) and a bar-stats summary table was printed; none of their values is used). dead_lookup run first (`out/better/s3a/dead_lookup.txt`: TR3_DON15_S, both PB7 cells, TB4W_10 EXACT in D1_ORB as program cells; the X cells and sisters NOT FOUND as add-a-book cells); DEAD_CELLS append_cells after, never rebuilt. Masks capped 20260206, UNTOUCHED never read. Code `l2vast/ds3/code/better_s3a/`, outputs `l2vast/ds3/out/better/s3a/`.

**Bases.** PART I = interim base: DS3_ONE_CONVENTION composite (live lots, 70/30, PE 45-s, zone skip, Asia cut, ER sizer, parity stop, combined week lock off, slip +0.25; L6M +41.1k/wk, maxDD 22.9k) PLUS X1-X5 at 2 lots (M basis) = "Base B" (L6M 44.8k/wk, maxDD 19.4k; ALL maxDD 259.4k). PART II = BASE-1's D7 engine (`code/d7base/d7lib.py`, **WORK-IN-PROGRESS engine, not yet the announced 20:00Z delivery: re-run pending**; v1.0d as configured there: L6M 18.2k/wk, maxDD 84.8k, ALL maxDD 190.7k). Both reported; the two bases rank differently because the D7 base has a much lower mean and a much deeper L6M drawdown, so every positive-mean add gains Calmar there.

**Definitions used on every row.** Added book = lots x $20 x M-basis net points per contract (costs inside), lots 1/2/4; "best session" for alt-bar cells = highest PRE+X' mean per contract (n>=40), chosen on PRE+X' only. ΔCalmar = Calmar(base+add) - Calmar(base) in the window (Calmar = mean/weekly-cumulative maxDD); because Calmar is scale-free this IS the Calmar gain at equal risk (continuous rescale); the "equal-risk mean" columns rescale the whole combination so the ALL-period worst-20 equals the base's, once through the engine lot table (base re-run at lot scale c, integer half-up rounding; add scaled continuously) and once as a pure scale ("cont."). **Caution on L6M:** the base's L6M maxDD is ONE week (Base B: 19.4k, the week of 2026-01-19), so an add that happens to earn in that week cuts L6M maxDD and gains L6M Calmar by luck; the column "add in the base's worst L6M week" is in the CSV and HOLD / ALL / PRE / X' ΔCalmar are given beside L6M for that reason. S/T/N = STRICT / TOLERANT(literal) / NOW-ONLY (TB = TOL-B, nc = TOL-nc, post-hoc definitions in the prereg). * = |Δmean| beyond MDE. Placebo = 200 random-time same-count circular shifts of the book's own daily series; rank 0.95+ = beaten.

## PAGE 1

### Plain statement

1. **Nothing added is distinguishable from chance as an improvement of the drawdown-first picture; what ranks first is a hedge, not an edge.** PART I (interim base B), post-hoc ranking (L3M and L6M positive per contract, by L6M Calmar gain, best of 1/2/4 lots): top row `PE volume_500|PE|D|london` (vi-PE) ΔCalmar L6M +0.44/+0.68/+1.26; PART II (d7wip) top row `OVERNIGHT NQ IBS_t20_n1` (iii) +0.05/+0.12/+0.18. In Table 3 the observed best-of-N is at or below the null median for the sister, wave-1 and pullback families on the interim base, and the honest procedure (select on PRE+X', judge on L6M/HOLD) returns a NEGATIVE judged L6M ΔCalmar for the wave-1, pullback and sister families on the interim base. On PART II the program-cell family top sits near the null 95th percentile (chance share in Table 3), not below 5%.
2. **Overnight RSI2 / IBS sleeves (iii), label OVERNIGHT (the user runs overnight sleeves separately; D7 cannot host them):** positive in L3M, L6M, HOLD, PRE and X' (STRICT and TOLERANT yes for all four), weekly correlation to the base -0.12 to -0.01 (-0.31 to -0.14 inside the base's 20 worst weeks), worst-20 ALL improves +6 to +25k, ΔCalmar L6M +0.05 to +0.30 on the interim base (L6M maxDD unchanged: they do not trade the base's worst week) and +0.02 to +0.18 on PART II (L6M maxDD -23.3 to -3.6k), PRE ΔCalmar +0.003 to +0.037, X' -0.036 to +0.036. Placebo rank (L6M) 0.60-0.83 on the interim base, 0.94-1.00 on PART II. A12 caveat stands: this is the no-lock reading; routed inside the combined week lock the sleeve's PRE value vanishes.
3. **DN15 at real stop fills (i) and the direct PB7 cells (ii):** on the interim base they DEEPEN it: correlation +0.45 to +0.46 (DN) / +0.36 to +0.45 (PB7), L6M maxDD +2.3 to +15.3k (DN) / +3.2 to +30.5k (PB7) across 1-4 lots, ΔCalmar L6M -0.75 to -0.12 / -1.30 to -0.27, X' ΔCalmar -0.075 to -0.021 / -0.018 to -0.001, ALL worst-20 -298 to -56k / -287 to -15k. On PART II (weak L6M base) DN gains L6M Calmar (+0.03 to +0.15, mean up beyond MDE) while the ALL worst-20 still deepens -314 to -63k and HOLD ΔCalmar turns negative at 2-4 lots. Real fills cost DN 25-40% of its mapped mean (mapped 3.17k -> about 2.3-2.7k per contract-week L6M with u 1.4-1.7); Native exits recover roughly 0.3k per contract-week; only the Native-exit variants are STRICT; none is TOLERANT (clause 5 / PRE worst-20 fail).
4. **Alt-bar sisters of X1-X5 (iv):** 51 sister cell-session rows at 2 lots; 27 NOW-ONLY, 8 STRICT, 3 TOLERANT (PART II: 1); only 1 row has an L6M mean change beyond its MDE and the largest L6M mean add is 2.3k/wk on a $45k/wk base; ΔCalmar L6M positive in 11 of 51 on the interim base (24 on PART II). The ranking of axes (bar size / bracket / parameter / var) is in section 4 and is inside noise.
5. **(v) 60%/70% lists: no book-type row is runnable** (the 89 runnable rows are exits, sizers, the 70/30 split and EINT2 signal-state rules; entry-filter and CF-COMBO rows are filters on existing books or need a zone engine). Zero ADD rows; those rules belong to sections 1, 4, 5 of T-BETTER.
6. **(vi) TB4W_10 on 10-min / Volume-500 and PE on volume bars** are scored from the stored pullback-store and BARS-ENG daily series (Tables 1-2, section 8 notes); D7 cannot host them: the NT8 spec of the pullback engine on alt bars is section 6.

### Table 1 - ranked ADD table, PART I (interim base B), post-hoc ranking by L6M Calmar gain; the 'honest #' column is the rank of the same cell when selected on PRE+X' only (blank = not selected: PRE+X' mean <= 0 or ΔCalmar_PX <= 0)

| # | honest # | what | scope | sess/lots | ΔCalmar L6M @1/2/4 | ΔCalmar HOLD @1/2/4 | L6M maxDD k base→new | L6M mean k base→new (MDE) | ΔCalmar ALL / PRE / X′ | worst-20 ALL k Δ | equal-risk Δmean L6M k (lot table / cont.) | placebo rank L6M/HOLD | S/T/N | slot / code needed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 40 | PE volume_500|PE|D|london | vi-PE | london 4L | +0.44/+0.68/+1.26 | +0.01/+0.02/+0.04 | 19.4→13.1 | 44.8→46.9 (6.3) | -0.00 / -0.001 / -0.025 | -59 | -2.8 / 0.0 | 0.97/0.56 | S-N (TBn/ncy) | NEW CODE: PE (PB3B) on volume bars; see section 6 spec |
| 2 |  | EM|60/40|tc/2m|G|london [X5 sister: stop 60->40 (2 step)] | iv | london 4L | +0.09/+0.18/+0.30 | +0.00/+0.00/+0.01 | 19.4→17.6 | 44.8→45.9 (4.3) | -0.01 / -0.017 / +0.008 | -132 | -6.7 / -3.2 | 0.90/0.47 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 3 | 1 | OVERNIGHT NQ IBS_t20_n1 | iii | overnight 4L | +0.08/+0.15/+0.30 | +0.01/+0.03/+0.05 | 19.4→19.4 | 44.8→50.7 (9.3) | +0.04 / +0.037 / +0.029 | 7 | 5.4 / 6.2 | 0.83/0.42 | STN (TBy/ncy) | OVERNIGHT sleeve, outside D7 (user runs separately): needs a sleeve host (daily-bar RSI2/IBS entry at the close, exit at next sessions) |
| 4 | 34 | PE ha_volume_1000|PE|D|pre | vi-PE | pre 4L | +0.14/+0.27/+0.30 | +0.00/+0.01/+0.01 | 19.4→17.6 | 44.8→45.8 (2.7) | +0.00 / +0.002 / +0.009 | 19 | -1.4 / 1.8 | 0.81/0.42 | STN (TBy/ncy) | NEW CODE: PE (PB3B) on volume bars; see section 6 spec |
| 5 | 20 | PE volume_1000|PE|D|pre | vi-PE | pre 4L | +0.25/+0.25/+0.27 | +0.01/+0.02/+0.03 | 19.4→17.6 | 44.8→45.3 (3.3) | +0.01 / +0.008 / -0.001 | 14 | -2.0 / 1.1 | 0.81/0.55 | S-N (TBn/ncy) | NEW CODE: PE (PB3B) on volume bars; see section 6 spec |
| 6 |  | EM|40/60|vol/500|D|london [X4 sister: stop 75->60 (1 step)] | iv | london 4L | +0.24/+0.25/+0.26 | -0.01/-0.01/-0.02 | 19.4→17.6 | 44.8→45.1 (4.6) | -0.01 / -0.016 / -0.016 | -108 | -7.4 / -3.2 | 0.92/0.29 | S-N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 7 |  | PE ha_volume_1000|PE|G|pre | vi-PE | pre 4L | +0.13/+0.24/+0.25 | +0.00/+0.00/+0.00 | 19.4→17.6 | 44.8→45.0 (2.4) | -0.00 / -0.001 / +0.006 | 7 | -0.3 / 0.5 | 0.88/0.46 | STN (TBy/ncy) | NEW CODE: PE (PB3B) on volume bars; see section 6 spec |
| 8 |  | KB|50/75|range/8|D|asia [X3 sister: var D/G] | iv | asia 2L | +0.22/+0.25/-0.48 | -0.03/-0.05/-0.09 | 19.4→18.4 | 44.8→47.1 (4.1) | -0.01 / -0.021 / -0.024 | -141 | -5.6 / -2.4 | 0.88/0.27 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 9 | 4 | OVERNIGHT NQ_RSI2_t10 | iii | overnight 4L | +0.06/+0.11/+0.22 | +0.01/+0.02/+0.04 | 19.4→19.4 | 44.8→49.1 (7.6) | +0.02 / +0.023 / -0.036 | 25 | 2.1 / 5.3 | 0.77/0.48 | STN (TBy/ncy) | OVERNIGHT sleeve, outside D7 (user runs separately): needs a sleeve host (daily-bar RSI2/IBS entry at the close, exit at next sessions) |
| 10 | 5 | OVERNIGHT NQ_RSI2C_s20 | iii | overnight 4L | +0.05/+0.11/+0.21 | +0.01/+0.02/+0.04 | 19.4→19.4 | 44.8→48.9 (7.8) | +0.02 / +0.019 / -0.036 | 25 | 1.9 / 5.1 | 0.76/0.51 | STN (TBy/ncy) | OVERNIGHT sleeve, outside D7 (user runs separately): needs a sleeve host (daily-bar RSI2/IBS entry at the close, exit at next sessions) |
| 11 | 9 | OVERNIGHT ES_RSI2_t10 | iii | overnight 4L | +0.05/+0.10/+0.20 | +0.01/+0.02/+0.04 | 19.4→19.4 | 44.8→48.7 (4.8) | +0.01 / +0.014 / +0.023 | 13 | 1.1 / 4.4 | 0.78/0.44 | STN (TBy/ncy) | OVERNIGHT sleeve, outside D7 (user runs separately): needs a sleeve host (daily-bar RSI2/IBS entry at the close, exit at next sessions) |
| 12 |  | EM|60/60|tc/2m|D|asia [X5 sister: var D/G] | iv | asia 1L | +0.16/+0.08/-0.05 | -0.05/-0.09/-0.15 | 19.4→18.4 | 44.8→45.3 (1.3) | -0.00 / -0.005 / +0.014 | 2 | 0.6 / 0.7 | 0.78/0.10 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 13 |  | EM|40/50|vol/500|D|london [X4 sister: stop 75->50 (2 step)] | iv | london 1L | +0.10/-0.01/-0.22 | -0.00/-0.00/-0.01 | 19.4→18.6 | 44.8→44.9 (1.1) | -0.00 / -0.004 / -0.016 | -24 | -4.4 / -0.7 | 0.80/0.48 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 14 | 3 | pb TB4W_10_volume_500_ST10_E20_1_T1_nvolume00|tc/10m|M|asia | vi-TB4W | asia 1L | +0.08/-0.15/-0.84 | -0.01/-0.02/-0.04 | 19.4→18.9 | 44.8→45.3 (1.5) | +0.00 / +0.006 / -0.014 | -9 | 0.5 / 0.2 | 0.62/0.12 | STN (TBy/ncy) | NEW CODE: pullback engine (TB4) on alt bars; see section 6 spec |
| 15 | 19 | EM|50/75|vol/500|D|london [X4 sister: target 40->50 (2 step)] | iv | london 2L | +0.04/+0.08/-0.20 | +0.01/+0.01/+0.02 | 19.4→18.8 | 44.8→44.9 (2.4) | +0.00 / +0.006 / -0.037 | -36 | -5.8 / -1.1 | 0.76/0.41 | STN (TBy/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 16 |  | EM|60/60|ha/3m|D|nyam [X2 sister: target 50->60 (1 step)] | iv | nyam 1L | +0.07/-0.07/-0.31 | +0.00/+0.01/+0.01 | 19.4→18.9 | 44.8→45.0 (0.9) | +0.00 / +0.005 / -0.004 | -36 | -4.3 / -1.0 | 0.67/0.51 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 17 |  | EM|50/60|tc/3m|D|nyam [X2 sister: bar] | iv | nyam 1L | +0.04/-0.12/-0.38 | +0.00/+0.00/+0.00 | 19.4→19.1 | 44.8→45.0 (1.0) | +0.00 / +0.003 / -0.012 | -42 | -4.4 / -1.2 | 0.64/0.52 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 18 |  | KB|60/75|range/8|G|pre [X3 sister: target 50->60 (1 step)] | iv | pre 1L | +0.04/-0.13/-0.47 | -0.01/-0.01/-0.03 | 19.4→19.1 | 44.8→44.9 (1.1) | -0.01 / -0.007 / -0.004 | -25 | -4.4 / -0.7 | 0.75/0.41 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 19 | 22 | EM|40/60|ha/3m|D|nyam [X2 sister: target 50->40 (2 step)] | iv | nyam 1L | +0.02/-0.16/-0.45 | +0.00/+0.00/+0.00 | 19.4→19.3 | 44.8→44.9 (0.8) | +0.00 / +0.004 / +0.006 | -39 | -4.4 / -1.2 | 0.61/0.53 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 20 | 36 | EM|20/60|ha/3m|D|close [X2 sister: target 50->20 (4 step)] | iv | close 4L | +0.00/+0.00/+0.00 | +0.00/+0.01/+0.01 | 19.4→19.4 | 44.8→44.9 (0.3) | +0.00 / +0.002 / -0.018 | 3 | -1.4 / 0.2 | 0.61/0.85 | -TN (TBy/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 21 |  | KB|60/75|range/8|G|close [X3 sister: target 50->60 (1 step)] | iv | close 4L | +0.00/+0.00/+0.00 | +0.00/+0.00/+0.00 | 19.4→19.4 | 44.8→44.8 (1.5) | -0.00 / -0.002 / -0.021 | -43 | -5.9 / -1.5 | 0.66/0.56 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 22 | 35 | EM|50/75|ha/3m|D|nyam [X2 sister: stop 60->75 (1 step)] | iv | nyam 1L | -0.02/-0.24/-0.55 | -0.01/-0.01/-0.02 | 19.4→19.7 | 44.8→45.0 (1.0) | +0.00 / +0.000 / +0.014 | -48 | -5.6 / -1.4 | 0.56/0.37 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 23 | 17 | EM|50/40|ha/3m|D|nyam [X2 sister: stop 60->40 (2 step)] | iv | nyam 1L | -0.06/-0.29/-0.63 | -0.00/-0.00/-0.00 | 19.4→20.0 | 44.8→45.0 (0.8) | +0.00 / +0.005 / -0.012 | -31 | -4.4 / -0.9 | 0.55/0.49 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 24 |  | EM|20/60|ha/3m|D|nyam [X2 sister: target 50->20 (4 step)] | iv | nyam 1L | -0.07/-0.31/-0.65 | +0.00/+0.00/+0.01 | 19.4→20.1 | 44.8→45.0 (0.6) | +0.00 / +0.003 / -0.008 | -20 | -4.4 / -0.5 | 0.42/0.52 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 25 | 24 | DN15 stop-fill u=1.4 exits Native 1.28 | i |  1L | -0.12/-0.37/-0.68 | -0.07/-0.11/-0.17 | 19.4→21.7 | 44.8→47.5 (2.4)* | +0.00 / +0.002 / -0.021 | -56 | -3.3 / 0.7 | 0.41/0.00 | S-N (TBn/ncy) | N7 (0 lots in D7): set lots; resting stop-market 15-min Donchian-20 per DS3_SPEC_TR3_DON15_S; real fills 1.4-1.7 pt |

### Table 2 - HONEST ranking, PART I: selected on PRE+X' only (per-contract PX mean > 0 and PX ΔCalmar > 0), judged on L6M and HOLD

| honest # | what | scope | lots | selection: PRE+X′ ΔCalmar (PX per-contract mean) | judged L6M ΔCalmar | judged HOLD ΔCalmar | L6M maxDD k Δ | placebo rank L6M/HOLD | S/T/N at those lots | verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OVERNIGHT NQ IBS_t20_n1 | iii | 4 | +0.0324 () | +0.30 | +0.05 | 0.0 | 0.83/0.42 | STN | judged + |
| 2 | PB7_PB5_depth_atr0.5_W15_s-3 DIRECT | ii | 4 | +0.0245 () | -1.30 | -0.09 | 30.5 | 0.17/0.09 | S-N | judged - |
| 3 | pb TB4W_10_volume_500_ST10_E20_1_T1_nvolume00|tc/10m|M|asia | vi-TB4W | 4 | +0.0172 (+7.20 pt) | -0.84 | -0.04 | 12.3 | 0.13/0.13 | STN | judged - |
| 4 | OVERNIGHT NQ_RSI2_t10 | iii | 4 | +0.0161 () | +0.22 | +0.04 | 0.0 | 0.77/0.48 | STN | judged + |
| 5 | OVERNIGHT NQ_RSI2C_s20 | iii | 4 | +0.0138 () | +0.21 | +0.04 | 0.0 | 0.76/0.51 | STN | judged + |
| 6 | STM(m=3.0,n=10,tf=10)|60/60|tc/5m|D|nyam [X1 sister: param STM(m=3.5,n=10,tf=10)->STM(m=3.0,n=10,tf=10)] | iv | 4 | +0.0121 (+4.33 pt) | -0.75 | -0.04 | 10.3 | 0.51/0.22 | S-N | judged - |
| 7 | EM|40/60|tc/2m|G|nyam [X5 sister: target 60->40 (3 step)] | iv | 4 | +0.0118 (+3.09 pt) | -0.86 | +0.02 | 12.1 | 0.38/0.43 | S-N | HOLD only |
| 8 | EM|60/40|tc/2m|G|nyam [X5 sister: stop 60->40 (2 step)] | iv | 4 | +0.0117 (+1.25 pt) | -0.72 | +0.01 | 9.9 | 0.55/0.48 | --N | HOLD only |
| 9 | OVERNIGHT ES_RSI2_t10 | iii | 4 | +0.0107 () | +0.20 | +0.04 | 0.0 | 0.78/0.44 | STN | judged + |
| 10 | PE volume_2500|PE|D|nyam | vi-PE | 4 | +0.0107 (+2.08 pt) | -1.39 | -0.07 | 29.4 | 0.07/0.15 | --- | judged - |
| 11 | PE volume_2500|PE|G|nyam | vi-PE | 4 | +0.0107 (+2.08 pt) | -1.39 | -0.07 | 29.4 | 0.07/0.15 | --- | judged - |
| 12 | STM(m=3.5,n=10,tf=10)|60/60|tc/5m|G|asia [X1 sister: var D/G] | iv | 4 | +0.0105 (+6.47 pt) | -0.46 | +0.03 | 5.4 | 0.52/0.43 | S-N | HOLD only |
| 13 | EM|60/60|ha/3m|D|asia [X2 sister: target 50->60 (1 step)] | iv | 4 | +0.0090 (+1.54 pt) | -0.82 | -0.16 | 10.7 | 0.70/0.04 | --N | judged - |
| 14 | EM|60/60|tc/3m|G|nyam [X5 sister: bar] | iv | 2 | +0.0089 (+4.69 pt) | -0.45 | -0.01 | 4.9 | 0.25/0.23 | STN | judged - |
| 15 | EM|50/60|tc/2m|G|nyam [X5 sister: target 60->50 (1 step)] | iv | 4 | +0.0085 (+1.66 pt) | -0.95 | +0.01 | 14.7 | 0.40/0.39 | --N | HOLD only |
| 16 | PB7_HMA55_EMA1_T2_W60_s-3 DIRECT | ii | 4 | +0.0070 () | -1.16 | -0.13 | 25.7 | 0.20/0.01 | S-N | judged - |
| 17 | EM|50/40|ha/3m|D|nyam [X2 sister: stop 60->40 (2 step)] | iv | 2 | +0.0070 (+0.14 pt) | -0.29 | -0.00 | 3.0 | 0.52/0.49 | --N | judged - |
| 18 | STM(m=3.5,n=10,tf=10)|60/60|tc/3m|D|asia [X1 sister: bar] | iv | 1 | +0.0070 (+1.49 pt) | -0.35 | -0.06 | 3.1 | 0.33/0.04 | --- | judged - |
| 19 | EM|50/75|vol/500|D|london [X4 sister: target 40->50 (2 step)] | iv | 4 | +0.0069 (+2.88 pt) | -0.20 | +0.02 | 1.9 | 0.80/0.41 | S-N | HOLD only |
| 20 | PE volume_1000|PE|D|pre | vi-PE | 4 | +0.0068 (+3.31 pt) | +0.27 | +0.03 | -1.8 | 0.81/0.55 | S-N | judged + |

### Table 3 - best-of-N chance null (200 global circular shifts of each family panel against the base B, lots 2)

| family (N cells, deduped) | null | honest procedure: observed top by PX gain → its L6M ΔCalmar (null median / p95; share of draws ≥ obs) | → its HOLD ΔCalmar (null median / p95; share ≥ obs) | post-hoc: observed max L6M ΔCalmar over L3M&L6M>0 cells (null median / p95 / p99; share ≥ obs) | cells passing honest select (obs / null med) |
|---|---|---|---|---|---|
| program cells (i)(ii)(iii) + memo (17) | shift (keeps each cell mean) | +0.15 (-0.19 / +1.39; 0.24) | +0.03 (+0.06 / +0.30; 0.65) | +0.15 (+0.44 / +2.56 / +3.82; 0.75) | 14 / 16 |
| program cells (i)(ii)(iii) + memo (17) | shift + demeaned cells (no-edge luck) | +0.15 (-0.19 / +1.39; 0.24) | +0.03 (+0.06 / +0.30; 0.65) | +0.15 (+0.44 / +2.56 / +3.82; 0.75) | 14 / 16 |
| alt-bar sisters (iv) incl. X refs, 2 sessions (56) | shift (keeps each cell mean) | -0.26 (-0.37 / +0.73; 0.41) | +0.03 (+0.02 / +0.16; 0.47) | +0.28 (+0.99 / +2.29 / +3.51; 0.95) | 24 / 22 |
| alt-bar sisters (iv) incl. X refs, 2 sessions (56) | shift + demeaned cells (no-edge luck) | -0.26 (-0.64 / +0.45; 0.32) | +0.03 (-0.03 / +0.05; 0.12) | +0.28 (+0.85 / +2.28 / +2.93; 0.93) | 24 / 15 |
| whole wave-1 alt-bar store, non-1-min, rule session, deduped (3320) | shift (keeps each cell mean) | -1.21 (-0.94 / +0.52; 0.73) | +0.00 (-0.02 / +0.23; 0.45) | +0.91 (+3.78 / +14.72 / +149.95; 0.94) | 1281 / 1430 |
| whole wave-1 alt-bar store, non-1-min, rule session, deduped (3320) | shift + demeaned cells (no-edge luck) | -1.21 (-1.14 / -0.37; 0.55) | +0.00 (-0.07 / +0.10; 0.18) | +0.91 (+3.76 / +13.80 / +59.66; 0.94) | 1281 / 808 |
| pullback store + PE volume (vi context) (4762) | shift (keeps each cell mean) | -0.90 (-0.37 / +0.63; 0.89) | -0.13 (+0.00 / +0.14; 0.99) | +1.06 (+2.09 / +4.55 / +9.87; 0.97) | 2446 / 2600 |
| pullback store + PE volume (vi context) (4762) | shift + demeaned cells (no-edge luck) | -0.90 (-0.49 / +0.25; 0.83) | -0.13 (-0.04 / +0.03; 0.96) | +1.06 (+1.95 / +3.90 / +8.43; 0.95) | 2446 / 1266 |

Reading: 'share of draws >= obs' is the chance probability of seeing a best-of-N at least as good. Program cells have no real selection stage (D1 chose them with the recent windows in view), so their honest row is a formality. The shift null keeps every cell's own mean; the demeaned null removes it (pure luck).

### Table 4 - gate counts (lots 2)

| family | cells | NOW-ONLY | STRICT | TOLERANT (literal) | TOL-B | TOL-nc |
|---|---|---|---|---|---|---|
| (i) DN15 stop-fill variants | 6 | 6 | 4 | 0 | 0 | 6 |
| (ii) PB7 direct | 2 | 2 | 2 | 0 | 0 | 2 |
| (iii) overnight sleeves | 4 | 4 | 4 | 4 | 4 | 4 |
| (iv) alt-bar sisters | 51 | 27 | 8 | 3 | 3 | 27 |
| (vi) TB4W | 2 | 1 | 1 | 1 | 1 | 1 |
| (vi) PE volume | 12 | 4 | 4 | 2 | 2 | 4 |

### PAGE 1b - same ADD table on PART II (BASE-1 WIP engine), post-hoc ranking

| # | honest # | what | scope | sess/lots | ΔCalmar L6M @1/2/4 | ΔCalmar HOLD @1/2/4 | L6M maxDD k base→new | L6M mean k base→new (MDE) | ΔCalmar ALL / PRE / X′ | worst-20 ALL k Δ | equal-risk Δmean L6M k (lot table / cont.) | placebo rank L6M/HOLD | S/T/N | slot / code needed |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 1 | OVERNIGHT NQ IBS_t20_n1 | iii | overnight 4L | +0.05/+0.12/+0.18 | +0.05/+0.12/+0.17 | 84.8→61.5 | 18.2→24.1 (9.3) | +0.04 / +0.037 / +0.024 | -9 | 6.2 / 5.7 | 0.98/0.97 | S-N (TBn/ncy) | OVERNIGHT sleeve, outside D7 (user runs separately): needs a sleeve host (daily-bar RSI2/IBS entry at the close, exit at next sessions) |
| 2 | 13 | DN15 stop-fill u=1.4 exits Native 1.28 | i |  4L | +0.04/+0.08/+0.15 | +0.03/+0.00/-0.03 | 84.8→79.6 | 18.2→29.0 (9.7)* | +0.02 / +0.020 / +0.013 | -279 | 5.8 / 4.3 | 0.90/0.07 | S-N (TBn/ncy) | N7 (0 lots in D7): set lots; resting stop-market 15-min Donchian-20 per DS3_SPEC_TR3_DON15_S; real fills 1.4-1.7 pt |
| 3 | 12 | OVERNIGHT ES_RSI2_t10 | iii | overnight 4L | +0.03/+0.07/+0.15 | +0.03/+0.07/+0.14 | 84.8→61.5 | 18.2→22.1 (4.8) | +0.02 / +0.017 / +0.006 | 53 | 6.4 / 5.2 | 0.99/1.00 | STN (TBy/ncy) | OVERNIGHT sleeve, outside D7 (user runs separately): needs a sleeve host (daily-bar RSI2/IBS entry at the close, exit at next sessions) |
| 4 | 16 | DN15 stop-fill u=1.55 exits Native 1.28 | i |  4L | +0.04/+0.08/+0.14 | +0.03/-0.00/-0.04 | 84.8→80.2 | 18.2→28.7 (9.7)* | +0.02 / +0.018 / +0.011 | -285 | 5.6 / 3.9 | 0.92/0.07 | S-N (TBn/ncy) | N7 (0 lots in D7): set lots; resting stop-market 15-min Donchian-20 per DS3_SPEC_TR3_DON15_S; real fills 1.4-1.7 pt |
| 5 | 17 | DN15 stop-fill u=1.7 exits Native 1.28 | i |  4L | +0.04/+0.08/+0.14 | +0.03/-0.00/-0.04 | 84.8→80.8 | 18.2→28.4 (9.7)* | +0.01 / +0.017 / +0.008 | -290 | 5.3 / 3.6 | 0.92/0.07 | S-N (TBn/ncy) | N7 (0 lots in D7): set lots; resting stop-market 15-min Donchian-20 per DS3_SPEC_TR3_DON15_S; real fills 1.4-1.7 pt |
| 6 | 23 | DN15 stop-fill u=1.4 exits join 2.45 | i |  4L | +0.04/+0.07/+0.13 | +0.03/-0.01/-0.04 | 84.8→82.0 | 18.2→28.1 (9.8)* | +0.01 / +0.014 / +0.005 | -303 | 5.0 / 3.1 | 0.92/0.06 | S-N (TBn/ncy) | N7 (0 lots in D7): set lots; resting stop-market 15-min Donchian-20 per DS3_SPEC_TR3_DON15_S; real fills 1.4-1.7 pt |
| 7 |  | KB|50/75|range/8|D|asia [X3 sister: var D/G] | iv | asia 4L | +0.03/+0.08/+0.13 | +0.03/+0.04/+0.02 | 84.8→67.3 | 18.2→22.9 (8.2) | -0.04 / -0.054 / +0.076 | -521 | -0.9 / -3.4 | 0.90/0.71 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 8 | 27 | DN15 stop-fill u=1.55 exits join 2.45 | i |  4L | +0.03/+0.07/+0.12 | +0.03/-0.01/-0.05 | 84.8→82.6 | 18.2→27.8 (9.8) | +0.01 / +0.012 / +0.003 | -308 | 4.4 / 2.8 | 0.92/0.06 | --N (TBn/ncy) | N7 (0 lots in D7): set lots; resting stop-market 15-min Donchian-20 per DS3_SPEC_TR3_DON15_S; real fills 1.4-1.7 pt |
| 9 | 33 | DN15 stop-fill u=1.7 exits join 2.45 | i |  4L | +0.03/+0.07/+0.12 | +0.02/-0.01/-0.05 | 84.8→83.3 | 18.2→27.5 (9.8) | +0.01 / +0.010 / +0.001 | -314 | 4.2 / 2.5 | 0.92/0.06 | --N (TBn/ncy) | N7 (0 lots in D7): set lots; resting stop-market 15-min Donchian-20 per DS3_SPEC_TR3_DON15_S; real fills 1.4-1.7 pt |
| 10 | 3 | OVERNIGHT NQ_RSI2_t10 | iii | overnight 4L | +0.02/+0.05/+0.10 | +0.02/+0.04/+0.10 | 84.8→70.6 | 18.2→22.5 (7.6) | +0.02 / +0.029 / -0.001 | 25 | 7.1 / 5.0 | 0.94/0.94 | S-N (TBn/ncy) | OVERNIGHT sleeve, outside D7 (user runs separately): needs a sleeve host (daily-bar RSI2/IBS entry at the close, exit at next sessions) |
| 11 | 8 | OVERNIGHT NQ_RSI2C_s20 | iii | overnight 4L | +0.02/+0.05/+0.10 | +0.02/+0.04/+0.09 | 84.8→70.6 | 18.2→22.4 (7.8) | +0.02 / +0.022 / -0.001 | 39 | 6.7 / 5.1 | 0.95/0.95 | STN (TBy/ncy) | OVERNIGHT sleeve, outside D7 (user runs separately): needs a sleeve host (daily-bar RSI2/IBS entry at the close, exit at next sessions) |
| 12 | 28 | EM|60/60|tc/2m|D|asia [X5 sister: var D/G] | iv | asia 4L | +0.02/+0.04/+0.08 | +0.01/+0.00/-0.04 | 84.8→68.9 | 18.2→20.5 (5.0) | +0.01 / +0.004 / +0.018 | -172 | -1.1 / -0.8 | 0.94/0.37 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 13 |  | STM(m=3.5,n=10,tf=10)|60/60|tc/3m|D|nyam [X1 sister: bar] | iv | nyam 4L | +0.01/+0.03/+0.06 | +0.01/+0.02/+0.05 | 84.8→68.3 | 18.2→18.6 (3.9) | -0.01 / +0.019 / -0.032 | -124 | -1.7 / -1.7 | 0.93/0.93 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 14 | 2 | PB7_HMA55_EMA1_T2_W60_s-3 DIRECT | ii |  1L | +0.04/+0.02/-0.01 | +0.04/+0.02/-0.01 | 84.8→78.7 | 18.2→20.0 (2.9) | +0.01 / +0.009 / +0.009 | -73 | 0.6 / 0.3 | 0.91/0.91 | S-N (TBn/ncy) | A-slot family (PB7 engine exists; A6 = PB5 depth W15 s+0): new cell config HMA55/EMA1/T2/W60/s-3 or PB5 W15 s-3 |
| 15 |  | PE volume_500|PE|D|london | vi-PE | london 4L | +0.01/+0.01/+0.03 | +0.01/+0.01/+0.03 | 84.8→84.0 | 18.2→20.3 (6.3) | -0.00 / -0.001 / +0.007 | -69 | 0.9 / 0.7 | 0.67/0.75 | S-N (TBn/ncy) | NEW CODE: PE (PB3B) on volume bars; see section 6 spec |
| 16 | 19 | EM|60/40|tc/2m|G|nyam [X5 sister: stop 60->40 (2 step)] | iv | nyam 4L | +0.00/+0.01/+0.02 | +0.00/+0.01/+0.02 | 84.8→84.8 | 18.2→19.9 (3.8) | +0.01 / +0.021 / -0.023 | -116 | -0.6 / -0.5 | 0.64/0.62 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 17 | 14 | EM|50/60|tc/2m|G|nyam [X5 sister: target 60->50 (1 step)] | iv | nyam 4L | +0.00/+0.01/+0.02 | +0.00/+0.01/+0.02 | 84.8→84.8 | 18.2→19.7 (4.0) | +0.02 / +0.024 / -0.016 | -202 | -1.8 / -1.9 | 0.65/0.63 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 18 | 31 | PE volume_1000|PE|D|pre | vi-PE | pre 4L | +0.00/+0.01/+0.02 | +0.00/+0.01/+0.02 | 84.8→81.2 | 18.2→18.8 (3.3) | +0.00 / +0.004 / +0.014 | -12 | 0.7 / 0.3 | 0.59/0.65 | S-N (TBn/ncy) | NEW CODE: PE (PB3B) on volume bars; see section 6 spec |
| 19 | 6 | STM(m=3.0,n=10,tf=10)|60/60|tc/5m|D|nyam [X1 sister: param STM(m=3.5,n=10,tf=10)->STM(m=3.0,n=10,tf=10)] | iv | nyam 4L | +0.00/+0.01/+0.01 | +0.00/+0.00/+0.01 | 84.8→86.1 | 18.2→19.7 (3.6) | +0.01 / +0.017 / +0.018 | -204 | -1.8 / -1.9 | 0.51/0.45 | S-N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 20 |  | EM|50/60|tc/2m|G|london [X5 sister: target 60->50 (1 step)] | iv | london 4L | +0.00/+0.01/+0.01 | +0.00/+0.01/+0.02 | 84.8→84.9 | 18.2→19.4 (3.7) | -0.01 / -0.010 / -0.003 | -165 | -2.0 / -1.7 | 0.61/0.68 | S-N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 21 | 36 | EM|50/75|ha/3m|D|nyam [X2 sister: stop 60->75 (1 step)] | iv | nyam 4L | +0.00/+0.01/+0.01 | +0.00/+0.00/+0.01 | 84.8→84.8 | 18.2→19.3 (4.1) | +0.00 / +0.001 / +0.009 | -238 | -2.1 / -2.7 | 0.62/0.64 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 22 |  | EM|60/60|ha/3m|D|nyam [X2 sister: target 50->60 (1 step)] | iv | nyam 4L | +0.00/+0.01/+0.01 | +0.00/+0.01/+0.01 | 84.8→84.8 | 18.2→19.3 (3.5) | +0.01 / +0.008 / -0.018 | -182 | -2.1 / -2.0 | 0.66/0.62 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 23 | 11 | EM|40/60|tc/2m|G|nyam [X5 sister: target 60->40 (3 step)] | iv | nyam 4L | +0.00/+0.01/+0.01 | +0.00/+0.01/+0.01 | 84.8→84.8 | 18.2→19.2 (4.0) | +0.01 / +0.026 / -0.007 | -108 | -1.2 / -1.0 | 0.46/0.47 | S-N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 24 |  | EM|50/60|tc/3m|D|nyam [X2 sister: bar] | iv | nyam 4L | +0.00/+0.01/+0.01 | +0.00/+0.00/+0.01 | 84.8→84.8 | 18.2→19.1 (3.9) | -0.00 / +0.004 / -0.021 | -158 | -2.2 / -1.8 | 0.69/0.71 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |
| 25 |  | EM|20/60|ha/3m|D|nyam [X2 sister: target 50->20 (4 step)] | iv | nyam 4L | +0.00/+0.01/+0.01 | +0.00/+0.00/+0.01 | 84.8→84.8 | 18.2→19.1 (2.2) | -0.01 / -0.012 / +0.006 | -103 | -0.4 / -0.9 | 0.72/0.73 | --N (TBn/ncy) | X-slot family: same engine as X; change the bar size / bracket / generator parameter of the Shadow identity cell; native NT8 bar type |

**Honest ranking, PART II**

| honest # | what | scope | lots | selection: PRE+X′ ΔCalmar (PX per-contract mean) | judged L6M ΔCalmar | judged HOLD ΔCalmar | L6M maxDD k Δ | placebo rank L6M/HOLD | S/T/N at those lots | verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| 1 | OVERNIGHT NQ IBS_t20_n1 | iii | 4 | +0.0337 () | +0.18 | +0.17 | -23.3 | 0.98/0.97 | S-N | judged + |
| 2 | PB7_HMA55_EMA1_T2_W60_s-3 DIRECT | ii | 4 | +0.0300 () | -0.01 | -0.01 | 40.0 | 0.07/0.08 | S-N | judged - |
| 3 | OVERNIGHT NQ_RSI2_t10 | iii | 4 | +0.0202 () | +0.10 | +0.10 | -14.2 | 0.94/0.94 | S-N | judged + |
| 4 | STM(m=3.5,n=10,tf=10)|60/60|tc/5m|G|asia [X1 sister: var D/G] | iv | 4 | +0.0190 (+6.47 pt) | -0.01 | -0.01 | 9.8 | 0.20/0.22 | S-N | judged - |
| 5 | PB7_PB5_depth_atr0.5_W15_s-3 DIRECT | ii | 4 | +0.0189 () | -0.02 | -0.03 | 39.2 | 0.18/0.20 | S-N | judged - |
| 6 | STM(m=3.0,n=10,tf=10)|60/60|tc/5m|D|nyam [X1 sister: param STM(m=3.5,n=10,tf=10)->STM(m=3.0,n=10,tf=10)] | iv | 4 | +0.0161 (+4.33 pt) | +0.01 | +0.01 | 1.4 | 0.51/0.45 | S-N | judged + |
| 7 | EM|60/60|tc/3m|G|nyam [X5 sister: bar] | iv | 4 | +0.0161 (+4.69 pt) | +0.01 | +0.01 | 0.0 | 0.39/0.42 | S-N | judged + |
| 8 | OVERNIGHT NQ_RSI2C_s20 | iii | 4 | +0.0158 () | +0.10 | +0.09 | -14.2 | 0.95/0.95 | STN | judged + |
| 9 | EM|60/60|ha/3m|D|asia [X2 sister: target 50->60 (1 step)] | iv | 4 | +0.0152 (+1.54 pt) | -0.00 | -0.05 | 2.3 | 0.52/0.21 | --N | judged - |
| 10 | STM(m=3.5,n=10,tf=10)|60/60|tc/3m|D|asia [X1 sister: bar] | iv | 2 | +0.0147 (+1.49 pt) | -0.01 | -0.03 | -3.3 | 0.45/0.16 | --- | judged - |
| 11 | EM|40/60|tc/2m|G|nyam [X5 sister: target 60->40 (3 step)] | iv | 4 | +0.0138 (+3.09 pt) | +0.01 | +0.01 | 0.0 | 0.46/0.47 | S-N | judged + |
| 12 | OVERNIGHT ES_RSI2_t10 | iii | 4 | +0.0133 () | +0.15 | +0.14 | -23.3 | 0.99/1.00 | STN | judged + |
| 13 | DN15 stop-fill u=1.4 exits Native 1.28 | i | 4 | +0.0133 () | +0.15 | -0.03 | -5.2 | 0.90/0.07 | S-N | L6M only |
| 14 | EM|50/60|tc/2m|G|nyam [X5 sister: target 60->50 (1 step)] | iv | 4 | +0.0129 (+1.66 pt) | +0.02 | +0.02 | 0.0 | 0.65/0.63 | --N | judged + |
| 15 | EM|50/75|vol/500|D|london [X4 sister: target 40->50 (2 step)] | iv | 4 | +0.0125 (+2.88 pt) | -0.01 | -0.01 | 7.4 | 0.33/0.28 | STN | judged - |
| 16 | DN15 stop-fill u=1.55 exits Native 1.28 | i | 4 | +0.0118 () | +0.14 | -0.04 | -4.5 | 0.92/0.07 | S-N | L6M only |
| 17 | DN15 stop-fill u=1.7 exits Native 1.28 | i | 4 | +0.0104 () | +0.14 | -0.04 | -3.9 | 0.92/0.07 | S-N | L6M only |
| 18 | EM|20/60|tc/2m|G|nyam [X5 sister: target 60->20 (5 step)] | iv | 4 | +0.0095 (+0.27 pt) | -0.01 | -0.01 | 0.0 | 0.40/0.36 | --- | judged - |
| 19 | EM|60/40|tc/2m|G|nyam [X5 sister: stop 60->40 (2 step)] | iv | 4 | +0.0088 (+1.25 pt) | +0.02 | +0.02 | 0.0 | 0.64/0.62 | --N | judged + |
| 20 | EM|50/60|ha/5m|D|nyam [X2 sister: bar] | iv | 2 | +0.0088 (+1.93 pt) | -0.00 | +0.00 | 0.0 | 0.35/0.51 | --- | HOLD only |

**Chance null, PART II**

| family (N cells, deduped) | null | honest procedure: observed top by PX gain → its L6M ΔCalmar (null median / p95; share of draws ≥ obs) | → its HOLD ΔCalmar (null median / p95; share ≥ obs) | post-hoc: observed max L6M ΔCalmar over L3M&L6M>0 cells (null median / p95 / p99; share ≥ obs) | cells passing honest select (obs / null med) |
|---|---|---|---|---|---|
| program cells (i)(ii)(iii) + memo (17) | shift (keeps each cell mean) | +0.04 (+0.03 / +0.10; 0.45) | +0.03 (+0.03 / +0.10; 0.50) | +0.12 (+0.07 / +0.13 / +0.14; 0.07) | 17 / 16 |
| program cells (i)(ii)(iii) + memo (17) | shift + demeaned cells (no-edge luck) | +0.04 (+0.03 / +0.10; 0.45) | +0.03 (+0.03 / +0.10; 0.50) | +0.12 (+0.07 / +0.13 / +0.14; 0.07) | 17 / 16 |
| alt-bar sisters (iv) incl. X refs, 2 sessions (56) | shift (keeps each cell mean) | -0.01 (+0.00 / +0.05; 0.70) | -0.01 (+0.00 / +0.04; 0.66) | +0.08 (+0.06 / +0.12 / +0.15; 0.27) | 26 / 25 |
| alt-bar sisters (iv) incl. X refs, 2 sessions (56) | shift + demeaned cells (no-edge luck) | -0.01 (-0.02 / +0.02; 0.26) | -0.01 (-0.02 / +0.00; 0.23) | +0.08 (+0.06 / +0.12 / +0.15; 0.24) | 26 / 18 |
| whole wave-1 alt-bar store, non-1-min, rule session, deduped (3320) | shift (keeps each cell mean) | +0.04 (-0.02 / +0.08; 0.15) | +0.04 (-0.02 / +0.07; 0.13) | +0.25 (+0.18 / +0.42 / +0.71; 0.27) | 1671 / 1610 |
| whole wave-1 alt-bar store, non-1-min, rule session, deduped (3320) | shift + demeaned cells (no-edge luck) | +0.04 (-0.06 / -0.00; 0.00) | +0.04 (-0.07 / -0.01; 0.00) | +0.25 (+0.18 / +0.35 / +0.70; 0.23) | 1671 / 946 |
| pullback store + PE volume (vi context) (4762) | shift (keeps each cell mean) | -0.01 (-0.00 / +0.05; 0.68) | -0.01 (+0.00 / +0.05; 0.67) | +0.11 (+0.08 / +0.16 / +0.25; 0.24) | 3098 / 2908 |
| pullback store + PE volume (vi context) (4762) | shift + demeaned cells (no-edge luck) | -0.01 (-0.02 / +0.01; 0.30) | -0.01 (-0.02 / +0.01; 0.29) | +0.11 (+0.07 / +0.15 / +0.24; 0.14) | 3098 / 1476 |

**Gate counts, PART II**

| family | cells | NOW-ONLY | STRICT | TOLERANT (literal) | TOL-B | TOL-nc |
|---|---|---|---|---|---|---|
| (i) DN15 stop-fill variants | 6 | 6 | 4 | 0 | 0 | 6 |
| (ii) PB7 direct | 2 | 2 | 2 | 0 | 0 | 2 |
| (iii) overnight sleeves | 4 | 4 | 4 | 4 | 4 | 4 |
| (iv) alt-bar sisters | 51 | 27 | 8 | 1 | 1 | 27 |
| (vi) TB4W | 2 | 1 | 1 | 0 | 0 | 1 |
| (vi) PE volume | 12 | 4 | 4 | 0 | 0 | 4 |

## 1. (i) Donchian 15-min resting-stop book TR3_DON15_S (D7 slot N7 at 0 lots) at real stop fills

Series: A12/D1 mapped per-contract daily $ (entry booked at the stop level, market-class P9 correction) minus entry slippage u x $20 per trade, u = 1.4 / 1.55 / 1.7 pt (the 10-lot real-book walk of DS3_DN_STOPFILL: 1.44 [1.37, 1.51], plan on 1.7), trade-days from the capped A12 direct rows (3,272 trades inside the grid); exits: stop at the mapped join 2.45, or re-priced to Native 1.28 (+1.17 pt on the 1,501 ST_Stop exits). The REF row is the mapped series as scored. PART I, Base B.

**PART I: DN15 variants x lots 1/2/4**

| cell | lots | L6M mean k base→new (MDE) | ΔmaxDD L6M k | ΔCalmar L6M | HOLD | PRE | X′ | ALL | Δworst-20 ALL k | equal-risk Δmean L6M k (lot table / cont.) | corr ALL | corr in base worst-20 wks | add $k/wk in base worst-20 wks | ΔSharpe ALL | placebo L6M/HOLD | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DN15 stop-fill u=1.4 exits Native 1.28 | 1 | 44.8→47.5 (2.4)* | 2.3 | -0.12 | -0.07 | +0.002 | -0.021 | +0.002 | -56 | -3.3 / 0.7 | +0.46 | +0.44 | -2.7 | +0.01 | 0.41/0.00 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.4 exits Native 1.28 | 2 | 44.8→50.2 (4.9)* | 6.5 | -0.37 | -0.11 | +0.004 | -0.036 | +0.003 | -125 | 2.0 / 0.9 | +0.46 | +0.44 | -5.4 | -0.00 | 0.45/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.4 exits Native 1.28 | 4 | 44.8→55.6 (9.7)* | 14.7 | -0.68 | -0.17 | +0.008 | -0.060 | +0.006 | -268 | 1.4 / 1.1 | +0.46 | +0.44 | -10.8 | -0.06 | 0.55/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.4 exits join 2.45 | 1 | 44.8→47.2 (2.4)* | 2.4 | -0.14 | -0.07 | +0.001 | -0.025 | +0.000 | -61 | -3.6 / 0.3 | +0.46 | +0.45 | -2.9 | -0.02 | 0.43/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.4 exits join 2.45 | 2 | 44.8→49.7 (4.9)* | 6.6 | -0.40 | -0.12 | +0.002 | -0.043 | +0.001 | -136 | 1.5 / 0.1 | +0.46 | +0.45 | -5.9 | -0.06 | 0.48/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.4 exits join 2.45 | 4 | 44.8→54.6 (9.8)* | 15.1 | -0.73 | -0.18 | +0.003 | -0.070 | +0.001 | -289 | 0.6 / -0.3 | +0.46 | +0.45 | -11.8 | -0.16 | 0.56/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits Native 1.28 | 1 | 44.8→47.4 (2.4)* | 2.4 | -0.13 | -0.07 | +0.002 | -0.022 | +0.001 | -58 | -3.4 / 0.6 | +0.46 | +0.44 | -2.8 | -0.00 | 0.41/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits Native 1.28 | 2 | 44.8→50.0 (4.9)* | 6.5 | -0.38 | -0.11 | +0.004 | -0.038 | +0.003 | -128 | 1.8 / 0.7 | +0.46 | +0.44 | -5.5 | -0.02 | 0.45/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits Native 1.28 | 4 | 44.8→55.3 (9.7)* | 14.8 | -0.69 | -0.17 | +0.007 | -0.063 | +0.005 | -272 | 1.1 / 0.7 | +0.46 | +0.44 | -11.0 | -0.09 | 0.55/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits join 2.45 | 1 | 44.8→47.2 (2.4) | 2.5 | -0.15 | -0.07 | +0.000 | -0.026 | -0.000 | -62 | -3.6 / 0.2 | +0.45 | +0.45 | -3.0 | -0.03 | 0.43/0.01 | --N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits join 2.45 | 2 | 44.8→49.5 (4.9) | 6.7 | -0.41 | -0.12 | +0.001 | -0.045 | -0.000 | -138 | -3.4 / -0.1 | +0.45 | +0.45 | -6.0 | -0.07 | 0.48/0.01 | --N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits join 2.45 | 4 | 44.8→54.3 (9.8) | 15.2 | -0.74 | -0.18 | +0.001 | -0.072 | -0.000 | -293 | 0.3 / -0.7 | +0.45 | +0.45 | -12.0 | -0.19 | 0.56/0.01 | --N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits Native 1.28 | 1 | 44.8→47.3 (2.4)* | 2.4 | -0.14 | -0.07 | +0.001 | -0.023 | +0.001 | -59 | -3.5 / 0.4 | +0.46 | +0.45 | -2.8 | -0.01 | 0.43/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits Native 1.28 | 2 | 44.8→49.9 (4.8)* | 6.6 | -0.39 | -0.11 | +0.003 | -0.040 | +0.002 | -130 | 1.7 / 0.4 | +0.46 | +0.45 | -5.6 | -0.03 | 0.45/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits Native 1.28 | 4 | 44.8→55.0 (9.7)* | 15.0 | -0.71 | -0.17 | +0.005 | -0.066 | +0.003 | -277 | 0.9 / 0.3 | +0.46 | +0.45 | -11.3 | -0.12 | 0.56/0.01 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits join 2.45 | 1 | 44.8→47.1 (2.4) | 2.5 | -0.16 | -0.07 | -0.000 | -0.027 | -0.000 | -64 | -2.6 / 0.0 | +0.45 | +0.46 | -3.1 | -0.04 | 0.43/0.01 | --N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits join 2.45 | 2 | 44.8→49.4 (4.9) | 6.8 | -0.42 | -0.12 | -0.000 | -0.047 | -0.001 | -141 | -3.6 / -0.3 | +0.45 | +0.46 | -6.1 | -0.09 | 0.48/0.01 | --N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits join 2.45 | 4 | 44.8→54.0 (9.8) | 15.3 | -0.75 | -0.18 | -0.000 | -0.075 | -0.001 | -298 | 0.1 / -1.1 | +0.45 | +0.46 | -12.2 | -0.22 | 0.56/0.01 | --N(TBn/ncy) |

PART II (same rows):

**PART II: DN15 variants x lots 1/2/4**

| cell | lots | L6M mean k base→new (MDE) | ΔmaxDD L6M k | ΔCalmar L6M | HOLD | PRE | X′ | ALL | Δworst-20 ALL k | equal-risk Δmean L6M k (lot table / cont.) | corr ALL | corr in base worst-20 wks | add $k/wk in base worst-20 wks | ΔSharpe ALL | placebo L6M/HOLD | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DN15 stop-fill u=1.4 exits Native 1.28 | 1 | 18.2→20.9 (2.4)* | -2.4 | +0.04 | +0.03 | +0.007 | +0.004 | +0.006 | -63 | 1.5 / 1.4 | +0.35 | -0.28 | -2.9 | +0.09 | 0.94/0.81 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.4 exits Native 1.28 | 2 | 18.2→23.6 (4.9)* | -4.9 | +0.08 | +0.00 | +0.013 | +0.007 | +0.011 | -130 | 2.7 / 2.6 | +0.35 | -0.28 | -5.8 | +0.16 | 0.92/0.21 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.4 exits Native 1.28 | 4 | 18.2→29.0 (9.7)* | -5.2 | +0.15 | -0.03 | +0.020 | +0.013 | +0.017 | -279 | 5.8 / 4.3 | +0.35 | -0.28 | -11.6 | +0.22 | 0.90/0.07 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.4 exits join 2.45 | 1 | 18.2→20.7 (2.4)* | -2.1 | +0.04 | +0.03 | +0.006 | +0.002 | +0.005 | -68 | 1.3 / 1.1 | +0.35 | -0.27 | -3.2 | +0.06 | 0.92/0.81 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.4 exits join 2.45 | 2 | 18.2→23.1 (4.9)* | -4.2 | +0.07 | -0.01 | +0.009 | +0.004 | +0.008 | -142 | 2.2 / 1.9 | +0.35 | -0.27 | -6.4 | +0.09 | 0.92/0.15 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.4 exits join 2.45 | 4 | 18.2→28.1 (9.8)* | -2.7 | +0.13 | -0.04 | +0.014 | +0.005 | +0.012 | -303 | 5.0 / 3.1 | +0.35 | -0.27 | -12.8 | +0.09 | 0.92/0.06 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits Native 1.28 | 1 | 18.2→20.8 (2.4)* | -2.3 | +0.04 | +0.03 | +0.007 | +0.003 | +0.006 | -64 | 1.5 / 1.3 | +0.35 | -0.27 | -3.0 | +0.08 | 0.93/0.81 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits Native 1.28 | 2 | 18.2→23.5 (4.9)* | -4.6 | +0.08 | -0.00 | +0.012 | +0.006 | +0.010 | -133 | 2.6 / 2.4 | +0.35 | -0.27 | -6.0 | +0.14 | 0.92/0.20 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits Native 1.28 | 4 | 18.2→28.7 (9.7)* | -4.5 | +0.14 | -0.04 | +0.018 | +0.011 | +0.016 | -285 | 5.6 / 3.9 | +0.35 | -0.27 | -11.9 | +0.18 | 0.92/0.07 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits join 2.45 | 1 | 18.2→20.6 (2.4) | -2.0 | +0.03 | +0.03 | +0.005 | +0.001 | +0.004 | -70 | 1.2 / 1.0 | +0.35 | -0.26 | -3.3 | +0.05 | 0.92/0.81 | --N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits join 2.45 | 2 | 18.2→23.0 (4.9) | -4.0 | +0.07 | -0.01 | +0.008 | +0.002 | +0.007 | -144 | 2.0 / 1.8 | +0.35 | -0.26 | -6.5 | +0.07 | 0.92/0.15 | --N(TBn/ncy) |
| DN15 stop-fill u=1.55 exits join 2.45 | 4 | 18.2→27.8 (9.8) | -2.1 | +0.12 | -0.05 | +0.012 | +0.003 | +0.010 | -308 | 4.4 / 2.8 | +0.35 | -0.26 | -13.0 | +0.05 | 0.92/0.06 | --N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits Native 1.28 | 1 | 18.2→20.8 (2.4)* | -2.2 | +0.04 | +0.03 | +0.006 | +0.002 | +0.005 | -65 | 1.4 / 1.2 | +0.35 | -0.27 | -3.0 | +0.07 | 0.93/0.81 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits Native 1.28 | 2 | 18.2→23.3 (4.8)* | -4.4 | +0.08 | -0.00 | +0.011 | +0.005 | +0.009 | -136 | 2.5 / 2.2 | +0.35 | -0.27 | -6.1 | +0.12 | 0.92/0.19 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits Native 1.28 | 4 | 18.2→28.4 (9.7)* | -3.9 | +0.14 | -0.04 | +0.017 | +0.008 | +0.014 | -290 | 5.3 / 3.6 | +0.35 | -0.27 | -12.2 | +0.14 | 0.92/0.07 | S-N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits join 2.45 | 1 | 18.2→20.5 (2.4) | -1.9 | +0.03 | +0.02 | +0.005 | +0.001 | +0.004 | -71 | 1.1 / 0.9 | +0.35 | -0.26 | -3.3 | +0.03 | 0.92/0.81 | --N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits join 2.45 | 2 | 18.2→22.8 (4.9) | -3.8 | +0.07 | -0.01 | +0.008 | +0.001 | +0.006 | -147 | 1.9 / 1.6 | +0.35 | -0.26 | -6.7 | +0.05 | 0.92/0.15 | --N(TBn/ncy) |
| DN15 stop-fill u=1.7 exits join 2.45 | 4 | 18.2→27.5 (9.8) | -1.5 | +0.12 | -0.05 | +0.010 | +0.001 | +0.008 | -314 | 4.2 / 2.5 | +0.35 | -0.26 | -13.3 | +0.02 | 0.92/0.06 | --N(TBn/ncy) |

## 2. (ii) The two direct PB7 cells, DIRECT basis only

**PART I: PB7_HMA55_EMA1_T2_W60_s-3 DIRECT and PB7_PB5_depth_atr0.5_W15_s-3 DIRECT (direct L6M 1,764 / 1,411 $ per contract-week; mapped 2,064 / 2,188 not scored)**

| cell | lots | L6M mean k base→new (MDE) | ΔmaxDD L6M k | ΔCalmar L6M | HOLD | PRE | X′ | ALL | Δworst-20 ALL k | equal-risk Δmean L6M k (lot table / cont.) | corr ALL | corr in base worst-20 wks | add $k/wk in base worst-20 wks | ΔSharpe ALL | placebo L6M/HOLD | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB7_HMA55_EMA1_T2_W60_s-3 DIRECT | 1 | 44.8→46.5 (2.9) | 5.1 | -0.41 | -0.04 | +0.002 | -0.001 | +0.002 | -55 | -4.2 / -0.2 | +0.45 | +0.37 | -2.6 | +0.01 | 0.17/0.01 | S-N(TBn/ncy) |
| PB7_HMA55_EMA1_T2_W60_s-3 DIRECT | 2 | 44.8→48.3 (5.8) | 11.9 | -0.77 | -0.08 | +0.004 | -0.001 | +0.004 | -121 | -4.6 / -0.7 | +0.45 | +0.37 | -5.3 | -0.00 | 0.15/0.01 | S-N(TBn/ncy) |
| PB7_HMA55_EMA1_T2_W60_s-3 DIRECT | 4 | 44.8→51.8 (11.7) | 25.7 | -1.16 | -0.13 | +0.008 | -0.016 | +0.007 | -287 | -3.4 / -2.6 | +0.45 | +0.37 | -10.6 | -0.06 | 0.20/0.01 | S-N(TBn/ncy) |
| PB7_PB5_depth_atr0.5_W15_s-3 DIRECT | 1 | 44.8→46.2 (3.1) | 3.2 | -0.27 | -0.03 | +0.007 | -0.001 | +0.007 | -15 | -3.2 / 0.9 | +0.36 | +0.28 | -0.7 | +0.03 | 0.29/0.09 | S-N(TBn/ncy) |
| PB7_PB5_depth_atr0.5_W15_s-3 DIRECT | 2 | 44.8→47.6 (6.2) | 10.9 | -0.74 | -0.05 | +0.013 | -0.008 | +0.013 | -41 | -3.2 / 1.3 | +0.36 | +0.28 | -1.5 | +0.03 | 0.22/0.09 | S-N(TBn/ncy) |
| PB7_PB5_depth_atr0.5_W15_s-3 DIRECT | 4 | 44.8→50.4 (12.5) | 30.5 | -1.30 | -0.09 | +0.026 | -0.018 | +0.027 | -149 | -2.7 / 0.3 | +0.36 | +0.28 | -3.0 | -0.02 | 0.17/0.09 | S-N(TBn/ncy) |

**PART II**

| cell | lots | L6M mean k base→new (MDE) | ΔmaxDD L6M k | ΔCalmar L6M | HOLD | PRE | X′ | ALL | Δworst-20 ALL k | equal-risk Δmean L6M k (lot table / cont.) | corr ALL | corr in base worst-20 wks | add $k/wk in base worst-20 wks | ΔSharpe ALL | placebo L6M/HOLD | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PB7_HMA55_EMA1_T2_W60_s-3 DIRECT | 1 | 18.2→20.0 (2.9) | -6.0 | +0.04 | +0.04 | +0.009 | +0.009 | +0.008 | -73 | 0.6 / 0.3 | +0.34 | -0.29 | -3.6 | +0.11 | 0.91/0.91 | S-N(TBn/ncy) |
| PB7_HMA55_EMA1_T2_W60_s-3 DIRECT | 2 | 18.2→21.7 (5.8) | 8.3 | +0.02 | +0.02 | +0.018 | +0.018 | +0.016 | -152 | 1.0 / 0.6 | +0.34 | -0.29 | -7.3 | +0.18 | 0.35/0.32 | S-N(TBn/ncy) |
| PB7_HMA55_EMA1_T2_W60_s-3 DIRECT | 4 | 18.2→25.3 (11.7) | 40.0 | -0.01 | -0.01 | +0.036 | +0.042 | +0.033 | -332 | 2.3 / 0.6 | +0.34 | -0.29 | -14.6 | +0.24 | 0.07/0.08 | S-N(TBn/ncy) |
| PB7_PB5_depth_atr0.5_W15_s-3 DIRECT | 1 | 18.2→19.6 (3.1) | 9.8 | -0.01 | -0.01 | +0.012 | +0.016 | +0.011 | -46 | 0.3 / 0.5 | +0.36 | -0.18 | -2.0 | +0.09 | 0.13/0.11 | S-N(TBn/ncy) |
| PB7_PB5_depth_atr0.5_W15_s-3 DIRECT | 2 | 18.2→21.0 (6.2) | 19.6 | -0.01 | -0.02 | +0.020 | +0.038 | +0.020 | -94 | 1.4 / 0.9 | +0.36 | -0.18 | -3.9 | +0.14 | 0.15/0.14 | S-N(TBn/ncy) |
| PB7_PB5_depth_atr0.5_W15_s-3 DIRECT | 4 | 18.2→23.8 (12.5) | 39.2 | -0.02 | -0.03 | +0.018 | +0.088 | +0.019 | -228 | 1.6 / 1.1 | +0.36 | -0.18 | -7.8 | +0.18 | 0.18/0.20 | S-N(TBn/ncy) |

## 3. (iii) RSI2 / IBS overnight sleeves - OVERNIGHT, the user runs overnight sleeves separately

**PART I (NQ RSI2_t10, NQ RSI2C_s20, ES RSI2_t10 at $50/pt, NQ IBS_t20_n1; memo rows ORB Asia and GSHORT_t90 are not positive L3M+L6M or not found)**

| cell | lots | L6M mean k base→new (MDE) | ΔmaxDD L6M k | ΔCalmar L6M | HOLD | PRE | X′ | ALL | Δworst-20 ALL k | equal-risk Δmean L6M k (lot table / cont.) | corr ALL | corr in base worst-20 wks | add $k/wk in base worst-20 wks | ΔSharpe ALL | placebo L6M/HOLD | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| MEMO NQ GSHORT_t90 | 1 | 44.8→45.1 (0.6) | -1.8 | +0.26 | +0.00 | +0.001 | -0.011 | +0.001 | -1 | 0.3 / 0.3 | -0.05 | +0.31 | -0.1 | +0.02 | 0.99/0.74 | ---(TBn/ncn) |
| MEMO NQ GSHORT_t90 | 2 | 44.8→45.4 (1.3) | -1.8 | +0.28 | +0.01 | +0.001 | -0.021 | +0.001 | -3 | 0.7 / 0.6 | -0.05 | +0.31 | -0.1 | +0.03 | 0.98/0.74 | ---(TBn/ncn) |
| MEMO NQ GSHORT_t90 | 4 | 44.8→46.1 (2.5) | -1.8 | +0.31 | +0.02 | +0.003 | -0.038 | +0.003 | -6 | 1.4 / 1.1 | -0.05 | +0.31 | -0.3 | +0.06 | 0.98/0.74 | ---(TBn/ncn) |
| MEMO NQ ORB_ASIA_15 s60 (Asia) | 1 | 44.8→45.5 (0.8) | 0.0 | +0.04 | -0.01 | +0.000 | -0.004 | +0.000 | -5 | 0.7 / 0.5 | +0.25 | +0.30 | -0.2 | -0.01 | 0.74/0.20 | --N(TBn/ncy) |
| MEMO NQ ORB_ASIA_15 s60 (Asia) | 2 | 44.8→46.2 (1.6) | 0.0 | +0.07 | -0.01 | +0.000 | -0.007 | +0.000 | -10 | 1.4 / 1.0 | +0.25 | +0.30 | -0.5 | -0.01 | 0.80/0.20 | --N(TBn/ncy) |
| MEMO NQ ORB_ASIA_15 s60 (Asia) | 4 | 44.8→47.5 (3.2) | 0.0 | +0.14 | -0.02 | -0.001 | -0.016 | -0.000 | -23 | -1.9 / 1.9 | +0.25 | +0.30 | -1.0 | -0.04 | 0.82/0.20 | --N(TBn/ncy) |
| OVERNIGHT ES_RSI2_t10 | 1 | 44.8→45.7 (1.2) | 0.0 | +0.05 | +0.01 | +0.003 | +0.012 | +0.003 | 6 | 0.4 / 1.2 | -0.01 | -0.18 | 0.3 | +0.07 | 0.74/0.43 | STN(TBy/ncy) |
| OVERNIGHT ES_RSI2_t10 | 2 | 44.8→46.7 (2.4) | 0.0 | +0.10 | +0.02 | +0.007 | +0.016 | +0.006 | 10 | 0.5 / 2.3 | -0.01 | -0.18 | 0.6 | +0.13 | 0.75/0.43 | STN(TBy/ncy) |
| OVERNIGHT ES_RSI2_t10 | 4 | 44.8→48.7 (4.8) | 0.0 | +0.20 | +0.04 | +0.014 | +0.023 | +0.013 | 13 | 1.1 / 4.4 | -0.01 | -0.18 | 1.3 | +0.22 | 0.78/0.44 | STN(TBy/ncy) |
| OVERNIGHT NQ IBS_t20_n1 | 1 | 44.8→46.2 (2.3) | 0.0 | +0.08 | +0.01 | +0.009 | +0.022 | +0.009 | 11 | -1.5 / 1.9 | -0.12 | -0.14 | 0.6 | +0.14 | 0.60/0.40 | STN(TBy/ncy) |
| OVERNIGHT NQ IBS_t20_n1 | 2 | 44.8→47.7 (4.6) | 0.0 | +0.15 | +0.03 | +0.019 | +0.036 | +0.019 | 20 | 0.6 / 3.7 | -0.12 | -0.14 | 1.1 | +0.24 | 0.70/0.40 | STN(TBy/ncy) |
| OVERNIGHT NQ IBS_t20_n1 | 4 | 44.8→50.7 (9.3) | 0.0 | +0.30 | +0.05 | +0.037 | +0.029 | +0.039 | 7 | 5.4 / 6.2 | -0.12 | -0.14 | 2.2 | +0.34 | 0.83/0.42 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2C_s20 | 1 | 44.8→45.8 (2.0) | 0.0 | +0.05 | +0.01 | +0.004 | +0.005 | +0.004 | 8 | -1.9 / 1.3 | -0.07 | -0.31 | 0.4 | +0.08 | 0.71/0.46 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2C_s20 | 2 | 44.8→46.8 (3.9) | 0.0 | +0.11 | +0.02 | +0.009 | -0.012 | +0.008 | 16 | -0.3 / 2.7 | -0.07 | -0.31 | 0.8 | +0.16 | 0.72/0.47 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2C_s20 | 4 | 44.8→48.9 (7.8) | 0.0 | +0.21 | +0.04 | +0.019 | -0.036 | +0.017 | 25 | 1.9 / 5.1 | -0.07 | -0.31 | 1.6 | +0.26 | 0.76/0.51 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2_t10 | 1 | 44.8→45.8 (1.9) | 0.0 | +0.06 | +0.01 | +0.005 | +0.005 | +0.004 | 8 | -1.9 / 1.4 | -0.06 | -0.31 | 0.4 | +0.10 | 0.70/0.46 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2_t10 | 2 | 44.8→46.9 (3.8) | 0.0 | +0.11 | +0.02 | +0.011 | -0.012 | +0.009 | 16 | -0.2 / 2.8 | -0.06 | -0.31 | 0.8 | +0.18 | 0.72/0.46 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2_t10 | 4 | 44.8→49.1 (7.6) | 0.0 | +0.22 | +0.04 | +0.023 | -0.036 | +0.019 | 25 | 2.1 / 5.3 | -0.06 | -0.31 | 1.6 | +0.26 | 0.77/0.48 | STN(TBy/ncy) |

**PART II**

| cell | lots | L6M mean k base→new (MDE) | ΔmaxDD L6M k | ΔCalmar L6M | HOLD | PRE | X′ | ALL | Δworst-20 ALL k | equal-risk Δmean L6M k (lot table / cont.) | corr ALL | corr in base worst-20 wks | add $k/wk in base worst-20 wks | ΔSharpe ALL | placebo L6M/HOLD | S/T/N |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| MEMO NQ GSHORT_t90 | 1 | 18.2→18.5 (0.6) | 0.0 | +0.00 | +0.00 | +0.001 | -0.001 | +0.001 | -3 | 0.3 / 0.3 | -0.08 | +0.52 | -0.1 | +0.02 | 0.72/0.77 | ---(TBn/ncn) |
| MEMO NQ GSHORT_t90 | 2 | 18.2→18.9 (1.3) | 0.0 | +0.01 | +0.01 | +0.001 | -0.002 | +0.001 | -6 | 0.8 / 0.6 | -0.08 | +0.52 | -0.3 | +0.05 | 0.72/0.77 | ---(TBn/ncn) |
| MEMO NQ GSHORT_t90 | 4 | 18.2→19.6 (2.5) | 0.0 | +0.02 | +0.02 | +0.000 | -0.004 | +0.001 | -14 | 1.5 / 1.1 | -0.08 | +0.52 | -0.6 | +0.08 | 0.72/0.80 | ---(TBn/ncn) |
| MEMO NQ ORB_ASIA_15 s60 (Asia) | 1 | 18.2→18.9 (0.8) | 1.3 | +0.00 | +0.00 | +0.001 | -0.001 | +0.001 | -6 | 0.8 / 0.6 | +0.18 | -0.14 | -0.3 | +0.01 | 0.76/0.72 | -TN(TBy/ncy) |
| MEMO NQ ORB_ASIA_15 s60 (Asia) | 2 | 18.2→19.6 (1.6) | 2.5 | +0.01 | +0.01 | +0.002 | -0.003 | +0.002 | -13 | 1.5 / 1.1 | +0.18 | -0.14 | -0.5 | +0.01 | 0.74/0.69 | --N(TBn/ncy) |
| MEMO NQ ORB_ASIA_15 s60 (Asia) | 4 | 18.2→21.0 (3.2) | 5.1 | +0.02 | +0.01 | +0.003 | -0.006 | +0.003 | -27 | 4.1 / 2.2 | +0.18 | -0.14 | -1.1 | +0.01 | 0.74/0.69 | --N(TBn/ncy) |
| OVERNIGHT ES_RSI2_t10 | 1 | 18.2→19.2 (1.2) | -7.0 | +0.03 | +0.03 | +0.004 | +0.002 | +0.004 | 13 | 3.1 / 1.2 | -0.11 | -0.58 | 0.7 | +0.10 | 1.00/1.00 | STN(TBy/ncy) |
| OVERNIGHT ES_RSI2_t10 | 2 | 18.2→20.2 (2.4) | -14.0 | +0.07 | +0.07 | +0.008 | +0.003 | +0.008 | 27 | 4.1 / 2.5 | -0.11 | -0.58 | 1.3 | +0.20 | 1.00/1.00 | STN(TBy/ncy) |
| OVERNIGHT ES_RSI2_t10 | 4 | 18.2→22.1 (4.8) | -23.3 | +0.15 | +0.14 | +0.017 | +0.006 | +0.016 | 53 | 6.4 / 5.2 | -0.11 | -0.58 | 2.7 | +0.35 | 0.99/1.00 | STN(TBy/ncy) |
| OVERNIGHT NQ IBS_t20_n1 | 1 | 18.2→19.7 (2.3) | -10.9 | +0.05 | +0.05 | +0.009 | +0.006 | +0.010 | 18 | 3.6 / 1.8 | -0.14 | -0.43 | 0.9 | +0.18 | 0.98/0.98 | STN(TBy/ncy) |
| OVERNIGHT NQ IBS_t20_n1 | 2 | 18.2→21.2 (4.6) | -21.8 | +0.12 | +0.12 | +0.018 | +0.012 | +0.018 | 31 | 5.3 / 3.7 | -0.14 | -0.43 | 1.8 | +0.31 | 0.99/1.00 | STN(TBy/ncy) |
| OVERNIGHT NQ IBS_t20_n1 | 4 | 18.2→24.1 (9.3) | -23.3 | +0.18 | +0.17 | +0.037 | +0.024 | +0.039 | -9 | 6.2 / 5.7 | -0.14 | -0.43 | 3.6 | +0.45 | 0.98/0.97 | S-N(TBn/ncy) |
| OVERNIGHT NQ_RSI2C_s20 | 1 | 18.2→19.2 (2.0) | -3.6 | +0.02 | +0.02 | +0.005 | -0.000 | +0.005 | 13 | 3.1 / 1.3 | -0.12 | -0.43 | 0.7 | +0.12 | 0.94/0.94 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2C_s20 | 2 | 18.2→20.3 (3.9) | -7.1 | +0.05 | +0.04 | +0.011 | -0.000 | +0.010 | 26 | 4.3 / 2.6 | -0.12 | -0.43 | 1.5 | +0.22 | 0.94/0.94 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2C_s20 | 4 | 18.2→22.4 (7.8) | -14.2 | +0.10 | +0.09 | +0.022 | -0.001 | +0.019 | 39 | 6.7 / 5.1 | -0.12 | -0.43 | 2.9 | +0.37 | 0.95/0.95 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2_t10 | 1 | 18.2→19.3 (1.9) | -3.6 | +0.02 | +0.02 | +0.007 | -0.000 | +0.005 | 13 | 3.2 / 1.4 | -0.11 | -0.43 | 0.7 | +0.14 | 0.94/0.93 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2_t10 | 2 | 18.2→20.4 (3.8) | -7.1 | +0.05 | +0.04 | +0.014 | -0.000 | +0.011 | 26 | 4.4 / 2.7 | -0.11 | -0.43 | 1.5 | +0.25 | 0.94/0.93 | STN(TBy/ncy) |
| OVERNIGHT NQ_RSI2_t10 | 4 | 18.2→22.5 (7.6) | -14.2 | +0.10 | +0.10 | +0.029 | -0.001 | +0.023 | 25 | 7.1 / 5.0 | -0.11 | -0.43 | 2.9 | +0.38 | 0.94/0.94 | S-N(TBn/ncy) |

A12's own risk work (DS3_ORB_RSI2_COMPLETE) found no full RISK-KEEP among 656 rows and that the sleeves' drawdown value disappears when routed inside the combined week lock; S3a adds them OUTSIDE the lock (lock off in both bases), so these numbers are the no-lock reading.

## 4. (iv) Alt-bar sister cells adjacent to X1-X5 (ranked by L6M ΔCalmar, all sisters, PART I)

Sister rule (prereg): one step on exactly one axis from the X cell's (generator, bracket, bar, var): adjacent bar size in its family or tc<->HA at the same minutes, target or stop to another registered value, STM parameter m/n, or var D<->G; 1-minute-bar cells excluded (D7 core engines). Each sister appears in its rule-chosen session and, where different, the X cell's own session. X cells themselves are reference rows (already in Base B at 2 lots).

| rank | cell [sister of: axis] | PX pts/ct | L3M / L6M pts/ct | ΔCalmar L6M @1/2/4 | ΔCalmar HOLD @1/2/4 | ΔmaxDD L6M k (best lots) | corr ALL | S/T/N (best lots) |
|---|---|---|---|---|---|---|---|---|
| 1 | EM|50/60|ha/3m|G|nyam [X2 : var D/G] | +6.45 | +6.12 / -0.15 | +0.11/+0.24/+0.53 | -0.00/-0.01/-0.01 | -3.6 | +0.06 | --- |
| 2 | EM|60/40|tc/2m|G|london [X5 : stop 60->40 (2 step)] | +0.16 | +0.68 / +3.58 | +0.09/+0.18/+0.30 | +0.00/+0.00/+0.01 | -1.8 | +0.23 | --N |
| 3 | EM|40/60|vol/500|D|london [X4 : stop 75->60 (1 step)] | +1.49 | +3.26 / +1.20 | +0.24/+0.25/+0.26 | -0.01/-0.01/-0.02 | -1.8 | +0.14 | S-N |
| 4 | KB|50/75|range/8|D|asia [X3 : var D/G] | -0.22 | +4.31 / +4.15 | +0.22/+0.25/-0.48 | -0.03/-0.05/-0.09 | -1.0 | +0.07 | --N |
| 5 | STM(m=3.5,n=10,tf=10)|60/60|tc/5m|G|nyam [X1 : var D/G] | +0.57 | -1.37 / +0.66 | +0.14/+0.23/+0.22 | +0.03/+0.06/+0.13 | -1.7 | +0.03 | --- |
| 6 | EM|40/40|vol/500|D|london [X4 : stop 75->40 (3 step)] | -2.79 | -3.25 / -0.30 | +0.22/+0.20/+0.17 | +0.00/+0.01/+0.02 | -1.7 | +0.05 | --- |
| 7 | EM|60/60|tc/2m|D|asia [X5 : var D/G] | +0.29 | +3.54 / +4.82 | +0.16/+0.08/-0.05 | -0.05/-0.09/-0.15 | -1.0 | +0.04 | --N |
| 8 | EM|40/60|ha/3m|D|nypm [X2 : target 50->40 (2 step)] | +0.40 | -9.46 / -5.85 | +0.07/+0.15/-0.10 | -0.01/-0.02/-0.03 | -1.4 | -0.02 | --- |
| 9 | EM|40/50|vol/500|D|london [X4 : stop 75->50 (2 step)] | -1.01 | +2.15 / +1.65 | +0.10/-0.01/-0.22 | -0.00/-0.00/-0.01 | -0.8 | +0.07 | --N |
| 10 | EM|50/75|vol/500|D|london [X4 : target 40->50 (2 step)] | +2.88 | +7.47 / +1.36 | +0.04/+0.08/-0.20 | +0.01/+0.01/+0.02 | -0.6 | +0.02 | STN |
| 11 | EM|60/60|ha/3m|D|nyam [X2 : target 50->60 (1 step)] | -0.01 | +5.24 / +4.26 | +0.07/-0.07/-0.31 | +0.00/+0.01/+0.01 | -0.5 | +0.20 | --N |
| 12 | EM|50/60|tc/3m|D|nyam [X2 : bar] | -0.60 | +2.36 / +3.35 | +0.04/-0.12/-0.38 | +0.00/+0.00/+0.00 | -0.3 | +0.13 | --N |
| 13 | KB|60/75|range/8|G|pre [X3 : target 50->60 (1 step)] | -0.51 | +2.81 / +3.24 | +0.04/-0.13/-0.47 | -0.01/-0.01/-0.03 | -0.3 | +0.09 | --N |
| 14 | KB|50/75|range/8|D|pre [X3 : var D/G] | -6.42 | -8.96 / -3.50 | +0.02/-0.16/-0.45 | -0.01/-0.01/-0.03 | -0.3 | -0.07 | --- |
| 15 | KB|50/75|range/16|G|pre [X3 : bar] | -2.93 | -4.30 / -3.84 | +0.02/-0.16/-0.45 | -0.04/-0.07/-0.13 | -0.3 | +0.00 | --- |
| 16 | EM|40/75|vol/1000|D|london [X4 : bar] | -2.36 | -6.39 / -6.18 | +0.02/-0.17/-0.47 | +0.00/+0.01/+0.02 | -0.3 | +0.10 | --- |
| 17 | EM|40/60|ha/3m|D|nyam [X2 : target 50->40 (2 step)] | +0.16 | +6.15 / +2.22 | +0.02/-0.16/-0.45 | +0.00/+0.00/+0.00 | -0.1 | +0.13 | --N |
| 18 | KB|90/75|range/8|G|pre [X3 : target 50->90 (2 step)] | +0.02 | +0.38 / -13.11 | +0.01/-0.18/-0.48 | -0.01/-0.02/-0.04 | -0.3 | -0.04 | --- |
| 19 | EM|20/60|ha/3m|D|close [X2 : target 50->20 (4 step)] | +1.07 | +15.46 / +6.47 | +0.00/+0.00/+0.00 | +0.00/+0.01/+0.01 | 0.0 | -0.18 | -TN |
| 20 | KB|60/75|range/8|G|close [X3 : target 50->60 (1 step)] | +1.49 | +2.81 / +1.00 | +0.00/+0.00/+0.00 | +0.00/+0.00/+0.00 | 0.0 | +0.04 | --N |
| 21 | KB|90/75|range/8|G|close [X3 : target 50->90 (2 step)] | +9.48 | +16.52 / -5.16 | -0.00/-0.00/-0.01 | +0.00/+0.00/+0.00 | 0.0 | +0.07 | --- |
| 22 | EM|40/40|vol/500|D|nypm [X4 : stop 75->40 (3 step)] | -1.31 | -7.06 / -6.47 | -0.00/-0.31/-1.06 | -0.04/-0.07/-0.12 | -0.6 | -0.06 | --- |
| 23 | STM(m=3.5,n=10,tf=10)|60/60|ha/5m|D|nyam [X1 : bar] | +0.82 | -1.37 / -0.13 | -0.01/-0.03/-0.05 | -0.00/-0.00/-0.01 | 0.1 | +0.09 | --- |
| 24 | EM|50/75|ha/3m|D|nyam [X2 : stop 60->75 (1 step)] | +0.95 | +5.66 / +4.48 | -0.02/-0.24/-0.55 | -0.01/-0.01/-0.02 | 0.3 | +0.21 | --N |
| 25 | EM|50/40|ha/3m|D|nyam [X2 : stop 60->40 (2 step)] | +0.14 | +2.13 / +2.76 | -0.06/-0.29/-0.63 | -0.00/-0.00/-0.00 | 0.6 | +0.10 | --N |
| 26 | EM|20/60|ha/3m|D|nyam [X2 : target 50->20 (4 step)] | -1.36 | +4.44 / +3.29 | -0.07/-0.31/-0.65 | +0.00/+0.00/+0.01 | 0.7 | +0.12 | --N |
| 27 | EM|50/40|ha/3m|D|asia [X2 : stop 60->40 (2 step)] | +0.59 | -1.73 / -1.12 | -0.07/-0.16/-0.46 | -0.05/-0.08/-0.14 | 0.6 | +0.14 | --- |
| 28 | EM|40/60|tc/2m|G|london [X5 : target 60->40 (3 step)] | +1.40 | +1.18 / -0.83 | -0.12/-0.23/-0.42 | +0.02/+0.05/+0.10 | 1.0 | +0.22 | --- |
| 29 | EM|50/60|ha/5m|D|nypm [X2 : bar] | +2.21 | +6.42 / +7.04 | -0.13/-0.24/-0.43 | -0.00/-0.00/-0.00 | 1.2 | +0.10 | --N |
| 30 | EM|60/60|tc/3m|G|london [X5 : bar] | -1.48 | +7.10 / +7.67 | -0.13/-0.24/-0.43 | +0.01/+0.03/+0.06 | 1.3 | +0.15 | --N |
| 31 | STM(m=3.5,n=10,tf=10)|60/60|tc/5m|G|asia [X1 : var D/G] | +6.47 | +0.78 / +4.99 | -0.14/-0.26/-0.46 | +0.01/+0.01/+0.03 | 1.3 | +0.13 | S-N |
| 32 | KB|50/75|range/4|G|pre [X3 : bar] | -5.26 | +0.21 / -0.33 | -0.14/-0.42/-0.81 | -0.02/-0.04/-0.07 | 1.2 | +0.04 | --- |
| 33 | STM(m=3.5,n=10,tf=10)|60/60|tc/3m|D|nyam [X1 : bar] | -0.36 | +3.30 / +1.01 | -0.14/-0.33/-0.69 | -0.01/-0.02/-0.04 | 1.3 | +0.06 | --N |
| 34 | EM|40/75|vol/500|G|asia [X4 : var D/G] | +1.99 | -2.92 / +1.78 | -0.17/-0.31/-0.54 | -0.02/-0.04/-0.08 | 1.5 | +0.06 | --- |
| 35 | STM(m=3.5,n=10,tf=10)|60/60|ha/5m|D|asia [X1 : bar] | +1.61 | +2.82 / +0.98 | -0.17/-0.47/-0.86 | -0.01/-0.03/-0.05 | 1.6 | +0.06 | S-N |
| 36 | EM|40/75|vol/500|G|london [X4 : var D/G] | -6.09 | +0.83 / -4.06 | -0.18/-0.33/-0.57 | -0.00/-0.01/-0.02 | 1.5 | +0.00 | --- |
| 37 | EM|60/60|tc/2m|D|london [X5 : var D/G] | -3.03 | -0.53 / -3.74 | -0.18/-0.33/-0.70 | +0.01/+0.01/+0.03 | 1.5 | -0.02 | --- |
| 38 | EM|40/60|tc/2m|G|nyam [X5 : target 60->40 (3 step)] | +3.09 | +13.19 / +4.05 | -0.18/-0.47/-0.86 | +0.01/+0.01/+0.02 | 1.7 | +0.14 | S-N |
| 39 | EM|20/60|tc/2m|G|london [X5 : target 60->20 (5 step)] | -1.85 | -2.61 / -5.25 | -0.19/-0.36/-0.63 | -0.01/-0.02/-0.04 | 1.5 | +0.13 | --- |
| 40 | EM|60/40|tc/2m|G|nyam [X5 : stop 60->40 (2 step)] | +1.25 | +11.52 / +6.68 | -0.24/-0.44/-0.72 | +0.00/+0.00/+0.01 | 2.5 | +0.14 | --N |
| 41 | EM|60/60|tc/3m|G|nyam [X5 : bar] | +4.69 | +0.63 / +3.67 | -0.25/-0.45/-0.75 | -0.00/-0.01/-0.02 | 2.5 | -0.03 | STN |
| 42 | STM(m=3.0,n=10,tf=10)|60/60|tc/5m|D|nyam [X1 : param STM(m=3.5,n=10,tf=10)->STM(m=3.0,n=10,tf=10)] | +4.33 | +2.61 / +4.38 | -0.25/-0.45/-0.75 | -0.01/-0.02/-0.04 | 2.6 | +0.24 | S-N |
| 43 | EM|50/60|ha/5m|D|nyam [X2 : bar] | +1.93 | +5.67 / -0.90 | -0.26/-0.47/-0.78 | +0.03/+0.06/+0.15 | 2.5 | +0.09 | --- |
| 44 | EM|20/60|tc/2m|G|nyam [X5 : target 60->20 (5 step)] | +0.27 | +3.71 / -3.21 | -0.27/-0.61/-1.04 | -0.01/-0.02/-0.04 | 2.5 | +0.09 | --- |
| 45 | EM|50/60|tc/2m|G|london [X5 : target 60->50 (1 step)] | +0.65 | +8.05 / +4.46 | -0.28/-0.49/-0.80 | +0.02/+0.05/+0.10 | 2.8 | +0.21 | S-N |
| 46 | EM|60/60|ha/3m|D|asia [X2 : target 50->60 (1 step)] | +1.54 | +0.10 / +0.25 | -0.28/-0.50/-0.82 | -0.05/-0.09/-0.16 | 2.7 | +0.13 | --N |
| 47 | KB|50/75|range/16|G|asia [X3 : bar] | -1.08 | -4.12 / -0.54 | -0.32/-1.01/-1.54 | -0.08/-0.13/-0.21 | 3.0 | +0.17 | --- |
| 48 | STM(m=3.5,n=10,tf=10)|60/60|tc/3m|D|asia [X1 : bar] | +1.49 | -5.81 / -4.48 | -0.35/-0.72/-1.18 | -0.06/-0.11/-0.19 | 3.1 | +0.12 | --- |
| 49 | EM|50/60|tc/2m|G|nyam [X5 : target 60->50 (1 step)] | +1.66 | +14.80 / +6.45 | -0.35/-0.61/-0.95 | +0.00/+0.00/+0.01 | 3.7 | +0.19 | --N |
| 50 | KB|50/75|range/4|G|nypm [X3 : bar] | -0.56 | -4.03 / -1.46 | -0.38/-1.06/-1.59 | -0.02/-0.04/-0.08 | 3.6 | -0.10 | --- |
| 51 | EM|40/75|vol/1000|D|asia [X4 : bar] | +2.48 | +0.59 / -1.31 | -0.56/-0.90/-1.30 | -0.02/-0.05/-0.09 | 6.1 | +0.02 | --- |

PART II ranking of the sisters:

| rank | cell [sister of: axis] | PX pts/ct | L3M / L6M pts/ct | ΔCalmar L6M @1/2/4 | ΔCalmar HOLD @1/2/4 | ΔmaxDD L6M k (best lots) | corr ALL | S/T/N (best lots) |
|---|---|---|---|---|---|---|---|---|
| 1 | KB|50/75|range/8|D|asia [X3 : var D/G] | -0.22 | +4.31 / +4.15 | +0.03/+0.08/+0.13 | +0.03/+0.04/+0.02 | -17.5 | +0.13 | --N |
| 2 | EM|60/60|tc/2m|D|asia [X5 : var D/G] | +0.29 | +3.54 / +4.82 | +0.02/+0.04/+0.08 | +0.01/+0.00/-0.04 | -15.9 | -0.00 | --N |
| 3 | STM(m=3.5,n=10,tf=10)|60/60|tc/3m|D|nyam [X1 : bar] | -0.36 | +3.30 / +1.01 | +0.01/+0.03/+0.06 | +0.01/+0.02/+0.05 | -16.5 | +0.02 | --N |
| 4 | EM|50/60|ha/3m|G|nyam [X2 : var D/G] | +6.45 | +6.12 / -0.15 | +0.00/+0.01/+0.02 | +0.01/+0.01/+0.02 | -7.3 | +0.13 | --- |
| 5 | EM|60/40|tc/2m|G|nyam [X5 : stop 60->40 (2 step)] | +1.25 | +11.52 / +6.68 | +0.00/+0.01/+0.02 | +0.00/+0.01/+0.02 | 0.0 | +0.11 | --N |
| 6 | EM|50/60|tc/2m|G|nyam [X5 : target 60->50 (1 step)] | +1.66 | +14.80 / +6.45 | +0.00/+0.01/+0.02 | +0.00/+0.01/+0.02 | 0.0 | +0.13 | --N |
| 7 | STM(m=3.0,n=10,tf=10)|60/60|tc/5m|D|nyam [X1 : param STM(m=3.5,n=10,tf=10)->STM(m=3.0,n=10,tf=10)] | +4.33 | +2.61 / +4.38 | +0.00/+0.01/+0.01 | +0.00/+0.00/+0.01 | 1.4 | +0.13 | S-N |
| 8 | EM|50/60|tc/2m|G|london [X5 : target 60->50 (1 step)] | +0.65 | +8.05 / +4.46 | +0.00/+0.01/+0.01 | +0.00/+0.01/+0.02 | 0.2 | +0.13 | S-N |
| 9 | EM|50/75|ha/3m|D|nyam [X2 : stop 60->75 (1 step)] | +0.95 | +5.66 / +4.48 | +0.00/+0.01/+0.01 | +0.00/+0.00/+0.01 | 0.0 | +0.18 | --N |
| 10 | EM|60/60|ha/3m|D|nyam [X2 : target 50->60 (1 step)] | -0.01 | +5.24 / +4.26 | +0.00/+0.01/+0.01 | +0.00/+0.01/+0.01 | 0.0 | +0.19 | --N |
| 11 | EM|40/60|tc/2m|G|nyam [X5 : target 60->40 (3 step)] | +3.09 | +13.19 / +4.05 | +0.00/+0.01/+0.01 | +0.00/+0.01/+0.01 | 0.0 | +0.09 | S-N |
| 12 | EM|50/60|tc/3m|D|nyam [X2 : bar] | -0.60 | +2.36 / +3.35 | +0.00/+0.01/+0.01 | +0.00/+0.00/+0.01 | 0.0 | +0.18 | --N |
| 13 | EM|20/60|ha/3m|D|nyam [X2 : target 50->20 (4 step)] | -1.36 | +4.44 / +3.29 | +0.00/+0.01/+0.01 | +0.00/+0.00/+0.01 | 0.0 | +0.11 | --N |
| 14 | EM|50/60|ha/5m|D|nypm [X2 : bar] | +2.21 | +6.42 / +7.04 | +0.00/+0.00/+0.01 | +0.00/+0.00/+0.01 | 0.0 | +0.11 | --N |
| 15 | EM|50/40|ha/3m|D|nyam [X2 : stop 60->40 (2 step)] | +0.14 | +2.13 / +2.76 | +0.00/+0.00/+0.01 | +0.00/+0.00/+0.01 | 0.0 | +0.12 | --N |
| 16 | EM|60/40|tc/2m|G|london [X5 : stop 60->40 (2 step)] | +0.16 | +0.68 / +3.58 | +0.00/+0.00/+0.01 | +0.00/+0.00/+0.01 | 2.1 | +0.17 | --N |
| 17 | EM|60/60|tc/3m|G|nyam [X5 : bar] | +4.69 | +0.63 / +3.67 | +0.00/+0.00/+0.01 | +0.00/+0.00/+0.01 | 0.0 | +0.00 | S-N |
| 18 | EM|40/60|ha/3m|D|nyam [X2 : target 50->40 (2 step)] | +0.16 | +6.15 / +2.22 | +0.00/+0.00/+0.01 | +0.00/+0.00/+0.00 | 0.0 | +0.07 | --N |
| 19 | EM|60/60|tc/3m|G|london [X5 : bar] | -1.48 | +7.10 / +7.67 | +0.00/+0.00/+0.00 | +0.00/+0.00/+0.00 | 6.3 | +0.13 | --N |
| 20 | EM|40/75|vol/500|G|asia [X4 : var D/G] | +1.99 | -2.92 / +1.78 | +0.00/+0.00/+0.00 | -0.00/-0.00/-0.00 | 0.4 | +0.07 | --- |
| 21 | STM(m=3.5,n=10,tf=10)|60/60|tc/5m|G|nyam [X1 : var D/G] | +0.57 | -1.37 / +0.66 | +0.00/+0.00/+0.00 | +0.00/+0.01/+0.01 | 0.0 | +0.05 | --- |
| 22 | STM(m=3.5,n=10,tf=10)|60/60|ha/5m|D|asia [X1 : bar] | +1.61 | +2.82 / +0.98 | +0.00/+0.00/+0.00 | -0.00/-0.00/-0.00 | 0.9 | +0.03 | S-N |
| 23 | EM|20/60|ha/3m|D|close [X2 : target 50->20 (4 step)] | +1.07 | +15.46 / +6.47 | +0.00/+0.00/+0.00 | +0.00/+0.00/+0.00 | 0.0 | -0.08 | --N |
| 24 | KB|60/75|range/8|G|close [X3 : target 50->60 (1 step)] | +1.49 | +2.81 / +1.00 | +0.00/+0.00/+0.00 | +0.00/+0.00/+0.00 | 0.0 | +0.01 | --N |
| 25 | STM(m=3.5,n=10,tf=10)|60/60|ha/5m|D|nyam [X1 : bar] | +0.82 | -1.37 / -0.13 | -0.00/-0.00/-0.00 | +0.00/+0.00/+0.00 | 0.0 | +0.12 | --- |
| 26 | KB|90/75|range/8|G|close [X3 : target 50->90 (2 step)] | +9.48 | +16.52 / -5.16 | -0.00/-0.00/-0.00 | +0.00/+0.00/+0.00 | 0.0 | +0.05 | --- |
| 27 | EM|50/60|ha/5m|D|nyam [X2 : bar] | +1.93 | +5.67 / -0.90 | -0.00/-0.00/-0.00 | +0.00/+0.00/+0.01 | 0.0 | +0.04 | --- |
| 28 | EM|40/60|vol/500|D|london [X4 : stop 75->60 (1 step)] | +1.49 | +3.26 / +1.20 | -0.00/-0.00/-0.00 | -0.00/-0.00/-0.01 | 0.8 | +0.15 | STN |
| 29 | EM|60/60|ha/3m|D|asia [X2 : target 50->60 (1 step)] | +1.54 | +0.10 / +0.25 | -0.00/-0.00/-0.00 | -0.00/-0.01/-0.05 | 0.6 | +0.06 | --N |
| 30 | EM|40/50|vol/500|D|london [X4 : stop 75->50 (2 step)] | -1.01 | +2.15 / +1.65 | -0.00/-0.00/-0.01 | -0.00/-0.00/-0.01 | 1.3 | +0.09 | --N |
| 31 | EM|20/60|tc/2m|G|nyam [X5 : target 60->20 (5 step)] | +0.27 | +3.71 / -3.21 | -0.00/-0.00/-0.01 | -0.00/-0.00/-0.01 | 0.0 | -0.00 | --- |
| 32 | EM|50/40|ha/3m|D|asia [X2 : stop 60->40 (2 step)] | +0.59 | -1.73 / -1.12 | -0.00/-0.01/-0.01 | -0.01/-0.01/-0.05 | 0.4 | +0.10 | --- |
| 33 | KB|50/75|range/4|G|pre [X3 : bar] | -5.26 | +0.21 / -0.33 | -0.00/-0.01/-0.01 | -0.00/-0.01/-0.02 | 1.2 | +0.02 | --- |
| 34 | STM(m=3.5,n=10,tf=10)|60/60|tc/5m|G|asia [X1 : var D/G] | +6.47 | +0.78 / +4.99 | -0.00/-0.01/-0.01 | -0.00/-0.00/-0.01 | 2.5 | +0.08 | S-N |
| 35 | STM(m=3.5,n=10,tf=10)|60/60|tc/3m|D|asia [X1 : bar] | +1.49 | -5.81 / -4.48 | -0.00/-0.01/-0.01 | -0.01/-0.03/-0.09 | -1.6 | +0.04 | --- |
| 36 | EM|40/40|vol/500|D|london [X4 : stop 75->40 (3 step)] | -2.79 | -3.25 / -0.30 | -0.00/-0.01/-0.01 | -0.00/-0.01/-0.01 | 1.3 | +0.10 | --- |
| 37 | EM|50/75|vol/500|D|london [X4 : target 40->50 (2 step)] | +2.88 | +7.47 / +1.36 | -0.00/-0.01/-0.01 | -0.00/-0.01/-0.01 | 1.8 | +0.05 | STN |
| 38 | KB|50/75|range/8|D|pre [X3 : var D/G] | -6.42 | -8.96 / -3.50 | -0.00/-0.01/-0.01 | -0.00/-0.01/-0.01 | 0.6 | -0.11 | --- |
| 39 | KB|90/75|range/8|G|pre [X3 : target 50->90 (2 step)] | +0.02 | +0.38 / -13.11 | -0.00/-0.01/-0.02 | -0.00/-0.01/-0.01 | -0.2 | +0.00 | --- |
| 40 | KB|50/75|range/16|G|pre [X3 : bar] | -2.93 | -4.30 / -3.84 | -0.01/-0.01/-0.02 | -0.01/-0.02/-0.03 | 1.2 | +0.01 | --- |
| 41 | EM|40/60|tc/2m|G|london [X5 : target 60->40 (3 step)] | +1.40 | +1.18 / -0.83 | -0.01/-0.01/-0.02 | -0.00/-0.01/-0.01 | 2.1 | +0.16 | --- |
| 42 | KB|60/75|range/8|G|pre [X3 : target 50->60 (1 step)] | -0.51 | +2.81 / +3.24 | -0.01/-0.01/-0.02 | -0.01/-0.01/-0.02 | 3.5 | +0.10 | --N |
| 43 | EM|40/75|vol/1000|D|london [X4 : bar] | -2.36 | -6.39 / -6.18 | -0.01/-0.01/-0.03 | -0.01/-0.01/-0.02 | 1.7 | +0.16 | --- |
| 44 | EM|40/75|vol/1000|D|asia [X4 : bar] | +2.48 | +0.59 / -1.31 | -0.01/-0.02/-0.03 | -0.01/-0.02/-0.04 | 3.2 | +0.12 | --- |
| 45 | EM|40/60|ha/3m|D|nypm [X2 : target 50->40 (2 step)] | +0.40 | -9.46 / -5.85 | -0.01/-0.02/-0.03 | -0.01/-0.02/-0.03 | 2.3 | +0.05 | --- |
| 46 | EM|40/75|vol/500|G|london [X4 : var D/G] | -6.09 | +0.83 / -4.06 | -0.01/-0.02/-0.03 | -0.01/-0.02/-0.03 | 3.2 | +0.05 | --- |
| 47 | EM|20/60|tc/2m|G|london [X5 : target 60->20 (5 step)] | -1.85 | -2.61 / -5.25 | -0.01/-0.02/-0.04 | -0.01/-0.02/-0.03 | 1.5 | +0.14 | --- |
| 48 | EM|60/60|tc/2m|D|london [X5 : var D/G] | -3.03 | -0.53 / -3.74 | -0.01/-0.03/-0.05 | -0.01/-0.02/-0.04 | 4.0 | +0.03 | --- |
| 49 | KB|50/75|range/16|G|asia [X3 : bar] | -1.08 | -4.12 / -0.54 | -0.03/-0.05/-0.08 | -0.03/-0.06/-0.10 | 11.7 | +0.24 | --- |
| 50 | EM|40/40|vol/500|D|nypm [X4 : stop 75->40 (3 step)] | -1.31 | -7.06 / -6.47 | -0.03/-0.06/-0.10 | -0.03/-0.05/-0.09 | 5.1 | +0.04 | --- |
| 51 | KB|50/75|range/4|G|nypm [X3 : bar] | -0.56 | -4.03 / -1.46 | -0.03/-0.05/-0.09 | -0.03/-0.06/-0.09 | 12.3 | +0.03 | --- |

## 5. (v) 60% / 70% lists
See Page 1 item 5. Counts from DS3_SIXTY_RUN (v2): 89 runnable of 903 (0.60 list), 14 of 382 (0.70 list): EQR lots_factor 26, EINT2 13, THPC2 12, THL 10, UF-LOSS 14, L2SP 6, SPLIT 4, CUTWAIT 2, EXP1 1, UF-PROFIT 1. No row adds a trade stream; no ADD row.

## 6. NT8 specification: the pullback engines on alternative bars (what D7 needs built before TB4W_10 on Volume-500 / 10-minute and PE on volume bars can be hosted)

Status: SPEC ONLY, written from the research code and the existing identity specs (DS3_SPEC_TB4D, DS3_SPEC_TB4W_03, DS3_SPEC_TB4B, DS3_SPEC_PB3B_R5_P1 and `bars_eng/be_lib.py` eng_PE / `bars_cand2/pb` / `pb4_sig.py`). No new strategy, no new scored statistic. Nothing here has been run in NT8: the verdict "DELIVERABLE WITH CONDITIONS" of the parent specs carries over, the conditions (bar-construction fidelity, signal-tick timing) are listed in 6.8. Shadow only until the identity test in 6.9 passes. Position size is not part of the spec (research units: 1 contract, $20/pt NQ).

### 6.0 What D7 would host (the cells that were scored)
| id | engine | trigger series X | regime series | level | trigger | W | bracket | session scored | store row |
|---|---|---|---|---|---|---|---|---|---|
| TB4W-10/vol500 | TB4 pullback (widening group of the TB4D parent) | Volume 500 (BarsPeriodType.Volume 500) | Supertrend(10, 3.0) on 10-minute bars | EMA(20) of 1-minute closes ("E20_1") | T1 | 600 s | 60 / 60 OCO, flat 16:55 ET | all entry windows, mapped program series; store cell session chosen by the S3a rule | `pb|TB4W_10_volume_500_ST10_E20_1_T1_nvolume00` on `vol/500` |
| TB4W-10/tc10m | same engine | Time 10-minute bars (BarsPeriodType.Minute 10) | same | same | T1 | 600 s | 60 / 60 | store cell (asia chosen on PRE+X′) | same spec on `tc/10m` |
| PE/vol | PE = PB3B_R5_P1 pullback engine run on the bar type itself ("variant D" / "variant G" of BARS-ENG) | Volume 500 / 1000 / 2500, Heikin-Ashi Volume 1000 | Supertrend(10, 3.0) on the SAME bars (D) or on groups of round(5 x bpm) bars (G) | EMA(20) of the X-bar closes | arming-bar-extreme break | 30 min converted to bars | 60 / 60 | store cells (london / pre chosen on PRE+X′) | `bars_eng` `trades/<bar>__PE__{D,G}` |
"10-min" in the request is read as the regime frame k = 10 of TB4W_10 and, separately, as the trigger-bar size of the store cell on `tc/10m`; both rows are given because the research has both.

### 6.1 Instruments, series, calendar
- NQ front month, trade-tick data (Last), MergeBackAdjusted continuous contract, Calculate = OnBarClose on every series. $20/pt, tick 0.25. Time zone America/New_York; label day opens 18:00 ET (Sunday 18:00 opens Monday); the Globex session template must NOT break volume bars at the 17:00-18:00 maintenance hour except as below.
- Series on the strategy (BarsInProgress): 0 = X trigger series (Volume N, Tick, Range, Renko, Minute-10 or Heikin-Ashi of one of them); 1 = 1-minute NQ (EMA20 level, ATR references, gap test); 2 = regime series, k-minute (k = 10 for TB4W_10, 3 / 5 / 15 for other TB4 cells; PE variant G uses 5-minute-equivalent groups of X bars, see 6.5).
- Bar counter reset: at the 18:00 ET label-day change the running volume / tick count restarts and the partial bar of the old day is CLOSED and NEVER traded (the research flags it `partial`; D7 must not signal on it).
- Entry gate (all engines): signal-bar time of day ET < 15:00 or >= 18:05 (the research `okb`); no entry 15:00-18:04. Flat at 16:55 ET (market order at the first tick at or after 16:55:00, early-close days at the final bar of the day). The scored library entry window of the BARS-ENG harness is 18:00-15:15; the TB4 gate above is the one the TB4 cells were scored under.

### 6.2 Volume bar construction (the identity-critical part)
- NT8 `BarsPeriodType.Volume`, Value N (500 / 1000 / 2500). Contracts accumulate tick by tick; a trade that overflows N is SPLIT across bars and EACH bar it completes is a completed bar signalled on that same tick (the library's overflow-split rule; 534,660 of 534,661 volume-1000 replay bars matched the library's completing-tick timestamps).
- The library bars come from the aggressor-level tape (one row per trade event, size per event). NT8 volume bars are built from the Rithmic Last-tick stream; multi-fill trades can be aggregated differently, which moves every later boundary. Required check before anything is trusted: compare NT8's Volume-N bars for one full day with the box's `l2vast/ds3/out/bars/volume_<N>.parquet` (time of completion, OHLC); if more than a few percent of boundaries differ the cell is not reproduced.
- Realised bars per minute (bpm; bars / 1-minute bars, capped sample): Volume 500 = 0.83, Volume 1000 = 0.41, Volume 2000 = 0.21 (median bar 27 s / 55 s / 111 s). These are used by the PE window and group conversions in 6.5. They are sample averages, fixed constants of the cell, not live-adapting.

### 6.3 Shared indicators (formulas exactly as scored)
- EMA20 level (TB4): alpha = 2/21 on 1-minute closes of series 1, seeded with the first close (NT8 EMA(20) first-bar seed); the value of the last COMPLETED 1-minute bar at the signal tick. Both sides use the same level.
- Supertrend regime (TB4 form, `tb_lib.supertrend`): on the k-minute bars aligned to epoch-minute // k (clock-aligned :00/:10/... for k = 10): TR = max(H-L, |H-C[1]|, |L-C[1]|); ATR = Wilder(10), seeded with the SMA of the first 10 TR at index 9; hl2 = (H+L)/2; ub = hl2 + 3.0 ATR, lb = hl2 - 3.0 ATR; fub = ub if (ub < fub[1] or Close[1] > fub[1]) else fub[1]; flb = lb if (lb > flb[1] or Close[1] < flb[1]) else flb[1]; d = +1 if Close > fub[1], -1 if Close < flb[1] (PREVIOUS bar's bands), else d[1]; d = 0 before index 9. As-of: a k-minute bar's d is usable only from its close (bar start + k minutes). This is NOT the NT8 stock SuperTrend and NOT the PE/TE form below.
- Supertrend regime (PE / TE6 form, `sd_state.supertrend_te`, used by the PE engine and by the PB3B spec): ATR length 10 with first-bar seed (ATR[0] = H0-L0; ATR[i] = (ATR[i-1] x 9 + TR[i]) / 10), bands hl2 +/- 3.0 ATR with the same ratchet, direction flips compare the CURRENT bar's Close with the CURRENT bar's final band: d[0] = +1; if d == +1 and Close[i] < flb[i] then -1; if d == -1 and Close[i] > fub[i] then +1. The two forms differ; each engine uses its own and the research cells were scored with them.

### 6.4 TB4 pullback engine on an arbitrary X series (TB4W_10: X = Volume 500 or Minute 10; regime k = 10; level = EMA20 of 1-min closes; trigger T1)
State per side, evaluated on every COMPLETED X bar (OnBarClose, i.e. on the bar-completing tick for volume bars):
1. Regime d from 6.3 (TB4 form) as of the bar's completion time. d = 0: no setup. A change of d clears all arming.
2. Touch (d = +1): X.Low <= level; (d = -1): X.High >= level. A touch bar arms the setup and stores aL = completion time of the touch bar, hL = X.High (long) / lS = X.Low (short). Armed for W = 600 s after the MOST RECENT touch bar.
3. Trigger T1 (TB4W_10 / TB4D, `pb4_sig._fire`): on each completed X bar while armed (within W of the most recent touch bar) and not yet fired on this touch episode: long if the bar closes up (Close > Open) AND Close > level; short if it closes down (Close < Open) AND Close < level. One fire per touch episode; the episode re-arms only after a non-touch bar. (T2 for other cells: non-touch bar and Close > hL / < lS. T3: see DS3_SPEC_TB4B; neither is needed for TB4W_10.)
4. Signal = side at the firing bar, edge-triggered (a second consecutive firing bar of the same side is ignored).
5. Entry: flat book (no open position, and not before the previous trade's exit second), gate 6.1, bar not partial: MARKET order sent ON the completing tick of the signal bar; the research fill is that tick's price plus the mapped slippage (the S3a research numbers are on the M basis, costs inside). One trade at a time.
6. Bracket: STOP-MARKET 60 pt (240 ticks) and LIMIT target 60 pt (240 ticks) OCO from the fill price, placed on fill; first tick through a level decides, the stop wins an identical tick; flat at 16:55 ET; after any exit the next entry cannot be before the next whole second.
7. No reversal, no trailing, no break-even, no re-entry in the same touch episode.

### 6.5 PE (PB3B_R5_P1) engine run on volume (or Heikin-Ashi volume) bars: BARS-ENG variants
(As coded in `bars_eng/be_lib.py eng_PE`; this differs from the live 1-minute PE of DS3_SPEC_PB3B_R5_P1 in that the trigger and the EMA live on the X series, not on the 1-minute series.)
- Series: X = Volume N (or HA of it; HA bar = OHLC4 close, HA open recursion as `heikin()`); no 1-minute series is needed for the level.
- Regime d (PE / TE6 form, 6.3): variant D = Supertrend(10, 3.0) on the X bars themselves (ATR 10 counts X bars); variant G = on groups of g = max(1, round(5 x bpm)) consecutive X bars (Volume 500: g = 4, Volume 1000: g = 2, Volume 2000: g = 1 = same as D), using the last COMPLETED group as of each X bar. d = 0 forbids setups.
- Level: EMA(20) of the X-bar CLOSES (alpha 2/21, first-bar seed, includes the current bar).
- Gap rule: if the time between an X bar's signal time and the next bar's open exceeds 90 minutes, disarm.
- Touch (not armed, d != 0), long: Low[i] <= EMA20[i] AND Close[i-1] > EMA20[i-1]; short: High[i] >= EMA20[i] AND Close[i-1] < EMA20[i-1]. A touch ARMS on bar i with side = d, reference = High[i] (long) / Low[i] (short) (the arming bar's own extreme, fixed; never updated).
- Armed: on each later bar j: disarm if (bars since arming) > Wb or d changed (processing continues as not armed: bar j can arm anew); else trigger if High[j] > reference (long) / Low[j] < reference (short). On trigger the bar is the signal bar and the setup is spent (the signal bar does not arm). Window Wb = max(1, round(30 x bpm)) bars for event bars (Volume 500: 25 bars; Volume 1000: 12; Volume 2500: ~10), or 30 real minutes for time bars. Touches while armed are ignored.
- Entry: MARKET on the completing tick of the signal bar j (the library enters at t_sig = bar completion with the tick price, not at the intrabar break and not at the next bar's open); one position at a time across all sessions; entry window 18:00-15:15 ET; the session of the cell is the session of the signal time.
- Bracket 60 / 60 OCO from the fill, flat 16:55 ET, as 6.4 item 6.

### 6.6 NT8 implementation notes (what has to be written)
1. A strategy with `AddDataSeries` for the 1-minute and the k-minute regime series; X is the primary series (Volume N). Per-series state in `OnBarUpdate` keyed by `BarsInProgress`; the regime state machine runs only on series 2, the EMA20 level only on series 1, the arming/trigger machine only on series 0 (`Calculate.OnBarClose`).
2. Supertrend: custom indicator implementing the TB4 form for TB4 cells and the TE6 form for PE (two small classes, not NT8's stock SuperTrend). Back-adjusted prices only; recompute indicators from the first bar of the loaded range with 4 days of warm-up at least (the parent specs showed 0 mismatches at 4 d / 7 d / 14 d / 2 mo / 3 mo warm-up).
3. Order handling: `EnterLong/ShortMarket` on the completing tick of the signal bar, `SetStopLoss`/`SetProfitTarget` 240 ticks each (OCO), `ExitLong/Short` market at 16:55 ET; position limit one; no stacking.
4. D7 slots needed: (a) a bar-type slot on the entry engine (Volume N / Minute 10 / HA-Volume N as the X series); (b) a regime-frame slot (k minutes); (c) an entry-mode slot "pullback to EMA20 + trigger T1/T2" (D7 has the volume bar type and a Supertrend slot but NOT this entry mode: DS3_ORB_ASIA_D7 table row for TB4W_10); (d) the PE-on-bars mode (level on X closes, window in bars via bpm). Lots/risk: through the normal book lots property; no change to the lock engine (the research books are outside the combined lock in the S3a scoring, as the other alt-bar books).
5. Per-signal log for the identity test (fields): label day, signal bar completion time (ET, to the millisecond), side, d, level, reference (hL / lS / arming-bar extreme), touch time, trigger type, fill price, exit type, exit time.

### 6.7 What the S3a scoring says about hosting these (not a recommendation)
See the ADD table: the TB4W_10 `tc/10m` store cell and the PE volume-bar cells are scored there with their labels; hosting them needs 6.6 item 4 (a)-(d). Building the engine does not make the cells better; it makes them testable live.

### 6.8 Conditions that decide DELIVERABLE in a real NT8 Sim (inherited from DS3_SPEC_TB4D)
1. Volume-bar construction on the live Rithmic feed (6.2): boundary identity vs the box's bars.
2. Signal-tick timing: the research sends the market order on the tick that completes the bar; NT8 with OnBarClose on Volume bars processes the bar on the completing tick (confirm in Sim; some bar types fire on the first tick of the next bar). Latency-sensitive at second level (the library's +1 s / +2 s delayed-entry tests moved WF little for the parent cell).
3. Costs: market entries on this family cost 87-115 $/trade at 10 lots in the parent mapping; the S3a M basis has costs inside but is a mapped/measured-fill basis, not a direct L2 replay of these cells (TB4W_10 direct coverage is 6 of 37 months).

### 6.9 Identity test to run before the cells are shown any lots
(1) Bars: one full day of NT8 Volume-500 (and Minute-10) bars vs the library file: bar count, completion time, OHLC; report the share of boundaries that differ. (2) Signals: for the last 10 trading days of the capped window (label days 20260126-20260206) the `TB4W_10` / `PE` signal log vs the library signals (side and time to the second, bar-completion key); the parent specs reached 98-99.4% exact signals and < 1% trade mismatch. (3) Trades: entries within 15 s and side >= 90%, count within +/-5%, stop and target exactly 240 / 240 ticks, exit type and time. The capped-window signal CSVs for TB4W_10 on Volume-500 and PE on Volume-500 are NOT produced by S3a (that is a replay job on the tape; this file is the rule text).

## 7. Risk lines (window by window) for the headline rows

### PART I

**PART I: DN15 stop-fill u=1.55 exits Native 1.28** (lots 2; c* = 0.92)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 40.2→45.4 | 17.6→25.9 | n/a (<40 wk) | 47.6→51.0 | 2.29→1.76 | 3.1 / 1.0 | 10.4 / 5.9 |
| L6M | 28 | 44.8→50.0 | 19.4→25.9 | n/a (<40 wk) | 43.0→45.8 | 2.31→1.93 | 1.8 / 0.7 | 8.6 / 4.1 |
| HOLD | 32 | 42.2→46.0 | 93.5→135.7 | n/a (<40 wk) | 52.1→57.2 | 0.45→0.34 | 0.9 / -0.4 | 30.5 / 29.8 |
| PRE | 75 | 26.5→29.0 | 259.4→274.3 | -1,007→-1,074 | 62.5→68.1 | 0.10→0.11 | -0.7 / -0.2 | 3.1 / -10.4 |
| X′ | 44 | 10.0→10.3 | 63.6→86.3 | -401→-454 | 35.1→38.3 | 0.16→0.12 | -1.0 / -0.7 | 18.7 / 14.7 |
| ALL | 149 | 25.4→27.5 | 259.4→274.3 | -1,257→-1,385 | 54.8→59.8 | 0.10→0.10 | -0.5 / -0.4 | 3.1 / -10.4 |

**PART I: DN15 stop-fill u=1.55 exits join 2.45** (lots 2; c* = 0.90)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 40.2→44.9 | 17.6→26.1 | n/a (<40 wk) | 47.6→51.0 | 2.29→1.72 | -4.7 / 0.2 | 5.9 / 5.9 |
| L6M | 28 | 44.8→49.5 | 19.4→26.1 | n/a (<40 wk) | 43.0→45.8 | 2.31→1.90 | -3.4 / -0.1 | 4.1 / 4.1 |
| HOLD | 32 | 42.2→45.6 | 93.5→137.4 | n/a (<40 wk) | 52.1→57.2 | 0.45→0.33 | -3.8 / -1.1 | 23.8 / 30.3 |
| PRE | 75 | 26.5→28.6 | 259.4→277.1 | -1,007→-1,085 | 62.5→68.1 | 0.10→0.10 | -2.5 / -0.8 | -3.9 / -9.8 |
| X′ | 44 | 10.0→9.9 | 63.6→88.5 | -401→-461 | 35.1→38.3 | 0.16→0.11 | -2.4 / -1.1 | 24.2 / 16.1 |
| ALL | 149 | 25.4→27.1 | 259.4→277.1 | -1,257→-1,395 | 54.8→59.8 | 0.10→0.10 | -2.8 / -1.0 | -3.9 / -9.8 |

**PART I: PB7_HMA55_EMA1_T2_W60_s-3 DIRECT** (lots 2; c* = 0.90)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 40.2→41.9 | 17.6→31.3 | n/a (<40 wk) | 47.6→55.1 | 2.29→1.34 | -7.4 / -2.0 | 10.6 / 11.0 |
| L6M | 28 | 44.8→48.3 | 19.4→31.3 | n/a (<40 wk) | 43.0→49.8 | 2.31→1.54 | -4.6 / -0.7 | 8.8 / 9.2 |
| HOLD | 32 | 42.2→45.7 | 93.5→122.7 | n/a (<40 wk) | 52.1→60.7 | 0.45→0.37 | -3.7 / -0.5 | 10.6 / 18.5 |
| PRE | 75 | 26.5→29.4 | 259.4→275.3 | -1,007→-1,129 | 62.5→68.0 | 0.10→0.11 | -1.8 / 0.3 | -6.5 / -8.3 |
| X′ | 44 | 10.0→11.5 | 63.6→73.5 | -401→-444 | 35.1→38.8 | 0.16→0.16 | -1.0 / 0.5 | 10.7 / 3.5 |
| ALL | 149 | 25.4→28.0 | 259.4→275.3 | -1,257→-1,377 | 54.8→60.5 | 0.10→0.10 | -2.0 / 0.2 | -6.5 / -8.3 |

**PART I: PB7_PB5_depth_atr0.5_W15_s-3 DIRECT** (lots 2; c* = 0.96)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 40.2→40.7 | 17.6→30.3 | n/a (<40 wk) | 47.6→51.8 | 2.29→1.34 | -6.5 / -0.8 | 0.1 / 11.8 |
| L6M | 28 | 44.8→47.6 | 19.4→30.3 | n/a (<40 wk) | 43.0→46.6 | 2.31→1.57 | -3.2 / 1.3 | 1.5 / 10.0 |
| HOLD | 32 | 42.2→44.7 | 93.5→111.9 | n/a (<40 wk) | 52.1→57.4 | 0.45→0.40 | -2.4 / 1.2 | 3.7 / 14.9 |
| PRE | 75 | 26.5→28.7 | 259.4→249.1 | -1,007→-1,036 | 62.5→67.3 | 0.10→0.12 | -1.1 / 1.3 | -20.8 / -18.1 |
| X′ | 44 | 10.0→12.2 | 63.6→81.7 | -401→-421 | 35.1→38.5 | 0.16→0.15 | 0.3 / 1.8 | 26.1 / 15.6 |
| ALL | 149 | 25.4→27.7 | 259.4→249.1 | -1,257→-1,298 | 54.8→59.3 | 0.10→0.11 | -1.0 / 1.4 | -20.8 / -18.1 |

**PART I: OVERNIGHT NQ IBS_t20_n1** (lots 4; c* = 1.02)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 40.2→47.5 | 17.6→17.6 | n/a (<40 wk) | 47.6→48.2 | 2.29→2.71 | 6.6 / 7.6 | 0.7 / 0.1 |
| L6M | 28 | 44.8→50.7 | 19.4→19.4 | n/a (<40 wk) | 43.0→46.3 | 2.31→2.62 | 5.4 / 6.2 | -0.1 / 0.1 |
| HOLD | 32 | 42.2→47.3 | 93.5→93.6 | n/a (<40 wk) | 52.1→52.5 | 0.45→0.51 | 5.1 / 5.4 | -11.5 / 0.7 |
| PRE | 75 | 26.5→29.5 | 259.4→211.6 | -1,007→-977 | 62.5→63.7 | 0.10→0.14 | 3.0 / 3.1 | -47.4 / -46.7 |
| X′ | 44 | 10.0→13.2 | 63.6→70.9 | -401→-436 | 35.1→40.0 | 0.16→0.19 | 3.4 / 3.3 | 9.0 / 7.7 |
| ALL | 149 | 25.4→28.9 | 259.4→211.6 | -1,257→-1,250 | 54.8→56.6 | 0.10→0.14 | 3.6 / 3.7 | -47.4 / -46.7 |

**PART I: OVERNIGHT NQ_RSI2_t10** (lots 4; c* = 1.08)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 40.2→45.6 | 17.6→17.6 | n/a (<40 wk) | 47.6→47.9 | 2.29→2.60 | 1.4 / 6.3 | -1.9 / 0.4 |
| L6M | 28 | 44.8→49.1 | 19.4→19.4 | n/a (<40 wk) | 43.0→46.4 | 2.31→2.54 | 2.1 / 5.3 | 1.5 / 0.4 |
| HOLD | 32 | 42.2→45.9 | 93.5→93.5 | n/a (<40 wk) | 52.1→52.5 | 0.45→0.49 | 2.5 / 4.7 | -9.8 / 1.9 |
| PRE | 75 | 26.5→30.2 | 259.4→242.1 | -1,007→-950 | 62.5→63.9 | 0.10→0.12 | 4.1 / 4.3 | -23.4 / -12.5 |
| X′ | 44 | 10.0→10.5 | 63.6→86.5 | -401→-431 | 35.1→37.6 | 0.16→0.12 | -0.0 / 0.7 | 43.7 / 24.6 |
| ALL | 149 | 25.4→28.2 | 259.4→242.1 | -1,257→-1,232 | 54.8→56.4 | 0.10→0.12 | 2.6 / 3.4 | -23.4 / -12.5 |

**PART I: OVERNIGHT ES_RSI2_t10** (lots 4; c* = 1.06)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 40.2→45.0 | 17.6→17.6 | n/a (<40 wk) | 47.6→45.5 | 2.29→2.56 | -0.1 / 5.3 | -3.3 / 0.2 |
| L6M | 28 | 44.8→48.7 | 19.4→19.4 | n/a (<40 wk) | 43.0→44.2 | 2.31→2.51 | 1.1 / 4.4 | 0.9 / 0.2 |
| HOLD | 32 | 42.2→45.6 | 93.5→93.5 | n/a (<40 wk) | 52.1→51.9 | 0.45→0.49 | 1.6 / 3.9 | -9.8 / 1.0 |
| PRE | 75 | 26.5→28.8 | 259.4→247.7 | -1,007→-985 | 62.5→63.4 | 0.10→0.12 | 2.6 / 2.5 | -23.0 / -9.1 |
| X′ | 44 | 10.0→10.9 | 63.6→60.2 | -401→-410 | 35.1→36.3 | 0.16→0.18 | 0.6 / 1.0 | 12.5 / -2.7 |
| ALL | 149 | 25.4→27.5 | 259.4→247.7 | -1,257→-1,244 | 54.8→55.7 | 0.10→0.11 | 1.8 / 2.4 | -23.0 / -9.1 |

**PART I: top vi-PE row PE volume_500|PE|D|london** (lots 4; c* = 0.94)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 40.2→43.2 | 17.6→19.5 | n/a (<40 wk) | 47.6→50.6 | 2.29→2.22 | -2.8 / 1.1 | 2.7 / 1.0 |
| L6M | 28 | 44.8→46.9 | 19.4→13.1 | n/a (<40 wk) | 43.0→40.7 | 2.31→3.57 | -2.8 / 0.0 | -3.1 / -6.8 |
| HOLD | 32 | 42.2→44.4 | 93.5→90.8 | n/a (<40 wk) | 52.1→50.5 | 0.45→0.49 | -2.0 / 0.2 | -16.4 / -6.7 |
| PRE | 75 | 26.5→27.9 | 259.4→276.3 | -1,007→-1,077 | 62.5→66.5 | 0.10→0.10 | -1.2 / 0.2 | -1.0 / 4.6 |
| X′ | 44 | 10.0→10.3 | 63.6→77.9 | -401→-445 | 35.1→37.9 | 0.16→0.13 | -1.1 / -0.2 | 10.4 / 10.8 |
| ALL | 149 | 25.4→26.6 | 259.4→276.3 | -1,257→-1,316 | 54.8→57.5 | 0.10→0.10 | -1.4 / 0.1 | -1.0 / 4.6 |

**PART I: top vi-TB4W row pb TB4W_10_volume_500_ST10_E20_1_T1_nvolume00|tc/10m|M|asia** (lots 1; c* = 1.00)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 40.2→40.4 | 17.6→18.9 | n/a (<40 wk) | 47.6→49.7 | 2.29→2.14 | 0.2 / -0.1 | 1.3 / 1.2 |
| L6M | 28 | 44.8→45.3 | 19.4→18.9 | n/a (<40 wk) | 43.0→44.4 | 2.31→2.39 | 0.5 / 0.2 | -0.5 / -0.6 |
| HOLD | 32 | 42.2→42.6 | 93.5→96.8 | n/a (<40 wk) | 52.1→53.3 | 0.45→0.44 | 0.4 / 0.1 | 3.4 / 2.7 |
| PRE | 75 | 26.5→27.4 | 259.4→253.1 | -1,007→-1,000 | 62.5→63.3 | 0.10→0.11 | 0.8 / 0.6 | -6.3 / -8.2 |
| X′ | 44 | 10.0→10.2 | 63.6→71.3 | -401→-403 | 35.1→35.4 | 0.16→0.14 | 0.2 / 0.1 | 7.7 / 7.2 |
| ALL | 149 | 25.4→25.9 | 259.4→253.1 | -1,257→-1,266 | 54.8→55.6 | 0.10→0.10 | 0.6 / 0.4 | -6.3 / -8.2 |

**PART I: top iv row EM|60/40|tc/2m|G|london** (lots 4; c* = 0.90)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 40.2→40.5 | 17.6→17.6 | n/a (<40 wk) | 47.6→47.8 | 2.29→2.30 | -8.7 / -3.6 | 0.1 / -1.7 |
| L6M | 28 | 44.8→45.9 | 19.4→17.6 | n/a (<40 wk) | 43.0→43.7 | 2.31→2.62 | -6.7 / -3.2 | -1.8 / -3.5 |
| HOLD | 32 | 42.2→43.3 | 93.5→94.3 | n/a (<40 wk) | 52.1→53.2 | 0.45→0.46 | -5.8 / -2.9 | -14.9 / -8.1 |
| PRE | 75 | 26.5→26.4 | 259.4→310.3 | -1,007→-1,138 | 62.5→67.9 | 0.10→0.09 | -4.5 / -2.6 | 25.9 / 21.4 |
| X′ | 44 | 10.0→10.4 | 63.6→63.2 | -401→-495 | 35.1→39.6 | 0.16→0.17 | -2.0 / -0.6 | 5.2 / -6.4 |
| ALL | 149 | 25.4→25.7 | 259.4→310.3 | -1,257→-1,389 | 54.8→59.0 | 0.10→0.08 | -4.1 / -2.1 | 25.9 / 21.4 |

### PART II

**PART II: DN15 stop-fill u=1.55 exits Native 1.28** (lots 2; c* = 0.90)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 15.1→20.3 | 84.8→80.1 | n/a (<40 wk) | 51.1→52.9 | 0.18→0.25 | 3.4 / 2.7 | -17.1 / -14.4 |
| L6M | 28 | 18.2→23.5 | 84.8→80.1 | n/a (<40 wk) | 39.6→42.2 | 0.21→0.29 | 2.6 / 2.4 | -17.1 / -14.4 |
| HOLD | 32 | 18.2→22.1 | 84.8→103.0 | n/a (<40 wk) | 42.6→47.2 | 0.21→0.21 | 1.5 / 1.2 | 7.4 / 5.7 |
| PRE | 75 | 14.1→16.5 | 190.7→193.7 | -759→-846 | 46.7→52.0 | 0.07→0.09 | 0.3 / 0.5 | -16.5 / -20.6 |
| X′ | 44 | 5.2→5.5 | 126.5→115.5 | -392→-385 | 27.2→28.2 | 0.04→0.05 | -0.1 / -0.4 | -24.8 / -25.1 |
| ALL | 149 | 12.5→14.7 | 190.7→193.7 | -957→-1,091 | 41.4→45.7 | 0.07→0.08 | 0.4 / 0.4 | -16.5 / -20.6 |

**PART II: DN15 stop-fill u=1.55 exits join 2.45** (lots 2; c* = 0.86)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 15.1→19.8 | 84.8→80.8 | n/a (<40 wk) | 51.1→52.9 | 0.18→0.24 | 2.8 / 2.1 | -12.8 / -14.6 |
| L6M | 28 | 18.2→23.0 | 84.8→80.8 | n/a (<40 wk) | 39.6→42.2 | 0.21→0.28 | 2.0 / 1.8 | -12.8 / -14.6 |
| HOLD | 32 | 18.2→21.6 | 84.8→104.7 | n/a (<40 wk) | 42.6→47.2 | 0.21→0.21 | 0.9 / 0.6 | 7.1 / 6.2 |
| PRE | 75 | 14.1→16.1 | 190.7→195.5 | -759→-858 | 46.7→52.0 | 0.07→0.08 | -0.3 / -0.1 | -18.4 / -20.8 |
| X′ | 44 | 5.2→5.1 | 126.5→117.6 | -392→-392 | 27.2→28.2 | 0.04→0.04 | -0.4 / -0.8 | -22.1 / -24.3 |
| ALL | 149 | 12.5→14.2 | 190.7→195.5 | -957→-1,102 | 41.4→45.7 | 0.07→0.07 | -0.1 / -0.1 | -18.4 / -20.8 |

**PART II: PB7_HMA55_EMA1_T2_W60_s-3 DIRECT** (lots 2; c* = 0.86)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 15.1→16.8 | 84.8→93.1 | n/a (<40 wk) | 51.1→56.2 | 0.18→0.18 | 0.2 / -0.6 | -13.4 / -4.4 |
| L6M | 28 | 18.2→21.7 | 84.8→93.1 | n/a (<40 wk) | 39.6→43.6 | 0.21→0.23 | 1.0 / 0.6 | -13.4 / -4.4 |
| HOLD | 32 | 18.2→21.7 | 84.8→93.1 | n/a (<40 wk) | 42.6→49.1 | 0.21→0.23 | 1.0 / 0.5 | -5.6 / -4.4 |
| PRE | 75 | 14.1→16.9 | 190.7→185.1 | -759→-870 | 46.7→51.8 | 0.07→0.09 | 0.4 / 0.5 | -24.3 / -30.9 |
| X′ | 44 | 5.2→6.7 | 126.5→112.8 | -392→-391 | 27.2→29.8 | 0.04→0.06 | 0.9 / 0.6 | -29.5 / -29.2 |
| ALL | 149 | 12.5→15.1 | 190.7→185.1 | -957→-1,109 | 41.4→46.2 | 0.07→0.08 | 0.7 / 0.6 | -24.3 / -30.9 |

**PART II: PB7_PB5_depth_atr0.5_W15_s-3 DIRECT** (lots 2; c* = 0.92)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 15.1→15.6 | 84.8→104.3 | n/a (<40 wk) | 51.1→56.5 | 0.18→0.15 | -0.4 / -0.9 | 7.3 / 10.3 |
| L6M | 28 | 18.2→21.0 | 84.8→104.3 | n/a (<40 wk) | 39.6→46.4 | 0.21→0.20 | 1.4 / 0.9 | 7.3 / 10.3 |
| HOLD | 32 | 18.2→20.8 | 84.8→104.3 | n/a (<40 wk) | 42.6→50.2 | 0.21→0.20 | 1.1 / 0.7 | 7.3 / 10.3 |
| PRE | 75 | 14.1→16.3 | 190.7→172.9 | -759→-825 | 46.7→51.3 | 0.07→0.09 | 0.7 / 0.8 | -34.2 / -33.2 |
| X′ | 44 | 5.2→7.4 | 126.5→93.0 | -392→-370 | 27.2→28.8 | 0.04→0.08 | 2.1 / 1.5 | -42.4 / -41.9 |
| ALL | 149 | 12.5→14.8 | 190.7→172.9 | -957→-1,051 | 41.4→46.0 | 0.07→0.09 | 1.2 / 1.0 | -34.2 / -33.2 |

**PART II: OVERNIGHT NQ IBS_t20_n1** (lots 4; c* = 1.04)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 15.1→22.4 | 84.8→61.5 | n/a (<40 wk) | 51.1→44.4 | 0.18→0.36 | 7.9 / 7.1 | -23.3 / -23.8 |
| L6M | 28 | 18.2→24.1 | 84.8→61.5 | n/a (<40 wk) | 39.6→37.6 | 0.21→0.39 | 6.2 / 5.7 | -23.3 / -23.8 |
| HOLD | 32 | 18.2→23.4 | 84.8→61.5 | n/a (<40 wk) | 42.6→39.3 | 0.21→0.38 | 6.0 / 5.0 | -23.3 / -23.8 |
| PRE | 75 | 14.1→17.0 | 190.7→153.5 | -759→-799 | 46.7→50.9 | 0.07→0.11 | 3.1 / 2.8 | -38.1 / -38.6 |
| X′ | 44 | 5.2→8.4 | 126.5→128.5 | -392→-400 | 27.2→31.7 | 0.04→0.07 | 3.4 / 3.1 | 2.1 / 0.9 |
| ALL | 149 | 12.5→16.0 | 190.7→153.5 | -957→-966 | 41.4→44.0 | 0.07→0.10 | 3.8 / 3.4 | -38.1 / -38.6 |

**PART II: OVERNIGHT NQ_RSI2_t10** (lots 4; c* = 1.12)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 15.1→20.5 | 84.8→70.6 | n/a (<40 wk) | 51.1→47.6 | 0.18→0.29 | 8.4 / 5.9 | -16.7 / -12.3 |
| L6M | 28 | 18.2→22.5 | 84.8→70.6 | n/a (<40 wk) | 39.6→39.8 | 0.21→0.32 | 7.1 / 5.0 | -16.7 / -12.3 |
| HOLD | 32 | 18.2→22.0 | 84.8→70.6 | n/a (<40 wk) | 42.6→41.0 | 0.21→0.31 | 6.5 / 4.4 | -16.7 / -12.3 |
| PRE | 75 | 14.1→17.7 | 190.7→173.4 | -759→-763 | 46.7→49.6 | 0.07→0.10 | 5.7 / 4.2 | -7.7 / -12.6 |
| X′ | 44 | 5.2→5.7 | 126.5→139.8 | -392→-394 | 27.2→28.4 | 0.04→0.04 | 0.9 / 0.6 | 25.2 / 17.0 |
| ALL | 149 | 12.5→15.3 | 190.7→173.4 | -957→-932 | 41.4→43.1 | 0.07→0.09 | 4.5 / 3.2 | -7.7 / -12.6 |

**PART II: OVERNIGHT ES_RSI2_t10** (lots 4; c* = 1.14)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 15.1→19.9 | 84.8→61.5 | n/a (<40 wk) | 51.1→46.8 | 0.18→0.32 | 7.5 / 6.0 | -16.5 / -19.7 |
| L6M | 28 | 18.2→22.1 | 84.8→61.5 | n/a (<40 wk) | 39.6→37.9 | 0.21→0.36 | 6.4 / 5.2 | -16.5 / -19.7 |
| HOLD | 32 | 18.2→21.6 | 84.8→61.5 | n/a (<40 wk) | 42.6→40.3 | 0.21→0.35 | 5.8 / 4.7 | -16.5 / -19.7 |
| PRE | 75 | 14.1→16.3 | 190.7→178.9 | -759→-743 | 46.7→47.6 | 0.07→0.09 | 4.1 / 3.2 | -30.0 / -1.2 |
| X′ | 44 | 5.2→6.0 | 126.5→127.3 | -392→-389 | 27.2→27.6 | 0.04→0.05 | 1.5 / 1.2 | 11.3 / 8.3 |
| ALL | 149 | 12.5→14.6 | 190.7→178.9 | -957→-904 | 41.4→41.6 | 0.07→0.08 | 3.8 / 3.0 | -30.0 / -1.2 |

**PART II: top vi-PE row PE volume_500|PE|D|london** (lots 4; c* = 0.98)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 15.1→18.1 | 84.8→84.0 | n/a (<40 wk) | 51.1→53.4 | 0.18→0.22 | 2.3 / 1.8 | -9.5 / -6.4 |
| L6M | 28 | 18.2→20.3 | 84.8→84.0 | n/a (<40 wk) | 39.6→38.9 | 0.21→0.24 | 0.9 / 0.7 | -9.5 / -6.4 |
| HOLD | 32 | 18.2→20.4 | 84.8→84.0 | n/a (<40 wk) | 42.6→42.2 | 0.21→0.24 | 1.6 / 0.8 | -9.5 / -6.4 |
| PRE | 75 | 14.1→15.4 | 190.7→212.8 | -759→-849 | 46.7→53.0 | 0.07→0.07 | 0.2 / 0.4 | 12.1 / 7.8 |
| X′ | 44 | 5.2→5.5 | 126.5→113.5 | -392→-425 | 27.2→30.2 | 0.04→0.05 | 0.5 / -0.1 | -21.3 / -20.6 |
| ALL | 149 | 12.5→13.8 | 190.7→212.8 | -957→-1,027 | 41.4→45.5 | 0.07→0.06 | 0.6 / 0.3 | 12.1 / 7.8 |

**PART II: top vi-TB4W row pb TB4W_10_volume_500_ST10_E20_1_T1_nvolume00|tc/10m|M|asia** (lots 1; c* = 1.00)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 15.1→15.3 | 84.8→90.0 | n/a (<40 wk) | 51.1→53.0 | 0.18→0.17 | 0.2 / 0.1 | 5.2 / 4.8 |
| L6M | 28 | 18.2→18.7 | 84.8→90.0 | n/a (<40 wk) | 39.6→41.0 | 0.21→0.21 | 0.5 / 0.4 | 5.2 / 4.8 |
| HOLD | 32 | 18.2→18.6 | 84.8→90.0 | n/a (<40 wk) | 42.6→44.0 | 0.21→0.21 | 0.4 / 0.3 | 5.2 / 4.8 |
| PRE | 75 | 14.1→14.9 | 190.7→191.9 | -759→-765 | 46.7→47.5 | 0.07→0.08 | 0.8 / 0.8 | 1.2 / 0.3 |
| X′ | 44 | 5.2→5.4 | 126.5→122.4 | -392→-387 | 27.2→27.2 | 0.04→0.04 | 0.2 / 0.2 | -4.1 / -4.7 |
| ALL | 149 | 12.5→13.1 | 190.7→191.9 | -957→-962 | 41.4→42.1 | 0.07→0.07 | 0.6 / 0.5 | 1.2 / 0.3 |

**PART II: top iv row KB|50/75|range/8|D|asia** (lots 4; c* = 0.70)

| window | n wk | mean $k/wk base→new | maxDD $k base→new | worst-20 $k base→new | SD $k base→new | Calmar base→new | equal-risk Δmean $k (lot table / cont.) | equal-risk maxDD $k Δ (lot table / cont.) |
|---|---|---|---|---|---|---|---|---|
| L3M | 14 | 15.1→21.1 | 84.8→67.3 | n/a (<40 wk) | 51.1→52.0 | 0.18→0.31 | 2.9 / -1.4 | -48.0 / -41.2 |
| L6M | 28 | 18.2→22.9 | 84.8→67.3 | n/a (<40 wk) | 39.6→40.7 | 0.21→0.34 | -0.9 / -3.4 | -48.0 / -41.2 |
| HOLD | 32 | 18.2→22.1 | 84.8→95.1 | n/a (<40 wk) | 42.6→46.0 | 0.21→0.23 | -1.6 / -3.9 | -18.9 / -23.1 |
| PRE | 75 | 14.1→11.1 | 190.7→551.9 | -759→-1,371 | 46.7→63.8 | 0.07→0.02 | -5.7 / -6.9 | 142.5 / 166.8 |
| X′ | 44 | 5.2→9.2 | 126.5→78.3 | -392→-424 | 27.2→35.2 | 0.04→0.12 | 1.4 / 0.8 | -69.4 / -75.8 |
| ALL | 149 | 12.5→13.0 | 190.7→551.9 | -957→-1,478 | 41.4→53.6 | 0.07→0.02 | -2.8 / -4.1 | 142.5 / 166.8 |

## 8. Method notes, caveats, files
* Windows L3M 14 wk / L6M 28 / HOLD 32 / PRE 75 / X' 44 / ALL 149; PX = PRE+X' is the selection window for the honest ranking. Worst-20 is a tail measure only where >= 40 weeks (PRE, X', ALL).
* Session choice for alt-bar cells: highest PRE+X' mean per contract, n>=40, among asia/london/pre/nyam/nypm/close (chosen on PX only, so the recent windows are untouched by the choice).
* Alt-bar and pullback cells are M basis from the stored bar-engine daily series (measured 1-s fills, costs inside, target haircut 1.4-4.3 pt); they are NOT direct L2 replays. DN is the mapped series with a measured-slip overlay. PB7 is direct. Sleeves are the stored struct48/D1 LIVE-CAL trades.
* The pb store 'pl*' placebo specs and 1-minute cells are excluded. Identical series (e.g. bracket-sequence variants that never branch) are deduplicated in the chance null (3,320 of 4,209 wave-1 cells; 4,762 pb cells).
* Placebo and null are circular shifts (keep each book's return distribution and count, destroy calendar alignment); they are not a no-edge null unless demeaned (shown). Neither tests the books against a differently-specified engine.
* Multiplicity: the swept families are wave-1 (4,209 cell-sessions), pb store (4,792), sisters (28 x 2), program cells (17); best-of-N is in Table 3. Cumulative UF_TRIALS bookkeeping is not extended here (no new signal generation).
* Files: `out/better/s3a/` (tbl_*.md, scope_long_*.pkl = every scope row x lots x all metrics, placebo_*.pkl, null_*.pkl, fam_scores_*.pkl, wide_*.pkl, rank_*.pkl, spec_nt8_pullback_altbars.md, dead_lookup.txt); code `code/better_s3a/` (s3lib.py scoring, fam.py gates/null, run_all.py, run_null.py, build_tables.py, write_md.py, write_doc.py, base_run*.py). Re-run on a new base: `base_run_d7.py TAG` then `run_all.py FILE TAG; run_null.py TAG FILE; build_tables.py TAG FILE; write_md.py TAG FILE; write_doc.py TAG FILE OUT`.
