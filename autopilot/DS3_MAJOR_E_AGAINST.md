# DS3_MAJOR_E_AGAINST - against-the-day streak rules on JL3 (W-ME, MAJOR PART E)

Page refreshed 2026-11-25 07:46Z (unattended loop me_loop). Data end 2026-10-31 (JL3 months 202304..202610). FIRST PASS.

PLAIN SUMMARY

1. Tried (re-aimed 11-17 14:26Z at what a manual trader sees): (a) same-side loser streak (vote-free) as skip/half, with a resume-at-new-session-extreme and a per-book version; (b) extended-entry bucket (how far price already ran: ATR from session open / 18:00 open, VWAP sigma, share of typical session range used, chase count, minutes since extreme) as SIZE and as TARGET/STOP, with a drawdown-period table; (c) after a book cut, halve or tighten the other same-side positions; the ordered vote rules (H/S/P1/P2) stay only as reference rows.
2. Key finding: the 2025-11-17..12-10 losers were WITH the causal 3-of-4 vote (333 trades -78.0k; against 26 trades +3.4k): the books enter after the move and the reversal comes later, so only hindsight labels show "against the day".
3. Screen: the ordered vote rules bind on 0.0-0.6% of trades and do nothing (P2 press hurts HOLD by 15-21%); extended-entry halving improves ulcer 6-12% in L6M but costs 1.5-4.7k/wk and is NOT better than random halving of the same share (p_ulc 0.2-0.9, no tier); the extended bucket earns MORE per trade (about $110 vs $60) but concentrates the drawdown (-39k of the path in the open_atr bucket).
4. What survives the screen: same-side loser K=2 pause 30 min (LS_K2_M30: ulcer +4% to +7% in TRAIN/L6M/L3M/HOLD at flat mean, screen tier LEAD, post-hoc); the longer pauses help HOLD (+14%/+19%) but hurt L6M. Nothing is CONFIRMED; DS7 needs nothing until the exact tiers below land.
5. Next: exact cells on the engine queue (identity IDX first; 0 queue lines pending, 2005 run-months landed); stage 2 adds 34 matched controls for the best cells automatically; this page refreshes every 30 min.

HEADER: trials counted = 30 screen configs (every one counted) + 6 exact picks; correction: no White RC/SPA/DSR run on this family yet (best-of picked per family on TRAIN only; DSR/BH on the ledger row ME in TRIALS_LEDGER.csv); PBO not computed; selection = walk-forward (choose <=2025-10, freeze), HOLD and L6M untouched for the 6 frozen exact picks; the screen tier table below is path arithmetic (kept trades keep their outcome; freed-book effects NOT in the screen). Prereg autopilot/PREREG_ME.md (screen run before the file was written, declared in DECISIONS.md).

## 1. Why the ordered rule is nearly inert (causal vote vs hindsight)

Whole JL3 sample (19,552 trades): vote = 0 for 11.4%, AGAINST 7.1%, WITH 81.5% of trades; mean $/trade against +37, with +82, neutral +67; loser share 54.6% against vs 54.7% with. HOLD drawdown path 2025-11-17..12-10 (396 trades, base lots), by each causal day label at the signal second:

| day label at signal | against n | against $ | with n | with $ | neutral n | neutral $ |
|--|--|--|--|--|--|--|
| session open | 64 | 1,589 | 328 | -71,946 | 4 | 1,660 |
| 18:00 open | 125 | -4,520 | 269 | -65,443 | 2 | 1,265 |
| session VWAP | 32 | 10,914 | 362 | -80,005 | 2 | 394 |
| close 60 min earlier | 39 | 13,264 | 357 | -81,962 | 0 | 0 |
| 3-of-4 vote (v2.0) | 26 | 3,405 | 333 | -78,018 | 37 | 5,916 |

Every causal label puts the drawdown losers on the WITH side: the books enter after the move has shown (trend-following entry), the reversal comes after. Only the hindsight close-open label (DS3_DD_HOLD: against 167 trades -53.5k) shows an against-the-day loss; it cannot be known at the signal second. So a rule keyed on "losers against the vote" cannot see the drawdown. The extension below keys on the repeated same-side loss itself (the trader behaviour: no repeated re-entry on a side that keeps losing).

## 2. Screen (path arithmetic on the JL3 trade list, 19,552 trades, base lots)

imp% = ulcer reduction vs JL3 in the window (+ = smaller ulcer); dMean = change in mean $/week; p_ulc = percentile of the real ulcer among <=30 persistent-draw controls matched on share affected per session (valid = share within max(min(.05,.25 share),.002)); share = trades affected (skipped or resized). Ordered families first, then the extension. Tier = pr_cands.tier_of on windows L3M/L6M/HOLD/GAP/PREUW/X' (older windows run here).

