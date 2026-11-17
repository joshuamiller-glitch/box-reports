# DS3_MAJOR_E_AGAINST - against-the-day streak rules on JL3 (W-ME, MAJOR PART E)

Page refreshed 2026-11-17 14:54Z (unattended loop me_loop). Data end 2026-10-31 (JL3 months 202304..202610). FIRST PASS.

PLAIN SUMMARY

1. Tried (re-aimed 11-17 14:26Z at what a manual trader sees): (a) same-side loser streak (vote-free) as skip/half, with a resume-at-new-session-extreme and a per-book version; (b) extended-entry bucket (how far price already ran: ATR from session open / 18:00 open, VWAP sigma, share of typical session range used, chase count, minutes since extreme) as SIZE and as TARGET/STOP, with a drawdown-period table; (c) after a book cut, halve or tighten the other same-side positions; the ordered vote rules (H/S/P1/P2) stay only as reference rows.
2. Key finding: the 2025-11-17..12-10 losers were WITH the causal 3-of-4 vote (333 trades -78.0k; against 26 trades +3.4k): the books enter after the move and the reversal comes later, so only hindsight labels show "against the day".
3. Screen: the ordered vote rules bind on 0.0-0.6% of trades and do nothing (P2 press hurts HOLD by 15-21%); extended-entry halving improves ulcer 6-12% in L6M but costs 1.5-4.7k/wk and is NOT better than random halving of the same share (p_ulc 0.2-0.9, no tier); the extended bucket earns MORE per trade (about $110 vs $60) but concentrates the drawdown (-39k of the path in the open_atr bucket).
4. What survives the screen: same-side loser K=2 pause 30 min (LS_K2_M30: ulcer +4% to +7% in TRAIN/L6M/L3M/HOLD at flat mean, screen tier LEAD, post-hoc); the longer pauses help HOLD (+14%/+19%) but hurt L6M. Nothing is CONFIRMED; DS7 needs nothing until the exact tiers below land.
5. Next: exact cells on the engine queue (identity IDX first; 1540 queue lines pending, 26 run-months landed); stage 2 adds 34 matched controls for the best cells automatically; this page refreshes every 30 min.

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

STATUS: no exact cell has landed yet (queue position after A and C; 1540 lines pending).

Controls: persistent draws (crc32 hash of seed, book, side, 300 s bucket), per-session p from the screen shares in L6M+HOLD; valid = lots-exposure share within max(min(0.05,0.25 share),0.002) of the real cell; <30 valid in L6M/L3M = NOT FINISHED, never passing; an invalid-draw refill (recalibrated p, seeds 101+) is added by me_loop when needed. Selection nulls (shifted labels) are not meaningful for a streak counter (no labels): the matched random-halving/skip controls are the null.

## 5. Files
code/th_major_e/{me_votes,me_sim,me_screen,me_hooks,me_mk,me_build,me_score,me_page,me_loop}.py; data /mnt/l2/l2vast/_major_e/ (votes_JL3.parquet, screen.pkl, me_res.pkl, pending.txt); sets TL3_ME_* under _th_sz/ijk/exact/sets.
