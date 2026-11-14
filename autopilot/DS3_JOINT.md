# DS3_JOINT - everything with everything (T-JOINT), version 1 (2026-11-14 02:22Z)

**ROLL-EXCL (33 contract-roll artifact trades excluded). FIRST-ORDER SCREEN ONLY. PRE-PROOF, post-hoc, shadow only, no PASS claims. Every layer stays ON in every stack: option 0 of each layer is the live setting (multiplier 1).** The layer pools are stand-ins built by SZ-IJK from the owners' multiplier files (M_*.npz, the lot-level layers only) until the owners write /mnt/l2/l2vast/_th_joint/layers/<layer>/topK.json. Cut / profit-rule / lock / entry layers are NOT multiplier-composable and are not in this version.

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
| B02 | 4 | reg |

## Registered layers (/mnt/l2/l2vast/_th_joint/layers/*/topK.json)

Static-M layers (multiplier arrays, composable first-order by product): a06_slots: 2 cells incl. live; b02: 4 cells incl. live; brackets: 1 cells incl. live; cooldown_r5: 1 cells incl. live; cooldowns: 1 cells incl. live; entry: 1 cells incl. live; hm5: 1 cells incl. live; locks: 1 cells incl. live; lot_tables: 4 cells incl. live; netting: 1 cells incl. live; ntz: 1 cells incl. live; o7: 1 cells incl. live; ote: 1 cells incl. live; reentry: 1 cells incl. live; regime_gate: 2 cells incl. live; session_blocks: 1 cells incl. live; shadow: 2 cells incl. live; signals: 7 cells incl. live; sizer: 5 cells incl. live; sizer_state: 1 cells incl. live; stack_cut: 1 cells incl. live; stack_exposure: 1 cells incl. live; stopexit: 4 cells incl. live; zone: 5 cells incl. live. In the screen: SIZER, LOT, ZONE, A06, B02 take the registered cells first (then the stand-in grids); hm5 and stack_cut registered only the live setting.

Trade-list / hook layers (NOT multiplier-composable: they change exits, re-entries, locks, entries; verdicts only from joint exact runs through their hooks): a06_slots: 1 cells; brackets: 4 cells; cooldown_r5: 3 cells; cooldowns: 5 cells; cut: 5 cells; entry: 4 cells; locks: 5 cells; lot_tables: 1 cells; netting: 4 cells; ntz: 3 cells; o7: 3 cells; ote: 3 cells; profit: 64 cells; reentry: 5 cells; session_blocks: 4 cells; shadow: 8 cells; signals: 28 cells; sizer_state: 1 cells; stack_exposure: 1 cells; stopexit: 4 cells.


## Top-10 joint stacks, first-order screen (full factorial of the top-5 per layer, distinct lot arrays)

Key (standing rule 2, recents first) = min over L6M / L3M of the maxDD cut at EQUAL MEAN to the live stack (global lot scale), then HOLD, worst-20; d mean at equal lots shown. Window cuts below are at equal mean.

| # | SIZER | LOT | SIGQ | REG | STACK | COOL | ZONE | A06 | B02 | key | eq cut L6M / HOLD / PRE / X' | cut at equal lots L6M | d mean L6M | worst-20 L6M cell / live | PRE tolerance | stage |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | reg:sizer:AB_73ca99b0ec2d | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +87.3 / +84.0 / +83.1 | +100.0 | -5733 | 216k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 2 | live | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +86.0 / +84.6 / +83.4 | +100.0 | -4237 | 238k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 3 | live | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:6e18cc85a3d6 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +88.7 / +84.3 / +80.9 | +100.0 | -4274 | 241k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 4 | reg:sizer:AB_73ca99b0ec2d | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:6e18cc85a3d6 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +90.4 / +81.6 / +81.7 | +100.0 | -5770 | 219k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 5 | reg:sizer:VT_S2 | live | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +77.1 / +87.6 / +87.0 | +100.0 | -1473 | 269k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 6 | reg:sizer:AB_73ca99b0ec2d | live | live | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +81.0 / +84.1 / +85.5 | +100.0 | -5641 | 221k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 7 | live | reg:lot_tables:lot_P7_744 | live | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZS_C0_6e93e2da912d | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +86.3 / +84.1 / +79.8 | +100.0 | -2263 | 264k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 8 | live | reg:lot_tables:lot_P7_644 | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.3 | +100.0 / +82.7 / +84.5 / +82.2 | +100.0 | -7940 | 256k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 9 | live | live | live | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZS_C0_6e93e2da912d | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.3 | +100.0 / +85.8 / +83.4 / +79.4 | +100.0 | -1960 | 272k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 10 | live | live | signal_quality:73c32e59f366 | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZS_C0_6e93e2da912d | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.3 | +100.0 / +78.9 / +81.7 / +79.6 | +100.0 | -3797 | 241k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |

## Coordinate descent (live + 10 random starts, one layer at a time against the key)

| start | local optimum | key |
|---|---|---|
| live | SIZER=sizer_vt:e3f124a36d05 / LOT=reg:lot_tables:lot_greedy_down / SIGQ=signal_quality:67c701bb2705 / REG=regime:72ffa1d9c2fa / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:f511b70e6d8d / ZONE=live / A06=live / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.3 |
| random | SIZER=sizer_vt:d65ad35f7583 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:98d80d0f642a / REG=regime:72ffa1d9c2fa / STACK=equity_state:D|eqdd_stack_20d| / COOL=cooldown:020242389bc4 / ZONE=zone:7570c5ff7f2d / A06=live / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.4 |
| random | SIZER=sizer_vol:1b5942ac8cd6 / LOT=reg:lot_tables:lot_greedy_down / SIGQ=signal_quality:894921a2d1c4 / REG=regime:0c9d251dc8cd / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:9f55d2c16275 / ZONE=zone:465821f8c60d / A06=live / B02=live | 100.3 |
| random | SIZER=reg:sizer:AB_e2058312a643 / LOT=p7_other:9ce43e948920 / SIGQ=signal_quality:da5d92c18f1f / REG=regime:ffe1dffa4c6a / STACK=equity_state:D|consec_loss|boo / COOL=cooldown:f4edae75e179 / ZONE=zone:0a3bc6037631 / A06=live / B02=reg:b02:B02_allbooks_20_1.00_a | 94.1 |
| random | SIZER=sizer_vt:7b692e38e6f1 / LOT=live / SIGQ=signal_quality:e47c3f7e101a / REG=regime:b3ea76f76089 / STACK=equity_state:D|eqdd_stack_20d| / COOL=cooldown:21142bd69657 / ZONE=zone:0c7c17f6c16b / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.20_all | 100.3 |
| random | SIZER=reg:sizer:AB_e2058312a643 / LOT=p7_other:28402d9ed83a / SIGQ=signal_quality:98d80d0f642a / REG=regime:4ea126879bc5 / STACK=equity_state:D|dayloss_stack$| / COOL=cooldown:f511b70e6d8d / ZONE=zone:f8fbee4f18de / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_allbooks_20_1.00_a | 100.4 |
| random | SIZER=sizer_vt:e7400edefb68 / LOT=p7_other:3720d0d6b4b1 / SIGQ=signal_quality:6b7b2de4509f / REG=regime:4f3bbda422f4 / STACK=equity_state:D|eqdd_book_20d_R / COOL=live / ZONE=zone:02625bc77f17 / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.4 |
| random | SIZER=sizer_vt:5cdd27c75bf6 / LOT=reg:lot_tables:lot_greedy_down / SIGQ=signal_quality:98d80d0f642a / REG=regime:9a89fe48f047 / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:446ba756b578 / ZONE=zone:8031aee5ac1d / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.20_all | 100.3 |
| random | SIZER=sizer_vt:6df60ffc81f9 / LOT=p7_other:ac4e6310f17b / SIGQ=signal_quality:a08183547df2 / REG=regime:27a5724a4970 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:c6feb36a19bf / ZONE=zone:f8fbee4f18de / A06=reg:a06_slots:a06_greedy_down / B02=live | 100.4 |
| random | SIZER=sizer_vt:c5f9e199982a / LOT=p7_other:3f44a5a78d9d / SIGQ=signal_quality:54892748d6f6 / REG=regime:0c9d251dc8cd / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:710c05205ee3 / ZONE=zone:f8fbee4f18de / A06=live / B02=live | 100.3 |
| random | SIZER=sizer_vt:7b692e38e6f1 / LOT=p7_other:5cc859f6b289 / SIGQ=signal_quality:98d80d0f642a / REG=regime:9ecb10dea3f9 / STACK=equity_state:D|consec_loss|sta / COOL=cooldown:47780790ba5d / ZONE=zone:8031aee5ac1d / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.20_all | 99.8 |

