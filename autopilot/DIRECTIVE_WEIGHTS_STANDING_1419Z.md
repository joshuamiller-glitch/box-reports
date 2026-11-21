# Order 1419Z Sat Nov 21 — follow-up to 1416Z; Josh's question quoted, the rest written by the relay (Claude)

Josh's words (14:17Z): "we have a ton of asia and NY books still in queue. The same thing will apply to them?"

Relay's reading: the weights work approved in order 1416Z ("yes both") must be STANDING, not a one-off on today's options. No new test beyond 1416Z; this only makes it automatic.

1. PART 2 (weighted add rule): the "-w" loops read the pool key every pass like the existing loops, so every book that enters the Asia or NY AM pool later (the 48 waiting for controls, the 127 waiting for prior years, the 712 without a _CANC base, the Asia widening, the NY AM all-new) is tried at sizes 0.25 / 0.5 / 1 / 2 automatically. Confirm that in W-COMBO's 5-line plan.
2. PART 1 (weight search on a fixed set of books): re-run it automatically whenever a FINAL (equal-weight or weighted) of any Asia or NY AM loop changes membership, on the new member set, and refresh WEIGHTS_ASIA.md / WEIGHTS_NYAM.md with the time and pool hash. Same gates as 1416Z.
3. Same for London and NY PM when their stacks are built: the weighted loop is the default from the start; the equal-weight loop stays as the reference row.
4. Every later FINAL line shows weights. A FINAL without weights is a reference row.
