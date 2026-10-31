# DS3_RECENT_EDGE_FINAL - T-RECENT-EDGE (RE-2: monitor, portfolio, re-examination, new cycles). Data to label day 20260206. Written 2026-10-31T04:23Z

Companion pages: DS3_EDGE_MONITOR.md (section 4), DS3_RECENT_PORTFOLIO.md (section 3), EDGE_STATUS_LOG.md (transitions). RE-1 owns the persistence study and the ledger columns (DS3_PERSISTENCE.md, RECENT_WINS.md); where RE-1 had published interim numbers they are quoted and labelled interim. Prereg `l2vast/ds3/prereg/RE2_prereg.md` sha256 5eb81c3287b4f232f680f7651669585958440b8883d72cba4d002cd6ee702e9b (DECISIONS.md, before scoring). Code `l2vast/ds3/code/recentedge2/`, outputs `l2vast/ds3/out/recentedge2/`, UF_TRIALS side `followup_re2`. UNTOUCHED never read; masks capped at 20260206; selection at month M used only earlier weeks.

## PAGE 1 - the plain answers

**Units.** Unless a table says otherwise: lock-engine stack, 70/30 split base, basis N, research lots, $ per week, delta against the same stack without the edge; live lots A = research / 2.35 (live lots per FOLLOWUP_BRIEF: K6 2, P6 7, U6 4, H6 4/2, M6 2, A6 1, O6 1 are not mapped per book here; the A mapping is the one used by STACK-2 and the follow-ups). Families whose programs stored per-trade results use 'pts per planned lot' and say so. Tier of everything in this file: LEAD or below; nothing is PASS.

1. **What is working now, is it real enough, is it still working?** Over 2024-26 the answer on this box's data is: *recent edges are real in the window they were found and do not persist well enough to size up.* RE-1's interim persistence curve over ~340k real (rule, month) pairs: a rule positive over the last 3 and 6 months is positive over the next 3 months **40.0%** of the time (coin = 50.0%, a noise twin that has the same selection effect = 43.9%); by family: entry filter 50.1%, sizing 50.8%, entry structure 38.1%, exit 44.4%, confirmation 32.7%, stack 17.4%, regime 20.7% (RE-1 interim `curve_by_month.csv`; the final numbers are in DS3_PERSISTENCE.md). My independent bank of recoverable stack series gives the same: P(next 13 weeks > 0 | ON) = 0.40 real vs 0.44 noise twin, and the forward mean after selection is negative (keep ratio -0.60 real, -0.29 twin).
2. **Portfolio walk-forward (DS3_RECENT_PORTFOLIO.md).** Rebuilding the ledger every month from earlier data and running its edges on the real lock engine: full size -9,598 $/wk over 2024-01..2026-01 (MDE 27,130; 10 of 25 months positive; 2024 -3,253, 2025 -22,128, Jan 2026 +59,813); half size -7,353; shrunk Kelly size -5,531; doing nothing 0. Screening by persistence >= 0.7 earns +213 on 11 active months (zero within noise). Worst month at full size -740,076 (2024-07), when many ON edges reversed together. The honest test of the user's approach says: not demonstrated.
3. **Monitor (DS3_EDGE_MONITOR.md).** The monitor flags a dead edge a median 4 weeks (quartiles 1-9) after it stopped paying and 38% of its flags are false alarms (1.75 per ON rule-year; 283 of 747 flags). A status of NEW, RISING or STABLE is not followed by a positive quarter more often than a block-shuffled twin of the same series (P 0.37 / 0.45 / 0.39 vs 0.41 / 0.45 / 0.47). Use it as the dashboard and as the 'drop to shadow' trigger, not as a licence to size up.
4. **Who is ON today (2026-02-06).** 69 S73-base bank edges are ON, in 35 correlation clusters, and those 35 are about 4 distinct bets: (i) cut the other books when the first stops (25 variants), (ii) the pre-session same-side cap, (iii) skip the opening hour / after losers, (iv) the ER-5m sizer. All four are positive in L3M and L6M and negative or flat in PRE (2024-02..2025-06): the lock-engine stack on today's ledger earns +64k/wk (MDE 83k) in L3M, +9k in L6M and -58k/wk (MDE 39k) in PRE at full size. The one bank edge that is positive in all five windows and ON with persistence >= 0.5 is the first-stop cut when a book is open on the other side (S2 LEAD).
5. **Per-edge one line (cluster representatives).** 'run at 25% size, review monthly' for the ones that pass every check I can run, 'shadow' for recent-only, 'no' otherwise: see section 1. Result: 1 run-at-25%, the rest shadow or no. In this file nothing is recommended above 25% size; the data do not support a higher number.
6. **The new cycles.** (a) Pure recent-fit chains (rules fitted on the last 26 weeks only, 1-month forward test rolled through 2024-26): the first-stop cut family chain earns +2.5k/wk (MDE 10k; random cell in the family -3.1k; chain above the 95th percentile of random-cell chains), the same-side cap chain +1.7k (MDE ~10k), the book/session on-off chain +0.5k, the ER sizer chain -4.0k, the skip-family chain -3.1k: the chain beats a random cell in every family, the positive chains are inside their MDE, and three chains are negative (first-target mirror -15.2k, ER sizer -4.0k, skip family -3.1k). (b) The 2025-26 regime: realised 5-minute vol and signals per day have doubled since 2023 (signals/day 41 -> 82; sig_rv_5m 12.3 -> 23.9), prior-day range and overnight range up 15-25%, ES-NQ 20-minute correlation 0.86 -> 0.93, London share of signals 16% -> 22%, NY-PM 21% -> 17%, high-vol days 35% -> 47% of days, while trend persistence did NOT rise (5-min ER20 0.282 -> 0.263, Hurst 0.585 -> 0.580). Running a recent edge means betting on a high-vol, high-ES-correlation, London-heavy, non-trending-per-bar market. (c) The regime library (6-month blocks): of the first-stop cut / cap cells 78% were positive in 2023H1, then 31% / 33% / 10% / 22% in the next four half-years and 70% in 2025-10..2026-02. At the half-year scale there is persistence above the base rate: a bank rule positive in a half-year was positive in the next one 60% of the time after 2023H2 (base rate 33%), 12.5% after 2024H1 (base 12.6%: none), 35% after 2024H2 (base 19%) and 86% after 2025H1 (base 59%). At the 13-week scale (point 1) the same rules do not beat their noise twin. So: 'an edge that is on for a half-year tends to last the next half-year more often than a random rule; an edge that has just turned on for a quarter does not' - and the most recent transition (2025H1 to 2025H2) is the strongest.

## 1. The board: cluster representatives that are ON (35), recommended action

