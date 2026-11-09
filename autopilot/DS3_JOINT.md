# DS3_JOINT - everything with everything (T-JOINT), version 1 (2026-11-09 17:21Z)

**FIRST-ORDER SCREEN ONLY. PRE-PROOF, post-hoc, shadow only, no PASS claims. Every layer stays ON in every stack: option 0 of each layer is the live setting (multiplier 1).** The layer pools are stand-ins built by SZ-IJK from the owners' multiplier files (M_*.npz, the lot-level layers only) until the owners write /mnt/l2/l2vast/_th_joint/layers/<layer>/topK.json. Cut / profit-rule / lock / entry layers are NOT multiplier-composable and are not in this version.

## Capacity budget (measured)

Exact engine throughput about 24 cell-months/hour/worker with month batching, 6 workers shared box-wide. One stack on L6M+PRE+X' = 33 months = 1.4 worker-hours; HOLD adds 6 months. A 243-stack factorial = 8,000 cell-months = 55 hours of ALL six workers; 3,125 stacks = about 3 weeks. NOT tractable exactly. Used instead: (1) first-order composable screen over every composable stack: full factorial of the top-5 per layer (46656 stacks) plus 5000 random stacks over the 60-cell grids and coordinate descent from live + 10 random starts (about 1 minute of one core); (2) exact runs on L6M+PRE+X' only for the top stacks and every coordinate-descent local optimum (batch mode, about 1.5 stacks/hour at 2 workers); (3) first-order overstates: for the J pairs the exact L6M equal-mean cut was about half the first-order value.

## Layers and pools (lot-level layers, first-order composable)

| layer | options (live + top by DD-first key, grid 60) | pool source |
|---|---|---|
| SIZER | 61 | sizer_vol, sizer_vt |
| LOT | 61 | p7_other |
| SIGQ | 61 | signal_quality |
| REG | 61 | regime |
| STACK | 61 | equal_risk, equity_state, exposure_stack |
| COOL | 61 | cooldown |

## Top-10 joint stacks, first-order screen (full factorial of the top-5 per layer, distinct lot arrays)

Key = min over L6M / PRE / X' of the maxDD cut at EQUAL MEAN to the live stack (global lot scale), then HOLD, worst-20; d mean at equal lots shown. Window cuts below are at equal mean.

| # | SIZER | LOT | SIGQ | REG | STACK | COOL | key | eq cut L6M / HOLD / PRE / X' | cut at equal lots L6M | d mean L6M | worst-20 L6M cell / live | stage |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | sizer_vt:cab7b88a3ae5 | p7_other:b8c7a11b7c62 | live | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | 80.6 | +89.9 / +24.9 / +80.9 / +80.6 | +91.3 | -2993 | 250k / 165k | FIRST-ORDER SCREEN ONLY |
| 2 | sizer_vt:cab7b88a3ae5 | p7_other:ac4e6310f17b | live | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | 79.8 | +89.3 / +30.3 / +79.8 / +81.0 | +90.9 | -3383 | 245k / 165k | FIRST-ORDER SCREEN ONLY |
| 3 | sizer_vt:cab7b88a3ae5 | p7_other:b8c7a11b7c62 | signal_quality:73c32e59f366 | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$2400|P7 | cooldown:6e18cc85a3d6 | 79.7 | +88.3 / +41.1 / +79.7 / +80.0 | +91.8 | -6669 | 189k / 165k | FIRST-ORDER SCREEN ONLY |
| 4 | sizer_vt:cab7b88a3ae5 | p7_other:7779bf143e94 | live | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | 79.7 | +89.3 / +30.0 / +79.7 / +80.9 | +90.9 | -3462 | 244k / 165k | FIRST-ORDER SCREEN ONLY |
| 5 | sizer_vt:cab7b88a3ae5 | p7_other:b8c7a11b7c62 | signal_quality:73c32e59f366 | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | 79.7 | +93.0 / +34.5 / +79.9 / +79.7 | +94.3 | -3927 | 232k / 165k | FIRST-ORDER SCREEN ONLY |
| 6 | sizer_vt:cab7b88a3ae5 | live | signal_quality:73c32e59f366 | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$2400|P7 | cooldown:6e18cc85a3d6 | 79.6 | +87.7 / +42.1 / +79.6 / +80.5 | +91.2 | -6431 | 189k / 165k | FIRST-ORDER SCREEN ONLY |
| 7 | sizer_vt:cab7b88a3ae5 | p7_other:7779bf143e94 | signal_quality:3fa50f26f751 | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | 79.5 | +91.5 / +31.8 / +80.2 / +79.5 | +93.3 | -4807 | 221k / 165k | FIRST-ORDER SCREEN ONLY |
| 8 | sizer_vt:cab7b88a3ae5 | p7_other:ac4e6310f17b | signal_quality:3fa50f26f751 | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | 79.5 | +91.5 / +31.8 / +80.2 / +79.5 | +93.3 | -4807 | 221k / 165k | FIRST-ORDER SCREEN ONLY |
| 9 | sizer_vt:cab7b88a3ae5 | live | signal_quality:3fa50f26f751 | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | 79.5 | +90.6 / +36.5 / +79.6 / +79.5 | +92.1 | -3546 | 223k / 165k | FIRST-ORDER SCREEN ONLY |
| 10 | sizer_vt:cab7b88a3ae5 | p7_other:2bed08857dfd | live | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:6e18cc85a3d6 | 79.4 | +89.1 / +28.9 / +79.4 / +80.6 | +90.9 | -3767 | 240k / 165k | FIRST-ORDER SCREEN ONLY |

