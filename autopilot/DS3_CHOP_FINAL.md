# DS3_CHOP_FINAL - T-CHOP block 0 (forward-register sleeves + 2 range-fade cells), D3CH 2026-10-27
**Chop: 0 PASS, 0 CANDIDATE. Best diversifier: C04 RSI2T_t10 (direct (cov 97%)), Sharpe 1.21, corr -0.12, losing-week P&L $26,261/wk (stack L25 weeks, mean $-134,975), marginal +0.30 / maxDD delta -43,349.**

PARTIAL DELIVERY: covers the ORIGINAL narrow T-CHOP brief (13 cells, prereg l2vast/ds3/prereg/T-CHOP_prereg.md sha256 fed8a99fa2d38ed9096eba13141b92c7d96852c3c5a73d9bb4c5fb9d545f9ea6, ledger +13). The FULL-SCOPE directive (DIRECTIVE_PBX_CHOP_FULL.md: band fades, range model, failed-breakout fades, gap/first-hour/Asia reversal, tape exhaustion, gates x bars x orders, random-in-regime placebo) arrived mid-run and is NOT started; its blocks need new preregs. Placebo (b) random-in-regime is not scored here: the named dip-buy sleeves are ungated, so their random-entry placebo from T3.10b is the (b)-equivalent (prior ranks in the tables).

## Answer
Under the prereg gates nothing is PASS or CANDIDATE: every dip-buy cell fails the 3-trades/wk measurability gate (0.4-1.0/wk) AND the timing-shift placebo on marginal Sharpe (ranks 0.34-0.90 vs 0.95: the diversification comes from an independent positive mean, not from timing). The diversification itself is consistent: the seven dip-buy cells have weekly corr to the DS2+DS3 stack of -0.12..+0.05 (WF; -0.11..-0.25 holdout), a POSITIVE mean in the stack's 36 worst weeks (+$7k..+$26k/wk at equal risk vs the stack's -$135k/wk there) and positive marginal Sharpe in WF and HOLD. The L25-week P&L timing-shift rank is 0.96-0.99 for C01, C04, C05, C06, C09. ORB Asia and the range fades are not diversifiers (L25 negative); the range fades lose money standalone.
Cost: unfiltered NQ/ES/YM dip-buy adds maxDD (+$240-420k at the WF cap line) from April 2025 (two crash dip-buys, -$19.9k/lot each); the SMA200-filtered RSI2T avoids them (dMaxDD -$43k WF / -$55k HOLD); IBS -$48k/-$17k.
RECOMMENDED-FOR-SIM: C04 RSI2T_t10 (NQ), spec DS3_SPEC_RSI2T_t10.md. Not a PASS: blocking gates G6 and M (0.39 trades/wk; ~135 weeks to settle the mean).

## Definitions (frozen in the prereg)
Stack = ST10+HM10+WT7 (per-book locks) + KB+SM+PB3B_R5_P1 (risk parity, DS3 peak 23 lots); WF mean $48,560/wk. L25 = 36 WF weeks below the 25th percentile (p25 -$48.8k, mean -$135.0k); 55 negative weeks. Chop sessions = FAILPRED +60 CHOSEN theta 0.3 (316 sessions), P&L allocated by time overlap. Equal risk = WF weekly SD scaled to ST10 ($57.3k). Weekly MDE 13.5k. Marginal = add-one to KB+SM+PB (risk parity), 50-cap line, interval peaks; non-NQ cells have their own per-instrument 50 cap (YM needs 65 lots at equal risk: infeasible).

