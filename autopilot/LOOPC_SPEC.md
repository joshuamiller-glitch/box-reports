# LOOPC_SPEC - the learned loss-side management loop (Loop C) for the NT8 build (W-DYNA; models W-DYNML code/th_dynml; hook W-DYNH code/th_dynexit/dx_algo.py)

Version 0.1, 2026-11-27 15:35Z. Keys-page standard: SPEC = read from code (file named), READING = my reading of how the hook/engine passes the value, OPEN = not decided / owner named. Companion pages: LOOPC_MODEL_<book>.md (model files), LOOPC_MATCH_<book>.md (3 trades per book with raw per-second prices, per-minute features, predictions; Asia MF1 first), ALGO_SPEC.md (whole algo), ALGO_LOG.md (versions). Research only.

## 0. WHAT LOOP C IS
```
purpose       = LOSS SIDE: once per trade-minute, while the trade is under water, choose among take-all / tighten / part / trail the action whose predicted advantage over simply HOLDING (with the safety stop only) exceeds theta; else hold   (SPEC: algo_hook_c.py docstring and decide())
state at entry = the book's live entry; NO fixed target; only the SAFETY STOP 1.5 x R0 from the entry fill (R0 = the book's own stop in points)   (SPEC: dml_algo_ds.py S = 1.5*R0)
models        = four LightGBM regressors per (book, refit period), one per action; target = (value of the action - value of holding) / R0, clipped to +-3   (SPEC: dml_algo_ds.py labels, dml_algo_fit.py fit)
```
Value definitions of the training labels (per lot, points, round-trip fee excluded, all on the 1-s NQ series instr_1s NQ_SS/SC/SH/SL):
```
entry reference e  = first 1-s close at/after the entry second + side*0.25 (one tick adverse)
V_hold   = if the safety stop (-1.5*R0 from e, touched by the 1-s HIGH/LOW) is hit: -1.5*R0 - 0.25 ; else (close at the session end - e)*side - 0.25   [session end = the bell of the live session; see d]
V_all    = open_pts_now - 0.25 (market, one tick slip)
V_tight  = stop moved to max(-1.5*R0, open_pts_now - 0.5*R0) then hold: stopped there at that level - 0.25, else as V_hold
V_part   = 0.5*V_all + 0.5*V_hold
V_trail  = trailing stop R0 behind the running best (1-s high for a long), never below -1.5*R0, from now on: stopped at the trail level - 0.25, else close at the session end - 0.25
```

## a. FEATURES (model order; 18 values x[0..17]; indices into the trees' "f")
```
 idx name   formula                                                                                      unit / side adjustment                       status
 0   openR  side*(P_now - entry)/R0 ; P_now = last NQ price at the decision second                          R0 units; positive = in profit               SPEC: dml_algo_ds.py o_f; hook (READING): st.openR*1.5 where st.openR is in safety-risk units
 1   mfeR   max over the trade so far of the favourable excursion (long: 1-s bar HIGH - e; short: e - 1-s bar LOW) / R0   R0 units, >= first-second value   SPEC (training). hook READING: engine best_R*1.5, best of the engine's prices (closes); OPEN: W-DYNML/W-DYNH to say which (highs vs prints); my match rows use per-second CLOSES
 2   maeR   min over the trade so far of the adverse excursion (long: LOW - e; short: e - HIGH) / R0         R0 units, <= 0                               SPEC (training); hook READING: -|worst_R|*1.5, same OPEN as mfeR
 3   sec    integer seconds since the entry second (decision second - entry second); multiple of 60 at the first call of each minute within one second of it   seconds    SPEC
 4   R0pts  the book's own stop distance in points (Asia MF1 40, NY AM see MANIFEST S0)                      points                                        SPEC (static per book)
 5   hod    ET clock of the ENTRY minute (the hook uses key = decision second - int(minutes*60) = entry second) minus 18 hours: hour + minute/60, i.e. 0.0 = 18:00 ET, 2.53 = 20:32 ET, 15.5 = 09:30 ET   hours   SPEC (hook _hod); constant for the whole trade
 6   nq60   side*(NQ_now - NQ_{60 s ago})/R0                                                                 R0 units
 7   nq300  same with 300 s
 8   nq900  same with 900 s
 9   ES60   side*1e4*(ES_now/ES_{60 s ago} - 1)                                                             basis points
10   ES300  same with 300 s
11   RTY60  side*1e4*(RTY_now/RTY_{60 s ago} - 1)
12   RTY300
13   CL60   side*1e4*(CL_now/CL_{60 s ago} - 1)
14   CL300
15   ZN60   side*1e4*(ZN_now/ZN_{60 s ago} - 1)
16   ZN300
17   gap    side*1e4*(ES_now/ES_300 - NQ_now/NQ_300) (= ES300 - NQ300 in bp, with NQ in relative terms, not R0)   basis points
```
series/basis (SPEC dml_algo_fit.py look(); hook READING): the 1-s bar series /mnt/l2/l2vast/instr_1s/<SYM>_SS.npy (epoch second of the bar START) and _SC.npy (bar close) for NQ ES RTY CL ZN; value at time T = close of the last bar with start <= T - lag - 1 (hook, lag 1 s: 'a bar is known at its start + 1 s' plus 1 s feed lag; training used bar start <= T, up to 1 s more recent: OPEN: W-DYNML to align training and hook; the difference is at most one bar); value 'N s ago' = same rule at T - N. If the last bar is older than 6 hours or does not exist: NaN. A second with no trade has no bar: the previous close is used (stale value), exactly like a 1-second series that only prints when a trade occurs.
missing values: NaN stays NaN; the trees route NaN by their missing_type/default direction (section f). No fill value, no clipping of features (only the training target is clipped to +-3).
contract / roll: OPEN (W-DYNX8: how instr_1s joins front contracts for NQ/ES/RTY/CL/ZN; the NT8 side must use the same front-month rule). Returns across a roll day would be wrong without an adjustment: OPEN.
FINAL FEATURE LIST: the hook-feature models use exactly these 18; the research models also had time-to-session-end, HAR/R0, ATR/R0, previous-session ER (dml_algo_fit.py columns 4, 6, 7, 9): DROPPED in the hook models (dml_algo_hookfit.py HK indices [0,1,2,3,5,8,10..21]); NO flow/book/L3 feature in this version.

