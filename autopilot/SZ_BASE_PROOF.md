**PLAIN VERDICT (3 sentences, for the user).** No: sizing is not independent of the exit rule - in the exact engine a lot change moves 82-86% of the affected trades' $ per lot and 6-7% of their exit types (cut counts 5,384 vs 4,731-5,566), so the old-looking signs on S3 (Q1-A shallowest, ladder L -46%, vol-target +29%) are mostly lot arithmetic, and the base itself did change (cuts 56% -> 38% of exits, stops 3% -> 14%, Q1-A L6M maxDD 105k -> 82k), with every family top cell losing most of its edge on the old base (rule-based recompute: A/B leaders keep their cut on volatility but ER cells flip to a mean cost, rank correlation new vs old 0.11-0.44). Defects found: first-order pnl-per-lot scaling cannot see exits (overstates up-size mean by $290k-$820k per 26 months; screen only, exact runs needed), the S3 page dropped carrying weeks before maxDD (L1M = L2M = L3M identical; corrected table in section 7), exact-driver multiplier table unmatched for 4-8% of re-entry signals, and J min/product duplicate cells; nothing is identical to the old page to the dollar and the fixes (all-weeks rescoring done here, exact re-runs ordered) are listed in section 4.

# SZ_BASE_PROOF - is sizing independent of the exit rule, or was something wrong? (SZ-BASE, 2026-11-09 ~16:50Z)
**Post-hoc, Shadow only, no PASS claims. PRE-PROOF (entries not live-matched). Trade-level numpy work only; no exact engine run by SZ-BASE.**