## Leaderboard A (standalone, equal-risk lots)
| id | family | cell | instr. | own bracket | lots (equal risk) | trades/wk | win rate vs required | WF $/wk | HOLD $/wk | 2023-04..24-01 $/wk | weekly SD | Sharpe (WF) | maxDD WF / HOLD | worst week | Basis |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C01 | RSI2 dip-buy | RSI2C_s20 | NQ | long 15:56 close if RSI2<10; stop entry-2.0 ATR14; time exit next 15:56 | 13.1 | 0.49 | 0.59 vs 0.44 | 11.5k | 13.8k | 1.4k | 57.3k | 1.45 | 632.2k / 229.0k | -225.1k | direct (cov 98%) |
| C02 | RSI2 dip-buy | ES_RSI2_t10 | ES | long 15:56 close if RSI2<10; no stop; time exit next 15:56 | 21.1 | 0.42 | 0.68 vs 0.43 | 13.9k | 16.0k | 4.6k | 57.3k | 1.74 | 463.7k / 136.6k | -320.5k | direct (cov 87%) |
| C04 | RSI2 dip-buy + SMA200 | RSI2T_t10 | NQ | RSI2<10 and open>SMA200; time exit next 15:56 | 15.8 | 0.39 | 0.59 vs 0.44 | 9.6k | 11.5k | 1.5k | 57.3k | 1.21 | 277.6k / 277.6k | -248.8k | direct (cov 97%) |
| C05 | IBS dip-buy | IBS_t20_n1 | NQ | IBS<0.20 (RTH range) at 15:55; time exit next 15:56 | 9.2 | 0.75 | 0.58 vs 0.44 | 9.2k | 12.0k | 7.3k | 57.3k | 1.16 | 266.0k / 160.9k | -214.4k | direct (cov 99%) |
| C06 | IBS dip-buy | RTY_IBS_t20_n1 | RTY | IBS<0.20 on RTY; time exit next 15:56 | 36.0 | 0.91 | 0.53 vs 0.44 | 7.6k | 10.7k | -0.4k | 57.3k | 0.96 | 249.1k / 210.9k | -162.5k | direct (cov 88%) |
| C07 | ORB Asia | ORB_ASIA_15_v1_s60 | NQ | Asia 15-min OR + vol filter; stop 60 pt, target 90 pt; own locks | 40.8 | 0.84 | 0.50 vs 0.42 | 9.0k | 14.0k | -7.8k | 57.3k | 1.14 | 426.1k / 259.1k | -103.5k | mapped |
| C08 | ORB Asia | ORB_ASIA_15_v1_s75 | NQ | as C07, stop 75 pt, target 112.5 pt | 34.8 | 0.84 | 0.50 vs 0.41 | 9.3k | 18.2k | -11.3k | 57.3k | 1.17 | 433.8k / 227.1k | -108.7k | mapped |
| C09 | RSI2/IBS combo | COMB_c3_R | NQ | RSI2<10 or IBS<0.2; lots 3 / 1.5 by trailing-8w rule; time exit next 15:56 | 10.5 | 0.98 | 0.58 vs 0.47 | 9.8k | 12.1k | 6.9k | 57.3k | 1.23 | 299.9k / 299.9k | -219.6k | direct (cov 99%) |
| C13 | RSI2 dip-buy (YM, mapped) | YM_RSI2_t10 | YM | long 15:56 close if RSI2<10 (YM), time exit next 15:56 | 31.7 | 0.55 | 0.59 vs 0.46 | 9.1k | 12.4k | 6.4k | 57.3k | 1.14 | 483.9k / 146.7k | -301.7k | mapped |
| C03 | RSI2 dip-buy (2 legs) | DIPBUY_RSI2_2lot | NQ+ES | C01 + C02 legs 1:1 (spec 2+2) | 8.9 | 0.92 | 0.63 vs 0.45 | 13.7k | 16.1k | 2.9k | 57.3k | 1.73 | 597.0k / 155.6k | -287.9k | direct (cov 93%) |
| C10 | trade-modifier (D2 shorts) | T14_S_s50_t1.5_n14 | NQ(DS2 shorts) | DS2 shorts 50 pt stop / 1.5R, 14 lots (longs 60/1.0R) | 14.0 | 0.00 | 0.20 vs 0.60 | 7.9k | 7.3k | 0.0k | 77.5k | 0.74 | 1139.9k / 875.0k | -289.2k | mapped |
| C11 | range fade (FOURTH R4) | FOURTH_R4_k2.0_H60_8lots | NQ | limit fade at VWAP+-1.5u, target VWAP, stop 2.0u, 60-min time exit, 8 lots | 15.1 | 30.80 | 0.50 vs 0.55 | -23.0k | -28.0k | -11.9k | 57.3k | -2.89 | 3500.0k / 2154.8k | -149.7k | mapped |
| C12 | range fade (FOURTH R2) | FOURTH_R2_k1.0_H120_8lots | NQ | limit fade at session high/low, target midpoint, stop 1.0u, 120-min time exit, 8 lots | 14.2 | 25.04 | 0.47 vs 0.52 | -26.3k | -24.4k | -14.8k | 57.3k | -3.31 | 3959.0k / 1902.9k | -162.8k | mapped |

