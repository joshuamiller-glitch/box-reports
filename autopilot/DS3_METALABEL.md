# DS3_METALABEL - take this signal or not: boosting + logit meta-label on path/L2/stack/ES-RTY state (+ EINT1/EINT2 signal-quality, HTF, calendar, day-type tables), META, 2026-10-30

Prereg: l2vast/ds3/prereg/META_prereg.md sha256 eaa7e0936f39a9f87c4cdb96cae73ee2212197d6979c873761996995cd02fa5d (logged in DECISIONS.md before any outcome statistic). PRE-only selection files: FS1 553802bbe4903ea835f7cb5f9d68cc5068a901d6fc4c57fd1eb94a03fc700682, FS2 7bbe88caf4de46449dbf0576d84be3fdd3cee29c35435450c3298a11fe18da60 (both written before the holdout look; one look per feature set). Research only; UNTOUCHED never read. Windows are my own masks capped at 20260206: 2026=20260101..20260206 (~5 real weeks, 6 label weeks: read as a sign only), L6M=20250801..20260206, HOLD=20250701..20260206, PRE=20240201..20250630, X'=20230401..20240131; s48score.WINMASK / vs_lib.WINS (no upper bound) not used; every frame filtered to label day <= 20260206. Code l2vast/ds3/code/meta/, outputs l2vast/ds3/out/meta/{FS1,FS2}/.

## Plain headline (five sentences)
1. **0 PASS and 0 CANDIDATE out of 2,660 configs (1,330 per feature set).** 363 (FS1) and 428 (FS2) are CANDIDATE-RECENT (2026>0 and L6M>0 on the stack), which is what chance produces (share of configs with pts 2026>0 and L6M>0: real 0.21 vs shuffled-feature placebo 0.34 and shuffled-label 0.39 on FS1; real 0.35 vs 0.37 / 0.30 on FS2); White RC best-of-N over the weekly stack delta: FS1 p 0.86 (HOLD) / 0.92 (L6M) / 0.92 (PRE); FS2 p 0.90 / 0.79 / 0.91.
2. **The honest (PRE-selected) pooled line is negative in the recent windows:** FS1 H1 GBM 12m window, skip bottom third / 1.5x top third (risk-matched): stack PRE +12.7k $/wk (MDE 22.0k) -> L6M -12.9k (MDE 35.2k), HOLD -11.4k (32.6k), 2026 -35.8k (73.7k), N-basis -22.5k / -21.0k; FS2 (H4 ensemble, skip bottom 20%): PRE +4.1k (26.1k) -> L6M -9.4k (34.9k), HOLD -8.3k (30.3k). The base stack is +65.7k/wk L6M, +52.4k HOLD, so these are -14% to -22% of the stack, inside the stack MDE (~30-35k) but consistently signed.
3. **Reversal, not noise:** on FS1 every model chain has a positive selection effect in PRE (lot-weighted pts minus unweighted, +0.14..+0.76 pts/trade) and a NEGATIVE one in L6M / HOLD (-0.18..-0.80; the shuffled-feature and shuffled-label placebos average about 0 to +0.1), i.e. the learned ranking turned against the signals after mid-2025 (models drift, as THP_C1). Adding EINT1/EINT2 (HTF, calendar, day type) moves the pooled selection effect to about 0 (H1 +0.02..+0.04, others -0.05..-0.35) but not to a positive: best pooled FS2 line by L6M (looked) is H2 ensemble 1.5x/half/skip +9.5k (MDE 30.6k), HOLD +3.4k, PRE +1.4k, 2026 +18.0k, N-basis L6M -6.2k, fails featshuf (0.20), random (0.12), RC.
4. **Session variants are registered and not killed by the pooled number**: PRE-selected FS1 cells that are CANDIDATE-RECENT with L6M and HOLD >= 0 on the stack are HM-nyam (+3.1k / +3.3k, MDE 10.9k / 10.1k), KB-asia (+0.8k / +1.0k, MDE 4.4k / 3.9k), PE-london (+0.9k / +0.5k), SM-asia (+1.9k / +0.9k), nypm (+1.8k / +1.2k, MDE 2.5k / 2.4k); on FS2 HM-nyam, KB-asia, PE-london, MV-nyam. Every one is inside its MDE (effects are 1-3k $/wk against MDEs of 2.4-11k), none clears the RC (adj p 1.0 per cell) or the shuffled-feature placebo, and several break on the N basis. PE-london TREE_6m skip-20% is >= 0 in L6M and HOLD in both feature sets (FS1 +0.9k / +0.5k with N-basis -1.8k / -1.9k; FS2 +0.5k / +0.9k with N-basis +1.2k / +1.7k), still inside MDE 2.4-4.8k.
5. **The distilled 6-rule tree keeps nothing**: on FS1 the chain it distils has no positive stack gain in L6M for any policy (retained gain n/a for 15 of 15 pooled cells); on FS2 the chain is positive in 5 cells and the tree retains -0.81, -0.49, -1.74, -2.03 and +0.06 of it. Nothing is promoted; the tree for the two PRE-selected scope cells is written as a research candidate (below), NOT live-ready. What drives the models: FS1 gain is L2 0.72-0.76 but the top single features are stack/day state (stk_real_day_pts 4-7% in 2024-25Q2, replaced by on_ratio 5-7% from 2025Q3; vpin50 2-4%, same as L2EA); FS2 gain is EINT1 HTF context 0.55-0.60 (EINT1_htf_gap_eth top in every quarter 2024Q1..2026Q1, 4.6-7.2%), i.e. day-level regime again, which is exactly what drifts.

## What was run (details in the prereg)
- 47,131 ABR signal rows (11 books) x features at the signal second (l2f_at.features_at: 128 numeric L2 columns; errata: prereg said 126, the exclusion rule governs), stack state 7 (other books' positions, unrealised and realised day P&L), ES/RTY concurrent move 5, path/signal state 12 (FS1 = 152 features). FS2 adds EINT1 68 columns (signal strength, VWAP/session/prior-day distances, HTF, confluence cf_same/opp/eng 1/3/5 min; the non-causal cf_future_* and price level px_pre excluded) and EINT2 51 columns (time in session, calendar, event minutes, day-type classes); both EINT markers existed at fit time (EINT1_READY.txt, EINT2_READY.txt) so FS2 contains every group requested: path, L2, signal quality, confluence, HTF, calendar, day type, stack state, ES/RTY.
- No book_code / session / srow / mod_now / tod / E / base_stop / lots / side column is a feature. Diagnostic (descriptive): the FS1 features still identify the book (66% accuracy vs 17% majority) and the session (85% vs 26%) through volume/time-of-day structure, so the "no ids" rule does not remove session gating, only the free id columns; this is why the explicit session splits and the demeaned-label head H4 exist, and why a time-of-day EINT2 feature (dm_*, mins_in_sess) in FS2 is a session proxy by construction.
- Heads: H1 LightGBM regression on net pts (monotone +imb1/2/3/5/10, svpin50, es_imb5/10, -spread_t), H2 LightGBM P(target first), H3 L2 logit on P(target first), H4 regression on (book,session)-demeaned pts. Windows 3m / 6m / 12m / ENS (mean of the three causal ranks); weekly refit (Saturday 00:00 UTC) on trades CLOSED before the refit time; distilled TREE (6 leaves) of H1. Policies P1..P5 (skip bottom 10% / 20% / 33%; half bottom third + 1.5x top third; skip 20% + half next 20% + 1.5x top 20%), causal rank thresholds, risk-matched per book by the causal mean multiplier; scopes: pooled, 5 entry sessions, 8 D6 session cells (KB-asia, PE-london, HM-asia, HM-nyam, SM-asia, SM-london, MV-london, MV-nyam; MV is not in the 6-book engine: pts level only, stack n/a). 1,330 configs per feature set; 132 pipelines per set (12 real + 120 placebo: 5 seeds x {feature shuffle, label shuffle} x 4 heads x 3 windows).
- Errata vs prereg text: (a) a window is "up to W months of closed trades, minimum 300 rows", so all three windows start predicting on 2023-07-03 (the prereg guessed 2024-01 / 2024-07); coverage of X' is 72.5% of trades (the first 3 months have no model), 100% for 2026 / L6M / HOLD / PRE. (b) The stack engine's own P is the library-like price with the engine's costs (the measured fill cost is not in it); the stack lines are therefore on the engine basis ("stack") and on a second basis "stack-N" (engine P + fill_cost_pts on target exits, matched rows); the measured (M, live_pts) and N (live_pts + fill cost on target exits) bases are shown at the pts-per-trade level. (c) Only the matched share of ABR rows (ST 81%, HM 87%, WT 85%, KB 79%, SM 88%, PE(PB) 100%) is scaled in the engine; others keep weight 1. (d) CR has no THP row: N=M and the target label is pts>0.
- Placebos: shuffled-feature and shuffled-label (5 seeds, pts-level E rank per config; TREE configs have no model placebo so the featshuf gate is unevaluable and counts as failed), random skip/half (200 draws pts-level, 20 draws on the lock engine for the top-5 pooled by L6M and the 14 PRE-selected configs).
- Tiers: PASS / CANDIDATE / CANDIDATE-RECENT / DEAD with the gates G1..G9 of the prereg; failed gates are listed in every ranked row. MDE beside every stack and pts number (MDE = 2.8 x s.e. of the weekly delta, or of the per-trade delta). Selection state: rows ranked by L6M are SELECTED ON LOOKED DATA; PRE-selected rows are the honest line.

## Policy / nightly
No PASS or CANDIDATE exists, so nothing is promoted. The two PRE-selected, rule-expressible CANDIDATE-RECENT scope cells with stack >= 0 in L6M and HOLD (KB-asia TREE_12m skip-20%, PE-london TREE_6m skip-20%) are written as threshold rules to l2vast/ds3/out/missed/meta_policy_candidate.txt (features D6 computes: imb5, imb10, delta60, rel_tot8, pulled_sup10; every other feature named exactly in the file header and appended to DS3_THL2_NEEDS.md). One-command nightly re-fit: autopilot/META_nightly.sh [cutoff<=20260206] [FS1|FS2] (= python3 -I l2vast/ds3/code/meta/meta_nightly_refit.py). The model chains (GBM/logit) are not expressible in the THP_POLICY grammar and are not published.


---

### Feature set FS1
Tiers over 1330 configs: DEAD 967, CANDIDATE-RECENT 363. White RC best-of-N over the weekly stack delta of the 1140 engine-affecting configs: HOLD tmax 2.72 p 0.860 (32 wk); L6M tmax 2.57 p 0.915 (28 wk); PRE tmax 2.45 p 0.920 (75 wk).
Stack as is (engine, weekly mean $/wk): 2026 +46.2k, L6M +65.7k, HOLD +52.4k, PRE +44.1k, X' +20.6k; base maxDD L6M +466.4k HOLD +601.0k; base worst-20-weeks HOLD -742.9k; weeks 2026/L6M/HOLD/PRE/X' = 6/28/32/75/44.

**Honest line: PRE-selected config per scope (selection_PRE.json written before the look; stack delta $/wk, MDE in brackets)**

| config | tier | stack d 2026 (MDE) | L6M | HOLD | PRE | X' | stack-N L6M / HOLD | pts/trade L6M (MDE) [n] | HOLD | PRE | N-basis pts L6M | placebo rank featshuf / labshuf / random | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| [PRE-selected HM-asia] `H2_ENS|P3|HM-asia` | DEAD | -2.8k (15.8k) | -9.4k (17.8k) | -9.9k (15.8k) | +5.7k (9.1k) | +0.3k (3.1k) | -8.5k / -10.5k | -4.08 (6.82) [259] | -4.87 (6.57) [289] | +1.64 (4.09) [622] | -4.41 | 0.00 / 0.00 / 0.04 | G2_HOLD,G3_L6M,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected HM-nyam] `H4_ENS|P3|HM-nyam` | CANDIDATE-RECENT | +3.9k (12.2k) | +3.1k (10.9k) | +3.3k (10.1k) | +3.0k (5.1k) | -1.1k (2.0k) | +3.6k / +3.0k | +0.50 (6.47) [223] | -0.45 (6.08) [250] | +4.65 (4.45) [558] | +0.66 | 0.00 / 0.60 / 0.56 | G4_Xp,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected KB-asia] `TREE_12m|P2|KB-asia` | CANDIDATE-RECENT | +0.9k (8.9k) | +0.8k (4.4k) | +1.0k (3.9k) | +0.7k (3.3k) | +0.0k (0.0k) | +0.8k / +1.0k | +0.68 (2.30) [335] | +0.48 (2.09) [371] | +0.07 (2.00) [779] | +0.77 | nan / nan / 0.94 | G4_Xp,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected MV-london] `TREE_6m|P1|MV-london` | DEAD | n/a | n/a | n/a | n/a | n/a | n/a / n/a | +1.36 (2.48) [230] | +1.40 (2.34) [249] | +1.24 (2.96) [548] | +1.66 | nan / nan / 0.97 | G7_featshuf,G9_RC |
| [PRE-selected MV-nyam] `H1_ENS|P3|MV-nyam` | DEAD | n/a | n/a | n/a | n/a | n/a | n/a / n/a | -0.57 (5.72) [330] | +0.15 (5.44) [369] | +1.80 (3.52) [797] | -0.67 | 0.40 / 0.60 / 0.36 | G3_L6M,G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected PE-london] `TREE_6m|P2|PE-london` | CANDIDATE-RECENT | +1.7k (6.5k) | +0.9k (3.9k) | +0.5k (4.8k) | +1.3k (4.7k) | +0.2k (0.5k) | -1.8k / -1.9k | -0.66 (4.82) [221] | -1.15 (4.72) [243] | +1.36 (4.03) [607] | -0.24 | nan / nan / 0.36 | G5_Nbasis,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected POOLED] `H1_12m|P4|POOLED` | DEAD | -35.8k (73.7k) | -12.9k (35.2k) | -11.4k (32.6k) | +12.7k (22.0k) | -2.4k (15.7k) | -22.5k / -21.0k | -0.35 (0.54) [10252] | -0.31 (0.51) [11396] | +0.37 (0.37) [26022] | -0.32 | 0.00 / 0.00 / 0.01 | G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected SM-asia] `H4_3m|P3|SM-asia` | CANDIDATE-RECENT | +6.5k (14.3k) | +1.9k (6.9k) | +0.9k (7.6k) | +1.7k (3.5k) | +0.0k (0.0k) | +1.1k / +0.1k | +3.80 (11.21) [96] | +0.23 (10.70) [113] | +4.94 (6.89) [242] | +4.03 | 1.00 / 0.80 / 0.84 | G4_Xp,G6b_w20,G8_rand,G9_RC |
| [PRE-selected SM-london] `H1_ENS|P1|SM-london` | DEAD | -1.5k (3.1k) | -2.8k (4.2k) | -1.6k (4.2k) | +1.6k (1.8k) | +0.0k (0.0k) | -3.2k / -1.9k | -3.59 (5.23) [84] | -1.62 (5.34) [96] | +2.87 (3.41) [269] | -3.63 | 0.00 / 0.00 / 0.05 | G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected asia] `TREE_3m|P2|asia` | DEAD | -28.5k (54.3k) | -14.8k (31.7k) | -12.1k (30.8k) | +10.4k (17.1k) | +2.7k (9.3k) | -23.9k / -20.9k | -0.70 (1.25) [2854] | -0.40 (1.29) [3205] | +0.10 (0.89) [6689] | -0.61 | nan / nan / 0.01 | G2_HOLD,G3_L6M,G5_Nbasis,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected london] `TREE_6m|P1|london` | DEAD | -19.0k (29.0k) | -3.7k (14.5k) | -2.1k (13.3k) | +5.7k (13.7k) | +0.4k (5.2k) | -2.4k / -1.9k | +0.66 (0.76) [2195] | +0.61 (0.71) [2411] | +1.12 (0.82) [5732] | +0.89 | nan / nan / 0.94 | G2_HOLD,G3_L6M,G5_Nbasis,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected nyam] `H2_12m|P5|nyam` | DEAD | -3.9k (28.2k) | +0.5k (13.2k) | -0.5k (12.1k) | +3.1k (8.1k) | -2.4k (10.3k) | -4.6k / -5.0k | -1.08 (1.26) [2878] | -0.87 (1.18) [3207] | +1.11 (0.96) [6850] | -1.17 | 0.00 / 0.00 / 0.01 | G2_HOLD,G4_Xp,G5_Nbasis,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected nypm] `H4_12m|P1|nypm` | CANDIDATE-RECENT | +3.3k (6.9k) | +1.8k (2.5k) | +1.2k (2.4k) | +3.4k (4.6k) | -0.7k (4.0k) | +0.6k / +0.2k | +0.22 (0.61) [1777] | +0.18 (0.56) [1964] | +0.34 (0.68) [5074] | +0.35 | 1.00 / 0.80 / 0.87 | G4_Xp,G6a_maxDD,G8_rand,G9_RC |
| [PRE-selected pre] `H1_6m|P2|pre` | DEAD | +0.1k (6.0k) | -0.5k (2.2k) | -1.2k (2.1k) | +4.0k (5.8k) | +0.3k (2.9k) | -0.2k / -0.9k | -1.60 (2.41) [525] | -1.73 (2.31) [583] | +1.81 (1.99) [1600] | -1.44 | 0.00 / 0.00 / 0.00 | G2_HOLD,G3_L6M,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |

**Pooled configs ranked by L6M stack delta, HOLD tie-break (top 15) [SELECTED ON LOOKED DATA]**

| config | tier | stack d 2026 (MDE) | L6M | HOLD | PRE | X' | stack-N L6M / HOLD | pts/trade L6M (MDE) [n] | HOLD | PRE | N-basis pts L6M | placebo rank featshuf / labshuf / random | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| #1 `H3_6m|P4|POOLED` | CANDIDATE-RECENT | +6.5k (29.8k) | +5.8k (26.8k) | +2.6k (25.1k) | -4.0k (18.4k) | -2.0k (17.0k) | -5.0k / -7.8k | -0.35 (0.55) [10252] | -0.40 (0.52) [11396] | +0.49 (0.36) [26022] | -0.41 | 0.00 / 0.00 / 0.03 | G1_PRE,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #2 `H2_12m|P3|POOLED` | CANDIDATE-RECENT | +3.3k (92.8k) | +3.3k (30.6k) | +3.1k (27.8k) | -7.1k (18.8k) | +5.7k (25.9k) | -8.5k / -8.1k | -0.34 (0.72) [10252] | -0.22 (0.68) [11396] | +0.24 (0.49) [26022] | -0.25 | 0.20 / 0.00 / 0.04 | G1_PRE,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #3 `H3_12m|P4|POOLED` | DEAD | -16.8k (44.8k) | +3.0k (29.5k) | +3.1k (26.0k) | +1.1k (18.8k) | -3.5k (17.6k) | -8.5k / -10.8k | -0.49 (0.50) [10252] | -0.42 (0.48) [11396] | +0.31 (0.35) [26022] | -0.50 | 0.00 / 0.00 / 0.01 | G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #4 `H2_12m|P5|POOLED` | CANDIDATE-RECENT | +21.8k (66.7k) | +3.0k (29.4k) | +1.4k (26.2k) | -3.0k (22.0k) | +9.0k (26.9k) | -12.4k / -13.2k | -0.29 (0.66) [10252] | -0.14 (0.63) [11396] | +0.41 (0.47) [26022] | -0.23 | 0.00 / 0.20 / 0.06 | G1_PRE,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #5 `H3_ENS|P4|POOLED` | CANDIDATE-RECENT | +3.1k (58.1k) | +1.7k (28.0k) | +1.6k (25.9k) | +2.7k (19.1k) | -0.3k (19.0k) | -8.3k / -7.9k | -0.65 (0.56) [10252] | -0.54 (0.53) [11396] | +0.48 (0.36) [26022] | -0.68 | 0.00 / 0.00 / 0.00 | G4_Xp,G5_Nbasis,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #6 `H3_12m|P1|POOLED` | DEAD | -2.4k (25.9k) | +1.7k (17.7k) | +1.8k (15.5k) | +0.9k (10.1k) | -3.8k (11.0k) | -2.9k / -3.3k | -0.06 (0.30) [10252] | -0.03 (0.29) [11396] | +0.15 (0.21) [26022] | -0.03 | 0.20 / 0.00 / 0.32 | G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| #7 `H2_12m|P1|POOLED` | DEAD | -3.2k (14.4k) | +1.3k (16.0k) | +1.1k (14.4k) | -1.7k (8.0k) | -1.8k (13.7k) | -5.9k / -5.0k | +0.08 (0.28) [10252] | +0.10 (0.27) [11396] | -0.02 (0.17) [26022] | +0.10 | 0.80 / 0.40 / 0.72 | G1_PRE,G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| #8 `H2_12m|P2|POOLED` | DEAD | -10.2k (57.8k) | +0.8k (25.6k) | +2.2k (22.6k) | -4.2k (14.7k) | +1.2k (18.4k) | -4.5k / -3.6k | -0.08 (0.47) [10252] | +0.02 (0.44) [11396] | +0.02 (0.31) [26022] | -0.03 | 0.00 / 0.00 / 0.19 | G1_PRE,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| #9 `H3_12m|P3|POOLED` | DEAD | -17.6k (87.0k) | +0.8k (34.4k) | +2.2k (30.5k) | -6.7k (18.9k) | -6.0k (27.2k) | -19.2k / -16.1k | -0.41 (0.81) [10252] | -0.31 (0.76) [11396] | +0.29 (0.54) [26022] | -0.37 | 0.00 / 0.00 / 0.08 | G1_PRE,G4_Xp,G5_Nbasis,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #10 `H2_12m|P4|POOLED` | DEAD | -15.4k (84.5k) | +0.3k (32.1k) | +1.1k (28.8k) | +0.0k (18.9k) | +3.3k (18.9k) | -14.0k / -13.2k | -0.38 (0.48) [10252] | -0.29 (0.46) [11396] | +0.32 (0.33) [26022] | -0.33 | 0.00 / 0.00 / 0.00 | G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #11 `H3_12m|P2|POOLED` | DEAD | -7.8k (47.0k) | -0.8k (28.0k) | -1.3k (24.8k) | -4.9k (14.8k) | -6.4k (20.2k) | -8.7k / -8.8k | -0.27 (0.52) [10252] | -0.23 (0.50) [11396] | +0.23 (0.35) [26022] | -0.22 | 0.00 / 0.00 / 0.09 | G1_PRE,G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #12 `H3_ENS|P1|POOLED` | DEAD | +13.6k (45.9k) | -1.8k (19.7k) | -1.3k (17.3k) | +0.0k (10.6k) | -3.2k (11.6k) | -5.7k / -6.2k | -0.22 (0.37) [10252] | -0.19 (0.37) [11396] | +0.17 (0.25) [26022] | -0.18 | 0.20 / 0.00 / 0.03 | G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| #13 `H2_3m|P4|POOLED` | DEAD | +5.3k (27.7k) | -2.2k (26.7k) | -5.6k (25.2k) | -7.2k (19.9k) | +5.3k (18.2k) | -12.0k / -14.8k | -0.56 (0.55) [10252] | -0.56 (0.53) [11396] | +0.19 (0.35) [26022] | -0.48 | 0.00 / 0.00 / 0.00 | G1_PRE,G2_HOLD,G3_L6M,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #14 `TREE_6m|P4|POOLED` | DEAD | -23.3k (80.8k) | -2.3k (32.5k) | -3.8k (29.3k) | -4.2k (20.9k) | +6.9k (17.0k) | -3.0k / -5.4k | -0.08 (0.53) [10252] | -0.05 (0.50) [11396] | +0.68 (0.38) [26022] | +0.03 | nan / nan / 0.21 | G1_PRE,G2_HOLD,G3_L6M,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #15 `H4_12m|P1|POOLED` | DEAD | -11.8k (36.7k) | -2.8k (15.7k) | -2.8k (14.0k) | +4.0k (13.6k) | -0.5k (12.8k) | -6.3k / -7.5k | +0.11 (0.30) [10252] | +0.06 (0.28) [11396] | +0.15 (0.26) [26022] | +0.18 | 0.60 / 0.60 / 0.74 | G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |

