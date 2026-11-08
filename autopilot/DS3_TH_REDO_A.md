# DS3_TH_REDO_A - program A (LOSS side, L2) on the REPLICA engine (TH-A, 2026-11-08)
**cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false cuts; engine Gate 0 NOT passed; PRE-PROOF**

No PASS claims, no policy-file change, no live statement. Windows: L1M/L2M/L3M/L6M/HOLD (as-of 2026-10-30), MID, PRE, X'. Deltas are USD per week, paired (rule minus the live cell, same engine), single largest-|delta| week dropped in windows >= 8 weeks (nodrop columns beside). Prereg A sha16 0dce7cef95179c57; adoption fb6d42b6e9d97a2d; addenda 07f947b4cf4bcdfc, 95ff9a48ee97e8fa; code shas in DECISIONS.md (logged before scoring).

## Plain result
- Smoke test passed: live cell 30/30x/5 s/1 on the replica reproduces the headline exactly (203 trades, +60,200, 108 cuts; blind week, seal manifest unchanged).
- Programme A has NO rule that clears the full ENTER test. 12 of 19 fully-covered pooled finalists beat the live cell on L6M AND PRE with the carrying week dropped and clear all three placebo nulls (random-timing, thinning, family), but every one of them is below its own 2.8-sd MDE, the Tier S walk-forward is not positive (p=0.38), and only P06/P07 pass the fragile-cut cap with a stable sign across the convention set (both fail drawdown-first). Nothing goes to the policy file.
- The live cell stays. It is not pulled (pull needs L3M AND L6M <= 0 for the live line vs alternatives; the baseline live weekly P&L on the replica is +11.6k L1M, +20.2k L6M, +7.6k PRE).
- Full-engine never-cut control (NOCUT) is worse than live on L1M..HOLD (-5.5k/week on L6M) although the no-cascade Tier S screen says 'cut less' is better: cascade/re-entries matter, so Tier S ranks are only a pre-filter (rank correlation Tier S vs Tier F S = 0.57 on the 19 fully covered finalists).

