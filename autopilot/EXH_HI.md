# EXH_HI - EX-PHI: profit families H (take) and I (tighten/trail), Stage 1 first order
Generated 2026-11-09 03:10Z. 9 cells scored (all ledgered, agent PHI). Label: PRE-PROOF (entries not live-matched). Fills: market exit k+1 mid -+0.80, targets nominal, stops at level. Features exist per month from the EX-FEAT store (rows with no feature never fire). Family p / WF / live week: not yet computed for these cells (lead runs family_p / walk_forward from the ledger); labels here are CAND-DD (L6M maxDD lower, L6M mean delta >= 0, PRE maxDD <= 1.05 x never-cut) only.

Ranking key: L6M maxDD (weekly, scope), then L6M worst-20, then Ulcer, then Calmar; filter nfire>=20, L6M mean >= never-cut. Delta mean columns are vs never-cut hold-to-bracket (the S1b-COMB live reference deltas are in the ledger columns *_dmean_c).
## Plain sentences
K7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3); stack-scope maxDD 15653 vs 26983 never-cut, L6M mean delta -21 USD/wk, PRE maxDD 27808 vs 30403; placebo p 0.015; does not qualify as CANDIDATE-DD.

P7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3); stack-scope maxDD 90109 vs 126710 never-cut, L6M mean delta -12018 USD/wk, PRE maxDD 143977 vs 131881; placebo p 0.015; does not qualify as CANDIDATE-DD.

M7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.1 feat=ahead_rel_fast secs=3 thr=1.3); stack-scope maxDD 28497 vs 43318 never-cut, L6M mean delta +867 USD/wk, PRE maxDD 58291 vs 48984; placebo p 0.015; does not qualify as CANDIDATE-DD.

U7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.5 feat=ahead_rel_fast secs=3 thr=1.3); stack-scope maxDD 11159 vs 21436 never-cut, L6M mean delta -921 USD/wk, PRE maxDD 28525 vs 42883; placebo p 0.015; does not qualify as CANDIDATE-DD.

A7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3); stack-scope maxDD 4398 vs 12456 never-cut, L6M mean delta -42 USD/wk, PRE maxDD 4987 vs 6208; placebo p 0.015; does not qualify as CANDIDATE-DD.

H7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3); stack-scope maxDD 6579 vs 16682 never-cut, L6M mean delta +240 USD/wk, PRE maxDD 9387 vs 20667; placebo p 0.015; CANDIDATE-DD.

O7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3); stack-scope maxDD 4897 vs 7489 never-cut, L6M mean delta +40 USD/wk, PRE maxDD 6648 vs 5097; placebo p 0.015; does not qualify as CANDIDATE-DD.

ALL profit: the technique that lowers L6M drawdown most is H_thick (arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3); stack-scope maxDD 85640 vs 117593 never-cut, L6M mean delta -15228 USD/wk, PRE maxDD 115552 vs 177634; placebo p 0.015; does not qualify as CANDIDATE-DD.

## Tables

### K7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut NOT MET by any cell: showing lowest-DD cells):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +1011 / -298 / +1866 / -21 / -893 / -3559 / -1561 / -23 | 15653 / 26983 | 27808 / 30403 | -5710 / -15009 | 6443 | 0.015 | pers 0.50 |  |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3 | +332 / +546 / +1198 / -1826 / -1898 / -676 / -1859 / -549 | 18678 / 26983 | 23006 / 30403 | -30259 / -15009 | 6443 | 0.015 | pers 0.75 |  |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=3 thr=1.3 | +767 / -2632 / -1000 / -1412 / -1354 / +72 / -1354 / -284 | 21625 / 26983 | 24589 / 30403 | -37710 / -15009 | 6443 | 0.015 | pers 0.25 |  |
| H_thick | arm=0.75 feat=ahead_rel_fast secs=1 thr=1.3 | -2692 / -1130 / -606 / -1316 / -1354 / -1180 / -435 / -190 | 23781 / 26983 | 27280 / 30403 | -37940 / -15009 | 6443 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.5 feat=ahead_rel_fast secs=3 thr=1.3 | +1736 / -3164 / -1181 / -2146 / -1752 / -847 / -827 / -191 | 23823 / 26983 | 29311 / 30403 | -34038 / -15009 | 6443 | 0.015 | pers 0.25 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +1011 / -298 / +1866 / -21 / -893 / -3559 / -1561 / -23 | 15653 / 26983 | 27808 / 30403 | -5710 / -15009 | 6443 | 0.015 | pers 0.50 |  |

