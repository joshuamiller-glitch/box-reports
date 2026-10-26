# REPORT PAIR_XENGINE - the pair's order books through exec_engine_x (v3-x), 1-second grid, two-book account (2026-10-17)
**Verdict: the pair-side resting-order books are NO under the engine with the pair account layer. SE1 limit cells NO, K96 NO (sign flips vs the stand-in), K96b and PA3 LEAD -> NO (H1 and H2 uplift turns negative; no cell of the 15-cell PA3 grid or K96b has uplift >= +0.10 on all three spans under ECON). The market-entry control is reproduced to +0.00/-0.02/+0.06 weekly Sharpe (clean/H1/H2) of the live pair 1.46/2.83/2.48 once the book rule is ooat per book and the NT8 lot netting is applied to ENGINE trades; the engine's own rule `rev` does NOT reproduce the live netting (control -0.81/+0.24/-0.34).** Family H on exec_engine v2: same gate-3 set as the v1 run (T3 0 of 140, V1 7 of 90); no verdict changes.

## 1. Engine checks
- exec_engine_x with every extension off equals exec_engine v2: `test_exec_engine_x.py` T0 re-run today, 160 programs (events and trades identical), T1-T9 pass (ALL X TESTS PASSED).
- Market: NQ 1-second rows (46.05M rows; only seconds with prints), open of a row = previous second's close (the same continuity assumption as the old gap logic), minute-bar opens exact on the first row of each minute; session flat at the last second of the block bar; bracket 60/60 relative to the entry price (equal to the fill price at zero engine slippage); engine slippage 0 and the account charges the live 1 tick per side + $34.88 per 8 lots, as in every earlier pair-side run, so deltas are comparable to the old reports.
- Conventions: `LIVE` = MECH (touch fills, no 1-tick-through requirement), used only to reconcile the control; `ECON` = limit entries and targets need >= 1 tick through (stops and gaps as in v2). MECH fills a stop-ENTRY order at its price even when the market is already beyond it (a marketable buy-stop below the market fills below the market), so LIVE numbers for K96/K96b/PA3 (+1.3 to +2.3 uplift, Sharpe 3-4) are an artefact and are NOT scored; ECON fills such orders at the gap/open.

## 2. Does the two-book account reproduce the live pair? (market-entry control, 50,199 signals, 13,221 engine trades)
| control variant | clean | H1 | H2 | all-in | net |
|---|---|---|---|---|---|
| LIVE pair (b11_nt8, asserted) | 1.46 | 2.83 | 2.48 | 1.90 | $2.870M |
| engine_x, per-book `ooat` (= the live busy rule) + NT8 lot netting on engine trades, LIVE fills | 1.46 | 2.81 | 2.54 | 1.91 | $2.961M |
| same, ECON fills (1 tick through for targets) | 1.44 | 2.99 | 2.49 | 1.91 | $2.896M |
| engine_x rule `rev` (one net position per book, opposite fill reverses), no account layer | -0.81 | 0.24 | -0.34 | -0.53 | -$0.785M |
| earlier proxy (two independent exec_engine v2 books summed, 1-minute grid) | 1.04 | 2.69 | 0.87 | - | - |
Reading: with the book rule = `ooat` per book and the account layer applied to the ENGINE's trades, the control matches the live pair within 0.00 / 0.02 / 0.06 weekly Sharpe (net +3% = $90k; daily series differs on 20 of 953 days, max $16.8k, against 1 day for the older acct_se stand-in whose entries are computed ahead). The account layer is the FIFO lot netting of nt8sim.acct (opposite-side entry closes the oldest opposite lot at the entry price; a bracket exit with no same-side lot opens an orphan opposite lot; session flat closes every lot at the block-bar close), run over time-ordered engine entries and exits. `rev` alone is wrong for this pair: the live strategies IGNORE a signal while their bracket is open (busy), they do not reverse, and the lot netting between the books (with orphan exits) is an account-level effect that the engine's per-book position does not have; day/week locks and per-book 5R/-2R are applied by the same downstream account code as before (K96.mkacct -> R.acct). Remaining gap = second-level bracket/gap ordering details (20 days).

