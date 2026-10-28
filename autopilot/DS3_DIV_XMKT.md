# DS3_DIV_XMKT - cross-market intraday signals into NQ and ES (D3DVX, 2026-10-28)

Research only; no live / execution / chart change; no download or purchase; no credentials. **UNTOUCHED never read: every array is cut to label date <= 2026-02-06 at load**, so HOLD here = 2025-07-01..2026-02-06 (not to 2026-10-16 as in D3CX/D3CFA; numbers are not comparable to those files). Code l2vast/ds3/code/dvx/, outputs l2vast/ds3/out/dvx/. Preregs (sha256 logged in DECISIONS.md before scoring): ENTRY group `b9e991dcfddd45ed151a99cfbabb5421d3bdfbfc29697f0d17109a4c8e012d61` (12 cells, F = 12); FILTER group `e5d56ca87139b6f9bdfa02b4b3f4aeee38a427b7d34aa23c6b5af2e6bc94edf9` (3 cells, F = 3, written after the entry group was read, see disclosures). Pre-holdout texts autopilot/DS3_DVX_ENTRY_PREHOLD.md and DS3_DVX_FILTER_PREHOLD.md (one logged holdout look per group plus the 2023-span look).

## Verdict (headline)

**Cells: 12 entry cells (A 4, B 2, C 2, D 4; <= 12 per family) + 3 filter cells = 15 of the 30 allowed. All 15 are DEAD under the gates. No CONFIRMED item, no PASS, no CANDIDATE.** Nothing here adds information the NQ books can use at the stated size: the ZN, CL and relative-strength entry cells have WF means inside their MDE (or negative) and a placebo-(a) direction effect inside its CI; the filter cells all REMOVE P&L (WFPRE difference to the stack negative on all three, shifted-signal placebo ranks 0.13-0.40 in WFPRE). The one cell worth a note is **B_6E_ES_S** (6E down in the first hour -> SHORT ES at 10:30): WF +$303/wk [57,550] (MDE 352), beats both placebos in WF (ranks 1.00 / 1.00), paired-vs-direction +0.26 R, positive in 2024, 2025 and 2026 and in HOLD (+$146); it fails exactly two gates, year_share (one year = 63 percent of the WFPRE gain vs the 60 percent limit) and span2 (2023-04..2024-01 mean -$153/wk, inside its MDE), so it is DEAD by the frozen rule, and one cell out of 12 at one-sided p = 0.008 (x12 = 0.09) is what luck gives about 1 time in 11. It is a LEAD to watch on the forward register, nothing more.

### Verdict table per signal

| signal | entry cells | best entry cell (WF $/wk [CI], MDE) | filter cell: WF stack diff $/wk [CI] (MDE) | verdict |
|---|---|---|---|---|
| A bond-equity (ZN first hour -> NQ/ES) | 4, all DEAD | A_ZN_NQ_L: 116 [-91,323], MDE 295 | F_A: -2,544 [-9,205,3,797] (9,310); rank 0.40; DEAD | **DEAD** (entry) / **DEAD** (filter) |
| B FX (6E first hour -> ES) | 2, all DEAD | B_6E_ES_S: 303 [57,550], MDE 352 | F_B: -3,845 [-11,341,3,383] (10,685); rank 0.23; DEAD | **DEAD** (entry) / **DEAD** (filter); B_6E_ES_S near-miss LEAD |
| C oil shock (CL 5-min -> ES, 30 min) | 2, all DEAD | C_CL_ES_S: -124 [-337,89], MDE 304 | not run (no year-consistent entry cell) | **DEAD** (entry) / **DEAD** (filter) |
| D relative strength 10:00 (ES/NQ/RTY) | 4, all DEAD | D_LEAD_S: 144 [-152,439], MDE 422 | F_D: -6,850 [-15,990,1,753] (12,669); rank 0.23; DEAD | **DEAD** (entry) / **DEAD** (filter) |

CONFIRMED items: none. Any cell would have been capped at CANDIDATE anyway (WEAK fees on RTY/ZN/6E/CL, NQ fee a proxy); the raw tiers below are what the gates alone give.