### K7 - entry session 1
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3 | +2264 / +522 / +592 / +689 / +402 / +344 / -525 / -57 | 6455 / 13569 | 13969 / 16206 | -8934 / -31166 | 1515 | 0.015 | pers 1.00 | CAND-DD |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=3 thr=1.3 | +400 / -131 / -382 / +651 / +263 / +174 / -456 / -82 | 9060 / 13569 | 14177 / 16206 | -13812 / -31166 | 1515 | 0.015 | pers 0.50 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3 | +2264 / +522 / +592 / +689 / +402 / +344 / -525 / -57 | 6455 / 13569 | 13969 / 16206 | -8934 / -31166 | 1515 | 0.015 | pers 1.00 | CAND-DD |

### K7 - entry session 3
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.25 feat=ahead_rel_fast secs=3 thr=1.3 | -42 / +621 / +542 / +173 / +20 / -747 / -480 / -499 | 9133 / 20697 | 14019 / 6231 | -22556 / -31954 | 1524 | 0.015 | pers 0.75 |  |
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | -736 / +116 / +106 / +39 / -87 / -543 / -427 / -207 | 12234 / 20697 | 11388 / 6231 | -19536 / -31954 | 1524 | 0.015 | pers 0.75 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.25 feat=ahead_rel_fast secs=3 thr=1.3 | -42 / +621 / +542 / +173 / +20 / -747 / -480 / -499 | 9133 / 20697 | 14019 / 6231 | -22556 / -31954 | 1524 | 0.015 | pers 0.75 |  |

### K7 - entry session 4
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +892 / -228 / +125 / +114 / -380 / -688 / -275 / +84 | 4127 / 6324 | 36960 / 39576 | -4157 / -7330 | 1144 | 0.015 | pers 0.75 | CAND-DD |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=3 thr=1.3 | +286 / -195 / +140 / +94 / -335 / -525 / -372 / +4 | 5298 / 6324 | 34460 / 39576 | -2372 / -7330 | 1144 | 0.015 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +892 / -228 / +125 / +114 / -380 / -688 / -275 / +84 | 4127 / 6324 | 36960 / 39576 | -4157 / -7330 | 1144 | 0.015 | pers 0.75 | CAND-DD |

### P7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut NOT MET by any cell: showing lowest-DD cells):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3 | -24943 / -17791 / -12920 / -12018 / -8976 / +909 / -7800 / +207 | 90109 / 126710 | 143977 / 131881 | -87593 / -2075 | 4706 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=3 thr=1.3 | -23979 / -22152 / -16020 / -15169 / -11628 / -3817 / -5471 / +910 | 114315 / 126710 | 104776 / 131881 | -202521 / -2075 | 4706 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | -10336 / -9787 / -13922 / -12499 / -7883 / -5428 / -4195 / +401 | 125538 / 126710 | 129654 / 131881 | -74901 / -2075 | 4706 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.75 feat=ahead_rel_fast secs=1 thr=1.3 | -11851 / -10342 / -4359 / -6469 / -3230 / -157 / -2911 / -1810 | 133642 / 126710 | 107497 / 131881 | -93846 / -2075 | 4706 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.75 feat=ahead_rel_fast secs=3 thr=1.3 | -4473 / -6278 / -6779 / -4594 / -2429 / +2024 / -2776 / -1029 | 134778 / 126710 | 133273 / 131881 | -63460 / -2075 | 4706 | 0.015 | pers 0.00 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.75 feat=ahead_rel_fast secs=3 thr=1.3 | -4473 / -6278 / -6779 / -4594 / -2429 / +2024 / -2776 / -1029 | 134778 / 126710 | 133273 / 131881 | -63460 / -2075 | 4706 | 0.015 | pers 0.00 |  |

