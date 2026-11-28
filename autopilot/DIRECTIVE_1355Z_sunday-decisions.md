# Josh's decisions for Sunday: lowest-drawdown mix per session; stop-to-entry on Asia and NY PM; Sunday start; backlog stays parked (RESEARCH order)

Josh, typed 13:49Z 28 Nov, verbatim (his answers in capitals after each of the relay's questions):

> 1. Per session: the lowest-drawdown mix or the best-income mix? This settles the drift books. Asia is the same answer either way. LOWEST DD
> 2. The manager: (A) keep brackets, ship what passed, and run the desk in shadow; (B) replay one last, narrower manager; or (C) use size as the smoothing tool. NO IDEA
> 3. Manager switch default: off or shadow? Don't understand. why not on?
> 4. Stop-to-entry at 70% of target: on Asia and NY PM only (Asia +9% income at the same drawdown, NY PM -3%), or nowhere? YES
> 5. Start date: Sunday 6 PM ET with a small v40, or Monday? SUNDAY
> 6. The box's parked backlog (about 380,000 older rows): let it run when the current queue empties, yes or no? NO

(relay) What this means for you:
A. The parked exits-only backlog STAYS PARKED (his "NO").
B. The Sunday build takes the LOWEST-DRAWDOWN row of SUNDAY_JOINT_MIXES.md per session, with your drift set (Asia MF4; London MF2; NY AM MF3 MF6 MF7 MF8 MF9; NY PM MF1 MF4): NY AM drift removed + NY-NODE g67a70; NY PM drift removed + late50; London drift at 1 lot + late75; Asia: the replacement book Ma1 cannot be coded and matched by Sunday, so Asia ships as "drift removed + AS-VWAPBRK tr100" (with or without late50: see C) and Ma1 follows when matched.
C. TOP PRIORITY ROWS (exact, 42 months + L3M / L6M; needed by 20:00Z today), because he said YES to stop-to-entry at 70% on Asia and NY PM and that has NOT been run together with the chosen mixes:
   1. Asia: drift removed + AS-VWAPBRK tr100, with BE70 on AS-NR7 and AS-RSI exactly as in your BE70 session row (say plainly which live profit-side keys BE70 replaced on those books), (a) without late50, (b) with late50.
   2. NY PM: drift removed + late50, with BE70 on the remaining books (NP-ZN, NP-YM), and the same without BE70 beside it.
   3. The exact per-book KEY STRINGS for those rows and for the chosen NY AM and London rows (stop / target / Trade Health keys per book, lots per book at the live session lots 6 / 8 / 6 / 6), in one block "SUNDAY BUILD KEYS" on EXIT_MGMT_SUNDAY.md, so the relay copies them without interpretation.
   If a joint row is WORSE on max drawdown or worst week than the same mix without BE70, say so at the top: the relay will then leave BE70 out of that session and tell him why.
D. Manager: (relay) he left the choice open; the build keeps brackets + what passed; the desk manager does not act on trades. As a last cheap check on spare capacity only (option B): ONE narrower replay, DESK v0.4 = v0.3 with ONLY the ABORT exit on the loss side (no DEFEND half, no clock rule), own target and own stop, same windows and scorecard. Label it post-result change no. 7. Low priority behind C and the proven-book rows.
E. LATE_ENTRY_SEED.md (asked 13:28Z) is now needed for London late75 and NY PM late50 by 18:00Z.
