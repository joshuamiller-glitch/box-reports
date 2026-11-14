# DS3_ENGINE_VS_LIVE - PRIORITY 13 engine vs live (W-EV)

VERDICT (2026-11-14 18:53Z): exact-engine entries vs the live file, 2026-11-01 18:00 .. 11-11 17:00 ET (355 live entries, X books excluded, order-second stamps, +-30 s): entry match U = A/(A+B+C) is 0.645 before any fix (best of LPB / JN04RM / JN05W2: TL3_EV_JN04RM_S), 0.730 in the first week (11-01..11-06) and 0.497 in the second (11-08..11-11); chance level (engine shifted 1-3 days or 10-60 min) is 0.00-0.01; raw signals agree (353 of 357 live entries have an engine signal), so the miss is exit cascades, live-cut silence, day-cap states and panel cells, not signals. Conditional on live exits (live-drive): 0.811 (TL3_EV_LPB_D).

Shadow only, no PASS claims, nothing adopted into the shared engine. Prereg autopilot/EV_PREREG.md (sha in DECISIONS.md). Code outputs/code/th_engfix/ (evmatch.py, ev_analyze.py, ev_report.py, ev_run.py, ev_drive.py, ev_panel.py, ev_jnprep.py, build_page.py, page_gen.py); runs and logs /mnt/l2/l2vast/_engvslive/. Admission tag EV (TL3_EV_*).

## 1. Data, method, exclusions
- Live: data/live/StratTrades_DS7_<acct>.csv (sha256 4d932dd9aa51cf58..., mtime 11-13 22:05Z, 422 rows; rows with entryTime 0001-01-01 dropped), DS7.cs v1.9a (sha256 2870791f506e3c17..., ~/DS7.cs, read, not inferred), GATE0_ANSWERS_1106.md. Only 11-01 18:00 .. 11-11 17:00 ET can be matched: the NQ tape (hist day files, 1-s state days) ends 11-11 17:00 ET; the 11-11 evening .. 11-13 live rows (92 rows) are listed in the lot/panel tables but not matched (no tape).
- Engine: the exact engine (state_sizer_ijk JointRep, ROLLFIX1, TP month cache), month 202611 (first run of this month for these sets), sets LPB (= LPB_EMPTY, live panel base), JN04RM (JN04 LOT/SIGQ/REG/STACK as rules), JN05W2 (JN04RM + ctx cut + K7 flat45 + C22 + WL_E1). Engine event log captured (SKIP reasons, ENTRY, FILL, locks).
- Stamp: live entryTime (ET second) vs engine order second = floor((first fill - 1.0 s)); one-to-one, smallest |dt| first, same book and side. Classes per the order: A both, B engine took / live flat, C live took / engine flat. Dollars: B = engine net, C = live net (pnlNet), A = engine minus live. U = A/(A+B+C).
- Exclusions: X3/X4/X5 (engine has them off), outage 11-03 02:55-08:20 ET both sides. The 11-08/09 night v1.5 bug exits (H7/M7) are bug exits: they do not enter the entry match (entries kept, exits not used).
- Windows: W45 = 11-01 18:00..11-06 17:00 (live v1.4/v1.5 era), W46 = 11-08 18:00..11-11 17:00 (v1.5a..v1.9 era).
- JN input gap found: the shared jnr_cfg.json (LOT table, SIGQ monthly threshold, REG atr_rel) ends 2026-11-05 (sz_core DATAEND 20261105, nq1m_state.npz ends 11-05 16:05): in a 202611 run REG/ATR-SKIP are inactive after 11-05 16:06 and SIGQ has no threshold. Private extension (ev_jnprep.py: REG atr_rel from NQ 1-min bars built from the hist day-file prints to 11-11 21:59; SIGQ thr = the 202610 value; LOT table not extended) in /mnt/l2/l2vast/_engvslive/work/.

## 2. Match table: engine runs vs live
(30 s tolerance; ALL = 11-01 18:00..11-11 17:00)

