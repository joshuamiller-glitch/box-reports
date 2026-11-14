# EXH_HI - EX-PHI: profit families H (take) and I (tighten/trail), Stage 1 first order
Generated 2026-11-14 12:29Z. 1077 cells scored (all ledgered, agent PHI). Label: PRE-PROOF (entries not live-matched). Fills: market exit k+1 mid -+0.80, targets nominal, stops at level. Features exist per month from the EX-FEAT store (rows with no feature never fire). Causality test (noise after second 900 on path, high/low/last and all feature panels; 17,926 exits <= 900 s over 128 sampled cells x 2 months, both directions): 0 changed - all kernels use only data <= decision second. Placebos null_ver 2 (cells re-scored after the leak audit). Family p, walk-forward and the live week are in the FINALISTS table at the top (finalists only). Labels in the generic tables below are CAND-DD only (L6M maxDD lower, L6M mean delta >= 0, PRE maxDD <= 1.05 x never-cut); the page label in FINALISTS uses labels_df.

Ranking key: L6M maxDD (weekly, scope), then L6M worst-20, then Ulcer, then Calmar; filter nfire>=20, L6M mean >= never-cut. Delta mean columns are vs never-cut hold-to-bracket (the S1b-COMB live reference deltas are in the ledger columns *_dmean_c).
## Best drawdown-first cell per book (Stage-1 screen, sessions pooled)
K7 profit: the technique that lowers L6M drawdown most is H_gated (arm=0.5 feat=ice_ag_w30 secs=1 thr=4); stack-scope maxDD 9694 vs 20902 never-cut, L6M mean delta +180 USD/wk, PRE maxDD 29792 vs 26707; placebo p 0.138; does not qualify as CANDIDATE-DD.

P7 profit: the technique that lowers L6M drawdown most is H_gated (arm=0.7 feat=tot_rel_fast secs=1 thr=2); stack-scope maxDD 71485 vs 133887 never-cut, L6M mean delta +655 USD/wk, PRE maxDD 107157 vs 109442; placebo p 0.092; CANDIDATE-DD.

M7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.1 feat=tot_rel_slow secs=1 thr=1.3); stack-scope maxDD 14461 vs 44425 never-cut, L6M mean delta +219 USD/wk, PRE maxDD 49060 vs 50321; placebo p 0.046; CANDIDATE-DD.

U7 profit: the technique that lowers L6M drawdown most is H_pcthour (pct=0.3 window=ldn); stack-scope maxDD 8700 vs 21561 never-cut, L6M mean delta +153 USD/wk, PRE maxDD 42735 vs 42226; placebo p 0.031; CANDIDATE-DD.

A7 profit: the technique that lowers L6M drawdown most is H_pcthour (pct=0.4 window=asia); stack-scope maxDD 3268 vs 12461 never-cut, L6M mean delta +427 USD/wk, PRE maxDD 6089 vs 6089; placebo p 0.015; CANDIDATE-DD.

H7 profit: the technique that lowers L6M drawdown most is H_mom (arm=0.25 feat=vel30<= secs=1 thr=0); stack-scope maxDD 5961 vs 15477 never-cut, L6M mean delta +137 USD/wk, PRE maxDD 10161 vs 20667; placebo p 0.015; CANDIDATE-DD.

O7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.1 feat=ahead_rel_slow secs=1 thr=1.3); stack-scope maxDD 2825 vs 7469 never-cut, L6M mean delta +122 USD/wk, PRE maxDD 6213 vs 5102; placebo p 0.015; does not qualify as CANDIDATE-DD.

ALL profit: the technique that lowers L6M drawdown most is I_trail (X=30 arm=0.7); stack-scope maxDD 39556 vs 121381 never-cut, L6M mean delta +4034 USD/wk, PRE maxDD 100321 vs 152455; placebo p 0.015; CANDIDATE-DD.

## Tables