## b. DECISION SCHEDULE
```
unit               = trade-minute counted from the ENTRY FILL second (hook: st['mins'] = (now - entry fill time)/60)                                READING
evaluation         = at the FIRST engine call (the hook runs at most once per second and on every print) with int(mins) > last evaluated minute; minute 0 is never evaluated; minute k is the first second with now - entry >= 60*k
first decision     = minute 1 (60 s after the fill); last = the last minute before the exit / the bell
loss-mode gate     = under water means open_pts < 0 strictly, open_pts = side*(P_now - entry fill price) at the evaluation second (the engine's current print); if open_pts >= 0 the loop returns HOLD without evaluating the models, and that minute IS consumed (the minute counter is set before the gate)   SPEC algo_hook_c.py
which models       = the period of the bundle whose [t0, t1) contains the decision second; after the last period the last model is reused; before the first: HOLD
exact order        = gate -> period -> features x -> four predictions -> best allowed action above theta
```
## c. ACTIONS
```
theta              = 0.2 R0 (R0 units: advantage, not safety units), the same for every book in the bundle config; OPEN: per-book theta
choice             = the action with the largest predicted advantage that is strictly > theta and ALLOWED; an equal value does not displace an earlier action (strict >); order of evaluation: take-all, tighten, part, trail
allowed            = tighten only if (open_pts - 0.5*R0) is beyond the current stop (stop moves toward price); part only if lots >= 2 and nothing parted yet; trail only if no trail yet in this trade; take-all always
take-all (action 'all')   = market exit of the whole position, state OUT, reason 'LOOP C adv ..'                                    engine: request_exit 'ExAlgoAll'
tighten  ('tighten')      = stop to entry + side*(open_pts - 0.5*R0) i.e. 0.5 R0 behind the current price, R0 = own stop (NOT the 1.5x safety); price not rounded by the loop: the engine ratchets only if the new stop is at least 0.25 pt (one tick) better than the current stop, rounding via the engine's tick rounding (SIM.rt, READING); if the price is already through the level the position is exited at market ('ExAlgoStop'); may repeat in later minutes (each time a new best level)
part     ('part')         = frac 0.5: qty = int(round(0.5*lots)) with Python rounding to even: 2 lots -> 1, 3 -> 2, 4 -> 2, 5 -> 2, 6 -> 3; never the whole position; market; at most once per trade (READING dx_algo.py: q >= 1 and pos > q)
trail    ('trail')        = k_R = R0/risk0 = 0.667 of the safety risk = trail distance R0 behind the best price, persistent chandelier-like trail ratcheting at every print (resting stop), only once; the safety stop stays until the trail passes it
repeat             = take-all ends the trade; tighten and part obey the allowed tests above and are re-evaluated every minute; trail once
```
## d. SAFETY STOP, FLAT, BELL
```
safety stop        = 1.5 x R0 from the entry FILL price (stop-market resting from the fill, hook/events: stop_pts = 1.5*R0, target none), never widened; order type stop-market (engine: resting stop with the engine's slippage/fill model)   SPEC order 13:05Z / dx_algo.py; READING for order type
hard flat          = 16:55 ET for everything (order 13:07Z)   SPEC (order)
the bell           = the training labels hold to the live SESSION END (gcore2.sess_end_fast: Asia 02:00 ET, NY AM 12:00, London 08:30, NY PM 16:00): the models never saw a carry past the bell. What replaces the bell flatten in the live algo is OPEN (ALGO_SPEC section 0; carry replay in EXIT_ANATOMY.md); until decided the loop runs to the bell and the position is flattened there as today
```
## e. RE-ENTRY
OPEN: no re-entry is part of Loop C v0 (rows L0-L3 not run). After a take-all the book's slot is free; the entry rule of the book can fire again as usual.
## f. MODEL FORMAT (SPEC)
```
library            = LightGBM LGBMRegressor(n_estimators=60, learning_rate=0.1, num_leaves=15, min_child_samples=300, subsample=0.7, subsample_freq=1, colsample_bytree=0.7, reg_lambda=10.0, max_bin=63, n_jobs=1); init score 0.0 (stored as "init"); the model is dumped with booster_.dump_model() and compiled by loopc_trees.compile_model
file               = json.gz, {"tag","step","feats":[18 names],"safety_mult":1.5,"periods":[{"wk0","wk1","t0","t1","fit_end","n_fit_signals","models":[{"init":0.0,"trees":[...60 trees...]} x4 (take-all, tighten, part, trail)]}]}
tree (arrays by node number, root 0) = {"f":[feature index, -1 for a leaf], "t":[threshold], "l":[left child], "r":[right child], "d":[default-left 0/1], "m":[missing type 0 None, 1 Zero, 2 NaN], "v":[leaf value]}
prediction         = init + sum over the 60 trees of the leaf value reached. Walk (identity-tested against lightgbm, dml_algo_hookfit.py):
                     i = 0; while f[i] >= 0: v = x[f[i]]
                        if v is NaN: go_left = (d[i] == 1) if m[i] == 2 else (0.0 <= t[i])
                        elif m[i] == 1 and |v| <= 1e-35: go_left = (d[i] == 1)
                        else: go_left = (v <= t[i])
                        i = l[i] if go_left else r[i]
                     pred += v_leaf[i]
training window    = rows are 1-minute states of past trades of the book at the same session; fit set = trades that ENDED before fit_end (= the decision date minus one day: purge), at most 104 weeks back, at most 150,000 rows (even subsampling), at least 150 distinct trades; period = the next step weeks (4 or 13) after t0; refit = new period with a new model
the bundle that would run TODAY = the LAST period of the bundle of the chosen step (s13: t0 2026-06-28; s4: t0 2026-08-30 for Asia MF1; fit_end the day before): a model is reused after its period ends, so a live build must add a refit period every step weeks (a bundle built with W-DYNML's dml_algo_hookfit.py and the new data). LOOPC_MODEL_AS_MF1.md carries both one-period bundles with sha256 = the version hash.
```
## g. LIVE-FEASIBILITY NOTE (from NT8 data series NQ, ES, RTY, CL, ZN ticks and the clock)
```
computable live       = all 18 features: 1-second price series of NQ (trades), ES, RTY, CL, ZN (NT8 Second bars: a bar exists only for seconds with a trade, which matches the instr_1s semantics, close = last trade of the second), the clock in ET, the entry fill and R0
needs care            = (1) mfeR/maeR use the 1-s HIGH/LOW of NQ (training) - NT8 Second bar high/low gives the same; (2) the 1-s lag: use the last COMPLETED second; (3) front-contract roll rule for the five series (OPEN); (4) ES/RTY/CL/ZN subscriptions on the same connection as NQ and their 1-s bars at the decision second: if one is missing the feature is NaN and the trees use the default direction - a mismatch with training is possible (a quantity worth testing: feeds missing at random); (5) the session clock for hod: Globex day = ET 18:00 - 18:00; (6) price source in training = instr_1s trades-based closes, in the engine = prints
not computable live  = nothing among the 18; time-to-session-end, HAR/ATR/prior-session (dropped from the hook models) would also be computable from the same data.
exact-engine caveat   = the hook-fit models were scored on a QUICK SCREEN (per-second replay on NQ 1-s series); the exact-engine verdict with the live mix and Trade Health is W-DYNH/W-DYNML's open row. These pages specify the model, not a verdict.
```
## h. OPEN LIST (owner)
```
mfeR/maeR definition in the hook (highs/lows vs prints), training vs hook 1-s lag alignment       W-DYNML + W-DYNH
roll rule of the five series in instr_1s                                                           W-DYNX8
exact-engine action logs for the match trades (engine_* columns of LOOPC_MATCH)                    W-DYNH
bundle cell id per book beyond Asia MF1 (MODEL/MATCH pages for the other books)                    W-DYNML
what replaces the bell flatten; re-entry rows; per-book theta                                      lead / W-DYNML
```