| run             | window   | nLive   | nEng   | A   | B   | C   | U     | usdB   | usdC   |
|:----------------|:---------|:--------|:-------|:----|:----|:----|:------|:-------|:-------|
| TL3_EV_LPB_S    | ALL      | 355     | 325    | 259 | 66  | 96  | 0.615 | 19430  | 61245  |
| TL3_EV_LPB_S    | W45      | 232     | 219    | 183 | 36  | 49  | 0.683 | 16861  | 44190  |
| TL3_EV_LPB_S    | W46      | 123     | 106    | 76  | 30  | 47  | 0.497 | 2569   | 17055  |
| TL3_EV_JN04RM_S | ALL      | 355     | 341    | 273 | 68  | 82  | 0.645 | 6624   | 23075  |
| TL3_EV_JN04RM_S | W45      | 232     | 235    | 197 | 38  | 35  | 0.730 | 4056   | 6020   |
| TL3_EV_JN04RM_S | W46      | 123     | 106    | 76  | 30  | 47  | 0.497 | 2569   | 17055  |
| TL3_EV_JN05W2_S | ALL      | 355     | 277    | 220 | 57  | 135 | 0.534 | 5840   | 31210  |
| TL3_EV_JN05W2_S | W45      | 232     | 183    | 154 | 29  | 78  | 0.590 | -1122  | 14585  |
| TL3_EV_JN05W2_S | W46      | 123     | 94     | 66  | 28  | 57  | 0.437 | 6962   | 16625  |

### 2c. Conditional on live exits (live-drive diagnostic C2: book states and realised P&L driven by the live exits; engine entry logic only)

| run             | window   | nLive   | nEng   | A   | B   | C   | U     | usdB   | usdC   |
|:----------------|:---------|:--------|:-------|:----|:----|:----|:------|:-------|:-------|
| TL3_EV_LPB_D    | ALL      | 355     | 317    | 301 | 16  | 54  | 0.811 | 8346   | 17025  |
| TL3_EV_LPB_D    | W45      | 232     | 212    | 201 | 11  | 31  | 0.827 | 6075   | 22130  |
| TL3_EV_LPB_D    | W46      | 123     | 105    | 100 | 5   | 23  | 0.781 | 2271   | -5105  |
| TL3_EV_JN04RM_D | ALL      | 355     | 316    | 300 | 16  | 55  | 0.809 | 4676   | 16290  |
| TL3_EV_JN04RM_D | W45      | 232     | 211    | 200 | 11  | 32  | 0.823 | 2406   | 21395  |
| TL3_EV_JN04RM_D | W46      | 123     | 105    | 100 | 5   | 23  | 0.781 | 2271   | -5105  |

### 2d. Tolerance (ALL)

| run             | tol_s   | A   | B   | C   | U     | usdB   | usdC   |
|:----------------|:--------|:----|:----|:----|:------|:-------|:-------|
| TL3_EV_LPB_S    | 2       | 259 | 66  | 96  | 0.615 | 19430  | 61245  |
| TL3_EV_LPB_S    | 30      | 259 | 66  | 96  | 0.615 | 19430  | 61245  |
| TL3_EV_LPB_S    | 120     | 260 | 65  | 95  | 0.619 | 20147  | 60045  |
| TL3_EV_JN04RM_S | 2       | 273 | 68  | 82  | 0.645 | 6624   | 23075  |
| TL3_EV_JN04RM_S | 30      | 273 | 68  | 82  | 0.645 | 6624   | 23075  |
| TL3_EV_JN04RM_S | 120     | 274 | 67  | 81  | 0.649 | 7342   | 21875  |
| TL3_EV_JN05W2_S | 2       | 220 | 57  | 135 | 0.534 | 5840   | 31210  |
| TL3_EV_JN05W2_S | 30      | 220 | 57  | 135 | 0.534 | 5840   | 31210  |
| TL3_EV_JN05W2_S | 120     | 221 | 56  | 134 | 0.538 | 6557   | 30010  |

### 2e. Chance level (engine entry stamps shifted by whole days or minutes, same matcher, +-30 s)

| shift_s   | A   | B   | C   | U     |
|:----------|:----|:----|:----|:------|
| 86400     | 3   | 304 | 352 | 0.005 |
| 172800    | 2   | 285 | 353 | 0.003 |
| 259200    | 0   | 254 | 355 | 0.000 |
| -86400    | 3   | 295 | 352 | 0.005 |
| -172800   | 1   | 261 | 354 | 0.002 |
| -259200   | 0   | 194 | 355 | 0.000 |
| 600       | 0   | 338 | 355 | 0.000 |
| 1800      | 4   | 334 | 351 | 0.006 |
| 3600      | 6   | 337 | 349 | 0.009 |

## 3. Splits, run TL3_EV_JN04RM_S, W45 11-01..11-06

