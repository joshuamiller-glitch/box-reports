# REPORT POWER2 - METHOD-2 power on the planted books (DIRECTIVE METHOD-2 item 5)

Written 2026-10-17 by worker FA. Harness: code/census/night_ins/ap_m2.py (API: outputs/methods2/M2_API.md). Experiment code: ap_power2.py (configuration sweep), ap_power2b.py / ap_power2c.py (final runs, nulls, beta families), ap_power2_report.py. Data: outputs/autopilot/power/power2_*.csv (sweep), power2b_*.csv (final), power2c_*.csv (beta). Planted families = the REPORT_POWER construction regenerated at daily level on the 2,040 real-NQ-bar noise worlds restricted to the harness window 2023-02-01..2026-10-16 (50 cells, 80% and 97% neighbour decay, correlation {0,0.3,0.6} with the live pair, Sharpe {0.5,0.75,1.0,1.5,2.0} defined on the centre cell over the window). No real family was scored; all tuning is on planted and zero-edge books.

## 1. Result and recommended configuration (PRE-REGISTERED HERE, before any real family is scored)

**Recommended: fit 12 months / read 3 / step 3, ensemble rule `tilt` (weights proportional to positive fit-window Sharpe; cells scaled to unit SD on the fit window), null (c) custom drift-matched random-entry copies where a simulator exists, otherwise (b) sign-flip for two-sided families only; verdict gates a-d and best-of-F rank >= 0.95.** First OOS week is 2024-02 (about 142 OOS weeks), halves 2024-02..2025-04 and 2025-05..2026-10. The directive's default (9/3/3 equal weight) and 12/6/6 tilt are reported beside it.

Against the targets (12/3/3 tilt, custom null): zero-edge false-positive rate 1.7% (target <= 5%: MET); long-biased beta families with the null matched to their drift 2.5-3% (MET; with an unmatched null 5.5-9% and with sign-flip 2.5-8%: NOT met); power at true Sharpe 1.5 38% (decay 80%, uncorrelated) and 90% (decay 97%) against a target of 70%: MET only when the neighbourhood is flat; power at true Sharpe 1.0 4% / 42% against a target of 50%: NOT met, and not attainable: see section 3.

## 2. Note on the null deviation (for the user)

The directive's family null shifts every cell by the same random offset. That null is not a valid test of the OOS Sharpe. A circular shift re-uses the same weeks of data, so the OOS Sharpe of a shifted copy barely moves (null SD about 0.15) whereas the Sharpe of a genuinely new zero-edge family has SD about 0.58 over 142 weeks; the shifted null therefore either cannot reject a stationary edge (raw shift keeps the drift: power 0-38% even at Sharpe 2.0 uncorrelated) or, if demeaned, is so narrow that a zero-edge family with a lucky draw ranks 0.985 (smoke test). I replaced it by two calibrated nulls and ran all three: (b) sign-flip (one random sign per ISO week on all cells, null SD 0.57, matches zero-edge worlds) and (c) re-simulated random-entry copies. Sign-flip removes drift, so it passes long-biased beta families (2.5-16% false positives, rising with the beta share and with less selective ensemble rules); the required null is therefore family-type dependent: one-sided / long-biased families need (c) with the same side balance and clock, two-sided families can use (b) or (c). The user decides whether to adopt the deviation; the shifted-null results are in every table.

## 3. Why the 50% / 70% targets are what they are (oracle ceiling and dilution)

