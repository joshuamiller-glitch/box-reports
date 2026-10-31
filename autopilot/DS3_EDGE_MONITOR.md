# DS3_EDGE_MONITOR - T-RECENT-EDGE section 4: when does a recent edge stop? (RE-2, 2026-10-31)

Prereg `l2vast/ds3/prereg/RE2_prereg.md` sha256 5eb81c3287b4f232f680f7651669585958440b8883d72cba4d002cd6ee702e9b (logged in DECISIONS.md before any series was scored). Code `l2vast/ds3/code/recentedge2/` (re2_bank, re2_monitor, re2_monitor_report, re2_mkmonitor), outputs `l2vast/ds3/out/recentedge2/`. Masks capped at label day 20260206; UNTOUCHED never read. Side `followup_re2`.

## PAGE 1 - the answer

**Units, read this first.** Every series below is the *weekly lock-engine stack delta* of a rule versus the same base without the rule (N basis, research lots; live lots A = research / 2.35), re-computed from the stored STACK-2 cells (202 cell-scopes) and from new row-multiplier runs of the same engine (ER-5m sizers/gates, skip-after-loser, skip-first-30/60-min, session and book on/off/size; 104 runs), 294 unique series after removing identical ones (306 before). That is the part of the ledger whose monthly/weekly series can be recovered. Rows whose programs stored only window aggregates (BARS-CAND, sub-minute MA, C2, 70% take/tighten, EINT2, ensemble) have NO series: they cannot be monitored and are listed in DS3_RECENT_EDGE_FINAL.md as profile-only. The Z2 weekly cells (5,271 unique) are monitored in section 5 of this file; their stored weekly units are zones2 per-trade sums, not lock-engine stack.

1. **The sentence.** Over 2024-01..2026-02 the monitor (prereg rule: STOPPED when the CUSUM passes 4 sigma or when both the 13-week and the 4-week mean are <= 0) flagged the end of the typical bank edge **4 weeks after it stopped paying** (median; interquartile 1 to 9 weeks; 'stopped paying' = the first week after which both the next 13 and next 26 weeks sum to <= 0), flagged every edge that did die (every ON episode ends in a flag sooner or later, so 'flagged' is not a skill statement; the lag is), and **283 of 747 flags (38%) were false alarms** (the rule earned > 0 over the 13 weeks after the flag). That is 162 rule-years of ON time, i.e. **1.75 false alarms per ON rule-year**, or about **135 per calendar year over the whole bank = 77 distinct correlation clusters that ever raised one** (the bank is 120 clusters of near-duplicates, so divide the bank-level counts by ~2.5).
2. **Does a flag mean anything?** Weak. Forward 13-week mean after a week labelled STOPPED has P(>0) = 0.40; after STABLE 0.39; after FADING 0.41; after RISING 0.45; after NEW 0.37. The difference between STOPPED and STABLE is inside noise (block-shuffled twins of the same series give 0.45 vs 0.47). **Every ON status has a negative forward mean (-0.10 to -0.06 weekly sigmas), worse than the noise twins (-0.05 to -0.01).** The monitor separates dying from living edges only in the sense that nearly all ON episodes in this bank die (of 793 resolved ON episodes 92% died by the 13+26-week criterion): there are almost no healthy edges for it to protect.
3. **Current board (2026-02-06, 294 unique series, 120 clusters).** All series: OFF 137, NEW 64, RISING 43, STABLE 36, FADING 9, STOPPED 5. Cluster representatives only: OFF 53, NEW 24, RISING 19, STABLE 19, FADING 3, STOPPED 2. 92% of the L6M gain of the first-stop Asia cut falls since 2025-10-01 (STACK-2): it turned on in the latest regime; nothing in 2024 predicted it.
4. **Regime check.** At 76% of the flags the day-vol tercile that carried the rule (over its trailing 26 weeks) was still present at the flag (4-week share >= 70% of the 26-week share); at the other 24% it was absent. Flags with the regime absent were followed by a non-positive 13-week outcome 36% of the time, flags with the regime present 56% of the time - the regime check is not a usable discriminator in the direction one would hope for (a flag with the carrying regime still present is the more reliable stop).
5. **Honest limit.** The CUSUM at 4 sigma on the weekly stack delta, taken alone, flags 56% of the edges that died, with a median lag of 16 weeks (h = 2 sigma: 93% flagged, 9 weeks, 38% false alarms; see the sensitivity table); in the preregistered monitor it was the first trigger in only 24 of 747 flags because the 'both 13- and 4-week mean <= 0' leg fires earlier. The weekly sigma of a stack delta is 5-10x its weekly mean, so neither leg has much power at this sample size, and the second leg flaps (an edge can be flagged STOPPED, turn ON again and be flagged again).

