# ORDER 20261119_1156Z - fake-fill scan of ALL results; layers landing rate; alert G W-SHORT

From: Josh's chat assistant (coordinator). Research orders only. Nothing here touches the execution server, the live chart, credentials or spend. Delete nothing.

## 1. Fake fills (the -$506,325 Thanksgiving trade): prove nothing else is contaminated
a) Scan EVERY trade file in every result tree (ladder Asia / NY AM / NY PM / London, near-target NT, ORB, XA3 and its layer sets, exit-engine, layer-fit, controls, JL3 baseline, AX/AB lead cells): list every trade with entry or exit price < 1,000, or |gross| per lot > $20,000, or exit time more than 10 minutes after the last print before it. Post counts per tree and the list (file autopilot/FAKE_FILL_SCAN.md). "0 found" per tree must be stated explicitly.
b) Which verdicts already told to Josh used a month with such a trade? (Asia L6M / L3M rows use 202605-202610, so they should be clean: confirm by scan, not by argument.)
c) ONE convention for the fix in every events builder (Asia, NY, London, exit-engine): if no print follows the scheduled exit within N seconds, exit at the last print at or before it. Pick one N (W-ASIA uses 600 s, W-EXITENG 120 s), write it in DECISIONS.md, apply it everywhere, and say how the engine itself treats an exit with no print (it filled at -0.25: that engine behaviour must be guarded in the research launcher so a missing print can never produce a price; a set-month with such a fill must FAIL loudly, not land).
d) List all exposed session ends 2023-04..2026-10 (holidays / early closes) and re-run every affected set-month. Then post the rule-B table for the Asia winners with real 2025 numbers.

## 2. Layers are landing ~80-100 set-months/h with a quota of 36
At 2x fast jobs (~180 s) 36 slots should land ~700/h. Find why the NYL slots do not fill (admit order, queue position, lease), fix it, and post the measured NYL rate. Target: the fit sets (432 each) of the tier-0 / tier-1 candidates land within 3 hours. Since rule B currently passes nobody (Asia waits for the artefact re-run; NY AM cells miss persistence by 0.02), run layers for: the NY AM cells with no RED year (L01811caa, L6a25b155) and the 4 Asia cells with bare persistence 0.622, first.

## 3. Alert G: W-SHORT silent since ~10:20Z, UNANSWERED since 11:20Z (re-wakes at 11:22Z and 11:38Z got no G ANSWER)
Answer it. Resume W-SHORT; it owns the calibration (deeper rungs, by-family and by-side tables) and the level re-run that starts when the stale re-run ends (~12:30Z).

## 4. Rates
Fleet rate 3,204/h at 11:45Z (up from 2,424). Post the rate again at 12:30Z with restated dates: Asia ladder, Asia + NY AM, and the first candidate through ALL gates.

One LEAD NOTE answering 1-4.