* **Ceiling.** An OOS test of 142 weeks at one-sided 5% cannot detect a true Sharpe of 1.0 more than 50% of the time even if the family were exactly the single true series (z = SR x sqrt(142/52) = 1.65, power = Phi(z - 1.645)); at 0.5, 0.75, 1.5, 2.0 the ceilings are 21%, 34%, 80%, 95%; the both-halves-positive gate lowers each further. The target of >= 50% at 1.0 equals the ceiling and is unattainable by any estimator on this window; with 155 OOS weeks (9/3/3) the ceiling at 1.0 is 53%.
* **Dilution.** The planted edge sits in the centre cell and decays off-centre (80% at the adjacent step), so the equal-weight ensemble of 50 cells has a Sharpe well below the centre cell's: at decay 80% a centre Sharpe of 1.5 gives a full-window ensemble Sharpe of about 0.4 (equal weight) and an OOS Sharpe of about 0.9 with the tilt rule; at 97% decay about 1.0 and 1.5. The tilt rule recovers most of the dilution without picking cells; equal weighting does not. Whether this dilution is a defect or the correct treatment of a family whose edge is concentrated is a modelling choice: a real mechanism with a broad plateau behaves like the 97% case.

## 4. Configuration sweep (planted books only, 40 families per design cell, pooled over correlations unless stated; null (b) sign-flip and (c) custom)

| config | null | power 1.0 (80% plateau, rho0) | power 1.0 (97% plateau, rho0) | power 1.0 (all cells avg) | power 1.5 (80% plateau, rho0) | power 1.5 (97% plateau, rho0) | power 1.5 (all cells avg) | FP zero-edge |
|---|---|---|---|---|---|---|---|---|
| 12,3,3,ew | signflip | 0.00 | 0.30 | 0.19 | 0.12 | 0.65 | 0.45 | 0.01 |
| 12,3,3,ew | custom | 0.03 | 0.33 | 0.23 | 0.12 | 0.65 | 0.49 | 0.03 |
| 12,3,3,tilt | signflip | 0.03 | 0.35 | 0.30 | 0.25 | 0.82 | 0.65 | 0.01 |
| 12,3,3,tilt | custom | 0.05 | 0.38 | 0.33 | 0.38 | 0.88 | 0.73 | 0.02 |
| 12,6,6,ew | signflip | 0.00 | 0.30 | 0.20 | 0.10 | 0.68 | 0.45 | 0.01 |
| 12,6,6,ew | custom | 0.03 | 0.35 | 0.25 | 0.15 | 0.70 | 0.51 | 0.03 |
| 12,6,6,tilt | signflip | 0.03 | 0.40 | 0.32 | 0.35 | 0.88 | 0.68 | 0.01 |
| 12,6,6,tilt | custom | 0.03 | 0.38 | 0.32 | 0.38 | 0.90 | 0.72 | 0.02 |
| 6,3,3,ew | signflip | 0.00 | 0.28 | 0.11 | 0.05 | 0.55 | 0.37 | 0.01 |
| 6,3,3,ew | custom | 0.00 | 0.35 | 0.14 | 0.10 | 0.65 | 0.44 | 0.01 |
| 6,3,3,tilt | signflip | 0.03 | 0.35 | 0.20 | 0.10 | 0.88 | 0.57 | 0.03 |
| 6,3,3,tilt | custom | 0.03 | 0.40 | 0.20 | 0.12 | 0.85 | 0.58 | 0.03 |
| 9,3,3,ew | signflip | 0.05 | 0.25 | 0.21 | 0.15 | 0.60 | 0.50 | 0.02 |
| 9,3,3,ew | custom | 0.05 | 0.25 | 0.25 | 0.15 | 0.75 | 0.56 | 0.03 |
| 9,3,3,posfit | signflip | 0.00 | 0.30 | 0.23 | 0.17 | 0.82 | 0.57 | 0.03 |
| 9,3,3,posfit | custom | 0.00 | 0.33 | 0.25 | 0.20 | 0.88 | 0.60 | 0.03 |
| 9,3,3,tilt | signflip | 0.00 | 0.28 | 0.26 | 0.25 | 0.90 | 0.65 | 0.04 |
| 9,3,3,tilt | custom | 0.00 | 0.35 | 0.29 | 0.25 | 0.90 | 0.67 | 0.05 |

Reading: longer fit windows and the tilt rule raise power; 12/3/3 and 12/6/6 with tilt are best at false-positive <= 2%; 9/3/3 tilt has FP up to 5% (marginal); 6/3/3 is worse (fit windows of 6 months are too noisy). 12/3/3 tilt was chosen over 12/6/6 tilt for the same power with 4 read windows a year, giving a finer OOS series.

