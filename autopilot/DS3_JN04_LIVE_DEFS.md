# DS3_JN04_LIVE_DEFS - JN04 and JP07 as exact live definitions (SHADOW ONLY; no PASS claims)

Written by SZ-IJK (JOINT), 2026-11-10. Base = the live D7 v1.4 panel (data/live_code/DS7.cs) with the Q1-A ER sizer (TrendMode Live, TrendErPeriod 20, TrendErThreshold 0.30, TrendMultLow 0.5, TrendMultHigh 1.0), the zone HALF layer (NtzMode Live, NtzAction Half, NtzDistancePts 20) and the other live layers unchanged. **JN04 = Q1-A + four extra lot-multiplier layers: LOT x SIGQ x REG x STACK.** **JP07 = JN04 + one entry panel change (CF_EN_45).** Evidence is the EXACT S1b engine (ROLLFIX1, reference base_b_rollfix S1-COMB). Labels under standing rules 2/2a with the 2026-11-10 13:45Z floor (PRE mean floor = 25% of the live PRE mean): JN04 = RECENT-ONLY (old fixed-floor: RECENT-ONLY); JP07 = OK-PRIOR (old fixed-floor: RECENT-ONLY). All first-order numbers are marked FIRST-ORDER.

## 0. How the four layers compose (and what the exact evidence did and did not test)

- Order of one signal: session lots (+ A06 slot half, B02 half) -> Q1-A ER x0.5 below 0.30 (rounded, min 1) -> **LOT x SIGQ x REG multiplier (each 1 or 0.5; product rounded: lots = max(1, floor(lots x m + .5)); 0 = skip)** -> zone HALF (rounded, min 1) -> **STACK cap at order time (room = 6 - open same-side lots of the other books; London only)**.
- The exact evidence rows (JN04, JD01-JD04) were run in TABLE mode: one multiplier per base signal (book, signal second) applied after the Q1-A ladder and before zone HALF; the STACK layer is therefore a table built from the BASE trades' open lots, not the engine's own live state. A RULE-MODE run of STACK (SZ-CDE cde code 8 hook on the JN04 table without STACK, set JR01) is queued; its rows appear below when done. The first-order rounding (after zone HALF) differs by a rounding step from the engine order above.
- The multiplier layers are DOWN-ONLY (never above the Q1-A lots), all ON; the 0.5 factor is a floor setting, not an off switch (standing rule 1: no layer is turned off).

## 1. LOT - P7 book recent-performance gate (JN04 layer 1; my family I/K cell K5 "I3 on P7")

