# REPORT C9-R1 - calendar avoid-filters on the pair (autopilot cycle 9)

**Task:** five frozen avoid-filters (release windows, quarterly roll week, holiday sessions, last trading day of month, Friday after 14:00 ET) tested as skips of NEW pair entries; developed on the pair's 2013-2022 trades (1-minute engine, C3-H2), then read untouched on 2023-2026. Pre-registered in `PREREG_AUTOPILOT.md` ('CYCLE 9') before any run.

## Verdict
**NO. FOUND 0, LEAD 0.** None of the six registered cells passes the development criterion (removed-trade mean below overall in >= 6 of 10 years), and none of them lifts weekly Sharpe by +0.10 on clean, H1 and H2 together (gate 3). The nearest, **Friday-after-14:00**, is +0.07 / +0.09 / -0.02 on clean / H1 / H2 and removes only 170 of 13,089 entries; it fails development (3 of 7 years) and H2. The only filter that passes development, last-2-days-of-month (8 of 10 years), is a registered *plateau variant*, not a gating cell, so it cannot count; its untouched read is negative (clean -0.29, H1 -0.54, H2 +0.39).

## Setup
- Pair: live corrected engine `B.Cfg(wk_floor=8, wk_loss_pb=None)` computed in a clean process (no `b10_core` import; asserted); robustness vs `B.Cfg()` below. 1 tick/side + $34.88 commission. Filters skip NEW entries via `Cfg.skipmask`; the account model (per-book rules, day lock, week floor) is re-run, so each cell's effect includes the path interaction.
- Development sample: the pair's 2013-2022 trades from the C3-H2 1-minute engine (`h2_pair_long.pkl`; entry match to the live engine 90%, so read magnitudes loosely), live-rule-surviving trades only (f > 0), net points after 1 tick/side.
- Dates: FOMC/NFP/CPI 2023-2026 **verified** (`ap_c2_g3_events.py`: Fed and BLS schedule pages). **Unverified:** FOMC 2013-2022 (from memory), NFP 2013-2022 (BLS release rule), CPI pre-2023 not available (E1 uses FOMC+NFP), holiday/early-close list by rule (Black Friday, Dec 24-26, Dec 31, Jan 2, Jul 3 if weekday), roll weeks = 5 business days before the third-Friday expiry of Mar/Jun/Sep/Dec (the registered text is ambiguous; this is the literal 'five trading days before the expiry'; 3 and 8 days and +expiry are plateau variants).

## 1. Development table (2013-2022, untouched by the live window)
| filter | registered gating | removed trades | % of trades | mean net pts removed | mean net pts all | delta | t vs rest | years removed < overall | years with >=3 removed | dev pass (>=6 of 10) | $ saved 2013-22 (post-lock) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| E1_FOMC+NFP_w30 | True | 44 | +0.5 | -10.99 | -1.54 | -9.45 | -1.12 | 3 | 4 | False | 81,415 |
| E1_FOMC+NFP_w60 | True | 63 | +0.7 | -6.96 | -1.54 | -5.42 | -0.78 | 3 | 5 | False | 72,477 |
| E1v_FOMC+NFP_w15 | False | 36 | +0.4 | -9.44 | -1.54 | -7.91 | -0.82 | 3 | 4 | False | 58,176 |
| E1v_FOMC+NFP_w90 | False | 63 | +0.7 | -6.96 | -1.54 | -5.42 | -0.78 | 3 | 5 | False | 72,477 |
| E2_roll5 | True | 750 | +7.9 | +2.75 | -1.54 | +4.29 | +2.39 | 0 | 10 | False | -318,800 |
| E2v_roll3 | False | 485 | +5.1 | +0.79 | -1.54 | +2.33 | +1.02 | 4 | 10 | False | -53,123 |
| E2v_roll8 | False | 1197 | +12.7 | -1.22 | -1.54 | +0.32 | +0.23 | 4 | 10 | False | 258,791 |
| E2v_roll5+exp | False | 878 | +9.3 | +2.55 | -1.54 | +4.09 | +2.50 | 0 | 10 | False | -351,935 |
| E3_holiday | True | 129 | +1.4 | +4.09 | -1.54 | +5.62 | +1.33 | 4 | 9 | False | -81,300 |
| E3v_holiday_narrow | False | 73 | +0.8 | +6.03 | -1.54 | +7.57 | +1.39 | 2 | 9 | False | -74,974 |
| E3v_holiday_wide | False | 317 | +3.4 | -0.15 | -1.54 | +1.39 | +0.52 | 5 | 10 | False | 18,457 |
| E4_lastday | True | 425 | +4.5 | -3.30 | -1.54 | -1.76 | -0.75 | 5 | 10 | False | 171,104 |
| E4v_last2 | False | 858 | +9.1 | -5.63 | -1.54 | -4.09 | -2.55 | 8 | 10 | True | 664,247 |
| E5_fri14 | True | 40 | +0.4 | -3.46 | -1.54 | -1.92 | -0.34 | 3 | 7 | False | 16,435 |
| E5v_fri13 | False | 72 | +0.8 | -0.05 | -1.54 | +1.49 | +0.34 | 3 | 9 | False | -13,489 |
| E5v_fri15 | False | 1 | +0.0 | +15.75 | -1.54 | +17.29 | +nan | 0 | 0 | False | -2,485 |

