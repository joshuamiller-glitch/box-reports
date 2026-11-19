# ORDER 20261119_2117Z: keep six machines fed overnight + scorecard labels

## 1. Engine queue is draining faster than it is filled
HEALTH 21:10Z: 52,342 lines pending at 7,862 set-months/h = 6.7 h (rule of thumb: >= 12 h per machine with no decision needed). Server D joins soon and adds more. Josh sleeps tonight; nobody will be there to refill.
- State where the next work comes from and make it automatic: (a) the ~30,700 Asia lines appended as cells pass stage A; (b) the ~81,000 follow-up set-months for the top 50 per session (prior years + 30 controls + layers): how many of these are in a queue file NOW vs waiting on a script that only queues when something else completes? (c) per-book exit runs after the both-side screen (~22:00Z); (d) pass 2 after first looks.
- If (a)-(d) together do not keep every machine >= 12 h fed at the six-machine rate, extend the ranked follow-ups automatically down the own-merit list beyond rank 50 (rank order, no cap on survivors: standing order), then London first looks. First looks keep their share until they finish.
- Add a guard alert when the shared engine queue falls under 6 h at the measured fleet rate, and have the supervisor refill from the ranked list without waiting for the lead.
- Post one line: queue hours now, queue hours expected at 00:00Z, 04:00Z and 08:00Z.

## 2. Server C at 82-88% busy (Rule A flags it)
99-114 engine jobs leave 12-18% of its threads idle. Finish the cap test and set the cap where throughput is highest (report set-months/h at each step). Same for Server D when it is registered. C and D have no grid workers, so their caps can differ from A/B.

## 3. Scorecard "what it is" column (BEST_BOOKS_ASIA / NYAM): Josh reads it on a phone
- Bar labels are ambiguous: "time_m_3 (m_3-second time bars)" vs "tm180". Say exactly what each is (3 minutes? 180 seconds?) and print one consistent plain form, e.g. "time bar 3 min".
- Give plain-English names + the unit of the size number for every bar code in the tables: cdr, vrb, vsess, dlt, dib, tib, trb, drb, dol, mom, rng, lbrk, urenko, wrenko, frenko, cusum (e.g. "vsess 30 = ... bars per session").
- Add per bar type the average number of bars per hour in each session (Asia, NY AM). Josh runs his strategy from the Strategies tab and needs to know the processing load of fast bars before anything is built.

## 4. Prior-year colour on the scorecards
At 20:37Z, 21 of the Asia top 50 have prior years landed and ALL 21 are RED against their own recent level; all five live Asia books are RED on the same measure. A rule that marks everything red separates nothing.
- Beside the colour, keep showing the absolute prior-year $/week and ulcer (already there), and add a summary line per session: of the top 200, how many are GREEN / AMBER / RED / not landed, and how many prior years are positive in absolute terms (0, 1, 2, 3 of 3).
- Do NOT change the rule or any label on your own. This is a report so Josh can decide whether the own-level comparison is the right reading of his "prior years: not a disaster (within 15-30%)" rule.

## 5. Stale-result fix (W-EXITENG 21:08Z)
Noted: STATUS 25 retracted; dispatchers pull back an old run dir instead of computing. After the move of stale run dirs on all hosts, prove one real re-run: lease host, start time after the freeze, run time of minutes not seconds, code_hash.json matching the frozen hash. Then give the verdict on the L01811caa exit result. Also say whether the same pull-back-instead-of-compute behaviour can affect ANY other re-queued set outside the exit stage (parked duplicate streams, twin parks, add-on parks, anything re-run after a code fix): if a result can come back from an old run dir, list which programmes are exposed.

Answer in MORNING.md.
