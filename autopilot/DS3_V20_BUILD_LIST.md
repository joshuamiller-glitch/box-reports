# DS3_V20_BUILD_LIST - v2.0 build list, one row per rule (W-JV, family D / T-DEEPEN PART 5)

VERDICT: build list v0. Only B (U7 fresh time stop) holds in recent and older windows and it is mean-specific only (its DD cut equals the delayed-exit placebo and turns negative with W44 removed): recommend Shadow. A is recent-only (PRE worse): Shadow candidate. C rejected: Off. D/L, P, R/W/V are recent-window or provisional evidence from their owners: Shadow-only candidates until older windows and placebos land. No PASS claim.

Generated 2026-11-14 23:29 UTC. Exact engine, JN05W2 all layers ON, base lots (user lots x1.75), engine fee $1.18/contract RT; every number is the single rule vs JN05W2. Joint results and interaction table: DS3_JOINT_V20.md. Each rule gets its own switch `<Rule>Mode` = Off | Shadow | Live (Shadow = evaluate and log the would-be action, orders unchanged). Recommendation text is mine, not a PASS. Exact specs as scored: DS3_JOINT_V20.md section 7.

| rule | scope | windows scored | DD cut % L3M / L6M / HOLD / PRE / X' / GAP | d mean $/wk (same windows) | d mean @4.84 L6M | DD cut % L6M with W44 removed | holds recent AND older? | placebo | recommendation |
|--|--|--|--|--|--|--|--|--|--|
| B | U7 time stop on fresh entries: at 15:00 after the first fill, if open P&L < -10 pts, market exit (fresh context only: chase_k <= 1.0, n <= 2 U7 entries in the session, >= 30 min since the last U7 exit). | L1M,L3M,L6M,HOLD,PRE,X',GAP | 11.7 / 11.7 / 3.3 / -1.0 / 18.0 / 0.0 | 1244 / 573 / 799 / -90 / 249 / 5 | 571 | -5.2 | yes | exact sets PL1-3 present | Shadow (small evidence; Live only by decision after a Shadow period) |
| A | SM_A6_halfNP7: after the first CLOSED trade of a book-session lost, later signals of that book-session at half lots (K7 M7 U7 H7 A7; P7 untouched). | L1M,L3M,L6M,HOLD,PRE,X',GAP | 11.8 / 11.8 / 11.6 / -7.6 / 7.8 / 2.3 | -691 / 383 / 724 / -42 / 243 / -915 | 407 | 6.2 | NO | exact sets PL1-3 present | Off |
| C | U7 Keltner-mid structure stop + equal-$ lots (REJECTED, older windows). | L1M,L3M,L6M,HOLD,PRE,X',GAP | 1.1 / 1.1 / -16.4 / -22.3 / -68.2 / -24.5 | 1746 / 712 / 145 / -2753 / -3246 / -4724 | 683 | -8.6 | NO | exact sets PL1-3 present | Off (rejected) |
| D | W-LR London range-used-up SKIP k=1 (PROVISIONAL). | L1M,L3M,L6M,HOLD | 13.9 / 13.9 / -3.7 / - / - / - | 2725 / 1945 / 608 / - / - / - | 2024 | -2.6 | NO | W-LR/W-PR/W-RA own placebos (see their pages) | Off |
| L | Same with k=1.25 (PROVISIONAL). | none yet | | | | | | | Off until scored |
| P | W-PR P7 Asia same-side 30-min block after a loser (recent-wi | none yet | | | | | | | Off until scored |
| R | W-RA M7 London cap: block new M7 London entries after 3 closed trades of the Globex day. | L1M,L3M | -0.3 / - / - / - / - / - | 671 / - / - / - / - / - | - | - | recent only (older windows missing) | W-LR/W-PR/W-RA own placebos (see their pages) | Shadow-only candidate; do not build Live until older windows land |
| W | Same with 2 closed trades (live night 2026-11-13 cost -2040 per W-RA). | L1M,L3M | -1.7 / - / - / - / - / - | 869 / - / - / - / - / - | - | - | recent only (older windows missing) | W-LR/W-PR/W-RA own placebos (see their pages) | Shadow-only candidate; do not build Live until older windows land |
| V | W-RA M7 London block same-side re-entry after a same-side loser until an opposite-side M7 signal. | L1M | - / - / - / - / - / - | - / - / - / - / - / - | - | - | recent only (older windows missing) | W-LR/W-PR/W-RA own placebos (see their pages) | Shadow-only candidate; do not build Live until older windows land |

## What D7 must compute to run each rule

- **B** per-trade clock from the first fill; open P&L in points; context tag fresh (session first close, ATR5, count of U7 entries, last U7 exit time). Exit name for logs EarlyCut.
- **A** per-book per-session ledger of closed trades (first closed trade of the six-session key and its net sign).
- **C** 5-min EMA20 of closes, 60 s lag.
- **D** ATR-only walk-forward forecast of the day range (file fc_lr), London range since 02:00 ET.
- **L** as D.
- **P** P7 Asia closed-trade list with side, net sign, exit time.
- **R** count of closed M7 trades in the London session instance.
- **W** as R.
- **V** M7 signal log including skipped signals.

## Interaction and joint

See DS3_JOINT_V20.md sections 1-6b (all pairs, interaction table, ranking, W44-removed rows, exact placebos). Survivors from W-EA/EB/EC, W-LA/LB/PA/TA, W-D9/D10, W-CH2, W-TD (C5_c1 is a trend-day size cell without an exact JN05W2 set yet), W-PM are added by writing their hook into mk_jv2.py (one letter each) and appending the sets to /mnt/l2/l2vast/_jointv20/cells.txt.