By by book (tol 30 s)

| book   | A   | B   | C   | usdB   | usdC   | U     |
|:-------|:----|:----|:----|:-------|:-------|:------|
| A7     | 22  | 2   | 10  | -1658  | -1025  | 0.647 |
| H7     | 4   | 0   | 0   | 0      | 0      | 1.000 |
| K7     | 79  | 18  | 10  | -1754  | -2450  | 0.738 |
| M7     | 29  | 6   | 7   | 2826   | -125   | 0.690 |
| O7     | 4   | 0   | 0   | 0      | 0      | 1.000 |
| P7     | 53  | 12  | 8   | 4642   | 9620   | 0.726 |
| U7     | 6   | 0   | 0   | 0      | 0      | 1.000 |

By by session (tol 30 s)

| sess   | A   | B   | C   | usdB   | usdC   | U     |
|:-------|:----|:----|:----|:-------|:-------|:------|
| asia   | 101 | 14  | 19  | -720   | 7540   | 0.754 |
| london | 65  | 12  | 6   | 4046   | -2625  | 0.783 |
| nyam   | 27  | 3   | 6   | 3596   | 1745   | 0.750 |
| nypm   | 4   | 9   | 4   | -2867  | -640   | 0.235 |

By by entry type (tol 30 s)

| typ                          | A   | B   | C   | usdB   | usdC   | U     |
|:-----------------------------|:----|:----|:----|:-------|:-------|:------|
| 1-lot single market          | 121 | 33  | 25  | 3909   | 75     | 0.676 |
| multi-lot (70/30 slices+add) | 76  | 5   | 10  | 147    | 5945   | 0.835 |

By ET hour block (tol 30 s)

| hb   | A   | B   | C   | usdB   | usdC   | U     |
|:-----|:----|:----|:----|:-------|:-------|:------|
| 00h  | 39  | 6   | 6   | -1463  | -2585  | 0.765 |
| 03h  | 28  | 2   | 2   | -1969  | 560    | 0.875 |
| 06h  | 21  | 6   | 4   | 5052   | -3185  | 0.677 |
| 09h  | 27  | 3   | 6   | 3596   | 1745   | 0.750 |
| 12h  | 4   | 9   | 4   | -2867  | -640   | 0.235 |
| 18h  | 46  | 6   | 6   | 2311   | 11075  | 0.793 |
| 21h  | 32  | 6   | 7   | -605   | -950   | 0.711 |

Matched pairs: lots relation (live qty vs engine lots) and entry price (engine minus live, adverse-signed pts)

| rel        | n   | med_dt   | mean_adverse_pts   |
|:-----------|:----|:---------|:-------------------|
| equal      | 140 | 0.0      | 0.40               |
| live fewer | 3   | 0.0      | -2.50              |
| live more  | 54  | 0.0      | 1.69               |

Mismatch causes (side B = engine took / live flat, C = live took / engine flat; usd = engine net for B, live net for C)

| side   | cause                                                                   | n   | usd   |
|:-------|:------------------------------------------------------------------------|:----|:------|
| B      | LIVE book lock fired earlier that day (BookLock exit)                   | 3   | 1455  |
| B      | LIVE flat, no live entry (gate/signal unknown)                          | 16  | -5260 |
| B      | LIVE reconnect/stall window                                             | 4   | 4795  |
| B      | LIVE-HELD (exit cascade)                                                | 15  | 3065  |
| C      | ENGINE give-back lock: engine P&L path only (live book had not crossed) | 5   | -1555 |
| C      | ENGINE loss cap: engine P&L path only (live book had not crossed)       | 1   | -4400 |
| C      | ENGINE loss cap: live book had ALSO crossed it (live kept entering)     | 1   | -1695 |
| C      | ENGINE no signal                                                        | 3   | -1935 |
| C      | ENGINE profit cap: engine P&L path only (live book had not crossed)     | 7   | 1105  |
| C      | ENGINE-HELD (exit cascade)                                              | 18  | 14500 |

## 3. Splits, run TL3_EV_JN04RM_S, W46 11-08..11-11

By by book (tol 30 s)

