# REPORT BASIS AUDIT (amendment FVG-REALIZABLE item 3 + EXECUTE-FIRST), compiled by a778, 2026-10-17
**Verdict: IN PROGRESS - library, assembly, FORWARD.md and errata stages DONE; executable re-scores of the affected books are run by the book owners (a41bb, a027, a3a74) through exec_engine and recorded in REPORT_BASIS_RESCORE.md.** No verdict change so far except the ones the owners already report below (FOUND-PENDING-REPLICATION -> NO for RZ1_GC / RZ1_CL / RZ9 / FVG_GCCL, LEAD -> NO for RZ2_BTC); the FVG-family FOUND-PENDING / LEAD rows are VOID (not re-labelled NO until re-scored).

## 1. Rule applied
Resting limit/stop entries must come from a forward-time order-state machine (working orders, placement blocked or OCO-grouped while a position or working order exists, first fill wins, cancels on expiry / stop touch / session end, no post-hoc selection among fills). 'Independent replay then sequential selection' is BASIS-VOID. Market-at-clock / market-at-signal entries with time exits are not resting-order books.
Key code evidence: ap_ict_core.sim takes setups in placement order, finds each limit's fill independently and skips later placements only while a previously ACCEPTED trade is open (`if s < busy: continue`) - a later-placed order that would fill first is ignored and unfilled earlier orders block nothing. ap_b_base.sim_events (B/Q/SW/BM/BJ/L families) enters at `ep=o[i]` (the open of the bar after the signal bar) and skips signals while in a position (`if i<=last: continue`): market entry, state known at signal time.

