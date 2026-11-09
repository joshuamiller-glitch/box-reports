# DS3_TH_EXHAUST - every exit technique, both sides, drawdown first (auto-generated 2026-11-09 02:58Z)
## Box-confirmation items for v1.5 fidelity
v1.5 NOT VERIFIED: the v1.5 source is absent from the box (requested from the user); no match with v1.5 is claimed for any item. What follows is the treatment of the state build used by every number on this page.
1. A level present at s-1 and absent at s: cancelled size = max(0, size(s-1) - size(s) - traded at that price in (s-1, s]); absent at s counts as size 0 when the price is inside or better than the visible top-10 range of row s; it is IGNORED when it fell outside the visible top 10 (worse than the 10th level of a full 10-level book; about 64 M levels per side over the history, ~0.8 per side per second, mostly price moves). Box treatment (state build) + v1.5 NOT VERIFIED.
2. Seconds with no feed event: one row per session second, book carried forward, zero cancels and zero prints. Box treatment (state build) + v1.5 NOT VERIFIED.
3. newMae tie rule: a tie with the running adverse extreme counts as new (DS3_TH_STATE section 2). Box treatment (state build) + v1.5 NOT VERIFIED.
Evidence level: stage S1 rows are first-order (each trade alone on its stored path, bracket exits at level, 1-s decision latency, 0.80 pt market-exit cost); rows marked S2 went through the replica engine cascade (re-entries, locks, stack gates). Entry match to the live week is below .85, so the page is PRE-PROOF.
Label: state base S1b universe (never-cut hold-to-bracket path; months not yet rebuilt are S1 timer-close, flagged src in the universe), entry match to the live week not yet >= .85 unless stated: PRE-PROOF. Windows as of 2026-11-09 (data to 2026-11-05). USD per ISO week at live lots net of 4.84/contract; delta = rule minus never-cut with the carrying week dropped; "w/wo" = with the rule / without (never-cut). LIVE REFERENCE ROW = S1b-COMB (live week from the u5 replica).
Cells scored: 1; families: ['A_pulled']. Labels: {'no': 1}

## ALL
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| ALL never-cut level | 39,825 | 67,490 | 39,397 | 32,529 | 17,017 | 11,473 | 13,779 | 2,398 | 117,593 | 177,634 | 89,449 |
| ALL LIVE REF S1b-COMB level | 11,588 | 45,231 | 24,973 | 28,018 | 16,943 | 18,454 | 13,319 | 1,937 | 82,873 | 144,002 | 190,560 |

### ALL loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S1bCOMB_K7_cell | {"W": 2, "arm": 45, "mult": 10, "pers": 3, "v": 2} | 2,194 | -55 | 1,295 | 783 | 476 | 931 | 18 | -37 | 115,574 / 117,593 | 176,515 / 177,634 | 114,236 / 89,449 | 1,547 | 1.00 | 1.00 / 0.30 | -15,544 | -2,741 | S1 | CANDIDATE-DD |

## K7
| ref | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M | maxDD PRE | worst-20 L6M |
|---|---|---|---|---|---|---|---|---|---|---|---|
| K7 never-cut level | 4,971 | 8,571 | 3,128 | 3,575 | 1,824 | 651 | 2,656 | -80 | 26,983 | 30,403 | -15,009 |
| K7 LIVE REF S1b-COMB level | 7,873 | 8,450 | 3,436 | 3,530 | 2,241 | 3,740 | 2,740 | -164 | 41,849 | 23,073 | -20,339 |

### K7 loss
| technique | params | L1M | L2M | L3M | L6M | HOLD | MID | PRE | X' | maxDD L6M w/wo | maxDD PRE w/wo | worst-20 L6M w/wo | nfire | placebo p | family p (indep / WY) | WF | live week | stage | label |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| S1bCOMB_K7_cell | {"W": 2, "arm": 45, "mult": 10, "pers": 3, "v": 2} | 2,194 | -55 | 1,295 | 783 | 476 | 931 | 18 | -37 | 31,536 / 26,983 | 20,737 / 30,403 | 14,541 / -15,009 | 1,547 | 1.00 | 1.00 / 0.61 | -15,544 | 1,501 | S1 | no |

## Walk-forward of the picking procedure (all cells of a book/side; purged monthly, 7-day embargo, trailing 26 weeks, key = maxDD, worst-20, Ulcer, -mean)
| book   | side   |   ncells |   total |   dd_never |   dd_wf |   share_pos |   npick |   months | wf_ok   |
|:-------|:-------|---------:|--------:|-----------:|--------:|------------:|--------:|---------:|:--------|
| ALL    | loss   |        1 |  -15544 |     177634 |  177634 |           0 |      11 |       35 | False   |
| K7     | loss   |        1 |  -15544 |      51147 |   51147 |           0 |      11 |       35 | False   |

## Stack view and one rule for all books (first-order)
Per-book picks stacked: L6M maxDD 115,574 vs never-cut 117,593; PRE maxDD 176,515 vs 177,634; L6M dmean 783. Best single cell on all books: S1bCOMB_K7_cell ({"W": 2, "arm": 45, "mult": 10, "pers": 3, "v": 2}), L6M maxDD 115,574, dmean 783.

## Plain sentences
- ALL loss: the technique that lowers drawdown most is S1bCOMB_K7_cell ({"W": 2, "arm": 45, "mult": 10, "pers": 3, "v": 2}); L6M maxDD 115,574 vs 117,593 never-cut (-2,018); it earns 5,294 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, the purged walk-forward is not positive. Label CANDIDATE-DD.
- K7 loss: the technique that lowers drawdown most is S1bCOMB_K7_cell ({"W": 2, "arm": 45, "mult": 10, "pers": 3, "v": 2}); L6M maxDD 31,536 vs 26,983 never-cut (+4,553); it earns 828 USD/week vs the live line (S1b-COMB, L6M); it does not hold out of sample because the placebo p is 1.00, the family p over all cells is 1.00, the purged walk-forward is not positive. Label no.
