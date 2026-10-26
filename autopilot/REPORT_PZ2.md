# REPORT PZ2 - PARTNER-BOOK EVENT EXITS (flatten or stop-to-breakeven when the other book exits same-direction; D00 x M5, H2)
**Verdict: NO. FOUND 0. Selected PSTOP_FLAT (clean-only among 4 cells): weekly Sharpe uplift -0.11 clean / +0.47 H1 / +0.63 H2 (needed +0.10 each); all-in +0.15; bootstrap 90% CI all-in [-0.09, +0.38]; own null clean rank 0.79 (p95 +0.06); selection-corrected null clean rank 0.07 (p95 +0.40); plateau 0.50 of 2; 2x slip +0.01/+0.28/+0.25; H0 +0.16; ES/RTY all-in +0.01/+0.08; failed: g1, g2, g3, g3b, g4, g5, g6.** Pre-registered in PREREG_AUTOPILOT.md block 'BATCH 8 PZ1-PZ5' before the first scored run.

## Disclosure (binding)
Observables (partner exit events) are new. H1/H2 of the pair are non-virgin for exit-management families (G0/J0/H7-B/K16/K20): exits keyed to the trade own MFE/age, ES/RTY spread or per-book P&L were read, not partner exit events. One cell (PSTOP_FLAT) had its H1/H2 printed in a plumbing smoke test before the run (PZ AMENDMENT 1); selection is clean-only so it could not change the carried cell. Event/exit modelling uses 1-minute bars (real stop fills are intra-bar). Maximum status is FOUND-PENDING; newest live weeks (after 2026-10-13) do not exist yet; pre-2023 not testable (pair rows start 2023-02-10; ERA FLAG n/a).

## Mechanism and design
Event: the other book exits a same-direction trade while this book is still open. PSTOP (partner stopped) = the shared signal family failed; PWIN (partner target) = the point where the survivor is nearest its own target. Actions at the next bar open: FLAT (market exit) or BE (stop moved to entry, first 1-min bar through it, gap fills at the open, stop-first within a bar). 4 cells. Null (PZ AMENDMENT 2): same number of victims drawn at random from all baseline-accepted rows, event bar at the same elapsed fraction of the victim life, same action (200 replicates); the registered same-victim random-bar null leaks the future for PSTOP and is reported only as a secondary column.
- Engine: live pair B.Cfg(wk_floor=8,wk_loss_pb=None) via ROWS_corrected_engine in a clean process (baseline reproduced 1.46 / 2.83 / 2.30, all-in 1.86; O(N) pass1 ap_pz_fast.py verified bit-identical to the original before use). Pair-change framing (overlay on the pair, constant-risk framing n/a). Fill: 1 tick/side + $34.88 per 8 lots; 2x slippage = SLIP_PT 1.0 on baseline and variant. Features use only data from earlier sessions or closed bars; frozen tables from clean.
- Own null: random-victim null (victims drawn from all accepted rows, event at the same elapsed life fraction, same action; PZ AMENDMENT 2), 200 replicates. Selection-corrected null: 200 worlds, the whole 4-cell grid re-run per world, best-clean cell carried (its clean mean +0.12, all-in mean +0.14). Secondary nulls (rank/p95 clean, all-in): randvictim 0.79/+0.06, 1.00/+0.03; samevictim_randbar_LEAKY 0.00/+1.92, 0.00/+1.98. Flat-size control: constant 1.000 on every trade.
- Touched trades of the carried cell: 655 in the pair window (359 in clean).

## All cells (weekly-Sharpe uplift vs baseline; clean is the only selection column; H1/H2 of unselected cells shown after selection and unused)
| cell | clean | H1 | H2 | all | mean mult | touched (all) | touched (clean) |
|---|---|---|---|---|---|---|---|
| PSTOP_FLAT | -0.11 | +0.47 | +0.63 | +0.15 | 1.000 | 655 | 359 |
| PSTOP_BE | -0.11 | +0.47 | +0.63 | +0.15 | 1.000 | 655 | 359 |
| PWIN_FLAT | -0.33 | -0.48 | +0.81 | -0.04 | 1.000 | 1060 | 526 |
| PWIN_BE | -0.26 | -0.27 | +0.26 | -0.12 | 1.000 | 372 | 179 |

## Result for the carried cell (weekly Sharpe)
| span | pair | overlay | uplift | flat-size uplift | uplift minus flat | vs B.Cfg() | 2x slip uplift |
|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.35 | -0.11 | +0.00 | -0.11 | +0.21 | +0.01 |
| H1 | 2.83 | 3.30 | +0.47 | +0.00 | +0.47 | +0.52 | +0.28 |
| H2 | 2.30 | 2.92 | +0.63 | +0.00 | +0.63 | +0.46 | +0.25 |
| all | 1.86 | 2.00 | +0.15 | +0.00 | +0.15 | +0.33 | +0.12 |

