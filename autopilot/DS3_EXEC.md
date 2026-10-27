# DS3_EXEC - executability verdicts (D3X, 2026-10-26)
Harness (independent of the library code path): l2vast/ds3/code/x_replay.py (bars, NT8 indicators, ET sessions, fills), x_rsi2.py, x_tb.py (online OnBarClose state machines: ORB, Renko-on-1-min, Supertrend, parameter re-fit, NT8-causal gap/early-close rules), x_locks.py, x_tf1.py, x_st10.py. Identity limit 2% of trades.

## Harness validation on known STRUCT48 sleeves (vs l2vast/struct48/out/<sleeve>_trades.parquet)
RSI2C_s20 NQ: 312/312 trades identical (0 mismatches, net $ equal). ES_RSI2_t10: 301/301 identical. Both DELIVERABLE (15:55 ET 1-min data, market orders, 2 x ATR14 stop for NQ); both are DEAD as DS3 books (<3 trades/wk, placebo), so no spec was written.

## Per book
| book | track verdict | exec verdict | identity (library vs replay) | note |
|---|---|---|---|---|
| ST10 (live DS2 ST book) | CANDIDATE (D3L) | DELIVERABLE | 1.07% entries, 1.40% entry+exit | already an NT8 strategy; entry window inferred from library rows; P9 fill mapping not re-derived. DS3_SPEC_ST10.md |
| TB7_ORBNY_k3_P60_N | CANDIDATE | DELIVERABLE | 0.00% (library flag), 0.00% NT8-causal | needs monthly parameter file (re-fit regenerated: 45/45 months match). DS3_SPEC_TB7_ORBNY_k3_P60_N.md |
| TB9_RENKO_c2_k1_P60_N | CANDIDATE (book bar DEAD per D3L) | DELIVERABLE | 0.00% / 1.01% | Renko logic on 1-min closes (not NT8 Renko bars); library flattens on a following data gap using hindsight, causal rule differs on 61 trades. Lock-dependent edge. Spec written |
| TB1_ST_k15_P60_N | CANDIDATE | DELIVERABLE | 0.00% / 0.02% | not in portfolio; spec written |
| TB9_RENKO_c5_k1_A3_N | DEAD after exact locks | rule DELIVERABLE, NOT A BOOK | 0.00% / 0.06% | spec marked NOT A BOOK |
| TF1_FOMC_NY block | CANDIDATE (filter) | DELIVERABLE (date-list gate) | proxy book 0.04% (2/5135), blocked set identical (82/82; 56 in WF) | FOMC list must be extended yearly; tested only on a proxy book |
| HM10, WT7 | pool members, not selected | not specified (not requested; live DualStrat books) | not re-derived | |
| TA MBO7 setups (TA_MBO7_*) | DEAD | NOT DELIVERABLE | n/a | need L2/MBO model at runtime (marked by D3A); can stay on the execution server |
| GSHORT_t90 | DEAD | NOT DELIVERABLE | n/a | flagged by D3A |
| other track cells (TA/TC/TD/TE/TF/TH-TK) | DEAD | not specified | n/a | no PASS/CANDIDATE; specs only for PASS/CANDIDATE |

## Cross-cutting findings for the lead
1. All T-B series use closed-trade locks; D3B/D3L's exact MTM re-score (EXACT_*) is the one to quote (7b in each spec).
2. The T-B library flags force-flat on a bar followed by a data gap (hindsight); the NT8-causal rule is in the specs; effect <= 1.1% of trades.
3. The T-B ORB/Renko/ST books depend on a monthly 6-month walk-forward parameter file (box-published); fixed-centre versions are weaker for ORB/ST.
4. Early closes (13:00/13:15 ET, Good Friday 09:15) force-flat on the final bar; the NT8 code needs the CME calendar.
5. DS2 ST10 identity covers base trade rows only; sub-minute tie-breaking and the P9 mapping come from the 1-s tape.
Specs: autopilot/DS3_SPEC_{ST10,TB7_ORBNY_k3_P60_N,TB9_RENKO_c2_k1_P60_N,TB1_ST_k15_P60_N,TB9_RENKO_c5_k1_A3_N,TF1_FOMC_NY_block}.md; identity JSONs in l2vast/ds3/spec/.

