# D8_LAYER_KEYS - layer setting codes of the truly-bare all-layers fit, as key = value (order 2140Z)

Written 2026-11-22 21:24Z by W-LAYERS2 by READING the fit/engine code (code/th_layers/barefit_gen.py, stackrule_gen.py, layer_gen.py, lay_hooks.py, sc_hooks.py, sizer_hooks.py, zone2_hooks.py, th_combo/mf_multi.py, th_works_c/c_gov.py + gov_lib.py, replica/ports.py PoiSet, replica/sim.py). No compute, nothing invented. SPEC = read from engine/fit code; OPEN = not decidable from the code read here. Stack = TL3_ALN_AS_STKd8106b26ef. Units: points, ticks (0.25 pt), dollars at $20 per NQ point per lot, R = see section 6.

## 0. THE 4-LOT JOINT PICK BF4_JT1 (panel defaults; set TL3_SR_AS_STKd8106b26ef_BF4_JT1) - factor = code (a factor shown as OFF is not in the pick, i.e. that layer is not applied; SPEC)
```
LOSS.MF1 = CU4    # loss cut when unrealised <= -40 pts (1.0 x stop)
LOCK.MF1 = OFF
TAKE.MF1 = SHV2    # target shave MF1 4 ticks
ZONE.MF1 = ZONE5    # zone no-trade set MF1 Skip within 30 pts
LOSS.MF2 = OFF
LOCK.MF2 = LK9    # lock at 80% -> stop to entry+20 pts
TAKE.MF2 = NRT1    # near-target latch MF2 X 0.90 stale 10
ZONE.MF2 = OFF
LOSS.MF3 = CU2    # loss cut when unrealised <= -36 pts (0.6 x stop)
LOCK.MF3 = LK7    # lock at 80% -> stop to entry+0 pts
TAKE.MF3 = OFF
ZONE.MF3 = ZONE6    # zone no-trade set MF3 Skip within 50 pts
LOSS.MF4 = CU3    # loss cut when unrealised <= -48 pts (0.8 x stop)
LOCK.MF4 = OFF
TAKE.MF4 = NRT4    # near-target latch MF4 X 0.95 givep 0.1
ZONE.MF4 = ZONE3    # zone no-trade set MF4 Half within 50 pts
LOSS.MF5 = OFF
LOCK.MF5 = LK5    # lock at 65% -> stop to entry+10 pts
TAKE.MF5 = TK8    # take at 80% of target after 15 s without a new extreme
ZONE.MF5 = OFF
SC = SC2    # StackCut share 50% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots)
BL = BL2    # BookLock arm 1.5R give-back 50%
CAP = OFF
STK = STK4    # WHOLE-STACK day profit stop +12R of one book ($57600)
SZW = SZW2    # ER sizer (new-book hook) ER(20,5m) < 0.30 -> lots x 0.50, half-up, min 1
NTS = OFF
CG = CG1    # CG1 IS A NO-OP in this pick: c_gov governed tag P7 only (fix in progress, W-LAYERS2 21:30Z): CG NOT FITTED on new books until done
```
Notes on this pick (SPEC unless marked): (a) CG1 has NO EFFECT as built: the c_gov hook of the stack set has no gov_book parameter, so it governs tag P7 only (c_gov.py default gov_book = P7) and none of the new books MF1..MF5: every CG row of the fit reads d ulcer +0 / d $ +0; CG1 in this pick is a no-op (OPEN for the build: either leave off or have a real new-book skip-after-losses rule fitted). (b) The 4-lot basis scales each book's events x4 (lots x4); every dollar rule below is value x lots through R (section 6). (c) Layers that are OFF here: LOSS.MF2 (J502), LOSS.MF5, LOCK.MF1, LOCK.MF4, TAKE.MF3, ZONE.MF2, ZONE.MF5, CAP, NTS. (d) The best joint of the 1-lot and 2-lot bases are different combos (BF1_JT57, BF2_JT19): see D8_LAYER_DEFAULTS_ASIA.md.

## 1. MEMBERS / TAGS (SPEC, from the set JSON mf_multi streams; question 3 CONFIRMED)
```
MF1 = Lb0e6dfa3.BRF40_80    stop 40 pts (median of the events' stop_pts) ; R per lot = $800 ; events _brkt/ev/Lb0e6dfa3_R0_F40_80.parquet
MF2 = L385f4f2e.J502    stop 60 pts (median of the events' stop_pts) ; R per lot = $1200 ; events _pass2/jev/L385f4f2e_CX502.parquet
MF3 = L92a90948    stop 60 pts (median of the events' stop_pts) ; R per lot = $1200 ; events _d8spec/ev/L92a90948_CANC.parquet
MF4 = L6b373671.BRP60    stop 60 pts (median of the events' stop_pts) ; R per lot = $1200 ; events _brkt/ev/L6b373671_R0_P60.parquet
MF5 = L578701ed.BRF30_90    stop 30 pts (median of the events' stop_pts) ; R per lot = $600 ; events _brkt/ev/L578701ed_R0_F30_90.parquet
```
Order of the streams in mf_multi = MF1..MF5 = the assumed order (CONFIRMED). Each stream carries its own day cap pair cap = [profit, loss] = [12000, 4800] in the set but OFF (1e12) in the truly bare base.

