# DS3 T-BRACKET-PM section D - Pyramiding / add to winners, risk held constant (D3PY, 2026-10-26T20:38Z)
Research only. No live recommendation. Tier-1 entries only (ST10, HM10 live; KB = TE7_kelt3m_n14_m1.0, SM = TE6_st10m_n7_m3.0, EM = TE7_emax5m_f30_s50), per the user's priority order; T-PULLBACK / T-TREND / other registry entries were NOT run (paused by the user).

## Verdict line
**Pyramiding risk-constant: 0 PASS, 0 CANDIDATE, 215 DEAD of 215 scored (5 entries x 43 cells; 20 of the 215 are duplicates-by-construction).** Paired delta (identical entries, WF, pts of the 10-lot base position, $200/pt): risk-constant D1 N30/50%/1 add/original target: ST -1.27 [-1.90, -0.68], HM -1.26 [-2.02, -0.50], KB -0.94 [-1.54, -0.30], SM -0.79 [-2.09, 0.49], EM -1.74 [-3.14, -0.42]; peak lots 15 per book (10 + the 50% add), 45 (median; range 40-55) with ST10+HM10+KB+SM concurrent and WT7 not modelled (+7 bound => 52 > 50 in the median cell: flagged); EM added as a fifth book reaches 50-65. The control D4 (original stop on everything = the earlier PY cell) reproduces the earlier result: pooled -0.71 pts/trade (earlier PY_t30_f50: -0.23, PY_t45_f50: -0.52, PY_t20_f50: +0.09). **No stop handling (risk-constant, breakeven+5, trail-to-last-add-10) rescues the add**: pooled over the five entries every add cell with the original target is negative (D1 -0.5 to -4.0, D2 -1.0 to -2.1, D3 -0.9 to -3.3 pts/trade) except the next-signal trigger with the original stop (D4_SG, +0.06, indistinguishable from 0). The only positive pooled cells are NOT pyramids: they are the trail-only controls (target dropped at +45 and a 30-pt trail, no add): D4_N45_f0_G3 pooled +1.02 pts/trade (holdout +1.56); the 50% add on top of that trail lowers it to +0.57. That exit shape belongs to sections A/B (hand-off to D3BA / D3NT), not to pyramiding. Best-of-43 null (random add timing after the trigger, per entry): the best cell beats the null max on every entry (it is a trail-shape effect, see below). Combined (section E) pyramiding contribution: none to carry. MDE: 1.28 pts/trade (ST), 1.30 (KB), 2.50 (SM), 2.58 (EM), 1.46 (HM): the null reads "an add that helps by more than ~1-3 pts/trade is not present"; the negatives of -1 to -4 pts/trade are many times the MDE.

## What was run, and the one thing that decides the reading (MAPPED screen vs direct L2)
* Method. 1-s path simulation (numba, `l2vast/ds3/code/py/py_kernel.py`) of the whole pyramided position, processing ALL signals in order with the one-open-position-per-book busy rule (a modified exit frees the book earlier/later, so extra and skipped trades appear; identity check: base series reproduced exactly for all five entries, max abs daily difference 0.0 vs DS2_daily pnl_ST/pnl_HM and te/direct_daily KB/SM/EM). Each leg is a row through the exact per-book lock engine (10 lots, locks as DS2: give-back 2R keep 50%, cap off, week floor 12R, per-book day -2R/+5R), commission $4.84/lot, S113 extra-lot charge on exits with more lots than the base. Base-trade main legs keep their DIRECT/P9 points (ST/HM corrected P9, KB/SM/EM T-ENTRY S10x1+XJ3); changed legs are MAPPED.
* Primary paired test = IDENTICAL ENTRIES (matched pairs; session-block bootstrap); the all-in paired delta (extras and skipped trades attributed to the base trade open at the time) is next to it, and the full-sequence weekly engine series (with extras, MAPPED) gives the weekly/maxDD columns. `weekly_noextra` in the rows drops the extra trades.
* **Two mappings are reported, and the verdict uses the conservative one.** The year x exit-type haircut of the T-ENTRY mapping credits a STOP exit with +4.0 pts (2025) / +4.2 (2026) over the natural path and charges a TARGET exit -4.2 / -4.3 (it is a property of the S10x1 slice brackets anchored at each fill, not of exit fills). Every pyramid stop (risk-constant, breakeven, trail-to-add, 30-pt trail) turns target exits into stop exits, so under the PLAIN mapping those cells receive an ~8-pt swing per converted trade. The direct L2 replay of the exits themselves (below) shows NO such bonus: stop-join exits are +0.4 to +0.5 pt WORSE than the stop level, base -60 stops included. The CONSERVATIVE mapping therefore gives modified stops no join bonus (-0.5 pt). PLAIN: 11 PASS / 52 CANDIDATE / 152 DEAD (upper bound, depends entirely on the +4 haircut; NOT registered). CONSERVATIVE: 0 PASS / 0 CANDIDATE / 215 DEAD (verdicts in `rows/DS3_TPYRAMID.json`; plain-mapping rows in `rows/DS3_TPYRAMID_plainmap.json`). Disclosure: the plain-mapping table was scored and read first (including HOLD); the switch to the conservative mapping was made because of the direct-replay evidence and can only lower results.
* Direct L2 replay (SO2 event standard; exec_engine_l2 on raw mbp-10, queue model, 5 ms latency; `py_direct.py`): add legs as true stop-entry orders (STP) at the trigger level and whole-position exits as stop-join (STPLMT: trigger at the stop, join the touch, 3 s then market) at the REAL lot count, plus the same exit at the base 10 lots and the base -60 stops (XB), placed at the start of the trigger second. SAMPLE: the first 8 trading days of 2023-09, 2024-04, 2024-11, 2025-10, 2026-04 (+2 days of 2025-04) = 8 cells x 5 entries of events (310k unique events deduplicated across cells/entries). exec_status = MAPPED_SCREEN + DIRECT_SAMPLE (not full-period direct; memory limited the replay to one 17-22 GB worker at a time, and a 22 GB worker was killed once by memguard).

