# DS3_JOINT - everything with everything (T-JOINT), version 1 (2026-11-09 23:57Z)

**ROLL-FIXED reference (engine ROLLFIX1: flatten at the 14 rolls; live reference = base_b_rollfix S1-COMB, 21,163 rows; M tables lifted by Z.lift_M, new rows m=1). FIRST-ORDER SCREEN ONLY. PRE-PROOF, post-hoc, shadow only, no PASS claims. Every layer stays ON in every stack: option 0 of each layer is the live setting (multiplier 1).** The layer pools are stand-ins built by SZ-IJK from the owners' multiplier files (M_*.npz, the lot-level layers only) until the owners write /mnt/l2/l2vast/_th_joint/layers/<layer>/topK.json. Cut / profit-rule / lock / entry layers are NOT multiplier-composable and are not in this version.

## Capacity budget (measured)

Exact engine throughput about 24 cell-months/hour/worker with month batching, 6 workers shared box-wide. One stack on L6M+PRE+X' = 33 months = 1.4 worker-hours; HOLD adds 6 months. A 243-stack factorial = 8,000 cell-months = 55 hours of ALL six workers; 3,125 stacks = about 3 weeks. NOT tractable exactly. Used instead: (1) first-order composable screen over every composable stack: full factorial of the top-5 per layer (131072 stacks) plus 5000 random stacks over the 60-cell grids and coordinate descent from live + 10 random starts (about 1 minute of one core); (2) exact runs on L6M+PRE+X' only for the top stacks and every coordinate-descent local optimum (batch mode, about 1.5 stacks/hour at 2 workers); (3) first-order overstates: for the J pairs the exact L6M equal-mean cut was about half the first-order value.

## Layers and pools (lot-level layers, first-order composable)

| layer | options (live + top by DD-first key, grid 60) | pool source |
|---|---|---|
| SIZER | 65 | reg, sizer_vol, sizer_vt |
| LOT | 64 | p7_other, reg |
| SIGQ | 61 | signal_quality |
| REG | 61 | regime |
| STACK | 61 | equal_risk, equity_state, exposure_stack |
| COOL | 61 | cooldown |
| ZONE | 65 | reg, zone |
| A06 | 2 | reg |
| B02 | 5 | reg |

## Registered layers (/mnt/l2/l2vast/_th_joint/layers/*/topK.json)

Static-M layers (multiplier arrays, composable first-order by product): a06_slots: 2 cells incl. live; b02: 5 cells incl. live; cooldown_r5: 1 cells incl. live; cooldowns: 1 cells incl. live; entry: 1 cells incl. live; hm5: 1 cells incl. live; locks: 1 cells incl. live; lot_tables: 4 cells incl. live; ntz: 1 cells incl. live; o7: 1 cells incl. live; ote: 1 cells incl. live; shadow: 2 cells incl. live; sizer: 5 cells incl. live; stack_cut: 1 cells incl. live; zone: 5 cells incl. live. In the screen: SIZER, LOT, ZONE, A06, B02 take the registered cells first (then the stand-in grids); hm5 and stack_cut registered only the live setting.

Trade-list / hook layers (NOT multiplier-composable: they change exits, re-entries, locks, entries; verdicts only from joint exact runs through their hooks): a06_slots: 1 cells; cooldown_r5: 5 cells; cooldowns: 5 cells; cut: 5 cells; entry: 4 cells; locks: 5 cells; lot_tables: 1 cells; ntz: 5 cells; o7: 4 cells; ote: 4 cells; profit: 64 cells; shadow: 8 cells.


## Top-10 joint stacks, first-order screen (full factorial of the top-5 per layer, distinct lot arrays)

Key (standing rule 2, recents first) = min over L6M / L3M of the maxDD cut at EQUAL MEAN to the live stack (global lot scale), then HOLD, worst-20; d mean at equal lots shown. Window cuts below are at equal mean.

