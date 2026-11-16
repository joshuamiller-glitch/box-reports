# DS3_JOINT_EXIT - joint exit design (T-JOINT-EXIT, owner W-JV). STATUS: DESIGN, no engine run yet (engine starts 21:00Z 11-16, JV quota set by the lead then)

**Plain verdict line: design only, no result. Nothing here is a lead. First results table due 12:00Z 11-17.**

Base TL3_EV_JN05W2JL2 (JL2: live caps, base lots, engine fee $1.18, x1.75 for live lots, $4.84 column). Books K7 P7 M7 U7 H7 A7 O7. Windows L3M, L6M, HOLD, PRE, X', GAP; recents first (L3M, L6M, HOLD). Drawdown on both bases (weekly series, daily cumulative) shown in every table; mean second; any setting that only works in L3M is flagged. Controls: persistent draw (bucket 300).

## 1. Factors per book
| factor | levels | source / switch |
|--|--|--|
| E exit rule | as live + top 3 for the book from DS3_BRACKET_DD_BUILD.md / DS3_BRACKET_DD.md / DS3_TARGET_REPLAY*.md (4 levels) | W-D10 bracket grammar (`bracket <book> <sess> stop= target=`; first matching line wins), give-back and other rules need code in a hook (W-BD2/W-D10) |
| L loss side | as live (book cut + flat) / flat level -10% / flat +10% / book-cut arm 10 pts earlier (4) | W-LA la_hooks (code/th_deepen_la/mk_lf.py, mk_fb.py; TL3_EV_FB_* sets: flat d, nocut, arm +/-10) |
| P existing profit lines | as live / locks removed / takes removed (3; reference rows, the deliverable is the best SETTING never none) | engine switches for K7 delta_mult lock, M7 tot_rel step, U7 delta_mult tighten and the take lines: names to be confirmed by W-EV / W-BD2 |
| T target the pct-based lines scale to | as live / rescaled to the new exit typical exit distance (2) | per-book target reference parameter, to be exposed by W-EV |
| Z lots | as live / constant-risk (2) | constant risk = lots x 60 / stop distance (sm_hooks eq lots exists; when the exit rule leaves the 60-pt stop unchanged this level equals as-live and is dropped) |
Full factorial 4 x 4 x 3 x 2 x 2 = 192 per book x 12 months is not run.

## 2. Staged design (cell-month budget, total about 3,200 of about 3,600 available: 15 h x about 240 cell-months/h)
**Stage 1: screen on 12 months (HOLD + L6M = 202511..202610), per book.** One-factor-at-a-time from the as-live baseline: (4-1)+(4-1)+(3-1)+(2-1)+(2-1) = 10 cells, then one coordinate-descent refinement round (take the best level of each factor, re-vary each factor around that combination, about 6 cells) = 16 cells x 12 months = 192 cell-months per book; 7 books = 1,344 (H7, A7, O7 are small books: run only if they have a top-3 exit; budget holds). Baseline cells are shared (one baseline per book is the JL2 reference, already run). Readout per cell: whole-stack drawdown (both bases), worst week, full stops/wk, best-5 weeks kept, winning weeks turned losing, mean, $4.84 column; ranking by drawdown first, mean second, L3M-only flag.
**Stage 2: the best 3-4 combinations per book over all 43 months with controls.** 3 combos x 43 = 129 plus persistent-draw controls (3 placebo + 3 matched per leader at the combination skip/fire share, 12 months HOLD + L6M = 72) = about 200 per book; 7 books = about 1,400.
**Stage 3: combined books and interaction table.** All per-book winners together (1 set x 43 months), leave-one-book-out (7 sets) and one-book-in (7 sets) on HOLD + L6M = 14 x 12 = 168, the combined set on 43 months and 3 persistent controls (about 45 + 36), the stage-2 runner-up combination per book swapped in (7 x 12 = 84): about 450. Interaction table: does book A's change move book B's result (cross-book delta of every other book's P&L and of the stack drawdown); where a single winner loses once combined; where a failed single passes in combination.

## 3. Hooks needed (must compose: exit rule + loss side + profit switches + target scale + lots)
- Exit rule layer (W-D10 / W-BD2): bracket grammar lines per book and session, plus a give-back / other rule hook for rules the grammar lacks. One hook module, one identity cell (rule list empty).
- Loss-side layer (W-LA la_hooks): flat level, nocut, arm shift per book; identity = TL3_EV_FB_M_ID.
- Profit-line switches (W-EV / W-BD2): named switches to remove the K7 delta_mult lock, the M7 tot_rel step, the U7 delta_mult tighten and the take lines, and to set their target reference. One identity cell (all as live).
- Lots layer: eq-$ lots (sm_hooks eq) with the stop of the new exit.
- Identity proofs: one cell per layer (hook present, nothing active) plus one cell with all four layers inert; each must equal TL3_EV_JN05W2JL2 trade for trade on 202610 and on 3 more months before any factor cell is read.

## 4. Open items / owners
W-D10, W-BD2: exit-rule hook with identity; top-3 list per book. W-LA: FB cells and arm switch confirmed. W-EV: profit-line switch names and target reference. W-JV: this page, the cell list generator (mk_je.py), scoring and interaction table. Nothing is scored until the engine starts.
