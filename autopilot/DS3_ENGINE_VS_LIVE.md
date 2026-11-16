# DS3_ENGINE_VS_LIVE - PRIORITY 13 engine vs live (W-EV)

LOT BASIS (lead, 11-14): JN05W2-family sets are at BASE (box) lots; live is x1.75 in the user-lot build; raw engine net_fee charges $1.18/contract RT (not the $4.84 of FEES.md) with the engine own fills; live fills carry the actual NT fees.

Basis of every dollar figure on this page: (a) usdB, usdC, the "mismatch causes" dollars and the live-vs-engine total P&L compare LIVE dollars (actual NT commissions) with ENGINE base-lot dollars (fee $1.18/contract). For the matched window 11-01..11-11 live ran box-scale lots (P7 qty 7/4, K7 1-2, etc.; the x1.75 user lots first appear 11-12), so these two sides are on the SAME lot scale: no x1.75 factor is applied or needed, and the only dollar bias is the fee difference (about $3.7 per contract RT, engine more favourable) plus fill drift. (b) Day-cap and give-back tests use LIVE dollars against caps converted to live dollars for the box-lot weeks (section 5). (c) Section 7 (re-score) compares engine with engine: stored reference month results vs the engine-copy runs, both base-lot dollars, both at the $1.18 fee: no lot or fee mismatch inside that table; multiply by 1.75 for user-lot dollars. (d) Entry-match counts (A/B/C, U) contain no dollars and no lot or fee dependence.

VERDICT (data ends 2026-11-13; 2026-11-16 01:48Z): exact-engine entries vs the live file, 2026-11-01 18:00 .. 11-11 17:00 ET (355 live entries, X books excluded, order-second stamps, +-30 s): entry match U = A/(A+B+C) is 0.645 before any fix (best of LPB / JN04RM / JN05W2: TL3_EV_JN04RM_S), 0.730 in the first week (11-01..11-06) and 0.497 in the second (11-08..11-11); chance level (engine shifted 1-3 days or 10-60 min) is 0.00-0.01; raw signals agree (353 of 357 live entries have an engine signal), so the miss is exit cascades, live-cut silence, day-cap states and panel cells, not signals. AFTER the panel-timeline fix (TL3_EV_LPBP_LC): ALL 0.675, W45 0.742, W46 0.567. Conditional on live exits (live-drive): 0.811 (TL3_EV_LPB_D).

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

### 2b. Same, with the panel timeline of the live strategy put in the engine (ev_panel.py: P7 sessions 7,7,0,7 -> 7,4,0,4 on 11-09 12:00Z, P7 cut v2 45/5x/w5/p10 -> 40/5x/w5/p3 on 11-09 20:30Z, all day caps at the live v1.9a coded values (K7 8,400, M7 8,400, U7 16,800, P7 14,700, H7 16,800, A7 4,200; user correction 11-14) instead of the engine box values (4,800 / 4,800 / 9,600 / P7 8,400 / 9,600 / 2,400), M7 asia/nypm and H7 london cells open 11-10 17:00Z..11-11 11:00Z as live traded them; JN04L adds ATR-SKIP and the P7 post-stop blackout from 11-10 09:00Z)

| run                 | window   | nLive   | nEng   | A   | B   | C   | U     | usdB   | usdC   |
|:--------------------|:---------|:--------|:-------|:----|:----|:----|:------|:-------|:-------|
| TL3_EV_LC_LPB_EMPTY | ALL      | 355     | 376    | 278 | 98  | 77  | 0.614 | 12414  | 63285  |
| TL3_EV_LC_LPB_EMPTY | W45      | 232     | 250    | 192 | 58  | 40  | 0.662 | 14998  | 49180  |
| TL3_EV_LC_LPB_EMPTY | W46      | 123     | 126    | 86  | 40  | 37  | 0.528 | -2584  | 14105  |
| TL3_EV_LC_JN04RM    | ALL      | 355     | 392    | 292 | 100 | 63  | 0.642 | -392   | 25115  |
| TL3_EV_LC_JN04RM    | W45      | 232     | 266    | 206 | 60  | 26  | 0.705 | 2192   | 11010  |
| TL3_EV_LC_JN04RM    | W46      | 123     | 126    | 86  | 40  | 37  | 0.528 | -2584  | 14105  |
| TL3_EV_LC_JN05W2    | ALL      | 355     | 305    | 234 | 71  | 121 | 0.549 | 15469  | 40580  |
| TL3_EV_LC_JN05W2    | W45      | 232     | 211    | 168 | 43  | 64  | 0.611 | 6194   | 18020  |
| TL3_EV_LC_JN05W2    | W46      | 123     | 94     | 66  | 28  | 57  | 0.437 | 9275   | 22560  |
| TL3_EV_LPBP_LC      | ALL      | 355     | 367    | 291 | 76  | 64  | 0.675 | 14131  | 18915  |
| TL3_EV_LPBP_LC      | W45      | 232     | 233    | 198 | 35  | 34  | 0.742 | 12764  | 17940  |
| TL3_EV_LPBP_LC      | W46      | 123     | 134    | 93  | 41  | 30  | 0.567 | 1366   | 975    |
| TL3_EV_JN04L_LC     | ALL      | 355     | 410    | 300 | 110 | 55  | 0.645 | 22558  | 17235  |
| TL3_EV_JN04L_LC     | W45      | 232     | 260    | 203 | 57  | 29  | 0.702 | 380    | 3705   |
| TL3_EV_JN04L_LC     | W46      | 123     | 150    | 97  | 53  | 26  | 0.551 | 22177  | 13530  |

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
| JN04 post-stop/cut blackout (P7) | JnOnClosed L2012, JnBlackout L2156 | NOT in JN04RM / JN05W2 / LPB references | 19 live P7 same-side re-entries within 30 min of a P7 stop/cut up to 11-10 03:48; 0 after (through 11-13 14:50) | live from ~11-10 (consistent with zero violations); MISSING in the references |
| ATR-SKIP (P7 atr_rel >= 1.6) | Jn04Size L1967 | NOT in the references (ATRSKIP_P7 is a separate set) | live P7 entered at atr_rel 2.81 on 11-13 11:18 (7 lots) and 1.63 on 11-11 19:11 (6 lots), and at 2-3 on 11-04 and 11-08/09: NOT firing live through 11-13 (Shadow, or a different input) | NOT live; the extended-store replays drop it |
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