## Leaderboard B (diversification)
| id | cell | corr stack WF [HOLD] | corr KB / SM / PB (WF) | stack-losing wks L25 $/wk (n) | negative wks $/wk (n) | chop(+60) sessions P&L WF [P&L share vs time share] | marg. Sharpe WF / HOLD | dMaxDD at 50-cap WF / HOLD | peak lots | placebo: prior min(WF,pre) / shift-marg / shift-L25 | executable from NT8 bars |
|---|---|---|---|---|---|---|---|---|---|---|---|
| C01 | RSI2C_s20 | -0.05 [-0.23] | -0.10 / -0.10 / +0.03 | 23.7k (36) | 11.4k (55) | 167.2k [10% vs 7%] | +0.44 / +0.90 | 241.0k / -107.1k | 50 (NQ line) | 0.92 / 0.84 / 0.97 | 0/312 (x_rsi2) |
| C02 | ES_RSI2_t10 | +0.05 [-0.11] | -0.02 / -0.14 / +0.11 | 15.2k (36) | 6.2k (55) | 119.5k [6% vs 6%] | +0.33 / +1.28 | 249.9k / -84.7k | 43 own instr. | 0.96 / 0.44 / 0.77 | 0/301 (x_rsi2) |
| C04 | RSI2T_t10 | -0.12 [-0.25] | -0.11 / -0.02 / -0.06 | 26.3k (36) | 17.2k (55) | 193.1k [14% vs 9%] | +0.30 / +0.30 | -43.3k / -54.6k | 50 (NQ line) | 0.91 / 0.87 / 0.99 | 0/218 (x_chop) |
| C05 | IBS_t20_n1 | -0.09 [-0.20] | -0.00 / -0.08 / +0.04 | 23.3k (36) | 13.1k (55) | 260.1k [20% vs 7%] | +0.10 / +0.85 | -47.6k / -16.5k | 50 (NQ line) | 0.93 / 0.34 / 0.96 | 0/585 (x_chop) |
| C06 | RTY_IBS_t20_n1 | -0.06 [-0.16] | -0.11 / -0.05 / +0.06 | 21.2k (36) | 13.4k (55) | 130.4k [12% vs 7%] | +0.11 / +0.50 | 68.3k / 32.0k | 47 own instr. | 0.93 / 0.90 / 0.97 | 1 extra/449 = 0.2% (x_chop) |
| C07 | ORB_ASIA_15_v1_s60 | +0.24 [+0.16] | +0.03 / +0.10 / +0.24 | -12.0k (36) | -1.4k (55) | -62.7k [-5% vs 6%] | -0.11 / +0.14 | 11.3k / -5.2k | 50 (NQ line) | 0.96 / 0.57 / 0.03 | not tested |
| C08 | ORB_ASIA_15_v1_s75 | +0.16 [+0.07] | -0.01 / +0.09 / +0.13 | -2.3k (36) | 3.1k (55) | -75.1k [-6% vs 8%] | +0.06 / +0.68 | 12.8k / -47.6k | 50 (NQ line) | 0.96 / 0.80 / 0.24 | not tested |
| C09 | COMB_c3_R | -0.06 [-0.23] | -0.04 / -0.03 / +0.04 | 23.5k (36) | 12.7k (55) | 228.9k [16% vs 8%] | +0.25 / +0.78 | 13.5k / -17.7k | 50 (NQ line) | 0.97 / 0.58 / 0.99 | 0/746 (x_chop) |
| C13 | YM_RSI2_t10 | +0.00 [-0.23] | -0.03 / -0.20 / +0.09 | 7.2k (36) | 3.2k (55) | 54.8k [4% vs 6%] | +0.03 / +1.20 | 305.8k / -5.0k | 65 own instr. | 0.95 / 0.42 / 0.45 | 0 mismatch (x_rsi2 YM) |
| C03 | DIPBUY_RSI2_2lot | -0.01 [-0.22] | -0.08 / -0.13 / +0.07 | 22.6k (36) | 10.4k (55) | 164.4k [8% vs 7%] | +0.33 / +1.19 | 418.7k / -109.1k | 50 (NQ line) | 0.92 / 0.57 / 0.92 | 0/312 + 0/301 |
| C10 | T14_S_s50_t1.5_n14 | -0.17 [-0.15] | -0.04 / +0.17 / -0.03 | 15.9k (36) | 16.6k (55) | 595.3k [53% vs nan%] | n/a | n/a | n/a | 0.91 / n/a / n/a | not tested |
| C11 | FOURTH_R4_k2.0_H60_8lots | -0.10 [-0.05] | -0.13 / -0.01 / +0.07 | -23.3k (36) | -21.0k (55) | -625.1k [19% vs 15%] | -1.90 / -1.96 | 244.6k / 221.9k | 50 (NQ line) | 0.00 / 0.22 / 0.36 | not tested |
| C12 | FOURTH_R2_k1.0_H120_8lots | -0.23 [-0.28] | -0.27 / +0.10 / -0.14 | -3.8k (36) | -9.0k (55) | -468.8k [13% vs 13%] | -1.92 / -1.82 | 259.6k / 173.7k | 50 (NQ line) | 0.00 / 0.16 / 0.99 | not tested |

