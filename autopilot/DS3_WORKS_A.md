# DS3_WORKS_A - T-WORKS part A: generalised risk dials (W-A)
Refreshed 2026-11-11 17:08Z. Shadow only, no PASS claims, label PRE-PROOF (post-hoc). Prereg: autopilot/WORKS_A_PREREG.md (sha in DECISIONS.md, plus an addendum for the composites and cap sets). Code: outputs/code/th_works_a. Data: /mnt/l2/l2vast/_th_works_a.

## 0. Status and method
Exact sets with the L6M window complete: 7; with HOLD complete: 0. First-order screens (all on the exact LPB_BASE trade list, 20,808 trades, and again on the exact JN04RM trade list, 21,783 trades; the dial state is always the LPB_BASE shadow base-lot P&L, which is what the live state sees): A1 17756 cells, A2 1176 cells, A3 3960 cells per base. Exact runs go one set per job through the harness code/th_works_a/wa_run.py (WorksMixin generalises the JN04 rule-mode layers; it reproduces LPB_EMPTY and JN04RM trade by trade on 202610 and 202608, see DECISIONS.md). Every exact set below is JN04RM plus the named change, so each row answers whether the dial adds to the live-form JN04 stack. A cut is the stack maxDD cut in per cent; d mean is the weekly mean difference in dollars with the carrying week dropped.

## 1. Exact results (windows complete only; vs JN04RM = the same set measured against the JN04RM exact series)
| set | change on top of JN04RM | L6M vs LPB_BASE cut / d mean | L6M vs JN04RM cut / d mean / eq-mean cut | HOLD vs LPB_BASE cut / d mean | HOLD vs JN04RM cut / d mean / eq-mean cut |
|--|--|--|--|--|--|
| WA_A2_18 | ALL hi thr=1.2,m=0.0 | +32.8 / +1579 | -24.4 / +1417 / -15.0 | not yet | not yet |
| WA_A2_19 | ALL hi thr=1.1,m=0.0 | +49.1 / -1529 | +5.8 / -2067 / -7.0 | not yet | not yet |
| WA_A2_20 | exP7 hi thr=1.1,m=0.0 | +44.9 / -346 | -2.1 / -1093 / -8.7 | not yet | not yet |
| WA_A2_21 | B:M7 hi thr=1.1,m=0.0 | +51.6 / -511 | +10.4 / +806 / +14.4 | not yet | not yet |
| WA_A2_22 | B:P7 hi thr=1.2,m=0.0 | +49.2 / -2694 | +5.9 / +1320 / +12.6 | not yet | not yet |
| WA_C1 | JN04RM + K7 gate (Calmar 15 d < 0.5 skip) + M7 gate (drawdown-from-peak 7 d >= 6,296 skip) + P7 gate (sum 7 d < -3,626 x0.5) | +61.7 / -1029 | +29.0 / +1302 / +34.0 | not yet | not yet |
| WA_C2 | WA_C1 + stack gate (stack Calmar 7 d < 0.5 x0.5, first-winning-day re-arm) | +63.1 / +732 | +31.6 / +751 / +34.6 | not yet | not yet |

Reference rows (JN04RM vs LPB_BASE, rule 2a floors from DS3_C2_REGIME.md section B2): L6M cut +46.0 / d mean -1,701, HOLD cut +7.7 / d mean -3,658.

## 2. First-order versus exact (JN04 base)
| set | first-order L6M cut vs JN04 | exact L6M cut vs JN04RM |
|--|--|--|
| WA_A2_18 | +20.5 | -24.4 |
| WA_A2_19 | +37.1 | +5.8 |
| WA_A2_20 | +16.8 | -2.1 |
| WA_A2_21 | +10.9 | +10.4 |
| WA_A2_22 | +19.4 | +5.9 |

Rank correlation (Spearman) first-order vs exact over 5 sets: -0.50. First-order overstates dials that skip signals (a skipped signal frees the book for the next one, and day caps, locks and re-entries move) and is used for ranking only.

