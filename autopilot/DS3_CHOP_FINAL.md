# DS3_CHOP_FINAL - T-CHOP full scope (D3CH, 2026-10-27). Block 0 is kept in DS3_CHOP_BLOCK0.md.
**Chop: 0 PASS, 22 CANDIDATE of 169 scorable cells (+ block 0: 0 PASS, 0 CANDIDATE of 13). Best diversifier / recommended: B3_F19 (NQ+ES+RTY union dip-buy basket, direct basis), Sharpe 1.80, corr -0.15, losing-week P&L +$32.7k/wk (stack L25 -$135.0k/wk), marginal +0.89 WF / +1.59 HOLD, maxDD delta +$61.6k WF / -$27.3k HOLD.**

## 1. Verdict and PASS / CANDIDATE list
No cell is a PASS. CANDIDATES (all fail exactly one gate; G8 identity passed where tested): X09 (fails M), B2_X09_DG1 (fails M), B2_X09_DG2 (fails M), B3_F02 (fails G4), B3_F05 (fails G4), B3_F06 (fails G4), B3_F08 (fails G4), B3_F15 (fails G4), B3_F19 (fails G4), B3_F20 (fails G4), B4_F05_K3 (fails G4), B4_F05_K6 (fails G4), B4_F19_K2 (fails G4), B4_F19_K6 (fails G4), B4_F20_K2 (fails G4), B4_F20_K3 (fails G4), B4_F20_K5 (fails G4), B4_F20_K6 (fails G4), B4_F06_K5 (fails G4), B4_F08_K2 (fails G4), B4_F08_K5 (fails G4), B4_F15_K2 (fails G4).
Family of the survivors: ONE mechanism, the overnight dip-buy above SMA200 (RSI2 / IBS / 2-3 lower opens), made measurable by pooling NQ/ES/RTY/YM (B3, 3-5.5 trades/wk). Single-index versions (X09, B2_X09_DG1/DG2) fail only the 3-trades/wk gate. Every B3/B4 candidate fails G4 only on the SIGN of dMaxDD in the walk-forward window (NOT verified as April 2025 for the baskets: see addendum A0, the basket drawdown is 2024-04..2024-08); HOLD dMaxDD is negative for F05, F19, F20 and F08 (positive for F02, F15, F06). Gates were not loosened.
Blocks (ledger +228 cells beyond block 0): B1 28 ungated families, B2 30 gated dip/gap, B2C 30 gated intraday fades (control), B3 20 frequency, B4 30 maxDD guards, B5 20 tape exhaustion (2 empty), B6 20 order types; hashes in DECISIONS.md; one holdout look per track; block (v) = direct re-pricing + robustness of the top 5 (X09, B3_F02, B3_F05, B3_F19, B3_F15, declared before the replay).

## 2. Top 10 regardless of verdict (target conditions met of 6; failed gate and size; MDE; forward weeks)
## Top 10 across blocks B1+B2+B2C+B3+B4+B5+B6 by the 2.1 target (conditions met of 6: corr<=0.2, L25>0, chop>0, marginal>0, dMaxDD<0, Sharpe>=0.8), regardless of verdict

