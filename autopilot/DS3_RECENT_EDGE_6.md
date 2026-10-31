# DS3_RECENT_EDGE_6 - T-RECENT-EDGE sections 3 and 4 refreshed with every cell scored since the RE-2 monitor run (RE-6). Data to label day 20260206. Written 2026-10-31T16:14Z

Companions: DS3_EDGE_MONITOR.md and DS3_RECENT_PORTFOLIO.md (RE-2, the 294-series bank; unchanged and used as the "old bank" reference), DS3_RECENT_EDGE_FINAL.md, DS3_RECENT_EDGE_3.md, DS3_PERSISTENCE.md (RE-1: persistence, shrink and size columns), DS3_NO_TRADE_C_D.md and DS3_NO_TRADE_RULES_2.md (NTE-2 / NT-3: the source of most new rows), DS3_LOCK_SWEEP.md (GOV-2), DS3_GOVERNOR_FIDELITY.md (GOV-1 halt-resume), DS3_QUIT_FINAL.md (QW-2), DS3_RISK_OFF_A2.md (RO-2). Prereg `l2vast/ds3/prereg/RE6_prereg.md` (+ addendum 1, before any walk-forward run), sha256 and addendum sha in autopilot/DECISIONS.md. Code `l2vast/ds3/code/recentedge6/` (run_all.sh), outputs `l2vast/ds3/out/recentedge6/`. Masks capped 20260206; UNTOUCHED never read; 3 workers, OMP/MKL=1. Research only. The page is a view; the value of a recent edge is its shrunk expectation.

**Units, read this first.** Every new series is a daily $ delta on the D6-faithful Sunday composite at LIVE lots (NT-3 engine: integer half-up lots, running-max locks, A6 = PB7, composite base +37.7k L3M / +43.5k L6M / +40.5k HOLD / +24.7k PRE / +8.4k X' per week), summed to Monday weeks. Windows L3M 20251106.., L6M 20250801.., HOLD 20250701.., PRE 20240201..20250630, X' 20230403..20240131. All $ in this file are per week, live lots, delta against the same composite without the rule (GOV-2 and GOV-1: against the lock-off / no-halt composite of that program). The RE-2 numbers (S73 stack, research lots, divide by 2.35 for live) are a different engine and are never added to these. MDE = 2.8 x SE of the weekly delta over the window (L3M: 14 weeks). Tier of everything here: LEAD or below; nothing is PASS.

## PAGE 1 - the answer

**Headline.** 4,530 series were scored after the RE-2 monitor run (4,292 unique, NTE-2 2,478 + GOV-2 266 + GOV-1 1,786); 690 unique ones are positive in BOTH L3M and L6M, 2 of those are repeats of cells already in DEAD_CELLS (same four window numbers), leaving **688 genuinely new recent-positive rows in 430 correlation clusters**. 211 of the 688 are scale-ups of a profitable composite with no edge over an equal-lot placebo, or lock-widening variants of the ER sizer whose gain is the governor widening (marked leverage, excluded from the edge count), which leaves 477 rows / 296 clusters. Only 12 edge rows clear their own L3M MDE, 3 rows (3 clusters) survive a Benjamini-Hochberg test over all 1790 scored clusters (q <= 0.10), and **2 rows earn a "run at <= 25% size" - the rest are shadow or no**. Implemented in D6 / THP_POLICY: 0 of the 688 new rows (the ER(20) sizer, already on the SHADOW list, is the nearest relative).

**Does running the month's recent-positive edges at full size work? (rerun of the user's approach, new rows added, 25 monthly decisions 2024-01..2026-01).** On the engine universe (NTE-2 rules, joint runs on the D6-faithful engine, reps by trailing-13-week mean, |corr| < 0.5, <= 12 per month): full size +59.4k/wk (MDE 44.2k), 19 of 25 months positive, versus the composite itself +30.1k/wk; **but the policy carries 3.6x the composite's weekly SD and 3.2x its maximum drawdown, and plain leverage of the composite to the same SD would have earned +108k: the policy is -18.6k (MDE 43.0k) against leverage.** Split by what the edge does: skip-type reps alone (no-trade rules) -11.5k/wk (MDE 9.9k, 8 of 25 months positive, -2.9k vs leverage); size-up reps alone +105.6k/wk (22 of 25, 5.0x SD, -14.9k vs leverage); the same number of RANDOM rules -12.2k / -10.6k/wk. At half size +20.9k, at the walk-forward shrunk Kelly size +75.5k (the shrink factor measured on earlier months is positive for sizing rules, so shrunk size is not zero here as it was for the RE-2 stack cuts), persistence >= 0.7 only (full size) +18.5k (MDE 15.1k). The gain is lots on a composite that earned +30k/wk through 2024-26 with the governors widening on larger lots (NT-3 finding, reproduced), not a recognisable edge. The additive halt-resume / lock universe (GOV-1/2, 8 reps) loses -31.2k/wk at full size (MDE 35.4k, 9 of 25 months positive; worst month -713k). The RE-2 bank (S73 stack cuts / caps, research lots) was -9,598/wk for the same policy.

**Monitor (section 4).** The RE-2 status machine on the 15,763 ON episodes of the 4,288 monitorable new series flags the end of a dying edge a median **6 weeks** after it stopped paying (quartiles 1 to 13; old bank 4 weeks, 1 to 9), flags every edge that died, and **38% of its flags (5,202 of 13,677) were false alarms** (old bank 38%), i.e. 1.53 per ON rule-year (old 1.75) - about 2,490 per calendar year across the 1,790 clusters. A status is still not a forecast: P(next 13 weeks > 0) after STABLE 0.53, RISING 0.49, NEW 0.48, FADING 0.47, STOPPED 0.43 against 0.57 / 0.59 / 0.49 / 0.55 / 0.46 for block-shuffled twins of the same series: the dashboard flags a death, it does not promise a survival.

### Table 1 - the genuinely new recent-positive edges: cluster representatives ranked by shrunk expectation (edge rows only; $/wk live lots; MDE beside every row)

