# DS3_NO_TRADE_RULES_2 - T-NO-TRADE-EXPANDED sections B, C, D: single-state rules, combinations, opposite side (NTE-1, 2026-10-31)

Research only. Prereg autopilot/NTE_prereg.md sha256 b446844d...; B/D carry list sha256 16449e8e... (PRE u X' selection, logged before the recent look); combination carry list sha256 459876f7...; learned model: weekly walk-forward (no selection). UNTOUCHED never read. Units: gain PER SIGNAL (rule net - base net over all the scope's signals, N basis, so skipped winners are charged), PER CONTRACT of final lots (kept signals, rule vs base), lock-engine STACK $/wk (6 engine books, research lots, planned-lot-R locks; sized-lot-R lock variant not available for per-signal multipliers - named limitation), eqr = equal-risk gain per signal (rule mean / lot ratio - base mean; STRUCTURE), uex = gain over the lot-factor-matched uniform scaling of the base. 'skipped pts' = mean N-basis P&L per signal of the signals the rule touches under the base (what is thrown away). plc = rank of the real L6M gain among 200 random fire sets at the same count per book x session x side x era x target-distance stratum (1.00 = beats all). Tiers follow the V2 gates unsoftened: LEAD = selected (gain>0 in PRE and X') and L6M >= 0; CANDIDATE-RECENT = + gain>0 and per contract >0 in L6M and HOLD and plc >= 0.90; PASS_pre_RC = + plc >= 0.95, above MDE in L6M and HOLD, stack > 0 in L6M and HOLD (before the program-level reality check, which none of them clears cumulatively).

## PAGE 1 - the answer

* B skip (selected on PRE u X'): 308 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +0.542 / +0.595, in the single recent look L6M / HOLD / L3M = -0.282 / -0.247 / -0.225; 101 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 46, PASS_pre_RC 0.
* B size 50% / 25%: 614 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +0.338 / +0.368, in the single recent look L6M / HOLD / L3M = -0.179 / -0.156 / -0.143; 201 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 92, PASS_pre_RC 0.
* B delay 5 / 15 min: 904 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +0.330 / +0.276, in the single recent look L6M / HOLD / L3M = -0.108 / -0.096 / -0.120; 389 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 134, PASS_pre_RC 3.
* B re-target x0.5: 474 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +0.321 / +0.442, in the single recent look L6M / HOLD / L3M = -0.164 / -0.150 / -0.043; 137 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 51, PASS_pre_RC 0.
* D take-only (skip everything outside the state): 53 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +1.437 / +1.553, in the single recent look L6M / HOLD / L3M = -0.897 / -0.522 / -0.487; 8 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 2, PASS_pre_RC 0.
* D size up x1.5 / x2 inside the state: 2247 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +0.821 / +0.641, in the single recent look L6M / HOLD / L3M = +0.660 / +0.552 / +0.392; 1814 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 468, PASS_pre_RC 43.

* **Skip rules decay out of sample and size-up rules are positive by construction.** The pooled skip cells chosen on PRE u X' average +0.110 / +0.167 per signal in PRE / X' and -0.230 / -0.193 in L6M / HOLD: the states that preceded failures in 2023-25 do not keep their sign. The size-up cells (D) are positive in the recent windows because the base is positive and the states are trend-continuation states (extension in the trade direction, premium location, chase): they are reported with the uniform-scaling control (uex) and equal-risk gain (eqr), they raise lots by 1.3-1.9x (the 50-contract cap and the margin question apply), and they are STRUCTURE until a forward test.
* Cells with tier >= CANDIDATE-RECENT AND stack > 0 in both L6M and HOLD: B 67, D 240; of the B cells, 67 are pooled (ALL scope).

## 1. Selection decay by action (selected cell-scopes; gain per signal; fraction >= 0 recent)

| grp | action | base | cells | PRE | X | L3M | L6M | HOLD | Y26 | pos_L6M_HOLD | plc95 | cand | pass_pre |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| B | d15 | MKT | 219 | 0.388 | 0.369 | -0.239 | -0.209 | -0.196 | -0.502 | 0.301 | 0.082 | 26 | 1 |
| B | d15 | SPL | 200 | 0.411 | 0.369 | -0.263 | -0.250 | -0.234 | -0.586 | 0.315 | 0.085 | 26 | 0 |
| B | d5 | MKT | 236 | 0.263 | 0.203 | 0.024 | 0.017 | 0.028 | -0.179 | 0.576 | 0.131 | 41 | 2 |
| B | d5 | SPL | 249 | 0.278 | 0.189 | -0.036 | -0.025 | -0.014 | -0.283 | 0.494 | 0.072 | 41 | 0 |
| B | rt50 | MKT | 234 | 0.307 | 0.429 | -0.039 | -0.149 | -0.140 | -0.187 | 0.295 | 0.051 | 25 | 0 |
| B | rt50 | SPL | 240 | 0.335 | 0.456 | -0.047 | -0.178 | -0.160 | -0.236 | 0.283 | 0.075 | 26 | 0 |
| B | skip | MKT | 154 | 0.541 | 0.612 | -0.218 | -0.269 | -0.238 | -0.455 | 0.331 | 0.123 | 24 | 0 |
| B | skip | SPL | 154 | 0.543 | 0.577 | -0.232 | -0.295 | -0.257 | -0.425 | 0.312 | 0.123 | 22 | 0 |
| B | z25 | MKT | 155 | 0.411 | 0.450 | -0.172 | -0.210 | -0.182 | -0.354 | 0.329 | 0.123 | 24 | 0 |
| B | z25 | SPL | 153 | 0.399 | 0.430 | -0.175 | -0.226 | -0.198 | -0.328 | 0.307 | 0.124 | 22 | 0 |
| B | z50 | MKT | 152 | 0.272 | 0.303 | -0.109 | -0.134 | -0.116 | -0.222 | 0.336 | 0.125 | 24 | 0 |
| B | z50 | SPL | 154 | 0.271 | 0.289 | -0.116 | -0.148 | -0.128 | -0.212 | 0.312 | 0.123 | 22 | 0 |
| D | keeponly | MKT | 25 | 1.471 | 1.551 | -0.497 | -0.795 | -0.435 | -2.000 | 0.160 | 0.280 | 1 | 0 |
| D | keeponly | SPL | 28 | 1.406 | 1.555 | -0.478 | -0.988 | -0.600 | -1.771 | 0.143 | 0.286 | 1 | 0 |
| D | u150 | MKT | 562 | 0.565 | 0.429 | 0.278 | 0.449 | 0.374 | 0.587 | 0.799 | 0.153 | 122 | 10 |
| D | u150 | SPL | 561 | 0.530 | 0.425 | 0.244 | 0.431 | 0.362 | 0.509 | 0.793 | 0.168 | 112 | 11 |
| D | u200 | MKT | 563 | 1.128 | 0.861 | 0.557 | 0.898 | 0.746 | 1.173 | 0.799 | 0.153 | 121 | 11 |
| D | u200 | SPL | 561 | 1.060 | 0.849 | 0.488 | 0.862 | 0.726 | 1.014 | 0.795 | 0.166 | 113 | 11 |

## 2. Section B - best single-state B cells that are CANDIDATE-RECENT or better with the stack > 0 in L6M and HOLD (sorted by stack L6M; PRE / X' = gain per signal the cell was selected on; the recent look is one look)

168 cells; pooled (ALL) first, then book / session scopes.

### 2a. pooled
| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| set.ahead20_set11_fresh | skip | SPL | ALL | 0.28 | 0.45 | 0.47 | 0.36 | 0.45 | 1.03 | 1.06 | 0.93 | 15.62 | -2.32 | 1.00 | 30117.59 | 26652.50 | 8879.78 | 3150.16 | 1.03 | 0.87 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | skip | MKT | ALL | 0.31 | 0.40 | 0.39 | 0.31 | 0.42 | 0.97 | 1.02 | 0.95 | 15.62 | -2.02 | 1.00 | 29833.67 | 25283.76 | 11298.83 | 5714.07 | 0.97 | 0.82 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | z25 | SPL | ALL | 0.21 | 0.34 | 0.36 | 0.27 | 0.34 | 0.74 | 0.76 | 0.70 | 15.62 | -2.32 | 1.00 | 23422.21 | 20328.31 | 2350.29 | 1623.58 | 0.74 | 0.65 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | z25 | MKT | ALL | 0.23 | 0.30 | 0.29 | 0.24 | 0.32 | 0.70 | 0.73 | 0.71 | 15.62 | -2.02 | 1.00 | 21304.64 | 17068.67 | 6320.20 | 2159.90 | 0.70 | 0.62 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | z50 | SPL | ALL | 0.14 | 0.23 | 0.24 | 0.18 | 0.23 | 0.47 | 0.48 | 0.47 | 15.62 | -2.32 | 1.00 | 16935.84 | 14450.24 | 1203.69 | 2460.41 | 0.47 | 0.44 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | z50 | MKT | ALL | 0.15 | 0.20 | 0.20 | 0.16 | 0.21 | 0.45 | 0.46 | 0.48 | 15.62 | -2.02 | 1.00 | 15803.46 | 12669.46 | 1346.85 | 1662.48 | 0.45 | 0.41 | CANDIDATE-RECENT |
| st.f60_vs_med>=1.809 | d15 | SPL | ALL | 0.12 | 0.05 | 0.50 | 0.23 | 0.22 | 0.37 | 0.32 | 0.70 | 11.68 | -3.05 | 0.99 | 10697.12 | 9523.70 | 53.95 | 6.75 | 0.37 | 0.35 | CANDIDATE-RECENT |
| st.f60_vs_med>=1.809 | d15 | MKT | ALL | 0.11 | 0.04 | 0.45 | 0.19 | 0.18 | 0.32 | 0.27 | 0.71 | 11.68 | -2.92 | 0.99 | 10517.91 | 9099.67 | 2578.03 | -358.64 | 0.32 | 0.31 | CANDIDATE-RECENT |
| eng.opp_flip_within60 | rt50 | SPL | ALL | 0.02 | 0.09 | 0.17 | 0.08 | 0.05 | 0.09 | 0.05 | 0.34 | 9.04 | -0.24 | 0.98 | 7978.59 | 6972.93 | -4042.84 | -2418.07 | 0.09 | 0.09 | CANDIDATE-RECENT |
| st.sig_vel30<=-3.6 | d5 | MKT | ALL | 0.05 | 0.12 | 0.33 | 0.17 | 0.17 | 0.22 | 0.21 | 0.32 | 11.16 | 2.32 | 0.97 | 7815.29 | 6306.57 | -7322.21 | 3169.78 | 0.22 | 0.22 | CANDIDATE-RECENT |
| xm.es15s<=-1 | d5 | SPL | ALL | 0.08 | 0.03 | 0.29 | 0.14 | 0.15 | 0.19 | 0.19 | 0.32 | 9.72 | -0.98 | 0.94 | 7480.32 | 6750.94 | -8877.99 | 723.90 | 0.19 | 0.19 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | rt50 | SPL | ALL | 0.05 | 0.11 | 0.33 | 0.21 | 0.18 | 0.22 | 0.19 | 0.75 | 15.62 | -2.32 | 1.00 | 6995.07 | 5980.26 | -587.28 | -5765.31 | 0.22 | 0.22 | CANDIDATE-RECENT |
| st.sig_vel30<=-3.6 | d5 | SPL | ALL | 0.06 | 0.11 | 0.36 | 0.17 | 0.18 | 0.22 | 0.21 | 0.38 | 11.16 | 2.39 | 0.99 | 6220.54 | 5512.82 | -6876.80 | 2854.62 | 0.22 | 0.21 | CANDIDATE-RECENT |
| st.rv30_ann>=46.11 | rt50 | SPL | ALL | 0.04 | 0.16 | 0.34 | 0.20 | 0.17 | 0.21 | 0.17 | 0.47 | 6.14 | -6.82 | 1.00 | 6171.04 | 5293.15 | -4333.42 | -153.85 | 0.21 | 0.21 | CANDIDATE-RECENT |
| st.sig_vol60>=2533 | d5 | MKT | ALL | 0.01 | 0.23 | 0.56 | 0.24 | 0.22 | 0.36 | 0.31 | 0.69 | 8.65 | 0.55 | 0.97 | 5660.23 | 5048.91 | -664.36 | 8868.50 | 0.36 | 0.35 | CANDIDATE-RECENT |
| st.prev_close_loc>=0.4225 | d15 | SPL | ALL | 0.07 | 0.09 | 0.32 | 0.24 | 0.17 | 0.31 | 0.22 | 0.32 | 6.54 | -2.58 | 1.00 | 4964.30 | 4017.13 | -5619.03 | 1580.95 | 0.31 | 0.30 | CANDIDATE-RECENT |
| st.sig_vol60>=2533 | d5 | SPL | ALL | 0.01 | 0.30 | 0.56 | 0.25 | 0.23 | 0.38 | 0.33 | 0.69 | 8.65 | 0.44 | 1.00 | 4920.89 | 4290.20 | -509.86 | 8864.35 | 0.38 | 0.36 | CANDIDATE-RECENT |
| st.1d.chop14>=60.39 | rt50 | MKT | ALL | 0.04 | 0.31 | 0.01 | 0.01 | 0.11 | 0.01 | 0.11 | 0.51 | 15.05 | 2.33 | 0.94 | 4331.40 | 8158.25 | -2178.86 | 341.47 | 0.01 | 0.01 | CANDIDATE-RECENT |
| px.loc.OR30.sidedloc<=0.2 | d15 | MKT | ALL | 0.08 | 0.07 | 0.04 | 0.08 | 0.07 | 0.12 | 0.10 | 0.19 | 7.46 | -4.20 | 0.92 | 4184.45 | 3761.33 | 4805.81 | -708.92 | 0.12 | 0.12 | CANDIDATE-RECENT |
| st.sig_delta10_s<=-26 | d5 | MKT | ALL | 0.10 | 0.11 | 0.30 | 0.21 | 0.23 | 0.28 | 0.28 | 0.34 | 9.73 | 2.68 | 0.97 | 3912.80 | 3561.70 | -4284.51 | 8763.41 | 0.28 | 0.27 | CANDIDATE-RECENT |
| st.prev_rng_atrd>=1.697 | d15 | MKT | ALL | 0.14 | 0.07 | 0.22 | 0.24 | 0.21 | 0.41 | 0.33 | 0.44 | 12.80 | -0.15 | 1.00 | 3840.61 | 3360.54 | -284.20 | -89.09 | 0.41 | 0.39 | CANDIDATE-RECENT |
| st.prev_close_loc>=0.4225 | skip | MKT | ALL | 0.05 | 0.33 | 0.04 | 0.15 | 0.06 | 0.39 | 0.25 | 0.88 | 6.54 | -2.33 | 1.00 | 3806.38 | 2165.82 | -5611.36 | 2417.18 | 0.39 | 0.36 | CANDIDATE-RECENT |
| st.rv30_ann>=46.11 | rt50 | MKT | ALL | 0.04 | 0.14 | 0.35 | 0.22 | 0.19 | 0.22 | 0.19 | 0.47 | 6.14 | -7.19 | 1.00 | 3800.49 | 3220.43 | -987.53 | -754.52 | 0.22 | 0.22 | CANDIDATE-RECENT |
| bk.sweepvol_against30>=150 | d5 | MKT | ALL | 0.03 | 0.10 | 0.48 | 0.18 | 0.14 | 0.29 | 0.22 | 0.36 | 8.36 | 1.76 | 0.93 | 3574.45 | 2715.30 | 1055.29 | 4064.36 | 0.29 | 0.28 | CANDIDATE-RECENT |
| st.prev_close_loc>=0.4225 | skip | SPL | ALL | 0.04 | 0.31 | 0.09 | 0.17 | 0.08 | 0.41 | 0.27 | 0.86 | 6.54 | -2.58 | 1.00 | 3130.49 | 1651.24 | -5857.22 | 1468.29 | 0.41 | 0.38 | CANDIDATE-RECENT |

### 2b. book / session scopes (live books first by $)
| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| bk.t_since_big_against<=300 | d15 | MKT | HM | 0.35 | 1.07 | -0.32 | 0.36 | 0.37 | 0.80 | 0.71 | 1.80 | 18.92 | 1.03 | 0.97 | 7736.84 | 7285.45 | 4095.93 | 458.66 | 0.80 | 0.73 | CANDIDATE-RECENT |
| bk.t_since_big_against<=300 | d15 | SPL | HM | 0.44 | 1.01 | -0.12 | 0.28 | 0.19 | 0.69 | 0.50 | 1.61 | 18.92 | 1.86 | 0.96 | 7268.77 | 6155.72 | 3088.59 | -916.56 | 0.69 | 0.63 | CANDIDATE-RECENT |
| st.1h.atr_ratio<=0.9103 | d5 | MKT | WT | 0.30 | 0.20 | 0.43 | 0.47 | 0.54 | 0.59 | 0.62 | 0.78 | 27.43 | -1.41 | 0.96 | 6153.95 | 6022.80 | 377.88 | 1333.76 | 0.59 | 0.56 | CANDIDATE-RECENT |
| st.sig_vel30<=-3.6 | d5 | MKT | nyam | 0.22 | 0.50 | 0.93 | 0.63 | 0.65 | 0.75 | 0.76 | 0.73 | 16.06 | -3.19 | 0.97 | 5629.11 | 4490.29 | -2573.38 | 2512.62 | 0.75 | 0.72 | CANDIDATE-RECENT |
| st.ret_ES_15m<=-4.073 | d5 | MKT | asia | 0.13 | 0.05 | 0.39 | 0.21 | 0.18 | 0.23 | 0.19 | 0.53 | 4.59 | -1.66 | 1.00 | 4897.74 | 4084.26 | -916.04 | -502.37 | 0.23 | 0.23 | CANDIDATE-RECENT |
| st.sig_intens_rel>=2.182 | d15 | SPL | PE | 0.58 | 0.43 | 1.80 | 1.01 | 0.85 | 1.15 | 0.97 | 1.56 | 25.29 | -2.77 | 0.96 | 4447.42 | 2788.39 | -809.45 | 748.92 | 1.15 | 1.07 | CANDIDATE-RECENT |
| st.prev_rng_atrd>=1.301 | d5 | MKT | KB | 0.73 | 0.09 | 2.14 | 1.33 | 1.05 | 1.40 | 1.10 | 1.97 | 34.92 | 1.12 | 0.97 | 4315.44 | 3492.92 | 1560.46 | 1405.18 | 1.40 | 1.37 | CANDIDATE-RECENT |
| day.afterbigday1p5pct | d5 | SPL | KB | 0.74 | 0.04 | 1.90 | 1.03 | 0.94 | 1.08 | 0.98 | 1.70 | 17.10 | -2.64 | 0.97 | 3908.66 | 3420.08 | 983.01 | 899.51 | 1.08 | 1.06 | CANDIDATE-RECENT |
| st.sig_delta10_s<=-26 | d15 | SPL | PE | 0.55 | 0.56 | 1.67 | 1.12 | 1.01 | 1.21 | 1.09 | 1.11 | 9.97 | -12.73 | 0.99 | 3742.89 | 2991.61 | 960.84 | 1460.39 | 1.21 | 1.16 | CANDIDATE-RECENT |
| day.afterbigday1p5pct | d5 | MKT | KB | 0.66 | 0.02 | 1.74 | 0.96 | 0.87 | 1.01 | 0.91 | 1.62 | 17.10 | -2.53 | 0.97 | 3416.11 | 2989.10 | 563.84 | 1073.06 | 1.01 | 0.99 | CANDIDATE-RECENT |
| st.prev_rng_atrd>=1.301 | d5 | SPL | KB | 0.78 | 0.10 | 2.02 | 1.26 | 0.99 | 1.33 | 1.04 | 1.86 | 34.92 | 1.38 | 0.93 | 3305.99 | 2617.55 | 2538.82 | 1643.68 | 1.33 | 1.29 | CANDIDATE-RECENT |
| evt.sweep_low.within15.ict_with | skip | MKT | london | 0.48 | 0.13 | 0.04 | 0.02 | 0.01 | 0.16 | 0.14 | 0.78 | 2.78 | -0.58 | 0.91 | 2771.20 | 2424.80 | 1984.05 | -315.36 | 0.16 | 0.15 | CANDIDATE-RECENT |
| st.prev_er_rth>=0.2767 | rt50 | MKT | asia | 0.70 | 0.45 | 1.01 | 0.37 | 0.26 | 0.37 | 0.26 | 1.29 | 6.24 | -8.87 | 0.99 | 2754.73 | 888.77 | 130.31 | -1702.78 | 0.37 | 0.37 | CANDIDATE-RECENT |
| st.5m.rng_exp1>=2.275 | rt50 | MKT | asia | 0.10 | 0.27 | 0.41 | 0.22 | 0.28 | 0.22 | 0.28 | 0.52 | 2.35 | -3.27 | 0.97 | 2665.76 | 3189.64 | -81.62 | 885.39 | 0.22 | 0.22 | CANDIDATE-RECENT |
| st.5m.rng_exp1>=3.556 | d5 | SPL | KB | 0.42 | 0.45 | 1.28 | 0.96 | 0.88 | 1.03 | 0.93 | 1.14 | 11.93 | -3.06 | 0.94 | 2564.18 | 2315.43 | 1154.83 | 2297.19 | 1.03 | 1.00 | CANDIDATE-RECENT |
| st.prev_er_rth>=0.2767 | rt50 | SPL | asia | 0.69 | 0.39 | 0.94 | 0.33 | 0.22 | 0.34 | 0.23 | 1.21 | 6.24 | -8.11 | 0.99 | 2501.84 | 880.90 | 1370.77 | -2832.31 | 0.34 | 0.34 | CANDIDATE-RECENT |
| st.f60_vs_med>=1.809 | d15 | MKT | PE | 0.63 | 0.12 | 1.47 | 0.81 | 0.75 | 0.86 | 0.79 | 1.17 | 12.48 | -8.45 | 0.93 | 2450.43 | 2162.50 | 634.98 | 705.47 | 0.86 | 0.83 | CANDIDATE-RECENT |
| st.sig_es_nq_div5<=-0.3786 | d5 | MKT | WT | 0.19 | 0.62 | -0.12 | 0.39 | 0.32 | 0.52 | 0.40 | 0.77 | 21.04 | 1.35 | 0.93 | 2363.61 | 2041.66 | 331.45 | 2867.43 | 0.52 | 0.49 | CANDIDATE-RECENT |
| st.prev_rng_atrd>=1.697 | skip | MKT | asia | 0.66 | 0.49 | 1.11 | 0.15 | 0.13 | 0.74 | 0.48 | 1.81 | 11.76 | -1.28 | 0.93 | 2318.71 | 2028.87 | 1214.91 | 2272.82 | 0.74 | 0.65 | CANDIDATE-RECENT |
| st.1m.adx14<=18.87 | skip | MKT | SM | 0.85 | 0.56 | 1.18 | 1.23 | 0.58 | 1.52 | 0.94 | 2.57 | 7.32 | -16.86 | 0.98 | 2264.52 | 1236.92 | 1233.30 | 1066.18 | 1.52 | 1.41 | CANDIDATE-RECENT |
| st.sig_delta10_s<=-26 | d15 | MKT | PE | 0.60 | 0.43 | 1.76 | 1.20 | 1.11 | 1.28 | 1.19 | 1.03 | 9.97 | -13.18 | 0.99 | 2229.73 | 1738.14 | 1047.10 | 1961.24 | 1.28 | 1.23 | PASS_pre_RC |
| st.sig_delta10_s<=-26 | d5 | MKT | nyam | 0.33 | 0.42 | 1.46 | 1.07 | 1.03 | 1.25 | 1.20 | 0.86 | 19.04 | -0.16 | 1.00 | 2159.62 | 2077.11 | -1544.22 | 8157.35 | 1.25 | 1.19 | PASS_pre_RC |
| st.prev_rng_atrd>=1.697 | skip | MKT | KB | 0.80 | 0.16 | 1.36 | 0.96 | 0.88 | 1.36 | 1.14 | 1.45 | 13.05 | -7.39 | 0.99 | 2099.03 | 1836.65 | 1817.10 | 1151.15 | 1.36 | 1.18 | CANDIDATE-RECENT |
| st.1h.rng_exp1>=2.395 | d5 | SPL | nypm | 0.62 | 0.43 | 0.56 | 0.57 | 0.76 | 0.69 | 0.86 | 2.16 | 35.04 | 0.60 | 0.90 | 2050.41 | 1114.23 | -2210.42 | 1674.39 | 0.69 | 0.65 | CANDIDATE-RECENT |
| st.prev_rng_atrd>=1.697 | skip | SPL | KB | 0.79 | 0.15 | 1.31 | 0.93 | 0.85 | 1.28 | 1.07 | 1.44 | 13.05 | -7.11 | 0.98 | 1990.19 | 1741.42 | 2079.21 | 861.79 | 1.27 | 1.10 | CANDIDATE-RECENT |
| st.1h.squeeze==1 | d5 | SPL | PE | 0.23 | 0.82 | 0.65 | 0.75 | 0.64 | 0.77 | 0.66 | 0.83 | 13.99 | 2.90 | 0.96 | 1832.63 | 511.71 | -888.15 | 2091.49 | 0.77 | 0.76 | CANDIDATE-RECENT |
| st.1h.squeeze==1 | d5 | MKT | PE | 0.27 | 0.80 | 0.66 | 0.73 | 0.63 | 0.75 | 0.65 | 0.81 | 13.99 | 3.52 | 0.95 | 1726.63 | 245.56 | 242.94 | 2129.54 | 0.75 | 0.74 | CANDIDATE-RECENT |
| tm.lunch.1130_1330 | skip | SPL | SM | 0.79 | 1.46 | 0.07 | 1.21 | 1.08 | 1.55 | 1.49 | 2.99 | 7.32 | -16.48 | 0.99 | 1642.52 | 1496.19 | 1728.75 | 1738.62 | 1.56 | 1.45 | CANDIDATE-RECENT |
| tm.edge.close_london_end0830.last30 | d15 | MKT | KB | 0.16 | 0.07 | 0.41 | 0.17 | 0.18 | 0.18 | 0.18 | 0.61 | 1.59 | -12.85 | 0.93 | 1612.83 | 1490.81 | 110.81 | -105.93 | 0.18 | 0.18 | CANDIDATE-RECENT |
| evt.sweep_low.within15.ict_with | z25 | MKT | london | 0.36 | 0.09 | 0.03 | 0.01 | 0.01 | 0.12 | 0.10 | 0.59 | 2.78 | -0.58 | 0.91 | 1610.39 | 1409.09 | 815.69 | -244.99 | 0.12 | 0.11 | CANDIDATE-RECENT |

### 2c. the plain sentences for the top B cells

* Skip all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (SPL): keeps 84.4% of trades and adds +1.03 pts per contract in the last 6 months (per signal +0.36, MDE 0.93; 1522 signals touched, they earn -2.32 pts each under the base; HOLD +1.06); stack +30,118 / +26,652 $/wk (L6M / HOLD, research lots), PRE +8,880, X' +3,150; placebo rank 1.00; tier CANDIDATE-RECENT
* Skip all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (MKT): keeps 84.4% of trades and adds +0.97 pts per contract in the last 6 months (per signal +0.31, MDE 0.95; 1522 signals touched, they earn -2.02 pts each under the base; HOLD +1.02); stack +29,834 / +25,284 $/wk (L6M / HOLD, research lots), PRE +11,299, X' +5,714; placebo rank 1.00; tier CANDIDATE-RECENT
* Size 25% all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (SPL): changes 15.6% of trades and adds +0.74 pts per contract in the last 6 months (per signal +0.27, MDE 0.70; 1522 signals touched, they earn -2.32 pts each under the base; HOLD +0.76); stack +23,422 / +20,328 $/wk (L6M / HOLD, research lots), PRE +2,350, X' +1,624; placebo rank 1.00; tier CANDIDATE-RECENT
* Size 25% all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (MKT): changes 15.6% of trades and adds +0.70 pts per contract in the last 6 months (per signal +0.24, MDE 0.71; 1522 signals touched, they earn -2.02 pts each under the base; HOLD +0.73); stack +21,305 / +17,069 $/wk (L6M / HOLD, research lots), PRE +6,320, X' +2,160; placebo rank 1.00; tier CANDIDATE-RECENT
* Size 50% all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (SPL): changes 15.6% of trades and adds +0.47 pts per contract in the last 6 months (per signal +0.18, MDE 0.47; 1522 signals touched, they earn -2.32 pts each under the base; HOLD +0.48); stack +16,936 / +14,450 $/wk (L6M / HOLD, research lots), PRE +1,204, X' +2,460; placebo rank 1.00; tier CANDIDATE-RECENT
* Size 50% all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (MKT): changes 15.6% of trades and adds +0.45 pts per contract in the last 6 months (per signal +0.16, MDE 0.48; 1522 signals touched, they earn -2.02 pts each under the base; HOLD +0.46); stack +15,803 / +12,669 $/wk (L6M / HOLD, research lots), PRE +1,347, X' +1,662; placebo rank 1.00; tier CANDIDATE-RECENT
* Delay 15 min all signals when [TG-1 store measure f60_vs_med >=1.809] (SPL): changes 11.7% of trades and adds +0.37 pts per contract in the last 6 months (per signal +0.23, MDE 0.70; 1138 signals touched, they earn -3.05 pts each under the base; HOLD +0.32); stack +10,697 / +9,524 $/wk (L6M / HOLD, research lots), PRE +54, X' +7; placebo rank 0.99; tier CANDIDATE-RECENT
* Delay 15 min all signals when [TG-1 store measure f60_vs_med >=1.809] (MKT): changes 11.7% of trades and adds +0.32 pts per contract in the last 6 months (per signal +0.19, MDE 0.71; 1138 signals touched, they earn -2.92 pts each under the base; HOLD +0.27); stack +10,518 / +9,100 $/wk (L6M / HOLD, research lots), PRE +2,578, X' -359; placebo rank 0.99; tier CANDIDATE-RECENT
* Re-target (target x0.5) all signals when [the book's previous signal was the OPPOSITE side and fired <= 60 min ago (whipsaw / flip)] (SPL): changes 9.0% of trades and adds +0.09 pts per contract in the last 6 months (per signal +0.08, MDE 0.34; 881 signals touched, they earn -0.24 pts each under the base; HOLD +0.05); stack +7,979 / +6,973 $/wk (L6M / HOLD, research lots), PRE -4,043, X' -2,418; placebo rank 0.98; tier CANDIDATE-RECENT
* Delay 5 min all signals when [TG-1 store measure sig_vel30 (already sided) <=-3.6] (MKT): changes 11.2% of trades and adds +0.22 pts per contract in the last 6 months (per signal +0.17, MDE 0.32; 1087 signals touched, they earn +2.32 pts each under the base; HOLD +0.21); stack +7,815 / +6,307 $/wk (L6M / HOLD, research lots), PRE -7,322, X' +3,170; placebo rank 0.97; tier CANDIDATE-RECENT
* Delay 15 min HM signals when [t_since_big_against (L2EA) <= 300] (MKT): changes 18.9% of trades and adds +0.80 pts per contract in the last 6 months (per signal +0.36, MDE 1.80; 172 signals touched, they earn +1.03 pts each under the base; HOLD +0.71); stack +7,737 / +7,285 $/wk (L6M / HOLD, research lots), PRE +4,096, X' +459; placebo rank 0.97; tier CANDIDATE-RECENT
* Delay 5 min all signals when [ES move over the prior 15 s in bp, sided (<0 = ES moved the OPPOSITE way) <= -1] (SPL): changes 9.7% of trades and adds +0.19 pts per contract in the last 6 months (per signal +0.14, MDE 0.32; 947 signals touched, they earn -0.98 pts each under the base; HOLD +0.19); stack +7,480 / +6,751 $/wk (L6M / HOLD, research lots), PRE -8,878, X' +724; placebo rank 0.94; tier CANDIDATE-RECENT
* Delay 15 min HM signals when [t_since_big_against (L2EA) <= 300] (SPL): changes 18.9% of trades and adds +0.69 pts per contract in the last 6 months (per signal +0.28, MDE 1.61; 172 signals touched, they earn +1.86 pts each under the base; HOLD +0.50); stack +7,269 / +6,156 $/wk (L6M / HOLD, research lots), PRE +3,089, X' -917; placebo rank 0.96; tier CANDIDATE-RECENT
* Re-target (target x0.5) all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (SPL): changes 15.6% of trades and adds +0.22 pts per contract in the last 6 months (per signal +0.21, MDE 0.75; 1522 signals touched, they earn -2.32 pts each under the base; HOLD +0.19); stack +6,995 / +5,980 $/wk (L6M / HOLD, research lots), PRE -587, X' -5,765; placebo rank 1.00; tier CANDIDATE-RECENT

## 3. The directive's TIME / calendar states, NAMED (not selected): skip, per scope, last 6 months first. 'n' = signals in the state; MDE = 2.8 SE of the gain per signal

### ALL
| state | n_in_L6M | keep_pct | gain_L6M | pc_L6M | MDE | gain_HOLD | gain_L3M | gain_PRE | gain_X | skipped_pts | plc | usd_live_wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.rel.CORE830.pre10 | 6 | 99.94 | -0.01 | -0.01 | 0.02 | -0.01 | -0.00 | 0.01 | 0.00 | 21.92 | 0.24 | -125.92 |
| tm.rel.R830.pre10 | 23 | 99.76 | -0.04 | -0.03 | 0.10 | -0.03 | 0.00 | 0.04 | -0.02 | 14.90 | 0.15 | -152.60 |
| tm.rel.R830.pre30 | 57 | 99.41 | -0.05 | -0.03 | 0.18 | -0.04 | -0.01 | 0.06 | -0.04 | 8.82 | 0.31 | -603.98 |
| tm.rel.R830.post5 | 56 | 99.43 | -0.03 | -0.01 | 0.19 | -0.03 | -0.04 | -0.07 | -0.17 | 4.95 | 0.18 | -42.68 |
| tm.rel.R1000.pre10 | 42 | 99.57 | -0.00 | 0.01 | 0.15 | -0.02 | -0.08 | -0.01 | 0.00 | 0.62 | 0.56 | 694.69 |
| tm.rel.R1000.pre30 | 161 | 98.35 | 0.05 | 0.11 | 0.39 | -0.00 | -0.17 | 0.01 | -0.04 | -3.02 | 0.90 | 1442.73 |
| tm.rel.FOMC.pre30 | 5 | 99.95 | 0.02 | 0.02 | 0.03 | 0.02 | 0.03 | 0.02 | 0.01 | -34.05 | 0.89 | 43.75 |
| tm.day.FOMC_whole | 334 | 96.57 | 0.02 | 0.13 | 0.43 | -0.02 | 0.07 | -0.12 | 0.09 | -0.44 | 0.90 | -851.54 |
| tm.day.FOMC_before14 | 161 | 98.35 | 0.12 | 0.18 | 0.24 | 0.15 | 0.09 | -0.00 | 0.03 | -7.26 | 0.99 | 840.88 |
| tm.day.CPINFP_morning | 516 | 94.70 | -0.09 | 0.09 | 0.58 | -0.14 | -0.07 | -0.20 | 0.32 | 1.66 | 0.49 | 249.14 |
| tm.block.0900_1000 | 1101 | 88.70 | 0.02 | 0.44 | 1.16 | 0.03 | -0.28 | -0.24 | 0.24 | -0.21 | 0.95 | 5220.52 |
| tm.lunch.1130_1330 | 1320 | 86.45 | -0.48 | -0.05 | 1.00 | -0.29 | 0.00 | -0.12 | 0.11 | 3.55 | 0.10 | 959.05 |
| tm.edge.open_rth0930.first10 | 347 | 96.44 | 0.05 | 0.17 | 0.49 | 0.10 | 0.06 | -0.13 | 0.15 | -1.46 | 0.88 | -577.30 |
| tm.edge.open_asia18.first10 | 375 | 96.15 | 0.14 | 0.27 | 0.44 | 0.25 | 0.37 | -0.22 | 0.33 | -3.56 | 0.99 | 3342.33 |
| tm.edge.open_london02.first10 | 52 | 99.47 | 0.03 | 0.04 | 0.17 | 0.01 | 0.09 | -0.03 | -0.02 | -4.90 | 0.89 | -487.67 |
| tm.edge.close_nypm_end1500.last30 | 291 | 97.01 | -0.08 | 0.02 | 0.37 | -0.08 | 0.10 | 0.13 | 0.06 | 2.59 | 0.23 | -698.04 |
| tm.edge.close_nyam_end1200.last30 | 427 | 95.62 | -0.15 | -0.01 | 0.58 | -0.08 | 0.09 | -0.08 | 0.07 | 3.43 | 0.36 | 1888.06 |
| cal.fri_after12 | 362 | 96.28 | 0.00 | 0.13 | 0.44 | 0.04 | 0.02 | 0.09 | 0.16 | -0.11 | 0.69 | -205.15 |
| cal.before_holiday | 42 | 99.57 | -0.04 | -0.03 | 0.16 | -0.04 | -0.08 | 0.05 | 0.09 | 10.26 | 0.20 | -984.95 |
| cal.after_holiday | 121 | 98.76 | 0.06 | 0.10 | 0.18 | 0.05 | 0.11 | -0.01 | 0.03 | -4.90 | 0.97 | 1002.58 |
| cal.month_last2 | 1026 | 89.47 | -0.42 | -0.08 | 0.71 | -0.55 | -0.53 | -0.30 | 0.32 | 3.96 | 0.40 | 144.43 |
| cal.opex_day | 548 | 94.37 | 0.29 | 0.50 | 0.88 | 0.31 | 0.46 | -0.30 | -0.14 | -5.08 | 1.00 | 4004.28 |
| cal.quad_witch | 114 | 98.83 | 0.02 | 0.06 | 0.13 | 0.02 | -0.03 | -0.05 | -0.08 | -1.98 | 0.82 | 1622.22 |

### KB
| state | n_in_L6M | keep_pct | gain_L6M | pc_L6M | MDE | gain_HOLD | gain_L3M | gain_PRE | gain_X | skipped_pts | plc | usd_live_wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.rel.CORE830.pre10 | 2.00 | 99.84 | 0.00 | 0.00 | 0.19 | 0.00 | 0.08 | 0.02 | 0.06 | -0.75 | 0.57 | 2.13 |
| tm.rel.R830.pre10 | 3.00 | 99.76 | 0.05 | 0.05 | 0.23 | 0.05 | 0.17 | 0.02 | 0.06 | -20.92 | 0.78 | 89.64 |
| tm.rel.R830.pre30 | 4.00 | 99.68 | 0.00 | 0.01 | 0.27 | 0.00 | 0.17 | 0.04 | 0.06 | -0.75 | 0.63 | 4.27 |
| tm.rel.R830.post5 | 9 | 99.28 | 0.15 | 0.16 | 0.34 | 0.14 | 0.17 | -0.09 | -0.05 | -20.92 | 0.77 | 0.00 |
| tm.rel.R1000.pre10 | 8 | 99.36 | 0.20 | 0.21 | 0.42 | 0.14 | 0.17 | -0.06 | -0.06 | -31.00 | 0.90 | 354.28 |
| tm.rel.R1000.pre30 | 28 | 97.77 | 0.21 | 0.25 | 0.69 | 0.10 | -0.07 | 0.03 | 0.07 | -9.39 | 0.71 | 375.62 |
| tm.rel.FOMC.pre30 | 0.00 | 100 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.02 | 0.00 | 0.00 | 0.50 | 0.00 |
| tm.day.FOMC_whole | 40 | 96.82 | -0.27 | -0.22 | 0.93 | -0.42 | -0.31 | -0.04 | -0.39 | 8.33 | 0.23 | -390.56 |
| tm.day.FOMC_before14 | 16 | 98.73 | -0.18 | -0.16 | 0.24 | -0.21 | -0.16 | 0.01 | -0.05 | 14.38 | 0.20 | -243.30 |
| tm.day.CPINFP_morning | 66 | 94.75 | 0.01 | 0.10 | 0.87 | 0.06 | 0.21 | -0.61 | 0.17 | -0.18 | 0.49 | -431.00 |
| tm.block.0900_1000 | 134 | 89.34 | 1.04 | 1.36 | 1.35 | 1.00 | 0.92 | -0.57 | -0.05 | -9.78 | 0.95 | 2014.70 |
| tm.lunch.1130_1330 | 199 | 84.17 | -0.43 | -0.20 | 1.60 | -0.22 | 0.07 | -0.31 | -0.09 | 2.72 | 0.35 | -772.68 |
| tm.edge.open_rth0930.first10 | 54 | 95.70 | 0.22 | 0.31 | 0.78 | 0.30 | 0.37 | -0.52 | 0.25 | -5.23 | 0.68 | 403.37 |
| tm.edge.open_asia18.first10 | 90 | 92.84 | 0.51 | 0.67 | 1.26 | 0.65 | 0.75 | -0.42 | 1.36 | -7.09 | 0.93 | 911.45 |
| tm.edge.open_london02.first10 | 7 | 99.44 | 0.05 | 0.06 | 0.35 | 0.05 | 0.00 | -0.06 | -0.11 | -9.39 | 0.80 | 93.91 |
| tm.edge.close_nypm_end1500.last30 | 36 | 97.14 | -0.32 | -0.29 | 0.54 | -0.29 | -0.19 | 0.23 | 0.38 | 11.35 | 0.12 | -615.27 |
| tm.edge.close_nyam_end1200.last30 | 64 | 94.91 | -0.07 | 0.01 | 1.18 | -0.08 | 0.80 | -0.19 | -0.19 | 1.46 | 0.30 | -133.59 |
| cal.fri_after12 | 54 | 95.70 | -0.14 | -0.08 | 0.70 | -0.10 | -0.30 | -0.21 | -0.09 | 3.34 | 0.49 | -172.15 |
| cal.before_holiday | 5 | 99.60 | -0.08 | -0.08 | 0.26 | -0.08 | -0.15 | 0.17 | 0.22 | 21.16 | 0.28 | -151.12 |
| cal.after_holiday | 15 | 98.81 | 0.21 | 0.23 | 0.46 | 0.19 | 0.36 | -0.03 | 0.04 | -17.66 | 0.94 | 291.02 |
| cal.month_last2 | 141 | 88.78 | 0.20 | 0.43 | 1.17 | -0.12 | -0.49 | -0.15 | 0.69 | -1.75 | 0.76 | 519.41 |
| cal.opex_day | 72 | 94.27 | 0.38 | 0.51 | 1.55 | 0.42 | 0.60 | -0.60 | 0.01 | -6.66 | 0.94 | 770.42 |
| cal.quad_witch | 16 | 98.73 | 0.12 | 0.14 | 0.59 | 0.11 | -0.13 | -0.23 | 0.26 | -9.48 | 0.80 | 302.09 |

### PE
| state | n_in_L6M | keep_pct | gain_L6M | pc_L6M | MDE | gain_HOLD | gain_L3M | gain_PRE | gain_X | skipped_pts | plc | usd_live_wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.rel.CORE830.pre10 | 0.00 | 100 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.06 | 0.00 | 0.00 | 0.50 | 0.00 |
| tm.rel.R830.pre10 | 3.00 | 99.75 | -0.05 | -0.05 | 0.25 | -0.04 | 0.00 | 0.10 | -0.06 | 19.42 | 0.34 | -291.32 |
| tm.rel.R830.pre30 | 7 | 99.41 | -0.05 | -0.04 | 0.37 | -0.04 | 0.00 | 0.20 | 0.00 | 7.90 | 0.38 | -276.38 |
| tm.rel.R830.post5 | 5 | 99.58 | 0.16 | 0.16 | 0.24 | 0.10 | 0.17 | 0.01 | -0.35 | -37.05 | 0.85 | 0.00 |
| tm.rel.R1000.pre10 | 7 | 99.41 | 0.06 | 0.06 | 0.32 | 0.05 | 0.00 | 0.02 | -0.06 | -9.39 | 0.66 | 328.67 |
| tm.rel.R1000.pre30 | 19 | 98.41 | 0.16 | 0.18 | 0.52 | 0.10 | -0.07 | -0.03 | -0.30 | -10.30 | 0.75 | 978.54 |
| tm.rel.FOMC.pre30 | 1.00 | 99.92 | -0.05 | -0.05 | 0.14 | 0.00 | -0.08 | 0.06 | 0.00 | 59.76 | 0.23 | 0.00 |
| tm.day.FOMC_whole | 43 | 96.40 | 0.18 | 0.21 | 0.56 | 0.17 | 0.45 | 0.14 | 0.20 | -4.97 | 0.80 | 104.58 |
| tm.day.FOMC_before14 | 17 | 98.58 | 0.16 | 0.17 | 0.32 | 0.24 | 0.18 | 0.21 | -0.11 | -11.42 | 0.81 | 351.08 |
| tm.day.CPINFP_morning | 64 | 94.64 | 0.06 | 0.10 | 0.76 | -0.08 | 0.30 | -0.32 | -0.08 | -1.07 | 0.42 | 589.19 |
| tm.block.0900_1000 | 134 | 88.78 | 0.35 | 0.47 | 1.51 | 0.32 | 0.69 | -0.45 | -0.60 | -3.10 | 0.58 | 2552.38 |
| tm.lunch.1130_1330 | 184 | 84.59 | 0.30 | 0.48 | 1.79 | 0.28 | 0.30 | -0.07 | -0.28 | -1.96 | 0.51 | 2789.03 |
| tm.edge.open_rth0930.first10 | 37 | 96.90 | -0.13 | -0.11 | 0.68 | -0.02 | -0.23 | -0.18 | -0.29 | 4.16 | 0.20 | -769.38 |
| tm.edge.open_asia18.first10 | 51 | 95.73 | 0.29 | 0.33 | 0.95 | 0.26 | 0.71 | -0.20 | 0.28 | -6.68 | 0.91 | 1703.11 |
| tm.edge.open_london02.first10 | 3.00 | 99.75 | -0.05 | -0.05 | 0.31 | -0.04 | 0.09 | -0.10 | 0.06 | 19.42 | 0.34 | -291.32 |
| tm.edge.close_nypm_end1500.last30 | 42 | 96.48 | 0.21 | 0.25 | 0.56 | 0.15 | 0.55 | 0.16 | -0.23 | -6.08 | 0.65 | 0.00 |
| tm.edge.close_nyam_end1200.last30 | 62 | 94.81 | 0.52 | 0.58 | 1.13 | 0.36 | 0.55 | -0.23 | 0.04 | -9.98 | 0.83 | 2789.03 |
| cal.fri_after12 | 47 | 96.06 | 0.29 | 0.33 | 0.72 | 0.31 | 0.21 | 0.39 | 0.52 | -7.28 | 0.79 | 0.00 |
| cal.before_holiday | 5 | 99.58 | -0.08 | -0.08 | 0.28 | -0.08 | -0.14 | 0.11 | 0.09 | 20.21 | 0.24 | -505.18 |
| cal.after_holiday | 15 | 98.74 | 0.12 | 0.13 | 0.24 | 0.11 | 0.20 | -0.08 | 0.02 | -9.60 | 0.73 | 37.35 |
| cal.month_last2 | 126 | 89.45 | 0.25 | 0.36 | 1.86 | 0.19 | 0.52 | -0.14 | 0.56 | -2.38 | 0.73 | 2059.82 |
| cal.opex_day | 70 | 94.14 | 0.50 | 0.58 | 1.56 | 0.47 | 0.96 | -0.57 | -0.40 | -8.60 | 0.87 | 3281.85 |
| cal.quad_witch | 15 | 98.74 | 0.07 | 0.08 | 0.17 | 0.06 | 0.11 | -0.22 | -0.40 | -5.31 | 0.62 | 996.10 |

### HM
| state | n_in_L6M | keep_pct | gain_L6M | pc_L6M | MDE | gain_HOLD | gain_L3M | gain_PRE | gain_X | skipped_pts | plc | usd_live_wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.rel.R830.pre10 | 2.00 | 99.78 | -0.13 | -0.12 | 0.25 | -0.12 | -0.12 | 0.05 | -0.14 | 59.76 | 0.08 | 0.00 |
| tm.rel.R830.pre30 | 7 | 99.23 | -0.19 | -0.16 | 0.40 | -0.11 | -0.36 | -0.02 | -0.35 | 25.18 | 0.15 | 0.00 |
| tm.rel.R830.post5 | 8 | 99.12 | 0.01 | 0.05 | 0.59 | -0.05 | -0.12 | -0.05 | 0.08 | -0.75 | 0.62 | 0.00 |
| tm.rel.R1000.pre10 | 5 | 99.45 | 0.07 | 0.10 | 0.50 | 0.00 | -0.24 | -0.08 | 0.07 | -12.85 | 0.72 | 91.77 |
| tm.rel.R1000.pre30 | 16 | 98.24 | -0.12 | -0.04 | 0.69 | -0.17 | -0.47 | -0.16 | 0.15 | 6.82 | 0.53 | -155.80 |
| tm.rel.FOMC.pre30 | 1.00 | 99.89 | 0.07 | 0.07 | 0.19 | 0.06 | 0.12 | -0.03 | 0.00 | -61.25 | 0.82 | 0.00 |
| tm.day.FOMC_whole | 38 | 95.82 | -0.10 | 0.10 | 0.44 | -0.15 | 0.15 | -0.08 | 0.23 | 2.44 | 0.57 | -911.31 |
| tm.day.FOMC_before14 | 16 | 98.24 | 0.28 | 0.37 | 0.59 | 0.31 | 0.50 | -0.04 | 0.29 | -15.87 | 0.93 | 96.04 |
| tm.day.CPINFP_morning | 41 | 95.49 | 0.10 | 0.33 | 1.30 | 0.18 | -0.21 | -0.04 | -0.20 | -2.22 | 0.81 | -68.29 |
| tm.block.0900_1000 | 88 | 90.32 | -0.79 | -0.36 | 2.08 | -0.65 | -1.12 | -0.61 | -0.21 | 8.14 | 0.55 | -698.58 |
| tm.lunch.1130_1330 | 126 | 86.14 | -0.93 | -0.32 | 2.20 | -0.36 | 0.26 | 0.09 | 0.60 | 6.72 | 0.18 | -545.94 |
| tm.edge.open_rth0930.first10 | 37 | 95.93 | -0.70 | -0.53 | 1.05 | -0.69 | -1.16 | -0.43 | 0.02 | 17.24 | 0.14 | -911.31 |
| tm.edge.open_asia18.first10 | 31 | 96.59 | 0.23 | 0.40 | 1.03 | 0.39 | 0.26 | -0.51 | 0.54 | -6.60 | 0.89 | 584.78 |
| tm.edge.open_london02.first10 | 10 | 98.90 | 0.14 | 0.20 | 0.58 | 0.13 | 0.13 | 0.01 | -0.07 | -12.85 | 0.72 | 0.00 |
| tm.edge.close_nypm_end1500.last30 | 31 | 96.59 | 0.10 | 0.28 | 0.82 | 0.09 | 0.15 | -0.06 | -0.47 | -3.07 | 0.65 | 0.00 |
| tm.edge.close_nyam_end1200.last30 | 39 | 95.71 | -0.49 | -0.30 | 1.36 | -0.19 | -0.09 | 0.13 | 0.32 | 11.33 | 0.34 | -545.94 |
| cal.fri_after12 | 39 | 95.71 | 0.14 | 0.35 | 1.14 | 0.12 | 0.56 | 0.18 | -0.00 | -3.17 | 0.60 | 0.00 |
| cal.before_holiday | 5 | 99.45 | 0.02 | 0.05 | 0.05 | 0.02 | 0.04 | 0.09 | 0.13 | -3.64 | 0.58 | -83.23 |
| cal.after_holiday | 10 | 98.90 | 0.18 | 0.24 | 0.49 | 0.16 | 0.33 | -0.10 | -0.09 | -16.40 | 0.88 | 700.02 |
| cal.month_last2 | 94 | 89.66 | -0.75 | -0.29 | 1.78 | -0.85 | -1.06 | -0.10 | 0.87 | 7.23 | 0.32 | -1037.61 |
| cal.opex_day | 54 | 94.06 | 0.51 | 0.85 | 1.22 | 0.46 | 0.58 | -0.24 | 0.35 | -8.64 | 0.96 | 729.90 |
| cal.quad_witch | 10 | 98.90 | 0.06 | 0.11 | 0.16 | 0.06 | 0.11 | 0.14 | 0.29 | -5.60 | 0.64 | 181.41 |

### SM
| state | n_in_L6M | keep_pct | gain_L6M | pc_L6M | MDE | gain_HOLD | gain_L3M | gain_PRE | gain_X | skipped_pts | plc | usd_live_wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.rel.CORE830.pre10 | 0.00 | 100 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.14 | 0.00 | 0.50 | 0.00 |
| tm.rel.R830.pre10 | 0.00 | 100 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.14 | 0.14 | 0.00 | 0.50 | 0.00 |
| tm.rel.R830.pre30 | 2.00 | 99.36 | -0.38 | -0.37 | 0.70 | -0.33 | -0.36 | 0.07 | 0.00 | 59.76 | 0.17 | -341.47 |
| tm.rel.R1000.pre10 | 0.00 | 100 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | -0.06 | 0.01 | 0.00 | 0.50 | 0.00 |
| tm.rel.R1000.pre30 | 3.00 | 99.04 | 0.20 | 0.22 | 0.93 | 0.17 | -0.36 | 0.21 | -0.40 | -20.92 | 0.82 | 0.00 |
| tm.rel.FOMC.pre30 | 0.00 | 100 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.07 | 0.00 | 0.00 | 0.50 | 0.00 |
| tm.day.FOMC_whole | 12 | 96.18 | 0.41 | 0.52 | 0.77 | 0.53 | 0.40 | 0.21 | 0.85 | -10.83 | 0.67 | 187.81 |
| tm.day.FOMC_before14 | 8 | 97.45 | 0.40 | 0.48 | 1.33 | 0.35 | 0.02 | 0.28 | 0.43 | -15.87 | 0.76 | 354.28 |
| tm.day.CPINFP_morning | 22 | 92.99 | 0.44 | 0.65 | 2.30 | 0.05 | -1.03 | -0.35 | 0.12 | -6.25 | 0.73 | -153.66 |
| tm.block.0900_1000 | 41 | 86.94 | -1.64 | -1.53 | 2.86 | -2.07 | -2.80 | -0.02 | -0.64 | 12.53 | 0.07 | 0.00 |
| tm.lunch.1130_1330 | 23 | 92.68 | 1.18 | 1.46 | 3.00 | 1.06 | -0.00 | 0.82 | 1.50 | -16.08 | 0.99 | 0.00 |
| tm.edge.open_rth0930.first10 | 4.00 | 98.73 | 0.39 | 0.43 | 1.07 | 0.34 | 0.01 | 0.07 | 0.00 | -31.00 | 0.90 | 0.00 |
| tm.edge.open_london02.first10 | 1.00 | 99.68 | 0.20 | 0.20 | 0.53 | 0.17 | 0.37 | 0.21 | 0.28 | -61.25 | 0.85 | 175.01 |
| tm.edge.close_nypm_end1500.last30 | 10 | 96.82 | 0.18 | 0.26 | 1.41 | 0.36 | 0.40 | 0.08 | 0.30 | -5.69 | 0.33 | 0.00 |
| tm.edge.close_nyam_end1200.last30 | 12 | 96.18 | 1.18 | 1.33 | 1.90 | 1.02 | 0.76 | 0.62 | 0.28 | -31.00 | 1.00 | 0.00 |
| cal.fri_after12 | 4.00 | 98.73 | 0.39 | 0.43 | 1.06 | 0.34 | 0.75 | -0.40 | 0.31 | -31.00 | 0.87 | 0.00 |
| cal.before_holiday | 2.00 | 99.36 | -0.38 | -0.37 | 1.05 | -0.33 | -0.72 | 0.25 | 0.06 | 59.76 | 0.14 | -170.74 |
| cal.after_holiday | 4.00 | 98.73 | 0.23 | 0.27 | 1.17 | 0.20 | 0.44 | 0.21 | 0.06 | -18.37 | 0.70 | 4.27 |
| cal.month_last2 | 30 | 90.45 | -0.90 | -0.75 | 2.30 | -0.94 | -1.04 | -0.36 | 0.40 | 9.45 | 0.20 | -660.96 |
| cal.opex_day | 11 | 96.50 | -0.17 | -0.09 | 1.96 | -0.47 | 0.76 | 0.30 | 0.25 | 4.75 | 0.48 | -328.67 |
| cal.quad_witch | 4.00 | 98.73 | -0.38 | -0.35 | 0.73 | -0.33 | -0.35 | 0.15 | 0.15 | 29.51 | 0.17 | -166.47 |

### ST
| state | n_in_L6M | keep_pct | gain_L6M | pc_L6M | MDE | gain_HOLD | gain_L3M | gain_PRE | gain_X | skipped_pts | plc | usd_live_wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| tm.rel.CORE830.pre10 | 0.00 | 100 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | -0.06 | 0.00 | 0.50 | 0.00 |
| tm.rel.R830.pre10 | 2.00 | 99.84 | -0.10 | -0.09 | 0.18 | -0.09 | -0.08 | 0.04 | -0.06 | 59.76 | 0.12 | 0.00 |
| tm.rel.R830.pre30 | 8 | 99.36 | 0.00 | 0.03 | 0.33 | 0.00 | 0.00 | 0.13 | -0.12 | -0.75 | 0.69 | 0.00 |
| tm.rel.R830.post5 | 6 | 99.52 | -0.09 | -0.07 | 0.37 | -0.04 | -0.08 | -0.25 | -0.36 | 19.42 | 0.17 | 0.00 |
| tm.rel.R1000.pre10 | 7 | 99.44 | -0.14 | -0.12 | 0.39 | -0.17 | -0.33 | -0.01 | -0.18 | 25.18 | 0.16 | 0.00 |
| tm.rel.R1000.pre30 | 20 | 98.41 | -0.08 | -0.02 | 0.68 | -0.16 | -0.24 | -0.15 | -0.11 | 5.30 | 0.50 | 0.00 |
| tm.rel.FOMC.pre30 | 1.00 | 99.92 | 0.05 | 0.05 | 0.13 | 0.04 | 0.09 | 0.02 | 0.06 | -61.25 | 0.80 | 0.00 |
| tm.day.FOMC_whole | 44 | 96.50 | 0.12 | 0.27 | 0.98 | 0.16 | 0.02 | -0.20 | 0.45 | -3.50 | 0.79 | 0.00 |
| tm.day.FOMC_before14 | 19 | 98.49 | 0.25 | 0.32 | 0.55 | 0.32 | 0.10 | -0.05 | 0.19 | -16.67 | 0.94 | 0.00 |
| tm.day.CPINFP_morning | 78 | 93.79 | -0.58 | -0.37 | 1.33 | -0.66 | -0.29 | 0.05 | 0.81 | 9.42 | 0.10 | 0.00 |
| tm.block.0900_1000 | 173 | 86.23 | -0.37 | 0.19 | 2.02 | -0.32 | -0.73 | -0.07 | 0.36 | 2.72 | 0.60 | 0.00 |
| tm.lunch.1130_1330 | 162 | 87.10 | -0.77 | -0.31 | 1.41 | -0.63 | -0.25 | -0.04 | -0.28 | 5.98 | 0.15 | 0.00 |
| tm.edge.open_rth0930.first10 | 49 | 96.10 | 0.08 | 0.24 | 1.24 | 0.12 | 0.21 | 0.02 | 0.36 | -1.98 | 0.77 | 0.00 |
| tm.edge.open_asia18.first10 | 61 | 95.14 | 0.25 | 0.47 | 0.95 | 0.59 | 0.49 | -0.29 | -0.22 | -5.22 | 0.84 | 0.00 |
| tm.edge.open_london02.first10 | 4.00 | 99.68 | 0.20 | 0.21 | 0.25 | 0.13 | 0.17 | -0.08 | 0.06 | -61.25 | 0.99 | 0.00 |
| tm.edge.close_nypm_end1500.last30 | 38 | 96.97 | -0.22 | -0.11 | 0.79 | -0.27 | -0.00 | 0.08 | 0.38 | 7.43 | 0.26 | 0.00 |
| tm.edge.close_nyam_end1200.last30 | 53 | 95.78 | -0.71 | -0.56 | 0.61 | -0.66 | -0.60 | -0.07 | 0.29 | 16.71 | 0.10 | 0.00 |
| cal.fri_after12 | 42 | 96.66 | -0.19 | -0.06 | 0.79 | -0.10 | -0.14 | 0.10 | -0.02 | 5.68 | 0.30 | 0.00 |
| cal.before_holiday | 3.00 | 99.76 | -0.09 | -0.08 | 0.27 | -0.08 | -0.15 | -0.05 | 0.05 | 35.68 | 0.16 | 0.00 |
| cal.after_holiday | 14 | 98.89 | 0.04 | 0.08 | 0.15 | 0.04 | 0.07 | -0.05 | -0.04 | -3.64 | 0.66 | 0.00 |
| cal.month_last2 | 136 | 89.17 | -0.88 | -0.51 | 0.86 | -0.88 | -0.76 | -0.60 | 0.19 | 8.11 | 0.19 | 0.00 |
| cal.opex_day | 76 | 93.95 | 0.16 | 0.42 | 0.73 | 0.21 | 0.31 | -0.33 | -0.24 | -2.60 | 0.87 | 0.00 |
| cal.quad_witch | 16 | 98.73 | -0.06 | -0.01 | 0.13 | -0.05 | -0.02 | -0.08 | -0.16 | 4.43 | 0.48 | 0.00 |

Plain sentences (skip, market base; last 6 months):

* Skip KB signals when [signal within 10 min BEFORE CPI/NFP 08:30 (verified)] (MKT): keeps 99.8% of trades and adds +0.00 pts per contract in the last 6 months (per signal +0.00, MDE 0.19; 2 signals touched, they earn -0.75 pts each under the base; HOLD +0.00)
* Skip KB signals when [signal within 10 min BEFORE all 08:30 (CPI/NFP verified + claims/PCE rules)] (MKT): keeps 99.8% of trades and adds +0.05 pts per contract in the last 6 months (per signal +0.05, MDE 0.23; 3 signals touched, they earn -20.92 pts each under the base; HOLD +0.05)
* Skip KB signals when [signal within 30 min BEFORE all 08:30 (CPI/NFP verified + claims/PCE rules)] (MKT): keeps 99.7% of trades and adds +0.01 pts per contract in the last 6 months (per signal +0.00, MDE 0.27; 4 signals touched, they earn -0.75 pts each under the base; HOLD +0.01)
* Skip KB signals when [signal within 10 min BEFORE 10:00 data (rules-based, approx)] (MKT): keeps 99.4% of trades and adds +0.21 pts per contract in the last 6 months (per signal +0.20, MDE 0.42; 8 signals touched, they earn -31.00 pts each under the base; HOLD +0.14)
* Skip KB signals when [FOMC day, whole day (ET date)] (MKT): keeps 96.8% of trades and adds -0.22 pts per contract in the last 6 months (per signal -0.27, MDE 0.93; 40 signals touched, they earn +8.33 pts each under the base; HOLD -0.40)
* Skip KB signals when [lunch window 11:30-13:30] (MKT): keeps 84.2% of trades and adds -0.20 pts per contract in the last 6 months (per signal -0.43, MDE 1.60; 199 signals touched, they earn +2.72 pts each under the base; HOLD -0.07)
* Skip KB signals when [the live 09:00-10:00 block window] (MKT): keeps 89.3% of trades and adds +1.36 pts per contract in the last 6 months (per signal +1.04, MDE 1.35; 134 signals touched, they earn -9.78 pts each under the base; HOLD +1.25)
* Skip all signals when [signal within 10 min BEFORE CPI/NFP 08:30 (verified)] (MKT): keeps 99.9% of trades and adds -0.01 pts per contract in the last 6 months (per signal -0.01, MDE 0.02; 6 signals touched, they earn +21.92 pts each under the base; HOLD -0.01)
* Skip all signals when [signal within 10 min BEFORE all 08:30 (CPI/NFP verified + claims/PCE rules)] (MKT): keeps 99.8% of trades and adds -0.03 pts per contract in the last 6 months (per signal -0.04, MDE 0.10; 23 signals touched, they earn +14.90 pts each under the base; HOLD -0.03)
* Skip all signals when [signal within 30 min BEFORE all 08:30 (CPI/NFP verified + claims/PCE rules)] (MKT): keeps 99.4% of trades and adds -0.03 pts per contract in the last 6 months (per signal -0.05, MDE 0.18; 57 signals touched, they earn +8.82 pts each under the base; HOLD -0.03)
* Skip all signals when [signal within 10 min BEFORE 10:00 data (rules-based, approx)] (MKT): keeps 99.6% of trades and adds +0.01 pts per contract in the last 6 months (per signal -0.00, MDE 0.15; 42 signals touched, they earn +0.62 pts each under the base; HOLD -0.01)
* Skip all signals when [FOMC day, whole day (ET date)] (MKT): keeps 96.6% of trades and adds +0.13 pts per contract in the last 6 months (per signal +0.02, MDE 0.43; 334 signals touched, they earn -0.44 pts each under the base; HOLD +0.07)
* Skip all signals when [lunch window 11:30-13:30] (MKT): keeps 86.4% of trades and adds -0.05 pts per contract in the last 6 months (per signal -0.48, MDE 1.00; 1320 signals touched, they earn +3.55 pts each under the base; HOLD +0.06)
* Skip all signals when [the live 09:00-10:00 block window] (MKT): keeps 88.7% of trades and adds +0.44 pts per contract in the last 6 months (per signal +0.02, MDE 1.16; 1101 signals touched, they earn -0.21 pts each under the base; HOLD +0.35)

## 4. Best selected B cell per family and per book (PRE u X' z rank; recent look)

| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| st.prev_ret_rth>=0.7105 | rt50 | SPL | ALL | 0.46 | 0.24 | -0.23 | -0.11 | -0.10 | -0.10 | -0.10 | 0.64 | 10.84 | 3.46 | 0.70 |  |  |  |  | -0.10 | -0.10 | DEAD |
| evt.failbrk_high.within30.ict_with | d15 | MKT | ALL | 0.06 | 0.06 | 0.03 | 0.04 | 0.02 | 0.05 | 0.03 | 0.05 | 0.24 | -20.51 | 0.98 | 952.20 | 710.94 | 1142.03 | 1182.45 | 0.05 | 0.05 | CANDIDATE-RECENT |
| tm.rel.R830.pre30 | d15 | SPL | ALL | 0.07 | 0.05 | 0.03 | -0.02 | -0.02 | -0.02 | -0.02 | 0.07 | 0.59 | 8.23 | 0.36 |  |  |  |  | -0.02 | -0.02 | DEAD |
| px.ext.5m.ema20<=-1 | d5 | MKT | ALL | 0.02 | 0.00 | 0.01 | 0.02 | 0.02 | 0.02 | 0.02 | 0.03 | 0.33 | 11.89 | 0.79 |  |  |  |  | 0.02 | 0.02 | LEAD |
| aft.stackday_R_q20 | rt50 | MKT | ALL | 0.38 | 0.17 | -0.72 | -0.76 | -0.49 | -0.76 | -0.49 | 1.17 | 22.45 | 5.65 | 0.00 |  |  |  |  | -0.76 | -0.76 | DEAD |
| st.5m.squeeze==1 | rt50 | SPL | ALL | 0.18 | 0.29 | 0.24 | 0.19 | 0.11 | 0.20 | 0.12 | 0.59 | 12.05 | -1.96 | 1.00 | -3027.08 | -2273.21 | 2678.58 | -278.16 | 0.20 | 0.20 | CANDIDATE-RECENT |
| st.sig_intens_rel>=2.182 | d15 | MKT | ALL | 0.08 | 0.48 | -0.09 | -0.18 | -0.08 | 0.16 | 0.18 | 0.85 | 29.34 | 1.93 | 0.80 |  |  |  |  | 0.16 | 0.15 | DEAD |
| st.ret_RTY_15m>=30.98 | rt50 | SPL | ALL | 0.15 | 0.15 | -0.23 | -0.23 | -0.19 | -0.23 | -0.18 | 0.38 | 6.79 | 3.78 | 0.02 |  |  |  |  | -0.23 | -0.23 | DEAD |
| day.afterbigday1p5pct | d5 | SPL | ALL | 0.16 | 0.04 | 0.27 | 0.13 | 0.12 | 0.22 | 0.18 | 0.51 | 16.43 | 3.41 | 0.88 |  |  |  |  | 0.22 | 0.22 | LEAD |
| eng.opp_flip_within30 | rt50 | SPL | ALL | 0.05 | 0.04 | -0.11 | -0.06 | -0.07 | -0.06 | -0.07 | 0.19 | 3.96 | 1.15 | 0.40 |  |  |  |  | -0.06 | -0.06 | DEAD |
| vol.r60_pts>=20 | rt50 | MKT | ALL | 0.04 | 0.18 | -0.04 | -0.06 | -0.03 | -0.06 | -0.03 | 0.88 | 30.04 | 1.09 | 0.91 |  |  |  |  | -0.06 | -0.06 | DEAD |

Per book (best selected B cell by PRE u X' z within the book scope):

| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| st.es_nq_open30_agree==-1 | d5 | MKT | MA | 0.43 | 0.40 | -0.31 | -0.11 | -0.08 | -0.11 | -0.08 | 1.16 | 9.09 | 4.02 | 0.57 |  |  |  |  | -0.11 | -0.11 | DEAD |
| st.prev_ret_rth>=0.7105 | z25 | SPL | ST | 0.51 | 0.77 | -0.80 | -0.72 | -0.65 | -0.35 | -0.39 | 1.13 | 12.26 | 7.83 | 0.20 |  |  |  |  | -0.35 | -0.32 | DEAD |
| st.prev_ret_rth>=0.7105 | z50 | SPL | ST | 0.34 | 0.51 | -0.53 | -0.48 | -0.44 | -0.23 | -0.26 | 0.76 | 12.26 | 7.83 | 0.20 |  |  |  |  | -0.23 | -0.21 | DEAD |
| aft.book_winner_within10 | d15 | MKT | HM | 0.76 | 0.57 | -0.99 | -0.99 | -0.65 | -0.86 | -0.55 | 1.35 | 10.56 | 14.23 | 0.07 |  |  |  |  | -0.86 | -0.83 | DEAD |
| st.prev_er_rth>=0.1843 | rt50 | SPL | KB | 1.00 | 1.35 | 0.90 | 0.39 | 0.30 | 0.40 | 0.30 | 1.45 | 24.82 | -0.84 | 0.94 | -1890.21 | -1681.50 | -1086.69 | 2130.77 | 0.40 | 0.39 | CANDIDATE-RECENT |
| st.prev_ret_rth>=0.7105 | skip | SPL | MV | 0.66 | 1.10 | -0.56 | -0.26 | -0.24 | 0.00 | -0.09 | 1.86 | 11.49 | 2.27 | 0.46 |  |  |  |  | 0.00 | 0.00 | DEAD |
| st.prev_ret_rth>=0.7105 | z25 | SPL | MV | 0.50 | 0.82 | -0.42 | -0.20 | -0.18 | 0.00 | -0.06 | 1.39 | 11.49 | 2.27 | 0.46 |  |  |  |  | 0.00 | 0.00 | DEAD |
| st.rv30m_vs_med20d>=4.318 | d5 | MKT | PB | 0.55 | 0.36 | 0.65 | 0.25 | 0.15 | 0.44 | 0.29 | 1.23 | 9.01 | -0.75 | 0.65 |  |  |  |  | 0.44 | 0.43 | LEAD |
| px.ext.5m.ema200>=8 | d5 | MKT | PB | 0.52 | 0.05 | 0.74 | 0.26 | 0.24 | 0.26 | 0.24 | 0.82 | 12.47 | 13.06 | 0.90 | 0.00 | 0.00 | 0.00 | 0.00 | 0.26 | 0.26 | CANDIDATE-RECENT |
| st.prev_close_loc>=0.4225 | d15 | MKT | MA | 0.81 | 0.55 | -0.85 | -0.98 | -0.84 | -0.90 | -0.79 | 0.98 | 5.65 | 10.11 | 0.10 |  |  |  |  | -0.90 | -0.88 | DEAD |
| aft.book_winner_within10 | d15 | SPL | HM | 0.72 | 0.53 | -0.86 | -0.93 | -0.58 | -0.81 | -0.48 | 1.30 | 10.56 | 13.60 | 0.06 |  |  |  |  | -0.81 | -0.78 | DEAD |
| st.prev_rng_atrd>=1.697 | rt50 | SPL | KB | 0.92 | 0.30 | 0.77 | 0.51 | 0.47 | 0.52 | 0.47 | 1.29 | 13.05 | -7.11 | 0.96 | 997.06 | 872.43 | 1361.93 | 977.88 | 0.52 | 0.52 | CANDIDATE-RECENT |
| stk.same_lots_res>=60 | d15 | MKT | DN | 0.43 | 0.62 | -0.30 | -0.48 | -0.20 | -0.46 | -0.19 | 0.81 | 4.71 | 9.83 | 0.26 |  |  |  |  | -0.46 | -0.46 | DEAD |
| st.5m.squeeze==1 | rt50 | MKT | PE | 0.55 | 0.49 | 0.34 | 0.38 | 0.32 | 0.38 | 0.32 | 1.36 | 9.13 | -3.94 | 0.94 | -171.82 | -373.16 | 1121.29 | 2143.06 | 0.38 | 0.38 | CANDIDATE-RECENT |
| st.5m.chop14>=53.83 | d15 | MKT | SM | 0.99 | 1.07 | -1.00 | -0.93 | -0.77 | -0.91 | -0.73 | 2.59 | 14.01 | 1.58 | 0.17 |  |  |  |  | -0.91 | -0.89 | DEAD |
| xm.es_minus_nq30s<=-1.5 | d5 | MKT | SM | 1.08 | 0.40 | -0.54 | -0.46 | -0.06 | -0.44 | -0.04 | 1.26 | 4.14 | 13.22 | 0.16 |  |  |  |  | -0.44 | -0.44 | DEAD |
| stk.same_lots_res>=60 | d15 | SPL | DN | 0.44 | 0.46 | -0.31 | -0.42 | -0.15 | -0.41 | -0.14 | 0.75 | 4.71 | 9.29 | 0.27 |  |  |  |  | -0.41 | -0.41 | DEAD |
| st.sig_delta10_s<=-26 | d5 | MKT | PE | 0.65 | 0.30 | 1.05 | 0.76 | 0.68 | 0.79 | 0.71 | 0.83 | 9.97 | -13.18 | 0.99 | 1031.90 | 557.96 | 699.08 | 3193.17 | 0.79 | 0.78 | CANDIDATE-RECENT |
| bk.imb10_run<=-10 | d5 | SPL | WT | 0.12 | 0.05 | -0.15 | -0.00 | -0.00 | 0.01 | 0.00 | 0.31 | 4.34 | -1.72 | 0.54 |  |  |  |  | 0.01 | 0.01 | DEAD |
| st.15m.macd_hist>=0.4146 | d5 | MKT | WT | 0.15 | 0.64 | 0.11 | 0.07 | 0.05 | 0.10 | 0.07 | 0.58 | 8.38 | -2.52 | 0.62 |  |  |  |  | 0.10 | 0.10 | LEAD |

## 5. Section D - the opposite side: take-only / size-up where the map shows a higher P(target) (STRUCTURE: lots rise; compare uex and eqr, not the raw gain)

363 size-up / take-only cell-scopes are CANDIDATE-RECENT or better with a positive stack; pooled u200 / MKT cells ranked by stack, with the lot-matched controls and the PRE / X' stack signs (the X' stack is negative for several - the rule is not consistent in 2023-24):

| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| px.ext.1m.ema200>=5 | u200 | MKT | ALL | 0.78 | 0.81 | 2.37 | 3.02 | 2.62 | 1.21 | 1.12 | 1.95 | 40.79 | 7.41 | 1.00 | 54570.58 | 54741.75 | 30788.63 | -9423.97 | 1.21 | 1.70 | PASS_pre_RC |
| px.loc.SESS.premium | u200 | MKT | ALL | 1.11 | 0.61 | 2.16 | 2.95 | 2.55 | 0.49 | 0.52 | 2.65 | 66.12 | 4.46 | 1.00 | 46625.21 | 44264.36 | 37552.03 | 16903.95 | 0.49 | 0.81 | CANDIDATE-RECENT |
| px.loc.DEAL4H.premium | u200 | MKT | ALL | 1.13 | 1.23 | 0.71 | 2.24 | 1.67 | 0.42 | 0.27 | 2.64 | 49.80 | 4.50 | 0.99 | 44709.86 | 39024.66 | 31770.44 | 21322.25 | 0.42 | 0.62 | CANDIDATE-RECENT |
| px.loc.SESS.sidedloc>=0.8 | u200 | MKT | ALL | 0.88 | 0.56 | 2.19 | 2.54 | 2.17 | 0.60 | 0.59 | 2.44 | 50.66 | 5.02 | 1.00 | 40908.80 | 35045.18 | 30944.38 | 5438.03 | 0.60 | 0.90 | CANDIDATE-RECENT |
| st.1h.range_pos60>=0.3562 | u200 | MKT | ALL | 1.22 | 0.84 | 0.25 | 1.15 | 0.89 | 0.27 | 0.22 | 1.99 | 25.14 | 4.57 | 0.94 | 38762.42 | 32230.35 | 29946.66 | 22375.00 | 0.27 | 0.33 | CANDIDATE-RECENT |
| px.ext.5m.ema20>=1.5 | u200 | MKT | ALL | 1.07 | 0.60 | 1.97 | 2.46 | 2.07 | 0.56 | 0.54 | 2.13 | 49.84 | 4.93 | 1.00 | 38397.80 | 36058.40 | 30277.87 | 198.35 | 0.56 | 0.84 | CANDIDATE-RECENT |
| px.ext.5m.ema50>=3 | u200 | MKT | ALL | 0.93 | 0.85 | 1.46 | 2.00 | 1.83 | 0.78 | 0.81 | 1.72 | 30.49 | 6.56 | 1.00 | 36122.09 | 35227.97 | 15073.16 | -5885.93 | 0.78 | 1.01 | PASS_pre_RC |
| st.1m.rng_exp1<=0.9489 | u200 | MKT | ALL | 0.58 | 0.26 | 1.45 | 1.69 | 1.31 | 0.66 | 0.51 | 1.41 | 26.44 | 6.39 | 0.99 | 35984.51 | 27159.00 | 23384.71 | -1213.68 | 0.66 | 0.83 | CANDIDATE-RECENT |
| stk.same_lots_live>=4 | u200 | MKT | ALL | 1.31 | 0.48 | 1.27 | 2.26 | 1.77 | 0.52 | 0.38 | 2.10 | 46.37 | 4.87 | 0.94 | 35775.02 | 34902.38 | 35896.30 | -1845.02 | 0.52 | 0.76 | CANDIDATE-RECENT |
| px.chase.pooled>=1 | u200 | MKT | ALL | 1.50 | 0.53 | 2.44 | 3.31 | 2.66 | 0.39 | 0.34 | 2.83 | 80.46 | 4.11 | 1.00 | 33988.89 | 34166.50 | 32627.79 | 15124.39 | 0.39 | 0.70 | CANDIDATE-RECENT |
| px.late.atDayExtreme20_run50 | u200 | MKT | ALL | 0.38 | 1.00 | 0.56 | 1.33 | 1.19 | 0.45 | 0.48 | 1.43 | 23.73 | 5.60 | 0.99 | 33319.58 | 26327.91 | 7521.86 | 15231.83 | 0.45 | 0.56 | CANDIDATE-RECENT |
| st.15m.hma_slope>=0.4067 | u200 | MKT | ALL | 0.68 | 0.39 | 1.07 | 1.45 | 1.16 | 0.58 | 0.47 | 1.46 | 22.88 | 6.34 | 1.00 | 32952.39 | 30991.79 | 3326.04 | 13364.98 | 0.58 | 0.71 | CANDIDATE-RECENT |
| st.1m.rng_exp1<=0.7 | u200 | MKT | ALL | 0.26 | 0.20 | 0.76 | 0.66 | 0.48 | 0.27 | 0.18 | 0.68 | 10.94 | 6.00 | 0.93 | 32287.02 | 25029.30 | -2002.24 | 1594.18 | 0.27 | 0.30 | CANDIDATE-RECENT |
| px.chase.pooled>=2 | u200 | MKT | ALL | 1.19 | 0.32 | 2.45 | 3.22 | 2.68 | 0.55 | 0.53 | 2.67 | 70.24 | 4.58 | 1.00 | 31655.82 | 29750.58 | 27457.04 | -2577.32 | 0.55 | 0.94 | CANDIDATE-RECENT |
| px.ext.15m.ema200>=3 | u200 | MKT | ALL | 0.68 | 1.36 | 0.80 | 1.74 | 1.30 | 0.25 | 0.17 | 2.26 | 42.70 | 4.08 | 0.92 | 30703.26 | 27364.59 | 21329.85 | 26351.83 | 0.25 | 0.36 | CANDIDATE-RECENT |

Take-only (keep ONLY the signals inside the state, skip the rest), selected on PRE u X':
| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| cal.weekend_gap>=20 | keeponly | SPL | ALL | 0.16 | 0.35 | -0.26 | -0.21 | -0.19 | -0.15 | -0.14 | 0.42 | 1.94 | 10.86 | 1.00 |  |  |  |  | -0.15 | -0.15 | DEAD |
| cal.weekend_gap>=20 | keeponly | MKT | ALL | 0.17 | 0.39 | -0.27 | -0.22 | -0.20 | -0.16 | -0.15 | 0.43 | 1.94 | 11.11 | 1.00 |  |  |  |  | -0.16 | -0.15 | DEAD |
| cal.weekend_gap>=40 | keeponly | SPL | ALL | 0.10 | 0.36 | -0.60 | -0.51 | -0.46 | -0.42 | -0.39 | 0.62 | 3.05 | 16.60 | 1.00 |  |  |  |  | -0.42 | -0.41 | DEAD |
| cal.weekend_gap>=40 | keeponly | MKT | ALL | 0.11 | 0.41 | -0.61 | -0.51 | -0.46 | -0.42 | -0.40 | 0.63 | 3.05 | 16.63 | 1.00 |  |  |  |  | -0.42 | -0.41 | DEAD |

Both edges per state (map file DS3_NO_TRADE_MAP_2.md section 9) show the same states: the higher-P(target) states are trend-continuation (extension / chase / premium location / ER high / trend-agreement), the lower-P states are their mirror, i.e. the no-trade map and the size-up map are ONE continuum (trend strength), not two independent findings.

## 6. Section C1 - combinations (pairs, triples, any-of-k, four-legged, nested with the 8-line set, per-book pairs)

1600 selected combination cell-scopes carried (1,491 masks x 6 actions x 2 bases scored on PRE u X'); mean gain per signal PRE / X' +0.311 / +0.324, L6M / HOLD -0.113 / -0.101; >= 0 in both: 641; CANDIDATE-RECENT 295; PASS_pre_RC 0.

* pairs: 371 selected cell-scopes; mean L6M -0.101, HOLD -0.095; >= 0 both 146; tier>=CAND 69
* triples: 173 selected cell-scopes; mean L6M -0.207, HOLD -0.193; >= 0 both 56; tier>=CAND 23
* any-of-k: 196 selected cell-scopes; mean L6M -0.157, HOLD -0.114; >= 0 both 78; tier>=CAND 20
* four-legged: 0 selected cell-scopes; mean L6M +nan, HOLD +nan; >= 0 both 0; tier>=CAND 0
* nested with set8 / set11: 136 selected cell-scopes; mean L6M -0.085, HOLD -0.086; >= 0 both 34; tier>=CAND 2
* per-book pairs: 724 selected cell-scopes; mean L6M -0.089, HOLD -0.081; >= 0 both 327; tier>=CAND 181

Best combination cells (tier >= CANDIDATE-RECENT, by L6M gain; stack where computed):
| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | rt50 | MKT | SM | 0.23 | 0.44 | 1.65 | 1.36 | 1.17 | 1.36 | 1.17 | 2.04 | 4.14 | -20.13 | 0.98 | 1548.96 | 1355.34 | 212.33 | 525.28 | 1.36 | 1.36 | CANDIDATE-RECENT |
| ANY4of30 | d15 | SPL | SM | 0.52 | 0.82 | 1.89 | 1.30 | 1.48 | 1.40 | 1.60 | 2.54 | 11.15 | -5.41 | 0.95 | 2850.95 | 3071.14 | 906.32 | 1372.99 | 1.40 | 1.37 | CANDIDATE-RECENT |
| ANY4of30 | d15 | MKT | SM | 0.34 | 1.06 | 1.88 | 1.29 | 1.47 | 1.38 | 1.57 | 2.63 | 11.15 | -5.45 | 0.96 | 2775.93 | 2995.78 | 587.31 | 1227.88 | 1.38 | 1.34 | CANDIDATE-RECENT |
| ANY3of30 | d15 | SPL | SM | 0.78 | 1.14 | 2.43 | 1.28 | 1.13 | 1.54 | 1.43 | 3.80 | 27.07 | -5.25 | 0.97 | 3417.87 | 3039.58 | 1423.77 | 1512.35 | 1.55 | 1.46 | CANDIDATE-RECENT |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | d15 | MKT | SM | 0.42 | 0.45 | 1.58 | 1.22 | 1.06 | 1.25 | 1.09 | 1.82 | 4.14 | -20.13 | 1.00 | 1441.78 | 1261.56 | 663.43 | 692.54 | 1.25 | 1.24 | CANDIDATE-RECENT |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | d15 | SPL | SM | 0.37 | 0.37 | 2.12 | 1.12 | 0.97 | 1.15 | 1.01 | 2.24 | 4.14 | -10.38 | 1.00 | 1279.03 | 1119.15 | 327.57 | 881.78 | 1.16 | 1.15 | CANDIDATE-RECENT |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301&st.days_since_t | d15 | SPL | SM | 0.19 | 0.17 | 2.12 | 1.12 | 0.97 | 1.15 | 1.01 | 2.24 | 3.82 | -16.29 | 1.00 | 1278.28 | 1118.49 | 119.24 | 469.26 | 1.16 | 1.15 | CANDIDATE-RECENT |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | skip | MKT | MA | 0.99 | 0.52 | 1.13 | 1.06 | 0.90 | 1.32 | 1.11 | 1.60 | 3.19 | -33.33 | 1.00 | 0.00 | 0.00 | 0.00 | 0.00 | 1.32 | 1.28 | CANDIDATE-RECENT |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301] | d15 | SPL | SM | 0.56 | 0.18 | 1.96 | 1.03 | 0.89 | 1.11 | 0.98 | 2.22 | 5.73 | -4.12 | 1.00 | 1777.24 | 1555.09 | 257.33 | 477.91 | 1.11 | 1.09 | CANDIDATE-RECENT |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | rt50 | SPL | SM | 0.18 | 0.38 | 1.54 | 0.91 | 0.79 | 0.92 | 0.80 | 1.97 | 4.14 | -10.38 | 0.94 | 829.87 | 726.14 | -115.20 | 624.25 | 0.92 | 0.92 | CANDIDATE-RECENT |
| ANY2of10[evt.failbrk_high.within30.ict_with,st.prev_ret_rth>=0.7105,st | skip | MKT | KB | 1.15 | 1.73 | 1.36 | 0.85 | 0.81 | 1.43 | 1.22 | 1.91 | 18.93 | -4.48 | 0.97 | 2695.51 | 2273.34 | 412.67 | 4226.84 | 1.43 | 1.16 | CANDIDATE-RECENT |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301&st.days_since_t | d15 | MKT | SM | 0.22 | 0.20 | 1.58 | 0.84 | 0.73 | 0.86 | 0.75 | 1.53 | 3.82 | -16.71 | 0.99 | 824.36 | 721.32 | 419.70 | 291.42 | 0.86 | 0.85 | CANDIDATE-RECENT |
| ANY2of10[evt.failbrk_high.within30.ict_with,st.prev_ret_rth>=0.7105,st | d15 | SPL | SM | 0.69 | 1.16 | 2.02 | 0.83 | 0.72 | 0.94 | 0.85 | 3.40 | 15.29 | 2.51 | 0.96 | 2006.54 | 1757.75 | 560.38 | 1839.91 | 0.95 | 0.92 | CANDIDATE-RECENT |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | z25 | MKT | MA | 0.74 | 0.39 | 0.85 | 0.80 | 0.68 | 0.98 | 0.82 | 1.20 | 3.19 | -33.33 | 1.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.98 | 0.96 | CANDIDATE-RECENT |
| ANY2of10[evt.failbrk_high.within30.ict_with,st.prev_ret_rth>=0.7105,st | skip | SPL | KB | 1.05 | 1.84 | 1.27 | 0.77 | 0.73 | 1.27 | 1.07 | 1.99 | 18.93 | -4.08 | 0.95 | 250.71 | 450.80 | 1023.99 | 4662.51 | 1.27 | 1.03 | CANDIDATE-RECENT |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301] | d15 | MKT | SM | 0.59 | 0.21 | 1.44 | 0.76 | 0.66 | 0.81 | 0.72 | 1.50 | 5.73 | -4.66 | 0.97 | 1327.83 | 1161.86 | 550.07 | 299.83 | 0.81 | 0.80 | CANDIDATE-RECENT |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | skip | SPL | MA | 0.96 | 0.52 | 0.56 | 0.75 | 0.63 | 0.99 | 0.82 | 1.17 | 3.19 | -23.56 | 1.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.99 | 0.96 | CANDIDATE-RECENT |
| ANY3of30 | skip | SPL | MV | 1.14 | 3.08 | 0.75 | 0.69 | 0.56 | 1.86 | 1.34 | 1.71 | 28.47 | -2.42 | 0.94 | 0.00 | 0.00 | 0.00 | 0.00 | 1.87 | 1.34 | CANDIDATE-RECENT |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | skip | SPL | KB | 1.06 | 0.96 | 0.98 | 0.67 | 0.62 | 1.05 | 0.85 | 1.59 | 15.67 | -4.30 | 0.95 | 1697.47 | 1485.28 | 1096.87 | 2841.15 | 1.05 | 0.88 | CANDIDATE-RECENT |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | rt50 | MKT | KB | 0.71 | 1.02 | 0.90 | 0.67 | 0.62 | 0.67 | 0.62 | 1.03 | 15.67 | -4.25 | 0.99 | 951.02 | 832.15 | -980.10 | 2295.45 | 0.67 | 0.67 | CANDIDATE-RECENT |

Does a combination beat its best single leg? For each of the top combination cells the best single-leg cell on the same scope/action/base (from section B table) is looked up below (PRE u X' z of the combo vs its legs):