## What was run
1. Engine: HIST-PIPE per-day arrays 2023-02..2026-10-30 (43 month chunks, 10 warm-up days, settled D7 config, DST-aware) via hist_adapter; HOLD and NO-CUT record runs for every month (23,788 trades, 37.7 M evaluation rows). Private tree /mnt/l2/l2vast/_th_redo_replica/.
2. Tier S: every cell of A1 as a filter on the recorded rows: arm 15-50 x mult 5-200 x window 2-15 s x persistence 1-10 x ext {0 live, 1 at-extreme, 2 none} = 4,200 rule cells x 14 units = 58,800 unit-cells (ext has 3 values per the REPLICA addendum, so the family is 4,200 not 2,800). HOLD-world entries held fixed; a cut trade's natural path comes from the no-cut run when the same (book, entry) exists (9,219 of 13,511 cut trades); other cut trades keep the live cut. Self-test: filter at the live cell reproduces the engine's cut trades (blind week: 108/108 cuts, 5 USD off in 60,200; history: net 1.929M vs engine 1.853M, 4% gap from fills/partials, stated).
3. Nulls (200 shared-seed worlds, the whole screened family): random-timing exits of the same cuts, THINNING (keep only as many live cuts as the cell cuts, random subset - tests 'cutting fewer'), family max-stat; walk-forward purged by month over the pooled 4,200 cells.
4. Convention set: literal (replica rows) + FIT finalists 1-3 (r2_gen rows, latency 1.175 s) on the days with a raw tape only (blind week + Oct 28-30: 8 days; no tape exists for the history, so history windows are literal-only). 80% of grid cells keep their sign across all four conventions on those days; the live cell cuts 96 trades under literal and 15-18 under FIT conventions on them.
5. Tier F (limit 40): 40 finalists selected by the frozen rule (top S = min(L6M,PRE) among drawdown-first passes, <=2 per (arm,mult), then 3): 30 pooled cells, CMP_all and 6 per-book composites of per-unit bests, 3 more pooled. Full replica month-chunk re-runs (cascade included). After the 12 recent months, the 16 finalists failing the recents test were not run on older months (ENTER cannot pass without it; their PRE/X' are 0.0 / blank below, months column shows coverage); 19 pooled + 5 composites fully covered (43 months).
6. Incident: MemAvailable fell to 18 GB (6 workers + a 29 GB analysis); own pool stopped by pid and restarted at 4 then 3 workers; no data lost (INCIDENTS.txt in the private tree).

## Table (Tier F, full replica, fully covered pooled finalists, sorted by min(L6M,PRE)); header label as above
| id | cell | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | L6M nodrop | PRE nodrop | p_plc | p_thin | p_fam | sign stable | fragile share | recents | tolerant | dd first |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P10 | arm 35, mult 5x, win 10 s, pers 1, ext 1 | -8973 | -3754 | 1207 | 3506 | 1862 | -6415 | 4943 | -3111 | 5153 | 6062 | 0.00 | 0.01 | 0.00 | True |  | True | False | True |
| P02 | arm 30, mult 10x, win 3 s, pers 1, ext 1 | -4095 | -6505 | 877 | 3330 | -130 | -6090 | 3573 | -1932 | 1098 | 4624 | 0.00 | 0.00 | 0.00 | True |  | True | True | False |
| P24 | arm 45, mult 20x, win 15 s, pers 1, ext 2 | -5384 | -3305 | 2292 | 4803 | 3575 | 6478 | 3253 | -2223 | 6092 | 3983 | 0.00 | 0.09 | 0.00 | False | 1.24 | True | True | True |
| P12 | arm 35, mult 5x, win 5 s, pers 1, ext 1 | -9181 | -5083 | 577 | 3102 | 1359 | -8488 | 5147 | -3153 | 4753 | 6264 | 0.00 | 0.01 | 0.00 | True |  | True | False | True |
| P05 | arm 45, mult 10x, win 2 s, pers 1, ext 0 | -2139 | 636 | 3816 | 4565 | 2220 | -285 | 3007 | -1160 | 3353 | 3764 | 0.00 | 0.00 | 0.00 | True | 3.22 | True | True | True |
| P08 | arm 25, mult 5x, win 3 s, pers 5, ext 0 | 1675 | 5718 | 3756 | 4093 | 3888 | 1961 | 2674 | -179 | 5558 | 3494 | 0.00 | 0.01 | 0.31 | False | 7.92 | True | True | False |
| P11 | arm 35, mult 10x, win 3 s, pers 3, ext 0 | -4345 | -4652 | 783 | 5364 | 3705 | 4785 | 2147 | -1910 | 6830 | 3101 | 0.00 | 0.01 | 0.02 | True | 41.16 | True | True | True |
| P07 | arm 40, mult 5x, win 15 s, pers 5, ext 0 | -930 | -5279 | 2535 | 4909 | 4725 | 1581 | 1886 | -1136 | 6156 | 2748 | 0.00 | 0.00 | 0.00 | True | 0.10 | True | True | False |
| P06 | arm 40, mult 10x, win 15 s, pers 5, ext 0 | -958 | -5305 | 2393 | 5576 | 4965 | 1236 | 1866 | -703 | 6841 | 2728 | 0.00 | 0.00 | 0.00 | True | 0.13 | True | True | False |
| P19 | arm 15, mult 10x, win 3 s, pers 5, ext 0 | 9385 | 4224 | 7889 | 5094 | 2499 | -916 | 1172 | -631 | 6971 | 2139 | 0.02 | 0.03 | 1.00 | False |  | True | True | True |
| P14 | arm 40, mult 30x, win 15 s, pers 1, ext 2 | -2025 | -726 | 2989 | 1788 | 829 | -4267 | 1141 | -1337 | 2900 | 512 | 0.00 | 0.02 | 0.00 | False | 25.88 | True | True | True |
| P28 | arm 20, mult 30x, win 5 s, pers 1, ext 1 | -5999 | 389 | 4058 | 3910 | 3434 | -2641 | 985 | -3312 | 5578 | 1650 | 0.88 | 0.07 | 1.00 | False |  | True | False | True |
| P17 | arm 35, mult 30x, win 10 s, pers 3, ext 0 | 945 | -2123 | 799 | 4142 | 2297 | -2155 | 775 | -3388 | 5320 | 1587 | 0.00 | 0.05 | 0.00 | False | 3.11 | True | False | True |
| P13 | arm 40, mult 10x, win 2 s, pers 1, ext 2 | -2536 | -2866 | 1734 | 3389 | 2078 | -103 | 645 | -1078 | 4610 | 1224 | 0.00 | 0.02 | 0.00 | False |  | True | True | False |
| P18 | arm 35, mult 30x, win 10 s, pers 5, ext 2 | 1440 | -2182 | 17 | 2555 | 306 | 1000 | 339 | -2580 | 1253 | 1151 | 0.00 | 0.04 | 0.00 | False |  | True | False | False |
| P21 | arm 35, mult 20x, win 5 s, pers 2, ext 0 | 5359 | 706 | 1275 | 4551 | 4031 | 2606 | -30 | -3329 | 5759 | 706 | 0.00 | 0.08 | 0.00 | True | 5.81 | True | False | False |
| P20 | arm 35, mult 20x, win 15 s, pers 5, ext 0 | -3518 | -2966 | 170 | 2831 | 2037 | -2490 | -166 | -4332 | 4380 | 514 | 0.00 | 0.06 | 0.00 | True |  | True | False | False |
| P27 | arm 25, mult 20x, win 5 s, pers 5, ext 0 | 8606 | 5018 | 6237 | 8798 | 2888 | -9507 | -301 | -1127 | 6763 | 397 | 0.00 | 0.06 | 0.02 | False | 2.77 | True | True | True |
| P15 | arm 40, mult 30x, win 15 s, pers 1, ext 0 | -1371 | -3942 | 272 | 2971 | 1622 | -4036 | -409 | -671 | 4343 | 286 | 0.00 | 0.02 | 0.00 | False | 145.04 | True | True | True |
Control row: never-cut engine run: L1M -15,994, L2M -8,273, L3M -6,549, L6M -5,539, HOLD -3,383, MID -1,815, PRE +4,106, X' -3,775 (worse than live on every recent window).
Composites (per-unit bests; fully covered): CMP_all L6M +2,517 PRE +2,584 X' -1,488 dd-first True; CMP_KB L6M +2,411 PRE +174; CMP_PE +1,134/+488; CMP_HM +125/+115; CMP_MV +531/+349. No placebo family exists for composites (selected from the per-unit family; not ENTER candidates).
Partially covered finalists (P00,P01,P03,P04,P09,P16,P22,P23,P25,P26,P29,P30,P31,P32, CMP_SM, CMP_PB) failed or were not completed on recents; they are not candidates. Full rows: /mnt/l2/l2vast/_th_redo_replica/out/A1_finalists_A2.csv.

## Candidates that beat the live cell on L6M AND PRE (carrying week dropped, placebo-clean) - NOT ENTER
| id | live-definition of the rule | L6M | PRE | X' | L6M/MDE | PRE/MDE | drawdown first | convention sign stable | fragile share |
|---|---|---|---|---|---|---|---|---|---|
| P02 | arm 30, mult 10x, win 3 s, pers 1, ext 1 | 3330 | 3573 | -1932 | 0.28 | 0.54 | False | True |  |
| P05 | arm 45, mult 10x, win 2 s, pers 1, ext 0 | 4565 | 3007 | -1160 | 0.55 | 0.54 | True | True | 3.22 |
| P06 | arm 40, mult 10x, win 15 s, pers 5, ext 0 | 5576 | 1866 | -703 | 0.61 | 0.36 | False | True | 0.13 |
| P07 | arm 40, mult 5x, win 15 s, pers 5, ext 0 | 4909 | 1886 | -1136 | 0.55 | 0.34 | False | True | 0.10 |
| P10 | arm 35, mult 5x, win 10 s, pers 1, ext 1 | 3506 | 4943 | -3111 | 0.33 | 0.72 | True | True |  |
| P11 | arm 35, mult 10x, win 3 s, pers 3, ext 0 | 5364 | 2147 | -1910 | 0.59 | 0.38 | True | True | 41.16 |
| P12 | arm 35, mult 5x, win 5 s, pers 1, ext 1 | 3102 | 5147 | -3153 | 0.29 | 0.76 | True | True |  |
| P13 | arm 40, mult 10x, win 2 s, pers 1, ext 2 | 3389 | 645 | -1078 | 0.40 | 0.14 | False | False |  |
| P14 | arm 40, mult 30x, win 15 s, pers 1, ext 2 | 1788 | 1141 | -1337 | 0.21 | 0.24 | True | False | 25.88 |
| P17 | arm 35, mult 30x, win 10 s, pers 3, ext 0 | 4142 | 775 | -3388 | 0.68 | 0.18 | True | False | 3.11 |
| P18 | arm 35, mult 30x, win 10 s, pers 5, ext 2 | 2555 | 339 | -2580 | 0.30 | 0.08 | False | False |  |
| P24 | arm 45, mult 20x, win 15 s, pers 1, ext 2 | 4803 | 3253 | -2223 | 0.48 | 0.61 | True | False | 1.24 |

Policy-file expression of a candidate (for the record only; persistence and the ext variant are not expressible in the policy grammar): loss * pct<=-(arm/60), pulled_mult>=mult, secs_ext<=win cut, and the ThL2 constants LOSS_MIN=arm, PULL_MULT=mult, PULL_SECS=win. Live: pct<=-0.5, pulled_mult>=30, secs_ext<=5, LOSS_MIN 30.

## Limits (plain)
- Engine Gate 0 not passed; the cut input differs from live (see label). Settled D7 config applied to 3.6 years (period facts, outages, SS slots of the blind week not replayed). Month chunks restart state each month.
- Convention-set robustness only on 8 tape days; history is literal-only. Tier S has no cascade. X' deltas are negative for all candidates (-0.7k to -3.4k) and tolerant gate is met only for some. All finalist deltas are below the MDE.
- Not run: A2 flip triggers, A4 blackout, A5 lot-scaled arm, A6 dwell, A7 HM neighbourhood (no replica wiring this pass); listed as open in DS3_TH_REDO.md.
- Dead ledger: dead_lookup before (live spec not found; TH-withdrawn note applies, nothing counts as dead); 40 finalist rows appended after (program THA_REPLICA_PREPROOF); ledger not rebuilt.
- Files: code /mnt/l2/l2vast/_th_redo_replica/code, tables /mnt/l2/l2vast/_th_redo_replica/out (A1_finalists_A2.csv, A1_pooled_table_A2.csv, A1_unit_table_A2.parquet, A1_convset_cells.csv, A1_candidates_beat_live.csv). Seal manifest_after.json re-hashed unchanged (smoke + record runs).

## Addendum: sub-programs A2, A4, A5, A6, A7 (TH-A, 2026-11-08)
**cut-input agreement with live: 14% at 0% false (best FIT-selected convention) / literal reading 45 of 92 within +-2 s with 23 false cuts; engine Gate 0 NOT passed; PRE-PROOF**

Tier F used 16 more full-replica finalists (24 + 16 = 40 total, the prereg limit). Same windows, paired deltas vs the live cell, carrying week dropped, no PASS words, nothing proposed for the policy file. Pool kept at 2-3 processes by the lead's memory orders; the seal manifest hash is unchanged (759f2258...).

### What is expressible on the replica, and what is not
- **A6 sustained-cut (15 cells), A5 lot-scaled arm (3), A2 flip triggers (24), A7 (15 of the 161) - Tier S** on the same 37.6 M rows and hybrid worlds as A1, same three nulls (random-timing, thinning, family over the 57 new cells x 14 units = 798 unit-cells). Offline features from the HIST-PIPE day arrays (no engine run): imbalance / iceberg / sweep / delta-turn (A2) and 1-s close path features (A7).
- **A2 definitions are mine** (the prereg names the triggers, not formulas): imbalance = top-5-level depth imbalance against the position; iceberg-against = recency of an opposite-side iceberg detection; sweep = recency of an adverse sweep; delta-turn = signed volume of the last 5 s against the position given the prior 10 s was with it. Trigger cell = loss >= 30 pt AND strength >= history-wide quantile q (look-ahead in the threshold, stated). Persistence 1.
- **A5**: lot_ref = median lots of the unit; arm = 30 x (lots/lot_ref)^gamma on the live 30x / 5 s / new-extreme structure.
- **A6**: loss >= lvl for dwell seconds of consecutive evaluations, no pulled-support condition.
- **A7**: only the NINE named cells (arm 20/25/30 x window 10/20/30; 3 of 3: >= 4 pt worse than W s ago, no new adverse extreme for W s with recovery <= 4 pt, efficiency < 0.35) plus six one-at-a-time neighbours of the primary a30/w10 (momentum 3/5, recovery 3/5, efficiency 0.30/0.40) = 15. The other ~146 cells of the 161-cell RETEST family are NOT wired: the old 158-rule grid definition (windows 30/60/120 and its vote variants) is in the DS3 THL code, not in the replica, and I did not port it. Evaluated per second from 1-s closes; MAE and the extreme price are approximated from the trade's secs-since-extreme. A7 is an L1 price-path rule: the replica has no C# for it (as for B).
- **A4 blackout**: needs the cascade, so Tier F only. Replica mechanism generalised by parameter (TH BLACKOUT_BOOKS = all books, BLACKOUT_MINS, same-side native; both-sides by clearing blackout_side). It acts after a ThL2 cut only (the literal code sets no blackout after a PolicyCut). Tested on the live rule: same/both x 5/15/30/60 min and 0 (U7's live 30-min blackout switched off) = 9 runs. The '+5 best A1 rules' x blackout part (50 cells) was not run (Tier F budget). No Tier S null exists for blackouts.
- **Per book x session thresholds**: done in A1 (unit tables, composites CMP_*), see above.
- Not expressible and not run: the A6/A7 rules as policy-file lines (policy grammar has no dwell, no path features); A2 in the engine (features are offline; Tier F for A6/A7 injects the Tier S fire time of each (book, entry) into the full replica instead, literal cut off for those trades; unmatched entries keep the live rule; blackout after injected cuts follows the TH constants).

### Tier S result (pooled, 57 cells; table /mnt/l2/l2vast/_th_redo_replica/out/B_pooled_table_A2.csv)
- A2: 0 of 24 cells have S>0 (best S -602). A5: 0 of 3 (best -1,763). A6: 5 of 15 positive, all at lvl 40 (best l40/d10: L6M +3,717, PRE +3,199; all three nulls clean). A7: 3 of 15 positive, best pooled S +645 (a20/w10); on the HM units alone S is at most +88 USD/week (HM_nyam), i.e. immaterial.

### Tier F (full replica; weekly USD delta vs live; recents first, older months only for survivors)
| id | months | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | recents | tolerant | dd first |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S_A6_l40_d10 | 12 | -13595 | -5814 | 2858 | 2504 | 3167 | 6274 |  |  | False | True | True |
| S_A6_l40_d20 | 12 | -16892 | -6597 | 1159 | 272 | 3336 | 540 |  |  | False | True | True |
| S_A6_l40_d2 | 12 | -14004 | -5854 | -3716 | 2557 | 2489 | -1346 |  |  | False | True | True |
| S_A6_l40_d5 | 12 | -12018 | -3919 | 2994 | 962 | 2573 | -899 |  |  | False | True | True |
| S_A7_a30_w10 | 12 | -191 | 536 | -2 | -6 | 147 | -739 |  |  | False | True | False |
| S_A7_a25_w30 | 12 | -412 | 41 | -445 | -207 | -259 | -656 |  |  | False | True | False |
| S_A7_a20_w10 | 12 | -817 | 306 | -70 | -242 | -6 | -737 |  |  | False | True | False |
| BO_same_5 | 43 | -408 | 761 | 260 | 546 | 822 | 92 | 708 | 38 | True | True | True |
| BO_same_15 | 43 | 1079 | 1232 | 621 | 524 | 935 | 493 | -495 | 277 | True | True | False |
| BO_same_30 | 12 | -550 | 378 | -362 | 1008 | 680 | 1575 |  |  | False | True | False |
| BO_same_60 | 12 | 5993 | 2735 | -494 | 5087 | 4182 | 6605 |  |  | False | True | True |
| BO_both_5 | 43 | 2426 | 1948 | 1643 | 3390 | 1833 | -41 | 647 | 263 | True | True | True |
| BO_both_15 | 43 | 1572 | 4470 | 3944 | 1605 | 1390 | 270 | -298 | 1113 | True | True | False |
| BO_both_30 | 43 | 3433 | 1828 | 1511 | 2885 | 2477 | 521 | -495 | 1066 | True | True | True |
| BO_both_60 | 12 | 8056 | -6530 | -37 | 1421 | 1033 | -965 |  |  | False | True | True |
| BO_off | 12 | 0 | 0 | 0 | 0 | 0 | 0 |  |  | False | True | True |

### Plain reading
- **Sustained-cut (A6) and the L1 path rule (A7) lose on the full engine in recent windows**: l40 dwell cells are negative on L1M/L2M and fail recents; the HM path rule is ~0 (L6M -6 to -242 per week). Tier S flattered A6 for the same reason as in A1 (cut-later artefact without cascade). A2 and A5 never reach positive S, so they were not sent to Tier F.
- **Blackout (A4)**: both-sides blackouts after a ThL2 cut help on every recent window: BO_both_5 min: L1M +2,426, L2M +1,948, L3M +1,643, L6M +3,390, HOLD +1,833, MID -41, PRE +647, X' +263 per week, drawdown-first met, tolerant gate met; BO_both_30 and BO_both_15 positive on recents but PRE -495/-298; same-side 5/15 smaller. Individually every delta is below its MDE (BO_both_5: L6M 3,390 vs MDE 4,046; PRE 647 vs 1,759). The blackout has no placebo or family null (not expressible in Tier S), so it cannot clear the ENTER test: it is a LEAD that needs a placebo (random-time blackouts of the same length after the same cuts) before any claim; best of 9 runs, so best-of-F applies.
- BO_off (U7's live 30-min same-side blackout removed) equals the live engine to the dollar on the 12 months it covers (11 months complete; one month missing because the pool was restarted), i.e. the U7 blackout is not binding in the replica over those months.
- Nothing here changes the program-A verdict: the live cell stays; no policy-file line.
- Ledger: dead_lookup before (not found); 16 rows appended (program THA_REPLICA_PREPROOF). Files: tiers_B.py, feat_extract.py, tierF2.py, final_B.py under /mnt/l2/l2vast/_th_redo_replica/code; tables B_*.csv and B_sched_A2.pkl in .../out.
