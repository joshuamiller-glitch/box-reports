# DS3_DIV2_E_MBO - the seven frozen NQ MBO setups as diversifiers of the live stack (T-DIVERSIFY-2 section E)

Agent D3D2E, 2026-10-28. Audit only: no new cells, no preregs, no execution-server or live file touched, no downloads. Code `l2vast/ds3/code/dv2e/` (e0_stack.py, e1_audit.py, e2_report.py), outputs `l2vast/ds3/out/dv2e/`.

## 0. VERDICT (plain)

- **Paper-soak series are NOT on this box** (see NEEDS). Everything below is the research backtest series of the seven (`h2/NQ7_3Y_TRADES_RECONSTRUCTED.csv`, 4,314 trades 2023-02-09..2026-02-06, a frozen-replay reconstruction, not live fills). No UNTOUCHED date read.
- **They are not another way of buying NQ trend.** Weekly correlation to the live stack is -0.09 to +0.09 across the seven (all 95% CIs contain 0; n=149 weeks, CI half-width about 0.16); seven-together +0.01 [-0.15,+0.17]. At the moment each MBO trade opens the stack is flat 45% of the time, on the same side 29%, on the opposite side 26%: direction-neutral relative to the stack.
- **But none is a demonstrated crisis hedge.** In the stack's 20 worst weeks every one of the seven earned money (all 7 positive; seven-together $102,366 at 1 NQ per setup), yet that is no better than chance: circular-shift null p(>= observed) = 0.21-0.69 for the seven, 0.42 together. Most of the worst-20 gain is simply their positive average week, not a negative dependence. Inside the worst-20 weeks the conditional correlation to the stack is negative for 5 of 7 (n=20 each, noisy; seven-together -0.33).
- **The one number: $ in the stack's 20 worst weeks at 20% risk for the best one = +$129,145** (H300000_cd_extratrees_Q575, 1-NQ-per-setup series scaled so its weekly SD is 20% of the stack's, = 3.86 NQ contracts of that setup), against the stack's own -3,303,356 in those 20 weeks (offset 3.9%). It is the best of seven chosen after the fact (best-of-7, p vs circular-shift null = 0.21), so treat it as an upper-end read, not an estimate; $82,461 of it is covariance (above its own average week), the rest is its average edge. Seven-together at 20% risk: +$77,771. Best marginal Sharpe at 20%: H300000_cd_histgb_Q700 +0.146 (stack 2.235).
- Verdict: **an uncorrelated, direction-neutral stream with a positive but statistically unproven mean (weekly means below are at or under their MDE). A weak diversifier by correlation (about 0), not shown to be a hedge in the worst weeks.** The edge itself is the open question; the seven were selected on 2023-02..2024-01 (IS) and on the pure out-of-sample part (WF 2024-02+, 105 weeks) seven-together earns $5,398/wk against an MDE of $10,703 (t about 1.4).

## 1. Definitions and data

- **Stack** = ST10+HM10+WT7 + KB/SM/PB (PB is the PE slot) from the exact corrected per-book lock engine, DS3 monthly weights, entries 09:00-09:59 blocked (`stacks()['live']` in `o2_eng.py`, the construction used by `o2_conc.py`/`cfc_lib.py` for DS3_CONFIRM_C); report-scale dollars, daily by label day (ET+6h). Pre-2023-04 weights are corrupt, so the window starts 2023-04-01; ends 2026-02-06 (UNTOUCHED never read; the stack arrays hold later days, cut before use). 149 weeks (Sun 18:00 ET weeks). Stack: mean $39,275 /wk, SD $126,746 /wk, Sharpe 2.23, daily-curve maxDD $548,152, worst week $-339,821.
- **MBO seven** = the seven frozen setups (names below), P&L per trade `net_usd_nq` (1 NQ contract, file carries 14.5 per round trip) adjusted by -0.34 to the FEES.md NQ standard $4.84 RT + 1 tick/side; booked on the exit label day. Sensitivity with the more conservative MNQ-cost-x10 convention (-$22/round trip) in section 6: nothing changes. Unit = 1 NQ per setup; ALL7 = 7 contracts.
- **Stack-add at p% of stack risk**: the MBO weekly series is scaled so its weekly SD equals p% of the stack's weekly SD ($126,746 /wk) and added to the stack. 'Worst-20-weeks $' = the added P&L in the 20 weeks in which the stack alone lost most (selected on the stack only, full 149-week window, 13 of the 20 are in WF 2024-02+). maxDD from the daily combined curve.
- **MDE** = 2.8 x SE of the weekly mean (80% power, 5% two-sided) at 1 NQ per setup. Sample size is the number of weeks n.

