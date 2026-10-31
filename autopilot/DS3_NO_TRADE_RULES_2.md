# DS3_NO_TRADE_RULES_2 - T-NO-TRADE-EXPANDED sections B, C, D: single-state rules, combinations, opposite side (NTE-1, 2026-10-31)

Research only. Prereg autopilot/NTE_prereg.md sha256 b446844d...; B/D carry list sha256 16449e8e... (PRE u X' selection, logged before the recent look); combination carry list sha256 459876f7...; learned model: weekly walk-forward (no selection). UNTOUCHED never read. Units: gain PER SIGNAL (rule net - base net over all the scope's signals, N basis, so skipped winners are charged), PER CONTRACT of final lots (kept signals, rule vs base), lock-engine STACK $/wk (6 engine books, research lots, planned-lot-R locks; sized-lot-R lock variant not available for per-signal multipliers - named limitation), eqr = equal-risk gain per signal (rule mean / lot ratio - base mean; STRUCTURE), uex = gain over the lot-factor-matched uniform scaling of the base. 'skipped pts' = mean N-basis P&L per signal of the signals the rule touches under the base (what is thrown away). plc = rank of the real L6M gain among 200 random fire sets at the same count per book x session x side x era x target-distance stratum (1.00 = beats all). Tiers follow the V2 gates unsoftened: LEAD = selected (gain>0 in PRE and X') and L6M >= 0; CANDIDATE-RECENT = + gain>0 and per contract >0 in L6M and HOLD and plc >= 0.90; PASS_pre_RC = + plc >= 0.95, above MDE in L6M and HOLD, stack > 0 in L6M and HOLD (before the program-level reality check, which none of them clears cumulatively).

## PAGE 1 - the answer

* B skip (selected on PRE u X'): 308 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +0.542 / +0.595, in the single recent look L6M / HOLD / L3M = -0.282 / -0.247 / -0.225; 101 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 46, PASS_pre_RC 0.
* B size 50% / 25%: 614 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +0.338 / +0.368, in the single recent look L6M / HOLD / L3M = -0.179 / -0.156 / -0.143; 201 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 92, PASS_pre_RC 0.
* B delay 5 / 15 min: 904 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +0.330 / +0.276, in the single recent look L6M / HOLD / L3M = -0.108 / -0.096 / -0.120; 389 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 134, PASS_pre_RC 3.
* B re-target x0.5: 474 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +0.321 / +0.442, in the single recent look L6M / HOLD / L3M = -0.164 / -0.150 / -0.043; 137 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 51, PASS_pre_RC 0.
* D take-only (skip everything outside the state): 53 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +1.437 / +1.553, in the single recent look L6M / HOLD / L3M = -0.897 / -0.522 / -0.487; 8 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 2, PASS_pre_RC 0.
* D size up x1.5 / x2 inside the state: 2247 selected cell-scopes carried; mean gain per signal on the selection windows PRE / X' = +0.821 / +0.641, in the single recent look L6M / HOLD / L3M = +0.660 / +0.552 / +0.392; 1814 are >= 0 in both L6M and HOLD; CANDIDATE-RECENT 476, PASS_pre_RC 35.

* **Skip rules decay out of sample and size-up rules are positive by construction.** The pooled skip cells chosen on PRE u X' average +0.110 / +0.167 per signal in PRE / X' and -0.230 / -0.193 in L6M / HOLD: the states that preceded failures in 2023-25 do not keep their sign. The size-up cells (D) are positive in the recent windows because the base is positive and the states are trend-continuation states (extension in the trade direction, premium location, chase): they are reported with the uniform-scaling control (uex) and equal-risk gain (eqr), they raise lots by 1.3-1.9x (the 50-contract cap and the margin question apply), and they are STRUCTURE until a forward test.
* Cells with tier >= CANDIDATE-RECENT AND stack > 0 in both L6M and HOLD: B 71, D 127; of the B cells, 71 are pooled (ALL scope).
* Program reality check B|MKT: 400 selected pooled cells; White RC best-cell p L6M 0.976 / HOLD 0.904; Sidak-adjusted to 317,628 cell-scopes (L6M) 1.000; Romano-Wolf survivors L6M 0, HOLD 0; PBO 0.41; min backtest length 8.9 y (bound 12.0). Against the lot-matched uniform scaling of the base (the right null for size rules): RC p 0.272 / 0.282, Romano-Wolf survivors 3 / 0, PBO 0.39.
* Program reality check B|SPL: 400 selected pooled cells; White RC best-cell p L6M 0.964 / HOLD 0.878; Sidak-adjusted to 317,628 cell-scopes (L6M) 1.000; Romano-Wolf survivors L6M 0, HOLD 0; PBO 0.42; min backtest length 8.9 y (bound 12.0). Against the lot-matched uniform scaling of the base (the right null for size rules): RC p 0.214 / 0.226, Romano-Wolf survivors 3 / 3, PBO 0.40.
* Program reality check D|MKT: 400 selected pooled cells; White RC best-cell p L6M 0.000 / HOLD 0.022; Sidak-adjusted to 317,628 cell-scopes (L6M) 0.000; Romano-Wolf survivors L6M 24, HOLD 10; PBO 0.79; min backtest length 8.9 y (bound 12.0). Against the lot-matched uniform scaling of the base (the right null for size rules): RC p 0.072 / 0.062, Romano-Wolf survivors 2 / 4, PBO 0.74.
* Program reality check D|SPL: 400 selected pooled cells; White RC best-cell p L6M 0.000 / HOLD 0.018; Sidak-adjusted to 317,628 cell-scopes (L6M) 0.000; Romano-Wolf survivors L6M 24, HOLD 12; PBO 0.69; min backtest length 8.9 y (bound 12.0). Against the lot-matched uniform scaling of the base (the right null for size rules): RC p 0.336 / 0.576, Romano-Wolf survivors 0 / 0, PBO 0.67.

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
| D | u150 | MKT | 562 | 0.565 | 0.429 | 0.278 | 0.449 | 0.374 | 0.587 | 0.799 | 0.153 | 124 | 8 |
| D | u150 | SPL | 561 | 0.530 | 0.425 | 0.244 | 0.431 | 0.362 | 0.509 | 0.793 | 0.168 | 113 | 10 |
| D | u200 | MKT | 563 | 1.128 | 0.861 | 0.557 | 0.898 | 0.746 | 1.173 | 0.799 | 0.153 | 124 | 8 |
| D | u200 | SPL | 561 | 1.060 | 0.849 | 0.488 | 0.862 | 0.726 | 1.014 | 0.795 | 0.166 | 115 | 9 |

## 2. Section B - best single-state B cells that are CANDIDATE-RECENT or better with the stack > 0 in L6M and HOLD (sorted by stack L6M; PRE / X' = gain per signal the cell was selected on; the recent look is one look)

171 cells; pooled (ALL) first, then book / session scopes.

### 2a. pooled
| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | touched/wk | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | $/wk live | $/wk res | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| set.ahead20_set11_fresh | skip | SPL | ALL | 0.28 | 0.45 | 0.47 | 0.36 | 0.45 | 1.03 | 1.06 | 0.93 | 15.62 | 54.36 | -2.32 | 1.00 | 30117.59 | 26652.50 | 8879.78 | 3150.16 | 1.03 | 0.87 | 1570.71 | 22342.58 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | skip | MKT | ALL | 0.31 | 0.40 | 0.39 | 0.31 | 0.42 | 0.97 | 1.02 | 0.95 | 15.62 | 54.36 | -2.02 | 1.00 | 29833.67 | 25283.76 | 11298.83 | 5714.07 | 0.97 | 0.82 | 1323.21 | 19925.82 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | z25 | SPL | ALL | 0.21 | 0.34 | 0.36 | 0.27 | 0.34 | 0.74 | 0.76 | 0.70 | 15.62 | 54.36 | -2.32 | 1.00 | 24278.59 | 21155.67 | 6258.86 | 3566.68 | 0.74 | 0.65 | 1178.03 | 16756.93 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | z25 | MKT | ALL | 0.23 | 0.30 | 0.29 | 0.24 | 0.32 | 0.70 | 0.73 | 0.71 | 15.62 | 54.36 | -2.02 | 1.00 | 19789.95 | 15628.60 | 10624.78 | 6660.13 | 0.70 | 0.62 | 992.41 | 14944.37 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | z50 | SPL | ALL | 0.14 | 0.23 | 0.24 | 0.18 | 0.23 | 0.47 | 0.48 | 0.47 | 15.62 | 54.36 | -2.32 | 1.00 | 17517.01 | 14937.98 | 2221.53 | 4034.47 | 0.47 | 0.44 | 785.35 | 11171.29 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | z50 | MKT | ALL | 0.15 | 0.20 | 0.20 | 0.16 | 0.21 | 0.45 | 0.46 | 0.48 | 15.62 | 54.36 | -2.02 | 1.00 | 14879.69 | 11534.61 | 5048.46 | 4575.50 | 0.45 | 0.41 | 661.61 | 9962.91 | CANDIDATE-RECENT |
| st.f60_vs_med>=1.809 | d15 | SPL | ALL | 0.12 | 0.05 | 0.50 | 0.23 | 0.22 | 0.37 | 0.32 | 0.70 | 11.68 | 40.64 | -3.05 | 0.99 | 10697.12 | 9523.70 | 53.95 | 6.75 | 0.37 | 0.35 | 2418.24 | 11840.34 | CANDIDATE-RECENT |
| st.f60_vs_med>=1.809 | d15 | MKT | ALL | 0.11 | 0.04 | 0.45 | 0.19 | 0.18 | 0.32 | 0.27 | 0.71 | 11.68 | 40.64 | -2.92 | 0.99 | 10517.91 | 9099.67 | 2578.03 | -358.64 | 0.32 | 0.31 | 1840.28 | 9573.51 | CANDIDATE-RECENT |
| eng.opp_flip_within60 | rt50 | SPL | ALL | 0.02 | 0.09 | 0.17 | 0.08 | 0.05 | 0.09 | 0.05 | 0.34 | 9.04 | 31.46 | -0.24 | 0.98 | 7978.59 | 6972.93 | -4042.84 | -2418.07 | 0.09 | 0.09 | -1491.14 | 7196.95 | CANDIDATE-RECENT |
| st.sig_vel30<=-3.6 | d5 | MKT | ALL | 0.05 | 0.12 | 0.33 | 0.17 | 0.17 | 0.22 | 0.21 | 0.32 | 11.16 | 38.82 | 2.32 | 0.97 | 7815.29 | 6306.57 | -7322.21 | 3169.78 | 0.22 | 0.22 | 3188.71 | 6299.96 | CANDIDATE-RECENT |
| xm.es15s<=-1 | d5 | SPL | ALL | 0.08 | 0.03 | 0.29 | 0.14 | 0.15 | 0.19 | 0.19 | 0.32 | 9.72 | 33.82 | -0.98 | 0.94 | 7480.32 | 6750.94 | -8877.99 | 723.90 | 0.19 | 0.19 | 3999.61 | 4206.79 | CANDIDATE-RECENT |
| set.ahead20_set11_fresh | rt50 | SPL | ALL | 0.05 | 0.11 | 0.33 | 0.21 | 0.18 | 0.22 | 0.19 | 0.75 | 15.62 | 54.36 | -2.32 | 1.00 | 6995.07 | 5980.26 | -587.28 | -5765.31 | 0.22 | 0.22 | 276.59 | 12926.77 | CANDIDATE-RECENT |
| st.sig_vel30<=-3.6 | d5 | SPL | ALL | 0.06 | 0.11 | 0.36 | 0.17 | 0.18 | 0.22 | 0.21 | 0.38 | 11.16 | 38.82 | 2.39 | 0.99 | 6220.54 | 5512.82 | -6876.80 | 2854.62 | 0.22 | 0.21 | 2947.44 | 5646.56 | CANDIDATE-RECENT |
| st.rv30_ann>=46.11 | rt50 | SPL | ALL | 0.04 | 0.16 | 0.34 | 0.20 | 0.17 | 0.21 | 0.17 | 0.47 | 6.14 | 21.36 | -6.82 | 1.00 | 6171.04 | 5293.15 | -4333.42 | -153.85 | 0.21 | 0.21 | 1915.80 | 10402.55 | CANDIDATE-RECENT |
| st.sig_vol60>=2533 | d5 | MKT | ALL | 0.01 | 0.23 | 0.56 | 0.24 | 0.22 | 0.36 | 0.31 | 0.69 | 8.65 | 30.11 | 0.55 | 0.97 | 5660.23 | 5048.91 | -664.36 | 8868.50 | 0.36 | 0.35 | 4645.17 | 11228.05 | CANDIDATE-RECENT |
| st.prev_close_loc>=0.4225 | d15 | SPL | ALL | 0.07 | 0.09 | 0.32 | 0.24 | 0.17 | 0.31 | 0.22 | 0.32 | 6.54 | 22.75 | -2.58 | 1.00 | 4964.30 | 4017.13 | -5619.03 | 1580.95 | 0.31 | 0.30 | 5313.03 | 10296.60 | CANDIDATE-RECENT |
| st.sig_vol60>=2533 | d5 | SPL | ALL | 0.01 | 0.30 | 0.56 | 0.25 | 0.23 | 0.38 | 0.33 | 0.69 | 8.65 | 30.11 | 0.44 | 1.00 | 4920.89 | 4290.20 | -509.86 | 8864.35 | 0.38 | 0.36 | 4670.04 | 11462.60 | CANDIDATE-RECENT |
| st.1d.chop14>=60.39 | rt50 | MKT | ALL | 0.04 | 0.31 | 0.01 | 0.01 | 0.11 | 0.01 | 0.11 | 0.51 | 15.05 | 52.36 | 2.33 | 0.94 | 4331.40 | 8158.25 | -2178.86 | 341.47 | 0.01 | 0.01 | -28.40 | 3144.98 | CANDIDATE-RECENT |
| px.loc.OR30.sidedloc<=0.2 | d15 | MKT | ALL | 0.08 | 0.07 | 0.04 | 0.08 | 0.07 | 0.12 | 0.10 | 0.19 | 7.46 | 25.96 | -4.20 | 0.92 | 4184.45 | 3761.33 | 4805.81 | -708.92 | 0.12 | 0.12 | 199.16 | 5282.12 | CANDIDATE-RECENT |
| st.1h.rng_exp1<=0.6003 | z25 | SPL | ALL | 0.01 | 0.24 | 0.10 | 0.07 | 0.15 | 0.29 | 0.33 | 0.46 | 8.26 | 28.75 | -1.06 | 0.99 | 3936.00 | 4850.14 | -5730.44 | 7903.26 | 0.29 | 0.27 | -1244.74 | 3447.28 | CANDIDATE-RECENT |
| st.sig_delta10_s<=-26 | d5 | MKT | ALL | 0.10 | 0.11 | 0.30 | 0.21 | 0.23 | 0.28 | 0.28 | 0.34 | 9.73 | 33.86 | 2.68 | 0.97 | 3912.80 | 3561.70 | -4284.51 | 8763.41 | 0.28 | 0.27 | 5047.53 | 8802.87 | CANDIDATE-RECENT |
| st.prev_rng_atrd>=1.697 | d15 | MKT | ALL | 0.14 | 0.07 | 0.22 | 0.24 | 0.21 | 0.41 | 0.33 | 0.44 | 12.80 | 44.54 | -0.15 | 1.00 | 3840.61 | 3360.54 | -284.20 | -89.09 | 0.41 | 0.39 | 8540.82 | 8450.50 | CANDIDATE-RECENT |
| st.prev_close_loc>=0.4225 | skip | MKT | ALL | 0.05 | 0.33 | 0.04 | 0.15 | 0.06 | 0.39 | 0.25 | 0.88 | 6.54 | 22.75 | -2.33 | 1.00 | 3806.38 | 2165.82 | -5611.36 | 2417.18 | 0.39 | 0.36 | 4878.23 | 4302.55 | CANDIDATE-RECENT |
| st.rv30_ann>=46.11 | rt50 | MKT | ALL | 0.04 | 0.14 | 0.35 | 0.22 | 0.19 | 0.22 | 0.19 | 0.47 | 6.14 | 21.36 | -7.19 | 1.00 | 3800.49 | 3220.43 | -987.53 | -754.52 | 0.22 | 0.22 | 1906.05 | 12073.26 | CANDIDATE-RECENT |
| bk.sweepvol_against30>=150 | d5 | MKT | ALL | 0.03 | 0.10 | 0.48 | 0.18 | 0.14 | 0.29 | 0.22 | 0.36 | 8.36 | 29.07 | 1.76 | 0.93 | 3574.45 | 2715.30 | 1055.29 | 4064.36 | 0.29 | 0.28 | 3449.55 | 8573.44 | CANDIDATE-RECENT |

### 2b. book / session scopes (live books first by $)
| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | touched/wk | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | $/wk live | $/wk res | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| bk.t_since_big_against<=300 | d15 | MKT | HM | 0.35 | 1.07 | -0.32 | 0.36 | 0.37 | 0.80 | 0.71 | 1.80 | 18.92 | 6.14 | 1.03 | 0.97 | 7736.84 | 7285.45 | 4095.93 | 458.66 | 0.80 | 0.73 | -38.84 | 2324.96 | CANDIDATE-RECENT |
| bk.t_since_big_against<=300 | d15 | SPL | HM | 0.44 | 1.01 | -0.12 | 0.28 | 0.19 | 0.69 | 0.50 | 1.61 | 18.92 | 6.14 | 1.86 | 0.96 | 7268.77 | 6155.72 | 3088.59 | -916.56 | 0.69 | 0.63 | 317.50 | 1808.96 | CANDIDATE-RECENT |
| st.1h.atr_ratio<=0.9103 | d5 | MKT | WT | 0.30 | 0.20 | 0.43 | 0.47 | 0.54 | 0.59 | 0.62 | 0.78 | 27.43 | 16.71 | -1.41 | 0.96 | 6153.95 | 6022.80 | 377.88 | 1333.76 | 0.59 | 0.56 | 0.00 | 4051.25 | CANDIDATE-RECENT |
| st.sig_vel30<=-3.6 | d5 | MKT | nyam | 0.22 | 0.50 | 0.93 | 0.63 | 0.65 | 0.75 | 0.76 | 0.73 | 16.06 | 15.96 | -3.19 | 0.97 | 5629.11 | 4490.29 | -2573.38 | 2512.62 | 0.75 | 0.72 | 4210.47 | 8817.71 | CANDIDATE-RECENT |
| st.ret_ES_15m<=-4.073 | d5 | MKT | asia | 0.13 | 0.05 | 0.39 | 0.21 | 0.18 | 0.23 | 0.19 | 0.53 | 4.59 | 4.39 | -1.66 | 1.00 | 4897.74 | 4084.26 | -916.04 | -502.37 | 0.23 | 0.23 | 946.09 | 3017.23 | CANDIDATE-RECENT |
| st.sig_intens_rel>=2.182 | d15 | SPL | PE | 0.58 | 0.43 | 1.80 | 1.01 | 0.85 | 1.15 | 0.97 | 1.56 | 25.29 | 10.79 | -2.77 | 0.96 | 4447.42 | 2788.39 | -809.45 | 748.92 | 1.15 | 1.07 | 2835.56 | 4820.99 | CANDIDATE-RECENT |
| st.prev_rng_atrd>=1.301 | d5 | MKT | KB | 0.73 | 0.09 | 2.14 | 1.33 | 1.05 | 1.40 | 1.10 | 1.97 | 34.92 | 15.68 | 1.12 | 0.97 | 4315.44 | 3492.92 | 1560.46 | 1405.18 | 1.40 | 1.37 | 2388.95 | 6190.85 | CANDIDATE-RECENT |
| day.afterbigday1p5pct | d5 | SPL | KB | 0.74 | 0.04 | 1.90 | 1.03 | 0.94 | 1.08 | 0.98 | 1.70 | 17.10 | 7.68 | -2.64 | 0.97 | 3908.66 | 3420.08 | 983.01 | 899.51 | 1.08 | 1.06 | 1786.90 | 4797.63 | CANDIDATE-RECENT |
| st.sig_delta10_s<=-26 | d15 | SPL | PE | 0.55 | 0.56 | 1.67 | 1.12 | 1.01 | 1.21 | 1.09 | 1.11 | 9.97 | 4.25 | -12.73 | 0.99 | 3742.89 | 2991.61 | 960.84 | 1460.39 | 1.21 | 1.16 | 4147.01 | 5365.76 | CANDIDATE-RECENT |
| day.afterbigday1p5pct | d5 | MKT | KB | 0.66 | 0.02 | 1.74 | 0.96 | 0.87 | 1.01 | 0.91 | 1.62 | 17.10 | 7.68 | -2.53 | 0.97 | 3416.11 | 2989.10 | 563.84 | 1073.06 | 1.01 | 0.99 | 1658.21 | 4465.50 | CANDIDATE-RECENT |
| st.prev_rng_atrd>=1.301 | d5 | SPL | KB | 0.78 | 0.10 | 2.02 | 1.26 | 0.99 | 1.33 | 1.04 | 1.86 | 34.92 | 15.68 | 1.38 | 0.93 | 3305.99 | 2617.55 | 2538.82 | 1643.68 | 1.33 | 1.29 | 2322.66 | 5876.31 | CANDIDATE-RECENT |
| evt.sweep_low.within15.ict_with | skip | MKT | london | 0.48 | 0.13 | 0.04 | 0.02 | 0.01 | 0.16 | 0.14 | 0.78 | 2.78 | 2.04 | -0.58 | 0.91 | 2771.20 | 2424.80 | 1984.05 | -315.36 | 0.16 | 0.15 | 585.18 | 95.52 | CANDIDATE-RECENT |
| st.prev_er_rth>=0.2767 | rt50 | MKT | asia | 0.70 | 0.45 | 1.01 | 0.37 | 0.26 | 0.37 | 0.26 | 1.29 | 6.24 | 5.96 | -8.87 | 0.99 | 2754.73 | 888.77 | 130.31 | -1702.78 | 0.37 | 0.37 | 1761.90 | 5316.24 | CANDIDATE-RECENT |
| st.5m.rng_exp1>=2.275 | rt50 | MKT | asia | 0.10 | 0.27 | 0.41 | 0.22 | 0.28 | 0.22 | 0.28 | 0.52 | 2.35 | 2.25 | -3.27 | 0.97 | 2665.76 | 3189.64 | -81.62 | 885.39 | 0.22 | 0.22 | -290.62 | 4402.27 | CANDIDATE-RECENT |
| st.5m.rng_exp1>=3.556 | d5 | SPL | KB | 0.42 | 0.45 | 1.28 | 0.96 | 0.88 | 1.03 | 0.93 | 1.14 | 11.93 | 5.36 | -3.06 | 0.94 | 2564.18 | 2315.43 | 1154.83 | 2297.19 | 1.03 | 1.00 | 1719.37 | 4502.72 | CANDIDATE-RECENT |
| st.prev_er_rth>=0.2767 | rt50 | SPL | asia | 0.69 | 0.39 | 0.94 | 0.33 | 0.22 | 0.34 | 0.23 | 1.21 | 6.24 | 5.96 | -8.11 | 0.99 | 2501.84 | 880.90 | 1370.77 | -2832.31 | 0.34 | 0.34 | 1621.12 | 4422.61 | CANDIDATE-RECENT |
| st.f60_vs_med>=1.809 | d15 | MKT | PE | 0.63 | 0.12 | 1.47 | 0.81 | 0.75 | 0.86 | 0.79 | 1.17 | 12.48 | 5.32 | -8.45 | 0.93 | 2450.43 | 2162.50 | 634.98 | 705.47 | 0.86 | 0.83 | 2098.63 | 3865.84 | CANDIDATE-RECENT |
| st.sig_es_nq_div5<=-0.3786 | d5 | MKT | WT | 0.19 | 0.62 | -0.12 | 0.39 | 0.32 | 0.52 | 0.40 | 0.77 | 21.04 | 12.82 | 1.35 | 0.93 | 2363.61 | 2041.66 | 331.45 | 2867.43 | 0.52 | 0.49 | 0.00 | 3368.48 | CANDIDATE-RECENT |
| st.prev_rng_atrd>=1.697 | skip | MKT | asia | 0.66 | 0.49 | 1.11 | 0.15 | 0.13 | 0.74 | 0.48 | 1.81 | 11.76 | 11.25 | -1.28 | 0.93 | 2318.71 | 2028.87 | 1214.91 | 2272.82 | 0.74 | 0.65 | -34.14 | 1796.20 | CANDIDATE-RECENT |
| evt.sweep_low.within15.ict_with | z50 | MKT | london | 0.24 | 0.06 | 0.02 | 0.01 | 0.01 | 0.08 | 0.07 | 0.39 | 2.78 | 2.04 | -0.58 | 0.91 | 2267.59 | 1984.14 | -219.77 | -9.97 | 0.08 | 0.08 | 292.59 | 47.76 | CANDIDATE-RECENT |
| st.1m.adx14<=18.87 | skip | MKT | SM | 0.85 | 0.56 | 1.18 | 1.23 | 0.58 | 1.52 | 0.94 | 2.57 | 7.32 | 0.82 | -16.86 | 0.98 | 2264.52 | 1236.92 | 1233.30 | 1066.18 | 1.52 | 1.41 | 883.57 | 2049.28 | CANDIDATE-RECENT |
| st.sig_delta10_s<=-26 | d15 | MKT | PE | 0.60 | 0.43 | 1.76 | 1.20 | 1.11 | 1.28 | 1.19 | 1.03 | 9.97 | 4.25 | -13.18 | 0.99 | 2229.73 | 1738.14 | 1047.10 | 1961.24 | 1.28 | 1.23 | 4859.65 | 5727.69 | PASS_pre_RC |
| evt.sweep_low.within15.ict_with | z25 | MKT | london | 0.36 | 0.09 | 0.03 | 0.01 | 0.01 | 0.12 | 0.10 | 0.59 | 2.78 | 2.04 | -0.58 | 0.91 | 2219.32 | 1941.90 | 1074.89 | -178.89 | 0.12 | 0.11 | 438.89 | 71.64 | CANDIDATE-RECENT |
| st.sig_delta10_s<=-26 | d5 | MKT | nyam | 0.33 | 0.42 | 1.46 | 1.07 | 1.03 | 1.25 | 1.20 | 0.86 | 19.04 | 18.93 | -0.16 | 1.00 | 2159.62 | 2077.11 | -1544.22 | 8157.35 | 1.25 | 1.19 | 5702.59 | 15952.51 | PASS_pre_RC |
| st.prev_rng_atrd>=1.697 | skip | MKT | KB | 0.80 | 0.16 | 1.36 | 0.96 | 0.88 | 1.36 | 1.14 | 1.45 | 13.05 | 5.86 | -7.39 | 0.99 | 2099.03 | 1836.65 | 1817.10 | 1151.15 | 1.36 | 1.18 | 1893.05 | 4500.22 | CANDIDATE-RECENT |
| st.1h.rng_exp1>=2.395 | d5 | SPL | nypm | 0.62 | 0.43 | 0.56 | 0.57 | 0.76 | 0.69 | 0.86 | 2.16 | 35.04 | 21.50 | 0.60 | 0.90 | 2050.41 | 1114.23 | -2210.42 | 1674.39 | 0.69 | 0.65 | 344.54 | 4739.92 | CANDIDATE-RECENT |
| st.prev_rng_atrd>=1.697 | skip | SPL | KB | 0.79 | 0.15 | 1.31 | 0.93 | 0.85 | 1.28 | 1.07 | 1.44 | 13.05 | 5.86 | -7.11 | 0.98 | 1990.19 | 1741.42 | 2079.21 | 861.79 | 1.27 | 1.10 | 1837.42 | 4329.94 | CANDIDATE-RECENT |
| st.1h.squeeze==1 | d5 | SPL | PE | 0.23 | 0.82 | 0.65 | 0.75 | 0.64 | 0.77 | 0.66 | 0.83 | 13.99 | 5.96 | 2.90 | 0.96 | 1832.63 | 511.71 | -888.15 | 2091.49 | 0.77 | 0.76 | 2832.97 | 3569.48 | CANDIDATE-RECENT |
| st.1h.squeeze==1 | d5 | MKT | PE | 0.27 | 0.80 | 0.66 | 0.73 | 0.63 | 0.75 | 0.65 | 0.81 | 13.99 | 5.96 | 3.52 | 0.95 | 1726.63 | 245.56 | 242.94 | 2129.54 | 0.75 | 0.74 | 3011.10 | 3472.84 | CANDIDATE-RECENT |
| tm.lunch.1130_1330 | skip | SPL | SM | 0.79 | 1.46 | 0.07 | 1.21 | 1.08 | 1.55 | 1.49 | 2.99 | 7.32 | 0.82 | -16.48 | 0.99 | 1642.52 | 1496.19 | 1728.75 | 1738.62 | 1.56 | 1.45 | 0.00 | 2003.59 | CANDIDATE-RECENT |

### 2c. the plain sentences for the top B cells

* Skip all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (SPL): keeps 84.4% of trades and adds +1.03 pts per contract in the last 6 months (per signal +0.36, MDE 0.93; 1522 signals touched, they earn -2.32 pts each under the base; HOLD +1.06) [POST-HOC: the 11-line set was chosen on the sign of dP(target) in all windows incl. the recent ones, ZONES-2]; stack +30,118 / +26,652 $/wk (L6M / HOLD, research lots), PRE +8,880, X' +3,150; placebo rank 1.00; tier CANDIDATE-RECENT
* Skip all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (MKT): keeps 84.4% of trades and adds +0.97 pts per contract in the last 6 months (per signal +0.31, MDE 0.95; 1522 signals touched, they earn -2.02 pts each under the base; HOLD +1.02) [POST-HOC: the 11-line set was chosen on the sign of dP(target) in all windows incl. the recent ones, ZONES-2]; stack +29,834 / +25,284 $/wk (L6M / HOLD, research lots), PRE +11,299, X' +5,714; placebo rank 1.00; tier CANDIDATE-RECENT
* Size 25% all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (SPL): changes 15.6% of trades and adds +0.74 pts per contract in the last 6 months (per signal +0.27, MDE 0.70; 1522 signals touched, they earn -2.32 pts each under the base; HOLD +0.76) [POST-HOC: the 11-line set was chosen on the sign of dP(target) in all windows incl. the recent ones, ZONES-2]; stack +24,279 / +21,156 $/wk (L6M / HOLD, research lots), PRE +6,259, X' +3,567; placebo rank 1.00; tier CANDIDATE-RECENT
* Size 25% all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (MKT): changes 15.6% of trades and adds +0.70 pts per contract in the last 6 months (per signal +0.24, MDE 0.71; 1522 signals touched, they earn -2.02 pts each under the base; HOLD +0.73) [POST-HOC: the 11-line set was chosen on the sign of dP(target) in all windows incl. the recent ones, ZONES-2]; stack +19,790 / +15,629 $/wk (L6M / HOLD, research lots), PRE +10,625, X' +6,660; placebo rank 1.00; tier CANDIDATE-RECENT
* Size 50% all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (SPL): changes 15.6% of trades and adds +0.47 pts per contract in the last 6 months (per signal +0.18, MDE 0.47; 1522 signals touched, they earn -2.32 pts each under the base; HOLD +0.48) [POST-HOC: the 11-line set was chosen on the sign of dP(target) in all windows incl. the recent ones, ZONES-2]; stack +17,517 / +14,938 $/wk (L6M / HOLD, research lots), PRE +2,222, X' +4,034; placebo rank 1.00; tier CANDIDATE-RECENT
* Size 50% all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (MKT): changes 15.6% of trades and adds +0.45 pts per contract in the last 6 months (per signal +0.16, MDE 0.48; 1522 signals touched, they earn -2.02 pts each under the base; HOLD +0.46) [POST-HOC: the 11-line set was chosen on the sign of dP(target) in all windows incl. the recent ones, ZONES-2]; stack +14,880 / +11,535 $/wk (L6M / HOLD, research lots), PRE +5,048, X' +4,576; placebo rank 1.00; tier CANDIDATE-RECENT
* Delay 15 min all signals when [TG-1 store measure f60_vs_med >=1.809] (SPL): changes 11.7% of trades and adds +0.37 pts per contract in the last 6 months (per signal +0.23, MDE 0.70; 1138 signals touched, they earn -3.05 pts each under the base; HOLD +0.32); stack +10,697 / +9,524 $/wk (L6M / HOLD, research lots), PRE +54, X' +7; placebo rank 0.99; tier CANDIDATE-RECENT
* Delay 15 min all signals when [TG-1 store measure f60_vs_med >=1.809] (MKT): changes 11.7% of trades and adds +0.32 pts per contract in the last 6 months (per signal +0.19, MDE 0.71; 1138 signals touched, they earn -2.92 pts each under the base; HOLD +0.27); stack +10,518 / +9,100 $/wk (L6M / HOLD, research lots), PRE +2,578, X' -359; placebo rank 0.99; tier CANDIDATE-RECENT
* Re-target (target x0.5) all signals when [the book's previous signal was the OPPOSITE side and fired <= 60 min ago (whipsaw / flip)] (SPL): changes 9.0% of trades and adds +0.09 pts per contract in the last 6 months (per signal +0.08, MDE 0.34; 881 signals touched, they earn -0.24 pts each under the base; HOLD +0.05); stack +7,979 / +6,973 $/wk (L6M / HOLD, research lots), PRE -4,043, X' -2,418; placebo rank 0.98; tier CANDIDATE-RECENT
* Delay 5 min all signals when [TG-1 store measure sig_vel30 (already sided) <=-3.6] (MKT): changes 11.2% of trades and adds +0.22 pts per contract in the last 6 months (per signal +0.17, MDE 0.32; 1087 signals touched, they earn +2.32 pts each under the base; HOLD +0.21); stack +7,815 / +6,307 $/wk (L6M / HOLD, research lots), PRE -7,322, X' +3,170; placebo rank 0.97; tier CANDIDATE-RECENT
* Delay 15 min HM signals when [t_since_big_against (L2EA) <= 300] (MKT): changes 18.9% of trades and adds +0.80 pts per contract in the last 6 months (per signal +0.36, MDE 1.80; 172 signals touched, they earn +1.03 pts each under the base; HOLD +0.71); stack +7,737 / +7,285 $/wk (L6M / HOLD, research lots), PRE +4,096, X' +459; placebo rank 0.97; tier CANDIDATE-RECENT
* Delay 5 min all signals when [ES move over the prior 15 s in bp, sided (<0 = ES moved the OPPOSITE way) <= -1] (SPL): changes 9.7% of trades and adds +0.19 pts per contract in the last 6 months (per signal +0.14, MDE 0.32; 947 signals touched, they earn -0.98 pts each under the base; HOLD +0.19); stack +7,480 / +6,751 $/wk (L6M / HOLD, research lots), PRE -8,878, X' +724; placebo rank 0.94; tier CANDIDATE-RECENT
* Delay 15 min HM signals when [t_since_big_against (L2EA) <= 300] (SPL): changes 18.9% of trades and adds +0.69 pts per contract in the last 6 months (per signal +0.28, MDE 1.61; 172 signals touched, they earn +1.86 pts each under the base; HOLD +0.50); stack +7,269 / +6,156 $/wk (L6M / HOLD, research lots), PRE +3,089, X' -917; placebo rank 0.96; tier CANDIDATE-RECENT
* Re-target (target x0.5) all signals when [a FRESH 11-line-set line within 20 pts ahead (the ZONES-2 skip fire)] (SPL): changes 15.6% of trades and adds +0.22 pts per contract in the last 6 months (per signal +0.21, MDE 0.75; 1522 signals touched, they earn -2.32 pts each under the base; HOLD +0.19) [POST-HOC: the 11-line set was chosen on the sign of dP(target) in all windows incl. the recent ones, ZONES-2]; stack +6,995 / +5,980 $/wk (L6M / HOLD, research lots), PRE -587, X' -5,765; placebo rank 1.00; tier CANDIDATE-RECENT

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

| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | touched/wk | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | $/wk live | $/wk res | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| st.prev_ret_rth>=0.7105 | rt50 | SPL | ALL | 0.46 | 0.24 | -0.23 | -0.11 | -0.10 | -0.10 | -0.10 | 0.64 | 10.84 | 37.71 | 3.46 | 0.70 |  |  |  |  | -0.10 | -0.10 | -19.16 | -9538.28 | DEAD |
| evt.failbrk_high.within30.ict_with | d15 | MKT | ALL | 0.06 | 0.06 | 0.03 | 0.04 | 0.02 | 0.05 | 0.03 | 0.05 | 0.24 | 0.82 | -20.51 | 0.98 | 952.20 | 710.94 | 1142.03 | 1182.45 | 0.05 | 0.05 | 571.63 | 2086.70 | CANDIDATE-RECENT |
| tm.rel.R830.pre30 | d15 | SPL | ALL | 0.07 | 0.05 | 0.03 | -0.02 | -0.02 | -0.02 | -0.02 | 0.07 | 0.59 | 2.04 | 8.23 | 0.36 |  |  |  |  | -0.02 | -0.02 | 477.39 | -1893.46 | DEAD |
| px.ext.5m.ema20<=-1 | d5 | MKT | ALL | 0.02 | 0.00 | 0.01 | 0.02 | 0.02 | 0.02 | 0.02 | 0.03 | 0.33 | 1.14 | 11.89 | 0.79 |  |  |  |  | 0.02 | 0.02 | 355.72 | 898.13 | LEAD |
| aft.stackday_R_q20 | rt50 | MKT | ALL | 0.38 | 0.17 | -0.72 | -0.76 | -0.49 | -0.76 | -0.49 | 1.17 | 22.45 | 78.11 | 5.65 | 0.00 |  |  |  |  | -0.76 | -0.76 | -10276.66 | -44010.60 | DEAD |
| st.5m.squeeze==1 | rt50 | SPL | ALL | 0.18 | 0.29 | 0.24 | 0.19 | 0.11 | 0.20 | 0.12 | 0.59 | 12.05 | 41.93 | -1.96 | 1.00 | -3027.08 | -2273.21 | 2678.58 | -278.16 | 0.20 | 0.20 | 3739.51 | 9189.42 | CANDIDATE-RECENT |
| st.sig_intens_rel>=2.182 | d15 | MKT | ALL | 0.08 | 0.48 | -0.09 | -0.18 | -0.08 | 0.16 | 0.18 | 0.85 | 29.34 | 102.07 | 1.93 | 0.80 |  |  |  |  | 0.16 | 0.15 | 1206.90 | -12249.15 | DEAD |
| st.ret_RTY_15m>=30.98 | rt50 | SPL | ALL | 0.15 | 0.15 | -0.23 | -0.23 | -0.19 | -0.23 | -0.18 | 0.38 | 6.79 | 23.61 | 3.78 | 0.02 |  |  |  |  | -0.23 | -0.23 | -3271.65 | -12275.93 | DEAD |
| day.afterbigday1p5pct | d5 | SPL | ALL | 0.16 | 0.04 | 0.27 | 0.13 | 0.12 | 0.22 | 0.18 | 0.51 | 16.43 | 57.14 | 3.41 | 0.88 |  |  |  |  | 0.22 | 0.22 | 1774.64 | 4259.93 | LEAD |
| eng.opp_flip_within30 | rt50 | SPL | ALL | 0.05 | 0.04 | -0.11 | -0.06 | -0.07 | -0.06 | -0.07 | 0.19 | 3.96 | 13.79 | 1.15 | 0.40 |  |  |  |  | -0.06 | -0.06 | -870.23 | -1477.00 | DEAD |
| vol.r60_pts>=20 | rt50 | MKT | ALL | 0.04 | 0.18 | -0.04 | -0.06 | -0.03 | -0.06 | -0.03 | 0.88 | 30.04 | 104.50 | 1.09 | 0.91 |  |  |  |  | -0.06 | -0.06 | -3168.78 | -1642.37 | DEAD |

Per book (best selected B cell by PRE u X' z within the book scope):

| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | touched/wk | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | $/wk live | $/wk res | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| st.es_nq_open30_agree==-1 | d5 | MKT | MA | 0.43 | 0.40 | -0.31 | -0.11 | -0.08 | -0.11 | -0.08 | 1.16 | 9.09 | 1.32 | 4.02 | 0.57 |  |  |  |  | -0.11 | -0.11 | 0.00 | -328.68 | DEAD |
| st.prev_ret_rth>=0.7105 | z25 | SPL | ST | 0.51 | 0.77 | -0.80 | -0.72 | -0.65 | -0.35 | -0.39 | 1.13 | 12.26 | 5.50 | 7.83 | 0.20 |  |  |  |  | -0.35 | -0.32 | 0.00 | -6461.03 | DEAD |
| st.prev_ret_rth>=0.7105 | z50 | SPL | ST | 0.34 | 0.51 | -0.53 | -0.48 | -0.44 | -0.23 | -0.26 | 0.76 | 12.26 | 5.50 | 7.83 | 0.20 |  |  |  |  | -0.23 | -0.21 | 0.00 | -4307.36 | DEAD |
| aft.book_winner_within10 | d15 | MKT | HM | 0.76 | 0.57 | -0.99 | -0.99 | -0.65 | -0.86 | -0.55 | 1.35 | 10.56 | 3.43 | 14.23 | 0.07 |  |  |  |  | -0.86 | -0.83 | -727.66 | -6424.43 | DEAD |
| st.prev_er_rth>=0.1843 | rt50 | SPL | KB | 1.00 | 1.35 | 0.90 | 0.39 | 0.30 | 0.40 | 0.30 | 1.45 | 24.82 | 11.14 | -0.84 | 0.94 | -1890.21 | -1681.50 | -1086.69 | 2130.77 | 0.40 | 0.39 | 759.42 | 1818.86 | CANDIDATE-RECENT |
| st.prev_ret_rth>=0.7105 | skip | SPL | MV | 0.66 | 1.10 | -0.56 | -0.26 | -0.24 | 0.00 | -0.09 | 1.86 | 11.49 | 4.64 | 2.27 | 0.46 |  |  |  |  | 0.00 | 0.00 | -574.28 | -2111.00 | DEAD |
| st.prev_ret_rth>=0.7105 | z25 | SPL | MV | 0.50 | 0.82 | -0.42 | -0.20 | -0.18 | 0.00 | -0.06 | 1.39 | 11.49 | 4.64 | 2.27 | 0.46 |  |  |  |  | 0.00 | 0.00 | -430.71 | -1583.25 | DEAD |
| st.rv30m_vs_med20d>=4.318 | d5 | MKT | PB | 0.55 | 0.36 | 0.65 | 0.25 | 0.15 | 0.44 | 0.29 | 1.23 | 9.01 | 2.79 | -0.75 | 0.65 |  |  |  |  | 0.44 | 0.43 | 154.42 | 1544.24 | LEAD |
| px.ext.5m.ema200>=8 | d5 | MKT | PB | 0.52 | 0.05 | 0.74 | 0.26 | 0.24 | 0.26 | 0.24 | 0.82 | 12.47 | 3.86 | 13.06 | 0.90 | 0.00 | 0.00 | 0.00 | 0.00 | 0.26 | 0.26 | 163.58 | 1635.79 | CANDIDATE-RECENT |
| st.prev_close_loc>=0.4225 | d15 | MKT | MA | 0.81 | 0.55 | -0.85 | -0.98 | -0.84 | -0.90 | -0.79 | 0.98 | 5.65 | 0.82 | 10.11 | 0.10 |  |  |  |  | -0.90 | -0.88 | 0.00 | -2853.91 | DEAD |
| aft.book_winner_within10 | d15 | SPL | HM | 0.72 | 0.53 | -0.86 | -0.93 | -0.58 | -0.81 | -0.48 | 1.30 | 10.56 | 3.43 | 13.60 | 0.06 |  |  |  |  | -0.81 | -0.78 | -717.00 | -6017.37 | DEAD |
| st.prev_rng_atrd>=1.697 | rt50 | SPL | KB | 0.92 | 0.30 | 0.77 | 0.51 | 0.47 | 0.52 | 0.47 | 1.29 | 13.05 | 5.86 | -7.11 | 0.96 | 997.06 | 872.43 | 1361.93 | 977.88 | 0.52 | 0.52 | 934.45 | 2394.21 | CANDIDATE-RECENT |
| stk.same_lots_res>=60 | d15 | MKT | DN | 0.43 | 0.62 | -0.30 | -0.48 | -0.20 | -0.46 | -0.19 | 0.81 | 4.71 | 1.18 | 9.83 | 0.26 |  |  |  |  | -0.46 | -0.46 | 0.00 | -2405.65 | DEAD |
| st.5m.squeeze==1 | rt50 | MKT | PE | 0.55 | 0.49 | 0.34 | 0.38 | 0.32 | 0.38 | 0.32 | 1.36 | 9.13 | 3.89 | -3.94 | 0.94 | -171.82 | -373.16 | 1121.29 | 2143.06 | 0.38 | 0.38 | 3049.62 | 1815.74 | CANDIDATE-RECENT |
| st.5m.chop14>=53.83 | d15 | MKT | SM | 0.99 | 1.07 | -1.00 | -0.93 | -0.77 | -0.91 | -0.73 | 2.59 | 14.01 | 1.57 | 1.58 | 0.17 |  |  |  |  | -0.91 | -0.89 | -823.62 | -1547.55 | DEAD |
| xm.es_minus_nq30s<=-1.5 | d5 | MKT | SM | 1.08 | 0.40 | -0.54 | -0.46 | -0.06 | -0.44 | -0.04 | 1.26 | 4.14 | 0.46 | 13.22 | 0.16 |  |  |  |  | -0.44 | -0.44 | 7.14 | -757.24 | DEAD |
| stk.same_lots_res>=60 | d15 | SPL | DN | 0.44 | 0.46 | -0.31 | -0.42 | -0.15 | -0.41 | -0.14 | 0.75 | 4.71 | 1.18 | 9.29 | 0.27 |  |  |  |  | -0.41 | -0.41 | 0.00 | -2107.69 | DEAD |
| st.sig_delta10_s<=-26 | d5 | MKT | PE | 0.65 | 0.30 | 1.05 | 0.76 | 0.68 | 0.79 | 0.71 | 0.83 | 9.97 | 4.25 | -13.18 | 0.99 | 1031.90 | 557.96 | 699.08 | 3193.17 | 0.79 | 0.78 | 2971.06 | 3645.84 | CANDIDATE-RECENT |
| bk.imb10_run<=-10 | d5 | SPL | WT | 0.12 | 0.05 | -0.15 | -0.00 | -0.00 | 0.01 | 0.00 | 0.31 | 4.34 | 2.64 | -1.72 | 0.54 |  |  |  |  | 0.01 | 0.01 | 0.00 | -11.05 | DEAD |
| st.15m.macd_hist>=0.4146 | d5 | MKT | WT | 0.15 | 0.64 | 0.11 | 0.07 | 0.05 | 0.10 | 0.07 | 0.58 | 8.38 | 5.11 | -2.52 | 0.62 |  |  |  |  | 0.10 | 0.10 | 0.00 | 560.62 | LEAD |

## 5. Section D - the opposite side: take-only / size-up where the map shows a higher P(target) (STRUCTURE: lots rise; compare uex and eqr, not the raw gain)

218 size-up / take-only cell-scopes are CANDIDATE-RECENT or better with a positive stack; pooled u200 / MKT cells ranked by stack, with the lot-matched controls and the PRE / X' stack signs (the X' stack is negative for several - the rule is not consistent in 2023-24):

| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | touched/wk | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | $/wk live | $/wk res | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| st.1m.rng_exp1<=0.7 | u200 | MKT | ALL | 0.26 | 0.20 | 0.76 | 0.66 | 0.48 | 0.27 | 0.18 | 0.68 | 10.94 | 38.07 | 6.00 | 0.93 | 25014.67 | 18958.90 | -95.20 | 920.58 | 0.27 | 0.30 | 9056.39 | 38150.39 | CANDIDATE-RECENT |
| st.1m.rng_exp1<=0.9489 | u200 | MKT | ALL | 0.58 | 0.26 | 1.45 | 1.69 | 1.31 | 0.66 | 0.51 | 1.41 | 26.44 | 92 | 6.39 | 0.99 | 24103.12 | 16988.69 | 8685.06 | -4220.93 | 0.66 | 0.83 | 14064.69 | 106271.63 | CANDIDATE-RECENT |
| st.15m.er20<=0.0408 | u200 | MKT | ALL | 0.41 | 0.12 | 0.51 | 0.62 | 0.58 | 0.26 | 0.28 | 0.66 | 10.36 | 36.04 | 5.99 | 0.94 | 18583.88 | 16779.66 | 3556.33 | -3792.61 | 0.26 | 0.28 | 4014.22 | 39252.18 | CANDIDATE-RECENT |
| px.ext.5m.ema200>=8 | u200 | MKT | ALL | 0.68 | 0.85 | 0.01 | 0.87 | 0.75 | 0.44 | 0.42 | 1.30 | 11.67 | 40.61 | 7.43 | 0.99 | 18473.66 | 14518.04 | -5265.84 | 11902.13 | 0.44 | 0.49 | 9640.42 | 51794.38 | CANDIDATE-RECENT |
| px.loc.DEAL4H.premium | u200 | MKT | ALL | 1.13 | 1.23 | 0.71 | 2.24 | 1.67 | 0.42 | 0.27 | 2.64 | 49.80 | 173.25 | 4.50 | 0.99 | 14787.67 | 10073.69 | 3255.36 | 13137.75 | 0.42 | 0.62 | 17207.28 | 140179.87 | CANDIDATE-RECENT |
| px.loc.OR30.sidedloc>=0.8 | u200 | MKT | ALL | 0.84 | 1.33 | 0.56 | 1.58 | 1.33 | 0.30 | 0.30 | 2.29 | 35.95 | 125.07 | 4.39 | 1.00 | 14389.24 | 14590.47 | 8124.07 | -2967.04 | 0.30 | 0.41 | 15761.84 | 97326.90 | CANDIDATE-RECENT |
| st.15m.er20<=0.105 | u200 | MKT | ALL | 0.64 | 0.17 | 0.72 | 1.25 | 1.07 | 0.34 | 0.32 | 0.95 | 25.41 | 88.39 | 4.91 | 0.96 | 14138.10 | 13628.76 | 8856.82 | -9739.78 | 0.34 | 0.42 | 8471.62 | 80180.98 | PASS_pre_RC |
| st.1h.range_pos60>=0.3562 | u200 | MKT | ALL | 1.22 | 0.84 | 0.25 | 1.15 | 0.89 | 0.27 | 0.22 | 1.99 | 25.14 | 87.46 | 4.57 | 0.94 | 14041.84 | 10698.23 | 11239.20 | 19085.41 | 0.27 | 0.33 | 8466.49 | 71542.25 | CANDIDATE-RECENT |
| st.sig_es_nq_div5>=0.6062 | u200 | MKT | ALL | 0.41 | 0.23 | 0.38 | 0.45 | 0.48 | 0.21 | 0.28 | 0.49 | 6.95 | 24.18 | 6.52 | 0.93 | 11463.82 | 11094.23 | 423.08 | -4668.32 | 0.21 | 0.23 | 7054.45 | 30334.08 | CANDIDATE-RECENT |
| px.loc.OR30.premium | u200 | MKT | ALL | 0.89 | 1.31 | 0.34 | 1.46 | 1.16 | 0.11 | 0.09 | 2.30 | 40.24 | 140 | 3.63 | 0.95 | 11199.42 | 11568.65 | 6979.53 | -6326.31 | 0.11 | 0.15 | 14561.67 | 90950.18 | CANDIDATE-RECENT |
| px.ext.1m.ema200>=8 | u200 | MKT | ALL | 0.62 | 0.56 | 1.07 | 1.20 | 1.16 | 0.72 | 0.76 | 0.84 | 12.09 | 42.07 | 9.90 | 1.00 | 11105.52 | 11476.77 | -4027.42 | -12804.11 | 0.72 | 0.80 | 8025.73 | 74316.63 | PASS_pre_RC |
| px.loc.PDR.outside | u200 | MKT | ALL | 0.81 | 0.37 | 0.47 | 1.38 | 1.12 | 0.21 | 0.20 | 2.01 | 33.95 | 118.11 | 4.07 | 0.92 | 11090.59 | 7414.72 | -13926.45 | 18016.97 | 0.21 | 0.28 | 12404.14 | 84977.21 | CANDIDATE-RECENT |
| px.ext.1m.ema200>=5 | u200 | MKT | ALL | 0.78 | 0.81 | 2.37 | 3.02 | 2.62 | 1.21 | 1.12 | 1.95 | 40.79 | 141.89 | 7.41 | 1.00 | 8816.37 | 11779.17 | 12770.88 | -12785.42 | 1.21 | 1.70 | 29586.53 | 181759.73 | PASS_pre_RC |
| bk.vpin50>=0.2 | u200 | MKT | ALL | 0.54 | 0.47 | 0.92 | 0.78 | 0.65 | 0.35 | 0.32 | 0.92 | 11.87 | 41.29 | 6.55 | 0.99 | 8463.61 | 6250.59 | 3164.18 | 2515.71 | 0.35 | 0.39 | 8623.99 | 46859.58 | CANDIDATE-RECENT |
| st.15m.hma_slope>=0.4067 | u200 | MKT | ALL | 0.68 | 0.39 | 1.07 | 1.45 | 1.16 | 0.58 | 0.47 | 1.46 | 22.88 | 79.61 | 6.34 | 1.00 | 8214.69 | 7760.67 | -3201.76 | 19095.54 | 0.58 | 0.71 | 15009.75 | 86869.07 | CANDIDATE-RECENT |

Take-only (keep ONLY the signals inside the state, skip the rest), selected on PRE u X':
| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | touched/wk | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | $/wk live | $/wk res | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| cal.weekend_gap>=20 | keeponly | SPL | ALL | 0.16 | 0.35 | -0.26 | -0.21 | -0.19 | -0.15 | -0.14 | 0.42 | 1.94 | 6.75 | 10.86 | 1.00 |  |  |  |  | -0.15 | -0.15 | -3738.90 | -12256.71 | DEAD |
| cal.weekend_gap>=20 | keeponly | MKT | ALL | 0.17 | 0.39 | -0.27 | -0.22 | -0.20 | -0.16 | -0.15 | 0.43 | 1.94 | 6.75 | 11.11 | 1.00 |  |  |  |  | -0.16 | -0.15 | -3767.95 | -12579.25 | DEAD |
| cal.weekend_gap>=40 | keeponly | SPL | ALL | 0.10 | 0.36 | -0.60 | -0.51 | -0.46 | -0.42 | -0.39 | 0.62 | 3.05 | 10.61 | 16.60 | 1.00 |  |  |  |  | -0.42 | -0.41 | -6374.45 | -29959.86 | DEAD |
| cal.weekend_gap>=40 | keeponly | MKT | ALL | 0.11 | 0.41 | -0.61 | -0.51 | -0.46 | -0.42 | -0.40 | 0.63 | 3.05 | 10.61 | 16.63 | 1.00 |  |  |  |  | -0.42 | -0.41 | -6522.15 | -29829.07 | DEAD |

Both edges per state (map file DS3_NO_TRADE_MAP_2.md section 9) show the same states: the higher-P(target) states are trend-continuation (extension / chase / premium location / ER high / trend-agreement), the lower-P states are their mirror, i.e. the no-trade map and the size-up map are ONE continuum (trend strength), not two independent findings.

## 6. Section C1 - combinations (pairs, triples, any-of-k, four-legged, nested with the 8-line set, per-book pairs)

1600 selected combination cell-scopes carried (1,491 masks x 6 actions x 2 bases scored on PRE u X'); mean gain per signal PRE / X' +0.311 / +0.324, L6M / HOLD -0.113 / -0.101; >= 0 in both: 641; CANDIDATE-RECENT 295; PASS_pre_RC 0.

* RC C|MKT: 300 cells, White RC best-cell p L6M 0.692 / HOLD 0.686; Sidak-cumulative 1.000; Romano-Wolf survivors 0 / 0; PBO 0.81
* RC C|SPL: 300 cells, White RC best-cell p L6M 0.676 / HOLD 0.674; Sidak-cumulative 1.000; Romano-Wolf survivors 0 / 0; PBO 0.81
* pairs: 371 selected cell-scopes; mean L6M -0.101, HOLD -0.095; >= 0 both 146; tier>=CAND 69
* triples: 173 selected cell-scopes; mean L6M -0.207, HOLD -0.193; >= 0 both 56; tier>=CAND 23
* any-of-k: 196 selected cell-scopes; mean L6M -0.157, HOLD -0.114; >= 0 both 78; tier>=CAND 20
* four-legged: 0 selected cell-scopes; mean L6M +nan, HOLD +nan; >= 0 both 0; tier>=CAND 0
* nested with set8 / set11: 136 selected cell-scopes; mean L6M -0.085, HOLD -0.086; >= 0 both 34; tier>=CAND 2
* per-book pairs: 724 selected cell-scopes; mean L6M -0.089, HOLD -0.081; >= 0 both 327; tier>=CAND 181

Best combination cells (tier >= CANDIDATE-RECENT, by L6M gain; stack where computed):
| rule | action | base | scope | PRE | X | L3M | L6M | HOLD | pc L6M | pc HOLD | MDE L6M | fire% | touched/wk | skipped pts | plc | stack L6M | stack HOLD | stack PRE | stack X | eqr L6M | uex L6M | $/wk live | $/wk res | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | rt50 | MKT | SM | 0.23 | 0.44 | 1.65 | 1.36 | 1.17 | 1.36 | 1.17 | 2.04 | 4.14 | 0.46 | -20.13 | 0.98 | 1548.96 | 1355.34 | 212.33 | 525.28 | 1.36 | 1.36 | 868.69 | 2252.03 | CANDIDATE-RECENT |
| ANY4of30 | d15 | SPL | SM | 0.52 | 0.82 | 1.89 | 1.30 | 1.48 | 1.40 | 1.60 | 2.54 | 11.15 | 1.25 | -5.41 | 0.95 | 2850.95 | 3071.14 | 906.32 | 1372.99 | 1.40 | 1.37 | -52.56 | 2152.49 | CANDIDATE-RECENT |
| ANY4of30 | d15 | MKT | SM | 0.34 | 1.06 | 1.88 | 1.29 | 1.47 | 1.38 | 1.57 | 2.63 | 11.15 | 1.25 | -5.45 | 0.96 | 2775.93 | 2995.78 | 587.31 | 1227.88 | 1.38 | 1.34 | 2.14 | 2144.70 | CANDIDATE-RECENT |
| ANY3of30 | d15 | SPL | SM | 0.78 | 1.14 | 2.43 | 1.28 | 1.13 | 1.54 | 1.43 | 3.80 | 27.07 | 3.04 | -5.25 | 0.97 | 3417.87 | 3039.58 | 1423.77 | 1512.35 | 1.55 | 1.46 | 284.60 | 2119.31 | CANDIDATE-RECENT |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | d15 | MKT | SM | 0.42 | 0.45 | 1.58 | 1.22 | 1.06 | 1.25 | 1.09 | 1.82 | 4.14 | 0.46 | -20.13 | 1.00 | 1441.78 | 1261.56 | 663.43 | 692.54 | 1.25 | 1.24 | 797.20 | 2031.16 | CANDIDATE-RECENT |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | d15 | SPL | SM | 0.37 | 0.37 | 2.12 | 1.12 | 0.97 | 1.15 | 1.01 | 2.24 | 4.14 | 0.46 | -10.38 | 1.00 | 1279.03 | 1119.15 | 327.57 | 881.78 | 1.16 | 1.15 | 706.26 | 1862.57 | CANDIDATE-RECENT |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301&st.days_since_t | d15 | SPL | SM | 0.19 | 0.17 | 2.12 | 1.12 | 0.97 | 1.15 | 1.01 | 2.24 | 3.82 | 0.43 | -16.29 | 1.00 | 1278.28 | 1118.49 | 119.24 | 469.26 | 1.16 | 1.15 | 705.82 | 1861.76 | CANDIDATE-RECENT |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | skip | MKT | MA | 0.99 | 0.52 | 1.13 | 1.06 | 0.90 | 1.32 | 1.11 | 1.60 | 3.19 | 0.46 | -33.33 | 1.00 | 0.00 | 0.00 | 0.00 | 0.00 | 1.32 | 1.28 | 0.00 | 3094.61 | CANDIDATE-RECENT |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301] | d15 | SPL | SM | 0.56 | 0.18 | 1.96 | 1.03 | 0.89 | 1.11 | 0.98 | 2.22 | 5.73 | 0.64 | -4.12 | 1.00 | 1777.24 | 1555.09 | 257.33 | 477.91 | 1.11 | 1.09 | 804.30 | 1716.92 | CANDIDATE-RECENT |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | rt50 | SPL | SM | 0.18 | 0.38 | 1.54 | 0.91 | 0.79 | 0.92 | 0.80 | 1.97 | 4.14 | 0.46 | -10.38 | 0.94 | 829.87 | 726.14 | -115.20 | 624.25 | 0.92 | 0.92 | 498.17 | 1517.78 | CANDIDATE-RECENT |
| ANY2of10[evt.failbrk_high.within30.ict_with,st.prev_ret_rth>=0.7105,st | skip | MKT | KB | 1.15 | 1.73 | 1.36 | 0.85 | 0.81 | 1.43 | 1.22 | 1.91 | 18.93 | 8.50 | -4.48 | 0.97 | 2695.51 | 2273.34 | 412.67 | 4226.84 | 1.43 | 1.16 | 1681.20 | 3960.51 | CANDIDATE-RECENT |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301&st.days_since_t | d15 | MKT | SM | 0.22 | 0.20 | 1.58 | 0.84 | 0.73 | 0.86 | 0.75 | 1.53 | 3.82 | 0.43 | -16.71 | 0.99 | 824.36 | 721.32 | 419.70 | 291.42 | 0.86 | 0.85 | 451.46 | 1391.54 | CANDIDATE-RECENT |
| ANY2of10[evt.failbrk_high.within30.ict_with,st.prev_ret_rth>=0.7105,st | d15 | SPL | SM | 0.69 | 1.16 | 2.02 | 0.83 | 0.72 | 0.94 | 0.85 | 3.40 | 15.29 | 1.71 | 2.51 | 0.96 | 2006.54 | 1757.75 | 560.38 | 1839.91 | 0.95 | 0.92 | 844.97 | 1382.56 | CANDIDATE-RECENT |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | z25 | MKT | MA | 0.74 | 0.39 | 0.85 | 0.80 | 0.68 | 0.98 | 0.82 | 1.20 | 3.19 | 0.46 | -33.33 | 1.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.98 | 0.96 | 0.00 | 2320.96 | CANDIDATE-RECENT |
| ANY2of10[evt.failbrk_high.within30.ict_with,st.prev_ret_rth>=0.7105,st | skip | SPL | KB | 1.05 | 1.84 | 1.27 | 0.77 | 0.73 | 1.27 | 1.07 | 1.99 | 18.93 | 8.50 | -4.08 | 0.95 | 250.71 | 450.80 | 1023.99 | 4662.51 | 1.27 | 1.03 | 1531.86 | 3608.85 | CANDIDATE-RECENT |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301] | d15 | MKT | SM | 0.59 | 0.21 | 1.44 | 0.76 | 0.66 | 0.81 | 0.72 | 1.50 | 5.73 | 0.64 | -4.66 | 0.97 | 1327.83 | 1161.86 | 550.07 | 299.83 | 0.81 | 0.80 | 552.87 | 1263.29 | CANDIDATE-RECENT |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | skip | SPL | MA | 0.96 | 0.52 | 0.56 | 0.75 | 0.63 | 0.99 | 0.82 | 1.17 | 3.19 | 0.46 | -23.56 | 1.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.99 | 0.96 | 0.00 | 2187.86 | CANDIDATE-RECENT |
| ANY3of30 | skip | SPL | MV | 1.14 | 3.08 | 0.75 | 0.69 | 0.56 | 1.86 | 1.34 | 1.71 | 28.47 | 11.50 | -2.42 | 0.94 | 0.00 | 0.00 | 0.00 | 0.00 | 1.87 | 1.34 | -1012.70 | 5570.93 | CANDIDATE-RECENT |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | skip | SPL | KB | 1.06 | 0.96 | 0.98 | 0.67 | 0.62 | 1.05 | 0.85 | 1.59 | 15.67 | 7.04 | -4.30 | 0.95 | 1697.47 | 1485.28 | 1096.87 | 2841.15 | 1.05 | 0.88 | 1383.44 | 3147.06 | CANDIDATE-RECENT |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | rt50 | MKT | KB | 0.71 | 1.02 | 0.90 | 0.67 | 0.62 | 0.67 | 0.62 | 1.03 | 15.67 | 7.04 | -4.25 | 0.99 | 951.02 | 832.15 | -980.10 | 2295.45 | 0.67 | 0.67 | 1293.75 | 3144.64 | CANDIDATE-RECENT |

| combo | act | base | scope | z_combo | z_best_leg | legs_found | L6M_combo |
|--|--|--|--|--|--|--|--|
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | rt50 | MKT | SM | 1.06 | 1.14 | 2 | 1.36 |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | d15 | MKT | SM | 1.84 | 1.49 | 2 | 1.22 |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | d15 | SPL | SM | 1.54 | 1.45 | 2 | 1.12 |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301&st.days_since_t | d15 | SPL | SM | 0.91 | 1.45 | 3 | 1.12 |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | skip | MKT | MA | 2.76 | 2.36 | 2 | 1.06 |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301] | d15 | SPL | SM | 1.75 | 1.36 | 2 | 1.03 |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | rt50 | SPL | SM | 0.97 | 1.02 | 2 | 0.91 |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301&st.days_since_t | d15 | MKT | SM | 1.10 | 1.49 | 3 | 0.84 |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | z25 | MKT | MA | 2.76 | 2.36 | 2 | 0.80 |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301] | d15 | MKT | SM | 1.88 | 1.49 | 2 | 0.76 |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | skip | SPL | MA | 2.66 | 2.38 | 2 | 0.75 |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | skip | SPL | KB | 2.98 | 2.89 | 2 | 0.67 |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | rt50 | MKT | KB | 3.11 | 2.85 | 2 | 0.67 |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | rt50 | SPL | KB | 3.14 | 3.37 | 2 | 0.67 |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | skip | MKT | KB | 3.10 | 2.87 | 2 | 0.67 |
| BOOKPAIR[KB][st.prev_trend_day==1&st.prev_er_rth>=0.2767] | skip | MKT | KB | 2.78 | 2.67 | 2 | 0.63 |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_er_rth>=0.2767] | skip | SPL | PE | 2.25 | 1.88 | 2 | 0.60 |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_er_rth>=0.2767&st.days_since_tr | skip | SPL | PE | 2.25 | 1.88 | 3 | 0.60 |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_er_rth>=0.2767] | skip | MKT | PE | 2.60 | 2.03 | 2 | 0.57 |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_er_rth>=0.2767&st.days_since_tr | skip | MKT | PE | 2.60 | 2.03 | 3 | 0.57 |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | z25 | SPL | MA | 2.66 | 2.38 | 2 | 0.56 |
| PAIR[st.prev_rng_atrd>=1.301&st.days_since_trend<=1] | d15 | SPL | SM | 1.70 | 1.45 | 2 | 0.56 |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&xm.es_minus_nq60s<=-1.5] | d15 | SPL | MA | 1.76 | 2.24 | 2 | 0.55 |
| PAIR[set.ahead20_set11_fresh&st.days_since_trend<=1] | d15 | MKT | pre | 2.91 | 1.23 | 2 | 0.54 |
| BOOKPAIR[MA][st.rv1m_vs_med20d>=5.811&st.sig_intens_rel>=2.182] | z50 | MKT | MA | 2.76 | 2.36 | 2 | 0.53 |

