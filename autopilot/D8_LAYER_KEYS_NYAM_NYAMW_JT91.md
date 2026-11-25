# D8_LAYER_KEYS_NYAM_NYAMW_JT91 - NYAM stack TL3_ALN_NY_STKd8cd0279ff: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-25 01:56Z by W-LAYERS2 from BAREFIT_NY_STKd8cd0279ff_L1.md (pick TL3_SR_NY_STKd8cd0279ff_BF1_JT91), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L43f0cbfb.BRS8U_w4_s0    stop 120 pts / target 120 pts ; R per lot = $2400 ; entries 0930-1159 ET
MF2 = B7bfd33b7_w4_s0    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0930-1159 ET
MF3 = Bf428c4a1.BRS8U_w4_s0    stop 120 pts / target 120 pts ; R per lot = $2400 ; entries 0930-1159 ET
MF4 = Le4fede95.BRF90_30_w4_s0    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 0930-1159 ET
MF5 = Lf0346d55.BRP60_w2_s0    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0930-1159 ET
MF6 = L8cfda948.BRF90_30_w4_s0    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 0930-1159 ET
MF7 = L4407508c.BRF120_60_w1_s0    stop 120 pts / target 60 pts ; R per lot = $2400 ; entries 0933-1157 ET
MF8 = L39287638.BRF80_40_w1_s0    stop 80 pts / target 40 pts ; R per lot = $1600 ; entries 0930-1159 ET
MF9 = L64390867.BRF80_40_w2_s0    stop 80 pts / target 40 pts ; R per lot = $1600 ; entries 0950-1150 ET
median book R (STK) = 90 pts x $20 = $1800 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_NY_STKd8cd0279ff_BF1_JT91 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = CU4    # loss cut when unrealised <= -120 pts (1.0 x stop)
TAKE.MF1 = SHV2    # target shave MF1 4 ticks
ZONE.MF1 = ZONE2    # zone no-trade set MF1 Half within 30 pts
LOSS.MF2 = FR_LOSS8    # W-FASTR pick: no-follow-through: < +5 pts after 20 min
LOCK.MF2 = LK9    # lock at 80% -> stop to entry+20 pts
ZONE.MF2 = ZONE5    # zone no-trade set MF2 Skip within 30 pts
LOSS.MF3 = CU3    # loss cut when unrealised <= -96 pts (0.8 x stop)
TAKE.MF3 = NRT4    # near-target latch MF3 X 0.95 givep 0.1
ZONE.MF3 = ZONE1    # zone no-trade set MF3 Half within 10 pts
TAKE.MF4 = SHV3    # target shave MF4 8 ticks
ZONE.MF4 = ZONE5    # zone no-trade set MF4 Skip within 30 pts
LOCK.MF5 = LK3    # lock at 50% -> stop to entry+20 pts
TAKE.MF5 = TK6    # take at 65% of target after 30 s without a new extreme
LOSS.MF6 = CU2    # loss cut when unrealised <= -54 pts (0.6 x stop)
LOCK.MF6 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF6 = SHV3    # target shave MF6 8 ticks
ZONE.MF6 = ZONE6    # zone no-trade set MF6 Skip within 50 pts
LOCK.MF7 = LK3    # lock at 50% -> stop to entry+20 pts
TAKE.MF7 = TK2    # take at 50% of target after 15 s without a new extreme
LOSS.MF8 = CU3    # loss cut when unrealised <= -64 pts (0.8 x stop)
LOCK.MF8 = LK8    # lock at 80% -> stop to entry+10 pts
ZONE.MF8 = ZONE2    # zone no-trade set MF8 Half within 30 pts
LOCK.MF9 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF9 = FR_TAKE1    # W-FASTR pick: take 50%/30 s
DLA = DLA9    # per-book day loss halt at -2R (new entries only, open position runs, rest of session)
DLB = DLB9    # stack day loss halt at -$4000 per lot per book (new entries only, open positions run, rest of session)
SC = SC1    # StackCut share 25% (scope Asia-only, lots 4; rounds up: 25% = 50% at 2 lots)
BL = BL4    # BookLock arm 2.0R give-back 33%
CAP = CAP6    # per-book day loss stop -3R ($14400)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS2    # no-trade-set rule dropped
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```

## Relay readings 2026-11-25 02:15Z (confirmed / corrected from the engine and hook code, read-only; W-LAYERS2)
1. **FR_LOSS8 (nft X 5, N 20) on MF2: CONFIRMED with one precision.** ONE check, never repeated: th_ec/ec_hooks.py:103 `f = (j == int(p['N'] * 60)) and x < p['X']` with j = r - r_e (ec_hooks.py:96): r_e = the first 1-second state-tape row at or after the entry second, so it tests exactly tape row r_e + 1200 (counted in tape rows = seconds when the tape is gapless; if that row does not exist there is no check), x = side x (mid[r] - entry_px) < +5 pts; exit event one row later, market at mid - side x 0.80 pt, exit name EarlyCut. Not 'every second after 20 min'.
2. **DLB9: CORRECTED.** The threshold is NOT the full-weight lots: dl_hooks.py:51 `thr = -float(SK['Y']) * float(b.base_qty) + D['sbase']` uses base_qty of the book whose check is running (checks run per book: dl_hooks.py:55-58, from check_book_lock every >= 2 s and check_limits every minute; b.base_qty = that book's lots at its last signal, mf_multi.py:41, initial BASEQ[tag] sim.py:49), while the sum is over all nine books (closed + open, dl_hooks.py:51). It fires when ANY not-yet-halted book's own threshold is met = effectively -$4,000 x (lots of the smallest-lot book not yet halted): at the native 4/2/1 basis -$4,000 in total (MF7 / MF8 carry 1 lot), at the file's 6/3/1 also -$4,000, at 6/3/2 -$8,000 - NOT -$16,000 / -$24,000. This is how it was FITTED (L6M numbers include it), so code that behaviour. After it fires: day_halt for all nine (no new entries until the 18:00 ET roll), open trades run (mode 'new', dl_hooks.py:_apply). The pre-first-signal value of base_qty is the engine table BASEQ[tag] (OPEN: not read).
3. **BL4: CONFIRMED.** lin bl = [2.0, 0.33, -12.0] in the JT91 set (stackrule_gen.py:65 builds weekly_R = 12.0 for the 9 arm x give-back rows): th_combo/mf_multi.py:79-92: WEEKLY FLOOR when week P&L (+ open) <= -12 R, else give-back lock when the day peak >= 2.0 R and day <= peak x (1 - 0.33) = 0.67 x peak; R = base_qty x max(1, size_mult) x the book's own stop x $20; per book; evaluated every >= 2 s (sim.py on_print last_lock).
4. **SC1: the relay is RIGHT, the page label is wrong.** The JT91 set carries lin {stackcut_share 0.25, stackcut_sessions [3]} (read from the set JSON); mf_multi.py:72 acts only when stopped.entry_session is in stackcut_sessions = [3] = NY AM (09:30-12:00 ET, all nine books enter there); 'scope Asia-only' is a hard-coded label string in stackrule_gen.py:60. Cut = ceil(pos x 0.25 - 1e-9), min 1; q >= pos closes the whole position (mf_multi.py:73-78): 6 -> 2, 3 -> 1, 1 -> closed: CONFIRMED; trigger = a book exits with a name containing Stop (not StackCut); every other open book on the same side.
5. **CAP6 with DLA9: PARTLY CORRECTED.** (a) CAP6 is the engine's own day cap (sim.py:722-730 check_limits, once per 1-minute bar, FIRST line `if b.day_halt: return`): it tests CLOSED day P&L only (b.day_pnl = realized, sim.py:77: NOT open P&L) <= -max_day_loss x max(1, size_mult), and it closes an open trade (DayHalt). (b) Its value is a STATIC dollar number, the same for every book: the set's stream cap is [48,000, 14,400] = 3 x the MEDIAN book R ($4,800), not 3 x each book's own R (stackrule_gen.py:57 reassigns lots = max(2, med_lots) BEFORE the CAP lambda at :71, so the 'lots == 0' per-book branch is never taken): -$14,400 per book at the native basis. [This also corrects the 'CAP uses each book's own R' line of the earlier keys pages (Asia, NY AM equal five, London, NY PM): CAP is static median-R dollars.] (c) DLA9 (dl_hooks.py:42-50): closed + open day P&L <= -2 x the book's OWN R (base_qty x stop x $20), mode 'new' = day_halt, no close. (d) Order in a minute check: the outer class calls super().check_limits first (CAP6, closed P&L), then the daily-loss check; between minute bars DLA9 is also checked in check_book_lock every >= 2 s. Once DLA9 has set day_halt, the engine's check_limits returns at its first line, so CAP6 can no longer fire that day. Which acts first is per book: DLA9's -2R own R = MF1 -$19,200, MF3 -$19,200 (stop 120 x 4 lots), MF4 / MF6 -$14,400 (equal to CAP6), MF2 -$9,600, MF9 -$6,400, MF5 / MF7 -$4,800, MF8 -$3,200 (at the native lots): for MF2, MF5, MF7, MF8, MF9 DLA9 comes first and CAP6 is then dead; for MF1 and MF3 CAP6 (-$14,400 closed P&L, closes the open trade) can come first.
6. **NRT4 on MF3: CONFIRMED.** wnt_hooks.py:36-52 per print: ufav = side x (b.fav_ext - entry) with b.fav_ext the engine's per-print favourable extreme; latched once ufav >= 0.95 x T (T = the trade's target pts, 120 for MF3); then market exit 'NtGive' on the first print with u <= ufav - 0.1 x T (wnt_hooks.py:51-52), per print (stale branch lines 49 not used by NRT4).

## CORRECTION 2026-11-25 (CAP/DLB engine reading) - written 2026-11-25 02:11Z by W-LAYERS2 (documentation only; the history above is not rewritten)
TOP LINE: 8cd0279ff_BF1_JT91: CODING CHANGE: YES: the CAP pair's second side (and the static median-R dollars) must be coded as above; the written named-side value is correct.
**Set TL3_SR_NY_STKd8cd0279ff_BF1_JT91**
- CAP: the set carries the SAME static dollar caps on EVERY book: profit +$48,000, loss -$14,400 (engine day cap sim.py:722-730, once per 1-minute bar, CLOSED day P&L only, closing an open trade with exit name DayHalt; the dollars are k x the MEDIAN book R of $4,800 at this basis, stackrule_gen.py:57 reassigns lots = max(2, ...) before the CAP lambda at :71, so the page wording 'each book's own R' is WRONG for CAP). The page names only ONE side of the pair: the profit rows (CAP1-4) ALSO set the loss cap at 4 R (= $19,200) and the loss rows (CAP5-8) ALSO set the profit cap at 10 R (= $48,000): the other side is part of the tested set and must be coded.
  Own R of the books differs here (own R per book at this basis: 9,600, 4,800, 9,600, 7,200, 2,400, 7,200, 2,400, 1,600, 3,200): the static dollars are NOT scaled per book.
- DLB: lots differ per book ([1.0, 2.0, 4.0]): threshold = -$4,000 x the lots of the smallest-lot book not yet halted (dl_hooks.py:51): see the JT91 readings section.
- FITTED RESULTS DO NOT CHANGE: the fit ran this exact engine code (the numbers on the page already include the static caps, the hidden side of the CAP pair and the DLB checking-book rule); only the written descriptions were incomplete.
- Engine code: sim.py:722-730 (day caps; `if b.day_halt: return` first line), stackrule_gen.py:57 and :71 (CAP dollars), dl_hooks.py:51 (DLB), D8_LAYER_KEYS_NYAM_NYAMW_JT91.md section Relay readings 2026-11-25 02:15Z.

## NULL RESULT 2026-11-25 03:31Z

Null FAILED: real best single-setting L6M ulcer cut -41.2% vs random-entry draws -50.4% and -81.9%; beats 0 of 2 draws, early stop after 2 misses (gate needs >=4 of 5). Label: NULL FAIL, plus 2023 RED. At the file size DLB9 also makes the pick worse (see NYAM_WEIGHTED_FILE_SIZE.md). No gate changed.
