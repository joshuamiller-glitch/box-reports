# Order 0532Z Sun Nov 22 — from Josh (quoted), with the relay's reading marked "(relay)"

Josh, 05:25Z: "then you can code d8 asia and maybe NY am?"
Josh, 05:28Z: "yes we can launch D8 asia on SiM with NY AM or with 1 lot live"
Josh, 05:30Z: "ok you can reach MAC now - order what you need to"

(relay) Josh wants D8 Asia coded and launched as soon as it is ready (SIM, or 1 lot live), with NY AM alongside if ready. The relay codes it from D8_BUILD_SPEC.md. His standing rules still hold: nothing in D8 without the exit run; fits before the build; code exactly as tested; never compare bare D8 with fitted D7. Nothing below is a new kind of test: it is the fit, the exit run and the spec he already ordered, started NOW on the current stacks instead of waiting for the complete pool. The relay's channel may drop again at any time, so make every item self-running.

## 1. Fit the current stacks now (W-LAYERS)
Note #24 says the stack-rule fit class is empty. Do not wait for the complete pool or for a loop to post FINAL.
a. Register and fit NOW (stack rules [stack cut, book lock, daily caps] + daily profit/loss stop, joint, with the truly bare R0 reference row) the current state of the weighted Asia stack asia-own-w: Lb0e6dfa3.BRF40_80 x1 + L385f4f2e.J502 x1 + L92a90948 x1 + L6b373671.BRP60 x1 + L578701ed.BRF30_90 x1 (step 5, 05:03Z).
b. Same for the NY AM provisional FINAL (Le4fede95.BRF90_30 + B7bfd33b7) and for each later NY AM / London / NY PM stack as it reaches 2+ books.
c. When a stack gains or changes a member, re-fit on the new stack (reuse landed rows, mark the old one SUPERSEDED). The last fit on the complete pool is the real one; earlier ones are PROVISIONAL and say so.
d. Because the weighted runs are x4 lots and not lot-linear: also run the current asia-own-w stack once at 1 lot per book (R1) and once truly bare (R0), and post those rows beside the x4 row. The build will run at 1 lot.

## 2. Exit run on the stack members at their new brackets (owner of the exit engine; LEAD assign)
Josh's rule: nothing goes into D8 without the non-fixed exit run. The exit queue has been starved all day (701 old lines, by design). Run the exit menu NOW on the five asia-own-w members and the NY AM stack members at their new brackets, bare, then on the stack. Post verdicts per book and for the stack (fixed bracket vs best exit, same gates as before). Then follow the stacks automatically: any book that enters a stack gets its exit run without an order.

## 3. Build spec for the relay (W-D8SPEC), D8_BUILD_SPEC.md AUTO blocks, today
One block per stack member, Asia first, then NY AM: Lb0e6dfa3, L385f4f2e + J502 filter, L92a90948 (not in the spec at all yet), L6b373671, L578701ed, Le4fede95, B7bfd33b7. Each block, exactly as the engine runs it:
a. bar type and every bar parameter (tm240 anchor time and time zone; frenko_40 brick rule and reversal; swing_atr_0.4; pnf; time_m_1), session window, days;
b. trigger rule with every parameter and warm-up length, entry order type and price, one-position rules, re-entry rules;
c. bracket (stop/target in points, or the unit rule for S8U-type shapes with its clip), the scheduled session-end exit time;
d. any filter (J502: its exact rule and inputs);
e. data the book needs beyond NQ trades (L2 depth, other symbols, tape/block prints);
f. a parity pack for two trading days (20261110 and one day in late October): the bar list (time, O, H, L, C, volume) and the signal/trade list (time, side, entry, exit, reason) per book, as CSV in the mirror, so the relay can check its code bar for bar and trade for trade.
g. the stack-level rules as fitted (item 1) and the sizes; mark each line SPEC (engine code) or OPEN.
Update the blocks by themselves when the stack or the fit changes.

## 4. Order of work and slots (LEAD)
Items 1 and 2 are small. Give them first call with the stack-search rows (inside the existing chain/stack shares; raise the stack-fit share if they wait). Asia first, NY AM second. London and NY PM keep their shares.

## 5. Report
One "LEAD TO JOSH" line when each lands: fit verdict (provisional/real), exit verdict, spec blocks ready. Reply to this order with one line per item and an expected time for each.
