**VOID DRAFT - built on a flawed scoring pass (nfire == ntrades); corrected re-score running; do not use**

# EXH_HI - EX-PHI: profit families H (take) and I (tighten/trail), Stage 1 first order
Generated 2026-11-09 04:02Z. 893 cells scored (all ledgered, agent PHI). Label: PRE-PROOF (entries not live-matched). Fills: market exit k+1 mid -+0.80, targets nominal, stops at level. Features exist per month from the EX-FEAT store (rows with no feature never fire). Causality test (noise after second 900 on path, high/low/last and all feature panels; 17,926 exits <= 900 s over 128 sampled cells x 2 months, both directions): 0 changed - all kernels use only data <= decision second. Placebos null_ver 2 (cells re-scored after the leak audit). Family p / WF / live week: not yet computed for these cells (lead runs family_p / walk_forward from the ledger); labels here are CAND-DD (L6M maxDD lower, L6M mean delta >= 0, PRE maxDD <= 1.05 x never-cut) only.

Ranking key: L6M maxDD (weekly, scope), then L6M worst-20, then Ulcer, then Calmar; filter nfire>=20, L6M mean >= never-cut. Delta mean columns are vs never-cut hold-to-bracket (the S1b-COMB live reference deltas are in the ledger columns *_dmean_c).
## Plain sentences
K7 profit: the technique that lowers L6M drawdown most is H_gated (arm=0.5 feat=ice_ag_w30 secs=1 thr=4); stack-scope maxDD 10465 vs 26983 never-cut, L6M mean delta +365 USD/wk, PRE maxDD 29099 vs 30403; placebo p 0.046; CANDIDATE-DD.

P7 profit: the technique that lowers L6M drawdown most is H_gated (arm=0.8 feat=pr_e001_own_w10 secs=1 thr=35); stack-scope maxDD 75303 vs 126710 never-cut, L6M mean delta +697 USD/wk, PRE maxDD 112606 vs 131881; placebo p 0.031; CANDIDATE-DD.

M7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.1 feat=tot_rel_slow secs=1 thr=1.3); stack-scope maxDD 16114 vs 43318 never-cut, L6M mean delta +1058 USD/wk, PRE maxDD 62827 vs 48984; placebo p 0.015; does not qualify as CANDIDATE-DD.

U7 profit: the technique that lowers L6M drawdown most is I_trail (X=30 arm=0.3); stack-scope maxDD 7325 vs 21436 never-cut, L6M mean delta +28 USD/wk, PRE maxDD 47919 vs 42883; placebo p 0.015; does not qualify as CANDIDATE-DD.

A7 profit: the technique that lowers L6M drawdown most is H_gated (arm=0.25 feat=pr_e001_own_w5 secs=1 thr=10); stack-scope maxDD 3743 vs 12456 never-cut, L6M mean delta +39 USD/wk, PRE maxDD 5327 vs 6208; placebo p 0.015; CANDIDATE-DD.

H7 profit: the technique that lowers L6M drawdown most is H_mom (arm=0.25 feat=vel30<= secs=1 thr=1); stack-scope maxDD 6026 vs 16682 never-cut, L6M mean delta +96 USD/wk, PRE maxDD 8089 vs 20667; placebo p 0.015; CANDIDATE-DD.

O7 profit: the technique that lowers L6M drawdown most is H_thick (arm=0.1 feat=ahead_rel_slow secs=1 thr=1.3); stack-scope maxDD 2875 vs 7489 never-cut, L6M mean delta +111 USD/wk, PRE maxDD 6153 vs 5097; placebo p 0.031; does not qualify as CANDIDATE-DD.

ALL profit: the technique that lowers L6M drawdown most is I_trail (X=30 arm=0.7); stack-scope maxDD 47230 vs 117593 never-cut, L6M mean delta +3252 USD/wk, PRE maxDD 108770 vs 177634; placebo p 0.015; CANDIDATE-DD.

## Tables

