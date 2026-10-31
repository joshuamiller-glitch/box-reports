# DS3_P70_POLICY - the `pct >= 0.7 take` policy line scored on the Sunday composite at live lots, DRAWDOWN FIRST (SX-1, 2026-10-31). POST-HOC labels, no PASS claim
Research only. Masks capped 20260206, UNTOUCHED never read. Prereg `l2vast/ds3/prereg/SX1_prereg.md` sha256 d8c51a873dd5709d3ce31fd468717bd026f428d43c554e476d5a6bdfbfcbed05 (DECISIONS.md before any scored cell; dead_lookup first: the plain take-at-70% is not an exact DEAD_CELLS entry, one partial hit RE5 EXP1 profit fixed F7_take_p70 DEAD; append_cells after). Engine = DS3_ONE_CONVENTION (`oneconv/oc_lib.py`), Sunday composite `COMP|s0.25|k670|off` (split 70/30 incl. K6, PE 45-s, zone skip, Asia-stop cut, ER sizer on all six books, A6 = PB7, parity stop), live lots K6 2 / P6 7 / U6 4 / H6 4 Asia + 2 NY-AM / M6 2 / A6 1, no combined lock (lock-free headline), research/live as that page. Code `l2vast/ds3/code/sx1/` (p70lib.py, run_main.py, run_plc.py, run_er.py, an_p70.py, diag.py, tie.py, val_jt.py, mk_p70_md.py); results `l2vast/ds3/out/sx1/`.

## PLAIN SENTENCES
**Not RISK-KEEP.** The `pct >= 0.7 take` line (exit the whole position at the first 10-second close with 70% of the way to target reached) applied to K6, P6, U6, M6 and A6 on the Sunday composite cuts the composite's maxDD only where it is already large and not in the recent windows: ALL 149 weeks -15% (241.2k to 205.7k), PRE -15%, but L3M +22%, L6M +14%, HOLD +3%, X' +24% (negative = shallower, positive = deeper). It costs 6.2k/wk of the composite's 22.3k (ALL, -28%; L6M -9.7k, inside its 12.5k MDE; ALL -6.2k, beyond its 5.7k MDE). Calmar (mean/maxDD) in L6M goes 1.80 to 1.20, in PRE 0.10 to 0.08. EQUAL-RISK (lots re-scaled so worst-20 matches the composite) the policy still loses 4.8k/wk ALL (5.4k PRE). Against the same-volume random skip/size-cut placebo (200 draws) it does not beat chance on maxDD in any window (ALL-window rank 0.41, bar 0.95; the pooled placebo's median maxDD change is -20%, i.e. a random cut of the same volume does better) and in PRE, ALL and X' gives up more mean than the placebo does for the same exposure cut (less only in the three recent windows, where any removed exposure removes winners). The ledger shows M-basis gains for p70 only because the hold arm is charged the 1.4-4.3 pt limit-target fill correction; on the composite engine the take loses mean on every basis (M -5.1k, N -6.2k, LIVE-CAL -6.2k per week, ALL windows). **A D6 policy line `profit K6/P6/U6/M6/A6 * pct >= 0.7 take` would shorten drawdowns in PRE and nowhere else, at about a quarter of the mean; on this evidence it is not worth a slot.**