Columns: L3M / L6M / HOLD / PRE / X' = weekly delta in the window; MDE = L3M minimum detectable effect; q = Benjamini-Hochberg over all scored clusters; P = RE-1 persistence score P(next 3 months positive); shrunk = RE-1 shrink factor (OOS/IS for the family and t-bucket) x L3M; size = uncertainty-adjusted fraction of normal (capped 25% in the action); regime = day-vol tercile that carries the gain (trailing 26 weeks) and whether it is still present; leverage check = L3M beyond an equal-lot placebo.

| # | edge (plain words) | src | status (since) | L3M | L6M | HOLD | PRE | X' | MDE (L3M) | q | P(+3m) | shrunk exp | size | excess over equal-lot | regime | action |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | lots x1.5 when sided distance from the 20 EMA >= 1.5 | NTE2-D | STABLE (2025-11-24) | +23.2k | +22.5k | +18.8k | +6.7k | +1.5k | 21.7k | 0.399 | 0.70 | +6.9k | 0.43 | +7.6k | high-vol carries; present now | shadow (clears MDE but best-of-N: cluster q>0.10) |
| 2 | lots x1.5 when days_since_trend >= 5 | NTE2-D | STABLE (2026-01-26) | +21.7k | +16.7k | +14.7k | +5.6k | +2.3k | 18.5k | 0.225 | 0.72 | +6.4k | 0.47 | +6.6k | high-vol carries; present now | shadow (clears MDE but best-of-N: cluster q>0.10) |
| 3 | lots x2.0 on every signal of H6 | NTE2-U | RISING (2026-01-26) | +13.3k | +9.8k | +8.4k | +2.6k | -0.8k | 10.9k | 1.000 | 0.73 | +3.9k | 0.49 | +5.7k | mid-vol carries; present now | shadow (clears MDE but best-of-N: cluster q>0.10) |
| 4 | lots x1.5 when 1h.adx14 <= 15 | NTE2-D | STABLE (2026-01-05) | +7.2k | +5.5k | +5.4k | +2.3k | +1.8k | 8.5k | 1.000 | 0.65 | +2.1k | 0.32 | +5.1k | low-vol carries; ABSENT now | shadow (positive in every window, inside MDE) |
| 5 | lots x1.5 when at least 3 of: f60_vs_med >= 1.4; 1h.range_pos60 >= 0.462; 5m.adx14 >= 34.8; open_drive30 >= 0.183; prev_er_rth <= 0.0495; sided distan | NTE2-D | RISING (2026-02-02) | +5.7k | +3.2k | +3.0k | +1.9k | +0.7k | 4.4k | 0.399 | 0.75 | +1.7k | 0.52 | +3.5k | high-vol carries; present now | shadow (clears MDE but best-of-N: cluster q>0.10) |
| 6 | lots x1.5 when sided distance from the 50 EMA >= 3 [K6] | NTE2-D | STABLE (2025-12-15) | +5.3k | +5.9k | +5.0k | +2.0k | +0.8k | 6.8k | 1.000 | 0.64 | +1.6k | 0.28 | +0.9k | high-vol carries; present now | shadow (positive in every window, inside MDE) |
| 7 | lots x1.5 when 5m.adx14 >= 34.8 [H6] | NTE2-D | STABLE (2026-02-02) | +5.1k | +3.6k | +3.2k | +1.1k | +0.5k | 3.5k | 0.037 | 0.78 | +1.5k | 0.58 | +2.9k | high-vol carries; present now | run at 25% size (cap 25%), review monthly |
| 8 | lots x1.5 when 15m.chop14 <= 39.9 [H6] | NTE2-D | RISING (2026-01-26) | +5.0k | +2.6k | +2.6k | +1.3k | +0.0k | 3.7k | 0.064 | 0.76 | +1.5k | 0.54 | +2.6k | high-vol carries; present now | run at 25% size (cap 25%), review monthly |
| 9 | lots x1.5 when sided distance from the 200 EMA >= 8 [H6] | NTE2-D | RISING (2026-01-19) | +4.4k | +2.4k | +2.3k | +0.9k | +0.4k | 4.0k | 0.369 | 0.71 | +1.3k | 0.44 | +2.8k | high-vol carries; present now | shadow (clears MDE but best-of-N: cluster q>0.10) |
| 10 | lots x1.5 when 5m.rsi14 <= 32.3 [H6] | NTE2-D | STABLE (2026-02-02) | +4.1k | +2.7k | +2.1k | +0.7k | +0.3k | 4.8k | 1.000 | 0.66 | +1.2k | 0.33 | +2.2k | high-vol carries; present now | shadow (positive in every window, inside MDE) |
| 11 | lots x1.5 when 5m.adx14 >= 34.8 AND sided distance from the 200 EMA >= 8 AND 15m.chop14 <= 39.9 [H6] | NTE2-D | RISING (2026-01-26) | +3.6k | +1.9k | +1.8k | +0.8k | +0.4k | 3.6k | 0.480 | 0.69 | +1.1k | 0.41 | +2.7k | high-vol carries; present now | shadow (clears MDE but best-of-N: cluster q>0.10) |
| 12 | lots x1.5 when 4h.adx14 <= 19.6 [H6] | NTE2-D | RISING (2026-01-19) | +3.6k | +2.5k | +2.0k | +0.7k | +0.3k | 4.6k | 1.000 | 0.64 | +1.1k | 0.29 | +2.4k | mid-vol carries; present now | shadow (positive in every window, inside MDE) |
| 13 | lots x1.5 when 15m.hma_slope >= 0.407 [H6] | NTE2-D | RISING (2026-01-19) | +3.2k | +1.9k | +1.7k | +1.4k | +0.2k | 4.1k | 1.000 | 0.64 | +0.9k | 0.29 | +2.3k | mid-vol carries; present now | shadow (positive in every window, inside MDE) |
| 14 | lots x1.5 when open_drive5 >= 0.0854 [H6] | NTE2-D | STABLE (2025-11-17) | +2.6k | +2.4k | +2.1k | +0.8k | +0.4k | 3.1k | 1.000 | 0.66 | +0.8k | 0.32 | +1.2k | mid-vol carries; present now | shadow (positive in every window, inside MDE) |
| 15 | lots x1.5 when sig_vel30 >= 5.5 [H6] | NTE2-D | RISING (2026-01-26) | +2.6k | +1.7k | +1.4k | +0.5k | +0.2k | 3.4k | 1.000 | 0.64 | +0.8k | 0.28 | +1.9k | mid-vol carries; present now | shadow (positive in every window, inside MDE) |
| 16 | lots x1.5 when 5m.macd_hist <= -0.0156 [H6] | NTE2-D | RISING (2026-01-05) | +2.5k | +1.5k | +1.7k | +0.7k | +0.1k | 3.0k | 1.000 | 0.65 | +0.7k | 0.32 | +0.6k | high-vol carries; present now | shadow (positive in every window, inside MDE) |
| 17 | lots x1.5 when 5m.adx14 >= 34.8 AND 5m.rsi14 <= 32.3 AND 15m.hma_slope >= 0.407 [H6] | NTE2-D | STABLE (2026-02-02) | +2.4k | +1.3k | +1.1k | +0.6k | +0.3k | 2.8k | 1.000 | 0.66 | +0.7k | 0.33 | +1.2k | high-vol carries; present now | shadow (positive in every window, inside MDE) |
| 18 | lots x1.5 when open_drive5 >= 0.0854 | NTE2-D | STABLE (2025-11-17) | +9.6k | +11.5k | +9.7k | +6.0k | +1.7k | 12.8k | 1.000 | 0.63 | +0.7k | 0.02 | +1.6k | mid-vol carries; present now | shadow (positive in every window, inside MDE) |

