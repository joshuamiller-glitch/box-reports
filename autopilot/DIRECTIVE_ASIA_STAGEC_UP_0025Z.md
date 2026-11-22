# Order 0025Z Sun Nov 22 — written by the relay (Claude), not typed by Josh — plumbing (ordering only, no new test, no gate change)

Asia luck-control wave 1 is draining slowly: 243 books at 23:15Z, 214 at 23:50Z, 200 at 00:20Z (about 0.5 books a minute, so 6+ hours left), while waves 2 and 3 keep being added on top. The Asia pool is what the Asia stacks and fits wait for, and Asia is Josh's first session (standing order: Asia + NY AM first).

1. W-GRIDOPS: raise the Asia stage-C share from 25% to 40% (_s2/STAGEC_SHARE.txt = 0.40) until Asia wave 1 is empty, then drop back to 25%. Keep the NY AM stage B and stage C shares at 20% each. The rest of the queue takes what is left.
2. Within the Asia stage-C head, serve wave 2 and wave 3 rows of books that already survived wave 1 BEFORE new wave-1 rows of weaker books (those are the closest to a verdict), then wave 1 in the written order.
3. LEAD: post the new expected time for "Asia wave 1 empty" and for "Asia pool complete", and the measured cost to NY AM.
4. W-BRKT: the stage counter says 15 Asia books passed (d) but only 12 "PASS (d)" lines are on the page. Post the missing lines (or say what the other 3 are, e.g. twins).
5. Reminder (the relay loses its order channel at about 03:00Z): the lead keeps managing these shares by its own judgment through the night with the same priority, Asia pool first, NY AM second.
