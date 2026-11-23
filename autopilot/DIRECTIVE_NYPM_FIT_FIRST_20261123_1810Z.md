# PRIORITY (research queue order only): NY PM 2-lot joint fit first, keys page at the verdict
**Josh's words are quoted; lines marked (relay) are the relay's reading. No new test, no gate or rule change, no spend, nothing live, no data deleted.**

Josh, 23 Nov 11:04 MT: "the NY PM fit is more important espeically if the NP ATR trades a ton"
Context (relay): NY PM is trading live bare today; L52359bf4 (the ATR fade book) trades about 8 times an afternoon with nothing limiting a bad day. Josh takes one final D8 file before Globex opens tonight; the relay must send it by 22:00Z.

## Do (relay)
1. Rank the NY PM 2-lot joint (STKd893133bd8, BF2) ahead of everything except rows already leased. If the Asia 2-lot re-run is not finished, NY PM goes level with it, not behind it. Time windows, session-end, carry-over, nulls and first looks stay behind.
2. The moment the NY PM verdict exists, post in the same hour (do not wait for the null):
   - `autopilot/D8_LAYER_KEYS_NYPM.md`: every code of the 2-lot pick resolved per book (L52359bf4, L8e0bf58c, L4bdd521a, L2c6916a5) exactly as the NY AM keys page did, with the hook order and any rule the D8 file does not have yet spelled out from the code.
   - `autopilot/D8_LAYER_DEFAULTS_NYPM.md`: the panel values at the 2-lot pick; say which parts need the cancel tape (STC) and give the STC-free pick beside it.
   - Daily-loss / losing-streak rules for NY PM: say whether the NY PM joint includes the DL families (DLA / DLB / DLC) as the NY AM one did. If not, say so plainly and give the count and ETA to add them.
3. One line in MORNING.md with the new ETA of the NY PM verdict.

Machines stay full. Nothing else changes.