## 5. Final runs (200 families per design cell: 6,000 planted + 600 zero-edge + 2 x 100 late-start + 2 x 200 beta families per configuration)

### Configuration 12,3,3,tilt (fit/read/step months, ensemble rule) - 7200 families, 142 OOS weeks

**Power, (a) shifted null - the literal directive spec (all cells circularly shifted by one common offset)** (fraction of 200 families passing gates a-d; stationary and regime-bound-from-2023-01 coincide inside the harness window)

| plateau | true Sharpe | rho=0.0 | rho=0.3 | rho=0.6 |
|---|---|---|---|---|
| decay 80% | 0.50 | 0.01 | 0.01 | 0.03 |
| decay 80% | 0.75 | 0.01 | 0.03 | 0.06 |
| decay 80% | 1.00 | 0.01 | 0.04 | 0.10 |
| decay 80% | 1.50 | 0.04 | 0.11 | 0.26 |
| decay 80% | 2.00 | 0.05 | 0.12 | 0.29 |
| decay 97% | 0.50 | 0.01 | 0.04 | 0.12 |
| decay 97% | 0.75 | 0.04 | 0.06 | 0.17 |
| decay 97% | 1.00 | 0.04 | 0.10 | 0.26 |
| decay 97% | 1.50 | 0.06 | 0.15 | 0.38 |
| decay 97% | 2.00 | 0.05 | 0.14 | 0.36 |

**Power, (b) sign-flip null (one random sign per ISO week on all cells)** (fraction of 200 families passing gates a-d; stationary and regime-bound-from-2023-01 coincide inside the harness window)

| plateau | true Sharpe | rho=0.0 | rho=0.3 | rho=0.6 |
|---|---|---|---|---|
| decay 80% | 0.50 | 0.03 | 0.01 | 0.03 |
| decay 80% | 0.75 | 0.03 | 0.04 | 0.06 |
| decay 80% | 1.00 | 0.02 | 0.09 | 0.11 |
| decay 80% | 1.50 | 0.28 | 0.38 | 0.54 |
| decay 80% | 2.00 | 0.60 | 0.81 | 0.95 |
| decay 97% | 0.50 | 0.06 | 0.04 | 0.12 |
| decay 97% | 0.75 | 0.14 | 0.17 | 0.21 |
| decay 97% | 1.00 | 0.38 | 0.48 | 0.56 |
| decay 97% | 1.50 | 0.85 | 0.92 | 0.98 |
| decay 97% | 2.00 | 0.99 | 1.00 | 1.00 |

**Power, (c) custom random-entry null (re-simulated zero-edge copies of the same 50-cell grid, same clock/trade counts)** (fraction of 200 families passing gates a-d; stationary and regime-bound-from-2023-01 coincide inside the harness window)

| plateau | true Sharpe | rho=0.0 | rho=0.3 | rho=0.6 |
|---|---|---|---|---|
| decay 80% | 0.50 | 0.03 | 0.01 | 0.03 |
| decay 80% | 0.75 | 0.04 | 0.06 | 0.07 |
| decay 80% | 1.00 | 0.04 | 0.12 | 0.15 |
| decay 80% | 1.50 | 0.38 | 0.45 | 0.72 |
| decay 80% | 2.00 | 0.67 | 0.83 | 0.97 |
| decay 97% | 0.50 | 0.06 | 0.06 | 0.15 |
| decay 97% | 0.75 | 0.18 | 0.21 | 0.29 |
| decay 97% | 1.00 | 0.42 | 0.55 | 0.67 |
| decay 97% | 1.50 | 0.90 | 0.93 | 0.98 |
| decay 97% | 2.00 | 0.99 | 1.00 | 1.00 |

**Dilution: what Sharpe the ensemble actually has** (means over families, all correlations)

