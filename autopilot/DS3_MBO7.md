# DS3_MBO7 - THE MBO SEVEN AS A THIRD LEG (T-INSTR-2 section 3; ZL-1, 2026-11-05). Research only. No PASS claim. Descriptive measurement of an existing file; nothing live.
**Plain sentence: the 3-year reconstructed trade file of the MBO seven IS on this box (outputs/h2/NQ7_3Y_TRADES_RECONSTRUCTED.parquet, 4,314 trades, 2023-02-09..2026-02-06); scored against the live Q1-A ts2 stack the seven are uncorrelated with it (daily correlation -0.04, weekly -0.02; -0.25 weekly with the SM book at worst) but strongly correlated with each other (weekly 0.20-0.80), so the leg is a real diversifier by correlation yet a very drawdown-heavy one on its own (maxDD $229k at one NQ-equivalent per setup vs a stack maxDD of $88k over the same 149 weeks); added to the stack at about one third of that size (k 0.33, ~2.3 NQ-equivalents in total) it keeps the stack maxDD unchanged, lifts the stack mean by about $1.4k a week (+13%) and the Calmar from 0.121 to 0.137, while the worst-20 weeks get $7k worse; at full size the stack maxDD doubles. The file ends 2026-02-06, so there is no window overlapping the last six months of the stack and no H2 test; what is missing is any LIVE MNQ fill record (the request to the user narrows to: live MNQ fills after 2026-02-06, if any).**
Scope note l2vast/ds3/prereg/MBO7_scope.md (sha256 in DECISIONS.md); code l2vast/ds3/code/instr2/mbo7_score.py (synthetic self-test: `--synthetic`, passes: known correlated pair 0.92, known +$40 drift recovered 39.8, zero-correlation setup vs stack 0.01); output /mnt/l2/l2vast/ds3_mbo7/ (mbo7_score_nq.pkl, mbo7_score_mnq.pkl).
## 1. Data and provenance (the search)
Search of the box: /opt/trading and any Stage6 journal are absent, but outputs/h2/ holds the reconstruction the directive thought missing: `NQ7_3Y_TRADES_RECONSTRUCTED.parquet/.csv` (4,314 rows), regenerated on 2026-09-16 from the frozen Stage-6 per-day model scores (777 days) and the NQ BBO tape (4.9e9 events) with the frozen replay code path (25 ms latency, 1 tick slippage per fill, $4.50 RT, PV 20; MNQ replay with $0.60/side commission, PV 2). `NQ7_3Y_VERIFICATION.csv`: trade count, net and PF match outputs/stage6_nq230/NQ230_3Y_RESULTS.csv exactly for all seven (814/341/483/810/342/1072/452). All seven are time-managed (hold 1-6 h, 16:59 ET cap; cap exits net negative for 6 of 7). Earlier consumers: d1/REPORT_D1_F5.md (MBO vs the old ST/HM pair), t3/INVENTORY.md, MECHANISM_INDEX T3S1_MBO. Columns used: variant_id, side, entry_event_ts_ns, exit_event_ts_ns, net_usd_mnq (net $ of ONE MNQ). Columns a live journal must supply to be scored the same way: setup id, side, entry and exit timestamps (UTC ns), net $ per MNQ after fees. P&L is booked on the exit label day; 187 of the 4,314 trades exit before 2023-04-03 and fall outside the stack days (kept in the setup tables, dropped from stack work).
Sizing: all tables below at **1 NQ-equivalent per setup** (net_usd_mnq x 10, MNQ-equivalent costs, the D1 convention; seven contracts when all seven are on); the live size (1 MNQ per setup) is exactly one tenth of every dollar figure (file mbo7_score_mnq.pkl). Stack = Q1-A ts2 (stack_q1a_ts2.npz, V0 = engine as run; the V2 live-window variant is not applied here), overlap 2023-04-03..2026-02-06 = 149 weeks.
## 2. Per setup, recents first (weekly mean $ at 1 NQ-equivalent; windows counted back from the file end 2026-02-06; maxDD, Calmar = weekly mean / maxDD, worst-20 weeks sum over ALL)
| setup | n | $/trade | E1M | E2M | E3M | E6M | E12M | 2025 | 2024 | 2023 | ALL $/wk | maxDD | Calmar | worst-20 wk |
|--|--|--|--|--|--|--|--|--|--|--|--|--|--|--|
| ALL SEVEN | 7 setups | - | 3558 | 2335 | 5370 | 2864 | 6643 | 7088 | 2930 | 1574 | 4194 | 229355 | 0.018 | -678208 |
| H120000_cd_xgboost_Q725 | 341 | 293 | -143 | -72 | -523 | 267 | 1248 | 1356 | 278 | 333 | 712 | 32090 | 0.022 | -146753 |
| H250_tb_long_xgboost_Q750 | 483 | 141 | 1309 | 1455 | 1626 | 1050 | 836 | 515 | 333 | 532 | 456 | 109048 | 0.004 | -182316 |
| H300000_cd_extratrees_Q575 | 810 | 109 | 3440 | 1519 | 4347 | 2363 | 1360 | 1329 | -297 | 586 | 567 | 82125 | 0.007 | -203310 |
| H300000_cd_histgb_Q700 | 814 | 76 | 0 | -20 | 99 | -67 | 425 | 487 | 645 | -82 | 393 | 25681 | 0.015 | -99550 |
| H60000_cd_histgb_Q675 | 342 | 352 | -341 | 198 | 264 | -269 | 1597 | 1781 | 313 | 130 | 836 | 17843 | 0.047 | -75914 |
| H60000_yeb_catboost_Q625 | 1072 | 110 | -880 | -833 | -977 | -519 | 146 | 351 | 1627 | 87 | 727 | 72335 | 0.010 | -196297 |
| H60000_yeb_lightgbm_Q700 | 452 | 161 | 174 | 87 | 536 | 38 | 1029 | 1268 | 32 | -11 | 502 | 45252 | 0.011 | -134669 |
Reading: the seven are not equally alive recently. In the last 13 weeks of the file (E3M) the extratrees Q575 (+3,440/wk), tb_long xgboost (+1,309) and the combined seven (+3,558) carry it; catboost Q625 is negative in every recent window (-880 E1M, -977 E3M); histgb Q700 earns about zero; xgboost Q725 and histgb Q675 are negative in E1M-E3M but positive over 12 months. Calmar by setup (weekly mean / maxDD): histgb Q675 0.047 is the best, tb_long xgboost 0.004 and extratrees 0.007 the worst because of $109k and $82k drawdowns.
## 3. Per setup x session (entry clock ET; sessions with >= 10 trades; weekly mean $ at 1 NQ-equivalent; E3M/E6M zeros = no trades in the window)
| setup | session | n | $/trade | E3M | E6M | E12M | ALL $/wk |
|--|--|--|--|--|--|--|--|
| H120000_cd_xgboost_Q725 | asia | 51 | 430 | 0 | 28 | 363 | 147 |
| H120000_cd_xgboost_Q725 | close | 45 | -395 | 0 | -53 | -265 | -146 |
| H120000_cd_xgboost_Q725 | london | 20 | -24 | 0 | 0 | -281 | -3 |
| H120000_cd_xgboost_Q725 | nyam | 133 | 25 | 0 | 457 | 382 | 76 |
| H120000_cd_xgboost_Q725 | nypm | 49 | 61 | -523 | -262 | 430 | 42 |
| H120000_cd_xgboost_Q725 | pre | 43 | 2091 | 0 | 97 | 619 | 596 |
| H250_tb_long_xgboost_Q750 | asia | 26 | 638 | 369 | 320 | 213 | 91 |
| H250_tb_long_xgboost_Q750 | close | 119 | -127 | -388 | -251 | -398 | -89 |
| H250_tb_long_xgboost_Q750 | london | 17 | 209 | -539 | -164 | -14 | 24 |
| H250_tb_long_xgboost_Q750 | nyam | 164 | 30 | 1117 | 469 | 11 | 26 |
| H250_tb_long_xgboost_Q750 | nypm | 96 | 497 | 455 | 615 | 1060 | 326 |
| H250_tb_long_xgboost_Q750 | pre | 61 | 170 | 611 | 61 | -36 | 79 |
| H300000_cd_extratrees_Q575 | asia | 152 | 102 | -199 | -164 | -16 | 96 |
| H300000_cd_extratrees_Q575 | close | 81 | -28 | 340 | -49 | -281 | 3 |
| H300000_cd_extratrees_Q575 | london | 90 | -41 | 425 | 230 | -260 | -10 |
| H300000_cd_extratrees_Q575 | nyam | 287 | 196 | 3546 | 1962 | 1717 | 423 |
| H300000_cd_extratrees_Q575 | nypm | 123 | 148 | 236 | 360 | 631 | 97 |
| H300000_cd_extratrees_Q575 | pre | 77 | 55 | 0 | 23 | -430 | -42 |
| H300000_cd_histgb_Q700 | asia | 535 | -1 | 99 | -139 | -30 | 14 |
| H300000_cd_histgb_Q700 | close | 102 | 5 | 0 | 6 | 74 | 3 |
| H300000_cd_histgb_Q700 | london | 123 | 261 | 0 | 66 | 156 | 227 |
| H300000_cd_histgb_Q700 | nyam | 14 | -621 | 0 | -0 | -93 | -58 |
| H300000_cd_histgb_Q700 | nypm | 14 | -41 | 0 | 0 | 17 | -4 |
| H300000_cd_histgb_Q700 | pre | 16 | 2452 | 0 | 0 | 302 | 213 |
| H60000_cd_histgb_Q675 | asia | 225 | 90 | 50 | -345 | 380 | 124 |
| H60000_cd_histgb_Q675 | close | 24 | -364 | 0 | 4 | -125 | -41 |
| H60000_cd_histgb_Q675 | london | 27 | 584 | 216 | 75 | -142 | 106 |
| H60000_cd_histgb_Q675 | nyam | 33 | 2176 | 0 | 0 | 1043 | 471 |
| H60000_cd_histgb_Q675 | nypm | 21 | -732 | -3 | -3 | 126 | -70 |
| H60000_cd_histgb_Q675 | pre | 10 | 3680 | 0 | 0 | 315 | 247 |
| H60000_yeb_catboost_Q625 | asia | 389 | 59 | -513 | -196 | 172 | 144 |
| H60000_yeb_catboost_Q625 | close | 116 | -26 | 0 | -109 | -213 | -36 |
| H60000_yeb_catboost_Q625 | london | 175 | 199 | 189 | 115 | -139 | 273 |
| H60000_yeb_catboost_Q625 | nyam | 207 | 170 | 0 | 0 | 64 | 199 |
| H60000_yeb_catboost_Q625 | nypm | 95 | 63 | -609 | -305 | 430 | 54 |
| H60000_yeb_catboost_Q625 | pre | 83 | 273 | -44 | -22 | -166 | 93 |
| H60000_yeb_lightgbm_Q700 | asia | 162 | 268 | -136 | -74 | 371 | 283 |
| H60000_yeb_lightgbm_Q700 | close | 52 | -73 | -295 | -308 | -365 | -28 |
| H60000_yeb_lightgbm_Q700 | london | 56 | 429 | 368 | 155 | 290 | 161 |
| H60000_yeb_lightgbm_Q700 | nyam | 104 | 153 | 341 | 117 | 65 | 99 |
| H60000_yeb_lightgbm_Q700 | nypm | 44 | 13 | 258 | 148 | 948 | 52 |
| H60000_yeb_lightgbm_Q700 | pre | 32 | -241 | 0 | 0 | -284 | -67 |
Pattern: the NY-AM entries of extratrees Q575 (287 trades, +423 $/wk all-period, +3,546 in E6M) and the NY-PM entries of tb_long xgboost (+326) are the steady earners; the close session (15:00-16:54 ET entries) is negative for five of seven setups (cap-exit losers); pre-market (08:30-09:29) entries have large $/trade (up to $3,680) on few trades (10-83).
## 4. Correlation with the six NQ books and the stack (overlap days/weeks; books = cube of the Q1-A ts2 stack summed over sessions: KB PE SM HM MV PB)
| series | stack daily | stack weekly | KB d/w | PE d/w | SM d/w | HM d/w | MV d/w | PB d/w |
|--|--|--|--|--|--|--|--|--|
| ALL SEVEN | -0.04 | -0.02 | 0.01 / 0.03 | -0.05 / 0.04 | -0.04 / -0.25 | 0.03 / 0.06 | -0.03 / -0.16 | -0.06 / 0.05 |
| H120000_cd_xgboost_Q725 | -0.02 | 0.00 | 0.01 / 0.02 | -0.02 / 0.05 | -0.02 / -0.19 | 0.02 / 0.07 | -0.03 / -0.14 | -0.04 / 0.07 |
| H250_tb_long_xgboost_Q750 | -0.03 | 0.02 | 0.05 / 0.12 | -0.05 / 0.07 | -0.04 / -0.24 | 0.05 / 0.08 | -0.03 / -0.21 | -0.04 / 0.07 |
| H300000_cd_extratrees_Q575 | -0.09 | -0.04 | -0.08 / -0.08 | -0.07 / 0.01 | -0.05 / -0.20 | -0.03 / 0.17 | -0.06 / -0.16 | -0.10 / 0.03 |
| H300000_cd_histgb_Q700 | -0.02 | -0.11 | 0.05 / 0.02 | -0.02 / -0.03 | -0.05 / -0.27 | -0.04 / -0.11 | -0.01 / -0.08 | 0.04 / 0.06 |
| H60000_cd_histgb_Q675 | -0.03 | -0.09 | 0.03 / -0.02 | -0.04 / -0.00 | -0.04 / -0.25 | 0.04 / 0.03 | -0.09 / -0.22 | -0.06 / -0.03 |
| H60000_yeb_catboost_Q625 | 0.02 | 0.04 | 0.03 / 0.05 | -0.00 / 0.07 | 0.02 / -0.12 | 0.05 / -0.05 | 0.06 / 0.10 | -0.03 / 0.02 |
| H60000_yeb_lightgbm_Q700 | -0.04 | 0.01 | -0.02 / 0.06 | -0.04 / 0.04 | -0.04 / -0.15 | 0.04 / 0.09 | -0.00 / -0.14 | -0.06 / 0.07 |

