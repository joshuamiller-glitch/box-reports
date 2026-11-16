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