## Gates and tiers
| id | cell | G2 HOLD>0 | G3 corr<=0.5 | G4 marg>0 WF&HOLD | G5 L25>0 | G6 placebo>=0.95 | G7 2023 span>0 | G8 NT8 identity | M >=3 tr/wk | failed gates | tier | tier if G6 = prior random-entry placebo only |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| C01 | RSI2C_s20 | yes | yes (max +0.10) | yes | yes | NO | yes | yes | NO | G6, M | **DEAD** | DEAD |
| C02 | ES_RSI2_t10 | yes | yes (max +0.23) | yes | yes | NO | yes | yes | NO | G6, M | **DEAD** | CANDIDATE |
| C04 | RSI2T_t10 | yes | yes (max -0.00) | yes | yes | NO | yes | yes | NO | G6, M | **DEAD** | DEAD |
| C05 | IBS_t20_n1 | yes | yes (max +0.04) | yes | yes | NO | yes | yes | NO | G6, M | **DEAD** | DEAD |
| C06 | RTY_IBS_t20_n1 | yes | yes (max +0.06) | yes | yes | NO | NO | yes | NO | G6, G7, M | **DEAD** | DEAD |
| C07 | ORB_ASIA_15_v1_s60 | yes | yes (max +0.24) | NO | NO | NO | NO | NO | NO | G4, G5, G6, G7, G8, M | **DEAD** | DEAD |
| C08 | ORB_ASIA_15_v1_s75 | yes | yes (max +0.16) | yes | NO | NO | NO | NO | NO | G5, G6, G7, G8, M | **DEAD** | DEAD |
| C09 | COMB_c3_R | yes | yes (max +0.04) | yes | yes | NO | yes | yes | NO | G6, M | **DEAD** | CANDIDATE |
| C13 | YM_RSI2_t10 | yes | yes (max +0.18) | yes | yes | NO | yes | yes | NO | G6, M | **DEAD** | CANDIDATE |
| C03 | DIPBUY_RSI2_2lot | yes | yes (max +0.16) | yes | yes | NO | yes | yes | NO | G6, M | **DEAD** | DEAD |
| C10 | T14_S_s50_t1.5_n14 | yes | yes (max +0.17) | NO | yes | NO | NO | NO | NO | G4, G6, G7, G8, M, T1 verdict DEAD inherited (paired CI [-5.9k,20.8k], year share 68%, placebo 0.91) | **DEAD** | DEAD |
| C11 | FOURTH_R4_k2.0_H60_8lots | NO | yes (max +0.07) | NO | NO | NO | NO | NO | yes | G2, G4, G5, G6, G7, G8 | **DEAD** | DEAD |
| C12 | FOURTH_R2_k1.0_H120_8lots | NO | yes (max +0.10) | NO | NO | NO | NO | NO | yes | G2, G4, G5, G6, G7, G8 | **DEAD** | DEAD |
Own risk rules: C01 2xATR catastrophe stop; C07/C08 own T3.2 locks (day -2R/+5R, cap 8R, give-back, week floor); C09 3/1.5-lot trailing-8w rule; others none (no D2 locks apply). C10 is the paired delta of D2 shorts (modifier), not a book.

