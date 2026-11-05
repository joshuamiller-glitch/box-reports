# DS3_NQ13 - NQ 13-year parameter-regime map (ZL-2, T2_NQ13) - INTERIM 1, 2026-11-05T19:46:29Z
Append-only. Scope note (prereg): outputs/l2vast/ds3/prereg/T2_NQ13_scope.md, sha256 0678be426feeeb3279cba2fcf3bc95c6012eaa637b75f9d6c91eda58d827cb14 (logged in DECISIONS.md before any outcome statistic). n_tested = 9,855 cell-sessions (3,483 cells x live sessions, brackets stop {40,60,80} x target {40,60,90}). Ledger T2_NQ13.

## Plain sentence
No walk-forward parameter selector (trailing 6/12/24 months -> next month, per book x session) beats the fixed live parameters on 2023-26; so no params_policy.txt refit rule is proposed.

## Objects and calibration (read first)
- 1-min object (2013-2026, percent frame: brackets/slip/fees scaled by raw_close/20,620, P&L in 2023-26 point-equivalents x $20). Live-cell weekly correlation to the 1-s engine plain-signal series is 0.49-0.84, below the 0.90 rule: NO formal verdict from it. Pre-2023 results (E2) are descriptive only.
- 1-s path object (2023-04..2026-10, same 935 label days): calibration >= .90 for 7 of 14 pairs: KB asia/london/nypm, SM asia/london, HM asia, PB asia. Near misses: KB nyam .890, PE nyam .894, PE london .870, PE asia .853, HM nyam .844, MV nyam .851; MV london .591. Formal verdicts only for the 7 pairs, only on 2023-26.
- Bases named: V0 = engine as run (09:00-09:29 and 15:00-16:54 blocked); V2 = V0 + 09:30-09:59 and 18:00-18:04 blocked. Carrying weeks dropped (2023 W21-41, 2025 W06-09, 2026 W06-08, W29-39). Cap 2026-10-31.

## 13-year map (1-min, V0; same shape on V2)
- Live cell by year: negative in most years before 2023 and positive mainly 2024-25. Years with positive live $/wk in 2013-2022 (of 10): HM asia 4, HM nyam 8, KB asia 1, KB london 1, KB nyam 4, KB nypm 3, MV london 2, MV nyam 4, PB asia 3, PE asia 3, PE london 4, PE nyam 3, SM asia 6, SM london 4.
- Stability: mean year-to-year rank correlation of cell rankings 0.07 (pairs 0.0-0.15): which parameters paid does not persist. Live-cell neighbour sign agreement 0.66-0.88 (mean 0.78), i.e. mild plateau locally but the whole plateau flips sign across years.
- Static pre-2023 best cell -> 2023-26: mean rank correlation pre/post 0.12; best-pre cell has mean post percentile 0.63 and beats the live cell post in 10 of 14 pairs, but the live cell was chosen with hindsight on 2023-26, so this is not evidence for a selector.
- Full per-year x session x cell tables: out/dis_nq13/cell_year_usd_wk_{V0,V2}.csv, map_live_and_stability_{V0,V2}.csv, static_pre_to_post_selection.csv.

## Walk-forward selector (criterion = trailing net $; min trades 10/20/40 for T=6/12/24; fallback to live cell)
Evaluation E1 = 2023-04..2026-10 (formal, 1-s object); E2 = 2015-01..2023-03 (1-min, descriptive). Placebos: P1 random cell per month (forward-only), P2 stale window, family max-T over 42 selectors.
- 1-s E1, V0: 0 of 42 selectors with CI above zero; 29 of 42 below live; mean selector-minus-live -$183/wk-unit (formal 21: -$297, 81% negative); selector drawdown > live in 76% (formal 86%); family max-T p = .68.
- 1-s E1, V2: 0 of 42 CI above zero; 30 of 42 negative; mean diff -$162 (formal 21: -$276, 90% negative); drawdown worse in 74%; best single placebo p1 = .06 but family p = .73.
- 1-min E1 (descriptive): 0 of 42 win; mean diff -105 (V0), -110 (V2).
- 1-min E2 (descriptive): mean diff +108 (V0), +75 (V2); 2 of 42 with CI above zero; placebo p1<=.10 in 12 (V0) / 16 (V2); family max-T p .13 (V0), .08 (V2). Not formal (calibration fails) and does not carry into 2023-26 where the sign reverses.
- Win rule (positive with CI above zero on E1 and E2, placebo and family p <= .10, both bases, calibration passed): NOT met on any selector.

## Caveats
Percent-frame 1-min object is not the live stack; E2 descriptive only; live cell picked with hindsight on 2023-26 (biases E1 toward live); 1-s object uses fixed-point brackets and a shorter usable window range per T; 7 of 14 pairs only formal. Cross-check against BASE-4 E.walk_forward not yet done. Next interim in 6 h.
