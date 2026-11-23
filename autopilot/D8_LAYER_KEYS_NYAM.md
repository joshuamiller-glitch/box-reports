# D8_LAYER_KEYS_NYAM - NY AM stack TL3_ALN_NY_STKd8b76ecd35: layer codes of the three joint picks as key = value (order 1125Z)

Written 2026-11-23 16:12Z by W-LAYERS2 by READING the fit/engine code (barefit_gen.py, stackrule_gen.py, layer_gen.py, dl_defs.py, dl_hooks.py, th_ec/ec_hooks.py, th_works_b/wb_ctx.py, th_engfix/ev_panel.py + ev_profit.py, th_nt/wnt_hooks.py, th_redo/state_base_b.py, th_layers/sizer_hooks.py, lay_hooks.py, th_combo/mf_multi.py, replica/sim.py + common.py + ports.py). SPEC = read from code; OPEN = not decidable from the code read here. The Asia page D8_LAYER_KEYS.md holds the shared mechanism text (BookLock, ZONE / PoiSet, sizer, NTS, StackCut rounding, CGB): not repeated here unless NY AM differs.

## 1. MEMBERS / TAGS and brackets as the fit used them (SPEC: events parquet stop_pts / tgt_pts medians; order of the mf_multi streams)
```
MF1 = L8cfda948.BRF90_30    stop 90 pts / target 30 pts ; R per lot = $1800 (stop x $20)
MF2 = Lf0346d55.BRP60    stop 60 pts / target 60 pts ; R per lot = $1200 (stop x $20)
MF3 = L7cc56d99    stop 120 pts / target 120 pts ; R per lot = $2400 (stop x $20)
MF4 = Lbb254083.BRP45    stop 45 pts / target 45 pts ; R per lot = $900 (stop x $20)
MF5 = L8f11883e.BRF30_90    stop 30 pts / target 90 pts ; R per lot = $600 (stop x $20)
median book R (STK, BL not) = median(stops 90,60,120,45,30) = 60 pts x $20 = $1,200 per lot x lots
entries: all five books enter 09:30-11:59 ET only (event ts), engine session code 3 (replica/common.py session_index: 09:30-12:00 ET = 3); session-flat exit per the book sets
```

