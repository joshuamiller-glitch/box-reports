# DS3_PERSISTENCE  (T-RECENT-EDGE section 2: do recent edges persist?)  compiled 2026-10-31 04:44Z

Research only. Own masks capped 2026-02-06 (months 2023-04 .. 2026-01; the 5 days of 2026-02 are not used); UNTOUCHED never read; no re-run of any program (monthly series re-read from stored per-trade / per-day outputs). Selection at month M uses only months before M (rolling windows ending at M-1); the outcome window is the 3 months M, M+1, M+2, strictly after; M runs 2023-10 .. 2025-11 (26 months; 2025-11 is the last month whose 3-month after-window, Nov-Jan, is readable). Walk-forward model: trained only on (rule, month) pairs whose after-window had finished before M.

## 1. The answer first (page 1)

**Headline.** Across all 450,016 (rule, scope) series in the frame, a rule that was positive in the last 3 and 6 months was positive over the next 3 months 41% of the time (CI 36%-47%); sign-flip noise with the same fire pattern: 50%; same-mean no-structure baseline: 44%. So in this universe a recent edge is **not** more likely than a coin to stay positive, and it is NOT more persistent than a rule whose months are exchangeable; the typical selected rule has a negative long-run mean (most rules scored here lose to the floor they were built on), and selecting on the last 3 and 6 months does not repair that. The exception is magnitude: rules whose 6-month t-statistic was at least 3 stayed positive 70% (t 3-4) and 83% (t >= 4) of the time, +15 and +27 points over the same-mean baseline, but those are few distinct rules (see section 3).

**Plain sentences by family** (each is "positive in the last 3 and 6 months" -> "next 3 months"; per exposure = per planned-lot base trade, or per day for the two stack-level families):

- A **confirmation** rule that was positive in the last 3 AND the last 6 months stayed positive in the next 3 months **32%** of the time (month-block 95% CI 26%-41%, 74,001 rule-months); a zero-edge noise rule with the same fire pattern does 50%, and a rule with the same long-run mean but no month-to-month structure does 34%, so the real persistence lift is -18 points over sign-flip noise (CI -24..-9) and -2 points over the same-mean no-structure baseline (CI -8..+6). It kept **-69%** of its last-3-month magnitude per exposure in the next 3 months (CI -88%..-41%; per final contract -113%).
- A **sizing** rule that was positive in the last 3 AND the last 6 months stayed positive in the next 3 months **51%** of the time (month-block 95% CI 49%-52%, 26,099 rule-months); a zero-edge noise rule with the same fire pattern does 50%, and a rule with the same long-run mean but no month-to-month structure does 51%, so the real persistence lift is +0 points over sign-flip noise (CI -2..+2) and -0 points over the same-mean no-structure baseline (CI -2..+2). It kept **4%** of its last-3-month magnitude per exposure in the next 3 months (CI -3%..9%; per final contract 3%).
- An **exit** rule that was positive in the last 3 AND the last 6 months stayed positive in the next 3 months **45%** of the time (month-block 95% CI 35%-55%, 100,934 rule-months); a zero-edge noise rule with the same fire pattern does 50%, and a rule with the same long-run mean but no month-to-month structure does 51%, so the real persistence lift is -5 points over sign-flip noise (CI -15..+5) and -6 points over the same-mean no-structure baseline (CI -16..+4). It kept **-23%** of its last-3-month magnitude per exposure in the next 3 months (CI -60%..11%; per final contract -26%).
- An **entry-filter** rule that was positive in the last 3 AND the last 6 months stayed positive in the next 3 months **50%** of the time (month-block 95% CI 48%-51%, 15,870 rule-months); a zero-edge noise rule with the same fire pattern does 50%, and a rule with the same long-run mean but no month-to-month structure does 50%, so the real persistence lift is +0 points over sign-flip noise (CI -2..+2) and +1 points over the same-mean no-structure baseline (CI -1..+2). It kept **-0%** of its last-3-month magnitude per exposure in the next 3 months (CI -6%..5%; per final contract -0%).
- An **entry-structure** rule that was positive in the last 3 AND the last 6 months stayed positive in the next 3 months **38%** of the time (month-block 95% CI 32%-46%, 83,787 rule-months); a zero-edge noise rule with the same fire pattern does 50%, and a rule with the same long-run mean but no month-to-month structure does 41%, so the real persistence lift is -12 points over sign-flip noise (CI -19..-4) and -3 points over the same-mean no-structure baseline (CI -9..+5). It kept **-45%** of its last-3-month magnitude per exposure in the next 3 months (CI -63%..-16%; per final contract -49%).
- A **stack-level** rule that was positive in the last 3 AND the last 6 months stayed positive in the next 3 months **17%** of the time (month-block 95% CI 6%-41%, 5,680 rule-months); a zero-edge noise rule with the same fire pattern does 50%, and a rule with the same long-run mean but no month-to-month structure does 27%, so the real persistence lift is -32 points over sign-flip noise (CI -43..-8) and -10 points over the same-mean no-structure baseline (CI -21..+14). It kept **-136%** of its last-3-month magnitude per exposure in the next 3 months (CI -270%..-40%; per final contract -136%).
- A **regime / day-type** rule that was positive in the last 3 AND the last 6 months stayed positive in the next 3 months **52%** of the time (month-block 95% CI 40%-59%, 33,498 rule-months); a zero-edge noise rule with the same fire pattern does 50%, and a rule with the same long-run mean but no month-to-month structure does 47%, so the real persistence lift is +2 points over sign-flip noise (CI -10..+10) and +5 points over the same-mean no-structure baseline (CI -7..+12). It kept **-27%** of its last-3-month magnitude per exposure in the next 3 months (CI -52%..-5%; per final contract -27%).