### K7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.5 feat=ice_ag_w30 secs=1 thr=4 | +1189 / -873 / +1398 / +365 / -827 / -1770 / -1305 / -103 | 10465 / 26983 | 29099 / 30403 | 13512 / -15009 | 6443 | 0.046 | pers 0.75 | CAND-DD |
| H_thick | arm=0.5 feat=tot_rel_slow secs=1 thr=2.0 | -49 / -971 / +672 / +57 / -212 / -1687 / -388 / -224 | 10997 / 26983 | 23591 / 30403 | 6330 / -15009 | 6443 | 0.031 | pers 0.50 | CAND-DD |
| H_thick | arm=0.1 feat=tot_rel_slow secs=3 thr=2.0 | +607 / -668 / +348 / +117 / -680 / -946 / -813 / +222 | 11035 / 26983 | 29498 / 30403 | -8938 / -15009 | 6443 | 0.092 | pers 0.75 | CAND-DD |
| I_chand | arm=0.3 atr=atr5m k=2 | +752 / +1515 / +2591 / +852 / -135 / +1909 / -1369 / +28 | 12340 / 26983 | 46776 / 30403 | 11519 / -15009 | 6443 | 0.031 | pers 1.00 |  |
| H_thick | arm=0.1 feat=tot_rel_fast secs=3 thr=2.5 | -468 / -18 / -515 / +538 / +162 / -1014 / -1061 / +190 | 12682 / 26983 | 25987 / 30403 | -1056 / -15009 | 6443 | 0.723 | pers 0.25 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_lock | X=3 arm=0.5 | +2189 / +881 / +2582 / +1425 / -346 / -1442 / -531 / +229 | 24637 / 26983 | 25165 / 30403 | 28190 / -15009 | 6443 | 0.477 | pers 1.00 | CAND-DD |

### K7 - entry session 0
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.25 feat=tot_rel_slow secs=1 thr=2.0 | -2160 / -988 / +76 / +498 / -52 / -934 / -437 / +411 | 12837 / 23228 | 14903 / 14762 | 11519 / -10100 | 2260 | 0.138 | pers 0.50 | CAND-DD |
| H_thick | arm=0.1 feat=tot_rel_fast secs=3 thr=2.0 | -1524 / -2435 / -1499 / +279 / +160 / -943 / -598 / -84 | 12891 / 23228 | 27395 / 14762 | 7628 / -10100 | 2260 | 0.108 | pers 0.25 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=tot_rel_fast secs=3 thr=2.5 | -416 / -1224 / -604 / +963 / +462 / -704 / -212 / +94 | 15687 / 23228 | 17198 / 14762 | 19240 / -10100 | 2260 | 0.615 | pers 0.25 |  |

### K7 - entry session 1
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.5 | +1908 / +563 / +642 / +1123 / +471 / +507 / -638 / -2 | 4190 / 13569 | 20374 / 16206 | 975 / -31166 | 1515 | 0.015 | pers 1.00 |  |
| H_thick | arm=0.1 feat=tot_rel_fast secs=1 thr=1.3 | +1710 / +650 / +592 / +979 / +369 / +265 / -460 / -27 | 4832 / 13569 | 17196 / 16206 | -3166 / -31166 | 1515 | 0.092 | pers 1.00 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.5 | +1908 / +563 / +642 / +1123 / +471 / +507 / -638 / -2 | 4190 / 13569 | 20374 / 16206 | 975 / -31166 | 1515 | 0.015 | pers 1.00 |  |

### K7 - entry session 3
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=tot_rel_fast secs=1 thr=1.3 | -540 / +411 / +571 / +273 / +427 / -238 / -869 / -619 | 4587 / 20697 | 23561 / 6231 | -9047 / -31954 | 1524 | 0.046 | pers 0.75 |  |
| H_dturn | arm=0.5 feat=dlt_med_w30<= secs=1 thr=-10 | +96 / +620 / +712 / +473 / +128 / -492 / -411 / -318 | 4778 / 20697 | 12089 / 6231 | -11545 / -31954 | 1524 | 0.031 | pers 1.00 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_dturn | arm=0.5 feat=dlt_med_w30<= secs=1 thr=-10 | +96 / +620 / +712 / +473 / +128 / -492 / -411 / -318 | 4778 / 20697 | 12089 / 6231 | -11545 / -31954 | 1524 | 0.031 | pers 1.00 |  |

### K7 - entry session 4
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_pcthour | pct=0.5 window=all | +619 / -41 / +316 / +90 / -420 / -831 / -212 / +337 | 2312 / 6324 | 23228 / 39576 | -1185 / -7330 | 1144 | 0.015 | pers 0.75 | CAND-DD |
| H_pcthour | pct=0.5 window=pm | +619 / -41 / +316 / +90 / -420 / -831 / -212 / +337 | 2312 / 6324 | 23228 / 39576 | -1185 / -7330 | 1144 | 0.015 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_swing | arm=0.5 buf=0 swing=swag1m | +283 / +158 / +442 / +544 / -209 / -628 / -241 / +273 | 4985 / 6324 | 44481 / 39576 | 2133 / -7330 | 1144 | 0.969 | pers 1.00 |  |

