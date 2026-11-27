# ORDER: everything on the cross-market management loop; done and coded for Sunday's Globex; scalping track paused (order from Josh, relayed)

Josh, 27 Nov 15:17Z, verbatim: "order the boxes to have the cross market thing done and coded for globex - we can pause the scalping one - everything on this - frist thing with promise"

(relay) My reading. Loop C (learned loss-side management from the trade's own state plus the other instruments) is the first thing with promise, and Josh wants it finished for every book and in the relay's hands in time to be coded for Sunday 29 Nov 23:00Z. All servers on it. Research only on the box; the live decision per book is Josh's on Saturday with your exact results in front of him.

PAUSED until further word (keep what exists, delete nothing): W-SCALP short order-book targets; the negative-R book search (W-NEGBOOK) and its sleeve rows; loop A/B tuning; the L3 moment tests; remaining session-end variants beyond the rows already queued. NOT paused: the Sunday exit-management job (15:15Z: tested profit-side and loss-side setting on every book: it supplies the profit side and the fallback for any book the loop does not pass) and the near-miss table.

1. EXACT ENGINE VERDICT FOR EVERY BOOK, Asia MF1 first, then Asia, NY AM, London, NY PM, as each bundle is ready. For each book, these rows, inside its live mix with live account layers and live lots, and alone:
 a. live as run (bracket + Trade Health): the reference;
 b. loss loop + the book's OWN target and own stop kept (loop only cuts under-water trades earlier);
 c. loss loop + 1.5x safety stop + own target kept;
 d. loss loop + 1.5x safety stop + NO target (the quick-screen design);
 e. the best of b-d + the profit-side setting from the Sunday exit-management job when it exists.
 Each with the re-entry rows (L0 free, L1 slot lock) and both modes (replacing Trade Health / on top of it). Loss-side table first (full stops avoided, false-exit cost, net), then max DD, worst week, worst day, income, L3M and L6M first, by year, NQ up weeks versus down weeks, long books and short-capable books apart. Random-management null (same action rate) and pessimistic fills on the best row per book.
 Josh must be able to see how much comes from cutting losers (b, c) and how much from removing the target (d).
2. ALL THE OTHER INSTRUMENTS IN THE MODEL that exist at 1-second or 1-minute resolution and that NT8 can also read live: ES, RTY, YM, ZN, ZB, CL, GC, 6E, 6J, NKD. Leave out for this deadline anything NT8 cannot get as a data series on Sunday (UW options flow, stock tapes, L3): they are the next version. Say which inputs each book's model actually uses.
3. PER-BOOK VERDICT TABLE in ALGO_REPORT.md kept current: PASS (beats the live row on drawdown and worst week with income not lower by more than 10%, or more income with drawdown not deeper; recent windows not worse; beats the null) / FAIL / STILL RUNNING, with the row that passed.
4. FOR THE RELAY'S BUILD, in the mirror as .md (my 15:07Z list), with these times: LOOPC_SPEC.md complete and LOOPC_MODEL / LOOPC_MATCH for Asia MF1 by TODAY 22:00Z; every other fitted book by SATURDAY 14:00Z. The model file per book must be the one that would trade on Sunday: trained on all data up to the latest stored day, with its training window, purge and hash stated. Model as LightGBM text dump (or the trees as a plain table) so NT8 can evaluate it without any library. Match vectors: per decision minute the feature row, the four predictions, the action, and the raw per-second prices of every instrument used, from entry-3900 s to exit.
5. LEAD TO JOSH line at least every 60 minutes with: books done / passed / failed on the exact engine, and whether the 22:00Z and Saturday 14:00Z deliveries are on time. If something will be late, say so the moment it is known.
