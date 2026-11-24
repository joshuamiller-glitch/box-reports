# ASIA FADE TABLE (bare, L6M 2026-05..10, L3M 08..10; $/wk, ulcer, max DD, worst week; stack sets x4 lots divided by 4 = 1-lot units; fade sizes 0.25/0.5/1 = 1/2/4 lots vs members at 4 lots)

## On Asia final STKd8da2eb47b (4 books)

| set | L6M $/wk | L3M $/wk | L6M ulcer | L6M max DD | L6M worst wk |
|---|---|---|---|---|---|
| WITHOUT fade (BF4_BASE /4) | 6833 | 5619 | 3528 | -12811 | -5197 |
| Le001fe42 P45 size 0.25 | 7455 | 6357 | 3618 | -13138 | -5146 |
| Le001fe42 P45 size 0.5 | 8043 | 7013 | 3708 | -13450 | -5078 |
| Le001fe42 P45 size 1 | 9179 | 8372 | 4031 | -14127 | -4977 |
| L1acc170a P45 size 0.25 | 7361 | 5979 | 3305 | -11897 | -5366 |
| L1acc170a P45 size 0.5 | 7830 | 6347 | 3341 | -11591 | -5537 |
| L1acc170a P45 size 1 | 8297 | 6713 | 4236 | -17269 | -10193 |
| L302f2cbb P60 size 0.25 | 7325 | 5998 | 3377 | -13300 | -5197 |
| L302f2cbb P60 size 0.5 | 7805 | 6351 | 3372 | -13944 | -5197 |
| L302f2cbb P60 size 1 | 8694 | 6928 | 3634 | -15682 | -5197 |
| L051dcad5 P30 size 0.25 | 7291 | 5995 | 3378 | -13086 | -5201 |
| L051dcad5 P30 size 0.5 | 7619 | 6239 | 3352 | -13370 | -5208 |
| L051dcad5 P30 size 1 | 8231 | 6761 | 3525 | -13966 | -5224 |
| Le3823c3e P45 size 0.25 | 7225 | 5833 | 3350 | -12918 | -5421 |
| Le3823c3e P45 size 0.5 | 7608 | 6038 | 3325 | -13043 | -5645 |
| Le3823c3e P45 size 1 | 8262 | 6243 | 3603 | -14142 | -6095 |

## On J502 alone

| set | L6M $/wk | L3M $/wk | L6M ulcer | L6M max DD | L6M worst wk |
|---|---|---|---|---|---|
| WITHOUT fade (BF4_BASE /4) | 2105 | 2489 | 546 | -1940 | -1635 |
| Le001fe42 P45 size 0.25 | 2727 | 3226 | 652 | -2218 | -1583 |
| Le001fe42 P45 size 0.5 | 3315 | 3882 | 894 | -3250 | -1516 |
| Le001fe42 P45 size 1 | 4452 | 5241 | 1632 | -5513 | -1942 |
| L1acc170a P45 size 0.25 | 2634 | 2848 | 574 | -2199 | -1803 |
| L1acc170a P45 size 0.5 | 3103 | 3216 | 889 | -3528 | -1975 |
| L1acc170a P45 size 1 | 3569 | 3583 | 2159 | -8598 | -5771 |
| L302f2cbb P60 size 0.25 | 2598 | 2867 | 709 | -2696 | -1635 |
| L302f2cbb P60 size 0.5 | 3077 | 3220 | 1038 | -3660 | -1972 |
| L302f2cbb P60 size 1 | 3967 | 3797 | 1870 | -5629 | -4279 |
| L051dcad5 P30 size 0.25 | 2563 | 2864 | 624 | -2796 | -1638 |
| L051dcad5 P30 size 0.5 | 2892 | 3109 | 866 | -4560 | -1646 |
| L051dcad5 P30 size 1 | 3503 | 3631 | 1598 | -8136 | -2245 |
| Le3823c3e P45 size 0.25 | 2498 | 2703 | 696 | -2612 | -1858 |
| Le3823c3e P45 size 0.5 | 2880 | 2908 | 956 | -3994 | -2808 |
| Le3823c3e P45 size 1 | 3534 | 3112 | 1623 | -6811 | -5635 |

## Each fade alone (1 lot, R0BR set) and daily L6M correlation with the stack (BF1_BASE)

| fade | bar / trigger | bracket | L6M $/wk | L3M $/wk | ulcer | max DD | worst wk | corr with stack (daily) |
|---|---|---|---|---|---|---|---|---|
| Le001fe42 | mrenko_20 trendline reject_native tol1.0 body | P45 | 2487 | 2950 | 1979 | -6481 | -3756 | 0.09 |
| L1acc170a | kagi_20 vwap false_break M3 k0.5 | P45 | 2113 | 1439 | 2279 | -5967 | -2647 | 0.20 |
| L302f2cbb | time_m_60 fib60 reject_native tol0.5 body | P60 | 1971 | 1515 | 2215 | -6292 | -4604 | 0.25 |
| L051dcad5 | pnf_14 piv_wf false_break_native M2 k0.5 | P30 | 1832 | 1502 | 2128 | -6976 | -2613 | 0.16 |
| Le3823c3e | vsess_450 gaps false_break_native M2 k0.5 | P45 | 1570 | 856 | 2135 | -5904 | -5573 | 0.20 |