## Top 10 by the 2.1 target (ranked by WF marginal Sharpe among cells with positive L25 mean)
| rank | cell | Sharpe | corr stack | L25 $/wk | marg WF/HOLD | gates failed | by how much | MDE | forward weeks to settle |
|---|---|---|---|---|---|---|---|---|---|
| 1 | C01 RSI2C_s20 | 1.45 | -0.05 | 23.7k | +0.44/+0.90 | G6, M | G6: shift-placebo rank 0.84 vs 0.95 (prior random-entry 0.92); M: 0.49 vs 3 trades/wk | weekly 13.5k; L25-week mean ~27k | ~135 weeks for the WF mean at 80% power; L25 effect ~40 losing weeks |
| 2 | C03 DIPBUY_RSI2_2lot | 1.73 | -0.01 | 22.6k | +0.33/+1.19 | G6, M | G6: shift-placebo rank 0.57 vs 0.95 (prior random-entry 0.92); M: 0.92 vs 3 trades/wk | weekly 13.5k; L25-week mean ~27k | ~135 weeks for the WF mean at 80% power; L25 effect ~40 losing weeks |
| 3 | C02 ES_RSI2_t10 | 1.74 | +0.05 | 15.2k | +0.33/+1.28 | G6, M | G6: shift-placebo rank 0.44 vs 0.95 (prior random-entry 0.96); M: 0.42 vs 3 trades/wk | weekly 13.5k; L25-week mean ~27k | ~135 weeks for the WF mean at 80% power; L25 effect ~40 losing weeks |
| 4 | C04 RSI2T_t10 | 1.21 | -0.12 | 26.3k | +0.30/+0.30 | G6, M | G6: shift-placebo rank 0.87 vs 0.95 (prior random-entry 0.91); M: 0.39 vs 3 trades/wk | weekly 13.5k; L25-week mean ~27k | ~135 weeks for the WF mean at 80% power; L25 effect ~40 losing weeks |
| 5 | C09 COMB_c3_R | 1.23 | -0.06 | 23.5k | +0.25/+0.78 | G6, M | G6: shift-placebo rank 0.58 vs 0.95 (prior random-entry 0.97); M: 0.98 vs 3 trades/wk | weekly 13.5k; L25-week mean ~27k | ~135 weeks for the WF mean at 80% power; L25 effect ~40 losing weeks |
| 6 | C06 RTY_IBS_t20_n1 | 0.96 | -0.06 | 21.2k | +0.11/+0.50 | G6, G7, M | G6: shift-placebo rank 0.90 vs 0.95 (prior random-entry 0.93); M: 0.91 vs 3 trades/wk | weekly 13.5k; L25-week mean ~27k | ~135 weeks for the WF mean at 80% power; L25 effect ~40 losing weeks |
| 7 | C05 IBS_t20_n1 | 1.16 | -0.09 | 23.3k | +0.10/+0.85 | G6, M | G6: shift-placebo rank 0.34 vs 0.95 (prior random-entry 0.93); M: 0.75 vs 3 trades/wk | weekly 13.5k; L25-week mean ~27k | ~135 weeks for the WF mean at 80% power; L25 effect ~40 losing weeks |
| 8 | C13 YM_RSI2_t10 | 1.14 | +0.00 | 7.2k | +0.03/+1.20 | G6, M | G6: shift-placebo rank 0.42 vs 0.95 (prior random-entry 0.95); M: 0.55 vs 3 trades/wk | weekly 13.5k; L25-week mean ~27k | ~135 weeks for the WF mean at 80% power; L25 effect ~40 losing weeks |