Windows are weekly means of the stack delta ($/wk, research lots); L3M = 2025-11-06..2026-02-06, L6M = 2025-08-01..2026-02-06, HOLD = 2025-07-01..2026-02-06, PRE = 2024-02-01..2025-06-30, X' = 2023-04-01..2024-01-31. Persistence = noise-adjusted first pass (0.5 = same as the block-shuffled twin); RE-1's score supersedes it when published. Shrunk expectation = 0 for every edge (the pooled forward/trailing ratio on earlier months is negative for each group).

Top 10 by L3M live-lot $/wk x persistence score:

| rank | edge | status (since) | 13-week mean $/wk research (to 2026-02-02) | live A | persistence | score | action |
|---|---|---|---|---|---|---|---|
| 1 | fs|P=50|block=hour [S73] | RISING (2026-01-12) | 50,756 | 21,598 | 0.37 | 7,884 | shadow |
| 2 | ER sizer x1.5 above .4 / x0.5 below .3 [S73] | NEW (2026-01-19) | 39,271 | 16,711 | 0.45 | 7,541 | shadow |
| 3 | skip first 60 min of every session [S73] | NEW (2026-01-26) | 35,389 | 15,059 | 0.50 | 7,517 | shadow |
| 4 | fs|P=100|stopdef=0 [S73] | NEW (2026-01-26) | 39,261 | 16,707 | 0.33 | 5,593 | shadow |
| 5 | fs|P=50|rearm=1 [S73] | NEW (2026-01-19) | 27,265 | 11,602 | 0.37 | 4,276 | shadow |
| 6 | session london first-60-min skip [S73] | RISING (2026-02-02) | 17,185 | 7,313 | 0.51 | 3,747 | shadow |
| 7 | fs|P=50|others<=3 [S73] | NEW (2026-01-26) | 21,105 | 8,981 | 0.42 | 3,738 | shadow |
| 8 | skip first 30 min of every session [S73] | NEW (2026-01-26) | 16,008 | 6,812 | 0.51 | 3,462 | shadow |
| 9 | fs|P=50|stoppedSession=asia [S73] | RISING (2026-02-02) | 17,117 | 7,284 | 0.46 | 3,347 | shadow |
| 10 | fs|P=50|voltercile>=1 [S73] | RISING (2026-01-12) | 20,037 | 8,526 | 0.39 | 3,287 | shadow |

All 35 representatives:

| edge | status | L3M | L6M | HOLD | PRE | X' | persistence | action |
|---|---|---|---|---|---|---|---|---|
| fs|P=50|block=hour [S73] | RISING | 46,410 | 19,162 | 16,467 | -12,812 | -1,758 | 0.37 | shadow |
| skip first 60 min of every session [S73] | NEW | 32,383 | 4,973 | 12,272 | -31,434 | 11,305 | 0.50 | shadow |
| ER sizer x1.5 above .4 / x0.5 below .3 [S73] | NEW | 31,207 | 12,495 | 11,939 | -10,794 | 3,987 | 0.45 | shadow |
| fs|P=100|stopdef=0 [S73] | NEW | 29,026 | 4,711 | 3,156 | -9,552 | 337 | 0.33 | shadow |
| fs|P=50|rearm=1 [S73] | NEW | 21,597 | 8,764 | 5,488 | -8,919 | -949 | 0.37 | shadow |
| session london first-60-min skip [S73] | RISING | 16,672 | 5,714 | 3,679 | -6,897 | 1,906 | 0.51 | shadow |
| fs|P=50|others<=3 [S73] | NEW | 15,304 | 6,676 | 6,045 | -1,457 | 4,052 | 0.42 | shadow |
| fs|P=50|voltercile>=1 [S73] | RISING | 14,307 | 7,311 | 7,814 | -1,679 | 2,606 | 0.39 | shadow |
| fs|P=50|er20_5m>=0.2 [S73] | NEW | 13,195 | 4,717 | 5,062 | -7,359 | -1,149 | 0.38 | shadow |
| fs|P=50|stoppedSession=asia [S73] | RISING | 12,406 | 13,579 | 11,463 | 2,043 | 2,844 | 0.46 | shadow |
| fs|P=50|voltercile<2 [S73] | NEW | 11,997 | 3,190 | 1,181 | -6,178 | -3,956 | 0.37 | shadow |
| fs|P=50|er20_5m<0.4 [S73] | RISING | 9,519 | 4,761 | 3,007 | -10,014 | 277 | 0.37 | shadow |
| skip first 30 min of every session [S73] | NEW | 8,847 | 567 | 5,353 | -25,836 | 2,787 | 0.51 | shadow |
| fs|P=50|er20_5m>=0.3 [S73] | STABLE | 8,813 | 3,240 | 4,209 | 576 | -2,280 | 0.36 | shadow |
| book HM x0.5 [S73] | NEW | 8,703 | -459 | -1,112 | -5,937 | -2,785 | 0.41 | no |
| skip any signal within 30 min after a LOSER in any book [S73] | NEW | 5,988 | 2,762 | -1,334 | -31,604 | -23,951 | 0.47 | shadow |
| fs|P=50|asia&voltercile>=2 [S73] | NEW | 5,783 | 7,001 | 6,501 | 4,635 | 4,786 | 0.49 | shadow |
| fs|P=100|win=30m|ref=stoppedEntry [S73] | NEW | 5,335 | 8,351 | 6,937 | -11,560 | -5,419 | 0.39 | shadow |
| ft|MAE+10|others>=1 [S73] | NEW | 5,021 | 3,297 | 2,012 | -19,175 | -8,729 | 0.35 | shadow |
| fs|P=25|stopdef=0 [S73] | NEW | 4,728 | 4,191 | 3,158 | -7,329 | 1,208 | 0.41 | shadow |
| skip 2nd same-dir signal in same book within 30 min after a LOSER [S73] | NEW | 4,633 | 464 | 1,596 | -4,321 | -9,909 | 0.51 | shadow |
| cap|live=6|x2.35|mode=skip|session=pre|count=both100 [S73] | STABLE | 4,613 | 4,941 | 5,987 | 1,815 | -1,217 | 0.45 | shadow |
| fs|P=50|stoppedSession=pre [S73] | STABLE | 3,573 | 1,919 | 2,385 | -36 | -69 | 0.40 | shadow |
| fs|P=50|oppBooks>=1 [S73] | STABLE | 3,407 | 4,934 | 4,623 | 2,845 | 4,220 | 0.51 | run at 25% size, review monthly (monitor: drop at STOPPED) |
| fs|P=50|win=60m|ref=stackFirstEntry [S73] | NEW | 3,109 | 120 | 1,104 | -5,963 | 588 | 0.34 | shadow |
| fs|P=50|win=10m|ref=stoppedEntry [S73] | NEW | 3,045 | 989 | 850 | 2,106 | -531 | 0.37 | shadow |
| fs|P=50|win=5m|ref=stoppedEntry [S73] | RISING | 2,899 | 810 | 374 | 872 | -644 | 0.36 | shadow |
| fs|P=50|voltercile<1 [S73] | NEW | 2,410 | -500 | -3,068 | -4,902 | -3,058 | 0.36 | no |
| book SM x1.5 [S73] | FADING | 2,184 | 4,534 | 5,395 | 941 | 3,561 | 0.57 | shadow (FADING) |
| book WT x1.5 [S73] | STABLE | 2,144 | 3,689 | 2,790 | 2,257 | -540 | 0.52 | shadow |
| cap|live=10|x2.35|mode=skip|session=pre|count=openAll [S73] | STABLE | 1,984 | 2,018 | 1,849 | 3,769 | -663 | 0.47 | shadow |
| fs|P=50|asia&er20_5m>=0.4 [S73] | NEW | 1,844 | 1,960 | 695 | 3,402 | 3,025 | 0.48 | shadow |
| session close OFF [S73] | NEW | 918 | 461 | 724 | 87 | -250 | 0.64 | shadow |
| fs|P=50|er20_5m>=0.4 [S73] | NEW | 112 | 957 | 612 | 3,716 | 898 | 0.44 | shadow |
| fs|P=50|win=30m|ref=stoppedEntry [S73] | NEW | -2,051 | 4,467 | 4,156 | -8,029 | -3,006 | 0.45 | no |

