# T-FIND (user, 2026-11-05 21:15Z) -- find what each instrument actually does, then build the book that fits it
All cores; supersedes the remaining T-INSTR-2 generic grids once their current stage finishes. Standing rule and LOAD RULE apply (zero workers = failure state). Addendum A native books fold into Step 2 as candidates where the map supports them.
User: "you are looking for trend setups on instruments that are range instruments -- there are ES setups that work, RTY setups that work -- order a study that finds things." Do not start from a list of shapes. Start from the instrument's behaviour, measured, and let the book follow.

## Step 1 -- Character map per instrument (ES, RTY, YM, GC, CL, ZN, ZB, 6E, 6J, BTC/MBT, NKD; NQ control), per session, by year
Causal, descriptive, on owned bars/ticks (2013+ 1-min where it exists, ticks 2023+):
- Autocorrelation of returns at 1/5/15/30/60/120-min horizons by session and hour: where positive (momentum), negative (reversion), stability by year.
- Variance ratio / Hurst by session; share of trend days vs range days (IB extension, close-location); typical path: how often a 1-ATR move continues to 2 ATR vs gives back half.
- Where the day's range forms (hour-of-day range share), gap behaviour (fill rate by size), reaction at prior-day H/L, overnight H/L, session VWAP +- sigma, round numbers, IB edges (touch -> bounce vs break-through rates), after a failed break.
- Cost ratio: median 1-ATR move in $ vs round-trip cost per lot ("room"); liquidity by hour (participation cap).
- Cross-instrument: correlation to NQ by session and horizon, lead/lag at 1-15 min.
Output DS3_FIND_CHARACTER.md: one page per instrument with a plain paragraph ("ES in NY-AM reverts at 5-30 min and trends at 60+; range forms 09:30-11:00; prior-day H/L bounce 62%; room 3.1x cost in RTH, 1.4x overnight").

## Step 2 -- Book candidates generated FROM the map
For each instrument x session where the map shows a tradable regularity (|autocorr| or bounce/break rate beyond its shuffled-day null, room > 2x cost), build the book that expresses it:
- Reversion -> fade shapes at that horizon and anchor (band fade, z-score-to-VWAP, RSI2/Bollinger, IB/range-edge fade, failed-break fade), stop beyond the extreme, target at mean/anchor, time stop at the horizon where autocorrelation turns.
- Momentum -> continuation shapes at that horizon (break of forming range, pullback in direction, acceleration), bracket in ATR units at the horizon's scale.
- Level reaction -> touch/reject and break/retest books. Time-of-day structure -> window books.
- Plus learned-rule search per instrument x session (<=6-leaf monotone tree / small GP over causal features: returns at the horizons above, position in range, distance to anchors in ATR, hour, day type), purged walk-forward, three seeds, family max-stat.
Every candidate: own parameter neighbourhood (plateau, not spike), own brackets, one position, equal-$ risk lots, participation cap, measured fills, NT8/Rithmic-executable.

## Step 3 -- The bar (unchanged, recents method)
Session by session; recent first (L1M L2M L3M L6M -> HOLD MID PRE X'; 2013+ as deep OOS where bars exist); tolerant OOS gate; persistence > 60% considered; drawdown first; placebos (random side / shifted trigger / shuffled day) + family max-stat over the instrument's whole candidate set; purged walk-forward of own parameters; corr to NQ stack <= 0.3; stack Calmar / maxDD improved at equal risk with carrying week dropped. NOW-ONLY -> REGIME, reported beside pooled, not killed. Exact live definition + 5 worked rows for anything that clears.

## Deliverables
DS3_FIND_CHARACTER.md (step 1; first ES, RTY, YM within 6 h, then the rest); DS3_FIND.md ranked table (instrument | session | regularity found | book | params | L1M..X' | maxDD | Calmar | corr | stack gain | placebo | label) every 6 h; plain sentence per instrument: "ES: the thing it does is X; the book that fits is Y; it clears / does not clear because Z". Anything that clears -> top of MORNING.md same hour.

## LEAD HOUSE RULES (apply on top)
Prereg + sha256 in DECISIONS.md BEFORE scoring (the map is descriptive: file its feature list + null definition first; a book is generated only from map rows whose null is beaten, and the map->book rule is frozen before any book is scored); dead_lookup before / append_cells after; append-only shared files with >>; forward-only placebos; epoch-second clocks; percent frame pre-2023 (name the base); instrument-native calendars from public rules, no downloads; evaluator code/instr2/instr2_eval.py, families code/instr2/families.py; frames with stop/target prices in /mnt/l2/l2vast/instr2_trades/; per-world max vectors saved. The map itself uses the same shuffled-day nulls and a family correction over (horizon x session x hour) so the map does not fish. Shadow only; no purchases. Memory guard; <=3 heavy workers per owner.