|             |    n |   mean |   med |   p90 |   big2 |   fill |
|:------------|-----:|-------:|------:|------:|-------:|-------:|
| ('A', 5)    | 4118 |   0.73 |  0.35 |  1.5  |   0.07 |      1 |
| ('X', 15)   | 3182 |   0.46 |  0    |  1.75 |   0.08 |      1 |
| ('X', 20)   |  202 |   0.67 |  0    |  2.09 |   0.11 |      1 |
| ('X10', 10) | 3378 |   0.43 |  0    |  1.59 |   0.07 |      1 |
| ('XB', 10)  |  211 |   0.51 |  0    |  0    |   0.06 |      1 |

Reading (shortfall in pts vs the order level, positive = worse; day offset between the continuous 1-s series and the raw contract estimated per day): a 5-lot stop-entry add fills +0.73 pt worse than the trigger level on average (0.38 in 2023, 1.10 in 2026; median 0.35; 7% worse than 2 pts); the stop-join exit of the whole position (15 lots) is +0.46 (10 lots +0.43, base -60 stops XB +0.51): going from 10 to 15 lots through the join costs ~0.03 pt, far below the S113 market-sweep charge (which is therefore conservative here, as it should be for a join model). Fill rate 100%. The assumed MAPPED add entry cost was 0.5 pt (measured 0.73: -0.2 pt per add, about -0.13 pt/trade at 68% add share, not applied; it only lowers the results) and the assumed modified-stop total -0.5 pt (measured exit shortfall +0.45 plus the entry-side part of the haircut: consistent).

## Pooled result by cell (5 entries pooled, matched pairs, CONSERVATIVE mapping), all 43 cells
| cell | pooled matched Δ pts/trade (5 entries, n-weighted) | PRE Δ | HOLD Δ | all-in Δ | Σ WF Δ$/wk over 5 entries | entries with Δ>0 | share adding |
|--|--|--|--|--|--|--|--|
| D4_N45_f0_m1_s30_G3 | 1.02 | 0.74 | 1.56 | 1.02 | 14k | 5/5 | 0.57 |
| D1_N45_f50_m1_s30_G3 | 0.57 | 0.45 | 1.11 | 0.63 | 6k | 5/5 | 0.57 |
| D4_N30_f0_m1_s30_G3 | 0.26 | -0.39 | 0.78 | 0.59 | 8k | 4/5 | 0.68 |
| D4_SG_f50_m1_s30_G1 | 0.06 | 0.23 | -0.01 | 0.09 | -11k | 4/5 | 0.32 |
| D4_PB_f50_m1_s30_G1 | -0.23 | 0.29 | -0.44 | -0.11 | -9k | 1/5 | 0.75 |
| D4_N15_f50_m1_s30_G1 | -0.23 | 0.19 | -0.36 | -0.11 | -15k | 1/5 | 0.81 |
| D2_N30_f50_m1_s30_G3 | -0.27 | -1.04 | 0.25 | 0.02 | -12k | 0/5 | 0.68 |
| D3_N30_f50_m1_s30_G3 | -0.30 | -0.90 | 0.28 | -0.03 | -11k | 1/5 | 0.68 |
| D1_N30_f50_m1_s30_G3 | -0.30 | -0.90 | 0.28 | -0.03 | -11k | 1/5 | 0.68 |
| D1_SG_f50_m1_s30_G1 | -0.49 | -0.28 | -0.34 | -0.24 | -14k | 1/5 | 0.32 |
| D1_N30_f50_m2_s15_G3 | -0.52 | -1.07 | 0.15 | -0.15 | -14k | 1/5 | 0.68 |
| D1_SG_f50_m1_s30_G3 | -0.56 | -0.67 | -0.42 | -0.76 | -23k | 0/5 | 0.34 |
| D4_N30_f50_m1_s30_G1 | -0.71 | -0.38 | -0.88 | -0.65 | -13k | 0/5 | 0.68 |
| D4_N15_f0_m1_s30_G3 | -0.72 | -1.53 | -0.25 | -0.86 | -30k | 0/5 | 0.81 |
| D1_N30_f50_m1_s30_G2 | -0.84 | -1.16 | -0.82 | -1.01 | -22k | 0/5 | 0.68 |
| D1_N30_f50_m1_s30_G4 | -0.85 | -1.14 | -0.83 | -1.24 | -24k | 0/5 | 0.68 |
| D1_N45_f50_m1_s30_G1 | -0.89 | -1.00 | -0.86 | -1.00 | -20k | 0/5 | 0.57 |
| D3_SG_f50_m1_s30_G1 | -0.94 | -0.84 | -0.60 | -1.07 | -36k | 1/5 | 0.34 |
| D4_N45_f50_m1_s30_G1 | -0.95 | -0.66 | -1.22 | -0.97 | -23k | 0/5 | 0.57 |
| D2_SG_f50_m1_s30_G1 | -0.99 | -1.18 | -0.57 | -1.11 | -38k | 0/5 | 0.36 |
| D1_N30_f100_m1_s30_G3 | -1.04 | -1.58 | -0.41 | -0.86 | -24k | 1/5 | 0.68 |
| D1_PB_f50_m1_s30_G3 | -1.07 | -1.86 | -0.58 | -1.42 | -44k | 0/5 | 0.75 |
| D1_N30_f50_m3_s15_G1 | -1.17 | -1.40 | -1.04 | -1.02 | -18k | 0/5 | 0.68 |
| D1_N30_f50_m1_s30_G1 | -1.17 | -1.40 | -1.04 | -1.02 | -18k | 0/5 | 0.68 |
| D1_N30_f50_m2_s15_G1 | -1.17 | -1.40 | -1.04 | -1.02 | -18k | 0/5 | 0.68 |
| D2_N30_f50_m2_s15_G1 | -1.33 | -1.89 | -1.28 | -1.47 | -37k | 0/5 | 0.68 |
| D2_N30_f50_m1_s30_G1 | -1.33 | -1.89 | -1.28 | -1.47 | -37k | 0/5 | 0.68 |
| D1_N15_f50_m1_s30_G3 | -1.36 | -2.06 | -0.81 | -1.66 | -44k | 0/5 | 0.81 |
| D1_PB_f50_m1_s30_G1 | -1.42 | -1.39 | -1.34 | -1.41 | -26k | 0/5 | 0.75 |
| D2_N20_f50_m1_s30_G1 | -1.44 | -2.17 | -0.98 | -1.56 | -42k | 0/5 | 0.76 |
| D3_N30_f50_m2_s15_G1 | -1.56 | -2.01 | -1.84 | -2.08 | -39k | 0/5 | 0.68 |
| D3_N30_f50_m1_s30_G1 | -1.56 | -2.01 | -1.84 | -2.08 | -39k | 0/5 | 0.68 |
| D2_PB_f50_m1_s30_G1 | -1.69 | -2.83 | -1.30 | -2.18 | -51k | 0/5 | 0.75 |
| D1_N15_f50_m1_s30_G1 | -1.85 | -2.17 | -1.72 | -1.96 | -28k | 0/5 | 0.81 |
| D2_N15_f50_m2_s15_G1 | -1.96 | -2.65 | -1.71 | -2.49 | -67k | 0/5 | 0.81 |
| D3_PB_f50_m1_s30_G1 | -2.09 | -2.72 | -2.22 | -2.97 | -57k | 0/5 | 0.75 |
| D2_N30_f100_m1_s30_G1 | -2.10 | -2.45 | -2.16 | -2.45 | -64k | 0/5 | 0.68 |
| D3_N15_f50_m1_s30_G1 | -2.50 | -3.03 | -2.71 | -3.32 | -64k | 0/5 | 0.81 |
| D1_N30_f100_m1_s30_G1 | -2.50 | -2.91 | -2.85 | -3.24 | -53k | 0/5 | 0.68 |
| D3_N30_f100_m1_s30_G1 | -2.73 | -3.08 | -3.25 | -3.54 | -57k | 0/5 | 0.68 |
| D1_N15_f50_m2_s15_G1 | -2.90 | -3.28 | -3.21 | -3.34 | -46k | 0/5 | 0.81 |
| D3_N15_f50_m2_s15_G1 | -3.25 | -3.74 | -3.40 | -4.51 | -92k | 0/5 | 0.81 |
| D1_N15_f50_m3_s15_G1 | -4.03 | -4.51 | -4.39 | -4.92 | -67k | 0/5 | 0.81 |