## Interaction table (best single cell per layer by key; pair gain minus the sum of single gains, equal-mean L6M cut points; FLAG = |interaction| > 10% of either single gain)

| layer a | layer b | cell a | cell b | gain a | gain b | pair | interaction | flag |
|---|---|---|---|---|---|---|---|---|
| SIZER | A06 | sizer_vt:e3f124a36d05 | reg:a06_slots:a06_greedy_down | +82.8 | +66.0 | +58.4 | -90.4 | FLAG |
| SIZER | ZONE | sizer_vt:e3f124a36d05 | zone:4825c9be186d | +82.8 | +70.7 | +83.9 | -69.6 | FLAG |
| ZONE | B02 | zone:4825c9be186d | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +70.7 | +58.3 | +61.8 | -67.1 | FLAG |
| REG | STACK | regime:d1b5ea189963 | equity_state:D|consec_loss|stack_k | +38.0 | +41.4 | +22.4 | -57.0 | FLAG |
| SIZER | B02 | sizer_vt:e3f124a36d05 | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +82.8 | +58.3 | +84.7 | -56.4 | FLAG |
| ZONE | A06 | zone:4825c9be186d | reg:a06_slots:a06_greedy_down | +70.7 | +66.0 | +83.8 | -52.9 | FLAG |
| SIGQ | ZONE | signal_quality:c39104e20d4f | zone:4825c9be186d | +37.0 | +70.7 | +57.0 | -50.6 | FLAG |
| COOL | ZONE | cooldown:020242389bc4 | zone:4825c9be186d | +38.3 | +70.7 | +62.0 | -47.0 | FLAG |
| A06 | B02 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +66.0 | +58.3 | +78.6 | -45.7 | FLAG |
| STACK | B02 | equity_state:D|consec_loss|stack_k | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +41.4 | +58.3 | +54.6 | -45.1 | FLAG |
| REG | ZONE | regime:d1b5ea189963 | zone:4825c9be186d | +38.0 | +70.7 | +64.6 | -44.1 | FLAG |
| SIZER | STACK | sizer_vt:e3f124a36d05 | equity_state:D|consec_loss|stack_k | +82.8 | +41.4 | +81.5 | -42.7 | FLAG |
| SIZER | SIGQ | sizer_vt:e3f124a36d05 | signal_quality:c39104e20d4f | +82.8 | +37.0 | +78.2 | -41.6 | FLAG |
| LOT | A06 | p7_other:b8c7a11b7c62 | reg:a06_slots:a06_greedy_down | +36.5 | +66.0 | +61.7 | -40.7 | FLAG |
| STACK | A06 | equity_state:D|consec_loss|stack_k | reg:a06_slots:a06_greedy_down | +41.4 | +66.0 | +66.9 | -40.5 | FLAG |
| STACK | ZONE | equity_state:D|consec_loss|stack_k | zone:4825c9be186d | +41.4 | +70.7 | +72.5 | -39.6 | FLAG |
| LOT | ZONE | p7_other:b8c7a11b7c62 | zone:4825c9be186d | +36.5 | +70.7 | +68.0 | -39.2 | FLAG |
| LOT | B02 | p7_other:b8c7a11b7c62 | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +36.5 | +58.3 | +56.3 | -38.4 | FLAG |
| REG | A06 | regime:d1b5ea189963 | reg:a06_slots:a06_greedy_down | +38.0 | +66.0 | +65.9 | -38.2 | FLAG |
| REG | B02 | regime:d1b5ea189963 | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +38.0 | +58.3 | +58.2 | -38.1 | FLAG |
| LOT | STACK | p7_other:b8c7a11b7c62 | equity_state:D|consec_loss|stack_k | +36.5 | +41.4 | +41.4 | -36.5 | FLAG |
| SIZER | REG | sizer_vt:e3f124a36d05 | regime:d1b5ea189963 | +82.8 | +38.0 | +85.7 | -35.1 | FLAG |
| SIZER | LOT | sizer_vt:e3f124a36d05 | p7_other:b8c7a11b7c62 | +82.8 | +36.5 | +87.0 | -32.2 | FLAG |
| LOT | REG | p7_other:b8c7a11b7c62 | regime:d1b5ea189963 | +36.5 | +38.0 | +43.1 | -31.4 | FLAG |
| COOL | A06 | cooldown:020242389bc4 | reg:a06_slots:a06_greedy_down | +38.3 | +66.0 | +74.7 | -29.6 | FLAG |
| SIGQ | B02 | signal_quality:c39104e20d4f | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +37.0 | +58.3 | +65.8 | -29.4 | FLAG |
| SIGQ | A06 | signal_quality:c39104e20d4f | reg:a06_slots:a06_greedy_down | +37.0 | +66.0 | +76.4 | -26.6 | FLAG |
| STACK | COOL | equity_state:D|consec_loss|stack_k | cooldown:020242389bc4 | +41.4 | +38.3 | +54.9 | -24.9 | FLAG |
| SIZER | COOL | sizer_vt:e3f124a36d05 | cooldown:020242389bc4 | +82.8 | +38.3 | +96.3 | -24.7 | FLAG |
| COOL | B02 | cooldown:020242389bc4 | reg:b02:B02_K7P7H7_20_1.20_alld_0. | +38.3 | +58.3 | +73.5 | -23.1 | FLAG |
| SIGQ | COOL | signal_quality:c39104e20d4f | cooldown:020242389bc4 | +37.0 | +38.3 | +53.2 | -22.1 | FLAG |
| SIGQ | REG | signal_quality:c39104e20d4f | regime:d1b5ea189963 | +37.0 | +38.0 | +54.0 | -21.0 | FLAG |
| LOT | SIGQ | p7_other:b8c7a11b7c62 | signal_quality:c39104e20d4f | +36.5 | +37.0 | +54.7 | -18.7 | FLAG |
| SIGQ | STACK | signal_quality:c39104e20d4f | equity_state:D|consec_loss|stack_k | +37.0 | +41.4 | +61.7 | -16.7 | FLAG |
| REG | COOL | regime:d1b5ea189963 | cooldown:020242389bc4 | +38.0 | +38.3 | +59.9 | -16.4 | FLAG |
| LOT | COOL | p7_other:b8c7a11b7c62 | cooldown:020242389bc4 | +36.5 | +38.3 | +58.9 | -15.9 | FLAG |