Worst 3 pooled by L6M (for scale):
- `H4_3m|P3` L6M -44.1k (41.5k), HOLD -42.4k, PRE -9.5k
- `H4_3m|P5` L6M -30.0k (42.0k), HOLD -27.2k, PRE -12.3k
- `H1_3m|P3` L6M -28.5k (46.5k), HOLD -25.5k, PRE -5.4k

**Session variants (14 scopes): best by L6M stack delta (looked) and the PRE-selected config; never killed by the pooled number**

| config | tier | stack d 2026 (MDE) | L6M | HOLD | PRE | X' | stack-N L6M / HOLD | pts/trade L6M (MDE) [n] | HOLD | PRE | N-basis pts L6M | placebo rank featshuf / labshuf / random | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| [best L6M POOLED] `H3_6m|P4|POOLED` | CANDIDATE-RECENT | +6.5k (29.8k) | +5.8k (26.8k) | +2.6k (25.1k) | -4.0k (18.4k) | -2.0k (17.0k) | -5.0k / -7.8k | -0.35 (0.55) [10252] | -0.40 (0.52) [11396] | +0.49 (0.36) [26022] | -0.41 | 0.00 / 0.00 / 0.03 | G1_PRE,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [best L6M asia] `TREE_3m|P4|asia` | CANDIDATE-RECENT | +17.7k (68.6k) | +8.1k (36.0k) | +7.3k (33.0k) | +0.6k (15.5k) | -4.2k (11.0k) | -4.2k / -3.5k | -0.30 (1.10) [2854] | -0.51 (1.07) [3205] | -0.07 (0.72) [6689] | -0.28 | nan / nan / 0.05 | G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| [best L6M london] `H3_12m|P4|london` | CANDIDATE-RECENT | +19.1k (28.1k) | +14.3k (15.5k) | +13.7k (14.1k) | -1.3k (11.2k) | -5.0k (11.7k) | +11.2k / +9.7k | +0.26 (1.10) [2195] | +0.31 (1.04) [2411] | -0.16 (0.72) [5732] | +0.31 | 0.80 / 1.00 / 0.82 | G1_PRE,G4_Xp,G7_featshuf,G8_rand,G9_RC |
| [best L6M pre] `TREE_3m|P5|pre` | CANDIDATE-RECENT | +0.6k (16.3k) | +3.4k (5.7k) | +2.8k (6.7k) | +3.3k (6.7k) | +2.0k (3.7k) | +2.6k / +2.3k | +3.19 (4.31) [525] | +4.53 (4.20) [583] | +2.79 (2.55) [1600] | +3.82 | nan / nan / 0.97 | G7_featshuf,G9_RC |
| [best L6M nyam] `H4_ENS|P5|nyam` | CANDIDATE-RECENT | +10.6k (16.0k) | +7.9k (17.7k) | +6.1k (16.9k) | -5.3k (11.2k) | +1.0k (12.4k) | +5.2k / +3.7k | -1.49 (1.58) [2878] | -1.23 (1.49) [3207] | +0.97 (1.12) [6850] | -1.33 | 0.00 / 0.00 / 0.01 | G1_PRE,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| [best L6M nypm] `H3_3m|P4|nypm` | CANDIDATE-RECENT | +5.5k (11.3k) | +2.8k (4.3k) | +3.4k (4.1k) | +2.4k (5.1k) | -0.1k (5.7k) | +0.6k / +1.9k | -1.02 (1.30) [1777] | -0.68 (1.24) [1964] | +0.57 (0.82) [5074] | -0.83 | 0.20 / 0.00 / 0.05 | G4_Xp,G7_featshuf,G8_rand,G9_RC |
| [best L6M KB-asia] `H3_6m|P4|KB-asia` | CANDIDATE-RECENT | +9.4k (19.3k) | +3.5k (5.7k) | +2.8k (5.1k) | -4.0k (3.8k) | +0.1k (1.3k) | +3.4k / +2.8k | -0.98 (3.60) [335] | -1.35 (3.41) [371] | -0.86 (2.10) [779] | -1.12 | 0.40 / 0.00 / 0.21 | G1_PRE,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [best L6M PE-london] `TREE_3m|P2|PE-london` | CANDIDATE-RECENT | +5.0k (11.6k) | +3.1k (4.1k) | +2.6k (5.2k) | -0.4k (4.1k) | +0.0k (0.0k) | +0.9k / +0.8k | +1.29 (4.32) [221] | +0.38 (4.58) [243] | +0.17 (3.47) [607] | +1.63 | nan / nan / 0.79 | G1_PRE,G4_Xp,G7_featshuf,G8_rand,G9_RC |
| [best L6M HM-asia] `TREE_3m|P4|HM-asia` | CANDIDATE-RECENT | +14.7k (38.5k) | +2.6k (17.6k) | +2.4k (15.7k) | +2.7k (7.3k) | +0.1k (4.1k) | +5.1k / +4.0k | +0.52 (3.82) [259] | +0.03 (3.73) [289] | +0.83 (2.53) [622] | +0.58 | nan / nan / 0.48 | G7_featshuf,G8_rand,G9_RC |
| [best L6M HM-nyam] `H4_6m|P2|HM-nyam` | CANDIDATE-RECENT | +6.3k (18.7k) | +3.7k (8.6k) | +4.3k (7.8k) | -0.4k (3.5k) | -1.2k (2.3k) | +3.4k / +2.7k | +1.04 (4.70) [223] | +0.45 (4.37) [250] | +0.72 (2.79) [558] | +1.02 | 0.40 / 0.80 / 0.76 | G1_PRE,G4_Xp,G7_featshuf,G8_rand,G9_RC |
| [best L6M SM-asia] `H3_6m|P3|SM-asia` | CANDIDATE-RECENT | +7.3k (14.1k) | +3.6k (7.6k) | +1.8k (7.1k) | +0.1k (2.3k) | +0.0k (0.0k) | +3.0k / +1.2k | +3.29 (10.61) [96] | +0.22 (9.74) [113] | +1.80 (4.81) [242] | +3.14 | 1.00 / 0.80 / 0.85 | G4_Xp,G6a_maxDD,G8_rand,G9_RC |
| [best L6M SM-london] `H1_6m|P4|SM-london` | CANDIDATE-RECENT | +4.0k (11.5k) | +1.3k (4.9k) | +1.1k (4.3k) | +0.5k (2.6k) | +0.0k (0.0k) | +0.8k / +0.7k | +1.22 (6.75) [84] | +0.89 (6.44) [96] | +0.41 (3.88) [269] | +1.19 | 0.60 / 1.00 / 0.69 | G4_Xp,G7_featshuf,G8_rand,G9_RC |
| [best L6M MV-london] `TREE_6m|P3|MV-london` | DEAD | n/a | n/a | n/a | n/a | n/a | n/a / n/a | +3.62 (6.52) [230] | +3.89 (6.34) [249] | -0.79 (5.46) [548] | +4.50 | nan / nan / 0.96 | G1_PRE,G7_featshuf,G9_RC |
| [best L6M MV-nyam] `H4_3m|P3|MV-nyam` | CANDIDATE-RECENT | n/a | n/a | n/a | n/a | n/a | n/a / n/a | +3.29 (5.24) [330] | +3.05 (5.22) [369] | +1.76 (3.69) [797] | +3.66 | 0.80 / 0.80 / 0.94 | G4_Xp,G7_featshuf,G8_rand,G9_RC |

Tier counts by scope: POOLED: DEAD 91/CANDIDATE-RECENT 4; asia: DEAD 93/CANDIDATE-RECENT 2; london: DEAD 63/CANDIDATE-RECENT 32; pre: CANDIDATE-RECENT 79/DEAD 16; nyam: DEAD 75/CANDIDATE-RECENT 20; nypm: DEAD 67/CANDIDATE-RECENT 28; KB-asia: DEAD 54/CANDIDATE-RECENT 41; PE-london: DEAD 74/CANDIDATE-RECENT 21; HM-asia: DEAD 91/CANDIDATE-RECENT 4; HM-nyam: DEAD 51/CANDIDATE-RECENT 44; SM-asia: CANDIDATE-RECENT 55/DEAD 40; SM-london: DEAD 90/CANDIDATE-RECENT 5; MV-london: DEAD 87/CANDIDATE-RECENT 8; MV-nyam: DEAD 75/CANDIDATE-RECENT 20

**Selection effect Y (lot-weighted mean pts minus unweighted mean, pts/trade, pooled scope, mean over the 5 policies; MDE per row in the table above)**

| score | Y L6M | Y HOLD | Y PRE | Y X' | E_N L6M (N basis) |
|---|---|---|---|---|---|
| H1_3m | -0.80 | -0.65 | +0.18 | -0.37 | -0.70 |
| H1_6m | -0.68 | -0.62 | +0.39 | -0.23 | -0.67 |
| H1_12m | -0.33 | -0.32 | +0.34 | -0.11 | -0.24 |
| H1_ENS | -0.71 | -0.62 | +0.49 | -0.26 | -0.58 |
| H2_3m | -0.60 | -0.56 | +0.16 | -0.35 | -0.52 |
| H2_6m | -0.50 | -0.55 | +0.31 | -0.09 | -0.50 |
| H2_12m | -0.20 | -0.11 | +0.17 | -0.10 | -0.15 |
| H2_ENS | -0.70 | -0.62 | +0.32 | -0.12 | -0.69 |
| H3_3m | -0.57 | -0.45 | +0.39 | -0.24 | -0.41 |
| H3_6m | -0.35 | -0.40 | +0.45 | -0.44 | -0.38 |
| H3_12m | -0.39 | -0.31 | +0.23 | -0.43 | -0.37 |
| H3_ENS | -0.77 | -0.69 | +0.48 | -0.27 | -0.77 |
| H4_3m | -0.74 | -0.61 | +0.14 | +0.03 | -0.67 |
| H4_6m | -0.59 | -0.61 | +0.26 | -0.08 | -0.53 |
| H4_12m | -0.31 | -0.28 | +0.40 | -0.07 | -0.09 |
| H4_ENS | -0.64 | -0.56 | +0.36 | -0.05 | -0.50 |
| TREE_3m | -0.18 | -0.11 | +0.55 | -0.07 | +0.13 |
| TREE_6m | -0.19 | -0.19 | +0.76 | +0.10 | -0.01 |
| TREE_12m | -0.35 | -0.27 | +0.25 | +0.25 | -0.30 |

**Placebo summary (pooled scope, 16 model scores x 5 policies = 80 configs; mean lot-matched pts/signal E)**

| source | E L6M mean | E HOLD mean | E PRE mean | share with 2026>0 and L6M>0 |
|---|---|---|---|---|
| real | -0.549 | -0.498 | +0.322 | 0.03 |
| featshuf (5 seeds: mean [min,max]) | -0.011 [-0.325,+0.158] | -0.006 | -0.030 | 0.39 |
| labshuf (5 seeds: mean [min,max]) | +0.115 [+0.020,+0.157] | +0.149 | +0.146 | 0.52 |

