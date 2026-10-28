T-ZEN ADDENDUM 7 — trailing stops, pyramiding, scaling in (2026-10-28)

Same rules as T-ZEN. All three are position-management shapes on the top entry cells, scored as entry x management combinations, paired on identical signals against the plain bracket. Every cell reports realised average lots, realised risk at the worst moment (max open risk in pts x lots), and the lot-matched comparison, because adds and scale-ins change exposure, and a result that only comes from more lots is not an edge.

P1. Trailing stops (complete set; S4 of Addendum 6 holds the structure trails)

Fixed-point trail: stop follows the high by 10 / 15 / 20 / 30 pt, activated immediately / after +10 / after +1R. ATR trail: 1 / 1.5 / 2 x 1-min ATR14 and 5-min ATR14. Percent trail 0.05% / 0.1%. Step trail: stop moves to +0 at +15, to +15 at +30, to +30 at +45 (ratchet ladder). Parabolic SAR (1-min, 0.02/0.2 and 0.01/0.1). Line trail: stop at the 1-min EMA20 / the entry line / VWAP, closing-basis and touch-basis. Time-decay trail: the trail tightens with time in trade (20 pt in the first 10 min, 10 pt after). Each with no target (trail only), with a far target (3R), and with a first scale at the nearest structure. Report the give-back distribution (max open profit vs realised) so the trade-off is visible.

P2. Pyramiding (adds in the direction of an open winner)

Triggers for the add: price +X pt in favour (10 / 20 / 30); each new 1-min / 5-min higher low; the next touch of the entry line in the same regime (the model's second pullback); a new FVG in the trade direction; a 1-min BOS. Size of the add: equal to the initial, 50%, 25% (and the anti-pyramid: 150%). Max adds 1 / 2 / 3. Stop management after an add: one stop for the whole position at the latest add's structure / at the average entry −X / each unit keeps its own stop. Exit: the whole position on the final target or trail; or each unit on its own bracket. Report the lot-matched result (a pyramid at average 1.6 lots vs a plain entry at 1.6 lots) and the worst-moment open risk; the honest sentence on whether the add improves pts per lot-risk or only multiplies exposure.

P3. Scaling in ("limping in") at the touch

Layers: 2 / 3 / 4 equal parts. Placement: (a) across the zone — first at the line, next at the line −5 / −10 pt, last at the wick extreme / zone far edge; (b) by confirmation stage — 1/3 resting at the line, 1/3 on the hold candle close, 1/3 on the stop-entry above the hold candle high; (c) by time — one part per minute while price stays within 3 pt of the line (max 4 min); (d) by fib of the pullback — at 0.5 / 0.618 / 0.786 of the impulse leg. Unfilled layers cancelled on the hold candle / on the first target / kept until the stop. One stop for the whole position (below the lowest layer + buffer, or the structure stop); target on the average entry (1R of average) or the structure target. Report fill rate per layer, average entry vs the line, realised lots, and the lot-matched comparison vs the single entry at the same average lots; also the partial-fill case (only the first layer fills and the trade runs) as a separate row, since that is the known failure of scaling in (small size on the winners, full size on the losers): quantify it in dollars.

P4. Combinations (top 3 cells only)

Scale in (P3b) + first scale out at structure + trail (P1 step ladder) + one pyramid add on the next higher low: the "complete management" cell vs the plain bracket, lot-matched and risk-matched.

P5. Interaction with the 15-pt stop

Every P1-P3 shape at the model's 15-pt stop AND at the 60-pt live bracket, because trails and adds behave differently when the initial stop is already tight. The verdict names the stop regime each shape belongs to.

Reporting

DS3_ZEN_MGMT.md: trails (P1) with give-back distributions, pyramids (P2) lot-matched, scale-ins (P3) with the partial-fill cost, the combination (P4), by stop regime (P5); plain line per block: "trailing by X after +Y adds/costs Z pts per trade vs the fixed target", "adds change pts per unit risk by ...", "scaling in fills N% of layers and costs/earns ... on winners vs losers". Folded into DS3_ZEN_FINAL.md.
