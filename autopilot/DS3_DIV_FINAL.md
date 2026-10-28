# DS3_DIV_FINAL - T-DIVERSIFY (intraday, other markets) - main, from D3DV1/E/C/R/X/G reports (2026-10-28)
Nothing CONFIRMED. No Sim spec written. No purchase made. Detail: DS3_DIV_0_INVENTORY, _1_MAPS, _ES/_RTY/_YM, _CL/_GC, _ZN/_6E, _XMKT, _VOLGATE.

## One verdict line per market / signal
- ES / RTY / YM own-clock rules (33 cells): 0 CONFIRMED / 0 CANDIDATE / 33 DEAD. Closest: ES overnight premium WF +$731/wk [-81,+1,543] MDE 1,160 (pooled index +$1,028 vs MDE 3,296); costs eat window rules.
- CL (7) and GC (10): 17 DEAD. Closest GC overnight long WF +$341/wk (MDE 293) fails random-clock placebo (gold trend, not a clock edge).
- ZN (8) and 6E (10): 18 DEAD. Cost 0.10-0.68 R/trade exceeds gross edge (<=0.18 R).
- Cross-market into NQ/ES (15 cells): 15 DEAD. Lead only: short ES 10:30 after first-hour 6E drop, WF +$303/wk (MDE 352), fails year_share and 2023 span, p 0.09 after x12.
- Vol-regime gates on live books (20 cells + ref): 20 DEAD. ATR/VIX skip-bottom/half-bottom significantly negative (-$25k/-$19k per wk skip-bottom); the stack earns 55% of P&L in the bottom ATR tercile. On/off adds nothing beyond the (DEAD) vol-scaled lots.
- Data finding: tick trades exist on disk for ES/RTY/CL/GC/ZN (not YM/6E); purchase list ($762.35 total, $158.63 P1) NOT bought, and no result justifies it.

## Top table regardless of verdict
| rank | cell | WF $/wk | MDE | failed gate |
|---|---|---|---|---|
| 1 | ES ON1 overnight | +731 | 1,160 | placebos a/b, best_of_N |
| 2 | GC ONL overnight long | +341 | 293 | beats_b, hold(b), best_of_N |
| 3 | B_6E_ES_S (short ES 10:30 after 6E drop) | +303 | 352 | year_share, span2 |
| 4 | A_up (1.5x top ATR tercile) | +3,504 | 12,099 | CI includes 0, maxDD/worst-week |
| 5 | CL ONL | +80 | 259 | placebos a/b |
| 6 | A_ZN_NQ_L | +116 | 295 | DEAD (no direction info) |
