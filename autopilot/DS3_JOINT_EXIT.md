# DS3_JOINT_EXIT - joint exit design (T-JOINT-EXIT, owner W-JV). STATUS: DESIGN, no engine run yet (engine starts 21:00Z 11-16, JV quota set by the lead then)
> VALIDATION (W-DV, FIRST PASS, 2026-11-16): trials counted design 16 cells x 7 books = 112 stage-1 cells, N_used 112 (TRIALS_LEDGER.csv JV; stage 2 picks inside it); correction will be RC / SPA / DSR over the stage-1 family and PBO on stage-2 picks; no result on this page yet; number shown will be IN-SAMPLE until a walk-forward or untouched window exists.

**Plain verdict line: STAGE 1 DONE (section 8): no one-factor cell is a lead; only P7 flat -10 pct improves the ulcer index in both HOLD and L6M and it costs mean. Stage 2 and older windows queued.**

Base TL3_EV_JN05W2JL2 (JL2: live caps, base lots, engine fee $1.18, x1.75 for live lots, $4.84 column). Books K7 P7 M7 U7 H7 A7 O7. Windows L3M, L6M, HOLD, PRE, X', GAP; recents first (L3M, L6M, HOLD). Drawdown on both bases (weekly series, daily cumulative) shown in every table; mean second; any setting that only works in L3M is flagged. Controls: persistent draw (bucket 300).

## 1. Factors per book
| factor | levels | source / switch |
|--|--|--|
| E exit rule | as live + top 3 for the book from DS3_BRACKET_DD_BUILD.md / DS3_BRACKET_DD.md / DS3_TARGET_REPLAY*.md (4 levels) | W-D10 bracket grammar (`bracket <book> <sess> stop= target=`; first matching line wins), give-back and other rules need code in a hook (W-BD2/W-D10) |
| L loss side | as live (book cut + flat) / flat level -10% / flat +10% / book-cut arm 10 pts earlier (4) | W-LA la_hooks (code/th_deepen_la/mk_lf.py, mk_fb.py; TL3_EV_FB_* sets: flat d, nocut, arm +/-10) |
| P existing profit lines | REPLAY ONLY (decision W-JV 11-16): the lines (K7 delta_mult lock, M7 tot_rel step, U7 delta_mult tighten, take lines) are ABSENT in JL2 and need per-second book features that exist only for the last ~60 days (cf2_mbo, tot_rel is a PROXY); engine cells carry P = as engine; the effect of locks removed / takes removed is read from W-LB2's replay (th_lcb2/profit_lines.py), labelled REPLAY ONLY, 60 days, proxy tot_rel. Pending W-EV confirmation that engine features exist. | no engine switch |
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

## 5. Factor P as an engine hook (stage 2) - UPDATE 11-16: W-CF2 reports per-second MBO delta and depth for all 1,126 days (cf2_mbo, 2023-04..2026-11); the 60-day limit was stale. Plan: hook jv_pl_hooks.py from per-day side files (mid, buy, sell, med, totrel PROXY) implementing the K7 lock (pct>=0.3, delta_mult>=5 over 10 s, persist 10 s, lock at entry), U7 tighten (pct>=0.4, delta_mult>=20 over 15 s, persist 5 s, 30 pts behind the running extreme) and M7 step (pct>=0.3, totrel>=2, persist 2 s, step 10 pts); inert identity = JL2; take lines still need their definitions (W-LB2/DS7.cs). Original slot text: if W-CF2 can turn the bought MBO history (2023-04..2026-11) into per-second delta and total-depth series for all 43 months (answer expected 19:30Z 11-16), the profit lines return as an engine hook for stage 2 with an inert-identity cell (TL3_JE_ID_P, equal to JL2 on 202610 and 3 more months) and levels as live / locks removed / takes removed. Until then stage 1 engine cells carry P = as engine and the effect is REPLAY ONLY (60 days, proxy tot_rel).

