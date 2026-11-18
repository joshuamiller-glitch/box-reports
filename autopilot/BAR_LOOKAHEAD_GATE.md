# BAR_LOOKAHEAD_GATE - W-GATE, refreshed 2026-11-18 14:23Z

Bar rule used by the whole grid: a bar exists only from its CONFIRMING PRINT (known_ts = the ts of that print; the iface t_close); the trigger signal is stamped at known_ts; the entry is the first print >= known_ts + 1 s plus measured slippage. Level lines / other-market values are looked up at the START of the signal bar (decision time T0 <= previous close), never later.
TESTS: (1) kernel TRUNCATION test: rebuild the month from prints cut at 8 random times per month (3 months: 2025-11, 2026-04, 2026-09), bars with known_ts <= cut must be IDENTICAL (14 columns) to the full build, none with known_ts > cut; also known_ts >= t1 >= t0, known_ts is the ts of a print, known_ts non-decreasing. (2) module-level causality on the REAL rows (signals on the first 70% / 40% of bars = signals of the full series restricted; sig_ts_ns == t_close of the bar). (3) independent causal replay vs stored bars on 6 days of 202606 (W-LEVEL: pnf_14, renko_14, dchg_14, kagi_14 match in 20 of 20 complete sessions: bar count, close, known_ts). (4) fill-delay: NY AM / NY PM candidate cells re-run with the entry delayed +4 / +14 / +29 s after the usual +1 s.

| bar type | confirming print (bar is final) | truncation cuts (specs x months) | failures | median known_ts - extreme time | module-level causality (module x row runs, failures) | verdict |
|---|---|---|---|---|---|---|
| pnf | point-and-figure: the print that falls/rises 3 boxes from the column extreme; the COMPLETED column is the bar (not the running column) | 72 cuts (3 specs x 3 months) | 0 | 0.0 s | 11 runs, 0 failures | PASS |
| renko | the print that trades 1 brick (N ticks) beyond the last brick close, or 2N against it for a reversal brick; that print closes the brick | 72 cuts (3 specs x 3 months) | 0 | 0.0 s | 9 runs, 0 failures | PASS |
| mrenko | median Renko: print that reaches +N, or 1.5N against, from the last brick close | 72 cuts (3 specs x 3 months) | 0 | 0.0 s | 6 runs, 0 failures | PASS |
| urenko | UniRenko: print N beyond the last close (reversal brick opens at the last close, closes N beyond) | 72 cuts (3 specs x 3 months) | 0 | 0.0 s | 8 runs, 0 failures | PASS |
| frenko | flex Renko: print N beyond (trend) or 0.5N against (reversal bar) the last close | 72 cuts (3 specs x 3 months) | 0 | 0.0 s | 11 runs, 0 failures | PASS |
| wrenko | Renko with wicks: same confirming print as classic Renko; high/low include raw prints since the previous brick (all earlier than the closing print) | 72 cuts (3 specs x 3 months) | 0 | 0.0 s | 12 runs, 0 failures | PASS |
| lbrk | line break: the print that breaks beyond the extreme of the last N lines, or one box beyond the last line | 72 cuts (3 specs x 3 months) | 0 | 0.0 s | 12 runs, 0 failures | PASS |
| kagi | the print that reverses by theta ticks from the running extreme; the bar is the finished leg (extreme time t1 is earlier than the confirming print) | 72 cuts (3 specs x 3 months) | 0 | 24.6 s | 11 runs, 0 failures | PASS |
| dchg | directional change: print that reverses theta ticks from the extreme; same kernel as Kagi | 72 cuts (3 specs x 3 months) | 0 | 24.6 s | 12 runs, 0 failures | PASS |
| swing_pct | zigzag by basis points: print that retraces pct of price from the extreme | 72 cuts (3 specs x 3 months) | 0 | 333.1 s | 12 runs, 0 failures | PASS |
| swing_atr | zigzag by ATR multiple (trailing-day range): print that retraces k x ATR from the extreme | 72 cuts (3 specs x 3 months) | 0 | 30.3 s | 12 runs, 0 failures | PASS |
| pasl | price-action swing leg: retrace of max(N ticks, 0.5 x previous completed leg) from the extreme | 72 cuts (3 specs x 3 months) | 0 | 49.9 s | 12 runs, 0 failures | PASS |
| trend | trend bar: print N beyond the prior close, or 2N against it | 72 cuts (3 specs x 3 months) | 0 | 0.0 s | 12 runs, 0 failures | PASS |
| mom | momentum bar: print >= N ticks away from the bar open (not a reversal type; included as a control) | 72 cuts (3 specs x 3 months) | 0 | 0.0 s | 12 runs, 0 failures | PASS |

MODULE TEST GAPS: 10 module x row runs errored with mmap length > file size (level-line files on server 2 were still being copied from box 1 then; not a causality finding); those pairs are untested here and rest on the W-GRIDD builder test below. Re-run once the feat_d copy has finished.

READING: no reversal-type bar type shows look-ahead in its construction: the bar the trigger sees is final only at the confirming print, and the stamp and the fill are after it. Kagi / dchg / swing / pasl bars close at the EXTREME of the leg, but the extreme is only known 25-330 s later (median lag in the table); the harness stamps the signal at the confirming print, so these are post-reversal entries, not look-ahead. P&F columns and Renko bricks are final at the print that completes them. Bar types that FAIL would be re-scored with the signal stamped at the confirming print; none failed, so no re-score changed any number.
NOT PROVEN BY THIS GATE: (a) the swing S/R / FVG / order-block LEVEL lines (confirmation rule: a fractal pivot counts only from the end of bar j+2 on the 5/15/60-min grid; W-GRIDD builder no-look-ahead test: 84 lines checked, 0 mismatches; my heuristic lag check on SW5/SW15 lines found 15 of ~430 changed-line values equal to a minute high within the last 10 minutes, consistent with a revisit of the same price, not proof either way); (b) real-world NT8 bar construction differences (custom BarsType, 1 tick price gaps on reverse bricks): construction rules are in BAR_REGISTRY.md.

### Fill-delay test, NY AM + NY PM candidate cells (entry delayed after the confirming print; 1 lot, $4.84, L6M points)
140 of 140 cells scored so far; 140 positive in the last 6 months at the normal +1 s; of these 108 keep > 50% of their L6M points at +15 s and 86 at +30 s.

