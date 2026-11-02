# V13Z CHANGE TABLE: which conclusions change from V13X (defect) -> V13Y (ordering fix, basis M) -> V13Z (basis N) (BASE-4, 2026-11-02T11:54Z; lock none unless stated)

Cells give the value on X / Y / Z in that order; maxDD cut = (without - with)/without, POSITIVE = shallower. Y = the M-basis (measured fill) scenario "if live targets really suffer 3.4 pts"; Z = basis N (touched targets fill at nominal, T-MISSED 11/11). Episodes lookup: DS3_ZONES_EPISODES_V13Y.md.

## 1. Base effects
| effect | F9 | L6M | HOLD | MID | PRE | X' |
|---|---|---|---|---|---|---|
| five gated lines ON vs OFF, maxDD cut (X / Y / Z) | -13% / +27% / -38% | -13% / +27% / -38% | -2% / +26% / -31% | -39% / +41% / +1% | -8% / +22% / -4% | -48% / +24% / +3% |
|   d mean $k/wk (X / Y / Z) | -12.5 / -8.1 / -19.1 | -11.9 / -8.4 / -20.3 | -9.1 / -6.6 / -16.3 | -12.8 / -6.9 / -14.8 | -8.0 / -5.0 / -8.7 | -6.0 / -3.1 / -3.5 |
| PLAIN 0.70 take all books, 1-s, cut (Y / Z) | n/a / +57% / +2% | n/a / +57% / +2% | n/a / +45% / +7% | n/a / +43% / +4% | n/a / +31% / +12% | n/a / +32% / +28% |
|   d mean (Y / Z) | n/a / +7.1 / -9.0 | n/a / +6.3 / -9.2 | n/a / +6.3 / -8.1 | n/a / +8.3 / -7.7 | n/a / -0.6 / -5.9 | n/a / +1.5 / -0.3 |
| shipped layer vs no layer, cut (X / Y / Z) | +9% / +25% / +12% | +9% / +25% / +12% | +9% / +19% / +12% | +19% / +31% / +21% | +27% / +23% / +24% | +29% / +13% / +18% |


## 2. Candidate layers vs the shipped layer (maxDD cut; X / Y / Z)
| candidate | F9 | L6M | PRE | X' |
|---|---|---|---|---|
| sA40>=1 skip | +36% / +36% / +34% | +36% / +36% / +34% | +14% / +0% / +18% | +27% / -5% / +14% |
| nA60>=1 skip | +38% / +36% / +32% | +38% / +36% / +32% | -6% / -36% / -8% | +31% / +7% / +19% |
| PUL k3 4h D20 skip | +1% / -6% / +7% | +1% / -6% / +7% | +17% / -6% / +5% | +11% / +0% / +0% |
| ALL7 skip | n/a / -35% / -27% | n/a / -35% / -27% | n/a / -9% / -15% | n/a / +6% / +7% |
| CRT4h 60 fresh solo | +4% / +3% / +13% | +4% / +3% / +13% | -14% / -0% / -10% | -2% / -2% / -1% |

(ALL7 skip on X: L6M -4%, HOLD -4%, PRE -8%, X' -8% vs HALF per Z3 lock-off cube.) Reading: candidate cuts of sA40/nA60 (volume rules) persist on Z in F9/L6M; PUL k3 is ~0 on every base; CRT4h60 is small and PRE-negative on Z; ALL7 skip is worse than the shipped HALF on every base in F9/L6M.

## 3. Layer vs random halving at equal risk (rank = share of random layers at least as good; small = shipped better; X / Y / Z)
| window | mean rank | maxDD rank | Calmar rank |
|---|---|---|---|
| F9 | 0.48 / 0.21 / 0.34 | 0.41 / 0.17 / 0.69 | 0.43 / 0.11 / 0.62 |
| L6M | 0.40 / 0.17 / 0.38 | 0.41 / 0.17 / 0.69 | 0.38 / 0.10 / 0.64 |
| HOLD | 0.58 / 0.29 / 0.52 | 0.39 / 0.20 / 0.69 | 0.42 / 0.16 / 0.72 |
| PRE | 0.06 / 0.02 / 0.00 | 0.11 / 0.01 / 0.01 | 0.05 / 0.00 / 0.00 |
| X' | 0.81 / 0.80 / 0.39 | 0.59 / 0.50 / 0.47 | 0.80 / 0.73 / 0.40 |
CHANGE: the ordering fix alone (Y) made the layer look better than random in F9-HOLD (ranks 0.1-0.3); the basis-N profit side (Z) removes that again: layer = random halving in the recent year, better only in PRE (all three bases). PRE attribution on Z: edge in all three PRE thirds on mean, books P7 / sessions Asia, NY-AM, 8 of 42 slices <= 0.05 vs 2.1 expected (X: 4 of 42, share 0.15; Y: 9, share 0.00; Z: 8, share 0.00).

## 4. Key masks (saved $ in $k, PA maxDD cut vs band; DS3_KEY_MASKS_V13Z.md): LP_AGAINST_D40 L6M +56k (Z) vs +49k (Y), PRE +50k vs +49k; BT swing D20 PRE +93k vs +89k, L6M +20k vs +18k; BT swing D40 HOLD +100k vs +93k: the saved dollars survive both bases essentially unchanged (these masks skip entries; they do not touch the profit-side basis). PA maxDD rule NOT met by any of the three on either base at lock none or 12R (cuts inside the band): mean-type leads, not drawdown leads. X-base (V13X) values are in ZL-1 / ZL-2 pages.

## 5. Conclusions that do NOT change (re-run on Y only; not re-run on Z because they skip entries or are descriptive): B6 age / touch (no layer helps), B8 zone-as-target (no survivor), profile variants (0 of 576 cells pass; DEAD), stream constructions, fire rates, descriptive reaction statistics. Their dependence on the profit-side basis is second order (the base lines-on series enters both arms) but they were NOT re-scored on Z; re-run with `import use_z` if the lead wants it.

## 6. Take-line verdicts by base (lock none, five gated lines ON vs OFF): X (defect) lines worsen drawdown (F9 -13% deeper) and cost 12k/wk; Y (basis M) lines cut maxDD (F9 +27%, 1-s +39%) at -8k/wk; Z (basis N) lines make maxDD DEEPER (F9 -38%, L6M -38%, HOLD -31%) and cost 19-21k/wk; PLAIN 0.70 take: Y +57% / +7.1k, Z +2% / -9.0k. The live-targets question (do touched targets fill at nominal?) decides: T-MISSED says yes (11/11), i.e. basis N.