## Entry group: what was run

- Clock and fills: market entry at the open of the bar after the information bar, 1 tick adverse; stop-market (2 ticks adverse), target limit only on 1-tick trade-through, flat 15:55 ET (family C: 30 minutes after entry), one trade per cell per day, equal $1,000 risk at the stop (fractional lots), fees per RT ES 4.84 (solid), NQ 4.84 (proxy), RTY 4.84 (WEAK). Bracket unit U = prior-20-session median 30-minute range of the TRADED instrument (13 RTH blocks per day), stop 1.0 U, target 1.5 U (median stop: ES 11 pt, NQ 51 pt, RTY 6.3 pt).
- (A) ZN move (close 10:29 - open 09:30) > 1.0 x U30(ZN): ZN up -> long, ZN down -> short, NQ and ES (4 cells). (B) same with 6E -> ES (2 cells; DXY is not on disk and the 6E/6J/6B/6C basket was not built to keep the cell count down). (C) CL 5-min block with range > 2 x the as-of median 5-min range, first of the day within 09:30-14:00: CL up -> short ES, CL down -> long ES, 30-minute hold (2 cells). (D) at 10:00, u = (close 09:59 - open 09:30)/U30 for ES, NQ, RTY; leader = max |u| >= 1.0, laggard = least move in the leader direction, dispersion >= 0.5: long/short the laggard (catch-up) and long/short the leader (continuation) (4 cells; RTY legs have the WEAK fee).
- Placebos (40 draws each): (a) random direction, same clock; (b) same rule at a random clock (A, B: decision 11:30-13:30; C: entry 10:00-14:00; D: decision 11:00-13:00). Trades per week and placebo-(b) trade counts are in the table (the A and B random-clock rule fires about half as often at midday).

### Table 1. Entry cells (windows by exit day; weekly dollars at $1,000 risk per trade; CI 95 percent, MDE = 2.8 SE)

| cell | tr/wk | WFPRE mean [CI] (MDE) | WF mean [CI] (MDE) | HOLD mean [CI] (MDE) | X 2023-04..2024-01 | 2x-cost WF | win | raw tier: failed gates |
|---|---|---|---|---|---|---|---|---|
| B_6E_ES_S | 1.17 | 366 [89,644] (396) | 303 [57,550] (352) | 146 [-350,642] (709) | -153 (494) | 240 | 0.52 | DEAD: year_share, span2 |
| D_LEAD_S | 1.53 | 96 [-245,437] (487) | 144 [-152,439] (422) | 250 [-322,822] (817) | 207 (637) | 70 | 0.44 | DEAD: beats_a, beats_b, best_of_N |
| A_ZN_NQ_L | 1.07 | 115 [-132,362] (353) | 116 [-91,323] (295) | 115 [-257,488] (532) | 319 (557) | 107 | 0.46 | DEAD: beats_a, beats_b, year_share, best_of_N |
| D_LEAD_L | 1.47 | -0 [-342,342] (488) | 72 [-240,384] (446) | 239 [-419,898] (941) | -216 (676) | 17 | 0.44 | DEAD: mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N |
| A_ZN_NQ_S | 1.06 | 73 [-236,382] (441) | 69 [-171,309] (342) | 57 [-293,407] (500) | -208 (441) | 59 | 0.44 | DEAD: beats_a, beats_b, year_share, span2, best_of_N |
| D_LAG_S | 1.53 | 48 [-274,370] (460) | 59 [-247,364] (436) | 83 [-600,766] (976) | -260 (630) | 1 | 0.43 | DEAD: beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N, halves |
| B_6E_ES_L | 1.13 | 3 [-237,243] (343) | 17 [-197,231] (306) | 48 [-389,484] (624) | 65 (669) | -22 | 0.45 | DEAD: beats_a, beats_b, cost2x_pre, year_share, best_of_N, halves |
| A_ZN_ES_S | 1.06 | 38 [-274,350] (446) | 16 [-231,264] (354) | -36 [-401,329] (522) | -166 (452) | -19 | 0.44 | DEAD: beats_a, beats_b, year_share, hold, span2, best_of_N, halves |
| A_ZN_ES_L | 1.07 | -101 [-365,163] (377) | -32 [-256,193] (321) | 133 [-282,547] (592) | 69 (517) | -116 | 0.42 | DEAD: mean_up, beats_a, beats_b, cost2x_pre, year_share, best_of_N, halves |
| D_LAG_L | 1.47 | 90 [-237,418] (468) | -35 [-316,246] (402) | -327 [-848,194] (744) | -139 (604) | -77 | 0.42 | DEAD: beats_a, beats_b, year_share, hold, span2, best_of_N, halves |
| C_CL_ES_S | 1.96 | -126 [-379,126] (361) | -124 [-337,89] (304) | -114 [-502,275] (556) | -341 (391) | -225 | 0.43 | DEAD: mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N, halves |
| C_CL_ES_L | 2.11 | -54 [-302,195] (355) | -129 [-336,78] (296) | -301 [-662,60] (516) | -365 (470) | -247 | 0.45 | DEAD: mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N, halves |

