# USER ANSWERS + FIXES 2026-11-16 (verbatim summary)
1. BOOK TYPES (from DS7.cs comments): none is mean-reversion.
   K7 = Keltner BREAK 3-min (breakout/trend). M7 = momentum vote 4-of-5 (trend). U7 = Supertrend 10-min (trend).
   P7 = pullback inside a Supertrend 5-min regime (trend pullback). H7 = HMA 20/55 cross with EMA200 filter (trend).
   A7 = Asia pullback. O7 = opening drive with pullback (trend).
   Regroup DEEPEN Part 1 as: breakout/trend (K7 M7 U7 H7) vs pullback (P7 A7 O7). Redo any table that used K7 = mean-reversion.
2. ATR-SKIP IS RUNNING LIVE BUT READS LOWER: live log 11/11 7:11:00 PM printed "P7 JN04 REG atr_rel 1.49 -> lots 12 -> 6"; engine has 1.63.
   Live: 5-min ATR(14) built from 1-min chart bars; base = median of the previous up-to-20 trading dates' daily medians (needs >= 5), from the days loaded on the chart, current date excluded.
   Find why the engine reads higher and make the engine reproduce 1.49 at that second. Then recount the "40 of 101".
3. JV back to 28 busy workers at 02:04Z after the 01:04Z kill. Stop jv_loop too; JV quota 0 until asked. Load1 80-96 on 32 cores is oversubscribed: cap total running engines so load1 stays near 40, and say what the throughput (cell-months/hour) was at load 45 vs load 85.
4. Live-equivalent base: when JN05W2JL lands, re-run on it first the reference + A7 Asia 40x40/40x90, U7 Asia 40x40, LS1_MP/LS125_MP, the L3 arrival item, P7 Asia gated set. Label every older number "old base".
