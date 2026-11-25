# Combined D8, all four sessions FITTED, at 6 lots; then the best lots per session (order from Josh, relayed)

Josh, 25 Nov 19:14Z, verbatim: "right now we have all books and fits stats right? last 6 months - give me stats for combined based on 6 lots for everything at top..also redo for max income with least DD different lots at top"

(relay) Reading, research only. "At top" = the four session lot boxes now at the top of the D8 panel (Lots ASIA / LONDON / NY AM / NY PM; a book's weight scales with its session's lots: lots = round-half-up(weight x session lots), min 1).

PART 1: combined at 6 everywhere. Refresh D8_ALL_SESSIONS_COMBINED.md (combine.py: one common trading-day calendar, true combined daily curve, NOT a sum of session drawdowns) for the picks AS THE FILE RUNS THEM, whole-stack engine runs at the file sizes:
- Asia: STKd8da2eb47b + JT110, 6 / 6 / 6 / 6.
- London: STKd8w42lo + its gated pick (JT4 if confirmed), 6 / 3 / 2.
- NY AM: STKd8cd0279ff + JT91, 6 / 6 / 6 / 6 / 3 / 6 / 2 / 2 / 3.
- NY PM: STKd8w42pm + JT19, 6 / 6 / 12 / 6 / 3.
Top of page: lots per session and per book. Rows: each session and COMBINED; columns L6M (lead) and L3M: $ per week, max DD, ulcer, worst day, worst week, trades per day; then 2023 / 2024 / 2025 $ per week and max DD. Say which months are in the series (data end) for each.

PART 2: best lots per session ("max income with least DD"). Using engine runs at each size (the size tests showed results are NOT linear in lots, so no scaling by arithmetic): session base lots from {0, 2, 3, 4, 6, 8} for each of the four sessions (runs that already exist: reuse; missing ones: run). Combine every mix of the four session sizes on the common calendar and report the FRONTIER on L6M: for each level of combined max DD the mix with the highest $ per week (and the same list by ulcer). Show L3M and 2023 / 2024 / 2025 beside each frontier row (drawdown first, prior years as the "not a disaster" check, by his standing rule). Mark the 6/6/6/6 row and the file's current row (Asia 6, London 6, NY AM 4, NY PM 3) in the table.

No gate or method change. Order of work unchanged (finish the London gated pick and its size table first). Post "LEAD TO JOSH" with the part 1 table as soon as it exists, part 2 after.
