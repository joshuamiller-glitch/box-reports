# DS3_JOINT - everything with everything (T-JOINT), version 1 (2026-11-10 09:51Z)

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
| B02 | 4 | reg |

## Registered layers (/mnt/l2/l2vast/_th_joint/layers/*/topK.json)

Static-M layers (multiplier arrays, composable first-order by product): a06_slots: 2 cells incl. live; b02: 4 cells incl. live; brackets: 1 cells incl. live; cooldown_r5: 1 cells incl. live; cooldowns: 1 cells incl. live; entry: 1 cells incl. live; hm5: 1 cells incl. live; locks: 1 cells incl. live; lot_tables: 4 cells incl. live; netting: 1 cells incl. live; ntz: 1 cells incl. live; o7: 1 cells incl. live; ote: 1 cells incl. live; reentry: 1 cells incl. live; session_blocks: 1 cells incl. live; shadow: 2 cells incl. live; signals: 7 cells incl. live; sizer: 5 cells incl. live; sizer_state: 1 cells incl. live; stack_cut: 1 cells incl. live; stack_exposure: 1 cells incl. live; stopexit: 4 cells incl. live; zone: 5 cells incl. live. In the screen: SIZER, LOT, ZONE, A06, B02 take the registered cells first (then the stand-in grids); hm5 and stack_cut registered only the live setting.

Trade-list / hook layers (NOT multiplier-composable: they change exits, re-entries, locks, entries; verdicts only from joint exact runs through their hooks): a06_slots: 1 cells; brackets: 4 cells; cooldown_r5: 5 cells; cooldowns: 5 cells; cut: 5 cells; entry: 4 cells; locks: 5 cells; lot_tables: 1 cells; netting: 4 cells; ntz: 5 cells; o7: 4 cells; ote: 4 cells; profit: 64 cells; reentry: 5 cells; session_blocks: 4 cells; shadow: 8 cells; signals: 28 cells; sizer_state: 1 cells; stack_cut: 4 cells; stack_exposure: 1 cells; stopexit: 4 cells.


## Top-10 joint stacks, first-order screen (full factorial of the top-5 per layer, distinct lot arrays)

Key (standing rule 2, recents first) = min over L6M / L3M of the maxDD cut at EQUAL MEAN to the live stack (global lot scale), then HOLD, worst-20; d mean at equal lots shown. Window cuts below are at equal mean.

| # | SIZER | LOT | SIGQ | REG | STACK | COOL | ZONE | A06 | B02 | key | eq cut L6M / HOLD / PRE / X' | cut at equal lots L6M | d mean L6M | worst-20 L6M cell / live | PRE tolerance | stage |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | reg:sizer:AB_73ca99b0ec2d | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +87.9 / +84.8 / +84.9 | +100.0 | -4921 | 221k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 2 | live | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:6e18cc85a3d6 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +89.2 / +85.0 / +82.9 | +100.0 | -3463 | 246k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 3 | reg:sizer:AB_73ca99b0ec2d | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:6e18cc85a3d6 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +90.9 / +82.5 / +83.7 | +100.0 | -4959 | 227k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 4 | live | reg:lot_tables:lot_greedy_down | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +86.6 / +85.3 / +85.1 | +100.0 | -3426 | 241k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 5 | live | reg:lot_tables:lot_P7_744 | live | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZS_C0_6e93e2da912d | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +86.9 / +84.7 / +81.8 | +100.0 | -1430 | 265k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 6 | reg:sizer:AB_73ca99b0ec2d | live | live | regime:e18edff4f8d3 | equal_risk:C|riskcap_per_trade|R$3600|P7 | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +81.5 / +84.5 / +86.8 | +100.0 | -5072 | 240k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 7 | live | live | live | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZS_C0_6e93e2da912d | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +86.3 / +84.1 / +81.4 | +100.0 | -1126 | 274k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 8 | live | reg:lot_tables:lot_P7_644 | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +83.4 / +84.4 / +83.9 | +100.0 | -7106 | 272k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 9 | reg:sizer:VT_S2 | live | live | regime:e18edff4f8d3 | live | cooldown:fbe1c726c9b2 | live | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.4 | +100.0 / +78.0 / +85.9 / +87.4 | +100.0 | -639 | 275k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |
| 10 | live | live | signal_quality:73c32e59f366 | regime:e18edff4f8d3 | live | cooldown:5adf9b2c9b46 | reg:zone:ZS_C0_6e93e2da912d | reg:a06_slots:a06_greedy_down | reg:b02:B02_K7P7H7_20_1.00_alld_0.0 | 100.3 | +100.0 / +79.9 / +82.5 / +81.7 | +100.0 | -2963 | 241k / 165k | RECENT-ONLY-UNKNOWN-WF | FIRST-ORDER SCREEN ONLY |

## Coordinate descent (live + 10 random starts, one layer at a time against the key)