## Validation of the joint pick (first-order)

- Placebo / family null over the joint space: 5000 random stacks over the full grids give key quantiles median 64.2, 90% 83.8, 99% 93.6, max 100.3. The best factorial stack key is 100.4: it is above the best random stack, i.e. the full-grid random search finds stacks as good as the top-K factorial (no evidence that top-K selection matters; family p for the best stack over this joint space is about 1 (it is the maximum of a searched set)).
- Joint walk-forward (monthly, purged 7 d, trailing 26 weeks, candidate pool = live + 1500 random stacks NOT selected on full-sample data, pick by equal-mean train maxDD): OOS maxDD cut +76.9% vs live, d mean -9434 $/wk, live kept in 0 of 34 months. The pick procedure does cut OOS maxDD but gives up mean (it is mostly an exposure reduction).
- STANDING RULE 2 primary OOS test, bi-weekly re-pick WF (trailing 26 weeks -> next 2 weeks, purged 7 d) of the whole joint procedure: 75 refit periods since 2024-01, OOS maxDD cut +76.5% with d mean -9863 $/wk; the pick beat live (period P&L >= live and in-period drawdown <= live) in 35% of periods (P&L alone 35%); since 2026-05-12 (13 periods): 46% beat, 46% P&L-ge.
- Held-out live week: n/a for stacks (the owners' M arrays cover the 21,135 base rows only).

## Exact engine results for joint stacks (table mode: the stack multiplier applied after the Q1-A ladder, before zone HALF)

| stack | window | cut | eq-mean cut | d mean | worst-20 | standing rule 2a label (PRE row) |
|---|---|---|---|---|---|---|
| J01 | L1M | +57.8 | +52.9 | +18143 | -26k / -3k |  |
| J01 | L2M | +57.8 | +52.9 | -2976 | 162k / 263k |  |
| J01 | L3M | +57.8 | +53.0 | -450 | 132k / 215k |  |
| J01 | L6M | +11.9 | +1.9 | -2287 | 114k / 165k |  |
| J01 | PRE | +31.5 | +23.7 | -4319 | -488k / -700k | RECENT-ONLY (allow 15.0%, WF 50%) |
| J01 | X' | +63.2 | +59.0 | +882 | -211k / -348k |  |
| J02 | L1M | +44.2 | +32.4 | +15441 | -45k / -3k |  |
| J02 | L2M | +35.5 | +22.0 | -5228 | 133k / 263k |  |
| J02 | L3M | +13.9 | -4.2 | -5353 | 63k / 215k |  |
| J02 | L6M | +13.9 | -4.2 | -3878 | 45k / 165k |  |
| J02 | PRE | +39.1 | +26.3 | -4191 | -447k / -700k | RECENT-ONLY (allow 15.0%, WF 45%) |
| J02 | X' | +72.5 | +66.7 | +4678 | -213k / -348k |  |
| J03 | L1M | +56.4 | +57.2 | +19492 | -35k / -3k |  |
| J03 | L2M | +56.4 | +57.2 | -679 | 167k / 263k |  |
| J03 | L3M | +52.0 | +52.9 | +513 | 131k / 215k |  |
| J03 | L6M | +18.9 | +20.4 | +434 | 133k / 165k |  |
| J03 | PRE | +31.5 | +32.8 | -6395 | -450k / -700k | RECENT-ONLY (allow 25.0%, WF 68%) |
| J03 | X' | +70.8 | +71.4 | +3593 | -175k / -348k |  |
| J04 | L1M | +65.5 | +58.1 | +17668 | -28k / -3k |  |
| J04 | L2M | +65.5 | +58.1 | -6817 | 131k / 263k |  |
| J04 | L3M | +59.8 | +51.2 | -2448 | 108k / 215k |  |
| J04 | L6M | +13.8 | -4.7 | -3945 | 104k / 165k |  |
| J04 | PRE | +43.4 | +31.2 | -4611 | -425k / -700k | RECENT-ONLY (allow 23.7830892631387%, WF 61%) |
| J04 | X' | +68.1 | +61.2 | +2059 | -170k / -348k |  |
| JZ01 | L1M | +40.0 | +16.8 | +16121 | -48k / -3k |  |
| JZ01 | L2M | +28.8 | +1.3 | -11067 | 81k / 263k |  |
| JZ01 | L3M | +28.9 | +1.4 | -7706 | 29k / 215k |  |
| JZ01 | L6M | +26.3 | -2.3 | -6234 | 27k / 165k |  |
| JZ01 | PRE | +55.5 | +38.2 | -4844 | -443k / -700k | RECENT-ONLY (allow 25.0%, WF 68%) |
| JZ02 | L1M | +88.5 | +86.0 | +27160 | -2k / -3k |  |
| JZ02 | L2M | +88.5 | +86.0 | -9597 | 106k / 263k |  |
| JZ02 | L3M | +32.0 | +17.3 | -6560 | 56k / 215k |  |
| JZ02 | L6M | +12.2 | -6.7 | -3960 | 88k / 165k |  |
| JZ02 | PRE | +47.9 | +36.6 | -5335 | -403k / -700k | RECENT-ONLY (allow 22.19294748141969%, WF 73%) |
| JZ03 | L1M | +51.1 | +41.1 | +17356 | -35k / -3k |  |
| JZ03 | L2M | +51.1 | +41.1 | -6451 | 127k / 263k |  |
| JZ03 | L3M | +10.4 | -7.9 | -5830 | 60k / 215k |  |
| JZ03 | L6M | -14.4 | -37.8 | -3789 | 41k / 165k |  |
| JZ03 | PRE | +46.0 | +34.9 | -3911 | -508k / -700k | RECENT-ONLY (allow 15.0%, WF 59%) |
| JZ04 | L1M | +32.1 | +10.5 | +12160 | -54k / -3k |  |
| JZ04 | L2M | +32.1 | +10.5 | -3171 | 150k / 263k |  |
| JZ04 | L3M | +1.2 | -30.3 | -4148 | 77k / 215k |  |
| JZ04 | L6M | +1.2 | -30.3 | -5392 | 48k / 165k |  |
| JZ04 | PRE | +39.1 | +19.8 | -4930 | -475k / -700k | RECENT-ONLY (allow 15.0%, WF 64%) |
| JY01 | L1M | +87.0 | +87.3 | +27878 | -7k / -3k |  |
| JY01 | L2M | +87.0 | +87.3 | -1138 | 167k / 263k |  |
| JY01 | L3M | +31.1 | +32.7 | -1222 | 113k / 215k |  |
| JY01 | L6M | -22.7 | -20.0 | +511 | 111k / 165k |  |
| JY02 | L1M | +86.6 | +86.5 | +27547 | -7k / -3k |  |
| JY02 | L2M | +86.6 | +86.5 | -2241 | 159k / 263k |  |
| JY02 | L3M | +22.0 | +21.2 | -2362 | 100k / 215k |  |
| JY02 | L6M | -27.2 | -28.5 | -231 | 93k / 165k |  |
| JY03 | L1M | +87.3 | +86.6 | +27376 | -4k / -3k |  |
| JY03 | L2M | +87.3 | +86.6 | -2864 | 157k / 263k |  |
| JY03 | L3M | +37.5 | +34.1 | -1180 | 118k / 215k |  |
| JY03 | L6M | -26.4 | -33.3 | -1166 | 110k / 165k |  |
| JY04 | L1M | +73.3 | +70.3 | +24601 | -21k / -3k |  |
| JY04 | L2M | +73.3 | +70.3 | -4127 | 138k / 263k |  |
| JY04 | L3M | +8.5 | -2.0 | -4215 | 72k / 215k |  |
| JY04 | L6M | -27.3 | -42.0 | -2309 | 39k / 165k |  |
| JY05 | L1M | +55.6 | +16.9 | +17885 | -30k / -3k |  |
| JY05 | L2M | +40.2 | -12.0 | -9447 | 106k / 263k |  |
| JY05 | L3M | -9.8 | -105.7 | -9531 | 20k / 215k |  |
| JY05 | L6M | -38.3 | -159.1 | -10407 | -99k / 165k |  |
| JY06 | L1M | +77.3 | +72.5 | +23883 | -18k / -3k |  |
| JY06 | L2M | +77.3 | +72.5 | -5236 | 134k / 263k |  |
| JY06 | L3M | +30.3 | +15.5 | -3158 | 90k / 215k |  |
| JY06 | L6M | -31.0 | -58.9 | -3925 | 42k / 165k |  |

## Exact vs first-order (so far)

First-order keys of these stacks were 86-88% (equal-mean cut). Exact engine: J01: L6M eq-mean cut +1.9 / d mean -2287, PRE eq-mean cut +23.7 / d mean -4319, X' eq-mean cut +59.0 / d mean +882; J02: L6M eq-mean cut -4.2 / d mean -3878, PRE eq-mean cut +26.3 / d mean -4191, X' eq-mean cut +66.7 / d mean +4678; J03: L6M eq-mean cut +20.4 / d mean +434, PRE eq-mean cut +32.8 / d mean -6395, X' eq-mean cut +71.4 / d mean +3593; J04: L6M eq-mean cut -4.7 / d mean -3945, PRE eq-mean cut +31.2 / d mean -4611, X' eq-mean cut +61.2 / d mean +2059; JY01: L6M eq-mean cut -20.0 / d mean +511; JY02: L6M eq-mean cut -28.5 / d mean -231; JY03: L6M eq-mean cut -33.3 / d mean -1166; JY04: L6M eq-mean cut -42.0 / d mean -2309; JY05: L6M eq-mean cut -159.1 / d mean -10407; JY06: L6M eq-mean cut -58.9 / d mean -3925; JZ01: L6M eq-mean cut -2.3 / d mean -6234, PRE eq-mean cut +38.2 / d mean -4844; JZ02: L6M eq-mean cut -6.7 / d mean -3960, PRE eq-mean cut +36.6 / d mean -5335; JZ03: L6M eq-mean cut -37.8 / d mean -3789, PRE eq-mean cut +34.9 / d mean -3911; JZ04: L6M eq-mean cut -30.3 / d mean -5392, PRE eq-mean cut +19.8 / d mean -4930.

Reading: the first-order joint screen of stacked down-sizing layers is NOT predictive of the engine. In the exact run a skipped signal frees the book, which then takes the next signal, and re-entries / locks / slice fills change; so a table that skips 60-85% of signals first-order removes only about 18% of the trades in the engine (F08 pair: 672 vs 823 trades in 202610, lots 1440 vs 1746) and behaves like a mild global lot reduction. Only exact numbers count. Missing windows are still running.

## REFIT 2026-11-22 (what the bi-weekly procedure would pick today; first-order screen, train = trailing 26 weeks to 2026-11-05, pick = lowest equal-mean train maxDD among live + 1500 random stacks)

Pick: SIZER=reg:sizer:VT_S2 | LOT=p7_other:593dae045f4a | SIGQ=signal_quality:d4304aa7f37a | REG=regime:8715ffc91335 | STACK=exposure_stack:E|total_lots_cap|cap6_skip|P7_sess_nyam | COOL=cooldown:50db603d2c5a | ZONE=zone:5fe923a731af | A06=reg:a06_slots:a06_greedy_down | B02=live. Train maxDD at equal mean 408 vs live 79907. NOT exact-confirmed; the verdict needs the exact runs.

Standing rule 2 tolerance check of the top-10 stacks: PRE maxDD not more than 15% deeper than live and PRE mean not below live - 1k; failing stacks are labelled RECENT-ONLY (reported, not killed).

## Leave-one-layer-out of the exact stack J03 (ROLL-FIXED engine, exact, L6M + PRE; each row = J03 with one layer set back to live)

| set | layer dropped | cut L6M / L3M / L1M | eq-mean cut L6M | d mean L6M | PRE cut / eq-mean / d mean | HOLD cut | bi-weekly WF beat | 2a label |
|---|---|---|---|---|---|---|---|---|
| J03 | none (full J03) | +18.9 / +52.0 / +56.4 | +21.6 | +769 | +33.0 / +35.2 / -6170 | +29.2 | 65% | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 65%) |
| JL01 | SIZER | +29.0 / +29.0 / +71.4 | +36.5 | +2625 | +37.9 / +44.5 / -4452 | +29.3 | 85% | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 85%) |
| JL02 | LOT | +18.9 / +45.0 / +51.8 | +21.3 | +699 | +7.1 / +10.0 / -3773 | n/a | 64% | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 64%) |
| JL03 | SIGQ | +14.9 / +59.8 / +59.7 | +21.1 | +1750 | +28.0 / +33.2 / -5161 | n/a | 64% | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 24.915826255760347%, WF 64%) |
| JL04 | REG | +20.9 / +52.0 / +54.9 | +23.8 | +876 | +21.7 / +24.7 / -5740 | n/a | 59% | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 15.0%, WF 59%) |
| JL05 | STACK | +10.1 / +47.5 / +60.4 | +9.8 | -94 | +27.2 / +26.9 / -6661 | n/a | 64% | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 20.14357379434636%, WF 64%) |
| JL06 | COOL | +22.6 / +43.6 / +54.9 | +25.6 | +882 | +23.2 / +26.1 / -4592 | n/a | 59% | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 15.0%, WF 59%) |

