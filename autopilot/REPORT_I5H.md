# REPORT I5H - Family H: Josh's NT8 strategies ported to the harness (BoS/CHoCH, fractal S/D, ultraZen, RangeBreak retrace, FlowEdge OFI, STStrat flip+retrace)

**Verdict (UPDATE 2, exec_engine ECON): 3-min clock: NO LEAD (0 of 140 null-passing books clear gate 3). Volume clock V1: 7 of 93 clear gate 3 (chance ~3.4), 1 LEAD (I5H-H2-a56ba2ee|V1|ooat, fails plateau, positive only under one-order-at-a-time) and 1 LEAD-weak; 0 FOUND-PENDING. Pair-side resting books re-run through exec_engine on an uncoupled-book approximation: SE1 limit, K96, PULLBACK 5.1 stay NO; K96b and PA3 move LEAD -> NO direction. The sections after UPDATE 2 are the withdrawn stand-in run, kept for the record.**

## UPDATE 2 (exec_engine ECONOMICS, AMENDMENT EXECUTE-FIRST) - SUPERSEDES the stand-in results below
Every number in this section comes from `exec_engine` (code/census/night_ins/exec_engine.py, ap_i5_engine.py; ECON fills: limit/target only on a trade-through of >= 1 tick, stops at the stop or gap open +1 tick, market +1 tick; rules ffw / ooat / nro / stk2 passed explicitly). The stand-in `ap_i5h_osm.py` is retired. Family H code: ap_i5h_det2.py (detectors -> RowSetups), ap_i5h_ex.py (programs -> Intents -> run_program, 200-replicate timing-destroyed null), ap_i5h_gates.py (full gates). Reconciliation of exec_engine with NT8 (REF_LIMIT_ORDERS) was not complete when this ran: every verdict below is provisional until the engine is accepted.

### Family H: 1,632 cells x 4 rules x 2 clocks = 13,056 cell-rules
| clock | cell-rules scored | pre-screen | null p95 passed (non-duplicate books) | gate 3 | chance gate-3 (3.7% of null-passers) |
|---|---|---|---|---|---|
| T3 3-min time bars | 6512 | 226 | 140 | 0 | 5.2 |
| V1 volume clock k1 (V1 = the VC unit built from 1-min volume; NOT tick-built, so it approximates the VC bars) | 5184 | 202 | 93 | 7 | 3.4 |

T3 by family (pre-screen / null passed): H1 14/12; H2 0/0; H3 143/103; H4 16/2; H5 44/21; H6 9/2. Median fill rate: n/a for market programs; duplicates (same book under different rules) 2403.

V1 by family (pre-screen / null passed): H1 30/4; H2 9/9; H3 116/57; H4 0/0; H5 29/16; H6 18/7. Median fill rate: n/a for market programs; duplicates (same book under different rules) 457.

**T3 (3-min): 0 of 140 books clear gate 3** (best all-in uplift +0.14 and it fails clean/H1). The ultraZen (H3) block again dominates the null-passers (74%) without adding to the pair.

**V1 (volume clock): 7 of 93 null-passing books clear gate 3** (chance about 3.4; the seven are 5 near-copies of two H2 zone programs and 2 H5 OFI programs, so the effective number of independent hits is about 3). Full gates for the seven (bootstrap, 2x slippage = entry and stop slippage doubled, worst-decile corr, +-25% plateau, uplift at 20% share):

