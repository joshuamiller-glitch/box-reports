# DS3_BRACKET_DD_BUILD - non-fixed target rules per book x session, engine on TL3_EV_JN05W2JL2 (written 16:55Z)
**Plain: this table carries only what the engine has finished. A row is CONFIRMED only when the real cell beats all 6 controls on max DD in HOLD AND L6M with mean not more than 5% below the reference; otherwise ENGINE ONLY (controls missing or not beaten) or REPLAY ONLY (replay rows of W-RP / W-RP2 / W-LB2 / W-BD2 are on DS3_TARGET_REPLAY*.md and DS3_BRACKET_DD_D.md). "Keep 58" is not a deliverable: every row names the best non-fixed rule found so far.**

Basis: JL2 base, whole-stack drawdown vs the reference (+ = smaller drawdown), $ per week base lots (x1.75 live; $4.84 repriced), HOLD = 2025-11..2026-04, L6M = 2026-05..10, only that book in that session altered; stop and lots at live values (all rules here leave the 60-point stop unchanged, so constant-risk lots are the same). Controls: placebo = the rule on a persistent-draw random subset (one draw per 5-minute bucket per book and side) of ALL signals at the cell share (day-direction rule: the label shifted 11/23/37 sessions); matched = the rule on a persistent 50% random subset of the cell's own signals (day-direction rule: random labels with the real against-day share). Realised control keep shares are in each control cell trade counts.

