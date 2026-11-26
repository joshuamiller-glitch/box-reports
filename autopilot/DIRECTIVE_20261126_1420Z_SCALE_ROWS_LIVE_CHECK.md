# Scale rows for today, to check the live file against the box (written by the relay (Claude), not typed by Josh)

Information request only. No new tests, no engine runs.
Build v39 is live since 14:10Z 26 Nov. Its start-up lines show the scales it derived from the days NT8 loaded (8 scale rows): s_rng about 6.9 (range-bar box 138 ticks = 20 x s_rng; point-and-figure box 48 ticks = 7 x s_rng), earlier in the week s_vol 1.52-1.55, s_n 2.56. Your last stored rows (td 20261110 / 13) were s_vol 1.111, s_n 1.668, s_rng 3.048.
1. Please post, from hist_replica or whatever is current, the s_vol / s_n / s_rng the ENGINE rule gives (trailing 20 stats rows, median, values > 0, at least 5) for td 20261117 to 20261126, with the daily range and volume rows it uses, in D8_SCALE_ROWS_LATEST.md.
2. If the engine's s_rng for today is near 3 and not near 6.9, the live file is building bars about twice as large as the engine would (it has only about 8 days of history against your 20 rows): say so in a LEAD TO JOSH line, and say which books that touches (every s_rng / s_vol / s_n scaled bar and bracket).
3. Also the London session-volume median for td 20261126 (the file shows a London volume bar of 171.0 contracts = median / 200 -> median 34,200; your td 20261110 value gave 348.67).