| book | uplift clean/H1/H2/all | boot lo | 2x-slip uplift clean/H1/H2 | wd corr | plateau | clean Sharpe under ffw / ooat / nro / stk2 | verdict |
|---|---|---|---|---|---|---|---|
| I5H-H2-a56ba2ee|V1|ooat {"f": "H2", "p": 2, "k": 1.5, "edge": "mid", "touch": "first", "inval": "close", "stop": "atr", "rr": 2, "life": 20} | +0.17/+0.55/+0.74/+0.35 | +0.13 | +0.11/+0.49/+0.69 | +0.29 | 0.50 (4 nb) | -0.39 / +0.87* / -0.41 / -0.86 | LEAD (fails plateau; rule-fragile) |
| I5H-H2-ee6ad880|V1|ooat {"f": "H2", "p": 2, "k": 1.0, "edge": "mid", "touch": "first", "inval": "close", "stop": "atr", "rr": 1, "life": 20} | +0.10/+0.60/+0.25/+0.21 | -0.01 | +0.02/+0.52/+0.19 | +0.44 | 0.25 (4 nb) | -2.35 / +0.51* / -2.65 / -3.15 | NO (fails bootstrap / wd / plateau) |
| I5H-H2-d6f0f122|V1|ooat {"f": "H2", "p": 2, "k": 1.0, "edge": "mid", "touch": "first", "inval": "close", "stop": "atr", "rr": 2, "life": 20} | +0.12/+0.87/+0.52/+0.30 | +0.09 | +0.05/+0.79/+0.46 | +0.18 | 0.75 (4 nb) | -1.21 / +0.65* / -1.29 / -1.75 | LEAD-weak (fails 2x slip) |
| I5H-H5-e23efc82|V1|stk2 {"f": "H5", "N": 3, "q": 99, "fl": 0.5, "stop": "origin", "rr": 3, "ctrl": 1} | +0.14/+0.19/+0.15/+0.17 | -0.03 | +0.09/+0.14/+0.11 | +0.22 | 0.50 (8 nb) | +0.06 / +0.06 / +0.06 / +0.92* | NO (fails bootstrap / wd / plateau) |
| I5H-H2-b74a8f25|V1|ooat {"f": "H2", "p": 3, "k": 1.0, "edge": "mid", "touch": "first", "inval": "close", "stop": "atr", "rr": 2, "life": 20} | +0.14/+0.36/+0.19/+0.20 | +0.00 | +0.08/+0.30/+0.15 | +0.51 | 0.67 (6 nb) | -0.43 / +0.77* / -1.07 / -1.30 | NO (fails bootstrap / wd / plateau) |
| I5H-H5-1afe7aff|V1|ffw {"f": "H5", "N": 2, "q": 99, "fl": 0.5, "stop": "origin", "rr": 2, "ctrl": 1} | +0.11/+0.11/+0.29/+0.15 | -0.04 | +0.05/+0.06/+0.25 | -0.06 | 0.50 (4 nb) | +0.73* / +0.73* / +0.73* / +0.52* | NO (fails bootstrap / wd / plateau) |
| I5H-H5-7e73308d|V1|ffw {"f": "H5", "N": 2, "q": 99, "fl": 0.382, "stop": "origin", "rr": 3, "ctrl": 0} | +0.14/+0.12/+0.46/+0.22 | +0.02 | +0.11/+0.09/+0.44 | +0.09 | 0.00 (6 nb) | +0.81* / +0.54 / +0.60* / +0.29 | NO (fails bootstrap / wd / plateau) |

(* = beats its own null p95.) Reading: the supply/demand zone programs (H2, mid-zone limit, close-through invalidation, 1-ATR stop, RR 1-2, volume clock) are standalone-positive on all three spans (clean 0.5-0.9, H1 1.9-3.2, H2 0.9-2.5) **only under the one-order-at-a-time rule**; under first-fill-wins OCO, newest-replaces and stack-2 the same programs lose (clean Sharpe -0.4 to -3.2). A result that exists in one order-handling rule only is an artefact risk of the placement filter, not a robust edge, and the null p95 under ooat is itself negative (-0.5 to -2.3: random deep limits lose on adverse selection), so passing it is weak evidence. The best, I5H-H2-a56ba2ee|V1|ooat, passes gate 3 (+0.17/+0.55/+0.74), bootstrap (lo +0.13), 2x slippage (all spans >= +0.11), worst-decile corr +0.29, but fails the plateau (2 of 4 neighbours) and the circular-shift null is reported only (p95 +0.36 vs all-in +0.35). LEAD status, H1/H2 read once (non-virgin for any follow-up), requires: tick-built VC bars (the V1 clock here is a 1-min-volume approximation), the NT8 reconciliation of exec_engine, and the cross-rule explanation. Chance expectation for the number of new passes at gate 3 in this family: about 3.4 of the V1 null-passers; observed 7 (about 3 independent).

