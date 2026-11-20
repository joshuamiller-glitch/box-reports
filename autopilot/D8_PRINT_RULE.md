# D8_PRINT_RULE: the D8 print rule (run merge + last-vs-bid/ask), its exact text, and the proof table (W-D8SPEC, relay order 1526Z)

Written 2026-11-20 ~15:45Z. Data end of bars/tape 2026-11-13 (NT8 file: td 20261110). Naming used everywhere on the engine side: **suffix `_CANR` = the D8 rule (relay's name "CANQ")**; the older `_CANQ` sets are CONTRACT-LEVEL prints (every contract its own print) and `_CAN` are ms-merge + tape flag. Only `_CANR` results may be used for the D8 spec.

## 1. The rule (text for the NT8 bar builder)
**Print stream.** Take the CQG tick records (Last events with the bid and ask in force) in file order.
1. **Side of a record**: if last >= ask: BUY (+1); else if last <= bid: SELL (-1); else UNCLASSIFIED (0). The buy test comes first.
   - *Locked or crossed book (bid >= ask):* both tests can be true; the buy test wins, so the record is a BUY. (Seen at the Globex open prints: 3 of 436,082 records in the NT8 file, 1 per evening open in our book table; the NT8 side column used the same precedence: 0 mismatches over 357,160 contracts.)
   - *Last strictly between bid and ask:* UNCLASSIFIED (side 0). It still counts in volume and in the tick/print counts, adds 0 to every delta, is its own merge class (consecutive side-0 records with the same price merge), and the imbalance/run bars apply their tick rule to it (up if price above the previous print's price, down if below, else the previous side). It never occurred in the NT8 file nor in our book table on the three sample days (0 of 436,082 records; 0 between-rows in the engine book trade rows of 2026-11-09, 10 and 11).
   - *Missing quote (bid or ask 0, absent or not yet received):* the engine never met one on the checked days (0 records with bid<=0 or ask<=0 in the NT8 file; the engine book table also 0). The engine code applies the same two comparisons to whatever the stored quote holds, so a missing quote is NOT specially handled in the engine. **NT8 must do the safe thing: treat a record whose bid or ask is missing as UNCLASSIFIED (0) and log it**; if it is rare (it should be) no result changes; if it is frequent that is a feed problem to fix, not a rule to guess.
2. **Merge into prints**: consecutive records with the SAME PRICE and the SAME SIDE (including side 0) form one print (volume summed). **No time condition.** A run never crosses a session boundary (02:00, 08:30, 09:30, 12:00, 16:00, 18:00 ET) or a contract change. The merged print carries the timestamp of its FIRST record (engine convention).
3. **Bars are built on prints** with the rules of `D8_BAR_DEFS.md` (a print is one event: it is added whole to the bar it falls into; the closing print stays in the bar). Time bars (tm*, time_m_*) are NOT built on prints: they use every tick's own timestamp (merging does not change them).
4. **Print-count scale (tick and imbalance/run bars only):** the trailing-20-day scale `s_n` is computed from the daily number of PRINTS (runs, side from the tape flag in the prepass, difference immaterial), `r0_n` = median of the first 60 days under the same count (file `/mnt/l2/l2vast/_d8spec/runstats/stats_day.parquet`, column n; the days 20251106 and 20251110 are tape-hole days and were filled with 0.753 x records). The bar parameter N is NOT rescaled. Effect: tick_500 and the imbalance/run bars now contain 500 x s_n PRINTS, i.e. roughly 12% fewer records per bar than before (the engine bar counts per month drop, see table). Volume, range and session-volume scales do not depend on print splitting and are unchanged.

**Known weakness (causality), measured on Asia td 20261110:** a run is only complete when the next print with a different price or side arrives. Run duration p99 1.05 s, max 19.0 s (466 of 45,022 runs last more than 1 s, 5 more than 10 s); the delay from a run's first record to the next different print is median 0.12 s, p90 1.8 s, p99 6.2 s, max 25.5 s. The engine stamps a bar closed by a run with the first record's time; a live NT8 builder that waits for the run to end would act that much later (an entry fill is the first print after signal + 1 s, so this moves roughly 10% of bar-closing signals by up to a couple of seconds). The contract-level stream has no such delay but yields different bars (table). A 1-second gap cap on the run gives identical boundaries on both feeds (100.000% on the Asia and NY AM files) and limits the extra delay to 1 s. This is a design choice for the lead, not made here; if wanted I can run `_CANR` with the causal close time (first record of the NEXT different print) or with the 1 s cap.

## 2. Proof: contract-level versus run-merge (and versus the old engine bars), month 2026-10 (all sessions, non-truncated bars)
"Identical" = a run-merge bar with the same session, O, H, L, C and close time exists in the other set.

| bar | bars_runmerge | bars_contract | bars old engine | run-merge bars with identical O/H/L/C+close time in contract-level (%) | ... also identical volume+delta (%) | run-merge bars identical to OLD engine bars in O/H/L/C+close (%) | contract-level vs run-merge |
|---|---|---|---|---|---|---|---|
| cdr_100 | 23466 | 23991 | 23596 | 30.16 | 12.47 | 58.22 | DIFFERENT |
| dib_3500 | 25290 | 50384 | 37784 | 0.3 | 0.01 | 0.53 | DIFFERENT |
| dlt_70 | 27447 | 28344 | 27729 | 2.79 | 0.96 | 19.51 | DIFFERENT |
| drb_700 | 22025 | 38088 | 36426 | 0.0 | 0.0 | 0.0 | DIFFERENT |
| lbrk_3_40 | 1769 | 1769 | 1769 | 100.0 | 27.47 | 100.0 | SAME bars (OHLC and close times); volume/delta columns differ |
| mrenko_20 | 13348 | 13348 | 13348 | 100.0 | 28.33 | 100.0 | SAME bars (OHLC and close times); volume/delta columns differ |
| swing_atr_0.25 | 20954 | 20954 | 20954 | 100.0 | 38.08 | 100.0 | SAME bars (OHLC and close times); volume/delta columns differ |
| swing_pct_8 | 4321 | 4321 | 4321 | 100.0 | 27.61 | 100.0 | SAME bars (OHLC and close times); volume/delta columns differ |
| tick_500 | 13276 | 22167 | 19396 | 0.0 | 0.0 | 0.0 | DIFFERENT |
| vol_1100 | 14079 | 14099 | 14087 | 2.29 | 1.4 | 12.7 | DIFFERENT |
| vol_350 | 44237 | 44427 | 44308 | 0.87 | 0.5 | 6.61 | DIFFERENT |
| vol_6000 | 2529 | 2530 | 2529 | 11.59 | 7.28 | 28.03 | DIFFERENT |
| vol_750 | 20657 | 20707 | 20673 | 1.67 | 1.07 | 7.98 | DIFFERENT |
| vrb_700 | 26802 | 45174 | 42291 | 0.0 | 0.0 | 0.01 | DIFFERENT |
| vsess_120 | 19956 | 20067 | 19993 | 1.87 | 1.14 | 11.9 | DIFFERENT |
| vsess_50 | 8308 | 8326 | 8316 | 3.85 | 2.44 | 24.42 | DIFFERENT |
| vsess_600 | 97656 | 99927 | 98516 | 2.03 | 1.08 | 11.63 | DIFFERENT |
| vsess_80 | 13304 | 13360 | 13323 | 2.53 | 1.62 | 14.9 | DIFFERENT |

**Reading.**
- **Price bars (line break, Renko, swing, both swing kinds): identical** in O/H/L/C, close time, and bar count between contract level, run merge AND the old engine bars (100.00%). Only the volume and delta columns move because the volume of the closing run is split differently. Books whose trigger uses only O/H/L/C and bar times (line-break L7cc56d99's VWAP-level break, swing L488784d8's rate-of-change with the bar durations, Renko L3faac8df's trendline, swing_pct L6547965c) therefore need only this proof for the bar; the stack books L7cc56d99 and L488784d8 are re-run anyway (queue 1).
- **Time bars: unaffected** (built from each tick's own timestamp; proved in D8_FEED_CHECK.md section 6).
- **Everything that accumulates volume, delta or counts (volume, tick, session-volume, delta, cumulative-delta-range, imbalance, run): DIFFERENT** between contract level and run merge, and different from the old engine bars (at most 2% to 28% of bars survive unchanged for volume-type bars; 0% to 0.5% for tick and imbalance/run bars, whose bar counts also change). The cause is the closing print: in the old engine and in the run merge the whole closing print/run stays in the closing bar (overshoot), at contract level the bar closes exactly at the crossing contract; the cumulative boundaries then diverge for the rest of the session. For imbalance/run bars the per-print EWMAs also see different events.
- Conclusion: the **run merge is the rule**; the contract-level `_CANQ` sets are superseded (they stay as a reference, and show how sensitive the volume-clock book is: Lfb608c7b breaks on them too). Rebuilt as run-merge sets under `_CANR` (queues `pending_canr1.txt` (4 stack sets) and `pending_canr2.txt` (15 pool sets)).

## 3. What was built
Bars (18 rows, 44 months): `/mnt/l2/l2vast/_d8spec/bars_r/<row>/<YYYYMM>.parquet`. Events `/mnt/l2/l2vast/_d8spec/ev/<id>_CANR.parquet` via the unchanged `ny_build.events()` code path (bars redirected). Sets `TL3_ALN_<AS|NY>_<id>_CANR`.


## 4. CAUSAL variants (lead decision 15:4xZ): _CANC and _CANG

**Note for the relay: a number built with a first-record stamp (_CANR) is optimistic by up to the run-completion delay.** `_CANR` is kept only as a reference.

- **_CANC** = run merge (consecutive same price + same side, no gap condition), side = last-vs-bid/ask; the merged print, and so the bar close and the signal time, is stamped with the time the run is KNOWN complete = the timestamp of the next print with a different price or side (for the last run of a session or contract: its own last record). Sets `TL3_ALN_<AS|NY>_<id>_CANC`, bars `/mnt/l2/l2vast/_d8spec/bars_c`, events `_CANC.parquet`, queue `pending_canc1.txt`.
- **_CANG** = run merge with a 1-second gap cap (a record more than 1 s after the previous record starts a new print), close time = min(next print's time, last record of the run + 1 s) (needs a 1 s timer in NT8). Sets `_CANG`, bars `bars_g`, queue `pending_cang1.txt`.

Share of print boundaries identical between our tape and the NT8 export (unit by unit; side from last-vs-bid/ask on both), and the causal delay (seconds from the run's first / last record to the time it is known), td 20261110:

### Asia, td 20261110

| rule | tape_prints | nt8_prints | identical_boundaries | match_pct | known_minus_first_record_s_p50 | p90 | p99 | max | known_minus_last_record_s_p50 | p99_last | nt8_minus_tape_known_ms_p50 | p99_ms | max_ms |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C (no cap, known at next different print) | 45022 | 45022 | 45022 | 100.0 | 0.117 | 1.845 | 6.194 | 25.52 | 0.102 | 5.911 | -0.12 | 42.0 | 255.7 |
| G (1 s cap) | 45486 | 45486 | 45486 | 100.0 | 0.119 | 1.0 | 1.002 | 2.35 | 0.107 | 1.0 | -0.11 | 41.9 | 255.7 |

### NY AM, td 20261110

| rule | tape_prints | nt8_prints | identical_boundaries | match_pct | known_minus_first_record_s_p50 | p90 | p99 | max | known_minus_last_record_s_p50 | p99_last | nt8_minus_tape_known_ms_p50 | p99_ms | max_ms |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C (no cap, known at next different print) | 208040 | 208040 | 208040 | 100.0 | 0.012 | 0.123 | 0.366 | 1.72 | 0.011 | 0.35 | 3.9 | 561.8 | 1582.8 |
| G (1 s cap) | 208040 | 208040 | 208040 | 100.0 | 0.012 | 0.123 | 0.366 | 1.42 | 0.011 | 0.35 | 3.9 | 561.8 | 1582.8 |

Reading: both causal rules give 100.000% identical boundaries on both sessions (45,022 / 45,486 Asia, 208,040 NY AM). The known-completion time of the same print differs between feeds by the CQG timestamp jitter only (median about 0 ms, p99 42 ms Asia / 562 ms NY AM, max 256 ms / 1.58 s). Causal delay with no cap (C): Asia median 0.12 s, p90 1.8 s, p99 6.2 s, max 25.5 s after the run's first record; NY AM median 0.012 s, p99 0.37 s, max 1.7 s. With the 1 s cap (G) the delay is bounded at about 1 s after the last record (Asia max 2.35 s after the first record).


## 5. CLASS TABLE of EVERY bar type in the search universe (relay order 1618Z item 4; pool books by class below)
Source: all cells of `/mnt/l2/l2vast/_split/best_books_{asia,nyam}_full.csv` (Asia 2,821, NY AM 4,794 distinct cells; "pos" = positive $/wk in both L6M and L3M on the old split). Test: each type's bars rebuilt for 2026-10 on run-merged prints with the quote-rule side (first-record stamp, so the test isolates the bar rule; `bars_r`-style builder, all grid rows of the type) and compared with the stored engine bars (non-truncated bars; share of run-merge bars with an identical session, O, H, L, C and close time). **UNAFFECTED = 100.00% on every row tested**: the book keeps its BASE result as long as D8 builds the bar from the raw tick stream (a price bar closes at the first record that breaches, as in the old engine; only the volume/delta columns of the closing bar differ, which these triggers do not read). **AFFECTED = needs a _CANC (causal run merge) set.** Note `mom` (explicitly asked): AFFECTED (20% to 54% of bars equal): a momentum bar opens at the next record after a close and the run merge removes the rest of the closing run, so every later bar differs.

| bar_type | cells_Asia | cells_NY_AM | CLASS | test_or_proof | why |
|---|---|---|---|---|---|
| tmN | 304 (165 pos) | 412 (182 pos) | UNAFFECTED | by construction: built from every tick's own timestamp (not from prints); verified 479-480/480 closes identical under variants a-d (D8_FEED_CHECK.md section 6); tm rule D8_BAR_DEFS.md section 8 | time bars use ticks |
| vol | 224 (137 pos) | 429 (205 pos) | AFFECTED: needs the run merge | month 2026-10, 8 rows (131457 bars): 6.61% to 28.03% of run-merge bars equal old-engine bars in O/H/L/C + close time | closing print overshoot / cumulative boundary |
| time_m | 302 (180 pos) | 279 (136 pos) | UNAFFECTED | by construction: built from every tick's own timestamp (not from prints); verified 479-480/480 closes identical under variants a-d (D8_FEED_CHECK.md section 6); tm rule D8_BAR_DEFS.md section 8 | time bars use ticks |
| tick | 140 (75 pos) | 345 (174 pos) | AFFECTED: needs the run merge | month 2026-10, 8 rows (82067 bars): 0.00% to 0.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | counts prints (runs vs records) |
| rng | 175 (57 pos) | 287 (153 pos) | UNAFFECTED | month 2026-10, 8 rows (274769 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only |
| vsess | 154 (75 pos) | 285 (132 pos) | AFFECTED: needs the run merge | month 2026-10, 8 rows (302282 bars): 9.14% to 28.46% of run-merge bars equal old-engine bars in O/H/L/C + close time | closing print overshoot |
| renko | 158 (55 pos) | 192 (107 pos) | UNAFFECTED | month 2026-10, 8 rows (80952 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only |
| pnf | 113 (44 pos) | 165 (79 pos) | UNAFFECTED | month 2026-10, 8 rows (53241 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only |
| cusum | 145 (58 pos) | 121 (56 pos) | AFFECTED: needs the run merge | month 2026-10, 8 rows (285152 bars): 75.18% to 81.68% of run-merge bars equal old-engine bars in O/H/L/C + close time | accumulates price changes from the previous record; reset/open point depends on the next record |
| dlt | 65 (40 pos) | 170 (75 pos) | AFFECTED: needs the run merge | month 2026-10, 8 rows (209641 bars): 17.37% to 31.66% of run-merge bars equal old-engine bars in O/H/L/C + close time | cumulative boundary |
| mom | 80 (32 pos) | 155 (78 pos) | AFFECTED: needs the run merge | month 2026-10, 8 rows (157199 bars): 19.97% to 54.13% of run-merge bars equal old-engine bars in O/H/L/C + close time | bar OPEN is the price of the next record after the close; the closing run's remaining records are skipped by the run merge, so bar opens differ |
| swing | 101 (42 pos) | 133 (69 pos) | UNAFFECTED | month 2026-10, 12 rows (220811 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only (swing_pct / swing_atr = dchg kernel) |
| drb | 73 (44 pos) | 158 (80 pos) | AFFECTED: needs the run merge | month 2026-10, 12 rows (293949 bars): 0.00% to 0.07% of run-merge bars equal old-engine bars in O/H/L/C + close time | per-print EWMAs |
| dib | 82 (35 pos) | 148 (75 pos) | AFFECTED: needs the run merge | month 2026-10, 12 rows (878953 bars): 0.22% to 2.90% of run-merge bars equal old-engine bars in O/H/L/C + close time | per-print EWMAs |
| kagi | 82 (31 pos) | 141 (75 pos) | UNAFFECTED | month 2026-10, 8 rows (147066 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only |
| urenko | 71 (37 pos) | 139 (72 pos) | UNAFFECTED | month 2026-10, 8 rows (158362 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only |
| dol | 63 (30 pos) | 127 (64 pos) | AFFECTED: needs the run merge | month 2026-10, 8 rows (121405 bars): 6.17% to 33.28% of run-merge bars equal old-engine bars in O/H/L/C + close time | cumulative boundary |
| vrb | 44 (25 pos) | 129 (81 pos) | AFFECTED: needs the run merge | month 2026-10, 12 rows (324101 bars): 0.00% to 0.08% of run-merge bars equal old-engine bars in O/H/L/C + close time | per-print EWMAs |
| pasl | 42 (26 pos) | 115 (43 pos) | UNAFFECTED | month 2026-10, 6 rows (32696 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only |
| cdr | 46 (30 pos) | 109 (46 pos) | AFFECTED: needs the run merge | month 2026-10, 8 rows (45293 bars): 43.33% to 59.04% of run-merge bars equal old-engine bars in O/H/L/C + close time | delta path restarts at bar open |
| tib | 50 (27 pos) | 99 (48 pos) | AFFECTED: needs the run merge | month 2026-10, 12 rows (708149 bars): 0.00% to 0.87% of run-merge bars equal old-engine bars in O/H/L/C + close time | per-print EWMAs |
| dchg | 62 (25 pos) | 78 (42 pos) | UNAFFECTED | month 2026-10, 8 rows (147066 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only (swing legs) |
| mrenko | 47 (27 pos) | 88 (34 pos) | UNAFFECTED | month 2026-10, 8 rows (107479 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only |
| wrenko | 42 (15 pos) | 75 (30 pos) | AFFECTED: needs the run merge | month 2026-10, 8 rows (80952 bars): 99.47% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | wick tracking sees merged prints |
| bmsg | 0 (0 pos) | 100 (53 pos) | NOT TRADE-PRINT BASED | built from the order-book message stream: independent of the print rule but not reproducible on NT8 depth data (no MBO) | book messages |
| lbrk | 44 (9 pos) | 55 (30 pos) | UNAFFECTED | month 2026-10, 9 rows (70752 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only |
| time_s | 37 (22 pos) | 53 (22 pos) | UNAFFECTED | by construction: built from every tick's own timestamp (not from prints); verified 479-480/480 closes identical under variants a-d (D8_FEED_CHECK.md section 6); tm rule D8_BAR_DEFS.md section 8 | time bars use ticks |
| frenko | 39 (16 pos) | 43 (17 pos) | UNAFFECTED | month 2026-10, 8 rows (305424 bars): 100.00% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | price path only |
| anch | 0 (0 pos) | 76 (50 pos) | AFFECTED (by construction; separate b2 builder, not yet rebuilt) | not tested: equal-volume buckets / per-print surprise / delta-or-range accumulate over prints | accumulating |
| bmsgq | 0 (0 pos) | 35 (17 pos) | NOT TRADE-PRINT BASED | built from the order-book message stream: independent of the print rule but not reproducible on NT8 depth data (no MBO) | book messages |
| trb | 23 (8 pos) | 8 (4 pos) | AFFECTED: needs the run merge | month 2026-10, 12 rows (275884 bars): 0.00% to 0.04% of run-merge bars equal old-engine bars in O/H/L/C + close time | per-print EWMAs |
| trend | 11 (7 pos) | 20 (11 pos) | AFFECTED: needs the run merge | month 2026-10, 8 rows (80952 bars): 99.88% to 100.00% of run-merge bars equal old-engine bars in O/H/L/C + close time | wick tracking (high/low since previous brick) sees merged prints |
| entropy | 0 (0 pos) | 23 (17 pos) | AFFECTED (by construction; separate b2 builder, not yet rebuilt) | not tested: equal-volume buckets / per-print surprise / delta-or-range accumulate over prints | accumulating |
| vib | 2 (2 pos) | 0 (0 pos) | AFFECTED: needs the run merge | month 2026-10, 12 rows (895388 bars): 0.26% to 2.93% of run-merge bars equal old-engine bars in O/H/L/C + close time | per-print EWMAs |
| dltor | 0 (0 pos) | 2 (1 pos) | AFFECTED (by construction; separate b2 builder, not yet rebuilt) | not tested: equal-volume buckets / per-print surprise / delta-or-range accumulate over prints | accumulating |

### Pool books by class (Asia pool 29, NY AM pool 8)
- **UNAFFECTED (BASE stands, bar built from ticks):** Asia: time bars L9aa7805c (time_m_5), L7c368a4f (time_m_5), L1edb9fab (tm300), L1756b913 (tm240), L15f14deb (tm120), L7f41b347 / Lcbc8a7ec (tm60), L578701ed / Lff52ec0c (time_m_1), M7423c0d9 (time_m_3), L973b5c8a (tm420), Lb68a132d (tm600), Lec335094 (tm780); median Renko L3faac8df (mrenko_20). NY AM: B6f77f23d (tm45), L05350e98 (tm420), L7cc56d99 (lbrk_3_40), L488784d8 (swing_atr_0.25), L6547965c (swing_pct_8).
- **AFFECTED (need _CANC; results in D8_CAN_RESULTS.md):** Asia: Ldcdb0b6e, L7ea48296 (cdr_100), Lfb608c7b, Lbe5ac95b, L29b1bc3f, La6f6f7ad, L40bde9ea (vsess), L11152f7a, Lda55d973, Lcae177ba (vol), Lc4584864 (tick), Lc849eb8c (dlt), M3f6f752c (dib), L86781ac0 (vrb), Le9bd7276 (drb). NY AM: B2010fec9 (vol_6000), L2176f633 (dib_3500).
- **NOT TRADE-PRINT BASED:** NY AM L063a587d (bmsgq_B200): not reproducible on NT8.
- Also held by W-P2A: L08df8bb0 (mom_20) is AFFECTED (class above), needs a _CANC set before it can enter the D8 pool.
