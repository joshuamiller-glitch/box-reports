# DS3_TH_LOSS - Trade Health loss-side on the DS3 books and the dip-buy basket (D3TH, item E of DIRECTIVE_OVERNIGHT_20261027; 2026-10-28)
Research only; no live / execution-server / chart change; no account number written (live files cited by name pattern, `<acct>` for the number). Preregs: `l2vast/ds3/prereg/THL_BOOKS_prereg.md` (18 cells, sha256 f523fc352f24b27aa93028abf8400fc0cfb2c9d40e574cbf3859fb2e0118729a) and `THL_BASKET_prereg.md` (11 cells, sha256 e5201adffe5244395ad88a7719d5618742fdac0fb7659128d2508593febaf277), frozen in `autopilot/DECISIONS.md` before any cell was scored; pre-holdout text `autopilot/DS3_TH_LOSS_PREHOLD.md` (sha256 e9626f1d...), one holdout look per group logged (`ledger/holdout_looks.jsonl`, tracks DS3_THL_BOOKS and DS3_THL_BASKET; HOLD 2025-07+ and the second holdout 2023-04..2024-01 read together in that one look). Code `l2vast/ds3/code/thl/` (thl_lib, thl_basket_sec, thl_prereg, thl_score, thl_prehold, thl_report); results `l2vast/ds3/out/thl/`.

## Verdict (one line per book; live TH loss rule = 15 pts / 3 of 3 / 30 s, paired on identical entries vs the uncut 60/60 bracket)
**Trade Health on the loss side does not help any DS3 book or the dip-buy basket; the PRE point estimate is negative in every unit, and it is statistically negative (PRE CI below 0) only for MV and MA (HURTS-LEAD); the rest are NEUTRAL by the fixed gates, but UNDERPOWERED (MDE 2-5 pts/trade vs effects of -0.5 to -2.7). Nothing here supports adding TH-loss to any of them; the live DS3 account already shows KB/PE/SM/PB LossExit rows since 10-26 (17 cuts, no tape yet to score them).**

| book | basis | TH_LIVE PRE (pts/trade, CI) | HOLD | SPAN2 | WF | placebo rank (random exits) | MAE15 PRE (CI) | verdict TH_LIVE | verdict MAE15 | sequence WF mean base -> TH_LIVE ($/wk, 10 lots) / pairwise $/wk | one-line |
|--|--|--|--|--|--|--|--|--|--|--|--|
| KB | direct series, cut leg mapped | -1.41 [-3.1, +0.1] | -0.54 [-1.8, +0.7] | -0.32 [-2.7, +2.2] | -0.91 [-1.9, +0.1] | 0.93 | -2.84 [-4.7, -1.0] | NEUTRAL | HURTS-LEAD | 16,202 -> 6,182 / -9,309 | cuts save on 67% of cut trades but kill targets; net -0.9 pts/trade, CI touches 0; time-only exit costs -2.2, so TH is better than an uninformed exit but still negative. |
| SM | direct series, cut leg mapped | -2.50 [-5.4, +0.2] | -0.25 [-3.0, +2.2] | -0.20 [-3.9, +3.3] | -1.34 [-3.3, +0.4] | 0.62 | -3.52 [-6.9, -0.4] | NEUTRAL | HURTS-LEAD | 9,522 -> 4,982 / -3,521 | same shape, thinnest sample (904 PRE pairs, MDE 4.0); NEUTRAL, negative in all windows. |
| PE | direct series, cut leg mapped | -1.05 [-2.7, +0.5] | -0.16 [-1.4, +1.0] | -0.73 [-3.3, +1.8] | -0.54 [-1.5, +0.4] | 0.60 | -1.31 [-3.1, +0.7] | NEUTRAL | NEUTRAL | 10,684 -> 5,333 / -5,389 | smallest effect (-1.0 PRE, -0.2 HOLD); NEUTRAL, TH rank 0.98 vs random exits on HOLD: closest to harmless. |
| MV | hybrid (mapped cut) | -1.98 [-3.5, -0.4] | -1.75 [-3.0, -0.5] | +1.59 [-0.9, +4.5] | -1.85 [-2.9, -0.8] | 0.57 | -3.49 [-5.5, -1.4] | HURTS-LEAD | HURTS-LEAD | 17,950 -> 2,455 / -17,216 | negative in PRE and HOLD with CI below 0, positive only in the 2023-24 span: HURTS-LEAD, not confirmed (SPAN2 and placebo-rank gates fail). |
| MA | hybrid (mapped cut) | -2.74 [-5.2, -0.2] | -0.86 [-3.4, +1.4] | +0.87 [-2.5, +4.2] | -1.74 [-3.7, -0.0] | 0.36 | -2.12 [-5.1, +1.0] | HURTS-LEAD | NEUTRAL | 9,458 -> 4,108 / -5,734 | PRE CI below 0, HOLD and SPAN2 not significant: HURTS-LEAD (thin sample). |
| DN | MAPPED stop-entry | -1.64 [-3.5, +0.2] | -1.67 [-3.5, +0.0] | +0.40 [-2.5, +3.1] | -1.66 [-3.1, -0.3] | 0.78 | -1.92 [-4.2, +0.2] | NEUTRAL | NEUTRAL | 20,196 -> 7,800 / -9,073 | PRE CI touches 0, HOLD -1.7 with CI touching 0, SPAN2 +0.4: NEUTRAL, negative-leaning. |

