# DS3_BRACKET_DD_BUILD - non-fixed target rules per book x session, engine on TL3_EV_JN05W2JL2 (written 20:05Z)
**Plain: this table carries only what the engine has finished. A row is CONFIRMED only when the real cell beats all 6 controls on max DD in HOLD AND L6M with mean not more than 5% below the reference; otherwise ENGINE ONLY (controls missing or not beaten) or REPLAY ONLY (replay rows of W-RP / W-RP2 / W-LB2 / W-BD2 are on DS3_TARGET_REPLAY*.md and DS3_BRACKET_DD_D.md). "Keep 58" is not a deliverable: every row names the best non-fixed rule found so far.**

Basis: JL2 base, whole-stack drawdown vs the reference (+ = smaller drawdown), $ per week base lots (x1.75 live; $4.84 repriced), HOLD = 2025-11..2026-04, L6M = 2026-05..10, only that book in that session altered; stop and lots at live values (all rules here leave the 60-point stop unchanged, so constant-risk lots are the same). Controls: placebo = the rule on a persistent-draw random subset (one draw per 5-minute bucket per book and side) of ALL signals at the cell share (day-direction rule: the label shifted 11/23/37 sessions); matched = the rule on a persistent 50% random subset of the cell's own signals (day-direction rule: random labels with the real against-day share). Realised control keep shares are in each control cell trade counts.

