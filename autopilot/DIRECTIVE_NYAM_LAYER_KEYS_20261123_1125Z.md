# nyam-layer-keys-for-the-port (information / plumbing, 2026-11-23 ~11:25Z)

Written by the relay (Claude), not typed by Josh. Information / plumbing only: no new tests, no gate or rule change. Same purpose as order 2140Z of 22 Nov for Asia: the D8 NinjaTrader file must copy the NY AM joint pick exactly as the engine applies it.

The NY AM joint landed 11:08Z (BAREFIT_NY_STKd8b76ecd35.md): BF1_JT22, BF2_JT68, BF4_JT15. Please, with a small agent, write autopilot/D8_LAYER_KEYS_NYAM.md and autopilot/D8_LAYER_DEFAULTS_NYAM.md:

1. The MF1..MF5 mapping for this stack (which book is which tag: L8cfda948.BRF90_30, Lf0346d55.BRP60, L7cc56d99, Lbb254083.BRP45, L8f11883e.BRF30_90) with each book's stop / target in points as the fit used them.
2. Every code in the three picks resolved to numbers for THIS stack (points, fractions, seconds, dollars, R): CU2/CU3/CU4, CX1/CX3, STC1/STC2/STC3, LK1/LK2/LK5/LK6/LK7/LK8, TK1/TK2/TK6, FR_TAKE4/FR_TAKE6, SHV1/SHV2, ZONE2..ZONE6 per book, SC2, BL1/BL7, CAP1/CAP2, STK1/STK3, SZW3, NTS1, DLA5, DLB6, DLC2/DLC10.
3. Full mechanism text, as code-level rules, for the families the Asia port did not need:
   a. CX "context cut (fresh)": the exact definition of the FRESH context (which series, which lookback, which comparison), when it is evaluated, on which price (closed 1-second mid as CU?), and what resets it.
   b. STC "state cut cell" {arm, mult, win, pers, newmae, var} on ev_panel cut_tl: every field, the series it reads, the evaluation clock, the exit it sends.
   c. FR_TAKE lock variants: how "lock 80% -> +10 / +30" differs from LK (trigger price, stop placement, order type), and take 50%/95% after N s.
   d. The new daily-loss family as used in this joint (DLA5, DLB6, DLC2, DLC10): level, what "day" is for NY AM, open P&L counted or not, checked when, what closes, when the halt lifts, and for DLC what counts as a full-stop loss and whether it is per side.
   e. SZW for NY AM: the same market-level ER(20, 5-minute) as Asia? threshold and multiplier of SZW3; applies only above 1 lot?
   f. SC "scope Asia-only" on a NY AM stack: what StackCut does in this fit (does it act on NY AM books at all?), and STK / CAP R definitions for this stack (median-book R in dollars).
   g. ZONE for NY AM: the same PoiSet line list and entry-price rule (close of the last completed 1-minute bar) as Asia?
4. The hook order at entry and in the trade for this stack (gate, sizer, zone, no-trade-set; cut / lock / take / day rules precedence when two fire on the same print).
5. D8_LAYER_DEFAULTS_NYAM.md: the pick per lot basis as one settings table (book by book and stack level), with its status line: walk-forward, persistence, year bands, null (pending / result), and which lot basis you recommend the file defaults follow for an account running 2 lots per book (Asia defaults followed the 4-lot pick), with the reason.
6. Say whether the picks will change when the 1-lot screen null and the joint null land, and their ETA; and whether the daily-loss family being inside this joint means the NY AM joint is already final with respect to order 0640Z.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