Count by status (representatives): NEW 22, RISING 6, STABLE 6, FADING 1. All 294 unique series: NEW 64, RISING 43, STABLE 36, FADING 9, STOPPED 5, OFF 137.

**This month (weeks of 2026-01-12 .. 2026-02-02), cluster representatives.** Turned ON: fs|P=50|win=20m|ref=stoppedEntry MKT; book WT x1.5 MKT; ER gate: skip 5m ER20<0.2 MKT; book KB x1.5; ER sizer x1.5/x0.5 at 5m ER20>=0.3; ft|MAE+10|others>=1 MKT. FADED: fs|P=50|stoppedSession=pre; fs|P=50|win=30m|ref=stoppedEntry MKT; book SM x1.5; session pre OFF; fs|P=25|stoppedSession=asia MKT; book PE x1.5. STOPPED: ft|MAE+10|others>=1 MKT; session asia first-60-min skip MKT; book KB x1.5; fs|P=100|win=30m|ref=stoppedEntry; ER sizer x1.5/x0.5 at 5m ER20>=0.3; fs|P=50|asia&voltercile>=2. (The monitor's weekly transition list is in EDGE_STATUS_LOG.md.)

## 2. Section 5 re-examination of the buried families

Two data sources. (A) Lock-engine series that RE-2 rebuilt (monthly and weekly since 2023-04; ER-5m rules = EINT1 state, skip-after-loser = N1b, skip-first-30/60-min = N1c, first-stop cut = S2 pooled and conditioned, pre-session cap): full persistence/status/size treatment. (B) RE-1's stored monthly per-cell series (imported read-only from `out/recentedge/series/`): EINT1 (H6), EINT2 (H10), C2 (H4 G1-G5; book scopes KB and HM), the 70%-take/tighten L2SET profit family (H1), BARS-ENG (H5), CF-ENG (H3), L2SE entry (H9), SPLIT-2 (H7). (C) Programs with window aggregates only (sub-minute MA events, the 6,943 BARS-CAND rows, ensemble subsets, Z2 stack cells): profile only - no monthly series exists, so no status can be assigned and the persistence score is the profile-based value from the bank (below). BARS-CAND/BARS-ENG rows are unconditional series (PAIRFIX: paired claims were inflated; none is used).

### 2A. Rules with rebuilt series (S73 base, research lots, weekly mean $)

| family | rule | L3M | L6M | HOLD | PRE | X' | status | persistence | one line |
|---|---|---|---|---|---|---|---|---|---|
| EINT1 trend ER sizer / gate | ER sizer x1.5/x0.5 at 5m ER20>=0.2 [S73] | 8,999 | -7,149 | -6,314 | -2,451 | 10,639 | OFF | 0.48 | no (not positive in L3M, L6M and HOLD) |
| EINT1 trend ER sizer / gate | ER gate: skip 5m ER20<0.2 [S73] | 22,447 | -2,920 | -5,061 | -16,270 | -746 | OFF | 0.56 | no (not positive in L3M, L6M and HOLD) |
| EINT1 trend ER sizer / gate | ER inverse: skip 5m ER20>=0.2 [S73] | -40,122 | -65,342 | -51,785 | -60,147 | -24,586 | OFF | 0.40 | no (not positive in L3M, L6M and HOLD) |
| EINT1 trend ER sizer / gate | ER sizer x1.5/x0.5 at 5m ER20>=0.3 [S73] | 30,174 | 8,730 | 10,149 | -9,395 | 6,589 | NEW | 0.42 | shadow (recent-only: PRE <=0) |
| EINT1 trend ER sizer / gate | ER gate: skip 5m ER20<0.3 [S73] | 18,398 | -15,119 | -9,427 | -20,083 | -9,627 | OFF | 0.53 | no (not positive in L3M, L6M and HOLD) |
| EINT1 trend ER sizer / gate | ER inverse: skip 5m ER20>=0.3 [S73] | -58,741 | -72,291 | -62,292 | -45,095 | -12,843 | OFF | 0.38 | no (not positive in L3M, L6M and HOLD) |
| EINT1 trend ER sizer / gate | ER sizer x1.5/x0.5 at 5m ER20>=0.4 [S73] | 28,265 | 1,310 | 2,247 | -16,192 | 945 | NEW | 0.38 | shadow (recent-only: PRE <=0) |
| EINT1 trend ER sizer / gate | ER gate: skip 5m ER20<0.4 [S73] | 18,942 | -29,684 | -21,879 | -37,622 | -9,128 | OFF | 0.49 | no (not positive in L3M, L6M and HOLD) |
| EINT1 trend ER sizer / gate | ER inverse: skip 5m ER20>=0.4 [S73] | -51,573 | -51,856 | -45,786 | -25,430 | -10,727 | OFF | 0.41 | no (not positive in L3M, L6M and HOLD) |
| EINT1 trend ER sizer / gate | ER sizer x1.5 above .4 / x0.5 below .3 [S73] | 31,207 | 12,495 | 11,939 | -10,794 | 3,987 | NEW | 0.45 | shadow (recent-only: PRE <=0) |
| N1b skip after loser | skip 2nd same-dir signal in same book within 30 min after a LOSER [S73] | 4,633 | 464 | 1,596 | -4,321 | -9,909 | NEW | 0.51 | shadow (recent-only: PRE <=0) |
| N1b skip after loser | skip any signal in same book within 30 min after a LOSER [S73] | -11,733 | -10,352 | -8,723 | -14,896 | -21,128 | OFF | 0.53 | no (not positive in L3M, L6M and HOLD) |
| N1b skip after loser | skip any signal within 30 min after a LOSER in any book [S73] | 5,988 | 2,762 | -1,334 | -31,604 | -23,951 | NEW | 0.47 | no (not positive in L3M, L6M and HOLD) |
| N1c skip first 30/60 min, first signal | skip first 30 min of every session [S73] | 8,847 | 567 | 5,353 | -25,836 | 2,787 | NEW | 0.51 | shadow (recent-only: PRE <=0) |
| N1c skip first 30/60 min, first signal | skip first 60 min of every session [S73] | 32,383 | 4,973 | 12,272 | -31,434 | 11,305 | NEW | 0.50 | shadow (recent-only: PRE <=0) |
| N1c skip first 30/60 min, first signal | skip first signal of each book each session [S73] | 12,660 | -22,008 | -13,855 | -45,820 | -8,969 | OFF | 0.49 | no (not positive in L3M, L6M and HOLD) |
| S2 first-stop cut (pooled & conditioned) | fs|P=50|stopdef=0 [MKT] | 37,345 | 23,651 | 19,440 | -8,375 | 682 | RISING | 0.41 | shadow (recent-only: PRE <=0) |
| S2 first-stop cut (pooled & conditioned) | fs|P=100|stopdef=0 [MKT] | 27,730 | 10,681 | 7,958 | -11,842 | 1,842 | NEW | 0.37 | shadow (recent-only: PRE <=0) |
| S2 first-stop cut (pooled & conditioned) | fs|P=50|stopdef=0 [S73] | 16,717 | 6,812 | 4,644 | -6,581 | -452 | NEW | 0.37 | shadow (recent-only: PRE <=0) |
| S2 first-stop cut (pooled & conditioned) | fs|P=100|stopdef=0 [S73] | 29,026 | 4,711 | 3,156 | -9,552 | 337 | NEW | 0.33 | shadow (recent-only: PRE <=0) |
| S2 first-stop cut (pooled & conditioned) | fs|P=50|stoppedSession=asia [S73] | 12,406 | 13,579 | 11,463 | 2,043 | 2,844 | RISING | 0.46 | shadow (positive PRE, X negative) |
| S2 first-stop cut (pooled & conditioned) | fs|P=50|er20_5m>=0.4 [S73] | 112 | 957 | 612 | 3,716 | 898 | NEW | 0.44 | shadow (positive PRE, X negative) |
| S2 first-stop cut (pooled & conditioned) | fs|P=50|oppBooks>=1 [S73] | 3,407 | 4,934 | 4,623 | 2,845 | 4,220 | STABLE | 0.51 | run at 25% size, review monthly |
| S2 first-stop cut (pooled & conditioned) | fs|P=50|asia&er20_5m>=0.4 [S73] | 1,844 | 1,960 | 695 | 3,402 | 3,025 | NEW | 0.48 | shadow (positive PRE, X negative) |
| S2 first-stop cut (pooled & conditioned) | fs|P=50|er20_5m>=0.4&voltercile>=2 [S73] | 895 | -767 | -127 | 676 | -619 | OFF | 0.42 | no (not positive in L3M, L6M and HOLD) |
| S2 first-stop cut (pooled & conditioned) | fs|P=50|asia&er20_5m>=0.4&voltercile>=2 [S73] | 3,081 | -240 | -217 | 783 | 3,426 | OFF | 0.45 | no (not positive in L3M, L6M and HOLD) |
| S2 first-stop cut (pooled & conditioned) | fs|P=25|stoppedSession=asia [S73] | 5,297 | 9,072 | 7,632 | -1,239 | 2,610 | STABLE | 0.51 | shadow (recent-only: PRE <=0) |
| S2 first-stop cut (pooled & conditioned) | fs|P=100|stoppedSession=asia [S73] | 15,605 | 12,146 | 9,922 | 5,447 | 2,237 | RISING | 0.43 | shadow (positive PRE, X negative) |
| STACK-2 pre-session cap | cap|live=8|x2.35|mode=room|session=pre|count=openAll [S73] | 1,510 | 2,616 | 2,108 | 1,815 | 1,136 | FADING | 0.47 | shadow, FADING |
| STACK-2 pre-session cap | cap|live=8|x2.35|mode=room|session=pre|count=70only [S73] | 118 | 1,228 | 1,146 | 2,045 | 1,001 | FADING | 0.49 | shadow, FADING |
| STACK-2 pre-session cap | cap|live=8|x2.35|mode=room|session=pre|count=both100 [S73] | -434 | -488 | -183 | 2,223 | 803 | OFF | 0.49 | no (not positive in L3M, L6M and HOLD) |
| STACK-2 pre-session cap | cap|live=8|x2.35|mode=skip|session=pre|count=openAll [S73] | 1,373 | 2,538 | 2,752 | 3,042 | 1,111 | FADING | 0.48 | shadow, FADING |
| STACK-2 pre-session cap | cap|live=8|x2.35|mode=skip|session=pre|count=70only [S73] | 1,123 | 1,218 | 1,550 | 3,843 | 554 | STABLE | 0.47 | shadow (positive PRE, X negative) |
| STACK-2 pre-session cap | cap|live=8|x2.35|mode=skip|session=pre|count=both100 [S73] | 2,173 | 3,599 | 4,292 | 3,843 | 329 | STABLE | 0.48 | shadow (positive PRE, X negative) |

Monthly series since 2023-04 ($/week of the month, research lots, thousands) for the named S2/EINT1/N1 rules: `out/recentedge2/reexam_series_rows.csv` (columns m202304..m202602).

Family verdicts. **EINT1 / trend terciles (ER-5m sizer):** the sizer x1.5/x0.5 at ER>=0.3 is NEW (ON since January 2026 on the 13/26-week rule), +30k/wk L3M, +9k L6M, -9k PRE, +7k X': shadow; the ER gate (skip ER below the threshold) is negative in L6M and PRE: no; the inverse is deeply negative: no. **N1b skip-after-loser:** the same-book same-direction variant is +4.6k L3M, +0.5k L6M, -4.3k PRE, -9.9k X': shadow only; the any-direction and any-book versions are negative or PRE -32k: no. **N1c skip first 60 min:** +32k L3M, +5k L6M, +12k HOLD, -31k PRE, +11k X': shadow (recent-only; PRE strongly negative); skip first signal per book per session: no. **S2 first-stop cut (pooled):** MKT base P50 +37k L3M, +24k L6M, -8k PRE: shadow; the Asia-stopped cut is positive in all five windows on the S73 base (+12k, +14k, +11k, +2k, +3k) but PRE and X' are small (+2k, +3k) and its first-pass persistence is 0.46: shadow; the opposite-books variant is the only one positive in every window with persistence >= 0.5: run at 25% size.

### 2B. RE-1 monthly series (per-trade pts per planned lot, or $ per day for stack files), imported

Decision months 2023-10..2025-11; ON = trailing 3-month and 6-month mean > 0; next-3-month positive share and keep ratio (forward mean / trailing-3-month mean), real vs month-shuffled twin; statuses at 2026-01 (monthly resolution: NEW = first ON month, RISING, STABLE, FADING, STOPPED).

| family (scope) | rules | ON pairs | P(next 3 m > 0) real | noise twin | keep real | keep twin | ON now (NEW/RISING/STABLE/FADING) | STOPPED | positive in all 5 windows | recent-only |
|---|---|---|---|---|---|---|---|---|---|---|
| EINT1 trend/ER state rules (H6) (pooled) | 389 | 3,881 | 0.49 | 0.51 | -0.01 | +0.04 | 52/26/43/44 | 41 | 30 | 74 |
| EINT2 day-type rules (H10) (pooled) | 4,950 | 32,850 | 0.53 | 0.47 | -0.25 | -0.23 | 285/95/882/237 | 161 | 150 | 1,136 |
| C2 candle patterns (H4 G1-G5) (pooled) | 9,952 | 20,852 | 0.18 | 0.24 | -1.74 | -1.01 | 2/0/1/4 | 48 | 0 | 6 |
| C2 candle patterns (H4 G1-G5) (KB) | 9,952 | 31,220 | 0.38 | 0.37 | -0.50 | -0.48 | 823/1368/1220/551 | 1773 | 186 | 3,450 |
| C2 candle patterns (H4 G1-G5) (HM) | 9,952 | 19,982 | 0.19 | 0.26 | -1.19 | -0.89 | 240/89/38/66 | 167 | 3 | 406 |
| L2SET profit: 70% take/tighten rules (H1) (pooled) | 23,773 | 37,868 | 0.41 | 0.52 | -0.25 | +0.02 | 361/4363/2484/710 | 1132 | 5,027 | 2,700 |
| CF-ENG confirm stage 1 (H3) (pooled) | 560 | 2,009 | 0.22 | 0.26 | -1.35 | -0.91 | 0/0/0/0 | 1 | 0 | 0 |
| L2SE entry (H9) (pooled) | 4,251 | 21,034 | 0.23 | 0.32 | -1.14 | -0.52 | 4/21/26/115 | 475 | 10 | 141 |
| SPLIT-2 stack (H7) (pooled) | 62 | 269 | 0.33 | 0.35 | -0.70 | -0.52 | 9/1/0/0 | 0 | 0 | 10 |
| L2SET-joint stack (H7b) (pooled) | 72 | 428 | 0.51 | 0.54 | -0.02 | -0.01 | 10/26/18/0 | 0 | 12 | 42 |
| UF loss (H2) (pooled) | 1,847 | 15,935 | 0.47 | 0.50 | -0.29 | -0.16 | 110/35/127/75 | 97 | 159 | 92 |

Reading: no family persists better than its noise twin, with two exceptions: EINT2 day-type rules (P 0.53 vs 0.47, keep -0.25 vs -0.23: slightly more often positive, forward magnitude still negative) and the L2SET-joint stack lines (0.51 vs 0.54, equal). The C2 candle patterns are worse than noise pooled (0.18 vs 0.25) and equal to noise on KB (0.38 vs 0.37); HM 0.19 vs 0.26. The 70%-take/tighten L2SET profit family (H1) is worse than noise (0.41 vs 0.52, keep -0.25 vs +0.02). H1's unit string does not state the fill basis; the stored rules include take/trail exits whose M-basis target-fill correction can inflate profit rules, so treat its 5,027 'all windows positive' rules as unverified.

Best-looking ON rows per family (all five windows positive, not STOPPED; units as in the family; descriptive, 'looked', not selected). One-line decisions: shadow unless a stack/engine check exists.

| family (scope) | rule | status | streak (months) | L3M | L6M | HOLD | PRE | X' | last 6 months (Aug..Jan) | one line |
|---|---|---|---|---|---|---|---|---|---|---|
| C2 candle patterns (H4 G1-G5) (HM) | c2G1|tc|15s|C_mom4|a|near|3|W0 | FADING | 3 | 1.25 | 0.53 | 0.87 | 0.04 | 0.14 | +0.20 / -0.61 / -0.13 / +2.62 / +1.90 / -0.77 | shadow |
| C2 candle patterns (H4 G1-G5) (HM) | c2G1|tc|15s|R_tweezer|b|mid|3|A70 | NEW | 1 | 0.83 | 0.38 | 0.23 | 0.21 | 0.03 | +1.20 / -0.22 / -1.21 / +1.58 / -0.81 / +1.73 | shadow |
| C2 candle patterns (H4 G1-G5) (KB) | c2G4|tc|15s|C_mom4@ER_ge20|a|near|3|W0 | STABLE | 3 | 4.95 | 2.49 | 1.99 | 0.08 | 1.84 | -1.89 / +0.16 / +1.83 / +7.15 / +3.22 / +4.49 | shadow |
| C2 candle patterns (H4 G1-G5) (KB) | c2G4|tc|30s|C_mom3@ER_ge20|a|near|3|W0 | RISING | 3 | 4.20 | 2.01 | 1.90 | 0.30 | 0.02 | -0.13 / -4.54 / +4.11 / +5.85 / +2.22 / +4.53 | shadow |
| EINT1 trend/ER state rules (H6) (pooled) | netOneORACLE_5m | STABLE | 28 | 1.80 | 1.60 | 1.47 | 1.49 | 1.21 | +1.14 / +1.48 / +1.61 / +2.84 / +0.80 / +1.75 | shadow |
| EINT1 trend/ER state rules (H6) (pooled) | netOneORACLE_3m | STABLE | 28 | 1.58 | 1.22 | 1.13 | 1.00 | 0.92 | +0.78 / +0.88 / +0.93 / +2.55 / +0.98 / +1.22 | shadow |
| EINT2 day-type rules (H10) (pooled) | eint2|e.fhd.c2.skip|stack7 | STABLE | 4 | 4115.87 | 2798.06 | 2134.87 | 907.18 | 1722.16 | +1332.01 / -77.11 / +3185.87 / -1013.77 / +10452.59 / +2908.80 | shadow |
| EINT2 day-type rules (H10) (pooled) | eint2|e.ongap.c1.skip|stack7 | FADING | 4 | 1253.35 | 1835.62 | 1118.10 | 699.33 | 1832.08 | -930.23 / +1289.28 / +6894.65 / -1765.27 / +5918.60 / -393.30 | shadow |
| L2SE entry (H9) (pooled) | dipentry_g1|37 | RISING | 12 | 0.46 | 0.39 | 0.37 | 0.14 | 0.14 | +0.44 / -0.21 / +0.74 / +0.23 / +0.61 / +0.54 | shadow |
| L2SE entry (H9) (pooled) | dipentry_g1|41 | FADING | 13 | 0.21 | 0.33 | 0.39 | 0.16 | 0.25 | +0.70 / -0.23 / +0.87 / +0.13 / +0.45 / +0.06 | shadow |
| L2SET profit: 70% take/tighten rules (H1) (pooled) | P|sess_tot_ge1.2|armpct0.7|d10|trail30|p70always | RISING | 10 | 1.19 | 0.96 | 1.02 | 0.25 | 0.37 | +0.85 / +0.34 / +1.02 / +0.96 / +1.25 / +1.34 | shadow (basis unverified) |
| L2SET profit: 70% take/tighten rules (H1) (pooled) | P|sess_ahead_ge1.2|armpct0.7|d30|take|p70always | RISING | 10 | 1.10 | 0.96 | 1.03 | 0.25 | 0.35 | +1.14 / +0.33 / +0.99 / +0.98 / +1.07 / +1.25 | shadow (basis unverified) |
| L2SET-joint stack (H7b) (pooled) | l2sj|daily_main|H__PL__M | RISING | 4 | 6727.72 | 5604.40 | 4705.27 | 1066.92 | 2088.35 | -3193.27 / +2636.56 / +13999.98 / -6169.12 / +3709.34 / +22642.94 | shadow |
| L2SET-joint stack (H7b) (pooled) | l2sj|daily_nightly|H__PL__M | RISING | 4 | 6727.72 | 5604.40 | 4705.27 | 1066.92 | 2088.35 | -3193.27 / +2636.56 / +13999.98 / -6169.12 / +3709.34 / +22642.94 | shadow |
| UF loss (H2) (pooled) | D3|loss|avoid|cumb_le=0.5 | FADING | 4 | 0.81 | 0.45 | 0.39 | 0.26 | 0.17 | -0.18 / +0.05 / +0.41 / +1.19 / +1.20 / +0.04 | shadow |
| UF loss (H2) (pooled) | D3|loss|avoid|drel_le=0.5 | STABLE | 2 | 0.71 | 0.26 | 0.21 | 0.17 | 0.10 | -0.38 / +0.13 / -0.30 / +0.64 / +1.29 / +0.21 | shadow |

### 2C. Profile-only families (no monthly series stored)

Counts of ledger rows that are positive in L3M by construction, and how many of them are also positive elsewhere. Bank-calibrated profile persistence: a rule ON over 3 and 6 months whose earlier year (PRE analogue) was NOT positive is positive over the next 13 weeks 34.5% of the time (noise twin 37.6%); if the earlier year was positive 38.3% (twin 48.3%); keep ratio -1.02 / -0.43. So even the best profile (all windows positive) carries a below-coin persistence on this evidence.

| family | rows (L3M>0) | L6M>0 | HOLD>0 | PRE>0 | X'>0 | L6M&HOLD>0 | + PRE>0 | all five >0 | L3M > MDE | decision |
|---|---|---|---|---|---|---|---|---|---|---|
| Z2 zones (ZONES-2 ledger rows) | 1,455 | 1,455 | 1,455 | 694 | 809 | 1,455 | 694 | 409 | 23 | shadow the 409 all-window rows as ONE bet (weekly Z2 cells: persistence = noise, section 4 of the monitor); no sizing |
| C2 KB 2-m HA / HM 15-s (confirm2) | 432 | 291 | 288 | 401 | 348 | 273 | 257 | 198 | 25 | HM 15-s: DROP (C2 addendum). KB 2-m HA: the L3M-positive file holds only 15/30/45-s HA cells (none 2-m); PE 45-s three-bar stays shadow (C2 LEAD); the 147 of 198 clean rows that are DEAD by placebo: no |
| 70% take / tighten (SD-A/SD-B/THPC/UF-PROFIT, N basis) | 4,071 | 252 | 282 | 172 | 106 | 234 | 129 | 37 | 20 | no: 20 rows beat MDE; worse than noise in the RE-1 series |
| sub-minute MA events (CF-SUBMIN) | 422 | 14 | 15 | 24 | 23 | 12 | 12 | 12 | 1 | no (14 of 422 positive in L6M; 0 candidates) |
| BARS-CAND / BARS-ALL / BARS-ENG L3M>0 rows | 9,017 | 2,765 | 2,432 | 1,149 | 1,643 | 2,347 | 809 | 423 | 35 | no (35 above MDE; PAIRFIX demotions; RE-1 H5 series equal to noise) |
| EINT2 day-type rules | 2,315 | 1,778 | 1,599 | 791 | 1,250 | 1,547 | 518 | 289 | 0 | shadow the stack7 lines positive in all windows (section 2B: 150 of 4,950, slightly above noise); none beats MDE in L3M |
| EINT1 (trend terciles, ledger rows) | 1,462 | 1,088 | 993 | 464 | 781 | 964 | 323 | 166 | 0 | see 2A: ER-5m sizer shadow |
| ensemble subsets (ENSM) | 39 | 19 | 17 | 1 | 12 | 15 | 1 | 0 | 0 | no (0 of 39 above MDE; 1 positive in PRE) |
| STACK-2 (ledger rows) | 20 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | see 2A |

## 3. New cycles aimed at the recent regime

### (a) Pure recent-fit chain (fit window = last 26 weeks only, choose the best cell of the family, test the next calendar month; decisions 2024-01..2026-01)

| family | cells | rule | mean $/wk | MDE | months + / - | random-cell mean | random 95th pct | rank vs random | L6M | cell fixed from the first 9 months |
|---|---|---|---|---|---|---|---|---|---|---|
| first-stop cut (A1-A3,D,E) | 59 | best of last 26w | 2,475 | 10,101 | 15 / 10 | -3,080 | 2,071 | 0.96 | 6,883 | 5,660 |
| first-stop cut (A1-A3,D,E) | 59 | best of last 26w, only if 13w also >0, half size | 396 | 4,203 | 11 / 10 | -1,460 | 1,063 | 0.89 | 1,318 | 5,660 |
| first-stop cut (A1-A3,D,E) | 59 | top-3 of last 26w avg | 1,528 | 8,199 | 12 / 13 | -3,000 | -240 | 0.99 | 7,493 | 5,660 |
| same-side cap (B) | 48 | best of last 26w | 1,749 | 5,874 | 13 / 11 | -7,453 | -545 | 0.98 | 724 | 603 |
| same-side cap (B) | 48 | best of last 26w, only if 13w also >0, half size | 617 | 2,680 | 12 / 9 | -3,747 | -435 | 0.99 | -1,130 | 603 |
| same-side cap (B) | 48 | top-3 of last 26w avg | 1,769 | 5,111 | 14 / 11 | -7,750 | -4,058 | 1.00 | 3,335 | 603 |
| first-target mirror (C) | 6 | best of last 26w | -15,155 | 11,813 | 5 / 20 | -17,567 | -14,678 | 0.90 | -3,133 | -21,310 |
| first-target mirror (C) | 6 | best of last 26w, only if 13w also >0, half size | 0 | 0 | 0 / 0 | -8,764 | -7,157 | 1.00 | 0 | -21,310 |
| first-target mirror (C) | 6 | top-3 of last 26w avg | -15,802 | 12,176 | 5 / 20 | -17,647 | -16,251 | 0.99 | -1,568 | -21,310 |
| trend ER sizer/gate | 10 | best of last 26w | -3,966 | 22,269 | 11 / 14 | -22,009 | -8,864 | 0.99 | 3,056 | -1,378 |
| trend ER sizer/gate | 10 | best of last 26w, only if 13w also >0, half size | -1,583 | 6,740 | 4 / 5 | -10,878 | -4,109 | 0.99 | -5,399 | -1,378 |
| trend ER sizer/gate | 10 | top-3 of last 26w avg | -6,018 | 19,198 | 11 / 14 | -21,573 | -14,686 | 1.00 | 4,193 | -1,378 |
| skip-after-loser / first-60 skips | 10 | best of last 26w | -3,149 | 14,255 | 9 / 16 | -13,957 | -4,927 | 0.97 | 4,560 | -17,254 |
| skip-after-loser / first-60 skips | 10 | best of last 26w, only if 13w also >0, half size | -935 | 3,788 | 4 / 7 | -6,946 | -2,514 | 0.99 | 0 | -17,254 |
| skip-after-loser / first-60 skips | 10 | top-3 of last 26w avg | -8,235 | 10,484 | 4 / 21 | -13,940 | -9,195 | 0.98 | -4,569 | -17,254 |
| book/session on-off-size | 30 | best of last 26w | 523 | 9,086 | 14 / 11 | -6,774 | -1,263 | 0.99 | -887 | 2,363 |
| book/session on-off-size | 30 | best of last 26w, only if 13w also >0, half size | 260 | 4,453 | 13 / 11 | -3,309 | -219 | 0.98 | -444 | 2,363 |
| book/session on-off-size | 30 | top-3 of last 26w avg | -4,369 | 6,630 | 8 / 17 | -6,483 | -2,945 | 0.83 | -2,823 | 2,363 |

Reading: the chain beats a random cell of the same family in every family (rank 0.83-1.00) because the average cell of these families loses money and the last-26-week winner is rarely the worst; in absolute terms only the first-stop cut and the same-side cap chains are positive (+2.5k and +1.7k, MDE ~10k), both inside noise. 'Fixed from the first 9 months' is the single cell best over 2023-04..2023-12 held through 2026: +5.7k/wk for the cut family, which is comparable to the chain and cheaper. Last re-fit (applies to February 2026): see `recentfit_last_refit.csv` - for the cut family the three best last-26-week cells are:

* fs|P=50|block=hour [S73]: 17,014 $/wk over the last 26 weeks, 43,522 over the last 13.
* fs|P=50|block=1800s [S73]: 16,348 $/wk over the last 26 weeks, 33,808 over the last 13.
* fs|P=50|stoppedSession!=london [S73]: 13,972 $/wk over the last 26 weeks, 17,341 over the last 13.

### (b) What is different about 2025-26 (what the user bets on when running a recent edge)

Per half-year block of signals (ENG6+ universe, 44k signals): trade-store features at the signal second, means. 5-minute realised vol (sig_rv_5m) is the stand-in for vol; prior-day and overnight range are in ATR(day) units; ES-NQ is the 20-minute correlation at the signal; |imbalance 10 levels| is the only book-depth-type measure in the stores (no top-5 depth column exists in the trend/flow stores: depth itself is a NAMED GAP; the imbalance magnitude has not changed).

| measure | 23H1 | 23H2 | 24H1 | 24H2 | 25H1 | 25H2 |
|---|---|---|---|---|---|---|
| signals_per_day | 41.338 | 42.378 | 61.076 | 69.383 | 71.600 | 81.582 |
| sig_rv_5m | 12.338 | 13.519 | 19.528 | 21.629 | 25.843 | 23.936 |
| on_range_atrd | 0.551 | 0.560 | 0.606 | 0.607 | 0.638 | 0.679 |
| prev_rng_atrd | 1.019 | 1.029 | 1.086 | 1.091 | 1.106 | 1.173 |
| sig_vol60 | 1111.557 | 1148.776 | 1046.067 | 936.449 | 843.274 | 944.775 |
| sig_intens_rel | 1.933 | 1.927 | 2.031 | 1.981 | 1.951 | 2.092 |
| er20_5m | 0.282 | 0.281 | 0.266 | 0.265 | 0.261 | 0.263 |
| sig_er300 | 0.104 | 0.101 | 0.099 | 0.097 | 0.098 | 0.098 |
| hurst100_5m | 0.585 | 0.582 | 0.579 | 0.576 | 0.572 | 0.580 |
| sig_esnq_corr20m | 0.857 | 0.869 | 0.896 | 0.909 | 0.932 | 0.931 |
| abs_imb10 | 0.111 | 0.133 | 0.129 | 0.115 | 0.115 | 0.110 |
| share_asia | 0.258 | 0.254 | 0.254 | 0.244 | 0.278 | 0.279 |
| share_london | 0.164 | 0.174 | 0.189 | 0.213 | 0.233 | 0.217 |
| share_pre | 0.058 | 0.068 | 0.069 | 0.057 | 0.050 | 0.049 |
| share_nyam | 0.309 | 0.277 | 0.282 | 0.281 | 0.254 | 0.279 |
| share_nypm | 0.206 | 0.224 | 0.203 | 0.200 | 0.183 | 0.173 |
| share_highvol_days | 0.346 | 0.377 | 0.374 | 0.400 | 0.336 | 0.473 |
| share_lowvol_days | 0.385 | 0.377 | 0.336 | 0.346 | 0.397 | 0.301 |

In words: the market since mid-2025 has about twice the 5-minute volatility, twice the signal frequency, a higher ES-NQ correlation (0.93 vs 0.86), larger overnight and prior-day ranges, a larger London share and a smaller NY-PM share, and more high-vol days (47% in 25H2 vs 35% in 23H1). It is not more trending per bar (ER and Hurst are flat to slightly lower). The edges that turned on in 2025-26 (first-stop cuts, skip-opening-hour, ER sizer) are therefore a bet on high-volatility, correlated, London-heavy conditions in which the first stop of a stacked entry is a better signal about the rest of the stack than it was in 2023. If volatility and correlation revert to 2023 levels, the 2023 half of the table (every one of these edges negative or flat in 2023H2-2025H1) is the guide.

### (c) Regime library: each edge scored in every 6-month regime of 2023-26

Share of the bank's rules positive in each regime, by family:

| family | rules | 23H1(Apr-Sep) | 23H2(Oct-Mar) | 24H1(Apr-Sep) | 24H2(Oct-Mar) | 25H1(Apr-Sep) | 25H2(Oct-Feb6) |
|---|---|---|---|---|---|---|---|
| book on/off | 36 | 0.50 | 0.33 | 0.36 | 0.19 | 0.11 | 0.25 |
| first-stop cut / cap (STACK-2) | 194 | 0.78 | 0.31 | 0.33 | 0.10 | 0.22 | 0.70 |
| session on/off | 24 | 0.38 | 0.12 | 0.25 | 0.33 | 0.25 | 0.50 |
| skip-after-loser (N1b) | 6 | 0.00 | 0.00 | 0.50 | 0.00 | 0.00 | 0.50 |
| skip-first-60-min (N1c) | 14 | 1.00 | 0.07 | 0.00 | 0.21 | 0.00 | 0.43 |
| trend terciles / ER sizer | 20 | 0.80 | 0.00 | 0.50 | 0.00 | 0.20 | 0.30 |

Library entries for the main edges (mean $/wk by regime; the 'worked in' column lists regimes with mean > 0 and t > 1):

| edge | 23H1(Apr-Sep) | 23H2(Oct-Mar) | 24H1(Apr-Sep) | 24H2(Oct-Mar) | 25H1(Apr-Sep) | 25H2(Oct-Feb6) | worked in |
|---|---|---|---|---|---|---|---|
| fs|P=50|stopdef=0 [S73] | 10,646 | -10,590 | -2,526 | -12,008 | -12,944 | 20,212 | 23H1(Apr-Sep), 25H2(Oct-Feb6) |
| fs|P=50|stoppedSession=asia [S73] | 6,456 | 130 | 2,877 | 265 | -429 | 20,758 | 23H1(Apr-Sep), 25H2(Oct-Feb6) |
| fs|P=50|oppBooks>=1 [S73] | 7,035 | 3,108 | 3,120 | -3,546 | 4,627 | 8,592 | 23H1(Apr-Sep), 25H2(Oct-Feb6) |
| ER sizer x1.5 above .4 / x0.5 below .3 [S73] | 6,443 | -8,418 | 11,016 | -31,506 | 9,145 | 6,146 | none with t>1 |
| skip first 60 min of every session [S73] | 26,649 | -21,651 | -501 | -45,043 | -20,016 | 11,041 | 23H1(Apr-Sep) |
| skip 2nd same-dir signal in same book within 30 min after a LOSER [S73] | -10,927 | -6,188 | 4,447 | -7,833 | -7,979 | 2,765 | none with t>1 |
| cap|live=8|x2.35|mode=skip|session=pre|count=both100 [S73] | 1,959 | 483 | 9,735 | -2,895 | 4,823 | 2,911 | 24H1(Apr-Sep), 25H1(Apr-Sep) |
| book SM x1.5 [S73] | 1,508 | 3,093 | 4,062 | 1,854 | -319 | 6,597 | 23H2(Oct-Mar), 25H2(Oct-Feb6) |

Does the library predict persistence? Rules positive in regime j, and positive in ALL earlier regimes, vs the next regime:

| regime j | rules positive in j | P(next regime positive) | if positive in all earlier regimes | n | base rate of next regime positive |
|---|---|---|---|---|---|
| 23H2(Oct-Mar) | 77 | 0.60 | 0.67 | 55 | 0.33 |
| 24H1(Apr-Sep) | 96 | 0.12 | 0.22 | 37 | 0.13 |
| 24H2(Oct-Mar) | 37 | 0.35 | 0.25 | 8 | 0.19 |
| 25H1(Apr-Sep) | 57 | 0.86 | 1.00 | 2 | 0.59 |

Reading: adjacent half-years carry persistence above the base rate in 3 of 4 transitions (0.60 vs 0.33, 0.35 vs 0.19, 0.86 vs 0.59; equal in 2024H1 to 2024H2); requiring the rule to have been positive in every earlier regime adds little (0.67 vs 0.60, 0.22 vs 0.13, 0.25 vs 0.35, n = 2 for the last), and the bank rules are strongly clustered, so the effective n is about the 120 clusters, not 294. Each edge's regime list is `regime_library.csv`.

## 4. Disclosures and limits

* **Bank vs ledger.** The walk-forward and the monitor cover only rules whose monthly/weekly series could be rebuilt (STACK-2 cells and the 52 new row-multiplier families on S73 and MKT bases, 294 unique series). They are the recent-edge candidates of the stack-level programs; they are not the whole ledger. Where RE-1's stored series exist (section 2B) they are used for persistence/status only, not for the portfolio (their units are per-trade pts, not stack $).
* **Selection.** The ledger at month M is every ON rule of the bank (no selection by outcome); the persistence score is walk-forward; the shrinkage is measured on earlier months. Section 1 / 2A reads the end-of-sample windows (L3M, L6M) that every program has already looked at: those columns are descriptive. The JOINT lock-engine run of today's ledger is in-sample for L3M/L6M by construction.
* **Persistence score.** Local first pass (walk-forward logistic with noise adjustment). RE-1's interim model has AUC 0.508 and Brier skill -0.011 (CI -0.049..+0.014): no usable persistence classifier either. I will replace the score by RE-1's when DS3_PERSISTENCE.md is final; given both are at chance the walk-forward conclusions will not change.
* **Linearity.** Sizing an edge at fraction f scales its own parameters; the engine's governors make the effect nonlinear and each f is run through the engine. The additive 'equal-weight sleeve' rows are not engine runs.
* **Z2 weekly cells** (5,271 unique) carry zones2's stored weekly sums (per-trade dollars, not lock-engine stack); persistence = noise (P 0.49 vs 0.47). **Depth**: no top-5 book depth in the stores: named gap. **ES correlation**: the sig_esnq_corr20m feature is available to 2026-02-06 (the ES 1-s tape built by N1 ends 2026-01-31 and was not used).
* **Ledger hook.** RE-1's STOPPED hook was not on disk at write time; statuses are in `out/recentedge2/STATUS_FOR_LEDGER.csv` (key `rule`) and the monitor appends to EDGE_STATUS_LOG.md. UF_TRIALS side `followup_re2`: 104 new engine runs, 202 stored cells re-read, 5,271 Z2 weekly series, 18,456 RE-1 ON rows read (no new strategy selection).

## 5. Files

`autopilot/DS3_EDGE_MONITOR.md`, `autopilot/DS3_RECENT_PORTFOLIO.md`, `autopilot/EDGE_STATUS_LOG.md`; code `l2vast/ds3/code/recentedge2/` (re2_bank, re2_lib, re2_ledger, re2_persist, re2_monitor, re2_monitor_report, re2_mkmonitor, re2_portfolio, re2_portfolio_eval, re2_portfolio_latest, re2_mkportfolio, re2_reexam, re2_hfam, re2_cycles, re2_regime_desc, re2_extra, re2_extra_analysis, re2_mkfinal); outputs `l2vast/ds3/out/recentedge2/` (bank.npz, bank_meta.csv, monitor_*.csv, STATUS_FOR_LEDGER.csv, portfolio_*, latest_*, reexam_*, hfam_*, recentfit_*, regime_*).