Insurance metrics and sized dollars of the best book (I5H-H2-a56ba2ee|V1|ooat; sleeve scale 1.03 x its R-sized book = 100% of pair risk; 20% share shown; R-sized contracts per trade: qty = min(24, 9,600/(stop pts x 20)))

| span | row | Sharpe | Sortino | MAR | net $ (span) | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | 1,329,959 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | pair + 20% sleeve | 1.63 | 3.10 | 5.58 | 1,488,205 | -84,264 | -80,382 | 266,492 | -92,833 | 40.0 |
| clean | sleeve at 20% size | 0.87 | 1.32 | 1.58 | 158,246 | -25,275 | -22,208 | 100,335 | -28,863 | 38.1 |
| H1 | pair | 2.83 | 6.09 | 3.91 | 593,797 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | pair + 20% sleeve | 3.38 | 7.59 | 4.64 | 702,530 | -71,978 | -60,479 | 151,474 | -102,104 | 39.3 |
| H1 | sleeve at 20% size | 1.87 | 3.24 | 2.23 | 108,732 | -23,880 | -22,965 | 48,728 | -23,942 | 32.1 |
| H2 | pair | 2.48 | 5.08 | 3.77 | 819,748 | -81,089 | -79,185 | 217,425 | -82,524 | 41.7 |
| H2 | pair + 20% sleeve | 3.22 | 7.32 | 4.99 | 1,071,153 | -90,555 | -76,464 | 214,842 | -98,586 | 27.8 |
| H2 | sleeve at 20% size | 2.49 | 4.75 | 2.71 | 251,405 | -34,635 | -27,747 | 92,786 | -42,582 | 30.6 |
| all | pair | 1.90 | 3.71 | 9.79 | 2,743,504 | -79,220 | -78,243 | 280,110 | -82,524 | 42.3 |
| all | pair + 20% sleeve | 2.25 | 4.52 | 12.24 | 3,261,887 | -87,644 | -80,438 | 266,492 | -102,104 | 37.5 |
| all | sleeve at 20% size | 1.48 | 2.50 | 5.17 | 518,384 | -27,421 | -24,044 | 100,335 | -42,582 | 35.1 |

### Pair-side resting-order books re-run through exec_engine (ECON), rules ffw / ooat / nro / stk2
**Approximation (stated):** exec_engine is single-instrument and single-book. ST and HM are run as two INDEPENDENT books (own position, own order-handling rule), their daily P&L summed; the pair's FIFO netting between the books and the live day/week locks (per-book 5R/-2R, combined cap, week floor) are NOT applied, and sub-minute windows (SE1's 15 s) cannot be represented on the 1-minute grid (SE1 60 s cells = one-row life; the 15 s cells are not scored). The market-entry CONTROL under the same approximation reads weekly Sharpe 1.04/2.69/0.87 clean/H1/H2 against 1.46/2.83/2.48 for the live account, so levels are not comparable to the live pair; the evidence is the sign and size of the delta against the control. A final verdict on these books needs the pair account layer in the engine.

Delta of weekly Sharpe vs the control (clean / H1 / H2 / all-in):

