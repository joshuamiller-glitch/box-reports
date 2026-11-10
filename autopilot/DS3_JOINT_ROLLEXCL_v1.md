# DS3_JOINT - everything with everything (T-JOINT), version 1 (2026-11-09 21:25Z)

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
| B02 | 5 | reg |

## Registered layers (/mnt/l2/l2vast/_th_joint/layers/*/topK.json)

Static-M layers (multiplier arrays, composable first-order by product): a06_slots: 2 cells incl. live; b02: 5 cells incl. live; cooldown_r5: 1 cells incl. live; cooldowns: 1 cells incl. live; entry: 1 cells incl. live; hm5: 1 cells incl. live; locks: 1 cells incl. live; lot_tables: 4 cells incl. live; ntz: 1 cells incl. live; o7: 1 cells incl. live; ote: 1 cells incl. live; shadow: 2 cells incl. live; sizer: 5 cells incl. live; stack_cut: 1 cells incl. live; zone: 5 cells incl. live. In the screen: SIZER, LOT, ZONE, A06, B02 take the registered cells first (then the stand-in grids); hm5 and stack_cut registered only the live setting.

Trade-list / hook layers (NOT multiplier-composable: they change exits, re-entries, locks, entries; verdicts only from joint exact runs through their hooks): a06_slots: 1 cells; cooldown_r5: 5 cells; cooldowns: 5 cells; cut: 5 cells; entry: 4 cells; locks: 5 cells; lot_tables: 1 cells; ntz: 5 cells; o7: 4 cells; ote: 4 cells; profit: 64 cells; shadow: 8 cells.


## Top-10 joint stacks, first-order screen (full factorial of the top-5 per layer, distinct lot arrays)

Key (standing rule 2, recents first) = min over L6M / L3M of the maxDD cut at EQUAL MEAN to the live stack (global lot scale), then HOLD, worst-20; d mean at equal lots shown. Window cuts below are at equal mean.

| # | SIZER | LOT | SIGQ | REG | STACK | COOL | ZONE | A06 | B02 | key | eq cut L6M / HOLD / PRE / X' | cut at equal lots L6M | d mean L6M | worst-20 L6M cell / live | PRE tolerance | stage |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | live | live | live | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZNC_B0 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +87.3 / +87.8 / +88.4 | +100.0 | -1022 | 294k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 2 | live | reg:lot_tables:lot_P7_744 | live | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZNC_B0 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +88.9 / +86.2 / +86.2 | +100.0 | -1895 | 275k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 3 | live | reg:lot_tables:lot_P7_644 | live | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZNC_B0 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +89.0 / +87.0 / +85.1 | +100.0 | -3142 | 268k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 4 | live | live | signal_quality:73c32e59f366 | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZNC_B0 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +80.1 / +87.6 / +87.8 | +100.0 | -3176 | 243k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 5 | live | reg:lot_tables:lot_P7_644 | signal_quality:73c32e59f366 | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZNC_B0 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +79.6 / +86.5 / +88.5 | +100.0 | -5112 | 220k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 6 | reg:sizer:AB_73ca99b0ec2d | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +87.3 / +84.0 / +83.1 | +100.0 | -5733 | 216k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 7 | reg:sizer:VT_S2 | reg:lot_tables:lot_P7_744 | live | regime:e18edff4f8d3 | live | cooldown:6e18cc85a3d6 | reg:zone:ZNC_B0 | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +86.2 / +85.7 / +82.4 | +100.0 | -3872 | 247k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 8 | live | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +86.0 / +84.6 / +83.4 | +100.0 | -4237 | 238k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 9 | live | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:6e18cc85a3d6 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +88.7 / +84.3 / +80.9 | +100.0 | -4274 | 241k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 10 | reg:sizer:AB_73ca99b0ec2d | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:6e18cc85a3d6 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +90.4 / +81.6 / +81.7 | +100.0 | -5770 | 219k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |

## Coordinate descent (live + 10 random starts, one layer at a time against the key)

