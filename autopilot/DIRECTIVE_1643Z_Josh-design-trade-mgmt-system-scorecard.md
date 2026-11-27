# Josh: design a sophisticated trade management system; new scorecard for all management work (RESEARCH order)

Josh, typed 16:39Z and 16:41Z 27 Nov, verbatim:

> this is the deal - we know the only thing that seems to work about backtesting with walking forward is bars and triggers that work over long time periods - right? that being said all these intruments and futures watching will probably fail in the same way as it's always changing
>
> so what we need to do is use pure intelligence to build an entry mangement system that does what i'm asking using a ton of available tools - how are we going to test it without the box saying it never works? because the box is looking at income over time and DD and not smoothing returns and we have no idea what the future holds...

> yes go for it - the box is to design a sophisitacted trade managment system that a smart retail trader would do watching the screen using entries and triggers that stand the test of time - that's it

(relay) "yes go for it" approves the test method below, which the relay proposed to him and he accepted. It replaces "does income go up" as the pass rule for ALL trade-management work from now on. Exact engine for every number.

## A. The base
Entries: only books whose bars and triggers stand the test of time (EDGE BEYOND DRIFT, both sides beat random; drift books out). Bare entry. A safety stop at entry. No fixed target.

## B. Two kinds of rule, judged differently
1. POLICY rules (true in any future by construction): e.g. a trade that reached X% of its old target never becomes a full loss; never give back more than Y of the peak; breakeven after Z. These do not have to "beat" anything. Report their PRICE: income given up vs swing removed, per book and per session mix. No pass / fail; a price list.
2. PREDICTION rules (reading other instruments, stocks, flow, book): these can drift, so:
   - DESIGN FIRST, FEW KNOBS. Write the system down the way a skilled discretionary trader watching 15 screens would act, BEFORE running it: e.g. "most of the session's other markets have turned against my trade and NQ has not followed yet -> take part and tighten"; "others have not moved on this dip -> hold"; "range for the session is used up -> stop asking for more"; "liquidity / level just ahead -> take it there". Post the design page (MGMT_DESIGN.md) with every rule in one plain sentence and every knob listed, BEFORE the results.
   - SELF-ADJUSTING MEASURES ONLY: every threshold relative to that instrument's own recent behaviour (moves in units of its own recent volatility, "N of M markets agree", ranks), no fixed point or dollar thresholds, so it adapts as markets change.
   - NO BEST-OF-MANY. At most 3 whole designs (cautious / middle / active), each tested once as written. No grid over thresholds. If a design is changed after seeing results, say so and count it.

## C. The scorecard (smoothness first, income as a floor)
Per book, per session mix, and the whole day:
- worst week; share of winning weeks; standard deviation of weekly income;
- biggest single-trade give-back (peak open profit minus exit) and count of trades giving back > 50% of peak;
- max drawdown; income.
- CONSISTENCY: in how many of the years, and how many of the quarters, is the managed version smoother (worst week AND weekly st.dev.) than the same entries on their fixed bracket? Split NQ-up and NQ-down weeks.
A design is ACCEPTABLE if it is smoother in at least two thirds of quarters, in both up and down weeks, and income stays above the floor. Show the result at three floors: income no more than 10% / 20% / 30% below the fixed bracket. Josh picks the floor; do not pick it for him.
The engine's old findings still count as facts to report (e.g. early exits freeing the slot for extra losing entries): show slot effects explicitly.

## D. Shadow evidence
Every design must be loggable live: one line per decision (time, book, state, which markets agreed, action). The relay builds the shadow logger into the next build; give the log format in MGMT_DESIGN.md.

## E. Order of work
1. MGMT_DESIGN.md (the three designs, plain sentences, knobs): today.
2. Policy price list per book (overlaps the Sunday page; keep that deadline, Sat 28 Nov 16:00Z).
3. The three designs on the exact engine, NY AM and Asia books first, then London, NY PM.
The lead finder from the 16:38Z order feeds step 1 as background only; it does not pick thresholds.
All six servers stay on this. No live or execution-server change. Data spend is Josh's alone to raise with you directly.