| book   | A   | B   | C   | usdB   | usdC   | U     |
|:-------|:----|:----|:----|:-------|:-------|:------|
| A7     | 6   | 4   | 0   | 2797   | 0      | 0.600 |
| H7     | 6   | 0   | 2   | 0      | 3600   | 0.750 |
| K7     | 21  | 13  | 15  | -1728  | 12820  | 0.429 |
| M7     | 22  | 6   | 12  | -469   | 11995  | 0.550 |
| P7     | 14  | 5   | 18  | 842    | -11360 | 0.378 |
| U7     | 7   | 0   | 0   | 0      | 0      | 1.000 |
| O7     | 0   | 2   | 0   | 1127   | 0      | 0.000 |

By by session (tol 30 s)

| sess   | A   | B   | C   | usdB   | usdC   | U     |
|:-------|:----|:----|:----|:-------|:-------|:------|
| asia   | 47  | 11  | 21  | 9122   | 5580   | 0.595 |
| london | 25  | 14  | 17  | -9456  | 975    | 0.446 |
| nyam   | 4   | 5   | 4   | 2902   | 5825   | 0.308 |
| nypm   | 0   | 0   | 5   | 0      | 4675   | 0.000 |

By by entry type (tol 30 s)

| typ                          | A   | B   | C   | usdB   | usdC   | U     |
|:-----------------------------|:----|:----|:----|:-------|:-------|:------|
| 1-lot single market          | 42  | 24  | 25  | 2291   | 10130  | 0.462 |
| multi-lot (70/30 slices+add) | 34  | 6   | 22  | 278    | 6925   | 0.548 |

By ET hour block (tol 30 s)

| hb   | A   | B   | C   | usdB   | usdC   | U     |
|:-----|:----|:----|:----|:-------|:-------|:------|
| 00h  | 10  | 5   | 8   | -8     | -5615  | 0.435 |
| 03h  | 15  | 6   | 9   | -2736  | 3750   | 0.500 |
| 06h  | 6   | 7   | 5   | -5483  | 3100   | 0.333 |
| 09h  | 4   | 5   | 4   | 2902   | 5825   | 0.308 |
| 18h  | 28  | 3   | 10  | -1697  | 1245   | 0.683 |
| 21h  | 13  | 4   | 6   | 9591   | 4075   | 0.565 |
| 12h  | 0   | 0   | 5   | 0      | 4675   | 0.000 |

Matched pairs: lots relation (live qty vs engine lots) and entry price (engine minus live, adverse-signed pts)

| rel        | n   | med_dt   | mean_adverse_pts   |
|:-----------|:----|:---------|:-------------------|
| equal      | 74  | 0.0      | 0.23               |
| live fewer | 1   | 0.0      | -0.44              |
| live more  | 1   | 0.0      | 4.38               |

Mismatch causes (side B = engine took / live flat, C = live took / engine flat; usd = engine net for B, live net for C)

| side   | cause                                                               | n   | usd   |
|:-------|:--------------------------------------------------------------------|:----|:------|
| B      | LIVE JN04 P7 post-stop blackout                                     | 1   | 4790  |
| B      | LIVE book lock fired earlier that day (BookLock exit)               | 4   | 2797  |
| B      | LIVE flat, no live entry (gate/signal unknown)                      | 7   | 3224  |
| B      | LIVE-HELD (exit cascade)                                            | 18  | -8242 |
| C      | ENGINE loss cap: engine P&L path only (live book had not crossed)   | 17  | -3400 |
| C      | ENGINE loss cap: live book had ALSO crossed it (live kept entering) | 5   | -1330 |
| C      | ENGINE no signal                                                    | 1   | 1085  |
| C      | ENGINE session lots 0                                               | 8   | 12395 |
| C      | ENGINE-HELD (exit cascade)                                          | 16  | 8305  |

## 4. Root causes of the mismatch (class counts and dollars)
### 4a. Unconditional, run TL3_EV_JN04RM_S (ALL)

| side   | cause                                                                   | n   | usd   |
|:-------|:------------------------------------------------------------------------|:----|:------|
| B      | LIVE JN04 P7 post-stop blackout                                         | 1   | 4790  |
| B      | LIVE O7 not trading (no live O7 entry since 11-06)                      | 2   | 1127  |
| B      | LIVE book lock fired earlier that day (BookLock exit)                   | 7   | 4252  |
| B      | LIVE flat, no live entry (gate/signal unknown)                          | 21  | -3162 |
| B      | LIVE reconnect/stall window                                             | 4   | 4795  |
| B      | LIVE-HELD (exit cascade)                                                | 33  | -5178 |
| C      | ENGINE give-back lock: engine P&L path only (live book had not crossed) | 5   | -1555 |
| C      | ENGINE loss cap: engine P&L path only (live book had not crossed)       | 18  | -7800 |
| C      | ENGINE loss cap: live book had ALSO crossed it (live kept entering)     | 6   | -3025 |
| C      | ENGINE no signal                                                        | 4   | -850  |
| C      | ENGINE profit cap: engine P&L path only (live book had not crossed)     | 7   | 1105  |
| C      | ENGINE session lots 0                                                   | 8   | 12395 |
| C      | ENGINE-HELD (exit cascade)                                              | 34  | 22805 |

