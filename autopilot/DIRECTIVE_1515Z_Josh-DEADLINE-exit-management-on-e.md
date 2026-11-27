# DEADLINE: tested exit management on EVERY live book for Sunday's Globex open (order from Josh, relayed)

Josh, 27 Nov 15:15Z, verbatim: "you better have exit management for all books ready for Sunday globex - no wonder it's not booking profits - it was 14k open profit and now will probably stop out - most stupid thing i've seen - no retail trader would do this"

(relay) My reading. A live NY-FIB trade (6 lots, 120/120) reached about 113 of 120 points and came all the way back because the live NY AM and London books carry NO per-book profit protection. Josh's standing rule is that every layer stays ON and "none" is never a deliverable. This is a HARD, DATED job that runs beside the algo build and takes whatever servers it needs: the relay must build and Josh must load before Sunday 29 Nov 23:00Z. Research only on the box.

WHAT IS NEEDED BY SATURDAY 28 NOV 16:00Z (earlier is better; post each session as it finishes, NY AM and London first because they are the unprotected ones, then Asia, NY PM):
1. For EVERY live book (Asia 4, London 3, NY AM 9, NY PM 4 + NP-MACD, NP-CONF): a tested PROFIT-SIDE rule and a tested LOSS-SIDE rule, on the EXACT engine, inside the live mix with the live account layers and live lots. No empty side on any book.
2. MENU, per book, only things the live NT8 file already has or that are a few lines to add (say which is which):
 - profit side: lock (LK: at 50 / 65 / 80 / 90% of target move the stop to +0 / +10 / +20 points; add: to a FRACTION of the peak, keep 50 / 67 / 75% of best open profit); take (TK); near-target trail (once >= 70 / 80% of target, trail 0.15 / 0.25 of the target distance behind the best price); breakeven after 50% of target;
 - loss side: the existing cuts (CU, CX), scratch (SCR), no-follow-through (NFT), stop-hunt variant (SHV), zones; and for the bell: profitable trades managed in the last 15 / 30 minutes.
 Screen each alone, then the JOINT profit + loss pair per book inside the mix (never one side on a frozen other side).
3. PICK by Josh's standing rule: best recent (L3M / L6M) that passes the prior-year filter, drawdown and worst week first; where nothing beats bare, deliver the BEST SETTING anyway with its evidence and mark it WEAK ("none" is not allowed). Report the near-miss numbers beside each pick: open profit given back from the peak per year before and after.
4. CHECK THE MIX: each session's mix with all its books on their picks versus the live mix as run: max DD, worst week, income, L3M, L6M, by year.
5. KEYS PAGE FOR THE BUILD: EXIT_MGMT_SUNDAY.md, per book: the exact setting strings in the live file's own keys (LK=, TK=, CU=, CX=, SCR=, NFT=, SHV=, ZH=/ZS= and any NEW key with its exact definition: trigger, level, rounding, order of evaluation with the existing rules, what happens at 1 / 2 / 3 / 6 lots), every line SPEC or READING, plus per-bar match rows for 2 dated trades per book where the new rule fires.
6. If the full job cannot finish for all books by the time above, finish in this order and say what is left: NY AM wide-bracket books (NY-FIB 120/120 and the 90-point books), the rest of NY AM, London, Asia, NY PM.
The algo build (loop A/B/C, loss side first) continues; when a loop passes the exact engine for a book it supersedes that book's setting later. Post a LEAD TO JOSH line now with the row count and the hour each session will be ready.
