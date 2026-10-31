# DS3_SIXTY - T-SIXTY (SIXTY-1): the "over a coin flip" book, sections 1-3 and the OOS-TOLERANCE addendum
Compiled 2026-10-31 16:25Z. Research only. Prereg `l2vast/ds3/prereg/SIXTY_prereg.md` sha256 6b927b6f9edd9533f73fa16934cd2ecdfa0d205c86ca58bbc0c1acdf5a6f31e8 (DECISIONS.md, before any scored cell). Masks capped 20260206, UNTOUCHED never read. PLAN36 (per contract first, stack second, session column), QUANT-LAYER, no gate softened. Code `l2vast/ds3/code/sixty/`, outputs `l2vast/ds3/out/sixty/`, rows `l2vast/ds3/out/recent_wins/sixty.csv`. Section 4 (D7 slots, STOP rules) is SIXTY-2's page; section 1 only says what D6/D7 can run today.

## PAGE 1 - THE PLAIN SENTENCES
**903 distinct rules clear 0.60 (382 clear 0.70), including 380 CF-COMBO rules (336 at 0.70) that I re-scored per contract on the all-signal gain (the ledger had carried the per-fired-trade gain). 206 independent bets among the 493 rules whose stream I could recompute (effective N by eigenvalues 47); the other 384 rules have no stored stream and cannot be clustered. At shrunk size the 252 rules with a positive shrunk size add +107.9k/wk in L6M and +11.8k/wk in PRE (live lots) to the live stack, and change the stack's PRE worst-20 weeks by -7.8% (negative = a deeper tail, positive = shallower): NOW-ONLY deepens it, TOLERANT +27.6%, STRICT +47.1% shallower - but STRICT and TOLERANT require PRE>0 (and PRE/X' picked each rule's representative), so PRE is a selected window for them, not evidence; on the lock-engine stack-delta streams alone NOW-ONLY is -24.4% and the +107.9k of L6M is dominated by trade-sum programs (M-basis per-contract deltas), see section 3c. The alt-bar rules contribute 0 of that: no alt-bar rule is in the ledger at 0.60 (15 alt-bar bracket rows score >= 0.60 but have no L6M, so they are not in the 14,741); the alt-method rules (ZONES-2 entries) contribute +0.2k/wk of it at shrunk size. Out of sample (walk-forward 2024-04..2025-11, outcome the next 3 months) the >= 0.60 selection stayed positive 51% of the time (CI 45-57%) vs 41% for 'positive last 3 and 6 months' and 33% for every active series; a random pick of the same count from the positive-3m/6m pool gives 41% (the score ranks above 75% of random draws, below the 95% bar), and it kept -2% of its last-13-week dollars in the next 3 months.**

**FINAL SENTENCE: 903 rules clear 60% (382 clear 70%); 206 independent bets (47 by eigenvalue) among the 493 that have a recomputable stream, the other 384 unknown; together at shrunk size they add +107.9k $/wk (L6M, live lots, in-sample by selection; +11.8k in PRE) at a PRE worst-20 7.8% deeper than the stack alone (the TOLERANT subset: 27.6% shallower); [stack-delta streams only (no trade-sum programs): +52.5k L6M, +6.8k PRE, PRE worst-20 -24.4%; negative = deeper tail]; the alt-bar rules contribute 0 of that (none clears 60%; the alt-method ZONES-2 rules +0.2k); out of sample the >= 60% selection held 51% of the time (CI 45-57%) vs 41% for rules positive in the last 3 and 6 months and 33% for everything, with the dollars after 3 months at -2% of the recent dollars.**

**The coin-flip question.** The 51% is not a coin-flip edge once you look at what is scored. The family mix of today's list at 0.60 (confirmation 42%, entry filter 36%, regime 10%, sizing 7%, exit 6%) has a study-wide base rate of 42% and RE-1's own walk-forward score at >= 0.60 gets 31% on that mix, because the confirmation family (CF-COMBO, 42% of the list) stayed positive only 4% of the time at >= 0.60 in the study (77 rule-months). Study-wide the 0.60+ score gets 65%, but 3,131 of its 6,453 rule-months are profit-protect exits at 93% and without exits it is 39%. **Addendum:** TOLERANT keeps 78% of STRICT's reliability lift over NOW-ONLY (44.5% vs 45.6% vs 40.8%; paired TOLERANT-STRICT -1.0 pts, CI -4.5..+2.0) with 1.37x the series per month in the walk-forward; on today's list the literal gate does NOT give more rules: 167 evaluable TOLERANT vs 543 STRICT overall (the 370 further rules that pass everything except a PRE worst-20 are almost all CF-COMBO, which have no weekly stream), and among the 519 streamed rules 167 TOLERANT vs 174 STRICT. The reason is the gate's last clause: for L6M>0, 'the L6M-to-PRE drop is less than 100% of the L6M gain' is exactly PRE>0, stricter than the -0.5 MDE clause and the same bar STRICT sets on PRE (structural question in MORNING.md). **Plain sentence for the user's decision: with L6M > 0, clause 5 reduces to PRE > 0.** The literal gate stays the headline. With that clause dropped (TOLERANT-b, POST-HOC reading, not the gate) the walk-forward hit rate is 43.2% and the evaluable list has 249 rules. So the claim 'most of STRICT's reliability' holds, 'far more rules' does not on the literal gate; and both columns lift the hit rate only from ~41% to ~45%, and the dollars after 3 months are negative for every column (-0.4k, -0.6k, -0.9k/wk per selected series, live lots).

| column (LIST60, de-duplicated) | rules (0.60) | rules (0.70) | of which streamed | independent bets (clusters / eff. N, streamed) | walk-forward: positive after 3 months | paired lift vs NOW-ONLY | $ next 3m per series (live/wk) | shrunk portfolio L6M / PRE ($k/wk live) | PRE worst-20 vs stack | SD of sum / sum of SDs |
|---|---|---|---|---|---|---|---|---|---|---|
| STRICT | 543 | 342 | 169 | 72 / 25 | 45.6% [41-50] | +4.8 pts [+1.2, +8.7] | -0.4k | +55.1k / +20.2k | +47.1% | 0.31 |
| TOLERANT | 167 | 11 | 163 | 72 / 26 | 44.5% [40-50] | +3.8 pts [+0.9, +7.0] | -0.6k | +21.2k / +8.1k | +27.6% | 0.30 |
| NOW-ONLY | 903 | 382 | 493 | 206 / 47 | 40.8% [37-44] | baseline | -0.9k | +107.9k / +11.8k | -7.8% | 0.27 |
| score >= 0.60 (walk-forward, within the stream universe) | - | - | - | - | 51.0% [45-57] | +10.3 pts [+4.5, +16.3] | -0.1k | - | - | - |

Reading the table: columns are nested by construction in the walk-forward (STRICT within NOW-ONLY); the portfolio columns use today's list, so L3M/L6M/HOLD are in-sample by selection (positive by construction) - PRE and X' are not selected on for NOW-ONLY (they are for STRICT and TOLERANT; each rule's representative variant was chosen on PRE+X'): NOW-ONLY contributes +11.8k and +20.5k/wk there. `PRE worst-20 vs stack` is the change in the sum of the 20 lowest PRE weeks of stack+portfolio against the live stack alone, as a share of the stack's own (negative = deeper tail, positive = shallower). SD of sum / sum of SDs is the portfolio of rule deltas alone (0.27-0.31 is what a random draw from the same programs gives, 0.28; the list is not more diversified than random). **Everything is POST-HOC**: the 0.60 / 0.70 cuts and the three columns' thresholds were stated by the user before scoring (not post-hoc as gates); the dedup representative, the tier rubric, the clustering cut (rho >= 0.5), the shrunk-size construction and the regime-carrier test are my choices, labelled post-hoc.

**What I recomputed and what I could not (read before using any number).** (1) CF-COMBO: the ledger rows carried `add`, the gain per FIRED trade (fill 0.3-0.8); DS3_CONFIRM_COMBOS_FINAL.md defines the primary as the ALL-signal paired gain per contract (`add_all`). I rebuilt all 807 CF-COMBO cells from the stored look tables, kept those with corrected L3M>0 and L6M>0 (769), recomputed MDE (add_mde x fill, an approximation), persistence (RE-1 formula, unchanged) and shrink, and tagged them `CFC-corrected`: 380 distinct rules clear 0.60. They have no weekly stream (the look tables are window summaries), so they are ledger-only: no monthly series, no TOLERANT worst-20, no correlation, no portfolio line. (2) The RE-1 persistence score is a logistic model (study AUC 0.507) on family, a 6-month t and neutral features; for 785 of 903 distinct rules it was built from a proxy (z6 = sqrt 2 x z3, neutral streak), not a stored monthly series; the corrected CF-COMBO scores sit at the model ceiling (0.60-0.75) because their z6 is large. RE-1 NEW/RISING status is likewise a proxy for most rows. Section 2 does not read the ledger: monthly series are recomputed from cell streams. (3) Streams: 519 of 903 rules now have a weekly stream: EINT1, EINT2, ZONES-2, ADDUW (365, as before) plus 154 built from stored per-day/per-trade data in this follow-up (META FS1/FS2 44, EQR 26, SPLIT 4, UF-ENTRY 28, L2SE 1, THPC2 12, THL 10, EXP1 7, L2SP 6, UF-LOSS 13, UF-PROFIT 1, CUTWAIT 2; each tied to the ledger L3M/L6M within 2%, UF to its 3-decimal rounding). Not buildable: ZONES-2 ADDENDUM (3, only window summaries stored) and one UF-LOSS c3 WT row (lot map irreproducible); CF-COMBO (380, summaries only). The 51 per-contract streams are trade sums at the ledger lot map (not the live lot map, not lock engine); the 103 stack streams are in the units their notes state (live). EQR is a stack scaler, not additive, and is excluded from the correlation and portfolio. The META/UF-ENTRY/SPLIT/L2SE rows overlap heavily (same stack base). (4) The portfolio is the ADDITIVE sum of individually computed deltas; no joint lock-engine re-run. (5) Weekly buckets: a week counts in a window if any day does (L3M = last 13 weeks); stream windows therefore differ from the day-exact ledger windows (only 10 of the 103 stack streams are within 2% of the ledger at weekly buckets), and the gates require BOTH ledger and stream windows to pass. The live stack is the ONE_CONVENTION as-is (`ASIS|off`), the Sunday composite its `COMP|s0.25|k670|off`, live lots; research streams are divided by 2.35. (6) The walk-forward universe (2d) is unchanged: only the four full program universes; the added streams are only the selected ledger rows (a look-ahead-selected set) and are not in the walk-forward.

