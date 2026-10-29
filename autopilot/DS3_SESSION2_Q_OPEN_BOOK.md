# DS3_SESSION2_Q_OPEN_BOOK - T-OPEN follow-up: six NT8 specs, the O6 opening book on the MEASURED basis, and the 09:30-09:59 block question (D3SOB, 2026-10-29)

Research only. No execution-server, chart or live change; no replay launched; no process killed; no credentials. Fees per FEES.md (NQ $4.84 round trip = 0.242 pt, applied inside the MEASURED net points). Prereg l2vast/ds3/prereg/OPENBOOK_prereg.md sha256 `d322b1fc095bf05f12adeae6e87afbb72aa06d7c4332f16ff75a9b6f4034fcb5` (and the PREHOLD sha256 `8ae4c8212fd3acfc1c0c4398455c6f60a7ad5733bbd81e9c3d1f4610608b1d3e`; both recorded in autopilot/DECISIONS.md, hashed BEFORE any book P&L and before HOLD/X). One HOLD+X look (out/ob/looks.jsonl), run once, output kept in out/ob/look_output.txt. Label days after 2026-02-06 never read. Code l2vast/ds3/code/ob/ (ob_lib.py, stageA.py, stageA2.py, stageB.py, specstats.py), outputs l2vast/ds3/out/ob/.

## 1. VERDICT: **DEAD** (O6 book). Failed gates: G3 (beta), G8 (2023 check), G9 (best-of-N). The book does NOT beat the single best cell. Block decision: **KEEP 09:00-09:59 BLOCKED for the whole stack.**
| gate (prereg section 7) | result | numbers (weekly $ at $1,000 risk per trade; MDE = 2.8 x SE) |
|---|---|---|
| G1 n_pre >= 30 | PASS | 603 post-lock PRE trades |
| G2 PRE mean > 0, CI lo > 0 | PASS | +1,772/wk, CI [1,189, 2,356], MDE 820, t 6.05 (selection window) |
| G3 beta: PRE edge CI lo > 0, HOLD edge > 0, AND source beats_beta true for every cell | **FAIL** | replay flip placebo edge PRE +1,972 (CI lo 1,411, MDE 789), HOLD +1,247 (CI lo 379, MDE 1,192) pass; but the source harness random-direction bracket-beta gate is False for all three cells (OR30m_stp, LV_RN_BH, OR15m_stp). 28 of the 30 pool members fail this source gate |
| G4 stack-add PRE r=0.20: d_sharpe>0, CI lo>0, d_maxDD<=0 | PASS | +18,064/wk (CI [11,771, 24,029], MDE 8,353), d_sharpe +0.78, d_maxDD -27.4k |
| G5 cost 2x PRE > 0 | PASS | +1,606/wk |
| G6 year share <= 0.6 | PASS (barely) | 0.589 (2024 $94.9k, 2025 $53.9k, 2026 $12.4k) |
| G7 HOLD mean>0, H25>0, H26>0, stack d_sharpe>0 | PASS (formally) | HOLD +884/wk (CI [-27, 1,795], MDE 1,251: effect is 0.71 MDE, CI includes zero), H25 +589, H26 +2,068 (only 6 weeks), stack d_sharpe +0.35 |
| G8 X (2023-04..2024-01): mean>0 and stack-add d_mean>0 | **FAIL** | X mean **-152/wk** (CI [-1,015, 710], MDE 1,197); stack add -1,553/wk (MDE 12,202), d_sharpe -0.24, d_maxDD +20.3k |
| G9 best-of-N: RC p(PRE)<0.05 AND HOLD t >= z_30 | **FAIL** | RC PRE: observed max t 3.99 vs null p95 2.94, p = 0.0018 (passes in-sample); HOLD t = 1.98 < z_30 = 2.93 (z_87 3.24, z_683 3.79). HOLD mean needed at N=30 is 1,308/wk (SE 447); observed 884 |
Tier: not PASS; because G3 and G8 also fail it is not even CANDIDATE (CANDIDATE = fails only G9). Replay completeness: complete (wave q1, 35 of 35 months, untaken share 0.0 in PRE, X and HOLD for every pool cell). The memguard-killed months (q2 2023-12; q4 2025-06/10/11) belong to other waves, are not in this pool, and were NOT re-run. Disclosures that weaken even the passes: (i) the pool of 30 was HOLD-gated by D3SQ (gate_M0 uses HOLD, H25, H26), so the HOLD numbers above are the optimistic side of a double look; (ii) the three book cells were chosen on PRE by a greedy search over 87 evaluated books; (iii) two of the three cells (OR30m_stp, OR15m_stp, 469 of 603 PRE trades) are stop-entry rules that the replay executed as MARKET orders at the break instant with 1 tick slippage (not a resting stop order); (iv) the lock engine is the closed-trade x_locks approximation (the engine D3SA/D3SQ used for every MEASURED lock number), not the 1-s mark-to-market engine; with locks off the book is PRE +1,757, X -245, HOLD +790 per week (little difference).

