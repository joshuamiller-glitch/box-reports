# DS3_L2_UF_PROFIT_C2 - PROFIT side, cycle 2 of L2-UNTIL-FOUND (UF-PROFIT, 2026-10-30)
Research only; UNTOUCHED never read; masks 2026=20260101..0206, L6M=20250801..0206, HOLD=20250701..0206, PRE=20240201..20250630, X'=20230401..20240131; label day <= 20260206. Prereg l2vast/ds3/prereg/UF_PROFIT_C2_prereg.md sha256 9937d27373ffabc56fc702eb12e0eee23cf0cceee425fa2dc17323550fb813f7 (cell-name list sha256 f0c01fc1...86), logged before any outcome was run; PRE+X' selection json sha256 7a6f1c47a11a9101174d863973e93cdec7cb00d3aed990f1716adcec7311155b logged before the one recent look. dead_lookup on all 222 specs: 0 EXACT/NEAR hits. Cells 222 (205 selectable) + 4 walk-forward chains. **Look-ahead audit:** no cell uses vol_tag_entry_day or any same-day full-session feature; thresholds are session-of-day quantiles fixed from PRE u X' profit rows, thin-book bits use prior-20-day normalisation (causal); scopes are book and entry session only. No cell is void.

## Verdict
**No PROFIT rule is found; the profit side stays hold-to-bracket.** 0 of 205 cells and 0 of 4 chains are >= 0 on N AND LIVE-CAL in PRE and X' separately with the fire gates (SEL RC p 0.9945); L6M cycle RC p 0.79 (best cell t +1.24 over 205 cells, 129 effective clusters), HOLD p 0.92; cumulative-adjusted (Sidak, N_cum = 143,960 + 226 = 144,186) p = 1.00. (1) Book-with-the-trade vetoes on the path rules do NOTHING: vetoed take-at-pct and tighten-at-arm differ from the un-vetoed control by -0.09..+0.05 pts/trade in SEL and are worse than state-persistent shuffled vetoes. (2) 'Lean before the extreme' gives the only non-negative numbers (delta10 pace 10 s before a new MFE against -> tighten trail 30): N ~0 or slightly positive in every window except 2026, but on 34-134 fired trades per window, inside MDE, stack negative. (3) Walk-forward of the F8 ES gate: the chains are negative in PRE (-0.27 / -0.10), inactive in 2025Q4, +0.08 in 2026Q1 on 81 fires; rank vs a random-cell chain 0.57 (L6M): the cycle-1 recent +0.1 is not distinguishable from noise.

