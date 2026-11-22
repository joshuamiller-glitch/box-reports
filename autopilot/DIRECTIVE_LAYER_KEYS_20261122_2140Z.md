# layer-keys-definitions-for-the-port (information only, 2026-11-22 ~21:40Z)

Written by the relay (Claude), not typed by Josh. Information / plumbing only: no new tests, no gate or rule change.

Context: D8 Asia (5-book stack TL3_ALN_AS_STKd8106b26ef) is being coded for SIM with the joint all-layers pick of the 4-lot basis (BF4_JT1) as panel defaults. Please answer on one page, autopilot/D8_LAYER_KEYS.md, in plain key = value form:

1. Every setting code used on BAREFIT_AS_STKd8106b26ef.md / D8_LAYER_DEFAULTS_ASIA.md with its exact parameters: CU1-4, STC1-4, CX*, LK1-9, TK1-12, NRT1-4, SHV1-3, ZONE1-6, SC1-3, BL1-n, CAP1-n, STK1-n, SZW1-3, NTS1-n, CG1-n (several are only visible when they happen to be the best single setting; SZW2 and BL2 are in the 4-lot joint pick and are not defined anywhere on the pages).
2. BookLock "arm 1.5R give-back 33% / 50% / 67%": is the book halted when day P&L <= X x day peak, or when it has given back X of the peak (day <= (1 - X) x peak)? And is the weekly floor on or off in BL1 / BL2?
3. MF1..MF5: confirm the member order (assumed MF1 Lb0e6dfa3, MF2 L385f4f2e.J502, MF3 L92a90948, MF4 L6b373671, MF5 L578701ed).
4. Zones in the fit: confirm the line set is the live DS7 PoiSet (PD_mid, RTH_camH3, Kijun_1h, CRT_mid_4h, KC_up_4h, OTE62 / OTE705 / OTE79 on 15-minute fractals), fed by 1-minute bars stamped at their end time in ET, "fresh" = not yet traded through; and whether the entry price for the "ahead within min(dist, target)" test is the last print at the order time.
5. Dollar rules at N lots: confirm every dollar value on the page scales as value-per-lot x lots (STK4 = +12R of one book = $14,400 per lot; R = lots x stop pts x $20).
6. When the NY AM table lands: the same key = value page for TL3_ALN_NY_STKd8b76ecd35.

Research only. Nothing here touches the execution server, any live chart, credentials, spend or data deletion.
