# EXIT_FAMILIES_STAGED_SWING - engine build + identity for the STAGED and SWING / LINE-TRAIL exit families (W-XB1), 2026-11-19 ~19:40Z
Research only. No live code touched; ex_inject.py untouched. Prereg line PREREG_XB1 in DECISIONS.md (sha of xb_inject + xb_events + xb_queue). No recipe P&L is stated anywhere in this file (identity only).

## Spec (what the hook does) - code/th_exiteng/xb_inject.py (hook), xb_events.py (recipes, events, bar series, set JSONs), xb_identity.py (checks)
Runs through the production driver (dispatchers, jn05_run2) as set hook module `xb_inject` on top of mf_inject (own per-entry stop / target, ADD or REPLACE like any EXE set). recipe = {} is byte-identical to mf_inject.
- STAGED: recipe `stage` = {lv: [R1..R3], fr: [f1..f3], be: bool, beoff: ticks}. Level_i = entry + side x R_i x risk (risk = initial stop distance). When a print goes 1 tick THROUGH the level, round(f_i x lots) lots are sold at the level (resting-limit convention = the screen's leg fill), exit name `ExStage`, engine call exec_exit(...) WITHOUT place_bracket (place_bracket would reset the stop). After leg 1 and be=true the stop moves to entry + beoff ticks (only tightens). The remainder keeps the target and any trail (chandelier etc.). One trade row per entry, exit_px = lot-weighted average. `be`: [R, offticks] = breakeven stop after +R x risk, no partial.
  Lots: a leg needs >= 2 lots: staged recipes enter 2 lots (1 leg of 0.5), 3 lots (2 legs of 1/3) or 4 lots (3 legs of 0.25). If an account layer resizes the entry below that (round(f x lots) < 1) the leg is skipped (documented limit; 8 of 150 staged trades).
- SWING TRAIL: recipe `swing`: ticks = stop follows the last CONFIRMED swing low (long) / high (short) (pivot m=2, confirmed 2 bars later, gexit.swing_conf) -/+ ticks x 0.25, evaluated at each bar close + 1 s, only tightens.
- LINE TRAIL: recipe `line` = {col, ticks}; columns in the bars file: ln_ema20 (EMA 20 of close), ln_st (Supertrend ATR14 x 3), ln_mid (SMA 20 = Bollinger mid), ln_psar (PSAR 0.02/0.02/0.2). Same bar-close + 1 s rule, only tightens. (ln_mid built, not engine-run: same code path as ema20.)
- Recipes in xb_events.RX: stg1r_chand_v25 (vol 2.5, R3 target, 1R half off, BE, chandelier 3 on the rest, 2 lots), stg2_v15 (vol 1.5, R3, legs 1R/2R of 1/3, BE, 3 lots), stg3_v15 (3 legs, 4 lots; built, not engine-run), be1_v15_t2, swing1_v25, line_{ema20,st,mid,psar}_v25, inert_stage, inert_trail.

## Identity protocol and results (production driver, 19 + 3 set-months used; budget ~10 per family: staged used 3 extra months because BookLock pre-empts staged winners)
1. INERT: neutral setting (stage level 1e6 / swing 1e6 + line ticks 1e6) vs the plain mf_inject set, same month, trade for trade on entry_ns, exit_ns, entry_px, exit_px, exit_name, net_fee: inert_stage 18/18 and inert_trail 20/20 on 202610 (L01811caa), 0 mismatched fields. PASS.
2. SAME-ENTRY SCREEN WALKER (gcore2.walk_path from each engine trade's own entry fill; xb_identity.walk): exit time within 3 s (resting stop / target) or 15 s (market time exit), exit class equal, layer exits (BookLock, StackCut ...) excluded and counted. Books: L01811caa (row tick_8000, both sides), L0f097450 (mode-correct).
| family | recipe | book | months | paired | time match | class match |
|---|---|---|---|---|---|---|
| B swing | swing1_v25 | L01811caa / L0f097450 | 202504, 202610 / 202610 | 47 / 32 | 100% / 100% | 100% |
| B line | line_st_v25 | L01811caa / L0f097450 | 202504, 202610 / 202610 | 51 / 52 | 100% / 100% | 100% |
| B line | line_ema20_v25 | L01811caa | 202610 | 32 | 100% | 100% |
| B line | line_psar_v25 | L0f097450 | 202610 | 47 | 100% | 100% |
| A staged | stg1r_chand_v25 | L01811caa / L0f097450 | 202504, 202509, 202606, 202610 / 202504, 202610 | 71 / 40 (lots as configured) | 100% / 97.5% | 100% |
| A staged | stg2_v15 | L01811caa / L0f097450 | 202504, 202610 / 202610 | 15 / 16 | 100% / 100% | 100% |
Pooled: family B 261 paired, 0 failures; family A 142 paired (lots as configured), 1 failure (a resting stop 5.1 s after the screen, tolerance 3 s) = 99.3% time, 100% class.
Exit price: engine resting stops fill 0.3 to 2.3 pt BETTER than the screen (screen exits one tick through the trigger print; engine rests the stop): mean signed dexit B +0.63, A +0.71 pt, stops A +1.48; |dexit| <= 0.75 pt on about 53%. Same caveat as W-EXITENG: engine P&L is not comparable to screen P&L; recipe-vs-fixed inside the engine is.
Entry-lot limit: 8 staged trades had fewer lots than configured (layer resize / short fill); their leg is not executable; excluded from the pooled rows and counted above.

## Open points (exact)
- Leg COUNT per trade is not verified directly: the hook's leg log (xb_logs/legs.jsonl, added 18:24Z) was never written by the dispatcher runs (the hook's run() override is not called there; cause not isolated). Evidence that legs execute: the lot-weighted engine exit price matches the screen's blended exit within 0.75 pt on 67% of staged-leg trades (median |d| about 0.5 pt) where no-leg prices would differ by several points, and class/time match 100%. A leg-log fix is the next step if a direct count is wanted.
- BookLock interaction: with all D7 layers ON the live BookLock exits most staged winners before the staged remainder logic acts (stg2: 29 of 60 engine exits are layer exits, stg1r 15 of 134). Staged recipes therefore have a small engine effect inside the stack; this is layer behaviour, not a hook defect, and matters when a staged recipe is judged in the stack.
- Gate stated by W-EXITENG is 95% exit class+time and >= 50 pooled per family over 43 months per set; this run is a 2-book, 2-4 month identity (inside the ~10 set-months budget); the pooled counts pass the 95% / >= 50 gates, the 43-month sets were not run.
- Identity date: family B and family A pass identity 2026-11-19 ~19:30Z (2-book basis). Not built: brick-reversal, stop-and-reverse (W-XB2 / others).