### P7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.8 feat=pr_e001_own_w10 secs=1 thr=35 | -8757 / -4418 / -1359 / +697 / -156 / -2288 / -356 / -310 | 75303 / 126710 | 112606 / 131881 | 40493 / -2075 | 4706 | 0.031 | pers 0.25 | CAND-DD |
| H_gated | arm=0.7 feat=tot_rel_fast secs=1 thr=2 | -993 / -1202 / -739 / +284 / +1151 / +2678 / -1711 / -1342 | 75587 / 126710 | 116005 / 131881 | 64376 / -2075 | 4706 | 0.708 | pers 0.25 | CAND-DD |
| I_trail | X=15 arm=0.9 | -7714 / -2973 / -111 / +1063 / -123 / -3212 / -1693 / -579 | 82400 / 126710 | 125379 / 131881 | 43840 / -2075 | 4706 | 0.108 | pers 0.25 | CAND-DD |
| H_thick | arm=0.5 feat=tot_rel_fast secs=30 thr=1.3 | +6011 / -739 / +1622 / +1695 / +1736 / +4577 / -2380 / -463 | 82486 / 126710 | 116156 / 131881 | 61085 / -2075 | 4706 | 0.123 | pers 0.75 | CAND-DD |
| I_swing | arm=0.5 buf=2 swing=swag5m | +6266 / -534 / +1553 / +3085 / -703 / -717 / -3927 / -543 | 83696 / 126710 | 125783 / 131881 | 35703 / -2075 | 4706 | 0.431 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_step | lag=2 step=20 | -7100 / -4447 / -92 / +3433 / +1092 / -1051 / -3032 / -443 | 102000 / 126710 | 129132 / 131881 | 76337 / -2075 | 4706 | 0.615 | pers 0.25 | CAND-DD |

### P7 - entry session 0
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_trail | X=25 arm=0.8 | +1249 / +1383 / +768 / +457 / +315 / -1236 / -1178 / +158 | 74617 / 106637 | 76691 / 78845 | 62235 / 49424 | 2125 | 0.046 | pers 1.00 | CAND-DD |
| H_gated | arm=0.8 feat=pr_e001_own_w5 secs=1 thr=20 | -6521 / -1085 / -246 / +2 / -918 / -4210 / -933 / -47 | 79017 / 106637 | 81792 / 78845 | 70483 / 49424 | 2125 | 0.062 | pers 0.25 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_swing | arm=0.5 buf=5 swing=swag5m | +6143 / +6744 / +3987 / +2534 / +775 / +759 / -1724 / +57 | 108210 / 106637 | 78515 / 78845 | 88241 / 49424 | 2125 | 0.538 | pers 1.00 |  |

### P7 - entry session 1
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.6 feat=tot_rel_fast secs=1 thr=2 | +125 / -2716 / -54 / +205 / +44 / -1254 / -592 / -567 | 35782 / 44287 | 147525 / 160840 | -21424 / -16876 | 1437 | 0.646 | pers 0.50 | CAND-DD |
| H_thick | arm=0.1 feat=tot_rel_slow secs=30 thr=1.3 | +48 / -3327 / -412 / +194 / +24 / +3901 / -111 / -1630 | 40964 / 44287 | 148248 / 160840 | -14469 / -16876 | 1437 | 1.000 | pers 0.50 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_swing | arm=0.5 buf=0 swing=swag1m | -2195 / -7053 / -4573 / +705 / -707 / -3982 / +1037 / -1823 | 43695 / 44287 | 108322 / 160840 | -27979 / -16876 | 1437 | 0.431 | pers 0.25 | CAND-DD |

