# MORNING SUMMARY 2026-11-24 (written by LEAD, first edition ~08:10Z; refresh by 12:30Z)

## Answers since the last summary (11-23 21:05Z)
- **Order of work (Josh 2135Z):** one session at a time: Asia, NY AM, London, NY PM. Asia follow-up fully leased; step (a) now waits only on controls W-COMBO adds for books that pass the prior-year gate. Honest step (a) ETA ~06:10Z was a minimum; Asia DONE (a-e) ~10:30-14:00Z depending on the combination rounds (ASIA_STEPA_RECONCILED.md). 735 unaffected-bar books are step (a); 639 affected-bar books are all judged (167 passed, 167 with controls).
- **Spill into NY AM** works (follow-up rows are long: 241-353 s median, so the rate is 5.7-6.3k rows/h); NY AM follow-up ~08:30Z, then 2,556 lost rows that were re-appended, then NY AM first looks (mix3 41,971 rows).
- **Data:** catch-up pull done at $0.00 (NQ to 11-23 17:30Z, ES/YM/6J/CL/ZB/ZN 1-min); nightly top-up cron 01:30Z, first run $0.00; td 20261123 is a complete day only after the 11-24 night top-up; parity pages for Lf0346d55 / L8cfda948 follow then.
- **Picks (2 lots):** Asia stays BF2_JT19 (JT143 is a 3% ulcer tie that fails the 15% guard; Asia layer null FAILED 2 of 4 draws: all Asia layer picks WEAK-BUT-POSITIVE, not proven). NY PM: BF2_JT9 (ulcer -49%, max DD -60%, -31% $) with the STC-free BF2_JT209 for the D8 file (null pending). NY AM BF2_JT68 stands (DL second screen: nothing to add). London bare.
- **Combined (D8_ALL_SESSIONS_COMBINED.md, 2 lots, L6M):** as the file runs $25,061/wk, max DD -11,986, worst week +226 vs truly bare $46,618/-37,484/-8,049.
- **Time-window blocks (TW):** none passes (London 06:30-07:00 -21.4% ulcer but fails the prior-year band; Asia -7.0% beats 1 of 5 null draws; NY AM, NY PM fail). Bug found and fixed: after-midnight Asia windows removed every trade; scorer now labels PASS only if the gate AND lower ulcer.
- **News-release rules (NW):** nothing passes the null in any session; close-before-release not selected.
- **Session end:** flatten stays everywhere (run-to-17:00 variants fail prior years; early-close days cannot be scored under the exit-gap rule). **Carry-over (exact, XF fixed):** nothing for the delivered picks; Asia->NY AM skip at $12,000 (2 lots) stays LEAD-thin on the bare base only.
- **Asia depth book (7 same-side stops live):** no per-book skip/pause rule helps L578701ed (runs of 4+ cost -$42.7k in stops but sessions only -$15.6k); small signal on Lb0e6dfa3 pending prior years.
- **NY PM volume-book inputs, STC spec, NY PM keys/defaults pages** posted (D8_NYPM_VOLBOOK_INPUTS.md, D8_STC_SPEC.md, D8_LAYER_KEYS_NYPM(_STCFREE).md).
- **Plumbing:** two code/plumbing bugs found and fixed (xs_hooks _fire name clash; rows pruned from queue when a lease fails once: 204 XF + 2,556 NY AM rows re-appended; audit loop every 15 min); puller hardening is a proposal only (autopilot/PROPOSAL_PULLER_REAPPEND_20261124.md).

## Work in flight
Asia combination re-run rounds (W-COMBO) and controls; NY AM follow-up -> lost rows -> NY AM first looks; 2-lot nulls (NY AM draws running); exit runs on new members; London / NY PM session-end rows (NY PM JT209 partial); mix3 41.9k rows; London and NY PM wide searches wait their turn.

