# Josh-london-book-spec-for-D8 (information / plumbing, 2026-11-23 ~02:12Z)

Josh's words, verbatim (21:08 ET, 22 Nov):

> "code london into D8?"

Everything below is the relay's reading (relay = Claude, not typed by Josh). Information / plumbing only: no new tests, no gate or rule change. The exit run and the bare all-layers fit on the London stack stay in the queue as already planned; this order only asks for what the port needs.

Context: London's stack FINAL (provisional pool, 01:43-01:51Z, every rule) is one book, L19201dfc.BRF90_30 (trend_20 + trig_xmarket_commod against_CL {"w": 15, "thr": 2.0}). D8_BUILD_SPEC.md has only a GENERIC AUTO BLOCK for it. The D8 file already runs the yen book Lbb254083 (own-15-minute z of 6J, against, edge over all bars), so the trigger machinery exists.

Please, with a small agent (almost no compute), as for order 2200Z:

1. A hand-written AUTO:BOOK block for L19201dfc: the trend_20 BAR rule in full (kernel, threshold and its daily scale, reset rules, known time, part bars, which sessions the series is built for), and the trigger: which CL series (calendar front month? roll day and time), 1-minute closes, return window, sigma window and minimum count, shift, z, threshold 2.0, the sign convention of "against", edge over which bar series (all sessions like Lbb254083?), handling of missing minutes / contract change, sides traded, bracket (stop 90 / target 30?), London window 02:00-08:30 ET and its session-end exit time.
2. An independent re-implementation check against the engine events (count matched / only-engine / only-mine).
3. Parity pages D8_PARITY_L19201dfc_<td>.md for the two most recent London sessions on or before td 20261110 with at least 2 signals each: bars, signals, trades, INPUTS (CL minute closes, r15, sigma, z, edges per bar), and the per-day bar threshold.
4. The same for the other three London passers (Lc78f2492, L12842dde, L74274eca) only as one line each for now (bar + trigger + data needed), so the port knows what is coming if the pool or the add rule changes.
5. Say what data a live feed must supply for the London stack (CL 1-minute, anything else) and until when the CL file on the box runs.
6. Dates: London pool complete, exit verdict on L19201dfc, bare all-layers fit start and end.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
