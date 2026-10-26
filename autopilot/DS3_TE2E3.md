# DS3_TE2E3 - addendum 2 E2 (instruments NT8 can chart) and E3 (per-instrument cost). D3INS, 2026-10-26

**Verdict: 0 PASS, 2 CANDIDATE (both GC 15-min, post-hoc, weak), 291 DEAD of 293 cells.** The 2 CANDIDATEs: TE2_GC_KEL_k15 and TE2_GC_VWAP_k15. No instrument other than gold shows anything; every FX, rates, energy, equity-index (ES/RTY/YM/NKD) and crypto family is negative after per-instrument costs, and the 15 pooled non-NQ family baskets (MDE about $3-4k/wk) are all strongly negative (-$15k to -$101k/wk). Pool contribution: 0 PASS; the 2 CANDIDATEs are registered (paper_all ds3_TE2_GC_KEL_k15, ds3_TE2_GC_VWAP_k15) and their daily series are in l2vast/ds3/out/SERIES/ for D3L; I do not recommend them for the pool (reasons below). Nothing here is a live recommendation.

Deliverables: this report; l2vast/ds3/out/INSTRUMENT_INVENTORY.md; l2vast/ds3/out/INSTRUMENT_COSTS.md; rows l2vast/ds3/rows/DS3_TE2E3.json (293 cells, fields as T-B rows plus instrument, commission_rt, commission_src, slip ticks, d15x/d2x, msharpe vs DS2/DS2+DS3, lib_rank_*, exec_status, basis, bracket, regime, series_file, peak_lots); preregs l2vast/ds3/prereg/T-E2E3_P1..P9,P11,P12_*.md (+.sha256); pre-holdout text autopilot/DS3_TE2E3_PREHOLD.md; code l2vast/ds3/code/te2_*.py; progress l2vast/ds3/out/TE2_PROGRESS.md.

## E2 inventory (details in INSTRUMENT_INVENTORY.md)
- 1-min Databento continuous `.v.0` on disk, 2013-2026 (crypto 2022-): ES, RTY (2017-07-), YM, NKD, CL, GC, ZN, ZB, ZF, ZT, 6E, 6J, 6A, 6B, 6C; MBT, MET, BTC, ETH (2022-01..2026-10-14). All have series, so every one is a scored cell group. Roll: `instrument_id` change flags the bar, the roll gap is removed additively (back-adjusted to the current contract). No 1-s/tick/L2 for any of them: MAPPED basis only (stop/target on the k-min bar high/low, stop first); no direct L2 replay is possible, so exec_status stays PENDING.
- Micros MNQ, MES, M2K, MYM, MGC, MCL: only DAILY bars on disk (data/t4/daily_micros); intraday = identical price series of the parent, so they are cost variants (below). FDAX: not on disk (not scored; would need a Eurex purchase). MBT/MET: real micro-contract 1-min series (thin: median 13/17 contracts per bar).

## E3 costs (details and per-instrument table in INSTRUMENT_COSTS.md)
- outputs/FEES.md has values only for ES, NQ (4.84), MES, MNQ, M2K, MYM (1.78) and MCL (2.08). It has NO value for RTY, YM, CL, GC, ZN, ZB, ZF, ZT, 6E, 6J, 6A, 6B, 6C, NKD, MGC, MBT, MET, BTC, ETH; the earlier T-C line 'MBT/MET $1.78 per FEES.md' was a micro-class proxy, not a FEES.md line. Proxies used and flagged in every cell (`commission_src`): standard-size contracts 4.84 (the ES/NQ FEES.md structure 0.59+1.39+0.19+0.25 per side), micro-class MBT/MET/MGC 1.78. Likely error direction: conservative for rates/FX (CME exchange fees lower), uncertain for CL/GC/NKD. Every cell was re-run at 1x, 1.5x and 2x (commission and slippage both scaled), which brackets any plausible correction: commission is NOT what decides the results (see anatomy).
- Slippage: market 1 tick/side, stop exit 2 ticks (m=2/s=3 for NKD, MBT, MET); NQ control cells use the live model (4/4 ticks). That is lighter than the NQ live model for the others, and 2x of the base approximates it.