### P7 - entry session 3
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_step | lag=1 step=5 | +7994 / -2868 / +929 / +2906 / +987 / -1881 / -1498 / -925 | 10816 / 103128 | 7870 / 75038 | 2128 / -164165 | 1144 | 0.015 | pers 0.75 | CAND-DD |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=1.3 | +9636 / -2551 / +1504 / +3156 / +1025 / -1280 / -2851 / -1053 | 15504 / 103128 | 31542 / 75038 | -16296 / -164165 | 1144 | 0.015 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_lock | X=0 arm=0.3 | +1991 / +3373 / +5355 / +3823 / +1513 / -200 / -1670 / +468 | 46389 / 103128 | 45766 / 75038 | -93766 / -164165 | 1144 | 0.046 | pers 1.00 | CAND-DD |

### M7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | -65 / -3632 / -676 / +1058 / +88 / -1326 / -394 / -1059 | 16114 / 43318 | 62827 / 48984 | -30554 / -68462 | 3777 | 0.015 | pers 0.25 |  |
| H_thick | arm=0.1 feat=tot_rel_slow secs=3 thr=1.3 | -108 / -3016 / -468 / +1146 / +391 / -1304 / -78 / -1254 | 19558 / 43318 | 41987 / 48984 | -30085 / -68462 | 3777 | 0.077 | pers 0.25 | CAND-DD |
| H_thick | arm=0.1 feat=tot_rel_fast secs=1 thr=1.5 | -186 / -2845 / -414 / +785 / -62 / -789 / -260 / -913 | 21574 / 43318 | 50569 / 48984 | -39624 / -68462 | 3777 | 0.123 | pers 0.25 | CAND-DD |
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.5 | +1688 / -3004 / +11 / +90 / -335 / -1063 / -442 / -1113 | 21723 / 43318 | 65275 / 48984 | -23335 / -68462 | 3777 | 0.077 | pers 0.75 |  |
| H_pcthour | pct=0.3 window=ldn | -1091 / -1913 / -768 / +549 / +80 / -1559 / +348 / -126 | 22791 / 43318 | 23616 / 48984 | -34570 / -68462 | 3777 | 0.031 | pers 0.25 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=tot_rel_slow secs=3 thr=1.3 | -108 / -3016 / -468 / +1146 / +391 / -1304 / -78 / -1254 | 19558 / 43318 | 41987 / 48984 | -30085 / -68462 | 3777 | 0.077 | pers 0.25 | CAND-DD |

### M7 - entry session 1
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_tip | pct=0 secs=60 | +353 / -2953 / -221 / +337 / +84 / -1267 / +594 / -33 | 5487 / 34745 | 38717 / 70941 | -6867 / -61665 | 2254 | 0.015 | pers 0.50 | CAND-DD |
| H_thick | arm=0.1 feat=tot_rel_fast secs=1 thr=1.3 | +1016 / -2107 / +241 / +708 / +109 / -2219 / +595 / -179 | 7894 / 34745 | 33102 / 70941 | -9988 / -61665 | 2254 | 0.015 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.4 feat=ice_ag_w30 secs=1 thr=4 | -472 / +426 / +948 / +914 / +659 / +1220 / -43 / -510 | 22289 / 34745 | 66425 / 70941 | -37781 / -61665 | 2254 | 0.092 | pers 0.75 | CAND-DD |

### M7 - entry session 3
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_chand | arm=0.7 atr=atr5m k=1 | +801 / +195 / +246 / +278 / +40 / +179 / -190 / -114 | 9416 / 12246 | 10377 / 7533 | -16422 / -18056 | 1523 | 0.615 | pers 1.00 |  |
| I_chand | arm=0.3 atr=atr5m k=1.5 | +896 / +163 / +260 / +254 / -83 / +81 / -387 / -216 | 9569 / 12246 | 8098 / 7533 | -14656 / -18056 | 1523 | 0.108 | pers 1.00 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_chand | arm=0.5 atr=atr1m k=4 | +1005 / +387 / +551 / +349 / +102 / +338 / -374 / +92 | 11474 / 12246 | 8541 / 7533 | -14356 / -18056 | 1523 | 0.308 | pers 1.00 |  |