| config | share | TRAIN imp% | dMean | L6M imp% | dMean | p_ulc | L3M imp% | p_ulc | HOLD imp% | dMean | p_ulc | GAP imp% | PREUW imp% | X' imp% | tier |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| H_K2 | 0.17% | +0.5 | +15 | -0.4 | -97 | 0.13 | -0.7 | 0.17 | -0.6 | +76 | 0.27 | +0.0 | +1.2 | +0.0 | FAIL |
| S_K2_M30 | 0.04% | -0.0 | -9 | +0.3 | -39 | 0.43 | +1.0 | 0.70 | -1.4 | +125 | 0.10 | +0.0 | +0.0 | -0.1 | FAIL |
| S_K2_M60 | 0.10% | -0.0 | -8 | -1.6 | -114 | 0.07 | -1.9 | 0.03 | -1.1 | +174 | 0.27 | +0.0 | -0.0 | -0.1 | FAIL |
| S_K2_M120 | 0.13% | +0.2 | +9 | -1.2 | -93 | 0.13 | -1.4 | 0.10 | -1.7 | +131 | 0.20 | +0.0 | +0.6 | -0.1 | FAIL |
| P1_K2 | 0.63% | +0.0 | -65 | -6.3 | +244 | 0.07 | -7.1 | 0.03 | -7.5 | -500 | 0.00 | +0.2 | +1.7 | -0.8 | FAIL |
| P2_K2 | 11.33% | -10.2 | +10 | -25.4 | +1346 | 0.37 | -29.7 | 0.07 | -14.6 | +2541 | 0.43 | -0.1 | -20.7 | -2.4 | FAIL |
| H_K3 | 0.03% | +0.0 | +0 | +0.0 | +0 | 0.35 | +0.0 | 0.43 | +0.0 | +0 | n/a | +0.0 | +0.0 | +0.0 | FAIL |
| S_K3_M30 | 0.01% | -0.7 | -8 | +0.0 | +0 | n/a | +0.0 | n/a | +0.0 | +0 | n/a | +0.0 | -1.6 | +0.0 | NOT FINISHED |
| S_K3_M60 | 0.02% | -0.1 | -1 | +0.4 | +44 | 0.70 | +0.6 | 0.67 | +0.0 | +0 | n/a | +0.0 | -0.3 | +0.0 | FAIL |
| S_K3_M120 | 0.03% | -0.1 | -1 | -0.4 | +1 | 0.03 | -0.6 | 0.07 | +0.0 | +0 | n/a | +0.0 | -0.3 | +0.0 | FAIL |
| P1_K3 | 0.10% | -1.5 | -21 | -3.3 | +0 | 0.00 | -4.3 | 0.03 | -0.6 | -59 | 0.13 | +0.0 | -1.9 | -0.6 | FAIL |
| P2_K3 | 6.15% | +1.8 | +347 | -12.3 | +755 | 0.50 | -15.8 | 0.40 | -19.4 | -152 | 0.03 | +1.3 | -5.3 | +4.0 | FAIL |
| H_K4 | 0.01% | +0.0 | +0 | +0.0 | +0 | 0.38 | +0.0 | 0.42 | +0.0 | +0 | n/a | +0.0 | +0.0 | +0.0 | FAIL |
| S_K4_M30 | 0.00% | +0.0 | +0 | +0.0 | +0 | n/a | +0.0 | n/a | +0.0 | +0 | n/a | +0.0 | +0.0 | +0.0 | NOT FINISHED |
| S_K4_M60 | 0.01% | +0.0 | +0 | -0.8 | -43 | 0.00 | -1.2 | 0.00 | +0.0 | +0 | n/a | +0.0 | +0.0 | +0.0 | FAIL |
| S_K4_M120 | 0.01% | +0.0 | +0 | -0.8 | -43 | 0.00 | -1.2 | 0.00 | +0.0 | +0 | n/a | +0.0 | +0.0 | +0.0 | FAIL |
| P1_K4 | 0.02% | +0.0 | +0 | +0.1 | +96 | 0.90 | +0.0 | n/a | +0.0 | +0 | n/a | +0.0 | +0.0 | +0.0 | NOT FINISHED |
| P2_K4 | 3.10% | +0.4 | +151 | -6.8 | +38 | 0.40 | -9.0 | 0.23 | -21.1 | -950 | 0.00 | +0.5 | -4.6 | +1.8 | FAIL |
| LH_K2 | 4.83% | +0.0 | -62 | -1.1 | -291 | 0.33 | -2.4 | 0.33 | +2.1 | +299 | 0.47 | +0.1 | +0.1 | -0.0 | FAIL |
| LS_K2_M30 | 2.41% | +5.2 | -9 | +4.3 | +90 | 0.73 | +7.3 | 0.80 | +4.2 | +635 | 0.63 | +4.3 | +4.7 | +2.1 | LEAD |
| LS_K2_M60 | 4.39% | +6.6 | +140 | -7.5 | -1965 | 0.27 | -4.6 | 0.37 | +14.1 | +859 | 0.97 | +8.2 | +6.6 | +2.2 | FAIL |
| LS_K2_M120 | 5.52% | +7.5 | +104 | -5.4 | -2149 | 0.30 | -4.8 | 0.37 | +19.4 | +1254 | 0.97 | +10.8 | +7.6 | +2.5 | FAIL |
| LH_K3 | 1.71% | -0.6 | -4 | -0.3 | -264 | 0.40 | +0.3 | 0.57 | +0.5 | +62 | 0.53 | +2.2 | -0.9 | -0.8 | FAIL |
| LS_K3_M30 | 0.93% | +1.9 | +5 | -0.4 | -559 | 0.53 | +1.3 | 0.70 | -0.5 | +308 | 0.33 | +0.0 | +4.2 | -1.0 | FAIL |
| LS_K3_M60 | 1.65% | +1.5 | +113 | -9.7 | -1640 | 0.10 | -3.9 | 0.27 | -0.3 | +60 | 0.40 | +0.0 | +3.7 | -2.4 | FAIL |
| LS_K3_M120 | 2.11% | +2.5 | +200 | -19.7 | -2220 | 0.03 | -18.0 | 0.13 | -0.9 | +103 | 0.33 | +4.3 | +3.8 | -1.6 | FAIL |
| LH_K4 | 0.51% | +0.1 | +7 | -1.2 | +13 | 0.10 | -1.8 | 0.17 | +0.0 | +0 | 0.42 | +2.2 | +0.0 | +0.0 | FAIL |
| LS_K4_M30 | 0.30% | +0.6 | -13 | +1.1 | +256 | 0.67 | +1.2 | 0.83 | +0.1 | -3 | 0.50 | +0.0 | +0.6 | +0.1 | FAIL |
| LS_K4_M60 | 0.51% | +0.8 | +20 | -3.9 | -219 | 0.10 | -0.6 | 0.30 | +1.6 | +16 | 0.73 | +0.0 | +0.6 | +0.1 | FAIL |
| LS_K4_M120 | 0.64% | +1.0 | +41 | -7.8 | -350 | 0.07 | -5.0 | 0.10 | +2.1 | +111 | 0.87 | +4.3 | +0.8 | +0.1 | FAIL |