| book x session | rule (replay rank) | HOLD engine: max DD (ref), worst wk, d net/wk (x1.75; $4.84) | L6M engine | controls HOLD / L6M (DD cut %, 6 of 6) | label | exact implementation |
|---|---|---|---|---|---|---|
| A7 asia | fixed target 45, stop 60 (a_T45) | -74364 (-74402; +0.1%), ww -31106, +87 (+152; +86) | -21503 (-22565; +4.7%), ww -13002, -572 (-1001; -580) | HOLD [+1.7, -0.5, -4.6, +0.5, +4.2, +0.7] real +0.1%; L6M [n/f] real +4.7% | ENGINE ONLY | `bracket A7 asia stop=60 target=45` (grammar supports it; place it ABOVE any `bracket A7 * ...` line, first matching bracket line wins; lots unchanged because the stop is unchanged) |
| H7 asia | give-back exit 60% of best once best >= 30 pts (k_F60_B30) | -72429 (-74402; +2.7%), ww -33394, +1033 (+1808; +1030) | -25023 (-22565; -10.9%), ww -13430, -1271 (-2224; -1265) | HOLD [+2.7, +0.0, -8.1, +5.6, -0.1, -5.1] real +2.7%; L6M [n/f] real -10.9% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 30 points and open profit <= (1 - 0.60) x best (give-back 60%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| H7 asia | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | -71746 (-74402; +3.6%), ww -31074, +378 (+661; +377) | -23908 (-22565; -6.0%), ww -13430, -841 (-1472; -840) | HOLD [-1.5, +0.0, -3.9, +3.4, -3.3, -1.4] real +3.6%; L6M [n/f] real -6.0% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| H7 nyam | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | -72537 (-74402; +2.5%), ww -31211, +72 (+125; +71) | -22565 (-22565; +0.0%), ww -11690, +82 (+143; +82) | HOLD [-0.7, +0.0, -1.4, +0.0, +2.5, +2.5] real +2.5%; L6M [n/f] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| H7 nyam | give-back exit 50% of best once best >= 40 pts (k_F50_B40) | -72627 (-74402; +2.4%), ww -31211, +48 (+84; +48) | -22565 (-22565; +0.0%), ww -11775, +97 (+169; +97) | HOLD [-0.9, +0.0, -1.6, +0.0, +2.4, +2.4] real +2.4%; L6M [n/f] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.50) x best (give-back 50%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| K7 nyam | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | -75309 (-74402; -1.2%), ww -30699, +125 (+218; +118) | -23010 (-22565; -2.0%), ww -13430, +263 (+460; +257) | HOLD [-0.3, +0.7, -4.7, -3.9, -0.9, +1.3] real -1.2%; L6M [n/f] real -2.0% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| K7 nyam | give-back exit 50% of best once best >= 20 pts (k_F50_B20) | -78354 (-74402; -5.3%), ww -31604, -356 (-622; -370) | -24340 (-22565; -7.9%), ww -14211, -345 (-603; -354) | HOLD [+7.5, -6.2, -6.3, -9.9, -3.6, -2.0] real -5.3%; L6M [n/f] real -7.9% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 20 points and open profit <= (1 - 0.50) x best (give-back 50%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| M7 nyam | 3-of-4 day-direction vote; AGAINST the day target 20, WITH the day unchanged (d_against_T20) | -74402 (-74402; +0.0%), ww -31211, +0 (+0; +0) | -22565 (-22565; +0.0%), ww -13430, +0 (+0; +0) | HOLD [+0.4, +4.4, -2.8, -0.4, +1.5, -1.1] real +0.0%; L6M [n/f] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs (not in the policy grammar): at the signal second compute the 3-of-4 day direction; when the trade is AGAINST it set TradeTgtPts = 20 (stop and lots unchanged) |
| O7 nyam | 3-of-4 day-direction vote; AGAINST the day target 20, WITH the day unchanged (d_against_T20) | -74402 (-74402; +0.0%), ww -31211, +0 (+0; +0) | -22565 (-22565; +0.0%), ww -13430, +0 (+0; +0) | HOLD [+0.0, +0.0, -0.4, +0.0, +0.0, +0.0] real +0.0%; L6M [n/f] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs (not in the policy grammar): at the signal second compute the 3-of-4 day direction; when the trade is AGAINST it set TradeTgtPts = 20 (stop and lots unchanged) |
| O7 nyam | 3-of-4 day-direction vote; AGAINST the day target 25, WITH the day unchanged (d_against_T25) | -74402 (-74402; +0.0%), ww -31211, +0 (+0; +0) | -22565 (-22565; +0.0%), ww -13430, +0 (+0; +0) | HOLD [+0.0, +0.0, -0.1, +0.0, +0.0, +0.0] real +0.0%; L6M [n/f] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs (not in the policy grammar): at the signal second compute the 3-of-4 day direction; when the trade is AGAINST it set TradeTgtPts = 25 (stop and lots unchanged) |
| P7 asia | give-back exit 50% of best once best >= 40 pts (k_F50_B40) | -75505 (-74402; -1.5%), ww -34923, +80 (+139; +59) | -30727 (-22565; -36.2%), ww -17244, -1978 (-3462; -2002) | HOLD [-0.7, +1.3, +3.2, +13.0, +2.8, +3.1] real -1.5%; L6M [n/f] real -36.2% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.50) x best (give-back 50%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| P7 asia | give-back exit 40% of best once best >= 40 pts (k_F40_B40) | -74710 (-74402; -0.4%), ww -35108, +317 (+555; +290) | -31640 (-22565; -40.2%), ww -18172, -2989 (-5232; -3022) | HOLD [-1.7, +1.7, -0.4, +12.1, +2.2, +2.5] real -0.4%; L6M [n/f] real -40.2% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 40 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |
| P7 nyam | give-back exit 40% of best once best >= 30 pts (k_F40_B30) | -73222 (-74402; +1.6%), ww -31662, -132 (-231; -133) | -22565 (-22565; +0.0%), ww -13430, -308 (-538; -308) | HOLD [+7.6, -3.8, -11.4, +2.0, +0.9, -1.0] real +1.6%; L6M [n/f] real +0.0% | ENGINE ONLY | CODE CHANGE in DS7.cs: exit at market when best open profit >= 30 points and open profit <= (1 - 0.40) x best (give-back 40%); policy grammar has `dd` (drawdown from MFE in points) but not a fraction of the best |

Rows owned by W-BD2 (b half-off, c step-down, e HAR remaining range, f atr/squeeze state, g trail) are in autopilot/DS3_BRACKET_DD_BUILD_D.md and DS3_BRACKET_DD_D.md. Families h (structure targets), i (book/tape) and j (other markets) are REPLAY ONLY in this file: h needs tape-derived levels per second, i and j need per-second feature files; they were not built as engine sets.

## Worked examples (3 altered trades per engine cell, L6M, Eastern time)
**A7 asia, a_T45**
- entry 2026-05-04 21:22:02 ET at 27808.75, exit 00:03:19 ET at 27853.75 (Target), lots 1, net $899.
- entry 2026-05-05 18:15:01 ET at 28260.25, exit 18:52:09 ET at 28305.25 (Target), lots 1, net $899.
- entry 2026-05-07 21:17:01 ET at 28761.25, exit 01:30:13 ET at 28806.25 (Target), lots 1, net $899.

**H7 asia, k_F60_B30**
- entry 2026-04-30 19:50:01 ET at 27615.00, exit 22:33:57 ET at 27632.50 (D10GiveBack), lots 1, net $349.
- entry 2026-05-06 23:40:01 ET at 28692.00, exit 02:06:56 ET at 28708.25 (D10GiveBack), lots 1, net $324.
- entry 2026-05-19 20:15:01 ET at 28830.75, exit 20:17:28 ET at 28817.75 (D10GiveBack), lots 1, net $259.

**H7 asia, k_F40_B40**
- entry 2026-04-30 19:50:01 ET at 27615.00, exit 21:41:24 ET at 27641.50 (D10GiveBack), lots 1, net $529.
- entry 2026-05-06 23:40:01 ET at 28692.00, exit 02:46:10 ET at 28726.50 (D10GiveBack), lots 1, net $689.
- entry 2026-05-19 22:45:01 ET at 28886.12, exit 23:11:36 ET at 28861.25 (D10GiveBack), lots 2, net $993.

**H7 nyam, k_F40_B40**
- entry 2026-05-05 11:50:01 ET at 28142.00, exit 14:51:52 ET at 28168.50 (D10GiveBack), lots 1, net $529.
- entry 2026-05-19 10:20:01 ET at 28711.75, exit 10:22:30 ET at 28677.50 (D10GiveBack), lots 1, net $684.
- entry 2026-05-26 10:10:01 ET at 30003.75, exit 10:21:43 ET at 30039.25 (D10GiveBack), lots 1, net $709.

**H7 nyam, k_F50_B40**
- entry 2026-05-05 11:50:01 ET at 28142.00, exit 14:52:20 ET at 28163.75 (D10GiveBack), lots 1, net $434.
- entry 2026-05-19 10:20:01 ET at 28711.75, exit 10:23:07 ET at 28686.75 (D10GiveBack), lots 1, net $499.
- entry 2026-06-29 10:05:01 ET at 29542.00, exit 10:07:12 ET at 29510.25 (D10GiveBack), lots 1, net $634.

**K7 nyam, k_F40_B40**
- entry 2026-05-01 10:36:01 ET at 27803.50, exit 10:38:31 ET at 27771.50 (D10GiveBack), lots 1, net $639.
- entry 2026-05-01 11:21:01 ET at 27860.25, exit 11:50:31 ET at 27884.75 (D10GiveBack), lots 1, net $489.
- entry 2026-05-05 11:15:01 ET at 28132.75, exit 14:52:13 ET at 28165.50 (D10GiveBack), lots 1, net $654.

**K7 nyam, k_F50_B20**
- entry 2026-05-01 10:36:01 ET at 27803.50, exit 10:37:06 ET at 27785.00 (D10GiveBack), lots 1, net $369.
- entry 2026-05-01 11:21:01 ET at 27860.25, exit 11:50:31 ET at 27879.50 (D10GiveBack), lots 1, net $384.
- entry 2026-05-05 11:15:01 ET at 28132.75, exit 14:53:15 ET at 28159.75 (D10GiveBack), lots 1, net $539.

**M7 nyam, d_against_T20**
- entry 2026-05-01 10:20:01 ET at 27878.50, exit 10:33:08 ET at 27831.33 (StateCut), lots 1, net $-945. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1
- entry 2026-05-01 11:21:01 ET at 27860.25, exit 12:33:12 ET at 27822.83 (StateCut), lots 1, net $-750. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, -1, 1]; side +1
- entry 2026-05-05 10:02:01 ET at 28097.75, exit 10:15:07 ET at 28038.00 (StopJoin), lots 1, net $-1196. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1

**O7 nyam, d_against_T20**
- entry 2026-05-01 09:42:01 ET at 27785.00, exit 09:59:59 ET at 27875.00 (Target), lots 1, net $1799. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1
- entry 2026-05-05 09:43:01 ET at 28066.75, exit 12:27:49 ET at 28108.50 (BookLock), lots 1, net $834. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1
- entry 2026-05-06 09:43:01 ET at 28439.25, exit 10:06:54 ET at 28401.75 (Stop), lots 1, net $-751. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, -1, 1]; side +1