### Table 2. By year (weekly mean, MDE in parentheses; 2026 = 5 weeks to 02-06), halves and placebos (WF)

| cell | 2023 | 2024 | 2025 | 2026 | 2024 / 2025+ halves | (a) direction effect [CI] rank (MDE) | (b) clock effect [CI] rank (MDE) | paired vs (a) R/trade [CI] | b-draw trades vs real |
|---|---|---|---|---|---|---|---|---|---|
| B_6E_ES_S | -224 (459) | 338 (492) | 268 (460) | 122 (2,244) | 352 / 257 | 304 [85,537] 1.00 (309) | 296 [43,536] 1.00 (347) | +0.260 [+0.063,+0.457] | 115 vs 181 |
| D_LEAD_S | 229 (590) | 36 (582) | 185 (614) | 294 (1,284) | 75 / 200 | 191 [-30,456] 0.93 (353) | 135 [-192,507] 0.90 (491) | +0.125 [-0.047,+0.297] | 293 vs 233 |
| A_ZN_NQ_L | 287 (501) | 84 (438) | 243 (417) | -257 (1,133) | 20 / 196 | 11 [-189,200] 0.57 (273) | 158 [-73,379] 0.97 (320) | +0.010 [-0.201,+0.221] | 90 vs 169 |
| D_LEAD_L | -218 (671) | 79 (597) | 58 (668) | 385 (1,078) | 46 / 93 | 133 [-137,437] 0.90 (410) | -32 [-331,272] 0.33 (446) | +0.090 [-0.086,+0.266] | 321 vs 244 |
| A_ZN_NQ_S | -152 (413) | 57 (531) | 81 (428) | -425 (1,379) | 114 / 30 | 61 [-167,289] 0.78 (332) | 73 [-156,298] 0.85 (346) | +0.058 [-0.150,+0.266] | 89 vs 172 |
| D_LAG_S | -138 (562) | -122 (554) | 271 (660) | -981 (1,876) | -45 / 146 | 51 [-219,374] 0.70 (421) | 119 [-193,511] 0.85 (506) | +0.033 [-0.142,+0.209] | 295 vs 233 |
| B_6E_ES_L | -58 (626) | 131 (401) | -86 (431) | 279 (1,831) | 95 / -50 | -1 [-226,213] 0.53 (314) | 74 [-165,308] 0.75 (337) | -0.001 [-0.212,+0.211] | 116 vs 187 |
| A_ZN_ES_S | -76 (432) | 34 (551) | -34 (444) | -453 (1,399) | 128 / -78 | -10 [-221,210] 0.47 (315) | 39 [-199,258] 0.70 (335) | -0.009 [-0.216,+0.198] | 90 vs 172 |
| A_ZN_ES_L | 53 (480) | -142 (455) | 126 (468) | -276 (1,157) | -171 / 86 | -7 [-222,195] 0.42 (287) | 29 [-222,271] 0.65 (346) | -0.007 [-0.219,+0.206] | 90 vs 169 |
| D_LAG_L | -209 (570) | 7 (577) | 13 (551) | -464 (1,569) | -32 / -36 | 49 [-218,310] 0.65 (366) | 18 [-295,326] 0.62 (441) | +0.033 [-0.139,+0.205] | 319 vs 244 |
| C_CL_ES_S | -267 (375) | -119 (395) | -236 (459) | 100 (1,573) | -25 / -205 | 10 [-191,219] 0.53 (296) | -50 [-269,148] 0.28 (304) | +0.005 [-0.109,+0.120] | 310 vs 310 |
| C_CL_ES_L | -197 (468) | 7 (388) | -405 (425) | 800 (1,095) | 61 / -287 | -43 [-268,173] 0.35 (315) | -52 [-259,160] 0.30 (296) | -0.020 [-0.135,+0.095] | 333 vs 333 |

