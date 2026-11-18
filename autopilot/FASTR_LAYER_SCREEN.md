# FASTR_LAYER_SCREEN - first-order screen of own-layer SETTINGS of the new books (W-FASTR, order 1840Z)

generated 2026-11-18 19:44 UTC. Research only. **Screen only: every verdict comes from the exact engine.** Ranked on the book's OWN-book ulcer (the replay ranks that like the engine: Spearman 1.00, FASTR_VALIDATION.md), trades >= 80% of the ADD baseline, own mean $/wk >= 90% of baseline. "own ulcer x base" < 1 = the book alone has a lower ulcer than the ADD row; the stack ulcer is NOT predicted (stack interplay not modelled).

Every setting here was picked as the best of a grid on the same window it is shown for: persistence across 2025 / 2024 is the check, and the selection-corrected null + 30 date-shift controls + prior years on the engine still apply.

## WP10 (NY PM vol_350 money flow, asym20u/10u): last 6 months, 2025, 2024
| layer | setting | own ulcer x base L6M | own mean/wk L6M | own ulcer x base Y2025 | own mean/wk Y2025 | own ulcer x base Y2024 | own mean/wk Y2024 | persistent |
|---|---|---|---|---|---|---|---|---|
| L1 profit take | take at 90% after 20 s | 0.95 | +112 | 1.15 | -89 | 0.84 | +105 | no |
| L1 profit take | take at 90% after 30 s | 0.96 | +54 | 1.11 | -87 | 0.82 | +110 | no |
| L1 profit take | take at 90% after 10 s | 0.97 | +155 | 1.17 | -108 | 0.88 | +58 | no |
| L10 DAY-DONE setting (NOT validated) | stack >= 22 closes and day <= $-1200 (live 22 / -2400; stricter = exact) | 1.00 | +125 | 1.00 | +60 | 0.98 | +63 | no |
| L10 DAY-DONE setting (NOT validated) | stack >= 22 closes and day <= $-2400 (live 22 / -2400; stricter = exact) | 1.00 | +0 | 0.96 | +100 | 1.00 | +15 | no |
| L10 DAY-DONE setting (NOT validated) | stack >= 10 closes and day <= $-1200 (live 22 / -2400; stricter = exact) | 1.01 | +106 | 1.83 | -547 | 0.94 | +53 | no |
| L2 profit lock | lock at 30% -> entry+10 | 0.59 | +60 | 2.66 | -654 | 0.29 | -191 | no |
| L2 profit lock | lock at 30% -> entry+0 | 0.64 | +189 | 2.71 | -608 | 0.60 | -416 | no |
| L2 profit lock | lock at 50% -> entry+30 | 0.69 | -123 | 0.88 | -188 | 1.27 | -673 | no |
| L3 loss cut | no-follow-through: < +5 pts after 5 min | 0.39 | +50 | 0.83 | -253 | 0.32 | -113 | yes |
| L3 loss cut | no-follow-through: < +0 pts after 5 min | 0.42 | +261 | 0.80 | -89 | 0.25 | +166 | yes |
| L3 loss cut | no-follow-through: < +15 pts after 15 min | 0.56 | -68 | 2.09 | -705 | 0.95 | -448 | no |
| L5 own day caps | loss 1.5 stops ($3600), profit $6000 | 0.96 | +94 | 0.98 | +87 | 1.01 | -23 | no |
| L5 own day caps | loss 1.5 stops ($3600), profit $12000 | 0.96 | +63 | 0.98 | +108 | 1.01 | -23 | no |
| L5 own day caps | loss 1.5 stops ($3600), profit $9000 | 0.96 | +63 | 0.98 | +108 | 1.01 | -23 | no |
| L7 no-trade times (NOT validated) | blank 1500-1530 ET | 0.85 | +38 | 1.02 | +15 | 1.21 | -126 | no |
| L7 no-trade times (NOT validated) | blank 1400-1430 ET | 0.92 | +79 | 0.87 | +103 | 0.92 | -80 | yes |
| L7 no-trade times (NOT validated) | blank 1430-1500 ET | 0.93 | -117 | 1.05 | -17 | 1.01 | -254 | no |

## XA3 (NY AM VWAP retest tick_5000): last 6 months
| layer | setting | own ulcer x base L6M | own mean/wk L6M | persistent |
|---|---|---|---|---|
| L1 profit take | take at 50% after 30 s | 0.68 | -158 | yes |
| L1 profit take | take at 95% after 30 s | 1.01 | -32 | no |
| L1 profit take | take at 95% after 20 s | 1.02 | -44 | no |
| L10 DAY-DONE setting (NOT validated) | stack >= 22 closes and day <= $-2400 (live 22 / -2400; stricter = exact) | 1.00 | +0 | no |
| L10 DAY-DONE setting (NOT validated) | stack >= 10 closes and day <= $-2400 (live 22 / -2400; stricter = exact) | 1.09 | -105 | no |
| L10 DAY-DONE setting (NOT validated) | stack >= 15 closes and day <= $-2400 (live 22 / -2400; stricter = exact) | 1.18 | -149 | no |
| L2 profit lock | lock at 80% -> entry+20 | 0.80 | -68 | yes |
| L2 profit lock | lock at 80% -> entry+30 | 0.85 | -117 | yes |
| L2 profit lock | lock at 80% -> entry+10 | 0.89 | -136 | yes |
| L3 loss cut | no-follow-through: < +10 pts after 20 min | 0.84 | -16 | yes |
| L3 loss cut | no-follow-through: < +5 pts after 20 min | 0.86 | -57 | yes |
| L3 loss cut | scratch: after -45 exit at -5 | 0.90 | -24 | yes |
| L5 own day caps | loss 2.0 stops ($2400), profit $6000 | 0.85 | +54 | yes |
| L5 own day caps | loss 2.0 stops ($2400), profit $9000 | 0.85 | +66 | yes |
| L5 own day caps | loss 2.0 stops ($2400), profit $12000 | 0.85 | +66 | yes |
| L7 no-trade times (NOT validated) | blank 1200-1230 ET | 1.00 | +0 | no |
| L7 no-trade times (NOT validated) | blank 1230-1300 ET | 1.00 | +0 | no |
| L7 no-trade times (NOT validated) | blank 1300-1330 ET | 1.00 | +0 | no |

## Not validated layers
- L7 no-trade times: entry filter: no false skips vs the engine NTZ sets, replay finds about half of the signals the engine removed (later entries shift): treat as indicative
- L6 post-stop blackout: same-side 30 min after a stop/cut: no false skips but the replay finds only 40-60% of the engine blocks (3 months): indicative only
- L10 DAY-DONE setting: stack interplay (engine blocked 17, replay 3): NOT validated
- context cut, ATR skip, sizer / session lots: not replayed (need the wb state / ATR series; the sizer is linear in lots).

Grid: loss cut flat 20-100 pts, no-follow-through (X 0-15 pts, N 5-20 min), back-to-entry (15-60 pts), scratch; take 50-95% x 5-30 s; lock 30-80% -> entry+0..30 and two-step; own day caps 1-4 stops x profit 6k-12k; blackout 15-90 min; no-trade 30-min windows; DAY-DONE n 10-22 x -1200/-2400. Files /mnt/l2/l2vast/_fr/screen_*.csv.