## 1. Method (as preregistered)

* ON at week t: trailing 13-week mean > 0 and trailing 26-week mean > 0 (both from weeks <= t). NEW for the first 4 ON weeks; RISING if m13 > 1.25 m26 and m4 >= m13; FADING if CUSUM > 2 sigma, or z4 <= -1.5, or m13 < 0.5 m26; STOPPED if CUSUM > 4 sigma or (m13 <= 0 and m4 <= 0); otherwise STABLE. A STOPPED rule is OFF until it is ON again (a new episode).
* CUSUM: S_t = max(0, S_{t-1} + (mu_ref - x_t) - 0.5 sigma), mu_ref = trailing 26-week mean on the ON date, sigma = standard deviation of the weekly series of the weeks seen so far (>= 26). For the live board at 2026-02-06 that is the same expanding sigma (PRE-window sigma is included in it; PRE = 2024-02..2025-06 weeks).
* z4 = (4-week mean - 26-week mean) / (sigma / 2).
* Regime check: for each rule the day-vol tercile (library tag `vol_tag_entry_day`, a same-day label, so this is a monitor not a predictor) with the highest mean $/day over the trailing 26 weeks is its carrier; 'present' = the carrier's share of days in the last 4 weeks >= 70% of its 26-week share.
* Back-test: every ON episode of every rule from 2023-10 on. Truth (hindsight, independent of the monitor): the edge died at the first week d >= episode start whose next 13 and next 26 weeks both sum <= 0. Lag = flag week - d (negative = flagged before d). A flag is a false alarm when the next 13 weeks sum > 0.

## 2. Back-test (2024-2026)

| quantity | value |
|---|---|
| ON episodes started (2023-10..2026-02) | 1108 (resolved for death: 860; died 793, did not die 67) |
| died episodes that were flagged | 100% |
| lag flag - death, weeks: median / quartiles / 90th percentile | 4 / 1, 9 / 13 |
| share of flags that came BEFORE the death date (negative lag) | 21% |
| flags 2024-01..2026-02 | 747 (384 followed by a non-positive 13 weeks, 283 false alarms, 80 unresolved at the data edge) |
| false alarms per ON rule-year / per calendar year (bank) / per calendar year (distinct clusters) | 1.75 / 135 / 37 |

By group (flags, false-alarm share, median lag in weeks):

| group | flags | false alarms | median lag |
|---|---|---|---|
| entry filter / regime | 103 | 28% | 5 |
| sizing | 151 | 40% | 4 |
| stack cut/cap | 493 | 39% | 5 |

State-conditional forward value (mean 13-week forward weekly delta, in weekly sigmas, and P(>0)); real series vs block-shuffled twins:

| status | n week-rules | P(fwd13 > 0) real | P(fwd13>0) noise twin | fwd mean (sigma) real | noise twin |
|---|---|---|---|---|---|
| NEW | 2779 | 0.37 | 0.41 | -0.103 | -0.054 |
| RISING | 900 | 0.45 | 0.45 | -0.057 | -0.028 |
| STABLE | 2961 | 0.39 | 0.47 | -0.095 | -0.015 |
| FADING | 1173 | 0.41 | 0.48 | -0.074 | -0.008 |
| STOPPED | 876 | 0.40 | 0.45 | -0.085 | -0.028 |

Sensitivity (NOT preregistered; shows why the CUSUM leg is weak): CUSUM-only flag at h sigma, first crossing inside the 52 weeks after the ON date:

| h | episodes | flagged | flagged share of died | median lag (wk) | false-alarm share |
|---|---|---|---|---|---|
| 2 | 1108 | 796 | 93% | 9 | 38% |
| 3 | 1108 | 623 | 75% | 14 | 35% |
| 4 | 1108 | 452 | 56% | 16 | 34% |

## 3. Named edges: status path

| rule | episode start | flag (why) | death date (hindsight) | lag (wk) | 13-wk outcome after flag ($, research lots) |
|---|---|---|---|---|---|
| fs|P=50|stoppedSession=asia [S73] | 2024-03-04 | 2024-04-29 (m13,m4<=0) | 2024-10-07 | -23 | -61,641 |
| fs|P=50|stoppedSession=asia [S73] | 2024-08-12 | 2025-01-06 (m13,m4<=0) | 2024-10-07 | 13 | -5,580 |
| fs|P=50|stoppedSession=asia [S73] | 2025-07-07 | 2025-09-15 (m13,m4<=0) | - |  | 166,561 |
| fs|P=50|stoppedSession=asia [S73] | 2025-10-13 | still ON () | - |  |  |
| fs|P=50|stoppedSession=asia [MKT] | 2023-10-02 | 2023-10-09 (m13,m4<=0) | 2023-10-02 | 1 | 55,356 |
| fs|P=50|stoppedSession=asia [MKT] | 2024-02-26 | 2024-04-08 (m13,m4<=0) | 2024-10-07 | -26 | 8,348 |
| fs|P=50|stoppedSession=asia [MKT] | 2024-04-15 | 2024-06-03 (m13,m4<=0) | 2024-10-07 | -18 | 125,872 |
| fs|P=50|stoppedSession=asia [MKT] | 2024-06-10 | 2024-06-17 (m13,m4<=0) | 2024-10-07 | -16 | 83,204 |
| fs|P=50|stoppedSession=asia [MKT] | 2024-06-24 | 2024-07-01 (m13,m4<=0) | 2024-10-07 | -14 | 96,828 |
| fs|P=50|stoppedSession=asia [MKT] | 2024-07-08 | 2024-07-15 (m13,m4<=0) | 2024-10-07 | -12 | 238,836 |
| fs|P=50|stoppedSession=asia [MKT] | 2024-09-02 | 2025-01-06 (m13,m4<=0) | 2024-10-07 | 13 | -101,436 |
| fs|P=50|stoppedSession=asia [MKT] | 2025-08-11 | 2025-09-15 (m13,m4<=0) | - |  | 354,190 |
| fs|P=50|stoppedSession=asia [MKT] | 2025-09-29 | still ON () | - |  |  |
| ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | 2023-09-25 | 2023-11-06 (m13,m4<=0) | 2023-09-25 | 6 | 8,330 |
| ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | 2024-01-29 | 2024-02-26 (m13,m4<=0) | 2024-08-05 | -23 | 98,380 |
| ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | 2024-04-15 | 2024-11-11 (CUSUM) | 2024-08-05 | 14 | -212,553 |
| ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | 2024-12-16 | 2025-01-06 (m13,m4<=0) | 2024-12-16 | 3 | -645,512 |
| ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | 2025-09-08 | 2025-10-06 (m13,m4<=0) | - |  | 23,520 |
| ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | 2025-10-13 | 2025-10-20 (m13,m4<=0) | - |  | 87,779 |
| ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | 2026-01-05 | 2026-01-12 (m13,m4<=0) | - |  |  |
| ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | 2026-01-19 | still ON () | - |  |  |
| skip 2nd same-dir signal in same book within 30 min after a LOSER [S73] | 2024-07-22 | 2024-11-11 (m13,m4<=0) | 2024-08-12 | 13 | -174,673 |
| skip 2nd same-dir signal in same book within 30 min after a LOSER [S73] | 2026-01-26 | still ON () | - |  |  |
| skip first 60 min of every session [S73] | 2023-09-25 | 2023-12-11 (m13,m4<=0) | 2023-09-25 | 11 | -214,260 |
| skip first 60 min of every session [S73] | 2024-06-10 | 2024-07-08 (m13,m4<=0) | 2024-06-10 | 4 | -77,004 |
| skip first 60 min of every session [S73] | 2026-01-26 | still ON () | - |  |  |
| fs|P=50|stopdef=0 [S73] | 2023-09-25 | 2023-10-09 (m13,m4<=0) | 2023-09-25 | 2 | -162,004 |
| fs|P=50|stopdef=0 [S73] | 2024-10-07 | 2024-12-02 (m13,m4<=0) | 2024-10-07 | 8 | -259,066 |
| fs|P=50|stopdef=0 [S73] | 2024-12-16 | 2024-12-30 (m13,m4<=0) | 2024-12-16 | 2 | -332,836 |
| fs|P=50|stopdef=0 [S73] | 2026-01-19 | still ON () | - |  |  |
| fs|P=50|oppBooks>=1 [S73] | 2023-10-02 | 2023-10-09 (m13,m4<=0) | 2024-09-02 | -47 | 23,310 |
| fs|P=50|oppBooks>=1 [S73] | 2024-01-08 | 2024-02-05 (m13,m4<=0) | 2024-09-02 | -30 | 170,966 |
| fs|P=50|oppBooks>=1 [S73] | 2024-02-19 | 2024-08-05 (m13,m4<=0) | 2024-09-02 | -4 | 108,314 |
| fs|P=50|oppBooks>=1 [S73] | 2024-08-19 | 2024-12-02 (m13,m4<=0) | 2024-09-02 | 13 | -101,257 |
| fs|P=50|oppBooks>=1 [S73] | 2025-05-19 | 2025-09-29 (m13,m4<=0) | - |  | 99,651 |
| fs|P=50|oppBooks>=1 [S73] | 2025-10-20 | 2025-12-08 (m13,m4<=0) | - |  |  |
| fs|P=50|oppBooks>=1 [S73] | 2025-12-15 | still ON () | - |  |  |
| fs|P=50|er20_5m>=0.4 [S73] | 2023-09-25 | 2023-10-09 (m13,m4<=0) | 2024-10-28 | -55 | -15,571 |
| fs|P=50|er20_5m>=0.4 [S73] | 2023-10-16 | 2023-11-20 (m13,m4<=0) | 2024-10-28 | -49 | 51,330 |
| fs|P=50|er20_5m>=0.4 [S73] | 2024-01-29 | 2024-06-03 (m13,m4<=0) | 2024-10-28 | -21 | 201,881 |
| fs|P=50|er20_5m>=0.4 [S73] | 2024-08-19 | 2024-12-30 (m13,m4<=0) | 2024-10-28 | 9 | 112,876 |
| fs|P=50|er20_5m>=0.4 [S73] | 2025-03-17 | 2025-04-28 (m13,m4<=0) | 2025-03-17 | 6 | -49,164 |
| fs|P=50|er20_5m>=0.4 [S73] | 2026-02-02 | still ON () | - |  |  |