Definition (read this before the numbers). The 'pct >= 0.70 take' is NOT a percentile rank. In THP_POLICY.txt (v2, 2026-10-30) the line is `profit <book> * pct >= 0.7 take`, with `pct` the D6 legal feature = the share of the way from the entry fill to the target already travelled (favourable move / target distance, 60 pt for most books, 45 pt WT); DS3_L2SET_PROFIT scores it as `REF|p70_take_always`: 'take the whole position at the first 10-s close with pct >= 0.7, measured exit 0.995 pt, vs hold-to-bracket'. Active plain lines exist for S6, W6, K6, U6, P6, A6, N6, M6; the H6 line is commented `NOT ACTIVE` (HM candidate cell is p70never); MA6 is DEAD. The thick-book `curDepthRel` variants are not scored. **Literal reading scored (headline, `polA`): the take on the five composite books that carry the active line (K6=KB, P6=PE, U6=SM, M6=MV, A6=PB7); variant `polH` adds H6 (HM), i.e. all six composite books.** Ambiguities I resolved: (i) whole position, not partial; (ii) the first 10-s close after entry (THL2 grid, 10-s clock, price of the second before the label, 99.5% tie to the stored rows) and before the bracket exit (bracket wins ties); (iii) the target distance is the book's own (60 / 45 pt) measured from the leg-1 entry price; (iv) a 70/30 add that has not filled at the trigger is cancelled, a filled add exits with leg 1 (same rule as the joint kernel, which my overlay reproduces to the last decimal on KB); (v) the market-exit cost 0.995 pt plus the engine fee 0.242; (vi) the stored L2SP rows only fire where L2 coverage exists (`pl == 1`); a live D6 line does not need L2, so I take the price rule for every trade (fires on 55% of trades; on the 24,701 trades where the stored stream fires, mine fires on 99.99%, same second on 90.8%, earlier on 9.2%).

## 1. DRAWDOWN FIRST, headline basis N (= DS3_ONE_CONVENTION engine), policy `polA`, $k per week, windows recent-first
Rows: as-is stack (`ASIS|off`, market entries, no D6 rules, join 2.45, same lots), the Sunday composite, and the composite with the take. maxDD = weekly-cumulative peak-to-trough from 0; worst-20 = sum of the 20 lowest weeks (`*` = window has fewer than 20 weeks, so worst-20 is the whole-window sum and is degenerate: read the worst-5 change in table 2 there); weekly SD = sample SD; Calmar = mean/maxDD; ratio = mean/|worst-20| (n/a when worst-20 >= 0).

| window (weeks) | maxDD $k as-is / composite / POLICY | worst-20 $k as-is / composite / POLICY | weekly SD $k as-is / composite / POLICY | Calmar (mean/maxDD) as-is / composite / POLICY | mean / |worst-20| as-is / composite / POLICY |
|---|---|---|---|---|---|
| L3M (14) * | 88.0 / 21.4 / **26.1** | 170.1 / 481.7 / **357.9** | 45.5 / 44.7 / **43.3** | 0.14 / 1.61 / **0.98** | - / - / **-** |
| L6M (28) | 88.0 / 22.9 / **26.1** | 58.0 / 371.0 / **226.1** | 43.9 / 42.7 / **39.3** | 0.25 / 1.80 / **1.20** | - / - / **-** |
| HOLD (32) | 144.2 / 97.0 / **100.3** | -187.1 / 136.5 / **8.3** | 53.8 / 51.8 / **47.1** | 0.15 / 0.40 / **0.29** | 0.12 / - / **-** |
| PRE (75) | 162.0 / 241.2 / **205.7** | -810.6 / -875.2 / **-798.7** | 50.4 / 55.7 / **46.9** | 0.11 / 0.10 / **0.08** | 0.02 / 0.03 / **0.02** |
| X' (44) | 316.5 / 120.5 / **149.4** | -572.1 / -419.6 / **-431.7** | 29.0 / 32.6 / **31.8** | -0.01 / 0.07 / **0.04** | -0.01 / 0.02 / **0.01** |
| ALL (149) | 316.5 / 241.2 / **205.7** | -1161.1 / -1098.1 / **-1006.1** | 47.2 / 50.3 / **44.1** | 0.04 / 0.09 / **0.08** | 0.01 / 0.02 / **0.02** |

### Table 2 - same-lot change and equal-risk change (headline basis N, policy `polA`)
Same-lot: percentage change in maxDD and in the worst-20 loss at identical lots (every risk change is signed so that + = worse/deeper, - = better/shallower). EQUAL-RISK: per window, scale s with s x worst-20(policy) = worst-20(composite) (lots re-scaled; engine-route check below), equal-risk mean change = s x mean(policy) - mean(composite). Mean change in $k/wk with MDE (2.8 x SE of the paired weekly delta) in brackets, `*` = beyond MDE.