All 14 scopes: real share of configs with pts 2026>0 and L6M>0 = 0.214; featshuf placebo share = 0.337; labshuf = 0.387. CANDIDATE-RECENT count is therefore about what chance produces (see the shares).

**Random skip/half placebo on the lock engine (20 draws, weights permuted within book x month inside the scope): real stack delta vs draws, L6M / HOLD ($/wk)**

| config | real L6M | draws mean [sd] | rank | real HOLD | draws mean [sd] | rank |
|---|---|---|---|---|---|---|
| `H1_12m|P4|POOLED` | -12.9k | -0.2k [+11.9k] | 0.10 | -11.4k | -1.1k [+10.0k] | 0.15 |
| `H2_12m|P3|POOLED` | +3.3k | -7.3k [+9.6k] | 0.80 | +3.1k | -7.6k [+8.7k] | 0.85 |
| `H2_12m|P5|POOLED` | +3.0k | -7.1k [+6.1k] | 0.90 | +1.4k | -6.7k [+5.9k] | 0.85 |
| `H3_6m|P4|POOLED` | +5.8k | -5.0k [+8.5k] | 0.95 | +2.6k | -4.2k [+7.2k] | 0.90 |
| `H3_12m|P4|POOLED` | +3.0k | -2.9k [+5.8k] | 0.80 | +3.1k | -2.9k [+5.3k] | 0.85 |
| `H3_ENS|P4|POOLED` | +1.7k | -0.7k [+7.7k] | 0.70 | +1.6k | -0.6k [+7.2k] | 0.60 |
| `TREE_3m|P2|asia` | -14.8k | -3.3k [+6.2k] | 0.00 | -12.1k | -2.3k [+5.5k] | 0.05 |
| `TREE_6m|P1|london` | -3.7k | -2.7k [+1.8k] | 0.35 | -2.1k | -1.2k [+1.6k] | 0.35 |
| `H1_6m|P2|pre` | -0.5k | +0.8k [+0.7k] | 0.05 | -1.2k | +0.2k [+0.8k] | 0.05 |
| `H2_12m|P5|nyam` | +0.5k | +1.6k [+2.1k] | 0.30 | -0.5k | +1.2k [+2.3k] | 0.20 |
| `H4_12m|P1|nypm` | +1.8k | +1.2k [+0.5k] | 0.95 | +1.2k | +0.8k [+0.4k] | 0.90 |
| `TREE_12m|P2|KB-asia` | +0.8k | +0.8k [+0.8k] | 0.50 | +1.0k | +1.0k [+0.7k] | 0.50 |
| `TREE_6m|P2|PE-london` | +0.9k | +1.3k [+0.9k] | 0.40 | +0.5k | +1.3k [+0.8k] | 0.15 |
| `H2_ENS|P3|HM-asia` | -9.4k | -1.0k [+5.6k] | 0.05 | -9.9k | -1.1k [+5.2k] | 0.05 |
| `H4_ENS|P3|HM-nyam` | +3.1k | -0.3k [+2.2k] | 1.00 | +3.3k | +0.5k [+2.1k] | 0.90 |
| `H4_3m|P3|SM-asia` | +1.9k | +0.2k [+2.4k] | 0.75 | +0.9k | +0.6k [+2.4k] | 0.60 |
| `H1_ENS|P1|SM-london` | -2.8k | -1.1k [+1.1k] | 0.05 | -1.6k | -1.1k [+1.0k] | 0.35 |
| `TREE_6m|P1|MV-london` | +0.0k | +0.0k [+0.0k] | 0.00 | +0.0k | +0.0k [+0.0k] | 0.00 |
| `H1_ENS|P3|MV-nyam` | +0.0k | +0.0k [+0.0k] | 0.00 | +0.0k | +0.0k [+0.0k] | 0.00 |

**Feature importance (LightGBM gain share)**
- H1 3m last refit (2026-01-31): svpin50 0.033, on_ratio 0.031, stk_real_day_pts 0.030, esnq_corr20m 0.027, t_since_big_against 0.027, d_imb10_1 0.025, vpin50 0.023, d_imb10_30 0.022 | group shares: L2 0.76, STK 0.08, XM 0.09, PATH 0.07
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 stk_real_day_pts 0.043; 2024Q2 on_ratio 0.048; 2024Q3 stk_real_day_pts 0.061; 2024Q4 stk_real_day_pts 0.062; 2025Q1 stk_real_day_pts 0.046; 2025Q2 stk_real_day_pts 0.041; 2025Q3 on_ratio 0.051; 2025Q4 stk_real_day_pts 0.040; 2026Q1 stk_real_day_pts 0.041
- H1 12m last refit (2026-01-31): on_ratio 0.053, rty_nq_div5 0.030, vpin50 0.029, stk_real_day_pts 0.025, stk_n_exited_day 0.023, esnq_corr20m 0.020, svpin50 0.020, d_imb10_5 0.019 | group shares: L2 0.72, STK 0.10, XM 0.09, PATH 0.09
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 stk_real_day_pts 0.048; 2024Q2 stk_real_day_pts 0.044; 2024Q3 stk_real_day_pts 0.056; 2024Q4 stk_real_day_pts 0.071; 2025Q1 stk_real_day_pts 0.075; 2025Q2 stk_real_day_pts 0.069; 2025Q3 on_ratio 0.065; 2025Q4 on_ratio 0.071; 2026Q1 on_ratio 0.060
  - H1 12m quarterly share of the 6 features with the largest mean share:

| feature | 2024Q1 | 2024Q2 | 2024Q3 | 2024Q4 | 2025Q1 | 2025Q2 | 2025Q3 | 2025Q4 | 2026Q1 |
|---|---|---|---|---|---|---|---|---|---|
| stk_real_day_pts | 0.048 | 0.044 | 0.056 | 0.071 | 0.075 | 0.069 | 0.059 | 0.042 | 0.029 |
| on_ratio | 0.046 | 0.040 | 0.049 | 0.057 | 0.055 | 0.046 | 0.065 | 0.071 | 0.060 |
| vpin50 | 0.036 | 0.040 | 0.027 | 0.024 | 0.029 | 0.037 | 0.036 | 0.027 | 0.018 |
| stk_n_exited_day | 0.014 | 0.009 | 0.020 | 0.019 | 0.028 | 0.031 | 0.025 | 0.032 | 0.029 |
| esnq_corr20m | 0.026 | 0.017 | 0.015 | 0.023 | 0.026 | 0.029 | 0.024 | 0.016 | 0.020 |
| es_move20_atr | 0.021 | 0.025 | 0.018 | 0.021 | 0.021 | 0.020 | 0.020 | 0.013 | 0.011 |
- H2 3m last refit (2026-01-31): svpin50 0.039, on_ratio 0.034, t_since_big_against 0.032, stk_real_day_pts 0.030, esnq_corr20m 0.030, atr_ratio 0.026, es_move20_atr 0.021, vpin50 0.020 | group shares: L2 0.73, STK 0.09, XM 0.09, PATH 0.08
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 on_ratio 0.042; 2024Q2 on_ratio 0.047; 2024Q3 stk_real_day_pts 0.051; 2024Q4 stk_real_day_pts 0.062; 2025Q1 on_ratio 0.042; 2025Q2 stk_real_day_pts 0.039; 2025Q3 on_ratio 0.045; 2025Q4 stk_real_day_pts 0.036; 2026Q1 svpin50 0.037
- H2 12m last refit (2026-01-31): on_ratio 0.056, es_move20_atr 0.039, stk_n_opp 0.032, svpin50 0.029, stk_n_exited_day 0.028, atr_ratio 0.027, vpin50 0.026, stk_real_day_pts 0.026 | group shares: L2 0.63, STK 0.14, XM 0.10, PATH 0.13
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 on_ratio 0.057; 2024Q2 on_ratio 0.051; 2024Q3 on_ratio 0.060; 2024Q4 stk_real_day_pts 0.063; 2025Q1 stk_real_day_pts 0.069; 2025Q2 stk_real_day_pts 0.061; 2025Q3 on_ratio 0.061; 2025Q4 on_ratio 0.065; 2026Q1 on_ratio 0.051
- H4 3m last refit (2026-01-31): on_ratio 0.035, esnq_corr20m 0.033, svpin50 0.029, stk_real_day_pts 0.028, d_imb10_1 0.025, d_imb10_30 0.021, refill_t10_ms 0.020, d_imb10_5 0.019 | group shares: L2 0.75, STK 0.09, XM 0.10, PATH 0.07
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 stk_real_day_pts 0.043; 2024Q2 on_ratio 0.045; 2024Q3 stk_real_day_pts 0.059; 2024Q4 stk_real_day_pts 0.062; 2025Q1 on_ratio 0.048; 2025Q2 stk_real_day_pts 0.040; 2025Q3 on_ratio 0.051; 2025Q4 stk_real_day_pts 0.042; 2026Q1 stk_real_day_pts 0.042
- H4 12m last refit (2026-01-31): on_ratio 0.045, rty_nq_div5 0.032, vpin50 0.031, stk_real_day_pts 0.027, stk_unreal_pts 0.022, atr_ratio 0.019, d_imb10_5 0.019, rty_move20_atr 0.019 | group shares: L2 0.74, STK 0.09, XM 0.09, PATH 0.08
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 stk_real_day_pts 0.047; 2024Q2 vpin50 0.043; 2024Q3 stk_real_day_pts 0.054; 2024Q4 stk_real_day_pts 0.068; 2025Q1 stk_real_day_pts 0.073; 2025Q2 stk_real_day_pts 0.067; 2025Q3 on_ratio 0.067; 2025Q4 on_ratio 0.071; 2026Q1 on_ratio 0.056

**Distilled 6-rule version (decision tree, max 6 leaves, fit at each weekly refit to the H1 prediction; features live-computable) vs the model chain it distils (pooled scope, per policy)**

| window | policy | TREE: stack L6M / HOLD / PRE (MDE L6M) | H1 chain: stack L6M / HOLD / PRE | TREE pts L6M | H1 pts L6M | retained gain (TREE/H1, L6M stack) |
|---|---|---|---|---|---|---|
| 3m | P1 | -12.8k / -13.1k / +6.2k (25.1k) | -13.0k / -15.3k / -3.5k | -0.19 | -0.55 | n/a (chain gain <= 0) |
| 3m | P2 | -15.2k / -14.7k / +2.3k (33.8k) | -16.2k / -12.6k / -2.8k | -0.14 | -0.92 | n/a (chain gain <= 0) |
| 3m | P3 | -23.2k / -25.4k / +9.7k (46.1k) | -28.5k / -25.5k / -5.4k | -0.05 | -1.08 | n/a (chain gain <= 0) |
| 3m | P4 | -12.1k / -12.7k / -0.0k (37.7k) | -16.6k / -16.1k / -2.5k | -0.07 | -0.60 | n/a (chain gain <= 0) |
| 3m | P5 | -17.3k / -18.7k / -9.1k (36.1k) | -23.9k / -21.3k / +0.4k | -0.07 | -0.86 | n/a (chain gain <= 0) |
| 6m | P1 | -14.2k / -12.4k / +0.1k (19.5k) | -11.6k / -8.6k / +0.3k | -0.06 | -0.46 | n/a (chain gain <= 0) |
| 6m | P2 | -18.2k / -17.5k / -5.1k (32.6k) | -18.8k / -18.9k / -5.3k | +0.19 | -0.55 | n/a (chain gain <= 0) |
| 6m | P3 | -26.2k / -23.7k / -13.2k (39.1k) | -18.7k / -19.6k / +8.3k | -0.57 | -0.97 | n/a (chain gain <= 0) |
| 6m | P4 | -2.3k / -3.8k / -4.2k (32.5k) | -17.4k / -17.7k / +7.9k | -0.08 | -0.62 | n/a (chain gain <= 0) |
| 6m | P5 | -11.4k / -15.3k / -6.3k (46.1k) | -15.8k / -18.0k / -0.8k | -0.26 | -0.80 | n/a (chain gain <= 0) |
| 12m | P1 | -2.9k / -2.0k / +0.8k (16.4k) | -3.4k / -3.0k / -1.3k | +0.05 | -0.16 | n/a (chain gain <= 0) |
| 12m | P2 | -5.5k / -5.9k / -3.9k (23.4k) | -18.6k / -17.6k / -3.7k | +0.27 | -0.12 | n/a (chain gain <= 0) |
| 12m | P3 | -26.5k / -19.5k / -10.2k (33.7k) | -12.1k / -9.1k / +10.5k | -0.97 | -0.55 | n/a (chain gain <= 0) |
| 12m | P4 | -7.6k / -2.0k / -9.5k (19.8k) | -12.9k / -11.4k / +12.7k | -0.52 | -0.35 | n/a (chain gain <= 0) |
| 12m | P5 | -24.1k / -15.0k / -25.3k (37.8k) | -5.6k / -1.9k / +0.3k | -0.51 | -0.38 | n/a (chain gain <= 0) |