## 2. The six NT8 specs (deliverable 1)
Files in autopilot/ (template DS3_SPEC_TOPEN_DR5m.md; each lists the code that produced the definition, section by section):
- DS3_SPEC_TOPEN_DR10m_pb1_rm0.5_X40_90_SESSION.md  (TOPEN_B2_DR10m_pb1_rm0.5__c3_X40_90, W1)
- DS3_SPEC_TOPEN_DR10m_hl_rm0.5_F60_SESSION.md  (TOPEN_B2_DR10m_hl_rm0.5_F60, NY-AM)
- DS3_SPEC_TOPEN_DR3m_hl_mv20_F60_SESSION.md  (TOPEN_B2_DR3m_hl_mv20_F60, W1)
- DS3_SPEC_TOPEN_DR5m_pb1_rm0.5_X40_90_SESSION.md  (TOPEN_B2_DR5m_pb1_rm0.5__c3_X40_90)
- DS3_SPEC_TOPEN_DR5m_pb3_rm0.5_X40_90_SESSION.md  (TOPEN_B2_DR5m_pb3_rm0.5__c3_X40_90)
- DS3_SPEC_TOPEN_OR30m_stp_ge0.5_F60_SESSION.md  (TOPEN_B2_OR30m_stp_ge0.5_F60)

Exact definitions (state of the code, not interpretation):
- **Drive**: DRDm = direction of `Close(bar D-1 from 09:30) - Open(09:30 bar)` on 1-min bars (D = 3, 5, 10); `move == 0` is no trade; side = sign of the move (trade WITH the drive). Evaluated once at the close of the D-th bar (code/open2/f32_drive.py day_event).
- **rm0.5**: `|move| >= 0.5 x Median5`, Median5 = median of the previous up-to-20 qualifying days' FIVE-minute opening range (high of bars 09:30-09:34 minus low), today excluded, >= 10 values required (shift(1).rolling(20, min_periods=10)). It is the 5-minute range even for D = 10 (f_common.or_median(5, 570)). **mv20**: `|move| >= 20.00` pt absolute. A qualifying day needs a Close on every 1-min bar 09:30-09:59; sample starts 2023-02-10.
- **Entry window**: signal bar open time from 09:30+D through 10:29 (`ie = origin + 60 min`; `sig >= ie` rejected); entry at the signal-bar close (market).
- **pb1**: first 1-min bar after the drive that closes against it (long: Close < Open; short: Close > Open; doji does not count). **pb3**: non-overlapping 3-bar blocks starting right after the drive (09:30+D, +3, ...), signal at the close of the third bar if `Close(3rd) < Open(1st)` (long) / `>` (short), block must end by the 10:29 bar. **hl**: first counter-trend bar B1 (as pb1), then the first later bar with `Low > Low(B1)` (long) / `High < High(B1)` (short) is the signal bar.
- **cK-chunk names**: `__c3_X40_90` = chunk 3 of the bracket grid (f_b3.py: chunks of fixed X{stop}_{target}); `c3` holds stops 40 and 60; `X40_90` = stop 40 pt, target 90 pt, both from the fill, time exit 16:00. `F60` = stop 60, target 60, time exit 16:00. Stop beats target inside one second.
- **OR30m_stp_ge0.5**: OR = high/low of 1-min bars 09:30-09:59; armed if `(OR_H - OR_L) / median(prior 20 days' 30-minute range, min 10) >= 0.5`; stop-entry one tick beyond the range (OR_H + 0.25 long, OR_L - 0.25 short), live 10:00:00 to 10:30:00 (breach scan on 1-second prints), same-second double breach = no trade; F60 bracket. All entries are at or after 10:00.
- **W1 / NY-AM**: the scored cell-session. W1 = entry instant before 09:45:00 (removes 11 of 212 DR10m_pb1 entries and 29 of 166 DR3m_hl entries in PRE); NY-AM = generator window (to 10:29).
- **Lots at $1,000 risk**: stop 40 -> 1.25 NQ exact, stop 60 -> 0.833 NQ exact; replayed lot class = 1 NQ for all six (class rule in sb1_surv.py). MNQ conversion is arithmetic only and was not replayed.
- Replay basis (MEASURED V0): market entry +1 tick, stop-market walking the book, limit target at touch + measured P9 Target correction by year (2023 -1.44, 2024 -1.53, 2025 -4.21, 2026 -4.32 pt), $4.84 RT.