## 3. Cell results (ECON, rule ooat per book, uplift = weekly Sharpe vs the ECON control; a cell needs >= +0.10 on clean, H1 and H2 to pass gate 3)
| cell | trades | Sharpe c/H1/H2/all | uplift c/H1/H2/all | allpos |
|---|---|---|---|---|
| CONTROL | 7325 | 1.43 / 2.99 / 2.49 / 1.91 | +0.00 / +0.00 / +0.00 / +0.00 | False |
| K96_oneshot | 6702 | 0.76 / 1.29 / 0.75 / 0.86 | -0.67 / -1.70 / -1.74 / -1.05 | False |
| K96_rearm | 6686 | 0.79 / 0.93 / 0.82 / 0.83 | -0.64 / -2.06 / -1.67 / -1.08 | False |
| K96b_HM_o1_RUN | 7007 | 1.77 / 2.57 / 1.96 / 1.94 | +0.34 / -0.42 / -0.53 / +0.03 | False |
| PA3_o0_L15 | 6936 | 1.37 / 2.83 / 1.87 / 1.71 | -0.07 / -0.17 / -0.62 / -0.20 | False |
| PA3_o0_L30 | 7147 | 1.46 / 2.98 / 2.30 / 1.89 | +0.03 / -0.01 / -0.19 / -0.01 | False |
| PA3_o0_L5 | 5870 | 1.83 / 2.37 / 0.88 / 1.71 | +0.40 / -0.63 / -1.61 / -0.19 | False |
| PA3_o0_L60 | 7103 | 1.83 / 3.00 / 1.49 / 1.91 | +0.39 / +0.01 / -0.99 / +0.00 | False |
| PA3_o0_LRUN | 7088 | 1.77 / 3.00 / 1.47 / 1.87 | +0.33 / +0.01 / -1.02 / -0.04 | False |
| PA3_o1_L15 | 6886 | 1.29 / 2.52 / 1.43 / 1.52 | -0.14 / -0.47 / -1.06 / -0.39 | False |
| PA3_o1_L30 | 7070 | 1.51 / 2.82 / 2.41 / 1.93 | +0.08 / -0.17 / -0.08 / +0.02 | False |
| PA3_o1_L5 | 5849 | 1.85 / 1.63 / 1.06 / 1.64 | +0.42 / -1.37 / -1.42 / -0.26 | False |
| PA3_o1_L60 | 7022 | 1.83 / 2.57 / 1.98 / 1.98 | +0.40 / -0.42 / -0.51 / +0.07 | False |
| PA3_o1_LRUN | 7007 | 1.77 / 2.57 / 1.96 / 1.94 | +0.34 / -0.42 / -0.53 / +0.03 | False |
| PA3_o2_L15 | 6773 | 1.41 / 2.57 / 1.50 / 1.59 | -0.02 / -0.42 / -0.99 / -0.32 | False |
| PA3_o2_L30 | 7047 | 1.56 / 2.42 / 2.40 / 1.89 | +0.12 / -0.57 / -0.09 / -0.02 | False |
| PA3_o2_L5 | 5850 | 1.78 / 1.75 / 1.42 / 1.70 | +0.35 / -1.24 / -1.07 / -0.20 | False |
| PA3_o2_L60 | 7031 | 1.77 / 2.31 / 1.99 / 1.91 | +0.34 / -0.68 / -0.50 / -0.00 | False |
| PA3_o2_LRUN | 7024 | 1.73 / 2.31 / 1.96 / 1.87 | +0.29 / -0.68 / -0.52 / -0.03 | False |
| SE1_delay1 | 7307 | 1.52 / 3.07 / 1.48 / 1.74 | +0.09 / +0.08 / -1.01 / -0.17 | False |
| SE1_delay120 | 7410 | 1.05 / 2.96 / 2.66 / 1.77 | -0.38 / -0.03 / +0.18 / -0.14 | False |
| SE1_delay15 | 7242 | 1.15 / 1.96 / 1.44 / 1.36 | -0.28 / -1.03 / -1.05 / -0.55 | False |
| SE1_delay30 | 7164 | 0.95 / 1.56 / 0.90 / 1.05 | -0.48 / -1.44 / -1.59 / -0.86 | False |
| SE1_delay300 | 7301 | 1.17 / 2.11 / 2.29 / 1.60 | -0.26 / -0.88 / -0.19 / -0.31 | False |
| SE1_delay5 | 7204 | 1.20 / 3.02 / 0.76 / 1.36 | -0.24 / +0.03 / -1.73 / -0.55 | False |
| SE1_delay60 | 7058 | 1.31 / 1.45 / 0.82 / 1.21 | -0.13 / -1.54 / -1.67 / -0.69 | False |
| SE1_flow15 | 6477 | -0.50 / 2.27 / 2.67 / 0.71 | -1.93 / -0.72 / +0.18 / -1.20 | False |
| SE1_flow30 | 6459 | 0.44 / 3.30 / 2.48 / 1.41 | -1.00 / +0.31 / -0.01 / -0.50 | False |
| SE1_flow5 | 6326 | 1.29 / 1.06 / 1.12 / 1.21 | -0.15 / -1.93 / -1.36 / -0.69 | False |
| SE1_lim_o0_W15 | 7086 | 0.90 / 1.80 / 0.52 / 0.97 | -0.54 / -1.19 / -1.96 / -0.94 | False |
| SE1_lim_o0_W60 | 7180 | 0.49 / 1.80 / 0.54 / 0.71 | -0.95 / -1.20 / -1.95 / -1.19 | False |
| SE1_lim_o1_W15 | 6958 | 0.67 / 1.58 / -0.37 / 0.59 | -0.77 / -1.41 / -2.86 / -1.31 | False |
| SE1_lim_o1_W60 | 7128 | 0.65 / 1.83 / 0.20 / 0.74 | -0.78 / -1.16 / -2.29 / -1.17 | False |

