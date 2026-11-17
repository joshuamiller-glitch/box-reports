RESEARCH ORDER (relay, 11-17 05:45Z): STAGE 1 survivors table: two faults to fix before anything is called CONFIRMED.

DS3_REBUILD_S1.md "Survivors with the ulcer-primary tier test" lists 269 CONFIRMED. The top rows are family 5 columns ending _d60 / _d120 (fl259_d120, fl051_d120, fl108_d120, fl116_d120, fl222_d120 ...) with lift about 0.3-0.5 R, z 5-8, and e.g. P7 NY AM L6M ulcer -52,822 -> -5,834. Effects that size are not believable as an at-entry skip.

FAULT 1 - TIMING. In the flow library _d30/_d60/_d120 are WAIT variants: the reading is taken 30/60/120 seconds AFTER the signal. Scored against a trade entered AT the signal, that reads 2 minutes of the trade's own path. So:
 a. State in the lead log, for the top 20 survivors, exactly when each column is known relative to the entry fill (seconds), and whether the outcome R is measured from the signal-time entry.
 b. Re-score every _d5/_d30/_d60/_d120 column the two honest ways and label them separately: (i) WAIT-THEN-ENTER: entry at signal + delay at the price then, same stop/target distances, trades that would already have stopped or hit target in the wait are handled explicitly; (ii) EARLY EXIT: trade entered at signal, rule acts at +delay, value = (exit at +delay mark) minus (hold to the raw outcome), i.e. only the REMAINING path counts.
 c. Run the same timing audit on every column whose name contains "ahead" (c_B_cl_ahead_*, n_dl_sp_ahead_60) and on family 9 trade context (8% beyond bar): confirm each uses only information available before the fill. Anything that does not is removed from the at-entry tables.
 d. At-entry survivors table must contain ONLY columns known at or before the signal (_v0/_d0 and true latency variants _d1/_d2 treated as latency).

FAULT 2 - SELECTION. The tier test was run on the top 60 by |z| per cell, chosen on the same 43 months it is then tested on, against random skips. That always passes. Do not use the words CONFIRMED / LEAD for these. Instead:
 a. Walk-forward: choose conditions on months up to 2025-10 only (PRE + GAP), freeze them, then report HOLD and L6M untouched. Report how many chosen, how many keep sign, and the ulcer and mean change on the untouched months, per book x session.
 b. Null for selection: do the identical top-60-then-tier procedure on the shifted-label (11/23/37) and nonsense columns and report how many "CONFIRMED" that produces. The real count only means something relative to that.
 c. Family table: add the same real-vs-shifted comparison restricted to at-entry columns only.

THEN, for whatever survives both: plain-words definition of each column (what it measures, which feed it needs, whether D7 can compute it live from the CQG book or it needs L3/MBO), and queue engine re-runs on JL3 for the top 5 per book x session (stage 2 input). Weak cells first: K7 NY AM, P7 NY AM, P7 London, M7 London, K7 London.

Keep the adaptive permutations running. Rebuild the page with a first line that says which tables are at-entry-clean and which are not. Research only.