## 2. The seven: weekly P&L, sample size, MDE, correlation (research series, 1 NQ each)

| setup | trades | n wks | weekly mean $ | SE | MDE80 $ | mean/MDE | Sharpe | corr to stack [95% CI] | Spearman | corr in stack worst-25% wks | $/wk in stack worst-20 (SE) | $/wk other 129 | worst-20 sum $ | null p (>=) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| H120000_cd_xgboost_Q725 | 327 | 149 | 728 | 514 | 1,438 | 0.51 | 0.84 | +0.09 [-0.07,+0.25] | +0.15 | -0.25 | 168 (625) | 815 | 3,369 | 0.69 |
| H250_tb_long_xgboost_Q750 | 459 | 149 | 478 | 555 | 1,554 | 0.31 | 0.51 | +0.02 [-0.14,+0.18] | +0.04 | -0.06 | 1,359 (750) | 341 | 27,187 | 0.23 |
| H300000_cd_extratrees_Q575 | 769 | 149 | 604 | 537 | 1,505 | 0.40 | 0.66 | -0.09 [-0.25,+0.07] | -0.04 | -0.30 | 1,671 (672) | 439 | 33,422 | 0.21 |
| H300000_cd_histgb_Q700 | 782 | 149 | 431 | 291 | 815 | 0.53 | 0.87 | -0.04 [-0.20,+0.12] | -0.01 | -0.09 | 270 (632) | 456 | 5,407 | 0.60 |
| H60000_cd_histgb_Q675 | 335 | 149 | 853 | 517 | 1,447 | 0.59 | 0.97 | +0.02 [-0.15,+0.18] | -0.13 | -0.16 | 552 (267) | 899 | 11,036 | 0.52 |
| H60000_yeb_catboost_Q625 | 1,017 | 149 | 776 | 543 | 1,521 | 0.51 | 0.84 | -0.01 [-0.17,+0.15] | -0.05 | -0.18 | 879 (859) | 760 | 17,583 | 0.45 |
| H60000_yeb_lightgbm_Q700 | 438 | 149 | 523 | 503 | 1,408 | 0.37 | 0.61 | +0.06 [-0.10,+0.22] | +0.09 | +0.08 | 218 (537) | 570 | 4,361 | 0.60 |
| ALL7 | 4,127 | 149 | 4,392 | 2,733 | 7,654 | 0.57 | 0.95 | +0.01 [-0.15,+0.17] | +0.03 | -0.29 | 5,118 (2,208) | 4,279 | 102,366 | 0.42 |

Every weekly mean is below its MDE (mean/MDE < 1): none of the seven has a statistically established weekly mean on its own at n=149 (block-bootstrap 95% CI of the mean: H120000_cd_xgboost_Q725 [79,1,538]; H250_tb_long_xgboost_Q750 [-374,1,296]; H300000_cd_extratrees_Q575 [-320,1,493]; H300000_cd_histgb_Q700 [-137,978]; H60000_cd_histgb_Q675 [-43,2,079]; H60000_yeb_catboost_Q625 [-223,1,885]; H60000_yeb_lightgbm_Q700 [-63,1,287]; ALL7 [1,490,8,059]). Only H120000_cd_xgboost_Q725 and the seven-together series have a block CI that excludes 0, and both include the in-sample 2023-04..2024-01 weeks (WF-only means are in section 2b).

### 2b. By window (selection window = IS; WF and HOLD are out-of-sample for the MBO selection; HOLD is also the stack's holdout)