## Same, PLAIN mapping (upper bound; the +4 stop haircut applies to every changed stop)
| cell | pooled matched Δ pts/trade (5 entries, n-weighted) | PRE Δ | HOLD Δ | all-in Δ | Σ WF Δ$/wk over 5 entries | entries with Δ>0 | share adding |
|--|--|--|--|--|--|--|--|
| D1_N30_f100_m1_s30_G3 | 4.20 | 2.21 | 5.91 | 5.20 | 77k | 5/5 | 0.68 |
| D1_N30_f50_m2_s15_G3 | 3.89 | 2.12 | 5.47 | 4.95 | 83k | 5/5 | 0.68 |
| D1_N45_f50_m1_s30_G3 | 3.89 | 2.84 | 5.12 | 4.06 | 69k | 5/5 | 0.57 |
| D2_N30_f50_m1_s30_G3 | 3.66 | 1.80 | 4.99 | 4.66 | 86k | 5/5 | 0.68 |
| D3_N30_f50_m1_s30_G3 | 3.63 | 1.95 | 5.02 | 4.52 | 75k | 5/5 | 0.68 |
| D1_N30_f50_m1_s30_G3 | 3.63 | 1.95 | 5.02 | 4.52 | 75k | 5/5 | 0.68 |
| D1_N15_f50_m1_s30_G3 | 3.34 | 1.32 | 4.86 | 4.62 | 76k | 5/5 | 0.81 |
| D1_PB_f50_m1_s30_G3 | 3.27 | 1.25 | 4.66 | 4.01 | 68k | 5/5 | 0.75 |
| D4_N45_f0_m1_s30_G3 | 3.23 | 2.33 | 4.23 | 3.30 | 59k | 5/5 | 0.57 |
| D4_N30_f0_m1_s30_G3 | 2.88 | 1.50 | 3.94 | 3.62 | 72k | 5/5 | 0.68 |
| D2_N15_f50_m2_s15_G1 | 2.63 | 0.62 | 3.84 | 4.27 | 105k | 5/5 | 0.81 |
| D4_N15_f0_m1_s30_G3 | 2.42 | 0.73 | 3.53 | 3.33 | 71k | 5/5 | 0.81 |
| D2_N20_f50_m1_s30_G1 | 2.21 | 0.47 | 3.43 | 3.35 | 81k | 5/5 | 0.76 |
| D2_PB_f50_m1_s30_G1 | 1.86 | -0.26 | 2.99 | 2.59 | 65k | 5/5 | 0.75 |
| D2_N30_f100_m1_s30_G1 | 1.85 | 0.38 | 2.63 | 2.34 | 45k | 5/5 | 0.68 |
| D1_SG_f50_m1_s30_G3 | 1.48 | 0.54 | 1.38 | 1.46 | 45k | 3/5 | 0.34 |
| D2_N30_f50_m1_s30_G1 | 1.31 | 0.02 | 1.92 | 1.70 | 34k | 5/5 | 0.68 |
| D2_N30_f50_m2_s15_G1 | 1.31 | 0.02 | 1.92 | 1.70 | 34k | 5/5 | 0.68 |
| D2_SG_f50_m1_s30_G1 | 0.72 | -0.17 | 0.92 | 1.09 | 44k | 3/5 | 0.36 |
| D1_N30_f50_m1_s30_G2 | 0.66 | -0.07 | 0.99 | 0.49 | -1k | 4/5 | 0.68 |

