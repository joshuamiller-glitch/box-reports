# REPORT B14 (= C2-G2 relaunch) - gradient-boosting meta-labeling of the live pair's entries

**Verdict: NO. 0 FOUND, 0 LEAD.** Selected cell (skip bottom 30% by walk-forward probability) has clean uplift +0.19 but H1 +0.35 and H2 -0.58 weekly Sharpe (all-in +0.06; gate needs >= +0.10 on each span), worst week worse on clean and H1; the label-shuffle null already rejects it (real clean uplift +0.194 vs null p95 of the max-cell uplift +0.496; 31% of 250 shuffled-label full-pipeline replicates do at least as well). Walk-forward OOS AUC 0.524 clean / 0.503 H1 / 0.518 H2. Runtime ~2 h (shuffle null 250 reps on 5 workers ~90 min). Pre-registered in PREREG_AUTOPILOT.md ('B14') before any run; all outputs regenerated from scratch (previous C2-G2 outputs not used or read).

## Setup
- Rows: ROWS_corrected_engine.parquet, 13,089 raw ST/HM signal entries; label = gross trade points > 0. 36 frozen features (list in PREREG; code ap_b14_feat.py): nt8sim signal-bar state (st/hm dist and age, adr20, trend agreement, EMA distance), time of day/RTH/dow, 1-min vol (rv30/120, ATR14, ranges), VWAP and day-range position, side-signed returns 5/30/120, 240-bar position, volume ratio, prior-trade outcomes (last-5 sign, last-3 same-book sign, win10, day points so far, prior-day sign).
- Model: LightGBM (300 trees, lr 0.03, 15 leaves, no tuning), expanding window, retrained monthly, training rows = trades that exited before the test month starts; first training span = live rows 2023-02..2023-07, first scored month 2023-08. 2013-2022 1-min-engine trades NOT used (different engine, 90% entry match; features not reproducible there: judged not clearly causal; registered).
- Cells: skip or half-size the bottom q% (q = 10/20/30), threshold = q-th percentile of clean-span OOS p, frozen for H1/H2 (note: this percentile uses the clean p distribution, not labels). Applied through b11_nt8 (skipmask / sizefn) vs B.Cfg(wk_floor=8, wk_loss_pb=None) in a clean process (baseline reproduced 1.46 / 2.83 / 2.30; no b10_core import asserted). Fill model: unchanged live rows with entries skipped or halved (no new fills simulated), 1 tick/side + $34.88 commission per 8 lots; 2x slippage = 2 ticks/side.
- Causality: feature-bar truncation test at 30/60/85% of the series reproduced every nt8sim feature and bar feature on earlier bars (mismatches: none; `b14/causality.txt`); signal bar is the latest flip at or before entry bar-1; trade-history features use only trades exited strictly before entry; training uses only exited trades before the month start. Assumption: skipped trades' hypothetical outcomes stay observable (shadow-book); skipping is treated as not changing later raw signals (as in C9-R1).

## Selection (clean 2023-08..2025-07 only)
Clean weekly-Sharpe uplift by cell: skip10 -0.28, skip20 -0.39, **skip30 +0.19**, half10 -0.15, half20 -0.24, half30 -0.49. Non-monotone and erratic: the signature of noise. Selected skip30 (1,845 ST + 1,009 HM entries skipped over 2023-08..2026-10).

## Gate checklist (selected cell skip30; H1/H2 read once)
| gate | result | pass |
|---|---|---|
| Sharpe uplift >= +0.10 clean / H1 / H2 | +0.194 / +0.353 / -0.580 (all-in +0.056) | NO |
| worst week not worse (clean/H1/H2) | -3.3% / -0.9% / +3.5% | NO |
| label-shuffle null (250 reps, labels permuted in month, full pipeline, max over 6 cells) | real +0.194 vs null p50 +0.075, p95 +0.496, p99 +0.612; p(null >= real) = 0.31 | NO |
| matched random-skip null (300 draws, same per-book count) | clean uplift p95 +0.305 (real +0.194, rank 0.91); H1 p95 +1.245; H2 p95 +0.584 | NO |
| bootstrap 90% CI of uplift (5000 week resamples) | all-in [-0.57, +0.69]; clean [-0.65, +1.05]; H1 [-1.24, +1.96]; H2 [-1.97, +0.68] | NO (lo < 0) |
| plateau (q x 0.75/1.25 and trees 225/375, 8 neighbours; keep >= 75% of all-in +0.056) | 0 of 8 (all-in uplifts -0.55 .. +0.01; clean -0.72 .. +0.37, H2 negative in all 8) | NO |
| 2x slippage uplift (vs 2x baseline) >= +0.10 each span | +0.485 / +0.350 / -0.824 (all-in +0.182) | NO (H2) |
| robustness vs B.Cfg() | +0.302 / +0.716 / -0.974 (all-in +0.066) | n/a |
| worst-decile correlation, hedge | not applicable (pair modification) | n/a |
| executable | needs an exported model/precomputed score table in NT8 (not simple parameter-level DualStrat change); not proposed | n/a |

Insurance metric set (standard key table, `b14/B14_keytable.md`): verdict NO; H2 net -17%, H2 DD +15%; H1 net +19%; clean net -5%; all-in cost -3.0%, CVaR5 -0%, worst week -2%, maxDD +11%. Small-sample flag: not applicable (thousands of trades).

## Reading
OOS AUC of 0.50-0.52 means the 36-feature model has almost no ranking power for trade outcome; the cell-to-cell sign flips (and H1 +0.35 vs H2 -0.58) are what random 30% skips of a high-variance book produce. A shuffled-label pipeline beats the real one in 31% of replicates. Nothing here survives for the pair.

Files: code `code/census/night_ins/ap_b14_{feat,core,sel,shuf,read}.py`; outputs `outputs/autopilot/b14/` (features.parquet, sel.pkl, shuf.pkl, read.pkl, B14_keytable.md, causality.txt).

DONE B14