### U7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_trail | X=30 arm=0.3 | +4392 / -1352 / +595 / +28 / +173 / -1112 / -981 / -1051 | 7325 / 21436 | 47919 / 42883 | 33498 / 45 | 1374 | 0.015 | pers 0.75 |  |
| H_pcthour | pct=0.3 window=ldn | +4824 / +1085 / +1758 / +235 / +681 / +2024 / -1216 / -919 | 8705 / 21436 | 43895 / 42883 | 3967 / 45 | 1374 | 0.046 | pers 1.00 | CAND-DD |
| I_trail | X=25 arm=0.7 | +4993 / -349 / +2036 / +1461 / +805 / -730 / -226 / -608 | 9981 / 21436 | 33544 / 42883 | 39206 / 45 | 1374 | 0.077 | pers 0.75 | CAND-DD |
| I_bookarm | X=20 arm=0.25 feat=ice_ag_w30 secs=3 thr=3 | +5868 / +1524 / +69 / +376 / -34 / -710 / -1511 / -1030 | 9985 / 21436 | 67745 / 42883 | 16433 / 45 | 1374 | 0.277 | pers 1.00 |  |
| I_chand | arm=0.7 atr=atr5m k=1 | +5814 / -287 / +2177 / +1269 / +813 / -1399 / -89 / -463 | 10001 / 21436 | 32763 / 42883 | 39938 / 45 | 1374 | 0.046 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_lock | X=0 arm=0.7 | +3299 / -90 / +1198 / +1725 / +670 / -527 / -333 / -396 | 14881 / 21436 | 29397 / 42883 | 29925 / 45 | 1374 | 1.000 | pers 0.75 | CAND-DD |

### U7 - entry session 0
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_lock | X=0 arm=0.3 | +1514 / -1778 / -1301 / +169 / +2 / -1527 / -791 / -805 | 2637 / 9836 | 36298 / 31041 | 38624 / 10132 | 690 | 0.015 | pers 0.50 |  |
| I_chand | arm=0.3 atr=atr5m k=2 | +1857 / +398 / -190 / +689 / +174 / -1071 / -736 / -992 | 2727 / 9836 | 28225 / 31041 | 56677 / 10132 | 690 | 0.062 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_trail | X=30 arm=0.7 | +3084 / +153 / +1685 / +1299 / +678 / -596 / -202 / -691 | 8631 / 9836 | 30588 / 31041 | 53881 / 10132 | 690 | 0.554 | pers 1.00 | CAND-DD |

### U7 - entry session 1
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_slow secs=3 thr=1.5 | +5638 / +951 / +1829 / +413 / -327 / -358 / -557 / -1 | 13487 / 33738 | 67082 / 39568 | -34170 / -56352 | 684 | 0.092 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=3 thr=1.5 | +5390 / +899 / +1687 / +354 / -194 / -647 / -363 / +91 | 13928 / 33738 | 48242 / 39568 | -31786 / -56352 | 684 | 0.031 | pers 1.00 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=tot_rel_slow secs=3 thr=2.0 | +3867 / +484 / +1898 / +1472 / +444 / -2185 / -232 / +14 | 21017 / 33738 | 43839 / 39568 | -19350 / -56352 | 684 | 0.877 | pers 1.00 |  |

### A7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=10 | -85 / -876 / -167 / +39 / -428 / -671 / -420 / +16 | 3743 / 12456 | 5327 / 6208 | -3815 / -17012 | 1170 | 0.015 | pers 0.25 | CAND-DD |
| H_pcthour | pct=0.3 window=all | +479 / -660 / +238 / +311 / -258 / -617 / -423 / +169 | 3963 / 12456 | 3612 / 6208 | 1639 / -17012 | 1170 | 0.015 | pers 0.75 | CAND-DD |
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=20 | -44 / -1360 / -217 / +324 / -54 / -833 / -201 / -176 | 4185 / 12456 | 5570 / 6208 | 589 / -17012 | 1170 | 0.015 | pers 0.25 | CAND-DD |
| H_pcthour | pct=0.4 window=all | +194 / -1093 / -502 / +117 / -336 / -393 / -175 / +12 | 4308 / 12456 | 4461 / 6208 | -7488 / -17012 | 1170 | 0.015 | pers 0.50 | CAND-DD |
| H_gated | arm=0.25 feat=pr_e001_own_w10 secs=1 thr=20 | -192 / -1030 / -94 / +67 / -381 / -629 / -284 / -116 | 4334 / 12456 | 4568 / 6208 | -2985 / -17012 | 1170 | 0.015 | pers 0.25 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=20 | -44 / -1360 / -217 / +324 / -54 / -833 / -201 / -176 | 4185 / 12456 | 5570 / 6208 | 589 / -17012 | 1170 | 0.015 | pers 0.25 | CAND-DD |

