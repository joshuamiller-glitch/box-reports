# DS3_SUNDAY_STACK_2 - Sunday stack, causal governors, M6/A6 books, bases, user sessions, K6 add (agent SS-2, follow-up to DS3_SUNDAY_STACK.md)

Research only. No live/execution/chart change. UNTOUCHED never read (every frame capped at label day 20260206); own masks L3M 20251106.. (view), L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230401..20240131. Prereg `autopilot/SUNDAYSTACK2_prereg.md` sha256 b0a1d835715a27170b83a1cc9f5a6ada159078b2aaadf9c0ecb0c25b28d3d4e4 (DECISIONS.md, before the SS-2 scoring run; the composite is unchanged and nothing is tuned: every variant below is reported, no selection among them). Same lock engine as SS (stack2/s2_lib -> sp_lib + sl_lib), extended in place; code `l2vast/ds3/code/sundaystack2/`, outputs `l2vast/ds3/out/sundaystack2/`. $/wk = lock-engine stack weekly mean; delta = D6 v2.3b minus "the stack as it is" (market entries, no rules, join stop 2.45) on the same lots and basis; MDE = 2.8 x SE of the paired weekly delta. Tie-outs (exact to the dollar): at the old session assumption and static governors this engine returns SS's live4 line (as-is 18.1k, D6 40.4k L6M) and SS's research line (132.8k); with the multiplier fixed at 1 the causal engine equals the base engine (difference 0.0); the six SS books of the 70/30 outcomes equal stackpart/o_S73_N.npy to 1e-9.

## 0. Page 1: the corrected headline, one plain sentence, and the one change

**as coded with causal governors, Sunday's D6 vs the stack as it is (LIVE lots K6 2, P6 7, U6 4, H6 4/2, M6 2, A6 1 in the user's sessions): +18.5k $/wk L6M (MDE 17.4k), +16.2k HOLD (MDE 16.8k), +4.7k PRE (MDE 13.4k) [+12.5k X' (MDE 14.7k)].**
**as coded with causal governors, Sunday's D6 vs the stack as it is (the same live lots + ST, WT at research/2.35): +31.1k $/wk L6M (MDE 27.2k), +29.7k HOLD (MDE 25.4k), +14.9k PRE (MDE 18.1k) [+9.9k X' (MDE 19.2k)].**
**as coded with causal governors, Sunday's D6 vs the stack as it is (RESEARCH lots): +79.5k $/wk L6M (MDE 50.6k), +74.9k HOLD (MDE 49.4k), +24.7k PRE (MDE 33.1k) [+12.8k X' (MDE 35.1k)].**