Reading: the STACK exposure cap (E same_side cap6_trunc london) carries the L6M gain (dropping it: L6M cut 10.1%, d mean -94). Dropping the SIZER (VT) layer IMPROVES recents (L6M cut 29.0%, d mean +2.6k/wk, L1M 71%) and raises PRE cut to 37.9% and PRE mean by +1.7k/wk. The PRE mean loss is NOT carried by one layer: every variant loses 3.8k-6.7k/wk on PRE; the LOT (P7 cap) layer costs about 2.4k/wk of PRE mean while adding about 26 points of PRE cut. The PRE loss is concentrated in 2024-H2 (J03 d mean -11.4k/wk, live +23k/wk) and 2025-H1 (-4.1k/wk), not in 2023 / 2024-H1.

New stacks queued for exact L6M + PRE (built from the leave-one-out; JN01 = JL01): JN01 = JL01: J03 minus SIZER; JN02 = JL01 minus SIGQ; JN03 = JL01 with LOT = LOT_P7_744; JN04 = JL01 minus COOL; JN05 = JL01 with STACK = E|same_side_lots_cap|cap8_skip|sess_london; JN06 = JL01 minus REG.

## Exact stack comparison (ROLL-FIXED engine, exact; standing rules 2 / 2a)

| stack | what | cut L6M / L3M / L1M | eq-mean L6M | d mean L6M / L3M | HOLD cut / d mean | PRE cut / d mean | X' cut / d mean | WF beat all (since 2026-05-18) | 2a label (PRE allowance, WF%) |
|---|---|---|---|---|---|---|---|---|---|
| J03 | full J03 (SIZER VT, LOT P7 cap, SIGQ, REG, STACK E cap6, COOL) | +18.9 / +52.0 / +56.4 | +21.6 | +769 / +513 | +29.2 / -1809 | +33.0 / -6170 | +72.6 / +3623 | 65% (55%) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 65%) |
| JL01 | J03 minus SIZER (= JN01) | +29.0 / +29.0 / +71.4 | +36.5 | +2625 / +3211 | +29.3 / -3207 | +37.9 / -4452 | +71.3 / +2509 | 85% (73%) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 85%) |
| JN02 | JL01 minus SIGQ | +28.8 / +28.8 / +78.4 | +37.9 | +3297 / +3649 | +12.8 / -1521 | +36.9 / -3265 | n/a / n/a | 82% (73%) | OK-PRIOR [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 82%) |
| JN03 | JL01 with LOT = LOT_P7_744 | +39.0 / +39.0 / +40.2 | +42.2 | +1251 / +1102 | +24.8 / -2593 | +37.6 / -3107 | +68.8 / +2543 | 82% (73%) | OK-PRIOR [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 82%) |
| JN04 | JL01 minus COOL | +43.4 / +43.4 / +67.9 | +53.5 | +4860 / +5959 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | 76% (73%) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 76%) |
| JN05 | JL01 with STACK = E|same_side_lots_cap|cap8_skip|sess_london | +35.2 / +35.2 / +56.2 | +39.5 | +1610 / +3448 | +14.9 / -1484 | +18.4 / -4001 | n/a / n/a | 70% (64%) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 70%) |
| JN06 | JL01 minus REG | +27.0 / +27.0 / +54.5 | +34.7 | +2896 / +3981 | +33.7 / -2519 | +29.4 / -3311 | n/a / n/a | 76% (73%) | OK-PRIOR [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 76%) |
| JP01 | JN04 + R1_3 lock: P7 day-LOSS cap fixed $8,400 (1R on 7 base lots, R on BASE lots) and day-WIN cap $33,600 (4R), no SizeMult scaling under Q1-A | +42.6 / +42.6 / +50.8 | +49.6 | +3109 / +3822 | +49.6 / -2559 | +41.7 / -3218 | +66.2 / +1165 | 85% (91%) | OK-PRIOR [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 85%) |
| JP02 | JN04 + CDE F04 stack equity-DD London x0.25 sticky | +40.4 / +56.6 / +65.6 | +41.6 | +550 / -938 | +29.9 / -3148 | +54.2 / -3622 | +67.8 / +1147 | 84% (64%) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 84%) |
| JP03 | JN04 + CDE F01 max books on 1 London x0.5 | +42.2 / +46.5 / +76.0 | +42.4 | +73 / -1456 | +21.9 / -3947 | +47.0 / -3713 | +69.7 / +419 | 80% (64%) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 80%) |
| JP04 | JN04 x ZS_D0 zone table | +48.1 / +48.1 / +84.6 | +51.8 | +1729 / +4347 | +37.6 / -3198 | +41.7 / -3207 | +72.5 / +2451 | 81% (73%) | OK-PRIOR [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 81%) |
| JP05 | JN04 with LOT = P7 table 7,4,0,4,0,0 | +32.2 / +32.2 / +32.1 | +36.4 | +1472 / +2176 | +27.5 / -1516 | +31.9 / -2290 | +63.0 / +2090 | 84% (73%) | OK-PRIOR [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 84%) |
| JP06 | JN04 x ZS_D0 + R1_3 lock (P7 day loss $8,400 / win $33,600, R on base lots) + F04 | +34.6 / +38.7 / +78.0 | +30.2 | -1426 / +998 | +31.9 / -6025 | +48.6 / -3607 | n/a / n/a | 82% (82%) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 82%) |
| JP07 | JN04 + CF_EN_45 entry engulf @45 s (P7 nyam/nypm; EntryMixin composed, regression JPE0 = JN04) | +50.1 / +50.1 / +82.8 | +56.6 | +4166 / +713 | +56.1 / +465 | +46.9 / -3068 | +65.2 / +2195 | 76% (91%) | OK-PRIOR [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 76%) |
| JP08 | JN04 x ZS_D0 + CF_EN_45 entry | +52.1 / +57.6 / +88.4 | +52.9 | +505 / -1815 | +48.1 / -1240 | +51.9 / -2741 | +72.0 / +2281 | 75% (91%) | OK-PRIOR [old fixed-floor: RECENT-ONLY; floor -3490] (allow 25.0%, WF 75%) |
| JY01 | first-order screen top stack (7-layer search) JY01 | -22.7 / +31.1 / +87.0 | -21.3 | +270 / -1623 | n/a / n/a | +2.0 / -4700 | n/a / n/a | 50% (n/a) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 15.0%, WF 50%) |
| JY02 | first-order top stack JY02 | -27.2 / +22.0 / +86.6 | -30.0 | -472 / -2762 | n/a / n/a | +5.0 / -5000 | n/a / n/a | 50% (n/a) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 15.0%, WF 50%) |
| JY03 | first-order top stack JY03 | -26.4 / +37.5 / +87.3 | -34.9 | -1407 / -1580 | n/a / n/a | +2.3 / -5164 | n/a / n/a | 50% (n/a) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 15.0%, WF 50%) |
| JY04 | first-order top stack JY04 | -27.3 / +8.5 / +73.3 | -43.7 | -2550 / -4615 | n/a / n/a | -3.2 / -6071 | n/a / n/a | 27% (n/a) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 15.0%, WF 27%) |
| JY05 | first-order top stack JY05 (CD optimum) | -38.3 / -9.8 / +55.6 | -164.4 | -10648 / -9931 | n/a / n/a | +18.3 / -5051 | n/a / n/a | 64% (n/a) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 15.0%, WF 64%) |
| JY06 | first-order top stack JY06 | -31.0 / +30.3 / +77.3 | -61.0 | -4166 / -3558 | n/a / n/a | -2.9 / -6507 | n/a / n/a | 27% (n/a) | RECENT-ONLY [old fixed-floor: RECENT-ONLY; floor -3490] (allow 15.0%, WF 27%) |
| JQ01 | JN04 + R5_BO_3 (P7 post cut/stop 30 min same-side blackout) | +11.9 / +11.9 / +71.7 | +17.3 | +1602 / -837 | +24.9 / -2688 | n/a / n/a | n/a / n/a | n/a | PRIOR-UNKNOWN |
| JQ02 | JN04 + R11_any_N30_ALL_SKIP (re-entry table) | +13.4 / +58.8 / +65.4 | +20.9 | +2130 / +4318 | n/a / n/a | n/a / n/a | n/a / n/a | n/a | PRIOR-UNKNOWN |
| JQ03 | JN04 + R7_P3 (bracket policy, R7 hook) | +21.0 / +46.5 / +67.0 | +9.7 | -2782 / +5224 | n/a / n/a | n/a / n/a | n/a / n/a | n/a | PRIOR-UNKNOWN |
| JQ04 | JN04 + R5_BO_3 + R11 (interaction pair) | +14.4 / +29.7 / +31.9 | +17.2 | +721 / -2488 | n/a / n/a | n/a / n/a | n/a / n/a | n/a | PRIOR-UNKNOWN |
| JQ05 | JP07 (JN04 + CF_EN_45) + R11 | +17.1 / +63.0 / +62.9 | +33.2 | +5115 / +4620 | n/a / n/a | n/a / n/a | n/a / n/a | n/a | PRIOR-UNKNOWN |
| JQ06 | JN04 + P7 ATR(14)>=1.6x skip (FGH_PBESTH e18edff4f8d3) | +22.5 / +45.6 / +87.0 | +28.7 | +1936 / +6158 | n/a / n/a | n/a / n/a | n/a / n/a | n/a | PRIOR-UNKNOWN |
| JQ07 | JN04 with REG replaced by P7 ATR>=1.6x skip | +24.2 / +46.5 / +83.3 | +33.2 | +3037 / +1038 | n/a / n/a | n/a / n/a | n/a / n/a | n/a | PRIOR-UNKNOWN |

