# DS3_ORB_ASIA_D7 - the PASS-tier rows we never built: count, ORB_ASIA_15 / 30 and the top-5 rows on the drawdown-first standard (D1, 2026-10-31/11-01)

**POST-HOC re-score of stored cells. Shadow only. No PASS claim is made by this agent; no tier below is a promotion.** Capped label day 20260206, UNTOUCHED never read, no tape/engine import (stored struct48 parquet sliced at load; 1-min bar store <=202602; composite and as-is from the stored DD-1 series, tie-out to DS3_DRAWDOWN exact). Prereg `l2vast/ds3/prereg/D1_ORB_prereg.md` sha256 f13db6a462f826670585e91348ce4751ada11a93ca9518cebf5e50a3815f9710 (in DECISIONS.md before scoring; dead_lookup first: ORB_ASIA_15 NOT FOUND, ORB_ASIA_30 s60 already stored as RE5_STRUCT48 DEAD; cells appended after). Windows L3M 14 / L6M 28 / HOLD 32 / PRE 75 / X' 44 weeks, ALL = 149. Code `l2vast/ds3/code/orb/`, outputs `l2vast/ds3/out/orb/`.

**BOTTOM LINE.** (1) 81 of the 82 PASS-tier rows in the ledgers (71 original, 60 after the cap; 30 exposures) have no D6/D7 implementation; the only identity match is the shipped A6 cell. (2) ORB_ASIA_15 s60 holds **CANDIDATE-RECENT, inherited post-hoc** (struct48 verdict after the cap: CANDIDATE, year share 0.65): re-scored with selection on PRE+X' only it FAILS (X' -$186 per contract-week; shuffled-day opening ranges beat it before mid-2025), the one recent look is +$545 (HOLD, inside MDE 759), long trades only. (3) At live-scale lots it is small and not a hedge: +0.7 to +3.5k/wk at 1-5 lots (inside MDE), deeper PRE/ALL tails (17.2 SD-matched lots: PRE worst-20 -875 -> -1,120k, equal-risk mean negative in PRE and X'); capacity at 17 lots untested (100% of the thinnest entry minute). D7 cannot host it; spec in section 8 for a new D6-type book, Shadow at 1 lot. (4) The best-supported unbuilt rows are the RSI2 sleeves (STRICT and TOLERANT, ten-year record), also not hostable (overnight, end-of-day entry).

## PAGE 1

### 1. How many PASS-tier rows have no D6/D7 implementation

**81 of 82 PASS-tier rows (original or capped tier == PASS) are NOT BUILT in D6 or D7, in 30 exposures** (one row is the shipped A6 = PB7_PB5_depth_atr0.5_W15_s+0 and is the only identity match; it is itself CANDIDATE after the cap). Build status is by identity: shipped A6 cell, the three monitor-only D6 lines (ba2/SM_t60_sst, TB4W_03, ba2/HM_t75_s90) or the five D7 alt-bar identity cells; none of the other PASS rows is any of them. Rows whose ENGINE FAMILY is live (K6/KB, H6/HM, U6/ST, A6/PB7) but whose cell is not the shipped one are counted NOT BUILT and flagged in Appendix A (family live: 23 rows).

| ledger | PASS rows (original) | PASS rows (after the 20260206 cap) | independent exposures | D6/D7 built |
|---|---|---|---|---|
| RECENT_WINS (tier column; positive-L3M view) | 8 | 1 (re-tiered by exposure: ORB x4, ES RSI2 x2, RSI2 x1 -> CANDIDATE; RSI2C stays PASS) | 5 (ORB s60, ORB s75, ES RSI2_t10, RSI2C_s20, NQ RSI2_t10) | 0 of 8 |
| STRUCT48 leaderboard (T3 / NM_B / NM_E rows) | 18 | 5 (4 RSI2C/RSI2CC rows + B01_SetB, which came UP from CANDIDATE) | 6 -> 2 (ORB s60, ORB s75, NQ RSI2_t10, ES RSI2_t10, GSHORT_t90, RSI2C/CC  ->  RSI2C/CC and Set B) | 0 |
| other programs in the capped rerun (PRO1 PRO2 PRO3 TA1 TPULLBACK TPULLBACK4 TR1 TR2) | 53 | 55 | 23 families | 1 (A6 cell: orig PASS, capped CANDIDATE) |
| **union** | **71** | **60** | **30 exposures (approx., same-stream rows merged by name)** | **1 of 82 rows** |

**Top 5 by SHRUNK $** (shrunk $ = 0.25 x min(capped WF, capped HOLD) per contract-week; 0.25 = the ratio RECENT_WINS itself applies to the one PASS family with a non-zero shrink, ES_RSI2 12,281 / 49,807; every other PASS row carries 0.00 in the ledger SHRUNK column, so the ledger cannot rank them). Program cells are at 10 lots on the MAPPED basis (known to flatter vs measured/direct), sleeves per contract on the struct48 measured-cost basis; the two groups are therefore ranked and shown separately and not mixed.

| group | # | exposure | best cell | tier orig -> capped | capped WF / HOLD (program-native $/wk) | shrunk $ per contract-week | D6/D7 mapping |
|---|---|---|---|---|---|---|---|
| program (mapped, 10 lots) | 1 | TR Donchian (15/30m) | TR3_DON15_S (= TRW_DON15m_n20_S, identical series) | PASS -> PASS | 19,705 / 24,591 | 493 | NOT hostable in D7 (no Donchian slot); needs a D6-type book |
| program (mapped, 10 lots) | 2 | TB4 alt-bar pullback (volume) | TB4W_10_volume_500_ST10_E20_1_T1_nvolume00 | PASS -> PASS | 19,253 / 25,699 | 481 | D7 has the volume-bar + Supertrend slot, but not the EMA20 pullback entry (E20_1, T1): partial, needs an entry-mode slot |
| program (mapped, 10 lots) | 3 | TB4 alt-bar pullback (time) | TB4A_time_03_time_30s_ST3_SW38_T2 | PASS -> PASS | 16,875 / 20,068 | 422 | D7 30-s bar + Supertrend yes; pullback entry no: partial |
| program (mapped, 10 lots) | 4 | PB HMA55 pullback (H6 family) | PB7_PB_HMA55_EMA1_T2_W60_s-3 | PASS -> PASS | 16,287 / 19,297 | 407 | family live as H6 (HM); this cell (PB7 widening, W60 s-3) is not the shipped one; D6 property change |
| program (mapped, 10 lots) | 5 | PB7 depth-ATR0.5 (A6 family) | PB7_PB5_depth_atr0.5_W15_s-3 | PASS -> PASS | 15,399 / 20,197 | 385 | family live as A6; this cell (W15 s-3) differs from shipped W15 s+0 by the level shift: one D6 parameter |
| sleeve (struct48, per contract) | 1 | NQ RSI2_t10 | E:NQ_RSI2_t10 | PASS -> CANDIDATE | stand WF/HOLD per contract: 938 / 949 | 235 | not hostable in D7 (no RSI / opening-range slot; see section 8) |
| sleeve (struct48, per contract) | 2 | NQ RSI2 combo (RSI2C/RSI2CC s20) | E:NQ_RSI2C_s20 | PASS -> PASS | stand WF/HOLD per contract: 773 / 910 | 193 | not hostable in D7 (no RSI / opening-range slot; see section 8) |
| sleeve (struct48, per contract) | 3 | ES RSI2_t10 | E:ES_RSI2_t10 | PASS -> CANDIDATE | stand WF/HOLD per contract: 649 / 857 | 162 | not hostable in D7 (no RSI / opening-range slot; see section 8) |
| sleeve (struct48, per contract) | 4 | ORB Asia 15 s75 | E:ORB_ASIA_15_v1_s75 | PASS -> CANDIDATE | stand WF/HOLD per contract: 260 / 747 | 65 | not hostable in D7 (no RSI / opening-range slot; see section 8) |
| sleeve (struct48, per contract) | 5 | ORB Asia 15 s60 | ORB_ASIA_15_v1__s60@0.5 | PASS -> CANDIDATE | stand WF/HOLD per contract: 257 / 554 | 64 | not hostable in D7 (no RSI / opening-range slot; see section 8) |
| sleeve (struct48, per contract) | 6 | NQ GSHORT_t90 | GSHORT_t90 | PASS -> CANDIDATE | stand WF/HOLD per contract: 207 / 422 | 52 | not hostable in D7 (no RSI / opening-range slot; see section 8) |

The deep-dive below covers ORB_ASIA_15 / ORB_ASIA_30 in full (sections 3-8) and the other top rows at the same measures in section 9 (sleeves: NQ RSI2_t10, RSI2C_s20, ES RSI2_t10, GSHORT_t90; programs: the five cells above).

### 2. The honest tier of ORB_ASIA_15 (60-pt stop) and the 30-min candidate

| gate (prereg order) | ORB_ASIA_15 s60 (lead) | ORB_ASIA_15 s75 | ORB_ASIA_30 s60 (CANDIDATE) |
|---|---|---|---|
| S1 selection windows only: per-contract mean > 0 in PRE **and** X' (LIVE-CAL $/ct/wk) | **NO** (PRE 114, X' -186) | NO (35, -321) | NO (79, -328) |
| S2 same-volume placebo >= 0.95 on PRE+X' (random-time / shuffled-day opening ranges, 200 draws each) | **NO** (0.76 / 0.15) | NO (0.47 / 0.01) | NO (0.49 / 0.00) |
| S3 neighbours (other OR length, other stop) same sign in PRE and X' | NO (no neighbour is positive in both: ASIA_15 s50 PRE -642 / X'-era +944, s75 +677 / -3,285, ASIA_30 s60 +1,292 / -3,909, unit-lot $/wk) | NO | NO |
| ONE recent look: HOLD per-contract $/ct/wk (t; 95% block CI) | +545 (t 2.0; 267 to 1,052) inside MDE 759 | +739 (t 2.7) | +640 (t 2.1) |
| descriptive: L6M / L3M | +696 (t 2.4) / +686 (t 1.4) | +742 / +597 | +805 / +904 |
| year-share gate (largest calendar-year share of the WF gain <= 0.60, capped) | **FAIL 0.66** (2025 carries it; ties to the capped rerun 0.65) | FAIL 0.75 | FAIL 0.71 |
| STRICT / TOLERANT / NOW-ONLY (T-SIXTY addendum, per contract AND stack at 3 lots) | NO / NO (fails PRE worst-20 not worse) / yes | NO / NO / yes | NO / NO / yes |
| **tier (this agent, post-hoc)** | **CANDIDATE-RECENT, INHERITED POST-HOC** | CANDIDATE-RECENT | CANDIDATE-RECENT (and already DEAD in RE5_STRUCT48) |

