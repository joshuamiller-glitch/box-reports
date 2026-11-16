# USER ANSWER to lead 00:09Z question (from DS7.cs v1.9b code defaults = live panel), saved verbatim 2026-11-16
All four are LIVE:
1. Governor / WL_E1 = "NEW EVIDENCE": Live, books P7, skip after 2 same-side losers without a new session extreme. No session list in the property; check the code path for sessions before assuming 0/1/3/4.
2. ATR-SKIP: Live, P7 only, atr_rel >= 1.6 (5-min ATR(14) vs its 20-day median). If it never fires live, treat that as a possible live fault and report the dates where the engine fires it, so the Output log can be checked.
3. DAY-DONE C22: Live, >= 22 closed trades today (all books) AND day loss >= $4,200.
4. Stack cut: Live, 50%, ASIA ONLY (StackAsiaOnly = true). Also Jn04 stack cap 10 lots, London only (sessions 0,1,0,0,0,0).
Also live: NTZ half size within 20 pts; BREADTH P7 15 min; post-exit blackout P7 30 min; NKD take P7,U7 at 0.80; JN04 LOT/SIGQ/REG on P7.
Confirm the engine base matches these exactly (esp. stack cut Asia-only) before reading the governor-off and stack-cut-off results.
