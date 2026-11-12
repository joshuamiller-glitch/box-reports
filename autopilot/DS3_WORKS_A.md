# DS3_WORKS_A - T-WORKS part A: generalised risk dials (W-A)
Refreshed 2026-11-12 06:22Z. Shadow only, no PASS claims, label PRE-PROOF (post-hoc). Prereg: autopilot/WORKS_A_PREREG.md (sha in DECISIONS.md, plus an addendum for the composites and cap sets). Code: outputs/code/th_works_a. Data: /mnt/l2/l2vast/_th_works_a.

## 0. Status and method
Exact sets with the L6M window complete: 30; with HOLD complete: 1. First-order screens (all on the exact LPB_BASE trade list, 20,808 trades, and again on the exact JN04RM trade list, 21,783 trades; the dial state is always the LPB_BASE shadow base-lot P&L, which is what the live state sees): A1 17756 cells, A2 1176 cells, A3 3960 cells per base. Exact runs go one set per job through the harness code/th_works_a/wa_run.py (WorksMixin generalises the JN04 rule-mode layers; it reproduces LPB_EMPTY and JN04RM trade by trade on 202610 and 202608, see DECISIONS.md). Every exact set below is JN04RM plus the named change, so each row answers whether the dial adds to the live-form JN04 stack. A cut is the stack maxDD cut in per cent; d mean is the weekly mean difference in dollars with the carrying week dropped.

WA jobs running at refresh (process count incl. forked child): code/th_tp/tp_launch.py x2. Since 20:3xZ (lead priority change for the P7 FIX) the queue is trimmed to WA_C1 (finalist, extending to PRE / X-prime / GAP for the bi-weekly WF); WA_A1_03, WA_A3_ALL6T and WA_A3_L5T were stopped and the rest of the queue is paused (queue_full_paused.txt); new sets start only at MemAvail >= 62 GB.