JPV is the regression of the new JointRep driver against the JN04 table run (must equal JN04 on the months run). CF_EN_45 is composed through the R4 EntryMixin (JP07, JP08) with the ROLLFIX1 blackout guard; JPE0 (entry {} on the JN04 table) equals JN04 on 202606 and 202610. JY01-JY06 (the top stacks of the first-order screen) FAIL exact: L6M cuts -23% to -38% with negative d mean, so the first-order key picks losers; none is a candidate.

## Per-period exact view (ROLL-FIXED; weekly sums, all weeks; maxDD cut and d mean per week vs live in each period)

| stack | HOLD 2025-11..2026-04 | X' 2023-04..2023-12 | X'/PRE 2024-01..2024-06 | PRE 2024-07..2024-12 | PRE 2025-01..2025-06 | L6M 2026-05..10 | GAP 2025-07..2025-10 |
|---|---|---|---|---|---|---|---|
| J03 | +29.2 / -6375 | +72.6 / +5023 | +28.3 / +1011 | +21.0 / -11427 | +33.0 / -4077 | +18.9 / -2855 | n/a |
| JN04 | +45.6 / -4037 | +68.6 / +3635 | +48.5 / -1347 | +39.6 / -7361 | +31.4 / -3072 | +43.4 / +3301 | -1.2 / -7148 |
| JP07 | +56.1 / -2665 | +65.2 / +3372 | +41.8 / -1551 | +34.1 / -7312 | +46.9 / -1772 | +50.1 / +5811 | -5.7 / -7967 |
| JP08 | +48.1 / -2486 | +72.0 / +3689 | +47.3 / -2502 | +40.7 / -7565 | +51.9 / +1 | +52.1 / +2319 | -3.8 / -8764 |
| JP04 | +37.6 / -3900 | +72.5 / +3951 | +46.7 / -2112 | +45.7 / -7376 | +41.7 / -1300 | +48.1 / -223 | +0.6 / -7945 |
| JD01 | +38.3 / -679 | n/a | n/a | -0.5 / -6258 | +24.5 / -3172 | +22.8 / +1646 | +16.3 / -3479 |
| JD02 | +45.1 / -5261 | n/a | n/a | +37.3 / -6336 | +33.8 / -1133 | +44.9 / +3179 | +9.4 / -7211 |
| JD03 | +43.7 / -4759 | n/a | n/a | +34.4 / -4932 | +17.4 / -3021 | +23.1 / +2880 | -6.2 / -4993 |
| JD04 | +37.7 / -4573 | n/a | n/a | +38.1 / -6238 | +26.5 / -3679 | +34.2 / +934 | +4.0 / -6169 |

