# DS3_ZONES_3 — INTERIM 1 (lead, 2026-11-02 00:45Z; due 01:00Z)

NEW windows only (cap 2026-10-31; last session day 2026-10-30): L1M L2M L3M L6M HOLD MID PRE X' (L1M/L2M view). Everything POST-HOC, Shadow only, no PASS claims. Bases: D7 v1.2 (v1.1 + U7 30-min post-cut blackout) = "v1.2 interim"; D7 v1.3 (v1.2 + gated THP take lines U6(SM)/P6(PE), 10-s L2 grid) = current base. **v1.3 is a best-effort reading: `THP_POLICY_D7.txt` is not on disk; the lead asked the user for it. U7 is an agent-built assumption (30-min same-book entry blackout after a TH-L2 loss cut). K7/H7/M7 = K6/H6/M6 is an assumption.** Detail files: DS3_ZONES_3_S1.md (§1), _S2.md (§2), _S3.md (§3), DS3_ZONES_3_S4A/S4B.md (§4), DS3_ZONES_3_S5.md (§5), DS3_ZONES_3_L2_COMBINED.md (§6/§7 tape+learned), DS3_ZONES_3_S7_BOOK.md (§7 book), DS3_ZONES_3_L2_TAPE_NEWCAP.md (§7 tape). Every agent's 30-min lines are in MORNING.md.

## 0. Load line (00:40Z)
load average 23.7 on 32 cores (~70-75% CPU); memory 162/187 GB used, 16 GB free, ~25 GB available. Memory, not cores, is the binding limit: each engine worker is ~10 GB RSS; agents run 2-3 workers and pause when available < 12 GB. Below the 80% load line, reason = memory. 8 agents running (Z1 just resumed = 9).

## 1. Base lines (D7 v1.3, 12R lock | lock off; mean / maxDD $k/wk, BASE-3)
| window | 12R | lock off |
|---|---|---|
| F9 (Feb-Oct) | 21.4 / 94.1 | 28.1 / 135.6 |
| L1M | 20.9 / 16.1 | 18.6 / 39.2 |
| L3M | 8.2 / 43.6 | 19.4 / 52.6 |
| L6M | 21.3 / 94.1 | 31.2 / 135.6 |
| HOLD | 23.5 / 94.1 | 27.9 / 135.6 |
| MID | 19.7 / 43.1 | 18.8 / 47.8 |
| PRE | 2.9 / 175.1 | 12.6 / 128.4 |
| X' | -3.9 / 234.6 | 0.4 / 142.9 |
v1.2 for comparison (12R): L6M 26.0/127.8, PRE 13.2/113.8, MID 11.3/92.1. **The Feb-Oct maxDD is ONE episode (weeks around 2026-09-14 = 2026-W38).** Any cut that rests on F9/L6M/HOLD alone is a one-week result; PRE, X' and MID are the independent episodes.

## 2. §1 — which lines carry the drawdown cut (Z1; premise = zone layer off vs the shipped HALF layer)
| base | L3M | L6M / HOLD | MID | PRE | X' |
|---|---|---|---|---|---|
| v1.2 HALF | 70 > 40k (+43%) | 157 > 128k (+19%) | 58 > 92k (worse) | 198 > 114k (+43%) | 270 > 277k (flat) |
| v1.2 SKIP frame | | +27% | | +56% | +10% |
| v1.3 HALF | -4% (L2M -6%) | 114 > 94k (+18%) | +22% | +33% | +22% |
- Chance: on v1.1 the layer beats the random-level and same-volume placebos only in PRE (ranks 0.050 / 0.040); in L6M/HOLD the ranks are ~0.57 / 0.70 (a random half-lot layer of the same size cuts about as much). v1.3 placebos are still running.
- Episode-proofing: dropping any one episode keeps the PRE cut positive (+11% to +46%) on v1.1 and v1.2.
- **No single line carries the layer; no line is RISK-KEEP.** Contribution leaders: CRT4h, OTE-705, OTE-62 (half line), OTE-62 B73, kijun1h; their cuts sit in X' and PRE, not L6M. The three profile lines (VAH15s sw15, LVN1 sw1h, HVN0 sw1h) add nothing measurable (also ZL-2: no usable Feb-Oct cut). Placebo ranks are partial (100+100 only for kijun1h, PDmid, CRT4h, KCup4h, camH3; OTE705 ~95/50; the three profile lines and OTE62b73 none yet).
- Profile-line exact definitions are published in DS3_ZONES_3_S1.md ("PROFILE LINES: EXACT DEFINITIONS"): all three need the 1-s tape (1-min rebuild Jaccard 0.73 / 0.45 / 0.76).

## 3. §2 — D / freshness (Z2, 43-draw 3-kind placebos)
No pick beats random: CRT4h 60 pts fresh solo L6M-cut placebo ranks 0.34 / 0.16 / 0.45; camH3 0.18-0.23; composite C_post 0.23-0.34; the "honest" composite 0.86-0.91 (worse than random). All LEAD-weak: **keep shipped D20 fresh** unless the per-session or null runs change it (null with 8 seeds running).

## 4. §3 — action per line (Z3, N-basis, 101 cells on v1.2; v1.3 finalist placebos 5 of 20 draws)
Shipped action is HALF. Ranked vs shipped HALF (no placebo yet on the first row): ALL 7 lines HALF->SKIP cuts maxDD L1M +50 / L3M +24 / L6M +11 / HOLD +11 / MID +28 / PRE +24 / X' +13%, but L3M/L6M only is not HOLD-robust (HOLD ONE-WEEK); OTE705 skip tiny TOLERANT. Honest picks keep HALF / B73. Purged walk-forward (monthly refit vs fixed layer vs none) is Z3's, grid supplied by Z2 (candidate_grid_for_Z3.csv): not run yet.