| # | SIZER | LOT | SIGQ | REG | STACK | COOL | ZONE | A06 | B02 | key | eq cut L6M / HOLD / PRE / X' | cut at equal lots L6M | d mean L6M | worst-20 L6M cell / live | PRE tolerance | stage |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | live | reg:lot_tables:lot_P7_744 | live | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZNC_B0 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +89.4 / +85.0 / +87.6 | +100.0 | -1081 | 275k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 2 | live | live | live | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZNC_B0 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +87.8 / +83.4 / +89.6 | +100.0 | -189 | 295k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 3 | live | reg:lot_tables:lot_P7_644 | live | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZNC_B0 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +89.5 / +83.9 / +86.6 | +100.0 | -2331 | 268k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 4 | reg:sizer:AB_73ca99b0ec2d | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +87.9 / +84.8 / +84.9 | +100.0 | -4921 | 221k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 5 | live | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:6e18cc85a3d6 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +89.2 / +85.0 / +82.9 | +100.0 | -3463 | 246k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 6 | reg:sizer:AB_73ca99b0ec2d | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:6e18cc85a3d6 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +90.9 / +82.5 / +83.7 | +100.0 | -4959 | 227k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 7 | live | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +86.6 / +85.3 / +85.1 | +100.0 | -3426 | 241k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 8 | reg:sizer:AB_73ca99b0ec2d | live | live | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +81.5 / +84.5 / +86.8 | +100.0 | -5072 | 240k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 9 | reg:sizer:VT_S2 | reg:lot_tables:lot_P7_744 | live | regime:e18edff4f8d3 | live | cooldown:6e18cc85a3d6 | reg:zone:ZNC_B0 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +86.1 / +81.9 / +83.9 | +100.0 | -3039 | 247k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 10 | live | reg:lot_tables:lot_P7_644 | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +83.4 / +84.4 / +83.9 | +100.0 | -7106 | 272k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |

## Coordinate descent (live + 10 random starts, one layer at a time against the key)

| start | local optimum | key |
|---|---|---|
| live | SIZER=sizer_vt:e3f124a36d05 / LOT=reg:lot_tables:lot_P7_744 / SIGQ=signal_quality:7f7622673f09 / REG=regime:3cf7b58e25a6 / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:f511b70e6d8d / ZONE=live / A06=live / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.3 |
| random | SIZER=sizer_vt:c5f9e199982a / LOT=p7_other:3f44a5a78d9d / SIGQ=signal_quality:4a5f60bba7ac / REG=regime:27a5724a4970 / STACK=exposure_stack:E|corr_same_sid / COOL=live / ZONE=zone:02625bc77f17 / A06=live / B02=reg:b02:B02_allbooks_5_1.50_al | 100.3 |
| random | SIZER=sizer_vol:1b5942ac8cd6 / LOT=p7_other:5cc859f6b289 / SIGQ=signal_quality:2b44cb2c7a67 / REG=regime:8715ffc91335 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:9f55d2c16275 / ZONE=zone:465821f8c60d / A06=live / B02=reg:b02:B02_allbooks_5_1.50_al | 100.3 |
| random | SIZER=sizer_vt:cc447c626f19 / LOT=p7_other:3720d0d6b4b1 / SIGQ=signal_quality:f591c705629b / REG=regime:e18edff4f8d3 / STACK=exposure_stack:E|same_side_lot / COOL=live / ZONE=zone:7570c5ff7f2d / A06=live / B02=reg:b02:B02_allbooks_5_1.50_al | 100.3 |
| random | SIZER=sizer_vt:419ae68d5979 / LOT=p7_other:3e206f50c848 / SIGQ=signal_quality:aa09f9fe883b / REG=regime:e933d2e9378d / STACK=equity_state:D|dayloss_stack$| / COOL=cooldown:8b279ff8d6b8 / ZONE=zone:855dd27acc89 / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.4 |
| random | SIZER=sizer_vt:419ae68d5979 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:e37f04b47dd5 / REG=regime:910b86c59480 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:2f1c1eaa9261 / ZONE=zone:7570c5ff7f2d / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_allbooks_5_1.50_al | 100.4 |
| random | SIZER=sizer_vt:92ddfe458baa / LOT=p7_other:28402d9ed83a / SIGQ=signal_quality:98d80d0f642a / REG=regime:4ea126879bc5 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:f511b70e6d8d / ZONE=zone:e34226b932fa / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.4 |
| random | SIZER=sizer_vol:faebfc320da8 / LOT=p7_other:17dc82660d90 / SIGQ=signal_quality:98d80d0f642a / REG=regime:9a89fe48f047 / STACK=exposure_stack:E|corr_same_sid / COOL=live / ZONE=zone:7570c5ff7f2d / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.4 |
| random | SIZER=sizer_vt:f7d0f18fbc1b / LOT=p7_other:b1c8bbda384d / SIGQ=signal_quality:a08183547df2 / REG=regime:47eaf3230c33 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:38737e4187ce / ZONE=zone:0c17aec1653b / A06=reg:a06_slots:a06_greedy_down / B02=live | 100.3 |
| random | SIZER=sizer_vt:7b692e38e6f1 / LOT=p7_other:b1c8bbda384d / SIGQ=signal_quality:2aeb93aa1b83 / REG=regime:4ea126879bc5 / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:6e18cc85a3d6 / ZONE=reg:zone:ZNS_6e93e2da912d / A06=live / B02=reg:b02:B02_K7P7H7_20_1.20_all | 98.1 |
| random | SIZER=sizer_vol:d852c862a088 / LOT=p7_other:049180332953 / SIGQ=signal_quality:98d80d0f642a / REG=regime:9ecb10dea3f9 / STACK=exposure_stack:E|max_books_on| / COOL=cooldown:f511b70e6d8d / ZONE=zone:2427fb49a296 / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.20_all | 100.3 |