Per-cell evidence (net pts per trade; PRE = selection, X = 2023-04..2024-01 check; HOLD = D3SQ's published look 2, not mine; beats_beta = source random-direction gate, **no for all six**):
| cell (window) | PRE n / mean | X n / mean | HOLD V0 [CI] (MDE) | edge HOLD | PRE rank in pool |
|---|---|---|---|---|---|
| DR10m_pb1_rm0.5 X40_90 (W1) | 201 / +11.22 | 106 / -2.31 | 17.81 [5.30, 30.32] (17.17) | +15.89 | 6 |
| DR10m_hl_rm0.5 F60 (NY-AM) | 185 / +10.92 | 92 / +4.08 | 15.25 [3.18, 27.33] (16.57) | +18.67 | 11 |
| DR3m_hl_mv20 F60 (W1) | 137 / +11.40 | 66 / -3.17 | 12.19 [-0.69, 25.07] (17.68) | +15.06 | 14 |
| DR5m_pb1_rm0.5 X40_90 (W1=NY-AM) | 170 / +16.42 | 91 / +3.79 | 9.42 [-2.86, 21.69] (16.85) | +13.22 | 5 |
| DR5m_pb3_rm0.5 X40_90 (NY-AM) | 170 / +12.30 | 91 / -1.76 | 9.53 [-3.14, 22.19] (17.39) | +10.83 | 9 |
| OR30m_stp_ge0.5 F60 (NY-AM) | 297 / +13.31 | 172 / +1.62 | 5.38 [-5.21, 15.97] (14.54) | +8.37 | 1 |
Three of six are negative in the 2023 span (small positive, +1.6 to +4.1 pt, for the other three); the HOLD CI clears zero only for DR10m_pb1 and DR10m_hl, and DR10m_pb1 (17.81 vs MDE 17.17) is the only one whose HOLD mean exceeds its own MDE. The X column is my own descriptive read of PRE/X rows (no HOLD).

Cells of the frozen book that are not among the six (definitions from code, no separate spec file): **LV_RN_BH_F60 [W1]** = round-number level (multiples of 50 below/above the 09:29 close, raw space), sweep >= 1.0 pt beyond the level, no reclaim (close back on the original side by >= 1 pt within 3 bars), then break-and-hold: first bar k with the last 3 closes all beyond the level and the first of them beyond by >= 2.0 pt; enter at that bar's close in the break direction, 09:30-10:29, F60 bracket (code/open2b2/o3_lib.py level_events, win_min 60, sweep 1.0, brk 2.0, hold 3, reclaim_bars 3); **OR15m_stp_le1_F60** = 15-minute OR (09:30-09:44), armed if OR width <= 1.0 x its 20-day median, stop-entry one tick beyond the range live 09:45:00-10:30:00, F60 bracket (f31_or.py, L = 15, cond le1).

## 3. O6 solve (deliverable 2): selection, all PRE-only
- Pool (N = 30) = the NY-AM cluster representatives of wave q1 that pass the MEASURED gate (out/ssa/cs_scores_q1.csv). Table of all 30 with PRE weekly $ in out/ob/poolA_pre.csv. PRE-selected: **single best = OR30m_stp_ge0.5_F60 (NY-AM)**: PRE +878/wk, SD 1,905, t 3.99, MDE 616. White RC over the 30 on PRE: p = 0.0018 (observed max t 3.99 vs null p95 2.94).
- Greedy PRE-Sharpe forward selection (equal $1,000 risk, x_locks R = $1,000): Sharpe 3.32 (OR30m) -> 4.36 (+ LV_RN_BH_F60) -> 5.04 (+ OR15m_stp_le1_F60) -> stop at 3 cells. **Frozen book = OR30m_stp_ge0.5_F60 + LV_RN_BH_F60 [W1] + OR15m_stp_le1_F60**, 0.833 lots (1 NQ replayed) each, $1,000 risk per trade, 603 PRE trades (290 / 134 / 179), 48 percent of trades and 41 percent of PRE dollars in 09:30-09:59.

## 4. Book vs single best, MEASURED basis (weekly $, equal $1,000 risk per trade; locks R = $1,000)
| series | window | weeks | mean | SD | MDE | CI | Sharpe | maxDD | worst-20 weeks $ |
|---|---|---|---|---|---|---|---|---|---|
| book | PRE | 75 | 1,772 | 2,535 | 820 | [1,189, 2,356] | 5.04 | 6,603 | -25,321 |
| book | X | 44 | **-152** | 2,836 | 1,197 | [-1,015, 710] | -0.39 | 30,267 | -53,196 |
| book | HOLD | 32 | 884 | 2,527 | 1,251 | [-27, 1,795] | 2.52 | 4,101 | -12,891 (20 of 32 weeks) |
| book | H25 / H26 | 27 / 6 | 589 / 2,068 | 2,345 / 2,915 | 1,264 / 3,332 | | 1.81 / 5.12 | | |
| single (OR30m) | PRE | 75 | 878 | 1,905 | 616 | [440, 1,317] | 3.32 | 6,422 | -30,832 |
| single | X | 44 | 105 | 1,778 | 750 | [-435, 646] | 0.43 | 18,030 | -28,794 |
| single | HOLD | 32 | 350 | 1,902 | 941 | [-335, 1,036] | 1.33 | 8,522 | -14,198 |
| book, sides flipped (placebo) | PRE / X / HOLD | | -2,172 / -137 / -1,610 | | | | | | |
**Does the book beat the single best cell? NO.** Sharpe difference (book - single), paired week bootstrap, with MDE: PRE +1.72 (CI [0.08, 3.29], MDE 2.23), HOLD +1.19 (CI [-0.13, 2.48], MDE 1.89), X **-0.82** (CI [-2.64, 0.91], MDE 2.52). The prereg definition needs the book to be higher in ALL of PRE, HOLD and X; it fails in X, and neither PRE nor HOLD difference exceeds its MDE. At equal PRE SD the book has a lower PRE maxDD (6.6k vs 8.5k) and lower worst-20 (-25k vs -41k) but in X the book is worse (maxDD 30.3k vs 24.0k).
Correlation of weekly book $ to the stack (S0 = live D3SL stack, 09:00-09:59 blocked; engine series): PRE 0.29, X 0.21, HOLD 0.08 (H25 0.17, H26 -0.30); vs the dv2a stack_trades live stack: 0.25 / 0.23 / 0.05. Beta placebo: edge = (real - flip)/2 PRE +1,972 (MDE 789), X -8 (MDE 1,164), HOLD +1,247 (MDE 1,192); beta component -200 / -144 / -363 per week (negative, i.e. no bracket-convexity gift).

## 5. Stack-add at 10 / 20 / 30 percent risk (book scaled to r x the S0 PRE weekly SD of $129,181; k = 5.10 / 10.19 / 15.29 times the $1,000-risk book, i.e. 4.2 / 8.5 / 12.7 NQ per cell-trade)
| window (weeks) | r | add $/wk [CI] (MDE) | stack SD -> sum | stack maxDD -> sum | d_sharpe | add in the stack's 20 worst weeks |
|---|---|---|---|---|---|---|
| PRE (75) | 10% | +9,032 [5,886, 12,014] (4,177) | 129.2k -> 133.5k | 390.5k -> 376.8k | +0.41 | +57.6k |
| PRE | 20% | +18,064 [11,771, 24,029] (8,353) | -> 138.8k | -> 363.1k | +0.78 | +115.2k |
| PRE | 30% | +27,096 [17,657, 36,043] (12,530) | -> 145.2k | -> 372.3k | +1.10 | +172.7k |
| X (44) | 10 / 20 / 30% | -777 / -1,553 / -2,330 (MDE 6,101 / 12,202 / 18,303) | 103.8k -> 107.8k / 113.5k / 120.7k | 458.7k -> 468.9k / 479.1k / 489.2k | -0.11 / -0.24 / -0.37 | -48.6k / -97.3k / -145.9k |
| HOLD (32) | 10% | +4,506 [32, 8,895] (6,375) | 145.5k -> 147.2k | 534.6k -> 546.4k | +0.19 | +115.0k |
| HOLD | 20% | +9,012 [65, 17,789] (12,750) | -> 149.9k | -> 558.3k | +0.35 | +230.0k |
| HOLD | 30% | +13,517 [97, 26,684] (19,124) | -> 153.7k | -> 570.1k | +0.49 | +345.0k |
HOLD worst-20 of the stack alone is -593k; with the book at 20% it is -408k (HOLD has only 32 weeks, so 20 weeks is most of the window). Size-dependent stop slippage (DS3_DN_STOPFILL, 0.85 pt at 1 lot rising to 1.44 at 10 lots, linear extrapolation beyond; flagged) lowers the add by about 1-3 percent (PRE 20%: 17,810; HOLD 20%: 8,713; X 20%: -1,881). Not modelled: the 50-contract cap (at 20% the book holds up to about 25 contracts simultaneously on top of the DS3 peak 23 / DS2 27) and the interaction with the live books' locks. Against the dv2a live stack the numbers are nearly identical (out/ob/stackadd_look.csv). Stack-add gate G4 passes in PRE only; X is negative at every scale; HOLD is positive but inside the MDE at every scale (CI lower bound ~0).

## 6. Best-of-N reality check
Multiplicity in this chain: 11,941 T-OPEN B2 cells -> 683 independent clusters -> 63 PRE-selected -> 44 alive after the first HOLD look -> 30 MEASURED-gate NY-AM cluster reps -> 87 evaluated books -> 1 frozen book. At 2.5 percent one-sided per independent cluster, about 17 of the 683 clusters would pass a PRE screen by luck. White RC on PRE with N = 30: observed 3.99 vs null p95 2.94 (p 0.0018): the PRE edge is not an artefact of picking 1 of 30 within PRE. But the PRE sample is the selection sample; the honest out-of-sample numbers are HOLD (t 1.98, below the N=30 hurdle 2.93, the N=87 hurdle 3.24 and the N=683 hurdle 3.79; the pool was already HOLD-gated) and X (negative). MDE beside each null: PRE mean 1,772 (MDE 820); HOLD 884 (MDE 1,251); X -152 (MDE 1,197); edge-vs-flip HOLD +1,247 (MDE 1,192); stack-add HOLD r=0.2 +9,012 (MDE 12,750); book-vs-single Sharpe HOLD +1.19 (MDE 1.89). Every HOLD effect is at or below its MDE: the HOLD look cannot distinguish the book from zero.

## 7. The 09:30-09:59 block question, stack-level (deliverable 3), decided once
Stacks (DS3 stack engine sl_lib/sl_stack as in o2_eng.stacks; rows with label day > 20260206 masked before the engine): S0 = live (09:00-09:59 entries blocked in every live book); S1 = un-blocked 09:30-09:59 only (09:00-09:29 still blocked); S2 = fully unblocked (D3SL published). Identity check: engine S0 differs from the dv2a stack_daily series (PRE sum 3.06M vs 3.31M), so all block numbers use the engine S0/S1/S2 consistently (prereg section 8); dv2a is shown beside it for stack-add and correlation only.
Book at r = 20% (k = 10.19). Weekly mean / SD / maxDD / Sharpe:
| window | S0 (blocked) | S0 + book | S1 (un-blocked) | S1 + book | S2 + book |
|---|---|---|---|---|---|
| PRE (75) | 40.8k / 129.2k / 390k / 2.28 | 58.9k / 138.8k / 363k / 3.06 | 48.6k / 133.0k / 479k / 2.63 | 66.6k / 143.5k / 451k / 3.30 | 65.4k / 148.1k / 599k / 3.2 |
| X (44) | 23.3k / 103.8k / 459k / 1.62 | 21.7k / 113.5k / 479k / 1.4 | 23.0k / 113.7k / 488k / 1.46 | 21.4k / 127.6k / 509k / 1.2 | 19.7k / 128.8k / 550k / 1.1 |
| HOLD (32) | 55.1k / 145.5k / 535k / 2.73 | 64.2k / 149.9k / 558k / 3.1 | 59.4k / 143.8k / 536k / 2.98 | 68.5k / 148.5k / 560k / 3.3 | 66.2k / 154.2k / 576k / 3.1 |
Un-blocking minus blocked, both WITH the book (B - A, paired weekly difference, with MDE): PRE d_mean +7,726/wk (CI [-2,528, 17,346], MDE 13,777), d_sharpe +0.29, **d_maxDD +88.3k (worse)**, d_worst20 -53k (less bad); X d_mean -291 (MDE 20,051), d_sharpe -0.17, d_maxDD +29.5k; HOLD d_mean +4,296 (CI [-11,165, 19,103], MDE 22,416), d_sharpe +0.24, d_maxDD +1.8k. Same B-A at r = 10% and 30% give the same signs (out/ob/block_decision_look.csv).
The book's own increment: blocked +18,064 (PRE), +9,012 (HOLD), -1,553 (X) per week; un-blocked identical in $ (the book is additive), d_sharpe of the book +0.78 / +0.71 (PRE), +0.35 / +0.34 (HOLD), -0.24 / -0.25 (X) blocked / un-blocked, so the book's value does not depend on the block state; its correlation to S1 is a little higher (PRE 0.33 vs 0.29; X 0.38 vs 0.21; HOLD 0.10 vs 0.08).
**Decision rule (prereg): UNBLOCK iff PRE (d_mean>0, d_sharpe>0, d_maxDD<=0) AND HOLD (d_mean>0, d_sharpe>0) AND X (d_mean>0). Result: PRE FAILS (d_maxDD +88k), HOLD passes, X FAILS (d_mean -291). Decision: KEEP-BLOCKED**, one decision for the whole stack, with or without the opening book. Reading beside the rule: un-blocking 09:30-09:59 raises the mean in PRE and HOLD (+7.7k and +4.3k per week) but both gains are inside their MDE (13.8k and 22.4k), it adds about 88k of maxDD in PRE (390k -> 479k without the book), and in X it is flat to slightly negative. The earlier harness finding (+5.8k/wk over WF for un-blocking) is consistent with this and not distinguishable from zero. A secondary fact for the user: 48 percent of the book's PRE trades are entered inside 09:30-09:59 (LV_RN_BH and OR15m_stp), and the book is the only trader of those minutes under the current block; OR30m_stp enters only at or after 10:00 so it is unaffected either way.

## 8. Flags and what was not done
- Replay: wave q1 complete (35/35 months); stop-entry cells replayed as market-at-break (disclosed). The six named specs and the book cells all come from this wave. No memguard-killed month is in the pool; none re-run.
- Lock engine: x_locks closed-trade approximation, R = $1,000, not the 1-s MTM engine (replay fills have no 1-s path here). Book tests: no-lock sensitivity PRE 1,757, X -245, HOLD 790.
- HOLD-contaminated pool (D3SQ gate_M0 used HOLD); my own HOLD+X was one look, logged, never repeated. 32 HOLD weeks, 6 in H26 (H26 statistics, including the Sharpe-difference MDE, are not meaningful).
- Stack used for the block question is the engine D3SL stack (live/live30/unblocked), which is not identical to the dv2a live stack (PRE mean 40.8k vs 44.1k per week); the post-2026-02-06 rows were masked before the engine, but the stack's frozen weights and the DS3 peak-lot constant c are defined on the full published sample (they are scalar settings of the published stack, not P&L I read).
- No NT8 port was run (no identity test performed); spec identity tables list the replay entries to compare.
- Evidence status for the user: the six clusters are SESSION-CANDIDATE singles; none beats the program's bracket-beta gate; the 2023 span is negative for three of them and small positive for the rest; the book's directional edge vs its own flipped placebo is positive in PRE and HOLD but absent in X (-8/wk), which is not enough for a PASS. Best-of-N is not cleared. Verdict stays DEAD for the O6 book; forward register only for the specs.