## SCORING (18:40Z): prior years, walk-forward, stack controls for L1acc170a on STKd8da2eb47b (bare, 1-lot units; controls shift the fade only +-7k days, stack fixed)

### Size 0.25 (Z25): with fade vs without, 1-lot units, bare
| window | without $/wk / ulcer / maxDD | with $/wk / ulcer / maxDD | ulcer change |
|---|---|---|---|
| L6M | 6833 / 3528 / -12811 | 7361 / 3305 / -11897 | -6.3% |
| L3M | 5619 / 4276 / -12811 | 5979 / 3767 / -11897 | -11.9% |
| Y2023 | 835 / 3084 / -6915 | 862 / 3048 / -6251 | -1.2% |
| Y2024 | 1188 / 5961 / -15661 | 1085 / 6614 / -16463 | +11.0% |
| Y2025 | 1077 / 6860 / -19438 | 1294 / 6461 / -19209 | -5.8% |
| ALL | 2131 / 6005 / -30795 | 2292 / 6040 / -30263 | +0.6% |
Walk-forward (10-weekday blocks, all 42 months, n=92): with >= without in 59.8% (strictly better 59.8%). Gate >= 58%.
Stack controls (fade shifted +-7k days, k=1..15; stack fixed; missing 10): real L6M ulcer gain 223 beats 20 of 20 controls on L6M ulcer gain (control gains median -81, max 107); on ALL-period ulcer gain real -35 beats 16 of 20.

### Size 0.5 (Z50): with fade vs without, 1-lot units, bare
| window | without $/wk / ulcer / maxDD | with $/wk / ulcer / maxDD | ulcer change |
|---|---|---|---|
| L6M | 6833 / 3528 / -12811 | 7830 / 3341 / -11591 | -5.3% |
| L3M | 5619 / 4276 / -12811 | 6347 / 3622 / -10989 | -15.3% |
| Y2023 | 835 / 3084 / -6915 | 882 / 3077 / -6189 | -0.2% |
| Y2024 | 1188 / 5961 / -15661 | 966 / 8345 / -20229 | +40.0% |
| Y2025 | 1077 / 6860 / -19438 | 1468 / 6384 / -19206 | -6.9% |
| ALL | 2131 / 6005 / -30795 | 2422 / 6599 / -29707 | +9.9% |
Walk-forward (10-weekday blocks, all 42 months, n=92): with >= without in 58.7% (strictly better 58.7%). Gate >= 58%.
Stack controls (fade shifted +-7k days, k=1..15; stack fixed; missing 8): real L6M ulcer gain 187 beats 19 of 22 controls on L6M ulcer gain (control gains median -330, max 427); on ALL-period ulcer gain real -595 beats 13 of 22.

VERDICT (delivery gates, as far as scored):
- Size 0.25: L6M ulcer -6.3%, max DD better, $/wk +7.7%; L3M better; prior years ulcer 2023 -1.2%, 2024 +11.0% (maxDD worse, $/wk 1188 -> 1085), 2025 -5.8% (inside the 15% band by ulcer; the band rule B colour itself was not recomputed here); walk-forward 59.8% (gate 58%: passes, marginal); controls: 20 of 20 landed beaten, 10 control sets still missing months (re-queued), need 7 of those 10 for 27/30: OPEN. Whole 42-month ulcer +0.6% (no gain over all history), so the benefit is a recent-window effect.
- Size 0.5: prior-year 2024 ulcer +40.0% and max DD -20229 vs -15661 = fails the band; walk-forward 58.7% (marginal); controls 19 of 22 landed: OPEN (needs all 8 remaining). Not a candidate.
- Not yet done for either size: exit run, 2-lot joint fit, null label.

## RE-SCORE of the stack controls under the LEAD rule (19:00Z): score each control on the months it HAS, real stack-with vs without on the SAME months; < 4 of 6 L6M months = unscorable; gate = 90% of scorable (27 of 30)
(The earlier 20-of-20 / 19-of-22 lines above required all 42 months and dropped sets with a missing prior-year month. The missing months are all PRIOR-YEAR months (the engine's F4 exit-gap guard fires on shifted dates); every control has all 6 L6M months, so all 30 are scorable on the L6M basis.)
- L1acc170a at 0.25: beats 29 of 30 controls on L6M ulcer gain (gate 27): PASS. Same test over all available months (prior years included): 25 of 30 (gate 27): below the gate.
- L1acc170a at 0.5: L6M 27 of 30 (gate 27); all months 20 of 30. Already fails the 2024 band.