**Plain reading.** The struct48 PASS (and the capped CANDIDATE, year-share 0.65) is a RECENT result: the cell was chosen among 644 cells on windows that include 2025-26. With selection on PRE and X' only, 3 of the 36 stored ORB cells (of 54 T3.2 rule-stop cells; unit = 14 lots) pass PRE>0 and X'>0 (NY_30_v0_s75, ASIA_15_v0_s50, ASIA_30_v0_s50) and none of the 3 has a positive HOLD (HOLD -7.4k, -0.7k, -1.3k $/wk at unit lots), while the volume-filtered Asia cells that win the recent look have a NEGATIVE X'. The per-contract edge is +$686 / +$696 / +$545 per contract-week in L3M / L6M / HOLD, +$114 in PRE and -$186 in X'; long trades earn it (66 longs +$24.9k per contract over the sample, 64 shorts -$7.1k); the five best HOLD trades are 51% of the HOLD gain; random-time trades rank 0.99-1.00 against it in HOLD/L6M but 0.76 in PRE+X', and shuffled-day opening ranges do BETTER than the real ones in PRE+X' (rank 0.15) and worse only in the recent windows (rank 1.00). That is a regime/direction result of 2025-26, not an opening-range-placement edge that existed before.

### 3. Risk table: ORB_ASIA_15 s60 (LIVE-CAL) added to the Sunday composite and to the as-is stack at live-scale lots