Setup-to-setup weekly correlation:

| | H120000_cd_xgboost | H250_tb_long_xgboo | H300000_cd_extratr | H300000_cd_histgb_ | H60000_cd_histgb_Q | H60000_yeb_catboos | H60000_yeb_lightgb |
|--|--|--|--|--|--|--|--|
| H120000_cd_xgboost | 1.00 | 0.68 | 0.59 | 0.35 | 0.77 | 0.59 | 0.77 |
| H250_tb_long_xgboo | 0.68 | 1.00 | 0.63 | 0.28 | 0.64 | 0.51 | 0.75 |
| H300000_cd_extratr | 0.59 | 0.63 | 1.00 | 0.20 | 0.47 | 0.53 | 0.63 |
| H300000_cd_histgb_ | 0.35 | 0.28 | 0.20 | 1.00 | 0.41 | 0.22 | 0.27 |
| H60000_cd_histgb_Q | 0.77 | 0.64 | 0.47 | 0.41 | 1.00 | 0.38 | 0.80 |
| H60000_yeb_catboos | 0.59 | 0.51 | 0.53 | 0.22 | 0.38 | 1.00 | 0.58 |
| H60000_yeb_lightgb | 0.77 | 0.75 | 0.63 | 0.27 | 0.80 | 0.58 | 1.00 |