## 1. Exact results (windows complete only; vs JN04RM = the same set measured against the JN04RM exact series)
| set | change on top of JN04RM | L6M vs LPB_BASE cut / d mean | L6M vs JN04RM cut / d mean / eq-mean cut | HOLD vs LPB_BASE cut / d mean | HOLD vs JN04RM cut / d mean / eq-mean cut |
|--|--|--|--|--|--|
| WA_A1_01 | B:K7 calmar D15 thr0.5 stateless x0.0 | +45.4 / -2420 | -1.2 / -84 / -1.7 | not yet | not yet |
| WA_A1_04 | B:M7 ddpeak D7 thr6295.69 stateless x0.0 | +52.1 / +267 | +11.4 / +1485 / +17.5 | not yet | not yet |
| WA_A1_07 | STACK calmar D7 thr0.5 firstwin x0.5 | +52.0 / -3711 | +11.2 / -1399 / +2.9 | not yet | not yet |
| WA_A1_09 | STACK>P7 calmar D10 thr1.0 stateless x0.25 | +58.3 / -4059 | +22.8 / -1629 / +15.1 | not yet | not yet |
| WA_A2_18 | ALL hi thr=1.2,m=0.0 | +32.8 / +1579 | -24.4 / +1417 / -15.0 | not yet | not yet |
| WA_A2_19 | ALL hi thr=1.1,m=0.0 | +49.1 / -1529 | +5.8 / -2067 / -7.0 | not yet | not yet |
| WA_A2_20 | exP7 hi thr=1.1,m=0.0 | +44.9 / -346 | -2.1 / -1093 / -8.7 | not yet | not yet |
| WA_A2_21 | B:M7 hi thr=1.1,m=0.0 | +51.6 / -511 | +10.4 / +806 / +14.4 | not yet | not yet |
| WA_A2_22 | B:P7 hi thr=1.2,m=0.0 | +49.2 / -2694 | +5.9 / +1320 / +12.6 | not yet | not yet |
| WA_A3_ALL6T | same-side cap 6 truncate in every session | +42.6 / -3993 | -6.2 / -1321 / -15.3 | not yet | not yet |
| WA_A3_L5T | London same-side cap 5 truncate (JN04 has 6) | +48.7 / -2339 | +5.0 / -199 / +3.8 | not yet | not yet |
| WA_A3_L6REG13 | London same-side cap 6 only when atr_rel >= 1.3 | +33.6 / -1639 | -22.9 / -341 / -25.3 | not yet | not yet |
| WA_A3_TOT10 | London total-lots cap 10 truncate (replaces the same-side cap) | +41.1 / -1205 | -9.1 / +46 / -8.8 | not yet | not yet |
| WA_A4_MINCOMB | JN04RM with min() of the multipliers instead of the product | +44.6 / -1770 | -2.6 / +86 / -2.1 | not yet | not yet |
| WA_A4_NOSQ_NODC | JN04RM minus SIGQ minus P7 day cap (8,400 -> 16,800) | +43.5 / +2215 | -4.5 / +684 / -0.7 | not yet | not yet |
| WA_A4_NOSQ_NODC_MIN | same, min() combine | +45.8 / +667 | -0.4 / +2897 / +12.4 | not yet | not yet |
| WA_A4_NO_LOT_REG | JN04RM minus LOT minus REG | +5.2 / +404 | -75.6 / +1721 / -59.7 | not yet | not yet |
| WA_A4_NO_LOT_STACK | minus LOT minus STACK | +1.7 / +2420 | -82.0 / +2643 / -58.5 | not yet | not yet |
| WA_A4_NO_LOT_TABLE | minus LOT minus 7/4/4 table | +6.2 / +535 | -73.8 / +1107 / -63.6 | not yet | not yet |
| WA_A4_NO_REG_STACK | minus REG minus STACK | +25.5 / -2202 | -37.9 / -885 / -45.3 | not yet | not yet |
| WA_A4_NO_REG_TABLE | minus REG minus 7/4/4 table | +19.4 / -1808 | -49.3 / -491 / -53.6 | not yet | not yet |
| WA_A4_NO_TABLE_STACK | minus 7/4/4 table minus STACK | +14.6 / +1090 | -58.1 / +1011 / -50.4 | not yet | not yet |
| WA_C1 | JN04RM + K7 gate (Calmar 15 d < 0.5 skip) + M7 gate (drawdown-from-peak 7 d >= 6,296 skip) + P7 gate (sum 7 d < -3,626 x0.5) | +61.7 / -1029 | +29.0 / +1302 / +34.0 | +44.5 / -3530 | +39.8 / -318 / +44.1 |
| WA_C2 | WA_C1 + stack gate (stack Calmar 7 d < 0.5 x0.5, first-winning-day re-arm) | +63.1 / +732 | +31.6 / +751 / +34.6 | not yet | not yet |
| WA_PL_K03 | WA_C1 with K7 Calmar threshold 0.3 (plateau) | +61.7 / -1229 | +29.0 / +1064 / +33.3 | not yet | not yet |
| WA_PL_K08 | WA_C1 with K7 Calmar threshold 0.8 | +53.4 / -1147 | +13.7 / +1183 / +19.3 | not yet | not yet |
| WA_PL_M40000 | WA_C1 with M7 drawdown threshold $4,000 | +64.1 / -2423 | +33.5 / +14 / +33.6 | not yet | not yet |
| WA_PL_M90000 | WA_C1 with M7 drawdown threshold $9,000 | +58.9 / -1777 | +23.8 / +474 / +25.9 | not yet | not yet |
| WA_PL_P20000 | WA_C1 with P7 sum threshold -$2,000 | +61.7 / -1212 | +29.0 / +1119 / +33.4 | not yet | not yet |
| WA_PL_P50000 | WA_C1 with P7 sum threshold -$5,000 | +61.7 / -1022 | +29.0 / +1308 / +34.1 | not yet | not yet |

Reference rows (JN04RM vs LPB_BASE, rule 2a floors from DS3_C2_REGIME.md section B2): L6M cut +46.0 / d mean -1,701, HOLD cut +7.7 / d mean -3,658.

## 2. First-order versus exact (JN04 base)
| set | first-order L6M cut vs JN04 | exact L6M cut vs JN04RM |
|--|--|--|
| WA_A1_01 | +5.0 | -1.2 |
| WA_A1_04 | +5.6 | +11.4 |
| WA_A1_07 | +18.1 | +11.2 |
| WA_A1_09 | +23.4 | +22.8 |
| WA_A2_18 | +20.5 | -24.4 |
| WA_A2_19 | +37.1 | +5.8 |
| WA_A2_20 | +16.8 | -2.1 |
| WA_A2_21 | +10.9 | +10.4 |
| WA_A2_22 | +19.4 | +5.9 |