| rank | cell | conditions | Sharpe | corr | L25 | trades/wk | failed gates | per-trade mean / SD ($, WF, n) | forward weeks to settle the mean (80% power, 2.8 SD/sqrt(n)) |
|---|---|---|---|---|---|---|---|---|---|
| 1 | B2_X09_DG2 | 6 | 1.51 | +0.04 | 19.5k | 0.27 | M | 2459 / 5510 (n=39) | 143 |
| 2 | B2_X09_DG1 | 6 | 1.50 | -0.02 | 15.6k | 0.18 | M | 2664 / 4930 (n=26) | 147 |
| 3 | X09 | 6 | 1.48 | -0.05 | 22.6k | 0.33 | M | 2069 / 6401 (n=47) | 227 |
| 4 | X11 | 6 | 1.40 | -0.07 | 20.4k | 0.73 | G6a, M | 1222 / 6112 (n=104) | 268 |
| 5 | B2_X09_DG3 | 6 | 1.37 | +0.04 | 15.3k | 0.11 | G6a, M | 2870 / 4324 (n=15) | 168 |
| 6 | B2_X11_DG1 | 6 | 1.30 | -0.01 | 11.6k | 0.44 | G6a, G6b, M | 1405 / 5097 (n=62) | 236 |
| 7 | X06 | 6 | 1.21 | -0.16 | 30.6k | 0.64 | G6a, M | 1197 / 5788 (n=91) | 286 |
| 8 | B2_X06_DG2 | 6 | 1.07 | -0.16 | 31.0k | 0.58 | G6a, G6b, M | 1112 / 5731 (n=82) | 361 |
| 9 | B2_X11_DG3 | 6 | 1.03 | +0.01 | 8.1k | 0.27 | G6a, G7, M | 1500 / 5352 (n=38) | 373 |
| 10 | B2_X12_DG3 | 5 | 2.24 | -0.09 | 28.5k | 1.28 | G4, G7, M | 1604 / 4943 (n=182) | 58 |
How to read the failed-gate column: M = trades/wk below 3 (gap to 3 = 3 - trades/wk; the gate is not loosened, B3 shows the family can be made measurable); G6a/G6b = placebo rank below 0.95 (the rank is in the table of DS3_CHOP_B23.md); G4 = marginal Sharpe or dMaxDD sign. Forward weeks = weeks for the per-trade mean to reach 80% power given the observed mean and SD (2.8 SD/sqrt(n) rule, WF per-trade figures); the weekly-mean MDE at equal risk is 13.5k/wk (SD 57.3k, 142 weeks), the L25-week-mean MDE about 27k/wk.

## 3. RECOMMENDED-FOR-SIM: B3_F19 (spec DS3_SPEC_B3_F19.md, forward-register entry l2vast/struct48/paper_all/ds3_B3_F19.json)
Reason: it is the best cell with a positive DIRECT holdout ($23.0k/wk equal risk), non-negative marginal line (+0.89 WF / +1.59 HOLD), corr -0.15, both placebos beaten (a 0.98, b 1.00), identity passed, and 3.39 trades/wk (measurable). It does NOT pass G4 (dMaxDD +$61.6k WF; -$27.3k HOLD), and its WF maxDD at equal risk is large ($519k vs ST10 $263k), so it is a Sim candidate, not a PASS. RSI2T_t10 (block 0) and X09 stay as lower-frequency companions: X09 (CANDIDATE, fails M only, dMaxDD -$129k WF / -$67k HOLD, year share 0.44) has the cleanest drawdown behaviour but 0.33 trades/wk (about 227 forward weeks). Direct basis: price legs of NQ/ES/RTY priced on mbp-10 (coverage F19 94% of trades; ES/RTY before 2023-08 and the YM leg of the 4-index cells mapped); direct and mapped agree within 1% in every cell (direct minus mapped per trade within a few $ per unit; the fills are half a tick per side up to 50 lots at 15:56 ET); no raw-vs-adjusted mixing (every direct P&L is a difference of two raw fills of the same contract, roll-crossing trades dropped).