The 6 rules at the last refit (training window n rows, H1 predictions as target; leaf value = predicted pts):

3m:
```
{'t': 1769817600, 'txt': '|--- svpin50 <= 0.04
|   |--- esnq_corr20m <= 0.98
|   |   |--- vol60 <= 76.50
|   |   |   |--- value: [4.54]
|   |   |--- vol60 >  76.50
|   |   |   |--- rel_behind8 <= 1.01
|   |   |   |   |--- value: [0.35]
|   |   |   |--- rel_behind8 >  1.01
|   |   |   |   |--- value: [-4.05]
|   |--- esnq_corr20m >  0.98
|   |   |--- value: [-7.35]
|--- svpin50 >  0.04
|   |--- t_since_big_against <= 965.00
|   |   |--- value: [1.34]
|   |--- t_since_big_against >  965.00
|   |   |--- value: [7.32]
', 'n': 5418}
```

6m:
```
{'t': 1769817600, 'txt': '|--- svpin50 <= 0.04
|   |--- esnq_corr20m <= 0.98
|   |   |--- rty_move20_atr <= -2.71
|   |   |   |--- value: [-2.96]
|   |   |--- rty_move20_atr >  -2.71
|   |   |   |--- stk_real_day_pts <= 390.81
|   |   |   |   |--- value: [1.83]
|   |   |   |--- stk_real_day_pts >  390.81
|   |   |   |   |--- value: [-0.79]
|   |--- esnq_corr20m >  0.98
|   |   |--- value: [-4.07]
|--- svpin50 >  0.04
|   |--- rty_nq_div5 <= 0.27
|   |   |--- value: [3.21]
|   |--- rty_nq_div5 >  0.27
|   |   |--- value: [7.24]
', 'n': 9495}
```

12m:
```
{'t': 1769817600, 'txt': '|--- svpin50 <= 0.03
|   |--- stk_n_exited_day <= 98.50
|   |   |--- on_ratio <= 0.63
|   |   |   |--- value: [-2.75]
|   |   |--- on_ratio >  0.63
|   |   |   |--- value: [-0.02]
|   |--- stk_n_exited_day >  98.50
|   |   |--- value: [-3.56]
|--- svpin50 >  0.03
|   |--- on_ratio <= 0.80
|   |   |--- value: [-0.93]
|   |--- on_ratio >  0.80
|   |   |--- stk_n_exited_day <= 69.50
|   |   |   |--- value: [3.28]
|   |   |--- stk_n_exited_day >  69.50
|   |   |   |--- value: [0.23]
', 'n': 20644}
```

---

### Feature set FS2
Tiers over 1330 configs: DEAD 902, CANDIDATE-RECENT 428. White RC best-of-N over the weekly stack delta of the 1140 engine-affecting configs: HOLD tmax 2.71 p 0.898 (32 wk); L6M tmax 3.22 p 0.793 (28 wk); PRE tmax 2.39 p 0.914 (75 wk).
Stack as is (engine, weekly mean $/wk): 2026 +46.2k, L6M +65.7k, HOLD +52.4k, PRE +44.1k, X' +20.6k; base maxDD L6M +466.4k HOLD +601.0k; base worst-20-weeks HOLD -742.9k; weeks 2026/L6M/HOLD/PRE/X' = 6/28/32/75/44.

**Honest line: PRE-selected config per scope (selection_PRE.json written before the look; stack delta $/wk, MDE in brackets)**

| config | tier | stack d 2026 (MDE) | L6M | HOLD | PRE | X' | stack-N L6M / HOLD | pts/trade L6M (MDE) [n] | HOLD | PRE | N-basis pts L6M | placebo rank featshuf / labshuf / random | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| [PRE-selected HM-asia] `H2_12m|P4|HM-asia` | DEAD | +9.1k (9.9k) | -0.6k (7.9k) | -0.1k (7.0k) | +4.9k (8.2k) | -0.3k (2.5k) | -1.6k / -2.3k | +0.39 (3.06) [259] | +0.00 (2.95) [289] | +2.01 (2.20) [622] | +0.43 | 0.80 / 0.60 / 0.57 | G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected HM-nyam] `TREE_3m|P1|HM-nyam` | CANDIDATE-RECENT | +1.7k (9.8k) | +0.4k (5.6k) | +0.7k (5.1k) | +1.3k (2.5k) | -0.5k (2.0k) | -0.1k / -0.7k | +0.25 (3.06) [223] | -0.16 (2.82) [250] | +1.23 (2.11) [558] | +0.27 | nan / nan / 0.66 | G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected KB-asia] `H1_6m|P5|KB-asia` | CANDIDATE-RECENT | +6.6k (9.4k) | +0.6k (4.1k) | +0.2k (3.7k) | +0.4k (4.7k) | +0.1k (0.9k) | -0.4k / -0.6k | +0.83 (4.97) [335] | -0.07 (4.68) [371] | +1.56 (3.01) [779] | +0.66 | 0.40 / 0.80 / 0.73 | G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected MV-london] `TREE_3m|P3|MV-london` | DEAD | n/a | n/a | n/a | n/a | n/a | n/a / n/a | -3.15 (6.28) [230] | -2.80 (6.15) [249] | +1.95 (5.35) [548] | -2.92 | nan / nan / 0.06 | G2_HOLD,G3_L6M,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected MV-nyam] `TREE_3m|P3|MV-nyam` | CANDIDATE-RECENT | n/a | n/a | n/a | n/a | n/a | n/a / n/a | +2.12 (5.82) [330] | +2.12 (5.58) [369] | +3.46 (3.90) [797] | +2.33 | nan / nan / 0.92 | G7_featshuf,G8_rand,G9_RC |
| [PRE-selected PE-london] `TREE_6m|P2|PE-london` | CANDIDATE-RECENT | +0.2k (4.9k) | +0.5k (2.4k) | +0.9k (3.4k) | +1.7k (4.0k) | +0.0k (0.0k) | +1.2k / +1.7k | +1.53 (3.51) [221] | +1.90 (3.56) [243] | +1.96 (3.00) [607] | +1.74 | nan / nan / 0.81 | G4_Xp,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected POOLED] `H4_ENS|P2|POOLED` | DEAD | -8.6k (70.7k) | -9.4k (34.9k) | -8.3k (30.3k) | +4.1k (26.1k) | -2.3k (22.0k) | -17.4k / -16.5k | -0.32 (0.66) [10252] | -0.33 (0.63) [11396] | +0.06 (0.45) [26022] | -0.26 | 0.20 / 0.20 / 0.07 | G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected SM-asia] `TREE_3m|P2|SM-asia` | DEAD | -0.7k (16.6k) | -2.5k (7.3k) | -2.9k (6.8k) | +1.9k (2.8k) | +0.0k (0.0k) | -3.0k / -3.4k | -1.62 (9.29) [96] | -2.77 (8.71) [113] | +3.93 (6.04) [242] | -1.64 | nan / nan / 0.33 | G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected SM-london] `H2_ENS|P5|SM-london` | DEAD | +1.0k (12.3k) | -4.2k (7.5k) | -2.1k (7.2k) | +2.5k (2.9k) | +0.0k (0.0k) | -4.8k / -2.6k | -5.13 (12.65) [84] | -1.92 (11.94) [96] | +4.71 (6.50) [269] | -5.06 | 0.00 / 0.00 / 0.16 | G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected asia] `H2_6m|P5|asia` | DEAD | +11.8k (80.3k) | -0.6k (29.7k) | -5.7k (27.9k) | +14.4k (20.8k) | +4.3k (16.2k) | -12.5k / -15.0k | +1.17 (1.50) [2854] | +0.56 (1.43) [3205] | +0.54 (0.97) [6689] | +1.22 | 1.00 / 1.00 / 0.93 | G2_HOLD,G3_L6M,G5_Nbasis,G6a_maxDD,G8_rand,G9_RC |
| [PRE-selected london] `TREE_6m|P2|london` | DEAD | -16.0k (28.0k) | -4.0k (18.3k) | -3.0k (18.8k) | +4.7k (14.9k) | +1.1k (8.3k) | +1.1k / +0.3k | +0.27 (1.05) [2195] | +0.40 (1.04) [2411] | +1.48 (0.89) [5732] | +0.43 | nan / nan / 0.62 | G2_HOLD,G3_L6M,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected nyam] `TREE_3m|P3|nyam` | DEAD | +7.8k (40.8k) | -3.1k (20.1k) | -2.5k (18.5k) | +2.8k (14.5k) | -11.9k (15.9k) | +1.2k / +1.4k | -1.17 (1.89) [2878] | -1.44 (1.81) [3207] | +1.89 (1.28) [6850] | -1.08 | nan / nan / 0.16 | G2_HOLD,G3_L6M,G4_Xp,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected nypm] `TREE_12m|P5|nypm` | DEAD | -3.8k (16.5k) | -3.3k (9.8k) | -4.2k (8.8k) | +5.2k (7.8k) | -0.6k (8.4k) | -6.4k / -6.5k | -0.33 (1.81) [1777] | -0.32 (1.66) [1964] | +0.98 (1.09) [5074] | -0.50 | nan / nan / 0.34 | G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| [PRE-selected pre] `H3_6m|P3|pre` | DEAD | +0.7k (12.4k) | -2.6k (4.8k) | -2.0k (4.7k) | +3.1k (7.1k) | -1.7k (5.0k) | -2.9k / -1.9k | -0.71 (4.31) [525] | +0.04 (4.11) [583] | +1.26 (2.84) [1600] | -0.51 | 0.00 / 0.00 / 0.07 | G2_HOLD,G3_L6M,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |

**Pooled configs ranked by L6M stack delta, HOLD tie-break (top 15) [SELECTED ON LOOKED DATA]**

