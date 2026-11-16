# SPEC_M7_LONDON_CAP3 - cap of 3 closed M7 trades per London session (W-RA, 2026-11-16)
**One line:** after M7 has closed 3 trades in the London session of a Globex day, drop every later M7 signal of that session. Lead from the exact engine on JN05W2 (old base; JL2 cells prepared, not yet run). Not a PASS.

## 1. Evidence as scored (JN05W2 exact engine, base lots, $1.18/contract RT; live lots x1.75)
- TL3_RA_M7L_CAP3 vs JN05W2, M7 London scope, HOLD (52 weeks): +1,176 $/wk, week-clustered t 2.68, 90% CI +455..+1,888; +1,200 without W44; +710 without the 3 best weeks; M7 London max DD -27.9k -> -13.9k (P shallower in 2000 week-resamples 0.99).
- 7 valid exact random-block placebos (same keep share: realized keep of n>=2 entries 0.53-0.60 vs 0.565 real) give +245..+663 $/wk (mean about +350). The real rule beats the best by about +500 $/wk. Hash-block drawn once per signal second.
- Stack level (all six books capped at 3) gives nothing; the effect is M7 London only. The evidence-based blocks (new extreme, higher low, ...) equal their random placebos.
- L6M effect on trades: 172 of 519 M7 London trades removed, their net -45,835 (base lots): 48 winners, 124 losers. PRE/X'/GAP and the JL2 base are pending (cells prepared).

## 2. Exact rule, every constant (hook code/th_reentry/ra_hooks.py, rule {"k":"capn","books":["M7"],"sess":[1],"N":3})
- **Book:** M7 only.
- **Session instance:** (Globex label day, engine session index 1). Label day = ET calendar date of (time + 6 h) (so 18:00 ET opens the next label day); session index 1 = ET 02:00:00 to 08:29:59 (hm 200 <= hm < 830). Reset: a new label day / the 02:00 ET start of London. Asia (18:00-02:00), pre 08:30-09:30, NY AM, NY PM are not counted and not restricted.
- **What counts as a "close":** every FULL close of an M7 position whose signal time falls in the instance, whatever the exit: Target, StateCut/PolicyCut, EarlyCut, Stop, StopJoin, StopJoinFallback, BookLock, full StackCut, RollFlat. Partial exits (partial target fill, partial StackCut) do not count; L2 adds / slices of a position are part of the same position (one close). Trades are keyed by the session of the ENTRY (a London entry that closes after 08:30 still counts, in London). A close counts for a signal only if its exit time <= the signal time.
- **What is blocked:** at the signal second (try_entry with want != 0, only when M7 is flat: not in trade, not armed for an L2 dip, no entry pending, no exit pending) if the instance already has >= 3 closes, the signal is dropped (logged SKIP). So the 4th and every later M7 London entry of that label day is blocked; the 1st-3rd are untouched. No re-test: a blocked signal is simply gone; the next signal is evaluated the same way (always blocked once closes >= 3, since closes cannot decrease).
- **Open trades:** never touched. An M7 position open when the 3rd close happens cannot exist (M7 holds one position at a time), so the cap only ever stops NEW entries. Stops, cuts, targets, locks of other books and of an M7 position opened before the cap bites are unchanged.
- **Sizing and other layers:** unchanged (LOT, SIGQ, REG, STACK, C22, WL_E1, context cut, K7 flat cut, BookLock). The hook sits outermost after the existing hooks, so the other layers see M7 as if the signal never came.
- **Constants:** N = 3 closes, book M7, session 1 only. Nothing else.

## 3. Worked examples (finished run TL3_RA_M7L_CAP3, L6M, base lots; ET)
First three trades of the day were identical in both runs, the later ones are absent in the cap run.
1. **Kept, 2026-05-05 trade 3:** M7 long 02:36:01 (1 lot) after two StateCut losers (02:00:02 long -644.68, 02:25:01 short -854.68; closes before the signal = 2 < 3) -> allowed, Target 03:42:04, +1,198.82.
2. **Blocked winner, 2026-05-05 trade 4:** signal at 04:11:02 long (2 lots); closes so far = 3 (-644.68, -854.68, +1,198.82) -> dropped. The base run took it and made Target +2,402.64 at 08:10:17. The cap forgoes +2,402.64.
3. **Blocked loser, 2026-05-13 trade 4:** closes before 07:24:01 = 3 (Target +2,397.64 at 03:44, StateCut -1,344.36 at 05:05, StateCut -712.18 at 06:31); the short at 07:24:01 (1 lot) is dropped. The base run took it and lost -832.18 (StateCut 08:03:03). The cap saves -832.18. The 5th trade the same morning (08:18:01 short, Target +1,198.82) is also dropped: that is the price of a blunt count.
Live night 2026-11-13 (hand application on the live CSV, engine not replayed): M7 London took 6 positions; cap 3 blocks positions 4-6 (4: +4,770, 5: -4,680, 6: -435): change +345 on that night; cap 4 +5,115; cap 2 -2,040.

## 4. Live computability (DS7.cs, read from <home>/...)
- DS7 already counts closed trades per book per session instance: `b.CtxTaken` is incremented in V9OnClosed (line ~2145) and reset when `b.CtxKey != key`, where `V9Key(t) = labelDay*10 + SessionIndex(ET hhmm)` (line 2081) - exactly the engine's (label day, session) key. In V9Gate the context tag computes `n = (b.CtxKey == key ? b.CtxTaken : 0) + 1` (line 2096), i.e. n-1 = closes of this book in this session instance.
- **Change needed (small):** one new parameter `M7LondonCapCloses` (int, 0 = off, default 3 when approved) and one line in V9Gate after `n` is computed: `if (M7LondonCapCloses > 0 && b.Tag == "M7" && SessionIndex(ET hhmm of now) == 1 && n - 1 >= M7LondonCapCloses) { V9Say(now, b, Ds7FeatMode.Live, "M7-LONDON-CAP", (n - 1) + " closes this session (cap " + M7LondonCapCloses + ")"); return false; }` using the same skip pattern as DAY-DONE/BREADTH. No new state. Existing `MaxTradesPerSession` is NOT the same: it counts TradesToday per book per whole chart session (resets 18:00 ET) and applies to all sessions, default 0, never scored.
- Policy file: not needed (no policy line is a per-session count); it is an input-parameter change plus the line above. Mode flag Off/Shadow/Live like the other v1.9 layers is advisable (Shadow logs "would be skipped").
- Differences live vs engine to check on the first Shadow week: CtxTaken counts closes via V9OnClosed (a position closed by a roll flatten or manual flat also counts there? verify); adds/slices are one position in both.

## 5. Open points (not claimed)
- Base: results are on JN05W2 (old base); the live-equivalent base TL3_EV_JN05W2JL2 cells TL3_RA_JL2_M7L_CAP3 and 3 valid M7-London-restricted placebo seeds (same draw design, p 0.703) are built and ready: `python3 code/th_reentry/ra_jl2.py start` queues them (43 months, all six windows) when RA quota is restored. Realized keep share of each placebo is re-measured against the real cell; > 0.05 apart = INVALID CONTROL.
- One search family, 52-week horizon; PRE/X'/GAP not yet scored for this cell; overlap with the London range-used-up rule (W-LR LS125 also removes late M7 London entries) is untested jointly.