### 4b. Unconditional with the panel timeline, run TL3_EV_LPBP (ALL)

| side   | cause                                                                   | n   | usd   |
|:-------|:------------------------------------------------------------------------|:----|:------|
| B      | LIVE JN04 P7 post-stop blackout                                         | 1   | 4790  |
| B      | LIVE O7 not trading (no live O7 entry since 11-06)                      | 2   | 1127  |
| B      | LIVE book lock fired earlier that day (BookLock exit)                   | 7   | 10070 |
| B      | LIVE day-loss cap reached                                               | 11  | -5626 |
| B      | LIVE flat, no live entry (gate/signal unknown)                          | 19  | -3755 |
| B      | LIVE reconnect/stall window                                             | 3   | 7188  |
| B      | LIVE-HELD (exit cascade)                                                | 36  | 1450  |
| C      | ENGINE give-back lock: engine P&L path only (live book had not crossed) | 6   | 2050  |
| C      | ENGINE loss cap: engine P&L path only (live book had not crossed)       | 10  | 10515 |
| C      | ENGINE loss cap: live book had ALSO crossed it (live kept entering)     | 5   | -1330 |
| C      | ENGINE no signal                                                        | 5   | 740   |
| C      | ENGINE profit cap: engine P&L path only (live book had not crossed)     | 7   | 1105  |
| C      | ENGINE-HELD (exit cascade)                                              | 42  | 18880 |

### 4c. Conditional on live exits (live-drive), run TL3_EV_JN04RM_D (ALL): what remains after the exit cascade is removed

| side   | cause                                                                   | n   | usd   |
|:-------|:------------------------------------------------------------------------|:----|:------|
| B      | LIVE JN04 P7 post-stop blackout                                         | 1   | -5    |
| B      | LIVE O7 not trading (no live O7 entry since 11-06)                      | 2   | 1078  |
| B      | LIVE flat, no live entry (gate/signal unknown)                          | 9   | -1192 |
| B      | LIVE reconnect/stall window                                             | 4   | 4795  |
| C      | ENGINE give-back lock: engine P&L path only (live book had not crossed) | 9   | 8860  |
| C      | ENGINE loss cap: engine P&L path only (live book had not crossed)       | 28  | -1205 |
| C      | ENGINE loss cap: live book had ALSO crossed it (live kept entering)     | 6   | -3025 |
| C      | ENGINE no signal                                                        | 4   | -735  |
| C      | ENGINE session lots 0                                                   | 8   | 12395 |

### 4d. Live-drive with panel timeline, run TL3_EV_LPBP_D (ALL)

| side   | cause                                                                   | n   | usd   |
|:-------|:------------------------------------------------------------------------|:----|:------|
| B      | LIVE JN04 P7 post-stop blackout                                         | 1   | -5    |
| B      | LIVE O7 not trading (no live O7 entry since 11-06)                      | 2   | 1078  |
| B      | LIVE book lock fired earlier that day (BookLock exit)                   | 4   | -1335 |
| B      | LIVE flat, no live entry (gate/signal unknown)                          | 9   | -4940 |
| B      | LIVE reconnect/stall window                                             | 4   | 11988 |
| C      | ENGINE give-back lock: engine P&L path only (live book had not crossed) | 9   | 8860  |
| C      | ENGINE loss cap: engine P&L path only (live book had not crossed)       | 3   | 3515  |
| C      | ENGINE loss cap: live book had ALSO crossed it (live kept entering)     | 5   | -1330 |
| C      | ENGINE no signal                                                        | 3   | 0     |

