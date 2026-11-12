# DS3_SURVIVORS_I - J_BR3S (breadth_ext15==3 skip) on the LIVE PANEL BASE, exact all windows + GAP + WF + scorecard + acceptance (W-I, 2026-11-12 15:11Z; Shadow only, no PASS)
Set WIL_J_BR3S (parts _A.._D + the first L6M run, merged as runs_rf/WIL_J_BR3S_ALL; 43 months, one set per job, TP_ENGINE). Definition as scored: skip a P7 signal when NQ, ES and RTY each hold their six-session running high (long) / low (short) from a bar that ended within 15 min (first bar and ties counted); P7 only. Reference LPB_BASE (LPB_EMPTY + the stored reference months). Spec: autopilot/V19_SPEC_BR3S.md.

## 1. Trend-week clause (first): 5 best weeks and winning weeks turned losing, per window (vs LPB_BASE)
| window | maxDD cut % | eq cut % | mean $/wk | 5 best ref weeks $ | same 5 weeks cell $ | delta $ | winning weeks turned losing | worst-5 delta $ |
|--|--|--|--|--|--|--|--|--|
| L1M | 5.0 | 10.7 | +1884 | 1363 | -681 | -2044 | 0 of 2 | -2044 |
| L3M | 21.5 | 26.1 | -1142 | 265726 | 245925 | -19801 | 0 of 8 | +24014 |
| L6M | 20.0 | 24.7 | +1287 | 331449 | 296451 | -34998 | 2 of 19 | +2186 |
| HOLD | 18.1 | 23.0 | +339 | 376655 | 345447 | -31208 | 2 of 37 | -37371 |
| PRE | 34.0 | 37.9 | +916 | 390682 | 336664 | -54018 | 2 of 48 | +65587 |
| X' | 22.6 | 27.2 | -94 | 182652 | 179612 | -3039 | 1 of 24 | +35992 |
| GAP | -8.0 | -1.5 | -1703 | 248293 | 231759 | -16534 | 1 of 14 | +22239 |
| WF2W (bi-weekly re-pick vs live) | 20.7 | % refits beaten 48.1 | +601 | | | | | |

Plain reading: the gate takes 10.6 percent of the 5 best L6M weeks (-$35.0k of $331k), 8.3 percent HOLD (-$31.2k of $377k), 13.8 percent PRE (-$54.0k of $391k), and turns 2 winning L6M weeks losing (2 of 19), 2 of 37 HOLD, 2 of 48 PRE. It does not turn the five best weeks themselves losing in any window. GAP (2025-07..10) is the failing window: maxDD cut -8.0 percent, mean -$1,704 per week.

## 2. Windows and walk-forward (vs LPB_BASE; same table, rows L1M..GAP, WF2W)
See table above. Summary: L6M cut 20.0 (mean +$1,287/wk), HOLD 18.1 (+339), PRE 34.0 (+916), X-prime 22.6 (-94), L1M 5.0 (+1,884), L3M 21.5 (-1,142), GAP -8.0 (-1,704); bi-weekly WF re-pick cut 20.7 percent, beats the live reference in 48.1 percent of refit periods, mean +$601/wk. Against JN04RM (the dressed reference) the LPB-base gate is not comparable (JN04 dials are not in it): see the second table at the end of surv_WIL_J_BR3S.csv.

## 3. Behavioural scorecard (W-Q tool, exact trades, whole stack, per week; LPB_BASE -> with gate)
- L6M: full stops 24.5 -> 24.6 per week; give-backs 9.1 -> 9.2; same-side losing run max 12 -> 10, p95 6 -> 6; $ lost on 3rd-and-later -$51.3k -> -$51.7k; no-new-evidence re-entries 37.3 -> 37.3 per week.
- HOLD: full stops 23.0 -> 23.0; give-backs 8.0 -> 8.1; run max 12 -> 10, p95 6 -> 6; no-new-evidence 30.0 -> 29.5.
- PRE: 16.9 -> 16.9; 5.2 -> 5.0; run max 11 -> 11, p95 4 -> 4. X-prime: 17.5 -> 17.5; 3.6 -> 3.4; 7 -> 7.
- Cost e (L6M, per week vs LPB_BASE): winners skipped $26.1k, losers avoided $25.6k, net +$2,470 per week; HOLD net +$1,097; PRE +$1,352; X-prime +$196.
The gate does not touch defects 1-3 (a, b, c unchanged apart from the longest run 12 -> 10): it is a drawdown / mean dial, not a behaviour fix.

## 4. Acceptance (acceptance_p7, 20 sessions: 10 worst L6M + 10 worst 3.5-year P7 sessions of the reference)
WIL_J_BR3S_ALL: FAIL, 3 of 20 sessions failed (PASS needs <= 2); LPB_BASE itself: FAIL 3 of 20. Winners kept on the 5 best sessions 0 -> 0 (no new-evidence re-entry winners exist there). The gate leaves the acceptance count unchanged.

## 5. User reading V19 (all books, strict exceed, first bar excluded) on LPB: exact
| window | maxDD cut % | eq cut % | mean $/wk | 5 best ref weeks $ | same 5 weeks cell $ | delta $ | winning weeks turned losing | worst-5 delta $ |
|--|--|--|--|--|--|--|--|--|
| L1M | 17.5 | 27.3 | +2092 | 1363 | -29535 | -30898 | 1 of 2 | -30898 |
| L3M | 32.0 | 40.1 | +1044 | 265726 | 186410 | -79316 | 1 of 8 | +35977 |
| L6M | 32.0 | 40.1 | +2142 | 331449 | 238931 | -92519 | 3 of 19 | +50292 |
| HOLD | 17.7 | 27.5 | +1787 | 376655 | 275153 | -101502 | 3 of 37 | +69504 |

P7-only strict (V19P):
| window | maxDD cut % | eq cut % | mean $/wk | 5 best ref weeks $ | same 5 weeks cell $ | delta $ | winning weeks turned losing | worst-5 delta $ |
|--|--|--|--|--|--|--|--|--|
| L1M | 6.9 | 8.3 | +1899 | 1363 | -634 | -1997 | 0 of 2 | -1997 |
| L3M | 12.6 | 13.9 | +2506 | 265726 | 244000 | -21726 | 0 of 8 | +13250 |
| L6M | 12.6 | 13.9 | +287 | 331449 | 292281 | -39169 | 1 of 19 | -8558 |
| HOLD | 14.4 | 15.7 | +18 | 376655 | 342760 | -33895 | 1 of 37 | -36745 |

## 6. Leave-one-out / composition hook for JN05W_2 (LPB + F3 + E1 + C22 + BR3S + FLAT45K, no WA_C1)
code/th_works_i/i_loo.py: `python3 -I i_loo.py NEW SRC_SET on|off jn=0 [nocde]` copies the exact set json SRC_SET, sets its works json = (SRC works json, or {jn all off, layers []} when jn=0) plus the BR3S gate rule (on) or no rule (off, identity = the leave-one-out of BR3S); hooklist / hooks / cde / jnrule of SRC are kept. Run the new set with i_run.py (IGateMixin on WorksMixin, the same runner as WI_N_BR3S, which stacked the gate on the JN05W_E1 hooklist set and was trade-identical outside the gate). For JN05W_2: W-J builds the five-component set WITHOUT the gate as SRC (jn=0, WA_C1 not used), then NEW_on and NEW_off; the other four leave-one-outs are W-J's sets with each component removed and the gate on. Feature function i_feat.build serves the gate for both definitions (rule cond breadth_ext15==3 as scored, breadth_v19==3 for the user reading; books [P7] or null for all books).