## 4. The live board (2026-02-06): cluster representatives that are not OFF, by L3M $/week at live lots A

| rule | status (since) | prev | 4w / 13w / 26w $/wk research | 13w $/wk live A | CUSUM (sigma) | z4 | carrier vol tercile present? | persistence (noise-adj, local) | shrunk expectation $/wk research | streak (wk) |
|---|---|---|---|---|---|---|---|---|---|---|
| fs|P=50|block=1800s [MKT] | RISING (2025-12-15) | STABLE | 104,422 / 64,179 / 35,761 | 27,310 | 0.0 | +2.3 | tercile 2: yes (0.45 -> 0.60) | 0.42 | 0 | 13 |
| ER sizer x1.5 above .4 / x0.5 below .3 [MKT] | RISING (2026-01-26) | STABLE | 76,835 / 55,908 / 26,189 | 23,790 | 0.0 | +1.4 | tercile 2: yes (0.45 -> 0.60) | 0.47 | 0 | 3 |
| skip first 60 min of every session [MKT] | RISING (2026-01-26) | STABLE | 88,088 / 51,999 / 15,691 | 22,127 | 0.0 | +1.4 | tercile 2: yes (0.45 -> 0.60) | 0.54 | 0 | 3 |
| ER gate: skip 5m ER20<0.2 [MKT] | NEW (2026-01-19) | OFF | 48,780 / 47,295 / 15,514 | 20,126 | 0.0 | +0.8 | tercile 0: NO (0.30 -> 0.05) | 0.53 | 0 | 3 |
| fs|P=50|voltercile>=1 [MKT] | RISING (2026-01-19) | STABLE | 70,578 / 38,041 / 19,365 | 16,188 | 0.0 | +2.5 | tercile 1: yes (0.25 -> 0.35) | 0.42 | 0 | 17 |
| ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | NEW (2026-01-19) | STOPPED | 71,907 / 37,472 / 9,864 | 15,946 | 0.0 | +1.7 | tercile 2: yes (0.45 -> 0.60) | 0.42 | 0 | 3 |
| fs|P=75|stopdef=0 [S73] | NEW (2026-01-19) | OFF | 81,209 / 36,316 / 12,354 | 15,454 | 0.0 | +2.4 | tercile 2: yes (0.45 -> 0.60) | 0.37 | 0 | 3 |
| fs|P=50|others<=3 [MKT] | RISING (2026-01-26) | STABLE | 64,922 / 33,808 / 21,750 | 14,386 | 0.0 | +2.5 | tercile 1: yes (0.25 -> 0.35) | 0.47 | 0 | 27 |
| session asia first-60-min skip [MKT] | NEW (2026-01-26) | OFF | 47,611 / 33,117 / 6,096 | 14,092 | 0.0 | +1.0 | tercile 2: yes (0.45 -> 0.60) | 0.52 | 0 | 2 |
| fs|P=50|stoppedSession!=london [MKT] | RISING (2026-02-02) | STABLE | 61,342 / 32,023 / 24,407 | 13,627 | 0.0 | +1.6 | tercile 2: yes (0.45 -> 0.60) | 0.47 | 0 | 17 |
| fs|P=50|others<=2 [MKT] | RISING (2026-01-19) | STABLE | 62,977 / 28,221 / 12,522 | 12,009 | 0.0 | +3.7 | tercile 2: yes (0.45 -> 0.60) | 0.43 | 0 | 8 |
| skip 2nd same-dir signal in same book within 30 min after a LOSER [MKT] | RISING (2026-01-19) | FADING | 63,779 / 27,036 / 11,659 | 11,505 | 0.0 | +2.9 | tercile 2: yes (0.45 -> 0.60) | 0.55 | 0 | 3 |
| fs|P=50|er20_5m>=0.2 [MKT] | RISING (2026-01-26) | STABLE | 43,402 / 26,919 / 15,345 | 11,455 | 0.0 | +1.4 | tercile 1: yes (0.25 -> 0.35) | 0.42 | 0 | 8 |
| skip any signal within 30 min after a LOSER in any book [MKT] | RISING (2026-01-26) | NEW | 48,415 / 26,744 / 8,379 | 11,380 | 0.0 | +1.0 | tercile 0: NO (0.30 -> 0.05) | 0.50 | 0 | 3 |
| ft|MAE+10|others>=1 [MKT] | NEW (2026-01-19) | STOPPED | 47,184 / 23,280 / 6,775 | 9,906 | 0.0 | +1.6 | tercile 0: NO (0.30 -> 0.05) | 0.34 | 0 | 3 |
| fs|P=50|voltercile<2 [MKT] | RISING (2026-02-02) | NEW | 36,825 / 21,562 / 11,690 | 9,175 | 0.0 | +1.3 | tercile 1: yes (0.25 -> 0.35) | 0.40 | 0 | 5 |
| fs|P=50|others<=3 [S73] | NEW (2026-01-26) | OFF | 59,613 / 21,105 / 8,414 | 8,981 | 0.0 | +3.0 | tercile 1: yes (0.25 -> 0.35) | 0.42 | 0 | 2 |
| fs|P=50|voltercile>=2 [MKT] | RISING (2026-01-19) | STABLE | 34,451 / 20,987 / 11,848 | 8,931 | 0.0 | +1.4 | tercile 2: yes (0.45 -> 0.60) | 0.43 | 0 | 17 |
| fs|P=50|er20_5m<0.3 [MKT] | STABLE (2026-01-12) | RISING | 28,185 / 20,623 / 18,825 | 8,776 | 0.0 | +0.5 | tercile 0: NO (0.30 -> 0.05) | 0.47 | 0 | 17 |
| fs|P=50|win=60m|ref=stoppedEntry [MKT] | STABLE (2026-01-26) | FADING | 43,084 / 19,370 / 17,359 | 8,242 | 0.0 | +1.3 | tercile 1: yes (0.25 -> 0.35) | 0.45 | 0 | 16 |
| ft|stackBE|others>=2 [MKT] | NEW (2026-01-26) | OFF | 72,065 / 19,182 / 2,810 | 8,162 | 0.0 | +2.3 | tercile 0: NO (0.30 -> 0.05) | 0.30 | 0 | 2 |
| fs|P=100|win=30m|ref=stoppedEntry [S73] | NEW (2026-01-26) | OFF | 54,472 / 18,676 / 8,838 | 7,947 | 0.0 | +2.0 | tercile 2: yes (0.45 -> 0.60) | 0.39 | 0 | 2 |
| session london first-60-min skip [S73] | RISING (2026-02-02) | NEW | 26,724 / 17,185 / 4,626 | 7,313 | 0.0 | +1.4 | tercile 1: yes (0.25 -> 0.35) | 0.51 | 0 | 5 |
| fs|P=50|stoppedSession=asia [S73] | RISING (2026-02-02) | STABLE | 54,649 / 17,117 / 13,611 | 7,284 | 0.0 | +2.1 | tercile 0: NO (0.30 -> 0.05) | 0.46 | 0 | 17 |
| session nypm OFF [MKT] | NEW (2026-02-02) | OFF | 27,349 / 16,186 / 3,933 | 6,888 | nan | +nan | tercile 0: NO (0.30 -> 0.05) | 0.55 | 0 | 1 |
| skip first 30 min of every session [S73] | NEW (2026-01-26) | OFF | 54,999 / 16,008 / 1,200 | 6,812 | 0.0 | +1.4 | tercile 2: yes (0.45 -> 0.60) | 0.51 | 0 | 2 |
| fs|P=25|stopdef=0 [MKT] | RISING (2026-02-02) | STABLE | 40,305 / 15,385 / 11,441 | 6,547 | 0.0 | +1.6 | tercile 1: yes (0.25 -> 0.35) | 0.44 | 0 | 6 |
| fs|P=50|win=20m|ref=stoppedEntry [MKT] | NEW (2026-01-12) | OFF | 37,606 / 14,237 / 7,726 | 6,058 | 0.0 | +2.4 | tercile 1: yes (0.25 -> 0.35) | 0.42 | 0 | 4 |
| fs|P=50|win=30m|ref=stoppedEntry [MKT] | STABLE (2026-01-26) | FADING | 36,520 / 14,133 / 12,784 | 6,014 | 0.0 | +1.5 | tercile 1: yes (0.25 -> 0.35) | 0.43 | 0 | 20 |
| session london x0.5 [MKT] | NEW (2026-01-26) | OFF | 36,341 / 14,060 / -2,853 | 5,983 | 0.0 | +1.6 | tercile 1: yes (0.25 -> 0.35) | 0.44 | 0 | 0 |
| fs|P=50|er20_5m<0.4 [S73] | RISING (2026-01-26) | FADING | 34,812 / 13,813 / 4,947 | 5,878 | 0.0 | +1.5 | tercile 0: NO (0.30 -> 0.05) | 0.37 | 0 | 2 |
| fs|P=50|er20_5m<0.2 [MKT] | RISING (2026-02-02) | STABLE | 23,305 / 12,729 / 9,124 | 5,417 | 0.4 | +1.0 | tercile 2: yes (0.45 -> 0.60) | 0.43 | 0 | 17 |
| fs|P=50|stoppedSession!=asia [MKT] | STABLE (2026-02-02) | RISING | 6,876 / 11,381 / 5,714 | 4,843 | 0.0 | +0.1 | tercile 1: yes (0.25 -> 0.35) | 0.37 | 0 | 6 |
| cap|live=6|x2.35|mode=skip|session=pre|count=openAll [MKT] | STABLE (2026-01-12) | NEW | -5,238 / 11,194 / 5,788 | 4,764 | 0.3 | -0.8 | tercile 1: yes (0.25 -> 0.35) | 0.41 | 0 | 8 |
| fs|P=50|win=60m|ref=stackFirstEntry [MKT] | NEW (2026-01-26) | OFF | 45,986 / 11,140 / 7,957 | 4,741 | 0.0 | +2.8 | tercile 1: yes (0.25 -> 0.35) | 0.45 | 0 | 2 |
| fs|P=25|stoppedSession=asia [MKT] | STABLE (2026-02-02) | FADING | 47,056 / 11,036 / 11,879 | 4,696 | 0.0 | +2.2 | tercile 1: yes (0.25 -> 0.35) | 0.53 | 0 | 2 |
| book HM x0.5 [MKT] | NEW (2026-01-26) | OFF | 24,794 / 10,683 / 3,684 | 4,546 | 0.0 | +1.4 | tercile 0: NO (0.30 -> 0.05) | 0.44 | 0 | 2 |
| fs|P=50|er20_5m>=0.3 [S73] | STABLE (2026-02-02) | NEW | 10,394 / 10,528 / 2,772 | 4,480 | 0.0 | +0.4 | tercile 1: yes (0.25 -> 0.35) | 0.36 | 0 | 5 |
| fs|P=50|stoppedSession=london [MKT] | STABLE (2026-02-02) | RISING | 3,623 / 9,656 / 5,574 | 4,109 | 0.0 | -0.1 | tercile 1: yes (0.25 -> 0.35) | 0.40 | 0 | 6 |
| fs|P=50|asia&voltercile>=2 [S73] | NEW (2026-01-26) | OFF | 43,790 / 9,371 / 5,772 | 3,988 | 0.0 | +2.6 | tercile 2: yes (0.45 -> 0.60) | 0.49 | 0 | 2 |