Reading: in the 2025-07..2025-10 months (run now, so the walk-forward block is contiguous) these stacks cut NO drawdown (-6% to +1%) and lose 7-9k per week of mean; the mean loss of these stacks is concentrated in 2024-H2 (-7k to -11k per week while the live made +23k) and in the HOLD months 2025-11..2026-04 (-1.3k to -6.4k); 2025-H1 loses 1-4k; X' 2023 is mean-positive (+2.7k to +5.0k per week) with 63-73% maxDD cuts; L6M is flat to positive. The PRE problem is therefore not a PRE-only artifact: HOLD shows the same sign, so these stacks buy their drawdown cut with mean in strong-trend months.

## Interaction vs additive (exact; delta vs JN04 for each lead alone, together, and the interaction = together minus the sum of the singles; FLAG = |interaction| > 10% of either single)

| pair | metric | R5_BO_3 alone | R11 alone | both | interaction | flag |
|---|---|---|---|---|---|---|
| R5_BO_3 x R11 on JN04 | L6M maxDD cut % | -31.5 | -30.0 | -29.1 | +32.5 | FLAG |
| R5_BO_3 x R11 on JN04 | L6M d mean $/wk | -3257 | -2730 | -4138 | +1849 | FLAG |

## JN04 / JP07 as live definitions (full page: autopilot/DS3_JN04_LIVE_DEFS.md)