| window | mean $k/wk as-is / composite / POLICY | change vs composite (MDE 2.8 SE) | same-lot change in maxDD (+ deeper) | same-lot change in worst-20 loss (+ worse) | worst-5 loss change (+ worse) | EQUAL-RISK scale s (worst-20 matched) | EQUAL-RISK mean change $k/wk |
|---|---|---|---|---|---|---|---|
| L3M | 12.2 / 34.4 / **25.6** | -8.8 (22.5) | +22% (21.4 to 26.1) | n/a (composite worst-20 sum >= 0) | +20% | n/a | n/a |
| L6M | 21.7 / 41.1 / **31.5** | -9.7 (12.5) | +14% (22.9 to 26.1) | n/a (composite worst-20 sum >= 0) | +33% | n/a | n/a |
| HOLD | 21.9 / 38.6 / **29.0** | -9.6 (11.2) | +3% (97.0 to 100.3) | n/a (composite worst-20 sum >= 0) | -5% | n/a | n/a |
| PRE | 18.6 / 23.1 / **16.2** | -6.9 (8.9) | -15% (241.2 to 205.7) | -9% | -24% | 1.10 | -5.4 |
| X' | -3.4 / 8.0 / **5.6** | -2.3 (8.8) | +24% (120.5 to 149.4) | +3% | +5% | 0.97 | -2.5 |
| ALL | 13.1 / 22.3 / **16.0** | -6.2 (5.7)* | -15% (241.2 to 205.7) | -8% | -14% | 1.09 | -4.8 |

Engine-route check of the equal-risk scaling (unrounded lots, multiplier route `mer_fn` x s, ALL window, basis N): the scaled policy's worst-20 lands on the composite's to the dollar (-1,096,273 vs -1,096,273) and its mean equals s x mean to $1; the engine is linear in the lot multiplier, so the linear rescale in Table 2 is the engine answer (rounded-lot composite used for the table; `p70_er_engine.csv`).

### Where the loss sits (basis N, `polA`; fires = share of composite rows that hit 70% of target before the bracket)
| book | composite rows | take applies | fired | fire rate | ALL mean $k/wk composite to policy (change) | PRE mean composite to policy (change) |
|---|---|---|---|---|---|---|
| K6 | 4,473 | yes | 2,462 | 55% | 2.9 to 2.0 (-0.96) | 3.7 to 2.8 (-0.88) |
| P6 | 3,870 | yes | 2,138 | 55% | 12.9 to 8.3 (-4.56) | 11.9 to 7.1 (-4.75) |
| U6 | 1,273 | yes | 750 | 59% | 1.8 to 1.7 (-0.07) | 2.3 to 2.2 (-0.09) |
| H6 | 3,363 | no (line not active) | 0 | 0% | 2.5 to 2.6 (+0.06) | 2.0 to 2.2 (+0.15) |
| M6 | 4,397 | yes | 2,415 | 55% | 0.9 to 0.3 (-0.58) | 1.8 to 0.7 (-1.05) |
| A6 | 14,079 | yes | 7,734 | 55% | 1.2 to 1.1 (-0.12) | 1.5 to 1.1 (-0.31) |

P6 (PE, 7 lots, NY-AM/NY-PM confirmation entries) carries about three quarters of the lost mean; the take exits the winners that were going to the target 18 pt early and removes few stops (a trade that reached 70% and then reversed is the only gain). H6 moves by +0.1k only through the shared lock engine (the take is not applied there).

## 2. The same table on the other two bases (the p70 gain on M is the target-fill artefact; N and LIVE-CAL beside)
### Basis M (target-fill correction on; stop parity), policy `polA`