| start | local optimum | key |
|---|---|---|
| live | SIZER=sizer_vt:e3f124a36d05 / LOT=reg:lot_tables:lot_greedy_down / SIGQ=signal_quality:67c701bb2705 / REG=regime:72ffa1d9c2fa / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:f511b70e6d8d / ZONE=live / A06=live / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.3 |
| random | SIZER=sizer_vt:c5f9e199982a / LOT=p7_other:3f44a5a78d9d / SIGQ=signal_quality:a08183547df2 / REG=regime:9ecb10dea3f9 / STACK=exposure_stack:E|corr_same_sid / COOL=cooldown:e650bffd7445 / ZONE=zone:e34226b932fa / A06=live / B02=reg:b02:B02_allbooks_5_1.50_al | 100.3 |
| random | SIZER=sizer_vol:1b5942ac8cd6 / LOT=reg:lot_tables:lot_greedy_down / SIGQ=signal_quality:894921a2d1c4 / REG=regime:0c9d251dc8cd / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:9f55d2c16275 / ZONE=zone:465821f8c60d / A06=live / B02=live | 100.3 |
| random | SIZER=sizer_vt:cc447c626f19 / LOT=p7_other:b8c7a11b7c62 / SIGQ=signal_quality:f591c705629b / REG=regime:e18edff4f8d3 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:6e18cc85a3d6 / ZONE=zone:7570c5ff7f2d / A06=live / B02=reg:b02:B02_allbooks_5_1.50_al | 100.3 |
| random | SIZER=sizer_vt:419ae68d5979 / LOT=p7_other:3e206f50c848 / SIGQ=signal_quality:e37f04b47dd5 / REG=regime:f1f4301eae70 / STACK=equity_state:D|dayloss_stack$| / COOL=cooldown:8b279ff8d6b8 / ZONE=zone:f75e4f990fd9 / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.4 |
| random | SIZER=sizer_vt:c5f9e199982a / LOT=p7_other:e230bca41b25 / SIGQ=signal_quality:2aeb93aa1b83 / REG=regime:a4041f165b35 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:8b279ff8d6b8 / ZONE=live / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_allbooks_5_1.50_al | 100.4 |
| random | SIZER=sizer_vt:92ddfe458baa / LOT=p7_other:3e206f50c848 / SIGQ=signal_quality:1d9d637a3a48 / REG=regime:910b86c59480 / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:10d9b4521e81 / ZONE=zone:f75e4f990fd9 / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.4 |
| random | SIZER=sizer_vt:5cdd27c75bf6 / LOT=reg:lot_tables:lot_greedy_down / SIGQ=signal_quality:98d80d0f642a / REG=regime:9a89fe48f047 / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:446ba756b578 / ZONE=zone:8031aee5ac1d / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.20_all | 100.3 |
| random | SIZER=sizer_vt:6df60ffc81f9 / LOT=p7_other:ac4e6310f17b / SIGQ=signal_quality:a08183547df2 / REG=regime:27a5724a4970 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:c6feb36a19bf / ZONE=zone:f8fbee4f18de / A06=reg:a06_slots:a06_greedy_down / B02=live | 100.4 |
| random | SIZER=sizer_vt:cc447c626f19 / LOT=p7_other:670dace4be4b / SIGQ=signal_quality:67c701bb2705 / REG=regime:910b86c59480 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:7cbfe396fd8d / ZONE=reg:zone:ZNC_B0 / A06=live / B02=reg:b02:B02_K7P7H7_20_1.20_all | 100.3 |
| random | SIZER=sizer_vt:7b692e38e6f1 / LOT=p7_other:bb051ae7284e / SIGQ=signal_quality:edafdf244894 / REG=regime:0916c957cf91 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:e650bffd7445 / ZONE=reg:zone:ZNC_B0 / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.20_all | 100.3 |

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

- Placebo / family null over the joint space: 5000 random stacks over the full grids give key quantiles median 65.5, 90% 84.5, 99% 94.7, max 100.3. The best factorial stack key is 100.4: it is above the best random stack, i.e. the full-grid random search finds stacks as good as the top-K factorial (no evidence that top-K selection matters; family p for the best stack over this joint space is about 1 (it is the maximum of a searched set)).
- Joint walk-forward (monthly, purged 7 d, trailing 26 weeks, candidate pool = live + 1500 random stacks NOT selected on full-sample data, pick by equal-mean train maxDD): OOS maxDD cut +84.6% vs live, d mean -9388 $/wk, live kept in 0 of 34 months. The pick procedure does cut OOS maxDD but gives up mean (it is mostly an exposure reduction).
- STANDING RULE 2 primary OOS test, bi-weekly re-pick WF (trailing 26 weeks -> next 2 weeks, purged 7 d) of the whole joint procedure: 75 refit periods since 2024-01, OOS maxDD cut +80.3% with d mean -9926 $/wk; the pick beat live (period P&L >= live and in-period drawdown <= live) in 36% of periods (P&L alone 36%); since 2026-05-12 (13 periods): 46% beat, 46% P&L-ge.
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