| level_0 | level_1 | full-window Sharpe of the equal-weight ensemble | mean OOS Sharpe (this rule) | oracle power of a one-sided 5% test at the OOS Sharpe | oracle power at the TRUE centre-cell Sharpe |
|---|---|---|---|---|---|
| decay 80% | 0.50 | 0.05 | 0.24 | 0.11 | 0.21 |
| decay 80% | 0.75 | 0.15 | 0.42 | 0.17 | 0.34 |
| decay 80% | 1.00 | 0.21 | 0.53 | 0.22 | 0.50 |
| decay 80% | 1.50 | 0.42 | 0.94 | 0.46 | 0.80 |
| decay 80% | 2.00 | 0.61 | 1.27 | 0.67 | 0.95 |
| decay 97% | 0.50 | 0.33 | 0.51 | 0.21 | 0.21 |
| decay 97% | 0.75 | 0.50 | 0.73 | 0.33 | 0.34 |
| decay 97% | 1.00 | 0.69 | 0.98 | 0.49 | 0.50 |
| decay 97% | 1.50 | 1.02 | 1.48 | 0.79 | 0.80 |
| decay 97% | 2.00 | 1.40 | 1.95 | 0.94 | 0.95 |

**False-positive rate** (families with no timing edge)

| family | N | null | FP |
|---|---|---|---|
| zero-edge (3 correlations pooled) | 600 | shifted | 0.010 |
| zero-edge (3 correlations pooled) | 600 | sign-flip | 0.013 |
| zero-edge (3 correlations pooled) | 600 | custom (b=0 zero-edge copies) | 0.017 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.37) | 200 | shifted | 0.000 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.37) | 200 | sign-flip | 0.080 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.37) | 200 | custom drift-matched (copies carry the same beta) | 0.025 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.37) | 200 | custom NOT drift-matched (zero-edge copies without beta) | 0.090 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.52) | 200 | shifted | 0.000 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.52) | 200 | sign-flip | 0.025 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.52) | 200 | custom drift-matched (copies carry the same beta) | 0.030 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.52) | 200 | custom NOT drift-matched (zero-edge copies without beta) | 0.055 |

**Edge that starts inside the window (2025-01, zero before)**, uncorrelated, decay 80% (n=100 per size): power under sign-flip / custom: Sharpe 1.5: 0.04 / 0.06, Sharpe 2.0: 0.07 / 0.08.


### Configuration 9,3,3,ew (fit/read/step months, ensemble rule) - 7200 families, 155 OOS weeks

**Power, (a) shifted null - the literal directive spec (all cells circularly shifted by one common offset)** (fraction of 200 families passing gates a-d; stationary and regime-bound-from-2023-01 coincide inside the harness window)

| plateau | true Sharpe | rho=0.0 | rho=0.3 | rho=0.6 |
|---|---|---|---|---|
| decay 80% | 0.50 | 0.01 | 0.01 | 0.05 |
| decay 80% | 0.75 | 0.01 | 0.04 | 0.08 |
| decay 80% | 1.00 | 0.01 | 0.07 | 0.10 |
| decay 80% | 1.50 | 0.01 | 0.08 | 0.28 |
| decay 80% | 2.00 | 0.03 | 0.11 | 0.44 |
| decay 97% | 0.50 | 0.02 | 0.06 | 0.18 |
| decay 97% | 0.75 | 0.04 | 0.10 | 0.30 |
| decay 97% | 1.00 | 0.03 | 0.17 | 0.57 |
| decay 97% | 1.50 | 0.06 | 0.20 | 0.67 |
| decay 97% | 2.00 | 0.05 | 0.20 | 0.62 |

**Power, (b) sign-flip null (one random sign per ISO week on all cells)** (fraction of 200 families passing gates a-d; stationary and regime-bound-from-2023-01 coincide inside the harness window)