| config | tier | stack d 2026 (MDE) | L6M | HOLD | PRE | X' | stack-N L6M / HOLD | pts/trade L6M (MDE) [n] | HOLD | PRE | N-basis pts L6M | placebo rank featshuf / labshuf / random | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| #1 `H2_ENS|P5|POOLED` | CANDIDATE-RECENT | +18.0k (61.0k) | +9.5k (30.6k) | +3.4k (30.0k) | +1.4k (23.6k) | -7.3k (23.5k) | -6.2k / -12.1k | -0.28 (0.81) [10252] | -0.45 (0.77) [11396] | +0.54 (0.49) [26022] | -0.30 | 0.20 / 0.80 / 0.12 | G4_Xp,G5_Nbasis,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| #2 `H1_6m|P3|POOLED` | CANDIDATE-RECENT | +54.1k (44.0k) | +9.3k (46.0k) | +3.8k (42.9k) | -1.3k (32.3k) | +2.5k (29.7k) | -3.1k / -8.1k | +0.38 (0.96) [10252] | +0.24 (0.91) [11396] | +0.47 (0.62) [26022] | +0.48 | 1.00 / 1.00 / 0.86 | G1_PRE,G5_Nbasis,G6a_maxDD,G8_rand,G9_RC |
| #3 `TREE_12m|P4|POOLED` | DEAD | -17.5k (58.3k) | +8.7k (31.0k) | +1.4k (29.4k) | -2.9k (21.9k) | -3.4k (19.6k) | -3.0k / -9.5k | -0.18 (0.49) [10252] | -0.44 (0.47) [11396] | +0.12 (0.35) [26022] | -0.35 | nan / nan / 0.47 | G1_PRE,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #4 `H3_ENS|P3|POOLED` | CANDIDATE-RECENT | +22.1k (84.6k) | +8.2k (42.7k) | +10.3k (36.6k) | -9.2k (25.2k) | -0.5k (19.5k) | -5.4k / -3.9k | -0.72 (0.95) [10252] | -0.53 (0.91) [11396] | -0.01 (0.62) [26022] | -0.61 | 0.00 / 0.20 / 0.00 | G1_PRE,G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| #5 `H3_12m|P5|POOLED` | DEAD | -13.3k (38.6k) | +7.4k (32.5k) | +4.9k (29.0k) | -6.8k (20.1k) | -3.4k (26.7k) | +0.4k / -2.9k | -0.47 (0.68) [10252] | -0.36 (0.64) [11396] | +0.12 (0.46) [26022] | -0.32 | 0.00 / 0.00 / 0.01 | G1_PRE,G4_Xp,G5_Nbasis,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| #6 `H3_ENS|P4|POOLED` | CANDIDATE-RECENT | +12.2k (84.8k) | +6.5k (34.4k) | +6.0k (31.1k) | +3.5k (17.5k) | -9.3k (14.6k) | -3.8k / -2.5k | -0.66 (0.57) [10252] | -0.51 (0.53) [11396] | +0.07 (0.36) [26022] | -0.59 | 0.00 / 0.20 / 0.00 | G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| #7 `H3_6m|P1|POOLED` | DEAD | -2.0k (51.5k) | +6.5k (20.7k) | +5.0k (19.4k) | -3.8k (11.0k) | -1.5k (10.6k) | +1.7k / -0.5k | +0.45 (0.37) [10252] | +0.39 (0.34) [11396] | +0.07 (0.23) [26022] | +0.47 | 1.00 / 1.00 / 1.00 | G1_PRE,G4_Xp,G5_Nbasis,G9_RC |
| #8 `H1_3m|P5|POOLED` | CANDIDATE-RECENT | +6.2k (68.3k) | +6.4k (37.4k) | +2.4k (33.8k) | -2.7k (31.1k) | -16.5k (31.9k) | -1.4k / -5.3k | +0.10 (0.92) [10252] | -0.04 (0.87) [11396] | +0.36 (0.56) [26022] | +0.21 | 0.80 / 0.60 / 0.61 | G1_PRE,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #9 `H4_3m|P5|POOLED` | CANDIDATE-RECENT | +25.7k (52.0k) | +6.0k (35.9k) | +4.2k (32.1k) | -10.0k (31.2k) | -15.4k (30.9k) | -8.9k / -9.8k | -0.32 (0.92) [10252] | -0.39 (0.87) [11396] | +0.13 (0.57) [26022] | -0.27 | 0.20 / 0.60 / 0.18 | G1_PRE,G4_Xp,G5_Nbasis,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| #10 `H1_6m|P5|POOLED` | CANDIDATE-RECENT | +17.0k (28.2k) | +5.3k (39.7k) | +0.8k (37.2k) | -11.4k (28.6k) | -10.4k (26.4k) | -1.5k / -6.5k | +0.07 (0.83) [10252] | -0.02 (0.79) [11396] | +0.63 (0.56) [26022] | +0.13 | 0.60 / 0.80 / 0.62 | G1_PRE,G4_Xp,G5_Nbasis,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| #11 `H1_12m|P5|POOLED` | CANDIDATE-RECENT | +39.5k (68.3k) | +4.9k (34.6k) | +9.8k (30.9k) | -13.4k (29.3k) | -4.2k (30.0k) | -11.6k / -5.3k | +0.07 (0.76) [10252] | +0.04 (0.72) [11396] | +0.20 (0.53) [26022] | +0.10 | 0.40 / 0.40 / 0.52 | G1_PRE,G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| #12 `H1_3m|P4|POOLED` | CANDIDATE-RECENT | +12.4k (41.1k) | +4.7k (33.4k) | +2.0k (29.6k) | -1.5k (20.7k) | -2.7k (20.3k) | -3.0k / -4.8k | -0.00 (0.60) [10252] | -0.08 (0.57) [11396] | +0.28 (0.37) [26022] | +0.06 | 0.80 / 0.60 / 0.43 | G1_PRE,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #13 `H2_3m|P5|POOLED` | DEAD | -5.7k (66.2k) | +4.7k (36.6k) | +0.3k (33.1k) | -4.1k (23.4k) | -7.9k (31.3k) | -18.9k / -20.9k | -0.40 (0.82) [10252] | -0.56 (0.78) [11396] | +0.32 (0.50) [26022] | -0.36 | 0.20 / 0.40 / 0.08 | G1_PRE,G4_Xp,G5_Nbasis,G6a_maxDD,G6b_w20,G7_featshuf,G8_rand,G9_RC |
| #14 `H2_6m|P4|POOLED` | DEAD | -9.5k (70.6k) | +4.7k (33.7k) | +3.6k (29.7k) | -4.5k (18.0k) | +3.7k (20.0k) | -4.3k / -4.7k | -0.08 (0.50) [10252] | -0.12 (0.48) [11396] | +0.25 (0.33) [26022] | -0.07 | 0.60 / 0.60 / 0.30 | G1_PRE,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| #15 `H4_3m|P1|POOLED` | DEAD | -29.6k (46.9k) | +4.5k (28.6k) | +3.2k (27.5k) | -2.8k (15.8k) | -11.6k (14.3k) | -4.0k / -4.6k | +0.12 (0.44) [10252] | +0.11 (0.42) [11396] | +0.02 (0.28) [26022] | +0.14 | 1.00 / 0.80 / 0.84 | G1_PRE,G4_Xp,G5_Nbasis,G8_rand,G9_RC |

Worst 3 pooled by L6M (for scale):
- `H2_3m|P3` L6M -28.8k (42.5k), HOLD -30.4k, PRE +1.5k
- `TREE_3m|P3` L6M -26.7k (49.1k), HOLD -22.0k, PRE -15.2k
- `H4_3m|P3` L6M -24.4k (46.3k), HOLD -23.0k, PRE -21.8k

**Session variants (14 scopes): best by L6M stack delta (looked) and the PRE-selected config; never killed by the pooled number**

| config | tier | stack d 2026 (MDE) | L6M | HOLD | PRE | X' | stack-N L6M / HOLD | pts/trade L6M (MDE) [n] | HOLD | PRE | N-basis pts L6M | placebo rank featshuf / labshuf / random | failed gates |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| [best L6M POOLED] `H2_ENS|P5|POOLED` | CANDIDATE-RECENT | +18.0k (61.0k) | +9.5k (30.6k) | +3.4k (30.0k) | +1.4k (23.6k) | -7.3k (23.5k) | -6.2k / -12.1k | -0.28 (0.81) [10252] | -0.45 (0.77) [11396] | +0.54 (0.49) [26022] | -0.30 | 0.20 / 0.80 / 0.12 | G4_Xp,G5_Nbasis,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| [best L6M asia] `H1_3m|P5|asia` | CANDIDATE-RECENT | +19.6k (51.0k) | +12.7k (23.5k) | +4.6k (24.9k) | +3.2k (25.3k) | -3.4k (17.5k) | -5.2k / -11.5k | +2.30 (1.79) [2854] | +1.25 (1.71) [3205] | +1.07 (1.10) [6689] | +2.35 | 1.00 / 1.00 / 1.00 | G4_Xp,G5_Nbasis,G6a_maxDD,G9_RC |
| [best L6M london] `H3_3m|P4|london` | CANDIDATE-RECENT | +17.1k (51.7k) | +6.8k (26.7k) | +4.7k (24.1k) | -6.6k (12.7k) | -3.3k (7.2k) | -2.6k / -2.8k | +0.13 (1.22) [2195] | +0.07 (1.16) [2411] | -0.01 (0.77) [5732] | +0.33 | 0.40 / 0.40 / 0.49 | G1_PRE,G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| [best L6M pre] `TREE_3m|P3|pre` | CANDIDATE-RECENT | +1.3k (14.9k) | +5.3k (6.2k) | +3.8k (5.8k) | -5.6k (7.9k) | -0.8k (5.0k) | +3.2k / +1.9k | -0.36 (4.29) [525] | -1.23 (4.01) [583] | -0.62 (2.66) [1600] | -0.32 | nan / nan / 0.87 | G1_PRE,G4_Xp,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| [best L6M nyam] `H3_6m|P2|nyam` | CANDIDATE-RECENT | +24.6k (27.3k) | +13.4k (13.5k) | +11.5k (12.1k) | -2.0k (7.0k) | -2.5k (6.5k) | +8.6k / +6.7k | +0.40 (1.22) [2878] | +0.33 (1.13) [3207] | -0.00 (0.71) [6850] | +0.33 | 0.80 / 1.00 / 0.74 | G1_PRE,G4_Xp,G6a_maxDD,G7_featshuf,G8_rand,G9_RC |
| [best L6M nypm] `H4_3m|P1|nypm` | CANDIDATE-RECENT | +1.5k (8.6k) | +4.5k (5.8k) | +3.7k (5.2k) | -0.3k (3.9k) | -3.0k (4.7k) | +3.0k / +2.6k | +0.69 (0.86) [1777] | +0.67 (0.79) [1964] | -0.57 (0.64) [5074] | +0.76 | 1.00 / 1.00 / 1.00 | G1_PRE,G4_Xp,G6a_maxDD,G9_RC |
| [best L6M KB-asia] `H1_3m|P5|KB-asia` | CANDIDATE-RECENT | +9.6k (8.8k) | +4.0k (4.8k) | +2.6k (5.0k) | -2.0k (4.0k) | +0.4k (1.9k) | +3.6k / +2.2k | +1.87 (5.64) [335] | +0.68 (5.45) [371] | +0.39 (3.19) [779] | +1.64 | 1.00 / 0.80 / 0.87 | G1_PRE,G8_rand,G9_RC |
| [best L6M PE-london] `H3_3m|P2|PE-london` | CANDIDATE-RECENT | +3.6k (9.4k) | +1.7k (3.9k) | +1.9k (5.3k) | +0.6k (4.2k) | +0.0k (0.0k) | -0.1k / +0.2k | -1.34 (4.71) [221] | -0.21 (4.75) [243] | +2.15 (3.50) [607] | -1.14 | 0.20 / 0.20 / 0.14 | G4_Xp,G5_Nbasis,G7_featshuf,G8_rand,G9_RC |
| [best L6M HM-asia] `H1_3m|P5|HM-asia` | CANDIDATE-RECENT | +22.8k (20.9k) | +15.4k (13.4k) | +12.5k (12.9k) | +3.2k (8.6k) | +0.9k (2.7k) | +13.3k / +9.2k | +6.25 (6.21) [259] | +3.91 (6.02) [289] | +2.97 (3.87) [622] | +6.37 | 1.00 / 1.00 / 0.99 | G6a_maxDD,G9_RC |
| [best L6M HM-nyam] `H1_6m|P3|HM-nyam` | DEAD | -4.5k (6.5k) | +5.3k (9.2k) | +5.8k (8.9k) | -0.9k (4.9k) | -0.9k (3.2k) | +5.9k / +5.9k | +4.35 (7.04) [223] | +5.10 (6.70) [250] | -1.53 (4.06) [558] | +4.34 | 1.00 / 1.00 / 0.98 | G1_PRE,G4_Xp,G6a_maxDD,G9_RC |
| [best L6M SM-asia] `H1_12m|P4|SM-asia` | CANDIDATE-RECENT | +3.0k (8.7k) | +3.3k (5.1k) | +3.6k (5.2k) | +0.1k (1.9k) | +0.0k (0.0k) | +2.6k / +3.0k | +3.87 (5.75) [96] | +3.62 (5.51) [113] | +1.04 (3.73) [242] | +4.04 | 1.00 / 1.00 / 0.97 | G4_Xp,G9_RC |
| [best L6M SM-london] `TREE_12m|P4|SM-london` | CANDIDATE-RECENT | +3.5k (6.0k) | +1.8k (2.4k) | +1.7k (2.5k) | -1.9k (2.2k) | +0.0k (0.0k) | +1.5k / +1.5k | +3.00 (6.02) [84] | +2.01 (5.92) [96] | -1.83 (3.81) [269] | +2.95 | nan / nan / 0.92 | G1_PRE,G4_Xp,G7_featshuf,G8_rand,G9_RC |
| [best L6M MV-london] `H4_12m|P3|MV-london` | CANDIDATE-RECENT | n/a | n/a | n/a | n/a | n/a | n/a / n/a | +3.25 (6.27) [230] | +3.06 (6.07) [249] | +1.77 (4.43) [548] | +3.66 | 0.80 / 1.00 / 0.94 | G7_featshuf,G8_rand,G9_RC |
| [best L6M MV-nyam] `TREE_3m|P2|MV-nyam` | CANDIDATE-RECENT | n/a | n/a | n/a | n/a | n/a | n/a / n/a | +2.31 (4.03) [330] | +2.60 (3.92) [369] | +2.78 (2.67) [797] | +2.44 | nan / nan / 0.97 | G4_Xp,G7_featshuf,G9_RC |