## 3. A1 performance gate: per-book result of the first-order screen (JN04RM trade list, shadow base-lot state; tolerance rule: L6M, HOLD cut > 0, PRE and X-prime cut >= -3; plateau: neighbours in window and threshold keep the sign)
Which books carry a gate: the screen finds tolerant plateau cells for K7, P7, M7 and H7 and the cross-book P7-state gates; U7, A7 and O7 have no cell that passes (no gate for them; reference row = no gate). The best cell per scope by L6M plus HOLD equal-mean cut:
| scope (state -> target) | best cell | n fired | L6M cut / eq / d mean | HOLD cut / eq | PRE / X-prime cut | cells passing / scanned |
|--|--|--|--|--|--|--|
| B:K7 | Calmar over the last 15 label days below 0.5 -> lots x0 (skip) (state resets when it recovers) | 3172 | +5.0 / +2.9 / -376 | +30.4 / +28.8 | +0.0 / +6.1 | 253 / 1208 |
| B:P7 | sum of P&L ($, base lots) over the last 7 label days below -3625.55 -> lots x0.5 (state resets when it recovers) | 2011 | +3.6 / +3.1 / -91 | +11.5 / +11.0 | +2.1 / +3.5 | 62 / 1208 |
| B:M7 | drawdown from window peak ($, base lots) over the last 7 label days at or above 6295.69 -> lots x0 (skip) (state resets when it recovers) | 1133 | +5.6 / +12.2 / +1340 | +16.7 / +22.5 | +24.3 / +8.4 | 144 / 1216 |
| B:U7 | no cell passes the tolerance and plateau rule | - | - | - | - | 0 / 1208 |
| B:H7 | Calmar over the last 10 label days below 1 -> lots x0.5 (state resets when it recovers) | 700 | +1.3 / +1.4 / +12 | +2.6 / +2.7 | +0.0 / +9.6 | 10 / 1208 |
| B:A7 | no cell passes the tolerance and plateau rule | - | - | - | - | 0 / 1196 |
| B:O7 | no cell passes the tolerance and plateau rule | - | - | - | - | 0 / 1204 |
| STACK | Calmar over the last 7 label days below 0.5 -> lots x0.5 (stays on until the first winning day) | 9379 | +18.1 / +12.7 / -1030 | +27.7 / +22.9 | +19.0 / +5.7 | 65 / 880 |
| STACK>P7 | Calmar over the last 10 label days below 1 -> lots x0.25 (state resets when it recovers) | 3071 | +23.4 / +15.7 / -1620 | +16.2 / +7.8 | +5.0 / +12.3 | 56 / 528 |
| K7>P7 | drawdown from window peak ($, base lots) over the last 5 label days at or above 9012.1 -> lots x0.75 (stays on until the first winning day) | 933 | +3.6 / +3.0 / -127 | +3.0 / +2.3 | +1.3 / -0.6 | 2 / 528 |
| M7>P7 | Calmar over the last 5 label days below 0.5 -> lots x0.5 (state resets when it recovers) | 3549 | +15.6 / +10.6 / -978 | +10.8 / +5.5 | +8.3 / +8.5 | 87 / 528 |
| P7>K7 | drawdown from window peak ($, base lots) over the last 10 label days at or above 14502.2 -> lots x0 (skip) (stays on until the first winning day) | 2853 | +6.3 / +6.1 / -29 | +30.4 / +30.2 | +20.0 / +27.1 | 20 / 528 |
| P7>ALLexP7 | drawdown from window peak ($, base lots) over the last 20 label days at or above 21753.3 -> lots x0 (skip) (stays on until the first winning day) | 5210 | +6.3 / +2.7 / -600 | +46.3 / +44.2 | +35.8 / +33.9 | 68 / 528 |

Per book x session (state = that book in that session, K7 P7 M7 U7 only), best five cells: BS:P7:nyam profit factor over the last 5 label days below 0.8 -> lots x0 (skip) (stays on until the first winning day); BS:M7:london drawdown from window peak ($, base lots) over the last 5 label days at or above 3443.2 -> lots x0.25 (stays on until the first winning day); BS:M7:london drawdown from window peak ($, base lots) over the last 5 label days at or above 3443.2 -> lots x0.5 (stays on until the first winning day); BS:M7:london drawdown from window peak ($, base lots) over the last 5 label days at or above 5164.8 -> lots x0.5 (stays on until the first winning day); BS:M7:london drawdown from window peak ($, base lots) over the last 5 label days at or above 5164.8 -> lots x0.25 (stays on until the first winning day).

## 4. A2 volatility-regime dial (atr_rel = 5-min ATR(14) over the 20-day median of daily medians, signal second)
First-order, JN04RM trade list, best tolerant plateau cells (high side skips or reduces, low side tests dead tape): 
| scope | rule | n fired | L6M cut / eq / d mean | HOLD cut / eq | PRE / X-prime cut | placebo-free plateau |
|--|--|--|--|--|--|--|
| ALL | hi thr=1.2,m=0.0 | 12470 | +20.5 / +30.8 / +2578 | +45.6 / +52.6 | +48.5 / +22.5 | 0.5 |
| ALL | hi thr=1.1,m=0.0 | 13681 | +37.1 / +32.1 / -1285 | +43.8 / +39.3 | +48.9 / +38.3 | 1.0 |
| exP7 | hi thr=1.1,m=0.0 | 10022 | +16.8 / +14.1 / -563 | +46.1 / +44.4 | +28.3 / +30.3 | 1.0 |
| B:M7 | hi thr=1.1,m=0.0 | 2872 | +10.9 / +15.2 / +897 | +31.4 / +34.8 | +20.0 / -2.8 | 1.0 |
| B:P7 | hi thr=1.2,m=0.0 | 3301 | +19.4 / +25.8 / +1508 | +12.2 / +19.3 | +23.4 / +30.2 | 0.5 |
| B:M7 | hi thr=1.2,m=0.0 | 2653 | +3.0 / +8.6 / +1056 | +29.4 / +33.4 | +16.1 / -0.9 | 0.5 |
| exP7 | hi thr=1.2,m=0.0 | 9169 | +1.1 / -0.4 / -294 | +39.0 / +38.1 | +16.4 / +13.4 | 0.5 |
| ALL | hi thr=1.2,m=0.25 | 12470 | +18.0 / +25.8 / +1816 | +2.5 / +11.8 | -2.6 / +15.9 | 0.5 |