**VERDICT (plain).** The base DID change, a lot (table below): old DS3 S4A engine (V13T ts2, 21,397 trades, 54-57% of exits are per-print TH-L2 cuts) vs S1b-COMB (21,135 trades, 38% state cuts, stop exits 3% -> 14%, X' cuts 51% -> 18%); maxDD of Q1-A L6M 105k -> 82k, PRE 88k -> 140k, X' 81k -> 122k; never-cut NOCUT maxDD L6M 222k -> 191k. So S3 did not run on the old base. Sizing is NOT independent of the exit rule: (a) in the EXACT engine lots change which exit fires (matched trades with changed lots: 82-86% change $ per lot, 6-7% change exit type, state-cut count 5384 -> 4731 sizer-off / 5432 ladder L / 5566 vol-target over 26 months), and first-order overstates the up-size mean by $290k-$820k per 26 months and understates the ladder drawdown (L6M cut: L -43 first-order vs -76 exact, B -73 vs -143); (b) the SIGNS of the reference rows (L and B deeper than Q1-A, vol-target shallower) repeat on every base because they are mostly lot arithmetic (L adds 33% lots, B 64%, vol-target removes 14%) - they are not evidence of exit independence; magnitudes move 20-30 points across bases and "sizer off" even changes sign (L6M cut +2 V0, -34 COMB, +9 NOCUT, +17 UNIF).
**What was wrong (DEFECTS, details section 4):** D1 first-order pnl-per-lot scaling cannot see exits (sz_core.daily, s3_sizer.scale_pnl): screen only, fails on every up-size row - exact engine needed (already ordered by the lead). D2 DS3_TH_S3_SIZER_S1B.md (S3 page): windows L1M = L2M = L3M identical to the dollar for every cell, because instr2_eval drops weeks 202629-39 from the weekly vector BEFORE maxDD (all-weeks rule broken; maxDD there is a 5-week path). Not a cached old trade list; but S3 maxDD/cuts must be re-read from the all-weeks rescore (here). D3 exact driver keys the multiplier table by (book, signal second) of the Q1-A base trades: signals created by changed exits (re-entries, blackout) are not matched (4-8% of exact trades) and get m = 1, and the table is applied after the Q1-A ladder (rounding differs from first-order). D4 J family: min/product pairs of 0/1 multipliers give identical cells (1,318 of 1,573 J rows share their result with another row), inflating the J count and J family p. No cell is identical to the old page to the dollar (0 of 4,110 down-only rescored cells; 133 zero-change cells are 0 on both).
**Old-vs-new for cells (task 2):** the new first-order top-5 of every family do NOT carry to the old base: median cut collapses (example A: +36% mean new cut L6M vs -2% on old V0, +20% on replica HOLD); cut correlation new vs old V0 0.41 (HOLD 0.76), equal-mean-cut rank correlation 0.27 (HOLD 0.55); the top-ranked cells fall to ranks 60-900 of their family. Reading: the first-order "top" is largely in-sample selection plus base-specific exits; no family result is base-independent. Transfer caveat: old trades carry the new M only where the signal matches (V0 59%, HOLD 78%; unmatched M = 1), so old numbers are biased toward smaller changes. Files: /mnt/l2/l2vast/_th_sz/sz_base_old.parquet (old = V0; hold_* = replica HOLD).

## 1. Base-change proof (stack ex O7 for like-for-like; windows as of 2026-11-09, data to 20261030; trades by label day of exit)
Old bases: V0 = research ts2 reference behind DS3_SIZER S4A (run_v13t_ts2; ledger /mnt/l2/l2vast/ds3_base4/defects/kfix/V0_off.pkl = 21,397 trades, $2,520,149.07, ties to the S4A Q1-A row 104,809 / 26,999 L6M exactly; V0_off_nocut.pkl = cut off); replica HOLD = /mnt/l2/l2vast/_th_state/base_b/HOLD (old live per-print cut on the S1b engine). New: S1b-COMB / NOCUT / UNIF.

**Window L6M**

| base | trades | cuts (n / %) | target % | stop % | lock/stack % | other % | mean trade $ | mean lots | $/wk | maxDD $ |
|--|--|--|--|--|--|--|--|--|--|--|
| OLD V0 (DS3 S4A engine) Q1-A | 4919 | 2788 / 56.7 | 39.0 | 3.4 | 0.8 | 0.1 | 147 | 2.13 | 27858 | 104809 |
| OLD V0 NOCUT | 4347 | 0 / 0.0 | 51.6 | 46.3 | 1.6 | 0.5 | 82 | 2.14 | 13738 | 222071 |
| OLD replica HOLD | 5028 | 2723 / 54.2 | 40.8 | 3.5 | 1.4 | 0.2 | 108 | 2.15 | 20789 | 121515 |
| NEW S1b-COMB | 4595 | 1756 / 38.2 | 45.3 | 13.5 | 2.6 | 0.3 | 137 | 2.14 | 24164 | 81955 |
| NEW S1b-NOCUT | 4035 | 0 / 0.0 | 51.4 | 42.1 | 6.1 | 0.4 | 106 | 2.20 | 16467 | 190667 |
| NEW S1b-UNIF | 4400 | 1230 / 28.0 | 47.2 | 20.9 | 3.5 | 0.4 | 86 | 2.16 | 14504 | 181551 |

**Window HOLD**

| base | trades | cuts (n / %) | target % | stop % | lock/stack % | other % | mean trade $ | mean lots | $/wk | maxDD $ |
|--|--|--|--|--|--|--|--|--|--|--|
| OLD V0 (DS3 S4A engine) Q1-A | 8811 | 5002 / 56.8 | 38.5 | 3.3 | 0.8 | 0.7 | 123 | 2.14 | 20870 | 122025 |
| OLD V0 NOCUT | 7885 | 0 / 0.0 | 51.6 | 46.1 | 1.5 | 0.8 | 88 | 2.16 | 13415 | 222071 |
| OLD replica HOLD | 9084 | 5029 / 55.4 | 39.7 | 3.2 | 1.4 | 0.3 | 82 | 2.15 | 14356 | 121515 |
| NEW S1b-COMB | 8258 | 3082 / 37.3 | 44.6 | 14.7 | 2.9 | 0.5 | 99 | 2.15 | 15746 | 105692 |
| NEW S1b-NOCUT | 7190 | 0 / 0.0 | 50.7 | 42.6 | 6.1 | 0.7 | 81 | 2.21 | 11220 | 190667 |
| NEW S1b-UNIF | 7758 | 1926 / 24.8 | 47.1 | 23.5 | 4.0 | 0.6 | 76 | 2.17 | 11400 | 181551 |

**Window PRE**

| base | trades | cuts (n / %) | target % | stop % | lock/stack % | other % | mean trade $ | mean lots | $/wk | maxDD $ |
|--|--|--|--|--|--|--|--|--|--|--|
| OLD V0 (DS3 S4A engine) Q1-A | 7814 | 4202 / 53.8 | 39.7 | 3.3 | 0.5 | 2.7 | 127 | 2.16 | 13202 | 88180 |
| OLD V0 NOCUT | 7367 | 0 / 0.0 | 52.8 | 43.9 | 0.8 | 2.5 | 134 | 2.16 | 13170 | 174642 |
| OLD replica HOLD | 8829 | 5092 / 57.7 | 38.5 | 2.3 | 0.9 | 0.6 | 65 | 2.08 | 7681 | 156758 |
| NEW S1b-COMB | 7719 | 2479 / 32.1 | 46.2 | 17.6 | 2.5 | 1.5 | 133 | 2.11 | 13681 | 139604 |
| NEW S1b-NOCUT | 6883 | 0 / 0.0 | 51.3 | 41.6 | 5.1 | 2.0 | 136 | 2.15 | 12515 | 126622 |
| NEW S1b-UNIF | 7105 | 908 / 12.8 | 49.7 | 31.3 | 4.3 | 1.9 | 146 | 2.15 | 13816 | 133429 |

**Window X'**

| base | trades | cuts (n / %) | target % | stop % | lock/stack % | other % | mean trade $ | mean lots | $/wk | maxDD $ |
|--|--|--|--|--|--|--|--|--|--|--|
| OLD V0 (DS3 S4A engine) Q1-A | 2928 | 1496 / 51.1 | 37.5 | 4.7 | 0.1 | 6.6 | 49 | 2.07 | 3293 | 80802 |
| OLD V0 NOCUT | 2887 | 0 / 0.0 | 47.2 | 45.1 | 0.2 | 7.4 | 41 | 2.08 | 2688 | 113305 |
| OLD replica HOLD | 3402 | 1900 / 55.8 | 38.1 | 2.3 | 0.9 | 2.8 | 62 | 1.98 | 4757 | 74347 |
| NEW S1b-COMB | 2878 | 522 / 18.1 | 45.2 | 27.5 | 4.0 | 5.1 | 29 | 2.04 | 1917 | 121660 |
| NEW S1b-NOCUT | 2767 | 0 / 0.0 | 47.4 | 40.8 | 5.9 | 5.9 | 30 | 2.04 | 1888 | 135482 |
| NEW S1b-UNIF | 2769 | 40 / 1.4 | 47.5 | 39.5 | 5.8 | 5.8 | 35 | 2.04 | 2172 | 131397 |

**Window L1M**

| base | trades | cuts (n / %) | target % | stop % | lock/stack % | other % | mean trade $ | mean lots | $/wk | maxDD $ |
|--|--|--|--|--|--|--|--|--|--|--|
| OLD V0 (DS3 S4A engine) Q1-A | 612 | 344 / 56.2 | 37.6 | 4.4 | 1.6 | 0.2 | 18 | 2.06 | 2719 | 62576 |
| OLD V0 NOCUT | 559 | 0 / 0.0 | 48.8 | 49.6 | 1.4 | 0.2 | -55 | 2.08 | -7733 | 90456 |
| OLD replica HOLD | 680 | 396 / 58.2 | 38.7 | 1.6 | 1.3 | 0.1 | 17 | 2.10 | 2856 | 60865 |
| NEW S1b-COMB | 586 | 229 / 39.1 | 44.0 | 14.2 | 2.7 | 0.0 | 3 | 2.07 | 479 | 76892 |
| NEW S1b-NOCUT | 492 | 0 / 0.0 | 48.2 | 44.5 | 7.1 | 0.2 | -101 | 2.15 | -12406 | 112054 |
| NEW S1b-UNIF | 573 | 162 / 28.3 | 45.5 | 21.8 | 4.2 | 0.2 | -91 | 2.09 | -13006 | 103369 |

**Window MID**

| base | trades | cuts (n / %) | target % | stop % | lock/stack % | other % | mean trade $ | mean lots | $/wk | maxDD $ |
|--|--|--|--|--|--|--|--|--|--|--|
| OLD V0 (DS3 S4A engine) Q1-A | 1970 | 1128 / 57.3 | 38.2 | 3.2 | 0.7 | 0.6 | 103 | 2.19 | 16851 | 59703 |
| OLD V0 NOCUT | 1748 | 0 / 0.0 | 51.5 | 46.7 | 1.5 | 0.3 | 53 | 2.22 | 7690 | 91353 |
| OLD replica HOLD | 2039 | 1123 / 55.1 | 39.7 | 3.3 | 1.7 | 0.2 | 86 | 2.22 | 14582 | 88606 |
| NEW S1b-COMB | 1853 | 685 / 37.0 | 44.8 | 14.9 | 3.0 | 0.3 | 94 | 2.24 | 14469 | 84998 |
| NEW S1b-NOCUT | 1609 | 0 / 0.0 | 50.5 | 43.6 | 5.5 | 0.4 | 71 | 2.26 | 9558 | 131510 |
| NEW S1b-UNIF | 1724 | 397 / 23.0 | 47.6 | 24.4 | 4.6 | 0.3 | 116 | 2.24 | 16613 | 113625 |

Zero-rule row = never-cut NOCUT (old V0 NOCUT vs S1b-NOCUT): maxDD L6M 222.1k vs 190.7k, HOLD 222.1k vs 190.7k, PRE 174.6k vs 126.6k, X' 113.3k vs 135.5k; no cut exits in either (stop 46% vs 42%). With the cut, stack maxDD (Q1-A row): L6M 104.8k (V0) / 121.5k (HOLD) / 82.0k (COMB); PRE 88.2k / 156.8k / 139.6k; X' 80.8k / 74.3k / 121.7k.

## 2. Reference rows: same recipe on every base (first-order, S3 harness s3_sizer.run on each trade list; all-weeks maxDD, ex O7; cut % vs Q1-A of the same base, + = shallower; equal-mean = global lot scale to Q1-A L6M mean)

| base | cell | cut L6M | PRE | X' | d mean L6M $/wk | eq-mean cut L6M | PRE | X' |
|--|--|--|--|--|--|--|--|--|
| OLD V0 (DS3 S4A engine, cut) | sizer off | 2.3 | -24.5 | -120.6 | 4439 | 15.8 | -7.3 | -90.1 |
| OLD V0 (DS3 S4A engine, cut) | old ladder L | -67.5 | -61.6 | -8.2 | 7680 | -26.7 | -22.2 | 18.2 |
| OLD V0 (DS3 S4A engine, cut) | B (x1/x1.5) | -55.9 | -58.8 | -84.3 | 12680 | -1.7 | -3.6 | -20.2 |
| OLD V0 (DS3 S4A engine, cut) | ZL-1 vol-target | 4.2 | 32.6 | -1.4 | -2362 | -6.4 | 25.1 | -12.6 |
| OLD V0 NOCUT | sizer off | -20.5 | 5.4 | -53.4 | 1851 | -8.0 | 15.2 | -37.4 |
| OLD V0 NOCUT | old ladder L | -51.1 | -58.6 | -5.3 | 3358 | -17.2 | -23.0 | 18.3 |
| OLD V0 NOCUT | B (x1/x1.5) | -64.9 | -52.0 | -58.7 | 2686 | -30.0 | -19.9 | -25.1 |
| OLD V0 NOCUT | ZL-1 vol-target | 12.4 | 14.3 | 22.6 | 1301 | 22.0 | 23.7 | 31.0 |
| OLD replica HOLD | sizer off | -8.0 | -34.2 | -63.4 | 6978 | 21.9 | 2.9 | -18.2 |
| OLD replica HOLD | old ladder L | -65.8 | -45.5 | -22.5 | 4020 | -34.4 | -18.0 | 0.7 |
| OLD replica HOLD | B (x1/x1.5) | -55.2 | -73.5 | -62.7 | 13263 | 10.2 | -0.5 | 5.8 |
| OLD replica HOLD | ZL-1 vol-target | 22.9 | 20.8 | 18.3 | 985 | 26.7 | 24.7 | 22.3 |
| NEW S1b-COMB | sizer off | -34.3 | -7.9 | -70.9 | 8295 | 3.1 | 22.2 | -23.2 |
| NEW S1b-COMB | old ladder L | -42.7 | -48.9 | 13.0 | 5643 | -12.5 | -17.3 | 31.4 |
| NEW S1b-COMB | B (x1/x1.5) | -72.9 | -52.2 | -51.6 | 15590 | -0.1 | 11.9 | 12.2 |
| NEW S1b-COMB | ZL-1 vol-target | 12.7 | 19.8 | 47.3 | 705 | 15.2 | 22.2 | 48.9 |
| NEW S1b-NOCUT | sizer off | 9.0 | 9.2 | -70.1 | 9019 | 36.3 | 36.4 | -19.2 |
| NEW S1b-NOCUT | old ladder L | -58.2 | -70.4 | 15.5 | 2993 | -26.3 | -36.1 | 32.5 |
| NEW S1b-NOCUT | B (x1/x1.5) | -49.2 | -52.6 | -54.2 | 9294 | 16.3 | 14.4 | 13.5 |
| NEW S1b-NOCUT | ZL-1 vol-target | 23.8 | 23.7 | 35.6 | 1081 | 27.5 | 27.4 | 38.8 |
| NEW S1b-UNIF | sizer off | 17.2 | 10.6 | -71.3 | 8729 | 43.7 | 39.2 | -16.5 |
| NEW S1b-UNIF | old ladder L | -76.0 | -61.9 | 15.6 | 2305 | -42.5 | -31.1 | 31.6 |
| NEW S1b-UNIF | B (x1/x1.5) | -45.2 | -51.3 | -55.8 | 8439 | 21.9 | 18.6 | 16.2 |
| NEW S1b-UNIF | ZL-1 vol-target | 25.5 | 24.1 | 37.0 | 568 | 27.7 | 26.4 | 38.9 |

Exact engine (SZ-CORE rows, S1b-COMB): sizer off L6M cut -28.2 / d mean -2,367; ladder L -76.1 / -494; B -142.6 / +2,876; vol-target +28.3 / +10. Old S4A page (genuine PA9 on V13T ts2): vol-target +32.9 / +30.6 / +21.9 / +16.1 (L6M/PRE/MID/X'), d mean -0.3k L6M; first-order here on V0: +4.2 / +32.6 (all weeks; the page drops carrying weeks and uses its own phase). None equal to the dollar.
Tie-out: the harness reproduces V0 Q1-A total $2,520,149.07 and mean lots 2.131 (page 2.139); chain_ok 98%.

## 3. Exact vs first-order on S1b-COMB (26 months 202409-202610, exact runs X_C / X_L / X_B / X_VT)

| cell | exact trades | Q1-A trades | exact state cuts | Q1-A state cuts | matched to base by (book, side, signal s) | same exit among matched | exact net $ | first-order net $ | Q1-A net $ |
|--|--|--|--|--|--|--|--|--|--|
| X_C | 13950 | 15472 | 4731 | 5384 | 95.4% | 95.5% | 2167885 | 2458713 | 1889280 |
| X_L | 15761 | 15472 | 5432 | 5384 | 94.4% | 97.5% | 2037457 | 2697473 | 1889280 |
| X_B | 14797 | 15472 | 5027 | 5384 | 92.4% | 94.5% | 2447678 | 3266907 | 1889280 |
| X_VT | 15882 | 15472 | 5566 | 5384 | 96.1% | 98.4% | 1785116 | 1845150 | 1889280 |

Among matched trades whose lots changed: X_L 32% of matched trades changed lots; 82% of them have a different $ per lot (not just x lots) and 6.3% a different exit type (0.7% among unchanged-lot trades); X_VT 17% changed lots, 86% different $ per lot, 7.1% different exit type (0.4% unchanged). Mechanisms in the engine: lot-scaled arm variants (K7/U7 V2 arm = clip(ARM*sqrt(lots/4)), H7 V1 narrower with more lots), sliced fills for large lots, post-cut same-side blackout and caps/locks changing re-entries.

## 4. Testing-defect hunt
1. **sz_core.daily / s3_sizer.scale_pnl** = pnl_per_planned_lot x new lots on trades whose exits were fixed at the Q1-A lots by the S1b-COMB engine run (state cut, arms, blackout, locks already embedded). Cannot see lot-scaled arms, re-entries, locks, slices. Result: up-size mean overstated by $290k (sizer off), $660k (L), $820k (B) over 26 months, ladder drawdown understated (L6M cut L -43 vs -76 exact; B -73 vs -143); even the sign of d mean for sizer off flips (first-order +8.3k/wk vs exact -2.4k/wk). FIX: first-order is a screen only (the page already labels it); verdict cells need exact runs.
2. **S3 page windows**: DS3_TH_S3_SIZER_S1B.md L1M, L2M, L3M columns identical to the dollar for every cell (e.g. Q1-A +15336 / 79821 in L2M and L3M); cause: instr2_eval CARRY drops weeks 202629-39 before maxDD, leaving weeks 40-44 only. maxDD of all S3/S4/S5 pages built on s345_common.win_stats are carry-dropped maxDD (this is the same defect SZ-CORE found in owner ledgers). FIX: re-read S3 with the all-weeks rescore in section 2 of this page (done here); drop only from means.
3. **Exact driver (state_sizer_b.py, sz_exact.py)**: lots are applied in trend_size at the entry decision, i.e. BEFORE the position, the arm (V1/V2 use position lots), the cut, blackout and locks exist - lot-scaled arms are therefore handled correctly. Gaps: sz_exact applies the static M table keyed by (book, signal second) of the Q1-A base trades: any signal that the changed exits create (re-entries, different blackout) gets m = 1 (exact trades unmatched: 4-8%); the table multiplies the post-Q1-A lots then the engine applies zone HALF (rounding order differs from first-order). Ladder cells (X_*) are rule-based and unaffected. FIX: key by rule where possible (features recomputed at the signal second), or report the unmatched share per cell.
4. **Cached old trade list?** No: sz_core.Base loads base_b/S1-COMB parquet (21,135 trades) and S3 loads the same; I found no reuse of the DS3 V0 list. The S3 reproduced signs are explained by lot arithmetic, not by a stale base.
5. **J pairs**: min and product of 0/1 multipliers are identical cells (J rows 550b48e55984 and 1643bef3f809 have identical M arrays): double counted in the J scoreboard and in family p.
6. **Old-base transfer limits (this page)**: H7 in V0 never matches the S1b H7 signals (1%), K7 67%, P7 61%, M7 66%, U7 98%, A7 92%; replica HOLD 78% overall. D/E/I (equity-curve, concentration, recent-performance) multipliers depend on the base P&L history; their old-base transfer is not meaningful (shown, flagged).

## 5. Family top-5 (first-order top-5 by equal-mean L6M cut on S1b-COMB among down-only cells with a saved M array, rescored all-weeks ex O7) beside the same multipliers on V0 (old DS3 S4A engine) and replica HOLD

Rank = rank within the family among all rescored down-only cells by equal-mean L6M cut (1 = best). Cut % L6M/PRE; d mean $/wk L6M; new | V0 | HOLD.

| fam | cell | cut L6M new/V0/HOLD | cut PRE new/V0/HOLD | d mean L6M new/V0/HOLD | eq cut L6M new/V0/HOLD | rank new/V0/HOLD (of n) |
|--|--|--|--|--|--|--|
| A | 3b5002e14e89 | 53.2 / 33.1 / 60.8 | 40.6 / -15.0 / 28.3 | -3117 / -6761 / -5343 | 45.2 / 9.4 / 43.2 | 1 / 74 / 2 (195) |
| A | 07a9eb57e868 | 55.8 / -16.3 / 42.2 | 58.1 / 24.6 / 10.5 | -5632 / -5918 / -1283 | 43.6 / -54.7 / 38.0 | 2 / 133 / 8 (195) |
| A | 1fb40ebdb01a | 48.1 / -65.7 / -1.6 | 42.9 / 14.7 / 19.2 | -2256 / -7022 / -4328 | 42.4 / -131.1 / -32.2 | 3 / 185 / 167 (195) |
| A | 27003ddb767c | 36.1 / 37.2 / 25.1 | 40.9 / 17.1 / 47.9 | 2270 / -198 / 518 | 42.4 / 36.7 / 27.2 | 4 / 5 / 42 (195) |
| A | 73ca99b0ec2d | 36.3 / 37.0 / 43.9 | 20.1 / 16.1 / -11.6 | 2179 / -586 / -530 | 42.3 / 35.4 / 42.2 | 5 / 6 / 3 (195) |
| B | 1b5942ac8cd6 | 54.1 / 15.3 / 26.1 | 48.4 / -10.9 / 30.9 | 3951 / -4163 / 867 | 61.1 / 0.2 / 29.4 | 1 / 99 / 55 (200) |
| B | d852c862a088 | 55.2 / 39.5 / 38.6 | 57.9 / -5.6 / 36.2 | 2634 / -3539 / 1498 | 60.0 / 30.5 / 43.2 | 2 / 11 / 20 (200) |
| B | 9806533560c9 | 51.9 / 33.1 / 52.6 | 46.5 / 13.3 / 13.5 | 4012 / -2808 / -3250 | 59.3 / 24.2 / 45.4 | 3 / 17 / 14 (200) |
| B | 4afef260a5d4 | 48.9 / 8.5 / 11.2 | 46.6 / -8.1 / 14.2 | 2970 / -5312 / -266 | 54.9 / -17.7 / 9.9 | 4 / 173 / 121 (200) |
| B | e2058312a643 | 41.9 / 22.5 / 39.9 | 40.2 / 12.1 / 23.4 | 5929 / -181 / 1226 | 54.2 / 21.9 / 42.7 | 5 / 20 / 23 (200) |
| C | C|riskcap_per_trade|R$3600|P7 | 36.5 / 9.0 / 25.7 | 39.2 / 19.6 / 24.2 | -627 / -4200 / -1868 | 34.6 / -9.6 / 16.7 | 1 / 2 / 1 (4) |
| C | C|riskcap_per_trade|R$2400|P7 | 42.4 / 1.9 / 16.5 | 48.6 / 22.8 / 25.7 | -3878 / -6825 / -5326 | 29.4 / -35.3 / -20.9 | 2 / 4 / 4 (4) |
| C | C|riskcap_per_trade|R$3600|ALL | 30.2 / 0.9 / 24.4 | 42.3 / 18.8 / 24.1 | -1544 / -4608 / -2706 | 24.6 / -21.7 / 10.4 | 3 / 3 / 3 (4) |
| C | C|volparity_down|win120_refmin|M7 | 7.6 / 6.3 / 12.8 | 3.6 / 6.4 / 8.0 | 252 / 288 / 709 | 8.6 / 7.2 / 16.0 | 4 / 1 / 2 (4) |
| D | D|consec_loss|stack_k2_f0.00|sess_london | 45.0 / 4.3 / 3.1 | 24.4 / -0.4 / 21.6 | -968 / -1355 / -111 | 42.6 / -1.5 / 2.5 | 1 / 108 / 81 (127) |
| D | D|consec_loss|stack_k3_f0.00|sess_london | 39.2 / 2.9 / -2.6 | 7.9 / -15.5 / 4.5 | 1285 / -1558 / -835 | 42.4 / -3.9 / -7.6 | 2 / 113 / 119 (127) |
| D | D|eqdd_stack_20d|Y20000_f0.25_sticky|sess_london | 32.6 / 8.0 / 8.5 | 41.0 / 6.5 / 43.7 | 1184 / 363 / 1580 | 35.8 / 9.3 / 16.2 | 3 / 19 / 14 (127) |
| D | D|eqdd_stack_20d|Y10000_f0.25_sticky|sess_london | 33.9 / 11.6 / 17.9 | 45.4 / 6.9 / 43.7 | 345 / 559 / 654 | 34.7 / 13.4 / 20.1 | 4 / 13 / 6 (127) |
| D | D|eqdd_book_20d_R|Y4R_f0.25_sticky|ALL | 49.3 / -26.9 / 19.5 | 47.4 / 7.8 / 27.7 | -4745 / -5506 / -4946 | 34.4 / -63.1 / -12.9 | 5 / 126 / 123 (127) |
| E | E|total_lots_cap|cap4_trunc|sess_london | 39.4 / 29.0 / 28.9 | 46.5 / 15.3 / 21.5 | -596 / 513 / -933 | 38.0 / 30.5 / 25.9 | 1 / 1 / 9 (53) |
| E | E|same_side_lots_cap|cap4_trunc|sess_london | 39.0 / 18.7 / 31.0 | 46.5 / 24.4 / 32.3 | -1035 / 168 / 294 | 36.5 / 19.2 / 32.1 | 2 / 5 / 6 (53) |
| E | E|same_side_lots_cap|cap6_skip|ALL | 42.0 / 7.0 / 46.7 | 45.2 / 9.6 / 17.3 | -2601 / -6552 / -4001 | 33.8 / -26.3 / 30.6 | 3 / 52 / 7 (53) |
| E | E|total_lots_cap|cap6_trunc|sess_london | 30.7 / 21.3 / 35.6 | 24.2 / 6.0 / 4.3 | 664 / 731 / 2188 | 32.3 / 23.1 / 42.9 | 4 / 3 / 1 (53) |
| E | E|same_side_lots_cap|cap6_skip|P7 | 35.3 / 2.6 / 31.2 | 47.6 / 9.6 / 26.0 | -1068 / -6539 / -3765 | 31.8 / -32.2 / 12.0 | 5 / 53 / 19 (53) |
| F | e42de98e2549 | 51.0 / 23.0 / 36.1 | -3.5 / 16.2 / 18.2 | 1432 / 1505 / 2071 | 54.1 / 26.9 / 42.2 | 1 / 2 / 1 (208) |
| F | 87dbd27287dc | 30.7 / 27.2 / 32.3 | 3.6 / 12.4 / 18.5 | 427 / 469 / 1631 | 32.0 / 28.6 / 37.5 | 2 / 1 / 2 (208) |
| F | ee16b3a53d27 | 11.8 / 6.7 / 7.8 | -1.0 / 4.3 / -5.4 | 2552 / 337 / -35 | 20.5 / 7.9 / 7.6 | 3 / 21 / 26 (208) |
| F | 40f61f193625 | 26.0 / 11.5 / 4.9 | 21.0 / -28.4 / -28.4 | -1797 / -3322 / -4433 | 19.6 / -0.6 / -23.6 | 4 / 144 / 204 (208) |
| F | 8c1367b3e9be | 14.0 / 12.8 / 19.8 | 6.0 / 5.8 / 7.7 | 578 / 199 / 841 | 16.1 / 13.5 / 23.1 | 5 / 9 / 5 (208) |
| G | cebf694ec6e2 | 44.2 / -18.2 / 33.9 | 31.8 / 11.1 / 14.6 | -2481 / -3337 / -1261 | 37.1 / -37.5 / 28.6 | 1 / 975 / 59 (978) |
| G | c39104e20d4f | 26.9 / 19.0 / 30.1 | 29.7 / -18.4 / -21.2 | 3484 / 505 / 1453 | 36.5 / 20.6 / 35.1 | 2 / 18 / 19 (978) |
| G | a05f46ed5e90 | 37.8 / -0.2 / 22.0 | 23.3 / 8.1 / -2.0 | -1203 / -1545 / -2340 | 34.3 / -7.2 / 9.8 | 3 / 905 / 286 (978) |
| G | d83c9df25d9f | 36.4 / 35.1 / 20.4 | 5.7 / 11.4 / 13.1 | -945 / -2921 / -4132 | 34.2 / 27.3 / 4.5 | 4 / 8 / 475 (978) |
| G | 9f4c524e3da6 | 34.3 / 10.6 / 44.4 | 5.2 / -7.0 / -44.7 | -860 / -1235 / -21 | 31.5 / 6.1 / 44.4 | 5 / 222 / 1 (978) |
| H | d1b5ea189963 | 40.5 / 27.0 / 34.0 | 26.3 / 15.2 / 16.6 | -522 / -2691 / -1431 | 39.0 / 18.5 / 28.0 | 1 / 17 / 8 (288) |
| H | 61f3cbb073a5 | 42.2 / 29.0 / 33.6 | 38.1 / 13.7 / 22.8 | -2574 / -3592 / -2729 | 34.1 / 17.5 / 21.1 | 2 / 19 / 16 (288) |
| H | 6530410a3fc1 | 32.6 / 7.8 / 2.5 | 45.7 / 15.5 / 37.3 | -2159 / -5762 / -5796 | 24.8 / -18.8 / -46.9 | 3 / 280 / 286 (288) |
| H | 75f207541970 | 37.2 / 55.3 / 37.8 | 57.1 / 8.9 / 9.3 | -3607 / -7420 / -4890 | 24.1 / 37.3 / 13.1 | 4 / 4 / 39 (288) |
| H | ffe1dffa4c6a | 43.1 / 60.0 / 36.0 | 28.2 / 4.4 / 15.1 | -5695 / -3511 / -5496 | 21.9 / 53.9 / 6.0 | 5 / 1 / 80 (288) |
| I | 375f8bd0e8af | 70.1 / -14.2 / 40.6 | 54.4 / 24.4 / -21.0 | -7766 / -9022 / -4210 | 52.6 / -83.8 / 21.4 | 1 / 168 / 8 (186) |
| I | 83d7d23f2f5d | 39.9 / 23.8 / 25.2 | 37.5 / 9.8 / 16.1 | -2711 / -1675 / -3009 | 30.9 / 18.6 / 9.4 | 2 / 4 / 25 (186) |
| I | 8ae630eded67 | 58.6 / 4.1 / 41.8 | 52.3 / 9.7 / 36.0 | -8555 / -7823 / -9142 | 30.1 / -40.0 / -24.1 | 3 / 145 / 151 (186) |
| I | da1529221cbe | 38.2 / -13.3 / 21.0 | 41.0 / 11.3 / 6.3 | -3883 / -3814 / -923 | 24.1 / -34.9 / 16.5 | 4 / 135 / 15 (186) |
| I | 54da69ab5440 | 25.9 / 8.1 / 26.7 | 46.6 / 15.6 / 33.0 | -1355 / -420 / 129 | 20.8 / 6.6 / 27.2 | 5 / 12 / 3 (186) |
| J | 550b48e55984 | 85.2 / 22.4 / 62.6 | 57.9 / 24.1 / 27.4 | 2705 / -2662 / -4433 | 86.8 / 12.6 / 54.5 | 1 / 685 / 67 (1570) |
| J | 1643bef3f809 | 85.2 / 22.4 / 62.6 | 57.9 / 24.1 / 27.4 | 2705 / -2662 / -4433 | 86.8 / 12.6 / 54.5 | 1 / 685 / 67 (1570) |
| J | b386f7e9a06c | 79.5 / 54.1 / 67.4 | 57.7 / 30.6 / 33.6 | 4293 / -2840 / -4562 | 82.9 / 47.9 / 60.0 | 3 / 62 / 19 (1570) |
| J | e53ad796cf6c | 79.5 / 54.1 / 67.4 | 57.7 / 30.6 / 33.6 | 4293 / -2840 / -4562 | 82.9 / 47.9 / 60.0 | 3 / 62 / 19 (1570) |
| J | 54c138ccba27 | 84.0 / 45.2 / 59.9 | 40.5 / 17.8 / 27.4 | -2520 / -2794 / -3047 | 82.3 / 37.9 / 54.2 | 5 / 192 / 73 (1570) |
| K | k6_81016ac86971 | 35.2 / 31.6 / 43.1 | 29.4 / 7.7 / 12.7 | 4129 / -437 / 3222 | 45.0 / 30.3 / 51.4 | 1 / 6 / 1 (429) |
| K | k6_d78f5a584507 | 40.6 / 12.0 / 28.6 | 27.1 / 13.9 / 20.6 | 778 / -2861 / -211 | 42.5 / 0.5 / 27.8 | 2 / 129 / 13 (429) |
| K | k6_ae7301464620 | 33.8 / 41.1 / 46.6 | 34.1 / 2.2 / 15.0 | 2285 / -3087 / 1313 | 39.8 / 33.3 / 50.1 | 3 / 4 / 2 (429) |
| K | k6_9b08afbafdfd | 39.4 / 24.1 / 43.7 | 14.7 / 9.7 / 17.2 | -1115 / -3999 / -157 | 36.3 / 9.5 / 43.2 | 4 / 40 / 4 (429) |
| K | k6_c4f0eb8db8fd | 40.5 / -15.7 / 18.1 | 27.5 / 10.2 / 20.7 | -1623 / -4705 / -2888 | 36.1 / -44.1 / 1.6 | 5 / 385 / 208 (429) |

Cut correlation across all 4238 down-only cells: new vs V0 0.41, new vs HOLD 0.76; equal-mean cut Spearman 0.27 / 0.55; d mean correlation 0.69 / 0.81. Same-to-the-dollar d mean (|diff| < 0.005, nonzero): 0 cells on either old base.

## 6. Needed next
- Exact runs for family top-5 and every reference row (lead ordered; SZ-CORE queue). Priority: sizer off, ladder L, vol-target PRE/X' windows, then the A/B/J leaders; until then every cut on the sizer page is a screen.
- S3 re-read on all-weeks maxDD (done in section 2 for 4 reference cells; the rest of DS3_TH_S3_SIZER_S1B.md numbers should not be quoted).
- If wanted: recompute rule-based multipliers (ER, vol, time) directly on old trades instead of signal matching, to remove the 22-41% unmatched bias (SZ-BASE can do it for families A, B, F once the feature store for OLD-BASE is complete: /mnt/l2/l2vast/_th_sz/fgh_feat_OLD-BASE.parquet exists).


## 7. S3 re-read on the all-weeks rescore (corrects DS3_TH_S3_SIZER_S1B.md L1M-L3M and cuts)
S1b-COMB, first-order, all 7 books, maxDD on ALL weeks of each window (windows as of 2026-11-09; the trade lists end 20261030, so each window also contains the empty week 202645; means drop the carrying week, which for the Q1-A row against itself is an artifact of the argmax on zeros - read the maxDD and cut columns, not the Q1-A mean). Cell format: $/wk mean / maxDD / cut vs Q1-A / d mean.

| cell | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' |
|--|--|--|--|--|--|--|--|--|
| Q1A | -26607 / 79821 / +0.0% / +0 | +30326 / 79821 / +0.0% / +0 | +17354 / 79907 / +0.0% / +0 | +22996 / 79907 / +0.0% / +0 | +15522 / 99496 / +0.0% / +0 | +11120 / 88531 / +0.0% / +0 | +14777 / 140288 / +0.0% / +0 | +2181 / 116941 / +0.0% / +0 |
| L | -38900 / 116699 / -46.2% / -12293 | +27248 / 116699 / -46.2% / +7347 | +10333 / 116699 / -46.0% / +1067 | +27181 / 116699 / -46.0% / +5837 | +20273 / 130207 / -30.9% / +5558 | +10775 / 116067 / -31.1% / +4643 | +19241 / 207515 / -47.9% / +6056 | +603 / 120096 / -2.7% / +634 |
| B | -42321 / 126963 / -59.1% / -15714 | +33468 / 126963 / -59.1% / +13566 | +16279 / 138459 / -73.3% / +7013 | +37611 / 138459 / -73.3% / +15784 | +26632 / 165603 / -66.4% / +11681 | +13754 / 131650 / -48.7% / +7622 | +22272 / 212116 / -51.2% / +9087 | +499 / 184316 / -57.6% / +530 |
| C | -30028 / 90085 / -12.9% / -3421 | +30624 / 90085 / -12.9% / +3733 | +19345 / 108038 / -35.2% / +3599 | +30122 / 108038 / -35.2% / +8295 | +20265 / 134892 / -35.6% / +5313 | +11858 / 118527 / -33.9% / +738 | +16662 / 151592 / -8.1% / +2760 | +656 / 203191 / -73.8% / -862 |
| BK_MV:london:0.50:0.5:1.0 | -26104 / 78311 / +1.9% / +503 | +23138 / 78311 / +1.9% / +32 | +11663 / 78311 / +2.0% / +261 | +25472 / 78311 / +2.0% / +400 | +17861 / 97422 / +2.1% / +252 | +19427 / 84383 / +4.7% / -278 | +14241 / 136763 / +2.5% / -42 | +1731 / 119776 / -2.4% / +202 |
| VT_ZL1 | +5218 / 56462 / +29.3% / -2309 | +26907 / 56462 / +29.3% / +17 | +15676 / 69538 / +13.0% / +1751 | +24099 / 69538 / +13.0% / +705 | +16069 / 73548 / +26.1% / +349 | +9936 / 71767 / +18.9% / -807 | +14624 / 112622 / +19.7% / -1123 | +1013 / 63280 / +45.9% / +1044 |

Corrections vs the S3 page: L1M, L2M, L3M are no longer identical (L2M/L3M maxDD differ for B 126,963 vs 138,459 and VT 56,462 vs 69,538; mean L2M +30,326 vs L3M +17,354 for Q1-A); VT cut L6M is +13.0 (S3 page +29.3, which was the 5-week path); L6M cut for B is -73.3 (page -59.1); sizer off -35.2 (page -26.8); ladder L -46.0 (unchanged, its drawdown is in the last weeks). Signs unchanged; magnitudes shift.

## 8. Rule-based recompute on the old trade lists (no signal matching; the multiplier is recomputed from features at each old trade's signal second)
Method: the A/B feature builders (code/th_sz_ab/ab_feat.py, ab_hyst.py) were run on the old V0 ledger (21,397 trades, DS3 S4A engine) and on the replica HOLD list (S1b-HOLD, 23,855 trades), then the owner cell code (run_cells.py, CELLS_ONLY = the 400 A/B finalist ids) and sz_core scoring (all weeks, equal-mean) on all three bases. Files /mnt/l2/l2vast/_th_sz/ab/{feat,trades}_{V0OLD,HOLDS1B}.parquet and shards/. F/G/H/K cells: the FGH owner's own OLD-BASE re-score (ledger_FGH_OLD-BASE.parquet; replica ITER14 timer close, old per-print cut), same rules recomputed, owner cut convention (not re-audited). C/D/E/I/J: state or lot-history rules, n/a (kept as the signal-matched transfer of section 5, flagged).
Across the 400 A/B finalists (down-only 400): cut correlation new vs V0 0.11, vs HOLD 0.59; equal-mean-cut Spearman 0.11 / 0.44. Mean L6M cut of the set: new 24.1, V0 19.5, HOLD 38.1.

| fam | sub | params | cut L6M new / V0 / HOLD | d mean L6M new / V0 / HOLD | eq-mean cut L6M new / V0 / HOLD | rank new / V0 / HOLD |
|--|--|--|--|--|--|--|
| A | ER-NQ-P7 | [0.35, 0.0, 1.0] | 50.0 / -37.8 / 52.3 | -2256 / -6785 / -820 | 44.6 / -83.6 / 50.1 | 1 / 182 / 57 (of 200) |
| A | ER-NQ | [0.4, 0.0, 1.0] | 50.8 / 60.4 / 66.7 | -3381 / -10969 / -4356 | 41.8 / 31.0 / 55.5 | 2 / 20 / 15 (of 200) |
| A | ER-NQ-sess | [0.45, 0.0, 1.0] | 35.1 / 31.5 / 44.2 | 2270 / -1417 / 3165 | 41.3 / 27.6 / 52.8 | 3 / 26 / 38 (of 200) |
| A | ER-NQ | [0.2, 0.4, 0.25, 0.5, 1.0] | 35.3 / 42.0 / 52.7 | 2179 / -3360 / 73 | 41.3 / 32.5 / 52.9 | 4 / 15 / 36 (of 200) |
| A | ER-NQ-P7 | [0.35, 0.0, 1.0] | 35.8 / 10.8 / 65.0 | 2030 / -2663 / 5745 | 41.1 / -0.4 / 73.1 | 5 / 98 / 2 (of 200) |
| B | VOL-pool | [1.25, 0.0] | 52.9 / 54.3 / 58.7 | 3560 / -1947 / -3174 | 59.3 / 50.3 / 52.7 | 1 / 19 / 51 (of 200) |
| B | VOL-pool | [1.25, 0.0] | 54.0 / 63.3 / 64.9 | 2243 / -2061 / 4524 | 58.2 / 59.9 / 71.6 | 2 / 4 / 6 (of 200) |
| B | VOL-pool | [1.25, 0.0] | 50.7 / 53.1 / 71.0 | 3658 / -2008 / -1884 | 57.3 / 48.8 / 68.6 | 3 / 21 / 10 (of 200) |
| B | VOL-P7 | [1.25, 0.0] | 43.0 / 46.7 / 45.4 | 5929 / 821 / 4235 | 54.9 / 48.4 / 54.8 | 4 / 22 / 47 (of 200) |
| B | VOL-pool | [1.25, 0.0] | 47.5 / 49.2 / 41.2 | 2579 / -4070 / 815 | 53.0 / 38.7 / 43.6 | 5 / 43 / 73 (of 200) |

Reading: volatility-target cells (B) keep most of their cut on both old bases but turn from a mean gain on the new base (+2.2k to +5.9k $/wk first-order) to a mean cost on V0 (-4.1k to +0.8k): the new-base "equal-mean" ranking is not stable. ER cells (A) lose rank sharply on V0 (ranks 15-182 of 195; 1fb40ebdb01a cut +50 new, -38 V0, equal-mean -84) and mostly keep it on replica HOLD. This is what base-dependence looks like; nothing is identical to the dollar.

F/G/H/K top-5 by new equal-mean L6M cut, same rule on the replica OLD-BASE (owner re-score; owner cut convention): cut L6M new / old, d mean new / old, rank new / old.

| fam | technique | params | cut L6M new / old | d mean L6M new / old | eq cut new / old | rank new / old |
|--|--|--|--|--|--|--|
| F | dow | {"dow": 2, "m": 0} | 51.2 / 49.4 | 1171 / 2156 | 53.7 / 54.7 | 1 / 1 |
| F | dow | {"dow": 2, "m": 0} | 31.5 / 42.5 | 427 / 1174 | 32.7 / 45.8 | 2 / 2 |
| F | slot48 | {"m": 0, "slot": 8} | 12.1 / 19.5 | 2552 / 789 | 20.7 / 22.9 | 3 / 13 |
| F | dow | {"dow": 0, "m": 0} | 24.4 / 19.3 | -1865 / -2573 | 17.7 / 5.9 | 4 / 97 |
| F | dow | {"dow": 2, "m": 0.5} | 14.4 / 18.9 | 578 / 680 | 16.4 / 21.7 | 5 / 17 |
| G | qgate | {"feat": "nA40", "m": 0, "q": 0.3, "tail": "low"} | 90.2 / 93.8 | -11981 / -8692 | 77.6 / 86.4 | 1 / 1 |
| G | qgate | {"feat": "nA40", "m": 0, "q": 0.5, "tail": "low"} | 90.2 / 93.8 | -11981 / -8692 | 77.6 / 86.4 | 1 / 1 |
| G | qgate | {"feat": "nA40", "m": 0, "q": 0.2, "tail": "low"} | 90.2 / 93.8 | -11981 / -8692 | 77.6 / 86.4 | 1 / 1 |
| G | qgate | {"feat": "nA40", "m": 0, "q": 0.1, "tail": "low"} | 90.2 / 93.8 | -11981 / -8692 | 77.6 / 86.4 | 1 / 1 |
| G | qgate | {"feat": "nA20", "m": 0, "q": 0.5, "tail": "low"} | 86.9 / 87.7 | -16790 / -13262 | 38.5 / 27.8 | 5 / 146 |
| H | regime | {"cond": "adx5_ge20", "m": 0.5} | 39.6 / 51.3 | -522 / -430 | 38.0 / 50.0 | 1 / 5 |
| H | regime | {"cond": "adx5_ge20", "m": 0.5} | 41.3 / 54.0 | -2574 / -1527 | 33.2 / 49.1 | 2 / 6 |
| H | regime | {"cond": "gap_abs_ge0.50", "m": 0} | 36.2 / -3.0 | -2614 / -6124 | 27.5 / -57.4 | 3 / 833 |
| H | regime | {"cond": "on_ratio_ge0.8", "m": 0} | 40.8 / 18.8 | -5549 / -6957 | 26.0 / -17.2 | 4 / 785 |
| H | regime | {"cond": "on_ratio_ge0.6", "m": 0} | 32.1 / 38.9 | -2159 / -2248 | 24.5 / 29.5 | 5 / 21 |
| K | lot_table_cell | {"book": "P7", "live_q": 7, "q": 1, "sess": 1} | 28.1 / 28.2 | 243 / -34 | 28.9 / 28.0 | 1 / 8 |
| K | P7_lot_table_joint | {"q_asia": 7, "q_london": 4, "q_nyam": 4} | 27.2 / 21.2 | 359 / -644 | 28.2 / 18.8 | 2 / 42 |
| K | P7_lot_table_joint | {"q_asia": 7, "q_london": 4, "q_nyam": 3} | 27.5 / 17.5 | -438 / -1459 | 26.3 / 11.7 | 3 / 79 |
| K | lot_table_cell | {"book": "P7", "live_q": 7, "q": 0, "sess": 1} | 27.5 / 34.1 | -639 / -820 | 25.3 / 30.6 | 4 / 1 |
| K | P7_lot_table_joint | {"q_asia": 7, "q_london": 3, "q_nyam": 4} | 26.0 / 22.4 | -330 / -1463 | 25.1 / 16.9 | 5 / 48 |

Across 5,137 matched F/G/H/K cells: cut correlation 0.70, equal-mean Spearman 0.49; 16 cells with d mean L6M identical new/old are all zero-change cells in L6M (no lot change in the window), not defects. H "gap_abs" / "on_ratio" cells keep +26-36% cut on the new base and fall to ranks 785-833 on the old base (cut -3 / +19); the nA40 quality gate and Wednesday skip (F dow=2) are the only cells that hold rank 1-2 on both bases.