## 2. THE THREE PICKS resolved for THIS stack (factor = code ; description as the fit prints it for that book at that lot basis)
### lot basis 1  =  set TL3_SR_NY_STKd8b76ecd35_BF1_JT22
```
LOSS.MF1 = CU3    # loss cut when unrealised <= -72 pts (0.8 x stop)
LOCK.MF1 = LK1    # lock at 50% -> stop to entry+0 pts
TAKE.MF1 = TK2    # take at 50% of target after 15 s without a new extreme
ZONE.MF1 = OFF
LOSS.MF2 = CX3    # context cut (fresh) at -48 pts
LOCK.MF2 = OFF
TAKE.MF2 = TK6    # take at 65% of target after 30 s without a new extreme
ZONE.MF2 = OFF
LOSS.MF3 = CU4    # loss cut when unrealised <= -120 pts (1.0 x stop)
LOCK.MF3 = LK5    # lock at 65% -> stop to entry+10 pts
TAKE.MF3 = FR_TAKE6    # W-FASTR pick: lock 80% -> +30
ZONE.MF3 = ZONE2    # zone no-trade set MF3 Half within 30 pts
LOSS.MF4 = OFF
LOCK.MF4 = OFF
TAKE.MF4 = SHV2    # target shave MF4 4 ticks
ZONE.MF4 = ZONE5    # zone no-trade set MF4 Skip within 30 pts
LOSS.MF5 = STC3    # state-cut cell MF5 mult 5.0
LOCK.MF5 = LK8    # lock at 80% -> stop to entry+10 pts
TAKE.MF5 = OFF
ZONE.MF5 = ZONE6    # zone no-trade set MF5 Skip within 50 pts
SC = OFF
BL = BL1    # BookLock arm 1.5R give-back 33%
CAP = CAP2    # per-book day profit stop +7.5R ($9000)
STK = OFF
DLA = DLA5    # per-book day loss halt at -3R (open P&L counts, close the position, halt rest of session)
DLB = OFF
DLC = DLC2    # per-book halt after 3 consecutive full-stop losses (rest of session)
```
### lot basis 2  =  set TL3_SR_NY_STKd8b76ecd35_BF2_JT68
```
LOSS.MF1 = CU2    # loss cut when unrealised <= -54 pts (0.6 x stop)
LOCK.MF1 = LK1    # lock at 50% -> stop to entry+0 pts
TAKE.MF1 = OFF
ZONE.MF1 = ZONE6    # zone no-trade set MF1 Skip within 50 pts
LOSS.MF2 = CX1    # context cut (fresh) at -24 pts
LOCK.MF2 = OFF
TAKE.MF2 = TK1    # take at 50% of target after 5 s without a new extreme
ZONE.MF2 = ZONE2    # zone no-trade set MF2 Half within 30 pts
LOSS.MF3 = CU4    # loss cut when unrealised <= -120 pts (1.0 x stop)
LOCK.MF3 = OFF
TAKE.MF3 = OFF
ZONE.MF3 = ZONE3    # zone no-trade set MF3 Half within 50 pts
LOSS.MF4 = CU4    # loss cut when unrealised <= -45 pts (1.0 x stop)
LOCK.MF4 = LK7    # lock at 80% -> stop to entry+0 pts
TAKE.MF4 = SHV2    # target shave MF4 4 ticks
ZONE.MF4 = OFF
LOSS.MF5 = OFF
LOCK.MF5 = LK8    # lock at 80% -> stop to entry+10 pts
TAKE.MF5 = FR_TAKE4    # W-FASTR pick: lock 80% -> +10
ZONE.MF5 = ZONE4    # zone no-trade set MF5 Skip within 20 pts
SC = OFF
BL = BL1    # BookLock arm 1.5R give-back 33%
CAP = OFF
STK = STK3    # WHOLE-STACK day profit stop +8R of one book ($19200)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS1    # no-trade-set halving 0.5 (today's rule)
DLA = OFF
DLB = DLB6    # stack day loss halt at -$8000 per lot per book (open P&L counts, all books halted, positions closed, rest of session)
DLC = DLC10    # per-book pause 120 min after 3 consecutive full-stop losses, then re-arm
```
### lot basis 4  =  set TL3_SR_NY_STKd8b76ecd35_BF4_JT15
```
LOSS.MF1 = OFF
LOCK.MF1 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF1 = SHV1    # target shave MF1 2 ticks
ZONE.MF1 = ZONE6    # zone no-trade set MF1 Skip within 50 pts
LOSS.MF2 = CX1    # context cut (fresh) at -24 pts
LOCK.MF2 = LK6    # lock at 65% -> stop to entry+20 pts
TAKE.MF2 = TK6    # take at 65% of target after 30 s without a new extreme
ZONE.MF2 = OFF
LOSS.MF3 = OFF
LOCK.MF3 = OFF
TAKE.MF3 = FR_TAKE6    # W-FASTR pick: lock 80% -> +30
ZONE.MF3 = ZONE3    # zone no-trade set MF3 Half within 50 pts
LOSS.MF4 = STC2    # state-cut cell MF4 arm 60.0
LOCK.MF4 = OFF
TAKE.MF4 = OFF
ZONE.MF4 = OFF
LOSS.MF5 = STC1    # state-cut cell MF5 arm 30.0
LOCK.MF5 = LK8    # lock at 80% -> stop to entry+10 pts
TAKE.MF5 = SHV2    # target shave MF5 4 ticks
ZONE.MF5 = ZONE4    # zone no-trade set MF5 Skip within 20 pts
SC = SC2    # StackCut share 50% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots)
BL = BL7    # BookLock arm 3.0R give-back 33%
CAP = CAP1    # per-book day profit stop +5R ($24000)
STK = STK1    # WHOLE-STACK day profit stop +4R of one book ($19200)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = OFF
DLA = OFF
DLB = OFF
DLC = DLC10    # per-book pause 120 min after 3 consecutive full-stop losses, then re-arm
```
Stack-level $ at each basis (R = median book R x lots): STK thresholds = k x R, e.g. STK1 = +4R = $4,800 per lot, STK3 = +8R = $9,600 per lot; CAP uses EACH BOOK's own R per lot (MF1 $1,800, MF2 $1,200, MF3 $2,400, MF4 $900, MF5 $600) x lots: CAP1 = per-book day PROFIT stop +5R, CAP2 = +7.5R (loss side OFF); BL1 = [arm 1.5R, give-back 33%, weekly -12R]; BL7 = [arm 3.0R, give-back 33%, weekly -12R] (R = base lots x max(1,size_mult) x the book's own stop x $20) ; SC2 = StackCut share 50% ; SZW3 = ER(20) of 5-minute closes < 0.40 -> lots x 0.5 half-up min 1 (lots > 1 only) ; NTS1 = no-trade-set halving 0.5 (>= 2 lots) ; DLA5 = per-book daily loss halt at -3R ; DLB6 = stack daily loss halt at -$8,000 per lot per book (DLB list 2000/3000/4000/5000/6000/8000/10000/12000: index 6 = 8,000) ; DLC2 = halt a book for the rest of the day after 3 consecutive full-stop losses (DLC1-4 = N 2/3/4/5) ; DLC10 = same N = 3 with a 120-minute pause instead of the rest of the day (DLC5-8 pause 60 min N 2-5, DLC9-12 pause 120 min N 2-5). Code lists: Asia page section 2-3 and dl_defs.py.