## Addendum: T-ENTRY PASS series (2026-10-26, D3X)
All five PASS cells are DELIVERABLE (1-min/3/5/10-min bar signals, fixed 60/60 bracket, no L2 at runtime). The direct-L2 series additionally assume the S10x1 slicing + XJ3 stop-join execution layer (second-level timers, unvalidated live). Replay: l2vast/ds3/code/x_te.py vs out/te/direct_tabs.pkl; specs autopilot/DS3_SPEC_{TE6_st10m_n7_m3.0, TE6_st10m_n10_m3.0 (= TE1_st_10m), TE6_st10m_n14_m3.0, TE7_emax5m_f30_s50, TE7_kelt3m_n14_m1.0}.md, identity JSONs in l2vast/ds3/spec/.
| cell | n library | entry mismatch | entry+exit mismatch | exit tolerance +/-2 min |
|---|---|---|---|---|
| TE6_st10m_n10_m3.0 | 2377 | 0.42% | 0.76% | 0.63% |
| TE6_st10m_n7_m3.0 | 2382 | 0.59% | 1.05% | 0.92% |
| TE6_st10m_n14_m3.0 | 2425 | 0.37% | 0.74% | 0.62% |
| TE7_emax5m_f30_s50 | 2315 | 1.17% | 1.38% | 1.34% |
| TE7_kelt3m_n14_m1.0 | 8504 | 0.51% | 0.83% | 0.73% |
| TE1_st_10m | 2377 | 0.42% | 0.76% | 0.63% |

CANDIDATE cells were not specified (lead has not selected them). Note the T-ENTRY Supertrend flips on the CURRENT-bar band and seeds ATR with H-L; a textbook Supertrend is a different system.

### TE6 st10m vs live WT10 (duplicate question)
Verdict: DISTINCT rule, partly redundant (not a renamed WT10). WT10 = Wilder ratchet trail on Close (ATR14 x3.0, EMA off, blackout 09:00-09:58 and 15:00-17:59); TE6 = median-price Supertrend (ATR 7/10/14 x3.0), no 09:00 blackout. My WT10 replay reproduces the forward CSV 69/69 entries. Flip bars on the same 10-min bar and side: n7 1979/4007, n10 2333/3933, n14 2704/3917. Trade entries sharing a 10-min bar and side with WT10: n7 40%, n10 49%, n14 59% (within +/-1 bar 51/61/69%); unlocked weekly gross correlation 0.52/0.61/0.67. Treat the three as one cluster with WT10 (n14 closest to a duplicate). Why WT10/WT7 look small: WT10 itself is not (census: 8-ct library 8,377/wk, Sharpe 2.04, about $85 per lot-trade vs about $69 for TE1 at 12 trades/wk, both ~12 trades/wk); the small number is DS2_WT7_pb (775/wk), a different 1-min book (ATR20 x2.0, EMA100, stop 45, 0.75R, trade-health on). WT10 has not been rescored on the TE direct-L2 cost basis, so the cost-basis difference is unquantified. Under V2 the st10m cells are neighbours of the scored WT10 family, not new edges.

## Addendum 2026-10-27: sub-minute pullback (D3PB4)
TB4D_volume_00_volume_1000_ST15_E20_1_T1 (the only mapped PASS of D3PB4 so far): independent tick replay (own tape cache, own volume-1000 bar builder, own as-of ST15/EMA20-1m/T1 state machine, own tick walk of the 60/60 bracket) gives 0.58% entry mismatch and 0.62% entry+exit mismatch over 8,082 trades (limit 2%); 534,660 of 534,661 bars have identical completing-tick timestamps. DELIVERABLE WITH CONDITIONS: (1) NT8 volume bars come from the feed's Last ticks, the library from tape trade events, so bar boundaries must be checked in Sim; (2) the order is sent on the bar-completing tick (latency/OnBarClose semantics to be confirmed in Sim); (3) D3PB4's direct-L2 replay for the cell is not finished (coverage 1.9%), costs are mapped. Spec autopilot/DS3_SPEC_TB4D_volume_00_volume_1000_ST15_E20_1_T1.md, identity JSON in l2vast/ds3/spec/. Other D3PB4 cells (time_15s/30s, tick, range, Renko bars; HMA55/EMA200/PSD regimes; other levels) are CANDIDATE/DEAD and not yet replayed; the harness supports volume bars + ST regime + E20_1 + T1/T2 now and is extendable.