## Coordinate descent (live + 10 random starts, one layer at a time against the key)

| start | local optimum | key |
|---|---|---|
| live | SIZER=sizer_vt:cab7b88a3ae5 / LOT=p7_other:baa6bbb5523c / SIGQ=signal_quality:6b7b2de4509f / REG=regime:72ffa1d9c2fa / STACK=equity_state:D|eqdd_book_20d_R / COOL=cooldown:fbe1c726c9b2 | 87.2 |
| random | SIZER=sizer_vt:e3f124a36d05 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:e37f04b47dd5 / REG=regime:c9675215fcf1 / STACK=equity_state:D|eqdd_book_20d_R / COOL=cooldown:f511b70e6d8d | 83.5 |
| random | SIZER=sizer_vt:7d550db94174 / LOT=p7_other:3f44a5a78d9d / SIGQ=signal_quality:a08183547df2 / REG=regime:8715ffc91335 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:1070903d9014 | 85.2 |
| random | SIZER=sizer_vol:0b2fdaaa8776 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:2aeb93aa1b83 / REG=regime:66c60fa89c89 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:1267b1ca674e | 83.8 |
| random | SIZER=sizer_vt:cab7b88a3ae5 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:f5e0f94f4e48 / REG=regime:72ffa1d9c2fa / STACK=equity_state:D|eqdd_book_20d_R / COOL=cooldown:50db603d2c5a | 88.2 |
| random | SIZER=sizer_vt:e8970df0a998 / LOT=p7_other:6fa18a1ca7ac / SIGQ=signal_quality:8db33322f63d / REG=regime:34e6b81002b1 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:f511b70e6d8d | 81.3 |
| random | SIZER=sizer_vt:1e464d797671 / LOT=p7_other:baa6bbb5523c / SIGQ=signal_quality:b9a6edabcd7b / REG=regime:8715ffc91335 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:1070903d9014 | 86.2 |
| random | SIZER=sizer_vt:b914834619ab / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:b9a6edabcd7b / REG=regime:f1f4301eae70 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:52f0e4f39d4c | 87.1 |
| random | SIZER=sizer_vt:7d550db94174 / LOT=p7_other:baa6bbb5523c / SIGQ=signal_quality:67c701bb2705 / REG=regime:c9675215fcf1 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:83fb4c1afb5d | 85.1 |
| random | SIZER=sizer_vt:b914834619ab / LOT=p7_other:3f44a5a78d9d / SIGQ=signal_quality:b765dec1cee2 / REG=regime:c9675215fcf1 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:ffbb77fe65de | 85.5 |
| random | SIZER=sizer_vt:ed624ef2d5e6 / LOT=p7_other:f4181da4c118 / SIGQ=signal_quality:6b7b2de4509f / REG=regime:72ffa1d9c2fa / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:5adf9b2c9b46 | 87.0 |

## Interaction table (best single cell per layer by key; pair gain minus the sum of single gains, equal-mean L6M cut points; FLAG = |interaction| > 10% of either single gain)

