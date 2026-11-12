# DS3_WORKS - T-WORKS expand-what-works (aggregate page; built by W-J; 2026-11-12T15:00:07Z; Shadow only, no PASS claims)

Sections A, B, C are the workers' own pages (DS3_WORKS_A/B/C.md) merged below. Section D is W-J: the reference rows (JN04RM vs LPB_BASE), the JN05 composition and the REFIT 2026-11-22 preview. Every number is exact-engine, live panel base (P7 day cap 8,400 + table 7,4,0,4,0,0 + P7 cut 40/5x/w5/p3), reference LPB_BASE, ROLLFIX1.

## 00. Acceptability first: acceptance table (JN05W is judged on this before profit)

| set | acceptance result (W-C acceptance_p7: PASS = at most 2 fails of 20 sessions) | scorecard file (W-Q) |
|--|--|--|
| LPB_BASE | ACCEPTANCE P7 LPB_BASE  2026-11-12 13:03Z   (months 43: 202304..202610; reference LPB_BASE months 43) | /mnt/l2/l2vast/_th_works/q/sc/sc_LPB_BASE.txt |
| JN04RM | ACCEPTANCE P7 JN04RM  2026-11-11 19:55Z   (months 43: 202304..202610; reference LPB_BASE months 43) | /mnt/l2/l2vast/_th_works/q/sc/sc_JN04RM.txt |
| WA_C1 | (not run) | /mnt/l2/l2vast/_th_works/q/sc/sc_WA_C1.txt |
| WG_E1 | ACCEPTANCE P7 WG_E1  2026-11-12 13:02Z   (months 43: 202304..202610; reference LPB_BASE months 43) | /mnt/l2/l2vast/_th_works/q/sc/sc_WG_E1.txt |
| JN05W_E1 | ACCEPTANCE P7 JN05W_E1  2026-11-12 07:59Z   (months 43: 202304..202610; reference LPB_BASE months 43) | /mnt/l2/l2vast/_th_works/q/sc/sc_JN05W_E1.txt |
| JN05W_E1A | ACCEPTANCE P7 JN05W_E1A  2026-11-12 13:51Z   (months 43: 202304..202610; reference LPB_BASE months 43) | /mnt/l2/l2vast/_th_works/q/sc/sc_JN05W_E1A.txt |

## 000. JN05W scorecard (plain words, W-Q behavior_scorecard.py)

JN05W_E1 L6M (stack, per week): full stops 21.5/wk $-33850; give-backs 8.6/wk (8.5 round-trips) realised $-8975, forgone vs target $23652; same-side losing runs max 14, p95 6, $-31548 lost on 3rd-and-later; no-new-evidence re-entries 34.9/wk $-608; recoveries cut 16.2/wk $42198, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $33908/wk, losers avoided $34100/wk, net -2313 $/wk; pnl $17471/wk.
JN05W_E1 HOLD (stack, per week): full stops 20.1/wk $-32026; give-backs 7.4/wk (7.1 round-trips) realised $-7673, forgone vs target $20244; same-side losing runs max 14, p95 6, $-28717 lost on 3rd-and-later; no-new-evidence re-entries 27.7/wk $443; recoveries cut 13.8/wk $34707, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $30570/wk, losers avoided $30216/wk, net -3721 $/wk; pnl $11630/wk.
JN05W_E1 PRE (stack, per week): full stops 15.6/wk $-25475; give-backs 4.8/wk (4.4 round-trips) realised $-4562, forgone vs target $12239; same-side losing runs max 10, p95 4, $-13386 lost on 3rd-and-later; no-new-evidence re-entries 12.3/wk $805; recoveries cut 7.7/wk $17042, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $21366/wk, losers avoided $19629/wk, net -3867 $/wk; pnl $8015/wk.
JN05W_E1 X' (stack, per week): full stops 17.3/wk $-28555; give-backs 3.2/wk (2.8 round-trips) realised $-3442, forgone vs target $9078; same-side losing runs max 6, p95 3, $-7264 lost on 3rd-and-later; no-new-evidence re-entries 2.2/wk $253; recoveries cut 2.0/wk $4369, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $14878/wk, losers avoided $13595/wk, net +1336 $/wk; pnl $2678/wk.


## 0. Behavioural scorecard (W-Q behavior_scorecard.py: LPB_BASE, JN04RM, JN05W per book and stack and window, plain words; JN05 is judged by acceptability first)

## Behavioural scorecard (reference rows, per week, mid-path based; stack = all books)
LPB_BASE L6M (stack, per week): full stops 24.5/wk $-40052; give-backs 9.1/wk (9.0 round-trips) realised $-14009, forgone vs target $35376; same-side losing runs max 12, p95 6, $-51344 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-363; recoveries cut 13.7/wk $46863, clipped fills 0.0/wk $0; pnl $19784/wk.
LPB_BASE HOLD (stack, per week): full stops 23.0/wk $-37923; give-backs 8.0/wk (7.8 round-trips) realised $-12167, forgone vs target $30716; same-side losing runs max 12, p95 6, $-43521 lost on 3rd-and-later; no-new-evidence re-entries 30.0/wk $732; recoveries cut 12.2/wk $41657, clipped fills 0.0/wk $0; pnl $15351/wk.
LPB_BASE PRE (stack, per week): full stops 16.9/wk $-28859; give-backs 5.2/wk (4.8 round-trips) realised $-7549, forgone vs target $19365; same-side losing runs max 11, p95 4, $-22384 lost on 3rd-and-later; no-new-evidence re-entries 12.7/wk $-160; recoveries cut 6.7/wk $22256, clipped fills 0.0/wk $0; pnl $11882/wk.
LPB_BASE X' (stack, per week): full stops 17.5/wk $-28195; give-backs 3.6/wk (3.0 round-trips) realised $-4902, forgone vs target $12802; same-side losing runs max 7, p95 4, $-12302 lost on 3rd-and-later; no-new-evidence re-entries 2.7/wk $569; recoveries cut 2.5/wk $9968, clipped fills 0.0/wk $0; pnl $1342/wk.
JN04RM L6M (stack, per week): full stops 25.4/wk $-38130; give-backs 9.9/wk (9.8 round-trips) realised $-11306, forgone vs target $28091; same-side losing runs max 13, p95 7, $-42885 lost on 3rd-and-later; no-new-evidence re-entries 43.3/wk $1885; recoveries cut 15.2/wk $39718, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4296/wk, losers avoided $4285/wk, net -254 $/wk; pnl $19530/wk.
JN04RM HOLD (stack, per week): full stops 23.6/wk $-35520; give-backs 8.6/wk (8.4 round-trips) realised $-9743, forgone vs target $24378; same-side losing runs max 13, p95 6, $-37009 lost on 3rd-and-later; no-new-evidence re-entries 34.2/wk $1140; recoveries cut 13.1/wk $34017, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $5311/wk, losers avoided $4661/wk, net -2854 $/wk; pnl $12497/wk.
JN04RM PRE (stack, per week): full stops 16.8/wk $-26445; give-backs 5.4/wk (5.0 round-trips) realised $-5634, forgone vs target $14565; same-side losing runs max 11, p95 5, $-17863 lost on 3rd-and-later; no-new-evidence re-entries 14.4/wk $-45; recoveries cut 7.2/wk $17046, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4797/wk, losers avoided $4304/wk, net -2474 $/wk; pnl $9409/wk.
JN04RM X' (stack, per week): full stops 17.7/wk $-27189; give-backs 3.5/wk (3.0 round-trips) realised $-3615, forgone vs target $9772; same-side losing runs max 7, p95 4, $-9998 lost on 3rd-and-later; no-new-evidence re-entries 3.1/wk $562; recoveries cut 2.5/wk $6540, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3512/wk, losers avoided $3147/wk, net +205 $/wk; pnl $1547/wk.
LIVE LIVEWK (stack, per week): full stops 3.0/wk $-4385; give-backs 14.0/wk (12.0 round-trips) realised $-18855, forgone vs target $56473; same-side losing runs max 5, p95 4, $-50669 lost on 3rd-and-later; no-new-evidence re-entries 36.0/wk $34824; recoveries cut 22.0/wk $105991, clipped fills 0.0/wk $0; pnl $102830/wk.


## D0. Reference rows (exact, rule mode, 43 months)

| cell | window | mean $/wk all-weeks | LPB_BASE all-weeks | d mean all-weeks | mean (carry week dropped) | mean_ref (carry dropped) | maxDD | maxDD_ref | cut % | d mean | WF beat % | label |
|--|--|--|--|--|--|--|--|--|--|--|--|--|
| JN04RM | L1M | 3824 | 341 | +3483 | 10653 | 17539 | 27056 | 51253 | +47.2 | -6886 | 90 |  |
| JN04RM | L3M | 12585 | 11957 | +628 | 15022 | 17224 | 41699 | 77224 | +46.0 | -2202 | 90 |  |
| JN04RM | L6M | 18457 | 18697 | -240 | 19862 | 21495 | 41699 | 77224 | +46.0 | -1633 | 90 | OK-PRIOR (allow 25.0%, WF 90%) |
| JN04RM | HOLD | 12384 | 15236 | -2852 | 12954 | 16540 | 72757 | 78842 | +7.7 | -3586 | 90 |  |
| JN04RM | PRE | 9247 | 11685 | -2438 | 8714 | 10548 | 66714 | 99479 | +32.9 | -1834 | 90 |  |
| JN04RM | X' | 1537 | 1334 | +203 | 2195 | 2553 | 64077 | 122553 | +47.7 | -357 | 90 |  |

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