**O7 nyam, d_against_T25**
- entry 2026-05-01 09:42:01 ET at 27785.00, exit 09:59:59 ET at 27875.00 (Target), lots 1, net $1799. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1
- entry 2026-05-05 09:43:01 ET at 28066.75, exit 12:27:49 ET at 28108.50 (BookLock), lots 1, net $834. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, 1, 1]; side +1
- entry 2026-05-06 09:43:01 ET at 28439.25, exit 10:06:54 ET at 28401.75 (Stop), lots 1, net $-751. day direction at the signal second (sess/18:00/VWAP/60m/vote) = [1, 1, 1, -1, 1]; side +1

**P7 asia, k_F50_B40**
- entry 2026-04-30 19:13:02 ET at 27589.75, exit 21:01:52 ET at 27614.75 (D10GiveBack), lots 2, net $998.
- entry 2026-04-30 21:12:01 ET at 27633.88, exit 23:36:13 ET at 27652.94 (D10GiveBack), lots 4, net $1520.
- entry 2026-05-03 20:06:01 ET at 27844.81, exit 21:04:02 ET at 27871.56 (D10GiveBack), lots 4, net $2135.

**P7 asia, k_F40_B40**
- entry 2026-04-30 19:13:02 ET at 27589.75, exit 21:01:48 ET at 27617.00 (D10GiveBack), lots 2, net $1088.
- entry 2026-04-30 21:12:01 ET at 27633.88, exit 23:32:33 ET at 27656.94 (D10GiveBack), lots 4, net $1840.
- entry 2026-05-01 00:16:24 ET at 27630.81, exit 03:52:40 ET at 27602.50 (D10GiveBack), lots 4, net $2260.

