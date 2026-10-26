# DS3 T-BRACKET-PM G1 - loss-side Trade Health grid (D3TH1, 2026-10-26)
Research only. Entries (tier 1): ST10, HM10 (live), KB = TE7_kelt3m_n14_m1.0, SM = TE6_st10m_n7_m3.0, EM = TE7_emax5m_f30_s50. Verdict type V2 trade-modifier, every cell paired per trade on identical entries vs the entry's own base bracket (60/60, 1R, flat 16:55).

## Verdict line
**Loss-side TH (G1): 0 PASS, 0 CANDIDATE, 4,800 DEAD of 4,800 cell x entry evaluations (960 cells x 5 entries) plus 1,228 neighbour evaluations.** The live TH-loss rule is negative on every entry; no conditional rule beats a random-timing cut with the same cut count and delay profile; the best of 960 cells on every entry is no better than the random-timing best-of-960 null. The MAE-only control (a shorter stop) and the time-only rule are also negative. No cell is registered in PAPER-ALL (nothing reached CANDIDATE), no direct L2 replay was needed (no survivor), no 3x3 widening (no PASS).

## What was run
* Full G1 space is 29,160 TH cells per entry (5 eligibility x 3 votes x 9 momentum x 9 stall x 6 efficiency x 2 eval frequencies) plus 12 time-only and 4 MAE-only. Preregistrable only as a staged fractional design: **960 screen cells** (2 live controls, 12 time-only X{0,5,10} x Y{5,10,20,30} min, 4 MAE-only D{15,20,30,40}, 28 one-factor-at-a-time around live ST 15/3/30, 914 per-factor-balanced space-filling draws, seed 20261026) = 3.3% of the TH space. 32 preregs of 30 cells, master sha256 `05c2373f...779c` in autopilot/DECISIONS.md before scoring (l2vast/ds3/prereg/DS3_TH_G1_master_prereg.md, G1_S00..S31).
* Control rows: `G1_TH_LIVE_ST` (min loss 15, 3 of 3, momentum 30 s/4, stall 30 s/4, efficiency 30 s/0.35, eval 1 s) and `G1_TH_LIVE_HM` (10/3/30) are in every entry's table (WT 10/2/30 not in tier 1).
* Engine: per-trade 1-s path from entry second to base-exit second (firmlib.sim_rrt, same builder as the ST/HM rows; exit class and pts reproduce the trade lists 100%), TH condition bits per second for all 24 condition settings, numba scan over cells. Kernel semantics = ap_th_port.th_scan; checked equal on 16,000 trade x config comparisons, 0 mismatches (g1_val.py). Cut fills at the close of the second after the trigger second; base exit wins if reached first. MAE-only fills at the -D level (gap-limited close) with stop-join cost.
* Cost: cut = market 0.995 pt; base exit = 1.01 pt on stops, 0 on targets, 0.995 on time-flat; 2x column doubles all of them. Delta = cut pts - base pts.
* Windows: selection WF-PRE 2024-02..2025-06; second holdout 2023-04..2024-01 (columns span23_*); main holdout 2025-07+ looked at once for the top-20 per entry + controls + best time/MAE cells (logged: track DS3_THG1, text out/g1/G1_PREHOLD.md written first). The ST/HM/KB/SM/EM series already had holdout looks in other tracks (disclosed in the text); this is the first look for loss-side TH.
* Ledger (struct48/ledger/trials.jsonl): 32 batch lines x 150 = 4,800 screen evaluations + 1,228 neighbour evaluations; cumulative corrected total after this track **42,701**. DSR is not meaningful for a set with no positive survivor; the best-of-N null replaces it.