## 5. DS7.cs v1.9a against the engine, rule by rule (live evidence from the 11-01..11-13 live file)
| rule | DS7.cs | engine | live evidence | status |
|--|--|--|--|--|
| session clock | SessionIndex L3240 | replica/common.py session_index | identical code; live entries sit in the expected session tables | OK |
| blocks 09:00-09:59, 15:00-17:59, 18:00-18:04 | TradingBlockedAt L4233, guards L450 | sim.GUARDS L32, blocked_at L193 | 0 live entries in 15:00-17:59 / 18:00-18:04; 4 live entries 09:41-09:43 are O7 (IgnoreTimeBlock) | OK |
| one position per book (EntriesPerDirection 1) | TryEntry L816 InTrade | try_entry L224 | 0 overlapping live trades in any book | OK |
| day loss / profit caps, give-back lock, week floor | CheckLimits L4071, CheckBookLock L4031 (R = BaseQty x SizeMult x stop x $20) | check_limits L722, check_book_lock L731 | K7 on label day 11-06 stopped entering exactly after -$4,805 at 08:30 (cap 4,800); 0 live entries after a profit cap or give-back crossing; CORRECTED (user, 11-14). Code check: live v1.9a defaults are the engine values x1.75 for every cap (K7 21,000/8,400 vs sim.DAYCAP 12,000/4,800; M7 same; U7 42,000/16,800 vs 24,000/9,600; P7 73,500/14,700 vs 42,000/8,400; H7 42,000/16,800 vs 24,000/9,600; A7 10,500/4,200 vs 6,000/2,400) and the book lots x1.75 (K7 4 vs 2, M7 4/2, U7 7/4, P7 12/7, H7 7/4, A7 2/1), and BookR uses BaseQty, so locks scale too: in engine units the caps ARE the live caps of the user-lot build. LPB_EMPTY (= LPB_BASE), JN04RM, JN05W2, JN05W2J were scored in engine units with P7 8,400 (p7_daycap [42000, 8400] in their set files) = live 14,700; the other books at the sim.DAYCAP box values = live x1/1.75. S1b-COMB / RB_COMB-type bases used P7 16,800 engine units = 29,400 live: flagged. BUT live ran box-scale lots until 11-11 (P7 qty 7/4, 6 on 11-11; user lots first appear 11-12) with the x1.75 caps already in force, so for 11-01..11-11 the engine caps are 1.75x too tight in live dollars. Evidence (live dollars): P7 11-11 -13,865 after two stops then a third entry, ended -20,285 and halted (cap 14,700); M7 -5,360 on 11-10 kept entering (cap 8,400, not 4,800); against the coded live caps only 6 entries follow a crossing in 11 days (P7 11-10 5 entries after -17.8k, -$1.3k, unexplained; P7 11-06 1). The earlier claim that live ignored the P7/M7 caps is WITHDRAWN (it compared live dollars to engine-unit caps). | Engine = code; the 11-01..11-11 Nov replays use the live-dollar caps (TL3_EV_*_LC); the 43-month history needs no cap change |
| U7 same-side 30-min blackout after a cut | L1856 | sim.blackout_until L54/L231 | 0 live U7 same-side entries inside 30 min of a cut | OK |
| JN04 post-stop/cut blackout (P7) | JnOnClosed L2012, JnBlackout L2156 | NOT in JN04RM / JN05W2 / LPB references | 19 live P7 same-side re-entries within 30 min of a P7 stop/cut, the last on 11-10 03:48; none after | MISSING in the engine references, live from about 11-10 |
| ATR-SKIP (P7 atr_rel >= 1.6) | Jn04Size L1967 | NOT in the references (ATRSKIP_P7 is a separate set) | live P7 entered at atr_rel 2-3 on 11-04 and 11-08/09 (REG halves the lots, no skip); none above 1.6 after 11-10 | MISSING in the references, Shadow before ~11-10 |
| LOT / SIGQ / REG sizing | Jn04Size | jnrule layers | live P7 qty in W45 is 4/7 (no layers); engine JN04RM gives 1/2: layers not live in W45 | timeline |
| STACK cap | Jn04Stack L1999: 10 lots London (user-lot build) | cap 6 (box lots) | scale-consistent (x1.75) | OK |
| v1.9 DAY-DONE (C22), EVIDENCE, BREADTH, ctx cut | V9Gate L2090, DayDoneLossDollars 4,200 | scr_hooks conj gate with R = $1,200 x -2 = -$2,400 | 79 live entries after >=22 closes with day <= -$4,200 (through 11-13 14:06): not firing live. Engine threshold -$2,400 vs source 4,200 | JN05W2 is not what was live |
| P7 45-s confirm | CfOnSubBar, ConfirmSessionsA L497 | cf_hold L284, on_45s | entry seconds :15/:30/:45 match to the second (P7 pairs dt median 0) | OK |
| L2-gated 70/30 and add | L2Arm L1519 | l2arm L333 | 80 multi-lot pairs: 49 equal fills, 6 one-sided add, 5 add-timing, 20 live more (P7 W45 layers) | add timing only |
| H7 on 5-min buckets (StackHm5Repl) | L762 | hm5 bucket | H7 pairs 10 of 12; the 2 misses are a live-only session cell (london) | OK |
| A7 PB7 asia, K7 StopJoin | books L597 | a6, JOIN_BOOKS | A7 28 A / 9 B / 10 C, exit-cascade driven; StopJoin names appear on both sides | OK |
| NT8 stall / reconnect | - | OUT1/OUT2 | live silent 11-03 02:55-08:20 and 19:19-19:52; engine entries there are excluded | excluded |
| O7 | O7 time exit, IgnoreTimeBlock | o6 | live O7 traded 11-03..11-06 only; engine takes O7 on 11-09, 11-10 | live O7 not trading since 11-06 |
| panel cells | K7/M7/U7/P7/H7/A7 Sessions L469 | sim.SESS | live traded M7 asia/nypm (11-10 12:26 .. 11-11 00:51) and H7 london (11-11 03:10, 05:15) where the box table says 0; P7 london/nyam 7 lots until ~11-09, 4 after | panel timeline (ev_panel.py) |
| live state cut | ManagePolicyState L1707 | state-base kernel | cut silent in whole sessions: label 11-09 K7 0 of 3 engine cuts, P7 0 of 4, U7 0 of 4; 11-11 K7 0 of 5; 11-12 P7 0 of 3 | live-side (W-LB2 owns) |

