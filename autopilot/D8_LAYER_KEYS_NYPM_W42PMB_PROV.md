**PROVISIONAL: L6M ONLY, NO WALK-FORWARD, PRIOR YEARS PENDING, NULL PENDING. NOT A GATED PICK. the delivered NY PM stack (STKd893133bd8, BF2_JT9 / JT209) stays the delivered pick until a gated pick exists.**

# D8_LAYER_KEYS_NYPM_W42PMB_PROV - NYPM stack TL3_ALN_NP_STKd8w42pmb: the 2-LOT pick as key = value (order 1840Z: fit at 2 lots only; settings do not change with size)

Written 2026-11-25 15:51Z by W-LAYERS2 from BAREFIT_NP_STKd8w42pmb_PROV.md (pick TL3_SR_NP_STKd8w42pmb_BF1_JT19), the builders and the engine code. Shared mechanism text (CX / STC / LK / TK / FR_TAKE / daily-loss / sizer / StackCut / zones / hook order and precedence): D8_LAYER_KEYS_NYAM.md sections 3-4 and D8_LAYER_KEYS.md; only what differs is below. SPEC / OPEN as there.

## 1. MEMBERS and brackets as the fit used them
```
MF1 = L2c6916a5_R0_P60    stop 60 pts / target 60 pts ; R per lot = $1200 ; entries 1200-1559 ET
MF2 = L4bdd521a_R0_F80_40    stop 80 pts / target 40 pts ; R per lot = $1600 ; entries 1200-1530 ET
median book R (STK) = 70 pts x $20 = $1400 per lot x lots; per-book R (CAP, BookLock, DLA) = its own stop x $20 x lots
```

## 2. THE 2-LOT PICK TL3_SR_NP_STKd8w42pmb_BF1_JT19 resolved for THIS stack (factor = code ; description at lot basis 2)
```
LOSS.MF1 = STC4    # state-cut cell MF1 mult 15.0    [NEEDS THE 10-LEVEL CANCEL TAPE: not reproducible from an NT8 feed]
TAKE.MF1 = TK12    # take at 95% of target after 30 s without a new extreme
ZONE.MF1 = ZONE2    # zone no-trade set MF1 Half within 30 pts
LOSS.MF2 = CU4    # loss cut when unrealised <= -80 pts (1.0 x stop)
TAKE.MF2 = TK6    # take at 65% of target after 30 s without a new extreme
ZONE.MF2 = ZONE2    # zone no-trade set MF2 Half within 30 pts
DLB = DLB5    # stack day loss halt at -$6000 per lot per book (open P&L counts, all books halted, positions closed, rest of session)
DLC = DLC8    # per-book pause 60 min after 5 consecutive full-stop losses, then re-arm
BL = BL7    # BookLock arm 3.0R give-back 33%
STK = STK1    # WHOLE-STACK day profit stop +4R of one book ($5600)
SZW = SZW2    # ER sizer (new-book hook) ER(20,5m) < 0.30 -> lots x 0.50, half-up, min 1
CG = CGB1    # skip after 1 same-side losses (c_gov, governs every new book MF1..MF5)
```

FEED NEEDS: STC state cut = 10-level cancel tape (canc_bid / canc_ask + displayed-size EWMA): IN THIS PICK on LOSS.MF1. Everything else = prices / 1-minute and 5-minute bars / the closed-second mid / trades (NT8 feed): yes.

## 3. HOOK ORDER (SPEC, same engine for every session; full text D8_LAYER_KEYS_NYAM.md section 4)
```
class chain = hooklist in written order, a LATER hook is OUTER and runs first. Entry: daily-loss pause gate (dl_hooks.try_entry) -> engine try_entry checks (halts, in trade, exit pending) -> trend_size -> ntz_check: sizer (SZW, lots x 0.5 when ER < thr, lots > 1) -> zone (ZONE replaces the inner no-trade-set for the book) -> mf_multi no-trade-set (NTS, lots > 1). In the trade, per print: resting bracket stop / target orders first; then manage_th_l2 (base logic, then hooks innermost-first: CU/CX and STC decide on closed seconds and exit one second later, LK lock = immediate PolicyTrail), then PolicyTake; check_book_lock at most every 2 s (BookLock, then the daily-loss check); check_limits once per minute. The FIRST rule that requests an exit wins and names it (request_exit guard).
```
