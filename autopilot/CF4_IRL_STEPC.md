## IRL / ERL Step C: where D7 gets hurt (JN05W2 losing exits, 43 months)

**Verdict line: of 1895 full stops (Stop / StopJoin / StopJoinFallback), 4.2% were internal-level-only sweeps followed by a recovery of at least the risk within 30 min (6.6% within 60 min), and 5.8% were external-level sweeps followed by recovery within 60 min: SMALL, so the proposed stop-placement changes are not pursued from this table; recovery after a stop-out is higher when the swept level was internal-only (rec60 0.53) than external (0.34), in the direction of the claim, but descriptive only.**
A losing exit counts as "taken by a sweep" if a headline sweep event (fade direction = trade side) confirms within 15 min after the exit with the exit price inside the poke zone (level to poke extreme +-1 pt). ext = the swept level is external to at least one of the 13 ranges; int_only = tagged internal only. Recovery = price came back from the exit price toward/through the entry by at least the original risk (>= max(risk,1pt)) within 30/60 min (1m highs/lows). Descriptive only; the stop-placement tests (beyond the nearest external level within 1.25x the stop distance, lots reduced; no entry when the stop sits just inside an unswept internal level) need the exact engine hook (W-CF3) and are NOT run here.

| group | n losers | share swept | ext | int only | recovered 30m | recovered 60m | rec60 if swept | rec60 if int-only | rec60 if ext | sum loss $ |
|---|---|---|---|---|---|---|---|---|---|---|
| ALL losers | 11135 | 0.263 | 0.106 | 0.157 | 0.288 | 0.405 | 0.455 | 0.534 | 0.338 | -16032286 |
| book A7 | 553 | 0.316 | 0.192 | 0.125 | 0.127 | 0.217 | 0.297 | 0.391 | 0.236 | -587025 |
| book H7 | 545 | 0.312 | 0.167 | 0.145 | 0.207 | 0.308 | 0.353 | 0.430 | 0.286 | -878226 |
| book K7 | 3981 | 0.255 | 0.092 | 0.163 | 0.289 | 0.406 | 0.445 | 0.509 | 0.334 | -3804342 |
| book M7 | 2323 | 0.224 | 0.078 | 0.146 | 0.317 | 0.447 | 0.486 | 0.550 | 0.365 | -2238420 |
| book O7 | 283 | 0.194 | 0.035 | 0.159 | 0.534 | 0.618 | 0.800 | 0.844 | 0.600 | -195288 |
| book P7 | 2806 | 0.274 | 0.100 | 0.174 | 0.307 | 0.430 | 0.495 | 0.571 | 0.365 | -6526100 |
| book U7 | 644 | 0.346 | 0.214 | 0.132 | 0.186 | 0.297 | 0.408 | 0.494 | 0.355 | -1802886 |
| exit BookLock | 104 | 0.173 | 0.019 | 0.154 | 0.510 | 0.577 | 0.500 | 0.500 | 0.500 | -100118 |
| exit EarlyCut | 2637 | 0.303 | 0.113 | 0.190 | 0.223 | 0.345 | 0.405 | 0.467 | 0.301 | -2852769 |
| exit StackCut | 291 | 0.402 | 0.285 | 0.117 | 0.199 | 0.302 | 0.444 | 0.412 | 0.458 | -266336 |
| exit StateCut | 6070 | 0.218 | 0.069 | 0.149 | 0.351 | 0.477 | 0.537 | 0.612 | 0.378 | -8937875 |
| exit Stop | 859 | 0.334 | 0.184 | 0.150 | 0.175 | 0.262 | 0.348 | 0.450 | 0.266 | -1248414 |
| exit StopJoin | 635 | 0.361 | 0.184 | 0.176 | 0.194 | 0.302 | 0.384 | 0.402 | 0.368 | -1476328 |
| exit StopJoinFallback | 401 | 0.382 | 0.239 | 0.142 | 0.097 | 0.202 | 0.314 | 0.404 | 0.260 | -1094865 |
| exit TimeBlock | 121 | 0.000 | 0.000 | 0.000 | 0.455 | 0.479 | nan | nan | nan | -47263 |