## Attribution: what drives the number
* Stop handling (D1 vs D2 vs D3 vs D4), original target, N30/50%/1 add, pooled: D4 (unchanged stop) -0.71, D1 -1.17, D2 -1.33, D3 -1.56. Moving the stop after the add does not help: a protected add converts some winners into small losers (ST win rate 0.517 -> 0.496 in D1_N30_f50_G1) and the stop moves do not repay it in the paired mean.
* Trigger (D1, G1, 50%): +15 -1.85, +30 -1.17, +45 -0.89, pullback-resume -1.42, next signal -0.49: the later and rarer the add, the less it costs; none is positive.
* Size: 100% adds are worse than 50% (D1 -2.50 vs -1.17); more adds are worse (N15 with 2 / 3 adds: -2.90 / -4.03).
* Target handling (D1 N30): original -1.17, re-set to avg+60 -0.84, per-leg +60 -0.85, no target + 30-pt trail -0.30. Dropping the target is the only thing that moves the number, and it works without the add (trail-only controls: +45 trigger +1.02, +30 +0.26, +15 -0.72 pooled), i.e. the add subtracts 0.4-0.6 pt from the trail shape.
* Added legs alone lose money in 165 of the 175 add cells (column 'added-leg P&L'; the 10 positive ones are next-signal (SG) cells and a few SM cells, +$5k to +$210k over 3.7 years): e.g. D1_N30_f50_G1 ST -$1.62M over 6,228 adds (unlocked, 3.7 yr) = -$261 per add at 5 lots.

## ST (ST10, live): top 6 by matched paired delta + the four N30/50%/1-add/original-target stop-handling cells (CONSERVATIVE mapping; all 43 cells are in rows/DS3_TPYRAMID.json)
| cell | paired matched pts/trade [CI] | MDE | all-in Δ | hold Δ (matched) | 2023-04..24-01 Δ (all-in) | placebo rank | nb agree | WF Δ$/wk (base->cell) | WF wk SD cell/base | maxDD cell/base (ALL) | worst wk cell/base | 2x Δ$/wk | trades/wk | share add | added-leg P&L $ | win base->cell | lots/trade | own lots avg/peak | DS2+DS3 peak (no WT7) | $/wk at equal risk vs base | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| D4_N45_f0_m1_s30_G3 | 0.95 [0.24, 1.62] | 0.99 | 0.60 | 1.32 | -0.14 | 1.00 | False | 2k (15k->16k) | 58k/57k | 421k/263k | -115k/-91k | 7k | 29.0 | 0.56 | 0k | 0.517->0.494 | 10.0 | 10.0/10 | 40 | 15940 | DEAD |
| D4_N30_f0_m1_s30_G3 | 0.53 [-0.41, 1.46] | 1.34 | 0.69 | 0.90 | -1.93 | 1.00 | False | 2k (15k->16k) | 58k/57k | 511k/263k | -144k/-91k | 3k | 38.1 | 0.67 | 0k | 0.517->0.538 | 10.0 | 10.0/10 | 40 | 15909 | DEAD |
| D1_N45_f50_m1_s30_G3 | 0.34 [-0.52, 1.16] | 1.20 | -0.02 | 0.56 | 0.04 | 1.00 | False | -1k (15k->13k) | 59k/57k | 419k/263k | -119k/-91k | -2k | 26.6 | 0.56 | -708k | 0.517->0.480 | 12.8 | 10.7/15 | 45 | 12728 | DEAD |
| D2_N30_f50_m1_s30_G3 | -0.01 [-0.98, 1.04] | 1.44 | -0.16 | 0.48 | -1.83 | 1.00 | True | -6k (15k->8k) | 64k/57k | 494k/263k | -144k/-91k | -9k | 35.3 | 0.67 | -1114k | 0.517->0.538 | 13.4 | 10.9/15 | 45 | 7587 | DEAD |
| D4_SG_f50_m1_s30_G1 | -0.12 [-0.52, 0.28] | 0.56 | -0.12 | -0.34 | -0.46 | 1.00 | True | -5k (15k->9k) | 67k/57k | 446k/263k | -144k/-91k | -6k | 21.3 | 0.44 | -177k | 0.517->0.515 | 12.2 | 12.3/15 | 45 | 7729 | DEAD |
| D1_N30_f50_m1_s30_G3 | -0.14 [-1.21, 0.93] | 1.54 | -0.18 | 0.23 | -2.59 | 1.00 | True | -3k (15k->11k) | 61k/57k | 539k/263k | -133k/-91k | -5k | 31.5 | 0.67 | -1156k | 0.517->0.457 | 13.4 | 11.2/15 | 45 | 10431 | DEAD |
| D4_N30_f50_m1_s30_G1 | -1.00 [-1.43, -0.52] | 0.65 | -1.00 | -1.12 | -0.69 | 1.00 | True | -6k (15k->9k) | 65k/57k | 476k/263k | -144k/-91k | -9k | 20.9 | 0.68 | -1455k | 0.517->0.511 | 13.4 | 12.3/15 | 45 | 7680 | DEAD |
| D3_N30_f50_m1_s30_G1 | -1.09 [-1.82, -0.32] | 1.05 | -1.56 | -0.76 | -0.10 | 1.00 | True | -10k (15k->5k) | 55k/57k | 383k/263k | -131k/-91k | -18k | 27.9 | 0.68 | -1840k | 0.517->0.470 | 13.4 | 11.5/15 | 45 | 5092 | DEAD |
| D2_N30_f50_m1_s30_G1 | -1.10 [-1.97, -0.26] | 1.28 | -1.45 | -0.90 | -1.85 | 1.00 | True | -13k (15k->1k) | 60k/57k | 754k/263k | -121k/-91k | -22k | 38.2 | 0.67 | -1993k | 0.517->0.552 | 13.4 | 10.7/15 | 45 | 984 | DEAD |
| D1_N30_f50_m1_s30_G1 | -1.27 [-1.90, -0.68] | 0.91 | -1.39 | -0.82 | -2.25 | 1.00 | True | -7k (15k->7k) | 57k/57k | 405k/263k | -132k/-91k | -17k | 23.3 | 0.68 | -1624k | 0.517->0.496 | 13.4 | 11.9/15 | 45 | 7438 | DEAD |

