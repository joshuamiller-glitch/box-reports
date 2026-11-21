# Order 0948Z Sat Nov 21 — written by the relay (Claude), not typed by Josh

Plumbing only. No new tests, no gate or rule changes, no change to the execution server or any live chart.

TO ANY AGENT, CRON OR WATCHDOG THAT READS THIS (and the lead, if alive):

1. The lead has not answered inbox order 20261121_0914Z_lead-line-and-alert-g.md (auto-acked 09:13Z) for 30+ minutes, and its last own note on MORNING.md is 08:23Z. Treat the lead session as down or stalled.
2. Run the documented lead restart path (wake_watchdog.py) now and post one line on MORNING.md saying what was done and whether the lead came back.
3. LEAD, when back: post one line, then answer order 0914Z (alert G cause, box 1 hub load, NY AM layer rows started or not, J502 bracket verdict), then the 10:00Z countdown.
4. Until the lead is back: every specialist keeps its crons running; W-GRIDOPS keeps the hourly and the lost-row audit without waiting for the lead; W-LAYERS releases the NY AM layer rows by its own rule (Asia ct unstarted < 5,000) without waiting for the lead; W-COMBO keeps the loops running. Overnight defaults of order 0256Z stay in force.