## 2. PER-BOOK TRADE HEALTH AND ZONE CODES (factor = LOSS.MFn / LOCK.MFn / TAKE.MFn / ZONE.MFn; every code below has the same numbers for each book except stop-scaled ones)
```
CU1..CU4  = flat loss cut: exit when unrealised <= -(f x book stop) pts, f = 0.4 / 0.6 / 0.8 / 1.0 ; rule ec_hooks kind flat p.d = round(f x stop,1) ; MF1 (stop 40): 16/24/32/40 pts ; MF2,MF3,MF4 (stop 60): 24/36/48/60 ; MF5 (stop 30): 12/18/24/30 ; SPEC (CU4 = at the full stop: acts as no extra cut)
CX1..CX3  = same as CU but only when the trade context is FRESH (rule ctx [fresh]); f = 0.4 / 0.6 / 0.8 x stop ; SPEC (context definition: see AUTO:LAYERS row CX in D8_BUILD_SPEC.md)
STC1..STC4 = state cut cell {arm, mult, win, pers, newmae, var} on ev_panel cut_tl, base cell arm 45 / mult 10 / win 2 / pers 3 / newmae 0 / var 2 (the live K7 cell); STC1 arm 30 ; STC2 arm 60 ; STC3 mult 5 ; STC4 mult 15 (other fields at base) ; SPEC (mechanism text: AUTO:LAYERS row STC)
FR_LOSS7 = no-follow-through: exit if unrealised < +10 pts after 20 min ; FR_LOSS8 = same with < +5 pts after 20 min ; FR_LOSS9 = scratch: after reaching -45 pts adverse, exit at -5 ; SPEC (kinds nft p{X,N} / scratch p{d,s})
LK1..LK9  = lock: at each closed second if unrealised >= pct x target distance, move the stop to entry + X pts (tighten only): LK1 50%/+0, LK2 50%/+10, LK3 50%/+20, LK4 65%/+0, LK5 65%/+10, LK6 65%/+20, LK7 80%/+0, LK8 80%/+10, LK9 80%/+20 ; ev_profit locks[tag] = [[pct, X]] ; SPEC
TK1..TK12 = take: if last-print unrealised >= pct x live target distance AND secs since the favourable extreme >= secs -> market exit: TK1 50%/5s, TK2 50%/15s, TK3 50%/30s, TK4 65%/5s, TK5 65%/15s, TK6 65%/30s, TK7 80%/5s, TK8 80%/15s, TK9 80%/30s, TK10 95%/5s, TK11 95%/15s, TK12 95%/30s ; ev_profit takes[tag] = [pct, secs] ; SPEC
NRT1..NRT4 = near-target latch (wnt_hooks latch): NRT1 X 0.90 stale 10 s ; NRT2 X 0.95 stale 20 s ; NRT3 X 0.90 give 8.0 pts ; NRT4 X 0.95 givep 0.10 (x target) ; after the favourable extreme reached X x target: exit (market) when no new extreme for stale seconds / price gave back give pts / givep x target from the extreme ; SPEC
SHV1..SHV3 = target shave: resting target limit order k ticks nearer the entry: 2 / 4 / 8 ticks (0.5 / 1.0 / 2.0 pts) ; nominal target is still used for pct denominators ; SPEC
FR_TAKE1..FR_TAKE6 = FR_TAKE1 take 50%/30 s ; FR_TAKE2 take 95%/30 s ; FR_TAKE3 take 95%/20 s ; FR_TAKE4 lock 80% -> +10 ; FR_TAKE5 lock 80% -> +20 ; FR_TAKE6 lock 80% -> +30 ; SPEC
ZONE1..ZONE6 = per-book no-trade set (lay_hooks zone, replaces the engine's own no-trade-set check for that book): ZONE1 dist 10 pts Half ; ZONE2 30 Half ; ZONE3 50 Half ; ZONE4 20 Skip ; ZONE5 30 Skip ; ZONE6 50 Skip ; Half = lots x 0.5 rounded half up, min 1 (INERT at 1 lot) ; Skip = signal dropped ; SPEC
ZT (zone-type variants by line class, zone2_hooks) were NOT in the screen or joint of this fit (env ZTYPE off): not part of any pick here ; SPEC
BRK (bracket) is NOT varied in this fit ; SPEC
```

