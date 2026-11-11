# DS3_WORKS - T-WORKS expand-what-works (aggregate page; built by W-J; 2026-11-11T18:00:10Z; Shadow only, no PASS claims)

Sections A, B, C are the workers' own pages (DS3_WORKS_A/B/C.md) merged below. Section D is W-J: the reference rows (JN04RM vs LPB_BASE), the JN05 composition and the REFIT 2026-11-22 preview. Every number is exact-engine, live panel base (P7 day cap 8,400 + table 7,4,0,4,0,0 + P7 cut 40/5x/w5/p3), reference LPB_BASE, ROLLFIX1.

## D0. Reference rows (exact, rule mode, 43 months)

| cell | window | mean $/wk | mean_ref (LPB_BASE) | maxDD | maxDD_ref | cut % | d mean | WF beat % | label |
|--|--|--|--|--|--|--|--|--|--|
| JN04RM | L1M | 10653 | 17539 | 27056 | 51253 | +47.2 | -6886 | 90 |  |
| JN04RM | L3M | 15022 | 17224 | 41699 | 77224 | +46.0 | -2202 | 90 |  |
| JN04RM | L6M | 19862 | 21495 | 41699 | 77224 | +46.0 | -1633 | 90 | OK-PRIOR (allow 25.0%, WF 90%) |
| JN04RM | HOLD | 12954 | 16540 | 72757 | 78842 | +7.7 | -3586 | 90 |  |
| JN04RM | PRE | 8714 | 10548 | 66714 | 99479 | +32.9 | -1834 | 90 |  |
| JN04RM | X' | 2195 | 2553 | 64077 | 122553 | +47.7 | -357 | 90 |  |

LPB_BASE is the reference itself (cut 0, d mean 0 by construction).

## D1. Harness reproduction check

| month | trades JN04RM / JN05W_REF | net JN04RM | net JN05W_REF | trade-by-trade identical (book, lots, entry_ns, exit_ns, net) |
|--|--|--|--|--|
| 202610 | 858 / 858 | 20778.50 | 20778.50 | IDENTICAL |
| 202608 | 695 / 695 | 38461.34 | 38461.34 | IDENTICAL |

Verdict: JN04RM reproduced through the W-J harness to the dollar.

## D2. JN05 composition and REFIT preview (W-J)

Status at the first build: harness ready, no A/B/C winners have landed, so JN05 has not been composed or scored.

Harness (code/th_works_j; reads and runs only; shared files append-only). mkset.py builds a set json as a copy of JN04RM with overrides (jnrule config, cde state rule, hooks/hooklist, mtab table, zact). run_one.sh runs ONE set per job through the IJK driver (jbjobs, JointRep, ROLLFIX1 patched engine) with one worker, gated on MemAvail of at least 62 GB sustained 60 s and aborting under 41 GB. score_w.py scores any runs_rf cell against the live panel base reference LPB_BASE on L1M, L3M, L6M, HOLD, PRE and X', with the bi-weekly walk-forward over the 43 contiguous months and the rule 2a label. A month of the full stack takes about four minutes on one worker, so a full 43-month set is about three hours on one worker. The new composition names carry the prefix JN05W because the name JN05 is already taken by an old IJK first-order stack (set json JN05.json, HOLD runs only).