## Settings table (recent first; N and LIVE-CAL primary, M beside; pts/trade vs hold-to-bracket over ALL trades, day-cluster, MDE=2.8 SE)
| role | cell | tier | 2026 N (MDE) | L6M N | HOLD N | PRE N | X' N | L6M LIVE / M | fires L6M | stack vs hold (lock engine, N) L6M / HOLD / PRE (MDE L6M) | EQR approx L6M | causal random-action rank / shuffled-book rank (L6M N) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CYCLE CANDIDATE (PRE+X highest t, fires 118/63) | `UFP2|G3lean|LEAN|dlt10|lag10s|q10|arm0.7|trail30` | BEST-AVAILABLE-NEGATIVE (fails G1 CI, G7, G8/G9) | -0.00 (0.39) | +0.04 (0.17) | +0.01 (0.16) | +0.01 (0.09) | +0.04 (0.22) | +0.03 / +0.06 | 70 | -2.5k / -2.8k / +0.4k (7k) | -3.3k | 0.83 / 0.92 |
| lean neighbour (q20; fires 226/135 in SEL) | `UFP2|G3lean|LEAN|dlt10|lag10s|q20|arm0.7|trail30` | BEST-AVAILABLE-NEGATIVE (fails G1 CI, G7, G8/G9) | -0.07 (0.48) | +0.12 (0.27) | +0.06 (0.26) | +0.02 (0.13) | +0.01 (0.31) | +0.11 / +0.15 | 134 | -0.7k / -1.6k / -0.2k (10k) | -1.3k | n/a |
| family best G1take | `UFP2|G1take|NV|V5_supp80|arm0.6|take` | BEST-AVAILABLE-NEGATIVE (fails G1 CI, G7, G8/G9) | -1.49 (2.14) | -1.44 (1.33) | -1.40 (1.27) | -0.95 (1.01) | -0.40 (1.59) | -1.31 / +0.72 | 6026 | -18.8k / -19.4k / -31.4k (45k) | -18.2k | 0.43 / 0.00 |
| family best G2trail | `UFP2|G2trail|NV|V3a_thin05|arm0.7|trail40` | BEST-AVAILABLE-NEGATIVE (fails G1 CI, G7, G8/G9) | -0.98 (1.86) | -0.82 (1.03) | -0.82 (0.96) | -0.48 (0.68) | +0.15 (1.04) | -0.98 / -0.39 | 1836 | +2.9k / -1.3k / -21.2k (30k) | +1.0k | 1.00 / 0.00 |
| family best G4esgate | `UFP2|G4esgate|F9|es10|s60|arm0.5|gdd8` | BEST-AVAILABLE-NEGATIVE (fails G1 CI, G7, G8/G9) | -0.67 (1.31) | -0.22 (0.60) | -0.31 (0.56) | +0.07 (0.47) | -0.03 (0.50) | -0.19 / +0.04 | 772 | -3.2k / -3.9k / -2.7k (15k) | -3.9k | 0.73 / 0.98 |
| cycle-1 F8 repeat (looked in C1) | `UFP2|G4esgate|F9|es20|s30|arm0.7|gdd12` | CANDIDATE-RECENT (label only) | +0.12 (0.72) | +0.10 (0.35) | +0.07 (0.32) | -0.01 (0.18) | -0.03 (0.15) | +0.11 / +0.16 | 188 | -3.9k / -3.5k / -3.5k (6k) | -3.9k | n/a |
| walk-forward chain | `CH_F9_12m` | BEST-AVAILABLE-NEGATIVE (fails G1 CI, G7, G8/G9) | +0.08 (0.79) | -0.05 (0.33) | -0.16 (0.34) | -0.27 (0.42) | -0.04 (0.17) | -0.04 / +0.02 | 223 | -2.7k / -3.5k / -6.3k (12k) | -5.8k | 0.57 vs random-cell chain |
| walk-forward chain | `CH_F9_3m` | BEST-AVAILABLE-NEGATIVE (fails G1 CI, G7, G8/G9) | -0.01 (0.99) | -0.05 (0.25) | -0.08 (0.27) | -0.10 (0.39) | -0.02 (0.24) | -0.04 / +0.01 | 210 | n/a | n/a | 0.77 vs random-cell chain |
| walk-forward chain | `CH_ALL_12m` | BEST-AVAILABLE-NEGATIVE (fails G1 CI, G7, G8/G9) | +0.08 (0.79) | -0.38 (0.56) | -0.46 (0.53) | -0.46 (0.50) | -0.32 (0.48) | -0.40 / -0.23 | 486 | n/a | n/a | 0.06 vs random-cell chain |
| walk-forward chain | `CH_ALL_3m` | BEST-AVAILABLE-NEGATIVE (fails G1 CI, G7, G8/G9) | -0.01 (0.99) | -0.19 (0.36) | -0.21 (0.36) | -0.30 (0.45) | -0.13 (0.32) | -0.18 / +0.05 | 644 | n/a | n/a | 0.59 vs random-cell chain |

Controls (path rules without any book): 
| control | 2026 N | L6M N | HOLD N | PRE N | X' N | L6M LIVE / M | fires L6M | note |
|---|---|---|---|---|---|---|---|---|
| `UFP2|CTL_take|ALL|arm0.5|take` | -1.63 (2.89) | -1.63 (1.72) | -1.59 (1.64) | -1.27 (1.26) | -0.46 (1.89) | -1.44 / +0.57 | 6539 | M basis = target-fill artefact |
| `UFP2|CTL_take|ALL|arm0.6|take` | -1.59 (2.14) | -1.46 (1.35) | -1.37 (1.29) | -1.03 (1.04) | -0.49 (1.59) | -1.32 / +0.72 | 6081 | M basis = target-fill artefact |
| `UFP2|CTL_take|ALL|arm0.7|take` | -0.95 (1.96) | -1.25 (1.12) | -1.13 (1.06) | -0.91 (0.77) | -0.31 (1.27) | -1.16 / +0.86 | 5565 | M basis = target-fill artefact |
| `UFP2|CTL_take|ALL|arm0.8|take` | -0.69 (1.34) | -0.98 (0.76) | -0.87 (0.72) | -0.63 (0.54) | -0.45 (0.96) | -0.93 / +0.96 | 4868 | M basis = target-fill artefact |
| `UFP2|CTL_trail|ALL|arm0.5|trail30` | -1.78 (3.32) | -1.76 (1.62) | -1.67 (1.53) | -1.07 (1.10) | +0.14 (1.58) | -2.11 / -0.81 | 3810 |  |
| `UFP2|CTL_trail|ALL|arm0.5|trail40` | -1.35 (2.74) | -1.23 (1.48) | -1.20 (1.41) | -0.97 (1.02) | +0.17 (1.46) | -1.48 / -0.58 | 3106 |  |
| `UFP2|CTL_trail|ALL|arm0.7|trail30` | -1.31 (2.16) | -1.11 (1.10) | -1.08 (1.02) | -0.61 (0.75) | +0.18 (1.11) | -1.35 / -0.46 | 2355 |  |
| `UFP2|CTL_trail|ALL|arm0.7|trail40` | -0.93 (1.88) | -0.84 (1.02) | -0.84 (0.95) | -0.50 (0.68) | +0.16 (1.05) | -1.00 / -0.40 | 1853 |  |

