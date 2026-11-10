# DS3_REDO_SUMMARY - T-STACK-REDO rounds R1-R13 in one page (written 2026-11-10 18:10Z by SZ-CORE; refreshed hourly)

**PRE-PROOF; post-hoc; Shadow only; no PASS claims.** Base = S1b-COMB (live D7 v1.5 with the seven state-cut lines), engine ROLLFIX1 where a row says ROLL-FIXED; entries not live-matched (match < .85). STANDING RULES: (1) every layer stays ON, off/no-rule rows are references, the live setting is retained where nothing beats it; (2)/(2a) recents first (L1M/L3M/L6M), bi-weekly re-pick WF is the primary OOS test, PRE/X' tolerant with the allowance min(25, L6M cut + 10)% when the WF beats live in >= 60% of periods else 15%, and the PRE mean floor = 25% of the live PRE mean (live PRE mean $13,961/wk, floor -$3,490/wk; user decision 2026-11-10 13:45Z); (3) exact engine runs decide, first-order is a screen only. The stop fill model is optimistic: ABSOLUTE means are optimistic everywhere; drawdown ranking is the usable output.

## Page status

| round | topic | page | last written | status |
|--|--|--|--|--|
| R1 | Locks (day caps, give-back, week floor, P7MaxDailyLoss) | DS3_REDO_R1_LOCKS.md | 11-10 16:19Z | FINAL DRAFT on disk - FINAL 2026-11-10 16:19Z: exact ROLL |
| R2 | A06 slots, B02 quiet-overnight, StackCut, HM5 bars | DS3_REDO_R2_STACKRULES.md | 11-10 15:19Z | FINAL DRAFT on disk - FINAL (rebuilt 2026-11-10 15:18Z) |
| R2b | StackCut variants (exact) | DS3_REDO_R2b_STACKCUT.md | 11-10 13:57Z | NOT YET FINAL (first version / screen) |
| R3 | Session lot tables per book | DS3_REDO_R3_LOTTABLES.md | 11-10 15:19Z | FINAL DRAFT on disk - FINAL (rebuilt 2026-11-10 15:18Z) |
| R4 | Entry mechanics (split, dip gate, confirmation, PB3B) | DS3_REDO_R4_ENTRY.md | 11-10 15:10Z | FINAL DRAFT on disk - FINAL - entry mechanics re-scored o |
| R5 | Cut-wait / post-cut blackout, NTZ, OTE, O7 | DS3_REDO_R5_CUTWAIT.md | 11-10 14:22Z | FINAL DRAFT on disk - FINAL |
| R6 | Shadow lines (signal-state, X1-X5, flip-level) | DS3_REDO_R6_SHADOW.md | 11-10 16:58Z | NOT YET FINAL (first version / screen) |
| R7 | Stop / target / ATR / time exit per book x session | DS3_REDO_R7_BRACKETS.md | 11-10 15:00Z | FINAL DRAFT on disk - FINAL DRAFT 2026-11-10 15:00Z** - exact L6M + PRE r |
| R8 | Live books own signal parameters | DS3_REDO_R8_SIGNALS.md | 11-10 16:32Z | FINAL DRAFT on disk - FINAL. PRE label per rule 2a as pat |
| R9 | Stop-exit and cut-exit mechanics (stop fill model) | DS3_REDO_R9_STOPEXIT.md | 11-10 17:09Z | NOT YET FINAL (first version / screen) - FINAL (draft status 2026-11-10 17:0 |
| R10 | Direction conflict / netting | DS3_REDO_R10_NETTING.md | 11-10 17:09Z | NOT YET FINAL (first version / screen) - FINAL (draft status 2026-11-10 17:0 |
| R11 | Re-entry after a win / target | DS3_REDO_R11_REENTRY.md | 11-10 17:09Z | NOT YET FINAL (first version / screen) - FINAL (draft status 2026-11-10 17:0 |
| R12 | Session boundaries, blocks, flatten, dow / roll / event days | DS3_REDO_R12_SESSIONS.md | 11-10 15:00Z | FINAL DRAFT on disk - FINAL DRAFT 2026-11-10 15:00Z** - exact L6M + PRE r |
| R13 | Fidelity loop and fill model; installed-panel fidelity (JN04 layers) | DS3_REDO_R13_FIDELITY.md | 11-10 15:11Z | FINAL DRAFT on disk - FINAL version 2026-11-10 15:11Z) |

## One table per round (setting | live value | best exact | holds OOS (recents, HOLD, PRE under the 25% floor, X', WF %) | change recommended? | panel field / v1.6 need). Extracted verbatim from each round page; the page is the source of record.

### R1 - Locks (day caps, give-back, week floor, P7MaxDailyLoss) (DS3_REDO_R1_LOCKS.md)

| setting | live value | best on the state base (first-order screen, equal mean) | holds OOS (dim WF eq cut) | change recommended | panel field |
|--|--|--|--|--|--|
| Day profit / loss caps | +5R / -2R per book | win4_loss1(arm2,keep.5,floor12) P7 (cut +33.7/+19.1/+20.9, d mean +2211) | -10.0 | KEEP the installed P7MaxDailyLoss 8,400 (it is the R1_3 value; better than the DS7.cs default 16,800 on L6M/PRE/X-prime/HOLD, exact) | P7MaxDailyLoss (fixed dollars; DS7.cs CheckLimits: DayPnl <= -MaxDayLoss * max(1, SizeMult)); R1_3 = the installed 8,400 (default 16,800): keep |
| Give-back arm / keep | arm 2R keep 50% | arm1_keep0.7(win5,loss2,floor12) P7 (cut +12.4/+34.1/+5.6, d mean +1823) | +20.5 | candidate for exact; live stays until exact confirms | GiveBackArmR / GiveBackKeepPct |
| Week floor | 12R per book | floor6(win5,loss2,arm2/.5) ALL (cut -4.5/+8.2/+5.5, d mean -521) | -2.5 | no (live stays) | ComboWeekFloorR |
| R basis | base lots | R_on_sized_lots P7 (cut +46.7/+44.6/+26.0, d mean +4488) | -5.2 | candidate for exact; live stays until exact confirms | v1.6 (R on sized lots not a field) |
| Halt scope in time | rest of day | resume_after_4h P7 (cut -17.8/+0.2/+4.0, d mean +335) | -20.4 | no (live stays) | v1.6 code (re-arm after N h / next session) |
| Stack quit-when-up | none (PerBook only) | stack_win$40000(+live pb) ALL (cut -8.4/-3.0/+5.3, d mean -858) | -22.4 | no (live stays) | v1.6 code (LockScope Combined $ cap) |
| Stack day loss cap | none | stack_loss$15000(+live pb) ALL (cut -2.2/-3.7/-4.2, d mean +262) | -47.1 | no (live stays) | v1.6 code |
| Stack give-back | none | stack_arm$45000_keep0.5(+live pb) ALL (cut -7.9/-2.6/+5.7, d mean -746) | +10.7 | no (live stays) | v1.6 code |
| Stack week floor | none | stack_floor$30000(+live pb) ALL (cut +17.1/+15.3/-13.4, d mean -1609) | -7.0 | no (live stays) | v1.6 code |

WF of the picking procedure over the whole R1 grid: OOS maxDD cut +13.3% raw / -12.4% at equal mean (d mean -3797 $/wk, 148 weeks).


Worked examples (today's P7 -20,985 day halt and the K7 give-back halts): those are 2026-11-09 live trades, not in the frozen live file (ends 11-05) and not in the exact lists (end 2026-10); not reproducible here. The frozen-week and the 14 roll days: see the roll-day check below.

### R2 - A06 slots, B02 quiet-overnight, StackCut, HM5 bars (DS3_REDO_R2_STACKRULES.md)

| setting | live value | best on the state base (first-order) | holds OOS? | change? | panel field |
|--|--|--|--|--|--|
| A06 slots (x0.5 half-hours) | K7 0330,0400,0430,0500,0530,1430,1900,1930,2030,2100; P7 0330,0500,0830; U7 0200,0830; H7 0400,0530,0830,1030,1230,1300,1400,1830 | per-book greedy over 48 slots x {0,.5,1}: see below; stack greedy sets 74 slots (mostly x0) | NO: walk-forward of the picking procedure 27% raw, -22% at equal mean, mean -6634$/wk | NO: live slots stay | SlotList per book (x0.5 only in v1.5; x0 slots need v1.6) |
| B02 (quiet overnight, K7/P7/H7 x0.5, 10:30-18:00, lookback 20 d, ratio < .85) | L20 / .85 / x0.5 / 1030-1800 | best by SEL: K7P7H7 L20 thr 1.20 allday x0.0 (size-down of 7888 trades, d mean -2644$/wk) | EXACT: the first-order leads fail the engine; picking-procedure WF (all down-only B02 cells): 23% raw, 21% eq-mean, mean -449$/wk; restricted to the live form (K7P7H7, 10:30-18:00): 3% raw, -2% eq, -780$/wk | NO: live B02 retained. EXACT (ROLLFIX1) FAILS: K7P7H7 L20 thr 1.0 all-day x0 L6M cut -11.8, PRE -20.1; all books L6M -6.7, PRE -17.1 (first-order had said +35/+34) | B02 lookback / threshold / action fields |
| StackCut Asia | 50%, Asia-only, first same-side stop | EXACT (SZ-CDE, DS3_REDO_R2b_STACKCUT.md): best candidate = cut other books on EITHER side after an Asia stop: L6M cut +4.3, d mean +1055, equal-mean +7.7, PRE +0.7 / +284, but worst-20 L6M -8.3 / PRE -11.0 (worse); pct 25/75/100, all-sessions, second-stop variants all deepen L6M maxDD; OFF is -4.5 (reference row only) | no bi-weekly WF available | NO: live retained | StackCutPct, StackAsiaOnly |
| HM5 vs 1/3/15-min for H7 | HM5 | not run (bar-type engine change; no exact set exists) | n/a | NO: live retained, untested | H7 BarMinutes |




<!--FGHFINAL-->

### R2b - StackCut variants (exact) (DS3_REDO_R2b_STACKCUT.md)

| set | variant | L6M maxDD / cut / d mean / (b) / w20 cut / n StackCut | PRE maxDD / cut / d mean / (b) / w20 cut / n StackCut | label |
|--|--|--|--|--|
| CDE_SC_LIVE | live: 50%, Asia-only, first stop, same side | 79907 / +0.0 / +0 / +0.0 / +0.0 / 67 | 140288 / +0.0 / +0 / +0.0 / +0.0 / 141 | LIVE setting |
| CDE_SC_OFF | OFF (reference row only) | 83537 / -4.5 / -4174 / -22.1 / +9.9 / 0 | 138499 / +1.3 / +192 / +2.6 / -3.9 / 0 | reference row only (standing rule: layer stays ON) |
| CDE_SC_P25 | pct 25, Asia-only | 81588 / -2.1 / -235 / -2.9 / +2.0 / 65 | 141031 / -0.5 / +151 / +0.6 / -1.0 / 137 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper +1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_P75 | pct 75, Asia-only | 82817 / -3.6 / -383 / -5.0 / +1.3 / 123 | 138295 / +1.4 / -200 / -0.0 / +1.7 / 223 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_P100 | pct 100, Asia-only | 85764 / -7.3 / -7619 / -45.4 / +4.4 / 179 | 138354 / +1.4 / +117 / +2.2 / +0.9 / 329 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_ALL | 50%, ALL sessions | 90449 / -13.2 / -86 / -13.5 / +5.3 / 151 | 136290 / +2.8 / -1309 / -7.5 / -1.1 / 371 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -3%) [old -1k rule: RECENT-ONLY-UNKNOWN-WF] |
| CDE_SC_AL | 50%, Asia+London | 89829 / -12.4 / -350 / -13.8 / +7.8 / 122 | 136385 / +2.8 / -836 / -3.6 / -0.8 / 247 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -3%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_SECOND | 50%, Asia, only on the 2nd same-side stop within 30 min | 83404 / -4.4 / -4816 / -25.1 / +7.6 / 11 | 142229 / -1.4 / +195 / +0.0 / -3.3 / 26 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper +1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_ANYSIDE | 50%, Asia, cut other books on either side | 76439 / +4.3 / +1055 / +7.7 / -8.3 / 152 | 139276 / +0.7 / +284 / +2.7 / -11.0 / 449 | RECENT-OK / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -1%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |
| CDE_SC_LOTS4 | 50%, Asia, only if other same-side open lots >= 4 | 80100 / -0.2 / -1073 / -4.1 / +2.7 / 28 | 139810 / +0.3 / -151 / -0.8 / -1.1 / 67 | recent: no / OK-PRIOR-UNKNOWN-WF (allow 15%, PRE deeper -0%) [old -1k rule: OK-PRIOR-UNKNOWN-WF] |

### R3 - Session lot tables per book (DS3_REDO_R3_LOTTABLES.md)

| setting | live value | best on the state base (first-order) | holds OOS? | change? | panel field |
|--|--|--|--|--|--|
| K7 SessionLots | 2,2,0,1,2,0 | stack-greedy down: 1,0,0,1,0,0 ; UP: 1,0,0,6,4,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO: live string retained (nothing beats it out of sample) | SessionLots_K7 |
| P7 SessionLots | 7,7,0,7,0,0 | stack-greedy down: 6,3,0,0,0,0 ; UP: 6,5,0,0,0,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk; P7 table cells alone WF 38% raw / 35% eq / -840$/wk | YES for P7: INSTALLED 7,4,0,4,0,0 (EXACT ROLLFIX1: cut L6M 22.5 / HOLD 10.0 / PRE 14.8 / X 18.8 %, d mean L6M +489, PRE -1021 -> RECENT-ONLY by the PRE mean floor; WF 73% beat); 6,4,0,4,0,0 queued exact | SessionLots_P7 |
| M7 SessionLots | 0,2,0,1,0,0 | stack-greedy down: 0,1,0,0,0,0 ; UP: 0,1,0,0,0,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO: live string retained (nothing beats it out of sample) | SessionLots_M7 |
| U7 SessionLots | 4,4,0,0,0,0 | stack-greedy down: 4,0,0,0,0,0 ; UP: 7,2,0,0,0,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO: live string retained (U7 4,4 grid: bi-weekly equal-mean WF beats live in 34% of periods) | SessionLots_U7 |
| A7 SessionLots | 1,0,0,0,0,0 | stack-greedy down: 1,0,0,0,0,0 ; UP: 4,0,0,0,0,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO: live string retained (nothing beats it out of sample) | SessionLots_A7 |
| H7 SessionLots | 4,0,0,1,0,0 | stack-greedy down: 4,0,0,1,0,0 ; UP: 8,0,0,2,0,0 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO: live string retained (nothing beats it out of sample) | SessionLots_H7 |
| O7 SessionLots | 1,1,1,1,1,1 | stack-greedy down: 1,1,1,1,1,1 ; UP: 1,1,1,6,1,1 | stack greedy WF: down 52% raw / 22% eq / -6443$/wk, UP 35% / 38% / +705$/wk | NO: live string retained (nothing beats it out of sample) | SessionLots_O7 |




<!--FGHFINAL-->

### R4 - Entry mechanics (split, dip gate, confirmation, PB3B) (DS3_REDO_R4_ENTRY.md)

| setting | live value | best on the state base | holds OOS? | change recommended | panel field |
|--|--|--|--|--|--|
| split | 70/30 | SP50: L6M cut -0.7% / dmean 4092; HOLD cut 18.4% / dmean 3048; PRE cut 6.5% / dmean 533; WF beat 33% | PRE OK-PRIOR [old fixed-floor: OK-PRIOR; floor 3490], WF 33% | no - live stays (no cell beats the noise floor with support) | L2SplitPct |
| resting offset (min dip) | 3 pts | DIP4: L6M cut -6.6% / dmean 2845; HOLD cut -2.9% / dmean -26; PRE cut 9.4% / dmean 787; WF beat 0% | PRE OK-PRIOR [old fixed-floor: OK-PRIOR; floor 3490], WF 0% | no - live stays (no cell beats the noise floor with support) | L2GateMinDipPts |
| confirmations required | 1 of 8 | REQ2: L6M cut -3.9% / dmean 1535; HOLD cut n/a% / dmean n/a; PRE cut n/a% / dmean n/a; WF beat n/a% | PRE not run (outside reduced scope) | no - live stays (no cell beats the noise floor with support) | L2GateRequired |
| which confirmation (alone) | all 8, 1 needed | ONLY_absorption: L6M cut -4.3% / dmean 2965; HOLD cut n/a% / dmean n/a; PRE cut n/a% / dmean n/a; WF beat n/a% | PRE not run (outside reduced scope) | no - live stays (no cell beats the noise floor with support) | code (GATE list); no panel field |
| stages | 1 | STG2: L6M cut -5.6% / dmean -1751; HOLD cut n/a% / dmean n/a; PRE cut n/a% / dmean n/a; WF beat n/a% | PRE not run (outside reduced scope) | no - live stays (no cell beats the noise floor with support) | L2GateStages / L2GateStageStepPts |
| max minutes | 0 (never) | MAXM15: L6M cut -4.4% / dmean -259; HOLD cut n/a% / dmean n/a; PRE cut n/a% / dmean n/a; WF beat n/a% | PRE not run (outside reduced scope) | no - live stays (no cell beats the noise floor with support) | L2GateMaxMinutes |
| slice size / cadence | 1 lot / 2 s | SLALL: L6M cut -0.0% / dmean 2735; HOLD cut 12.2% / dmean 1955; PRE cut 13.9% / dmean 787; WF beat 33% | PRE OK-PRIOR [old fixed-floor: OK-PRIOR; floor 3490], WF 33% | no - live stays (no cell beats the noise floor with support) | code constant (no panel field) |
| true resting limit | not used (market add) | (not scored: outside the reduced exact scope; first-order cannot see fills) | - | no | new order type, code change |
| add cancelled on exit | cancelled | (not scored: outside the reduced exact scope; first-order cannot see fills) | - | no | code (L2Disarm) |
| P7 PB3B confirm (pattern / tf / sessions / dip / minutes) | three-bar, 45 s, nyam+nypm, dip 0, 0 min | CF_EN_45: L6M cut 13.5% / dmean 1643; HOLD cut 30.6% / dmean 2069; PRE cut 6.2% / dmean 1096; WF beat 67% | PRE OK-PRIOR [old fixed-floor: OK-PRIOR; floor 3490], WF 67% | no - live stays (best cell clears the floor on L6M/PRE/WF but see verdict: neighbours or noise do not support it; Shadow only) | ConfirmPatternA, ConfirmTfSecsA, ConfirmSessionsA, ConfirmMinDip, ConfirmMaxMinutes |

### R5 - Cut-wait / post-cut blackout, NTZ, OTE, O7 (DS3_REDO_R5_CUTWAIT.md)

All "best" values are FIRST-ORDER screens until the exact rows land (section 5); no change is recommended on screens alone.

| setting | live value | best on the state base (screen) | holds OOS? | change recommended | panel field |
|---|---|---|---|---|---|
| post-cut / post-stop blackout (books, minutes, side) | U7, 30 min, same side, on StateCut | N=120 same=both scope=allbooks trig=cut | placebo p 0.27/0.47, family p 1.00, WF ok; EXACT (23 months): cut L6M -26 / PRE 40, equal-mean L6M -74, d mean L6M -6417 | no (screen only; U7 live row changes nothing in the list) | ThL2BlackoutMins / ThL2BlackoutBooks / ThL2BlackoutSameSideOnly (post-stop blackout has no panel field) |
| blackout, single-book best (P7) | none on P7 | N=30 same=same scope=book:P7 trig=cutstop | placebo p 0.14/0.12, family p 1.00, WF ok | no | ThL2BlackoutBooks |
| NTZ action / distance (global) | Half, D 20 | N1 D=60 act=retarget | placebo p 0.30/0.18, family p 1.00, WF ok; EXACT (23 months): cut L6M 7 / PRE -6, equal-mean L6M -21, d mean L6M -5268 | no (UP / optimistic retarget path; exact R5_NTZ_1 decides) | NtzAction / NtzDistancePts |
| Kijun line (timeframe, period, own D / action) | Kijun 1h, 26 periods, D 20 Half | N3 Dk=40 act=skip p=52 tf=4h | placebo p 0.02/0.17, family p 1.00, WF ok | no | none (Kijun definition is in code, not a panel field) |
| OTE-62 band / D / action / max minutes | .62, D 30, B73, 60 | {"D": 10, "act": "WT", "f": 0.65, "maxmin": 15} | placebo p 0.06/0.15, family p 1.00, WF fails; EXACT (23 months): cut L6M 4 / PRE 6, equal-mean L6M 0, d mean L6M -1142 | no | OteMode / OteAction / OteDistancePts / OteMaxMinutes |
| O7 opening drive (arm, trigger, window, stop/target, time exit, lots) | 0.5 x median5, pb1, before 09:45, 40/90, 16:00, 1 lot | lots=1.0 rm=0.5 stop=30 texit=1400 tgt=90 trig=pb1 wend=945 | placebo p 0.18/0.58, family p 1.00, WF ok; EXACT (23 months): cut L6M -1 / PRE 3, equal-mean L6M -1, d mean L6M 23 | no (stack effect < 2 points; O7-only drawdown cells listed) | O7Enabled / O7Qty (the rest is hardcoded in OpenDriveEngine) |
STATUS: post-hoc, Shadow only, no PASS claims, PRE-PROOF (entry match < .85), ROLL-EXCL (33 roll-artifact trades weight 0). Base S1b-COMB (live D7 v1.5 state cut, Q1-A, HALF D20 + OTE-62 B73 D30); carrying week dropped from MEANS only, maxDD / worst-20 / Ulcer on all weeks; windows as of 2026-11-09, trade lists end 2026-10-30. **Every cell below is a FIRST-ORDER SCREEN unless the exact column says EXACT**; exact runs go through the SZ-CORE queue (prefix R5_, tier 2, hooks code/th_r5/r5_hooks.py). Prereg autopilot/R5_PREREG.md (sha in DECISIONS.md). Standing rule: every layer stays ON; the live setting is a reference row; "no rule" never a verdict. Held-out live week = frozen file only; 11-08/09 night v1.5 cuts are bug exits and live NQ cuts are not ground truth, so no live-cut input is used (the live week is used for stop-triggered blackout and O7 only, see section 6).

### R6 - Shadow lines (signal-state, X1-X5, flip-level) (DS3_REDO_R6_SHADOW.md)

| setting | live value | best on the state base | holds OOS? | change recommended | panel field |
|--|--|--|--|--|--|
| Signal-state rule 1 (H7 Slope SkipBot3) | Shadow | H7 Slope HalveBot r=100 q=0.25 (eq-mean cut L6M/PRE/X' 1/1/2, d mean 162 $/wk, placebo p 0.15/0.13) | no: placebo p .15/.13, family p 1.0, H7 WF -2.1% | no | Ss1Mode/Ss1Template |
| Signal-state rule 2 (K7 St1Dist SkipTop3) | Shadow | K7 Slope SkipTop r=200 q=0.25 (eq-mean cut L6M/PRE/X' 7/6/-2, d mean 447 $/wk, placebo p 0.13/0.28) | no (placebo p > .10, family p 1.0) | no | Ss2* |
| Signal-state rule 3 (P7 St1Dist SizeHi) | Shadow (UP cell, never promoted) | P7 Slope SkipTop r=exp q=0.50 (eq-mean cut L6M/PRE/X' 12/33/43, d mean -4098 $/wk, placebo p 0.14/0.17) | partly: P7 WF OOS cut 35% but at -3.0k/wk mean (not equal mean; equal-lots 35%); placebo p .14/.17, family p 1.0 -> no | no | Ss3* |
| Signal-state rule 4 (H7 St1Dist SkipBot3) | Shadow | see H7 table | no | no | Ss4* |
| X1-X5 (2 lots, Shadow, no cut, caps 12000/-4800) | Shadow | best cell X|X4|lots4|K7cell|cap1 (stack cut L6M 2.7, PRE 0.8) | no: the full X set deepens the stack maxDD L6M by 48% | no; keep Shadow | X1Mode..X5Mode |
| Flip-level (break 10, valid 4 h, reach 40, Shadow = skip) | Shadow | brk 15 valid 8h reach 60 skip (eq-mean cut L6M/PRE/X' 12/12/45, d mean 3152; placebo p 0.57/0.80); live cell eq-mean cut 15/14/23, d mean 3461, placebo p 0.23/0.67 | no: mean-type, placebo p > .10 everywhere, family p 1.0 | no (stay Shadow) | FlipMode, FlipBreakPts, FlipValidHours, FlipReachPts |

### R7 - Stop / target / ATR / time exit per book x session (DS3_REDO_R7_BRACKETS.md)

| setting | live value | best on the state base (screen) | holds OOS? | change recommended | panel field |
|---|---|---|---|---|---|
| bracket A7 asia | 60/60 | stop40|R1.75|tx_180m|arm_pct | no (WF beat 27.0 %) | no | policy line `bracket A7 asia ...` |
| bracket H7 asia | 60/60 | stop50|R2.25|tx_none|arm_pts | no (WF beat 44.6 %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket H7 nyam | 60/60 | none eligible | no (WF beat - %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket K7 asia | 60/60 | none eligible | no (WF beat - %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket K7 london | 60/60 | stop80|R1.25|tx_120m|arm_pct | no (WF beat 24.3 %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket K7 nyam | 60/60 | atr5_k4|R0.50|tx_none|arm_pct | no (WF beat 10.8 %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket K7 nypm | 60/60 | none eligible | no (WF beat - %) | no | K7/H7BracketSessions or policy line `bracket` |
| bracket M7 london | 60/60 | atr1_k4|R1.25|tx_180m|arm_pct | no (WF beat 45.9 %) | no | policy line `bracket M7 london ...` |
| bracket M7 nyam | 60/60 | none eligible | no (WF beat - %) | no | policy line `bracket M7 nyam ...` |
| bracket O7 nyam | 40/90 | stop30|R1.25|tx_none|arm_pts | no (WF beat 18.9 %) | no | O7BracketSessions |
| bracket P7 asia | 60/60 | stop40|R1.25|tx_180m|arm_pts | no (WF beat 35.1 %) | no | policy line `bracket P7 asia ...` |
| bracket P7 london | 60/60 | atr1_k2|R2.25|tx_180m|arm_pts | no (WF beat 24.3 %) | no | policy line `bracket P7 london ...` |
| bracket P7 nyam | 60/60 | atr5_k3|R0.50|tx_180m|arm_pct | no (WF beat 12.2 %) | no | policy line `bracket P7 nyam ...` |
| bracket U7 asia | 60/60 | stop40|R1.50|tx_sess|arm_pts | no (WF beat 17.6 %) | no | policy line `bracket U7 asia ...` |
| bracket U7 london | 60/60 | atr1_k1|R1.00|tx_none|arm_pct | no (WF beat 18.9 %) | no | policy line `bracket U7 london ...` |
| state-cut arm vs stop | points held fixed | points | yes (screen) | no | state-cut arm lines (points) |

### R8 - Live books own signal parameters (DS3_REDO_R8_SIGNALS.md)

| setting | live value | best on the state base | holds OOS? | change recommended | panel field |
|---|---|---|---|---|---|
| KB signal (ema 14 / atr 10 / mult 1.0 / 3-min) | ema 14 / atr 10 / mult 1.0 / 3-min | KB_e12_m1.25_b1 (key 8.3, L6M cut at equal mean 7.8 %, d mean -1085 $/wk) | yes; OK-PRIOR; WF 62 % | no | KbEmaPeriod / KbAtrPeriod / KbMult / KbBarMinutes (K7 signal bar) |
| SM signal (atr 7 / mult 3.0 / 10-min) | atr 7 / mult 3.0 / 10-min | SM_a21_m2.0_b5 (key 24.7, L6M cut at equal mean 24.7 %, d mean 2608 $/wk) | yes; OK-PRIOR; WF 51 % | yes (needs exact) | SmAtrPeriod / SmMult / EmBarMinutes (U7 signal bar) |
| HM signal (fast 20 / slow 55 / EMA200 / 5-min / VWAP FixedMidnightUtc4) | fast 20 / slow 55 / EMA200 / 5-min / VWAP FixedMidnightUtc4 | HM_f27_s55_b1_fixed (key 14.8, L6M cut at equal mean 10.7 %, d mean 3322 $/wk) | no (WF/prior gate not met); OK-PRIOR; WF 46 % | no | H7FastPeriod / H7SlowPeriod / H7EmaPeriod / HmVwapAnchor (5-min bucket hard-coded by StackHm5Repl) |
| MV signal (thr 0.5 / votes 4 of 5 (15,30,60,120,240)) | thr 0.5 / votes 4 of 5 (15,30,60,120,240) | MV_t0.75_v3_L5 (spike, not a plateau) (key 2.6, L6M cut at equal mean -1.2 %, d mean -106 $/wk) | no (WF/prior gate not met); OK-PRIOR; WF 51 % | no | MvThreshold / MvVotes (lookback set 15,30,60,120,240 is a constant, MomentumVote L2396) |
| PE signal (regime 5-min / arm 30 / T2 / EMA20) | regime 5-min / arm 30 / T2 / EMA20 | PE_r15_a60_T2_e20 (key 15.3, L6M cut at equal mean -4.4 %, d mean -2071 $/wk) | no (WF/prior gate not met); OK-PRIOR; WF 45 % | no | NONE (Pb3Rules constants in PbEngine L2225: regime bar 5, arm 30, trigger T2, EMA20 level): a new input would be needed |
| PB signal (regime 10-min / arm 15 / depth 0.5 ATR5 / T1) | regime 10-min / arm 15 / depth 0.5 ATR5 / T1 | PB_r5_a10_d0.5_T1 (spike, not a plateau) (key 8.4, L6M cut at equal mean 5.0 %, d mean 781 $/wk) | no (WF/prior gate not met); OK-PRIOR; WF 49 % | no | NONE (Pb7Rules constants: regime bar 10, arm 15, ATR5 depth 0.5, trigger T1): a new input would be needed |
| OD signal (arm 0.5 x median5 / last entry 09:44) | arm 0.5 x median5 / last entry 09:44 | OD_arm1.0_w944 (spike, not a plateau) (key 1.5, L6M cut at equal mean 1.6 %, d mean 165 $/wk) | no (WF/prior gate not met); OK-PRIOR; WF 14 % | no | NONE (arm 0.5 x median5 is a constant in OpenDriveEngine L1298; last-entry minute 09:44) |

### R9 - Stop-exit and cut-exit mechanics (stop fill model) (DS3_REDO_R9_STOPEXIT.md)

The live stop setting stays unless a PRE/X'-complete exact row beats it with the bi-weekly WF. L6M exact: join 5 s one tick inside, catastrophe 10 (R9_J5_i1_c10) cuts maxDD 4.8% at +$297/wk, STRAT0 (strategy-worked market, c10) 4.1%; waits of 10 s HURT (-9%). The native / mode rows (REF_R9_STOP_G0, _NAT: +5.3% / +6.7%, +$967 / +$1,290/wk) are fill-basis artefacts of the optimistic engine native fill (section 1) and are not a recommendation; the installed panel stop-mode per book is the open input. Nothing here is proposed for the panel. (draft generated 2026-11-10 17:09 UTC)

### R10 - Direction conflict / netting (DS3_REDO_R10_NETTING.md)

Take-both (live) stays. (Under the new 25% PRE floor R10_sess_london_SKIP is OK-PRIOR, old floor RECENT-ONLY, but its L6M exact cut is negative and WF 32%.) Exact L6M: SKIP of the newer London signal FAILS (-8.7% maxDD cut, first-order said +4.9%); the opposite-flip exit on all books (R10_ALL_FLIP) is far worse (-31%); NET on newer K7 cuts 5.6% but costs $805/wk; FLIP U7>K7 5.3% at +$37/wk on few events. No policy is promoted; PRE/X' exact rows decide any LEAD. (draft generated 2026-11-10 17:09 UTC)

### R11 - Re-entry after a win / target (DS3_REDO_R11_REENTRY.md)

FULL re-entry (live) stays. Exact: SKIP of a same-side signal within 30 min of ANY book's Target (R11_any_N30_ALL_SKIP) cuts L6M maxDD 19.0% at +$1,481/wk and PRE maxDD 18.5% (PRE d mean -$1,558/wk): OK-PRIOR under the new 25% floor (OLD -$1k floor: RECENT-ONLY). Its bi-weekly WF beats live in only 36% of refit periods, so it is a LEAD (recents + prior ok), not a CANDIDATE; X' and the remaining months are still pending. Own-book N120 and any-book N60 do not hold. Not a panel change. (draft generated 2026-11-10 17:09 UTC)

### R12 - Session boundaries, blocks, flatten, dow / roll / event days (DS3_REDO_R12_SESSIONS.md)

| setting | live value | best on the state base (screen) | holds OOS? | change recommended | panel field |
|---|---|---|---|---|---|
| session flatten | 16:55 | flatten=1700 | no (label LEAD+, WF beat 9 %) | no | flatten time (D7 constant 16:55) |
| asia-open block | 5 min | asia-open block 18:00-18:10 (live 18:05) | no (label no, WF beat 39 %) | no | block 18:00-18:04 (constant) |
| session clock boundaries | asia 18-02 / london -08:30 / nyam -12:00 | asia end 03:00 (removals/lot re-read only) | no (label LEAD+, WF beat 36 %) | no | session clock constants |
| calendar (dow / roll / events) | normal | dow Thu x0 | no (label LEAD+, WF beat 28 %) | no | day-of-week / event lot policy (not in panel) |
| 09:00-09:59 block / Asia guard 15:00-17:59 | block / on | not scored (additions, exact only; 09:00-09:29 and the guard are inert at lots 0) | n/a | no | guard constants |

### R13 - Fidelity loop and fill model; installed-panel fidelity (JN04 layers) (DS3_REDO_R13_FIDELITY.md)

| item | result |
|--|--|
| Data status | **The Monday live CSV is NOT on the box.** data/live/StratTrades_DS7_<acct>.csv is the 2026-11-08 22:05Z sync: last entryTime 2026-11-06 11:36 ET, last P7 exit 2026-11-05 20:28 ET; nothing after 11-05 20:28 ET exists and nothing after was read. The 11-02..11-05 rows of it were reconciled to the frozen reconstruction: all 187 frozen rows are in the unfrozen file with identical qty, times, prices, P&L, exit names (0 differences); 55 other rows lie after 11-05 11:05 ET. |
| (a) Entry match, state base, unconditional | U_main **0.719** (U_nolots 0.736, strict 0.633; 153 matched of 187 live / 174 engine; class A 34, class B 21). Target >= .85: **NOT met**. Same engine with the old per-print cut (what live ran in the blind week): 0.776. Conditional on live exits (C2/C3 diagnostic, ENTRY_MATCH.md): .896 / .914. |
| Why it cannot close on this week | 36 of the 55 unconditional mismatches (A 21 + B 15) are exit-cascade (the engine's state cut exits at other times than the live per-print cut, so books are open/flat at different moments), 12 (A 9 + B 3) are lock states fed by those P&L paths, 7 (A 4 + B 3) raw-signal differences. Closing the cascade alone would give U_nolots .90, cascade+locks .96 (table 1h). The blind-week live cut was a per-print NT8-DOM rule, v1.5 replaced it by the state cut: **the blind week is not a clean unconditional test for the state base; the first clean test is the Monday week (v1.5 live = state cuts), via monday_acceptance.py.** |
| Fixable engine settings found from DS7.cs / panel | none new beyond ENTRY_MATCH F1-F7 (tick close, half-even rounding, X-bar rules, extras held), which are already in the base. Session tables, lots chain, locks, skip slots: planned lots equal live qty in 177 of 184 pairs; no mismatch traced to them. Nothing was fitted to the live week. Open inputs listed in R13_INSTALLED_PANEL.md section 3. |
| (b) Fill drift, entries | engine pays **0.47 pt more** than live on the average entry (n=153, se 0.10); 1-lot market 0.33 (n=80); sliced + 30% add 0.71 (n=51); sliced no add 0.06 (n=9): the drift sits in the add. About $4,226 over the 153 pairs. |
| (b) Fill drift, market cuts | live adverse vs 1-s mid at stamp+1: **0.57 pt** (n=94, se 0.15; stamp+0 1.19, +2 0.59) vs engine model 0.80: the 0.80 basis is 0.23 pt pessimistic (inside ~1.5 se of the prior 0.80+-0.22); about $1,090 on the sample. Recalibrated central value 0.57 +- 0.15 (not applied to the base). |
| (b) Fill drift, targets | resting target at nominal both sides: live distance from own fill average 60.00, engine median difference 0.00 pt; fill second median 0 s (mean +1.9 s, p90 +6.6 s). No slippage to calibrate. |
| (b) Fill drift, stops | **live sample = 2 Stop exits** (K7 -83.00, M7 -80.75 from the entry average: both during the Tue 02:55-08:20 stall at the native 80 catastrophe level, i.e. +3.0 and +0.75 beyond 80) + 3 BookLock market exits. The 2.45-pt figure cannot be re-calibrated from the frozen week (n=2, both in the stall); join exits (`_StopJoin`, `_StopJoinFallback`) n=0 live vs 12 in the engine. Monday's file is the first chance (need >= 20 stops). |
| (c) Monday acceptance | code/th_r13/monday_acceptance.py written and regression-tested on the frozen week (U_main .719, identical to runs/u_comb); hist-week path smoke-tested (2 days, 1.9 GB peak, 19 s); stops cleanly with TAPE_MISSING.txt when the week's tape is absent (it is, for 11-06..11-13). Panel as installed: R13_INSTALLED_PANEL.md. |
| Needs from the user | brackets as installed, policy file text, P7 lot string, join/native stop modes, bug-exit list, DS7.cs v1.5, the week's live CSV + NQ mbp-10 tape (R13_INSTALLED_PANEL.md s3; MORNING_FLAGS.md). |

| ROLLFIX1 base | Entry match and fill tables re-run on the current state base ROLLFIX1 (S1BRF-COMB, base_b_rollfix, SZ_BASE_PROOF s10): ROLLFIX1 flattens positions only at the 14 contract-roll seconds (last roll 2026-09-15, none inside 11-01..11-05); 202610 base_b_rollfix trades are identical to base_b (823 trades, net 47,330.50), so every number of the frozen week is unchanged by ROLLFIX1 (fresh run R13_BLIND_FINAL = u_comb byte for byte). |
| Rule 2a (25% of live PRE mean) | live PRE mean $13,961/wk (Z.live_pre_mean ROLLFIX1), floor -$3,490/wk (Z.prior_info). Only label in R13's scope: the P7 cut 40/5x/w5/p3 (exact PRE maxDD +25.2% deeper, d mean -$1,056/wk, L6M cut +16.9%): mean floor now PASSES (-1,056 > -3,490), maxDD allowance 15% at WF 42-54% (< 60%) and 25% even at WF 70% (25.2 > 25): **RECENT-ONLY** unchanged (old -$1k label also RECENT-ONLY). Fidelity tables themselves carry no rule-2a labels. |
| Stop-fill caveat | every stop figure here is n = 2 (K7 Stop, M7 Stop; both in the Tue stall at the native 80 level) plus 3 BookLock; join fills n = 0. The 2.45-pt basis and the engine's native/join stop model are NOT validated by this week: treat every stop-fill-dependent result (R7, R9, R12, P7 7-lot stops) as using an uncalibrated basis until Monday's file has >= 20 stops. |
| Bug exits | the 10 v1.5 state cuts of 11-08/09 (1 H7 + 9 M7) are outside the frozen week (0 in it); monday_acceptance.py excludes them (panel.bug_*: H7/M7 cut exits, 11-08 18:00..11-09 09:00 ET window, assumed until the list arrives), from exit match, P&L by cause and fill tables, and flags same-book followers. |
| Monday acceptance status | installed panel in panel_installed.json = SZ-CORE LPB_BASE (P7 lots 7,4,0,4,0,0; P7 day cap 42,000 / 8,400; P7 cut 40/5x/w5/p3 from 11-09 20:30Z, v2 45/5x/w5/p10 before; other books S1b-COMB cells incl. H7 nyam override; brackets live 60/60, O7 40/90: **bracket retargets still not given, ask open in MORNING_FLAGS**). Script regression-tested twice on the frozen week; the new-week path runs but stops with TAPE_MISSING: hist day files end 2026-10-30, 1-s state days end 2026-11-05, so the week of 11-08 cannot be engine-run here. The unfrozen data/live DS7 file has a newer sync (mtime 11-09 22:05Z); per the R13 read rule only its 11-02..11-05 rows were used (reconciled, identical to the frozen file) and nothing later was read: running the acceptance on it is one command once the tape exists. |

## Installed-panel fidelity status

See the R13 summary block above (page DS3_REDO_R13_FIDELITY.md) and the JN04 specs: [JN04_LIVE_SPEC.md](JN04_LIVE_SPEC.md) (live panel base: P7 day cap 8,400 + P7 table 7,4,0,4,0,0 + P7 cut 40/5x/w5/p3; JN04 layers SIGQ, REG, LOT cap, STACK), [JN04_SPEC_ATR_SKIP.md](JN04_SPEC_ATR_SKIP.md) (ATR-regime skip), [JN04_SPEC_POSTSTOP_BLACKOUT.md](JN04_SPEC_POSTSTOP_BLACKOUT.md) (P7 post-stop blackout 30 min same side).

## Open items (as of this refresh)

- **Pages not yet FINAL:** see the status table (R6, R8, R13 were being finished at 15:00Z; R4, R9, R10, R11 are first-order screens with exact rows still landing).
- **Exact gaps:** R7_P3 / R12_OPEN930 X' months 202310-202401 (queued at the front); R5 HOLD / X' windows were cut from the exact ask except R5_BO_3; R9-R11 exact rows pending; HOLD / X' months of non-top-1 sets are first-order screens.
- **v1.6 code needed** (not in D7 v1.5): P7 post-chain lot cap (KCAP3), vol-target fields, signal-state / regime / calendar multipliers, equity / day-state sizers, cooldown / chop pauses, book-level performance gates, stop-exit modes; panel fields in each table above.
- **Stop fill model / stop-exit modes (R9):** unresolved; absolute means optimistic; hooks are outside the ROLLFIX1 rebuild.
- **User decisions pending:** see the DECISIONS FOR THE USER box on DS3_SIZER_EXHAUST_FINAL.md (P7 7,4,0,4,0,0 vs cap, P7MaxDailyLoss 8,400, stop-exit mode and fill bias, JN04/JP04 shadow candidate).
- **Refit:** REFIT 2026-11-22 sections are on each FINAL (joint refit; live retained where nothing beats it).