## What was run
293 cells in 11 preregs (sha256 in DECISIONS.md, all frozen before any cell was scored; P12 frozen after the P1-P9/P11 pre-holdout tables since its variant selection uses them): P1-P9 17 instruments x 15 cells (families Supertrend, Donchian, Keltner, EMA cross, HMA cross, PSAR, VWAP-slope at 5 and 15 min; ORB at 5 min with opening-range 15/30/60 at each instrument's own open: equity 09:30, CL 09:00, GC/rates 08:20, FX 08:00 ET) = 255 cells; P11 NQ control 15 cells (same engine, live-model costs); P12 15 pooled family baskets + 8 cost variants (MES, M2K, MYM, MGC, MCL, MNQ, BTC, ETH = best WF-PRE parent cell of ES, RTY, YM, GC, CL, NQ, MBT, MET re-costed). Ledger: 2,345 grid configurations appended for DS3_TE2E3 (cumulative 34,651). T-C already scored ES, RTY, YM, CL, GC, ZN, 6E, 6J, MBT, MET at hourly/daily; the 5/15-min intraday cells on these and all cells on ZB, ZF, ZT, 6A, 6B, 6C, NKD are new.
Bracket (DS2-like, in ATR units): stop 3 x ATR14(bar), target 1.0R (= 3 ATR), signal-reversal exit, flat 16:55 ET, one position, entries outside 15:00-18:05 ET. Sizing: lots per trade = 12,000 / (stop x point value) (risk in dollars per trade equals R=12,000 for every instrument; fractional contracts; p95 lots reported), per-book locks as T-B (closed-trade approximation: day -2R/+5R, give-back arm 2R keep 50%, week floor 12R). Monthly WF re-fit over the declared 9-point grid (trailing 6-month net R). NQ-equivalent: GC lots at R=12,000 = about 8.9 median (p95 23) = about 5.7 NQ-equivalent notional; margin proxy 5% of notional (no margin table on disk).
Tests: timing-destroyed shift placebo (100 draws; circular shift of the raw signal state of every grid point, same exits/re-fit/locks) is the null of record; DSR vs the ledger; marginal Sharpe at 0.5 vs ST10, HM10, pair, DS2 (pnl) and DS2 + DS3 (G1_selected_RP plus23 line of TG2: ST10/HM10/WT7 + TB7_ORBNY_k3, TE6_st10m_n7, TE7_kelt3m_n14); 300 random library books from pool.parquet (marginal-Sharpe delta rank, `lib_rank_dmsharpe_DS2`); MDE per cell; 1.5x and 2x re-runs; neighbours; span 2023-04..2024-01. ONE holdout look for the whole track (logged 16:54Z, text sha 5d07649f...). Interpretation note: placebo rank is the rank of the cell among 100 timing-shifted versions of itself; because the shifted books pay the same costs, a cell can rank near 1.0 and still be deeply negative (the signal beats random timing but not the cost).

## Results by instrument (15 cells each; WF = 2024-02..2026-10-16, $/week at R=12,000 per trade-book, per-cell locks)
| instrument | cells | median WF $/wk | best WF $/wk | cells with WF>0 | cells with WF>0 and HOLD>0 | median trades/wk | median MDE 80% $/wk | median lots (contracts at R=12k) | commission src |
|---|---|---|---|---|---|---|---|---|---|
| ES | 15 | -13,891 | 428 | 1 | 0 | 27.2 | 11,669 | 15.6 | FEES |
| RTY | 15 | -21,366 | 1,960 | 1 | 1 | 28.8 | 12,143 | 27.6 | PROXY-STD |
| YM | 15 | -15,988 | 391 | 1 | 0 | 29.6 | 12,733 | 23.9 | PROXY-STD |
| NKD | 15 | -37,560 | -7,884 | 0 | 0 | 22.6 | 11,755 | 22.8 | PROXY-STD |
| CL | 15 | -23,589 | -7,038 | 0 | 0 | 27.9 | 12,011 | 21.0 | PROXY-STD |
| GC | 15 | -4,503 | 5,697 | 4 | 4 | 30.6 | 11,622 | 12.3 | PROXY-STD |
| ZN | 15 | -77,102 | -20,418 | 0 | 0 | 16.7 | 7,451 | 79.4 | PROXY-STD |
| ZB | 15 | -81,309 | -22,369 | 0 | 0 | 16.7 | 7,917 | 41.7 | PROXY-STD |
| ZF | 15 | -86,550 | -23,853 | 0 | 0 | 17.0 | 7,047 | 136.1 | PROXY-STD |
| ZT | 15 | -96,857 | -27,410 | 0 | 0 | 14.7 | 6,932 | 171.1 | PROXY-STD |
| 6E | 15 | -45,422 | -12,776 | 0 | 0 | 25.2 | 10,973 | 63.5 | PROXY-STD |
| 6J | 15 | -40,035 | -10,401 | 0 | 0 | 22.5 | 10,402 | 92.7 | PROXY-STD |
| 6A | 15 | -52,666 | -18,986 | 0 | 0 | 22.5 | 10,001 | 107.5 | PROXY-STD |
| 6B | 15 | -61,468 | -14,263 | 0 | 0 | 23.2 | 9,158 | 104.0 | PROXY-STD |
| 6C | 15 | -75,131 | -19,504 | 0 | 0 | 20.6 | 8,726 | 153.2 | PROXY-STD |
| MBT | 15 | -13,632 | -2,604 | 0 | 0 | 27.5 | 12,203 | 205.9 | PROXY-MICRO |
| MET | 15 | -119,386 | -47,354 | 0 | 0 | 13.5 | 8,056 | 5,254.5 | PROXY-MICRO |
| NQ | 15 | -4,799 | 4,151 | 3 | 3 | 31.6 | 12,191 | 7.6 | FEES |

All 293 cells have trades/wk >= 3 (the bar is not binding; costs are: 5-min cells trade 25-60 times/wk).

## The two CANDIDATEs (gold, 15-min), post-hoc, with the evidence against them
| cell | WF $/wk | WF SD | WF Sharpe | WF-PRE | HOLD $/wk | HOLD Sharpe | L8W | IS (<=2024-01) | span23 | 1.5x | 2x | unlocked WF-PRE | year share | DSR | shift-null Sharpe p95 | rank vs 300 library books (dMarg Sharpe vs DS2) | trades/wk | corr DS2 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| TE2_GC_KEL_k15 | 5,697 | 40,771 | 1.01 | -703 | 12,672 | 2.27 | -7,883 | -6,901 | -9,981 | 3,934 | 2,370 | -647 | 2024:-0.40, 2025:0.70, 2026:0.70 | 0.034 | 0.68 | 0.96 | 18.7 | 0.03 |
| TE2_GC_VWAP_k15 | 4,769 | 39,096 | 0.88 | 4,943 | 4,506 | 0.83 | 655 | -19,019 | -20,430 | 1,504 | -1,445 | 5,376 | 2024:0.24, 2025:0.28, 2026:0.48 | 0.023 | 0.19 | 0.96 | 28.3 | -0.04 |

- Both lose in the pre-2024 span (IS negative; span 2023-04..2024-01 -$10k and -$20k per week: the DS3 span23>0 flag fails, so the verdict is CANDIDATE and not PASS) and earn only in 2025-26 (gold's trend run); KEL's WF-PRE is -$0.7k and its year share is 70% + 70% - 40% (fails the 60% rule); VWAP fails 2x cost (-$1.4k). DSR 0.02-0.03 at 34.6k cumulative trials (the PASS bar is 0.95). Best-of-N null over 270 single-instrument cells: p95 of the maximum WF Sharpe among timing-destroyed draws is 0.92 (mean 0.23); the best real cell (GC KEL k15) is 1.01 - a hair above the p95 of a best-of-270 null, i.e. what 2 of 270 cells would do by chance in a trend year, with a negative IS span. Weekly corr to DS2 is +0.03/-0.04, so the cells are diversifying if real; marginal Sharpe vs DS2 goes up (msharpe_up_DS2 True) but the rank among random library books is 0.96 (not above 0.95 by a margin that survives 270 looks). GC's commission is a proxy (4.84); both cells stay positive at 1.5x (and KEL at 2x), commission is only about $0.9k-1.8k/wk of the $40k SD. Verdict stands: CANDIDATE (post-selection), register and watch forward; do not add to the pool.
- Series for D3L: l2vast/ds3/out/SERIES/TE2_GC_KEL_k15.parquet and TE2_GC_VWAP_k15.parquet (ld, pnl, pnl_1p5x, pnl_2x, trades; MAPPED basis, closed-trade lock approximation, R=12,000 per trade, bracket stop 3xATR14 / target 1.0R / reversal / flat 16:55, regime all); rows carry exec_status, span23_mean, trades_wk, hold_mean, lots (median, contracts), peak_lots (p95 contracts), series_file, basis, bracket, regime. GC lots 8.9 median / 23 p95 = about 5.7 NQ-equivalent (notional ratio), within the 50-contract limit.

## Pooled baskets (best power; MDE next to every null)
| basket | WF $/wk | WF SD | HOLD $/wk | span23 | trades/wk (all 17 instruments) | MDE 80% | placebo rank | verdict |
|---|---|---|---|---|---|---|---|---|
| TE2_BASKET_ST_k5 | -85,829 | 17,021 | -86,133 | -95,932 | 456 | 4,002 | 0.99 | DEAD |
| TE2_BASKET_ST_k15 | -33,679 | 16,239 | -36,689 | -39,156 | 334 | 3,818 | 0.02 | DEAD |
| TE2_BASKET_DON_k5 | -52,657 | 14,860 | -53,854 | -57,129 | 275 | 3,494 | 0.99 | DEAD |
| TE2_BASKET_DON_k15 | -15,131 | 10,653 | -15,749 | -17,115 | 159 | 2,505 | 0.2 | DEAD |
| TE2_BASKET_KEL_k5 | -70,901 | 16,571 | -70,862 | -78,174 | 398 | 3,896 | 0.17 | DEAD |
| TE2_BASKET_KEL_k15 | -19,753 | 12,429 | -20,312 | -27,808 | 210 | 2,922 | 0.58 | DEAD |
| TE2_BASKET_EMA_k5 | -70,871 | 17,551 | -72,200 | -77,597 | 371 | 4,126 | 1.0 | DEAD |
| TE2_BASKET_EMA_k15 | -25,412 | 13,961 | -25,627 | -25,643 | 235 | 3,282 | 0.0 | DEAD |
| TE2_BASKET_HMA_k5 | -96,978 | 17,116 | -96,808 | -111,332 | 573 | 4,024 | 1.0 | DEAD |
| TE2_BASKET_HMA_k15 | -47,671 | 18,284 | -49,426 | -53,616 | 462 | 4,299 | 0.64 | DEAD |
| TE2_BASKET_PSAR_k5 | -101,243 | 17,507 | -99,536 | -114,692 | 607 | 4,116 | 0.93 | DEAD |
| TE2_BASKET_PSAR_k15 | -52,694 | 15,811 | -54,149 | -57,199 | 510 | 3,717 | 0.0 | DEAD |
| TE2_BASKET_VWAP_k5 | -85,993 | 17,871 | -83,992 | -97,376 | 512 | 4,202 | 1.0 | DEAD |
| TE2_BASKET_VWAP_k15 | -43,052 | 15,880 | -43,786 | -47,812 | 418 | 3,733 | 0.88 | DEAD |
| TE2_BASKET_ORB_k5 | -18,220 | 12,862 | -20,038 | -20,879 | 153 | 3,024 | 1.0 | DEAD |

Each basket is the mean of the 17 instrument cell series (each at R=12,000), so its weekly SD is $10-18k and the MDE is $2.5-4.3k; the observed means are -$15k to -$101k, i.e. outside any CI that includes zero by an order of magnitude. Conclusion: the 5/15-min trend families at these entries are not net-positive on any instrument group (equity index ex-NQ, rates, FX, energy/metals, crypto) at 1-2 tick costs; the cause is cost per trade relative to the 3-ATR stop (a rates or FX 5-min 3-ATR stop is 5-12 ticks, so RT slippage plus commission is 0.2-0.6 R per trade at 15-60 trades/wk).

## Cost variants (same trades, other contract; commission only differs)
| variant | parent cell | WF $/wk | HOLD $/wk | 2x WF | verdict |
|---|---|---|---|---|---|
| MES | TE2_PARENT_KEL_k15 | -1,110 | -5,285 | -7,898 | DEAD |
| M2K | TE2_PARENT_ORB_k5 | -437 | 4,420 | -5,384 | DEAD |
| MYM | TE2_PARENT_ORB_k5 | -2,416 | -1,955 | -7,011 | DEAD |
| MGC | TE2_PARENT_VWAP_k15 | 335 | -133 | -8,088 | DEAD |
| MCL | TE2_PARENT_DON_k15 | -9,655 | -11,035 | -16,681 | DEAD |
| BTC | TE2_PARENT_ST_k15 | -2,314 | -7,349 | -10,120 | DEAD |
| ETH | TE2_PARENT_DON_k15 | -10,009 | -8,070 | -17,466 | DEAD |
| MNQ | TE2_PARENT_ST_k15 | 1,159 | 4,472 | -7,949 | DEAD |

Micro commission per unit of exposure is 3.7x the standard contract (17.80 vs 4.84 per standard-equivalent), which removes $0.7k-4.4k/wk from the micro variants of the same trades (MES -1.5k, M2K -2.4k, MYM -2.8k, MGC -4.4k, MCL -0.7k, MNQ -3.0k). The micro version of the GC VWAP candidate (MGC) falls from +$4.8k to +$0.3k/wk and is DEAD; a micro-sized deployment of any of these cells is therefore not viable at FEES.md costs. BTC/ETH standard-size variants (proxy 4.84 per 0.02/0.002 contracts per MBT/MET) are far cheaper per unit exposure than MBT/MET (+2.5k and +37k/wk vs the MBT/MET parents) and still negative: the CME crypto micros are commission-dominated.

## NT8 chartability (each instrument/bar)
All 17 instruments plus NQ chart in NT8 as Minute 5 / Minute 15 bars on the CME feed (24h session template), merge-back-adjusted continuous contract; symbols: ES, RTY, YM, NKD, CL, GC, ZN, ZB, ZF, ZT, 6E, 6J, 6A, 6B, 6C, MBT, MET (+ MNQ/MES/M2K/MYM/MGC/MCL micros: same prices). Built into NT8: ATR, EMA, Donchian Channel, Keltner Channel, Parabolic SAR, VWAP (session), Opening Range; Supertrend and HMA need custom NinjaScript or third-party indicators. NKD/MBT/MET/6A/6B/6C have missing minutes (thin); NT8 minute bars are built the same way from trades, so the chart matches the data used. Identity test not run (nothing to deliver).

## Caveats (stated, not hidden)
1. Commission is a flagged proxy for 12 of the 17 instruments (no FEES.md value); results are cost-dominated by slippage ticks, not commission, but a real statement per instrument settles it. 2. Closed-trade lock approximation, MAPPED 1-min basis only; a PASS would have needed the exact 1-s engine (none exists for these instruments). 3. P11 mechanism text of the NQ control says 'no cell scored on NQ' (frozen text; T-B did score NQ at 1-min/NQ bracket); NQ control cells use a 3-ATR/1R bracket not T-B's 60-pt exits, so they are not a replication of T-B. 4. Sessions/hours of entry are the NQ template (no entries 15:00-18:05 ET) for all instruments. 5. ORB uses a fixed 0 buffer. 6. 3x3 widening: not run (no PASS). 7. A1-A3 regime splitters, B-class entries and C-class exits were not applied here (other tracks).

## Per-cell table (all 293)
| cell | commission src | WF $/wk | WF-PRE | HOLD | span23 | tr/wk | MDE | placebo rank | 2x WF | verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| TE2_ES_ST_k5 | FEES | -38,598 | -41,004 | -35,376 | -56,030 | 34.0 | 15,302 | 0.23 | -60,540 | DEAD |
| TE2_ES_ST_k15 | FEES | -7,152 | -3,097 | -11,519 | -18,179 | 23.9 | 10,875 | 0.77 | -15,982 | DEAD |
| TE2_ES_DON_k5 | FEES | -21,596 | -17,773 | -25,495 | -38,343 | 20.8 | 12,675 | 0.23 | -36,792 | DEAD |
| TE2_ES_DON_k15 | FEES | -1,858 | -852 | -2,941 | -6,785 | 9.5 | 8,525 | 0.92 | -5,357 | DEAD |
| TE2_ES_KEL_k5 | FEES | -21,151 | -26,804 | -14,606 | -30,907 | 26.7 | 11,669 | 0.71 | -39,713 | DEAD |
| TE2_ES_KEL_k15 | FEES | 428 | 4,745 | -4,340 | -13,070 | 12.5 | 8,402 | 0.99 | -4,107 | DEAD |
| TE2_ES_EMA_k5 | FEES | -23,292 | -17,493 | -29,345 | -50,438 | 27.2 | 15,059 | 0.87 | -44,249 | DEAD |
| TE2_ES_EMA_k15 | FEES | -3,060 | -2,465 | -3,672 | -3,862 | 14.2 | 10,632 | 0.94 | -7,650 | DEAD |
| TE2_ES_HMA_k5 | FEES | -52,075 | -52,459 | -50,887 | -89,131 | 48.3 | 13,869 | 0.56 | -83,933 | DEAD |
| TE2_ES_HMA_k15 | FEES | -13,891 | -12,335 | -15,404 | -37,645 | 31.4 | 11,272 | 0.71 | -26,185 | DEAD |
| TE2_ES_PSAR_k5 | FEES | -58,784 | -66,418 | -49,499 | -97,282 | 50.8 | 14,496 | 0.46 | -89,915 | DEAD |
| TE2_ES_PSAR_k15 | FEES | -11,920 | -11,066 | -12,686 | -35,782 | 35.1 | 12,134 | 0.9 | -26,147 | DEAD |
| TE2_ES_VWAP_k5 | FEES | -41,100 | -43,701 | -37,627 | -66,476 | 43.2 | 14,691 | 0.98 | -69,222 | DEAD |
| TE2_ES_VWAP_k15 | FEES | -12,769 | -10,166 | -15,454 | -22,893 | 29.0 | 10,386 | 0.71 | -24,355 | DEAD |
| TE2_ES_ORB_k5 | FEES | -1,779 | 280 | -4,024 | -4,167 | 9.8 | 8,025 | 0.99 | -5,918 | DEAD |
| TE2_RTY_ST_k5 | PROXY-STD | -36,424 | -38,161 | -33,973 | -43,254 | 34.9 | 15,626 | 0.53 | -58,605 | DEAD |
| TE2_RTY_ST_k15 | PROXY-STD | -16,452 | -17,850 | -14,668 | -18,136 | 22.8 | 10,413 | 0.06 | -24,081 | DEAD |
| TE2_RTY_DON_k5 | PROXY-STD | -21,145 | -20,931 | -21,070 | -19,954 | 19.4 | 12,143 | 0.29 | -36,159 | DEAD |
| TE2_RTY_DON_k15 | PROXY-STD | -8,781 | -10,130 | -7,163 | -14,238 | 12.3 | 8,906 | 0.13 | -13,144 | DEAD |
| TE2_RTY_KEL_k5 | PROXY-STD | -27,626 | -34,513 | -19,624 | -42,463 | 28.8 | 13,849 | 0.19 | -43,718 | DEAD |
| TE2_RTY_KEL_k15 | PROXY-STD | -7,858 | -6,802 | -8,906 | -14,863 | 12.1 | 7,292 | 0.24 | -11,592 | DEAD |
| TE2_RTY_EMA_k5 | PROXY-STD | -22,603 | -30,364 | -13,710 | -34,778 | 28.0 | 15,176 | 0.87 | -42,384 | DEAD |
| TE2_RTY_EMA_k15 | PROXY-STD | -13,688 | -13,294 | -13,921 | -12,500 | 16.5 | 9,736 | 0.0 | -19,210 | DEAD |
| TE2_RTY_HMA_k5 | PROXY-STD | -47,027 | -50,071 | -42,978 | -81,618 | 46.8 | 12,788 | 0.88 | -78,748 | DEAD |
| TE2_RTY_HMA_k15 | PROXY-STD | -21,366 | -27,909 | -13,834 | -30,289 | 31.7 | 11,286 | 0.08 | -33,131 | DEAD |
| TE2_RTY_PSAR_k5 | PROXY-STD | -63,310 | -62,711 | -63,040 | -86,299 | 49.8 | 14,523 | 0.04 | -89,904 | DEAD |
| TE2_RTY_PSAR_k15 | PROXY-STD | -24,217 | -31,185 | -16,175 | -34,621 | 35.0 | 12,294 | 0.04 | -37,260 | DEAD |
| TE2_RTY_VWAP_k5 | PROXY-STD | -46,778 | -55,850 | -36,084 | -64,000 | 42.7 | 14,069 | 0.51 | -76,025 | DEAD |
| TE2_RTY_VWAP_k15 | PROXY-STD | -18,204 | -19,703 | -16,282 | -25,896 | 29.2 | 9,263 | 0.1 | -30,072 | DEAD |
| TE2_RTY_ORB_k5 | PROXY-STD | 1,960 | -2,474 | 6,822 | 1,238 | 8.6 | 7,072 | 1.0 | -744 | DEAD |
| TE2_YM_ST_k5 | PROXY-STD | -34,870 | -38,205 | -30,679 | -45,875 | 35.3 | 15,129 | 0.19 | -55,260 | DEAD |
| TE2_YM_ST_k15 | PROXY-STD | -4,254 | -2,185 | -6,474 | -20,358 | 24.5 | 11,902 | 0.96 | -11,909 | DEAD |
| TE2_YM_DON_k5 | PROXY-STD | -10,550 | -13,893 | -6,708 | -31,992 | 19.3 | 12,916 | 0.91 | -23,035 | DEAD |
| TE2_YM_DON_k15 | PROXY-STD | -5,188 | -8,606 | -1,341 | -9,709 | 11.6 | 8,553 | 0.43 | -8,465 | DEAD |
| TE2_YM_KEL_k5 | PROXY-STD | -24,687 | -27,773 | -20,920 | -35,439 | 29.6 | 13,502 | 0.21 | -42,253 | DEAD |
| TE2_YM_KEL_k15 | PROXY-STD | -4,276 | -4,459 | -4,011 | -11,674 | 14.7 | 9,428 | 0.69 | -8,123 | DEAD |
| TE2_YM_EMA_k5 | PROXY-STD | -24,829 | -29,408 | -19,415 | -37,632 | 26.9 | 13,029 | 0.39 | -40,869 | DEAD |
| TE2_YM_EMA_k15 | PROXY-STD | -5,372 | -10,954 | 864 | -22,266 | 13.3 | 8,796 | 0.63 | -9,181 | DEAD |
| TE2_YM_HMA_k5 | PROXY-STD | -43,940 | -38,573 | -49,213 | -72,341 | 48.0 | 13,542 | 0.72 | -74,390 | DEAD |
| TE2_YM_HMA_k15 | PROXY-STD | -15,899 | -18,316 | -13,000 | -29,456 | 31.4 | 12,733 | 0.35 | -25,244 | DEAD |
| TE2_YM_PSAR_k5 | PROXY-STD | -57,382 | -65,419 | -47,674 | -77,641 | 51.1 | 14,790 | 0.13 | -84,237 | DEAD |
| TE2_YM_PSAR_k15 | PROXY-STD | -18,358 | -20,929 | -15,252 | -28,636 | 38.2 | 11,699 | 0.28 | -30,722 | DEAD |
| TE2_YM_VWAP_k5 | PROXY-STD | -43,270 | -50,658 | -34,485 | -76,518 | 46.0 | 13,341 | 0.46 | -67,384 | DEAD |
| TE2_YM_VWAP_k15 | PROXY-STD | -15,988 | -20,824 | -10,418 | -28,751 | 30.7 | 10,179 | 0.08 | -26,063 | DEAD |
| TE2_YM_ORB_k5 | PROXY-STD | 391 | 852 | -122 | -7,448 | 9.0 | 8,051 | 1.0 | -2,353 | DEAD |
| TE2_NKD_ST_k5 | PROXY-STD | -73,652 | -84,000 | -61,155 | -112,014 | 32.2 | 14,131 | 1.0 | -105,550 | DEAD |
| TE2_NKD_ST_k15 | PROXY-STD | -21,460 | -29,896 | -11,841 | -42,693 | 21.1 | 11,222 | 0.82 | -43,304 | DEAD |
| TE2_NKD_DON_k5 | PROXY-STD | -41,271 | -52,354 | -28,440 | -59,751 | 16.3 | 11,929 | 0.66 | -66,435 | DEAD |
| TE2_NKD_DON_k15 | PROXY-STD | -7,884 | -10,231 | -5,180 | -9,714 | 8.1 | 7,675 | 0.83 | -15,936 | DEAD |
| TE2_NKD_KEL_k5 | PROXY-STD | -67,809 | -74,875 | -59,018 | -103,413 | 28.3 | 11,403 | 0.89 | -103,082 | DEAD |
| TE2_NKD_KEL_k15 | PROXY-STD | -19,849 | -21,320 | -17,935 | -29,984 | 15.5 | 8,835 | 0.12 | -35,228 | DEAD |
| TE2_NKD_EMA_k5 | PROXY-STD | -61,280 | -71,454 | -49,157 | -82,646 | 22.6 | 13,065 | 0.32 | -91,756 | DEAD |
| TE2_NKD_EMA_k15 | PROXY-STD | -19,402 | -27,079 | -10,650 | -20,558 | 14.3 | 9,581 | 0.13 | -34,418 | DEAD |
| TE2_NKD_HMA_k5 | PROXY-STD | -75,608 | -89,002 | -59,723 | -119,576 | 34.6 | 15,244 | 1.0 | -110,566 | DEAD |
| TE2_NKD_HMA_k15 | PROXY-STD | -33,581 | -36,330 | -30,056 | -70,381 | 28.5 | 11,755 | 0.65 | -60,833 | DEAD |
| TE2_NKD_PSAR_k5 | PROXY-STD | -86,387 | -91,579 | -79,391 | -119,706 | 35.8 | 12,595 | 0.86 | -118,853 | DEAD |
| TE2_NKD_PSAR_k15 | PROXY-STD | -37,560 | -46,388 | -27,271 | -59,839 | 29.8 | 11,944 | 0.47 | -65,544 | DEAD |
| TE2_NKD_VWAP_k5 | PROXY-STD | -57,131 | -67,711 | -44,621 | -87,544 | 31.5 | 12,178 | 1.0 | -85,976 | DEAD |
| TE2_NKD_VWAP_k15 | PROXY-STD | -22,976 | -27,866 | -17,244 | -36,904 | 21.0 | 9,013 | 0.92 | -43,064 | DEAD |
| TE2_NKD_ORB_k5 | PROXY-STD | -14,279 | -18,489 | -9,427 | -30,089 | 8.2 | 7,681 | 1.0 | -30,408 | DEAD |
| TE2_CL_ST_k5 | PROXY-STD | -44,244 | -55,827 | -30,819 | -54,177 | 34.1 | 15,231 | 0.88 | -77,234 | DEAD |
| TE2_CL_ST_k15 | PROXY-STD | -16,806 | -13,710 | -19,974 | -6,637 | 21.7 | 11,032 | 0.16 | -26,714 | DEAD |
| TE2_CL_DON_k5 | PROXY-STD | -23,589 | -23,353 | -23,502 | -17,861 | 17.9 | 10,534 | 0.78 | -41,907 | DEAD |
| TE2_CL_DON_k15 | PROXY-STD | -8,907 | -8,089 | -9,678 | -7,541 | 9.8 | 7,756 | 0.21 | -14,041 | DEAD |
| TE2_CL_KEL_k5 | PROXY-STD | -36,484 | -41,964 | -29,903 | -31,792 | 27.9 | 12,712 | 0.12 | -60,035 | DEAD |
| TE2_CL_KEL_k15 | PROXY-STD | -7,038 | -10,275 | -3,363 | -12,967 | 14.2 | 7,739 | 0.57 | -13,886 | DEAD |
| TE2_CL_EMA_k5 | PROXY-STD | -36,072 | -38,431 | -32,939 | -33,962 | 25.3 | 12,522 | 0.69 | -57,659 | DEAD |
| TE2_CL_EMA_k15 | PROXY-STD | -7,686 | -9,834 | -5,204 | 1,007 | 15.9 | 9,915 | 0.6 | -15,267 | DEAD |
| TE2_CL_HMA_k5 | PROXY-STD | -70,520 | -81,233 | -57,666 | -67,994 | 41.5 | 13,032 | 0.24 | -100,162 | DEAD |
| TE2_CL_HMA_k15 | PROXY-STD | -16,499 | -19,337 | -13,126 | -18,480 | 29.1 | 12,408 | 0.77 | -30,443 | DEAD |
| TE2_CL_PSAR_k5 | PROXY-STD | -68,929 | -79,093 | -56,705 | -73,742 | 45.1 | 15,153 | 0.66 | -97,316 | DEAD |
| TE2_CL_PSAR_k15 | PROXY-STD | -27,897 | -40,566 | -13,514 | -25,102 | 33.8 | 12,011 | 0.03 | -44,782 | DEAD |
| TE2_CL_VWAP_k5 | PROXY-STD | -59,821 | -64,377 | -53,916 | -68,896 | 38.5 | 13,466 | 0.63 | -87,523 | DEAD |
| TE2_CL_VWAP_k15 | PROXY-STD | -21,129 | -21,629 | -20,267 | -23,768 | 28.7 | 9,526 | 0.06 | -35,924 | DEAD |
| TE2_CL_ORB_k5 | PROXY-STD | -9,077 | -8,723 | -9,333 | -4,911 | 9.6 | 6,273 | 0.94 | -14,808 | DEAD |
| TE2_GC_ST_k5 | PROXY-STD | -6,313 | -15,719 | 4,153 | -40,975 | 38.0 | 15,294 | 0.96 | -19,455 | DEAD |
| TE2_GC_ST_k15 | PROXY-STD | -2,024 | -6,645 | 3,103 | -21,891 | 24.1 | 9,899 | 0.7 | -7,549 | DEAD |
| TE2_GC_DON_k5 | PROXY-STD | -5,557 | -9,875 | -713 | -29,174 | 25.3 | 13,026 | 0.83 | -15,259 | DEAD |
| TE2_GC_DON_k15 | PROXY-STD | 1,134 | -1,969 | 4,538 | -11,496 | 14.6 | 8,492 | 0.83 | -1,759 | DEAD |
| TE2_GC_KEL_k5 | PROXY-STD | -4,503 | -10,519 | 2,199 | -26,484 | 30.6 | 11,582 | 0.96 | -14,105 | DEAD |
| TE2_GC_KEL_k15 | PROXY-STD | 5,697 | -703 | 12,672 | -9,981 | 18.7 | 9,585 | 1.0 | 2,370 | CANDIDATE |
| TE2_GC_EMA_k5 | PROXY-STD | -10,365 | -17,280 | -2,587 | -32,650 | 30.9 | 14,454 | 0.74 | -21,181 | DEAD |
| TE2_GC_EMA_k15 | PROXY-STD | 1,389 | -723 | 3,699 | -19,162 | 19.4 | 9,167 | 0.85 | -2,523 | DEAD |
| TE2_GC_HMA_k5 | PROXY-STD | -19,160 | -25,018 | -12,416 | -64,920 | 57.5 | 15,846 | 0.96 | -43,508 | DEAD |
| TE2_GC_HMA_k15 | PROXY-STD | -8,454 | -12,925 | -3,398 | -15,410 | 31.8 | 12,711 | 0.49 | -15,748 | DEAD |
| TE2_GC_PSAR_k5 | PROXY-STD | -19,961 | -32,033 | -6,352 | -67,856 | 63.1 | 15,724 | 0.96 | -41,763 | DEAD |
| TE2_GC_PSAR_k15 | PROXY-STD | -5,927 | -6,099 | -5,650 | -31,689 | 37.8 | 11,622 | 0.71 | -13,664 | DEAD |
| TE2_GC_VWAP_k5 | PROXY-STD | -2,666 | -18,056 | 14,348 | -53,082 | 49.7 | 14,973 | 1.0 | -21,116 | DEAD |
| TE2_GC_VWAP_k15 | PROXY-STD | 4,769 | 4,943 | 4,506 | -20,430 | 28.3 | 9,192 | 1.0 | -1,445 | CANDIDATE |
| TE2_GC_ORB_k5 | PROXY-STD | -603 | -1,160 | 20 | -4,664 | 11.1 | 8,826 | 0.92 | -3,462 | DEAD |
| TE2_ZN_ST_k5 | PROXY-STD | -124,516 | -122,274 | -125,158 | -122,911 | 17.9 | 7,451 | 0.88 | -152,743 | DEAD |
| TE2_ZN_ST_k15 | PROXY-STD | -46,051 | -40,743 | -51,229 | -38,841 | 14.8 | 9,028 | 0.37 | -81,269 | DEAD |
| TE2_ZN_DON_k5 | PROXY-STD | -77,047 | -71,438 | -82,099 | -78,417 | 12.7 | 8,236 | 0.93 | -114,646 | DEAD |
| TE2_ZN_DON_k15 | PROXY-STD | -23,830 | -18,775 | -29,056 | -15,381 | 7.6 | 6,357 | 0.2 | -43,609 | DEAD |
| TE2_ZN_KEL_k5 | PROXY-STD | -77,102 | -75,983 | -77,201 | -81,054 | 14.0 | 7,395 | 0.77 | -120,150 | DEAD |
| TE2_ZN_KEL_k15 | PROXY-STD | -20,418 | -21,554 | -18,865 | -27,872 | 7.6 | 5,297 | 0.94 | -38,622 | DEAD |
| TE2_ZN_EMA_k5 | PROXY-STD | -112,083 | -104,776 | -118,494 | -103,905 | 16.7 | 8,906 | 0.84 | -143,115 | DEAD |
| TE2_ZN_EMA_k15 | PROXY-STD | -39,195 | -33,880 | -44,480 | -29,885 | 11.3 | 8,240 | 0.06 | -67,797 | DEAD |
| TE2_ZN_HMA_k5 | PROXY-STD | -141,388 | -138,724 | -142,248 | -135,490 | 22.2 | 4,509 | 1.0 | -149,913 | DEAD |
| TE2_ZN_HMA_k15 | PROXY-STD | -77,004 | -72,364 | -80,991 | -71,553 | 22.3 | 9,360 | 0.62 | -118,514 | DEAD |
| TE2_ZN_PSAR_k5 | PROXY-STD | -143,571 | -140,339 | -145,025 | -142,836 | 22.9 | 4,126 | 0.88 | -150,330 | DEAD |
| TE2_ZN_PSAR_k15 | PROXY-STD | -86,855 | -83,390 | -89,400 | -77,558 | 23.7 | 8,078 | 0.12 | -126,392 | DEAD |
| TE2_ZN_VWAP_k5 | PROXY-STD | -133,831 | -131,432 | -134,509 | -124,283 | 19.2 | 4,953 | 1.0 | -149,445 | DEAD |
| TE2_ZN_VWAP_k15 | PROXY-STD | -77,797 | -74,273 | -80,541 | -66,652 | 22.2 | 7,712 | 0.54 | -116,442 | DEAD |
| TE2_ZN_ORB_k5 | PROXY-STD | -24,594 | -21,477 | -27,669 | -19,260 | 7.4 | 6,421 | 1.0 | -47,481 | DEAD |
| TE2_ZB_ST_k5 | PROXY-STD | -138,403 | -135,380 | -139,702 | -129,137 | 17.6 | 6,572 | 0.49 | -153,492 | DEAD |
| TE2_ZB_ST_k15 | PROXY-STD | -46,639 | -36,317 | -57,338 | -45,289 | 15.9 | 10,125 | 0.88 | -80,860 | DEAD |
| TE2_ZB_DON_k5 | PROXY-STD | -87,846 | -87,133 | -87,339 | -83,123 | 12.5 | 8,666 | 0.67 | -125,679 | DEAD |
| TE2_ZB_DON_k15 | PROXY-STD | -22,369 | -17,969 | -26,893 | -16,707 | 7.1 | 6,419 | 0.64 | -40,715 | DEAD |
| TE2_ZB_KEL_k5 | PROXY-STD | -113,624 | -114,589 | -110,889 | -111,632 | 16.7 | 8,201 | 0.55 | -150,111 | DEAD |
| TE2_ZB_KEL_k15 | PROXY-STD | -30,365 | -30,184 | -30,118 | -29,789 | 10.0 | 6,508 | 0.46 | -52,864 | DEAD |
| TE2_ZB_EMA_k5 | PROXY-STD | -113,698 | -108,055 | -118,250 | -104,034 | 16.2 | 8,851 | 1.0 | -145,012 | DEAD |
| TE2_ZB_EMA_k15 | PROXY-STD | -42,347 | -38,082 | -46,428 | -31,764 | 11.6 | 10,005 | 0.0 | -69,420 | DEAD |
| TE2_ZB_HMA_k5 | PROXY-STD | -143,091 | -136,991 | -147,715 | -137,660 | 21.0 | 4,607 | 1.0 | -153,446 | DEAD |
| TE2_ZB_HMA_k15 | PROXY-STD | -77,794 | -75,055 | -79,670 | -68,806 | 22.7 | 9,985 | 0.77 | -116,196 | DEAD |
| TE2_ZB_PSAR_k5 | PROXY-STD | -144,747 | -142,569 | -145,020 | -139,838 | 21.5 | 4,699 | 1.0 | -152,706 | DEAD |
| TE2_ZB_PSAR_k15 | PROXY-STD | -81,309 | -77,346 | -84,484 | -70,927 | 24.5 | 9,518 | 0.68 | -122,726 | DEAD |
| TE2_ZB_VWAP_k5 | PROXY-STD | -135,065 | -134,358 | -133,857 | -123,388 | 17.3 | 5,510 | 1.0 | -153,052 | DEAD |
| TE2_ZB_VWAP_k15 | PROXY-STD | -77,822 | -72,072 | -83,019 | -64,582 | 23.1 | 7,917 | 0.6 | -116,402 | DEAD |
| TE2_ZB_ORB_k5 | PROXY-STD | -26,421 | -23,155 | -29,636 | -18,406 | 7.7 | 6,989 | 1.0 | -49,624 | DEAD |
| TE2_ZF_ST_k5 | PROXY-STD | -137,695 | -132,019 | -141,930 | -130,249 | 18.7 | 6,779 | 0.84 | -154,226 | DEAD |
| TE2_ZF_ST_k15 | PROXY-STD | -58,530 | -53,200 | -63,549 | -34,014 | 15.7 | 10,095 | 0.0 | -93,376 | DEAD |
| TE2_ZF_DON_k5 | PROXY-STD | -86,550 | -80,057 | -92,438 | -81,399 | 12.9 | 9,003 | 0.93 | -125,249 | DEAD |
| TE2_ZF_DON_k15 | PROXY-STD | -23,853 | -20,387 | -27,326 | -12,547 | 7.4 | 6,092 | 0.27 | -43,120 | DEAD |
| TE2_ZF_KEL_k5 | PROXY-STD | -120,614 | -114,109 | -126,016 | -118,068 | 17.0 | 7,047 | 0.05 | -150,375 | DEAD |
| TE2_ZF_KEL_k15 | PROXY-STD | -34,601 | -32,920 | -35,946 | -34,003 | 10.6 | 6,485 | 0.03 | -60,183 | DEAD |
| TE2_ZF_EMA_k5 | PROXY-STD | -119,329 | -114,150 | -123,285 | -104,804 | 16.5 | 8,634 | 0.85 | -148,076 | DEAD |
| TE2_ZF_EMA_k15 | PROXY-STD | -40,289 | -31,566 | -49,319 | -25,849 | 11.8 | 8,697 | 0.02 | -68,955 | DEAD |
| TE2_ZF_HMA_k5 | PROXY-STD | -143,125 | -138,474 | -146,149 | -134,920 | 21.0 | 4,186 | 1.0 | -153,345 | DEAD |
| TE2_ZF_HMA_k15 | PROXY-STD | -79,523 | -72,952 | -85,600 | -66,138 | 22.6 | 9,340 | 0.51 | -118,740 | DEAD |
| TE2_ZF_PSAR_k5 | PROXY-STD | -145,745 | -142,583 | -147,090 | -139,559 | 20.7 | 4,982 | 0.86 | -153,463 | DEAD |
| TE2_ZF_PSAR_k15 | PROXY-STD | -90,007 | -83,604 | -95,746 | -75,654 | 23.6 | 8,408 | 0.02 | -127,350 | DEAD |
| TE2_ZF_VWAP_k5 | PROXY-STD | -136,091 | -132,109 | -138,482 | -127,543 | 17.7 | 5,637 | 1.0 | -153,138 | DEAD |
| TE2_ZF_VWAP_k15 | PROXY-STD | -78,822 | -76,030 | -80,743 | -61,957 | 22.3 | 7,831 | 0.4 | -119,209 | DEAD |
| TE2_ZF_ORB_k5 | PROXY-STD | -26,400 | -22,762 | -30,024 | -20,623 | 7.8 | 6,951 | 1.0 | -49,520 | DEAD |
| TE2_ZT_ST_k5 | PROXY-STD | -146,026 | -143,057 | -147,154 | -140,924 | 15.2 | 4,855 | 0.47 | -158,387 | DEAD |
| TE2_ZT_ST_k15 | PROXY-STD | -62,120 | -55,282 | -68,747 | -55,834 | 14.7 | 9,466 | 0.2 | -101,964 | DEAD |
| TE2_ZT_DON_k5 | PROXY-STD | -99,966 | -95,499 | -103,423 | -90,953 | 11.6 | 8,243 | 0.77 | -135,258 | DEAD |
| TE2_ZT_DON_k15 | PROXY-STD | -27,410 | -25,999 | -28,563 | -20,128 | 6.9 | 6,006 | 0.33 | -48,479 | DEAD |
| TE2_ZT_KEL_k5 | PROXY-STD | -129,217 | -129,355 | -127,164 | -131,521 | 14.6 | 6,932 | 0.35 | -153,122 | DEAD |
| TE2_ZT_KEL_k15 | PROXY-STD | -36,674 | -31,109 | -42,273 | -33,523 | 9.7 | 6,322 | 0.49 | -64,689 | DEAD |
| TE2_ZT_EMA_k5 | PROXY-STD | -134,717 | -128,725 | -139,344 | -127,533 | 14.2 | 6,704 | 0.13 | -154,839 | DEAD |
| TE2_ZT_EMA_k15 | PROXY-STD | -47,786 | -46,421 | -48,588 | -31,994 | 10.4 | 7,922 | 0.0 | -77,249 | DEAD |
| TE2_ZT_HMA_k5 | PROXY-STD | -148,092 | -143,623 | -150,843 | -145,435 | 17.9 | 4,221 | 0.92 | -155,761 | DEAD |
| TE2_ZT_HMA_k15 | PROXY-STD | -88,322 | -80,301 | -95,870 | -73,856 | 21.9 | 9,954 | 0.95 | -127,789 | DEAD |
| TE2_ZT_PSAR_k5 | PROXY-STD | -148,613 | -145,533 | -149,825 | -144,507 | 17.7 | 3,246 | 0.75 | -156,038 | DEAD |
| TE2_ZT_PSAR_k15 | PROXY-STD | -96,857 | -86,360 | -107,010 | -92,693 | 21.8 | 8,206 | 0.28 | -134,851 | DEAD |
| TE2_ZT_VWAP_k5 | PROXY-STD | -143,880 | -140,883 | -145,071 | -136,608 | 14.9 | 4,447 | 0.97 | -155,672 | DEAD |
| TE2_ZT_VWAP_k15 | PROXY-STD | -95,464 | -90,632 | -99,389 | -79,518 | 20.9 | 7,262 | 0.22 | -131,657 | DEAD |
| TE2_ZT_ORB_k5 | PROXY-STD | -29,089 | -23,214 | -35,140 | -22,832 | 7.4 | 7,203 | 1.0 | -54,268 | DEAD |
| TE2_6E_ST_k5 | PROXY-STD | -80,565 | -73,658 | -86,998 | -90,007 | 28.7 | 14,025 | 0.35 | -113,756 | DEAD |
| TE2_6E_ST_k15 | PROXY-STD | -31,047 | -29,536 | -32,257 | -33,510 | 21.9 | 10,760 | 0.0 | -49,911 | DEAD |
| TE2_6E_DON_k5 | PROXY-STD | -47,044 | -45,577 | -47,969 | -30,861 | 16.6 | 11,312 | 0.27 | -76,944 | DEAD |
| TE2_6E_DON_k15 | PROXY-STD | -12,776 | -11,429 | -14,073 | -12,455 | 8.2 | 7,183 | 0.14 | -21,065 | DEAD |
| TE2_6E_KEL_k5 | PROXY-STD | -57,617 | -55,612 | -58,981 | -60,839 | 25.2 | 10,973 | 0.22 | -93,607 | DEAD |
| TE2_6E_KEL_k15 | PROXY-STD | -15,935 | -15,754 | -15,901 | -17,096 | 11.3 | 6,973 | 0.08 | -25,629 | DEAD |
| TE2_6E_EMA_k5 | PROXY-STD | -63,341 | -58,254 | -68,019 | -64,885 | 23.0 | 12,444 | 0.42 | -96,971 | DEAD |
| TE2_6E_EMA_k15 | PROXY-STD | -20,666 | -22,776 | -18,035 | -16,870 | 13.9 | 9,170 | 0.06 | -33,765 | DEAD |
| TE2_6E_HMA_k5 | PROXY-STD | -92,823 | -94,706 | -89,381 | -112,535 | 35.7 | 12,542 | 0.98 | -128,464 | DEAD |
| TE2_6E_HMA_k15 | PROXY-STD | -37,168 | -39,658 | -33,875 | -27,088 | 29.4 | 11,422 | 0.21 | -63,328 | DEAD |
| TE2_6E_PSAR_k5 | PROXY-STD | -99,297 | -101,821 | -95,053 | -102,234 | 39.2 | 11,722 | 0.88 | -132,684 | DEAD |
| TE2_6E_PSAR_k15 | PROXY-STD | -45,422 | -42,032 | -48,492 | -43,136 | 33.9 | 11,546 | 0.03 | -72,865 | DEAD |
| TE2_6E_VWAP_k5 | PROXY-STD | -88,369 | -93,166 | -81,778 | -81,902 | 32.1 | 10,808 | 0.66 | -116,472 | DEAD |
| TE2_6E_VWAP_k15 | PROXY-STD | -28,300 | -32,639 | -23,099 | -32,086 | 25.9 | 8,944 | 0.63 | -51,095 | DEAD |
| TE2_6E_ORB_k5 | PROXY-STD | -16,697 | -16,567 | -16,594 | -13,327 | 9.9 | 7,529 | 1.0 | -28,745 | DEAD |
| TE2_6J_ST_k5 | PROXY-STD | -77,597 | -63,298 | -92,226 | -85,071 | 27.7 | 13,450 | 0.96 | -113,728 | DEAD |
| TE2_6J_ST_k15 | PROXY-STD | -28,523 | -20,635 | -36,803 | -35,279 | 18.2 | 10,107 | 0.24 | -50,038 | DEAD |
| TE2_6J_DON_k5 | PROXY-STD | -36,804 | -27,825 | -46,165 | -52,888 | 15.6 | 9,752 | 1.0 | -68,772 | DEAD |
| TE2_6J_DON_k15 | PROXY-STD | -12,790 | -11,124 | -14,439 | -8,279 | 10.2 | 7,795 | 0.44 | -25,373 | DEAD |
| TE2_6J_KEL_k5 | PROXY-STD | -58,498 | -45,561 | -71,907 | -61,508 | 24.4 | 10,758 | 0.76 | -92,912 | DEAD |
| TE2_6J_KEL_k15 | PROXY-STD | -10,401 | -5,195 | -15,991 | -17,955 | 10.4 | 6,991 | 0.97 | -22,001 | DEAD |
| TE2_6J_EMA_k5 | PROXY-STD | -60,077 | -50,545 | -69,706 | -76,071 | 22.5 | 12,156 | 0.98 | -96,941 | DEAD |
| TE2_6J_EMA_k15 | PROXY-STD | -19,075 | -12,966 | -25,533 | -15,252 | 14.5 | 8,781 | 0.45 | -36,703 | DEAD |
| TE2_6J_HMA_k5 | PROXY-STD | -98,110 | -85,925 | -110,106 | -98,707 | 33.6 | 11,723 | 0.89 | -130,361 | DEAD |
| TE2_6J_HMA_k15 | PROXY-STD | -40,035 | -31,545 | -48,810 | -58,269 | 27.4 | 10,402 | 0.76 | -68,623 | DEAD |
| TE2_6J_PSAR_k5 | PROXY-STD | -99,671 | -89,658 | -109,250 | -103,530 | 37.5 | 11,404 | 0.92 | -132,553 | DEAD |
| TE2_6J_PSAR_k15 | PROXY-STD | -45,323 | -32,062 | -59,284 | -52,668 | 31.0 | 11,116 | 0.39 | -76,225 | DEAD |
| TE2_6J_VWAP_k5 | PROXY-STD | -71,854 | -60,178 | -83,676 | -82,993 | 31.0 | 11,721 | 1.0 | -102,795 | DEAD |
| TE2_6J_VWAP_k15 | PROXY-STD | -29,599 | -26,691 | -32,372 | -23,982 | 22.1 | 9,092 | 0.88 | -53,235 | DEAD |
| TE2_6J_ORB_k5 | PROXY-STD | -24,279 | -17,200 | -31,730 | -16,823 | 9.3 | 8,074 | 1.0 | -42,233 | DEAD |
| TE2_6A_ST_k5 | PROXY-STD | -92,616 | -84,300 | -100,427 | -75,533 | 27.4 | 11,776 | 0.3 | -127,196 | DEAD |
| TE2_6A_ST_k15 | PROXY-STD | -35,545 | -33,896 | -36,841 | -26,730 | 18.5 | 9,937 | 0.02 | -56,355 | DEAD |
| TE2_6A_DON_k5 | PROXY-STD | -51,950 | -46,517 | -57,178 | -46,135 | 16.0 | 10,554 | 0.42 | -85,589 | DEAD |
| TE2_6A_DON_k15 | PROXY-STD | -18,986 | -21,286 | -16,170 | -12,854 | 8.2 | 7,200 | 0.01 | -29,536 | DEAD |
| TE2_6A_KEL_k5 | PROXY-STD | -77,849 | -72,677 | -82,409 | -58,481 | 25.2 | 10,959 | 0.0 | -112,229 | DEAD |
| TE2_6A_KEL_k15 | PROXY-STD | -19,785 | -20,293 | -18,933 | -17,639 | 11.1 | 7,574 | 0.03 | -32,437 | DEAD |
| TE2_6A_EMA_k5 | PROXY-STD | -69,660 | -64,737 | -74,066 | -65,235 | 22.5 | 12,677 | 0.61 | -105,399 | DEAD |
| TE2_6A_EMA_k15 | PROXY-STD | -25,433 | -27,633 | -22,632 | -20,069 | 13.1 | 9,226 | 0.03 | -40,717 | DEAD |
| TE2_6A_HMA_k5 | PROXY-STD | -106,444 | -101,970 | -109,813 | -100,599 | 33.2 | 10,001 | 0.57 | -134,676 | DEAD |
| TE2_6A_HMA_k15 | PROXY-STD | -53,140 | -51,233 | -54,462 | -33,815 | 28.9 | 10,893 | 0.02 | -81,286 | DEAD |
| TE2_6A_PSAR_k5 | PROXY-STD | -110,700 | -104,508 | -115,902 | -110,724 | 35.4 | 9,349 | 0.56 | -138,957 | DEAD |
| TE2_6A_PSAR_k15 | PROXY-STD | -52,666 | -45,664 | -59,615 | -44,236 | 30.7 | 12,004 | 0.06 | -79,551 | DEAD |
| TE2_6A_VWAP_k5 | PROXY-STD | -86,519 | -79,706 | -92,760 | -67,559 | 30.3 | 11,857 | 0.99 | -114,768 | DEAD |
| TE2_6A_VWAP_k15 | PROXY-STD | -33,284 | -28,500 | -38,070 | -27,404 | 22.5 | 9,887 | 0.49 | -55,261 | DEAD |
| TE2_6A_ORB_k5 | PROXY-STD | -20,098 | -16,487 | -23,784 | -22,167 | 10.2 | 8,335 | 1.0 | -38,432 | DEAD |
| TE2_6B_ST_k5 | PROXY-STD | -109,396 | -106,893 | -110,547 | -122,300 | 24.3 | 10,495 | 0.98 | -143,211 | DEAD |
| TE2_6B_ST_k15 | PROXY-STD | -43,490 | -39,547 | -47,199 | -41,828 | 18.2 | 9,822 | 0.0 | -70,888 | DEAD |
| TE2_6B_DON_k5 | PROXY-STD | -66,347 | -67,906 | -63,651 | -62,624 | 15.3 | 8,889 | 0.54 | -105,056 | DEAD |
| TE2_6B_DON_k15 | PROXY-STD | -14,263 | -12,092 | -16,447 | -21,277 | 7.4 | 6,340 | 0.49 | -25,652 | DEAD |
| TE2_6B_KEL_k5 | PROXY-STD | -94,307 | -87,004 | -100,975 | -95,806 | 23.2 | 10,764 | 0.17 | -131,957 | DEAD |
| TE2_6B_KEL_k15 | PROXY-STD | -25,132 | -23,198 | -26,896 | -21,626 | 12.4 | 6,985 | 0.02 | -43,018 | DEAD |
| TE2_6B_EMA_k5 | PROXY-STD | -87,485 | -87,795 | -85,858 | -84,630 | 20.1 | 11,008 | 0.97 | -125,774 | DEAD |
| TE2_6B_EMA_k15 | PROXY-STD | -30,302 | -30,818 | -29,287 | -29,379 | 13.3 | 8,250 | 0.0 | -50,276 | DEAD |
| TE2_6B_HMA_k5 | PROXY-STD | -130,258 | -129,659 | -129,005 | -128,844 | 25.9 | 7,582 | 0.5 | -148,154 | DEAD |
| TE2_6B_HMA_k15 | PROXY-STD | -55,926 | -47,890 | -63,967 | -43,722 | 26.1 | 10,561 | 0.14 | -90,328 | DEAD |
| TE2_6B_PSAR_k5 | PROXY-STD | -130,588 | -129,999 | -129,317 | -131,098 | 26.6 | 7,204 | 0.72 | -149,154 | DEAD |
| TE2_6B_PSAR_k15 | PROXY-STD | -61,468 | -57,630 | -64,798 | -48,796 | 29.0 | 11,181 | 0.04 | -97,169 | DEAD |
| TE2_6B_VWAP_k5 | PROXY-STD | -110,098 | -109,505 | -109,132 | -124,935 | 24.0 | 9,158 | 1.0 | -136,987 | DEAD |
| TE2_6B_VWAP_k15 | PROXY-STD | -45,647 | -48,530 | -41,797 | -51,408 | 25.0 | 9,536 | 0.55 | -75,752 | DEAD |
| TE2_6B_ORB_k5 | PROXY-STD | -20,448 | -19,953 | -20,693 | -17,575 | 9.8 | 8,059 | 1.0 | -40,095 | DEAD |
| TE2_6C_ST_k5 | PROXY-STD | -129,820 | -122,487 | -135,999 | -125,679 | 21.2 | 7,651 | 0.7 | -153,406 | DEAD |
| TE2_6C_ST_k15 | PROXY-STD | -49,174 | -48,190 | -49,535 | -43,787 | 18.1 | 10,150 | 0.01 | -80,568 | DEAD |
| TE2_6C_DON_k5 | PROXY-STD | -75,131 | -71,014 | -78,568 | -74,202 | 13.7 | 9,483 | 0.92 | -112,353 | DEAD |
| TE2_6C_DON_k15 | PROXY-STD | -19,504 | -20,920 | -17,655 | -17,488 | 7.1 | 6,494 | 0.14 | -33,474 | DEAD |
| TE2_6C_KEL_k5 | PROXY-STD | -115,819 | -106,501 | -124,393 | -105,534 | 21.3 | 9,145 | 0.04 | -147,083 | DEAD |
| TE2_6C_KEL_k15 | PROXY-STD | -30,592 | -31,809 | -28,800 | -23,819 | 11.6 | 7,205 | 0.0 | -51,717 | DEAD |
| TE2_6C_EMA_k5 | PROXY-STD | -105,173 | -100,667 | -108,597 | -88,660 | 18.3 | 9,187 | 0.76 | -141,327 | DEAD |
| TE2_6C_EMA_k15 | PROXY-STD | -34,504 | -39,052 | -28,980 | -23,725 | 11.7 | 9,329 | 0.0 | -55,926 | DEAD |
| TE2_6C_HMA_k5 | PROXY-STD | -136,058 | -129,971 | -140,772 | -131,538 | 24.4 | 5,868 | 0.98 | -148,998 | DEAD |
| TE2_6C_HMA_k15 | PROXY-STD | -67,015 | -54,736 | -79,572 | -59,716 | 25.5 | 11,352 | 0.21 | -102,539 | DEAD |
| TE2_6C_PSAR_k5 | PROXY-STD | -136,691 | -131,172 | -140,768 | -140,232 | 24.1 | 5,992 | 1.0 | -149,808 | DEAD |
| TE2_6C_PSAR_k15 | PROXY-STD | -75,797 | -72,367 | -78,466 | -57,701 | 27.3 | 10,515 | 0.02 | -113,158 | DEAD |
| TE2_6C_VWAP_k5 | PROXY-STD | -123,962 | -119,612 | -126,937 | -117,951 | 20.6 | 7,288 | 1.0 | -147,462 | DEAD |
| TE2_6C_VWAP_k15 | PROXY-STD | -62,319 | -59,357 | -64,669 | -60,399 | 24.3 | 8,726 | 0.19 | -98,258 | DEAD |
| TE2_6C_ORB_k5 | PROXY-STD | -27,829 | -23,403 | -32,302 | -22,868 | 10.3 | 8,076 | 1.0 | -53,475 | DEAD |
| TE2_MBT_ST_k5 | PROXY-MICRO | -37,576 | -30,193 | -45,166 | -103,408 | 35.7 | 14,057 | 0.78 | -67,370 | DEAD |
| TE2_MBT_ST_k15 | PROXY-MICRO | -4,828 | 3,387 | -13,818 | -33,778 | 24.5 | 11,813 | 0.96 | -17,000 | DEAD |
| TE2_MBT_DON_k5 | PROXY-MICRO | -13,632 | -7,122 | -20,612 | -49,962 | 18.4 | 12,210 | 0.93 | -31,060 | DEAD |
| TE2_MBT_DON_k15 | PROXY-MICRO | -2,604 | 1,779 | -7,401 | -9,915 | 16.4 | 9,303 | 0.97 | -11,111 | DEAD |
| TE2_MBT_KEL_k5 | PROXY-MICRO | -29,105 | -25,945 | -32,163 | -79,089 | 31.0 | 12,598 | 0.82 | -56,097 | DEAD |
| TE2_MBT_KEL_k15 | PROXY-MICRO | -4,442 | -907 | -8,275 | -19,553 | 15.4 | 8,778 | 0.89 | -12,212 | DEAD |
| TE2_MBT_EMA_k5 | PROXY-MICRO | -19,743 | -10,058 | -30,135 | -83,837 | 27.5 | 13,221 | 1.0 | -46,181 | DEAD |
| TE2_MBT_EMA_k15 | PROXY-MICRO | -7,935 | -6,063 | -9,884 | -23,023 | 18.3 | 9,279 | 0.52 | -19,309 | DEAD |
| TE2_MBT_HMA_k5 | PROXY-MICRO | -49,205 | -43,809 | -54,432 | -115,203 | 47.2 | 13,870 | 0.96 | -84,878 | DEAD |
| TE2_MBT_HMA_k15 | PROXY-MICRO | -9,018 | -7,338 | -10,738 | -57,936 | 31.5 | 12,203 | 0.99 | -26,274 | DEAD |
| TE2_MBT_PSAR_k5 | PROXY-MICRO | -56,042 | -50,661 | -61,154 | -118,289 | 51.3 | 14,672 | 0.67 | -88,503 | DEAD |
| TE2_MBT_PSAR_k15 | PROXY-MICRO | -14,836 | -10,056 | -19,889 | -44,098 | 34.1 | 11,434 | 0.81 | -31,357 | DEAD |
| TE2_MBT_VWAP_k5 | PROXY-MICRO | -35,120 | -28,743 | -41,637 | -96,844 | 40.6 | 13,285 | 1.0 | -64,868 | DEAD |
| TE2_MBT_VWAP_k15 | PROXY-MICRO | -9,225 | -3,458 | -15,449 | -46,993 | 26.4 | 9,458 | 0.97 | -24,058 | DEAD |
| TE2_MBT_ORB_k5 | PROXY-MICRO | -5,265 | 1,133 | -12,244 | -10,226 | 9.4 | 7,036 | 0.99 | -11,446 | DEAD |
| TE2_MET_ST_k5 | PROXY-MICRO | -150,786 | -148,485 | -151,106 | -153,293 | 13.6 | 3,283 | 0.67 | -158,165 | DEAD |
| TE2_MET_ST_k15 | PROXY-MICRO | -98,443 | -91,165 | -105,022 | -148,867 | 16.0 | 10,248 | 0.83 | -136,419 | DEAD |
| TE2_MET_DON_k5 | PROXY-MICRO | -129,146 | -126,521 | -130,142 | -123,559 | 11.0 | 6,354 | 0.99 | -152,939 | DEAD |
| TE2_MET_DON_k15 | PROXY-MICRO | -47,354 | -46,184 | -47,948 | -84,448 | 7.1 | 8,056 | 0.18 | -79,441 | DEAD |
| TE2_MET_KEL_k5 | PROXY-MICRO | -149,308 | -146,065 | -150,689 | -154,933 | 13.5 | 3,944 | 0.67 | -158,754 | DEAD |
| TE2_MET_KEL_k15 | PROXY-MICRO | -74,560 | -70,973 | -77,420 | -137,322 | 12.0 | 9,425 | 0.91 | -117,661 | DEAD |
| TE2_MET_EMA_k5 | PROXY-MICRO | -141,065 | -136,071 | -144,500 | -143,448 | 12.7 | 5,558 | 0.97 | -158,133 | DEAD |
| TE2_MET_EMA_k15 | PROXY-MICRO | -76,659 | -69,336 | -83,608 | -110,781 | 11.5 | 9,392 | 0.0 | -114,355 | DEAD |
| TE2_MET_HMA_k5 | PROXY-MICRO | -151,696 | -149,041 | -152,394 | -156,133 | 14.5 | 3,850 | 0.13 | -156,328 | DEAD |
| TE2_MET_HMA_k15 | PROXY-MICRO | -115,768 | -112,317 | -117,872 | -148,909 | 19.3 | 9,695 | 1.0 | -144,252 | DEAD |
| TE2_MET_PSAR_k5 | PROXY-MICRO | -150,708 | -148,392 | -151,045 | -154,399 | 14.0 | 2,978 | 0.68 | -156,956 | DEAD |
| TE2_MET_PSAR_k15 | PROXY-MICRO | -119,386 | -114,694 | -122,806 | -149,238 | 20.4 | 8,696 | 1.0 | -146,738 | DEAD |
| TE2_MET_VWAP_k5 | PROXY-MICRO | -146,321 | -143,177 | -147,636 | -154,876 | 12.7 | 4,491 | 1.0 | -157,902 | DEAD |
| TE2_MET_VWAP_k15 | PROXY-MICRO | -107,315 | -103,398 | -110,058 | -139,173 | 16.4 | 8,871 | 1.0 | -140,540 | DEAD |
| TE2_MET_ORB_k5 | PROXY-MICRO | -65,239 | -64,802 | -64,762 | -120,792 | 7.9 | 9,729 | 1.0 | -110,100 | DEAD |
| TE2_NQ_ST_k5 | FEES | -12,408 | -15,679 | -8,617 | -40,964 | 37.6 | 16,626 | 0.86 | -30,790 | DEAD |
| TE2_NQ_ST_k15 | FEES | 4,151 | 2,409 | 6,011 | -8,972 | 25.1 | 11,520 | 1.0 | -3,594 | DEAD |
| TE2_NQ_DON_k5 | FEES | -2,864 | -9,488 | 4,483 | -26,597 | 25.6 | 12,340 | 0.94 | -14,533 | DEAD |
| TE2_NQ_DON_k15 | FEES | -4,799 | -6,120 | -3,270 | -11,975 | 13.5 | 8,760 | 0.29 | -8,353 | DEAD |
| TE2_NQ_KEL_k5 | FEES | -5,221 | -9,011 | -964 | -21,118 | 32.5 | 12,752 | 0.98 | -19,206 | DEAD |
| TE2_NQ_KEL_k15 | FEES | -2,943 | -3,818 | -1,934 | -5,974 | 16.8 | 9,487 | 0.67 | -6,603 | DEAD |
| TE2_NQ_EMA_k5 | FEES | 202 | -2,705 | 3,404 | -17,085 | 31.6 | 15,270 | 1.0 | -15,432 | DEAD |
| TE2_NQ_EMA_k15 | FEES | -4,321 | -7,603 | -638 | -4,000 | 16.4 | 9,172 | 0.45 | -8,158 | DEAD |
| TE2_NQ_HMA_k5 | FEES | -33,332 | -34,986 | -31,016 | -68,833 | 52.7 | 15,028 | 0.65 | -58,031 | DEAD |
| TE2_NQ_HMA_k15 | FEES | -9,248 | -4,104 | -14,785 | -16,090 | 33.2 | 12,095 | 0.62 | -18,065 | DEAD |
| TE2_NQ_PSAR_k5 | FEES | -29,696 | -28,939 | -30,094 | -61,369 | 59.5 | 14,274 | 0.95 | -61,526 | DEAD |
| TE2_NQ_PSAR_k15 | FEES | -9,211 | -8,068 | -10,337 | -14,880 | 34.7 | 12,191 | 0.74 | -18,587 | DEAD |
| TE2_NQ_VWAP_k5 | FEES | -21,204 | -36,730 | -3,769 | -53,088 | 47.5 | 15,470 | 0.99 | -40,575 | DEAD |
| TE2_NQ_VWAP_k15 | FEES | -4,221 | -8,561 | 627 | -10,896 | 30.8 | 10,185 | 0.98 | -13,534 | DEAD |
| TE2_NQ_ORB_k5 | FEES | 453 | 75 | 864 | 2,440 | 10.0 | 8,193 | 0.98 | -2,336 | DEAD |
| TE2_BASKET_ST_k5 | mixed (see members) | -85,829 | -84,409 | -86,133 | -95,932 | 456.5 | 4,002 | 0.99 | -110,137 | DEAD |
| TE2_BASKET_ST_k15 | mixed (see members) | -33,679 | -30,500 | -36,689 | -39,156 | 334.5 | 3,818 | 0.02 | -55,776 | DEAD |
| TE2_BASKET_DON_k5 | mixed (see members) | -52,657 | -50,870 | -53,854 | -57,129 | 275.5 | 3,494 | 0.99 | -79,596 | DEAD |
| TE2_BASKET_DON_k15 | mixed (see members) | -15,131 | -14,368 | -15,749 | -17,115 | 159.3 | 2,505 | 0.2 | -27,075 | DEAD |
| TE2_BASKET_KEL_k5 | mixed (see members) | -70,901 | -69,991 | -70,862 | -78,174 | 398.1 | 3,896 | 0.17 | -98,194 | DEAD |
| TE2_BASKET_KEL_k15 | mixed (see members) | -19,753 | -18,983 | -20,312 | -27,808 | 209.7 | 2,922 | 0.58 | -34,800 | DEAD |
| TE2_BASKET_EMA_k5 | mixed (see members) | -70,871 | -68,721 | -72,200 | -77,597 | 371.3 | 4,126 | 1.0 | -97,639 | DEAD |
| TE2_BASKET_EMA_k15 | mixed (see members) | -25,412 | -24,879 | -25,627 | -25,643 | 235.0 | 3,282 | 0.0 | -42,513 | DEAD |
| TE2_BASKET_HMA_k5 | mixed (see members) | -96,978 | -95,838 | -96,808 | -111,332 | 573.4 | 4,024 | 1.0 | -119,743 | DEAD |
| TE2_BASKET_HMA_k15 | mixed (see members) | -47,671 | -45,444 | -49,426 | -53,616 | 461.5 | 4,299 | 0.64 | -73,497 | DEAD |
| TE2_BASKET_PSAR_k5 | mixed (see members) | -101,243 | -101,440 | -99,536 | -114,692 | 606.7 | 4,116 | 0.93 | -122,538 | DEAD |
| TE2_BASKET_PSAR_k15 | mixed (see members) | -52,694 | -50,673 | -54,149 | -57,199 | 509.6 | 3,717 | 0.0 | -79,206 | DEAD |
| TE2_BASKET_VWAP_k5 | mixed (see members) | -85,993 | -86,660 | -83,992 | -97,376 | 511.9 | 4,202 | 1.0 | -109,400 | DEAD |
| TE2_BASKET_VWAP_k15 | mixed (see members) | -43,052 | -41,813 | -43,786 | -47,812 | 418.1 | 3,733 | 0.88 | -67,225 | DEAD |
| TE2_BASKET_ORB_k5 | mixed (see members) | -18,220 | -16,330 | -20,038 | -20,879 | 153.2 | 3,024 | 1.0 | -34,301 | DEAD |
| TE2_MES_KEL_k15 | variant MES | -1,110 | 2,689 | -5,285 | -13,180 | 12.2 | 8,313 | 0.99 | -7,898 | DEAD |
| TE2_M2K_ORB_k5 | variant M2K | -437 | -4,834 | 4,420 | -1,390 | 8.6 | 7,008 | 1.0 | -5,384 | DEAD |
| TE2_MYM_ORB_k5 | variant MYM | -2,416 | -2,802 | -1,955 | -10,229 | 8.7 | 8,038 | 1.0 | -7,011 | DEAD |
| TE2_MGC_VWAP_k15 | variant MGC | 335 | 756 | -133 | -27,448 | 26.9 | 9,028 | 0.99 | -8,088 | DEAD |
| TE2_MCL_DON_k15 | variant MCL | -9,655 | -8,275 | -11,035 | -10,783 | 8.5 | 7,379 | 0.42 | -16,681 | DEAD |
| TE2_BTC_ST_k15 | variant BTC | -2,314 | 2,282 | -7,349 | -14,652 | 27.9 | 11,246 | 0.85 | -10,120 | DEAD |
| TE2_ETH_DON_k15 | variant ETH | -10,009 | -11,633 | -8,070 | -17,674 | 13.1 | 8,808 | 0.16 | -17,466 | DEAD |
| TE2_MNQ_ST_k15 | variant MNQ | 1,159 | -1,859 | 4,472 | -15,358 | 24.4 | 11,526 | 1.0 | -7,949 | DEAD |