The seven are one family: weekly 0.20-0.80 among themselves (histgb Q700 the most independent, 0.20-0.41; xgboost Q725, histgb Q675 and lightgbm Q700 are 0.77-0.80 pairs), max 7 trades open at once (time-weighted mean 0.64 open). Against the stack they are uncorrelated (|r| <= 0.17 daily and weekly for every setup and book except SM, which is -0.12 to -0.27 weekly): a negative weekly correlation with SM (the stack book that earns on trend days) is the diversification.
## 5. Equal-risk stack with the seven added (149 overlap weeks; stack alone: mean $10,664/wk, maxDD $88,180, worst-20 weeks -$741k, Calmar 0.121)
| k (x 1 NQ-equivalent per setup) | stack mean $/wk | maxDD $ | worst-20 wk $ | Calmar | d Calmar | d maxDD $ | MBO alone mean / maxDD |
|--|--|--|--|--|--|--|--|
| 0.05 | 10874 | 85005 | -739585 | 0.128 | +0.007 | -3175 | 210 / 11468 |
| 0.10 | 11084 | 82528 | -737932 | 0.134 | +0.013 | -5652 | 419 / 22936 |
| 0.25 | 11713 | 85117 | -740068 | 0.138 | +0.017 | -3064 | 1048 / 57339 |
| 0.50 | 12761 | 96846 | -791709 | 0.132 | +0.011 | +8666 | 2097 / 114678 |
| 1.00 | 14858 | 197113 | -946888 | 0.075 | -0.046 | +108932 | 4194 / 229355 |

