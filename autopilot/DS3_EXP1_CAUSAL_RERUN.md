# DS3_EXP1_CAUSAL_RERUN - EXP1 profit re-keyed with vol_tag_causal (VOLFIX RR1, 2026-10-30)
Label: RESCORE_CAUSAL, no new selection. Amendment A5 (defect) logged in DECISIONS.md before any statistic. Same 120 chains, 66 fixed cells, A4 chains, prereg V2 gates, cached per-trade deltas (profit_cells.npz); only the 3x3 key changed (ON = asia/london/pre now uses the PREVIOUS label day's tag; AM/PM unchanged). v0 outputs kept in out/thp/wf/exp1/; causal outputs in out/thp/wf/exp1_causal/ (chains_profit_B.csv, fixed_profit_B.csv, vf_cell_table.csv, vf_chain_spans.csv, vf_A4_F7_chains.csv, vf_extra.json, distill_profit.json). Own masks only (2026=20260101..20260206, L6M=20250801..20260206, HOLD=20250701..20260206, PRE=20240201..20250630, X'=20230401..20240131; chains are scored from 20230701 because the first quarter is walk-forward warm-up: "X'(sc)"), label day <= 20260206, UNTOUCHED never read. Reproduction check: running the same code with the v0 key reproduces the published chains (tight|cell|6m|m0.5 PRE +0.636, 3 CANDIDATE / 117 DEAD) to the digit.
Bases: M = measured; N = no target-fill correction; C = doubled friction. LIVE-CAL (LIVE_CAL_SUMMARY.md): targets fill at nominal (target correction 0) = the N basis is the point estimate; market exits ~1.0 pt (profit-exit measured +0.19 +/- 0.28 vs path, so the 0.995 pt used is conservative) -> LIVE-CAL profit basis = N; M is the stress case. All numbers pts/trade, MDE = 2.8 SE (cluster label day x session).

## 1. Verdicts
| | v0 (look-ahead) | causal |
|---|---|---|
| profit chains (120) | 0 PASS / 3 CANDIDATE / 117 DEAD | **0 PASS / 0 CANDIDATE / 120 DEAD** |
| fixed cells (66, no regime key) | 0/0/66 | 0/0/66 (identical) |
| RC family (N=186) p | 0.035 | 0.035 (the max is a fixed non-regime cell) |
| mean PRE by scope: cell / bookcell / pooled / perbook | +0.36 / -0.04 / -0.15 / -0.53 | **-0.36 / -0.55 / -0.15 / -0.53** (pooled, perbook identical) |
| mean HOLD by scope (same order) | +0.14 / -0.11 / +0.03 / -0.09 | -0.22 / -0.12 / +0.03 / -0.09 |
| best cell-scope chain PRE | +0.64 | +0.016 (all|cell|ew10|m1.0; CI -0.66..+0.69, MDE 0.96; HOLD -0.32, N -0.66/-1.53) |
| best bookcell chain PRE | | -0.32 |
| best chain of all 120 (PRE) | +0.64 | all|pooled|6m|m0.0 +0.249 (MDE 0.32), HOLD +0.53, X'(sc) -0.42, N basis -0.36 PRE, placebo rank 0.5, DEAD (pooled: unchanged from v0, was already DEAD) |
Where the v0 gain came from: ON-session trades contributed +0.72 (PRE) / +0.52 (HOLD) of the +0.64/+0.41 of the top chain; AM +(-0.10)/(-0.04), PM +0.02/-0.06. Causal: ON -0.19 / -0.34, AM and PM identical to v0 (their key was already causal). The whole effect was the look-ahead in the ON half (vf_ON_AMPM_split.csv).

