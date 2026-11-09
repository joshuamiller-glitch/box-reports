# DS3_TH_EXHAUST - every exit technique, both sides, drawdown first (auto-generated 2026-11-09 06:55Z)
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
QUARANTINE: 0 cells of agent PHI from the flawed first scoring pass (nfire == ntrades, leg 2 fed back into a new Outcome) are excluded from every table, nulls and the family max-stat; they stay on disk. H/I (take / trail) section: corrected cells in the ledger 0 of 0 expected so far.
Cells scored: 15700; families: ['A', 'A_pulled', 'B_book', 'C_flow', 'D', 'E', 'F', 'G', 'J_scale', 'K_target', 'L_cond', 'L_cross', 'L_learned', 'X_cross']. Labels: {'no': 79788, 'CANDIDATE-DD': 24220, 'LEAD': 6399, 'CANDIDATE-DD FAILS-LIVE-WEEK': 4100, 'LEAD FAILS-LIVE-WEEK': 1520}

## ALL
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL never-cut level | 35,468 | 67,950 | 37,850 | 31,832 | 16,868 | 12,409 | 14,153 | 2,398 | 121,381 | 152,455 | 77,580 |
| ALL LIVE REF S1b-COMB level | 11,588 | 45,231 | 24,973 | 28,018 | 16,943 | 18,454 | 12,266 | 1,937 | 82,873 | 144,002 | 190,560 |

