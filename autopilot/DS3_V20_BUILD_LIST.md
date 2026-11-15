# DS3_V20_BUILD_LIST - v2.0 build list, one row per rule (W-JV, family D / T-DEEPEN PART 5)

VERDICT: build list v0. Only B (U7 fresh time stop) holds in recent and older windows and it is mean-specific only (its DD cut equals the delayed-exit placebo and turns negative with W44 removed): recommend Shadow. A helps recent windows but is worse in PRE (-7.6 pct DD): Off or Shadow-only. C rejected: Off. D/L, P, R/W/V are recent-window or provisional evidence from their owners: Shadow-only candidates until older windows and placebos land. No PASS claim.

**Closest to live: B (U7 fresh time stop, Shadow).** It is the only rule that passes the tolerant gate in all five windows (L3M, L6M, HOLD, PRE, X'). It still lacks: (1) specificity - its DD cut equals the delayed-exit placebo and is -5.2 pct with W44 removed, so only the mean gain (+573 L6M, +799 HOLD vs placebo +238..+625) is specific; (2) walk-forward beat rate is 16.5 pct of 2-week blocks (cut 0.0); (3) HOLD placebos incomplete. Joint candidates AB+F, DV, AR, ABD, BR show recent+HOLD gains and are in the PRE/X' battery (S3) now; none is a lead until PRE and X' land.

Generated 2026-11-15 18:37 UTC. Exact engine, JN05W2 all layers ON, base lots (user lots x1.75), engine fee $1.18/contract RT; every number is the single rule vs JN05W2. Joint results and interaction table: DS3_JOINT_V20.md. Each rule gets its own switch `<Rule>Mode` = Off | Shadow | Live (Shadow = evaluate and log the would-be action, orders unchanged). Recommendation text is mine, not a PASS. Exact specs as scored: DS3_JOINT_V20.md section 7.

| rule | scope | windows scored | DD cut % WEEKLY L3M / L6M / HOLD / PRE / X' / GAP | DD cut % DAILY same windows | d mean $/wk (same windows) | d mean @4.84 L6M | DD cut % L6M with W44 removed | holds recent AND older? | placebo | vs random skip (PATH EFFECT) | recommendation |
|--|--|--|--|--|--|--|--|--|--|--|--|
| B | U7 time stop on fresh entries: at 15:00 after the first fill, if open P&L < -10 pts, market exit (fresh context only: chase_k <= 1.0, n <= 2 U7 entries in the session, >= 30 min since the last U7 exit). | L1M,L3M,L6M,HOLD,PRE,X',GAP | 11.7 / 11.7 / 3.3 / -1.0 / 18.0 / 0.0 | 9.2 / 9.2 / 4.9 / 0.0 / 11.3 / 0.0 | 1244 / 573 / 799 / -90 / 249 / 5 | 571 | -5.2 | yes | exact sets PL1-3 present | n/a (not a skip) | Shadow (small evidence; Live only by decision after a Shadow period) |
| A | SM_A6_halfNP7: after the first CLOSED trade of a book-session lost, later signals of that book-session at half lots (K7 M7 U7 H7 A7; P7 untouched). | L1M,L3M,L6M,HOLD,PRE,X',GAP | 11.8 / 11.8 / 11.6 / -7.6 / 7.8 / 2.3 | 8.2 / 8.2 / 19.4 / -0.7 / 1.8 / -0.7 | -691 / 383 / 724 / -42 / 243 / -915 | 407 | 6.2 | NO | exact sets PL1-3 present | n/a (not a skip) | BASIS-DEPENDENT (passes on daily DD, fails on weekly): Shadow-only |
| C | U7 Keltner-mid structure stop + equal-$ lots (REJECTED, older windows). | L1M,L3M,L6M,HOLD,PRE,X',GAP | 1.1 / 1.1 / -16.4 / -22.3 / -68.2 / -24.5 | 0.7 / 0.7 / 20.1 / -11.7 / -58.4 / -15.3 | 1746 / 712 / 145 / -2753 / -3246 / -4724 | 683 | -8.6 | NO | exact sets PL1-3 present | n/a (not a skip) | Off (rejected) |
| D | W-LR London range-used-up SKIP k=1 (PROVISIONAL). | L1M,L3M,L6M,HOLD | 13.9 / 13.9 / -3.7 / - / - / - | 4.7 / 4.7 / 13.6 / - / - / - | 2725 / 1945 / 608 / - / - / - | 2024 | -2.6 | NO | W-LR/W-PR/W-RA own placebos (see their pages) | L6M: cut -7.1 / -14.9 / -3.3 | dMean -1655 / -113 / 47; HOLD: cut -39.7 / -26.0 / -50.7 | dMean -609 / 808 / -564 [CF_RS = W-CF3 engine random skip same keep share (first set listed: shares from the _MP London sets, to be rebuilt at 0.686 / 0.724); other sets are shifted-forecast placebos, not random skips] | BASIS-DEPENDENT (passes on daily DD, fails on weekly): Shadow-only |
| L | Same with k=1.25 (PROVISIONAL). | none yet | | | | | | | Off until scored |
| P | W-PR P7 Asia same-side 30-min block after a loser (recent-window evidence only). | L1M,L3M,L6M,HOLD | 15.6 / 15.6 / -9.6 / - / - / - | 16.9 / 16.9 / 6.1 / - / - / - | 803 / 1720 / 551 / - / - / - | 1720 | -0.5 | NO | W-LR/W-PR/W-RA own placebos (see their pages) | L6M: cut -8.9 / -2.3 / -2.4 | dMean -529 / -312 / -683; HOLD: cut -4.6 / -1.4 / -1.4 | dMean -58 / 153 / 72 [W-PR random same-count blocks] | BASIS-DEPENDENT (passes on daily DD, fails on weekly): Shadow-only |
| R | W-RA M7 London cap: block new M7 London entries after 3 closed trades of the Globex day. | L1M,L3M,L6M,HOLD | -0.3 / -0.3 / 18.0 / - / - / - | -2.6 / -2.6 / 3.5 / - / - / - | 671 / 1065 / 982 / - / - / - | 1086 | -6.5 | yes | W-LR/W-PR/W-RA own placebos (see their pages) | PENDING (engine random skip of same keep share) [W-RA random block, same count] | Shadow (small evidence; Live only by decision after a Shadow period) |
| T | W-TD C5_c1 trend-day call: when all four causal tests hold (last 90 one-minute closes >= 0.15 x expR on one side of the running mean since 18:00 ET; day range >= 1.0 x expR (median range of previous 20 Globex days); >= 2 closed Target winners today on that side; >= 1 counter-side closed trade net <= 0 with with-side closed net > 0): counter-trend entries skipped, with-trend lots x1.5, profit cap off and give-back lock 0.3 x peak for with-trend. Mean gain at equal DD (W44 untouched). | L1M,L3M,L6M,HOLD | 0.0 / 0.0 / 1.6 / - / - / - | -0.0 / 0.0 / 0.0 / - / - / - | 1065 / 1196 / 1638 / - / - / - | 1191 | -18.3 | yes | none yet | n/a (not a skip) | Shadow (small evidence; Live only by decision after a Shadow period) |
| Y | W-TD C1_c1: price-only trend-day call (same actions as T: co | none yet | | | | | | | Off until scored |
| S | W-TD XC5_snyam: C5_c1 call applied in NY AM only (L6M +1,473 | none yet | | | | | | | Off until scored |
| N | W-NT U7 near-target ladder: trigger 70 pct of target, lock 4 | none yet | | | | | | | Off until scored |
| Q | W-NT M7 ladder 90/20/3 s (FIRST PASS). | none yet | | | | | | | Off until scored |
| Z | W-NT lot table SMALL1: H7 lots 5,0,0,1,0,0 by session and O7 | none yet | | | | | | | Off until scored |
| W | Same with 2 closed trades (live night 2026-11-13 cost -2040 per W-RA). | L1M,L3M | -1.7 / - / - / - / - / - | -7.3 / - / - / - / - / - | 869 / - / - / - / - / - | - | - | recent only (older windows missing) | W-LR/W-PR/W-RA own placebos (see their pages) | L6M: cut -23.5 / -27.6 / -17.0 | dMean -4955 / -4728 / -5739; HOLD: cut 6.4 / 2.2 / 4.5 | dMean -2942 / -3103 / -3156 [W-RA random block (all-books scope)] | Shadow-only candidate; do not build Live until older windows land |
| V | W-RA M7 London block same-side re-entry after a same-side loser until an opposite-side M7 signal. | L1M,L3M,L6M,HOLD | -0.9 / -0.9 / 17.2 / - / - / - | -1.6 / -1.6 / 13.5 / - / - / - | -856 / -303 / 302 / - / - / - | -286 | -20.2 | NO | W-LR/W-PR/W-RA own placebos (see their pages) | L6M: cut -24.6 / -26.2 / -23.4 | dMean -3152 / -2310 / -3325; HOLD: cut 23.1 / 23.1 | dMean -748 / -393 [W-RA random block (all-books scope)] | BASIS-DEPENDENT (passes on daily DD, fails on weekly): Shadow-only |

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
- **Y** running mean of 1-min closes since 18:00 ET, 20-day median range.
- **S** as T plus the session clock.
- **N** per-trade MFE vs target distance; moving a resting stop.
- **Q** as N.
- **Z** session lot table.
- **W** as R.
- **V** M7 signal log including skipped signals.

## Confluence / bracket families (H5/H6 addendum) - structure placeholders, status IN TEST

Rule for filling rows: a mechanism gets a row only from results that passed (1) its planted-edge check, (2) its per-cell cells, (3) its controls. Until its planted-edge check has passed, this page never says that nothing passes for that mechanism (H6): the status stays IN TEST. Each row will carry: exact spec as scored; what D7 computes itself; what needs a file or feed; Off / Shadow / Live recommendation; its row in the DS3_JOINT_V20 interaction table (letter in mk_jv2.py).

### W-CF3 confluence mechanisms (W-CF3: gate / size / ladder / wait / stand-down)

| mechanism | planted-edge check | per-cell cells | controls | exact spec as scored | D7 computes itself | needs file or feed | recommendation | joint letter |
|--|--|--|--|--|--|--|--|--|
| (none received yet) | - | - | - | - | - | - | IN TEST | - |

### W-CF1 confluence conditions (W-CF1: conditions)

| mechanism | planted-edge check | per-cell cells | controls | exact spec as scored | D7 computes itself | needs file or feed | recommendation | joint letter |
|--|--|--|--|--|--|--|--|--|
| (none received yet) | - | - | - | - | - | - | IN TEST | - |

### W-D10 per-book bracket cells and the assembled stack (W-D10: per-book bracket cells + assembled stack)

| mechanism | planted-edge check | per-cell cells | controls | exact spec as scored | D7 computes itself | needs file or feed | recommendation | joint letter |
|--|--|--|--|--|--|--|--|--|
| (none received yet) | - | - | - | - | - | - | IN TEST | - |

### W-CF6 checklist books (W-CF6: checklist books)

| mechanism | planted-edge check | per-cell cells | controls | exact spec as scored | D7 computes itself | needs file or feed | recommendation | joint letter |
|--|--|--|--|--|--|--|--|--|
| (none received yet) | - | - | - | - | - | - | IN TEST | - |


## Tolerant gate table (W-RE, DS3_RECENTS section 8; data ends 2026-10-30, weekly basis, base lots, engine fee, x1.75 for live lots; rule-by-rule: /mnt/l2/l2vast/_recents/gate_table.csv, code/th_recents/rc_gate.py)

List B only (rules passing the proposed tolerant reading):

| rule | recent | older | placebo | persistence |
|--|--|--|--|--|
| B = U7 time stop (TL3_EB_U7F_T15D10) | L3M +998/wk DD cut 11.7 pct; L6M +916/wk 11.7 pct; HOLD +679/wk +3.3 pct | PASS on available older windows only: X' +249/wk DD cut +18.0 pct; PRE -93/wk DD cut -1.0 pct; GAP not run | beats placebo p95 | own weekly delta persistence 44-52 pct vs base 48-52 pct: NOT above 60 pct, level case only |

Everything else fails or is unresolved under the tolerant reading: half-size A, London range LS1/LS125 (GAP -1.6k/-1.1k per wk fails), K7/A7 flat -40, BLK_M30 (placebo/recent DD, HOLD -9.6 pct), M7 caps CAP3/CAP2/BLKiv and the recent-only confluence cells (older windows not run: UNRESOLVED).


**PATH EFFECT = FREED-BOOK REPLACEMENT (generic; autopilot/PATH_EFFECT_RULE.md: a random 50 pct skip alone takes L6M DD 52k -> 86k and net 661k -> 428k).** Every skip-type rule (R, W, V, D, L, P, F with its stack cut) must be read against an engine random skip of the same keep share; column vs random skip. Rule F (A7 flat -40) is a PATH EFFECT / stack-cut (W-PM: A7 itself is +345 of the +1,869 $/wk; StackCut exits go 40 -> 15). Every pair that carries F (BF, ABF, AF) or an R-type skip inherits the flag until W-CF3 PX runs land; do not read their gain as the rule on its own trades.


## Received, not yet joined (waiting for exact set names)

- W-NT U7 near-target ladder (trigger 70 pct of target, lock 40 pct, persist 3 s, all sessions): +1220 L6M / +837 HOLD $/wk, stack DD cut -7.6 pct L6M (-2.6 ex-W44) / +12.0 HOLD; 1.2 targets clipped per week. FIRST PASS; Shadow-only until PRE and placebos. M7 ladder 90/20/3 s: +584 / +207, DD cut 0 (ex-W44 +5.3). Lot table SMALL1 (H7 5,0,0,1,0,0 + O7 2 lots): +55 L6M / +559 HOLD, DD cut 2.6 / 11.9 (ex-W44 -11.8 in L6M). P7 ladders: none holds. Hook nt_hooks (code/th_neartarget), resting-stop ladder, fill min(lock level, second mid) - 0.44 pt. D7 computes: per-trade MFE vs target distance, a resting stop order moved to the lock level.

## Interaction and joint

See DS3_JOINT_V20.md sections 1-6b (all pairs, interaction table, ranking, W44-removed rows, exact placebos). Survivors from W-EA/EB/EC, W-LA/LB/PA/TA, W-D9/D10, W-CH2, W-TD (C5_c1 is a trend-day size cell without an exact JN05W2 set yet), W-PM are added by writing their hook into mk_jv2.py (one letter each) and appending the sets to /mnt/l2/l2vast/_jointv20/cells.txt.