| setup | IS 2023-04..2024-01 mean (n=44) / MDE / corr | WF 2024-02+ mean (n=105) / MDE / corr [CI] | HOLD 2025-07+ mean (n=31) / MDE / corr [CI] |
|---|---|---|---|
| H120000_cd_xgboost_Q725 | 425 / 957 / +0.19 | 855 / 2,004 / +0.09 [-0.11,+0.27] | 140 / 1,115 / -0.04 [-0.39,+0.32] |
| H250_tb_long_xgboost_Q750 | 562 / 789 / +0.23 | 443 / 2,183 / +0.01 [-0.18,+0.20] | 816 / 2,744 / -0.18 [-0.50,+0.19] |
| H300000_cd_extratrees_Q575 | 596 / 1,377 / +0.10 | 607 / 2,060 / -0.12 [-0.31,+0.07] | 2,278 / 3,300 / -0.31 [-0.60,+0.05] |
| H300000_cd_histgb_Q700 | 105 / 1,159 / +0.16 | 567 / 1,051 / -0.09 [-0.28,+0.10] | 96 / 934 / -0.42 [-0.68,-0.08] |
| H60000_cd_histgb_Q675 | 101 / 666 / +0.07 | 1,167 / 2,032 / +0.01 [-0.19,+0.20] | -171 / 882 / -0.41 [-0.67,-0.07] |
| H60000_yeb_catboost_Q625 | 313 / 1,525 / +0.30 | 970 / 2,063 / -0.06 [-0.25,+0.13] | -297 / 1,029 / -0.22 [-0.53,+0.15] |
| H60000_yeb_lightgbm_Q700 | -111 / 769 / +0.19 | 789 / 1,970 / +0.05 [-0.14,+0.24] | 96 / 944 / -0.33 [-0.61,+0.03] |
| ALL7 | 1,991 / 4,485 / +0.30 | 5,398 / 10,703 / -0.02 [-0.21,+0.18] | 2,958 / 5,853 / -0.49 [-0.72,-0.16] |

HOLD 2025-07+ correlations are negative for all seven (seven-together -0.49, CI excludes 0) on 31 weeks; the full-window and WF correlations are about 0. With 7 setups x 4 windows tested this is suggestive, not established; it is the one place a hedge-like signal shows up and it should be re-read when the paper weeks accumulate.

## 3. Stack-add at 10/20/30% of stack risk (research series, FEES-standard costs)

Base stack: Sharpe 2.235 (weekly x sqrt52), maxDD $548,152, worst week $-339,821, worst-20-weeks $-3,303,356, 149 weeks.