Other order-handling rules for the two cells that had been LEADs (ECON):
| cell | rule | trades | uplift c/H1/H2/all |
|---|---|---|---|
| K96b_HM_o1_RUN | ffw | 7291 | -0.08 / -0.06 / -0.85 / -0.26 |
| K96b_HM_o1_RUN | nro | 7291 | -0.08 / -0.06 / -0.85 / -0.26 |
| K96b_HM_o1_RUN | stk2 | 7872 | -0.29 / -0.55 / -0.93 / -0.43 |
| PA3_o2_L60 | ffw | 7295 | -0.00 / +0.38 / -1.23 / -0.25 |
| PA3_o2_L60 | nro | 7295 | -0.00 / +0.38 / -1.23 / -0.25 |
| PA3_o2_L60 | stk2 | 7845 | -0.13 / -0.30 / -0.76 / -0.25 |

SE1 and delay/flow cells under LIVE (touch) fills, for reconciliation with the old SE1 table (stand-in acct_se: delay_1 +0.02/+0.35/-0.46, delay_5 -0.13/+0.24/-1.68, delay_15 -0.27/-0.82/-0.86, delay_30 -0.34/-1.22/-1.41, limit_0_15 -0.13/-0.51/-0.33, limit_1_60 -0.96/-0.59/-1.94, flow_5 -0.12/-1.86/-1.28, flow_30 -0.73/+0.46/-0.02):
| cell | trades | uplift c/H1/H2/all |
|---|---|---|
| CONTROL | 7362 | +0.00 / +0.00 / +0.00 / +0.00 |
| SE1_delay1 | 7290 | +0.09 / +0.36 / -0.73 / -0.05 |
| SE1_delay120 | 7411 | -0.28 / +0.04 / +0.12 / -0.09 |
| SE1_delay15 | 7257 | -0.28 / -0.80 / -1.07 / -0.51 |
| SE1_delay30 | 7188 | -0.37 / -1.20 / -1.48 / -0.72 |
| SE1_delay300 | 7337 | -0.33 / -0.81 / -0.18 / -0.33 |
| SE1_delay5 | 7260 | -0.15 / +0.25 / -1.68 / -0.44 |
| SE1_delay60 | 7142 | -0.06 / -1.36 / -1.31 / -0.53 |
| SE1_flow15 | 6493 | -1.85 / -0.49 / +0.24 / -1.09 |
| SE1_flow30 | 6500 | -0.74 / +0.50 / -0.09 / -0.34 |
| SE1_flow5 | 6352 | -0.12 / -1.84 / -1.26 / -0.64 |
| SE1_lim_o0_W15 | 7157 | -0.56 / -0.95 / -1.20 / -0.75 |
| SE1_lim_o0_W60 | 7233 | -0.63 / -0.96 / -1.44 / -0.85 |
| SE1_lim_o1_W15 | 7080 | -0.55 / -0.49 / -1.84 / -0.81 |
| SE1_lim_o1_W60 | 7197 | -0.84 / -0.57 / -1.92 / -1.02 |

