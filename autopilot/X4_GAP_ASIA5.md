# X4_GAP_ASIA5 - why the x4 run does not scale (W-LAYERS, 2026-11-22 10:44Z) - 5-book Asia stack TL3_ALN_AS_STKd8106b26ef, L6M

Source: landed engine rows only (no depth data: the "levels walked" figure is W-COMBO's). Per lot = dollars / lots.

| set | lots | ulcer | max DD | worst week | $/wk | per lot: ulcer / max DD / $ per wk | trades | exits: Stop / Target / DayHalt / BookLock / StackCut | trades with lots < base | mean lots |
|---|---|---|---|---|---|---|---|---|---|---|
| R0 x1 | 1 | 3046 | -9450 | -4971 | 10834 | 3046 / -9450 / 10834 | 2259 | 1154 / 774 / 0 / 0 / 0 | 0 | 1.00 |
| R0 x2 | 2 | 6963 | -21015 | -19862 | 20495 | 3481 / -10508 / 10247 | 2261 | 1160 / 769 / 0 / 0 / 0 | 0 | 2.00 |
| R0 x3 | 3 | 11608 | -39028 | -30088 | 29550 | 3869 / -13009 / 9850 | 2261 | 1163 / 765 / 0 / 0 / 0 | 0 | 3.00 |
| R0 x4 | 4 | 15687 | -52366 | -40859 | 38613 | 3922 / -13091 / 9653 | 2259 | 1163 / 762 / 0 / 0 / 0 | 0 | 4.00 |
| R1 x1 (today) | 1 | 3462 | -11350 | -4928 | 9103 | 3462 / -11350 / 9103 | 1939 | 687 / 619 / 0 / 121 / 293 | 0 | 1.00 |
| R1 x4 non-lin, caps x4 | 4 | 15090 | -42733 | -31261 | 11086 | 3773 / -10683 / 2772 | 994 | 313 / 212 / 0 / 382 / 2 | 116 | 3.77 |
| R1 x4 lin, caps x4 | 4 | 11727 | -39464 | -15817 | 34991 | 2932 / -9866 / 8748 | 1884 | 856 / 655 / 1 / 106 / 20 | 209 | 3.78 |
| R1 x4 lin, caps NOT scaled | 4 | 13760 | -43865 | -35231 | 23844 | 3440 / -10966 / 5961 | 1401 | 622 / 509 / 4 / 93 / 15 | 168 | 3.76 |
| R1 x4 non-lin, caps NOT scaled | 4 | 15949 | -51683 | -36644 | 9611 | 3987 / -12921 / 2403 | 886 | 264 / 176 / 2 / 385 / 2 | 109 | 3.75 |

### Fills only: R0 truly bare, the same signals at 1 and 4 lots (2243 matched trades of 2259 / 2259)

Adverse points = how much worse the 4-lot fill is than the 1-lot fill (positive = worse); P&L per lot = net dollars / lots.

| book | matched | entry adverse pts (mean) | entry >= 0.5 pt | exit adverse pts (stops) | exit adverse pts (targets) | P&L per lot at 1 lot | at 4 lots |
|---|---|---|---|---|---|---|---|
| MF1 | 572 | 0.25 | 6% | 0.03 | 0.75 | 82270 | 75058 |
| MF2 | 166 | 0.23 | 4% | -0.05 | -0.23 | 59144 | 58603 |
| MF3 | 208 | 0.24 | 3% | -0.20 | 2.42 | 17305 | 12245 |
| MF4 | 442 | 0.28 | 8% | -0.00 | 0.96 | 60373 | 53468 |
| MF5 | 855 | 0.29 | 11% | 0.02 | 0.32 | 75646 | 68824 |

Reading guide: R0 x1..x4 isolates the FILL effect (no rule at all). R1 x4 rows differ from R0 x4 by the wrapper rules; "caps x4 vs NOT scaled" and "lin vs non-lin" isolate the cap scaling and the BookLock-R (non-lin keeps base_qty 1, so BookLock R stays the 1-lot value at 4 lots).