| window (weeks) | maxDD $k as-is / composite / POLICY | worst-20 $k as-is / composite / POLICY | weekly SD $k as-is / composite / POLICY | Calmar (mean/maxDD) as-is / composite / POLICY | mean / |worst-20| as-is / composite / POLICY |
|---|---|---|---|---|---|
| L3M (14) * | 97.7 / 22.4 / **26.1** | -52.7 / 445.9 / **357.2** | 44.4 / 45.0 / **43.2** | -0.04 / 1.42 / **0.98** | -0.07 / - / **-** |
| L6M (28) | 97.7 / 24.2 / **26.1** | -219.8 / 336.2 / **225.9** | 41.2 / 41.8 / **39.2** | 0.07 / 1.61 / **1.20** | 0.03 / - / **-** |
| HOLD (32) | 155.3 / 100.2 / **100.3** | -438.9 / 102.2 / **8.1** | 51.0 / 51.0 / **47.1** | 0.05 / 0.36 / **0.29** | 0.02 / - / **-** |
| PRE (75) | 195.8 / 244.5 / **206.1** | -971.5 / -884.7 / **-798.8** | 47.9 / 55.3 / **46.9** | 0.05 / 0.09 / **0.08** | 0.01 / 0.02 / **0.02** |
| X' (44) | 408.2 / 124.1 / **149.4** | -620.4 / -427.9 / **-431.7** | 28.5 / 32.5 / **31.8** | -0.02 / 0.06 / **0.04** | -0.01 / 0.02 / **0.01** |
| ALL (149) | 408.2 / 244.5 / **206.1** | -1281.3 / -1108.1 / **-1006.1** | 44.4 / 49.8 / **44.1** | 0.01 / 0.09 / **0.08** | 0.00 / 0.02 / **0.02** |

| window | mean $k/wk as-is / composite / POLICY | change vs composite (MDE 2.8 SE) | same-lot change in maxDD (+ deeper) | same-lot change in worst-20 loss (+ worse) | worst-5 loss change (+ worse) | EQUAL-RISK scale s (worst-20 matched) | EQUAL-RISK mean change $k/wk |
|---|---|---|---|---|---|---|---|
| L3M | -3.8 / 31.9 / **25.5** | -6.3 (22.8) | +17% (22.4 to 26.1) | n/a (composite worst-20 sum >= 0) | -13% | n/a | n/a |
| L6M | 6.9 / 38.9 / **31.4** | -7.5 (12.2) | +8% (24.2 to 26.1) | n/a (composite worst-20 sum >= 0) | +18% | n/a | n/a |
| HOLD | 7.8 / 36.4 / **28.9** | -7.5 (11.0) | +0% (100.2 to 100.3) | n/a (composite worst-20 sum >= 0) | -7% | n/a | n/a |
| PRE | 9.3 / 22.0 / **16.1** | -5.9 (8.8) | -16% (244.5 to 206.1) | -10% | -25% | 1.11 | -4.1 |
| X' | -6.5 / 7.4 / **5.6** | -1.8 (8.8) | +20% (124.1 to 149.4) | +1% | +5% | 0.99 | -1.8 |
| ALL | 4.5 / 21.1 / **16.0** | -5.1 (5.6) | -16% (244.5 to 206.1) | -9% | -15% | 1.10 | -3.5 |

### Basis LIVE-CAL (target correction 0, stop 2.45 every row), policy `polA`