Basket legs (overnight dip-buy, no stop/target, TH is the only exit before the 15:55 time exit; instrument points per leg; ES/RTY thresholds scaled by price ratio 0.27/0.11):

| leg | n legs PRE/HOLD/SPAN2 | TH_LIVE PRE (CI) | HOLD (CI) | SPAN2 (CI) | WF (CI) | $/leg WF (1 lot) | MAE15 PRE | time-only placebo PRE | verdict | note |
|--|--|--|--|--|--|--|--|--|--|--|
| NQ | 78/74/66 | -7.3 [-52.7, +42.3] | -70.6 [-140.8, +2.2] | -26.9 [-60.0, +3.9] | -38.1 [-79.4, +5.1] | -762 | -22.1 [-76.2, +30.7] | -20.2 | NEUTRAL | MDE 69 pts at PRE: cannot tell; HOLD -71 pts/leg is the worst window, 2024 was +17. |
| ES | 80/78/52 | -2.3 [-11.5, +7.1] | -19.1 [-30.3, -7.9] | -5.1 [-12.7, +1.3] | -10.6 [-17.8, -3.0] | -528 | -2.2 [-12.3, +8.3] | -1.7 | NEUTRAL | HOLD -19 pts [-30,-8] and WF -10.6 [-17.8,-3.0] exclude 0, but PRE (the gate) does not: NEUTRAL by the fixed gate, direction HURTS (all four years negative, 2026 -22.6). |
| RTY | 80/89/32 | -0.5 [-5.4, +4.6] | -6.3 [-12.6, +0.1] | -0.8 [-7.0, +6.0] | -3.5 [-7.6, +0.2] | -176 | -1.0 [-6.4, +4.7] | -1.2 | NEUTRAL | NEUTRAL, negative in every window (PRE -0.5, HOLD -6.3, SPAN2 -0.8); the literal-points RTY variant cuts only 12 legs (WF -1.1), the literal ES variant 59 legs (WF -6.4). |

Basket impact of TH_LIVE at the equal-risk unit (k=1: 1 NQ + 2.061 ES + 3.117 RTY, scaled thresholds) WF 2024-02..2026-10: -2,679 $/wk per unit (NQ -815, ES -1,210, RTY -654); the spec's equal-risk-to-ST10 size is about 5 units.

Basket impact of TH_LIVE at the equal-risk unit (k=1: 1 NQ + 2.061 ES + 3.117 RTY, scaled thresholds) HOLD 2025-07+: -5,145 $/wk per unit (NQ -1,559, ES -2,286, RTY -1,300); the spec's equal-risk-to-ST10 size is about 5 units.

