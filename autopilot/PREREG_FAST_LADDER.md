# PREREG_FAST_LADDER (W-FASTLADDER, order 0633Z)
No strategy is scored here. The work is an ENGINEERING identity test, decided before any fast-path number is used:
- Identity criterion: a fast-path set-month is accepted only if its trades parquet equals the exact engine's trades parquet for the same set and month: same row count, same entry_ns / exit_ns / book / side / qty / exit reason, prices and pnl equal to 1e-9 (to the cent after rounding), same ncut_state. Any difference = FAIL (published); a failing month falls back to the exact engine automatically.
- Sample: >= 200 set-months spread over Asia and NY AM, ADD / REPLACE vs each live book (K7, P7, U7, M7, H7, A7), quiet and busy months, months where DAY-DONE trips; sample drawn by fixed seed 20261119 from DONE set-months that already exist in runs_rf (reference = existing exact result, no re-scoring of candidates).
- Speed-up = wall seconds of the exact path divided by wall seconds of the fast path, same host, same load, median over the sample; target >= 10x.
- A 2% random re-check of fast results in the exact engine stays on forever; any mismatch stops the fast path for that row type.
