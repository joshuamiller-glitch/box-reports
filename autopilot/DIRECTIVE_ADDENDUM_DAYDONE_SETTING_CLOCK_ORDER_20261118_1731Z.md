# 1731Z — ADDENDUM to 1722Z (Josh: "just order the correct thing"). Five corrections; the four phases stand.

From: Josh's chat assistant (relay). Research orders only; no spend.

WHY: DAY-DONE (22 closes, day <= -$4,200 live) was fitted to TODAY's stack. If books change, the days on which it trips change. A mask built from JL3's history is only right for "add one book to today's stack". Do not let it steer a rebuild.

1. THREE SCREEN RANKINGS per session, side by side, each clearly labelled (replaces "two ways" in 1722Z item 1c):
   (a) BARE.
   (b) OWN-STOP (stack-independent): the cell with its own bad-day stop = no new entries for the rest of the trading day once the cell itself is down 2 stops on the day (also show 1.5 and 3 stops as neighbours). This is the ranking that stays valid whatever happens to the other books; it carries the weight in the shortlist.
   (c) CURRENT-STACK MASK (JL3 DAY-DONE day-state + one position). Label on every table: "valid for ADDING a book to today's stack only; not valid for a rebuilt stack". Information, never the sole reason to shortlist or drop.
   Shortlist = cells strong on (b), with (a) and (c) shown. A cell that is strong only on (c) is flagged "depends on today's stack".

2. DAY-DONE IS A SETTING, NOT A CONSTANT. In phase 3 express it in stack-relative units and refit it for the candidate stack, jointly with everything else: close count as a multiple of that stack's typical closes per day (grid around the value that 22 represents today), loss threshold in R of that stack's own dollar stops (grid around 2R), and test whether it should count all books or be per session. Same for the day loss / profit caps when wider-stop books are in the stack. "Off" is a reference row only.

3. CLOCK ORDER. A later session's day-state depends on the earlier sessions' books, so in phases 3-4 sessions are DECIDED in clock order: Asia -> London -> NY AM -> NY PM. After each session is decided, rebuild the day-state from the chosen books (exact engine) before judging the next session. Nothing chosen for a later session is final until every earlier session is final. If an earlier session changes later, everything after it is re-run.

4. ASIA IS NOT "ADD-ONLY" (my earlier wording, not Josh's). Asia gets the same three tests as every session: replace, add, mixed, against what each live Asia book earns in the engine (publish that bar-to-beat table for Asia as for NY and London). Because Asia is the main earner the BAR is higher, not the scope narrower: a replacement must beat the live book on drawdown first AND on dollars, in the last 6 and 3 months, with no red prior year, 30 controls and the selection-corrected test; a wash is not a reason to change Asia.

5. ENGINE ROWS ALREADY ON THE PAGES (NY, London): keep them, and add one line at the top of each page: "These rows are vs TODAY's stack (JL3) with today's DAY-DONE setting; they answer 'add / swap one book in today's stack', not 'the rebuilt stack'." WP10 and XA3 stay leads on that basis.

Nothing else in 1722Z changes. Reply in MORNING.md: accepted; and confirm the OWN-STOP ranking (b) is being computed in the grid scorer, with its ETA for the cells already scored.
