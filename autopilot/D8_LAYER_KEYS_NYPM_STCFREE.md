# D8_LAYER_KEYS_NYPM_STCFREE - NYPM stack TL3_ALN_NP_STKd893133bd8: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-23 20:47Z by W-LAYERS2 from BAREFIT_NP_STKd893133bd8_R200_L2.md (pick TL3_SR_NP_STKd893133bd8_BF2_JT209), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L52359bf4_R0_P30    stop 30 pts / target 30 pts ; R per lot = $600 ; entries 1200-1800 ET
MF2 = L8e0bf58c_R0_S8U    stop 120 pts / target 120 pts ; R per lot = $2400 ; entries 1200-1559 ET
MF3 = L4bdd521a_R0_F80_40    stop 80 pts / target 40 pts ; R per lot = $1600 ; entries 1200-1530 ET
MF4 = L2c6916a5_R0_P60    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 1200-1559 ET
median book R (STK) = 70 pts x $20 = $1400 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_NP_STKd893133bd8_BF2_JT209 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF2 = CU3    # loss cut when unrealised <= -96 pts (0.8 x stop)
LOCK.MF2 = LK5    # lock at 65% -> stop to entry+10 pts
TAKE.MF2 = SHV1    # target shave MF2 2 ticks
ZONE.MF2 = ZONE4    # zone no-trade set MF2 Skip within 20 pts
LOSS.MF3 = CU4    # loss cut when unrealised <= -80 pts (1.0 x stop)
LOCK.MF3 = LK7    # lock at 80% -> stop to entry+0 pts
TAKE.MF3 = SHV2    # target shave MF3 4 ticks
ZONE.MF3 = ZONE1    # zone no-trade set MF3 Half within 10 pts
LOSS.MF4 = CU4    # loss cut when unrealised <= -60 pts (1.0 x stop)
STK = STK6    # WHOLE-STACK day loss stop -4R of one book ($11200)
SZW = SZW3    # ER sizer (new-book hook) ER(20,5m) < 0.40 -> lots x 0.50, half-up, min 1
NTS = NTS2    # no-trade-set rule dropped
CG = CGB3    # skip after 3 same-side losses (c_gov, governs every new book MF1..MF5)
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```

## CORRECTION 2026-11-25 (CAP/DLB engine reading) - written 2026-11-25 02:11Z by W-LAYERS2 (documentation only; the history above is not rewritten)
TOP LINE: 93133bd8_BF2_JT209: NO CHANGE to what the page tells the relay to code (this set has no CAP; DLB / STK values are as written).
**Set TL3_SR_NP_STKd893133bd8_BF2_JT209**
- STK (whole-stack day loss stop): static dollars $11,200 on the SUM of the day P&L (closed) of the listed books (lay_hooks.py stack_caps, evaluated in check_limits once per minute); = k x the median book R ($2,800); no per-book scaling; the written value is correct.
- FITTED RESULTS DO NOT CHANGE: the fit ran this exact engine code (the numbers on the page already include the static caps, the hidden side of the CAP pair and the DLB checking-book rule); only the written descriptions were incomplete.
- Engine code: sim.py:722-730 (day caps; `if b.day_halt: return` first line), stackrule_gen.py:57 and :71 (CAP dollars), dl_hooks.py:51 (DLB), D8_LAYER_KEYS_NYAM_NYAMW_JT91.md section Relay readings 2026-11-25 02:15Z.
