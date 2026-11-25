# LONDON_PRIMARY_FILE_SIZE - London recent-basis weighted stack STKd8w42lo (= STKd8e4ab42ac) pick JT4 at the file sizes (W-LAYERS2, 2026-11-25 19:17Z)

## 1. LOTS PER SESSION (book) at each size, for drawdown sizing

Fit basis = base 4 (4/2/1; weights 1 / 0.5 / 0.25). Base 6 is tested both ways (6/3/1 and 6/3/2: the 0.25 book at 1.5 lots rounds either way); base 3 is 3/2/1 (0.5 x 3 = 1.5 rounds up) and 3/1/1. R per lot = median stop pts x $20 (NQ). Entry window = first and last entry time ET of the book in the event file. Whole-stack dollars throughout the rest of the page are for all three books together.

| book | events | entry window ET | stop pts (R $/lot) | base 6a lots (R at risk) | base 6b lots (R at risk) | base 4 lots (R at risk) | base 3a lots (R at risk) | base 3b lots (R at risk) |
|---|---|---|---|---|---|---|---|---|
| MF1 | L19201dfc.BRF90_30 | 0200-0829 | 90.0 ($1800) | 6 ($10800) | 6 ($10800) | 4 ($7200) | 3 ($5400) | 3 ($5400) |
| MF2 | L12842dde.BRP45 | 0200-0829 | 45.0 ($900) | 3 ($2700) | 3 ($2700) | 2 ($1800) | 2 ($1800) | 1 ($900) |
| MF3 | L74274eca.BRF120_60 | 0200-0829 | 120.0 ($2400) | 1 ($2400) | 2 ($4800) | 1 ($2400) | 1 ($2400) | 1 ($2400) |

The "per session" lots are the per-book lots above (a session = one book entry window, London). Total at risk if every book is stopped: base 6a $15900; base 6b $18300; base 4 $11400; base 3a $9600; base 3b $8700

## 2. WHOLE-STACK RESULTS (dollars for the whole three-book stack, not per lot). PICK = JT4 (GATE: FAIL on the prior-year bands RED / RED / RED; rolling walk-forward 0.775 passes; null pending; see BAREFIT_LO_STKd8w42lo_L1.md), static caps scaled by file lots / fit lots. BARE = the same stack with no layers at the same size (reference only).

### base 6a (6/3/1)

| row | L6M | L3M | 2023 $/wk, max DD | 2024 $/wk, max DD | 2025 $/wk, max DD |
|---|---|---|---|---|---|
| PICK | $7535/wk, ulcer 5010, max DD -12776, worst wk -8516, worst day -9131 | $9913/wk, ulcer 4658, max DD -11657, worst wk -5824, worst day -9131 | $679, -27122 | $330, -39663 | $-1975, -135490 |
| BARE | $14815/wk, ulcer 9024, max DD -27028, worst wk -13345, worst day -19973 | $13289/wk, ulcer 10503, max DD -27028, worst wk -13345, worst day -15591 | $2284, -48995 | $3142, -64636 | $903, -161224 |

### base 6b (6/3/2)

| row | L6M | L3M | 2023 $/wk, max DD | 2024 $/wk, max DD | 2025 $/wk, max DD |
|---|---|---|---|---|---|
| PICK | $8081/wk, ulcer 5502, max DD -14183, worst wk -7636, worst day -13998 | $11002/wk, ulcer 5125, max DD -13037, worst wk -7003, worst day -9836 | $409, -39097 | $9, -43837 | $-1990, -138170 |
| BARE | $15548/wk, ulcer 10602, max DD -33376, worst wk -18230, worst day -19907 | $14989/wk, ulcer 12554, max DD -33376, worst wk -16062, worst day -17848 | $2343, -60777 | $3941, -63468 | $1384, -169030 |

### base 4 (4/2/1)

| row | L6M | L3M | 2023 $/wk, max DD | 2024 $/wk, max DD | 2025 $/wk, max DD |
|---|---|---|---|---|---|
| PICK | $5847/wk, ulcer 3210, max DD -8124, worst wk -6244, worst day -7522 | $7590/wk, ulcer 3253, max DD -8124, worst wk -3461, worst day -6352 | $293, -24534 | $529, -31437 | $-1227, -83262 |
| BARE | $10773/wk, ulcer 6305, max DD -19383, worst wk -10078, worst day -12650 | $9954/wk, ulcer 7424, max DD -19383, worst wk -9051, worst day -10341 | $1617, -36148 | $2535, -41168 | $1023, -107674 |

### base 3a (3/2/1)

| row | L6M | L3M | 2023 $/wk, max DD | 2024 $/wk, max DD | 2025 $/wk, max DD |
|---|---|---|---|---|---|
| PICK | $5731/wk, ulcer 3058, max DD -8380, worst wk -6514, worst day -7777 | $7373/wk, ulcer 2881, max DD -7005, worst wk -2702, worst day -6352 | $112, -24713 | $573, -26943 | $-1251, -80370 |
| BARE | $9243/wk, ulcer 5967, max DD -18375, worst wk -10609, worst day -10313 | $8627/wk, ulcer 6335, max DD -17501, worst wk -8373, worst day -9741 | $1367, -33802 | $2276, -33975 | $927, -96261 |

### base 3b (3/1/1)

| row | L6M | L3M | 2023 $/wk, max DD | 2024 $/wk, max DD | 2025 $/wk, max DD |
|---|---|---|---|---|---|
| PICK | $5031/wk, ulcer 3011, max DD -8321, worst wk -5477, worst day -6867 | $6513/wk, ulcer 3187, max DD -8321, worst wk -5477, worst day -6647 | $-168, -29348 | $584, -28234 | $-663, -53947 |
| BARE | $7946/wk, ulcer 5526, max DD -18610, worst wk -8469, worst day -9841 | $7574/wk, ulcer 5816, max DD -15837, worst wk -8469, worst day -8017 | $1108, -27112 | $1971, -27064 | $1044, -68585 |

## 3. DAYS THE DAY-STOP FIRED (the pick's daily-loss hooks together; days whose trades or P&L differ from the same pick with them removed, L6M)

- base 6a: day-stop changed 8 of 131 L6M days; changed-day P&L with -27445 vs without -29203
- base 6b: day-stop changed 8 of 131 L6M days; changed-day P&L with -33555 vs without -35705
- base 4: day-stop changed 7 of 131 L6M days; changed-day P&L with -16476 vs without -17483
- base 3a: day-stop changed 7 of 131 L6M days; changed-day P&L with -15297 vs without -16303
- base 3b: day-stop changed 8 of 131 L6M days; changed-day P&L with -10752 vs without -11654