## 4. Block (v) table: top 5 on the direct basis (equal-risk to ST10; stack and cap as before)
| cell | direct coverage | lots (eq. risk) | WF $/wk | HOLD $/wk | 2023-04..24-01 | Sharpe | maxDD WF | corr stack | L25 $/wk | chop +60 | marg WF/HOLD | dMaxDD WF/HOLD | 1.5x cost WF | 2x cost WF | boot mean 95% CI | boot maxDD p5/50/95 (obs) | year means 2024/25/26 | max-year share |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| X09 | 97% | 17.2 | 11.7k | 12.2k | 8.2k | 1.47 | 301.8k | -0.05 | 22.6k | 247.5k | +0.48/+0.83 | -129.0k/-67.3k | 11.7k | 11.7k | [4.9k, 22.0k] | 83.7k/230.4k/471.3k (301.8k) | 9.8k/10.0k/15.8k | 0.44 |
| B3_F02 | 69% | 8.4 | 14.7k | 21.6k | 1.3k | 1.84 | 344.8k | -0.12 | 29.0k | 204.6k | +0.73/+1.17 | +123.2k/+110.6k | 14.2k | 13.8k | [6.5k, 23.1k] | 185.6k/291.5k/482.9k (344.8k) | 10.3k/13.3k/25.1k | 0.51 |
| B3_F05 | 71% | 8.6 | 11.7k | 20.4k | 5.0k | 1.47 | 318.9k | -0.21 | 33.4k | 322.7k | +0.63/+1.23 | +23.6k/-26.4k | 11.3k | 10.9k | [2.7k, 21.0k] | 191.7k/326.8k/592.9k (318.9k) | 4.6k/7.9k/25.7k | 0.67 (fails 0.60) |
| B3_F19 | 94% | 10.1 | 14.3k | 23.0k | 9.2k | 1.80 | 519.2k | -0.15 | 32.7k | 281.1k | +0.89/+1.59 | +61.6k/-27.3k | 13.9k | 13.5k | [5.1k, 23.3k] | 183.3k/350.2k/664.6k (519.2k) | 3.0k/17.8k/23.9k | 0.54 |
| B3_F15 | 70% | 5.6 | 13.7k | 23.8k | 7.0k | 1.73 | 378.9k | -0.09 | 29.0k | 244.0k | +0.59/+1.22 | +92.1k/+14.5k | 13.4k | 13.2k | [4.8k, 22.3k] | 184.1k/317.8k/611.5k (378.9k) | 2.6k/16.4k/23.4k | 0.55 |
Cost multipliers are applied on the mapped basis (fee + 2 ticks/lot); costs barely matter for this overnight sleeve. The observed maxDD sits inside the day-block bootstrap band (4-week blocks, 2000 draws). Largest-year share: 2026 carries the most in every cell (0.44-0.67); B3_F05 exceeds the 0.60 limit. Not run in the robustness block: VIX terciles, capacity curve above the equal-risk lots (fills are flat to 50 lots at 15:56), mirror control, limit-fill latency sensitivity. 50-cap concurrency: replay of the interval overlap with KB+SM+PB (pre-lock) gives an NQ line peak of 50 lots at the cap line for every cell by construction of the cap; beside DS2 (27 nominal) + DS3 trio the sleeve adds its NQ lots only for the overlap hours (overnight holds overlap every NQ trend trade), so the combined line needs the cap line scale shown in the marginal columns; DS2 has no interval table (nominal 27 lots).

## 5. Structural read (which axis moved)
* Entry family: the only axis that moved the result. Overnight dip-buy (daily close, SMA200 filter) carries a positive, stack-uncorrelated edge; every intraday fade family (Bollinger, Keltner, VWAP 2/3 sigma, prior-day/overnight/opening-range sweeps, Asia/London range fades, KB/SM failed-breakout fades, cross-asset divergence, first-hour, end-of-Asia, event reversion) is negative after cost ungated (mean R per trade -0.02 to -0.11) on NQ.
* Gates (B2, B2C): on dip-buys they thin trades without raising the placebo-adjusted edge (B2 gated X09 cells keep the CANDIDATE status but drop below 0.3 trades/wk); on the intraday fades gates do NOT rescue them (control: 2 of 29 gated fades have a positive WF mean, both on <90 trades). Claim tested, not assumed.
* Order type (B6): resting-limit entries (fill rate 92-99% under the trade-through rule, which flatters passive fills) improve R by 0.00-0.05 but only the gap fill (X24) is positive (+0.04 to +0.10 R) and it fails the placebo and 2023-span gates. Bars axis (D3BX range/Renko/volume/dollar bars): not run, a limit-order tick simulator per bar type does not exist.
* Tape (B5): the exhaustion flags select better-than-random extremes (placebo (b) ranks 0.9-1.0 for delta divergence, stacked imbalance, aggressor exhaustion, large-print clusters) but every cell stays negative after cost (best: B5_T8_A cumulative-delta BOS against the move, WF +$2.0k/wk, Sharpe 0.25, placebos 1.00/1.00, but marginal Sharpe -0.40 WF, 0.85 trades/wk, 2023 span -$5.0k). 9 of 10 features are not NT8-bar executable (README_TAPELAYER proxy identity 5-60%).
* Stops / guards (B4): a catastrophic stop (K8) destroys the edge (mean about zero), crash guards (falling-knife K2, vol cap K3, compression K4, rising SMA K6, concurrency cap K1) reduce Sharpe more than they reduce the April 2025 loss; no guard turned the WF dMaxDD sign. Frequency (B3) is what moved the measurability gate.
* Instruments: ES and RTY are as good as NQ; YM is weaker (mapped only).