**Rule.** Books: P7 only (all sessions). State = the P7 SHADOW equity: the P&L the P7 book would have made at its BASE (Q1-A) lots, closed trades only (exit before the signal second), summed per label day (label day rolls at 17:00 ET). At each P7 signal take the last 10 COMPLETED label days before the signal's label day: S = sum of the 10 daily P&L, DD = maximum drawdown of their cumulative path (from 0), C10 = S / DD (undefined if DD = 0: gate off). **If C10 < 1.0: lot multiplier 0.5, else 1.** Applied once per signal; the gate state is recomputed at every signal (shadow state continues while the book is gated, so it can switch back on).
**Inputs.** P7 closed-trade P&L per lot x base lots (needs a shadow base-lot ledger because gated trades are smaller), label-day clock. No other book.
**DS7 v1.4 fields.** None implements it. Closest: group 12 RECENT FILTERS (b) RfLoserMode / RfLoserMins (skip the next signal after the book's own loser) - different rule. **NEW CODE FOR v1.6** (proposed field names): `P7PerfGateMode` (Off|Shadow|Live), `P7PerfGateBooks` = "P7", `P7PerfGateDays` = 10, `P7PerfGateCalmarBelow` = 1.0, `P7PerfGateMult` = 0.5; plus a per-book shadow-equity tracker.

**Worked example (frozen week, first-order, P7 rows of data/live_frozen).** The P7 shadow Calmar was below 1.0 for the whole week (C10 = -0.85 with S = -57,677 on 11-01 and 11-02 until 17:00; -0.63 / S = -42,793 on 11-02 evening and 11-03; -0.12 on 11-03 evening to 11-04; +0.25 / S = +14,165 from 11-04 evening, still < 1.0). So every P7 signal of the week is x0.5: 11-01 18:36 ET long 4 lots -> floor(4 x .5 + .5) = 2 lots (actual +4,805 -> about +2,402); 11-01 19:11 10 lots -> 5 lots (actual +12,010 -> about +6,005); 11-04 18:48 4 -> 2. First-order live-week effect of the whole P7 gate: about -37k (the week was a big P7 win week; this is the known cost of any down-sizing in a winning week). FIRST-ORDER.

**Exact evidence (table mode).** JD01 = JN04 without this layer.

| exact set | what | L6M cut / d mean | HOLD cut / d mean | PRE cut / d mean | X' cut / d mean | GAP 2025-07..10 cut / d mean |
|---|---|---|---|---|---|---|
| JN04 | full JN04 | +43.4 / +4860 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | -1.2 / -7148 |
| JD01 | JN04 minus LOT | +22.8 / +3205 | +38.0 / -321 | n/a / n/a | n/a / n/a | +16.3 / -3479 |

Reading: LOT contributes 20.6 points of the L6M maxDD cut (JN04 +43.4 vs JD01 +22.8) and adds 1655 $/wk in L6M; in the trend regimes it costs 3358 $/wk in HOLD 2025-11..2026-04, costs 3668 $/wk in 2025-07..10 and costs 1103 $/wk in 2024-H2: it is the largest mean cost in the trend regimes and it also adds drawdown in 2025-07..10 (cut -1.2 with it, +16.3 without).

## 2. SIGQ - zone-distance signal-quality gate (JN04 layer 2; FGH family G cell b9a6edabcd7b "qgate dA high 0.3 x0.5", scope ALL books)

**Rule.** dA = distance in points from the signal price (last closed 1-min bar close) to the nearest UNTOUCHED zone line AHEAD of the trade (lines of the live no-trade set: PD_mid, RTH_camH3, Kijun_1h, CRT_mid_4h, KC_up_4h, OTE62_15m, OTE705_15m, OTE79_15m; any distance; no line = no gate). Threshold = the 70th percentile of dA over ALL signals of ALL books in the PREVIOUS calendar months (expanding history, at least 200 past signals before the rule acts; recomputed monthly). **If dA >= threshold (the top 30% of the distribution): multiplier 0.5, else 1.** Frozen-week threshold = 98.7 pts.
**Inputs.** The same PoiSet lines the NTZ layer already tracks, signal price, a monthly-updated quantile of dA.
**DS7 v1.4 fields.** Closest: group 14 SIGNAL-STATE FILTERS (`Ss1Mode..Ss4Mode`, `SsNFeature`, `SsNTemplate` = HalveTop3, `SsMinHistory`): same HalveTop idea, but the feature set (St1Age, St1Dist, Slope, Kelt1, HmaSpread, AtrRatio, PdPos, PdAhead, PdBehind, DayOpenAtr, WeekOpenAtr) has no zone-line distance, and the rank is against the BOOK's own past signals in terciles, not an all-book 70th percentile. **NEW CODE FOR v1.6**: feature `ZoneAheadPts` (from the NTZ PoiSet lines) + a quantile-threshold mode (q = 0.70, pooled across books, monthly refresh); proposed fields `Ss5Mode`=Live, `Ss5Feature`=ZoneAheadPts, `Ss5Template`=HalveTop, `Ss5Quantile`=0.70, `Ss5Books`="" (all), `Ss5PoolBooks`=true.

**Worked example (frozen week, first-order).** P7 London 2026-11-02 05:01 ET long, planned 2 lots, dA = 983.3 pts >= threshold 98.7 -> x0.5 -> 1 lots (actual +-1405 -> about +-702). Caution: on the first live evening (2026-11-01..02) the rebuilt dA reaches 980+ pts (stale-line frame after the weekend), so 66 of 127 live signals clear the threshold; the first-order count on the live week is not reliable and must be verified on the panel with a Shadow print before Live. FIRST-ORDER.

**Exact evidence (table mode).** JD02 = JN04 without SIGQ.

| exact set | what | L6M cut / d mean | HOLD cut / d mean | PRE cut / d mean | X' cut / d mean | GAP 2025-07..10 cut / d mean |
|---|---|---|---|---|---|---|
| JN04 | full JN04 | +43.4 / +4860 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | -1.2 / -7148 |
| JD02 | JN04 minus SIGQ | +44.9 / +4734 | +45.1 / -1602 | n/a / n/a | n/a / n/a | +9.4 / -7211 |

Reading: SIGQ is the weakest layer in the exact runs: removing it changes the L6M cut from +43.4 to +44.9 and L6M d mean from +4860 to +4734; per period it adds 1223 $/wk in HOLD 2025-11..2026-04, costs 1938 $/wk in 2025-H1 and costs 1025 $/wk in 2024-H2. Marginal; the first candidate to drop if a simpler stack is wanted.

## 3. REG - P7 volatility-regime halving (JN04 layer 3; FGH family H cell f1f4301eae70 "regime atr_rel >= 1.3 x0.5", scope P7)

**Rule.** P7 only. atr5 = Wilder ATR(14) on 5-minute bars (value of the last COMPLETED 5-min bar at the signal); base = median over the previous 20 trading days (trading date = 18:00 ET start; at least 5 days) of the daily median of atr5; atr_rel = atr5 / base. **If atr_rel >= 1.3: P7 lot multiplier 0.5, else 1.**
**DS7 v1.4 fields.** `Ss?Feature` = `AtrRatio` exists (DS7.cs line 1104: atrNow / atrMed), but atrNow is a 14-period RMA of 1-MINUTE true range and atrMed the median of the last 28,800 one-minute values, and the templates (SkipBot3 ... HalveTop3) rank by tercile of the book's own history, not a fixed 1.3 threshold. **NEW CODE FOR v1.6**: a 5-minute ATR(14) series, the 20-day median-of-daily-medians base, and a fixed-threshold template `HalveAbove`; proposed fields `Ss6Mode`=Live, `Ss6Books`="P7", `Ss6Feature`=AtrRatio5m, `Ss6Template`=HalveAbove, `Ss6Threshold`=1.3.

**Worked example (frozen week, first-order).** P7 2026-11-01 18:36:00 ET planned 4 lots, atr_rel = 1.62 >= 1.3 -> x0.5 -> 2 lots (actual +4805 -> about +2402). 31 of the 53 P7 signals of the frozen week have atr_rel >= 1.3 (a high-volatility week). FIRST-ORDER.

**Exact evidence (table mode).** JD03 = JN04 without REG.

| exact set | what | L6M cut / d mean | HOLD cut / d mean | PRE cut / d mean | X' cut / d mean | GAP 2025-07..10 cut / d mean |
|---|---|---|---|---|---|---|
| JN04 | full JN04 | +43.4 / +4860 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | -1.2 / -7148 |
| JD03 | JN04 minus REG | +23.1 / +1660 | +38.3 / -1916 | n/a / n/a | n/a / n/a | -6.2 / -4993 |

Reading: REG contributes 20.3 points of the L6M maxDD cut (JN04 +43.4 vs JD03 +23.1) and adds 3200 $/wk in L6M; it costs 2429 $/wk in 2024-H2, costs 2155 $/wk in 2025-07..10 and adds 722 $/wk in HOLD 2025-11..2026-04.

## 4. STACK - same-side lots cap 6, London (JN04 layer 4; SZ-CDE cell E|same_side_lots_cap|cap6_trunc|sess_london, cde code 8)

**Rule.** For a signal of ANY of the seven books whose entry session is London (02:00-08:29 ET): same = total lots currently open (all other books, same side as the signal); room = 6 - same. If the signal's lots (after Q1-A, LOT/SIGQ/REG, zone HALF) exceed room: **lots = room (truncate, rounded, minimum 1); if room <= 0 the signal is SKIPPED.** Parameters P = [cap 6, mode 0 = truncate]; smask = London only, bmask = all books.
**DS7 v1.4 fields.** Closest: group 09 STACK RULE (`StackMode`, `StackCutPct`, `StackAsiaOnly`: a STOPPED book cuts the other same-side books by %): a different trigger (stop event vs a cap at order time). The code that enumerates open same-side books (StackOnStop, DS7.cs line 3090) can be reused. **NEW CODE FOR v1.6**: `ExpCapMode` (Off|Shadow|Live), `ExpCapLots` = 6, `ExpCapSessions` = "0,1,0,0,0,0", `ExpCapBooks` = "" (all), `ExpCapSkipWhenFull` = true (truncate to the room, skip at room <= 0).

**Worked example (frozen week).** 2026-11-04 03:36 ET: K7 signal 1 lot with 6 same-side lots already open -> room 0 -> skipped; P7 signal 4 lots with 3 same-side open -> room 3 -> 3 lots (actual -4,105 -> about -3,079). 2026-11-05 07:58 ET P7 7 lots with 4 open -> room 2 -> 2 lots (actual -4,485 -> about -1,282). Ten London signals of the week would have been truncated or skipped (M7 11-02 02:35, U7 11-02 02:40, K7/P7/M7 11-04 03:36-03:57, M7/P7/K7/M7 11-05). FIRST-ORDER, from the frozen live trades.

**Exact evidence (table mode; rule-mode set JR01 queued).** JD04 = JN04 without STACK.

| exact set | what | L6M cut / d mean | HOLD cut / d mean | PRE cut / d mean | X' cut / d mean | GAP 2025-07..10 cut / d mean |
|---|---|---|---|---|---|---|
| JN04 | full JN04 | +43.4 / +4860 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | -1.2 / -7148 |
| JD04 | JN04 minus STACK | +34.2 / -523 | +37.7 / -3064 | n/a / n/a | n/a / n/a | +4.0 / -6169 |
| JR01 | JN04 with STACK as the engine rule (cde code 8) - RULE MODE | n/a / n/a | n/a / n/a | n/a / n/a | n/a / n/a | n/a / n/a |

Reading: STACK carries the L6M gain (JN04 +43.4 vs JD04 +34.2 L6M cut; d mean +4860 vs -523); in the trend regimes it costs 979 $/wk in 2025-07..10, costs 1123 $/wk in 2024-H2 and adds 536 $/wk in HOLD 2025-11..2026-04. Rule-mode rows (JR01) show whether the table version is a fair proxy for the engine rule.

## 5. JP07 entry - CF_EN_45: P7 engulf confirmation instead of three-bar (R4 cell; JP07 = JN04 + this)

**Rule.** Unchanged hold-the-signal confirmation for P7 in NY-AM and NY-PM (sessions mask 0,0,0,1,1,0), 45-second bars, no minimum dip, no maximum wait; only the PATTERN changes from ThreeBar to **Engulf**: long: the last 45-s bar is up, the previous bar is down, the last close is above the previous open and the last open is below the previous close; short: mirror (DS7.cs line 1648).
**DS7 v1.4 fields - panel values only, no new code (DS7.cs line 447 defaults).** `ConfirmMode` = Live; `ConfirmBooksA` = "P7"; **`ConfirmPatternA` = Engulf (live default ThreeBar)**; `ConfirmTfSecsA` = 45; `ConfirmSessionsA` = "0,0,0,1,1,0"; `ConfirmMinDip` = 0; `ConfirmMaxMinutes` = 0; Slot B unchanged (Off).

**Worked example (frozen week).** The frozen week has 7 P7 entries in NY-AM / NY-PM that go through this hold: 11-02 10:02:15 short 4 lots (-2,865), 11-02 11:51:45 short 2 (+2,400), 11-03 10:20:15 long 4 (-2,745), 11-03 10:46:30 long 4 (+3,600), 11-03 11:57:00 long 3 (+3,605), 11-05 10:39:00 short 5 (+6,000), 11-05 11:04:30 short 5 (+6,000) - each of these would have been held until an ENGULFING 45-s bar prints in its direction instead of the three-bar pattern. A bar-level demonstration from the tape was attempted (45-s bars from the 1-s state arrays) but the bar alignment of NT8 did not reproduce the live three-bar confirmations, so no per-trade pattern verdict is claimed.

**Exact evidence.** JP07 = JN04 + CF_EN_45 (EntryMixin composed; regression JPE0 = JN04 with the empty entry on 202606 and 202610).

| exact set | what | L6M cut / d mean | HOLD cut / d mean | PRE cut / d mean | X' cut / d mean | GAP 2025-07..10 cut / d mean |
|---|---|---|---|---|---|---|
| JN04 | JN04 reference | +43.4 / +4860 | +45.6 / -1456 | +31.4 / -3620 | +68.6 / +2252 | -1.2 / -7148 |
| JP07 | JN04 + CF_EN_45 | +50.1 / +4166 | +56.1 / +465 | +46.9 / -3068 | +65.2 / +2195 | -5.7 / -7967 |

Reading: the entry change adds about +6.7 points of L6M maxDD cut and +10.5 points of HOLD cut and turns the HOLD mean from -1456 to +465 $/wk; it does not repair the 2025-07..10 months (cut -5.7, d mean -7967).

## 6. Status of the stacks under the standing rules (2026-11-10 13:45Z PRE mean floor = 25% of the live PRE mean)

Live weekly means used (ROLLFIX1, carry week dropped): PRE 14408, HOLD 16391, X' 1645, L6M 22949 $/wk. Rule 2a PRE mean floor = -25% x live PRE mean = -3602 $/wk (old fixed floor -1000).

Conditions: R = recents (L6M cut > 0 and L3M cut > -3); H = HOLD cut > 0 and HOLD d mean >= -25% of live HOLD mean (-4098); P = rule 2a PRE label OK-PRIOR (PRE maxDD allowance min(25, L6M cut + 10)% if WF >= 60% else 15%, PRE mean floor -3602); X = X' tolerant (cut > 0, d mean >= -1000); W = contiguous bi-weekly WF 2023-04..2026-10 beat share >= 60%; GAP = 2025-07..10 d mean / cut (reported, not a gate).

| stack | R | H (cut / d mean) | P new label (old) PRE cut / d mean | X (cut / d mean) | W (WF %, full block) | GAP d mean / cut | clears all |
|---|---|---|---|---|---|---|---|
| F08 | yes (26.5 / 26.5) | yes (39.8 / +1922) | OK-PRIOR (RECENT-ONLY) 28.0 / -2063 | yes (52.9 / +2007) | NO (64%, no) | +nan / +nan | no |
| J03 | yes (18.9 / 52.0) | yes (29.2 / -1809) | RECENT-ONLY (RECENT-ONLY) 33.0 / -6170 | yes (72.6 / +3623) | NO (65%, no) | +nan / +nan | no |
| JL01 | yes (29.0 / 29.0) | yes (29.3 / -3207) | RECENT-ONLY (RECENT-ONLY) 37.9 / -4452 | yes (71.3 / +2509) | NO (85%, no) | +nan / +nan | no |
| JN02 | yes (28.8 / 28.8) | yes (12.8 / -1521) | OK-PRIOR (RECENT-ONLY) 36.9 / -3265 | n/a (nan / +nan) | NO (82%, no) | +nan / +nan | no |
| JN03 | yes (39.0 / 39.0) | yes (24.8 / -2593) | OK-PRIOR (RECENT-ONLY) 37.6 / -3107 | yes (68.8 / +2543) | NO (82%, no) | +nan / +nan | no |
| JN04 | yes (43.4 / 43.4) | yes (45.6 / -1456) | RECENT-ONLY (RECENT-ONLY) 31.4 / -3620 | yes (68.6 / +2252) | yes (76%, yes) | -7148 / -1.2 | no |
| JN05 | yes (35.2 / 35.2) | yes (14.9 / -1484) | RECENT-ONLY (RECENT-ONLY) 18.4 / -4001 | n/a (nan / +nan) | NO (70%, no) | +nan / +nan | no |
| JN06 | yes (27.0 / 27.0) | yes (33.7 / -2519) | OK-PRIOR (RECENT-ONLY) 29.4 / -3311 | n/a (nan / +nan) | NO (76%, no) | +nan / +nan | no |
| JP01 | yes (42.6 / 42.6) | yes (49.6 / -2559) | OK-PRIOR (RECENT-ONLY) 41.7 / -3218 | yes (66.2 / +1165) | NO (85%, no) | +nan / +nan | no |
| JP02 | yes (40.4 / 56.6) | yes (29.9 / -3148) | RECENT-ONLY (RECENT-ONLY) 54.2 / -3622 | yes (67.8 / +1147) | NO (84%, no) | +nan / +nan | no |
| JP03 | yes (42.2 / 46.5) | yes (21.9 / -3947) | RECENT-ONLY (RECENT-ONLY) 47.0 / -3713 | yes (69.7 / +419) | NO (80%, no) | +nan / +nan | no |
| JP04 | yes (48.1 / 48.1) | yes (37.6 / -3198) | OK-PRIOR (RECENT-ONLY) 41.7 / -3207 | yes (72.5 / +2451) | yes (81%, yes) | -7945 / +0.6 | YES |
| JP05 | yes (32.2 / 32.2) | yes (27.5 / -1516) | OK-PRIOR (RECENT-ONLY) 31.9 / -2290 | yes (63.0 / +2090) | NO (84%, no) | +nan / +nan | no |
| JP06 | yes (34.6 / 38.7) | NO (31.9 / -6025) | RECENT-ONLY (RECENT-ONLY) 48.6 / -3607 | n/a (nan / +nan) | NO (82%, no) | +nan / +nan | no |
| JP07 | yes (50.1 / 50.1) | yes (56.1 / +465) | OK-PRIOR (RECENT-ONLY) 46.9 / -3068 | yes (65.2 / +2195) | yes (76%, yes) | -7967 / -5.7 | YES |
| JP08 | yes (52.1 / 57.6) | yes (48.1 / -1240) | OK-PRIOR (RECENT-ONLY) 51.9 / -2741 | yes (72.0 / +2281) | yes (75%, yes) | -8764 / -3.8 | YES |

Stacks clearing every condition: JP04, JP07, JP08.



## 7. What is NOT proven / open

- Table mode: the four layers were run as per-signal multiplier tables (STACK from base-trade state); the rule-mode STACK run (JR01) is the confirmation to wait for before the panel build.
- LOT, SIGQ, REG and STACK need new v1.6 code (fields above); only CF_EN_45 is a pure panel change.
- All stacks lose mean in the strong-trend months (2024-H2, 2025-07..10, HOLD), where they also cut no drawdown in 2025-07..10: they are drawdown-for-mean trades that pay off in range / choppy months and in the recent window. Shadow first.
- Live-week numbers are first-order on the frozen file (180 DS7-book rows); the SIGQ live frame needs a panel Shadow check.