### A7 - entry session 0
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=10 | -85 / -876 / -167 / +39 / -428 / -671 / -420 / +16 | 3743 / 12456 | 5327 / 6208 | -3815 / -17012 | 1170 | 0.015 | pers 0.25 | CAND-DD |
| H_pcthour | pct=0.3 window=all | +479 / -660 / +238 / +311 / -258 / -617 / -423 / +169 | 3963 / 12456 | 3612 / 6208 | 1639 / -17012 | 1170 | 0.015 | pers 0.75 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_gated | arm=0.25 feat=pr_e001_own_w5 secs=1 thr=20 | -44 / -1360 / -217 / +324 / -54 / -833 / -201 / -176 | 4185 / 12456 | 5570 / 6208 | 589 / -17012 | 1170 | 0.015 | pers 0.25 | CAND-DD |

### H7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_mom | arm=0.25 feat=vel30<= secs=1 thr=1 | +1265 / +442 / +1596 / +96 / +477 / -377 / -574 / -477 | 6026 / 16682 | 8089 / 20667 | -467 / -36140 | 1097 | 0.015 | pers 1.00 | CAND-DD |
| H_mom | arm=0.25 feat=vel30<= secs=1 thr=2 | +1212 / +383 / +1529 / +124 / +506 / -383 / -534 / -523 | 6206 / 16682 | 7967 / 20667 | -1244 / -36140 | 1097 | 0.015 | pers 1.00 | CAND-DD |
| H_gated | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.5 | +2523 / +1088 / +2016 / +432 / +581 / -206 / -517 / -349 | 6546 / 16682 | 9332 / 20667 | 6057 / -36140 | 1097 | 0.015 | pers 1.00 | CAND-DD |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.5 | +2523 / +1088 / +2016 / +432 / +581 / -206 / -517 / -349 | 6546 / 16682 | 9332 / 20667 | 6057 / -36140 | 1097 | 0.015 | pers 1.00 | CAND-DD |
| H_thick | arm=0.25 feat=ahead_rel_fast secs=1 thr=1.3 | +2175 / +851 / +1821 / +240 / +482 / -355 / -563 / -467 | 6579 / 16682 | 9387 / 20667 | 4092 / -36140 | 1097 | 0.015 | pers 1.00 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_chand | arm=0.7 atr=atr5m k=2 | +1869 / +208 / +700 / +1386 / +658 / +121 / -386 / +14 | 10553 / 16682 | 21288 / 20667 | -5806 / -36140 | 1097 | 0.015 | pers 1.00 | CAND-DD |

### H7 - entry session 0
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_mom | arm=0.25 feat=vel30_chg15<= secs=1 thr=-1 | +2433 / +705 / +1377 / +287 / +611 / -102 / -597 / -345 | 7198 / 16891 | 9795 / 17912 | -5906 / -42912 | 684 | 0.031 | pers 1.00 | CAND-DD |
| H_mom | arm=0.25 feat=vel30_chg15<= secs=1 thr=-2 | +2440 / +735 / +1404 / +331 / +641 / -102 / -528 / -286 | 7271 / 16891 | 9160 / 17912 | -5331 / -42912 | 684 | 0.015 | pers 1.00 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_lock | X=2 arm=0.7 | +1266 / -138 / +409 / +1314 / +653 / +641 / -214 / +40 | 9529 / 16891 | 17912 / 17912 | -12596 / -42912 | 684 | 0.785 | pers 0.75 | CAND-DD |

### H7 - entry session 3
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_mom | arm=0.5 feat=vel30_chg15<= secs=1 thr=-4 | -790 / -352 / +108 / +46 / -44 / -216 / -141 / -181 | 2159 / 3747 | 29831 / 23673 | 2624 / -5368 | 413 | 0.015 | pers 0.50 |  |
| H_dturn | arm=0.5 feat=dlt_med_w10<= secs=1 thr=-1 | -861 / -416 / +46 / +1 / -54 / -210 / -83 / -243 | 2179 / 3747 | 28145 / 23673 | 1669 / -5368 | 413 | 0.015 | pers 0.50 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_chand | arm=0.3 atr=atr5m k=1.5 | +47 / -69 / +271 / +164 / +81 / +107 / +25 / -59 | 4490 / 3747 | 25915 / 23673 | -4704 / -5368 | 413 | 0.800 | pers 0.75 |  |