## 3. STACK-LEVEL CODES (factor = SC / BL / CAP / STK / SZW / NTS / CG; the fit uses the lin form of mf_multi because the stack basis is lots = max(2, median lots): SPEC)
```
SC1 = StackCut share 25% ; SC2 = 50% ; SC3 = 100% of the OTHER same-side open positions when a book is STOPPED; q = ceil(pos x share - 1e-9), min 1 lot; q >= pos -> whole position exits (exit name StackCut), else q lots by market order after LAT_FILL ; fires only when the stopped book ENTERED in Asia (stackcut_sessions [0]) ; at 4 lots SC2 cuts 2 of 4 ; 100% = whole position ; SPEC (mf_multi.stack_on_stop lin)
BL1..BL12 = BookLock per book in the lin form lin.bl = [arm_R, give_back, weekly_R]: BL1 [1.5, 0.33, -12] ; BL2 [1.5, 0.50, -12] ; BL3 [1.5, 0.67, -12] ; BL4 [2.0, 0.33, -12] ; BL5 [2.0, 0.50, -12] (= today's D7) ; BL6 [2.0, 0.67, -12] ; BL7 [3.0, 0.33, -12] ; BL8 [3.0, 0.50, -12] ; BL9 [3.0, 0.67, -12] ; BL10 [2.0, 0.50, -8] ; BL11 [2.0, 0.50, -12] ; BL12 [2.0, 0.50, -16] ; SPEC
CAP1..CAP4 = per-book day PROFIT stop at +5 / +7.5 / +10 / +15 R (own loss stop OFF) ; CAP5..CAP8 = per-book day LOSS stop at -2 / -3 / -4 / -6 R (own profit stop OFF) ; DayHalt: the book is halted for the day and an open position exits ; R = THAT book's own stop pts x $20 x its lots (see section 6: the dollar figure printed on the page uses the median book, the engine uses each book's own R) ; SPEC (stackrule_gen.caps_R, lots=0 mode)
STK1..STK4 = WHOLE-STACK day PROFIT stop at +4 / +6 / +8 / +12 R (loss side OFF) ; STK5..STK8 = WHOLE-STACK day LOSS stop at -3 / -4 / -6 / -8 R (profit side OFF) ; when the SUM of the day P&L of all 5 books reaches it, every book is day-halted and exits (DayHalt) ; R here = median over the five books of (stop x $20 x lots) = $1,200 x lots ; STK4 = 12R = $14,400 per lot ; SPEC (lay_hooks stack_caps)
SZW1 = ER sizer: ER(20) of 5-minute closes < 0.20 -> lots x 0.50 ; SZW2 = ER < 0.30 -> lots x 0.50 (= D7's thresholds) ; SZW3 = ER < 0.40 -> lots x 0.50 ; SZW4 = ER < 0.30 -> lots x 0.75 ; SZW0 = identity (thr 0) ; ER = market-level, the same for every book (s.trend_er(), NOT per-book bars) ; applies only when lots > 1 ; rounding max(1, floor(lots x lo + 0.5)) (half up) ; NaN ER (warm-up) = no cut ; applied in the entry no-trade check BEFORE the zone / no-trade-set step ; SPEC (sizer_hooks.py). SZW2 at 4 lots: 4 -> 2 when ER < 0.30.
NTS1 = engine no-trade-set with halving 0.5 (today's D7 rule): when a level (PoiSet line) lies ahead of the entry within min(20 pts, target), lots = max(1, floor(lots x 0.5 + 0.5)); fires only when it changes the lots (>= 2 lots) ; NTS2 = no-trade-set rule dropped entirely (neither halving nor Skip) ; the truly bare base keeps ntz_share 1.0 (rule present, no halving) ; applies to books WITHOUT a ZONE setting (a ZONE setting replaces this check for its book, section 5) ; SPEC (mf_multi.ntz_check lin). Needs >= 2 lots.
CG1..CG3 = c_gov skip after n = 1 / 2 / 3 same-side losses: rule when {sess [0,1,3,4], loss_same_ge n, noevid 1} act skip: skip the signal when the book already has >= n same-side LOSING closes in the same label-day session AND noevid = 1 (last exit was a same-side loss and no new session extreme in the trade direction beyond the extreme at that exit, no opposite-side entry in between) ; AS BUILT IN THIS FIT THE HOOK GOVERNS ONLY TAG P7 (gov_book default) = NO EFFECT on MF1..MF5 ; SPEC for the rule text, and the no-effect finding is SPEC from c_gov.py (par without gov_book)
```

## 4. BOOKLOCK (question 2; SPEC, mf_multi.check_book_lock lin)
```
per book, evaluated each time the book is checked while it is in a trade (price update): day = day P&L + unrealised ; week = week P&L + unrealised ; day peak gb_peak = max over the day of day (the book's own peak)
WEEKLY FLOOR: if weekly_R is not None and week <= weekly_R_value x R  (weekly_R is stored negative: -12) -> book locked for the day AND the week (week_halt), open position exits (exit name BookLock)
GIVE-BACK LOCK: elif day peak >= arm_R x R and day <= peak x (1 - give_back) -> book locked for the day, open position exits (BookLock)
so "give-back 33%" means the book is halted when it has GIVEN BACK 33% of its day peak, i.e. day P&L <= 0.67 x peak (NOT day <= 0.33 x peak); 50%: day <= 0.5 x peak; 67%: day <= 0.33 x peak
weekly floor ON in BL1 and BL2 (and BL3-BL9): -12 R of the book; BL10 -8 R, BL11 -12 R, BL12 -16 R; the bare base has the lock OFF (lin.bl = [None, 0.5, None])
R = base lots x max(1, size_mult) x stop pts x $20 (the book's own stop; size_mult = the sizer multiplier of the day, 1.0 unless the sizer set it > 1)
BL2 = arm 1.5 R, give-back 50%, weekly floor -12 R (the 4-lot pick): halt when day peak >= 1.5 R and day <= 0.5 x peak, or week <= -12 R
```