Tier gates (fixed in the prereg, not softened): HELPS/HURTS-CONFIRMED need PRE CI excluding 0 AND HOLD and SPAN2 same sign AND random-trade placebo rank >= 0.90 (<= 0.10 for HURTS) AND weekly maxDD not worse (not better for HURTS); LEAD = PRE CI excludes 0 but another gate fails; NEUTRAL otherwise. No cell reached CONFIRMED in either direction.

## Full cell table (29 cells; effect = paired cut minus uncut, pts per trade for books / per leg for the basket; + = TH helped)
| cell | PRE n | PRE effect [CI] | MDE | cut share | cut better | HOLD [CI] | SPAN2 [CI] | WF [CI] | random-trade placebo mean / rank (PRE) | tier |
|--|--|--|--|--|--|--|--|--|--|--|
| KB_TIME_ONLY | 3093 | -2.21 (placebo mean; sd 0.52) | - | - | - | HOLD -0.50 | SPAN2 -0.13 | - | - | control |
| KB_TH_LIVE | 3093 | -1.41 [-3.1, +0.1] | 2.2 | 0.61 | 0.67 | -0.54 [-1.8, +0.7] | -0.32 [-2.7, +2.2] | -0.91 [-1.9, +0.1] | -2.21 / 0.93 | NEUTRAL |
| KB_MAE15 | 3093 | -2.84 [-4.7, -1.0] | 2.7 | 0.78 | 0.59 | -0.80 [-2.4, +0.8] | +0.52 [-2.3, +3.5] | -1.67 [-3.0, -0.5] | -3.16 / 0.76 | HURTS-LEAD |
| SM_TIME_ONLY | 904 | -2.82 (placebo mean; sd 0.89) | - | - | - | HOLD -1.93 | SPAN2 -0.72 | - | - | control |
| SM_TH_LIVE | 904 | -2.50 [-5.4, +0.2] | 4.0 | 0.62 | 0.65 | -0.25 [-3.0, +2.2] | -0.20 [-3.9, +3.3] | -1.34 [-3.3, +0.4] | -2.82 / 0.62 | NEUTRAL |
| SM_MAE15 | 904 | -3.52 [-6.9, -0.4] | 4.7 | 0.78 | 0.58 | -2.02 [-5.6, +1.0] | -1.60 [-6.0, +3.1] | -2.75 [-5.2, -0.4] | -3.85 / 0.66 | HURTS-LEAD |
| PE_TIME_ONLY | 3050 | -1.17 (placebo mean; sd 0.52) | - | - | - | HOLD -1.01 | SPAN2 -1.03 | - | - | control |
| PE_TH_LIVE | 3050 | -1.05 [-2.7, +0.5] | 2.1 | 0.62 | 0.67 | -0.16 [-1.4, +1.0] | -0.73 [-3.3, +1.8] | -0.54 [-1.5, +0.4] | -1.17 / 0.60 | NEUTRAL |
| PE_MAE15 | 3050 | -1.31 [-3.1, +0.7] | 2.6 | 0.79 | 0.61 | -1.59 [-3.2, -0.1] | -2.05 [-5.1, +0.9] | -1.47 [-2.6, -0.3] | -1.47 / 0.67 | NEUTRAL |
| MV_TIME_ONLY | 2923 | -2.05 (placebo mean; sd 0.55) | - | - | - | HOLD -1.28 | SPAN2 +1.02 | - | - | control |
| MV_TH_LIVE | 2923 | -1.98 [-3.5, -0.4] | 2.2 | 0.61 | 0.66 | -1.75 [-3.0, -0.5] | +1.59 [-0.9, +4.5] | -1.85 [-2.9, -0.8] | -2.05 / 0.57 | HURTS-LEAD |
| MV_MAE15 | 2923 | -3.49 [-5.5, -1.4] | 2.9 | 0.80 | 0.59 | -2.42 [-4.1, -0.8] | +1.68 [-1.4, +4.9] | -2.89 [-4.2, -1.7] | -2.88 / 0.12 | HURTS-LEAD |
| MA_TIME_ONLY | 1094 | -2.38 (placebo mean; sd 0.88) | - | - | - | HOLD -1.87 | SPAN2 -0.96 | - | - | control |
| MA_TH_LIVE | 1094 | -2.74 [-5.2, -0.2] | 3.6 | 0.62 | 0.65 | -0.86 [-3.4, +1.4] | +0.87 [-2.5, +4.2] | -1.74 [-3.7, -0.0] | -2.38 / 0.36 | HURTS-LEAD |
| MA_MAE15 | 1094 | -2.12 [-5.1, +1.0] | 4.5 | 0.77 | 0.59 | -3.13 [-6.2, -0.3] | -0.80 [-4.8, +2.9] | -2.66 [-4.9, -0.6] | -3.00 / 0.87 | NEUTRAL |
| DN_TIME_ONLY | 1762 | -2.13 (placebo mean; sd 0.66) | - | - | - | HOLD -1.24 | SPAN2 -0.57 | - | - | control |
| DN_TH_LIVE | 1762 | -1.64 [-3.5, +0.2] | 2.7 | 0.59 | 0.66 | -1.67 [-3.5, +0.0] | +0.40 [-2.5, +3.1] | -1.66 [-3.1, -0.3] | -2.13 / 0.78 | NEUTRAL |
| DN_MAE15 | 1762 | -1.92 [-4.2, +0.2] | 3.2 | 0.76 | 0.60 | -2.60 [-4.9, -0.5] | -0.56 [-4.1, +2.9] | -2.29 [-4.1, -0.6] | -3.02 / 0.96 | NEUTRAL |
| BK_NQ_TIME_ONLY | 78 | -20.21 (placebo mean; sd 13.92) | - | - | - | - | - | - | - | control |
| BK_NQ_TH_LIVE | 78 | -7.26 [-52.7, +42.3] | 69.3 | 0.82 | 0.42 | -70.59 [-140.8, +2.2] | -26.91 [-60.0, +3.9] | -38.09 [-79.4, +5.1] | -20.21 / 0.83 | NEUTRAL |
| BK_NQ_MAE15 | 78 | -22.14 [-76.2, +30.7] | 75.6 | 0.92 | 0.40 | -56.83 [-122.6, +15.8] | -40.45 [-77.0, -3.4] | -39.03 [-80.7, +5.8] | -23.23 / 0.52 | NEUTRAL |
| BK_ES_TIME_ONLY | 80 | -1.65 (placebo mean; sd 3.07) | - | - | - | - | - | - | - | control |
| BK_ES_TH_LIVE | 80 | -2.26 [-11.5, +7.1] | 13.5 | 0.80 | 0.42 | -19.05 [-30.3, -7.9] | -5.06 [-12.7, +1.3] | -10.55 [-17.8, -3.0] | -1.65 / 0.40 | NEUTRAL |
| BK_ES_MAE15 | 80 | -2.19 [-12.3, +8.3] | 15.2 | 0.89 | 0.45 | -17.94 [-29.1, -7.3] | -8.86 [-17.4, -0.5] | -9.96 [-17.6, -1.8] | -2.29 / 0.47 | NEUTRAL |
| BK_ES_TH_LIVE_LITERAL | 80 | -0.54 [-7.5, +6.3] | 9.7 | 0.33 | 0.54 | -12.37 [-20.1, -5.8] | +0.65 [-0.9, +2.3] | -6.38 [-11.4, -1.2] | -0.05 / 0.42 | NEUTRAL |
| BK_RTY_TIME_ONLY | 80 | -1.18 (placebo mean; sd 1.44) | - | - | - | - | - | - | - | control |
| BK_RTY_TH_LIVE | 80 | -0.46 [-5.4, +4.6] | 7.2 | 0.78 | 0.44 | -6.28 [-12.6, +0.1] | -0.75 [-7.0, +6.0] | -3.53 [-7.6, +0.2] | -1.18 / 0.68 | NEUTRAL |
| BK_RTY_MAE15 | 80 | -1.01 [-6.4, +4.7] | 8.0 | 0.93 | 0.39 | -6.46 [-13.0, +0.0] | +0.85 [-5.5, +7.7] | -3.88 [-8.3, +0.2] | -1.52 / 0.69 | NEUTRAL |
| BK_RTY_TH_LIVE_LITERAL | 80 | +0.26 [-1.6, +1.9] | 2.4 | 0.06 | 0.80 | -2.28 [-6.1, +0.2] | +0.16 [-1.9, +2.5] | -1.08 [-3.1, +0.5] | -0.07 / 0.71 | NEUTRAL |

