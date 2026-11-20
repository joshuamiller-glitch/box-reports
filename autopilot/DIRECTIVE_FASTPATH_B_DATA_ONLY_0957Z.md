# ORDER 20261120_0957Z: fast path for the B-id first looks: the data-only step, by the standard procedure (no code change)

Lead 09:39Z: identity (fast vs production exact) passed 10/10 over 10 books for the B-id RK7 first looks and 10/10 for the P2J kinds; the change set was held because it also touched code (fl_autonew). NY AM first looks now finish ~13:00Z at ~380 s per job; London waits on them.

1. Split the change. Do ONLY the data step that W-FASTLADDER has done for every cleared kind before: add the B-id RK7 first-look kind (and the P2J kinds, if 10/10 stands) to the fast-kind list by the usual tooling / list file, sync to the hosts, no .py file edited. This is the established cleared-kind procedure (identity >= 6 identical across >= 2 books; you have 10 across 10), and a queue/list change is inside the freeze rules.
2. Watch 20 minutes: pair-check the first 10 fast results against exact; ANY mismatch => remove the kind at once and re-run what landed fast. Post before / after: seconds per job, B first looks per hour, new NY AM finish time and London start time.
3. The fl_autonew code fix (pandas path, B-id pattern) stays for 14:00Z.
4. If your harness refuses the step, do NOT work around it: hold it for Josh and say so in one line.
C/D follow-ups-first stays as it is: Josh's question.
Answer in MORNING.md.