### K7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.5 feat=ice_ag_w30 secs=1 thr=4 | +1176 / -1211 / +978 / +180 / -1173 / -2234 / -1175 / -103 | 9694 / 20902 | 29792 / 26707 | 22808 / 1791 | 4094 | 0.138 | pers 0.75 |  |
| I_bookarm | X=20 arm=0.5 feat=ice_ag_w30 secs=30 thr=3 | -378 / -936 / +1557 / +209 / -826 / -1726 / -483 / -197 | 9899 / 20902 | 20040 / 26707 | 35611 / 1791 | 2239 | 0.046 | pers 0.50 | CAND-DD |
| H_thick | arm=0.5 feat=tot_rel_slow secs=1 thr=2.0 | +128 / -805 / +758 / +2 / -272 / -1807 / -410 / -224 | 10243 / 20902 | 23821 / 26707 | 22354 / 1791 | 1748 | 0.015 | pers 0.75 | CAND-DD |
| H_thick | arm=0.1 feat=tot_rel_slow secs=3 thr=2.0 | +496 / -386 / +663 / +19 / -925 / -1587 / -1108 / +222 | 11309 / 20902 | 33872 / 26707 | 4348 / 1791 | 2049 | 0.200 | pers 0.75 |  |
| I_bookarm | X=5 arm=0.5 feat=ice_ag_w30 secs=10 thr=3 | +2058 / -1026 / +1421 / +232 / -1128 / -2951 / -718 / -318 | 11655 / 20902 | 29861 / 26707 | 20430 / 1791 | 3850 | 0.323 | pers 0.75 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_swing | arm=0.5 buf=0 swing=swag1m | +1385 / +1106 / +2784 / +1276 / -315 / -1177 / -1337 / +9 | 21480 / 20902 | 33516 / 26707 | 20446 / 1791 | 2732 | 0.877 | pers 1.00 |  |

### P7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.7 feat=tot_rel_fast secs=1 thr=2 | +3680 / -4505 / +522 / +655 / +1007 / +4519 / -2499 / -1342 | 71485 / 133887 | 107157 / 109442 | 64089 / -29902 | 1028 | 0.092 | pers 0.75 | CAND-DD |
| NT_retarget | k=8 | +2611 / -2261 / +535 / +1658 / +2001 / -1154 / -358 / -498 | 77449 / 133887 | 111128 / 109442 | 59878 / -29902 | 1857 | 0.031 | pers 0.75 | CAND-DD |
| I_trail | X=15 arm=0.9 | -5654 / -1939 / +757 / +1179 / +135 / -3353 / -2422 / -579 | 78294 / 133887 | 127068 / 109442 | 28267 / -29902 | 646 | 0.015 | pers 0.50 |  |
| H_gated | arm=0.8 feat=tot_rel_fast secs=1 thr=2 | -2786 / -3368 / -173 / +525 / +399 / -2576 / -1154 / -622 | 82220 / 133887 | 110881 / 109442 | 34321 / -29902 | 725 | 0.154 | pers 0.25 | CAND-DD |
| I_trail | X=20 arm=0.9 | -6900 / -2706 / +46 / +961 / +1159 / -6301 / -2499 / -884 | 84167 / 133887 | 125763 / 109442 | 23738 / -29902 | 529 | 0.108 | pers 0.50 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_step | lag=2 step=20 | -4653 / -3269 / +209 / +3816 / +1314 / -1026 / -3374 / -443 | 103981 / 133887 | 101168 / 109442 | 67869 / -29902 | 869 | 0.800 | pers 0.50 | CAND-DD |

### M7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | -72 / -3687 / -1015 / +219 / -180 / -472 / -744 / -1059 | 14461 / 44425 | 49060 / 50321 | -28224 / -68299 | 2923 | 0.046 | pers 0.25 | CAND-DD |
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.5 | +1398 / -2880 / -238 / +299 / -93 / -327 / -728 / -1113 | 19927 / 44425 | 52736 / 50321 | -22948 / -68299 | 2978 | 0.277 | pers 0.50 | CAND-DD |
| I_decay | X0=40 Xmin=5 arm=0.3 rate=2 | -220 / -62 / +655 / +370 / -175 / +137 / -738 / -968 | 21098 / 44425 | 58862 / 50321 | -30842 / -68299 | 2624 | 0.046 | pers 0.50 |  |
| I_decay | X0=30 Xmin=5 arm=0.3 rate=1 | -331 / -282 / +464 / +383 / -85 / +424 / -673 / -847 | 21793 / 44425 | 52180 / 50321 | -24876 / -68299 | 2622 | 0.046 | pers 0.50 | CAND-DD |
| I_decay | X0=40 Xmin=10 arm=0.3 rate=2 | -144 / -289 / +480 / +283 / -178 / +324 / -751 / -886 | 21883 / 44425 | 59500 / 50321 | -32131 / -68299 | 2585 | 0.108 | pers 0.50 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_swing | arm=0.3 buf=2 swing=swag5m | -670 / -375 / +17 / +917 / +395 / -116 / -1062 / -1231 | 29095 / 44425 | 90967 / 50321 | -47053 / -68299 | 1464 | 0.046 | pers 0.50 |  |

