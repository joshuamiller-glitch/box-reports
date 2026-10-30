# DS3_L2_UF_PROFIT_C3 - PROFIT side, cycle 3 of L2-UNTIL-FOUND (UF-PROFIT, 2026-10-30)
Research only; UNTOUCHED never read (1-s tables filtered ts <= 2026-02-06 22:00Z); masks 2026=20260101..0206, L6M=20250801..0206, HOLD=20250701..0206, PRE=20240201..20250630, X'=20230401..20240131. Prereg l2vast/ds3/prereg/UF_PROFIT_C3_prereg.md sha256 62efbec9b1c4056501ea784108e71929f979078778c329314e81eec5ac3afb7e (cell-name list sha256 6514d176...b507), logged before any model was fitted or any outcome read; PRE+X' selection json sha256 1474b18e9f28924c51553f59e7ea9071cdcf08b906e032143a9e6a501f5e32e8 logged before the one recent look. Cells 225 (144 selectable; 130 with PRE fires >= 200). dead_lookup: 0 EXACT/NEAR hits. Look-ahead audit: no day-level feature in any cell (all states at the decision second; session-of-day quantiles fixed on PRE u X').

## Verdict
**No PROFIT rule is found; the profit side stays hold-to-bracket.** 4 of 144 selectable cells (all ES-divergence on the cycle-2 lean base) were eligible on N and LIVE-CAL in PRE and X' separately; the PRE+X' rank-1 of them (the cycle candidate) flips from +0.09 in SEL to **-0.16 (MDE 0.39) in L6M and HOLD** and is -2.2k/wk in the lock-engine stack. SEL RC p 0.71; L6M cycle RC p 0.87 (best cell t +1.38 over 144 cells, 97 effective clusters), HOLD 0.87; cumulative-adjusted (Sidak, N_cum = 146,342 + 225 = 146,567) p = 1.00. **The sequence model does not work: the 60-s book TRAJECTORY adds nothing over the last book state or over the book-free path** (S1 vs S0 vs P below). The only cell that is >= 0 on N and LIVE in every window including 2026 is a WIDEN-to-the-next-round-50 rule with ES price/book confirm, on 99 fired trades in L6M (MDE 0.15): label CANDIDATE-RECENT only.

## Settings table (recent first; N and LIVE-CAL primary, M beside; pts/trade vs hold-to-bracket over ALL trades; day-cluster; MDE = 2.8 SE)
| role | cell | tier | 2026 N (MDE) | L6M N | HOLD N | PRE N | X' N | L6M LIVE / M | fires L6M | stack vs hold (lock engine, N) L6M / HOLD / PRE (MDE L6M) | EQR approx L6M | rank vs random-trade-shift (P3) SEL / L6M ; shuffled-day (P2) L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CYCLE CANDIDATE (eligible rank 1) | `UFP3|H2div|D|B2|ES|h300|q80|arm0.3|trail30` | BEST-AVAILABLE-NEGATIVE | -0.03 (1.23) | -0.16 (0.39) | -0.16 (0.35) | +0.04 (0.20) | +0.23 (0.50) | -0.18 / -0.11 | 168 | -2.2k / -2.2k / -3.2k (19k) | -3.2k | 1.00 / 0.88 ; 0.02 |
| family best H3 (positive in every window) | `UFP3|H3widen|W|hour_ahead_le0.5|esret|pct0.85|widenrnd50` | CANDIDATE-RECENT (label only; fails G1 CI, G7, G8, stack) | +0.06 (0.14) | +0.04 (0.15) | +0.04 (0.14) | +0.05 (0.09) | +0.01 (0.10) | +0.04 / +0.05 | 99 | -3.6k / -3.2k / +2.2k (5k) | -3.7k | 1.00 / 0.77 ; 1.00 |
| family best H1 (sequence model) | `UFP3|H1traj|M|S1|12m|reg|q99|a0.3|arm0.3|trail30` | BEST-AVAILABLE-NEGATIVE | -0.40 (0.85) | -0.29 (0.42) | -0.22 (0.45) | -0.01 (0.24) | -0.09 (0.23) | -0.33 / -0.21 | 328 | -2.9k / -3.1k / +0.7k (16k) | -0.4k | 1.00 / 0.63 ; 0.00 |
| eligible neighbour H2 | `UFP3|H2div|D|B2|ES|h60|q80|arm0.3|trail30` | CANDIDATE-RECENT (label only; fails G1 CI, G7, G8, stack) | +0.26 (1.18) | +0.05 (0.35) | +0.06 (0.32) | +0.05 (0.21) | +0.15 (0.48) | +0.04 / +0.09 | 142 | +3.3k / +3.2k / -1.7k (14k) | +3.6k | n/a |
| eligible neighbour H2 | `UFP3|H2div|D|B2|ES|h300|q90|arm0.3|trail30` | BEST-AVAILABLE-NEGATIVE | -0.14 (1.13) | -0.10 (0.33) | -0.10 (0.30) | +0.08 (0.17) | +0.06 (0.41) | -0.12 / -0.07 | 120 | n/a | n/a | n/a |

Placebos: P3 = circular shift of the trigger bits within each trade by a random offset (100 draws; keeps per-trade fire counts and persistence, destroys alignment with the path) - the relevant null for state-persistent triggers; P2 = trigger bits taken from another trade of the same label day (60 draws, correct map; fires fewer than real, so only a rough check); P1 = independent per-row Bernoulli at the real row rate (200 draws) fires 5-10x more TRADES than the real persistent state and is not used for judging (its ranks are in look.json). G8 (rank >= 0.95 on both P3 and P2) fails for every cell in L6M: P3 L6M ranks H2div 0.88, H1traj 0.63, H3widen 0.77.

## Does the 60-s TRAJECTORY matter? (SEL-only means over all model cells, N pts/trade; then the matched family-best look)
| feature set | mean PRE N | mean X' N | mean PRE fires | matched cell (12m, reg, q99, arm 0.3, trail30) L6M N (MDE) / HOLD / PRE / X' |
|---|---|---|---|---|
| S1 trajectory (60 s, 175 book features + path) | -0.378 | -0.175 | 2621 | -0.29 (0.42) / -0.22 (0.45) / -0.01 (0.24) / -0.09 (0.23) |
| S0 last state only (25 + path) | -0.410 | -0.124 | 3093 | -0.15 (0.43) / -0.09 (0.45) / -0.11 (0.23) / -0.09 (0.24) |
| P path only, book-free hazard | -0.348 | -0.184 | 2659 | -0.13 (0.36) / -0.13 (0.35) / -0.02 (0.15) / -0.12 (0.26) |
Reading: the trajectory model is not better than the last state, and neither beats the book-free path model; all are negative on N (clf cells, which fire on 10-20% of trades, are -0.3..-1.1 in L6M). The 'rare' q99.7 reg cells fire on 0.5-1.5% of trades and sit at -0.1..-0.2 in L6M, i.e. the model's most adverse predictions are followed by NO more give-back than average: the models do not rank give-back risk out of sample (walk-forward, fit only on closed trades, threshold from the last 60 d of closed trades).

## ES / RTY price divergence (H2) and widen-to-liquidity (H3)
* H2div: the eligible cells are all on base B2 (cycle-2 lean: delta10 pace against 10 s before a new MFE) with NQ outrunning ES over 60-300 s (`>= q80/q90`), tighten 30. SEL N +0.04..+0.09 (PRE) / +0.06..+0.23 (X'), 171-358 fires PRE; then L6M -0.16 / -0.10 / +0.05 / -0.03 (the h60 q80 neighbour is the only one >= 0 in L6M and HOLD: +0.05 (MDE 0.35), 142 fires; stack +3.3k/wk (MDE 14k) L6M, PRE -1.7k, X' -2.3k). On B1 (the model state) and B3 (price only) the divergence is negative. Whether the lean base or the ES divergence carries the SEL sign is not separable at 100-400 fires; the sign is not stable out of sample.
* H3widen: `UFP3|H3widen|W|hour_ahead_le0.5|esret|pct0.85|widenrnd50` N: 2026 +0.06 (0.14) (9 fired), L6M +0.04 (0.15) (99), HOLD +0.04 (0.14), PRE +0.05 (0.09) (203), X' +0.01 (0.10) (23); LIVE L6M +0.04; M L6M +0.05. Mechanism: thin book ahead (rel_ahead8 <= 0.5), ES price sided return over 60 s > 0 and es_imb5 with the trade, MFE >= 85% of the target: move the target to the next round-50 level. Rank vs the trigger shifted within trades: SEL 1.00, L6M 0.77 (not significant); lock-engine stack L6M -3.6k/wk (MDE 5.4k), PRE +2.2k, X' +0.5k: the longer holds block later signals. All other widen cells (23) are within -0.1..+0.1 or negative; the widen rule family is not yet a rule (X' has 23 fires, the L6M gain 0.04 pts/trade = about $1.7k/wk at live lots before the lock effect).

## Controls: book-free scale-out grid (take-half at arm then trail), N basis
| control | 2026 | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| `ALL|arm0.3|half20` | -3.13 (3.53) | -2.87 (2.32) | -2.55 (2.27) | -1.92 (1.65) | -0.57 (2.29) |
| `ALL|arm0.3|half30` | -2.91 (3.65) | -2.62 (2.19) | -2.33 (2.11) | -1.81 (1.55) | -0.32 (2.12) |
| `ALL|arm0.3|half40` | -2.74 (3.27) | -2.37 (2.03) | -2.09 (1.97) | -1.67 (1.46) | -0.19 (1.97) |
| `ALL|arm0.5|half20` | -1.99 (2.99) | -2.03 (1.73) | -1.89 (1.68) | -1.36 (1.26) | -0.19 (1.80) |
| `ALL|arm0.5|half30` | -1.88 (3.07) | -1.88 (1.66) | -1.75 (1.59) | -1.20 (1.19) | -0.13 (1.70) |
| `ALL|arm0.5|half40` | -1.66 (2.76) | -1.62 (1.56) | -1.52 (1.50) | -1.14 (1.13) | -0.12 (1.59) |
| `ALL|arm0.7|half20` | -1.22 (1.82) | -1.29 (1.18) | -1.21 (1.12) | -0.90 (0.84) | +0.01 (1.24) |
| `ALL|arm0.7|half30` | -1.23 (1.90) | -1.19 (1.12) | -1.12 (1.05) | -0.78 (0.80) | -0.04 (1.19) |
| `ALL|arm0.7|half40` | -1.04 (1.74) | -1.05 (1.06) | -1.00 (1.00) | -0.73 (0.75) | -0.05 (1.13) |
Scale-out at the arm is -1.0..-2.9 on N in L6M (M basis -0.2..-0.95 with the target-fill correction in the hold arm): the half taken at market costs the target-fill value on the half and the trailing remainder gets stopped. Nothing book-free in this program beats hold-to-bracket either.

## Sessions / books for the H3 widen cell and the cycle candidate (N; L6M and SEL; MDE in brackets)
* `UFP3|H3widen|W|hour_ahead_le0.5|esret|pct0.85|widenrnd50` sessions: asia +0.04 (0.23, f26) / -0.01 (f100); london +0.29 (0.41, f32) / +0.17 (f70); pre +0.02 (0.06, f1) / +0.04 (f8); nyam -0.04 (0.27, f21) / +0.02 (f16); nypm -0.11 (0.30, f19) / +0.02 (f32); close +0.00 (0.00, f0) / +0.00 (f0)
  books: ST -0.02 (0.45, f14); HM -0.03 (0.43, f10); WT +0.00 (0.16, f6); KB +0.03 (0.36, f13); SM +0.42 (0.65, f5); PE +0.10 (0.23, f12); PB +0.07 (0.25, f12); DN -0.22 (0.92, f13); MV +0.20 (0.26, f11); MA +0.13 (0.27, f3)
* `UFP3|H2div|D|B2|ES|h300|q80|arm0.3|trail30` sessions: asia -0.34 (0.91, f71) / +0.15 (f322); london -0.31 (1.16, f73) / +0.22 (f136); pre +0.26 (0.53, f2) / +0.04 (f13); nyam +0.04 (0.30, f17) / +0.00 (f11); nypm -0.15 (0.22, f5) / +0.04 (f55); close +0.00 (0.00, f0) / -0.30 (f1)
  books: ST +0.16 (0.68, f25); HM -0.22 (0.73, f17); WT +0.01 (0.23, f14); KB -0.18 (0.65, f25); SM -0.81 (1.31, f7); PE -0.30 (0.64, f22); PB -0.36 (0.80, f16); DN -0.25 (0.81, f12); MV -0.11 (0.68, f23); MA -0.35 (1.13, f7)

## Lock-engine stack lines (6 books, plain sum at live lots; delta vs CONTROL_N; $/wk; MDE in brackets)
* `UFP3|H2div|D|B2|ES|h300|q80|arm0.3|trail30`: 2026 +4658 (73253); L6M -2229 (18616); HOLD -2239 (16267); PRE -3189 (6891); X' -2317 (6391); changed trades 389
* `UFP3|H1traj|M|S1|12m|reg|q99|a0.3|arm0.3|trail30`: 2026 +9338 (49347); L6M -2930 (16034); HOLD -3051 (14082); PRE +693 (9268); X' -2737 (4043); changed trades 649
* `UFP3|H3widen|W|hour_ahead_le0.5|esret|pct0.85|widenrnd50`: 2026 -1604 (4491); L6M -3626 (5407); HOLD -3173 (4758); PRE +2240 (3516); X' +542 (6925); changed trades 175
* `UFP3|H2div|D|B2|ES|h60|q80|arm0.3|trail30`: 2026 +11144 (66327); L6M +3256 (14426); HOLD +3216 (12747); PRE -1687 (6342); X' -2291 (6699); changed trades 381
EQR approximation as in cycles 1-2 (lots-linear, worst-20 on PRE).

## What was learned
1. **The order-book trajectory (the only MBO-derived information on disk: 1-s add/cancel/OFI/imbalance aggregates by side and level bucket) does not predict give-back on open winners.** A walk-forward LightGBM on the last 60 s (175 features) is no better than the last state (25) or the book-free path model; rare-state fires (q99.7) are not followed by more give-back than average out of sample. Together with cycles 1-2 (single states, vetoes, leans, ES gate, hazard), the book carries no exit-timing signal for winners that survives the walk-forward, on N or LIVE-CAL.
2. Cross-index price divergence (ES/RTY) adds a SEL-positive sign on the lean base that does not hold in L6M/HOLD (candidate -0.16).
3. The only all-window non-negative cell is a TARGET WIDENER (thin book ahead + ES price/book with the trade, at 85% of the target, to the next round-50 level): +0.04 on N in L6M on 99 fires (MDE 0.15), 0 significance, stack negative. It is the first positive sign for the 'add instead of cut' direction (user hypothesis 7), consistent with cycle 1's F7 being closest to zero; worth one more cycle on its own with more data (X' has 23 fires) rather than as part of a sweep.
4. Book-free scale-out (take-half then trail) is -1..-2.9 on N: the profit side has no path-only edge either; hold-to-bracket stays the reference.

## Counts / multiplicity
Cells 225 (144 selectable, 130 with PRE fires >= 200). n_effective = 97 (greedy clusters of daily N sums on SEL at corr < 0.95). Cumulative N_cum = UF_TRIALS n_cells 146,342 (all sides, cycles up to and incl. this day's others) + 225 = 146,567. Candidate L6M t = -1.17 (raw one-sided p 0.88); best-cell L6M t over 144 cells 1.38 (RC p 0.87); HOLD RC p 0.87; SEL RC p 0.71. Cumulative Sidak p = 1.00. DEAD_CELLS +225; UF_TRIALS cycle 3 profit appended.

## Next PROFIT family (must differ)
Stay on the book but change the question: the book has been tested as a signal for WHEN TO EXIT; the one weak positive is the ADD direction (widen when nothing is ahead and the cross-market confirms). Cycle 4: (a) widen / hold-longer family only - target extension to the next liquidity level with confirmation by cross-index price AND book, scored with the exact lock engine from the start (the stack penalty of longer holds is the binding constraint), using all 10 books and pct arm 0.5-0.85, walk-forward 6/12 months over the extension distance (+10/+20/next level) and the 'thin ahead' definition; (b) the same widen idea expressed as a trailing instead of a fixed target (replace the limit by a trail 20-30 from the high once the confirm is on), which removes the stop-vs-target asymmetry that kills fixed widening. No further exit-timing models on the book.

## Files
code l2vast/ds3/code/uf/uf_p3_*.py (feat, model, trig, cells, run, select, look, shift, stack); data l2vast/ds3/out/uf/profit_c3/{X_book.npy,X_path.npy,trigG.npy,thr3.json,selection_SEL.json,look.json,placebo_P3.json,stack_out.json}; candidate l2vast/ds3/out/uf/profit_cycle3_candidate.txt.