## 3. MECHANISMS NOT NEEDED FOR ASIA (SPEC unless marked)
```
(a) CX context cut (fresh): rule ec_hooks kind flat p.d = round(f x book stop, 1) with ctx [fresh]; CX1 f 0.4, CX2 0.6, CX3 0.8 (NY AM: MF2 stop 60 -> 24 / 36 / 48 pts; MF3 stop 120 -> 48 / 72 / 96). CONTEXT (th_works_b/wb_ctx.py + ec_hooks._ec_state), computed ONCE per trade when the first cut check runs, from the SIGNAL second sg of the entry: session start t0 = the start of the ET clock block containing sg (0 Asia 18:00, 1 London 02:00, 2 pre-open 08:30, 3 NY AM 09:30, 4 midday 12:00, 5 PM 15:00); ck (chase_k) = (close of the last 1-minute bar at or before sg - open of the 1-minute bar at t0) x side / ATR5rel(sg), where ATR5 = Bars5.atr_rel(sg)[0] = the ATR(14) Wilder of 5-MINUTE bars of NQ 1-minute data (bars closed left / labelled left, roll gaps > 120 pts between consecutive 1-minute bars within 5 minutes removed by back-adjustment, seed = mean of the first 14 true ranges then (13 x prev + TR)/14), value of the last 5-minute bar COMPLETED at or before the signal second (must be within 15 min), in POINTS (not the relative ratio; th_r13/r13_rules.py Bars5); the 1-minute opens / closes are the engine's NQ 1-minute state bars (_th_state/s345/nq1m_state.npz); chasing = ck > 1.0; n = 1 + number of THIS book's earlier entries with t0 <= entry < sg; gap = minutes since this book's last exit at or before sg (inf if none); context = chasing if chasing, else fresh if n <= 2 and gap >= 30, else reentry. A CX rule is active only when context = fresh. Evaluation (same as CU): on the 1-second state tape (closed second rows), x = side x (mid[r] - entry_px); fires on the first row r with x <= -d; exit event at row r+1: market exit at mid[r+1] - side x 0.80 pt (slip), exit name EarlyCut; once per trade. Reset: the context is recomputed for every new trade (per entry).
(b) STC state cut (ev_panel cut_tl cell {arm, mult, win, pers, newmae, var}; engine th_redo/state_base_b.py): decision on the closed 1-second state tape rows, per trade from the row of the entry second: un = side x (mid[r] - entry_px); ext = running minimum of un (<= 0), last_ext = the row where ext was last set; condition at row r = (-un >= arm_eff) AND (med[r] > 0) AND (pulled >= mult x med[r]) AND (not newmae OR r - last_ext <= win); pulled = sum over the last win seconds of the CANCELLED size on the side of the book that is adverse to the position (canc_bid for a long, canc_ask for a short: state tape arrays canc_bid / canc_ask, cumulative-sum difference over win rows); med = the state tape's per-second reference size = an EWMA (alpha 0.001 per second, restarted at a contract change, carried across days) of x = (sum of the top-5 bid sizes + the top-5 ask sizes) / 10 (average displayed size per level over 10 levels; th_state/th_state.py kern_ewma + build_day); canc_bid / canc_ask of a second = the sum over the 10 levels of the size that disappeared at a level's price compared with the previous second's size and the traded size at that price (d = prev size - current size - traded size, only d > 0 counted; levels whose price fell out of the 10-level depth are ignored; th_state.py kern_cancel); fire when the condition has held on pers CONSECUTIVE rows (run counter reset to 0 on any row that fails); arm_eff by var: 0 = arm ; 1 = min(50, max(15, arm x sqrt(4/q))) ; 2 = min(50, max(15, arm x sqrt(q/4))), q = lots of the position (max 1). Base cell arm 45 / mult 10 / win 2 / pers 3 / newmae 0 / var 2 (the live K7 cell); STC1 arm 30, STC2 arm 60, STC3 mult 5, STC4 mult 15 (other fields at base). Exit: decision at the end of second r, market exit at the end of second r+1 at mid[r+1] - side x 0.80 pt, exit name StateCut; the bracket orders are cancelled at the exit; once per trade.
(c) LK vs FR_TAKE lock vs TK (th_engfix/ev_profit.py): LK1-9 and FR_TAKE4-6 are THE SAME mechanism: a SOFTWARE lock level, not a resting stop order. At each CLOSED second (state tape mid of the last closed second, only rows at or after the entry second): pct = side x (mid - entry_px) / target distance; target distance = the live target distance (TG par not set here: abs(target_px - entry_px), else stop x target_r); when pct >= th the level lvl = round((entry_px + side x X) x 4) / 4 (quarter-point) is set (tighten only, each rule once); on EVERY print: if the print is at or through the level (long: px <= lvl, short: px >= lvl) -> request_exit market, exit name PolicyTrail. LK: th 0.50/0.65/0.80 with X 0/+10/+20 pts (LK1 50%/+0, LK2 50%/+10, LK5 65%/+10, LK6 65%/+20, LK7 80%/+0, LK8 80%/+10). FR_TAKE4 = lock at 80% of the target -> level entry +10 pts, FR_TAKE5 = +20, FR_TAKE6 = +30 pts (same engine rule, th 0.80); FR_TAKE1 = take 50% after 30 s, FR_TAKE2 = take 95% after 30 s, FR_TAKE3 = take 95% after 20 s. TK (take, TK1-12 = pct 50/65/80/95% x secs 5/15/30): per print, at most once per ThEvalFrequencySecs: last-print unrealised >= pct x live target distance AND seconds since the favourable extreme >= secs (strict new extreme resets the clock) -> market exit PolicyTake. TK1 = 50% / 5 s, TK2 = 50% / 15 s, TK6 = 65% / 30 s. SHV1/SHV2 (target shave, th_nt/wnt_hooks): the resting target limit order is placed k = 2 / 4 ticks nearer the entry (0.5 / 1.0 pt); the nominal target stays the denominator of the pct rules.
(d) DAILY LOSS family as used in this joint (code/th_layers/dl_hooks.py, no engine edit): "day" = the engine's session key m_sesskey = the GLOBEX TRADING DAY rolling at 18:00 ET (sim.py L140): for NY AM books that trade 09:30-12:00 the day is that morning; b.day_pnl = realised P&L of the day net of commissions (session_base reset at the 18:00 ET roll). Open P&L COUNTS: day = day_pnl + (px - entry) x side x lots x $20 of the open position, the check runs inside the engine's check_book_lock call, which on_print makes at most once every 2 seconds (the first print after 2 s) for every book whose BookLock has not fired, and once per 1-minute bar in check_limits (px = last 1-minute close). DLA5 = per-book halt when the book's day P&L <= -3 R (R = base lots x max(1,size_mult) x ITS stop x $20): closes the open position (market, exit name DayHalt, a name without "Stop" so StackCut does not fire) and halts the book until the 18:00 ET roll (b.day_halt lifted at the roll). DLB6 = stack halt when the SUM over the five books of (day P&L + open P&L) <= -$8,000 x lots-per-book: every book halted, open positions closed (DayHalt), until the roll. DLC2 = after 3 consecutive FULL-STOP LOSSES of a book (closed trade whose exit name contains Stop and not StackCut, net P&L < 0; either side counts; any other close - target, cut, lock exit, time exit, DayHalt, BookLock - or a stop with a profit resets the run to 0; counter per book, reset at the roll) the book is halted for the rest of the day (nothing is open at that moment). DLC10 = same trigger, N = 3, but only a 120-minute pause of new entries of that book (after the pause the run counter restarts at 0). Pause variants re-arm from the day P&L at the firing. All four are in the NY picks as listed in section 2.
(e) SZW3 for NY AM: the same hook (th_layers/sizer_hooks.py) and the same MARKET-LEVEL ER: ER(20) of the 5-minute closes (s.trend_er(), the same value for every book, not per-book bars); SZW3 = thr 0.40, lo 0.50: when ER < 0.40 and lots > 1: lots = max(1, floor(lots x 0.5 + 0.5)) (half up); NaN ER (warm-up) = no cut; inert at 1 lot; applied inside the entry no-trade check BEFORE the zone / no-trade-set step.
(f) StackCut on the NY AM stack: SC2 = share 50% with stackcut_sessions = [3] (stackrule_gen sets SCODE 3 for NYAM): the rule fires when a book that ENTERED in session 3 (09:30-12:00 ET: all five NY AM books, 100% of their events) is stopped by a full stop (exit name Stop, not StackCut): every OTHER book in a trade on the SAME side is cut by q = ceil(position x 0.5 - 1e-9), min 1 lot (q >= position -> the whole position exits, exit name StackCut); at 1 lot the whole position, at 4 lots 2 of 4. So YES it acts on NY AM books in this fit (the "scope Asia-only" text in the page line is the label of the Asia builder). STK / CAP R: STK R = median book R = $1,200 x lots ($4,800 x lots for +4R); CAP R = each book's own stop x $20 x lots (above).
(g) ZONE for NY AM: the same lay_hooks.zone code and PoiSet (PD_mid, RTH_camH3, Kijun_1h, CRT_mid_4h, KC_up_4h, OTE62/705/79_15m) and the same entry price (s.last1m_close = close of the last COMPLETED 1-minute bar at the decision) as Asia; ZONE2..6 = dist 30 Half / 50 Half / 20 Skip / 30 Skip / 50 Skip (ZONE1 = 10 Half); the target used in min(dist, target) is the book's own target pts (MF1 30, MF2 60, MF3 120, MF4 45, MF5 90): so a ZONE on MF1 (target 30) tests lines within min(dist, 30) pts. Half = lots x 0.5 half-up min 1 (inert at 1 lot); engine default action: Half after 2026-11-02 08:50 ET (Skip before it when PERIODS on).
```

