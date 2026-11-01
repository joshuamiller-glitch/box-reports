# DS3_INST_F_DD - INSTITUTIONAL section F, flow calendar (month-end, quarter-end, opex, roll week, Fed blackout, coupon settlement): re-read under DRAWDOWN FIRST (F1, overnight order, written 2026-11-01 00:00Z)

DATA. On disk or rule-derived, nothing to buy: month-end, first-of-month, quarter-end, opex, quad, coupon-settlement, NQ roll day / roll-Thursday week, Fed blackout, Russell, x 5 intraday windows x skip / x1.5. 110 cells reconstructed (f_stack.py code). The 24 close-window standalone class books are not stack rules (not re-priced here; C1 builds the close-fade sleeve).

**Prereg** `prereg/F1_INSTDD_prereg.md` sha256 `b177b68129c4bf2e492749bdf8ac98d8f1da9bac3c6c7dc4bc5957806d03ae98`; stage-1 selection `out/inst_dd/stage1_selection.json` sha256 `8ce67ccbbedfc6a5810d8ac8d1d8710a45b1b17084b618b4f17cb5854f802763` logged in DECISIONS.md before the recent look. Capped 20260206; UNTOUCHED never read. Frames: Sunday composite (headline) and as-is stack, live lots (K6 2 / P6 7 / U6 4 / H6 4-2 / M6 2 / A6 1), one-convention engine (dd_lib/lib3, unchanged).
**Coverage.** 110 cells swept in this group; 1 carried on PRE and X' (composite maxDD cut >= 20% in BOTH and mean not beyond -MDE in both); 1 distinct fire vectors; 1 looked at once in L3M/L6M/HOLD/ALL (cap 40 by min(PRE cut, X' cut)); 0 more carry in the as-is frame only (not looked at).
**Family-wise.** 110 cells swept; program placebo false-carry rate of the PRE+X' criterion for same-volume random skips/size-cuts in this group: 0/170 draws = 0.0% (17 sampled cells x 10 draws; mean volume cut 0%), i.e. about 0 chance carries expected of 110 swept vs 1 observed. Bonferroni placebo p = min(1, placebo rank p x distinct carried).

### Baselines (weekly $, label weeks; maxDD of the weekly cumulative)
| window | frame | mean $/wk | SD | maxDD | worst-20 | Calmar | mean/\|worst-20\| |
|---|---|---|---|---|---|---|---|
| L3M | Sunday composite | 34,406 | 44,702 | 21,361 | n/a (<20 loss wks) | 1.611 | nan |
| L3M | as-is stack | 12,153 | 45,510 | 88,039 | n/a (<20 loss wks) | 0.138 | nan |
| L6M | Sunday composite | 41,137 | 42,743 | 22,892 | n/a (<20 loss wks) | 1.797 | nan |
| L6M | as-is stack | 21,715 | 43,891 | 88,039 | n/a (<20 loss wks) | 0.247 | nan |
| HOLD | Sunday composite | 38,574 | 51,791 | 96,995 | n/a (<20 loss wks) | 0.398 | nan |
| HOLD | as-is stack | 21,874 | 53,850 | 144,173 | n/a (<20 loss wks) | 0.152 | nan |
| PRE | Sunday composite | 23,095 | 55,723 | 241,199 | -875,191 | 0.096 | 0.0264 |
| PRE | as-is stack | 18,612 | 50,445 | 161,956 | -810,578 | 0.115 | 0.0230 |
| X' | Sunday composite | 7,955 | 32,632 | 120,500 | -419,642 | 0.066 | 0.0190 |
| X' | as-is stack | -3,410 | 28,974 | 316,507 | -572,111 | -0.011 | -0.0060 |
| ALL | Sunday composite | 22,258 | 50,318 | 241,199 | -1,098,057 | 0.092 | 0.0203 |
| ALL | as-is stack | 13,060 | 47,240 | 316,507 | -1,161,104 | 0.041 | 0.0112 |

### Table 1. Risk at live lots, composite frame, recent-first (maxDD cut = 1 - after/before; negative = deeper)

| cell | session mix of affected live signals | affected live | L3M cut | L6M maxDD before > after (cut) | HOLD cut | PRE cut | X' cut | ALL cut | worst-20 PRE b>a | X' b>a | ALL b>a | SD L6M b>a | Calmar L6M b>a | as-is L6M cut / PRE / X' |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fl.BLACKOUT.DAY.skip | nyam 40%, asia 30%, london 21% | 3396 | +53% | 22,892 > 10,090 (+56%) | +30% | +29% | +32% | +29% | -875,191 > -780,877 | -419,642 > -362,401 | -1,098,057 > -976,973 | 42,743 > 38,876 | 1.80 > 3.63 | +65% / -13% / +30% |

### Table 2. Mean (MDE), equal-risk, placebo, gates, label ($/wk stack change vs the Sunday composite; MDE = 2.8 x SE of the paired weekly delta)

| cell | mean L3M | L6M (MDE) | HOLD | PRE | X' | ALL | equal-risk mean change L6M (c) | PRE | placebo L6M cut p95 / rank p | Bonf p | STRICT | TOL (literal) | NOW-ONLY | TOL-B / TOL-nc | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| fl.BLACKOUT.DAY.skip | 2,932 | -4,523 (14,758) | -3,846 | -7,970 | -487 | -4,982 | -4,568 (1.14) | -9,243 | -3% / 0.005 | 0.01 | n | n | n | n / n | RISK-KEEP (LEAD) |

### Reading