Reading: **E2 (roll week) has the opposite sign in all 10 years** - roll-week trades earned +2.75 net pts against -1.54 overall, so avoiding them would have cost $319k over 2013-2022. E1 has too few trades (4-5 years with >= 3 removed) and 3 of 4-5 years below overall. E3, E4, E5 do not reach 6 of 10. The post-hoc last-2-days variant (8 of 10 years, t = -2.5) is flagged *exploratory*.

## 2. Untouched read (live rows, 2023-02..2026-10; spans clean 2023-08..2025-07, H1, H2)
Baseline pair Sharpe: clean 1.46, H1 2.83, H2 2.30 (this config).
| filter | registered | entries removed (live rows) | clean Sharpe uplift | H1 | H2 | all-in | all-in net % | all-in worst-week chg % | gate 3 | boot 5% | boot 95% | rolling26 >= base | all-in uplift at 2x slippage |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| E1_FOMC+NFP_w30 | True | 140 | -0.088 | -0.118 | -0.192 | -0.112 | -6.7 | +0.0 | False | -0.227 | -0.009 | 20% | -0.095 |
| E1_FOMC+NFP_w60 | True | 191 | -0.101 | -0.154 | -0.240 | -0.136 | -8.9 | +0.0 | False | -0.264 | -0.019 | 20% | -0.122 |
| E2_roll5 | True | 1049 | -0.133 | -0.757 | -0.321 | -0.259 | -17.5 | +0.8 | False | -0.597 | +0.059 | 31% | -0.265 |
| E3_holiday | True | 143 | -0.137 | -0.433 | -0.144 | -0.176 | -9.6 | +0.0 | False | -0.307 | -0.069 | 0% | -0.170 |
| E4_lastday | True | 604 | -0.017 | -0.399 | +0.283 | +0.012 | -0.5 | +0.0 | False | -0.244 | +0.289 | 40% | +0.027 |
| E5_fri14 | True | 170 | +0.069 | +0.088 | -0.021 | +0.052 | +2.7 | +0.0 | False | +0.004 | +0.105 | 72% | +0.042 |
| E4v_last2 | False | 1227 | -0.286 | -0.544 | +0.394 | -0.152 | -9.6 | +0.0 | False | -0.506 | +0.201 | 32% | -0.073 |
| E1v_FOMC+NFP_w15 | False | 109 | -0.115 | -0.124 | -0.237 | -0.142 | -8.1 | +0.0 | False | -0.268 | -0.032 | 6% | -0.125 |
| E1v_FOMC+NFP_w90 | False | 193 | -0.091 | -0.154 | -0.240 | -0.130 | -8.6 | +0.0 | False | -0.256 | -0.013 | 20% | -0.116 |
| E2v_roll3 | False | 634 | -0.152 | -0.217 | +0.110 | -0.104 | -9.2 | +0.8 | False | -0.290 | +0.093 | 22% | -0.114 |
| E2v_roll8 | False | 1768 | -0.286 | -0.709 | +0.227 | -0.216 | -18.1 | +0.8 | False | -0.602 | +0.156 | 36% | -0.220 |
| E2v_roll5+exp | False | 1235 | -0.151 | -0.487 | -0.222 | -0.208 | -16.0 | +0.8 | False | -0.545 | +0.118 | 36% | -0.215 |
| E3v_holiday_narrow | False | 46 | -0.044 | -0.344 | +0.000 | -0.074 | -3.6 | +0.0 | False | -0.167 | +0.000 | 43% | -0.069 |
| E3v_holiday_wide | False | 256 | -0.102 | -0.129 | -0.144 | -0.112 | -6.4 | +0.0 | False | -0.223 | -0.013 | 16% | -0.105 |
| E5v_fri13 | False | 327 | +0.130 | -0.023 | -0.002 | +0.084 | +4.4 | +0.0 | False | +0.015 | +0.158 | 70% | +0.084 |
| E5v_fri15 | False | 11 | +0.001 | -0.011 | +0.000 | -0.001 | -0.1 | +0.0 | False | -0.007 | +0.005 | 73% | -0.001 |

Gate 3 = Sharpe uplift >= +0.10 on clean, H1 and H2 separately and worst week not worse: **0 of 16 filters (including plateau variants) pass.** The worst week is unchanged for every filter except the roll-week family, where the all-in worst week improves by only 0.8%. Standard SURVIVES/INSURANCE key tables: `c9/r1/REPORT_C9_R1_keytable_live.md` and `..._b11.md`: all cells NO.

