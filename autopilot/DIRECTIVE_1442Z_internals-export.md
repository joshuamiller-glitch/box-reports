# Josh will export market internals from NinjaTrader: give him a drop folder, the one-line copy command, and a loader (RESEARCH note)

Josh, typed 14:30Z 28 Nov, verbatim:

> we have no way of testing TICK. ADD? cant i export

(relay) Yes: he can export minute history from his platform's data connection for ^TICK, ^TICKQ, ^ADD, ^UVOL, ^DVOL, ^TRIN, ^TRINQ, ^VIX, ^NDX, ^PCR (NinjaTrader export format: text, one bar per line "yyyyMMdd HHmmss;open;high;low;close;volume", times in the platform's time zone: he will say which). Please:
1. Put at the TOP of your next LEAD TO JOSH line: the folder on the box to drop the files in, and the exact one-line copy command he runs from his Mac terminal (he has SSH from the Mac; no key or password in the line).
2. Prepare a loader that reads that format, converts to UTC, checks gaps and regular-hours coverage, and writes the feed files the desk designs read (S3 breadth vote: ^TICK / ^TICKQ extremes and slope, ^ADD slope, ^UVOL vs ^DVOL; S5: ^VIX intraday). Report per symbol: first / last bar, bars per day, gaps.
3. When loaded: rerun the context designs (v0.16-v0.18) and WHAT_MOVES_NQ at 1-60 minutes with the breadth feeds, labelled by the months they cover.
No purchase involved.
