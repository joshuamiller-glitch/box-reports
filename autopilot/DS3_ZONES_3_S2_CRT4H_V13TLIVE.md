# DS3_ZONES_3_S2_CRT4H_V13TLIVE - CRT4h 60pts fw2 any on V13T_LIVE proper, reconciled with Z1's CRT term (Z2, 2026-11-02 ~16:45Z). POST-HOC, Shadow only, nothing is a PASS
Prereg `l2vast/ds3/prereg/ZONES3_S2_CRT4H_V13TLIVE_prereg.md` sha256 3febf442fc8d1cd65f28ba5cd83c4ca44d3df1bafaaf88db310d793b4a7aa9c3 (in DECISIONS.md before any statistic here). Engine d7_v13t.run_v13t_live (xcost 0.80, stopcost 2.45, tshort 0, lines empty, lock none, lockfix legs); code `l2vast/ds3/code/zones3/s2/crt_rec.py, crt_an.py, crt_null.py`; data `l2vast/ds3/out/zones3/s2/v12/crt_rec.pkl, crt_an.md, crt_null.md`.
## Page 1 - plain sentences
**Label: LEAD, L6M/HOLD only; FRAGILE in D; NOT RISK-KEEP (RISK-KEEP needs L6M AND PRE; PRE maxDD is not cut) and the best-of-N null does not separate it from the best cell of a no-information grid.** On V13T_LIVE proper the cell halves the CRT 4h midpoint line when it is fresh, formed within 2 h and within 60 pts (replacing the shipped D20 fresh any-age term): L6M maxDD 150.7 -> 117.1k (-22%), HOLD -20%, MID -9%, PRE -1%, X' -4%; at equal risk (lots x1.047, ALL worst-20 matched) the mean is +2.6k/wk L6M, +2.5k HOLD, +1.0k MID, +0.2k PRE, +0.4k X'. The PA9 band confirms the L6M/HOLD cut (+23.9% / +23.1% mean over 9 lock-reset phases, 9/9 positive, above the 5%-flip band 0.219 / 0.205) and shows PRE (+0.1%) and X' (-1.3%) inside noise. **But the cut IS the L6M episode:** with ISO weeks W29..W39 dropped the cell's L6M maxDD cut falls from +22% to +4% (94.0k vs 90.6k; dropping W37 alone leaves +23%). The dollar gain inside the episode is real (July 2026 +39.9k, November +20.8k, February +14.7k, April +14.8k; 11 of the last 14 months positive, two small negatives), and it is carried by London (P6 London -26.7k of the L6M series maxDD), not Asia.
**Reconciliation with Z1.** Z1's FRAGILE verdict is about the SHIPPED CRT D20 HALF term (leave-one-out, S vs OFF): in my run it reads L6M +7%, HOLD +7%, MID +35%, PRE +1%, X' -22%, mean -34 $/wk: a small, episode-dependent term, so I agree it is FRAGILE. The cell tested here is a different rule: shipped term = fresh CRT midpoint of ANY age within 20 pts (587 live-lot rows); cell = fresh CRT midpoint formed <= 2 h within 60 pts (940 rows; 390 shared, 550 new, 197 dropped). The age rule alone does nothing (D20 fw2: -0%; D40 fw2 +1%), the 60-pt window alone is most of it (D60 fresh any age: +36% L6M, but +19% without W37 and -1% with W29-W39 dropped); the combination gives +22%. Across the D ladder at fw2: 10/15/20/30/40 pts -4/0/0/0/+1%, 60 pts +21%, 25/50/75% of target 0/0/+2%: **the effect exists at one D only (FRAGILE in D)**, and 60 pts is the end of my pts ladder (no 80/100 tested).
**Best-of-N (selection priced).** Under shuffled-day line sets (29 worlds, 126-cell reduced grid per world incl. C) the maximum L6M cut of the grid has median +17.4% (min +8.7%, max +45.3%) against the real +20.9%: share of worlds >= real 0.47; among STRICT/TOLERANT cells the null median is +8.0% (max +32.6%) against +20.9%, share 0.13. So the size of the cut is what the best of a ~120-cell grid reaches by chance about half the time; the cell-level placebos (ranks 0.02-0.03 on L6M, 0.01-0.02 on HOLD, none on PRE/X') say it is better than random half-sizing of the same size, but they do not price the choice among cells. Resolution: 29 worlds (the order asked for >= 100; limited by compute, 3,810 engine runs).
**Verdict:** keep in Shadow as a recent-regime (L6M/HOLD) LEAD with London as the carrying session; do not promote; it does not meet the L6M-and-PRE bar.

## Tables
### 1. Rows on V13T_LIVE proper (xcost 0.80, stopcost 2.45, lockfix legs, lock none): mean $/wk | maxDD $k | Calmar by window; cut vs S (the shipped layer)

| row | L3M | L6M | HOLD | MID | PRE | X' | cut L6M / HOLD / MID / PRE / X' |
|---|---|---|---|---|---|---|---|
| S | 14.7/94.0/0.16 | 36.7/150.7/0.24 | 30.4/150.7/0.20 | 24.0/43.7/0.55 | 17.3/166.2/0.10 | 4.8/92.5/0.05 | +0% / +0% / +0% / +0% / +0% |
| OFF | 13.8/91.4/0.15 | 36.8/161.6/0.23 | 30.2/161.6/0.19 | 22.7/66.9/0.34 | 16.8/167.3/0.10 | 5.2/75.7/0.07 | -7% / -7% / -53% / -1% / +18% |
| C | 14.8/90.6/0.16 | 38.1/117.1/0.33 | 32.1/120.9/0.27 | 25.8/40.0/0.64 | 17.7/168.0/0.11 | 5.0/88.8/0.06 | +22% / +20% / +9% / -1% / +4% |
| C_D20fw2 | 14.5/91.4/0.16 | 37.1/151.4/0.25 | 30.9/151.4/0.20 | 25.1/41.3/0.61 | 17.5/166.2/0.11 | 5.1/88.8/0.06 | -0% / -0% / +6% / +0% / +4% |
| C_D40fw2 | 14.5/90.8/0.16 | 37.2/148.6/0.25 | 31.5/148.6/0.21 | 25.7/42.1/0.61 | 18.1/168.7/0.11 | 5.2/80.3/0.07 | +1% / +1% / +4% / -2% / +13% |
| C_D60fresh | 16.0/94.9/0.17 | 38.3/96.4/0.40 | 32.2/124.9/0.26 | 25.6/42.7/0.60 | 17.4/167.9/0.10 | 4.7/91.7/0.05 | +36% / +17% / +2% / -1% / +1% |

Z1's variant (the SHIPPED CRT D20 HALF term; leave-one-out = S vs OFF): cut L6M / HOLD / MID / PRE / X' = +7% / +7% / +35% / +1% / -22%; Calmar gain +7% / +8% / +62% / +3% / -24%; mean d L6M -34 (MDE 1573).

### 2. L6M maxDD cut vs S with weeks dropped (carrying episode ISO 2026-W29..W39; W37 alone), and the L6M window of the 16 remaining weeks

| row | cut L6M full | cut with W37 dropped | cut with W29-W39 dropped | cell maxDD / S maxDD ($k) with W29-W39 dropped |
|---|---|---|---|---|
| OFF | -7% | -9% | +3% | 91.4 / 94.0 |
| C | +22% | +23% | +4% | 90.6 / 94.0 |
| C_D20fw2 | -0% | -0% | +3% | 91.4 / 94.0 |
| C_D40fw2 | +1% | +2% | +3% | 90.8 / 94.0 |
| C_D60fresh | +36% | +19% | -1% | 94.9 / 94.0 |

### 3. Phase-averaged (Z3 PA9: week key shifted -4..+4 label days, ship and cell re-run per phase, paired); band = 95th pct |maxDD cut| of the random-flip placebo (DS3_ZONES_3_NOISE_V13T_FINAL: 2% / 5% flips)

| row | window | PA9 mean cut (min..max) | phases > 0 | band 2% / 5% | above band? |
|---|---|---|---|---|---|
| OFF | L6M | -2.4% (-7.2%..+5.2%) | 2/9 | 0.188 / 0.219 | no (inside noise) |
| OFF | HOLD | -2.4% (-7.2%..+5.2%) | 2/9 | 0.182 / 0.205 | no (inside noise) |
| OFF | PRE | -1.2% (-3.1%..+0.7%) | 2/9 | 0.078 / 0.099 | no (inside noise) |
| OFF | X' | +5.0% (+0.4%..+18.2%) | 9/9 | 0.145 / 0.182 | no (inside noise) |
| C | L6M | +23.9% (+17.3%..+34.2%) | 9/9 | 0.188 / 0.219 | yes (> 5% band) |
| C | HOLD | +23.1% (+17.3%..+34.2%) | 9/9 | 0.182 / 0.205 | yes (> 5% band) |
| C | PRE | +0.1% (-3.3%..+4.1%) | 4/9 | 0.078 / 0.099 | no (inside noise) |
| C | X' | -1.3% (-11.2%..+7.3%) | 5/9 | 0.145 / 0.182 | no (inside noise) |

### 4. Equal-risk (lots x1.047 through the engine lot table so the ALL-window worst-20 equals S's; achieved ratio 0.982)

| window | mean S $/wk | mean C at equal risk | equal-risk mean change | maxDD S | maxDD C(equal risk) |
|---|---|---|---|---|---|
| L3M | 14740 | 15806 | +1065 | 94.0 | 88.9 |
| L6M | 36747 | 39371 | +2624 | 150.7 | 95.8 |
| HOLD | 30405 | 32903 | +2498 | 150.7 | 115.7 |
| MID | 24008 | 24967 | +959 | 43.7 | 35.6 |
| PRE | 17285 | 17520 | +236 | 166.2 | 166.3 |
| X' | 4801 | 5172 | +370 | 92.5 | 73.8 |

### 5a. Per calendar month: C minus S ($ total in the month), last 14 months

| month | 202509 | 202510 | 202511 | 202512 | 202601 | 202602 | 202603 | 202604 | 202605 | 202606 | 202607 | 202608 | 202609 | 202610 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| delta $k | +2.3 | +0.5 | +20.8 | +1.5 | +2.6 | +14.7 | -3.9 | +14.8 | +4.1 | -7.8 | +39.9 | +1.6 | +0.1 | -1.1 |

### 5b. Per book x session (C minus S): mean $/wk and series maxDD change ($k) in L6M, HOLD, PRE, X'

| book | session | d mean L6M | d mean HOLD | d mean PRE | d mean X' | d maxDD L6M | d maxDD HOLD | d maxDD PRE | d maxDD X' |
|---|---|---|---|---|---|---|---|---|---|
| K6 | asia | +198 | -32 | -84 | +66 | -1.2 | -1.2 | -0.7 | -2.9 |
| K6 | london | +105 | +39 | -38 | +67 | +0.6 | +0.5 | +1.3 | -0.0 |
| K6 | nyam | +104 | +78 | +36 | -6 | +0.8 | -0.5 | -0.8 | +0.0 |
| K6 | nypm | +62 | +32 | -4 | +22 | -1.7 | -1.7 | +3.0 | -0.9 |
| P6 | asia | +147 | +487 | +73 | -165 | -4.9 | -4.2 | +3.3 | +7.3 |
| P6 | london | +649 | +411 | +149 | +0 | -26.7 | -1.1 | -11.2 | +0.0 |
| P6 | nyam | +0 | +296 | +189 | -92 | +0.0 | +0.0 | +1.6 | +0.0 |
| U6 | asia | +428 | +226 | +74 | +294 | -0.7 | +0.0 | -3.3 | +0.0 |
| U6 | london | +48 | +61 | +59 | -14 | -0.7 | -0.7 | -1.4 | +0.0 |
| H6 | asia | -245 | +7 | -20 | +40 | -0.4 | -0.4 | -1.0 | -1.2 |
| H6 | nyam | -39 | +9 | -57 | -12 | -0.5 | +0.1 | +0.7 | +0.5 |
| M6 | london | +5 | +3 | +8 | +0 | -0.1 | -0.1 | -0.1 | +0.0 |
| M6 | nyam | +0 | -2 | +0 | -1 | +0.0 | +0.0 | +0.0 | +0.0 |
| A6 | asia | -103 | +62 | +44 | +27 | +2.8 | +2.3 | +0.0 | +0.0 |

By session (all books summed): 
asia: L6M: d mean +426, d maxDD -8.8k; PRE: d mean +87, d maxDD -0.1k | 
london: L6M: d mean +808, d maxDD -19.4k; PRE: d mean +177, d maxDD -14.0k | 
nyam: L6M: d mean +65, d maxDD -1.9k; PRE: d mean +168, d maxDD +4.9k | 
nypm: L6M: d mean +62, d maxDD -1.7k; PRE: d mean -4, d maxDD +3.0k | 

### 6. Best-of-N null
Null worlds complete: 29 (each: 7 lines x 9 D x {fresh, fw2} = 126 cells, all line features of the world permuted within book x session x td-bin x side strata; per-world shipped layer = its own base; V13T default engine as in the screen). Real reduced grid: 119 changed cells; max L6M cut +20.9%, max among STRICT/TOLERANT +20.9%; the cell C = +20.8%.

| statistic | real | null min / median / max | share of null worlds >= real |
|---|---|---|---|
| max L6M cut over the grid | +20.9% | +8.7% / +17.4% / +45.3% | 0.47 (n=29) |
| max L6M cut among STRICT/TOLERANT cells | +20.9% | +1.0% / +8.0% / +32.6% | 0.13 (n=29) |
| max HOLD cut over the grid | +20.9% | +5.4% / +17.4% / +47.8% | 0.43 (n=29) |
| rank of C's own cut (+20.8%) against the null maxima | - | - | 0.47 |

Caveats: single-ISO-week boundaries use in-window days only; the PA9 phases shift the lock week key (-4..+4 label days), the cost phases of Z3's band are not re-run here; the null uses V13T (xcost .995) as in the screen, the table rows V13T_LIVE.