18 of the 18 rows are size-up rules ("lots x1.5 when ...", or a whole book x2) on the composite; NT-3's finding applies to every one of them: any extra lot on a profitable composite adds money, and part of that is the running-max governors widening, not the signal. The excess column is the part beyond an equal-lot placebo (a random subset of the same trade share scaled the same way). Entry filters and halts follow in Table 2.

### Table 2 - status board of the genuinely new rows, by kind of rule (all unique rows | cluster representatives | edge rows after the equal-lot check)

| kind | rows | NEW | RISING | STABLE | FADING | STOPPED | edge rows | clusters | edge clusters | rows >= own MDE (L3M) | run at <=25% |
|---|---|---|---|---|---|---|---|---|---|---|---|
| GOV-1 halt-resume | 73 | 9 | 38 | 20 | 6 | 0 | 73 | 45 | 45 | 0 | 0 |
| GOV-2 lock config | 6 | 0 | 0 | 6 | 0 | 0 | 6 | 1 | 1 | 0 | 0 |
| NTE-2 size-down | 174 | 26 | 34 | 71 | 41 | 2 | 113 | 103 | 77 | 0 | 0 |
| NTE-2 size-up | 264 | 43 | 74 | 107 | 36 | 4 | 134 | 184 | 90 | 15 | 2 |
| NTE-2 skip (entry filter) | 132 | 38 | 22 | 53 | 18 | 1 | 113 | 81 | 68 | 0 | 0 |
| NTE-2 take-only | 39 | 15 | 13 | 8 | 1 | 2 | 38 | 16 | 15 | 0 | 0 |
| ALL | 688 | 131 | 181 | 265 | 102 | 9 | 477 | 430 | 296 | 15 | 2 |

Cluster representatives only: NEW 76, RISING 111, STABLE 173, FADING 64, STOPPED 6 of 430. Edge cluster representatives: NEW 52, RISING 79, STABLE 128, FADING 34, STOPPED 3 of 296.

### Table 3 - the non-sizing rows: best entry filters (skip) and halt-resume / lock configs by L3M z (cluster representatives, edge rows)

| # | edge (plain words) | src | status (since) | L3M | L6M | HOLD | PRE | X' | MDE (L3M) | q | P(+3m) | shrunk exp | size | regime | action |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | skip: learned no-trade model (POOL6), Q|ls|3|q20 | NTE2-L | STABLE (2025-12-29) | +2.5k | +0.2k | +0.2k | -3.8k | -5.9k | 2.9k | 1.000 | 0.65 | +0.6k | 0.17 | high-vol carries; present now | shadow |
| 2 | skip when sig_imb5_s >= 0.103 AND 1h.rsi14 <= 40.4 [M6] | NTE2-C | RISING (2026-01-19) | +2.1k | +0.9k | +0.8k | +0.2k | +1.0k | 3.0k | 1.000 | 0.61 | +0.0k | 0.00 | mid-vol carries; present now | shadow (positive in every window, inside MDE) |
| 3 | skip when ret_RTY_15m >= 14.7 AND an unfilled gap lies within 50% of the target distance ahead AND signal in the middle third of the 4-h dealing range | NTE2-C | STABLE (2026-01-26) | +0.6k | +0.8k | +0.7k | +0.2k | +0.6k | 0.9k | 1.000 | 0.60 | +0.0k | 0.00 | high-vol carries; present now | shadow (positive in every window, inside MDE) |
| 4 | skip when 5m.hma_slope >= 0.527 [U6] | NTE2-C | RISING (2026-02-02) | +4.0k | +1.4k | +1.0k | -0.3k | -0.2k | 6.3k | 1.000 | 0.60 | +0.0k | 0.00 | high-vol carries; present now | shadow |
| 5 | skip when on_range_atrd <= 0.303 [K6] | NTE2-C | STABLE (2025-12-29) | +1.3k | +0.4k | +0.4k | -0.1k | +0.3k | 2.0k | 1.000 | 0.60 | +0.0k | 0.00 | low-vol carries; ABSENT now | shadow |
| 6 | skip when t_since_big_with <= 300 [A6] | NTE2-C | RISING (2026-01-26) | +0.5k | +0.2k | +0.3k | -0.0k | +0.2k | 0.8k | 1.000 | 0.59 | +0.0k | 0.00 | low-vol carries; ABSENT now | shadow |
| 7 | halt-resume (book scope): halt on OR:z20_1.5:map_dow, resume day, half-size-first 0 | GOV1-HR | NEW (2026-01-26) | +2.0k | +0.0k | +0.1k | -1.1k | +2.8k | 3.3k | 1.000 | 0.26 | +0.0k | 0.00 | low-vol carries; ABSENT now | shadow |
| 8 | skip: learned no-trade model (K6), M|real|0|q20 | NTE2-L | STABLE (2025-12-08) | +1.1k | +0.8k | +0.6k | +0.3k | +0.0k | 1.9k | 1.000 | 0.58 | +0.0k | 0.00 | low-vol carries; ABSENT now | shadow (positive in every window, inside MDE) |
| 9 | skip when vix9d_over_vix <= 0.894 [U6] | NTE2-D | NEW (2026-01-19) | +3.1k | +1.4k | +0.8k | -1.2k | -1.3k | 5.4k | 1.000 | 0.58 | +0.0k | 0.00 | mid-vol carries; present now | shadow |
| 10 | skip when ES minus NQ move over 60 s >= 1.5 AND ret_ES_15m >= 10.6 | NTE2-C | STABLE (2025-12-29) | +0.8k | +1.0k | +0.4k | -0.1k | +2.5k | 1.5k | 1.000 | 0.58 | +0.0k | 0.00 | high-vol carries; present now | shadow |
| 11 | skip when 15m.swing_run >= 2 AND 1h structure mixed / undefined AND 15m.st10_3_age >= 37 [P6] | NTE2-C | RISING (2026-02-02) | +3.0k | +1.1k | +0.9k | +2.1k | +1.2k | 5.6k | 1.000 | 0.57 | +0.0k | 0.00 | mid-vol carries; present now | shadow (positive in every window, inside MDE) |
| 12 | skip when 8-tick depth vs same-minute 20-day median <= 0.7 [A6] | NTE2-C | STABLE (2026-01-12) | +1.1k | +0.5k | +0.4k | -0.1k | -0.1k | 2.0k | 1.000 | 0.57 | +0.0k | 0.00 | high-vol carries; present now | shadow |

