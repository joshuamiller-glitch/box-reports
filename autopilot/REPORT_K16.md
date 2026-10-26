# REPORT K16 - TRAILING STOP THAT RATCHETS ONLY WHEN ES CONFIRMS (D07 x M5), live pair
**Verdict: NO. FOUND 0. Selected (45, 5, 1): weekly Sharpe uplift -0.14 clean / +0.07 H1 / -0.44 H2 (needed +0.10 each); all-in -0.17; bootstrap 90% CI of all-in uplift [-0.65, +0.26]; plateau 0.00 of 4; shifted-state null (best-of-grid) clean rank 0.13 (p95 +0.14).** Backlog 2 item 16. Runtime 17 s (grid, neighbours, 2x slip, 100-draw best-of-grid null). Pre-registered in PREREG_AUTOPILOT.md (K11/K13/K14/K16 block) before the first run.

## Set-up and fill model
- Rows: 13,089 live pair rows (ROWS_corrected_engine.parquet, 2023-02-10..2026-10-13), replayed from the fill on 1-second bars (ap_g11_c_core.rs, as G11-C/H10-A) with the 60/60 bracket until the trigger bar, exit at that 1-min bar close; rows whose real exit was external (kind 1) exit at the trigger bar close; rows and signals not touched keep their live P&L. Modified rows re-run through the live account B.Cfg(wk_floor=8,wk_loss_pb=None) in a clean process (reproduced baseline 1.46/2.83/2.30). Slippage 1 tick/side + $34.88 per 8 lots; 2x = SLIP_PT 1.0. Triggers use data through the trigger bar only.
- Rule: the pair has fixed 60/60 brackets; ratchet: MFE (bar highs/lows after entry) >= D arms; at a bar close where ES cumulative close change since entry (in the trade direction) set a new running best within the last N bars, the stop moves to E0 + side x min(MFE - D, close - 1 pt offset), tighten-only; 60-pt target unchanged. Rows whose actual exit was external (kind 1) keep that exit unless the ratcheted stop hits first.
- Grid (6 (arm/trail D {20,30,45} pts x ES-confirm window N {1,5} bars); 3 no-ES controls reported, not selected); selection clean only; H1/H2 printed after selection (the grid table below lists all spans for transparency, only the selected cell was acted on).
- Null: external state series (ES returns / signed volume / VWAP deviation) circularly shifted by 7-400 whole days (time-of-day preserved), identical rule over the full grid, best clean uplift per draw, 100 draws, linear delta-P&L on the baseline account. Pair-change framing only (exit rule of the pair; no separate book so additive and constant-risk framings do not apply; ES/RTY cross-check not applicable). Pair rows start 2023-02, so the pre-2023 ERA flag is n/a.

## Grid (weekly Sharpe uplift vs baseline)
| cell | clean | H1 | H2 | all | rows changed | total pts delta |
|---|---|---|---|---|---|---|
| (20, 1, 1) | -1.50 | +0.15 | -1.39 | -1.19 | 6925 | -11069 |
| (20, 5, 1) | -1.69 | +1.41 | -2.00 | -1.29 | 7239 | -12778 |
| (30, 1, 1) | -0.99 | -1.00 | -1.27 | -1.05 | 4203 | -6796 |
| (30, 5, 1) | -0.84 | -1.03 | -1.40 | -1.00 | 4495 | -7635 |
| (45, 1, 1) | -0.16 | +0.01 | -0.46 | -0.19 | 1398 | -1284 |
| (45, 5, 1) | -0.14 | +0.07 | -0.44 | -0.17 | 1560 | -1141 |

No-ES control (plain trail, same D, N=1; reported only): (20, 1, 0) clean -2.23/H1 +0.95/H2 -2.99; (30, 1, 0) clean -0.99/H1 -0.95/H2 -1.74; (45, 1, 0) clean -0.15/H1 -0.19/H2 -0.35.

Mechanism: tighten the stop only when the broader market confirms the move, so a stall in NQ alone does not choke the trade. Result: every ratchet loses (dpts -1.1k to -12.8k); ES confirmation lessens the damage versus the plain trail (D=20: -1.50 vs -2.23 clean) but never turns it positive. Replay validated: with D = infinity the replay reproduces all 13,089 baseline P&Ls exactly.

## Result for the carried cell (45, 5, 1)
Sharpe clean/H1/H2/all: pair 1.46/2.83/2.30/1.86; candidate 1.32/2.90/1.85/1.69. Neighbours: D x0.75: -0.74/-0.40/-0.95 (all -0.74); D x1.25: +0.11/-0.07/-0.16 (all +0.03); N 4: -0.12/+0.11/-0.45 (all -0.15); N 6: -0.16/+0.09/-0.47 (all -0.18); 
Weekly correlation with the pair 0.87 (same trades, no hedge claim; worst-decile correlation n/a).

## Gate checklist
- 3 uplift >= +0.10 on clean, H1, H2: FAIL (-0.14/+0.07/-0.44)
- worst week not worse (all-in): PASS (delta +200 $)
- own null p95 (clean / H1 / H2 / all-in rank): FAIL (0.13 / 0.30 / 0.16 / 0.14)
- bootstrap CI > 0: FAIL ([-0.65, +0.26])
- plateau >= 75% of +-25% neighbours keep >= 75%: FAIL (0.00 of 4)
- 2x slippage uplift >= +0.10 each span: FAIL (+0.06/-0.40/-1.14)
- replication (H0 and alt-month): FAIL (H0 +0.81; alt-month select odd -> (45, 1, 1) -0.52 reads +0.20 even; select even -> (45, 5, 1) +0.34 reads -0.61 odd)
- wd corr: n/a (modification of pair rows)
- Pre-registration, clean-only selection, H1/H2 once: PASS (process)

## Insurance metrics (weekly)
| span | pair Sharpe | cand Sharpe | pair Sortino | cand Sortino | pair CVaR5 | cand CVaR5 | pair maxDD | cand maxDD | pair worst wk | cand worst wk | pair %neg | cand %neg |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| clean | 1.46 | 1.32 | 2.78 | 2.45 | -78.7k | -79.2k | 280k | 351k | -81.9k | -81.3k | 42.9 | 45.7 |
| H1 | 2.83 | 2.90 | 6.09 | 6.97 | -77.6k | -77.3k | 152k | 150k | -78.3k | -77.3k | 39.3 | 32.1 |
| H2 | 2.30 | 1.85 | 4.69 | 3.72 | -81.1k | -81.1k | 217k | 220k | -82.5k | -82.3k | 44.4 | 44.4 |
| all | 1.86 | 1.69 | 3.63 | 3.28 | -79.2k | -79.5k | 280k | 351k | -82.5k | -82.3k | 42.9 | 43.5 |

## Executability / era
NT8: second ES series; per-position MFE tracking; ChangeOrder on the stop at bar close when ES makes a new favourable high/low; works inside DualStrat per-lot stop management (needs per-lot stop modification, which DualStrat does not currently do). Margin: unchanged (exits only; same 8/8 pair). Fill model: market exit at the trigger bar close. Era flag: pair rows start 2023-02; pre-2023 and ES/RTY replication n/a; H0 as in the checklist. Mechanism depends on current structure (ES leads NQ at 1 minute, aggressor-flow persistence).
Files: code/census/night_ins/ap_k_core.py, ap_k_run.py; outputs/autopilot/k16/ (k16_summary.json, k16_all.pkl); log k16.log.

DONE K16