Placebos: P1 = independent per-row Bernoulli causal random action (200 draws; rate = the real trigger rate among the rows the kernel can act on); P2 = trigger bits shuffled by trade within label day with the CORRECT row->trade map (60 draws). For state-persistent vetoes (G1/G2) P1 is a poor null (an iid veto flips every 10 s, the real book state persists) so P2 is the relevant one. Ranks (L6M N / SEL N): LEAN|dlt10|lag10s|q10|arm0.7|trail30: P1 0.83/0.94, P2 0.92/0.82; NV|V5_supp80|arm0.6|take: P1 0.43/1.00, P2 0.00/0.00; NV|V3a_thin05|arm0.7|trail40: P1 1.00/1.00, P2 0.00/0.02; F9|es10|s60|arm0.5|gdd8: P1 0.73/1.00, P2 0.98/1.00.

## Veto vs control, SEL only (mean over arms; N basis; delta = veto cell minus the un-vetoed path rule; fire ratio = fires with veto / fires without)
| path rule | veto (book with the trade = hold) | delta N pts/trade | fire ratio |
|---|---|---|---|
| G1take | NV|V10_imb_es | -0.002 | 0.996 |
| G1take | NV|V1_tape | +0.053 | 0.821 |
| G1take | NV|V2_imb5q70 | +0.004 | 0.969 |
| G1take | NV|V3a_thin05 | -0.008 | 0.976 |
| G1take | NV|V3b_thinz | -0.087 | 0.900 |
| G1take | NV|V4_es80 | -0.002 | 0.987 |
| G1take | NV|V5_supp80 | +0.040 | 0.976 |
| G1take | NV|V6_refill70 | -0.028 | 0.947 |
| G1take | NV|V7_dimb60q80 | -0.028 | 0.982 |
| G1take | NV|V8_tape_es | -0.005 | 0.989 |
| G1take | NV|V9_tape_imb | -0.000 | 0.972 |
| G2trail | NV|V10_imb_es | -0.002 | 0.999 |
| G2trail | NV|V1_tape | +0.016 | 0.997 |
| G2trail | NV|V2_imb5q70 | +0.013 | 0.998 |
| G2trail | NV|V3a_thin05 | +0.016 | 0.988 |
| G2trail | NV|V3b_thinz | +0.009 | 0.946 |
| G2trail | NV|V4_es80 | -0.003 | 0.998 |
| G2trail | NV|V5_supp80 | +0.012 | 0.998 |
| G2trail | NV|V6_refill70 | +0.011 | 0.982 |
| G2trail | NV|V7_dimb60q80 | +0.005 | 0.999 |
| G2trail | NV|V8_tape_es | -0.000 | 1.000 |
| G2trail | NV|V9_tape_imb | +0.005 | 0.999 |
Reading: the vetoes remove only 0-18% of the takes/tightens (the book is rarely against the 'with the trade' definitions at these thresholds) and move N by +0.05 at best (V1 tape-with, 18% fewer takes, plain take at pct), which is the effect of taking less, not of taking better. None turns the path rule above 0 (control take-at-70% N PRE -0.91, L6M -1.25; tighten-at-arm -0.5..-1.8).