## 6. Profit-line hook status (11-16 evening)
Built: jv_pl_hooks.py (K7 delta_mult lock, U7 delta_mult tighten; state machine jv_pl_core.py verified against W-LB2's replay loop on 3000 random segments of the W-CF2 side files, 0 mismatches; identity cell TL3_JE_ID_P). NOT built: M7 tot_rel step (W-LB2 withdrew it: proxy correlation 0.28 with the live definition) and the take lines (A7 pct>=0.983 secs_ext>=5, K7 pct>=0.95 secs_ext>=5, U7/H7 pct lock persist 1, NKD take: need the v2.9 policy file; live delta_mult was about 13x too high before v1.9c; MBO delta uses the exchange aggressor flag, live uses print vs bid/ask: parity not testable, the v1.9b log prints no features). W-LB2 43-month replay on JL2 trades: K7 lock net -86.5k (max DD 50.2k -> 42.7k; last 6 months -1.1k), U7 tighten net -63.4k (DD 44.9k -> 36.9k; last 6 months +27.1k): recent-window effects, 43-month net negative. Use: stage 2 only as a recent-window question for K7 and U7; reported as REPLAY-DERIVED HOOK, tot_rel proxy not used, no build recommendation without live feature logs.

## 7. Base label (W-EV, 11-16)
Every result on this page is on the JL2 base (without live take/lock lines). The live-equivalent base JL3 = JL2 + persist=1 profit takes/locks (sets TL3_EV_JL3*, runs from 21:00Z on L6M + HOLD) is built by W-EV; the replay says JL3 costs about -3 pct mean per week and 5-8k more drawdown, so the joint exit decisions are to be re-judged on JL3 (the composed cells will be rebuilt on JL3 as a stage-2 base swap).

## 8. STAGE 1 RESULTS (FIRST PASS; JL2 base without live take/lock lines; 12 months HOLD+L6M; one factor at a time; written by jv_je_score.py)

Cell name TL3_JE_<book>_<E><L><P><T><Z>. Levels: E 1-3 = buildable top exit rules (W-D10 hook), L 1 = flat -10 pct (K7 40.5, P7 38), 2 = +10 pct, 3 = book-cut arm 10 pts earlier, P 1 = the book profit line AS DESIGNED (K7 lock, U7 tighten; world B, see DS3_PROFIT_LINES_LOO.md). Reference: JL2 for every book except P7, whose cells use TL3_EV_FB_A_KP (K7 45 + P7 42 flat through la_hooks). Not run: T (target scale) and Z (constant-risk lots) layers (missing target reference / new-exit stop distance), M7 step, take lines. Ulcer gain = (ulcer_ref - ulcer)/ulcer_ref, + = better. d mean in base lots (x1.75 for user lots), engine fee; @4.84 repriced.

| cell | book | window | ulcer ref -> cell | ulcer gain % | DD cut weekly % | DD cut daily % | worst wk ref -> cell | d mean $/wk | d mean @4.84 | full stops/wk ref -> cell | win->lose |
|--|--|--|--|--|--|--|--|--|--|--|--|
| TL3_JE_K7_10000 | K7 | HOLD | 18323 -> 17881 | +2.4 | +0.4 | -1.2 | -31211 -> -30699 | +146 | +140 | 10.6 -> 10.6 | 1 |
| TL3_JE_K7_10000 | K7 | L6M | 8274 -> 8323 | -0.6 | -7.4 | -2.0 | -13430 -> -13430 | +217 | +212 | 11.0 -> 11.0 | 1 |
| TL3_JE_K7_20000 | K7 | HOLD | 18323 -> 18770 | -2.4 | -2.0 | -5.3 | -31211 -> -31604 | -316 | -328 | 10.6 -> 10.6 | 1 |
| TL3_JE_K7_20000 | K7 | L6M | 8274 -> 8606 | -4.0 | -20.0 | -7.9 | -13430 -> -14211 | -168 | -177 | 11.0 -> 11.0 | 1 |
| TL3_JE_K7_01000 | K7 | HOLD | 18323 -> 22352 | -22.0 | -21.4 | -16.8 | -31211 -> -34865 | -1119 | -1120 | 10.6 -> 10.5 | 1 |
| TL3_JE_K7_01000 | K7 | L6M | 8274 -> 9134 | -10.4 | -22.1 | -15.5 | -13430 -> -16396 | -903 | -904 | 11.0 -> 10.8 | 0 |
| TL3_JE_K7_02000 | K7 | HOLD | 18323 -> 20927 | -14.2 | -5.6 | -7.3 | -31211 -> -32594 | -268 | -260 | 10.6 -> 10.9 | 3 |
| TL3_JE_K7_02000 | K7 | L6M | 8274 -> 8828 | -6.7 | -17.8 | -12.7 | -13430 -> -14495 | -444 | -432 | 11.0 -> 11.3 | 1 |
| TL3_JE_K7_03000 | K7 | HOLD | 18323 -> 19985 | -9.1 | -16.1 | -4.0 | -31211 -> -28818 | -1072 | -1073 | 10.6 -> 10.4 | 1 |
| TL3_JE_K7_03000 | K7 | L6M | 8274 -> 9593 | -15.9 | -35.8 | -22.9 | -13430 -> -18241 | -1733 | -1733 | 11.0 -> 10.7 | 0 |
| TL3_JE_K7_00100 | K7 | HOLD | 18323 -> 19457 | -6.2 | -6.5 | +8.4 | -31211 -> -33021 | -1524 | -1557 | 10.6 -> 10.4 | 2 |
| TL3_JE_K7_00100 | K7 | L6M | 8274 -> 8202 | +0.9 | -19.5 | -12.6 | -13430 -> -16044 | -995 | -1042 | 11.0 -> 10.7 | 0 |
| TL3_JE_P7_10000 | P7 | HOLD | 17016 -> 19147 | -12.5 | -13.8 | -4.5 | -30409 -> -32588 | -1176 | -1202 | 10.3 -> 10.3 | 2 |
| TL3_JE_P7_10000 | P7 | L6M | 9276 -> 10716 | -15.5 | -19.6 | -27.9 | -21267 -> -25436 | -2465 | -2490 | 10.7 -> 10.7 | 0 |
| TL3_JE_P7_20000 | P7 | HOLD | 17016 -> 19756 | -16.1 | -14.2 | -4.9 | -30409 -> -33091 | -1482 | -1513 | 10.3 -> 10.3 | 2 |
| TL3_JE_P7_20000 | P7 | L6M | 9276 -> 11191 | -20.6 | -24.0 | -34.4 | -21267 -> -26364 | -3011 | -3044 | 10.7 -> 10.8 | 0 |
| TL3_JE_P7_01000 | P7 | HOLD | 17016 -> 16252 | +4.5 | -3.3 | +8.9 | -30409 -> -30565 | -232 | -234 | 10.3 -> 10.3 | 0 |
| TL3_JE_P7_01000 | P7 | L6M | 9276 -> 9114 | +1.8 | +1.8 | +2.8 | -21267 -> -20879 | -369 | -371 | 10.7 -> 10.7 | 0 |
| TL3_JE_P7_02000 | P7 | HOLD | 17016 -> 17809 | -4.7 | -2.4 | -6.5 | -30409 -> -30757 | -8 | -8 | 10.3 -> 10.4 | 1 |
| TL3_JE_P7_02000 | P7 | L6M | 9276 -> 9262 | +0.2 | -3.0 | -3.9 | -21267 -> -21903 | +258 | +259 | 10.7 -> 10.8 | 0 |
| TL3_JE_P7_03000 | P7 | HOLD | 17016 -> 18695 | -9.9 | +7.6 | -5.8 | -30409 -> -29132 | -4100 | -4104 | 10.3 -> 10.1 | 4 |
| TL3_JE_P7_03000 | P7 | L6M | 9276 -> 11541 | -24.4 | -37.0 | -19.2 | -21267 -> -29132 | -6079 | -6077 | 10.7 -> 10.5 | 2 |
| TL3_JE_M7_10000 | M7 | HOLD | 18323 -> 18323 | +0.0 | +0.0 | +0.0 | -31211 -> -31211 | +0 | +0 | 10.6 -> 10.6 | 0 |
| TL3_JE_M7_10000 | M7 | L6M | 8274 -> 8274 | +0.0 | +0.0 | +0.0 | -13430 -> -13430 | +0 | +0 | 11.0 -> 11.0 | 0 |
| TL3_JE_M7_03000 | M7 | HOLD | 18323 -> 20093 | -9.7 | -14.5 | -2.2 | -31211 -> -35879 | -964 | -976 | 10.6 -> 9.9 | 0 |
| TL3_JE_M7_03000 | M7 | L6M | 8274 -> 9702 | -17.3 | -85.2 | -36.9 | -13430 -> -24868 | -1365 | -1381 | 11.0 -> 10.4 | 0 |
| TL3_JE_U7_03000 | U7 | HOLD | 18323 -> 18640 | -1.7 | -5.7 | +0.2 | -31211 -> -31211 | -23 | -24 | 10.6 -> 10.4 | 1 |
| TL3_JE_U7_03000 | U7 | L6M | 8274 -> 8372 | -1.2 | +0.0 | +0.2 | -13430 -> -13430 | -47 | -47 | 11.0 -> 10.8 | 1 |
| TL3_JE_U7_00100 | U7 | HOLD | 18323 -> 19397 | -5.9 | -30.3 | -1.6 | -31211 -> -40117 | -471 | -471 | 10.6 -> 10.1 | 4 |
| TL3_JE_U7_00100 | U7 | L6M | 8274 -> 8760 | -5.9 | -8.1 | -26.1 | -13430 -> -9195 | -30 | -30 | 11.0 -> 10.6 | 2 |
| TL3_JE_H7_10000 | H7 | HOLD | 18323 -> 17980 | +1.9 | +1.9 | +5.2 | -31211 -> -33394 | -132 | -131 | 10.6 -> 10.3 | 2 |
| TL3_JE_H7_10000 | H7 | L6M | 8274 -> 8512 | -2.9 | -7.4 | -8.9 | -13430 -> -11711 | -1113 | -1107 | 11.0 -> 10.8 | 1 |
| TL3_JE_H7_20000 | H7 | HOLD | 18323 -> 17671 | +3.6 | +5.6 | +6.0 | -31211 -> -31074 | -161 | -161 | 10.6 -> 10.4 | 1 |
| TL3_JE_H7_20000 | H7 | L6M | 8274 -> 8332 | -0.7 | -14.4 | -3.0 | -13430 -> -11775 | -681 | -680 | 11.0 -> 10.9 | 1 |
| TL3_JE_H7_03000 | H7 | HOLD | 18323 -> 18322 | +0.0 | +0.0 | +0.0 | -31211 -> -31211 | +40 | +40 | 10.6 -> 10.5 | 0 |
| TL3_JE_H7_03000 | H7 | L6M | 8274 -> 8274 | +0.0 | +0.0 | +0.0 | -13430 -> -13430 | +46 | +46 | 11.0 -> 11.0 | 0 |
| TL3_JE_A7_10000 | A7 | HOLD | 18323 -> 18594 | -1.5 | -0.8 | +0.1 | -31211 -> -31106 | -276 | -281 | 10.6 -> 10.7 | 0 |
| TL3_JE_A7_10000 | A7 | L6M | 8274 -> 8433 | -1.9 | +3.2 | +4.7 | -13430 -> -13002 | -532 | -541 | 11.0 -> 11.3 | 0 |
| TL3_JE_A7_03000 | A7 | HOLD | 18323 -> 18740 | -2.3 | +2.7 | +0.0 | -31211 -> -31211 | +195 | +194 | 10.6 -> 10.5 | 0 |
| TL3_JE_A7_03000 | A7 | L6M | 8274 -> 8241 | +0.4 | +0.0 | -4.1 | -13430 -> -13430 | +631 | +629 | 11.0 -> 10.9 | 0 |
| TL3_JE_O7_10000 | O7 | HOLD | 18323 -> 18323 | +0.0 | +0.0 | +0.0 | -31211 -> -31211 | +0 | +0 | 10.6 -> 10.6 | 0 |
| TL3_JE_O7_10000 | O7 | L6M | 8274 -> 8274 | +0.0 | +0.0 | +0.0 | -13430 -> -13430 | +0 | +0 | 11.0 -> 11.0 | 0 |
| TL3_JE_O7_20000 | O7 | HOLD | 18323 -> 18323 | +0.0 | +0.0 | +0.0 | -31211 -> -31211 | +0 | +0 | 10.6 -> 10.6 | 0 |
| TL3_JE_O7_20000 | O7 | L6M | 8274 -> 8274 | +0.0 | +0.0 | +0.0 | -13430 -> -13430 | +0 | +0 | 11.0 -> 11.0 | 0 |
| TL3_JE_O7_03000 | O7 | HOLD | 18323 -> 18611 | -1.6 | +0.9 | +0.3 | -31211 -> -30982 | -244 | -244 | 10.6 -> 10.1 | 1 |
| TL3_JE_O7_03000 | O7 | L6M | 8274 -> 8267 | +0.1 | +0.0 | +0.2 | -13430 -> -13430 | -135 | -136 | 11.0 -> 10.5 | 0 |

**Reading (plain).** Of the 23 stage-1 cells scored, only 1 improve the ulcer index in BOTH HOLD and L6M: TL3_JE_P7_01000. They cut ulcer by 4.5 / 1.8 pct (HOLD / L6M) and cost mean (-232 / -369 $/wk). Most one-factor changes make the ulcer index worse in both windows (K7 loss-side moves, P7 exit rules and arm, M7 exit rule, K7 lock as designed). Zero-effect cells: M7 E1, O7 E1/E2 (no trades altered in the windows). No stage-1 cell is a lead. Stage 2 (two-factor combos of the one-factor leaders and two joint-across-books sets) and the older windows (GAP / PRE / X' ) of the leaders are queued (queue_stage2.txt).
