# NYPM_PRIMARY_FILE_SIZE - NY PM primary stack STKd8w42pm (recent-basis weighted STKd8e1d3c0ce) pick JT19 at the file sizes (W-LAYERS2, 2026-11-25 17:28Z)

## 1. LOTS PER SESSION (book) at each size, for drawdown sizing

Fit basis = base 4 (4/4/8/4/2). R per lot = median stop pts x $20 (NQ). Entry window = first and last entry time ET of the book in the event file. Whole-stack dollars throughout the rest of the page are for all five books together.

| book | events | entry window ET | stop pts (R $/lot) | base 6 lots (R at risk) | base 4 lots (R at risk) | base 3 lots (R at risk) |
|---|---|---|---|---|---|---|
| MF1 | L6d238076.BRF90_30 | 1201-1559 | 90.0 ($1800) | 6 ($10800) | 4 ($7200) | 3 ($5400) |
| MF2 | L8dff280f.BRP90 | 1200-1800 | 90.0 ($1800) | 6 ($10800) | 4 ($7200) | 3 ($5400) |
| MF3 | L4bdd521a.BRF80_40 | 1200-1530 | 80.0 ($1600) | 12 ($19200) | 8 ($12800) | 6 ($9600) |
| MF4 | L8e0bf58c.BRS8U | 1200-1559 | 120.0 ($2400) | 6 ($14400) | 4 ($9600) | 3 ($7200) |
| MF5 | L52359bf4.BRP30 | 1200-1800 | 30.0 ($600) | 3 ($1800) | 2 ($1200) | 2 ($1200) |

All five books trade inside one NY PM session window; the "per session" lots are the per-book lots above (a session = one book entry window). Total at risk if every book is stopped: base 6 $57000, base 4 $38000, base 3 $28800.

## 2. WHOLE-STACK RESULTS (dollars for the whole five-book stack, not per lot). PICK = JT19 (PROVISIONAL until the gated verdict), static caps scaled by file lots / fit lots. BARE = the same stack with no layers at the same size (reference only).

### base 6 (6/6/12/6/3)

| row | L6M | L3M | 2023 $/wk, max DD | 2024 $/wk, max DD | 2025 $/wk, max DD |
|---|---|---|---|---|---|
| PICK | $19392/wk, ulcer 8180, max DD -25044, worst wk -23907, worst day -24302 | $20133/wk, ulcer 6452, max DD -21602, worst wk -8332, worst day -16709 | $3779, -68141 | $3084, -114292 | $5585, -161083 |
| BARE | $36383/wk, ulcer 17915, max DD -84327, worst wk -28739, worst day -63154 | $34690/wk, ulcer 16327, max DD -54582, worst wk -12263, worst day -49803 | $14675, -87872 | $9473, -214034 | $22646, -137579 |

### base 4 (4/4/8/4/2)

| row | L6M | L3M | 2023 $/wk, max DD | 2024 $/wk, max DD | 2025 $/wk, max DD |
|---|---|---|---|---|---|
| PICK | $13298/wk, ulcer 5536, max DD -18074, worst wk -17369, worst day -16450 | $14084/wk, ulcer 3912, max DD -12874, worst wk -6184, worst day -11618 | $2824, -40583 | $2199, -82569 | $3810, -101174 |
| BARE | $24985/wk, ulcer 11696, max DD -55861, worst wk -18817, worst day -41896 | $24083/wk, ulcer 10508, max DD -35805, worst wk -7770, worst day -33004 | $9933, -58488 | $6863, -130798 | $15662, -89607 |

### base 3 (3/3/6/3/2)

| row | L6M | L3M | 2023 $/wk, max DD | 2024 $/wk, max DD | 2025 $/wk, max DD |
|---|---|---|---|---|---|
| PICK | $11679/wk, ulcer 4837, max DD -17925, worst wk -14096, worst day -17925 | $12291/wk, ulcer 3631, max DD -10994, worst wk -6136, worst day -10994 | $2458, -34664 | $2290, -70695 | $3157, -77403 |
| BARE | $19133/wk, ulcer 8857, max DD -41152, worst wk -14198, worst day -31364 | $18402/wk, ulcer 8242, max DD -27975, worst wk -7291, worst day -23676 | $7553, -46654 | $5106, -94342 | $12475, -66529 |

## 3. DAYS THE DAY-STOP FIRED (the pick's daily-loss hooks DLA9 / DLB11 / DLC6 together; days whose trades or P&L differ from the same pick with them removed, L6M)

- base 6: day-stop changed 11 of 131 L6M days; changed-day P&L with -32824 vs without -29202
- base 4: day-stop changed 11 of 131 L6M days; changed-day P&L with -12970 vs without -11167
- base 3: day-stop changed 11 of 131 L6M days; changed-day P&L with -16158 vs without -14355