| layer | rule in one line | DS7 v1.4 / v1.6 fields | status |
|---|---|---|---|
| LOT | P7 only: shadow-equity Calmar over the last 10 completed label days < 1.0 -> lots x0.5 | none in v1.4; NEW v1.6: P7PerfGateMode / Days=10 / CalmarBelow=1.0 / Mult=0.5 | new code (shadow base-lot ledger) |
| SIGQ | all books: dA (points to the nearest untouched zone line ahead) >= 70th percentile of previous months -> x0.5 | closest Ss1..4 HalveTop3 (PdAhead); NEW: ZoneAheadPts feature + pooled quantile mode | new code; weakest layer (marginal) |
| REG | P7 only: 5-min ATR(14) / 20-day median-of-daily-medians >= 1.3 -> x0.5 | AtrRatio exists but on 1-min RMA with tercile templates; NEW: AtrRatio5m + HalveAbove 1.3 | new code |
| STACK | any book, London: truncate lots to 6 - same-side open lots of the other books (skip at <= 0) | none (group 09 StackCut is stop-triggered); NEW: ExpCapMode / Lots=6 / Sessions=0,1,0,0,0,0 | new code; rule-mode exact run JR01 pending |
| JP07 entry | P7 NY-AM/NY-PM confirmation pattern ThreeBar -> Engulf (45 s bars) | ConfirmPatternA = Engulf (panel value only) | no new code |

## Rule 2a relabel under the 2026-11-10 13:45Z decision (PRE mean floor = 25% of live PRE mean) and which stacks clear everything

Live weekly means used (ROLLFIX1, carry week dropped): PRE 14408, HOLD 16391, X' 1645, L6M 22949 $/wk. Rule 2a PRE mean floor = -25% x live PRE mean = -3602 $/wk (old fixed floor -1000).

Conditions: R = recents (L6M cut > 0 and L3M cut > -3); H = HOLD cut > 0 and HOLD d mean >= -25% of live HOLD mean (-4098); P = rule 2a PRE label OK-PRIOR (PRE maxDD allowance min(25, L6M cut + 10)% if WF >= 60% else 15%, PRE mean floor -3602); X = X' tolerant (cut > 0, d mean >= -1000); W = contiguous bi-weekly WF 2023-04..2026-10 beat share >= 60%; GAP = 2025-07..10 d mean / cut (reported, not a gate).

| stack | R | H (cut / d mean) | P new label (old) PRE cut / d mean | X (cut / d mean) | W (WF %, full block) | GAP d mean / cut | clears all |
|---|---|---|---|---|---|---|---|
| F08 | yes (26.5 / 26.5) | yes (39.8 / +1922) | OK-PRIOR (RECENT-ONLY) 28.0 / -2063 | yes (52.9 / +2007) | NO (64%, no) | +nan / +nan | no |
| J03 | yes (18.9 / 52.0) | yes (29.2 / -1809) | RECENT-ONLY (RECENT-ONLY) 33.0 / -6170 | yes (72.6 / +3623) | NO (65%, no) | +nan / +nan | no |
| JL01 | yes (29.0 / 29.0) | yes (29.3 / -3207) | RECENT-ONLY (RECENT-ONLY) 37.9 / -4452 | yes (71.3 / +2509) | NO (85%, no) | +nan / +nan | no |
| JN02 | yes (28.8 / 28.8) | yes (12.8 / -1521) | OK-PRIOR (RECENT-ONLY) 36.9 / -3265 | n/a (nan / +nan) | NO (82%, no) | +nan / +nan | no |
| JN03 | yes (39.0 / 39.0) | yes (24.8 / -2593) | OK-PRIOR (RECENT-ONLY) 37.6 / -3107 | yes (68.8 / +2543) | NO (82%, no) | +nan / +nan | no |
| JN04 | yes (43.4 / 43.4) | yes (45.6 / -1456) | RECENT-ONLY (RECENT-ONLY) 31.4 / -3620 | yes (68.6 / +2252) | yes (76%, yes) | -7148 / -1.2 | no |
| JN05 | yes (35.2 / 35.2) | yes (14.9 / -1484) | RECENT-ONLY (RECENT-ONLY) 18.4 / -4001 | n/a (nan / +nan) | NO (70%, no) | +nan / +nan | no |
| JN06 | yes (27.0 / 27.0) | yes (33.7 / -2519) | OK-PRIOR (RECENT-ONLY) 29.4 / -3311 | n/a (nan / +nan) | NO (76%, no) | +nan / +nan | no |
| JP01 | yes (42.6 / 42.6) | yes (49.6 / -2559) | OK-PRIOR (RECENT-ONLY) 41.7 / -3218 | yes (66.2 / +1165) | NO (85%, no) | +nan / +nan | no |
| JP02 | yes (40.4 / 56.6) | yes (29.9 / -3148) | RECENT-ONLY (RECENT-ONLY) 54.2 / -3622 | yes (67.8 / +1147) | NO (84%, no) | +nan / +nan | no |
| JP03 | yes (42.2 / 46.5) | yes (21.9 / -3947) | RECENT-ONLY (RECENT-ONLY) 47.0 / -3713 | yes (69.7 / +419) | NO (80%, no) | +nan / +nan | no |
| JP04 | yes (48.1 / 48.1) | yes (37.6 / -3198) | OK-PRIOR (RECENT-ONLY) 41.7 / -3207 | yes (72.5 / +2451) | yes (81%, yes) | -7945 / +0.6 | YES |
| JP05 | yes (32.2 / 32.2) | yes (27.5 / -1516) | OK-PRIOR (RECENT-ONLY) 31.9 / -2290 | yes (63.0 / +2090) | NO (84%, no) | +nan / +nan | no |
| JP06 | yes (34.6 / 38.7) | NO (31.9 / -6025) | RECENT-ONLY (RECENT-ONLY) 48.6 / -3607 | n/a (nan / +nan) | NO (82%, no) | +nan / +nan | no |
| JP07 | yes (50.1 / 50.1) | yes (56.1 / +465) | OK-PRIOR (RECENT-ONLY) 46.9 / -3068 | yes (65.2 / +2195) | yes (76%, yes) | -7967 / -5.7 | YES |
| JP08 | yes (52.1 / 57.6) | yes (48.1 / -1240) | OK-PRIOR (RECENT-ONLY) 51.9 / -2741 | yes (72.0 / +2281) | yes (75%, yes) | -8764 / -3.8 | YES |

Stacks clearing every condition: JP04, JP07, JP08.


## Trend-regime diagnosis (exact, ROLL-FIXED): which JN04 layer costs the mean in the trend regimes, and do the new layer leads repair it

