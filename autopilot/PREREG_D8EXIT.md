# PREREG_D8EXIT (W-D8EXIT, order 0213Z stage a + coordinator 0220Z), written 2026-11-19 ~02:25Z before any scoring
Scope: exit-recipe screen ONLY on D8 candidate cells (autopilot/D8_CANDIDATES.txt, append-only, re-read every cycle). NOT the broad grid run.
Session priority (0220Z): Asia, NY AM, London, NY PM; inside a session finished/yes engine rows first, then engine rank.
Run: gjob2.run_exits(row, module, tag, idx=[param index of the candidate cell]) for the full 68-recipe gexit.EXIT_GRID. Tags: d8real (real entries), randd8a, randd8b (same count/side mix random entries, gjob2.rand_signals, as EXIT_YIELD). Flags GL_OWNSTOP=1.
Pick rule (recent rule, drawdown first): recipe eligible if L6M pts>0, L3M pts>0, trades L6M>=20, no prior year (2023/24/25) worse than 30% vs L6M weekly rate (amber 15-30% shown). Among eligible: lowest ulcer (RMS drawdown of weekly equity since 2023-10), tie-break higher L6M. Top 3 + fixed references (best fixed bracket by L6M from p1real; cell's own bracket if present).
Null: same pick rule on randd8a/randd8b; cell flagged BEATS-NULL only if best eligible recipe L6M > both nulls' best-of-68 L6M (2 draws = screen only; finalists get more draws later). Best-of-68 selection is covered by comparing against best-of-68 on null entries.
Engine support per family: autopilot/D8_EXIT_ENGINE_SUPPORT.md. Fixed numbers: $20/pt/lot, fees per FEES.md applied by the engine later (screen is points).
Limits: nice 7, box-1 MemAvail>40 GB, A/B workers <=24 each, Dallas rows (crc32%12 in 0,1) on server 2 <=8 workers; no pkill -f; no spend.