## 5. ZONES IN THE FIT (question 4)
```
line set = the live DS7 PoiSet as ported in replica/ports.py (docstring "PoiSet L1881"): PD_mid, RTH_camH3, Kijun_1h, CRT_mid_4h, KC_up_4h, OTE62_15m, OTE705_15m, OTE79_15m ; CONFIRMED (SPEC): the engine builds s.poi = PT.PoiSet() and feeds it from 1-minute bars (s.poi.bar1m) and 15-minute bars (s.poi.bar15m); the ZONE settings use ALL lines
bars: 1-minute bars stamped at their END (B = bar end ns; hhmm / hour = ET of the bar end; day grouping key = the Globex-day key passed by the caller) ; 15-minute bars: h, l and close_ns from the engine's 15m bars ; SPEC (docstring + sim.py L785, L821)
PD_mid = (high + low)/2 of the PREVIOUS Globex day ; RTH_camH3 = RTH close + 1.1 x (RTH high - RTH low)/4, set when RTH (09:30-16:00 ET bars) ends ; Kijun_1h = (max of the last 26 completed hourly highs + min of the 26 lows)/2 ; CRT_mid_4h = (high+low)/2 of the last completed 4-hour bucket (buckets start 18:00 ET: slot = ((hour-18+24)%24)//4) ; KC_up_4h = EMA20 of 4h closes (first value = mean of the first 20) + 2 x mean of the last 10 true ranges of 4h bars ; OTE62/705/79_15m: 5-bar fractals on 15-minute bars (strictly higher/lower than 2 neighbours each side), keep the last 3 swing highs and 3 swing lows, H3 = max of the 3 highs, L3 = min of the 3 lows, if H3 - L3 >= 4: line = L3 + 0.62 / 0.705 / 0.79 x (H3 - L3) ; SPEC
fresh = not touched: a line is Touched when a later 1-minute bar (t > the bar that formed/changed the line) has low <= Px <= high; a line whose Px changes becomes untouched again; touched lines are ignored ; SPEC
entry price used by the "ahead" test = s.last1m_close = the CLOSE OF THE LAST COMPLETED 1-MINUTE BAR at the time of the entry decision (set in the 1-minute bar handler), NOT the last print ; SPEC (sim.py ntz_check: entry = s.last1m_close)
"ahead within min(dist, target)": d = (line Px - entry) x side; counts when 0 < d <= min(dist, tgt), tgt = the trade's target pts if > 0 else stop pts x target_r; the NEAREST such line is the one reported; ZONE settings use dist = 10 / 20 / 30 / 50 as above; SPEC
action: Skip = signal dropped; Half = lots x 0.5 rounded half up, min 1 (a ZONE setting replaces the engine's default no-trade-set check for that book: lay_hooks.ntz_check does not call the inner check when it has a ZONE entry for the tag); the engine default (no ZONE setting) = same lines, dist 20, action = ntz_action(now) = Half after P1_START (OPEN: the action before P1_START and its exact time, read s.ntz_action)
hook order: later-appended hooks wrap earlier ones (the builders append lay_hooks and sizer_hooks last); the sizer acts first, then zone / no-trade-set (OPEN: confirm the chain order in the engine runner if bit-exact parity of sizer-then-zone is needed)
```

## 6. DOLLAR RULES AT N LOTS (question 5)
```
CONFIRMED with one correction: every dollar value scales as value-per-lot x lots, but R differs by rule: 
STK (whole-stack) R = MEDIAN over the five books of (stop pts x $20 x lots) = $1,200 x lots at stops 40/60/60/60/30 (median 60); STK4 = +12R of one book = $14,400 per lot (page: $57,600 at 4 lots = 12 x 1,200 x 4) ; SPEC
CAP (per-book day stops) use EACH BOOK'S OWN R = its stop pts x $20 x lots (MF1 $800, MF2-4 $1,200, MF5 $600 per lot): the dollar amount printed on the fit page for CAP rows uses the median R, the engine applies the per-book R ; the port must use per-book R ; SPEC (stackrule_gen.caps_R)
BookLock R = base lots x max(1, size_mult) x the book's own stop pts x $20 (per book) ; SPEC
caps in the truly bare base are OFF (1e12); in the lin form lots scale the events (lots column x N) and the R scales with it ; SPEC
```