## Headline numbers (WF-PRE paired pts/trade vs base, 1,000-draw session-block CI in rows; MDE = 80% power)
| entry | n trades (WF-PRE) | live ST rule 15/3/30 | live HM rule 10/3/30 | median of 960 cells | share of cells > 0 | best of 960 | random-timing best-of-960 null (median / 95th) |
|---|---|---|---|---|---|---|---|
| ST10 | 3,020 | -1.80 [-3.38,-0.27] (hold -0.15) | -2.12 [-3.81,-0.46] | -1.95 | 0.1% | +0.05 | +0.21 / +0.44 |
| HM10 | 2,285 | -0.32 [-2.15,+1.44] (hold -1.98) | -0.31 [-2.20,+1.54] (hold -2.32) | -1.38 | 9.2% | +1.05 | +0.68 / +0.99 |
| KB | 3,093 | -1.44 [-2.95,+0.08] | -2.10 [-3.71,-0.47] | -2.38 | 0.2% | +0.16 | +0.20 / +0.63 |
| SM | 905 | -2.50 [-5.28,+0.24] | -2.91 [-5.87,+0.05] | -3.33 | 0.9% | +0.32 | +0.55 / +1.14 |
| EM | 871 | -1.54 [-4.35,+1.15] | -1.86 [-4.90,+1.00] | -2.02 | 2.2% | +1.39 [+0.09,+2.55] (hold +0.75 [-0.73,+2.13]) | +1.36 / +1.82 |
Paired MDE (80% power, bootstrap) is about 1.5-2.7 pts/trade for a typical cell on ST/HM/KB and 3-4 on SM/EM; the live-control MDE on ST is 2.2 pts/trade. A cell with a true effect below that cannot be separated from zero on this window. The existing forward evidence (50 live ST cuts, +5.6 pts/trade [-11.8,+22.3]) has a 24-pt MDE and is consistent with this result.
Live ST rule on ST, the control the question started from: 61% of trades are cut; cut trades realise -24.7 pts vs -21.7 uncut counterfactual (EV per cut -3.0 pts); of cut trades 30% would have hit the target and 65% the stop; negative in both directions (long -1.81, short -1.80) and in every session; worse in quiet (-3.2) than wide (-0.4) conditions; 2x cost -1.98; second-holdout span -0.05, holdout -0.15 [-1.37,+1.03]. Random-timing placebo rank 0.30 (the rule is no better than cutting at random times with the same delay profile).

## Why the grid cannot win (mechanism seen in the data)
Cutting a loser early costs the 0.995 market fill and gives up the recoveries (30-45% of eligible losers reach the target); the conditions pick stop-bound trades no better than chance (placebo ranks of the live rules 0.27-0.99, never with a positive mean). Because the 60-pt stop is wide relative to the 5-30 pt eligibility depth, the cuts that help (stop-bound) and hurt (target-bound) offset almost exactly and costs decide the sign. Shorter-stop control (MAE-only): D=40 is the best of the four on ST (-0.96 [-2.28,+0.27]), HM (+0.31 [-1.07,+1.65], holdout -0.83), EM (-0.34); D=15/20 are the worst everywhere. Time-only: best cells are X0/Y20 on ST (-0.98) and X5/Y20 on EM (+0.46, holdout -3.10); nothing positive survives holdout.

## Finalists (top 20 per entry by WF-PRE mean + controls + best time/MAE; 123 cells) - tiers
* PASS: none. CANDIDATE: none. DEAD: all 123 finalists and the other 4,677 screen cells (reason in rows; screen cells beyond rank 20 are DEAD by the declared selection rule or because the pre mean <= 0).
* Cells with pre > 0 and holdout > 0 (the only ones that could have been CANDIDATE): ST 1, HM 4, KB 1, SM 4, EM 11. None passes the neighbour condition (every one has at least one single-step neighbour with the opposite sign); none has a pre CI excluding zero except EM `G1_0508` (+1.39 [+0.09,+2.55], placebo 0.994, hold +0.75 [-0.73,+2.13], 2nd-span -0.38, neighbours disagree, year share > 60%) which also equals the best-of-960 random null median (+1.36): selection from 960 cells, DEAD.
* Top by entry (full list: rows file): ST `G1_0563` +0.05 [-1.02,+1.10]; HM `G1_0069` +1.05 [-0.18,+2.17] (holdout negative); KB `G1_0527` +0.16 [-0.22,+0.50]; SM `G1_0720` +0.32 [-0.71,+1.29]; EM `G1_0508` as above.

