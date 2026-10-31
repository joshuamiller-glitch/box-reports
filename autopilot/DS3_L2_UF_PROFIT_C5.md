# DS3_L2_UF_PROFIT_C5 - PROFIT side, cycle 5: L2 TARGET-CHOOSER AT ENTRY (UF-PROFIT, 2026-10-31)
Research only; UNTOUCHED never read; masks 2026=20260101..0206, L3M=20251106..0206, L6M=20250801..0206, HOLD=20250701..0206, PRE=20240201..20250630, X'=20230401..20240131. Prereg l2vast/ds3/prereg/UF_PROFIT_C5_prereg.md sha256 793f89eeb36b43d316f5c200b141573c1c79213adb261414a3888f3004bc5610 (168 cells; name-list sha256 336dae2a...fb9f), logged before any cell was scored; PRE+X' stack-level selection json sha256 f2175ee38890013b6ea8b5a28d77251d893b3a8c01b9f97bcfe834fede156689 logged before the one recent look. dead_lookup: 0 hits. No day-level feature (DS3_CAUSAL_TIMES.md): all states are the book at the END of the signal second (entry_ts, before the fill); thresholds are entry-session quantiles on SEL. Family chosen and why: MORNING.md start line.
**Units (FOLLOWUP lessons):** every number is pts per trade PER CONTRACT vs hold-to-bracket (= per contract of the final position: one entry, no adds) with N and LIVE-CAL primary and M beside; $ per trade at the planned lots (book lots) and $/wk at research lots and at LIVE lots (K6=KB 2, P6=PE 7, U6=SM 4 Asia/London, H6=HM 4 Asia / 2 NY-AM, M6=MV 2, A6=PB 1; ST/WT/DN/MA not live = 0) beside; the lock-engine stack at research lots is the third unit (lock-engine at live lots is NOT re-run: the engine's sizing is the research size). Target-fill artefact: N has targets filled at nominal (live 11/11); every alternative target is scored on the same basis (hit = +m x target at nominal, stop = fixed stop, timeout = market 0.995 at the flatten time); LIVE-CAL = N - 1.44 x change in stop-class exits.

## Verdict
**Null. No target chooser is information.** 0 of 120 selectable cells is > 0 on trade level AND on the exact lock-engine stack (N and LIVE-CAL) in PRE and X' separately; weekly-stack RC on SEL p = 0.95, qv White RC p 0.53 (SEL) / 0.45 (L6M) / 0.79 (HOLD), Romano-Wolf survivors 0, candidate DSR 0.008, PBO 0.23-0.53; cumulative (UF_TRIALS 2,861,650 + 168) Sidak p = 1.00. The only structure that is positive in the recent windows is 'thin depth ahead (rel_ahead8 <= 0.5) -> shorten the target to 0.67-0.83', and **the same rule applied to the book 60 s EARLIER does at least as well (shifted-book rank 0.00 in every window)**: the condition marks a persistent liquidity regime, not a real-time book prediction. STRUCTURE, post-hoc, view only.

## Header (qv standard columns; the cycle candidate and the post-hoc view)
| cell | per-contract pts N (CI) L6M | L3M / L6M / HOLD / PRE / X' (N) | deviating trades per week (L6M) | fire rate | 1 of N cells | RC p program (SEL) | Romano-Wolf survives | DSR | PBO | placebo ranks L6M N: P1 random chooser / P3 book 60 s earlier / P2 shuffled day | neighbourhood mean (same condition, other m: L6M / SEL) | top-5% share of gain | quarters positive | plain sentence |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| `UFP5|S1cond|thin_a|m0.5` | -0.019 [-0.26,+0.22] | +0.15 / -0.02 / -0.02 / -0.07 / +0.09 | 18.3 | 0.053 | 1 of 168 | 0.53 | N (0 survivors) | 0.008 | 0.23 | 0.69 / 0.00 / 0.73 | -0.12 / -0.03 | n/a | 4/12 | thin depth ahead, shorten the target to 50%: no gain per contract in any window and no better than the same rule on a 60-s older book |
| `UFP5|S1cond|thin_a|m0.67` | +0.030 [-0.18,+0.24] | +0.10 / +0.03 / +0.03 / -0.04 / +0.02 | 18.3 | 0.053 | 1 of 168 | 0.53 | N (0 survivors) | 0.008 | 0.23 | 0.81 / 0.00 / 0.95 | -0.12 / -0.03 | n/a | n/a | thin depth ahead, shorten to 67%: +0.03 per contract in L6M/HOLD but the 60-s older book does as well: liquidity regime, not information |
Not given (cell does not reach CANDIDATE-RECENT or better; qv section 6): breakeven slippage, capacity, stack correlation, regime table beyond sessions. Block-bootstrap (week blocks) CI of the candidate, L6M N: [-0.18,+0.12], HOLD [-0.15,+0.11].

## Settings table (recent first; per contract, N | LIVE-CAL | M, MDE in brackets; stack = exact lock engine at research lots, $/wk vs hold on N and LIVE)
| role | cell | 2026 N | L3M N | L6M N (MDE) | L6M LIVE | L6M M | HOLD N | PRE N | X' N | deviating trades L6M | $/trade planned lots L6M | $/wk research / LIVE lots L6M | stack N / LIVE L6M $/wk (MDE) | stack PRE / X' |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CYCLE CANDIDATE (best min-z; none eligible) | `UFP5|S1cond|thin_a|m0.5` | +0.31 (0.57) | +0.15 (0.37) | -0.02 (0.34) | -0.01 | -0.03 | -0.02 (0.31) | -0.07 (0.24) | +0.09 (0.24) | 512 | -5.3 | -1839 / +454 | +3.1k / +3.8k (7k) | +0.6k / +0.9k |
| post-hoc view (same condition, other multiple; not selected) | `UFP5|S1cond|thin_a|m0.67` | +0.23 (0.60) | +0.10 (0.34) | +0.03 (0.30) | +0.04 | +0.02 | +0.03 (0.27) | -0.04 (0.17) | +0.02 (0.18) | 512 | +5.0 | +1754 / +26 | +6.3k / +6.8k (8k) | +0.3k / +0.6k |
| post-hoc view (same condition, other multiple; not selected) | `UFP5|S1cond|thin_a|m0.83` | +0.19 (0.50) | +0.05 (0.23) | +0.02 (0.21) | +0.03 | +0.02 | +0.03 (0.19) | +0.01 (0.12) | -0.01 (0.12) | 512 | +5.5 | +1909 / -1132 | +2.0k / +2.3k (6k) | +0.1k / -0.5k |
| family best S2pair | `UFP5|S2pair|thin_a+thick_a|up1.25|dn0.83` | -0.29 (0.54) | -0.13 (0.36) | -0.22 (0.29) | -0.22 | -0.20 | -0.20 (0.28) | +0.02 (0.21) | -0.07 (0.26) | 1187 | -39.4 | -13727 / -222 | -2.2k / -2.3k (10k) | +0.4k / -0.4k |
| family best L1model | `UFP5|L1model|L2|6m|k1.0` | +0.23 (5.66) | -1.26 (3.01) | -0.52 (2.28) | -0.62 | +0.00 | -0.76 (2.16) | +0.03 (1.38) | -0.31 (1.15) | 9304 | -99.8 | -34723 / +11322 | -4.6k / -10.5k (46k) | -18.7k / -19.3k |
| control (structure) | `UFP5|C2global|all|m2.0` | +1.53 (7.10) | -0.69 (3.92) | +0.57 (3.11) | +0.36 | +1.38 | +0.23 (2.92) | -0.10 (2.21) | -0.91 (3.41) | 9743 | +92.7 | +32253 / +16680 | -10.9k / -22.7k (54k) | -30.7k / -23.0k |

## Placebos (trade-level, N per contract; rank = share of placebo draws below the real cell; P1 primary)
| cell | real SEL / L6M / HOLD | P1 random chooser (same deviation rate and multiple distribution, 200 draws) mean; rank SEL / L6M / HOLD | P3 same rule on the book 60 s earlier: value; rank | P2 same rule on another same-day trade's book (60 draws): mean; rank |
|---|---|---|---|---|
| `UFP5|S1cond|thin_a|m0.5` | -0.028 / -0.019 / -0.016 | -0.061; 0.41 / 0.69 / 0.64 | +0.052 / +0.188 / +0.167; ranks 0.00 / 0.00 / 0.00 | -0.076; 0.17 / 0.73 / 0.77 |
| `UFP5|S2pair|thin_a+thick_a|up1.25|dn0.83` | -0.005 / -0.218 / -0.201 | -0.063; 0.69 / 0.04 / 0.05 | -0.066 / -0.173 / -0.156; ranks 1.00 / 0.00 / 0.00 | -0.071; 0.73 / 0.02 / 0.02 |
| `UFP5|L1model|L2|6m|k1.0` | -0.060 / -0.516 / -0.763 | -0.096; 0.84 / 0.09 / 0.03 | n/a | n/a |
| `UFP5|S1cond|thin_a|m0.67` | -0.027 / +0.030 / +0.030 | -0.037; 0.32 / 0.81 / 0.83 | +0.027 / +0.184 / +0.159; ranks 0.00 / 0.00 / 0.00 | -0.063; 0.17 / 0.95 / 0.95 |
| `UFP5|S1cond|thin_a|m0.83` | +0.003 / +0.024 / +0.034 | -0.023; 0.67 / 0.88 / 0.89 | -0.015 / +0.138 / +0.121; ranks 1.00 / 0.00 / 0.00 | -0.013; 0.55 / 0.83 / 0.85 |
Reading: P3 ranks of 0.00 mean the shifted-book version of the same rule is better than or equal to the real-time rule in all windows (thin_a: 1,722 trades fire on the shifted book vs 1,670 on the real book): the book state carries no timing information at the signal second, the rule is a regime tag. For the two-sided pair, P1 and P2 ranks in L6M/HOLD are 0.02-0.05 (the real choice is worse than random choosers). The learned chooser (6 cells, 7 LightGBM regressors per refit on 134 book features + context) deviates on 9,000-10,000 trades per 6 months (about 330 per week) and is -0.52 N per contract in L6M (MDE 2.3) vs its book-free twin +0.2..+0.6 (MDE 2.2-2.7): no information, and no stable sign either way.

## Book-free controls (pure structure), N per contract
| control | 2026 | L6M (MDE) | HOLD | PRE | X' | stack L6M $/wk |
|---|---|---|---|---|---|---|
| `UFP5|C1session|london|m0.67` | +0.01 (1.31) | -0.39 (0.61) | -0.37 (0.57) | -0.03 (0.42) | -0.20 (0.60) | 6.3k |
| `UFP5|C1session|london|m1.5` | +0.38 (1.92) | +0.08 (0.99) | -0.08 (0.94) | +0.03 (0.61) | +0.08 (0.85) | 0.1k |
| `UFP5|C1session|nyam|m0.67` | -0.32 (1.36) | -0.17 (0.69) | -0.16 (0.65) | -0.26 (0.45) | -0.14 (0.76) | -4.6k |
| `UFP5|C1session|nyam|m1.5` | +0.18 (2.15) | +0.15 (1.00) | +0.20 (0.94) | +0.13 (0.64) | +0.14 (0.96) | -1.2k |
| `UFP5|C2global|all|m0.5` | -1.23 (3.03) | -1.27 (1.84) | -1.07 (1.79) | -0.67 (1.34) | +0.40 (1.98) | -9.8k |
| `UFP5|C2global|all|m0.67` | -0.50 (2.22) | -0.80 (1.34) | -0.67 (1.28) | -0.44 (0.95) | +0.30 (1.46) | -6.0k |
| `UFP5|C2global|all|m0.83` | -0.09 (1.52) | -0.55 (0.84) | -0.45 (0.79) | -0.32 (0.57) | +0.12 (0.94) | 0.7k |
| `UFP5|C2global|all|m1.25` | -0.67 (2.66) | -0.16 (1.14) | -0.40 (1.07) | +0.01 (0.79) | -0.28 (1.21) | -15.2k |
| `UFP5|C2global|all|m1.5` | -0.24 (4.46) | -0.28 (1.88) | -0.52 (1.78) | +0.04 (1.29) | -0.32 (2.05) | -25.5k |
| `UFP5|C2global|all|m2.0` | +1.53 (7.10) | +0.57 (3.11) | +0.23 (2.92) | -0.10 (2.21) | -0.91 (3.41) | -10.9k |
| `UFP5|C3ctxmodel|CTX|12m|k1.0` | +1.22 (6.21) | +0.62 (2.69) | +0.33 (2.54) | -0.08 (1.63) | +0.27 (1.31) | -5.5k |
Unconditional multiples (all trades) move the bracket along its P(hit)-vs-distance frontier: m 0.5 / 0.67 / 0.83 are -1.27 / -0.81 / -0.55 per contract in L6M on N (shortening the target to 50-83% loses 0.5-1.3 pts/trade; PRE the same sign; only X' is positive), m 1.25 / 1.5 / 2.0 are -0.16 / -0.28 / +0.57 (MDE 1.1-3.1: no better than zero). Per-session multiples: NY-AM m1.5 +0.13/+0.14 (PRE/X' trade level) and NY-PM m0.67 +0.06/+0.52, both inside MDE and sign-unstable across windows (full table in selection_SEL.json controls).

## Candidate and post-hoc view by session / book (N per contract, L6M | SEL; MDE; deviating trades)
* `UFP5|S1cond|thin_a|m0.5` sessions: asia +0.03 (0.35, d64) | -0.08; london -0.08 (0.83, d71) | -0.17; pre -0.01 (1.81, d48) | +0.18; nyam -0.01 (0.62, d139) | +0.10; nypm -0.08 (0.96, d187) | -0.05; close +2.86 (7.26, d3) | -0.41
  books: ST +0.14 (0.93); HM -0.14 (0.68); WT +0.08 (0.38); KB -0.06 (0.89); SM -0.09 (1.18); PE +0.14 (0.88); PB -0.48 (0.71); DN +0.22 (1.03); MV -0.26 (0.64); MA +0.30 (1.44)
* `UFP5|S1cond|thin_a|m0.67` sessions: asia +0.06 (0.36, d64) | -0.05; london -0.03 (0.60, d71) | -0.07; pre -0.78 (0.91, d48) | -0.23; nyam +0.09 (0.51, d139) | +0.06; nypm +0.19 (0.88, d187) | -0.01; close +0.00 (0.00, d3) | -0.27
  books: ST +0.21 (0.76); HM -0.05 (0.66); WT +0.07 (0.33); KB +0.08 (0.68); SM -0.12 (1.02); PE -0.06 (0.74); PB -0.31 (0.62); DN +0.27 (1.01); MV -0.18 (0.59); MA +0.61 (1.45)

## Lock-engine stack (secondary; N and LIVE-adjusted $/wk vs hold at research lots)
* `UFP5|S1cond|thin_a|m0.5`: 2026 +3.7k / +4.4k (11k); L6M +3.1k / +3.8k (7k); HOLD +2.6k / +3.2k; PRE +0.6k / +1.3k; X' +0.9k / +1.1k
* `UFP5|S1cond|thin_a|m0.67`: 2026 +8.8k / +9.3k (19k); L6M +6.3k / +6.8k (8k); HOLD +5.4k / +5.8k; PRE +0.3k / +0.7k; X' +0.6k / +0.7k
* `UFP5|S1cond|thin_a|m0.83`: 2026 +6.7k / +7.0k (22k); L6M +2.0k / +2.3k (6k); HOLD +1.7k / +1.9k; PRE +0.1k / +0.3k; X' -0.5k / -0.5k
* `UFP5|S2pair|thin_a+thick_a|up1.25|dn0.83`: 2026 +0.2k / +0.0k (16k); L6M -2.2k / -2.3k (10k); HOLD -1.6k / -1.6k; PRE +0.4k / +0.4k; X' -0.4k / -0.3k
* `UFP5|L1model|L2|6m|k1.0`: 2026 +16.6k / +7.5k (100k); L6M -4.6k / -10.5k (46k); HOLD -9.6k / -15.3k; PRE -18.7k / -22.5k; X' -19.3k / -19.5k
* `UFP5|C2global|all|m2.0`: 2026 -17.7k / -31.0k (62k); L6M -10.9k / -22.7k (54k); HOLD -14.1k / -25.3k; PRE -30.7k / -41.6k; X' -23.0k / -28.0k

## What was learned
1. A book-conditioned TARGET distance is not information: no cell is positive in PRE and X' on the trade level and the stack together; the one recent pattern (thin depth ahead -> shorten to 0.67: +0.03 L6M/HOLD, +0.10 L3M, +0.23 2026 per contract, stack +6.3k/+5.4k L6M/HOLD with MDE 7.8k/6.9k) is a regime tag: the 60-s-old book gives it too (P3), PRE is -0.045 per contract, 167 deviating trades in X'. Post-hoc, view only, STRUCTURE.
2. The fixed-fraction target moves (global m) lose per contract in every window on N (shorter = more hits at lower gain, net -0.5..-1.3), confirming the bracket sits near its optimum in the 0.8-1.5 range; the learned book chooser is no better than the context-only chooser (neither distinguishable from 0 at MDE 2).
3. The target-fill artefact check: the M basis is within 0.01-0.2 of N for every conditional cell (no alt-target gain comes from the fill correction), i.e. nothing is flattered by M.
4. Together with cycles 1-4 and INFO (touch-level IC 0.02/30 s), nothing in the book at the signal second, in the trade, or at the exit carries a rule that survives per contract; what remains is regime structure (thin liquidity) that a time/liquidity calendar would capture without the book.

## Counts / multiplicity
Cells 168 (120 selectable). n_cum = UF_TRIALS n_cells 2,861,650 (all sides at the start of this cycle) + 168 = 2,861,818. qv program (120 cells, SEL): White RC p 0.53, studentised 0.27, Romano-Wolf survivors 0, PBO 0.23; L6M RC 0.45, HOLD 0.79; min backtest length 6.7 y at 120 trials. Cumulative Sidak p 1.00. DEAD_CELLS +168 (program UFP5). UF_TRIALS cycle 5 profit appended. RECENT_WINS rows: out/recent_wins/uf_profit_c5.csv (view only, post-hoc).

## Next family (must differ; lead may override)
Target chooser and exit timing are exhausted for the book. The one surviving regime tag (thin liquidity) suggests testing LIQUIDITY/TIME CALENDAR as a book-free chooser (session x time-of-day x normalised depth percentile from a trailing table, no tick book) against the same placebos; and, since the 70/30 entry split and re-based targets are structure, the next L2 question is the ENTRY side with INFO's touch signal (imb1/micro-price at the signal second) - owned by UF-ENTRY.