Reproduction: JN04RM re-run through this harness as the set JN05W_REF (identical config, one set per job) is identical trade by trade to the stored JN04RM in 202610 (858 trades, net 20,778.50) and 202608 (695 trades, net 38,461.34); see D1. The scorer also reproduces the stored lpb_rm_scores.csv for JN04RM to the digit (L6M cut +46.0, mean 19,862 against LPB_BASE 21,495; HOLD +7.7; PRE +32.9; X' +47.7; WF 90%).

Plan once winners land. Candidate layers per family: dial layers from DS3_WORKS_A (performance gates, volatility dial, exposure caps), regime-conditional exits from DS3_WORKS_B, P7 re-entry and Asia rules from DS3_WORKS_C, plus the existing leads JX01 to JX07 (being re-run one set per job by SZ-CDE) and the C2 regime stacks. Each layer enters as top-K from its own page, then coordinate descent in the exact engine on top of JN04RM, one set per job, L6M then HOLD then PRE then X', then the 43-month walk-forward. Rule 2a floors apply: PRE mean not worse than the 25% floor, recents-first ranking. The two live weeks (frozen week 11-01..05 only; 11-09..11 live data is not on the box) are replayed through the engine replay (code/th_r13) with the JN05W rules at the end.

Not yet available: JN05W composition, live-week replay, REFIT 2026-11-22 preview with JN05W. For reference the existing first-order REFIT dry run (DS3_JOINT_2.md C3) does not select the four JN04 layers on the 26-week training window.


## A. Generalise the dials (W-A)

Source DS3_WORKS_A.md (mtime 2026-11-11T17:59:11Z UTC), included verbatim, read only:

# DS3_WORKS_A - T-WORKS part A: generalised risk dials (W-A)
Refreshed 2026-11-11 17:59Z. Shadow only, no PASS claims, label PRE-PROOF (post-hoc). Prereg: autopilot/WORKS_A_PREREG.md (sha in DECISIONS.md, plus an addendum for the composites and cap sets). Code: outputs/code/th_works_a. Data: /mnt/l2/l2vast/_th_works_a.

## 0. Status and method
Exact sets with the L6M window complete: 8; with HOLD complete: 0. First-order screens (all on the exact LPB_BASE trade list, 20,808 trades, and again on the exact JN04RM trade list, 21,783 trades; the dial state is always the LPB_BASE shadow base-lot P&L, which is what the live state sees): A1 17756 cells, A2 1176 cells, A3 3960 cells per base. Exact runs go one set per job through the harness code/th_works_a/wa_run.py (WorksMixin generalises the JN04 rule-mode layers; it reproduces LPB_EMPTY and JN04RM trade by trade on 202610 and 202608, see DECISIONS.md). Every exact set below is JN04RM plus the named change, so each row answers whether the dial adds to the live-form JN04 stack. A cut is the stack maxDD cut in per cent; d mean is the weekly mean difference in dollars with the carrying week dropped.

## 1. Exact results (windows complete only; vs JN04RM = the same set measured against the JN04RM exact series)
| set | change on top of JN04RM | L6M vs LPB_BASE cut / d mean | L6M vs JN04RM cut / d mean / eq-mean cut | HOLD vs LPB_BASE cut / d mean | HOLD vs JN04RM cut / d mean / eq-mean cut |
|--|--|--|--|--|--|
| WA_A1_07 | STACK calmar D7 thr0.5 firstwin x0.5 | +52.0 / -3711 | +11.2 / -1399 / +2.9 | not yet | not yet |
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
| WA_A1_07 | +18.1 | +11.2 |
| WA_A2_18 | +20.5 | -24.4 |
| WA_A2_19 | +37.1 | +5.8 |
| WA_A2_20 | +16.8 | -2.1 |
| WA_A2_21 | +10.9 | +10.4 |
| WA_A2_22 | +19.4 | +5.9 |

Rank correlation (Spearman) first-order vs exact over 6 sets: -0.43. First-order overstates dials that skip signals (a skipped signal frees the book for the next one, and day caps, locks and re-entries move) and is used for ranking only.

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



## B. Regime-conditional exits (W-B)

Source DS3_WORKS_B.md (mtime 2026-11-11T17:34:29Z UTC), included verbatim, read only:

# DS3_WORKS_B - T-WORKS part B (W-B): regime flag and regime-conditional exits. Page 1, 2026-11-11T17:34Z (date -u)

STATUS: Shadow only, post-hoc, no PASS claims, PRE-PROOF. Prereg autopilot/WORKS_B_PREREG.md (sha256 2167fd1caa1fdef7, DECISIONS.md). Base LPB_BASE exact (ROLL-fixed engine); every exact row below is one set per job, 43 months unless the months column says fewer; a window is shown only when all its months ran. cut = stack maxDD cut vs LPB_BASE in % (negative = deeper), dmean = mean change in dollars per week, eq_cut = equal-mean cut. Code code/th_works_b (wb_flags, wb_state, wb_hooks, wb_score). Hook identity tests passed to the dollar (WB_ID cut hook, WB_BR_ID bracket hook: 904 trades, 202,420.96 identical to LPB_BASE on 202606).

## 0. Plain sentences (page 1)
1. No causal flag from the working dials separates the live trend week from choppy weeks well. Last week (frozen file 11-02..05, 53 P7 trades) the P7 LOT gate was cold on every signal (Calmar10 below 1 all four days, even though P7 made 24.8k, 21.2k, 9.1k, 31.0k shadow base-lot dollars on the four days) because the ten days before were losses; "cold" therefore marks chop in history but was a lagging, wrong signal in the live trend week. ER(20) at the signal sat at the median of all weeks (percentile 0.38 of weekly share at 0.30), REG hot (atr_rel >= 1.3) was high (live week share 0.60 vs median 0.46, percentile 0.76; atr_rel >= 1.1: 0.81 vs 0.59, percentile 0.86), the family H day flags were the sharpest (F_ER share 0.23 vs median 0.07, percentile 0.94; F_ER2 0.23, percentile 0.80). Persistence: LOT and stack-Calmar states last 13-24 P7 signals; REG and ER20 flip every 2 signals (P(same next signal) 0.52-0.75), F_ER 0.89, F_PRIOR 0.91 (8 signals).
2. The P7 state cut (40/5x/w5/p3) is NOT earning its place in the exact engine on three of four windows: never cutting P7 (WB_C_NONE) gives stack maxDD cut +19.1 percent L6M, +10.4 PRE, +27.4 X' (mean +2,180, +964, +46 dollars per week) and loses only in HOLD (-19.1 percent, mean -1,016). Bi-weekly WF of NONE vs LPB_BASE: +9.95 percent OOS cut, mean +350, beats LPB in 14.9 percent of the 74 periods. The first-order hold-universe screen had said the opposite (never cut: -33.9 percent L6M); exact decides (re-entries and locks free up).
3. Conditional loss cut. Per-trade first-order regret (hold-to-bracket minus the cut, P7 StateCut trades, week-block bootstrap): REG hot atr_rel >= 1.5 (+338 per cut, 90 percent CI 45 to 642), >= 1.8 (+345, 64 to 639) and ER20 >= 0.30 with LOT warm (+530, 103 to 985) are the flags where the cut costs more; F_ER (trend day so far) goes the OTHER way (cut saves 1,184 per trade more on F_ER days). EXACT: switching the P7 cut off when atr_rel >= 1.5 (WB_B2_REG15, L6M) is worse: cut -11.1 percent, dmean -579. Switching it off when the stack Calmar5 >= 1 (WB_B2_STK5, 40 of 43 months): L6M cut 0.0 / mean +2,159, PRE -1.3 / +44, HOLD +2.1 / -845; one cut-active-only-after-a-trend-day set (WB_B2_FPRI, F_PRIOR) shows L6M +30.7 / +4,119 on 7 months (other windows running). Family max-stat over 86 flag x direction day-level mixtures of the two exact runs (cut on / cut off): best mean cut 17.3 vs null max 95th percentile 24.1, p 0.69: no flag beats random mixing of cut and no-cut days at the day level, so no conditional cut is claimed; the finding is the NONE row.
4. Live replay of the cuts (frozen week, hold-to-bracket counterfactual on the 1-s mid path, no re-entries): P7 24 cuts = 17 saves (-29.9k) and 7 recoveries (+69.1k), net hold better by +39.3k; K7 30 cuts: 25 saves (-15.0k), 5 recoveries (+11.4k); M7 13 cuts: 11 saves (-7.0k), 2 recoveries (+7.9k). No flag keeps the saves and drops the recoveries: with cut OFF in the trend state the P7 week gains +30.7k for ER20 >= 0.35, +29.1k for atr_rel >= 1.3, +19.6k for hot and ER20 >= 0.30, but each of these states still contains 4 to 9 saves; LOT warm and stack warm 10-day flags are never true in the live week (0 trend cuts), so they change nothing. The second live week (11-09..11) is NOT on the box: no trade log, no shadow P&L after 11-05, no MBO state days after 11-05 (NQ 1-min OHLCV to 11-10 exists in data/ext_20261110 but not the P&L history the LOT and stack flags need).
5. Conditional profit protection (first-order screens on the LPB_BASE cache, P7 first; exact sets WB_B3_P2/P3/P4 started): the best P7 profit lines lower four-window drawdown only by 16-19 percent at a mean cost of 300 to 3,400 dollars per week, conditioning on chop (ER20 >= 0.30 and LOT warm; stack warm; hot and ER20) raises the worst-window cut from 16.3 to about 19 percent at the same mean cost. In the live week the P7 lines clip 8-10 of 28 targets in either ER state (ER20 does not separate the live week), so the conditional line saves little there (P7 pct>=0.5 ahead_rel>=1.5 take: trend state net +6.5k, chop state -24.8k). K7/M7/U7 (three live lines) conditional vs unconditional: first-order K7 best unconditional line 6.5 percent worst-window cut, conditional on LOT warm 6.1 (no gain), M7 conditional on hot and ER20 trend 4.7 vs 1.2, U7 only in not-dead-tape 5.4 vs 0.0; all below 7 percent and all at a negative mean, none promoted yet.
6. Near-target (B4). The live stand-in as the exact engine can express it (K7/P7/M7 take when price is within 3 pts of target and the favourable extreme is 5 s old, mid-based: policy line `profit K7 * pct>=0.95 secs_fav>=5 take win=5 persist=1`, the same for P7 and M7) is WORSE than no stand-in in L6M: cut -9.1 percent, dmean -1,253 dollars per week (WB_B4_ST). First-order (EX universe, never-cut reference, 43 months) agrees: the stand-in costs 206.7k on K7/P7/M7 (P7 -120.5k) with a worst-window cut of -1.4 to 7.8 percent. The scored replacement is a REGIME RETARGET instead of a take: pull the target in by 8 ticks (2 pts, 58 instead of 60) on K7/P7/M7 only when atr_rel < 1.3 (chop), full 60 target otherwise (WB_B4_R8C): L6M +26.1 percent / +51 dollars per week, HOLD +8.1 / +460, PRE -10.6 / +227, X' +5.2 / -50, L1M -5.8; the unconditional 8-tick retarget (WB_B4_R8A, L6M only so far) is +24.2 / -287. It passes L6M and HOLD and fails PRE on drawdown, so the label is RECENTS-ONLY (rule 2a), and the bi-weekly WF vs LPB_BASE is -10.6 percent OOS cut, beats 12 percent of periods. Stand-in plus conditional retarget (WB_B4_STR8C, L6M): +24.4 / -218 (the take adds nothing).
7. Brackets (B5): P7 stop 45 / target 60 always (WB_B5_P7_4560, L6M): +5.5 / +1,556 (equal-mean +13.4); P7 target 45 when atr_rel < 1.5, else 60 (WB_B5_P_T45): L6M +42.9 / -2,026; P7 target 90 when atr_rel >= 1.5 (WB_B5_P_T90): -6.0 / -590 (trend extension does not pay in L6M). Only L6M exists for these; the chop short target buys drawdown at a mean cost, not a free lunch.
8. Field answer: `regime` (third column of the policy file) can NOT carry the flag as built. DayRegime in DS7.cs is a once-a-day string (vol_lo / vol_mid / vol_hi) set at 10:30 ET from the overnight range vs its median and never reset; rules match it (or the session name) for profit, loss-cut and bracket lines (lines 2136 and 2189). The flags above are per-signal and change every few signals. A new feature is needed: a per-book EntryRegime string ("chop" / "trend", or "cold"/"hot" for LOT/REG) written at signal time from the 5-min ATR (REG, already computed for JN04) and, for stack/LOT states, the daily shadow ledger, stored on the Book and matched by the same third column token (v1.8 field `EntryRegime`, rule match `r.Regime == b.EntryRegime`); the REG-based retarget above needs only atr_rel at signal, which the live code already has.

## 1. B1 flag table (P7 signals, 43 months; trend-direction flags; live week = frozen file 11-02..05, 53 P7 trades)
live_pctile = percentile of the live-week share among all weeks; regret columns = P7 cut regret in dollars per cut trade (hold minus cut), trend state vs chop state, difference with 90 percent week-block bootstrap interval (first-order, hold-universe).
| flag | on_rate | week_share_median | live_week_share | live_pctile | p_same_next_signal | median_run_signals | day_to_day_agree | regret_trend | regret_chop | diff | ci_lo | ci_hi |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ER20>=0.25 | 0.516 | 0.526 | 0.509 | 0.46 | 0.519 | 2 | 0.523 | -31 | -4 | -27 | -298 | 260 |
| ER20>=0.30 | 0.424 | 0.44 | 0.396 | 0.38 | 0.529 | 2 | 0.479 | -12 | -23 | 11 | -336 | 284 |
| ER20>=0.35 | 0.337 | 0.333 | 0.321 | 0.44 | 0.579 | 2 | 0.526 | -41 | -5 | -36 | -418 | 343 |
| ER20>=0.40 | 0.255 | 0.25 | 0.226 | 0.36 | 0.642 | 2 | 0.639 | -46 | -8 | -38 | -323 | 313 |
| REG hot atr_rel>=1.1 | 0.598 | 0.588 | 0.811 | 0.86 | 0.708 | 2 | 0.67 | 8 | -65 | 73 | -196 | 330 |
| REG hot atr_rel>=1.3 | 0.482 | 0.455 | 0.604 | 0.76 | 0.707 | 2 | 0.623 | 66 | -107 | 173 | -116 | 455 |
| REG hot atr_rel>=1.5 | 0.396 | 0.375 | 0.547 | 0.81 | 0.717 | 2 | 0.637 | 179 | -159 | 338 | 45 | 642 |
| REG hot atr_rel>=1.8 | 0.294 | 0.3 | 0.321 | 0.55 | 0.75 | 2 | 0.712 | 222 | -124 | 345 | 64 | 639 |
| dead atr_rel<=0.6 (chop-ish) | 0.044 | 0.0 | 0.0 | 0.27 | 0.937 | 2 | 0.929 | -909 | 12 | -921 | -1569 | -297 |
| dead atr_rel<=0.9 (chop-ish) | 0.245 | 0.231 | 0.075 | 0.16 | 0.761 | 2 | 0.721 | 11 | -26 | 37 | -316 | 394 |
| LOT warm (P7 Cal10>=1) | 0.399 | 0.235 | 0.0 | 0.21 | 0.975 | 23 | 0.867 | 146 | -131 | 277 | -22 | 547 |
| LOT warm Cal10>=2 | 0.252 | 0.0 | 0.0 | 0.29 | 0.978 | 19 | 0.883 | -51 | -7 | -45 | -362 | 284 |
| STACK warm Cal5>=1 | 0.419 | 0.389 | 0.302 | 0.42 | 0.951 | 13 | 0.736 | 96 | -98 | 194 | -75 | 452 |
| STACK warm Cal10>=1 | 0.491 | 0.389 | 0.0 | 0.17 | 0.975 | 18 | 0.866 | -71 | 34 | -105 | -372 | 135 |
| STACK warm Cal20>=1 | 0.572 | 0.56 | 0.0 | 0.18 | 0.986 | 24 | 0.924 | -55 | 32 | -87 | -366 | 182 |
| F_ER | 0.09 | 0.065 | 0.226 | 0.94 | 0.887 | 3 | 0.87 | -1089 | 95 | -1184 | -1684 | -665 |
| F_ER2 | 0.153 | 0.154 | 0.226 | 0.8 | 0.817 | 2 | 0.785 | 120 | -47 | 168 | -205 | 512 |
| F_PRIOR | 0.361 | 0.314 | 0.189 | 0.28 | 0.909 | 8 | 0.515 | -16 | -19 | 3 | -269 | 256 |
| ER20>=0.30 & LOT warm | 0.171 | 0.091 | 0.0 | 0.21 | 0.81 | 2 | 0.76 | 413 | -117 | 530 | 103 | 985 |
| ER20>=0.30 | F_ER | 0.448 | 0.458 | 0.491 | 0.62 | 0.532 | 2 | 0.479 | -55 | 13 | -68 | -364 | 244 |
| hot1.3 & ER20>=0.30 | 0.196 | 0.19 | 0.264 | 0.77 | 0.732 | 2 | 0.76 | 142 | -64 | 206 | -170 | 612 |

## 2. Exact rows (vs LPB_BASE; this page 1)
| set | months | cut_L1M | dmean_L1M | eq_cut_L1M | cut_L3M | dmean_L3M | eq_cut_L3M | cut_L6M | dmean_L6M | eq_cut_L6M | cut_HOLD | dmean_HOLD | eq_cut_HOLD | cut_PRE | dmean_PRE | eq_cut_PRE | cut_X' | dmean_X' | eq_cut_X' |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| WB_C_NONE | 43 | 3.3 | -345.6 | 13.4 | 19.1 | 5552.3 | 27.6 | 19.1 | 2180.2 | 27.6 | -19.1 | -1015.8 | -6.6 | 10.4 | 964.1 | 19.8 | 27.4 | 45.5 | 35.0 |
| WB_B2_REG15 | 6 | -16.4 | -2228.9 | -20.2 | -11.1 | -2546.6 | -14.7 | -11.1 | -578.6 | -14.7 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B2_STK5 | 40 | 0.0 | -402.6 | 10.4 | 0.0 | 484.0 | 10.4 | 0.0 | 2159.2 | 10.4 | 2.1 | -845.1 | 12.2 | -1.3 | 44.4 | 9.2 | 33.8 | 797.6 | 40.6 |
| WB_B2_FPRI | 7 | 9.4 | 705.4 | 25.8 | 30.7 | 7365.2 | 43.2 | 30.7 | 4119.1 | 43.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B3_P4 | 4 | -2.1 | -4156.8 | -96.2 | 32.2 | -1706.7 | -30.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B4_ST | 6 | -2.6 | 282.0 | -9.9 | -9.1 | 396.3 | -16.8 | -9.1 | -1253.3 | -16.8 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B4_R8A | 6 | -9.5 | -2048.5 | -11.2 | 24.2 | 803.4 | 23.1 | 24.2 | -287.2 | 23.1 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B4_R8C | 43 | -5.8 | -1049.6 | -5.5 | 26.1 | 789.8 | 26.3 | 26.1 | 51.3 | 26.3 | 8.1 | 460.1 | 8.4 | -10.6 | 227.2 | -10.3 | 5.2 | -50.2 | 5.4 |
| WB_B4_STR8C | 6 | -4.2 | -274.4 | -5.4 | 24.4 | 923.8 | 23.6 | 24.4 | -218.2 | 23.6 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B5_P7_4560 | 6 | 0.0 | 1995.4 | 8.4 | 5.5 | 1256.6 | 13.4 | 5.5 | 1556.1 | 13.4 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B5_P_T90 | 6 | -7.2 | -1036.3 | -11.0 | -6.0 | -1176.8 | -9.7 | -6.0 | -590.4 | -9.7 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B5_P_T45 | 6 | 14.0 | 4219.7 | 4.5 | 42.9 | 1159.7 | 36.6 | 42.9 | -2025.9 | 36.6 | nan | nan | nan | nan | nan | nan | nan | nan | nan |

Exact notes: WB_C_NONE = P7 cut off (43 months). WB_B2_REG15 = cut off when atr_rel >= 1.5. WB_B2_STK5 = cut off when stack Calmar5 >= 1 (40 of 43 months; X' column is from the months shown only when the window is complete). WB_B2_FPRI = cut active only when the prior day trended (7 months). WB_B3_P4 = P7 `profit P7 * pct>=0.7 pulled_against_mult>=5 tighten 10 win=5 persist=1` ON in chop (hot1.3 and ER20 >= 0.30 false), 4 months, no complete window yet. WB_B4_* = K7/P7/M7 near-target / retarget; WB_B5_* = P7 brackets (L6M).

## 3. Live-week replay summary (frozen week; flag state at the signal second; hold-to-bracket counterfactual; data /mnt/l2/l2vast/_works_b/live_cut_replay.csv)
Cuts by book and kind (hold minus live, dollars): see section 0 item 4. P7 lines flagged per cut: of the 7 recoveries (rows 11-03 x2, 11-04 x3, 11-05 x2) atr_rel >= 1.3 was true on 5, ER20 >= 0.30 on 3, hot and ER20 on 2; of the 17 saves atr_rel >= 1.3 was true on 9, ER20 >= 0.30 on 6. The flag would have switched off 5 of the 7 recovery cuts and 9 of the 17 saves (REG), i.e. it does not keep the saves.

## 4. Missing
11-09..11 live trades and shadow P&L; MBO state days after 11-05 (NQ OHLCV 1-min to 11-10 only). Exact conditional sets still queued: WB_B2_ERLOT, WB_B2_FER (reverse control), WB_B3_P1/P2/P3, other windows of WB_B2_FPRI and WB_B3_P4; first-order K7/M7 conditional cut not run exact.



## C. P7 anatomy (W-C)

Source DS3_WORKS_C.md (mtime 2026-11-11T17:34:49Z UTC), included verbatim, read only:

# DS3_WORKS_C - T-WORKS Part C (P7 anatomy), W-C, page2026-11-11 17:34Z (C1 anatomy, C3/C4 L6M exact rows, C2 queued)
Label: PRE-PROOF, post-hoc, descriptive, Shadow only, no PASS claim. Prereg autopilot/WORKS_C_PREREG.md (sha in DECISIONS.md 13:35Z). Source: the exact LPB_BASE trade list (live panel base: P7 day cap 8,400, 7/4/4, P7 cut 40/5x/w5/p3, no JN04 dials), 4,958 P7 trades 2023-04..2026-10, plus the 53 P7 trades of the frozen live week 11-01..05 (data/live_frozen reconstructed file; live fees proxied at $4.84 per contract). Features are causal at the signal second (NQ 1-min bars, ER(20) on 5-min, atr_rel = 5-min ATR over its 20-day norm, LOT state = P7 shadow Calmar over the last 10 label days from the same list). Code code/th_works/c1_build.py, c1_cells.py, c1_excess.py, c1_page.py; table /mnt/l2/l2vast/_th_works/c/c1_cells.csv.

## C1 in plain sentences
1. P7 earns $897k over the 3.5 years in this base, $237k in L6M, and $85k in the live week (28 targets, 24 cuts, 1 BookLock). Its 20 worst weeks lose $552k together. Winners are targets at a flat 60 points (mean about +$4,000 per trade in L6M) and losers are StateCuts at a mean of about -$3,000 per trade; P7 wins only about 45 percent of its trades, so the week is decided by the cut rate.
2. A worst-20 week is not a busy week (26.5 P7 trades in both the worst and the other weeks). It is a week where 62 percent of trades end as StateCuts against 50 percent in other weeks, i.e. the same entries, but the trend continues through the cut instead of reverting to target.
3. Where the worst weeks sit (excess loss = worst-week net minus what the same cell earns per trade in other weeks): Asia is the largest carrier (284 trades in worst weeks, mean -$1,475 against +$580 in other weeks, 76 percent of the worst-20 loss; Asia is also where 80 percent of the 3.5-year profit comes from). By lots, 7-lot trades (all Asia in the live table) lose -$3,557 per trade in worst weeks against +$1,037 otherwise: 98 trades carry -$349k of the -$552k. 4-lot trades are flat over the whole history (-$3 per trade outside worst weeks) and lose -$1,240 in worst weeks.
4. Trend state matters, a result that matches the live week: signals taken WITH a session move of more than 1 ATR (the trend is already running in the trade direction, 3,270 trades) carry 66 percent of the worst-20 loss, and entries after a P7 loss, within 30 minutes of the last P7 exit, and with K7/U7/M7 already open on the same side are all over-represented. These are one regime seen from several sides: a trending Asia session where P7 keeps re-entering the same direction, gets cut, and re-enters. In L6M the worst 5 weeks (202644, 202631, 202636, 202635, 202621) show the same shape: with-trend, short side (87 percent of the L6M worst-5 loss is on the short side), inside 30 minutes of the last exit (96 percent), third-or-later trade of the session (72 percent).
5. What the table says about the dials: LOT state "cold" (Calmar10 < 1) is true for 3,000 of 4,958 trades, and cold trades earn MORE per trade in L6M (+$357) than warm ones (+$55) while also carrying 73 percent of the worst-20 loss. So the LOT dial (halve when cold) cuts both the winners and the losers of a state that is cold 60 percent of the time; it is a drawdown dial, not a profit dial, and in the live week all 53 P7 trades were taken cold (Calmar10 mean 0.07) so the JN04 LOT dial would have been halving lots all week while 28 targets paid +$159k (this is an inference from the LPB shadow Calmar, to be confirmed by replaying JN04RM on the live week). This is the same finding as the loss-cut page: the dials are right in chop and wrong in trend.
6. ER(20) and atr_rel do not separate the carriers cleanly. ER above 0.45 has the worst per-trade loss in worst weeks (-$2,269 against +$798 otherwise) but ER below 0.15 loses little in worst weeks (-$208 per trade); atr_rel above 1.6 is the only atr bucket negative in L6M (-$373 per trade, -$70k net) but earned +$27 per trade over 3.5 years. The live week was atr_rel above 1.6 for 27 of 53 trades and made +$39k there. So REG (atr_rel >= 1.3) is a poor stand-alone chop/trend flag for P7; the cleaner conditional flags in the table are "with-trend entry" and "same-side re-entry inside 30 minutes".
7. Side: shorts carry 54 percent of the 3.5-year worst-week loss and 87 percent in L6M; the whole L6M bad stretch is short Asia (308 trades, +$956 other weeks, -$1,175 in worst-5 weeks).
8. Live week: 53 trades, +$84.8k net of proxy fees. 24 StateCuts/PolicyCuts cost -$74k and 28 targets made +$159k. 33 of 53 trades were the 3rd or later P7 trade of the session, 29 were taken inside 30 minutes of the previous P7 exit (+$52.9k), 33 were with-trend. The with-trend and within-30-minutes cells were the winners that week; in the five worst L6M weeks the same cells were the losers. That is the regime flag problem in one sentence: the same cell wins in a trend that persists and loses when it stalls, so a causal flag must be about persistence of the session move, not about the cell.

## Worst-20 P7 weeks of the 3.5 years (LPB_BASE trades)
| ISO week | P7 trades | net $ | StateCut share % | Asia share % | mean lots | mean atr_rel |
|---|---|---|---|---|---|---|
| 202644 | 40 | -43324 | 70 | 78 | 4.0 | 1.34 |
| 202411 | 19 | -41863 | 58 | 42 | 3.6 | 1.54 |
| 202528 | 25 | -34733 | 72 | 48 | 3.2 | 1.13 |
| 202331 | 26 | -31799 | 58 | 35 | 3.7 | 1.94 |
| 202436 | 35 | -31352 | 66 | 46 | 3.3 | 1.66 |
| 202515 | 73 | -30999 | 55 | 66 | 3.5 | 2.93 |
| 202329 | 14 | -29606 | 64 | 43 | 3.4 | 1.69 |
| 202604 | 24 | -29549 | 71 | 46 | 3.5 | 1.81 |
| 202409 | 24 | -28036 | 62 | 33 | 3.0 | 1.49 |
| 202517 | 32 | -27072 | 53 | 59 | 3.8 | 0.94 |
| 202541 | 22 | -25793 | 64 | 45 | 3.8 | 1.45 |
| 202434 | 20 | -24356 | 70 | 45 | 3.3 | 1.15 |
| 202533 | 16 | -24142 | 62 | 50 | 3.2 | 1.40 |
| 202447 | 16 | -23135 | 62 | 75 | 4.6 | 1.18 |
| 202318 | 10 | -22701 | 70 | 60 | 4.9 | 1.13 |
| 202428 | 15 | -22213 | 60 | 60 | 3.6 | 1.43 |
| 202631 | 42 | -21798 | 60 | 64 | 3.8 | 1.29 |
| 202606 | 39 | -21032 | 62 | 59 | 3.7 | 2.14 |
| 202326 | 21 | -19455 | 67 | 24 | 2.7 | 1.70 |
| 202346 | 16 | -18651 | 62 | 44 | 3.3 | 1.13 |

## The P7 table (every cell: all 3.5 years, L6M, the live week, and the share of the worst-20-week loss it carries)
Cell definitions: ER bucket = ER(20) of 5-min closes at the signal; atr_rel = 5-min ATR(14) / 20-day median of daily medians; LOT cold = P7 shadow Calmar over the previous 10 label days < 1.0; P7 order = 1st / 2nd / 3rd or later P7 signal of the same session-day; since last P7 exit = minutes between the previous P7 exit and this signal; side vs session move = (signal close minus first close of the session) x side in 5-min ATRs; K7/U7/M7 open = another of those books holds lots at the signal second, same side or opposite. The "exit" rows are outcomes, not features.

| cut | cell | n 3.5y | net $k | mean $/trade | win % | n L6M | net $k | mean | win % | n live wk | net $k | mean | win % | worst-20-wk net $k | share of worst-20 loss % |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| session | asia | 2246 | +719 | +320 | 45 | 558 | +202 | +362 | 47 | 31 | +69 | +2220 | 55 | -419 | 76 |
| session | london | 1520 | +224 | +147 | 45 | 330 | +58 | +175 | 47 | 15 | +0 | +9 | 40 | -76 | 14 |
| session | nyam | 1192 | -46 | -38 | 44 | 129 | -23 | -179 | 42 | 7 | +16 | +2266 | 71 | -57 | 10 |
| lots | 1 | 879 | +154 | +175 | 49 | 145 | +46 | +317 | 54 | 1 | +1 | +1195 | 100 | +1 | -0 |
| lots | 2 | 1212 | -99 | -82 | 40 | 232 | +1 | +4 | 42 | 7 | +1 | +148 | 43 | -44 | 8 |
| lots | 3 | 245 | +485 | +1979 | 74 | 42 | +102 | +2424 | 81 | 2 | +7 | +3590 | 100 | +44 | -8 |
| lots | 4 | 1764 | -243 | -138 | 40 | 394 | -32 | -81 | 42 | 24 | +8 | +351 | 42 | -238 | 43 |
| lots | 5 | 61 | +224 | +3678 | 79 | 15 | +80 | +5323 | 93 | 3 | +12 | +3946 | 67 | +34 | -6 |
| lots | 7 | 797 | +376 | +472 | 46 | 189 | +40 | +213 | 43 | 15 | +43 | +2879 | 60 | -349 | 63 |
| ER(20) 5-min | .15-.3 | 1454 | -57 | -39 | 42 | 311 | -32 | -102 | 42 | 19 | +19 | +1000 | 47 | -127 | 23 |
| ER(20) 5-min | .3-.45 | 1158 | +282 | +243 | 45 | 223 | +67 | +302 | 46 | 10 | +39 | +3876 | 60 | -181 | 33 |
| ER(20) 5-min | <.15 | 1463 | +252 | +172 | 45 | 331 | +131 | +397 | 50 | 15 | +11 | +754 | 53 | -30 | 5 |
| ER(20) 5-min | >.45 | 882 | +415 | +471 | 48 | 152 | +70 | +459 | 47 | 9 | +16 | +1749 | 56 | -213 | 39 |
| atr_rel | .8-1 | 785 | +344 | +438 | 48 | 218 | +185 | +849 | 52 | 5 | +17 | +3382 | 60 | -65 | 12 |
| atr_rel | 1-1.3 | 920 | +262 | +285 | 46 | 272 | +56 | +206 | 48 | 15 | +14 | +944 | 47 | -148 | 27 |
| atr_rel | 1.3-1.6 | 616 | +0 | +1 | 41 | 132 | +19 | +142 | 43 | 4 | +11 | +2856 | 75 | -108 | 20 |
| atr_rel | <.8 | 850 | +247 | +291 | 46 | 208 | +47 | +224 | 45 | 2 | +3 | +1683 | 50 | -109 | 20 |
| atr_rel | >1.6 | 1774 | +49 | +28 | 44 | 187 | -70 | -373 | 41 | 27 | +39 | +1443 | 52 | -122 | 22 |
| LOT state (Calmar10 of P7) | cold | 3000 | +707 | +236 | 45 | 600 | +214 | +357 | 47 | 53 | +85 | +1600 | 53 | -400 | 73 |
| LOT state (Calmar10 of P7) | na | 10 | +7 | +701 | 50 | 0 |  |  |  | 0 |  |  |  | +0 | -0 |
| LOT state (Calmar10 of P7) | warm | 1948 | +183 | +94 | 44 | 417 | +23 | +55 | 45 | 0 |  |  |  | -152 | 27 |
| P7 order in session | 1st | 2213 | +548 | +248 | 46 | 267 | +152 | +569 | 50 | 10 | +6 | +604 | 50 | -163 | 29 |
| P7 order in session | 2nd | 1349 | +198 | +147 | 43 | 242 | -26 | -106 | 41 | 10 | +35 | +3495 | 70 | -163 | 30 |
| P7 order in session | 3rd+ | 1396 | +151 | +108 | 44 | 508 | +110 | +217 | 47 | 33 | +44 | +1328 | 48 | -226 | 41 |
| since last P7 exit | 1-2h | 597 | +102 | +171 | 45 | 105 | +22 | +210 | 44 | 6 | -1 | -178 | 50 | -57 | 10 |
| since last P7 exit | 2-6h | 332 | +27 | +82 | 45 | 39 | -16 | -400 | 46 | 3 | +8 | +2594 | 67 | -19 | 3 |
| since last P7 exit | 30-60m | 971 | +14 | +14 | 43 | 230 | +34 | +150 | 47 | 11 | +21 | +1893 | 64 | -142 | 26 |
| since last P7 exit | <30m | 2351 | +436 | +185 | 45 | 529 | +75 | +142 | 45 | 29 | +53 | +1824 | 48 | -221 | 40 |
| since last P7 exit | >6h | 706 | +313 | +443 | 47 | 114 | +121 | +1059 | 54 | 4 | +4 | +1094 | 50 | -113 | 20 |
| last P7 trade | after_loss | 2736 | +346 | +127 | 44 | 547 | +68 | +124 | 45 | 26 | +53 | +2023 | 62 | -341 | 62 |
| last P7 trade | after_win | 2221 | +546 | +246 | 46 | 470 | +169 | +360 | 48 | 27 | +32 | +1193 | 44 | -211 | 38 |
| last P7 trade | none | 1 | +5 | +4795 | 100 | 0 |  |  |  | 0 |  |  |  | +0 | -0 |
| side vs session move | against<1 | 456 | -110 | -242 | 40 | 82 | +24 | +292 | 50 | 4 | +2 | +561 | 50 | -44 | 8 |
| side vs session move | against>1atr | 486 | +62 | +127 | 42 | 110 | +14 | +130 | 45 | 11 | +14 | +1269 | 45 | -95 | 17 |
| side vs session move | with<1 | 745 | +295 | +397 | 47 | 148 | +60 | +406 | 47 | 5 | +7 | +1462 | 60 | -50 | 9 |
| side vs session move | with>1atr | 3270 | +645 | +197 | 45 | 677 | +138 | +204 | 46 | 33 | +61 | +1858 | 55 | -362 | 66 |
| K7/U7/M7 open | KUM none | 1813 | +35 | +19 | 43 | 401 | +39 | +97 | 45 | 22 | +16 | +714 | 45 | -193 | 35 |
| K7/U7/M7 open | KUM opp only | 601 | +34 | +57 | 43 | 107 | +7 | +61 | 46 | 2 | +2 | +1131 | 50 | -109 | 20 |
| K7/U7/M7 open | KUM same | 2544 | +828 | +326 | 47 | 509 | +191 | +376 | 48 | 29 | +67 | +2305 | 59 | -249 | 45 |
| any other book open | any same | 2943 | +983 | +334 | 47 | 593 | +194 | +327 | 47 | 31 | +60 | +1946 | 55 | -354 | 64 |
| any other book open | none | 1445 | -91 | -63 | 42 | 320 | +39 | +122 | 45 | 20 | +22 | +1111 | 50 | -108 | 20 |
| any other book open | opp only | 570 | +5 | +9 | 42 | 104 | +4 | +37 | 45 | 2 | +2 | +1131 | 50 | -90 | 16 |
| side | long | 2480 | +442 | +178 | 45 | 465 | +58 | +125 | 43 | 23 | +35 | +1539 | 57 | -253 | 46 |
| side | short | 2478 | +455 | +184 | 45 | 552 | +179 | +324 | 49 | 30 | +49 | +1647 | 50 | -299 | 54 |
| exit | BookLock | 22 | -47 | -2125 | 0 | 11 | -22 | -2009 | 0 | 1 | -0 | -114 | 0 | -7 | 1 |
| exit | RollFlat | 13 | +1 | +63 | 69 | 2 | -0 | -159 | 50 | 0 |  |  |  | +0 | -0 |
| exit | StackCut | 10 | -17 | -1749 | 10 | 0 |  |  |  | 0 |  |  |  | -14 | 2 |
| exit | StateCut | 2564 | -7459 | -2909 | 0 | 519 | -1590 | -3064 | 0 | 24 | -74 | -3084 | 0 | -1061 | 192 |
| exit | Stop | 13 | -30 | -2276 | 15 | 3 | -3 | -972 | 33 | 0 |  |  |  | -12 | 2 |
| exit | StopJoin | 71 | -132 | -1857 | 0 | 10 | -25 | -2493 | 0 | 0 |  |  |  | -26 | 5 |
| exit | StopJoinFallback | 39 | -74 | -1887 | 0 | 3 | -5 | -1672 | 0 | 0 |  |  |  | -12 | 2 |
| exit | Target | 2186 | +8644 | +3954 | 100 | 468 | +1883 | +4023 | 100 | 28 | +159 | +5676 | 100 | +580 | -105 |
| exit | TimeBlock | 40 | +11 | +268 | 57 | 1 | -1 | -667 | 0 | 0 |  |  |  | +0 | -0 |

## Excess-loss ranking (worst-20 weeks of 3.5 years, then L6M worst-5 weeks; excess = worst-week net minus n_worst x cell mean in other weeks)
```
ALL 3.5y, worst-20 weeks, 1-way
             cell    n  n_worst  worst_mean  other_mean    excess  worst_net
      sess_n=asia 2246      284     -1475.0       580.0 -583742.0  -418993.0
       lot_b=cold 3000      405      -988.0       426.0 -572692.0  -399988.0
trend_b=with>1atr 3270      344     -1052.0       344.0 -480290.0  -361888.0
         lots_b=7  797       98     -3557.0      1037.0 -450160.0  -348544.0
prev_b=after_loss 2736      354      -962.0       288.0 -442668.0  -340582.0
     side_b=short 2478      282     -1060.0       343.0 -395715.0  -298927.0
   kum_b=KUM same 2544      258      -966.0       471.0 -370985.0  -249355.0
      side_b=long 2480      247     -1023.0       311.0 -329547.0  -252686.0
       gap_b=<30m 2351      260      -848.0       314.0 -302180.0  -220536.0
        er_b=>.45  882       94     -2269.0       798.0 -288243.0  -213252.0
       ord_b=3rd+ 1396      183     -1233.0       310.0 -282388.0  -225567.0
 prev_b=after_win 2221      175     -1206.0       370.0 -275766.0  -211031.0
         lots_b=4 1764      192     -1240.0        -3.0 -237542.0  -238162.0
        ord_b=1st 2213      209      -779.0       355.0 -236837.0  -162714.0
ALL 3.5y, worst-20 weeks, 2-way
                              cell    n  n_worst  worst_mean  other_mean    excess  worst_net
          sess_n=asia & lot_b=cold 1364      220     -1449.0       755.0 -484876.0  -318692.0
            sess_n=asia & lots_b=7  797       98     -3557.0      1037.0 -450160.0  -348544.0
             lots_b=7 & lot_b=cold  486       80     -3608.0      1426.0 -402760.0  -288674.0
   sess_n=asia & trend_b=with>1atr 1228      161     -1620.0       704.0 -374179.0  -260899.0
   sess_n=asia & prev_b=after_loss 1312      189     -1427.0       516.0 -367182.0  -269699.0
    lot_b=cold & prev_b=after_loss 1663      269      -920.0       423.0 -361136.0  -247353.0
    lot_b=cold & trend_b=with>1atr 1960      263      -954.0       361.0 -346043.0  -251027.0
      lots_b=7 & trend_b=with>1atr  549       70     -3513.0      1142.0 -325871.0  -245914.0
        sess_n=asia & side_b=short 1129      158     -1348.0       658.0 -317066.0  -213047.0
         lot_b=cold & side_b=short 1551      219      -970.0       473.0 -316124.0  -212489.0
      sess_n=asia & kum_b=KUM same  934      108     -1676.0       941.0 -282620.0  -180976.0
  trend_b=with>1atr & side_b=short 1697      197     -1023.0       387.0 -277749.0  -201439.0
         sess_n=asia & side_b=long 1117      126     -1634.0       503.0 -269379.0  -205946.0
  prev_b=after_loss & side_b=short 1372      185     -1016.0       429.0 -267331.0  -188045.0
          lot_b=cold & side_b=long 1449      186     -1008.0       377.0 -257636.0  -187499.0
    gap_b=<30m & trend_b=with>1atr 1832      198      -890.0       399.0 -255264.0  -176280.0
       lot_b=cold & kum_b=KUM same 1532      199      -745.0       538.0 -255199.0  -148224.0
prev_b=after_loss & kum_b=KUM same 1353      167     -1045.0       458.0 -251030.0  -174556.0
L6M worst-5 weeks, 1-way
             cell   n  n_worst  worst_mean  other_mean    excess  worst_net
trend_b=with>1atr 677      122      -911.0       450.0 -166036.0  -111167.0
     side_b=short 552       97     -1049.0       616.0 -161562.0  -101776.0
       gap_b=<30m 529       80     -1399.0       416.0 -145232.0  -111916.0
      sess_n=asia 558      116      -629.0       623.0 -145176.0   -72958.0
       lot_b=cold 600      105      -642.0       568.0 -127087.0   -67405.0
       ord_b=3rd+ 508       86      -970.0       459.0 -122917.0   -83412.0
 prev_b=after_win 470       58     -1043.0       557.0  -92833.0   -60505.0
         lots_b=7 189       38     -1676.0       689.0  -89844.0   -63675.0
prev_b=after_loss 547      113      -495.0       285.0  -88141.0   -55958.0
   kum_b=KUM none 401       68      -973.0       315.0  -87606.0   -66183.0
        er_b=>.45 152       29     -1557.0       934.0  -72251.0   -45160.0
       lot_b=warm 417       66      -743.0       205.0  -62575.0   -49058.0
L6M worst-5 weeks, 2-way
                              cell   n  n_worst  worst_mean  other_mean    excess  worst_net
        sess_n=asia & side_b=short 308       65     -1175.0       956.0 -138509.0   -76382.0
    gap_b=<30m & trend_b=with>1atr 398       62     -1688.0       391.0 -128931.0  -104671.0
  trend_b=with>1atr & side_b=short 393       73     -1117.0       648.0 -128847.0   -81512.0
   sess_n=asia & trend_b=with>1atr 352       77      -871.0       736.0 -123797.0   -67099.0
          sess_n=asia & gap_b=<30m 283       55     -1622.0       614.0 -122981.0   -89221.0
          sess_n=asia & ord_b=3rd+ 311       66     -1065.0       665.0 -114204.0   -70291.0
          sess_n=asia & lot_b=cold 339       74      -663.0       863.0 -112904.0   -49035.0
trend_b=with>1atr & kum_b=KUM none 275       51     -1768.0       442.0 -112705.0   -90176.0
         lot_b=cold & side_b=short 350       63     -1069.0       693.0 -111033.0   -67366.0
    lot_b=cold & trend_b=with>1atr 390       71     -1003.0       435.0 -102081.0   -71186.0
      lots_b=7 & trend_b=with>1atr 150       30     -2426.0       876.0  -99061.0   -72781.0
         ord_b=3rd+ & side_b=short 297       54     -1182.0       636.0  -98174.0   -63814.0
P7 trades per week mean n worst20 vs other: 26.45 26.520958083832337
stop/cut rate worst vs other 0.6238185255198487 0.5044027997290584
        size                                     sum                                              
lots_b     1     2     3      4     5      7       1        2        3        4        5         7
half                                                                                              
2023H1   NaN   9.0   3.0   34.0   NaN   29.0     NaN   1628.0  -1922.0 -26218.0      NaN   -7164.0
2023H2   4.0  19.0   7.0   76.0   3.0   56.0  1670.0    518.0  -5627.0 -60299.0   2257.0   -5171.0
2024H1   1.0  18.0   8.0   86.0  11.0   60.0 -1629.0   5910.0   8593.0 -11058.0  45698.0   11054.0
2024H2   3.0  29.0   8.0  136.0  11.0   90.0  1982.0 -28992.0  28777.0  75073.0  35835.0   -4765.0
2025H1  12.0  25.0  22.0  168.0   7.0  145.0  1621.0  -1620.0  72417.0 -76278.0  21901.0  104756.0
2025H2   3.0  22.0  
```

## Open questions for the rest of Part C
Caveats: cells overlap heavily (Asia, 7 lots, cold and with-trend are mostly the same trades), so the excess ranking says where the loss sits, not which flag is causal; LOT cold uses the LPB shadow Calmar (no JN04 gating), and in the live week the Calmar history is the LPB list to 10-30 plus the 11-02..05 live trades (11-01..2 gap); live week trades have no layer features beyond what the signal second gives (no NTZ/zone state).
Running now (exact, JN04RM base, one set per job via jbjobs, 1 worker): C3 blackout sets WC3_S60, S15, S120, B30, B60, then C2 sets WC2_A5, A4, A6, L5, STKA (7/4/4 Asia lots 5/4/6, London 5, STACK on Asia+London). Next: first-order flag-conditional blackout screen from this table; rest-of-session hook; C4 spec.


## Status sentences (page1, 18:00Z; updated by hand each page)
1. The C1 anatomy is complete and is the first section below; the P7 table (every cell, all 3.5 years / L6M / live week / share of the worst-20-week loss) is in it.
2. C3 (re-entry blackout) first-order screen, exact LPB_BASE trade list: a same-side blackout of 15 to 60 minutes after a P7 StateCut or stop is positive at the P7 level in L6M, HOLD and PRE only when the blocked signal is in a hot tape (atr_rel >= 1.3: 30 min same side gives +$1,990/wk L6M, +$995 HOLD, +$592 PRE, -$4 X'); in a calm tape (atr_rel < 1.3) longer blackouts (60 min and above) and "rest of session" lose money (rest-of-session in calm: -$5,009/wk L6M, -$3,753 HOLD). Both-sides blackout is worse than same side in X'. That is the regime split the directive asked for, but it is a first-order screen.
3. The exact runs on the DRESSED base (JN04RM, dials on) say the dials already take most of that: the live 30-minute same-side blackout (WC3_S30) is -5.2 % maxDD cut and -$473/wk in L6M and -5.9 % / -$441 in HOLD against JN04RM, i.e. it does not help once LOT/REG/SIGQ/STACK are on; 120 minutes is worse (-12.0 % L6M); both sides 30 minutes is worse still (-25.5 % L6M, -$1,677/wk). The only positive L6M row so far is the hot-only 60-minute same-side blackout (WC3_H60S: +4.1 %, +$1,380/wk), which is inside the engine noise floor (about 8 % / $1,200 per week) and has not been run on HOLD, PRE, X' yet. Read: on the dressed stack the blackout is not an earner; it is a LEAD at best until H60S passes the other windows.
4. C4: composing the engine's entry-confirmation key with the JN04 rule dials is exact (WC4_REG reproduced JN04RM trade for trade on 202607-202610). Confirm-only-in-hot-tape variants: live sessions (WC4_HOT_LIVE) -1.8 % / -$152 L6M, all sessions (WC4_HOT_ALL) -17.7 % / -$968: neither helps; calm-only and the 30-s / 60-s timeframe variants are still running.
5. C2 first-order (stack level, vs LPB_BASE): moving the Asia lots down loses mean in L6M, HOLD and PRE at every size tried (A=3..6 of 7: d L6M -$3.8k to -$0.7k/wk) and only cuts maxDD in X' and PRE; raising Asia (8/7, 9/7) adds mean (+$0.7k to +$1.7k/wk L6M) and costs maxDD (-4.6 %). The exact Asia sets (WC2_A4/A5/A6, 7/5/4, STACK on Asia) are queued behind the C3/C4 L6M rows.
6. Not done yet: HOLD/PRE/X' for the survivors, bi-weekly WF, the exact flag-conditional runs for the Asia sets, and the 11-09..11 live week replay (that week is not on the box; the week 11-01..05 only contributes the 53 frozen P7 trades above). The compute is memory-bound: only 3 to 4 W-C workers fit under the 62 GB launch gate while the other programs run, about 10 minutes per set-month.




# C2 / C3 / C4 - exact runs (JN04RM = dials ON on the live panel; one set per job; every row is a candidate or reference as labelled; Shadow only)
Cut = maxDD cut vs the reference (positive = shallower), d$ = change in mean $/week, both over the window; noise floor for entry/blackout-type changes is about 8 percent maxDD and about 1,200 $/wk (R4 noise probes). Windows appear only when every month is exact-run.

### C3 blackout, JN04RM base (live = 30 min same side; no-blackout = JN04RM)
| set | months | vs | L1M cut % / d$ | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | L6M worst-20 cell/ref $k | bi-weekly WF beat % | rule-2a label |
|---|---|---|---|---|---|---|---|---|---|---|
| WC3_S15 | 6 | JN04RM | 14.7 / +541 | -1.9 / +180 | n/a | n/a | n/a | 145/138 | n/a | PRE not yet run |
| WC3_S15 | 6 | LPB | 55.0 / -5800 | 45.0 / -1616 | n/a | n/a | n/a | 145/102 | n/a |  |
| WC3_S30 | 14 | JN04RM | -5.6 / -61 | -5.2 / -473 | -5.9 / -441 | n/a | n/a | 139/138 | n/a | PRE not yet run |
| WC3_S30 | 14 | LPB | 44.3 / -6947 | 43.2 / -2396 | 2.3 / -2921 | n/a | n/a | 139/102 | n/a |  |
| WC3_S60 | 6 | JN04RM | 27.1 / -1235 | 12.6 / -450 | n/a | n/a | n/a | 164/138 | n/a | PRE not yet run |
| WC3_S60 | 6 | LPB | 61.5 / -1242 | 52.8 / -1257 | n/a | n/a | n/a | 164/102 | n/a |  |
| WC3_S120 | 6 | JN04RM | 67.3 / +2065 | -12.0 / -1000 | n/a | n/a | n/a | 123/138 | n/a | PRE not yet run |
| WC3_S120 | 6 | LPB | 82.8 / -4764 | 39.5 / -3672 | n/a | n/a | n/a | 123/102 | n/a |  |
| WC3_B30 | 6 | JN04RM | -25.8 / -826 | -25.5 / -1677 | n/a | n/a | n/a | 127/138 | n/a | PRE not yet run |
| WC3_B30 | 6 | LPB | 33.6 / -7712 | 32.2 / -10 | n/a | n/a | n/a | 127/102 | n/a |  |
| WC3_B60 | 1 | JN04RM | 28.5 / -964 | n/a | n/a | n/a | n/a |  | n/a | PRE not yet run |
| WC3_B60 | 1 | LPB | 62.3 / +910 | n/a | n/a | n/a | n/a |  | n/a |  |
| WC3_H15S | 0 | not started | | | | | | | | |
| WC3_H30S | 6 | JN04RM | 16.1 / +322 | -3.7 / +106 | n/a | n/a | n/a | 146/138 | n/a | PRE not yet run |
| WC3_H30S | 6 | LPB | 55.7 / -6497 | 44.0 / -1993 | n/a | n/a | n/a | 146/102 | n/a |  |
| WC3_H60S | 6 | JN04RM | 27.2 / +377 | 4.1 / +1380 | n/a | n/a | n/a | 162/138 | n/a | PRE not yet run |
| WC3_H60S | 6 | LPB | 61.6 / -4662 | 48.2 / -999 | n/a | n/a | n/a | 162/102 | n/a |  |
| WC3_H30B | 6 | JN04RM | 19.1 / +388 | -3.7 / +96 | n/a | n/a | n/a | 145/138 | n/a | PRE not yet run |
| WC3_H30B | 6 | LPB | 57.3 / -6497 | 44.0 / -2035 | n/a | n/a | n/a | 145/102 | n/a |  |
| WC3_H30S_t11 | 0 | not started | | | | | | | | |
| WC3_H30S_t15 | 0 | not started | | | | | | | | |
| WC3_RS | 0 | not started | | | | | | | | |
| WC3_RH | 1 | JN04RM | 35.7 / +528 | n/a | n/a | n/a | n/a |  | n/a | PRE not yet run |
| WC3_RH | 1 | LPB | 66.1 / -5735 | n/a | n/a | n/a | n/a |  | n/a |  |

### C2 P7 Asia table and STACK on Asia, JN04RM base (reference 7/4/4)
| set | months | vs | L1M cut % / d$ | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | L6M worst-20 cell/ref $k | bi-weekly WF beat % | rule-2a label |
|---|---|---|---|---|---|---|---|---|---|---|
| WC2_A4 | 0 | not started | | | | | | | | |
| WC2_A5 | 0 | not started | | | | | | | | |
| WC2_A6 | 0 | not started | | | | | | | | |
| WC2_L5 | 0 | not started | | | | | | | | |
| WC2_STKA | 0 | not started | | | | | | | | |

### C4 P7 45-s confirmation (live: three-bar 45 s, NY-AM/NY-PM), JN04RM base; WC4_REG proved identical to JN04RM
| set | months | vs | L1M cut % / d$ | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | L6M worst-20 cell/ref $k | bi-weekly WF beat % | rule-2a label |
|---|---|---|---|---|---|---|---|---|---|---|
| WC4_NONE | 0 | not started | | | | | | | | |
| WC4_T30 | 0 | not started | | | | | | | | |
| WC4_T60 | 0 | not started | | | | | | | | |
| WC4_HOT_LIVE | 6 | JN04RM | 0.0 / +0 | -1.8 / -152 | n/a | n/a | n/a | 135/138 | n/a | PRE not yet run |
| WC4_HOT_LIVE | 6 | LPB | 47.2 / -6886 | 45.0 / -1641 | n/a | n/a | n/a | 135/102 | n/a |  |
| WC4_HOT_ALL | 6 | JN04RM | 14.5 / -199 | -17.7 / -968 | n/a | n/a | n/a | 107/138 | n/a | PRE not yet run |
| WC4_HOT_ALL | 6 | LPB | 54.8 / -4943 | 36.4 / -3020 | n/a | n/a | n/a | 107/102 | n/a |  |
| WC4_CALM_LIVE | 1 | JN04RM | 0.7 / +24 | n/a | n/a | n/a | n/a |  | n/a | PRE not yet run |
| WC4_CALM_LIVE | 1 | LPB | 47.6 / -6501 | n/a | n/a | n/a | n/a |  | n/a |  |
| WC4_CALM_ALL | 0 | not started | | | | | | | | |
| WC4_HOT_ALL_T30 | 0 | not started | | | | | | | | |

### First-order screens on the exact LPB_BASE trade list (P7 level, d $/wk vs no blackout; blocked trades removed, no follow-on)
| N min | side | flag at the blocked signal | blocked trades | blocked net $k | d L6M $/wk | d HOLD | d PRE | d X' |
|---|---|---|---|---|---|---|---|---|
| 15 | same | all | 201 | -68 | +703 | +578 | +450 | -8 |
| 15 | same | cold | 122 | -31 | +394 | +157 | +297 | -2 |
| 15 | same | warm | 79 | -38 | +309 | +420 | +153 | -6 |
| 15 | same | hot13 | 151 | -73 | +903 | +699 | +424 | -8 |
| 15 | same | calm | 51 | +1 | -200 | -121 | +74 | +0 |
| 15 | same | er_lo | 152 | -51 | +600 | +680 | +124 | +43 |
| 15 | same | er_hi | 52 | -19 | +102 | -102 | +278 | +24 |
| 15 | same | against_or_flat | 69 | -21 | -461 | +153 | +122 | -36 |
| 15 | same | with_trend | 132 | -48 | +1164 | +424 | +329 | +28 |
| 30 | same | all | 411 | -78 | +2164 | +551 | +506 | -4 |
| 30 | same | cold | 235 | -47 | +1163 | +331 | +232 | -37 |
| 30 | same | warm | 176 | -31 | +1001 | +219 | +275 | +32 |
| 30 | same | hot13 | 299 | -116 | +1990 | +995 | +592 | -4 |
| 30 | same | calm | 117 | +28 | +240 | -411 | +21 | +0 |
| 30 | same | er_lo | 328 | -19 | +979 | +396 | +57 | -52 |
| 30 | same | er_hi | 91 | -55 | +1097 | +110 | +461 | +48 |
| 30 | same | against_or_flat | 146 | -19 | +86 | +120 | +215 | -198 |
| 30 | same | with_trend | 266 | -59 | +2078 | +431 | +303 | +194 |
| 60 | same | all | 630 | -3 | +1642 | -11 | +64 | -317 |
| 60 | same | cold | 359 | -16 | +908 | +79 | +188 | -420 |
| 60 | same | warm | 271 | +13 | +734 | -90 | -124 | +103 |
| 60 | same | hot13 | 435 | -48 | +1206 | +138 | +302 | -166 |
| 60 | same | calm | 203 | +43 | +467 | -133 | -229 | -151 |
| 60 | same | er_lo | 518 | +6 | +531 | +607 | -344 | -174 |
| 60 | same | er_hi | 126 | -15 | +1232 | -557 | +439 | -143 |
| 60 | same | against_or_flat | 231 | -4 | +165 | +132 | +68 | -468 |
| 60 | same | with_trend | 407 | +1 | +1523 | -122 | -17 | +151 |
| 120 | same | all | 931 | +45 | +576 | -1507 | +181 | -180 |
| 120 | same | cold | 539 | -9 | +1281 | -515 | +392 | -289 |
| 120 | same | warm | 392 | +54 | -705 | -992 | -211 | +109 |
| 120 | same | hot13 | 609 | -67 | +1468 | -251 | +668 | -121 |
| 120 | same | calm | 332 | +97 | -940 | -1266 | -372 | -28 |
| 120 | same | er_lo | 748 | -22 | +874 | +211 | +67 | -34 |
| 120 | same | er_hi | 211 | +44 | +194 | -1605 | +168 | -47 |
| 120 | same | against_or_flat | 320 | -15 | -153 | -273 | +529 | -427 |
| 120 | same | with_trend | 628 | +53 | +702 | -1201 | -284 | +204 |
| 30 | both | all | 1017 | +106 | +1571 | -902 | +438 | -1950 |
| 30 | both | cold | 599 | +132 | +835 | -746 | +53 | -2218 |
| 30 | both | warm | 418 | -26 | +736 | -156 | +385 | +268 |
| 30 | both | hot13 | 458 | -132 | +2087 | +1249 | +569 | -9 |
| 30 | both | calm | 575 | +221 | -588 | -2187 | +50 | -1777 |
| 30 | both | er_lo | 667 | +45 | +164 | -772 | +328 | -293 |
| 30 | both | er_hi | 427 | +66 | +847 | -450 | -20 | -1542 |
| 30 | both | against_or_flat | 385 | +2 | -479 | -1137 | +832 | -719 |
| 30 | both | with_trend | 726 | +109 | +1642 | -154 | -436 | -1113 |
| 60 | both | all | 1443 | +108 | +1901 | -788 | +349 | -1957 |
| 60 | both | cold | 839 | +154 | +1191 | -967 | -47 | -2233 |
| 60 | both | warm | 604 | -46 | +710 | +179 | +396 | +276 |
| 60 | both | hot13 | 720 | -96 | +1235 | -117 | +964 | +356 |
| 60 | both | calm | 771 | +192 | +256 | -949 | -456 | -2109 |
| 60 | both | er_lo | 1005 | +35 | -92 | -953 | +343 | -22 |
| 60 | both | er_hi | 588 | +86 | +1407 | -511 | +60 | -1770 |
| 60 | both | against_or_flat | 596 | +38 | -594 | -1540 | +787 | -817 |
| 60 | both | with_trend | 1036 | +114 | +894 | -304 | -412 | -1109 |
| session | same | all | 1112 | +203 | -3837 | -4345 | +171 | -524 |
| session | same | cold | 661 | +173 | -3336 | -3315 | +58 | -461 |
| session | same | warm | 451 | +29 | -501 | -1030 | +113 | -62 |
| session | same | hot13 | 642 | -31 | +1173 | -591 | +585 | +52 |
| session | same | calm | 470 | +233 | -5009 | -3753 | -414 | -576 |
| session | same | er_lo | 795 | +51 | -453 | -1013 | +67 | +36 |
| session | same | er_hi | 317 | +152 | -3384 | -3332 | +104 | -559 |
| session | same | against_or_flat | 371 | +79 | -2397 | -1749 | +293 | -661 |
| session | same | with_trend | 741 | +124 | -1440 | -2596 | -122 | +138 |
| session | both | all | 1968 | +169 | -2145 | -5248 | +1561 | -791 |
| session | both | cold | 1160 | +205 | -1858 | -4454 | +768 | -1078 |
| session | both | warm | 808 | -36 | -287 | -794 | +793 | +287 |
| session | both | hot13 | 942 | -145 | +2775 | -349 | +1747 | +329 |
| session | both | calm | 1024 | +322 | -4920 | -4900 | -186 | -1293 |
| session | both | er_lo | 1274 | +54 | -1478 | -2804 | +921 | +506 |
| session | both | er_hi | 694 | +116 | -667 | -2444 | +640 | -1297 |
| session | both | against_or_flat | 701 | +9 | -1880 | -2618 | +1675 | -570 |
| session | both | with_trend | 1267 | +161 | -265 | -2631 | -113 | -221 |

### Flag threshold x N plateau (flag = atr_rel >= thr at the blocked signal)
| thr | N | side | blocked | d L6M | d HOLD | d PRE | d X' |
|---|---|---|---|---|---|---|---|
| 1.00 | 10 | same | 117 | +887 | +825 | +296 | +61 |
| 1.00 | 10 | both | 189 | +1030 | +694 | +496 | +427 |
| 1.00 | 15 | same | 170 | +1470 | +1016 | +450 | -8 |
| 1.00 | 15 | both | 312 | +1323 | +464 | +607 | +708 |
| 1.00 | 20 | same | 227 | +1671 | +940 | +533 | +120 |
| 1.00 | 20 | both | 421 | +1660 | +398 | +549 | +51 |
| 1.00 | 30 | same | 346 | +2538 | +1003 | +688 | -4 |
| 1.00 | 30 | both | 631 | +2633 | +832 | +384 | -202 |
| 1.00 | 45 | same | 451 | +2364 | +848 | +330 | -144 |
| 1.00 | 45 | both | 830 | +2572 | +49 | +178 | -159 |
| 1.00 | 60 | same | 524 | +2303 | +312 | +280 | -174 |
| 1.00 | 60 | both | 970 | +3267 | -135 | +543 | -117 |
| 1.00 | 90 | same | 645 | +2183 | +306 | +616 | -7 |
| 1.00 | 90 | both | 1170 | +3049 | -566 | +971 | -71 |
| 1.15 | 10 | same | 106 | +466 | +615 | +333 | +61 |
| 1.15 | 10 | both | 154 | +591 | +672 | +398 | +162 |
| 1.15 | 15 | same | 156 | +981 | +738 | +476 | -8 |
| 1.15 | 15 | both | 262 | +1158 | +546 | +668 | +190 |
| 1.15 | 20 | same | 210 | +1048 | +641 | +558 | +120 |
| 1.15 | 20 | both | 356 | +1485 | +492 | +662 | -93 |
| 1.15 | 30 | same | 319 | +1822 | +632 | +691 | -4 |
| 1.15 | 30 | both | 541 | +2043 | +693 | +783 | -460 |
| 1.15 | 45 | same | 417 | +1333 | +411 | +333 | -144 |
| 1.15 | 45 | both | 719 | +1632 | -15 | +936 | -362 |
| 1.15 | 60 | same | 479 | +628 | -424 | +333 | -174 |
| 1.15 | 60 | both | 840 | +1389 | -772 | +1350 | -266 |
| 1.15 | 90 | same | 589 | +895 | -158 | +680 | +48 |
| 1.15 | 90 | both | 1024 | +1703 | -618 | +1730 | -128 |
| 1.30 | 10 | same | 104 | +424 | +594 | +333 | +61 |
| 1.30 | 10 | both | 136 | +481 | +663 | +377 | +200 |
| 1.30 | 15 | same | 151 | +903 | +699 | +424 | -8 |
| 1.30 | 15 | both | 219 | +947 | +763 | +626 | +123 |
| 1.30 | 20 | same | 204 | +1155 | +787 | +558 | +120 |
| 1.30 | 20 | both | 302 | +1323 | +895 | +559 | +194 |
| 1.30 | 30 | same | 299 | +1990 | +995 | +592 | -4 |
| 1.30 | 30 | both | 458 | +2087 | +1249 | +569 | -9 |
| 1.30 | 45 | same | 385 | +1800 | +711 | +281 | -164 |
| 1.30 | 45 | both | 611 | +1608 | +441 | +630 | +69 |
| 1.30 | 60 | same | 435 | +1206 | +138 | +302 | -166 |
| 1.30 | 60 | both | 720 | +1235 | -117 | +964 | +356 |
| 1.30 | 90 | same | 529 | +1542 | +531 | +524 | +15 |
| 1.30 | 90 | both | 881 | +1674 | +150 | +1487 | +444 |
| 1.50 | 10 | same | 93 | +707 | +828 | +293 | +61 |
| 1.50 | 10 | both | 117 | +764 | +897 | +243 | +129 |
| 1.50 | 15 | same | 134 | +1028 | +946 | +363 | -8 |
| 1.50 | 15 | both | 181 | +948 | +900 | +445 | -61 |
| 1.50 | 20 | same | 182 | +1235 | +944 | +441 | +120 |
| 1.50 | 20 | both | 255 | +1185 | +895 | +378 | -10 |
| 1.50 | 30 | same | 265 | +1997 | +1350 | +446 | -4 |
| 1.50 | 30 | both | 392 | +1826 | +1390 | +399 | -166 |
| 1.50 | 45 | same | 338 | +2038 | +1373 | +180 | -164 |
| 1.50 | 45 | both | 518 | +1516 | +838 | +188 | +21 |
| 1.50 | 60 | same | 382 | +1733 | +861 | +194 | -166 |
| 1.50 | 60 | both | 606 | +1113 | +185 | +600 | +133 |
| 1.50 | 90 | same | 466 | +2076 | +1129 | +282 | +15 |
| 1.50 | 90 | both | 749 | +1705 | +914 | +543 | +186 |
| 1.70 | 10 | same | 78 | +88 | +576 | +188 | +61 |
| 1.70 | 10 | both | 96 | +88 | +579 | +153 | +88 |
| 1.70 | 15 | same | 112 | +514 | +748 | +217 | -8 |
| 1.70 | 15 | both | 148 | +376 | +681 | +291 | -75 |
| 1.70 | 20 | same | 149 | +729 | +679 | +224 | +120 |
| 1.70 | 20 | both | 202 | +621 | +726 | +266 | -101 |
| 1.70 | 30 | same | 220 | +1564 | +1212 | +168 | -4 |
| 1.70 | 30 | both | 315 | +1318 | +1160 | +296 | -248 |
| 1.70 | 45 | same | 283 | +1605 | +1076 | -133 | -136 |
| 1.70 | 45 | both | 419 | +1497 | +780 | -124 | -34 |
| 1.70 | 60 | same | 321 | +1268 | +594 | -93 | -139 |
| 1.70 | 60 | both | 500 | +1125 | +35 | +192 | +78 |
| 1.70 | 90 | same | 391 | +1360 | +705 | +79 | +50 |
| 1.70 | 90 | both | 624 | +1406 | +475 | +165 | +240 |
| 2.00 | 10 | same | 67 | +268 | +549 | +133 | +61 |
| 2.00 | 10 | both | 77 | +268 | +549 | +133 | +44 |
| 2.00 | 15 | same | 93 | +408 | +509 | +181 | -8 |
| 2.00 | 15 | both | 115 | +270 | +440 | +244 | -64 |
| 2.00 | 20 | same | 119 | +590 | +609 | +19 | +52 |
| 2.00 | 20 | both | 155 | +483 | +654 | +60 | -50 |
| 2.00 | 30 | same | 176 | +916 | +879 | -95 | -18 |
| 2.00 | 30 | both | 238 | +670 | +853 | -14 | -191 |
| 2.00 | 45 | same | 225 | +882 | +705 | -208 | -150 |
| 2.00 | 45 | both | 317 | +756 | +652 | -245 | -37 |
| 2.00 | 60 | same | 254 | +843 | +562 | -136 | -229 |
| 2.00 | 60 | both | 379 | +687 | +439 | +70 | +75 |
| 2.00 | 90 | same | 306 | +778 | +638 | +23 | -40 |
| 2.00 | 90 | both | 472 | +636 | +579 | +15 | +197 |

### C2 first-order: Asia lots scaled to A/7 of the live lots on a cell (stack level, d vs LPB_BASE)
| variant | cut L6M % | d L6M | cut HOLD % | d HOLD | cut PRE % | d PRE | cut X' % | d X' |
|---|---|---|---|---|---|---|---|---|
| Asia x3/7 on all asia | -11.6 | -3846 | -9.3 | -4294 | 9.0 | -1817 | 29.4 | +504 |
| Asia x3/7 on asia hot | -3.1 | -223 | -6.3 | -679 | -14.7 | -698 | 24.6 | +956 |
| Asia x3/7 on asia calm | -8.5 | -3863 | -6.3 | -3312 | 14.9 | -1060 | 4.8 | -90 |
| Asia x3/7 on asia cold | 12.6 | -3231 | -15.3 | -4015 | 7.3 | -756 | 29.5 | -275 |
| Asia x3/7 on asia warm | -24.2 | +278 | -21.7 | +199 | 1.7 | -813 | -0.1 | +1057 |
| Asia x3/7 on asia with-trend | -20.2 | -2246 | -17.7 | -3172 | 26.5 | -734 | -3.7 | -183 |
| Asia x3/7 on asia not-with-trend | 9.4 | -1029 | 11.3 | -872 | -18.9 | -955 | 34.1 | +1048 |
| Asia x3/7 on asia first | -0.6 | -1917 | 1.5 | -1002 | -39.5 | -1604 | 37.5 | +1050 |
| Asia x3/7 on asia later | -6.2 | -3334 | -4.0 | -3064 | 28.6 | -738 | -8.3 | -244 |
| Asia x4/7 on all asia | -7.0 | -2428 | -4.8 | -2925 | 13.7 | -973 | 26.4 | +597 |
| Asia x4/7 on asia hot | -3.1 | +130 | -5.2 | -277 | -5.3 | -390 | 20.2 | +812 |
| Asia x4/7 on asia calm | -3.9 | -2828 | -1.8 | -2439 | 16.6 | -530 | 6.3 | +71 |
| Asia x4/7 on asia cold | 11.6 | -2228 | -1.8 | -2992 | 11.7 | -659 | 26.3 | -58 |
| Asia x4/7 on asia warm | -18.6 | +556 | -16.1 | +465 | 1.9 | -502 | 0.1 | +878 |
| Asia x4/7 on asia with-trend | -11.9 | -1407 | -9.6 | -2179 | 23.0 | -245 | -2.5 | -107 |
| Asia x4/7 on asia not-with-trend | 5.8 | -1353 | 7.7 | -525 | -8.2 | -947 | 29.9 | +988 |
| Asia x4/7 on asia first | -0.2 | -1547 | 1.9 | -744 | -28.3 | -1100 | 31.9 | +926 |
| Asia x4/7 on asia later | -2.0 | -1974 | 0.1 | -1963 | 27.3 | -301 | -5.5 | -102 |
| Asia x5/7 on all asia | -2.8 | -1668 | -0.6 | -1930 | 7.4 | -678 | 14.0 | +235 |
| Asia x5/7 on asia hot | -1.6 | -12 | -3.2 | -269 | -6.8 | -449 | 13.0 | +498 |
| Asia x5/7 on asia calm | -1.2 | -1810 | 0.9 | -1539 | 12.7 | -395 | 0.9 | +238 |
| Asia x5/7 on asia cold | 6.4 | -1597 | 8.3 | -1914 | 6.1 | -199 | 13.7 | -148 |
| Asia x5/7 on asia warm | -9.1 | +310 | -6.9 | +224 | 1.3 | -347 | 0.3 | +522 |
| Asia x5/7 on asia with-trend | -6.0 | -992 | -3.8 | -1453 | 14.8 | -256 | -2.0 | -76 |
| Asia x5/7 on asia not-with-trend | 3.7 | -459 | 5.7 | -351 | -7.5 | -357 | 16.9 | +505 |
| Asia x5/7 on asia first | 1.3 | -924 | 3.4 | -452 | -18.7 | -671 | 18.2 | +513 |
| Asia x5/7 on asia later | -0.2 | -1494 | 1.8 | -1882 | 16.7 | -277 | -4.2 | -127 |
| Asia x6/7 on all asia | 0.6 | -693 | 2.6 | -964 | 11.0 | -295 | 13.1 | +362 |
| Asia x6/7 on asia hot | -1.6 | +93 | -2.1 | -197 | 1.5 | -123 | 7.1 | +314 |
| Asia x6/7 on asia calm | 2.1 | -979 | 4.1 | -891 | 8.6 | -136 | 6.0 | +153 |
| Asia x6/7 on asia cold | 5.2 | -631 | 7.1 | -1073 | 10.3 | -66 | 13.3 | +90 |
| Asia x6/7 on asia warm | -4.6 | +246 | -2.5 | +243 | 0.7 | -155 | -0.2 | +356 |
| Asia x6/7 on asia with-trend | -1.1 | -398 | 1.0 | -700 | 11.8 | +11 | 0.5 | -31 |
| Asia x6/7 on asia not-with-trend | 2.1 | -161 | 3.6 | -173 | -0.7 | -401 | 12.6 | +482 |
| Asia x6/7 on asia first | 3.3 | -623 | -0.5 | -292 | -9.7 | -429 | 14.4 | +414 |
| Asia x6/7 on asia later | 1.0 | -480 | 3.0 | -588 | 15.2 | -24 | -1.3 | +24 |
| Asia x8/7 on all asia | -4.6 | +693 | -7.4 | +964 | -11.0 | +295 | -13.1 | -362 |
| Asia x8/7 on asia hot | 1.6 | -93 | 2.1 | +197 | -1.5 | +123 | -7.1 | -314 |
| Asia x8/7 on asia calm | -6.2 | +979 | -9.5 | +891 | -9.6 | +136 | -6.0 | -153 |
| Asia x8/7 on asia cold | -5.2 | +631 | -7.4 | +1073 | -10.4 | +66 | -13.3 | -90 |
| Asia x8/7 on asia warm | 0.6 | -246 | 0.0 | -243 | -0.7 | +155 | 0.2 | -356 |
| Asia x8/7 on asia with-trend | -2.5 | +398 | -3.8 | +700 | -11.8 | -11 | -0.5 | +31 |
| Asia x8/7 on asia not-with-trend | -2.1 | +161 | -3.6 | +173 | 0.7 | +401 | -12.6 | -482 |
| Asia x8/7 on asia first | -3.6 | +623 | -1.5 | +292 | 8.9 | +429 | -14.4 | -414 |
| Asia x8/7 on asia later | -1.0 | +480 | -7.9 | +588 | -20.7 | +24 | 1.3 | -24 |
| Asia x9/7 on all asia | -4.5 | +1668 | -17.1 | +1930 | -8.5 | +678 | -16.8 | -235 |
| Asia x9/7 on asia hot | 1.6 | +12 | 3.2 | +269 | 6.8 | +449 | -13.0 | -498 |
| Asia x9/7 on asia calm | -6.1 | +1810 | -20.3 | +1539 | -14.7 | +395 | -3.6 | -238 |
| Asia x9/7 on asia cold | -6.4 | +1597 | -17.1 | +1914 | -7.2 | +199 | -16.5 | +148 |
| Asia x9/7 on asia warm | 1.8 | -310 | 0.0 | -224 | -1.3 | +347 | -0.3 | -522 |
| Asia x9/7 on asia with-trend | -0.8 | +992 | -9.2 | +1453 | -15.4 | +256 | 1.0 | +76 |
| Asia x9/7 on asia not-with-trend | -3.7 | +459 | -7.9 | +351 | 7.5 | +357 | -17.6 | -505 |
| Asia x9/7 on asia first | -4.8 | +924 | -3.4 | +452 | 14.0 | +671 | -23.1 | -513 |
| Asia x9/7 on asia later | 0.2 | +1494 | -13.7 | +1882 | -26.6 | +277 | 4.2 | +127 |