## HM (HM10, live): top 6 by matched paired delta + the four N30/50%/1-add/original-target stop-handling cells (CONSERVATIVE mapping; all 43 cells are in rows/DS3_TPYRAMID.json)
| cell | paired matched pts/trade [CI] | MDE | all-in Δ | hold Δ (matched) | 2023-04..24-01 Δ (all-in) | placebo rank | nb agree | WF Δ$/wk (base->cell) | WF wk SD cell/base | maxDD cell/base (ALL) | worst wk cell/base | 2x Δ$/wk | trades/wk | share add | added-leg P&L $ | win base->cell | lots/trade | own lots avg/peak | DS2+DS3 peak (no WT7) | $/wk at equal risk vs base | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| D4_N45_f0_m1_s30_G3 | 0.62 [-0.16, 1.47] | 1.19 | 0.53 | 0.75 | 0.11 | 1.00 | False | 4k (10k->13k) | 54k/53k | 265k/284k | -123k/-108k | 8k | 25.0 | 0.57 | 0k | 0.520->0.493 | 10.0 | 10.0/10 | 40 | 13227 | DEAD |
| D4_SG_f50_m1_s30_G1 | 0.16 [-0.26, 0.61] | 0.64 | 0.16 | 0.16 | -0.65 | 1.00 | False | -5k (10k->5k) | 59k/53k | 452k/284k | -144k/-108k | -7k | 20.4 | 0.44 | 102k | 0.520->0.517 | 12.2 | 12.3/15 | 45 | 4208 | DEAD |
| D1_N45_f50_m1_s30_G3 | 0.10 [-0.90, 1.10] | 1.46 | 0.00 | 0.18 | 0.07 | 1.00 | False | 4k (10k->14k) | 55k/53k | 226k/284k | -119k/-108k | 4k | 23.3 | 0.57 | -464k | 0.520->0.477 | 12.8 | 10.7/15 | 45 | 13583 | DEAD |
| D4_PB_f50_m1_s30_G1 | -0.11 [-0.72, 0.49] | 0.85 | -0.11 | -0.15 | -1.05 | 1.00 | True | 1k (10k->11k) | 61k/53k | 408k/284k | -128k/-108k | -5k | 19.0 | 0.75 | -266k | 0.520->0.516 | 13.8 | 13.1/15 | 45 | 9293 | DEAD |
| D4_N15_f50_m1_s30_G1 | -0.18 [-0.81, 0.43] | 0.90 | -0.18 | -0.13 | -0.83 | 1.00 | True | -6k (10k->4k) | 62k/53k | 515k/284k | -144k/-108k | -9k | 18.3 | 0.82 | -298k | 0.520->0.517 | 14.1 | 13.7/15 | 45 | 3650 | DEAD |
| D1_SG_f50_m1_s30_G1 | -0.33 [-0.90, 0.28] | 0.85 | -0.17 | -0.66 | 0.20 | 1.00 | True | -3k (10k->7k) | 55k/53k | 375k/284k | -139k/-108k | -9k | 22.3 | 0.45 | -57k | 0.520->0.499 | 12.2 | 12.0/15 | 45 | 7086 | DEAD |
| D4_N30_f50_m1_s30_G1 | -0.53 [-1.08, 0.01] | 0.76 | -0.53 | -0.49 | -0.84 | 1.00 | False | -2k (10k->8k) | 57k/53k | 338k/284k | -143k/-108k | -9k | 20.6 | 0.68 | -654k | 0.520->0.515 | 13.4 | 12.4/15 | 45 | 7498 | DEAD |
| D1_N30_f50_m1_s30_G1 | -1.26 [-2.02, -0.50] | 1.09 | -1.32 | -1.30 | -1.22 | 1.00 | True | -4k (10k->6k) | 56k/53k | 478k/284k | -145k/-108k | -11k | 21.9 | 0.67 | -1005k | 0.520->0.491 | 13.4 | 12.0/15 | 45 | 5624 | DEAD |
| D2_N30_f50_m1_s30_G1 | -1.53 [-2.52, -0.53] | 1.46 | -1.20 | -1.51 | -3.40 | 1.00 | True | -5k (10k->5k) | 54k/53k | 619k/284k | -117k/-108k | -12k | 33.4 | 0.68 | -1344k | 0.520->0.569 | 13.4 | 10.7/15 | 45 | 4752 | DEAD |
| D3_N30_f50_m1_s30_G1 | -2.11 [-3.05, -1.26] | 1.28 | -2.29 | -2.13 | -0.89 | 1.00 | True | -10k (10k->0k) | 53k/53k | 774k/284k | -107k/-108k | -16k | 25.0 | 0.67 | -1361k | 0.520->0.447 | 13.4 | 11.5/15 | 45 | 26 | DEAD |