Corrected headline table (N basis, Native stops 1.28 as coded, delta vs the stack as it is, $k/wk, MDE in brackets; "static" = SS's reading, non-causal; (a) running max is the headline because it is the reading D6 can compute):

| lots | governor reading | L3M | L6M | HOLD | PRE | X' | D6 can implement? |
|---|---|---|---|---|---|---|---|
| LIVE (K6 P6 U6 H6 M6 A6) | (a) running max | +19.4 (24.1) | +18.5 (17.4) | +16.2 (16.8) | +4.7 (13.4) | +12.5 (14.7) | YES: headline |
| LIVE (K6 P6 U6 H6 M6 A6) | (b) opener of the day | +6.3 (26.3) | +4.6 (19.0) | +5.4 (17.8) | +2.5 (13.3) | +13.0 (13.8) | yes (causal) but bad |
| LIVE (K6 P6 U6 H6 M6 A6) | (b') last-entered trade | +6.9 (31.8) | +11.7 (21.5) | +9.6 (19.6) | +4.3 (15.0) | +10.3 (14.7) | yes (causal) but weak |
| LIVE (K6 P6 U6 H6 M6 A6) | (c) base-lot | +6.9 (24.2) | +9.8 (16.2) | +8.7 (15.1) | +1.7 (12.7) | +13.3 (14.1) | yes (no multiplier on locks) |
| LIVE (K6 P6 U6 H6 M6 A6) | static (SS, non-causal) | +21.4 (22.5) | +19.4 (16.9) | +16.9 (16.4) | +4.0 (14.3) | +12.5 (14.7) | NO: needs the day's later signals |
| LIVE + ST WT at research/2.35 | (a) running max | +38.6 (40.8) | +31.1 (27.2) | +29.7 (25.4) | +14.9 (18.1) | +9.9 (19.2) | YES: headline |
| LIVE + ST WT at research/2.35 | (b) opener of the day | +16.1 (45.4) | +11.7 (27.1) | +13.9 (26.0) | +6.2 (16.9) | +9.4 (18.2) | yes (causal) but bad |
| LIVE + ST WT at research/2.35 | (b') last-entered trade | +22.9 (51.2) | +23.5 (32.7) | +20.8 (29.6) | +11.1 (20.0) | +8.5 (19.2) | yes (causal) but weak |
| LIVE + ST WT at research/2.35 | (c) base-lot | +29.5 (35.6) | +23.2 (25.5) | +22.3 (23.6) | +4.7 (15.9) | +14.3 (19.9) | yes (no multiplier on locks) |
| LIVE + ST WT at research/2.35 | static (SS, non-causal) | +40.1 (39.6) | +32.3 (26.9) | +29.9 (25.3) | +14.5 (19.0) | +10.2 (19.2) | NO: needs the day's later signals |
| RESEARCH | (a) running max | +95.2 (75.9) | +79.5 (50.6) | +74.9 (49.4) | +24.7 (33.1) | +12.8 (35.1) | YES: headline |
| RESEARCH | (b) opener of the day | +60.7 (84.8) | +40.3 (51.0) | +41.9 (50.9) | +5.4 (32.9) | +15.6 (32.5) | yes (causal) but bad |
| RESEARCH | (b') last-entered trade | +79.5 (96.0) | +69.1 (60.0) | +61.4 (57.2) | +8.2 (34.8) | +14.3 (34.5) | yes (causal) but weak |
| RESEARCH | (c) base-lot | +71.5 (63.1) | +45.7 (50.6) | +44.9 (48.7) | +5.6 (29.3) | +21.9 (36.3) | yes (no multiplier on locks) |
| RESEARCH | static (SS, non-causal) | +100.2 (77.7) | +82.8 (51.7) | +76.1 (50.7) | +27.0 (33.3) | +13.0 (34.6) | NO: needs the day's later signals |

**Reading of the table.** (1) The non-causal inflation is small: the running-max reading keeps almost all of SS's static number (live: +18.5k vs +19.4k L6M, +16.2k vs +16.9k HOLD, +4.7k vs +4.0k PRE; research: +79.5k vs +82.8k L6M). Cost of making it causal: about 1k at live lots, 3k at research lots. (2) The other two causal readings are much worse and are NOT acceptable implementations: fixing the locks at the multiplier of the trade that opened the day ((b)) gives only +4.6k L6M at live lots (+40.3k research), below the base-lot governors ((c), +9.8k live, +45.7k research), because on days that open with a 0.5 the locks stay at half size for later 1.5 trades; the last-entered-trade rule ((b')) gives +11.7k / +69.1k. (3) The running-max reading is what D6 can implement: it needs only the multipliers of signals as they fire (ER(20) on the 5-min bar at the signal) and a per-book, per-day maximum that is reset at the trading-day rollover; the lock thresholds are R x (running max) evaluated every second. (4) Significance is unchanged in kind: at live lots L6M clears its MDE (+18.5k vs 17.4k) and HOLD is just inside (16.2k vs 16.8k), PRE and X' are positive but inside their MDE; at research lots L6M and HOLD clear. Tier stays CANDIDATE-RECENT (post-hoc-selected pieces; SS section 8 labels stand; cumulative-trial adjusted p is 1.00).

**The one change before 18:00 ET Sunday: none to the six pieces; one specification to D6.** The lock multiplier (day and week locks x the ER multiplier) must be the RUNNING MAXIMUM of the ER multipliers of the signals the book has taken so far today, updated at each signal (reading (a)), not a value fixed from the first trade ((b): +4.6k vs +18.5k L6M at live lots) and not the multiplier of the trade currently open ((b'): +11.7k). If D6 currently has the locks on the base lot R only (c), the stack gives up 8.7k L6M at live lots (research: 33.8k). Piece-removal rule (SS rule: remove a piece only if its removal improves L6M, HOLD, PRE and X' together): at the actual live lots no piece meets it (section 5); at "live + ST, WT" the Asia-stopped cut does (contribution -1.9k / -2.5k / -0.8k / -1.5k, each inside its MDE) but ST/WT are not live, so it is a watch item, not a change. K6 add: keep as coded (section 4: the SS vs C7 gap is context, both inside MDE).

Other corrections in this report (details below): M6=MV and A6=PB are now in the lock-engine stack (they add +0.7k to the L6M delta at the live lots: from +17.8k to +18.5k); the user's sessions (PRE and CLOSE lot 0, not folded into London / NY-PM) lower the four-book delta by 3.5k L6M (as-is stack rises, D6 stack falls); basis M vs N moves the delta by 0.1k at live lots (L6M) and the LIVE-CAL stop (join 2.45) lowers it by 2.3k; integer lots (A6 at 1 lot cannot be split; ER x0.5 / x1.5 on 1-2 lots must round) are in section 3b.

## 1. Item 1: causal readings of the sized-lot governor, per window
Definitions (implemented in `ss2_lib.run_book3` / `_first_trigger_c`; the entry test of a trade uses the multiplier in force at its own signal, the give-back arm and the week floor are evaluated every second against R x the multiplier of the latest trade entered): **static** = SS: R x the largest multiplier of the day among the taken trades (day locks) / of the week's days (week floor), known only after the day ends = non-causal. **(a) running max** = R x the maximum of the multipliers of the signals taken so far today (the multiplier updates when a later signal fires; resets each day). **(b) opener** = R x the multiplier of the day's first taken trade (the one that opened the day's exposure), fixed for the day. **(b') last-entered** = R x the multiplier of the trade entered last (an episode rule). **(c) base** = planned-lot R, no multiplier. "Taken" = passes the zone skip, the PE confirmation and the book's one-position rule; a signal skipped by the day entry test still counts toward the maximum (its ER is known when it fires). Week floor: the multiplier in force on the day the second falls in (reset with each day).

#### LIVE lots (user sessions): K6 2, P6 7, U6 4, H6 4/2, M6 2, A6 1 (ST, WT, O6 0)
| config | stop | L3M mean $k/wk | L6M | HOLD | PRE | X' | delta vs as-is $k/wk (MDE): L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|---|---|
| stack as it is (market entries, no rules, join stop 2.45) | 2.45 | 13.8 | 24.0 | 23.7 | 17.7 | -3.6 | - | - | - | - | - |
| D6 v2.3b, governors static (SS, non-causal) | 1.28 | 35.2 | 43.4 | 40.6 | 21.7 | 8.9 | +21.4 (22.5) | +19.4 (16.9) | +16.9 (16.4) | +4.0 (14.3) | +12.5 (14.7) |
| D6 v2.3b, governors (a) running max | 1.28 | 33.2 | 42.6 | 39.9 | 22.4 | 9.0 | +19.4 (24.1) | +18.5 (17.4) | +16.2 (16.8) | +4.7 (13.4) | +12.5 (14.7) |
| D6 v2.3b, governors (b) opener of the day | 1.28 | 20.1 | 28.6 | 29.1 | 20.2 | 9.5 | +6.3 (26.3) | +4.6 (19.0) | +5.4 (17.8) | +2.5 (13.3) | +13.0 (13.8) |
| D6 v2.3b, governors (b') last-entered trade | 1.28 | 20.7 | 35.7 | 33.3 | 22.0 | 6.7 | +6.9 (31.8) | +11.7 (21.5) | +9.6 (19.6) | +4.3 (15.0) | +10.3 (14.7) |
| D6 v2.3b, governors (c) base-lot | 1.28 | 20.7 | 33.9 | 32.4 | 19.4 | 9.8 | +6.9 (24.2) | +9.8 (16.2) | +8.7 (15.1) | +1.7 (12.7) | +13.3 (14.1) |
| D6 v2.3b, governors static (SS, non-causal) | 2.45 | 33.1 | 41.4 | 38.6 | 19.1 | 7.2 | +19.3 (23.0) | +17.4 (17.1) | +14.9 (16.5) | +1.4 (14.4) | +10.8 (14.7) |
| D6 v2.3b, governors (a) running max | 2.45 | 30.9 | 40.2 | 37.6 | 20.0 | 7.3 | +17.1 (24.5) | +16.2 (17.8) | +13.9 (17.0) | +2.3 (13.5) | +10.8 (14.7) |
| D6 v2.3b, governors (b) opener of the day | 2.45 | 18.4 | 27.0 | 27.6 | 18.3 | 8.0 | +4.6 (26.1) | +3.0 (19.0) | +3.9 (17.9) | +0.6 (13.4) | +11.5 (13.8) |
| D6 v2.3b, governors (b') last-entered trade | 2.45 | 18.8 | 33.1 | 30.8 | 19.8 | 5.0 | +5.0 (31.6) | +9.1 (21.6) | +7.1 (19.6) | +2.1 (15.1) | +8.6 (14.8) |
| D6 v2.3b, governors (c) base-lot | 2.45 | 14.7 | 30.0 | 28.9 | 17.1 | 8.1 | +0.9 (25.8) | +6.0 (17.1) | +5.2 (15.8) | -0.6 (12.7) | +11.7 (14.1) |

#### LIVE lots + ST, WT at research/2.35 (4.26 / 2.98)
| config | stop | L3M mean $k/wk | L6M | HOLD | PRE | X' | delta vs as-is $k/wk (MDE): L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|---|---|
| stack as it is (market entries, no rules, join stop 2.45) | 2.45 | 18.6 | 34.4 | 30.0 | 24.6 | -0.5 | - | - | - | - | - |
| D6 v2.3b, governors static (SS, non-causal) | 1.28 | 58.7 | 66.7 | 59.9 | 39.1 | 9.7 | +40.1 (39.6) | +32.3 (26.9) | +29.9 (25.3) | +14.5 (19.0) | +10.2 (19.2) |
| D6 v2.3b, governors (a) running max | 1.28 | 57.2 | 65.5 | 59.7 | 39.5 | 9.5 | +38.6 (40.8) | +31.1 (27.2) | +29.7 (25.4) | +14.9 (18.1) | +9.9 (19.2) |
| D6 v2.3b, governors (b) opener of the day | 1.28 | 34.8 | 46.1 | 43.9 | 30.8 | 8.9 | +16.1 (45.4) | +11.7 (27.1) | +13.9 (26.0) | +6.2 (16.9) | +9.4 (18.2) |
| D6 v2.3b, governors (b') last-entered trade | 1.28 | 41.6 | 57.9 | 50.8 | 35.7 | 8.0 | +22.9 (51.2) | +23.5 (32.7) | +20.8 (29.6) | +11.1 (20.0) | +8.5 (19.2) |
| D6 v2.3b, governors (c) base-lot | 1.28 | 48.1 | 57.6 | 52.2 | 29.3 | 13.8 | +29.5 (35.6) | +23.2 (25.5) | +22.3 (23.6) | +4.7 (15.9) | +14.3 (19.9) |
| D6 v2.3b, governors static (SS, non-causal) | 2.45 | 53.9 | 61.3 | 54.8 | 34.1 | 6.7 | +35.3 (39.1) | +26.8 (27.7) | +24.8 (25.9) | +9.5 (18.6) | +7.2 (19.2) |
| D6 v2.3b, governors (a) running max | 2.45 | 52.6 | 60.3 | 54.7 | 34.4 | 6.5 | +34.0 (40.1) | +25.8 (28.0) | +24.8 (26.0) | +9.8 (17.8) | +7.0 (19.2) |
| D6 v2.3b, governors (b) opener of the day | 2.45 | 31.4 | 42.7 | 41.2 | 27.0 | 6.1 | +12.7 (44.9) | +8.3 (26.9) | +11.2 (25.7) | +2.4 (16.6) | +6.6 (18.1) |
| D6 v2.3b, governors (b') last-entered trade | 2.45 | 38.2 | 52.9 | 46.1 | 31.8 | 4.9 | +19.6 (49.5) | +18.4 (32.9) | +16.1 (29.7) | +7.2 (19.8) | +5.4 (19.3) |
| D6 v2.3b, governors (c) base-lot | 2.45 | 42.7 | 52.9 | 47.7 | 25.0 | 10.7 | +24.1 (35.5) | +18.5 (25.1) | +17.7 (23.1) | +0.4 (15.7) | +11.2 (19.8) |

#### RESEARCH lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6; MV, PB not in the stack)
| config | stop | L3M mean $k/wk | L6M | HOLD | PRE | X' | delta vs as-is $k/wk (MDE): L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|---|---|
| stack as it is (market entries, no rules, join stop 2.45) | 2.45 | -1.0 | 50.0 | 37.2 | 46.1 | 7.0 | - | - | - | - | - |
| D6 v2.3b, governors static (SS, non-causal) | 1.28 | 99.2 | 132.8 | 113.3 | 73.1 | 20.0 | +100.2 (77.7) | +82.8 (51.7) | +76.1 (50.7) | +27.0 (33.3) | +13.0 (34.6) |
| D6 v2.3b, governors (a) running max | 1.28 | 94.2 | 129.5 | 112.1 | 70.9 | 19.8 | +95.2 (75.9) | +79.5 (50.6) | +74.9 (49.4) | +24.7 (33.1) | +12.8 (35.1) |
| D6 v2.3b, governors (b) opener of the day | 1.28 | 59.7 | 90.3 | 79.1 | 51.5 | 22.6 | +60.7 (84.8) | +40.3 (51.0) | +41.9 (50.9) | +5.4 (32.9) | +15.6 (32.5) |
| D6 v2.3b, governors (b') last-entered trade | 1.28 | 78.5 | 119.1 | 98.6 | 54.4 | 21.3 | +79.5 (96.0) | +69.1 (60.0) | +61.4 (57.2) | +8.2 (34.8) | +14.3 (34.5) |
| D6 v2.3b, governors (c) base-lot | 1.28 | 70.5 | 95.7 | 82.1 | 51.7 | 29.0 | +71.5 (63.1) | +45.7 (50.6) | +44.9 (48.7) | +5.6 (29.3) | +21.9 (36.3) |
| D6 v2.3b, governors static (SS, non-causal) | 2.45 | 89.2 | 121.1 | 102.3 | 63.4 | 13.7 | +90.2 (77.6) | +71.1 (53.6) | +65.1 (52.1) | +17.2 (32.6) | +6.7 (34.5) |
| D6 v2.3b, governors (a) running max | 2.45 | 84.4 | 118.2 | 101.4 | 60.8 | 13.6 | +85.5 (75.7) | +68.2 (52.5) | +64.2 (50.7) | +14.7 (32.5) | +6.6 (34.7) |
| D6 v2.3b, governors (b) opener of the day | 2.45 | 50.6 | 82.3 | 72.6 | 44.8 | 16.9 | +51.6 (86.6) | +32.3 (51.5) | +35.4 (50.8) | -1.4 (32.6) | +9.9 (32.1) |
| D6 v2.3b, governors (b') last-entered trade | 2.45 | 66.9 | 105.7 | 86.8 | 46.7 | 15.3 | +67.9 (94.3) | +55.7 (60.6) | +49.6 (57.7) | +0.6 (34.4) | +8.3 (34.8) |
| D6 v2.3b, governors (c) base-lot | 2.45 | 61.0 | 88.0 | 74.7 | 43.2 | 23.6 | +62.1 (62.1) | +38.0 (50.7) | +37.5 (48.9) | -3.0 (29.3) | +16.6 (36.2) |

#### Weekly statistics of the headline reading (a), live lots
| config | window | mean $k/wk | SD | maxDD | worst-20 (sum $k) | delta vs as-is $k/wk (MDE) [4-wk-block 95% CI] |
|---|---|---|---|---|---|---|
| stack as it is | L3M | 13.8 | 48 | 98 | 193 | - |
|  | L6M | 24.0 | 47 | 98 | 68 | - |
|  | HOLD | 23.7 | 56 | 155 | -178 | - |
|  | PRE | 17.7 | 53 | 232 | -874 | - |
|  | X' | -3.6 | 29 | 330 | -588 | - |
| D6 v2.3b, (a) running-max governors, Native 1.28 | L3M | 33.2 | 46 | 102 | 464 | +19.4 (24.1) [+6.5, +33.0] |
|  | L6M | 42.6 | 42 | 102 | 401 | +18.5 (17.4) [+9.2, +26.1] |
|  | HOLD | 39.9 | 52 | 109 | 165 | +16.2 (16.8) [+7.6, +24.1] |
|  | PRE | 22.4 | 57 | 267 | -905 | +4.7 (13.4) [-4.5, +15.6] |
|  | X' | 9.0 | 33 | 154 | -395 | +12.5 (14.7) [+4.7, +21.0] |

#### Same, research lots
| config | window | mean $k/wk | SD | maxDD | worst-20 (sum $k) | delta vs as-is $k/wk (MDE) [4-wk-block 95% CI] |
|---|---|---|---|---|---|---|
| stack as it is | L3M | -1.0 | 141 | 417 | -14 | - |
|  | L6M | 50.0 | 145 | 417 | -372 | - |
|  | HOLD | 37.2 | 173 | 684 | -1321 | - |
|  | PRE | 46.1 | 137 | 778 | -2620 | - |
|  | X' | 7.0 | 104 | 560 | -1661 | - |
| D6 v2.3b, (a) running-max governors, Native 1.28 | L3M | 94.2 | 153 | 453 | 1318 | +95.2 (75.9) [+53.5, +146.1] |
|  | L6M | 129.5 | 145 | 453 | 1268 | +79.5 (50.6) [+41.4, +114.1] |
|  | HOLD | 112.1 | 168 | 453 | 288 | +74.9 (49.4) [+44.2, +108.4] |
|  | PRE | 70.9 | 154 | 525 | -2265 | +24.7 (33.1) [+6.7, +47.5] |
|  | X' | 19.8 | 107 | 625 | -1427 | +12.8 (35.1) [-7.6, +32.0] |

Trades per week D6 / as-is (kept trades; L6M ; HOLD ; PRE ; X'): live 109 / 100 ; 105 / 98 ; 99 / 95 ; 62 / 73; research 162 / 127 ; 157 / 126 ; 147 / 128 ; 95 / 105.

## 2. Item 2: M6 (MV) and A6 (PB) in the lock-engine stack; O6
**Mapping (verified).** `d6_tag` of the trade library (abr_build.py) and the D6 tag table in DS3_MAEMFE.md: KB=K6, PE=P6 (PB3B), SM=U6, HM=H6, **MV=M6, PB=A6**, DN=N6, CR=C6; ST, WT, MA are placeholders (S6, W6, MA6) and are not D6. O6 (the opening-range book, DS3_SESSION2_Q_OPEN_BOOK.md, verdict DEAD) is not in the tag table and not in the trade library. A6 is the library `PB` series (4,049 trades), not the PB7 variant (PB7 has no series in the library).
**Done: MV (5,167 trades) and PB (4,049) are inside the lock engine** (8 books: ST HM WT KB SM PE MV PB; per-book day/week locks, one position per book, the Asia-stopped cut counts them as open same-side books, ER sizer and zone skip apply to their signals: ER is defined for 100% of their signals, ER >= 0.30 on 41% / 44%, the zone skip fires on 15% / 6%). Their 70/30 outcomes use the same S73 cell as the other books (MV and PB were not in the SS split tables; the six SS books tie out to the dollar). Lots: M6 2 (London, NY-AM), A6 1 (all sessions; variant with 0 in PRE/CLOSE below), governor R = nominal live lot x 60 pt x $20. Research lots for MV, PB are 10 (l2feat LOTS) and appear only in the `research8` run.
Effect of adding the two books (running-max governors, Native 1.28, N basis, delta vs as-is, $k/wk, MDE):

| lots | what is added | as-is mean L6M | D6 (a) mean L6M | delta vs as-is: L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|
| live4 | K6 P6 U6 H6 (user sessions) | 19.8 | 37.7 | +17.8 (18.2) | +15.5 (17.5) | +4.4 (13.2) | +10.0 (13.7) |
| live | + M6=MV 2 and A6=PB 1 | 24.0 | 42.6 | +18.5 (17.4) | +16.2 (16.8) | +4.7 (13.4) | +12.5 (14.7) |
| liveX | + M6, A6 with A6 0 in PRE/CLOSE | 24.2 | 42.8 | +18.6 (17.4) | +16.3 (16.7) | +4.8 (13.5) | +12.5 (14.6) |

Per-book table, live lots (D6 (a) minus as-is):

| book | window | as-is $k/wk | D6 $k/wk | delta |
|---|---|---|---|---|
| HM | L3M | 7.0 | 11.4 | +4.4 |
| HM | L6M | 5.4 | 9.8 | +4.4 |
| HM | HOLD | 4.9 | 8.7 | +3.8 |
| HM | PRE | 2.7 | 2.8 | +0.0 |
| HM | X' | -0.8 | -0.3 | +0.5 |
| KB | L3M | -1.7 | 2.2 | +3.9 |
| KB | L6M | 3.2 | 5.2 | +2.0 |
| KB | HOLD | 2.6 | 4.3 | +1.6 |
| KB | PRE | 4.0 | 3.8 | -0.2 |
| KB | X' | -0.2 | 1.0 | +1.2 |
| SM | L3M | -0.3 | -2.4 | -2.1 |
| SM | L6M | 1.1 | 0.4 | -0.7 |
| SM | HOLD | 1.1 | 0.7 | -0.5 |
| SM | PRE | 2.6 | 2.4 | -0.2 |
| SM | X' | 0.5 | 2.2 | +1.7 |
| PE | L3M | 6.3 | 18.6 | +12.3 |
| PE | L6M | 10.1 | 22.3 | +12.2 |
| PE | HOLD | 11.5 | 22.2 | +10.7 |
| PE | PRE | 6.5 | 11.4 | +4.9 |
| PE | X' | -1.6 | 5.7 | +7.4 |
| MV | L3M | -0.0 | -0.4 | -0.4 |
| MV | L6M | 1.3 | 0.6 | -0.7 |
| MV | HOLD | 1.4 | 0.6 | -0.7 |
| MV | PRE | 1.8 | 2.1 | +0.3 |
| MV | X' | -1.6 | -0.5 | +1.1 |
| PB | L3M | 2.5 | 3.7 | +1.2 |
| PB | L6M | 2.9 | 4.2 | +1.3 |
| PB | HOLD | 2.2 | 3.4 | +1.3 |
| PB | PRE | 0.1 | -0.0 | -0.2 |
| PB | X' | 0.1 | 0.9 | +0.8 |

M6 (MV) loses a little under the composite (L6M -0.7k, HOLD -0.7k, PRE +0.3k, X' +1.1k) and A6 (PB) gains (+1.3k / +1.3k / -0.2k / +0.8k): every per-book number for the two new books is inside its MDE (about 1-2k); the stack-level gain from adding them (+0.7k L6M) is not distinguishable from zero.

**Research-lots check with MV and PB at 10 lots (8 books):** delta vs as-is +126.5 (81.4) | +104.4 (56.7) | +96.6 (54.5) | +31.5 (48.9) | +31.1 (48.2) (L3M | L6M | HOLD | PRE | X').

**O6.** No per-trade series in the library and no lock-engine form; the only series is the weekly book from the T-OPEN solve (`out/ob/series_look.pkl`, 3 opening-range cells at $1,000 risk per trade, locks inside, N basis). Run as a STAND-ALONE additive line (no sizer, split, zone, PE or cut: those need signal-time state the weekly series does not have; the live O6 cells may differ from the three that solve picked, and the book was tiered DEAD: G3 beta, G8 2023, G9 best-of-N): $/wk at about 1 lot = L3M +951, L6M +975, HOLD +768, PRE +1798, X' -152 (HOLD CI includes 0, X' negative). Adding it to the stack changes the delta by +0.8k..+1.0k a week at most in L6M/HOLD, which is inside every MDE; it is not included in any headline number.
**Limitations of the MV/PB extension:** (i) the rule sim uses research lots (MV, PB 10) only as relative weights and for the cut fraction arithmetic; the lock engine and all $ use the live lots; (ii) MV and PB had no PE-style confirmation (the PE piece acts on P6 only); (iii) the split is the L2SE S73 cell, fractional: A6 at 1 lot cannot be split and M6 at 2 lots is 1/1 (section 3b gives the integer-lot version).

## 3. Items 3 and 4: bases and live-lot sessions
### 3a. Bases (composite, delta vs as-is on the same basis)
Basis N = no target correction; M = measured with the year target-fill correction (1.4 / 1.5 / 4.2 / 4.3 pt) and the 70/30 outcomes recomputed on M; LIVE-CAL (LIVE_CAL_SUMMARY.md) = N with the stop cost 2.45 (stop-class exits 2.45 worse than the nominal level); M with the 2.45 stop is the LIVE-P9 stress. "As-is" is always the join stop 2.45 on that basis. The Native 1.28 vs join 2.45 comparison is the stop column.

#### LIVE lots (user sessions): K6 2, P6 7, U6 4, H6 4/2, M6 2, A6 1 (ST, WT, O6 0)
| basis | stop | governors | as-is mean L6M | D6 mean L6M | delta vs as-is $k/wk (MDE): L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| N (no target correction) | Native 1.28 | (a) running max | 24.0 | 42.6 | +19.4 (24.1) | +18.5 (17.4) | +16.2 (16.8) | +4.7 (13.4) | +12.5 (14.7) |
| N (no target correction) | Native 1.28 | static (SS, non-causal) | 24.0 | 43.4 | +21.4 (22.5) | +19.4 (16.9) | +16.9 (16.4) | +4.0 (14.3) | +12.5 (14.7) |
| N (no target correction) = LIVE-CAL | join 2.45 | (a) running max | 24.0 | 40.2 | +17.1 (24.5) | +16.2 (17.8) | +13.9 (17.0) | +2.3 (13.5) | +10.8 (14.7) |
| N (no target correction) = LIVE-CAL | join 2.45 | static (SS, non-causal) | 24.0 | 41.4 | +19.3 (23.0) | +17.4 (17.1) | +14.9 (16.5) | +1.4 (14.4) | +10.8 (14.7) |
| M (target correction 1.4/1.5/4.2/4.3) | Native 1.28 | (a) running max | 8.2 | 26.8 | +19.6 (25.2) | +18.6 (18.0) | +16.4 (16.9) | +6.1 (13.1) | +13.4 (14.6) |
| M (target correction 1.4/1.5/4.2/4.3) | Native 1.28 | static (SS, non-causal) | 8.2 | 27.7 | +21.0 (23.9) | +19.5 (17.3) | +17.2 (16.3) | +5.4 (13.8) | +13.3 (14.7) |
| M (target correction 1.4/1.5/4.2/4.3) = LIVE-P9 stress | join 2.45 | (a) running max | 8.2 | 24.2 | +16.8 (25.0) | +16.0 (18.3) | +13.6 (17.3) | +3.5 (13.3) | +11.5 (14.6) |
| M (target correction 1.4/1.5/4.2/4.3) = LIVE-P9 stress | join 2.45 | static (SS, non-causal) | 8.2 | 25.1 | +18.0 (23.8) | +16.9 (17.6) | +14.7 (16.5) | +2.6 (14.0) | +11.4 (14.7) |

#### LIVE lots + ST, WT at research/2.35 (4.26 / 2.98)
| basis | stop | governors | as-is mean L6M | D6 mean L6M | delta vs as-is $k/wk (MDE): L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| N (no target correction) | Native 1.28 | (a) running max | 34.4 | 65.5 | +38.6 (40.8) | +31.1 (27.2) | +29.7 (25.4) | +14.9 (18.1) | +9.9 (19.2) |
| N (no target correction) | Native 1.28 | static (SS, non-causal) | 34.4 | 66.7 | +40.1 (39.6) | +32.3 (26.9) | +29.9 (25.3) | +14.5 (19.0) | +10.2 (19.2) |
| N (no target correction) = LIVE-CAL | join 2.45 | (a) running max | 34.4 | 60.3 | +34.0 (40.1) | +25.8 (28.0) | +24.8 (26.0) | +9.8 (17.8) | +7.0 (19.2) |
| N (no target correction) = LIVE-CAL | join 2.45 | static (SS, non-causal) | 34.4 | 61.3 | +35.3 (39.1) | +26.8 (27.7) | +24.8 (25.9) | +9.5 (18.6) | +7.2 (19.2) |
| M (target correction 1.4/1.5/4.2/4.3) | Native 1.28 | (a) running max | 11.2 | 38.8 | +35.1 (40.4) | +27.6 (27.3) | +26.2 (25.3) | +13.7 (17.1) | +10.6 (19.0) |
| M (target correction 1.4/1.5/4.2/4.3) | Native 1.28 | static (SS, non-causal) | 11.2 | 39.9 | +35.3 (39.7) | +28.7 (26.9) | +26.3 (25.1) | +13.5 (17.9) | +10.8 (19.1) |
| M (target correction 1.4/1.5/4.2/4.3) = LIVE-P9 stress | join 2.45 | (a) running max | 11.2 | 35.2 | +31.1 (40.3) | +24.0 (27.6) | +22.2 (25.4) | +10.0 (17.1) | +7.5 (19.0) |
| M (target correction 1.4/1.5/4.2/4.3) = LIVE-P9 stress | join 2.45 | static (SS, non-causal) | 11.2 | 36.1 | +31.1 (39.6) | +24.9 (27.2) | +22.5 (25.2) | +9.3 (18.1) | +7.7 (19.1) |

#### RESEARCH lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6; MV, PB not in the stack)
| basis | stop | governors | as-is mean L6M | D6 mean L6M | delta vs as-is $k/wk (MDE): L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|---|
| N (no target correction) | Native 1.28 | (a) running max | 50.0 | 129.5 | +95.2 (75.9) | +79.5 (50.6) | +74.9 (49.4) | +24.7 (33.1) | +12.8 (35.1) |
| N (no target correction) | Native 1.28 | static (SS, non-causal) | 50.0 | 132.8 | +100.2 (77.7) | +82.8 (51.7) | +76.1 (50.7) | +27.0 (33.3) | +13.0 (34.6) |
| N (no target correction) = LIVE-CAL | join 2.45 | (a) running max | 50.0 | 118.2 | +85.5 (75.7) | +68.2 (52.5) | +64.2 (50.7) | +14.7 (32.5) | +6.6 (34.7) |
| N (no target correction) = LIVE-CAL | join 2.45 | static (SS, non-causal) | 50.0 | 121.1 | +90.2 (77.6) | +71.1 (53.6) | +65.1 (52.1) | +17.2 (32.6) | +6.7 (34.5) |
| M (target correction 1.4/1.5/4.2/4.3) | Native 1.28 | (a) running max | 7.7 | 74.8 | +79.6 (74.6) | +67.1 (49.7) | +63.0 (48.3) | +21.1 (32.0) | +13.6 (34.5) |
| M (target correction 1.4/1.5/4.2/4.3) | Native 1.28 | static (SS, non-causal) | 7.7 | 78.2 | +82.0 (76.4) | +70.5 (49.9) | +64.3 (48.8) | +22.1 (31.9) | +13.2 (34.2) |
| M (target correction 1.4/1.5/4.2/4.3) = LIVE-P9 stress | join 2.45 | (a) running max | 7.7 | 67.9 | +72.3 (74.6) | +60.3 (50.4) | +55.6 (49.0) | +13.1 (31.6) | +7.0 (34.4) |
| M (target correction 1.4/1.5/4.2/4.3) = LIVE-P9 stress | join 2.45 | static (SS, non-causal) | 7.7 | 71.0 | +74.8 (76.5) | +63.3 (50.7) | +56.8 (49.3) | +13.2 (32.2) | +6.8 (34.2) |

Reading: the basis moves the DELTA little (live, running max, Native: L6M +18.5k N / +18.6k M; with the 2.45 join +16.2k LIVE-CAL / +16.0k M); the level of both stacks falls on M (as-is L6M 24.0k N vs 8.2k M at live lots), which is the target-fill question the live calibration leaves undecided (11 of 11 touched targets filled, no marginal touches). Native vs join: Native 1.28 vs the 2.45 join is worth +2.3k L6M at live lots and +11.4k at research lots in the composite.

### 3b. Executable lots (integer split, add slippage, rounded ER lots)
The headline uses the fractional 70/30 and fractional ER lots. D6 trades whole contracts: K6 2 = 1/1, U6 4 = 3/1, H6 4 = 3/1 (1/1 in NY-AM), P6 7 = 5/2, M6 2 = 1/1, A6 1 = unsplittable (market); the add pays +0.25 (modelled; +0.45 stress, UF-ENTRY C7) per lot; ER lots = session lot x 1.5 / x 0.5 rounded half-up to a whole contract, minimum 1 (the rounding policy is NOT specified by the directive: the rows below are a sensitivity). Delta vs as-is, $k/wk (MDE):

#### live

| executability variant (causal running-max governors) | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| FULL frac | +19.4 (24.1) | +18.5 (17.4) | +16.2 (16.8) | +4.7 (13.4) | +12.5 (14.7) |
| int split, slip 0.25, A6 market | +20.6 (24.0) | +18.5 (17.5) | +16.0 (16.8) | +4.3 (13.4) | +12.0 (14.9) |
| int split, slip 0.45, A6 market | +20.1 (23.9) | +18.0 (17.2) | +15.5 (16.6) | +4.0 (13.4) | +11.8 (14.9) |
| int split 0.25 + ER lots rounded | +25.0 (22.6) | +22.8 (17.6) | +19.3 (17.3) | +7.4 (13.0) | +12.9 (15.0) |
| int split 0.45 + ER lots rounded | +24.6 (22.5) | +22.2 (17.4) | +18.8 (17.2) | +7.1 (13.0) | +12.7 (15.0) |
| frac split + ER lots rounded | +23.9 (21.9) | +22.4 (17.0) | +19.2 (16.8) | +7.7 (13.2) | +13.7 (14.9) |
| FULL base-lot governors, int 0.25 + rounded | +6.1 (26.5) | +11.2 (17.4) | +10.0 (16.0) | +0.4 (13.0) | +12.8 (14.3) |

#### live4

| executability variant (causal running-max governors) | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| FULL frac | +18.7 (25.2) | +17.8 (18.2) | +15.5 (17.5) | +4.4 (13.2) | +10.0 (13.7) |
| int split, slip 0.25, A6 market | +19.9 (25.9) | +17.8 (18.7) | +15.3 (17.9) | +4.1 (13.0) | +9.6 (14.0) |
| int split, slip 0.45, A6 market | +19.6 (25.9) | +17.5 (18.6) | +15.1 (17.8) | +3.8 (13.0) | +9.4 (14.0) |
| int split 0.25 + ER lots rounded | +24.6 (24.1) | +21.4 (18.6) | +18.3 (18.0) | +5.7 (12.5) | +10.5 (14.2) |
| int split 0.45 + ER lots rounded | +24.2 (24.1) | +21.1 (18.5) | +18.0 (18.0) | +5.4 (12.5) | +10.3 (14.2) |
| frac split + ER lots rounded | +23.4 (23.4) | +21.5 (18.1) | +18.5 (17.7) | +6.0 (12.7) | +11.0 (13.9) |
| FULL base-lot governors, int 0.25 + rounded | +7.9 (26.3) | +11.7 (17.5) | +10.5 (16.3) | +0.4 (12.8) | +10.3 (13.1) |

#### research

| executability variant (causal running-max governors) | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| FULL frac | +95.2 (75.9) | +79.5 (50.6) | +74.9 (49.4) | +24.7 (33.1) | +12.8 (35.1) |
| int split, slip 0.25, A6 market | +98.4 (76.2) | +77.7 (51.8) | +72.7 (50.3) | +23.0 (33.1) | +9.6 (35.7) |
| int split, slip 0.45, A6 market | +97.5 (76.3) | +76.5 (51.7) | +71.5 (50.3) | +22.2 (33.1) | +8.9 (35.7) |
| int split 0.25 + ER lots rounded | +97.7 (73.5) | +74.9 (49.7) | +70.8 (48.6) | +23.1 (33.3) | +9.5 (34.9) |
| int split 0.45 + ER lots rounded | +96.7 (73.8) | +73.7 (49.8) | +69.2 (49.1) | +22.2 (33.2) | +8.8 (34.9) |
| frac split + ER lots rounded | +96.1 (73.5) | +78.0 (49.5) | +73.4 (48.9) | +23.9 (33.3) | +12.1 (34.3) |
| FULL base-lot governors, int 0.25 + rounded | +72.8 (67.3) | +44.1 (53.0) | +43.0 (50.7) | +3.8 (29.1) | +20.5 (36.5) |

Reading: integer splits with slippage change the live delta by -0.5k..0 (L6M +18.5k -> +18.5k / +18.0k); rounding the ER lots half-up RAISES it (+22.8k L6M at live lots) because 0.5 x 1 lot and 0.5 x 3.5 lots round up and 1.5 x 7 rounds up (more average lots, not more edge): the number at live lots is therefore sensitive to the rounding rule; use the fractional line for the headline and ask D6 which rule it uses (MORNING.md question).

### 3c. Session tags (verified) and the live-lot assignment
D6 / THP session tag by ENTRY minute (ET), verified in `l2vast/ds3/code/thp/thp_dict.py` and `session_entry` of the trade library: asia 18:00-02:00, london 02:00-08:30, pre 08:30-09:30, nyam 09:30-12:00, nypm 12:00-15:00, close 15:00-16:54 (DIRECTIVE_SESSION_20261028.md says the same). SS had assumed pre -> London and close -> NY-PM and had given K6 lots in pre/close and P6/U6 lots in pre; the user's list does not mention PRE or CLOSE for any book, so those entry sessions are lot 0 here (a PRE signal takes no trade): K6 2 in asia/london/nyam/nypm, P6 7 in asia/london/nyam, U6 4 in asia/london, H6 4 asia / 2 nyam, M6 2 london/nyam, A6 1 in every session (listed without sessions; the liveX row sets it to 0 in pre/close: no change beyond 0.1k). Effect of the assignment on the four SS books:

| lots / sessions | governors | as-is mean L6M | D6 mean L6M | delta vs as-is $k/wk (MDE): L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|---|
| K6 P6 U6 H6, SS assumption (pre->London, close->NY-PM) | static (SS, non-causal) | 18.1 | 40.4 | +25.8 (27.4) | +22.3 (18.9) | +20.0 (18.3) | +3.3 (14.4) | +11.1 (14.7) |
| K6 P6 U6 H6, SS assumption (pre->London, close->NY-PM) | (a) running max | 18.1 | 39.4 | +23.6 (29.0) | +21.3 (19.4) | +18.9 (18.8) | +3.7 (13.7) | +11.6 (14.5) |
| K6 P6 U6 H6, user sessions (PRE and CLOSE lot 0) | static (SS, non-causal) | 19.8 | 38.5 | +20.6 (24.1) | +18.7 (17.9) | +16.3 (17.3) | +3.2 (13.9) | +10.0 (13.8) |
| K6 P6 U6 H6, user sessions (PRE and CLOSE lot 0) | (a) running max | 19.8 | 37.7 | +18.7 (25.2) | +17.8 (18.2) | +15.5 (17.5) | +4.4 (13.2) | +10.0 (13.7) |

Per-session table, live lots, D6 (a) vs as-is (pre and close are the A6-only sessions):

| session | window | as-is $k/wk | D6 $k/wk | delta | trades/wk as-is | trades/wk D6 |
|---|---|---|---|---|---|---|
| asia | L3M | 4.7 | 20.7 | +15.9 | 44.9 | 42.4 |
| asia | L6M | 12.5 | 23.5 | +11.0 | 40.6 | 35.7 |
| asia | HOLD | 10.3 | 21.2 | +10.9 | 40.0 | 34.3 |
| asia | PRE | 9.5 | 11.7 | +2.2 | 37.5 | 30.6 |
| asia | X' | -4.4 | 4.8 | +9.2 | 25.0 | 15.1 |
| london | L3M | 8.5 | 2.5 | -6.0 | 25.8 | 32.4 |
| london | L6M | 8.6 | 8.0 | -0.5 | 24.2 | 27.1 |
| london | HOLD | 9.7 | 8.3 | -1.4 | 23.7 | 26.0 |
| london | PRE | -0.3 | -0.3 | +0.0 | 23.9 | 24.6 |
| london | X' | 0.4 | 1.6 | +1.2 | 14.7 | 12.5 |
| pre | L3M | 0.2 | 0.5 | +0.3 | 0.8 | 1.4 |
| pre | L6M | -0.1 | -0.0 | +0.0 | 0.9 | 1.3 |
| pre | HOLD | -0.2 | -0.2 | -0.0 | 0.9 | 1.2 |
| pre | PRE | 0.1 | 0.1 | -0.0 | 1.1 | 1.4 |
| pre | X' | -0.2 | -0.1 | +0.1 | 0.9 | 1.0 |
| nyam | L3M | 1.0 | 10.6 | +9.6 | 28.1 | 39.2 |
| nyam | L6M | 2.8 | 11.2 | +8.4 | 28.8 | 36.4 |
| nyam | HOLD | 3.6 | 10.3 | +6.8 | 28.8 | 35.4 |
| nyam | PRE | 7.3 | 10.8 | +3.4 | 28.1 | 33.4 |
| nyam | X' | 0.6 | 3.2 | +2.6 | 26.5 | 25.6 |
| nypm | L3M | -0.5 | -1.1 | -0.5 | 3.2 | 8.4 |
| nypm | L6M | 0.3 | -0.1 | -0.3 | 4.9 | 8.8 |
| nypm | HOLD | 0.4 | 0.2 | -0.2 | 4.8 | 8.5 |
| nypm | PRE | 1.1 | 0.2 | -0.9 | 4.8 | 8.9 |
| nypm | X' | -0.0 | -0.5 | -0.4 | 6.0 | 7.6 |
| close | L6M | 0.0 | 0.0 | +0.0 | 0.0 | 0.0 |
| close | HOLD | 0.0 | 0.0 | +0.0 | 0.0 | 0.0 |
| close | PRE | 0.0 | 0.0 | +0.0 | 0.0 | 0.0 |

Research lots (all sessions at research lots):

| session | window | as-is $k/wk | D6 $k/wk | delta | trades/wk as-is | trades/wk D6 |
|---|---|---|---|---|---|---|
| asia | L3M | 14.5 | 61.6 | +47.1 | 61.8 | 59.4 |
| asia | L6M | 27.4 | 56.2 | +28.8 | 56.4 | 50.0 |
| asia | HOLD | 17.1 | 46.5 | +29.4 | 55.4 | 47.8 |
| asia | PRE | 24.2 | 34.5 | +10.3 | 51.2 | 42.0 |
| asia | X' | -3.5 | 6.8 | +10.4 | 32.3 | 19.5 |
| london | L3M | 7.8 | -4.1 | -11.9 | 27.6 | 41.1 |
| london | L6M | 18.6 | 20.9 | +2.2 | 28.5 | 35.6 |
| london | HOLD | 19.2 | 20.8 | +1.6 | 28.0 | 34.1 |
| london | PRE | 3.5 | 5.2 | +1.7 | 30.4 | 33.2 |
| london | X' | 9.5 | 9.3 | -0.2 | 20.5 | 17.2 |
| pre | L3M | -10.5 | 4.3 | +14.8 | 5.4 | 10.2 |
| pre | L6M | -6.4 | 0.8 | +7.2 | 5.8 | 9.0 |
| pre | HOLD | -10.1 | -1.7 | +8.4 | 5.9 | 8.7 |
| pre | PRE | -0.1 | -3.9 | -3.8 | 7.3 | 9.5 |
| pre | X' | -2.5 | 1.0 | +3.5 | 7.2 | 6.7 |
| nyam | L3M | 3.7 | 37.9 | +34.2 | 22.8 | 45.3 |
| nyam | L6M | 13.8 | 42.9 | +29.2 | 26.0 | 43.5 |
| nyam | HOLD | 15.5 | 40.1 | +24.6 | 26.2 | 42.6 |
| nyam | PRE | 17.9 | 29.7 | +11.8 | 26.4 | 37.8 |
| nyam | X' | 1.9 | 2.5 | +0.7 | 28.6 | 30.9 |
| nypm | L3M | -15.6 | -4.6 | +11.0 | 6.5 | 23.2 |
| nypm | L6M | -2.8 | 9.8 | +12.6 | 10.4 | 24.1 |
| nypm | HOLD | -3.7 | 7.9 | +11.6 | 10.4 | 23.2 |
| nypm | PRE | 0.8 | 5.8 | +5.0 | 12.7 | 24.4 |
| nypm | X' | 1.5 | -0.4 | -1.8 | 15.8 | 20.4 |
| close | L3M | -0.9 | -0.8 | +0.1 | 0.1 | 0.1 |
| close | L6M | -0.5 | -1.0 | -0.5 | 0.1 | 0.1 |
| close | HOLD | -0.8 | -1.4 | -0.6 | 0.2 | 0.2 |
| close | PRE | -0.1 | -0.4 | -0.4 | 0.1 | 0.2 |
| close | X' | 0.3 | 0.5 | +0.2 | 0.1 | 0.1 |

## 4. Item 5: "no add on K6": SS (lowers the stack 0.2-0.7k) vs UF-ENTRY C7 (K6 -3.0k L6M)
**Both are reproduced on ONE engine (this lock engine, N basis); they measure different contexts; for Sunday SS's context (the composite) is the relevant one, and in neither context is the K6 add distinguishable from zero at the live lots.** The table varies only what the two reports differ on: the K6 book is the only book whose add changes in the first rows (K6 alone splits 1/1 with the add slip, every other book at market), then the pieces are switched on one at a time, then the whole composite with all books on the integer split.

Research lots (K6 5.2 lots, C7's lots; the planned-lot units of the books are identical):

| engine context | add slip pt/lot | K6-book delta add-on minus add-off, $k/wk: L6M / HOLD / PRE / X' | MDE (same order) | whole-stack delta | K6 lots per trade, add-on / add-off |
|---|---|---|---|---|---|
| PLAIN stack (no ER, zone, cut, PE; stop 1.01 N): K6 alone splits 1/1, other books market | 0.25 | -2.1 / -1.5 / -3.2 / +0.6 | 8.0 / 7.1 / 3.7 / 3.9 | -2.1 / -1.5 / -3.2 / +0.6 | 0.993 / 1.000 |
| PLAIN stack (no ER, zone, cut, PE; stop 1.01 N): K6 alone splits 1/1, other books market | 0.45 | -3.0 / -2.3 / -3.5 / +0.4 | 7.5 / 6.6 / 3.7 / 3.9 | -3.0 / -2.3 / -3.5 / +0.4 | 0.993 / 1.000 |
| PLAIN stack, all books integer split, K6 add on vs off | 0.25 | -2.1 / -1.5 / -3.2 / +0.6 | 8.0 / 7.1 / 3.7 / 3.9 | -2.1 / -1.5 / -3.2 / +0.6 | 0.993 / 1.000 |
| PLAIN, ideal fractional 70/30 on all books, K6 add on vs off | 0 | +0.5 / +0.7 / -1.9 / +0.9 | 7.0 / 6.2 / 2.8 / 3.5 | +0.5 / +0.7 / -1.9 / +0.9 | 0.996 / 1.000 |
| + ER sizer only (K6 alone splits) | 0.25 | -0.5 / -0.9 / +0.4 / +0.3 | 7.2 / 6.4 / 3.5 / 2.6 | -0.5 / -0.9 / +0.4 / +0.3 | 0.993 / 1.000 |
| + zone skip only (K6 alone splits) | 0.25 | +0.9 / +0.8 / -0.7 / -0.1 | 6.8 / 6.0 / 3.0 / 3.2 | +0.9 / +0.8 / -0.7 / -0.1 | 0.995 / 1.000 |
| + Asia-stopped cut only (K6 alone splits) | 0.25 | -1.9 / -1.3 / -0.9 / +0.4 | 8.8 / 7.8 / 3.5 / 2.9 | -0.3 / +0.2 / -0.9 / +0.4 | 0.993 / 1.000 |
| + ER + zone + cut (K6 alone splits) | 0.25 | +1.6 / +0.7 / +2.9 / +0.5 | 7.1 / 6.5 / 3.4 / 3.2 | +1.6 / +0.7 / +2.9 / +0.5 | 0.995 / 1.000 |
| COMPOSITE (all six pieces, causal running-max governors, Native 1.28): all books integer split, K6 add on vs off | 0.0 | +2.0 / +1.1 / +2.8 / +0.7 | 7.1 / 6.5 / 3.4 / 3.2 | +2.0 / +1.0 / +2.8 / +0.7 | 0.995 / 1.000 |
| COMPOSITE (all six pieces, causal running-max governors, Native 1.28): all books integer split, K6 add on vs off | 0.25 | +1.2 / +0.3 / +2.6 / +0.5 | 6.8 / 6.2 / 3.4 / 3.2 | +1.2 / +0.3 / +2.5 / +0.5 | 0.995 / 1.000 |
| COMPOSITE (all six pieces, causal running-max governors, Native 1.28): all books integer split, K6 add on vs off | 0.45 | +0.9 / +0.1 / +2.4 / +0.4 | 6.7 / 6.1 / 3.3 / 3.2 | +0.9 / +0.0 / +2.3 / +0.4 | 0.995 / 1.000 |
| COMPOSITE, fractional 70/30 (SS "no add on K6" row) | 0 | +1.5 / +1.0 / +2.4 / +1.2 | 3.4 / 3.1 / 3.1 / 2.3 | +1.5 / +1.0 / +2.4 / +1.2 | 0.997 / 1.000 |

Live lots (K6 2 lots):

| engine context | add slip pt/lot | K6-book delta add-on minus add-off, $k/wk: L6M / HOLD / PRE / X' | MDE (same order) | whole-stack delta | K6 lots per trade, add-on / add-off |
|---|---|---|---|---|---|
| PLAIN stack (no ER, zone, cut, PE; stop 1.01 N): K6 alone splits 1/1, other books market | 0.25 | -0.7 / -0.4 / -0.3 / +0.1 | 3.0 / 2.7 / 1.2 / 1.5 | -0.7 / -0.4 / -0.3 / +0.1 | 0.993 / 1.000 |
| PLAIN stack (no ER, zone, cut, PE; stop 1.01 N): K6 alone splits 1/1, other books market | 0.45 | -1.3 / -0.9 / -0.4 / +0.0 | 2.9 / 2.6 / 1.2 / 1.5 | -1.3 / -0.9 / -0.4 / +0.0 | 0.993 / 1.000 |
| PLAIN stack, all books integer split, K6 add on vs off | 0.25 | -0.7 / -0.4 / -0.3 / +0.1 | 3.0 / 2.7 / 1.2 / 1.5 | -0.7 / -0.4 / -0.3 / +0.1 | 0.993 / 1.000 |
| PLAIN, ideal fractional 70/30 on all books, K6 add on vs off | 0 | +0.1 / +0.2 / -0.1 / +0.2 | 2.7 / 2.4 / 0.9 / 1.3 | +0.1 / +0.2 / -0.1 / +0.2 | 0.996 / 1.000 |
| + ER sizer only (K6 alone splits) | 0.25 | -0.2 / -0.3 / +0.0 / -0.2 | 2.7 / 2.4 / 1.1 / 1.0 | -0.2 / -0.3 / +0.0 / -0.2 | 0.993 / 1.000 |
| + zone skip only (K6 alone splits) | 0.25 | +0.7 / +0.6 / +0.6 / -0.3 | 2.8 / 2.4 / 1.3 / 1.1 | +0.7 / +0.6 / +0.6 / -0.3 | 0.995 / 1.000 |
| + Asia-stopped cut only (K6 alone splits) | 0.25 | -1.4 / -1.0 / -0.1 / -0.1 | 3.1 / 2.8 / 1.2 / 1.2 | -1.4 / -1.1 / -0.4 / +0.0 | 0.993 / 1.000 |
| + ER + zone + cut (K6 alone splits) | 0.25 | +1.0 / +0.6 / +0.6 / -0.1 | 2.5 / 2.3 / 1.1 / 1.1 | +1.0 / +0.6 / +0.6 / -0.1 | 0.995 / 1.000 |
| COMPOSITE (all six pieces, causal running-max governors, Native 1.28): all books integer split, K6 add on vs off | 0.0 | +1.1 / +0.7 / +0.7 / -0.1 | 2.5 / 2.3 / 1.2 / 1.1 | +1.0 / +0.7 / +0.7 / -0.1 | 0.995 / 1.000 |
| COMPOSITE (all six pieces, causal running-max governors, Native 1.28): all books integer split, K6 add on vs off | 0.25 | +0.7 / +0.4 / +0.6 / -0.1 | 2.4 / 2.2 / 1.1 / 1.1 | +0.7 / +0.4 / +0.5 / -0.1 | 0.995 / 1.000 |
| COMPOSITE (all six pieces, causal running-max governors, Native 1.28): all books integer split, K6 add on vs off | 0.45 | +0.6 / +0.3 / +0.5 / -0.2 | 2.4 / 2.2 / 1.2 / 1.1 | +0.6 / +0.3 / +0.5 / -0.2 | 0.995 / 1.000 |
| COMPOSITE, fractional 70/30 (SS "no add on K6" row) | 0 | +0.4 / +0.2 / +0.5 / +0.0 | 1.3 / 1.2 / 0.9 / 0.8 | +0.4 / +0.2 / +0.5 / +0.0 | 0.997 / 1.000 |

What this says. (1) C7's per-book result is reproduced on the PLAIN stack at research lots: K6 add -2.1k L6M / -1.5k HOLD / -3.2k PRE at +0.25 pt per add lot, -3.0k / -2.3k / -3.5k at +0.45 (C7: -3.0k / -2.4k / -3.1k with its state-dependent slip, i.e. about 0.45 uniform) - with MDE 7-8k, i.e. negative in L6M, HOLD and PRE and +0.6k in X', each number inside its MDE, as C7 itself says; the K6 add changes the average lots per K6 trade by 0.7% (0.993 vs 1.000), so equal-risk scaling cannot change the sign (C7 reports c=1 for the per-book rows too). The no-slip ideal 70/30 is about zero (+0.5 / +0.7 / -1.9): the loss is the 50/50 integer rounding plus the add slip, which is C7's point. At the live 2 lots the same plain-stack effect is -0.7k L6M (MDE 3.0k). (2) SS's sign comes from the pieces that surround the add, not from a different engine: switching on the zone skip moves the K6 add by +3.0k (L6M -2.1k -> +0.9k), the ER sizer by +1.6k (-> -0.5k), the Asia cut by about 0; all three together +1.6k L6M / +0.7k HOLD / +2.9k PRE (research), and the full composite +1.2k / +0.3k / +2.6k / +0.5k (research) and +0.7k / +0.4k / +0.6k / -0.1k (live, +0.25 pt). (The mechanism - which K6 signals the zone skip and the sizer move - was not decomposed here.) (3) SS's earlier statement "no add lowers the stack by 0.4k" is the same thing on a stack that includes the other pieces and the other books' adds; C7's "-3.0k" is the K6 book alone at 2.6x the live lots in a stack with no sizer, no zone skip and no cut. (4) Which is right for Sunday: D6 runs the composite, so the composite number applies: the K6 add is worth +0.4k..+0.7k L6M/HOLD/PRE at live lots (MDE 2.2-2.4k L6M/HOLD, 1.1k PRE), i.e. zero within error and not negative; there is no evidence to remove the add. If the zone skip and the ER sizer were NOT switched on for K6, C7 would apply and the add would be a small loss (-0.7k L6M at 2 lots, -0.3k PRE), also within MDE; D6 owner's risk call, not a numbers call. No change recommended.

## 5. Leave-one-out and each piece alone, causal running-max governors (N basis, Native 1.28 where the stop piece is on)
Contribution = D6 minus D6-without-the-piece; "alone" = the piece on the as-is stack; $k/wk (MDE). Without (6) the stop is the 2.45 join; without (1) the PE confirmation enters at market with the whole lot.

#### LIVE lots (user sessions): K6 2, P6 7, U6 4, H6 4/2, M6 2, A6 1 (ST, WT, O6 0)
| piece | view | L3M | L6M | HOLD | PRE | X' | harmful in all four (L6M,HOLD,PRE,X')? |
|---|---|---|---|---|---|---|---|
| (1) 70/30 split @3 pt | alone vs as-is | +0.3 (15.0) | +0.4 (9.0) | +0.4 (8.0) | -0.2 (3.5) | +2.9 (3.9) | |
|  | left out of FULL (contribution) | +5.2 (7.6) | +2.8 (4.6) | +3.0 (4.4) | +1.9 (3.4) | +0.8 (2.5) | no |
| (2) PE 45-s three-bar NY-AM/NY-PM | alone vs as-is | +2.0 (9.1) | +1.6 (6.4) | +1.3 (5.8) | +0.5 (3.6) | +1.4 (4.9) | |
|  | left out of FULL (contribution) | +5.1 (15.1) | +2.3 (9.0) | +3.1 (8.4) | -1.1 (5.6) | +0.1 (5.8) | no |
| (3) ER(20) 5m x1.5/x0.5 + causal running-max governors | alone vs as-is | +4.5 (17.5) | +6.5 (11.0) | +6.2 (10.8) | -3.0 (11.8) | +3.8 (12.8) | |
|  | left out of FULL (contribution) | +11.6 (24.4) | +10.2 (14.6) | +9.8 (14.1) | +1.4 (9.0) | +0.7 (9.4) | no |
| (4) Asia-stopped -> cut other same-side 50% | alone vs as-is | +1.0 (10.3) | +2.2 (6.9) | +1.5 (6.1) | +1.1 (3.4) | +3.9 (3.7) | |
|  | left out of FULL (contribution) | -0.8 (7.2) | -0.6 (3.9) | -1.0 (3.7) | -0.9 (2.4) | +1.2 (1.4) | no |
| (5) no-trade set (8 lines, D 20, fresh) | alone vs as-is | -2.1 (14.0) | +3.1 (10.0) | +2.2 (11.0) | +0.5 (8.1) | +5.5 (8.3) | |
|  | left out of FULL (contribution) | +2.3 (12.3) | +2.2 (8.3) | +0.7 (9.1) | +1.8 (8.1) | +3.3 (7.8) | no |
| (6) Native stops 1.28 | alone vs as-is | +2.7 (0.7) | +2.7 (0.5) | +2.7 (0.4) | +2.7 (0.4) | +2.4 (0.5) | |
|  | left out of FULL (contribution) | +2.2 (1.7) | +2.3 (1.2) | +2.3 (1.1) | +2.4 (0.5) | +1.7 (0.5) | no |

Pieces meeting the SS change rule (removal improves L6M, HOLD, PRE, X' together): none.

#### LIVE lots + ST, WT at research/2.35 (4.26 / 2.98)
| piece | view | L3M | L6M | HOLD | PRE | X' | harmful in all four (L6M,HOLD,PRE,X')? |
|---|---|---|---|---|---|---|---|
| (1) 70/30 split @3 pt | alone vs as-is | +4.4 (16.2) | +4.6 (9.8) | +4.7 (8.7) | +1.1 (4.6) | +2.3 (5.1) | |
|  | left out of FULL (contribution) | +6.0 (7.9) | +5.5 (5.0) | +5.6 (4.7) | +5.0 (5.2) | -0.1 (3.2) | no |
| (2) PE 45-s three-bar NY-AM/NY-PM | alone vs as-is | +2.0 (9.1) | +1.6 (6.4) | +1.3 (5.8) | +0.5 (3.6) | +1.4 (4.9) | |
|  | left out of FULL (contribution) | +6.2 (14.6) | +1.9 (9.3) | +2.8 (8.7) | -1.8 (6.1) | -0.2 (5.7) | no |
| (3) ER(20) 5m x1.5/x0.5 + causal running-max governors | alone vs as-is | +17.9 (30.9) | +14.8 (20.7) | +15.9 (18.7) | +0.9 (15.9) | +2.0 (16.7) | |
|  | left out of FULL (contribution) | +12.3 (38.5) | +10.4 (23.1) | +11.8 (21.5) | +7.7 (12.9) | +0.4 (11.8) | no |
| (4) Asia-stopped -> cut other same-side 50% | alone vs as-is | +9.7 (15.9) | +7.6 (12.4) | +7.8 (11.1) | +0.4 (7.4) | +2.3 (6.2) | |
|  | left out of FULL (contribution) | +2.2 (13.2) | -1.9 (8.6) | -2.5 (7.8) | -0.8 (4.7) | -1.5 (4.0) | YES |
| (5) no-trade set (8 lines, D 20, fresh) | alone vs as-is | +1.4 (15.0) | +3.0 (12.1) | +2.4 (13.5) | +3.0 (9.6) | +5.0 (11.4) | |
|  | left out of FULL (contribution) | +6.3 (14.4) | +3.3 (11.8) | +0.7 (12.6) | +2.9 (10.2) | +2.2 (10.1) | no |
| (6) Native stops 1.28 | alone vs as-is | +4.8 (2.0) | +4.6 (1.6) | +4.4 (1.5) | +4.5 (1.7) | +3.6 (0.6) | |
|  | left out of FULL (contribution) | +4.6 (2.6) | +5.2 (3.0) | +4.9 (2.7) | +5.1 (2.6) | +3.0 (0.6) | no |

Pieces meeting the change rule: ['cut'] (inside MDE; ST/WT not live).

#### RESEARCH lots (ST10 HM10 WT7 KB5.2 SM7.4 PE5.6; MV, PB not in the stack)
| piece | view | L3M | L6M | HOLD | PRE | X' | harmful in all four (L6M,HOLD,PRE,X')? |
|---|---|---|---|---|---|---|---|
| (1) 70/30 split @3 pt | alone vs as-is | +16.1 (24.4) | +15.1 (15.8) | +16.0 (14.7) | +3.8 (11.2) | +2.5 (8.4) | |
|  | left out of FULL (contribution) | +10.1 (12.2) | +11.1 (8.7) | +11.0 (7.9) | +10.8 (10.8) | +0.8 (6.5) | no |
| (2) PE 45-s three-bar NY-AM/NY-PM | alone vs as-is | +7.0 (7.5) | +4.6 (5.8) | +4.3 (5.4) | +0.5 (3.6) | +0.7 (5.3) | |
|  | left out of FULL (contribution) | +9.4 (12.5) | +3.7 (9.0) | +5.0 (8.3) | -1.3 (5.2) | -2.3 (6.6) | no |
| (3) ER(20) 5m x1.5/x0.5 + causal running-max governors | alone vs as-is | +60.5 (87.0) | +43.2 (55.8) | +42.2 (49.6) | +0.5 (30.4) | +2.9 (32.4) | |
|  | left out of FULL (contribution) | +9.8 (86.2) | +23.3 (51.9) | +23.9 (46.6) | +10.3 (24.9) | +4.2 (21.9) | no |
| (4) Asia-stopped -> cut other same-side 50% | alone vs as-is | +15.3 (30.6) | +17.7 (21.8) | +14.6 (19.7) | -0.0 (11.9) | +3.5 (13.9) | |
|  | left out of FULL (contribution) | +12.1 (21.2) | +3.2 (14.2) | +0.4 (13.7) | -3.0 (7.8) | -2.0 (6.0) | no |
| (5) no-trade set (8 lines, D 20, fresh) | alone vs as-is | +39.4 (34.4) | +22.4 (29.2) | +19.4 (30.5) | +3.3 (18.9) | +7.0 (21.7) | |
|  | left out of FULL (contribution) | +25.0 (43.4) | +17.3 (31.2) | +11.3 (31.0) | +6.2 (18.9) | -0.8 (21.6) | no |
| (6) Native stops 1.28 | alone vs as-is | +9.4 (4.8) | +9.4 (4.0) | +9.1 (3.6) | +9.8 (3.7) | +7.1 (1.2) | |
|  | left out of FULL (contribution) | +9.7 (4.0) | +11.4 (6.7) | +10.7 (5.9) | +10.1 (4.3) | +6.1 (1.4) | no |

Pieces meeting the change rule: none.

## 6. What was coded, what was not, bookkeeping
* **Coded:** causal governors (a), (b), (b') plus SS's static reading and the base reading, with the exact equivalence tests above; the 8-book engine; the user's session lot tables; bases N and M (the PE confirmation kernel carries the M target cost); integer-lot split with add slippage and half-up ER lot rounding; the K6 reconciliation grid; O6 as a stand-alone weekly line.
* **Not done:** the SS QUANT-LAYER header (placebo ranks, RC / Romano-Wolf, DSR, PBO, sensitivity surface, IC) was NOT re-run for the new engine; SS's page-5 columns stand for the static reading and the differences here (running max within 1k of static at live lots) do not change them in kind; capacity at depth (PE confirm and cut seconds not joined to mbp-10); MV and PB do not appear in the split-slippage report beyond the +0.25 model; the PE "session lots 0 kills the hold" event is handled by the lot table only; the D6 rounding rule for 1-lot books.
* **Open question (MORNING.md only):** what rounding rule does D6 apply to ER-sized lots on 1-2 lot books (A6 1 x 0.5, K6 2 x 1.5)? The live delta moves from +18.5k to +22.8k L6M between fractional and half-up rounding.
* UF_TRIALS side=followup_sundaystack2 (about 190 scenario runs, n_eff 6, same composite); DECISIONS.md prereg line; pickles `out/sundaystack2/s1_<lots>_<basis>.pkl`, `loo_*.pkl`, `k6_*.pkl`, `int_*.pkl`, `o73_8_<basis>.npy`. Reproduce: `python3 -I run_s1.py <lots> <N|M>`, `run_loo.py <lots> N runmax`, `run_k6.py <lots>`, `run_int.py <lots>`, `write_final2.py`.

## 7. ADDENDUM (lead request, UF-ENTRY C10): PE NY-AM/NY-PM confirmation at market with NO split
**Page-1 line: it does NOT change the one-change-before-18:00 answer. In the full composite (causal running-max governors, Native 1.28, 8-book engine) removing the split on the confirmed PE entry changes the stack by -0.4k L6M / -0.8k HOLD / -0.1k PRE / -0.1k X' (live lots; MDE 1.1-1.9k) and 0.0k at research lots; dropping the ER multiplier on those entries as well costs -1.7k / -1.0k / -1.6k and gains +1.4k in X' (MDE 3.5-4.9k). Keep the spec as coded.**

Variants (only PE entries in nyam / nypm change; other sessions and books unchanged): coded = confirmation at market then 70/30 split, ER multiplier applied; V2 = confirmed entry is a single order of the planned size WITH the ER multiplier (no split); V1 = single order, planned size, no ER multiplier (the multiplier is set to 1 for those rows, so their governor multiplier is 1 too). Code `run_pe.py`; tie-out: the coded row equals the section-0 headline (live +18.5k L6M). Delta in $k/wk (MDE); N = Native 1.28 on basis N, LIVE-CAL = stop 2.45 on N.

| lots | basis | variant | vs as-is L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|---|---|
| live | N | coded | +19.4 (24.1) | +18.5 (17.4) | +16.2 (16.8) | +4.7 (13.4) | +12.5 (14.7) |
| live | N | V2 no split, ER | +18.0 (24.1) | +18.2 (17.6) | +15.3 (17.3) | +4.6 (13.2) | +12.4 (14.4) |
| live | N | V1 no split, no ER | +19.2 (22.2) | +16.9 (15.7) | +15.2 (15.9) | +3.1 (12.2) | +13.9 (14.2) |
| live | LIVE-CAL | coded | +17.1 (24.5) | +16.2 (17.8) | +13.9 (17.0) | +2.3 (13.5) | +10.8 (14.7) |
| live | LIVE-CAL | V2 | +15.3 (24.5) | +15.6 (17.9) | +12.9 (17.5) | +2.2 (13.3) | +10.8 (14.5) |
| live | LIVE-CAL | V1 | +16.3 (21.9) | +14.1 (15.7) | +12.6 (15.9) | +0.8 (12.3) | +12.3 (14.2) |
| research | N | coded | +95.2 (75.9) | +79.5 (50.6) | +74.9 (49.4) | +24.7 (33.1) | +12.8 (35.1) |
| research | N | V2 | +95.2 (76.1) | +79.6 (50.7) | +74.9 (49.4) | +24.7 (33.0) | +12.7 (34.9) |
| research | N | V1 | +92.9 (72.4) | +77.4 (48.7) | +73.4 (48.5) | +23.6 (32.8) | +12.0 (34.6) |
| research | LIVE-CAL | coded / V2 / V1 | +85.5 / +85.5 / +83.8 | +68.2 / +68.3 / +66.2 | +64.2 / +64.3 / +62.8 | +14.7 / +14.7 / +13.7 | +6.6 / +6.3 / +5.6 |

Leave-one-out style (variant minus coded, same engine, paired MDE in brackets), live lots, N: V2 -1.4 (2.8) L3M, -0.4 (1.6) L6M, -0.8 (1.9) HOLD, -0.1 (1.1) PRE, -0.1 (1.3) X'; V1 -0.1 (6.7), -1.7 (4.8), -1.0 (4.9), -1.6 (3.5), +1.4 (4.7). LIVE-CAL: V2 -1.9 / -0.6 / -1.0 / -0.1 / -0.1; V1 -0.8 / -2.1 / -1.3 / -1.5 / +1.4. Research lots, N: V2 0.0 in every window; V1 -2.3 / -2.2 / -1.6 / -1.1 / -0.8. (live+ with ST/WT: same signs and sizes.)
The per-planned-lot C10 gap does not reproduce as a stack gain here (reason not decomposed: P6 NY-PM live lot is 0, and the stack engine adds governors, sizer and locks); all differences are within about one paired MDE. No change.