JL3 reference ulcer (RMS daily drawdown, base $): TRAIN -25599, L6M -9176, L3M -10841, HOLD -27872, GAP -17546, PREUW -31421, X' -22483, ALL43 -24344; mean $/wk TRAIN 5291, L6M 20109, HOLD 9996.

## 2b. Late entry / extension as SIZE (item b screen; lots x0.5 on the top third of each feature, thresholds frozen on TRAIN <=2025-10)

Feature thresholds (top third of TRAIN trades): open_atr ge 3.3; o18_atr ge 4.4; vwap_sig ge 1.72; used ge 0.96; mins_ext le 5; chase ge 2. imp% = ulcer reduction; p_ulc vs 30 persistent-draw random halvings with the same share per session; DD path = 2025-11-17..12-10.

| feature bucket | share | mean $/trade bucket vs rest | DD path bucket $ (n) | TRAIN imp% / dMean | L6M imp% / dMean / p_ulc | L3M imp% / p_ulc | HOLD imp% / dMean / p_ulc | tier |
|--|--|--|--|--|--|--|--|--|
| SZ_open_atr | 31.2% | 113 vs 60 | -39,132 (111 of 396) | +9.7 / -825 | +11.2 / -3271 / 0.80 | +11.6 / 0.70 | +7.6 / -678 / 0.30 | FAIL |
| SZ_o18_atr | 31.9% | 117 vs 58 | -26,549 (89 of 396) | +7.6 / -676 | +11.9 / -3091 / 0.83 | +16.7 / 1.00 | +6.5 / +2 / 0.33 | FAIL |
| SZ_vwap_sig | 28.0% | 114 vs 62 | -52,015 (109 of 396) | -1.6 / -814 | +11.4 / -2111 / 0.90 | +19.9 / 1.00 | +18.3 / -569 / 0.97 | FAIL |
| SZ_used | 32.4% | 84 vs 73 | 1,532 (102 of 396) | +15.5 / -642 | -0.4 / -1432 / 0.23 | -3.9 / 0.23 | +4.2 / -1523 / 0.17 | FAIL |
| SZ_mins_ext | 32.4% | 76 vs 77 | -37,480 (118 of 396) | +6.6 / -412 | +5.6 / -1690 / 0.47 | +10.0 / 0.73 | +7.8 / -122 / 0.47 | FAIL |
| SZ_chase | 51.8% | 94 vs 59 | -41,383 (231 of 396) | +9.9 / -887 | +6.7 / -4672 / 0.17 | +2.7 / 0.17 | +16.8 / -1670 / 0.30 | FAIL |

