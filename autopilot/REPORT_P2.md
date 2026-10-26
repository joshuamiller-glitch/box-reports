# REPORT P2 - regime stand-down (walk-forward size switch) on the pair, 2013-2026

**Verdict: NO as a profit lever on the live path; LEAD-only as a risk-control monitor on the scaled path is NOT supported either. The apparent 13-year gain (Sharpe -0.59 -> +0.30 on run_a_real; +0.13 -> +0.86 on run_fixed_real) is almost entirely "stop trading a path with no edge in 2013-22" and does not carry into the live era: on 2023-26 the selected rules change Sharpe by +0.32 (a_real, bootstrap 90% CI [-0.08,+0.78]) and -0.04 (fixed_real, CI [-0.38,+0.24]) while the false-stand-down cost in 2024-26 is -$264k / -$259k and in 2023-08..2025-07 -$103k / -$316k. H1 and H2: the selected rules stood down 0 weeks (no effect, no protection).** Selection-aware null: p = 0.54 (a_real), 0.03 (fixed_real).

Pre-registered in PREREG_AUTOPILOT.md (CYCLE 11) before any run. Code: code/census/night_ins/ap_p2.py (grid, selection), ap_p2_eval.py (scores, nulls, bootstrap; 5-worker pool). Outputs: outputs/autopilot/p2/{grid_a_real.csv, grid_fixed_real.csv, sel.pkl, P2_eval.txt}. Runtime ~3 min.