## 5. §4 — other 183 streams (S4a even / S4b odd; 663-stream split)
S4a: the v1.1 screen leads do NOT carry to v1.3 (32 shortlisted cells re-run with U7: EQL_tight 5m D40 skip L6M cut 0.04 vs 0.46 on v1.1; FIB ote705_dn 15m D40 skip L6M .39 HOLD .33 MID .37 PRE .49 but X' -.22; ARR iFVG 15s half = ONE-WEEK). Because cuts flip with the base the whole grid is being re-screened on v1.3 (1,272 masks, ~00:55Z). S4b: 319 of 331 streams usable; 1,258 D7 runs (D20/D40 x skip/half) in progress (~2 h). Top-20 across ahead/behind/at due 03:00Z.

## 6. §5 — density (S5)
Ranked (unchanged since 00:05, placebo ranks pending): sA40>=1 skip, nA60>=1 skip, nB40>=2 half; nA40>=1 ONE-WEEK. Tape-zone density (ZL-3): best TAPEALL >=5 zones within 20 pts halved +17/+17/+16/+15% (L6M/HOLD/PRE/X'), mean +3.9k/wk inside MDE 10.8k, placebo rank 0.04, **L6M cut 17.5% < the 20% bar: LEAD at most**; the one density candidate to re-test (engine placebos queued).

## 7. §6 — learned rule (ZL-3, price + tape)
Walk-forward (13-week and expanding re-fit): AUC 0.60-0.63 price-only / price+tape / tape-only vs 0.60-0.64 shuffled-feature placebo. **The signal is the book x session prior, not the zones**; the 6-leaf tree splits only on book and session; no per-line D7 table results from it. Arm B (price + book + tape) is queued now that ZL-1's streams exist.

## 8. §7 — order-book and tape zones (ZL-1, ZL-2, ZL-3)
- Tape (126 streams, 268+152 cells): **no tape zone is a drawdown lead.** 14 of 268 cells have same-count random-skip rank <= 0.05 vs ~13 expected by chance; TAPEALL D20's +47/+39/+24/+65% is VOLUME (skips 35k of 88k rows, rank 0.33); ONE-WEEK on the Sept episode for every cut >= 20% (7 of 8 finalists fall below a third without it; month-block bootstrap CI includes 0 for all 8). Weak leads only: TPF hvn1 sw1h D20 (+12/+12/+3/+8%, rank 0.035), TLQ SES asia D20 (rank 0.025), TCD divbull D20 (0.025). Liquidity-pool (TLQ) levels are worse than random; the break-window pool "predicts" +6..8 pts mechanically. v1.3 shrinks the tape cuts (TVP developing-LVN D40 half -31% -> -5%, FRAGILE).
- Book (96 streams to 20261030; 56 AHEAD cells on v1.3): **the order book adds ~nothing.** 53 of 56 cells cut L6M/HOLD maxDD < 10%. One lead-like cell, PUL k3 4h D20 skip: L6M 94.1 > 60.2k (+36%), HOLD +35%, L3M +32% (falls to 18% without W38), PRE -3%, MID -4%, X' +6%; beats 3 placebos (20 draws) in L6M/HOLD only; fails D40 (L6M 11%, MID -50%); carried by one month (2026-09 +158k, the other 27 months net -2k) and by the Asia books (P6 +72k, H6 +32k): **ONE-WEEK / FRAGILE, not RISK-KEEP.** Sweep extremes and defended walls are worse than random levels (ranks 0.99-1.0). Iceberg/defended-wall event counts fell ~10x from 2023-24 to 2026 (80/month in 2026-10).
- "L2 zone confirms a price line" (ZL-1 18 cells, ZL-3 174 cells): L2 evidence does not separate good set-line rows from bad. Skipping confirmed rows ~0; undoing the HALF on lines with no L2 evidence deepens L6M maxDD 12-40% (ZL-1) / in every family (ZL-3). The shipped HALF works and the book/tape cannot tell weak lines from good ones.

## 9. Plain sentence (interim, NOT the 06:00Z one)
On the new windows the shipped zone layer lowers maxDD in PRE and (on v1.2) L3M/L6M, but in Feb-Oct it is one September episode and a same-size random half-lot layer cuts about as much; no single line carries it; the uncoded profile lines, the 183 other streams so far, the tape zones and the order-book zones add nothing that survives dropping that week or the same-volume placebo; the learned rule is the book x session prior. **The robust candidates so far: none beyond the shipped layer; leads to re-test: TAPEALL density-half (L6M 17.5%), CRT4h/OTE lines in PRE/X'.** The monthly-refit vs fixed-layer walk-forward verdict is not in yet.

## 10. Not done at this checkpoint (all queued, agents running)
v1.3 placebos at >= 100 draws for the line table; 2^10 subset landscape on v1.3; walk-forward chain (Z3); §4 top-20 with BEHIND/AT frames and robustness; §5 placebo ranks; ZL-3 book half + engine placebos; 1-s/3-s delay cells; per book x session x vol tercile tables; DEAD_CELLS append for S1/S2/S3/S4/S5 cells; zones_policy.txt (06:00Z).