| start | local optimum | key |
|---|---|---|
| live | SIZER=sizer_vt:e3f124a36d05 / LOT=reg:lot_tables:lot_P7_744 / SIGQ=signal_quality:7f7622673f09 / REG=regime:3cf7b58e25a6 / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:f511b70e6d8d / ZONE=live / A06=live / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.3 |
| random | SIZER=sizer_vt:d65ad35f7583 / LOT=p7_other:17dc82660d90 / SIGQ=signal_quality:894921a2d1c4 / REG=regime:72ffa1d9c2fa / STACK=equity_state:D|eqdd_stack_20d| / COOL=cooldown:fbe1c726c9b2 / ZONE=zone:7570c5ff7f2d / A06=live / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.4 |
| random | SIZER=sizer_vol:1b5942ac8cd6 / LOT=p7_other:5cc859f6b289 / SIGQ=signal_quality:2b44cb2c7a67 / REG=regime:8715ffc91335 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:9f55d2c16275 / ZONE=zone:465821f8c60d / A06=live / B02=live | 100.3 |
| random | SIZER=reg:sizer:AB_e2058312a643 / LOT=p7_other:9ce43e948920 / SIGQ=signal_quality:da5d92c18f1f / REG=regime:ffe1dffa4c6a / STACK=equity_state:D|consec_loss|boo / COOL=cooldown:f4edae75e179 / ZONE=zone:0a3bc6037631 / A06=live / B02=reg:b02:B02_allbooks_20_1.00_a | 94.4 |
| random | SIZER=sizer_vt:7b692e38e6f1 / LOT=p7_other:3720d0d6b4b1 / SIGQ=signal_quality:6b7b2de4509f / REG=regime:d11857aae126 / STACK=equity_state:D|eqdd_book_20d_R / COOL=cooldown:21142bd69657 / ZONE=zone:8031aee5ac1d / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.20_all | 100.3 |
| random | SIZER=reg:sizer:AB_e2058312a643 / LOT=p7_other:3e206f50c848 / SIGQ=signal_quality:98d80d0f642a / REG=regime:d11857aae126 / STACK=equity_state:D|dayloss_stack$| / COOL=cooldown:f511b70e6d8d / ZONE=zone:f8fbee4f18de / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_allbooks_20_1.00_a | 100.4 |
| random | SIZER=sizer_vt:e7400edefb68 / LOT=live / SIGQ=signal_quality:894921a2d1c4 / REG=regime:910b86c59480 / STACK=exposure_stack:E|total_lots_ca / COOL=cooldown:0ca796d7b606 / ZONE=zone:e34226b932fa / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.4 |
| random | SIZER=sizer_vol:faebfc320da8 / LOT=p7_other:17dc82660d90 / SIGQ=signal_quality:98d80d0f642a / REG=regime:9a89fe48f047 / STACK=exposure_stack:E|corr_same_sid / COOL=live / ZONE=zone:7570c5ff7f2d / A06=reg:a06_slots:a06_greedy_down / B02=reg:b02:B02_K7P7H7_20_1.00_all | 100.4 |
| random | SIZER=sizer_vt:f7d0f18fbc1b / LOT=p7_other:b1c8bbda384d / SIGQ=signal_quality:a08183547df2 / REG=regime:47eaf3230c33 / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:38737e4187ce / ZONE=zone:0c17aec1653b / A06=reg:a06_slots:a06_greedy_down / B02=live | 100.3 |
| random | SIZER=sizer_vt:c5f9e199982a / LOT=p7_other:2e1688481e8c / SIGQ=signal_quality:2b44cb2c7a67 / REG=regime:0c9d251dc8cd / STACK=exposure_stack:E|same_side_lot / COOL=cooldown:1b987436da19 / ZONE=zone:f8fbee4f18de / A06=live / B02=live | 100.3 |
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