## Exact vs first-order (so far)

First-order keys of these stacks were 86-88% (equal-mean cut). Exact engine: J01: L6M eq-mean cut +1.9 / d mean -2287, PRE eq-mean cut +23.7 / d mean -4319, X' eq-mean cut +59.0 / d mean +882; J02: L6M eq-mean cut -4.2 / d mean -3878, PRE eq-mean cut +26.3 / d mean -4191, X' eq-mean cut +66.7 / d mean +4678; J03: L6M eq-mean cut +20.4 / d mean +434, PRE eq-mean cut +32.8 / d mean -6395, X' eq-mean cut +71.4 / d mean +3593; J04: L6M eq-mean cut -4.7 / d mean -3945, PRE eq-mean cut +31.2 / d mean -4611, X' eq-mean cut +61.2 / d mean +2059.

Reading: the first-order joint screen of stacked down-sizing layers is NOT predictive of the engine. In the exact run a skipped signal frees the book, which then takes the next signal, and re-entries / locks / slice fills change; so a table that skips 60-85% of signals first-order removes only about 18% of the trades in the engine (F08 pair: 672 vs 823 trades in 202610, lots 1440 vs 1746) and behaves like a mild global lot reduction. Only exact numbers count. Missing windows are still running.

## REFIT 2026-11-22 (what the bi-weekly procedure would pick today; first-order screen, train = trailing 26 weeks to 2026-11-05, pick = lowest equal-mean train maxDD among live + 1500 random stacks)

Pick: SIZER=reg:sizer:VT_S2 | LOT=p7_other:593dae045f4a | SIGQ=signal_quality:d4304aa7f37a | REG=regime:8715ffc91335 | STACK=exposure_stack:E|total_lots_cap|cap6_skip|P7_sess_nyam | COOL=cooldown:50db603d2c5a | ZONE=zone:5fe923a731af | A06=reg:a06_slots:a06_greedy_down | B02=live. Train maxDD at equal mean 408 vs live 79907. NOT exact-confirmed; the verdict needs the exact runs.

Standing rule 2 tolerance check of the top-10 stacks: PRE maxDD not more than 15% deeper than live and PRE mean not below live - 1k; failing stacks are labelled RECENT-ONLY (reported, not killed).

## Plain sentence

EXACT (recents first): the best exact joint stack so far is J03: it lowers L6M maxDD +18.9% at equal lots (+20.4% at equal mean, d mean +434 $/wk), L3M +52.0%, L1M +56.4%; it differs from live in these layers: SIZER=sizer_vt:b914834619ab, LOT=p7_other:f4181da4c118, SIGQ=signal_quality:b9a6edabcd7b, REG=regime:f1f4301eae70, STACK=exposure_stack:E, same_side_lots_cap, cap6_trunc, sess_london, COOL=cooldown:52f0e4f39d4c. On the prior it reads: PRE cut +31.5% with d mean -6395 $/wk and X' cut +70.8%; standing rule 2a label: RECENT-ONLY (allow 25.0%, WF 68%).

First-order screen: the best first-order joint stack lowers L6M maxDD +100.0% at equal mean (PRE +87.8%, X' +88.4%) and differs from live in these layers: REG=regime:e18edff4f8d3, COOL=cooldown:5adf9b2c9b46, ZONE=reg:zone:ZNC_B0, A06=reg:a06_slots:a06_greedy_down, B02=reg:b02:B02_K7P7H7_20_1.00_alld_0.0. The screen is lot-level layers only, in-sample, and first-order overstates badly (exact J-pair and joint-stack runs gave a fraction of it). The verdict comes from exact runs, the bi-weekly re-pick WF and the REFIT section; cut / profit / lock / entry / NTZ layers join only through exact hooks.
