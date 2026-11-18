# 1333Z — TODAY: NEW-BOOK SHORTLIST, ALL FOUR SESSIONS (Josh: "push the box to get this done today so we can build new books")

From: Josh's chat assistant (relay). Research orders only; nothing here touches the execution server, a live chart, credentials or spend.

GOAL BY 23:00Z TODAY: one page, autopilot/NEW_BOOK_SHORTLIST.md, with the best new-book prospects for EACH of Asia, London, NY AM and NY PM, taken all the way from the screen to the exact engine with the live layers on. Not NY AM only. This outranks finishing the rest of pass 1 (keep pass 1 running only on cores the funnel below cannot use).

THE FUNNEL (run the stages in parallel across sessions; do not wait for one session to finish before starting the next):

STAGE 1 (by 15:00Z) - LOOK-AHEAD GATE. For every reversal-type bar (kagi, pnf, renko family, lbrk, swing, dchg, pasl): write the confirming print (when the bar is final), prove by the truncation test that no trigger acts before it, and re-score with the signal stamped at that print. Publish pass/fail per bar type on the grid page. Bar types that fail are re-scored correctly, not dropped.

STAGE 2 (by 16:00Z) - SHORTLIST 12 PER SESSION from everything scored so far (grid top cells + level modules + order-flow modules): selection rule as always = positive in the last 6 months (3 months beside), prior years 2023/24/25 not a disaster (flag amber 15-30% worse, red >30%), persistence, >= 100 trades in the last 6 months. At least 6 of the 12 per session must be on NON-reversal bars (time, volume, tick, dollar, delta, imbalance, range), and at least 4 per session must be level / supply-demand triggers. No two rows the same trigger on neighbouring bar sizes. Print for each: bracket in POINTS, the same signals on plain 60/60, trades per day, average hold time.

STAGE 3 (by 18:00Z) - TRUST + NULLS on those 48: brute-force re-simulation, 6 truncation cuts, fills >= signal + 1 s; random-entry nulls >= 20 draws each AND the selection-corrected best-pick null per session; rolling procedure (pick on trailing 26 weeks -> next 2 weeks) through history with persistence.

STAGE 4 (by 20:00Z) - EXITS + LAYERS on the survivors (target about 6 per session): the 7 exit families (best non-fixed exit beside the best fixed bracket, with its null), then the live layers in fast replay (session lots, no-trade zones, context check, trade-health cuts, locks, stack cap, day caps). Every layer ON; off is a reference row only.

STAGE 5 (by 23:00Z) - EXACT ENGINE (JL3, identity first) for the best 3 per session: as a NEW book added to the live stack, and as a REPLACEMENT for the weakest live book of that session; last 6 months + 3 months + each prior year; drawdown / ulcer first, then mean; 30 controls; correlation of weekly P&L with the live stack. Asia: compare against the live Asia books, which already rank in the top 1-2% - a new Asia book must ADD (low correlation), not just match.

THE PAGE: per session a table of the finalists with, in plain words: trigger, bar type, bracket in points, trades/day, last 6 months and each prior year in dollars at 1 lot, drawdown effect on the stack, null percentile, look-ahead pass, what D7 needs to run it (custom bar type? new data feed?), and a label: BUILD-READY / NEEDS MORE / DROPPED with the reason. Publish the page at every stage (partial is fine, say which stage each row has reached). First publish by 15:15Z.

CORES: both machines 90%+ the whole time. If the funnel cannot use all cores, pass 1 fills the rest. If you judge that 23:00Z cannot be met on two machines, say so in MORNING.md by 14:30Z with the number of core-hours short - do NOT rent anything; only Josh can approve spend, by pasting to you directly.

Still required first: watchdog built and tested (1306Z). Near-target controls keep their reserved engine slots.

Reply in MORNING.md now with: accepted, stage ETAs, and anything that blocks 23:00Z.
