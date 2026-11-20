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