## Interaction table (best single cell per layer by key; pair gain minus the sum of single gains, equal-mean L6M cut points; FLAG = |interaction| > 10% of either single gain)

| layer a | layer b | cell a | cell b | gain a | gain b | pair | interaction | flag |
|---|---|---|---|---|---|---|---|---|
| SIZER | A06 | sizer_vt:e3f124a36d05 | reg:a06_slots:a06_greedy_down | +82.9 | +65.9 | +59.2 | -89.5 | FLAG |
| SIZER | ZONE | sizer_vt:e3f124a36d05 | zone:4825c9be186d | +82.9 | +71.1 | +84.3 | -69.7 | FLAG |
| ZONE | B02 | zone:4825c9be186d | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +71.1 | +58.3 | +63.6 | -65.9 | FLAG |
| REG | STACK | regime:d1b5ea189963 | equity_state:D|consec_loss|stack_k | +38.7 | +41.4 | +23.3 | -56.9 | FLAG |
| SIZER | B02 | sizer_vt:e3f124a36d05 | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +82.9 | +58.3 | +85.5 | -55.7 | FLAG |
| ZONE | A06 | zone:4825c9be186d | reg:a06_slots:a06_greedy_down | +71.1 | +65.9 | +84.1 | -52.9 | FLAG |
| SIGQ | ZONE | signal_quality:c39104e20d4f | zone:4825c9be186d | +37.0 | +71.1 | +57.8 | -50.3 | FLAG |
| A06 | B02 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +65.9 | +58.3 | +79.0 | -45.3 | FLAG |
| REG | ZONE | regime:d1b5ea189963 | zone:4825c9be186d | +38.7 | +71.1 | +65.4 | -44.5 | FLAG |
| STACK | B02 | equity_state:D|consec_loss|stack_k | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +41.4 | +58.3 | +55.4 | -44.4 | FLAG |
| SIZER | STACK | sizer_vt:e3f124a36d05 | equity_state:D|consec_loss|stack_k | +82.9 | +41.4 | +81.6 | -42.7 | FLAG |
| SIZER | SIGQ | sizer_vt:e3f124a36d05 | signal_quality:c39104e20d4f | +82.9 | +37.0 | +78.3 | -41.6 | FLAG |
| LOT | A06 | p7_other:b8c7a11b7c62 | reg:a06_slots:a06_greedy_down | +36.5 | +65.9 | +62.1 | -40.3 | FLAG |
| STACK | A06 | equity_state:D|consec_loss|stack_k | reg:a06_slots:a06_greedy_down | +41.4 | +65.9 | +67.3 | -40.0 | FLAG |
| STACK | ZONE | equity_state:D|consec_loss|stack_k | zone:4825c9be186d | +41.4 | +71.1 | +72.9 | -39.6 | FLAG |
| LOT | ZONE | p7_other:b8c7a11b7c62 | zone:4825c9be186d | +36.5 | +71.1 | +68.5 | -39.1 | FLAG |
| REG | B02 | regime:d1b5ea189963 | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +38.7 | +58.3 | +58.3 | -38.8 | FLAG |
| LOT | B02 | p7_other:b8c7a11b7c62 | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +36.5 | +58.3 | +56.4 | -38.4 | FLAG |
| SIGQ | B02 | signal_quality:c39104e20d4f | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +37.0 | +58.3 | +57.1 | -38.2 | FLAG |
| REG | A06 | regime:d1b5ea189963 | reg:a06_slots:a06_greedy_down | +38.7 | +65.9 | +66.5 | -38.2 | FLAG |
| LOT | STACK | p7_other:b8c7a11b7c62 | equity_state:D|consec_loss|stack_k | +36.5 | +41.4 | +41.4 | -36.5 | FLAG |
| SIZER | REG | sizer_vt:e3f124a36d05 | regime:d1b5ea189963 | +82.9 | +38.7 | +85.9 | -35.7 | FLAG |
| SIZER | COOL | sizer_vt:e3f124a36d05 | cooldown:d06ba2496691 | +82.9 | +39.2 | +88.0 | -34.1 | FLAG |
| COOL | B02 | cooldown:d06ba2496691 | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +39.2 | +58.3 | +63.6 | -34.0 | FLAG |
| SIZER | LOT | sizer_vt:e3f124a36d05 | p7_other:b8c7a11b7c62 | +82.9 | +36.5 | +87.1 | -32.2 | FLAG |
| COOL | ZONE | cooldown:d06ba2496691 | zone:4825c9be186d | +39.2 | +71.1 | +78.2 | -32.1 | FLAG |
| LOT | REG | p7_other:b8c7a11b7c62 | regime:d1b5ea189963 | +36.5 | +38.7 | +43.7 | -31.5 | FLAG |
| LOT | COOL | p7_other:b8c7a11b7c62 | cooldown:d06ba2496691 | +36.5 | +39.2 | +44.8 | -30.9 | FLAG |
| STACK | COOL | equity_state:D|consec_loss|stack_k | cooldown:d06ba2496691 | +41.4 | +39.2 | +50.1 | -30.5 | FLAG |
| REG | COOL | regime:d1b5ea189963 | cooldown:d06ba2496691 | +38.7 | +39.2 | +48.0 | -30.0 | FLAG |
| COOL | A06 | cooldown:d06ba2496691 | reg:a06_slots:a06_greedy_down | +39.2 | +65.9 | +77.4 | -27.7 | FLAG |
| SIGQ | A06 | signal_quality:c39104e20d4f | reg:a06_slots:a06_greedy_down | +37.0 | +65.9 | +76.6 | -26.2 | FLAG |
| SIGQ | COOL | signal_quality:c39104e20d4f | cooldown:d06ba2496691 | +37.0 | +39.2 | +51.4 | -24.8 | FLAG |
| SIGQ | REG | signal_quality:c39104e20d4f | regime:d1b5ea189963 | +37.0 | +38.7 | +54.4 | -21.3 | FLAG |
| LOT | SIGQ | p7_other:b8c7a11b7c62 | signal_quality:c39104e20d4f | +36.5 | +37.0 | +54.7 | -18.8 | FLAG |
| SIGQ | STACK | signal_quality:c39104e20d4f | equity_state:D|consec_loss|stack_k | +37.0 | +41.4 | +61.7 | -16.7 | FLAG |

