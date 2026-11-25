# D8_LAYER_KEYS_ASIA_STCFREE - Asia stack TL3_ALN_AS_STKd8106b26ef: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-24 02:00Z by W-LAYERS2 from BAREFIT_AS_STKd8106b26ef_R200_L2.md (pick TL3_SR_AS_STKd8106b26ef_BF2_JT243), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = Lb0e6dfa3_R0_F40_80    stop 40 pts / target 80 pts ; R per lot = $800 ; entries 0000-2356 ET
MF2 = L385f4f2e_CX502    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0001-2359 ET
MF3 = L92a90948_CANC    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0000-2359 ET
MF4 = L6b373671_R0_P60    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 0001-2359 ET
MF5 = L578701ed_R0_F30_90    stop 30 pts / target 90 pts ; R per lot = $600 ; entries 0000-2359 ET
median book R (STK) = 60 pts x $20 = $1200 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_AS_STKd8106b26ef_BF2_JT243 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = CU4    # loss cut when unrealised <= -40 pts (1.0 x stop)
LOCK.MF1 = LK5    # lock at 65% -> stop to entry+10 pts
ZONE.MF1 = ZONE5    # zone no-trade set MF1 Skip within 30 pts
LOSS.MF2 = CU4    # loss cut when unrealised <= -60 pts (1.0 x stop)
LOCK.MF2 = LK9    # lock at 80% -> stop to entry+20 pts
LOSS.MF3 = CU2    # loss cut when unrealised <= -36 pts (0.6 x stop)
LOCK.MF3 = LK3    # lock at 50% -> stop to entry+20 pts
TAKE.MF3 = TK1    # take at 50% of target after 5 s without a new extreme
LOSS.MF4 = CU2    # loss cut when unrealised <= -36 pts (0.6 x stop)
LOCK.MF4 = LK2    # lock at 50% -> stop to entry+10 pts
TAKE.MF4 = NRT2    # near-target latch MF4 X 0.95 stale 20
LOCK.MF5 = LK6    # lock at 65% -> stop to entry+20 pts
TAKE.MF5 = NRT2    # near-target latch MF5 X 0.95 stale 20
ZONE.MF5 = ZONE2    # zone no-trade set MF5 Half within 30 pts
BL = BL1    # BookLock arm 1.5R give-back 33%
CAP = CAP8    # per-book day loss stop -6R ($14400)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS1    # no-trade-set halving 0.5 (today's rule)
CG = CGB2    # skip after 2 same-side losses (c_gov, governs every new book MF1..MF5)
DLC = DLC12    # per-book pause 120 min after 5 consecutive full-stop losses, then re-arm
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```

## CORRECTION 2026-11-25 (CAP/DLB engine reading) - written 2026-11-25 02:11Z by W-LAYERS2 (documentation only; the history above is not rewritten)
TOP LINE: 106b26ef_BF2_JT243: CODING CHANGE: YES: the CAP pair's second side (and the static median-R dollars) must be coded as above; the written named-side value is correct.
**Set TL3_SR_AS_STKd8106b26ef_BF2_JT243**
- CAP: the set carries the SAME static dollar caps on EVERY book: profit +$24,000, loss -$14,400 (engine day cap sim.py:722-730, once per 1-minute bar, CLOSED day P&L only, closing an open trade with exit name DayHalt; the dollars are k x the MEDIAN book R of $2,400 at this basis, stackrule_gen.py:57 reassigns lots = max(2, ...) before the CAP lambda at :71, so the page wording 'each book's own R' is WRONG for CAP). The page names only ONE side of the pair: the profit rows (CAP1-4) ALSO set the loss cap at 4 R (= $9,600) and the loss rows (CAP5-8) ALSO set the profit cap at 10 R (= $24,000): the other side is part of the tested set and must be coded.
  Own R of the books differs here (own R per book at this basis: 1,600, 2,400, 2,400, 2,400, 1,200): the static dollars are NOT scaled per book.
- FITTED RESULTS DO NOT CHANGE: the fit ran this exact engine code (the numbers on the page already include the static caps, the hidden side of the CAP pair and the DLB checking-book rule); only the written descriptions were incomplete.
- Engine code: sim.py:722-730 (day caps; `if b.day_halt: return` first line), stackrule_gen.py:57 and :71 (CAP dollars), dl_hooks.py:51 (DLB), D8_LAYER_KEYS_NYAM_NYAMW_JT91.md section Relay readings 2026-11-25 02:15Z.