Gate detail (all 12 are DEAD; best-of-12 p95 of the (b) effect = $270/wk):

| cell | failed gates | WF one-sided p | Bonferroni x12 |
|---|---|---|---|
| B_6E_ES_S | year_share, span2 | 0.008 | 0.09 |
| A_ZN_NQ_L | beats_a, beats_b, year_share, best_of_N | 0.135 | 1.00 |
| D_LEAD_S | beats_a, beats_b, best_of_N | 0.170 | 1.00 |
| A_ZN_NQ_S | beats_a, beats_b, year_share, span2, best_of_N | 0.286 | 1.00 |
| D_LEAD_L | mean_up, beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N | 0.325 | 1.00 |
| D_LAG_S | beats_a, beats_b, cost2x_pre, year_share, span2, best_of_N, halves | 0.353 | 1.00 |
| B_6E_ES_L | beats_a, beats_b, cost2x_pre, year_share, best_of_N, halves | 0.440 | 1.00 |
| A_ZN_ES_S | beats_a, beats_b, year_share, hold, span2, best_of_N, halves | 0.449 | 1.00 |
| D_LAG_L | beats_a, beats_b, year_share, hold, span2, best_of_N, halves | 0.596 | 1.00 |
| A_ZN_ES_L | mean_up, beats_a, beats_b, cost2x_pre, year_share, best_of_N, halves | 0.609 | 1.00 |
| C_CL_ES_S | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N, halves | 0.873 | 1.00 |
| C_CL_ES_L | mean_up, beats_a, beats_b, cost2x_pre, year_share, hold, span2, best_of_N, halves | 0.888 | 1.00 |

### Table 3. Relation to the live stack (D3SL stack, WF 2024-02..2026-02-06; cell at $1,000 risk per trade, i.e. a tiny sleeve)

| cell | weekly corr to stack | cell $ in the stack 20 worst weeks | (stack $ in those weeks) |
|---|---|---|---|
| B_6E_ES_S | +0.11 | 429 | -3,116,593 |
| D_LEAD_S | +0.22 | -8,619 | -3,116,593 |
| A_ZN_NQ_L | -0.18 | 6,194 | -3,116,593 |
| D_LEAD_L | +0.16 | -7,133 | -3,116,593 |
| A_ZN_NQ_S | -0.02 | 5,395 | -3,116,593 |
| D_LAG_S | +0.20 | -3,264 | -3,116,593 |
| B_6E_ES_L | -0.07 | 948 | -3,116,593 |
| A_ZN_ES_S | -0.05 | 5,998 | -3,116,593 |
| A_ZN_ES_L | -0.20 | 2,547 | -3,116,593 |
| D_LAG_L | +0.08 | -7,330 | -3,116,593 |
| C_CL_ES_S | +0.04 | -7,159 | -3,116,593 |
| C_CL_ES_L | +0.05 | -3,701 | -3,116,593 |

All correlations are within +/-0.23 (the cross-market cells are close to uncorrelated with the stack, as hoped: the info is different), but the cells earn nothing positive to diversify with: the 12 cell series have WF means of -$129 to +$303/wk against a stack of tens of thousands, and in the stack's 20 worst weeks (-$3.1M in total at live lots) the cells make between -$8.6k and +$6.2k at $1,000 risk, i.e. under 0.3 percent of the loss either way. Even B_6E_ES_S (+$429 there, corr +0.11) is below noise on that measure.

