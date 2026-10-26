# REPORT LIVE AUDIT (DDMIN step 1): the live DualStrat log (account <acct>, 2026-10-04..10-16) against the corrected engine and the tested risk rules

**Headline.** The live book earned $27,595 over the 10 sessions in the log ($ 32,330 from ST+HM, -4,735 from WT). Three facts drive the audit: (1) the combined give-back lock was NOT live before the 10-15 chart change; run as TESTED (rules on every day) the engine would have fired it in 6 of the 10 sessions (10-05, 10-07, 10-13, 10-14, 10-15, 10-16) and the cap in 2 (10-07, 10-14); (2) 64% of ST exits (77 of 120) and 45% of HM exits (35 of 77) were TH LossExits, while the scoring base is TH-off; (3) only 105 of 197 live ST/HM entries (53%) can be matched to an engine entry (same book and side, within 2.5 minutes), because a TH exit frees the book for a new signal that the engine (still in the trade) skips and vice versa; the matched entries agree on exit class when the exit is a Target (36 of 37 live Targets are engine Targets) and diverge on TH exits (live LossExit vs engine Target 16 / Stop 20 / flip 14 / time block 2).

## 1. Data notes
- Source: `outputs/h2/StratTrades_DualStrat_<acct>.csv`, 208 rows; 4 rows (WTStrat, `entryTime` 0001-01-01, all exiting 2026-10-04 20:11:21 with pnlNet 0) are corrupt duplicates and excluded (204 rows used). Times are exchange ET; session label = ET time + 6 h (Sunday 18:00 belongs to Monday); the log ends at 2026-10-16 04:30:11 (label 10-16 is a partial session: entries up to 04:30, so only ~11 hours of it are in the log).
- WT book: 7 valid WT trades, all on the evening of 2026-10-04 (label 10-05), 5 contracts, 6 LossExits and 1 Target, net $-4,735; none afterwards. WT is NOT live after that session (WT-10's own rule would give ~13 signals per week). The WT test session is outside the pair engine and is excluded from the engine comparisons.
- Quantities: ST 7-8 contracts, HM 4-8 (engine: 8/8); live `pnlNet` is the log's net per trade (commission and slippage fields are empty). The engine rows are TH-off (exit names Target/Stop/Entry flip/TimeBlock only).
- Engine sessions are replayed with the live-config machinery of the DAYRULES base (per-book 5R/-2R, combined day lock cap 8R + give-back arm 2R keep 33%, week floor -8R): the base reproduces 1.46/2.83/2.48/1.90. 'As tested' = all rules on every day; 'as live' = give-back off until the 10-16 session (the log shows the first firing at 10-16 04:30 ET; the user note says the give-back went live on 10-15, the session label 10-16 starts 10-15 18:00); the cap, per-book rules and week floor are assumed live throughout (the log gives no evidence either way; `ComboLock` is the only combined-rule exit seen).

## 2. Per-session table
| session | live net | live trades ST/HM | live LossExits ST/HM | engine TH-off, per-book rules only | engine as tested (gb on) | engine as live (gb off until 10-16) | live - engine as live | give-back WOULD fire (ET; marked / realised / peak) | cap WOULD fire (ET; marked / realised) | live ComboLock |
|---|---|---|---|---|---|---|---|---|---|---|
| 20261005 | -7,925 | 0/1 | 0/1 | 65,477 | 8,500 | 65,477 | -73,402 | 10-04 23:39; 8,575 / 9,255 / 27,170 | no | - |
| 20261006 | 35,595 | 8/8 | 3/6 | 2,296 | 2,296 | 2,296 | +33,299 | no | no | - |
| 20261007 | 20,450 | 17/13 | 11/10 | 89,577 | 6,191 | 77,287 | -56,837 | 10-07 04:04; 6,226 / 9,026 / 19,690 | 10-07 11:48; 77,357 / 65,477 | - |
| 20261008 | -5,600 | 17/14 | 14/8 | -22,339 | -22,339 | -22,339 | +16,739 | no | no | - |
| 20261009 | -38,965 | 4/11 | 3/10 | -49,399 | -49,399 | -49,399 | +10,434 | no | no | - |
| 20261012 | 15,365 | 3/5 | 0/0 | -3,344 | -3,344 | -3,344 | +18,709 | no | no | - |
| 20261013 | -5,855 | 21/6 | 13/0 | -42,248 | 10,211 | -42,248 | +36,393 | 10-12 23:53; 10,361 / 18,281 / 31,721 | no | - |
| 20261014 | 49,135 | 20/8 | 12/0 | 83,758 | 7,860 | 77,868 | -28,733 | 10-14 01:02; 8,490 / 18,970 / 26,090 | 10-14 14:01; 77,822 / 74,502 | - |
| 20261015 | -43,280 | 20/8 | 14/0 | 9,488 | 16,436 | 9,488 | -52,768 | 10-14 20:41; 16,351 / 18,511 / 52,460 | no | - |
| 20261016 | 8,675 | 10/3 | 7/0 | 74,502 | 6,881 | 6,881 | +1,794 | 10-16 05:00; 7,191 / 18,511 / 25,351 | no | STStrat 10-16 04:30:11 8@30178.25; HMStrat 10-16 04:30:11 8@30178.5 |
| **total** | **27,595** | 120/77 | 77/35 | 207,769 | -16,705 | 121,967 | -94,372 | | | |

The label-10-05 live net includes the WT test session (-$4,735); the engine columns have no WT book. Engine P&L is at 8/8 contracts; live quantities were 7-8 ST and 4-8 HM.

**Effect of the give-back (engine as tested minus as live), per session ($):** 20261005: -56,976, 20261006: +0, 20261007: -71,096, 20261008: +0, 20261009: +0, 20261012: +0, 20261013: +52,460, 20261014: -70,007, 20261015: +6,948, 20261016: +0. Total -138,672 over the sessions before it went live (and 10-16, where it is on in both versions: 0). I.e. running the give-back on the 9 earlier sessions would have changed the engine P&L by -138,672.

## 3. Sessions where the live chart diverged from the tested rules
- 20261005: live -7,925 vs engine as live 65,477 (as tested 8,500): live minus engine -73,402
- 20261006: live 35,595 vs engine as live 2,296 (as tested 2,296): live minus engine +33,299
- 20261007: live 20,450 vs engine as live 77,287 (as tested 6,191): live minus engine -56,837
- 20261013: live -5,855 vs engine as live -42,248 (as tested 10,211): live minus engine +36,393
- 20261014: live 49,135 vs engine as live 77,868 (as tested 7,860): live minus engine -28,733
- 20261015: live -43,280 vs engine as live 9,488 (as tested 16,436): live minus engine -52,768

Sessions where the give-back would have fired but the chart ran without it (as tested minus as live differs): 20261005 (-56,976), 20261007 (-71,096), 20261013 (+52,460), 20261014 (-70,007), 20261015 (+6,948). The first live firing (10-16 04:30:11: ST_ComboLock 8 contracts at 30178.25 and HM_ComboLock 8 at 30178.50) is 30 minutes BEFORE the engine's as-tested firing time (05:00, marked equity $7.2k from a $25.4k peak): the live book had a higher intraday peak or lower marks than the engine rows at that moment (live fills, qty and TH exits differ).

**Start of the live books.** First logged entry: ST 2026-10-05 20:08, HM 2026-10-04 19:45, WT 2026-10-04 18:16. No ST trade is logged for the session labelled 10-05 (the first full ST/HM session is 10-06), while the engine has 10 ST and 5 HM rows for it: the 10-05 engine P&L (+$65k) is a session the live book did not trade, so the 10-05 difference is a start-up gap, not a rule or TH gap. Session 10-16 is partial in the log (to 04:30:11): the engine rows that closed by that time net $18,511 against the live $8,675; the full-session engine figures in the table (as tested $6,881) include the rest of the day.

## 4. Live versus engine: entries, exits and the TH gap (ST and HM)
- Entries: live ST/HM 197 (ST 120, HM 77); engine rows in the window 201 (ST 127, HM 74); matched 105; live-only 92; engine-only 96.
- Matching rule: same book and side, live entry time within 150 s of the engine entry-minute start (engine `et_in` is the END of the entry minute); greedy nearest.

Exit class of the MATCHED entries (rows = live, columns = engine TH-off):

| cls         |   Entry |   Stop |   Target |   TimeBlock |
|:------------|--------:|-------:|---------:|------------:|
| ComboLock   |       0 |      1 |        0 |           0 |
| LossExit    |      14 |     20 |       16 |           2 |
| SessionFlat |       0 |      1 |        0 |           0 |
| Stop        |       2 |     12 |        0 |           0 |
| Target      |       1 |      0 |       36 |           0 |

Live exits by type per book:

| book   |   ComboLock |   LossExit |   SessionFlat |   Stop |   Target |
|:-------|------------:|-----------:|--------------:|-------:|---------:|
| HM     |           1 |         35 |             0 |     14 |       27 |
| ST     |           1 |         77 |             1 |      4 |       37 |

Engine exits by type per book (account-level labels: `Entry` = closed by the other book's opposite entry through lot netting):

| book   |   Entry |   Stop |   Target |   TimeBlock |
|:-------|--------:|-------:|---------:|------------:|
| HM     |       6 |     22 |       43 |           3 |
| ST     |      18 |     38 |       68 |           3 |

**Gap decomposition (ST+HM, whole window, raw rows without the combined rules):** live $32,330 versus engine TH-off $246,589 (8/8, engine rows after the per-book rule are not applied here): difference -214,259 = matched trades with a live LossExit -66,068 + other matched trades +21,539 + live-only trades (re-entries after exits the engine did not take, other timing) +3,880 + engine-only trades the live book did not take (engine net $164,052, counted against live: -164,052; the 10-05 session before ST started is $46,971 of the ST part).

Per-session matched entries and gap:

| session | live ST/HM trades | engine rows | matched | live-only | engine-only | matched LossExit diff | live-only net | engine-only net |
|---|---|---|---|---|---|---|---|---|
| 20261005 | 1 | 15 | 0 | 1 | 15 | +0 | -3,190 | +65,477 |
| 20261006 | 16 | 11 | 7 | 9 | 4 | +4,582 | +20,525 | +1,940 |
| 20261007 | 30 | 19 | 14 | 16 | 5 | -67,565 | +11,705 | +2,826 |
| 20261008 | 31 | 23 | 14 | 17 | 9 | +4,510 | -5,005 | -9,874 |
| 20261009 | 15 | 17 | 7 | 8 | 10 | +833 | -10,775 | -26,589 |
| 20261012 | 8 | 18 | 6 | 2 | 12 | +0 | -105 | +17,421 |
| 20261013 | 27 | 23 | 14 | 13 | 9 | +1,999 | -6,700 | -40,674 |
| 20261014 | 28 | 23 | 20 | 8 | 3 | -36,426 | +5,605 | +5,655 |
| 20261015 | 28 | 32 | 18 | 10 | 14 | +17,699 | -21,035 | +51,232 |
| 20261016 | 13 | 20 | 5 | 8 | 15 | +8,300 | +12,855 | +96,637 |

**TH exits (LossExit) in the log:** ST 77 of 120 (64%), HM 35 of 77; net of all LossExits $-372,575 (ST $-291,085, HM $-81,490); mean hold of a LossExit 28 min against 65 min for the other exits.
- HM TH timing: HM LossExits by label day: 20261005: 1, 20261006: 6, 20261007: 10, 20261008: 8, 20261009: 10 (the user states HM TH was on until 10-09 and off after; the log shows HM LossExits only up to 10-09, consistent).

On the 52 matched entries that the live book closed with a LossExit, the engine (TH-off) outcome was: Stop 20, Target 16, Entry 14, TimeBlock 2; live net on them $-174,700 versus engine $-108,632 (live minus engine -66,068): i.e. in this sample the TH exits cost money relative to letting the same entries run (small sample, 10 sessions; B3-TH on the older engine called ST TH neutral, MAR +0.60).

## 5. What to do with this
- The live and tested books differ on three counts: TH exits (the scoring base is TH-off), the give-back (not live before 10-16), and 7-8 / 4-8 contract quantities. Until the TH rule is ported (step 2) the TH-off DAYRULES / SMOOTH / DDMIN scores describe a book that is not the live book; the gap above is the size of that difference on these 10 sessions.
- No live change recommended from this audit.

DONE LIVE_AUDIT