## 4. Stand-in -> engine, both directions (for REPORT_BASIS_RESCORE)
| book | before (stand-in acct_se, touch fills) clean/H1/H2 | exec_engine_x ECON + pair account | change |
|---|---|---|---|
| SE1 limit (4 cells) | -0.13..-0.96 / -0.51..-0.70 / -0.33..-1.94 | -0.54..-0.95 / -1.19..-1.41 / -1.96..-2.86 | NO -> NO (worse) |
| SE1 delay/flow | delay_1 +0.02/+0.35/-0.46 (selected, NO) | delay_1 +0.09/+0.08/-1.01; no cell positive on all spans | NO -> NO |
| K96 oneshot / rearm | -0.20/+1.28/+1.34 ; -0.36/+1.95/+0.75 | -0.67/-1.70/-1.74 ; -0.64/-2.06/-1.67 | NO -> NO; the stand-in's positive H1/H2 came from filling marketable stop orders at the stop price |
| K96b (HM causal stop-entry, ST market) | LEAD +0.72/+0.66/+0.25 | ooat +0.34/-0.42/-0.53; ffw/nro -0.08/-0.06/-0.85; stk2 -0.29/-0.55/-0.93 | **LEAD -> NO** |
| PA3 o2_L60 (selected) | LEAD +0.98/+0.65/+0.31 | ooat +0.34/-0.68/-0.50; ffw/nro 0.00/+0.38/-1.23; stk2 -0.13/-0.30/-0.76 | **LEAD -> NO** |
| PA3 grid (15 cells) | clean +0.32..+0.98 | best clean cells o0_L5/o0_L60 +0.40/-0.63/-1.61 and +0.39/+0.01/-0.99; no cell >= +0.10 on all three spans | LEAD -> NO |
| PULLBACK pair-side 5.1 (64 cell-rules, 1-minute proxy) | all negative | not re-run on the 1-second account (limit-at-EMA/VWAP sets of 4-60 orders per signal; proxy v2 result stands) | NO |
New NO -> LEAD: none. LEAD -> NO: K96b, PA3.

## 5. Family H on exec_engine v2 (the earlier run was on v1: price priority absent; stand-in osm retired before)
Re-run of all 6,528 cell-rules x {T3, V1} with v2 (ap_i5h_ex.py unchanged except the duplicate-hash filter now ignores the family's own earlier registry rows). Backups of the v1 pickles in outputs/autopilot/i5h/v1engine/.
| clock | prescreen v1/v2 | null-pass (not dup) v1/v2 | gate-3 v1/v2 | cells with |change in clean Sharpe| > 0.01 |
|---|---|---|---|---|
| 3-min | 226 / 226 | 140 / 140 | 0 / 0 | 822 of 6,512 (ffw 519, stk2 303; mean ffw -0.017) |
| volume clock V1 | 202 / 195 | 93 / 90 | 7 / 7 (same cells) | 1,404 of 5,184 (ffw 866, stk2 538; mean ffw -0.071) |
Gate-3 set unchanged: H2-a56ba2ee, H2-b74a8f25, H2-d6f0f122, H2-ee6ad880 (all ooat), H5-1afe7aff ffw, H5-7e73308d ffw, H5-e23efc82 stk2. Best I5H-H2-a56ba2ee|V1|ooat: +0.17/+0.55/+0.74, boot lo +0.13, 2x slip +0.11/+0.49/+0.69, wd corr +0.29, plateau 0.50 (fails), positive only under ooat (ffw -0.58, nro -0.41, stk2 -1.02 clean standalone): LEAD, no change. Chance expectation for gate-3 passes among null-passers ~3.4, observed 7 (about 3 independent). Verdict unchanged: 3-min NO; V1 one LEAD (H2 zone ooat-only) and one LEAD-weak. Shared-seed 200-replicate nulls for the selected cells written to outputs/ideas5000/nulls_H.npz for the IDEAS-5000 union null.

## 6. Approximations and what is not done
- Entry rule per book is `ooat` (live busy rule); lot netting between the books is an account-layer post-process on engine trades, not an engine feature; its results depend on the engine's per-book trades being independent of the other book, which holds for market entries and for resting orders (a book's resting orders do not interact with the other book's orders in NT8 except through account netting, which the layer reproduces for fills).
- Stop-entry one-shot per regime run = impulse id with cap_imp=1; a first order blocked by `busy` does not use up the run's shot (the stand-in did); this makes oneshot slightly more permissive.
- ECON stop-entry brackets are fixed at order placement relative to the order price; a gap fill beyond it shrinks the stop distance slightly (rare).
- SE1 limit lifetime is measured in clock seconds from the next-bar open (the stand-in counted print-seconds rows).
- LIVE (MECH) fills are not valid for stop-entry books (section 1).
- No new nulls/bootstraps for pair cells: none clears the +0.10 x 3 gate, so the later gates are moot.
Code: code/census/night_ins/ap_x_pair.py, ap_x_pair_run.py, ap_i5h_ex.py (patched), ap_i5h_nulls.py; results outputs/autopilot/xpair/xpair_results.pkl, tab.pkl.