Rank correlation (Spearman) first-order vs exact over 9 sets: 0.00. First-order overstates dials that skip signals (a skipped signal frees the book for the next one, and day caps, locks and re-entries move) and is used for ranking only.

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
| JN04RM minus SIGQ minus P7 day cap (8,400 -> 16,800) | +43.5 / +2215 | n/a / n/a |
| same, min() combine | +45.8 / +667 | n/a / n/a |
| JN04RM with min() of the multipliers instead of the product | +44.6 / -1770 | n/a / n/a |
| JN04RM minus LOT minus REG | +5.2 / +404 | n/a / n/a |
| minus LOT minus 7/4/4 table | +6.2 / +535 | n/a / n/a |
| minus LOT minus STACK | +1.7 / +2420 | n/a / n/a |
| minus REG minus 7/4/4 table | +19.4 / -1808 | n/a / n/a |
| minus REG minus STACK | +25.5 / -2202 | n/a / n/a |
| minus 7/4/4 table minus STACK | +14.6 / +1090 | n/a / n/a |

## 7. v1.8 fields needed (names proposed; the JN04 layers keep their v1.6 names: P7PerfGate*, Ss5* SIGQ, Ss6* REG)
- Performance gate slot N (N = 1..8): PgNMode (Off, Shadow, Live), PgNBooks (target books), PgNSessions (empty = all), PgNStateBooks (the books whose shadow base-lot P&L is the state: one book, a list, or STACK), PgNStat (Calmar, Sum, WinRate, ProfitFactor, DrawdownFromPeak, ConsecLoss), PgNDays (label days, signal day excluded), PgNThreshold, PgNDirection (Below or AtOrAbove), PgNMult (0.75, 0.5, 0.25, 0), PgNRearm (Stateless or FirstWinDay). Needs the shadow base-lot P&L of every book stored beside the executed P&L (new strategy-internal field, same as the LOT note in JN04_LIVE_SPEC section C1).
- Volatility dial slot N: VdNMode, VdNBooks, VdNSessions, VdNHiThreshold and VdNHiMult (atr_rel at or above), VdNLoThreshold and VdNLoMult (at or below), feature AtrRel5m exactly as Ss6Feature.
- Exposure cap slot N: EcNMode, EcNKind (SameSide or Total), EcNCap, EcNSessions, EcNAction (Truncate or Skip), EcNBooks (who is limited), EcNMinAtrRel (cap only above this atr_rel; 0 = always).
- Combination: DialCombine (Product or Min), rounding once at the end: lots = max(1, floor(lots x m + 0.5)), m = 0 skips.
## 8. Behavioural scorecard (standing principle 19:45Z; tool code/th_works_q/behavior_scorecard.py; stack, L6M and HOLD, per week; a = full stops, b = give-backs, c = same-side losing run p95 and $ lost on the 3rd-and-later, d = no-new-evidence re-entries, e = net vs LPB_BASE)
A finalist must at least halve a, b and c on L6M against the live stack without the cost in e exceeding the saving, and must not turn a trend week into a loser. The dials in this part change lot sizes and skip signals; they do not change how a trade is exited, so they cannot by themselves remove full stops (a) or give-backs (b): they act on c and d through fewer or smaller attempts.
| set | window | a full stops /wk ($/wk) | b give-backs /wk ($ realised) | c run p95 / max ($ on 3rd+) | d no-evidence re-entries /wk ($) | e net vs LPB_BASE $/wk | halves a, b, c? |
|--|--|--|--|--|--|--|--|
| LPB_BASE | L6M | 24.5 (-40052) | 9.1 (-14009) | +6 / +12 (-51344) | +37.3 (-363) | n/a | reference |
| LPB_BASE | HOLD | 23.0 (-37923) | 8.0 (-12167) | +6 / +12 (-43521) | +30.0 (+732) | n/a | reference |
| JN04RM | L6M | 25.4 (-38130) | 9.9 (-11306) | +7 / +13 (-42885) | +43.3 (+1885) | n/a | no (a x1.03, b x1.09) |
| JN04RM | HOLD | 23.6 (-35520) | 8.6 (-9743) | +6 / +13 (-37009) | +34.2 (+1140) | n/a | no (a x1.03, b x1.08) |
| WA_A1_01 | L6M | 20.8 (-31655) | 9.0 (-10439) | +6 / +13 (-35110) | +37.1 (+727) | -1054 | no (a x0.85, b x1.00) |
| WA_A1_04 | L6M | 24.8 (-37444) | 9.1 (-10634) | +6 / +11 (-38578) | +39.6 (+2144) | +1674 | no (a x1.01, b x1.00) |
| WA_A1_07 | L6M | 25.6 (-35371) | 10.1 (-10077) | +7 / +13 (-40899) | +44.5 (+2014) | -2544 | no (a x1.04, b x1.11) |
| WA_A1_09 | L6M | 25.5 (-38107) | 9.9 (-10567) | +7 / +13 (-41151) | +44.1 (+1794) | -2677 | no (a x1.04, b x1.09) |
| WA_A2_18 | L6M | 18.0 (-26614) | 6.0 (-7454) | +6 / +9 (-26791) | +21.4 (+1215) | -801 | no (a x0.73, b x0.66) |
| WA_A2_19 | L6M | 16.8 (-24376) | 5.2 (-6494) | +5 / +9 (-22938) | +17.6 (+484) | -4036 | no (a x0.68, b x0.57) |
| WA_A2_20 | L6M | 17.2 (-24926) | 6.5 (-7808) | +6 / +9 (-27348) | +26.1 (+1217) | -2181 | no (a x0.70, b x0.72) |
| WA_A2_21 | L6M | 24.4 (-36906) | 8.9 (-10301) | +6 / +11 (-36955) | +36.3 (+1891) | +979 | no (a x1.00, b x0.98) |
| WA_A2_22 | L6M | 25.0 (-37592) | 8.7 (-10063) | +6 / +11 (-35557) | +36.4 (+1839) | -679 | no (a x1.02, b x0.96) |
| WA_A3_ALL6T | L6M | 24.7 (-36351) | 9.8 (-10958) | +6 / +13 (-40515) | +43.0 (+1714) | -2556 | no (a x1.01, b x1.08) |
| WA_A3_L5T | L6M | 25.5 (-38104) | 9.7 (-11112) | +7 / +13 (-42464) | +43.4 (+1663) | -764 | no (a x1.04, b x1.07) |
| WA_A3_L6REG13 | L6M | 25.5 (-38533) | 9.8 (-11435) | +7 / +13 (-43507) | +43.5 (+2183) | -406 | no (a x1.04, b x1.08) |
| WA_A3_TOT10 | L6M | 25.4 (-38335) | 9.8 (-11381) | +7 / +13 (-43318) | +43.3 (+2203) | +36 | no (a x1.03, b x1.08) |
| WA_A4_MINCOMB | L6M | 25.4 (-38324) | 9.7 (-11547) | +6 / +12 (-44756) | +42.2 (+1343) | -755 | no (a x1.03, b x1.07) |
| WA_A4_NOSQ_NODC | L6M | 24.8 (-39411) | 10.0 (-12872) | +6 / +13 (-47744) | +43.5 (+1277) | +1285 | no (a x1.01, b x1.10) |
| WA_A4_NOSQ_NODC_MIN | L6M | 24.8 (-39500) | 10.0 (-13220) | +6 / +13 (-49203) | +43.4 (+1181) | +1723 | no (a x1.01, b x1.10) |
| WA_A4_NO_LOT_REG | L6M | 25.5 (-39083) | 9.4 (-12747) | +6 / +13 (-48687) | +40.2 (+1704) | +2573 | no (a x1.04, b x1.04) |
| WA_A4_NO_LOT_STACK | L6M | 25.4 (-38662) | 9.7 (-12735) | +6 / +13 (-46533) | +41.3 (+2789) | +3568 | no (a x1.03, b x1.07) |
| WA_A4_NO_LOT_TABLE | L6M | 25.0 (-38629) | 9.6 (-13644) | +6 / +12 (-49000) | +40.7 (+3376) | +1815 | no (a x1.02, b x1.06) |
| WA_A4_NO_REG_STACK | L6M | 25.5 (-38820) | 9.6 (-11749) | +6 / +13 (-45751) | +42.4 (+1431) | -79 | no (a x1.04, b x1.06) |
| WA_A4_NO_REG_TABLE | L6M | 25.2 (-38884) | 9.6 (-12640) | +6 / +11 (-48924) | +41.4 (+1431) | +96 | no (a x1.03, b x1.05) |
| WA_A4_NO_TABLE_STACK | L6M | 25.4 (-38956) | 9.9 (-12713) | +7 / +12 (-46982) | +42.9 (+2485) | +125 | no (a x1.03, b x1.09) |
| WA_C1 | L6M | 20.1 (-30920) | 8.3 (-9376) | +6 / +11 (-30793) | +34.0 (+838) | +356 | no (a x0.82, b x0.91) |
| WA_C1 | HOLD | 18.9 (-29150) | 7.4 (-8382) | +5 / +11 (-28293) | +26.7 (+747) | -2800 | no (a x0.83, b x0.92) |
| WA_C2 | L6M | 20.5 (-28710) | 8.4 (-8580) | +6 / +11 (-29932) | +34.6 (+996) | -898 | no (a x0.83, b x0.93) |
| WA_PL_K03 | L6M | 20.5 (-31359) | 8.3 (-9366) | +6 / +11 (-31729) | +34.3 (+677) | +152 | no (a x0.84, b x0.91) |
| WA_PL_K08 | L6M | 19.7 (-30328) | 8.1 (-9228) | +6 / +11 (-29942) | +33.3 (+1155) | +235 | no (a x0.80, b x0.90) |
| WA_PL_M40000 | L6M | 20.0 (-30730) | 8.1 (-9264) | +6 / +11 (-29751) | +32.9 (+793) | -1063 | no (a x0.81, b x0.90) |
| WA_PL_M90000 | L6M | 20.4 (-31217) | 8.5 (-9578) | +6 / +13 (-32177) | +34.9 (+787) | -486 | no (a x0.83, b x0.94) |
| WA_PL_P20000 | L6M | 20.1 (-30920) | 8.3 (-9263) | +6 / +11 (-30793) | +34.0 (+838) | +170 | no (a x0.82, b x0.91) |
| WA_PL_P50000 | L6M | 20.1 (-30969) | 8.3 (-9376) | +6 / +11 (-30825) | +33.9 (+948) | +363 | no (a x0.82, b x0.91) |
Metric names not found in the scorecard file print n/a; the full plain-word lines are in /mnt/l2/l2vast/_th_works/q/sc/sc_<SET>.txt. Trend-week test (frozen live week and the five best L6M weeks replayed) is not done yet for these finalists.

