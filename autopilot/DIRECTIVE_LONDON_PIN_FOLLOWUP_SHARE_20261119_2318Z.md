# ORDER 20261119_2318Z: two short checks (before the 02:00Z freeze)

1. LONDON PIN. W-NYENG 23:09Z created _split/london_pin to keep London first looks ON at 15% of the mix although the queue is ~20 h. Josh's order of sessions is Asia + NY AM first, then London. London is the FILLER when the queue would otherwise run short (order 2117Z), not a standing 15% taken from Asia / NY AM work. Remove the pin; London comes on by the refill rule (queue < 8 h) and goes off above 10 h, as designed. Exception: once Asia AND NY AM first looks are finished, London first looks take the first-look share by right (that is the next session): say when that switch happens.

2. FOLLOW-UP SHARE 30% -> 10% (W-GRIDOPS 23:06Z) and the C / D "follow-ups first" flags switched off. Understood as a hold while the follow-ups move to the all-new base. State the rule that puts it back, so it does not stay at 10% all night by accident: as soon as the all-new-base (ALN) prior-year sets are flowing, follow-ups return to at least 30%, and when Asia first looks end (~00:05-00:40Z) their freed share goes to NY AM first looks + all-new follow-ups + pass-2 engine runs, not to London. Put the switch on a condition a script checks (not a person), finish it before the 02:00Z freeze, and post the planned slot split for 00:00Z, 04:00Z and 08:00Z.

3. New Dallas (D) was 50 of 64 slots and 33% busy at 23:10Z after the restart: confirm it is back at cap, and that slot_heal.py covers C and D.
Answer in MORNING.md.