## Walk-forward of the F8 / G4 ES gate (regime vs noise)
Chains (12m / 91d fit window, 9 refits 2024-01..2026-01, hold when no cell has fit N>0 and LIVE>0 and enough fires). N pts/trade: 
| chain | 2026 | L6M | HOLD | PRE | X' | active share of trades PRE / L6M | rank vs random-cell chain (L6M N / SEL N) |
|---|---|---|---|---|---|---|---|
| CH_F9_12m | +0.08 (0.79) | -0.05 (0.33) | -0.16 (0.34) | -0.27 (0.42) | -0.04 (0.17) | 0.080 / 0.023 | 0.57 / 0.06 |
| CH_F9_3m | -0.01 (0.99) | -0.05 (0.25) | -0.08 (0.27) | -0.10 (0.39) | -0.02 (0.24) | 0.066 / 0.022 | 0.77 / 0.24 |
| CH_ALL_12m | +0.08 (0.79) | -0.38 (0.56) | -0.46 (0.53) | -0.46 (0.50) | -0.32 (0.48) | 0.104 / 0.050 | 0.06 / 0.00 |
| CH_ALL_3m | -0.01 (0.99) | -0.19 (0.36) | -0.21 (0.36) | -0.30 (0.45) | -0.13 (0.32) | 0.094 / 0.066 | 0.59 / 0.04 |
Cycle-1 F8 cell by quarter (N pts/trade, fired trades): arm 0.7 gdd12: 2023Q2 +0.00 (0), 2023Q3 +0.04 (13), 2023Q4 +0.02 (24), 2024Q1 -0.26 (53), 2024Q2 +0.32 (52), 2024Q3 +0.14 (98), 2024Q4 +0.04 (68), 2025Q1 -0.24 (145), 2025Q2 -0.10 (207), 2025Q3 -0.13 (54), 2025Q4 +0.17 (96), 2026Q1 +0.12 (52). arm 0.3 gdd12: 2023Q2 +0.00 (0), 2023Q3 +0.02 (35), 2023Q4 +0.20 (53), 2024Q1 -0.30 (104), 2024Q2 +0.51 (109), 2024Q3 +0.07 (191), 2024Q4 -0.05 (148), 2025Q1 -0.41 (333), 2025Q2 -0.34 (451), 2025Q3 -0.18 (115), 2025Q4 +0.10 (247), 2026Q1 +0.28 (108). Sign flips every 2-3 quarters (+0.32 2024Q2, -0.26 2024Q1, -0.24 2025Q1, +0.17 2025Q4, +0.12 2026Q1): a noisy ~0 series with a lucky recent run, no regime switch that a trailing-fit chain can catch (chain fits choose the cell that was best in the previous year, which is wrong in the next quarter in PRE).

## Lean-before-the-extreme (G3), sessions and books (N, L6M / SEL; MDE in brackets) for the candidate and the q20 neighbour
* `UFP2|G3lean|LEAN|dlt10|lag10s|q10|arm0.7|trail30` sessions: asia -0.16 (0.37, f29) / +0.04 (f83); london +0.25 (0.50, f30) / -0.07 (f56); pre +0.67 (1.47, f4) / +0.08 (f5); nyam -0.02 (0.11, f7) / -0.00 (f12); nypm +0.00 (0.00, f0) / +0.07 (f24); close +0.00 (0.00, f0) / -0.30 (f1)
  books: ST -0.06 (0.32, f8); HM -0.09 (0.54, f8); WT -0.03 (0.18, f8); KB +0.03 (0.34, f8); SM +0.66 (1.65, f7); PE +0.09 (0.41, f9); PB +0.37 (0.58, f7); DN +0.05 (0.35, f2); MV -0.09 (0.37, f9); MA -0.11 (0.77, f4)
* `UFP2|G3lean|LEAN|dlt10|lag10s|q20|arm0.7|trail30` sessions: asia +0.14 (0.65, f63) / +0.02 (f195); london +0.22 (0.63, f45) / -0.00 (f101); pre +0.68 (1.51, f6) / +0.08 (f5); nyam +0.05 (0.30, f17) / -0.02 (f24); nypm -0.06 (0.13, f3) / +0.07 (f35); close +0.00 (0.00, f0) / -0.30 (f1)
  books: ST +0.03 (0.47, f14); HM -0.20 (0.65, f14); WT +0.11 (0.31, f19); KB +0.08 (0.47, f16); SM +1.18 (1.93, f9); PE +0.13 (0.62, f20); PB +0.56 (0.83, f15); DN -0.01 (0.71, f6); MV +0.14 (0.57, f15); MA -0.31 (0.86, f6)
Reading: every session cell is inside its MDE (fires per cell 0-40); the pooled +0.04/+0.12 L6M are a sum of small noise terms. The mechanism ('tape pace turned against 10 s before a fresh high => fake extreme') is the cycle-1 reversal idea in a rarer state; its positive sign is the only one this program has seen on N in PRE, X', HOLD and L6M together, but with 34-134 fires per window it is MDE 0.17-0.27, tier cannot exceed BEST-AVAILABLE.