Equal risk (largest scale whose stack maxDD does not exceed the stack's own): k = 0.33 (about 2.3 NQ-equivalents in total) -> stack mean +$1392/wk (13%), Calmar 0.137 (+0.016), worst-20 weeks -748591. At k = 0.5 the stack maxDD is +$8.7k, at k = 1.0 +$108.9k (the leg's own drawdown dominates). Whole-leg alone: mean $4,194/wk, maxDD $229k, worst-20 weeks -$678k, i.e. weekly mean/maxDD 0.018 vs the stack 0.121.
## 6. Caveats and what is not answered
(1) The file is RECONSTRUCTED (frozen scores + BBO tape, 25 ms latency, 1-tick slippage), not live Rithmic fills; MNQ execution through the Rithmic server may differ in slippage and rejects. (2) It ends 2026-02-06: no overlap with the stack's L1M..L6M or the 2026 regime (the stack's HOLD/MID are partly after the file), so "recents" here means the last weeks before 2026-02-06; there is no out-of-sample after the freeze date and no H2. (3) Stack = V0 (engine as run); the V2 live-window question is open and would change the stack side, not the MBO side. (4) Setups, thresholds and scores are frozen Stage-6 products selected on earlier data; their 3-year holdout is the file; the seven are correlated and were not family-tested here (descriptive). (5) At one MNQ per setup the leg is $419/wk on 149 weeks (maxDD $22.9k), small beside the stack; the numbers above scale linearly. (6) What would settle it: any live MNQ fill journal after 2026-02-06 (setup id, side, entry/exit UTC, net $ per MNQ) -> `python3 -I mbo7_score.py --file <csv>` produces these tables in minutes.