## Columns available per cell (rows/DS3_TH_G1.json, copy DS3_TBRACKET_G1.json; ids `G1_<nnnn>__<ENTRY>`, controls `G1_TH_LIVE_ST__<ENTRY>`, `G1_TH_LIVE_HM__<ENTRY>`)
paired effect and CI, MDE, cut count and share, cut-trade P&L vs uncut counterfactual, would-hit-target and would-hit-stop shares, EV per cut, 2x-cost effect, long/short, by session, quiet/wide (60-min range above/below median), second-holdout span, placebo rank, neighbours, unlocked weekly delta ($, 10 lots). Finalists add: 10,000-draw CI, holdout effect with CI, freed minutes per cut and cuts per active day (the cooldown/attempt-budget column), weekly mean/SD/maxDD of the delta, year share.

## Limits (stated, not hidden)
* The weekly mean/SD/maxDD columns are the UNLOCKED per-trade delta x 10 lots; the exact lock engine (riskeng_pb / asm_*) was not run because no cell survived the trade-level criterion (V2: a trade-modifier is decided on the paired test). The cooldown/attempts-per-day budget is a column of freed time and cut frequency only; the knock-on of extra same-day entries needs signal regeneration and was not simulated (the forward report found 30 of 50 cuts followed by a later live entry).
* Screen is 3.3% of the factorial TH space; the declared best-of-960 null says no part of that sample is distinguishable from noise, not that no cell exists. Neighbours are single-step lattice neighbours; random-timing placebo draws delays from the cell's own cut-delay distribution, non-anticipating (a first version sampling uniformly to the base exit looked ahead and was discarded before any verdict).
* Cut fills use the 1-s close one second after the trigger (cancel wait + latency), not the L2 book; MAPPED basis. No finalist qualified for direct L2 replay.
* G2/G3/G4 (profit side, tape cuts, combinations) are other agents; this file covers G1 only.

Code: l2vast/ds3/code/g1/ (g1_extract, g1_prep, g1_kern, g1_val, g1_cells, g1_prereg, g1_screen, g1_an, g1_stage1, g1_s2pre, g1_s2final); data out/g1/ (per-entry path npz, stage1 parquet, s2pre.pkl, bestofN.txt, G1_cells.csv).

## Addendum 2026-10-26: live stop-join profile re-score of the G1 live rules (USER ORDER, D3TH1)

Same cells as G1 (`G1_TH_LIVE_ST` 15/3/30 and `G1_TH_LIVE_HM` 10/3/30 applied to ST, HM, KB, SM, EM; plus the two nearest MAE-only controls D=30 and D=40). No new cells, no new ledger trials. Rows: `l2vast/ds3/rows/DS3_TH_G1_LIVEJOIN.json`; code `l2vast/ds3/code/g1/g1_livejoin.py`.
**Cost model.** Original G1: every stop exit (base arm; MAE-only cut arm) costs a fixed 1.01 pt below the stop level, cut-arm market exits 0.995 pt. Live-join model (JOIN_RECON section 5.3, replay XJ3 queue, all history): expected stop-exit cost = -(p x (+0.52) + (1-p) x (-4.25)) pts, where p = join fill rate by ET hour of the STOP-EXIT time: 18-22 0.680, 22-02 0.597, 02-08 0.669, 08-12 0.847, 12-18 0.835 (so Asia 18-02 = 0.60-0.68; London overnight 02-08 = 0.669; 08:00 onward, including 08:00-09:30 London/NY open and all NY = 0.835-0.847). Resulting expected cost per stop exit: 1.39 pt (22-02), 1.04 (02-08), 0.99 (18-22), 0.20 (08-12), 0.28 (12-18). Applied as an expected value (not random draws) to the base arm's stop exits (the uncut counterfactual) and to MAE-only stop fills; the TH cut stays at the 0.995 market. Note the fixed 1.01 equals the live-join cost at p of about 0.68, i.e. the OVERNIGHT rate; the RTH profile is cheaper than 1.01, not dearer. The '0.78 average' (cost 0.53) was not what G1 used.
**Result: the live-join profile makes the live rule slightly WORSE, not better.** Cut trades are mostly in NY/RTH hours where uncut stops are cheap (p 0.84), so the uncut counterfactual improves by ~0.8 pt on those stops; Asia is unchanged to within 0.05 pt because 1.01 already equals the overnight cost.