| layer a | layer b | cell a | cell b | gain a | gain b | pair | interaction | flag |
|---|---|---|---|---|---|---|---|---|
| REG | STACK | regime:61f3cbb073a5 | equal_risk:C|riskcap_per_trade|R$3 | +33.2 | +35.6 | +34.6 | -34.2 | FLAG |
| SIZER | LOT | sizer_vt:cab7b88a3ae5 | p7_other:b8c7a11b7c62 | +78.9 | +36.4 | +84.2 | -31.2 | FLAG |
| LOT | REG | p7_other:b8c7a11b7c62 | regime:61f3cbb073a5 | +36.4 | +33.2 | +39.0 | -30.6 | FLAG |
| SIZER | STACK | sizer_vt:cab7b88a3ae5 | equal_risk:C|riskcap_per_trade|R$3 | +78.9 | +35.6 | +86.3 | -28.2 | FLAG |
| LOT | STACK | p7_other:b8c7a11b7c62 | equal_risk:C|riskcap_per_trade|R$3 | +36.4 | +35.6 | +46.0 | -26.0 | FLAG |
| SIZER | COOL | sizer_vt:cab7b88a3ae5 | cooldown:fbe1c726c9b2 | +78.9 | +29.7 | +83.3 | -25.3 | FLAG |
| SIZER | REG | sizer_vt:cab7b88a3ae5 | regime:61f3cbb073a5 | +78.9 | +33.2 | +90.9 | -21.3 | FLAG |
| LOT | SIGQ | p7_other:b8c7a11b7c62 | signal_quality:1d9d637a3a48 | +36.4 | +28.1 | +47.5 | -17.0 | FLAG |
| SIZER | SIGQ | sizer_vt:cab7b88a3ae5 | signal_quality:1d9d637a3a48 | +78.9 | +28.1 | +91.0 | -16.1 | FLAG |
| STACK | COOL | equal_risk:C|riskcap_per_trade|R$3 | cooldown:fbe1c726c9b2 | +35.6 | +29.7 | +50.8 | -14.5 | FLAG |
| LOT | COOL | p7_other:b8c7a11b7c62 | cooldown:fbe1c726c9b2 | +36.4 | +29.7 | +53.6 | -12.6 | FLAG |
| SIGQ | STACK | signal_quality:1d9d637a3a48 | equal_risk:C|riskcap_per_trade|R$3 | +28.1 | +35.6 | +51.7 | -11.9 | FLAG |
| SIGQ | REG | signal_quality:1d9d637a3a48 | regime:61f3cbb073a5 | +28.1 | +33.2 | +53.2 | -8.2 | FLAG |
| REG | COOL | regime:61f3cbb073a5 | cooldown:fbe1c726c9b2 | +33.2 | +29.7 | +58.7 | -4.2 | FLAG |
| SIGQ | COOL | signal_quality:1d9d637a3a48 | cooldown:fbe1c726c9b2 | +28.1 | +29.7 | +61.2 | +3.4 | FLAG |

## Validation of the joint pick (first-order)

- Placebo / family null over the joint space: 5000 random stacks over the full grids give key quantiles median 57.6, 90% 70.1, 99% 77.0, max 81.0. The best factorial stack key is 80.6: it is below the best random stack, i.e. the full-grid random search finds stacks as good as the top-K factorial (no evidence that top-K selection matters; family p for the best stack over this joint space is about 1 (it is the maximum of a searched set)).
- Joint walk-forward (monthly, purged 7 d, trailing 26 weeks, candidate pool = live + 1500 random stacks NOT selected on full-sample data, pick by equal-mean train maxDD): OOS maxDD cut +19.2% vs live, d mean -10104 $/wk, live kept in 0 of 34 months. The pick procedure does cut OOS maxDD but gives up mean (it is mostly an exposure reduction).
- Held-out live week: n/a for stacks (the owners' M arrays cover the 21,135 base rows only).

## Plain sentence

The best first-order joint stack lowers L6M maxDD +89.9% at equal mean (PRE +80.9%, X' +80.6%) and differs from live in these layers: SIZER=sizer_vt:cab7b88a3ae5, LOT=p7_other:b8c7a11b7c62, REG=regime:e18edff4f8d3, STACK=equal_risk:C|riskcap_per_trade|R$3600|P7, COOL=cooldown:6e18cc85a3d6. This is a screen: lot-level layers only, in-sample, and first-order overstates (exact J-pair runs gave about half). The verdict comes from the exact runs and the joint walk-forward once the owners' top-K files and the cut / profit / lock layers are in.
