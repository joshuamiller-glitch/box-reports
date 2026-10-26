# REPORT BL1 - audit of long-only / short-only rules judged with the alternating-side random-entry null (analysis only)
**Verdict: 93 lead cells (gate-3 at any share, non-diagnostic) were found in the ap_b_base pipelines (B, Q, SW, BI, BJ families, 13 instruments). 80 of them trade a balanced long/short mix in the pair window (long fraction 0.38-0.62) so the alternating-side null was a fair test; 13 are drift-sensitive (long fraction >= 0.62 or <= 0.38) and were re-scored with a same-clock, same-side random-date null (200 replicates, ap_bl_rescore.py = the logic of ap_bj_pipe.py applied to existing cells). Result: 2 cells flip pass -> FAIL (SW13 GC daily LGBM, SW34 ES P>=0.55), 2 flip fail -> pass (BJ8 YM May-Oct long, SW20 YM clv fade); 9 unchanged. No FOUND or FOUND-PENDING status changes, because none of these cells was FOUND-PENDING and every one of them still fails other gates (bootstrap or plateau). Non-pipeline sleeves (ES/YM dip-buy, I9, J4, N3, K4 family, XS momentum) are listed in section 3 with the null each report used: all use long-only or drift-matched nulls already, except N3 whose long-beta explanation is on record (PX34). Nothing in LEDGER.md or the frozen forward predictions was edited.**