Low-vol side (atr_rel at or below 0.6-0.9, halve or skip): 15 of 384 low cells pass the tolerance rule; the best on P7 is atr_rel <= 0.8 halve (L6M cut +15.9, HOLD cut +12.9 on the LPB_BASE list) but it costs PRE/X-prime heavily (X-prime -15.4), so dead-tape skipping is not carried.

## 5. A3 exposure caps (first-order on the exact JN04RM list; JN04 already has London same-side 6 truncate)
On the LPB_BASE list the live-form London same-side 6 truncate gives L6M cut +24.4, HOLD cut -12.2, PRE +8.6 (first-order). Tolerant cells on top of JN04: 72 of 3960; best five:
| session | same-side cap | total cap | mode | who | only when atr_rel >= | L6M cut / eq / d mean | HOLD cut | PRE / X-prime |
|--|--|--|--|--|--|--|--|--|
| all | 3 | 14 | skip | P7 | 1.3 | +2.0 / +8.5 / +1228 | +2.4 | +2.6 / +5.2 |
| all | 3 | 12 | skip | P7 | 1.3 | +2.0 / +8.5 / +1228 | +2.4 | +2.6 / +5.2 |
| all | 3 | 6 | skip | P7 | 1.3 | +2.0 / +8.5 / +1228 | +2.4 | +2.6 / +6.7 |
| all | 3 | 0 | skip | P7 | 1.3 | +2.0 / +8.5 / +1228 | +2.4 | +2.6 / +5.2 |
| all | 3 | 8 | skip | P7 | 1.3 | +2.0 / +8.5 / +1228 | +2.4 | +2.6 / +5.2 |

## 6. A4 dial interactions (exact)
Leave-one-out in rule mode on the live panel base (SZ-CDE, DS3_C2_REGIME.md section F; cut points lost on removal, L6M / HOLD): LOT 24.5 / 27.8, REG 12.8 / -3.0, STACK 12.4 / -1.5, 7/4/4 table 12.3 / -9.3, P7 cut 4.8 / 4.5, SIGQ 1.3 / 4.4, day cap 1.2 / 0.0. The pair-removal sets below fill the interaction table (a pair loses more than the sum when the two dials overlap).
| removed together | L6M cut vs LPB_BASE (JN04RM = +46.0) | HOLD cut vs LPB_BASE (JN04RM = +7.7) |
|--|--|--|
| JN04RM minus SIGQ minus P7 day cap (8,400 -> 16,800) | n/a / n/a | n/a / n/a |
| same, min() combine | n/a / n/a | n/a / n/a |
| JN04RM with min() of the multipliers instead of the product | n/a / n/a | n/a / n/a |
| JN04RM minus LOT minus REG | n/a / n/a | n/a / n/a |
| minus LOT minus 7/4/4 table | n/a / n/a | n/a / n/a |
| minus LOT minus STACK | n/a / n/a | n/a / n/a |
| minus REG minus 7/4/4 table | n/a / n/a | n/a / n/a |
| minus REG minus STACK | n/a / n/a | n/a / n/a |
| minus 7/4/4 table minus STACK | n/a / n/a | n/a / n/a |

## 7. v1.8 fields needed (names proposed; the JN04 layers keep their v1.6 names: P7PerfGate*, Ss5* SIGQ, Ss6* REG)
- Performance gate slot N (N = 1..8): PgNMode (Off, Shadow, Live), PgNBooks (target books), PgNSessions (empty = all), PgNStateBooks (the books whose shadow base-lot P&L is the state: one book, a list, or STACK), PgNStat (Calmar, Sum, WinRate, ProfitFactor, DrawdownFromPeak, ConsecLoss), PgNDays (label days, signal day excluded), PgNThreshold, PgNDirection (Below or AtOrAbove), PgNMult (0.75, 0.5, 0.25, 0), PgNRearm (Stateless or FirstWinDay). Needs the shadow base-lot P&L of every book stored beside the executed P&L (new strategy-internal field, same as the LOT note in JN04_LIVE_SPEC section C1).
- Volatility dial slot N: VdNMode, VdNBooks, VdNSessions, VdNHiThreshold and VdNHiMult (atr_rel at or above), VdNLoThreshold and VdNLoMult (at or below), feature AtrRel5m exactly as Ss6Feature.
- Exposure cap slot N: EcNMode, EcNKind (SameSide or Total), EcNCap, EcNSessions, EcNAction (Truncate or Skip), EcNBooks (who is limited), EcNMinAtrRel (cap only above this atr_rel; 0 = always).
- Combination: DialCombine (Product or Min), rounding once at the end: lots = max(1, floor(lots x m + 0.5)), m = 0 skips.