## 4. HOOK ORDER AND PRECEDENCE (SPEC; the two OPEN items of 1125Z resolved)
```
class chain: the engine builds the class by looping the set hooklist in written order, each make_rep wrapping the previous: a LATER entry is OUTER and its method runs FIRST. Hooklist of the NY picks as built (barefit_gen shells then joint edits in factor order): swb_inject2 x7 (live books off) , ec_hooks, ev_panel, ev_profit, mf_multi, then lay_hooks (first ZONE or STK edit), sizer_hooks (SZW), dl_hooks (DLA / DLB / DLC, appended last = OUTERMOST). (the old c_gov hook is not in these sets; CGB was not a factor of the NY joint.)
ENTRY (try_entry): dl_hooks.try_entry (pause gate: skip the signal while a pause is running) -> mf_multi / engine try_entry (disabled / inTrade / exitPending / dayHalt / weekHalt checks, then l2arm -> trend_size -> ntz_check) ; ntz_check order: sizer_hooks (SZW: lots x 0.5 when ER < thr) -> lay_hooks.zone (a ZONE setting REPLACES the inner no-trade-set check for that book: Skip drops the signal, Half halves lots) -> mf_multi no-trade-set (NTS1: lots x 0.5 half-up when a level is within min(20, target) ahead and lots >= 2; books without a ZONE setting). A halted book (b.day_halt / week_halt) is dropped by the engine at try_entry.
IN THE TRADE (per print): the engine's own order flow (bracket stop and target orders, executed through the event queue) , then manage_th_l2 hooks: ev_profit (LK lock check, takes through policy), ec_hooks (CU/CX decision on the closed 1-second rows, exit one row later), state cut (StateCut; closed rows), wnt_hooks (latch exits, shave), check_book_lock chain: dl_hooks.check_book_lock = (BookLock of mf_multi lin first, then the daily-loss check), and once per 1-minute bar check_limits (own caps, stack caps, daily-loss).
PRECEDENCE (sim.py on_print, RESOLVED 2026-11-23): per print the order is (1) resting bracket orders (stop / target) see the print first (match_resting); (2) policy_poll and the L2 arming; (3) per book that has no exit pending: manage_th_l2 = the base engine logic, then the hooks' own parts from the INNERMOST hook outward (ec_hooks CU/CX registers its exit EVENT for the next second, the state cut likewise, ev_profit LK lock = immediate request_exit PolicyTrail on the first print through the level, wnt latch), then manage_policy (PolicyTake) only if no exit is pending; (4) every >= 2 s: check_book_lock for each book: BookLock (mf_multi lin) first, then the daily-loss check of dl_hooks; (5) once per 1-minute bar: check_limits (own caps, stack caps, daily-loss). request_exit / exec_exit carry the guard 'not in trade or exit pending: return', so the FIRST rule to ask wins and names the exit; the second-based exits (EarlyCut, StateCut) are events executed at the next second row and are skipped if an exit is pending or a stop is triggered by then. So on one print: bracket fill > LK lock exit > (cuts at the next second) > PolicyTake > BookLock > DayHalt.
```

## 6. WILL THE PICKS CHANGE (SPEC from the procedure)
The null does NOT change a pick: the joint pick is the best of the 80 combinations per lot basis on L6M ulcer inside the 15% guards; the 1-lot screen null and the controls only label it (gate: real beats >= 4 of 5 null draws; the 5-book Asia result was 3 of 5 = FAIL). The NY AM null files exist (finalset TL3_ALN_NY_STKd8b76ecd35); the run is queued behind the London joint and the Asia daily-loss work: ETA after ~23:00Z (about 9,150 rows, ~3 h at the stack share). The daily-loss family IS inside this joint (DLA, DLB, DLC were factors with their top-2 screened levels, 27 / 29 / 29 factors), so the joint answers order 0640Z for NY AM with the screen's two best levels per group; it is NOT final in two respects: (1) the other levels / variants of the 46 were not in the OA (only the top-2 per group), and (2) the order's second screen "on top of the delivered pick" was not run for NY. A small refinement is cheap (46 settings x 6 months x 3 lots ON TOP of each NY pick ~ 830 rows, ~15-20 min of the share): it can change ONLY the DLA / DLB / DLC lines of the picks; proposed, not queued yet.
