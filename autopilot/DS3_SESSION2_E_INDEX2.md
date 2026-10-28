# DS3_SESSION2_E_INDEX2 - D6 session-book specs, part 2 (D3SSE2, 2026-10-28)

Research/spec only. No live, execution-server or chart change; no engine code edited; UNTOUCHED never read (ledger window ends label day 2026-02-06). The IF and CRT cells are D3SSE's (not touched here). Every spec below: "session cell, tier X, basis Y, NOT live-eligible until the live-latency result (D3SA) lands". All dollars are the ledger's (10 NQ lots equivalent, pts x 200 - 100.13 per trade unless the source table stores its own net).

## 1. Specs written (each its own file)
| cell | session | file | tier | basis | PRE n / mean $ | HOLD n / mean $ | 2023 span mean $ | slippage break-even (HOLD, pt) | reconstructible |
|---|---|---|---|---|---|---|---|---|---|
| ba2/KB_t60_s75 | ASIA | DS3_SPEC_ba2_KB_t60_s75_SESSION.md | SESSION-CANDIDATE | STORED (rows-as-stored) | 704 / 1,445 | 321 / 600 | 84 | 3.0 | yes |
| ba2/HM_t75_s90 | NY-AM | DS3_SPEC_ba2_HM_t75_s90_SESSION.md | SESSION-CANDIDATE | STORED | 427 / 2,443 | 197 / 1,798 | 2,103 | 9.0 | yes |
| ba2/SM_t60_sst | ASIA | DS3_SPEC_ba2_SM_t60_sst_SESSION.md | SESSION-CANDIDATE | STORED | 264 / 1,539 | 123 / 459 | 953 | 2.3 | yes |
| PB7_PB5_depth_atr0.5_W15_s+0 | ASIA | DS3_SPEC_PB7_PB5_depth_atr0.5_W15_s+0_SESSION.md | SESSION-CANDIDATE | MAPPED in the rows (ledger label "DIRECT L2" is the family verdict label; mapped PASS / direct CANDIDATE) | 342 / 2,372 | 192 / 905 | 777 | 4.5 (raw basis 2.2) | yes |
| E1A_RENKOC5_A3_r48 | ASIA | DS3_SPEC_E1A_RENKOC5_A3_r48_SESSION.md | SESSION-CANDIDATE | STORED (tick-exact, rows-as-stored) | 424 / 2,341 | 188 / 2,321 | -13 | 11.6 | yes (code + tick data on disk) |
| TB4B_tick_26_tick_250_ST3_SW62_T2 | ASIA | DS3_SPEC_TB4B_tick_26_tick_250_ST3_SW62_T2_SESSION.md | **DEAD-IN-HOLD** | mapped | 450 / 1,842 | 200 / -1,060 | 46 | negative | yes |
| TB4W_03_time_15s_ST3_E20_1_T2 (ledger id ..._ntime14) | ASIA | DS3_SPEC_TB4W_03_time_15s_ST3_E20_1_T2_SESSION.md | SESSION-CANDIDATE | mapped | 800 / 1,237 | 369 / 494 | -106 | 2.5 | yes |
Each spec has an identity-test table (rows path, expected trade count and first/last stamps for PRE / HOLD / 2023 span / ALL, tolerance), which reproduces the ledger row.