### P7 - entry session 3
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3 | +9636 / -2551 / +1504 / +3156 / +1025 / -1280 / -2851 / -1053 | 15504 / 103128 | 31542 / 75038 | -16296 / -164165 | 1144 | 0.015 | pers 0.75 | CAND-DD |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=3 thr=1.3 | +5010 / -3234 / +717 / +1593 / +320 / -2048 / -2272 / -314 | 44219 / 103128 | 48035 / 75038 | -68804 / -164165 | 1144 | 0.015 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3 | +9636 / -2551 / +1504 / +3156 / +1025 / -1280 / -2851 / -1053 | 15504 / 103128 | 31542 / 75038 | -16296 / -164165 | 1144 | 0.015 | pers 0.75 | CAND-DD |

### M7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=3 thr=1.3 | +1181 / -2062 / -289 / +867 / +421 / -1210 / -369 / -1085 | 28497 / 43318 | 58291 / 48984 | -38197 / -68462 | 3777 | 0.015 | pers 0.50 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=3 thr=1.3 | +1181 / -2062 / -289 / +867 / +421 / -1210 / -369 / -1085 | 28497 / 43318 | 58291 / 48984 | -38197 / -68462 | 3777 | 0.015 | pers 0.50 |  |

### M7 - entry session 1
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3 | +2246 / -1754 / +814 / +543 / +273 / -1570 / +434 / -208 | 13479 / 34745 | 48006 / 70941 | -9305 / -61665 | 2254 | 0.015 | pers 0.75 | CAND-DD |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=3 thr=1.3 | +1056 / -1684 / +77 / +341 / +215 / -1214 / +311 / -274 | 15274 / 34745 | 52736 / 70941 | -20286 / -61665 | 2254 | 0.015 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3 | +2246 / -1754 / +814 / +543 / +273 / -1570 / +434 / -208 | 13479 / 34745 | 48006 / 70941 | -9305 / -61665 | 2254 | 0.015 | pers 0.75 | CAND-DD |

### M7 - entry session 3
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=10 thr=1.3 | -576 / -688 / -612 / +22 / +85 / +358 / -411 / -416 | 15961 / 12246 | 11100 / 7533 | -24621 / -18056 | 1523 | 0.031 | pers 0.25 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=10 thr=1.3 | -576 / -688 / -612 / +22 / +85 / +358 / -411 / -416 | 15961 / 12246 | 11100 / 7533 | -24621 / -18056 | 1523 | 0.031 | pers 0.25 |  |

### U7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut NOT MET by any cell: showing lowest-DD cells):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.5 feat=ahead_rel_fast secs=3 thr=1.3 | +2734 / +438 / +837 / -921 / -647 / -823 / -308 / -1080 | 11159 / 21436 | 28525 / 42883 | 16061 / 45 | 1374 | 0.015 | pers 0.75 |  |
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +1005 / -803 / +530 / -585 / -12 / +159 / -11 / -953 | 13942 / 21436 | 26417 / 42883 | -10081 / 45 | 1374 | 0.015 | pers 0.50 |  |
| H_thick | arm=0.75 feat=ahead_rel_fast secs=1 thr=1.3 | +2433 / -1504 / -159 / -541 / -538 / -2165 / -712 / -736 | 14251 / 21436 | 29043 / 42883 | -4947 / 45 | 1374 | 0.015 | pers 0.25 |  |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3 | +6179 / -1541 / -1073 / -1751 / -1269 / -390 / -1765 / -627 | 14797 / 21436 | 63401 / 42883 | -22730 / 45 | 1374 | 0.015 | pers 0.25 |  |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=3 thr=1.3 | +7092 / -1584 / -654 / -1478 / -1237 / -929 / -1270 / -487 | 15131 / 21436 | 39804 / 42883 | -10822 / 45 | 1374 | 0.015 | pers 0.25 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.75 feat=ahead_rel_fast secs=1 thr=1.3 | +2433 / -1504 / -159 / -541 / -538 / -2165 / -712 / -736 | 14251 / 21436 | 29043 / 42883 | -4947 / 45 | 1374 | 0.015 | pers 0.25 |  |