## 7. EXPANDED PER-BOOK CODES (generated from the builders at the 4-lot basis; description strings as printed by the fit)
```
LOCK.MF1.LK1 = lock at 50% -> stop to entry+0 pts
LOCK.MF1.LK2 = lock at 50% -> stop to entry+10 pts
LOCK.MF1.LK3 = lock at 50% -> stop to entry+20 pts
LOCK.MF1.LK4 = lock at 65% -> stop to entry+0 pts
LOCK.MF1.LK5 = lock at 65% -> stop to entry+10 pts
LOCK.MF1.LK6 = lock at 65% -> stop to entry+20 pts
LOCK.MF1.LK7 = lock at 80% -> stop to entry+0 pts
LOCK.MF1.LK8 = lock at 80% -> stop to entry+10 pts
LOCK.MF1.LK9 = lock at 80% -> stop to entry+20 pts
LOCK.MF2.LK1 = lock at 50% -> stop to entry+0 pts
LOCK.MF2.LK2 = lock at 50% -> stop to entry+10 pts
LOCK.MF2.LK3 = lock at 50% -> stop to entry+20 pts
LOCK.MF2.LK4 = lock at 65% -> stop to entry+0 pts
LOCK.MF2.LK5 = lock at 65% -> stop to entry+10 pts
LOCK.MF2.LK6 = lock at 65% -> stop to entry+20 pts
LOCK.MF2.LK7 = lock at 80% -> stop to entry+0 pts
LOCK.MF2.LK8 = lock at 80% -> stop to entry+10 pts
LOCK.MF2.LK9 = lock at 80% -> stop to entry+20 pts
LOCK.MF3.LK1 = lock at 50% -> stop to entry+0 pts
LOCK.MF3.LK2 = lock at 50% -> stop to entry+10 pts
LOCK.MF3.LK3 = lock at 50% -> stop to entry+20 pts
LOCK.MF3.LK4 = lock at 65% -> stop to entry+0 pts
LOCK.MF3.LK5 = lock at 65% -> stop to entry+10 pts
LOCK.MF3.LK6 = lock at 65% -> stop to entry+20 pts
LOCK.MF3.LK7 = lock at 80% -> stop to entry+0 pts
LOCK.MF3.LK8 = lock at 80% -> stop to entry+10 pts
LOCK.MF3.LK9 = lock at 80% -> stop to entry+20 pts
LOCK.MF4.LK1 = lock at 50% -> stop to entry+0 pts
LOCK.MF4.LK2 = lock at 50% -> stop to entry+10 pts
LOCK.MF4.LK3 = lock at 50% -> stop to entry+20 pts
LOCK.MF4.LK4 = lock at 65% -> stop to entry+0 pts
LOCK.MF4.LK5 = lock at 65% -> stop to entry+10 pts
LOCK.MF4.LK6 = lock at 65% -> stop to entry+20 pts
LOCK.MF4.LK7 = lock at 80% -> stop to entry+0 pts
LOCK.MF4.LK8 = lock at 80% -> stop to entry+10 pts
LOCK.MF4.LK9 = lock at 80% -> stop to entry+20 pts
LOCK.MF5.LK1 = lock at 50% -> stop to entry+0 pts
LOCK.MF5.LK2 = lock at 50% -> stop to entry+10 pts
LOCK.MF5.LK3 = lock at 50% -> stop to entry+20 pts
LOCK.MF5.LK4 = lock at 65% -> stop to entry+0 pts
LOCK.MF5.LK5 = lock at 65% -> stop to entry+10 pts
LOCK.MF5.LK6 = lock at 65% -> stop to entry+20 pts
LOCK.MF5.LK7 = lock at 80% -> stop to entry+0 pts
LOCK.MF5.LK8 = lock at 80% -> stop to entry+10 pts
LOCK.MF5.LK9 = lock at 80% -> stop to entry+20 pts
LOSS.MF1.CU1 = loss cut when unrealised <= -16 pts (0.4 x stop)
LOSS.MF1.CU2 = loss cut when unrealised <= -24 pts (0.6 x stop)
LOSS.MF1.CU3 = loss cut when unrealised <= -32 pts (0.8 x stop)
LOSS.MF1.CU4 = loss cut when unrealised <= -40 pts (1.0 x stop)
LOSS.MF1.CX1 = context cut (fresh) at -16 pts
LOSS.MF1.CX2 = context cut (fresh) at -24 pts
LOSS.MF1.CX3 = context cut (fresh) at -32 pts
LOSS.MF1.FR_LOSS7 = W-FASTR pick: no-follow-through: < +10 pts after 20 min
LOSS.MF1.FR_LOSS8 = W-FASTR pick: no-follow-through: < +5 pts after 20 min
LOSS.MF1.FR_LOSS9 = W-FASTR pick: scratch: after -45 exit at -5
LOSS.MF1.STC1 = state-cut cell MF1 arm 30.0
LOSS.MF1.STC2 = state-cut cell MF1 arm 60.0
LOSS.MF1.STC3 = state-cut cell MF1 mult 5.0
LOSS.MF1.STC4 = state-cut cell MF1 mult 15.0
LOSS.MF2.CU1 = loss cut when unrealised <= -24 pts (0.4 x stop)
LOSS.MF2.CU2 = loss cut when unrealised <= -36 pts (0.6 x stop)
LOSS.MF2.CU3 = loss cut when unrealised <= -48 pts (0.8 x stop)
LOSS.MF2.CU4 = loss cut when unrealised <= -60 pts (1.0 x stop)
LOSS.MF2.CX1 = context cut (fresh) at -24 pts
LOSS.MF2.CX2 = context cut (fresh) at -36 pts
LOSS.MF2.CX3 = context cut (fresh) at -48 pts
LOSS.MF2.FR_LOSS7 = W-FASTR pick: no-follow-through: < +10 pts after 20 min
LOSS.MF2.FR_LOSS8 = W-FASTR pick: no-follow-through: < +5 pts after 20 min
LOSS.MF2.FR_LOSS9 = W-FASTR pick: scratch: after -45 exit at -5
LOSS.MF2.STC1 = state-cut cell MF2 arm 30.0
LOSS.MF2.STC2 = state-cut cell MF2 arm 60.0
LOSS.MF2.STC3 = state-cut cell MF2 mult 5.0
LOSS.MF2.STC4 = state-cut cell MF2 mult 15.0
LOSS.MF3.CU1 = loss cut when unrealised <= -24 pts (0.4 x stop)
LOSS.MF3.CU2 = loss cut when unrealised <= -36 pts (0.6 x stop)
LOSS.MF3.CU3 = loss cut when unrealised <= -48 pts (0.8 x stop)
LOSS.MF3.CU4 = loss cut when unrealised <= -60 pts (1.0 x stop)
LOSS.MF3.CX1 = context cut (fresh) at -24 pts
LOSS.MF3.CX2 = context cut (fresh) at -36 pts
LOSS.MF3.CX3 = context cut (fresh) at -48 pts
LOSS.MF3.FR_LOSS7 = W-FASTR pick: no-follow-through: < +10 pts after 20 min
LOSS.MF3.FR_LOSS8 = W-FASTR pick: no-follow-through: < +5 pts after 20 min
LOSS.MF3.FR_LOSS9 = W-FASTR pick: scratch: after -45 exit at -5
LOSS.MF3.STC1 = state-cut cell MF3 arm 30.0
LOSS.MF3.STC2 = state-cut cell MF3 arm 60.0
LOSS.MF3.STC3 = state-cut cell MF3 mult 5.0
LOSS.MF3.STC4 = state-cut cell MF3 mult 15.0
LOSS.MF4.CU1 = loss cut when unrealised <= -24 pts (0.4 x stop)
LOSS.MF4.CU2 = loss cut when unrealised <= -36 pts (0.6 x stop)
LOSS.MF4.CU3 = loss cut when unrealised <= -48 pts (0.8 x stop)
LOSS.MF4.CU4 = loss cut when unrealised <= -60 pts (1.0 x stop)
LOSS.MF4.CX1 = context cut (fresh) at -24 pts
LOSS.MF4.CX2 = context cut (fresh) at -36 pts
LOSS.MF4.CX3 = context cut (fresh) at -48 pts
LOSS.MF4.FR_LOSS7 = W-FASTR pick: no-follow-through: < +10 pts after 20 min
LOSS.MF4.FR_LOSS8 = W-FASTR pick: no-follow-through: < +5 pts after 20 min
LOSS.MF4.FR_LOSS9 = W-FASTR pick: scratch: after -45 exit at -5
LOSS.MF4.STC1 = state-cut cell MF4 arm 30.0
LOSS.MF4.STC2 = state-cut cell MF4 arm 60.0
LOSS.MF4.STC3 = state-cut cell MF4 mult 5.0
LOSS.MF4.STC4 = state-cut cell MF4 mult 15.0
LOSS.MF5.CU1 = loss cut when unrealised <= -12 pts (0.4 x stop)
LOSS.MF5.CU2 = loss cut when unrealised <= -18 pts (0.6 x stop)
LOSS.MF5.CU3 = loss cut when unrealised <= -24 pts (0.8 x stop)
LOSS.MF5.CU4 = loss cut when unrealised <= -30 pts (1.0 x stop)
LOSS.MF5.CX1 = context cut (fresh) at -12 pts
LOSS.MF5.CX2 = context cut (fresh) at -18 pts
LOSS.MF5.CX3 = context cut (fresh) at -24 pts
LOSS.MF5.FR_LOSS7 = W-FASTR pick: no-follow-through: < +10 pts after 20 min
LOSS.MF5.FR_LOSS8 = W-FASTR pick: no-follow-through: < +5 pts after 20 min
LOSS.MF5.FR_LOSS9 = W-FASTR pick: scratch: after -45 exit at -5
LOSS.MF5.STC1 = state-cut cell MF5 arm 30.0
LOSS.MF5.STC2 = state-cut cell MF5 arm 60.0
LOSS.MF5.STC3 = state-cut cell MF5 mult 5.0
LOSS.MF5.STC4 = state-cut cell MF5 mult 15.0
TAKE.MF1.FR_TAKE1 = W-FASTR pick: take 50%/30 s
TAKE.MF1.FR_TAKE2 = W-FASTR pick: take 95%/30 s
TAKE.MF1.FR_TAKE3 = W-FASTR pick: take 95%/20 s
TAKE.MF1.FR_TAKE4 = W-FASTR pick: lock 80% -> +10
TAKE.MF1.FR_TAKE5 = W-FASTR pick: lock 80% -> +20
TAKE.MF1.FR_TAKE6 = W-FASTR pick: lock 80% -> +30
TAKE.MF1.NRT1 = near-target latch MF1 X 0.90 stale 10
TAKE.MF1.NRT2 = near-target latch MF1 X 0.95 stale 20
TAKE.MF1.NRT3 = near-target latch MF1 X 0.90 give 8.0
TAKE.MF1.NRT4 = near-target latch MF1 X 0.95 givep 0.1
TAKE.MF1.SHV1 = target shave MF1 2 ticks
TAKE.MF1.SHV2 = target shave MF1 4 ticks
TAKE.MF1.SHV3 = target shave MF1 8 ticks
TAKE.MF1.TK1 = take at 50% of target after 5 s without a new extreme
TAKE.MF1.TK2 = take at 50% of target after 15 s without a new extreme
TAKE.MF1.TK3 = take at 50% of target after 30 s without a new extreme
TAKE.MF1.TK4 = take at 65% of target after 5 s without a new extreme
TAKE.MF1.TK5 = take at 65% of target after 15 s without a new extreme
TAKE.MF1.TK6 = take at 65% of target after 30 s without a new extreme
TAKE.MF1.TK7 = take at 80% of target after 5 s without a new extreme
TAKE.MF1.TK8 = take at 80% of target after 15 s without a new extreme
TAKE.MF1.TK9 = take at 80% of target after 30 s without a new extreme
TAKE.MF1.TK10 = take at 95% of target after 5 s without a new extreme
TAKE.MF1.TK11 = take at 95% of target after 15 s without a new extreme
TAKE.MF1.TK12 = take at 95% of target after 30 s without a new extreme
TAKE.MF2.FR_TAKE1 = W-FASTR pick: take 50%/30 s
TAKE.MF2.FR_TAKE2 = W-FASTR pick: take 95%/30 s
TAKE.MF2.FR_TAKE3 = W-FASTR pick: take 95%/20 s
TAKE.MF2.FR_TAKE4 = W-FASTR pick: lock 80% -> +10
TAKE.MF2.FR_TAKE5 = W-FASTR pick: lock 80% -> +20
TAKE.MF2.FR_TAKE6 = W-FASTR pick: lock 80% -> +30
TAKE.MF2.NRT1 = near-target latch MF2 X 0.90 stale 10
TAKE.MF2.NRT2 = near-target latch MF2 X 0.95 stale 20
TAKE.MF2.NRT3 = near-target latch MF2 X 0.90 give 8.0
TAKE.MF2.NRT4 = near-target latch MF2 X 0.95 givep 0.1
TAKE.MF2.SHV1 = target shave MF2 2 ticks
TAKE.MF2.SHV2 = target shave MF2 4 ticks
TAKE.MF2.SHV3 = target shave MF2 8 ticks
TAKE.MF2.TK1 = take at 50% of target after 5 s without a new extreme
TAKE.MF2.TK2 = take at 50% of target after 15 s without a new extreme
TAKE.MF2.TK3 = take at 50% of target after 30 s without a new extreme
TAKE.MF2.TK4 = take at 65% of target after 5 s without a new extreme
TAKE.MF2.TK5 = take at 65% of target after 15 s without a new extreme
TAKE.MF2.TK6 = take at 65% of target after 30 s without a new extreme
TAKE.MF2.TK7 = take at 80% of target after 5 s without a new extreme
TAKE.MF2.TK8 = take at 80% of target after 15 s without a new extreme
TAKE.MF2.TK9 = take at 80% of target after 30 s without a new extreme
TAKE.MF2.TK10 = take at 95% of target after 5 s without a new extreme
TAKE.MF2.TK11 = take at 95% of target after 15 s without a new extreme
TAKE.MF2.TK12 = take at 95% of target after 30 s without a new extreme
TAKE.MF3.FR_TAKE1 = W-FASTR pick: take 50%/30 s
TAKE.MF3.FR_TAKE2 = W-FASTR pick: take 95%/30 s
TAKE.MF3.FR_TAKE3 = W-FASTR pick: take 95%/20 s
TAKE.MF3.FR_TAKE4 = W-FASTR pick: lock 80% -> +10
TAKE.MF3.FR_TAKE5 = W-FASTR pick: lock 80% -> +20
TAKE.MF3.FR_TAKE6 = W-FASTR pick: lock 80% -> +30
TAKE.MF3.NRT1 = near-target latch MF3 X 0.90 stale 10
TAKE.MF3.NRT2 = near-target latch MF3 X 0.95 stale 20
TAKE.MF3.NRT3 = near-target latch MF3 X 0.90 give 8.0
TAKE.MF3.NRT4 = near-target latch MF3 X 0.95 givep 0.1
TAKE.MF3.SHV1 = target shave MF3 2 ticks
TAKE.MF3.SHV2 = target shave MF3 4 ticks
TAKE.MF3.SHV3 = target shave MF3 8 ticks
TAKE.MF3.TK1 = take at 50% of target after 5 s without a new extreme
TAKE.MF3.TK2 = take at 50% of target after 15 s without a new extreme
TAKE.MF3.TK3 = take at 50% of target after 30 s without a new extreme
TAKE.MF3.TK4 = take at 65% of target after 5 s without a new extreme
TAKE.MF3.TK5 = take at 65% of target after 15 s without a new extreme
TAKE.MF3.TK6 = take at 65% of target after 30 s without a new extreme
TAKE.MF3.TK7 = take at 80% of target after 5 s without a new extreme
TAKE.MF3.TK8 = take at 80% of target after 15 s without a new extreme
TAKE.MF3.TK9 = take at 80% of target after 30 s without a new extreme
TAKE.MF3.TK10 = take at 95% of target after 5 s without a new extreme
TAKE.MF3.TK11 = take at 95% of target after 15 s without a new extreme
TAKE.MF3.TK12 = take at 95% of target after 30 s without a new extreme
TAKE.MF4.FR_TAKE1 = W-FASTR pick: take 50%/30 s
TAKE.MF4.FR_TAKE2 = W-FASTR pick: take 95%/30 s
TAKE.MF4.FR_TAKE3 = W-FASTR pick: take 95%/20 s
TAKE.MF4.FR_TAKE4 = W-FASTR pick: lock 80% -> +10
TAKE.MF4.FR_TAKE5 = W-FASTR pick: lock 80% -> +20
TAKE.MF4.FR_TAKE6 = W-FASTR pick: lock 80% -> +30
TAKE.MF4.NRT1 = near-target latch MF4 X 0.90 stale 10
TAKE.MF4.NRT2 = near-target latch MF4 X 0.95 stale 20
TAKE.MF4.NRT3 = near-target latch MF4 X 0.90 give 8.0
TAKE.MF4.NRT4 = near-target latch MF4 X 0.95 givep 0.1
TAKE.MF4.SHV1 = target shave MF4 2 ticks
TAKE.MF4.SHV2 = target shave MF4 4 ticks
TAKE.MF4.SHV3 = target shave MF4 8 ticks
TAKE.MF4.TK1 = take at 50% of target after 5 s without a new extreme
TAKE.MF4.TK2 = take at 50% of target after 15 s without a new extreme
TAKE.MF4.TK3 = take at 50% of target after 30 s without a new extreme
TAKE.MF4.TK4 = take at 65% of target after 5 s without a new extreme
TAKE.MF4.TK5 = take at 65% of target after 15 s without a new extreme
TAKE.MF4.TK6 = take at 65% of target after 30 s without a new extreme
TAKE.MF4.TK7 = take at 80% of target after 5 s without a new extreme
TAKE.MF4.TK8 = take at 80% of target after 15 s without a new extreme
TAKE.MF4.TK9 = take at 80% of target after 30 s without a new extreme
TAKE.MF4.TK10 = take at 95% of target after 5 s without a new extreme
TAKE.MF4.TK11 = take at 95% of target after 15 s without a new extreme
TAKE.MF4.TK12 = take at 95% of target after 30 s without a new extreme
TAKE.MF5.FR_TAKE1 = W-FASTR pick: take 50%/30 s
TAKE.MF5.FR_TAKE2 = W-FASTR pick: take 95%/30 s
TAKE.MF5.FR_TAKE3 = W-FASTR pick: take 95%/20 s
TAKE.MF5.FR_TAKE4 = W-FASTR pick: lock 80% -> +10
TAKE.MF5.FR_TAKE5 = W-FASTR pick: lock 80% -> +20
TAKE.MF5.FR_TAKE6 = W-FASTR pick: lock 80% -> +30
TAKE.MF5.NRT1 = near-target latch MF5 X 0.90 stale 10
TAKE.MF5.NRT2 = near-target latch MF5 X 0.95 stale 20
TAKE.MF5.NRT3 = near-target latch MF5 X 0.90 give 8.0
TAKE.MF5.NRT4 = near-target latch MF5 X 0.95 givep 0.1
TAKE.MF5.SHV1 = target shave MF5 2 ticks
TAKE.MF5.SHV2 = target shave MF5 4 ticks
TAKE.MF5.SHV3 = target shave MF5 8 ticks
TAKE.MF5.TK1 = take at 50% of target after 5 s without a new extreme
TAKE.MF5.TK2 = take at 50% of target after 15 s without a new extreme
TAKE.MF5.TK3 = take at 50% of target after 30 s without a new extreme
TAKE.MF5.TK4 = take at 65% of target after 5 s without a new extreme
TAKE.MF5.TK5 = take at 65% of target after 15 s without a new extreme
TAKE.MF5.TK6 = take at 65% of target after 30 s without a new extreme
TAKE.MF5.TK7 = take at 80% of target after 5 s without a new extreme
TAKE.MF5.TK8 = take at 80% of target after 15 s without a new extreme
TAKE.MF5.TK9 = take at 80% of target after 30 s without a new extreme
TAKE.MF5.TK10 = take at 95% of target after 5 s without a new extreme
TAKE.MF5.TK11 = take at 95% of target after 15 s without a new extreme
TAKE.MF5.TK12 = take at 95% of target after 30 s without a new extreme
ZONE.MF1.ZONE1 = zone no-trade set MF1 Half within 10 pts
ZONE.MF1.ZONE2 = zone no-trade set MF1 Half within 30 pts
ZONE.MF1.ZONE3 = zone no-trade set MF1 Half within 50 pts
ZONE.MF1.ZONE4 = zone no-trade set MF1 Skip within 20 pts
ZONE.MF1.ZONE5 = zone no-trade set MF1 Skip within 30 pts
ZONE.MF1.ZONE6 = zone no-trade set MF1 Skip within 50 pts
ZONE.MF2.ZONE1 = zone no-trade set MF2 Half within 10 pts
ZONE.MF2.ZONE2 = zone no-trade set MF2 Half within 30 pts
ZONE.MF2.ZONE3 = zone no-trade set MF2 Half within 50 pts
ZONE.MF2.ZONE4 = zone no-trade set MF2 Skip within 20 pts
ZONE.MF2.ZONE5 = zone no-trade set MF2 Skip within 30 pts
ZONE.MF2.ZONE6 = zone no-trade set MF2 Skip within 50 pts
ZONE.MF3.ZONE1 = zone no-trade set MF3 Half within 10 pts
ZONE.MF3.ZONE2 = zone no-trade set MF3 Half within 30 pts
ZONE.MF3.ZONE3 = zone no-trade set MF3 Half within 50 pts
ZONE.MF3.ZONE4 = zone no-trade set MF3 Skip within 20 pts
ZONE.MF3.ZONE5 = zone no-trade set MF3 Skip within 30 pts
ZONE.MF3.ZONE6 = zone no-trade set MF3 Skip within 50 pts
ZONE.MF4.ZONE1 = zone no-trade set MF4 Half within 10 pts
ZONE.MF4.ZONE2 = zone no-trade set MF4 Half within 30 pts
ZONE.MF4.ZONE3 = zone no-trade set MF4 Half within 50 pts
ZONE.MF4.ZONE4 = zone no-trade set MF4 Skip within 20 pts
ZONE.MF4.ZONE5 = zone no-trade set MF4 Skip within 30 pts
ZONE.MF4.ZONE6 = zone no-trade set MF4 Skip within 50 pts
ZONE.MF5.ZONE1 = zone no-trade set MF5 Half within 10 pts
ZONE.MF5.ZONE2 = zone no-trade set MF5 Half within 30 pts
ZONE.MF5.ZONE3 = zone no-trade set MF5 Half within 50 pts
ZONE.MF5.ZONE4 = zone no-trade set MF5 Skip within 20 pts
ZONE.MF5.ZONE5 = zone no-trade set MF5 Skip within 30 pts
ZONE.MF5.ZONE6 = zone no-trade set MF5 Skip within 50 pts
```

## 8. NY AM (question 6)
NOT YET: TL3_ALN_NY_STKd8b76ecd35 bare fit is still running (screens restarted 20:40Z after the identity harness fix); the same page will be written for it when its table lands. The setting codes and their numbers (sections 2-4) are the same code; the member tags and stop sizes differ (read from its set JSON).
