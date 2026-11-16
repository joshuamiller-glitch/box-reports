# USER ORDER 2026-11-16 (verbatim): T-BRACKET-DD (replaces the remainder of P2; finish only U7 Asia 40x40 through all windows with controls). Research only, guard rails apply.
Base TL3_EV_JN05W2JL2 ONLY. Objective is DRAWDOWN: rank by max DD and worst week over the full 43 months AND inside the HOLD path 2025-11-17..12-10, subject to mean $/wk not more than 5% below the reference. L3M alone never ranks anything. Every candidate: 3 placebos + 3 matched random controls, W44-removed row, $4.84 column, lots held at live values AND constant-risk (lots x baseStop/newStop) shown side by side.

A. FULL GRID PER BOOK x SESSION (all 7 books, all sessions they trade): target 30,40,50,58,70,85,100,120 x stop 40,50,60,75,90. Report the DD surface, not one winner: a cell counts only if its neighbours agree.
B. TARGET BY DIRECTION OF THE DAY (the HOLD path lost 53.5k on trades against the day direction). Day direction known causally at entry: sign of (price - session open), (price - 18:00 ET open), price vs session VWAP, 60-min slope; each alone and 3-of-4 vote. WITH the day: target 58, 85, 120, trail. AGAINST the day: target 20, 30, 40, and size x0.5, and skip (vs engine random skip).
C. TARGET BY ROOM: target = min(58, k x distance to the nearest of prior day high/low, overnight high/low, session high/low, VWAP band 2) for k 0.6, 0.8, 1.0; and target = k x forecast remaining range (HAR), k 0.5, 0.75, 1.0, floor 20. Never a target beyond the forecast.
D. PARTIAL EXITS: half off at 20, 30, 40 pts, remainder to 58 / 85 / trail (trail 15, 20, 30 pts or Keltner mid); stop to breakeven after the partial yes/no.
E. TIME: target steps down to 40 then 25 if not reached after 15, 30, 60 min; time stop at 30, 60, 90 min when below +5 pts.
F. BY VOLATILITY STATE at entry (atr_rel thirds, squeeze on/off 5-min): best target per state from A, walk-forward (pick on trailing 26 weeks, apply next 2), against the same procedure with shuffled state labels.
G. JOINT: best survivor of B-F per book combined, with the interaction table, drawdown first.

ORDER OF WORK: B first (all workers), then D, C, E, A, F, G. Other tags stay at quota 0 except FL 4 and CF 4. Page DS3_BRACKET_DD.md, rebuilt after each part; each row says passes / fails / not finished, and no row is called a lead until its controls are in. Lead notes at 17:00Z, 20:00Z, 23:00Z with what passed.
Also approved: buy the NQ MBO night 2026-11-15 00:00Z to 11-16 07:00Z (quoted $0.00, 0.43 GB).

# ADDENDUM (deadline: build installs before 23:00Z)
1. Run Part B and Part D in parallel from the start (half the workers each), windows in this order: HOLD, L6M, L3M, then GAP, PRE, X'. Controls run alongside the real cells, not after.
2. At 19:00Z and 21:00Z write DS3_BRACKET_DD_BUILD.md: for every candidate that beats all its controls on drawdown in HOLD and L6M and is not worse than -5% on mean: the exact rule as the engine applied it (every constant, how day direction is computed, at what second, from which bars), the policy-file line or the code change needed in DS7.cs, and 3 worked examples with timestamps. If nothing qualifies, say so plainly.
3. Do not relax the pass rule to meet the deadline. A candidate with controls missing is listed as "not finished", never as passing.

# ADDENDUM 2 (user 11-16, ~15:35Z, verbatim)
run M7 cap. RA quota 2 for TL3_RA_JL2_M7L_CAP3 + PL1-3 only, HOLD and L6M first, then L3M, GAP, PRE, X'. Report in DS3_BRACKET_DD_BUILD.md at 19:00Z and 21:00Z beside the bracket candidates, drawdown first.
Also: re-run every skip-type control in the programme with the persistent draw (bucket=300) before any skip rule is called a lead again, and list which earlier "beats random" statements are now void.