Per-contract LIVE-CAL series (stop 2.45 pt, target at level, $4.84 RT) x lots, added to the stored composite (COMP|off: six pieces, K6 2 / P6 7 / U6 4 / H6 4+2 / M6 2 / A6 1, split 70/30, no combined lock) and as-is (ASIS|off). maxDD = weekly-cumulative peak-to-trough ($k); worst-20 = sum of the 20 worst weeks ($k; n/a in windows with fewer than 20 losing weeks, tail claims rest on PRE, X', ALL); `*` = beyond MDE; EQUAL-RISK = base+sleeve scaled by one factor c so the ALL-window worst-20 equals the base's, change in ALL mean. **SD-matched lot = 17.2 NQ lots** (0.5 x the as-is stack's WF weekly SD 51.4k / the sleeve's 1.49k per contract; literal 0.5 x Set A's report-scale SD 104.5k would be 35 lots, struct48's own row says 33.8; 1.0 x = 34 / 67.7 lots).

**vs the Sunday composite**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +0.7 (0.8) | 23 -> 23 | 241 -> 243 | 121 -> 121 | 241 -> 243 | -875 -> -884 | -420 -> -422 | -1,098 -> -1,101 | 50.3 -> 50.7 | 0.09 -> 0.09 | +0.1 |
| 2 | +1.4 (1.6) | 23 -> 23 | 241 -> 245 | 121 -> 121 | 241 -> 245 | -875 -> -895 | -420 -> -426 | -1,098 -> -1,107 | 50.3 -> 51.2 | 0.09 -> 0.09 | +0.0 |
| 3 | +2.1 (2.4) | 23 -> 23 | 241 -> 247 | 121 -> 121 | 241 -> 247 | -875 -> -905 | -420 -> -430 | -1,098 -> -1,114 | 50.3 -> 51.6 | 0.09 -> 0.09 | +0.0 |
| 5 | +3.5 (4.1) | 23 -> 23 | 241 -> 251 | 121 -> 122 | 241 -> 251 | -875 -> -926 | -420 -> -438 | -1,098 -> -1,133 | 50.3 -> 52.7 | 0.09 -> 0.09 | -0.1 |
| **17.2** (SD 0.5x as-is) | +12.0 (14.0) | 23 -> 23 | 241 -> 276 | 121 -> 153 | 241 -> 276 | -875 -> -1,120 | -420 -> -518 | -1,098 -> -1,333 | 50.3 -> 61.4 | 0.09 -> 0.09 | -2.2 |

**vs the as-is stack**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +0.7 (0.8) | 88 -> 86 | 162 -> 165 | 317 -> 324 | 317 -> 324 | -811 -> -819 | -572 -> -574 | -1,161 -> -1,166 | 47.2 -> 47.6 | 0.04 -> 0.04 | +0.1 |
| 2 | +1.4 (1.6) | 88 -> 84 | 162 -> 169 | 317 -> 331 | 317 -> 331 | -811 -> -829 | -572 -> -576 | -1,161 -> -1,174 | 47.2 -> 48.1 | 0.04 -> 0.04 | +0.1 |
| 3 | +2.1 (2.4) | 88 -> 83 | 162 -> 172 | 317 -> 338 | 317 -> 338 | -811 -> -842 | -572 -> -579 | -1,161 -> -1,183 | 47.2 -> 48.6 | 0.04 -> 0.04 | +0.1 |
| 5 | +3.5 (4.1) | 88 -> 79 | 162 -> 179 | 317 -> 352 | 317 -> 352 | -811 -> -868 | -572 -> -586 | -1,161 -> -1,203 | 47.2 -> 49.6 | 0.04 -> 0.04 | +0.1 |
| **17.2** (SD 0.5x as-is) | +12.0 (14.0) | 88 -> 57 | 162 -> 219 | 317 -> 440 | 317 -> 440 | -811 -> -1,073 | -572 -> -677 | -1,161 -> -1,379 | 47.2 -> 58.5 | 0.04 -> 0.03 | -0.3 |

**Reading.** Added at 1-5 lots the sleeve is small against a stack with 51k/wk weekly SD: it adds +0.1 to +0.6k/wk (ALL) and +0.7 to +3.5k/wk in L6M, all inside MDE, leaves the L6M maxDD unchanged (the composite's L6M maxDD is one week), deepens the ALL maxDD by 2-10k and the PRE worst-20 by 9-51k (composite -875k), and X' by 2-18k. At the SD-matched 17 lots it adds +12.0k/wk in L6M (MDE 14.0k, not beyond), but PRE maxDD +15% (241 -> 276k), PRE worst-20 +28% (-875 -> -1,120k), X' maxDD +26% (121 -> 153k), ALL worst-20 -1,098 -> -1,333k, ALL SD 50.3 -> 61.4k and the equal-risk mean is NEGATIVE in PRE and X' (-2.5k, -4.0k): at equal risk it does not help outside the last 12 months. Weekly correlation with the composite 0.28 (ALL), 0.40 (PRE), but 0.44 inside the composite's 20 worst weeks (sleeve earns -3.1k per contract summed over them: not a hedge); vs the as-is 0.28 / worst-20 0.10.

**Capacity / lot reality.** 17 lots is 86% of the live 20-lot book cap, one 60-pt stop = $20.6k + costs (8.6x the K6 2-lot R of $2.4k), and 9% of the median entry-minute NQ volume (194 contracts), 24% of the 10th percentile (72) and 100% of the thinnest entry minute (17); 71 of 134 entries are the Sunday-evening open. 1-5 lots are executable; the SD-matched size is not recommended (section 7).

**What is inherited (post-hoc) vs fresh:** inherited = the choice of Asia / 15-min / volume filter on / 60-pt stop / 1.5R target among 644 STRUCT48 cells selected on WF+holdout windows that include 2025-26, the sizing ratios, the Set-A-SD sizing convention; fresh here = the selection re-score on PRE+X' only, the ONE recent look (HOLD), the placebos, the cost bases, the risk tables. Because the recent look is the only look it is still not a clean holdout (the cell was already chosen on it); a clean test is the forward Shadow log.

---

## DETAIL

### 4. The definition, restated exactly from the struct48 code (`struct48/code/t32lib.py` gen_orb / sim_orders / run_sim / sleeve; rule registry RULES[ORB_ASIA_15_v1] = open_hm 1080, Lmin 15, volon True; cell suffix `__s60` = 60-pt stop)

* **Instrument / clock:** NQ continuous, 1-minute bars stamped by bar START in ET; label day = 18:00 ET (previous calendar day) to 17:59 ET (Sunday 18:00 opens Monday's label day). HM = minutes since midnight ET.
* **Opening range:** the bars whose start is in [18:00, 18:15) ET of each label day (30-min cell: [18:00, 18:30)); needs at least max(2, L/2) bars and a span < L+2 minutes, else no trade that day. OR high = max High, OR low = min Low, OR volume = sum of the bars' volume.
* **Volume filter ("v1" = on):** trade only if OR volume >= 1.5 x the mean OR volume of the previous 20 label days that had a valid OR (needs 20 such days). ("v0" = filter off; the PASS/CANDIDATE rows are all v1; v1 trades 0.84/wk, v0 4.9/wk.)
* **Trigger:** scan 1-minute bars from the first bar after the window (start 18:15; first eligible CLOSE is at 18:16:00 for the 15-min cell, 18:31:00 for the 30-min cell) to the end of the label day, entry bar must start before 15:00 ET or at/after 18:05 ET (the 15:00-18:05 zone is blocked and ends the scan): the first bar whose **close** is above the OR high -> long, below the OR low -> short. One signal per label day.
* **Entry:** market order at the signal bar's close (decision epoch = bar end); modelled fill = first trade-second at/after T+1 s, reference price = open of the next 1-min bar, 0.995 pt slippage against. One position at a time across days (a signal while a position is open is skipped).
* **Stop:** 60 pt from the reference price (stop-market), modelled exit at the stop - 1.01 pt (stored harness; LIVE-CAL replaces 1.01 by 2.45 pt / Native 1.28).
* **Target:** 1.5 x stop = 90 pt, limit at the level, filled only when price trades 0.25 pt (1 tick) through it and not in the entry second.
* **Flatten:** first bar starting at/after 16:55 ET (and before 18:00) after the entry bar -> market out at that second's close - 0.995 pt (2 of 134 exits); a gap > 5 minutes exits at the last close (3 of 134). Typical life: stop or target hit within hours; the position is carried overnight until then and until 16:55 ET of the label day at the latest.
* **Costs / units:** net per contract = points x $20 - $4.84 round trip (FEES NQ); the stored points already carry the 0.995 pt entry and the 1.01 pt stop slippage. The sleeve was run through the firm lock engine (Ctx) with its own day/week locks: none ever fired on this stream (locked = unlocked series). Unit series = 14 lots; the "@0.25 / 0.5 / 1.0" rows scale it so the sleeve's weekly SD is that fraction of Set A's: for s60 that is **16.9 / 33.8 / 67.7 NQ lots** (k = 1.208 / 2.416 / 4.833 x 14).

**Reproduction (independent code, 1-min bar store, `orb_lib.py`):** signals re-generated with the identical rule and simulated on 1-minute bars (stop-before-target inside one minute). Entry minute, side and exit type match the stored trades on 119 of 120 (ASIA_15 s60/s75) and 113 of 113 (ASIA_30 s60) trades from 2023-05-02, mean absolute difference 0.03-0.08 pt per trade; 7-8 stored trades per cell are missing from the re-generation, all on contract-roll weeks (2023-06-26, 2023-09-18/25/28, 2024-12-18/19, 2025-12-22, 2026-01-12) where the bar store carries one contract's volume and the 20-day OR-volume filter flips. The stored trades, not the re-generation, are the series scored in sections 3, 5-7; the re-generation is the placebo simulator.

### 5. Per-contract L3M / L6M / HOLD / PRE / X' / ALL on the capped windows, fills, and the 30-min cell

LIVE-CAL = stop 2.45 pt, target at the level (correction 0), $4.84 RT. $ per contract per week (weekly t; MDE = 2.8 x SE of the weekly mean; 95% 4-week block CI); trades per week 0.8-1.0.

| cell | window | weeks | trades | pts/trade | $/trade | $/ct/wk | t | MDE | 95% CI | win rate |
|---|---|---|---|---|---|---|---|---|---|---|
| ASIA_15 s60 | L3M | 14 | 14 | 34.6 | 686 | 686 | 1.36 | 1,411 | 469 to 1,395 | 0.64 |
| ASIA_15 s60 | L6M | 28 | 23 | 42.6 | 847 | 696 | 2.40 | 812 | 335 to 1,114 | 0.70 |
| ASIA_15 s60 | HOLD | 32 | 27 | 32.5 | 646 | 545 | 2.01 | 759 | 267 to 1,052 | 0.63 |
| ASIA_15 s60 | PRE | 75 | 66 | 6.7 | 129 | 114 | 0.68 | 470 | -247 to 468 | 0.45 |
| ASIA_15 s60 | X' | 44 | 37 | -10.8 | -222 | -186 | -1.25 | 419 | -372 to 28 | 0.32 |
| ASIA_15 s60 | ALL | 149 | 130 | 7.1 | 137 | 119 | 1.06 | 316 | -76 to 363 | 0.45 |
| ASIA_15 s60 | WF | 106 | 93 | 14.2 | 279 | 245 | 1.69 | 406 | -20 to 556 | 0.51 |
| ASIA_15 s75 | L3M | 14 | 14 | 30.1 | 597 | 597 | 1.25 | 1,333 | 260 to 1,524 | 0.57 |
| ASIA_15 s75 | L6M | 28 | 23 | 45.4 | 904 | 742 | 2.45 | 847 | 312 to 1,206 | 0.65 |
| ASIA_15 s75 | HOLD | 32 | 27 | 44.0 | 876 | 739 | 2.73 | 757 | 383 to 1,205 | 0.63 |
| ASIA_15 s75 | PRE | 75 | 66 | 2.2 | 39 | 35 | 0.17 | 581 | -390 to 461 | 0.42 |
| ASIA_15 s75 | X' | 44 | 37 | -18.8 | -381 | -321 | -1.74 | 516 | -558 to -97 | 0.30 |
| ASIA_15 s75 | ALL | 149 | 130 | 4.9 | 93 | 81 | 0.61 | 375 | -176 to 378 | 0.43 |
| ASIA_15 s75 | WF | 106 | 93 | 14.3 | 282 | 248 | 1.45 | 477 | -65 to 643 | 0.48 |
| ASIA_30 s60 | L3M | 14 | 14 | 45.4 | 904 | 904 | 1.74 | 1,456 | 325 to 1,411 | 0.71 |
| ASIA_30 s60 | L6M | 28 | 23 | 49.2 | 980 | 805 | 2.35 | 958 | 315 to 1,140 | 0.74 |
| ASIA_30 s60 | HOLD | 32 | 27 | 38.2 | 759 | 640 | 2.06 | 870 | 172 to 1,069 | 0.67 |
| ASIA_30 s60 | PRE | 75 | 64 | 4.9 | 92 | 79 | 0.46 | 476 | -259 to 387 | 0.45 |
| ASIA_30 s60 | X' | 44 | 32 | -22.3 | -450 | -328 | -1.81 | 507 | -594 to -63 | 0.25 |
| ASIA_30 s60 | ALL | 149 | 123 | 5.1 | 97 | 80 | 0.65 | 345 | -164 to 316 | 0.45 |
| ASIA_30 s60 | WF | 106 | 91 | 14.7 | 290 | 249 | 1.62 | 431 | -31 to 520 | 0.52 |

**By cost basis (ASIA_15 s60, $/contract/week):** the basis matters little because only 30-50% of exits are stops and target exits carry the larger haircut only in M/LIVE-P9.

| window | STORED (struct48; = N basis) | M (target haircut 1.4/1.5/4.2/4.3 pt) | LIVE-P9 (M + stop 2.45) | **LIVE-CAL (stop 2.45, no haircut)** | LIVE-CAL-NATIVE (stop 1.28) |
|---|---|---|---|---|---|
| L3M | 697 | 642 | 632 | **686** | 695 |
| L6M | 703 | 655 | 648 | **696** | 702 |
| HOLD | 554 | 509 | 500 | **545** | 552 |
| PRE | 127 | 107 | 94 | **114** | 125 |
| X' | -172 | -179 | -194 | **-186** | -175 |
| ALL | 132 | 110 | 98 | **119** | 130 |
| WF | 257 | 230 | 217 | **245** | 255 |

**Stop-order entry (post-hoc sensitivity, 1-min bar sim, not the researched spec):** resting stop order at the OR level instead of a market order after the bar closes beyond it (fill = level + 0.995 pt, same 60/90 bracket, ambiguous both-sides minutes skipped): ASIA_15 s60 $/ct/wk L3M 433 / L6M 460 / HOLD 434 / PRE 131 / X' 70 / ALL 180; ASIA_30 s60 787 / 720 / 133 / -123 (L6M / HOLD / PRE / X'). The stop-order version is LOWER in the recent windows (HOLD 434 vs 545) and POSITIVE in X' (+70, 1-minute-bar resolution, so only indicative): market-after-close entries pay for confirmation and gain in the recent trend. It is a different rule (entry earlier and at the level) chosen after seeing the table: LABELLED POST-HOC, no tier.

**Where the money is (ASIA_15 s60, LIVE-CAL, per contract, label years):** 2023 -$6.7k (31 trades), 2024 +$4.0k (48), 2025 +$17.1k (44), 2026 to 02-06 +$3.3k (7); longs +$24.9k (66 trades, +$377 each), shorts -$7.1k (64, -$111 each); Sunday-evening opens 68 trades +$7.9k, Mon-Thu opens 62 trades +$9.8k.
WF-window (20240201..20260206) calendar-year shares of the per-contract gain: ASIA_15 s60 {2024: 0.214, 2025: 0.659, 2026: 0.126}, s75 {2024: 0.092, 2025: 0.749, 2026: 0.159}, ASIA_30 s60 {2024: -0.015, 2025: 0.708, 2026: 0.307}; maximum 0.66 / 0.75 / 0.71 against the 0.60 gate (STORED basis 0.649 / 0.735 / 0.694: ties to the capped rerun's 0.65 / 0.73 / n/a).

### 6. Selection re-score (PRE+X' only, ONE recent look), multiplicity and placebos

**Stored rows, all 36 ORB cells of T3.2 (unit = 14 lots, $/wk):** PRE>0 in 19, X'-era (stored IS 2023-02..2024-01)>0 in 17, both in 3 (ORB_NY_30_v0_s75: PRE +7.3k / IS +0.7k / HOLD -7.4k; ORB_ASIA_15_v0_s50: +3.4k / +1.1k / -0.7k; ORB_ASIA_30_v0_s50: +3.4k / +0.1k / -1.3k), and HOLD>0 in 18 (PRE>0 and HOLD>0 in 9; X'-era>0 and HOLD>0 in 6; all three positive in NONE of the 36). Of the 12 ASIA cells 2 pass PRE+X' and 9 have HOLD>0. The volume-filtered ASIA cells (v1) that carry the recent result: ASIA_15_v1_s60 PRE +1.8k / IS -2.6k / HOLD +5.1k; ASIA_15_v1_s75 +0.7k / -3.3k / +7.5k; ASIA_30_v1_s60 +1.3k / -3.9k / +5.6k. Selecting on PRE+X' picks cells whose HOLD is <= 0; the cells with a good HOLD were reachable only through the recent windows.

**Same-volume placebos (200 draws, seeds 0..199; the same bar simulator and LIVE-CAL cost for real and placebo; trade windows start 2023-05-02 so the 20-day volume filter has history).** P-A = each real trade replaced by one with the same direction at a uniformly random allowed minute of a random label day of the same quarter; P-B = shuffled-day opening ranges (each day's OR high/low offsets taken from a random day of the same year, real day's volume-filter flag kept). Cell = rank of the real per-contract weekly mean among the 200 placebo means (>= 0.95 passes).

| cell | placebo | PRE+X' | X' | PRE | HOLD | L6M | L3M | ALL (from 05-02) |
|---|---|---|---|---|---|---|---|---|
| ASIA_15 s60 | P-A random time | 0.76 | 0.33 | 0.86 | 0.99 | 1.00 | 0.97 | 0.97 |
| ASIA_15 s60 | P-B shuffled-day OR | 0.15 | 0.21 | 0.23 | 1.00 | 1.00 | 1.00 | 0.83 |
| ASIA_15 s75 | P-A random time | 0.47 | 0.21 | 0.74 | 1.00 | 0.99 | 0.93 | 0.92 |
| ASIA_15 s75 | P-B shuffled-day OR | 0.01 | 0.01 | 0.03 | 1.00 | 1.00 | 1.00 | 0.36 |
| ASIA_30 s60 | P-A random time | 0.49 | 0.09 | 0.81 | 1.00 | 1.00 | 0.98 | 0.91 |
| ASIA_30 s60 | P-B shuffled-day OR | 0.00 | 0.01 | 0.00 | 0.92 | 0.95 | 0.99 | 0.01 |

Placebo means (ASIA_15 s60, $/ct/wk): P-A PRE+X' -56 (real 30), HOLD -28 (real 545); P-B PRE+X' 95 (shuffled ORs earn MORE than the real ones before mid-2025), HOLD 61. **Added to the composite at 3 lots** (delta mean ALL / maxDD ALL rank among 200): P-A 0.97 / 0.63; P-B 0.83 / 0.00 (rank_dd = share of placebos with a SMALLER maxDD change; a risk claim would need <= 0.05): no risk claim. Reading: the real rule beats random timing (P-A) only in the recent windows; before mid-2025 neither random timing nor the real opening range placement is distinguishable from shuffled ranges, i.e. no OR-specific information; the recent edge is the direction (long) of a trending NQ in the Asia/Sunday open after volume spikes.

### 7. Correlation, the stack's worst weeks, capacity

| base | corr ALL | PRE | X' | L6M | HOLD | corr inside the base's 20 worst weeks (ALL) | sleeve $ per contract summed over those 20 weeks (base sum) | sleeve +/-/0 weeks |
|---|---|---|---|---|---|---|---|---|
| COMP/off | 0.28 | 0.40 | -0.09 | -0.11 | 0.10 | 0.44 | -3,132 (-1,098k) | 4/8/8 |
| ASIS/off | 0.28 | 0.38 | 0.03 | -0.12 | 0.11 | 0.10 | -4,406 (-1,161k) | 4/9/7 |
| COMP/12R | 0.26 | 0.35 | -0.02 | -0.07 | 0.08 | -0.08 | -1,522 (-688k) | 5/6/9 |
| ON/off | 0.27 | 0.39 | -0.05 | -0.10 | 0.11 | 0.16 | -5,679 (-1,088k) | 5/9/6 |

The sleeve does not make money in the stack's bad weeks (slightly negative in the composite's 20 worst), and its own 20 worst weeks (-$33k per contract summed) coincide with composite weeks that sum to +$39k: independent, not a hedge.

**Capacity (ASIA_15 s60 entries, NQ volume in the fill minute / next 5 minutes, contracts):** all entries n=128: median 194 / 818, 10th pct 72 / 342, minimum 17; Sunday-evening opens (n=68) median 198, 10th pct 71; stop-exit minute median 484. Share of the fill-minute volume: 1 lot 0.5% / 5 lots 2.6% / 17 lots 8.8% (median), 17 lots = 24% of the 10th percentile and 100% of the thinnest entry. The market-order fill cost used (0.995 pt) was measured on 1-5 lot style clips; no calibration exists for 17+ lots at 18:16 ET Sunday. Entry minute: median 18:39 ET (25th pct 18:25, 75th pct 19:27); 84 of 134 entries are in the 18:00 hour, 71 are Sunday evenings.

### 8. The exact NT8 specification (for a new D6-type book; D7 slots cannot host it)

**Name (proposal): `OA6`, a new D6-style book (NinjaScript Strategy, one instance), Shadow log only at 1 lot first.** All values are the researched ones; nothing is tuned.

| item | specification |
|---|---|
| instrument / data | NQ front month, continuous MergeBackAdjusted, Globex trading-hours template (18:00 ET open, 17:00 ET close), **1-minute time bars (Minute, 1)**, Calculate = OnBarClose, time = ET, bar stamped by END time in NT8 (bar start = Time[0] - 1 min). BarsRequired >= 22 sessions of 1-minute data (the volume filter needs the previous 20 opening ranges). |
| session / label day | label day = 18:00 ET to 17:59 ET (Sunday 18:00 starts Monday's label day); runs every Globex day (Sun-Thu evening opens). |
| opening window | the 15 one-minute bars STARTING 18:00..18:14 ET (bars with end time 18:01..18:15). 30-min cell: 30 bars 18:00..18:29. Require >= 7 bars (15-min) / 15 bars (30-min) present within L+1 minutes of the first, otherwise no trade today. Record OR_high = max High, OR_low = min Low, OR_vol = sum Volume. |
| volume filter | trade only if OR_vol >= 1.5 x mean(OR_vol of the previous 20 label days that had a valid OR); fewer than 20 valid days = no trade. (State kept in an array persisted across sessions, or recomputed from history on start.) |
| trigger | from the bar that ENDS at 18:16 (first bar after the window; 18:31 for the 30-min cell) until the last bar before 15:00 ET (no signal if the NEXT bar would start in 15:00-18:04 ET): first bar whose Close > OR_high -> long, Close < OR_low -> short, evaluated once per bar close. One signal per label day. |
| entry mechanic | **market order submitted at the signal bar's close** (NT8: EnterLong/EnterShort Market in OnBarUpdate with OnBarClose); modelled fill = open of the next minute + 0.995 pt against. One position at a time across days: ignore signals while a position is open. A resting stop order at the OR level is a DIFFERENT rule (section 5, post-hoc). |
| stop | stop-market 60 pt from the reference price (next-bar open ~ fill price); LIVE-CAL assumption 2.45 pt slippage on a JoinThenMarket stop (Native stop-market 1.28; D6 stop parity by day of month as coded). |
| target | limit 90 pt (= 1.5 x stop) from the reference price, resting limit (modelled as filled when price trades 1 tick through). |
| time exit / flatten | market flatten at 16:55 ET (first bar starting at/after 16:55 ET) of the label day if neither bracket was hit: **the position is carried through the 18:00 ET entry itself overnight, so it may hold up to ~23 h**; this is allowed by the research (D6 flat time 16:55 ET is the same clock) but means no new-day trade can start while a prior one is open. |
| filters | none besides the volume filter and the one-position rule. **D7 group 12 (a) "skip the first 60 min of each session" must NOT apply** (all entries are in the first 2 hours of the Asia session: median 18:39 ET); like O6 it needs an exemption. The 15:00-18:05 ET entry block is respected (no signals there). |
| lots / governor | Shadow = 1 lot (paper rows `taken=0`); any live sizing 1-3 lots from the risk table; BookR = lots x 60 pt x $20 ($1,200/lot) for the D6 day/week locks. |
| log fields (for the forward register) | label day, OR_high/low/vol, 20-day mean OR_vol, volume-filter flag, signal time, side, planned lots, fill, stop, target, exit type/time, slippage vs model. Missing state is logged blank with a reason, never as "no signal". |

**Can the D7 slots host it? No.** D7 v1.0 has generic alt-bar slots for Supertrend / Keltner / EMA-cross / HMA-VWAP entries on any NT8 bar type (HA optional), group-12 clock filters and the policy file. An opening-range breakout needs (i) a clock-window high/low/volume state, (ii) a 20-session volume-ratio filter and (iii) a once-per-label-day latch with a one-position rule across days; none of those is a D7 entry type, filter or sizer, and the Keltner/Supertrend slots do not reproduce a fixed-window break. It needs either a new D6-type book (`OA6`) or a new D7 slot "ORB (window start, window length, volume ratio, side latch)". Cheapest honest route: a new D6-type book in Shadow with the log schema above, since D6 already owns the lock engine, the 16:55 flatten and the ER/zone/PE state fields.

**Recommendation (not a decision):** Shadow only, 1 lot, forward log from the first Sunday open after 2026-11-01 (Sunday 18:00 ET opens are 71 of 134 historical entries; the first signals arrive within days at ~0.9/week). Do not size beyond 1-3 lots on this evidence (capacity at 17 lots untested, PRE/X' tail deepens, year-share 0.66, selected on the recent window). Judge the forward log with the register rule: theta = 0.5 x the research L6M estimate, W_on = 37.5 x (MDE/est)^2 weeks. With L6M est $696/ct/wk and MDE $812, W_on is ~51 weeks; futility check at ~26 weeks.

### 9. The other top rows, same measures

**9a. Sleeves (struct48; per contract = 1 NQ or 1 ES contract per trade; measured-cost basis of the harness: $14.84 / $29.84 RT incl. 1 tick per side; no stops except RSI2C).** All four hold a position from 15:56 ET to 15:56 ET of the next trading day.

| sleeve | window | weeks | trades | $/ct/wk | t | MDE |
|---|---|---|---|---|---|---|
| NQ RSI2_t10 | L3M | 14 | 11 | 1,347 | 1.75 | 2,150 |
| NQ RSI2_t10 | L6M | 28 | 17 | 1,085 | 1.61 | 1,892 |
| NQ RSI2_t10 | HOLD | 32 | 17 | 949 | 1.60 | 1,661 |
| NQ RSI2_t10 | PRE | 75 | 35 | 921 | 1.45 | 1,782 |
| NQ RSI2_t10 | X' | 44 | 20 | 114 | 0.38 | 847 |
| NQ RSI2_t10 | ALL | 149 | 72 | 701 | 1.97 | 996 |
| NQ RSI2_t10 | OOS13-23 | 535 | 222 | 155 | 2.28 | 191 |
| NQ RSI2C_s20 | L3M | 14 | 11 | 1,347 | 1.75 | 2,150 |
| NQ RSI2C_s20 | L6M | 28 | 17 | 1,040 | 1.49 | 1,961 |
| NQ RSI2C_s20 | HOLD | 32 | 17 | 910 | 1.48 | 1,720 |
| NQ RSI2C_s20 | PRE | 75 | 35 | 704 | 1.54 | 1,278 |
| NQ RSI2C_s20 | X' | 44 | 20 | 114 | 0.38 | 847 |
| NQ RSI2C_s20 | ALL | 149 | 72 | 584 | 2.09 | 782 |
| NQ RSI2C_s20 | OOS13-23 | 535 | 222 | 108 | 1.51 | 201 |
| ES RSI2_t10 | L3M | 14 | 8 | 1,202 | 2.09 | 1,607 |
| ES RSI2_t10 | L6M | 28 | 13 | 979 | 2.27 | 1,209 |
| ES RSI2_t10 | HOLD | 32 | 13 | 857 | 2.25 | 1,068 |
| ES RSI2_t10 | PRE | 75 | 31 | 552 | 1.46 | 1,057 |
| ES RSI2_t10 | X' | 44 | 29 | 210 | 0.92 | 640 |
| ES RSI2_t10 | ALL | 149 | 73 | 524 | 2.41 | 608 |
| ES RSI2_t10 | OOS13-23 | 535 | 212 | 76 | 1.26 | 169 |
| NQ GSHORT_t90 | L3M | 14 | 0 | 0 | nan | 0 |
| NQ GSHORT_t90 | L6M | 28 | 6 | 338 | 1.50 | 630 |
| NQ GSHORT_t90 | HOLD | 32 | 7 | 422 | 1.84 | 641 |
| NQ GSHORT_t90 | PRE | 75 | 22 | 112 | 0.52 | 605 |
| NQ GSHORT_t90 | X' | 44 | 11 | -114 | -0.85 | 377 |
| NQ GSHORT_t90 | ALL | 149 | 40 | 114 | 0.94 | 339 |
| NQ GSHORT_t90 | OOS13-23 | 535 | 2 | 6 | 1.24 | 14 |

| sleeve | S1 (PRE>0 and X'>0) | S2 placebo on PRE+X' (random-day, same count) | S3 neighbours | HOLD (ONE look) | year share (<=0.60) | x2-cost WF per contract | STRICT / TOLERANT / NOW-ONLY | tier (post-hoc) |
|---|---|---|---|---|---|---|---|---|
| NQ RSI2_t10 | yes (PRE 921, X' 114) | **0.945** (PRE alone 0.955) | yes (RSI(2)<5: PRE +458 / X' +96; <15: +1,082 / +510 per contract-wk, my re-derivation from the bar store) | +949 (t 1.6); placebo HOLD 0.955 | 0.606 FAIL by 0.006 | +931 | yes / yes / yes | CANDIDATE-RECENT, closest to LEAD (S2 0.94 vs 0.95); 2013-2023 window +155/ct/wk (t 2.3, 222 trades) inherited from the NM_E OOS |
| NQ RSI2C_s20 (RSI2 + 2.0 x ATR14 stop) | yes (704, 114) | not run separately (stop needs the intraday path; family value 0.94; struct48 stored 0.976) | yes (s15, s25 positive on WF in the stored rows) | +910 (t 1.5) | 0.522 pass | +766 | yes / yes / yes | CANDIDATE-RECENT (STRUCT48 PASS survives the cap) |
| ES RSI2_t10 | yes (552, 210) | not run (the bar store is NQ only; struct48 stored 1.00) | stored WF neighbours agree | +857 (t 2.2) | 0.611 FAIL by 0.011 | +637 | yes / yes / yes | CANDIDATE-RECENT; 2013-2023 +76/ct/wk (t 1.3) |
| NQ GSHORT_t90 | **NO** (PRE 112, X' -114) | 0.705 | stored neighbours agree | +422 (t 1.8; 7 trades) | 0.600 FAIL by 0.0002 | +203 | NO / NO / NO (no L3M trade) | CANDIDATE-RECENT, thin (42 trades since 2023-03; a gate on the STACK's own trailing 4-week P&L) |

Risk when added to the Sunday composite (live scale, per-contract series x lots; `*` beyond MDE). SD-matched lots are 0.5 x the as-is WF SD: NQ RSI2_t10 5.2, NQ RSI2C 6.7, ES RSI2 8.6, GSHORT 15.6 contracts.

**NQ RSI2_t10 vs the Sunday composite**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +1.1 (1.9) | 23 -> 23 | 241 -> 237 | 121 -> 113 | 241 -> 237 | -875 -> -871 | -420 -> -429 | -1,098 -> -1,092 | 50.3 -> 50.3 | 0.09 -> 0.10 | +0.8 |
| 3 | +3.3 (5.7) | 23 -> 23 | 241 -> 228 | 121 -> 99 | 241 -> 228 | -875 -> -861 | -420 -> -448 | -1,098 -> -1,091 | 50.3 -> 51.5 | 0.09 -> 0.11 | +2.3 |
| 5 | +5.4 (9.5) | 23 -> 23 | 241 -> 220 | 121 -> 85 | 241 -> 220 | -875 -> -852 | -420 -> -470 | -1,098 -> -1,096 | 50.3 -> 54.0 | 0.09 -> 0.12 | +3.6 |
| **5.2** (SD 0.5x as-is) | +5.6 (9.8) | 23 -> 23 | 241 -> 219 | 121 -> 84 | 241 -> 219 | -875 -> -852 | -420 -> -472 | -1,098 -> -1,096 | 50.3 -> 54.3 | 0.09 -> 0.12 | +3.7 |

**NQ RSI2C_s20 vs the Sunday composite**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +1.0 (2.0) | 23 -> 23 | 241 -> 237 | 121 -> 113 | 241 -> 237 | -875 -> -871 | -420 -> -429 | -1,098 -> -1,092 | 50.3 -> 50.3 | 0.09 -> 0.10 | +0.7 |
| 3 | +3.1 (5.9) | 23 -> 23 | 241 -> 228 | 121 -> 99 | 241 -> 228 | -875 -> -861 | -420 -> -448 | -1,098 -> -1,091 | 50.3 -> 51.0 | 0.09 -> 0.11 | +1.9 |
| 5 | +5.2 (9.8) | 23 -> 23 | 241 -> 220 | 121 -> 85 | 241 -> 220 | -875 -> -852 | -420 -> -470 | -1,098 -> -1,096 | 50.3 -> 52.6 | 0.09 -> 0.11 | +3.0 |
| **6.7** (SD 0.5x as-is) | +7.0 (13.2) | 23 -> 39 | 241 -> 212 | 121 -> 77 | 241 -> 212 | -875 -> -854 | -420 -> -489 | -1,098 -> -1,106 | 50.3 -> 54.6 | 0.09 -> 0.12 | +3.7 |

**ES RSI2_t10 vs the Sunday composite**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +1.0 (1.2) | 23 -> 23 | 241 -> 238 | 121 -> 114 | 241 -> 238 | -875 -> -869 | -420 -> -425 | -1,098 -> -1,090 | 50.3 -> 50.4 | 0.09 -> 0.10 | +0.7 |
| 3 | +2.9 (3.6) | 23 -> 23 | 241 -> 232 | 121 -> 101 | 241 -> 232 | -875 -> -856 | -420 -> -440 | -1,098 -> -1,085 | 50.3 -> 51.0 | 0.09 -> 0.10 | +1.9 |
| 5 | +4.9 (6.0) | 23 -> 23 | 241 -> 226 | 121 -> 88 | 241 -> 226 | -875 -> -843 | -420 -> -457 | -1,098 -> -1,084 | 50.3 -> 52.1 | 0.09 -> 0.11 | +2.9 |
| **8.6** (SD 0.5x as-is) | +8.4 (10.4) | 23 -> 23 | 241 -> 216 | 121 -> 66 | 241 -> 216 | -875 -> -843 | -420 -> -488 | -1,098 -> -1,099 | 50.3 -> 55.4 | 0.09 -> 0.12 | +4.5 |

**NQ GSHORT_t90 vs the Sunday composite**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +0.3 (0.6) | 23 -> 21 | 241 -> 241 | 121 -> 125 | 241 -> 241 | -875 -> -869 | -420 -> -425 | -1,098 -> -1,094 | 50.3 -> 50.2 | 0.09 -> 0.09 | +0.2 |
| 3 | +1.0 (1.9) | 23 -> 21 | 241 -> 239 | 121 -> 133 | 241 -> 239 | -875 -> -864 | -420 -> -437 | -1,098 -> -1,097 | 50.3 -> 50.2 | 0.09 -> 0.09 | +0.4 |
| 5 | +1.7 (3.1) | 23 -> 21 | 241 -> 238 | 121 -> 141 | 241 -> 238 | -875 -> -873 | -420 -> -449 | -1,098 -> -1,103 | 50.3 -> 50.4 | 0.09 -> 0.10 | +0.5 |
| **15.6** (SD 0.5x as-is) | +5.3 (9.8) | 23 -> 21 | 241 -> 231 | 121 -> 186 | 241 -> 231 | -875 -> -988 | -420 -> -510 | -1,098 -> -1,212 | 50.3 -> 54.0 | 0.09 -> 0.10 | -0.5 |

**Correlation and the stack's worst weeks (vs COMP|off):** NQ RSI2_t10 corr ALL -0.04, PRE -0.08, inside the composite's 20 worst weeks -0.34 (sleeve sum 9.0k per contract); NQ RSI2C_s20 corr ALL -0.03, PRE -0.07, inside the composite's 20 worst weeks -0.34 (sleeve sum 9.0k per contract); ES RSI2_t10 corr ALL 0.01, PRE -0.02, inside the composite's 20 worst weeks -0.09 (sleeve sum 9.2k per contract); NQ GSHORT_t90 corr ALL -0.07, PRE -0.08, inside the composite's 20 worst weeks 0.28 (sleeve sum 6.3k per contract).

Reading: the three RSI2 sleeves (NQ RSI2_t10, RSI2C_s20, ES RSI2_t10) are the only unbuilt PASS rows that pass STRICT (positive per contract in L3M, L6M, HOLD, PRE and X') AND TOLERANT (the program cells are STRICT but fail the PRE worst-20 clause because they deepen it). Added to the composite they do not deepen its PRE worst-20 (NQ RSI2_t10 at 3 lots: -875 -> -861k), lower the PRE and ALL maxDD (241 -> 228k) and the X' maxDD (121 -> 99k), but they deepen the X' worst-20 (-420 -> -448k); and they have a ten-year 2013-2023 record outside the PRE/X' selection windows (NQ +155/ct/wk, t 2.3). They are small (low frequency, 1 trade every ~2 weeks), inside MDE as additions (ALL +2.1k at 3 lots vs MDE 3.0k), not beyond a same-volume random-day placebo before mid-2025 (rank 0.94-0.96), and they fail the year-share gate by a hair (0.606 / 0.611) because 2025 was the best year. They are NOT hostable in D7 and conflict with D6 as built: entry 15:56 ET is inside the 15:00-18:00 ET block, the hold crosses the 16:55 ET flatten and the 17:00-18:00 break (overnight), and there is no RSI(2) slot. Spec (struct48 `t36lib.py` RSI2 / `t37lib.py` RSI2C / `t38lib.py` GSHORT): at the 15:55 ET bar of each label day compute Wilder RSI(2) (alpha 0.5, seeded with the mean of the first two up/down moves) on the series of daily 15:55 bar opens; if RSI(2) < 10 buy 1 lot at the 15:56 open (RSI2C: stop = entry - 2.0 x ATR14 of the prior completed label day, filled at min(next open, stop - 1.01); CC adds a cap of 3 lots), exit at the next label day's 15:56 open; skip if a contract roll lies between entry and exit. ES version: same on ES (point value $50). GSHORT: RSI(2) > 90 AND the stack's own P&L over the previous 4 complete ISO weeks < 0 -> sell 1 NQ at 15:56, cover next 15:56 (needs the live stack P&L: a cross-book dependency). A forward Shadow log needs only the 15:55 bar and the daily series; it can be a separate paper strategy outside D6/D7.

**9b. Program PASS cells (T-programs; $/wk at 10 lots on the MAPPED basis, per-contract = /10).** These are the top 5 by shrunk $ across all unbuilt PASS rows; they are the same kind of NQ intraday trend/pullback entries as the live books and carry the mapped-basis caveat of their reports (e.g. TR3_DON15_S "PASS on the mapped basis; no direct L2 replay"; $1.5-2.0k per contract-week is higher per lot than the whole live stack's ~$1.1k, which is a flag for the mapping, not evidence).

| cell | L3M | L6M | HOLD | PRE | X' | ALL ($/ct/wk) | t ALL | year share | S1 (PRE,X'>0) | STRICT / TOLERANT / NOW | tier (post-hoc) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| TR3_DON15_S | 3,174 | 3,165 | 2,459 | 1,736 | 473 | 1,541 | 3.8 | 0.43 | yes | yes / NO / yes | LEAD-posthoc (S2 carried from the program, not re-run; mapped basis) |
| TB4W_10_volume_500_ST10 | -160 | 3,003 | 2,570 | 1,625 | 223 | 1,436 | 3.2 | 0.61 | yes | NO / NO / NO | LEAD-posthoc (S2 carried from the program, not re-run; mapped basis) |
| TB4A_time_03_30s_ST3_SW38 | 2,546 | 2,569 | 2,007 | 1,529 | 266 | 1,279 | 3.0 | 0.70 | yes | yes / NO / yes | LEAD-posthoc (S2 carried from the program, not re-run; mapped basis) |
| PB7_HMA55_EMA1_T2_W60_s-3 | 1,211 | 2,064 | 1,930 | 1,479 | 375 | 1,269 | 2.9 | 0.60 | yes | yes / NO / yes | LEAD-posthoc (S2 carried from the program, not re-run; mapped basis) |
| PB7_PB5_depth_atr0.5_W15_s-3 | 1,238 | 2,188 | 2,020 | 1,315 | 1,141 | 1,433 | 3.5 | 0.66 | yes | yes / NO / yes | LEAD-posthoc (S2 carried from the program, not re-run; mapped basis) |

Added to the Sunday composite (3 lots; the full 1/2/3/5/SD-matched grid is in `out/orb/s10_prog_risk.csv`): the means rise (+3.8 to +4.6k/wk ALL, each just beyond its MDE of 3.4-3.7k) but they are the same trend bet as the stack and DEEPEN the tail: ALL worst-20 -1,098k -> -1,216k to -1,333k, PRE worst-20 -875k -> -941k to -1,019k, HOLD maxDD 97k -> 126-165k, and the recent L3M of TB4W_10 is negative (-160/ct/wk, composite maxDD L6M 23 -> 58k). On the drawdown-first standard none of them is a RISK-KEEP; they are mean additions to a book that does not need more correlated trend risk.

**TR3_DON15_S vs the Sunday composite**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +3.2 (2.5)* | 23 -> 23 | 241 -> 234 | 121 -> 130 | 241 -> 234 | -875 -> -917 | -420 -> -439 | -1,098 -> -1,160 | 50.3 -> 53.0 | 0.09 -> 0.10 | +0.3 |
| 3 | +9.5 (7.4)* | 23 -> 24 | 241 -> 228 | 121 -> 149 | 241 -> 228 | -875 -> -1,012 | -420 -> -500 | -1,098 -> -1,333 | 50.3 -> 59.1 | 0.09 -> 0.12 | -0.1 |
| 5 | +15.8 (12.3)* | 23 -> 30 | 241 -> 237 | 121 -> 168 | 241 -> 237 | -875 -> -1,125 | -420 -> -580 | -1,098 -> -1,535 | 50.3 -> 66.2 | 0.09 -> 0.13 | -0.8 |
| **5.0** (SD 0.5x as-is) | +15.8 (12.3)* | 23 -> 30 | 241 -> 237 | 121 -> 168 | 241 -> 237 | -875 -> -1,125 | -420 -> -580 | -1,098 -> -1,535 | 50.3 -> 66.2 | 0.09 -> 0.13 | -0.8 |

**TB4W_10_volume_500_ST10 vs the Sunday composite**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +3.0 (3.5) | 23 -> 34 | 241 -> 238 | 121 -> 133 | 241 -> 238 | -875 -> -895 | -420 -> -442 | -1,098 -> -1,150 | 50.3 -> 53.3 | 0.09 -> 0.10 | +0.4 |
| 3 | +9.0 (10.4) | 23 -> 58 | 241 -> 233 | 121 -> 158 | 241 -> 233 | -875 -> -970 | -420 -> -493 | -1,098 -> -1,304 | 50.3 -> 60.3 | 0.09 -> 0.11 | +0.1 |
| 5 | +15.0 (17.3) | 23 -> 83 | 241 -> 227 | 121 -> 186 | 241 -> 227 | -875 -> -1,071 | -420 -> -557 | -1,098 -> -1,487 | 50.3 -> 68.4 | 0.09 -> 0.13 | -0.5 |
| **4.3** (SD 0.5x as-is) | +13.0 (15.0) | 23 -> 75 | 241 -> 229 | 121 -> 176 | 241 -> 229 | -875 -> -1,034 | -420 -> -532 | -1,098 -> -1,426 | 50.3 -> 65.7 | 0.09 -> 0.12 | -0.3 |

**TB4A_time_03_30s_ST3_SW38 vs the Sunday composite**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +2.6 (3.1) | 23 -> 28 | 241 -> 254 | 121 -> 125 | 241 -> 254 | -875 -> -891 | -420 -> -440 | -1,098 -> -1,125 | 50.3 -> 52.0 | 0.09 -> 0.09 | +0.7 |
| 3 | +7.7 (9.3) | 23 -> 40 | 241 -> 279 | 121 -> 135 | 241 -> 279 | -875 -> -963 | -420 -> -489 | -1,098 -> -1,236 | 50.3 -> 56.7 | 0.09 -> 0.09 | +0.9 |
| 5 | +12.8 (15.5) | 23 -> 52 | 241 -> 304 | 121 -> 144 | 241 -> 304 | -875 -> -1,051 | -420 -> -542 | -1,098 -> -1,401 | 50.3 -> 62.8 | 0.09 -> 0.09 | +0.2 |
| **4.7** (SD 0.5x as-is) | +12.1 (14.6) | 23 -> 51 | 241 -> 300 | 121 -> 143 | 241 -> 300 | -875 -> -1,037 | -420 -> -533 | -1,098 -> -1,376 | 50.3 -> 61.8 | 0.09 -> 0.09 | +0.3 |

**PB7_HMA55_EMA1_T2_W60_s-3 vs the Sunday composite**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +2.1 (3.1) | 23 -> 22 | 241 -> 245 | 121 -> 127 | 241 -> 245 | -875 -> -911 | -420 -> -437 | -1,098 -> -1,157 | 50.3 -> 53.2 | 0.09 -> 0.10 | +0.1 |
| 3 | +6.2 (9.2) | 23 -> 32 | 241 -> 252 | 121 -> 141 | 241 -> 252 | -875 -> -1,019 | -420 -> -503 | -1,098 -> -1,314 | 50.3 -> 59.9 | 0.09 -> 0.10 | -0.5 |
| 5 | +10.3 (15.3) | 23 -> 59 | 241 -> 259 | 121 -> 155 | 241 -> 259 | -875 -> -1,149 | -420 -> -591 | -1,098 -> -1,523 | 50.3 -> 67.6 | 0.09 -> 0.11 | -1.6 |
| **4.6** (SD 0.5x as-is) | +9.5 (14.1) | 23 -> 53 | 241 -> 257 | 121 -> 152 | 241 -> 257 | -875 -> -1,122 | -420 -> -571 | -1,098 -> -1,477 | 50.3 -> 66.0 | 0.09 -> 0.11 | -1.4 |

**PB7_PB5_depth_atr0.5_W15_s-3 vs the Sunday composite**

| lots | d-mean L6M (MDE) | maxDD L6M | maxDD PRE | maxDD X' | maxDD ALL | worst-20 PRE | worst-20 X' | worst-20 ALL | SD ALL | Calmar ALL | EQUAL-RISK d-mean ALL |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | +2.2 (2.9) | 23 -> 25 | 241 -> 240 | 121 -> 126 | 241 -> 240 | -875 -> -884 | -420 -> -428 | -1,098 -> -1,119 | 50.3 -> 52.5 | 0.09 -> 0.10 | +1.0 |
| 3 | +6.6 (8.8) | 23 -> 30 | 241 -> 239 | 121 -> 139 | 241 -> 239 | -875 -> -941 | -420 -> -453 | -1,098 -> -1,216 | 50.3 -> 57.9 | 0.09 -> 0.11 | +1.7 |
| 5 | +10.9 (14.7) | 23 -> 35 | 241 -> 238 | 121 -> 156 | 241 -> 238 | -875 -> -1,045 | -420 -> -486 | -1,098 -> -1,365 | 50.3 -> 64.4 | 0.09 -> 0.12 | +1.4 |
| **4.9** (SD 0.5x as-is) | +10.7 (14.4) | 23 -> 35 | 241 -> 238 | 121 -> 155 | 241 -> 238 | -875 -> -1,038 | -420 -> -483 | -1,098 -> -1,356 | 50.3 -> 63.9 | 0.09 -> 0.12 | +1.4 |

D6/D7 mapping and NT8 spec per program cell (existing executability specs, not re-written here):

| cell | existing spec | D7 slot? | D6? |
|---|---|---|---|
| TR3_DON15_S (= TRW_DON15m_n20_S) | `DS3_SPEC_TR3_DON15_S.md`: Donchian-20 (level one bar back) on 15-min bars, stop-entry at level + 1 tick, 60 pt / 1.0R bracket, flat 16:55, DELIVERABLE in NT8 (OnBarClose, stop orders intrabar), identity 0.63% entry mismatch | no: no Donchian/channel-break slot | new book (stop-entry channel breakout) |
| TB4W_10_volume_500_ST10_E20_1_T1 | nearest `DS3_SPEC_TB4D_volume_00_volume_1000_ST15_E20_1_T1.md` (volume bars, Supertrend regime, EMA20 pullback level, trigger T1; DELIVERABLE WITH CONDITIONS: tick-built volume bars) | partial: volume bar type + Supertrend are D7 capabilities, the EMA20-pullback entry is not | new entry mode |
| TB4A_time_03_time_30s_ST3_SW38_T2 | same family as `DS3_SPEC_TB4W_03_time_15s_ST3_E20_1_T2_SESSION.md` (30-s bars; swing-level pullback) | partial (as above) | new entry mode |
| PB7_PB_HMA55_EMA1_T2_W60_s-3 | PB7 widening around the HMA55 pullback (H6 family); `DS3_SPEC_PB7_PB5_depth_atr0.5_W15_s+0_SESSION.md` is the A6 reference | no | H6/A6 property change (window 60, shift -3) |
| PB7_PB5_depth_atr0.5_W15_s-3 | A6 = W15 s+0; this is the level shifted -3 pt | no | one A6 parameter (Pb7Rules level shift) |

### 10. Open items, decisions for the user, and disclosure

1. **D1-Q1 (non-blocking):** should ORB_ASIA_15 s60 be built as a Shadow-only D6-type book `OA6` at 1 lot (spec section 8)? Default: build the paper logger after Sunday; no live lots. Reason: the evidence is a 2025-26 direction effect with year share 0.66; the forward log is the only clean test (W_on ~ 51 weeks).
2. **D1-Q2 (non-blocking):** the RSI2 sleeves (NQ RSI2_t10, RSI2C_s20, ES RSI2_t10) are the best-supported unbuilt rows (STRICT and TOLERANT, ten-year record, low correlation 0.03-0.11 to the stack by struct48, no deepening of the composite's PRE tail) but are overnight, end-of-day entries that D6's 16:55 flatten and 15:00-18:00 block forbid and D7 cannot host. Should a separate paper strategy log them? Default: yes, paper only, no live.
3. **Definition used for "shrunk $":** 0.25 x min(capped WF, capped HOLD) per contract-week (ledger ratio of the only PASS family with a non-zero shrink). The ledger's own SHRUNK column is 0.00 for all other PASS rows, so any other ranking convention would reorder items 3-5 but not the conclusion that program cells are mapped-basis and trend-correlated.
4. **Not done / limits:** (i) ES RSI2 and GSHORT placebo not run (no ES bars; GSHORT needs the stack's own P&L); (ii) RSI2C placebo uses the RSI2_t10 family value; (iii) program cells: S2 carried, no re-run of placebos or direct-basis pricing; (iv) risk additions are pure additions (the ORB sleeve fired no lock; new lock interplay with the composite's combined week lock not modelled); (v) the stop-order entry and the cell neighbours in the bar store are 1-minute-resolution sensitivities; (vi) the 11 tape-defect label days are in the bar store unfixed (de-duplicated by bar end time); the stored struct48 series used for the headline predate that rebuild (TAPE-2: no tier change); (vii) one discovery scan listed column names of stored series files that contain post-cap rows; no post-cap value was read or kept (all series sliced at load).
5. **Multiplicity:** the lead was 1 of 644 STRUCT48 cells (cumulative 28,337 trials in the ledger); the 36-cell ORB family is the relevant selection set here and 12 of its 36 cells have HOLD>0 with 0 of 36 positive in PRE, X' and HOLD together.

Files: `autopilot/DS3_ORB_ASIA_D7.md`, `autopilot/ORB_BRIEF_SECTION.md`, `l2vast/ds3/out/orb/` (s1_tieout.pkl, s2_windows.csv, s2_yearshare.csv, s3_risk.csv, s3b_corr.csv, s4_placebo.pkl, s4b_rank.csv, s5_capacity.csv, s6_stoporder.pkl, s7_inventory_rows.csv, s8_sleeve_*.csv, s8b_placebo.csv, s9_rsi2_nb.pkl, s10_prog_*.csv, s11_gates.csv), code `l2vast/ds3/code/orb/` (orb_lib.py, orb_risk.py, s1..s12).
### Appendix A. The 30 exposures (all PASS-tier rows in the ledgers; union of original and capped PASS; approximate grouping by name, same-stream rows merged)

| exposure | rows | PASS orig | PASS capped | built | engine family live | best cell (by shrunk $/ct-wk) | shrunk $/ct-wk | native unit |
|---|---|---|---|---|---|---|---|---|
| PB HMA55 pullback (H6 family) | 8 | 7 | 7 | 0 | H6/HM | PB7_PB_HMA55_EMA1_T2_W60_s-3 | 407 | $/wk at 10 lots, mapped (program report) |
| TR Donchian (15/30m) | 8 | 8 | 7 | 0 |  | TRW_DON15m_n20_S | 493 | $/wk at 10 lots, mapped (program report) |
| TB4 alt-bar pullback (volume) | 6 | 6 | 5 | 0 |  | TB4W_10_volume_500_ST10_E20_1_T1_nvolume00 | 481 | $/wk at 10 lots, mapped (program report) |
| PB7 depth-ATR0.5 (A6 family) | 6 | 6 | 5 | 1 | A6/PB7 | PB7_PB5_depth_atr0.5_W15_s-3 | 385 | $/wk at 10 lots, mapped (program report) |
| TR Keltner break (K6 family) | 5 | 4 | 5 | 0 | K6/KB | TR2_KB_plain | 384 | $/wk at 10 lots, mapped (program report) |
| TB4 alt-bar pullback (time) | 5 | 5 | 5 | 0 |  | TB4A_time_03_time_30s_ST3_SW38_T2 | 422 | $/wk at 10 lots, mapped (program report) |
| ORB Asia 15 s75 | 4 | 4 | 0 | 0 |  | ORB_ASIA_15_v1__s75@1.0 | 65 | sleeve $ per contract (struct48 harness) |
| NQ RSI2 combo (RSI2C/RSI2CC s20) | 4 | 4 | 4 | 0 |  | E:NQ_RSI2CC_s20 | 193 | sleeve $ per contract (struct48 harness) |
| ORB Asia 15 s60 | 4 | 4 | 0 | 0 |  | ORB_ASIA_15_v1__s60@0.5 | 64 | sleeve $ per contract (struct48 harness) |
| TA1 order-flow imbalance (wide) | 3 | 0 | 3 | 0 |  | TE3_ofi_w1_q0.99|wide | 139 | $/wk at 10 lots, mapped (program report) |
| PB6 ST60m-EMA20 pullback | 3 | 1 | 3 | 0 |  | PB6_ST60m_EMA20_3m_T1 | 317 | $/wk at 10 lots, mapped (program report) |
| NQ RSI2_t10 | 2 | 2 | 0 | 0 |  | E:NQ_RSI2_t10 | 235 | sleeve $ per contract (struct48 harness) |
| ES RSI2_t10 | 2 | 2 | 0 | 0 |  | ES_RSI2_t10 | 162 | sleeve $ per contract (struct48 harness) |
| NQ GSHORT_t90 | 2 | 2 | 0 | 0 |  | E:GSHORT_t90 | 52 | sleeve $ per contract (struct48 harness) |
| PB ST10 pullback (S6/U6 family) | 2 | 2 | 2 | 0 | U6-S6/ST | PB_ST10_SWZ_T1 | 320 | $/wk at 10 lots, mapped (program report) |
| TA1 Supertrend 10m | 2 | 1 | 2 | 0 | U6-S6/ST | TE1_st_10m|wide | 173 | $/wk at 10 lots, mapped (program report) |
| PRO2 ER-trend EMA5 | 2 | 2 | 2 | 0 |  | PRO_ER4_EMA5 | 166 | $/wk at 10 lots, mapped (program report) |
| PRO1 absorption | 2 | 2 | 1 | 0 |  | PRO1_ABS_R10_EMA200_SWZ | 200 | $/wk at 10 lots, mapped (program report) |
| PRO2 Kalman | 1 | 1 | 0 | 0 |  | PRO_KAL_k0.0 | 174 | $/wk at 10 lots, mapped (program report) |
| PRO1 imbalance | 1 | 1 | 1 | 0 |  | PRO1_IMB_K5_ST10_SWZ | 292 | $/wk at 10 lots, mapped (program report) |
| PRO3 PRO3A_A1P3 | 1 | 0 | 1 | 0 |  | PRO3A_A1P3 | 61 | $/wk at 10 lots, mapped (program report) |
| PRO3 PRO3A_REL | 1 | 1 | 0 | 0 |  | PRO3A_REL | 108 | $/wk at 10 lots, mapped (program report) |
| TA1 big-trade (wide) | 1 | 0 | 1 | 0 |  | TE2_big_w5_q0.98|wide | 149 | $/wk at 10 lots, mapped (program report) |
| TA1 Keltner 3m (wide) | 1 | 1 | 1 | 0 | K6/KB | TE7_kelt3m_n14_m1.0|wide | 349 | $/wk at 10 lots, mapped (program report) |
| PRO3 PRO3A_VOL | 1 | 1 | 1 | 0 |  | PRO3A_VOL | 138 | $/wk at 10 lots, mapped (program report) |
| Set B (B01_SetB bracket set) | 1 | 0 | 1 | 0 |  | B01_SetB |  | sleeve $ per contract (struct48 harness) |
| TB4 alt-bar pullback (renko) | 1 | 1 | 0 | 0 |  | TB4E_renko_28_renko_20_ST15_E20_1_T3 | 243 | $/wk at 10 lots, mapped (program report) |
| TB4 alt-bar pullback (tick) | 1 | 1 | 1 | 0 |  | TB4B_tick_26_tick_250_ST3_SW62_T2 | 38 | $/wk at 10 lots, mapped (program report) |
| TR1 MAMA flip | 1 | 1 | 1 | 0 |  | TR1C_MAMA_10m_flip | 262 | $/wk at 10 lots, mapped (program report) |
| TR1 ensemble | 1 | 1 | 1 | 0 |  | TR1A_ens_s1.0_k3 | 229 | $/wk at 10 lots, mapped (program report) |

Row-level list (82 rows with tiers, capped WF/HOLD/L6M/PRE/X', build status): `l2vast/ds3/out/orb/s7_inventory_rows.csv`.

