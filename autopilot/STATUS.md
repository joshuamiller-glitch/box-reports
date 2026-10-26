# AUTOPILOT STATUS (hand-maintained by lead; resume point after any restart)
Updated: 2026-10-15 ~21:20Z. 48-h clock STARTED 2026-10-15T21:52Z (D3 finished; EXEC_SUMMARY.md written). Stop at 2026-10-17T21:52Z or 5 FOUND.
Phase: LOOP cycle 1 (launched 21:58Z; families C1-F1..F7 in PREREG_AUTOPILOT.md). Order: V5, T4 (A,B,E,F), E9, E10, D3, then LOOP.

## Done
T4 B, C, D, F; T3 S1, S2, S3, S6; D1 F1-F8; D2 E1,E3-E8; E10 ledger v1 (outputs/LEDGER.md; refresh after E2/E9).
## Running (as of this update)
Databento download (8 shards, data/t4, log outputs/t4/download.log), T4 A (+T3 S4), T3 S5, V5 P1, V5 P2, V5 P3+P4, D2 E2.
## Next launches
T4 E (crypto, when crypto files land), E9 (after E2), E10 refresh, D3 (7 sections), then LOOP cycle 1.
## Budget
T4 data cap $150 (tracked outputs/t4/SPEND_*.json). AUTOPILOT data cap $3,000 (outputs/autopilot/SPEND.json) - spent $2,215.22 of $3,000: RTY mbp-10 $547.68 + ES mbp-10 $1,303.05 (both jobs still 'processing' at 22:48Z) + 1-min bars for 26 outrights 2013-2026 $364.49 (complete, data/autopilot/ohlcv1m). NQ mbp-10 NOT re-bought (A5 job still processing). Remaining ~$785.
## Counts
FOUND 0. LEADS: 5-min NQ trend family (validation in V5), ES/YM dip-buy (amended survivors, small-sample), MBO seven (provisional, no H2), NQ prior-day break (D2 family), HM-heavy split (D1 F3, in E9).
- BASELINE NOTE: user's quoted pair Sharpes (1.35/1.65/2.26) = B.Cfg(); described config = 1.46/2.83/2.30. See DECISIONS.md 2026-10-15.
- TODO: rerun C3-H1 RTY cells after RTY 1-min bars complete (ap_c3_h1_run.py).

SPEND UPDATE 22:50Z: spent $2,215.22 of $3,000 = RTY mbp-10 $547.68 + ES mbp-10 $1,303.05 (both jobs 'processing') + 1-min bars 26 outrights 2013-2026 $364.49 (complete; data/autopilot/ohlcv1m). NQ mbp-10 not re-bought (A5 job processing). Remaining ~$785.

UPDATE 2026-10-16 13:50Z: cycles 1-10 done, FOUND 0. 15.9 h of 48 used. Spent $2,215.22. C2-G2 worker died without a report (no process, no REPORT_C2_G2.md) -> relaunch in cycle 11. mbp-10 jobs (NQ/ES/RTY) still 'processing'. MORNING.md written (outputs/MORNING.md). Load ~0: nothing running; cycle 11 to be pre-registered next.

UPDATE 2026-10-16 14:10Z: DURATION AMENDMENT: no 48h stop; runs until told. 5 worker agents launched (WT, P1B+P2, B1/4/7/10/11, B2/3/5/6, B12/9/8/DIP/HM/B14). P1 pair scaled-bracket result: outputs/autopilot/p1/P1_all.csv. Next: rewrite EXEC_SUMMARY key finding, MORNING.md every 4h (next 18:00Z), weekly data extension (due ~10-22), ledger refresh.

UPDATE 2026-10-16 evening: E1-E8 and BACKLOG2 dispatched. Weekly extension procedure: extend NQ/ES/RTY 1-min + NQ/ES trades (for PERS30), rebuild H2, then python3 outputs/autopilot/forward/ap_forward_score.py --refresh, then re-score all LEADs/FOUND-PENDING.
UPDATE 2026-10-17 EXTENSION: weekly data extension done (data + pair H2 end 2026-10-16, FORWARD.md live rows). Next due ~2026-10-24. Procedure scripts: code/census/night_ins/ap_ext_*.py (build, h2, drv, ohlcv, icache, series); license lag ~8 h so buy after Fri 21:30 UTC + 8 h.
UPDATE 2026-10-25 EXT: L2 week 10-19..10-24 bought ($35.59), NQ/ES/RTY library+series+rows+bench3 extended to 2026-10-23 from L2-derived trades (no other purchase); join reconciliation JOIN_RECON.md section 5. Next L2 purchase Sat 2026-10-31: START 2026-10-24T00:00Z, END 2026-10-31T00:00Z (includes Sunday 10-25 evening). See REPORT_EXT_1019_1024.md.