### U7 - entry session 1
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.25 feat=ahead_rel_fast secs=3 thr=1.3 | +5900 / +1754 / +1786 / +414 / -229 / -428 / -560 / -6 | 17017 / 33738 | 47350 / 39568 | -31449 / -56352 | 684 | 0.015 | pers 1.00 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.25 feat=ahead_rel_fast secs=3 thr=1.3 | +5900 / +1754 / +1786 / +414 / -229 / -428 / -560 / -6 | 17017 / 33738 | 47350 / 39568 | -31449 / -56352 | 684 | 0.015 | pers 1.00 |  |

### A7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut NOT MET by any cell: showing lowest-DD cells):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3 | -67 / -955 / -156 / -42 / -171 / -607 / -546 / +4 | 4398 / 12456 | 4987 / 6208 | -5892 / -17012 | 1170 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=3 thr=1.3 | +608 / -1043 / -196 / -164 / -274 / -43 / -451 / +55 | 6736 / 12456 | 6119 / 6208 | -13113 / -17012 | 1170 | 0.015 | pers 0.25 |  |
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +391 / -1538 / -810 / -569 / -385 / -176 / -226 / -210 | 9149 / 12456 | 4467 / 6208 | -17788 / -17012 | 1170 | 0.015 | pers 0.25 |  |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3 | -363 / -1710 / -1001 / -625 / -663 / -1030 / -779 / -66 | 9815 / 12456 | 4318 / 6208 | -15694 / -17012 | 1170 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.5 feat=ahead_rel_fast secs=3 thr=1.3 | +30 / -1785 / -1264 / -653 / -533 / -156 / -143 / -231 | 11666 / 12456 | 5762 / 6208 | -20773 / -17012 | 1170 | 0.015 | pers 0.25 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3 | -67 / -955 / -156 / -42 / -171 / -607 / -546 / +4 | 4398 / 12456 | 4987 / 6208 | -5892 / -17012 | 1170 | 0.015 | pers 0.00 |  |

### H7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3 | +2175 / +851 / +1821 / +240 / +482 / -355 / -563 / -467 | 6579 / 16682 | 9387 / 20667 | 4092 / -36140 | 1097 | 0.015 | pers 1.00 | CAND-DD |
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +997 / +680 / +1019 / +588 / +418 / -16 / -410 / -566 | 10529 / 16682 | 12740 / 20667 | -1270 / -36140 | 1097 | 0.015 | pers 1.00 | CAND-DD |
| H_thick | arm=0.5 feat=ahead_rel_fast secs=3 thr=1.3 | +82 / -1123 / -363 / +403 / +339 / -76 / -380 / -516 | 11990 / 16682 | 16825 / 20667 | -7824 / -36140 | 1097 | 0.015 | pers 0.50 | CAND-DD |
| H_thick | arm=0.75 feat=ahead_rel_fast secs=1 thr=1.3 | +1875 / -382 / -329 / +359 / -5 / -625 / -235 / -401 | 17593 / 16682 | 21279 / 20667 | -11710 / -36140 | 1097 | 0.015 | pers 0.50 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +997 / +680 / +1019 / +588 / +418 / -16 / -410 / -566 | 10529 / 16682 | 12740 / 20667 | -1270 / -36140 | 1097 | 0.015 | pers 1.00 | CAND-DD |

### H7 - entry session 0
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3 | +3014 / +1004 / +1577 / +357 / +640 / +11 / -634 / -416 | 7578 / 16891 | 9870 / 17912 | -2223 / -42912 | 684 | 0.015 | pers 1.00 | CAND-DD |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=3 thr=1.3 | +2787 / +611 / +1110 / +111 / +625 / +189 / -520 / -303 | 10359 / 16891 | 11985 / 17912 | -13894 / -42912 | 684 | 0.015 | pers 1.00 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +2061 / +818 / +844 / +579 / +550 / +235 / -330 / -455 | 11209 / 16891 | 15915 / 17912 | -6274 / -42912 | 684 | 0.015 | pers 1.00 | CAND-DD |

