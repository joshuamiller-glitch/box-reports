# REPORT H10-C - EVENT HARD-SKIP AND POST-RELEASE SIDE SWITCH (D10 x M4), live pair
**Verdict: NO. FOUND 0. Selected F_W240 (skip pair entries in [T+5, T+240) that are aligned with the first-5-minute release reaction, i.e. keep only entries that fade it): weekly Sharpe uplift +0.149 clean / -0.218 H1 / -0.175 H2 (needed +0.10 each); all-in +0.031; bootstrap 90% CI of all-in uplift [-0.13, +0.19]; plateau 0.0 of 2; null rank clean 0.86 (p95 +0.247).** The classic clean-only gain that reverses on H1 and H2. Runtime ~25 min (pool of 5). Pre-registered in PREREG_AUTOPILOT.md section H10 before the first run.

## Set-up and fill model
- Verified calendars only (FOMC 14:00, NFP and CPI 08:30 ET, 2023-08..2026-10-13; no ECB). Reaction = NQ close of the 1-min bar T+4 minus close of bar T-1 (known at T+5, causal for entries from T+5); zero reaction -> no skip.
- Skip implemented as a size multiplier 0 (B.Cfg.sizefn) on the live pair engine; dollar rules unchanged. Baseline B.Cfg(wk_floor=8,wk_loss_pb=None) clean process 1.46/2.83/2.30. Fill 1 tick/side + $34.88 per 8 lots; 2x slip SLIP_PT 1.0 both sides.
- Grid (6): S1 skip all entries on event days; S2 skip [T-60,T+60); A_W60/A_W240 skip entries opposing the reaction in [T+5,T+W); F_W60/F_W240 skip entries aligned with it. Null: pseudo-releases on random pair days with the same clock times and count, 100 draws. Plateau: window x0.75/x1.25 (S1: skip fraction).

## Grid uplift (clean selection; other spans shown after selection for transparency)
| cell | clean | H1 | H2 | all |
|---|---|---|---|---|
| S1 skip event days | +0.081 | -0.394 | -0.515 | -0.109 |
| S2 skip [-60,+60) | +0.004 | -0.190 | -0.333 | -0.098 |
| A_W60 skip opposing | -0.005 | -0.051 | -0.048 | -0.022 |
| A_W240 skip opposing | -0.008 | -0.052 | -0.172 | -0.051 |
| F_W60 skip aligned | +0.057 | +0.029 | -0.174 | +0.001 |
| **F_W240 skip aligned (selected)** | **+0.149** | -0.218 | -0.175 | +0.031 |
Hard skips (S1, S2) cost Sharpe out of sample; the event-day trades are net-positive for the pair.

## Gate checklist (selected cell)
- 3 uplift >= +0.10 clean/H1/H2: FAIL (+0.149/-0.218/-0.175); vs B.Cfg(): +0.290/-0.141/-0.216
- worst week not worse (all-in): PASS (delta 0)
- null p95: clean FAIL (rank 0.86 < 0.95; p95 +0.247), H1 FAIL (rank 0.17), H2 FAIL (rank 0.16), all-in FAIL (rank 0.60)
- bootstrap CI > 0 (all-in): FAIL ([-0.130, +0.188]; clean [-0.057, +0.387])
- plateau: FAIL (0 of 2: W x0.75 all-in -0.005, x1.25 -0.013)
- 2x slip: FAIL (+0.139/-0.209/-0.172)
- alternating-month split (pre-registered): select odd -> S1_day (+0.253) reads -0.065 on even; select even -> F_W240 (+0.130) reads +0.116 on odd. One of two holds (F_W240), but it is the cell that reverses on H1/H2, so it does not count as replication.
- wd corr: n/a (switch overlay; weekly corr with pair 0.983)
- Insurance: INS False on every span; worst week and CVaR unchanged (delta 0); clean maxDD 280k -> 273k only.

## Insurance metrics (weekly)
| span | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|
| clean pair | 1.46 | 2.78 | 4.75 | -78.7k | -78.0k | 280k | -81.9k | 42.9 |
| clean cand | 1.61 | 3.04 | 5.32 | -78.7k | -78.0k | 273k | -81.9k | 41.0 |
| H1 pair | 2.83 | 6.09 | 3.91 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H1 cand | 2.61 | 5.59 | 3.72 | -77.6k | -66.0k | 152k | -78.3k | 39.3 |
| H2 pair | 2.30 | 4.69 | 3.50 | -81.1k | -79.2k | 217k | -82.5k | 44.4 |
| H2 cand | 2.12 | 4.30 | 3.26 | -81.1k | -79.2k | 217k | -82.5k | 47.2 |
| all pair | 1.86 | 3.63 | 9.59 | -79.2k | -78.2k | 280k | -82.5k | 42.9 |
| all cand | 1.89 | 3.66 | 9.98 | -79.2k | -78.2k | 273k | -82.5k | 42.3 |

## Executability / era / replication
NT8: the rule needs the NQ close at the release bar and a calendar table inside the strategy; no new orders. Era flag n/a (pair rows 2023-08+). Replication not attempted beyond the pre-registered alt-month split (primary gates fail). Mechanism (fade entries only after the release reaction) plausibly depends on current structure but has no support on H1/H2.
Files: code/census/night_ins/ap_h10_bc.py (c), ap_g10_rep.py; outputs/autopilot/h10_c/.

DONE H10-C