## 6. Findings, in order of size
1. Raw signals are right: 353 of 357 live entries have an engine signal of the same book; the 4 without are K7 11-02 10:36 (Keltner band path), U7 and M7 11-03 08:20 (reconnect edge) and M7 11-05 08:01 (vote timing). Placebo U is 0.00-0.01.
2. Exit cascades are the largest class: 45 roots (exit class or time differs) produce 91 of the 150 B+C mismatches (61 %) in the unconditional JN04RM run. Roots: live cut vs engine cut at another second (13 roots, 26 descendants), live target vs engine cut (9), live cut vs engine target (8), target-target with a different second (4), live stop vs engine cut (6), live lock vs engine cut (2). Live cut silence (section 5) is the main source of engine-cut-vs-live-target and live-stop-vs-engine-cut roots.
3. Conditional on the live exits (live-drive), U is 0.81 (A 300, B 16, C 55): exit cascades explain about 0.17 of the 0.19 gap to 1. What remains: engine loss-cap halts the live P7/M7 did not obey (34 C), engine give-back lock from the engine's own P&L path (9), live-only panel cells (8, +$12.4k), no engine signal (4).
4. Day caps and locks: engine = code, and in engine units equal to live for the user-lot build. For the box-lot weeks 11-01..11-11 live caps in live dollars are 1.75x the engine's (see section 5), which explains part of the 'engine dayHalt' class; the unit mix-up in my first version (live dollars against engine caps) is corrected and the 'live did not obey the cap' finding is withdrawn. Residual: 5 P7 entries on label day 11-10 after -$17.8k (cap 14,700), -$1.3k.
5. Reference sets are not the live strategy: no engine reference contains ATR-SKIP or the P7 post-stop blackout (live from ~11-10); JN04 sizing layers were not live in W45; the v1.9 survivors in JN05W2 (C22, ctx cut, K7 flat45, WL_E1) show no sign of being live through 11-13 (C22: 79 entries inside its own trigger). JN05W2 matches live worse (U 0.53) than LPB (0.61) or JN04RM (0.65).
6. Engine input gap (data, not logic): JN-layer artefacts end 11-05; fixed in a private copy through 11-11.
7. Fill drift, equal-lot pairs: engine entry worse than live by 0.34 pt on average (median 0, p90 1.4 pt), K7 0.35, M7 0.38, P7 0.34.

