# DS3_MISSED_FINAL — T-MISSED, one page (lead, 2026-10-30)

Sources: DS3_BASIS_LIVE.md (+LIVE_CAL_SUMMARY.md), DS3_EQUAL_RISK.md, DS3_ENSEMBLE.md, DS3_ENTRY_INTEL_A.md / _B.md, DS3_METALABEL.md. All numbers are the agents' reports (not re-run by the lead). Windows capped at 2026-02-06; 2026 alone is ~5 weeks.

## The five plain sentences
1. **Basis.** Live fills say touched targets fill at nominal (11 of 11, none marginal; 95% lower bound 0.72) and stops cost 2.45 pt more than nominal (n=21): the N basis is the live point estimate, so every profit-side gain that exists only on the measured basis (take-at-70%, +0.86 M vs -1.16 live-cal) is the target-fill artefact.
2. **Equal risk.** Rescaling risk-lowering rules to the stack's worst-20-weeks makes the 70/30 entry split +22.6k/wk (L6M, N basis, 1.06x lots) but 55% of PRE-selected series are >= 0 in L6M — a coin flip — and the tighter gate (source RC <= 0.05) fails it.
3. **Ensemble.** The sum of the small things is worth -18.0k/wk out of sample (MDE 67.8k); only a post-hoc loss-exit+entry subset is positive in L6M/HOLD (+20.5k/+18.5k) and it is negative in PRE (-9.6k).
4. **Entry intelligence never scored.** Signal quality, confluence, HTF, calendar, day type and time-in-session look good in the last year and are zero or reversed before it (EINT1: 28,950 cells; EINT2: 550 cells; 0 PASS); walk-forward re-selection loses (-35.4k/wk L6M for the three combined).
5. **Meta-label.** A model over everything at once selects well in PRE (+0.14 to +0.76 pts/trade) and badly after (-0.18 to -0.80); stack L6M -12.9k (FS1) / -9.4k (FS2), RC p 0.79-0.92, 0 PASS in 2,660 configs.

## "Run this tonight" table (nothing here is a PASS; user decides)
| Item | What | L6M | HOLD | PRE | MDE (L6M) | Tier / caveat |
|---|---|---|---|---|---|---|
| Entry | 70/30 risk-capped split (dip 3 pt, 1 of 8) — already in THP_POLICY v2 | +13.3k M, +17.6k N, +15.2k live-P9 | +11.6k / +18.4k / +13.0k | +7.6k | 14.5k | CANDIDATE-RECENT; fails placebo, PRE CI, engine maxDD, RC; breaks even at ~+1 pt per remainder fill (PRE) |
| Sizing | lots_factor * * 1.14 (EQR, H EL set) | +15.0k M | +7.9k | n/a | 49k | CANDIDATE, research only; needs forward evidence; HOLD SD 228k vs 173k when scaled on PRE |
| Entry filter | skip signals against first-hour delta (usable from 10:31) | +14.0k | +12.0k | +3.3k | 17-20k | forward-watch lead; RC p 0.83 |
| Profit | take-at-70% | +0.86 M / -1.16 live-cal | | | 1.08 | artefact — do not run |
| Anything else | | | | | | DEAD or inside MDE |

Open: forward evidence is the only clean test left (HM forward register starts 2026-11-01 18:00 ET).