## 7. Section C2 - the learned no-trade model (walk-forward LightGBM; no selection step, so the whole chain is the forward-facing answer)

Features: all 655 states + book, session, side, target / stop distance, minute of day, weekday (663 columns). Target: the signal reaches its target (market base). Re-fit every week on the trailing window of trades CLOSED before the re-fit: P3 = 3 months pooled, P12 = 12 months pooled, PB12 = 12 months per book; predictions are for the following week only (135 weeks, 2023-07 to 2026-02). Policies use the 20th / 33rd percentile of the previous 13 weeks of OUT-OF-SAMPLE predictions as the threshold (per book for PB12). Placebo: the same pipeline trained on label-shuffled data (6 draws). A second target (regression of the N-basis net pts, P12) is reported after.

OOS skill by window (AUC of P(target); IC = rank correlation of the prediction with the signal's N-basis pts; Brier vs unconditional; calibration slope of the decile curve, 1.0 = calibrated):
| variant | win | n | auc | ic_pts | brier | brier_unc | mean_pred | base_rate | slope_dec |
|--|--|--|--|--|--|--|--|--|--|
| P3_0 | PRE | 24644 | 0.5186 | 0.0004 | 0.2680 | 0.2497 | 0.4926 | 0.5159 | 0.1104 |
| P3_0 | X | 6342 | 0.5217 | -0.0292 | 0.2716 | 0.2499 | 0.4546 | 0.4901 | 0.1145 |
| P3_0 | HOLD | 10803 | 0.4862 | -0.0602 | 0.2760 | 0.2496 | 0.4945 | 0.5200 | -0.0652 |
| P3_0 | L6M | 9741 | 0.4842 | -0.0603 | 0.2750 | 0.2491 | 0.5029 | 0.5295 | -0.0841 |
| P3_0 | L3M | 5518 | 0.4950 | -0.0287 | 0.2676 | 0.2495 | 0.5333 | 0.5234 | -0.0135 |
| P3_0 | Y26 | 2229 | 0.5067 | -0.0254 | 0.2621 | 0.2478 | 0.5348 | 0.5464 | 0.0744 |
| P12_0 | PRE | 24644 | 0.5371 | 0.0104 | 0.2533 | 0.2497 | 0.4934 | 0.5159 | 0.3366 |
| P12_0 | X | 6342 | 0.5428 | -0.0052 | 0.2605 | 0.2499 | 0.4502 | 0.4901 | 0.2666 |
| P12_0 | HOLD | 10803 | 0.5280 | -0.0144 | 0.2527 | 0.2496 | 0.5111 | 0.5200 | 0.2958 |
| P12_0 | L6M | 9741 | 0.5249 | -0.0166 | 0.2525 | 0.2491 | 0.5154 | 0.5295 | 0.2800 |
| P12_0 | L3M | 5518 | 0.5238 | -0.0006 | 0.2524 | 0.2495 | 0.5226 | 0.5234 | 0.2810 |
| P12_0 | Y26 | 2229 | 0.5373 | 0.0086 | 0.2497 | 0.2478 | 0.5141 | 0.5464 | 0.4074 |
| PB12_0 | PRE | 24644 | 0.5293 | 0.0085 | 0.2594 | 0.2497 | 0.5035 | 0.5159 | 0.2044 |
| PB12_0 | X | 4745 | 0.5452 | -0.0075 | 0.2588 | 0.2500 | 0.4731 | 0.4938 | 0.2783 |
| PB12_0 | HOLD | 10803 | 0.5163 | -0.0221 | 0.2601 | 0.2496 | 0.5167 | 0.5200 | 0.1346 |
| PB12_0 | L6M | 9741 | 0.5155 | -0.0224 | 0.2597 | 0.2491 | 0.5191 | 0.5295 | 0.1313 |
| PB12_0 | L3M | 5518 | 0.5154 | -0.0121 | 0.2595 | 0.2495 | 0.5241 | 0.5234 | 0.1071 |
| PB12_0 | Y26 | 2229 | 0.5235 | -0.0080 | 0.2571 | 0.2478 | 0.5231 | 0.5464 | 0.1627 |

Calibration curve, P12 (deciles of the predicted P(target) vs the realised rate; PRE and L6M):
| decile | predicted_P12_0_L6M | predicted_P12_0_PRE | realised_P12_0_L6M | realised_P12_0_PRE |
|--|--|--|--|--|
| 1 | 0.356 | 0.308 | 0.471 | 0.439 |
| 2 | 0.426 | 0.389 | 0.500 | 0.491 |
| 3 | 0.460 | 0.428 | 0.541 | 0.496 |
| 4 | 0.486 | 0.459 | 0.531 | 0.500 |
| 5 | 0.509 | 0.485 | 0.539 | 0.521 |
| 6 | 0.532 | 0.511 | 0.520 | 0.536 |
| 7 | 0.553 | 0.536 | 0.521 | 0.537 |
| 8 | 0.575 | 0.564 | 0.566 | 0.522 |
| 9 | 0.603 | 0.597 | 0.535 | 0.549 |
| 10 | 0.653 | 0.657 | 0.573 | 0.568 |

Policy gain per signal (market base, N basis; pooled; negative = the policy loses money relative to taking every signal):
| variant | policy | PRE | X | HOLD | L6M | L3M | Y26 |
|--|--|--|--|--|--|--|--|
| P12_0 | half_bottom33 | -0.059 | -0.171 | -0.488 | -0.638 | -0.511 | -0.885 |
| P12_0 | skip20_half20_40 | -0.165 | -0.292 | -0.839 | -1.060 | -0.869 | -1.474 |
| P12_0 | skip_bottom20 | -0.203 | -0.233 | -0.629 | -0.811 | -0.772 | -1.202 |
| P12_0 | skip_bottom33 | -0.117 | -0.343 | -0.976 | -1.276 | -1.022 | -1.769 |
| P3_0 | half_bottom33 | -0.263 | -0.256 | -1.093 | -1.131 | -0.646 | -0.802 |
| P3_0 | skip20_half20_40 | -0.483 | -0.462 | -1.976 | -2.040 | -1.226 | -1.700 |
| P3_0 | skip_bottom20 | -0.436 | -0.519 | -1.250 | -1.214 | -0.482 | -0.978 |
| P3_0 | skip_bottom33 | -0.526 | -0.512 | -2.187 | -2.261 | -1.291 | -1.605 |
| PB12_0 | half_bottom33 | -0.197 | -0.215 | -0.600 | -0.647 | -0.387 | -0.489 |
| PB12_0 | skip20_half20_40 | -0.371 | -0.439 | -0.984 | -1.124 | -0.565 | -0.808 |
| PB12_0 | skip_bottom20 | -0.167 | -0.267 | -0.511 | -0.594 | -0.238 | -0.445 |
| PB12_0 | skip_bottom33 | -0.395 | -0.430 | -1.200 | -1.295 | -0.774 | -0.979 |

Kept signals per contract, signals thrown away, share kept (L6M / HOLD):
| variant | policy | keeps_L6M | pc_L6M | pc_HOLD | fired_base_L6M | fired_base_HOLD | lots_ratio_L6M |
|--|--|--|--|--|--|--|--|
| P12_0 | skip_bottom20 | 0.827 | -0.301 | -0.155 | 4.684 | 3.186 | 0.827 |
| P12_0 | skip_bottom33 | 0.707 | -0.462 | -0.244 | 4.360 | 3.081 | 0.707 |
| P3_0 | skip_bottom20 | 0.846 | -0.844 | -0.951 | 7.882 | 6.700 | 0.846 |
| P3_0 | skip_bottom33 | 0.717 | -1.873 | -2.019 | 7.992 | 6.976 | 0.717 |
| PB12_0 | skip_bottom20 | 0.814 | 0.013 | -0.013 | 3.187 | 2.606 | 0.814 |
| PB12_0 | skip_bottom33 | 0.686 | -0.401 | -0.548 | 4.119 | 3.690 | 0.686 |

Shuffled-label placebo (6 draws; the same policy on a model trained on label-shuffled data; gain per signal): real P12 sits above every placebo draw only if its gain exceeds the max.
| policy | win | mean | std | min | max |
|--|--|--|--|--|--|
| skip_bottom20 | HOLD | -0.782 | 0.347 | -1.309 | -0.291 |
| skip_bottom20 | L6M | -0.961 | 0.221 | -1.220 | -0.635 |
| skip_bottom33 | HOLD | -0.894 | 0.468 | -1.477 | -0.352 |
| skip_bottom33 | L6M | -1.178 | 0.387 | -1.708 | -0.704 |

Lock-engine stack delta ($/wk, research lots, planned-lot-R locks) of the pooled skip policies:
| variant | policy | base | stack|Y26 | stack|L6M | stack|HOLD | stack|PRE | stack|X |
|--|--|--|--|--|--|--|--|
| P3_0 | skip_bottom20 | MKT | 20265 | -14849 | -17953 | -7231 | -7515 |
| P3_0 | skip_bottom20 | SPL | 11431 | -20041 | -21590 | -9147 | -7906 |
| P3_0 | skip_bottom33 | MKT | 25682 | -36848 | -36627 | -9697 | -6511 |
| P3_0 | skip_bottom33 | SPL | 17591 | -40357 | -38821 | -14624 | -9092 |
| P12_0 | skip_bottom20 | MKT | 30547 | -2074 | 2913 | -1664 | -1658 |
| P12_0 | skip_bottom20 | SPL | 28118 | -480 | 4784 | -1669 | -1645 |
| P12_0 | skip_bottom33 | MKT | 48518 | -3402 | 3366 | 834 | -4403 |
| P12_0 | skip_bottom33 | SPL | 35276 | -6183 | 2047 | -2248 | -5827 |
| PB12_0 | skip_bottom20 | MKT | 14378 | -13610 | -14003 | 2213 | -3649 |
| PB12_0 | skip_bottom20 | SPL | 12576 | -14637 | -13735 | 1831 | -3617 |
| PB12_0 | skip_bottom33 | MKT | 69560 | -5727 | -7179 | -11991 | -5233 |
| PB12_0 | skip_bottom33 | SPL | 65946 | -8623 | -8933 | -15355 | -4836 |

Per book (gain per signal of the book, skip bottom 20%, market base): pooled P12 model and per-book PB12 models:
| scope | P12 PRE | P12 X | P12 HOLD | P12 L6M | PB12 PRE | PB12 X | PB12 HOLD | PB12 L6M |
|--|--|--|--|--|--|--|--|--|
| DN | -0.413 | -1.111 | -2.300 | -2.778 | -0.771 | -0.023 | -1.592 | -2.222 |
| HM | 0.047 | -0.328 | -0.696 | -1.291 | 0.695 | -0.599 | -0.730 | -0.756 |
| KB | -0.359 | 0.195 | -0.664 | -0.774 | -0.373 | -0.395 | 0.062 | 0.047 |
| MA | -0.594 | -0.680 | 0.490 | -0.805 | -0.685 | -0.218 | -0.709 | -1.830 |
| MV | -0.065 | 0.343 | -0.996 | -0.985 | 0.418 | -0.267 | -0.330 | -0.694 |
| PB | -0.047 | -0.293 | -1.216 | -1.419 | -0.580 | 0.234 | -0.724 | -0.910 |
| PE | -0.277 | -0.598 | -0.439 | -0.466 | 0.137 | -0.523 | -0.089 | 0.355 |
| SM | -0.466 | 0.374 | 0.523 | 0.504 | -1.427 | 0.000 | -1.924 | -1.116 |
| ST | -0.332 | -0.472 | -0.485 | -0.467 | 0.225 | 0.271 | -0.579 | -0.624 |
| WT | -0.016 | -0.022 | -0.073 | -0.091 | -0.508 | -0.655 | -0.295 | -0.333 |

The extracted rule set (depth-limited tree fitted on PRE u X' to the model's skip-bottom-33% decision; 6 leaves; 'class: True' = skip):
```
|--- px.loc.ON.sidedloc <= 0.98
|   |--- st.vwap_dist_pts_eth <= 44.69
|   |   |--- class: False
|   |--- st.vwap_dist_pts_eth >  44.69
|   |   |--- st.4h.atr_ratio <= 2.01
|   |   |   |--- px.ext.1m.ema200>=5 <= 0.50
|   |   |   |   |--- class: False
|   |   |   |--- px.ext.1m.ema200>=5 >  0.50
|   |   |   |   |--- class: False
|   |   |--- st.4h.atr_ratio >  2.01
|   |   |   |--- class: True
|--- px.loc.ON.sidedloc >  0.98
|   |--- px.loc.OR30.sidedloc <= 1.53
|   |   |--- class: False
|   |--- px.loc.OR30.sidedloc >  1.53
|   |   |--- class: True
```
Retained: the tree rule set applied as a skip (gain per signal, per contract of the kept signals, MDE):
| base | HOLD | L3M | L6M | PRE | X | Y26 |
|--|--|--|--|--|--|--|
| MKT | 0.076 | 0.401 | 0.094 | -0.066 | -0.001 | 0.711 |
| SPL | 0.049 | 0.402 | 0.056 | -0.073 | 0.053 | 0.745 |

### 7b. Second learned target - regression of the signal's N-basis net pts (P12, weekly walk-forward)

Rank IC of the predicted pts with the realised pts (OOS) by window, real vs the shuffled-label draws:
| variant | HOLD | L3M | L6M | PRE | X |
|--|--|--|--|--|--|
| P12_0 | 0.022 | 0.030 | 0.022 | -0.000 | 0.005 |
| P3S_1 | 0.018 | 0.006 | 0.014 | -0.009 | 0.012 |
| P3S_2 | 0.005 | -0.007 | 0.001 | 0.003 | -0.008 |
| P3S_3 | -0.018 | -0.006 | -0.021 | 0.011 | -0.018 |
| P3S_4 | -0.013 | -0.017 | -0.014 | -0.014 | -0.019 |

Policy gain per signal (skip bottom 20 / 33% of predicted pts):
| variant | policy | PRE | X | HOLD | L6M | L3M | Y26 |
|--|--|--|--|--|--|--|--|
| P12_0 | skip_bottom20 | -0.455 | -0.280 | -0.192 | -0.271 | -0.362 | -0.418 |
| P12_0 | skip_bottom33 | -0.427 | -0.109 | 0.030 | -0.086 | 0.150 | 0.209 |
| P3S_1 | skip_bottom20 | -0.499 | -0.031 | 0.016 | -0.206 | -0.104 | -0.593 |
| P3S_1 | skip_bottom33 | -0.686 | -0.074 | -0.318 | -0.624 | -0.261 | -1.160 |
| P3S_2 | skip_bottom20 | -0.319 | 0.067 | -0.438 | -0.608 | -0.371 | -0.454 |
| P3S_2 | skip_bottom33 | -0.603 | -0.255 | -0.533 | -0.818 | -0.865 | -1.482 |
| P3S_3 | skip_bottom20 | -0.091 | -0.224 | -0.838 | -1.045 | -0.499 | -0.742 |
| P3S_3 | skip_bottom33 | -0.364 | -0.531 | -1.267 | -1.590 | -0.772 | -1.339 |
| P3S_4 | skip_bottom20 | -0.510 | -0.144 | -0.592 | -0.846 | -0.644 | -1.385 |
| P3S_4 | skip_bottom33 | -0.710 | -0.295 | -1.182 | -1.495 | -0.883 | -1.609 |

Per contract of the kept signals, share kept, lot ratio, throw-away P&L:
| policy | fired_base_HOLD | fired_base_L6M | lots_ratio_HOLD | lots_ratio_L6M | n_HOLD | n_L6M | nfire_HOLD | nfire_L6M | pc_HOLD | pc_L6M |
|--|--|--|--|--|--|--|--|--|--|--|
| skip_bottom20 | 1.053 | 1.623 | 0.817 | 0.833 | 10803 | 9741 | 1974 | 1625 | 0.336 | 0.325 |
| skip_bottom33 | -0.099 | 0.301 | 0.694 | 0.713 | 10803 | 9741 | 3306 | 2792 | 1.170 | 1.183 |
Stack ($/wk):
| policy | base | stack|Y26 | stack|L6M | stack|HOLD | stack|PRE | stack|X |
|--|--|--|--|--|--|--|
| skip_bottom20 | MKT | 39696 | 2699 | 3509 | -6420 | -3770 |
| skip_bottom20 | SPL | 22428 | -740 | 1533 | -8265 | -3173 |
| skip_bottom33 | MKT | 69500 | 19691 | 21479 | -7177 | -1361 |
| skip_bottom33 | SPL | 67863 | 18897 | 22186 | -11922 | -2568 |

## 8. QUANT-LAYER program validity (White RC best-cell p, Romano-Wolf survivors, PBO, DSR) over the selected pooled cells of each group

| program | group_base | cells | RC_L6M | RC_HOLD | RC_cum_L6M | RW_surv_L6M | RW_surv_HOLD | PBO | xRC_L6M | xRC_HOLD | xRC_cum | xRW_L6M | xPBO |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| B_D | B|MKT | 400 | 0.976 | 0.904 | 1.000 | 0 | 0 | 0.413 | 0.272 | 0.282 | 1.000 | 3.000 | 0.389 |
| B_D | B|SPL | 400 | 0.964 | 0.878 | 1.000 | 0 | 0 | 0.421 | 0.214 | 0.226 | 1.000 | 3.000 | 0.397 |
| B_D | D|MKT | 400 | 0.000 | 0.022 | 0.000 | 24 | 10 | 0.786 | 0.072 | 0.062 | 1.000 | 2.000 | 0.738 |
| B_D | D|SPL | 400 | 0.000 | 0.018 | 0.000 | 24 | 12 | 0.694 | 0.336 | 0.576 | 1.000 | 0.000 | 0.675 |
| combo | C|MKT | 300 | 0.692 | 0.686 | 1.000 | 0 | 0 | 0.806 |  |  |  |  |  |
| combo | C|SPL | 300 | 0.676 | 0.674 | 1.000 | 0 | 0 | 0.813 |  |  |  |  |  |

xRC / xPBO = the same test on the gain OVER the lot-matched uniform scaling of the base (the right null for size rules). RC_cum = Sidak-adjusted to the 317,628 cell-scopes of this program (cumulative with earlier programs the multiplicity is ~1 million: no cell clears). A size-up cell clears the raw RC (p 0.00) only because a positive base grows with lots; the right null is the uniform scaling (xRC columns): market base p 0.07 / 0.06, 2 / 4 Romano-Wolf survivors, 70/30 base p 0.34 / 0.58; Sidak-adjusted to 317,628 cell-scopes both are ~1.

## 9. Shortlist checks (the 382 cells with tier >= CANDIDATE-RECENT and a positive stack, plus the directive's named release / calendar cells): neighbourhood, circular-shift state placebo, lag-one-signal state placebo, 1 s / 3 s latency, stack with its MDE, stack against the lot-matched uniform control

* nbL6M = mean L6M gain of the two ADJACENT thresholds of the same state (blank for states without a threshold family); shift = rank of the real L6M gain among 100 circular shifts of the state within book x session (1.00 = beats all); lag1 = gain with the previous signal's state; lat1s / lat3s = the same rule when the entry is one / three seconds late (blank for delay / re-target rules); stkMDE = 2.8 x SE of the weekly stack delta; ex* = stack minus the stack of uniformly scaling every signal to the same lot ratio (engine-mult route, equal-risk frame, STRUCTURE).

**Sunday-brief rule (directive: L6M and HOLD >= 0 per contract AND on the stack, placebo beaten) is met by 148 of the 382 shortlisted cells (selected on PRE u X', per contract >= 0 in L6M and HOLD, stack >= 0 in L6M and HOLD, random-fire plc >= 0.95, circular-shift rank >= 0.95, size rules also >= 0 against the uniform control); 76 of them also have a positive stack in PRE and in X'.** Inside their own MDE: 143 of 148 have a stack delta below its MDE in L6M. Program-level reality check: none clears (section 8).

### 9. B single-state (skip / size down / delay / re-target): 44 eligible
| rule | act | base | scope | tier | PRE | X | L6M | HOLD | pcL6M | MDE | plc | shift | nbL6M | lag1 | lat1s | lat3s | stkL6M | stkMDE | stkHOLD | stkPRE | stkX | exL6M | exHOLD | exPRE | exX | lots |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| set.ahead20_set11_fresh | skip | SPL | ALL | CANDIDATE-RECENT | 0.28 | 0.45 | 0.36 | 0.45 | 1.03 | 0.93 | 1.00 | 1.00 |  | -0.64 | 0.47 | 0.38 | 30117.59 | 29404.71 | 26652.50 | 8879.78 | 3150.16 | 35377.42 | 30882.66 | 21744.13 | 5193.86 | 0.84 |
| set.ahead20_set11_fresh | skip | MKT | ALL | CANDIDATE-RECENT | 0.31 | 0.40 | 0.31 | 0.42 | 0.97 | 0.95 | 1.00 | 1.00 |  | -0.65 | 0.42 | 0.36 | 29833.67 | 29358.49 | 25283.76 | 11298.83 | 5714.07 | 31080.28 | 27703.82 | 19179.01 | 7077.62 | 0.84 |
| set.ahead20_set11_fresh | z25 | SPL | ALL | CANDIDATE-RECENT | 0.21 | 0.34 | 0.27 | 0.34 | 0.74 | 0.70 | 1.00 | 1.00 |  | -0.48 | 0.35 | 0.29 | 24278.59 | 22309.77 | 21155.67 | 6258.86 | 3566.68 | 32166.85 | 28032.58 | 17554.56 | 4141.61 | 0.88 |
| set.ahead20_set11_fresh | z25 | MKT | ALL | CANDIDATE-RECENT | 0.23 | 0.30 | 0.24 | 0.32 | 0.70 | 0.71 | 1.00 | 1.00 |  | -0.48 | 0.32 | 0.27 | 19789.95 | 20781.62 | 15628.60 | 10624.78 | 6660.13 | 21889.62 | 19928.39 | 16082.17 | 5668.25 | 0.88 |
| set.ahead20_set11_fresh | z50 | SPL | ALL | CANDIDATE-RECENT | 0.14 | 0.23 | 0.18 | 0.23 | 0.47 | 0.47 | 1.00 | 1.00 |  | -0.32 | 0.23 | 0.19 | 17517.01 | 18998.09 | 14937.98 | 2221.53 | 4034.47 | 17957.38 | 15515.21 | 12825.07 | 5325.91 | 0.92 |
| set.ahead20_set11_fresh | z50 | MKT | ALL | CANDIDATE-RECENT | 0.15 | 0.20 | 0.16 | 0.21 | 0.45 | 0.48 | 1.00 | 1.00 |  | -0.32 | 0.21 | 0.18 | 14879.69 | 19179.39 | 11534.61 | 5048.46 | 4575.50 | 15453.31 | 14838.17 | 9847.88 | 1951.36 | 0.92 |
| st.f60_vs_med>=1.809 | d15 | SPL | ALL | CANDIDATE-RECENT | 0.12 | 0.05 | 0.23 | 0.22 | 0.37 | 0.70 | 0.99 | 1.00 | 0.08 | -0.05 |  |  | 10697.12 | 21681.35 | 9523.70 | 53.95 | 6.75 |  |  |  |  | 0.96 |
| st.f60_vs_med>=1.809 | d15 | MKT | ALL | CANDIDATE-RECENT | 0.11 | 0.04 | 0.19 | 0.18 | 0.32 | 0.71 | 0.99 | 0.96 | 0.02 | -0.04 |  |  | 10517.91 | 23862.76 | 9099.67 | 2578.03 | -358.64 |  |  |  |  | 0.96 |
| bk.t_since_big_against<=300 | d15 | MKT | HM | CANDIDATE-RECENT | 0.35 | 1.07 | 0.36 | 0.37 | 0.80 | 1.80 | 0.97 | 0.97 | 0.51 | -0.56 |  |  | 7736.84 | 6524.30 | 7285.45 | 4095.93 | 458.66 |  |  |  |  | 0.92 |
| eng.opp_flip_within60 | rt50 | SPL | ALL | CANDIDATE-RECENT | 0.02 | 0.09 | 0.08 | 0.05 | 0.09 | 0.34 | 0.98 | 0.95 |  | -0.11 |  |  | 7978.59 | 13469.24 | 6972.93 | -4042.84 | -2418.07 |  |  |  |  | 1.00 |
| set.ahead20_set11_fresh | rt50 | SPL | ALL | CANDIDATE-RECENT | 0.05 | 0.11 | 0.21 | 0.18 | 0.22 | 0.75 | 1.00 | 0.99 |  | -0.21 |  |  | 6995.07 | 25939.42 | 5980.26 | -587.28 | -5765.31 |  |  |  |  | 1.00 |
| st.sig_vel30<=-3.6 | d5 | SPL | ALL | CANDIDATE-RECENT | 0.06 | 0.11 | 0.17 | 0.18 | 0.22 | 0.38 | 0.99 | 0.98 | -0.01 | -0.02 |  |  | 6220.54 | 14670.61 | 5512.82 | -6876.80 | 2854.62 |  |  |  |  | 0.99 |
| st.rv30_ann>=46.11 | rt50 | SPL | ALL | CANDIDATE-RECENT | 0.04 | 0.16 | 0.20 | 0.17 | 0.21 | 0.47 | 1.00 | 1.00 | 0.01 | -0.18 |  |  | 6171.04 | 18890.77 | 5293.15 | -4333.42 | -153.85 |  |  |  |  | 1.00 |
| st.sig_vol60>=2533 | d5 | MKT | ALL | CANDIDATE-RECENT | 0.01 | 0.23 | 0.24 | 0.22 | 0.36 | 0.69 | 0.97 | 1.00 | 0.05 | 0.03 |  |  | 5660.23 | 14103.34 | 5048.91 | -664.36 | 8868.50 |  |  |  |  | 0.97 |
| st.sig_vel30<=-3.6 | d5 | MKT | nyam | CANDIDATE-RECENT | 0.22 | 0.50 | 0.63 | 0.65 | 0.75 | 0.73 | 0.97 | 0.98 | 0.21 | 0.51 |  |  | 5629.11 | 9662.48 | 4490.29 | -2573.38 | 2512.62 |  |  |  |  | 0.96 |
| st.sig_vol60>=2533 | d5 | SPL | ALL | CANDIDATE-RECENT | 0.01 | 0.30 | 0.25 | 0.23 | 0.38 | 0.69 | 1.00 | 0.99 | 0.02 | 0.03 |  |  | 4920.89 | 16463.62 | 4290.20 | -509.86 | 8864.35 |  |  |  |  | 0.97 |
| st.ret_ES_15m<=-4.073 | d5 | MKT | asia | CANDIDATE-RECENT | 0.13 | 0.05 | 0.21 | 0.18 | 0.23 | 0.53 | 1.00 | 1.00 | -0.29 | -0.04 |  |  | 4897.74 | 10673.67 | 4084.26 | -916.04 | -502.37 |  |  |  |  | 1.00 |
| st.prev_close_loc>=0.4225 | d15 | SPL | ALL | CANDIDATE-RECENT | 0.07 | 0.09 | 0.24 | 0.17 | 0.31 | 0.32 | 1.00 | 1.00 | -0.03 | 0.07 |  |  | 4964.30 | 9738.24 | 4017.13 | -5619.03 | 1580.95 |  |  |  |  | 0.98 |
| st.1h.rng_exp1<=0.6003 | z25 | SPL | ALL | CANDIDATE-RECENT | 0.01 | 0.24 | 0.07 | 0.15 | 0.29 | 0.46 | 0.99 | 1.00 | -0.10 | -0.26 | 0.07 | 0.06 | 3936.00 | 26835.38 | 4850.14 | -5730.44 | 7903.26 | 4647.64 | 5802.11 | 3431.71 | 8169.83 | 0.94 |
| st.sig_delta10_s<=-26 | d5 | MKT | ALL | CANDIDATE-RECENT | 0.10 | 0.11 | 0.21 | 0.23 | 0.28 | 0.34 | 0.97 | 0.99 | 0.04 | 0.12 |  |  | 3912.80 | 8372.79 | 3561.70 | -4284.51 | 8763.41 |  |  |  |  | 0.98 |
| st.prev_rng_atrd>=1.301 | d5 | MKT | KB | CANDIDATE-RECENT | 0.73 | 0.09 | 1.33 | 1.05 | 1.40 | 1.97 | 0.97 | 0.98 | 0.46 | 1.07 |  |  | 4315.44 | 5971.83 | 3492.92 | 1560.46 | 1405.18 |  |  |  |  | 0.98 |
| day.afterbigday1p5pct | d5 | SPL | KB | CANDIDATE-RECENT | 0.74 | 0.04 | 1.03 | 0.94 | 1.08 | 1.70 | 0.97 | 0.96 |  | 1.14 |  |  | 3908.66 | 5827.71 | 3420.08 | 983.01 | 899.51 |  |  |  |  | 0.98 |
| st.prev_rng_atrd>=1.697 | d15 | MKT | ALL | CANDIDATE-RECENT | 0.14 | 0.07 | 0.24 | 0.21 | 0.41 | 0.44 | 1.00 | 1.00 | -0.53 | 0.10 |  |  | 3840.61 | 14387.62 | 3360.54 | -284.20 | -89.09 |  |  |  |  | 0.95 |
| st.rv30_ann>=46.11 | rt50 | MKT | ALL | CANDIDATE-RECENT | 0.04 | 0.14 | 0.22 | 0.19 | 0.22 | 0.47 | 1.00 | 1.00 | 0.04 | -0.14 |  |  | 3800.49 | 14596.70 | 3220.43 | -987.53 | -754.52 |  |  |  |  | 1.00 |
| st.sig_delta10_s<=-26 | d15 | SPL | PE | CANDIDATE-RECENT | 0.55 | 0.56 | 1.12 | 1.01 | 1.21 | 1.11 | 0.99 | 1.00 | 0.54 | -0.43 |  |  | 3742.89 | 5320.85 | 2991.61 | 960.84 | 1460.39 |  |  |  |  | 0.96 |

### 9. D opposite side (size up / take-only): 57 eligible
| rule | act | base | scope | tier | PRE | X | L6M | HOLD | pcL6M | MDE | plc | shift | nbL6M | lag1 | lat1s | lat3s | stkL6M | stkMDE | stkHOLD | stkPRE | stkX | exL6M | exHOLD | exPRE | exX | lots |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| st.15m.range_pos60>=0.3921 | u200 | SPL | ALL | CANDIDATE-RECENT | 0.64 | 0.44 | 1.26 | 1.11 | 0.37 | 1.60 | 0.97 | 0.96 | 0.65 | 0.60 | 1.17 | 1.19 | 30715.50 | 27628.86 | 27967.63 | 4192.24 | 420.35 | 37167.77 | 32950.54 | 4395.47 | -3362.08 | 1.24 |
| px.loc.SESS.premium | u150 | MKT | ALL | CANDIDATE-RECENT | 0.55 | 0.30 | 1.48 | 1.27 | 0.30 | 1.32 | 1.00 | 1.00 |  | 0.96 | 1.39 | 1.38 | 24049.20 | 36992.26 | 18834.89 | 2413.60 | 14896.23 | 28615.98 | 25700.61 | 6024.72 | 9596.62 | 1.33 |
| px.ext.1m.ema200>=8 | u200 | SPL | ALL | PASS_pre_RC | 0.57 | 0.52 | 1.17 | 1.13 | 0.69 | 0.85 | 1.00 | 1.00 | 2.96 | -0.00 | 1.11 | 1.10 | 20139.92 | 28970.93 | 18525.40 | -7367.75 | -8883.89 | 19981.46 | 17975.63 | -7091.26 | -10448.30 | 1.12 |
| px.ext.5m.ema200>=8 | u200 | SPL | ALL | CANDIDATE-RECENT | 0.67 | 0.82 | 0.85 | 0.75 | 0.42 | 1.30 | 0.99 | 0.99 | 1.37 | -0.03 | 0.83 | 0.81 | 22293.78 | 23925.37 | 18504.36 | -2344.18 | 13221.52 | 21697.52 | 17585.04 | -1943.56 | 11824.93 | 1.12 |
| px.loc.SESS.premium | u150 | SPL | ALL | CANDIDATE-RECENT | 0.55 | 0.28 | 1.48 | 1.27 | 0.30 | 1.34 | 1.00 | 1.00 |  | 0.95 | 1.38 | 1.43 | 19857.49 | 37346.92 | 18126.34 | -718.16 | 11905.45 | 19564.14 | 19921.45 | 537.33 | 5684.80 | 1.33 |
| px.loc.SESS.sidedloc>=0.8 | u150 | MKT | ALL | CANDIDATE-RECENT | 0.44 | 0.28 | 1.27 | 1.08 | 0.36 | 1.22 | 1.00 | 1.00 |  | 0.52 | 1.19 | 1.17 | 25280.30 | 34692.56 | 17234.27 | 3802.08 | 11220.44 | 25071.88 | 20110.52 | 3520.60 | 8860.68 | 1.25 |
| st.1m.rng_exp1<=0.9489 | u200 | MKT | ALL | CANDIDATE-RECENT | 0.58 | 0.26 | 1.69 | 1.31 | 0.66 | 1.41 | 0.99 | 1.00 | 0.66 | 0.46 | 1.54 | 1.52 | 24103.12 | 33140.94 | 16988.69 | 8685.06 | -4220.93 | 23934.63 | 19556.40 | 8011.06 | -5946.05 | 1.26 |
| px.wrong.priorclose>=50 | u200 | SPL | asia | PASS_pre_RC | 2.81 | 1.23 | 5.17 | 4.36 | 2.65 | 3.40 | 1.00 | 1.00 | 4.80 | 0.59 | 5.02 | 5.12 | 20292.90 | 43471.48 | 15792.13 | 9328.45 | 6363.69 | 28952.34 | 23671.49 | 10007.19 | 8228.60 | 1.38 |
| st.1m.rng_exp1<=0.9489 | u200 | SPL | ALL | CANDIDATE-RECENT | 0.51 | 0.24 | 1.58 | 1.22 | 0.57 | 1.40 | 0.99 | 1.00 | 0.61 | 0.45 | 1.57 | 1.54 | 21892.63 | 28397.28 | 15719.14 | 14365.55 | -1853.10 | 28289.99 | 20616.93 | 14712.22 | -6931.53 | 1.26 |
| st.15m.er20<=0.0408 | u200 | SPL | ALL | CANDIDATE-RECENT | 0.39 | 0.17 | 0.66 | 0.62 | 0.29 | 0.68 | 0.96 | 1.00 | 1.25 | 0.26 | 0.67 | 0.65 | 16332.02 | 20749.65 | 15179.64 | 5553.12 | -2856.09 | 12644.58 | 11343.91 | 5011.77 | -4952.54 | 1.10 |
| st.15m.er20<=0.105 | u200 | SPL | ALL | PASS_pre_RC | 0.60 | 0.24 | 1.25 | 1.09 | 0.34 | 1.01 | 0.96 | 0.98 | 0.66 | 0.77 | 1.19 | 1.22 | 15172.13 | 27330.91 | 16095.99 | 11226.65 | -5186.24 | 20041.25 | 19616.78 | 11395.37 | -10355.29 | 1.25 |
| px.wrong.priorclose>=50 | u150 | MKT | asia | PASS_pre_RC | 1.44 | 0.60 | 2.62 | 2.20 | 1.53 | 1.73 | 1.00 | 1.00 | 2.48 | 0.33 | 2.49 | 2.52 | 20696.35 | 24381.44 | 14743.08 | 3189.96 | 3106.39 | 22679.39 | 17672.41 | 5515.54 | 1797.64 | 1.19 |
| px.ext.1m.ema200>=5 | u150 | MKT | ALL | PASS_pre_RC | 0.39 | 0.41 | 1.51 | 1.31 | 0.71 | 0.98 | 1.00 | 1.00 | 1.10 | 0.42 | 1.41 | 1.41 | 19820.64 | 33919.35 | 14633.05 | -1932.11 | 14379.34 | 20188.91 | 17445.79 | 1783.34 | 11805.91 | 1.20 |
| px.ext.5m.ema200>=8 | u200 | MKT | ALL | CANDIDATE-RECENT | 0.68 | 0.85 | 0.87 | 0.75 | 0.44 | 1.30 | 0.99 | 0.98 | 1.42 | -0.03 | 0.81 | 0.80 | 18473.66 | 25471.34 | 14518.04 | -5265.84 | 11902.13 | 14262.00 | 13074.19 | -979.02 | 8718.36 | 1.12 |
| px.loc.OR30.sidedloc>=0.8 | u200 | MKT | ALL | CANDIDATE-RECENT | 0.84 | 1.33 | 1.58 | 1.33 | 0.30 | 2.29 | 1.00 | 1.00 |  | 0.50 | 1.44 | 1.45 | 14389.24 | 41554.62 | 14590.47 | 8124.07 | -2967.04 | 19642.08 | 24245.30 | 10977.87 | -11242.41 | 1.36 |
| st.15m.er20<=0.105 | u200 | MKT | ALL | PASS_pre_RC | 0.64 | 0.17 | 1.25 | 1.07 | 0.34 | 0.95 | 0.96 | 0.97 | 0.62 | 0.83 | 1.16 | 1.10 | 14138.10 | 30198.31 | 13628.76 | 8856.82 | -9739.78 | 13918.00 | 16478.38 | 8469.94 | -12104.18 | 1.25 |
| px.wrong.priorclose>=50 | u150 | SPL | asia | PASS_pre_RC | 1.41 | 0.61 | 2.59 | 2.18 | 1.53 | 1.70 | 1.00 | 1.00 | 2.40 | 0.30 | 2.51 | 2.56 | 16801.69 | 25415.65 | 13071.57 | 1563.91 | 1955.98 | 20072.62 | 15362.27 | 5363.53 | 3272.75 | 1.19 |
| px.wrong.priorclose>=50 | u200 | MKT | asia | PASS_pre_RC | 2.88 | 1.19 | 5.25 | 4.40 | 2.64 | 3.45 | 1.00 | 1.00 | 4.97 | 0.65 | 4.98 | 5.04 | 19212.75 | 39762.44 | 12994.83 | 7316.86 | 6083.09 | 23911.89 | 19437.54 | 7413.23 | 7144.40 | 1.38 |
| px.loc.SESS.sidedloc>=0.8 | u150 | SPL | ALL | CANDIDATE-RECENT | 0.44 | 0.23 | 1.25 | 1.06 | 0.34 | 1.23 | 1.00 | 1.00 |  | 0.52 | 1.18 | 1.19 | 17780.53 | 36012.94 | 12905.65 | 3065.73 | 8005.02 | 23185.86 | 16890.30 | 3177.64 | 2845.80 | 1.25 |
| px.ext.1m.ema200>=8 | u150 | MKT | ALL | PASS_pre_RC | 0.31 | 0.28 | 0.60 | 0.58 | 0.38 | 0.42 | 1.00 | 1.00 | 1.51 | 0.00 | 0.57 | 0.57 | 14842.30 | 21061.97 | 12114.67 | -3295.99 | 10473.38 | 12545.34 | 11710.10 | -3157.45 | 6970.05 | 1.06 |
| st.1h.rsi14>=60.22 | u200 | SPL | ALL | CANDIDATE-RECENT | 1.05 | 0.96 | 1.12 | 1.12 | 0.30 | 1.37 | 0.99 | 0.95 | 0.26 | 0.90 | 1.11 | 1.11 | 11600.96 | 38710.36 | 13557.83 | 6676.99 | 100.20 | 12208.40 | 13391.31 | 6451.77 | -2909.16 | 1.23 |
| px.ext.1m.ema200>=8 | u200 | MKT | ALL | PASS_pre_RC | 0.62 | 0.56 | 1.20 | 1.16 | 0.72 | 0.84 | 1.00 | 1.00 | 3.02 | 0.00 | 1.14 | 1.13 | 11105.52 | 31618.48 | 11476.77 | -4027.42 | -12804.11 | 7288.31 | 10408.88 | 166.32 | -16019.43 | 1.12 |
| st.15m.hma_slope>=0.4067 | u200 | SPL | ALL | CANDIDATE-RECENT | 0.67 | 0.30 | 1.47 | 1.19 | 0.58 | 1.49 | 1.00 | 1.00 | 0.49 | 0.55 | 1.40 | 1.35 | 11026.55 | 29418.58 | 10983.09 | -6320.45 | 17801.61 | 12059.02 | 11173.41 | -5853.75 | 14949.68 | 1.23 |
| px.ext.5m.ema50>=3 | u200 | SPL | ALL | PASS_pre_RC | 0.91 | 0.75 | 1.99 | 1.81 | 0.76 | 1.72 | 1.00 | 1.00 | 1.41 | 0.45 | 1.89 | 1.81 | 13763.09 | 44653.52 | 10949.46 | -646.28 | -6029.53 | 16693.14 | 14862.17 | 911.58 | -11113.95 | 1.31 |
| st.open_drive5>=0.08545 | u150 | MKT | ALL | CANDIDATE-RECENT | 0.45 | 0.37 | 0.56 | 0.50 | 0.18 | 0.93 | 0.97 | 1.00 | 0.39 | 0.35 | 0.52 | 0.47 | 12419.21 | 23010.31 | 10896.79 | 8100.24 | 1121.69 | 7896.68 | 9162.58 | 11502.11 | -2273.60 | 1.11 |

### 9. C combinations: 47 eligible
| rule | act | base | scope | tier | PRE | X | L6M | HOLD | pcL6M | MDE | plc | shift | nbL6M | lag1 | lat1s | lat3s | stkL6M | stkMDE | stkHOLD | stkPRE | stkX | exL6M | exHOLD | exPRE | exX | lots |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ANY2of10[evt.failbrk_high.within30.ict_with,st.prev_ret_rth> | skip | MKT | KB | CANDIDATE-RECENT | 1.15 | 1.73 | 0.85 | 0.81 | 1.43 | 1.91 | 0.97 | 0.95 |  | -0.05 | 0.86 | 0.89 | 2695.51 | 6920.80 | 2273.34 | 412.67 | 4226.84 | 4305.75 | 3869.01 | 1814.75 | 3412.71 | 0.81 |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_er_rth>=0.2767&st.day | rt50 | SPL | ALL | CANDIDATE-RECENT | 0.19 | 0.27 | 0.19 | 0.18 | 0.20 | 0.23 | 1.00 | 1.00 |  | 0.01 |  |  | 2371.32 | 7644.64 | 2074.91 | 1083.90 | 1985.13 |  |  |  |  | 1.00 |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_er_rth>=0.2767] | rt50 | SPL | ALL | CANDIDATE-RECENT | 0.19 | 0.27 | 0.19 | 0.18 | 0.20 | 0.23 | 1.00 | 1.00 |  | 0.01 |  |  | 2371.32 | 7644.64 | 2074.91 | 1083.90 | 1985.13 |  |  |  |  | 1.00 |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301] | d15 | SPL | SM | CANDIDATE-RECENT | 0.56 | 0.18 | 1.03 | 0.89 | 1.11 | 2.22 | 1.00 | 1.00 |  | 0.23 |  |  | 1777.24 | 3942.90 | 1555.09 | 257.33 | 477.91 |  |  |  |  | 0.98 |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | skip | MKT | ALL | CANDIDATE-RECENT | 0.14 | 0.11 | 0.09 | 0.08 | 0.15 | 0.20 | 0.96 | 0.99 |  | 0.05 | 0.09 | 0.10 | 1754.43 | 4946.13 | 1535.12 | 886.63 | 3345.16 | 3364.96 | 2784.80 | 1675.81 | 3282.52 | 0.98 |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | skip | MKT | KB | CANDIDATE-RECENT | 1.09 | 0.95 | 0.67 | 0.61 | 1.10 | 1.53 | 0.96 | 0.98 |  | 0.39 | 0.68 | 0.79 | 1754.43 | 4946.13 | 1535.12 | 886.63 | 3345.16 | 2450.75 | 2404.53 | 1377.04 | 2786.13 | 0.84 |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | rt50 | SPL | ALL | CANDIDATE-RECENT | 0.34 | 0.30 | 0.13 | 0.12 | 0.13 | 0.44 | 0.99 | 1.00 |  | -0.02 |  |  | 1722.38 | 17229.46 | 1507.08 | 1918.76 | 2447.12 |  |  |  |  | 1.00 |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_er_rth>=0.2767&st.day | rt50 | MKT | ALL | CANDIDATE-RECENT | 0.17 | 0.27 | 0.20 | 0.18 | 0.20 | 0.23 | 1.00 | 1.00 |  | -0.00 |  |  | 1706.54 | 5349.78 | 1493.22 | -555.38 | 2351.03 |  |  |  |  | 1.00 |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_er_rth>=0.2767] | rt50 | MKT | ALL | CANDIDATE-RECENT | 0.17 | 0.27 | 0.20 | 0.18 | 0.20 | 0.23 | 1.00 | 1.00 |  | -0.00 |  |  | 1706.54 | 5349.78 | 1493.22 | -555.38 | 2351.03 |  |  |  |  | 1.00 |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | skip | SPL | ALL | CANDIDATE-RECENT | 0.13 | 0.11 | 0.09 | 0.08 | 0.16 | 0.21 | 0.95 | 0.98 |  | 0.06 | 0.09 | 0.09 | 1697.47 | 4986.05 | 1485.28 | 1096.87 | 2841.15 | 2629.13 | 1950.24 | 3682.00 | 3760.55 | 0.98 |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.301] | skip | SPL | KB | CANDIDATE-RECENT | 1.06 | 0.96 | 0.67 | 0.62 | 1.05 | 1.59 | 0.95 | 0.96 |  | 0.45 | 0.70 | 0.71 | 1697.47 | 4986.05 | 1485.28 | 1096.87 | 2841.15 | 4170.57 | 3667.85 | 854.07 | 2838.80 | 0.84 |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.697] | rt50 | MKT | ALL | CANDIDATE-RECENT | 0.08 | 0.04 | 0.09 | 0.08 | 0.09 | 0.14 | 1.00 | 1.00 |  | 0.04 |  |  | 1568.63 | 2816.75 | 1372.55 | -811.98 | 1118.65 |  |  |  |  | 1.00 |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | rt50 | MKT | SM | CANDIDATE-RECENT | 0.23 | 0.44 | 1.36 | 1.17 | 1.36 | 2.04 | 0.98 | 0.99 |  | 0.10 |  |  | 1548.96 | 2546.16 | 1355.34 | 212.33 | 525.28 |  |  |  |  | 1.00 |
| BOOKPAIR[KB][st.prev_er_rth>=0.1843&st.prev_rng_atrd>=1.697] | rt50 | SPL | ALL | CANDIDATE-RECENT | 0.09 | 0.04 | 0.09 | 0.08 | 0.09 | 0.14 | 1.00 | 0.99 |  | 0.04 |  |  | 1543.44 | 2871.43 | 1350.51 | -283.06 | 1200.94 |  |  |  |  | 1.00 |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | d15 | MKT | SM | CANDIDATE-RECENT | 0.42 | 0.45 | 1.22 | 1.06 | 1.25 | 1.82 | 1.00 | 1.00 |  | 0.33 |  |  | 1441.78 | 2293.41 | 1261.56 | 663.43 | 692.54 |  |  |  |  | 0.99 |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | skip | SPL | ALL | CANDIDATE-RECENT | 0.37 | 0.63 | 0.10 | 0.09 | 0.30 | 0.70 | 0.99 | 1.00 |  | 0.05 | 0.11 | 0.12 | 1430.21 | 23587.34 | 1251.44 | 4189.53 | 13801.13 | -355.17 | 270.10 | 13648.24 | 13497.86 | 0.94 |
| PAIR[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301] | d15 | MKT | SM | CANDIDATE-RECENT | 0.59 | 0.21 | 0.76 | 0.66 | 0.81 | 1.50 | 0.97 | 0.98 |  | 0.20 |  |  | 1327.83 | 2859.94 | 1161.86 | 550.07 | 299.83 |  |  |  |  | 0.98 |
| PAIR[st.prev_ret_rth>=0.7105&st.days_since_trend<=1] | d15 | SPL | SM | CANDIDATE-RECENT | 0.37 | 0.37 | 1.12 | 0.97 | 1.15 | 2.24 | 1.00 | 1.00 |  | 0.38 |  |  | 1279.03 | 2754.30 | 1119.15 | 327.57 | 881.78 |  |  |  |  | 0.99 |
| TRIPLE[st.prev_ret_rth>=0.7105&st.prev_rng_atrd>=1.301&st.da | d15 | SPL | SM | CANDIDATE-RECENT | 0.19 | 0.17 | 1.12 | 0.97 | 1.15 | 2.24 | 1.00 | 1.00 |  | 0.38 |  |  | 1278.28 | 2754.40 | 1118.49 | 119.24 | 469.26 |  |  |  |  | 0.99 |
| BOOKPAIR[KB][st.days_since_trend<=0&st.prev_rng_atrd>=1.697] | z50 | MKT | asia | CANDIDATE-RECENT | 0.09 | 0.07 | 0.08 | 0.07 | 0.10 | 0.15 | 0.96 | 0.96 |  | 0.10 | 0.08 | 0.09 | 1171.11 | 2659.13 | 1024.72 | -403.67 | 212.20 | 2233.33 | 1922.71 | -12.16 | 560.05 | 1.00 |
| BOOKPAIR[KB][st.prev_trend_day==1&st.prev_rng_atrd>=1.301] | rt50 | MKT | KB | CANDIDATE-RECENT | 0.70 | 0.99 | 0.40 | 0.36 | 0.40 | 1.23 | 0.95 | 0.97 |  | 0.12 |  |  | 1131.07 | 2631.45 | 989.69 | -702.43 | 2373.20 |  |  |  |  | 1.00 |
| BOOKPAIR[KB][st.days_since_trend<=0&st.prev_rng_atrd>=1.301] | rt50 | MKT | ALL | CANDIDATE-RECENT | 0.09 | 0.11 | 0.05 | 0.05 | 0.05 | 0.16 | 0.95 | 0.96 |  | 0.02 |  |  | 1131.07 | 2631.45 | 989.69 | -702.43 | 2373.20 |  |  |  |  | 1.00 |
| ANY2of10[evt.failbrk_high.within30.ict_with,st.prev_ret_rth> | z25 | MKT | KB | CANDIDATE-RECENT | 0.86 | 1.29 | 0.64 | 0.60 | 1.02 | 1.43 | 0.97 | 1.00 |  | -0.04 | 0.65 | 0.67 | 1343.58 | 6046.80 | 922.60 | -899.15 | 3218.52 | 3085.86 | 2853.60 | -552.36 | 2889.00 | 0.86 |
| BOOKPAIR[KB][st.prev_rng_atrd>=1.301&st.prev_rng_atrd>=1.697 | rt50 | MKT | KB | CANDIDATE-RECENT | 0.90 | 0.32 | 0.50 | 0.46 | 0.50 | 1.27 | 0.96 | 1.00 |  | 0.03 |  |  | 1034.06 | 4486.68 | 904.81 | 851.69 | 901.16 |  |  |  |  | 1.00 |
| BOOKPAIR[KB][st.prev_rng_atrd>=1.301&st.prev_rng_atrd>=1.697 | rt50 | MKT | ALL | CANDIDATE-RECENT | 0.11 | 0.04 | 0.06 | 0.06 | 0.06 | 0.17 | 0.96 | 1.00 |  | 0.00 |  |  | 1034.06 | 4486.68 | 904.81 | 851.69 | 901.16 |  |  |  |  | 1.00 |

### 9d. The directive's own named cells (not selected) with a stack: skip, market base, last 6 months, shift / lag controls

| rule | act | base | scope | tier | PRE | X | L6M | HOLD | pcL6M | MDE | plc | shift | nbL6M | lag1 | lat1s | lat3s | stkL6M | stkMDE | stkHOLD | stkPRE | stkX | exL6M | exHOLD | exPRE | exX | lots |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| cal.fri_after12 | skip | MKT | HM | DEAD | 0.18 | -0.00 | 0.14 | 0.12 | 0.35 | 1.14 | 0.60 | 0.63 |  | -0.28 | 0.00 | 0.14 | 1028.09 | 4590.94 | 899.58 | 297.11 | 418.61 | -2205.58 | -1266.10 | 724.19 | -18.21 | 0.96 |
| cal.fri_after12 | skip | MKT | KB | DEAD | -0.21 | -0.09 | -0.14 | -0.10 | -0.08 | 0.70 | 0.49 | 0.53 |  | 0.15 | -0.15 | -0.14 | 1239.83 | 1299.74 | 1084.85 | -18.33 | -109.79 | 2703.40 | 2955.60 | -111.68 | -600.50 | 0.96 |
| cal.fri_after12 | skip | MKT | SM | DEAD | -0.40 | 0.31 | 0.39 | 0.34 | 0.43 | 1.06 | 0.87 | 0.00 |  | -0.35 | 0.43 | 0.41 | 354.39 | 1538.38 | 310.09 | -438.60 | 239.13 | 352.51 | 334.72 | -320.52 | 274.52 | 0.99 |
| cal.fri_after12 | skip | MKT | ST | DEAD | 0.10 | -0.02 | -0.19 | -0.10 | -0.06 | 0.79 | 0.30 | 0.26 |  | 0.37 | -0.21 | -0.21 | -583.55 | 3802.42 | -457.56 | -138.95 | -1100.78 | -1275.82 | -808.37 | 1375.48 | 1402.56 | 0.97 |
| cal.fri_after12 | skip | MKT | WT | DEAD | 0.03 | 0.01 | 0.01 | 0.05 | 0.07 | 0.43 | 0.42 | 0.59 |  | 0.04 | -0.01 | -0.00 | 1583.50 | 1705.79 | 1385.56 | 159.07 | 324.06 | 4719.69 | 4547.15 | 1102.83 | -334.04 | 0.96 |
| tm.block.0900_1000 | skip | MKT | ALL | DEAD | -0.24 | 0.24 | 0.02 | 0.03 | 0.44 | 1.16 | 0.95 | 1.00 |  | -0.22 | 0.05 | 0.04 | 580.49 | 27112.60 | 914.73 | -2785.55 | 1737.53 | 2368.05 | 4990.17 | 2728.30 | 696.13 | 0.89 |
| tm.block.0900_1000 | skip | MKT | HM | DEAD | -0.61 | -0.21 | -0.79 | -0.65 | -0.36 | 2.08 | 0.55 | 0.43 |  | -0.76 | -0.76 | -0.59 | -83.19 | 9642.75 | -1000.46 | -1799.78 | 825.47 | -6481.64 | -4717.47 | -3324.15 | -756.46 | 0.90 |
| tm.block.0900_1000 | skip | MKT | KB | DEAD | -0.57 | -0.05 | 1.04 | 1.00 | 1.36 | 1.35 | 0.95 | 0.99 |  | -0.01 | 0.94 | 0.91 | 6287.23 | 5922.99 | 5802.90 | -1376.45 | -713.29 | 9414.89 | 9030.46 | -1270.00 | -1675.96 | 0.89 |
| tm.block.0900_1000 | skip | MKT | PE | DEAD | -0.45 | -0.60 | 0.35 | 0.32 | 0.47 | 1.51 | 0.58 | 0.69 |  | 0.38 | 0.13 | 0.12 | 493.52 | 5603.90 | 491.62 | -502.66 | 361.14 | 2470.46 | 2867.33 | 2762.69 | -3114.00 | 0.89 |
| tm.block.0900_1000 | skip | MKT | SM | DEAD | -0.02 | -0.64 | -1.64 | -2.07 | -1.53 | 2.86 | 0.07 | 0.14 |  | 0.49 | -1.20 | -1.20 | -2559.77 | 6362.83 | -3241.28 | -51.92 | -1030.83 | -3640.38 | -3402.02 | 718.74 | -196.77 | 0.87 |
| tm.block.0900_1000 | skip | MKT | ST | DEAD | -0.07 | 0.36 | -0.37 | -0.32 | 0.19 | 2.02 | 0.60 | 0.85 |  | -0.29 | -0.26 | -0.57 | -1828.14 | 14406.91 | 226.72 | -535.44 | -387.64 | 2478.23 | 3127.23 | 3152.73 | 4255.76 | 0.86 |
| tm.block.0900_1000 | skip | MKT | WT | DEAD | 0.03 | 0.41 | -0.09 | -0.14 | 0.14 | 0.95 | 0.81 | 0.80 |  | -0.18 | 0.15 | 0.17 | -1729.17 | 5318.88 | -1364.76 | 1480.70 | 2682.69 | 371.70 | 51.20 | 2142.82 | 2854.51 | 0.88 |
| tm.day.CPINFP_morning | skip | MKT | ALL | DEAD | -0.20 | 0.32 | -0.09 | -0.14 | 0.09 | 0.58 | 0.49 | 0.49 |  | -0.10 | -0.05 | -0.01 | 949.63 | 21680.29 | -1967.85 | -868.30 | 3895.25 | 3443.67 | 3218.21 | 663.59 | -596.84 | 0.95 |
| tm.day.CPINFP_morning | skip | MKT | HM | DEAD | -0.04 | -0.20 | 0.10 | 0.18 | 0.33 | 1.30 | 0.81 | 0.65 |  | -0.43 | 0.12 | 0.11 | 963.99 | 7849.36 | 323.58 | 666.51 | -928.10 | -2250.18 | -1831.78 | 134.22 | -2881.74 | 0.95 |
| tm.day.CPINFP_morning | skip | MKT | KB | DEAD | -0.61 | 0.17 | 0.01 | 0.06 | 0.10 | 0.87 | 0.49 | 0.34 |  | -0.57 | -0.08 | -0.09 | 553.67 | 3091.23 | 683.53 | -1978.46 | 1072.74 | 2986.29 | 3379.97 | -2813.83 | 71.14 | 0.95 |
| tm.day.CPINFP_morning | skip | MKT | PE | DEAD | -0.32 | -0.08 | 0.06 | -0.08 | 0.10 | 0.76 | 0.42 | 0.60 |  | 0.21 | 0.16 | 0.25 | 249.34 | 4592.11 | -179.53 | -1088.71 | -478.50 | 2442.61 | 2344.03 | -66.19 | -4036.41 | 0.95 |
| tm.day.CPINFP_morning | skip | MKT | SM | DEAD | -0.35 | 0.12 | 0.44 | 0.05 | 0.65 | 2.30 | 0.73 | 0.73 |  | 1.40 | 1.00 | 1.46 | 486.25 | 3379.18 | 451.81 | 99.59 | -180.98 | -659.33 | 145.30 | 554.77 | 562.02 | 0.93 |
| tm.day.CPINFP_morning | skip | MKT | ST | DEAD | 0.05 | 0.81 | -0.58 | -0.66 | -0.37 | 1.33 | 0.10 | 0.16 |  | -0.06 | -0.51 | -0.50 | -627.30 | 10038.22 | -1245.01 | -506.01 | 2831.03 | -137.71 | -700.51 | 524.82 | 5220.07 | 0.94 |
| tm.day.CPINFP_morning | skip | MKT | WT | DEAD | 0.07 | 0.43 | -0.27 | -0.44 | -0.20 | 0.60 | 0.16 | 0.30 |  | -0.04 | -0.21 | -0.19 | -676.32 | 3945.91 | -2002.23 | 1938.77 | 1579.07 | 2417.33 | 1087.20 | 2873.80 | 920.81 | 0.95 |
| tm.day.FOMC_before14 | skip | MKT | ALL | DEAD | -0.00 | 0.03 | 0.12 | 0.15 | 0.18 | 0.24 | 0.99 | 1.00 |  | -0.12 | 0.15 | 0.14 | 4628.15 | 7790.41 | 5658.51 | -316.88 | 1030.24 | 5425.48 | 6225.79 | 93.30 | 947.80 | 0.98 |
| tm.day.FOMC_before14 | skip | MKT | HM | DEAD | -0.04 | 0.29 | 0.28 | 0.31 | 0.37 | 0.59 | 0.93 | 0.98 |  | 0.01 | 0.29 | 0.27 | 350.53 | 1810.91 | 689.54 | -383.95 | 919.32 | 428.45 | 717.77 | -573.57 | 1080.65 | 0.98 |
| tm.day.FOMC_before14 | skip | MKT | KB | DEAD | 0.01 | -0.05 | -0.18 | -0.21 | -0.16 | 0.24 | 0.20 | 0.31 |  | -0.28 | -0.18 | -0.18 | 455.65 | 1589.94 | 218.13 | 492.74 | -292.33 | -579.97 | -708.89 | 591.70 | -423.54 | 0.99 |
| tm.day.FOMC_before14 | skip | MKT | PE | DEAD | 0.21 | -0.11 | 0.16 | 0.24 | 0.17 | 0.32 | 0.81 | 0.72 |  | -0.14 | 0.17 | 0.16 | 307.38 | 749.73 | 483.34 | 415.55 | -252.39 | 296.12 | 483.49 | 546.89 | -244.59 | 0.99 |
| tm.day.FOMC_before14 | skip | MKT | SM | DEAD | 0.28 | 0.43 | 0.40 | 0.35 | 0.48 | 1.33 | 0.76 | 0.76 |  | -0.18 | 0.43 | 0.42 | 384.48 | 2017.92 | 336.42 | 474.73 | 647.29 | -1124.48 | -353.56 | 505.31 | 1349.09 | 0.97 |
| tm.day.FOMC_before14 | skip | MKT | ST | DEAD | -0.05 | 0.19 | 0.25 | 0.32 | 0.32 | 0.55 | 0.94 | 0.99 |  | 0.06 | 0.37 | 0.35 | 3183.21 | 5238.59 | 3168.14 | -943.47 | -45.84 | 3505.59 | 3383.25 | -1590.01 | 66.89 | 0.98 |
| tm.day.FOMC_before14 | skip | MKT | WT | DEAD | -0.01 | -0.02 | 0.03 | 0.10 | 0.06 | 0.14 | 0.66 | 0.61 |  | -0.11 | 0.08 | 0.04 | -53.11 | 995.35 | 762.94 | -372.48 | 54.18 | 1237.89 | 1849.06 | 503.72 | -503.32 | 0.98 |
| tm.day.FOMC_whole | skip | MKT | ALL | DEAD | -0.12 | 0.09 | 0.02 | -0.02 | 0.13 | 0.43 | 0.90 | 0.87 |  | -0.28 | 0.07 | 0.07 | 3745.63 | 16158.99 | 3889.55 | -1345.15 | 2030.91 | 5229.27 | 8406.40 | 1724.88 | 1078.73 | 0.97 |
| tm.day.FOMC_whole | skip | MKT | HM | DEAD | -0.08 | 0.23 | -0.10 | -0.15 | 0.10 | 0.44 | 0.57 | 0.65 |  | -0.52 | -0.08 | -0.09 | -893.79 | 6245.92 | -724.31 | -515.34 | 373.32 | -4137.20 | -2895.14 | -92.02 | -64.76 | 0.96 |
| tm.day.FOMC_whole | skip | MKT | KB | DEAD | -0.04 | -0.39 | -0.27 | -0.42 | -0.22 | 0.93 | 0.23 | 0.26 |  | -0.22 | -0.13 | -0.15 | -16.79 | 3849.29 | -736.94 | 629.76 | -756.64 | 2260.33 | 1871.59 | 214.88 | -1238.15 | 0.97 |
| tm.day.FOMC_whole | skip | MKT | PE | DEAD | 0.14 | 0.20 | 0.18 | 0.17 | 0.21 | 0.56 | 0.80 | 0.69 |  | -0.38 | 0.08 | 0.10 | 1303.79 | 2904.43 | 859.18 | -191.89 | 797.51 | 2772.13 | 2746.61 | 614.07 | -1783.93 | 0.96 |
| tm.day.FOMC_whole | skip | MKT | SM | DEAD | 0.21 | 0.85 | 0.41 | 0.53 | 0.52 | 0.77 | 0.67 | 0.65 |  | -0.59 | 0.47 | 0.46 | -137.25 | 2770.73 | 163.20 | 365.68 | 1078.82 | -1628.41 | -492.49 | 491.28 | 1792.39 | 0.96 |
| tm.day.FOMC_whole | skip | MKT | ST | DEAD | -0.20 | 0.45 | 0.12 | 0.16 | 0.27 | 0.98 | 0.79 | 0.91 |  | -0.26 | 0.27 | 0.36 | 3259.10 | 7998.62 | 2887.30 | -977.92 | 604.66 | 2589.76 | 2548.85 | -22.50 | 3116.16 | 0.96 |
| tm.day.FOMC_whole | skip | MKT | WT | DEAD | -0.06 | -0.04 | 0.04 | 0.08 | 0.10 | 0.28 | 0.78 | 0.70 |  | -0.01 | 0.16 | 0.08 | 230.57 | 2035.81 | 1441.13 | -655.45 | -66.76 | 3369.07 | 4606.40 | 290.72 | -724.85 | 0.96 |
| tm.edge.close_nypm_end1500.last10 | skip | MKT | HM | DEAD | -0.01 | -0.17 | 0.14 | 0.13 | 0.19 | 0.46 | 0.69 | 0.76 |  | -0.10 | 0.14 | 0.14 | 1069.46 | 1850.69 | 843.51 | 360.36 | -551.15 | 1121.41 | 866.50 | 140.22 | -502.89 | 0.99 |
| tm.edge.close_nypm_end1500.last10 | skip | MKT | KB | DEAD | 0.07 | -0.11 | -0.16 | -0.17 | -0.14 | 0.37 | 0.22 | 0.15 |  | -0.20 | -0.16 | -0.16 | -61.81 | 1085.30 | -234.64 | 113.63 | 104.45 | -1097.37 | -1160.31 | 206.85 | -25.83 | 0.99 |
| tm.edge.close_nypm_end1500.last10 | skip | MKT | PE | DEAD | 0.00 | -0.13 | 0.23 | 0.16 | 0.24 | 0.38 | 0.87 | 0.75 |  | -0.30 | 0.13 | 0.13 | 267.78 | 1164.83 | 234.31 | 90.97 | -417.11 | 250.78 | 227.66 | 161.92 | -402.72 | 0.99 |
| tm.edge.close_nypm_end1500.last10 | skip | MKT | SM | DEAD | -0.07 | 0.38 | 0.33 | 0.49 | 0.39 | 1.09 | 0.39 | 0.00 |  | 0.82 | 0.34 | 0.30 | 445.26 | 1246.74 | 722.55 | -216.87 | 478.29 | 442.45 | 759.51 | -67.63 | 523.79 | 0.98 |
| tm.edge.close_nypm_end1500.last10 | skip | MKT | ST | DEAD | 0.10 | 0.07 | 0.05 | 0.03 | 0.10 | 0.40 | 0.79 | 0.83 |  | -0.24 | -0.04 | 0.05 | 875.03 | 1700.08 | 418.41 | 604.55 | -156.52 | 1145.24 | 605.50 | 585.99 | -73.46 | 0.99 |
| tm.edge.close_nypm_end1500.last10 | skip | MKT | WT | DEAD | 0.11 | -0.19 | 0.01 | 0.01 | 0.03 | 0.27 | 0.38 | 0.41 |  | 0.01 | 0.01 | -0.00 | 462.52 | 898.62 | 404.70 | 320.74 | 274.98 | 1016.89 | 865.31 | 1246.03 | 192.78 | 0.99 |
| tm.edge.close_nypm_end1500.last20 | skip | MKT | HM | DEAD | 0.02 | -0.04 | 0.18 | 0.16 | 0.29 | 0.55 | 0.79 | 0.78 |  | -0.25 | 0.32 | 0.33 | 1474.58 | 2022.62 | 1197.99 | 469.47 | -61.66 | -1766.59 | -906.83 | 651.48 | -488.84 | 0.98 |
| tm.edge.close_nypm_end1500.last20 | skip | MKT | KB | DEAD | 0.14 | 0.21 | -0.11 | -0.13 | -0.08 | 0.46 | 0.33 | 0.33 |  | -0.23 | -0.11 | -0.11 | 23.59 | 1112.71 | -159.92 | 89.65 | 455.30 | -1012.37 | -1095.05 | 230.21 | 54.47 | 0.98 |
| tm.edge.close_nypm_end1500.last20 | skip | MKT | PE | DEAD | 0.06 | -0.05 | 0.47 | 0.38 | 0.50 | 0.53 | 0.97 | 0.90 |  | -0.37 | 0.37 | 0.36 | 494.58 | 1194.84 | 432.75 | -378.48 | -145.17 | 2048.56 | 2394.09 | 932.56 | -2651.46 | 0.97 |
| tm.edge.close_nypm_end1500.last20 | skip | MKT | SM | DEAD | 0.07 | 0.20 | 0.56 | 0.68 | 0.64 | 1.19 | 0.63 | 0.00 |  | 0.66 | 0.59 | 0.56 | 825.78 | 1514.05 | 1055.50 | 31.25 | 232.46 | -683.19 | 365.52 | 61.83 | 934.25 | 0.97 |
| tm.edge.close_nypm_end1500.last20 | skip | MKT | ST | DEAD | 0.01 | 0.31 | 0.03 | -0.04 | 0.10 | 0.56 | 0.71 | 0.62 |  | -0.23 | -0.07 | 0.03 | 915.70 | 2388.69 | 454.00 | 587.65 | 161.89 | 2169.50 | 1466.49 | 0.40 | 850.48 | 0.98 |
| tm.edge.close_nypm_end1500.last20 | skip | MKT | WT | DEAD | 0.07 | -0.15 | 0.04 | 0.05 | 0.07 | 0.32 | 0.44 | 0.39 |  | 0.10 | 0.03 | 0.02 | 925.04 | 1220.99 | 809.41 | 175.07 | 539.42 | 1470.86 | 1246.21 | 1055.90 | -17.95 | 0.98 |
| tm.edge.close_nypm_end1500.last30 | skip | MKT | HM | DEAD | -0.06 | -0.47 | 0.10 | 0.09 | 0.28 | 0.82 | 0.65 | 0.65 |  | -0.44 | 0.25 | 0.27 | 1118.41 | 2650.42 | 886.34 | 738.63 | -1109.56 | -2193.23 | -1320.60 | 968.13 | -1556.51 | 0.97 |
| tm.edge.close_nypm_end1500.last30 | skip | MKT | KB | DEAD | 0.23 | 0.38 | -0.32 | -0.29 | -0.29 | 0.54 | 0.12 | 0.12 |  | -0.09 | -0.32 | -0.32 | 98.76 | 1131.98 | 104.92 | 101.62 | 526.57 | 2387.00 | 2730.59 | -338.37 | 47.70 | 0.97 |
| tm.edge.close_nypm_end1500.last30 | skip | MKT | PE | DEAD | 0.16 | -0.23 | 0.21 | 0.15 | 0.25 | 0.56 | 0.65 | 0.59 |  | -0.39 | 0.11 | 0.10 | -153.17 | 1287.94 | -134.03 | -535.82 | -432.39 | 1314.50 | 1752.73 | 267.38 | -3013.84 | 0.96 |
| tm.edge.close_nypm_end1500.last30 | skip | MKT | SM | DEAD | 0.08 | 0.30 | 0.18 | 0.36 | 0.26 | 1.41 | 0.33 | 0.00 |  | 0.28 | 0.20 | 0.18 | 532.64 | 1684.06 | 799.01 | -72.47 | 379.94 | -967.42 | 126.17 | 21.19 | 1087.62 | 0.97 |
| tm.edge.close_nypm_end1500.last30 | skip | MKT | ST | DEAD | 0.08 | 0.38 | -0.22 | -0.27 | -0.11 | 0.79 | 0.26 | 0.38 |  | -0.34 | -0.33 | -0.22 | 474.12 | 2733.02 | 67.62 | 384.73 | 206.15 | -264.01 | -307.89 | 1869.09 | 2693.19 | 0.97 |
| tm.edge.close_nypm_end1500.last30 | skip | MKT | WT | DEAD | 0.17 | -0.20 | -0.02 | -0.01 | 0.03 | 0.41 | 0.26 | 0.21 |  | 0.03 | -0.04 | -0.04 | 1103.19 | 1614.11 | 965.29 | 581.48 | 587.73 | 3493.95 | 3496.25 | 1629.41 | 192.77 | 0.97 |
| tm.lunch.1130_1330 | skip | MKT | ALL | DEAD | -0.12 | 0.11 | -0.48 | -0.29 | -0.05 | 1.00 | 0.10 | 0.08 |  | 0.21 | -0.50 | -0.54 | -1788.38 | 16910.85 | 951.12 | 1375.69 | 2553.48 | 392.78 | 5388.53 | 8047.97 | 3284.00 | 0.86 |
| tm.lunch.1130_1330 | skip | MKT | HM | DEAD | 0.09 | 0.60 | -0.93 | -0.36 | -0.32 | 2.20 | 0.18 | 0.18 |  | 0.58 | -1.05 | -1.12 | 1146.76 | 8616.63 | 2527.54 | 755.64 | 2504.90 | -5650.33 | -1730.40 | -1249.49 | 1649.40 | 0.86 |
| tm.lunch.1130_1330 | skip | MKT | KB | DEAD | -0.31 | -0.09 | -0.43 | -0.22 | -0.20 | 1.60 | 0.35 | 0.28 |  | 0.51 | -0.39 | -0.37 | 693.67 | 4463.08 | 987.96 | -372.65 | -1197.70 | 1386.59 | 1850.80 | 167.51 | -1758.10 | 0.84 |
| tm.lunch.1130_1330 | skip | MKT | PE | DEAD | -0.07 | -0.28 | 0.30 | 0.28 | 0.48 | 1.79 | 0.51 | 0.43 |  | 0.42 | 0.20 | 0.18 | 557.49 | 4070.83 | 137.85 | -1404.51 | 93.45 | 2718.73 | 2677.47 | 1682.30 | -3196.19 | 0.85 |
| tm.lunch.1130_1330 | skip | MKT | ST | DEAD | -0.04 | -0.28 | -0.77 | -0.63 | -0.31 | 1.41 | 0.15 | 0.15 |  | -0.03 | -0.81 | -0.78 | -5729.75 | 8002.02 | -5017.76 | -904.50 | -2477.80 | -1513.98 | -2160.39 | 2899.27 | 2385.38 | 0.87 |
| tm.lunch.1130_1330 | skip | MKT | WT | DEAD | -0.13 | 0.11 | -0.48 | -0.26 | -0.29 | 0.85 | 0.03 | 0.03 |  | 0.01 | -0.60 | -0.64 | -42.56 | 4223.23 | 865.40 | 1584.80 | 1848.59 | 1910.67 | 2405.51 | 2157.26 | 1574.25 | 0.87 |
| tm.rel.CORE830.pre10 | skip | MKT | ALL | DEAD | 0.01 | 0.00 | -0.01 | -0.01 | -0.01 | 0.02 | 0.24 | 0.15 |  | 0.01 | -0.01 | -0.01 | -425.81 | 1260.40 | -372.59 | -416.32 | 117.97 | -414.22 | -367.30 | 43.57 | -8.16 | 1.00 |
| tm.rel.CORE830.pre10 | skip | MKT | KB | DEAD | 0.02 | 0.06 | 0.00 | 0.00 | 0.00 | 0.19 | 0.57 | 0.66 |  | 0.00 | 0.00 | -0.00 | -448.71 | 1256.39 | -392.62 | 0.00 | 0.00 | -450.47 | -396.77 | 11.49 | -131.24 | 1.00 |
| tm.rel.CORE830.pre10 | skip | MKT | PE | DEAD | 0.06 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.50 | 0.29 |  | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | 0.00 | -416.32 | 0.00 | 0.00 | 0.00 | -416.32 | 0.00 | 1.00 |

### 9e. Regime it works in (sessions and vol terciles where the whole slice gain is > 0 in both L6M and PRE u X'), eligible cells with a positive stack in all four windows

| rule | act | base | scope | regime | stk |
|--|--|--|--|--|--|
| st.15m.range_pos60>=0.3921 | u200 | SPL | ALL | asia,london | volT0,volT1,volT2 | 30715 |
| set.ahead20_set11_fresh | skip | SPL | ALL | asia,pre | volT0,volT1 | 30118 |
| set.ahead20_set11_fresh | skip | MKT | ALL | asia,pre | volT0,volT1 | 29834 |
| px.loc.SESS.sidedloc>=0.8 | u150 | MKT | ALL | asia,london,nyam | volT0 | 25280 |
| set.ahead20_set11_fresh | z25 | SPL | ALL | asia,pre | volT0,volT1 | 24279 |
| px.loc.SESS.premium | u150 | MKT | ALL | asia,london,nyam | volT0 | 24049 |
| px.wrong.priorclose>=50 | u150 | MKT | asia | asia | volT0,volT1,volT2 | 20696 |
| px.wrong.priorclose>=50 | u200 | SPL | asia | asia | volT0,volT1,volT2 | 20293 |
| set.ahead20_set11_fresh | z25 | MKT | ALL | asia,pre | volT0,volT1 | 19790 |
| px.wrong.priorclose>=50 | u200 | MKT | asia | asia | volT0,volT1,volT2 | 19213 |
| px.wrong.priorclose>=50 | u150 | MKT | ALL | asia,london,nyam,nypm | volT0,volT1,volT2 | 18704 |
| px.loc.SESS.sidedloc>=0.8 | u150 | SPL | ALL | asia,london,nyam | volT0 | 17781 |
| set.ahead20_set11_fresh | z50 | SPL | ALL | asia,pre | volT0,volT1 | 17517 |
| px.wrong.priorclose>=50 | u150 | SPL | asia | asia | volT0,volT1,volT2 | 16802 |
| st.1m.rng_exp1<=0.9489 | u150 | MKT | ALL | asia,nyam | volT0,volT1,volT2 | 15408 |
| set.ahead20_set11_fresh | z50 | MKT | ALL | asia,pre | volT0,volT1 | 14880 |
| px.loc.DEAL4H.premium | u200 | MKT | ALL | asia,london,pre,nyam,nypm | volT0,volT1,volT2 | 14788 |
| st.5m.er20>=0.3857 | u150 | MKT | asia | asia | volT0,volT1 | 12460 |
| st.open_drive5>=0.08545 | u150 | MKT | ALL | asia,nyam,nypm | volT0,volT1,volT2 | 12419 |
| px.wrong.priorclose>=50 | u150 | SPL | ALL | asia,london,nyam,nypm | volT0,volT1,volT2 | 11872 |
| st.1h.rsi14>=60.22 | u200 | SPL | ALL | asia,pre,nyam,nypm | volT0,volT1,volT2 | 11601 |
| st.5m.er20>=0.3857 | u150 | MKT | ALL | asia,nyam | volT0,volT2 | 10953 |
| st.1m.rng_exp1<=0.9489 | u150 | SPL | ALL | asia,nyam | volT0,volT1,volT2 | 10823 |
| st.f60_vs_med>=1.809 | d15 | SPL | ALL | asia,nyam,nypm | volT0,volT2 | 10697 |
| st.open_drive5>=0.08545 | u150 | SPL | ALL | asia,nyam,nypm | volT0,volT1,volT2 | 9814 |
| st.5m.adx14>=44.21 | u200 | SPL | ALL | asia,london,nyam,nypm | volT0,volT1,volT2 | 9210 |
| px.ext.5m.ema200>=5 | u200 | MKT | HM | asia,london,nyam | volT0,volT1,volT2 | 8569 |
| bk.vpin50>=0.2 | u200 | MKT | ALL | asia,london,nyam,nypm | volT0,volT1,volT2 | 8464 |
| px.ext.5m.ema200>=5 | u200 | SPL | HM | asia,london,nyam | volT0,volT1 | 8413 |
| st.5m.adx14>=34.82 | u200 | SPL | ALL | asia,london,nyam | volT0,volT2 | 8244 |
