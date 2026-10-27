# DS3_TPBX_DIRECT - direct-L2 basis for the PB_ST10_SWZ_T3 f60 cells (D3PX, PARTIAL: D3XT months 19/45)

Research output. Cells: PBX_PB_ST10_SWZ_T3_f60_{T1 (control), SW, T3} (the two block (i) mapped CANDIDATEs and the 60/1R base). Entries S10x1 gap-2 s and exits XJ touch-join / 10-lot market from D3XT's replay (identical event keys; pbx_dprep: 0 new events; nominal identity of f60_T1 vs D3XT PBS BASE rows: {"n_mine": 6092, "n_d3xt": 6092, "n_matched": 6092, "k_equal": 1.0, "px_equal": 1.0, "reason_equal": 1.0}). Price basis: raw L2 prices with the per-bar real-minus-adjusted offset (dc_asm.adj_arr). 10 lots (fixed 60 stop, $12,000 risk), per-book locks.

| cell | missing entry / exit fills | n pairs WF | direct mean pts/trade WF | paired vs 60/1R direct [CI] WF | HOLD paired | 2023 paired | direct WF wk mean / SD / maxDD | HOLD wk | 2023 wk | 2x wk | mapped (conservative) WF wk mean | direct real minus mapped random-in-regime (b) draws, pts/trade (WF) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PBX_PB_ST10_SWZ_T3_f60_SW | 4363 / 1930 | 5098 | +0.22 | -1.00 [-2.19,+0.24] | -1.95 | -0.83 | -1,247 / 60,332 / 804,503 | -847 | +8,456 | -8,514 | +5,760 | -0.53 |
| PBX_PB_ST10_SWZ_T3_f60_T1 | 4363 / 1512 | 5098 | +1.22 | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +6,867 / 57,235 / 556,368 | +9,821 | +8,119 | +2,370 | +295 | +1.66 |
| PBX_PB_ST10_SWZ_T3_f60_T3 | 4363 / 2147 | 5098 | +2.83 | +1.61 [-0.86,+4.13] | +0.05 | -1.36 | +4,295 / 61,303 / 719,041 | +9,729 | +7,021 | +2,155 | +6,901 | +2.71 |

Reading notes: (1) the direct real mean includes the XJ stop-join credit and measured friction; the mapped placebo draws carry no join credit, so "direct real minus mapped random-in-regime" favours the real cell; it is shown only to size the gap, not as a placebo test (placebo trades were not replayed). (2) Base-cell sanity: compare the control row (direct f60_T1 WF mean pts/trade) with the mapped control; D3XT's own PBS BASE direct rows are the same trades.