## 2. Decoded rules (one line each)
- **KB_t60_s75**: live KB (TE7_kelt3m_n14_m1.0: 3-min EMA14 +/- 1.0 x ATR10-Wilder band close-break, edge) with target 60 / stop 75 pt; ASIA entries; the generator at 60/60 reproduces the live base rows exactly (8593 vs 8593, 0 differences).
- **HM_t75_s90**: live DS2 HM (1-min HMA20 x HMA55 cross of Close minus VWAP-reset-at-00:00-UTC-4, HMA55 slope confirm, EMA200 filter) with target 75 / stop 90 pt; NY-AM entries; generator at 60/60 reproduces ROWS_bench3 HM exactly (6311 vs 6311).
- **SM_t60_sst**: live SM (TE6_st10m_n7_m3.0: 10-min median-price Supertrend ATR7 x 3.0 flip) with target 60 pt and the STRUCTURE stop; ASIA; 60/60 identity exact (2397 vs 2397). **"sst" is the structure stop = s + st, not a Supertrend-line stop**: stop distance = entry open to the extreme of the 10 one-minute bars of the signal bar + 5 pt, clipped to [20, 120] pt (ba_rows2.py lines 118-120; ba_prereg2.py line 13).
- **PB7_PB5_depth_atr0.5_W15_s+0**: PbEngine (tp_sig.pullback) reg ST10 (10-min Supertrend ATR10 x 3.0 median price, as-of), level = running 1-min extreme since the regime segment began -/+ 0.5 x ATR(14, 5-min Wilder), touch = edge (Low <= level with previous Low > previous level), armed W = 15 one-minute bars, trigger T1 (bullish bar closing above the level; mirrored short), shift 0; entry next 1-min open; 60/60 bracket, 16:55 flat; rebuilt from the library code today: all 342 PRE ASIA executed trades reproduced.
- **E1A_RENKOC5_A3_r48**: true Renko bricks of 48 ticks (12 pt, reversal 96 ticks), colour-run state 5 (reset each 18:00 label day), state-following, stop 3 x ATR14 of 1-min bars (SMA-seeded Wilder), no target, exit on the first brick whose state differs, 16:55 flat, no entries 15:00-18:05.
- **TB4B_tick_26_...**: 250-tick bars, regime Supertrend(10,3) on 3-min bars (flip vs previous bands), level = 62% retrace of the last-60-minute range, trigger T2 (non-touch bar closing beyond the last touch bar's extreme), W 600 s, 60/60.
- **TB4W_03_time_15s_...**: 15-s bars, regime ST3, level EMA20 of 1-min closes, trigger T2, W 600 s, 60/60; parent TB4A_time_14_time_30s_ST5_E20_1_T2.

## 3. Findings that change the D6 picture
1. **"sst" is not a Supertrend-line stop** (coordinator note was wrong on this): ba2/SM_t60_sst is a structure stop; half of its PRE trades sit on the 20-pt floor. In ASIA the same SM entries with the live 60/60 bracket earn more in PRE (1,840 vs 1,539) and HOLD (544 vs 459) per 10-lot trade; the cell is not better than the live SM bracket in-session (pooled calibrated paired effect -0.88 pt, CI crosses 0).
2. **The three ba2 cells are the live engines with a different bracket**, nothing else changed in the entry path (verified by exact row identity at 60/60); but the trade CHAIN differs (longer/shorter holds change which later signals the one-open-trade rule drops), and for NY-AM HM a session-only build differs from the ledger chain on 355 of 924 library days (an earlier-morning HM trade is still open at 09:30 in the library chain).
3. **HM live guard question (material, user side):** about a quarter of the HM NY-AM cell trades have a signal bar in 09:00-09:58 (PRE 106 of 427) and they carry a mean of $4,221 vs $1,856 for the rest. The library (BENCH3) has no 09:00-09:58 guard; FR_SEC5 describes the live HM as having it. If live has it, the cell is the 09:59-12:00 part only.
4. **PB7_PB5 is a fixed 60/60 bracket**, not a dynamic exit: D3SA can replay it on all three fill bases (the coordinator's 19:45Z note lists PB7 among the dynamic-exit legs). Its stored net is the P9 MAPPED table; on raw bracket points the HOLD mean is 434 not 905 (half the HOLD edge is the mapping credit). TB4B, TB4W bracket 240/240 ticks fixed: also fully replayable. Only E1A has a dynamic exit (3 x ATR stop + signal exit + no target).
5. **TB4B is DEAD-IN-HOLD** (ASIA HOLD -1,060/trade); spend no replay beyond the cheap pass.
6. **2023 span:** KB ~0 (84), SM positive (953), HM positive (2,103), PB7 777, E1A -13, TB4B 46, TB4W -106.

## 4. Open items
- Live HM 09:00-09:58 guard setting (user side, DualStrat2 properties not read).
- Bar identity checks on the user side: NT8 Renko 48-tick, 250-tick and 15-s bars vs out/bars/{renko_48,tick_250,time_15s}.parquet; the time-bar close convention (library fires at the 15-s bucket end, NT8 on the first tick of the next bucket) for TB4W; tick counting for TB4B.
- Entry-time convention: ledger et_in for the 1-min cells is the entry-bar END stamp (actual entry instant + 1 min); tick-built cells use the entry-tick time. Session edges differ by one minute between the two families.
- Session locks, handoff (flat at session end vs run to bracket: the ledger rows run to bracket/16:55), MNQ sizing at $1,000 risk (NQ whole lots cannot do 60-90 pt stops at $1,000), per-trade variable risk for sst and E1A (D3SD).
- Update these specs after D3SA (DS3_SESSION2_A_D6.md): fill-basis columns (STORED / MEASURED / CONSERVATIVE) are not yet in the specs.