### O7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +1598 / -78 / +10 / +40 / -122 / -33 / -412 / -21 | 4897 / 7489 | 6648 / 5097 | -5339 / -9447 | 509 | 0.015 | pers 0.75 |  |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3 | +1226 / +378 / +481 / +104 / -244 / -81 / -550 / +163 | 5864 / 7489 | 4622 / 5097 | 993 / -9447 | 509 | 0.123 | pers 1.00 | CAND-DD |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=3 thr=1.3 | +1322 / +246 / +83 / +160 / -238 / -189 / -555 / +135 | 6660 / 7489 | 9867 / 5097 | -7536 / -9447 | 509 | 0.123 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=10 thr=1.3 | +442 / +0 / -105 / +45 / -150 / -280 / -166 / +141 | 7489 / 7489 | 4729 / 5097 | -11858 / -9447 | 509 | 1.000 | pers 0.50 |  |
| H_thick | arm=0.5 feat=ahead_rel_fast secs=3 thr=1.3 | +948 / +24 / +42 / +102 / -40 / -312 / -292 / +6 | 7604 / 7489 | 9322 / 5097 | -8401 / -9447 | 509 | 0.185 | pers 1.00 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=3 thr=1.3 | +1322 / +246 / +83 / +160 / -238 / -189 / -555 / +135 | 6660 / 7489 | 9867 / 5097 | -7536 / -9447 | 509 | 0.123 | pers 1.00 |  |

### O7 - entry session 3
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | +1598 / -78 / +10 / +40 / -122 / -33 / -412 / -21 | 4897 / 7489 | 6648 / 5097 | -5339 / -9447 | 509 | 0.015 | pers 0.75 |  |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3 | +1226 / +378 / +481 / +104 / -244 / -81 / -550 / +163 | 5864 / 7489 | 4622 / 5097 | 993 / -9447 | 509 | 0.123 | pers 1.00 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_fast secs=3 thr=1.3 | +1322 / +246 / +83 / +160 / -238 / -189 / -555 / +135 | 6660 / 7489 | 9867 / 5097 | -7536 / -9447 | 509 | 0.123 | pers 1.00 |  |

### ALL - pooled sessions
Drawdown-first top (L6M mean >= never-cut NOT MET by any cell: showing lowest-DD cells):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.5 feat=ahead_rel_fast secs=1 thr=1.3 | -5633 / -12587 / -3775 / -15228 / -10002 / -11148 / -6368 / -1075 | 85640 / 117593 | 115552 / 177634 | 710 / 89449 | 19084 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.5 feat=ahead_rel_fast secs=3 thr=1.3 | -5248 / -11968 / -3342 / -13321 / -10014 / -3839 / -6731 / -1236 | 97687 / 117593 | 118121 / 177634 | 22052 / 89449 | 19084 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.75 feat=ahead_rel_fast secs=1 thr=1.3 | -9455 / -11911 / -4720 / -9131 / -5188 / -4170 / -4678 / -3068 | 107233 / 117593 | 136134 / 177634 | -65726 / 89449 | 19084 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.75 feat=ahead_rel_fast secs=3 thr=1.3 | -2453 / -6598 / -2230 / -6855 / -4068 / -1670 / -4000 / -2792 | 113505 / 117593 | 143817 / 177634 | -42689 / 89449 | 19084 | 0.015 | pers 0.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3 | -20368 / -24798 / -13533 / -19807 / -14448 / -3597 / -16117 / -2120 | 117615 / 117593 | 237832 / 177634 | -97688 / 89449 | 19084 | 0.015 | pers 0.00 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.75 feat=ahead_rel_fast secs=3 thr=1.3 | -2453 / -6598 / -2230 / -6855 / -4068 / -1670 / -4000 / -2792 | 113505 / 117593 | 143817 / 177634 | -42689 / 89449 | 19084 | 0.015 | pers 0.00 |  |