**P7 nyam, k_F40_B30**
- entry 2026-05-06 10:50:16 ET at 28536.25, exit 11:37:04 ET at 28566.75 (D10GiveBack), lots 1, net $609.
- entry 2026-05-13 11:40:31 ET at 29339.75, exit 11:45:21 ET at 29368.00 (D10GiveBack), lots 1, net $564.
- entry 2026-05-26 11:40:31 ET at 29973.50, exit 11:51:00 ET at 29948.50 (D10GiveBack), lots 1, net $499.

## Merged section from W-RA (M7 London cap 3) (DS3_BRACKET_DD_BUILD_RA.md)
# DS3_BRACKET_DD_BUILD_RA - M7 London cap 3 on the live-equivalent base JN05W2JL2 (W-RA)

**VERDICT (drawdown first; pass rule = real cell beats ALL its controls on stack max DD in HOLD and L6M and mean not worse than -5%; missing controls = not finished): HOLD: stack DD real -70924 vs ref -74402, best control -63564 -> does NOT beat all controls on DD; mean +1012 $/wk (6.6% of ref) -> ok | L6M: stack DD real -23715 vs ref -22565, best control -22397 -> does NOT beat all controls on DD; mean +1747 $/wk (7.9% of ref) -> ok. No PASS claim until the controls are in.**

Built epoch 1794859330. Cells: TL3_RA_JL2_M7L_CAP3 (rule: M7, London session 02:00-08:29 ET, block entry once 3 M7 trades closed in the Globex-day session; spec autopilot/SPEC_M7_LONDON_CAP3.md) vs reference TL3_EV_JN05W2JL2. Controls: PL1-3 = random block drawn once per signal second at block rate 0.703 (M7 London, entries with >=1 close); PP1-3 = persistent draw (one draw per session instance and number of closes, so a blocked idea is not redrawn at the next signal; p 0.208 = open-loop keep of cap 3 on the JL2 reference sequence, 0.594). Dollars are base-lot engine net_fee at $1.18/contract RT; columns x175 = live lots; d_mean_484 = mean change repriced at $4.84/contract. Drawdown from cumulative daily P&L of the scope. PATH EFFECT = FREED-BOOK REPLACEMENT (generic): the controls are the baseline.

identity of the placebo branch (PP with p=0, 202610): 642 trades net 27487.58 vs JL2 642 net 27487.58 -> IDENTICAL