# ORDER 3: TARGETS BEFORE GLOBEX (user 11-16, ~16:00Z, verbatim). Overrides the pass rule of T-BRACKET-DD for the 21:00Z deliverable.
The user will not run a fixed 58 target tonight. "Keep 58" and "nothing qualifies" are NOT deliverables: deliver the best non-fixed target setting per book x session with its evidence, and the user decides.

STEP 1 (now, no engine workers, due 17:30Z): FAST REPLAY on the JL2 trade list, all 43 months, 1-s paths, each trade's real entry and real exit kept (cuts, takes, locks as they happened). For each alternative, exit = the earlier of (alternative fires) and (the real exit). Per book x session:
 a. fixed target 20,25,30,35,40,45,50
 b. half off at 15,20,25,30,40; remainder to the real exit; stop to breakeven after the partial yes/no
 c. target steps down: 58 -> 40 -> 25 after 10,15,30,60 min
 d. target by day direction (3-of-4 vote as defined in DS3_BRACKET_DD.md): AGAINST the day 20,25,30,40; WITH the day unchanged
 e. target = k x remaining forecast range (HAR), k 0.5,0.75,1.0, floor 20
 f. target by atr_rel third and by squeeze on/off (5-min)
 g. trail: after +20/+30 trail 15/20/30 behind the extreme
Report per cell: max DD, worst week, HOLD-path DD (2025-11-17..12-10), mean $/wk, vs the same trades at 58; by year; L6M and HOLD separately. State that replay ignores freed-book re-entries.

STEP 2 (engine, all D10 + BD workers, due 20:30Z): the top 2 settings per book x session from Step 1 by drawdown, on JL2, HOLD and L6M first, with controls using the persistent draw. Then L3M, GAP, PRE, X'.

STEP 3 (21:00Z, DS3_BRACKET_DD_BUILD.md): one row per book x session: the recommended target rule, replay numbers, engine numbers where done, controls where done, and a label: CONFIRMED (engine + controls), ENGINE ONLY, or REPLAY ONLY. Give each rule as a policy-file line where the grammar allows (bracket <book> <session> <conds> target=), else the exact code change with every constant and 3 worked examples.
Keep RA quota 2 for the M7 London cap 3 cells on JL2.

# ADDENDUM 2 to TARGETS BEFORE GLOBEX (user 11-16, ~16:05Z, verbatim): the target must be DYNAMIC. Session is a reporting cut only. Add to Step 1 (replay, same deadline) and carry the best into Step 2:
 h. STRUCTURE targets: exit at the first of prior-day high/low, overnight high/low, session high/low, session VWAP and its 1/2-sigma bands, prior swing (5-min, strength 2), round 50s, when that level lies between +15 and +58; variants: exit AT the level, 2 pts before it, or half off at the level and trail the rest.
 i. IN-TRADE EXIT from the book and tape (owned MBO, clean replica): once the trade is at +10 / +15 / +20 or better, exit when
    - a resting level >= 3x / 5x MedLevel sits within 8 ticks ahead
    - aggressor delta against the trade over 5 / 10 / 30 s >= 5x / 10x
    - no new favourable extreme for 30 / 60 / 120 s
    - own-side support pulled >= 5x / 10x over 5 s
    each alone and any-2-of-4.
 j. IN-TRADE EXIT from other markets: ES / RTY / NKD turning against the trade over 1 / 5 min while NQ is at +15 or better (the AL hold/cut lead, applied to winners).
 k. GIVE-BACK rule: exit when the trade has given back 40% / 50% / 60% of its best open profit, once best >= 20 / 30 / 40.
Rank h-k against a-g in the same table, drawdown first. In Step 3 give one rule per BOOK (not per session) wherever one dynamic rule beats the per-session fixed numbers; fall back to per-session only where it does not.
Also report: the live profit-side state lines (K7 delta_mult lock, M7 tot_rel step, U7 delta_mult tighten) were blind in live until 11-16; what do they do on the clean replica for the last 4 weeks?