## 2. The three v0 CANDIDATE chains, causal key (M basis; X' = scored 2023-07..2024-01; MDE in brackets)
| chain | PRE (MDE) | X'(sc) | HOLD (MDE) | L6M (MDE) | 2026 (MDE) | N PRE / HOLD / L6M / 2026 | C PRE / HOLD |
|---|---|---|---|---|---|---|---|
| tight|cell|6m|m0.5 | -0.28 (0.86) | -0.10 | -0.44 (1.39) | -0.49 (1.49) | -0.45 (2.76) | -0.74 / -1.50 / -1.56 / -1.27 | -0.57 / -0.81 |
| all|cell|6m|m1.0 | -0.44 (0.79) | -0.02 | -0.20 (1.29) | -0.19 (1.38) | -0.82 (2.51) | -0.85 / -1.26 / -1.27 / -1.71 | -0.69 / -0.55 |
| all|cell|6m|m0.5 | -0.32 (0.85) | -0.21 | -0.07 (1.35) | -0.08 (1.44) | -0.48 (2.58) | -0.84 / -1.39 / -1.41 / -1.57 | -0.63 / -0.49 |
(v0 for reference: +0.64/+0.61/+0.61 PRE, HOLD +0.41/+0.53/+0.65.) Placebos (causal): within-session shuffled-tag (24 draws, tag permuted across label days within ON/AM/PM, whole WF re-run): real PRE is NOT above the shuffles (share of shuffles >= real: 0.38 / 0.79 / 0.46; best-of-60 cell+bookcell chains real +0.016 vs shuffled-best mean -0.05, p(shuffle >= real) 0.25); random action at the same fire rate (200 draws, uniform menu action on the chain's fired set): real PRE below random mean (p(random >= real) 0.94). Same placebos on v0: shuffled-tag p = 0.00 (the leaky key beats every shuffle by construction), random-action p 0.00-0.005. The v0 apparent significance was entirely the leak.

## 3. Fixed 3x3 table (best fixed action per cell, within-cell mean, PRE-selected, as before; M basis; HOLD/X'full/L6M/2026 and N basis out of the selection)
| cell | best fixed action | n PRE | PRE (MDE) [CI lo] | X' full | HOLD | L6M | 2026 | N PRE / HOLD | C PRE / HOLD | RC adj p |
|---|---|---|---|---|---|---|---|---|---|---|
| vol_lo+ON | F5_ddhalf_D16_a75 | 4053 | +0.71 (2.0) [-0.69] | +0.58 | +1.15 | +0.68 | +7.08 | -0.15 / -0.16 | +0.32 / +0.76 | 0.995 |
| vol_lo+AM | F7_take_p90 | 1861 | +0.07 (0.6) | +0.13 | +0.48 | +0.19 | -0.21 | -0.25 / -0.13 | -0.07 / +0.33 | 1.00 |
| vol_lo+PM | F1_atr_k3_a25 | 1479 | +1.88 (4.4) [-1.22] | +2.96 | -0.12 | 0.00 | -3.67 | +1.47 / -0.88 | +1.39 / -0.64 | 0.98 |
| vol_mid+ON | F7_take_p70 | 2977 | +0.29 (1.7) | -1.74 | +0.54 | +0.49 | +0.89 | -0.89 / -1.36 | -0.20 / +0.04 | 1.00 |
| vol_mid+AM | F7_take_p90 | 1787 | +0.15 (0.6) | -0.23 | +0.71 | +0.84 | +1.04 | -0.18 / +0.16 | -0.01 / +0.57 | 1.00 |
| vol_mid+PM | F6_step_S2 | 1173 | +0.51 (4.7) | +0.20 | -2.61 | -2.95 | +0.22 | -0.46 / -4.24 | -0.12 / -3.25 | 1.00 |
| vol_hi+ON | F7_take_p70 | 6071 | +0.46 (1.2) | -0.42 | +0.02 | -0.03 | +1.91 | -0.64 / -2.05 | +0.01 / -0.52 | 0.995 |
| vol_hi+AM | F1_atr_k3_a25 | 2932 | +0.39 (2.6) | -1.99 | +0.38 | +0.52 | -2.55 | +0.18 / -0.08 | +0.08 / +0.06 | 1.00 |
| vol_hi+PM | F1_atr_k5_a25 | 2321 | +0.88 (2.2) | +2.63 | -0.18 | -0.39 | -1.16 | +0.79 / -0.41 | +0.63 / -0.44 | 0.99 |
RC over 594 cell x action pairs (PRE): v0 p = 0.0245, causal p = **0.764**. Every cell DEAD (no cell has PRE CI > 0; the AM/PM rows are identical to v0 because their key was already causal; v0 vol_lo+ON +4.27 / vol_mid+ON +1.53 are gone). Best of 594 PRE mean now +1.88 (vol_lo+PM, unchanged cell, CI -1.2..+5.0, MDE 4.4); shuffled-tag best-of-594 PRE mean +2.31 (p95 3.78), p(shuffle >= real) 0.65.

## 4. The post-hoc lead "vol_lo+ON take@50%" (F7_take_p50 in the vol_lo + ON cell; same spec, causal key; within-cell mean)
| key | n cell | PRE (CI; MDE) | X' full | X'(sc) | HOLD (CI; MDE) | L6M (MDE) | 2026 (n=110; MDE) | N PRE / HOLD / L6M / 2026 | C PRE / HOLD | books > 0 (PRE+HOLD) | years > 0 |
|---|---|---|---|---|---|---|---|---|---|---|---|
| v0 (look-ahead) | 5,715 | +4.27 (+2.14..+6.40; 3.0) | +5.02 | +2.97 | +3.52 (+0.69..+6.36; 4.1) | +2.79 (4.3) | +11.57 (13.7; n=100) | +2.89 / +1.66 / +0.81 / +10.15 | +3.64 / +2.93 | 9/10 | 2023-26 all |
| **causal** | **7,285** | **+0.25 (-1.75..+2.24; 2.8)** | +1.79 | +1.22 | +3.06 (+0.12..+6.01; 4.2) | +3.28 (4.9) | +9.41 (15.9) | **-1.17** / +1.07 / +1.22 / +7.65 | -0.39 / +2.44 | 8/10 | 2023 +1.6, 2024 -0.8, 2025 +1.9, 2026 +9.4 |
New lead number: **PRE +0.25 (CI includes 0, MDE 2.8), N basis PRE -1.17**. Placebos: shuffled-tag (1000 draws, tag permuted across label days within ON) p(shuffle >= real) = 0.54 for PRE (v0: 0.00); best-of-66-actions in the cell 0.39; best of 594 pairs 0.65; rank of take@50 among all 66 actions in the cell (random fixed action): 0.61 (v0: 0.985). HOLD +3.06 does beat the HOLD shuffles (p 0.005, v0 control 0.003), and L6M/2026 are positive on M and N; PRE and X' (full) are not. So the causal residual is a HOLD/L6M-only observation (take at 50% of target in vol_lo-yesterday ON entries earns in 2025-07..2026-02 but not in 2023-04..2025-06: PRE N basis negative, 2024 negative); it was NOT PRE-selected under the causal key, so it cannot be a lead; at most "recent-only observation, needs forward evidence". Diagnostic (PRE, ON trades, take@50% by (prev tag, today tag)): today=lo +5.14/+3.83/+3.27 for prev=lo/mid/hi, today=hi -3.93/-4.14/-0.41: the effect lives in TODAY's overnight tag (information from the future of the trade), not in yesterday's.

## 5. Volsplit student and teacher (rolling monthly refit on trailing 12 months, out of sample; teacher tight|cell|6m|m0.5 on the causal key)
| student | PRE | HOLD | X'(sc) | v0 (PRE / HOLD / X') |
|---|---|---|---|---|
| teacher (causal table chain) | -0.28 | -0.44 | -0.25 | +0.64 / +0.41 / +0.42 |
| bal | -0.96 | -0.98 | -1.92 | -1.30 / -1.27 / -2.41 |
| unbal | +0.04 | +0.13 | -1.10 | -0.03 / +0.12 / -0.11 |
| volsplit | -0.41 | -0.02 | -0.08 | +0.19 / +0.07 / +0.09 |
Retained gain is undefined (teacher negative). No student has a positive teacher to retain. unbal PRE +0.04 / HOLD +0.13 is the pooled-leaf tree that fires 1.6% of trades (not a key effect).