### O7 - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.3 | +746 / +156 / +89 / +111 / -411 / +47 / -615 / +47 | 2875 / 7489 | 6153 / 5097 | -448 / -9447 | 509 | 0.031 | pers 1.00 |  |
| H_thick | arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | +1212 / +452 / +268 / +30 / -291 / +142 / -547 / +73 | 3248 / 7489 | 6158 / 5097 | 529 / -9447 | 509 | 0.031 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.5 | +1132 / +396 / +240 / +35 / -358 / +12 / -603 / +68 | 3248 / 7489 | 7906 / 5097 | 339 / -9447 | 509 | 0.046 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=2.0 | +1361 / +365 / +217 / +311 / -252 / -53 / -430 / +122 | 3248 / 7489 | 7257 / 5097 | -1155 / -9447 | 509 | 0.015 | pers 1.00 |  |
| H_thick | arm=0.1 feat=ahead_rel_fast secs=1 thr=2.5 | +1056 / +316 / -53 / +19 / -185 / +195 / -229 / +80 | 3431 / 7489 | 8986 / 5097 | -1363 / -9447 | 509 | 0.015 | pers 0.75 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_chand | arm=0.5 atr=atr1m k=1 | +1217 / +374 / +456 / +410 / -32 / -345 / -375 / +24 | 6701 / 7489 | 6826 / 5097 | -6435 / -9447 | 509 | 0.154 | pers 1.00 |  |

### O7 - entry session 3
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| H_thick | arm=0.1 feat=ahead_rel_slow secs=1 thr=1.3 | +746 / +156 / +89 / +111 / -411 / +47 / -615 / +47 | 2875 / 7489 | 6153 / 5097 | -448 / -9447 | 509 | 0.031 | pers 1.00 |  |
| H_thick | arm=0.1 feat=tot_rel_slow secs=1 thr=1.3 | +1212 / +452 / +268 / +30 / -291 / +142 / -547 / +73 | 3248 / 7489 | 6158 / 5097 | 529 / -9447 | 509 | 0.031 | pers 1.00 |  |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_chand | arm=0.5 atr=atr1m k=1 | +1217 / +374 / +456 / +410 / -32 / -345 / -375 / +24 | 6701 / 7489 | 6826 / 5097 | -6435 / -9447 | 509 | 0.154 | pers 1.00 |  |

### ALL - pooled sessions
Drawdown-first top (L6M mean >= never-cut):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_trail | X=30 arm=0.7 | -1415 / -718 / +7350 / +3252 / +1606 / -1407 / -4275 / -430 | 47230 / 117593 | 108770 / 177634 | 188622 / 89449 | 19084 | 0.015 | pers 0.50 | CAND-DD |
| I_lock | X=10 arm=0.7 | -2699 / -2357 / +5568 / +3824 / +1634 / -2430 / -3150 / -402 | 49295 / 117593 | 125031 / 177634 | 192269 / 89449 | 19084 | 0.015 | pers 0.50 | CAND-DD |
| I_trail | X=40 arm=0.7 | -2766 / -3168 / +5263 / +2748 / +502 / -3668 / -5094 / -125 | 51072 / 117593 | 127897 / 177634 | 154682 / 89449 | 19084 | 0.015 | pers 0.50 | CAND-DD |
| I_lock | X=15 arm=0.7 | -1757 / -1405 / +5978 / +3240 / +1572 / -1497 / -3269 / +283 | 53488 / 117593 | 116479 / 177634 | 176613 / 89449 | 19084 | 0.015 | pers 0.50 | CAND-DD |
| I_bookarm | X=20 arm=0.5 feat=ice_ag_w30 secs=30 thr=3 | -2914 / -3384 / +6934 / +1293 / -1272 / -6572 / -4261 / -2434 | 54082 / 117593 | 99253 / 177634 | 148713 / 89449 | 19084 | 0.015 | pers 0.50 | CAND-DD |
Best mean (for reference):
| technique | params | delta mean vs never-cut L1M/L2M/L3M/L6M/HOLD/MID/PRE/X' (USD/wk) | maxDD L6M with/without | maxDD PRE with/without | worst-20 L6M with/without | nfire | placebo p | persistence | label |
|---|---|---|---|---|---|---|---|---|---|
| I_lock | X=3 arm=0.6 | -14566 / -8829 / +3406 / +5954 / +958 / -4406 / -5049 / -1762 | 55605 / 117593 | 132167 / 177634 | 240091 / 89449 | 19084 | 0.015 | pers 0.50 | CAND-DD |