| setup | % risk | NQ lots equiv. | marginal Sharpe | maxDD change $ | worst-20-weeks $ added | (of which covariance only) | worst week after $ | weekly corr(stack+add, stack) | weekly corr (MBO, stack) |
|---|---|---|---|---|---|---|---|---|---|
| H120000_cd_xgboost_Q725 | 10% | 2.02 | +0.051 | -2,810 | +6,809 | -22,614 | -330,564 | 0.995 | +0.095 |
| H120000_cd_xgboost_Q725 | 20% | 4.04 | +0.079 | -5,620 | +13,617 | -45,229 | -321,306 | 0.981 | +0.095 |
| H120000_cd_xgboost_Q725 | 30% | 6.06 | +0.087 | +22,760 | +20,426 | -67,843 | -318,175 | 0.960 | +0.095 |
| H250_tb_long_xgboost_Q750 | 10% | 1.87 | +0.035 | +681 | +50,879 | +32,993 | -342,291 | 0.995 | +0.021 |
| H250_tb_long_xgboost_Q750 | 20% | 3.74 | +0.047 | +1,362 | +101,758 | +65,985 | -344,760 | 0.981 | +0.021 |
| H250_tb_long_xgboost_Q750 | 30% | 5.61 | +0.039 | +2,043 | +152,636 | +98,978 | -347,229 | 0.958 | +0.021 |
| H300000_cd_extratrees_Q575 | 10% | 1.93 | +0.076 | -20,309 | +64,573 | +41,231 | -327,550 | 0.995 | -0.093 |
| H300000_cd_extratrees_Q575 | 20% | 3.86 | +0.130 | -40,617 | +129,145 | +82,461 | -315,280 | 0.980 | -0.093 |
| H300000_cd_extratrees_Q575 | 30% | 5.80 | +0.159 | -60,926 | +193,718 | +123,692 | -303,009 | 0.956 | -0.093 |
| H300000_cd_histgb_Q700 | 10% | 3.57 | +0.085 | -26,698 | +19,280 | -11,434 | -316,746 | 0.995 | -0.040 |
| H300000_cd_histgb_Q700 | 20% | 7.13 | +0.146 | -53,397 | +38,560 | -22,868 | -315,318 | 0.980 | -0.040 |
| H300000_cd_histgb_Q700 | 30% | 10.70 | +0.184 | -21,405 | +57,840 | -34,302 | -313,889 | 0.957 | -0.040 |
| H60000_cd_histgb_Q675 | 10% | 2.01 | +0.082 | -6,360 | +22,170 | -12,084 | -340,594 | 0.995 | +0.016 |
| H60000_cd_histgb_Q675 | 20% | 4.02 | +0.140 | -12,719 | +44,340 | -24,167 | -341,366 | 0.981 | +0.016 |
| H60000_cd_histgb_Q675 | 30% | 6.03 | +0.175 | -19,079 | +66,510 | -36,251 | -342,139 | 0.958 | +0.016 |
| H60000_yeb_catboost_Q625 | 10% | 1.91 | +0.075 | -11,305 | +33,617 | +3,945 | -333,950 | 0.995 | -0.008 |
| H60000_yeb_catboost_Q625 | 20% | 3.82 | +0.126 | -22,610 | +67,234 | +7,890 | -328,079 | 0.981 | -0.008 |
| H60000_yeb_catboost_Q625 | 30% | 5.74 | +0.154 | -33,915 | +100,851 | +11,836 | -322,207 | 0.958 | -0.008 |
| H60000_yeb_lightgbm_Q700 | 10% | 2.07 | +0.036 | -12,852 | +9,009 | -12,597 | -339,985 | 0.995 | +0.064 |
| H60000_yeb_lightgbm_Q700 | 20% | 4.13 | +0.049 | -25,704 | +18,018 | -25,194 | -340,150 | 0.981 | +0.064 |
| H60000_yeb_lightgbm_Q700 | 30% | 6.20 | +0.043 | -38,556 | +27,027 | -37,790 | -340,314 | 0.959 | +0.064 |
| ALL7 | 10% | 0.38 | +0.080 | -13,039 | +38,885 | +5,518 | -332,524 | 0.995 | +0.013 |
| ALL7 | 20% | 0.76 | +0.137 | -26,079 | +77,771 | +11,035 | -325,227 | 0.981 | +0.013 |
| ALL7 | 30% | 1.14 | +0.170 | -39,118 | +116,656 | +16,553 | -317,930 | 0.958 | +0.013 |

'Of which covariance only' = the same worst-20 sum after removing each setup's own weekly mean before scaling: the part that comes from being positive when the stack is bad, not from the setup's average edge. Marginal Sharpe rises for all seven mostly because the added mean is positive and the correlation is ~0; the in-sample-selected mean overstates the forward gain. WF-only marginal Sharpe at 20%: H120000_cd_xgboost_Q725 +0.077; H250_tb_long_xgboost_Q750 +0.024; H300000_cd_extratrees_Q575 +0.134; H300000_cd_histgb_Q700 +0.211; H60000_cd_histgb_Q675 +0.183; H60000_yeb_catboost_Q625 +0.171; H60000_yeb_lightgbm_Q700 +0.085; ALL7 +0.165.

## 4. P&L by hour / session and overlap with the stack