Windows landed (cells present / 7) : HOLD 7/7, L6M 7/7, L3M 7/7, GAP 0/7, PREUW 0/7, X' 0/7

## STACK (all books), drawdown first

| win | cell | dd | dd_ref | dd_cut_pct | dd_x175 | ww | ww_ref | stops_wk | stops_ref | d_mean | d_mean_x175 | d_mean_484 | best5 | w2l | n | n_ref |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HOLD | M7L_CAP3 | -70923.9 | -74401.8 | 4.7 | -124116.8 | -30595.5 | -31210.9 | 10.3 | 10.5 | 1011.6 | 1770.3 | 1029.2 | 1.0 | 1 | 7166 | 7380 |
| HOLD | PL1_M7L_CAP3 | -67021.1 | -74401.8 | 9.9 | -117286.9 | -34187.6 | -31210.9 | 10.4 | 10.5 | 124.1 | 217.1 | 140.9 | 1.0 | 2 | 7171 | 7380 |
| HOLD | PL2_M7L_CAP3 | -63564.4 | -74401.8 | 14.6 | -111237.8 | -30872.9 | -31210.9 | 10.4 | 10.5 | -100.7 | -176.3 | -82.6 | 1.0 | 2 | 7163 | 7380 |
| HOLD | PL3_M7L_CAP3 | -65459.9 | -74401.8 | 12.0 | -114554.8 | -29477.7 | -31210.9 | 10.5 | 10.5 | 741.6 | 1297.8 | 758.3 | 1.0 | 3 | 7172 | 7380 |
| HOLD | PP1_M7L_CAP3 | -64352.7 | -74401.8 | 13.5 | -112617.3 | -31210.9 | -31210.9 | 10.4 | 10.5 | 814.0 | 1424.4 | 831.8 | 1.0 | 1 | 7168 | 7380 |
| HOLD | PP2_M7L_CAP3 | -64370.5 | -74401.8 | 13.5 | -112648.4 | -31210.9 | -31210.9 | 10.4 | 10.5 | 343.8 | 601.6 | 363.3 | 1.0 | 1 | 7145 | 7380 |
| HOLD | PP3_M7L_CAP3 | -66190.1 | -74401.8 | 11.0 | -115832.7 | -30595.5 | -31210.9 | 10.3 | 10.5 | 361.9 | 633.3 | 382.9 | 1.0 | 1 | 7118 | 7380 |
| L6M | M7L_CAP3 | -23715.3 | -22564.6 | -5.1 | -41501.7 | -15143.1 | -13429.6 | 10.7 | 10.9 | 1747.4 | 3057.9 | 1768.0 | 1.1 | 0 | 4034 | 4161 |
| L6M | PL1_M7L_CAP3 | -22396.6 | -22564.6 | 0.7 | -39194.0 | -13152.1 | -13429.6 | 10.7 | 10.9 | 108.5 | 189.9 | 125.9 | 1.0 | 1 | 4047 | 4161 |
| L6M | PL2_M7L_CAP3 | -24637.3 | -22564.6 | -9.2 | -43115.3 | -15048.0 | -13429.6 | 10.7 | 10.9 | -519.3 | -908.8 | -498.7 | 1.0 | 1 | 4028 | 4161 |
| L6M | PL3_M7L_CAP3 | -26199.5 | -22564.6 | -16.1 | -45849.1 | -13323.1 | -13429.6 | 11.0 | 10.9 | 578.6 | 1012.6 | 599.1 | 1.0 | 1 | 4031 | 4161 |
| L6M | PP1_M7L_CAP3 | -23763.4 | -22564.6 | -5.3 | -41586.0 | -12293.9 | -13429.6 | 10.8 | 10.9 | 1203.7 | 2106.5 | 1225.0 | 1.0 | 0 | 4031 | 4161 |
| L6M | PP2_M7L_CAP3 | -23587.9 | -22564.6 | -4.5 | -41278.8 | -13066.6 | -13429.6 | 10.8 | 10.9 | 942.6 | 1649.6 | 965.5 | 1.0 | 0 | 4023 | 4161 |
| L6M | PP3_M7L_CAP3 | -25538.1 | -22564.6 | -13.2 | -44691.7 | -15196.0 | -13429.6 | 10.6 | 10.9 | 738.8 | 1292.8 | 763.7 | 1.1 | 1 | 4001 | 4161 |
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
| HOLD | M7L_CAP3 | -13877.0 | -54248.4 | 74.4 | -24284.7 | -9211.1 | -14641.5 | 0.4 | 0.7 | 1086.3 | 1901.0 | 1110.2 | 0.9 | 3 | 674 | 963 |
| HOLD | PL1_M7L_CAP3 | -28451.4 | -54248.4 | 47.6 | -49789.9 | -8662.4 | -14641.5 | 0.4 | 0.7 | 752.2 | 1316.3 | 778.3 | 0.7 | 5 | 652 | 963 |
| HOLD | PL2_M7L_CAP3 | -32327.4 | -54248.4 | 40.4 | -56572.9 | -8255.8 | -14641.5 | 0.4 | 0.7 | 660.1 | 1155.1 | 685.3 | 0.7 | 4 | 669 | 963 |
| HOLD | PL3_M7L_CAP3 | -24580.7 | -54248.4 | 54.7 | -43016.3 | -9363.7 | -14641.5 | 0.6 | 0.7 | 905.2 | 1584.1 | 929.6 | 1.1 | 7 | 658 | 963 |
| HOLD | PP1_M7L_CAP3 | -27757.4 | -54248.4 | 48.8 | -48575.5 | -8986.9 | -14641.5 | 0.4 | 0.7 | 892.4 | 1561.7 | 920.1 | 0.8 | 5 | 632 | 963 |
| HOLD | PP2_M7L_CAP3 | -29760.3 | -54248.4 | 45.1 | -52080.5 | -10579.7 | -14641.5 | 0.4 | 0.7 | 378.0 | 661.6 | 407.3 | 0.8 | 5 | 612 | 963 |
| HOLD | PP3_M7L_CAP3 | -16954.8 | -54248.4 | 68.7 | -29670.9 | -10917.8 | -14641.5 | 0.4 | 0.7 | 687.9 | 1203.8 | 718.0 | 0.9 | 6 | 599 | 963 |
| L6M | M7L_CAP3 | -13877.0 | -37263.0 | 62.8 | -24284.7 | -9189.1 | -14641.5 | 0.5 | 0.8 | 1945.3 | 3404.3 | 1971.5 | 1.1 | 1 | 349 | 512 |
| L6M | PL1_M7L_CAP3 | -16003.8 | -37263.0 | 57.1 | -28006.7 | -8087.7 | -14641.5 | 0.3 | 0.8 | 893.4 | 1563.5 | 920.7 | 0.7 | 2 | 346 | 512 |
| L6M | PL2_M7L_CAP3 | -16954.1 | -37263.0 | 54.5 | -29669.6 | -8093.4 | -14641.5 | 0.4 | 0.8 | 747.2 | 1307.7 | 774.1 | 0.6 | 2 | 349 | 512 |
| L6M | PL3_M7L_CAP3 | -24580.7 | -37263.0 | 34.0 | -43016.3 | -9363.7 | -14641.5 | 0.7 | 0.8 | 880.4 | 1540.8 | 908.0 | 0.7 | 4 | 337 | 512 |
| L6M | PP1_M7L_CAP3 | -15532.6 | -37263.0 | 58.3 | -27182.1 | -6278.5 | -14641.5 | 0.5 | 0.8 | 1279.5 | 2239.2 | 1310.6 | 0.7 | 2 | 324 | 512 |
| L6M | PP2_M7L_CAP3 | -15034.0 | -37263.0 | 59.7 | -26309.5 | -8244.5 | -14641.5 | 0.5 | 0.8 | 1033.5 | 1808.6 | 1065.3 | 0.8 | 2 | 318 | 512 |
| L6M | PP3_M7L_CAP3 | -15664.7 | -37263.0 | 58.0 | -27413.2 | -8690.5 | -14641.5 | 0.3 | 0.8 | 1115.3 | 1951.8 | 1148.7 | 0.9 | 3 | 305 | 512 |
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
| HOLD | M7L_CAP3 | M7:london | -13877.0 | -54248.4 | 74.4 | 5430.4 | 1105.9 |
| HOLD | PL1_M7L_CAP3 | M7:london | -28451.4 | -54248.4 | 47.6 | 5979.1 | 748.5 |
| HOLD | PL2_M7L_CAP3 | M7:london | -32327.4 | -54248.4 | 40.4 | 6385.7 | 669.3 |
| HOLD | PL3_M7L_CAP3 | M7:london | -24580.7 | -54248.4 | 54.7 | 5277.8 | 948.5 |
| HOLD | PP1_M7L_CAP3 | M7:london | -27757.4 | -54248.4 | 48.8 | 5654.6 | 915.4 |
| HOLD | PP2_M7L_CAP3 | M7:london | -29760.3 | -54248.4 | 45.1 | 4061.8 | 397.7 |
| HOLD | PP3_M7L_CAP3 | M7:london | -16954.8 | -54248.4 | 68.7 | 3723.7 | 694.3 |
| L3M | M7L_CAP3 | M7:london | -13877.0 | -23405.7 | 40.7 | 5452.4 | 1783.9 |
| L3M | PL1_M7L_CAP3 | M7:london | -16003.8 | -23405.7 | 31.6 | 6553.8 | 691.6 |
| L3M | PL2_M7L_CAP3 | M7:london | -16954.1 | -23405.7 | 27.6 | 6548.1 | 585.3 |
| L3M | PL3_M7L_CAP3 | M7:london | -16507.1 | -23405.7 | 29.5 | 5277.8 | 717.6 |
| L3M | PP1_M7L_CAP3 | M7:london | -15532.6 | -23405.7 | 33.6 | 8363.0 | 680.7 |
| L3M | PP2_M7L_CAP3 | M7:london | -15034.0 | -23405.7 | 35.8 | 6397.0 | 962.3 |
| L3M | PP3_M7L_CAP3 | M7:london | -15664.7 | -23405.7 | 33.1 | 5951.0 | 474.9 |
| L6M | M7L_CAP3 | M7:london | -13877.0 | -37263.0 | 62.8 | 5452.4 | 1984.3 |
| L6M | PL1_M7L_CAP3 | M7:london | -16003.8 | -37263.0 | 57.1 | 6553.8 | 886.2 |
| L6M | PL2_M7L_CAP3 | M7:london | -16954.1 | -37263.0 | 54.5 | 6548.1 | 765.7 |
| L6M | PL3_M7L_CAP3 | M7:london | -24580.7 | -37263.0 | 34.0 | 5277.8 | 966.3 |
| L6M | PP1_M7L_CAP3 | M7:london | -15532.6 | -37263.0 | 58.3 | 8363.0 | 1325.2 |
| L6M | PP2_M7L_CAP3 | M7:london | -15034.0 | -37263.0 | 59.7 | 6397.0 | 1072.4 |
| L6M | PP3_M7L_CAP3 | M7:london | -15664.7 | -37263.0 | 58.0 | 5951.0 | 1128.0 |
| HOLD | M7L_CAP3 | all | -70923.9 | -74401.8 | 4.7 | 615.4 | 1031.2 |
| HOLD | PL1_M7L_CAP3 | all | -67021.1 | -74401.8 | 9.9 | -2976.6 | 120.4 |
| HOLD | PL2_M7L_CAP3 | all | -63564.4 | -74401.8 | 14.6 | 338.0 | -91.4 |
| HOLD | PL3_M7L_CAP3 | all | -65459.9 | -74401.8 | 12.0 | 1733.2 | 749.7 |
| HOLD | PP1_M7L_CAP3 | all | -64352.7 | -74401.8 | 13.5 | 0.0 | 836.9 |
| HOLD | PP2_M7L_CAP3 | all | -64370.5 | -74401.8 | 13.5 | 0.0 | 363.4 |
| HOLD | PP3_M7L_CAP3 | all | -66190.1 | -74401.8 | 11.0 | 615.4 | 368.3 |
| L3M | M7L_CAP3 | all | -23715.3 | -22508.4 | -5.4 | -1713.5 | 1348.6 |
| L3M | PL1_M7L_CAP3 | all | -21542.6 | -22508.4 | 4.3 | 277.5 | -784.1 |
| L3M | PL2_M7L_CAP3 | all | -24637.3 | -22508.4 | -9.5 | -1618.4 | -987.3 |
| L3M | PL3_M7L_CAP3 | all | -26199.5 | -22508.4 | -16.4 | 106.5 | 148.4 |
| L3M | PP1_M7L_CAP3 | all | -18805.6 | -22508.4 | 16.5 | 2472.9 | -61.2 |
| L3M | PP2_M7L_CAP3 | all | -21422.1 | -22508.4 | 4.8 | 363.0 | 353.8 |
| L3M | PP3_M7L_CAP3 | all | -25538.1 | -22508.4 | -13.5 | -1766.4 | -519.9 |
| L6M | M7L_CAP3 | all | -23715.3 | -22508.4 | -5.4 | -1713.5 | 1786.3 |
| L6M | PL1_M7L_CAP3 | all | -21542.6 | -22508.4 | 4.3 | 277.5 | 101.3 |
| L6M | PL2_M7L_CAP3 | all | -24637.3 | -22508.4 | -9.5 | -1618.4 | -500.9 |
| L6M | PL3_M7L_CAP3 | all | -26199.5 | -22508.4 | -16.4 | 106.5 | 594.8 |
| L6M | PP1_M7L_CAP3 | all | -19463.8 | -22508.4 | 13.5 | 2472.9 | 1249.3 |
| L6M | PP2_M7L_CAP3 | all | -21422.1 | -22508.4 | 4.8 | 363.0 | 981.6 |
| L6M | PP3_M7L_CAP3 | all | -25538.1 | -22508.4 | -13.5 | -1766.4 | 751.4 |

