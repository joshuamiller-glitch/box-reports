# DS3_JOINT - everything with everything (T-JOINT), version 1 (2026-11-09 17:51Z)

**ROLL-EXCL (33 contract-roll artifact trades excluded). FIRST-ORDER SCREEN ONLY. PRE-PROOF, post-hoc, shadow only, no PASS claims. Every layer stays ON in every stack: option 0 of each layer is the live setting (multiplier 1).** The layer pools are stand-ins built by SZ-IJK from the owners' multiplier files (M_*.npz, the lot-level layers only) until the owners write /mnt/l2/l2vast/_th_joint/layers/<layer>/topK.json. Cut / profit-rule / lock / entry layers are NOT multiplier-composable and are not in this version.

## Capacity budget (measured)

Exact engine throughput about 24 cell-months/hour/worker with month batching, 6 workers shared box-wide. One stack on L6M+PRE+X' = 33 months = 1.4 worker-hours; HOLD adds 6 months. A 243-stack factorial = 8,000 cell-months = 55 hours of ALL six workers; 3,125 stacks = about 3 weeks. NOT tractable exactly. Used instead: (1) first-order composable screen over every composable stack: full factorial of the top-5 per layer (279936 stacks) plus 5000 random stacks over the 60-cell grids and coordinate descent from live + 10 random starts (about 1 minute of one core); (2) exact runs on L6M+PRE+X' only for the top stacks and every coordinate-descent local optimum (batch mode, about 1.5 stacks/hour at 2 workers); (3) first-order overstates: for the J pairs the exact L6M equal-mean cut was about half the first-order value.

## Layers and pools (lot-level layers, first-order composable)

| layer | options (live + top by DD-first key, grid 60) | pool source |
|---|---|---|
| SIZER | 61 | sizer_vol, sizer_vt |
| LOT | 61 | p7_other |
| SIGQ | 61 | signal_quality |
| REG | 61 | regime |
| STACK | 61 | equal_risk, equity_state, exposure_stack |
| COOL | 61 | cooldown |
| ZONE | 61 | zone |

## Top-10 joint stacks, first-order screen (full factorial of the top-5 per layer, distinct lot arrays)

Key = min over L6M / PRE / X' of the maxDD cut at EQUAL MEAN to the live stack (global lot scale), then HOLD, worst-20; d mean at equal lots shown. Window cuts below are at equal mean.

| # | SIZER | LOT | SIGQ | REG | STACK | COOL | ZONE | key | eq cut L6M / HOLD / PRE / X' | cut at equal lots L6M | d mean L6M | worst-20 L6M cell / live | stage |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | sizer_vt:cab7b88a3ae5 | p7_other:b8c7a11b7c62 | live | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | live | 80.8 | +89.9 / +43.3 / +80.8 / +82.5 | +91.3 | -2942 | 250k / 165k | FIRST-ORDER SCREEN ONLY |
| 2 | sizer_vt:cab7b88a3ae5 | p7_other:b8c7a11b7c62 | signal_quality:73c32e59f366 | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | live | 80.0 | +93.1 / +50.2 / +80.0 / +81.6 | +94.3 | -3877 | 232k / 165k | FIRST-ORDER SCREEN ONLY |
| 3 | sizer_vt:cab7b88a3ae5 | p7_other:b8c7a11b7c62 | signal_quality:73c32e59f366 | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$2400|P7 | cooldown:6e18cc85a3d6 | live | 79.8 | +88.4 / +41.5 / +79.8 / +81.9 | +91.8 | -6571 | 189k / 165k | FIRST-ORDER SCREEN ONLY |
| 4 | sizer_vt:cab7b88a3ae5 | p7_other:b8c7a11b7c62 | signal_quality:f591c705629b | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | live | 79.5 | +85.3 / +36.6 / +79.5 / +81.1 | +88.1 | -4329 | 226k / 165k | FIRST-ORDER SCREEN ONLY |
| 5 | sizer_vt:ed624ef2d5e6 | p7_other:b8c7a11b7c62 | signal_quality:f591c705629b | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | live | 79.4 | +82.4 / +39.2 / +79.4 / +80.4 | +83.8 | -1731 | 271k / 165k | FIRST-ORDER SCREEN ONLY |
| 6 | sizer_vt:cab7b88a3ae5 | p7_other:2710ebd7314f | live | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:fbe1c726c9b2 | live | 79.1 | +93.9 / +49.9 / +79.1 / +79.9 | +94.4 | -1843 | 258k / 165k | FIRST-ORDER SCREEN ONLY |
| 7 | sizer_vt:cab7b88a3ae5 | p7_other:ac4e6310f17b | live | regime:e18edff4f8d3 | live | cooldown:c1b730e63dd6 | live | 79.1 | +90.6 / +62.5 / +79.5 / +79.1 | +91.0 | -798 | 264k / 165k | FIRST-ORDER SCREEN ONLY |
| 8 | sizer_vt:cab7b88a3ae5 | live | live | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:c1b730e63dd6 | live | 79.1 | +89.2 / +62.0 / +79.1 / +79.9 | +91.2 | -4167 | 213k / 165k | FIRST-ORDER SCREEN ONLY |
| 9 | sizer_vt:cab7b88a3ae5 | live | signal_quality:f591c705629b | live | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:c1b730e63dd6 | live | 78.9 | +83.9 / +54.8 / +80.8 / +78.9 | +87.6 | -5059 | 186k / 165k | FIRST-ORDER SCREEN ONLY |
| 10 | sizer_vt:cab7b88a3ae5 | live | signal_quality:73c32e59f366 | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$2400|P7 | cooldown:6e18cc85a3d6 | live | 78.9 | +87.7 / +42.4 / +78.9 / +82.4 | +91.2 | -6332 | 189k / 165k | FIRST-ORDER SCREEN ONLY |