## Direct vs mapped (mbp-10 book walk; 112 symbol-months, 887 legs; ES/RTY before 2023-08 mapped)
| cell | coverage (both legs priced direct) | mapped WF $/wk @ equal risk lots | direct WF $/wk | mapped lots | direct lots | mapped HOLD $/wk | direct HOLD $/wk |
|---|---|---|---|---|---|---|---|
| C01 RSI2C_s20 | 98% | 11.6k | 11.5k | 13.1 | 13.1 | 14.0k | 13.8k |
| C02 ES_RSI2_t10 | 87% | 13.8k | 13.9k | 21.1 | 21.1 | 15.9k | 16.0k |
| C03 DIPBUY_RSI2_2lot | 93% | 13.8k | 13.7k | 9.0 | 8.9 | 16.3k | 16.1k |
| C04 RSI2T_t10 | 97% | 9.7k | 9.6k | 15.8 | 15.8 | 11.6k | 11.5k |
| C05 IBS_t20_n1 | 99% | 9.3k | 9.2k | 9.2 | 9.2 | 12.0k | 12.0k |
| C06 RTY_IBS_t20_n1 | 88% | 7.9k | 7.6k | 36.0 | 36.0 | 11.0k | 10.7k |
| C09 COMB_c3_R | 99% | 9.9k | 9.8k | 10.5 | 10.5 | 12.2k | 12.1k |
Sanity check (D3XT back-adjustment issue): every direct number is a DIFFERENCE of two raw fills of the same contract (no roll inside a trade; roll-crossing trades dropped as in the mapped series), so raw-vs-adjusted offsets never enter. Direct minus mapped per-trade P&L: C01 +$20, C02 +$11, C04 -$2, C05 -$3, C06 +$3, C09 -$14. The 15:56 book is deep: 0.5 tick/side up to 50 lots. Engine (exec_engine_l2 single MKT, 5 ms) and explicit book walk agree exactly.

## Correlation matrix (WF weekly)
| cell | STACK | STACK_PB2 | ST | HM | WT | KB | SM | PB | PB_ST10_SWZ_T3 | DS2 | DS3trio |
|---|---|---|---|---|---|---|---|---|---|---|---|
| C01 RSI2C_s20 | -0.05 | -0.05 | -0.07 | +0.10 | -0.13 | -0.10 | -0.10 | +0.03 | -0.00 | -0.02 | -0.09 |
| C02 ES_RSI2_t10 | +0.05 | +0.05 | -0.01 | +0.23 | -0.08 | -0.02 | -0.14 | +0.11 | +0.08 | +0.08 | -0.04 |
| C04 RSI2T_t10 | -0.12 | -0.12 | -0.12 | -0.00 | -0.14 | -0.11 | -0.02 | -0.06 | -0.06 | -0.11 | -0.10 |
| C05 IBS_t20_n1 | -0.09 | -0.10 | -0.14 | +0.02 | -0.14 | -0.00 | -0.08 | +0.04 | -0.07 | -0.10 | -0.03 |
| C06 RTY_IBS_t20_n1 | -0.06 | -0.08 | -0.10 | +0.03 | -0.07 | -0.11 | -0.05 | +0.06 | -0.05 | -0.06 | -0.05 |
| C07 ORB_ASIA_15_v1_s60 | +0.24 | +0.23 | +0.16 | +0.18 | +0.13 | +0.03 | +0.10 | +0.24 | +0.17 | +0.21 | +0.20 |
| C08 ORB_ASIA_15_v1_s75 | +0.16 | +0.17 | +0.11 | +0.12 | +0.16 | -0.01 | +0.09 | +0.13 | +0.14 | +0.16 | +0.11 |
| C09 COMB_c3_R | -0.06 | -0.05 | -0.07 | -0.01 | -0.10 | -0.04 | -0.03 | +0.04 | +0.05 | -0.07 | -0.02 |
| C13 YM_RSI2_t10 | +0.00 | -0.01 | -0.03 | +0.18 | -0.12 | -0.03 | -0.20 | +0.09 | +0.00 | +0.04 | -0.07 |
| C03 DIPBUY_RSI2_2lot | -0.01 | -0.02 | -0.05 | +0.16 | -0.12 | -0.08 | -0.13 | +0.07 | +0.03 | +0.02 | -0.08 |
| C10 T14_S_s50_t1.5_n14 | -0.17 | -0.20 | -0.19 | -0.30 | -0.01 | -0.04 | +0.17 | -0.03 | -0.13 | -0.25 | +0.04 |
| C11 FOURTH_R4_k2.0_H60_8lots | -0.10 | -0.16 | -0.09 | -0.07 | -0.14 | -0.13 | -0.01 | +0.07 | -0.24 | -0.12 | -0.02 |
| C12 FOURTH_R2_k1.0_H120_8lots | -0.23 | -0.28 | -0.16 | -0.19 | -0.20 | -0.27 | +0.10 | -0.14 | -0.36 | -0.24 | -0.15 |

