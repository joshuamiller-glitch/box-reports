# DS3_D7_SPLIT_V13Y - is D7's 70/30 ENTRY SPLIT (L2SE: market F now + a dip add) worth keeping on the fixed base? (ZL-3, V13Y, 2026-11-02)
Research only, post-hoc, Shadow only, no PASS claim. Base = D7 V13Y (BASE-4's fixed base, add-fill ordering fixed). Frames: lock=None (headline) and 12R. Code l2vast/ds3/code/zl3 (zl3lib.run_split, split_grid.py); results /mnt/l2/l2vast/ds3_zones3_new/ZL-3/split_v13y*.pkl. Tie-out: re-simulating the shipped split with the shipped parameters through my hook reproduces the V13Y base to $0.0 on every day (lock=None), after excluding PB (A7 trades at market, no split).

## 1. What the shipped split is (from the kernel lj_kernel.jtrade, cell 'F5|F=0.7|X=3|N=1|chase=none|veto=v4')
* F = fraction entered at the signal second at market: KB 0.5, MV 0.5, SM 0.75, HM 0.5 in NY-AM / 0.75 elsewhere, PE 0.7 (per-book table), PB no split.
* Dip add: the first second where price has gone X = 3 pts adverse (close-to-E) AND the L2 book gate passes (bit 51 'gate_ok', veto bit v4 = no add) triggers a passive limit at the book offset (or market after T seconds): fill lots a = (1-F) x stop / (fill - stop) (risk-equal, > 1-F), and the target is re-based to (average fill + td); stop unchanged. If no dip: the position stays at F lots for the whole trade (the missing lots are never bought).
* What the add does if the original leg exits first: the kernel scans for the dip before the original exit is known; I probed every filled add for 'original (stop/target from E) exit second < add fill second' (the bug class found in B73): **0 rows** (ncancel = 0 in all cells; cancel-on/off give identical results), so the split does NOT have the B73 ordering defect.

## 2. Grid (uniform F and dip X for all five split books, everything else shipped; exact fill rules above; the TH-L2 cut/take lines then apply as in V13Y). maxDD cut vs the shipped base (negative = deeper maxDD), L3M / L6M / HOLD / MID / PRE / X' (%); mean change L6M ($/wk, MDE)
| F, X | lock=None cut | d mean L6M (MDE) | lock=12R cut | d mean L6M (MDE) |
|---|---|---|---|---|
| shipped (per-book F, X 3) | 0 | 0 | 0 | 0 |
| **F 1.0 (market entry, no split)** | -43 / -32 / -23 / -28 / +4 / -17 | -3,068 (9,177) | -56 / -61 / -24 / -18 / +6 / -6 | -7,570 (12,923) |
| F 0.5, X 3 | -10 / -17 / -16 / -26 / -5 / -9 | -1,342 (3,442) | -18 / -11 / +6 / +33 / -3 / -33 | -1,219 (1,434) |
| F 0.7, X 3 (uniform) | +4 / -13 / -5 / -2 / -2 / +2 | -133 (2,144) | -56 / -4 / +1 / +7 / +32 / 0 | -499 (2,678) |
| F 0.9, X 3 | -54 / -42 / -33 / -29 / +1 / -24 | -4,322 (9,161) | -63 / -70 / -10 / -17 / +1 / -8 | -8,012 (12,942) |
| F 0.7, X 1 | -35 / -49 / -40 / -34 / -8 / -21 | -5,811 (8,995) | -28 / -77 / -15 / -21 / -14 / -27 | -8,978 (12,539) |
| F 0.7, X 2 | -47 / -41 / -32 / -4 / -1 / -7 | -4,657 (8,727) | -28 / -49 / -12 / +9 / +3 / -37 | -6,979 (12,130) |
| F 0.7, X 5 | -3 / -8 / -5 / -6 / -21 / -3 | -3,260 (3,447) | -23 / -2 / -3 / +20 / +29 / +2 | -2,080 (3,310) |
| F 0.5, X 1 / 2 / 5 | -53,-16,-36 L3M; L6M -60,-61,-7 | -4.3k, -3.2k, -3.7k | L6M -36,-63,-3 | -2.3k, -2.9k, -1.8k |
(Full grid, 4 F x 4 X, in the pickle; X applies only where a dip add exists.)
**Reading.** No alternative beats the shipped split on drawdown or mean in either frame. Market entry (no split) is worse on L3M / L6M / HOLD / MID (cuts -43 / -32 / -23 / -28% lock=None; -56 / -61 / -24 / -18% lock=12R), slightly better only on PRE (+4 / +6%); means -3.1k / -7.6k per week on L6M, inside the MDE but negative; L3M mean +12 / -252 $ per week: **the ledger's L3M sign change of the split piece (-5.4k vs +10.0k) is not reproduced on V13Y at the D7-book level: the split is neutral on L3M mean and clearly positive on L3M drawdown.** (The earlier '+6% / +1.4k' for market entry came from the defect base V13X.)
**Fragility of the optimum.** X = 3 is a sharp optimum: X = 1, 2 and 5 are -30..-77% on L6M and lose 2-9k per week, F = 0.9 is -42..-70%: the shipped point (X 3, per-book F) was chosen on old data and sits on a ridge (the dip is tied to the L2 gate bits, which fire at 3 pts). Not a reason to change it; a reason to expect the split's edge to be partly in-sample.

## 3. Equal-risk and placebos
* Equal-risk (lot table scaled until the worst-20 sum of ALL equals the base's): market entry lock=None lscale 1.00 (already at equal risk) -> L6M cut -32%, mean 25.7k vs 28.8k; lock=12R lscale 0.93 -> L6M cut -41%, mean 13.0k vs 21.2k per week (-8.3k, MDE 12.1k). Market entry loses at equal risk.
* Random-row placebo: a random 25 / 50 / 75% of the standard rows keep the shipped split, the rest enter at market (3 seeds each): lock=None L6M cut -36,-25,-27 / -27,-11,-27 / -5,+5,+9; lock=12R -67,-46,-53 / -15,-32,-77 / -5,+8,0: the more rows keep the split the closer to the base; no random subset reaches the shipped result. Shuffled dip (X drawn at random per row from 1,2,3,5; 3 seeds): L6M cut -2,-8,-6 (lock=None), +0,-6,0 (12R), mean -0.7k..-2.0k: the specific X = 3 is worth +2..+8 points of L6M cut over a random X (a small, real effect against a random dip).
* Phase-averaging (entry-second phase): not done; the dip rule is conditional on price excursions, not on a time grid, so there is no entry-clock phase to average.

## 4. Per book x session (market entry vs shipped, L6M; lock=None / 12R)
P7 (PE) Asia: cut -40 / -79% (mean -4.1k/wk), P7 London: -64 / -103% (-0.8k / -3.1k): the split protects the PE book most. K7 NY-PM: +43 / +55% (market entry is better there, +0.9k/wk, base maxDD 49k / 37k), K7 Asia -13 / +7%, U7 London +7 / -14%, M7 London +7 / +12%, H7 Asia +1 / -15%, A7 (no split) 0. So the split's value sits in the PE book (and Asia); in K7's NY-PM sessions market entry would be better on both drawdown and mean (a candidate per-session exception for the owners, not a proven one: one base episode).

## 5. Verdict
**Keep the 70/30 L2SE entry split on the fixed base (V13Y).** Market entry and every other (F, X) alternative are worse on drawdown in every window except PRE, and at equal risk the mean is lower; it has no B73-type ordering flaw; the ledger's 'sign change' on L3M is a mean-inside-MDE neutral and not a drawdown effect. Caveats: the optimum is sharp in X (in-sample selection), the value is concentrated in PE and Asia, and K7 NY-PM would prefer market entry. Nothing here meets the lead flag (no cell beats the shipped one).

## 6. How sharp is X = 3? (dip trigger in 0.25-pt steps; shipped per-book F; maxDD cut L3M / L6M / HOLD / MID / PRE / X' % vs shipped; mean change L6M, MDE)
| X (pts) | lock=None | d mean L6M | lock=12R | d mean L6M |
|---|---|---|---|---|
| 2.0 | -33 / -54 / -44 / +1 / 0 / -17 | -5.5k (9.7k) | -28 / -50 / -13 / +4 / -2 / -24 | -7.9k (12.4k) |
| 2.25 | -32 / -22 / -14 / +1 / -1 / -4 | -1.9k (3.5k) | -26 / -48 / -15 / 0 / -3 / -13 | -4.3k (9.8k) |
| 2.5 | -32 / -30 / -21 / -1 / -1 / -9 | -1.0k (1.9k) | -37 / -12 / -15 / -1 / -2 / -5 | -0.8k (1.9k) |
| 2.75 | -34 / -20 / -12 / +1 / 0 / -11 | -1.2k (1.4k) | -51 / -9 / 0 / +1 / 0 / -6 | -1.4k (2.0k) |
| **3.0 (shipped)** | 0 | 0 | 0 | 0 |
| 3.25 | -19 / -7 / -1 / -17 / -2 / -5 | -1.0k (1.5k) | -23 / -8 / 0 / -10 / +2 / 0 | -0.8k (1.3k) |
| 3.5 | -18 / -10 / -3 / -16 / -4 / -5 | -1.4k (1.8k) | -23 / -9 / +1 / -17 / 0 / 0 | -1.1k (1.7k) |
| 3.75 | -15 / +1 / 0 / -15 / 0 / -8 | -1.5k (2.3k) | -27 / -3 / +2 / -13 / +2 / 0 | -1.3k (2.0k) |
| 4.0 | -13 / -3 / -1 / -10 / -9 / -11 | -3.3k (3.9k) | -25 / +2 / -3 / -1 / +21 / +1 | -2.4k (3.7k) |
**X = 3 is a SPIKE, not a plateau**: a one-tick move (0.25 pt) in either direction costs -7..-20% of the L6M maxDD cut (lock=None) and about -$1.0k..-1.2k per week of mean (lock=12R: -8..-9% and -$0.8k..-1.4k); two ticks 2.5 / 3.5 cost -10..-30%; all 12 off-grid values have L6M cuts <= +2%. Because the dip is tied to the L2 gate bits and to the 1-s close grid, small shifts change which seconds fire. The shipped X = 3 is the in-sample best of the family; a live fill 1 tick different from the research fill would cost roughly the amounts above.

## 7. Purged walk-forward of the per book x session entry mode (market vs shipped 70/30), 2024-01..2026-10, and the multiplicity null
Method: the five split books x six sessions = 30 slices; each month, per slice, choose market entry if its trailing-12-month P&L exceeds the shipped split's, apply to the next month (the cube series of the two engine runs per slice; also an exact engine run with the chosen rows at F = 1). Compare: always-shipped, always-market, 500 additive / 20 engine random choice sets with the same market share (28-30% of slice-months).
| 2024-01..2026-10 (148 weeks) | total $ | weekly-cumulative maxDD $ |
|---|---|---|
| lock=None shipped | 2.516M | 129.7k |
| lock=None always market | 2.612M (+3.9%) | 126.6k |
| lock=None walk-forward choice (engine) | 2.605M | 125.6k |
| lock=None random choice (engine, mean of 20) | 2.570M | 127.3k |
| lock=12R shipped | 1.524M | 282.2k |
| lock=12R always market | 1.398M (-8.3%) | 265.7k |
| lock=12R walk-forward choice (engine) | 1.529M | 265.0k |
| lock=12R random choice (engine, mean of 20) | 1.551M | 263.7k |
Walk-forward ranks vs random choices: lock=None total rank 0.40, maxDD rank 0.35; lock=12R 0.55 / 0.65 (additive version: 0.42 / 0.68, 0.64 / 0.52): **the choice rule is no better than random.** Multiplicity null over the slices with a base maxDD > $20k (6 slices; random monthly mixes of the two modes, 2,000 draws, maximum slice cut): the best observed slice, K7 NY-PM market entry (+43% lock=None, +55% lock=12R L6M cut), against the null maximum's 95th percentile 0.45 (lock=None; median 0.29) and 0.54 (lock=12R; median 0.43): **inside the null (lock=None) / borderline (12R): ONE-SLICE, not a finding.**
Over the whole 2.8 years market entry is not worse than the split in lock=None (+3.9% total, -2.4% maxDD) and is -8% total with -6% maxDD in 12R; the split's advantage is concentrated in the recent windows (L3M .. MID) and in the PE book, not in PRE / X'. Verdict in section 5 stands for the recent regime ('keep'), softened for the long run: the split is a recent-window feature on a sharp parameter, with no evidence that a per-slice switch helps.

## 8. Execution risk: how much of the split's edge survives realistic live fills? (V13Y; shipped split re-simulated with a modified fill model; the shipped add is a MARKET order one second after the dip trigger: fill = close of the trigger second + 1 tick)
Variants: add fills 1 / 2 ticks (0.25 pt each) WORSE or 1 tick better than the research fill; add sent 1 s / 3 s late (fill price taken at trigger + delay); only 50% / 75% of the add lots fill; combined. Reference 'edge' = shipped minus market entry (F = 1) on the same metric, 'kept' = 1 - variant cut / market cut (maxDD cut vs the shipped base, L-window; >100% = better than shipped relative to market; unreliable where the market-entry edge is small, MID, PRE).
| variant | lock=None cut L3M / L6M / HOLD / MID / PRE / X' | d mean L6M (MDE) | L6M edge kept | lock=12R cut L3M / L6M / HOLD / MID / PRE / X' | d mean L6M (MDE) | L6M edge kept |
|---|---|---|---|---|---|---|
| shipped | 0 | 0 | 100% | 0 | 0 | 100% |
| add fills 1 tick better | +1 / +2 / +1 / +3 / +1 / +3 | +398 (93) | 108% | +3 / +1 / 0 / +1 / +1 / 0 | +269 (121) | 102% |
| add fills 1 tick worse | -31 / -20 / -12 / -2 / -1 / -16 | -959 (1,131) | 37% | -3 / -13 / 0 / -3 / -1 / 0 | -417 (597) | 79% |
| add fills 2 ticks worse | -32 / -22 / -14 / -7 / -2 / -33 | -2,515 (2,943) | 29% | -5 / -47 / -1 / -2 / -3 / -10 | -4,308 (9,635) | 23% |
| add sent 1 s late | -37 / -6 / 0 / 0 / +1 / -3 | -2,994 (4,570) | 81% | -3 / -39 / +1 / 0 / +16 / 0 | -4,223 (9,822) | 36% |
| add sent 3 s late | -33 / -16 / -8 / -5 / -5 / -18 | -2,815 (2,987) | 50% | -20 / -10 / +1 / 0 / +7 / 0 | -2,016 (2,889) | 84% |
| 75% of the add fills | -48 / -24 / -16 / +1 / +7 / -30 | -3,973 (4,503) | 25% | -28 / -42 / -10 / +20 / +11 / +2 | -6,375 (9,659) | 31% |
| 50% of the add fills | -22 / -42 / -33 / +24 / +6 / -13 | -8,036 (9,596) | negative (worse than market entry, -32%) | -18 / -39 / +17 / +5 / +9 / -9 | -7,373 (13,312) | 36% |
| 3 s late + 50% fills | -25 / +2 / +9 / +18 / +5 / -13 | -5,352 (5,770) | ~ | -19 / -41 / +12 / -3 / +5 / -10 | -6,711 (10,640) | 33% |
**Reading.** The split's edge is fragile to the live fill: a fill one tick (0.25 pt) worse than the research fill removes about 60% of the L6M drawdown edge under lock=None and 20% under 12R (mean -$1.0k / -$0.4k per week); two ticks worse removes ~70-77%; a 3-second late send removes half (lock=None) to 16% (12R); fills of only half of the add lots make the L6M result worse than no split at all (lock=None) or keep ~36% (12R). Signs are consistent (every degradation reduces the edge; a better fill raises it a little) but magnitudes differ between frames and the market-entry reference edge is small in some windows, so 'kept' percentages are indicative. Together with the sharp X = 3 optimum (section 6) this says the 70/30 split's research edge on the recent windows should be treated as an upper bound: the live add is a market order on a 1-second grid, and the recent edge shrinks by roughly a half under realistic slippage and partial fills. The sizes involved are inside the MDE for the mean in every row (the mean cost is -0.4k..-8k per week against MDE 0.6k-13k), so the statement concerns drawdown.