## ADDENDUM 1 (ZL-1, 2026-11-05): provenance of the frozen scores, post-cutoff windows, V0 and V2 stack side, sleeve placebos, walk-forward
**Provenance of the Stage-6 scores (stated BEFORE reading any window; what the box documents).** The fit/training period of the seven setups is NOT recorded anywhere on this box: /mnt/mbo/mbo4x_v2 (the pipeline tree with scores, bbo_memmap and NQ230_3Y_RESULTS.csv) is not mounted, h2/README.md calls the file "the seven frozen NQ Stage-6 setups on the 3Y holdout" (scores per day 2023-02-09..2026-02-06, 777 days), the sister evaluations say "post-freeze NQ is never touched" (freeze = 2026-02-06 = the file end) and ststrat_eval fixes DISCOVERY 2023-02-09..2025-02-08 / CONFIRM 2025-02-09..2026-02-06 for ST (a different strategy). The names (stage6_nq230, NQ230_3Y_RESULTS, variants H<hold>_<model>_Q<quantile>) say the seven are a selection from a larger variant set (about 230) evaluated on the same 3Y window; whether that selection used the 3Y results (best-of-230 in-sample) or an earlier fit is not documented. **Reading taken (conservative): the cutoff is unknown, so the whole file is treated as possibly selection-contaminated; the evidence I weigh is (a) the later, shorter windows below as post-cutoff candidates (since 2025-02-09 and, stricter, since 2025-05-13 = the end of the host MBO coverage) and (b) the placebo/family block; the question to the user (fit period, selection set, whether the seven were chosen on the 3Y results) is in MORNING_FLAGS.md and does not stop work.**
### A. Windows after candidate cutoffs (weekly $ at 1 NQ-equivalent per setup; SEVEN = all seven; maxDD, Calmar = mean/maxDD, share of positive weeks)
| window | weeks | SEVEN $/wk | maxDD | Calmar | % weeks > 0 | per setup $/wk: H120000_cd_xgboost_Q / H250_tb_long_xgboost / H300000_cd_extratree / H300000_cd_histgb_Q7 / H60000_cd_histgb_Q67 / H60000_yeb_catboost_ / H60000_yeb_lightgbm_ |
|--|--|--|--|--|--|--|
| since 2025-02-09 (STStrat CONFIRM block, last 12m) | 52 | 6643 | 229355 | 0.029 | 62% | 1248 / 836 / 1360 / 425 / 1597 / 146 / 1029 |
| since 2025-05-13 (end of the host MBO coverage; strict) | 39 | 4431 | 44324 | 0.100 | 67% | 262 / 1107 / 2246 / -64 / -297 / 692 / 485 |
| before 2025-02-09 (DISCOVERY-style block) | 97 | 2881 | 94312 | 0.031 | 61% | 425 / 252 / 142 / 376 / 428 / 1038 / 219 |
| ALL overlap 2023-04-03..2026-02-06 | 149 | 4194 | 229355 | 0.018 | 61% | 712 / 456 / 567 / 393 / 836 / 727 / 502 |
Reading: the later windows are not weaker: +$6.6k/wk over the last 12 months of the file and +$4.4k/wk since 2025-05-13 (maxDD $44k) against +$2.9k/wk in the first 22 months; histgb Q675 (+1,597/wk) and xgboost Q725 (+1,248) lead the last 12 months, but since 2025-05-13 histgb Q675 is -297 and histgb Q700 -64: the per-setup leaders change with the window (same pattern as the E-windows in section 2). No window after 2026-02-06 exists.
### B. Stack side on V0 (engine as run) and V2 (live windows 09:30-09:59 + 18:00-18:04 blocked; out/dis_ba bj_out W3)
**V0**: correlation of the seven (summed) with the stack daily -0.038, weekly -0.020; equal-risk k* (largest scale keeping the stack maxDD over the 149 overlap weeks) = 0.33 x 1 NQ-equivalent per setup.
| window (inside the file) | stack alone: mean $/wk / maxDD / Calmar | d Calmar / d maxDD $ at k = 0.10 | 0.25 | 0.33 | 0.50 | 0.75 | 1.00 |
|--|--|--|--|--|--|--|--|
| X' 2023-04..2024-01 | 3293 / 80802 / 0.041 | +0.001 / +1726 | +0.002 / +4314 | +0.002 / +5695 | +0.003 / +8629 | +0.005 / +12944 | +0.006 / +17258 |
| PRE 2024-02..2025-06 | 13202 / 88180 / 0.150 | +0.019 / -6351 | +0.028 / -4825 | +0.025 / -508 | +0.020 / +8666 | -0.021 / +51593 | -0.050 / +108932 |
| HOLD-trunc 2025-11..2026-02-06 | 17389 / 62322 / 0.279 | +0.010 / -454 | +0.027 / -1136 | +0.035 / -1499 | +0.054 / -2271 | +0.083 / -3406 | +0.112 / -4542 |
| ALL 2023-04..2026-02-06 | 10664 / 88180 / 0.121 | +0.013 / -5652 | +0.017 / -3064 | +0.016 / -508 | +0.011 / +8666 | -0.022 / +51593 | -0.046 / +108932 |
**V2**: correlation of the seven (summed) with the stack daily -0.045, weekly -0.050; equal-risk k* (largest scale keeping the stack maxDD over the 149 overlap weeks) = 0.52 x 1 NQ-equivalent per setup.
| window (inside the file) | stack alone: mean $/wk / maxDD / Calmar | d Calmar / d maxDD $ at k = 0.10 | 0.25 | 0.33 | 0.50 | 0.75 | 1.00 |
|--|--|--|--|--|--|--|--|
| X' 2023-04..2024-01 | 3681 / 77536 / 0.047 | +0.004 / -3072 | +0.005 / -1387 | +0.006 / -273 | +0.007 / +2093 | +0.008 / +5573 | +0.010 / +9053 |
| PRE 2024-02..2025-06 | 11320 / 93974 / 0.120 | +0.016 / -6351 | +0.044 / -15598 | +0.042 / -11281 | +0.037 / -2107 | +0.018 / +22684 | -0.019 / +80023 |
| HOLD-trunc 2025-11..2026-02-06 | 17826 / 55221 / 0.323 | +0.012 / -454 | +0.031 / -1136 | +0.041 / -1499 | +0.063 / -2271 | +0.097 / -3406 | +0.132 / -4542 |
| ALL 2023-04..2026-02-06 | 9941 / 93974 / 0.106 | +0.012 / -6351 | +0.034 / -15598 | +0.031 / -11281 | +0.025 / -2107 | +0.006 / +22684 | -0.025 / +80023 |
The leg helps in every window inside the file for k up to 0.5 on V2 and up to 0.33 on V0 (V0 PRE: Calmar +0.025 at k 0.33 but maxDD turns up at 0.5 and the Calmar goes negative at 0.75; the HOLD-truncated window 2025-11..2026-02-06 improves monotonically up to k = 1 because the leg earned most there); X' (2023-04..2024-01) is neutral. HOLD/MID/L-windows of the stack after 2026-02-06 cannot be scored (file ends).
### C. Sleeve placebos (300 worlds; P&L approximated on 1-minute closes for real and placebo alike: side x (close at exit minute - close at entry minute) x $2 - $2.2 per MNQ; correlation of the approximation with the file's exact net_usd_mnq = 0.992)
| placebo | sleeve p (mean $/trade of the seven) | family p per setup (max over the 7 setups): H120000_cd_xgboost_Q / H250_tb_long_xgboost / H300000_cd_extratree / H300000_cd_histgb_Q7 / H60000_cd_histgb_Q67 / H60000_yeb_catboost_ / H60000_yeb_lightgbm_ |
|--|--|--|
| random side per trade | 0.003 | 0.17 / 0.63 / 0.63 / 0.76 / 0.06 / 0.63 / 0.50 |
| shift5 forward-only (both times delayed 1-5 minutes, same hold) | 0.066 | 1.00 / 1.00 / 1.00 / 1.00 / 0.10 / 1.00 / 1.00 |
| shuffled day (same time of day and weekday, same hold) | 0.003 | 0.04 / 0.46 / 0.46 / 0.70 / 0.01 / 0.45 / 0.21 |
Reading: as a SLEEVE the seven beat the random-side and shuffled-day placebos (p 0.003 both) and sit at p 0.066 against shift5, which is expected for 1-6 hour holds (a 1-5 minute forward delay barely changes a multi-hour position), so shift5 does not discriminate here. Family-adjusted per setup (7 setups): only H60000 histgb Q675 clears (random side 0.06, shuffled day 0.01); xgboost Q725 reaches 0.04 on shuffled days but 0.17 on random side; the other five are not separable from placebo individually (family p 0.21-0.76 on days/side). The sleeve is therefore carried by two or three setups, the rest are consistent with zero edge after selection among seven.
### D. Purged walk-forward of the setup choice (trailing 12 months, next month; 25 months from 2024-02, mean 5.8 setups selected)
Selected-setups P&L 4028 $ per week vs all seven 5237 $ per week (no selector beats holding all seven); random choices of the same sizes reach the selector's total in 37% of 2,000 draws (p 0.37): the selector has no value and the leg should be taken as the fixed set (or as the two/three setups of section C with a selection charge).
**Plain sentence (addendum): the provenance of the scores cannot be established from the box, so the file is treated as possibly selected; read that way, the seven as a sleeve still beat random-side and shuffled-day placebos (p 0.003), the later windows are not weaker, they stay uncorrelated with the stack on V0 and V2 (-0.04/-0.05 weekly) and add Calmar up to k = 0.33 (V0) / 0.52 (V2) of one NQ-equivalent per setup with the stack maxDD unchanged or lower, but the individual evidence rests on 2-3 setups, no setup-selector works, and nothing after 2026-02-06 exists.**