## Design (as pre-registered)
Paths: run_a_real (scaled bracket a, real cost; faithful) and run_fixed_real (live fixed 60); weekly P&L (ISO week by label day) of the pair at 8/8 with the live rules, in $. Decision after week t uses weeks <= t of the pair's own ungated shadow P&L (so a stood-down pair can still re-enter), applied to week t+1. Grid A (36): trailing {13,26,52}-week Sharpe < {0,0.5,1.0} -> size {0, 0.5}; re-enter after Sharpe > threshold for {4,8} consecutive weeks. Grid B (32): D3 S3 early-warning statistic (trailing 8- and 13-week Sharpe of the HM book's weekly P&L, code d3_s3_health.py; HM rows of the same pair run) with an expanding walk-forward q-quantile threshold (5%/10%, min 52 weeks) or the fixed D3 thresholds (-2.65/-3.74 for sharpe8, -1.54/-2.17 for sharpe13; flagged: those were fitted on 2023-25). Selection per path on the weekly Sharpe over 2013-22 + clean 2023-08..2025-07 weeks (concatenated), with a guard that the clean net is >= 75% of always-on. H1/H2 read once for the selected rule.
(Caveat: the D3 statistic was designed on HM's HM-live-ruled book; here HM is the live-ruled HM rows of each path.)

## Selected rules and scores (always-on vs gated; $ at pair 8/8)
**run_a_real - A_W26_th0_s0_N8** (stand down to 0% when trailing-26-week Sharpe < 0; re-enter after 8 consecutive weeks > 0)
| span | weeks | Sharpe on / gated | net on / gated | maxDD on / gated | % weeks down | worst year on / gated | worst week on / gated |
|---|---|---|---|---|---|---|---|
| 2013-2026 | 719 | -0.59 / 0.30 | -$3.61M / +$1.06M | $6.27M / $1.30M | 71% | -$1.34M / -$0.59M | -$84k / -$83k |
| 2013-22 | 521 | -1.37 / -0.79 | -$5.78M / -$1.30M | $5.90M / $1.30M | 85% | | |
| 2023-26 | 192 | 1.24 / 1.56 | +$2.17M / +$2.36M | $585k / $260k | 31% | -$454k / $0 | -$79k / -$79k |
| clean | 104 | 1.71 / 1.82 | $1.55M / $1.45M | $260k / $260k | 34% | | |
| H1 | 27 | 2.18 / 2.18 | $540k / $540k | | 0% | | |
| H2 | 36 | 1.03 / 1.03 | $371k / $371k | | 0% | | |
Stand-down episodes (start, weeks, always-on net during): 2013-07 252 wks -$3.42M (the path never recovered a positive 26-week Sharpe for 5 years); 2018-05 39 -> +$326k (false); 2019-06 75 -> -$875k; 2021-04 17 -> -$29k; 2021-08 20 -> +$259k (false); 2022-03 106 -> -$922k (spans into 2023-2024, so it also dodges 2023's -$454k and delays entry into 2024).
**run_fixed_real - A_W52_th1.0_s0_N4**
| span | weeks | Sharpe on / gated | net on / gated | maxDD on / gated | % down | worst year on / gated | worst week on / gated |
|---|---|---|---|---|---|---|---|
| 2013-2026 | 719 | 0.13 / 0.86 | +$0.61M / +$2.50M | $2.53M / $0.26M | 73% | -$921k / -$54k | -$80k / -$79k |
| 2013-22 | 521 | -0.79 / -0.07 | -$2.24M / -$23k | $2.49M / $119k | 89% | | |
| 2023-26 | 192 | 1.77 / 1.73 | +$2.93M / +$2.52M | $257k / $257k | 31% | +$147k / $0 | -$79k / -$79k |
| clean | 104 | 1.69 / 1.55 | $1.52M / $1.20M | $257k / $257k | 33% | | |
| H1 | 27 | 2.73 / 2.73 | $616k / $616k | | 0% | | |
| H2 | 36 | 2.00 / 2.00 | $706k / $706k | | 0% | | |
Episodes: 2013-12 163 wks +$33k; 2017-02 16 wks +$59k (false); 2017-07 348 wks (to 2024-03; always-on during = -$1.98M).

## False-stand-down cost 2024-2026 (explicit)
| path | weeks 2024-26 | weeks down | pair earned > 0 in those | always-on net in stood-down weeks | of which earned weeks / losing weeks | net lost vs always-on |
|---|---|---|---|---|---|---|
| a_real, W26/th0/N8 | 146 | 14 (10%) | 8 (57%) | +$264,530 | +$512,775 / -$248,245 | **$264,530** |
| fixed_real, W52/th1/N4 | 146 | 13 (9%) | 8 (62%) | +$259,313 | +$537,196 / -$277,883 | **$259,313** |
In the clean window (2023-08..2025-07): 35 / 34 weeks down, 18 of which the pair earned; net lost $103k / $316k. The rule is late into the 2024 recovery (it stays down through the first months of 2024 after a losing 2022-23) and gives up the first profitable weeks; it removes nothing in H1/H2 (no stand-down at all, so no protection for the 2026-09 HM drawdown either).

## Grid-wide view (whole grid, not just the selected rule; grid_*.csv)
| span | a_real: always-on Sharpe; rules better / 68; median net change | fixed_real: always-on; rules better; median net change |
|---|---|---|
| 2013-26 | -0.59; 68; +$1.98M | 0.13; 57; +$0.27M |
| 2013-22 | -1.37; 51; +$2.24M | -0.79; 22; +$0.78M |
| 2023-26 | 1.24; 27; **-$204k** | 1.77; 7; **-$370k** |
| clean | 1.71; 17; -$160k | 1.69; 3; -$318k |
| H1 | 2.18; 0; $0 | 2.73; 0; $0 |
| H2 | 1.03; 6; $0 | 2.00; 3; $0 |
The typical rule loses money in the live era; on the live fixed path only 7 of 68 rules raise 2023-26 Sharpe. Top-5 by the selection objective are all trailing-26/52-week Sharpe rules to 0% size (HM early-warning rules rank lower: best B rule objective -0.17 / -0.14; on fixed_real the 13-week HM statistic at its expanding 5-10% quantile never triggers in 2023-26 = harmless but no effect; the fixed D3 thresholds with N=8 stand down 12-28% of 2023-26 weeks on a_real and cost money). The HM early-warning statistic is therefore not a useful trigger for the full pair in this walk-forward test.

## Nulls and bootstrap (600 null draws per type, 500 bootstrap reps)
| test | a_real | fixed_real |
|---|---|---|
| iid random stand-down weeks, same count: 13-yr gated Sharpe vs null median / p95 (p) | 0.30 vs -0.33 / 0.04 (p=0.005) | 0.86 vs 0.06 / 0.44 (p<0.002) |
| same, 2023-26 | 1.56 vs 0.68 / 1.28 (p=0.010) | 1.73 vs 0.90 / 1.54 (p=0.015) |
| circular shift of the actual stand-down mask, 13-yr p / 2023-26 p | 0.103 / 0.048 | 0.065 / 0.060 |
| **selection-aware null** (best of 68 random-mask rules, objective on 2013-22 + clean): real vs null median / p95 | 0.05 vs 0.07 / 0.34 (p=0.54) | 0.60 vs 0.33 / 0.57 (p=0.03) |
| block bootstrap (mean 8 wks) of paired Sharpe(gated)-Sharpe(on): 13-yr 90% CI | [+0.42,+1.31] | [+0.36,+1.10] |
| 2013-22 | [-0.08,+1.31] | [+0.13,+1.32] |
| **2023-26 Sharpe diff / net diff** | [-0.08,+0.78]; net [-$434k,+$830k] | **[-0.38,+0.24]; net [-$1.02M,+$72k]** |
Reading of the random-week nulls: the iid null is easily beaten because stand-down weeks are clustered in losing stretches (that is the point of a trailing rule, serial dependence of the pair's weekly P&L), and the shift null (which preserves clustering) is not beaten (p 0.06-0.10). The selection-aware null on a_real is not beaten at all (p=0.54).

## Honest interpretation
1. On the 13-year path the "improvement" is a statement about 2013-22 where the pair has no edge (gross Sharpe ~+0.05, real -1.4): any rule that switches the strategy off after the first bad stretch wins there. It is not evidence that the live-era pair can be timed. Both selected rules sit in cash 85-89% of 2013-22 and 31% of 2023-26.
2. On the live era alone (2023-26) the effect is a wash: +0.32 / -0.04 Sharpe with bootstrap CIs spanning zero, with -$264k / -$259k of false stand-down in 2024-26 and zero stand-down in H1/H2. Where the a_real rule helps in 2023-26 it does so by sitting out the 2023 loss year (-$454k), i.e. through the 2022-23 regime continuation, not through detecting the 2026-09 drawdown.
3. Cross-application: the other path's selected rule on this path gives 13-yr Sharpe 0.10 (a_real, with fixed's rule) and 0.71 (fixed_real, with a's rule) - same story.
4. Gates (pre-registered): Sharpe gain >= +0.10 on both 2013-22 and 2023-26: a_real +0.58/+0.32 (OK), fixed_real +0.72/-0.04 (FAIL); iid null p <= 0.05 OK both, but selection-aware null p 0.54 (a_real FAIL) / 0.03; bootstrap 2023-26 net CI excludes a loss > 0.10 of net: FAIL for fixed_real (lower bound -$1.02M = -35% of net), a_real lower bound -$434k = -20% (FAIL). **Overall: NO.**
5. The only credible use is the one the D3 report supports: a monitor, not an automatic switch. A stand-down lever costs a quarter-million dollars per two years of false signals against a drawdown it has not demonstrably avoided.

## Spec if ever built (quant-dash monitor + size switch; NOT DualStrat logic)
- Input: weekly P&L of the live pair (ungated shadow, every Sunday close: sum of Mon-Fri label days from the NT8 trade list). Quant-dash computes trailing 26-week Sharpe = mean/std(ddof=1) x sqrt(52).
- Alert (monitor only): trailing Sharpe < 0 -> amber; stays < 0 -> red; recovery needs 8 consecutive weeks > 0 for green. The size switch (0% or 50% from the following Monday, via the existing account size/enable toggle, human-confirmed) is not recommended on this evidence; if used, 50% size loses less on false stand-downs than 0% (grid shows s=0.5 variants in grid_*.csv).
- Data: needs only the weekly P&L series (no tick data), 26 weeks of history, runs in the dash, no NT8 change. Executable at NTB/Rithmic (it is a size toggle, no new orders); margin falls with stand-down.
Insurance metrics: stand-down reduces maxDD on the 13-yr path (6.27M -> 1.30M) only by not trading 2013-22; on clean/H1/H2 maxDD, worst week and CVaR are unchanged (rule inactive in H1/H2, the worst week -$79k happens at full size).
DONE P2
