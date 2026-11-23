# Josh-carry-over-first-and-fitted-combined (research order, 2026-11-23 ~17:25Z)

Josh's words, verbatim (10:21 Mountain time = 17:21Z, 23 Nov):

> "i want the numbers with the fittings - not bare - so i have an idea"

> "carry over rule looks promising - that i'm interested in - not daily stop or profit"

Everything below is the relay's reading (relay = Claude, not typed by Josh).

1. (relay, information only, merge of series on disk) On D8_ALL_SESSIONS_COMBINED.md add a table "AS THE D8 FILE RUNS AT 2 LOTS PER BOOK" = Asia 5-book with its 2-lot joint pick (BF2_JT19) + NY AM 5-book with its 2-lot joint pick (BF2_JT68) + London L19201dfc bare at 2 lots (+ NY PM bare when a 2-lot series exists; otherwise a second row with NY PM at 1 lot x 2, labelled as such): whole-stack dollars at 2 lots (not per lot): $ per week, max drawdown, worst week, worst day, share of losing weeks, for L6M, L3M, each prior year and all 42 months; the same for Asia + NY AM only; each session's line beside it. Also one row with Asia on the 4-lot pick's settings run at 2 lots if such a set exists (the NinjaTrader file's Asia defaults are the 4-lot pick BF4_JT1 while the account runs 2 lots): if it does not exist, say so (no new run under this item).
2. (relay) Cross-session work (order 0750Z): Josh is interested in the CARRY-OVER family and not in a whole-day loss stop or a whole-day profit stop / lock. Re-order the exact screen so the carry-over rules (XD: skip / half size / normal for the following sessions after an earlier session lost more than X, on a finer grid of X around $2,000-$6,000 per lot-per-book, per pair of sessions: Asia -> London, Asia -> NY AM, London -> NY AM, NY AM -> NY PM, and "any earlier session") run FIRST, with their prior-year, walk-forward and null checks next; the whole-day loss stop and day profit rows (XA, XB) drop to reference rows only (keep the rows already run, queue no more); the week rules (XC) stay as queued, behind carry-over. Report carry-over per combination (Asia + NY AM; + London; all four) at 1 / 2 / 4 lots on both bases (bare; each session's delivered pick), with how many days it fired and what it cost on days that would have recovered, and the exact engine definition (what "lost more than X" measures: closed + open P&L of the session's books at its end; when the skip lifts) for the D8 file.
3. (relay) Not in this order: any spend, new machine or data purchase; no gate or pin change.

Research only. Nothing here touches the execution server, any live chart, credentials, spend authority or data deletion.
