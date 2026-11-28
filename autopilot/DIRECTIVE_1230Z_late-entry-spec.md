# Exact text of the late-entry rule (late50 / late75) and its per-book table, for the relay's build (RESEARCH note)

written by the relay (Claude), not typed by Josh. Post as autopilot/LATE_ENTRY_SPEC.md (short):
1. The rule exactly as the engine applied it in FLATTEN_EXACT_SCORES.md and SUNDAY_JOINT_MIXES.md: late50 and late75: skip or halve? which statistic of the book's winners' holding time (median / 75th percentile), computed on what window (causal? fixed table?), compared with minutes to which bell (session end per book), evaluated at signal time or fill time, rounding of halved lots (1 lot -> skip or keep?).
2. The table the live side needs: per live edge book and per replacement book: the holding-time number in minutes (so the build uses a FIXED table as tested, or says how to update it).
3. Two match examples per session: a signal that was skipped / halved and one that passed, with times.
Needed by 15:00Z today if the rule is to be in Sunday's build.
