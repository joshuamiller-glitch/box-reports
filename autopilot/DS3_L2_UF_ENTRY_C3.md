# DS3_L2_UF_ENTRY_C3 - L2-UNTIL-FOUND cycle 3, ENTRY: time-staggered entry slices and the pull-z skip LEAD (agent UF-ENTRY, 2026-10-30)
Research only; UNTOUCHED never read. Prereg autopilot/UF_ENTRY_C3_prereg.md sha256 d2e1242008b9835c251cac34b6f76b441eaca4f9effd683bfe5cb71edfbe9aa0 (DECISIONS.md, before any cell statistic); 204 cells (192 staggered-slice + 12 pull-z), spec sha256 4569daec2d5aa60d327ae291d26bd824c6655129ac48d6bd4a2564d01bb8361e; PRE+X' selection out/uf/entry_c3/pre_sel.json (copy autopilot/UF_ENTRY_C3_PRESEL.json) sha256 f0ed57224398a69de35f582b74eb3c5382a1643cc934c7088efac85689f554ff logged before the one recent look. Masks, EQR frame, bases (N primary, LIVE-CAL = L, M), +pt = extra cost per slice fill j>=1 (charged to the cell AND the reference), MDE80 in parentheses as in cycles 1-2. References: the 70/30 split S, the cost-robust mix C (F.9/X8/no gate), market; every cell is scored vs all three. dead_lookup: 0 EXACT/NEAR hits; nearest = DIPENTRY timer entries and L2EA pulled book skips; no stored staggered-slice or pull-z cell.
Look-ahead: no day-level feature used (conditions are 1-s book/price at the decision second; pull-z uses months before the trade month). DS3_CAUSAL_TIMES.md (LEAKAUDIT) does not exist yet: cycle-1 G11 (htf_vwap_atr / htf_gap_eth) was UNVERIFIED; DS3_CAUSAL_TIMES.md has since been published (section 2d): htf_vwap_atr and htf_gap_eth are verified causal, so cycle-1 G11 is re-marked VERIFIED-CAUSAL for those features (sig_* rows not checked in that file).