## Validation of the joint pick (first-order)

- Placebo / family null over the joint space: 5000 random stacks over the full grids give key quantiles median 68.4, 90% 85.5, 99% 95.1, max 100.3. The best factorial stack key is 100.4: it is above the best random stack, i.e. the full-grid random search finds stacks as good as the top-K factorial (no evidence that top-K selection matters; family p for the best stack over this joint space is about 1 (it is the maximum of a searched set)).
- Joint walk-forward (monthly, purged 7 d, trailing 26 weeks, candidate pool = live + 1500 random stacks NOT selected on full-sample data, pick by equal-mean train maxDD): OOS maxDD cut +75.1% vs live, d mean -9175 $/wk, live kept in 0 of 34 months. The pick procedure does cut OOS maxDD but gives up mean (it is mostly an exposure reduction).
- STANDING RULE 2 primary OOS test, bi-weekly re-pick WF (trailing 26 weeks -> next 2 weeks, purged 7 d) of the whole joint procedure: 75 refit periods since 2024-01, OOS maxDD cut +72.0% with d mean -9626 $/wk; the pick beat live (period P&L >= live and in-period drawdown <= live) in 39% of periods (P&L alone 39%); since 2026-05-12 (13 periods): 46% beat, 46% P&L-ge.
- Held-out live week: n/a for stacks (the owners' M arrays cover the 21,135 base rows only).

## REFIT 2026-11-22 (what the bi-weekly procedure would pick today; first-order screen, train = trailing 26 weeks to 2026-11-05, pick = lowest equal-mean train maxDD among live + 1500 random stacks)

Pick: SIZER=sizer_vt:4ddecada7421 | LOT=p7_other:29234d9766a9 | SIGQ=signal_quality:b9a6edabcd7b | REG=regime:9ecb10dea3f9 | STACK=equity_state:D|eqdd_book_20d_R|Y1R_f0.50_sticky|sess_london | COOL=cooldown:f511b70e6d8d | ZONE=zone:a4a12796db42 | A06=reg:a06_slots:a06_greedy_down | B02=live. Train maxDD at equal mean 94 vs live 79907. NOT exact-confirmed; the verdict needs the exact runs.

Standing rule 2 tolerance check of the top-10 stacks: PRE maxDD not more than 15% deeper than live and PRE mean not below live - 1k; failing stacks are labelled RECENT-ONLY (reported, not killed).

## Plain sentence


First-order screen: the best first-order joint stack lowers L6M maxDD +100.0% at equal mean (PRE +85.0%, X' +87.6%) and differs from live in these layers: LOT=reg:lot_tables:lot_P7_744, REG=regime:e18edff4f8d3, COOL=cooldown:5adf9b2c9b46, ZONE=reg:zone:ZNC_B0, A06=reg:a06_slots:a06_greedy_down, B02=reg:b02:B02_K7P7H7_20_1.00_alld_0.0. The screen is lot-level layers only, in-sample, and first-order overstates badly (exact J-pair and joint-stack runs gave a fraction of it). The verdict comes from exact runs, the bi-weekly re-pick WF and the REFIT section; cut / profit / lock / entry / NTZ layers join only through exact hooks.