### Paired delta, WF-PRE (2024-02..2025-06), pts per trade [95% session-block CI, 2,000 draws]; MDE = 80% power

| entry | rule | scope | n | cuts (share) | original (fixed 1.01) | live-join profile | MDE | EV/cut orig -> live-join | cut P&L vs uncut (live-join) | would hit target / stop |
|---|---|---|---|---|---|---|---|---|---|---|
| ST | ST | ALL | 3020 | 1843 (61%) | -1.80 [-3.36,-0.17] | -2.00 [-3.55,-0.38] | 2.2 | -2.96 -> -3.28 | -24.7 vs -21.4 | 30% / 65% |
| ST | ST | ASIA | 790 | 455 (58%) | -3.59 [-6.55,-0.59] | -3.59 [-6.55,-0.60] | 4.2 | -6.23 -> -6.23 | -26.7 vs -20.5 | 33% / 66% |
| ST | ST | LONDON | 747 | 496 (66%) | -0.13 [-3.13,+2.76] | -0.36 [-3.34,+2.52] | 4.2 | -0.20 -> -0.53 | -24.5 vs -24.0 | 30% / 70% |
| ST | ST | NY | 1483 | 892 (60%) | -1.69 [-4.03,+0.48] | -1.98 [-4.30,+0.18] | 3.2 | -2.82 -> -3.30 | -23.8 vs -20.5 | 29% / 62% |
| ST | HM | ALL | 3020 | 1991 (66%) | -2.12 [-3.78,-0.33] | -2.32 [-3.98,-0.54] | 2.4 | -3.21 -> -3.51 | -20.5 vs -16.9 | 34% / 61% |
| ST | HM | ASIA | 790 | 490 (62%) | -4.48 [-7.55,-1.25] | -4.48 [-7.55,-1.26] | 4.6 | -7.22 -> -7.22 | -23.2 vs -15.9 | 37% / 62% |
| ST | HM | LONDON | 747 | 531 (71%) | +0.81 [-2.47,+4.01] | +0.58 [-2.69,+3.75] | 4.7 | +1.14 -> +0.82 | -19.7 vs -20.5 | 33% / 67% |
| ST | HM | NY | 1483 | 970 (65%) | -2.33 [-4.89,+0.05] | -2.62 [-5.17,-0.24] | 3.5 | -3.56 -> -4.01 | -19.5 vs -15.5 | 33% / 58% |
| HM | ST | ALL | 2285 | 1411 (62%) | -0.32 [-2.08,+1.44] | -0.52 [-2.27,+1.24] | 2.5 | -0.51 -> -0.84 | -24.9 vs -24.1 | 28% / 67% |
| HM | ST | ASIA | 673 | 391 (58%) | -2.42 [-5.65,+0.49] | -2.44 [-5.66,+0.47] | 4.4 | -4.17 -> -4.19 | -27.7 vs -23.5 | 30% / 69% |
| HM | ST | LONDON | 569 | 367 (64%) | +0.53 [-3.08,+4.18] | +0.30 [-3.30,+3.94] | 5.2 | +0.82 -> +0.47 | -23.9 vs -24.4 | 30% / 70% |
| HM | ST | NY | 1043 | 653 (63%) | +0.58 [-2.10,+3.32] | +0.27 [-2.39,+3.00] | 3.8 | +0.92 -> +0.44 | -23.8 vs -24.3 | 25% / 64% |
| HM | HM | ALL | 2285 | 1510 (66%) | -0.31 [-2.20,+1.56] | -0.51 [-2.38,+1.34] | 2.7 | -0.47 -> -0.78 | -20.5 vs -19.7 | 31% / 63% |
| HM | HM | ASIA | 673 | 414 (62%) | -2.43 [-5.77,+0.74] | -2.44 [-5.78,+0.72] | 4.7 | -3.95 -> -3.97 | -23.4 vs -19.4 | 34% / 65% |
| HM | HM | LONDON | 569 | 389 (68%) | +1.13 [-2.68,+5.03] | +0.90 [-2.88,+4.77] | 5.5 | +1.66 -> +1.32 | -19.5 vs -20.8 | 33% / 67% |
| HM | HM | NY | 1043 | 707 (68%) | +0.27 [-2.41,+3.11] | -0.04 [-2.70,+2.78] | 4.0 | +0.39 -> -0.06 | -19.4 vs -19.3 | 29% / 60% |
| KB | ST | ALL | 3093 | 1882 (61%) | -1.44 [-2.94,+0.07] | -1.63 [-3.13,-0.13] | 2.2 | -2.36 -> -2.68 | -24.8 vs -22.1 | 29% / 65% |
| KB | ST | ASIA | 837 | 470 (56%) | -2.41 [-5.31,+0.53] | -2.41 [-5.31,+0.54] | 4.2 | -4.30 -> -4.29 | -26.6 vs -22.3 | 32% / 68% |
| KB | ST | LONDON | 699 | 463 (66%) | -0.30 [-3.49,+3.07] | -0.52 [-3.70,+2.86] | 4.7 | -0.45 -> -0.78 | -24.3 vs -23.6 | 30% / 69% |
| KB | ST | NY | 1557 | 949 (61%) | -1.42 [-3.54,+0.61] | -1.71 [-3.81,+0.30] | 2.9 | -2.33 -> -2.81 | -24.1 vs -21.3 | 28% / 62% |
| KB | HM | ALL | 3093 | 2054 (66%) | -2.10 [-3.75,-0.53] | -2.30 [-3.94,-0.73] | 2.3 | -3.16 -> -3.46 | -20.2 vs -16.7 | 34% / 61% |
| KB | HM | ASIA | 837 | 505 (60%) | -2.29 [-5.40,+0.70] | -2.28 [-5.39,+0.71] | 4.3 | -3.79 -> -3.78 | -22.0 vs -18.2 | 35% / 64% |
| KB | HM | LONDON | 699 | 505 (72%) | -1.41 [-4.76,+2.15] | -1.63 [-4.97,+1.92] | 5.0 | -1.95 -> -2.25 | -19.6 vs -17.3 | 36% / 64% |
| KB | HM | NY | 1557 | 1044 (67%) | -2.31 [-4.66,-0.07] | -2.61 [-4.94,-0.38] | 3.2 | -3.44 -> -3.89 | -19.6 vs -15.7 | 33% / 58% |
| SM | ST | ALL | 905 | 556 (61%) | -2.50 [-5.40,+0.06] | -2.70 [-5.59,-0.14] | 3.9 | -4.07 -> -4.40 | -24.8 vs -20.4 | 31% / 65% |
| SM | ST | ASIA | 305 | 162 (53%) | -3.62 [-8.25,+0.69] | -3.67 [-8.28,+0.64] | 6.3 | -6.81 -> -6.91 | -28.6 vs -21.7 | 32% / 67% |
| SM | ST | LONDON | 266 | 184 (69%) | -3.68 [-9.67,+2.03] | -3.92 [-9.89,+1.78] | 8.3 | -5.32 -> -5.67 | -23.4 vs -17.8 | 35% / 64% |
| SM | ST | NY | 334 | 210 (63%) | -0.54 [-4.84,+3.78] | -0.85 [-5.11,+3.42] | 6.1 | -0.86 -> -1.35 | -23.0 vs -21.6 | 28% / 63% |
| SM | HM | ALL | 905 | 611 (68%) | -2.91 [-5.97,+0.00] | -3.12 [-6.16,-0.21] | 4.2 | -4.31 -> -4.61 | -19.8 vs -15.2 | 36% / 60% |
| SM | HM | ASIA | 305 | 181 (59%) | -4.56 [-9.66,+0.20] | -4.61 [-9.71,+0.14] | 7.1 | -7.68 -> -7.77 | -22.9 vs -15.1 | 38% / 62% |
| SM | HM | LONDON | 266 | 194 (73%) | -3.12 [-9.08,+2.71] | -3.37 [-9.27,+2.45] | 8.5 | -4.28 -> -4.62 | -19.0 vs -14.4 | 38% / 61% |
| SM | HM | NY | 334 | 236 (71%) | -1.23 [-5.96,+3.72] | -1.55 [-6.26,+3.36] | 6.8 | -1.74 -> -2.19 | -18.2 vs -16.0 | 33% / 58% |
| EM | ST | ALL | 871 | 530 (61%) | -1.54 [-4.17,+1.17] | -1.72 [-4.35,+0.98] | 3.9 | -2.53 -> -2.83 | -24.6 vs -21.8 | 29% / 65% |
| EM | ST | ASIA | 293 | 159 (54%) | -0.22 [-4.81,+4.19] | -0.26 [-4.83,+4.15] | 6.5 | -0.40 -> -0.48 | -28.3 vs -27.8 | 27% / 72% |
| EM | ST | LONDON | 253 | 169 (67%) | -2.66 [-8.33,+2.67] | -2.88 [-8.50,+2.43] | 8.0 | -3.98 -> -4.31 | -22.9 vs -18.6 | 34% / 65% |
| EM | ST | NY | 325 | 202 (62%) | -1.86 [-6.23,+2.38] | -2.14 [-6.47,+2.07] | 6.1 | -3.00 -> -3.45 | -23.2 vs -19.7 | 27% / 59% |
| EM | HM | ALL | 871 | 578 (66%) | -1.86 [-4.81,+1.11] | -2.05 [-4.98,+0.91] | 4.2 | -2.80 -> -3.08 | -20.8 vs -17.7 | 33% / 61% |
| EM | HM | ASIA | 293 | 168 (57%) | -0.15 [-5.07,+4.60] | -0.19 [-5.10,+4.57] | 6.9 | -0.26 -> -0.34 | -24.9 vs -24.5 | 30% / 70% |
| EM | HM | LONDON | 253 | 183 (72%) | -3.59 [-9.65,+2.03] | -3.82 [-9.86,+1.78] | 8.5 | -4.97 -> -5.28 | -19.2 vs -13.9 | 38% / 61% |
| EM | HM | NY | 325 | 227 (70%) | -2.05 [-6.82,+2.64] | -2.34 [-7.08,+2.32] | 6.9 | -2.93 -> -3.35 | -19.0 vs -15.6 | 30% / 55% |

