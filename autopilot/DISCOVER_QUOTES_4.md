# DISCOVER_QUOTES_4 (CAL, 2026-11-05): METADATA ONLY, nothing bought or downloaded. Balance $711.74 unchanged.
Scope: l2vast/ds3/prereg/INSTR2_QUOTES4_scope.md sha256 c5ed8d4e26f89814bfb9576ca29c058c378d3170c77b17f93ac7ae0feed1388e. Dataset GLBX.MDP3, schema ohlcv-1m, stype continuous .v.0. Script code/instr2/quotes4.py; raw QUOTES4.json.
Dataset available up to 2026-11-05 19:10Z at quote time, so the top-up span is 2026-10-17..2026-11-05 (end exclusive; 11-05 itself is partial and not complete).

| symbol | span | records | GB | USD |
|---|---|---|---|---|
| GC.v.0 | 2026-10-17..2026-11-05 | 17,997 | 0.00101 | 0.0657 |
| CL.v.0 | 2026-10-17..2026-11-05 | 17,958 | 0.00101 | 0.0656 |
| ZN.v.0 | 2026-10-17..2026-11-05 | 17,226 | 0.00096 | 0.0629 |
| ZB.v.0 | 2026-10-17..2026-11-05 | 16,378 | 0.00092 | 0.0598 |
| 6E.v.0 | 2026-10-17..2026-11-05 | 17,730 | 0.00099 | 0.0647 |
| 6J.v.0 | 2026-10-17..2026-11-05 | 17,429 | 0.00098 | 0.0636 |
| NKD.v.0 | 2026-10-17..2026-11-05 | 12,862 | 0.00072 | 0.0470 |
| YM.v.0 | 2026-10-17..2026-11-05 | 17,877 | 0.001 | 0.0653 |
| BTC.v.0 | 2026-10-17..2026-11-05 | 13,424 | 0.00075 | 0.0490 |
| MBT.v.0 | 2026-10-17..2026-11-05 | 17,683 | 0.00099 | 0.0646 |
| MES.v.0 | 2026-10-17..2026-11-05 | 18,000 | 0.00101 | 0.0657 |
| MNQ.v.0 | 2026-10-17..2026-11-05 | 18,000 | 0.00101 | 0.0657 |
| M2K.v.0 | 2026-10-17..2026-11-05 | 17,505 | 0.00098 | 0.0639 |
| MYM.v.0 | 2026-10-17..2026-11-05 | 17,949 | 0.00101 | 0.0655 |
| RTY.v.0 | 2013-01-01..2017-07-09 | 0 | 0.0 | 0.0000 |

Top-up total for the 10 requested instruments (GC CL ZN ZB 6E 6J NKD YM BTC MBT): $0.61. All four micros (MES MNQ M2K MYM) add about $0.26 more.
Micros: MES, MNQ, M2K, MYM are separate series with their own ohlcv-1m (about 18,000 records each in the span, same price as the parent, different volume); they only matter for micro liquidity/slippage, the parent 1-min suffices for price paths.
RTY 2013-01-01..2017-07-09: the quote returns 0 records and $0.00 under RTY.v.0, RTY.c.0, RTY.n.0 and RTY.FUT, and raw RTYH7/RTYZ6/RTYH3 do not resolve. A control span 2017-06-01..2017-08-01 returns 7,863 records. Conclusion: GLBX.MDP3 on Databento holds no RTY before about 2017-06/07, which matches the owned file start 2017-07-09. There is nothing to buy there; the earlier inventory line 'RTY 1-min 2013..2017 purchase' is withdrawn (no such data).
BTC and MBT are on GLBX.MDP3 continuous and quoted above. BTC 2017-12..2021-12 history was not quoted (not requested).
Recommendation (no action taken): the whole top-up is under one dollar; buying needs the user's OK. Wait until 11-06 so 11-05 is a complete day, then pull 2026-10-17..2026-11-06 in one request set.