Time-only controls (random exit at the TH cut's elapsed fraction, same cut count): they cost -1.2 to -2.8 pts/trade on the books (PRE); TH_LIVE is less negative than that on KB, SM, PE (PRE rank vs random-trade exits 0.93/0.62/0.60) and not distinguishable on MV/MA/DN (0.57/0.36/0.78): the 3-of-3 test carries a small amount of information relative to a blind exit but not enough to pay for the cut cost and the forfeited targets. MAE15 (cut at the first 15-pt excursion) is worse than TH_LIVE in 5 of 6 books (all but MA): the momentum/stall/efficiency conditions do filter, they just do not filter enough. PLC_TIME (TH's own cut trades with a uniform-random exit time) is informational only and favourable to the placebo by construction (can exit before the excursion that selected the trade).

## By entry session (TH_LIVE, pts/trade, windows PRE+HOLD+SPAN2 pooled in the final stage; n_cut in brackets)
| book | window | ASIA | LONDON | NY |
|--|--|--|--|--|
| KB | PRE | -1.52 [-4.5,+1.6] (427) | -1.26 [-4.6,+2.0] (505) | -1.42 [-3.5,+0.8] (949) |
| KB | HOLD | -2.27 [-4.8,+0.3] (758) | -1.07 [-3.5,+1.4] (742) | +0.91 [-0.9,+2.7] (1100) |
| SM | PRE | -4.69 [-9.8,+0.3] (126) | -2.89 [-7.7,+2.6] (220) | -0.54 [-5.2,+3.7] (210) |
| SM | HOLD | +0.82 [-3.2,+4.9] (189) | -2.30 [-6.9,+1.6] (216) | +1.03 [-3.7,+5.8] (165) |
| PE | PRE | -2.01 [-5.2,+1.1] (430) | -0.85 [-3.9,+2.2] (532) | -0.66 [-2.9,+1.5] (922) |
| PE | HOLD | -1.62 [-4.1,+0.6] (701) | -0.83 [-3.5,+1.4] (706) | +1.23 [-0.5,+2.9] (1008) |
| MV | PRE | -2.50 [-5.2,+0.6] (416) | -1.85 [-5.0,+1.4] (480) | -1.78 [-4.0,+0.3] (895) |
| MV | HOLD | -1.15 [-3.6,+1.2] (651) | -3.15 [-5.9,-0.5] (701) | -1.20 [-3.1,+0.9] (929) |
| MA | PRE | -3.72 [-8.0,+0.8] (179) | -6.19 [-11.5,-1.4] (227) | +0.59 [-3.0,+4.6] (274) |
| MA | HOLD | -0.13 [-4.3,+3.8] (276) | -2.30 [-6.7,+2.2] (238) | -0.34 [-4.0,+3.0] (255) |
| DN | PRE | -2.26 [-6.3,+1.4] (226) | -1.49 [-5.2,+2.4] (328) | -1.41 [-4.2,+1.2] (489) |
| DN | HOLD | -5.09 [-8.4,-1.8] (355) | -2.20 [-5.5,+1.5] (425) | +0.94 [-1.5,+3.5] (507) |

