Updated 2026-11-19 05:30Z by W-NYENG. PRIORITY (order 0220Z): 1 Asia, 2 NY AM, 3 London, 4 NY PM (nothing dropped). Rule: a new book enters D8 when it beats the live book(s) it replaces in the exact engine vs TODAY's stack (drawdown first, then $/wk; L6M + L3M; no RED prior year; persistence > 0.60; 30 date-shift controls) AND has had the exit run on its own entries; "BETTER, calibration pending" until the calibration exists.

| order | session | D8 candidates | REPLACE rows finished | beats live book: yes / no / pending | exit run | date decided |
|---|---|---|---|---|---|---|
| 1 | Asia | 1954 REPLACE rows listed in D8_CANDIDATES.txt (20 cells with engine rows; 0 beat a live Asia book) | 7 | 0 yes / 7 finished-no / 0 pending | pending (exit screen takes Asia cells as their REPLACE rows land) | not decided; engine-only estimate Asia first ~Nov 21 04:00Z (W-ASIA, page NEW_BOOK_BEATS_LIVE_ASIA.md) |
| 2 | NY AM | 6830 REPLACE rows listed in D8_CANDIDATES.txt (187 cells with engine rows; 4 cells beat a live book) | 122 | 4 / 118 / 19 | pending (NOT started) | not decided; earliest 2026-11-20 12:00Z if the exit screen starts by 11-19 06:00Z |
| 3 | London | W-LONENG: NEW_BOOK_ENGINE_LONDON.md | n/a here | n/a here | pending | not decided |
| 4 | NY PM (behind NY AM in every W-NYENG file) | 787 REPLACE rows listed (0 cells with engine rows) | 0 | 0 / 0 / 0 | pending | not decided (nothing run yet; queued behind NY AM) |

Missing for each candidate: prior years 2023-25 without a RED year, the 30 date-shift controls, persistence > 0.60, exit run (68 recipes): NOT started on these candidates (screen stage owner; engine families trailing / staged / SAR 11-19 18:00Z, order flow 11-20 12:00Z, D8_EXIT_ENGINE_SUPPORT.md), then the engine confirmation of the top 3 recipes (ADD + REPLACE, L6M + L3M, prior years, 30 controls = 438 set-months per candidate).

D8 SPEC DATE (Asia + NY AM only): the engine cost after the exit screen for the 4 NY AM cells that beat a live book today is 1752 set-months = 1.9 h at the measured 928 set-months/h (0.6 h at 2,894/h). The date is set by the exit-screen stage and the unbuilt engine exit families, not by the engine queue: earliest 2026-11-20 12:00Z for NY AM, conditional on the exit screen starting by 11-19 06:00Z (duration not measured, candidate list still growing). Asia: W-LONENG's date; the combined date is the later of the two.
