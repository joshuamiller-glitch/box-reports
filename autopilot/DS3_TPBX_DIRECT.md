# DS3_TPBX_DIRECT - direct-L2 basis for the PB_ST10_SWZ_T3 f60 cells (D3PX, complete)

Research output. Cells: PBX_PB_ST10_SWZ_T3_f60_{T1 (control), SW, T3} (the two block (i) mapped CANDIDATEs and the 60/1R base). Entries S10x1 gap-2 s and exits XJ touch-join / 10-lot market from D3XT's replay (identical event keys; pbx_dprep: 0 new events; nominal identity of f60_T1 vs D3XT PBS BASE rows: {"n_mine": 6092, "n_d3xt": 6092, "n_matched": 6092, "k_equal": 1.0, "px_equal": 1.0, "reason_equal": 1.0}). Price basis: raw L2 prices with the per-bar real-minus-adjusted offset (dc_asm.adj_arr). 10 lots (fixed 60 stop, $12,000 risk), per-book locks.

Coverage: D3XT exclusion filter applied (L2 raw on disk ends 2026-10-09): trades entered after 2026-10-09 20:00 UTC dropped from every cell and the control (360 of 18276 rows).

| cell | missing entry / exit fills | n pairs WF | direct mean pts/trade WF | paired vs 60/1R direct [CI] WF | HOLD paired | 2023 paired | direct WF wk mean / SD / maxDD | HOLD wk | 2023 wk | 2x wk | mapped (conservative) WF wk mean | direct real minus mapped random-in-regime (b) draws, pts/trade (WF) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| PBX_PB_ST10_SWZ_T3_f60_SW | 12 / 0 | 4978 | +1.31 | -1.12 [-2.33,+0.14] | -2.16 | -0.83 | +2,955 / 61,228 / 734,158 | +4,374 | +8,456 | -1,140 | +5,760 | +0.56 |
| PBX_PB_ST10_SWZ_T3_f60_T1 | 12 / 0 | 4978 | +2.43 | +0.00 [+0.00,+0.00] | +0.00 | +0.00 | +12,652 / 59,729 / 537,122 | +17,213 | +8,119 | +14,014 | +295 | +2.87 |
| PBX_PB_ST10_SWZ_T3_f60_T3 | 12 / 0 | 4978 | +3.63 | +1.20 [-1.25,+3.77] | -0.63 | -1.36 | +7,255 / 61,989 / 679,737 | +13,526 | +7,021 | +5,600 | +6,901 | +3.51 |

Direct real vs the mapped random-in-regime / timing-destroyed draws (16 each; placebo trades were not replayed, so the comparison is real-direct vs placebo-mapped, which favours the real cell), pts/trade per kept trade:

| cell | WF vs random-in-regime [CI] rank | HOLD vs (b) [CI] | 2023 span vs (b) | WF vs (a) rank | mapped (conservative) mean pts/trade WF | direct mean pts/trade WF |
|---|---|---|---|---|---|---|
| PBX_PB_ST10_SWZ_T3_f60_SW | +0.85 [-1.19,+2.73] r0.94 | +1.14 [-1.17,+3.68] | +1.07 | +2.10 r1.00 | +1.86 | +1.31 |
| PBX_PB_ST10_SWZ_T3_f60_T1 | +2.87 [+1.70,+3.99] r1.00 | +3.67 [+2.27,+5.27] | +2.25 | +4.29 r1.00 | +0.11 | +2.43 |
| PBX_PB_ST10_SWZ_T3_f60_T3 | +3.02 [+0.79,+5.17] r1.00 | +4.22 [+1.33,+7.14] | +2.49 | +4.24 r1.00 | +2.99 | +3.63 |

Reading notes: (1) the direct real mean includes the XJ stop-join credit and measured friction; the mapped placebo draws carry no join credit, so "direct real minus mapped random-in-regime" favours the real cell; it is shown only to size the gap, not as a placebo test (placebo trades were not replayed). (2) Base-cell sanity: compare the control row (direct f60_T1 WF mean pts/trade) with the mapped control; D3XT's own PBS BASE direct rows are the same trades.