## 6. Power statement
Per-trade MDE (80% power) of the dip-buy cells is $0.7k-2.6k on trade SDs of $4.9k-6.4k with n = 47-480 WF trades (observed means $0.8k-2.9k); weekly-mean MDE 13.5k/wk at equal risk with SD 57.3k and 142 weeks: effects below that are not resolvable on the stack-relative weekly test, so these are confirmed by the per-trade and placebo tests, not by weekly significance. Forward weeks to settle the per-trade mean: 58 (B3 basket cells) to 230-460 (single-index cells). The L25-week (36 weeks) mean MDE is about 27k/wk; the observed L25 means (+$20k to +$33k) are 0.7-1.2 MDE: suggestive, not proven (timing-shift rank of L25 P&L 0.96-0.99 for five cells).

## 7. Deviations, disclosures
* All numbers mapped (1-min bars, 1 tick/side + fee) except block (v) direct re-pricing of the dip-buy legs; direct coverage is 69-97% by trade (ES/RTY before 2023-08 and YM mapped).
* Holdout: one look per track (DS3_TCHOP, _B1, _B2, _B2C, _B3, _B4, _B5, _B6; _V5 re-pricing note). Block-0 sleeves and several signal rules were seen on the holdout by earlier tracks. Smoke test on the full 2013-2026 history before the B1 freeze (mean R per trade of 9 generators) is disclosed in that prereg. B3 and B4 were designed after seeing B1-B2 results (stated in their preregs).
* Selection: the top-5 and the recommendation are chosen among 169 scorable cells with a placebo that does not penalise selection; best-of-N (block 0): the best marginal Sharpe of the 12 block-0 cells did not beat the best of 12 timing-destroyed copies (rank 0.25); the B3 cells share one mechanism and are not independent evidence (their pairwise weekly corr is high).
* Placebos for basket/union cells draw equal-weight instrument-days (weights and concurrency scaling ignored); B4 pool (b) for K1/K8 uses the SMA200 regime only.
* B5: 2 cells empty (T10 feature never fired, T1 absorption fired once); dupwin bars excluded.
* Replay: chop_direct.py via the governor, cap respected (8 workers), no kills; both legs sets finished (112 + 115 symbol-months).
* Not done: ORB/range-book direct replay (DEAD earlier), bars axis in block (iii), VIX terciles, mirror control, forward-register evaluator wiring.