## 9. WA_C1 on all 43 months (exact, live panel base, the only finalist run to full length)
WA_C1 is JN04RM plus three extra dials: K7 off while its 15-day Calmar is below 0.5; M7 off while its drawdown from the 7-day window peak is at or above $6,296 (base lots); P7 halved while its 7-day P&L is below -$3,626. Against LPB_BASE the stack maxDD cut is L1M +48.8, L3M +64.1, L6M +61.7, HOLD +44.5, PRE +42.6, X-prime +55.9 (d mean -6,488 / -2,556 / -1,029 / -3,530 / -4,062 / -73 $/wk). Against JN04RM the cut is L1M +2.9, L3M +33.5, L6M +29.0, HOLD +39.8, PRE +14.4, X-prime +15.7 with d mean -1,786 / +933 / +1,302 / -318 / -1,978 / +273 $/wk; equal-mean cuts vs JN04RM L6M +34.0, HOLD +44.1, PRE +20.4, X-prime +21.7. Bi-weekly WF vs LPB_BASE: beats in 89.9% of periods (OOS cut +42.6%, d mean -4,387); WF with JN04RM as the reference: beats in 40.5% of 79 periods (OOS cut +16.7%, d mean -690), so the picks improve on JN04RM in recents and HOLD but are not a majority win in the walk-forward. Rule 2a label: RECENT-ONLY. These three gates were chosen from the first-order screen on windows that include L6M and HOLD, so this is post-hoc; it is a LEAD, not a PASS.
best five L6M weeks by LPB_BASE P&L (ISO week: LPB_BASE / JN04RM / WA_C1 $): 202638: 88836 / 72104 / 60296; 202623: 73836 / 68072 / 51442; 202625: 59099 / 59990 / 59990; 202639: 57178 / 52634 / 35068; 202633: 52499 / 36328 / 30881. Of 25 L6M weeks WA_C1 is negative in 5, JN04RM in 6, LPB_BASE in 6; WA_C1 is positive in 5 of the five best LPB weeks.

## 10. Hand-off to W-J (JN05 dial candidates)
WA_C1 and WA_C2 (definitions in section 1, exact, set json in /mnt/l2/l2vast/_th_sz/ijk/exact/sets, layer configs in /mnt/l2/l2vast/_th_works_a/cfg) are offered as JN05 dial candidates, to be judged only as part of a JN05 that also fixes the three standing-principle defects with the exit and entry rules of W-C, W-N and W-X: on their own they cut drawdown but remove only about 18% of full stops and give-backs (section 8). Plateau of the WA_C1 thresholds: rows WA_PL_* in section 1 (L6M exact; read them against WA_C1 +29.0 cut / +1,302 d mean vs JN04RM). Scorecards: section 8 and /mnt/l2/l2vast/_th_works/q/sc/sc_WA_C1.txt, sc_WA_C2.txt.