| plateau | true Sharpe | rho=0.0 | rho=0.3 | rho=0.6 |
|---|---|---|---|---|
| decay 80% | 0.50 | 0.01 | 0.01 | 0.05 |
| decay 80% | 0.75 | 0.01 | 0.04 | 0.04 |
| decay 80% | 1.00 | 0.02 | 0.07 | 0.07 |
| decay 80% | 1.50 | 0.10 | 0.20 | 0.24 |
| decay 80% | 2.00 | 0.17 | 0.35 | 0.48 |
| decay 97% | 0.50 | 0.03 | 0.07 | 0.11 |
| decay 97% | 0.75 | 0.14 | 0.16 | 0.24 |
| decay 97% | 1.00 | 0.25 | 0.39 | 0.58 |
| decay 97% | 1.50 | 0.62 | 0.77 | 0.92 |
| decay 97% | 2.00 | 0.90 | 0.93 | 0.99 |

**Power, (c) custom random-entry null (re-simulated zero-edge copies of the same 50-cell grid, same clock/trade counts)** (fraction of 200 families passing gates a-d; stationary and regime-bound-from-2023-01 coincide inside the harness window)

| plateau | true Sharpe | rho=0.0 | rho=0.3 | rho=0.6 |
|---|---|---|---|---|
| decay 80% | 0.50 | 0.03 | 0.02 | 0.06 |
| decay 80% | 0.75 | 0.03 | 0.08 | 0.10 |
| decay 80% | 1.00 | 0.03 | 0.12 | 0.15 |
| decay 80% | 1.50 | 0.10 | 0.24 | 0.36 |
| decay 80% | 2.00 | 0.21 | 0.41 | 0.58 |
| decay 97% | 0.50 | 0.03 | 0.10 | 0.23 |
| decay 97% | 0.75 | 0.18 | 0.24 | 0.38 |
| decay 97% | 1.00 | 0.29 | 0.45 | 0.74 |
| decay 97% | 1.50 | 0.66 | 0.81 | 0.95 |
| decay 97% | 2.00 | 0.92 | 0.94 | 0.99 |

**Dilution: what Sharpe the ensemble actually has** (means over families, all correlations)

| level_0 | level_1 | full-window Sharpe of the equal-weight ensemble | mean OOS Sharpe (this rule) | oracle power of a one-sided 5% test at the OOS Sharpe | oracle power at the TRUE centre-cell Sharpe |
|---|---|---|---|---|---|
| decay 80% | 0.50 | 0.05 | 0.21 | 0.10 | 0.22 |
| decay 80% | 0.75 | 0.15 | 0.34 | 0.14 | 0.36 |
| decay 80% | 1.00 | 0.21 | 0.37 | 0.16 | 0.53 |
| decay 80% | 1.50 | 0.42 | 0.61 | 0.28 | 0.83 |
| decay 80% | 2.00 | 0.61 | 0.78 | 0.38 | 0.96 |
| decay 97% | 0.50 | 0.33 | 0.51 | 0.22 | 0.22 |
| decay 97% | 0.75 | 0.50 | 0.69 | 0.33 | 0.36 |
| decay 97% | 1.00 | 0.69 | 0.87 | 0.44 | 0.53 |
| decay 97% | 1.50 | 1.02 | 1.22 | 0.68 | 0.83 |
| decay 97% | 2.00 | 1.40 | 1.59 | 0.86 | 0.96 |

**False-positive rate** (families with no timing edge)

| family | N | null | FP |
|---|---|---|---|
| zero-edge (3 correlations pooled) | 600 | shifted | 0.013 |
| zero-edge (3 correlations pooled) | 600 | sign-flip | 0.013 |
| zero-edge (3 correlations pooled) | 600 | custom (b=0 zero-edge copies) | 0.025 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.53) | 200 | shifted | 0.005 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.53) | 200 | sign-flip | 0.125 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.53) | 200 | custom drift-matched (copies carry the same beta) | 0.050 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.53) | 200 | custom NOT drift-matched (zero-edge copies without beta) | 0.155 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.74) | 200 | shifted | 0.000 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.74) | 200 | sign-flip | 0.160 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.74) | 200 | custom drift-matched (copies carry the same beta) | 0.025 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.74) | 200 | custom NOT drift-matched (zero-edge copies without beta) | 0.250 |

