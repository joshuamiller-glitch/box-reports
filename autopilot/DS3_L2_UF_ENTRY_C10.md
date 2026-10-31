# DS3_L2_UF_ENTRY_C10 - L2-UNTIL-FOUND cycle 10, ENTRY: resting-limit entry fill realism (queue model) (agent UF-ENTRY, 2026-10-31)
**ERRATUM (cycle 11, 2026-10-31): the CF2 cell 'a | A70' that this report calls 'the Sunday spec as coded (market at the close, THEN the 70/30 split)' (+0.92 per planned lot L6M) is NOT the coded spec: for F > 0 the 70% slice is entered at the SIGNAL whether or not a confirmation arrives and only the 30% remainder is bought at the confirmation. The coded spec (confirmation at market, then the split, no confirmation = no trade) is re-scored in DS3_L2_UF_ENTRY_C11.md. The queue-model results (fill rates, adverse selection, limit vs market W0 +3.57) are unaffected; every 'Sunday spec' row and the sentence about 'the split takes 2.6 pts away' in this report are superseded.**

Research only; UNTOUCHED never read; no live data. Prereg autopilot/UF_ENTRY_C10_prereg.md sha256 782d7e4898c318a3a58319cb865b05507ab078557182147ab6fc1f69e411a6da (before any cycle-10 statistic). Population: the CF2 LEAD cell tc|45s|R_three|b|near|3|W0 (45-s three-bar, limit at the confirming candle's body mid, pure wait, hold dies at the original stop / target / opposite signal) - 21,390 placed events on the six engine books, 18,851 touch fills (PE 4,266 placed). QUEUE MODEL on the 1-s tape and the mbp-10 1-s aggregates: first second whose trade low <= L = TOUCH; low <= L - 1 tick = THROUGH (every order at L filled, ours included); touch-only fills need the cumulative volume traded against the bid at L (full credit when L is the best bid at second end, 0.5 otherwise) plus cancels at the best bid >= phi x Q_ahead + 1 lot, phi in {0, 0.5, 1} (front, central, back of the displayed queue; Q_start = best-bid size at the touch + the volume traded in that second; median 8 contracts, quartiles 4-17, 10-90% 3-32); partial fills for 7 lots (fill fraction accumulated until 120 s after the first fill). Identity check: with phi = 0 the model's fills and outcomes at the touch second reproduce the kernel to 0.0 on 18,578 events (17,480 / 17,036 for the mid / far levels). The selection protocol has nothing to select (conventions fixed in the prereg); the recent windows were read once.

## Page 1 - the headline
1. **The queue model does not change the PE limit LEAD: the touch-fill assumption is almost free.** 82.7% of the touch fills are THROUGH in the very second of the touch (price trades at least one tick below the level, so every order at the level is filled whatever the queue), 97.6% within 60 s; only 2.4% are touch-and-bounce. The queue-realistic fill rate on touch is **99.9% at phi = 0 and 99.7-99.9% at phi = 0.5 / 1** (PE L6M: 99.9%, PRE 99.7%), and the per-contract value of the queue-realistic fills is +4.57 (phi 0.5) vs +4.64 (touch) in L6M and +2.05 / +2.01 vs +2.09 in PRE. The same holds for the mid and far levels (touch-fill rates 99.6-100%, through-in-the-second 77%).
2. **Adverse selection is real but it is not a fill-probability problem.** PE L6M by class (pts per contract, N): through in the touch second +3.05 (89% of fills), through later +15.7 (9%), touch-and-bounce +24.2 (2%, n=17): the winners that bounce off the level ARE the best trades - and the queue model still fills 16 of 17 of them at phi 0.5 / 1 (all 17 at phi 0), but LATE: median 3.4 min (phi 0.5) / 4.6 min (phi 1) after the touch, when price returns and trades through the level - the bounce winners are not lost, they are delayed, and the exit is re-scored from the late fill. PRE has the same shape (+2.56 / -1.03 / +4.96). The limit LEAD's gain comes from the through-in-the-second fills (price runs past the level and the order is filled at a better price than the close), not from the rare bounces.
3. **The latency risk is real: 4.1% of PE L6M events touch within 3 s of the placement** (mean +14.0 pts per contract in L6M, +0.7 in PRE): an order placed 1-3 s late misses or improves them; removing them costs about 0.6 pts per filled contract (about 0.35 per planned lot) in L6M.
4. **Stack at P6 7 lots (PE, NY-AM + NY-PM signals replaced, all else floor; research lots 5.6, x1.25 for 7 lots; delta vs the plain-split floor, \$/wk; MDE in parentheses):** limit body mid with TOUCH fills +4357 L6M / +3478 HOLD / -156 PRE / -215 X'; queue phi = 1: +4357 / +3478 / -245 / -228; phi = 0.5 with 7-lot partial fills +4357 / +3433 / -200 / -38; **market at the close, pure wait +3569 / +3272 / -425 / -588; market at the close then the 70/30 split (the Sunday spec as coded, no extra cost) +2334 / +1598 / -1106 / -418** (MDE 2-7k in every cell: inside MDE in every window).
5. **Per planned lot (delta vs floor, N, L6M):** limit touch +4.74, queue phi 0.5 / 1 +4.64, MARKET at the close (pure wait, full lot) **+3.57** - the number quoted for Sunday - and the Sunday spec as coded (market at the close, THEN the 70/30 split) **+0.92** (HOLD / PRE / X' +0.88 / +0.82 / +1.03); the +3.57 belongs to the no-split market entry, so the split on top of the confirmation takes 2.6 pts per planned lot away in L6M. LIVE-CAL: limit queue +4.97, market W0 +3.90, market + split +1.00.
6. **Break-even vs market at the close (L6M, N):** the limit LEAD equals market-at-close (+3.57) when the fill probability falls to **p* = 0.58** (uniform random non-fill) or when each limit fill is **2.1 pts** worse than the level; the modelled queue fill rate is 0.997-0.999, i.e. 1.7x the break-even; vs the Sunday spec as coded the limit wins at any fill probability (p* < 0). Modelled slippage of the market-at-close order itself (7 lots as 1-lot slices @2 s, d = 2 s, first 5 slices): +0.34 pt per lot in L6M (+-0.07 PRE), which reduces the market value by about 0.3 pt per planned lot on the lots that fill.
7. **Tier/honesty:** nothing is selected here; the LEAD's tier is unchanged (LEAD, CF2: not CANDIDATE: RC p 0.74, post-hoc, PRE stack negative): PRE stack -0.16k / -0.25k, X' -0.2k (queue) - the LEAD still lives in the recent windows only (L6M +4.4k, HOLD +3.5k, 2026 +6.4k). The queue model removes one objection (fill realism); the remaining risks are placement latency (4% of events), the pattern's post-hoc status and the PRE/X' stack.
8. Limits: 1-s resolution (the order of trades inside the touch second is unknown: through-in-the-second assumes the order was filled before the lower prints, which holds under price priority), the displayed queue is for the best level only (limits 6 pts from the market are outside the 10 displayed levels at placement; the queue is observed when price arrives), cancels are credited as ahead of us, phi bounds the placement-position uncertainty.

## 1. Fill statistics by level, population and window
| level | pop | window | touch fills | P(through in the touch second) | P(>=1 tick through within 60 s) | queue fill rate phi=0 | phi=0.5 | phi=1 | mean pts/contract (touch) | (queue phi=0.5) |
|--|--|--|--|--|--|--|--|--|--|--|
| body mid (LEAD, lvl near) | PE | L6M | 830 | 0.888 | 0.980 | 1.0000 | 0.9988 | 0.9988 | +4.64 | +4.57 |
| body mid (LEAD, lvl near) | PE | HOLD | 933 | 0.872 | 0.976 | 1.0000 | 0.9989 | 0.9989 | +4.31 | +4.25 |
| body mid (LEAD, lvl near) | PE | PRE | 2151 | 0.837 | 0.981 | 1.0000 | 0.9986 | 0.9972 | +2.09 | +2.05 |
| body mid (LEAD, lvl near) | PE | X | 849 | 0.767 | 0.961 | 0.9988 | 0.9965 | 0.9965 | +2.54 | +2.63 |
| body mid (LEAD, lvl near) | ALL6 | L6M | 3943 | 0.864 | 0.977 | 0.9992 | 0.9980 | 0.9975 | +3.93 | +3.83 |
| body mid (LEAD, lvl near) | ALL6 | HOLD | 4457 | 0.851 | 0.976 | 0.9993 | 0.9982 | 0.9978 | +3.32 | +3.23 |
| body mid (LEAD, lvl near) | ALL6 | PRE | 10178 | 0.841 | 0.980 | 0.9997 | 0.9982 | 0.9975 | +2.41 | +2.37 |
| body mid (LEAD, lvl near) | ALL6 | X | 4216 | 0.768 | 0.966 | 0.9991 | 0.9969 | 0.9967 | +1.56 | +1.58 |
| lvl mid | PE | L6M | 769 | 0.811 | 0.973 | 0.9974 | 0.9961 | 0.9948 | +2.96 | +2.74 |
| lvl mid | PE | HOLD | 869 | 0.797 | 0.969 | 0.9977 | 0.9954 | 0.9942 | +3.31 | +3.07 |
| lvl mid | PE | PRE | 2034 | 0.789 | 0.965 | 0.9995 | 0.9966 | 0.9951 | +2.58 | +2.49 |
| lvl mid | PE | X | 817 | 0.715 | 0.967 | 1.0000 | 1.0000 | 0.9988 | +1.52 | +1.52 |
| lvl mid | ALL6 | L6M | 3651 | 0.808 | 0.966 | 0.9995 | 0.9964 | 0.9945 | +2.49 | +2.33 |
| lvl mid | ALL6 | HOLD | 4147 | 0.801 | 0.965 | 0.9995 | 0.9961 | 0.9937 | +2.31 | +2.13 |
| lvl mid | ALL6 | PRE | 9507 | 0.794 | 0.965 | 0.9993 | 0.9965 | 0.9952 | +2.44 | +2.37 |
| lvl mid | ALL6 | X | 4074 | 0.709 | 0.954 | 1.0000 | 0.9990 | 0.9983 | +1.09 | +1.07 |
| lvl far | PE | L6M | 756 | 0.779 | 0.963 | 0.9987 | 0.9947 | 0.9947 | +3.48 | +3.18 |
| lvl far | PE | HOLD | 852 | 0.772 | 0.962 | 0.9988 | 0.9941 | 0.9941 | +4.01 | +3.68 |
| lvl far | PE | PRE | 1987 | 0.789 | 0.970 | 1.0000 | 0.9990 | 0.9990 | +2.54 | +2.48 |
| lvl far | PE | X | 808 | 0.723 | 0.962 | 1.0000 | 1.0000 | 1.0000 | +1.70 | +1.70 |
| lvl far | ALL6 | L6M | 3547 | 0.802 | 0.972 | 0.9989 | 0.9969 | 0.9961 | +2.47 | +2.35 |
| lvl far | ALL6 | HOLD | 4029 | 0.794 | 0.971 | 0.9990 | 0.9963 | 0.9955 | +2.41 | +2.26 |
| lvl far | ALL6 | PRE | 9254 | 0.786 | 0.967 | 0.9996 | 0.9972 | 0.9967 | +2.43 | +2.36 |
| lvl far | ALL6 | X | 3994 | 0.705 | 0.949 | 1.0000 | 0.9975 | 0.9962 | +1.18 | +1.13 |

## 2. Adverse selection: classes of touch fills (pts per contract, N)
| population | window | class | events (share) | mean pts per contract |
|--|--|--|--|--|
| PE | L6M | through in the touch second | 737 (88.8%) | +3.05 |
| PE | L6M | through later (<=60 s) | 76 (9.2%) | +15.68 |
| PE | L6M | touch-and-bounce (no 1-tick through in 60 s) | 17 (2.0%) | +24.25 |
| PE | L6M | all | 830 (100.0%) | +4.64 |
| PE | L6M | queue-realistic fills, phi=0.0 | fill rate 1.0000 | +4.64 |
| PE | L6M | queue-realistic fills, phi=0.5 | fill rate 0.9988 | +4.57 |
| PE | L6M | queue-realistic fills, phi=1.0 | fill rate 0.9988 | +4.57 |
| PE | L6M | touch within 3 s of placement | 4.1% | +14.02 |
| PE | HOLD | through in the touch second | 814 (87.2%) | +2.95 |
| PE | HOLD | through later (<=60 s) | 97 (10.4%) | +11.86 |
| PE | HOLD | touch-and-bounce (no 1-tick through in 60 s) | 22 (2.4%) | +21.20 |
| PE | HOLD | all | 933 (100.0%) | +4.31 |
| PE | HOLD | queue-realistic fills, phi=0.0 | fill rate 1.0000 | +4.31 |
| PE | HOLD | queue-realistic fills, phi=0.5 | fill rate 0.9989 | +4.25 |
| PE | HOLD | queue-realistic fills, phi=1.0 | fill rate 0.9989 | +4.25 |
| PE | HOLD | touch within 3 s of placement | 4.1% | +10.88 |
| PE | PRE | through in the touch second | 1801 (83.7%) | +2.56 |
| PE | PRE | through later (<=60 s) | 310 (14.4%) | -1.03 |
| PE | PRE | touch-and-bounce (no 1-tick through in 60 s) | 40 (1.9%) | +4.96 |
| PE | PRE | all | 2151 (100.0%) | +2.09 |
| PE | PRE | queue-realistic fills, phi=0.0 | fill rate 1.0000 | +2.09 |
| PE | PRE | queue-realistic fills, phi=0.5 | fill rate 0.9986 | +2.05 |
| PE | PRE | queue-realistic fills, phi=1.0 | fill rate 0.9972 | +2.01 |
| PE | PRE | touch within 3 s of placement | 4.8% | +0.71 |
| PE | X | through in the touch second | 651 (76.7%) | +2.04 |
| PE | X | through later (<=60 s) | 165 (19.4%) | +4.15 |
| PE | X | touch-and-bounce (no 1-tick through in 60 s) | 33 (3.9%) | +4.49 |
| PE | X | all | 849 (100.0%) | +2.54 |
| PE | X | queue-realistic fills, phi=0.0 | fill rate 0.9988 | +2.63 |
| PE | X | queue-realistic fills, phi=0.5 | fill rate 0.9965 | +2.63 |
| PE | X | queue-realistic fills, phi=1.0 | fill rate 0.9965 | +2.63 |
| PE | X | touch within 3 s of placement | 4.2% | -14.66 |
| ALL6 | L6M | through in the touch second | 3405 (86.4%) | +2.99 |
| ALL6 | L6M | through later (<=60 s) | 447 (11.3%) | +8.04 |
| ALL6 | L6M | touch-and-bounce (no 1-tick through in 60 s) | 91 (2.3%) | +18.88 |
| ALL6 | L6M | all | 3943 (100.0%) | +3.93 |
| ALL6 | L6M | queue-realistic fills, phi=0.0 | fill rate 0.9992 | +3.91 |
| ALL6 | L6M | queue-realistic fills, phi=0.5 | fill rate 0.9980 | +3.83 |
| ALL6 | L6M | queue-realistic fills, phi=1.0 | fill rate 0.9975 | +3.81 |
| ALL6 | L6M | touch within 3 s of placement | 4.4% | +11.35 |
| ALL6 | HOLD | through in the touch second | 3793 (85.1%) | +2.42 |
| ALL6 | HOLD | through later (<=60 s) | 556 (12.5%) | +6.76 |
| ALL6 | HOLD | touch-and-bounce (no 1-tick through in 60 s) | 108 (2.4%) | +17.38 |
| ALL6 | HOLD | all | 4457 (100.0%) | +3.32 |
| ALL6 | HOLD | queue-realistic fills, phi=0.0 | fill rate 0.9993 | +3.30 |
| ALL6 | HOLD | queue-realistic fills, phi=0.5 | fill rate 0.9982 | +3.23 |
| ALL6 | HOLD | queue-realistic fills, phi=1.0 | fill rate 0.9978 | +3.21 |
| ALL6 | HOLD | touch within 3 s of placement | 4.3% | +11.20 |
| ALL6 | PRE | through in the touch second | 8558 (84.1%) | +2.53 |
| ALL6 | PRE | through later (<=60 s) | 1413 (13.9%) | +0.85 |
| ALL6 | PRE | touch-and-bounce (no 1-tick through in 60 s) | 207 (2.0%) | +8.27 |
| ALL6 | PRE | all | 10178 (100.0%) | +2.41 |
| ALL6 | PRE | queue-realistic fills, phi=0.0 | fill rate 0.9997 | +2.40 |
| ALL6 | PRE | queue-realistic fills, phi=0.5 | fill rate 0.9982 | +2.37 |
| ALL6 | PRE | queue-realistic fills, phi=1.0 | fill rate 0.9975 | +2.34 |
| ALL6 | PRE | touch within 3 s of placement | 4.5% | +5.26 |
| ALL6 | X | through in the touch second | 3239 (76.8%) | +0.02 |
| ALL6 | X | through later (<=60 s) | 834 (19.8%) | +7.32 |
| ALL6 | X | touch-and-bounce (no 1-tick through in 60 s) | 143 (3.4%) | +2.96 |
| ALL6 | X | all | 4216 (100.0%) | +1.56 |
| ALL6 | X | queue-realistic fills, phi=0.0 | fill rate 0.9991 | +1.62 |
| ALL6 | X | queue-realistic fills, phi=0.5 | fill rate 0.9969 | +1.58 |
| ALL6 | X | queue-realistic fills, phi=1.0 | fill rate 0.9967 | +1.57 |
| ALL6 | X | touch within 3 s of placement | 4.5% | -13.34 |

## 3. PE NY-AM + NY-PM: variants per planned lot, LIVE-CAL, fills, stack
| variant (PE, NY-AM + NY-PM signals) | metric | 2026 | L6M | HOLD | PRE | X' |
|--|--|--|--|--|--|--|
| limit body-mid, TOUCH fill (CF2 convention) | delta vs the plain split floor, pts per planned lot (N) | +4.65 | +4.74 | +4.21 | +1.36 | +0.61 |
| | LIVE-CAL, pts per planned lot | +5.04 | +5.07 | +4.52 | +1.64 | +0.73 |
| | fills / signals (L6M) | 330 / 582 | | | | |
| | stack delta vs the all-floor stack, \$/wk at research lots (MDE) | +6446 (13399) | +4357 (6616) | +3478 (6002) | -156 (3400) | -215 (4478) |
| limit, queue phi=0 (front) | delta vs the plain split floor, pts per planned lot (N) | +4.65 | +4.74 | +4.21 | +1.36 | +0.61 |
| | LIVE-CAL, pts per planned lot | +5.04 | +5.07 | +4.52 | +1.64 | +0.73 |
| | fills / signals (L6M) | 330 / 582 | | | | |
| | stack delta vs the all-floor stack, \$/wk at research lots (MDE) | +6446 (13399) | +4357 (6616) | +3478 (6002) | -156 (3400) | -215 (4478) |
| limit, queue phi=0.5 | delta vs the plain split floor, pts per planned lot (N) | +4.65 | +4.64 | +4.11 | +1.36 | +0.61 |
| | LIVE-CAL, pts per planned lot | +5.04 | +4.97 | +4.43 | +1.64 | +0.73 |
| | fills / signals (L6M) | 329 / 582 | | | | |
| | stack delta vs the all-floor stack, \$/wk at research lots (MDE) | +6446 (13399) | +4357 (6616) | +3478 (6002) | -156 (3400) | -215 (4478) |
| limit, queue phi=1 (back) | delta vs the plain split floor, pts per planned lot (N) | +4.65 | +4.64 | +4.11 | +1.29 | +0.61 |
| | LIVE-CAL, pts per planned lot | +5.04 | +4.97 | +4.43 | +1.57 | +0.73 |
| | fills / signals (L6M) | 329 / 582 | | | | |
| | stack delta vs the all-floor stack, \$/wk at research lots (MDE) | +6446 (13399) | +4357 (6616) | +3478 (6002) | -245 (3375) | -228 (4485) |
| limit, queue phi=0.5, 7-lot partial fills | delta vs the plain split floor, pts per planned lot (N) | +4.65 | +4.64 | +4.09 | +1.33 | +0.59 |
| | LIVE-CAL, pts per planned lot | +5.04 | +4.97 | +4.41 | +1.61 | +0.71 |
| | fills / signals (L6M) | 329 / 582 | | | | |
| | stack delta vs the all-floor stack, \$/wk at research lots (MDE) | +6446 (13399) | +4357 (6616) | +3433 (6011) | -200 (3385) | -38 (4478) |
| limit, queue phi=1, 7-lot partial fills | delta vs the plain split floor, pts per planned lot (N) | +4.65 | +4.64 | +4.11 | +1.27 | +0.61 |
| | LIVE-CAL, pts per planned lot | +5.04 | +4.97 | +4.43 | +1.55 | +0.73 |
| | fills / signals (L6M) | 329 / 582 | | | | |
| | stack delta vs the all-floor stack, \$/wk at research lots (MDE) | +6446 (13399) | +4357 (6616) | +3478 (6002) | -290 (3353) | -228 (4485) |
| MARKET at the confirming close, pure wait (W0) | delta vs the plain split floor, pts per planned lot (N) | +5.31 | +3.57 | +3.54 | +1.58 | +0.81 |
| | LIVE-CAL, pts per planned lot | +5.71 | +3.90 | +3.87 | +1.87 | +0.93 |
| | fills / signals (L6M) | 352 / 582 | | | | |
| | stack delta vs the all-floor stack, \$/wk at research lots (MDE) | +5665 (17892) | +3569 (7112) | +3272 (6485) | -425 (3491) | -588 (4553) |
| SUNDAY SPEC: market at the close, then the 70/30 split (A70) | delta vs the plain split floor, pts per planned lot (N) | +2.22 | +0.92 | +0.88 | +0.82 | +1.03 |
| | LIVE-CAL, pts per planned lot | +2.34 | +1.00 | +0.96 | +0.89 | +1.04 |
| | fills / signals (L6M) | 582 / 582 | | | | |
| | stack delta vs the all-floor stack, \$/wk at research lots (MDE) | +3251 (9363) | +2334 (5399) | +1598 (4824) | -1106 (2434) | -418 (2630) |

## 4. Break-even vs market at the close
| window | market-at-close (W0) per planned lot | limit touch per planned lot | p* (uniform random fill prob at which limit = market-at-close) | fill-price slack s* (pts per fill) | Sunday spec (market + split) per planned lot | p* vs Sunday spec |
|--|--|--|--|--|--|--|
| Y26 | +5.31 | +4.65 | -1.73 | -1.34 | +2.22 | 11.07 |
| L6M | +3.57 | +4.74 | 0.58 | +2.07 | +0.92 | -0.36 |
| HOLD | +3.54 | +4.21 | 0.76 | +1.13 | +0.88 | -0.19 |
| PRE | +1.58 | +1.36 | 1.12 | -0.37 | +0.82 | 0.71 |
| X | +0.81 | +0.61 | 1.06 | -0.25 | +1.03 | 1.12 |

## 5. Files
code l2vast/ds3/code/uf/ufe10_store.py, ufe10_queue.py, ufe10_final.py, ufe10_report.py; outputs l2vast/ds3/out/uf/entry_c10/.
