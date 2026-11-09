# DS3_TH_EXHAUST - every exit technique, both sides, drawdown first (auto-generated 2026-11-09 10:57Z)
**Universe U2 = full S1b tick-close never-cut (43 months) + the u5 live-week entries; this page shows U2 cells only.** The S1b-COMB live reference row is unchanged (S1b).

**Reading guide.** ENTER = passes every gate (recents, tolerant older windows, drawdown not worse in L6M and PRE, delta above MDE, placebo p <= .10, family p <= .10, walk-forward ok, not FAILS-LIVE-WEEK). CANDIDATE-DD = lowers L6M maxDD at equal or better L6M mean and PRE maxDD within +5% (even inside MDE); LEAD = L6M mean and drawdown not worse with >60% of L1M..L6M windows positive. FAILS-LIVE-WEEK = the held-out live-week delta is below -1 MDE-week of that scope (never ENTER). Sub-flags in the label cell: rec-ok/rec-FAIL (no L1M..L6M delta below -1 MDE-week), wf-ok/wf-FAIL, plc-ok/plc-FAIL (placebo p <= .10), exposure (fires on more than 50% of trades = exposure shrink). **ENTER cells on this page: 0.**

## Box-confirmation items for v1.5 fidelity
v1.5 NOT VERIFIED: the v1.5 source is absent from the box (requested from the user); no match with v1.5 is claimed for any item. What follows is the treatment of the state build used by every number on this page.
1. A level present at s-1 and absent at s: cancelled size = max(0, size(s-1) - size(s) - traded at that price in (s-1, s]); absent at s counts as size 0 when the price is inside or better than the visible top-10 range of row s; it is IGNORED when it fell outside the visible top 10 (worse than the 10th level of a full 10-level book; about 64 M levels per side over the history, ~0.8 per side per second, mostly price moves). Box treatment (state build) + v1.5 NOT VERIFIED.
2. Seconds with no feed event: one row per session second, book carried forward, zero cancels and zero prints. Box treatment (state build) + v1.5 NOT VERIFIED.
3. newMae tie rule: a tie with the running adverse extreme counts as new (DS3_TH_STATE section 2). Box treatment (state build) + v1.5 NOT VERIFIED.
Null audit: placebo version 2 (causal, leak-tested; EXH_API section 9). Placebo p of cells scored with the version-1 (leaky) null were recomputed or set to NaN (shown as nan, treated as 1.0 by the labels).
Evidence level: stage S1 rows are first-order (each trade alone on its stored path, bracket exits at level, 1-s decision latency, 0.80 pt market-exit cost); rows marked S2 went through the replica engine cascade (re-entries, locks, stack gates). Entry match to the live week is below .85, so the page is PRE-PROOF.
Label: state base S1b universe (never-cut hold-to-bracket path; months not yet rebuilt are S1 timer-close, flagged src in the universe), entry match to the live week not yet >= .85 unless stated: PRE-PROOF. Windows as of 2026-11-09 (data to 2026-11-05). USD per ISO week at live lots net of 4.84/contract; delta = rule minus never-cut with the carrying week dropped; "w/wo" = with the rule / without (never-cut). LIVE REFERENCE ROW = S1b-COMB (live week from the u5 replica).
QUARANTINE: 0 cells of agent PHI from the flawed first scoring pass (nfire == ntrades, leg 2 fed back into a new Outcome) are excluded from every table, nulls and the family max-stat; they stay on disk. H/I (take / trail) section: corrected cells in the ledger 893 of 893 expected so far.
Cells scored: 17046; families: ['A', 'A_pulled', 'B_book', 'B_book/C_flow', 'C_flow', 'D', 'E', 'F', 'G', 'J_scale', 'K_target', 'L_cond', 'L_cross', 'L_learned', 'PHI_H', 'PHI_H/I', 'PHI_I', 'X_cross']. Labels: {'no': 88905, 'CANDIDATE-DD': 25720, 'LEAD': 6891, 'CANDIDATE-DD FAILS-LIVE-WEEK': 4391, 'LEAD FAILS-LIVE-WEEK': 1572, 'S2-partial (older windows pending)': 40}

## ALL
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL never-cut level | 35,468 | 67,950 | 37,850 | 31,832 | 16,868 | 12,409 | 14,153 | 2,398 | 121,381 | 152,455 | 77,580 |
| ALL LIVE REF S1b-COMB level | 11,588 | 45,231 | 24,973 | 28,018 | 16,943 | 18,454 | 12,266 | 1,937 | 82,873 | 144,002 | 190,560 |