| program | ffw | ooat | nro | stk2 |
|---|---|---|---|---|
| SE1 limit at signal close -0 tick, 1-min life, both books | -0.30/-0.44/-0.38/-0.33 | -0.30/-0.44/-0.38/-0.33 | -0.30/-0.44/-0.38/-0.33 | -0.25/+0.09/-0.17/-0.18 |
| SE1 limit at signal close -1 tick, 1-min life, both books | -0.30/-0.25/-0.59/-0.37 | -0.30/-0.25/-0.59/-0.37 | -0.30/-0.25/-0.59/-0.37 | -0.09/+0.14/-0.32/-0.15 |
| K96 stop-entry at flip level +1 tick oneshot, both books | -1.02/-0.16/-1.30/-0.91 | -0.73/-1.53/-0.75/-0.87 | -1.02/-0.16/-1.30/-0.91 | -1.08/-0.28/-0.87/-0.87 |
| K96 stop-entry at flip level +1 tick rearm, both books | -1.02/-0.16/-1.30/-0.91 | -0.73/-1.53/-0.75/-0.87 | -1.02/-0.16/-1.30/-0.91 | -1.08/-0.28/-0.87/-0.87 |
| K96b HM stop-entry (causal level, one-shot) + ST at market | -0.09/+0.75/-0.51/-0.13 | +0.37/-0.92/-0.30/-0.05 | -0.09/+0.75/-0.51/-0.13 | -0.33/-0.32/-0.03/-0.25 |
| PA3 o2_L60 HM stop-entry (causal, offset 2 ticks, 60 min) + ST at market | -0.10/+0.57/-0.74/-0.21 | +0.35/-1.18/-0.35/-0.13 | -0.10/+0.57/-0.74/-0.21 | -0.27/-0.43/-0.13/-0.27 |

PULLBACK pair-side 5.1 re-timed resting limits (REB form: limit at min(signal close, level), level in EMA9(1m), EMA20(1m), EMA20(5m), session VWAP, updated each minute for N in 5/15/30/60 min, OCO per signal, fresh 60/60 bracket from the limit; 64 cell-rules): the delta vs the market control is negative in EVERY cell-rule (best clean delta -0.06, best all-in -0.33; mean all-in -4.46). The ABS form (original absolute exits of the recorded rows) cannot be rebuilt without the recorded exit prices: not re-run.

### Both-direction summary for REPORT_BASIS_RESCORE.md (this worker's scope)
| book | prior verdict | exec_engine ECON result | change |
|---|---|---|---|
| Family H, 3-min (stand-in first run withdrawn) | n/a | 0 gate-3 of 140 null-passing books | none (NO) |
| Family H, volume clock V1 (new) | n/a | 7 gate-3 of 93 (chance ~3.4); 1 LEAD (H2 zone, ooat only), 1 LEAD-weak, 5 NO | new pre-registered stage-1 passes, H1/H2 read once (non-virgin) |
| SE1 limit cells (60 s life, pair proxy) | NO | negative vs control under ffw/ooat/nro (-0.30 clean), stk2 -0.25/+0.09/-0.17 | NO -> NO |
| K96 stop-entry both books | NO | -1.0 clean, -0.9 all-in in every rule | NO -> NO |
| K96b HM stop-entry (causal level) + ST market | LEAD (+0.72/+0.66/+0.25 in the live account) | clean -0.09 (ffw, nro) / +0.37 (ooat) / -0.33 (stk2); H2 negative in all rules, H1 +0.75 only under ffw/nro | **LEAD -> NO direction** (proxy; needs the pair account layer) |
| PA3 o2_L60 HM stop-entry | LEAD | clean -0.10/+0.35/-0.10/-0.27, H2 negative in all rules | **LEAD -> NO direction** (proxy) |
| PULLBACK pair-side 5.1 (REB, 64 cell-rules) | NO | all negative | NO -> NO |
| PULLBACK strategy cells, PX*, PA5-PA10, SW*, SX, SK, WT-10 | - | market-entry books: not resting-order programs, not re-run | BASIS-OK |
New passes (NO -> LEAD): none among pre-existing books; the only new pass is family H V1. Chance expectation for new gate-3 passes among the V1 null-passers: 3.4.

---
# (superseded) stand-in run

**Verdict: NO LEAD, NO FOUND-PENDING. 1,632 distinct cells x 4 order-handling rules = 6,528 order-program cell-rules scored through stage 1 under an EXECUTABLE order-state machine; 283 pass the pre-screen (>= 100 clean trades, positive weekly Sharpe in both clean halves), 120 of those beat their own timing-destroyed null p95 (200 replicates; 84 distinct cells), and 0 of the 222 null-passing cell-rules (120 distinct books after the series-hash dedupe; the other 102 are the same book under a different order-handling rule) clear gate 3 (additive 20% uplift >= +0.10 on clean AND H1 AND H2).** Chance expectation: the null gate passes 5% of the pre-screened cells by construction (about 14 of 283); gate 3 passes about 3.7% of selected random cells (SW calibration) = about 8 of 222; observed 0. The standalone null is passed far more often than 5% (mostly H3 ultraZen: trend-stack timing beats random timing in a rising clean span) but none of it adds to the pair on all three spans.