## 1. How the audit was done
- Population: every non-diagnostic scored cell in outputs/autopilot/b/*_CO_all_selected_scored.csv with uplift >= +0.10 on clean, H1 and H2 together at any of 10/20/30/50% (the pipelines' 'LEAD' criterion): 93 cells. For each: events re-generated from the family module, fraction of long events in the pair window (2023-08+) computed.
- Null in the old pipelines (ap_b_base.run_cell with rand): random valid 1-minute rows, same trade count, ALTERNATING sides, any clock minute. For a rule with a fixed side that null has zero drift and the wrong time-of-day mix, so it is too easy to beat when the asset drifts up (long-only) and too hard when it drifts down for shorts.
- New null: every real event is moved to a uniformly random date at the SAME clock minute, KEEPING its side, same attr/exit logic, 200 replicates; statistic = standalone pair-window all-in weekly Sharpe (as the old gate). Old rank is the pipeline's null_pw_rank, new rank the shifted-date rank; pass means real Sharpe > null p95.
- b2356 daily families (X, Y, Z, W, B2/B6): their null uses random entry days with the same count per year and random +-1 sides (50/50), so it has the same weakness for long-only rules; those leads were WITHDRAWN (X1/Y6/B2-D path artefact) or are not long-biased (gap fades are two-sided).

## 2. Re-scored cells (drift-sensitive subset; the other 80 cells have long fraction 0.38-0.62)
| family | sym | cell | side mix | pair-window trades | old rank | new rank | p95 old -> new | real Sharpe | null gate old -> new | change | other gates |
|---|---|---|---|---|---|---|---|---|---|---|---|
| SW13 | GC | daily LGBM(<=2022) RTHopen+30m P>=0.58 hold=240m | net long (0.62) | 166 | 0.95 | 0.94 | +0.73 -> +0.76 | +0.74 | pass -> fail | pass->FAIL | boot lo -0.00, plateau 0.25 |
| BI4 | NQ | prior-day volume pct>=90 of 20d mode=against RTH open hold flat | net long (0.68) | 146 | 0.93 | 0.91 | +0.86 -> +0.87 | +0.78 | fail -> fail | none | boot lo -0.01, plateau 0.33 |
| SW20 | NQ | clv prior1d |m|>=0.02 RTHopen+30 dir=against hold=flat | net short (0.31) | 619 | 0.93 | 0.97 | +0.99 -> +0.85 | +0.83 | fail -> fail | none | boot lo -0.03, plateau 0.50 |
| SW22 | NQ | gex_norm tail0.2 mode=hi dir=- entry=rth | short-only (0.00) | 203 | 0.98 | 0.99 | +0.85 -> +0.79 | +1.19 | pass -> pass | none | boot lo +0.03, plateau 0.00 |
| SW32 | NQ | pair P&L prior 1d mode=pm dir=+1 hold=3d | net long (0.62) | 794 | 0.99 | 0.97 | +0.98 -> +0.93 | +1.15 | pass -> pass | none | boot lo -0.04, plateau 0.00 |
| SW34 | NQ | LGBM(<=2022) 2d P>=0.52 entries=week | long-only (0.98) | 155 | 0.99 | 0.96 | +0.86 -> +1.06 | +1.17 | pass -> pass | none | boot lo -0.05, plateau 1.00 |
| BJ8 | YM | season MayOct dir=long hold=c2c | long-only (1.00) | 436 | 0.94 | 0.95 | +1.08 -> +1.04 | +1.05 | fail -> pass | fail->pass | boot lo -0.01, plateau 0.00 |
| SW20 | YM | clv prior3d |m|>=0.02 RTHopen+30 dir=against hold=flat | net short (0.35) | 431 | 0.92 | 0.96 | +0.91 -> +0.71 | +0.80 | fail -> pass | fail->pass | boot lo +0.00, plateau 0.75 |
| SW34 | YM | LGBM(<=2022) 2d P>=0.52 entries=week | net long (0.87) | 132 | 1.00 | 0.99 | +0.90 -> +1.01 | +1.31 | pass -> pass | none | boot lo +0.02, plateau 1.00 |
| BI8 | ES | prior-day range>=1.5xATR20 mode=long hold=1d | long-only (1.00) | 114 | 0.95 | 0.97 | +0.79 -> +0.71 | +0.83 | pass -> pass | none | boot lo +0.01, plateau 0.50 |
| SW34 | ES | LGBM(<=2022) 2d P>=0.5 entries=week | long-only (0.99) | 167 | 0.99 | 0.98 | +0.91 -> +1.27 | +1.47 | pass -> pass | none | boot lo +0.02, plateau 0.00 |
| SW34 | ES | LGBM(<=2022) 2d P>=0.55 entries=week | long-only (1.00) | 105 | 0.99 | 0.89 | +0.87 -> +1.35 | +1.05 | pass -> fail | pass->FAIL | boot lo -0.07, plateau 1.00 |
| SW34 | ES | LGBM(<=2022) 2d P>=0.52 entries=week | long-only (0.99) | 148 | 0.99 | 0.97 | +1.01 -> +1.11 | +1.37 | pass -> pass | none | boot lo -0.00, plateau 1.00 |
Reading. (a) The long-biased LGBM weekly cells (SW34 on ES/NQ/YM, long fraction 0.87-1.00, null median now +0.17 to +0.44 Sharpe: the bull drift is visible) keep ranks 0.96-0.99 on four of five cells; the exception is ES P>=0.55 (rank 0.88, fails). (b) The short-only SW22 NQ gex rule has null median -0.13, so the alternating null understated it (rank 0.98 -> 1.00): bear-drift sensitivity is the mirror effect, short-only rules are judged harsher by a drift-matched null only if the asset falls; here (2023-26 bull) they gain. (c) BI4 NQ against-mode and BJ8 YM stay below or at the p95 line. (d) None of the 13 changes any other gate: every cell still has bootstrap lower bound <= +0.03 or plateau < 0.75; so none moves between LEAD and FOUND-PENDING; downgrades by the new null alone: SW13 GC and SW34 ES P>=0.55 become 'LEAD, fails null' (they were 'LEAD gate-3 only').

## 3. Items outside the ap_b_base pipelines (documented, not re-scored: trade series are in the library but the entry rules/null live in other harnesses)
| item | direction | null used (report / code) | drift handled? | status impact |
|---|---|---|---|---|
| ES / YM dip-buy (T4 B, C11-DIP, FOUND-PENDING-REPLICATED) | long-only | own random-date null: 1000 draws of 23 random LONG signals with the same exits (ap_c11_dip_score.null_job), rank 0.999, null median Sharpe +0.35 | yes (random-date long-only; the circular-shift null is reported only) | none |
| I9 IBS (REPORT_I9), J4 / J4X quad-witching long (REPORT_J4), I4 volume surge | long (I9, J4) | I-series fam.run with rng: random candidate rows each carrying the candidate side of the family base signal (always long for I9, J4, K4); I9 null median 0.32, J4 median 0.07 (drift visible), ranks 1.00 / 0.99 | yes (direction kept) | none |
| K4 / K4v2 / E7 / RW / RX / RY / RV (long-only daily GBM, FOUND-PENDING-REPLICATION) | long-only | K4v2 and E7 report BOTH the random-entry null and a drift-matched (month-stratified) null: ranks 1.00 (real 1.22-1.43 vs p95 0.50-0.62); variants inherit | yes | none |
| N3 VX flat -> long ES/NQ/RTY | long | own-null rank 0.99 (random entries); long-only null diagnostic in PX34: 'better explained as long NQ beta' (all-days-long Sharpe 0.75 vs 1.20) | partly; already recorded as weak LEAD / beta | none |
| BI8 ES long after a range-shock day | long | alternating null rank 0.96; drift-matched null in REPORT_BI8B: below p95 on clean/H1/H2 | withdrawn | withdrawn (BI8B) |
| BJ8 YM May-Oct long | long | BJ pipeline drift-matched null (rank 0.94-0.95) | yes | NO (opposite sign, fails bootstrap/plateau) |
| W4 Monday equity drift, RTY overnight carry, Q9 low-vol reversal, Q5 / Q10 / R9 XS momentum | long-biased or long/short | b2356 / Q harnesses: random entry with 50/50 sides (W4, carry) or market-neutral long-top/short-bottom (Q5, Q10, R9; Q9 long highest ATR is net long across markets) | W4 and carry: no, but both are NO / failed other gates; Q5/Q10/R9: construction is neutral; Q9: net-long sensitivity NOT re-scored (daily b2356 harness, flagged) | Q9 (LEAD under ERA retro) flagged: re-score recommended with a same-year-count long-only null |
| Track L short-VX (T3 S6) | short-only | own signal-shift null rank 0.10-0.48 | bear-drift sensitivity: the short carry sells vol into drift; NO already, not executable at NT Brokerage | none |
| BTC / ETH rules (B1 WT, SW1 BTC emax, Q8D ETH, L92) | two-sided (long fraction 0.43-0.51 across all 11 BTC/ETH lead cells) | alternating null | balanced mix, drift cancels | none |

## 4. Bear-drift sensitivity (item 2)
Short-only or net-short cells in the pipeline set: SW22 NQ gex (short-only, rank 1.00 new), SW20 NQ clv fade (0.31 long, 0.93 -> 0.97), SW20 YM clv fade (0.35 long, 0.92 -> 0.96, fails -> passes the null line but still fails bootstrap/plateau). In the 2023-26 bull sample the drift-matched null for a short rule has a NEGATIVE median (SW22 -0.13, SW20 -0.02/-0.23), so shorts that earn money are judged more favourably than under the alternating null; the sensitivity would reverse in a bear sample, and the 2013-22 pre-2023 ERA flags (negative for SW22 NQ) are the check that matters. No short-only rule is FOUND-PENDING.

## 5. What to flag
- No FOUND-PENDING status changes (confirmed: ES dip-buy, K4 family, FVG family, SW4-REPL RTY fade, RZ9 are either drift-matched or two-sided). Nothing edited in LEDGER.md or the frozen forward predictions.
- Recommended follow-up (not done): re-score Q9 (net long XS) and the b2356 daily families that are long-biased with a same-year-count long-only random null; generalise ap_bj_pipe's drift-matched null to the b2356 and I-series harnesses.

Files: code/census/night_ins/ap_bl_rescore.py; outputs/autopilot/b/bl1_all.csv, bl1_rescored.csv.

DONE BL1
