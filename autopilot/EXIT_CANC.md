# EXIT_CANC (W-EXITENG): exit recipes on the D8 working-rule base _CANC (hand-over events). Research only.

| session | book | exit | ready | controls L6M | L3M | ulcer L6M ex/CANC | years $/wk ex/CANC (ulcer) | years>0 | PASS |
|---|---|---|---|---|---|---|---|---|---|
| NY | L488784d8 | bricks3_v25 | True | 30 | 21 | 2285/3024 | 2023 22/459 (ulc 5494/4875) 2024 539/381 (ulc 3485/5109) 2025 734/622 (ulc 3204/11834) | True | True |
| NY | L488784d8 | v25_t2 | True | 30 | 21 | 2335/3024 | 2023 267/459 (ulc 3659/4875) 2024 438/381 (ulc 2805/5109) 2025 384/622 (ulc 11797/11834) | True | True |
| AS | L29b1bc3f | v25_t2 | True | 27 | 12 | 2991/3897 | 2023 -346/40 (ulc 10312/6301) 2024 98/325 (ulc 7413/8793) 2025 232/519 (ulc 7531/8722) | False | False |

## NEW GATES (walk-forward persistence >= 0.58 drawdown first; prior-year band red > 30% fails; null n/a; 27/30 shown in the table above is information only)

| basis | session | book | exit | WF persistence (periods) | 2023 ulcer% / eq-risk $% (band) | 2024 | 2025 | null | 27/30 (L6M / L3M, old count) | verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| _CANC | NY | L488784d8 | bricks3_v25 | 0.72 (85) | +13 / +96 (red) | -32 / -107 (green) | -73 / -336 (green) | n/a | 30 / 21 | not kept |
| _CANC | NY | L488784d8 | v25_t2 | 0.72 (85) | -25 / +22 (amber) | -45 / -109 (green) | -0 / +38 (red) | n/a | 30 / 21 | not kept |
| _CANC | AS | L29b1bc3f | v25_t2 | 0.55 (85) | +64 / +626 (red) | -16 / +64 (red) | -14 / +48 (red) | n/a | 27 / 12 | not kept |

- NY L488784d8 `bricks3_v25`: **exit not kept** - prior-year red: 2023 (ulcer +13%, eq-risk $/wk +96% worse)
- NY L488784d8 `v25_t2`: **exit not kept** - prior-year red: 2025 (ulcer -0%, eq-risk $/wk +38% worse)
- AS L29b1bc3f `v25_t2`: **exit not kept** - walk-forward persistence 0.55 < 0.58; prior-year red: 2023 (ulcer +64%, eq-risk $/wk +626% worse), 2024 (ulcer -16%, eq-risk $/wk +64% worse), 2025 (ulcer -14%, eq-risk $/wk +48% worse)