### U7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_pcthour | pct=0.3 window=ldn | +4858 / +1091 / +1509 / +153 / +464 / +1037 / -1294 / -919 | 8700 / 21561 | 42735 / 42226 | 3983 / 120 | 769 | 0.031 | pers 1.00 | CAND-DD |
| I_bookarm | X=20 arm=0.25 feat=ice_ag_w30 secs=3 thr=3 | +5854 / +1301 / -86 / +296 / -113 / -1172 / -1779 / -1030 | 10015 / 21561 | 65213 / 42226 | 15471 / 120 | 904 | 0.369 | pers 0.75 |  |
| I_trail | X=25 arm=0.7 | +4988 / -480 / +1950 / +1154 / +899 / -376 / -243 / -608 | 10126 / 21561 | 33544 / 42226 | 37905 / 120 | 387 | 0.062 | pers 0.75 | CAND-DD |
| I_chand | arm=0.7 atr=atr5m k=1 | +5809 / -604 / +1967 / +1036 / +891 / -1280 / -318 / -463 | 10146 / 21561 | 35510 / 42226 | 38825 / 120 | 527 | 0.046 | pers 0.75 | CAND-DD |
| I_lock | X=20 arm=0.7 | +5370 / +74 / +2240 / +1598 / +1119 / -197 / -248 / -532 | 11031 / 21561 | 35820 / 42226 | 45962 / 120 | 342 | 0.400 | pers 1.00 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_lock | X=2 arm=0.7 | +3489 / -584 / +932 / +1634 / +815 / +72 / -348 / -417 | 14576 / 21561 | 28407 / 42226 | 30137 / 120 | 235 | 0.923 | pers 0.75 | CAND-DD |

### A7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_pcthour | pct=0.4 window=asia | +788 / -536 / -75 / +427 / -45 / -810 / -289 / +43 | 3268 / 12461 | 6089 / 6089 | -1783 / -17069 | 680 | 0.015 | pers 0.50 | CAND-DD |
| H_pcthour | pct=0.4 window=all | +788 / -806 / -30 / +374 / +106 / -546 / -183 / +12 | 3268 / 12461 | 4461 / 6089 | -2128 / -17069 | 892 | 0.015 | pers 0.50 | CAND-DD |
| H_gated | arm=0.25 feat=pr_e001_own_w10 secs=1 thr=20 | +422 / -731 / +229 / +328 / +62 / -681 / -246 / -116 | 3723 / 12461 | 4568 / 6089 | 1459 / -17069 | 905 | 0.015 | pers 0.75 | CAND-DD |
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=20 | +574 / -1177 / +165 / +587 / +22 / -968 / -148 / -176 | 3733 / 12461 | 4455 / 6089 | 6397 / -17069 | 754 | 0.015 | pers 0.75 | CAND-DD |
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=10 | +519 / -582 / +173 / +272 / +35 / -694 / -431 / +16 | 3750 / 12461 | 5327 / 6089 | 1017 / -17069 | 939 | 0.015 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=20 | +574 / -1177 / +165 / +587 / +22 / -968 / -148 / -176 | 3733 / 12461 | 4455 / 6089 | 6397 / -17069 | 754 | 0.015 | pers 0.75 | CAND-DD |

