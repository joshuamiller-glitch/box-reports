# REPORT POWER - would the gate chain find a book of known edge? (DIRECTIVE CALIBRATE item 2)

Written 2026-10-17 by worker FA. Pre-registered in PREREG_AUTOPILOT.md ('POWER') before any planted book was scored. Code: code/census/night_ins/ap_power_pool.py (noise worlds on real NQ bars), ap_power_chain.py (planting + chain), ap_power_report.py. Data: outputs/autopilot/power/ (power_books.csv = 6,600 books with every gate, power_table.csv, power_chain_by_cell.csv, power_books_flat.csv = plateau sensitivity). No purchases; gates unchanged from ap_sw_pipe/ap_sw_nullcal/FA4.

## 1. Verdict

**The chain has low power against pair-grade books.** A planted book with a true standalone weekly Sharpe of 1.5 (the pair's clean-span level), regime-bound like the pair and uncorrelated with it, passes the full additive chain (selection, H1/H2 standalone positive, gate 3, null, bootstrap, worst-decile correlation, plateau, 2x slippage) in **3.0% of books** (95% interval 1.4-6.4%); 18% reach the LEAD-grade point (through the bootstrap) and **19% pass gate 3**. Even an uncorrelated stationary Sharpe-2.0 book passes the full chain only 8.5% of the time (regime-bound 4.5%). At correlation +0.3 with the pair a Sharpe-1.5 book passes gate 3 in 1.0% and at +0.6 in 0% (all sizes up to 2.0: <= 2%). The same chain on zero-edge books passes 0 of 600 (consistent with FA4: 0 of 25,664). **The gates that kill a pair-grade edge are, in order: gate 3 (three-span additive uplift against a base pair whose H1/H2 Sharpe is 3.1/2.4, and the worst-week condition; conditional pass 25%), the plateau (conditional 19% with a planted neighbour edge of 80%, 12% full-chain with a 97% neighbour edge), and the H1/H2 standalone-positive requirement (79% conditional)**; the null, bootstrap and 2x-slippage gates remove little once those pass, and the worst-decile correlation gate removes 3-14%. A LEAD that fails gate 3 or the plateau therefore cannot be read as 'no edge'; a pair-grade edge would usually fail the same gates.

## 2. Design (as pre-registered)

* **Real-bar noise, zero edge.** 2,040 worlds on the real NQ 1-min bars 2013-26: 3 random base entry rows per day with random sides, 50 cells = 5 entry offsets x 5 time-exit holds x 2 session windows, each simulated by the real v2-style simulator (next-open entry, 1 tick/side + $4.36, one position at a time, 16:55 flatten). Neighbouring cells share entries, so they are correlated as parameter neighbours are. About 6,300 trades per cell; a zero-edge cell loses about $14 per trade (the cost).
* **Plant.** A constant dollar drift per trade (scaled by the local weekly dollar volatility so the Sharpe is stationary across 2013-26 price levels) on the centre cell, solved so the realised weekly Sharpe of the final book over the 167-week pair window equals the target; off-centre cells carry m = exp(-(di^2+dj^2)/(2 x 1.5^2)) of the drift (adjacent 0.80, diagonal 0.64, two steps 0.41; RTH-only variant x 0.9). Regime types: stationary (drift in all trades 2013-26) and regime-bound (drift only in weeks from 2023-W01, zero before). Because the pair-window Sharpe is the target in both, the two types differ only in 2013-22 behaviour (ERA, H0), and in the stationary type the 2013-22 Sharpe is lower than the target (price level and volatility differ).
* **Correlation.** A shared component (real PAIR from 2023-02, rescaled engine proxy before) on every cell, solved so that the final centre-cell weekly correlation with the pair equals the target. Verified (mean over books, table 6): realised Sharpe equals the target within 0.04 on average, correlation equals the target to 0.01.
* **Chain** per book, cumulative: S -> H -> G3 -> N -> B -> W -> P -> X (full definitions in the prereg). The candidate is the best clean-Sharpe cell among the eligible ones of the 50. Not applied: ES/RTY/YM replication (the plant is NQ-only by construction; a cross-market test would measure an assumed transfer ratio, not the pipeline); executability passes by construction (market entries); H0, alternating months and ERA are reported, not gating.
* 6,000 planted books (5 sizes x 2 regime types x 3 correlations x 200) + 600 zero-edge books.

## 3. Cumulative pass rate by gate (fraction of books; whole chain in the last column)

| regime | SR | rho | books | S | H | G3 | N | B (LEAD-grade) | W | P | full chain | full lo95 | full hi95 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| regime | 0.500 | 0.000 | 200 | 0.705 | 0.155 | 0.025 | 0.025 | 0.020 | 0.020 | 0.000 | 0.000 | 0.000 | 0.019 |
| regime | 0.500 | 0.300 | 200 | 0.550 | 0.200 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| regime | 0.500 | 0.600 | 200 | 0.440 | 0.245 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| regime | 0.750 | 0.000 | 200 | 0.825 | 0.340 | 0.040 | 0.040 | 0.030 | 0.030 | 0.005 | 0.000 | 0.000 | 0.019 |
| regime | 0.750 | 0.300 | 200 | 0.685 | 0.335 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| regime | 0.750 | 0.600 | 200 | 0.470 | 0.340 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| regime | 1.000 | 0.000 | 200 | 0.885 | 0.490 | 0.055 | 0.055 | 0.045 | 0.045 | 0.010 | 0.000 | 0.000 | 0.019 |
| regime | 1.000 | 0.300 | 200 | 0.780 | 0.495 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| regime | 1.000 | 0.600 | 200 | 0.685 | 0.580 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| regime | 1.500 | 0.000 | 200 | 0.955 | 0.755 | 0.190 | 0.190 | 0.185 | 0.180 | 0.035 | 0.030 | 0.014 | 0.064 |
| regime | 1.500 | 0.300 | 200 | 0.895 | 0.765 | 0.010 | 0.010 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| regime | 1.500 | 0.600 | 200 | 0.860 | 0.820 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| regime | 2.000 | 0.000 | 200 | 0.985 | 0.925 | 0.280 | 0.280 | 0.280 | 0.240 | 0.050 | 0.045 | 0.024 | 0.083 |
| regime | 2.000 | 0.300 | 200 | 0.975 | 0.950 | 0.150 | 0.150 | 0.150 | 0.145 | 0.000 | 0.000 | 0.000 | 0.019 |
| regime | 2.000 | 0.600 | 200 | 0.960 | 0.960 | 0.005 | 0.005 | 0.005 | 0.005 | 0.000 | 0.000 | 0.000 | 0.019 |
| stationary | 0.500 | 0.000 | 200 | 0.730 | 0.225 | 0.010 | 0.010 | 0.010 | 0.010 | 0.005 | 0.005 | 0.001 | 0.028 |
| stationary | 0.500 | 0.300 | 200 | 0.590 | 0.180 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| stationary | 0.500 | 0.600 | 200 | 0.380 | 0.215 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| stationary | 0.750 | 0.000 | 200 | 0.785 | 0.290 | 0.010 | 0.010 | 0.005 | 0.005 | 0.000 | 0.000 | 0.000 | 0.019 |
| stationary | 0.750 | 0.300 | 200 | 0.665 | 0.335 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| stationary | 0.750 | 0.600 | 200 | 0.535 | 0.335 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| stationary | 1.000 | 0.000 | 200 | 0.880 | 0.445 | 0.035 | 0.035 | 0.015 | 0.015 | 0.005 | 0.000 | 0.000 | 0.019 |
| stationary | 1.000 | 0.300 | 200 | 0.760 | 0.485 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| stationary | 1.000 | 0.600 | 200 | 0.670 | 0.535 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| stationary | 1.500 | 0.000 | 200 | 0.935 | 0.750 | 0.210 | 0.210 | 0.210 | 0.190 | 0.045 | 0.030 | 0.014 | 0.064 |
| stationary | 1.500 | 0.300 | 200 | 0.875 | 0.750 | 0.015 | 0.015 | 0.010 | 0.010 | 0.000 | 0.000 | 0.000 | 0.019 |
| stationary | 1.500 | 0.600 | 200 | 0.845 | 0.810 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| stationary | 2.000 | 0.000 | 200 | 0.990 | 0.915 | 0.325 | 0.325 | 0.325 | 0.310 | 0.090 | 0.085 | 0.054 | 0.132 |
| stationary | 2.000 | 0.300 | 200 | 0.975 | 0.950 | 0.105 | 0.105 | 0.105 | 0.100 | 0.010 | 0.005 | 0.001 | 0.028 |
| stationary | 2.000 | 0.600 | 200 | 0.960 | 0.955 | 0.020 | 0.020 | 0.020 | 0.020 | 0.000 | 0.000 | 0.000 | 0.019 |
| zero | 0.000 | 0.000 | 200 | 0.520 | 0.085 | 0.005 | 0.005 | 0.005 | 0.005 | 0.000 | 0.000 | 0.000 | 0.019 |
| zero | 0.000 | 0.300 | 200 | 0.395 | 0.145 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |
| zero | 0.000 | 0.600 | 200 | 0.260 | 0.115 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.019 |

## 4. Power curve - full additive chain (S..X) by true standalone Sharpe

| SR | regime rho=0.0 | regime rho=0.3 | regime rho=0.6 | stationary rho=0.0 | stationary rho=0.3 | stationary rho=0.6 |
|---|---|---|---|---|---|---|
| 0.500 | 0.000 | 0.000 | 0.000 | 0.005 | 0.000 | 0.000 |
| 0.750 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 |
| 1.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 |
| 1.500 | 0.030 | 0.000 | 0.000 | 0.030 | 0.000 | 0.000 |
| 2.000 | 0.045 | 0.000 | 0.000 | 0.085 | 0.005 | 0.000 |

LEAD-grade point (through the bootstrap):

| SR | regime rho=0.0 | regime rho=0.3 | regime rho=0.6 | stationary rho=0.0 | stationary rho=0.3 | stationary rho=0.6 |
|---|---|---|---|---|---|---|
| 0.500 | 0.020 | 0.000 | 0.000 | 0.010 | 0.000 | 0.000 |
| 0.750 | 0.030 | 0.000 | 0.000 | 0.005 | 0.000 | 0.000 |
| 1.000 | 0.045 | 0.000 | 0.000 | 0.015 | 0.000 | 0.000 |
| 1.500 | 0.185 | 0.000 | 0.000 | 0.210 | 0.010 | 0.000 |
| 2.000 | 0.280 | 0.150 | 0.005 | 0.325 | 0.105 | 0.020 |

Standalone track (selection, H1/H2 net positive, null p95, bootstrap of the weekly mean > 0, standalone plateau, 2x slippage net positive on H1 and H2):

| SR | regime rho=0.0 | regime rho=0.3 | regime rho=0.6 | stationary rho=0.0 | stationary rho=0.3 | stationary rho=0.6 |
|---|---|---|---|---|---|---|
| 0.500 | 0.000 | 0.035 | 0.015 | 0.015 | 0.035 | 0.025 |
| 0.750 | 0.035 | 0.035 | 0.020 | 0.035 | 0.040 | 0.025 |
| 1.000 | 0.090 | 0.090 | 0.140 | 0.085 | 0.075 | 0.170 |
| 1.500 | 0.185 | 0.240 | 0.425 | 0.210 | 0.215 | 0.415 |
| 2.000 | 0.400 | 0.430 | 0.535 | 0.330 | 0.420 | 0.565 |

Plateau sensitivity - full additive chain when the planted edge decays only to 97% at the adjacent step (sigma 4 steps instead of 1.5; same books otherwise):

| SR | regime rho=0.0 | regime rho=0.3 | regime rho=0.6 | stationary rho=0.0 | stationary rho=0.3 | stationary rho=0.6 |
|---|---|---|---|---|---|---|
| 0.500 | 0.010 | 0.000 | 0.000 | 0.005 | 0.000 | 0.000 |
| 0.750 | 0.005 | 0.000 | 0.000 | 0.005 | 0.000 | 0.000 |
| 1.000 | 0.015 | 0.000 | 0.000 | 0.040 | 0.000 | 0.000 |
| 1.500 | 0.125 | 0.005 | 0.000 | 0.110 | 0.000 | 0.000 |
| 2.000 | 0.250 | 0.090 | 0.015 | 0.290 | 0.085 | 0.005 |

## 5. Which gates kill what (conditional pass rate, i.e. given the previous gates passed)

| gate | regime SR1.5 rho0 | stationary SR1.5 rho0 | regime SR2.0 rho0 | stationary SR2.0 rho0 | regime SR1.5 rho0.3 | regime SR1.0 rho0 |
|---|---|---|---|---|---|---|
| clean-only selection (>=100 trades, both halves positive) | 0.955 | 0.935 | 0.985 | 0.990 | 0.895 | 0.885 |
| standalone net > 0 on H1 and H2 | 0.791 | 0.802 | 0.939 | 0.924 | 0.855 | 0.554 |
| gate 3 additive uplift >= +0.10 on clean, H1, H2 + worst week | 0.252 | 0.280 | 0.303 | 0.355 | 0.013 | 0.112 |
| own timing-destroyed null p95 | 1.000 | 1.000 | 1.000 | 1.000 | 1.000 | 1.000 |
| bootstrap 90% lower bound > 0 | 0.974 | 1.000 | 1.000 | 1.000 | 0.000 | 0.818 |
| worst-decile correlation <= +0.30 | 0.973 | 0.905 | 0.857 | 0.954 | nan | 1.000 |
| plateau 75/75 | 0.194 | 0.237 | 0.208 | 0.290 | nan | 0.222 |
| 2x slippage uplift >= +0.10 each span | 0.857 | 0.667 | 0.900 | 0.944 | nan | 0.000 |

For the pair-grade profile (regime-bound, Sharpe 1.5, uncorrelated) the cumulative path is: clean-only 95.5%, standalone 75.5%, gate 19.0%, own 19.0%, bootstrap 18.5%, worst-decile 18.0%, plateau 3.5%, 2x 3.0%. Why:
1. **Selection and H1/H2 positive.** With 28 and 35 weeks, a true Sharpe-1.5 book is net positive on both spans only 79% of the time it is selected, and clean selection picks an off-centre cell in 44% of books (mean planted multiplier of the selected cell 0.87).
2. **Gate 3** (conditional pass 25% for this profile) has two parts. (a) Uplift >= +0.10 on all of clean, H1, H2: the sleeve adds a median +0.25/+0.32/+0.30 (mean +0.26/+0.33/+0.32; SD 0.10/0.32/0.27) uncorrelated, but H1 and H2 are 28 and 35 weeks, so the per-span pass rates are 95%/76%/78% and the three-span pass is 54%. (b) Worst week not worse by more than 20% of the risk share: given (a), only 47% pass, because a 20% sleeve of weekly SD about $12k can add -$16k or more in a pair-bad week (the pair's worst week is -$82k and it has 17 weeks below the worst decile). Any positive correlation with the pair removes the benefit (rho +0.3: gate 3 conditional pass 1%; rho +0.6: negative uplift at Sharpe 1.0 and <= 2% at 2.0).
3. **Plateau.** With adjacent-cell edge 0.80 and independent trade noise on 20-40% of each cell's trades, a neighbour keeps 75% of the uplift about half the time; three of four are needed. With the planted plateau real, this gate removes about 80% of otherwise-qualifying books, as much as gate 3.
4. The own timing-destroyed null passes every positive-edge book that reached it (conditional 100%: random-entry nulls with the cost drag sit near Sharpe -0.4, so any real edge clears p95; this gate is non-discriminating on the power side, as FA4 found it on the false-positive side: 89%). Bootstrap (97-100% for uncorrelated Sharpe >= 1.5), worst-decile correlation (86-97%) and 2x slippage (67-94%; +$10 per trade on about 6,300 trades against a $70-110 per trade planted edge) remove 0-33% together.

## 6. Verification of the planted books (means over books)

| regime | target | rho | real_SR_pairwin | real_rho | ERA_SR |
|---|---|---|---|---|---|
| regime | 0.50 | 0.00 | 0.52 | 0.01 | -0.53 |
| regime | 0.50 | 0.30 | 0.51 | 0.30 | -0.40 |
| regime | 0.50 | 0.60 | 0.52 | 0.60 | -0.28 |
| regime | 0.75 | 0.00 | 0.75 | 0.01 | -0.63 |
| regime | 0.75 | 0.30 | 0.75 | 0.30 | -0.43 |
| regime | 0.75 | 0.60 | 0.75 | 0.60 | -0.31 |
| regime | 1.00 | 0.00 | 1.00 | 0.01 | -0.70 |
| regime | 1.00 | 0.30 | 1.00 | 0.30 | -0.55 |
| regime | 1.00 | 0.60 | 1.00 | 0.60 | -0.36 |
| regime | 1.50 | 0.00 | 1.50 | 0.02 | -0.70 |
| regime | 1.50 | 0.30 | 1.50 | 0.30 | -0.62 |
| regime | 1.50 | 0.60 | 1.50 | 0.60 | -0.39 |
| regime | 2.00 | 0.00 | 2.00 | 0.02 | -0.79 |
| regime | 2.00 | 0.30 | 2.00 | 0.30 | -0.59 |
| regime | 2.00 | 0.60 | 2.00 | 0.60 | -0.38 |
| stationary | 0.50 | 0.00 | 0.52 | 0.01 | -0.15 |
| stationary | 0.50 | 0.30 | 0.52 | 0.30 | -0.18 |
| stationary | 0.50 | 0.60 | 0.51 | 0.60 | -0.09 |
| stationary | 0.75 | 0.00 | 0.76 | 0.00 | -0.09 |
| stationary | 0.75 | 0.30 | 0.76 | 0.30 | -0.00 |
| stationary | 0.75 | 0.60 | 0.75 | 0.60 | 0.01 |
| stationary | 1.00 | 0.00 | 1.00 | 0.01 | 0.19 |
| stationary | 1.00 | 0.30 | 1.00 | 0.30 | 0.16 |
| stationary | 1.00 | 0.60 | 1.00 | 0.60 | 0.16 |
| stationary | 1.50 | 0.00 | 1.50 | 0.01 | 0.63 |
| stationary | 1.50 | 0.30 | 1.50 | 0.30 | 0.51 |
| stationary | 1.50 | 0.60 | 1.50 | 0.60 | 0.45 |
| stationary | 2.00 | 0.00 | 2.00 | 0.02 | 1.05 |
| stationary | 2.00 | 0.30 | 2.00 | 0.30 | 0.90 |
| stationary | 2.00 | 0.60 | 2.00 | 0.60 | 0.77 |

## 7. False-positive rate of the same chain (zero-edge books; consistency with FA4)

| rho | books | selected | H | G3 | null | boot | full_chain | gate3_spans_only |
|---|---|---|---|---|---|---|---|---|
| 0.000 | 200.000 | 0.520 | 0.085 | 1.000 | 1.000 | 1.000 | 0.000 | 4.000 |
| 0.300 | 200.000 | 0.395 | 0.145 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 |
| 0.600 | 200.000 | 0.260 | 0.115 | 0.000 | 0.000 | 0.000 | 0.000 | 0.000 |

Counts of books out of 200 per correlation level. Full chain: 0 of 600; gate 3 alone: 1 of 600 (0.5% of books, 1-2% of selected books; FA4: 3.5% of selected cells through gate 3 over a 10-cell selection, 0 of 25,664 through the full chain). The 95% upper bound for the full chain is 0.5% of books here and 0.012% in FA4. Selection passes only 26-52% of zero-edge books because the cost drag makes most cells net negative.

## 8. Implications

* Calibrated for false positives, the chain is not calibrated for power: for books of the pair's quality it admits at most about 1 in 5 at LEAD-grade and 1 in 30 at full FOUND-PENDING-equivalent when uncorrelated, and almost none when correlated with the pair by +0.3 or more. The failure is dominated by gate 3 (three-span additive uplift against a very strong base) and the plateau, not by the null or the bootstrap.
* Therefore: (i) a LEAD that fails gate 3 or the plateau but passes the standalone gates is not evidence of no edge; (ii) the standalone track (H1/H2 net positive, null, bootstrap, plateau, 2x slip) detects a Sharpe-1.5 uncorrelated book 18% of the time (stationary 21%), against a standalone-chain false-positive rate on zero-edge books of 1-4.5% (additive chain 0/600); its power is also modest; (iii) the re-ranking of LEADs should use the standalone track and the ranking by Sharpe with the best-of-N null (item 4), not gate 3; (iv) sample length is the binding constraint: H1 and H2 together are 63 weeks, so a true Sharpe-1.0 book is net positive on both only about half of the time.
* Caveat on realism: the planted edge is a constant per-trade drift on random-timed trades with real noise; real edges are lumpier and regime-dependent, so power on real edges is likely lower. The plateau result depends on the planted decay rule (80% at the adjacent step); with a flatter plateau (97%) the pair-grade full-chain rate rises to 12% (table above). The base pair's own strength (H1/H2 Sharpe 3.1/2.4) is the reason the additive gate is hard; against a weaker base the same books would pass much more often.

DONE POWER