## KB (TE7_kelt3m_n14_m1.0): top 6 by matched paired delta + the four N30/50%/1-add/original-target stop-handling cells (CONSERVATIVE mapping; all 43 cells are in rows/DS3_TPYRAMID.json)
| cell | paired matched pts/trade [CI] | MDE | all-in Δ | hold Δ (matched) | 2023-04..24-01 Δ (all-in) | placebo rank | nb agree | WF Δ$/wk (base->cell) | WF wk SD cell/base | maxDD cell/base (ALL) | worst wk cell/base | 2x Δ$/wk | trades/wk | share add | added-leg P&L $ | win base->cell | lots/trade | own lots avg/peak | DS2+DS3 peak (no WT7) | $/wk at equal risk vs base | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| D4_N45_f0_m1_s30_G3 | 0.99 [0.29, 1.77] | 1.06 | 0.36 | 1.25 | 0.42 | 1.00 | False | -1k (17k->15k) | 58k/59k | 342k/337k | -145k/-124k | 4k | 27.9 | 0.56 | 0k | 0.509->0.480 | 10.0 | 10.0/10 | 40 | 15984 | DEAD |
| D1_N45_f50_m1_s30_G3 | 0.62 [-0.26, 1.58] | 1.30 | -0.14 | 0.77 | 0.05 | 1.00 | False | -6k (17k->10k) | 60k/59k | 328k/337k | -145k/-124k | -2k | 25.2 | 0.56 | -672k | 0.509->0.467 | 12.8 | 10.8/15 | 45 | 10358 | DEAD |
| D4_N30_f0_m1_s30_G3 | 0.40 [-0.55, 1.32] | 1.37 | 0.48 | 0.80 | 1.92 | 1.00 | False | -1k (17k->16k) | 55k/59k | 286k/337k | -108k/-124k | 5k | 37.0 | 0.67 | 0k | 0.509->0.527 | 10.0 | 10.0/10 | 40 | 17612 | DEAD |
| D4_SG_f50_m1_s30_G1 | 0.13 [-0.31, 0.55] | 0.62 | 0.13 | -0.13 | -0.53 | 1.00 | False | -1k (17k->16k) | 67k/59k | 409k/337k | -125k/-124k | -2k | 20.1 | 0.56 | 210k | 0.509->0.508 | 12.8 | 13.0/15 | 45 | 14393 | DEAD |
| D1_N30_f50_m1_s30_G3 | -0.06 [-1.14, 1.05] | 1.56 | -0.23 | 0.31 | 1.86 | 1.00 | True | -6k (17k->11k) | 59k/59k | 356k/337k | -139k/-124k | -4k | 30.5 | 0.67 | -903k | 0.509->0.447 | 13.3 | 11.2/15 | 45 | 10908 | DEAD |
| D3_N30_f50_m1_s30_G3 | -0.06 [-1.14, 1.05] | 1.56 | -0.23 | 0.31 | 1.86 | 1.00 | True | -6k (17k->11k) | 59k/59k | 356k/337k | -139k/-124k | -4k | 30.5 | 0.67 | -903k | 0.509->0.447 | 13.3 | 11.2/15 | 45 | 10908 | DEAD |
| D4_N30_f50_m1_s30_G1 | -0.65 [-1.14, -0.21] | 0.66 | -0.65 | -0.88 | -1.72 | 1.00 | False | -1k (17k->15k) | 65k/59k | 564k/337k | -144k/-124k | -4k | 21.8 | 0.67 | -1275k | 0.509->0.505 | 13.4 | 12.3/15 | 45 | 14149 | DEAD |
| D1_N30_f50_m1_s30_G1 | -0.94 [-1.54, -0.30] | 0.89 | -1.12 | -0.81 | -0.83 | 1.00 | True | -3k (17k->14k) | 62k/59k | 430k/337k | -126k/-124k | -11k | 24.5 | 0.67 | -1568k | 0.509->0.490 | 13.4 | 12.0/15 | 45 | 13524 | DEAD |
| D2_N30_f50_m1_s30_G1 | -0.99 [-1.87, -0.11] | 1.27 | -0.90 | -0.75 | 0.80 | 1.00 | True | -9k (17k->8k) | 56k/59k | 413k/337k | -144k/-124k | -16k | 39.0 | 0.67 | -1647k | 0.509->0.541 | 13.3 | 10.7/15 | 45 | 8463 | DEAD |
| D3_N30_f50_m1_s30_G1 | -1.03 [-1.75, -0.26] | 1.07 | -1.58 | -0.60 | 2.58 | 1.00 | True | -7k (17k->10k) | 57k/59k | 405k/337k | -114k/-124k | -17k | 27.5 | 0.67 | -1504k | 0.509->0.460 | 13.3 | 11.5/15 | 45 | 10066 | DEAD |

## SM (TE6_st10m_n7_m3.0): top 6 by matched paired delta + the four N30/50%/1-add/original-target stop-handling cells (CONSERVATIVE mapping; all 43 cells are in rows/DS3_TPYRAMID.json)
| cell | paired matched pts/trade [CI] | MDE | all-in Δ | hold Δ (matched) | 2023-04..24-01 Δ (all-in) | placebo rank | nb agree | WF Δ$/wk (base->cell) | WF wk SD cell/base | maxDD cell/base (ALL) | worst wk cell/base | 2x Δ$/wk | trades/wk | share add | added-leg P&L $ | win base->cell | lots/trade | own lots avg/peak | DS2+DS3 peak (no WT7) | $/wk at equal risk vs base | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| D4_N45_f0_m1_s30_G3 | 1.70 [0.17, 3.31] | 2.21 | 1.38 | 3.09 | 0.26 | 1.00 | False | 4k (9k->13k) | 37k/36k | 190k/197k | -79k/-99k | 7k | 12.7 | 0.58 | 0k | 0.529->0.563 | 10.0 | 10.0/10 | 40 | 12248 | DEAD |
| D1_N45_f50_m1_s30_G3 | 1.58 [-0.31, 3.67] | 2.80 | 1.21 | 3.13 | -0.10 | 1.00 | False | 3k (9k->12k) | 41k/36k | 233k/197k | -84k/-99k | 4k | 12.4 | 0.58 | -29k | 0.529->0.541 | 12.9 | 10.7/15 | 45 | 10356 | DEAD |
| D1_N30_f50_m2_s15_G3 | 0.69 [-1.64, 3.07] | 3.40 | 0.44 | 2.35 | 1.93 | 1.00 | False | -2k (9k->7k) | 38k/36k | 267k/197k | -86k/-99k | -1k | 13.0 | 0.68 | 124k | 0.529->0.486 | 14.7 | 11.6/20 | 50 | 6548 | DEAD |
| D4_PB_f50_m1_s30_G1 | 0.61 [-0.47, 1.53] | 1.42 | 0.61 | 0.15 | -1.08 | 1.00 | False | 1k (9k->10k) | 47k/36k | 300k/197k | -127k/-99k | -1k | 11.2 | 0.75 | 80k | 0.529->0.520 | 13.8 | 13.1/15 | 45 | 7451 | DEAD |
| D4_N15_f50_m1_s30_G1 | 0.61 [-0.59, 1.69] | 1.56 | 0.61 | 0.24 | -0.74 | 1.00 | False | 1k (9k->9k) | 48k/36k | 277k/197k | -131k/-99k | -1k | 11.0 | 0.81 | 126k | 0.529->0.521 | 14.1 | 13.7/15 | 45 | 6996 | DEAD |
| D1_N30_f50_m1_s30_G3 | 0.59 [-1.46, 2.68] | 2.99 | 0.30 | 2.13 | 1.32 | 1.00 | False | -1k (9k->8k) | 36k/36k | 264k/197k | -83k/-99k | -0k | 13.2 | 0.68 | -19k | 0.529->0.488 | 13.4 | 11.2/15 | 45 | 7801 | DEAD |
| D4_N30_f50_m1_s30_G1 | -0.23 [-1.14, 0.65] | 1.25 | -0.23 | -0.57 | -1.98 | 1.00 | False | -2k (9k->7k) | 45k/36k | 306k/197k | -97k/-99k | -4k | 11.5 | 0.69 | -294k | 0.529->0.521 | 13.4 | 12.4/15 | 45 | 5608 | DEAD |
| D1_N30_f50_m1_s30_G1 | -0.79 [-2.09, 0.49] | 1.88 | -0.38 | -0.67 | -0.18 | 1.00 | False | -2k (9k->6k) | 38k/36k | 262k/197k | -85k/-99k | -6k | 11.8 | 0.69 | -253k | 0.529->0.495 | 13.4 | 12.1/15 | 45 | 5886 | DEAD |
| D2_N30_f50_m1_s30_G1 | -1.94 [-3.44, -0.33] | 2.35 | -2.20 | -1.29 | -1.58 | 1.00 | True | -6k (9k->3k) | 32k/36k | 268k/197k | -93k/-99k | -8k | 13.6 | 0.68 | -454k | 0.529->0.622 | 13.4 | 10.7/15 | 45 | 2911 | DEAD |
| D3_N30_f50_m1_s30_G1 | -2.10 [-3.53, -0.53] | 2.11 | -2.42 | -2.19 | 0.53 | 1.00 | False | -6k (9k->2k) | 37k/36k | 302k/197k | -110k/-99k | -10k | 12.7 | 0.69 | -492k | 0.529->0.438 | 13.4 | 11.6/15 | 45 | 2365 | DEAD |

