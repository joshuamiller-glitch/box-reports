# REPORT PY8 - MINUTE-OF-HOUR ENTRY SKIP x BOOK SPLIT (J6a localisation; D06 x M4/M8, H1)
**Verdict: NO. FOUND 0. Selected ST_m0.0 (clean-only among 4 cells): weekly Sharpe uplift +0.14 clean / +0.40 H1 / -0.42 H2 (needed +0.10 each); all-in +0.04; vs flat-size control +0.42/+0.46/-0.66; bootstrap 90% CI all-in [-0.24, +0.35]; own null clean rank 0.93 (p95 +0.17); selection-corrected null clean rank 0.93 (p95 +0.17), all-in rank 0.72; plateau 0.00 of 2; 2x slip +0.15/+0.45/-0.33; H0 -0.61; failed: g1, g3, g3b, g4, g5, g6, g7, g8, g9.** Pre-registered in PREREG_AUTOPILOT.md block 'PY7-PY10' before the first run.

## Disclosure (binding)
The all-book window and its clean/H1/H2/H0/alt-month results were read in J6a; the by-book split is a localisation of a parent LEAD: H1/H2/H0/alt-month are non-virgin. ES/RTY is the only data the parent did not use (same calendar window). Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
J6a skipped fills at minutes :00/:15/:30/:45 in both books (LEAD, null rank .88, H0 -0.22). A bar-phase fill cost belongs to the book whose signal is evaluated on the bar close; cells split the skip by book (ST/HM) x m {0,0.5}. Phase specificity gate: windows shifted by -1/+1 minute must keep < 50% of the uplift. ES/RTY standalone-book leg.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Multiplier applied through B.Cfg.sizefn (whole contracts rounded by the engine). Features use only bars closed before the entry bar or earlier sessions; edges/terciles/CDFs frozen on clean entries.
- Nulls: (3) own block null = 100 joint within (book, year, ET-hour) permutations of the state, cell rebuilt with re-derived frozen edges (PY9: random afternoon break on the same fired days, same action and scope); (3b) selection-corrected null = 40 worlds, the whole 4-cell grid re-run per world, best-clean cell carried, statistic = its uplift (its clean mean +0.03, all-in mean -0.00). Flat-size control: constant multiplier 0.969 on every trade (the carried cell's mean multiplier).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | min-max | share touched |
|---|---|---|---|---|---|---|---|
| ST_m0.0 | +0.14 | +0.40 | -0.42 | +0.04 | 0.969 | 0.00-1.00 | 0.031 |
| ST_m0.5 | +0.00 | +0.07 | -0.43 | -0.08 | 0.984 | 0.50-1.00 | 0.031 |
| HM_m0.0 | +0.07 | +0.03 | +0.40 | +0.14 | 0.976 | 0.00-1.00 | 0.024 |
| HM_m0.5 | -0.03 | +0.07 | +0.20 | +0.05 | 0.988 | 0.50-1.00 | 0.024 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.60 | +0.14 | -0.28 | +0.42 | +0.10 | +0.15 |
| H1 | 2.83 | 3.22 | +0.40 | -0.06 | +0.46 | +0.27 | +0.45 |
| H2 | 2.30 | 1.88 | -0.42 | +0.24 | -0.66 | -0.39 | -0.33 |
| all | 1.86 | 1.90 | +0.04 | -0.14 | +0.18 | +0.02 | +0.08 |

## Gate checklist
- g1 uplift >= +0.10 clean/H1/H2: FAIL
- g2 worst week not worse (every span): PASS
- g3 own block null p95 clean and all-in: FAIL
- g3b selection-corrected null p95 clean and all-in: FAIL
- g4 bootstrap 90% CI of all-in uplift > 0: FAIL
- g5 plateau >= 75%: FAIL
- g6 2x slip uplift >= +0.10 each span: FAIL
- g7 uplift minus flat-size control >= +0.10 clean/H1/H2: FAIL
- g8 phase specificity: -1/+1 minute shifted windows keep < 50% of all-in uplift: FAIL
- g9 replication legs >= 2 of 4 (H0, alt-month, ES/RTY, newest weeks n/a): 0 (H0-, alt-month-, ES/RTY-): FAIL
- worst week (cand vs pair, k$): clean -79.9 vs -81.9, H1 -78.3 vs -78.3, H2 -82.5 vs -82.5, all -82.5 vs -82.5
- own null (rank/p95): clean 0.93/+0.17, H1 0.85/+0.57, H2 0.25/+0.41, all 0.85/+0.14
- selection-corrected null (rank/p95): clean 0.93/+0.17, H1 0.90/+0.44, H2 0.20/+0.42, all 0.72/+0.18
- plateau neighbours (all-in uplift; need >= 0.03): {'depth x0.5': -0.08, 'depth x0.75': 0.03} ; neighbour definitions {'depth x0.5': "{'depthf': 0.5}", 'depth x0.75': "{'depthf': 0.75}"}
- flat-size control under 2x slippage: {'clean': -0.07, 'H1': -0.09, 'H2': -0.05, 'all': -0.07}
- bootstrap clean CI [-0.19, +0.53]; weekly corr with pair 0.95; worst-week delta all-in +0; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Reported controls (uplift clean/H1/H2/all): ALL_BOOKS_same_m +0.18/+0.38/+0.14/+0.20; PHASE_PLUS1 -0.39/-0.37/-0.59/-0.41; PHASE_MINUS1 +0.05/-0.41/+0.52/+0.09
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 0.06, uplift -0.61 -> fails (needs > 0 and >= 50% of clean).
- Alternating months (2023-08..2026-10): carried cell odd-half +0.08, even-half +0.02 ; select-on-odd -> ST_m0.5 (sel +0.14) read even -0.28; select-on-even -> HM_m0.0 (sel +0.20) read odd +0.08 -> fails.
- ES/RTY standalone ST+HM books (d1_f4_core, ADR20 k=0.75, live account rules, 1 tick/side; same minute mask, selected book): weekly-Sharpe uplift
| book | cell | clean | H1 | H2 | all-in | flagged share | base all-in |
|---|---|---|---|---|---|---|---|
| ES | CARRIED | +0.03 | -0.09 | +0.04 | +0.02 | 0.022 | -0.75 |
| ES | ALL_BOOKS | +0.09 | +0.06 | -0.09 | +0.05 | 0.051 | -0.75 |
| ES | SHIFT_-1 | +0.13 | +0.28 | -0.01 | +0.12 | 0.026 | -0.75 |
| ES | SHIFT_+1 | +0.15 | -0.58 | +0.06 | +0.04 | 0.095 | -0.75 |
| RTY | CARRIED | +0.01 | -0.28 | -0.08 | -0.06 | 0.023 | -0.41 |
| RTY | ALL_BOOKS | +0.01 | -0.19 | +0.01 | -0.03 | 0.049 | -0.41 |
| RTY | SHIFT_-1 | +0.15 | -0.09 | +0.03 | +0.09 | 0.022 | -0.41 |
| RTY | SHIFT_+1 | +0.15 | +0.29 | -0.32 | +0.08 | 0.094 | -0.41 |
  -> ES/RTY leg fails (both all-in > 0, mean >= 50% of NQ all-in, no span below -0.10); same calendar window as the pair, so correlated evidence.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.60 | 3.11 | 5.57 | -78.4k | -77.8k | 259k | -79.9k | 42.9 |
| H1 cand | 3.22 | 7.24 | 5.33 | -77.6k | -66.0k | 127k | -78.3k | 35.7 |
| H2 cand | 1.88 | 3.57 | 2.71 | -81.1k | -79.7k | 236k | -82.5k | 41.7 |
| all cand | 1.90 | 3.74 | 10.65 | -79.2k | -78.3k | 259k | -82.5k | 41.7 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, 8.6, 0.4, 2.5, 7.4); H1 (False, 14.5, 0.0, 0.0, 16.0); H2 (False, -16.2, 0.0, 0.0, -8.4); all (False, 2.9, 0.0, 0.0, 7.4)

## Executability
NT8: suppress (m=0) or halve the order on ST (or HM) entries whose fill minute (ET) is :00/:15/:30/:45; reduce-only, no extra margin. Note the live strategy evaluates signals on the 1-min close, so the fill minute equals the signal minute+1; the rule is a calendar-minute mask. Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_py7_core.py, ap_py7_run.py, ap_py7_xi.py, ap_py7_doc.py; outputs/autopilot/py8/ (runtime 1793s, pool of 4).

DONE PY8
