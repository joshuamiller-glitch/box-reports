**PROVISIONAL: L6M ONLY, NO WALK-FORWARD, PRIOR YEARS PENDING, NULL PENDING. NOT A GATED PICK. the delivered London stack and pick (L19201dfc, JT14 with STC4) stay the delivered pick until a gated pick exists.**

# D8_LAYER_KEYS_LONDON_W42LO_PROV - London stack TL3_ALN_LO_STKd8w42lo: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-25 18:58Z by W-LAYERS2 from BAREFIT_LO_STKd8w42lo_PROV.md (pick TL3_SR_LO_STKd8w42lo_BF1_JT4), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L19201dfc.BRF90_30_w4_s0    stop 90 pts / target 30 pts ; R per lot = $1800 ; entries 0200-0829 ET
MF2 = L12842dde.BRP45_w2_s0    stop 45 pts / target 45 pts ; R per lot = $900 ; entries 0200-0829 ET
MF3 = L74274eca.BRF120_60_w1_s0    stop 120 pts / target 60 pts ; R per lot = $2400 ; entries 0200-0829 ET
median book R (STK) = 90 pts x $20 = $1800 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_LO_STKd8w42lo_BF1_JT4 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = CU4    # loss cut when unrealised <= -90 pts (1.0 x stop)
LOCK.MF1 = LK3    # lock at 50% -> stop to entry+20 pts
TAKE.MF1 = TK12    # take at 95% of target after 30 s without a new extreme
LOCK.MF2 = LK5    # lock at 65% -> stop to entry+10 pts
TAKE.MF2 = TK12    # take at 95% of target after 30 s without a new extreme
ZONE.MF2 = ZONE3    # zone no-trade set MF2 Half within 50 pts
LOSS.MF3 = FR_LOSS7    # W-FASTR pick: no-follow-through: < +10 pts after 20 min
TAKE.MF3 = TK8    # take at 80% of target after 15 s without a new extreme
DLA = DLA3    # per-book day loss halt at -2R (open P&L counts, close the position, halt rest of session)
DLC = DLC1    # per-book halt after 2 consecutive full-stop losses (rest of session)
SC = SC1    # StackCut share 25% (scope Asia-only, lots 2; rounds up: 25% = 50% at 2 lots)
BL = BL4    # BookLock arm 2.0R give-back 33%
CAP = CAP1    # per-book day profit stop +5R ($12000)
SZW = SZW2    # ER sizer (new-book hook) ER(20,5m) < 0.30 -> lots x 0.50, half-up, min 1
CG = CGB2    # skip after 2 same-side losses (c_gov, governs every new book MF1..MF5)
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): not in this pick. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```