## By year (TH_LIVE, pts/trade; 2023 = Apr-Dec, 2026 = to 10-16)
| unit | 2023 | 2024 | 2025 | 2026 |
|--|--|--|--|--|
| KB | +0.33 (572) | -1.12 (1068) | -1.22 (1551) | -0.71 (1936) |
| SM | -0.29 (235) | -2.81 (386) | -1.31 (370) | +0.14 (405) |
| PE | -0.97 (548) | -0.88 (1065) | -1.06 (1506) | +0.15 (1792) |
| MV | +1.86 (565) | -1.61 (1042) | -1.94 (1448) | -1.86 (1657) |
| MA | +0.69 (274) | -3.01 (433) | -1.38 (497) | -0.78 (548) |
| DN | +0.44 (400) | -1.00 (643) | -2.07 (833) | -1.66 (905) |
| BK_NQ | -22.85 (45) | +16.61 (55) | -79.76 (39) | -77.20 (43) |
| BK_ES | -5.27 (35) | -0.63 (51) | -11.50 (43) | -22.55 (42) |
| BK_RTY | n/a (19) | -1.43 (65) | -2.65 (35) | -7.01 (50) |

## Sequence view (weekly, identical entries, exact per-book locks, 10 lots; TH exits free the book but no re-entries are generated: informational)
| book | arm | WF mean $/wk base -> cell | SD base -> cell | maxDD base -> cell | HOLD mean base -> cell | HOLD maxDD base -> cell |
|--|--|--|--|--|--|--|
| KB | TH_LIVE | 16,202 -> 6,182 | 59,308 -> 48,727 | 377,692 -> 362,277 | 11,687 -> 5,140 | 377,692 -> 362,277 |
| KB | MAE15 | 16,202 -> -1,630 | 59,308 -> 38,438 | 377,692 -> 1,007,340 | 11,687 -> -4,494 | 377,692 -> 608,782 |
| SM | TH_LIVE | 9,522 -> 4,982 | 35,892 -> 28,597 | 192,117 -> 226,050 | 9,831 -> 7,602 | 123,822 -> 149,613 |
| SM | MAE15 | 9,522 -> 1,847 | 35,892 -> 21,141 | 192,117 -> 244,127 | 9,831 -> 3,423 | 123,822 -> 130,683 |
| PE | TH_LIVE | 10,684 -> 5,333 | 50,370 -> 44,343 | 289,439 -> 599,975 | 13,906 -> 11,919 | 268,670 -> 227,434 |
| PE | MAE15 | 10,684 -> -4,836 | 50,370 -> 38,642 | 289,439 -> 866,083 | 13,906 -> -3,541 | 268,670 -> 514,913 |
| MV | TH_LIVE | 17,950 -> 2,455 | 59,484 -> 42,431 | 310,314 -> 391,736 | 19,730 -> 2,983 | 281,343 -> 391,736 |
| MV | MAE15 | 17,950 -> -7,890 | 59,484 -> 37,193 | 310,314 -> 1,333,314 | 19,730 -> -7,830 | 281,343 -> 762,224 |
| MA | TH_LIVE | 9,458 -> 4,108 | 43,965 -> 30,003 | 291,981 -> 243,059 | 9,865 -> 7,350 | 226,243 -> 196,103 |
| MA | MAE15 | 9,458 -> 724 | 43,965 -> 23,526 | 291,981 -> 211,598 | 9,865 -> -454 | 226,243 -> 211,598 |
| DN | TH_LIVE | 20,196 -> 7,800 | 53,313 -> 39,698 | 219,235 -> 247,711 | 23,030 -> 6,196 | 219,235 -> 203,220 |
| DN | MAE15 | 20,196 -> 4,274 | 53,313 -> 28,788 | 219,235 -> 372,041 | 23,030 -> -2,294 | 219,235 -> 362,459 |
Reading: TH_LIVE cuts the weekly SD (cutting deep drawdowns) but costs mean in every book; the maxDD effect is mixed (lower on KB and MA over the WF window and on PE/DN over HOLD alone; higher on SM, MV, PE-WF and DN-WF) and the sequence $/wk deltas are about 2x what the pairwise pts imply (lock-engine path dependence plus the sizecost surface on market cuts); the pairwise statistic is the object of record. MAE15 is a clear loser in the sequence view (maxDD 1.7-4.3x on KB, PE, MV, DN).