## Placebo validity: realized M7 London keep share (entries with >=1 earlier close in the instance) vs the real cell, HOLD

A control is INVALID when its kept-entry count differs from the real cell by more than 5%.

| control | kept_n_ge2 | real_kept_n_ge2 | ratio_to_real | trades | real_trades | INVALID_CONTROL |
|---|---|---|---|---|---|---|
| PL1_M7L_CAP3 | 401 | 423 | 0.948 | 652 | 674 | True |
| PL2_M7L_CAP3 | 418 | 423 | 0.988 | 669 | 674 | False |
| PL3_M7L_CAP3 | 407 | 423 | 0.962 | 658 | 674 | False |
| PP1_M7L_CAP3 | 381 | 423 | 0.901 | 632 | 674 | True |
| PP2_M7L_CAP3 | 361 | 423 | 0.853 | 612 | 674 | True |
| PP3_M7L_CAP3 | 348 | 423 | 0.823 | 599 | 674 | True |

## Week-clustered statistics, M7 London slice, HOLD (52 weeks; delta vs reference)

| cell | weeks | mean_wk | t_cluster | ci90_lo | ci90_hi | pos_weeks | mean_noW44 | mean_wo_top3 | dd_ref | dd_cell | P_dd_shallower |
|---|---|---|---|---|---|---|---|---|---|---|---|
| M7L_CAP3 | 52 | 1089.25 | 2.64 | 431.62 | 1766.69 | 0.62 | 1130.67 | 615.01 | -48166.20 | -11416.62 | 0.99 |
| PL1_M7L_CAP3 | 52 | 754.23 | 1.77 | 48.12 | 1455.79 | 0.56 | 765.28 | 321.35 | -48166.20 | -27663.08 | 0.95 |
| PL2_M7L_CAP3 | 52 | 661.87 | 1.56 | -38.24 | 1344.24 | 0.52 | 684.34 | 250.51 | -48166.20 | -31539.08 | 0.93 |
| PL3_M7L_CAP3 | 52 | 907.71 | 2.13 | 211.08 | 1599.63 | 0.60 | 969.76 | 578.53 | -48166.20 | -19751.14 | 0.98 |
| PP1_M7L_CAP3 | 52 | 894.85 | 1.87 | 144.35 | 1691.06 | 0.54 | 935.90 | 415.62 | -48166.20 | -24070.96 | 0.95 |
| PP2_M7L_CAP3 | 52 | 379.08 | 0.88 | -303.16 | 1081.07 | 0.52 | 406.57 | -67.15 | -48166.20 | -24229.10 | 0.90 |
| PP3_M7L_CAP3 | 52 | 689.75 | 1.71 | 60.52 | 1356.88 | 0.50 | 709.81 | 263.01 | -48166.20 | -14668.32 | 0.97 |

## Earlier statements about random placebos (see DS3_REENTRY_ALL.md 5a)
See autopilot/RA_PLACEBO_VOID_LIST.md.