## Gate checklist
- g1 uplift >= +0.10 clean/H1/H2: FAIL
- g2 worst week not worse (every span): FAIL
- g3 own null p95 clean and all-in (200): FAIL
- g3b selection-corrected null p95 clean and all-in (200 worlds): FAIL
- g4 bootstrap 90% CI of all-in uplift > 0: FAIL
- g5 plateau >= 75%: FAIL
- g6 2x slip uplift >= +0.10 each span: FAIL
- g8 >= 100 touched trades in the pair window (carried 655; else small-sample): PASS
- g9 replication legs >= 2 of 4 (newest weeks n/a): 2 (H0+, alt-month+, ES/RTY-): PASS
- worst week (cand vs pair, k$): clean -82.6 vs -81.9, H1 -78.2 vs -78.3, H2 -78.6 vs -82.5, all -82.6 vs -82.5
- own null (rank/p95): clean 0.79/+0.06, H1 0.89/+0.76, H2 0.98/+0.32, all 1.00/+0.03
- selection-corrected null (rank/p95): clean 0.07/+0.40, H1 0.55/+1.07, H2 0.94/+0.66, all 0.52/+0.37
- plateau neighbours (all-in uplift; need >= 0.11): {'delay+1': 0.17, 'delay+2': 0.05} ; definitions {'delay+1': "{'delay': 1}", 'delay+2': "{'delay': 2}"}
- bootstrap clean CI [-0.39, +0.14]; weekly corr with pair 0.96; worst-week delta all-in -69; worst-decile corr: n/a (overlay on the pair, no hedge claim)
- Controls (uplift clean/H1/H2/all): OTHER_ACTION -0.11/+0.47/+0.63/+0.15; OTHER_TRIGGER -0.33/-0.48/+0.81/-0.04
- g10 insurance metrics: table below. g11 NT8-codable: see Executability.

## Replication legs (>= 2 of 4 needed for FOUND)
- H0 2023-02-10..07-31 (26 weeks, pair Sharpe 0.67): overlay 0.83, uplift +0.16 -> holds.
- Alternating months (2023-08..2026-10): carried cell odd-half +0.01, even-half +0.29; select-on-odd -> PSTOP_FLAT (sel +0.01) read even +0.29; select-on-even -> PSTOP_FLAT (sel +0.29) read odd +0.01 -> holds (needs both > 0 and mean >= 50% of all-in).
- ES / RTY standalone ST+HM books (d1_f4_core, ADR20 k=0.75, live account rules, 1 tick/side, own-instrument state, same recipe): ES +0.04/-0.22/+0.06 (all +0.01, modified 148 of 2780, base all-in -0.75); RTY +0.09/+0.01/+0.14 (all +0.08, modified 137 of 2784, base all-in -0.41) -> fails; same calendar window as the pair (correlated evidence).
- Newest live weeks: none exist after 2026-10-13; the forward monitor (PZ5) will score them. ERA flag: pair rows start 2023-02, pre-2023 not testable (n/a).
- Degeneracy note: on PSTOP events the victim is already at a median -57 pts (it entered on the same signal family within minutes), so BE collapses to FLAT for PSTOP (clean uplift PSTOP_FLAT -0.11 vs PSTOP_BE -0.11); the PSTOP rules are effectively a 3-point-earlier stop.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| clean cand | 1.35 | 2.51 | 4.08 | -79.2k | -78.3k | 305k | -82.6k | 44.8 |
| H1 cand | 3.30 | 7.81 | 5.06 | -77.5k | -66.0k | 146k | -78.2k | 35.7 |
| H2 cand | 2.92 | 6.62 | 4.63 | -78.1k | -75.4k | 216k | -78.6k | 33.3 |
| all cand | 2.00 | 4.01 | 9.78 | -78.8k | -78.1k | 305k | -82.6k | 41.1 |

Insurance flags (INS?, cost%, CVaR5 impr%, worst-week impr%, maxDD impr%): clean (False, -6.3, -0.6, -0.9, -9.0); H1 (False, 24.6, 0.1, 0.1, 3.7); H2 (False, 31.4, 3.7, 4.7, 0.7); all (False, 11.2, 0.5, -0.1, -9.0)

## Executability
NT8: at the fill of an exit order of one book, if the other book holds a same-direction position, submit a market exit (FLAT) or replace its stop with a stop at its average entry price (BE). Reduce-only; DualStrat already tracks both books (NETTING report), so this is a handler on the exit event. Execution at NinjaTrader Brokerage via Rithmic; no data purchase.

Files: code/census/night_ins/ap_pz_fast.py, ap_pz_core.py, ap_pz2_run.py, ap_pz_xi.py, ap_pz_doc.py; outputs/autopilot/pz2/ (runtime 202s, pool of 5).

DONE PZ2
