# DS3_V20_BUILD_LIST - v2.0 build list, one row per rule (W-JV, family D / T-DEEPEN PART 5)

VERDICT: build list v0. Only B (U7 fresh time stop) holds in recent and older windows and it is mean-specific only (its DD cut equals the delayed-exit placebo and turns negative with W44 removed): recommend Shadow. A helps recent windows but is worse in PRE (-7.6 pct DD): Off or Shadow-only. C rejected: Off. D/L, P, R/W/V are recent-window or provisional evidence from their owners: Shadow-only candidates until older windows and placebos land. No PASS claim.

Generated 2026-11-15 08:32 UTC. Exact engine, JN05W2 all layers ON, base lots (user lots x1.75), engine fee $1.18/contract RT; every number is the single rule vs JN05W2. Joint results and interaction table: DS3_JOINT_V20.md. Each rule gets its own switch `<Rule>Mode` = Off | Shadow | Live (Shadow = evaluate and log the would-be action, orders unchanged). Recommendation text is mine, not a PASS. Exact specs as scored: DS3_JOINT_V20.md section 7.

| rule | scope | windows scored | DD cut % WEEKLY L3M / L6M / HOLD / PRE / X' / GAP | DD cut % DAILY same windows | d mean $/wk (same windows) | d mean @4.84 L6M | DD cut % L6M with W44 removed | holds recent AND older? | placebo | recommendation |
|--|--|--|--|--|--|--|--|--|--|--|
| B | U7 time stop on fresh entries: at 15:00 after the first fill, if open P&L < -10 pts, market exit (fresh context only: chase_k <= 1.0, n <= 2 U7 entries in the session, >= 30 min since the last U7 exit). | L1M,L3M,L6M,HOLD,PRE,X',GAP | 11.7 / 11.7 / 3.3 / -1.0 / 18.0 / 0.0 | 9.2 / 9.2 / 4.9 / 0.0 / 11.3 / 0.0 | 1244 / 573 / 799 / -90 / 249 / 5 | 571 | -5.2 | yes | exact sets PL1-3 present | Shadow (small evidence; Live only by decision after a Shadow period) |
| A | SM_A6_halfNP7: after the first CLOSED trade of a book-session lost, later signals of that book-session at half lots (K7 M7 U7 H7 A7; P7 untouched). | L1M,L3M,L6M,HOLD,PRE,X',GAP | 11.8 / 11.8 / 11.6 / -7.6 / 7.8 / 2.3 | 8.2 / 8.2 / 19.4 / -0.7 / 1.8 / -0.7 | -691 / 383 / 724 / -42 / 243 / -915 | 407 | 6.2 | NO | exact sets PL1-3 present | BASIS-DEPENDENT (passes on daily DD, fails on weekly): Shadow-only |
| C | U7 Keltner-mid structure stop + equal-$ lots (REJECTED, older windows). | L1M,L3M,L6M,HOLD,PRE,X',GAP | 1.1 / 1.1 / -16.4 / -22.3 / -68.2 / -24.5 | 0.7 / 0.7 / 20.1 / -11.7 / -58.4 / -15.3 | 1746 / 712 / 145 / -2753 / -3246 / -4724 | 683 | -8.6 | NO | exact sets PL1-3 present | Off (rejected) |
| D | W-LR London range-used-up SKIP k=1 (PROVISIONAL). | L1M,L3M,L6M,HOLD | 13.9 / 13.9 / -3.7 / - / - / - | 4.7 / 4.7 / 13.6 / - / - / - | 2725 / 1945 / 608 / - / - / - | 2024 | -2.6 | NO | W-LR/W-PR/W-RA own placebos (see their pages) | BASIS-DEPENDENT (passes on daily DD, fails on weekly): Shadow-only |
| L | Same with k=1.25 (PROVISIONAL). | none yet | | | | | | | Off until scored |
| P | W-PR P7 Asia same-side 30-min block after a loser (recent-window evidence only). | L1M,L3M,L6M,HOLD | 15.6 / 15.6 / -9.6 / - / - / - | 16.9 / 16.9 / 6.1 / - / - / - | 803 / 1720 / 551 / - / - / - | 1720 | -0.5 | NO | W-LR/W-PR/W-RA own placebos (see their pages) | BASIS-DEPENDENT (passes on daily DD, fails on weekly): Shadow-only |
| R | W-RA M7 London cap: block new M7 London entries after 3 closed trades of the Globex day. | L1M,L3M,L6M,HOLD | -0.3 / -0.3 / 18.0 / - / - / - | -2.6 / -2.6 / 3.5 / - / - / - | 671 / 1065 / 982 / - / - / - | 1086 | -6.5 | yes | W-LR/W-PR/W-RA own placebos (see their pages) | Shadow (small evidence; Live only by decision after a Shadow period) |
| T | W-TD C5_c1 trend-day call: when all four causal tests hold (last 90 one-minute closes >= 0.15 x expR on one side of the running mean since 18:00 ET; day range >= 1.0 x expR (median range of previous 20 Globex days); >= 2 closed Target winners today on that side; >= 1 counter-side closed trade net <= 0 with with-side closed net > 0): counter-trend entries skipped, with-trend lots x1.5, profit cap off and give-back lock 0.3 x peak for with-trend. Mean gain at equal DD (W44 untouched). | L1M,L3M,L6M,HOLD | 0.0 / 0.0 / 1.6 / - / - / - | -0.0 / 0.0 / 0.0 / - / - / - | 1065 / 1196 / 1638 / - / - / - | 1191 | -18.3 | yes | none yet | Shadow (small evidence; Live only by decision after a Shadow period) |
| W | Same with 2 closed trades (live night 2026-11-13 cost -2040 per W-RA). | L1M,L3M | -1.7 / - / - / - / - / - | -7.3 / - / - / - / - / - | 869 / - / - / - / - / - | - | - | recent only (older windows missing) | W-LR/W-PR/W-RA own placebos (see their pages) | Shadow-only candidate; do not build Live until older windows land |
| V | W-RA M7 London block same-side re-entry after a same-side loser until an opposite-side M7 signal. | L1M,L3M,L6M,HOLD | -0.9 / -0.9 / 17.2 / - / - / - | -1.6 / -1.6 / 13.5 / - / - / - | -856 / -303 / 302 / - / - / - | -286 | -20.2 | NO | W-LR/W-PR/W-RA own placebos (see their pages) | BASIS-DEPENDENT (passes on daily DD, fails on weekly): Shadow-only |

