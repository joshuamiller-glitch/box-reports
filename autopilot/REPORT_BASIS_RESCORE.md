# REPORT BASIS RESCORE (amendments FVG-REALIZABLE + EXECUTE-FIRST) - final, compiled by a778, 2026-10-17
**Verdict: under executable order handling (exec_engine v2 ECON / exec_engine_x with the pair account layer / the owners' tick-level state machines) NO resting-order book in the library or the reports is positive on all three spans, apart from six cell-rule pairs that restart as stage-1 cells (section 4), which is what chance alone predicts (section 5). Every FOUND-PENDING / LEAD that rested on independent replay + sequential selection is VOID or NO. NO -> LEAD changes: none that survive. LEAD / FOUND-PENDING -> NO/VOID: the FVG line, the ICT C2 / C12 LEADs, RZ1_GC / RZ1_CL / RZ9 / FVG_GCCL (FOUND-PENDING-REPLICATION), RZ2_BTC, K96b, PA3. Engine caveat: results are v2 (price priority) unless marked; nothing here is a final resting-order verdict until the NT8 Analyzer reconciliation of REF_LIMIT_ORDERS.csv is accepted.**

## 1. Work list and status (basis/WORKLIST.csv)
| scope | owner | cells re-run | rules | engine | status |
|---|---|---|---|---|---|
| ICT study: 1,978 limit cells (of 3,878 grid cells) flagged; 21 report-level / selected cells re-scored | a41bb | 21 cells x 5 rules (FROZEN, FFW, ONE, NEWEST, STACK2) | ffw / ooat / nro / stk2 | tick-level state machine + exec_engine v2 | DONE (BASIS_RESCORE_ICT_VERIFIED.csv); 1,900 ICT cells are market entries: basis OK |
| FVG line (P1, E1, IMP3 tf3 m1.5, VC k1 m1.125, S1-S3, FV2-FV19 siblings, G6/G7/G9 variants) | a41bb | ~32 cells x 4 rules, tick and 1-minute | ffw / ooat / nro / stk2 | per-order tick paths + state machine; exec_engine v2 | DONE (REPORT_FVG_REALIZABLE.md) |
| GC / CL / RZ transplants: RZ1 (7), RZ2 (2), RZ9, FVG_GCCL, RZ7 | a027 + a41bb | 13 books x 4 rules (GC / CL tick) | 4 | a027's own machine; exec_engine v2 | DONE (own machine); exec_engine tick-level GC/CL/RZ9 replay not done |
| Q40 / Q41 passive variants | a027 | 10 objects x 4 rules x (d, W) variants + market control | 4 | exec_engine v1 ECON (single working order per signal: unaffected by the v1 tie-break defect) | DONE |
| Pair-side resting books: K96, K96b, PA3 (15-cell grid), SE1 limit cells, PULLBACK pair-side 5.1 | a3a74 + a778 | 1 control + ~20 cells | per-book ooat + NT8 lot netting; ffw / ooat / nro / stk2 proxies | exec_engine_x ECON, 1-second grid, two-book account | DONE (REPORT_PAIR_XENGINE.md; control reproduces the live pair within 0.00 / 0.02 / 0.06 weekly Sharpe) |
| Family H (stage 1, 3-min and V1) | H worker | 140 + 93 null-passing books | 4 | exec_engine v2 | DONE (I5H_BASIS_RESCORE_PART.md) |
| Families E, J | E/J worker | 1,120 cells | 4 | exec_engine v2 | DONE: with the corrected engine 0 LEAD / 0 FOUND-PENDING (v1 had shown 6 apparent winners) |
| Families G, I (IDEAS-5000) | a778 | G 3,152 + I 1,296 programs (I with paired market controls) | 4 | exec_engine v2 ECON | DONE: 0 LEAD (G 66 null passers vs 157 expected; I 10 vs 64; limit net R - market control net R = about 0.00 R) |
| Market-entry books (SW, BM, BJ, Q, B, L, K, GC fade, I9, ES dip, WT-10, PULLBACK strategy cells, PX*, 1,900 ICT market cells) | a027 / a3a74 / a41bb / a778 | not re-run | market | reconciled engine | BASIS-OK: evidence ap_b_base.sim_events (`ep=o[i]`, `if i<=last: continue`), ap_pb_core.sim, ap_i_common.seq_nooverlap; closed by BASIS_REVIEW_CLOSURE.md (160 REVIEW rows cleared) |
| Derived books: RY5 (FVG E1 sleeve x K4 factor, ap_fv_e1.trades), RU2 (ap_ru_sim.py lines 27-29 selection over the filled set) | a778 | not re-run | - | - | BASIS-VOID (derived); library flag total 1,629 of 40,041 |

## 2. Both-direction verdict table
| book / family | prior label | executable-basis result | new label |
|---|---|---|---|
| FVG P1 / E1 / IMP3 tf3 m1.5 / VC k1 m1.125 and siblings FV2-FV19 | FOUND-PENDING / LEAD (counted once) | tick-level and v2: net R/trade -0.03 to -0.07 under ffw / ooat / nro / stk2 on IMP3, VC, P1, E1; bands_by_rule.json the same | VOID (not a promotion candidate); no cell positive on all spans except section 4 |
| ICT C2 FVG cells (8 verified) | LEAD (report level) | ffw net R -0.035 .. -0.070, Sharpe -1.4 .. -3.3 clean | LEAD -> NO |
| ICT C12_SB10_tf1_m0.25 | LEAD (vol-matched gates) | ffw clean -1.02, H1 -1.22, H2 positive only | LEAD -> NO |
| ICT other selected cells (C3 BRK, C13 macro, C5 OTE, C1 CHOCH) | NO | stay NO (C1 / C13 market entries unchanged) | NO -> NO |
| RZ1_GC, RZ1_CL, RZ9 basket, FVG_GCCL GC / CL / RZ9 tick | FOUND-PENDING-REPLICATION (-NT8-SPEC) | all four rules negative or non-positive on every span (GC tick best +0.03 R, uplift +0.22 / +0.13 / -0.16) | -> NO |
| RZ2_BTC | LEAD | ffw Sharpe -2.4 / -3.3 / -4.6 | LEAD -> NO |
| RZ1 ES/RTY/YM/ZN/6E, RZ2 ETH, RZ7 | NO | unchanged | NO -> NO |
| K96b (HM stop entry) | LEAD (non-virgin) | exec_engine_x ECON + account layer: no cell uplift >= +0.10 on all three spans; H1 / H2 turn negative (K96b +0.34 / -0.42 / -0.53) | LEAD -> NO |
| PA3 (15-cell HM stop-entry grid) | LEAD | best cells +0.40 / -0.63 / -1.61; none passes | LEAD -> NO |
| K96 (both books), SE1 limit cells, PULLBACK pair-side 5.1 | NO | negative in every rule | NO -> NO |
| Q40 / Q41 passive variants (all 10 objects) | NO | passive worse than the market control for 7 of 10 (-$3 .. -$13 per trade); three small positives (ESQ20 +$7, NQQ12 +$2.6, GCQ14 +$1.5) inside the Q40 nulls | NO -> NO |
| Family H V1 clock | new | 7 gate-3 of 93 (chance about 3.4); 1 LEAD (H2 zone, ooat only), 1 weak, 5 NO | new stage-1 passes, H1/H2 read once (non-virgin) |
| Families E, J | new | 1,120 cells: 0 LEAD / 0 FOUND-PENDING on the corrected engine | none |
| Families G, I | new | 0 LEAD on v2 | none |
| RY5 (4), RU2 (6) | LEAD-class (K4-based top of the MONEY list) | derived from voided generators | BASIS-VOID |
| NO -> LEAD | none | | |

## 3. Library and program accounting
BASIS-VOID library books: 1,629 of 40,041 (1,584 ICT limit cells and FVG-line / RZ books from BASIS_VOID_LIST.csv + families ICT_FVG, FV16_VC, FV17, FVG_GCCL, RZ1, RZ2, RZ6, RZ9, RY5, RU2). Assembly input excludes them: best-of-N clean Sharpe 11.16 -> 6.42 (null mean 7.09, p95 7.58, real rank 0.00; best portfolio 6.26 / 1.98 / 0.41), i.e. the library no longer contains a portfolio beyond chance. MONEY re-rank: the live pair is the only PAIR-GRADE book. FORWARD.md: FVG_P1 / E1 / IMP3 / VC in the VOID section (20 active leads, 4 void).

## 4. Fresh stage-1 candidates created by the re-score (H1/H2 NON-VIRGIN; not promoted)
FV:tf=15 under ooat (tick: 2,701 trades, net R +0.043, Sharpe 0.75 / 0.94 / 2.45; v2 1-minute: +0.011), FV:tf=15 stk2 (tick +0.019), G6:NDOG_fade ffw / ooat / nro / stk2 (140 trades, net R +0.17 .. +0.19, Sharpe 0.65 / 2.18 / 0.66). Each enters IDEAS-5000 as a fresh pre-registered stage-1 cell and must pass the standalone null, plateau, 2x slippage and the replication rules before any label.

## 5. Chance expectation for the new passes (FA4 rates, REPORT_FA4.md: gate 3 on 3.53% of selected cells, LEAD-grade 0.97%, FOUND-PENDING-equivalent 0 of 25,664 grid cells, 95% bound about 0.09%)
Cells actually re-run under an executable rule: about 21 (ICT) + 32 (FVG line) + 13 (RZ) + 10 (Q40) + 21 (pair-side) + 93 (H V1) = about 190 distinct cells (x 4 rules = about 760 correlated cell-rule programs), plus the IDEAS-5000 families (E / J 1,120; G 848; I 324; H) counted in their own tallies. Expected by chance among the 190 cells: gate-3 passes about 6.7 (3.53%), LEAD-grade about 1.8 (0.97%), FOUND-PENDING-equivalent about 0 (at most 0.17). Observed: 3 distinct cells (FV:tf=15, G6:NDOG_fade, plus the H V1 zone cell) with all-three-span positives, 7 gate-3 passes in H V1 (chance 3.4) - consistent with chance; no re-score produced a pass that exceeds the chance band, and none is promoted.

## 6. Caveats
exec_engine v1 had a same-row fill-priority defect (v2 fixes it; first-fill-wins / stack results with overlapping orders were optimistic under v1): every row above that is engine-based is v2 except Q40 (v1, single working order, unaffected) and a027's own-machine RZ rows (1-minute own machine agrees with v2 to a median |net R| 0.0046 per cell-rule). Resting-order verdicts stay provisional until the NT8 Analyzer reconciliation. K96b / PA3 / SE1 depend on the two-book pair account layer, validated only on the market control (within 0.06 weekly Sharpe).
DONE BASIS_RESCORE
