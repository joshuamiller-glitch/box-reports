ADDENDUM (user) to DIRECTIVE_ALPHA_20261115 — SMALL-SIZE EDGES, THE THREE D7 FAULTS, AND MORE COMPUTE. Research only. Save verbatim, log within 15 minutes.

A. SMALL-SIZE EDGES. We do not need a fund's capacity. For every forecast, book and market report capacity in contracts before the edge is gone, and KEEP edges that only support 5-50 contracts. Look specifically where large size cannot go: Asia and early London hours; the micros; thinner markets (NKD, RTY, the smaller FX and metals contracts); passive entries with realistic queue position at our size; the first and last minutes around the 17:00-18:00 ET halt; holiday and half-day sessions.

B. THE THREE D7 FAULTS THE USER NAMED, each tied to the forecast:
1. RE-ENTRY AGAINST THE TREND. Define "trend has turned against this book" from the combined forecast and the day-type call. Test: block or half-size same-side re-entries while the forecast is against them; require the forecast to flip back before the next same-side entry; after two cuts on one side in a session, that side needs forecast agreement to trade again. Report per book and session, and what it would have done on the 20 worst weeks of the post-mortem.
2. THE FIXED BRACKET. DIRECTIVE_BASIC_TESTS Part 1 (static grid, then lookup by condition) stays first. Add the forecast-volatility lookup as one more bucket type once the forecast exists.
3. ONE INSTRUMENT. PART 3 of the parent order. In addition, port each D7 book's own entry logic (K7, M7, U7, P7, H7, A7) to ES, RTY, YM, GC, CL, ZN and 6E with instrument-scaled brackets, per session, exact-style simulation with each market's costs: which books travel, and what a multi-market D7 does to drawdown through diversification.

C. COMPUTE. The box is at 98% of 32 cores, memory-limited, with hundreds of jobs queued per tag. QUOTE (do not buy) what a larger or second research machine costs per month at three sizes (about 64, 128 and 256 cores, with memory to match the engine's per-worker need), from the current provider and two others, and state how many hours each would cut from the present queue. Also state whether the exact engine and the forecast training can use GPUs, and the cost of one GPU machine if so. The user decides.

D. AUTONOMY. The lead generates and tests its own hypotheses from results, without waiting for the user, within the standing rules: after each batch, write three new testable ideas that follow from what just passed or failed, register them, run them, and log them in a HYPOTHESIS LEDGER (idea, why, test, result). The auto-expand protocol and all controls apply. Report the ledger count in the hourly block.

Same rules, controls and reporting as the parent order.