## Filter group (separate prereg, written after the entry group was scored)

Trigger: a signal is scored as a filter only if an entry cell is year-consistent (frozen in the entry prereg: years gate and halves gate pass, WF mean > 0, WF placebo-(a) effect > 0). Eligible: A (A_ZN_NQ_L/S), B (B_6E_ES_S), D (D_LEAD_L/S); C not eligible. One cell per signal: remove every entry of ST, HM, WT, KB, SM, PB at/after the decision minute (10:30; D 10:00) whose side opposes the signal direction (exact lock engine, rows regenerated before the busy chain, PB masked; unfiltered identity reproduces the stack series to 0.0 abs difference), paired by week against the unfiltered D3SL stack at nominal lots. Placebo = signal series shifted by 5r days (30 draws).

| cell | base WFPRE -> filtered | WFPRE diff [CI] (MDE) | HOLD diff [CI] (MDE) | X diff | WF diff [CI] (MDE) | shift effect (rank) WF | 2x diff WFPRE | by year diff (2023/24/25/26) | stack worst-20 weeks: filtered vs base | tier: failed |
|---|---|---|---|---|---|---|---|---|---|---|
| F_A | 44,127 -> 41,543 | -2,584 [-10,636,5,496] (12,077) | -2,369 [-11,390,5,839] (12,611) | 4,492 | -2,544 [-9,205,3,797] (9,310) | -212 (0.40) | -288 | 7,394/3,611/-7,950/10,021 | -2,872,426 vs -3,077,351 | DEAD: f_mean_up, f_ci, f_shift, f_2x, f_year_share, f_hold, f_best3 |
| F_B | 44,127 -> 39,444 | -4,683 [-14,592,5,104] (14,096) | -1,760 [-11,221,6,609] (12,955) | 2,740 | -3,845 [-11,341,3,383] (10,685) | -2,253 (0.23) | -2,736 | 4,856/-1,871/-4,299/-12,019 | -3,155,237 vs -3,077,351 | DEAD: f_mean_up, f_ci, f_shift, f_2x, f_year_share, f_hold, f_best3 |
| F_D | 44,127 -> 34,709 | -9,418 [-20,047,1,178] (15,707) | -617 [-14,364,12,369] (20,180) | 1,682 | -6,850 [-15,990,1,753] (12,669) | -2,443 (0.23) | -9,118 | 43/-13,885/-1,643/13,697 | -2,713,828 vs -3,077,351 | DEAD: f_mean_up, f_ci, f_shift, f_2x, f_year_share, f_hold, f_best3 |

Reading: every filter lowers the stack's WFPRE and WF weekly P&L (by -$2.5k, -$3.8k and -$6.9k per week in WF; the expected cost of removing 6-8 percent of entries at average expectancy is of that order) and none is separable from its shifted-signal placebo (ranks 0.13-0.40 in WFPRE). All three WF CIs contain zero (upper bounds +$3.8k, +$3.4k, +$1.8k per week; MDEs $9k-$13k), so a modest filter benefit is not excluded, but none is indicated: HOLD differences are negative (-$2.4k, -$1.8k, -$0.6k) and only the 2023 span is positive (+$4.5k, +$2.7k, +$1.7k, all far inside MDE), the pattern of noise. The lot-matched (exposure-equalised, linear) WF difference is -$0.9k, -$2.2k, -$4.8k per week, still negative.

## Top cells regardless of verdict (never empty-handed)