## 1. THE 60% LIST (RE-1 ledger, 14,741 rows)
Ledger rows with persistence >= 0.60 after the CF-COMBO correction: **1520** (>= 0.70: **581**) -> **903 distinct rules** at 0.60 and **382 rules** at 0.70 (de-duplication: same program, book, session and mechanic with every number replaced by '#', representative = best mean of PRE and X'; no L3M/L6M look). Of the 14,741 ledger rows the 684 CF-COMBO rows carried the per-fired-trade gain (the first version of this page excluded them: 563 rows at 0.60); they are re-scored per contract on the all-signal gain (see page 1, item 1) and tagged CFC-corrected: **380 rules at 0.60, 336 at 0.70**. Of the 903 rules 519 have a recomputable weekly stream (EINT1 109, ZONES-2 137, EINT2 87, ADDUW 32 from the first pass; META 44, EQR 26, UF-ENTRY 28, SPLIT 4, L2SE 1, THPC2 12, THL 10, EXP1 7, L2SP 6, UF-LOSS 13, UF-PROFIT 1, CUTWAIT 2 built in the follow-up); 384 are ledger-only (380 CF-COMBO, 3 ZONES-2 ADDENDUM, 1 UF-LOSS). Persistence in the ledger rows affected by proxies: 785 of 903 rules at 0.60 have a score built without a stored monthly series (372 of 382 at 0.70).

| list | rules | STRICT | TOLERANT (literal, evaluable) | TOLERANT unevaluated but all else passes | TOLERANT-b (clause 5 dropped, POST-HOC) | NOW-ONLY | streamed |
|---|---|---|---|---|---|---|---|
| >= 0.60 | 903 | 543 | 167 | 370 | 249 | 903 | 519 |
| >= 0.70 | 382 | 342 | 11 | 326 | 15 | 382 | 39 |

By program (LIST60, distinct rules / STRICT / TOLERANT / tiers CANDIDATE vs DEAD / sum of positive shrunk $/wk at live lots, NOT additive):

| program | family | rules | STRICT | TOLERANT | CANDIDATE | DEAD | ledger-only? | sum shrunk $/wk live |
|---|---|---|---|---|---|---|---|---|
| ADDUW B1 | sizing | 1 | 0 | 0 | 0 | 1 | no | 1,421 |
| ADDUW B2 | sizing | 31 | 29 | 25 | 29 | 2 | no | 16,358 |
| CF-COMBO FOUR | confirmation | 27 | 27 | 0 | 19 | 8 | yes | 0 |
| CF-COMBO GREEDY | confirmation | 1 | 1 | 0 | 1 | 0 | yes | 0 |
| CF-COMBO POOL | confirmation | 196 | 196 | 0 | 17 | 179 | yes | 0 |
| CF-COMBO stage1B | confirmation | 14 | 0 | 0 | 0 | 14 | yes | 0 |
| CF-COMBO stage1ENG | confirmation | 142 | 142 | 0 | 46 | 96 | yes | 0 |
| CUTWAIT | exit | 2 | 1 | 2 | 1 | 1 | no | 5,633 |
| EINT1 | entry filter | 109 | 22 | 33 | 38 | 71 | no | 117,945 |
| EINT2 | regime | 87 | 18 | 24 | 6 | 81 | no | 0 |
| EQR lots_factor | sizing | 26 | 5 | 4 | 0 | 26 | no | 303,982 |
| EXP1 loss per-stream fixed | exit | 6 | 1 | 0 | 1 | 5 | no | 13,977 |
| EXP1 profit fixed | exit | 1 | 1 | 1 | 0 | 1 | no | 25,348 |
| L2SE entry (THP_POLICY entry) | entry structure | 1 | 0 | 0 | 0 | 1 | no | 0 |
| L2SP profit (THP_POLICY profit) | exit | 6 | 4 | 2 | 0 | 6 | no | 142,808 |
| META FS1 | entry filter | 18 | 4 | 3 | 0 | 18 | no | 19,051 |
| META FS2 | entry filter | 26 | 3 | 3 | 4 | 22 | no | 37,592 |
| SPLIT 70/30 | sizing | 4 | 2 | 1 | 2 | 2 | no | 8,546 |
| THL (THLB classic loss rules) | exit | 10 | 4 | 1 | 1 | 9 | no | 43,289 |
| THPC2 (profit) | exit | 12 | 6 | 2 | 3 | 9 | no | 472,899 |
| UF-ENTRY c1 | entry filter | 9 | 8 | 0 | 8 | 1 | no | 46,296 |
| UF-ENTRY c2 | entry filter | 11 | 8 | 1 | 8 | 3 | no | 26,887 |
| UF-ENTRY c3 | entry filter | 2 | 2 | 0 | 2 | 0 | no | 7,839 |
| UF-ENTRY c4 | entry filter | 6 | 4 | 0 | 4 | 2 | no | 25,027 |
| UF-LOSS c1 | exit | 5 | 3 | 3 | 3 | 2 | no | 7,831 |
| UF-LOSS c3 | exit | 7 | 3 | 0 | 3 | 4 | no | 82,644 |
| UF-LOSS c4 | exit | 1 | 1 | 1 | 1 | 0 | no | 1,030 |
| UF-LOSS c6 | exit | 1 | 1 | 1 | 1 | 0 | no | 263 |
| UF-PROFIT c4 | exit | 1 | 0 | 0 | 0 | 1 | no | 1,276 |
| ZONES-2 | entry filter | 137 | 45 | 60 | 63 | 74 | no | 632 |
| ZONES-2 ADDENDUM | entry filter | 3 | 2 | 0 | 3 | 0 | yes | 1,958 |

Tiers (post-hoc rubric, prereg F): PASS needs L3M > MDE, L6M and HOLD > 0, PRE and X' > 0, placebo rank >= 0.95, a fill basis that is not an artefact, a recomputed and tied-out stream. **0 PASS.** CANDIDATE = fails only some of those but not the -0.5 MDE / L6M-HOLD / artefact gates; DEAD otherwise. The failed gates are in column `failed_gates` of the CSV. The placebo rank is missing for most rows (the program did not store one), which by itself blocks PASS.

Tier counts LIST60: {'DEAD': 639, 'CANDIDATE': 263, 'CANDIDATE (TOLERANT unevaluated: no weekly stream)': 1}; LIST70: {'DEAD': 293, 'CANDIDATE': 89}.

**Top 30 by shrunk $/wk at live lots** (sorted; rows flagged `unit-inflated` (EQR lot factors) are ranked last and not shown; full 903-row list with every column in `l2vast/ds3/out/sixty/sixty_list60.csv` and `l2vast/ds3/out/recent_wins/sixty.csv`). Units: windows are the ledger primary measure (pts per contract per base trade for pts rows, $/wk research-lot stack for stack rows; the unit is in `prim_unit`); MDE beside the L3M window in the same unit; shrunk $/wk = max(shrink,0) x L3M $/wk at live lots (stream rows research/2.35; ledger-only per-contract rows use the ledger live $ / 13, a per-contract sum that is NOT a lock-engine number).

| # | program / family | book / session | bar / TF | mechanic (cell) | L3M | L6M | HOLD | PRE | X' | MDE L3M | tr/wk | t6 | score (drivers) | shrunk $/wk | status | D6 / D7 today | S/T/N | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | qr_profit|qr|YTD|S1w|reg | 1.58 | 0.63 | 0.39 | 0.10 | 0.01 | 338,811.54 | 424.6 | 4.5 | 0.66 (t6 4.5, age proxy, plc n/a, PRE +) | 62,311 | NEW | PARTLY: D6 profit group / THP_POLICY line; this  | S-N | CANDIDATE |
| 2 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | dp_profit|dp|2w|Sintra|tod | 1.46 | 0.94 | 0.95 | 0.39 | -0.57 | 312,572.79 | 424.6 | 3.6 | 0.61 (t6 3.6, age proxy, plc n/a, PRE +) | 52,144 | RISING | PARTLY: D6 profit group / THP_POLICY line; this  | --N | DEAD |
| 3 | L2SP profit (THP_POLIC / exit | ST,HM,WT,KB,SM,PE / ALL | live 1-min engine bars (no alt bar | ST,HM,WT,KB,SM,PE|P|sess_tot_ge1.2|armpct0.7|d10|take|p7 | 1.37 | 1.04 | 1.07 | 0.32 | 0.41 | 291,756.35 | 424.6 | 3.5 | 0.61 (t6 3.5, age proxy, plc n/a, PRE +) | 50,918 | RISING | RUNS TODAY: in THP_POLICY profit lines (pct >= 0 | S-N | DEAD |
| 4 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | dp_profit|dp|2w|S1w|tod | 1.38 | 0.92 | 0.95 | 0.27 | -0.55 | 280,537.93 | 424.6 | 3.6 | 0.61 (t6 3.6, age proxy, plc n/a, PRE +) | 50,764 | RISING | PARTLY: D6 profit group / THP_POLICY line; this  | --N | DEAD |
| 5 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | dp_profit|dp|2w|S1d|tod | 1.40 | 0.92 | 0.93 | 0.41 | -0.57 | 299,012.84 | 424.6 | 3.5 | 0.61 (t6 3.5, age proxy, plc n/a, PRE +) | 50,601 | RISING | PARTLY: D6 profit group / THP_POLICY line; this  | --N | DEAD |
| 6 | L2SP profit (THP_POLIC / exit | ST,HM,WT,KB,SM,PE / ALL | live 1-min engine bars (no alt bar | ST,HM,WT,KB,SM,PE|P|sess_tot_ge1.2|armpct0.7|d10|trail30 | 1.34 | 1.04 | 1.07 | 0.34 | 0.43 | 283,828.19 | 424.6 | 3.4 | 0.60 (t6 3.4, age proxy, plc n/a, PRE +) | 49,893 | RISING | RUNS TODAY: in THP_POLICY profit lines (pct >= 0 | S-N | DEAD |
| 7 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | qr_profit|qr|YTD|S1w|none | 1.06 | 0.72 | 0.45 | 0.03 | 0.17 | 324,200.06 | 424.6 | 3.4 | 0.60 (t6 3.4, age proxy, plc n/a, PRE +) | 46,066 | RISING | PARTLY: D6 profit group / THP_POLICY line; this  | --N | DEAD |
| 8 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | qr_profit|qr|12m|S1w|none | 1.14 | 0.57 | 0.43 | 0.33 | 0.09 | 298,504.85 | 424.6 | 3.4 | 0.60 (t6 3.4, age proxy, plc n/a, PRE +) | 43,130 | NEW | PARTLY: D6 profit group / THP_POLICY line; this  | STN | CANDIDATE |
| 9 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | qr_profit|qr|6m|S1d|reg | 1.11 | 0.35 | 0.55 | 0.30 | 0.36 | 153,345.86 | 424.6 | 4.4 | 0.66 (t6 4.4, age proxy, plc n/a, PRE +) | 38,046 | NEW | PARTLY: D6 profit group / THP_POLICY line; this  | S-N | CANDIDATE |
| 10 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | qr_profit|qr|6m|S1m|reg | 0.93 | 0.55 | 0.96 | 0.23 | 0.02 | 150,667.38 | 424.6 | 3.9 | 0.63 (t6 3.9, age proxy, plc n/a, PRE +) | 32,669 | RISING | PARTLY: D6 profit group / THP_POLICY line; this  | S-N | DEAD |
| 11 | UF-LOSS c3 / exit | ALL / all | live 1-min engine bars (no alt bar | loss|avoid|cumb_le=0.5 [scope ALL] | 0.76 | 0.44 | 0.40 | 0.30 | 0.17 | 154,499.22 | 22.2 | 3.5 | 0.61 (t6 3.5, age 5, plc n/a, PRE +) | 30,645 | RISING | PARTLY: D6 loss-exit group; this variant needs i | S-N | CANDIDATE |
| 12 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | qr_profit|qr|6m|S1w|reg | 0.88 | 0.39 | 1.20 | 0.11 | -0.12 | 137,264.15 | 424.6 | 3.9 | 0.63 (t6 3.9, age proxy, plc n/a, PRE +) | 29,093 | NEW | PARTLY: D6 profit group / THP_POLICY line; this  | --N | DEAD |
| 13 | UF-LOSS c3 / exit | ALL / all | live 1-min engine bars (no alt bar | loss|avoid|drel_le=0.5 [scope ALL] | 0.68 | 0.24 | 0.21 | 0.22 | 0.10 | 139,537.84 | 16.4 | 3.6 | 0.61 (t6 3.6, age 3, plc n/a, PRE +) | 28,745 | NEW | PARTLY: D6 loss-exit group; this variant needs i | S-N | CANDIDATE |
| 14 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | qr_profit|qr|ew20|S1w|reg | 0.64 | 0.21 | -0.21 | 0.00 | 0.02 | 151,077.97 | 424.6 | 3.6 | 0.61 (t6 3.6, age proxy, plc n/a, PRE +) | 25,699 | NEW | PARTLY: D6 profit group / THP_POLICY line; this  | --N | DEAD |
| 15 | EXP1 profit fixed / exit | ALL10 profit side / ALL | live 1-min engine bars (no alt bar | F7_take_p90 | 0.57 | 0.63 | 0.61 | 0.23 | 0.06 | 63,935.18 | 424.6 | 5.4 | 0.71 (t6 5.4, age proxy, plc n/a, PRE +) | 25,348 | STABLE | PARTLY: D6 profit group / THP_POLICY line; this  | STN | DEAD |
| 16 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | qr_profit|qr|6m|S1m|none | 0.58 | 0.78 | 1.17 | 0.15 | 0.03 | 41,053.65 | 424.6 | 6.6 | 0.77 (t6 6.6, age proxy, plc n/a, PRE +) | 23,735 | FADING | PARTLY: D6 profit group / THP_POLICY line; this  | S-N | DEAD |
| 17 | THPC2 (profit) / exit | ALL books (pooled  / ALL | live 1-min engine bars (no alt bar | qr_profit|qr|ew20|S1m|none | 0.49 | 0.20 | 0.30 | 0.16 | 0.22 | 68,827.41 | 424.6 | 6.2 | 0.75 (t6 6.2, age proxy, plc n/a, PRE +) | 18,640 | NEW | PARTLY: D6 profit group / THP_POLICY line; this  | STN | DEAD |
| 18 | META FS2 / entry filter | POOLED / ALL | live 1-min engine bars (no alt bar | H1_6m|P3|POOLED|cfg7 | 47,967.52 | 9,277.95 | 3,799.90 | -1,324.52 | 2,455.00 | 88,255.11 | 1.1 | 4.0 | 0.69 (t6 4.0, age proxy, plc 1.00, PRE -) | 13,763 | NEW | NO: model-scored filter (needs a scoring module) | --N | DEAD |
| 19 | L2SP profit (THP_POLIC / exit | WT / ALL | live 1-min engine bars (no alt bar | WT|P|sess_ahead_ge1.2|armpts15|d30|trail20|p70always | 1.99 | 2.20 | 2.36 | 0.51 | -0.93 | 45,584.24 | 73.4 | 4.5 | 0.67 (t6 4.5, age proxy, plc n/a, PRE +) | 12,224 | STABLE | RUNS TODAY: in THP_POLICY profit lines (pct >= 0 | --N | DEAD |
| 20 | L2SP profit (THP_POLIC / exit | WT / ALL | live 1-min engine bars (no alt bar | WT|P|hour_tot_ge1.2|armpts20|d0|trail20|p70always | 1.85 | 2.05 | 2.30 | 0.30 | -0.41 | 44,358.78 | 73.4 | 4.3 | 0.65 (t6 4.3, age proxy, plc n/a, PRE +) | 11,359 | STABLE | RUNS TODAY: in THP_POLICY profit lines (pct >= 0 | --N | DEAD |
| 21 | THL (THLB classic loss / exit | HM / ALL | live 1-min engine bars (no alt bar | L6_a30_r3_w60|HM | 4.18 | 2.32 | 2.21 | 0.52 | 1.10 | 52,807.62 | 23.5 | 3.6 | 0.61 (t6 3.6, age proxy, plc 0.75, PRE +) | 10,248 | RISING | PARTLY: D6 loss-exit group; this variant needs i | STN | DEAD |
| 22 | L2SP profit (THP_POLIC / exit | KB / ALL | live 1-min engine bars (no alt bar | KB|P|hour_tot_ge1.2|armpct0.7|d0|trail30|p70always | 2.89 | 1.18 | 1.46 | 0.10 | 0.90 | 43,327.94 | 56.0 | 3.7 | 0.62 (t6 3.7, age proxy, plc n/a, PRE +) | 9,354 | NEW | RUNS TODAY: in THP_POLICY profit lines (pct >= 0 | STN | DEAD |
| 23 | L2SP profit (THP_POLIC / exit | KB / ALL | live 1-min engine bars (no alt bar | KB|P|t60_ahead_ge2.0|armpct0.7|d0|trail30|p70always | 2.94 | 1.36 | 1.58 | 0.04 | 0.98 | 40,096.81 | 56.0 | 3.9 | 0.63 (t6 3.9, age proxy, plc n/a, PRE +) | 9,058 | NEW | RUNS TODAY: in THP_POLICY profit lines (pct >= 0 | STN | DEAD |
| 24 | EINT1 / entry filter | ENG / ALL | live 1-min engine bars (no alt bar | skipBot3_htf_d_open_atr|ENG | 78,635.32 | 17,030.65 | 11,508.10 | -23,870.62 | -2,575.52 | 82,804.79 | 1.1 | 3.9 | 0.68 (t6 3.9, age 1, plc n/a, PRE -) | 8,456 | NEW | NO: needs engine feature (htf_d_open_atr) comput | --N | DEAD |
| 25 | UF-ENTRY c3 / entry filter | all 6 engine books / all | live 1-min engine bars (no alt bar | UF3|PZ|C|half|z1.2 | ref=market | 30,828.00 | 29,795.00 | 27,977.00 | 13,075.00 | 11,436.00 | 82,862.76 | 1.1 | 3.7 | 0.67 (t6 3.7, age proxy, plc n/a, PRE +) | 7,839 | STABLE | NO / not assessed | S-N | CANDIDATE |
| 26 | UF-ENTRY c1 / entry filter | all 6 engine books / all | live 1-min engine bars (no alt bar | UF1|G3|F=0.7|X1=3|X2=8|N=0 | ref=market | 27,386.00 | 28,914.00 | 26,425.00 | 5,525.00 | 7,961.00 | 81,417.95 | 1.1 | 3.2 | 0.64 (t6 3.2, age proxy, plc n/a, PRE +) | 7,645 | STABLE | NO / not assessed | S-N | CANDIDATE |
| 27 | META FS2 / entry filter | asia / asia | live 1-min engine bars (no alt bar | H2_ENS|P5|asia|cfg134 | 27,112.19 | 3,013.52 | -1,382.85 | 9,804.19 | -439.09 | 79,297.51 | 1.1 | 3.1 | 0.63 (t6 3.1, age proxy, plc 1.00, PRE +) | 7,531 | NEW | NO: model-scored filter (needs a scoring module) | --N | DEAD |
| 28 | UF-LOSS c3 / exit | ALL / all | live 1-min engine bars (no alt bar | loss|trig=L6a40w10|gate=sess4|rem=TS300 [scope ALL] | 0.19 | 0.06 | 0.06 | -0.00 | 0.04 | 36,304.12 | 9.5 | 4.0 | 0.64 (t6 4.0, age 3, plc n/a, PRE -) | 7,003 | NEW | PARTLY: D6 loss-exit group; this variant needs i | --N | DEAD |
| 29 | UF-LOSS c3 / exit | ALL / all | live 1-min engine bars (no alt bar | loss|trig=L6a40w10|gate=sess4|rem=TR20 [scope ALL] | 0.18 | 0.05 | 0.06 | -0.01 | 0.04 | 36,504.86 | 9.5 | 3.6 | 0.61 (t6 3.6, age 0, plc n/a, PRE -) | 6,865 | NEW | PARTLY: D6 loss-exit group; this variant needs i | --N | DEAD |
| 30 | UF-ENTRY c4 / entry filter | all 6 engine books / all | live 1-min engine bars (no alt bar | UF4|P|S|6m|ce1|fbC | ref=market | 25,511.00 | 25,303.00 | 23,582.00 | 7,282.00 | 11,248.00 | 77,278.69 | 1.1 | 3.3 | 0.64 (t6 3.3, age proxy, plc n/a, PRE +) | 6,591 | STABLE | NO / not assessed | S-N | CANDIDATE |

The top of this table is not a trading list. Rows from THPC2 / L2SP / EXP1 / UF-LOSS / CF-COMBO are per-contract deltas on the M (measured) fill basis (trade sums, not lock-engine), and several carry the ledger's own warning that the M-basis gain is a target-fill artefact (N-basis L3M <= 0): they are DEAD here. The stack-level programs (EINT1, ADDUW, META, UF-ENTRY) are the only ones whose dollars are lock-engine numbers.

**The >= 0.70 list (46 rules):** CF-COMBO POOL 173, CF-COMBO stage1ENG 127, CF-COMBO FOUR 24, CF-COMBO stage1B 12, EINT1 10, EQR lots_factor 8, ZONES-2 8, EINT2 5, THPC2 (profit) 3, EXP1 loss per-stream fixed 3, META FS2 3, META FS1 2, ADDUW B2 1, EXP1 profit fixed 1, SPLIT 70/30 1, UF-ENTRY c1 1. STRICT 342, TOLERANT 11 (+326 unevaluated), NOW-ONLY 382; tiers {'DEAD': 293, 'CANDIDATE': 89}. Sorted by shrunk $/wk, top 10:

| # | program | book | cell | L3M | L6M | HOLD | PRE | X' | score | shrunk $/wk | S/T/N | tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | EXP1 profit fixed | ALL10 profit s | F7_take_p90 | 0.57 | 0.63 | 0.61 | 0.23 | 0.06 | 0.71 | 25,348 | STN | DEAD |
| 2 | THPC2 (profit) | ALL books (poo | qr_profit|qr|3m|S1w|none | 0.63 | 0.14 | -0.19 | 0.03 | -0.33 | 0.70 | 25,268 | --N | DEAD |
| 3 | THPC2 (profit) | ALL books (poo | qr_profit|qr|6m|S1m|none | 0.58 | 0.78 | 1.17 | 0.15 | 0.03 | 0.77 | 23,735 | S-N | DEAD |
| 4 | THPC2 (profit) | ALL books (poo | qr_profit|qr|ew20|S1m|none | 0.49 | 0.20 | 0.30 | 0.16 | 0.22 | 0.75 | 18,640 | STN | DEAD |
| 5 | UF-ENTRY c1 | all 6 engine b | UF1|G2|F=0.7|X=3|ev=IMBF20 | ref=market | 23,058.00 | 26,742.00 | 23,500.00 | 9,766.00 | 1,811.00 | 0.71 | 5,781 | S-N | CANDIDATE |
| 6 | META FS2 | nyam | H3_ENS|P2|nyam|cfg436 | 23,236.34 | 9,534.37 | 9,220.68 | -3,397.83 | -2,724.41 | 0.76 | 5,730 | --N | DEAD |
| 7 | META FS2 | HM-asia | H2_ENS|P3|HM-asia|cfg797 | 21,103.05 | 13,674.91 | 10,440.53 | 1,169.01 | 163.72 | 0.71 | 5,204 | S-N | CANDIDATE |
| 8 | EINT1 | HM | skipBot3_htf_d_open_atr|HM | 41,327.32 | 14,671.09 | 11,173.45 | -11,896.15 | -3,865.08 | 0.85 | 4,099 | --N | DEAD |
| 9 | SPLIT 70/30 | STACK | fam=F5|F=0.7|X=10|N=2|chase=none|veto=v4 [STACK] | 31,904.05 | 21,831.59 | 17,242.83 | 1,350.28 | 5,315.18 | 0.71 | 4,016 | S-N | CANDIDATE |
| 10 | EINT1 | HM | skipBot3_htf_wk_open_atr|HM | 41,667.57 | 16,249.78 | 11,332.22 | 1,334.78 | 2,771.83 | 0.75 | 3,746 | S-N | CANDIDATE |

**Count and independent exposures.** 903 rules at 0.60; among the 519 with streams: 206 clusters at weekly rho >= 0.5 (average linkage), effective N 47 by eigenvalues; the other 384 rules are programs with no weekly stream (their overlap with the streamed bets is unknown).

## 2. THE REGIME ARGUMENT, TESTED
**2a. Monthly series.** Each streamed rule's monthly series since 2023-04 (34 months) is in `rules_monthly_regime.csv` (sign string per month, mean $/wk live in 2023, 2024, 2025-26, the regime-carrier test). Ten largest streamed rules by shrunk $/wk:

| rule | 2023-04..2026-01 monthly sign (+/-) | 2023 $/wk | 2024 $/wk | 2025-26 $/wk | 2025-26 minus 2024, t | best regime measure (Spearman, n=34) |
|---|---|---|---|---|---|---|
| THPC2 (pro qr_profit|qr|YTD|S1w|reg (ALL books (pooled chain)) | `...-+++--+++----+--++---+++----+++` | 341 | 2,609 | 11,659 | +0.4 | vol (NQ rv5 daily %) +0.36 (p 0.034) |
| THPC2 (pro dp_profit|dp|2w|Sintra|tod (ALL books (pooled chain)) | `...++-----+++---++----+-++++++++++` | -8,207 | -1,837 | 48,498 | +1.9 | book depth (top10 median) -0.52 (p 0.002) |
| L2SP profi ST,HM,WT,KB,SM,PE|P|sess_tot_ge1.2|armpct0.7 (ST,HM,WT,KB,SM,PE) | `++++++++---++-+-++----++++++++++++` | 20,274 | -16,848 | 63,392 | +3.2 | book depth (top10 median) -0.55 (p 0.001) |
| THPC2 (pro dp_profit|dp|2w|S1w|tod (ALL books (pooled chain)) | `...++--+--+++---++----+--+++++++++` | -8,225 | -6,915 | 45,818 | +1.9 | book depth (top10 median) -0.47 (p 0.005) |
| THPC2 (pro dp_profit|dp|2w|S1d|tod (ALL books (pooled chain)) | `...++--+--+++---++----+-++++++++++` | -8,135 | -1,501 | 48,600 | +1.9 | book depth (top10 median) -0.52 (p 0.002) |
| L2SP profi ST,HM,WT,KB,SM,PE|P|sess_tot_ge1.2|armpct0.7 (ST,HM,WT,KB,SM,PE) | `++++++++---++-+-++----++++++++++++` | 19,816 | -14,793 | 63,314 | +3.2 | book depth (top10 median) -0.56 (p 0.001) |
| THPC2 (pro qr_profit|qr|YTD|S1w|none (ALL books (pooled chain)) | `...-++---+-++-+-+--+----++--++++++` | 3,935 | -318 | 14,220 | +0.7 | ES-NQ corr 20m +0.37 (p 0.031) |
| THPC2 (pro qr_profit|qr|12m|S1w|none (ALL books (pooled chain)) | `...-++----+++--++---++++++-+-+++++` | 3,935 | 12,327 | 21,350 | +0.5 | ES-NQ corr 20m +0.36 (p 0.038) |
| THPC2 (pro qr_profit|qr|6m|S1d|reg (ALL books (pooled chain)) | `...+-+-+----+---++-++++-++++---+++` | 16,133 | 5,972 | 29,387 | +1.4 | book depth (top10 median) -0.36 (p 0.036) |
| THPC2 (pro qr_profit|qr|6m|S1m|reg (ALL books (pooled chain)) | `...-++++---++-.--+--+++-++-+++-++-` | 6,968 | -3,709 | 45,491 | +2.0 | ES-NQ corr 20m +0.34 (p 0.053) |

**2b. 2024 versus 2025-26.** 
| program | rules | mean 2024 $/wk live | mean 2025-26 $/wk live | share with 2025-26 > 0 | share with |t| > 2 for the change |
|---|---|---|---|---|---|
| ADDUW B1 | 1 | -148 | 2,747 | 100% | 0% |
| ADDUW B2 | 31 | 605 | 1,405 | 90% | 10% |
| CUTWAIT | 2 | 674 | 426 | 100% | 0% |
| EINT1 | 109 | 223 | 777 | 82% | 3% |
| EINT2 | 87 | -188 | 349 | 75% | 6% |
| EQR lots_factor | 26 | -1,755 | 8,337 | 85% | 12% |
| EXP1 loss per-stream fixed | 6 | -457 | 425 | 83% | 0% |
| EXP1 profit fixed | 1 | 4,463 | 31,252 | 100% | 100% |
| L2SE entry (THP_POLICY entry) | 1 | 816 | -927 | 0% | 0% |
| L2SP profit (THP_POLICY profit) | 6 | -8,240 | 29,577 | 100% | 100% |
| META FS1 | 18 | 485 | 875 | 61% | 6% |
| META FS2 | 26 | 429 | 1,159 | 73% | 8% |
| SPLIT 70/30 | 4 | -1,287 | 6,445 | 100% | 25% |
| THL (THLB classic loss rules) | 10 | -478 | 1,034 | 80% | 0% |
| THPC2 (profit) | 12 | -810 | 31,769 | 92% | 17% |
| UF-ENTRY c1 | 9 | 6,108 | 14,754 | 89% | 11% |
| UF-ENTRY c2 | 11 | 6,996 | 12,535 | 91% | 0% |
| UF-ENTRY c3 | 2 | 16,735 | 14,074 | 100% | 0% |
| UF-ENTRY c4 | 6 | 5,881 | 14,946 | 100% | 17% |
| UF-LOSS c1 | 5 | 1 | 1,499 | 80% | 0% |
| UF-LOSS c3 | 6 | 2,815 | 7,062 | 83% | 0% |
| UF-LOSS c4 | 1 | 866 | 1,501 | 100% | 0% |
| UF-LOSS c6 | 1 | -33 | 500 | 100% | 0% |
| UF-PROFIT c4 | 1 | 934 | 1,056 | 100% | 0% |
| ZONES-2 | 137 | 1 | 12 | 94% | 1% |

78% of the 519 streamed rules earn more per week in 2025-26 than in 2024 - which is what a list selected on being positive in L3M/L6M must show - but only 6.0% of them have a change beyond 2 standard errors: the split is mostly noise.

**2c. Regime measures (RECENT-EDGE 5b description, half-year means):**

| measure | 23H1 | 23H2 | 24H1 | 24H2 | 25H1 | 25H2 |
|---|---|---|---|---|---|---|
| vol (NQ rv5 daily %) | 0.945 | 0.890 | 1.066 | 1.104 | 1.152 | 1.016 |
| trend persistence (5m ER20) | 0.278 | 0.281 | 0.266 | 0.265 | 0.261 | 0.263 |
| London share of signals | 0.163 | 0.174 | 0.189 | 0.213 | 0.233 | 0.217 |
| Asia share | 0.258 | 0.254 | 0.254 | 0.244 | 0.278 | 0.279 |
| NY-AM share | 0.307 | 0.277 | 0.282 | 0.281 | 0.254 | 0.279 |
| book depth (top10 median) | 114.000 | 129.000 | 99.000 | 87.000 | 78.000 | 76.000 |
| ES-NQ corr (20m) | 0.860 | 0.869 | 0.896 | 0.909 | 0.932 | 0.931 |
| signals/day | 42.209 | 42.378 | 61.076 | 69.383 | 71.600 | 81.582 |

**Which measure carries the difference.** For each streamed rule I took its monthly mean weekly P&L (34 months) and the Spearman correlation with each of 8 regime measures; a rule gets a carrier only if |rho| >= 0.5 and p < 0.05/8 (POST-HOC test). Result: 18 of 519 rules (3.5%) have a carrier (signals/day x4, ES-NQ corr 20m x4, book depth (top10 median) x4, NY-AM share x3, trend persist (5m ER20) x1, vol (NQ rv5 daily %) x1, London share x1); a random sample of 1,500 series from the whole stream universe gives 4.5%. So the list has fewer regime-linked rules than chance and no measure carries the 2024 vs 2025-26 difference. Rules with a carrier are marked in `regime_reason`; all others read **'no identifiable reason'**: that is 501 of 519 streamed rules. Those that have one: EINT1 doubleBot3_sig_st10_age|HM: works now because its monthly P&L tracks NY-AM share (rho +0.52) - a correlation, not a mechanism; EINT1 doubleTop3_sig_kelt3|HM: works now because its monthly P&L tracks NY-AM share (rho +0.51) - a correlation, not a mechanism; EINT2 d2.dow1.skip|HM: works now because its monthly P&L tracks trend persist (5m ER20) (rho -0.52) - a correlation, not a mechanism; EQR lots C|F|A06 @ lots x1.159: works now because its monthly P&L tracks signals/day (rho +0.52) - a correlation, not a mechanism; EXP1 los SM|L6_a25_r3_w15: works now because its monthly P&L tracks NY-AM share (rho +0.54) - a correlation, not a mechanism; EXP1 pro F7_take_p90: works now because its monthly P&L tracks ES-NQ corr 20m (rho +0.59) - a correlation, not a mechanism; L2SP pro ST,HM,WT,KB,SM,PE|P|sess_tot_ge1.2|armpc: works now because its monthly P&L tracks book depth (top10 median) (rho -0.55) - a correlation, not a mechanism; L2SP pro ST,HM,WT,KB,SM,PE|P|sess_tot_ge1.2|armpc: works now because its monthly P&L tracks book depth (top10 median) (rho -0.56) - a correlation, not a mechanism; L2SP pro WT|P|hour_tot_ge1.2|armpts20|d0|trail20|: works now because its monthly P&L tracks ES-NQ corr 20m (rho +0.54) - a correlation, not a mechanism; L2SP pro WT|P|sess_ahead_ge1.2|armpts15|d30|trail: works now because its monthly P&L tracks ES-NQ corr 20m (rho +0.57) - a correlation, not a mechanism; SPLIT 70 fam=F5|F=0.3|X=15|N=1|chase=imb10|veto=v: works now because its monthly P&L tracks vol (NQ rv5 daily %) (rho +0.58) - a correlation, not a mechanism; THL (THL L8_p40|CR: works now because its monthly P&L tracks signals/day (rho +0.55) - a correlation, not a mechanism; THL (THL L1_x40|CR: works now because its monthly P&L tracks signals/day (rho +0.55) - a correlation, not a mechanism; THL (THL L7s_x45|CR: works now because its monthly P&L tracks signals/day (rho +0.52) - a correlation, not a mechanism; THPC2 (p dp_profit|dp|2w|S1d|tod: works now because its monthly P&L tracks book depth (top10 median) (rho -0.52) - a correlation, not a mechanism; THPC2 (p dp_profit|dp|2w|Sintra|tod: works now because its monthly P&L tracks book depth (top10 median) (rho -0.52) - a correlation, not a mechanism; THPC2 (p qr_profit|qr|ew20|S1m|none: works now because its monthly P&L tracks London share (rho +0.50) - a correlation, not a mechanism; UF-LOSS  loss|wf|w=6m|cad=3m|scope=pooled|crit=t|: works now because its monthly P&L tracks ES-NQ corr 20m (rho +0.53) - a correlation, not a mechanism. For the 384 ledger-only rules there is no monthly series, so 'no identifiable reason' is the default and the data cannot support any other sentence. What did move in the market: realised vol (+10 to +20% vs 2023), London share up 6 points, book depth down by a third, ES-NQ correlation up 7 points, signals/day nearly doubled; trend persistence did not rise.

**2d. Walk-forward of 'take only rules scored >= 0.60 at month M'.** Universe = every active series of the four stream programs (43,660 distinct series), M = 2024-04..2025-11, score at M from the RE-1 formula on data before M, outcome = sum of the next three months > 0. Selection at M uses weeks before M only; the older windows are the rolling analogs in the prereg (halves of the history before M-26 weeks).

| selection at M | series-months | positive after 3 months [month-block 95% CI] | program-equal | random pick of same count from the positive-3m/6m pool | placebo rank | mean next-3m $/wk per series (live) | kept vs last 13 weeks |
|---|---|---|---|---|---|---|---|
| every active series | 867,748 | 33.2% [30-37] | 36.7% | - | - | -2,173 | +124% |
| NOW-ONLY (positive last 3 and 6 months) | 179,261 | 40.8% [37-44] | 42.3% | 41.3% | 0.00 | -887 | -44% |
| STRICT | 36,640 | 45.6% [41-50] | 47.4% | 41.3% | 0.79 | -372 | -24% |
| TOLERANT (literal) | 50,179 | 44.5% [40-50] | 46.3% | 41.3% | 0.69 | -618 | -33% |
| TOLERANT-b (post-hoc) | 94,280 | 43.2% [40-47] | 44.1% | 41.3% | 0.80 | -701 | -34% |
| score >= 0.60 | 1,773 | 51.0% [45-57] | 46.5% | 41.4% | 0.75 | -71 | -2% |
| score >= 0.70 | 113 | 73.5% [64-84] | 62.4% | 41.3% | 0.75 | -221 | -158% |
| score >= 0.60 and STRICT | 562 | 55.7% [47-65] | 53.6% | 41.2% | 0.78 | -117 | -5% |
| score >= 0.60 and TOLERANT | 572 | 52.3% [40-65] | 49.1% | 41.4% | 0.72 | -384 | -12% |
| score >= 0.60 and NOW-ONLY | 1,759 | 50.8% [44-58] | 46.5% | 41.2% | 0.75 | -99 | -2% |

Reading: (1) the 41% reproduces (40.8%). (2) The >= 0.60 selection holds 51.0% (+10.3 pts over the pool, CI +4.5..+16.3) but program-equal weighting gives 47%, it ranks at 0.75 of random draws (not 0.95) and it is not above a coin (CI includes 50%). (3) Score >= 0.70: 73% on 113 series-months in 11 months, 110 of 113 from one program (EINT2 day-type rules): one cluster, not 113 observations. (4) Shrinkage: the selected series gave back all of it - next-3-month dollars per series are -2% of their last-13-week dollars (every set is negative: -24% STRICT, -33% TOLERANT, -44% NOW-ONLY). (5) 2024 vs 2025 split: S60 {2024: 0.47, 2025: 0.53} (STRICT 41% -> 50%, TOLERANT 42% -> 47%, NOW-ONLY 38% -> 43%: the whole universe was kinder in 2025).

**The $ line** (monthly rebalanced, hold month M, program-equal average of the selected series, live lots, research/2.35; 87 weeks 2024-04..2025-12):

| selection | mean $/wk | SD | cumulative $ | worst-20 weeks $ | share positive weeks |
|---|---|---|---|---|---|
| score >= 0.60 | -489 | 3,705 | -42,521 | -108,221 | 49% |
| score >= 0.70 | -848 | 5,557 | -73,743 | -91,211 | 31% |
| NOW-ONLY (positive last 3 and 6 months) | -870 | 2,628 | -75,661 | -89,602 | 37% |
| STRICT | -288 | 2,372 | -25,044 | -65,513 | 44% |
| TOLERANT (literal) | -400 | 2,819 | -34,763 | -79,480 | 44% |
| score >= 0.60 and STRICT | 275 | 4,674 | 23,952 | -100,847 | 53% |
| score >= 0.60 and TOLERANT | 161 | 4,111 | 13,984 | -94,720 | 49% |

The score >= 0.60 line loses money (-0.5k/wk per program-average), the same direction as the RE-2 portfolio walk-forward (DS3_RECENT_PORTFOLIO.md: -5.5k/wk at shrunk size over the whole ledger; screening on persistence >= 0.7 +0.2k on 11 active months). Only the scored >= 0.60 AND STRICT intersection is positive (+0.3k/wk on 28 series-months per month, MDE far larger).

**Study-wide check on RE-1's own walk-forward scores (247,552 rule-months, all programs incl. profit-protect exits):** score >= 0.60 positive 65% [47-83] vs 43% for all (placebo 39%); >= 0.70 93%. By family at >= 0.60: exit 93% (3,131 rule-months), sizing 54% (1,326), entry filter 51% (711), regime 19% (1,107), entry structure 11% (101), confirmation 4% (77). Without exits: 39% at 0.60 and 51% at 0.70 (227). The answer to 'does the score beat 41% out of sample': yes at the study level, because the score loads on a family (profit exits) that persisted in 2025 for a structural reason (DS3_PERSISTENCE_SUNDAY.md); on the families that make up this list it equals the family base rate (50%).

## 3. DIVERSIFICATION
**3a. Pairwise weekly correlation** (149 weeks since 2023-04, rule deltas in $ of stack P&L, 493 streamed distinct rules). Mean pairwise rho 0.047, median 0.035, share of pairs above 0.5: 1.4%, above 0.3: 2.9%. Within the same program the mean is 0.136, across programs 0.029. **Placebo:** 100 random draws of the same number of series from the same programs (whole stream universe, no gate) give mean rho 0.026 (sd 0.003); the list is more correlated than random, i.e. selecting on 'positive now' does not buy independence. Correlation of each rule's weekly delta with the live stack's weekly P&L (as-is, unlocked, live lots): mean -0.044, median |rho| 0.086, max |rho| 0.409; with the Sunday composite: mean +0.002, max |rho| 0.344. These are deltas (a filter's saved/added P&L), so they are near zero against the P&L level by construction: the rules do not ride the stack's own weekly swings, but a delta that is uncorrelated with the stack is not the same as a bet that is independent of the stack's signals (every rule here filters, sizes or re-enters the stack's own trades).

Mean pairwise rho by program pair:

| | ADDUW B1 | ADDUW B2 | CUTWAIT | EINT1 | EINT2 | EXP1 loss per-stream fixed | EXP1 profit fixed | L2SE entry (THP_POLICY entry) | L2SP profit (THP_POLICY profit) | META FS1 | META FS2 | SPLIT 70/30 | THL (THLB classic loss rules) | THPC2 (profit) | UF-ENTRY c1 | UF-ENTRY c2 | UF-ENTRY c3 | UF-ENTRY c4 | UF-LOSS c1 | UF-LOSS c3 | UF-LOSS c4 | UF-LOSS c6 | UF-PROFIT c4 | ZONES-2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| ADDUW B1 (n=1) | 0.000 | 0.075 | 0.094 | -0.021 | 0.015 | 0.001 | 0.067 | 0.212 | 0.166 | -0.008 | -0.013 | 0.026 | -0.025 | 0.142 | -0.093 | -0.101 | -0.107 | -0.052 | -0.000 | -0.033 | -0.011 | 0.032 | -0.128 | 0.076 |
| ADDUW B2 (n=31) | 0.075 | 0.372 | 0.043 | 0.017 | 0.023 | -0.000 | 0.016 | 0.021 | 0.061 | 0.012 | 0.011 | 0.021 | -0.011 | 0.020 | -0.018 | -0.035 | -0.051 | -0.013 | -0.003 | 0.101 | 0.115 | 0.041 | -0.066 | 0.008 |
| CUTWAIT (n=2) | 0.094 | 0.043 | 0.444 | 0.020 | 0.029 | 0.049 | 0.073 | 0.088 | 0.086 | 0.049 | 0.026 | 0.080 | 0.057 | 0.037 | -0.011 | 0.005 | 0.108 | -0.033 | 0.033 | 0.106 | -0.037 | 0.145 | -0.055 | -0.010 |
| EINT1 (n=109) | -0.021 | 0.017 | 0.020 | 0.102 | 0.065 | 0.022 | 0.052 | 0.070 | 0.025 | 0.028 | 0.025 | 0.060 | 0.030 | 0.023 | 0.055 | 0.062 | 0.081 | 0.042 | 0.029 | 0.030 | 0.047 | -0.045 | -0.020 | 0.031 |
| EINT2 (n=87) | 0.015 | 0.023 | 0.029 | 0.065 | 0.069 | 0.013 | 0.030 | 0.094 | 0.022 | 0.026 | 0.008 | 0.048 | 0.019 | 0.026 | 0.046 | 0.037 | 0.047 | 0.033 | 0.020 | 0.008 | 0.028 | -0.006 | 0.013 | 0.033 |
| EXP1 loss per-stream fixed (n=6) | 0.001 | -0.000 | 0.049 | 0.022 | 0.013 | 0.198 | 0.030 | 0.050 | 0.061 | 0.031 | 0.037 | 0.001 | 0.236 | 0.041 | -0.017 | -0.009 | -0.023 | -0.028 | 0.039 | 0.060 | 0.014 | 0.099 | 0.015 | 0.017 |
| EXP1 profit fixed (n=1) | 0.067 | 0.016 | 0.073 | 0.052 | 0.030 | 0.030 | 0.000 | 0.104 | 0.315 | 0.046 | 0.050 | 0.224 | 0.059 | 0.233 | 0.218 | 0.133 | 0.152 | 0.166 | 0.060 | -0.010 | -0.022 | -0.204 | 0.050 | 0.050 |
| L2SE entry (THP_POLICY entry) (n=1) | 0.212 | 0.021 | 0.088 | 0.070 | 0.094 | 0.050 | 0.104 | -0.000 | 0.146 | 0.048 | 0.036 | 0.235 | 0.066 | 0.073 | 0.077 | 0.013 | 0.082 | 0.034 | 0.076 | -0.027 | 0.042 | -0.042 | -0.175 | 0.066 |
| L2SP profit (THP_POLICY profit) (n=6) | 0.166 | 0.061 | 0.086 | 0.025 | 0.022 | 0.061 | 0.315 | 0.146 | 0.471 | -0.007 | 0.002 | 0.186 | 0.075 | 0.342 | 0.005 | -0.041 | -0.054 | 0.005 | 0.035 | 0.099 | 0.085 | 0.019 | -0.058 | 0.072 |
| META FS1 (n=18) | -0.008 | 0.012 | 0.049 | 0.028 | 0.026 | 0.031 | 0.046 | 0.048 | -0.007 | 0.062 | 0.069 | 0.024 | 0.029 | 0.021 | 0.079 | 0.067 | 0.065 | 0.051 | 0.029 | 0.046 | 0.013 | 0.013 | 0.032 | 0.015 |
| META FS2 (n=26) | -0.013 | 0.011 | 0.026 | 0.025 | 0.008 | 0.037 | 0.050 | 0.036 | 0.002 | 0.069 | 0.101 | 0.011 | 0.039 | 0.025 | 0.028 | 0.017 | 0.063 | 0.010 | 0.043 | 0.018 | 0.012 | 0.000 | -0.003 | -0.001 |
| SPLIT 70/30 (n=4) | 0.026 | 0.021 | 0.080 | 0.060 | 0.048 | 0.001 | 0.224 | 0.235 | 0.186 | 0.024 | 0.011 | 0.316 | 0.006 | 0.095 | 0.238 | 0.133 | 0.119 | 0.168 | 0.041 | 0.027 | -0.062 | -0.121 | -0.068 | -0.002 |
| THL (THLB classic loss rules) (n=10) | -0.025 | -0.011 | 0.057 | 0.030 | 0.019 | 0.236 | 0.059 | 0.066 | 0.075 | 0.029 | 0.039 | 0.006 | 0.245 | 0.055 | -0.049 | -0.033 | -0.093 | -0.033 | 0.062 | 0.091 | 0.089 | 0.062 | -0.049 | 0.038 |
| THPC2 (profit) (n=12) | 0.142 | 0.020 | 0.037 | 0.023 | 0.026 | 0.041 | 0.233 | 0.073 | 0.342 | 0.021 | 0.025 | 0.095 | 0.055 | 0.397 | -0.039 | -0.058 | -0.083 | -0.043 | 0.067 | 0.073 | 0.034 | -0.123 | -0.013 | 0.064 |
| UF-ENTRY c1 (n=9) | -0.093 | -0.018 | -0.011 | 0.055 | 0.046 | -0.017 | 0.218 | 0.077 | 0.005 | 0.079 | 0.028 | 0.238 | -0.049 | -0.039 | 0.572 | 0.436 | 0.407 | 0.438 | -0.058 | -0.055 | -0.095 | -0.060 | 0.104 | -0.036 |
| UF-ENTRY c2 (n=11) | -0.101 | -0.035 | 0.005 | 0.062 | 0.037 | -0.009 | 0.133 | 0.013 | -0.041 | 0.067 | 0.017 | 0.133 | -0.033 | -0.058 | 0.436 | 0.335 | 0.295 | 0.309 | -0.045 | 0.002 | -0.026 | -0.057 | 0.076 | -0.025 |
| UF-ENTRY c3 (n=2) | -0.107 | -0.051 | 0.108 | 0.081 | 0.047 | -0.023 | 0.152 | 0.082 | -0.054 | 0.065 | 0.063 | 0.119 | -0.093 | -0.083 | 0.407 | 0.295 | 0.820 | 0.281 | -0.063 | -0.058 | -0.096 | -0.082 | 0.036 | -0.057 |
| UF-ENTRY c4 (n=6) | -0.052 | -0.013 | -0.033 | 0.042 | 0.033 | -0.028 | 0.166 | 0.034 | 0.005 | 0.051 | 0.010 | 0.168 | -0.033 | -0.043 | 0.438 | 0.309 | 0.281 | 0.275 | -0.058 | -0.051 | -0.055 | -0.072 | 0.100 | -0.020 |
| UF-LOSS c1 (n=5) | -0.000 | -0.003 | 0.033 | 0.029 | 0.020 | 0.039 | 0.060 | 0.076 | 0.035 | 0.029 | 0.043 | 0.041 | 0.062 | 0.067 | -0.058 | -0.045 | -0.063 | -0.058 | 0.269 | 0.042 | 0.032 | -0.036 | -0.044 | 0.011 |
| UF-LOSS c3 (n=6) | -0.033 | 0.101 | 0.106 | 0.030 | 0.008 | 0.060 | -0.010 | -0.027 | 0.099 | 0.046 | 0.018 | 0.027 | 0.091 | 0.073 | -0.055 | 0.002 | -0.058 | -0.051 | 0.042 | 0.523 | 0.135 | -0.036 | -0.088 | 0.042 |
| UF-LOSS c4 (n=1) | -0.011 | 0.115 | -0.037 | 0.047 | 0.028 | 0.014 | -0.022 | 0.042 | 0.085 | 0.013 | 0.012 | -0.062 | 0.089 | 0.034 | -0.095 | -0.026 | -0.096 | -0.055 | 0.032 | 0.135 | 0.000 | 0.065 | -0.053 | 0.021 |
| UF-LOSS c6 (n=1) | 0.032 | 0.041 | 0.145 | -0.045 | -0.006 | 0.099 | -0.204 | -0.042 | 0.019 | 0.013 | 0.000 | -0.121 | 0.062 | -0.123 | -0.060 | -0.057 | -0.082 | -0.072 | -0.036 | -0.036 | 0.065 | 0.000 | -0.028 | 0.014 |
| UF-PROFIT c4 (n=1) | -0.128 | -0.066 | -0.055 | -0.020 | 0.013 | 0.015 | 0.050 | -0.175 | -0.058 | 0.032 | -0.003 | -0.068 | -0.049 | -0.013 | 0.104 | 0.076 | 0.036 | 0.100 | -0.044 | -0.088 | -0.053 | -0.028 | -0.000 | 0.017 |
| ZONES-2 (n=137) | 0.076 | 0.008 | -0.010 | 0.031 | 0.033 | 0.017 | 0.050 | 0.066 | 0.072 | 0.015 | -0.001 | -0.002 | 0.038 | 0.064 | -0.036 | -0.025 | -0.057 | -0.020 | 0.011 | 0.042 | 0.021 | 0.014 | 0.017 | 0.168 |

**3b. Clusters** (average linkage, rho >= 0.5): 206 clusters among 493 rules, effective N 47. Largest 8 (same bet in different clothes, i.e. threshold/feature variants of one filter on one book):

| cluster | rules | programs | books |
|---|---|---|---|
| 72 | 23 | ZONES-2 | ALL |
| 112 | 19 | UF-ENTRY c1, UF-ENTRY c2, UF-ENTRY c4 | all 6 engine books (ST HM WT KB SM PE, pooled lock engine) |
| 53 | 17 | ADDUW B2 | WT |
| 76 | 16 | ZONES-2 | ALL |
| 81 | 15 | ZONES-2 | ALL |
| 70 | 13 | ZONES-2 | ALL |
| 64 | 12 | ZONES-2 | ALL |
| 56 | 12 | ZONES-2 | ALL |

116 clusters have a single rule. STRICT list: 72 clusters / eff. N 25 among 169; TOLERANT: 72 / 26 among 163. The independent-exposure count is therefore between 47 (eigenvalue) and 206 (clusters), for the 493 streamed non-EQR rules; the 384 ledger-only rules (380 CF-COMBO among them, which are 42% of the list and heavily overlapping: array pairs on the same books) are not in it.

**3c. The portfolio on the lock engine** (hence the limits: ADDITIVE sum of each rule's own lock-engine delta, no joint re-run). Sizes: m_i = min(1, size_rec_i x sigma_med / sigma_i): equal-risk against the median weekly SD of the list, times the ledger's shrunk Kelly-capped size (size_rec is 0 for rules whose family shrinkage is <= 0, so they drop out: that is why only 252 of 493 are active). Stack = ONE_CONVENTION as-is, unlocked, live lots; Sunday composite = the six-piece composite on the same convention. $k/wk, live lots; maxDD on cumulative weekly P&L in the window; worst-20 = sum of the 20 lowest weeks in the window (L3M has 13 weeks and L6M 28, so there the worst-20 is nearly total P&L; PRE (75 weeks) and X' (44) are the informative tail windows). L3M, L6M and HOLD are in-sample by construction.

**STRICT column, shrunk size** (169 rules, 116 active; SD of the sum of the active rules' deltas 46,864 vs sum of their SDs 150,075: ratio 0.31; the same ratio for a random draw from the same programs: 0.28 at equal weights):

| window | stack mean | +port mean | port alone | stack SD | +port SD | stack maxDD | +port maxDD | stack worst-20 | +port worst-20 | worst-20 change | Sunday mean | Sunday+port mean | Sunday worst-20 | Sunday+port worst-20 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | +11.8 | +103.4 | +91.6 | +47.3 | +61.4 | +88.0 | +0.0 | +152.8 | +1343.6 | n/m | +37.6 | +129.2 | +489.4 | +1680.1 |
| L6M | +26.7 | +81.8 | +55.1 | +50.1 | +58.3 | +88.0 | +0.0 | +96.6 | +1025.3 | n/m | +45.2 | +100.2 | +408.6 | +1335.4 |
| HOLD | +21.7 | +74.9 | +53.2 | +53.6 | +58.6 | +144.2 | +2.9 | -187.1 | +726.6 | +488.4% | +38.3 | +91.5 | +136.5 | +900.6 |
| PRE | +19.7 | +39.9 | +20.2 | +51.2 | +58.5 | +162.0 | +107.1 | -822.9 | -435.4 | +47.1% | +23.9 | +44.1 | -884.8 | -507.9 |
| X' | -3.9 | +13.1 | +17.0 | +29.3 | +42.6 | +316.5 | +152.3 | -595.1 | -427.0 | +28.2% | +7.4 | +24.4 | -446.0 | -367.3 |

**TOLERANT column, shrunk size** (163 rules, 99 active; SD of the sum of the active rules' deltas 20,712 vs sum of their SDs 68,255: ratio 0.30; the same ratio for a random draw from the same programs: 0.28 at equal weights):

| window | stack mean | +port mean | port alone | stack SD | +port SD | stack maxDD | +port maxDD | stack worst-20 | +port worst-20 | worst-20 change | Sunday mean | Sunday+port mean | Sunday worst-20 | Sunday+port worst-20 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | +11.8 | +51.7 | +39.9 | +47.3 | +43.9 | +88.0 | +34.1 | +152.8 | +672.0 | n/m | +37.6 | +77.6 | +489.4 | +1008.5 |
| L6M | +26.7 | +47.9 | +21.2 | +50.1 | +47.1 | +88.0 | +34.1 | +96.6 | +499.8 | n/m | +45.2 | +66.4 | +408.6 | +822.5 |
| HOLD | +21.7 | +40.4 | +18.7 | +53.6 | +52.3 | +144.2 | +128.2 | -187.1 | +185.4 | +199.1% | +38.3 | +57.1 | +136.5 | +428.3 |
| PRE | +19.7 | +27.8 | +8.1 | +51.2 | +47.6 | +162.0 | +78.8 | -822.9 | -596.2 | +27.6% | +23.9 | +31.9 | -884.8 | -677.4 |
| X' | -3.9 | +2.0 | +5.9 | +29.3 | +34.0 | +316.5 | +241.5 | -595.1 | -537.7 | +9.6% | +7.4 | +13.2 | -446.0 | -398.1 |

**NOW-ONLY column, shrunk size** (493 rules, 252 active; SD of the sum of the active rules' deltas 92,965 vs sum of their SDs 340,122: ratio 0.27; the same ratio for a random draw from the same programs: 0.28 at equal weights):

| window | stack mean | +port mean | port alone | stack SD | +port SD | stack maxDD | +port maxDD | stack worst-20 | +port worst-20 | worst-20 change | Sunday mean | Sunday+port mean | Sunday worst-20 | Sunday+port worst-20 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | +11.8 | +219.0 | +207.3 | +47.3 | +94.6 | +88.0 | +0.0 | +152.8 | +2847.4 | n/m | +37.6 | +244.9 | +489.4 | +3183.9 |
| L6M | +26.7 | +134.6 | +107.9 | +50.1 | +116.9 | +88.0 | +35.5 | +96.6 | +1519.7 | n/m | +45.2 | +153.1 | +408.6 | +1771.6 |
| HOLD | +21.7 | +126.0 | +104.3 | +53.6 | +112.7 | +144.2 | +35.5 | -187.1 | +1073.1 | +673.6% | +38.3 | +142.6 | +136.5 | +1248.9 |
| PRE | +19.7 | +31.5 | +11.8 | +51.2 | +68.8 | +162.0 | +383.4 | -822.9 | -887.5 | -7.8% | +23.9 | +35.6 | -884.8 | -877.2 |
| X' | -3.9 | +16.5 | +20.5 | +29.3 | +62.9 | +316.5 | +262.4 | -595.1 | -679.0 | -14.1% | +7.4 | +27.8 | -446.0 | -664.2 |

**Full-size equal-risk sensitivity** (m_i = min(1, sigma_med/sigma_i), no shrinkage; every rule on; this is the portfolio the user's argument would build if persistence were real): 

| column | window | portfolio alone mean | stack worst-20 | stack+port worst-20 | change | stack maxDD | +port maxDD |
|---|---|---|---|---|---|---|---|
| STRICT | L6M | +290.5 | +96.6 | +4042.5 | +nan% | +88.0 | +25.2 |
| STRICT | PRE | +101.6 | -822.9 | -2596.0 | -215.5% | +162.0 | +1000.8 |
| STRICT | X' | +92.6 | -595.1 | -780.4 | -31.1% | +316.5 | +242.9 |
| TOLERANT | L6M | +126.5 | +96.6 | +1732.5 | +nan% | +88.0 | +72.8 |
| TOLERANT | PRE | +44.3 | -822.9 | -1497.5 | -82.0% | +162.0 | +385.2 |
| TOLERANT | X' | +26.8 | -595.1 | -959.2 | -61.2% | +316.5 | +621.0 |
| NOW-ONLY | L6M | +642.2 | +96.6 | +6685.5 | +nan% | +88.0 | +474.0 |
| NOW-ONLY | PRE | +24.9 | -822.9 | -8155.8 | -891.1% | +162.0 | +3653.5 |
| NOW-ONLY | X' | +96.9 | -595.1 | -3445.0 | -478.9% | +316.5 | +1410.2 |

At full size the PRE contribution is negative for NOW-ONLY (+24.9k/wk alone) and the PRE worst-20 changes by -891% (negative = deeper); STRICT and TOLERANT are positive in PRE (+101.6k and +44.3k) because the gates require it, and still change the PRE worst-20 by (-215% / -82%) at that size.

**3d. The diversification benefit, stated.** SD of the sum of the active rules' deltas versus the sum of their SDs: STRICT 46,864 vs 150,075 (ratio 0.31); TOLERANT 20,712 vs 68,255 (ratio 0.30); NOW-ONLY 92,965 vs 340,122 (ratio 0.27). Real, but it is what low pairwise correlation (mean 0.05) gives any set of 493 such series; random draws from the same programs give a ratio of 0.28 at equal weights against 0.29 for the list, so the list is not more diversified than a random pick. The benefit shows as a smaller portfolio SD, not as a lower tail relative to the stack: at shrunk size the PRE worst-20 of stack+portfolio against the stack alone moves -7.8% (NOW-ONLY), +47.1% (STRICT), +27.6% (TOLERANT); on the Sunday composite +0.9% / +42.6% / +23.4%. Added to the Sunday composite the shrunk portfolios lift L6M by +107.9k / +55.1k / +21.2k per week (in-sample) and PRE by +11.8k / +20.2k / +8.1k.

**3e. With and without alt-bar / alt-method rules.**

| column | all | without ZONES-2 (alt-method) | ZONES-2 only | alt-bar |
|---|---|---|---|---|
| STRICT (shrunk, alone, L6M / PRE $k/wk live) | +55.1 / +20.2 | +55.0 / +20.2 | +0.1 / +0.0 | none on the list |
| TOLERANT (shrunk, alone, L6M / PRE $k/wk live) | +21.2 / +8.1 | +21.1 / +8.1 | +0.1 / +0.0 | none on the list |
| NOW-ONLY (shrunk, alone, L6M / PRE $k/wk live) | +107.9 / +11.8 | +107.7 / +11.7 | +0.2 / +0.0 | none on the list |

**Alt-bar:** none of the 14,741 ledger rows at >= 0.60 is an alt-bar rule (BARS-ENG best 0.57; 15 bracket-assign alt-bar rows reach 0.61-0.79 but have no L6M value and are L3M-only, so they are not in the ledger or in any column). The question 'are the alt-bar rules the live signals shifted a few seconds' is therefore moot for this list; what exists on the alt-bar side is DS3_ALT_BAR_IDENTITY.md: the five alt-bar cells (5-min SuperTrend, HA 3-min EMA, range-8 Keltner, volume-500 EMA, 4-min EMA) are built from the raw tape on their own bars (98-99.9% signal-second identity with the library, i.e. the bar build is verified), their HOLD paired difference against the 1-min engine has a CI that includes 0 in all five, and none is promoted. I did not measure their weekly correlation with the live books here (no stored stream in the ledger) and will not infer it. **Alt-method (ZONES-2 entries):** 137 rules contribute +0.2k of the +107.9k/wk (L6M) at shrunk size (their family shrinkage is ~0, so their size is ~0); at full size +3.0k of +642.2k, and -0.0k in PRE. Their cross-program correlation with the rest is 0.023 against 0.168 among themselves: different clothes, but one stream is not evidence of a better risk picture.

**3f. LIST70 portfolio.** 31 rules in NOW-ONLY: 31 streamed, 22 clusters; 15 rules in STRICT: 15 streamed, 9 clusters; 10 rules in TOLERANT: 10 streamed, 5 clusters. NOW-ONLY70 shrunk portfolio alone: L6M +26.5k, PRE +2.1k, PRE worst-20 +14.2% (n active 26); with 8-24 series the SDs are not distinguishable from one cluster.

## 4. WHAT TO RUN AND HOW (pointer; SIXTY-2 owns the slot settings and STOP rules)
Section 1 column `d6d7` says per rule what exists today. Summary over the 903 rules: {'NO / not assessed': 415, 'NO': 399, 'PARTLY': 66, 'D7 group-12 rule (a) skip': 13, 'RUNS TODAY': 6, 'RUNS': 4}. In plain words: of the streamed (stack-level) rules none maps onto a D7 alt-bar slot (there is no alt-bar rule on the list), the first-N-minute skip variants in EINT2 map to D7 group-12 rule (a) (which ships OFF: DS3_D7_FILTERS.md, 0 of 19 lines ON), the profit/loss exit variants map to THP_POLICY / D6 groups that already exist, the ER-sizer-like EINT1 sizers have the shadow ER(20) sizer, and ZONES-2, ADDUW, META and the EINT1 feature filters have no module. Per the three columns, the Shadow/Live split is: **Live: none** (0 PASS; the persistence score is at the family base rate; the walk-forward dollars are negative). **Shadow: the STRICT streamed rules with a positive shrunk size and the TOLERANT ones that D6/D7 can already host** (list in the CSV: `d6d7` starting RUNS/PARTLY and tier CANDIDATE). Monitor STOP rule per rule is SIXTY-2's and RE-2's (drop to shadow at STOPPED); the walk-forward above says a status NEW/RISING/STABLE is not a licence to size up.

## 5. WHAT THE RESULT SAYS ABOUT THE USER'S REASONING (scored, not argued)
1. *"Persistence >= 60% means it is working now".* The score is a logistic on family and a 6-month t; its study AUC is 0.507. Within the families that make up this list the walk-forward hit rate of the >= 0.60 selection is 51% (45-57), above the 41% pool by 10 points but equal to the 50% family base rate, program-equal 47%, and it kept -2% of the dollars. Result: supported in direction (+10 points over 'positive last 3 and 6 months'), not supported in size (no dollars) and not above a coin once the family mix is accounted for.
2. *"Rules on different candle sizes / methods are less correlated".* Mean pairwise rho 0.05 (random same-program draw 0.03); cross-program 0.03 vs same-program 0.14. Low, but not lower than random draws; no alt-bar rule exists on the list to test the candle-size part, and the alt-method part (ZONES-2) contributes about nothing at shrunk size. Result: not demonstrated.
3. *"A portfolio of them has a better risk picture".* SD of the sum is 0.27 of the sum of SDs (as for random draws); the PRE worst-20 of the stack does not fall (-7.8% NOW-ONLY, +47.1% STRICT, +27.6% TOLERANT; negative = deeper tail). Result: SD benefit real and ordinary; tail benefit not found.
4. *Addendum, TOLERANT keeps most of STRICT's reliability with far more rules.* Reliability: 78% of STRICT's lift (44.5% vs 45.6%, difference -1.0 pts, CI -4.5..+2.0: not distinguishable) - held. Number of rules: 1.37x STRICT in the walk-forward universe, but 167 vs 543 on the list (0.79x; 370 more unevaluated) - not held on the literal gate, because of clause 5. The thresholds were stated by the user before scoring and were not tuned; the TOLERANT-b reading is the only post-hoc variant shown.

## 6. LABELS, LIMITS, AND WHAT IS NOT DONE
* Post-hoc: dedup representative rule, tier rubric (PASS/CANDIDATE/DEAD with gates in `failed_gates`), cluster cut rho >= 0.5, equal-risk/shrunk size construction, regime-carrier test, TOLERANT-b, all walk-forward rolling analogs of the older windows. User-stated in advance: the 0.60 / 0.70 cuts, STRICT, TOLERANT and NOW-ONLY definitions.
* ONE recent look per prereg group: the columns and the portfolios were each computed once on the final list; the list representative was chosen on PRE and X' only.
* Not done: (a) CF-COMBO weekly streams (re-scored per contract on the window summaries only); (b) streams for the 384 ledger-only rules (380 CF-COMBO: only window summaries are stored; 3 ZONES-2 ADDENDUM; 1 UF-LOSS c3): no monthly series, no correlation, no TOLERANT worst-20, no portfolio line; (c) a joint lock-engine re-run of the portfolio; (d) any alt-bar correlation with live signals; (e) Section 4 slot settings (SIXTY-2). MDE: beside each ledger row (MDE L3M in the CSV and for PRE and X' scaled by sqrt(13/weeks) or, for streams, 2.8 x the weekly SE); every portfolio delta is far inside its MDE in PRE and X'.
* The ZONES-2 stream (RE-2 stitched swA/swL: PRE+X' selection window plus HOLD) is a stack-$ stream and could not be tied to the per-contract ledger row; it is used for sections 2-3 with that flag. EINT1, EINT2, ADDUW were tied to the ledger L3M and L6M within 2%.
* The persistence study's 450,016-series frame is not re-run. The only walk-forward "score" used on the stream universe is the RE-1 logistic re-applied to features I could compute at M (z6, older-window sign, streak; fire-rate neutral, correlation neutral): a re-implementation, not RE-1's own prediction. RE-1's own prediction table (no rule ids) is used only for the study-wide check.
* dead_lookup run on the portfolio spec before (NOT FOUND); three portfolio cells appended to DEAD_CELLS.csv after (SIXTY_PORT_NOWONLY / STRICT / TOLERANT, tier DEAD/CANDIDATE per above). DEAD_CELLS.csv was not rebuilt.

## FILES
Code `l2vast/ds3/code/sixty/` (s0_common, s1_streams, s2_list, s3_dedup, s4_universe, s5_walkforward, s6_wf_summary, s7_regime, s8_stacks, s9_portfolio, s10_extra, s11_table, s12_paired, s13-s16 documents; c1_cfc.py = CF-COMBO re-score; x2_*.py, x3_*.py = follow-up stream builders; s1b_merge_extras.py). Outputs `l2vast/ds3/out/sixty/`: sixty_list60.csv, sixty_list70.csv, stream_meta.csv, stream_W.npy, rules_monthly_regime.csv, wf_months.csv, wf_summary.csv, wf_paired.csv, wf_dollar_line.csv, wf_line_weekly.csv, portfolio_results.csv, corr_clusters.csv, div_placebo.csv, study_wf_scores.csv. Rows `l2vast/ds3/out/recent_wins/sixty.csv` (903 LIST60 representatives + 382 LIST70).

