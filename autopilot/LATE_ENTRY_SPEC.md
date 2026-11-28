# LATE ENTRY SPEC (W-SUNDAY-MX, from the code as run)

Code: `late(q, skip)` in code/th_dynexit/dx_build15.py (used in the FLATTEN_EXACT_SCORES sets TL3_DX_<S>_ALL_late50_M / late75) and its copy `late_ev` in code/th_sunday/sun_joint_mix.py (used in the SUNDAY_JOINT_MIXES sets TL3_DX_<S>_JM_*). Same arithmetic in both. Examples below are from the exact rows TL3_DX_<S>_JM_a_late50, Sep-Oct 2026.

## ANSWER FIRST (what differs from a plain reading)
1. late50 / late75 HALVE, they never skip (skip is a separate variant, `skip50/skip75`, not in the joint mixes). Lots become max(1, lots // 2).
2. The threshold is NOT a fixed table. It is an EXPANDING quantile (q = 0.50 or 0.75) of the holding times of the book's past WINNING trades, recomputed at every signal, sorted by entry time, starting after 30 winners (before that: no halving). Early in the sample the threshold is high, so early months halve far more entries. The tested result therefore does not equal a build with the end-of-sample numbers in section 2 (see the table: the fixed version halves a different 2 to 43% of the entries).
3. Causality: almost, not strictly. The winners used are those ENTERED before the signal, not those already EXITED. A winner still open at the signal has its realised hold included (small look-ahead). Strictly causal version (only winners already exited before the signal) changes the decision on under 0.6% of entries (column `differ`), so the look-ahead is negligible. A second, larger caveat: the winner pool is the LIVE MIX AS RUN of this study (trades after layers, 42 months, including the trades of the test window itself), so the rule is evaluated in-sample on the history it learns from, only ordered in time.
4. The winners' holding time is falling over the sample (e.g. AS-VWAPBRK p50 137 min before 2024, 23 min over all data), so the threshold at the end of Oct 2026 is the full-sample value but the recent-only (L6M) value is 2 to 3 times shorter. A live build with a trailing window would halve fewer entries than the tested rule.
5. Lots: engine lots are not the event lots: after the late rule the live layers (sizer_hooks, zones, stack caps) still act, so a 3-lot event can be filled as 2 (see examples).

## 1. The rule exactly
- Per entry (signal) with event time `ts` (signal second; fill is 1-2 s later) and planned exit `exit_ts` from the book's event row.
- planned hold = `exit_ts - ts` in seconds. `exit_ts` is the planned time exit = the book's session bell: Asia 02:00 ET, London 08:30 ET, NY AM 12:00 ET, NY PM 16:00 ET (a few NP-ZN rows end 12:59 / 13:14). Evaluated at SIGNAL time (`ts`), not fill time; the 1-2 s fill delay is not used.
- Winner pool for book `tag`: trades of that book in the live set as run (`TL3_SR_<S>_...` live mix; NP-CONF from `TL3_DX_NP_CONF_fix_M`, tag MF5) over all 42 months with gross > 0; hold = exit_ns - entry_ns (actual realised hold: target hits, policy takes, time exits all count). Sorted by entry second.
- Threshold at signal `ts`: i = last winner whose entry second is strictly before `ts`; thr = pandas expanding quantile q of the holds of winners 0..i (min_periods 30; NaN before that, NaN means not late).
- LATE if planned hold < thr (strictly). Action `late50` (q = 0.50) / `late75` (q = 0.75): lots = max(1, lots // 2) (1 lot stays 1; 2 -> 1; 3 -> 1; 4 -> 2; 5 -> 2; 6 -> 3; 8 -> 4). Stop, target, side, exit time unchanged; the entry is NOT skipped.
- Applied to the stream's event file before the engine; every book of the mix gets its own pool. Replacement streams (Ma1 in place of MF4, Z1 in place of MF1) are NOT late-adjusted in the joint sets.

## 2. Holding-time table for a FIXED build (minutes, winners of the live mix as run, all 42 months; NY PM MF5 = NP-CONF)
`p50 / p75` = full-sample (what the expanding quantile reaches at the end of Oct 2026). `L6M` = winners entered since 1 May 2026. `halved` = share of the book's 42-month entries halved as TESTED (expanding), `fixed` = share that would be halved if the end-of-sample number were used for the whole history, `differ` = share of entries where the two decisions differ.

| session | book | winners | p50 min | p75 min | p50 L6M | p75 L6M | median planned hold | halved50 tested / fixed / differ | halved75 tested / fixed / differ |
|---|---|---|---|---|---|---|---|---|---|
| AS MF1 | AS-NR7 | 931 | 172.0 | 420.0 | 63.9 | 111.8 | 236 | 74% / 34% / 43% | 90% / 87% / 12% |
| AS MF2 | AS-RSI | 334 | 86.8 | 254.5 | 37.5 | 80.1 | 305 | 23% / 16% / 12% | 48% / 38% / 19% |
| AS MF3 | AS-VWAPBRK | 1625 | 23.3 | 69.2 | 10.4 | 25.5 | 315 | 8% / 3% / 5% | 20% / 10% / 11% |
| AS MF4 | AS drift MF4 | 524 | 19.5 | 55.6 | 6.9 | 14.7 | 162 | 15% / 7% / 9% | 28% / 21% / 11% |
| LO MF1 | LO-CRUDE | 754 | 30.3 | 85.7 | 20.4 | 45.1 | 203 | 16% / 13% / 5% | 31% / 24% / 9% |
| LO MF2 | LO MF2 (drift) | 1572 | 45.4 | 113.4 | 21.7 | 50.0 | 190 | 28% / 15% / 14% | 55% / 34% / 24% |
| LO MF3 | LO-ZB | 1082 | 93.4 | 257.3 | 51.0 | 106.5 | 176 | 62% / 37% / 29% | 87% / 67% / 26% |
| NY MF1 | NY-FIB | 903 | 53.6 | 110.5 | 30.3 | 61.0 | 104 | 34% / 20% / 16% | 76% / 56% / 27% |
| NY MF2 | NY-VALUE | 1009 | 15.0 | 35.5 | 7.7 | 15.5 | 97 | 10% / 6% / 5% | 24% / 14% / 11% |
| NY MF3 | NY MF3 (drift) | 527 | 57.8 | 143.3 | 21.3 | 55.1 | 129 | 27% / 14% / 15% | 81% / 69% / 21% |
| NY MF4 | NY-NODE | 2383 | 5.2 | 14.4 | 2.5 | 6.3 | 106 | 4% / 2% / 2% | 9% / 5% / 4% |
| NY MF5 | NY-OFI | 1364 | 17.2 | 39.5 | 9.0 | 20.1 | 93 | 13% / 8% / 6% | 26% / 18% / 9% |
| NY MF6 | NY MF6 (drift) | 2097 | 7.2 | 20.0 | 3.3 | 8.5 | 103 | 5% / 3% / 2% | 11% / 7% / 4% |
| NY MF7 | NY MF7 (drift) | 554 | 30.0 | 64.8 | 15.5 | 27.6 | 96 | 22% / 16% / 8% | 38% / 34% / 8% |
| NY MF8 | NY MF8 (drift) | 627 | 10.3 | 26.8 | 4.8 | 11.3 | 118 | 4% / 2% / 2% | 10% / 6% / 5% |
| NY MF9 | NY MF9 (drift) | 447 | 18.1 | 40.8 | 10.5 | 24.6 | 90 | 9% / 8% / 3% | 21% / 17% / 7% |
| NP MF1 | NP MF1 (drift) | 1958 | 12.7 | 27.9 | 8.3 | 16.8 | 116 | 9% / 7% / 2% | 17% / 13% / 4% |
| NP MF2 | NP-ZN | 314 | 110.7 | 192.4 | 65.8 | 156.5 | 108 | 54% / 51% / 12% | 75% / 82% / 8% |
| NP MF3 | NP-YM | 735 | 30.0 | 63.1 | 16.9 | 41.0 | 150 | 10% / 0% / 9% | 22% / 22% / 2% |
| NP MF4 | NP MF4 (drift) | 890 | 36.4 | 83.8 | 28.2 | 59.1 | 92 | 32% / 26% / 8% | 52% / 47% / 10% |
| NP MF5 | NP-CONF (added book) | 499 | 78.0 | 135.0 | 39.0 | 105.5 | 111 | 41% / 36% / 10% | 62% / 59% / 12% |

Replacement books Ma1 and Z1: late was not applied to them in any test, so they have no tested threshold. Their winners' holds can be read from the REPL2 sets (TL3_DX_AS_REPL2_Ma1_M tag MF4; TL3_DX_NP_REPL2_Z1_M tag MF1) if a live late rule is wanted; the same function gives them a table (not computed here, flagged as open).

How the number moves over time (p50 / p75 minutes of winners entered before the date, the expanding value the rule used then):
| book | to 2024-01 | to 2025-01 | to 2026-01 | to 2026-10 |
|---|---|---|---|---|
| AS-VWAPBRK | 137 / 275 | 79 / 192 | 46 / 119 | 23 / 69 |
| LO-ZB (MF3) | 331 / 374 | 257 / 356 | 149 / 326 | 93 / 257 |
| NY-NODE | 13.6 / 36 | 10.3 / 26 | 7.7 / 21 | 5.2 / 14 |
| NP-ZN | 158 / 190 | 146 / 195 | 124 / 198 | 111 / 192 |

Update rule if the build is made live: recompute the p50 / p75 per book from the winners of the live trade log (entry before now, hold = exit - entry, gross > 0), at least weekly; a causal version using only winners already exited differs on under 0.6% of entries from the tested rule (column differ in the working table), so the rule as run is a fair stand-in for a causal one. A fixed table at the end-of-sample values would NOT reproduce the tested rows (differ column); to reproduce them, a growing quantile per book with the 30-winner start has to be used. A trailing-window (e.g. 6 months) version is NOT tested and would give much lower thresholds (L6M columns), halving fewer entries.

## 3. Match examples from the exact rows (sets TL3_DX_<S>_JM_a_late50; book shown; all times ET)
| session | case | signal | fill | bell | planned hold | threshold p50 | lots event -> after late50 -> engine trade | result |
|---|---|---|---|---|---|---|---|---|
| Asia, AS-VWAPBRK (MF3) | halved | Tue 01 Sep 2026 01:59:15 | 01:59:16 | 02:00 | 0.8 min | 24.6 min | 6 -> 3 -> 2 | UWTime exit, +$15 |
| Asia, AS-VWAPBRK (MF3) | passed | Mon 31 Aug 2026 22:30:48 | 22:30:49 | Tue 02:00 | 209.2 min | 24.7 min | 6 -> 6 -> 3 | PolicyTake, +$1,445 |
| London, LO-ZB (MF3) | halved | Wed 02 Sep 2026 07:11:28 | 07:11:29 | 08:30 | 78.5 min | 96.8 min | 2 -> 1 -> 1 | Target, +$1,200 |
| London, LO-ZB (MF3) | passed | Tue 01 Sep 2026 02:15:39 | 02:15:40 | 08:30 | 374.4 min | 97.4 min | 2 -> 2 -> 2 | Target, +$2,400 |
| NY AM, NY-NODE (MF4) | halved | Thu 08 Oct 2026 11:59:15 | 11:59:16 | 12:00 | 0.8 min | 5.2 min | 6 -> 3 -> 2 | UWTime exit, -$170 |
| NY AM, NY-NODE (MF4) | passed | Tue 01 Sep 2026 10:49:23 | 10:49:24 | 12:00 | 70.6 min | 5.2 min | 6 -> 6 -> 6 | Target, +$3,610 |
| NY PM, NP-ZN (MF2) | halved | Tue 22 Sep 2026 15:32:18 | 15:32:19 | 16:00 | 27.7 min | 114.7 min | 6 -> 3 -> 2 | UWTime exit, -$470 |
| NY PM, NP-ZN (MF2) | passed | Wed 02 Sep 2026 12:56:40 | 12:56:41 | 16:00 | 183.3 min | 111.8 min | 6 -> 6 -> 3 | UWTime exit, +$1,715 |

Engine lots below the post-rule lots (3 -> 2, 6 -> 3) are the live layers (sizer / zone / caps) acting after the rule.
Scripts: /tmp scratch only (late_an.py, late_ex.py, copied logic of sun_joint_mix.late_ev); table CSV /dev/shm/sun/late_tab.csv.