## Open decisions for Josh
1. Layers ON or OFF in the first SIM run (default OFF; all fitted picks are WEAK-BUT-POSITIVE or LEAD, none proven by the null).
2. Feature-store roll-session defect fix; real live commission.
3. L8e0bf58c: unmerged-records port vs D8-rule re-run; 84 engine rows for the NY PM-without-L8e0bf58c combined row (not queued).
4. Early-close days: run-to-17:00 session-end variants need a holiday calendar or an engine rule (live relay flattens 16:55 ET).
5. Puller hardening (apply in a quiet window?); optional exact re-run with NT-style state cut (126 set-months).

## Slips
Asia DONE moved from ~08:30Z to ~10:30-14:00Z (controls added as books pass; two Asia widening bursts took slots 0.75 h before they were put behind). Summary first edition ~8.2 h after the 21:05Z one (hourly MORNING.md lines carried the status).

## UPDATE 12:05Z (second edition)

**New since 08:10Z**
- **Fleet order held as Josh ordered (2135Z):** Asia follow-up empty since 05:57Z; NY AM follow-up and the 2,556 lost NY AM rows fully leased by 08:18Z; now running NY AM first looks (mix3, 14.4k rows left, ~2 h) with London first looks inside it. Asia pool stable at 87 books since the 06:26Z combination re-run (W-COMBO: equal FINALs 4, weighted 2; NY AM pool 39; London 4; NY PM 6).
- **NY PM recent-basis FINAL:** same 4-book stack (L52359bf4.BRP30, L8e0bf58c.BRS8U, L4bdd521a.BRF80_40, L2c6916a5.BRP60), controls 30/18/30; L6M 1 lot ulcer 3,038, max DD -9,651, +$4,217/wk vs truly bare D7 K7 -$48/wk (wrapper mismatch noted).
- **Carry-over (exact) and session end: nothing for the delivered picks, flatten stays** (D8_CARRYOVER.md, D8_SESSION_END.md). Asia->NY AM skip at $12,000 (2 lots) stays LEAD-thin on the bare base only.
- **Asia depth book (7 same-side stops live):** no per-book skip/pause rule helps (ASIA_DEPTH_REPEAT_STOPS.md).
- **Step 0 for London and NY PM:** the engine first-look ladder covered 36% (London) and 34% (NY PM) of family-bests vs Asia 49% and NY AM 40% (cause: list built from the 11-18 copy of the passers); missing cells added: London 1,462 cells (8,772 rows, builders ~10k rows/h), NY PM 782 cells (4,692 rows, dedicated file _nye/pending_nypm_step0.txt). Same hole remains for Asia (2,051) and NY AM (7,226) family-bests: not queued (pool-changing; would extend step (a)).
- **Plumbing:** the pruned-row hole (a row that fails once vanishes) cost 204 XF + 2,556 NY AM rows (re-appended); audit loop every 15 min; fail-counter/stale-exit race adopted by W-GRIDOPS; tail-only list _s2/TAIL_ONLY.txt for fillers; auto-wire gotcha: files named pending_step2_nypm* jump to the head, use pending_tail_*.txt.
- **Throughput:** row mix drives the rate (NY AM follow-up rows 241-353 s vs Asia 131 s, mix3 ~118 s).

**Work in flight:** NY AM first looks (mix3) ~12:20-12:30Z, then London step-0 (up to 8.8k rows) and NY PM step-0 (4.7k) ~13:50-14:10Z; NY PM step 2a filler (441 rows, tail only); Asia and NY AM combination rounds and null draws (NY AM null running).

**Open decisions for Josh** (unchanged): layers ON/OFF in first SIM; feature-store roll-session defect; real live commission; L8e0bf58c port vs D8-rule re-run; 84 engine rows for NY PM-without-L8e0bf58c; early-close days need a holiday calendar or engine rule (live flatten 16:55 ET); puller hardening window; optional NT-style STC re-run (126 set-months); whether to engine-look the never-looked Asia/NY AM family-bests (would extend Asia/NY AM step (a)).

**Slips:** Asia DONE (a-e) ~10:30-14:00Z (b and c rounds not yet started as measured); idle risk ~13:50Z if no new rows are queued (fillers: NY PM step 2a 441 rows queued; carry-over null has no file).