**Best predictor of persistence.** The walk-forward ablation (section 6) ranks the 6-month t-statistic (the size of the edge relative to its own noise, i.e. magnitude/MDE) first: family-only Brier 0.2466, +t-stat 0.2445 (skill +0.9% vs family-only, CI -0.1..+1.6); streak length, PRE sign, fire rate and stack correlation add nothing out of sample (their skill is zero or negative). The model beats the base rate by +1.6% in Brier terms, i.e. barely: **the best available forecast of persistence is the family base rate plus a little credit for a large t-statistic.**

**Null result stated plainly:** there is no evidence in this data that "positive in L3M and L6M" by itself raises the probability of a positive next quarter above what chance and the rule's own long-run mean already imply. The page of recent wins is a view of what happened, not a forecast; its forecast value is the shrunk expectation in section 5, which for most families is zero or negative.

## 2. Sampling frame, coverage and method

* Harvested monthly series (rule x scope: pooled + 10 books for per-trade sources; pooled for per-day sources) from stored outputs, no re-run: exit/profit rules 23,773 (l2set_profit D_real), exit/loss rules 2,380 (uf loss1 D2/D3/D5/D6/D6q/D_main/D_extra/C4), confirmation CF-ENG 560 (confirm/eng/s1, N basis minus the plain 70/30 dip floor) and confirm2 G1-G5 about 9,950, entry structure: bars_eng 7,165 trade files and L2SE/dipentry grids 4,251, EINT1 389 rules (entry filter + sizing), split2 63 policies (sizing, lock-engine stack $/day), L2SJ joint policy stack lines 72, THP walk-forward policy chains 1,880 and EINT2 day-type rules 4,950 (regime; 550 rules x stack + 8 D6 cell lines). A (rule, scope) series enters the frame if it fired >= 30 times in total.
* **Frame size 450,016 (rule, scope) series**; DEAD_CELLS.csv lists 143,584 stored cell rows (673,671 cell x scope, 81,198 distinct specs) and the directive quotes ~2.5 million cells; so the recoverable fraction is **18% of the 2.5M figure and 67% of the 673,671 cell x scope count** (distinct rules before the scope split: 54,558). The rest of the catalogue is stored only as window aggregates (2026 / L6M / HOLD / PRE / X') - EINT1/EINT2 maps, ZONES-2, NEWIDEAS, TRENDGATE tables, L2EA/L2EB - and has no monthly series that can be recovered without a re-run; those programs are therefore NOT in the persistence study (a limit, stated).
* **Sample 50,000** stratified by family, equal allocation capped at availability, remainder redistributed: entry filter 1,628 of 1,628, entry structure 12,929 of 46,418, confirmation 12,928 of 112,508, exit 12,928 of 279,875, sizing 2,685 of 2,685, stack 1,762 of 1,762, regime 5,140 of 5,140. Entry filter, sizing, stack and regime are small families (all of the frame is used); exit, confirmation and entry structure are sub-sampled. All headline numbers are on the sample; family numbers are exact for the sampled series.
* Rule value per month: sum of the stored per-trade delta (pts per planned lot, vs the program comparator: hold-to-bracket for exits, the plain 70/30 3-pt-dip floor for entry/confirmation cells, base lots for sizing/filters) or the per-day lock-engine stack $ delta. "Positive" = the sum over the window > 0. A rule is SELECTED at M if sum(M-3..M-1) > 0, sum(M-6..M-1) > 0 and it fired >= 10 times in M-6..M-1. Outcome: sum(M..M+2) > 0.
* **Noise-rule baselines (guard 2).** N0 = same fire pattern and per-month variance with shuffled signs: month sums redrawn as Normal(0, sum of squared trade values) (3 replicates per rule). N1 = the rule's own months permuted at random among its valid months (3 replicates): same marginal monthly distribution and same long-run mean, serial structure destroyed. P(positive next | positive last) is about 50% minus a little for N0 and below 50% for N1 whenever the typical rule has a negative mean; the lift over those baselines, not the raw percentage, is the persistence.
* Placebo-beaten flag at M: the rule's trailing 6-month t-statistic exceeds the 95th percentile of the N0 t-statistics of all rules in its family at that M. Streak = consecutive positive months ending M-1. PRE sign = sign of the rule's total over all months before M-6 (known from M = 2024-01 on; "unknown" before). Stack correlation = correlation of the rule's monthly per-exposure series (months before M, >= 8 months) with its family mean series.
* Bootstrap: month blocks of 3 (moving), 1000 draws, resampling selection months; all CIs 95%. Rule-months within a month are strongly dependent (same trades), so CIs are driven by the 26 months, not by the 340,000 selections.

## 3. (a) Persistence curve

### 3.1 Overall and per family (selected = positive in last 3 AND 6 months; outcome = positive over next 3 months)

| family | rule-months selected | P(positive next 3m) [95% CI] | noise N0 | same-mean N1 | lift vs N0 [CI] | lift vs N1 [CI] |
|---|---|---|---|---|---|---|
| ALL (sample, family-balanced) | 339,869 | 41% [36%-47%] | 50% | 44% | -8.5 [-13.6,-3.1] | -3.0 [-8.1,+2.4] |
| entry filter | 15,870 | 50% [48%-51%] | 50% | 50% | +0.2 [-2.0,+1.7] | +0.6 [-1.0,+1.6] |
| entry structure | 83,787 | 38% [32%-46%] | 50% | 41% | -12.0 [-18.5,-4.2] | -2.7 [-9.0,+4.9] |
| confirmation | 74,001 | 32% [26%-41%] | 50% | 34% | -17.6 [-24.0,-9.1] | -1.8 [-8.3,+6.5] |
| exit | 100,934 | 45% [35%-55%] | 50% | 51% | -4.5 [-14.8,+5.3] | -5.7 [-15.9,+4.0] |
| sizing | 26,099 | 51% [49%-52%] | 50% | 51% | +0.4 [-1.9,+2.2] | -0.0 [-2.1,+1.6] |
| stack | 5,680 | 17% [6%-41%] | 50% | 27% | -32.1 [-43.5,-8.1] | -9.7 [-20.7,+13.8] |
| regime | 33,498 | 52% [40%-59%] | 50% | 47% | +1.8 [-10.2,+9.5] | +4.9 [-7.4,+12.4] |

### 3.2 By selection month (overall; real vs N0 vs N1; the month-to-month swing is the regime factor shared by all rules)

| M | real P | N0 | N1 | n real |
|---|---|---|---|---|
| 2023-10 | 0.41 | 0.50 | 0.45 | 18,972 |
| 2023-11 | 0.31 | 0.50 | 0.45 | 21,086 |
| 2023-12 | 0.33 | 0.50 | 0.45 | 17,138 |
| 2024-01 | 0.36 | 0.50 | 0.44 | 13,081 |
| 2024-02 | 0.38 | 0.50 | 0.45 | 10,539 |
| 2024-03 | 0.49 | 0.50 | 0.44 | 11,501 |
| 2024-04 | 0.56 | 0.50 | 0.45 | 11,318 |
| 2024-05 | 0.38 | 0.50 | 0.43 | 12,792 |
| 2024-06 | 0.25 | 0.50 | 0.44 | 14,848 |
| 2024-07 | 0.27 | 0.50 | 0.44 | 16,471 |
| 2024-08 | 0.35 | 0.50 | 0.44 | 11,010 |
| 2024-09 | 0.40 | 0.50 | 0.44 | 9,310 |
| 2024-10 | 0.39 | 0.50 | 0.44 | 9,376 |
| 2024-11 | 0.43 | 0.50 | 0.45 | 8,886 |
| 2024-12 | 0.54 | 0.50 | 0.44 | 7,760 |
| 2025-01 | 0.43 | 0.50 | 0.45 | 6,435 |
| 2025-02 | 0.55 | 0.50 | 0.44 | 7,095 |
| 2025-03 | 0.47 | 0.50 | 0.44 | 10,415 |
| 2025-04 | 0.62 | 0.50 | 0.45 | 9,968 |
| 2025-05 | 0.57 | 0.50 | 0.45 | 15,031 |
| 2025-06 | 0.57 | 0.50 | 0.45 | 15,207 |
| 2025-07 | 0.38 | 0.50 | 0.44 | 21,728 |
| 2025-08 | 0.33 | 0.50 | 0.44 | 20,766 |
| 2025-09 | 0.39 | 0.50 | 0.45 | 16,652 |
| 2025-10 | 0.47 | 0.50 | 0.45 | 12,605 |
| 2025-11 | 0.58 | 0.50 | 0.45 | 9,879 |

### 3.3 Strata (pooled across families; then the families with >= 200 selections)

| stratum | n | P [CI] | N0 | N1 | lift vs N1 |
|---|---|---|---|---|---|
| magnitude z6 1-2 | 314,324 | 40% [35%-46%] | 50% | 44% | -3.8 |
| magnitude z6 2-3 | 17,554 | 48% [31%-59%] | 50% | 51% | -3.0 |
| magnitude z6 3-4 | 2,616 | 70% [49%-77%] | 50% | 55% | +14.9 |
| magnitude z6 >=4 | 5,375 | 83% [37%-97%] | 49% | 56% | +27.1 |
| fire rate <5% | 10,566 | 39% [33%-45%] | 50% | 44% | -4.8 |
| fire rate 5-20% | 23,956 | 40% [35%-48%] | 50% | 44% | -3.9 |
| fire rate 20-60% | 83,010 | 44% [34%-56%] | 50% | 49% | -4.8 |
| fire rate >=60% | 222,337 | 41% [37%-44%] | 50% | 42% | -1.8 |
| PRE(history) positive | 120,976 | 47% [38%-54%] | 50% | 49% | -2.4 |
| PRE(history) negative | 158,887 | 40% [35%-47%] | 50% | 42% | -1.1 |
| PRE unknown (M<2024-01) | 60,006 | 34% [6%-40%] | 50% | 44% | -9.8 |
| placebo beaten (z6>noise p95) | 43,539 | 51% [38%-59%] | 50% | 50% | +1.0 |
| placebo not beaten | 296,330 | 40% [35%-46%] | 50% | 44% | -3.6 |
| streak 1-2 | 243,301 | 41% [36%-46%] | 50% | 44% | -3.4 |
| streak 3-5 | 80,482 | 40% [35%-47%] | 50% | 45% | -4.3 |
| streak 6-11 | 15,974 | 58% [42%-64%] | 50% | 48% | +9.6 |
| streak >=12 | 112 | 66% [56%-75%] | 52% | 63% | +2.6 |
| corr w/ family mean <0.2 | 121,119 | 43% [40%-46%] | 50% | 44% | -1.1 |
| corr 0.2-0.6 | 140,382 | 42% [34%-51%] | 50% | 44% | -1.5 |
| corr >=0.6 | 21,172 | 42% [28%-55%] | 50% | 43% | -0.7 |

*exit*

| stratum | n | P [CI] | N1 | lift vs N1 |
|---|---|---|---|---|
| magnitude z6 1-2 | 91,483 | 43% [34%-54%] | 50% | -7.3 |
| magnitude z6 2-3 | 5,503 | 53% [38%-66%] | 59% | -5.3 |
| magnitude z6 3-4 | 1,834 | 80% [46%-89%] | 63% | +17.3 |
| magnitude z6 >=4 | 2,114 | 96% [43%-98%] | 59% | +36.6 |
| fire rate <5% | 8,567 | 41% [35%-46%] | 46% | -5.2 |
| fire rate 5-20% | 17,657 | 43% [37%-51%] | 47% | -3.3 |
| fire rate 20-60% | 54,999 | 50% [36%-62%] | 54% | -4.0 |
| fire rate >=60% | 19,711 | 35% [23%-48%] | 48% | -12.7 |
| PRE(history) positive | 44,396 | 50% [38%-61%] | 55% | -5.5 |
| PRE(history) negative | 35,727 | 46% [32%-56%] | 46% | -0.5 |
| PRE unknown (M<2024-01) | 20,811 | 35% [23%-61%] | 51% | -16.5 |
| placebo beaten (z6>noise p95) | 14,903 | 62% [40%-72%] | 58% | +4.0 |
| placebo not beaten | 86,031 | 42% [33%-53%] | 50% | -7.4 |
| streak 1-2 | 70,374 | 45% [35%-56%] | 51% | -5.2 |
| streak 3-5 | 24,831 | 40% [30%-53%] | 51% | -11.0 |
| streak 6-11 | 5,709 | 64% [31%-84%] | 55% | +9.3 |
| corr w/ family mean <0.2 | 16,381 | 40% [33%-48%] | 51% | -10.6 |
| corr 0.2-0.6 | 54,292 | 50% [37%-61%] | 51% | -1.3 |
| corr >=0.6 | 10,266 | 51% [28%-64%] | 51% | +0.9 |

*confirmation*

| stratum | n | P [CI] | N1 | lift vs N1 |
|---|---|---|---|---|
| magnitude z6 1-2 | 72,209 | 32% [26%-41%] | 34% | -1.8 |
| magnitude z6 2-3 | 1,733 | 31% [21%-39%] | 34% | -2.9 |
| fire rate <5% | 1,265 | 23% [8%-47%] | 22% | +1.1 |
| fire rate 5-20% | 3,578 | 22% [12%-38%] | 22% | -0.2 |
| fire rate 20-60% | 12,582 | 27% [21%-36%] | 31% | -4.2 |
| fire rate >=60% | 56,576 | 35% [28%-43%] | 36% | -1.7 |
| PRE(history) positive | 21,733 | 36% [27%-45%] | 34% | +1.4 |
| PRE(history) negative | 36,349 | 32% [25%-41%] | 34% | -2.0 |
| PRE unknown (M<2024-01) | 15,919 | 28% [0%-50%] | 35% | -6.5 |
| placebo beaten (z6>noise p95) | 4,914 | 32% [23%-41%] | 34% | -1.7 |
| placebo not beaten | 69,087 | 32% [26%-41%] | 34% | -1.9 |
| streak 1-2 | 55,158 | 33% [27%-40%] | 34% | -1.6 |
| streak 3-5 | 17,084 | 31% [24%-42%] | 34% | -2.3 |
| streak 6-11 | 1,756 | 30% [22%-37%] | 35% | -5.1 |
| corr w/ family mean <0.2 | 28,074 | 39% [33%-46%] | 34% | +5.3 |
| corr 0.2-0.6 | 26,061 | 29% [21%-40%] | 34% | -5.6 |
| corr >=0.6 | 4,012 | 23% [12%-41%] | 34% | -11.2 |

*entry structure*

| stratum | n | P [CI] | N1 | lift vs N1 |
|---|---|---|---|---|
| magnitude z6 1-2 | 79,191 | 37% [31%-46%] | 41% | -3.1 |
| magnitude z6 2-3 | 4,206 | 47% [34%-55%] | 43% | +4.3 |
| magnitude z6 3-4 | 374 | 36% [25%-48%] | 38% | -1.2 |
| fire rate <5% | 733 | 45% [28%-64%] | 50% | -5.3 |
| fire rate 5-20% | 2,647 | 41% [26%-60%] | 50% | -8.7 |
| fire rate 20-60% | 15,097 | 39% [26%-56%] | 44% | -5.8 |
| fire rate >=60% | 65,310 | 38% [33%-43%] | 39% | -1.7 |
| PRE(history) positive | 22,141 | 45% [33%-54%] | 44% | +0.6 |
| PRE(history) negative | 49,644 | 39% [31%-46%] | 39% | -0.4 |
| PRE unknown (M<2024-01) | 12,002 | 23% [22%-86%] | 40% | -17.9 |
| placebo beaten (z6>noise p95) | 9,162 | 42% [33%-50%] | 43% | -0.0 |
| placebo not beaten | 74,625 | 37% [31%-46%] | 40% | -3.1 |
| streak 1-2 | 60,134 | 37% [31%-45%] | 41% | -3.7 |
| streak 3-5 | 20,661 | 39% [32%-49%] | 41% | -1.3 |
| streak 6-11 | 2,986 | 49% [40%-57%] | 42% | +6.7 |
| corr w/ family mean <0.2 | 31,786 | 39% [35%-43%] | 41% | -1.6 |
| corr 0.2-0.6 | 34,959 | 42% [31%-50%] | 40% | +1.5 |
| corr >=0.6 | 5,085 | 40% [22%-59%] | 40% | -0.7 |

*sizing*

| stratum | n | P [CI] | N1 | lift vs N1 |
|---|---|---|---|---|
| magnitude z6 1-2 | 24,195 | 51% [49%-52%] | 51% | +0.0 |
| magnitude z6 2-3 | 1,580 | 51% [45%-57%] | 53% | -1.3 |
| magnitude z6 3-4 | 226 | 62% [54%-69%] | 58% | +4.3 |
| fire rate 20-60% | 316 | 79% [72%-85%] | 80% | -0.7 |
| fire rate >=60% | 25,710 | 50% [48%-52%] | 50% | +0.0 |
| PRE(history) positive | 11,807 | 51% [48%-53%] | 51% | -0.3 |
| PRE(history) negative | 11,314 | 51% [48%-53%] | 51% | +0.7 |
| PRE unknown (M<2024-01) | 2,978 | 49% [0%-49%] | 51% | -1.8 |
| placebo beaten (z6>noise p95) | 3,571 | 53% [47%-57%] | 53% | +0.1 |
| placebo not beaten | 22,528 | 50% [49%-52%] | 51% | -0.0 |
| streak 1-2 | 18,599 | 51% [49%-52%] | 51% | +0.2 |
| streak 3-5 | 6,479 | 50% [46%-53%] | 51% | -0.9 |
| streak 6-11 | 986 | 52% [45%-57%] | 50% | +2.8 |
| corr w/ family mean <0.2 | 19,321 | 51% [49%-53%] | 51% | +0.3 |
| corr 0.2-0.6 | 3,602 | 50% [46%-53%] | 50% | -0.2 |

*entry filter*

| stratum | n | P [CI] | N1 | lift vs N1 |
|---|---|---|---|---|
| magnitude z6 1-2 | 14,757 | 50% [48%-51%] | 49% | +0.8 |
| magnitude z6 2-3 | 971 | 46% [41%-51%] | 51% | -5.0 |
| fire rate >=60% | 15,870 | 50% [48%-51%] | 50% | +0.6 |
| PRE(history) positive | 6,583 | 50% [48%-52%] | 50% | +0.2 |
| PRE(history) negative | 7,554 | 50% [47%-52%] | 49% | +0.8 |
| PRE unknown (M<2024-01) | 1,733 | 51% [0%-52%] | 50% | +0.9 |
| placebo beaten (z6>noise p95) | 2,195 | 49% [45%-53%] | 49% | +0.0 |
| placebo not beaten | 13,675 | 50% [48%-51%] | 50% | +0.6 |
| streak 1-2 | 11,292 | 50% [48%-51%] | 49% | +0.8 |
| streak 3-5 | 3,958 | 50% [48%-51%] | 49% | +0.3 |
| streak 6-11 | 617 | 52% [45%-57%] | 54% | -2.1 |
| corr w/ family mean <0.2 | 8,900 | 50% [48%-52%] | 50% | +0.7 |
| corr 0.2-0.6 | 4,865 | 49% [46%-51%] | 49% | +0.1 |
| corr >=0.6 | 372 | 56% [49%-61%] | 50% | +6.6 |

Reading: the high-t-statistic strata (>= 3) are where the lift is, mostly exit rules whose gain is structural (take-at-fraction / target-fill style rules; their persistence is a property of the exit geometry, not of the recent market). Fire rate, streak below 6, PRE sign and stack correlation separate nothing once the family is fixed.

## 4. (b) Decay of the selected edge from month +1 to +6, and half-life

R_k = (mean per exposure of the selected rules in month M+k-1) / (their mean per month in the selection window M-3..M-1), ratio of means within source group, selection-weighted; M <= 2025-08 so that all six months are readable (23 selection months). R = 1 would be "no decay"; R < 0 means the edge reversed. Half-life = ln(0.5)/ln(lambda) from R_k = a*lambda^(k-1) fitted on positive R_k (months); undefined when R is not positive.

| family | kind | n | R1 | R2 | R3 | R4 | R5 | R6 | half-life (months) [CI] |
|---|---|---|---|---|---|---|---|---|---|
| ALL | real | 300,733 | -0.34 | -0.44 | -0.41 | -0.28 | -0.22 | -0.28 | n/a (R<=0: nothing left to decay) |
| confirmation | real | 67,988 | -0.64 | -0.74 | -0.64 | -0.50 | -0.57 | -0.60 | n/a (R<=0: nothing left to decay) |
| entry filter | real | 14,241 | -0.01 | -0.05 | +0.00 | +0.02 | +0.07 | +0.05 | n/a (R<=0: nothing left to decay) |
| entry structure | real | 73,582 | -0.37 | -0.47 | -0.49 | -0.40 | -0.31 | -0.32 | n/a (R<=0: nothing left to decay) |
| exit | real | 88,134 | -0.22 | -0.35 | -0.33 | -0.11 | +0.00 | -0.08 | n/a (R<=0: nothing left to decay) |
| regime | real | 28,419 | -0.24 | -0.30 | -0.25 | -0.30 | -0.31 | -0.35 | n/a (R<=0: nothing left to decay) |
| sizing | real | 23,273 | +0.00 | +0.01 | +0.02 | +0.07 | +0.10 | +0.08 | no decay fitted (R rises) |
| stack | real | 5,096 | -0.80 | -1.64 | -1.78 | -0.95 | -0.16 | -0.87 | n/a (R<=0: nothing left to decay) |
| ALL | N1 | 911,341 | -0.22 | -0.22 | -0.22 | -0.22 | -0.23 | -0.23 | n/a (R<=0: nothing left to decay) |
| confirmation | N1 | 175,281 | -0.53 | -0.53 | -0.53 | -0.53 | -0.54 | -0.53 | n/a (R<=0: nothing left to decay) |
| entry filter | N1 | 41,225 | -0.03 | -0.02 | -0.02 | -0.02 | -0.02 | -0.03 | n/a (R<=0: nothing left to decay) |
| entry structure | N1 | 219,850 | -0.33 | -0.33 | -0.33 | -0.33 | -0.34 | -0.34 | n/a (R<=0: nothing left to decay) |
| exit | N1 | 303,478 | -0.03 | -0.03 | -0.03 | -0.03 | -0.03 | -0.03 | n/a (R<=0: nothing left to decay) |
| regime | N1 | 87,910 | -0.25 | -0.23 | -0.23 | -0.23 | -0.23 | -0.22 | n/a (R<=0: nothing left to decay) |
| sizing | N1 | 69,776 | +0.03 | +0.03 | +0.04 | +0.04 | +0.04 | +0.03 | no decay fitted (R rises) |
| stack | N1 | 13,821 | -0.80 | -0.80 | -0.77 | -0.80 | -0.83 | -0.83 | n/a (R<=0: nothing left to decay) |

Reading: for every family except sizing and entry filter the selected edge is already negative in month +1 on average (the typical selected rule reverts to its long-run negative mean), so there is no half-life to report - the "edge" has a half-life of less than one month. Sizing and entry-filter rules are flat at about zero (they are small perturbations of the base trades), so their ratio is ~0 rather than decaying.

## 5. (c) Shrinkage factor = out-of-sample / in-sample magnitude

Ratio of the per-exposure mean over the next 3 months to the per-exposure mean over the selection 3 months, within source group (units are not mixed), selection-weighted. In-sample = the last 3 months at selection (and the last 6 in the second column).

| family / stratum | kind | n | OOS/IS (vs L3M) [CI] | OOS/IS (vs L6M) | per final contract |
|---|---|---|---|---|---|
| ALL | real | 339,869 | -0.38 [-0.53,-0.18] | -0.57 | -0.49 |
| confirmation | real | 74,001 | -0.69 [-0.88,-0.41] | -1.05 | -1.13 |
| entry filter | real | 15,870 | -0.00 [-0.06,+0.05] | -0.00 | -0.00 |
| entry structure | real | 83,787 | -0.45 [-0.63,-0.16] | -0.70 | -0.49 |
| exit | real | 100,934 | -0.23 [-0.60,+0.11] | -0.32 | -0.26 |
| regime | real | 33,498 | -0.27 [-0.52,-0.05] | -0.41 | -0.27 |
| sizing | real | 26,099 | +0.04 [-0.03,+0.09] | +0.06 | +0.03 |
| stack | real | 5,680 | -1.36 [-2.70,-0.40] | -2.14 | -1.36 |
| ALL | N1 | 1,030,386 | -0.23 [-0.23,-0.22] | -0.36 | -0.29 |
| confirmation | N1 | 198,101 | -0.56 [-0.57,-0.55] | -0.92 | -0.93 |
| entry filter | N1 | 46,510 | -0.01 [-0.02,+0.00] | -0.01 | -0.01 |
| entry structure | N1 | 248,603 | -0.32 [-0.33,-0.32] | -0.50 | -0.24 |
| exit | N1 | 343,151 | -0.03 [-0.03,-0.02] | -0.04 | -0.07 |
| regime | N1 | 99,326 | -0.23 [-0.25,-0.22] | -0.35 | -0.23 |
| sizing | N1 | 78,918 | +0.05 [+0.03,+0.06] | +0.06 | +0.04 |
| stack | N1 | 15,777 | -0.80 [-0.89,-0.71] | -1.13 | -0.81 |
| ALL | N0 | 1,436,497 | +0.00 [-0.00,+0.00] | +0.00 | +0.01 |

By strength of evidence (real records; the sizing column of the ledger uses these):

| scope | stratum | n | OOS/IS vs L3M [CI] | per final contract |
|---|---|---|---|---|
| pooled | all selected | 339,869 | -0.38 [-0.53,-0.18] | -0.49 |
| entry filter | all selected | 15,870 | -0.00 [-0.06,+0.05] | -0.00 |
| entry structure | all selected | 83,787 | -0.45 [-0.61,-0.16] | -0.49 |
| confirmation | all selected | 74,001 | -0.69 [-0.89,-0.41] | -1.13 |
| exit | all selected | 100,934 | -0.23 [-0.59,+0.10] | -0.26 |
| sizing | all selected | 26,099 | +0.04 [-0.03,+0.10] | +0.03 |
| stack | all selected | 5,680 | -1.36 [-2.66,-0.49] | -1.36 |
| regime | all selected | 33,498 | -0.27 [-0.54,-0.05] | -0.27 |
| pooled | t-stat(6m) 1-2 | 314,324 | -0.42 [-0.58,-0.21] | -0.54 |
| entry filter | t-stat(6m) 1-2 | 14,757 | -0.00 [-0.05,+0.05] | -0.00 |
| entry structure | t-stat(6m) 1-2 | 79,191 | -0.47 [-0.66,-0.17] | -0.54 |
| confirmation | t-stat(6m) 1-2 | 72,209 | -0.71 [-0.91,-0.42] | -1.16 |
| exit | t-stat(6m) 1-2 | 91,483 | -0.32 [-0.63,+0.05] | -0.31 |
| sizing | t-stat(6m) 1-2 | 24,195 | +0.03 [-0.03,+0.08] | +0.03 |
| stack | t-stat(6m) 1-2 | 5,639 | -1.37 [-2.69,-0.50] | -1.37 |
| regime | t-stat(6m) 1-2 | 26,850 | -0.28 [-0.55,-0.05] | -0.28 |
| pooled | t-stat(6m) 2-3 | 17,554 | -0.01 [-0.13,+0.08] | -0.08 |
| entry filter | t-stat(6m) 2-3 | 971 | -0.01 [-0.09,+0.04] | -0.01 |
| entry structure | t-stat(6m) 2-3 | 4,206 | -0.11 [-0.22,+0.01] | -0.14 |
| confirmation | t-stat(6m) 2-3 | 1,733 | -0.27 [-0.42,-0.17] | -0.25 |
| exit | t-stat(6m) 2-3 | 5,503 | +0.23 [-0.17,+0.49] | +0.02 |
| sizing | t-stat(6m) 2-3 | 1,580 | +0.07 [-0.03,+0.14] | +0.06 |
| regime | t-stat(6m) 2-3 | 3,520 | -0.15 [-0.39,+0.07] | -0.14 |
| pooled | t-stat(6m) >=3 | 7,991 | +0.25 [-0.06,+1.38] | +0.20 |
| entry structure | t-stat(6m) >=3 | 390 | -0.23 [-0.35,-0.12] | -0.25 |
| exit | t-stat(6m) >=3 | 3,948 | +0.59 [-0.03,+0.96] | +0.49 |
| sizing | t-stat(6m) >=3 | 324 | +0.30 [+0.15,+0.42] | +0.28 |
| regime | t-stat(6m) >=3 | 3,128 | -0.11 [-0.27,+2.00] | -0.10 |
| pooled | placebo beaten | 43,539 | -0.00 [-0.18,+0.12] | -0.11 |
| entry filter | placebo beaten | 2,195 | +0.00 [-0.07,+0.06] | +0.00 |
| entry structure | placebo beaten | 9,162 | -0.19 [-0.30,-0.04] | -0.31 |
| confirmation | placebo beaten | 4,914 | -0.32 [-0.45,-0.17] | -0.46 |
| exit | placebo beaten | 14,903 | +0.29 [-0.17,+0.50] | +0.10 |
| sizing | placebo beaten | 3,571 | +0.09 [-0.01,+0.17] | +0.09 |
| regime | placebo beaten | 8,573 | -0.15 [-0.36,+0.01] | -0.15 |
| pooled | PRE positive & placebo beaten | 16,759 | +0.01 [-0.16,+0.08] | -0.01 |
| entry filter | PRE positive & placebo beaten | 969 | -0.00 [-0.06,+0.05] | -0.00 |
| entry structure | PRE positive & placebo beaten | 2,706 | +0.05 [-0.18,+0.13] | +0.29 |
| confirmation | PRE positive & placebo beaten | 1,293 | -0.25 [-0.46,-0.04] | -0.29 |
| exit | PRE positive & placebo beaten | 5,508 | +0.20 [-0.10,+0.28] | +0.04 |
| sizing | PRE positive & placebo beaten | 1,758 | +0.11 [+0.01,+0.17] | +0.10 |
| regime | PRE positive & placebo beaten | 4,451 | -0.23 [-0.57,-0.02] | -0.22 |
| pooled | PRE positive | 120,976 | -0.20 [-0.41,+0.01] | -0.28 |
| entry filter | PRE positive | 6,583 | +0.01 [-0.04,+0.04] | +0.01 |
| entry structure | PRE positive | 22,141 | -0.20 [-0.46,+0.07] | -0.13 |
| confirmation | PRE positive | 21,733 | -0.52 [-0.79,-0.27] | -0.88 |
| exit | PRE positive | 44,396 | -0.11 [-0.48,+0.25] | -0.18 |
| sizing | PRE positive | 11,807 | +0.07 [+0.01,+0.13] | +0.07 |
| stack | PRE positive | 355 | -0.20 [-0.46,+0.20] | -0.20 |
| regime | PRE positive | 13,961 | -0.33 [-0.58,-0.13] | -0.32 |
| pooled | streak >=6 | 16,086 | -0.06 [-0.33,+0.18] | -0.12 |
| entry filter | streak >=6 | 620 | -0.06 [-0.18,+0.03] | -0.05 |
| entry structure | streak >=6 | 2,992 | -0.11 [-0.22,+0.02] | +0.12 |
| confirmation | streak >=6 | 1,759 | -0.42 [-0.58,-0.26] | -0.93 |
| exit | streak >=6 | 5,729 | +0.24 [-0.51,+0.65] | +0.10 |
| sizing | streak >=6 | 1,021 | +0.06 [-0.06,+0.15] | +0.06 |
| regime | streak >=6 | 3,910 | -0.34 [-0.53,-0.11] | -0.33 |

Plain sentences. A confirmation rule keeps **-69%** of its last-3-month magnitude (CI -88%..-41%). A sizing rule keeps **4%** of its last-3-month magnitude (CI -3%..9%). An exit rule keeps **-23%** of its last-3-month magnitude (CI -60%..11%). An entry-filter rule keeps **-0%** of its last-3-month magnitude (CI -6%..5%). An entry-structure rule keeps **-45%** of its last-3-month magnitude (CI -63%..-16%). A stack-level rule keeps **-136%** of its last-3-month magnitude (CI -270%..-40%). A regime / day-type rule keeps **-27%** of its last-3-month magnitude (CI -52%..-5%).
A negative factor does not mean the rule is a short signal: it means that picking rules because the last 3 and 6 months were positive selected rules that on average lose money in the following quarter, because most rules in the catalogue have a negative long-run mean against their floor. Where the evidence is strong (6-month t >= 3) the factor is positive: exit +0.59 [-0.03,+0.96] (n 3,948); sizing +0.30 [+0.15,+0.42] (n 324) - that is what such a recent edge is worth: roughly a third to a half of its recent number, with wide error.

## 6. (d) Which signals of persistence exist: walk-forward model P(persist) = f(features)

Logistic regression (L2, standardised features), refit every month on selections whose outcome window had finished; test months 2024-04 .. 2025-11 (20 months). Features: family, 6-month t-statistic, placebo rank / beaten flag, PRE sign, streak, log fire rate, stack correlation. Base rate = the training-set prevalence of persistence.

* Full-feature model on real records: Brier 0.2518 vs base rate 0.2485 (skill -1.3%, CI -5.5..+1.6), AUC 0.507; on the permuted-month baseline N1 the same model has skill +2.2% (it can read the rule's long-run mean through the family and t-statistic), on sign-flip noise N0 -0.01% (no skill, as it must be).

### 6.1 Ablation (Brier skill vs the family-only model; 95% CI by month blocks)

| features | Brier | skill vs family-only [CI] | AUC |
|---|---|---|---|
| family only | 0.2466 | +0.00% [+0.00,+0.00] | 0.542 |
| +z6 | 0.2445 | +0.87% [-0.10,+1.58] | 0.559 |
| +placebo rank | 0.2458 | +0.34% [-0.03,+0.64] | 0.552 |
| +streak | 0.2464 | +0.10% [-0.02,+0.26] | 0.546 |
| +PRE sign | 0.2482 | -0.62% [-2.69,+0.84] | 0.529 |
| +fire rate | 0.2466 | +0.01% [-0.09,+0.05] | 0.542 |
| +stack corr | 0.2493 | -1.07% [-3.23,+0.09] | 0.515 |
| +z6+PRE+streak+fire rate | 0.2458 | +0.33% [-1.91,+1.57] | 0.545 |
| all features | 0.2518 | -2.10% [-5.54,-0.39] | 0.507 |

Univariate AUC for "persists" (pooled test months): t-stat 0.558, placebo rank 0.558, PRE sign 0.541, streak 0.513, fire rate 0.478, stack correlation 0.503; within family: t-stat 0.542, placebo rank 0.542, PRE sign 0.528, streak 0.511, fire rate 0.486, corr 0.500. 0.5 = no information.

### 6.2 Calibration of the best walk-forward model (deciles of predicted P vs realised share positive)

| decile | predicted | realised | n |
|---|---|---|---|
| 1 | 0.25 | 0.38 | 24,756 |
| 2 | 0.32 | 0.42 | 24,755 |
| 3 | 0.34 | 0.39 | 24,755 |
| 4 | 0.35 | 0.38 | 24,755 |
| 5 | 0.36 | 0.40 | 24,755 |
| 6 | 0.38 | 0.37 | 24,755 |
| 7 | 0.40 | 0.38 | 24,755 |
| 8 | 0.44 | 0.50 | 24,755 |
| 9 | 0.48 | 0.53 | 24,755 |
| 10 | 0.53 | 0.56 | 24,756 |

Best feature set: **+z6**. Per-family AUC/Brier of the full model are in model_results.json. The realised share is flat at 37-42% across deciles 1-7 and 50-56% in deciles 8-10, while the predictions run 25-53%: the lowest deciles are under-forecast (the model learned on earlier months in which low-t rules reverted harder). Treat the score as a coarse ranking with a family-level offset, not a precise probability; its calibration slope is well below 1 in the middle and about right at the top.

## 7. Units (guard 5)

* Per planned lot = the stored delta per planned lot per base trade (exits, filters, confirmation, entry structure). Per contract of final position = sum of the delta / sum of final lots where the program stored lots (confirm2 cells, EINT1 sizing rules): shown in the "per final contract" column; for EINT1 sizing rules and confirmation cells that change lots the two differ and the per-contract ratio is the less favourable one. For rules that do not change lots the two are identical by construction.
* Stack-level families (sizing via split policies, L2SJ joint lines, THP chains, EINT2 day-type rules) are stored as lock-engine daily $ at research lots; per week = 5 x per day. For the selected stack/regime rules: mean in the selection window 1,877 $/wk, next 3 months -449 $/wk (average over selected rule-months of the 7-book/6-book stack delta; research lots, live lots about 1/2.35).

## 8. Caveats (honest)

* The study universe is the box's catalogue of scored rules, which is dominated by rules that lose to their floor; the persistence of "any rule that screens positive" is therefore low. A reader who only runs rules that passed the V2 gates is in the high-t tail (section 3.3 / 5), where persistence is 70%-83% and the exit/sizing shrinkage factor 0.3-0.6, but that tail is a handful of structural exit rules, not the entry/confirmation cells.
* The selection rule (positive L3M and L6M) is applied mechanically to every rule; rules that the programs themselves selected on L6M/HOLD/L3M are in the frame with the same weight as the rest (post-hoc selection by the programs is not undone).
* Several months are dominated by a single regime (the month-to-month swing in 3.2 is large); the CIs reflect 26 selection months only and are wide. 2025-09..2025-11 selections use after-windows that include Dec-Jan only partly independent of each other.
* Coverage: see section 2. Programs stored only as window aggregates (EINT1/EINT2 maps, ZONES-2, NEWIDEAS, TRENDGATE named tables, L2EA/L2EB entry grids, ADDUW, ABR bracket tables, SD-A/B/C, RC-1 reverse-confirm exits) are NOT in the study; the family results for their families are extrapolated by the family label only in the ledger.
* The sizing column in RECENT_WINS.md uses sections 5 and 2: size = mu_s^2/(mu_s^2+SE^2+(mu*se_shrink)^2), mu_s = shrink(family, t-bucket) x L3M, capped at 1.0; zero where mu_s <= 0.

## 9. Files

Code: l2vast/ds3/code/recentedge/ (re_lib.py, h1..h10 harvesters, floor_build.py, pe_frame.py, pe_study.py, pe_tables.py, pe_shrink2.py, pe_model.py, pe_report.py, run_study.sh, edge_columns.py). Outputs: l2vast/ds3/out/recentedge/ (series/*.npz monthly series, sample.npz, study_records.parquet, persistence_table.csv, curve_by_month.csv, decay.csv, shrinkage.csv, shrinkage_strata.csv, model_results.json, model_ablation.csv, model_calibration_best.csv, persist_model_best.pkl, frame_summary.json).