## Coordinate descent (live + 10 random starts, one layer at a time against the key)

| start | local optimum | key |
|---|---|---|
| live | SIZER=sizer_vt:cab7b88a3ae5 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:f5e0f94f4e48 / REG=regime:0916c957cf91 / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:8b279ff8d6b8 / ZONE=live | 85.8 |
| random | SIZER=sizer_vt:419ae68d5979 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:54892748d6f6 / REG=regime:4ea126879bc5 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:ba3a911f09dd / ZONE=zone:f3aaf20b5270 | 80.3 |
| random | SIZER=sizer_vt:cab7b88a3ae5 / LOT=p7_other:29234d9766a9 / SIGQ=signal_quality:6b7b2de4509f / REG=regime:34e6b81002b1 / STACK=equity_state:D|eqdd_stack_20d| / COOL=cooldown:fbe1c726c9b2 / ZONE=zone:d58e6420fc65 | 83.9 |
| random | SIZER=sizer_vt:1e464d797671 / LOT=p7_other:5cc859f6b289 / SIGQ=signal_quality:67c701bb2705 / REG=regime:8715ffc91335 / STACK=exposure_stack:E|corr_same_sid / COOL=cooldown:dc05c08da340 / ZONE=zone:d58e6420fc65 | 83.4 |
| random | SIZER=sizer_vt:ed624ef2d5e6 / LOT=p7_other:3f44a5a78d9d / SIGQ=signal_quality:cfe2f21cee78 / REG=regime:8715ffc91335 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:6e18cc85a3d6 / ZONE=zone:f8fbee4f18de | 89.0 |
| random | SIZER=sizer_vol:7516311b6c67 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:6413b77d4f0f / REG=regime:66c60fa89c89 / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:854b949372c0 / ZONE=zone:4cf87019e3e9 | 74.8 |
| random | SIZER=sizer_vt:cab7b88a3ae5 / LOT=p7_other:cd1a7df33ff4 / SIGQ=signal_quality:98d80d0f642a / REG=regime:8715ffc91335 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:e650bffd7445 / ZONE=zone:f8fbee4f18de | 87.9 |
| random | SIZER=sizer_vt:cab7b88a3ae5 / LOT=p7_other:baa6bbb5523c / SIGQ=signal_quality:54892748d6f6 / REG=regime:d11857aae126 / STACK=equity_state:D|eqdd_book_20d_R / COOL=cooldown:8b279ff8d6b8 / ZONE=live | 86.1 |
| random | SIZER=sizer_vt:cab7b88a3ae5 / LOT=p7_other:baa6bbb5523c / SIGQ=signal_quality:6b7b2de4509f / REG=regime:8715ffc91335 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:72dcb1f928a1 / ZONE=zone:967d8a6a25a7 | 87.6 |
| random | SIZER=sizer_vt:cab7b88a3ae5 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:b765dec1cee2 / REG=regime:8715ffc91335 / STACK=equity_state:D|eqdd_book_20d_R / COOL=cooldown:2f1c1eaa9261 / ZONE=zone:62448442efbe | 86.0 |
| random | SIZER=sizer_vt:e3f124a36d05 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:939256846c67 / REG=regime:d11857aae126 / STACK=equity_state:D|dayloss_stack$| / COOL=cooldown:f511b70e6d8d / ZONE=zone:698af8273f74 | 84.4 |

## Interaction table (best single cell per layer by key; pair gain minus the sum of single gains, equal-mean L6M cut points; FLAG = |interaction| > 10% of either single gain)