## 0. Plain verdict
* **Time-staggering the entry is strictly worse than the split, worse than C and worse than market entry.** 0 of 192 staggered cells is >= 0 vs the split in L6M, HOLD or PRE (share >= 0: L6M 0%, HOLD 0%, PRE 0%, X' 5%). Means vs the split (N, +0 pt, equal risk): L6M -25.0k, HOLD -24.5k, PRE -19.6k; vs market -3.9k / -3.5k / -13.1k. Every schedule (A-L), every condition, every wait mode is negative; the least bad (H 0:.7/120:.3 'price no worse than the signal, drop') is -5.6k L6M and -18.5k PRE vs the split. Mechanism: the signals drift in the signal direction after the signal, so a fill 15-120 s later is at a worse price, and a book-with-trade condition selects the moments after the drift. The prediction of the prereg (all delay schedules negative) holds.
* **PRE-selected cell `UF3|PZ|C|half|z2.0`** (the only cell besides cell 202 eligible vs split, vs C and vs market at +1 pt in PRE and X'): the cost-robust mix C with HALF SIZE on trades whose own-side pulled_sup10 z >= 2.0 (3.9% of trades). It is NEGATIVE where it matters: vs C (N, +0 pt) 2026 -17.3k, L6M -3.5k, HOLD -1.6k, PRE +2.1k, X' +0.4k (MDE L6M 19.4k); vs the split -6.9k / -2.0k / -2.5k / +3.4k / +7.3k. Tier **BEST-AVAILABLE-NEGATIVE** (L6M and HOLD < 0 vs both bases; RC p 0.8+; cumulative 1.0).
* **The pull-z LEAD from UF-LOSS C3 is not an entry rule.** Its literal threshold (z >= 2 by my normalisation) fires on only 3.9% of SEL trades (UF-LOSS's z >= 2 skipped 17.7%: their normalisation differs; I matched the SKIP SHARE with z >= 1.2 = 18.1%, chosen without outcomes). Used as a skip on a plain market entry it is far below the split (+22.6k L6M vs market): z >= 1.2 skip on market: L6M -18.0k, HOLD -15.4k, PRE -9.2k vs the split (only +3.4k L6M vs market itself); z >= 2: L6M -31.9k. The per-trade PRE edge (+0.57 pt) does not survive the lock engine at equal risk: skipping 18% of signals removes more profit than it removes loss. As a modifier on S: skip z>=1.2 +5.4k L6M, +7.3k HOLD, +1.5k PRE, -2.9k X' vs the split (inside MDE 29k); half-size -1.4k / +1.5k / +0.9k / +1.8k.
* **Best of the pull-z cells (second eligible, rank 2 by SEL t, NOT hindsight-picked): `UF3|PZ|C|half|z1.2`** (C with half size on the 18% of trades with the highest own-side pull z; same eligibility set as the selected cell). vs C (N, +0 pt): 2026 -4.3k, L6M +5.0k (MDE 13.1k), HOLD +5.7k, PRE +3.7k, X' +0.7k; vs the split +6.5k / +6.8k / +5.0k / +5.0k / +7.6k; vs market +29.8k L6M, +28.0k HOLD. Positive in L6M, HOLD, PRE and X' vs C, also at +1 and +2 pt (vs C L6M +2.9k / +2.6k), negative only in the ~5-week 2026 window (-4.3k, MDE ~big). Not significant: single-test t vs C L6M 1.07, HOLD 1.35; CI(PRE) vs C [-7.3k, +14.2k]; placebo vs C P1 rank 0.85 / 0.80 / 0.95 / 0.75 (L6M/HOLD/PRE/X'), P2 0.55 / 0.60 / 0.90 / 0.70 (<0.95); cycle RC vs C max t 1.07, p 0.782, cum-adj p 1.000 (best UF3|PZ|C|half|z1.2); cumulative p 1.0 (N_cum = 146,546); year share of the delta 1.05 (2024 carries it; 2025 negative). Tier **BEST-AVAILABLE-NEGATIVE with a forward-watch LEAD flag**: it is one of 12 pull-z cells and the only one of this kind in the cycle with that sign pattern.
* Cost-robust base C stays the reference (C vs split +0 pt L6M +1.6k, HOLD -0.8k, PRE +1.2k, X' +6.9k; +2 pt +17.8k / +14.0k / +12.2k / +13.5k). Nothing in three cycles improves it beyond MDE.

## 1. SETTINGS TABLE (recent windows first)
| row | basis | +pt/slice fill | ref | 2026 (~5 wk) | L6M | HOLD | PRE | X' | c* |
|--|--|--|--|--|--|--|--|--|--|
| C + half size when pull-z >= 2.0 (PRE-selected) | N | 0 | vs split | -6.9k (21.7k) | -2.0k (21.3k) | -2.5k (19.0k) | +3.4k (11.1k) | +7.3k (9.9k) | 1.020 |
| C + half size when pull-z >= 2.0 (PRE-selected) | N | 0 | vs C | -17.3k (26.2k) | -3.5k (19.4k) | -1.6k (17.2k) | +2.1k (8.8k) | +0.4k (5.1k) | 0.993 |
| C + half size when pull-z >= 2.0 (PRE-selected) | N | 0 | vs market | +13.1k (40.5k) | +20.5k (23.9k) | +19.9k (22.5k) | +11.3k (12.4k) | +11.1k (10.6k) | 1.085 |
| C + half size when pull-z >= 2.0 (PRE-selected) | N | 1 | vs split | -6.4k (22.2k) | +8.0k (18.8k) | +6.5k (17.2k) | +9.0k (12.1k) | +10.9k (9.7k) | 1.045 |
| C + half size when pull-z >= 2.0 (PRE-selected) | N | 1 | vs C | -17.2k (25.7k) | -3.1k (19.2k) | -1.3k (17.0k) | +2.0k (9.2k) | +0.5k (5.2k) | 0.997 |
| C + half size when pull-z >= 2.0 (PRE-selected) | N | 1 | vs market | +11.6k (39.0k) | +18.3k (23.6k) | +17.8k (22.1k) | +8.5k (12.4k) | +9.0k (10.1k) | 1.075 |
| C + half size when pull-z >= 2.0 (PRE-selected) | N | 2 | vs split | -2.2k (27.8k) | +14.0k (21.6k) | +12.3k (19.6k) | +14.4k (12.6k) | +14.1k (10.0k) | 1.076 |
| C + half size when pull-z >= 2.0 (PRE-selected) | N | 2 | vs C | -17.5k (25.6k) | -3.5k (18.4k) | -1.7k (16.3k) | +2.0k (9.3k) | +0.6k (5.2k) | 0.998 |
| C + half size when pull-z >= 2.0 (PRE-selected) | N | 2 | vs market | +8.2k (36.3k) | +15.6k (23.4k) | +15.3k (21.7k) | +5.6k (12.4k) | +7.3k (10.1k) | 1.066 |
| C + half size when pull-z >= 2.0 (PRE-selected) | L | 0 | vs split | -17.8k (41.2k) | -0.8k (21.9k) | -0.9k (19.5k) | +3.6k (12.1k) | +5.5k (10.1k) | 1.017 |
| C + half size when pull-z >= 2.0 (PRE-selected) | L | 0 | vs C | -22.1k (19.3k) | -3.8k (18.1k) | -2.0k (16.0k) | +3.4k (9.8k) | +0.3k (5.2k) | 1.000 |
| C + half size when pull-z >= 2.0 (PRE-selected) | L | 0 | vs market | -2.8k (24.9k) | +17.9k (22.9k) | +17.9k (21.1k) | +10.3k (12.5k) | +8.8k (10.8k) | 1.072 |
| C + half size when pull-z >= 2.0 (PRE-selected) | L | 1 | vs split | -21.2k (40.8k) | +5.4k (23.0k) | +4.7k (20.7k) | +8.9k (13.0k) | +8.4k (9.5k) | 1.048 |
| C + half size when pull-z >= 2.0 (PRE-selected) | L | 1 | vs C | -22.1k (18.4k) | -3.4k (18.1k) | -1.6k (16.1k) | +5.1k (9.6k) | +0.4k (5.2k) | 1.007 |
| C + half size when pull-z >= 2.0 (PRE-selected) | L | 1 | vs market | -8.5k (22.7k) | +14.9k (22.9k) | +15.1k (20.9k) | +8.0k (12.4k) | +6.8k (10.3k) | 1.062 |
| C + half size when pull-z >= 2.0 (PRE-selected) | L | 2 | vs split | -21.1k (40.9k) | +10.5k (24.2k) | +9.8k (21.6k) | +13.7k (13.4k) | +10.6k (10.0k) | 1.075 |
| C + half size when pull-z >= 2.0 (PRE-selected) | L | 2 | vs C | -15.2k (24.9k) | -0.2k (16.6k) | +1.2k (14.7k) | +4.9k (9.6k) | -0.4k (6.1k) | 1.007 |
| C + half size when pull-z >= 2.0 (PRE-selected) | L | 2 | vs market | -10.2k (22.2k) | +13.0k (22.5k) | +13.3k (20.4k) | +5.2k (12.4k) | +4.4k (10.6k) | 1.051 |
| C + half size when pull-z >= 2.0 (PRE-selected) | M | 0 | vs split | -24.2k (24.1k) | +1.9k (21.7k) | +0.5k (19.8k) | +6.4k (11.4k) | +5.2k (9.3k) | 1.057 |
| C + half size when pull-z >= 2.0 (PRE-selected) | M | 0 | vs C | -8.6k (32.8k) | +0.4k (16.3k) | +1.1k (14.3k) | +5.1k (8.5k) | -0.5k (6.0k) | 1.012 |
| C + half size when pull-z >= 2.0 (PRE-selected) | M | 0 | vs market | -4.7k (38.1k) | +15.3k (22.3k) | +12.2k (20.3k) | +14.2k (12.8k) | +8.0k (9.6k) | 1.060 |
| C + half size when pull-z >= 2.0 (PRE-selected) | M | 1 | vs split | -29.1k (23.9k) | +5.1k (23.0k) | +3.5k (21.3k) | +13.0k (12.3k) | +7.4k (9.4k) | 1.082 |
| C + half size when pull-z >= 2.0 (PRE-selected) | M | 1 | vs C | -11.8k (29.2k) | -0.2k (16.3k) | +0.6k (14.3k) | +4.5k (8.4k) | -0.7k (6.1k) | 1.006 |
| C + half size when pull-z >= 2.0 (PRE-selected) | M | 1 | vs market | -9.6k (35.7k) | +12.2k (22.2k) | +9.3k (20.1k) | +11.4k (12.3k) | +6.4k (9.8k) | 1.048 |
| C + half size when pull-z >= 2.0 (PRE-selected) | M | 2 | vs split | -24.4k (24.5k) | +8.7k (23.4k) | +6.5k (22.0k) | +20.8k (12.8k) | +11.2k (9.7k) | 1.115 |
| C + half size when pull-z >= 2.0 (PRE-selected) | M | 2 | vs C | -13.3k (28.3k) | +0.3k (16.7k) | +1.0k (14.7k) | +4.4k (8.3k) | -0.6k (6.1k) | 1.003 |
| C + half size when pull-z >= 2.0 (PRE-selected) | M | 2 | vs market | -10.2k (36.7k) | +10.4k (21.8k) | +7.4k (19.6k) | +9.9k (12.1k) | +4.9k (9.8k) | 1.039 |
| C + half size when pull-z >= 1.2 (2nd eligible) | N | 0 | vs split | +6.5k (43.4k) | +6.8k (18.5k) | +5.0k (17.7k) | +5.0k (18.2k) | +7.6k (13.3k) | 1.102 |
| C + half size when pull-z >= 1.2 (2nd eligible) | N | 0 | vs C | -4.3k (43.1k) | +5.0k (13.1k) | +5.7k (11.9k) | +3.7k (15.2k) | +0.7k (10.2k) | 1.073 |
| C + half size when pull-z >= 1.2 (2nd eligible) | N | 0 | vs market | +27.4k (61.4k) | +29.8k (19.4k) | +28.0k (20.9k) | +13.1k (19.0k) | +11.4k (14.6k) | 1.172 |
| C + half size when pull-z >= 1.2 (2nd eligible) | N | 1 | vs split | +5.0k (44.9k) | +14.3k (15.8k) | +12.3k (16.3k) | +9.6k (18.3k) | +11.4k (13.4k) | 1.118 |
| C + half size when pull-z >= 1.2 (2nd eligible) | N | 1 | vs C | -6.3k (40.4k) | +2.9k (13.0k) | +4.3k (12.0k) | +2.5k (15.0k) | +0.9k (10.6k) | 1.066 |
| C + half size when pull-z >= 1.2 (2nd eligible) | N | 1 | vs market | +23.4k (54.7k) | +24.9k (18.6k) | +23.8k (19.8k) | +9.1k (18.4k) | +9.5k (14.4k) | 1.150 |
| C + half size when pull-z >= 1.2 (2nd eligible) | N | 2 | vs split | +9.4k (52.2k) | +20.6k (19.6k) | +18.4k (18.9k) | +12.9k (18.8k) | +14.5k (13.8k) | 1.140 |
| C + half size when pull-z >= 1.2 (2nd eligible) | N | 2 | vs C | -6.8k (38.5k) | +2.6k (13.9k) | +4.0k (12.7k) | +0.7k (15.4k) | +0.9k (10.5k) | 1.058 |
| C + half size when pull-z >= 1.2 (2nd eligible) | N | 2 | vs market | +19.7k (50.3k) | +22.2k (17.6k) | +21.4k (18.5k) | +4.2k (18.5k) | +7.7k (14.2k) | 1.130 |
| C + half size when pull-z >= 1.2 (2nd eligible) | L | 0 | vs split | +4.6k (49.9k) | +6.6k (17.7k) | +5.6k (16.5k) | +0.9k (18.5k) | +4.2k (13.8k) | 1.076 |
| C + half size when pull-z >= 1.2 (2nd eligible) | L | 0 | vs C | -0.1k (52.0k) | +3.5k (14.6k) | +4.4k (13.1k) | +0.7k (15.9k) | -1.1k (10.8k) | 1.058 |
| C + half size when pull-z >= 1.2 (2nd eligible) | L | 0 | vs market | +20.9k (53.0k) | +25.7k (18.2k) | +24.7k (18.4k) | +7.5k (18.7k) | +7.4k (15.1k) | 1.134 |
| C + half size when pull-z >= 1.2 (2nd eligible) | L | 1 | vs split | +2.0k (56.8k) | +12.9k (18.9k) | +11.6k (18.1k) | +6.1k (18.8k) | +7.4k (13.7k) | 1.108 |
| C + half size when pull-z >= 1.2 (2nd eligible) | L | 1 | vs C | +0.2k (51.8k) | +3.8k (14.5k) | +5.0k (13.2k) | +2.4k (15.5k) | -0.5k (11.3k) | 1.064 |
| C + half size when pull-z >= 1.2 (2nd eligible) | L | 1 | vs market | +15.1k (55.1k) | +22.5k (18.4k) | +22.1k (18.3k) | +5.2k (18.5k) | +5.8k (14.9k) | 1.123 |
| C + half size when pull-z >= 1.2 (2nd eligible) | L | 2 | vs split | +2.4k (56.5k) | +14.7k (19.6k) | +13.8k (18.3k) | +10.5k (19.0k) | +9.5k (14.0k) | 1.127 |
| C + half size when pull-z >= 1.2 (2nd eligible) | L | 2 | vs C | +6.8k (61.6k) | +3.6k (15.5k) | +4.9k (14.0k) | +1.9k (15.5k) | -1.4k (11.5k) | 1.055 |
| C + half size when pull-z >= 1.2 (2nd eligible) | L | 2 | vs market | +12.7k (53.6k) | +17.0k (17.4k) | +17.2k (17.1k) | +2.0k (18.3k) | +3.4k (15.0k) | 1.102 |
| C + half size when pull-z >= 1.2 (2nd eligible) | M | 0 | vs split | -5.9k (25.9k) | -0.5k (17.6k) | -0.8k (16.4k) | -1.0k (17.2k) | +4.5k (12.5k) | 1.053 |
| C + half size when pull-z >= 1.2 (2nd eligible) | M | 0 | vs C | +8.9k (42.2k) | -1.9k (12.7k) | -0.2k (11.5k) | -2.0k (13.1k) | -1.1k (10.6k) | 1.007 |
| C + half size when pull-z >= 1.2 (2nd eligible) | M | 0 | vs market | +13.7k (45.1k) | +12.9k (19.0k) | +10.9k (17.2k) | +6.7k (17.6k) | +7.4k (13.5k) | 1.056 |
| C + half size when pull-z >= 1.2 (2nd eligible) | M | 1 | vs split | -10.0k (21.7k) | +1.9k (18.3k) | +1.5k (17.5k) | +5.8k (17.2k) | +6.9k (12.6k) | 1.081 |
| C + half size when pull-z >= 1.2 (2nd eligible) | M | 1 | vs C | +5.9k (36.2k) | -3.2k (11.5k) | -1.3k (10.6k) | -2.1k (13.0k) | -1.1k (10.6k) | 1.005 |
| C + half size when pull-z >= 1.2 (2nd eligible) | M | 1 | vs market | +8.9k (40.5k) | +9.1k (18.7k) | +7.4k (16.8k) | +4.5k (17.1k) | +5.9k (13.6k) | 1.047 |
| C + half size when pull-z >= 1.2 (2nd eligible) | M | 2 | vs split | -5.8k (27.6k) | +4.5k (18.7k) | +3.7k (18.0k) | +13.3k (16.5k) | +10.6k (12.8k) | 1.111 |
| C + half size when pull-z >= 1.2 (2nd eligible) | M | 2 | vs C | +3.5k (33.3k) | -3.4k (11.0k) | -1.5k (10.3k) | -2.3k (12.7k) | -1.2k (10.6k) | 0.999 |
| C + half size when pull-z >= 1.2 (2nd eligible) | M | 2 | vs market | +7.2k (41.2k) | +6.6k (18.7k) | +4.8k (16.7k) | +2.9k (16.6k) | +4.4k (13.6k) | 1.035 |

### References
| row | basis | +pt/slice fill | ref | 2026 (~5 wk) | L6M | HOLD | PRE | X' | c* |
|--|--|--|--|--|--|--|--|--|--|
| split vs market | N | 0 | +20.5k (43.8k) | +22.6k (16.4k) | +22.6k (16.0k) | +7.7k (11.4k) | +3.3k (8.8k) | 1.064 |
| C (F.9 X8) vs market | N | 0 | +32.1k (41.5k) | +24.4k (15.1k) | +21.7k (17.0k) | +9.0k (10.6k) | +10.7k (9.5k) | 1.093 |
| C vs split | N | 0 | +10.9k (29.9k) | +1.6k (14.4k) | -0.8k (13.5k) | +1.2k (9.1k) | +6.9k (8.8k) | 1.027 |
| split vs market | N | 1 | +18.2k (39.5k) | +10.1k (15.5k) | +11.1k (14.8k) | -0.8k (11.4k) | -2.2k (8.7k) | 1.029 |
| C (F.9 X8) vs market | N | 1 | +30.2k (39.4k) | +21.7k (14.5k) | +19.2k (16.1k) | +6.4k (10.3k) | +8.5k (9.3k) | 1.079 |
| C vs split | N | 1 | +11.7k (26.2k) | +11.3k (12.0k) | +7.9k (12.5k) | +6.9k (9.7k) | +10.4k (9.3k) | 1.049 |
| split vs market | N | 2 | +10.4k (39.1k) | +1.8k (16.1k) | +3.1k (14.8k) | -8.6k (11.9k) | -6.7k (8.6k) | 0.991 |
| C (F.9 X8) vs market | N | 2 | +27.0k (37.4k) | +19.4k (14.2k) | +17.1k (15.5k) | +3.5k (10.2k) | +6.7k (9.3k) | 1.068 |
| C vs split | N | 2 | +16.7k (35.4k) | +17.8k (14.5k) | +14.0k (14.5k) | +12.2k (10.0k) | +13.5k (9.7k) | 1.078 |
| split vs market | L | 0 | +16.0k (44.4k) | +18.7k (15.9k) | +18.9k (15.5k) | +6.5k (11.9k) | +3.0k (8.8k) | 1.054 |
| C (F.9 X8) vs market | L | 0 | +21.0k (40.8k) | +22.0k (15.2k) | +20.0k (15.8k) | +6.7k (10.5k) | +8.5k (9.3k) | 1.072 |
| C vs split | L | 0 | +4.7k (47.6k) | +3.1k (13.1k) | +1.1k (12.1k) | +0.2k (8.8k) | +5.3k (8.6k) | 1.017 |
| split vs market | L | 1 | +13.0k (39.9k) | +9.4k (15.5k) | +10.4k (14.6k) | -1.0k (11.4k) | -1.7k (8.6k) | 1.014 |
| C (F.9 X8) vs market | L | 1 | +14.8k (31.7k) | +18.5k (14.1k) | +16.8k (14.4k) | +2.7k (10.3k) | +6.4k (9.1k) | 1.055 |
| C vs split | L | 1 | +1.8k (42.2k) | +8.9k (13.3k) | +6.4k (12.8k) | +3.6k (9.4k) | +7.9k (8.8k) | 1.041 |
| split vs market | L | 2 | +10.3k (36.4k) | +2.7k (16.1k) | +3.7k (14.6k) | -8.3k (11.2k) | -5.9k (8.7k) | 0.978 |
| C (F.9 X8) vs market | L | 2 | +5.6k (32.0k) | +13.2k (14.6k) | +12.1k (14.5k) | +0.1k (10.2k) | +4.9k (9.1k) | 1.044 |
| C vs split | L | 2 | -4.9k (34.8k) | +10.8k (13.0k) | +8.6k (12.3k) | +8.5k (9.8k) | +11.0k (9.2k) | 1.068 |
| split vs market | M | 0 | +19.5k (41.7k) | +13.4k (14.5k) | +11.6k (14.0k) | +7.8k (11.3k) | +2.8k (8.4k) | 1.003 |
| C (F.9 X8) vs market | M | 0 | +4.3k (35.4k) | +14.9k (17.0k) | +11.1k (16.4k) | +8.8k (11.6k) | +8.5k (9.4k) | 1.048 |
| C vs split | M | 0 | -15.2k (25.7k) | +1.5k (15.2k) | -0.6k (14.6k) | +1.0k (9.6k) | +5.7k (8.8k) | 1.045 |
| split vs market | M | 1 | +18.5k (44.1k) | +7.3k (14.5k) | +5.9k (14.2k) | -1.2k (11.5k) | -0.7k (8.5k) | 0.968 |
| C (F.9 X8) vs market | M | 1 | +2.7k (34.7k) | +12.4k (16.6k) | +8.7k (16.0k) | +6.7k (11.1k) | +7.1k (9.4k) | 1.042 |
| C vs split | M | 1 | -16.4k (34.0k) | +5.3k (17.1k) | +2.9k (16.8k) | +8.1k (10.1k) | +8.1k (8.9k) | 1.076 |
| split vs market | M | 2 | +12.6k (42.7k) | +2.4k (13.7k) | +1.3k (14.1k) | -9.5k (11.7k) | -5.5k (9.2k) | 0.931 |
| C (F.9 X8) vs market | M | 2 | +3.6k (34.6k) | +10.1k (16.4k) | +6.3k (15.7k) | +5.3k (10.9k) | +5.6k (9.4k) | 1.035 |
| C vs split | M | 2 | -9.7k (32.2k) | +8.3k (17.5k) | +5.4k (17.7k) | +15.9k (11.1k) | +11.9k (9.9k) | 1.112 |

### All 12 pull-z cells, N, +0 pt, vs the split / C / market
| cid | cell | ref | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|--|
| 192 | UF3|PZ|M|skip|z2.0 | vs | -42.6k (58.5k) | -31.9k (29.8k) | -29.2k (26.9k) | -1.5k (15.6k) | -3.5k (11.7k) |
| 192 | UF3|PZ|M|skip|z2.0 | vc | -52.1k (64.4k) | -32.6k (35.2k) | -27.6k (32.1k) | -2.6k (15.0k) | -10.2k (12.7k) |
| 192 | UF3|PZ|M|skip|z2.0 | vm | -24.9k (35.8k) | -11.3k (32.7k) | -8.5k (29.1k) | +6.2k (13.1k) | -0.4k (9.1k) |
| 193 | UF3|PZ|S|skip|z2.0 | vs | -25.2k (30.0k) | -16.5k (29.5k) | -13.6k (26.2k) | +3.4k (13.5k) | -1.7k (8.8k) |
| 193 | UF3|PZ|S|skip|z2.0 | vc | -35.1k (47.3k) | -17.7k (36.6k) | -12.4k (32.8k) | +2.1k (15.1k) | -8.4k (12.8k) |
| 193 | UF3|PZ|S|skip|z2.0 | vm | -6.3k (34.8k) | +5.1k (38.4k) | +8.1k (34.8k) | +11.3k (17.6k) | +1.5k (13.1k) |
| 194 | UF3|PZ|S|half|z2.0 | vs | -13.4k (24.5k) | -3.0k (17.3k) | -1.2k (15.4k) | +0.3k (8.8k) | -0.3k (5.9k) |
| 194 | UF3|PZ|S|half|z2.0 | vc | -23.7k (47.7k) | -4.6k (23.3k) | -0.3k (21.6k) | -0.9k (12.1k) | -7.0k (10.4k) |
| 194 | UF3|PZ|S|half|z2.0 | vm | +6.2k (48.0k) | +19.4k (24.8k) | +21.4k (22.2k) | +8.0k (13.6k) | +3.0k (10.4k) |
| 195 | UF3|PZ|C|skip|z2.0 | vs | -14.2k (28.7k) | -17.0k (30.5k) | -15.5k (27.2k) | +2.4k (15.4k) | +4.8k (11.8k) |
| 195 | UF3|PZ|C|skip|z2.0 | vc | -24.5k (32.4k) | -18.1k (33.4k) | -14.2k (29.6k) | +1.2k (13.2k) | -2.0k (9.1k) |
| 195 | UF3|PZ|C|skip|z2.0 | vm | +5.3k (19.9k) | +4.5k (36.6k) | +6.1k (33.7k) | +10.3k (16.7k) | +8.4k (12.9k) |
| 196 | UF3|PZ|C|half|z2.0 | vs | -6.9k (21.7k) | -2.0k (21.3k) | -2.5k (19.0k) | +3.4k (11.1k) | +7.3k (9.9k) |
| 196 | UF3|PZ|C|half|z2.0 | vc | -17.3k (26.2k) | -3.5k (19.4k) | -1.6k (17.2k) | +2.1k (8.8k) | +0.4k (5.1k) |
| 196 | UF3|PZ|C|half|z2.0 | vm | +13.1k (40.5k) | +20.5k (23.9k) | +19.9k (22.5k) | +11.3k (12.4k) | +11.1k (10.6k) |
| 197 | UF3|PZ|TA-px<=signal-wait60drop|skip|z2.0 | vs | -12.3k (73.8k) | -30.0k (36.6k) | -27.9k (32.8k) | -12.8k (17.5k) | -6.4k (16.1k) |
| 197 | UF3|PZ|TA-px<=signal-wait60drop|skip|z2.0 | vc | -22.6k (91.6k) | -30.8k (40.8k) | -26.3k (36.9k) | -13.7k (16.9k) | -13.0k (14.8k) |
| 197 | UF3|PZ|TA-px<=signal-wait60drop|skip|z2.0 | vm | +7.4k (74.2k) | -9.3k (40.9k) | -7.0k (36.3k) | -5.9k (16.7k) | -3.5k (15.3k) |
| 198 | UF3|PZ|M|skip|z1.2 | vs | +18.1k (76.1k) | -18.0k (31.0k) | -15.4k (28.3k) | -9.2k (24.2k) | -7.3k (20.0k) |
| 198 | UF3|PZ|M|skip|z1.2 | vc | +7.0k (75.4k) | -19.1k (30.3k) | -14.1k (28.2k) | -10.2k (22.7k) | -13.8k (18.9k) |
| 198 | UF3|PZ|M|skip|z1.2 | vm | +39.7k (82.2k) | +3.4k (32.1k) | +6.3k (29.4k) | -2.1k (23.8k) | -4.4k (19.2k) |
| 199 | UF3|PZ|S|skip|z1.2 | vs | +22.7k (46.5k) | +5.4k (25.8k) | +7.3k (23.9k) | +1.5k (22.7k) | -2.9k (18.2k) |
| 199 | UF3|PZ|S|skip|z1.2 | vc | +11.4k (43.9k) | +3.6k (29.3k) | +7.9k (26.5k) | +0.3k (22.2k) | -9.6k (19.1k) |
| 199 | UF3|PZ|S|skip|z1.2 | vm | +44.5k (62.8k) | +28.3k (34.1k) | +30.3k (32.8k) | +9.3k (24.8k) | +0.2k (21.0k) |
| 200 | UF3|PZ|S|half|z1.2 | vs | -1.3k (38.5k) | -1.4k (13.5k) | +1.5k (13.0k) | +0.9k (15.7k) | +1.8k (10.7k) |
| 200 | UF3|PZ|S|half|z1.2 | vc | -11.9k (56.2k) | -3.0k (18.3k) | +2.3k (17.6k) | -0.3k (15.6k) | -5.0k (12.9k) |
| 200 | UF3|PZ|S|half|z1.2 | vm | +19.1k (57.9k) | +21.1k (19.7k) | +24.2k (19.5k) | +8.7k (17.7k) | +5.3k (13.9k) |
| 201 | UF3|PZ|C|skip|z1.2 | vs | +47.2k (75.1k) | +8.2k (30.9k) | +7.9k (29.2k) | +2.9k (23.9k) | +4.5k (19.9k) |
| 201 | UF3|PZ|C|skip|z1.2 | vc | +35.3k (62.9k) | +6.4k (29.2k) | +8.5k (26.8k) | +1.7k (21.9k) | -2.4k (17.3k) |
| 201 | UF3|PZ|C|skip|z1.2 | vm | +70.7k (84.9k) | +31.4k (35.8k) | +31.0k (35.6k) | +10.9k (25.8k) | +8.1k (21.2k) |
| 202 | UF3|PZ|C|half|z1.2 | vs | +6.5k (43.4k) | +6.8k (18.5k) | +5.0k (17.7k) | +5.0k (18.2k) | +7.6k (13.3k) |
| 202 | UF3|PZ|C|half|z1.2 | vc | -4.3k (43.1k) | +5.0k (13.1k) | +5.7k (11.9k) | +3.7k (15.2k) | +0.7k (10.2k) |
| 202 | UF3|PZ|C|half|z1.2 | vm | +27.4k (61.4k) | +29.8k (19.4k) | +28.0k (20.9k) | +13.1k (19.0k) | +11.4k (14.6k) |
| 203 | UF3|PZ|TA-px<=signal-wait60drop|skip|z1.2 | vs | +47.1k (97.6k) | -6.1k (43.5k) | -6.7k (38.8k) | -14.7k (23.8k) | -10.4k (21.6k) |
| 203 | UF3|PZ|TA-px<=signal-wait60drop|skip|z1.2 | vc | +35.2k (107.1k) | -7.5k (44.0k) | -5.7k (39.1k) | -15.5k (22.3k) | -16.9k (20.0k) |
| 203 | UF3|PZ|TA-px<=signal-wait60drop|skip|z1.2 | vm | +70.5k (118.7k) | +16.1k (47.7k) | +15.5k (42.6k) | -7.9k (23.5k) | -7.7k (21.2k) |

### Staggered cells: means by schedule, condition and wait mode (vs the split, N, +0 pt, equal risk)
| sch | n | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| A | 16 | -11.5k | -24.1k | -23.7k | -18.6k | -6.6k |
| B | 16 | -5.5k | -22.0k | -21.6k | -20.3k | -6.7k |
| C | 16 | -13.4k | -30.5k | -29.0k | -19.6k | -5.7k |
| D | 16 | -8.0k | -25.5k | -25.9k | -21.2k | -6.2k |
| E | 16 | -1.0k | -25.6k | -26.6k | -24.5k | -6.8k |
| F | 16 | -19.5k | -26.9k | -25.7k | -17.0k | -4.9k |
| G | 16 | -13.0k | -21.1k | -21.5k | -14.1k | -4.6k |
| H | 16 | -0.6k | -18.6k | -18.6k | -23.5k | -6.2k |
| I | 16 | -10.5k | -29.1k | -27.4k | -22.1k | -3.8k |
| J | 16 | -10.1k | -20.5k | -20.6k | -13.7k | -5.0k |
| K | 16 | -22.1k | -29.4k | -28.2k | -16.7k | -7.5k |
| L | 16 | -5.6k | -26.2k | -25.6k | -24.1k | -6.1k |

| cond | n | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| 1of8 | 36 | -17.3k | -26.0k | -25.8k | -20.5k | -5.5k |
| delta10&30 | 36 | -8.1k | -29.4k | -28.4k | -24.1k | -6.5k |
| imb5>=.2 | 36 | -3.2k | -25.3k | -25.1k | -22.5k | -6.0k |
| none | 12 | -17.0k | -24.0k | -23.3k | -15.2k | -5.4k |
| px<=signal | 36 | -3.9k | -19.7k | -20.1k | -16.9k | -5.7k |
| veto-free | 36 | -15.5k | -24.6k | -23.8k | -15.5k | -5.6k |

| mode | n | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| - | 12 | -17.0k | -24.0k | -23.3k | -15.2k | -5.4k |
| drop | 60 | -2.8k | -27.0k | -27.2k | -26.3k | -7.8k |
| wait60drop | 60 | -8.9k | -23.7k | -23.2k | -17.8k | -4.0k |
| wait60mkt | 60 | -17.1k | -24.3k | -23.5k | -15.7k | -5.8k |

### Six staggered cells with the best L6M vs the split (SELECTED ON LOOKED DATA; all PRE-negative)
| cid | cell | ref | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|--|
| 122 | UF3|TH|px<=signal|drop | vs split | +29.1k (36.6k) | -5.6k (27.7k) | -7.8k (25.8k) | -18.5k (16.2k) | -0.1k (16.3k) |
| 123 | UF3|TH|px<=signal|wait60drop | vs split | +24.4k (39.0k) | -8.1k (21.7k) | -11.9k (21.0k) | -18.7k (12.8k) | -2.1k (15.5k) |
| 27 | UF3|TB|px<=signal|wait60drop | vs split | -9.5k (84.3k) | -9.5k (27.7k) | -10.1k (26.5k) | -20.2k (16.6k) | -4.9k (14.3k) |
| 106 | UF3|TG|px<=signal|drop | vs split | +15.6k (24.8k) | -9.5k (24.0k) | -12.1k (21.7k) | -9.2k (14.9k) | +1.3k (14.6k) |
| 97 | UF3|TG|imb5>=.2|drop | vs split | +20.9k (35.6k) | -10.8k (23.8k) | -12.4k (21.9k) | -18.9k (16.0k) | -1.9k (17.2k) |
| 75 | UF3|TE|px<=signal|wait60drop | vs split | +13.9k (100.5k) | -12.7k (35.9k) | -15.3k (33.3k) | -19.8k (21.1k) | -7.8k (17.6k) |

## 2. Placebo, RC, gates
* Placebo (rank = share of draws the real cell beats; delta vs the split or vs C):
| cell | placebo (20 draws) | ref | L6M | HOLD | PRE | X' | 2026 |
|--|--|--|--|--|--|--|--|
| UF3|TD|imb5>=.2|wait60drop | P1 random condition / random subset at the same rate: rank | vs | 0.65 | 0.60 | 1.00 | 0.95 | 0.55 |
| UF3|TD|imb5>=.2|wait60drop | P2 book bits / z shuffled within day: rank | vs | 0.40 | 0.20 | 1.00 | 0.65 | 0.60 |
| UF3|TF|px<=signal|drop | P1 random condition / random subset at the same rate: rank | vs | 1.00 | 1.00 | 1.00 | 0.95 | 0.35 |
| UF3|TG|px<=signal|drop | P1 random condition / random subset at the same rate: rank | vs | 0.95 | 0.95 | 1.00 | 0.95 | 0.85 |
| UF3|PZ|C|skip|z2.0 | P1 random condition / random subset at the same rate: rank | vc | 0.00 | 0.05 | 0.85 | 0.35 | 0.10 |
| UF3|PZ|C|skip|z2.0 | P1 random condition / random subset at the same rate: rank | vs | 0.00 | 0.05 | 0.85 | 0.35 | 0.10 |
| UF3|PZ|C|skip|z2.0 | P2 book bits / z shuffled within day: rank | vc | 0.00 | 0.00 | 0.75 | 0.20 | 0.05 |
| UF3|PZ|C|skip|z2.0 | P2 book bits / z shuffled within day: rank | vs | 0.00 | 0.00 | 0.75 | 0.20 | 0.05 |
| UF3|PZ|C|half|z2.0 | P1 random condition / random subset at the same rate: rank | vc | 0.45 | 0.70 | 0.80 | 0.70 | 0.10 |
| UF3|PZ|C|half|z2.0 | P1 random condition / random subset at the same rate: rank | vs | 0.45 | 0.70 | 0.80 | 0.70 | 0.10 |
| UF3|PZ|C|half|z2.0 | P2 book bits / z shuffled within day: rank | vc | 0.10 | 0.20 | 1.00 | 0.50 | 0.10 |
| UF3|PZ|C|half|z2.0 | P2 book bits / z shuffled within day: rank | vs | 0.10 | 0.20 | 1.00 | 0.50 | 0.10 |
| UF3|PZ|M|skip|z1.2 | P1 random condition / random subset at the same rate: rank | vs | 0.75 | 0.85 | 0.80 | 0.55 | 0.85 |
| UF3|PZ|M|skip|z1.2 | P2 book bits / z shuffled within day: rank | vs | 0.35 | 0.50 | 0.75 | 0.10 | 0.75 |
| UF3|PZ|S|half|z1.2 | P1 random condition / random subset at the same rate: rank | vs | 0.60 | 0.80 | 0.95 | 0.85 | 0.15 |
| UF3|PZ|S|half|z1.2 | P2 book bits / z shuffled within day: rank | vs | 0.15 | 0.15 | 0.75 | 0.70 | 0.20 |
| UF3|PZ|C|half|z1.2 | P1 random condition / random subset at the same rate: rank | vc | 0.85 | 0.80 | 0.95 | 0.75 | 0.40 |
| UF3|PZ|C|half|z1.2 | P1 random condition / random subset at the same rate: rank | vs | 0.85 | 0.80 | 0.95 | 0.75 | 0.40 |
| UF3|PZ|C|half|z1.2 | P2 book bits / z shuffled within day: rank | vc | 0.55 | 0.60 | 0.90 | 0.70 | 0.30 |
| UF3|PZ|C|half|z1.2 | P2 book bits / z shuffled within day: rank | vs | 0.55 | 0.60 | 0.90 | 0.70 | 0.30 |

  Staggered cells without a condition: placebo n/a (fail). Staggered rows with the best ranks (TF/TG 'price no worse than the signal') beat random timing at the same fill rate (rank 0.95-1.00) but are -9k..-15k vs the split in absolute terms: the condition is information, delaying is the loss.
* RC over the cycle's 204 cells (centred weekly deltas, 2000 draws): vs split N L6M max t 1.02, p 0.874, cum-adj p 1.000 (best UF3|PZ|C|half|z1.2); HOLD max t 0.85, p 0.909, cum-adj p 1.000 (best UF3|PZ|S|skip|z1.2); PRE max t 0.86, p 0.835, cum-adj p 1.000 (best UF3|PZ|C|half|z2.0). vs C N L6M max t 1.07, p 0.782, cum-adj p 1.000 (best UF3|PZ|C|half|z1.2); HOLD max t 1.35, p 0.632, cum-adj p 1.000 (best UF3|PZ|C|half|z1.2). vs market (base claim): N L6M max t 4.30, p 0.022, cum-adj p 1.000 (best UF3|PZ|C|half|z1.2). N_cum = 146,546 = 146,342 stored (UF_TRIALS) + 204.
* Gates for the selected cell vs C / vs split: CI(PRE) [-3.9k, +8.2k] / [-4.0k, +10.9k] (includes 0); year_share 1.52 / 0.73 (fail); maxDD(engine HOLD) 648k vs C 685k (pass) / 666k vs split 625k (fail); holdout_sign fail.
* D6 session cells (row attribution, N, c=1, $k/wk, no per-cell MDE), `C half z>=1.2` vs C:
| D6 session cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| KB asia | -6.9k | -3.2k | -2.8k | +1.1k | -0.4k |
| PE london | +3.8k | +1.3k | +1.0k | +0.3k | -0.5k |
| HM asia | -6.8k | -3.0k | -2.8k | +0.2k | -0.6k |
| HM nyam | +5.4k | +2.7k | +2.3k | +1.5k | +2.8k |
| SM asia | +0.1k | +0.1k | -0.1k | -0.7k | -0.4k |
| SM london | +2.9k | +0.7k | +0.6k | +0.5k | +0.2k |
| ST asia | -6.9k | -1.3k | +0.1k | -2.1k | -1.4k |
| WT london | +5.0k | +2.0k | +1.1k | +0.3k | -0.9k |

  `C half z>=2.0` (selected) vs C:
| D6 session cell | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|
| KB asia | -4.8k | -2.4k | -2.1k | +1.0k | -0.1k |
| PE london | +0.2k | +0.3k | +0.3k | -0.4k | +0.1k |
| HM asia | -6.8k | -3.8k | -3.5k | -0.3k | -0.5k |
| HM nyam | -0.5k | +2.3k | +2.0k | +1.1k | +1.1k |
| SM asia | -1.4k | -0.4k | -0.5k | -0.2k | -0.2k |
| SM london | +1.3k | +0.6k | +0.5k | +0.3k | +0.0k |
| ST asia | -7.9k | -2.3k | -0.9k | -1.2k | -0.1k |
| WT london | +4.2k | +1.4k | +1.2k | +0.7k | +0.1k |

## 3. What was learned
1. Delay is a cost. The post-signal drift makes every time-staggered schedule 20-30k/wk worse than the split at equal risk and 4-13k worse than market itself; conditions (book with the trade) and wait modes do not change that sign; price-conditioned fills ('no worse than the signal') are the least bad because they only buy pullbacks (the split's own mechanism, with a time lag).
2. The pull-z LEAD does not transfer from the per-trade loss view to the lock-engine entry view when used as a skip on the whole entry; as a half-size modifier on the cost-robust base at the share-matched threshold it is a small positive in L6M/HOLD/PRE (+5k, MDE 13k) that is not significant and negative in 2026. It stays a forward-watch LEAD and a candidate for the PROFIT/LOSS agents' own-side pulled/'sizing' work, not an entry rule.
3. z normalisation matters: UF-LOSS's z >= 2 and mine differ in rate by 4.5x; any D6 implementation must fix the exact z definition (log1p of 10-s cancelled size levels 1-10, support side, vs same 15-min ET bucket of prior calendar months, all-seconds distribution, n >= 300).
4. Floor unchanged after three cycles (~1,000 cells): the 70/30 split and its cost-robust form C are the ENTRY best; entry-time book information (lean, ES, cancel/refill, pulled z), add timing models (hazard), slice timing and L2-event triggers do not improve them beyond MDE.
## 4. Caveats
2026 ~5 weeks. c* on WF (EQR), SEL-only for selection. Kernel identity (market slice) reproduces the base: mean abs diff 0.003 pt, exit type agreement 99.997% (one outlier trade). Slice fills are market +1 tick at the decision second (no limit). Pull-z windows and normalisation are mine (the LOSS agent's table was not reused). Placebo draws 20.
## 5. Files
code l2vast/ds3/code/uf/ufe3_pull.py (pull-z), ufe3_kernel.py (staggered slices), ufe3_cells.py, ufe3_run.py, ufe3_stageA.py, ufe3_stageB.py, ufe3_plac.py, ufe3_gates.py, ufe3_report.py; outputs l2vast/ds3/out/uf/entry_c3/ ; cells l2vast/ds3/prereg/UF_ENTRY_C3_cells.csv.