**Edge that starts inside the window (2025-01, zero before)**, uncorrelated, decay 80% (n=100 per size): power under sign-flip / custom: Sharpe 1.5: 0.02 / 0.03, Sharpe 2.0: 0.04 / 0.05.


### Configuration 12,6,6,tilt (fit/read/step months, ensemble rule) - 7200 families, 142 OOS weeks

**Power, (a) shifted null - the literal directive spec (all cells circularly shifted by one common offset)** (fraction of 200 families passing gates a-d; stationary and regime-bound-from-2023-01 coincide inside the harness window)

| plateau | true Sharpe | rho=0.0 | rho=0.3 | rho=0.6 |
|---|---|---|---|---|
| decay 80% | 0.50 | 0.01 | 0.02 | 0.02 |
| decay 80% | 0.75 | 0.03 | 0.01 | 0.06 |
| decay 80% | 1.00 | 0.01 | 0.04 | 0.10 |
| decay 80% | 1.50 | 0.06 | 0.11 | 0.26 |
| decay 80% | 2.00 | 0.07 | 0.13 | 0.26 |
| decay 97% | 0.50 | 0.01 | 0.03 | 0.09 |
| decay 97% | 0.75 | 0.06 | 0.07 | 0.11 |
| decay 97% | 1.00 | 0.04 | 0.11 | 0.23 |
| decay 97% | 1.50 | 0.04 | 0.15 | 0.34 |
| decay 97% | 2.00 | 0.07 | 0.15 | 0.36 |

**Power, (b) sign-flip null (one random sign per ISO week on all cells)** (fraction of 200 families passing gates a-d; stationary and regime-bound-from-2023-01 coincide inside the harness window)

| plateau | true Sharpe | rho=0.0 | rho=0.3 | rho=0.6 |
|---|---|---|---|---|
| decay 80% | 0.50 | 0.03 | 0.03 | 0.03 |
| decay 80% | 0.75 | 0.04 | 0.03 | 0.06 |
| decay 80% | 1.00 | 0.03 | 0.09 | 0.10 |
| decay 80% | 1.50 | 0.34 | 0.42 | 0.58 |
| decay 80% | 2.00 | 0.62 | 0.83 | 0.97 |
| decay 97% | 0.50 | 0.04 | 0.04 | 0.07 |
| decay 97% | 0.75 | 0.17 | 0.19 | 0.20 |
| decay 97% | 1.00 | 0.38 | 0.49 | 0.56 |
| decay 97% | 1.50 | 0.87 | 0.93 | 0.96 |
| decay 97% | 2.00 | 0.99 | 1.00 | 1.00 |

**Power, (c) custom random-entry null (re-simulated zero-edge copies of the same 50-cell grid, same clock/trade counts)** (fraction of 200 families passing gates a-d; stationary and regime-bound-from-2023-01 coincide inside the harness window)

| plateau | true Sharpe | rho=0.0 | rho=0.3 | rho=0.6 |
|---|---|---|---|---|
| decay 80% | 0.50 | 0.04 | 0.03 | 0.03 |
| decay 80% | 0.75 | 0.04 | 0.04 | 0.07 |
| decay 80% | 1.00 | 0.04 | 0.10 | 0.14 |
| decay 80% | 1.50 | 0.34 | 0.47 | 0.68 |
| decay 80% | 2.00 | 0.64 | 0.85 | 0.96 |
| decay 97% | 0.50 | 0.04 | 0.04 | 0.09 |
| decay 97% | 0.75 | 0.19 | 0.20 | 0.20 |
| decay 97% | 1.00 | 0.41 | 0.54 | 0.62 |
| decay 97% | 1.50 | 0.88 | 0.94 | 0.97 |
| decay 97% | 2.00 | 0.99 | 1.00 | 1.00 |

**Dilution: what Sharpe the ensemble actually has** (means over families, all correlations)