### H7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_mom | arm=0.25 feat=vel30<= secs=1 thr=0 | +1418 / +639 / +1607 / +137 / +535 / -570 / -975 / -504 | 5961 / 15477 | 10161 / 20667 | 2693 / -32750 | 847 | 0.015 | pers 1.00 | CAND-DD |
| H_gated | arm=0.4 feat=imb_ag5 secs=1 thr=0.2 | +1263 / +524 / +1252 / +301 / +589 / -348 / -634 / -225 | 5992 / 15477 | 10534 / 20667 | -533 / -32750 | 791 | 0.015 | pers 1.00 | CAND-DD |
| H_mom | arm=0.25 feat=vel30<= secs=1 thr=1 | +1236 / +414 / +1458 / +116 / +583 / -357 / -675 / -477 | 6016 / 15477 | 8137 / 20667 | 2354 / -32750 | 853 | 0.015 | pers 1.00 | CAND-DD |
| H_mom | arm=0.25 feat=vel30<= secs=1 thr=2 | +1250 / +397 / +1417 / +74 / +579 / -383 / -654 / -523 | 6241 / 15477 | 8042 / 20667 | 399 / -32750 | 856 | 0.015 | pers 1.00 | CAND-DD |
| H_gated | arm=0.4 feat=pr_e001_own_w10 secs=1 thr=10 | +1765 / +715 / +1285 / +194 / +631 / +13 / -800 / -86 | 6390 / 15477 | 14345 / 20667 | -1620 / -32750 | 796 | 0.015 | pers 1.00 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_chand | arm=0.7 atr=atr5m k=2 | +1874 / +207 / +699 / +1387 / +860 / +122 / -496 / +14 | 9348 / 15477 | 21288 / 20667 | -2391 / -32750 | 253 | 0.015 | pers 1.00 | CAND-DD |

### O7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.3 | +801 / +192 / +111 / +122 / -388 / +46 / -650 / +47 | 2825 / 7469 | 6213 / 5102 | -258 / -9532 | 367 | 0.015 | pers 1.00 |  |
| H_thick | arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | +1212 / +454 / +267 / +30 / -274 / +141 / -582 / +73 | 3243 / 7469 | 6193 / 5102 | 454 / -9532 | 354 | 0.031 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.5 | +1132 / +404 / +244 / +37 / -339 / +11 / -638 / +68 | 3243 / 7469 | 7956 / 5102 | 276 / -9532 | 354 | 0.031 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=2.0 | +1361 / +363 / +214 / +310 / -234 / -54 / -465 / +122 | 3243 / 7469 | 7322 / 5102 | -1205 / -9532 | 312 | 0.015 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=2.5 | +1056 / +316 / -55 / +18 / -197 / +195 / -264 / +80 | 3426 / 7469 | 9051 / 5102 | -1438 / -9532 | 243 | 0.015 | pers 0.75 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_chand | arm=0.5 atr=atr1m k=1 | +1217 / +525 / +557 / +459 / -31 / -446 / -409 / +24 | 5522 / 7469 | 6816 / 5102 | -5261 / -9532 | 221 | 0.031 | pers 1.00 |  |

### ALL - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_trail | X=30 arm=0.7 | +1706 / +1072 / +7978 / +4034 / +2252 / -954 / -5322 / -430 | 39556 / 121381 | 100321 / 152455 | 180274 / 77580 | 4534 | 0.015 | pers 1.00 | CAND-DD |
| I_lock | X=10 arm=0.7 | -1007 / -1221 / +5479 / +4513 / +2280 / -1383 / -3986 / -402 | 41951 / 121381 | 117200 / 152455 | 184415 / 77580 | 3622 | 0.015 | pers 0.50 | CAND-DD |
| I_trail | X=40 arm=0.7 | +309 / -1625 / +5664 / +3347 / +939 / +1735 / -4779 / -125 | 45635 / 121381 | 119526 / 152455 | 163943 / 77580 | 3683 | 0.015 | pers 0.75 | CAND-DD |
| H_gated | arm=0.5 feat=pr_e001_own_w10 secs=1 thr=35 | -15557 / -4245 / +4473 / +1653 / -3027 / -8993 / -2702 / +602 | 47569 / 121381 | 95799 / 152455 | 173355 / 77580 | 6199 | 0.123 | pers 0.50 | CAND-DD |
| H_gated | arm=0.6 feat=pr_e001_own_w10 secs=1 thr=35 | -7129 / -165 / +5754 / +1473 / -1863 / -6673 / -2930 / -994 | 48072 / 121381 | 137331 / 152455 | 149728 / 77580 | 4908 | 0.015 | pers 0.50 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_lock | X=0 arm=0.6 | -11256 / -9624 / +1333 / +5440 / +471 / -5457 / -5507 / -299 | 73489 / 121381 | 121459 / 152455 | 237076 / 77580 | 4333 | 0.015 | pers 0.50 | CAND-DD |