F (flow calendar): 110 cells swept, 1 cut the composite maxDD >= 20% in BOTH PRE and X-prime with the mean inside its MDE; 1 looked at once in L3M/L6M/HOLD/ALL: 1 meet the user's L6M definition (cut >= 20% with the mean inside MDE), median L6M maxDD change -56% (positive = deeper), 1 still cut ALL by >= 20%, STRICT 0 / TOLERANT 0 / NOW-ONLY 0 (TOL-B 0, TOL-nc 0); program placebo false-carry rate 0.0% at a 0% typical volume cut (about 0 chance carries of 110 vs 1 observed).

**The one cell: skip every signal on Fed-blackout trading days** (second Saturday before the FOMC meeting through the statement day; 183 of 745 trading days, 22% of the composite's taken signals, calendar known months ahead). Facts, composite frame:

- blackout days 183 of 745
- L3M base pnl on blackout days -41632 (n=15)  on others 523310 (n=52)  skip-effect total 41043
- L6M base pnl on blackout days 131621 (n=31)  on others 1020224 (n=105)  skip-effect total -126633
- HOLD base pnl on blackout days 129047 (n=39)  on others 1105323 (n=120)  skip-effect total -123064
- PRE base pnl on blackout days 672637 (n=88)  on others 1059468 (n=280)  skip-effect total -597760
- X base pnl on blackout days 37516 (n=56)  on others 312509 (n=162)  skip-effect total -21427
- ALL base pnl on blackout days 839201 (n=183)  on others 2477300 (n=562)  skip-effect total -742250

Worst 12 weeks of the composite (ALL): 4 of them are blackout weeks (2024-w11 -71k, 2024-w37 -68k, 2025-w30 -67k, 2025-w24 -58k become +1k, +3k, -0.1k, -6k); the other 7 are untouched. So the cut is a calendar effect on 4 weeks and costs the 22% of the mean that the blackout days earned (ALL mean 22.3k -> 17.3k per week; PRE blackout days earned +673k of 1,732k).

Read honestly: user definition met (L6M maxDD 22.9k -> 10.1k, -56%, mean -4.5k inside MDE 14.8k); beats the same-volume placebo (placebo p95 of the L6M cut is -2.7%, i.e. random 22%-volume skips make it deeper; rank p 0.005 of 200); PRE -29%, X-prime -32%, ALL -29%, worst-20 ALL -1.098M -> -0.977M (-11%), Calmar ALL 0.092 -> 0.100. Against it: (a) the L6M as-is maxDD is the single week of 2026-01-19 (FOMC Jan 27-28), so the L6M cut is that one week (4 of its 5 label days are inside the blackout window); (b) the as-is frame DEEPENS in PRE (-13%), only the composite agrees; (c) equal-risk (lots x1.14 so the ALL worst-20 matches) the mean is still -4.6k L6M (MDE 16.0k), -9.2k PRE (MDE 10.8k), -5.5k ALL (MDE 6.8k): the rule does not beat simply running the composite on a worst-20 basis, it trades a smaller maxDD for a lower mean; (d) 110 cells swept in F, one carried; Bonferroni against the 80 cells looked at in this program is 0.40 (against distinct carried in F, 0.005 as preregistered); (e) the STRICT/TOLERANT/NOW-ONLY columns are all no (mean falls in HOLD, PRE, X-prime). Label: RISK-KEEP (LEAD under the prereg rule: beats placebo, PRE and X-prime agree, group Bonferroni 0.005), NOT confirmed program-wide. **Shadow only; D6 mapping = a calendar policy line 'flat on Fed-blackout days' (FOMC dates from the event calendar, no discretion); D7 none.** It is the cheapest hedge-by-omission in the INST list and the first one that survives its own placebo, but it is one cell out of 110 and its maxDD cut is four weeks of 2024-25 plus the one L6M week.

### Notes
- Counts: STRICT/TOLERANT(literal)/NOW-ONLY over the looked cells: see Reading; TOL-B and TOL-nc are post-hoc, beside.
- dead_lookup (run before scoring): every cell here exists in the ledger under INST_D 1,044 / INST_E 396 / INST3C 701 / INST3F 134 / INSTG 36 / INST_H 16 (scored on the mean, 'EXACT' by name); this program re-prices them on drawdown. The new H4 (12) and H5 (4) cells and the engine-route H2 bracket rows have 0 hits. Appended after scoring with append_cells (program F1DD, tier PRICED), never rebuilt.
- Coverage gaps (not stack rules, not re-priced here): 8 NQ/ES pair-book cells (C), 24 close-window class books (F; C1 builds the close-fade sleeve), the stored INST-D/E s2 series (neighbours, shifted-state and random placebos, not scored cells).
- Single-week caveat: the composite L6M maxDD (22.9k) is one week (2026-01-19); the as-is L6M maxDD is the same week. L3M/L6M/HOLD have fewer than 20 losing weeks, so worst-20 is shown for PRE, X-prime, ALL only.
- Deviation from the prereg count: H4 has 12 cells, not 14 (counting error); swept total 2,311.
- Top-N by in-sample drawdown (the 40 cap in C) is post-hoc; nothing promoted; Shadow only.
- Code l2vast/ds3/code/inst_dd/, results l2vast/ds3/out/inst_dd/ (stage1_table.csv, stage2a_table.csv, final_rows.csv, summary.json), rows out/recent_wins/inst_dd.csv.
- Fed-blackout cell, own volume-matched placebo: random skips of the same 22% volume pass the PRE-and-X-prime criterion (cut >= 20% in both, mean inside MDE) in 14% of the 200 draws (the group-level rate above is 0% only because the sampled F cells are small calendar days); the L6M test against those draws is rank p 0.005.