## Basis
- Pre-registered in PREREG_IDEAS5000.md ('FAMILY H appendix') before scoring. The FIRST run of this family (independent replay, placement-order selection by `ap_ict_core.sim`) was BASIS-VOID under AMENDMENT FVG-REALIZABLE and is WITHDRAWN (registry rows marked `void_basis`); no number of that run is reported. The independent-replay path is removed from `ap_i5h.py`.
- Engine: `ap_i5h_osm.py`, an executable order-state machine over the 1-minute path (ECONOMICS fills: a limit fills only when price trades THROUGH the level by >= 1 tick; stops fill at the stop plus 1 tick, stop gaps at the open; target limit without slippage; exits, 360-min hold cap, 16:55 flat as ICT core). Every order is placed at the close of its signal bar and lives until fill, expiry (life), the 16:55 session end; rule applied FORWARD in time, no post-hoc choice among fills: `ffw` first-fill-wins OCO (one OCO group while flat, first fill cancels the rest, placement blocked while a position is open), `one` one order at a time, `newest` newest replaces oldest, `stack2` up to two concurrent positions. The rule is an explicit factor of every cell (4 rows per cell, `CELLS.csv` verdict column `rule=`). Stop-entry control forms (H1/H2/H4/H5/H6 'ctrl') are represented as market orders on the close of the confirming bar (a resting stop-entry is a family-E arm); they are order programs too. exec_engine (outputs/exec) did not exist when this ran: results must be re-run through it when it is accepted (the state machine is a stand-in with the same ECONOMICS fill rule; NOT yet reconciled to NT8).
- Clean-only selection on 2023-08..2025-07, NQ 3-min time bars. VC k1 (volume clock) stage 1 NOT run: needs the tick-built bars of the engine API (deviation logged); stage 2 (clocks/instruments) not run because no stage-1 cell passes gate 3 (a stage-2 expansion would be a new search; the family-K refill will mutate the null-passers).

## Definitions used (quoted from the repo where it exists)
- H4 RangeBreak: t4_f_core.py ('approximate port': range = 18:00..09:29 ET high/low, from 09:30, stop = opposite side of the range, target tm x range width, flat 16:55) with a retrace limit instead of the stop entry. H6 STStrat: the pair's Supertrend (night_ind.supertrend, Wilder ATR, close source; ATR120/2.0/EMA200 on 1-min = ATR40/2.0/EMA67 on 3-min).
- NOT in the repo, 'author-defined, needs your confirmation': H1 BoS/CHoCH (swing pivots, close-through breaks), H2 fractal supply/demand zones, H3 ultraZen (33/50/200 EMA stack + inverted FVG), H5 FlowEdge (OFI from trades with aggressor). Exact grammar: PREREG appendix.

## Counts by family and rule
| family | cells | cell-rules | scored | fill rate (median) | pre-screen | null p95 passed | gate 3 |
|---|---|---|---|---|---|---|---|
| H1 BoS/CHoCH | 270 | 1080 | 1080 | 0.77 | 13 | 0 | 0 |
| H2 fractal supply/demand | 306 | 1224 | 1224 | 0.48 | 0 | 0 | 0 |
| H3 ultraZen | 216 | 864 | 864 | 0.74 | 205 | 116 | 0 |
| H4 RangeBreak retrace | 336 | 1344 | 1344 | 0.50 | 24 | 0 | 0 |
| H5 FlowEdge OFI + retrace | 270 | 1080 | 1080 | 0.74 | 31 | 4 | 0 |
| H6 STStrat flip + retrace | 234 | 936 | 936 | 0.10 | 10 | 0 | 0 |

