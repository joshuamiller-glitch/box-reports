# NY AM weighted pick JT91: coded; five readings to confirm (information note)

written by the relay (Claude), not typed by Josh. No new tests, no gate or priority change. The file (build v29) now carries TL3_SR_NY_STKd8cd0279ff_BF1_JT91 for the nine books. Please confirm or correct each line from the engine code, one line each:

1. FR_LOSS8 (kind nft, X 5, N 20) on MF2: coded as ONE check at the first closed second at or after 20 minutes from the entry fill: exit if unrealised (closed-second mid) < +5 pts; never checked again in that trade. Or is it checked on every closed second after 20 minutes?
2. DLB9 on the weighted stack: coded as sum over the nine books of (day P&L + open P&L) <= -$4,000 x LOTS OF A FULL-WEIGHT BOOK (4 at the fit basis = -$16,000; 6 in the file = -$24,000); then no new entries for the nine, open trades run. Is "lots per book" the full-weight lots, or something else when the books carry 4 / 2 / 1?
3. BL4: coded as arm 2.0R, give-back 33% (halt + close when the day falls to 67% of its peak), weekly floor -12R, R = the book's own stop x $20 x its lots. Is the weekly floor -12R in BL4?
4. SC1 on this stack: coded as acting on the NY AM books (session 3), share 25%: on a full stop of one book every other open same-side book of the nine is cut by ceil(0.25 x position), at least 1 lot (6 lots -> 2, 3 lots -> 1, 1 lot -> closed). Confirm it acts in session 3 for this set (the page line says "scope Asia-only").
5. CAP6 with DLA9 together: coded as DLA9 first (-2R: no new entries, open trade runs), then CAP6 (-3R including open P&L: the open trade is closed, book halted). NRT4 on MF3 coded as: once the best excursion reached 0.95 x target, exit when price gives back 0.1 x target from that best (per print).
Also: the file's lots for this mix are 6 / 6 / 6 / 6 / 3 / 6 / 1 / 1 / 3 until your FS631 / FS632 verdict says 1 or 2 for MF7 and MF8.