### Table 4 - recent-positive rows scored by their own programs and new to the ledger / monitor (profile only: no daily series stored, so no CUSUM, MDE for RISKOFF-NTE2 rows from the CI half-width x 2.8/1.96 x sqrt(2); status by the RE-1 L3M-vs-L6M rule; not re-scored here, not repeated as findings)

| program | cell | unit | L3M | L6M | HOLD | PRE | X' | MDE (L3M) | status | P(+3m) | shrunk exp | size | their tier |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| QW-2 | book plus own X=4 meas=R LR | $/wk live lots (D6 composite) | +1.9k | +1.0k | +1.0k | +0.1k | +0.1k | 2.4k | RISING | 0.63 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | book plus own X=4 meas=RO LR | $/wk live lots (D6 composite) | +1.9k | +1.0k | +1.0k | +0.1k | +0.1k | 2.4k | RISING | 0.63 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | book timeif own T=11:30 X=2 LR | $/wk live lots (D6 composite) | +2.5k | +1.3k | +1.0k | +0.1k | +0.1k | 4.3k | RISING | 0.58 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | book timeif own T=14:00 X=0 LR | $/wk live lots (D6 composite) | +0.0k | +0.1k | +0.1k | +0.1k | +0.1k | 1.0k | FADING | 0.44 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | stack timeif K6 T=12:00 X=regardless LR dow=(2,) | $/wk live lots (D6 composite) | +1.2k | +0.9k | +0.6k | +0.3k | +0.3k | 2.6k | RISING | 0.23 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'er_chop') pol=quit_if_chop | $/wk live lots (D6 composite) | +0.6k | +0.6k | +0.5k | +0.5k | +0.5k | 1.6k | STABLE | 0.21 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | stack timeif K6 T=12:00 X=regardless LR regime=('12:00', 'ci_chop') pol=quit_if_chop | $/wk live lots (D6 composite) | +1.0k | +0.3k | +0.1k | +0.5k | +0.5k | 3.8k | NEW | 0.20 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | book timeif own T=12:00 X=regardless LR regime=('12:00', 'er_chop') pol=quit_if_chop | $/wk live lots (D6 composite) | +0.6k | +0.6k | +0.5k | +0.5k | +0.5k | 1.6k | STABLE | 0.52 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | book timeif own T=12:00 X=regardless LR regime=('12:00', 'ci_chop') pol=quit_if_chop | $/wk live lots (D6 composite) | +1.0k | +0.3k | +0.1k | +0.5k | +0.5k | 3.8k | NEW | 0.50 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | stack timeif K6 T=12:00 X=0 LR regime=('12:00', 'er_chop') | $/wk live lots (D6 composite) | +0.3k | +0.6k | +0.5k | +0.4k | +0.4k | 1.8k | FADING | 0.19 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | stack timeif K6 T=12:00 X=0 LR regime=('12:00', 'ci_chop') | $/wk live lots (D6 composite) | +1.5k | +0.9k | +0.6k | +0.3k | +0.3k | 3.7k | RISING | 0.22 | +0.0k | 0.00 | CANDIDATE-RECENT |
| QW-2 | stack timeif K6 T=12:00 X=2 LR regime=('12:00', 'er_chop') | $/wk live lots (D6 composite) | +0.5k | +0.4k | +0.3k | +0.3k | +0.3k | 1.2k | RISING | 0.22 | +0.0k | 0.00 | CANDIDATE-RECENT |
| ERSIZER | ER(20) sizer as coded, in-stack, running-max governors, integer live lots | $/wk live lots (D6 composite) | +15.3k | +12.5k | +13.7k | +9.5k | +0.8k | 33.2k | RISING | 0.57 | +0.6k | 0.00 | CANDIDATE-RECENT (view; post-hoc-selected, inside MDE) |
| RO-2 | IMB_A+G|MAE15|IP|5 [HM] | pts/contract/trade vs hold-the | +1.65 | +0.52 | +0.44 | +0.16 | +1.07 | 1.91 | NEW | 0.60 | +0.97 | 0.59 | CARRIED |
| RO-2 | VEL_20|ATR15|AL|1 [SM] | pts/contract/trade vs hold-the | +2.42 | +1.08 | +1.29 | +0.07 | +0.93 | 4.58 | NEW | 0.52 | +0.56 | 0.10 | CARRIED |
| RISKOFF-NTE2 | V_bar2atr|mae10|profit|0 [SM] | pts/contract/trade vs hold the | +1.21 | +0.63 | +0.01 | +0.52 | +0.58 | 2.38 | RISING | 0.52 | +0.28 | 0.09 | LEAD |
| RISKOFF-NTE2 | V_bar2atr|mae10|profit|60 [PE] | pts/contract/trade vs hold the | +0.78 | +0.58 | +0.67 | +0.20 | +0.74 | 0.97 | RISING | 0.59 | +0.46 | 0.57 | LEAD |
| RISKOFF-NTE2 | T_kz_end10|half|always|0 [PB] | pts/contract/trade vs hold the | +0.23 | +0.11 | +0.13 | +0.17 | +0.48 | 0.99 | NEW | 0.45 | +0.00 | 0.00 | LEAD |
| RISKOFF-NTE2 | V_bar2atr|sw1|profit|0 [PE] | pts/contract/trade vs hold the | +0.46 | +0.22 | +0.24 | +0.20 | +0.51 | 1.13 | NEW | 0.49 | +0.00 | 0.00 | LEAD |
| RISKOFF-NTE2 | V_spike5|mae15|under|300 [ALL] | pts/contract/trade vs hold the | +0.02 | +0.05 | +0.05 | +0.07 | +0.09 | 0.32 | FADING | 0.41 | +0.00 | 0.00 | LEAD |
| RISKOFF-NTE2 | V_bar2atr|mae15|profit|120 [PE] | pts/contract/trade vs hold the | +0.75 | +0.44 | +0.51 | +0.20 | +0.47 | 1.01 | RISING | 0.57 | +0.17 | 0.17 | LEAD |
| RISKOFF-NTE2 | V_bar2atr|mae5|profit|60 [PE] | pts/contract/trade vs hold the | +0.73 | +0.60 | +0.68 | +0.21 | +0.67 | 1.10 | RISING | 0.56 | +0.17 | 0.14 | LEAD |
| RISKOFF-NTE2 | V_bar2atr|sig|profit|120 [PE] | pts/contract/trade vs hold the | +0.91 | +0.64 | +0.82 | +0.24 | +0.69 | 1.30 | RISING | 0.56 | +0.21 | 0.15 | LEAD |
| RISKOFF-NTE2 | AND2[V_bar2atr&ICE_30]|mae5|profit|120 [MV] | pts/contract/trade vs hold the | +0.27 | +0.20 | +0.08 | +0.13 | +0.32 | 0.59 | RISING | 0.50 | +0.00 | 0.00 | CANDIDATE-RECENT |
| RISKOFF-NTE2 | AND3[K_st5&IMB_A&S_same_stop]|mae10|profit|0 [ALL] | pts/contract/trade vs hold the | +0.01 | +0.02 | +0.01 | +0.02 | +0.05 | 0.07 | FADING | 0.42 | +0.00 | 0.00 | CANDIDATE-RECENT |
| RISKOFF-NTE2 | AND3[K_st5&IMB_A&S_same_stop]|sw5|under|120 [PB] | pts/contract/trade vs hold the | +0.39 | +0.17 | +0.01 | +0.36 | +0.65 | 1.37 | NEW | 0.46 | +0.00 | 0.00 | LEAD |
| RISKOFF-NTE2 | AND2[V_spike3&S_same_stop]|mae10|always|0 [PE] | pts/contract/trade vs hold the | +0.13 | +0.06 | +0.09 | +0.15 | +0.32 | 0.58 | NEW | 0.44 | +0.00 | 0.00 | CANDIDATE-RECENT |
| RISKOFF-NTE2 | AND4[STL_600&IMB_A&K_st5&S_same_stop]|mae10|profit|120 [ALL] | pts/contract/trade vs hold the | +0.00 | +0.01 | +0.01 | +0.02 | +0.05 | 0.08 | FADING | 0.40 | +0.00 | 0.00 | CANDIDATE-RECENT |
| RISKOFF-NTE2 | AND4[MAER_10&PUL_2&K_st10&S_opp_entry]|mae5|always|0 [MV] | pts/contract/trade vs hold the | +0.14 | +0.21 | +0.21 | +0.19 | +0.56 | 0.62 | FADING | 0.45 | +0.00 | 0.00 | LEAD |