## EM (TE7_emax5m_f30_s50): top 6 by matched paired delta + the four N30/50%/1-add/original-target stop-handling cells (CONSERVATIVE mapping; all 43 cells are in rows/DS3_TPYRAMID.json)
| cell | paired matched pts/trade [CI] | MDE | all-in Δ | hold Δ (matched) | 2023-04..24-01 Δ (all-in) | placebo rank | nb agree | WF Δ$/wk (base->cell) | WF wk SD cell/base | maxDD cell/base (ALL) | worst wk cell/base | 2x Δ$/wk | trades/wk | share add | added-leg P&L $ | win base->cell | lots/trade | own lots avg/peak | DS2+DS3 peak (no WT7) | $/wk at equal risk vs base | verdict |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| D4_N45_f0_m1_s30_G3 | 1.67 [0.13, 3.15] | 2.19 | 2.22 | 1.37 | -0.44 | 1.00 | False | 6k (7k->13k) | 38k/34k | 218k/198k | -93k/-74k | 9k | 12.2 | 0.58 | 0k | 0.523->0.564 | 10.0 | 10.0/10 | 50 | 11930 | DEAD |
| D1_N45_f50_m1_s30_G3 | 1.38 [-0.57, 3.29] | 2.78 | 2.08 | 0.89 | -1.15 | 1.00 | False | 6k (7k->13k) | 41k/34k | 298k/198k | -99k/-74k | 8k | 11.8 | 0.58 | -90k | 0.523->0.545 | 12.9 | 10.7/15 | 55 | 10931 | DEAD |
| D4_N30_f0_m1_s30_G3 | 0.19 [-1.70, 2.00] | 2.64 | 1.00 | 0.37 | -2.20 | 1.00 | False | 3k (7k->10k) | 33k/34k | 233k/198k | -93k/-74k | 5k | 13.2 | 0.69 | 0k | 0.523->0.618 | 10.0 | 10.0/10 | 50 | 10028 | DEAD |
| D4_SG_f50_m1_s30_G1 | 0.17 [-0.15, 0.46] | 0.44 | 0.17 | 0.11 | -0.13 | 1.00 | False | 0k (7k->8k) | 36k/34k | 210k/198k | -74k/-74k | -0k | 11.7 | 0.10 | 12k | 0.523->0.522 | 10.5 | 10.5/15 | 55 | 7214 | DEAD |
| D1_SG_f50_m1_s30_G1 | -0.05 [-0.53, 0.41] | 0.68 | 0.10 | 0.16 | -0.01 | 1.00 | True | 0k (7k->7k) | 35k/34k | 178k/198k | -74k/-74k | -1k | 11.8 | 0.10 | 5k | 0.523->0.514 | 10.5 | 10.4/15 | 55 | 7125 | DEAD |
| D3_SG_f50_m1_s30_G1 | -0.16 [-0.72, 0.42] | 0.80 | -0.46 | -0.29 | -0.34 | 1.00 | True | -1k (7k->6k) | 35k/34k | 181k/198k | -74k/-74k | -1k | 12.1 | 0.10 | -35k | 0.523->0.513 | 10.5 | 10.2/15 | 55 | 6182 | DEAD |
| D4_N30_f50_m1_s30_G1 | -0.83 [-1.73, 0.10] | 1.31 | -0.83 | -1.34 | -0.60 | 1.00 | False | -3k (7k->4k) | 42k/34k | 387k/198k | -119k/-74k | -4k | 11.2 | 0.69 | -364k | 0.523->0.515 | 13.4 | 12.3/15 | 55 | 3639 | DEAD |
| D1_N30_f50_m1_s30_G1 | -1.74 [-3.14, -0.42] | 1.99 | -0.90 | -1.60 | -1.11 | 1.00 | True | -2k (7k->5k) | 39k/34k | 284k/198k | -100k/-74k | -5k | 11.7 | 0.69 | -411k | 0.523->0.488 | 13.4 | 12.0/15 | 55 | 4295 | DEAD |
| D2_N30_f50_m1_s30_G1 | -2.24 [-4.13, -0.54] | 2.54 | -1.61 | -1.94 | -3.62 | 1.00 | True | -3k (7k->4k) | 30k/34k | 457k/198k | -97k/-74k | -5k | 13.3 | 0.69 | -586k | 0.523->0.627 | 13.4 | 10.7/15 | 55 | 4181 | DEAD |
| D3_N30_f50_m1_s30_G1 | -3.18 [-4.86, -1.66] | 2.30 | -2.56 | -3.53 | -1.84 | 1.00 | True | -6k (7k->1k) | 36k/34k | 432k/198k | -88k/-74k | -9k | 12.6 | 0.69 | -656k | 0.523->0.423 | 13.4 | 11.5/15 | 55 | 1190 | DEAD |