Target pull-in (x0.5, x0.67), stop x0.67 and breakeven cannot be judged by path arithmetic (they change the exit): exact cells EXT_<feature>_<TG50|TG67|ST67|SZ50> below for the two TRAIN-best features (used = share of the typical session range already used; open_atr). Breakeven-after-+20 is NOT built (needs a stop-move mechanism in the engine hook; stated as not done). The same cells are the item-D (W-MD / W-S3 environment) extension test: run once here.

## 3. Walk-forward pick (choose on TRAIN <=2025-10, freeze; HOLD / L6M untouched)

Best TRAIN ulcer improvement per family: H_K2 (+0.5%), S_K2_M120 (+0.2%), P1 none positive (P1_K2 0.0%), P2_K3 (+1.8%, +347/wk), LH_K2 (0.0%), LS_K2_M120 (+7.5%, +104/wk; overall best). LS_K2_M30 (+5.2%) is the only screen LEAD and is carried as a flagged post-hoc cell. Frozen exact picks: LS_K2_M120, P2_K3, LS_K2_M30, LH_K2, S_K2_M120, H_K2 (order of the queue).

Walk-forward out-of-sample read of the picks (screen): LS_K2_M120 HOLD +19.4% / L6M -5.4% / L3M -4.8%; P2_K3 HOLD -19.4% / L6M -12.3% / L3M -15.8%; LS_K2_M30 HOLD +4.2% / L6M +4.3% / L3M +7.3%; LH_K2 HOLD +2.1% / L6M -1.1% / L3M -2.4%; S_K2_M120 HOLD -1.7% / L6M -1.2% / L3M -1.4%; H_K2 HOLD -0.6% / L6M -0.4% / L3M -0.7%.

## 4. Exact engine (hook me_hooks.py, outermost; set TL3_ME_JL3_<code>, controls TL3_ME_C_<code>_S<k>)

Hook method: only try_entry, exec_exit and trend_size are overridden (no base layer method: lock/exit/stack layers untouched, so no switched-off layer can be re-enabled); it is the LAST entry of the base hooklist. Day vote = th_dial10/d10_core.day_dir(sec,key,t0,"vote"), the engine-side function W-D10 already uses: reads only NQ 1-min bars (min1_NQ.npz), closed bars ts <= sec-60 at the signal second (clock second of try_entry); sessions asia/london/nyam/nypm (08:30-09:30 and 15:00-18:00 have no key: vote 0, rule off). Counters: causal, stack-wide, updated only when a trade fully closes (s.trades grows) over all books; a closed trade is classified with the vote at ITS OWN signal second (tr.sig_ns) and net_fee; instance = (Globex day, session of the signal); a winner resets the streak; a new instance starts at 0. Half size = lots x0.5 round-half-up min 1 inside trend_size; press x1.5. Identity cell TL3_ME_JL3_ID (state machine runs, never acts).

IDENTITY (TL3_ME_JL3_ID vs TL3_EV_JL3, trade for trade on entry_ns, exit_ns, lots, book, net_fee): IDX 202504: IDENTICAL (n 637/637, net 41239.76/41239.76); IDX 202610: IDENTICAL (n 691/691, net 37159.82/37159.82). No exact result below is used unless both 202610 and 202504 are IDENTICAL.