Note on drawdown basis: this page and DS3_JOINT_V20 use the program convention (max drawdown of the cumulative WEEKLY series). W-LR / W-RU / W-RA pages use cumulative DAILY P&L, so their DD cuts differ (example: D = LS1 HOLD is +13.6 pct on their daily basis, -3.7 pct on the weekly basis here; the trades are identical, checked on 6 months).

## What D7 must compute to run each rule

- **B** per-trade clock from the first fill; open P&L in points; context tag fresh (session first close, ATR5, count of U7 entries, last U7 exit time). Exit name for logs EarlyCut.
- **A** per-book per-session ledger of closed trades (first closed trade of the six-session key and its net sign).
- **C** 5-min EMA20 of closes, 60 s lag.
- **D** ATR-only walk-forward forecast of the day range (file fc_lr), London range since 02:00 ET.
- **L** as D.
- **P** P7 Asia closed-trade list with side, net sign, exit time.
- **R** count of closed M7 trades in the London session instance.
- **T** running mean of 1-min closes since 18:00 ET, 20-day median range, today closed-trade ledger by side.
- **W** as R.
- **V** M7 signal log including skipped signals.

## Interaction and joint

See DS3_JOINT_V20.md sections 1-6b (all pairs, interaction table, ranking, W44-removed rows, exact placebos). Survivors from W-EA/EB/EC, W-LA/LB/PA/TA, W-D9/D10, W-CH2, W-TD (C5_c1 is a trend-day size cell without an exact JN05W2 set yet), W-PM are added by writing their hook into mk_jv2.py (one letter each) and appending the sets to /mnt/l2/l2vast/_jointv20/cells.txt.