### ALL loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback@after30 | {"X": 20, "ctx": "after30", "pb": 40} | -29,431 | -15,996 | -7,144 | 1,877 | -4,042 | -7,476 | -10,031 | -147 | 54,622 / 121,381 | 100,443 / 152,455 | 179,120 / 77,580 | 10,642 | 0.12 | 1.00 / 0.95 | -125,733 | -1,645 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 20, "blk": "C", "cancels" | -4,054 | -11,920 | -7,011 | 1,446 | 172 | 1,824 | -5,195 | 1,484 | 61,695 / 121,381 | 83,161 / 152,455 | 149,247 / 77,580 | 8,239 | 0.03 | 1.00 / 0.95 | -970,636 | -8,894 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_dlt_med_w10 | {"arm": 25.0, "arm_kind": "abs", "dir": -1, "feat": "dlt_med | 3,607 | 8,880 | 735 | 6,103 | -182 | -4,866 | -4,549 | 1,354 | 62,188 / 121,381 | 81,956 / 152,455 | 208,614 / 77,580 | 6,892 | 0.11 | 1.00 / 0.95 | -188,044 | 2,744 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| D4_eff@blk_both_30 | {"X": 35, "ctx": "blk_both_30", "thr": 0.3, "w": 60} | -12,105 | -10,424 | -6,453 | 1,304 | -678 | -1,475 | -8,918 | 788 | 62,613 / 121,381 | 120,569 / 152,455 | 136,651 / 77,580 | 9,632 | 0.02 | 1.00 / 0.95 | -57,654 | -8,586 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_dlt_med_w60 | {"arm": 0.3, "arm_kind": "pct", "dir": -1, "feat": "dlt_med_ | -6,116 | -6,312 | 1,416 | 2,233 | -3,067 | -3,657 | -7,592 | -1,123 | 62,740 / 121,381 | 125,684 / 152,455 | 167,175 / 77,580 | 7,954 | 0.02 | 1.00 / 0.95 | -331,761 | -13,584 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### ALL profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 1,664 | 2,177 | 4,874 | 3,824 | 2,515 | 264 | -1,426 | -501 | 55,296 / 121,381 | 117,149 / 152,455 | 250,937 / 77,580 | 1,789 | 0.02 | 1.00 / 0.94 | -216,598 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 1,905 | 2,072 | 5,258 | 3,836 | 2,563 | 166 | -1,514 | -574 | 56,444 / 121,381 | 115,335 / 152,455 | 251,176 / 77,580 | 1,789 | 0.04 | 1.00 / 0.94 | -216,598 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -2,493 | -1,781 | 2,031 | 1,299 | -1,659 | -1,045 | -5,749 | -1,200 | 57,492 / 121,381 | 120,670 / 152,455 | 258,667 / 77,580 | 3,720 | 0.04 | 1.00 / 0.94 | -216,598 | -3,806 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -1,935 | -1,568 | 2,331 | 1,535 | -1,548 | -898 | -5,731 | -1,301 | 59,365 / 121,381 | 119,860 / 152,455 | 265,450 / 77,580 | 3,720 | 0.04 | 1.00 / 0.95 | -216,598 | -3,806 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 40}, "base_tech":  | 8,004 | -6,918 | -1,619 | 3,134 | 2,579 | 798 | -1,902 | -615 | 69,132 / 121,381 | 115,652 / 152,455 | 219,670 / 77,580 | 1,664 | 0.04 | 1.00 / 0.95 | -216,598 | -5,288 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### ALL both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -39,428 | -11,483 | -416 | -8,838 | -11,557 | -12,911 | -11,867 | -3,167 | 43,078 / 121,381 | 225,516 / 152,455 | 12,283 / 77,580 | 12,235 | 0.82 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -32,560 | -20,213 | -10,879 | -9,397 | -11,899 | -9,772 | -10,393 | -8 | 77,173 / 121,381 | 151,329 / 152,455 | -4,977 / 77,580 | 10,882 | 0.45 | 1.00 / 0.95 | 0 |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -30,130 | -35,888 | -28,786 | -20,418 | -24,218 | -17,361 | -20,761 | -5,068 | 232,660 / 121,381 | 546,408 / 152,455 | -253,661 / 77,580 | 14,101 | 1.00 | 1.00 / 1.00 | 0 |  | S1 | no |
| CROSS[cd4451a22198+87cd2ee2381f] | {"book": "K7", "loss": "cd4451a22198", "profit": "87cd2ee238 | -59,010 | -32,978 | -25,254 | -36,190 | -32,233 | -22,784 | -22,355 | -9,661 | 406,212 / 121,381 | 673,184 / 152,455 | -526,357 / 77,580 | 13,276 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[e3877cab15a7+55aab8e87e08] | {"book": "O7", "loss": "e3877cab15a7", "profit": "55aab8e87e | -48,196 | -25,718 | -20,377 | -35,754 | -29,982 | -20,594 | -25,227 | -7,270 | 427,687 / 121,381 | 842,588 / 152,455 | -526,616 / 77,580 | 15,443 | 1.00 | 1.00 / - |  |  | S1 | no |

## K7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 never-cut level | 4,952 | 8,594 | 3,229 | 4,245 | 2,469 | 1,911 | 2,803 | -80 | 20,902 | 26,707 | 1,791 |
| K7 LIVE REF S1b-COMB level | 7,873 | 8,450 | 3,436 | 3,530 | 2,241 | 3,740 | 2,616 | -164 | 41,849 | 23,073 | -20,339 |

### K7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_adv_best_move | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best | 909 | 2,784 | 3,589 | 1,123 | -23 | 1,148 | -1,202 | 9 | 8,636 / 20,902 | 23,900 / 26,707 | 28,728 / 1,791 | 3,051 | 0.05 | 1.00 / 0.99 | -107,558 | 126 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_tot_rel_base | {"arm": 40.0, "arm_kind": "abs", "dir": -1, "feat": "tot_rel | 920 | 1,852 | 2,089 | 839 | -207 | -14 | -425 | -99 | 9,396 / 20,902 | 25,381 / 26,707 | 39,604 / 1,791 | 2,191 | 0.03 | 1.00 / 1.00 | -53,344 | 879 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_imb_ag10 | {"arm": 0.45, "arm_kind": "pct", "dir": 1, "feat": "imb_ag10 | -302 | 1,268 | 1,522 | 683 | 120 | 32 | -275 | 228 | 9,560 / 20,902 | 21,646 / 26,707 | 18,437 / 1,791 | 1,148 | 0.02 | 1.00 / 1.00 |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_dlt_med_w60 | {"arm": 15.0, "arm_kind": "abs", "dir": -1, "feat": "dlt_med | 2,476 | 2,037 | 2,834 | 683 | 310 | 1,694 | -1,484 | -187 | 9,563 / 20,902 | 17,229 / 26,707 | 23,178 / 1,791 | 3,487 | 0.38 | 1.00 / 1.00 | -74,266 | -1,734 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| LBC_dtot8_w5 | {"arm": 30.0, "arm_kind": "abs", "dir": -1, "feat": "dtot8_w | 1,834 | 1,339 | 1,765 | 1,322 | 432 | -95 | -630 | -105 | 9,940 / 20,902 | 22,345 / 26,707 | 33,119 / 1,791 | 1,869 | 0.85 | 1.00 / 1.00 |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |

### K7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, " | 1,717 | 728 | 1,963 | 666 | -5 | 100 | -673 | 390 | 8,893 / 20,902 | 23,892 / 26,707 | 16,614 / 1,791 | 636 | 0.02 | 1.00 / 0.91 | -41,710 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "trail", "x": 10} | 2,081 | -874 | 1,144 | 277 | -389 | -1,516 | -399 | 463 | 9,147 / 20,902 | 17,406 / 26,707 | 39,575 / 1,791 | 969 | 0.04 | 1.00 / 0.99 | -34,760 | -40 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 5} | 2,286 | -761 | 1,258 | 270 | -409 | -1,718 | -412 | 480 | 9,389 / 20,902 | 17,644 / 26,707 | 40,236 / 1,791 | 689 | 0.04 | 1.00 / 1.00 | -46,439 | 56 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J1_scale | {"p": 0.5, "rest": "trail", "x": 10} | 2,146 | -846 | 1,106 | 205 | -427 | -1,502 | -395 | 479 | 9,411 / 20,902 | 18,094 / 26,707 | 37,916 / 1,791 | 689 | 0.04 | 1.00 / 0.99 | -46,439 | -472 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 1.25, "p": 0.5, "rest": "trail", "x": 10} | 2,235 | -811 | 1,130 | 204 | -422 | -1,556 | -399 | 488 | 9,411 / 20,902 | 18,094 / 26,707 | 37,734 / 1,791 | 969 | 0.04 | 1.00 / 0.99 | -34,760 | -472 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### K7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -3,325 | -599 | 1,945 | -1,115 | -1,464 | 399 | -1,816 | -323 | 8,298 / 20,902 | 43,335 / 26,707 | 4,693 / 1,791 | 4,112 | 0.18 | 1.00 / - |  |  | S1 | no |
| CROSS[cd4451a22198+87cd2ee2381f] | {"book": "K7", "loss": "cd4451a22198", "profit": "87cd2ee238 | -5,570 | -963 | 1,904 | -1,755 | -2,174 | -323 | -2,709 | -663 | 12,829 / 20,902 | 52,166 / 26,707 | -13,392 / 1,791 | 4,084 | 0.42 | 1.00 / - |  |  | S1 | no |
| CROSS[e0fb6a9abc57+8e7c342b397d] | {"book": "M7", "loss": "e0fb6a9abc57", "profit": "8e7c342b39 | -4,163 | -4,573 | -1,407 | -4,158 | -3,263 | -336 | -3,580 | -1,455 | 31,237 / 20,902 | 69,931 / 26,707 | -44,587 / 1,791 | 5,527 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | -4,471 | -69 | -51 | -2,182 | -2,464 | -180 | -2,640 | -234 | 37,843 / 20,902 | 53,526 / 26,707 | -30,807 / 1,791 | 3,296 | 0.97 | 1.00 / 1.00 | -21,028 |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 528 | -2,881 | -1,910 | -876 | -1,378 | 1,268 | -1,570 | 464 | 43,996 / 20,902 | 30,048 / 26,707 | -4,398 / 1,791 | 3,516 | 0.97 | 1.00 / 1.00 | -63,757 |  | S1 | no |

## P7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| P7 never-cut level | 33,625 | 22,555 | 13,873 | 11,894 | 8,318 | 5,178 | 8,641 | -118 | 133,887 | 109,442 | -29,902 |
| P7 LIVE REF S1b-COMB level | 5,700 | 18,966 | 12,054 | 14,708 | 10,485 | 11,144 | 6,746 | -2 | 96,490 | 106,914 | 53,844 |

### P7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback@after30 | {"X": 20, "ctx": "after30", "pb": 40} | -33,284 | -14,544 | -9,266 | 3,938 | -2,898 | -2,253 | -5,504 | 424 | 38,077 / 133,887 | 57,033 / 109,442 | 95,825 / -29,902 | 2,730 | 0.02 | 1.00 / 0.67 | -244,967 | -3,790 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D0_plain@after30 | {"X": 30, "ctx": "after30"} | -26,936 | -13,786 | -8,177 | 2,195 | -2,050 | 843 | -5,691 | 703 | 45,910 / 133,887 | 88,649 / 109,442 | 86,435 / -29,902 | 2,600 | 0.02 | 1.00 / 0.75 | -188,556 | 991 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 25, "blk": "A", "cancels" | -18,744 | -19,970 | -11,421 | 892 | -1,176 | 9,213 | -2,698 | -728 | 49,145 / 133,887 | 87,956 / 109,442 | 56,330 / -29,902 | 2,017 | 0.02 | 1.00 / 0.74 | -541,581 | -15,057 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "C", "cancels" | -16,198 | -12,587 | -6,208 | 8,451 | 3,214 | 2,334 | -4,292 | 329 | 50,418 / 133,887 | 97,168 / 109,442 | 161,266 / -29,902 | 2,528 | 0.37 | 1.00 / 0.97 | -541,581 | -5,309 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "C", "cancels" | -16,198 | -12,390 | -6,190 | 8,227 | 2,893 | 1,230 | -4,242 | 634 | 50,418 / 133,887 | 95,628 / 109,442 | 154,417 / -29,902 | 2,539 | 0.31 | 1.00 / 0.97 | -541,581 | -5,309 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

### P7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -841 | 678 | 1,582 | 5,082 | 2,987 | 766 | -1,380 | -800 | 82,296 / 133,887 | 92,199 / 109,442 | 76,006 / -29,902 | 1,006 | 0.02 | 1.00 / 1.00 | -186,434 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -1,382 | 528 | 1,972 | 5,069 | 3,016 | 754 | -1,412 | -876 | 83,539 / 133,887 | 91,553 / 109,442 | 78,160 / -29,902 | 1,006 | 0.04 | 1.00 / 1.00 | -186,434 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 40}, "base_tech":  | 3,029 | -7,152 | -3,235 | 1,621 | 1,825 | 2,116 | -1,081 | -832 | 87,937 / 133,887 | 97,537 / 109,442 | 63,228 / -29,902 | 946 | 0.04 | 1.00 / 1.00 | -186,434 | -5,288 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech":  | -646 | -184 | 889 | 515 | 1,200 | 2,100 | -1,148 | -1,053 | 88,539 / 133,887 | 99,024 / 109,442 | 72,153 / -29,902 | 946 | 0.04 | 1.00 / 1.00 | -186,434 | -3,688 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 2, "p": 0.7, "rest": "be"}, "base_tech": "J1_ | 1,611 | 1,121 | 2,061 | 1,541 | 1,787 | 1,989 | -1,197 | -624 | 92,512 / 133,887 | 99,394 / 109,442 | 63,452 / -29,902 | 946 | 0.04 | 1.00 / 1.00 | -186,434 | -6,038 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### P7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -33,626 | -8,066 | -2,745 | -2,283 | -6,501 | -7,547 | -9,178 | -1,662 | 26,813 / 133,887 | 178,169 / 109,442 | 20,561 / -29,902 | 3,178 | 0.03 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -30,791 | -13,682 | -8,608 | -2,939 | -7,029 | -6,418 | -8,098 | -986 | 45,473 / 133,887 | 152,285 / 109,442 | -16,581 / -29,902 | 2,981 | 0.03 | 1.00 / 0.35 | 0 |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -35,154 | -32,544 | -26,288 | -15,368 | -18,497 | -15,180 | -12,938 | -2,932 | 238,845 / 133,887 | 459,309 / 109,442 | -279,528 / -29,902 | 4,163 | 1.00 | 1.00 / 1.00 | 0 |  | S1 | no |
| CROSS[63c14ae16fd1+2dd5c144c1a7] | {"book": "U7", "loss": "63c14ae16fd1", "profit": "2dd5c144c1 | -49,137 | -24,819 | -20,957 | -19,572 | -19,200 | -12,679 | -12,481 | -3,144 | 249,975 / 133,887 | 466,013 / 109,442 | -396,572 / -29,902 | 4,420 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[e3e1c7125354+e1e6e2a7d150] | {"book": "H7", "loss": "e3e1c7125354", "profit": "e1e6e2a7d1 | -40,406 | -20,813 | -19,226 | -21,777 | -19,155 | -13,629 | -14,642 | -3,735 | 275,650 / 133,887 | 606,326 / 109,442 | -389,686 / -29,902 | 3,740 | 1.00 | 1.00 / - |  |  | S1 | no |

## M7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7 never-cut level | 419 | 3,250 | 247 | 410 | 128 | 154 | 90 | -128 | 44,425 | 50,321 | -68,299 |
| M7 LIVE REF S1b-COMB level | 40 | 2,590 | -776 | -227 | -639 | 601 | 523 | -64 | 46,547 | 25,812 | -64,633 |

### M7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3_stop_extreme | {"X": 10, "k": 0} | -1,522 | -1,232 | -1,921 | 737 | 108 | -1,018 | -812 | -447 | 13,450 / 44,425 | 45,329 / 50,321 | -26,663 / -68,299 | 3,214 | 0.03 | 1.00 / 0.04 | -12,478 | -1,985 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 10, "blk": "A", "cancels" | 2,543 | 1,840 | 3,151 | 1,741 | 14 | -865 | 238 | 113 | 13,485 / 44,425 | 31,252 / 50,321 | -12,409 / -68,299 | 1,195 | 0.02 | 1.00 / 0.44 | -18,261 | 724 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| A_pulled | {"W": 1, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | -878 | -1,089 | 756 | 527 | -316 | -939 | -59 | 26 | 14,218 / 44,425 | 26,832 / 50,321 | -36,027 / -68,299 | 2,050 | 0.72 | 1.00 / 0.04 | -18,261 | -2,838 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| LBC_cps_rel_w10 | {"arm": 0.3, "arm_kind": "pct", "dir": 1, "feat": "cps_rel_w | -350 | -3,309 | -795 | 554 | -90 | -912 | -167 | -860 | 14,306 / 44,425 | 37,643 / 50,321 | -34,516 / -68,299 | 2,397 | 0.06 | 1.00 / 0.01 | -17,132 | -1,135 | S1 | CANDIDATE-DD [rec-FAIL wf-FAIL plc-ok exposure] |
| LBC_cps_rel_w10 | {"arm": 0.3, "arm_kind": "pct", "dir": 1, "feat": "cps_rel_w | 288 | -3,350 | -833 | 535 | -145 | -136 | -674 | -713 | 16,117 / 44,425 | 46,632 / 50,321 | -32,328 / -68,299 | 2,493 | 0.60 | 1.00 / 0.08 | -17,132 | -2,864 | S1 | CANDIDATE-DD [rec-FAIL wf-FAIL plc-FAIL exposure] |

### M7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| J1_scale | {"p": 0.3, "rest": "trail", "x": 10} | -2,365 | -1,516 | -1,887 | 405 | 519 | -55 | 326 | -83 | 25,111 / 44,425 | 29,613 / 50,321 | -46,302 / -68,299 | 545 | 0.02 | 1.00 / 1.00 | 1,792 | -382 | S1 | CANDIDATE-DD [rec-FAIL wf-ok plc-ok] |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 5} | -2,493 | -1,577 | -1,897 | 451 | 551 | -117 | 138 | -102 | 25,462 / 44,425 | 29,064 / 50,321 | -44,834 / -68,299 | 545 | 0.04 | 1.00 / 1.00 | 1,792 | -452 | S1 | CANDIDATE-DD [rec-FAIL wf-ok plc-ok] |
| J1_scale | {"p": 0.3, "rest": "trail", "x": 20} | -2,620 | -1,616 | -2,047 | 314 | 426 | -268 | 199 | -102 | 28,225 / 44,425 | 34,097 / 50,321 | -49,879 / -68,299 | 545 | 0.08 | 1.00 / 1.00 | 1,792 | -939 | S1 | CANDIDATE-DD [rec-FAIL wf-ok plc-ok] |
| J1_scale | {"p": 0.4, "rest": "trail", "x": 5} | -1,864 | -1,116 | -1,545 | 451 | 715 | -110 | 141 | -237 | 29,534 / 44,425 | 41,163 / 50,321 | -49,017 / -68,299 | 505 | 0.08 | 1.00 / 1.00 | 1,792 | -1,747 | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok] |
| J1_scale | {"b": 2, "p": 0.3, "rest": "be"} | -2,285 | -1,458 | -1,856 | 292 | 375 | -58 | 42 | 271 | 29,683 / 44,425 | 34,337 / 50,321 | -51,921 / -68,299 | 545 | 0.08 | 1.00 / 1.00 | 1,792 | 443 | S1 | CANDIDATE-DD [rec-FAIL wf-ok plc-ok] |

### M7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -1,143 | -1,185 | -352 | -345 | -560 | -318 | -689 | 5 | 34,844 / 44,425 | 66,902 / 50,321 | -47,794 / -68,299 | 2,491 | 0.52 | 1.00 / - |  |  | S1 | no |
| CROSS[e0fb6a9abc57+8e7c342b397d] | {"book": "M7", "loss": "e0fb6a9abc57", "profit": "8e7c342b39 | -1,942 | -1,859 | -53 | -492 | -1,022 | -2,671 | -1,375 | -933 | 35,034 / 44,425 | 84,737 / 50,321 | -45,579 / -68,299 | 3,296 | 0.42 | 1.00 / - |  |  | S1 | no |
| CROSS[cd4451a22198+87cd2ee2381f] | {"book": "K7", "loss": "cd4451a22198", "profit": "87cd2ee238 | -934 | -2,709 | -1,182 | -203 | -743 | -841 | -846 | -504 | 41,584 / 44,425 | 74,700 / 50,321 | -50,616 / -68,299 | 2,500 | 0.91 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -709 | -463 | -247 | -1,778 | -1,746 | 229 | -1,355 | -543 | 47,665 / 44,425 | 113,002 / 50,321 | -68,134 / -68,299 | 2,663 | 1.00 | 1.00 / 1.00 | -22,118 |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -1,042 | -1,541 | -75 | -825 | -965 | -1,299 | -466 | 98 | 50,392 / 44,425 | 55,729 / 50,321 | -61,893 / -68,299 | 2,190 | 1.00 | 1.00 / 0.97 | -21,584 |  | S1 | no |

## U7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| U7 never-cut level | -4,186 | 275 | -125 | 3,207 | 1,811 | 1,724 | 1,437 | 1,354 | 21,561 | 42,226 | 120 |
| U7 LIVE REF S1b-COMB level | -3,377 | 1,858 | 1,576 | 3,562 | 2,081 | 2,437 | 1,419 | 1,157 | 16,419 | 39,155 | 8,146 |

### U7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "C", "cancels" | 4,731 | 2,325 | 1,591 | 894 | 1,188 | 1,309 | -33 | 553 | 7,335 / 21,561 | 37,858 / 42,226 | 21,476 / 120 | 430 | 0.02 | 1.00 / 0.98 | -129,230 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_cps_rel_w10 | {"arm": 0.3, "arm_kind": "pct", "dir": 1, "feat": "cps_rel_w | 4,182 | 654 | 990 | 584 | 771 | -1,528 | -1,200 | -561 | 7,524 / 21,561 | 27,019 / 42,226 | 35,085 / 120 | 879 | 0.02 | 1.00 / 0.99 | -96,400 | 2,304 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_cps_rel_w30 | {"arm": 0.3, "arm_kind": "pct", "dir": 1, "feat": "cps_rel_w | 3,040 | -701 | 265 | 67 | 360 | -1,253 | -1,682 | -300 | 7,703 / 21,561 | 42,355 / 42,226 | 19,651 / 120 | 947 | 0.03 | 1.00 / 0.97 | -95,444 | 2,109 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_cps_rel_w30 | {"arm": 0.3, "arm_kind": "pct", "dir": 1, "feat": "cps_rel_w | 3,902 | -336 | 472 | 200 | 412 | -1,336 | -1,686 | -368 | 7,763 / 21,561 | 43,056 / 42,226 | 24,231 / 120 | 943 | 0.05 | 1.00 / 0.98 | -95,444 | 2,304 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "C", "cancels" | 4,219 | 1,896 | 1,221 | 652 | 1,126 | 1,032 | -43 | 455 | 7,821 / 21,561 | 40,947 / 42,226 | 16,988 / 120 | 397 | 0.02 | 1.00 / 0.98 | -129,230 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### U7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X2_target_trail | {"arm": 0.7, "m": 2, "x": 20} | 6,557 | -148 | 1,992 | 551 | 525 | -1,411 | -704 | -575 | 10,319 / 21,561 | 38,921 / 42,226 | 20,588 / 120 | 849 | 0.03 | 1.00 / 1.00 | -76,727 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X1_scale_target | {"m": 2, "p": 0.7, "rest": "trail", "x": 20} | 4,928 | -1,147 | 1,772 | 600 | 502 | -744 | -359 | -270 | 11,277 / 21,561 | 30,968 / 42,226 | 28,281 / 120 | 1,135 | 0.04 | 1.00 / 1.00 | -59,612 | -1,085 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 20} | 3,419 | -1,642 | 1,083 | 266 | 347 | -1,708 | -177 | -229 | 11,660 / 21,561 | 25,905 / 42,226 | 21,130 / 120 | 1,135 | 0.02 | 1.00 / 1.00 | -59,612 | -1,990 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X1_scale_target | {"m": 0.75, "p": 0.7, "rest": "trail", "x": 10} | 3,471 | -1,795 | 1,018 | 203 | 284 | -1,673 | -124 | -183 | 12,029 / 21,561 | 24,988 / 42,226 | 18,811 / 120 | 1,135 | 0.02 | 1.00 / 1.00 | -59,612 | -1,990 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| L1_cond | {"base": {"p": 0.7, "rest": "trail", "x": 20}, "base_tech":  | 2,836 | -1,040 | 967 | 1,250 | 582 | 89 | -538 | -316 | 12,063 / 21,561 | 31,646 / 42,226 | 35,284 / 120 | 462 | 0.08 | 1.00 / 1.00 | -55,326 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### U7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 1,141 | -1,906 | -1,782 | -1,284 | -1,749 | -1,232 | -2,182 | -1,370 | 12,841 / 21,561 | 78,568 / 42,226 | -22,711 / 120 | 1,150 | 0.12 | 1.00 / 0.96 | 0 |  | S1 | no |
| CROSS[63c14ae16fd1+2dd5c144c1a7] | {"book": "U7", "loss": "63c14ae16fd1", "profit": "2dd5c144c1 | 5,250 | 1,759 | 1,036 | -1,086 | -1,175 | -1,969 | -3,078 | -963 | 16,992 / 21,561 | 150,582 / 42,226 | -23,365 / 120 | 1,282 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 739 | -2,641 | -1,533 | -1,539 | -790 | -1,196 | -952 | 453 | 18,512 / 21,561 | 51,925 / 42,226 | -36,857 / 120 | 805 | 0.48 | 1.00 / 1.00 | -6,381 |  | S1 | no |
| CROSS[e3877cab15a7+55aab8e87e08] | {"book": "O7", "loss": "e3877cab15a7", "profit": "55aab8e87e | 1,935 | -4,174 | -2,504 | -4,352 | -2,926 | -1,692 | -2,200 | -1,059 | 25,307 / 21,561 | 63,301 / 42,226 | -48,700 / 120 | 1,076 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[e3e1c7125354+e1e6e2a7d150] | {"book": "H7", "loss": "e3e1c7125354", "profit": "e1e6e2a7d1 | 609 | -4,114 | -2,685 | -3,644 | -2,570 | -1,864 | -2,317 | -1,011 | 27,862 / 21,561 | 62,000 / 42,226 | -57,929 / 120 | 1,074 | 1.00 | 1.00 / - |  |  | S1 | no |

## A7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| A7 never-cut level | 389 | -97 | -190 | 601 | 538 | -81 | 989 | 207 | 12,461 | 6,089 | -17,069 |
| A7 LIVE REF S1b-COMB level | -1,287 | 217 | 169 | 821 | 731 | -228 | 937 | 240 | 8,518 | 7,325 | -11,915 |

### A7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback | {"X": 20, "pb": 50} | 34 | 855 | 467 | 511 | 183 | 304 | -146 | 183 | 4,760 / 12,461 | 5,445 / 6,089 | -6,160 / -17,069 | 700 | 0.02 | 1.00 / 0.60 | -12,489 | -1,314 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D3_pullback | {"X": 15, "pb": 50} | -11 | 288 | 199 | 129 | 24 | 223 | -207 | 201 | 4,785 / 12,461 | 4,912 / 6,089 | -4,174 / -17,069 | 713 | 0.02 | 1.00 / 0.59 | -12,489 | -1,018 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 20, "blk": "C", "cancels" | -737 | 848 | 651 | 298 | -18 | 306 | -199 | 37 | 4,900 / 12,461 | 5,378 / 6,089 | -11,330 / -17,069 | 521 | 0.11 | 1.00 / 0.59 | -50,405 | -42 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 1, "arm": "fixed", "armval": 15, "blk": "A", "cancels" | -1,359 | 469 | 197 | 60 | -86 | 140 | -263 | -96 | 5,011 / 12,461 | 5,315 / 6,089 | -15,604 / -17,069 | 573 | 0.11 | 1.00 / 0.54 | -50,405 | -1,306 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| A_pulled | {"W": 3, "arm": "fixed", "armval": 20, "blk": "A", "cancels" | -868 | 953 | 693 | 92 | -87 | -196 | -195 | 32 | 5,218 / 12,461 | 6,308 / 6,089 | -13,403 / -17,069 | 477 | 0.02 | 1.00 / 0.57 | -50,405 | -169 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### A7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.6} | 1,706 | -707 | -222 | 171 | -71 | -296 | -119 | -180 | 5,693 / 12,461 | 4,907 / 6,089 | -543 / -17,069 | 785 | 0.02 | 1.00 / 0.76 | -1,340 | 930 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 20} | 435 | -1,645 | -771 | 303 | 80 | -616 | -159 | -145 | 6,463 / 12,461 | 5,050 / 6,089 | -10,528 / -17,069 | 831 | 0.04 | 1.00 / 0.89 | -47,075 |  | S1 | CANDIDATE-DD [rec-FAIL wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 2, "x": 20} | 199 | -1,646 | -809 | 284 | 89 | -641 | -161 | -107 | 7,617 / 12,461 | 5,050 / 6,089 | -12,003 / -17,069 | 831 | 0.04 | 1.00 / 0.95 | -47,075 |  | S1 | CANDIDATE-DD [rec-FAIL wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 1.25, "x": 20} | -15 | -1,826 | -824 | 209 | 21 | -539 | -208 | -145 | 7,663 / 12,461 | 4,701 / 6,089 | -11,892 / -17,069 | 831 | 0.08 | 1.00 / 0.94 | -47,075 |  | S1 | CANDIDATE-DD [rec-FAIL wf-FAIL plc-ok exposure] |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 90} | -1,149 | -81 | -54 | 105 | 67 | -243 | -12 | 0 | 11,375 / 12,461 | 6,089 / 6,089 | -16,207 / -17,069 | 21 | 0.04 | 1.00 / 1.00 | -9,203 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### A7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -907 | 293 | 148 | 521 | 204 | 21 | -232 | 80 | 4,415 / 12,461 | 4,374 / 6,089 | -7,646 / -17,069 | 732 | 0.03 | 1.00 / 0.57 | 4,462 |  | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok exposure] |
| CROSS[d37df9ed0314+8e7c342b397d] | {"book": "M7", "loss": "d37df9ed0314", "profit": "8e7c342b39 | -79 | 1,126 | 656 | 252 | -23 | 302 | -59 | 30 | 6,506 / 12,461 | 5,710 / 6,089 | -13,365 / -17,069 | 453 | 0.06 | 1.00 / 0.76 | -24,127 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | -1,696 | -428 | -114 | -293 | -266 | 279 | -236 | -3 | 10,135 / 12,461 | 5,229 / 6,089 | -17,946 / -17,069 | 591 | 0.76 | 1.00 / 0.81 | -10,659 |  | S1 | no |
| CROSS[e0fb6a9abc57+8e7c342b397d] | {"book": "M7", "loss": "e0fb6a9abc57", "profit": "8e7c342b39 | -2,756 | -591 | -261 | -763 | -484 | 610 | -713 | 51 | 13,144 / 12,461 | 10,762 / 6,089 | -24,434 / -17,069 | 977 | 0.79 | 1.00 / - |  |  | S1 | no |
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -2,783 | -154 | 331 | 34 | -151 | -478 | -283 | 172 | 13,240 / 12,461 | 9,917 / 6,089 | -11,496 / -17,069 | 594 | 0.97 | 1.00 / - |  |  | S1 | no |

## H7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| H7 never-cut level | -88 | 1,778 | -301 | 1,647 | -73 | -2,452 | 1,623 | 103 | 15,477 | 20,667 | -32,750 |
| H7 LIVE REF S1b-COMB level | 3,186 | 1,158 | 406 | 2,545 | 625 | -1,655 | 1,574 | 220 | 8,818 | 19,256 | 11,007 |

### H7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_sweep8_w10 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | 1,289 | 322 | 1,222 | 1,281 | 917 | 834 | -138 | -22 | 4,988 / 15,477 | 15,783 / 20,667 | 6,350 / -32,750 | 338 | 0.02 | 1.00 / 0.73 | -45,009 | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_adv_best_move | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "adv_best | 343 | 157 | -58 | 384 | 822 | 712 | -43 | 137 | 5,048 / 15,477 | 19,458 / 20,667 | -3,411 / -32,750 | 496 | 0.02 | 1.00 / 0.36 | -6,353 | 109 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_adv_best_move | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best | 223 | 97 | -98 | 261 | 772 | 712 | -105 | 118 | 5,048 / 15,477 | 20,484 / 20,667 | -4,679 / -32,750 | 504 | 0.02 | 1.00 / 0.35 | -6,353 | 109 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w60 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 1,550 | 604 | 1,039 | 990 | 614 | 703 | -27 | 83 | 5,146 / 15,477 | 16,156 / 20,667 | 3,037 / -32,750 | 394 | 0.02 | 1.00 / 0.69 | -18,875 | 244 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w30 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 408 | 305 | 474 | 654 | 516 | 871 | -175 | 108 | 5,190 / 15,477 | 15,940 / 20,667 | -922 / -32,750 | 354 | 0.03 | 1.00 / 0.55 | 15,942 | 374 | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok] |

### H7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K1_target | {"m": 0.5} | 1,216 | 752 | 1,333 | 760 | 657 | -170 | -646 | -522 | 7,798 / 15,477 | 12,907 / 20,667 | 7,005 / -32,750 | 761 | 0.02 | 1.00 / 0.84 | -47,880 | 3,175 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 1.5, "x": 10} | 1,421 | 601 | 1,116 | 356 | 341 | -312 | -552 | -319 | 8,561 / 15,477 | 16,400 / 20,667 | -1,011 / -32,750 | 755 | 0.04 | 1.00 / 0.73 | -33,598 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 1.25, "x": 10} | 1,421 | 601 | 1,116 | 356 | 334 | -319 | -613 | -328 | 8,561 / 15,477 | 16,629 / 20,667 | -1,011 / -32,750 | 755 | 0.04 | 1.00 / 0.73 | -33,598 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| X2_target_trail | {"arm": 0.5, "m": 2, "x": 10} | 1,421 | 601 | 1,116 | 356 | 337 | -312 | -487 | -331 | 8,561 / 15,477 | 15,800 / 20,667 | -1,011 / -32,750 | 755 | 0.04 | 1.00 / 0.73 | -33,598 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| L3_tree_profit | {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d | 1,562 | 84 | 603 | 1,206 | 645 | -954 | -365 | 0 | 9,470 / 15,477 | 20,667 / 20,667 | 598 / -32,750 | 207 | 0.24 | 1.00 / 0.99 | 20,188 |  | S1 | CANDIDATE-DD [rec-ok wf-ok plc-FAIL] |

### H7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e3e1c7125354+e1e6e2a7d150] | {"book": "H7", "loss": "e3e1c7125354", "profit": "e1e6e2a7d1 | 833 | 290 | 1,243 | -409 | -277 | 1,160 | -1,332 | -1,073 | 7,541 / 15,477 | 25,504 / 20,667 | -12,559 / -32,750 | 872 | 0.36 | 1.00 / - |  |  | S1 | no |
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | -646 | -413 | 580 | -177 | 257 | 1,924 | 67 | 426 | 9,891 / 15,477 | 19,959 / 20,667 | -16,547 / -32,750 | 603 | 0.24 | 1.00 / - |  |  | S1 | no |
| CROSS[e3877cab15a7+55aab8e87e08] | {"book": "O7", "loss": "e3877cab15a7", "profit": "55aab8e87e | 228 | 288 | 948 | -303 | -12 | 356 | -1,122 | -682 | 9,991 / 15,477 | 23,638 / 20,667 | -10,538 / -32,750 | 869 | 0.94 | 1.00 / - |  |  | S1 | no |
| CROSS[afa4804db573+e1e6e2a7d150] | {"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d1 | -536 | -708 | 210 | -1,609 | -990 | 728 | -1,369 | -784 | 15,597 / 15,477 | 22,528 / 20,667 | -36,028 / -32,750 | 914 | 0.79 | 1.00 / 0.50 | -3,845 |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 423 | -130 | 732 | -234 | 96 | 1,270 | -13 | 365 | 18,057 / 15,477 | 15,996 / 20,667 | -17,809 / -32,750 | 527 | 0.73 | 1.00 / 0.99 | -21,295 |  | S1 | no |

## O7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| O7 never-cut level | -685 | -396 | -65 | 280 | 687 | -245 | 644 | -119 | 7,469 | 5,102 | -9,532 |
| O7 LIVE REF S1b-COMB level | -988 | -446 | -78 | 331 | 651 | -343 | 636 | -147 | 6,656 | 4,532 | -8,247 |

### O7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_dlt_med_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dlt_med | 321 | 309 | 116 | 34 | -308 | 134 | -500 | 165 | 3,243 / 7,469 | 4,699 / 5,102 | -4,802 / -9,532 | 448 | 0.05 | 1.00 / 0.30 | -20,988 | -243 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_dlt_med_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dlt_med | 624 | 479 | 226 | 66 | -216 | 137 | -494 | 130 | 3,600 / 7,469 | 5,318 / 5,102 | -4,838 / -9,532 | 441 | 0.11 | 1.00 / 0.36 | -20,988 | 1,302 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| LBC_sweep8_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 461 | 41 | 400 | 110 | -186 | 223 | -35 | 226 | 3,859 / 7,469 | 4,241 / 5,102 | -4,740 / -9,532 | 220 | 0.03 | 1.00 / 0.45 | -22,094 | 826 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 179 | 301 | 149 | 129 | -133 | 202 | -14 | 124 | 4,019 / 7,469 | 3,820 / 5,102 | -4,654 / -9,532 | 159 | 0.02 | 1.00 / 0.57 | -22,094 | 399 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_tot_rel_base | {"arm": 10.0, "arm_kind": "abs", "dir": -1, "feat": "tot_rel | 178 | 331 | 271 | 145 | -102 | 272 | -308 | -67 | 4,104 / 7,469 | 5,196 / 5,102 | -3,149 / -9,532 | 315 | 0.03 | 1.00 / 0.71 | -10,336 | 404 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### O7 profit
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 150} | 1,208 | 377 | 464 | 27 | -183 | 96 | -54 | -31 | 5,487 / 7,469 | 3,920 / 5,102 | -2,571 / -9,532 | 151 | 0.08 | 1.00 / 1.00 | -6,496 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 0, "level": "prior_day", "lim": 90} | 1,208 | 377 | 464 | 27 | -183 | 96 | -54 | -31 | 5,487 / 7,469 | 3,920 / 5,102 | -2,571 / -9,532 | 151 | 0.02 | 1.00 / 1.00 | -6,496 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 90} | 1,148 | 523 | 531 | 29 | -249 | -38 | -11 | 0 | 5,687 / 7,469 | 3,914 / 5,102 | -3,832 / -9,532 | 128 | 0.04 | 1.00 / 1.00 | -6,496 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| K3_structtarget | {"buf": 2, "level": "prior_day", "lim": 150} | 1,148 | 523 | 531 | 29 | -249 | -38 | -11 | 0 | 5,687 / 7,469 | 3,914 / 5,102 | -3,832 / -9,532 | 128 | 0.04 | 1.00 / 1.00 | -6,496 |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L3_tree_profit | {"arm": 0.15, "features_used_last": ["mae", "d_pd_ahead", "d | 0 | -47 | 52 | 44 | -273 | -296 | 6 | 0 | 7,104 / 7,469 | 4,578 / 5,102 | -7,351 / -9,532 | 76 | 0.60 | 1.00 / 1.00 | 0 |  | S1 | CANDIDATE-DD [rec-ok wf-ok plc-FAIL] |

### O7 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | 366 | 286 | 61 | 68 | -344 | 194 | -603 | 112 | 2,425 / 7,469 | 8,075 / 5,102 | -3,682 / -9,532 | 430 | 0.06 | 1.00 / - |  |  | S1 | LEAD [rec-ok wf-FAIL plc-ok exposure] |
| CROSS[e0fb6a9abc57+8e7c342b397d] | {"book": "M7", "loss": "e0fb6a9abc57", "profit": "8e7c342b39 | 581 | -16 | 199 | 110 | -194 | 219 | -590 | 263 | 2,941 / 7,469 | 9,135 / 5,102 | -2,554 / -9,532 | 431 | 0.06 | 1.00 / - |  |  | S1 | LEAD [rec-ok wf-FAIL plc-ok exposure] |
| CROSS[cd4451a22198+87cd2ee2381f] | {"book": "K7", "loss": "cd4451a22198", "profit": "87cd2ee238 | 510 | -64 | 176 | 37 | -273 | 182 | -582 | 187 | 3,560 / 7,469 | 9,106 / 5,102 | -4,548 / -9,532 | 395 | 0.06 | 1.00 / - |  |  | S1 | LEAD [rec-ok wf-FAIL plc-ok exposure] |
| CROSS[e3877cab15a7+55aab8e87e08] | {"book": "O7", "loss": "e3877cab15a7", "profit": "55aab8e87e | 670 | 499 | 178 | -88 | -519 | 60 | -658 | 10 | 1,915 / 7,469 | 11,683 / 5,102 | -3,519 / -9,532 | 435 | 0.03 | 1.00 / - |  |  | S1 | no |
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | 248 | 151 | -87 | -248 | -657 | -51 | -785 | -74 | 4,786 / 7,469 | 17,226 / 5,102 | -7,262 / -9,532 | 506 | 0.36 | 1.00 / 0.21 | 0 |  | S1 | no |

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
| J1_scale | {"b": 0, "p": 0.9, "rest": "be"} | -60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 904 / 664 | 0 / 0 | -904 / -664 | 2 | 0.83 | 1.00 / - |  |  | S1 | no |
| J1_scale | {"p": 0.9, "rest": "trail", "x": 40} | -60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 904 / 664 | 0 / 0 | -904 / -664 | 2 | 0.83 | 1.00 / - |  |  | S1 | no |
| J1_scale | {"p": 0.9, "rest": "trail", "x": 20} | -60 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 904 / 664 | 0 / 0 | -904 / -664 | 2 | 0.91 | 1.00 / - |  |  | S1 | no |

### X3 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 379 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 2 | 0.52 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL] |
| CROSS[cd4451a22198+87cd2ee2381f] | {"book": "K7", "loss": "cd4451a22198", "profit": "87cd2ee238 | 171 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 664 | 0 / 0 | 0 / -664 | 3 | 0.42 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| CROSS[3442b23cadf7+55aab8e87e08] | {"book": "O7", "loss": "3442b23cadf7", "profit": "55aab8e87e | 97 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 275 / 664 | 0 / 0 | -275 / -664 | 4 | 0.48 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | 57 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 435 / 664 | 0 / 0 | -435 / -664 | 4 | 0.64 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | 4 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 650 / 664 | 0 / 0 | -650 / -664 | 3 | 0.61 | 1.00 / - |  |  | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-FAIL exposure] |

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
| J3_statescale | {"a": 0.4, "f": "ahead_rel_slow", "rest": "hold", "s": 3, "t | -17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 18 / 0 | 0 / 0 | -18 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| J3_statescale | {"a": 0.6, "f": "ahead_rel_slow", "rest": "hold", "s": 3, "t | -17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 18 / 0 | 0 / 0 | -18 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "hold", "s": 3, "t | -17 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 18 / 0 | 0 / 0 | -18 / 0 | 1 | 1.00 | 1.00 / - |  | 0 | S1 | no |
| J1_scale | {"b": 0, "p": 0.9, "rest": "be"} | -30 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 69 / 0 | 0 / 0 | -69 / 0 | 1 | 0.55 | 1.00 / - |  |  | S1 | no |

### X5 both
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[afa4804db573+e1e6e2a7d150] | {"book": "H7", "loss": "afa4804db573", "profit": "e1e6e2a7d1 | 121 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[d8088d34f428+87cd2ee2381f] | {"book": "K7", "loss": "d8088d34f428", "profit": "87cd2ee238 | 99 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 0.76 | 1.00 / - |  |  | S1 | no |
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | 108 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[254d02cb61ad+9cdf7469ba89] | {"book": "P7", "loss": "254d02cb61ad", "profit": "9cdf7469ba | 439 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 1 | 1.00 | 1.00 / - |  |  | S1 | no |
| CROSS[966d0f8e1e9e+9cdf7469ba89] | {"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba | 226 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 / 0 | 0 / 0 | 0 / 0 | 2 | 0.76 | 1.00 / - |  |  | S1 | no |

## Survivors per book (CANDIDATE-DD and rec-ok and plc-ok and not FAILS-LIVE-WEEK; wf shown, not required; top 3 by drawdown-first)
### ALL survivors (1042 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 1,664 | 2,177 | 4,874 | 3,824 | 2,515 | 264 | -1,426 | -501 | 55,296 / 121,381 | 117,149 / 152,455 | 250,937 / 77,580 | 1,789 | 0.02 | 1.00 / 0.94 | -216,598 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 0, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | 1,905 | 2,072 | 5,258 | 3,836 | 2,563 | 166 | -1,514 | -574 | 56,444 / 121,381 | 115,335 / 152,455 | 251,176 / 77,580 | 1,789 | 0.04 | 1.00 / 0.94 | -216,598 | -6,398 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| L1_cond | {"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_ | -2,493 | -1,781 | 2,031 | 1,299 | -1,659 | -1,045 | -5,749 | -1,200 | 57,492 / 121,381 | 120,670 / 152,455 | 258,667 / 77,580 | 3,720 | 0.04 | 1.00 / 0.94 | -216,598 | -3,806 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### K7 survivors (159 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_adv_best_move | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best | 909 | 2,784 | 3,589 | 1,123 | -23 | 1,148 | -1,202 | 9 | 8,636 / 20,902 | 23,900 / 26,707 | 28,728 / 1,791 | 3,051 | 0.05 | 1.00 / 0.99 | -107,558 | 126 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| J3_statescale | {"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, " | 1,717 | 728 | 1,963 | 666 | -5 | 100 | -673 | 390 | 8,893 / 20,902 | 23,892 / 26,707 | 16,614 / 1,791 | 636 | 0.02 | 1.00 / 0.91 | -41,710 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| X1_scale_target | {"m": 0.75, "p": 0.5, "rest": "trail", "x": 10} | 2,081 | -874 | 1,144 | 277 | -389 | -1,516 | -399 | 463 | 9,147 / 20,902 | 17,406 / 26,707 | 39,575 / 1,791 | 969 | 0.04 | 1.00 / 0.99 | -34,760 | -40 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### P7 survivors (291 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| D3_pullback@after30 | {"X": 20, "ctx": "after30", "pb": 40} | -33,284 | -14,544 | -9,266 | 3,938 | -2,898 | -2,253 | -5,504 | 424 | 38,077 / 133,887 | 57,033 / 109,442 | 95,825 / -29,902 | 2,730 | 0.02 | 1.00 / 0.67 | -244,967 | -3,790 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D0_plain@after30 | {"X": 30, "ctx": "after30"} | -26,936 | -13,786 | -8,177 | 2,195 | -2,050 | 843 | -5,691 | 703 | 45,910 / 133,887 | 88,649 / 109,442 | 86,435 / -29,902 | 2,600 | 0.02 | 1.00 / 0.75 | -188,556 | 991 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 25, "blk": "A", "cancels" | -18,744 | -19,970 | -11,421 | 892 | -1,176 | 9,213 | -2,698 | -728 | 49,145 / 133,887 | 87,956 / 109,442 | 56,330 / -29,902 | 2,017 | 0.02 | 1.00 / 0.74 | -541,581 | -15,057 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### M7 survivors (790 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3_stop_extreme | {"X": 10, "k": 0} | -1,522 | -1,232 | -1,921 | 737 | 108 | -1,018 | -812 | -447 | 13,450 / 44,425 | 45,329 / 50,321 | -26,663 / -68,299 | 3,214 | 0.03 | 1.00 / 0.04 | -12,478 | -1,985 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| A_pulled | {"W": 5, "arm": "fixed", "armval": 10, "blk": "A", "cancels" | 2,543 | 1,840 | 3,151 | 1,741 | 14 | -865 | 238 | 113 | 13,485 / 44,425 | 31,252 / 50,321 | -12,409 / -68,299 | 1,195 | 0.02 | 1.00 / 0.44 | -18,261 | 724 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_pps_rel_w30 | {"arm": 15.0, "arm_kind": "abs", "dir": 1, "feat": "pps_rel_ | 813 | -1,701 | -437 | 1,036 | 673 | -54 | -260 | -119 | 16,985 / 44,425 | 40,526 / 50,321 | -26,252 / -68,299 | 1,893 | 0.02 | 1.00 / 0.72 | -38,488 | 1,099 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### U7 survivors (303 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| A_pulled | {"W": 5, "arm": "fixed", "armval": 30, "blk": "C", "cancels" | 4,731 | 2,325 | 1,591 | 894 | 1,188 | 1,309 | -33 | 553 | 7,335 / 21,561 | 37,858 / 42,226 | 21,476 / 120 | 430 | 0.02 | 1.00 / 0.98 | -129,230 | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_cps_rel_w10 | {"arm": 0.3, "arm_kind": "pct", "dir": 1, "feat": "cps_rel_w | 4,182 | 654 | 990 | 584 | 771 | -1,528 | -1,200 | -561 | 7,524 / 21,561 | 27,019 / 42,226 | 35,085 / 120 | 879 | 0.02 | 1.00 / 0.99 | -96,400 | 2,304 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_cps_rel_w30 | {"arm": 0.3, "arm_kind": "pct", "dir": 1, "feat": "cps_rel_w | 3,040 | -701 | 265 | 67 | 360 | -1,253 | -1,682 | -300 | 7,703 / 21,561 | 42,355 / 42,226 | 19,651 / 120 | 947 | 0.03 | 1.00 / 0.97 | -95,444 | 2,109 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### A7 survivors (982 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CROSS[e7c0088d2553+2c9eb23c8f1d] | {"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f | -907 | 293 | 148 | 521 | 204 | 21 | -232 | 80 | 4,415 / 12,461 | 4,374 / 6,089 | -7,646 / -17,069 | 732 | 0.03 | 1.00 / 0.57 | 4,462 |  | S1 | CANDIDATE-DD [rec-ok wf-ok plc-ok exposure] |
| D3_pullback | {"X": 20, "pb": 50} | 34 | 855 | 467 | 511 | 183 | 304 | -146 | 183 | 4,760 / 12,461 | 5,445 / 6,089 | -6,160 / -17,069 | 700 | 0.02 | 1.00 / 0.60 | -12,489 | -1,314 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| D3_pullback | {"X": 15, "pb": 50} | -11 | 288 | 199 | 129 | 24 | 223 | -207 | 201 | 4,785 / 12,461 | 4,912 / 6,089 | -4,174 / -17,069 | 713 | 0.02 | 1.00 / 0.59 | -12,489 | -1,018 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |

### H7 survivors (365 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_sweep8_w10 | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w | 1,289 | 322 | 1,222 | 1,281 | 917 | 834 | -138 | -22 | 4,988 / 15,477 | 15,783 / 20,667 | 6,350 / -32,750 | 338 | 0.02 | 1.00 / 0.73 | -45,009 | 394 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_adv_best_move | {"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "adv_best | 343 | 157 | -58 | 384 | 822 | 712 | -43 | 137 | 5,048 / 15,477 | 19,458 / 20,667 | -3,411 / -32,750 | 496 | 0.02 | 1.00 / 0.36 | -6,353 | 109 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_adv_best_move | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best | 223 | 97 | -98 | 261 | 772 | 712 | -105 | 118 | 5,048 / 15,477 | 20,484 / 20,667 | -4,679 / -32,750 | 504 | 0.02 | 1.00 / 0.35 | -6,353 | 109 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### O7 survivors (96 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LBC_dlt_med_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dlt_med | 321 | 309 | 116 | 34 | -308 | 134 | -500 | 165 | 3,243 / 7,469 | 4,699 / 5,102 | -4,802 / -9,532 | 448 | 0.05 | 1.00 / 0.30 | -20,988 | -243 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok exposure] |
| LBC_sweep8_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 461 | 41 | 400 | 110 | -186 | 223 | -35 | 226 | 3,859 / 7,469 | 4,241 / 5,102 | -4,740 / -9,532 | 220 | 0.03 | 1.00 / 0.45 | -22,094 | 826 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |
| LBC_sweep8_w10 | {"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "sweep8_w | 179 | 301 | 149 | 129 | -133 | 202 | -14 | 124 | 4,019 / 7,469 | 3,820 / 5,102 | -4,654 / -9,532 | 159 | 0.02 | 1.00 / 0.57 | -22,094 | 399 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

### X3 survivors (1 cells)
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo (sum of the P&L of the 20 worst weeks of 26, higher = less bad) | nfire | placebo p | family p (indep / WY) | WF (picking procedure, technique-family total) | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| F3_stop_extreme | {"X": 55, "k": 2} | 164 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 9 / 664 | 0 / 0 | -9 / -664 | 1 | 0.02 | 1.00 / - |  | 0 | S1 | CANDIDATE-DD [rec-ok wf-FAIL plc-ok] |

- X4: none (no cell is CANDIDATE-DD with rec-ok and plc-ok and not FAILS-LIVE-WEEK)
- X5: none (no cell is CANDIDATE-DD with rec-ok and plc-ok and not FAILS-LIVE-WEEK)

## Walk-forward of the picking procedure (all cells of a book/side; purged monthly, 7-day embargo, trailing 26 weeks, key = maxDD, worst-20, Ulcer, -mean)
| book   | side   |   ncells |   total |   dd_never |   dd_wf |   share_pos |   npick |   months | wf_ok   |
|:-------|:-------|---------:|--------:|-----------:|--------:|------------:|--------:|---------:|:--------|
| ALL    | loss   |    12895 | -925967 |     153255 |  193549 |           0 |      35 |       35 | False   |
| ALL    | profit |      564 | -675395 |     153255 |  200591 |           0 |      35 |       35 | False   |
| ALL    | both   |        7 |       0 |     153255 |  153255 |           0 |       0 |       35 | True    |
| K7     | loss   |    11603 | -204821 |      42831 |   37873 |           0 |      35 |       35 | False   |
| K7     | profit |      493 |  -87590 |      42831 |   58216 |           0 |      35 |       35 | False   |
| K7     | both   |        7 |  -82756 |      42831 |   42831 |           0 |       7 |       35 | False   |
| P7     | loss   |    11702 | -546533 |     144370 |  174599 |           0 |      35 |       35 | False   |
| P7     | profit |      555 | -381361 |     144370 |  193891 |           0 |      35 |       35 | False   |
| P7     | both   |        7 |       0 |     144370 |  144370 |           0 |       0 |       35 | True    |
| M7     | loss   |    11335 |  -14013 |      68802 |   42964 |           1 |      35 |       35 | False   |
| M7     | profit |      453 |  -19679 |      68802 |   79123 |           0 |      35 |       35 | False   |
| M7     | both   |        7 |  -22644 |      68802 |   91447 |           0 |       5 |       35 | False   |
| U7     | loss   |    10653 |  -75629 |      42226 |   33074 |           1 |      35 |       35 | False   |
| U7     | profit |      522 |  -98069 |      42226 |   48580 |           0 |      35 |       35 | False   |
| U7     | both   |        7 |  -37600 |      42226 |   42226 |           0 |       3 |       35 | False   |
| A7     | loss   |    10532 |  -32633 |      14181 |   11878 |           1 |      35 |       35 | False   |
| A7     | profit |      124 |    6226 |      14181 |   13799 |           1 |      35 |       35 | True    |
| A7     | both   |        7 |  -14563 |      14181 |   14181 |           0 |      23 |       35 | False   |
| H7     | loss   |    10516 |  -63350 |      57397 |   31200 |           1 |      35 |       35 | False   |
| H7     | profit |      481 |   -1732 |      57397 |   37692 |           0 |      35 |       35 | False   |
| H7     | both   |        7 |  -57521 |      57397 |   74469 |           0 |      16 |       35 | False   |
| O7     | loss   |     5868 |  -47288 |       7469 |    9508 |           0 |      35 |       35 | False   |
| O7     | profit |      111 |  -14782 |       7469 |   11523 |           0 |      35 |       35 | False   |
| O7     | both   |        7 |  -11378 |       7469 |    7469 |           0 |      25 |       35 | False   |

## Stack view and one rule for all books (first-order, IN-SAMPLE best-of-thousands picks per book: read them against the walk-forward table above, which is negative for almost every book/side)
Per-book picks stacked: L6M maxDD 32,068 vs never-cut 121,381; PRE maxDD 143,861 vs 152,455; L6M dmean 4,842. Best single cell on all books: X1_scale_target ({"m": 0.75, "p": 0.7, "rest": "trail", "x": 10}), L6M maxDD 33,846, dmean 574.

## Plain sentences
- ALL loss: the technique that lowers drawdown most is D3_pullback@after30 ({"X": 20, "ctx": "after30", "pb": 40}); L6M maxDD 54,622 vs 121,381 never-cut (-66,759); it costs 1,361 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.12, the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- ALL profit: the technique that lowers drawdown most is L1_cond ({"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_scale", "cond": "atr_mid"}); L6M maxDD 55,296 vs 121,381 never-cut (-66,085); it earns 7,628 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- ALL both: the technique that lowers drawdown most is CROSS[966d0f8e1e9e+9cdf7469ba89] ({"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba89"}); L6M maxDD 43,078 vs 121,381 never-cut (-78,303); it costs 12,076 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.82, the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- K7 loss: the technique that lowers drawdown most is LBC_adv_best_move ({"arm": 0.15, "arm_kind": "pct", "dir": 1, "feat": "adv_best_move", "mode": "latch", "months": "202304-202611(44)", "pers": 5, "thr": 3.0}); L6M maxDD 8,636 vs 20,902 never-cut (-12,266); it earns 1,136 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- K7 profit: the technique that lowers drawdown most is J3_statescale ({"a": 0.2, "f": "ahead_rel_slow", "rest": "trail", "s": 3, "th": 1.5, "x": 10}); L6M maxDD 8,893 vs 20,902 never-cut (-12,009); it earns 1,385 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- K7 both: the technique that lowers drawdown most is CROSS[966d0f8e1e9e+9cdf7469ba89] ({"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba89"}); L6M maxDD 8,298 vs 20,902 never-cut (-12,604); it costs 1,102 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.18, the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- P7 loss: the technique that lowers drawdown most is D3_pullback@after30 ({"X": 20, "ctx": "after30", "pb": 40}); L6M maxDD 38,077 vs 133,887 never-cut (-95,809); it earns 1,125 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- P7 profit: the technique that lowers drawdown most is L1_cond ({"base": {"b": 2, "p": 0.6, "rest": "be"}, "base_tech": "J1_scale", "cond": "atr_mid"}); L6M maxDD 82,296 vs 133,887 never-cut (-51,591); it earns 2,268 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- P7 both: the technique that lowers drawdown most is CROSS[966d0f8e1e9e+9cdf7469ba89] ({"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba89"}); L6M maxDD 26,813 vs 133,887 never-cut (-107,073); it costs 5,097 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- M7 loss: the technique that lowers drawdown most is F3_stop_extreme ({"X": 10, "k": 0}); L6M maxDD 13,450 vs 44,425 never-cut (-30,976); it earns 1,349 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- M7 profit: the technique that lowers drawdown most is J1_scale ({"p": 0.3, "rest": "trail", "x": 10}); L6M maxDD 25,111 vs 44,425 never-cut (-19,314); it earns 1,250 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00. Label CANDIDATE-DD.
- M7 both: the technique that lowers drawdown most is CROSS[966d0f8e1e9e+9cdf7469ba89] ({"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba89"}); L6M maxDD 34,844 vs 44,425 never-cut (-9,582); it earns 267 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.52, the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- U7 loss: the technique that lowers drawdown most is A_pulled ({"W": 5, "arm": "fixed", "armval": 30, "blk": "C", "cancels": "net", "maeW": 0, "med": "h1", "mult": 20, "newmae": 0, "pers": 3, "pulled": "against"}); L6M maxDD 7,335 vs 21,561 never-cut (-14,226); it earns 937 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- U7 profit: the technique that lowers drawdown most is X2_target_trail ({"arm": 0.7, "m": 2, "x": 20}); L6M maxDD 10,319 vs 21,561 never-cut (-11,242); it earns 545 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- U7 both: the technique that lowers drawdown most is CROSS[e7c0088d2553+2c9eb23c8f1d] ({"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f1d"}); L6M maxDD 12,841 vs 21,561 never-cut (-8,720); it costs 1,411 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.12, the family p over all cells is 1.00, PRE drawdown is worse than without it. Label no.
- A7 loss: the technique that lowers drawdown most is D3_pullback ({"X": 20, "pb": 50}); L6M maxDD 4,760 vs 12,461 never-cut (-7,701); it earns 606 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- A7 profit: the technique that lowers drawdown most is K1_target ({"m": 0.6}); L6M maxDD 5,693 vs 12,461 never-cut (-6,767); it earns 308 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- A7 both: the technique that lowers drawdown most is CROSS[e7c0088d2553+2c9eb23c8f1d] ({"book": "U7", "loss": "e7c0088d2553", "profit": "2c9eb23c8f1d"}); L6M maxDD 4,415 vs 12,461 never-cut (-8,046); it earns 301 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00. Label CANDIDATE-DD.
- H7 loss: the technique that lowers drawdown most is LBC_sweep8_w10 ({"arm": 10.0, "arm_kind": "abs", "dir": 1, "feat": "sweep8_w10", "mode": "latch", "months": "202304-202611(44)", "pers": 3, "thr": 4.0}); L6M maxDD 4,988 vs 15,477 never-cut (-10,489); it earns 11 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- H7 profit: the technique that lowers drawdown most is K1_target ({"m": 0.5}); L6M maxDD 7,798 vs 15,477 never-cut (-7,679); it costs 511 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- H7 both: the technique that lowers drawdown most is CROSS[e3e1c7125354+e1e6e2a7d150] ({"book": "H7", "loss": "e3e1c7125354", "profit": "e1e6e2a7d150"}); L6M maxDD 7,541 vs 15,477 never-cut (-7,936); it costs 1,679 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 0.36, the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label no.
- O7 loss: the technique that lowers drawdown most is LBC_dlt_med_w10 ({"arm": 0.15, "arm_kind": "pct", "dir": -1, "feat": "dlt_med_w10", "mode": "latch", "months": "202304-202611(44)", "pers": 1, "thr": -28.11239242553711}); L6M maxDD 3,243 vs 7,469 never-cut (-4,226); it costs 18 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- O7 profit: the technique that lowers drawdown most is K3_structtarget ({"buf": 0, "level": "prior_day", "lim": 150}); L6M maxDD 5,487 vs 7,469 never-cut (-1,982); it earns 2 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- O7 both: the technique that lowers drawdown most is CROSS[966d0f8e1e9e+9cdf7469ba89] ({"book": "P7", "loss": "966d0f8e1e9e", "profit": "9cdf7469ba89"}); L6M maxDD 2,425 vs 7,469 never-cut (-5,043); it earns 17 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the family p over all cells is 1.00, no walk-forward has been run, PRE drawdown is worse than without it. Label LEAD.
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
