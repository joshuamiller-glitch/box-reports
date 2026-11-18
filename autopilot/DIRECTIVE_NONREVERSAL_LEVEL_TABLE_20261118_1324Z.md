# 1324Z — LEVEL TRIGGERS: add a "best NON-reversal bar" table (Josh asked; research only)

From: Josh's chat assistant (relay). Research orders only.

WHY: the level table on DS3_SIGNAL_BAR_GRID.md shows only the single best bar row per (module, variant). 105 of the 141 rows that are positive in 2023, 2024, 2025 and the last 6 months have Kagi / point-and-figure / Renko-type bars as that best row, which hides how the same trigger does on bars with no reversal construction. Josh wants the prospects that do NOT depend on those bars.

DO (after the machines are full and the watchdog is tested; cheap, it is a re-read of results already on disk):

1. On the same page add, per session, a second level table: best cell per (module, variant) restricted to NON-reversal bar rows = time (tm, time_s, time_m), activity (vol, tick, dol, vsess), information (tib, vib, dib, trb, vrb, drb, dlt, cdr, vnorm, cusum) and plain range bars (rng), plus composites (rngor, volor, dltor). EXCLUDE kagi, pnf, renko, mrenko, urenko, frenko, wrenko, lbrk, swing, dchg, pasl, trend, mom and ha_ of any of them. Same columns as the current table, PLUS the bracket in points (stop / target after the 10..120 clip) and the same signals on plain 60/60 (L6M pts and the three prior years).
2. Beside each row print the Kagi/P&F best row's L6M and prior years for the same (module, variant), so the drop is visible.
3. Do the same for the supply/demand modules by zone definition (A, B, C, D, E, Abrk, Agap ...) and entry type, so Josh can see which definition holds on non-reversal bars.
4. Send every non-reversal row that is positive in all three prior years and the last 6 months, with >= 100 trades in the last 6 months, to the random-entry nulls (>= 20 draws) and list the top 12 by weakest prior year on GRID_TOP_CANDIDATES.md under a new heading "Level triggers on non-reversal bars".
5. The P&F / Kagi / Renko look-ahead check (0602Z) stays FIRST among the level jobs: for each reversal bar type state when the bar is known (the confirming print), prove the trigger never uses a bar before that print, and re-score the six best NY AM level cells with the signal stamped at the confirming print.

Reply in MORNING.md with the ETA for the table.
