## IRL / ERL Step C: where D7 gets hurt (JN05W2 losing exits, 43 months)

**Verdict line: of 1895 full stops (Stop / StopJoin / StopJoinFallback), 4.3% were internal-level-only sweeps followed by a recovery of at least the risk within 30 min (6.8% within 60 min), and 5.8% were external-level sweeps followed by recovery within 60 min: SMALL, so the proposed stop-placement changes are not pursued from this table; recovery after a stop-out is higher when the swept level was internal-only (rec60 0.54) than external (0.34), in the direction of the claim, but descriptive only.**
A losing exit counts as "taken by a sweep" if a headline sweep event (fade direction = trade side) confirms within 15 min after the exit with the exit price inside the poke zone (level to poke extreme +-1 pt). ext = the swept level is external to at least one of the 13 ranges; int_only = tagged internal only. Recovery = price came back from the exit price toward/through the entry by at least the original risk (>= max(risk,1pt)) within 30/60 min (1m highs/lows). Descriptive only; the stop-placement tests (beyond the nearest external level within 1.25x the stop distance, lots reduced; no entry when the stop sits just inside an unswept internal level) need the exact engine hook (W-CF3) and are NOT run here.

| group | n losers | share swept | ext | int only | recovered 30m | recovered 60m | rec60 if swept | rec60 if int-only | rec60 if ext | sum loss $ |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL losers | 11135 | 0.266 | 0.106 | 0.159 | 0.295 | 0.415 | 0.458 | 0.538 | 0.338 | -16032286 |
| book A7 | 553 | 0.322 | 0.193 | 0.128 | 0.137 | 0.233 | 0.303 | 0.408 | 0.234 | -587025 |
| book H7 | 545 | 0.316 | 0.167 | 0.149 | 0.217 | 0.319 | 0.360 | 0.444 | 0.286 | -878226 |
| book K7 | 3981 | 0.257 | 0.093 | 0.165 | 0.296 | 0.416 | 0.448 | 0.511 | 0.336 | -3804342 |
| book M7 | 2323 | 0.227 | 0.079 | 0.149 | 0.325 | 0.455 | 0.489 | 0.557 | 0.361 | -2238420 |
| book O7 | 283 | 0.194 | 0.035 | 0.159 | 0.537 | 0.622 | 0.800 | 0.844 | 0.600 | -195288 |
| book P7 | 2806 | 0.277 | 0.102 | 0.175 | 0.313 | 0.438 | 0.497 | 0.574 | 0.365 | -6526100 |
| book U7 | 644 | 0.348 | 0.214 | 0.134 | 0.191 | 0.303 | 0.406 | 0.488 | 0.355 | -1802886 |
| exit BookLock | 104 | 0.183 | 0.019 | 0.163 | 0.529 | 0.596 | 0.526 | 0.529 | 0.500 | -100118 |
| exit EarlyCut | 2637 | 0.306 | 0.114 | 0.192 | 0.228 | 0.351 | 0.409 | 0.471 | 0.303 | -2852769 |
| exit StackCut | 291 | 0.402 | 0.285 | 0.117 | 0.203 | 0.309 | 0.444 | 0.412 | 0.458 | -266336 |
| exit StateCut | 6070 | 0.220 | 0.070 | 0.150 | 0.360 | 0.488 | 0.540 | 0.616 | 0.376 | -8937875 |
| exit Stop | 859 | 0.338 | 0.185 | 0.153 | 0.180 | 0.270 | 0.352 | 0.458 | 0.264 | -1248414 |
| exit StopJoin | 635 | 0.365 | 0.186 | 0.180 | 0.198 | 0.307 | 0.384 | 0.404 | 0.364 | -1476328 |
| exit StopJoinFallback | 401 | 0.382 | 0.239 | 0.142 | 0.097 | 0.202 | 0.314 | 0.404 | 0.260 | -1094865 |
| exit TimeBlock | 121 | 0.000 | 0.000 | 0.000 | 0.455 | 0.479 | nan | nan | nan | -47263 |