- Placebo / family null over the joint space: 5000 random stacks over the full grids give key quantiles median 67.5, 90% 85.0, 99% 94.4, max 100.3. The best factorial stack key is 100.4: it is above the best random stack, i.e. the full-grid random search finds stacks as good as the top-K factorial (no evidence that top-K selection matters; family p for the best stack over this joint space is about 1 (it is the maximum of a searched set)).
- Joint walk-forward (monthly, purged 7 d, trailing 26 weeks, candidate pool = live + 1500 random stacks NOT selected on full-sample data, pick by equal-mean train maxDD): OOS maxDD cut +76.9% vs live, d mean -9529 $/wk, live kept in 0 of 34 months. The pick procedure does cut OOS maxDD but gives up mean (it is mostly an exposure reduction).
- STANDING RULE 2 primary OOS test, bi-weekly re-pick WF (trailing 26 weeks -> next 2 weeks, purged 7 d) of the whole joint procedure: 75 refit periods since 2024-01, OOS maxDD cut +76.5% with d mean -9669 $/wk; the pick beat live (period P&L >= live and in-period drawdown <= live) in 36% of periods (P&L alone 36%); since 2026-05-12 (13 periods): 46% beat, 46% P&L-ge.
- Held-out live week: n/a for stacks (the owners' M arrays cover the 21,135 base rows only).

## Exact engine results for joint stacks (table mode: the stack multiplier applied after the Q1-A ladder, before zone HALF)

| stack | window | cut | eq-mean cut | d mean | worst-20 | standing rule 2a label (PRE row) |
|---|---|---|---|---|---|---|
| J01 | L1M | +57.8 | +54.0 | +18143 | -26k / -3k |  |
| J01 | L3M | +57.8 | +54.1 | -450 | 133k / 216k |  |
| J01 | L6M | +11.9 | +4.2 | -1809 | 114k / 165k |  |
| J01 | PRE | +31.6 | +25.5 | -4092 | -493k / -717k | RECENT-ONLY (allow 21.935724552964608%, WF 61%) |
| J01 | X' | +65.5 | +62.4 | +915 | -211k / -348k |  |
| J02 | L1M | +44.2 | +34.0 | +15441 | -45k / -3k |  |
| J02 | L3M | +13.9 | -1.7 | -5353 | 64k / 216k |  |
| J02 | L6M | +13.9 | -1.7 | -3422 | 45k / 165k |  |
| J02 | PRE | +40.2 | +29.4 | -4187 | -471k / -717k | RECENT-ONLY (allow 15.0%, WF 59%) |
| J02 | X' | +74.2 | +69.5 | +4485 | -213k / -348k |  |
| J03 | L1M | +56.4 | +57.9 | +19492 | -35k / -3k |  |
| J03 | L3M | +52.0 | +53.6 | +513 | 132k / 216k |  |
| J03 | L6M | +18.9 | +21.6 | +769 | 140k / 165k |  |
| J03 | HOLD | +29.2 | +31.6 | -1809 | -388k / -551k |  |
| J03 | PRE | +33.0 | +35.2 | -6170 | -454k / -717k | RECENT-ONLY (allow 25.0%, WF 65%) |
| J03 | X' | +72.6 | +73.5 | +3623 | -175k / -348k |  |
| J04 | L1M | +65.5 | +58.5 | +17668 | -28k / -3k |  |
| J04 | L3M | +59.8 | +51.7 | -2675 | 106k / 216k |  |
| J04 | L6M | +13.8 | -3.7 | -3767 | 104k / 165k |  |
| J04 | PRE | +43.4 | +31.9 | -4383 | -428k / -717k | RECENT-ONLY (allow 23.7830892631387%, WF 64%) |
| J04 | X' | +70.1 | +64.0 | +2093 | -170k / -348k |  |
| JL01 | L1M | +71.4 | +74.4 | +18989 | 12k / -3k |  |
| JL01 | L3M | +29.0 | +36.5 | +3211 | 213k / 216k |  |
| JL01 | L6M | +29.0 | +36.5 | +2625 | 245k / 165k |  |
| JL01 | HOLD | +29.3 | +36.7 | -3207 | -342k / -551k |  |
| JL01 | PRE | +37.9 | +44.5 | -4452 | -469k / -717k | RECENT-ONLY (allow 25.0%, WF 85%) |
| JL01 | X' | +71.3 | +74.3 | +2509 | -123k / -348k |  |
| JL02 | L1M | +51.8 | +53.3 | +18279 | -38k / -3k |  |
| JL02 | L3M | +45.0 | +46.6 | -751 | 117k / 216k |  |
| JL02 | L6M | +18.9 | +21.3 | +699 | 151k / 165k |  |
| JL02 | PRE | +7.1 | +10.0 | -3773 | -474k / -717k | RECENT-ONLY (allow 25.0%, WF 64%) |
| JL03 | L1M | +59.7 | +62.7 | +20985 | -32k / -3k |  |
| JL03 | L3M | +59.8 | +62.7 | +2979 | 160k / 216k |  |
| JL03 | L6M | +14.9 | +21.1 | +1750 | 159k / 165k |  |
| JL03 | PRE | +28.0 | +33.2 | -5161 | -454k / -717k | RECENT-ONLY (allow 24.915826255760347%, WF 64%) |
| JL04 | L1M | +54.9 | +56.6 | +19102 | -36k / -3k |  |
| JL04 | L3M | +52.0 | +53.8 | +82 | 127k / 216k |  |
| JL04 | L6M | +20.9 | +23.8 | +876 | 146k / 165k |  |
| JL04 | PRE | +21.7 | +24.7 | -5740 | -467k / -717k | RECENT-ONLY (allow 15.0%, WF 59%) |
| JL05 | L1M | +60.4 | +60.2 | +18800 | -32k / -3k |  |
| JL05 | L3M | +47.5 | +47.3 | -986 | 119k / 216k |  |
| JL05 | L6M | +10.1 | +9.8 | -94 | 132k / 165k |  |
| JL05 | PRE | +27.2 | +26.9 | -6661 | -456k / -717k | RECENT-ONLY (allow 20.14357379434636%, WF 64%) |
| JL06 | L1M | +54.9 | +56.6 | +19778 | -36k / -3k |  |
| JL06 | L3M | +43.6 | +45.7 | +138 | 125k / 216k |  |
| JL06 | L6M | +22.6 | +25.6 | +882 | 137k / 165k |  |
| JL06 | PRE | +23.2 | +26.1 | -4592 | -455k / -717k | RECENT-ONLY (allow 15.0%, WF 59%) |
| JN02 | L1M | +78.4 | +81.2 | +21324 | 21k / -3k |  |
| JN02 | L3M | +28.8 | +37.9 | +3649 | 220k / 216k |  |
| JN02 | L6M | +28.8 | +37.9 | +3297 | 247k / 165k |  |
| JN02 | PRE | +36.9 | +45.0 | -3265 | -479k / -717k | RECENT-ONLY (allow 25.0%, WF 86%) |
| JN03 | L1M | +40.2 | +43.3 | +12466 | -8k / -3k |  |
| JN03 | L3M | +39.0 | +42.2 | +1102 | 187k / 216k |  |
| JN03 | L6M | +39.0 | +42.2 | +1251 | 218k / 165k |  |
| JN03 | HOLD | +24.8 | +28.7 | -2593 | -350k / -551k |  |
| JN03 | PRE | +37.6 | +40.9 | -3107 | -458k / -717k | RECENT-ONLY (allow 25.0%, WF 82%) |
| JN03 | X' | +68.8 | +70.4 | +2543 | -155k / -348k |  |
| JN04 | L1M | +67.9 | +73.7 | +18072 | 13k / -3k |  |
| JN04 | L3M | +43.4 | +53.5 | +5959 | 249k / 216k |  |
| JN04 | L6M | +43.4 | +53.5 | +4860 | 284k / 165k |  |
| JN04 | HOLD | +45.6 | +55.3 | -1456 | -329k / -551k |  |
| JN04 | PRE | +31.4 | +43.7 | -3620 | -462k / -717k | RECENT-ONLY (allow 25.0%, WF 85%) |
| JN04 | X' | +68.6 | +74.2 | +2252 | -156k / -348k |  |
| JN05 | L1M | +56.2 | +59.1 | +14954 | 5k / -3k |  |
| JN05 | L3M | +35.2 | +39.5 | +3448 | 221k / 216k |  |
| JN05 | L6M | +35.2 | +39.5 | +1610 | 215k / 165k |  |
| JN05 | PRE | +18.4 | +23.9 | -4001 | -503k / -717k | RECENT-ONLY (allow 25.0%, WF 73%) |
| JN06 | L1M | +54.5 | +59.4 | -6311 | 12k / -3k |  |
| JN06 | L3M | +27.0 | +34.7 | +3981 | 229k / 216k |  |
| JN06 | L6M | +27.0 | +34.7 | +2896 | 246k / 165k |  |
| JN06 | PRE | +29.4 | +36.8 | -3311 | -487k / -717k | RECENT-ONLY (allow 25.0%, WF 77%) |
| JP01 | L1M | +50.8 | +56.8 | +13523 | -4k / -3k |  |
| JP01 | L3M | +42.6 | +49.6 | +3822 | 220k / 216k |  |
| JP01 | L6M | +42.6 | +49.6 | +3109 | 275k / 165k |  |
| JP01 | HOLD | +49.6 | +55.8 | -2559 | -318k / -551k |  |
| JP01 | PRE | +41.7 | +48.8 | -3218 | -430k / -717k | RECENT-ONLY (allow 25.0%, WF 85%) |
| JP01 | X' | +66.2 | +70.3 | +1165 | -169k / -348k |  |
| JP02 | L1M | +65.6 | +66.3 | +17454 | 13k / -3k |  |
| JP02 | L3M | +56.6 | +57.5 | -938 | 245k / 216k |  |
| JP02 | L6M | +40.4 | +41.6 | +550 | 273k / 165k |  |
| JP02 | HOLD | +29.9 | +31.3 | -3148 | -358k / -551k |  |
| JP02 | PRE | +54.2 | +55.1 | -3622 | -424k / -717k | RECENT-ONLY (allow 25.0%, WF 84%) |
| JP02 | X' | +67.8 | +68.4 | +1147 | -169k / -348k |  |
| JP03 | L1M | +76.0 | +76.0 | -635 | 31k / -3k |  |
| JP03 | L3M | +46.5 | +46.6 | -1456 | 234k / 216k |  |
| JP03 | L6M | +42.2 | +42.4 | +73 | 243k / 165k |  |
| JP03 | HOLD | +21.9 | +22.1 | -3947 | -374k / -551k |  |
| JP03 | PRE | +47.0 | +47.2 | -3713 | -406k / -717k | RECENT-ONLY (allow 25.0%, WF 80%) |
| JP03 | X' | +69.7 | +69.8 | +419 | -188k / -348k |  |
| JP04 | L1M | +84.6 | +85.8 | +23904 | 20k / -3k |  |
| JP04 | L3M | +48.1 | +51.8 | +4347 | 220k / 216k |  |
| JP04 | L6M | +48.1 | +51.8 | +1729 | 217k / 165k |  |
| JP04 | HOLD | +37.6 | +42.1 | -3198 | -322k / -551k |  |
| JP04 | PRE | +41.7 | +45.9 | -3207 | -434k / -717k | RECENT-ONLY (allow 25.0%, WF 85%) |
| JP04 | X' | +72.5 | +74.5 | +2451 | -136k / -348k |  |
| JP05 | L1M | +32.1 | +36.3 | +11756 | -2k / -3k |  |
| JP05 | L3M | +32.2 | +36.4 | +2176 | 208k / 216k |  |
| JP05 | L6M | +32.2 | +36.4 | +1472 | 251k / 165k |  |
| JP05 | HOLD | +27.5 | +32.0 | -1516 | -330k / -551k |  |
| JP05 | PRE | +31.9 | +36.1 | -2290 | -473k / -717k | RECENT-ONLY (allow 25.0%, WF 84%) |
| JP05 | X' | +63.0 | +65.3 | +2090 | -186k / -348k |  |
| JP06 | L1M | +78.0 | +76.5 | +22248 | 13k / -3k |  |
| JP06 | L3M | +38.7 | +34.6 | +998 | 177k / 216k |  |
| JP06 | L6M | +34.6 | +30.2 | -1426 | 185k / 165k |  |
| JP06 | PRE | +48.6 | +45.1 | -3607 | -423k / -717k | RECENT-ONLY (allow 25.0%, WF 82%) |
| JY01 | L1M | +87.0 | +65.4 | +27878 | -7k / -3k |  |
| JY02 | L1M | +86.6 | +61.8 | +27547 | -7k / -3k |  |
| JY03 | L1M | +87.3 | +58.4 | +27376 | -4k / -3k |  |
| JY04 | L1M | +73.3 | +14.7 | +24601 | -21k / -3k |  |
| JY05 | L1M | +55.6 | -1892.7 | +17885 | -30k / -3k |  |
| JY06 | L1M | +77.3 | +9.1 | +23883 | -18k / -3k |  |
| JZ01 | L1M | +40.0 | +19.0 | +16121 | -48k / -3k |  |
| JZ01 | L3M | +28.9 | +4.0 | -7928 | 28k / 216k |  |
| JZ01 | L6M | +26.3 | +0.5 | -5790 | 30k / 165k |  |
| JZ01 | PRE | +55.5 | +39.8 | -4554 | -446k / -717k | RECENT-ONLY (allow 25.0%, WF 68%) |
| JZ02 | L1M | +88.5 | +86.3 | +27160 | -2k / -3k |  |
| JZ02 | L3M | +32.0 | +19.0 | -6782 | 54k / 216k |  |
| JZ02 | L6M | +12.2 | -4.6 | -3587 | 98k / 165k |  |
| JZ02 | PRE | +47.9 | +37.9 | -5056 | -409k / -717k | RECENT-ONLY (allow 22.19294748141969%, WF 73%) |
| JZ03 | L1M | +51.1 | +40.6 | +17356 | -35k / -3k |  |
| JZ03 | L3M | +10.4 | -8.8 | -6056 | 59k / 216k |  |
| JZ03 | L6M | -14.4 | -39.0 | -3944 | 39k / 165k |  |
| JZ03 | PRE | +47.3 | +35.9 | -3919 | -532k / -717k | RECENT-ONLY (allow 15.0%, WF 59%) |
| JZ04 | L1M | +32.1 | +11.5 | +12160 | -54k / -3k |  |
| JZ04 | L3M | +1.2 | -28.8 | -4148 | 79k / 216k |  |
| JZ04 | L6M | +1.2 | -28.8 | -5200 | 48k / 165k |  |
| JZ04 | PRE | +39.1 | +20.7 | -4926 | -498k / -717k | RECENT-ONLY (allow 15.0%, WF 64%) |

## Exact vs first-order (so far)

First-order keys of these stacks were 86-88% (equal-mean cut). Exact engine: J01: L6M eq-mean cut +4.2 / d mean -1809, PRE eq-mean cut +25.5 / d mean -4092, X' eq-mean cut +62.4 / d mean +915; J02: L6M eq-mean cut -1.7 / d mean -3422, PRE eq-mean cut +29.4 / d mean -4187, X' eq-mean cut +69.5 / d mean +4485; J03: L6M eq-mean cut +21.6 / d mean +769, PRE eq-mean cut +35.2 / d mean -6170, X' eq-mean cut +73.5 / d mean +3623, HOLD eq-mean cut +31.6 / d mean -1809; J04: L6M eq-mean cut -3.7 / d mean -3767, PRE eq-mean cut +31.9 / d mean -4383, X' eq-mean cut +64.0 / d mean +2093; JL01: L6M eq-mean cut +36.5 / d mean +2625, PRE eq-mean cut +44.5 / d mean -4452, X' eq-mean cut +74.3 / d mean +2509, HOLD eq-mean cut +36.7 / d mean -3207; JL02: L6M eq-mean cut +21.3 / d mean +699, PRE eq-mean cut +10.0 / d mean -3773; JL03: L6M eq-mean cut +21.1 / d mean +1750, PRE eq-mean cut +33.2 / d mean -5161; JL04: L6M eq-mean cut +23.8 / d mean +876, PRE eq-mean cut +24.7 / d mean -5740; JL05: L6M eq-mean cut +9.8 / d mean -94, PRE eq-mean cut +26.9 / d mean -6661; JL06: L6M eq-mean cut +25.6 / d mean +882, PRE eq-mean cut +26.1 / d mean -4592; JN02: L6M eq-mean cut +37.9 / d mean +3297, PRE eq-mean cut +45.0 / d mean -3265; JN03: L6M eq-mean cut +42.2 / d mean +1251, PRE eq-mean cut +40.9 / d mean -3107, X' eq-mean cut +70.4 / d mean +2543, HOLD eq-mean cut +28.7 / d mean -2593; JN04: L6M eq-mean cut +53.5 / d mean +4860, PRE eq-mean cut +43.7 / d mean -3620, X' eq-mean cut +74.2 / d mean +2252, HOLD eq-mean cut +55.3 / d mean -1456; JN05: L6M eq-mean cut +39.5 / d mean +1610, PRE eq-mean cut +23.9 / d mean -4001; JN06: L6M eq-mean cut +34.7 / d mean +2896, PRE eq-mean cut +36.8 / d mean -3311; JP01: L6M eq-mean cut +49.6 / d mean +3109, PRE eq-mean cut +48.8 / d mean -3218, X' eq-mean cut +70.3 / d mean +1165, HOLD eq-mean cut +55.8 / d mean -2559; JP02: L6M eq-mean cut +41.6 / d mean +550, PRE eq-mean cut +55.1 / d mean -3622, X' eq-mean cut +68.4 / d mean +1147, HOLD eq-mean cut +31.3 / d mean -3148; JP03: L6M eq-mean cut +42.4 / d mean +73, PRE eq-mean cut +47.2 / d mean -3713, X' eq-mean cut +69.8 / d mean +419, HOLD eq-mean cut +22.1 / d mean -3947; JP04: L6M eq-mean cut +51.8 / d mean +1729, PRE eq-mean cut +45.9 / d mean -3207, X' eq-mean cut +74.5 / d mean +2451, HOLD eq-mean cut +42.1 / d mean -3198; JP05: L6M eq-mean cut +36.4 / d mean +1472, PRE eq-mean cut +36.1 / d mean -2290, X' eq-mean cut +65.3 / d mean +2090, HOLD eq-mean cut +32.0 / d mean -1516; JP06: L6M eq-mean cut +30.2 / d mean -1426, PRE eq-mean cut +45.1 / d mean -3607; JY01: ; JY02: ; JY03: ; JY04: ; JY05: ; JY06: ; JZ01: L6M eq-mean cut +0.5 / d mean -5790, PRE eq-mean cut +39.8 / d mean -4554; JZ02: L6M eq-mean cut -4.6 / d mean -3587, PRE eq-mean cut +37.9 / d mean -5056; JZ03: L6M eq-mean cut -39.0 / d mean -3944, PRE eq-mean cut +35.9 / d mean -3919; JZ04: L6M eq-mean cut -28.8 / d mean -5200, PRE eq-mean cut +20.7 / d mean -4926.

Reading: the first-order joint screen of stacked down-sizing layers is NOT predictive of the engine. In the exact run a skipped signal frees the book, which then takes the next signal, and re-entries / locks / slice fills change; so a table that skips 60-85% of signals first-order removes only about 18% of the trades in the engine (F08 pair: 672 vs 823 trades in 202610, lots 1440 vs 1746) and behaves like a mild global lot reduction. Only exact numbers count. Missing windows are still running.

## REFIT 2026-11-22 (what the bi-weekly procedure would pick today; first-order screen, train = trailing 26 weeks to 2026-11-05, pick = lowest equal-mean train maxDD among live + 1500 random stacks)

Pick: SIZER=sizer_vt:4ddecada7421 | LOT=p7_other:29234d9766a9 | SIGQ=signal_quality:b9a6edabcd7b | REG=regime:9ecb10dea3f9 | STACK=equity_state:D|eqdd_book_20d_R|Y1R_f0.50_sticky|sess_london | COOL=cooldown:f511b70e6d8d | ZONE=zone:a4a12796db42 | A06=reg:a06_slots:a06_greedy_down | B02=live. Train maxDD at equal mean 94 vs live 79907. NOT exact-confirmed; the verdict needs the exact runs.

Standing rule 2 tolerance check of the top-10 stacks: PRE maxDD not more than 15% deeper than live and PRE mean not below live - 1k; failing stacks are labelled RECENT-ONLY (reported, not killed).

## Leave-one-layer-out of the exact stack J03 (ROLL-FIXED engine, exact, L6M + PRE; each row = J03 with one layer set back to live)

| set | layer dropped | cut L6M / L3M / L1M | eq-mean cut L6M | d mean L6M | PRE cut / eq-mean / d mean | HOLD cut | bi-weekly WF beat | 2a label |
|---|---|---|---|---|---|---|---|---|
| J03 | none (full J03) | +18.9 / +52.0 / +56.4 | +21.6 | +769 | +33.0 / +35.2 / -6170 | +29.2 | 65% | RECENT-ONLY (allow 25.0%, WF 65%) |
| JL01 | SIZER | +29.0 / +29.0 / +71.4 | +36.5 | +2625 | +37.9 / +44.5 / -4452 | +29.3 | 85% | RECENT-ONLY (allow 25.0%, WF 85%) |
| JL02 | LOT | +18.9 / +45.0 / +51.8 | +21.3 | +699 | +7.1 / +10.0 / -3773 | n/a | 64% | RECENT-ONLY (allow 25.0%, WF 64%) |
| JL03 | SIGQ | +14.9 / +59.8 / +59.7 | +21.1 | +1750 | +28.0 / +33.2 / -5161 | n/a | 64% | RECENT-ONLY (allow 24.915826255760347%, WF 64%) |
| JL04 | REG | +20.9 / +52.0 / +54.9 | +23.8 | +876 | +21.7 / +24.7 / -5740 | n/a | 59% | RECENT-ONLY (allow 15.0%, WF 59%) |
| JL05 | STACK | +10.1 / +47.5 / +60.4 | +9.8 | -94 | +27.2 / +26.9 / -6661 | n/a | 64% | RECENT-ONLY (allow 20.14357379434636%, WF 64%) |
| JL06 | COOL | +22.6 / +43.6 / +54.9 | +25.6 | +882 | +23.2 / +26.1 / -4592 | n/a | 59% | RECENT-ONLY (allow 15.0%, WF 59%) |

Reading: the STACK exposure cap (E same_side cap6_trunc london) carries the L6M gain (dropping it: L6M cut 10.1%, d mean -94). Dropping the SIZER (VT) layer IMPROVES recents (L6M cut 29.0%, d mean +2.6k/wk, L1M 71%) and raises PRE cut to 37.9% and PRE mean by +1.7k/wk. The PRE mean loss is NOT carried by one layer: every variant loses 3.8k-6.7k/wk on PRE; the LOT (P7 cap) layer costs about 2.4k/wk of PRE mean while adding about 26 points of PRE cut. The PRE loss is concentrated in 2024-H2 (J03 d mean -11.4k/wk, live +23k/wk) and 2025-H1 (-4.1k/wk), not in 2023 / 2024-H1.

New stacks queued for exact L6M + PRE (built from the leave-one-out; JN01 = JL01): JN01 = JL01: J03 minus SIZER; JN02 = JL01 minus SIGQ; JN03 = JL01 with LOT = LOT_P7_744; JN04 = JL01 minus COOL; JN05 = JL01 with STACK = E|same_side_lots_cap|cap8_skip|sess_london; JN06 = JL01 minus REG.

## Exact stack comparison (ROLL-FIXED engine, exact; standing rules 2 / 2a)

| stack | what | cut L6M / L3M / L1M | eq-mean L6M | d mean L6M / L3M | HOLD cut / d mean | PRE cut / d mean | X' cut / d mean | WF beat all (block B) | 2a label (PRE allowance, WF%) |
|---|---|---|---|---|---|---|---|---|---|
| J03 | full J03 (SIZER VT, LOT P7 cap, SIGQ, REG, STACK E cap6, COOL) | +18.9 / +52.0 / +56.4 | +21.6 | +769 / +513 | +29.2 / -1809 | +33.0 / -6170 | +72.6 / +3623 | 65% (55%) | RECENT-ONLY (allow 25.0%, WF 65%) |
| JL01 | J03 minus SIZER (= JN01) | +29.0 / +29.0 / +71.4 | +36.5 | +2625 / +3211 | +29.3 / -3207 | +37.9 / -4452 | +71.3 / +2509 | 85% (73%) | RECENT-ONLY (allow 25.0%, WF 85%) |
| JN02 | JL01 minus SIGQ | +28.8 / +28.8 / +78.4 | +37.9 | +3297 / +3649 | n/a / n/a | +36.9 / -3265 | n/a / n/a | 86% (n/a) | RECENT-ONLY (allow 25.0%, WF 86%) |
| JN03 | JL01 with LOT = LOT_P7_744 | +39.0 / +39.0 / +40.2 | +42.2 | +1251 / +1102 | +24.8 / -2593 | +37.6 / -3107 | +68.8 / +2543 | 82% (73%) | RECENT-ONLY (allow 25.0%, WF 82%) |
| JN04 | JL01 minus COOL | +43.4 / +43.4 / +67.9 | +53.5 | +4860 / +5959 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | 85% (82%) | RECENT-ONLY (allow 25.0%, WF 85%) |
| JN05 | JL01 with STACK = E|same_side_lots_cap|cap8_skip|sess_london | +35.2 / +35.2 / +56.2 | +39.5 | +1610 / +3448 | n/a / n/a | +18.4 / -4001 | n/a / n/a | 73% (n/a) | RECENT-ONLY (allow 25.0%, WF 73%) |
| JN06 | JL01 minus REG | +27.0 / +27.0 / +54.5 | +34.7 | +2896 / +3981 | n/a / n/a | +29.4 / -3311 | n/a / n/a | 77% (n/a) | RECENT-ONLY (allow 25.0%, WF 77%) |
| JP01 | JN04 + R1_3 P7 MaxDailyLoss 8400 lock | +42.6 / +42.6 / +50.8 | +49.6 | +3109 / +3822 | +49.6 / -2559 | +41.7 / -3218 | +66.2 / +1165 | 85% (91%) | RECENT-ONLY (allow 25.0%, WF 85%) |
| JP02 | JN04 + CDE F04 stack equity-DD London x0.25 sticky | +40.4 / +56.6 / +65.6 | +41.6 | +550 / -938 | +29.9 / -3148 | +54.2 / -3622 | +67.8 / +1147 | 84% (64%) | RECENT-ONLY (allow 25.0%, WF 84%) |
| JP03 | JN04 + CDE F01 max books on 1 London x0.5 | +42.2 / +46.5 / +76.0 | +42.4 | +73 / -1456 | +21.9 / -3947 | +47.0 / -3713 | +69.7 / +419 | 80% (64%) | RECENT-ONLY (allow 25.0%, WF 80%) |
| JP04 | JN04 x ZS_D0 zone table | +48.1 / +48.1 / +84.6 | +51.8 | +1729 / +4347 | +37.6 / -3198 | +41.7 / -3207 | +72.5 / +2451 | 85% (73%) | RECENT-ONLY (allow 25.0%, WF 85%) |
| JP05 | JN04 with LOT = P7 table 7,4,0,4,0,0 | +32.2 / +32.2 / +32.1 | +36.4 | +1472 / +2176 | +27.5 / -1516 | +31.9 / -2290 | +63.0 / +2090 | 84% (73%) | RECENT-ONLY (allow 25.0%, WF 84%) |
| JP06 | JN04 x ZS_D0 + R1_3 lock + F04 | +34.6 / +38.7 / +78.0 | +30.2 | -1426 / +998 | n/a / n/a | +48.6 / -3607 | n/a / n/a | 82% (n/a) | RECENT-ONLY (allow 25.0%, WF 82%) |

JPV is the regression of the new JointRep driver against the JN04 table run (must equal JN04 on the months run). CF_EN_45 (entry engulf hook) is not composed here; it needs the EntryMixin class swap.

## Per-period exact view (ROLL-FIXED; weekly sums, all weeks; maxDD cut and d mean per week vs live in each period)

| stack | HOLD 2025-11..2026-04 | X' 2023-04..2023-12 | X'/PRE 2024-01..2024-06 | PRE 2024-07..2024-12 | PRE 2025-01..2025-06 | L6M 2026-05..10 |
|---|---|---|---|---|---|---|
| J03 | +29.2 / -6375 | +72.6 / +5023 | +28.3 / +1011 | +21.0 / -11427 | +33.0 / -4077 | +18.9 / -2855 |
| JL01 | +29.3 / -5378 | +71.3 / +4050 | +46.1 / -1404 | +38.5 / -9700 | +37.9 / -2810 | +29.0 / +936 |
| JN04 | +45.6 / -4037 | +68.6 / +3635 | +48.5 / -1347 | +39.6 / -7361 | +31.4 / -3072 | +43.4 / +3301 |
| JP01 | +49.6 / -4457 | +66.2 / +2734 | +46.1 / -2042 | +29.5 / -8105 | +41.7 / -1099 | +42.6 / +1428 |
| JP04 | +37.6 / -3900 | +72.5 / +3951 | +46.7 / -2112 | +45.7 / -7376 | +41.7 / -1300 | +48.1 / -223 |
| JP05 | +27.5 / -1333 | +63.0 / +3163 | +55.2 / +1530 | +1.0 / -7543 | +33.3 / -1868 | +32.2 / +74 |

Reading: the mean loss of these stacks is concentrated in 2024-H2 (-7k to -11k per week while the live made +23k) and in the HOLD months 2025-11..2026-04 (-1.3k to -6.4k); 2025-H1 loses 1-4k; X' 2023 is mean-positive (+2.7k to +5.0k per week) with 63-73% maxDD cuts; L6M is flat to positive. The PRE problem is therefore not a PRE-only artifact: HOLD shows the same sign, so these stacks buy their drawdown cut with mean in strong-trend months.

## REFIT 2026-11-22 from EXACT ROLL-FIXED series (27 exact stacks with the full 2026-05..10 block; train = trailing 26 weeks to 2026-11-05)

Ranking = Z.refit_pick (maxDD, worst-20, Ulcer, mean). Live trailing: maxDD 79907, mean 24125/wk.

Pick among all candidates: **JP04**. Pick among candidates whose trailing mean is not below live: **JN04**.

| rank | stack | trailing maxDD | worst-20 | mean/wk | rule 2a label (PRE exact) |
|---|---|---|---|---|---|
| 1 | JP04 | 41501 | 204974 | 23946 | RECENT-ONLY (allow 25.0%, WF 82%) |
| 2 | JN04 | 45203 | 266189 | 27187 | RECENT-ONLY (allow 25.0%, WF 82%) |
| 3 | JP01 | 45880 | 233710 | 25352 | RECENT-ONLY (allow 25.0%, WF 77%) |
| 4 | JP03 | 46157 | 220338 | 25450 | RECENT-ONLY (allow 25.0%, WF 82%) |
| 5 | JP02 | 47594 | 251694 | 26137 | RECENT-ONLY (allow 25.0%, WF 82%) |
| 6 | JN03 | 48727 | 203100 | 23553 | RECENT-ONLY (allow 25.0%, WF 68%) |
| 7 | JN05 | 51781 | 202875 | 24141 | RECENT-ONLY (allow 25.0%, WF 73%) |
| 8 | JP06 | 52249 | 163702 | 20945 | RECENT-ONLY (allow 25.0%, WF 82%) |
| 9 | JP05 | 54192 | 227278 | 24082 | RECENT-ONLY (allow 25.0%, WF 64%) |
| 10 | JL01 | 56706 | 234827 | 25172 | RECENT-ONLY (allow 25.0%, WF 82%) |

Candidates with trailing mean >= live, best 5: JN04 (maxDD 45203, mean 27187, RECENT-ONLY); JP01 (maxDD 45880, mean 25352, RECENT-ONLY); JP03 (maxDD 46157, mean 25450, RECENT-ONLY); JP02 (maxDD 47594, mean 26137, RECENT-ONLY); JN05 (maxDD 51781, mean 24141, RECENT-ONLY).

This is the pick of a screen over 27 stacks chosen by earlier steps (in-sample over the recent block), not a validated deployment; the bi-weekly WF columns above are the out-of-sample evidence.


## Plain sentence

EXACT (recents first): the best exact joint stack so far is JN04: it lowers L6M maxDD +43.4% at equal lots (+53.5% at equal mean, d mean +4860 $/wk), L3M +43.4%, L1M +67.9%; it differs from live in these layers: ?. On the prior it reads: PRE cut +31.4% with d mean -3620 $/wk and X' cut +68.6%; standing rule 2a label: RECENT-ONLY (allow 25.0%, WF 85%).

First-order screen: the best first-order joint stack lowers L6M maxDD +100.0% at equal mean (PRE +84.8%, X' +84.9%) and differs from live in these layers: SIZER=reg:sizer:AB_73ca99b0ec2d, LOT=reg:lot_tables:lot_greedy_down, REG=regime:e18edff4f8d3, COOL=cooldown:fbe1c726c9b2, A06=reg:a06_slots:a06_greedy_down, B02=reg:b02:B02_K7P7H7_20_1.00_alld_0.0. The screen is lot-level layers only, in-sample, and first-order overstates badly (exact J-pair and joint-stack runs gave a fraction of it). The verdict comes from exact runs, the bi-weekly re-pick WF and the REFIT section; cut / profit / lock / entry / NTZ layers join only through exact hooks.
