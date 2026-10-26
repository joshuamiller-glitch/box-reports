# BASIS AUDIT - PART PB (PULLBACK study, PX*/PA* books, SE1/SE2 and K96-type stop-entry books, my SW/SE/SK/WT books, family H first run), 2026-10-17T14:47Z
Rule 1 (AMENDMENT FVG-REALIZABLE): a book that uses resting orders (limit or stop entries, scale-ins, re-entries) must come from an executable order-state machine; 'independent replay then sequential selection (in placement order)' is BASIS-VOID. Classification below: entry form, evidence, the ORIGINAL order-handling rule, status. Evidence = report text and code read on this box.

## 1. PULLBACK study (REPORT_PULLBACK.md; code ap_pb_core.py, ap_pb_stage1/2.py, ap_pb_final.py, ap_pb_pair.py)
| item | entry form | resting orders? | original order-handling rule | status |
|---|---|---|---|---|
| NQ stage-1 3,280 + stage-2 1,495 strategy cells, the 12 finalists, ES/RTY screens, the weak LEAD (NQ 15-min PSAR touch-and-close-back) | trigger on a CLOSED signal bar, market order at the next 1-minute open, OCO stop/target bracket (protective), time/trail exit | NO (report s.'Executability': 'market entry on the next bar and an OCO stop/limit bracket'; code: entry index e = trigger bar + 1 at the open) | n/a (market entries, one position at a time by the trade walker) | **BASIS-OK** (no resting entry); verdict unchanged (1 weak LEAD, 0 FOUND) |
| PX32 PSAR 15-min pullback ensemble | same market-at-next-open form | NO | n/a | BASIS-OK, NO unchanged |
| Pair-side 5.1: the pair's own entries re-timed as RESTING LIMITS at min(entry, level), cancel after N min, 32 cells | resting limit per pair row | YES | each pair row replayed INDEPENDENTLY (fill row found on the minute path), patched rows then run through B.run in fill-time order with the live per-book rules; no cancellation of the sibling resting orders of other rows when one fills | **BASIS-VOID** (independent replay + sequential selection). Verdict was NO (0/32 pass gate 3, mean all-in uplift -0.71, best +0.17): a rule-1 re-score can only remove orders, it cannot create the missing continuation trades, so NO is not expected to change; formal re-score deferred (needs the pair-row signal timestamps in the executable machine) |
| Pair-side 5.2 depth tilt (12 cells) | sizing multiplier on market entries | NO | n/a | BASIS-OK |
| Level-respect tables (3 instruments x 41 levels) | not a P&L book | n/a | n/a | not affected |

## 2. PX*/PA* books (REPORT_PX1, PX20-PX34, PA3-PA10, PA_L2)
- PX1, PX20-27 (shock skip/half, tilts), PX31 (monthly momentum), PX33 (WT-10 with denoisers: WT bracket book, market at the next 1-min open), PA5, PA6, PA7, PA8, PA9, PA10: size multipliers, skips or EXIT rules on the live pair, or market-entry sleeves with protective OCO brackets. No resting entry orders. **BASIS-OK**, verdicts unchanged.
- PA3 (K96b cure, HM stop-entry grid, 1-second account): RESTING stop-market entries re-quoted every bar, one-shot per regime run, replayed through the K96 order-level account (acct_se). That account takes triggers in TRIGGER-TIME order and drops a trigger when the book is busy: this is a per-book first-fill-wins / one-working-order-per-book rule (a re-quoted order replaces the previous one), i.e. close to executable rule 1 (the placement of a new order is also blocked while the book holds a position because its triggers are dropped). Caveat already in the report: 64% of the selected cell's fills are marketable at placement (they would be market orders at the touch, price assumption optimistic). **REVIEW, not void**: LEAD stays LEAD (it already failed selection-corrected null, plateau, 2x slip, H0, alt-month), not a FOUND-PENDING; no verdict change. K96 (NO) and K96b (LEAD, non-virgin) use the same account: same classification (REVIEW; verdicts unchanged).
- PX_L2ES / PA4 (L2 at pair flips): measurement of market-entry flips, no resting book.
- E1 (denoised signals driving ST/HM) and Q40 (passive-fill execution test of gross-positive families): Q40 is the passive-fill (resting limit) test; its verdict NO already says passive fills lose: **BASIS-VOID label applies to its fill model (q50/through1 independent replay)**, NO unchanged.

## 3. My books (this worker)
- SW1-SW36 (36 sleeve families, 3,000+ selected cells): every entry is a MARKET order at the next 1-minute open after a bar-close signal or a clock/event minute (sim: `ap_b_base.sim_events`, entry `ep=o[i]+slip`), brackets/time exits are protective; the only 'limit' wording is the bracket target. **BASIS-OK.** In particular SW4 (RTY fade of the first 15 min, FOUND-PENDING-REPLICATION -> LEAD) and SW20 are market-at-clock entries held to a time exit: not resting orders, not BASIS-VOID. SW19 (prior-day level crossings) and SW3/SW6/SW10/SW14/SW23/SW26-SW30 enter at market after the bar closes beyond the level.
- SE1: delay cells = market orders (BASIS-OK); flow-confirmed = market (OK); the 4 LIMIT cells (limit at the signal-bar close, 15/60 s) are resting orders replayed independently per signal with the K96 account's busy-at-fill filter: BASIS-REVIEW, all NO (-0.13..-1.10) -> no change. SE2 tolerance cells TOL are market-with-skip (OK); CAP cells are resting limits (NO). SE2's decomposition used the same account (analysis only).
- SX1-SX3, SK (K4 stress test), WT-10 config: sizing / daily market orders at 16:16 / bracket books: BASIS-OK.
- WT-10 (WT bracket sleeve, ap_wt_*): market entry at the next 1-min open, OCO 60/60 bracket: BASIS-OK.

## 4. Family H, FIRST RUN (stage 1, 1,632 cells, 14:5x UTC) = BASIS-VOID
`ap_ict_core.sim` takes the setups in PLACEMENT order, finds each order's fill independently, and skips later placements only while a previously ACCEPTED trade is open: an order placed later that would fill first is ignored, and orders placed earlier that never fill do not block. That is exactly 'independent replay then sequential selection in placement order'. All first-run family-H numbers (and every FVG/IMP3/ICT number from the same simulator) carry the BASIS-VOID label; none of them is reported as a result. Family H is re-simulated under an explicit order-state machine with the order-handling rule as a factor (section 5).

## 5. BASIS-VOID list for a778 (this scope)
1. PULLBACK pair-side 5.1 (32 resting-limit re-timing cells): verdict NO, no change expected.
2. Q40 passive-fill fill model: verdict NO, no change expected.
3. Family H first run (1,632 cells): withdrawn, re-run under rule 1 (REPORT_I5H.md).
4. REVIEW (not void): K96, K96b, PA3 (per-book first-fill-wins account; marketable-at-placement caveat): verdicts LEAD/NO unchanged, no FOUND-PENDING among them.
5. My SE1 LIMIT cells / SE2 CAP cells: NO, no change.
BASIS-OK: PULLBACK strategy cells, PX*, PA5-PA10, SW1-SW36 (incl. SW4, SW20), SX1-3, SK, WT-10.

Verdict changes in this scope: none (every affected book was already NO or non-promoted LEAD). Family-H first-run results are withdrawn.