## Stack losing weeks used (L25, WF label weeks, stack P&L)
| week | stack P&L | | week | stack P&L |
|---|---|---|---|---|
| 202409 | -137.9k | | 202529 | -78.9k |
| 202411 | -250.5k | | 202530 | -205.9k |
| 202413 | -110.7k | | 202533 | -143.5k |
| 202415 | -122.3k | | 202543 | -62.2k |
| 202417 | -116.2k | | 202549 | -63.8k |
| 202418 | -206.2k | | 202552 | -158.4k |
| 202419 | -139.8k | | 202604 | -188.5k |
| 202422 | -76.5k | | 202606 | -54.5k |
| 202426 | -95.5k | | 202609 | -82.0k |
| 202434 | -158.0k | | 202612 | -49.0k |
| 202435 | -50.6k | | 202617 | -90.3k |
| 202440 | -244.8k | | 202621 | -270.0k |
| 202447 | -269.0k | | 202624 | -140.4k |
| 202502 | -111.9k | | 202630 | -58.8k |
| 202518 | -195.0k | | 202632 | -95.5k |
| 202521 | -82.4k | | 202635 | -121.5k |
| 202524 | -109.7k | | 202636 | -161.0k |
| 202528 | -267.1k | | 202637 | -90.7k |
Negative weeks (55): out/CHOP/chop_final.json losing_weeks.WF.LNEG.

## Structural read
Only the entry family was varied. Trend-filtered (SMA200) or IBS dip-buy lowers drawdown; unfiltered RSI2 raises it in crashes. Timing relative to the stack is not significant for marginal Sharpe; the independent mean does the work; L25-week P&L is above chance for 5 cells. Bracket, bar, order, gate, tape axes: not run.

## Power
Weekly MDE 13.5k at equal risk; L25 (36 weeks) mean MDE ~27k/wk; 70-100 WF trades per dip-buy cell: CIs touch zero. Best-of-N (12 add-one cells): best real marginal +0.44 (C01) vs null-max q95 0.91 (rank 0.25).

## Disclosures
One holdout look (track DS3_TCHOP); direct re-pricing re-reads the same window; sleeves were seen on the holdout by earlier tracks. ds3_addbook not called (re-implemented in chop_lib, base KB+SM+PB). ORB, range fades, C10: NT8 identity untested; ORB/range not direct-replayed (DEAD before replay). 6 stop-exit legs priced at the mapped stop bar +30 s. COMB 3-lot cap exceeded at equal risk. YM mapped. Code l2vast/ds3/code/chop_*.py, x_chop*.py; numbers out/CHOP/chop_final*.json; rows rows/DS3_TCHOP.json; series SERIES/DS3_TCHOP__*.parquet. No paper_all registration (no PASS/CANDIDATE).