## 2. Stage 1 - library marking (DONE)
- outputs/library/INDEX.csv has columns basis_void and basis_note (lib_save.FIELDS extended; re-saves keep the flag; authoritative rules outputs/library/BASIS_VOID.csv; applier code/census/night_ins/ap_basis_void.py; note BASIS_VOID_NOTE.md). Nothing deleted.
- Flagged BASIS-VOID: **1,619 of 40,041 books** (revised: the first pass flagged 2,877 using a blanket family:ICT rule; the ICT worker's per-cell audit, outputs/ideas5000/BASIS_VOID_LIST.csv, shows 1,978 of the 3,878 ICT grid cells are limit entries and 1,900 are market entries, so the blanket rule was superseded: audit trail kept as a 'superseded' row in BASIS_VOID.csv and the old file BASIS_VOID.csv.bak_blanket_ict). Now: 1,584 books from the a41bb list (ICT limit cells, FVG-line, RZ) + ICT_FVG 6, FV16_VC 8, FV17 4, FVG_GCCL 3, RZ1 7, RZ2 2, RZ6 4, RZ9 1 by family; the 18 time-symmetry books (FV16_TS, market-on-trigger, 'basis OK') are not flagged.
- Checked and NOT flagged (evidence): FV16_TS (spec: market entry k x 9 min after the impulse), FV16_SEMIV / OPENTYPE / IB, FV14_* (timed market entries with stops), FV15 (pair overlays), PULLBACK / PX32 (spec: 'market entry at next 1-min open'), PX30 gap fade ensemble (fade at bar N+1 open), RZ3 / RZ8 (stop-entry once per day, day-level state: classified NOT affected by a027, exec_engine check pending), RZ4 / RZ10 (pair-row conditioning), SW/BM/BJ/Q/GC-fade/I9/ES-dip/K4/WT-10 (market). Families searched for 'limit', 'q50', 'through1', 'tick replay', 'stop-entry', 'resting', 'retrace', 'fvg', 'imp3', 'pullback' in name+spec+tags+exits: only ICT, ICT_FVG, FV16_*, FV17, FV14/15 (market), PULLBACK (market) contain them. Q40/Q41, K96/K96b/PA3, SE1/SE2, PULLBACK pair-side 5.1 have no library books (report-level only).

## 3. Stage 2 - assembly input (DONE)
ap_assembly.py (and so the assembly daemon, which launches it) drops basis_void books at load_index() (prints 'assembly input: excluded N BASIS-VOID books'); load_series also tolerates a family file being rewritten by another worker. Re-run once (--null 100, tag basisvoid; REPORT_ASSEMBLY_20261017T1448Z.md) against the previous run (T0703Z, 37,549 books, 253 pool books):
| | before (with void books) | after (void excluded, 37,164 books, 243 pool books) |
|---|---|---|
| best stage-1 clean plateau-passing weekly Sharpe | 11.16 | 7.68 |
| chance expectation (timing-destroyed library, 100 reps) mean / p95 | 13.83 / 15.02 | 8.25 / 8.99 |
| real rank vs the chance distribution | 0.00 | 0.07 (inside the chance band: the library no longer beats its own best-of-search null) |
| best portfolio clean / H1 / H2 | 11.87 / 8.09 / 10.20 (ICT_FVG_IMP3 x3 + SW10CO + Q18CO) | 7.60 / 2.48 / 2.48 (C10S1_GC macd + RY5_E1_K4 x6 + SW10CO + SW14CO) |
After narrowing the ICT flags to the 1,619 per-cell list (38,422 books in the input, 243 pool books, run T1526Z) the result is unchanged: 7.68 clean, chance mean 8.23 / p95 8.90, rank 0.07, same best portfolio (the 1,223 un-flagged market-entry ICT books do not enter the pool).
The previous 'portfolio lead' rested on the voided FVG/ICT books; without them the best assembled portfolio is a K4 + market-book mix with H1/H2 Sharpe 2.5, indistinguishable from chance (rank 0.07).

## 4. Stage 3 - FORWARD.md / ap_forward_score.py (DONE)
FVG_P1, FVG_E1, FVG_IMP3, FVG_VC are in a 'VOID rows' section (forward/VOID_LEADS.json), excluded from the table body, the lead count (20 active leads, 4 void) and the FOUND-PENDING count; PRED_FVG.json predictions untouched, flagged with a top-level `_BASIS_VOID` note. New columns `engine` and `order-handling rule` on every forward row (market-entry books: 'harness 1-min bars / market next-open ...'; pair-side and WT-10: NT8-faithful 1-s engine; daily books: daily engine; void rows: independent tick replay q50 / independent resting limits then one at a time (VOID)).

## 5. Stage 4 - errata (DONE)
CANDIDATES.md and LEDGER.md: dated ERRATUM 2026-10-17 (BASIS-VOID) blocks appended (no line edited or deleted).

## 6. Classification (compiled; owner parts BASIS_AUDIT_PART_Q.md = a027, BASIS_AUDIT_PART_PB.md = a3a74, ICT/FVG part = a41bb pending)
| book(s) | entry form | original order-handling rule | affected | verdict change |
|---|---|---|---|---|
| ICT study cells (3,878 grid cells; 4,064 incl. variants) | 1,978 limit entries (ap_ict_core.sim) / 1,900 market entries | independent fills, sequential in placement order (limit cells) | YES for the 1,978 limit cells (BASIS_VOID_LIST.csv); NO for the 1,900 market-entry cells | limit cells VOID; re-score by a41bb |
| FVG P1 / E1 / IMP3 / VC and siblings FV2-FV19; FVG_QA, SI1 sleeve rows | resting limit at the 50% retrace | independent tick replay (q50) then one at a time | YES | FOUND-PENDING / LEAD -> VOID (bands_by_rule.json: executable rules give negative net R/trade for IMP3 and VC) |
| RZ1_GC, RZ1_CL, RZ9 basket, FVG_GCCL GC / CL / RZ9 tick | resting limit at the FVG retrace | ap_rz_fams.LimFam.run selection over the filled set | YES | FOUND-PENDING-REPLICATION -> NO (a027's own state machine: GC tick best +0.03 R, uplift +0.22/+0.13/-0.16; CL +0.025 R; RZ9 -0.5..-1.1 on every span) |
| RZ2_BTC | same | same | YES | LEAD -> NO |
| RZ2_ETH, RZ1_ES / RTY / YM / ZN / 6E, RZ7 | same | same | YES in form | none (already NO) |
| PULLBACK pair-side 5.1 (32 cells) | resting limit re-timing of pair rows | each row replayed independently | YES | none expected (NO); formal re-score deferred |
| Q40 / Q41 passive variants | limit at close - d, resting 5/15 min | thin() blocks the whole hold window per signal = one order at a time | CONDITIONAL (equivalent to OOAT); fill model q50/through1 | NO unchanged; exec_engine re-run pending |
| K96 / K96b / PA3, SW exec variants, SE1 LIMIT / SE2 CAP | stop / limit entries | order-level account by fill time, fill ignored while busy | REVIEW (executable-like); marketable-at-placement caveat for PA3 | none (LEAD stays LEAD, non-promoted); exec_engine pending |
| IDEAS-5000 family H first run (1,632 cells) | limit setups through ap_ict_core.sim | banned basis | YES | withdrawn, re-run under rule 1 |
| PULLBACK strategy cells, PX32 / PX* / PA5-PA10, SW1-SW36 (SW4, SW20), SX, SK, WT-10, GC fade (B7 / L93 / Q14 / R5), BM1 / BM12 / BM13, BJ2, Q34, Q12, Q20, Q1B, Q8D, Q29, I9, ES dip-buy, K4 / E7 and the other B/Q/L/K event books | market at the next 1-min open (sim_events) or at a clock / daily close, protective brackets | state known at signal time, signals skipped while in a position | NO | none |

## 7. Own work affected
My IDEAS-5000 families G and I were first built on ap_ict_core.sim (banned basis); no cell was scored on it. The ap_ict_core.sim / K.run_cell path was removed from ap_i5_core.py (backup ap_i5_core.py.bak_banned_basis) and both families were scored through exec_engine ECON v1 with the order-handling rule as a factor (see REPORT_I5G.md / REPORT_I5I.md and REPORT_BASIS_RESCORE.md s4). exec_engine v1 has a same-row fill-priority defect (oldest-first; v2 price-priority pending): ffw / nro / stk2 results with overlapping orders are optimistic and are marked v1.

## 8. FA1 / FA4 false-discovery counts
Void FOUND-PENDING / LEAD rows leave the counts: FOUND-PENDING from 5 (E1, P1, IMP3, RZ9, GC/CL transplants) to the market-entry set only (K4 family, C11-DIP, per CANDIDATES.md); the FA4 per-cell chance rates (gate 3: 3.5% per selected cell; LEAD-grade through gates 3, 3b, 4a, 4b, 6: 0.97%; full gate chain 0 of 25,664 grid cells) apply unchanged to the cells that remain; the program-level cells-read denominator drops by the voided books only after the re-score decides which of them were real.
DONE (stages 1-4); stage 5 (re-scores) continues in REPORT_BASIS_RESCORE.md.