### Holdout (2025-07+) RE-READ and 2023-04..2024-01 span (same rules, same data; the holdout was already looked at once in G1, this is a re-read of the same two pre-specified rules, no selection is made on it)

| entry | rule | holdout original | holdout live-join | span23 original | span23 live-join |
|---|---|---|---|---|---|
| ST | ST | -0.15 [-1.35,+1.01] | -0.31 [-1.51,+0.85] | -0.05 [-2.50,+2.42] | -0.30 [-2.74,+2.15] |
| ST | HM | -0.63 [-1.90,+0.61] | -0.79 [-2.06,+0.44] | +0.86 [-1.71,+3.43] | +0.60 [-1.96,+3.16] |
| HM | ST | -1.98 [-3.55,-0.45] | -2.12 [-3.68,-0.60] | -0.18 [-2.77,+2.41] | -0.43 [-2.99,+2.15] |
| HM | HM | -2.32 [-3.97,-0.75] | -2.46 [-4.11,-0.90] | -0.07 [-2.85,+2.65] | -0.32 [-3.08,+2.38] |
| KB | ST | -0.43 [-1.72,+0.83] | -0.60 [-1.87,+0.65] | -0.32 [-2.71,+2.19] | -0.57 [-2.95,+1.92] |
| KB | HM | -0.59 [-1.95,+0.75] | -0.76 [-2.11,+0.57] | -0.40 [-2.90,+2.29] | -0.65 [-3.15,+2.03] |
| SM | ST | -0.23 [-2.58,+2.16] | -0.37 [-2.71,+2.02] | -0.20 [-3.90,+3.42] | -0.43 [-4.12,+3.17] |
| SM | HM | -0.79 [-3.43,+1.99] | -0.93 [-3.54,+1.84] | +0.10 [-3.85,+3.82] | -0.14 [-4.07,+3.56] |
| EM | ST | -1.54 [-4.32,+1.20] | -1.67 [-4.44,+1.03] | -1.15 [-4.63,+2.47] | -1.37 [-4.84,+2.22] |
| EM | HM | -1.32 [-4.28,+1.56] | -1.46 [-4.40,+1.42] | -1.18 [-4.94,+2.66] | -1.40 [-5.14,+2.42] |

