# STRUCT48 LEADERBOARD

Updated 2026-10-24T14:07:44Z. Benchmark Set A (corrected P9, live cost, locks on): WF $24,975/wk, SD 104,523, maxDD 401,293. 644 cells scored in rows/*.json. Rows with stage=pre are WF-PRE numbers (holdout not looked); stage=final are WF + holdout.

PASS cells (6/6): 0

## Top 25 overall (by pass count, then d mean)

| track | cell | stage | d mean $/wk | d maxDD $ | CI | placebo | holdout d $/wk | pass /6 | neighbours | failed |
|---|---|---|---|---|---|---|---|---|---|---|
| T3 | ORB_ASIA_15_v1__s60@1.0 | final | 16,276 | 402,533 | [1,553,32,788] | 0.96 | 24,491 | 5 | Y | c2_maxdd_not_worse |
| T3 | ORB_ASIA_15_v1__s75@1.0 | final | 15,455 | 324,955 | [926,30,113] | 0.96 | 29,359 | 5 | Y | c2_maxdd_not_worse |
| T3 | ORB_NY_15_v0__s75@0.5 | pre | 12,611 | -28,690 | [1,193,23,188] | 1.00 | - | 5 | Y | c5_holdout_sign(not looked) |
| T3 | ORB_ASIA_15_v1__s60@0.5 | final | 8,138 | 157,032 | [776,16,394] | 0.96 | 12,245 | 5 | Y | c2_maxdd_not_worse |
| T3 | ORB_ASIA_15_v1__s75@0.5 | final | 7,727 | 129,729 | [463,15,057] | 0.96 | 14,680 | 5 | Y | c2_maxdd_not_worse |
| T3 | ORB_NY_15_v0__s75@0.25 | pre | 6,305 | -15,439 | [596,11,594] | 1.00 | - | 5 | Y | c5_holdout_sign(not looked) |
| T3 | ON_none_L4 | final | 4,716 | -62,917 | [-540,10,046] | 0.96 | 6,264 | 5 | Y | c3_ci_excludes0 |
| T3 | ON_VT_L4 | final | 4,445 | -29,520 | [145,9,196] | 0.75 | 3,992 | 5 | Y | c4_placebo_ge95 |
| T3 | ORB_ASIA_15_v1__s60@0.25 | final | 4,069 | 49,875 | [388,8,197] | 0.96 | 6,123 | 5 | Y | c2_maxdd_not_worse |
| T3 | ORB_ASIA_15_v1__s75@0.25 | final | 3,864 | 37,157 | [232,7,528] | 0.96 | 7,340 | 5 | Y | c2_maxdd_not_worse |
| T3 | ON_none_L2 | final | 2,358 | -43,538 | [-270,5,023] | 0.96 | 3,132 | 5 | Y | c3_ci_excludes0 |
| T3 | ON_VT_L2 | final | 2,223 | -22,691 | [72,4,598] | 0.75 | 1,996 | 5 | Y | c4_placebo_ge95 |
| T3 | ORB_NY_15_v0__s60@1.0 | pre | 31,923 | 106,669 | [8,737,53,243] | 1.00 | - | 4 | Y | c2_maxdd_not_worse, c5_holdout_sign(not looked) |
| T3 | ORB_NY_15_v0__s75@1.0 | pre | 25,222 | 96,897 | [2,386,46,375] | 1.00 | - | 4 | Y | c2_maxdd_not_worse, c5_holdout_sign(not looked) |
| T3 | ORB_ASIA_30_v1__s60@1.0 | final | 16,003 | 409,961 | [-464,32,465] | 0.98 | 26,620 | 4 | Y | c2_maxdd_not_worse, c3_ci_excludes0 |
| T3 | ORB_NY_15_v0__s60@0.5 | pre | 15,962 | 28,024 | [4,369,26,622] | 1.00 | - | 4 | Y | c2_maxdd_not_worse, c5_holdout_sign(not looked) |
| T3 | ORB_ASIA_30_v1__s75@1.0 | final | 14,390 | 431,698 | [-2,059,30,776] | 0.96 | 28,509 | 4 | Y | c2_maxdd_not_worse, c3_ci_excludes0 |
| T3 | ORB_ASIA_30_v1__s50@1.0 | final | 11,468 | 415,379 | [-4,170,27,370] | 0.95 | 20,400 | 4 | Y | c2_maxdd_not_worse, c3_ci_excludes0 |
| T3 | ORB_ASIA_30_v1__s60@0.5 | final | 8,001 | 178,198 | [-232,16,232] | 0.98 | 13,310 | 4 | Y | c2_maxdd_not_worse, c3_ci_excludes0 |
| T3 | ORB_NY_15_v0__s60@0.25 | pre | 7,981 | 14,012 | [2,184,13,311] | 1.00 | - | 4 | Y | c2_maxdd_not_worse, c5_holdout_sign(not looked) |
| T3 | ORB_ASIA_30_v1__s75@0.5 | final | 7,195 | 189,066 | [-1,030,15,388] | 0.96 | 14,254 | 4 | Y | c2_maxdd_not_worse, c3_ci_excludes0 |
| T3 | ORB_ASIA_30_v1__s50@0.5 | final | 5,734 | 180,907 | [-2,085,13,685] | 0.95 | 10,200 | 4 | Y | c2_maxdd_not_worse, c3_ci_excludes0 |
| T3 | ON_VT_L4 | pre | 4,798 | -29,520 | [193,9,606] | 0.91 | - | 4 | Y | c4_placebo_ge95, c5_holdout_sign(not looked) |
| T3 | ORB_ASIA_30_v1__s60@0.25 | final | 4,001 | 77,380 | [-116,8,116] | 0.98 | 6,655 | 4 | Y | c2_maxdd_not_worse, c3_ci_excludes0 |
| T3 | ORB_NY_30_v0__s75@0.25 | pre | 3,764 | -49,201 | [-1,623,9,450] | 0.97 | - | 4 | Y | c3_ci_excludes0, c5_holdout_sign(not looked) |

## Track 3: 630 cells scored; top 10

| track | cell | stage | d mean $/wk | d maxDD $ | CI | placebo | holdout d $/wk | pass /6 | neighbours | failed |
|---|---|---|---|---|---|---|---|---|---|---|
| T3 | ORB_ASIA_15_v1__s60@1.0 | final | 16,276 | 402,533 | [1,553,32,788] | 0.96 | 24,491 | 5 | Y | c2_maxdd_not_worse |
| T3 | ORB_ASIA_15_v1__s75@1.0 | final | 15,455 | 324,955 | [926,30,113] | 0.96 | 29,359 | 5 | Y | c2_maxdd_not_worse |
| T3 | ORB_NY_15_v0__s75@0.5 | pre | 12,611 | -28,690 | [1,193,23,188] | 1.00 | - | 5 | Y | c5_holdout_sign(not looked) |
| T3 | ORB_ASIA_15_v1__s60@0.5 | final | 8,138 | 157,032 | [776,16,394] | 0.96 | 12,245 | 5 | Y | c2_maxdd_not_worse |
| T3 | ORB_ASIA_15_v1__s75@0.5 | final | 7,727 | 129,729 | [463,15,057] | 0.96 | 14,680 | 5 | Y | c2_maxdd_not_worse |
| T3 | ORB_NY_15_v0__s75@0.25 | pre | 6,305 | -15,439 | [596,11,594] | 1.00 | - | 5 | Y | c5_holdout_sign(not looked) |
| T3 | ON_none_L4 | final | 4,716 | -62,917 | [-540,10,046] | 0.96 | 6,264 | 5 | Y | c3_ci_excludes0 |
| T3 | ON_VT_L4 | final | 4,445 | -29,520 | [145,9,196] | 0.75 | 3,992 | 5 | Y | c4_placebo_ge95 |
| T3 | ORB_ASIA_15_v1__s60@0.25 | final | 4,069 | 49,875 | [388,8,197] | 0.96 | 6,123 | 5 | Y | c2_maxdd_not_worse |
| T3 | ORB_ASIA_15_v1__s75@0.25 | final | 3,864 | 37,157 | [232,7,528] | 0.96 | 7,340 | 5 | Y | c2_maxdd_not_worse |

## Track 4: 14 cells scored; top 10

| track | cell | stage | d mean $/wk | d maxDD $ | CI | placebo | holdout d $/wk | pass /6 | neighbours | failed |
|---|---|---|---|---|---|---|---|---|---|---|
| T4 | T4.1a | interim-no-holdout | - | - | - | - | - | - | - |  |
| T4 | T4.1b | interim-no-holdout | - | - | - | - | - | - | - |  |
| T4 | T4.2_L0 | interim-no-holdout | - | - | - | - | - | - | - |  |
| T4 | T4.2_Lm2 | interim-no-holdout | - | - | - | - | - | - | - |  |
| T4 | T4.2_Y4 | interim-no-holdout | - | - | - | - | - | - | - |  |
| T4 | T4.2_LB0 | interim-no-holdout | - | - | - | - | - | - | - |  |
| T4 | T4.3_G1 | interim-no-holdout | - | - | - | - | - | - | - |  |
| T4 | T4.3_G4 | interim-no-holdout | - | - | - | - | - | - | - |  |
| T4 | T4.3_S2x7 | interim-no-holdout | - | - | - | - | - | - | - |  |
| T4 | T4.4_W2 | interim-no-holdout | - | - | - | - | - | - | - |  |

Ledger: PRED corrected 27,682 + STRUCT48 655 ({'T1': 151, 'T3.3': 58, 'T2': 39, 'T4': 14, 'T3.2': 162, 'T3_1': 90, 'T3.5': 20, 'T3.6b1': 30, 'T3.6b2': 30, 'T3.7b3': 29, 'T3.7b4': 26, 'T3.7rsi2c': 6}) = cumulative 28,337 trials.