## Splits for the headline risk-constant cell (D1_N30_f50_m1_s30_G1), WF matched/all-in pts/trade by side, session, regime
| entry | long | short | ASIA | LONDON | NY | quiet | wide |
|--|--|--|--|--|--|--|--|
| ST10 | -1.44 | -1.34 | -1.28 | -1.06 | -1.62 | -1.00 | -1.68 |
| HM10 | -0.92 | -1.73 | -2.04 | -0.65 | -1.16 | -1.19 | -1.41 |
| KB | -0.62 | -1.64 | -0.44 | -0.12 | -2.06 | -1.00 | -1.21 |
| SM | 0.55 | -1.28 | 1.57 | -1.09 | -1.81 | 0.19 | -0.80 |
| EM | -1.22 | -0.61 | 0.37 | -2.15 | -1.18 | 0.17 | -1.69 |
(session rule: ASIA 18:00-03:00, LONDON 03:00-09:30, NY 09:30-18:00 ET as in the registry; quiet/wide = as-of trailing 390-bar mean range below/above the sample median. The same splits exist for every cell in the rows file.)

## Pre-registration, ledger, holdout, disclosures
* Prereg groups (sha256 in autopilot/DECISIONS.md before scoring): PY_ST10 b5672829..., PY_HM10 d31d2d72..., PY_KB e40d9786..., PY_SM 90c425f6..., PY_EM 98a8d30d... (30 cells each; mechanism, predicted effect, MDE, object type, nearest scored cell per cell: l2vast/ds3/prereg/PY_<entry>_prereg.md) and the amendment + group B (13 cells each: replacements for four degenerate cells, trail-only controls, G3 widening): PY_<entry>_B_prereg.md. Ledger: 5 x (31 + 13) = 220 cells appended to l2vast/struct48/ledger/trials.jsonl (tracks DS3_PY_<entry> and DS3_PY_<entry>_B). The conservative re-score re-uses the same 43 cells (no new cells).
* Stratification: groups A = 11 risk-constant, 7 breakeven, 7 trail-to-add, 5 unchanged cells (stop handling x trigger x size x adds x target; the full grid is 6 x 2 x 3 x 2 x 4 x 4 = 1,152 per entry, so each entry sees 43 of 1,152 declared cells). Best-of-N null: random add timing among the seconds at/after the first trigger touch with net >= the trigger level, same add count, 40 replicates per cell; the maximum over the 43 cells per replicate gives the null for the best cell (rows: best_of_N).
* Disclosures. (1) A D4_N30 pilot (WF-PRE SD sizing) and a plumbing smoke test of D1_N30_f50_m1_s30_G1 on ST10 printed all windows including HOLD before the prereg (HOLD +0.59 all-in under the first-pass engine). (2) The first screen of ST10 group A (WF-PRE) exposed four design flaws (degenerate m2/m3 cells, no busy rule, placebo not matched on net-positive state, no attribution control); fixed in the B amendment written before group B or any holdout. (3) The first full scoring used the plain mapping and its HOLD column was read before the conservative mapping was adopted. (4) Holdout (2025-07+) and the 2023-04..2024-01 span: one look per prereg group (10 logged looks, pre-holdout text autopilot/DS3_TPYRAMID_PREHOLD.md sha256 b5d8c779...). (5) Placebo definition changed between the plain run (random net-positive seconds) and the conservative run (net >= trigger level after first touch); the conservative run's placebo is the one used.
* Neighbours: same stop mode, one factor different (frozen in py_cells.nbrs); ALL must agree in sign; the only cells with a positive pooled mean (trail-only +45 / +30) fail it because their +15 neighbour is negative.

## Caveats
* The weekly/maxDD columns include EXTRA trades (signals the busy rule had skipped) priced on the MAPPED basis; `weekly_noextra` in the rows removes them. The exit shape changes trade count by up to +90% (KB D2 cells), so weekly deltas are partly a capacity effect; the paired matched column is the clean per-trade measure.
* The direct replay covers 8 days x 5 months of events (adds, whole-position exits, base stops) and calibrates execution costs; it is not a full-period replay of the pyramid P&L. A full direct replay of any cell would have been needed only for a PASS/CANDIDATE; there is none under the conservative mapping.
* WT7 has no interval table; combined-peak columns exclude it (+7 bound). Locks are applied per book; DS2+DS3 are not run through a joint 50-cap trim here.
* P9 haircut structure (stop +4 / target -4 in 2025-26): origin not an exit-fill effect (XB replay), not resolved here; it is the reason the plain mapping is an upper bound and is flagged for D3BL/section A, whose bracket-shape cells face the same issue.

## Hand-offs
* Trail-only exit (drop the target after +30/+45, trail 30 pts) is positive in the matched pairs on SM, EM, KB, ST (conservative mapping, WF) - an exit-shape result for sections A/B (D3BA/D3NT) and for G4 combinations; it should be direct-replayed there.
* Equal-risk fields (user addendum) are in every row under cell['equal_risk'] (pnl_wk_equal_lots, pnl_wk_equal_risk [vs ST10's weekly SD, equal_risk.py], lots_equal_risk, capacity_lots_zero_mean, ds3_marginal_sharpe [only computed for PASS/CANDIDATE: none], plus pnl_wk_equal_risk_vs_base = the cell scaled to its base entry's weekly SD). No cell is DEAD solely for earning less than ST at equal lots: every DEAD above fails on the paired mean/CI/holdout against its own base.

## Files
Report autopilot/DS3_TPYRAMID.md; rows l2vast/ds3/rows/DS3_TPYRAMID.json (conservative, 215 cells, verdicts) and DS3_TPYRAMID_plainmap.json (upper bound); prereg l2vast/ds3/prereg/PY_*; code l2vast/ds3/code/py/ (py_kernel, py_lib, py_cells, py_score, py_run, py_final, py_verdict, py_direct, py_calib2, py_md); results l2vast/ds3/out/py/ (per-entry res pickles, series, direct_events_all.parquet); direct fills /mnt/l2/l2vast/ds3_py/.