| cell | months landed | tier | L6M imp% / dMean base / $4.84 / x1.75 | p_ulc (valid ctrls) | L3M imp% | HOLD imp% (p_ulc, valid) | boot p_ulc L6M | exposure share L6M |
|--|--|--|--|--|--|--|--|--|
| H_K2 | 12 | NOT FINISHED | -5.2 / -196 / -195 / -369 | n/a | -7.5 | -0.7 n/a | 0.16 | 0.001 |
| LH_K2 | 12 | NOT FINISHED | -6.2 / +156 / +162 / +370 | 0.00 (5) | -9.2 | +2.6 0.50 (8) | 0.15 | 0.007 |
| LH_K2_B | 12 | NOT FINISHED | -5.5 / -326 / -323 / -575 | n/a | -7.7 | -1.9 n/a | 0.17 | 0.003 |
| LH_K3 | 12 | FAIL | +0.4 / -36 / -33 / -26 | 0.69 (26) | +1.6 | +0.5 0.59 (29) | 0.21 | 0.003 |
| LS_K2_M120 | 12 | NOT FINISHED | -28.4 / -2644 / -2601 / -5122 | 0.12 (8) | -41.3 | +4.5 0.45 (31) | 0.02 | 0.049 |
| LS_K2_M120_B | 12 | NOT FINISHED | -6.9 / +179 / +196 / +233 | n/a | -11.9 | +5.4 n/a | 0.06 | 0.020 |
| LS_K2_M120_R | 12 | NOT FINISHED | -21.7 / -2049 / -2018 / -3957 | n/a | -29.5 | -1.5 n/a | 0.02 | 0.036 |
| LS_K2_M30 | 43 | NOT FINISHED | -1.0 / -563 / -551 / -1035 | 0.52 (21) | -4.4 | +2.1 0.62 (21) | 0.26 | 0.014 |
| LS_K2_M30_B | 12 | NOT FINISHED | -0.7 / +418 / +422 / +836 | n/a | -5.9 | -0.4 n/a | 0.57 | 0.005 |
| LS_K2_M30_R | 12 | NOT FINISHED | -3.8 / -555 / -546 / -1047 | n/a | -1.4 | +2.9 n/a | 0.22 | 0.011 |
| LS_K2_M60 | 12 | NOT FINISHED | -15.9 / -1971 / -1941 / -3725 | n/a | -16.0 | +10.3 n/a | 0.00 | 0.036 |
| LS_K2_M60_B | 12 | NOT FINISHED | -10.0 / -110 / -100 / -308 | n/a | -15.7 | +2.5 n/a | 0.14 | 0.012 |
| LS_K2_M60_R | 12 | NOT FINISHED | -7.2 / -879 / -857 / -1600 | n/a | -9.3 | -1.0 n/a | 0.00 | 0.026 |
| LS_K3_M120 | 12 | NOT FINISHED | -10.4 / -3069 / -3049 / -6011 | n/a | -13.6 | -1.4 n/a | 0.01 | 0.022 |
| LS_K3_M30 | 12 | NOT FINISHED | -1.9 / -1119 / -1111 / -2206 | n/a | -2.7 | -0.2 n/a | 0.35 | 0.009 |
| LS_K3_M60 | 12 | NOT FINISHED | -14.8 / -2672 / -2653 / -5195 | n/a | -11.8 | +0.5 n/a | 0.00 | 0.023 |
| S_K2_M120 | 12 | NOT FINISHED | -9.6 / -441 / -441 / -870 | n/a | -9.2 | -6.5 n/a | 0.13 | 0.000 |
| CUT_half | 12 | NOT FINISHED | -1.1 / -699 / -692 / -1200 | n/a | -3.7 | -5.5 n/a | 0.36 | 0.008 |
| CUT_tight | 12 | NOT FINISHED | -6.7 / +1104 / +1101 / +2377 | n/a | -3.2 | -18.5 n/a | 0.22 | -0.005 |
| EXT_openatr_ST67 | 12 | NOT FINISHED | -8.4 / -1935 / -1904 / -3648 | n/a | -14.2 | +15.5 n/a | 0.32 | 0.037 |
| EXT_openatr_SZ50 | 12 | NOT FINISHED | +9.2 / -3304 / -3232 / -5464 | n/a | +4.9 | +6.9 n/a | 0.88 | 0.086 |
| EXT_openatr_TG50 | 12 | NOT FINISHED | +9.7 / -3625 / -3702 / -6549 | n/a | +3.1 | +20.7 n/a | 0.68 | -0.092 |
| EXT_openatr_TG67 | 12 | NOT FINISHED | +5.4 / -2076 / -2109 / -3867 | n/a | +7.9 | +22.4 n/a | 0.91 | -0.040 |
| EXT_used_ST67 | 12 | NOT FINISHED | -3.2 / -601 / -583 / -1050 | n/a | -3.5 | +2.3 n/a | 0.46 | 0.021 |
| EXT_used_SZ50 | 12 | NOT FINISHED | +5.2 / -2054 / -1996 / -3134 | n/a | +7.5 | +10.8 n/a | 0.71 | 0.070 |
| EXT_used_TG50 | 12 | NOT FINISHED | +1.4 / -426 / -509 / -323 | n/a | -6.8 | -8.3 n/a | 0.63 | -0.098 |
| EXT_used_TG67 | 12 | NOT FINISHED | -4.8 / -676 / -709 / -1070 | n/a | -8.0 | +6.7 n/a | 0.47 | -0.038 |