QW-2 rows are the CANDIDATE-RECENT cells of DS3_QUIT_FINAL.md (all sub-MDE, post-hoc); the ER(20) sizer is the SHADOW-list sizer of the Sunday brief; RISKOFF-NTE2 rows are the cells of DS3_RISK_OFF_FINAL.md that are positive in L3M, L6M and HOLD (stack fails a window or inside MDE); RO-2 rows are the two LEAD ideas (U6 60-s move against -> stop to 1.5 ATR; H6 imbalance flipped against -> MAE+15) that DS3_RISK_OFF_A2.md calls inside MDE and not placebo-beaten. They are tracked here so the status log has one line for them; nothing new is claimed.

### Table 5 - the walk-forward of "run the month's recent-positive ledger", 2024-01..2026-01 (25 monthly decisions, next-month delta, $/wk live lots; the composite itself earned +30.1k/wk, SD 54.5k, max DD 258k over the same weeks)

| universe / policy | mean $/wk | MDE | months + / - (active) | 2024 | 2025 | Jan 2026 | worst month | max DD | SD ratio vs composite | vs equal-SD leverage [MDE] |
|---|---|---|---|---|---|---|---|---|---|---|
| engine: every ON rep at FULL size | +59.4k | 44.2k | 19 / 6 (25) | +32.4k | +79.3k | +109.9k | -444k | 767k | 3.6x | -18.6k [43.0k] |
| engine: every ON rep at half size | +20.9k | 16.6k | 19 / 6 (25) | +12.0k | +26.3k | +48.3k | -157k | 275k | 1.9x | -5.0k [14.8k] |
| engine: every ON rep at shrunk Kelly size (size column) | +75.5k | 46.9k | 21 / 4 (25) | +31.0k | +111.2k | +140.1k | -198k | 753k | 3.9x | -10.4k [41.9k] |
| engine: persistence >= 0.5, shrunk | +76.7k | 46.8k | 20 / 4 (24) | +33.3k | +111.2k | +140.1k | -198k | 753k | 3.9x | -9.2k [41.7k] |
| engine: persistence >= 0.6, shrunk | +62.7k | 38.3k | 20 / 4 (24) | +40.9k | +78.7k | +98.3k | -236k | 705k | 3.3x | -7.0k [32.6k] |
| engine: persistence >= 0.7, full | +18.5k | 15.1k | 15 / 8 (23) | +15.9k | +18.9k | +35.1k | -108k | 208k | 1.7x | -2.4k [14.6k] |
| engine: skip-type reps only, full | -11.5k | 9.9k | 8 / 17 (25) | -8.9k | -12.9k | -19.8k | -318k | 1421k | 0.7x | -2.9k [7.6k] |
| engine: skip-type reps only, shrunk | -2.9k | 6.6k | 14 / 11 (25) | -6.0k | +0.0k | +0.0k | -318k | 561k | 0.9x | +0.1k [6.1k] |
| engine: size-type reps only, full | +105.6k | 64.2k | 22 / 3 (25) | +74.7k | +131.5k | +117.0k | -110k | 810k | 5.0x | -14.9k [59.0k] |
| engine: size-type reps only, shrunk | +103.1k | 64.3k | 22 / 3 (25) | +69.6k | +131.5k | +117.0k | -110k | 810k | 5.0x | -17.5k [59.4k] |
| engine placebo: same count of RANDOM rules, full (draw 1) | -12.2k | 11.9k | 9 / 16 (25) | -3.9k | -18.7k | -26.9k | -250k | 1622k | 0.7x | -3.5k [9.4k] |
| engine placebo: same count of RANDOM rules, full (draw 2) | -10.6k | 11.1k | 12 / 13 (25) | -5.4k | -16.7k | +3.9k | -231k | 1448k | 0.8x | -3.5k [9.3k] |
| additive GOV-1/2 reps, full | -31.2k | 35.4k | 9 / 16 (25) | -10.4k | -51.1k | -29.7k | -713k | 3923k |  | n/a (additive) |
| additive GOV-1/2 reps, half | -15.6k | 17.7k | 9 / 16 (25) | -5.2k | -25.5k | -14.8k | -357k | 1962k |  | n/a (additive) |
| additive GOV-1/2 reps, shrunk | -6.7k | 16.6k | 1 / 2 (3) | -13.8k | +0.0k | +0.0k | -401k | 1084k |  | n/a (additive) |
| RE-2 bank (S73 stack cuts/caps/ER/skips; RESEARCH lots, /2.35 for live): full / half / shrunk | -9,598 / -7,353 / -5,531 | 27,130 | 10 / 15 | | | | | | | |