Entry hour (ET), all seven pooled (4,127 trades, 1 NQ each) vs stack trade entries (report scale; the stack's 'live' construction blocks entries 09:00-09:59 and has none after 15:00, so its zero hours are by rule):

| ET hour | MBO trades | MBO $ | stack entries | stack $ |
|---|---|---|---|---|
| 00 | 191 | 39,146 | 368 | 145,125 |
| 01 | 131 | 17,846 | 461 | 7,560 |
| 02 | 79 | 22,273 | 613 | 270,635 |
| 03 | 67 | -4,399 | 908 | 54,634 |
| 04 | 65 | -34,640 | 904 | 272,602 |
| 05 | 55 | 37,284 | 648 | -142,511 |
| 06 | 87 | 69,614 | 532 | 357,945 |
| 07 | 93 | 57,620 | 641 | 249,937 |
| 08 | 293 | 123,252 | 1111 | -95,230 |
| 09 | 527 | 3,569 | 0 | 0 |
| 10 | 325 | 130,012 | 2276 | 1,279,335 |
| 11 | 97 | 74,316 | 1478 | 433,300 |
| 12 | 100 | 79,731 | 1083 | 165,590 |
| 13 | 127 | 65,450 | 897 | 166,434 |
| 14 | 191 | -68,149 | 864 | 147,002 |
| 15 | 218 | -35,645 | 0 | 0 |
| 16 | 313 | -10,705 | 0 | 0 |
| 17 | 0 | 0 | 0 | 0 |
| 18 | 443 | 14,026 | 2095 | 562,000 |
| 19 | 202 | -1,313 | 1089 | 781,761 |
| 20 | 130 | 70,946 | 870 | 650,269 |
| 21 | 100 | 4,076 | 615 | 591,183 |
| 22 | 134 | 1,251 | 514 | -24,500 |
| 23 | 159 | -1,145 | 387 | -21,033 |

| session (entry) | MBO trades | MBO $ | stack entries | stack $ |
|---|---|---|---|---|
| Asia 18:00-02:00 | 1490 | 144,833 | 6399 | 2,692,365 |
| Europe 02:00-08:30 | 491 | 119,414 | 4638 | 1,102,556 |
| preUS 08:30-09:30 | 297 | 168,938 | 719 | -134,543 |
| RTH 09:30-16:00 | 1536 | 231,936 | 6598 | 2,191,661 |
| close 16:00-17:00 | 313 | -10,705 | 0 | 0 |

MBO trades are spread across the whole day (Asia 36%, Europe 12%, pre-US 7%, RTH 37%, 16:00-17:00 8% of trades); 26% of MBO entries (1,058 trades) fall in the 09:00-09:59 and 15:00-17:59 hours in which the live stack opens nothing (hour 09 alone: 527 MBO trades, +$3.6k). The 16:00-17:00 hour is the only session that loses (-$10.7k). The 14:00-15:59 entry hours lose (-$104k together over 3 years, 1 NQ each); the stack opens nothing after 15:00.

Stack state at the moment each MBO trade opens (net signed stack lots; flat means |net| < 0.5 lot):

| setup | stack flat: n / mean $ | same side: n / mean $ | opposite: n / mean $ |
|---|---|---|---|
| H120000_cd_xgboost_Q725 | 223.0 (68%) / 486 | 55.0 (17%) / 46 | 49.0 (15%) / -48 |
| H250_tb_long_xgboost_Q750 | 318.0 (69%) / 242 | 80.0 (17%) / 150 | 61.0 (13%) / -292 |
| H300000_cd_extratrees_Q575 | 446.0 (58%) / 93 | 143.0 (19%) / -95 | 180.0 (23%) / 345 |
| H300000_cd_histgb_Q700 | 124.0 (16%) / 5 | 368.0 (47%) / 118 | 290.0 (37%) / 69 |
| H60000_cd_histgb_Q675 | 88.0 (26%) / 1,238 | 97.0 (29%) / 52 | 150.0 (45%) / 87 |
| H60000_yeb_catboost_Q625 | 430.0 (42%) / 139 | 329.0 (32%) / 175 | 258.0 (25%) / -6 |
| H60000_yeb_lightgbm_Q700 | 243.0 (55%) / 328 | 110.0 (25%) / 205 | 85.0 (19%) / -287 |
| ALL7 | 1872.0 (45%) / 254 | 1182.0 (29%) / 110 | 1073.0 (26%) / 46 |

The MBO does not follow the stack: same-side and opposite-side entries are about equally common and neither state pays systematically. Two setups (H300000_cd_histgb_Q700, H60000_cd_histgb_Q675) trade mostly while the stack is in a position (84% and 74%); the other five enter while the stack is flat 42-69% of the time.

MBO trades exiting in the stack's 20 worst weeks: 445 trades, +$102,366 (1 NQ each); the other 129 weeks: 3682 trades, +$552,049.

## 5. Paper-soak series

**NEEDS (paper series not on this box).** The grep of the repo, MORNING.md, FORWARD*.md, `autopilot/forward/` (FORWARD_WEEKS/LOG, `series/PAPERALL_CELLS.json` = 229 cells, none an MBO setup), the paper_all rows, `LIVE_RECON.md` and `data/live` found no MBO paper trades: the MBO executor and its paper log live only on the execution server; earlier notes record the same ('MBO no data', 'MBO seven stays on the execution server', DS3_TA/DS3_CENSUS: not deliverable, L2-dependent). To finish section E with forward evidence, export from the execution server: (1) the per-setup paper trade log for the seven setups (one row per trade: variant id, side, entry/exit timestamps with timezone, fill prices or net $ per contract, lots, exit reason) from soak start to date; (2) the frozen-spec/config file listing the seven variant ids, hold and quantile thresholds and the contract size used, so the series can be tied to the names here; (3) the soak start date. Stack weekly series for the same weeks is available from the live files (`StratTrades_DS3_*`, `LIVE_RECON.md`); paper weeks are forward data and would be reported separately labelled paper evidence with n and MDE (at roughly 20 weeks of soak the MDE of one setup's weekly mean is about $3.5k-$5.5k per NQ and the correlation CI half-width about 0.4, so the soak can only reject a strongly positive correlation, not confirm a hedge).

## 6. Cost sensitivity and checks

MNQ-cost-x10 convention (-$22 per round trip instead of -$14.84): weekly means H120000_cd_xgboost_Q725 712; H250_tb_long_xgboost_Q750 456; H300000_cd_extratrees_Q575 567; H300000_cd_histgb_Q700 393; H60000_cd_histgb_Q675 836; H60000_yeb_catboost_Q625 727; H60000_yeb_lightgbm_Q700 502; ALL7 4,194. Correlations move by < 0.002; worst-20 sums: seven-together 99,180 vs 102,366. Best 20%-risk worst-20 $ on that basis: 127,033.

Checks: (a) stack trade rows re-summed to the daily stack series within $420 over 7.36M (rounding of the engine's day booking), cleaned-vs-raw weights identical from 2023-04; (b) all MBO exit days exist as stack label days (no dropped P&L); (c) 99.9% of file `trading_day_et` equals the recomputed exit label day; (d) the null for worst-20 mean is a 5,000-draw circular week shift of the MBO weekly series against the stack (random shift 5..n-5 weeks), which keeps the MBO's own mean and autocorrelation.

## 7. Disclosures and caveats

- The seven setups were chosen on 2023-02..2024-01; the 2023-04..2024-01 weeks are in-sample for them (n=44 of 149). WF/HOLD are the honest parts. The series is a frozen-replay reconstruction with modelled slippage (entry/exit prices carry the slipped fills), not live fills; 'no H2/paper' remains the main limitation (EXEC_SUMMARY).
- Stack-add risk uses full-window weekly SD; MBO SD matching assumes the MBO risk is its weekly SD, not its worst week (the MBO seven together had worst week -$136k at 7 NQ in D1 F5).
- 'Best of seven' for the single number is selected on the outcome; the pooled seven-together line is the unselected alternative.
- Bug check: first run of e1_audit.py failed (`sd.stack` collides with a DataFrame method); fixed by indexing `sd['stack']` before any result was produced. No other bugs found. The garbage pre-2023-04 stack weights were excluded, not used.
- Fees: FEES.md NQ standard; NQ exchange/NFA part is a PROXY per FEES.md flag 1.