## 8. The engine copy (code/th_engfix/, shared engine files untouched)
- ev_panel.py (make_rep hook): per-book session-lot timeline, per-book day-cap timeline, state-cut-cell timeline, JN04 ATR-SKIP and post-stop blackout as in DS7.cs. With par = {} it is a no-op: regression below.
- ev_drive.py: live-drive mixin (diagnostic C2).  ev_jnprep.py: private JN input extension to 11-11.  build_1113.py: separate price-store extension (11-12, 11-13) at /mnt/l2/l2vast/_engvslive/store_1113/ (days_root, std_root; shared stores untouched; the 1-s state days 11-10/11-11 rebuilt there are bit-identical to the shared ones). ev_run.py: run wrapper (EV_DAYS/EV_STD for the separate store, EV_DRIVE for the diagnostic).
- Diff: no edit to any shared engine file (replica/sim.py, th_redo/state_base_b.py, th_sz_ijk/state_sizer_ijk.py, hist_pipe): the fixes are additive subclasses in th_engfix/ev_panel.py and the matcher convention (order second, not signal second, +0.02 U).


## 7. Which earlier results move by more than 10 % (stage 1: L6M 202605-202610 and HOLD 202511-202604; ref = stored month results, fix = engine copy)
L6 = ATR-SKIP (P7, atr_rel >= 1.6) + P7 post-stop/cut 30-min same-side blackout as in DS7.cs v1.9a Live.

| fix   | ref       | window   | months   | net_wk_ref   | net_wk_fix   | net_wk_chg%   | maxDD_ref   | maxDD_fix   | maxDD_chg%   | worst_wk_chg%   | stops_wk_ref   | stops_wk_fix   | stops_wk_chg%   | moves>10%   |
|:------|:----------|:---------|:---------|:-------------|:-------------|:--------------|:------------|:------------|:-------------|:----------------|:---------------|:---------------|:----------------|:------------|
| L6    | LPB_EMPTY | L6M      | 6        | 17431        | 21830        | 25.2          | 104473      | 90474       | -13.4        | -25.6           | 23.2           | 23.1           | -0.5            | True        |
| L6    | JN04RM    | L6M      | 6        | 17544        | 17433        | -0.6          | 57823       | 57200       | -1.1         | -33.1           | 23.7           | 23.4           | -1.6            | True        |
| L6    | JN05W2    | L6M      | 6        | 24470        | 20189        | -17.5         | 52233       | 42536       | -18.6        | -64.6           | 10.7           | 10.5           | -1.7            | True        |
| L6    | JN05W2J   | L6M      | 6        | 20625        | 19007        | -7.8          | 32335       | 46786       | 44.7         | -46.5           | 10.4           | 10.5           | 1.1             | True        |
| L6    | WL_E1     | L6M      | 6        | 16511        | 21241        | 28.6          | 106084      | 92872       | -12.5        | -29.4           | 23.3           | 23.1           | -0.6            | True        |
| L6    | WG_E1     | L6M      | 6        | 17294        | 17407        | 0.7           | 60220       | 58718       | -2.5         | -35.9           | 23.7           | 23.4           | -1.3            | True        |

### 8b. Identity-style regression, 3 reference months (LPB_EMPTY stored result of record vs engine copy)
```
202608: patch OFF vs stored LPB_EMPTY: IDENTICAL (677 trades, net 70353.96 vs 70353.96)
   patch ON (P7 cap 16,800: illustration of the hook only, NOT a fix: engine-unit cap 8,400 = live 14,700): trades 677 -> 700, net 70354 -> 57978; trades only in stored 0 (net 0), only in fixed 23 (net -12376); books of changed trades {'P7': np.int64(23)}
202609: patch OFF vs stored LPB_EMPTY: IDENTICAL (678 trades, net 127125.82 vs 127125.82)
   patch ON (P7 cap 16,800: illustration of the hook only, NOT a fix: engine-unit cap 8,400 = live 14,700): trades 678 -> 714, net 127126 -> 138788; trades only in stored 0 (net 0), only in fixed 36 (net 11662); books of changed trades {'P7': np.int64(36)}
202610: patch OFF vs stored LPB_EMPTY: IDENTICAL (769 trades, net 12236.22 vs 12236.22)
   patch ON (P7 cap 16,800: illustration of the hook only, NOT a fix: engine-unit cap 8,400 = live 14,700): trades 769 -> 864, net 12236 -> 47080; trades only in stored 0 (net 0), only in fixed 95 (net 34843); books of changed trades {'P7': np.int64(95)}
```
