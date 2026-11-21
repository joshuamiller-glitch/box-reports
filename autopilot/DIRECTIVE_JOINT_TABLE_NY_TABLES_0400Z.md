# 0400Z Sat: joint table status + NY AM book tables (written by the relay (Claude), not typed by Josh)

No new tests. Josh is asleep; nothing here needs him.

1. **W-LAYERS, joint stage status.** autopilot/ASIA_JOINT_TABLE.md is still stamped 02:05Z at 03:55Z with one row (L578701ed KEPT) and 24 "pending"; the first 10 corrected verdicts were estimated for 03:30-03:45Z. Please post one line and refresh the page:
   - set-months landed of the 8,400 under the corrected 9-row array, per-hour rate, and combos done per book for the first ten books;
   - is the L578701ed row from the corrected JNT9 run or from the voided 80-combo run? If voided, remove it or mark it VOID until the JNT9 row lands;
   - why the table has not refreshed (joint_verdict.py on a timer? waiting for whole books?), and make it refresh on a timer (every 15 min) with a stamp, showing partial progress per book;
   - new ETA for the first ten and the last book. The two stack books first: L7c368a4f and La010c3eb rows go to the head of the joint queue.
2. **W-D8SPEC, documentation only (no engine slots, low priority, box 1 table work):** the NY AM main final is five books. Three have no debug tables yet. Same format and care as D8_TRIGDEBUG_L488784d8.md (exact definitions from the code first, per-bar rows for the NY AM session of trading date 20261110 plus 300 bars before, recompute checked against the module over the whole series, history-needed paragraph, state carried in at the first row):
   - autopilot/D8_TRIGDEBUG_B7bfd33b7.md: dib_6000 bars on the _CANC print rule + trig_levels_profile_va break_native {"n": 2, "k": 0.25}, both sides; plus autopilot/D8_VECTORS_CANC_B7bfd33b7.md (the dib_6000 bars of that session with the day's threshold and every running quantity the bar rule uses, so the NT8 builder can be checked on Josh's tick export). Say exactly how the profile and its value area are built (which bars/prints, bin size, session, when it resets, value-area percent).
   - autopilot/D8_TRIGDEBUG_B6f77f23d.md: tm45 bars + trig_levels_opens false_break_native {"M": 3, "k": 0.5}, bracket asym15u/30u. Say exactly: tm45 stamping and known time (epoch-aligned? waits for the next print?), which opens are levels, what "u" is here and how stop/target follow from asym15u/30u.
   - autopilot/D8_TRIGDEBUG_L6547965c.md: swing_pct_8 bars + trig_tape_unfinished unf_fade {"m": 6, "cp": 0.0}; plus the swing_pct_8 bar vectors of that session with the day's theta. Say exactly what tape data the trigger reads (per-price volumes at the bar extreme? bid/ask split?) and whether NT8 can compute it from last/bid/ask ticks alone.
   If the NY AM final changes later I will ask for the new book.