| window (weeks) | maxDD $k as-is / composite / POLICY | worst-20 $k as-is / composite / POLICY | weekly SD $k as-is / composite / POLICY | Calmar (mean/maxDD) as-is / composite / POLICY | mean / |worst-20| as-is / composite / POLICY |
|---|---|---|---|---|---|
| L3M (14) * | 88.0 / 23.6 / **28.1** | 170.1 / 473.3 / **341.1** | 45.5 / 44.4 / **43.4** | 0.14 / 1.43 / **0.87** | - / - / **-** |
| L6M (28) | 88.0 / 24.0 / **28.1** | 58.0 / 356.5 / **202.7** | 43.9 / 42.4 / **39.3** | 0.25 / 1.68 / **1.08** | - / - / **-** |
| HOLD (32) | 144.2 / 103.0 / **106.0** | -187.1 / 118.5 / **-18.1** | 53.8 / 51.6 / **47.2** | 0.15 / 0.36 / **0.26** | 0.12 / - / **1.53** |
| PRE (75) | 162.0 / 250.2 / **217.2** | -810.6 / -903.3 / **-825.6** | 50.4 / 55.8 / **47.0** | 0.11 / 0.09 / **0.07** | 0.02 / 0.02 / **0.02** |
| X' (44) | 316.5 / 124.8 / **157.7** | -572.1 / -435.6 / **-447.7** | 29.0 / 32.7 / **31.9** | -0.01 / 0.06 / **0.03** | -0.01 / 0.02 / **0.01** |
| ALL (149) | 316.5 / 250.2 / **217.2** | -1161.1 / -1126.4 / **-1029.2** | 47.2 / 50.3 / **44.1** | 0.04 / 0.08 / **0.07** | 0.01 / 0.02 / **0.01** |

| window | mean $k/wk as-is / composite / POLICY | change vs composite (MDE 2.8 SE) | same-lot change in maxDD (+ deeper) | same-lot change in worst-20 loss (+ worse) | worst-5 loss change (+ worse) | EQUAL-RISK scale s (worst-20 matched) | EQUAL-RISK mean change $k/wk |
|---|---|---|---|---|---|---|---|
| L3M | 12.2 / 33.8 / **24.4** | -9.4 (21.8) | +19% (23.6 to 28.1) | n/a (composite worst-20 sum >= 0) | +45% | n/a | n/a |
| L6M | 21.7 / 40.2 / **30.3** | -10.0 (12.2) | +17% (24.0 to 28.1) | n/a (composite worst-20 sum >= 0) | +29% | n/a | n/a |
| HOLD | 21.9 / 37.6 / **27.7** | -9.9 (10.9) | +3% (103.0 to 106.0) | n/a (composite worst-20 sum >= 0) | -5% | n/a | n/a |
| PRE | 18.6 / 21.9 / **15.1** | -6.8 (9.0) | -13% (250.2 to 217.2) | -9% | -24% | 1.09 | -5.4 |
| X' | -3.4 / 7.2 / **5.0** | -2.2 (8.9) | +26% (124.8 to 157.7) | +3% | +5% | 0.97 | -2.4 |
| ALL | 13.1 / 21.2 / **15.0** | -6.2 (5.7)* | -13% (250.2 to 217.2) | -9% | -15% | 1.09 | -4.8 |

Reading across bases: the composite itself changes with the basis (M charges target exits 1.4-4.3 pt, LIVE-CAL charges every stop 2.45 pt), the policy barely does (it exits at market: 0.995 pt), so the policy's mean cost is smallest on M exactly because M makes the hold arm worse. Even there it loses mean in every window, adds maxDD in L3M, L6M and X' and leaves HOLD level.

## 3. Variant `polH`: the take on all six composite books (H6 added), basis N

| window | mean $k/wk as-is / composite / POLICY | change vs composite (MDE 2.8 SE) | same-lot change in maxDD (+ deeper) | same-lot change in worst-20 loss (+ worse) | worst-5 loss change (+ worse) | EQUAL-RISK scale s (worst-20 matched) | EQUAL-RISK mean change $k/wk |
|---|---|---|---|---|---|---|---|
| L3M | 12.2 / 34.4 / **21.0** | -13.4 (22.7) | +17% (21.4 to 25.1) | n/a (composite worst-20 sum >= 0) | +61% | n/a | n/a |
| L6M | 21.7 / 41.1 / **27.0** | -14.2 (12.4)* | +10% (22.9 to 25.1) | n/a (composite worst-20 sum >= 0) | +50% | n/a | n/a |
| HOLD | 21.9 / 38.6 / **24.6** | -14.0 (11.1)* | +11% (97.0 to 108.1) | n/a (composite worst-20 sum >= 0) | +1% | n/a | n/a |
| PRE | 18.6 / 23.1 / **15.8** | -7.3 (9.3) | -10% (241.2 to 217.1) | -12% | -25% | 1.14 | -5.0 |
| X' | -3.4 / 8.0 / **5.7** | -2.3 (9.6) | +28% (120.5 to 154.2) | +7% | +8% | 0.94 | -2.6 |
| ALL | 13.1 / 22.3 / **14.9** | -7.3 (6.0)* | -10% (241.2 to 217.1) | -9% | -16% | 1.09 | -5.9 |

