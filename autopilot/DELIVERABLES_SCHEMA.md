# DELIVERABLES schema (lead, 2026-11-17 14:55Z) - user order 14:47Z (autopilot/DIRECTIVE_DELIVERABLES_20261117.md)
Page: autopilot/DS3_MAJOR_DELIVERABLES.md (assembled by W-DL; first version by 02:00Z 2026-11-18, refreshed hourly). Every row is a BEST SETTING with its evidence and an honest label; "off", "no rule", "native 60/58", "nothing found" are reference rows only. Labels: CONFIRMED / LEAD / WEAK-BUT-POSITIVE / BEST-AVAILABLE-NOT-PROVEN (use the calibrated rule for CONFIRMED/LEAD: engine-exact controls required).
Each owner appends/replaces its rows in /mnt/l2/l2vast/_deliver/<OWNER>.jsonl (one JSON object per line; rewrite the whole file atomically each refresh; update at least hourly via your unattended loop). Row fields:
 table: 1 BRACKETS | 2 BOOKS | 3 LOTS | 4 BEHAVIOUR
 row_id: unique string (e.g. 'K7|asia|bracket', 'NYAM-book-1', 'DAYDONE')
 cell: book x session (x environment bucket) or the book/rule name
 setting: the exact setting to run (Table 1: the THP policy line 'bracket <book> <session> stop=<pts> target=<pts> [timestop=<min> halfoff=...]' as in ~/internals/THP_POLICY_D7_v2_9.txt format; Table 2: plain spec exact enough to code: signal, bar, window, entry type, stop/target/time-stop, lots; Table 3: lots today -> proposed; Table 4: the rule with its parameters)
 today: what runs today (e.g. '60/58')
 label: one of the four labels
 metrics: {window: {ulcer_change_pct, maxdd_base, maxdd_cell, worst_week_base, worst_week_cell, mean_wk_base_lots, mean_wk_x175, mean_wk_484}} for windows L6M, L3M, HOLD, GAP, PRE, XP, pooled (last 6 months first; null where not run)
 controls: e.g. '30 valid persistent draws, percentile ulcer .93' or 'not run (screen only)'
 untouched_year: numbers on the untouched year if walk-forward selected
 trials: trials counted / correction
 behaviour: (Table 2) standalone untouched-year R and trades; behaviour in D7's five deepest drawdowns and 20 worst weeks; stack test result
 ds7_need: 'panel setting' | 'policy line' | 'existing switch (name)' | 'new code (describe)'
 evidence_page: path of the page with the detail
 caveats: one short line
 updated_utc