By rule (all families): ffw: pre-screen 72, null passed 28; one: pre-screen 75, null passed 37; newest: pre-screen 70, null passed 29; stack2: pre-screen 66, null passed 26. The four rules differ little for market-like and sparse programs; `one` and `stack2` differ most for H6 (dense one-bar retrace orders: fill rate 10%) and H3.

## Stage 3 (H1/H2 read once for the null-passers; additive 20% share, sleeve scaled to the pair's clean weekly sd)
| family | null-passing cell-rules | gate 3 | H1 standalone Sharpe > 0 | H2 standalone Sharpe > 0 | best all-in uplift |
|---|---|---|---|---|---|
| H1 | 12 | 0 | 0 | 4 | +0.07 |
| H3 | 168 | 0 | 76 | 161 | +0.10 |
| H4 | 4 | 0 | 4 | 4 | +0.10 |
| H5 | 28 | 0 | 15 | 0 | +0.07 |
| H6 | 10 | 0 | 4 | 6 | +0.05 |

H2 (306 cells) has no cell passing the pre-screen: zone entries fill only 48% of the time and none is profitable in both clean halves.

Best eight null-passers by all-in uplift (none is a LEAD; gate 3 needs +0.10 on all three spans):
| cell-rule | spec | uplift clean/H1/H2/all | standalone Sharpe clean/H1/H2 | worst-week change % |
|---|---|---|---|---|
| I5H-H3-987983df|stack2 | {"f": "H3", "stack": "part", "m": 0.25, "win": 10, "entry": "edge", "ex": "sw_rr2"} | +0.06/+0.09/+0.24/+0.10 | 0.90/0.94/1.75 | +17.6 |
| I5H-H4-57e2e357|one | {"f": "H4", "buf": 0.25, "cut": "1000", "entry": "mkt", "stop": "atr", "tm": "w1.0", "life": 0} | +0.15/+0.11/-0.07/+0.10 | 1.17/1.01/0.78 | +11.1 |
| I5H-H4-57e2e357|newest | {"f": "H4", "buf": 0.25, "cut": "1000", "entry": "mkt", "stop": "atr", "tm": "w1.0", "life": 0} | +0.15/+0.11/-0.07/+0.10 | 1.17/1.01/0.78 | +11.1 |
| I5H-H4-57e2e357|stack2 | {"f": "H4", "buf": 0.25, "cut": "1000", "entry": "mkt", "stop": "atr", "tm": "w1.0", "life": 0} | +0.15/+0.11/-0.07/+0.10 | 1.17/1.01/0.78 | +11.1 |
| I5H-H4-57e2e357|ffw | {"f": "H4", "buf": 0.25, "cut": "1000", "entry": "mkt", "stop": "atr", "tm": "w1.0", "life": 0} | +0.15/+0.11/-0.07/+0.10 | 1.17/1.01/0.78 | +11.1 |
| I5H-H3-f45426d7|stack2 | {"f": "H3", "stack": "full", "m": 0.25, "win": 10, "entry": "edge", "ex": "sw_rr2"} | +0.08/+0.03/+0.18/+0.08 | 0.96/0.08/1.65 | +17.6 |
| I5H-H3-83bfe77d|stack2 | {"f": "H3", "stack": "part", "m": 0.25, "win": 5, "entry": "mkt", "ex": "atr1.0"} | +0.07/-0.32/+0.36/+0.08 | 0.91/-0.94/2.21 | +30.6 |
| I5H-H3-83bfe77d|ffw | {"f": "H3", "stack": "part", "m": 0.25, "win": 5, "entry": "mkt", "ex": "atr1.0"} | +0.10/-0.24/+0.22/+0.08 | 1.03/-0.52/1.75 | +26.2 |