Robustness vs `B.Cfg()` (per-book -6R week rule on, no week floor; Sharpe 1.35 / 1.65 / 2.26): uplifts
| filter | clean | H1 | H2 | all-in | all-in net % |
|---|---|---|---|---|---|
| E1_FOMC+NFP_w30 | -0.072 | -0.089 | -0.112 | -0.081 | -5.7 |
| E1_FOMC+NFP_w60 | -0.086 | -0.128 | -0.159 | -0.106 | -8.1 |
| E2_roll5 | -0.061 | -0.582 | -0.495 | -0.246 | -18.7 |
| E3_holiday | -0.135 | -0.314 | -0.159 | -0.171 | -10.6 |
| E4_lastday | -0.113 | -0.274 | +0.276 | -0.047 | -3.3 |
| E5_fri14 | +0.038 | +0.070 | -0.022 | +0.031 | +1.8 |
| E4v_last2 | -0.320 | -0.385 | +0.500 | -0.150 | -10.3 |
| E1v_FOMC+NFP_w15 | -0.087 | -0.099 | -0.156 | -0.102 | -6.8 |
| E1v_FOMC+NFP_w90 | -0.076 | -0.128 | -0.159 | -0.100 | -7.7 |
| E2v_roll3 | -0.095 | -0.180 | -0.109 | -0.114 | -10.5 |
| E2v_roll8 | -0.144 | -0.427 | +0.193 | -0.116 | -14.9 |
| E2v_roll5+exp | -0.079 | -0.383 | -0.404 | -0.202 | -17.0 |
| E3v_holiday_narrow | -0.043 | -0.247 | +0.000 | -0.069 | -4.0 |
| E3v_holiday_wide | -0.101 | -0.091 | -0.159 | -0.111 | -7.1 |
| E5v_fri13 | +0.056 | +0.045 | -0.004 | +0.042 | +2.7 |
| E5v_fri15 | +0.001 | -0.012 | +0.000 | -0.001 | -0.1 |

## 3. Nulls (matched random removal, same removed-entry count per book)
Run for the best registered cell (E5 Fri 14:00) and the exploratory E4 last-2-days variant only; the other cells fail gate 3 outright.

**E5_fri14** (removed per book ST/HM = [90, 80], 500 matched random-removal draws; same removed-entry count per book, uniformly random entries):

| span | real Sharpe uplift | null median | null p95 | real rank in null |
|---|---|---|---|---|
| clean | +0.069 | -0.058 | +0.160 | 0.82 |
| H1 | +0.088 | -0.016 | +0.407 | 0.65 |
| H2 | -0.021 | -0.073 | +0.444 | 0.59 |
| all | +0.052 | -0.057 | +0.143 | 0.83 |

**E4v_last2** (removed per book ST/HM = [732, 495], 500 matched random-removal draws; same removed-entry count per book, uniformly random entries):

| span | real Sharpe uplift | null median | null p95 | real rank in null |
|---|---|---|---|---|
| clean | -0.286 | -0.186 | +0.267 | 0.36 |
| H1 | -0.544 | -0.113 | +0.993 | 0.23 |
| H2 | +0.394 | -0.420 | +0.686 | 0.89 |
| all | -0.152 | -0.204 | +0.193 | 0.60 |

Reading: the real E5 uplift ranks 0.82 / 0.65 / 0.59 / 0.83 in its null (p95 needed), i.e. a random removal of 170 entries does as well about one time in five; the last-2-days variant is at or below the median on clean and H1 and only H2 (0.89) leans positive. Neither is distinguishable from chance.

## 4. Plateau, bootstrap, rolling, slippage
- **E5 Friday-after-14:00 (best):** neighbours Fri 13:00 +0.084 and Fri 15:00 -0.001 all-in against its own +0.052; 1 of 2 neighbours keeps 75% of the uplift (the 15:00 window removes only 11 entries). All-in bootstrap interval for the Sharpe uplift [+0.004, +0.105] (clears zero by 0.004, all-in only; the H2 effect is negative), rolling 26-week Sharpe at or above the pair in 72% of windows, 2x-slippage all-in uplift +0.042.
- **All other filters:** negative all-in uplift in the main cell and in both neighbours (E1, E2, E3), or all-in positive from H2 alone and negative in clean/H1 (E4). Bootstrap intervals contain zero or are negative; E1 and E3 intervals are entirely negative.
- Descriptive (no gate): roll-week entries in the live window earn -10.7 pts (2023-02..07), +1.0 (clean, vs 1.5 overall), +9.2 (H1, vs 4.2), +1.4 (H2, vs 1.1) - no stable sign, so a size-*up* in roll weeks is not supported either.

## 5. Implementability and limits
Each filter is a dated no-new-entries window: a DualStrat parameter-level change (time/date blackout list; the release and holiday lists need maintenance). None is recommended. Limits: development trades come from the 1-minute engine (90% entry match, a losing sample), so a "removed trades are worse" test is weak by construction; E1 has under 50 removed trades per year; holiday/roll dates partly unverified; slippage 1 tick/side, not calibrated to live fills. Fill model: unchanged live rows with entries skipped (no new fills simulated).

Runtime: calendar + development table seconds; untouched read 51 account runs in 131 s on 4 workers; the two 500-draw nulls took 23 and 19 minutes on 4 workers.

DONE C9_R1