## 4. Placebo: same-volume random skips and random 50% size cuts (200 draws per policy per basis; 100 skips + 100 cuts)
Volume = lot-seconds of exposure (lots x seconds held) of the composite rows; the policy removes 19.5% of it (`polA`; `polH` 21.9%) by ending trades early, each placebo draw removes the same share by skipping random trades (engine zone-skip route) or halving random trades' lots (engine multiplier route, integer half-up min 1, realised share 19.5% / 21.9%). Statistic = the change in maxDD (+ = deeper) and in the worst-20 loss in each window; rank = share of placebo draws that cut maxDD LESS than the policy does (bar 0.95 = the policy beats 95% of draws); the 95th-percentile column is the placebo's best-case 5% tail of the change (most negative values are best).
### Basis N = ONE_CONVENTION (target correction 0, stop parity 1.28/2.45), policy `polA`

| window | POLICY maxDD change (+ deeper) | random skip: median (95th pct), rank | random 50% size cut: median (95th pct), rank | pooled 200 draws: rank | POLICY worst-20 loss change vs placebo median (+ worse) | POLICY mean change vs placebo median ($k/wk) |
|---|---|---|---|---|---|---|
| L3M | +22% | +99% (-12%), 0.84 | +83% (-14%), 0.85 | 0.84 | n/a | -8.8 vs -12.7 |
| L6M | +14% | +91% (-11%), 0.87 | +69% (-14%), 0.86 | 0.86 | n/a | -9.7 vs -11.6 |
| HOLD | +3% | -20% (-49%), 0.15 | -19% (-45%), 0.10 | 0.12 | n/a | -9.6 vs -10.5 |
| PRE | -15% | -7% (-34%), 0.67 | -31% (-47%), 0.14 | 0.41 | -9% vs -8% | -6.9 vs -4.5 |
| X' | +24% | -6% (-47%), 0.16 | -2% (-36%), 0.14 | 0.15 | +3% vs -7% | -2.3 vs -1.9 |
| ALL | -15% | -7% (-32%), 0.68 | -30% (-43%), 0.15 | 0.41 | -8% vs -8% | -6.2 vs -5.1 |

### Basis M (target-fill correction on; stop parity), policy `polA` (pooled 200 draws; ALL and PRE)

| window | POLICY maxDD change (+ deeper) | placebo median change (best-5% tail) | rank | POLICY mean change vs placebo median ($k/wk) |
|---|---|---|---|---|
| PRE | -16% | -22% (-44%) | 0.32 | -5.9 vs -4.3 |
| ALL | -16% | -21% (-42%) | 0.33 | -5.1 vs -4.7 |
| L6M | +8% | +74% (-23%) | 0.87 | -7.5 vs -10.7 |

### Basis LIVE-CAL (target correction 0, stop 2.45 every row), policy `polA` (pooled 200 draws; ALL and PRE)

| window | POLICY maxDD change (+ deeper) | placebo median change (best-5% tail) | rank | POLICY mean change vs placebo median ($k/wk) |
|---|---|---|---|---|
| PRE | -13% | -23% (-46%) | 0.34 | -6.8 vs -4.7 |
| ALL | -13% | -23% (-46%) | 0.35 | -6.2 vs -5.1 |
| L6M | +17% | +86% (-28%) | 0.82 | -10.0 vs -10.9 |