## Lock-engine stack lines (6 books, plain sum at live lots; delta vs CONTROL_N; $/wk; MDE in brackets)
* `UFP2|G3lean|LEAN|dlt10|lag10s|q10|arm0.7|trail30`: 2026 -8707 (27004); L6M -2526 (6918); HOLD -2758 (6003); PRE +444 (4978); X' -1304 (3059); changed trades 155
* `UFP2|G3lean|LEAN|dlt10|lag10s|q20|arm0.7|trail30`: 2026 -6593 (31746); L6M -727 (9948); HOLD -1587 (8932); PRE -189 (6398); X' -3206 (5192); changed trades 295
* `UFP2|G4esgate|F9|es10|s60|arm0.5|gdd8`: 2026 -12604 (45021); L6M -3192 (14996); HOLD -3916 (14382); PRE -2721 (13047); X' -909 (7677); changed trades 2124
* `UFP2|G1take|NV|V5_supp80|arm0.6|take`: 2026 +19064 (101309); L6M -18848 (45466); HOLD -19401 (41071); PRE -31432 (25435); X' -14596 (31632); changed trades 15509
* `UFP2|G2trail|NV|V3a_thin05|arm0.7|trail40`: 2026 +29460 (77067); L6M +2878 (29623); HOLD -1269 (26930); PRE -21161 (20005); X' -963 (19801); changed trades 4604
* `UFP2|G4esgate|F9|es20|s30|arm0.7|gdd12`: 2026 -301 (9925); L6M -3881 (6268); HOLD -3502 (5501); PRE -3494 (5007); X' -457 (3127); changed trades 453
* `CH_F9_12m`: 2026 -11985 (43694); L6M -2693 (11957); HOLD -3479 (12025); PRE -6335 (12007); X' -2268 (3864); changed trades 1224
Equal risk (EQR) approximation: lots scaled so worst-20-weeks equals the control's on PRE (c 0.95-1.02), L6M equal-risk deltas in the table above; same caveat as cycle 1 (no sweep-surface correction).

## What was learned
1. Book state WITH the trade does not tell the path rules when to hold: the vetoed take-at-pct and tighten-at-arm are as negative as the un-vetoed ones (N L6M -1.44 vs -1.46 at arm 0.6; tighten -0.82 vs -0.84), and against a state-persistent shuffled veto the real book is WORSE (rank 0.00 in all windows for take, 0.00 L6M for tighten). Together with cycle 1 (book against = continuation) the order book carries no usable timing information for exiting winners on this data; what is left is rare-state noise.
2. Lean-before-the-extreme and the ES gate are the only families with non-negative recent N; both are tiny (<2% of trades), inside MDE, negative in the lock-engine stack (-0.7k..-3.9k/wk L6M), and the 12m/91d walk-forward cannot select them in advance (chains -0.05..-0.27 PRE).
3. The row-to-trade defect found in cycle 1 was corrected in all placebo code here (P2). TASK A (separately appended to DS3_L2_UF_PROFIT_C1.md) shows the L2SP G8 ranks were void, not that the thick-book condition was useless; on N/LIVE levels the L2SP verdict stands.

## Counts / multiplicity
Cells 222 (+4 chains). n_effective = 129 (greedy clusters of daily N sums on SEL at corr < 0.95, 205 selectable cells). Cumulative N_cum = 143,960 + 226 = 144,186 (distinct specs +222 new). Candidate L6M t = +0.63 (raw one-sided p 0.27, cycle RC p 0.98); best-cell L6M t over 205 cells +1.24 (RC p 0.79); HOLD RC p 0.92. Cumulative Sidak p = 1.00. DEAD_CELLS +222 (+4 chains), UF_TRIALS cycle 2 profit appended.

## Next PROFIT family (must differ from book-as-trigger/veto on exit timing and from lean/ES gate)
Exit-timing from the book is exhausted (cycles 1-2: reversal trigger, continuation veto, lean, ES gate, hazard, widen). Remaining untested structure on the profit side: (a) the PRICE-PATH shape alone at finer grain with no book (time-in-profit, MFE-velocity, giveback ratio) as a hazard model with a proper walk-forward - the L2P 'path alone' lost -0.2 on M but was never run on the N/LIVE basis with restricted tighten/half actions; (b) cross-instrument: ES/RTY price (not book) divergence at the extreme as the confirm; (c) trade-level SIZING of the winner (scale-out of half at 50% of target is the half-take family: only cycle-1 F6 touched it; a book-free 'take-half at pct x then trail' grid on N). If the lead prefers to stay on the book: MBO order lifetimes are not on disk, so nothing further on queue position.