| book x session | rule (replay rank) | HOLD engine: max DD (ref), worst wk, d net/wk (x1.75; $4.84) | L6M engine | controls HOLD / L6M (DD cut %, 6 of 6) | label | exact implementation |
|---|---|---|---|---|---|---|
| A7 asia | fixed target 45, stop 60 (a_T45) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | `bracket A7 asia stop=60 target=45` (grammar supports it; place it ABOVE any `bracket A7 * ...` line, first matching bracket line wins; lots unchanged because the stop is unchanged) |
| H7 asia | give-back exit 60% of best once best >= 30 pts (k_F60_B30) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 30 points and open profit <= (1 - 0.60) x best (give-back 60%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| H7 asia | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| H7 nyam | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| H7 nyam | give-back exit 50% of best once best >= 40 pts (k_F50_B40) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.50) x best (give-back 50%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| K7 nyam | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| K7 nyam | give-back exit 50% of best once best >= 20 pts (k_F50_B20) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 20 points and open profit <= (1 - 0.50) x best (give-back 50%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| M7 nyam | 3-of-4 day-direction vote; AGAINST the day target 20, WITH the day unchanged (d_against_T20) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs (not in the policy grammar): at the signal second compute the 3-of-4 day direction; when the trade is AGAINST it set TradeTgtPts = 20 (stop and lots unchanged) |
| O7 nyam | 3-of-4 day-direction vote; AGAINST the day target 20, WITH the day unchanged (d_against_T20) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs (not in the policy grammar): at the signal second compute the 3-of-4 day direction; when the trade is AGAINST it set TradeTgtPts = 20 (stop and lots unchanged) |
| O7 nyam | 3-of-4 day-direction vote; AGAINST the day target 25, WITH the day unchanged (d_against_T25) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs (not in the policy grammar): at the signal second compute the 3-of-4 day direction; when the trade is AGAINST it set TradeTgtPts = 25 (stop and lots unchanged) |
| P7 asia | give-back exit 50% of best once best >= 40 pts (k_F50_B40) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.50) x best (give-back 50%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| P7 asia | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| P7 nyam | give-back exit 40% of best once best >= 30 pts (k_F40_B30) | not finished | not finished | HOLD [n/f] real n/f; L6M [n/f] real n/f | REPLAY ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 30 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |

Rows owned by W-BD2 (b half-off, c step-down, e HAR remaining range, f atr/squeeze state, g trail) are in autopilot/DS3_BRACKET_DD_BUILD_D.md and DS3_BRACKET_DD_D.md. Families h (structure targets), i (book/tape) and j (other markets) are REPLAY ONLY in this file: h needs tape-derived levels per second, i and j need per-second feature files; they were not built as engine sets.

## Worked examples (3 altered trades per engine cell, L6M, Eastern time)
## Merged section from W-RA (M7 London cap 3) (DS3_BRACKET_DD_BUILD_RA.md)
# DS3_BRACKET_DD_BUILD_RA - M7 London cap 3 on the live-equivalent base JN05W2JL2 (W-RA)

**VERDICT (drawdown first; pass rule = real cell beats ALL its controls on stack max DD in HOLD and L6M and mean not worse than -5%; missing controls = not finished): HOLD: controls missing (0 of 7 cells present) = NOT FINISHED | L6M: controls missing (0 of 7 cells present) = NOT FINISHED. No PASS claim until the controls are in.**

Built epoch 1794847214. Cells: TL3_RA_JL2_M7L_CAP3 (rule: M7, London session 02:00-08:29 ET, block entry once 3 M7 trades closed in the Globex-day session; spec autopilot/SPEC_M7_LONDON_CAP3.md) vs reference TL3_EV_JN05W2JL2. Controls: PL1-3 = random block drawn once per signal second at block rate 0.703 (M7 London, entries with >=1 close); PP1-3 = persistent draw (one draw per session instance and number of closes, so a blocked idea is not redrawn at the next signal; p 0.208 = open-loop keep of cap 3 on the JL2 reference sequence, 0.594). Dollars are base-lot engine net_fee at $1.18/contract RT; columns x175 = live lots; d_mean_484 = mean change repriced at $4.84/contract. Drawdown from cumulative daily P&L of the scope. PATH EFFECT = FREED-BOOK REPLACEMENT (generic): the controls are the baseline.

identity of the placebo branch (PP with p=0, 202610): 642 trades net 27487.58 vs JL2 642 net 27487.58 -> IDENTICAL

Windows landed (cells present / 7) : HOLD 0/7, L6M 0/7, L3M 7/7, GAP 0/7, PREUW 0/7, X' 0/7

## STACK (all books), drawdown first

| win | cell | dd | dd_ref | dd_cut_pct | dd_x175 | ww | ww_ref | stops_wk | stops_ref | d_mean | d_mean_x175 | d_mean_484 | best5 | w2l | n | n_ref |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | M7L_CAP3 | -23715.3 | -22564.6 | -5.1 | -41501.7 | -15143.1 | -13429.6 | 10.3 | 10.3 | 1270.7 | 2223.8 | 1284.4 | 1.0 | 0 | 1870 | 1913 |
| L3M | PL1_M7L_CAP3 | -22396.6 | -22564.6 | 0.7 | -39194.0 | -13152.1 | -13429.6 | 10.3 | 10.3 | -769.6 | -1346.8 | -757.9 | 1.0 | 1 | 1870 | 1913 |
| L3M | PL2_M7L_CAP3 | -24637.3 | -22564.6 | -9.2 | -43115.3 | -15048.0 | -13429.6 | 10.3 | 10.3 | -1024.2 | -1792.3 | -1011.6 | 1.0 | 1 | 1870 | 1913 |
| L3M | PL3_M7L_CAP3 | -26199.5 | -22564.6 | -16.1 | -45849.1 | -13323.1 | -13429.6 | 10.6 | 10.3 | 116.0 | 203.0 | 133.0 | 1.0 | 1 | 1855 | 1913 |
| L3M | PP1_M7L_CAP3 | -23763.4 | -22564.6 | -5.3 | -41586.0 | -12293.9 | -13429.6 | 10.4 | 10.3 | -152.4 | -266.7 | -135.7 | 0.9 | 0 | 1861 | 1913 |
| L3M | PP2_M7L_CAP3 | -23587.9 | -22564.6 | -4.5 | -41278.8 | -13066.6 | -13429.6 | 10.4 | 10.3 | 275.9 | 482.9 | 294.6 | 1.0 | 0 | 1853 | 1913 |
| L3M | PP3_M7L_CAP3 | -25538.1 | -22564.6 | -13.2 | -44691.7 | -15196.0 | -13429.6 | 10.3 | 10.3 | -545.3 | -954.2 | -525.8 | 1.0 | 1 | 1851 | 1913 |

## M7 LONDON slice, drawdown first

| win | cell | dd | dd_ref | dd_cut_pct | dd_x175 | ww | ww_ref | stops_wk | stops_ref | d_mean | d_mean_x175 | d_mean_484 | best5 | w2l | n | n_ref |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| L3M | M7L_CAP3 | -13877.0 | -23405.7 | 40.7 | -24284.7 | -9189.1 | -14641.5 | 0.7 | 0.9 | 1706.1 | 2985.6 | 1725.8 | 1.1 | 1 | 175 | 236 |
| L3M | PL1_M7L_CAP3 | -16003.8 | -23405.7 | 31.6 | -28006.7 | -8087.7 | -14641.5 | 0.5 | 0.9 | 706.1 | 1235.6 | 730.0 | 0.9 | 1 | 161 | 236 |
| L3M | PL2_M7L_CAP3 | -16954.1 | -23405.7 | 27.6 | -29669.6 | -8093.4 | -14641.5 | 0.6 | 0.9 | 548.5 | 959.8 | 571.0 | 0.8 | 0 | 167 | 236 |
| L3M | PL3_M7L_CAP3 | -16507.1 | -23405.7 | 29.5 | -28887.5 | -9363.7 | -14641.5 | 0.8 | 0.9 | 545.9 | 955.2 | 567.3 | 0.7 | 2 | 164 | 236 |
| L3M | PP1_M7L_CAP3 | -15532.6 | -23405.7 | 33.6 | -27182.1 | -6278.5 | -14641.5 | 0.8 | 0.9 | 589.5 | 1031.6 | 613.7 | 0.8 | 1 | 164 | 236 |
| L3M | PP2_M7L_CAP3 | -15034.0 | -23405.7 | 35.8 | -26309.5 | -8244.5 | -14641.5 | 0.8 | 0.9 | 884.4 | 1547.7 | 909.8 | 0.8 | 1 | 158 | 236 |
| L3M | PP3_M7L_CAP3 | -15664.7 | -23405.7 | 33.1 | -27413.2 | -8690.5 | -14641.5 | 0.6 | 0.9 | 449.6 | 786.7 | 480.2 | 0.8 | 2 | 144 | 236 |

## With week 2026-W44 removed from both sides

| win | cell | scope | dd | dd_ref | dd_cut_pct | d_ww | d_mean |
|---|---|---|---|---|---|---|---|
| L3M | M7L_CAP3 | M7:london | -13877.0 | -23405.7 | 40.7 | 5452.4 | 1783.9 |
| L3M | PL1_M7L_CAP3 | M7:london | -16003.8 | -23405.7 | 31.6 | 6553.8 | 691.6 |
| L3M | PL2_M7L_CAP3 | M7:london | -16954.1 | -23405.7 | 27.6 | 6548.1 | 585.3 |
| L3M | PL3_M7L_CAP3 | M7:london | -16507.1 | -23405.7 | 29.5 | 5277.8 | 717.6 |
| L3M | PP1_M7L_CAP3 | M7:london | -15532.6 | -23405.7 | 33.6 | 8363.0 | 680.7 |
| L3M | PP2_M7L_CAP3 | M7:london | -15034.0 | -23405.7 | 35.8 | 6397.0 | 962.3 |
| L3M | PP3_M7L_CAP3 | M7:london | -15664.7 | -23405.7 | 33.1 | 5951.0 | 474.9 |
| L3M | M7L_CAP3 | all | -23715.3 | -22508.4 | -5.4 | -1713.5 | 1348.6 |
| L3M | PL1_M7L_CAP3 | all | -21542.6 | -22508.4 | 4.3 | 277.5 | -784.1 |
| L3M | PL2_M7L_CAP3 | all | -24637.3 | -22508.4 | -9.5 | -1618.4 | -987.3 |
| L3M | PL3_M7L_CAP3 | all | -26199.5 | -22508.4 | -16.4 | 106.5 | 148.4 |
| L3M | PP1_M7L_CAP3 | all | -18805.6 | -22508.4 | 16.5 | 2472.9 | -61.2 |
| L3M | PP2_M7L_CAP3 | all | -21422.1 | -22508.4 | 4.8 | 363.0 | 353.8 |
| L3M | PP3_M7L_CAP3 | all | -25538.1 | -22508.4 | -13.5 | -1766.4 | -519.9 |

## Earlier statements about random placebos (see DS3_REENTRY_ALL.md 5a)
See autopilot/RA_PLACEBO_VOID_LIST.md.