### MAE-only controls (D=30, D=40; stop-join fill at the -D level), WF-PRE, scope ALL

| entry | D | original | live-join | MDE |
|---|---|---|---|---|
| ST | 0016 (30) | -1.86 [-3.44,-0.32] | -1.80 [-3.37,-0.27] | 2.2 |
| ST | 0017 (40) | -0.96 [-2.24,+0.29] | -0.92 [-2.20,+0.32] | 1.8 |
| HM | 0016 (30) | -1.19 [-3.06,+0.66] | -1.14 [-3.00,+0.70] | 2.6 |
| HM | 0017 (40) | +0.31 [-1.06,+1.77] | +0.34 [-1.02,+1.79] | 2.0 |
| KB | 0016 (30) | -1.79 [-3.34,-0.34] | -1.72 [-3.27,-0.27] | 2.2 |
| KB | 0017 (40) | -1.70 [-3.01,-0.42] | -1.66 [-2.96,-0.38] | 1.8 |
| SM | 0016 (30) | -1.56 [-4.46,+1.07] | -1.54 [-4.40,+1.08] | 3.9 |
| SM | 0017 (40) | -2.06 [-4.48,+0.19] | -2.04 [-4.46,+0.20] | 3.3 |
| EM | 0016 (30) | -0.65 [-3.41,+2.00] | -0.62 [-3.37,+2.02] | 3.8 |
| EM | 0017 (40) | -0.34 [-2.62,+1.75] | -0.32 [-2.59,+1.76] | 3.1 |