| level_0 | level_1 | full-window Sharpe of the equal-weight ensemble | mean OOS Sharpe (this rule) | oracle power of a one-sided 5% test at the OOS Sharpe | oracle power at the TRUE centre-cell Sharpe |
|---|---|---|---|---|---|
| decay 80% | 0.50 | 0.05 | 0.24 | 0.11 | 0.21 |
| decay 80% | 0.75 | 0.15 | 0.42 | 0.17 | 0.34 |
| decay 80% | 1.00 | 0.21 | 0.55 | 0.23 | 0.50 |
| decay 80% | 1.50 | 0.42 | 0.97 | 0.48 | 0.80 |
| decay 80% | 2.00 | 0.61 | 1.31 | 0.70 | 0.95 |
| decay 97% | 0.50 | 0.33 | 0.51 | 0.21 | 0.21 |
| decay 97% | 0.75 | 0.50 | 0.74 | 0.34 | 0.34 |
| decay 97% | 1.00 | 0.69 | 0.99 | 0.50 | 0.50 |
| decay 97% | 1.50 | 1.02 | 1.49 | 0.79 | 0.80 |
| decay 97% | 2.00 | 1.40 | 1.99 | 0.95 | 0.95 |

**False-positive rate** (families with no timing edge)

| family | N | null | FP |
|---|---|---|---|
| zero-edge (3 correlations pooled) | 600 | shifted | 0.012 |
| zero-edge (3 correlations pooled) | 600 | sign-flip | 0.015 |
| zero-edge (3 correlations pooled) | 600 | custom (b=0 zero-edge copies) | 0.015 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.44) | 200 | shifted | 0.000 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.44) | 200 | sign-flip | 0.090 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.44) | 200 | custom drift-matched (copies carry the same beta) | 0.025 |
| beta family 0.3 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.44) | 200 | custom NOT drift-matched (zero-edge copies without beta) | 0.085 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.60) | 200 | shifted | 0.000 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.60) | 200 | sign-flip | 0.035 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.60) | 200 | custom drift-matched (copies carry the same beta) | 0.030 |
| beta family 0.6 contracts of NQ buy-and-hold added to a zero-edge grid (mean OOS Sharpe 0.60) | 200 | custom NOT drift-matched (zero-edge copies without beta) | 0.050 |

**Edge that starts inside the window (2025-01, zero before)**, uncorrelated, decay 80% (n=100 per size): power under sign-flip / custom: Sharpe 1.5: 0.04 / 0.04, Sharpe 2.0: 0.06 / 0.06.



## 6. Fold schedule and a regime-bound book

The harness window starts 2023-02-01, after the planted regime starts (2023-01), so inside the window a 'regime-bound' book is a stationary-edge book and the first fit window already contains the edge; stationary and regime-bound-from-2023-01 give identical results (they differ only before the window). A book whose edge starts inside the window (2025-01) has fit windows without the edge for the early folds (scales and weights estimated on noise) and the edge only in later read windows: power for that case is reported in each configuration (uncorrelated Sharpe 1.5 and 2.0: 4-9%), i.e. a late-starting edge is largely invisible to this method within the window, as expected from 12-month fits.

## 7. Which null for which family type (recommendation)

| family type | required null | reason |
|---|---|---|
| two-sided (long/short symmetric) rule, no net market exposure | custom (c) preferred, sign-flip (b) acceptable | sign-flip FP 1.3% on zero-edge, power close to (c) |
| one-sided / long-biased / positive average net exposure | custom (c) with the same side balance and clock (drift-matched) only | sign-flip removes the drift and passes beta (2.5-16%); an unmatched custom null does too (5.5-25%) |
| P&L-only family with no simulator | sign-flip plus an explicit net-exposure check (corr with NQ daily returns); treat as long-biased if beta > 0.15 | |
| any family | never the raw/demeaned circular shift as a gate | wrong null SD; reported only |

DONE POWER2

POWER2 MET (by user acceptance 2026-10-17 of the 12/3/3 tilt configuration; false-positive targets met, power targets met only for flat neighbourhoods: 70% at Sharpe 1.5 needs decay ~97%; see section 1). Real-family verdicts must report plateau breadth / power class.