## Forward evidence: the live ST/HM book's Trade Health cuts since 2026-10-20 (read-only; counterfactual = uncut 60/60 bracket on the real tape)
Source: `data/live/StratTrades_*.csv` (exitName ending LossExit) and the existing replay cache `autopilot/forward/series/FORWARD_TH.json` (direct mbp-10 counterfactual, machinery check 119/120 outcomes reproduced). The pair file (`StratTrades_DualStrat_<acct>.csv`) has 0 cuts since 10-20 (TH off from 10-20); the DualStrat2 file has TH on from 10-23 morning; a Sim file (`StratTrades_DualStrat_<sim-acct>.csv`) shows cuts only on 10-26/27. The NQ tape on disk ends 2026-10-23, so every cut after 10-23 is PENDING (not imputed).

| book / file | cuts since 10-20 | replayed (tape) | pending | mean d pts/cut (cut minus uncut; + = TH helped) | 95% CI |
|--|--|--|--|--|--|
| ST, DualStrat2 file (live) | 16 (10-23: 4, 10-26: 12) | 4 | 12 | +34.9 | [+30.9, +40.1] (4 trades, ONE session-day: not an interval for the mean) |
| HM, DualStrat2 file (live) | 3 (10-23) | 3 | 0 | -9.7 | [-71.5, +51.4] (trade-level; $-CI [-11.4k, +8.2k] per trade at 8 lots) |
| ST + HM live, replayed | 7 | 7 | - | +15.8 | n too small to bootstrap sensibly |
| ST, <sim-acct> file | 24 (10-26: 12, 10-27: 12) | 0 | 24 | pending | - |
| HM, <sim-acct> file | 20 (10-26: 11, 10-27: 9) | 0 | 20 | pending | - |
| WT (informational) DualStrat2 / <sim-acct> | 9 / 41 | 7 | 43 | -10.3 on 7 | - |
| DS3 live account KB / PB / PE / SM LossExit (10-26, 10-27) | 9 / 3 / 4 / 1 | 0 | 17 | pending | - |
| DS4 Sim MV / DS5 S5 | 4 / 1 | 0 | 5 | pending | - |
Context before 10-20 (REPORT_FORWARD_TH, already published): ST loss cuts 10-13..10-23 n=50, +5.58 pts/cut, 95% CI [-11.8, +22.3] = +$893/trade [-$1.9k, +$3.6k]; the sequence view (cuts buy extra entries that lose) gave -$5.9k on the pair file.

