# NEW_BOOK_BEATS_LIVE_NYPM - does a new book beat the live NY PM book(s) in the exact engine? (W-NYENG, order 0210Z), refreshed 2026-11-20 00:00Z

**vs TODAY's stack (JL3, today's DAY-DONE); provisional until Asia and London are decided; label BETTER = calibration pending, NOT calibrated.** Rule: REPLACE row (the new book switched on, the named live book's NY PM entries switched OFF) beats that live book when, DRAWDOWN FIRST, the stack ulcer change is < 0 AND the mean $/week change is >= 0 on BOTH the last 6 and last 3 months (engine base lots, $4.84 RT proxy); then prior years must show no RED (> 30% worse on ulcer / max DD / mean) where run; persistence > 0.60 and the 30 date-shift controls are still PENDING for every row below (shown as counts). Bare R0/R3 only orders the engine queue. Live books of this session: K7. verdict yes / no / pending (not run or months not landed). Sorted by the best last-6-month stack-ulcer change of any REPLACE row (most negative first). Full table of every cell: /mnt/l2/l2vast/_nye/beats_NYPM.csv.

**Counts (distinct event streams: parked twins are listed with the label [twin of ...] but NOT counted again):** cells with any engine row 2; cells with a finished REPLACE verdict (L6M+L3M landed) 1; cells that beat at least one live book on L6M+L3M (BETTER, calibration pending) 0; twin cells listed 1.

## Cells that beat a live book (yes), drawdown first
| rank | cell | REPLACE K7 | ADD | prior years run | controls |
|---|---|---|---|---|---|

## Both-side / long-only / short-only rows side by side (order 1014Z; both-side sets are VALID engine results for the both-side book; LO / SO = mode-correct sets, engine-tested separately; replace K7 and ADD; vs the live stack, engine base lots; d = change vs JL3, ulcer first)
| cell (id) | row | variant | L6M d ulcer / d worst wk / d max DD / d mean $/wk | L3M d ulcer / d worst / d max DD / d mean | beats K7 (yes/no/pending) |
|---|---|---|---|---|---|

## D8 gate under the exit-run rule (order 0213Z)
Nothing enters D8 without the EXIT RUN (all 68 recipes, 7 families) on its own entries beside the fixed brackets. Candidate hand-over: autopilot/D8_CANDIDATES.txt (append-only; 3 cells with engine rows listed, one line per live book). Exit run progress: screen stage (68 recipes x params on real entries + null draws) NOT started by W-NYENG on these candidates yet (owner: the exit-screen stage; start order = D8_CANDIDATES.txt engine rank); engine families that cannot run a recipe yet and their build dates: autopilot/D8_EXIT_ENGINE_SUPPORT.md (per-entry stops/targets/time exits run now; opposite-signal exit 11-19 14:00Z; trailing / staged / SAR 11-19 18:00Z; order-flow exits 11-20 12:00Z). Engine cost after the exit screen per candidate: top 3 recipes x (ADD + REPLACE) x (6 last-6-month + 37 prior-year months) + 30 date-shift controls x 6 = 438 set-months; for the 0 candidates that beat a live book now = 0 set-months = 0.0 h at 928 set-months/h (0.0 h at 2,894/h). D8 SPEC DATE: not before the exit-screen stage and the unbuilt engine families are done; earliest realistic 2026-11-20 12:00Z for the cells that beat a live book today if the exit screen starts by 11-19 06:00Z (cannot be firmer: the screen duration is not measured, the candidate list is still growing).

## All other cells: see the csv (verdict per live book: no / pending)

