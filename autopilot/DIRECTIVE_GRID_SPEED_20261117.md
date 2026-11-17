RESEARCH ORDER (relay, 11-17 22:24Z): TRIGGER GRID SPEED. At ~1,200 jobs/h the ~350,000-job grid takes more than ten days. Scope is NOT cut (user: every trigger on every bar). Change HOW it is computed and the ORDER, so the whole grid gets a first answer tonight/tomorrow and depth follows where it matters.

1. ENGINEERING FIRST (W-GRIDA + one helper agent, now):
   - one job = one bar row: load the bar series once, compute each indicator ONCE and reuse it across all parameter sets, sides, sessions and brackets (sessions and sides are masks, not separate runs);
   - brackets: simulate exits for all 7 bracket shapes in one pass from a per-entry forward path (max favourable / max adverse / time-to-level tables per entry), not 7 simulations;
   - numba / vectorised exit loop, persistent worker processes, bars in shared memory (server 2 has 1.3 TB: hold the whole bar library in RAM), no per-job pickle of the tape;
   - seconds / 1-minute rows are the heavy ones (133-193 s per job): profile one and post the before/after seconds per job in the next lead note. Target: 10x or better.
2. COARSE-TO-FINE, not cut (successive halving): 
   - PASS 1 (everything, cheap): every trigger module x every bar row x every session and side, with a COARSE parameter grid (2-3 settings per module spanning its range) and 2 brackets (60/60 and one bar-scaled), real + 2 random nulls. This gives the full heat table trigger family x bar family for ALL bars.
   - PASS 2 (depth where pass 1 shows life): for the top 10% of (trigger family x bar family x session) cells by rolling out-of-sample excess AND a random 5% of the rest (so nothing is trusted only because pass 1 liked it, and so the null for the best pick stays honest): the full parameter grid, all 7 brackets, neighbours, rc random-clock + rand3-5 nulls.
   - PASS 3: layers + exact engine for the top cells (order 1949Z).
   State on the page which pass each number comes from. The live-bar time rows and the live-seven baseline stay first in pass 1.
3. CORES: server 2 gets the grid almost entirely (engine cap 12 is fine); keep 8-12 engine slots for LS_K2_M30 months and the bar-swap engine rows. BOX 1 MEMORY fell to 41 GB at 22:15Z: cap the analysis jobs there so MemAvail stays above 40 GB (move feature builders and grid workers to server 2); do not let the box swap.
4. If after the engineering fix pass 1 still needs more than ~12 hours, post the numbers (jobs, seconds per job, hours) and a price quote for one more compute-only server for 24-48 h; the user decides spend, nobody else.
5. Next lead note: seconds per job before/after, pass-1 job count, ETA for the pass-1 partial (live-bar rows) and the pass-1 full heat table.

Research only. No spend.