**Honest line on the forward sample (MDE).** Per-cut SD of d is 50 pts (n=50 replayed). With a session-block design effect of about 1.5 the minimum detectable effect (80% power, 5%) is 2.8 x 50.3 / sqrt(n/1.5) pts per cut: **n=7 replayed (since 10-20) -> 65 pts/cut; n=50 (since 10-13) -> 24 pts/cut; n=63 if every cut since 10-20 on both ST/HM files could be replayed -> 22 pts/cut** (the <sim-acct> and DualStrat2 cuts are largely the SAME signals, so adding them does not add independent information). The backtest says the effect to look for is about -1.7 to -4.4 pts per cut (PRE ev per cut) (-0.9 to -2.0 pts per trade at a 60% cut share). Detecting 3 pts/cut needs about (2.8 x 50.3 / 3)^2 x 1.5 = **3,300 independent cuts**, i.e. roughly 65 weeks at the live rate of about 10 independent ST+HM cuts per trading day (19 on the DualStrat2 file over 10-23 and 10-26; 46 in 4 days on the pair file earlier). **The forward sample cannot distinguish anything yet, and will not for a year or more; it is a machinery check (the replay reproduces live outcomes), not evidence for or against TH.** The four +35 pts ST cuts on 10-23 are one session; they do not contradict the negative backtest sign (the same backtest has 67% of cuts 'better' and still loses on net).