Registered dial candidates (W-A relay, 2026-11-11): WA_C1 = JN04RM + K7 off while 15-day Calmar < 0.5 + M7 off while drawdown from 7-day peak >= $6,296 + P7 halved while 7-day P&L < -$3,626 (exact 43 months; RECENT-ONLY; cut vs JN04RM L6M +29.0, HOLD +39.8, PRE +14.4, X' +15.7). WA_C2 = WA_C1 plus the stack gate. Scorecards: /mnt/l2/l2vast/_th_works/q/sc/sc_WA_C1.txt and sc_WA_C2.txt; alone they remove only about 18-30% of full stops and give-backs, so they enter JN05 only together with the exit and entry rules of W-C (governor, new-evidence re-entry), W-N (near-zone) and W-X (early cut). Neighbour-plateau sets WA_PL_* are queued by W-A on L6M and will be read before composing. Composition waits for exact winners from W-C, W-N, W-X and W-Q.


## A. Generalise the dials (A)

Source DS3_WORKS_A.md (mtime 2026-11-12T14:25:56Z UTC), included verbatim, read only:

# DS3_WORKS_A - T-WORKS part A: generalised risk dials (W-A)
Refreshed 2026-11-12 14:25Z. Shadow only, no PASS claims, label PRE-PROOF (post-hoc). Prereg: autopilot/WORKS_A_PREREG.md (sha in DECISIONS.md, plus an addendum for the composites and cap sets). Code: outputs/code/th_works_a. Data: /mnt/l2/l2vast/_th_works_a.

## 0. Status and method
Exact sets with the L6M window complete: 32; with HOLD complete: 1. First-order screens (all on the exact LPB_BASE trade list, 20,808 trades, and again on the exact JN04RM trade list, 21,783 trades; the dial state is always the LPB_BASE shadow base-lot P&L, which is what the live state sees): A1 17756 cells, A2 1176 cells, A3 3960 cells per base. Exact runs go one set per job through the harness code/th_works_a/wa_run.py (WorksMixin generalises the JN04 rule-mode layers; it reproduces LPB_EMPTY and JN04RM trade by trade on 202610 and 202608, see DECISIONS.md). Every exact set below is JN04RM plus the named change, so each row answers whether the dial adds to the live-form JN04 stack. A cut is the stack maxDD cut in per cent; d mean is the weekly mean difference in dollars with the carrying week dropped.

WA jobs running at refresh (process count incl. forked child): none. Since 20:3xZ (lead priority change for the P7 FIX) the queue is trimmed to WA_C1 (finalist, extending to PRE / X-prime / GAP for the bi-weekly WF); WA_A1_03, WA_A3_ALL6T and WA_A3_L5T were stopped and the rest of the queue is paused (queue_full_paused.txt); new sets start only at MemAvail >= 62 GB.

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
| WA_A3_L6P7 | London same-side cap 6, applied to P7 only | +36.8 / -1393 | -17.0 / -167 / -18.0 | not yet | not yet |
| WA_A3_L6REG13 | London same-side cap 6 only when atr_rel >= 1.3 | +33.6 / -1639 | -22.9 / -341 / -25.3 | not yet | not yet |
| WA_A3_L8T | London same-side cap 8 truncate | +38.4 / -1596 | -14.1 / +45 / -13.8 | not yet | not yet |
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
| JN04RM | L6M | 25.4 (-38130) | 9.9 (-11306) | +7 / +13 (-42885) | +43.3 (+1885) | -254 | no (a x1.03, b x1.09) |
| JN04RM | HOLD | 23.6 (-35520) | 8.6 (-9743) | +6 / +13 (-37009) | +34.2 (+1140) | -2854 | no (a x1.03, b x1.08) |
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
| WA_A3_L6P7 | L6M | 25.5 (-38533) | 9.8 (-11405) | +7 / +13 (-43164) | +43.4 (+2215) | -88 | no (a x1.04, b x1.08) |
| WA_A3_L6REG13 | L6M | 25.5 (-38533) | 9.8 (-11435) | +7 / +13 (-43507) | +43.5 (+2183) | -406 | no (a x1.04, b x1.08) |
| WA_A3_L8T | L6M | 25.5 (-38479) | 9.8 (-11428) | +7 / +13 (-43218) | +43.3 (+2204) | -362 | no (a x1.04, b x1.08) |
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




## B. Regime-conditional exits (B)

Source DS3_WORKS_B.md (mtime 2026-11-12T08:29:01Z UTC), included verbatim, read only:

# DS3_WORKS_B - T-WORKS part B (W-B) FINAL, 2026-11-12T08:28Z (date -u). Pages 3, 2, 1 are kept below. Shadow only, no PASS claims, PRE-PROOF.

## A. Scorecard first (standing principle; W-Q tool; L6M stack per week; LPB_BASE = live panel base, JN04RM = JN04 reference)
LPB_BASE L6M: full stops 24.5/wk (-$40.1k), give-backs 9.1/wk, same-side losing runs max 12 / p95 6 ($-51.3k on the 3rd and later), no-new-evidence re-entries 37.3/wk. Finalists of part B, same measures: context cut WB_X_FR_F3 24.9/wk, 9.4/wk, 12 / 7, 42.9/wk; context cut F4 25.7/wk, 9.4/wk, 13 / 7, 44.2/wk; Asia sweep skip WB_D5_SW 24.6/wk, 9.1/wk, 12 / 6, 37.8/wk; cut-only-after-a-trend-day WB_B2_FPRI 32.4/wk (-$75.4k), 8.8/wk, 12 / 6, 35.7/wk; never cut WB_C_NONE 36.4/wk (-$94.8k), 8.7/wk, 11 / 6, 34.3/wk. On JN04RM: JN04RM 25.4/wk, 9.9/wk, 13 / 7, 43.3/wk; JN04RM_WBF3 25.7/wk, 10.3/wk, 13 / 7, 47.9/wk. PRE and the frozen week behave the same (F3 PRE full stops 17.4/wk vs LPB 16.9). NO part-B rule halves full stops, give-backs or same-side runs: the standing principle says none of them is a result. What they do is change the cost of a failure: F3 on LPB L6M skips $8.1k/wk of winners and avoids $6.6k/wk of losers (net +$335/wk), D5_SW skips $8.7k and avoids $9.2k (net +$3.2k/wk), F3 on JN04RM nets -$2.3k/wk. The loss-cut line cannot fix defects 1-3; the entry side (W-A/W-C governors) has to.

## B. Plain sentences, final
1. Flag (B1): nothing from LOT/REG/ER(20)/stack Calmar/family H separates last week (trend) from choppy weeks well. LOT was cold on every P7 signal of the live trend week (10-day Calmar below 1 all four days even with +$21k to +$31k shadow days, because the ten days before were losses), REG hot (atr_rel >= 1.3) was 60 percent of live P7 signals vs 46 percent median (percentile 0.76), ER(20) at the signal sat at the median (0.38 percentile), family H F_ER was the sharpest (0.94 percentile). REG and ER(20) flip every 2 signals; LOT, stack Calmar, F_ER, F_PRIOR persist (13-24 signals; F_PRIOR 91 percent same state next signal). Per-trade regret of the cut (first-order, week-block bootstrap): REG hot >= 1.5 / 1.8 and ER20 >= 0.30 with LOT warm are the flags where cutting costs more, F_ER goes the other way.
2. Conditional cut by a flag (B2): not a result. Exact: never cutting (NONE) cut +19.1/+10.4/+27.4 L6M/PRE/X' and -19.1 HOLD; cut off when atr_rel >= 1.5 worse (-11.1 L6M); cut off with stack Calmar5 >= 1: 0.0/-1.3/+33.8 and HOLD +2.1, means +2,159/+44/+798/-845, WF 0.0 / +596; cut on only after a trend day (F_PRIOR): +30.7/+9.9/+7.6/-6.0 (L6M/HOLD/PRE/X'), means +4,119/+1,103/+364/-682, WF +17.6 percent / +1,389, but full stops 32.4/wk and the family max-stat of 86 day-level mixtures says the best mixture is no better than random (p 0.69). Frozen week: 24 P7 cuts = 17 saves (-$29.9k) + 7 recoveries (+$69.1k); the flags keep 4-9 saves in every state that holds the recoveries.
3. Context cut (P7 FIX B) is the one real, robust finding of part B: choose the cut by entry context fixed at entry; fresh trade -> V2 (45/5x/w5/p10), re-entry/chasing -> fast. WB_X_FR_F3 (fast 30/10x/w5/p2): L6M +30.6 / +2,129, HOLD +1.8 / -866, PRE +28.4 / +335, X' +24.3 / +191, WF 0.0 / -461, beats 43 percent; reverse control -20.1 / -1,939 (L6M); by lots (>=5 lots fast, <5 V2, WB_X_LOTS): VOID - its L6M numbers equal the uniform-V2 set to the dollar (+15.4 / +1,483), i.e. the hook read the lot count as below 5 for every trade (defect in my lots lookup, not fixed); the by-lots question is open; by side (short fast) +22.0 / +3,216, HOLD -21.5. On the JN04RM base F3 is +9.0 / +1.0 / +2.3 / +45.9 (L6M/HOLD/PRE/X') with means -974 / -931 / -275 / +836: a drawdown line of little size there. 202510 is not in the JN04RM runs (WF vs JN04RM not computed). Scorecard fails (section A). Rule 2a: all four windows pass the DD floors on LPB; on JN04RM means are negative in the three recent windows.
4. Profit side (B3): conditional protection (`profit P7 * pct>=0.5 pulled_against_mult>=10 take win=5 persist=5`, ON only when stack Calmar10 < 1; WB_B3_P3) +23.2/+24.8/-9.9/+13.2 (L6M/HOLD/PRE/X') at means -710/-598/-1,370/-51, WF -14.6 percent: fails PRE and WF, clips 11.9 fills/wk. Other conditional lines (P2, P4, K7/M7/U7) screens only, not promoted. 28 of 28 live-target clipping problem: P7 lines clip 8-10 of 28 live targets in either ER20 state.
5. Near-target (B4): the live stand-in (K7/P7/M7 take within 3 pts and 5 s stall) is worse than nothing in L6M (-9.1 / -1,253). Scored replacement: retarget 8 ticks only when atr_rel < 1.3, 60 otherwise (WB_B4_R8C): +26.1/+8.1/-10.6/+5.2 (L6M/HOLD/PRE/X') means +51/+460/+227/-50, WF -10.6 (12 percent beats): RECENTS-ONLY (rule 2a), PRE fails. Brackets (B5), P7, L6M only: stop 45 / target 60 +5.5 / +1,556; target 45 when atr_rel < 1.5 +42.9 / -2,026; target 90 when atr_rel >= 1.5 -6.0 / -590.
6. D5 (addendum): at the signal second no book-state feature (absorption/ice/delta/pulled_against push) removes more worst-20-week losers than best-20-week winners; the one selective cell, Asia sweep_against max(60 s) >= 16 ticks skip (226 trades, WB_D5_SW): +2.8/-0.1/+20.1/+6.2 (L6M/HOLD/PRE/X') means +1,758/+1,120/+256/+2, WF 0.0 / +67; on JN04RM +3.1/-1.9/+11.9/+4.7 with means +619/+662/+58/+1. Small, one cell of a 1,034-cell family, no placebo run: candidate only.
7. Deliverables. (1) What is expressible in v1.7 today: only the unconditional parts (P7 cut cell per session, PolicyCut loss lines matched by book/session/regime string, the day-level regime string); a cut chosen per entry context and any per-signal flag is NOT. (2) Field: `regime` (third policy column, DayRegime = daily vol_lo/vol_mid/vol_hi set at 10:30 ET and never reset) can carry only DAY-level flags if the code assigns it at the roll: F_PRIOR (prior-day trend ratio) would fit if DayRegime were set at 18:00 ET to trend_prev / chop_prev (it replaces the vol label unless a second field is added). Per-signal flags (REG, ER(20), LOT, stack, entry context) need a new per-book string `EntryRegime` written at the signal second and matched by the same third column token (`r.Regime == b.EntryRegime`), plus the context counters: P7 session trade counter (n_sess), minutes since last P7 exit, session move / ATR5 at the signal (chasing flag; same definitions as W-C in P7_CONTEXT_DEFS.md), tag values fresh / rechase; the loss-cut rows then read one per tag (fresh: 45/5x/w5/p10, rechase: 30/10x/w5/p2). Worked rows (live week 11-02, Asia, P7 trade list): 1st trade (n_sess 1, no prior exit, session move 1.56 ATR, chasing) = rechase, Target +4,800; 2nd (gap 8 min, 2.80 ATR) = rechase, Target +11,998; 3rd (19 min, 5.51) = rechase, Target +4,805; 4th (1 min, 11.73) = rechase, ThL2Cut -1,407; 5th (30 min, -10.31, against the move) = rechase (n_sess 5), Target +4,795; London 2nd trade (gap 42 min, -0.14 ATR) = fresh, Target +3,601. (3) P7 table: see section C and the exact rows below. (4) JN05 joint with W-J: candidates from part B in priority order: context cut F3 (V2 fresh / 30-10x-p2 rechase), Asia sweep skip D5_SW; both fail the scorecard, so they enter the joint only as cost reducers behind the entry-side governors. (5) REFIT 2026-11-22 preview: F3 and D5_SW would be refit as the cut cell pair and the sweep threshold; the L6M-heavy F4 (+34.8) is the aggressive variant and needs HOLD (-11.7) tolerated.
8. Missing: the 11-09..11 live week (no trade log, no shadow P&L, no state days after 11-05); exact K7/M7 context cuts; WF vs JN04RM (202510 not run); worst-10 session replay on JN04RM.

## C. Exact rows (LPB_BASE reference, 43 months)
| set | months | cut_L1M | dmean_L1M | eq_cut_L1M | cut_L3M | dmean_L3M | eq_cut_L3M | cut_L6M | dmean_L6M | eq_cut_L6M | cut_HOLD | dmean_HOLD | eq_cut_HOLD | cut_PRE | dmean_PRE | eq_cut_PRE | cut_X' | dmean_X' | eq_cut_X' |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| WB_X_FR_F3 | 43 | 10.3 | 853.8 | 20.9 | 30.6 | 1838.6 | 38.8 | 30.6 | 2129.0 | 38.8 | 1.8 | -865.7 | 13.4 | 28.4 | 335.3 | 36.8 | 24.3 | 190.7 | 33.2 |
| WB_X_FR_F4 | 43 | 27.1 | 2824.3 | 43.0 | 34.8 | 2781.6 | 49.0 | 34.8 | 4435.1 | 49.0 | -11.7 | 310.3 | 12.7 | 22.0 | 1207.1 | 39.0 | 36.3 | -189.8 | 50.2 |
| WB_X_SIDE | 43 | 13.7 | 1438.8 | 27.2 | 22.0 | 4239.5 | 34.2 | 22.0 | 3216.4 | 34.2 | -21.5 | 1224.9 | -2.5 | 19.2 | 311.3 | 31.9 | 18.2 | 1533.3 | 31.0 |
| WB_D5_SW | 43 | -8.1 | -418.7 | 1.0 | 2.8 | -62.3 | 11.0 | 2.8 | 1757.5 | 11.0 | -0.1 | 1119.6 | 8.3 | 20.1 | 255.8 | 26.8 | 6.2 | 1.6 | 14.1 |
| WB_B2_FPRI | 43 | 9.4 | 705.4 | 25.8 | 30.7 | 7365.2 | 43.2 | 30.7 | 4119.1 | 43.2 | 9.9 | 1103.2 | 26.2 | 7.6 | 363.7 | 24.3 | -6.0 | -681.5 | 13.1 |
| WB_B4_R8C | 43 | -5.8 | -1049.6 | -5.5 | 26.1 | 789.8 | 26.3 | 26.1 | 51.3 | 26.3 | 8.1 | 460.1 | 8.4 | -10.6 | 227.2 | -10.3 | 5.2 | -50.2 | 5.4 |

JN04RM-reference rows (42 months, 202510 missing; cut vs JN04RM): JN04RM_WBF3 cut L1M -1.6, L3M +9.0, L6M +9.0, HOLD +1.0, PRE +2.3, X' +45.9; dmean -142 / -1,910 / -974 / -931 / -275 / +836. JN04RM_WBSW cut +18.9 / +8.6 / +3.1 / -1.9 / +11.9 / +4.7; dmean +453 / +353 / +619 / +662 / +58 / +1.

## D. Worst-10 P7 sessions replayed entry by entry (L6M, ranked by LPB_BASE P7 session P&L): LPB_BASE vs WB_X_FR_F3 vs WB_D5_SW
### session start 07-27 22:00 UTC, session 0, LPB P7 session P&L -14274
- LPB_BASE: total -14274 over 8 trades: -22:38 4L StateCut -3007; -00:11 4L Target 4800; -01:06 5L Target 5984; -01:23 7L StateCut -5705; -02:14 4L StateCut -3254; +03:54 4L StateCut -3694; +04:43 4L StateCut -3394; -05:40 7L StateCut -6005
- WB_X_FR_F3: total -11315 over 9 trades: -22:38 4L StateCut -2722; -00:11 4L Target 4800; -01:06 5L Target 5984; -01:23 7L StateCut -5093; -02:14 4L StateCut -2624; -02:27 4L StateCut -2449; +03:54 4L StateCut -2624; +04:43 4L StateCut -2474; -05:40 7L StateCut -4115
- WB_D5_SW: total -10669 over 5 trades: -22:38 4L StateCut -3007; -00:32 4L StateCut -3504; -00:51 4L Target 4800; -01:23 7L StateCut -5705; -02:14 4L StateCut -3254
### session start 05-27 13:30 UTC, session 3, LPB P7 session P&L -13000
- LPB_BASE: total -13000 over 5 trades: -14:11 4L StateCut -3374; -14:33 3L StateCut -2449; -15:00 4L StateCut -3654; -15:20 2L StateCut -1759; -15:39 2L StateCut -1764
- WB_X_FR_F3: total -10525 over 5 trades: -14:11 4L StateCut -3184; -14:33 3L StateCut -1909; -15:00 4L StateCut -2904; -15:20 2L StateCut -1199; -15:39 2L StateCut -1329
- WB_D5_SW: total -13000 over 5 trades: -14:11 4L StateCut -3374; -14:33 3L StateCut -2449; -15:00 4L StateCut -3654; -15:20 2L StateCut -1759; -15:39 2L StateCut -1764
### session start 09-09 22:00 UTC, session 0, LPB P7 session P&L -12681
- LPB_BASE: total -12681 over 3 trades: -23:01 4L StateCut -3274; -01:07 4L StateCut -3349; +05:07 7L StateCut -6059
- WB_X_FR_F3: total -4394 over 3 trades: -23:01 4L StateCut -2924; -01:07 4L StateCut -2669; +04:47 1L Target 1199
- WB_D5_SW: total -12681 over 3 trades: -23:01 4L StateCut -3274; -01:07 4L StateCut -3349; +05:07 7L StateCut -6059
### session start 08-25 22:00 UTC, session 0, LPB P7 session P&L -12662
- LPB_BASE: total -12662 over 4 trades: +22:09 7L StateCut -5810; -00:04 7L Target 6004; -01:09 7L StateCut -5718; +03:03 7L StateCut -7138
- WB_X_FR_F3: total -10334 over 4 trades: +22:09 7L StateCut -7263; -00:04 7L Target 6004; -01:09 7L StateCut -4370; +03:03 7L StateCut -4705
- WB_D5_SW: total -10255 over 4 trades: +22:58 4L StateCut -3404; -00:04 7L Target 6004; -01:09 7L StateCut -5718; +03:03 7L StateCut -7138
### session start 05-05 22:00 UTC, session 0, LPB P7 session P&L -12366
- LPB_BASE: total -12366 over 2 trades: +23:48 7L StateCut -6223; -00:48 7L StateCut -6143
- WB_X_FR_F3: total -11754 over 2 trades: +23:48 7L StateCut -4998; -00:48 7L StateCut -6756
- WB_D5_SW: total -12366 over 2 trades: +23:48 7L StateCut -6223; -00:48 7L StateCut -6143
### session start 09-30 22:00 UTC, session 0, LPB P7 session P&L -12188
- LPB_BASE: total -12188 over 2 trades: -23:08 7L StateCut -6615; +00:01 7L StateCut -5573
- WB_X_FR_F3: total -8498 over 1 trades: -23:08 7L StopJoin -8498
- WB_D5_SW: total -12188 over 2 trades: -23:08 7L StateCut -6615; +00:01 7L StateCut -5573
### session start 05-15 06:00 UTC, session 1, LPB P7 session P&L -11920
- LPB_BASE: total -11920 over 8 trades: -06:07 4L StateCut -3344; -06:21 4L StateCut -3714; +06:56 1L Target 1199; +07:28 2L StateCut -1699; -09:12 1L Target 1199; -09:42 4L StateCut -3294; -10:40 2L StateCut -1464; +11:01 2L BookLock -802
- WB_X_FR_F3: total -10528 over 10 trades: -06:07 4L StateCut -2724; -06:21 4L StateCut -2764; +06:56 1L Target 1199; +07:28 2L StateCut -1289; -09:12 1L Target 1199; -09:42 4L StateCut -2314; -10:05 2L StateCut -1269; -10:40 2L StateCut -1039; +11:01 2L StateCut -1279; +11:52 2L BookLock -247
- WB_D5_SW: total -11920 over 8 trades: -06:07 4L StateCut -3344; -06:21 4L StateCut -3714; +06:56 1L Target 1199; +07:28 2L StateCut -1699; -09:12 1L Target 1199; -09:42 4L StateCut -3294; -10:40 2L StateCut -1464; +11:01 2L BookLock -802
### session start 10-07 22:00 UTC, session 0, LPB P7 session P&L -11851
- LPB_BASE: total -11851 over 2 trades: +22:21 7L StateCut -5873; -00:56 7L StateCut -5978
- WB_X_FR_F3: total -8963 over 2 trades: +22:21 7L StateCut -4665; -00:56 7L StateCut -4298
- WB_D5_SW: total -11851 over 2 trades: +22:21 7L StateCut -5873; -00:56 7L StateCut -5978
### session start 06-17 22:00 UTC, session 0, LPB P7 session P&L -11837
- LPB_BASE: total -11837 over 2 trades: -23:42 7L StateCut -6615; +00:31 7L StateCut -5221
- WB_X_FR_F3: total -12053 over 2 trades: -23:42 7L StateCut -7578; +00:31 7L StateCut -4475
- WB_D5_SW: total -10253 over 2 trades: -23:42 7L StateCut -6615; +00:35 7L StateCut -3638
### session start 06-02 22:00 UTC, session 0, LPB P7 session P&L -11538
- LPB_BASE: total -11538 over 2 trades: +22:12 7L StateCut -5710; -23:35 7L StateCut -5828
- WB_X_FR_F3: total -12343 over 2 trades: +22:12 7L StateCut -7163; -23:35 7L StateCut -5180
- WB_D5_SW: total -11538 over 2 trades: +22:12 7L StateCut -5710; -23:35 7L StateCut -5828


---- PAGE 3 ----
# DS3_WORKS_B - T-WORKS part B (W-B) incl. P7 FIX B and D5. PAGE 3, 2026-11-12T03:48Z (date -u). Pages 2 and 1 are kept below.

STATUS: Shadow only, post-hoc, no PASS claims, PRE-PROOF. Exact, one set per job, 43 months, reference LPB_BASE (live panel base). cut = stack maxDD cut % (negative = deeper), dmean = $/week, eq = equal-mean cut. Preregs WORKS_B_PREREG.md, WORKS_B_P7FIX_PREREG.md; tags P7_CONTEXT_DEFS.md.

## 0. Plain sentences (page 3 = what changed since page 2)
1. The context-dependent P7 cut now has a finalist that holds in all four windows: WB_X_FR_F3, fresh trade (1st/2nd P7 trade of the session, not chasing, 30+ minutes after the last P7 exit) gets V2 (45/5x/w5/p10), re-entry or chasing trade gets the fast line 30/10x/w5/p2. L6M +30.6 percent / +2,129 $/wk, HOLD +1.8 / -866, PRE +28.4 / +335, X' +24.3 / +191 (equal-mean +38.8 / +13.4 / +36.8 / +33.2). It passes the drawdown-first floors (L6M and PRE not worse, HOLD not deeper than -5). Bi-weekly WF vs LPB_BASE: 0.0 percent OOS cut, -461 $/wk, beats LPB in 43 percent of the 74 periods (it is a drawdown rule, its mean is flat to slightly negative outside L6M). The reverse control (fresh fast, re-entry slow) is -20.1 / -1,939 in L6M, so the direction is right. The faster 25/20x/w5/p1 (WB_X_FR_F4) is better in L6M (+34.8 / +4,435) and PRE (+22.0) but HOLD is -11.7 (fails the floor): F3 is the plateau choice. By side (short 40/5x/p3, long V2; WB_X_SIDE): L6M +22.0 / +3,216, HOLD -21.5 / +1,225 (fails), PRE +19.2, X' +18.2; WF +3.7 / +539.
2. Behavioural scorecard (W-Q tool, per week): the finalist FAILS the standing principle. WB_X_FR_F3 L6M: full stops 24.9/wk vs 24.5 (LPB), give-backs 9.4/wk vs 9.1, same-side losing runs max 12 / p95 7 vs 12 / 6, no-new-evidence re-entries 42.9/wk vs 37.3, recoveries cut 16.6/wk vs 13.7; cost view vs LPB_BASE: winners skipped $8.1k/wk, losers avoided $6.6k/wk (net +$335/wk). PRE: full stops 17.4/wk vs 16.9, runs max 12 / p95 5 vs 11 / 4. The context cut changes the size of the loss on a failed trade (smaller on re-entries, larger on fresh ones), not how often the book fails or repeats. It does not turn the frozen week into a loser only because the week's 48 of 53 P7 trades are re-entries/chasers and the fast line is the live-like line there; replay of the 24 live P7 cuts: 22 are re-entry/chasing (16 saves -$27.9k, 6 recoveries +$61.9k if held) and 2 fresh (1 save, 1 recovery). So F3 is acceptable as a drawdown/cost line (rule-2a: all four windows ok on DD) but is NOT a result under the standing principle.
3. D5 book exhaustion (Asia P7 skip when sweep_against, the retreat of the own-side best price in one second, max of the last 60 s >= 16 ticks; 226 trades, WB_D5_SW, 43 months): L6M +2.8 / +1,758, HOLD -0.1 / +1,120, PRE +20.1 / +256, X' +6.2 / +2 (eq +11.0 / +8.3 / +26.8 / +14.1); WF 0.0 / +67, beats 14 percent. Small but positive in all four windows on drawdown and mean; scorecard L6M essentially unchanged (full stops 24.6/wk, runs 12/6, winners skipped $8.7k/wk vs losers avoided $9.2k/wk, net +$3.2k/wk). Selectivity at the first-order screen: it removes -$25.4k from the worst-20 weeks and -$4.9k (losers too) from the best-20 weeks, so it does not skip trend-week winners. The wider D5 family (absorption/ice/delta/pulled_against push features, all sessions, K7/M7) has no selective cell. A one-feature, one-threshold, one-session result: reported as a candidate, family size 1,034 cells, no placebo yet.
4. JN04RM base: the two winners are being run on the JN04RM reference (IJK jbjobs, one set per job): JN04RM_WBF3 (context cut F3) and JN04RM_WBSW (Asia sweep skip); results on page 4 (06:00Z).
5. Everything on page 2 about FPRI, STK5, NONE, near-target (take loses, 8-tick regime retarget RECENTS-ONLY), `regime` / DayRegime (cannot carry a per-signal flag; new per-book EntryRegime field, values fresh / rechase) stands.

## 1. Exact rows (all 43 months)
| set | months | cut_L1M | dmean_L1M | eq_cut_L1M | cut_L3M | dmean_L3M | eq_cut_L3M | cut_L6M | dmean_L6M | eq_cut_L6M | cut_HOLD | dmean_HOLD | eq_cut_HOLD | cut_PRE | dmean_PRE | eq_cut_PRE | cut_X' | dmean_X' | eq_cut_X' |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| WB_C_V2 | 6 | 1.2 | 6120.8 | 8.5 | 15.4 | 2960.5 | 21.6 | 15.4 | 1482.9 | 21.6 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_C0 | 6 | -3.8 | -1202.2 | 4.4 | 21.0 | 2447.9 | 27.2 | 21.0 | 1810.8 | 27.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_F2 | 6 | 2.4 | -465.3 | 2.2 | 34.4 | -257.9 | 34.3 | 34.4 | -32.7 | 34.3 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_F3 | 43 | 10.3 | 853.8 | 20.9 | 30.6 | 1838.6 | 38.8 | 30.6 | 2129.0 | 38.8 | 1.8 | -865.7 | 13.4 | 28.4 | 335.3 | 36.8 | 24.3 | 190.7 | 33.2 |
| WB_X_FR_F4 | 43 | 27.1 | 2824.3 | 43.0 | 34.8 | 2781.6 | 49.0 | 34.8 | 4435.1 | 49.0 | -11.7 | 310.3 | 12.7 | 22.0 | 1207.1 | 39.0 | 36.3 | -189.8 | 50.2 |
| WB_X_FR_F5 | 6 | 21.7 | 1862.3 | 22.5 | 31.5 | 2591.1 | 32.2 | 31.5 | 194.4 | 32.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_REV | 6 | 3.6 | -276.5 | -7.5 | -20.1 | -2604.4 | -34.0 | -20.1 | -1939.2 | -34.0 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_SIDE | 43 | 13.7 | 1438.8 | 27.2 | 22.0 | 4239.5 | 34.2 | 22.0 | 3216.4 | 34.2 | -21.5 | 1224.9 | -2.5 | 19.2 | 311.3 | 31.9 | 18.2 | 1533.3 | 31.0 |
| WB_X_LOTS | 6 | 1.2 | 6120.8 | 8.5 | 15.4 | 2960.5 | 21.6 | 15.4 | 1482.9 | 21.6 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B2_FPRI | 43 | 9.4 | 705.4 | 25.8 | 30.7 | 7365.2 | 43.2 | 30.7 | 4119.1 | 43.2 | 9.9 | 1103.2 | 26.2 | 7.6 | 363.7 | 24.3 | -6.0 | -681.5 | 13.1 |
| WB_B2_STK5 | 43 | 0.0 | -402.6 | 10.4 | 0.0 | 484.0 | 10.4 | 0.0 | 2159.2 | 10.4 | 2.1 | -845.1 | 12.2 | -1.3 | 44.4 | 9.2 | 33.8 | 797.6 | 40.6 |
| WB_B3_P3 | 43 | 21.2 | 2559.7 | 17.5 | 23.2 | 4378.9 | 19.6 | 23.2 | -710.0 | 19.6 | 24.8 | -597.9 | 21.3 | -9.9 | -1369.5 | -15.1 | 13.2 | -51.0 | 9.2 |
| WB_D5_SW | 43 | -8.1 | -418.7 | 1.0 | 2.8 | -62.3 | 11.0 | 2.8 | 1757.5 | 11.0 | -0.1 | 1119.6 | 8.3 | 20.1 | 255.8 | 26.8 | 6.2 | 1.6 | 14.1 |
| WB_B4_R8C | 43 | -5.8 | -1049.6 | -5.5 | 26.1 | 789.8 | 26.3 | 26.1 | 51.3 | 26.3 | 8.1 | 460.1 | 8.4 | -10.6 | 227.2 | -10.3 | 5.2 | -50.2 | 5.4 |

## 2. Worst-10 P7 sessions (L6M), entry by entry: LPB_BASE vs WB_X_FR_F3 vs WB_D5_SW
### session start 07-27 22:00 UTC, session 0, LPB P7 session P&L -14274
- LPB_BASE: total -14274 over 8 trades: -22:38 4L StateCut -3007; -00:11 4L Target 4800; -01:06 5L Target 5984; -01:23 7L StateCut -5705; -02:14 4L StateCut -3254; +03:54 4L StateCut -3694; +04:43 4L StateCut -3394; -05:40 7L StateCut -6005
- WB_X_FR_F3: total -11315 over 9 trades: -22:38 4L StateCut -2722; -00:11 4L Target 4800; -01:06 5L Target 5984; -01:23 7L StateCut -5093; -02:14 4L StateCut -2624; -02:27 4L StateCut -2449; +03:54 4L StateCut -2624; +04:43 4L StateCut -2474; -05:40 7L StateCut -4115
- WB_D5_SW: total -10669 over 5 trades: -22:38 4L StateCut -3007; -00:32 4L StateCut -3504; -00:51 4L Target 4800; -01:23 7L StateCut -5705; -02:14 4L StateCut -3254
### session start 05-27 13:30 UTC, session 3, LPB P7 session P&L -13000
- LPB_BASE: total -13000 over 5 trades: -14:11 4L StateCut -3374; -14:33 3L StateCut -2449; -15:00 4L StateCut -3654; -15:20 2L StateCut -1759; -15:39 2L StateCut -1764
- WB_X_FR_F3: total -10525 over 5 trades: -14:11 4L StateCut -3184; -14:33 3L StateCut -1909; -15:00 4L StateCut -2904; -15:20 2L StateCut -1199; -15:39 2L StateCut -1329
- WB_D5_SW: total -13000 over 5 trades: -14:11 4L StateCut -3374; -14:33 3L StateCut -2449; -15:00 4L StateCut -3654; -15:20 2L StateCut -1759; -15:39 2L StateCut -1764
### session start 09-09 22:00 UTC, session 0, LPB P7 session P&L -12681
- LPB_BASE: total -12681 over 3 trades: -23:01 4L StateCut -3274; -01:07 4L StateCut -3349; +05:07 7L StateCut -6059
- WB_X_FR_F3: total -4394 over 3 trades: -23:01 4L StateCut -2924; -01:07 4L StateCut -2669; +04:47 1L Target 1199
- WB_D5_SW: total -12681 over 3 trades: -23:01 4L StateCut -3274; -01:07 4L StateCut -3349; +05:07 7L StateCut -6059
### session start 08-25 22:00 UTC, session 0, LPB P7 session P&L -12662
- LPB_BASE: total -12662 over 4 trades: +22:09 7L StateCut -5810; -00:04 7L Target 6004; -01:09 7L StateCut -5718; +03:03 7L StateCut -7138
- WB_X_FR_F3: total -10334 over 4 trades: +22:09 7L StateCut -7263; -00:04 7L Target 6004; -01:09 7L StateCut -4370; +03:03 7L StateCut -4705
- WB_D5_SW: total -10255 over 4 trades: +22:58 4L StateCut -3404; -00:04 7L Target 6004; -01:09 7L StateCut -5718; +03:03 7L StateCut -7138
### session start 05-05 22:00 UTC, session 0, LPB P7 session P&L -12366
- LPB_BASE: total -12366 over 2 trades: +23:48 7L StateCut -6223; -00:48 7L StateCut -6143
- WB_X_FR_F3: total -11754 over 2 trades: +23:48 7L StateCut -4998; -00:48 7L StateCut -6756
- WB_D5_SW: total -12366 over 2 trades: +23:48 7L StateCut -6223; -00:48 7L StateCut -6143
### session start 09-30 22:00 UTC, session 0, LPB P7 session P&L -12188
- LPB_BASE: total -12188 over 2 trades: -23:08 7L StateCut -6615; +00:01 7L StateCut -5573
- WB_X_FR_F3: total -8498 over 1 trades: -23:08 7L StopJoin -8498
- WB_D5_SW: total -12188 over 2 trades: -23:08 7L StateCut -6615; +00:01 7L StateCut -5573
### session start 05-15 06:00 UTC, session 1, LPB P7 session P&L -11920
- LPB_BASE: total -11920 over 8 trades: -06:07 4L StateCut -3344; -06:21 4L StateCut -3714; +06:56 1L Target 1199; +07:28 2L StateCut -1699; -09:12 1L Target 1199; -09:42 4L StateCut -3294; -10:40 2L StateCut -1464; +11:01 2L BookLock -802
- WB_X_FR_F3: total -10528 over 10 trades: -06:07 4L StateCut -2724; -06:21 4L StateCut -2764; +06:56 1L Target 1199; +07:28 2L StateCut -1289; -09:12 1L Target 1199; -09:42 4L StateCut -2314; -10:05 2L StateCut -1269; -10:40 2L StateCut -1039; +11:01 2L StateCut -1279; +11:52 2L BookLock -247
- WB_D5_SW: total -11920 over 8 trades: -06:07 4L StateCut -3344; -06:21 4L StateCut -3714; +06:56 1L Target 1199; +07:28 2L StateCut -1699; -09:12 1L Target 1199; -09:42 4L StateCut -3294; -10:40 2L StateCut -1464; +11:01 2L BookLock -802
### session start 10-07 22:00 UTC, session 0, LPB P7 session P&L -11851
- LPB_BASE: total -11851 over 2 trades: +22:21 7L StateCut -5873; -00:56 7L StateCut -5978
- WB_X_FR_F3: total -8963 over 2 trades: +22:21 7L StateCut -4665; -00:56 7L StateCut -4298
- WB_D5_SW: total -11851 over 2 trades: +22:21 7L StateCut -5873; -00:56 7L StateCut -5978
### session start 06-17 22:00 UTC, session 0, LPB P7 session P&L -11837
- LPB_BASE: total -11837 over 2 trades: -23:42 7L StateCut -6615; +00:31 7L StateCut -5221
- WB_X_FR_F3: total -12053 over 2 trades: -23:42 7L StateCut -7578; +00:31 7L StateCut -4475
- WB_D5_SW: total -10253 over 2 trades: -23:42 7L StateCut -6615; +00:35 7L StateCut -3638
### session start 06-02 22:00 UTC, session 0, LPB P7 session P&L -11538
- LPB_BASE: total -11538 over 2 trades: +22:12 7L StateCut -5710; -23:35 7L StateCut -5828
- WB_X_FR_F3: total -12343 over 2 trades: +22:12 7L StateCut -7163; -23:35 7L StateCut -5180
- WB_D5_SW: total -11538 over 2 trades: +22:12 7L StateCut -5710; -23:35 7L StateCut -5828


---- PAGE 2 ----
# DS3_WORKS_B - T-WORKS part B (W-B) incl. P7 FIX part B and D5. PAGE 2, 2026-11-11T22:08Z (date -u). Page 1 (17:35Z) is kept below unchanged.

STATUS: Shadow only, post-hoc, no PASS claims, PRE-PROOF. Preregs WORKS_B_PREREG.md (sha 2167fd1caa1fdef7) and WORKS_B_P7FIX_PREREG.md (sha 39e1955d48481866); context tags P7_CONTEXT_DEFS.md (shared with W-C). All rows exact, one set per job, LPB_BASE reference, cut = stack maxDD cut % (negative = deeper), dmean = $/week, eq = equal-mean cut. Hook identity to the dollar: WB_X_ID (context cut hook), WB_D5_ID (entry-skip hook), WB_ID, WB_BR_ID.

## 0. Plain sentences (page 2)
1. Context-dependent P7 cut (P7 FIX B): choosing the cut by ENTRY context works and the reverse is a clear loser. Fresh trade (1st/2nd P7 trade of the session, not chasing, 30 minutes or more after the last P7 exit) gets the slow V2 line (45/5x/w5/p10); a re-entry or chasing trade gets a fast line. With the fast line 25/20x/w5/p1 (WB_X_FR_F4, 43 months): L6M cut +34.8 percent / +4,435 $/wk, HOLD -11.7 / +310, PRE +22.0 / +1,207, X' +36.3 / -190; equal-mean +49.0 / +12.7 / +39.0 / +50.2; bi-weekly WF vs LPB_BASE +20.75 percent OOS cut, mean -241 $/wk, beats 24 percent of 74 periods. L6M-only rows (6 months, other windows not yet run): fast 30/10x/w5/p2 +30.6 / +2,129 (WB_X_FR_F3), 30/5x/w5/p5 +31.5 / +194, 35/5x/w5/p3 +34.4 / -33, 40/5x/w5/p3 +21.0 / +1,811; the REVERSE control (fresh fast, re-entry V2) is -20.1 / -1,939; by side (short 40/5x/p3, long V2) +22.0 / +3,216; V2 uniform +15.4 / +1,483; by lots: VOID (see final section). Rule 2a label for FR_F4: HOLD drawdown is 11.7 percent deeper (floor -5), so it is RECENTS-ONLY, not a standing change; V2 is the floor so every P7 trade still carries a loss line.
2. Behavioural scorecard (standing principle 19:45Z, W-Q tool, L6M stack per week; LPB_BASE: full stops 24.5/wk -$40.1k, give-backs 9.1/wk, same-side losing runs max 12 / p95 6, no-new-evidence re-entries 37.3/wk): FR_F4 does NOT pass: full stops 25.7/wk (-$44.7k), give-backs 9.4/wk, runs max 13 / p95 7, no-new-evidence 44.2/wk; its gain is smaller losses per cut ("winners skipped 9.4k, losers avoided 8.8k, net +2.6k per week vs LPB_BASE"), not fewer failures. The same is true of never cutting (full stops 36.4/wk, -$94.8k) and of the cut-only-after-a-trend-day rule WB_B2_FPRI (32.4/wk, -$75.4k, runs max 12). A finalist must halve (a), (b), (c); no flag or context cut in part B does, so the repeat-after-failure defect has to be fixed by the entry-side governors (W-C/W-A), not by the cut line. The only thing the cut contributes is cost per failure.
3. P7 cut conditional on the prior day (WB_B2_FPRI = cut ON only when the prior day trended, F_PRIOR; 43 months): L6M +30.7 / +4,119, HOLD +9.9 / +1,103, PRE +7.6 / +364, X' -6.0 / -682 (eq +13.1); WF +17.6 percent OOS cut, +1,389 $/wk, beats 28 percent. The best exact conditional cut by the drawdown-first rule (L6M, HOLD, PRE all positive) but it triples full stops (32.4/wk, scorecard fail), and the day-level family max-stat test (86 flag x direction day mixtures of the cut-on / cut-off exact runs) puts the best mean cut at 17.3 vs a null 95th percentile of 24.1 (p 0.69): the cut-on/off split is as good as random mixing. WB_B2_STK5 (cut off while the stack Calmar5 >= 1): L6M 0.0 / +2,159, HOLD +2.1 / -845, PRE -1.3 / +44, X' +33.8 / +798, WF 0.0 / +596; never cutting (WB_C_NONE): +19.1/+10.4/+27.4 (L6M/PRE/X') and -19.1 HOLD, WF +9.95 / +350.
4. Frozen live week and the context tags: 48 of the 53 live P7 trades are "re-entry or chasing" (only 5 fresh, +10.3k), so the context cut is the fast line on nearly the whole trend week: of the 24 live P7 cuts, 22 are on re-entry/chasing trades (16 saves -$27.9k and 6 recoveries +$61.9k if held), 2 on fresh trades (1 save -$1.9k, 1 recovery +$7.2k). The fast line therefore does NOT spare the recoveries of last week; the week-turn test (no trend week turned losing) cannot be shown for a cut rule, because the live week's recoveries are re-entry trades. The 11-09..11 live week is not on the box.
5. D5 book exhaustion at the signal second (PTR 1-s features, push = max over the previous 60 s, P7/K7/M7 16,652 signals, first-order, 1,034 skip/half cells; leg-based divergence not built, W-C owns D3): no feature removes more worst-20-week losers than best-20-week winners for P7 (best ratio 0.95: pulled_against15 push >= 45 removes -$173k in the worst 20 weeks and +$189k in the best 20). The only selective cell is Asia: sweep_against (ticks the own-side best price retreated in one second) max of the last 60 s >= 16 skips 226 Asia P7 trades: removed worst-20 -$25.4k vs best-20 -$4.9k. Exact (WB_D5_SW, L6M only): +2.8 percent / +1,758 $/wk (eq +11.0), L1M -8.1; the other windows are not run. Reported, not promoted.
6. Carried from page 1 (unchanged): conditional cut-off flags (REG15) lose; near-target stand-in take loses in L6M (-9.1 / -1,253); conditional retarget 8 ticks when atr_rel < 1.3 (WB_B4_R8C) L6M +26.1 / +51, HOLD +8.1 / +460, PRE -10.6 / +227, X' +5.2 / -50, RECENTS-ONLY; `regime` (DayRegime, daily vol_lo/mid/hi at 10:30 ET) cannot carry a per-signal flag, a new per-book `EntryRegime` field is needed (v1.8); the entry-context tag (fresh / rechase) is exactly that field: the policy file's third column would match `r.Regime == b.EntryRegime` with values fresh / rechase, and the cut line per tag goes in the same row as the existing loss-cut grammar.
7. Profit side (conditional protection, exact, P7): WB_B3_P3 (`profit P7 * pct>=0.5 pulled_against_mult>=10 take win=5 persist=5` ON only when stack Calmar10 < 1), 43 months: L6M +23.2 / -710, HOLD +24.8 / -598, PRE -9.9 / -1,370, X' +13.2 / -51; WF -14.6 percent OOS cut, -1,624 $/wk: fails PRE and WF. Clips 11.9 fills per week in L6M (scorecard e), net -$2.4k/wk vs LPB_BASE.

## 1. Exact rows (this page)
| set | months | cut_L1M | dmean_L1M | eq_cut_L1M | cut_L3M | dmean_L3M | eq_cut_L3M | cut_L6M | dmean_L6M | eq_cut_L6M | cut_HOLD | dmean_HOLD | eq_cut_HOLD | cut_PRE | dmean_PRE | eq_cut_PRE | cut_X' | dmean_X' | eq_cut_X' |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| WB_C_V2 | 6 | 1.2 | 6120.8 | 8.5 | 15.4 | 2960.5 | 21.6 | 15.4 | 1482.9 | 21.6 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_C0 | 6 | -3.8 | -1202.2 | 4.4 | 21.0 | 2447.9 | 27.2 | 21.0 | 1810.8 | 27.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_F2 | 6 | 2.4 | -465.3 | 2.2 | 34.4 | -257.9 | 34.3 | 34.4 | -32.7 | 34.3 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_F3 | 6 | 10.3 | 853.8 | 20.9 | 30.6 | 1838.6 | 38.8 | 30.6 | 2129.0 | 38.8 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_FR_F4 | 43 | 27.1 | 2824.3 | 43.0 | 34.8 | 2781.6 | 49.0 | 34.8 | 4435.1 | 49.0 | -11.7 | 310.3 | 12.7 | 22.0 | 1207.1 | 39.0 | 36.3 | -189.8 | 50.2 |
| WB_X_FR_F5 | 6 | 21.7 | 1862.3 | 22.5 | 31.5 | 2591.1 | 32.2 | 31.5 | 194.4 | 32.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_REV | 6 | 3.6 | -276.5 | -7.5 | -20.1 | -2604.4 | -34.0 | -20.1 | -1939.2 | -34.0 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_SIDE | 6 | 13.7 | 1438.8 | 27.2 | 22.0 | 4239.5 | 34.2 | 22.0 | 3216.4 | 34.2 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_X_LOTS | 6 | 1.2 | 6120.8 | 8.5 | 15.4 | 2960.5 | 21.6 | 15.4 | 1482.9 | 21.6 | nan | nan | nan | nan | nan | nan | nan | nan | nan |
| WB_B2_FPRI | 43 | 9.4 | 705.4 | 25.8 | 30.7 | 7365.2 | 43.2 | 30.7 | 4119.1 | 43.2 | 9.9 | 1103.2 | 26.2 | 7.6 | 363.7 | 24.3 | -6.0 | -681.5 | 13.1 |
| WB_B2_STK5 | 43 | 0.0 | -402.6 | 10.4 | 0.0 | 484.0 | 10.4 | 0.0 | 2159.2 | 10.4 | 2.1 | -845.1 | 12.2 | -1.3 | 44.4 | 9.2 | 33.8 | 797.6 | 40.6 |
| WB_B3_P3 | 43 | 21.2 | 2559.7 | 17.5 | 23.2 | 4378.9 | 19.6 | 23.2 | -710.0 | 19.6 | 24.8 | -597.9 | 21.3 | -9.9 | -1369.5 | -15.1 | 13.2 | -51.0 | 9.2 |
| WB_D5_SW | 6 | -8.1 | -418.7 | 1.0 | 2.8 | -62.3 | 11.0 | 2.8 | 1757.5 | 11.0 | nan | nan | nan | nan | nan | nan | nan | nan | nan |

Context-cut sets: WB_X_FR_Fn = fresh V2 / re-entry-or-chasing fast line Fn (F2 35/5x/p3, F3 30/10x/p2, F4 25/20x/p1, F5 30/5x/p5, C0 40/5x/p3); WB_X_REV reverse; WB_X_LOTS/SIDE by lots/side; all windows shown only when complete; L6M-only rows are screens.

## 2. Worst-10 P7 sessions (L6M, by LPB_BASE P7 session P&L), entry by entry: LPB_BASE vs WB_X_FR_F4 vs WB_B2_FPRI (times are UTC entry minutes; exit name and $ per trade)
### session start 07-27 22:00 UTC, session 0, LPB P7 session P&L -14274
- LPB_BASE: total -14274 over 8 trades: -22:38 4L StateCut -3007; -00:11 4L Target 4800; -01:06 5L Target 5984; -01:23 7L StateCut -5705; -02:14 4L StateCut -3254; +03:54 4L StateCut -3694; +04:43 4L StateCut -3394; -05:40 7L StateCut -6005
- WB_X_FR_F4: total -10462 over 7 trades: -22:38 4L StateCut -2412; -00:11 4L StateCut -2204; -00:51 4L Target 4800; -01:23 7L StateCut -3990; -02:14 4L StateCut -1934; -02:27 4L StateCut -2209; +03:54 4L StateCut -2514
- WB_B2_FPRI: total -8562 over 4 trades: -22:38 4L Target 1105; -00:32 4L StopJoin -4710; -00:51 4L Target 4800; -01:23 7L StopJoinFallback -9758
### session start 05-27 13:30 UTC, session 3, LPB P7 session P&L -13000
- LPB_BASE: total -13000 over 5 trades: -14:11 4L StateCut -3374; -14:33 3L StateCut -2449; -15:00 4L StateCut -3654; -15:20 2L StateCut -1759; -15:39 2L StateCut -1764
- WB_X_FR_F4: total -8630 over 5 trades: -14:11 4L StateCut -1844; -14:33 3L StateCut -1894; -15:00 4L StateCut -1964; -15:20 2L StateCut -1799; -15:39 2L StateCut -1129
- WB_B2_FPRI: total 16 over 2 trades: -14:11 4L Target 4790; -15:00 4L StopJoinFallback -4775
### session start 09-09 22:00 UTC, session 0, LPB P7 session P&L -12681
- LPB_BASE: total -12681 over 3 trades: -23:01 4L StateCut -3274; -01:07 4L StateCut -3349; +05:07 7L StateCut -6059
- WB_X_FR_F4: total -3764 over 3 trades: -23:01 4L StateCut -2884; -01:07 4L StateCut -2079; +04:47 1L Target 1199
- WB_B2_FPRI: total 1239 over 3 trades: -23:01 4L Target 4790; -02:17 4L StopJoin -4750; +04:47 1L Target 1199
### session start 08-25 22:00 UTC, session 0, LPB P7 session P&L -12662
- LPB_BASE: total -12662 over 4 trades: +22:09 7L StateCut -5810; -00:04 7L Target 6004; -01:09 7L StateCut -5718; +03:03 7L StateCut -7138
- WB_X_FR_F4: total -9542 over 3 trades: +22:09 7L StateCut -7263; -00:04 7L Target 6004; -01:09 7L StopJoinFallback -8283
- WB_B2_FPRI: total -9358 over 1 trades: +22:09 7L StopJoinFallback -9358
### session start 05-05 22:00 UTC, session 0, LPB P7 session P&L -12366
- LPB_BASE: total -12366 over 2 trades: +23:48 7L StateCut -6223; -00:48 7L StateCut -6143
- WB_X_FR_F4: total -11754 over 2 trades: +23:48 7L StateCut -4998; -00:48 7L StateCut -6756
- WB_B2_FPRI: total -12366 over 2 trades: +23:48 7L StateCut -6223; -00:48 7L StateCut -6143
### session start 09-30 22:00 UTC, session 0, LPB P7 session P&L -12188
- LPB_BASE: total -12188 over 2 trades: -23:08 7L StateCut -6615; +00:01 7L StateCut -5573
- WB_X_FR_F4: total -8498 over 1 trades: -23:08 7L StopJoin -8498
- WB_B2_FPRI: total -8498 over 1 trades: -23:08 7L StopJoin -8498
### session start 05-15 06:00 UTC, session 1, LPB P7 session P&L -11920
- LPB_BASE: total -11920 over 8 trades: -06:07 4L StateCut -3344; -06:21 4L StateCut -3714; +06:56 1L Target 1199; +07:28 2L StateCut -1699; -09:12 1L Target 1199; -09:42 4L StateCut -3294; -10:40 2L StateCut -1464; +11:01 2L BookLock -802
- WB_X_FR_F4: total -7617 over 10 trades: -06:07 4L StateCut -2004; -06:21 4L StateCut -2244; +06:56 1L Target 1199; +07:28 2L StateCut -1679; -09:12 1L Target 1199; -09:42 4L StateCut -2094; -10:40 2L StateCut -1139; +11:01 2L StateCut -984; +11:52 2L StateCut -1069; -12:25 1L Target 1199
- WB_B2_FPRI: total -9962 over 6 trades: -06:07 4L StopJoin -3425; +06:56 1L Target 1199; +07:28 2L StopJoin -2342; -09:12 1L Target 1199; -09:42 4L StopJoinFallback -4630; -10:40 2L BookLock -1962
### session start 10-07 22:00 UTC, session 0, LPB P7 session P&L -11851
- LPB_BASE: total -11851 over 2 trades: +22:21 7L StateCut -5873; -00:56 7L StateCut -5978
- WB_X_FR_F4: total -12082 over 2 trades: +22:21 7L StateCut -6979; -00:56 7L StateCut -5103
- WB_B2_FPRI: total 1588 over 2 trades: +22:21 7L StopJoinFallback -6808; -04:10 7L Target 8397
### session start 06-17 22:00 UTC, session 0, LPB P7 session P&L -11837
- LPB_BASE: total -11837 over 2 trades: -23:42 7L StateCut -6615; +00:31 7L StateCut -5221
- WB_X_FR_F4: total -11178 over 2 trades: -23:42 7L StateCut -7578; +00:31 7L StateCut -3600
- WB_B2_FPRI: total -14022 over 2 trades: -23:42 7L StopJoin -8148; +00:31 7L StopJoin -5873
### session start 06-02 22:00 UTC, session 0, LPB P7 session P&L -11538
- LPB_BASE: total -11538 over 2 trades: +22:12 7L StateCut -5710; -23:35 7L StateCut -5828
- WB_X_FR_F4: total -11048 over 2 trades: +22:12 7L StateCut -7163; -23:35 7L StateCut -3885
- WB_B2_FPRI: total -8643 over 1 trades: +22:12 7L StopJoin -8643


## 3. Missing / next
11-09..11 live week; JN04RM-base versions of the winners (IJK jbjobs driver) and the exact JN05 joint with W-J; WB_X_LOTS (2 months to go), WB_X_FR_F2/F3/F5/SIDE other windows (F4 first); D5 other windows; scorecard on the four-window finalists once W-Q posts the acceptance file.

---- PAGE 1 (17:35Z) ----
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



## C. P7 anatomy (C)

Source DS3_WORKS_C.md (mtime 2026-11-12T02:52:28Z UTC), included verbatim, read only:

# P7 FIX - session governors and entry-quality tests (W-C; orders 19:05, 19:15, 19:30, 19:45Z); Shadow only, no PASS claim

## Acceptance test on the live references (acceptance_p7.py, code/th_works_c; usage in its first lines and in autopilot/P7_CONTEXT_DEFS.md)
| set | fails of the 20 worst sessions | all P7: max run / p95 / mean | sessions with run>=3 | $ lost on 3rd+ same-side losers | 3rd+ attempts without new evidence (n / $) | Asia: max / $ on 3rd+ | verdict |
|---|---|---|---|---|---|---|---|
| LPB_BASE (all 43 months) | 3/20 | 6 / 2.0 / 0.89 | 48 | -136326 | 90 / -11382 | 6 / -80482 | FAIL |
| JN04RM (all 43 months) | 4/20 | 6 / 2.0 / 0.94 | 78 | -99088 | 162 / +7640 | 6 / -45408 | FAIL |
| WG_A4 (9 months 202602..202610) | 3/16 | 5 / 2.0 / 1.12 | 16 | -25128 | 29 / -4157 | 4 / -17134 | FAIL |
|   JN04RM, same months | 4/16 | 5 / 3.0 / 1.26 | 31 | -41321 | 75 / +14670 | 4 / -20713 | FAIL |
| WG_E1 (27 months 202304..202610) | 2/17 | 4 / 2.0 / 0.99 | 25 | -36984 | 0 / +0 | 4 / -25183 | PASS |
|   JN04RM, same months | 4/17 | 6 / 2.0 / 1.02 | 63 | -84844 | 133 / +299 | 6 / -42769 | FAIL |
| WG_E1A (12 months 202511..202610) | 4/16 | 5 / 3.0 / 1.21 | 38 | -51898 | 51 / -159 | 4 / -21517 | FAIL |
|   JN04RM, same months | 4/16 | 5 / 3.0 / 1.21 | 39 | -52653 | 89 / +10241 | 4 / -25666 | FAIL |
| WG_E1L (6 months 202605..202610) | 1/15 | 4 / 2.0 / 1.22 | 8 | -33873 | 0 / +0 | 4 / -33873 | PASS |
|   LPB_BASE, same months | 3/20 | 6 / 2.0 / 0.89 | 48 | -136326 | 90 / -11382 | 6 / -80482 | FAIL |
| WG_E2Q (12 months 202511..202610) | 2/16 | 5 / 3.0 / 1.23 | 44 | -48913 | 98 / +8522 | 4 / -20129 | PASS |
|   JN04RM, same months | 4/16 | 5 / 3.0 / 1.21 | 39 | -52653 | 89 / +10241 | 4 / -25666 | FAIL |
| WG_E4 (12 months 202511..202610) | 0/16 | 4 / 2.0 / 1.19 | 21 | -34260 | 0 / +0 | 4 / -25986 | PASS |
|   JN04RM, same months | 4/16 | 5 / 3.0 / 1.21 | 39 | -52653 | 89 / +10241 | 4 / -25666 | FAIL |
| WG_E5 (12 months 202511..202610) | 0/16 | 4 / 2.0 / 1.19 | 21 | -23724 | 0 / +0 | 4 / -16337 | PASS |
|   JN04RM, same months | 4/16 | 5 / 3.0 / 1.21 | 39 | -52653 | 89 / +10241 | 4 / -25666 | FAIL |
| WG_E6 (8 months 202603..202610) | 0/16 | 2 / 2.0 / 1.22 | 0 | +0 | 0 / +0 | 2 / +0 | PASS |
|   JN04RM, same months | 4/16 | 5 / 3.0 / 1.27 | 28 | -38987 | 70 / +14606 | 4 / -19373 | FAIL |
| WG_E7 (12 months 202511..202610) | 4/16 | 5 / 2.0 / 1.14 | 23 | -36073 | 44 / +10157 | 5 / -21588 | FAIL |
|   JN04RM, same months | 4/16 | 5 / 3.0 / 1.21 | 39 | -52653 | 89 / +10241 | 4 / -25666 | FAIL |
| WL_A4 (6 months 202605..202610) | 2/15 | 3 / 2.0 / 1.13 | 8 | -28270 | 11 / -2594 | 3 / -25859 | PASS |
|   LPB_BASE, same months | 3/20 | 6 / 2.0 / 0.89 | 48 | -136326 | 90 / -11382 | 6 / -80482 | FAIL |
| WL_E1 (12 months 202511..202610) | 1/16 | 4 / 2.0 / 1.13 | 12 | -44762 | 0 / +0 | 4 / -39774 | PASS |
|   LPB_BASE, same months | 3/20 | 6 / 2.0 / 0.89 | 48 | -136326 | 90 / -11382 | 6 / -80482 | FAIL |
| WL_E1A (6 months 202605..202610) | 3/15 | 5 / 2.0 / 1.25 | 13 | -47429 | 12 / -1562 | 4 / -33873 | FAIL |
|   LPB_BASE, same months | 3/20 | 6 / 2.0 / 0.89 | 48 | -136326 | 90 / -11382 | 6 / -80482 | FAIL |
| WL_E2Q (12 months 202511..202610) | 2/16 | 5 / 3.0 / 1.20 | 34 | -41595 | 71 / +7546 | 4 / -18442 | PASS |
|   LPB_BASE, same months | 3/20 | 6 / 2.0 / 0.89 | 48 | -136326 | 90 / -11382 | 6 / -80482 | FAIL |
| WL_E4 (12 months 202511..202610) | 1/16 | 4 / 2.0 / 1.13 | 14 | -49355 | 0 / +0 | 4 / -44367 | PASS |
|   LPB_BASE, same months | 3/20 | 6 / 2.0 / 0.89 | 48 | -136326 | 90 / -11382 | 6 / -80482 | FAIL |
| WL_E5 (6 months 202605..202610) | 1/15 | 4 / 2.0 / 1.23 | 9 | -23111 | 0 / +0 | 4 / -23111 | PASS |
|   LPB_BASE, same months | 3/20 | 6 / 2.0 / 0.89 | 48 | -136326 | 90 / -11382 | 6 / -80482 | FAIL |
| WL_E6 (6 months 202605..202610) | 1/15 | 2 / 2.0 / 1.21 | 0 | +0 | 0 / +0 | 2 / +0 | PASS |
|   LPB_BASE, same months | 3/20 | 6 / 2.0 / 0.89 | 48 | -136326 | 90 / -11382 | 6 / -80482 | FAIL |
| WL_E7 (12 months 202511..202610) | 3/16 | 4 / 2.0 / 1.10 | 17 | -40710 | 25 / +21560 | 4 / -30895 | FAIL |
|   LPB_BASE, same months | 3/20 | 6 / 2.0 / 0.89 | 48 | -136326 | 90 / -11382 | 6 / -80482 | FAIL |

## First-order sequential screen on the exact LPB_BASE P7 list (stack level, P7 outcomes scaled/removed, no follow-on; saved $ positive = losers removed; the frozen week is the 53 live P7 trades)

### Evidence governors (E1-E10): "no new evidence" = no new session extreme in the trade direction beyond the extreme at the last same-side failure and no opposite-side P7 entry since
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| E6 all 2nd attempt half, 3rd always skip | 143 / 419 | -3 / +2081 | -14 / +829 | 15 / -35 | 2 / -64 | +50242 / -1780 | -35737 (12) | 0 / +0 |
| E6 asia 2nd attempt half, 3rd always skip | 63 / 202 | -4 / +1548 | -5 / +678 | 13 / -233 | -1 / -39 | +41315 / -19198 | -31504 (11) | 29 / -50856 |
| E7 all noevid & lgap<30 skip | 380 / 0 | 0 / +1224 | -12 / -233 | 11 / +456 | -4 / +226 | +42317 / +16658 | -600 (7) | 10 / -27909 |
| E7 all noevid & lgap<60 skip | 538 / 0 | -2 / +1156 | -23 / +244 | 15 / +56 | -1 / +96 | +42133 / -27143 | -7503 (10) | 4 / -11362 |
| E2 all noevid(after same-side loss) q | 0 / 465 | -9 / +1110 | -11 / -9 | 18 / +147 | 2 / +133 | +42994 / +6077 | -9687 (0) | 53 / -51927 |
| E7 all noevid & lgap<120 skip | 605 / 0 | -10 / +1074 | -29 / +465 | 14 / +61 | -3 / -29 | +67591 / -30186 | -14669 (12) | 0 / +0 |
| E5 all 2nd attempt half, 3rd noevid skip | 101 / 442 | -1 / +864 | -14 / +650 | 13 / +77 | 2 / -64 | +41765 / +15897 | -26019 (4) | 0 / +0 |
| E2 all noevid(after same-side loss) half | 0 / 465 | -4 / +848 | -8 / +80 | 14 / +202 | 2 / +106 | +30395 / +14229 | -5901 (0) | 53 / -72503 |
| E8 asia noevid skip + lgap<120 same skip after 2nd | 55 / 0 | 0 / +836 | -5 / +588 | 13 / -120 | 0 / +0 | +19306 / +10887 | -26398 (9) | 29 / -50856 |
| E9 all short-only noevid skip | 337 / 0 | -2 / +834 | -6 / -532 | 14 / -175 | -1 / -168 | +40601 / -57695 | -20082 (10) | 25 / -59845 |
| E2 all noevid(after same-side loss) skip | 627 / 0 | -15 / +654 | -28 / -489 | 14 / +80 | -3 / -29 | +63989 / -37143 | -23035 (13) | 0 / +0 |
| E4 all noevid half + 3rd skip | 101 / 395 | -4 / +623 | -17 / +477 | 12 / +69 | 2 / -36 | +38303 / +9700 | -17683 (4) | 0 / +0 |
| E8 all noevid skip + lgap<120 same skip after 2nd | 128 / 0 | -0 / +520 | -15 / +253 | 12 / -120 | 0 / +20 | +15947 / -4274 | -28788 (10) | 0 / +0 |
| E8 asia noevid skip + lgap<60 same skip after 2nd | 49 / 0 | 0 / +297 | -5 / +323 | 13 / -39 | 0 / +0 | +18035 / +7009 | -18305 (6) | 29 / -50856 |
| E8 asia noevid skip + lgap<30 same skip after 2nd | 48 / 0 | 0 / +262 | -5 / +306 | 13 / -39 | 0 / +0 | +18035 / +8520 | -31935 (6) | 29 / -50856 |
| E5 asia 2nd attempt half, 3rd noevid skip | 46 / 212 | -4 / +256 | -5 / +12 | 13 / -97 | -1 / -39 | +32595 / -5602 | -22980 (4) | 29 / -50856 |
| E7 asia noevid & lgap<120 skip | 241 / 0 | -12 / +252 | -11 / -426 | 14 / -106 | -4 / -103 | +47569 / -34431 | -13367 (8) | 29 / -50856 |
| E7 asia noevid & lgap<60 skip | 207 / 0 | -6 / +240 | -8 / -285 | 11 / -191 | 0 / +8 | +24791 / -59066 | -8591 (7) | 32 / -60474 |
| E1 all loss_same>=2 & noevid skip | 101 / 0 | 0 / +237 | -15 / +283 | 9 / -122 | 0 / +20 | +10668 / +3126 | -15198 (4) | 0 / +0 |
| E10 all noevid & chase>1 skip | 381 / 0 | 9 / +236 | -20 / -721 | 14 / -120 | -1 / -33 | +38163 / -42468 | -4974 (6) | 16 / -42622 |

### A1 loss-count step-down / off
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| A1 asia loss>=2 same skip | 63 / 0 | 0 / +1192 | -5 / +828 | 13 / -201 | 0 / +0 | +26208 / +1794 | -32310 (11) | 29 / -50856 |
| A1 all loss>=1 same q | 0 / 497 | -4 / +1096 | -7 / +145 | 18 / +91 | 2 / +105 | +42676 / +8060 | -16505 (0) | 53 / -51927 |
| A1 all loss>=2 same skip | 143 / 0 | -0 / +1000 | -15 / +583 | 12 / -179 | 0 / +20 | +22850 / -6978 | -34700 (12) | 0 / +0 |
| A1 all loss>=1 same half | 0 / 497 | -1 / +922 | -5 / +516 | 14 / +181 | 2 / +78 | +31257 / +16942 | -10649 (0) | 53 / -72503 |
| A1 all loss>=1 same skip | 859 / 0 | -14 / +299 | -29 / -1627 | 24 / +37 | -1 / +56 | +93939 / -158821 | -38768 (25) | 0 / +0 |
| A1 all loss>=3 same skip | 17 / 0 | 0 / +203 | 0 / +110 | 8 / +24 | 0 / +0 | +12230 / +11782 | -4776 (1) | 44 / -102140 |

### A2 trade-count and $ loss caps per session
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| A2 all sessloss>=12600 skip | 65 / 0 | 0 / +495 | 0 / +5 | 15 / +241 | 0 / +0 | +26355 / -19299 | -19158 (9) | 47 / -104818 |
| A2 asia sessloss>=12600 skip | 63 / 0 | 0 / +463 | 0 / -11 | 11 / +193 | 0 / +0 | +22840 / -20101 | -19158 (9) | 47 / -104818 |
| A2 asia trades>=6 skip | 90 / 0 | 0 / +179 | 0 / +378 | 18 / -4 | 0 / +0 | +33126 / +41 | -7118 (9) | 45 / -98522 |
| A2 all trades>=6 skip | 130 / 0 | 0 / +84 | -6 / +316 | 18 / +6 | 0 / +0 | +43676 / -736 | -5223 (10) | 44 / -96179 |
| A2 all trades>=5 skip | 236 / 0 | -9 / -1648 | -14 / -1128 | 18 / +225 | 0 / +0 | +106332 / -67472 | -17437 (13) | 39 / -85278 |
| A2 asia trades>=2 skip | 753 / 0 | -29 / -1824 | -26 / -3963 | 27 / +287 | 4 / -11 | +170292 / -356891 | -51845 (23) | 29 / -50856 |

### A3 step-down lots
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| A3 all step 0.5 | 0 / 1224 | 5 / +1165 | 5 / -242 | 25 / +652 | 3 / +98 | +118331 / -70443 | -22323 (0) | 53 / -51100 |
| A3 all step 0.7 | 0 / 1224 | 7 / +440 | 0 / -590 | 26 / +586 | 2 / +82 | +84732 / -62538 | -19105 (0) | 53 / -65372 |
| A3 asia step 0.5 | 0 / 690 | -4 / -821 | -2 / -1318 | 17 / +233 | -4 / -291 | +83332 / -110979 | -19331 (0) | 53 / -76049 |
| A3 asia step 0.7 | 0 / 690 | -0 / -1022 | 2 / -1182 | 19 / +201 | -2 / -221 | +55678 / -84979 | -15816 (0) | 53 / -88591 |

### A4 re-entry gap after a loss (30/60/90/120/rest of session, same vs both, chasing flag)
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| A4 all lossgap<120 both | 1528 / 0 | 13 / +3438 | -1 / -1152 | 16 / +570 | -16 / -215 | +183787 / -233914 | -34886 (23) | 1 / -5880 |
| A4 all lossgap<90 same | 681 / 0 | 10 / +2598 | -10 / +205 | 19 / +20 | 2 / +91 | +56581 / -21556 | -30947 (17) | 3 / -9891 |
| A4 all lossgap<60 both | 1196 / 0 | 20 / +2541 | -16 / +864 | 6 / +804 | -14 / -324 | +110566 / -42756 | -10247 (16) | 8 / -28425 |
| A4 all lossgap<90 same chase>0.75 | 477 / 0 | 20 / +2357 | -7 / +101 | 19 / -291 | 3 / -52 | +31606 / -25105 | -21253 (11) | 18 / -49194 |
| A4 all lossgap<60 same chase>2.00 | 292 / 0 | 8 / +2171 | -24 / +367 | 21 / +134 | 1 / -174 | +38617 / +2839 | +5240 (6) | 27 / -65388 |
| A4 all lossgap<120 same chase>1.00 | 504 / 0 | 20 / +1920 | -12 / -151 | 18 / -438 | 1 / +33 | +48036 / -65680 | -6213 (12) | 16 / -42622 |

### A5 chasing filter
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| A5 asia chase>0.75 & gap<30 skip | 528 / 0 | 9 / +317 | -15 / -2186 | 10 / -123 | -9 / -448 | +139472 / -342940 | -41043 (9) | 43 / -93175 |
| A5 asia chase>1.00 & gap<30 skip | 521 / 0 | 5 / +235 | -19 / -2190 | 10 / -172 | -10 / -529 | +137946 / -360641 | -41043 (9) | 44 / -96449 |
| A5 asia chase>2.00 & n>=3 half | 0 / 430 | -6 / +6 | -4 / -730 | 18 / -136 | 2 / +31 | +46433 / -86309 | -10146 (0) | 53 / -112170 |
| A5 all chase>1.00 & n>=3 half | 0 / 813 | 1 / -18 | 1 / -833 | 27 / +108 | 4 / +60 | +69252 / -81947 | -8204 (0) | 53 / -93448 |
| A5 all chase>2.00 & gap<30 skip | 950 / 0 | 29 / -30 | -7 / -2391 | 21 / -839 | 0 / -864 | +177646 / -459527 | -34474 (12) | 30 / -72838 |
| A5 asia chase>1.00 & n>=3 half | 0 / 484 | -6 / -30 | -4 / -838 | 20 / -66 | 2 / +90 | +48206 / -95458 | -10146 (0) | 53 / -112170 |

### A6 short side
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| A6 asia short loss>=2 same skip | 35 / 0 | 0 / +437 | -5 / +355 | 10 / +8 | 0 / +0 | +17034 / +1392 | -32310 (11) | 39 / -84479 |
| A6 all short loss>=1 same half | 0 / 267 | 3 / +415 | -1 / -75 | 5 / +113 | 3 / -100 | +13093 / -2916 | -6786 (0) | 53 / -99183 |
| A6 all short loss>=2 same skip | 80 / 0 | -0 / +211 | -5 / +373 | 5 / -21 | 0 / +0 | +14686 / -3408 | -32310 (11) | 25 / -59845 |
| A6 asia short loss>=1 same half | 0 / 141 | -1 / -228 | 0 / -378 | 6 / -1 | 1 / +0 | +6079 / -17718 | -5341 (0) | 53 / -109282 |

### D1 trend-alive clock
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| D1 all since_ext>15 & loss>=1 half | 0 / 1085 | 5 / +632 | -9 / -1123 | 23 / +458 | 9 / -67 | +74189 / -76252 | -11933 (0) | 53 / -72503 |
| D1 asia since_ext>60 skip | 549 / 0 | 5 / +396 | 4 / -1553 | 8 / -304 | -20 / -957 | +96522 / -230713 | -39465 (12) | 35 / -65355 |
| D1 all since_ext>15 & loss>=1 skip | 1348 / 0 | 8 / +229 | -20 / -3295 | 16 / +523 | 0 / -697 | +158901 / -276876 | -29484 (24) | 0 / +0 |
| D1 all since_ext>60 & loss>=1 half | 0 / 671 | 10 / +12 | -6 / -479 | 22 / +537 | 5 / -157 | +53337 / -23298 | -14521 (0) | 53 / -87132 |
| D1 all since_ext>30 & loss>=1 half | 0 / 914 | 4 / -112 | -6 / -1090 | 22 / +449 | 7 / -55 | +67331 / -58881 | -13948 (0) | 53 / -76077 |
| D1 asia since_ext>30 half | 0 / 900 | 8 / -261 | 2 / -928 | 2 / -41 | 13 / -261 | +74739 / -162455 | -17130 (0) | 53 / -94631 |

### D3 pullback number
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| D3 asia pb>=3 skip | 365 / 0 | -17 / +625 | -15 / -758 | 20 / -292 | 0 / +0 | +78465 / -147183 | -41423 (15) | 29 / -50856 |
| D3 all pb>=3 half | 0 / 584 | -3 / +604 | -7 / -446 | 15 / -170 | 1 / +90 | +39589 / -63685 | -16517 (0) | 53 / -72503 |
| D3 all pb>=3 skip | 681 / 0 | -9 / +579 | -19 / -1573 | 24 / -612 | -0 / +174 | +83898 / -195865 | -39931 (22) | 0 / +0 |
| D3 asia pb>=3 half | 0 / 352 | -7 / +369 | -4 / -226 | 14 / -100 | 0 / +0 | +33605 / -55705 | -18459 (0) | 53 / -92884 |
| D3 all pb>=4 half | 0 / 256 | 0 / +178 | -15 / -689 | 12 / +20 | 0 / +0 | +36242 / -53429 | -6018 (0) | 53 / -102011 |
| D3 all pb>=4 skip | 294 / 0 | -1 / -4 | -35 / -1762 | 21 / -211 | 0 / +0 | +83345 / -157665 | -14150 (13) | 30 / -68004 |

### D4 extension from value
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| D4 all dev>3.0 half | 0 / 1543 | 4 / +655 | 6 / +45 | 19 / -287 | -5 / -44 | +138891 / -169919 | -13098 (0) | 53 / -108801 |
| D4 all dev>3.0 & loss>=1 half | 0 / 590 | 2 / +255 | 1 / -81 | 15 / +407 | -4 / -38 | +85339 / -62381 | -8697 (0) | 53 / -108801 |
| D4 all dev>1.0 & loss>=1 half | 0 / 1090 | 6 / +105 | -3 / -1529 | 27 / +355 | -2 / +46 | +101218 / -152054 | -16451 (0) | 53 / -95734 |
| D4 all dev>2.0 & loss>=1 half | 0 / 832 | 5 / +93 | -7 / -778 | 18 / +27 | -3 / +1 | +100387 / -111007 | -15946 (0) | 53 / -103846 |
| D4 asia dev>2.0 half | 0 / 759 | -8 / -155 | -6 / -1396 | 16 / -414 | -8 / -289 | +107499 / -244476 | -15061 (0) | 53 / -119101 |
| D4 all dev>3.0 & loss>=1 skip | 685 / 0 | -1 / -171 | 1 / -705 | 25 / +517 | -16 / -306 | +184127 / -205778 | -21904 (16) | 34 / -84753 |

### D6 cross-book vote
| governor | removed / halved | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | saved $ in worst-20 weeks / other weeks (all 3.5y) | frozen live week d$ (n removed) | losing 3rd+ no-evidence entries left (n / $) |
|---|---|---|---|---|---|---|---|---|
| D6 asia vote<1 half | 0 / 1207 | -16 / -1047 | -14 / -1536 | 6 / -435 | 33 / +1097 | +111744 / -219564 | -5727 (0) | 53 / -96109 |
| D6 all vote<3 half | 0 / 4064 | 22 / -1990 | 15 / -2794 | 31 / -500 | 39 / +1288 | +259201 / -497991 | -36345 (0) | 53 / -72503 |
| D6 all vote<1 half | 0 / 2199 | -8 / -2007 | -6 / -1863 | 13 / -459 | 38 / +1756 | +150314 / -264682 | -10773 (0) | 53 / -83000 |
| D6 all vote<2 half | 0 / 3711 | 23 / -2064 | 13 / -2646 | 21 / -578 | 37 / +1388 | +228955 / -467487 | -32836 (0) | 53 / -72503 |
| D6 asia vote<2 half | 0 / 1975 | -2 / -2197 | -0 / -2791 | 10 / -1001 | 29 / +786 | +164897 / -420201 | -29155 (0) | 53 / -92884 |
| D6 asia vote<3 half | 0 / 2182 | -9 / -2651 | -7 / -2932 | 14 / -982 | 29 / +681 | +188104 / -459238 | -31515 (0) | 53 / -92884 |

## Exact runs (WG_* on the dressed base JN04RM; WL_* and WG_E1L on the live panel base LPB, compared with LPB_BASE; one set per job; hook c_gov.py)

| set | months | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | L6M worst-20 cell/ref $k | WF beat % | rule-2a label |
|---|---|---|---|---|---|---|---|---|
| WG_A4 | 10 | -10.4 / +9 | n/a | n/a | n/a | 124/138 | n/a | |
| WG_E1 | 28 | 0.0 / +20 | -4.6 / +59 | n/a | 0.0 / +19 | 140/138 | n/a | |
| WG_E1A | 12 | 0.0 / -84 | -5.9 / -18 | n/a | n/a | 139/138 | n/a | |
| WG_E1K | 0 | not started | | | | | | |
| WG_E1L | 6 | 0.0 / -416 | n/a | n/a | n/a | 81/102 | n/a | |
| WG_E1M | 0 | not started | | | | | | |
| WG_E2Q | 12 | -8.6 / -343 | -0.5 / -576 | n/a | n/a | 122/138 | n/a | |
| WG_E4 | 12 | -5.7 / -669 | -1.8 / -307 | n/a | n/a | 116/138 | n/a | |
| WG_E5 | 12 | -3.0 / -471 | -0.6 / -202 | n/a | n/a | 119/138 | n/a | |
| WG_E6 | 8 | -5.6 / -601 | n/a | n/a | n/a | 117/138 | n/a | |
| WG_E7 | 13 | -5.2 / -340 | -6.5 / -519 | n/a | n/a | 142/138 | n/a | |
| WL_A4 | 6 | 11.9 / +423 | n/a | n/a | n/a | 120/102 | n/a | |
| WL_E1 | 12 | 0.0 / -416 | -14.5 / -143 | n/a | n/a | 81/102 | n/a | |
| WL_E1A | 7 | -0.0 / -829 | n/a | n/a | n/a | 76/102 | n/a | |
| WL_E2Q | 12 | -5.2 / +748 | -8.8 / -570 | n/a | n/a | 92/102 | n/a | |
| WL_E4 | 12 | -2.1 / -631 | -19.8 / -750 | n/a | n/a | 75/102 | n/a | |
| WL_E5 | 6 | 1.1 / +128 | n/a | n/a | n/a | 87/102 | n/a | |
| WL_E6 | 6 | -0.5 / +552 | n/a | n/a | n/a | 94/102 | n/a | |
| WL_E7 | 12 | 0.8 / +376 | -1.5 / -429 | n/a | n/a | 110/102 | n/a | |

## Behavioural scorecard (items a-e)

### Behavioural scorecard JN04RM (W-Q tool, ref JN04RM)
```
JN04RM L6M (stack, per week): full stops 25.4/wk $-38130; give-backs 9.9/wk (9.8 round-trips) realised $-11306, forgone vs target $28091; same-side losing runs max 13, p95 7, $-42885 lost on 3rd-and-later; no-new-evidence re-entries 43.3/wk $1885; recoveries cut 15.2/wk $39718, clipped fills 0.0/wk $0; pnl $19530/wk.
JN04RM HOLD (stack, per week): full stops 23.6/wk $-35520; give-backs 8.6/wk (8.4 round-trips) realised $-9743, forgone vs target $24378; same-side losing runs max 13, p95 6, $-37009 lost on 3rd-and-later; no-new-evidence re-entries 34.2/wk $1140; recoveries cut 13.1/wk $34017, clipped fills 0.0/wk $0; pnl $12497/wk.
JN04RM PRE (stack, per week): full stops 16.8/wk $-26445; give-backs 5.4/wk (5.0 round-trips) realised $-5634, forgone vs target $14565; same-side losing runs max 11, p95 5, $-17863 lost on 3rd-and-later; no-new-evidence re-entries 14.4/wk $-45; recoveries cut 7.2/wk $17046, clipped fills 0.0/wk $0; pnl $9409/wk.
JN04RM X' (stack, per week): full stops 17.7/wk $-27189; give-backs 3.5/wk (3.0 round-trips) realised $-3615, forgone vs target $9772; same-side losing runs max 7, p95 4, $-9998 lost on 3rd-and-later; no-new-evidence re-entries 3.1/wk $562; recoveries cut 2.5/wk $6540, clipped fills 0.0/wk $0; pnl $1547/wk.

```

### Behavioural scorecard WG_E1 (W-Q tool, ref JN04RM)
```
WG_E1 L6M (stack, per week): full stops 25.4/wk $-38079; give-backs 9.9/wk (9.8 round-trips) realised $-11307, forgone vs target $28092; same-side losing runs max 13, p95 6, $-42134 lost on 3rd-and-later; no-new-evidence re-entries 40.8/wk $1434; recoveries cut 14.8/wk $38876, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2489/wk, losers avoided $1938/wk, net -174 $/wk; pnl $19356/wk.
WG_E1 HOLD (stack, per week): full stops 23.6/wk $-35496; give-backs 8.6/wk (8.4 round-trips) realised $-9734, forgone vs target $24323; same-side losing runs max 13, p95 6, $-36640 lost on 3rd-and-later; no-new-evidence re-entries 32.5/wk $1083; recoveries cut 12.9/wk $33401, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $1707/wk, losers avoided $1536/wk, net +246 $/wk; pnl $12743/wk.
WG_E1 PRE: months missing (12 of 17), window not scored
WG_E1 X' (stack, per week): full stops 17.7/wk $-27189; give-backs 3.5/wk (2.9 round-trips) realised $-3595, forgone vs target $9725; same-side losing runs max 7, p95 4, $-9959 lost on 3rd-and-later; no-new-evidence re-entries 3.0/wk $601; recoveries cut 2.5/wk $6540, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $0/wk, losers avoided $38/wk, net +38 $/wk; pnl $1585/wk.

```


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


## 02:50Z update (P7 FIX, exact, 8 lanes on the TP engine)
A. Dressed base (JN04RM), L6M / HOLD / X' maxDD cut and d$/wk: WG_E1 (evidence rule, all sessions) 0.0 / -4.6 / 0.0 percent and +$20 / +$59 / +$19 per week; WG_E1A (Asia only) 0.0 / -5.9, -$84 / -$18; WG_E5 -3.0 / -0.6, -$471 / -$202; WG_E4 -5.7 / -1.8, -$669 / -$307; WG_E2Q -8.6 / -0.5, -$343 / -$576; WG_E6 -5.6 (L6M), -$601; WG_E7 (no evidence and within 30 min of a loss) -5.2 / -6.5, -$340 / -$519; WG_A4 (same-side re-entry within 90 min of a loss while chasing) -10.4 (L6M), +$9. Every governor is inside the engine noise floor (about 8 percent, $1.2k/wk) and none improves L6M drawdown; WG_E1 is the only one that costs nothing in mean on three windows.
B. Live panel base (LPB_BASE reference), WL_ sets: WL_E1 L6M 0.0 percent / -$416 per week, HOLD -14.5 / -$143; WL_A4 L6M +11.9 percent / +$423 (HOLD pending). So the evidence rule does not cut drawdown on the live base either, and it is not a drawdown fix.
C. Acceptance (session replay, fails over covered worst sessions): PASS for WG_E1, WL_E1, WL_E4, WL_E5, WL_E6, WG_E1L, WL_A4, WL_E2Q; FAIL for WL_E1A (Asia-only leaves the other sessions with 3rd-attempt losers) and WL_E7 (timer without evidence leaves 25 no-evidence re-entries, +$21.6k). The evidence rule is the only one that takes "3rd+ attempts without new evidence" to zero while keeping the mean.
D. Not yet: PRE and bi-weekly WF for all sets (chains continue: PRE then GAP then X'), WG_E1K / WG_E1M (K7 and M7 versions, queued behind), the rule-2a label. WG_E1 is offered to JN05 only as a defect-3 fix at zero cost, not as a drawdown earner; its WF and PRE rows are due before any label.

## Status sentences (P7 FIX first page; updated by hand each page)
0. P7 FIX, first read (20:00Z). The acceptance tool exists (acceptance_p7.py) and both live references FAIL it: LPB_BASE fails 3 of the 20 worst sessions and JN04RM fails 4 of 20 (the dials do not fix the repeated same-side entries: JN04RM still has 78 sessions with a run of 3 or more same-side losers and $99k lost on the 3rd-and-later losers; LPB_BASE 48 sessions and $136k). The first-order screen says the cleanest governor is the evidence rule itself: skip a 3rd same-side attempt that has no new session extreme and no opposite-side signal since the last failure (E1 all sessions: 101 trades removed over 3.5 years, saves $10.7k in the worst-20 weeks and $3.1k in the other weeks, so it removes losers in both and costs no mean: +$237/wk L6M, +$283 HOLD, -$122 PRE, maxDD cut 0 percent L6M, -15 percent HOLD, +9 percent PRE; first-order only, so not yet a result). It takes the scorecard item "3rd-and-later no-evidence losers" to zero by construction and removes 4 live-week trades that made +$15k (the frozen week stays strongly positive). Timer and chase rules (lgap < 90 min same side with chase_k > 0.75) show larger L6M mean (+$2.4k/wk) but cost the live week -$21k and HOLD. The exact sets WG_E1, E4, E5, E6, E2Q, E7, A4, E1A (JN04RM base, hook c_gov.py) are queued, L6M first; memory-gated, so results arrive after this page. D1/D3/D4/D6 screens (trend-alive clock, pullback number, extension, vote) in their tables below remove too many winners at every threshold tried (they are monotone mean-for-drawdown trades, not clean filters) and D5, D7, E-Q belong to the other agents.

00. EXACT L6M (22:50Z, JN04RM base, 6 months each): the new-evidence rule WG_E1 (skip a 3rd same-side attempt without new evidence) is NEUTRAL in L6M: maxDD cut 0.0 percent, +$20/wk, 13 sessions with a run of 3+ against 21 for JN04RM on the same months and $18.7k lost on 3rd+ losers against $31.2k; acceptance 2 fails of 15 covered worst sessions (JN04RM 4 of 15) = PASS by the tool, with zero 3rd+ attempts left without evidence (JN04RM: 57, +$12.8k). WG_E5 (2nd attempt half, 3rd without evidence skip): maxDD cut -3.0 percent, -$471/wk, 0 fails of 15 = PASS, but it halves winners too (best-session nets fall from +$23k to +$11k per Asia session). Neither has HOLD, PRE, X' or WF yet, so no label; read: the evidence gate is a free fix for scorecard item c (consecutive same-side losers: max 5 to 4 on the same months, 3rd+ losers -$31k to -$19k) and does not move drawdown; the loss-count/timer governors that move drawdown cost the frozen week. The scorecard items a, b, e (W-Q tool) are not on this pageyet. Memory: the exact queue is gated; 2 workers, about 12 min per cell-month before the throughput cache.




# C2 / C3 / C4 - exact runs (JN04RM = dials ON on the live panel; one set per job; every row is a candidate or reference as labelled; Shadow only)
Cut = maxDD cut vs the reference (positive = shallower), d$ = change in mean $/week, both over the window; noise floor for entry/blackout-type changes is about 8 percent maxDD and about 1,200 $/wk (R4 noise probes). Windows appear only when every month is exact-run.

### C3 blackout, JN04RM base (live = 30 min same side; no-blackout = JN04RM)
| set | months | vs | L1M cut % / d$ | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | L6M worst-20 cell/ref $k | bi-weekly WF beat % | rule-2a label |
|---|---|---|---|---|---|---|---|---|---|---|
| WC3_S15 | 6 | JN04RM | 14.7 / +541 | -1.9 / +180 | n/a | n/a | n/a | 145/138 | n/a | PRE not yet run |
| WC3_S15 | 6 | LPB | 55.0 / -5800 | 45.0 / -1616 | n/a | n/a | n/a | 145/102 | n/a |  |
| WC3_S30 | 27 | JN04RM | -5.6 / -61 | -5.2 / -473 | -5.9 / -441 | n/a | n/a | 139/138 | n/a | PRE not yet run |
| WC3_S30 | 27 | LPB | 44.3 / -6947 | 43.2 / -2396 | 2.3 / -2921 | n/a | n/a | 139/102 | n/a |  |
| WC3_S60 | 6 | JN04RM | 27.1 / -1235 | 12.6 / -450 | n/a | n/a | n/a | 164/138 | n/a | PRE not yet run |
| WC3_S60 | 6 | LPB | 61.5 / -1242 | 52.8 / -1257 | n/a | n/a | n/a | 164/102 | n/a |  |
| WC3_S120 | 6 | JN04RM | 67.3 / +2065 | -12.0 / -1000 | n/a | n/a | n/a | 123/138 | n/a | PRE not yet run |
| WC3_S120 | 6 | LPB | 82.8 / -4764 | 39.5 / -3672 | n/a | n/a | n/a | 123/102 | n/a |  |
| WC3_B30 | 6 | JN04RM | -25.8 / -826 | -25.5 / -1677 | n/a | n/a | n/a | 127/138 | n/a | PRE not yet run |
| WC3_B30 | 6 | LPB | 33.6 / -7712 | 32.2 / -10 | n/a | n/a | n/a | 127/102 | n/a |  |
| WC3_B60 | 6 | JN04RM | 28.5 / -964 | 5.5 / -2068 | n/a | n/a | n/a | 150/138 | n/a | PRE not yet run |
| WC3_B60 | 6 | LPB | 62.3 / +910 | 49.0 / -15 | n/a | n/a | n/a | 150/102 | n/a |  |
| WC3_H15S | 0 | not started | | | | | | | | |
| WC3_H30S | 6 | JN04RM | 16.1 / +322 | -3.7 / +106 | n/a | n/a | n/a | 146/138 | n/a | PRE not yet run |
| WC3_H30S | 6 | LPB | 55.7 / -6497 | 44.0 / -1993 | n/a | n/a | n/a | 146/102 | n/a |  |
| WC3_H60S | 6 | JN04RM | 27.2 / +377 | 4.1 / +1380 | n/a | n/a | n/a | 162/138 | n/a | PRE not yet run |
| WC3_H60S | 6 | LPB | 61.6 / -4662 | 48.2 / -999 | n/a | n/a | n/a | 162/102 | n/a |  |
| WC3_H30B | 6 | JN04RM | 19.1 / +388 | -3.7 / +96 | n/a | n/a | n/a | 145/138 | n/a | PRE not yet run |
| WC3_H30B | 6 | LPB | 57.3 / -6497 | 44.0 / -2035 | n/a | n/a | n/a | 145/102 | n/a |  |
| WC3_H30S_t11 | 0 | not started | | | | | | | | |
| WC3_H30S_t15 | 0 | not started | | | | | | | | |
| WC3_RS | 6 | JN04RM | 35.7 / -827 | -57.2 / -5186 | n/a | n/a | n/a | 20/138 | n/a | PRE not yet run |
| WC3_RS | 6 | LPB | 66.1 / -7713 | 15.1 / -8585 | n/a | n/a | n/a | 20/102 | n/a |  |
| WC3_RH | 6 | JN04RM | 35.7 / +528 | -1.6 / +731 | n/a | n/a | n/a | 128/138 | n/a | PRE not yet run |
| WC3_RH | 6 | LPB | 66.1 / -5735 | 45.1 / -2535 | n/a | n/a | n/a | 128/102 | n/a |  |

### C2 P7 Asia table and STACK on Asia, JN04RM base (reference 7/4/4)
| set | months | vs | L1M cut % / d$ | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | L6M worst-20 cell/ref $k | bi-weekly WF beat % | rule-2a label |
|---|---|---|---|---|---|---|---|---|---|---|
| WC2_A4 | 1 | JN04RM | 5.8 / +523 | n/a | n/a | n/a | n/a |  | n/a | PRE not yet run |
| WC2_A4 | 1 | LPB | 50.3 / -11064 | n/a | n/a | n/a | n/a |  | n/a |  |
| WC2_A5 | 6 | JN04RM | 19.1 / -1082 | -7.6 / -1609 | n/a | n/a | n/a | 122/138 | n/a | PRE not yet run |
| WC2_A5 | 6 | LPB | 57.3 / -7968 | 41.9 / -3921 | n/a | n/a | n/a | 122/102 | n/a |  |
| WC2_A6 | 0 | not started | | | | | | | | |
| WC2_L5 | 0 | not started | | | | | | | | |
| WC2_STKA | 0 | not started | | | | | | | | |

### C4 P7 45-s confirmation (live: three-bar 45 s, NY-AM/NY-PM), JN04RM base; WC4_REG proved identical to JN04RM
| set | months | vs | L1M cut % / d$ | L6M cut % / d$ | HOLD cut % / d$ | PRE cut % / d$ | X' cut % / d$ | L6M worst-20 cell/ref $k | bi-weekly WF beat % | rule-2a label |
|---|---|---|---|---|---|---|---|---|---|---|
| WC4_NONE | 0 | not started | | | | | | | | |
| WC4_T30 | 4 | JN04RM | 0.4 / +38 | n/a | n/a | n/a | n/a |  | n/a | PRE not yet run |
| WC4_T30 | 4 | LPB | 47.4 / -7716 | n/a | n/a | n/a | n/a |  | n/a |  |
| WC4_T60 | 0 | not started | | | | | | | | |
| WC4_HOT_LIVE | 6 | JN04RM | 0.0 / +0 | -1.8 / -152 | n/a | n/a | n/a | 135/138 | n/a | PRE not yet run |
| WC4_HOT_LIVE | 6 | LPB | 47.2 / -6886 | 45.0 / -1641 | n/a | n/a | n/a | 135/102 | n/a |  |
| WC4_HOT_ALL | 6 | JN04RM | 14.5 / -199 | -17.7 / -968 | n/a | n/a | n/a | 107/138 | n/a | PRE not yet run |
| WC4_HOT_ALL | 6 | LPB | 54.8 / -4943 | 36.4 / -3020 | n/a | n/a | n/a | 107/102 | n/a |  |
| WC4_CALM_LIVE | 6 | JN04RM | 0.7 / +24 | -11.7 / -1268 | n/a | n/a | n/a | 126/138 | n/a | PRE not yet run |
| WC4_CALM_LIVE | 6 | LPB | 47.6 / -6501 | 39.7 / -2361 | n/a | n/a | n/a | 126/102 | n/a |  |
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


## E. P7 fix (W-E) (E)

Source DS3_WORKS_E.md (mtime 2026-11-12T12:08:24Z UTC), included verbatim, read only:

# DS3_WORKS_E - T-WORKS / P7 FIX, W-E (families E multi-timeframe trend health, F participation, G pullback anatomy, H leg anatomy), page 2026-11-12 12:07Z
Label: PRE-PROOF, post-hoc, Shadow only, no PASS claim. Prereg autopilot/WORKS_E_PREREG.md (sha in DECISIONS.md 19:19Z, logged before any cell was scored). Code code/th_works_e/ (e0_flow, e1_table, e2_screen, e3_full, e_hooks, e_sets, e_chain, e_score, e_page).

## What exists
1. The shared P7 signal feature table is /mnt/l2/l2vast/_th_works/p7_signal_features.parquet: 6212 P7 signals 2023-04-03..2026-11-05, key utc_epoch_s, taken flag, session, side, base lots (live table 7/4/4), entry price, trade net if taken, shadow base-lot net, the week flags (worst-20 weeks of the 3.5-year P7 net, L6M worst-5, live week) and 64 causal feature columns of families E, F, G, H. Taken = 5011 (LPB_BASE trades plus the 53 frozen live-week trades). Untaken = 1201. CAVEAT: the untaken rows are S1B-COMB P7 signals that LPB_BASE does not contain; they include engine-divergence differences (different re-entry paths between the two engine runs), not only blocks by the day cap, the blackout or the lock, so taken=0 does not always mean the live panel refused the signal.
2. All features are computed from the 1-min bars (NQ, roll-adjusted) that closed at or before the signal second, plus 1-min flow bars (volume, aggressor delta, prints of 10 or more contracts) built from the state-base tick arrays. Legs and pullbacks come from a causal zigzag at 1.0 ATR(5-min) (pushes inside a leg at 0.4 ATR). Features at every P7-session minute boundary and both sides (1.9 million rows) are in /mnt/l2/l2vast/_th_works/e/full_*.parquet so the exact engine can look up the feature at any re-entry second; a signal that falls a few seconds after the bar boundary uses the last closed bar, identical to the shared table (checked: 6,211 of 6,212 rows match to 1e-6).

## First-order screen (P7 only, equal-mean drawdown cut, skip and half, P7 Asia then all sessions)
Each family has 312 cells per scope (feature x tail x percentile x action). Objective = mean of the equal-mean maxDD cut in L6M and HOLD on weekly P7 P&L; a cell must keep a positive mean in both windows. Family null = 300 within-month-and-session permutations of the feature rows with fixed thresholds, max objective over the family; forward-only placebo = the feature of the signal k positions earlier, k = 1..40, max over k.

| scope | family | best observed objective | null median / 95th / 99th (permutation) | forward-lag placebo 95th | verdict |
|---|---|---|---|---|---|
| ASIA | E | 28.3 | 34.1 / 49.0 / 53.9 | 46.4 | inside the null |
| ASIA | F | 20.3 | 28.3 / 44.6 / 51.2 | 42.5 | inside the null |
| ASIA | G | 30.8 | 26.3 / 41.7 / 46.1 | 40.9 | inside the null |
| ASIA | H | 36.1 | 27.5 / 42.1 / 47.4 | 44.7 | inside the null |
| ALL | E | 34.4 | 37.6 / 52.1 / 62.3 | 49.8 | inside the null |
| ALL | F | 28.8 | 31.0 / 47.9 / 55.0 | 49.9 | inside the null |
| ALL | G | 32.8 | 29.4 / 46.8 / 57.9 | 42.1 | inside the null |
| ALL | H | 36.7 | 31.6 / 49.8 / 57.2 | 46.6 | inside the null |

Plain reading: in every family and both scopes the best cell is at or below the 95th percentile of what random feature assignments give as their best cell (the median of the null maximum is 26-38, the best observed is 20-37). First-order, none of the E, F, G, H features is distinguishable from noise as a skip/half rule on P7. The cells below are therefore registered and sent to exact only because the order requires it, not because they passed a null.

## Registered top-3 per family and scope (first-order; cut = P7 weekly maxDD cut %, d = mean change per week $)
| id | rule (P7 signal second) | action | obj | cut L6M | cut HOLD | acted | total P&L effect 3.5y $ | removed net in worst-20 weeks (n) | removed net other weeks (n) | live week acted n / removed net |
|---|---|---|---|---|---|---|---|---|---|---|
| E1A | e_ac1_120 >= 0.133 (ASIA) | skip | 28.3 | 24.7 | 23.3 | 225 | 80529 | -101372 (47) | 20844 (178) | 4 / 7818 |
| E2A | e_sw15_dist <= -0.0915 (ASIA) | skip | 19.4 | 15.7 | 15.7 | 224 | 23284 | -57058 (28) | 33774 (196) | 2 / 3351 |
| E3A | e_sw60_dist >= 9.23 (ASIA) | skip | 18.9 | 22.9 | 21.0 | 447 | -100549 | -103717 (58) | 204266 (389) | 6 / -3116 |
| F1A | f_leg_vpm_rel >= 1.78 (ASIA) | skip | 20.3 | 20.8 | 20.8 | 225 | -38926 | -74419 (37) | 113346 (188) | 0 / 0 |
| F2A | f_leg_delta_share <= -0.0114 (ASIA) | skip | 15.4 | 13.1 | 13.1 | 225 | -70837 | -38828 (29) | 109665 (196) | 1 / -2424 |
| F3A | f_leg_vpm_rel >= 1.78 (ASIA) | half | 14.1 | 13.4 | 13.4 | 225 | -14174 | -32516 (37) | 46690 (188) | 0 / 0 |
| G1A | g_push_min <= 3 (ASIA) | skip | 30.8 | 24.5 | 24.5 | 228 | -26305 | -20928 (28) | 47233 (200) | 0 / 0 |
| G2A | g_pb_vel_over_push_vel <= 0.188 (ASIA) | skip | 19.5 | 19.6 | 12.7 | 449 | -68265 | -109486 (73) | 177751 (376) | 7 / 26676 |
| G3A | g_push_min <= 5 (ASIA) | half | 17.5 | 18.6 | 18.6 | 488 | -34174 | -25908 (64) | 60082 (424) | 4 / 3132 |
| H1A | h_leg_age <= 3 (ASIA) | skip | 36.1 | 32.3 | 32.3 | 246 | -56394 | -28825 (33) | 85219 (213) | 2 / 16722 |
| H2A | h_leg_slope_atr_min >= 0.449 (ASIA) | skip | 34.0 | 22.6 | 22.6 | 225 | 33719 | -43357 (27) | 9637 (198) | 0 / 0 |
| H3A | h_leg_atr <= 1.43 (ASIA) | skip | 31.9 | 40.9 | 40.9 | 674 | -193636 | -92570 (82) | 286206 (592) | 13 / 10245 |
| E1L | e_vwap_sl60 >= 1.16 (ALL) | skip | 34.4 | 38.3 | 38.3 | 1487 | -182128 | -252322 (156) | 434450 (1331) | 7 / 147 |
| E2L | e_vr5_60 <= 0.736 (ALL) | half | 33.4 | 36.1 | 36.1 | 1487 | -83802 | -106729 (160) | 190530 (1327) | 16 / -2450 |
| E3L | e_ac1_120 >= 0.128 (ALL) | skip | 31.7 | 23.4 | 21.6 | 496 | 116065 | -126819 (67) | 10754 (429) | 5 / 7704 |
| F1L | f_lastpush_delta_share <= 0.0442 (ALL) | skip | 28.8 | 35.5 | 34.9 | 1487 | -170933 | -206689 (168) | 377622 (1319) | 16 / 16311 |
| F2L | f_lastpush_delta_share <= 0.0442 (ALL) | half | 22.2 | 22.7 | 22.7 | 1487 | -8577 | -101863 (168) | 110440 (1319) | 16 / 6550 |
| F3L | f_leg_delta_agree <= 0 (ALL) | skip | 22.2 | 23.4 | 23.4 | 629 | -140519 | -69999 (62) | 210519 (567) | 7 / -4766 |
| G1L | g_push_min <= 4 (ALL) | skip | 32.8 | 35.9 | 33.5 | 1012 | -144554 | -80650 (103) | 225204 (909) | 7 / 12160 |
| G2L | g_push_min <= 4 (ALL) | half | 22.6 | 20.5 | 20.5 | 1012 | -18374 | -35450 (103) | 53824 (909) | 7 / 4288 |
| G3L | g_pb_vel_over_push_vel <= 0.206 (ALL) | skip | 22.1 | 22.0 | 22.0 | 992 | -21184 | -169506 (123) | 190690 (869) | 9 / 22097 |
| H1L | h_leg_pts >= 59 (ALL) | skip | 36.7 | 52.7 | 7.5 | 1490 | -25251 | -166435 (185) | 191686 (1305) | 38 / 83230 |
| H2L | h_leg_push_min <= 4 (ALL) | skip | 32.8 | 35.9 | 33.5 | 1012 | -144554 | -80650 (103) | 225204 (909) | 7 / 12160 |
| H3L | h_leg_pts >= 59 (ALL) | half | 31.4 | 21.9 | 21.9 | 1490 | 36316 | -79032 (185) | 42715 (1305) | 38 / 36281 |

Negative removed net = the rule removes losses (good); positive = removes profit. Total P&L effect = minus the sum removed over the 3.5 years (positive = the rule added P&L before any lot reallocation). The sign of the effect is mixed across cells and none survives its family null; the large-leg cell H1L (leg >= 59 pts, skip) cuts L6M drawdown by 53% but removes $83k of the frozen live week (the trend week).

## Which flag separates the frozen trend week from the worst weeks (taken P7, mean of the signed feature)
| feature | live week mean | worst-20 weeks mean | other weeks mean | live minus worst, in SD |
|---|---|---|---|---|
| h_leg_pts | 105.717 | 60.337 | 51.855 | 0.99 |
| g_pb_vol_share | 0.233 | 0.314 | 0.306 | -0.45 |
| g_aligned | 0.811 | 0.595 | 0.632 | 0.45 |
| g_pb_vel_over_push_vel | 1.183 | 0.741 | 0.838 | 0.44 |
| e_sw60_run | 0.792 | 1.321 | 1.014 | -0.38 |
| g_pb_depth_atr | 0.818 | 1.056 | 1.035 | -0.35 |
| e_sw15_run | 1.642 | 1.197 | 1.248 | 0.30 |
| e_sw60_dist | 1.003 | 3.397 | 3.385 | -0.29 |
| g_depth_max | 0.420 | 0.501 | 0.508 | -0.28 |
| h_leg_slope_atr_min | 0.190 | 0.246 | 0.248 | -0.27 |

(One live week against twenty bad weeks is one observation; this table says what differed, not what is predictive.)

## Exact promotion status
| set | ref | window | exact cut % | d mean/week | eq cut % |
|---|---|---|---|---|---|
| WEJ_E1A | JN04RM | L1M | 42.8 | 3859 | 47.6 |
| WEJ_E1A | JN04RM | L3M | 16.1 | 2096 | 23.2 |
| WEJ_E1A | JN04RM | L6M | 16.1 | 1615 | 23.2 |
| WEJ_E1A | LPB | L1M | 69.8 | -11941 | 68.2 |
| WEJ_E1A | LPB | L3M | 54.7 | -2334 | 52.3 |
| WEJ_E1A | LPB | L6M | 54.7 | -1087 | 52.3 |
| WEL_E1A | JN04RM | L1M | -36.2 | -307 | -34.9 |
| WEL_E1A | JN04RM | L3M | -35.8 | 1596 | -34.5 |
| WEL_E1A | JN04RM | L6M | -35.8 | 166 | -34.5 |
| WEL_E1A | LPB | L1M | 28.1 | 6854 | 23.4 |
| WEL_E1A | LPB | L3M | 26.7 | 2906 | 21.9 |
| WEL_E1A | LPB | L6M | 26.7 | -1151 | 21.9 |
| WEJ_E2A | JN04RM | L1M | 27.5 | 1066 | 26.8 |
| WEJ_E2A | JN04RM | L3M | -14.5 | -259 | -15.4 |
| WEJ_E2A | JN04RM | L6M | -14.5 | -149 | -15.4 |
| WEJ_E2A | LPB | L1M | 61.7 | -5820 | 60.1 |
| WEJ_E2A | LPB | L3M | 38.2 | -527 | 35.6 |
| WEJ_E2A | LPB | L6M | 38.2 | -854 | 35.6 |
| WEL_E2A | JN04RM | L1M | -54.5 | -3921 | -58.8 |
| WEL_E2A | JN04RM | L3M | -113.1 | -812 | -119.0 |
| WEL_E2A | JN04RM | L6M | -113.1 | -481 | -119.0 |
| WEL_E2A | LPB | L1M | 18.4 | 3241 | 17.7 |
| WEL_E2A | LPB | L3M | -15.1 | 1071 | -16.1 |
| WEL_E2A | LPB | L6M | -15.1 | -153 | -16.1 |
| WEJ_E3A | JN04RM | L1M | -0.6 | -58 | 2.9 |
| WEJ_E3A | JN04RM | L3M | 6.2 | 1580 | 9.6 |
| WEJ_E3A | JN04RM | L6M | 6.2 | 620 | 9.6 |
| WEJ_E3A | LPB | L1M | 46.9 | -6606 | 40.9 |
| WEJ_E3A | LPB | L3M | 49.4 | -409 | 43.7 |
| WEJ_E3A | LPB | L6M | 49.4 | -2162 | 43.7 |
| WEL_E3A | JN04RM | L1M | -38.8 | 5658 | -26.9 |
| WEL_E3A | JN04RM | L3M | -58.2 | 4460 | -44.6 |
| WEL_E3A | JN04RM | L6M | -58.2 | 1634 | -44.6 |
| WEL_E3A | LPB | L1M | 26.7 | -1228 | 31.7 |
| WEL_E3A | LPB | L3M | 14.6 | 1920 | 20.4 |
| WEL_E3A | LPB | L6M | 14.6 | 1248 | 20.4 |
| WEJ_F1A | JN04RM | L1M | -0.9 | -78 | -6.3 |
| WEJ_F1A | JN04RM | L3M | 7.6 | -1329 | 2.6 |
| WEJ_F1A | JN04RM | L6M | 3.8 | -1019 | -1.4 |
| WEJ_F1A | LPB | L1M | 46.8 | -8271 | 40.8 |
| WEJ_F1A | LPB | L3M | 50.1 | -2531 | 44.5 |
| WEJ_F1A | LPB | L6M | 48.0 | -2172 | 42.2 |
| WEL_F1A | JN04RM | L1M | -55.2 | 5139 | -48.8 |
| WEL_F1A | JN04RM | L3M | -78.2 | 2205 | -70.8 |
| WEL_F1A | JN04RM | L6M | -78.2 | 750 | -70.8 |
| WEL_F1A | LPB | L1M | 18.1 | -1747 | 18.6 |
| WEL_F1A | LPB | L3M | 3.8 | -206 | 4.4 |
| WEL_F1A | LPB | L6M | 3.8 | 106 | 4.4 |
| WEJ_F2A | JN04RM | L1M | -5.8 | -374 | -10.8 |
| WEJ_F2A | JN04RM | L3M | 8.2 | -1641 | 3.9 |
| WEJ_F2A | JN04RM | L6M | -3.2 | -881 | -8.0 |
| WEJ_F2A | LPB | L1M | 44.1 | -8403 | 38.5 |
| WEJ_F2A | LPB | L3M | 50.4 | -2728 | 45.4 |
| WEJ_F2A | LPB | L6M | 44.3 | -1979 | 38.6 |
| WEL_F2A | JN04RM | L1M | -89.1 | 7472 | -64.9 |
| WEL_F2A | JN04RM | L3M | -50.4 | 3775 | -31.2 |
| WEL_F2A | JN04RM | L6M | -50.4 | 2920 | -31.2 |
| WEL_F2A | LPB | L1M | 0.2 | 87 | 3.6 |
| WEL_F2A | LPB | L3M | 18.8 | 388 | 21.5 |
| WEL_F2A | LPB | L6M | 18.8 | 718 | 21.5 |
| WEJ_F3A | JN04RM | L1M | -0.3 | -30 | -0.3 |
| WEJ_F3A | JN04RM | L3M | 13.2 | -361 | 13.2 |
| WEJ_F3A | JN04RM | L6M | 9.3 | 4 | 9.4 |
| WEJ_F3A | LPB | L1M | 47.0 | -8311 | 42.1 |
| WEJ_F3A | LPB | L3M | 53.1 | -2168 | 48.7 |
| WEJ_F3A | LPB | L6M | 51.0 | -1833 | 46.5 |
| WEL_F3A | JN04RM | L1M | -47.7 | 10313 | -29.8 |
| WEL_F3A | JN04RM | L3M | -77.0 | 3708 | -55.5 |
| WEL_F3A | JN04RM | L6M | -77.0 | 2403 | -55.5 |
| WEL_F3A | LPB | L1M | 22.0 | 3427 | 29.7 |
| WEL_F3A | LPB | L3M | 4.4 | 1506 | 13.9 |
| WEL_F3A | LPB | L6M | 4.4 | 1808 | 13.9 |
| WEJ_G1A | JN04RM | L1M | -9.1 | -825 | -18.8 |
| WEJ_G1A | JN04RM | L3M | 29.2 | -1130 | 22.9 |
| WEJ_G1A | JN04RM | L6M | 8.7 | -1613 | 0.6 |
| WEJ_G1A | LPB | L1M | 42.4 | -9272 | 34.2 |
| WEJ_G1A | LPB | L3M | 61.8 | -2154 | 56.3 |
| WEJ_G1A | LPB | L6M | 50.7 | -2681 | 43.7 |
| WEL_G1A | JN04RM | L1M | -51.2 | 6962 | -29.3 |
| WEL_G1A | JN04RM | L3M | -39.7 | 3913 | -19.5 |
| WEL_G1A | JN04RM | L6M | -39.7 | 3367 | -19.5 |
| WEL_G1A | LPB | L1M | 20.2 | 77 | 22.8 |
| WEL_G1A | LPB | L3M | 24.5 | 1390 | 27.0 |
| WEL_G1A | LPB | L6M | 24.5 | 626 | 27.0 |
| WEJ_G2A | JN04RM | L1M | 21.4 | 1928 | 16.7 |
| WEJ_G2A | JN04RM | L3M | 11.2 | -519 | 5.9 |
| WEJ_G2A | JN04RM | L6M | -5.2 | -1120 | -11.5 |
| WEJ_G2A | LPB | L1M | 58.5 | -4831 | 53.6 |
| WEJ_G2A | LPB | L3M | 52.1 | -1742 | 46.4 |
| WEJ_G2A | LPB | L6M | 43.2 | -2283 | 36.5 |
| WEL_G2A | JN04RM | L1M | -57.4 | 8760 | -53.2 |
| WEL_G2A | JN04RM | L3M | -80.5 | -2254 | -75.6 |
| WEL_G2A | JN04RM | L6M | -80.5 | 492 | -75.6 |
| WEL_G2A | LPB | L1M | 16.9 | 1875 | 18.1 |
| WEL_G2A | LPB | L3M | 2.6 | -712 | 3.9 |
| WEL_G2A | LPB | L6M | 2.6 | 277 | 3.9 |
| WEJ_G3A | JN04RM | L1M | 12.4 | 1117 | 9.9 |
| WEJ_G3A | JN04RM | L3M | 16.8 | 172 | 14.4 |
| WEJ_G3A | JN04RM | L6M | 10.3 | -489 | 7.7 |
| WEJ_G3A | LPB | L1M | 53.8 | -9337 | 47.5 |
| WEJ_G3A | LPB | L3M | 55.1 | -2922 | 49.0 |
| WEJ_G3A | LPB | L6M | 51.5 | -2550 | 45.0 |
| WEL_G3A | JN04RM | L1M | -47.5 | 9030 | -26.0 |
| WEL_G3A | JN04RM | L3M | -47.8 | 3997 | -26.3 |
| WEL_G3A | JN04RM | L6M | -47.8 | 3386 | -26.3 |
| WEL_G3A | LPB | L1M | 22.1 | 2144 | 24.6 |
| WEL_G3A | LPB | L3M | 20.2 | 1641 | 22.7 |
| WEL_G3A | LPB | L6M | 20.2 | 608 | 22.7 |
| WEJ_H1A | JN04RM | L1M | -3.5 | -314 | -10.2 |
| WEJ_H1A | JN04RM | L3M | 18.2 | -731 | 12.9 |
| WEJ_H1A | JN04RM | L6M | 8.7 | -1069 | 2.8 |
| WEJ_H1A | LPB | L1M | 45.4 | -12066 | 35.5 |
| WEJ_H1A | LPB | L3M | 55.8 | -4150 | 47.9 |
| WEJ_H1A | LPB | L6M | 50.7 | -3286 | 41.8 |
| WEL_H1A | JN04RM | L1M | -48.7 | 5751 | -38.1 |
| WEL_H1A | JN04RM | L3M | -62.1 | 2006 | -50.6 |
| WEL_H1A | JN04RM | L6M | -62.1 | 1519 | -50.6 |
| WEL_H1A | LPB | L1M | 21.5 | -1135 | 16.8 |
| WEL_H1A | LPB | L3M | 12.5 | -196 | 7.2 |
| WEL_H1A | LPB | L6M | 12.5 | -1052 | 7.2 |
| WEJ_H2A | JN04RM | L1M | 0.2 | 18 | -1.8 |
| WEJ_H2A | JN04RM | L3M | 33.0 | -3 | 31.6 |
| WEJ_H2A | JN04RM | L6M | 8.7 | -381 | 6.9 |
| WEJ_H2A | LPB | L1M | 47.3 | -9222 | 43.8 |
| WEJ_H2A | LPB | L3M | 63.8 | -819 | 61.4 |
| WEJ_H2A | LPB | L6M | 50.7 | -1349 | 47.4 |
| WEL_H2A | JN04RM | L1M | -59.8 | 3696 | -34.8 |
| WEL_H2A | JN04RM | L3M | -46.2 | 4284 | -23.3 |
| WEL_H2A | JN04RM | L6M | -46.2 | 3696 | -23.3 |
| WEL_H2A | LPB | L1M | 15.6 | 2670 | 18.8 |
| WEL_H2A | LPB | L3M | 21.1 | 1360 | 24.0 |
| WEL_H2A | LPB | L6M | 21.1 | 717 | 24.0 |
| WEJ_H3A | JN04RM | L1M | 21.0 | 1898 | 13.9 |
| WEJ_H3A | JN04RM | L3M | -11.1 | 1458 | -21.0 |
| WEJ_H3A | JN04RM | L6M | -11.1 | -1505 | -21.0 |
| WEJ_H3A | LPB | L1M | 58.3 | -8425 | 49.1 |
| WEJ_H3A | LPB | L3M | 40.0 | -1792 | 26.7 |
| WEJ_H3A | LPB | L6M | 40.0 | -3909 | 26.7 |
| WEL_H3A | JN04RM | L1M | -53.1 | 9130 | -36.2 |
| WEL_H3A | JN04RM | L3M | -144.9 | 4261 | -117.9 |
| WEL_H3A | JN04RM | L6M | -144.9 | 2376 | -117.9 |
| WEL_H3A | LPB | L1M | 19.2 | 2244 | 15.0 |
| WEL_H3A | LPB | L3M | -32.2 | 4170 | -39.1 |
| WEL_H3A | LPB | L6M | -32.2 | -927 | -39.1 |
| WEJ_E1L | JN04RM | L1M | 42.5 | -238 | 37.2 |
| WEJ_E1L | JN04RM | L3M | 1.5 | 684 | -7.6 |
| WEJ_E1L | JN04RM | L6M | 1.5 | -1571 | -7.6 |
| WEJ_E1L | LPB | L1M | 69.6 | -7124 | 61.7 |
| WEJ_E1L | LPB | L3M | 46.8 | -3533 | 32.9 |
| WEJ_E1L | LPB | L6M | 46.8 | -4468 | 32.9 |
| WEL_E1L | JN04RM | L1M | -21.3 | 3966 | -1.3 |
| WEL_E1L | JN04RM | L3M | -40.4 | 1507 | -17.2 |
| WEL_E1L | JN04RM | L6M | -40.4 | 3533 | -17.2 |
| WEL_E1L | LPB | L1M | 36.0 | -2920 | 46.1 |
| WEL_E1L | LPB | L3M | 24.2 | -1249 | 36.2 |
| WEL_E1L | LPB | L6M | 24.2 | 3505 | 36.2 |

Exact sets: 23 registered cells (H2L duplicates G1L) x 2 references = 46 sets (WEJ_* on JN04RM, WEL_* on LPB_EMPTY), one set per job through state_sizer_ijk jbjobs with the e_hooks signal-second lookup applied in trend_size before the JN04 dials. Months DONE so far: 156. Chain scheduler (restart-safe, launches when MemAvailable >= 62 GB, at most 3 W-E jobs, runs until 2026-11-12 12:00Z): pids 2998742; W-E jobs running now 0; log /mnt/l2/l2vast/_th_works/e/logs/chain.log. A set continues past L6M only if its exact L6M cut is positive (e_gate.csv).

## Behavioural scorecard (standing principle 2026-11-11 19:45Z)
A cell counts only if full stops, give-backs and same-side repeats each fall by at least half in L6M without skipping trend-week winners. On first-order numbers H1L fails the trend-week test (it removes $83k of the frozen live week) and most other registered cells act on live-week trades; the registered E-H cells carry no stop, give-back or repeat logic of their own (they are entry filters), so the scorecard is expected to show little change in full stops and give-backs. W-Q tool code/th_works_q/behavior_scorecard.py is run per promoted set once its L6M is complete; output below.
### WEJ_E1A
```
WEJ_E1A L6M (stack, per week): full stops 25.4/wk $-38085; give-backs 10.0/wk (9.8 round-trips) realised $-11406, forgone vs target $28215; same-side losing runs max 13, p95 6, $-42040 lost on 3rd-and-later; no-new-evidence re-entries 42.6/wk $2165; recoveries cut 14.9/wk $38698, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $9077/wk, losers avoided $10648/wk, net +634 $/wk; pnl $20418/wk.
WEJ_E1A HOLD: months missing (6 of 12), window not scored
WEJ_E1A PRE: months missing (17 of 17), window not scored
WEJ_E1A X': months missing (10 of 10), window not scored

```
### WEL_E1A
```
WEL_E1A L6M (stack, per week): full stops 24.5/wk $-40052; give-backs 9.2/wk (9.1 round-trips) realised $-14152, forgone vs target $35325; same-side losing runs max 12, p95 6, $-51441 lost on 3rd-and-later; no-new-evidence re-entries 37.8/wk $396; recoveries cut 13.8/wk $47391, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $6099/wk, losers avoided $6833/wk, net +1193 $/wk; pnl $20976/wk.
WEL_E1A HOLD: months missing (6 of 12), window not scored
WEL_E1A PRE: months missing (17 of 17), window not scored
WEL_E1A X': months missing (10 of 10), window not scored

```
### WEJ_E2A
```
WEJ_E2A L6M (stack, per week): full stops 25.5/wk $-38226; give-backs 10.0/wk (9.9 round-trips) realised $-11238, forgone vs target $28121; same-side losing runs max 13, p95 7, $-42357 lost on 3rd-and-later; no-new-evidence re-entries 42.8/wk $1559; recoveries cut 15.0/wk $39045, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $9176/wk, losers avoided $10612/wk, net +708 $/wk; pnl $20492/wk.
WEJ_E2A HOLD: months missing (6 of 12), window not scored
WEJ_E2A PRE: months missing (17 of 17), window not scored
WEJ_E2A X': months missing (10 of 10), window not scored

```
### WEL_E2A
```
WEL_E2A L6M (stack, per week): full stops 24.5/wk $-39856; give-backs 9.2/wk (9.1 round-trips) realised $-13691, forgone vs target $34912; same-side losing runs max 9, p95 6, $-50983 lost on 3rd-and-later; no-new-evidence re-entries 37.6/wk $178; recoveries cut 13.7/wk $46237, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $6930/wk, losers avoided $8218/wk, net +959 $/wk; pnl $20742/wk.
WEL_E2A HOLD: months missing (6 of 12), window not scored
WEL_E2A PRE: months missing (17 of 17), window not scored
WEL_E2A X': months missing (10 of 10), window not scored

```
### WEJ_E3A
```
WEJ_E3A L6M (stack, per week): full stops 25.2/wk $-37793; give-backs 9.7/wk (9.6 round-trips) realised $-11017, forgone vs target $27083; same-side losing runs max 13, p95 6, $-41690 lost on 3rd-and-later; no-new-evidence re-entries 42.4/wk $1608; recoveries cut 14.8/wk $38138, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $10878/wk, losers avoided $11122/wk, net -603 $/wk; pnl $19181/wk.
WEJ_E3A HOLD: months missing (6 of 12), window not scored
WEJ_E3A PRE: months missing (17 of 17), window not scored
WEJ_E3A X': months missing (10 of 10), window not scored

```
### WEL_E3A
```
WEL_E3A L6M (stack, per week): full stops 24.5/wk $-39856; give-backs 9.0/wk (9.0 round-trips) realised $-13635, forgone vs target $34347; same-side losing runs max 12, p95 6, $-49839 lost on 3rd-and-later; no-new-evidence re-entries 37.1/wk $-67; recoveries cut 13.6/wk $45615, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $7851/wk, losers avoided $7387/wk, net -0 $/wk; pnl $19784/wk.
WEL_E3A HOLD: months missing (6 of 12), window not scored
WEL_E3A PRE: months missing (17 of 17), window not scored
WEL_E3A X': months missing (10 of 10), window not scored

```
### WEJ_F1A
```
WEJ_F1A L6M (stack, per week): full stops 25.4/wk $-38262; give-backs 9.9/wk (9.8 round-trips) realised $-11168, forgone vs target $27758; same-side losing runs max 13, p95 7, $-42769 lost on 3rd-and-later; no-new-evidence re-entries 42.8/wk $1699; recoveries cut 15.0/wk $38098, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $10020/wk, losers avoided $10046/wk, net -811 $/wk; pnl $18972/wk.
WEJ_F1A HOLD: months missing (6 of 12), window not scored
WEJ_F1A PRE: months missing (17 of 17), window not scored
WEJ_F1A X': months missing (10 of 10), window not scored

```
### WEL_F1A
```
WEL_F1A L6M (stack, per week): full stops 24.5/wk $-40004; give-backs 9.0/wk (8.9 round-trips) realised $-13769, forgone vs target $34768; same-side losing runs max 12, p95 6, $-50663 lost on 3rd-and-later; no-new-evidence re-entries 37.1/wk $-774; recoveries cut 13.5/wk $44847, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $8154/wk, losers avoided $7949/wk, net -655 $/wk; pnl $19129/wk.
WEL_F1A HOLD: months missing (6 of 12), window not scored
WEL_F1A PRE: months missing (17 of 17), window not scored
WEL_F1A X': months missing (10 of 10), window not scored

```
### WEJ_F2A
```
WEJ_F2A L6M (stack, per week): full stops 25.4/wk $-38130; give-backs 9.9/wk (9.8 round-trips) realised $-11237, forgone vs target $28008; same-side losing runs max 13, p95 7, $-43101 lost on 3rd-and-later; no-new-evidence re-entries 43.1/wk $2624; recoveries cut 15.1/wk $39640, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $9192/wk, losers avoided $8512/wk, net -568 $/wk; pnl $19216/wk.
WEJ_F2A HOLD: months missing (6 of 12), window not scored
WEJ_F2A PRE: months missing (17 of 17), window not scored
WEJ_F2A X': months missing (10 of 10), window not scored

```
### WEL_F2A
```
WEL_F2A L6M (stack, per week): full stops 24.5/wk $-39856; give-backs 9.1/wk (9.0 round-trips) realised $-13911, forgone vs target $35181; same-side losing runs max 12, p95 6, $-51490 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $745; recoveries cut 13.8/wk $47098, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4945/wk, losers avoided $4975/wk, net +1313 $/wk; pnl $21097/wk.
WEL_F2A HOLD: months missing (6 of 12), window not scored
WEL_F2A PRE: months missing (17 of 17), window not scored
WEL_F2A X': months missing (10 of 10), window not scored

```
### WEJ_F3A
```
WEJ_F3A L6M (stack, per week): full stops 25.4/wk $-38131; give-backs 9.9/wk (9.8 round-trips) realised $-11165, forgone vs target $27755; same-side losing runs max 13, p95 7, $-42550 lost on 3rd-and-later; no-new-evidence re-entries 43.4/wk $1789; recoveries cut 15.2/wk $38754, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3856/wk, losers avoided $4296/wk, net -461 $/wk; pnl $19323/wk.
WEJ_F3A HOLD: months missing (6 of 12), window not scored
WEJ_F3A PRE: months missing (17 of 17), window not scored
WEJ_F3A X': months missing (10 of 10), window not scored

```
### WEL_F3A
```
WEL_F3A L6M (stack, per week): full stops 24.5/wk $-40004; give-backs 9.0/wk (8.9 round-trips) realised $-13692, forgone vs target $34446; same-side losing runs max 12, p95 6, $-50955 lost on 3rd-and-later; no-new-evidence re-entries 37.5/wk $116; recoveries cut 13.8/wk $46094, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1171/wk, losers avoided $1391/wk, net +1076 $/wk; pnl $20860/wk.
WEL_F3A HOLD: months missing (6 of 12), window not scored
WEL_F3A PRE: months missing (17 of 17), window not scored
WEL_F3A X': months missing (10 of 10), window not scored

```
### WEJ_G1A
```
WEJ_G1A L6M (stack, per week): full stops 25.5/wk $-38456; give-backs 9.8/wk (9.7 round-trips) realised $-11102, forgone vs target $27594; same-side losing runs max 13, p95 6, $-42449 lost on 3rd-and-later; no-new-evidence re-entries 42.8/wk $2079; recoveries cut 14.9/wk $39002, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $11044/wk, losers avoided $12428/wk, net -1317 $/wk; pnl $18467/wk.
WEJ_G1A HOLD: months missing (6 of 12), window not scored
WEJ_G1A PRE: months missing (17 of 17), window not scored
WEJ_G1A X': months missing (10 of 10), window not scored

```
### WEL_G1A
```
WEL_G1A L6M (stack, per week): full stops 24.5/wk $-40221; give-backs 9.1/wk (9.0 round-trips) realised $-13909, forgone vs target $35345; same-side losing runs max 12, p95 6, $-50905 lost on 3rd-and-later; no-new-evidence re-entries 37.2/wk $1601; recoveries cut 13.6/wk $44334, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $9861/wk, losers avoided $10984/wk, net +2186 $/wk; pnl $21970/wk.
WEL_G1A HOLD: months missing (6 of 12), window not scored
WEL_G1A PRE: months missing (17 of 17), window not scored
WEL_G1A X': months missing (10 of 10), window not scored

```
### WEJ_G2A
```
WEJ_G2A L6M (stack, per week): full stops 25.4/wk $-38096; give-backs 10.0/wk (9.9 round-trips) realised $-11618, forgone vs target $29135; same-side losing runs max 13, p95 6, $-42427 lost on 3rd-and-later; no-new-evidence re-entries 42.4/wk $2231; recoveries cut 14.9/wk $39440, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $14509/wk, losers avoided $14301/wk, net -804 $/wk; pnl $18980/wk.
WEJ_G2A HOLD: months missing (6 of 12), window not scored
WEJ_G2A PRE: months missing (17 of 17), window not scored
WEJ_G2A X': months missing (10 of 10), window not scored

```
### WEL_G2A
```
WEL_G2A L6M (stack, per week): full stops 24.6/wk $-40265; give-backs 9.1/wk (9.0 round-trips) realised $-14108, forgone vs target $35302; same-side losing runs max 9, p95 6, $-51957 lost on 3rd-and-later; no-new-evidence re-entries 37.7/wk $1194; recoveries cut 13.7/wk $46971, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $11482/wk, losers avoided $12574/wk, net +1430 $/wk; pnl $21214/wk.
WEL_G2A HOLD: months missing (6 of 12), window not scored
WEL_G2A PRE: months missing (17 of 17), window not scored
WEL_G2A X': months missing (10 of 10), window not scored

```
### WEJ_G3A
```
WEJ_G3A L6M (stack, per week): full stops 25.4/wk $-38180; give-backs 10.0/wk (9.8 round-trips) realised $-10880, forgone vs target $27031; same-side losing runs max 13, p95 7, $-42509 lost on 3rd-and-later; no-new-evidence re-entries 43.8/wk $1386; recoveries cut 15.3/wk $38259, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3759/wk, losers avoided $4276/wk, net -1190 $/wk; pnl $18594/wk.
WEJ_G3A HOLD: months missing (6 of 12), window not scored
WEJ_G3A PRE: months missing (17 of 17), window not scored
WEJ_G3A X': months missing (10 of 10), window not scored

```
### WEL_G3A
```
WEL_G3A L6M (stack, per week): full stops 24.5/wk $-40004; give-backs 9.3/wk (9.2 round-trips) realised $-14374, forgone vs target $35985; same-side losing runs max 10, p95 6, $-51434 lost on 3rd-and-later; no-new-evidence re-entries 39.0/wk $1257; recoveries cut 14.3/wk $47612, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $1756/wk, losers avoided $875/wk, net +2245 $/wk; pnl $22029/wk.
WEL_G3A HOLD: months missing (6 of 12), window not scored
WEL_G3A PRE: months missing (17 of 17), window not scored
WEL_G3A X': months missing (10 of 10), window not scored

```
### WEJ_H1A
```
WEJ_H1A L6M (stack, per week): full stops 25.4/wk $-38175; give-backs 9.8/wk (9.7 round-trips) realised $-11161, forgone vs target $27702; same-side losing runs max 13, p95 6, $-42336 lost on 3rd-and-later; no-new-evidence re-entries 42.7/wk $2231; recoveries cut 15.0/wk $39584, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $11953/wk, losers avoided $13141/wk, net -1906 $/wk; pnl $17878/wk.
WEJ_H1A HOLD: months missing (6 of 12), window not scored
WEJ_H1A PRE: months missing (17 of 17), window not scored
WEJ_H1A X': months missing (10 of 10), window not scored

```
### WEL_H1A
```
WEL_H1A L6M (stack, per week): full stops 24.5/wk $-40004; give-backs 9.3/wk (9.2 round-trips) realised $-14575, forgone vs target $36864; same-side losing runs max 10, p95 6, $-52567 lost on 3rd-and-later; no-new-evidence re-entries 38.1/wk $2082; recoveries cut 14.0/wk $47211, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $10721/wk, losers avoided $11143/wk, net +333 $/wk; pnl $20117/wk.
WEL_H1A HOLD: months missing (6 of 12), window not scored
WEL_H1A PRE: months missing (17 of 17), window not scored
WEL_H1A X': months missing (10 of 10), window not scored

```
### WEJ_H2A
```
WEJ_H2A L6M (stack, per week): full stops 25.5/wk $-38412; give-backs 9.9/wk (9.8 round-trips) realised $-11248, forgone vs target $27886; same-side losing runs max 13, p95 6, $-42558 lost on 3rd-and-later; no-new-evidence re-entries 42.7/wk $2016; recoveries cut 14.9/wk $38045, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $10314/wk, losers avoided $12442/wk, net +37 $/wk; pnl $19821/wk.
WEJ_H2A HOLD: months missing (6 of 12), window not scored
WEJ_H2A PRE: months missing (17 of 17), window not scored
WEJ_H2A X': months missing (10 of 10), window not scored

```
### WEL_H2A
```
WEL_H2A L6M (stack, per week): full stops 24.5/wk $-40221; give-backs 9.1/wk (9.0 round-trips) realised $-14198, forgone vs target $35955; same-side losing runs max 12, p95 6, $-51066 lost on 3rd-and-later; no-new-evidence re-entries 37.6/wk $694; recoveries cut 13.6/wk $44193, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $9287/wk, losers avoided $9919/wk, net +2425 $/wk; pnl $22209/wk.
WEL_H2A HOLD: months missing (6 of 12), window not scored
WEL_H2A PRE: months missing (17 of 17), window not scored
WEL_H2A X': months missing (10 of 10), window not scored

```
### WEJ_H3A
```
WEJ_H3A L6M (stack, per week): full stops 25.5/wk $-38240; give-backs 9.9/wk (9.8 round-trips) realised $-11496, forgone vs target $28705; same-side losing runs max 13, p95 7, $-42472 lost on 3rd-and-later; no-new-evidence re-entries 42.5/wk $768; recoveries cut 14.8/wk $38470, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $20698/wk, losers avoided $18511/wk, net -2520 $/wk; pnl $17264/wk.
WEJ_H3A HOLD: months missing (6 of 12), window not scored
WEJ_H3A PRE: months missing (17 of 17), window not scored
WEJ_H3A X': months missing (10 of 10), window not scored

```
### WEL_H3A
```
WEL_H3A L6M (stack, per week): full stops 24.5/wk $-40254; give-backs 9.3/wk (9.2 round-trips) realised $-14351, forgone vs target $36045; same-side losing runs max 10, p95 6, $-51937 lost on 3rd-and-later; no-new-evidence re-entries 37.8/wk $381; recoveries cut 13.6/wk $45018, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $20643/wk, losers avoided $17802/wk, net +477 $/wk; pnl $20261/wk.
WEL_H3A HOLD: months missing (6 of 12), window not scored
WEL_H3A PRE: months missing (17 of 17), window not scored
WEL_H3A X': months missing (10 of 10), window not scored

```
### WEJ_E1L
```
WEJ_E1L L6M (stack, per week): full stops 25.4/wk $-38229; give-backs 9.5/wk (9.4 round-trips) realised $-10818, forgone vs target $26920; same-side losing runs max 13, p95 6, $-40488 lost on 3rd-and-later; no-new-evidence re-entries 40.9/wk $1417; recoveries cut 14.4/wk $36228, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $22285/wk, losers avoided $22098/wk, net -2780 $/wk; pnl $17003/wk.
WEJ_E1L HOLD: months missing (6 of 12), window not scored
WEJ_E1L PRE: months missing (17 of 17), window not scored
WEJ_E1L X': months missing (10 of 10), window not scored

```
### WEL_E1L
```
WEL_E1L L6M (stack, per week): full stops 24.5/wk $-39966; give-backs 9.0/wk (8.9 round-trips) realised $-13203, forgone vs target $33642; same-side losing runs max 10, p95 6, $-50090 lost on 3rd-and-later; no-new-evidence re-entries 37.2/wk $2063; recoveries cut 13.6/wk $44413, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $19844/wk, losers avoided $20196/wk, net +5374 $/wk; pnl $25158/wk.
WEL_E1L HOLD: months missing (6 of 12), window not scored
WEL_E1L PRE: months missing (17 of 17), window not scored
WEL_E1L X': months missing (10 of 10), window not scored

```

## Throughput
W-E adopted the W-T shared-memory month cache (TP_ENGINE=1 via tp_launch, launch gate lowered from 62 to 25 GB, tp_admit request WORKS_JN05, at most 3 workers). Identity check on my own driver: WEJ_H1A 202610 under TP_ENGINE=1 vs the recorded run, 845 vs 845 trades, trade-for-trade IDENTICAL. Before adoption W-E finished 1 cell-month in the first hour (the gate at 62 GB never opened). Box-wide rate now: window 3.0 h: 894 cell-months finished = 298.0 /h total; mean engine secs per cell 117 {'PTR': 287, 'BO': 126, 'WL': 86, 'WG': 78, 'EC': 71, 'WI': 60, 'ZJ': 57, 'JN': 48, 'WM': 47, 'WEL': 18, 'WEJ': 16}

## Not done yet
Asymmetric-bracket cells (60/45, 60/90 by flag) and the late-entry swing stop (D7) are exact-only and are queued after the skip/half stage; the flag separation by persistence across weeks, and the "trend weeks" comparison beyond the live week, wait for more exact output. DS3_WORKS_E.md is regenerated by code/th_works_e/e_page.py every 4 hours from 23:00Z until the final at 2026-11-12 12:00Z.



## I. (W-I) (I)

Source DS3_WORKS_I.md (mtime 2026-11-12T11:49:22Z UTC), included verbatim, read only:

# DS3_WORKS_I - T-WORKS / P7 FIX, worker W-I (families I room to target, J cross-market, K context, L P7 signal internals), page 2026-11-12 11:48Z
Label PRE-PROOF, post-hoc, Shadow only, no PASS claim. Prereg autopilot/WORKS_I_PREREG.md (sha in DECISIONS.md; the first first-order screen ran before the sha line, disclosed there). Code code/th_works_i/, tables /mnt/l2/l2vast/_th_works/i/, feature table /mnt/l2/l2vast/_th_works/p7_feat_I.parquet (key sig_ts, 5,011 P7 taken trades x 128 columns; W-E signal-level table not used, so signals that were not taken are not in these tests).

## What exists
1. One feature function (i_feat.build) serves both the first-order table and the exact engine (identity checked: the table and the function output are identical in all 128 columns). Bars: NQ/ES/RTY 1-min with volume to 2026-11-10, ZN/6E/6J owned core bars, calendar events verified against the 08:30 / 14:00 ET range spike (unverified dates: FOMC 2026-03-18, NFP 2025-04-04, 2025-11-16, 2026-02-06; CPI identity cannot be told apart from PPI/retail days by the spike alone, the listed CPI dates all spike).
2. First-order screen: 1,176 flags x skip/half = 2,352 cells on the LPB_BASE trade list (whole-stack daily P&L, live rows excluded), each with removed-$ in the 20 worst P7 weeks vs the 20 best (trend) weeks and the flagged trades of the frozen live week. Not built: ES print absorption (needs ES trades), tick-level 45-s confirm quality beyond signal-to-entry seconds and the 1-s dip.
3. Exact hook: i_mixin.IGateMixin (skip / half / target retarget at the signal second inside the JN04RM / LPB engine), set builder i_mkset.py, manager i_mgr.py (launch gate 62 GB, hard guard 40 GB), scorer i_score.py.

## Family null (is the best cell of a family better than the best cell of random flags?)
The feature rows were permuted among P7 trades inside the same calendar month, the whole grid re-scored, and the best minimum equal-mean cut over L6M, HOLD, PRE and X-prime (cells flagging 5-45 percent of trades) recorded; 300 draws.

| family | observed best | null median | null p90 | family p |
|--|--|--|--|--|
| I | 16.3 | 7.9 | 16.6 | 0.110 |
| J | 27.3 | 20.6 | 28.8 | 0.136 |
| K | 21.3 | 13.3 | 22.6 | 0.140 |
| L | 14.4 | 18.2 | 25.1 | 0.751 |

Plain reading: no family beats its null at 5 percent. J (cross-market) is closest on cell count; I, K are about 0.1; L is at the null. Everything below is therefore a lead, not a finding.

## Registered cells (top-3 per family by the prereg rule, plus asymmetry picks)
Columns: cut and eq_cut are stack maxDD cut percent (first-order, vs LPB_BASE, equal-mean for eq); rem w20 / rem b20 = P&L $ of the removed part in the 20 worst / 20 best P7 weeks (negative = losers removed); live = flagged trades in the frozen live week and the $ removed there (positive = winners removed).

| fam | kind | cell | scope | act | n_flag | cut_L6M | cut_HOLD | cut_PRE | cut_X' | dmean_L6M | placebo_p | rem_w20 | rem_b20 | live_n | live_rem |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| I | prereg_top3 | room_on_x<2.0 | all | skip | 1766 | 27.6 | 13.0 | 12.2 | 29.9 | 776.6 | 0.0 | -232901.7 | 281945.8 | 11 | 20662.8 |
| I | prereg_top3 | room_on_x<1.5 | all | skip | 1431 | 20.6 | 7.2 | 0.3 | 23.6 | 1074.2 | 0.1 | -188232.2 | 238580.1 | 9 | 18761.6 |
| I | prereg_top3 | room_on_x<1.5 | asia | half | 505 | 0.5 | 2.5 | -0.4 | 10.9 | 623.5 | 0.1 | -62023.8 | 76271.3 | 3 | 6552.3 |
| J | prereg_top3 | breadth_ext15==3 | all | skip | 1602 | 22.5 | 24.1 | 25.1 | 39.7 | 1081.1 | 0.0 | -190031.7 | 283510.9 | 11 | 30227.7 |
| J | prereg_top3 | x_es_pull_opp5>=1.225(q70) | all | skip | 1245 | 3.5 | 5.4 | -1.0 | 0.9 | 4691.2 | 0.1 | -90678.8 | 165414.9 | 0 | 0.0 |
| J | prereg_top3 | es_r60m>=21.82(q70) | all | skip | 1147 | 20.1 | 21.7 | 12.5 | 20.2 | 1657.7 | 0.0 | -143057.5 | 151408.8 | 13 | 12470.2 |
| K | prereg_top3 | dow==2 | asia | skip | 408 | 35.5 | 8.0 | 4.7 | 13.2 | 3584.8 | 0.0 | -76942.0 | 88268.5 | 14 | 10053.3 |
| K | prereg_top3 | dow==2 | all | skip | 895 | 40.4 | 1.1 | 12.4 | 13.9 | 3069.8 | 0.0 | -89549.4 | 141877.1 | 19 | 8571.2 |
| K | prereg_top3 | dow>1 | asia | skip | 1307 | 33.1 | 10.3 | -0.1 | 33.2 | 2900.3 | 0.0 | -276281.1 | 340685.0 | 21 | 27343.7 |
| L | prereg_top3 | push_beyond_ref<=-1(q30) | all | half | 1682 | 14.1 | 15.9 | 14.3 | 11.8 | 527.0 | 0.0 | -73951.5 | 98885.3 | 24 | 20206.2 |
| L | prereg_top3 | pb_depth>=13.75(q70) | all | half | 1875 | 4.0 | 6.0 | 2.2 | 11.1 | 2109.7 | 0.1 | -56351.0 | 60354.7 | 38 | 20686.8 |
| L | prereg_top3 | pb_depth>=18(q80) | all | skip | 1275 | 28.5 | -11.4 | 8.3 | 9.6 | 4657.0 | 0.0 | -91302.4 | 85225.2 | 32 | 29690.0 |
| J | asymmetry_pick | rs_es15>=4.377(q80) | all | half | 1090 | 12.3 | 12.2 | 10.0 | 14.8 | 1804.4 | nan | -60988.7 | -4937.7 | 21 | 15820.3 |
| J | asymmetry_pick | rs_es30>=9.397(q80) | all | half | 998 | 19.9 | 9.4 | 21.0 | 6.5 | 592.0 | nan | -53167.4 | -1761.4 | 18 | 13599.6 |
| J | asymmetry_pick | nq_r60m>=32.91(q70) | all | skip | 1199 | 46.5 | 37.4 | 20.7 | 10.4 | 1242.3 | nan | -154496.0 | 153429.7 | 19 | 4934.1 |

## Bi-weekly walk-forward (first-order)
| kind | fam | cell | wf2w_cut | wf2w_mean | wf2w_beat_pct |
|--|--|--|--|--|--|
| family_repick | I | all 68 cells | -8.3 | -2495.7 | 59.5 |
| family_repick | J | all 954 cells | -3.2 | -2402.3 | 60.8 |
| family_repick | K | all 206 cells | -7.9 | -2768.6 | 51.9 |
| family_repick | L | all 488 cells | 11.4 | -1266.0 | 68.4 |
| cell_vs_live | I | I|room_on_x<2.0|all|skip | 12.2 | -2150.4 | 41.8 |
| cell_vs_live | I | I|room_on_x<1.5|all|skip | 0.3 | -1696.8 | 30.4 |
| cell_vs_live | I | I|room_on_x<1.5|asia|half | -0.4 | -337.9 | 34.2 |
| cell_vs_live | J | J|breadth_ext15==3|all|skip | 25.1 | -127.2 | 64.6 |
| cell_vs_live | J | J|breadth_ext15>2|all|skip | 25.1 | -127.2 | 64.6 |
| cell_vs_live | J | J|x_es_pull_opp5>=1.225(q70)|all|skip | -1.0 | 445.7 | 39.2 |
| cell_vs_live | J | J|es_r60m>=21.82(q70)|all|skip | 2.9 | 18.2 | 51.9 |
| cell_vs_live | J | J|rs_es15>=4.377(q80)|all|half | 10.0 | 565.8 | 48.1 |
| cell_vs_live | J | J|rty_ext15==1|all|skip | 20.7 | -1052.6 | 63.3 |
| cell_vs_live | J | J|rty_ext15>0|all|skip | 20.7 | -1052.6 | 63.3 |
| cell_vs_live | J | J|rs_es15>=4.377(q80)|all|skip | 25.1 | 876.9 | 46.8 |
| cell_vs_live | K | K|dow==2|asia|skip | -0.3 | 312.3 | 39.2 |
| cell_vs_live | K | K|dow==2|all|skip | -3.3 | -615.8 | 48.1 |
| cell_vs_live | K | K|dow>1|asia|skip | -0.1 | -1254.5 | 40.5 |
| cell_vs_live | K | K|dow>1|asia|half | 4.5 | -739.8 | 62.0 |
| cell_vs_live | K | K|dow==2|asia|half | 3.9 | 37.8 | 48.1 |
| cell_vs_live | K | K|dow==3|all|skip | 14.2 | -108.8 | 54.4 |
| cell_vs_live | K | K|dow==2|all|half | 8.9 | -64.9 | 57.0 |
| cell_vs_live | K | K|dow==3|asia|skip | -2.5 | -894.7 | 26.6 |
| cell_vs_live | L | L|push_beyond_ref<=-1(q30)|all|half | 14.3 | 82.2 | 73.4 |
| cell_vs_live | L | L|pb_depth>=13.75(q70)|all|half | -6.5 | 363.2 | 70.9 |
| cell_vs_live | L | L|pb_depth>=18(q80)|all|skip | -14.1 | 203.5 | 55.7 |
| cell_vs_live | L | L|ema_slope15>=1.3(q80)|all|skip | -0.4 | -528.3 | 57.0 |
| cell_vs_live | L | L|dip3>=20.75(q80)|all|half | -4.6 | 380.0 | 54.4 |
| cell_vs_live | L | L|l2conf<=1|asia|half | 14.1 | -63.7 | 51.9 |
| cell_vs_live | L | L|pb_depth>=13.75(q70)|all|skip | -15.5 | -747.4 | 53.2 |
| cell_vs_live | L | L|ema_slope15>=1.3(q80)|all|half | 28.2 | 193.4 | 65.8 |

The family re-pick rows are the honest out-of-sample of the whole screen: only L shows a drawdown cut and it costs mean; the others are negative.

## Asymmetric bracket (flagged entries get target 30/35/45 instead of 60, first-order from the PTR paths; only the target side is representable)
| cell | tgt | n_flag | n_hit | cut_L6M | cut_HOLD | cut_PRE | cut_X' | dmean_L6M | chg_w20 | chg_b20 |
|--|--|--|--|--|--|--|--|--|--|--|
| I|room_on_x<2.0|all | 30.0 | 1766 | 1060 | -6.0 | -4.8 | 14.0 | 10.1 | -948.5 | 99731.7 | -143534.0 |
| I|room_on_x<2.0|all | 35.0 | 1766 | 993 | -3.7 | -1.7 | 12.4 | 3.7 | -1199.2 | 98673.2 | -111047.0 |
| I|room_on_x<2.0|all | 45.0 | 1766 | 877 | 7.9 | -4.3 | 2.6 | -0.3 | -1341.8 | 46673.2 | -60972.5 |
| J|breadth_ext15==3|all | 30.0 | 1602 | 943 | 3.9 | 5.9 | 13.5 | 5.4 | 75.5 | 68954.2 | -79936.5 |
| J|breadth_ext15==3|all | 35.0 | 1602 | 877 | 2.6 | 4.6 | 18.9 | 9.1 | -369.1 | 42752.7 | -50883.0 |
| J|breadth_ext15==3|all | 45.0 | 1602 | 781 | 17.7 | 17.9 | 5.5 | 2.6 | -304.7 | 29479.7 | -17524.5 |
| J|es_r60m>=21.82(q70)|all | 30.0 | 1147 | 653 | 3.8 | 5.7 | 7.1 | -0.1 | 1161.7 | 61170.2 | -56213.0 |
| J|es_r60m>=21.82(q70)|all | 35.0 | 1147 | 623 | 4.0 | 6.0 | 11.9 | 0.5 | 1937.8 | 56669.7 | -47780.0 |
| J|es_r60m>=21.82(q70)|all | 45.0 | 1147 | 543 | 4.5 | 6.5 | 18.4 | -2.1 | 539.7 | 39691.7 | -33925.0 |
| J|rs_es15>=4.377(q80)|all | 30.0 | 1090 | 637 | -0.4 | 1.6 | 0.0 | 24.4 | 495.5 | 42236.0 | 6908.5 |
| J|rs_es15>=4.377(q80)|all | 35.0 | 1090 | 606 | 1.0 | 3.0 | 8.4 | 26.3 | 257.0 | 38303.0 | 24323.5 |
| J|rs_es15>=4.377(q80)|all | 45.0 | 1090 | 516 | 6.0 | 0.3 | -10.6 | -0.6 | 506.7 | 7740.0 | 37582.0 |
| K|dow==2|asia | 30.0 | 408 | 244 | 24.1 | 15.3 | 5.1 | 12.1 | 1027.4 | 22861.0 | -56825.0 |
| K|dow==2|asia | 35.0 | 408 | 224 | 27.5 | 18.5 | 2.9 | 10.4 | 1085.7 | 20156.5 | -39525.0 |
| K|dow==2|asia | 45.0 | 408 | 193 | 30.5 | 24.9 | 9.5 | 16.3 | 257.1 | 36951.5 | -6917.0 |
| L|push_beyond_ref<=-1(q30)|all | 30.0 | 1682 | 1017 | 36.4 | 16.4 | 12.7 | 29.6 | 972.9 | 84315.0 | -109085.0 |
| L|push_beyond_ref<=-1(q30)|all | 35.0 | 1682 | 953 | 40.7 | 22.8 | 15.8 | 19.3 | 963.9 | 89365.0 | -75674.0 |
| L|push_beyond_ref<=-1(q30)|all | 45.0 | 1682 | 836 | 28.8 | 18.1 | 9.3 | 14.8 | 1815.0 | 63708.0 | -33010.5 |
| L|ema_slope15>=1.3(q80)|all | 30.0 | 1257 | 737 | 15.0 | 11.3 | 24.4 | 5.2 | -562.7 | 92699.2 | -20066.5 |
| L|ema_slope15>=1.3(q80)|all | 35.0 | 1257 | 695 | 12.8 | 14.6 | 26.3 | 5.3 | 758.2 | 80441.7 | -4730.0 |
| L|ema_slope15>=1.3(q80)|all | 45.0 | 1257 | 614 | 8.5 | 10.4 | 24.1 | 5.2 | 656.6 | 48607.2 | 13658.5 |

## Exact (one set per job, JN04RM base, vs JN04RM and LPB references)

vs JN04RM
| cell | window | cut | eq_cut | dmean | dd | dd_ref | d_worst5 | d_best5 |
|--|--|--|--|--|--|--|--|--|
| WI_J_RS15H | L1M | 4.4 | 1.5 | 398.3 | 25860.9 | 27055.7 | -8967.6 | -8967.6 |
| WI_J_RS15H | L3M | -13.5 | -17.0 | -142.2 | 47325.8 | 41699.4 | 995.9 | -6839.6 |
| WI_J_RS15H | L6M | -13.5 | -17.0 | -518.8 | 47325.8 | 41699.4 | 9437.5 | -14404.1 |
| WI_J_ES60S | L1M | -6.1 | -6.3 | 119.6 | 28692.8 | 27055.7 | -3185.1 | -3185.1 |
| WI_J_ES60S | L3M | 0.0 | -0.3 | -213.5 | 41694.9 | 41699.4 | -1632.6 | 3410.2 |
| WI_J_ES60S | L6M | 0.0 | -0.3 | -47.5 | 41694.9 | 41699.4 | 7220.0 | -34804.8 |
| WI_L_SL13S | L1M | 51.1 | 53.8 | 1337.1 | 13236.2 | 27055.7 | 13480.3 | 13480.3 |
| WI_L_SL13S | L3M | -8.1 | -2.2 | 687.9 | 45087.2 | 41699.4 | 15172.9 | 6062.0 |
| WI_L_SL13S | L6M | -8.1 | -2.2 | 1061.9 | 45087.2 | 41699.4 | 13101.0 | -9716.9 |
| WI_J_BR3T45 | L1M | 17.0 | 12.3 | 401.0 | 22462.1 | 27055.7 | 3700.1 | 3700.1 |
| WI_J_BR3T45 | L3M | 12.7 | 7.8 | 428.3 | 36418.2 | 41699.4 | 13297.8 | -1804.3 |
| WI_J_BR3T45 | L6M | 3.3 | -2.1 | -1010.2 | 40309.0 | 41699.4 | 12080.4 | -14483.7 |
| WI_L_SL13T35 | L1M | 41.1 | 36.0 | 40.7 | 15944.4 | 27055.7 | 9072.2 | 9072.2 |
| WI_L_SL13T35 | L3M | -36.0 | -47.6 | -1376.9 | 56717.1 | 41699.4 | -1697.7 | 16818.1 |
| WI_L_SL13T35 | L6M | -36.0 | -47.6 | -1406.6 | 56717.1 | 41699.4 | 6956.8 | -8163.5 |
| WI_I_ON15S | L1M | 10.3 | 7.0 | -2871.2 | 24263.6 | 27055.7 | -2122.3 | -2122.3 |
| WI_I_ON15S | L3M | -12.4 | -16.6 | -660.5 | 46873.7 | 41699.4 | -2382.2 | -40967.2 |
| WI_I_ON15S | L6M | -12.4 | -16.6 | -585.7 | 46873.7 | 41699.4 | 16505.6 | -48766.7 |
| WI_J_RS30T35 | L1M | 60.2 | 60.0 | 1094.9 | 10775.2 | 27055.7 | 11703.3 | 11703.3 |
| WI_J_RS30T35 | L3M | 8.5 | 8.1 | 1031.0 | 38158.6 | 41699.4 | 21333.7 | 7413.0 |
| WI_J_RS30T35 | L6M | 8.5 | 8.1 | -83.4 | 38158.6 | 41699.4 | 31162.1 | -4886.5 |
| WI_J_RS30T35 | HOLD | -0.5 | -0.9 | 90.1 | 73098.7 | 72757.5 | 16772.8 | -2761.7 |
| WI_K_DOW1AS | L1M | 31.2 | 23.5 | -2906.0 | 18603.7 | 27055.7 | 2288.8 | 2288.8 |
| WI_K_DOW1AS | L3M | -10.6 | -23.0 | -1684.1 | 46100.8 | 41699.4 | 15996.2 | -28524.3 |
| WI_K_DOW1AS | L6M | -10.6 | -23.0 | -1695.6 | 46100.8 | 41699.4 | 22766.3 | -80446.9 |
| WI_K_W2S | L1M | 32.8 | 35.7 | -1510.9 | 18189.9 | 27055.7 | 2356.9 | 2356.9 |
| WI_K_W2S | L3M | 35.0 | 37.9 | 1579.3 | 27090.1 | 41699.4 | 25296.7 | -3913.0 |
| WI_K_W2S | L6M | 27.3 | 30.5 | 766.5 | 30321.6 | 41699.4 | 34066.6 | -3965.6 |
| WI_K_W2S | HOLD | -5.4 | -0.8 | -41.3 | 76692.8 | 72757.5 | 20557.6 | -14435.0 |
| WI_J_BR3S | L1M | 26.7 | 29.9 | -3564.8 | 19835.4 | 27055.7 | -414.4 | -414.4 |
| WI_J_BR3S | L3M | 28.1 | 31.2 | -811.4 | 29993.2 | 41699.4 | 29596.9 | -17763.8 |
| WI_J_BR3S | L6M | 14.4 | 18.1 | 782.7 | 35674.8 | 41699.4 | 33013.6 | -57351.5 |
| WI_J_BR3S | HOLD | 19.0 | 22.5 | 441.6 | 58943.3 | 72757.5 | 5774.6 | -44697.2 |
| WI_J_BR3S | PRE | 5.2 | 9.3 | -452.3 | 63274.5 | 66713.5 | 12000.0 | -26099.3 |
| WI_J_BR3S | X' | 4.3 | 8.5 | 69.4 | 61307.4 | 64076.6 | 15525.5 | -345.4 |
| WI_J_BR3S | WF2W | 0.0 | 50.6 | -257.7 | nan | nan | nan | nan |
| WI_J_RS30H | L1M | 15.9 | 12.0 | -50.0 | 22762.2 | 27055.7 | 3316.3 | 3316.3 |
| WI_J_RS30H | L3M | 13.6 | 9.6 | 108.5 | 36044.5 | 41699.4 | 13070.7 | -24516.5 |
| WI_J_RS30H | L6M | 13.6 | 9.6 | -755.3 | 36044.5 | 41699.4 | 20365.3 | -36859.2 |
| WI_L_PUSHH | L1M | 4.7 | 3.0 | 423.3 | 25785.9 | 27055.7 | -2344.1 | -2344.1 |
| WI_L_PUSHH | L3M | 15.9 | 14.4 | -215.0 | 35087.7 | 41699.4 | 12501.2 | -22280.8 |
| WI_L_PUSHH | L6M | 15.9 | 14.4 | -296.1 | 35087.7 | 41699.4 | 18416.1 | -21772.9 |
| WI_L_PUSHH | HOLD | 20.2 | 18.8 | -342.1 | 58036.4 | 72757.5 | 22567.1 | -18037.8 |
| WI_L_PB18S | L1M | 26.2 | 31.1 | -2824.7 | 19979.6 | 27055.7 | -361.0 | -361.0 |
| WI_L_PB18S | L3M | 11.4 | 17.3 | 445.6 | 36964.7 | 41699.4 | 16723.1 | -1314.5 |
| WI_L_PB18S | L6M | 11.4 | 17.3 | 1245.3 | 36964.7 | 41699.4 | 24513.1 | -39871.6 |
| WI_L_SL19H | L1M | 32.8 | 33.2 | -191.1 | 18190.7 | 27055.7 | 4825.3 | 4825.3 |
| WI_L_SL19H | L3M | -3.7 | -3.1 | 919.2 | 43224.7 | 41699.4 | 11334.0 | -1416.8 |
| WI_L_SL19H | L6M | -3.7 | -3.1 | 109.3 | 43224.7 | 41699.4 | 13461.4 | -14078.5 |
| WI_G_BR3S | L1M | 37.7 | 33.7 | -3343.3 | 16856.9 | 27055.7 | 238.9 | 238.9 |
| WI_G_BR3S | L3M | 28.1 | 23.4 | -987.7 | 29993.2 | 41699.4 | 32575.3 | -22858.3 |
| WI_G_BR3S | L6M | 13.5 | 8.0 | -1202.3 | 36051.4 | 41699.4 | 35615.5 | -67149.8 |
| WI_G_BR3S | HOLD | 13.1 | 7.5 | -454.3 | 63203.0 | 72757.5 | 1955.4 | -55526.5 |
| WI_I_ON2S | L1M | 12.4 | 5.1 | 1114.7 | 23711.7 | 27055.7 | -4186.2 | -4186.2 |
| WI_I_ON2S | L3M | 9.5 | 2.0 | -1526.0 | 37742.4 | 41699.4 | 7301.0 | -43953.3 |
| WI_I_ON2S | L6M | 9.5 | 2.0 | -1458.7 | 37742.4 | 41699.4 | 25695.5 | -61850.9 |
| WI_I_ON2S | HOLD | 5.2 | -2.7 | -817.8 | 68965.0 | 72757.5 | -234.0 | -52530.8 |
| WI_J_NQ60S | L1M | 15.2 | 13.8 | -762.5 | 22937.5 | 27055.7 | 4668.6 | 4668.6 |
| WI_J_NQ60S | L3M | 8.0 | 6.4 | 969.0 | 38376.9 | 41699.4 | 11382.0 | -1301.6 |
| WI_J_NQ60S | L6M | 8.0 | 6.4 | -288.0 | 38376.9 | 41699.4 | 21433.4 | -57892.7 |
| WI_J_NQ60S | HOLD | 6.1 | 4.5 | 505.7 | 68351.0 | 72757.5 | 13699.1 | -33750.7 |
| WI_K_W2AS | L1M | -1.1 | -3.2 | -95.4 | 27342.1 | 27055.7 | -4255.9 | -4255.9 |
| WI_K_W2AS | L3M | 8.0 | 6.1 | -447.0 | 38344.3 | 41699.4 | 6498.6 | 717.1 |
| WI_K_W2AS | L6M | 8.0 | 6.1 | -430.7 | 38344.3 | 41699.4 | 18250.5 | 1471.6 |
| WI_K_W2AS | HOLD | -4.9 | -7.1 | -573.7 | 76301.0 | 72757.5 | 18293.2 | 598.3 |
| WI_K_W2AT45 | L1M | -0.7 | -1.9 | 323.1 | 27254.1 | 27055.7 | -230.7 | -230.7 |
| WI_K_W2AT45 | L3M | 10.1 | 9.1 | -37.7 | 37471.9 | 41699.4 | 6724.7 | 11805.6 |
| WI_K_W2AT45 | L6M | 10.1 | 9.1 | -203.1 | 37471.9 | 41699.4 | 13914.0 | -7040.1 |
| WI_L_PB13H | L1M | 2.0 | -0.1 | 181.3 | 26511.7 | 27055.7 | -6564.8 | -6564.8 |
| WI_L_PB13H | L3M | 7.4 | 5.4 | -72.0 | 38613.6 | 41699.4 | 3629.8 | -13748.2 |
| WI_L_PB13H | L6M | 7.4 | 5.4 | -370.8 | 38613.6 | 41699.4 | 19538.6 | -37748.5 |
| WI_L_PB13H | HOLD | 7.7 | 5.7 | 221.4 | 67177.1 | 72757.5 | 20784.9 | -21626.7 |
| WI_N_BR3S | L1M | 36.2 | 35.0 | 3260.4 | 17274.5 | 27055.7 | -1585.9 | -1585.9 |
| WI_N_BR3S | L3M | 58.6 | 57.8 | 12.6 | 17274.5 | 41699.4 | 35565.0 | -73428.4 |
| WI_N_BR3S | L6M | 58.6 | 57.8 | -287.0 | 17274.5 | 41699.4 | 72070.9 | -125597.8 |
| WI_N_BR3S | HOLD | 34.4 | 33.3 | -875.3 | 47706.1 | 72757.5 | 80020.3 | -128640.7 |

vs LPB
| cell | window | cut | eq_cut | dmean | dd | dd_ref | d_worst5 | d_best5 |
|--|--|--|--|--|--|--|--|--|
| WI_J_RS15H | L1M | 49.5 | 42.7 | -10029.2 | 25860.9 | 51252.7 | 4963.7 | 4963.7 |
| WI_J_RS15H | L3M | 38.7 | 30.4 | -3229.6 | 47325.8 | 77224.2 | 71571.3 | -55741.2 |
| WI_J_RS15H | L6M | 38.7 | 30.4 | -2576.8 | 47325.8 | 77224.2 | 80897.7 | -46417.0 |
| WI_J_ES60S | L1M | 44.0 | 36.0 | -6766.1 | 28692.8 | 51252.7 | 10746.2 | 10746.2 |
| WI_J_ES60S | L3M | 46.0 | 38.3 | -1811.6 | 41694.9 | 77224.2 | 69149.4 | -45491.3 |
| WI_J_ES60S | L6M | 46.0 | 38.3 | -2695.8 | 41694.9 | 77224.2 | 78886.9 | -46554.7 |
| WI_L_SL13S | L1M | 74.2 | 72.2 | -3842.5 | 13236.2 | 51252.7 | 27411.6 | 27411.6 |
| WI_L_SL13S | L3M | 41.6 | 37.2 | -1087.4 | 45087.2 | 77224.2 | 74220.8 | -42839.6 |
| WI_L_SL13S | L6M | 41.6 | 37.2 | -1523.3 | 45087.2 | 77224.2 | 73033.7 | -37514.0 |
| WI_J_BR3T45 | L1M | 56.2 | 51.1 | -6484.8 | 22462.1 | 51252.7 | 17631.3 | 17631.3 |
| WI_J_BR3T45 | L3M | 52.8 | 47.4 | -920.2 | 36418.2 | 77224.2 | 77891.7 | -50705.9 |
| WI_J_BR3T45 | L6M | 47.8 | 41.7 | -2233.5 | 40309.0 | 77224.2 | 77559.1 | -54900.7 |
| WI_L_SL13T35 | L1M | 68.9 | 65.1 | -4582.1 | 15944.4 | 51252.7 | 23003.4 | 23003.4 |
| WI_L_SL13T35 | L3M | 26.6 | 17.6 | -2102.2 | 56717.1 | 77224.2 | 61243.7 | -32083.5 |
| WI_L_SL13T35 | L6M | 26.6 | 17.6 | -2330.9 | 56717.1 | 77224.2 | 70783.0 | -39984.9 |
| WI_I_ON15S | L1M | 52.7 | 43.9 | -9757.0 | 24263.6 | 51252.7 | 11808.9 | 11808.9 |
| WI_I_ON15S | L3M | 39.3 | 28.1 | -5207.0 | 46873.7 | 77224.2 | 74588.7 | -89868.8 |
| WI_I_ON15S | L6M | 39.3 | 28.1 | -3344.1 | 46873.7 | 77224.2 | 94361.3 | -83398.6 |
| WI_J_RS30T35 | L1M | 79.0 | 77.3 | -5605.3 | 10775.2 | 51252.7 | 25634.5 | 25634.5 |
| WI_J_RS30T35 | L3M | 50.6 | 46.6 | -908.3 | 38158.6 | 77224.2 | 82343.0 | -41488.6 |
| WI_J_RS30T35 | L6M | 50.6 | 46.6 | -1590.3 | 38158.6 | 77224.2 | 93056.2 | -43899.2 |
| WI_J_RS30T35 | HOLD | 7.3 | -0.1 | -3434.3 | 73098.7 | 78842.0 | 110152.0 | -63127.0 |
| WI_K_DOW1AS | L1M | 63.7 | 52.9 | -9791.7 | 18603.7 | 51252.7 | 16220.1 | 16220.1 |
| WI_K_DOW1AS | L3M | 40.3 | 22.6 | -2983.4 | 46100.8 | 77224.2 | 96778.0 | -77425.9 |
| WI_K_DOW1AS | L6M | 40.3 | 22.6 | -4924.2 | 46100.8 | 77224.2 | 104432.9 | -111633.0 |
| WI_K_W2S | L1M | 64.5 | 61.2 | -8396.7 | 18189.9 | 51252.7 | 16288.1 | 16288.1 |
| WI_K_W2S | L3M | 64.9 | 61.6 | -2210.0 | 27090.1 | 77224.2 | 96672.7 | -52814.6 |
| WI_K_W2S | L6M | 60.7 | 57.0 | -1846.0 | 30321.6 | 77224.2 | 106327.5 | -55401.4 |
| WI_K_W2S | HOLD | 2.7 | -6.4 | -4107.6 | 76692.8 | 78842.0 | 113676.1 | -88542.8 |
| WI_J_BR3S | L1M | 61.3 | 63.7 | -6004.0 | 19835.4 | 51252.7 | 13516.8 | 13516.8 |
| WI_J_BR3S | L3M | 61.2 | 63.6 | 4396.7 | 29993.2 | 77224.2 | 83169.8 | -66665.4 |
| WI_J_BR3S | L6M | 53.8 | 56.6 | 1043.4 | 35674.8 | 77224.2 | 87471.4 | -81571.0 |
| WI_J_BR3S | HOLD | 25.2 | 29.8 | -2144.8 | 58943.3 | 78842.0 | 96023.4 | -102406.2 |
| WI_J_BR3S | PRE | 36.4 | 40.3 | -1961.6 | 63274.5 | 99479.4 | 104974.3 | -166595.6 |
| WI_J_BR3S | X' | 50.0 | 53.1 | -641.8 | 61307.4 | 122552.7 | 82071.3 | -54645.7 |
| WI_J_BR3S | WF2W | 36.4 | 86.1 | -3018.3 | nan | nan | nan | nan |
| WI_J_RS30H | L1M | 55.6 | 48.0 | -6056.0 | 22762.2 | 51252.7 | 17247.6 | 17247.6 |
| WI_J_RS30H | L3M | 53.3 | 45.3 | -3679.1 | 36044.5 | 77224.2 | 79613.0 | -73418.1 |
| WI_J_RS30H | L6M | 53.3 | 45.3 | -3149.5 | 36044.5 | 77224.2 | 87792.4 | -70769.5 |
| WI_L_PUSHH | L1M | 49.7 | 43.4 | -7528.7 | 25785.9 | 51252.7 | 11587.1 | 11587.1 |
| WI_L_PUSHH | L3M | 54.6 | 48.9 | -3386.0 | 35087.7 | 77224.2 | 84244.1 | -71182.4 |
| WI_L_PUSHH | L6M | 54.6 | 48.9 | -2394.2 | 35087.7 | 77224.2 | 91043.9 | -49731.0 |
| WI_L_PUSHH | HOLD | 26.4 | 17.2 | -4156.3 | 58036.4 | 78842.0 | 109098.8 | -61452.5 |
| WI_L_PB18S | L1M | 61.0 | 58.4 | -6660.4 | 19979.6 | 51252.7 | 13570.2 | 13570.2 |
| WI_L_PB18S | L3M | 52.1 | 49.0 | -205.4 | 36964.7 | 77224.2 | 75388.6 | -50216.1 |
| WI_L_PB18S | L6M | 52.1 | 49.0 | -1330.0 | 36964.7 | 77224.2 | 84063.5 | -67373.7 |
| WI_L_SL19H | L1M | 64.5 | 60.4 | -7076.9 | 18190.7 | 51252.7 | 18756.6 | 18756.6 |
| WI_L_SL19H | L3M | 44.0 | 37.5 | -2329.6 | 43224.7 | 77224.2 | 78255.4 | -50318.4 |
| WI_L_SL19H | L6M | 44.0 | 37.5 | -2232.5 | 43224.7 | 77224.2 | 81267.6 | -41370.0 |
| WI_G_BR3S | L1M | 67.1 | 68.7 | -6782.8 | 16856.9 | 51252.7 | 14170.2 | 14170.2 |
| WI_G_BR3S | L3M | 61.2 | 63.1 | 4420.2 | 29993.2 | 77224.2 | 86159.4 | -71759.8 |
| WI_G_BR3S | L6M | 53.3 | 55.6 | 817.4 | 36051.4 | 77224.2 | 90084.3 | -92400.3 |
| WI_G_BR3S | HOLD | 19.8 | 23.8 | -2201.9 | 63203.0 | 78842.0 | 95193.8 | -113050.6 |
| WI_I_ON2S | L1M | 53.7 | 48.5 | -10628.9 | 23711.7 | 51252.7 | 9745.0 | 9745.0 |
| WI_I_ON2S | L3M | 51.1 | 45.6 | -2253.1 | 37742.4 | 77224.2 | 91523.7 | -92854.8 |
| WI_I_ON2S | L6M | 51.1 | 45.6 | -2174.3 | 37742.4 | 77224.2 | 110803.1 | -95845.2 |
| WI_I_ON2S | HOLD | 12.5 | 2.7 | -3954.3 | 68965.0 | 78842.0 | 106844.5 | -119290.6 |
| WI_J_NQ60S | L1M | 55.2 | 47.6 | -4383.7 | 22937.5 | 51252.7 | 18599.8 | 18599.8 |
| WI_J_NQ60S | L3M | 50.3 | 41.8 | -1589.0 | 38376.9 | 77224.2 | 75561.9 | -50203.2 |
| WI_J_NQ60S | L6M | 50.3 | 41.8 | -3149.4 | 38376.9 | 77224.2 | 86498.1 | -66613.5 |
| WI_J_NQ60S | HOLD | 13.3 | -1.6 | -3682.7 | 68351.0 | 78842.0 | 92824.2 | -95224.0 |
| WI_K_W2AS | L1M | 46.7 | 42.2 | -8806.1 | 27342.1 | 51252.7 | 9675.3 | 9675.3 |
| WI_K_W2AS | L3M | 50.3 | 46.2 | -2083.6 | 38344.3 | 77224.2 | 79180.0 | -48184.5 |
| WI_K_W2AS | L6M | 50.3 | 46.2 | -1653.8 | 38344.3 | 77224.2 | 91816.8 | -43340.5 |
| WI_K_W2AS | HOLD | 3.2 | -4.8 | -3951.4 | 76301.0 | 78842.0 | 107497.4 | -74772.4 |
| WI_K_W2AT45 | L1M | 46.8 | 43.3 | -6562.7 | 27254.1 | 51252.7 | 13700.5 | 13700.5 |
| WI_K_W2AT45 | L3M | 51.5 | 48.3 | -1203.1 | 37471.9 | 77224.2 | 74249.8 | -37096.0 |
| WI_K_W2AT45 | L6M | 51.5 | 48.3 | -1338.6 | 37471.9 | 77224.2 | 82324.0 | -47862.1 |
| WI_L_PB13H | L1M | 48.3 | 41.2 | -7762.6 | 26511.7 | 51252.7 | 7366.4 | 7366.4 |
| WI_L_PB13H | L3M | 50.0 | 43.2 | -2538.4 | 38613.6 | 77224.2 | 70056.5 | -62649.8 |
| WI_L_PB13H | L6M | 50.0 | 43.2 | -2586.2 | 38613.6 | 77224.2 | 86850.1 | -65544.4 |
| WI_L_PB13H | HOLD | 14.8 | 3.1 | -3650.2 | 67177.1 | 78842.0 | 101377.3 | -78723.9 |
| WI_N_BR3S | L1M | 66.3 | 66.4 | -8424.7 | 17274.5 | 51252.7 | 12345.3 | 12345.3 |
| WI_N_BR3S | L3M | 77.6 | 77.7 | 2087.5 | 17274.5 | 77224.2 | 109668.7 | -122330.0 |
| WI_N_BR3S | L6M | 77.6 | 77.7 | 68.4 | 17274.5 | 77224.2 | 147059.4 | -167919.2 |
| WI_N_BR3S | HOLD | 39.5 | 39.8 | -3486.8 | 47706.1 | 78842.0 | 151518.0 | -171076.8 |

## Behaviour-targeted use (standing principle 19:45Z): flag acts only on a same-side P7 re-entry after a P7 loser (within 120 min, same session list)
There are 651 such re-entries in 4,958 P7 trades (mean -$54 per trade against +$216 for all other P7 trades). Skipping all of them cuts the L6M stack drawdown by only -2.0 percent (HOLD -14.2, PRE 13.7, X-prime -1.8) and removes $48k of best-20-week winners against $65k of worst-20-week losers; half-size: L6M -0.8, HOLD -4.6. Best flag-conditioned re-entry cells (minimum equal-mean cut over four windows) are all below 9 percent and flag fewer than 300 trades: no robust cell.

## Behavioural scorecard (W-Q tool, exact trades, L6M, whole stack, per week)
- JN04RM L6M (stack, per week): full stops 25.4/wk $-38130; give-backs 9.9/wk (9.8 round-trips) realised $-11306, forgone vs target $28091; same-side losing runs max 13, p95 7, $-42885 lost on 3rd-and-later; no-new-evidence re-entries 43.3/wk $1885; recoveries cut 15.2/wk $39718, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4296/wk, losers avoided $4285/wk, net -254 $/wk; pnl $19530/wk.
- WI_G_BR3S L6M (stack, per week): full stops 25.4/wk $-38297; give-backs 9.8/wk (9.7 round-trips) realised $-11293, forgone vs target $27911; same-side losing runs max 13, p95 6, $-39955 lost on 3rd-and-later; no-new-evidence re-entries 39.2/wk $1185; recoveries cut 14.7/wk $37599, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $19408/wk, losers avoided $18264/wk, net -393 $/wk; pnl $19137/wk.
- WI_I_ON15S L6M (stack, per week): full stops 25.2/wk $-37911; give-backs 9.6/wk (9.5 round-trips) realised $-10923, forgone vs target $27074; same-side losing runs max 13, p95 6, $-39365 lost on 3rd-and-later; no-new-evidence re-entries 40.4/wk $1166; recoveries cut 14.9/wk $38252, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $13267/wk, losers avoided $9756/wk, net -1477 $/wk; pnl $18053/wk.
- WI_I_ON2S L6M (stack, per week): full stops 25.2/wk $-37942; give-backs 9.5/wk (9.4 round-trips) realised $-10702, forgone vs target $26691; same-side losing runs max 13, p95 6, $-37527 lost on 3rd-and-later; no-new-evidence re-entries 39.8/wk $1571; recoveries cut 14.7/wk $37637, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $16129/wk, losers avoided $13422/wk, net -264 $/wk; pnl $19266/wk.
- WI_J_BR3S L6M (stack, per week): full stops 25.4/wk $-38252; give-backs 9.8/wk (9.7 round-trips) realised $-11326, forgone vs target $27992; same-side losing runs max 13, p95 7, $-40619 lost on 3rd-and-later; no-new-evidence re-entries 41.2/wk $1521; recoveries cut 14.9/wk $37941, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $17749/wk, losers avoided $17043/wk, net -65 $/wk; pnl $19465/wk.
- WI_J_BR3T45 L6M (stack, per week): full stops 25.4/wk $-38231; give-backs 9.4/wk (9.2 round-trips) realised $-10360, forgone vs target $25562; same-side losing runs max 13, p95 7, $-43327 lost on 3rd-and-later; no-new-evidence re-entries 43.5/wk $2281; recoveries cut 15.3/wk $40661, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2538/wk, losers avoided $2277/wk, net -509 $/wk; pnl $19021/wk.
- WI_J_ES60S L6M (stack, per week): full stops 25.3/wk $-38028; give-backs 9.4/wk (9.2 round-trips) realised $-10669, forgone vs target $26478; same-side losing runs max 13, p95 7, $-41534 lost on 3rd-and-later; no-new-evidence re-entries 41.5/wk $1546; recoveries cut 14.8/wk $38563, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $8392/wk, losers avoided $7033/wk, net -1226 $/wk; pnl $18305/wk.
- WI_J_NQ60S L6M (stack, per week): full stops 25.3/wk $-37976; give-backs 9.5/wk (9.4 round-trips) realised $-10704, forgone vs target $26709; same-side losing runs max 13, p95 6, $-39788 lost on 3rd-and-later; no-new-evidence re-entries 40.2/wk $2380; recoveries cut 14.6/wk $37653, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $13575/wk, losers avoided $12103/wk, net -1658 $/wk; pnl $17872/wk.
- WI_J_RS15H L6M (stack, per week): full stops 25.4/wk $-38034; give-backs 9.9/wk (9.8 round-trips) realised $-10915, forgone vs target $27124; same-side losing runs max 13, p95 7, $-42321 lost on 3rd-and-later; no-new-evidence re-entries 44.0/wk $1533; recoveries cut 15.5/wk $38697, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $342/wk, losers avoided $539/wk, net -941 $/wk; pnl $18589/wk.
- WI_J_RS30H L6M (stack, per week): full stops 25.5/wk $-38276; give-backs 9.9/wk (9.8 round-trips) realised $-11002, forgone vs target $27348; same-side losing runs max 13, p95 7, $-42920 lost on 3rd-and-later; no-new-evidence re-entries 44.1/wk $1686; recoveries cut 15.3/wk $37636, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $208/wk, losers avoided $295/wk, net -1509 $/wk; pnl $18021/wk.
- WI_J_RS30T35 L6M (stack, per week): full stops 25.5/wk $-38189; give-backs 9.2/wk (9.1 round-trips) realised $-10401, forgone vs target $25868; same-side losing runs max 13, p95 6, $-40963 lost on 3rd-and-later; no-new-evidence re-entries 43.5/wk $2955; recoveries cut 14.9/wk $39205, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $2441/wk, losers avoided $1922/wk, net +363 $/wk; pnl $19893/wk.
- WI_K_DOW1AS L6M (stack, per week): full stops 25.4/wk $-37932; give-backs 9.6/wk (9.5 round-trips) realised $-10431, forgone vs target $25863; same-side losing runs max 13, p95 6, $-35717 lost on 3rd-and-later; no-new-evidence re-entries 40.0/wk $1543; recoveries cut 14.2/wk $34685, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $21275/wk, losers avoided $18005/wk, net -2901 $/wk; pnl $16629/wk.
- WI_K_W2AS L6M (stack, per week): full stops 25.4/wk $-38081; give-backs 9.9/wk (9.8 round-trips) realised $-10968, forgone vs target $27363; same-side losing runs max 13, p95 6, $-41119 lost on 3rd-and-later; no-new-evidence re-entries 42.2/wk $2243; recoveries cut 14.9/wk $37388, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $5402/wk, losers avoided $5430/wk, net +40 $/wk; pnl $19570/wk.
- WI_K_W2AT45 L6M (stack, per week): full stops 25.4/wk $-38181; give-backs 9.8/wk (9.6 round-trips) realised $-10892, forgone vs target $27140; same-side losing runs max 13, p95 7, $-42691 lost on 3rd-and-later; no-new-evidence re-entries 43.8/wk $2743; recoveries cut 15.3/wk $39223, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $1220/wk, losers avoided $737/wk, net +251 $/wk; pnl $19781/wk.
- WI_K_W2S L6M (stack, per week): full stops 25.2/wk $-37882; give-backs 9.6/wk (9.5 round-trips) realised $-10649, forgone vs target $26653; same-side losing runs max 11, p95 6, $-38739 lost on 3rd-and-later; no-new-evidence re-entries 40.2/wk $2632; recoveries cut 14.3/wk $35693, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $9109/wk, losers avoided $8854/wk, net +64 $/wk; pnl $19594/wk.
- WI_L_PB13H L6M (stack, per week): full stops 25.4/wk $-38019; give-backs 9.9/wk (9.8 round-trips) realised $-10640, forgone vs target $26459; same-side losing runs max 13, p95 6, $-42157 lost on 3rd-and-later; no-new-evidence re-entries 44.4/wk $1951; recoveries cut 15.5/wk $36873, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $391/wk, losers avoided $787/wk, net -1130 $/wk; pnl $18400/wk.
- WI_L_PB18S L6M (stack, per week): full stops 25.2/wk $-37803; give-backs 9.1/wk (9.0 round-trips) realised $-10387, forgone vs target $25913; same-side losing runs max 10, p95 6, $-37541 lost on 3rd-and-later; no-new-evidence re-entries 37.4/wk $2805; recoveries cut 13.9/wk $34898, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $18204/wk, losers avoided $19048/wk, net +266 $/wk; pnl $19796/wk.
- WI_L_PUSHH L6M (stack, per week): full stops 25.5/wk $-38238; give-backs 10.0/wk (9.9 round-trips) realised $-10608, forgone vs target $26098; same-side losing runs max 13, p95 7, $-42784 lost on 3rd-and-later; no-new-evidence re-entries 44.4/wk $2049; recoveries cut 15.5/wk $37935, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $439/wk, losers avoided $976/wk, net -791 $/wk; pnl $18739/wk.
- WI_L_SL13S L6M (stack, per week): full stops 25.4/wk $-38216; give-backs 9.1/wk (9.0 round-trips) realised $-10347, forgone vs target $25489; same-side losing runs max 13, p95 6, $-40201 lost on 3rd-and-later; no-new-evidence re-entries 39.8/wk $2445; recoveries cut 14.2/wk $35279, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $19867/wk, losers avoided $18845/wk, net +289 $/wk; pnl $19819/wk.
- WI_L_SL13T35 L6M (stack, per week): full stops 25.4/wk $-38129; give-backs 8.9/wk (8.8 round-trips) realised $-10063, forgone vs target $24777; same-side losing runs max 13, p95 7, $-42080 lost on 3rd-and-later; no-new-evidence re-entries 43.3/wk $1104; recoveries cut 15.0/wk $39004, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $4078/wk, losers avoided $2538/wk, net -622 $/wk; pnl $18908/wk.
- WI_L_SL19H L6M (stack, per week): full stops 25.5/wk $-38226; give-backs 9.8/wk (9.8 round-trips) realised $-10964, forgone vs target $27065; same-side losing runs max 13, p95 7, $-43009 lost on 3rd-and-later; no-new-evidence re-entries 43.7/wk $1831; recoveries cut 15.3/wk $38631, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $13/wk, losers avoided $174/wk, net -390 $/wk; pnl $19140/wk.
- WI_N_BR3S L6M (stack, per week): full stops 21.6/wk $-34323; give-backs 8.3/wk (8.3 round-trips) realised $-9141, forgone vs target $23997; same-side losing runs max 14, p95 6, $-29442 lost on 3rd-and-later; no-new-evidence re-entries 32.2/wk $-997; recoveries cut 14.7/wk $37905, clipped fills 0.0/wk $0; vs JN04RM: winners skipped $44763/wk, losers avoided $44405/wk, net -1811 $/wk; pnl $17719/wk.

Plain reading: an entry gate leaves the three defects (full stops, give-backs, same-side losing runs) where they were, because it only removes entries and the entries it removes are not the ones that form the runs; by the standing principle families I-L are therefore NOT acceptable as exits or re-entry fixes on their own. Their use is as evidence tests inside the re-entry rule (W-M probe / confirm).

## Follow-up (lead request 2026-11-12): HOLD for L6M-positive sets, BR3S stacked on WG_E1 and JN05W_E1, BR3S on the LPB base, overlap with no-new-evidence re-entries
1. HOLD (JN04RM base, maxDD cut percent / mean change per week) for the L6M-positive sets: J_NQ60S 6.1 / +506; J_BR3S 19.0 / +442; L_PUSHH 20.2 / -342; L_PB13H 7.7 / +221; I_ON2S 5.2 / -818; K_W2AS -4.9 / -574 (fails); K_W2S -5.4 / -41 (fails); J_RS30T35 -0.5 / +90 (flat). Still running or queued when this was written: PRE and X-prime only for BR3S (done: PRE 5.2, X-prime 4.3); no other set has PRE/X-prime because none but BR3S and PUSHH is positive on both L6M and HOLD, and PUSHH costs mean (-342 per week).
2. Stacked on top of the new-evidence rule (exact, one set per job, reference = the base itself; the set json is the base set plus the gate, so any base dial in the mixin is the same as the base set): on WG_E1 (WI_G_BR3S) L6M cut 13.5 percent, mean 616.1 per week, worst-5-week delta 30587.0, best-5-week delta -62617.4; HOLD cut 17.0, mean 109.2. On JN05W_E1 (WI_N_BR3S) L6M cut 32.9 percent (maxDD 17.3k vs 25.7k), mean 828.5 per week, worst-5 9572.9, best-5 -38564.0; HOLD cut 26.5, mean -318.5 per week. So the gate is additive on top of both: on JN05W_E1 it takes the L6M drawdown down by a third at roughly equal mean (+829 L6M, -319 HOLD).
3. Cost e (scorecard tool, L6M, per week, vs the base set): on JN05W_E1 the gate skips $15.9k of winners and avoids $14.9k of losers per week, net +$248 per week; on WG_E1 it skips $18.4k of winners and avoids $17.0k of losers, net -$219 per week. The worst-5-week gain is large (+$9.6k on JN05W_E1) and the best-5-week loss larger (-$38.6k): it gives up trend-week winners and the net is about zero in dollars while the drawdown falls. Frozen live week, first-order replay: $30.2k of winners removed, week stays +$54.6k.
4. Behavioural scorecard on the stacked sets (L6M): JN05W_E1 full stops 21.5 per week, give-backs 8.6, same-side run max 14 / p95 6, no-new-evidence re-entries 34.9 per week; with the gate 21.6, 8.3, 14 / 6, 32.2. WG_E1 25.4, 9.9, 13 / 6, 40.8; with the gate 25.4, 9.8, 13 / 6, 39.2. The gate does not change the defects (a, b, c) and trims d by 8 percent: it is a drawdown dial, not a behaviour fix.
5. BR3S on the LPB base (WIL_J_BR3S, no JN dials), L6M: maxDD cut 20.0 percent vs LPB, mean 1286.7 per week, worst-5 delta 2186.2, best-5 delta -34997.7. Against JN04RM it deepens the drawdown (-48.2), as expected, because it lacks the JN dials.
6. Overlap with the no-new-evidence same-side re-entries (exact JN04RM P7 trades, /mnt/l2/l2vast/_th_works_i/overlap.md): L6M 380 breadth-3 entries and 343 no-new-evidence entries share only 5 trades (1 percent either way, those 5 lost $4.2k); HOLD 723 vs 547 share 8. The two rules therefore act on different entries (extended first entries vs re-entries after a failure that never made a new extreme), which is why they stack. Note that both sets are net winners overall in these windows (breadth-3 entries +$18.0k L6M, no-new-evidence entries +$28.1k L6M): skipping either removes more winners than losers in dollars, and the benefit is only in the drawdown path.



## M. (W-M) (M)

Source DS3_WORKS_M.md (mtime 2026-11-11T19:35:53Z UTC), included verbatim, read only:

# DS3_WORKS_M - T-WORKS / P7 FIX families M N O P (adaptive response, side-level stack governor, the flip, no-follow-through exit), W-M

Page stamp 2026-11-11T19:35Z. Label: PRE-PROOF, post-hoc, Shadow only, no PASS claims. Prereg autopilot/WORKS_M_PREREG.md (sha in DECISIONS.md before any cell). Code code/th_works_m/ (private tree). Reference stacks: LPB_BASE (live panel base) and JN04RM.

## Plain-sentence summary (first page, first-order only; exact sets are queued and no exact number exists yet)
Status: the hooks for all four families are written (code/th_works_m/m_hooks.py: probe, stricter confirm after a loss, side governor, flip, no-follow-through exit) and 24 exact sets (WM_*) are queued one set per job on LPB_BASE through m_mgr.py. ACTUALLY LAUNCHED at 19:36Z: 1 set (WM_N1, 0 of 6 L6M months finished); FINISHED: 0 months of any set; the box had 5-67 GB free and jobs wait on the 50-62 GB gates. Queue priority per lead: C1-C4 stricter confirm, D2 re-arm on evidence (new session extreme since the last failure), N1. The hooks have not yet run once in the engine: WM_T2 (all features on, 202610) and the identity set WM_T1 are the first proofs and must pass before any exact row is believed. JN04RM versions (WMJ_) follow after the LPB winners.
Family O (the flip): dead at first order. After two failed same-side P7 exits in a session the opposite-side signal earns 54 USD per lot (n=116, 45.7 percent wins) against 61 USD per lot for all P7 signals, so it is not a better-than-average signal; sizing it up 1.5x or 2x gives L6M cut -2.5 to -2.8 and costs the live week. The same-side signal after two failures earns -16 USD per lot (n=98): blocking it removes 11.6k of losses but also trend winners, L6M eq-cut about 0.
Family N (side governor): only fires at 0.5R or 0.75R of one-side realised loss (P7 day cap 8,400 = 1R means 1R or more almost never prints). Best: block P7 after 0.5R P7 net loss on that side, release on a new session extreme: eq-cut L6M 14.1, PRE 8.6, HOLD 9.6, 75 trades changed; it removes 15.8k of trend-week winners against 6.9k of worst-week losses and costs 22.7k in the frozen live week. The stack-wide loss count (all books, block P7) gives PRE 18 but L6M 4.6 and takes 88.7k from trend weeks.
Family M (probe / blackout): the plain blackout beats the probe at first order. Both-side 120-minute blackout: eq-cut L6M 37.3, PRE 33.6, HOLD 15.2, but it removes 178k from trend weeks and costs 41k in the live week. Probe at 0.5 after a loss, both sides, restore after the probe wins: L6M 16.6, PRE 30.0, HOLD 11.3, live week -15.9k; probe at 1 lot is lighter on the live week (-28k) with less benefit. Stricter confirm (90-s confirm, 2-3 L2 confirmations) cannot be scored first-order; exact sets WM_C1-C4 are queued.
Family P (no-follow-through exit): on all P7 trades it fails (mean -9.5k per week, trend weeks -705k). Restricted to the 3rd-and-later P7 trade of a session: exit if MFE < 12 pt after 3 minutes gives eq-cut L6M 9.8, PRE 20.9, HOLD 6.1 (841 trades, worst-20 weeks +135k, trend weeks -219k, live week -22k); Asia only, 5 minutes: 11.0 / 19.7 / 12.8, live week -19k. On M7 the chase-flagged version raises the mean (L6M +1.4k per week, eq-cut 25.8 at X=10, N=5) but PRE is near 7; K7 and U7 show little (fo_PK.csv).
Behavioural scorecard (interim, P7, first-order, my own m_card.py until W-Q's tool exists; card_fo.csv): LPB_BASE L6M has 0.4 full stops per week (-1.2k per week), 2.9 give-backs per week (MFE >= 80 percent of target, closed below 50 percent; -7.6k per week), 2.7 round-trips per week, a maximum of 5 consecutive same-side losing entries in one session and -37.4k lost on the 3rd-and-later; the frozen live week has 3 give-backs (-13.0k). The families M, N, O act on item (c) only: the 3rd-and-later loss falls to -15.3k (30-min blackout), 0 (120-min both-side blackout), -13.6k (probe 1 lot), -13.8k (N3), -19.2k (N1), unchanged for the same-side block after two failures; none of them moves full stops or give-backs by half, except the 120-minute both-side blackout (give-backs 1.5 per week, full stops 0.2) which pays for it with 41k of the live week and 178k of trend weeks. Verdict at first order: no M, N or O cell passes the standing gate (a, b, c each halved without (e) exceeding the saving, trend week not turned losing); item (b) needs a profit-side rule, not a re-entry rule. Exact numbers and the worst-10 session replay follow on the next pages.
Expressible in v1.7 today: only the plain P7 post-exit blackout (PostExitBlackoutMins, same side) and the P7 session string; probe, side governor, flip, stricter confirm and no-follow-through exit need v1.8 fields (session loss counter per side, probe-lots-after-loss with restore-on-win, per-side session governor limit in R with release on new session extreme, confirm strictness after a loss, per-trade follow-through clock). Worked rows come with the first exact winner.
Dead-lookup: no prior row for these families (hits for 'flip', 'mfe', 'stall' were profit-side HMM/EXP1/THPC cells on other books). Addendum logged in DECISIONS.md: N grid extended to 0.5R/0.75R, P first pass on roll-adjusted bars voided and rerun on raw bars.

## First-order tables (equal-lot trade list, 3.5 years of LPB_BASE trades plus the 180 frozen-week rows; ranking only, exact decides)
Columns: eqcut_* = stack maxDD cut at equal mean (percent, window L6M/PRE/HOLD), cut_* = plain maxDD cut, dmean_L6M = weekly mean change in USD, n_chg = trades changed (3.5 years), d_worst20 / d_trend20 = P&L change in the 20 worst / 20 best P7 weeks (positive = the rule removed losses; negative = it removed winners), live_d = change in the frozen live week 11-01..05.

### N side-level stack governor (192 cells) - top 10 by min(eq-cut L6M, eq-cut PRE), HOLD eq-cut > -5
| cell | eqcut_L6M | eqcut_PRE | eqcut_HOLD | cut_L6M | cut_PRE | cut_HOLD | cut_X' | dmean_L6M | n_chg | d_worst20 | d_trend20 | live_d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| N|X=0.5R|act=block|loss=p7|apply=p7|sess=all|release=False | 10.8 | 9.0 | 6.1 | 9.2 | 7.3 | 4.4 | -6.8 | 313.4 | 113 | -126.6 | -34534.8 | -41883.9 |
| N|X=0.5R|act=block|loss=p7|apply=p7|sess=all|release=True | 14.1 | 8.6 | 9.6 | 9.2 | 3.4 | 4.4 | -6.8 | 1068.4 | 75 | 6853.3 | -15829.2 | -22715.8 |
| N|X=0.5R|act=block|loss=p7|apply=p7|sess=asia|release=True | 12.3 | 6.7 | 7.7 | 9.2 | 3.4 | 4.4 | -6.8 | 656.1 | 55 | 9250.9 | -13213.8 | -24610.1 |
| N|X=0.5R|act=block|loss=p7|apply=all|sess=all|release=True | 12.1 | 6.0 | -0.8 | 8.7 | 2.3 | -4.7 | -4.0 | 731.7 | 269 | 2753.6 | -10989.1 | -25733.0 |
| N|X=0.5R|act=block|loss=p7|apply=p7|sess=asia|release=False | 7.7 | 5.8 | 2.8 | 9.2 | 7.3 | 4.4 | -6.8 | -293.1 | 85 | 3469.8 | -33984.4 | -43778.3 |
| N|X=0.5R|act=half|loss=p7|apply=p7|sess=all|release=False | 5.4 | 5.7 | 3.7 | 4.0 | 4.3 | 2.2 | -2.9 | 271.9 | 104 | 3661.3 | -10920.8 | -18468.7 |
| N|X=0.5R|act=half|loss=p7|apply=p7|sess=all|release=True | 6.3 | 4.8 | 4.6 | 4.0 | 2.3 | 2.2 | -2.9 | 479.5 | 70 | 5054.0 | -5089.9 | -9941.1 |
| N|X=0.5R|act=block|loss=all|apply=p7|sess=all|release=False | 4.6 | 19.0 | 1.0 | 3.4 | 18.0 | -0.2 | -9.2 | 222.1 | 344 | 15047.7 | -88722.7 | -44114.7 |
| N|X=0.5R|act=block|loss=p7|apply=all|sess=asia|release=True | 7.9 | 4.0 | -2.9 | 6.3 | 2.3 | -4.7 | -4.0 | 332.5 | 225 | 5151.2 | -9602.3 | -27627.4 |
| N|X=0.5R|act=half|loss=p7|apply=p7|sess=asia|release=True | 5.4 | 3.8 | 3.7 | 4.0 | 2.3 | 2.2 | -2.9 | 289.1 | 53 | 5054.0 | -4381.6 | -10888.3 |

### M probe after a loss and plain blackout reference (52 cells) - top 10 by min(eq-cut L6M, eq-cut PRE), HOLD eq-cut > -5
| cell | eqcut_L6M | eqcut_PRE | eqcut_HOLD | cut_L6M | cut_PRE | cut_HOLD | cut_X' | dmean_L6M | n_chg | d_worst20 | d_trend20 | live_d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| M|blackout=120|same=False|sess=all | 37.3 | 33.6 | 15.2 | 31.6 | 27.5 | 7.5 | -20.0 | 1945.0 | 1759 | 255222.0 | -177880.1 | -41310.3 |
| M|blackout=15|same=False|sess=all | 28.8 | 25.8 | -1.5 | 19.6 | 16.3 | -14.5 | -2.8 | 2194.7 | 432 | 66591.1 | -26316.9 | -600.0 |
| M|blackout=15|same=False|sess=asia | 19.4 | 21.8 | -4.8 | 17.2 | 19.7 | -7.7 | -0.3 | 588.2 | 180 | 51733.6 | -28812.4 | -5278.7 |
| M|probe=0.5|scope=both|restore=probe|sess=all | 16.6 | 30.0 | 11.3 | 8.4 | 23.1 | 2.6 | -0.9 | 1716.4 | 1220 | 100789.1 | -51260.0 | -15860.4 |
| M|probe=0.5|scope=both|restore=anywin|sess=all | 16.6 | 30.0 | 11.3 | 8.4 | 23.1 | 2.6 | -0.9 | 1716.4 | 1220 | 100789.1 | -51260.0 | -15860.4 |
| M|blackout=120|same=False|sess=asia | 10.7 | 11.6 | 10.6 | 5.9 | 6.8 | 5.9 | -27.3 | 1149.8 | 826 | 183828.8 | -133948.5 | -29365.8 |
| M|probe=1|scope=both|restore=probe|sess=all | 9.8 | 18.9 | 11.6 | 5.4 | 14.9 | 7.3 | -13.1 | 805.8 | 1220 | 165925.0 | -91596.2 | -28346.4 |
| M|probe=1|scope=both|restore=anywin|sess=all | 9.8 | 18.9 | 11.6 | 5.4 | 14.9 | 7.3 | -13.1 | 805.8 | 1220 | 165925.0 | -91596.2 | -28346.4 |
| M|blackout=15|same=True|sess=all | 8.9 | 26.0 | 0.1 | 1.1 | 19.6 | -8.5 | -2.9 | 1469.4 | 212 | 31625.9 | -996.6 | -600.0 |
| M|probe=0.5|scope=same|restore=probe|sess=all | 8.9 | 20.9 | -0.1 | 7.6 | 19.8 | -1.5 | 2.8 | 295.7 | 648 | 43594.7 | -24377.1 | -10648.9 |

### O flip (28 cells)
Flip statistics (mean P&L per lot of the flip signal versus all P7 signals and versus the same-side signal after the same failures):
| cell | n_flip | flip_mean_per_lot | flip_win | all_p7_mean_per_lot | all_p7_win | same_n | same_mean_per_lot | same_win |
|---|---|---|---|---|---|---|---|---|
| Ostat|k=2|sess=all | 116.0 | 54.21 | 0.46 | 61.26 | 0.45 | 98.0 | -15.77 | 0.42 |
| Ostat|k=2|sess=asia | 56.0 | 42.77 | 0.45 | 64.83 | 0.45 | 40.0 | -248.11 | 0.35 |
| Ostat|k=3|sess=all | 13.0 | 117.78 | 0.46 | 61.26 | 0.45 | 13.0 | -442.98 | 0.31 |
| Ostat|k=3|sess=asia | 8.0 | -51.53 | 0.38 | 64.83 | 0.45 | 7.0 | -670.73 | 0.29 |

### O flip (28 cells) - top 10 by min(eq-cut L6M, eq-cut PRE), HOLD eq-cut > -5
| cell | eqcut_L6M | eqcut_PRE | eqcut_HOLD | cut_L6M | cut_PRE | cut_HOLD | cut_X' | dmean_L6M | n_chg | d_worst20 | d_trend20 | live_d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| O|k=2|flip_m=full|sess=asia | 1.3 | 16.8 | 3.3 | 0.0 | 15.7 | 2.1 | 0.0 | 236.1 | 40.0 | 8335.4 | -4099.4 | -0.0 |
| O|k=3|flip_m=2.0|sess=all | 0.8 | 6.7 | 0.8 | 0.0 | 6.0 | 0.0 | 0.0 | 143.9 | 13.0 | 2565.4 | 721.9 | -0.0 |
| O|k=2|flip_m=2.0|sess=all | 1.1 | 0.8 | 3.1 | -2.8 | -3.1 | -0.7 | -4.4 | 691.9 | 116.0 | -23118.5 | -1853.6 | 8351.1 |
| O|k=3|flip_m=1.5|sess=all | 0.5 | 4.1 | 0.5 | 0.0 | 3.6 | 0.0 | 0.0 | 95.9 | 13.0 | 1881.3 | -38.9 | -0.0 |
| O|k=3|flip_m=full|sess=all | 0.3 | 11.1 | 0.3 | 0.0 | 10.8 | 0.0 | 0.0 | 48.0 | 10.0 | 10782.7 | -57.8 | -0.0 |
| O|k=3|flip_m=2.0|sess=asia | 0.0 | 6.0 | 0.0 | 0.0 | 6.0 | 0.0 | 0.0 | 0.0 | 8.0 | 5989.1 | -3278.7 | -0.0 |
| O|k=3|flip_m=full|sess=asia | 0.0 | 10.8 | 0.0 | 0.0 | 10.8 | 0.0 | 0.0 | 0.0 | 6.0 | 10782.7 | -2459.0 | -0.0 |
| O|k=3|flip_m=1.5|sess=asia | 0.0 | 3.6 | 0.0 | 0.0 | 3.6 | 0.0 | 0.0 | 0.0 | 8.0 | 3593.1 | -1639.4 | -0.0 |
| O|k=2|same_side_m=0.5|sess=all | -0.0 | 4.7 | -1.9 | 0.0 | 4.7 | -1.9 | 0.0 | -0.8 | 70.0 | 413.6 | -2441.1 | -8192.3 |
| O|k=3|same_side_m=0.5|sess=all | -0.1 | 1.7 | -0.1 | 0.0 | 1.8 | 0.0 | 0.0 | -25.3 | 10.0 | -564.3 | -326.6 | -2387.8 |

### P no-follow-through exit on P7 (370 cells) - top 10 by min(eq-cut L6M, eq-cut PRE), HOLD eq-cut > -5
| cell | eqcut_L6M | eqcut_PRE | eqcut_HOLD | cut_L6M | cut_PRE | cut_HOLD | cut_X' | dmean_L6M | n_chg | d_worst20 | d_trend20 | live_d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| P|mfe|X=12|N=5|scope=late3|sess=asia | 11.0 | 19.7 | 12.8 | 14.6 | 23.0 | 16.3 | -2.2 | -692.4 | 406 | 73435.7 | -222842.2 | -19405.2 |
| P|mfe|X=5|N=5|scope=late3|sess=asia | 10.4 | 21.0 | 12.3 | 8.7 | 19.5 | 10.6 | -3.2 | 331.6 | 213 | 67888.7 | -127551.4 | 3744.0 |
| P|mfe|X=12|N=3|scope=late3|sess=all | 9.8 | 20.9 | 6.1 | 18.0 | 28.0 | 14.6 | 1.9 | -1542.5 | 841 | 135366.8 | -218754.3 | -22384.2 |
| P|mfe|X=12|N=3|scope=late3|sess=asia | 9.0 | 16.0 | 10.9 | 14.6 | 21.1 | 16.4 | -2.0 | -1050.6 | 488 | 101304.0 | -231587.3 | -27821.6 |
| P|mfe|X=8|N=5|scope=late3|sess=asia | 5.8 | 16.3 | 7.7 | 13.8 | 23.4 | 15.6 | -5.3 | -1455.0 | 300 | 87392.7 | -171866.9 | -1491.8 |
| P|mfe|X=12|N=5|scope=late3|sess=all | 4.1 | 24.5 | 6.0 | 9.1 | 28.5 | 11.0 | 1.8 | -899.1 | 694 | 104857.2 | -210539.2 | -16136.4 |
| P|mfe|X=5|N=8|scope=late3|sess=asia | 1.0 | 16.0 | 3.0 | 3.7 | 18.3 | 5.7 | -3.4 | -593.1 | 160 | 46488.2 | -105250.4 | 2924.0 |
| P|mfe|X=10|N=5|scope=late3|sess=asia | 0.5 | 13.5 | 2.5 | 8.4 | 20.3 | 10.3 | -2.2 | -1359.7 | 357 | 71356.7 | -212591.7 | -14709.2 |
| P|mfe|X=5|N=10|scope=late3|sess=asia | 0.0 | 13.8 | 2.1 | 2.4 | 15.8 | 4.4 | -3.3 | -511.2 | 143 | 43854.2 | -80295.6 | 2784.0 |
| P|mfe|X=12|N=5|scope=reentry|sess=all | -1.4 | 5.3 | -3.9 | 11.7 | 17.5 | 9.5 | -13.0 | -2199.8 | 997 | 112590.6 | -306735.5 | -37107.0 |

### P no-follow-through exit on K7/M7/U7 (444 cells) - top 10 by min(eq-cut L6M, eq-cut PRE), HOLD eq-cut > -5
| cell | eqcut_L6M | eqcut_PRE | eqcut_HOLD | cut_L6M | cut_PRE | cut_HOLD | cut_X' | dmean_L6M | n_chg | d_worst20 | d_trend20 | live_d |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PM7|mfe|X=5|N=3|scope=chase|sess=all | 18.0 | 10.6 | 10.4 | 13.9 | 6.1 | 5.9 | 0.3 | 797.3 | 1163 | 22087.0 | -43147.0 | -3282.0 |
| PM7|mfe|X=8|N=3|scope=chase|sess=all | 19.4 | 8.8 | 11.2 | 16.5 | 5.5 | 8.1 | -0.9 | 564.5 | 1543 | 32255.0 | -56200.5 | -101.8 |
| PM7|mfe|X=10|N=3|scope=chase|sess=all | 17.7 | 8.2 | 13.3 | 14.9 | 5.1 | 10.4 | -7.7 | 536.1 | 1760 | 26033.0 | -60006.5 | -3754.0 |
| PM7|mfe|X=10|N=5|scope=chase|sess=all | 25.8 | 7.2 | 13.2 | 20.3 | 0.3 | 6.8 | -5.8 | 1366.3 | 1473 | 14624.0 | -42846.5 | -4783.0 |
| PM7|mfe|X=5|N=5|scope=chase|sess=all | 20.1 | 7.1 | 10.3 | 14.7 | 0.7 | 4.1 | -4.4 | 1092.1 | 933 | 5802.5 | -30407.0 | -3599.0 |
| PM7|mfe|X=10|N=2|scope=chase|sess=all | 14.3 | 6.9 | 12.2 | 13.5 | 6.0 | 11.4 | -8.2 | 175.6 | 2014 | 17802.5 | -56532.5 | -2063.8 |
| PM7|mfe|X=12|N=5|scope=chase|sess=all | 25.4 | 6.2 | 18.9 | 21.0 | 0.7 | 14.2 | -9.6 | 1088.9 | 1661 | 8879.0 | -43581.0 | -4362.0 |
| PM7|mfe|X=12|N=3|scope=chase|sess=all | 19.8 | 6.1 | 17.2 | 18.2 | 4.3 | 15.6 | -7.2 | 361.3 | 1943 | 17992.5 | -55481.0 | -3754.0 |
| PM7|mfe|X=5|N=3|scope=all|sess=all | 11.7 | 5.7 | 7.0 | 8.2 | 2.0 | 3.3 | -8.8 | 627.3 | 1629 | 25605.0 | -53862.0 | -7954.0 |
| PM7|mfe|X=15|N=5|scope=chase|sess=all | 30.9 | 5.0 | 19.3 | 25.8 | -2.1 | 13.2 | -9.5 | 1379.9 | 1907 | 16153.5 | -47900.0 | -4362.0 |



## Q. Ranker, joint stage, minimal rule set (W-Q) (Q)

Source DS3_WORKS_Q.md (mtime 2026-11-12T11:31:02Z UTC), included verbatim, read only:

# DS3_WORKS_Q - W-Q (family Q ranker + JOINT STAGE), page 0, 2026-11-11 19:20Z (date -u). Shadow only, post-hoc, no PASS claim.
Prereg autopilot/WORKS_Q_PREREG.md (sha256 bc9d2cde..., DECISIONS.md 19:14Z). Code outputs/code/th_works_q/q_rank.py and q_registry.py; outputs /mnt/l2/l2vast/_th_works/q/.

## Status in plain sentences
1. The ranker harness is built and ran once on the features that exist today (22 causal columns of the C1 table: ER, ATR, atr_rel, ADX, session move, TWAP slope/dev, P7 order/gap/last pnl, K/U/M same/opp side, calmar10, lots, session, side). It is a purged expanding walk-forward, refit every 2 label-weeks from 2024-04-01, label = the P7 trade ended in Target, a 12-leaf monotone LightGBM (3 seeds) and a 6-leaf tree (3 seeds), and a 20-shuffle family null (labels shuffled within month, same pipeline). Out-of-fold AUC is 0.534-0.538 for the GBDT and 0.509 for the tree.
2. Result today (first-order, trade level, equal-lot removal, NOT exact): skipping the bottom decile changes P7 by +$739 per week in L6M (null mean -$1,320, null 95th percentile +$732), +$197 in HOLD (null 95th +$648), +$431 in PRE (null 95th +$444); skipping the bottom quintile and halving the next gives +$470 L6M, -$349 HOLD, -$78 PRE. The 6-leaf tree is negative in every window (-$1.6k to -$4.9k per week). So on the current features the ranker is at the family-null edge, not above it: no lead. The null mean is negative because skipping random trades from a positive-mean book costs money, so the honest comparison is the null 95th percentile.
3. Top features by gain (GBDT mean over seeds): lots, p7_gap_min (minutes since the last P7 exit), atr_rel, p7_last_pnl, twap_dev, atr5, adx5, session move. Nothing yet is expressible as 2-3 plain conditions beyond what C1 already said (lots, re-entry gap, vol state). The X' window (2023-04..2024-01) has no out-of-fold scores because the first fold is 2024-04: X' is empty for Q by construction until a shorter warm-up is tried.
4. Not done: the E/F/G/H/I/J/K/L/M/N/O/P feature tables have not landed (shared table p7_signal_features.parquet and p7_feat_*.parquet are absent; the _th_works/e and /i directories exist but are empty at 19:17Z). q_rank.py joins them automatically on sig_ts / utc_epoch_s when they appear, and the ranker must be re-run then, including untaken signals if W-E supplies them (today it ranks taken trades only, so it cannot see signals the live blackout or caps already skipped).
5. Joint registry: /mnt/l2/l2vast/_th_works/q/joint_registry.tsv, rebuilt by `python3 -I code/th_works_q/q_registry.py` (read-only on others' files). It holds 18 exact rows today (W-A A1 3, A2 5, A-composites 2, W-C C3/C4 6, others 2) with windows done, L6M/HOLD/PRE maxDD cut and mean; top3 flag per family and reference. W-B rows are in its DS3 page and drive logs, not yet in a score csv, so they are not in the registry: to be added when W-B publishes one.
6. The joint stage has NOT started. Budget stated honestly: exact throughput is about 35-40 cell-months per worker per hour with a shared cap, and MemAvail was 34 GB at 19:17Z (below the 40 GB guard), so no exact worker was launched by W-Q. 2,000 exact stacks x even one window (6 months) = 12,000 cell-months = about 300 worker-hours, impossible. Plan once families land: (1) full factorial of the six top-1s = 64 stacks, pre-screened first-order, the top 8 exact on L6M then HOLD, PRE, X'; (2) coordinate descent from LPB/JN04RM and from 10 random stacks, exact only for the final 5 stacks; (3) 2,000 random stacks first-order only (labelled first-order, never a result) to pick 6-10 stacks for exact L6M; (4) interaction table from first-order pair-drops, confirmed exact for the top pairs; (5) the minimal 2-3 rule set exact on L6M + HOLD, then repeated unchanged on K7/M7/U7. Dial pairs already suspected duplicate from W-A/W-B: SIGQ vs day cap, LOT vs 7/4/4.
7. Known inputs for the joint (from the other pages, exact, JN04RM base): W-C 30-min blackout -5.2 % L6M (not an earner on the dressed stack), hot-only 60-min same-side blackout +4.1 % (inside noise); W-B never-cut P7 +19.1 / +10.4 / +27.4 % L6M/PRE/X', -19.1 % HOLD on LPB_BASE; W-A A2_18 first-order L6M overstated vs exact (-24.4 %). These are registry candidates, not joint results.

## Next
Page 03:00Z will carry: ranker re-run on the landed feature tables with untaken signals, registry with top-3 per family, factorial pre-screen, first exact joint rows, and the budget actually spent.

## Auto section (chain, rebuilt 2026-11-12T11:31:02Z)
Inputs seen: 42 watched files; feature tables landed: ['p7_feat_I.parquet', 'p7_feat_I_v2.parquet', 'p7_signal_features.parquet']. Cycle log: no change in feature tables, ranker not re-run.
Registry rows by family: {'A-comp': 2, 'A1': 5, 'A2': 5, 'A3': 6, 'A4': 9, 'G': 2, 'other': 9}. launch gate MemAvail 112 GB (need 62): OPEN; no joint set is defined yet (needs the families top-3 specs), so nothing launched.
Ranker (first-order, GBDT mean over 3 seeds vs null 95th percentile, dollars per week):
action  win    gbdt  null95
   dec HOLD  6527.0  3526.0
   dec  L1M  4457.0  4843.0
   dec  L3M  4649.0  5014.0
   dec  L6M  5687.0  4350.0
   dec  PRE  6079.0  3269.0
   dec   X'     0.0     0.0
  quin HOLD 22226.0  7645.0
  quin  L1M 25847.0 10883.0
  quin  L3M 21528.0  9788.0
  quin  L6M 22451.0  8132.0
  quin  PRE 16756.0  6193.0
  quin   X'     0.0     0.0
First-order P7-only rule interaction on the six rules R1 gap<30 min skip, R2 atr_rel>=1.3 half, R3 chasing 3rd+ skip, R4 LOT cold half, R5 Asia 7-lot short half, R6 same-side stack>=5 half (trade-level, week-level P7 drawdown, NOT stack, NOT exact; top 6 of the 64-cell factorial by L6M drawdown cut; k = rule count; removed_w20 / removed_other = pnl removed in the worst-20 weeks vs other weeks):
      rules  k  ddcut_L6M  dmean_L6M  ddcut_HOLD  dmean_HOLD  ddcut_PRE  dmean_PRE  ddcut_X'  dmean_X'  removed_w20  removed_other
   R1+R2+R5  3       60.2    -3366.3        26.5     -6136.0       46.3    -1458.4      -7.8    -947.2    -331787.2       881706.7
   R2+R4+R5  3       58.8    -2874.6        57.8     -4544.6       33.4    -2023.6      54.8      70.2    -322498.0       756219.8
      R1+R5  2       53.5    -2957.4        -5.5     -5715.8       32.7     -999.2     -40.1   -1389.9    -275708.8       772993.8
R1+R2+R4+R5  4       52.8    -5885.2         0.7     -7986.3       67.7    -2120.6      36.1    -637.2    -422370.3      1101324.4
R2+R3+R4+R5  4       51.5    -5999.0        51.5     -6927.5       46.7    -2397.5      54.5      86.5    -369540.7       951206.9
R1+R2+R5+R6  4       49.9    -3775.1        24.9     -6286.8       47.7    -1673.4      -6.3    -953.6    -331459.5       908276.6
ACCEPTANCE (user test: a finalist that fails test 1 on more than 2 of the 20 worst sessions is NOT the P7 fix; joint ranked by passes acceptance first, then L6M/HOLD cut). LPB_BASE P7 baseline (test 2, consecutive same-side losing entries per session; a win or an opposite-side trade resets): all sessions max 6, 95th 2, mean 0.89, $ lost on 3rd-and-later: -136326; Asia max 6, 95th 2, mean 0.90, -80482. Sessions with a run of 3 or more: 48 of 2213.
Finalist results: no finalist yet (finalists.txt empty or W-C acceptance_p7.py absent)
Pairs (jaccard = overlap of flagged trades; L6M columns = P7 drawdown cut percent, pair vs each alone; additive pairs with small jaccard do not duplicate, big jaccard with pair < sum duplicates):
                 a                  b  n_a  n_b  jaccard  L6M_pair  L6M_i  L6M_j
     R1_gap30_skip      R2_hot13_half 2350 2390     0.28     47.16  39.44  20.67
     R1_gap30_skip      R3_chase_skip 2350  931     0.26     11.96  39.44   2.09
     R1_gap30_skip       R4_cold_half 2350 3000     0.36     28.93  39.44  22.60
     R1_gap30_skip R5_asia7short_half 2350  404     0.08     53.55  39.44  25.79
     R1_gap30_skip     R6_stack5_half 2350  356     0.10     22.36  39.44  -0.00
     R2_hot13_half      R3_chase_skip 2390  931     0.17     24.72  20.67   2.09
     R2_hot13_half       R4_cold_half 2390 3000     0.35     49.35  20.67  22.60
     R2_hot13_half R5_asia7short_half 2390  404     0.06     39.71  20.67  25.79
     R2_hot13_half     R6_stack5_half 2390  356     0.02     23.38  20.67  -0.00
     R3_chase_skip       R4_cold_half  931 3000     0.16     18.53   2.09  22.60
     R3_chase_skip R5_asia7short_half  931  404     0.11     27.30   2.09  25.79
     R3_chase_skip     R6_stack5_half  931  356     0.06      5.42   2.09  -0.00
      R4_cold_half R5_asia7short_half 3000  404     0.08     36.41  22.60  25.79
      R4_cold_half     R6_stack5_half 3000  356     0.07      6.13  22.60  -0.00
R5_asia7short_half     R6_stack5_half  404  356     0.07     25.79  25.79  -0.00

## Behavioural scorecard (reference rows, per week, mid-path based; stack = all books)
LPB_BASE L6M (stack, per week): full stops 24.5/wk $-40052; give-backs 9.1/wk (9.0 round-trips) realised $-14009, forgone vs target $35376; same-side losing runs max 12, p95 6, $-51344 lost on 3rd-and-later; no-new-evidence re-entries 37.3/wk $-363; recoveries cut 13.7/wk $46863, clipped fills 0.0/wk $0; pnl $19784/wk.
LPB_BASE HOLD (stack, per week): full stops 23.0/wk $-37923; give-backs 8.0/wk (7.8 round-trips) realised $-12167, forgone vs target $30716; same-side losing runs max 12, p95 6, $-43521 lost on 3rd-and-later; no-new-evidence re-entries 30.0/wk $732; recoveries cut 12.2/wk $41657, clipped fills 0.0/wk $0; pnl $15351/wk.
LPB_BASE PRE (stack, per week): full stops 16.9/wk $-28859; give-backs 5.2/wk (4.8 round-trips) realised $-7549, forgone vs target $19365; same-side losing runs max 11, p95 4, $-22384 lost on 3rd-and-later; no-new-evidence re-entries 12.7/wk $-160; recoveries cut 6.7/wk $22256, clipped fills 0.0/wk $0; pnl $11882/wk.
LPB_BASE X' (stack, per week): full stops 17.5/wk $-28195; give-backs 3.6/wk (3.0 round-trips) realised $-4902, forgone vs target $12802; same-side losing runs max 7, p95 4, $-12302 lost on 3rd-and-later; no-new-evidence re-entries 2.7/wk $569; recoveries cut 2.5/wk $9968, clipped fills 0.0/wk $0; pnl $1342/wk.
JN04RM L6M (stack, per week): full stops 25.4/wk $-38130; give-backs 9.9/wk (9.8 round-trips) realised $-11306, forgone vs target $28091; same-side losing runs max 13, p95 7, $-42885 lost on 3rd-and-later; no-new-evidence re-entries 43.3/wk $1885; recoveries cut 15.2/wk $39718, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4296/wk, losers avoided $4285/wk, net -254 $/wk; pnl $19530/wk.
JN04RM HOLD (stack, per week): full stops 23.6/wk $-35520; give-backs 8.6/wk (8.4 round-trips) realised $-9743, forgone vs target $24378; same-side losing runs max 13, p95 6, $-37009 lost on 3rd-and-later; no-new-evidence re-entries 34.2/wk $1140; recoveries cut 13.1/wk $34017, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $5311/wk, losers avoided $4661/wk, net -2854 $/wk; pnl $12497/wk.
JN04RM PRE (stack, per week): full stops 16.8/wk $-26445; give-backs 5.4/wk (5.0 round-trips) realised $-5634, forgone vs target $14565; same-side losing runs max 11, p95 5, $-17863 lost on 3rd-and-later; no-new-evidence re-entries 14.4/wk $-45; recoveries cut 7.2/wk $17046, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $4797/wk, losers avoided $4304/wk, net -2474 $/wk; pnl $9409/wk.
JN04RM X' (stack, per week): full stops 17.7/wk $-27189; give-backs 3.5/wk (3.0 round-trips) realised $-3615, forgone vs target $9772; same-side losing runs max 7, p95 4, $-9998 lost on 3rd-and-later; no-new-evidence re-entries 3.1/wk $562; recoveries cut 2.5/wk $6540, clipped fills 0.0/wk $0; vs LPB_BASE: winners skipped $3512/wk, losers avoided $3147/wk, net +205 $/wk; pnl $1547/wk.
LIVE LIVEWK (stack, per week): full stops 3.0/wk $-4385; give-backs 14.0/wk (12.0 round-trips) realised $-18855, forgone vs target $56473; same-side losing runs max 5, p95 4, $-50669 lost on 3rd-and-later; no-new-evidence re-entries 36.0/wk $34824; recoveries cut 22.0/wk $105991, clipped fills 0.0/wk $0; pnl $102830/wk.
## Scorecard acceptability / acceptance (a, b, c each down at least half on L6M vs LPB_BASE, cost e <= saving, none of the 5 best L6M weeks turned losing; ranking = acceptable first, then drawdown)
  cell  a_fullstops_wk  a_fullstops_wk_ref  b_giveback_wk  b_giveback_wk_ref  c_lost_3rd_plus_usd_wk  c_lost_3rd_plus_usd_wk_ref  d_noevidence_wk  d_noevidence_wk_ref  saving_usd_wk  cost_usd_wk  a_half  b_half  c_half  best5_turned_losing  acceptable
JN04RM            25.4                24.5            9.9                9.1                -42884.8                    -51344.1             43.3                 37.3        17665.7      44014.2   False   False   False                    0       False
## Worst 10 sessions replay (P7, L6M, LPB_BASE; entry by entry, before and after)
Session 20260728 (sess 0) LPB_BASE net $-14274: 22:38 short 4L StateCut -3007; 00:11 short 4L Target +4800; 01:06 short 5L Target +5984; 01:23 short 7L StateCut -5705; 02:14 short 4L StateCut -3254; 03:54 long 4L StateCut -3694; 04:43 long 4L StateCut -3394; 05:40 short 7L StateCut -6005
Session 20260527 (sess 3) LPB_BASE net $-13000: 14:11 short 4L StateCut -3374; 14:33 short 3L StateCut -2449; 15:00 short 4L StateCut -3654; 15:20 short 2L StateCut -1759; 15:39 short 2L StateCut -1764
Session 20260910 (sess 0) LPB_BASE net $-12681: 23:01 short 4L StateCut -3274; 01:07 short 4L StateCut -3349; 05:07 long 7L StateCut -6059
Session 20260826 (sess 0) LPB_BASE net $-12662: 22:09 long 7L StateCut -5810; 00:04 short 7L Target +6004; 01:09 short 7L StateCut -5718; 03:03 long 7L StateCut -7138
Session 20261001 (sess 0) LPB_BASE net $-12188: 23:08 short 7L StateCut -6615; 00:01 long 7L StateCut -5573
Session 20260515 (sess 1) LPB_BASE net $-11920: 06:07 short 4L StateCut -3344; 06:21 short 4L StateCut -3714; 06:56 long 1L Target +1199; 07:28 long 2L StateCut -1699; 09:12 short 1L Target +1199; 09:42 short 4L StateCut -3294; 10:40 short 2L StateCut -1464; 11:01 long 2L BookLock -802
Session 20261008 (sess 0) LPB_BASE net $-11851: 22:21 long 7L StateCut -5873; 00:56 short 7L StateCut -5978
Session 20260618 (sess 0) LPB_BASE net $-11837: 23:42 short 7L StateCut -6615; 00:31 long 7L StateCut -5221
Session 20260603 (sess 0) LPB_BASE net $-11538: 22:12 long 7L StateCut -5710; 23:35 short 7L StateCut -5828
Session 20260520 (sess 0) LPB_BASE net $-11477: 22:26 short 4L StateCut -3454; 01:00 long 1L StateCut -1506; 01:51 long 4L StateCut -3164; 03:00 short 4L StateCut -3354



## Y. Weekly check and frozen-week re-simulation (W-J)

# Weekly check, L6M (ISO weeks with trading days in 2026-05..10; weeks at the month edges are partial; exact engine; Shadow only)

| week | LPB_BASE | JN04RM | JN05W_E1A |
|--|--|--|--|
| 202638 (best of LPB_BASE) | 88836 | 72104 | 47801 |
| 202623 (best of LPB_BASE) | 73836 | 68072 | 43954 |
| 202625 (best of LPB_BASE) | 59099 | 59990 | 31727 |
| 202639 (best of LPB_BASE) | 57178 | 52634 | 32538 |
| 202633 (best of LPB_BASE) | 52499 | 36328 | 14820 |
| 202644 (worst of LPB_BASE) | -51253 | -16664 | -10591 |
| 202636 (worst of LPB_BASE) | -44984 | -25704 | -11779 |
| 202621 (worst of LPB_BASE) | -39976 | -39092 | -6477 |
| 202635 (worst of LPB_BASE) | -23667 | -15995 | -13608 |
| 202637 (worst of LPB_BASE) | -8573 | 679 | 8790 |

JN04RM: LPB_BASE winning weeks 20 of 27; of those, JN04RM turn losing: 1; weeks where JN04RM beats LPB_BASE: 13 of 27; sum over the 5 best LPB_BASE weeks 289128 vs 331449

JN05W_E1A: LPB_BASE winning weeks 20 of 27; of those, JN05W_E1A turn losing: 2; weeks where JN05W_E1A beats LPB_BASE: 9 of 27; sum over the 5 best LPB_BASE weeks 170840 vs 331449

# Frozen week 11-02..05 exact re-simulation (month 202611; state days 20261102-05)

NOT POSSIBLE on this box: the exact engine needs the hist day files (_hist_replica/days) built from raw mbp-10, and the latest raw NQ file is 2026-10-31 (GLBX-20261031); only the 1-s state arrays for 11-02..05 exist. FW_LPB 202611 failed with: no day files in range. Needed: raw mbp-10 for 2026-11-02..05 into /mnt/l2/l2vast/raw/NQ/ext/ then the hist_pipe day build. Sets FW_LPB, FW_JN04RM, JN05W_E1_FW, JN05W_E1A_FW and jnr_cfg_nov.json (Nov dA threshold) are ready and run with chain_jn05.sh SET 202611. Until then the trend-week cost evidence is the L6M weekly table above (the 5 best LPB_BASE weeks).

## Z0. Worst 10 L6M P7 sessions, entry by entry (W-J)

# Worst 10 L6M P7 sessions of LPB_BASE, replayed entry by entry (W-J; session key = label day + ET session index; exact engine; Shadow only)

## session 202607280 (LPB_BASE P7 net -14274)
- LPB_BASE: total -14274 over 8 trades: 22:38 4L short StateCut -3007; 00:11 4L short Target 4800; 01:06 5L short Target 5984; 01:23 7L short StateCut -5705; 02:14 4L short StateCut -3254; 03:54 4L long StateCut -3694; 04:43 4L long StateCut -3394; 05:40 7L short StateCut -6005
- JN04RM: total -6508 over 8 trades: 22:38 2L short StateCut -1433; 00:11 2L short Target 2398; 01:06 3L short Target 3601; 01:23 4L short StateCut -3464; 02:14 2L short StateCut -1684; 03:54 2L long StateCut -1719; 04:43 1L long StateCut -877; 05:40 4L short StateCut -3329
- JN05W_E1A: total -3623 over 9 trades: 22:38 2L short StateCut -1049; 00:11 2L short Target 2398; 01:06 3L short Target 3601; 01:23 4L short StateCut -2224; 02:14 2L short StateCut -1194; 02:41 2L short StateCut -1274; 03:54 2L long StateCut -1129; 04:43 1L long StateCut -592; 05:40 4L short StateCut -2159

## session 202605273 (LPB_BASE P7 net -13000)
- LPB_BASE: total -13000 over 5 trades: 14:11 4L short StateCut -3374; 14:33 3L short StateCut -2449; 15:00 4L short StateCut -3654; 15:20 2L short StateCut -1759; 15:39 2L short StateCut -1764
- JN04RM: total -6130 over 5 trades: 14:11 2L short StateCut -1759; 14:33 1L short StateCut -880; 15:00 2L short StateCut -1649; 15:20 1L short StateCut -992; 15:39 1L short StateCut -850
- JN05W_E1A: total -4243 over 5 trades: 14:11 2L short StateCut -1069; 14:33 1L short StateCut -675; 15:00 2L short StateCut -1409; 15:20 1L short StateCut -505; 15:39 1L short StateCut -585

## session 202609100 (LPB_BASE P7 net -12681)
- LPB_BASE: total -12681 over 3 trades: 23:01 4L short StateCut -3274; 01:07 4L short StateCut -3349; 05:07 7L long StateCut -6059
- JN04RM: total -6750 over 3 trades: 23:01 2L short StateCut -1659; 01:07 2L short StateCut -1659; 05:07 4L long StateCut -3432
- JN05W_E1A: total -53 over 3 trades: 23:01 1L short StateCut -725; 01:07 1L short StateCut -527; 04:47 1L long Target 1199

## session 202608260 (LPB_BASE P7 net -12662)
- LPB_BASE: total -12662 over 4 trades: 22:09 7L long StateCut -5810; 00:04 7L short Target 6004; 01:09 7L short StateCut -5718; 03:03 7L long StateCut -7138
- JN04RM: total -12662 over 4 trades: 22:09 7L long StateCut -5810; 00:04 7L short Target 6004; 01:09 7L short StateCut -5718; 03:03 7L long StateCut -7138
- JN05W_E1A: total -9542 over 3 trades: 22:09 7L long StateCut -7263; 00:04 7L short Target 6004; 01:09 7L short StopJoinFallback -8283

## session 202605060 (LPB_BASE P7 net -12366)
- LPB_BASE: total -12366 over 2 trades: 23:48 7L long StateCut -6223; 00:48 7L short StateCut -6143
- JN04RM: total 3079 over 3 trades: 23:48 4L long StateCut -3594; 00:48 2L short StateCut -1729; 04:22 7L long Target 8402
- JN05W_E1A: total 3595 over 3 trades: 23:48 4L long StateCut -2894; 00:48 2L short StateCut -1913; 04:22 7L long Target 8402

## session 202610010 (LPB_BASE P7 net -12188)
- LPB_BASE: total -12188 over 2 trades: 23:08 7L short StateCut -6615; 00:01 7L long StateCut -5573
- JN04RM: total -9974 over 2 trades: 23:08 7L short StateCut -6615; 00:01 4L long StateCut -3359
- JN05W_E1A: total -8498 over 1 trades: 23:08 7L short StopJoin -8498

## session 202605151 (LPB_BASE P7 net -11920)
- LPB_BASE: total -11920 over 8 trades: 06:07 4L short StateCut -3344; 06:21 4L short StateCut -3714; 06:56 1L long Target 1199; 07:28 2L long StateCut -1699; 09:12 1L short Target 1199; 09:42 4L short StateCut -3294; 10:40 2L short StateCut -1464; 11:01 2L long BookLock -802
- JN04RM: total -2664 over 10 trades: 06:07 1L short StateCut -837; 06:21 1L short StateCut -957; 06:56 1L long Target 1199; 07:28 1L long StateCut -847; 09:12 1L short Target 1199; 09:42 1L short StateCut -942; 10:40 1L short StateCut -970; 11:01 1L long StateCut -857; 11:52 1L long StateCut -850; 12:25 1L short Target 1199
- JN05W_E1A: total -624 over 10 trades: 06:07 1L short StateCut -525; 06:21 1L short StateCut -542; 06:56 1L long Target 1199; 07:28 1L long StateCut -885; 09:12 1L short Target 1199; 09:42 1L short StateCut -585; 10:40 1L short StateCut -617; 11:01 1L long StateCut -527; 11:52 1L long StateCut -540; 12:25 1L short Target 1199

## session 202610080 (LPB_BASE P7 net -11851)
- LPB_BASE: total -11851 over 2 trades: 22:21 7L long StateCut -5873; 00:56 7L short StateCut -5978
- JN04RM: total -11851 over 2 trades: 22:21 7L long StateCut -5873; 00:56 7L short StateCut -5978
- JN05W_E1A: total -12082 over 2 trades: 22:21 7L long StateCut -6979; 00:56 7L short StateCut -5103

## session 202606180 (LPB_BASE P7 net -11837)
- LPB_BASE: total -11837 over 2 trades: 23:42 7L short StateCut -6615; 00:31 7L long StateCut -5221
- JN04RM: total -2812 over 3 trades: 23:42 4L short StateCut -3759; 00:31 2L long StateCut -1456; 05:27 2L long Target 2403
- JN05W_E1A: total -6402 over 3 trades: 23:42 4L short StateCut -4309; 00:31 2L long StateCut -964; 01:04 2L long StateCut -1129

## session 202606030 (LPB_BASE P7 net -11538)
- LPB_BASE: total -11538 over 2 trades: 22:12 7L long StateCut -5710; 23:35 7L short StateCut -5828
- JN04RM: total -5057 over 4 trades: 22:12 4L long StateCut -3259; 23:35 4L short StateCut -3349; 01:36 1L long StateCut -847; 02:11 2L long Target 2398
- JN05W_E1A: total -4796 over 4 trades: 22:12 4L long StateCut -4049; 23:35 4L short StateCut -2239; 01:36 1L long StackCut -906; 02:11 2L long Target 2398


## Z. Worst 10 sessions replayed entry by entry, before and after (acceptance replays, W-Q)

## Scorecard acceptability / acceptance (a, b, c each down at least half on L6M vs LPB_BASE, cost e <= saving, none of the 5 best L6M weeks turned losing; ranking = acceptable first, then drawdown)
  cell  a_fullstops_wk  a_fullstops_wk_ref  b_giveback_wk  b_giveback_wk_ref  c_lost_3rd_plus_usd_wk  c_lost_3rd_plus_usd_wk_ref  d_noevidence_wk  d_noevidence_wk_ref  saving_usd_wk  cost_usd_wk  a_half  b_half  c_half  best5_turned_losing  acceptable
JN04RM            25.4                24.5            9.9                9.1                -42884.8                    -51344.1             43.3                 37.3        17665.7      44014.2   False   False   False                    0       False