### G1 replay by cut size (points lost at the cut from entry; cut-trade mean delta per cut, live-join profile, 95% CI of the per-cut mean, whole span 2023-02..2026-10)

| entry | <15 pts | 15-25 pts | >25 pts |
|---|---|---|---|
| ST (live ST rule) | -0.80 [-4.3,+2.7] n=1030, tgt 36% | -3.28 [-5.6,-0.9] n=2184, tgt 34% | +0.32 [-1.8,+2.5] n=1819, tgt 19% |
| HM (live ST rule) | -5.74 [-9.7,-1.8] n=820, tgt 39% | -1.77 [-4.4,+0.9] n=1683, tgt 32% | +0.09 [-2.4,+2.5] n=1380, tgt 19% |
| KB (live ST rule) | -4.10 [-7.6,-0.7] n=1069, tgt 38% | -1.52 [-3.8,+0.7] n=2343, tgt 32% | -0.20 [-2.3,+1.9] n=1913, tgt 19% |
| SM (live ST rule) | -2.73 [-8.9,+3.5] n=330, tgt 38% | -4.25 [-8.6,+0.1] n=653, tgt 34% | +2.56 [-1.4,+6.5] n=478, tgt 16% |
| EM (live ST rule) | -0.33 [-6.7,+6.0] n=308, tgt 35% | -4.10 [-8.5,+0.3] n=631, tgt 34% | -1.00 [-5.2,+3.2] n=489, tgt 19% |

The forward (live) split of the 50 ST cuts by session and by cut size, set next to the ST replay numbers, is in FORWARD_REGISTER.md (section Forward TH-cut counterfactual) and REPORT_FORWARD_TH.md; bucket definition: points lost at the cut vs the live entry price. All live group CIs include zero and the live MDEs (24-81 pts per cut) exceed every replay per-cut effect, so live and replay are not distinguishable by session or size.