1. **B_6E_ES_S** (short ES at 10:30 after a first-hour 6E drop beyond 1 x median 30-min range): WF +$303/wk [57, 550], MDE 352, 1.17 trades/wk, win 52 percent, 2x-cost +$240; failed gates year_share (0.63) and span2 (X -$153). Weak-side counterpart B_6E_ES_L: +$17/wk, no information on the long side.
2. **D_LEAD_S** (short the leader in a falling 10:00 tape): WF +$144 [-152, 439], MDE 422; failed beats_a, beats_b (ranks 0.93 / 0.90), best_of_N. All four years positive (+229, +36, +185, +294).
3. **A_ZN_NQ_L** (long NQ after ZN up): WF +$116 [-91, 323], MDE 295; failed beats_a (effect +$11, rank 0.57: the direction does not matter), beats_b, year_share, best_of_N.

## Why nothing here is a result (power and interpretation)

- MDE beside every mean: single-cell WF MDEs are $295-$446/wk for means that, if real, would be $100-$300, so most nulls are inconclusive rather than negative. What is excluded at 95 percent (CI upper bound) is a WF mean above about +$320 for the A, B-long and C cells and above +$440 for the D cells; B_6E_ES_S is the only cell with a CI above zero.
- The A cells (ZN) carry no signed information: placebo (a) effects are -$10..+$61/wk with ranks 0.42-0.78, i.e. buying or selling NQ/ES after a bond move is no better than flipping a coin about the direction; the positive A_ZN_NQ means are the market's own 2024-25 drift under a stop/target bracket (NQ is long-biased in the sample). C (CL) is negative on both sides in WF (2026, 5 weeks, is the only positive year): oil shocks are routine here (87 percent of days) and their equity reaction is not tradable at this cost. D: no leader/laggard asymmetry separable from noise.
- Costs: cost2x_pre fails on 6 of 12 cells; edges that exist are on the order of one tick-and-fee per trade.

## Disclosures

- Cut and windows: all data <= 2026-02-06 (label date); HOLD = 2025-07-01..2026-02-06, 2026 = 5 weeks. The D3SL lock engine regenerates rows over its full shipped span and the stack baseline series file out/dvx/stack_base.npz stores the whole-span days/series array, but no statistic, window, bootstrap or worst-week list uses a day after 2026-02-06 (masks verified in dvx_flib.WMASK).
- Entry prereg: only order counts were inspected before it was hashed (A 169/172, B 187/181, C 333/310, D 244/233 orders). The CL shock definition as written fires on 87 percent of days (643 of 742); I tested counts of a body-filtered variant (560-620 days) before the prereg, did not adopt it, and kept the directive's literal definition. No P&L was printed before the hash.
- Filter prereg was written AFTER the entry results were read (disclosed in the DECISIONS line); the design (block opposing entries; the eligibility rule) was frozen in the entry prereg, the cell choice (one cell per eligible signal, block-opposing direction) was made after seeing entry results. The eligibility rule is lenient (within-MDE years pass) and admitted signals whose entry cells were all DEAD. Filter series (actual, 2x, 30 shifted) were computed in one run for all days <= the cut; PRE scoring read WFPRE only and the holdout look was logged before HOLD/X/year numbers were scored.
- Fees: ES 4.84 solid; NQ 4.84 PROXY; RTY 4.84 WEAK; ZN/6E/CL are signal-only (no fee paid) but the directive ceiling (CANDIDATE) is applied to all cells; ZN/6E/CL bars are 1-min with no tick/L2 here. DXY is not on disk and no basket was built: (b) is 6E only.
- Fill model is bar-based (D3CX conservative): stop-first within a minute, no quote data; ES/NQ at 10:00-10:30 are liquid but the first minute after a release can gap beyond the +2 tick stop slippage. The 1.0/1.5 U bracket is a single frozen choice; no neighbours were tested.
- Harness slip, no scoring impact: the first call of dvx_fscore.py failed (sys.argv overwritten by an import in dvg_lib); the stage argument is now read before imports; nothing had been scored. Placebo (b) for A and B yields about half as many orders as the real rule (midday moves are smaller); it is a valid same-rule/random-clock null but not trade-count matched (counts shown in Table 2).
- Stack correlation / worst-20 use the DS3 D3SL stack series from dvg_lib.evaluate (live lots, WF baseline reproduced); the cell is at $1,000 risk per trade, not at 10-30 percent of stack risk (section 5 sizing was not run because nothing is CONFIRMED).
