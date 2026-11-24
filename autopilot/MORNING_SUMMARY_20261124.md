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
