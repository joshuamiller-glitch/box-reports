# DS3_BARS_2 - bars, second pass (plan36 section 5; agent B2; 2026-10-30/31)

Code `l2vast/ds3/code/bars2/` (tb_lib, grid, phase, shuf, an_tb, an_plc, stack_lib, te6g, an_te6*, plus wave2_*/be_lib reused). Outputs `l2vast/ds3/out/bars2/`. Preregs `PREREG_TB4W2.md` sha256 `4e3ab7e237c82ea5908493611b73a4fe76066c763c4b81eeb685c329a82cce90` and `PREREG_TE6G.md` sha256 `902fcfb59eb566480bec28cc2c229ce185d2b606c2927213ff4c854e2e11f7eb`, both logged in DECISIONS.md before any new statistic. Masks own, capped 20260206, UNTOUCHED never read. Measured M basis (N, P9 beside), per contract; 60/60 unless stated.

## Page 1: results

1. **TB4W (pullback, 10-min time bars, Asia) is NOT confirmed. Tier: LEAD-weak, not promoted. It fails G4, G5 (HOLD), G7 and G8.** It is post-hoc-selected (found after the wave-2 HOLD look). There is a real-looking effect that does not depend on the 10-min grid phase: the same rule on 200 shifted 10-min grids averages **PRE +5.8 / HOLD +6.1 [-1.0, +13.2] / L6M +6.9 [+0.1, +13.8] / L3M +1.4 pts per contract (Asia)**, against the 1-min version PRE -1.1 / HOLD +1.1. The honest forward estimate is therefore about +5 to +6 pts per contract with a CI that includes 0 in HOLD; not the +9.5 PRE of the registered grid (that grid ranked 2 of 201 in PRE, i.e. about 3.7 pts of it is selection luck).
2. **The wave-2 headline "HOLD paired +13.4, CI excludes 0" is an artefact of conditioning on days on which both the 10-min cell and the 1-min control traded.** The unconditional trade-weighted difference (cell minus 1-min, no conditioning, day-clustered SE) is **PRE +10.6 (SE 3.2) / X' +5.2 (5.3) / HOLD +3.3 (4.8) / L6M +3.1 (5.3) / L3M +5.2 (7.2)**. By the letter of the prereg G3 (per-day paired on common days, HOLD +12.0, SE 5.8) passes; on the unconditional measure it does not. Both are reported; the unconditional one is the right comparison (the book runs either cell, not the intersection).
3. **Genericity of the 5-min-bar note for the live KB / PE / SM engines in NY-AM: null.** On 5-min bars, with bar-count or minute-converted parameters, no engine beats its 1-min version in PRE or X'. The apparent HOLD/L6M/L3M "wins" are the 1-min control being negative in those windows (KB control -3.2 HOLD, PE -3.6); the cells themselves are about 0 (phase-averaged M: KB -0.0, PE +1.6/-0.2, SM +2.1/+1.0 in HOLD, all CIs include 0). No stack case (section 5).
4. Nothing here is PASS. Cumulative-multiplicity RC fails (family RC p on PRE+X' paired 0.021 over the 250 live cells, studentised 0.082, Romano-Wolf survivors 0; HOLD RC p 0.35, survivors 0; cumulative trial count about 2.46 million cells incl. the 50,000 start).

## 1. TB4W-2

### 1.1 The registered set (300 cells, honest count)
6 signal variants x 5 sessions x 10 brackets. Variants: X bar 5 min (regime ST10 fixed) `b5_fix`; 5 min regime matched `b5_mat`; 10 min `b10`; 15 min fixed `b15_fix`; 15 min matched `b15_mat`; 1-min control `ctl1m` (store tc/1m; the live library aux 1-min is the second control, within 0.3 of it). Brackets 45/45 60/60 75/75 90/90 45/60 60/45 45/90 90/45 60/90 90/60. Primary = b10, Asia, 60/60 (1 of 300). Signal = wave-2 TB4W exactly (ST ATR10 x 3.0 on 10-min aggregates, EMA20 of 1-min closes, T1, 600 s arming, market entry at X-bar close, flat 16:55). A reproduction of the registered cell matched the wave-2 numbers exactly (PRE +9.5 n 328, HOLD +4.4 n 154).

### 1.2 Per-contract M by window, Asia, 60/60 (n in brackets); N and P9 beside
| cell | X' | PRE | HOLD | L6M | L3M | N: PRE / HOLD | P9: PRE / HOLD |
|---|---|---|---|---|---|---|---|
| 10 min (primary) | +2.7 (165) | +9.5 (328) | +4.4 (154) | +5.3 (129) | +1.9 (75) | +11.0 / +6.7 | +8.9 / +3.8 |
| 15 min fixed | +2.5 (98) | +10.5 (200) | +4.2 (107) | +7.2 (87) | +0.9 (47) | +12.0 / +6.6 | +9.9 / +3.6 |
| 15 min matched | +19.9 (39) | +3.1 (125) | +5.7 (75) | +8.1 (64) | +6.5 (31) | small n | |
| 5 min fixed | -1.7 (233) | +2.8 (706) | +3.4 (331) | +5.5 (296) | +5.1 (166) | +4.3 / +5.7 | +2.1 / +2.8 |
| 5 min matched | -8.1 (239) | +2.8 (770) | +0.4 (347) | +2.3 (311) | +1.9 (178) | | |
| 1-min control | -2.5 (247) | -1.1 (794) | +1.1 (360) | +2.3 (326) | -3.3 (192) | +0.3 / +3.4 | -1.8 / +0.5 |
Scale ladder PRE: 1 min -1.1, 5 min +2.8, 10 min +9.5, 15 min +10.5. N basis is above M in HOLD (target-fill correction 4.2 pts in 2025), so the result does not rest on the correction artefact.

### 1.3 Honest evidence for a post-hoc-selected cell
* **Splits (10-min primary):** X' +2.7 [-6.0, +11.5] (n 165), PRE +9.5 [+3.1, +16.0] (328), HOLD +4.4 [-5.6, +13.5] (154), L3M +1.9 [-12.6, +16.8] (75) (day-block bootstrap; week-block CI within 0.6). MDE (2.8 x day-clustered SE): X' 12.8, PRE 9.1, HOLD 13.8, L6M 15.2. Only PRE is above zero by its CI; the later windows are below MDE.
* **Selection luck:** the real (phase-0) grid is rank 2/201 in PRE among shifted grids (draw mean +5.75, p5..p95 +2.5..+8.1) but rank 139/201 in HOLD (draw mean +6.1). 15 min: PRE rank 36/201, HOLD 127/201. 5 min: PRE 24/201, HOLD 59/201. The grid alignment is not special; the bar size is (the 5-min draws average PRE +1.7 / HOLD +2.5; 10-min +5.8 / +6.1; 15-min +8.3 / +5.4).
* **Phase-averaged (selection-free) vs the 1-min control, unconditional:** 10 min PRE +6.9 [+2.2, +11.1], HOLD +4.9 [-2.0, +12.1], L6M +4.6 [-2.6, +11.7]; 15 min PRE +9.4 [+2.3, +16.2], HOLD +4.2 [-5.3, +14.1]; 5 min PRE +2.8 [+0.7, +5.0], HOLD +1.3 [-2.1, +4.7].
* **Anchored walk-forward chain** (monthly refit from 2024-04 over the 60 Asia cells, trades closed before the refit, n >= 30): OOS PRE +11.2 (117), **HOLD -2.4 (74)**, L6M +3.4 (63), L3M -4.3 (31); the chain locks onto `b15_mat|asia|75/75` (22 of 23 months), a small-sample X' cell (n 39, +19.9) - last re-fit `b15_mat|asia|45/60`. Rolling-12 chain: HOLD +0.6, L3M +2.1. The 1-min control chain: PRE -0.3, HOLD +2.2. The fixed rule (10 min, 60/60) over the same OOS months: PRE +9.8, HOLD +4.4. Over all 300 cells the anchored chain is identical (it picks Asia); the rolling-12 chain over all sessions is negative (HOLD -14.6). So re-selecting among the grid does worse than the plain registered rule, because the grid has no stable winner; G7 fails.
* **Shuffled-day placebo (200 draws per variant, fire times and sides on other days of the same block; draw means about -2.2):** 10 min PRE rank 1/201, X' 27/201, HOLD 19/201 (0.91 percentile, below the 0.95 gate), L6M 16/201; 15 min fixed PRE 2/201, HOLD 29/201; 5 min fixed PRE 1/201, HOLD 6/201. The pullback timing carries information in PRE; in HOLD it is suggestive, short of the gate.
* **Neighbourhood (mean of the 8 neighbours of 60/60 on {45,60,90}^2, 10 min Asia):** X' +5.6, PRE +4.8, HOLD +3.2, L6M +4.3, L3M +0.9 (G9 passes); 10/10 brackets positive in PRE and L6M, 9/10 in HOLD, 8/10 in L3M. Bar-size neighbours: 15 min +, 5 min weaker (above).
* **Latency (decision + 0 / 1 / 3 s), 10 min Asia M:** PRE +9.5 / +9.5 / +9.4, HOLD +4.4 / +3.6 / +5.1, L3M +1.9 / +1.9 / +3.4: no sensitivity.
* **Stability:** quarters positive 8 of 12 (negative: 2023Q2 -12.5 n 35, 2024Q4 -1.9, 2025Q3 -1.7, 2026Q1 -2.9 n 34); the last quarter and L3M are flat to negative. Weekly P&L Newey-West t 3.4, ACF about 0; longest losing run 5 weeks. Top 5% of trades carry 0.57 of the gain (L6M, k 7 trades make half of it). Vol-tercile (PRE-fixed cuts): the high-vol third carries it (PRE +16.8 n 136, HOLD +8.0 n 59; low third +6.2 PRE, +2.5 HOLD). Long/short both positive in PRE (+10.5 / +8.2) and HOLD (+3.9 / +5.0).
* **DSR** (weekly P&L, HOLD, 300 trials): 0.02 (about 0 at the cumulative count); over all weeks 0.44 at 300 trials. **PBO** (CSCV over the 50 Asia cells) 0.35; over all 250 cells 0.18. Capacity (needs the mbp-10 join at the fill seconds): NOT computed, so promote_ok = False.
* **Sessions:** other sessions are not part of the claim: phase-averaged 10-min PRE/HOLD: London -3.4/+5.4, pre-open -8.9/-5.2, NY-AM +1.7/+2.4, NY-PM 0.0/-3.7.

### 1.4 Gates (not softened)
G1 PRE paired t >= 2: pass (unconditional +10.6, t 3.3). G2 X' > 0 and X' paired > 0: pass (+2.7; +5.2 unconditional; both well inside noise). G3 HOLD paired CI excludes 0: pass on the registered per-day common-day paired (+12.0, SE 5.8), FAIL unconditional (+3.3, SE 4.8). G4 phase-averaged HOLD > 0 with CI excluding 0: FAIL ([-1.0, +13.2]). G5 shuffled-day rank >= 0.95 in PRE and HOLD: PRE pass, HOLD FAIL (19/201). G6 N >= 0 PRE and HOLD: pass. G7 walk-forward chain > 0 and > 1-min chain: FAIL (HOLD -2.4 vs +2.2). G8 cumulative RC/independent forward: FAIL. G9 neighbourhood > 0: pass. Tier: fails more than G8 alone -> not CANDIDATE-RECENT; LEAD-weak (positive, phase-independent, bar-size-dependent, unproven in HOLD).

### 1.5 Units, $ and the stack
Trades per week 4.4 (4.8 in L6M). One TB4W book at 10 lots (PB/ST/HM lots; the D6 lot for a new book is not set - stated assumption), 60-pt stop. $ per week at 10 lots: L6M +5.0k, HOLD +4.3k, PRE +8.5k, X' +1.8k, L3M +2.1k (at 5.6 lots: +2.8k / +2.4k / +4.8k / +1.0k / +1.2k).
Stack = the six engine books (daily_main BASE, lock engine, live lots, no 70/30 split) vs plus the TB4W book through the same lock engine (BASE spec, PB proxy):
| $/wk | L3M | L6M | HOLD | PRE | X' |
|---|---|---|---|---|---|
| stack | -26.5k | +18.8k | +8.6k | +27.7k | +5.2k |
| stack + TB4W 10-min | -24.4k | +23.8k | +12.8k | +36.2k | +6.9k |
| stack + 15-min | -25.9k | +23.3k | +11.4k | +33.3k | +6.0k |
| stack + 1-min control | -31.4k | +26.1k | +12.6k | +24.2k | +2.7k |
Weekly correlation of the TB4W book with the stack: 0.36 (all 149 weeks), 0.39 HOLD, 0.40 PRE. Marginal Sharpe of adding it (weekly, annualised): +0.21 all, +0.15 HOLD; weekly SD of the stack rises 131k -> 142k; marginal worst-20-weeks -196k (all weeks) and -48k (HOLD): it adds mean and adds tail. Note that the 1-min control adds +4.0k HOLD and +7.3k L6M to the stack through the lock engine too, so on the stack the 10-min cell is not distinguishable from the 1-min in HOLD (+4.3k vs +4.0k) and is better in PRE (+8.5k vs -3.5k).

### 1.6 NT8 spec (SHADOW ONLY, proposed D6 tag TB4W; not promoted; carries 'post-hoc-selected')
Bar type: 10-minute time bars (epoch-aligned; any alignment does as well per the phase test), session Asia (entries 18:00-02:00 ET), plus a 1-minute series. Regime: Supertrend(ATR period 10, multiplier 3.0) computed on 10-minute bars, read only after the 10-minute bar closed. Level: EMA(20) of 1-minute closes at the last completed minute. Touch: bar low <= level (long, regime +1) or bar high >= level (short, regime -1); armed 600 s after the most recent touch; fire when the 10-minute bar closes in the trend direction (close > open for long) AND beyond the level; one fire per touch episode; one position. Market entry at the bar close; bracket 60 pt stop / 60 pt target from the fill (45-90 all positive, 60/60 kept); flat 16:55 ET. Lots: 10 for the numbers above (assumption). Weakest points: only PRE is significant; the L3M is flat; an NT8 identity test and a forward window are required before ON.

## 2. TE6 genericity: live KB / PE / SM on 5-minute bars, NY-AM
Cells: 3 engines x A (bar-count: KB EMA14/ATR10, SM ST(7,3), PE EMA20/ST(10,3)) or B (minute-converted: KB EMA8/ATR6, SM ST(14,3), PE EMA4/ST(10,3)) x 5 sessions = 30, primary 6 (NY-AM). Controls = the live 1-min engines (aux, native grouping). 60/60.
NY-AM M per contract (n in L6M ~ 260-400 for KB/PE, ~115-135 SM):
| cell | X' | PRE | HOLD | L6M | L3M | unconditional d vs 1-min X'/PRE/HOLD/L6M/L3M (SE HOLD) |
|---|---|---|---|---|---|---|
| KB A | -1.7 | +0.4 | -0.1 | +0.6 | -1.3 | -2.3 / -3.0 / +3.2 / +4.0 / +7.5 (2.8) |
| KB B | -0.7 | +1.1 | +0.2 | -0.1 | +4.8 | -1.3 / -2.3 / +3.4 / +3.4 / +13.6 (3.2) |
| PE A | -2.8 | 0.0 | -1.5 | -1.6 | +1.3 | -8.0 / -0.1 / +2.1 / +3.5 / +6.8 (3.6) |
| PE B | +0.3 | +0.6 | -1.6 | -1.4 | -0.2 | -4.9 / +0.6 / +2.0 / +3.6 / +5.3 (2.5) |
| SM A | +8.6 | +4.4 | +2.0 | +2.2 | +0.0 | +6.6 / +2.3 / -3.8 / -0.4 / -6.6 (7.6) |
| SM B | +1.6 | +0.7 | -0.2 | +0.9 | +0.7 | -0.4 / -1.4 / -6.1 / -1.7 / -6.0 (7.5) |
1-min controls NY-AM: KB +0.6 / +3.4 / -3.2 / -3.4 / -8.8; PE +5.2 / +0.1 / -3.6 / -5.0 / -5.5; SM +2.0 / +2.1 / +5.8 / +2.6 / +6.7. The paired same-day (both traded) numbers are larger (SM +9..+17, KB/PE mixed) and carry the conditioning bias described in 1 above.
Phase placebo (200 distinct random grid phases in [1,300) s, NY-AM): phase-averaged M HOLD: KB A -0.0, KB B -0.3, PE A +1.6, PE B -0.2, SM A +2.1, SM B +1.0; PRE: +0.7, +1.1, +0.4, +0.9, +1.8, +1.2. Real grid rank among draws is unremarkable (HOLD 86-165/201) except SM A in X' (1/201: +8.6 against a draw mean +0.6) and PE A L6M/L3M (rank 180, 187: the other phases do better). The phase-averaged difference to the 1-min engine is -3.0/-2.7 (KB A X'/PRE), -7.6 (PE A X') and about 0 for SM in PRE; in L3M KB and PE draws beat the (negative) control by +10 to +12, which is the control collapsing, not 5-min bars earning (the cells' own L3M M is -1.3..+4.8, phase mean 1-7).
Reading: for the live engines there is no PRE or X' gain from 5-min bars, no phase-independent positive level, and nothing above MDE (MDE ~ 7-9 pts per contract for KB/PE in HOLD, ~ 20 for SM). The earlier SM-type lead (TE6, Supertrend on 5-min) does not generalise to KB or PE and, for SM A, is concentrated in the 2023-24 grid alignment (X' rank 1/201). Result: null; do not change KB/PE/SM bar size.
Units and stack (lock engine, live lots KB 5.2 / PE 5.6 / SM 7.4; $/wk delta of replacing the NY-AM rows of the book): KB A +12.6k L3M / +7.7k L6M / +6.4k HOLD / -1.6k PRE / -0.6k X'; KB B +11.8k / +5.5k / +4.8k / -1.1k / -2.6k; PE A -0.2k / -0.6k / -1.4k / -2.4k / -0.9k; PE B +4.8k / +3.9k / +3.1k / -2.8k / +0.6k; SM A -4.3k / +1.3k / -0.5k / +0.8k / +3.4k; SM B -5.0k / +0.5k / -1.9k / -0.3k / +0.8k. The sign flips between PRE and the recent windows for every cell: this tracks the 1-min control's own regime (negative in 2025-26), not a bar effect. Weekly correlation with the six-book stack -0.18..+0.14. (File te6g/stack.json.)

## 3. Not done / caveats
Capacity (mbp-10 depth at the fills), purged k-fold/CPCV for the grid (the anchored and rolling walk-forward chains are done), the 3/6 month walk-forward windows (12-month rolling done), lock-engine lot assumptions for a new book, and the NT8 identity test. The pairing statistic of wave 2 (per-day mean on common days) overstates gains for sparse cells; other wave-2 CANDIDATE-RECENT rows that used it should be re-read on the unconditional difference (the trade-weighted `dtw_*` columns in REPS_TIERED already show this: TB4W 15m dtw_HOLD +3.4).
Files: out/bars2/{grid_trades.parquet, grid_cells.csv, an_tb.json, an_plc.json, phase/, shuf_daily.parquet, family_daily_M.npy, wf_picks_*.csv, te6g/{real_trades, te6g_cells.csv, an_te6_phase.json, stack.json}}; DEAD_CELLS (+390 rows, programs B2TB4W2/B2TE6G), UF_TRIALS side plan36_bars2 (300 + 30 cells), RECENT_WINS out/recent_wins/bars2.csv (L3M-positive cells, view only).
