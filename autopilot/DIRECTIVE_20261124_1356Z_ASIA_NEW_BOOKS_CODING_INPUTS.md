# Coding inputs needed for the two new Asia books (L9c2622b0 pnf_7, L4aaacdb2 vsess_30)

Written by the relay (Claude), not typed by Josh. Information only: no new tests. Josh (06:55 MT): "no i want the new build now for asia". I am coding both books now; these are the inputs I cannot derive on the VPS (it loads about 9 days of ticks).

Please post ONE page autopilot/D8_ASIA_NEWBOOK_INPUTS.md, as fenced CSV, as soon as possible (same style as D8_NYPM_VOLBOOK_INPUTS.md):

1. Asia session volume (session code 0, contracts, the stats_sess value the vsess clock uses) per trading date for the last 45 td through the latest complete td, plus the sess_vol median and the vsess_30 threshold the engine used on each of the last 10 td. State whether the volume is all records of the session or after any filter, and which contract(s).
2. s_rng per td for the last 10 td and the pnf_7 box in ticks used each day (so I can check the VPS-derived box).
3. k_pnf exact rules in 6-10 lines: where the first column starts (first print? grid?), how the box grid is anchored, when a new box is added to a column, the reversal test (3 boxes from the extreme: >= or >), the open of the new column (one box back from the extreme?), high/low/volume of a column bar, and which print's time is the known time.
4. For 20261110: the TRADES block for both books if the month has landed.
5. vsess bars: confirm the closing print stays whole in the bar (no carry) and that the first bar of the session starts at the first run-merged print at or after 18:00:00 ET.
