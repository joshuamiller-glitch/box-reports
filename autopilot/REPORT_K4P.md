# REPORT K4P - supplementary extended plateau and replication battery for K4 (REPORT ONLY, post-hoc, registered after the K4 result)

Selected K4 cell: {'model': 'd2', 'N': 1, 'delta': 0.08, 'mode': 'longonly'}; all-in 20% uplift +0.203 (clean/H1/H2 +0.183/+0.392/+0.193).

## Extended plateau (all-in 20% uplift, scaled with the selected cell's factor)

| neighbour | clean | H1 | H2 | all | keeps >=75% |
|---|---|---|---|---|---|
| delta x0.75 | +0.220 | +1.085 | +0.360 | +0.333 | yes |
| delta x1.25 | +0.147 | +0.089 | +0.105 | +0.127 | no |
| trees x0.75 | +0.129 | +0.097 | +0.231 | +0.147 | no |
| trees x1.25 | +0.196 | +0.324 | +0.204 | +0.205 | yes |
| lr x0.75 | +0.138 | +0.375 | +0.238 | +0.191 | yes |
| lr x1.25 | +0.268 | +0.447 | +0.235 | +0.272 | yes |
| seed 1 | +0.202 | +0.278 | +0.286 | +0.221 | yes |
| seed 2 | +0.169 | +0.456 | +0.185 | +0.205 | yes |
| seed 3 | +0.215 | +0.321 | +0.273 | +0.238 | yes |

Neighbours keeping >= 75% of the selected uplift: 7/9 = 78% (gate needs >= 75%): PASS.

## (a) Per-instrument sleeves 2023-08..2026-10 (same rule, own ADR units; scaled by the pooled factor f)

| instrument | trades | standalone weekly Sharpe | 20% share all-in uplift |
|---|---|---|---|
| ES | 84 | 1.76 | +0.102 |
| NQ | 76 | 1.08 | +0.055 |
| RTY | 56 | 0.90 | +0.036 |
| YM | 51 | 0.93 | +0.032 |

## (b) H0 window 2023-02-10..2023-07-31

pair weekly Sharpe 0.67; pair + 20% K4 sleeve 0.76; uplift +0.086 (26 weeks).

## (c) Alternating-month split of 2023-08..2026-10 (same selected cell)

- odd months: pair 2.70 -> pair + 20% K4 2.85; uplift +0.151
- even months: pair 0.76 -> pair + 20% K4 0.95; uplift +0.198

Reading: report only. K4 stays a LEAD (plateau gate as written failed); this supplement shows whether the failure is a feature of the delta-only neighbourhood or of the model.

DONE K4P