## Insurance metrics of the best cell-rule (I5H-H3-987983df|stack2; not a lead; sleeve at 20% share = 0.18x its 1-contract-risk scale; $ per week at 20% share)
| span | row | Sharpe | Sortino | MAR | CVaR5 | CVaR10 | maxDD | worst week | %neg wk |
|---|---|---|---|---|---|---|---|---|---|
| clean | pair | 1.46 | 2.78 | 4.75 | -78,736 | -78,009 | 280,110 | -81,874 | 42.9 |
| clean | pair + 20% sleeve | 1.52 | 2.84 | 4.78 | -91,863 | -86,764 | 312,444 | -97,040 | 41.0 |
| clean | sleeve alone (20% sized) | 0.90 | 1.50 | 1.79 | -20,407 | -18,133 | 91,419 | -25,626 | 52.4 |
| H1 | pair | 2.83 | 6.09 | 3.91 | -77,610 | -66,030 | 151,713 | -78,287 | 39.3 |
| H1 | pair + 20% sleeve | 2.91 | 5.91 | 4.29 | -86,920 | -73,778 | 147,928 | -90,207 | 39.3 |
| H1 | sleeve alone (20% sized) | 0.94 | 1.59 | 0.75 | -15,275 | -14,157 | 53,926 | -17,992 | 46.4 |
| H2 | pair | 2.48 | 5.08 | 3.77 | -81,089 | -79,185 | 217,425 | -82,524 | 41.7 |
| H2 | pair + 20% sleeve | 2.72 | 6.21 | 4.18 | -79,351 | -73,425 | 236,834 | -87,736 | 44.4 |
| H2 | sleeve alone (20% sized) | 1.75 | 3.15 | 2.75 | -29,955 | -26,303 | 61,648 | -31,431 | 41.7 |
| all | pair | 1.90 | 3.71 | 9.79 | -79,220 | -78,243 | 280,110 | -82,524 | 42.3 |
| all | pair + 20% sleeve | 2.00 | 3.93 | 9.98 | -90,416 | -84,070 | 312,444 | -97,040 | 41.7 |
| all | sleeve alone (20% sized) | 1.14 | 1.96 | 4.03 | -23,661 | -20,431 | 92,820 | -31,431 | 49.4 |

## Re-score of other resting-order books under the executable machine (AMENDMENT EXECUTE-FIRST item 4)
- PULLBACK stage-1/2 strategy cells (4,775 NQ cells, ES/RTY screens, 12 finalists): not resting-order books (market at the next open; BASIS_AUDIT_PART_PB.md): nothing to re-score.
- SE1 limit cells, K96/K96b/PA3 stop-entry books, PULLBACK pair-side 5.1 re-timed limits, Pair-limit: two-book pair-engine books (FIFO netting, live day/week locks); they need the pair order program in exec_engine and CANNOT be reproduced with this single-book machine without rebuilding the pair netting. PENDING exec_engine; reported to a778 as pending, not as results. The audit expects no NO -> LEAD change for SE1 (all limit cells -0.13..-1.10) and PULLBACK 5.1 (mean -0.71); K96b/PA3 are the cells most likely to move (they are LEADs that already fail 5-6 gates).

## Executability / reading
- All programs are order programs: bar-close signal -> market or limit entry with attached stop and target (OCO) -> time/session flat; NT8 can run them as ordinary strategies on a 3-min series. Margin/sizing: R-sized (qty = min(24, 9,600/(stop pts x 20))), same as the FVG line, so 20% share is about 3.4 NQ-equivalents.
- The H3 result deserves a note: 20-25% of ultraZen cells beat the random-timing null with positive standalone Sharpe on all three spans (clean/H1/H2 median positive), yet no cell adds >= +0.10 to the pair on clean, H1 and H2. This is the typical signature of trend-aligned long exposure in a rising sample (the null keeps sides and geometry but randomises time, so it does not reproduce trend alignment); the 'drift/clock-matched' null of the brief is the next check if any H3 cell is carried forward (family K mutants).

Code: code/census/night_ins/ap_i5h_det.py, ap_i5h_osm.py, ap_i5h.py, ap_i5h_rep.py; data outputs/autopilot/i5h/; registry outputs/ideas5000/CELLS.csv, TALLY.csv.

DONE I5H