Tier counts by scope: POOLED: DEAD 75/CANDIDATE-RECENT 20; asia: DEAD 76/CANDIDATE-RECENT 19; london: DEAD 89/CANDIDATE-RECENT 6; pre: DEAD 71/CANDIDATE-RECENT 24; nyam: CANDIDATE-RECENT 62/DEAD 33; nypm: CANDIDATE-RECENT 48/DEAD 47; KB-asia: DEAD 49/CANDIDATE-RECENT 46; PE-london: DEAD 88/CANDIDATE-RECENT 7; HM-asia: CANDIDATE-RECENT 50/DEAD 45; HM-nyam: DEAD 49/CANDIDATE-RECENT 46; SM-asia: DEAD 54/CANDIDATE-RECENT 41; SM-london: DEAD 88/CANDIDATE-RECENT 7; MV-london: DEAD 59/CANDIDATE-RECENT 36; MV-nyam: DEAD 79/CANDIDATE-RECENT 16

**Selection effect Y (lot-weighted mean pts minus unweighted mean, pts/trade, pooled scope, mean over the 5 policies; MDE per row in the table above)**

| score | Y L6M | Y HOLD | Y PRE | Y X' | E_N L6M (N basis) |
|---|---|---|---|---|---|
| H1_3m | +0.03 | -0.02 | +0.21 | -0.38 | +0.11 |
| H1_6m | +0.02 | -0.02 | +0.34 | -0.18 | +0.10 |
| H1_12m | +0.04 | +0.06 | +0.12 | -0.10 | +0.11 |
| H1_ENS | -0.05 | -0.08 | +0.29 | -0.30 | +0.02 |
| H2_3m | -0.34 | -0.45 | +0.22 | -0.27 | -0.33 |
| H2_6m | -0.06 | -0.12 | +0.24 | +0.03 | -0.01 |
| H2_12m | +0.11 | +0.04 | +0.35 | -0.12 | +0.19 |
| H2_ENS | -0.15 | -0.29 | +0.33 | -0.16 | -0.18 |
| H3_3m | -0.29 | -0.11 | -0.02 | -0.42 | -0.22 |
| H3_6m | -0.10 | -0.14 | +0.08 | -0.32 | -0.10 |
| H3_12m | -0.13 | -0.05 | +0.14 | -0.29 | -0.02 |
| H3_ENS | -0.35 | -0.24 | +0.08 | -0.38 | -0.27 |
| H4_3m | -0.10 | -0.16 | -0.07 | -0.42 | -0.06 |
| H4_6m | -0.07 | -0.04 | +0.20 | +0.07 | +0.04 |
| H4_12m | +0.05 | +0.04 | +0.27 | +0.07 | +0.20 |
| H4_ENS | -0.26 | -0.28 | +0.26 | -0.07 | -0.20 |
| TREE_3m | -0.74 | -0.67 | +0.46 | -1.20 | -0.66 |
| TREE_6m | -0.48 | -0.47 | +0.64 | -0.25 | -0.32 |
| TREE_12m | -0.34 | -0.53 | +0.14 | -0.49 | -0.40 |

**Placebo summary (pooled scope, 16 model scores x 5 policies = 80 configs; mean lot-matched pts/signal E)**

| source | E L6M mean | E HOLD mean | E PRE mean | share with 2026>0 and L6M>0 |
|---|---|---|---|---|
| real | -0.095 | -0.115 | +0.187 | 0.39 |
| featshuf (5 seeds: mean [min,max]) | -0.007 [-0.279,+0.167] | -0.024 | -0.041 | 0.47 |
| labshuf (5 seeds: mean [min,max]) | -0.062 [-0.256,+0.125] | -0.033 | +0.107 | 0.33 |

All 14 scopes: real share of configs with pts 2026>0 and L6M>0 = 0.348; featshuf placebo share = 0.373; labshuf = 0.301. CANDIDATE-RECENT count is therefore about what chance produces (see the shares).

**Random skip/half placebo on the lock engine (20 draws, weights permuted within book x month inside the scope): real stack delta vs draws, L6M / HOLD ($/wk)**

| config | real L6M | draws mean [sd] | rank | real HOLD | draws mean [sd] | rank |
|---|---|---|---|---|---|---|
| `H1_6m|P3|POOLED` | +9.3k | -12.2k [+12.5k] | 0.95 | +3.8k | -11.1k [+10.5k] | 0.95 |
| `H2_ENS|P5|POOLED` | +9.5k | -8.7k [+6.8k] | 1.00 | +3.4k | -6.8k [+5.9k] | 1.00 |
| `H3_12m|P5|POOLED` | +7.4k | -5.7k [+7.2k] | 0.95 | +4.9k | -5.2k [+6.4k] | 0.95 |
| `H3_ENS|P3|POOLED` | +8.2k | -12.6k [+8.4k] | 0.95 | +10.3k | -10.9k [+6.0k] | 1.00 |
| `H4_ENS|P2|POOLED` | -9.4k | -3.8k [+10.1k] | 0.25 | -8.3k | -4.0k [+9.8k] | 0.25 |
| `TREE_12m|P4|POOLED` | +8.7k | -1.1k [+8.4k] | 0.80 | +1.4k | -1.4k [+8.3k] | 0.60 |
| `H2_6m|P5|asia` | -0.6k | -2.0k [+6.2k] | 0.55 | -5.7k | -1.6k [+5.9k] | 0.30 |
| `TREE_6m|P2|london` | -4.0k | -2.3k [+3.2k] | 0.40 | -3.0k | -1.4k [+3.2k] | 0.45 |
| `H3_6m|P3|pre` | -2.6k | +1.2k [+1.5k] | 0.00 | -2.0k | +1.1k [+1.6k] | 0.05 |
| `TREE_3m|P3|nyam` | -3.1k | -3.3k [+4.4k] | 0.65 | -2.5k | -3.0k [+4.9k] | 0.50 |
| `TREE_12m|P5|nypm` | -3.3k | +0.9k [+2.1k] | 0.00 | -4.2k | -0.0k [+1.9k] | 0.00 |
| `H1_6m|P5|KB-asia` | +0.6k | +0.0k [+1.7k] | 0.65 | +0.2k | +0.3k [+1.7k] | 0.50 |
| `TREE_6m|P2|PE-london` | +0.5k | +0.7k [+0.8k] | 0.45 | +0.9k | +0.9k [+0.8k] | 0.65 |
| `H2_12m|P4|HM-asia` | -0.6k | -1.5k [+2.9k] | 0.60 | -0.1k | -1.0k [+2.7k] | 0.65 |
| `TREE_3m|P1|HM-nyam` | +0.4k | +0.7k [+0.9k] | 0.30 | +0.7k | +1.0k [+0.8k] | 0.35 |
| `TREE_3m|P2|SM-asia` | -2.5k | +1.3k [+1.7k] | 0.00 | -2.9k | +1.6k [+1.7k] | 0.00 |
| `H2_ENS|P5|SM-london` | -4.2k | -1.6k [+1.6k] | 0.05 | -2.1k | -1.3k [+1.5k] | 0.35 |
| `TREE_3m|P3|MV-london` | +0.0k | +0.0k [+0.0k] | 0.00 | +0.0k | +0.0k [+0.0k] | 0.00 |
| `TREE_3m|P3|MV-nyam` | +0.0k | +0.0k [+0.0k] | 0.00 | +0.0k | +0.0k [+0.0k] | 0.00 |

**Feature importance (LightGBM gain share)**
- H1 3m last refit (2026-01-31): EINT1_htf_tr50 0.045, EINT1_htf_gap_eth 0.039, stk_real_day_pts 0.034, EINT1_sd_pdrth_lo 0.025, EINT1_htf_wk_open_atr 0.024, EINT1_htf_d_open_atr 0.024, EINT1_htf_pd_range_atr 0.023, EINT1_htf_on_range_atr 0.022 | group shares: L2 0.21, STK 0.05, XM 0.02, PATH 0.02, EINT1 0.60, EINT2 0.11
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 stk_real_day_pts 0.041; 2024Q2 EINT1_htf_gap_eth 0.039; 2024Q3 EINT1_htf_pd_pos 0.043; 2024Q4 EINT1_htf_gap_eth 0.053; 2025Q1 EINT1_htf_gap_eth 0.046; 2025Q2 EINT1_htf_gap_eth 0.034; 2025Q3 EINT1_htf_tr50 0.053; 2025Q4 EINT1_htf_gap_eth 0.052; 2026Q1 EINT1_htf_gap_eth 0.067
- H1 12m last refit (2026-01-31): EINT1_htf_gap_eth 0.046, EINT1_htf_wk_open_atr 0.036, EINT1_rg_prior_rth_range 0.030, on_ratio 0.029, EINT1_htf_tr50 0.029, EINT1_sd_sess_lo_atr 0.025, atr_ratio 0.024, EINT2_gap_r 0.021 | group shares: L2 0.17, STK 0.03, XM 0.03, PATH 0.06, EINT1 0.55, EINT2 0.14
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 EINT1_htf_gap_eth 0.061; 2024Q2 EINT1_htf_gap_eth 0.072; 2024Q3 EINT1_htf_gap_eth 0.046; 2024Q4 EINT1_htf_gap_eth 0.054; 2025Q1 EINT1_htf_gap_eth 0.062; 2025Q2 EINT1_htf_gap_eth 0.069; 2025Q3 EINT1_htf_gap_eth 0.051; 2025Q4 EINT1_htf_gap_eth 0.048; 2026Q1 EINT1_htf_gap_eth 0.046
  - H1 12m quarterly share of the 6 features with the largest mean share:

| feature | 2024Q1 | 2024Q2 | 2024Q3 | 2024Q4 | 2025Q1 | 2025Q2 | 2025Q3 | 2025Q4 | 2026Q1 |
|---|---|---|---|---|---|---|---|---|---|
| EINT1_htf_gap_eth | 0.061 | 0.072 | 0.046 | 0.054 | 0.062 | 0.069 | 0.051 | 0.048 | 0.046 |
| EINT1_htf_tr50 | 0.050 | 0.037 | 0.032 | 0.036 | 0.036 | 0.021 | 0.041 | 0.043 | 0.031 |
| EINT1_htf_tr20 | 0.038 | 0.051 | 0.045 | 0.029 | 0.029 | 0.036 | 0.026 | 0.019 | 0.012 |
| EINT1_htf_wk_open_atr | 0.025 | 0.023 | 0.029 | 0.033 | 0.031 | 0.029 | 0.034 | 0.032 | 0.032 |
| EINT1_rg_prior_rth_range | 0.036 | 0.032 | 0.023 | 0.023 | 0.023 | 0.019 | 0.029 | 0.034 | 0.036 |
| stk_real_day_pts | 0.035 | 0.025 | 0.020 | 0.028 | 0.030 | 0.030 | 0.019 | 0.015 | 0.014 |
- H2 3m last refit (2026-01-31): EINT1_htf_gap_eth 0.049, EINT1_htf_tr50 0.045, stk_real_day_pts 0.034, EINT2_mins_in_sess 0.027, EINT1_htf_d_open_atr 0.024, EINT1_htf_on_range_atr 0.024, EINT1_htf_wk_open_atr 0.023, EINT1_sd_pdrth_lo 0.022 | group shares: L2 0.22, STK 0.05, XM 0.03, PATH 0.03, EINT1 0.54, EINT2 0.15
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 stk_real_day_pts 0.033; 2024Q2 EINT1_htf_gap_eth 0.035; 2024Q3 EINT1_htf_gap_eth 0.039; 2024Q4 EINT1_htf_gap_eth 0.051; 2025Q1 EINT1_htf_gap_eth 0.042; 2025Q2 EINT1_htf_gap_eth 0.034; 2025Q3 EINT1_htf_tr50 0.039; 2025Q4 EINT1_htf_gap_eth 0.052; 2026Q1 EINT1_htf_gap_eth 0.070
- H2 12m last refit (2026-01-31): EINT1_htf_gap_eth 0.044, on_ratio 0.033, atr_ratio 0.031, EINT1_rg_prior_rth_range 0.029, EINT1_htf_tr50 0.029, EINT2_dm_1000 0.029, EINT1_fh_over_atr 0.027, EINT2_or60_ratio 0.025 | group shares: L2 0.17, STK 0.02, XM 0.02, PATH 0.07, EINT1 0.53, EINT2 0.19
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 EINT1_htf_tr50 0.050; 2024Q2 EINT1_htf_gap_eth 0.050; 2024Q3 EINT1_htf_gap_eth 0.043; 2024Q4 EINT1_htf_gap_eth 0.051; 2025Q1 EINT1_htf_gap_eth 0.059; 2025Q2 EINT1_htf_gap_eth 0.056; 2025Q3 EINT1_htf_gap_eth 0.044; 2025Q4 EINT1_htf_gap_eth 0.040; 2026Q1 EINT1_htf_gap_eth 0.047
- H4 3m last refit (2026-01-31): stk_real_day_pts 0.042, EINT1_htf_gap_eth 0.041, EINT1_htf_tr50 0.041, EINT1_sd_pdrth_lo 0.028, EINT1_htf_d_open_atr 0.028, EINT1_htf_wk_open_atr 0.026, EINT1_htf_on_range_atr 0.022, EINT1_sig_st1_age 0.021 | group shares: L2 0.20, STK 0.06, XM 0.02, PATH 0.02, EINT1 0.60, EINT2 0.10
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 stk_real_day_pts 0.040; 2024Q2 EINT1_htf_gap_eth 0.042; 2024Q3 EINT1_htf_pd_pos 0.043; 2024Q4 EINT1_htf_gap_eth 0.054; 2025Q1 EINT1_htf_gap_eth 0.048; 2025Q2 EINT1_htf_gap_eth 0.035; 2025Q3 EINT1_htf_tr50 0.055; 2025Q4 EINT1_htf_gap_eth 0.051; 2026Q1 EINT1_htf_gap_eth 0.064
- H4 12m last refit (2026-01-31): EINT1_htf_gap_eth 0.039, EINT1_htf_wk_open_atr 0.034, EINT1_rg_prior_rth_range 0.032, EINT1_htf_tr50 0.030, on_ratio 0.030, EINT1_htf_d_open_atr 0.026, EINT1_sd_pd_lo 0.022, EINT2_or60_ratio 0.021 | group shares: L2 0.15, STK 0.03, XM 0.03, PATH 0.05, EINT1 0.58, EINT2 0.15
  - drift by quarter, top feature per quarter (mean gain share): 2024Q1 EINT1_htf_gap_eth 0.060; 2024Q2 EINT1_htf_gap_eth 0.073; 2024Q3 EINT1_htf_gap_eth 0.046; 2024Q4 EINT1_htf_gap_eth 0.055; 2025Q1 EINT1_htf_gap_eth 0.065; 2025Q2 EINT1_htf_gap_eth 0.068; 2025Q3 EINT1_htf_gap_eth 0.050; 2025Q4 EINT1_htf_gap_eth 0.047; 2026Q1 EINT1_htf_gap_eth 0.049

**Distilled 6-rule version (decision tree, max 6 leaves, fit at each weekly refit to the H1 prediction; features live-computable) vs the model chain it distils (pooled scope, per policy)**

| window | policy | TREE: stack L6M / HOLD / PRE (MDE L6M) | H1 chain: stack L6M / HOLD / PRE | TREE pts L6M | H1 pts L6M | retained gain (TREE/H1, L6M stack) |
|---|---|---|---|---|---|---|
| 3m | P1 | -1.6k / -3.1k / +2.4k (24.7k) | -0.0k / +1.5k / -4.0k | -0.04 | -0.04 | n/a (chain gain <= 0) |
| 3m | P2 | -21.2k / -15.7k / -2.1k (32.2k) | -3.9k / -3.0k / -3.4k | -0.80 | -0.04 | n/a (chain gain <= 0) |
| 3m | P3 | -26.7k / -22.0k / -15.2k (49.1k) | -16.7k / -17.2k / -0.9k | -1.72 | +0.25 | n/a (chain gain <= 0) |
| 3m | P4 | -3.8k / -3.2k / -8.0k (35.8k) | +4.7k / +2.0k / -1.5k | -0.62 | -0.00 | -0.81 |
| 3m | P5 | -3.1k / -0.0k / -14.5k (44.6k) | +6.4k / +2.4k / -2.7k | -0.54 | +0.10 | -0.49 |
| 6m | P1 | -3.6k / -4.6k / +2.6k (23.1k) | -2.0k / -0.7k / -4.4k | -0.02 | -0.15 | n/a (chain gain <= 0) |
| 6m | P2 | -10.7k / -7.0k / +0.0k (28.1k) | -3.1k / -3.6k / -6.4k | -0.43 | -0.18 | n/a (chain gain <= 0) |
| 6m | P3 | -16.2k / -13.2k / -7.3k (40.9k) | +9.3k / +3.8k / -1.3k | -0.84 | +0.38 | -1.74 |
| 6m | P4 | -7.8k / -9.0k / -1.8k (25.4k) | -0.8k / -4.3k / +1.7k | -0.46 | +0.07 | n/a (chain gain <= 0) |
| 6m | P5 | -10.7k / -11.5k / -5.6k (35.4k) | +5.3k / +0.8k / -11.4k | -0.59 | +0.07 | -2.03 |
| 12m | P1 | -4.3k / -3.7k / +2.3k (22.1k) | -2.4k / -2.9k / -4.3k | +0.03 | +0.08 | n/a (chain gain <= 0) |
| 12m | P2 | -15.6k / -14.4k / -6.6k (28.3k) | -2.2k / +2.4k / -4.0k | -0.37 | -0.00 | n/a (chain gain <= 0) |
| 12m | P3 | -13.9k / -22.9k / -7.2k (47.6k) | -2.8k / +0.0k / -7.4k | -1.09 | +0.20 | n/a (chain gain <= 0) |
| 12m | P4 | +8.7k / +1.4k / -2.9k (31.0k) | -2.3k / +2.4k / -7.5k | -0.18 | -0.07 | n/a (chain gain <= 0) |
| 12m | P5 | +0.3k / -4.0k / -2.8k (33.1k) | +4.9k / +9.8k / -13.4k | -0.13 | +0.07 | 0.06 |

The 6 rules at the last refit (training window n rows, H1 predictions as target; leaf value = predicted pts):

3m:
```
{'t': 1769817600, 'txt': '|--- EINT1_htf_tr50 <= -0.86
|   |--- EINT1_sd_pd_hi <= 521.25
|   |   |--- EINT1_htf_d_open_atr <= 1.02
|   |   |   |--- value: [10.12]
|   |   |--- EINT1_htf_d_open_atr >  1.02
|   |   |   |--- value: [-5.30]
|   |--- EINT1_sd_pd_hi >  521.25
|   |   |--- value: [-13.46]
|--- EINT1_htf_tr50 >  -0.86
|   |--- EINT1_mins_in_session <= 74.50
|   |   |--- value: [-6.68]
|   |--- EINT1_mins_in_session >  74.50
|   |   |--- EINT1_htf_gap_eth <= 0.01
|   |   |   |--- value: [-3.43]
|   |   |--- EINT1_htf_gap_eth >  0.01
|   |   |   |--- value: [9.59]
', 'n': 5418}
```

6m:
```
{'t': 1769817600, 'txt': '|--- EINT1_sig_st1_age <= 57.50
|   |--- EINT1_htf_gap_eth <= 0.06
|   |   |--- EINT1_rg_prior_rth_range <= 668.12
|   |   |   |--- EINT2_mins_in_sess <= 30.22
|   |   |   |   |--- value: [-3.97]
|   |   |   |--- EINT2_mins_in_sess >  30.22
|   |   |   |   |--- value: [0.91]
|   |   |--- EINT1_rg_prior_rth_range >  668.12
|   |   |   |--- value: [-12.71]
|   |--- EINT1_htf_gap_eth >  0.06
|   |   |--- EINT1_htf_gap_rth <= 0.68
|   |   |   |--- value: [8.97]
|   |   |--- EINT1_htf_gap_rth >  0.68
|   |   |   |--- value: [-6.10]
|--- EINT1_sig_st1_age >  57.50
|   |--- value: [7.39]
', 'n': 9495}
```

12m:
```
{'t': 1769817600, 'txt': '|--- EINT1_rg_prior_rth_range <= 138.25
|   |--- value: [6.35]
|--- EINT1_rg_prior_rth_range >  138.25
|   |--- EINT1_htf_gap_eth <= 0.05
|   |   |--- on_ratio <= 0.52
|   |   |   |--- value: [-9.14]
|   |   |--- on_ratio >  0.52
|   |   |   |--- EINT1_sd_sess_lo <= -548.50
|   |   |   |   |--- value: [-7.65]
|   |   |   |--- EINT1_sd_sess_lo >  -548.50
|   |   |   |   |--- value: [-0.45]
|   |--- EINT1_htf_gap_eth >  0.05
|   |   |--- atr_ratio <= 1.26
|   |   |   |--- value: [8.64]
|   |   |--- atr_ratio >  1.26
|   |   |   |--- value: [0.01]
', 'n': 20644}
```