## 6. A4 exploratory F7-only cell chains (post-look, label LEAD at most)
v0 best (F7|cell|12m|m0.0): PRE +0.73 / HOLD +1.22 / X' +0.15, N +0.07 / -0.15. Causal: best by PRE F7|cell|3m|m1.0 PRE +0.14 / HOLD +0.38 / X'(sc) +0.46, N -0.33 / -0.61; F7|cell|12m|m0.0 (the v0 best spec) PRE +0.06 / HOLD +1.12 / X' +0.03, N -0.58 / -0.32 (vf_A4_F7_chains.csv). No LEAD.

## 7. Causal 6m table at asof 20260206 (what the nightly would publish for chain tight|cell|6m|m0.5)
WF all-scored -0.29, last-6m -0.27 (v0 +0.53 / +0.40). Table rows: vol_lo+ON F0_const_D16_a50, vol_lo+PM F6_step_S3, vol_hi+AM F5_ddhalf_D12_a25, vol_hi+PM F2_mfefrac_f0.15_a25, others hold (vf_table_asof_20260206.csv). Recommendation: the profit section of policy_candidate_exp1.txt must be EMPTY.

## 8. EXACT lines for the report owner to change in DS3_ADAPTIVE_EXP1.md (not edited here)
1. Title/first paragraph: append "RESCORE NOTE (VOLFIX 2026-10-30): the 3x3 vol key of the profit side used the look-ahead vol_tag_entry_day for ON (asia/london/pre) trades; every profit-regime result below marked [VOID] is replaced by autopilot/DS3_EXP1_CAUSAL_RERUN.md. Loss side was causal and is unchanged."
2. "## Verdicts (V2)" bullet PROFIT: replace "0 PASS / 3 CANDIDATE / 117 DEAD" by "0 PASS / 0 CANDIDATE / 120 DEAD (causal key; v0 3 CANDIDATE void)"; keep "fixed cells 0/0/66 (RC family N=186, p=0.035)". The sentence "Profit was predicted <= +0.1 and came out higher (+0.64 PRE)" -> "Profit was predicted <= +0.1; with the causal key the best regime chain is +0.016 PRE; the +0.64 was look-ahead".
3. The "(a)+(e) Profit: top chains" table: replace by the 3-row table of section 2 above (all three DEAD, PRE -0.28/-0.44/-0.32, HOLD -0.44/-0.20/-0.07; N basis negative everywhere); delete the 4th row and "CANDIDATE" labels.
4. "By scope (mean chain PRE): cell +0.36, bookcell -0.04, pooled -0.15, perbook -0.53. Only the 3x3 ... carries the effect" -> "By scope (mean chain PRE, causal): cell -0.36, bookcell -0.55, pooled -0.15, perbook -0.53; no scope carries a positive effect (the +0.36 cell mean was the look-ahead)."
5. Delete the paragraph "Where the gain comes from (top chain, PRE) ..." (replace by: "v0 gain came entirely from ON trades (+0.72 of +0.64 PRE); causal ON contributes -0.19").
6. "Best fixed action per 3x3 cell ..." bullet: replace by "vol_lo+ON take at 50% of target (causal key, previous-day tag): PRE +0.25 (CI -1.75..+2.24, MDE 2.8, n=4,053), X' +1.79, HOLD +3.06 (+0.12..+6.01), L6M +3.28, 2026 +9.41 (n=110, MDE 15.9); N basis PRE -1.17 / HOLD +1.07; shuffled-tag placebo p 0.54 (PRE), RC over 594 cell x action pairs p 0.76 (was 0.027). The v0 +4.27/+3.52/+2.97 was look-ahead [VOID]. Recent-only observation, not a lead." Exploratory A4 sentence -> "F7-only cell chains (causal) PRE +0.14, HOLD +0.38 (best by PRE); N basis <= 0; no LEAD".
7. Distillation: the profit teacher line and the volsplit/bal/unbal table -> section 5 numbers; delete "The table (teacher) beats the distilled rules; it needs a two-token regime" -> "There is no causal profit teacher to distill; the two-token regime request (vol_x+ON|AM|PM) is withdrawn."
8. "Candidate rule text": "profit = 8-rule 3x3 table from the 6m cell chain, WF last-6m +0.40 / all +0.53" -> "profit section EMPTY (causal 6m cell table WF last-6m -0.27 / all -0.29); policy_candidate_exp1.txt and policy_candidates_tables_students.txt profit sections are VOID".
9. Caveats 1 and 2: replace with "1. No profit regime result survives the causal key; the live target-fill measurement is no longer needed to decide the 3x3 table. 2. Profit selection by regime does NOT work (the earlier claim was look-ahead)." Caveats 3-4 unchanged except 4 "none of them reaches 50% retained gain" -> "teacher negative".
10. Cells scored line unchanged (1,526); add "RESCORE_CAUSAL, no new selection".
11. Also stamp the ENSM registry row for the EXP1 lead VOID and mark policy_candidate_exp1.txt profit rules VOID (not done here).
