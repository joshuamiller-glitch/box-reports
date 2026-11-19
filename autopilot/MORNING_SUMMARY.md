**NEWEST EDITION: 2026-11-19 -> autopilot/MORNING_SUMMARY_20261119.md (read that first; this file below is the 11-18 edition, kept).**

# MORNING SUMMARY (lead, written 2026-11-18 13:15Z; late - the promised 12:30Z rewrite was missed, see "What went wrong")
Research only. No spend, nothing rented, nothing on the execution server or live chart. Data end 2026-11-12 (NQ raw engine through 2026-11-13).

## What went wrong overnight (own it first)
1. SERVER 2 WAS ~43% BUSY FOR ~8 HOURS (you pay $5.44/h; ~$234 so far). Cause: both grid loops (pass-1 and pass-2, 52 workers) stopped dispatching around 05:00-12:46Z - workers blocked on pipe read, 84k + 22k jobs todo, status file stale. Only the 28 engine workers ran. Fixed 13:05Z (loops killed by pid and relaunched, 56 grid workers, load 54 and rising). A watchdog (s2_grid_watch.py, every 5 min) now restarts the grid loops itself when workers idle two readings in a row.
2. I (lead) was not running between 05:35Z and 13:03Z: no heartbeat, orders 0602Z / 0616Z / 0633Z not acted on until 13:03Z. Heartbeat restarted.
3. GRID_TOP_CANDIDATES.md stayed at the 05:34Z version (gtop step inside the cycle did not rewrite it). Rebuilt by hand 13:12Z (188 candidates); a 30-min cron now rebuilds and pulls it.
4. Near-target engine rows stalled at 214 set-months (K7 last-6-month cells landed 0; table due 06:00Z NOT delivered; controls due 12:00Z NOT delivered). Agent W-ENG started 13:10Z to find why and fix it (also ORB identity pending 7+ h; box-1 /mnt/l2 is 100% full, 28 GB free - the UW recorder has stopped for that reason).

## LEAD / CONFIRMED
- CONFIRMED: none new.
- LEAD (marginal): NY AM opening-range fade (N1_ORB_LIM) - engine identity still PENDING, so the label is NOT FINISHED; do not treat as delivered.
- Screen-level sign of life only (NOT a lead, no engine, naked, few null draws): NY AM best-pick of the trigger x bar grid, +40-42 pts/week out of sample vs null mean -27..-47; 2023 RED. Needs more nulls, layers, engine.
- WEAK-BUT-POSITIVE: 1,045 shelf rows (W-REREAD); LS_K2_M30 same-side loser (screen only, engine 12 months disagree).
- Order 0602Z level cells (positive in 2023, 2024, 2025 and L6M, many on point-and-figure bars): NOT yet tested. First check: point-and-figure look-ahead (agent W-LEVEL started 13:10Z). Treat all pnf rows as suspect until it reports.

## What died
London grid best pick (no edge); NY PM grid best pick (no edge); bar swap: no weak cell has a delivered pick (P7 NY AM gain is not bar-specific); bracket cells under the new rule; DAY-DONE / resume downgraded.

## Still running (13:15Z)
Server 2: grid pass-1 84k jobs todo (stages b+d), pass-2 22k (exit stage a2 5.8k, family cells 16k, top cells 45), engine 28 workers (P7L, ORB, NT, swap rows, LS_K2_M30). Box 1: engine + NT chains (being repaired), grid scorer processes. Exit-family table for the candidate list: not delivered yet (est. after a2 jobs clear; will state a number once the rate is measured at 14:00Z).
Hours of work left: cannot be stated honestly until the restarted loops show one hour of rate; I will append "hours left, one vs two servers" with measured rates at ~14:15Z in MORNING.md.

## Decisions for you (not mine)
- Extra compute server: no quote obtained; $5.44/h x 24-48 h = $131-$261. Nothing rented.
- Data quotes (volatility ETFs $1.50-2.50, CME tails $0, 6J history $33.13, ES MBO history $984.71): NOT approved, nothing bought.
- Box-1 disk is 100% full (/mnt/l2 28 GB free): needs clean-up decision; I will not delete data without your OK.