## Top 10 cells by PRE z (effect / SE), regardless of verdict (never-empty-handed)
| rank | cell | PRE effect pts | CI | z |
|--|--|--|--|--|
| 1 | BK_RTY_TH_LIVE_LITERAL | +0.26 | [-1.6, +1.9] | +0.30 |
| 2 | BK_ES_TH_LIVE_LITERAL | -0.54 | [-7.5, +6.3] | -0.15 |
| 3 | BK_RTY_TH_LIVE | -0.46 | [-5.4, +4.6] | -0.18 |
| 4 | BK_NQ_TH_LIVE | -7.26 | [-52.7, +42.3] | -0.30 |
| 5 | BK_RTY_MAE15 | -1.01 | [-6.4, +4.7] | -0.35 |
| 6 | BK_ES_MAE15 | -2.19 | [-12.3, +8.3] | -0.42 |
| 7 | BK_ES_TH_LIVE | -2.26 | [-11.5, +7.1] | -0.48 |
| 8 | BK_NQ_MAE15 | -22.14 | [-76.2, +30.7] | -0.81 |
| 9 | PE_TH_LIVE | -1.05 | [-2.7, +0.5] | -1.31 |
| 10 | MA_MAE15 | -2.12 | [-5.1, +1.0] | -1.37 |

No cell has a positive PRE CI; the best is the least-bad (z below 0). Failed gate for all: `PRE CI > 0` (HELPS) - nothing passes; MDEs are in the full table (books 1.4-4.5 pts/trade realised, basket 7-105 pts/leg).

**Recommended-for-Sim cell: none.** The recommendation the data supports is the reverse: keep Trade Health loss-side OFF on KB, SM, PE, MV, MA, DN and on the basket; the nearest 'live-eligible once scored' change is switching it off where it is on (DS3 live account rows show KB/PE/SM/PB LossExit since 10-26), which is consistent with the ST decision of 10-20. Not a live change by this item.

## Method and deviations (honest list)
1. **No direct L2 replay of the cut legs.** Cut exits are priced on the 1-s trade-print path (NQ 1-s arrays of the g3 kernel; the basket legs from Databento trade prints rebuilt to 1-s), cost on the live-cost-delta basis (market cut 0.995 pt vs the replaced exit's class). The memory plan reserved L2 for R1-R4; this item is CPU-only. 'Direct basis where the series exists' is met only in the sense that KB/SM/PE series are direct (the unaffected trades keep their direct prices through the paired delta); the cut legs, and all of MV/MA (hybrid) and DN (mapped stop-entry), are mapped. The only direct evidence is the forward counterfactual.
2. Rows for PE/MV/MA were regenerated with te_core.gen_entries from the registered events (counts equal the library: PE 8,260, MV 7,813, MA 2,951, KB 8,504, SM 2,382, DN 4,759 to 2026-10-16; kernel base exit class reproduces 100% (DN 99.98%) with identical mean pts). DN uses the stop-entry second (first 1-s row touching the level).
3. Prereg MDE assumed cut shares of 0.25/0.45; the live rule cuts about 60% of trades (57% of live ST/HM exits in REPORT_TH_TICK), so realised MDEs (bootstrap) are larger than the prereg text; the tier gates do not depend on the MDE. Disclosed in DECISIONS.md.
4. Basket: ES/RTY thresholds scaled by price ratio (0.27 / 0.11, 'live points x price ratio') because the live NQ thresholds in literal points would be 4x/9x tighter in notional terms; literal-point variants are separate cells (they cut 5-59 legs). Basket verdicts use the PRE gate; ES HOLD/WF intervals exclude 0 but are not a gate (selection-free rule, single look). Basket session split n/a; basket weekly lock engine n/a (no locks apply).
5. Holdout: one logged look per group (books, basket), read together with SPAN2; These cells' HOLD numbers are first reads. Sequence view does not regenerate entries released by early exits (knock-on caveat, see REPORT_FORWARD_TH: 30 of 50 live cuts were followed by a same-book entry).
6. Time-only control is implemented as a placebo (random exit at the TH elapsed fraction), because a matched deterministic 'time-only' exit has no natural definition on a 60/60 bracket; MAE-only is the deterministic control.
7. Forward: no new replay was run (tape ends 10-23, no downloads); the since-10-20 slice is read from the existing FORWARD_TH cache plus a direct count of LossExit rows in the live CSVs (read-only).