Placebo reading: in PRE and ALL a random skip or size cut of the same volume cuts maxDD by about as much as the take or more (pooled rank 0.40 on N PRE, 0.42 ALL; the size-cut placebo cuts PRE maxDD by 31% at median, the skip placebo 7%), in HOLD and X' the placebo cuts it (HOLD -20% median) or leaves it level while the take does not (HOLD +3%, X' +24%), and in L3M/L6M every draw makes the small 21-23k maxDD deeper (random removal of winners from a smooth run) while the take deepens it less (rank 0.85-0.87, short of 0.95). The take therefore carries no drawdown skill beyond the volume it removes, and it gives up slightly more mean than the placebo for it in PRE, ALL and X' (the placebo is costlier only in the three recent windows, where removing exposure removes winners).

## 5. RISK-KEEP test (prereg: maxDD cut >= 20% in ALL and in >= 3 of {L6M, HOLD, PRE, X'}; mean change not worse than -MDE in each of those; beats the pooled placebo at 0.95 in ALL)
| basis | policy | label | maxDD change per window | failed |
|---|---|---|---|---|
| N | five books (K6 P6 U6 M6 A6) | **NOT RISK-KEEP** | L6M maxDD +14%, mean -9.7 (MDE 12.5); HOLD maxDD +3%, mean -9.6 (MDE 11.2); PRE maxDD -15%, mean -6.9 (MDE 8.9); X' maxDD +24%, mean -2.3 (MDE 8.8) | maxDD cut >= 20% fails (ALL change -15%; 0 of 4 windows reach it); does not beat the same-volume placebo (ALL-window rank 0.41 < 0.95) |
| N | six books (+H6) | **NOT RISK-KEEP** | L6M maxDD +10%, mean -14.2 (MDE 12.4); HOLD maxDD +11%, mean -14.0 (MDE 11.1); PRE maxDD -10%, mean -7.3 (MDE 9.3); X' maxDD +28%, mean -2.3 (MDE 9.6) | maxDD cut >= 20% fails (ALL change -10%; 0 of 4 windows reach it); mean worse than -MDE in at least one window; does not beat the same-volume placebo (ALL-window rank 0.27 < 0.95) |
| M | five books (K6 P6 U6 M6 A6) | **NOT RISK-KEEP** | L6M maxDD +8%, mean -7.5 (MDE 12.2); HOLD maxDD +0%, mean -7.5 (MDE 11.0); PRE maxDD -16%, mean -5.9 (MDE 8.8); X' maxDD +20%, mean -1.8 (MDE 8.8) | maxDD cut >= 20% fails (ALL change -16%; 0 of 4 windows reach it); does not beat the same-volume placebo (ALL-window rank 0.33 < 0.95) |
| M | six books (+H6) | **NOT RISK-KEEP** | L6M maxDD +4%, mean -12.0 (MDE 12.1); HOLD maxDD +8%, mean -11.9 (MDE 10.8); PRE maxDD -11%, mean -6.2 (MDE 9.1); X' maxDD +24%, mean -1.8 (MDE 9.6) | maxDD cut >= 20% fails (ALL change -11%; 0 of 4 windows reach it); mean worse than -MDE in at least one window; does not beat the same-volume placebo (ALL-window rank 0.23 < 0.95) |
| LIVE-CAL | five books (K6 P6 U6 M6 A6) | **NOT RISK-KEEP** | L6M maxDD +17%, mean -10.0 (MDE 12.2); HOLD maxDD +3%, mean -9.9 (MDE 10.9); PRE maxDD -13%, mean -6.8 (MDE 9.0); X' maxDD +26%, mean -2.2 (MDE 8.9) | maxDD cut >= 20% fails (ALL change -13%; 0 of 4 windows reach it); does not beat the same-volume placebo (ALL-window rank 0.35 < 0.95) |
| LIVE-CAL | six books (+H6) | **NOT RISK-KEEP** | L6M maxDD +13%, mean -14.5 (MDE 12.2); HOLD maxDD +11%, mean -14.3 (MDE 10.9); PRE maxDD -9%, mean -7.2 (MDE 9.3); X' maxDD +31%, mean -2.2 (MDE 9.7) | maxDD cut >= 20% fails (ALL change -9%; 0 of 4 windows reach it); mean worse than -MDE in at least one window; does not beat the same-volume placebo (ALL-window rank 0.23 < 0.95) |