Full table (all 294 series): `out/recentedge2/monitor_current_status.csv` and `STATUS_FOR_LEDGER.csv` (status, since, previous, numbers) - this is the file for the RE-1 ledger hook (RE-1's hook did not exist when this was written; join key = `rule`). Weekly status matrix: `monitor_status_matrix.npy`. Episodes: `monitor_episodes.csv`. Transitions: `monitor_transitions.csv`.

## 5. Z2 11-line set and the other zones cells (weekly stored series)
5271 unique non-empty weekly series (A = 11-line SET family, L = line-id family). Status at 2026-02-06: OFF 2804, STABLE 1227, NEW 525, RISING 355, FADING 249, STOPPED 111. Persistence (ON at month M -> next 13 weeks, 2023-10..2025-11 decisions, 1,500 cells): P(next 13 w > 0) real 0.49 vs noise twin 0.47; keep-ratio (forward/in-sample magnitude) real -0.16 vs twin -0.20. The Z2 edges do not persist better than noise. Top ON cells: `z2_current_status.csv` (e.g. ARR|iFVG|4h lid 30pt skip/rt: STABLE, 13-week mean ~500 per week, PRE mean negative, X' mean negative = recent-only).

## 6. What this means

* The monitor works as a bookkeeping device (it records NEW/RISING/STABLE/FADING/STOPPED with dates, see EDGE_STATUS_LOG.md) but, on this bank, it is not a risk control: the dates it gives are 4 weeks after the edge stopped paying, and 38% of its stops are followed by a profitable quarter. Treat STOPPED as 'drop to shadow', not as proof the edge is gone.
* The larger result is in section 2 of the sentences above: the statuses NEW, RISING and STABLE are not followed by a positive quarter more often than a block-shuffled twin of the same series. A status of STABLE is not evidence that the edge will continue.