Do nothing = 0 in every column. "vs equal-SD leverage" = total weekly P&L (composite + policy delta) minus the composite scaled to the same weekly SD; negative = the policy is worth less than simply running the composite bigger. Skip-type and size-type reps are chosen by the same walk-forward ON rule inside their own group.

## 1. What was scanned, what was a repeat, what is new

| source | series / rows | unique | recent-positive (L3M and L6M > 0) | note |
|---|---|---|---|---|
| GOV-1 halt-resume (1,786 cells, book / stack scope) | 1,786 | 1,761 | 97 | |
| GOV-2 lock sweep (stack C minus all locks off) | 266 | 170 | 8 | |
| NTE-2 section C: where NOT to take a signal (skip / x0.5, 7 scopes) | 926 | 851 | 175 | |
| NTE-2 section D: where to take MORE (x1.5, take-only) | 1,024 | 986 | 305 | |
| NTE-2 learned no-trade model policies | 438 | 438 | 99 | |
| NTE-2 lock-widening decoupling variants of the ER sizer | 55 | 51 | 50 | |
| NTE-2 time-of-day / calendar cells | 14 | 14 | 3 | |
| NTE-2 uniform sizing (every signal of a book x0.5/x1.5/x2) | 21 | 21 | 12 | |
| **total** | 4,530 | 4,292 | 749 (690 unique) | 2 unique recent-positive rows repeat a DEAD_CELLS row (same L6M / HOLD / PRE / X' to one decimal) and are not counted; placebo draws (NTE-2 group P, 601 cells) are not rows |

Profile-only files (no daily series) read from `recent_wins/`:

| file | rows | status |
|---|---|---|
| nte1.csv (NTE-1) | 1,045 | L3M window rows only; program NTE1/NTE1C is in DEAD_CELLS (36,576 rows) -> repeat |
| sdgap.csv (SD-GAP) | 18,744 | L3M only (no L6M/HOLD/PRE): cannot be classified; SDGAP1/2 in DEAD_CELLS (85,212 rows) -> repeat / L3M-only |
| bars3.csv (BARS-3) | 411 | L3M only; BARSCAND3 in DEAD_CELLS -> repeat / L3M-only |
| rhq.csv (RHQ halt-resume) | 9 | 7 recent-positive; RHQ-HALT-RESUME(-ADD) in DEAD_CELLS -> repeat |
| d7f.csv (D7 filters) | 4 | 0 recent-positive (all four negative in L6M) -> repeat / none positive |
| eslead.csv (ES-lead) | 2 | ESL in DEAD_CELLS -> repeat |
| nt3.csv (NT-3) | 501 | 501 L6M rows = the same NTE-2 engine cells scored above (same keys/numbers); counted once, in the bank -> repeat of the bank |
| riskoff_nte2.csv (NTE-2 risk-off) | 18 | 14 positive in L3M, L6M and HOLD, all LEAD or CANDIDATE-RECENT inside MDE; RISKOFF_NTE2 in DEAD_CELLS -> repeat; carried in Table 4 |
| riskoff_ro2.csv (RO-2) | 3 | the two LEAD ideas; RISKOFF_RO2 in DEAD_CELLS -> repeat; carried in Table 4 |
| sixty.csv (SIXTY list) | 569 | a post-hoc re-listing of RE-1 ledger rows (not new cells); SIXTY1 in DEAD_CELLS -> repeat of the ledger |

dead_lookup was applied before scoring (numeric four-window key against DEAD_CELLS.csv, any program); after the report the genuinely new rows are appended with `dead_lookup.append_cells` (program RE6). DEAD_CELLS.csv was not rebuilt.

## 2. The monitor, refreshed

### 2a. Current board (data to 2026-02-06) - how the new rows moved

**This round the edges that turned ON are** (52 edge clusters in NEW): skip when vix9d_over_vix <= 0.894 [U6] (NTE2-D, L3M +3.1k, MDE 5.4k); lots x1.5 when 5m.adx14 >= 44.2 [K6] (NTE2-D, L3M +2.3k, MDE 5.0k); skip when 15m.macd_hist >= 0.283 [U6] (NTE2-D, L3M +2.2k, MDE 7.2k); skip when at least 3 of: days_since_trend >= 5; 1m.adx14 >= 32.4; 1h.er20 <= 0.0458; 1m.rs (NTE2-D, L3M +2.2k, MDE 4.3k); skip when prev_ret_rth >= 0.71 AND ret_ES_15m >= 10.6 AND prev_rng_atrd >= 1.3 (NTE2-C, L3M +2.0k, MDE 7.5k); halt-resume (book scope): halt on OR:z20_1.5:map_dow, resume day, half-size-first 0 (GOV1-HR, L3M +2.0k, MDE 3.3k). **The ones that FADED are** (34): lots x1.5 when 15m.st10_3_age <= 6 (NTE2-D, L3M +2.1k, MDE 16.2k); lots x1.5 when f60_vs_med >= 1.4 AND 5m.er20 >= 0.386 AND sided premium third of the sessi (NTE2-D, L3M +0.6k, MDE 9.6k); skip: learned no-trade model (P6), M|ls|6|q20 (NTE2-L, L3M +1.9k, MDE 11.5k); lots x1.5 when nest.setline_20_30 AND 15m.st10_3_age <= 6 (NTE2-D, L3M +0.9k, MDE 5.4k); lots x0.5 when 5m.st10_3_dist <= 1.64 [P6] (NTE2-C, L3M +0.9k, MDE 4.7k); lots x1.5 when 1h.swing_run >= 2 AND impulse30 <= 0.27 AND open_drive30 >= 0.183 (NTE2-D, L3M +0.6k, MDE 1.2k). **The ones that STOPPED are** (9 rows, 6 clusters): lots x2.0 on every signal of M6 (NTE2-U, L3M +0.2k, MDE 6.9k); lots x1.5 when f60_vs_med >= 1.4 AND 5m.range_pos60 >= 0.451 (NTE2-D, L3M +0.4k, MDE 4.9k); lots x1.5 when prev_rng_atrd <= 0.733 [H6] (NTE2-D, L3M +0.0k, MDE 2.7k); skip when at least 3 of: 15m.bbw_pct100 >= 0.97; 15m.rsi14 >= 69.3; within 5 pts of the da (NTE2-D, L3M +0.1k, MDE 3.8k); skip when sweep of the session high within 15 min and the signal is the ICT-expected rever (NTE2-C, L3M +0.1k, MDE 1.1k); lots x1.5 when 1h.swing_run >= 2 AND RTH overnight gap |09:30 open - prior 16:00 close| in (NTE2-D, L3M +0.3k, MDE 2.2k). Status dates are the week the status began; the board is as of the week of 2026-02-02.

Transitions in the last 13 data weeks (cluster representatives) are appended to autopilot/EDGE_STATUS_LOG.md; the full log is `out/recentedge6/monitor6_log_last13w.csv`.

### 2b. Back-test of the monitor on the new series (2024-01..2026-02)

| set | ON episodes | died (hindsight) | flags | false alarms | share | median lag (weeks) [quartiles] | died episodes flagged before death |
|---|---|---|---|---|---|---|---|
| old bank (294, RE-2) | 1,108 | 793 | 747 | 283 | 38% | 4 [1, 9] | 21% |
| new series (all unique) | 15,763 | 12,698 | 13,677 | 5,202 | 38% | 6 [1, 13] | 23% |
| new: GOV1-HR | 5,657 | 5,408 | 5,187 | 1,423 | 27% | 7 [2, 13] | 18% |
| new: GOV2 | 375 | 210 | 312 | 38 | 12% | 13 [5, 14] | 3% |
| new: NTE2-C | 3,883 | 3,074 | 3,381 | 1,507 | 45% | 6 [-4, 13] | 28% |
| new: NTE2-D | 3,698 | 2,412 | 3,084 | 1,510 | 49% | 4 [-6, 12] | 29% |
| new: NTE2-L | 1,738 | 1,365 | 1,422 | 537 | 38% | 5 [1, 13] | 19% |
| new: NTE2-R | 297 | 167 | 207 | 140 | 68% | 4 [-19, 12] | 44% |
| new: NTE2-T | 47 | 36 | 38 | 15 | 39% | 4 [1, 13] | 19% |
| new: NTE2-U | 68 | 26 | 46 | 32 | 70% | 4 [3, 11] | 15% |

"Died" = the first week after which both the next 13 and the next 26 weeks sum to <= 0 (hindsight, independent of the monitor); lag = flag week minus that week (negative = flagged before); a flag is a false alarm if the rule earned > 0 over the 13 weeks after it. The GOV-2 lock configs are the slowest to flag (13 weeks) because their weekly sigma is large against their mean.

### 2c. What a status is worth: forward 13-week result after each status (new series), real vs block-shuffled twins

| status | week-rules | P(fwd13 > 0) real | twin | median fwd mean in sigmas real | twin |
|---|---|---|---|---|---|
| NEW | 43,019 | 0.480 | 0.489 | -0.007 | -0.001 |
| RISING | 23,159 | 0.489 | 0.588 | -0.000 | +0.049 |
| STABLE | 79,096 | 0.526 | 0.575 | +0.005 | +0.035 |
| FADING | 35,418 | 0.474 | 0.547 | -0.004 | +0.005 |
| STOPPED | 14,037 | 0.433 | 0.464 | -0.049 | -0.016 |

Real series sit below their twins after every status: a recent turn-on carries no information about the next quarter beyond what the selection effect alone gives. Same conclusion as the old bank (DS3_EDGE_MONITOR.md, section 2).

## 3. The portfolio, in more detail

### 3a. Persistence score calibration inside the walk-forward (logit on earlier months only; realised share of ON series positive over the next 13 weeks)

| universe | score bin | ON series-months | realised P(next 13w > 0) | realised keep (fwd/m13) |
|---|---|---|---|---|
| engine (NTE-2) | (0.0, 0.4] | 993 | 0.33 | -0.81 |
| engine (NTE-2) | (0.4, 0.5] | 2,243 | 0.37 | -0.51 |
| engine (NTE-2) | (0.5, 0.6] | 5,172 | 0.51 | -0.05 |
| engine (NTE-2) | (0.6, 0.7] | 7,109 | 0.62 | +0.37 |
| engine (NTE-2) | (0.7, 1.0] | 4,583 | 0.67 | +0.65 |
| additive (GOV-1/2) | (0.0, 0.4] | 6,126 | 0.30 | -0.47 |
| additive (GOV-1/2) | (0.4, 0.5] | 1,700 | 0.26 | -1.27 |
| additive (GOV-1/2) | (0.5, 0.6] | 1,005 | 0.23 | -1.39 |
| additive (GOV-1/2) | (0.6, 0.7] | 669 | 0.22 | -1.65 |
| additive (GOV-1/2) | (0.7, 1.0] | 720 | 0.19 | -1.81 |

In the NTE-2 universe the score discriminates (0.33 to 0.68) and the keep ratio rises with it; most of that is the sizing rules turning ON and OFF with the composite's own recent profit (a sizing rule on a profitable base is positive whenever the base is), which is the leverage effect again, not a property of the signals. In the halt/lock universe the score is inverted (0.30 to 0.19): halts that looked good keep losing. RE-1's persistence curve (P next 3m positive: entry filter 50%, sizing 51%, stack 17%) is the prior used in the Table 1 / 3 P column.

### 3b. Composition and correlation of what the policy holds

Across the 25 monthly ledgers the engine policy held 444 skip, 385 size-up and 71 size-down slots (mean 12.0 reps per month). Rows by kind in the unique new set: GOV-1 halt-resume 73; GOV-2 lock config 6; NTE-2 size-down 174; NTE-2 size-up 264; NTE-2 skip (entry filter) 132; NTE-2 take-only 39; 430 clusters at |corr| >= 0.8 over all weeks, and at the stricter walk-forward rule (|corr| < 0.5 over 52 weeks) at most 12 distinct reps in any month. Regime that carries the edge clusters (trailing 26 weeks): high-vol 114, mid-vol 100, low-vol 82; the carrying tercile is ABSENT in the most recent four weeks for 82 of 296 edge clusters, so those would be run in a regime that is no longer the one that paid.

Correlation of each new row's weekly delta with the composite's own weekly P&L (all 149 weeks), median [10th, 90th percentile]: GOV-1 halt-resume -0.11 [-0.27, +0.05]; GOV-2 lock config -0.14 [-0.19, -0.11]; NTE-2 size-down -0.02 [-0.20, +0.44]; NTE-2 size-up +0.19 [+0.03, +0.41]; NTE-2 skip (entry filter) -0.09 [-0.22, +0.05]; NTE-2 take-only -0.22 [-0.27, -0.14]. Among the rows themselves (share of the weekly-delta variance on the first principal component | median pairwise correlation): GOV-1 halt-resume 25% | +0.05; GOV-2 lock config 95% | +0.95; NTE-2 size-down 15% | +0.01; NTE-2 size-up 14% | +0.07; NTE-2 skip (entry filter) 9% | +0.02; NTE-2 take-only 68% | +0.78. Read: the new rows are individually diverse (first component 9-25%), except the GOV-2 lock configs (95%, one bet) and the take-only rows (68%). "Same regime wearing different clothes" is therefore true at the level of the cause, not of the correlation: every size-up row earns because the composite earned on those trades in the last six months, and held together their multipliers stack on the same trades (the policy's weekly SD is 3.6x the composite's), which is why the portfolio of them is a leverage trade.

### 3c. What the worst months looked like

Full-size engine policy: worst month 2025-06 (-444k), best 2025-11 (+1132k); skip-type: worst 2024-07 (-318k). With the maximum drawdown 3.2x the composite's, "drawdown when a regime ends" is the policy's own risk, not a hedge: the months it lost were the months the composite itself fell while lots were large.

## 4. Limits and what was not done

* The engine walk-forward covers the NTE-2 rules (their fire vectors rebuild exactly; joint run = OR of skip masks, product of multipliers, engine rounding inside). NTE-2 group R (lock-widening decoupling) and the GOV-1/2 rows are scored by the monitor but run additively in the walk-forward (R is excluded from it). Additive sums double-count overlapping rules; the sign of the GOV-1/2 result (negative) does not depend on that.
* Rows are best-of-N selected on L3M and L6M by construction; the equal-lot check (excess column), the BH q over all scored clusters, and the RE-1 shrink are the three guards. Halt-resume and lock rows have stack-family persistence (RE-1: 17%) and shrink <= 0, so their shrunk expectation is 0 by that study.
* Profile-only sources (NTE-1, SD-GAP, BARS-3: ~20,000 rows) are all repeats of DEAD_CELLS programs or L3M-only; not classified. QW-2, RO-2, NTE-2 risk-off and the ER sizer are carried in Table 4 from their own reports; their daily series were not stored in a form that can be diffed against a base in this pass (QW-2 stores per-cell daily levels against two bases).
* Prereg deviation (disclosed, addendum 1, logged before the first walk-forward run): the literal "|corr| < 0.8, one rep per cluster" rule gave 435-645 reps a month, which is not a runnable ledger; the corr < 0.5 / at most 12 rule replaces it and a random-rule placebo was added. NTE-2 and NT-3 kept writing while this ran (groups P, R and U appeared after the first pass); the pipeline (`run_all.sh`) was rerun on the files present at the time stamped above.
* The 2026-02 depth month, post-cut tables and UNTOUCHED were not read.

Files: `out/recentedge6/rows6_ledger_new.csv` (every new row with all columns), `rows6_carried.csv`, `monitor6_*`, `wf6_*`, `nte2_excess.csv`, `bank6.npz`.