Labels are post-hoc and user-defined (RISK-KEEP = maxDD cut >= 20% with the mean inside MDE, and a rule that the same-volume placebo equals is not a KEEP). No PASS claim; nothing changes live.

## 6. What this scoring can and cannot say
* The composite's own maxDD is 241k over 149 weeks and is set inside PRE (2024-02..2025-06), so ALL and PRE show the same drawdown; the recent windows (L3M/L6M/HOLD) have 14-32 weeks and maxDD 21-97k, so a '20% cut' there is a few k of dollars and the placebo spread is wide. The headline therefore leans on PRE / X' / ALL, where the policy's maxDD change is a 15% cut in PRE (and in ALL, which is the same PRE drawdown) and a 24% deepening in X'.
* worst-20 is the sum of the 20 lowest weeks; L3M (14 wk), L6M (28 wk) and HOLD (32 wk) cannot have a meaningful worst-20 (their composite sums are positive; 20 of 28 / 32 weeks include most of the winners): the worst-5 loss change is shown and the equal-risk change is n/a there. The mean/|worst-20| ratio is n/a where the sum is positive and unreliable in 20-32-week windows.
* The take is evaluated on the lock engine with the Sunday pieces in place (cut, locks per book/week as in ONE_CONVENTION); a take exit is a market exit, so the first-stop cut and the Asia-stop rules only see trades that were not taken. No combined week lock is applied (lock-free headline); under a 12R/20R/30R lock the composite itself changes (DS3_ONE_CONVENTION).
* Exit time: the take exits at the 10-s grid second after the favourable move prints (one-second label convention of THL2); a live D6 evaluation is on its own clock, so the live fire rate and slippage may differ (+0.8 pt measured on LossExit/ProfitExit vs path in LIVE_CAL_SUMMARY: ProfitExit n=4 +0.19 +- 0.28).
* PE entries are confirmation-timed; I measure pct from the leg-1 fill and keep the bracket target distance. H6's active/inactive status follows THP_POLICY (HM carries no plain 70% line).
* Tie-outs: unmodified composite reproduces `oc_res.pkl` daily to 0.0; the overlay arithmetic equals the joint (L2SJ) kernel on every KB row (pts, entry, exit, type, add fill, add size); stored REF stream agreement as above; risk-table rows tie to DS3_ONE_CONVENTION Table E (composite 34.4/21/-21/482 L3M ... 23.1/241/-120/-875 PRE, mean/maxDD/worst week/worst-20 $k).
* The p70 family in the ledger: 27 rows, 26 L2SP cells (`p70always` 17, `p70never` 4, `p70thickonly` 2, `p70_if_thin` 2, plain `REF|p70_take_always` 1) and EXP1 `F7_take_p70`; persistence scores 0.19-0.67 (REF 0.567, EXP1 0.530), none at or above 0.70 and six at >= 0.60 (WT/KB trail rules and the pooled `armpct0.7` take/trail30 rows, all DEAD tier on SIXTY-1 gates). The plain take is therefore not on the SIXTY lists; this page scores the policy line, not the family variants.

## 7. Where it goes
Decision for you (D6 policy line): `profit K6 * pct >= 0.7 take` and the P6/U6/M6/A6 siblings are in THP_POLICY.txt as active lines today. On the Sunday composite they cost about a quarter of the mean and buy no drawdown the placebo does not buy; my default is to leave them out of the Sunday policy until a forward look (N basis, live fills) says otherwise. Rows appended to DEAD_CELLS; MORNING.md has the pointer.