## 10. User answer 11-16: all four layers LIVE. Does the engine base match the live list? (differences with dollars on the label week 11-08 18:00 .. 11-13 17:00)
Engine sets compared: NY_A = JN05W2 as scored in the research (LPB + ctx cut F3 + governor E1 + DAY-DONE C22 + BR3S + K7 flat 45 + JN04 LOT/SIGQ/REG rules) with the panel timeline and caps; NY_B = A plus the JN04 STACK cap (the cde key); NY_C = B plus the P7 post-stop/cut blackout; NY_D = C plus ATR-SKIP. All on the extended store ev1113b, BREADTH bars extended to the 11-13 close (the shared bars_<I>.npz ended 11-10 07:59Z; private copy, prefix identical). Dollars: base-lot engine, $4.84 fee, x1.75 beside; live actual -$26.5k (45 full stops).

| live layer (user list) | live spec | engine base JN05W2 | match | note |
|--|--|--|--|--|
| Governor WL_E1 (NEW EVIDENCE) | Live, P7, skip after 2 same-side losers without a new session extreme; no session list in the property; session key = label day x 6-session clock | c_gov rule gov: loss_same_ge 2 and noevid 1, sess [0,1,3,4], P7 only, history by session key of the signal | YES in effect | the engine list excludes sessions 2 (pre) and 5 (close), but P7's lot table is 0 in both, so nothing is traded there; extreme definition: engine 1-min bar highs/lows, live bar highs/lows and the current price; opposite-side entry resets the run in both |
| ATR-SKIP | Live, P7, atr_rel >= 1.6 (5-min ATR(14) Wilder vs median of the previous 20 dates' daily medians, >= 5 dates) | NOT in JN05W2/JN04RM/LPB; restored in NY_D | restored | definition identical to fgh_feat.bar_features (checked against DS7.cs JnClose5m/JnAtrRel L1914-1938); live behaviour: see section 11 |
| DAY-DONE C22 | Live, >= 22 closed trades today (all books) AND day loss >= $4,200 | scr_hooks conj: n >= 22 and day P&L <= -2 x $1,200 = -$2,400 engine dollars (= $4,200 / 1.75), closes counted by exit label day over all books | YES in the user-lot build (x1.75 lots); in the box-lot weeks 11-01..11-11 live dollars are 1.0x the engine, so the equivalent live threshold would have been $2,400 | live closes counted per session roll (IsFirstBarOfSession), engine per 18:00 ET label day; X-book shadow closes count live, not in the engine (7 rows) |
| Stack cut 50% | Live, Asia only (StackAsiaOnly) | sim.stack_on_stop: entry_session != 0 -> 'Asia-only, no cut'; 50% ceil of the other same-side books; trigger = exit name with Stop and not StackCut | YES | identical code path |
| Jn04 stack cap 10 lots, London only | Live (sessions 0,1,0,0,0,0) | JN05W2 has NO cde key = no STACK cap. JN04RM and JN05W2J DO (cde code 8, cap 6 engine lots = 10 live lots, London). The live-matching base is JN05W2J (JN04RM base), not JN05W2 | NO for JN05W2 | effect on the label week: see the table below (B minus A) |
| NTZ half within 20 pts | Live | all bases (Q1-A live panel base) | YES | |
| BREADTH P7 15 min | Live, 3-of-3 new session extreme within 15 min -> skip | JN05W2 igate breadth_ext15 == 3, P7 | YES in rule; inputs: NQ/ES/RTY 1-min bars in /mnt/l2/l2vast/_th_works/i ended 11-10 07:59Z (BREADTH silently inactive after that in every engine run), extended here | any JN05W2-family November result outside this page ran BR3S blind after 11-10 07:59Z |
| Post-exit blackout P7 30 min | Live (stop or cut, same side) | NOT in JN05W2/JN04RM/LPB; added in NY_C | added | live shows 0 violations after 11-10 03:48 |
| NKD take P7,U7 at 0.80 | Live | NOT in the engine (needs NKD top of book; first-order only on the box) | NO | no exact effect can be given from owned data |
| JN04 LOT/SIGQ/REG on P7 | Live | jnrule: LOT table ends 11-05 (not extended), SIGQ threshold 202611 = the 202610 value, REG real to 11-13 | PARTLY | live LOT needs 10 label days of its own P7 records (jnFirstPerfDay), so LOT cannot have gated before about 11-23 if the records started on installation |

### Dollar effect of each difference, label week (engine, base-lot dollars at $4.84 fee, x1.75 beside)

| set                                                                                  | trades   | full_stops   | week_net_4p84_base   | week_net_x1p75   | delta_vs_previous_base   | U_all   | U_label_week   |
|:-------------------------------------------------------------------------------------|:---------|:-------------|:---------------------|:-----------------|:-------------------------|:--------|:---------------|
| A: JN05W2 as scored (no STACK cap, no blackout, no ATR-SKIP) + panel timeline + caps | 165      | 8            | -6943                | -12150           |                          | 0.486   | 0.407          |
| B: A + JN04 STACK cap (cde; JN05W2J base)                                            | 194      | 7            | 4133                 | 7233             | 11076                    | 0.537   | 0.466          |
| C: B + P7 post-stop/cut blackout 30 min (from 11-10 09:00Z)                          | 189      | 7            | -3476                | -6083            | -7609                    | 0.539   | 0.470          |
| D: C + ATR-SKIP P7 atr_rel>=1.6 restored = full live list in the engine              | 183      | 8            | 7977                 | 13959            | 11452                    | 0.490   | 0.457          |

Reading: adding the STACK cap moves the week by +$11.1k base (+$19.4k x1.75), the blackout by -$7.6k, restoring ATR-SKIP by +$11.5k. With the whole live list in the engine (NY_D) the label week is +$8.0k base (+$14.0k x1.75) against live -$26.5k, 183 trades against 177 live, and the entry match FALLS (0.490 all, 0.457 label week) when ATR-SKIP is restored: the live record does not look like an ATR-SKIP world (section 11). The JN05W2-family layers (governor, C22, ctx cut, BR3S) cut the engine's trade count to 165-194 for the week, close to the live 177; they are why the family matches live entries less well (0.49-0.54) than the plain panel-timeline base NX_D (0.594) while having the right number of trades.

## 11. ATR-SKIP on the live record: every P7 entry/signal with atr_rel >= 1.6 (2026-10-01..11-13), for checking against the Output log
atr5 = Wilder ATR(14) of 5-min NQ bars at the last closed bar, base = median over the previous 20 trading dates (>= 5) of the daily medians of atr5, atr_rel = atr5/base (the engine's computation, same as DS7.cs JnAtrRel). LIVE rows are real P7 entries; ENGINE rows are P7 signals of the engine run (October: LPB_EMPTY; November: NX_D).
- Of 101 live P7 entries from 11-01, 40 had atr_rel >= 1.6. By label day (entries / with atr_rel >= 1.6 / max): 11-02 10/3/1.74, 11-03 8/4/2.23, 11-04 19/15/3.20, 11-05 16/5/4.60, 11-06 8/8/3.55, 11-09 4/3/2.32, 11-10 16/0/1.30, 11-11 12/0/1.55 (but one at 1.63 on 11-11 19:11), 11-12 3/1/1.63, 11-13 5/1/2.81.
- After the ATR-SKIP "Live" date the two live P7 entries at atr_rel >= 1.6 to check in the Output log are: 2026-11-11 19:11:00 (6 lots, atr5 50.95 / base 31.34 = 1.63) and 2026-11-13 11:18:45 (7 lots, atr5 87.93 / base 31.34 = 2.81; this trade lost 67 pts at 11:26 on a gap move). If ATR-SKIP was Live on those seconds the log must show an 'ATR-SKIP: ... -> signal SKIPPED' line; if it shows nothing, jnDailyMed had fewer than 5 dates or jnAtr was NaN at the entry (strategy reload: JnAtrRel returns NaN until 5 daily medians exist), which is the first thing to look for.
- Full list (all 140 rows):

| source                       | time_ET             |   qty_or_lots |   atr5_pts |   base_20d_median_pts |   atr_rel |
|:-----------------------------|:--------------------|--------------:|-----------:|----------------------:|----------:|
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-05 10:09:00 |             3 |      36.2  |                 19.44 |      1.86 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-06 10:43:00 |             1 |      32.82 |                 19.84 |      1.65 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-07 10:35:00 |             1 |      37.13 |                 19.44 |      1.91 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-12 10:00:00 |             3 |      36.77 |                 19.79 |      1.86 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-12 10:23:00 |             2 |      38.29 |                 19.79 |      1.94 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-14 18:50:00 |             7 |      34.11 |                 20.44 |      1.67 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-14 19:27:00 |             7 |      33.58 |                 20.44 |      1.64 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-14 20:00:00 |             7 |      34.44 |                 20.44 |      1.68 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-14 20:15:00 |             4 |      36.77 |                 20.44 |      1.8  |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-14 21:08:00 |             4 |      37.2  |                 20.44 |      1.82 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-14 21:25:00 |             4 |      38.7  |                 20.44 |      1.89 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-16 10:08:00 |             4 |      52.57 |                 21.36 |      2.46 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-16 11:03:00 |             1 |      57.44 |                 21.36 |      2.69 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-16 11:56:00 |             1 |      53.16 |                 21.36 |      2.49 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-20 10:53:00 |             4 |      58.59 |                 22.77 |      2.57 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-20 11:49:00 |             1 |      57.26 |                 22.77 |      2.51 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-21 10:00:00 |             2 |      48.98 |                 23.43 |      2.09 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-21 10:39:00 |             1 |      52.97 |                 23.43 |      2.26 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-22 11:04:00 |             4 |      52.59 |                 23.95 |      2.2  |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-22 11:41:00 |             4 |      52.53 |                 23.95 |      2.19 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-25 21:00:00 |             4 |      43.67 |                 24.1  |      1.81 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-25 21:46:00 |             4 |      44.7  |                 24.1  |      1.86 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-26 10:37:00 |             1 |      58.55 |                 24.1  |      2.43 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-26 11:15:00 |             4 |      55.72 |                 24.1  |      2.31 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-28 18:07:00 |             4 |      60.44 |                 24.41 |      2.48 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-28 18:49:00 |             7 |      50.35 |                 24.41 |      2.06 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-28 20:22:00 |             4 |      42.84 |                 24.41 |      1.76 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-28 20:39:00 |             1 |      42.44 |                 24.41 |      1.74 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-29 18:59:00 |             4 |      43.26 |                 24.41 |      1.77 |
| ENGINE P7 signal (LPB_EMPTY) | 2026-10-29 21:39:00 |             7 |      40.55 |                 24.41 |      1.66 |
| ENGINE P7 signal (NX_D)      | 2026-11-01 18:36:00 |             1 |      41.06 |                 25.28 |      1.62 |
| LIVE P7 entry                | 2026-11-01 18:36:00 |             4 |      41.06 |                 25.28 |      1.62 |
| ENGINE P7 signal (NX_D)      | 2026-11-02 10:02:00 |             1 |      42.11 |                 25.28 |      1.67 |
| LIVE P7 entry                | 2026-11-02 10:02:15 |             4 |      42.11 |                 25.28 |      1.67 |
| ENGINE P7 signal (NX_D)      | 2026-11-02 11:39:00 |             1 |      46.59 |                 25.28 |      1.84 |
| LIVE P7 entry                | 2026-11-02 11:51:45 |             2 |      44.01 |                 25.28 |      1.74 |
| LIVE P7 entry                | 2026-11-02 18:47:01 |             4 |      45.3  |                 26.24 |      1.73 |
| ENGINE P7 signal (NX_D)      | 2026-11-02 18:47:01 |             1 |      45.3  |                 26.24 |      1.73 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 10:18:00 |             1 |      56.26 |                 26.24 |      2.14 |
| LIVE P7 entry                | 2026-11-03 10:20:15 |             4 |      57.37 |                 26.24 |      2.19 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 10:42:00 |             1 |      56.24 |                 26.24 |      2.14 |
| LIVE P7 entry                | 2026-11-03 10:46:30 |             4 |      58.47 |                 26.24 |      2.23 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 11:53:00 |             1 |      50.22 |                 26.24 |      1.91 |
| LIVE P7 entry                | 2026-11-03 11:57:00 |             3 |      50.24 |                 26.24 |      1.91 |
| LIVE P7 entry                | 2026-11-03 18:56:01 |             4 |      43.75 |                 27.08 |      1.62 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 18:56:01 |             1 |      43.75 |                 27.08 |      1.62 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 19:15:00 |             1 |      46.9  |                 27.08 |      1.73 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 20:03:00 |             2 |      57.84 |                 27.08 |      2.14 |
| LIVE P7 entry                | 2026-11-03 20:03:00 |             7 |      57.84 |                 27.08 |      2.14 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 20:30:00 |             2 |      86.58 |                 27.08 |      3.2  |
| LIVE P7 entry                | 2026-11-03 20:30:00 |             7 |      86.58 |                 27.08 |      3.2  |
| ENGINE P7 signal (NX_D)      | 2026-11-03 20:44:00 |             2 |      86.79 |                 27.08 |      3.2  |
| LIVE P7 entry                | 2026-11-03 20:44:00 |             7 |      86.79 |                 27.08 |      3.2  |
| ENGINE P7 signal (NX_D)      | 2026-11-03 21:34:00 |             2 |      77.64 |                 27.08 |      2.87 |
| LIVE P7 entry                | 2026-11-03 21:34:00 |             7 |      77.64 |                 27.08 |      2.87 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 21:56:00 |             1 |      65.59 |                 27.08 |      2.42 |
| LIVE P7 entry                | 2026-11-03 21:56:00 |             4 |      65.59 |                 27.08 |      2.42 |
| LIVE P7 entry                | 2026-11-03 22:15:00 |             4 |      65.55 |                 27.08 |      2.42 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 22:15:00 |             1 |      65.55 |                 27.08 |      2.42 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 22:52:00 |             2 |      58.69 |                 27.08 |      2.17 |
| LIVE P7 entry                | 2026-11-03 22:52:00 |             7 |      58.69 |                 27.08 |      2.17 |
| LIVE P7 entry                | 2026-11-03 23:07:00 |             4 |      57.62 |                 27.08 |      2.13 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 23:07:00 |             1 |      57.62 |                 27.08 |      2.13 |
| ENGINE P7 signal (NX_D)      | 2026-11-03 23:18:01 |             1 |      59.65 |                 27.08 |      2.2  |
| LIVE P7 entry                | 2026-11-03 23:18:01 |             4 |      59.65 |                 27.08 |      2.2  |
| ENGINE P7 signal (NX_D)      | 2026-11-04 00:30:00 |             2 |      67.61 |                 27.08 |      2.5  |
| LIVE P7 entry                | 2026-11-04 00:30:00 |             7 |      67.61 |                 27.08 |      2.5  |
| LIVE P7 entry                | 2026-11-04 00:53:00 |             7 |      63.83 |                 27.08 |      2.36 |
| ENGINE P7 signal (NX_D)      | 2026-11-04 00:53:00 |             2 |      63.83 |                 27.08 |      2.36 |
| LIVE P7 entry                | 2026-11-04 01:31:01 |             7 |      57.3  |                 27.08 |      2.12 |
| ENGINE P7 signal (NX_D)      | 2026-11-04 01:31:01 |             2 |      57.3  |                 27.08 |      2.12 |
| LIVE P7 entry                | 2026-11-04 02:45:00 |             4 |      43.93 |                 27.08 |      1.62 |
| ENGINE P7 signal (NX_D)      | 2026-11-04 02:45:00 |             1 |      43.93 |                 27.08 |      1.62 |
| LIVE P7 entry                | 2026-11-04 07:25:00 |             5 |      45.16 |                 27.08 |      1.67 |
| ENGINE P7 signal (NX_D)      | 2026-11-04 07:25:00 |             1 |      45.16 |                 27.08 |      1.67 |
| ENGINE P7 signal (NX_D)      | 2026-11-04 07:43:00 |             1 |      45.35 |                 27.08 |      1.67 |
| ENGINE P7 signal (NX_D)      | 2026-11-04 08:05:00 |             1 |      50.25 |                 27.08 |      1.86 |
| ENGINE P7 signal (NX_D)      | 2026-11-04 11:21:00 |             1 |      87.97 |                 27.08 |      3.25 |
| LIVE P7 entry                | 2026-11-04 21:11:00 |             4 |      50.18 |                 27.94 |      1.8  |
| ENGINE P7 signal (NX_D)      | 2026-11-04 21:11:00 |             1 |      50.18 |                 27.94 |      1.8  |
| ENGINE P7 signal (NX_D)      | 2026-11-04 21:31:00 |             1 |      49.53 |                 27.94 |      1.77 |
| LIVE P7 entry                | 2026-11-04 21:31:00 |             4 |      49.53 |                 27.94 |      1.77 |
| LIVE P7 entry                | 2026-11-04 21:42:02 |             4 |      48.48 |                 27.94 |      1.74 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 10:37:00 |             2 |     103.14 |                 27.94 |      3.69 |
| LIVE P7 entry                | 2026-11-05 10:39:00 |             5 |     103.14 |                 27.94 |      3.69 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 11:00:00 |             1 |     128.45 |                 27.94 |      4.6  |
| LIVE P7 entry                | 2026-11-05 11:04:30 |             5 |     128.45 |                 27.94 |      4.6  |
| ENGINE P7 signal (NX_D)      | 2026-11-05 18:06:00 |             4 |      85.02 |                 28.62 |      2.97 |
| LIVE P7 entry                | 2026-11-05 18:06:00 |             7 |      85.02 |                 28.62 |      2.97 |
| LIVE P7 entry                | 2026-11-05 18:38:00 |             7 |     101.52 |                 28.62 |      3.55 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 18:38:00 |             4 |     101.52 |                 28.62 |      3.55 |
| LIVE P7 entry                | 2026-11-05 18:50:00 |             4 |     100.88 |                 28.62 |      3.52 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 18:50:00 |             2 |     100.88 |                 28.62 |      3.52 |
| LIVE P7 entry                | 2026-11-05 19:17:00 |             4 |      98.17 |                 28.62 |      3.43 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 19:17:00 |             1 |      98.17 |                 28.62 |      3.43 |
| LIVE P7 entry                | 2026-11-05 20:07:00 |             7 |      87.83 |                 28.62 |      3.07 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 20:07:00 |             2 |      87.83 |                 28.62 |      3.07 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 20:15:00 |             1 |      94.44 |                 28.62 |      3.3  |
| LIVE P7 entry                | 2026-11-05 20:15:00 |             7 |      94.44 |                 28.62 |      3.3  |
| LIVE P7 entry                | 2026-11-05 20:21:00 |             7 |      93.5  |                 28.62 |      3.27 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 20:21:00 |             1 |      93.5  |                 28.62 |      3.27 |
| LIVE P7 entry                | 2026-11-05 20:28:00 |             4 |      93.63 |                 28.62 |      3.27 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 20:28:00 |             1 |      93.63 |                 28.62 |      3.27 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 20:32:00 |             2 |      92.89 |                 28.62 |      3.24 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 20:48:00 |             1 |      89.51 |                 28.62 |      3.13 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 21:00:00 |             2 |      88.07 |                 28.62 |      3.08 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 21:18:00 |             2 |      84.42 |                 28.62 |      2.95 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 21:38:00 |             2 |      77.24 |                 28.62 |      2.7  |
| ENGINE P7 signal (NX_D)      | 2026-11-05 21:49:00 |             2 |      75.37 |                 28.62 |      2.63 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 22:56:01 |             1 |      56.34 |                 28.62 |      1.97 |
| ENGINE P7 signal (NX_D)      | 2026-11-05 23:09:00 |             4 |      57.72 |                 28.62 |      2.02 |
| ENGINE P7 signal (NX_D)      | 2026-11-06 00:13:01 |             1 |      47.48 |                 28.62 |      1.66 |
| ENGINE P7 signal (NX_D)      | 2026-11-06 00:28:00 |             1 |      49.9  |                 28.62 |      1.74 |
| ENGINE P7 signal (NX_D)      | 2026-11-06 01:01:02 |             1 |      48.82 |                 28.62 |      1.71 |
| ENGINE P7 signal (NX_D)      | 2026-11-06 03:02:00 |             1 |      51.41 |                 28.62 |      1.8  |
| ENGINE P7 signal (NX_D)      | 2026-11-06 03:39:01 |             1 |      50.81 |                 28.62 |      1.78 |
| ENGINE P7 signal (NX_D)      | 2026-11-06 04:02:00 |             2 |      48.58 |                 28.62 |      1.7  |
| ENGINE P7 signal (NX_D)      | 2026-11-06 04:45:00 |             2 |      46.56 |                 28.62 |      1.63 |
| ENGINE P7 signal (NX_D)      | 2026-11-06 08:04:00 |             2 |      46.09 |                 28.62 |      1.61 |
| ENGINE P7 signal (NX_D)      | 2026-11-06 10:42:00 |             2 |      90.9  |                 28.62 |      3.18 |
| LIVE P7 entry                | 2026-11-08 18:33:00 |             4 |      61.88 |                 29.14 |      2.12 |
| ENGINE P7 signal (NX_D)      | 2026-11-08 18:33:00 |             2 |      61.88 |                 29.14 |      2.12 |
| LIVE P7 entry                | 2026-11-08 19:01:00 |             4 |      67.61 |                 29.14 |      2.32 |
| ENGINE P7 signal (NX_D)      | 2026-11-08 19:01:00 |             2 |      67.61 |                 29.14 |      2.32 |
| ENGINE P7 signal (NX_D)      | 2026-11-08 19:03:00 |             2 |      67.61 |                 29.14 |      2.32 |
| LIVE P7 entry                | 2026-11-08 21:44:00 |             4 |      58.05 |                 29.14 |      1.99 |
| ENGINE P7 signal (NX_D)      | 2026-11-08 21:44:00 |             1 |      58.05 |                 29.14 |      1.99 |
| ENGINE P7 signal (NX_D)      | 2026-11-09 04:01:00 |             2 |      49.84 |                 29.14 |      1.71 |
| ENGINE P7 signal (NX_D)      | 2026-11-09 10:08:00 |             1 |      62.59 |                 29.14 |      2.15 |
| ENGINE P7 signal (NX_D)      | 2026-11-09 10:27:00 |             1 |      61.53 |                 29.14 |      2.11 |
| ENGINE P7 signal (NX_D)      | 2026-11-09 10:41:00 |             1 |      58.81 |                 29.14 |      2.02 |
| ENGINE P7 signal (NX_D)      | 2026-11-09 11:08:00 |             1 |      60.28 |                 29.14 |      2.07 |
| ENGINE P7 signal (NX_D)      | 2026-11-09 11:42:00 |             1 |      54.12 |                 29.14 |      1.86 |
| ENGINE P7 signal (NX_D)      | 2026-11-11 11:13:00 |             1 |      52.08 |                 31.34 |      1.66 |
| ENGINE P7 signal (NX_D)      | 2026-11-11 19:11:00 |             4 |      50.95 |                 31.34 |      1.63 |
| LIVE P7 entry                | 2026-11-11 19:11:00 |             6 |      50.95 |                 31.34 |      1.63 |
| ENGINE P7 signal (NX_D)      | 2026-11-12 10:38:00 |             1 |      78.16 |                 31.34 |      2.49 |
| ENGINE P7 signal (NX_D)      | 2026-11-12 10:52:00 |             1 |      74.85 |                 31.34 |      2.39 |
| ENGINE P7 signal (NX_D)      | 2026-11-13 11:15:00 |             2 |      87.93 |                 31.34 |      2.81 |
| LIVE P7 entry                | 2026-11-13 11:18:45 |             7 |      87.93 |                 31.34 |      2.81 |

## 9. Extended store (tape, 1-s state days and REG inputs to 2026-11-13 17:00 ET; store ev1113b, parity with the shared store identical on 202610) - panel timeline, live-dollar caps to 11-12 20:41Z then engine-unit caps (user-lot build), JN04 blackout from 11-10 09:00Z, no ATR-SKIP

| run            | window                                        | nLive   | nEng   | A   | B   | C   | U     | usdB   | usdC   |
|:---------------|:----------------------------------------------|:--------|:-------|:----|:----|:----|:------|:-------|:-------|
| TL3_EV_NX_D    | W45 11-01..11-06                              | 232     | 253    | 196 | 57  | 36  | 0.678 | 380    | 4810   |
| TL3_EV_NX_D    | W46 11-08..11-11                              | 123     | 150    | 98  | 52  | 25  | 0.560 | 20978  | 12445  |
| TL3_EV_NX_D    | W47 11-11 18:00..11-13 17:00 (user-lot build) | 54      | 95     | 44  | 51  | 10  | 0.419 | 4031   | -3455  |
| TL3_EV_NX_D    | ALL 11-01..11-13                              | 409     | 498    | 338 | 160 | 71  | 0.594 | 25390  | 13800  |
| TL3_EV_NX_D_DR | W45 11-01..11-06                              | 232     | 244    | 228 | 16  | 4   | 0.919 | 2568   | -735   |
| TL3_EV_NX_D_DR | W46 11-08..11-11                              | 123     | 134    | 118 | 16  | 5   | 0.849 | 4684   | -1330  |
| TL3_EV_NX_D_DR | W47 11-11 18:00..11-13 17:00 (user-lot build) | 54      | 58     | 42  | 16  | 12  | 0.600 | 1892   | -11840 |
| TL3_EV_NX_D_DR | ALL 11-01..11-13                              | 409     | 436    | 388 | 48  | 21  | 0.849 | 9143   | -13905 |

### 9b. Every remaining mismatch class after the exit cascade is removed (live-drive, ALL 11-01..11-13), with dollars (B = engine net, C = live net; engine base-lot dollars at $1.18 vs live dollars at actual fees; no x1.75 applied to either side)

| side   | cause                                                                     | n   | usd    |
|:-------|:--------------------------------------------------------------------------|:----|:-------|
| B      | LIVE JN04 P7 post-stop blackout                                           | 1   | -2327  |
| B      | LIVE O7 not trading (no live O7 entry since 11-06)                        | 4   | 2095   |
| B      | LIVE book lock fired earlier that day (BookLock exit)                     | 4   | 80     |
| B      | LIVE flat, no live entry (gate/signal unknown)                            | 34  | 2102   |
| B      | LIVE flat; other book entered                                             | 1   | 1199   |
| B      | LIVE reconnect/stall window                                               | 4   | 5994   |
| C      | ENGINE give-back lock: engine P&L path only (live book had not crossed)   | 2   | -3670  |
| C      | ENGINE give-back lock: live book had ALSO crossed it (live kept entering) | 4   | -2175  |
| C      | ENGINE loss cap: engine P&L path only (live book had not crossed)         | 1   | -2175  |
| C      | ENGINE loss cap: live book had ALSO crossed it (live kept entering)       | 5   | -1330  |
| C      | ENGINE no signal                                                          | 8   | 6845   |
| C      | ENGINE skip: SKIP JN04 post-stop blackout                                 | 1   | -11400 |

### 9c. What the engine would have made 11-08 18:00 .. 11-13 17:00 (label week), base-lot dollars, x1.75 and the $4.84 fee beside; live actual beside

B1/B2 apply the cut behaviour the lead listed (K7 flat -45 only, P7 flat -42 from 11-12, the P7 split-entry trades of 11-11 evening silent). Full stops counted on exit names Stop*.

| run                                                                                                    | trades   | full_stops   | net_1p18_base   | net_4p84_base   | net_4p84_x1p75   | maxDayLoss_base   |
|:-------------------------------------------------------------------------------------------------------|:---------|:-------------|:----------------|:----------------|:-----------------|:------------------|
| AS DESIGNED (state cuts as in the policy lines)                                                        | 245      | 18           | 3558            | 2149            | 3761             | -35923            |
| AS LIVE BEHAVED B1 (K7 flat45 all week, P7 silent 11-11 22Z..11-12 20:41Z, P7 flat42 after)            | 251      | 17           | -10056          | -11473          | -20077           | -36196            |
| AS LIVE BEHAVED B2 (flat lines only from the v1.9a install 11-12 20:41Z, P7 silent 11-11 22Z..install) | 237      | 21           | -9860           | -11225          | -19644           | -35923            |
| ALL CUTS OFF all week (lower bound; flat K7 45 / P7 42 only from the 11-12 20:41Z install)             | 225      | 58           | 32838           | 31502           | 55128            | -29135            |
| LIVE actual (live lots, actual NT fees)                                                                | 177      | 45           |                 |                 | -26520           | -29195            |

### 9d. Engine-only entries with no identified live gate, window 11-11 18:00..11-13 17:00 (live-drive, caps corrected: box to 11-08 23Z, live-coded to 11-12 20:41Z, engine-unit after), engine state and live state at entry

Each row: engine path (ARM/ENTRY/confirm from the engine log), live day closes and day P&L (user-lot dollars after 11-12), live consecutive same-side losers of the book in the session (v1.9 EVIDENCE candidate for P7), minutes since the live book last exited.

| cls                                                               | n   | usd   |
|:------------------------------------------------------------------|:----|:------|
| EVIDENCE candidate (P7, >=2 same-side live losers in the session) | 2   | -4715 |
| live exited <60 min ago (re-entry gate/blackout/ctx?)             | 1   | 1199  |
| live flat >60 min, signal present engine-side only                | 11  | 6536  |

| book   | te_et               | qty   | usd   | live_day_closes   | live_day_pnl   | live_same_side_loser_run   | mins_since_live_exit   | last_live_exit   | engine_log                                                                                 | cls                                                               |
|:-------|:--------------------|:------|:------|:------------------|:---------------|:---------------------------|:-----------------------|:-----------------|:-------------------------------------------------------------------------------------------|:------------------------------------------------------------------|
| M7     | 2026-11-12 08:29:00 | 1     | -2302 | 19                | -19955         | 0                          | 68                     | PolicyCut        | ARM side -1 sigpx 28078.75 stopLevel 28138.75 lots | ENTRY side -1 qty 1 slices; trade_sto | live flat >60 min, signal present engine-side only                |
| O7     | 2026-11-12 09:43:00 | 1     | -781  | 19                | -19955         | 0                          | 8640                   | PolicyCut        | pb1 signal 1 at 28371.75 | ENTRY side 1 qty 1 market | BRACKET stop 28330.00 (native 28330 | live flat >60 min, signal present engine-side only                |
| M7     | 2026-11-12 10:54:00 | 1     | 1199  | 19                | -19955         | 1                          | 212                    | PolicyCut        | ARM side 1 sigpx 28430.25 stopLevel 28370.25 lots  | ENTRY side 1 qty 1 slices; trade_stop | live flat >60 min, signal present engine-side only                |
| P7     | 2026-11-12 21:02:00 | 2     | -2357 | 6                 | -9015          | 2                          | 57                     | PolicyCut        | ARM side 1 sigpx 28577.75 stopLevel 28517.75 lots  | ENTRY side 1 qty 1 slices; trade_stop | EVIDENCE candidate (P7, >=2 same-side live losers in the session) |
| K7     | 2026-11-12 21:18:00 | 1     | 1199  | 7                 | -10765         | 0                          | 2                      | PolicyCut        | ARM side -1 sigpx 28512.50 stopLevel 28572.50 lots | ENTRY side -1 qty 1 slices; trade_sto | live exited <60 min ago (re-entry gate/blackout/ctx?)             |
| P7     | 2026-11-12 21:39:00 | 2     | -2357 | 8                 | -15615         | 2                          | 94                     | PolicyCut        | ARM side 1 sigpx 28533.00 stopLevel 28473.00 lots  | ENTRY side 1 qty 1 slices; trade_stop | EVIDENCE candidate (P7, >=2 same-side live losers in the session) |
| P7     | 2026-11-12 22:09:00 | 1     | 1199  | 8                 | -15615         | 0                          | 124                    | PolicyCut        | ARM side -1 sigpx 28472.00 stopLevel 28532.00 lots | ENTRY side -1 qty 1 slices; trade_sto | live flat >60 min, signal present engine-side only                |
| U7     | 2026-11-12 22:30:00 | 4     | 4800  | 8                 | -15615         | 0                          | 862                    | Target           | ARM side -1 sigpx 28409.25 stopLevel 28469.25 lots | ENTRY side -1 qty 3 slices; trade_sto | live flat >60 min, signal present engine-side only                |
| A7     | 2026-11-12 22:33:00 | 1     | 1199  | 8                 | -15615         | 0                          | 1282                   | Stop             | ENTRY side -1 qty 1 slices; trade_stop_pts 0.00 | BRACKET stop 28454.25 (native 28454.25)  | live flat >60 min, signal present engine-side only                |
| K7     | 2026-11-12 22:51:00 | 1     | -1    | 8                 | -15615         | 0                          | 95                     | PolicyCut        | ARM side -1 sigpx 28400.25 stopLevel 28460.25 lots | ENTRY side -1 qty 1 slices; trade_sto | live flat >60 min, signal present engine-side only                |
| A7     | 2026-11-13 00:38:00 | 1     | 1199  | 8                 | -15615         | 0                          | 1407                   | Stop             | ENTRY side -1 qty 1 slices; trade_stop_pts 0.00 | BRACKET stop 28379.00 (native 28379.00)  | live flat >60 min, signal present engine-side only                |
| H7     | 2026-11-13 01:00:00 | 2     | -1772 | 9                 | -13255         | 0                          | 215                    | Stop             | ARM side -1 sigpx 28289.50 stopLevel 28349.50 lots | ENTRY side -1 qty 1 slices; trade_sto | live flat >60 min, signal present engine-side only                |
| A7     | 2026-11-13 01:06:00 | 1     | -1    | 9                 | -13255         | 0                          | 1435                   | Stop             | ENTRY side -1 qty 1 slices; trade_stop_pts 0.00 | BRACKET stop 28322.25 (native 28322.25)  | live flat >60 min, signal present engine-side only                |
| O7     | 2026-11-13 09:41:00 | 1     | 1799  | 25                | -2120          | 0                          | 10078                  | PolicyCut        | pb1 signal -1 at 28286.50 | ENTRY side -1 qty 1 market | BRACKET stop 28327.00 (native 283 | live flat >60 min, signal present engine-side only                |

### 9e. Same classes, unconditional run, ALL 11-01..11-13

| cls                                                               | n   | usd   |
|:------------------------------------------------------------------|:----|:------|
| DAY-DONE candidate (closes>=22 and day<=-4200)                    | 12  | -4718 |
| EVIDENCE candidate (P7, >=2 same-side live losers in the session) | 1   | -1769 |
| live exited <60 min ago (re-entry gate/blackout/ctx?)             | 10  | 569   |
| live flat >60 min, signal present engine-side only                | 12  | 6163  |

## 12. The 45 live full stops 11-08 18:00..11-13 17:00 (live -$122,565) against the engine (state cuts as designed, run NX_D on the extended store)

For each live full stop: did the engine take the same entry (+-30 s, same book and side) and what did its exit do. Dollars: live pnlNet (x1.75 lots from 11-12) vs engine base-lot net_fee on the same entry. Engine cut lead = seconds the engine exit precedes the live stop fill; for the 32 trades where the engine cut earlier: median 186 s, quartiles 68 / 795 s.

| cls                                               | n   | live_usd   | engine_usd   | live_minus_engine   |
|:--------------------------------------------------|:----|:-----------|:-------------|:--------------------|
| engine also full stop                             | 5   | -12200     | -9049        | -3151               |
| engine cut EARLIER (state cut fired, live silent) | 32  | -90160     | -37314       | -52846              |
| engine did not take it (class C)                  | 6   | -14375     | 0            | -14375              |
| engine other exit: StateCut                       | 1   | -1210      | -1145        | -65                 |
| engine target (engine price path differs)         | 1   | -4620      | 2393         | -7013               |

| book   | te_et               | qty   | live_exit        | live_usd   | engine_exit       | engine_usd   | engine_exit_lead_s   | cls                                               |
|:-------|:--------------------|:------|:-----------------|:-----------|:------------------|:-------------|:---------------------|:--------------------------------------------------|
| P7     | 2026-11-08 18:33:00 | 4     | StopJoin         | -4685      | StopJoin          | -2242        | 0                    | engine also full stop                             |
| P7     | 2026-11-08 19:01:00 | 4     | StopJoinFallback | -4620      | Target            | 2393         | 273                  | engine target (engine price path differs)         |
| K7     | 2026-11-08 19:39:00 | 1     | StopJoin         | -1255      | StateCut          | -645         | 172                  | engine cut EARLIER (state cut fired, live silent) |
| K7     | 2026-11-08 20:18:00 | 1     | StopJoinFallback | -1370      | StateCut          | -587         | 162                  | engine cut EARLIER (state cut fired, live silent) |
| H7     | 2026-11-08 20:40:01 | 2     | Stop             | -2410      | StateCut          | -859         | 103                  | engine cut EARLIER (state cut fired, live silent) |
| U7     | 2026-11-08 21:30:00 | 4     | StopJoin         | -4680      | StateCut          | -1054        | 1997                 | engine cut EARLIER (state cut fired, live silent) |
| P7     | 2026-11-08 21:44:00 | 4     | StopJoin         | -4325      | StateCut          | -960         | 438                  | engine cut EARLIER (state cut fired, live silent) |
| P7     | 2026-11-08 22:32:00 | 7     | StopJoin         | -7355      | StateCut          | -2034        | 50                   | engine cut EARLIER (state cut fired, live silent) |
| M7     | 2026-11-09 03:04:00 | 2     | StopJoinFallback | -2325      | StateCut          | -1604        | 18                   | engine cut EARLIER (state cut fired, live silent) |
| P7     | 2026-11-09 20:12:00 | 4     | StopJoinFallback | -4925      | (no engine entry) | 0            |                      | engine did not take it (class C)                  |
| K7     | 2026-11-09 20:12:00 | 1     | StopJoinFallback | -1360      | StateCut          | -1047        | 163                  | engine cut EARLIER (state cut fired, live silent) |
| U7     | 2026-11-09 22:40:00 | 4     | StopJoin         | -3715      | StopJoin          | -2207        | 0                    | engine also full stop                             |
| K7     | 2026-11-09 23:12:00 | 2     | StopJoinFallback | -2150      | StateCut          | -597         | 73                   | engine cut EARLIER (state cut fired, live silent) |
| U7     | 2026-11-10 00:40:00 | 2     | StopJoinFallback | -2160      | StopJoinFallback  | -2217        | -1                   | engine also full stop                             |
| A7     | 2026-11-10 00:43:00 | 1     | Stop             | -1205      | Stop              | -1191        | 0                    | engine also full stop                             |
| P7     | 2026-11-10 01:26:00 | 4     | StopJoin         | -4865      | StateCut          | -3249        | 206                  | engine cut EARLIER (state cut fired, live silent) |
| M7     | 2026-11-10 02:11:02 | 1     | StopJoin         | -1230      | StateCut          | -620         | 1036                 | engine cut EARLIER (state cut fired, live silent) |
| K7     | 2026-11-10 02:48:00 | 1     | StopJoin         | -1145      | (no engine entry) | 0            |                      | engine did not take it (class C)                  |
| P7     | 2026-11-10 03:48:02 | 1     | StopJoin         | -1210      | StateCut          | -1145        | 3                    | engine other exit: StateCut                       |
| K7     | 2026-11-10 04:03:00 | 1     | StopJoinFallback | -1380      | StateCut          | -515         | 560                  | engine cut EARLIER (state cut fired, live silent) |
| M7     | 2026-11-10 04:04:00 | 1     | StopJoinFallback | -1295      | StateCut          | -600         | 1528                 | engine cut EARLIER (state cut fired, live silent) |
| U7     | 2026-11-10 04:10:01 | 2     | StopJoinFallback | -2460      | StateCut          | -662         | 715                  | engine cut EARLIER (state cut fired, live silent) |
| K7     | 2026-11-10 04:33:02 | 1     | StopJoinFallback | -1390      | StateCut          | -597         | 2569                 | engine cut EARLIER (state cut fired, live silent) |
| M7     | 2026-11-10 05:43:00 | 1     | StopJoin         | -1215      | StateCut          | -755         | 1170                 | engine cut EARLIER (state cut fired, live silent) |
| K7     | 2026-11-10 07:33:01 | 1     | Stop             | -80        | StateCut          | -762         | 3067                 | engine cut EARLIER (state cut fired, live silent) |
| M7     | 2026-11-10 14:48:00 | 1     | StopJoin         | -1240      | (no engine entry) | 0            |                      | engine did not take it (class C)                  |
| P7     | 2026-11-11 02:31:00 | 1     | StopJoin         | -1175      | (no engine entry) | 0            |                      | engine did not take it (class C)                  |
| M7     | 2026-11-11 02:38:00 | 1     | StopJoinFallback | -1165      | StateCut          | -670         | 200                  | engine cut EARLIER (state cut fired, live silent) |
| M7     | 2026-11-11 04:04:01 | 1     | StopJoin         | -1145      | StateCut          | -610         | 405                  | engine cut EARLIER (state cut fired, live silent) |
| P7     | 2026-11-11 04:04:01 | 2     | StopJoin         | -2195      | StateCut          | -1659        | 151                  | engine cut EARLIER (state cut fired, live silent) |
| K7     | 2026-11-11 18:45:00 | 4     | StopJoin         | -4130      | StateCut          | -1679        | 99                   | engine cut EARLIER (state cut fired, live silent) |
| P7     | 2026-11-11 19:11:00 | 6     | StopJoin         | -7030      | StateCut          | -3664        | 34                   | engine cut EARLIER (state cut fired, live silent) |
| P7     | 2026-11-11 19:58:01 | 6     | StopJoin         | -6835      | StateCut          | -1679        | 54                   | engine cut EARLIER (state cut fired, live silent) |
| P7     | 2026-11-11 21:31:00 | 6     | StopJoin         | -6420      | StateCut          | -3464        | 120                  | engine cut EARLIER (state cut fired, live silent) |
| A7     | 2026-11-12 00:58:00 | 2     | Stop             | -2405      | StateCut          | -1122        | 321                  | engine cut EARLIER (state cut fired, live silent) |
| U7     | 2026-11-12 04:30:00 | 2     | StopJoinFallback | -2675      | StateCut          | -1384        | 2152                 | engine cut EARLIER (state cut fired, live silent) |
| M7     | 2026-11-12 06:58:01 | 2     | StopJoin         | -2340      | StateCut          | -805         | 11                   | engine cut EARLIER (state cut fired, live silent) |
| H7     | 2026-11-12 20:50:00 | 4     | Stop             | -4850      | StateCut          | -795         | 600                  | engine cut EARLIER (state cut fired, live silent) |
| A7     | 2026-11-13 01:14:00 | 1     | Stop             | -1210      | (no engine entry) | 0            |                      | engine did not take it (class C)                  |
| M7     | 2026-11-13 03:22:00 | 2     | StopJoin         | -2285      | StateCut          | -750         | 2846                 | engine cut EARLIER (state cut fired, live silent) |
| M7     | 2026-11-13 07:12:00 | 4     | StopJoin         | -4680      | (no engine entry) | 0            |                      | engine did not take it (class C)                  |
| M7     | 2026-11-13 08:28:02 | 2     | StopJoin         | -435       | StopJoin          | -1191        | 1                    | engine also full stop                             |
| M7     | 2026-11-13 10:48:00 | 2     | StopJoin         | -2145      | StateCut          | -575         | 48                   | engine cut EARLIER (state cut fired, live silent) |
| M7     | 2026-11-13 11:05:00 | 1     | StopJoin         | -1220      | StateCut          | -602         | 11                   | engine cut EARLIER (state cut fired, live silent) |
| M7     | 2026-11-13 11:23:00 | 2     | StopJoin         | -2175      | StateCut          | -710         | 43                   | engine cut EARLIER (state cut fired, live silent) |

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