### ALL loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback@after30 | {"X": 20, "ctx": "after30", "pb": 40} | -29,431 | -15,996 | -7,144 | 1,877 | -4,042 | -7,476 | -10,031 | -147 | 54,622 / 121,381 | 100,443 / 152,455 | 179,120 / 77,580 | 10,642 | 0.12 | 1.00 / 0.96 | -125,733 | -1,645 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 20, "blk": "C", "cancels" | -4,054 | -11,920 | -7,011 | 1,446 | 172 | 1,824 | -5,195 | 1,484 | 61,695 / 121,381 | 83,161 / 152,455 | 149,247 / 77,580 | 8,239 | 0.03 | 1.00 / 0.96 | -970,636 | -8,894 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_dlt_med_w10 | {"arm": 25.0, "arm_kind": "abs", "dir": -1, "feat": "dlt_med | 3,607 | 8,880 | 735 | 6,103 | -182 | -4,866 | -4,549 | 1,354 | 62,188 / 121,381 | 81,956 / 152,455 | 208,614 / 77,580 | 6,892 | 0.11 | 1.00 / 0.95 | -188,044 | 2,744 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| D4_eff@blk_both_30 | {"X": 35, "ctx": "blk_both_30", "thr": 0.3, "w": 60} | -12,105 | -10,424 | -6,453 | 1,304 | -678 | -1,475 | -8,918 | 788 | 62,613 / 121,381 | 120,569 / 152,455 | 136,651 / 77,580 | 9,632 | 0.02 | 1.00 / 0.96 | -57,654 | -8,586 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_dlt_med_w60 | {"arm": 0.3, "arm_kind": "pct", "dir": -1, "feat": "dlt_med_ | -6,116 | -6,312 | 1,416 | 2,233 | -3,067 | -3,657 | -7,592 | -1,123 | 62,740 / 121,381 | 125,684 / 152,455 | 167,175 / 77,580 | 7,954 | 0.02 | 1.00 / 0.95 | -331,761 | -13,584 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### ALL profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 1,664 | 2,177 | 4,874 | 3,824 | 2,515 | 264 | -1,426 | -501 | 55,296 / 121,381 | 117,149 / 152,455 | 250,937 / 77,580 | 1,789 | 0.02 | 1.00 / 0.95 | -216,598 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 1,905 | 2,072 | 5,258 | 3,836 | 2,563 | 166 | -1,514 | -574 | 56,444 / 121,381 | 115,335 / 152,455 | 251,176 / 77,580 | 1,789 | 0.04 | 1.00 / 0.95 | -216,598 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -2,493 | -1,781 | 2,031 | 1,299 | -1,659 | -1,045 | -5,749 | -1,200 | 57,492 / 121,381 | 120,670 / 152,455 | 258,667 / 77,580 | 3,720 | 0.04 | 1.00 / 0.95 | -216,598 | -3,806 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -1,935 | -1,568 | 2,331 | 1,535 | -1,548 | -898 | -5,731 | -1,301 | 59,365 / 121,381 | 119,860 / 152,455 | 265,450 / 77,580 | 3,720 | 0.04 | 1.00 / 0.95 | -216,598 | -3,806 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 40}, "base_tech":  | 8,004 | -6,918 | -1,619 | 3,134 | 2,579 | 798 | -1,902 | -615 | 69,132 / 121,381 | 115,652 / 152,455 | 219,670 / 77,580 | 1,664 | 0.04 | 1.00 / 0.95 | -216,598 | -5,288 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### ALL both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -39,428 | -11,483 | -416 | -8,838 | -11,557 | -12,911 | -11,867 | -3,167 | 43,078 / 121,381 | 225,516 / 152,455 | 12,283 / 77,580 | 12,235 | 0.82 | 1.00 / 0.88 | 0 |  | S1 | no |
| CROSS[966d0f8e1e9e+01618af6c2a8] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "01618af6c2 | -38,113 | -12,222 | -1,688 | -11,171 | -12,499 | -13,464 | -13,874 | -4,222 | 43,510 / 121,381 | 282,758 / 152,455 | -41,223 / 77,580 | 13,472 | 0.52 | 1.00 / 0.88 |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -32,560 | -20,213 | -10,879 | -9,397 | -11,899 | -9,772 | -10,393 | -8 | 77,173 / 121,381 | 151,329 / 152,455 | -4,977 / 77,580 | 10,882 | 0.45 | 1.00 / 0.95 | 0 |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -30,130 | -35,888 | -28,786 | -20,418 | -24,218 | -17,361 | -20,761 | -5,068 | 232,660 / 121,381 | 546,408 / 152,455 | -253,661 / 77,580 | 14,101 | 1.00 | 1.00 / 1.00 | 0 |  | S1 | no |
| CROSS[cd4451a22198+87cd2ee2381f] | {"book": "K7", "loss": "cd4451a22198", "profit": "87cd2ee238 | -59,010 | -32,978 | -25,254 | -36,190 | -32,233 | -22,784 | -22,355 | -9,661 | 406,212 / 121,381 | 673,184 / 152,455 | -526,357 / 77,580 | 13,276 | 1.00 | 1.00 / 0.88 | 0 |  | S1 | no |

## K7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 never-cut level | 4,952 | 8,594 | 3,229 | 4,245 | 2,469 | 1,911 | 2,803 | -80 | 20,902 | 26,707 | 1,791 |
| K7 LIVE REF S1b-COMB level | 7,873 | 8,450 | 3,436 | 3,530 | 2,241 | 3,740 | 2,616 | -164 | 41,849 | 23,073 | -20,339 |

### K7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_adv_best_move | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best | 909 | 2,784 | 3,589 | 1,123 | -23 | 1,148 | -1,202 | 9 | 8,636 / 20,902 | 23,900 / 26,707 | 28,728 / 1,791 | 3,051 | 0.05 | 1.00 / 1.00 | -107,558 | 126 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_tot_rel_base | {"arm": 40.0, "arm_kind": "abs", "dir": -1, "feat": "tot_rel | 920 | 1,852 | 2,089 | 839 | -207 | -14 | -425 | -99 | 9,396 / 20,902 | 25,381 / 26,707 | 39,604 / 1,791 | 2,191 | 0.03 | 1.00 / 1.00 | -102,892 | 879 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_imb_ag10 | {"arm": 0.45, "arm_kind": "pct", "dir": 1, "feat": "imb_ag10 | -302 | 1,268 | 1,522 | 683 | 120 | 32 | -275 | 228 | 9,560 / 20,902 | 21,646 / 26,707 | 18,437 / 1,791 | 1,148 | 0.02 | 1.00 / 1.00 | -23,175 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_dlt_med_w60 | {"arm": 15.0, "arm_kind": "abs", "dir": -1, "feat": "dlt_med | 2,476 | 2,037 | 2,834 | 683 | 310 | 1,694 | -1,484 | -187 | 9,563 / 20,902 | 17,229 / 26,707 | 23,178 / 1,791 | 3,487 | 0.38 | 1.00 / 1.00 | -74,266 | -1,734 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| LBC_dtot8_w5 | {"arm": 30.0, "arm_kind": "abs", "dir": -1, "feat": "dtot8_w | 1,834 | 1,339 | 1,765 | 1,322 | 432 | -95 | -630 | -105 | 9,940 / 20,902 | 22,345 / 26,707 | 33,119 / 1,791 | 1,869 | 0.85 | 1.00 / 1.00 | -52,452 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

### K7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, " | 1,717 | 728 | 1,963 | 666 | -5 | 100 | -673 | 390 | 8,893 / 20,902 | 23,892 / 26,707 | 16,614 / 1,791 | 636 | 0.02 | 1.00 / 0.94 | -41,710 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "trail", "x": 10} | 2,081 | -874 | 1,144 | 277 | -389 | -1,516 | -399 | 463 | 9,147 / 20,902 | 17,406 / 26,707 | 39,575 / 1,791 | 969 | 0.04 | 1.00 / 1.00 | -34,760 | -40 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 5} | 2,286 | -761 | 1,258 | 270 | -409 | -1,718 | -412 | 480 | 9,389 / 20,902 | 17,644 / 26,707 | 40,236 / 1,791 | 689 | 0.04 | 1.00 / 1.00 | -46,439 | 56 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 10} | 2,146 | -846 | 1,106 | 205 | -427 | -1,502 | -395 | 479 | 9,411 / 20,902 | 18,094 / 26,707 | 37,916 / 1,791 | 689 | 0.04 | 1.00 / 1.00 | -46,439 | -472 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 1.25, "p": 0.5, "rest": "trail", "x": 10} | 2,235 | -811 | 1,130 | 204 | -422 | -1,556 | -399 | 488 | 9,411 / 20,902 | 18,094 / 26,707 | 37,734 / 1,791 | 969 | 0.04 | 1.00 / 1.00 | -34,760 | -472 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### K7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -3,325 | -599 | 1,945 | -1,115 | -1,464 | 399 | -1,816 | -323 | 8,298 / 20,902 | 43,335 / 26,707 | 4,693 / 1,791 | 4,112 | 0.18 | 1.00 / 0.44 | -2,336 |  | S1 | no |
| CROSS[cd4451a22198+87cd2ee2381f] | {"book": "K7", "loss": "cd4451a22198", "profit": "87cd2ee238 | -5,570 | -963 | 1,904 | -1,755 | -2,174 | -323 | -2,709 | -663 | 12,829 / 20,902 | 52,166 / 26,707 | -13,392 / 1,791 | 4,084 | 0.42 | 1.00 / 0.73 | -10,676 |  | S1 | no |
| CROSS[966d0f8e1e9e+01618af6c2a8] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "01618af6c2 | -3,900 | -1,220 | 1,106 | -2,168 | -2,351 | -580 | -2,370 | -551 | 14,494 / 20,902 | 52,848 / 26,707 | -17,117 / 1,791 | 4,633 | 0.30 | 1.00 / 0.50 |  |  | S1 | no |
| CROSS[e0fb6a9abc57+8e7c342b397d] | {"book": "M7", "loss": "e0fb6a9abc57", "profit": "8e7c342b39 | -4,163 | -4,573 | -1,407 | -4,158 | -3,263 | -336 | -3,580 | -1,455 | 31,237 / 20,902 | 69,931 / 26,707 | -44,587 / 1,791 | 5,527 | 1.00 | 1.00 / 0.59 | -29,780 |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | -4,471 | -69 | -51 | -2,182 | -2,464 | -180 | -2,640 | -234 | 37,843 / 20,902 | 53,526 / 26,707 | -30,807 / 1,791 | 3,296 | 0.97 | 1.00 / 1.00 | -21,028 |  | S1 | no |

## P7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7 never-cut level | 33,625 | 22,555 | 13,873 | 11,894 | 8,318 | 5,178 | 8,641 | -118 | 133,887 | 109,442 | -29,902 |
| P7 LIVE REF S1b-COMB level | 5,700 | 18,966 | 12,054 | 14,708 | 10,485 | 11,144 | 6,746 | -2 | 96,490 | 106,914 | 53,844 |

### P7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback@after30 | {"X": 20, "ctx": "after30", "pb": 40} | -33,284 | -14,544 | -9,266 | 3,938 | -2,898 | -2,253 | -5,504 | 424 | 38,077 / 133,887 | 57,033 / 109,442 | 95,825 / -29,902 | 2,730 | 0.02 | 1.00 / 0.72 | -244,967 | -3,790 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D0_plain@after30 | {"X": 30, "ctx": "after30"} | -26,936 | -13,786 | -8,177 | 2,195 | -2,050 | 843 | -5,691 | 703 | 45,910 / 133,887 | 88,649 / 109,442 | 86,435 / -29,902 | 2,600 | 0.02 | 1.00 / 0.79 | -188,556 | 991 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 25, "blk": "A", "cancels" | -18,744 | -19,970 | -11,421 | 892 | -1,176 | 9,213 | -2,698 | -728 | 49,145 / 133,887 | 87,956 / 109,442 | 56,330 / -29,902 | 2,017 | 0.02 | 1.00 / 0.79 | -541,581 | -15,057 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "C", "cancels" | -16,198 | -12,587 | -6,208 | 8,451 | 3,214 | 2,334 | -4,292 | 329 | 50,418 / 133,887 | 97,168 / 109,442 | 161,266 / -29,902 | 2,528 | 0.37 | 1.00 / 0.99 | -541,581 | -5,309 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "C", "cancels" | -16,198 | -12,390 | -6,190 | 8,227 | 2,893 | 1,230 | -4,242 | 634 | 50,418 / 133,887 | 95,628 / 109,442 | 154,417 / -29,902 | 2,539 | 0.31 | 1.00 / 0.99 | -541,581 | -5,309 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

### P7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_gated | {"P": [1.0, 2.0, 2.0, 1.0, 0.7, 1.0], "arm": 0.7, "feat": "t | 3,680 | -4,505 | 522 | 655 | 1,007 | 4,519 | -2,499 | -1,342 | 71,485 / 133,887 | 107,157 / 109,442 | 64,089 / -29,902 | 1,028 | 0.09 | 1.00 / 0.96 | -647,399 | -1,317 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| H_gated | {"P": [1.0, 2.0, 2.0, 1.0, 0.8, 1.0], "arm": 0.8, "feat": "t | -2,786 | -3,368 | -173 | 525 | 399 | -2,576 | -1,154 | -622 | 82,220 / 133,887 | 110,881 / 109,442 | 34,321 / -29,902 | 725 | 0.15 | 1.00 / 0.98 | -647,399 | 1,633 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -841 | 678 | 1,582 | 5,082 | 2,987 | 766 | -1,380 | -800 | 82,296 / 133,887 | 92,199 / 109,442 | 76,006 / -29,902 | 1,006 | 0.02 | 1.00 / 1.00 | -186,434 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -1,382 | 528 | 1,972 | 5,069 | 3,016 | 754 | -1,412 | -876 | 83,539 / 133,887 | 91,553 / 109,442 | 78,160 / -29,902 | 1,006 | 0.04 | 1.00 / 1.00 | -186,434 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 40}, "base_tech":  | 3,029 | -7,152 | -3,235 | 1,621 | 1,825 | 2,116 | -1,081 | -832 | 87,937 / 133,887 | 97,537 / 109,442 | 63,228 / -29,902 | 946 | 0.04 | 1.00 / 1.00 | -186,434 | -5,288 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### P7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -33,626 | -8,066 | -2,745 | -2,283 | -6,501 | -7,547 | -9,178 | -1,662 | 26,813 / 133,887 | 178,169 / 109,442 | 20,561 / -29,902 | 3,178 | 0.03 | 1.00 / 0.21 | 0 |  | S1 | no |
| CROSS[966d0f8e1e9e+01618af6c2a8] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "01618af6c2 | -31,445 | -6,862 | -1,756 | -1,789 | -5,659 | -6,620 | -9,527 | -1,706 | 37,485 / 133,887 | 203,578 / 109,442 | 33,034 / -29,902 | 3,247 | 0.03 | 1.00 / 0.37 |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -30,791 | -13,682 | -8,608 | -2,939 | -7,029 | -6,418 | -8,098 | -986 | 45,473 / 133,887 | 152,285 / 109,442 | -16,581 / -29,902 | 2,981 | 0.03 | 1.00 / 0.41 | 0 |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -35,154 | -32,544 | -26,288 | -15,368 | -18,497 | -15,180 | -12,938 | -2,932 | 238,845 / 133,887 | 459,309 / 109,442 | -279,528 / -29,902 | 4,163 | 1.00 | 1.00 / 1.00 | 0 |  | S1 | no |
| CROSS[63c14ae16fd1+2dd5c144c1a7] | {"book": "U7", "loss": "63c14ae16fd1", "profit": "2dd5c144c1 | -49,137 | -24,819 | -20,957 | -19,572 | -19,200 | -12,679 | -12,481 | -3,144 | 249,975 / 133,887 | 466,013 / 109,442 | -396,572 / -29,902 | 4,420 | 1.00 | 1.00 / 0.15 | 0 |  | S1 | no |

## M7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7 never-cut level | 419 | 3,250 | 247 | 410 | 128 | 154 | 90 | -128 | 44,425 | 50,321 | -68,299 |
| M7 LIVE REF S1b-COMB level | 40 | 2,590 | -776 | -227 | -639 | 601 | 523 | -64 | 46,547 | 25,812 | -64,633 |

### M7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3_stop_extreme | {"X": 10, "k": 0} | -1,522 | -1,232 | -1,921 | 737 | 108 | -1,018 | -812 | -447 | 13,450 / 44,425 | 45,329 / 50,321 | -26,663 / -68,299 | 3,214 | 0.03 | 1.00 / 0.06 | -12,478 | -1,985 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 10, "blk": "A", "cancels" | 2,543 | 1,840 | 3,151 | 1,741 | 14 | -865 | 238 | 113 | 13,485 / 44,425 | 31,252 / 50,321 | -12,409 / -68,299 | 1,195 | 0.02 | 1.00 / 0.54 | -18,261 | 724 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_dtot8_rel_w15 | {"arm": 15.0, "arm_kind": "abs", "dir": -1, "feat": "dtot8_r | -2,042 | -1,152 | 634 | 849 | -290 | -991 | -360 | 14 | 13,767 / 44,425 | 48,783 / 50,321 | -28,007 / -68,299 | 2,323 | 0.03 | 1.00 / 0.13 | -22,187 | -1,886 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 1, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | -878 | -1,089 | 756 | 527 | -316 | -939 | -59 | 26 | 14,218 / 44,425 | 26,832 / 50,321 | -36,027 / -68,299 | 2,050 | 0.72 | 1.00 / 0.06 | -18,261 | -2,838 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| LBC_cps_rel_w10 | {"arm": 0.3, "arm_kind": "pct", "dir": 1, "feat": "cps_rel_w | -350 | -3,309 | -795 | 554 | -90 | -912 | -167 | -860 | 14,306 / 44,425 | 37,643 / 50,321 | -34,516 / -68,299 | 2,397 | 0.06 | 1.00 / 0.02 | -17,132 | -1,135 | S1 | CANDIDATE-DD [rec-FAIL wf-FAIL plc-ok exposure] |

### M7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_thick | {"P": [1.0, 3.0, 1.3, 1.0, 0.1, 1.0], "arm": 0.1, "feat": "t | -72 | -3,687 | -1,015 | 219 | -180 | -472 | -744 | -1,059 | 14,461 / 44,425 | 49,060 / 50,321 | -28,224 / -68,299 | 2,923 | 0.05 | 1.00 / 0.32 | -17,582 | -2,874 | S1 | CANDIDATE-DD [rec-FAIL wf-FAIL plc-ok exposure] |
| H_thick | {"P": [1.0, 1.0, 1.5, 1.0, 0.1, 1.0], "arm": 0.1, "feat": "a | 1,398 | -2,880 | -238 | 299 | -93 | -327 | -728 | -1,113 | 19,927 / 44,425 | 52,736 / 50,321 | -22,948 / -68,299 | 2,978 | 0.28 | 1.00 / 0.95 | -17,582 | -2,338 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| I_decay | {"P": [9.0, 30.0, 5.0, 1.0, 0.3], "X0": 30, "Xmin": 5, "arm" | -331 | -282 | 464 | 383 | -85 | 424 | -673 | -847 | 21,793 / 44,425 | 52,180 / 50,321 | -24,876 / -68,299 | 2,622 | 0.05 | 1.00 / 0.99 |  | 3,872 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_pcthour | {"P": [3.0, 0.3, 120.0, 510.0], "pct": 0.3, "window": "ldn"} | -1,088 | -1,922 | -1,095 | 673 | 300 | -751 | 293 | -126 | 21,934 / 44,425 | 22,514 / 50,321 | -32,139 / -68,299 | 1,594 | 0.03 | 1.00 / 1.00 |  | -328 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| H_pcthour | {"P": [3.0, 0.3, 0.0, 1440.0], "pct": 0.3, "window": "all"} | -1,202 | -1,038 | -1,271 | 43 | 100 | 1,254 | -290 | -420 | 22,817 / 44,425 | 30,733 / 50,321 | -30,035 / -68,299 | 2,927 | 0.09 | 1.00 / 0.98 |  | 2 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### M7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -1,143 | -1,185 | -352 | -345 | -560 | -318 | -689 | 5 | 34,844 / 44,425 | 66,902 / 50,321 | -47,794 / -68,299 | 2,491 | 0.52 | 1.00 / 0.77 | -6,040 |  | S1 | no |
| CROSS[e0fb6a9abc57+8e7c342b397d] | {"book": "M7", "loss": "e0fb6a9abc57", "profit": "8e7c342b39 | -1,942 | -1,859 | -53 | -492 | -1,022 | -2,671 | -1,375 | -933 | 35,034 / 44,425 | 84,737 / 50,321 | -45,579 / -68,299 | 3,296 | 0.42 | 1.00 / 0.59 | -3,016 |  | S1 | no |
| CROSS[e7c0088d2553+a66d38e1ce5f] | {"book": "A7", "loss": "e7c0088d2553", "profit": "a66d38e1ce | 132 | 295 | 361 | -1,039 | -957 | 1,592 | -926 | -613 | 38,416 / 44,425 | 82,068 / 50,321 | -54,836 / -68,299 | 2,496 | 0.82 | 1.00 / 1.00 |  |  | S1 | no |
| CROSS[cd4451a22198+87cd2ee2381f] | {"book": "K7", "loss": "cd4451a22198", "profit": "87cd2ee238 | -934 | -2,709 | -1,182 | -203 | -743 | -841 | -846 | -504 | 41,584 / 44,425 | 74,700 / 50,321 | -50,616 / -68,299 | 2,500 | 0.91 | 1.00 / 1.00 | -15,298 |  | S1 | no |
| CROSS[966d0f8e1e9e+01618af6c2a8] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "01618af6c2 | -1,166 | -1,333 | -604 | -665 | -810 | -595 | -1,083 | -239 | 42,687 / 44,425 | 92,894 / 50,321 | -57,919 / -68,299 | 2,761 | 0.91 | 1.00 / 0.90 |  |  | S1 | no |

## U7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7 never-cut level | -4,186 | 275 | -125 | 3,207 | 1,811 | 1,724 | 1,437 | 1,354 | 21,561 | 42,226 | 120 |
| U7 LIVE REF S1b-COMB level | -3,377 | 1,858 | 1,576 | 3,562 | 2,081 | 2,437 | 1,419 | 1,157 | 16,419 | 39,155 | 8,146 |

### U7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_ice_ag_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "ice_ag_w | 4,365 | 3,585 | 2,874 | 809 | 534 | 845 | -624 | -423 | 6,061 / 21,561 | 35,033 / 42,226 | 21,429 / 120 | 777 | 0.02 | 1.00 / 0.91 | -73,167 | 2,829 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_ice_ag_w10 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "ice_ag_w | 4,325 | 1,039 | 860 | 774 | 439 | 692 | -559 | -423 | 6,061 / 21,561 | 30,662 / 42,226 | 20,553 / 120 | 768 | 0.02 | 1.00 / 0.90 | -73,167 | 2,829 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_ice_ag_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "ice_ag_w | 3,819 | -1,506 | -110 | 856 | 785 | -1,235 | 10 | -1,105 | 6,621 / 21,561 | 20,630 / 42,226 | 28,980 / 120 | 792 | 0.02 | 1.00 / 0.94 | -119,760 | 2,829 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_r_ab8 | {"arm": 45.0, "arm_kind": "abs", "dir": 1, "feat": "r_ab8",  | 3,951 | 1,893 | 991 | 382 | 729 | 2,083 | 358 | 987 | 7,200 / 21,561 | 40,937 / 42,226 | 21,278 / 120 | 490 | 0.02 | 1.00 / 0.94 | -151,022 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "C", "cancels" | 4,731 | 2,325 | 1,591 | 894 | 1,188 | 1,309 | -33 | 553 | 7,335 / 21,561 | 37,858 / 42,226 | 21,476 / 120 | 430 | 0.02 | 1.00 / 0.98 | -129,230 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### U7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_pcthour | {"P": [3.0, 0.3, 120.0, 510.0], "pct": 0.3, "window": "ldn"} | 4,858 | 1,091 | 1,509 | 153 | 464 | 1,037 | -1,294 | -919 | 8,700 / 21,561 | 42,735 / 42,226 | 3,983 / 120 | 769 | 0.03 | 1.00 / 0.96 |  | 7,540 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| I_trail | {"P": [4.0, 25.0, 0.7, 0.0], "X": 25, "arm": 0.7} | 4,988 | -480 | 1,950 | 1,154 | 899 | -376 | -243 | -608 | 10,126 / 21,561 | 33,544 / 42,226 | 37,905 / 120 | 387 | 0.06 | 1.00 / 1.00 |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| I_chand | {"P": [4.0, 1.0, 0.7, 2.0], "arm": 0.7, "atr": "atr5m", "k": | 5,809 | -604 | 1,967 | 1,036 | 891 | -1,280 | -318 | -463 | 10,146 / 21,561 | 35,510 / 42,226 | 38,825 / 120 | 527 | 0.05 | 1.00 / 1.00 |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X2_target_trail | {"arm": 0.7, "m": 2, "x": 20} | 6,557 | -148 | 1,992 | 551 | 525 | -1,411 | -704 | -575 | 10,319 / 21,561 | 38,921 / 42,226 | 20,588 / 120 | 849 | 0.03 | 1.00 / 1.00 | -76,727 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| I_lock | {"P": [8.0, 0.7, 20.0], "X": 20, "arm": 0.7} | 5,370 | 74 | 2,240 | 1,598 | 1,119 | -197 | -248 | -532 | 11,031 / 21,561 | 35,820 / 42,226 | 45,962 / 120 | 342 | 0.40 | 1.00 / 1.00 |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

### U7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 1,141 | -1,906 | -1,782 | -1,284 | -1,749 | -1,232 | -2,182 | -1,370 | 12,841 / 21,561 | 78,568 / 42,226 | -22,711 / 120 | 1,150 | 0.12 | 1.00 / 0.96 | 0 |  | S1 | no |
| CROSS[892462577f14+2874a7dfe132] | {"book": "U7", "loss": "892462577f14", "profit": "2874a7dfe1 | 1,635 | 435 | 120 | -2,768 | -3,405 | -3,459 | -3,641 | -3,017 | 13,469 / 21,561 | 178,279 / 42,226 | -41,770 / 120 | 1,140 | 1.00 | 1.00 / 0.90 |  |  | S1 | no |
| CROSS[63c14ae16fd1+2dd5c144c1a7] | {"book": "U7", "loss": "63c14ae16fd1", "profit": "2dd5c144c1 | 5,250 | 1,759 | 1,036 | -1,086 | -1,175 | -1,969 | -3,078 | -963 | 16,992 / 21,561 | 150,582 / 42,226 | -23,365 / 120 | 1,282 | 1.00 | 1.00 / 1.00 | 0 |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 739 | -2,641 | -1,533 | -1,539 | -790 | -1,196 | -952 | 453 | 18,512 / 21,561 | 51,925 / 42,226 | -36,857 / 120 | 805 | 0.48 | 1.00 / 1.00 | -6,381 |  | S1 | no |
| CROSS[e3877cab15a7+55aab8e87e08] | {"book": "O7", "loss": "e3877cab15a7", "profit": "55aab8e87e | 1,935 | -4,174 | -2,504 | -4,352 | -2,926 | -1,692 | -2,200 | -1,059 | 25,307 / 21,561 | 63,301 / 42,226 | -48,700 / 120 | 1,076 | 1.00 | 1.00 / 1.00 | 0 |  | S1 | no |

## A7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 never-cut level | 389 | -97 | -190 | 601 | 538 | -81 | 989 | 207 | 12,461 | 6,089 | -17,069 |
| A7 LIVE REF S1b-COMB level | -1,287 | 217 | 169 | 821 | 731 | -228 | 937 | 240 | 8,518 | 7,325 | -11,915 |

### A7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback | {"X": 20, "pb": 50} | 34 | 855 | 467 | 511 | 183 | 304 | -146 | 183 | 4,760 / 12,461 | 5,445 / 6,089 | -6,160 / -17,069 | 700 | 0.02 | 1.00 / 0.64 | -12,489 | -1,314 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D3_pullback | {"X": 15, "pb": 50} | -11 | 288 | 199 | 129 | 24 | 223 | -207 | 201 | 4,785 / 12,461 | 4,912 / 6,089 | -4,174 / -17,069 | 713 | 0.02 | 1.00 / 0.63 | -12,489 | -1,018 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 20, "blk": "C", "cancels" | -737 | 848 | 651 | 298 | -18 | 306 | -199 | 37 | 4,900 / 12,461 | 5,378 / 6,089 | -11,330 / -17,069 | 521 | 0.11 | 1.00 / 0.63 | -50,405 | -42 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 1, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | -1,359 | 469 | 197 | 60 | -86 | 140 | -263 | -96 | 5,011 / 12,461 | 5,315 / 6,089 | -15,604 / -17,069 | 573 | 0.11 | 1.00 / 0.57 | -50,405 | -1,306 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| LBC_lp_ag_w30 | {"arm": 15.0, "arm_kind": "abs", "dir": 1, "feat": "lp_ag_w3 | -1,110 | 482 | 239 | 339 | -128 | 116 | -468 | 247 | 5,157 / 12,461 | 5,621 / 6,089 | -8,141 / -17,069 | 657 | 0.17 | 1.00 / 0.64 | -21,630 | -449 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

### A7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_pcthour | {"P": [3.0, 0.4, 1080.0, 120.0], "pct": 0.4, "window": "asia | 788 | -536 | -75 | 427 | -45 | -810 | -289 | 43 | 3,268 / 12,461 | 6,089 / 6,089 | -1,783 / -17,069 | 680 | 0.02 | 1.00 / 0.55 |  | 665 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_pcthour | {"P": [3.0, 0.4, 0.0, 1440.0], "pct": 0.4, "window": "all"} | 788 | -806 | -30 | 374 | 106 | -546 | -183 | 12 | 3,268 / 12,461 | 4,461 / 6,089 | -2,128 / -17,069 | 892 | 0.02 | 1.00 / 0.56 |  | 665 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_gated | {"P": [1.0, 5.0, 20.0, 1.0, 0.25, 1.0], "arm": 0.25, "feat": | 422 | -731 | 229 | 328 | 62 | -681 | -246 | -116 | 3,723 / 12,461 | 4,568 / 6,089 | 1,459 / -17,069 | 905 | 0.02 | 1.00 / 0.61 | -61,186 | 161 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_gated | {"P": [1.0, 4.0, 20.0, 1.0, 0.25, 1.0], "arm": 0.25, "feat": | 574 | -1,177 | 165 | 587 | 22 | -968 | -148 | -176 | 3,733 / 12,461 | 4,455 / 6,089 | 6,397 / -17,069 | 754 | 0.02 | 1.00 / 0.63 | -61,186 | -1,592 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_gated | {"P": [1.0, 4.0, 10.0, 1.0, 0.25, 1.0], "arm": 0.25, "feat": | 519 | -582 | 173 | 272 | 35 | -694 | -431 | 16 | 3,750 / 12,461 | 5,327 / 6,089 | 1,017 / -17,069 | 939 | 0.02 | 1.00 / 0.59 | -61,186 | 339 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### A7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -907 | 293 | 148 | 521 | 204 | 21 | -232 | 80 | 4,415 / 12,461 | 4,374 / 6,089 | -7,646 / -17,069 | 732 | 0.03 | 1.00 / 0.60 | 4,462 |  | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok exposure] |
| CROSS[d37df9ed0314+8e7c342b397d] | {"book": "M7", "loss": "d37df9ed0314", "profit": "8e7c342b39 | -79 | 1,126 | 656 | 252 | -23 | 302 | -59 | 30 | 6,506 / 12,461 | 5,710 / 6,089 | -13,365 / -17,069 | 453 | 0.06 | 1.00 / 0.81 | -24,127 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -1,696 | -428 | -114 | -293 | -266 | 279 | -236 | -3 | 10,135 / 12,461 | 5,229 / 6,089 | -17,946 / -17,069 | 591 | 0.76 | 1.00 / 0.86 | -10,659 |  | S1 | no |
| CROSS[966d0f8e1e9e+01618af6c2a8] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "01618af6c2 | -2,354 | -221 | 173 | -345 | -255 | -897 | -492 | 180 | 11,977 / 12,461 | 13,504 / 6,089 | -14,811 / -17,069 | 786 | 1.00 | 1.00 / 0.95 |  |  | S1 | no |
| CROSS[e0fb6a9abc57+8e7c342b397d] | {"book": "M7", "loss": "e0fb6a9abc57", "profit": "8e7c342b39 | -2,756 | -591 | -261 | -763 | -484 | 610 | -713 | 51 | 13,144 / 12,461 | 10,762 / 6,089 | -24,434 / -17,069 | 977 | 0.79 | 1.00 / 0.81 | -806 |  | S1 | no |

## H7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7 never-cut level | -88 | 1,778 | -301 | 1,647 | -73 | -2,452 | 1,623 | 103 | 15,477 | 20,667 | -32,750 |
| H7 LIVE REF S1b-COMB level | 3,186 | 1,158 | 406 | 2,545 | 625 | -1,655 | 1,574 | 220 | 8,818 | 19,256 | 11,007 |

### H7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_sweep8_w10 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | 1,289 | 322 | 1,222 | 1,281 | 917 | 834 | -138 | -22 | 4,988 / 15,477 | 15,783 / 20,667 | 6,350 / -32,750 | 338 | 0.02 | 1.00 / 0.79 | -45,009 | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_adv_best_move | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "adv_best | 343 | 157 | -58 | 384 | 822 | 712 | -43 | 137 | 5,048 / 15,477 | 19,458 / 20,667 | -3,411 / -32,750 | 496 | 0.02 | 1.00 / 0.41 | -6,353 | 109 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_adv_best_move | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best | 223 | 97 | -98 | 261 | 772 | 712 | -105 | 118 | 5,048 / 15,477 | 20,484 / 20,667 | -4,679 / -32,750 | 504 | 0.02 | 1.00 / 0.39 | -6,353 | 109 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w60 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 1,550 | 604 | 1,039 | 990 | 614 | 703 | -27 | 83 | 5,146 / 15,477 | 16,156 / 20,667 | 3,037 / -32,750 | 394 | 0.02 | 1.00 / 0.76 | -18,875 | 244 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 408 | 305 | 474 | 654 | 516 | 871 | -175 | 108 | 5,190 / 15,477 | 15,940 / 20,667 | -922 / -32,750 | 354 | 0.03 | 1.00 / 0.60 | 15,942 | 374 | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok] |

### H7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_mom | {"P": [1.0, 9.0, 0.0, 1.0, 0.25, -1.0], "arm": 0.25, "feat": | 1,418 | 639 | 1,607 | 137 | 535 | -570 | -975 | -504 | 5,961 / 15,477 | 10,161 / 20,667 | 2,693 / -32,750 | 847 | 0.02 | 1.00 / 0.54 | -78,529 | 2,524 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_gated | {"P": [1.0, 7.0, 0.2, 1.0, 0.4, 1.0], "arm": 0.4, "feat": "i | 1,263 | 524 | 1,252 | 301 | 589 | -348 | -634 | -225 | 5,992 / 15,477 | 10,534 / 20,667 | -533 / -32,750 | 791 | 0.02 | 1.00 / 0.55 | -42,458 | 2,741 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_mom | {"P": [1.0, 9.0, 1.0, 1.0, 0.25, -1.0], "arm": 0.25, "feat": | 1,236 | 414 | 1,458 | 116 | 583 | -357 | -675 | -477 | 6,016 / 15,477 | 8,137 / 20,667 | 2,354 / -32,750 | 853 | 0.02 | 1.00 / 0.53 | -78,529 | 2,369 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_mom | {"P": [1.0, 9.0, 2.0, 1.0, 0.25, -1.0], "arm": 0.25, "feat": | 1,250 | 397 | 1,417 | 74 | 579 | -383 | -654 | -523 | 6,241 / 15,477 | 8,042 / 20,667 | 399 / -32,750 | 856 | 0.02 | 1.00 / 0.52 | -78,529 | 2,361 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_gated | {"P": [1.0, 5.0, 10.0, 1.0, 0.4, 1.0], "arm": 0.4, "feat": " | 1,765 | 715 | 1,285 | 194 | 631 | 13 | -800 | -86 | 6,390 / 15,477 | 14,345 / 20,667 | -1,620 / -32,750 | 796 | 0.02 | 1.00 / 0.55 | -42,458 | 2,659 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### H7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e3e1c7125354+e1e6e2a7d150] | {"book": "H7", "loss": "e3e1c7125354", "profit": "e1e6e2a7d1 | 833 | 290 | 1,243 | -409 | -277 | 1,160 | -1,332 | -1,073 | 7,541 / 15,477 | 25,504 / 20,667 | -12,559 / -32,750 | 872 | 0.36 | 1.00 / 0.38 | 1,213 |  | S1 | no |
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -646 | -413 | 580 | -177 | 257 | 1,924 | 67 | 426 | 9,891 / 15,477 | 19,959 / 20,667 | -16,547 / -32,750 | 603 | 0.24 | 1.00 / 0.69 | -12,327 |  | S1 | no |
| CROSS[e3877cab15a7+55aab8e87e08] | {"book": "O7", "loss": "e3877cab15a7", "profit": "55aab8e87e | 228 | 288 | 948 | -303 | -12 | 356 | -1,122 | -682 | 9,991 / 15,477 | 23,638 / 20,667 | -10,538 / -32,750 | 869 | 0.94 | 1.00 / 0.70 | -32,897 |  | S1 | no |
| CROSS[966d0f8e1e9e+01618af6c2a8] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "01618af6c2 | -781 | -490 | 509 | -397 | 37 | 1,510 | -295 | 346 | 10,769 / 15,477 | 19,947 / 20,667 | -19,684 / -32,750 | 714 | 0.55 | 1.00 / 0.69 |  |  | S1 | no |
| CROSS[afa4804db573+e1e6e2a7d150] | {"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d1 | -536 | -708 | 210 | -1,609 | -990 | 728 | -1,369 | -784 | 15,597 / 15,477 | 22,528 / 20,667 | -36,028 / -32,750 | 914 | 0.79 | 1.00 / 0.56 | -3,845 |  | S1 | no |

## O7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 never-cut level | -685 | -396 | -65 | 280 | 687 | -245 | 644 | -119 | 7,469 | 5,102 | -9,532 |
| O7 LIVE REF S1b-COMB level | -988 | -446 | -78 | 331 | 651 | -343 | 636 | -147 | 6,656 | 4,532 | -8,247 |

### O7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_dtot8_rel_w15 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dtot8_r | 574 | 173 | 214 | 325 | -8 | -57 | -395 | 50 | 2,725 / 7,469 | 5,195 / 5,102 | -437 / -9,532 | 355 | 0.02 | 1.00 / 0.57 | 1,916 | 940 | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok exposure] |
| LBC_dlt_med_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dlt_med | 321 | 309 | 116 | 34 | -308 | 134 | -500 | 165 | 3,243 / 7,469 | 4,699 / 5,102 | -4,802 / -9,532 | 448 | 0.05 | 1.00 / 0.45 | -20,988 | -243 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_dlt_med_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dlt_med | 624 | 479 | 226 | 66 | -216 | 137 | -494 | 130 | 3,600 / 7,469 | 5,318 / 5,102 | -4,838 / -9,532 | 441 | 0.11 | 1.00 / 0.50 | -20,988 | 1,302 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| LBC_sweep8_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 461 | 41 | 400 | 110 | -186 | 223 | -35 | 226 | 3,859 / 7,469 | 4,241 / 5,102 | -4,740 / -9,532 | 220 | 0.03 | 1.00 / 0.58 | -22,094 | 826 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 179 | 301 | 149 | 129 | -133 | 202 | -14 | 124 | 4,019 / 7,469 | 3,820 / 5,102 | -4,654 / -9,532 | 159 | 0.02 | 1.00 / 0.69 | -22,094 | 399 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### O7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| I_step | {"P": [7.0, 10.0, 1.0], "lag": 1, "step": 10} | 1,130 | 289 | 203 | 215 | -335 | -170 | -498 | 29 | 4,420 / 7,469 | 4,995 / 5,102 | -891 / -9,532 | 406 | 0.09 | 1.00 / 0.96 |  | 1,167 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_thick | {"P": [1.0, 3.0, 1.3, 1.0, 0.25, 1.0], "arm": 0.25, "feat":  | 728 | 219 | 291 | 262 | -148 | -191 | -507 | 85 | 4,450 / 7,469 | 5,025 / 5,102 | -1,790 / -9,532 | 299 | 0.03 | 1.00 / 0.97 | -25,014 | 636 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 150} | 1,208 | 377 | 464 | 27 | -183 | 96 | -54 | -31 | 5,487 / 7,469 | 3,920 / 5,102 | -2,571 / -9,532 | 151 | 0.08 | 1.00 / 1.00 | -6,496 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 90} | 1,208 | 377 | 464 | 27 | -183 | 96 | -54 | -31 | 5,487 / 7,469 | 3,920 / 5,102 | -2,571 / -9,532 | 151 | 0.02 | 1.00 / 1.00 | -6,496 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| I_step | {"P": [7.0, 5.0, 3.0], "lag": 3, "step": 5} | 1,239 | 267 | 301 | 272 | -245 | -191 | -501 | 145 | 5,672 / 7,469 | 5,284 / 5,102 | -266 / -9,532 | 361 | 0.31 | 1.00 / 1.00 |  | 807 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

### O7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | 366 | 286 | 61 | 68 | -344 | 194 | -603 | 112 | 2,425 / 7,469 | 8,075 / 5,102 | -3,682 / -9,532 | 430 | 0.06 | 1.00 / 0.35 | -11,998 |  | S1 | LEAD [rec-ok wf-FAIL plc-ok exposure] |
| CROSS[966d0f8e1e9e+01618af6c2a8] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "01618af6c2 | 366 | 244 | 33 | 14 | -384 | 194 | -605 | 70 | 2,425 / 7,469 | 8,927 / 5,102 | -4,194 / -9,532 | 453 | 0.03 | 1.00 / 0.28 |  |  | S1 | LEAD [rec-ok wf-FAIL plc-ok exposure] |
| CROSS[e0fb6a9abc57+8e7c342b397d] | {"book": "M7", "loss": "e0fb6a9abc57", "profit": "8e7c342b39 | 581 | -16 | 199 | 110 | -194 | 219 | -590 | 263 | 2,941 / 7,469 | 9,135 / 5,102 | -2,554 / -9,532 | 431 | 0.06 | 1.00 / 0.44 | -14,495 |  | S1 | LEAD [rec-ok wf-FAIL plc-ok exposure] |
| CROSS[cd4451a22198+87cd2ee2381f] | {"book": "K7", "loss": "cd4451a22198", "profit": "87cd2ee238 | 510 | -64 | 176 | 37 | -273 | 182 | -582 | 187 | 3,560 / 7,469 | 9,106 / 5,102 | -4,548 / -9,532 | 395 | 0.06 | 1.00 / 0.48 | -7,025 |  | S1 | LEAD [rec-ok wf-FAIL plc-ok exposure] |
| CROSS[892462577f14+2874a7dfe132] | {"book": "U7", "loss": "892462577f14", "profit": "2874a7dfe1 | 142 | 494 | 117 | 37 | -298 | -104 | -671 | 86 | 3,639 / 7,469 | 14,653 / 5,102 | -4,672 / -9,532 | 436 | 0.15 | 1.00 / 0.49 |  |  | S1 | LEAD [rec-ok wf-FAIL plc-FAIL exposure] |

## X3
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X3 never-cut level | -166 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 664 | 0 | -664 |
| X3 LIVE REF S1b-COMB level | -448 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 1,794 | 0 | -1,794 |

### X3 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 30, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 228 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 1 | 0.49 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 15, "arm": "fixed", "armval": 15, "blk": "A", "cancels | 235 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.48 | 1.00 / - |  | 1,481 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 30, "arm": "fixed", "armval": 50, "blk": "A", "cancels | 211 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 1 | 0.55 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 182 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.49 | 1.00 / - |  | 1,166 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 336 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.51 | 1.00 / - |  | 1,941 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

### X3 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K2_atrtarget | {"c": 6} | 393 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 2 | 1.00 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| K1_target | {"m": 1.1} | 120 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 184 / 664 | 0 / 0 | -184 / -664 | 2 | 1.00 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| PJKL_perbook_best | {"picks": {"H7": ["K1_target", "{\"m\": 0.5}"], "K7": ["K1_t | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 |  | nan | 1.00 / - |  |  | S2 | no |
| PJKL_uniform_best | {"cell": "{\"m\": 0.75, \"p\": 0.7, \"rest\": \"trail\", \"x | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 |  | nan | 1.00 / - |  |  | S2 | no |
| PHI_perbook_s2able | {"rules": {"A7": {"cell_id": "a66d38e1ce5f", "pct": 0.4, "te | 0 | 0 | 0 | 0 | 0 | 0 |  |  | 0 / 0 |  /  | 0 / 0 |  | nan | 1.00 / - |  |  | S2[L1M,L2M,L3M,L6M,HOLD,MID-covered] | S2-partial (older windows pending) [rec-ok wf-FAIL plc-FAIL] |

### X3 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 379 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 2 | 0.52 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| CROSS[892462577f14+2874a7dfe132] | {"book": "U7", "loss": "892462577f14", "profit": "2874a7dfe1 | 311 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.58 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| CROSS[cd4451a22198+87cd2ee2381f] | {"book": "K7", "loss": "cd4451a22198", "profit": "87cd2ee238 | 171 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.42 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| CROSS[e7c0088d2553+a66d38e1ce5f] | {"book": "A7", "loss": "e7c0088d2553", "profit": "a66d38e1ce | 379 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 2 | 0.36 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| CROSS[966d0f8e1e9e+01618af6c2a8] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "01618af6c2 | 177 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.58 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

## X4
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X4 never-cut level | 1,195 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| X4 LIVE REF S1b-COMB level | 795 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### X4 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 3, "arm": "fixed", "armval": 20, "blk": "A", "cancels" | -874 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 513 | S1 | no |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 25, "blk": "A", "cancels | -904 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 538 | S1 | no |
| A_pulled | {"W": 15, "arm": "fixed", "armval": 30, "blk": "A", "cancels | -883 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 533 | S1 | no |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 10, "blk": "A", "cancels | -686 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 1,223 | S1 | no |
| A_pulled | {"W": 30, "arm": "fixed", "armval": 20, "blk": "A", "cancels | -842 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 568 | S1 | no |

### X4 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J3_statescale | {"a": 0.4, "f": "tot_rel_slow", "rest": "hold", "s": 10, "th | -118 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| J1_scale | {"p": 0.8, "rest": "trail", "x": 5} | -299 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| J3_statescale | {"a": 0.2, "f": "tot_rel_slow", "rest": "trail", "s": 10, "t | -292 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| J3_statescale | {"a": 0.2, "f": "tot_rel_slow", "rest": "hold", "s": 10, "th | -118 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| L1_cond | {"base": {"b": 0, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | -468 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |

### X4 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[afa4804db573+e1e6e2a7d150] | {"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d1 | -1,121 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -853 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -1,057 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+55aab8e87e08] | {"book": "A7", "loss": "e7c0088d2553", "profit": "55aab8e87e | -480 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[63c14ae16fd1+2dd5c144c1a7] | {"book": "U7", "loss": "63c14ae16fd1", "profit": "2dd5c144c1 | -551 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |

## X5
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| X5 never-cut level | 13 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| X5 LIVE REF S1b-COMB level | 95 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

### X5 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 15, "arm": "fixed", "armval": 15, "blk": "A", "cancels | 424 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 788 | S1 | no |
| A_pulled | {"W": 30, "arm": "fixed", "armval": 50, "blk": "A", "cancels | 44 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 0 | S1 | no |
| A_pulled | {"W": 10, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 471 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 973 | S1 | no |
| A_pulled | {"W": 3, "arm": "fixed", "armval": 30, "blk": "A", "cancels" | 232 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 18 | S1 | no |
| A_pulled | {"W": 15, "arm": "fixed", "armval": 10, "blk": "A", "cancels | 414 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  | 748 | S1 | no |

### X5 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 1.1} | 60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| PJKL_perbook_best | {"picks": {"H7": ["K1_target", "{\"m\": 0.5}"], "K7": ["K1_t | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 |  | nan | 1.00 / - |  |  | S2 | no |
| PJKL_uniform_best | {"cell": "{\"m\": 0.75, \"p\": 0.7, \"rest\": \"trail\", \"x | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 |  | nan | 1.00 / - |  |  | S2 | no |
| PHI_perbook_s2able | {"rules": {"A7": {"cell_id": "a66d38e1ce5f", "pct": 0.4, "te | 0 | 0 | 0 | 0 | 0 | 0 |  |  | 0 / 0 |  /  | 0 / 0 |  | nan | 1.00 / - |  |  | S2[L1M,L2M,L3M,L6M,HOLD,MID-covered] | S2-partial (older windows pending) [rec-ok wf-FAIL plc-FAIL] |
| J3_statescale | {"a": 0.4, "f": "ahead_rel_slow", "rest": "hold", "s": 3, "t | -17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 18 / 0 | 0 / 0 | -18 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |

### X5 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[afa4804db573+e1e6e2a7d150] | {"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d1 | 121 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | 99 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 0.76 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 108 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 439 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | 226 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 0.76 | 1.00 / - |  |  | S1 | no |

## Survivors per book (CANDIDATE-DD and rec-ok and plc-ok and not FAILS-LIVE-WEEK; wf shown, not required; top 3 by drawdown-first)
### ALL survivors (1092 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 1,664 | 2,177 | 4,874 | 3,824 | 2,515 | 264 | -1,426 | -501 | 55,296 / 121,381 | 117,149 / 152,455 | 250,937 / 77,580 | 1,789 | 0.02 | 1.00 / 0.95 | -216,598 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 1,905 | 2,072 | 5,258 | 3,836 | 2,563 | 166 | -1,514 | -574 | 56,444 / 121,381 | 115,335 / 152,455 | 251,176 / 77,580 | 1,789 | 0.04 | 1.00 / 0.95 | -216,598 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -2,493 | -1,781 | 2,031 | 1,299 | -1,659 | -1,045 | -5,749 | -1,200 | 57,492 / 121,381 | 120,670 / 152,455 | 258,667 / 77,580 | 3,720 | 0.04 | 1.00 / 0.95 | -216,598 | -3,806 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### K7 survivors (180 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_adv_best_move | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best | 909 | 2,784 | 3,589 | 1,123 | -23 | 1,148 | -1,202 | 9 | 8,636 / 20,902 | 23,900 / 26,707 | 28,728 / 1,791 | 3,051 | 0.05 | 1.00 / 1.00 | -107,558 | 126 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, " | 1,717 | 728 | 1,963 | 666 | -5 | 100 | -673 | 390 | 8,893 / 20,902 | 23,892 / 26,707 | 16,614 / 1,791 | 636 | 0.02 | 1.00 / 0.94 | -41,710 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "trail", "x": 10} | 2,081 | -874 | 1,144 | 277 | -389 | -1,516 | -399 | 463 | 9,147 / 20,902 | 17,406 / 26,707 | 39,575 / 1,791 | 969 | 0.04 | 1.00 / 1.00 | -34,760 | -40 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### P7 survivors (322 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback@after30 | {"X": 20, "ctx": "after30", "pb": 40} | -33,284 | -14,544 | -9,266 | 3,938 | -2,898 | -2,253 | -5,504 | 424 | 38,077 / 133,887 | 57,033 / 109,442 | 95,825 / -29,902 | 2,730 | 0.02 | 1.00 / 0.72 | -244,967 | -3,790 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D0_plain@after30 | {"X": 30, "ctx": "after30"} | -26,936 | -13,786 | -8,177 | 2,195 | -2,050 | 843 | -5,691 | 703 | 45,910 / 133,887 | 88,649 / 109,442 | 86,435 / -29,902 | 2,600 | 0.02 | 1.00 / 0.79 | -188,556 | 991 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 25, "blk": "A", "cancels" | -18,744 | -19,970 | -11,421 | 892 | -1,176 | 9,213 | -2,698 | -728 | 49,145 / 133,887 | 87,956 / 109,442 | 56,330 / -29,902 | 2,017 | 0.02 | 1.00 / 0.79 | -541,581 | -15,057 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### M7 survivors (853 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3_stop_extreme | {"X": 10, "k": 0} | -1,522 | -1,232 | -1,921 | 737 | 108 | -1,018 | -812 | -447 | 13,450 / 44,425 | 45,329 / 50,321 | -26,663 / -68,299 | 3,214 | 0.03 | 1.00 / 0.06 | -12,478 | -1,985 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 10, "blk": "A", "cancels" | 2,543 | 1,840 | 3,151 | 1,741 | 14 | -865 | 238 | 113 | 13,485 / 44,425 | 31,252 / 50,321 | -12,409 / -68,299 | 1,195 | 0.02 | 1.00 / 0.54 | -18,261 | 724 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_dtot8_rel_w15 | {"arm": 15.0, "arm_kind": "abs", "dir": -1, "feat": "dtot8_r | -2,042 | -1,152 | 634 | 849 | -290 | -991 | -360 | 14 | 13,767 / 44,425 | 48,783 / 50,321 | -28,007 / -68,299 | 2,323 | 0.03 | 1.00 / 0.13 | -22,187 | -1,886 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### U7 survivors (374 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_ice_ag_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "ice_ag_w | 4,365 | 3,585 | 2,874 | 809 | 534 | 845 | -624 | -423 | 6,061 / 21,561 | 35,033 / 42,226 | 21,429 / 120 | 777 | 0.02 | 1.00 / 0.91 | -73,167 | 2,829 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_ice_ag_w10 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "ice_ag_w | 4,325 | 1,039 | 860 | 774 | 439 | 692 | -559 | -423 | 6,061 / 21,561 | 30,662 / 42,226 | 20,553 / 120 | 768 | 0.02 | 1.00 / 0.90 | -73,167 | 2,829 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_ice_ag_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "ice_ag_w | 3,819 | -1,506 | -110 | 856 | 785 | -1,235 | 10 | -1,105 | 6,621 / 21,561 | 20,630 / 42,226 | 28,980 / 120 | 792 | 0.02 | 1.00 / 0.94 | -119,760 | 2,829 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### A7 survivors (1072 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H_pcthour | {"P": [3.0, 0.4, 1080.0, 120.0], "pct": 0.4, "window": "asia | 788 | -536 | -75 | 427 | -45 | -810 | -289 | 43 | 3,268 / 12,461 | 6,089 / 6,089 | -1,783 / -17,069 | 680 | 0.02 | 1.00 / 0.55 |  | 665 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_pcthour | {"P": [3.0, 0.4, 0.0, 1440.0], "pct": 0.4, "window": "all"} | 788 | -806 | -30 | 374 | 106 | -546 | -183 | 12 | 3,268 / 12,461 | 4,461 / 6,089 | -2,128 / -17,069 | 892 | 0.02 | 1.00 / 0.56 |  | 665 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| H_gated | {"P": [1.0, 5.0, 20.0, 1.0, 0.25, 1.0], "arm": 0.25, "feat": | 422 | -731 | 229 | 328 | 62 | -681 | -246 | -116 | 3,723 / 12,461 | 4,568 / 6,089 | 1,459 / -17,069 | 905 | 0.02 | 1.00 / 0.61 | -61,186 | 161 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### H7 survivors (456 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_sweep8_w10 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | 1,289 | 322 | 1,222 | 1,281 | 917 | 834 | -138 | -22 | 4,988 / 15,477 | 15,783 / 20,667 | 6,350 / -32,750 | 338 | 0.02 | 1.00 / 0.79 | -45,009 | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_adv_best_move | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "adv_best | 343 | 157 | -58 | 384 | 822 | 712 | -43 | 137 | 5,048 / 15,477 | 19,458 / 20,667 | -3,411 / -32,750 | 496 | 0.02 | 1.00 / 0.41 | -6,353 | 109 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_adv_best_move | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best | 223 | 97 | -98 | 261 | 772 | 712 | -105 | 118 | 5,048 / 15,477 | 20,484 / 20,667 | -4,679 / -32,750 | 504 | 0.02 | 1.00 / 0.39 | -6,353 | 109 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### O7 survivors (148 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_dtot8_rel_w15 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dtot8_r | 574 | 173 | 214 | 325 | -8 | -57 | -395 | 50 | 2,725 / 7,469 | 5,195 / 5,102 | -437 / -9,532 | 355 | 0.02 | 1.00 / 0.57 | 1,916 | 940 | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok exposure] |
| LBC_dlt_med_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dlt_med | 321 | 309 | 116 | 34 | -308 | 134 | -500 | 165 | 3,243 / 7,469 | 4,699 / 5,102 | -4,802 / -9,532 | 448 | 0.05 | 1.00 / 0.45 | -20,988 | -243 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_sweep8_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 461 | 41 | 400 | 110 | -186 | 223 | -35 | 226 | 3,859 / 7,469 | 4,241 / 5,102 | -4,740 / -9,532 | 220 | 0.03 | 1.00 / 0.58 | -22,094 | 826 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### X3 survivors (1 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3_stop_extreme | {"X": 55, "k": 2} | 164 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 9 / 664 | 0 / 0 | -9 / -664 | 1 | 0.02 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

- X4: none (no cell is CANDIDATE-DD with rec-ok and plc-ok and not FAILS-LIVE-WEEK)
- X5: none (no cell is CANDIDATE-DD with rec-ok and plc-ok and not FAILS-LIVE-WEEK)

## Walk-forward of the picking procedure (all cells of a book/side; purged monthly, 7-day embargo, trailing 26 weeks, key = maxDD, worst-20, Ulcer, -mean)
| book   | side   |   ncells |   total |   dd_never |   dd_wf |   share_pos |   npick |   months | wf_ok   |
|:-------|:-------|---------:|--------:|-----------:|--------:|------------:|--------:|---------:|:--------|
| ALL    | loss   |    13392 | -970761 |     153255 |  193549 |           0 |      35 |       35 | False   |
| ALL    | profit |     1055 | -644276 |     153255 |  200591 |           0 |      35 |       35 | False   |
| ALL    | both   |       13 |       0 |     153255 |  153255 |           0 |       0 |       35 | True    |
| K7     | loss   |    12100 | -190946 |      42831 |   37873 |           0 |      35 |       35 | False   |
| K7     | profit |      969 | -119026 |      42831 |   49331 |           0 |      35 |       35 | False   |
| K7     | both   |       13 |  -97760 |      42831 |   42831 |           0 |       7 |       35 | False   |
| P7     | loss   |    12199 | -457318 |     144370 |  143827 |           0 |      35 |       35 | False   |
| P7     | profit |     1031 | -436138 |     144370 |  161195 |           0 |      35 |       35 | False   |
| P7     | both   |       13 |       0 |     144370 |  144370 |           0 |       0 |       35 | True    |
| M7     | loss   |    11832 |  -35965 |      68802 |   42852 |           1 |      35 |       35 | False   |
| M7     | profit |      921 |  -21327 |      68802 |   40280 |           0 |      35 |       35 | False   |
| M7     | both   |       13 |  -16238 |      68802 |   67488 |           0 |       7 |       35 | False   |
| U7     | loss   |    11150 |  -49721 |      42226 |   33074 |           1 |      35 |       35 | False   |
| U7     | profit |      976 | -173957 |      42226 |   57483 |           0 |      35 |       35 | False   |
| U7     | both   |       13 |  -37600 |      42226 |   42226 |           0 |       3 |       35 | False   |
| A7     | loss   |    11029 |  -32911 |      14181 |   11878 |           0 |      35 |       35 | False   |
| A7     | profit |      580 |  -49969 |      14181 |   19480 |           0 |      35 |       35 | False   |
| A7     | both   |       13 |  -16568 |      14181 |   14181 |           0 |      23 |       35 | False   |
| H7     | loss   |    11013 |  -93264 |      57397 |   34472 |           0 |      35 |       35 | False   |
| H7     | profit |      929 |  -60835 |      57397 |   51334 |           0 |      35 |       35 | False   |
| H7     | both   |       13 |  -77850 |      57397 |   72445 |           0 |      18 |       35 | False   |
| O7     | loss   |     6272 |  -44366 |       7469 |    9479 |           0 |      35 |       35 | False   |
| O7     | profit |      454 |  -19808 |       7469 |    7469 |           0 |      35 |       35 | False   |
| O7     | both   |       13 |  -19861 |       7469 |    7469 |           0 |      27 |       35 | False   |

## Stack view and one rule for all books (first-order, IN-SAMPLE best-of-thousands picks per book: read them against the walk-forward table above, which is negative for almost every book/side)
Per-book picks stacked: L6M maxDD 32,994 vs never-cut 121,381; PRE maxDD 141,395 vs 152,455; L6M dmean 3,878. Best single cell on all books: X1_scale_target ({"m": 0.75, "p": 0.7, "rest": "trail", "x": 10}), L6M maxDD 33,846, dmean 574.

## Plain sentences
- ALL loss: the technique that lowers drawdown most is D3_pullback@after30 ({"X": 20, "ctx": "after30", "pb": 40}); L6M maxDD 54,622 vs 121,381 never-cut (-66,759); it costs 1,361 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.12, the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- ALL profit: the technique that lowers drawdown most is L1_cond ({"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_scale", "cond": "atr_mid"}); L6M maxDD 55,296 vs 121,381 never-cut (-66,085); it earns 7,628 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- ALL both: the technique that lowers drawdown most is CROSS[966d0f8e1e9e+9cdf7469ba89] ({"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba89"}); L6M maxDD 43,078 vs 121,381 never-cut (-78,303); it costs 12,076 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.82, the family p over all cells is 1.00, PRE drawdown is worse than without it. Label no.
- K7 loss: the technique that lowers drawdown most is LBC_adv_best_move ({"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best_move", "mode": "latch", "months": "202304-202611(44)", "pers": 5, "thr": 3.0}); L6M maxDD 8,636 vs 20,902 never-cut (-12,266); it earns 1,136 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- K7 profit: the technique that lowers drawdown most is J3_statescale ({"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "th": 1.5, "x": 10}); L6M maxDD 8,893 vs 20,902 never-cut (-12,009); it earns 1,385 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- K7 both: the technique that lowers drawdown most is CROSS[966d0f8e1e9e+9cdf7469ba89] ({"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba89"}); L6M maxDD 8,298 vs 20,902 never-cut (-12,604); it costs 1,102 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.18, the family p over all cells is 1.00, the purged walk-forward is not positive, PRE drawdown is worse than without it. Label no.
- P7 loss: the technique that lowers drawdown most is D3_pullback@after30 ({"X": 20, "ctx": "after30", "pb": 40}); L6M maxDD 38,077 vs 133,887 never-cut (-95,809); it earns 1,125 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- P7 profit: the technique that lowers drawdown most is H_gated ({"P": [1.0, 2.0, 2.0, 1.0, 0.7, 1.0], "arm": 0.7, "feat": "tot_rel_fast", "secs": 1, "thr": 2}); L6M maxDD 71,485 vs 133,887 never-cut (-62,402); it earns 3,507 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- P7 both: the technique that lowers drawdown most is CROSS[966d0f8e1e9e+9cdf7469ba89] ({"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba89"}); L6M maxDD 26,813 vs 133,887 never-cut (-107,073); it costs 5,097 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, PRE drawdown is worse than without it. Label no.
- M7 loss: the technique that lowers drawdown most is F3_stop_extreme ({"X": 10, "k": 0}); L6M maxDD 13,450 vs 44,425 never-cut (-30,976); it earns 1,349 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- M7 profit: the technique that lowers drawdown most is H_thick ({"P": [1.0, 3.0, 1.3, 1.0, 0.1, 1.0], "arm": 0.1, "feat": "tot_rel_slow", "secs": 1, "thr": 1.3}); L6M maxDD 14,461 vs 44,425 never-cut (-29,964); it earns 1,214 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- M7 both: the technique that lowers drawdown most is CROSS[966d0f8e1e9e+9cdf7469ba89] ({"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba89"}); L6M maxDD 34,844 vs 44,425 never-cut (-9,582); it earns 267 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.52, the family p over all cells is 1.00, the purged walk-forward is not positive, PRE drawdown is worse than without it. Label no.
- U7 loss: the technique that lowers drawdown most is LBC_ice_ag_w10 ({"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "ice_ag_w10", "mode": "cur", "months": "202304-202611(44)", "pers": 5, "thr": 4.0}); L6M maxDD 6,061 vs 21,561 never-cut (-15,500); it earns 482 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- U7 profit: the technique that lowers drawdown most is H_pcthour ({"P": [3.0, 0.3, 120.0, 510.0], "pct": 0.3, "window": "ldn"}); L6M maxDD 8,700 vs 21,561 never-cut (-12,861); it costs 104 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- U7 both: the technique that lowers drawdown most is CROSS[e7c0088d2553+2c9eb23c8f1d] ({"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f1d"}); L6M maxDD 12,841 vs 21,561 never-cut (-8,720); it costs 1,411 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.12, the family p over all cells is 1.00, PRE drawdown is worse than without it. Label no.
- A7 loss: the technique that lowers drawdown most is D3_pullback ({"X": 20, "pb": 50}); L6M maxDD 4,760 vs 12,461 never-cut (-7,701); it earns 606 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- A7 profit: the technique that lowers drawdown most is H_pcthour ({"P": [3.0, 0.4, 1080.0, 120.0], "pct": 0.4, "window": "asia"}); L6M maxDD 3,268 vs 12,461 never-cut (-9,192); it earns 349 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- A7 both: the technique that lowers drawdown most is CROSS[e7c0088d2553+2c9eb23c8f1d] ({"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f1d"}); L6M maxDD 4,415 vs 12,461 never-cut (-8,046); it earns 301 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00. Label CANDIDATE-DD.
- H7 loss: the technique that lowers drawdown most is LBC_sweep8_w10 ({"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w10", "mode": "latch", "months": "202304-202611(44)", "pers": 3, "thr": 4.0}); L6M maxDD 4,988 vs 15,477 never-cut (-10,489); it earns 11 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- H7 profit: the technique that lowers drawdown most is H_mom ({"P": [1.0, 9.0, 0.0, 1.0, 0.25, -1.0], "arm": 0.25, "feat": "vel30<=", "secs": 1, "thr": 0}); L6M maxDD 5,961 vs 15,477 never-cut (-9,516); it costs 1,133 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- H7 both: the technique that lowers drawdown most is CROSS[e3e1c7125354+e1e6e2a7d150] ({"book": "H7", "loss": "e3e1c7125354", "profit": "e1e6e2a7d150"}); L6M maxDD 7,541 vs 15,477 never-cut (-7,936); it costs 1,679 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.36, the family p over all cells is 1.00, PRE drawdown is worse than without it. Label no.
- O7 loss: the technique that lowers drawdown most is LBC_dtot8_rel_w15 ({"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dtot8_rel_w15", "mode": "latch", "months": "202304-202611(44)", "pers": 1, "thr": -0.044443998485803604}); L6M maxDD 2,725 vs 7,469 never-cut (-4,743); it earns 273 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00. Label CANDIDATE-DD.
- O7 profit: the technique that lowers drawdown most is I_step ({"P": [7.0, 10.0, 1.0], "lag": 1, "step": 10}); L6M maxDD 4,420 vs 7,469 never-cut (-3,048); it earns 164 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- O7 both: the technique that lowers drawdown most is CROSS[966d0f8e1e9e+9cdf7469ba89] ({"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba89"}); L6M maxDD 2,425 vs 7,469 never-cut (-5,043); it earns 17 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive, PRE drawdown is worse than without it. Label LEAD.
- X3 loss: the technique that lowers drawdown most is A_pulled ({"W": 30, "arm": "fixed", "armval": 10, "blk": "A", "cancels": "net", "maeW": 0, "med": "e001", "mult": 120, "newmae": 0, "pers": 2, "pulled": "own"}); L6M maxDD 0 vs 664 never-cut (-664); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.49, the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- X3 profit: the technique that lowers drawdown most is K2_atrtarget ({"c": 6}); L6M maxDD 0 vs 664 never-cut (-664); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- X3 both: the technique that lowers drawdown most is CROSS[e7c0088d2553+2c9eb23c8f1d] ({"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f1d"}); L6M maxDD 0 vs 664 never-cut (-664); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.52, the family p over all cells is 1.00, no walk-forward has been run. Label CANDIDATE-DD.
- X4 loss: the technique that lowers drawdown most is A_pulled ({"W": 3, "arm": "fixed", "armval": 20, "blk": "A", "cancels": "net", "maeW": 0, "med": "e001", "mult": 15, "newmae": 0, "pers": 3, "pulled": "own"}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X4 profit: the technique that lowers drawdown most is J3_statescale ({"a": 0.4, "f": "tot_rel_slow", "rest": "hold", "s": 10, "th": 1.5}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X4 both: the technique that lowers drawdown most is CROSS[afa4804db573+e1e6e2a7d150] ({"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d150"}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X5 loss: the technique that lowers drawdown most is A_pulled ({"W": 15, "arm": "fixed", "armval": 15, "blk": "A", "cancels": "net", "maeW": 15, "med": "e001", "mult": 15, "newmae": 1, "pers": 1, "pulled": "own"}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X5 profit: the technique that lowers drawdown most is K1_target ({"m": 1.1}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.
- X5 both: the technique that lowers drawdown most is CROSS[afa4804db573+e1e6e2a7d150] ({"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d150"}); L6M maxDD 0 vs 0 never-cut (-0); it earns 0 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, no walk-forward has been run. Label no.

---
universe U2: U2 = full S1b tick-close never-cut (43 months), U1 kept on disk (universe_U1/) as screen-only