| layer a | layer b | cell a | cell b | gain a | gain b | pair | interaction | flag |
|---|---|---|---|---|---|---|---|---|
| SIZER | ZONE | sizer_vt:cab7b88a3ae5 | zone:e2b9736063c7 | +78.9 | +57.0 | +70.5 | -65.4 | FLAG |
| LOT | ZONE | p7_other:b8c7a11b7c62 | zone:e2b9736063c7 | +36.5 | +57.0 | +52.2 | -41.2 | FLAG |
| STACK | ZONE | equal_risk:C|riskcap_per_trade|R$3 | zone:e2b9736063c7 | +35.5 | +57.0 | +57.2 | -35.3 | FLAG |
| REG | ZONE | regime:e18edff4f8d3 | zone:e2b9736063c7 | +31.9 | +57.0 | +55.7 | -33.2 | FLAG |
| SIZER | LOT | sizer_vt:cab7b88a3ae5 | p7_other:b8c7a11b7c62 | +78.9 | +36.5 | +84.2 | -31.2 | FLAG |
| LOT | REG | p7_other:b8c7a11b7c62 | regime:e18edff4f8d3 | +36.5 | +31.9 | +39.0 | -29.4 | FLAG |
| SIZER | REG | sizer_vt:cab7b88a3ae5 | regime:e18edff4f8d3 | +78.9 | +31.9 | +82.6 | -28.2 | FLAG |
| SIZER | STACK | sizer_vt:cab7b88a3ae5 | equal_risk:C|riskcap_per_trade|R$3 | +78.9 | +35.5 | +86.3 | -28.2 | FLAG |
| LOT | STACK | p7_other:b8c7a11b7c62 | equal_risk:C|riskcap_per_trade|R$3 | +36.5 | +35.5 | +46.0 | -26.0 | FLAG |
| SIZER | COOL | sizer_vt:cab7b88a3ae5 | cooldown:fbe1c726c9b2 | +78.9 | +29.7 | +83.3 | -25.4 | FLAG |
| REG | STACK | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3 | +31.9 | +35.5 | +45.3 | -22.1 | FLAG |
| LOT | SIGQ | p7_other:b8c7a11b7c62 | signal_quality:1d9d637a3a48 | +36.5 | +28.1 | +47.5 | -17.1 | FLAG |
| SIZER | SIGQ | sizer_vt:cab7b88a3ae5 | signal_quality:1d9d637a3a48 | +78.9 | +28.1 | +91.0 | -16.1 | FLAG |
| STACK | COOL | equal_risk:C|riskcap_per_trade|R$3 | cooldown:fbe1c726c9b2 | +35.5 | +29.7 | +50.8 | -14.5 | FLAG |
| COOL | ZONE | cooldown:fbe1c726c9b2 | zone:e2b9736063c7 | +29.7 | +57.0 | +73.2 | -13.5 | FLAG |
| LOT | COOL | p7_other:b8c7a11b7c62 | cooldown:fbe1c726c9b2 | +36.5 | +29.7 | +53.6 | -12.6 | FLAG |
| SIGQ | STACK | signal_quality:1d9d637a3a48 | equal_risk:C|riskcap_per_trade|R$3 | +28.1 | +35.5 | +51.8 | -11.8 | FLAG |
| SIGQ | REG | signal_quality:1d9d637a3a48 | regime:e18edff4f8d3 | +28.1 | +31.9 | +50.1 | -9.9 | FLAG |
| SIGQ | ZONE | signal_quality:1d9d637a3a48 | zone:e2b9736063c7 | +28.1 | +57.0 | +77.2 | -7.9 | FLAG |
| REG | COOL | regime:e18edff4f8d3 | cooldown:fbe1c726c9b2 | +31.9 | +29.7 | +56.3 | -5.3 | FLAG |
| SIGQ | COOL | signal_quality:1d9d637a3a48 | cooldown:fbe1c726c9b2 | +28.1 | +29.7 | +61.3 | +3.4 | FLAG |

## Validation of the joint pick (first-order)

- Placebo / family null over the joint space: 5000 random stacks over the full grids give key quantiles median 52.1, 90% 67.5, 99% 75.6, max 84.6. The best factorial stack key is 80.8: it is below the best random stack, i.e. the full-grid random search finds stacks as good as the top-K factorial (no evidence that top-K selection matters; family p for the best stack over this joint space is about 1 (it is the maximum of a searched set)).
- Joint walk-forward (monthly, purged 7 d, trailing 26 weeks, candidate pool = live + 1500 random stacks NOT selected on full-sample data, pick by equal-mean train maxDD): OOS maxDD cut +59.9% vs live, d mean -10966 $/wk, live kept in 0 of 34 months. The pick procedure does cut OOS maxDD but gives up mean (it is mostly an exposure reduction).
- Held-out live week: n/a for stacks (the owners' M arrays cover the 21,135 base rows only).

## Exact engine results for joint stacks (table mode: the stack multiplier applied after the Q1-A ladder, before zone HALF)

| stack | window | cut | eq-mean cut | d mean | worst-20 |
|---|---|---|---|---|---|

## Plain sentence

The best first-order joint stack lowers L6M maxDD +89.9% at equal mean (PRE +80.8%, X' +82.5%) and differs from live in these layers: SIZER=sizer_vt:cab7b88a3ae5, LOT=p7_other:b8c7a11b7c62, REG=regime:e18edff4f8d3, STACK=equal_risk:C|riskcap_per_trade|R$3600|P7, COOL=cooldown:6e18cc85a3d6. This is a screen: lot-level layers only, in-sample, and first-order overstates (exact J-pair runs gave about half). The verdict comes from the exact runs and the joint walk-forward once the owners' top-K files and the cut / profit / lock layers are in.