## 8. Files
autopilot/DS3_CHOP_B1.md, DS3_CHOP_B23.md (all cell tables), DS3_CHOP_BLOCK0.md, DS3_SPEC_B3_F19.md, DS3_SPEC_RSI2T_t10.md, prehold texts DS3_TCHOP_*_PREHOLD.md; preregs l2vast/ds3/prereg/T-CHOP*_prereg.md; numbers l2vast/ds3/out/CHOP/*.json; rows rows/DS3_TCHOP.json; paper_all/ds3_B3_F19.json; code l2vast/ds3/code/chop*.py, x_chop*.py.


## ADDENDUM (2026-10-27, block (v) gaps closed on lead request; verdict line above unchanged: B3_F19 is a CANDIDATE, not a PASS)
Code l2vast/ds3/code/chop_addendum.py, numbers l2vast/ds3/out/CHOP/addendum.json. All on the direct-basis equal-risk series of block (v) (WF 142 weeks); no replay needed.
**A0. Correction to the narrative above.** The section-1/5 wording that the B3/B4 dMaxDD problem "comes from April 2025" is not verified for B3_F19. B3_F19's own WF maxDD ($519k) runs from 2024-04-11 to 2024-08-05 (the 2024-08-05 volatility shock: -$205k that day, -$153k on 08-02, -$140k on 07-24). Excluding April 2025 changes nothing: WF mean $14.6k/wk, Sharpe 1.82, maxDD $519k (139 weeks); HOLD unchanged ($23.0k, Sharpe 2.92, maxDD $184k). April 2025 hurt the single-index X-cells (RSI2C/IBS: two crash dip-buys at -$19.9k/lot), not this basket's maxDD. The dMaxDD sign for the baskets is a 2024 (July-August) effect and a 2024-specific weakness: the cells earn $3.0k/wk in 2024 against $17.8k and $23.9k in 2025 and 2026.
**A1. VIX terciles** (weekly equal-risk P&L, WF weeks; VIX close before the week's first label day; cuts 15.19 / 21.21 fixed from data <= 2023-01-31). n weeks / mean / weekly SD:
| cell | low VIX (<=15.2) n/mean/SD | mid (15.2-21.2) | high (>21.2) |
|---|---|---|---|
| X09 | 49 / -1.2k / 68.8k | 72 / 22.1k / 53.8k | 21 / 5.9k / 26.9k |
| B3_F02 | 49 / 2.1k / 57.6k | 72 / 23.7k / 57.5k | 21 / 12.9k / 52.8k |
| B3_F05 | 49 / -2.8k / 53.8k | 72 / 17.5k / 58.6k | 21 / 25.5k / 56.7k |
| B3_F19 | 49 / -0.8k / 61.3k | 72 / 22.8k / 55.4k | 21 / 20.3k / 49.2k |
| B3_F15 | 49 / 5.8k / 55.5k | 72 / 19.8k / 52.9k | 21 / 11.2k / 74.6k |
| STACK (reference) | 49 / 46.0k | 72 / 43.5k | 21 / 71.8k |

| B3_F19 year x VIX tercile | low | mid | high |
|---|---|---|---|
| 2024 | 28 wk / 4.5k | 17 wk / 0.3k | 3 wk / 4.0k |
| 2025 | 9 wk / -0.7k | 31 wk / 23.5k | 12 wk / 17.0k |
| 2026 | 12 wk / -13.3k | 24 wk / 37.8k | 6 wk / 35.1k |

Reading: every dip-buy cell earns about zero in the lowest VIX tercile (-$2.8k to +$5.8k/wk) and 80-90% of its gain in the middle and high terciles; the stack earns $44-72k/wk in all three, so the sleeve diversifies the stack but is itself a volatility-conditional edge (2024 low-VIX weeks +$4.5k, 2026 low-VIX weeks -$13.3k for F19). Weekly SD per tercile is 49-74k (no tercile with a distinctly higher SD except X09/F15 in the high tercile).
**A2. Mirror and random-in-regime control (B3_F19 rule, NQ+ES+RTY, same weights, same scale):**
* Mirror (short when o < SMA200 and (RSI2 > 80 or 3 higher opens or IBS > 0.8), exit next 15:55): 90 trades, $+52 per unit trade (before weights/scale), WF mean $210/wk, Sharpe 0.04, HOLD $-3,827/wk: the inverted trigger earns nothing, as the mechanism (long-side overnight liquidity premium) predicts.
* Random-in-regime with the same time-of-day window (15:56 ET entry, one-day hold): the already-reported placebo (b) ranks 0.997 (300 draws of days with o > SMA200). The unconditional version, long EVERY day with o > SMA200 (the regime beta, 1743 trades), earns WF $15,673/wk at the same scale (Sharpe 0.87, maxDD $737k, HOLD $21,825/wk) against the signal's $14.3k/wk (Sharpe 1.80, maxDD $519k): the mean per trade is 838 for the signal vs 255 for any above-SMA200 day (3.3x), so the signal improves Sharpe (1.80 vs 0.87) and trades 8x less often, but the absolute weekly mean is the regime's; a pure above-SMA200 long book is the benchmark this CANDIDATE must be read against (it has the same 2024 drawdown).
**A3. Concentration (B3_F19, WF gain $2.03M at equal risk):** by year 2024 7% / 2025 43% / 2026 50%; by instrument ES 38% / NQ 37% / RTY 25%; 5 largest trades 19% of the WF gain (2026-06-11 NQ +$86.5k, 2026-07-30 NQ +$83.3k, 2026-02-06 RTY +$75.9k and ES +$72.2k, 2026-06-18 NQ +$71.7k; the 5 worst sum to $-349k). Excluding April 2025 (sensitivity, not a gate change): WF $14,582/wk, Sharpe 1.82, maxDD $519k; HOLD $23,006/wk, Sharpe 2.92.
**A4. Marginal Sharpe with both bases (B3_F19 added at equal risk; the sleeve's NQ leg is now counted in the NQ 50-contract cap, which the main block-(v) table did not do for 'MULTI' cells: dMaxDD +$61.6k there, +$26.2k here with KB+SM+PB):**
| base | window | marginal Sharpe | dMaxDD at 50-cap | ex-April-2025 marginal / dMaxDD |
|---|---|---|---|---|
| KB+SM+PB | WFPRE | +0.29 | 26.2k | - |
| KB+SM+PB | WF | +0.89 | 26.2k | +0.90 / 26.2k |
| KB+SM+PB | HOLD | +1.59 | -47.7k | +1.59 / -47.7k |
| KB+SM+EM | WFPRE | +0.22 | 37.8k | - |
| KB+SM+EM | WF | +0.70 | 37.8k | +0.72 / 37.8k |
| KB+SM+EM | HOLD | +1.22 | -5.7k | +1.22 / -5.7k |

Marginal Sharpe is positive on both bases in all windows (EM base smaller: +0.70 WF / +1.22 HOLD); the dMaxDD sign is positive in WF on both bases (the same 2024 effect) and negative in HOLD (KB+SM+PB -$47.7k; EM base -$5.7k). Excluding April 2025 changes nothing (it is outside the drawdown).
**A5. 50-cap concurrency (full sequence).** Equal-risk lots of the sleeve are NOT the 10.1 shown in the lots column of the leaderboard (that is the weight-averaged figure); per fully signalled day the sleeve is 5.0 NQ + 10.3 ES + 15.6 RTY contracts (spec section 2 corrected). NQ lots beside the stack, nominal: DS2 10/10/7 = 27 + DS3 trio (KB/SM/PB at the DS2+DS3 line, peak 23) + sleeve 5.0 = 55 > 50 when everything is at its equal-risk size: the sum of nominal peaks breaches the NQ cap by about 5 lots; at the interval-replay cap line (KB/SM/PB intervals, sleeve NQ leg included, DS2 not in the replay) the whole DS3+sleeve portfolio is scaled so the NQ peak is 50 (base line c = 42,287, with sleeve c = 38,797 for KB+SM+PB: trend books scaled down by 8%). ES (10.3) and RTY (15.6) are far below their own 50-contract caps. DS2 has no interval table, so DS2's own concurrency is nominal (27, an upper bound).