Cells: maxDD cut % / d mean $/wk vs live in each period. JD rows = JN04 with one layer removed; the layer's cost in a period = JN04 minus the JD row (d mean). JQ rows = JN04 plus a new lead.

| stack | what | PRE 2024-07..2024-12 | PRE 2025-01..2025-06 | GAP 2025-07..2025-10 | HOLD 2025-11..2026-04 | L6M 2026-05..10 |
|---|---|---|---|---|---|---|
| JN04 | JN04 (reference: LOT P7 cap + SIGQ + REG + STACK E cap6) | +39.6 / -7361 | +31.4 / -3072 | -1.2 / -7148 | +45.6 / -4037 | +43.4 / +3301 |
| JD01 | JN04 minus LOT (p7_other:f4181da4c118) | -0.5 / -6258 | +24.5 / -3172 | +16.3 / -3479 | +38.3 / -679 | +22.8 / +1646 |
| JD02 | JN04 minus SIGQ (signal_quality:b9a6edabcd7b) | +37.3 / -6336 | +33.8 / -1133 | +9.4 / -7211 | +45.1 / -5261 | +44.9 / +3179 |
| JD03 | JN04 minus REG (regime:f1f4301eae70) | +34.4 / -4932 | +17.4 / -3021 | -6.2 / -4993 | +43.7 / -4759 | +23.1 / +2880 |
| JD04 | JN04 minus STACK (exposure_stack:E|same_side_lots_cap|cap6_trunc|sess_london) | +38.1 / -6238 | +26.5 / -3679 | +4.0 / -6169 | +37.7 / -4573 | +34.2 / +934 |

Largest mean cost per period: PRE 2024-07..2: REG costs +2429 $/wk; PRE 2025-01..2: SIGQ costs +1938 $/wk; GAP 2025-07..2: LOT costs +3668 $/wk; HOLD 2025-11..2: LOT costs +3358 $/wk; L6M: no single layer costs mean. Note the trade-off: dropping the P7 lot cap (LOT) repairs mean and gap drawdown but halves the recents cut (L6M cut 22.8% vs 43.4%).


Layer cost in mean per week (JN04 minus the leave-one-out): JD01 (layer LOT (p7_other:f4181da4c118)): PRE 2024-07 -1103, PRE 2025-01 +100, GAP 2025-07 -3668, HOLD 2025-11 -3358, L6M 2026-05 +1655; JD02 (layer SIGQ (signal_quality:b9a6edabcd7b)): PRE 2024-07 -1025, PRE 2025-01 -1938, GAP 2025-07 +63, HOLD 2025-11 +1223, L6M 2026-05 +122; JD03 (layer REG (regime:f1f4301eae70)): PRE 2024-07 -2429, PRE 2025-01 -51, GAP 2025-07 -2155, HOLD 2025-11 +722, L6M 2026-05 +421; JD04 (layer STACK (exposure_stack:E|same_side_): PRE 2024-07 -1123, PRE 2025-01 +607, GAP 2025-07 -979, HOLD 2025-11 +536, L6M 2026-05 +2367.

## REFIT 2026-11-22 from EXACT ROLL-FIXED series (35 exact stacks with the full 2026-05..10 block; train = trailing 26 weeks to 2026-11-05)

Ranking = Z.refit_pick (maxDD, worst-20, Ulcer, mean). Live trailing: maxDD 79907, mean 24125/wk.

Pick among all candidates: **JP08**. Pick among candidates whose trailing mean is not below live: **JP08**.

| rank | stack | trailing maxDD | worst-20 | mean/wk | rule 2a label (PRE exact) |
|---|---|---|---|---|---|
| 1 | JP08 | 38301 | 272333 | 26122 | RECENT-ONLY (allow 25.0%, WF 75%) |
| 2 | JP07 | 39878 | 326224 | 29334 | RECENT-ONLY (allow 25.0%, WF 76%) |
| 3 | JP04 | 41501 | 204974 | 23946 | RECENT-ONLY (allow 25.0%, WF 81%) |
| 4 | JN04 | 45203 | 266189 | 27187 | RECENT-ONLY (allow 25.0%, WF 76%) |
| 5 | JP01 | 45880 | 233710 | 25352 | RECENT-ONLY (allow 25.0%, WF 85%) |
| 6 | JP03 | 46157 | 220338 | 25450 | RECENT-ONLY (allow 25.0%, WF 80%) |
| 7 | JP02 | 47594 | 251694 | 26137 | RECENT-ONLY (allow 25.0%, WF 84%) |
| 8 | JN03 | 48727 | 203100 | 23553 | RECENT-ONLY (allow 25.0%, WF 82%) |
| 9 | JN05 | 51781 | 202875 | 24141 | RECENT-ONLY (allow 25.0%, WF 70%) |
| 10 | JP06 | 52249 | 163702 | 20945 | RECENT-ONLY (allow 25.0%, WF 82%) |

Candidates with trailing mean >= live, best 5: JP08 (maxDD 38301, mean 26122, RECENT-ONLY); JP07 (maxDD 39878, mean 29334, RECENT-ONLY); JN04 (maxDD 45203, mean 27187, RECENT-ONLY); JP01 (maxDD 45880, mean 25352, RECENT-ONLY); JP03 (maxDD 46157, mean 25450, RECENT-ONLY).

This is the pick of a screen over 35 stacks chosen by earlier steps (in-sample over the recent block), not a validated deployment; the bi-weekly WF columns above are the out-of-sample evidence.


## Plain sentence

EXACT (recents first): the best exact joint stack so far is J03: it lowers L6M maxDD +18.9% at equal lots (+20.4% at equal mean, d mean +434 $/wk), L3M +52.0%, L1M +56.4%; it differs from live in these layers: SIZER=sizer_vt:b914834619ab, LOT=p7_other:f4181da4c118, SIGQ=signal_quality:b9a6edabcd7b, REG=regime:f1f4301eae70, STACK=exposure_stack:E, same_side_lots_cap, cap6_trunc, sess_london, COOL=cooldown:52f0e4f39d4c. On the prior it reads: PRE cut +31.5% with d mean -6395 $/wk and X' cut +70.8%; standing rule 2a label: RECENT-ONLY (allow 25.0%, WF 68%).

First-order screen: the best first-order joint stack lowers L6M maxDD +100.0% at equal mean (PRE +84.0%, X' +83.1%) and differs from live in these layers: SIZER=reg:sizer:AB_73ca99b0ec2d, LOT=reg:lot_tables:lot_greedy_down, REG=regime:e18edff4f8d3, COOL=cooldown:fbe1c726c9b2, A06=reg:a06_slots:a06_greedy_down, B02=reg:b02:B02_K7P7H7_20_1.00_alld_0.0. The screen is lot-level layers only, in-sample, and first-order overstates badly (exact J-pair and joint-stack runs gave a fraction of it). The verdict comes from exact runs, the bi-weekly re-pick WF and the REFIT section; cut / profit / lock / entry / NTZ layers join only through exact hooks.