Freed-book effects (base $, window L6M, trades only in the cell / only in JL3 / common pnl change by book): 
- H_K2: K7 lost 3 (-3331) gained 0 (+0) common +0; M7 lost 1 (+700) gained 0 (+0) common +0; P7 lost 0 (-0) gained 0 (+0) common -2523
- LH_K2: K7 lost 4 (-2884) gained 16 (+8430) common -2508; M7 lost 3 (+2686) gained 2 (+492) common -2132; U7 lost 0 (-0) gained 0 (+0) common +1414; P7 lost 2 (+2269) gained 2 (+1473) common +415; H7 lost 0 (-0) gained 0 (+0) common -5556
- LH_K2_B: K7 lost 3 (-3331) gained 0 (+0) common +0; M7 lost 2 (+1247) gained 1 (-707) common +1392; P7 lost 1 (+1334) gained 0 (+0) common -5931; H7 lost 0 (-0) gained 0 (+0) common -2576
- LH_K3: K7 lost 0 (-0) gained 3 (+1465) common -1724; M7 lost 3 (+2766) gained 1 (-640) common -1204; U7 lost 0 (-0) gained 0 (+0) common -1199; P7 lost 2 (+2269) gained 1 (+1199) common -1689; H7 lost 0 (-0) gained 0 (+0) common -2184
- LS_K2_M120: K7 lost 167 (-18819) gained 115 (-6741) common +1208; M7 lost 123 (-10609) gained 51 (+7094) common +0; U7 lost 11 (-5459) gained 7 (-1236) common -405; P7 lost 137 (-28634) gained 62 (+10722) common +3726; H7 lost 21 (-15768) gained 2 (-3542) common +0; A7 lost 31 (-280) gained 9 (-412) common +305; O7 lost 1 (-1799) gained 2 (+1162) common +0
- LS_K2_M120_B: K7 lost 66 (-4927) gained 42 (+4829) common -873; M7 lost 66 (+2420) gained 9 (+6298) common +0; U7 lost 0 (-0) gained 2 (+1001) common +0; P7 lost 25 (-14363) gained 8 (+16537) common +299; H7 lost 2 (-5233) gained 0 (+0) common +618; A7 lost 10 (+2918) gained 2 (-2277) common +0; O7 lost 1 (-1799) gained 1 (-741) common +0
- LS_K2_M120_R: K7 lost 130 (-8628) gained 90 (-11388) common -2644; M7 lost 94 (-5356) gained 42 (+3113) common +0; U7 lost 6 (+2709) gained 5 (-4833) common +0; P7 lost 120 (-14328) gained 45 (-3122) common +999; H7 lost 11 (-10124) gained 2 (-3542) common +0; A7 lost 14 (+54) gained 7 (+1773) common +305; O7 lost 0 (-0) gained 2 (+1162) common +0
- LS_K2_M30: K7 lost 82 (-10902) gained 55 (-1269) common -2613; M7 lost 63 (+5956) gained 21 (+3705) common +256; U7 lost 4 (+2958) gained 3 (-1811) common +0; P7 lost 51 (-907) gained 36 (-10718) common -5; H7 lost 3 (-1295) gained 1 (-1139) common +0; A7 lost 7 (-449) gained 3 (+1640) common +0; O7 lost 0 (-0) gained 1 (+1799) common +0
- LS_K2_M30_B: K7 lost 33 (+2866) gained 21 (+6148) common +451; M7 lost 32 (+8765) gained 10 (-302) common +256; U7 lost 1 (+2512) gained 3 (-6149) common +0; P7 lost 3 (-1478) gained 3 (-3191) common +0; A7 lost 3 (+1104) gained 0 (+0) common +0
- LS_K2_M30_R: K7 lost 67 (-3115) gained 52 (-1640) common -2644; M7 lost 58 (+4284) gained 24 (+2393) common +0; U7 lost 5 (+1760) gained 3 (-1326) common +0; P7 lost 59 (-3784) gained 44 (-9793) common -5; H7 lost 4 (-3063) gained 1 (-1139) common +0; A7 lost 7 (-229) gained 4 (+2662) common +0; O7 lost 0 (-0) gained 2 (+1058) common +0
- LS_K2_M60: K7 lost 151 (-12023) gained 91 (-4757) common +1252; M7 lost 106 (-9669) gained 45 (+2235) common +0; U7 lost 9 (-3245) gained 5 (-1136) common -70; P7 lost 116 (-32872) gained 70 (+23201) common +5076; H7 lost 17 (-12524) gained 3 (-2603) common +0; A7 lost 21 (-4653) gained 10 (+2840) common +305; O7 lost 2 (-3598) gained 3 (+420) common +0
- LS_K2_M60_B: K7 lost 63 (-7810) gained 34 (+3997) common -458; M7 lost 48 (+5976) gained 10 (-345) common +0; U7 lost 0 (-0) gained 3 (-6149) common +0; P7 lost 10 (-6011) gained 5 (+9357) common +1004; H7 lost 0 (-0) gained 0 (+0) common +118; A7 lost 10 (+1501) gained 2 (-2272) common +0; O7 lost 1 (-1799) gained 0 (+0) common +0
- LS_K2_M60_R: K7 lost 110 (+2383) gained 75 (-8961) common -2613; M7 lost 90 (-2814) gained 39 (+6705) common +0; U7 lost 5 (+3908) gained 4 (-2335) common +0; P7 lost 107 (-19985) gained 60 (+8711) common +1649; H7 lost 9 (-8087) gained 2 (-3542) common +0; A7 lost 8 (+496) gained 5 (+1716) common +305; O7 lost 1 (-1799) gained 2 (+1162) common +0
- LS_K3_M120: K7 lost 92 (-28181) gained 64 (-1690) common +1415; M7 lost 61 (-7747) gained 29 (+1189) common +0; U7 lost 5 (-3488) gained 3 (-3471) common -405; P7 lost 63 (-19573) gained 27 (-2872) common -705; H7 lost 13 (-9405) gained 2 (-3542) common +0; A7 lost 15 (+2016) gained 6 (-1327) common +305; O7 lost 1 (-1799) gained 2 (-1387) common +0
- LS_K3_M30: K7 lost 43 (-13487) gained 17 (-2461) common -2175; M7 lost 32 (+1875) gained 8 (+1859) common +256; U7 lost 1 (-2398) gained 0 (+0) common -70; P7 lost 24 (-9369) gained 20 (-2214) common -5; H7 lost 1 (-909) gained 0 (+0) common +0; A7 lost 3 (+2571) gained 2 (-2141) common +0; O7 lost 0 (-0) gained 1 (-741) common +0
- LS_K3_M60: K7 lost 72 (-15055) gained 44 (-4226) common +1384; M7 lost 55 (-7354) gained 15 (-2137) common +0; U7 lost 3 (-3557) gained 1 (-1009) common -405; P7 lost 55 (-16813) gained 21 (-10302) common -5; H7 lost 10 (-8203) gained 2 (-3542) common +0; A7 lost 10 (+820) gained 4 (+2400) common +305; O7 lost 1 (-1799) gained 1 (-741) common +0
- S_K2_M120: K7 lost 13 (-4080) gained 11 (-2540) common +0; M7 lost 3 (-958) gained 2 (+1543) common +0; P7 lost 4 (-3444) gained 4 (-920) common +0; H7 lost 1 (-1199) gained 0 (+0) common +0
- CUT_half: K7 lost 37 (+869) gained 11 (+801) common +955; M7 lost 30 (-2548) gained 9 (-2993) common +2430; U7 lost 3 (+3336) gained 2 (-4650) common +13973; P7 lost 12 (-3242) gained 9 (-2905) common -14797; H7 lost 1 (-1199) gained 0 (+0) common -8800; A7 lost 0 (-0) gained 0 (+0) common +45; O7 lost 4 (+356) gained 0 (+0) common +0
- CUT_tight: K7 lost 158 (-15541) gained 178 (+20834) common +21766; M7 lost 57 (-2371) gained 44 (-2835) common -2318; U7 lost 3 (-1759) gained 6 (-207) common +12446; P7 lost 38 (-1319) gained 26 (-1856) common -8556; H7 lost 3 (-901) gained 5 (+269) common +3423; A7 lost 10 (-3453) gained 34 (+6993) common +4775; O7 lost 4 (-2229) gained 3 (+3025) common -1154
- EXT_openatr_ST67: K7 lost 242 (-4548) gained 99 (+27419) common -4287; M7 lost 64 (+4332) gained 19 (-5144) common -12518; U7 lost 4 (-1657) gained 2 (-4280) common +233; P7 lost 26 (-9556) gained 8 (+1924) common -22974; H7 lost 1 (-1199) gained 2 (-2787) common -2019; A7 lost 35 (-7274) gained 27 (+9143) common -6379; O7 lost 4 (-2229) gained 1 (-801) common -6275
- EXT_openatr_SZ50: K7 lost 53 (+4927) gained 83 (+23438) common -7255; M7 lost 23 (+1356) gained 27 (-1042) common +2940; U7 lost 2 (+295) gained 3 (-6216) common -11980; P7 lost 22 (-4111) gained 20 (-3663) common -77414; H7 lost 3 (-1221) gained 2 (+174) common -6795; O7 lost 2 (+1087) gained 2 (-1378) common +0
- EXT_openatr_TG50: K7 lost 170 (-21165) gained 368 (+35144) common +3147; M7 lost 62 (-2152) gained 98 (-9299) common -6892; U7 lost 3 (-11818) gained 4 (-3193) common -1770; P7 lost 47 (-20657) gained 129 (+2435) common -44608; H7 lost 3 (-3311) gained 7 (-3194) common -9745; A7 lost 15 (-2568) gained 109 (+10001) common +862; O7 lost 5 (-1836) gained 4 (-2759) common -1894
- EXT_openatr_TG67: K7 lost 152 (-6848) gained 252 (+16441) common -8544; M7 lost 60 (-11120) gained 60 (-7440) common +1104; U7 lost 2 (-1159) gained 0 (+0) common +2879; P7 lost 42 (-26989) gained 70 (+23970) common -25650; H7 lost 3 (-1221) gained 1 (+624) common -8297; A7 lost 29 (-8661) gained 75 (+4477) common +2505; O7 lost 4 (-37) gained 3 (+360) common -949
- EXT_used_ST67: K7 lost 192 (-6288) gained 78 (+24313) common +4385; M7 lost 23 (-2730) gained 11 (-1255) common -13230; U7 lost 1 (-2393) gained 2 (-7672) common -320; P7 lost 7 (-2490) gained 7 (-5036) common -10233; H7 lost 0 (-0) gained 1 (-1577) common +6257; A7 lost 19 (-5522) gained 17 (+10040) common -1305; O7 lost 1 (-1799) gained 2 (+1058) common +0
- EXT_used_SZ50: K7 lost 54 (-428) gained 85 (+11528) common -2767; M7 lost 24 (-2979) gained 15 (-5884) common +4540; U7 lost 2 (+4859) gained 2 (-5035) common -13928; P7 lost 23 (+1221) gained 12 (-808) common -45578; H7 lost 4 (-867) gained 0 (+0) common +4749; O7 lost 3 (-1881) gained 1 (-741) common +0
- EXT_used_TG50: K7 lost 75 (+570) gained 348 (+11097) common +15942; M7 lost 25 (-175) gained 76 (-6881) common -2117; U7 lost 2 (-2288) gained 5 (-8759) common +187; P7 lost 27 (-6515) gained 104 (+5875) common -35703; H7 lost 1 (-1199) gained 3 (+653) common +7780; A7 lost 9 (+207) gained 76 (+9714) common -2716; O7 lost 2 (+908) gained 4 (+2219) common +0
- EXT_used_TG67: K7 lost 92 (-9556) gained 231 (+22265) common +2436; M7 lost 27 (-4389) gained 37 (+1692) common -4358; U7 lost 2 (+2377) gained 1 (-2812) common -2483; P7 lost 23 (+595) gained 45 (+2128) common -32735; H7 lost 1 (-1199) gained 0 (+0) common +6387; A7 lost 17 (-2615) gained 45 (+9588) common -4770; O7 lost 2 (-1493) gained 2 (+1162) common +0

Controls: persistent draws (crc32 hash of seed, book, side, 300 s bucket), per-session p from the screen shares in L6M+HOLD; valid = lots-exposure share within max(min(0.05,0.25 share),0.002) of the real cell; <30 valid in L6M/L3M = NOT FINISHED, never passing; an invalid-draw refill (recalibrated p, seeds 101+) is added by me_loop when needed. Selection nulls (shifted labels) are not meaningful for a streak counter (no labels): the matched random-halving/skip controls are the null.

## 5. Files
code/th_major_e/{me_votes,me_sim,me_screen,me_hooks,me_mk,me_build,me_score,me_page,me_loop}.py; data /mnt/l2/l2vast/_major_e/ (votes_JL3.parquet, screen.pkl, me_res.pkl, pending.txt); sets TL3_ME_* under _th_sz/ijk/exact/sets.
