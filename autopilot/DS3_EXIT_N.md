# DS3_EXIT_N - integrator page for T-EXIT-N (S5 = E5). Refreshed 2026-11-05 01:17Z. Base = V13T_LIVE (V13Z take lines OFF, lock none = per-book locks; xcost 0.80, stopcost 2.45, targets nominal, resting add cancelled on any exit). POST-HOC, Shadow only.

Shared scorer for all families: autopilot/EXIT_HARNESS.md (code/zones3_s5/exit_harness.py). Rule for 'passes on N': drawdown cut > Z3 V13T_LIVE phase-averaged band (DS3_ZONES_3_NOISE_V13T_FINAL.md) in L6M AND (PRE or X'), no-harm (PRE and MID not worse than -(flip-2 band)), the carrying week dropped keeps the cut (not ONE-WEEK), three placebos (same count per day / same volume / shuffled-day, >= 100 draws, same cost model) rank <= 0.10, mean inside MDE or equal-risk mean not negative.

Context (BASE-4, autopilot/DS3_SIZER_DRAWDOWN_ANATOMY.md): the 2026 and PRE drawdowns sit in the ER >= 0.30 (x1.5) trades (63% / 77% of the gross loss on 37% / 46% of trades); about half of the loss is size excess, half is selection; the worst 30 trades of every episode are P6 x1.5 trades with the split add filled and 27-30 of 30 ended by the TH-L2 cut, so exit rules act on cut trades and the sizer is the larger lever.

## Family status

| family | page | updated | size |
|---|---|---|---|
| E1 LOSS-side cuts (S4a) | DS3_EXIT_N_LOSS.md | 17:28Z | 14k |
| E2 TIGHTEN + scale-out (S4b) | DS3_EXIT_N_TIGHTEN_SCALE.md | 14:07Z | 10k |
| E3 TAKE (Z2) | DS3_EXIT_N_TAKE.md | 14:09Z | 26k |
| E4 RE-TARGET + time/session (ZL-2) | DS3_EXIT_N_FLOW.md | 14:17Z | 4k |

## Plain sentences (copied from the family pages; first 'plain sentence' block of each)

### E1 LOSS-side cuts (S4a) (DS3_EXIT_N_LOSS.md)

## 0. Plain sentences

* The shipped loss cut is a drawdown protector, not a profit tool: removing it makes maxDD worse in every window (L6M -0.31, HOLD -0.31, MID -2.90, PRE -0.70, X' -0.35) while costing only -1728 $/wk of mean (MDE 6929).
* Of 94 alternative cells, 3 lower maxDD AND improve worst-20 in BOTH L6M and PRE on the single path: A arm30 pull50x w10s (cut L6M +0.18, PRE +0.01, X' -0.07, mean -487 $/wk); B flip K2 arm30 (cut L6M +0.04, PRE +0.07, X' -0.10, mean -415 $/wk); B flip SWP arm30 (cut L6M +0.21, PRE +0.09, X' -0.07, mean -450 $/wk). None of them is above the Z3 phase-averaged band in L6M AND (PRE or X') (section 4), so none is a lead.
* TIME-STOPS (no progress at <= 0 after 5/10/20/30 min) are harmful on true fills: mean change -18767 to -13099 $/wk and worse maxDD in nearly every window (they give up trades that come back). The exact U7 blackout (SM only, same side) has zero effect ('never binds'); the all-books both-sides blackout is mixed and costs $/wk.

* FLOW-GATED replacement cuts on the 1-s path (sweep-against and iceberg-ahead, arms 15-40, S4b's flow arrays) are worse than the shipped cut in L6M and HOLD in all 12 cells (best L6M cut -0.14, median -0.32) and cost -14698 to -1078 $/wk: these flags are present on 40,000 of the 88,490 rows, so they are not selective. Delta-turn and large-print-against are S4b's (E2c).

### E2 TIGHTEN + scale-out (S4b) (DS3_EXIT_N_TIGHTEN_SCALE.md)

**On true fills no tighten rule pays.** Of 61 cells (breakeven/+X at pct 0.3/0.5/0.7 gated and ungated, trails 5-15 pts, and the K7 panel line as coded) 0 are eligible and the best mean change in HOLD is -0.20k/wk (all inside MDE, nearly all negative; ungated rules cost -4k to -14k/wk and deepen HOLD/MID maxDD). The K7 line as coded: -0.79k/wk in HOLD, -0.11k in PRE, maxDD HOLD +5%, PRE -3%, MID -21%: neutral on average, no tail cut. Breakeven stops are hit by the ordinary pullback of winners at an extra 2.45-pt stop cost; trails give up the right tail. The P>=0.7 gated BE variants are the least bad (arming is rare) and cut HOLD maxDD +9..+13% with PRE ~0% but X' -30..-45% (harm). No placebo was run (no cell passes eligibility).

### E3 TAKE (Z2) (DS3_EXIT_N_TAKE.md)

## Page 1 - plain sentences
**The five erased THP_POLICY_D7 lines on the true fill basis lose: L6M mean -18.8k/wk (MDE 21.9k), PRE -11.0k/wk, maxDD L6M 150.7 -> 163.8k, PRE 166 -> 223k; no window cut.** The plain-pct take is no better: pct 0.3 -23.1k/wk L6M (PRE maxDD +84% worse), 0.5 -11.3k (L6M maxDD cut +36% but PRE -12%, MID/PRE/X' Calmar -42..-97%), 0.7 -7.5k (L6M cut +21%, ONE-WEEK). Answer to 'does the take pay when the alternative outcome is a stop at 2.45?': no on any window and any book x session pooled; the per-book x session cube shows isolated positive cells (K6 Asia L6M +1.1k/wk, M6 London +0.6..1.2k/wk) swamped by P6 Asia/London and H6 Asia losses (-4k to -8k/wk).
**Flow-gated takes (delta-turn against, large print against, pulled-support ratio, iceberg refill) do not rescue it:** of 28 gated cells none is STRICT or TOLERANT; four are NOW-ONLY with TOL-B (delta-turn <= -100 contracts at pct 0.5 and 0.7, delta <= -60 at pct 0.7, zone take with ahead_rel >= 1.2): L6M mean +0.3..+2.5k/wk (MDE 4-6k, inside), L6M maxDD cut +6..+13%, but PRE mean -0.6..-1.8k/wk and X' -0.4..-1.2k/wk, PRE Calmar -2..-6%; two of the four are ONE-WEEK. Gate firing is not selective: a gate that is true at any second of a 4-h trade fires on 25-60% of trades, so the deltas are close to the ungated take.
**'Take at a line' (zone take):** price reaching the nearest fresh set line ahead with the book thick there (ahead_rel >= 1.2): 3,712 fires, L6M maxDD 150.7 -> 138.7k (-8%), L6M mean +0.9k (inside MDE), ONE-WEEK, PRE mean -1.2k/wk, MID Calmar +27%; ahead_rel >= 1.5 is negative; with no book gate (>= 0) the L6M cut is +22% and MID Calmar +64% but PRE Calmar -19% and X' -29%. No cell passes the two-window test (L6M and PRE).
**THP_POLICY_D7 recommendation from E3: none of the take lines or gates pass on N; publish the empty header.**
Pending: three placebos (>= 100 draws, same cost model) for the four NOW-ONLY(B) cells, equal-risk, phase-average band on V13T, two-episode rule.

### E4 RE-TARGET + time/session (ZL-2) (DS3_EXIT_N_FLOW.md)

**Flow-gated loss cuts (20 cells: adverse A = 20/25/30/35/40 pts AND delta-turn against or a tier-2 large print against, ADD to the base TH-L2 cut or REPLACE it): 0 eligible.** The large-print-against cut ADDED to the base cut is the least harmful (mean change -0.4k to +0.3k/wk, inside MDE; X' maxDD +16..+39% but HOLD ~0% and PRE -5..-10%, MID -6..-26%): it moves the X' episode only. The delta-turn gate fires on 26k-38k rows and costs -2k to -6k/wk; REPLACING the live cut by any of these gates is worse than the live cut. Best score +0.099 (LP A30 ADD).
* **Flow-gated takes (18 cells: pct 0.3/0.5/0.7 AND delta-turn / large print / own-support pulled / iceberg against): 0 eligible**, best HOLD mean change -0.58k/wk (large-print-against at pct 0.7, 8,243 rows), every other cell -3k to -13k/wk. On basis N an early market exit at 0.80 pt gives up more than the flow signal saves, even when gated by order flow.

## Ranked table across families

Rows are added here as soon as a family page publishes a cell with the harness record (cut L6M/PRE/X', MID, PA-band, no-harm, week drop, placebo ranks, equal-risk mean). Until then the ranking is by the family plain sentences above: no exit rule has been reported as passing on N.
