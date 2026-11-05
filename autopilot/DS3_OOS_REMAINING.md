# DS3_OOS_REMAINING - pre-2023 out-of-sample of the remaining watch lines (DIS-BM), and the one-table verdict list (ZL-1, 2026-11-05). Research only. No PASS claim, nothing bought.
**Plain sentence: before 2023 none of the remaining 2026 watch lines earned anything in out-of-sample 1-minute NQ data (Z1 swing failed break -6.0 pt per trade, G1 NQ-ES ratio -3.1 with t -6.4, DIS-Q 15:00 imbalance fade -1.8, DIS-Q 15:50 drift fade -2.4), and re-running the ten DIS-W lines with every fixed-point rule converted to a percent rule changes no verdict (Q13 -1.0, DIS-B -1.5, DIS-C -4.7; DIS-K flips to -0.25; OR15 rises to +1.1 but its one-minute-shift placebo matches it), so the 2026 watch list is a 2026-regime list: its member lines are REGIME-ONLY or NULL, none REPLICATES.**
Prereg l2vast/ds3/prereg/DISBM_prereg.md sha256 49997bf430c25280756e4c04dbf7695d5a0249c4051369d98bfc2f3f1737f5f1 (DECISIONS.md; frozen code and data hashes inside; logged before any outcome of the new lines or of the percent frame). Protocol = DIS-W (DS3_HISTORY_EXTENSION.md): owned NQ.v.0 1-minute 2013-01-02..2026-10-16, 110 roll days dropped, 1-minute live fill model, OOS = label days <= 2023-04-02. Code l2vast/ds3/code/dw/ (bm_pctfeed.py, bm_signals.py, bm_eval_lib.py, bm_calib.py, bm_oos.py, bm/ = copies of fade_mz events.py, events_v2.py, disg_sig.py that differ from the originals only in loading the feed from BM_FEED and skipping the ROUND-level offsets); data /mnt/l2/l2vast/ds3_dbm/. n_tested FADE_DISBM 28; ledger DIS_BM 28 rows. Placebos (100 worlds each, all causal): P1 random side, shift5 (entry delayed 1-5 minutes), delayed entry 5-120 minutes, P3 random day of the same weekday; family max-T over 14 lines (P1 and P3 worlds); Benjamini-Hochberg q on the largest of the four placebo p.

## 1. Definitions (from the code) and calibration before looking at 2013-2023
Z1_SWING: fade_mz events_v2 v2a, nyam, X=15, N=3, stop ext +- 0.5 Wilder ATR, 1R, T60, lots clip(1200/(dist*20), 0.25, 2). G1_NQES: disg_sig.g1 L=60, k=3.0, cooldown 30 bars, NY-AM, fade NQ, 1.5 ATR stop, 2R, T120 (ES 1-minute owned). DISQ_1500_IMB / DISQ_1550_DRIFT: disq.build('15:00','IMB','fade','ALL','60/60') and ('15:50','DRIFT',...), T60, 2 lots; the research IMB is already the 1-minute volume-sign proxy (volume x sign(close - open) over the 10 minutes before 15:00), so no extra proxy is introduced. Calibration (RAW frame, 2023-04..2026-10, 1-minute pipeline vs the 1-s harness on the research lists):
| line | research signals / 1-min feed signals (2023-04..2026-10) | per-trade corr | weekly corr | mean pt per trade 1-s harness / 1-min |
|--|--|--|--|--|
| Z1_SWING | 692 / 661 (659 common) | 0.952 | 0.925 | +0.96 / +1.69 |
| G1_NQES | 1030 / 1000 (1000 common) | 0.960 | 0.907 | +1.33 / +0.85 |
| DISQ_1500_IMB | 881 / 855 (855 common) | 0.970 | 0.943 | +2.80 / +2.54 |
| DISQ_1550_DRIFT | 891 / 854 (843 common) | 0.858 | 0.832 | -0.97 / +0.12 |
Rule fixed in the prereg: weekly correlation below 0.90 gets no formal verdict: DISQ_1550_DRIFT 0.83 (and, from DIS-W, DIS-K 0.83, VB2 NYPM T1 0.80, VB2 NYAM T3 0.89, VWAPF 0.875).

## 2. The percent frame
RAW = fixed-point rules as built (as DIS-W). PCT = prices multiplied per roll segment by 20620 / median close, so brackets, X, thresholds and floors scale with price while costs stay at their 2023-26 point values (DIS-Y / DIS-AA convention; before 2023 NQ traded at 3,000-10,000, so a fixed 60-point bracket was 3-10 times wider in percent than in 2026). PCT is the primary frame; RAW is the object as built. Z1 swing and DIS-K change most between frames (the 15-point X and the 60/60 bracket).

## 3. Results, 14 lines, OOS 2013-01..2023-04-02 (1 lot except where the line has its own lots; stop-first fills; weekly-cluster t in brackets)
| line | calib. weekly corr | n OOS raw / pct | OOS mean pt per lot-trade RAW (t) | PCT (t) | years positive RAW / PCT | IS mean RAW / PCT | placebo p PCT P1 / shift5 / delay5-120 / P3 | p_maxT PCT | q_BH PCT | verdict (PCT, primary) |
|--|--|--|--|--|--|--|--|--|--|--|
| Q13GAP_T1 | 0.908 | 496 / 696 | -2.10 (-1.4) | -0.98 (-0.7) | 4/10 / 5/11 | +2.90 / +1.40 | 0.56 / 0.02 / 0.26 / 0.30 | 1.00 | 1.00 | NEGATIVE: REGIME-ONLY |
| DISK_BO_CH | 0.826 | 748 / 753 | +0.55 (0.5) | -0.25 (-0.2) | 4/11 / 5/11 | +4.84 / +2.63 | 0.19 / 0.53 / 0.51 / 0.31 | 0.86 | 1.00 | no formal verdict (calibration 0.83) |
| DISB_PREL | 0.926 | 820 / 820 | -1.34 (-2.5) | -1.49 (-2.0) | 2/11 / 2/11 | +0.91 / +0.81 | 0.48 / 0.49 / 0.49 / 0.55 | 1.00 | 1.00 | NEGATIVE: REGIME-ONLY |
| DISC_SUN30 | 0.968 | 346 / 346 | -3.62 (-4.6) | -4.71 (-4.4) | 1/8 / 1/8 | +2.71 / +2.10 | 0.97 / 1.00 / 1.00 / 1.00 | 1.00 | 1.00 | NEGATIVE: REGIME-ONLY |
| VB2NYPM_T1 | 0.795 | 602 / 1101 | -0.95 (-1.3) | -0.82 (-1.5) | 3/7 / 4/11 | +1.22 / +1.06 | 0.31 / 0.01 / 0.28 / 0.23 | 0.99 | 1.00 | no formal verdict (calibration 0.80) |
| PDASIA_T2 | 0.970 | 561 / 809 | -0.31 (-0.6) | -0.59 (-1.1) | 2/9 / 3/11 | +2.39 / +1.64 | 0.24 / 0.02 / 0.24 / 0.04 | 0.95 | 1.00 | NEGATIVE: REGIME-ONLY |
| VB2NYAM_T3 | 0.889 | 1576 / 2114 | -2.31 (-4.2) | -2.65 (-4.5) | 1/10 / 1/11 | +0.61 / +0.27 | 0.98 / 0.85 / 0.98 / 1.00 | 1.00 | 1.00 | no formal verdict (calibration 0.89) |
| OR15NYAM_T2 | 0.941 | 2165 / 2299 | +0.35 (0.4) | +1.12 (0.9) | 3/11 / 8/11 | +2.51 / +1.45 | 0.03 / 0.71 / 0.01 / 0.02 | 0.25 | 1.00 | NULL |
| ONRTH | 0.922 | 1472 / 1476 | -0.83 (-1.0) | -1.49 (-1.4) | 4/11 / 4/11 | +1.01 / +0.87 | 0.63 / 0.21 / 0.24 / 0.55 | 1.00 | 1.00 | NEGATIVE: REGIME-ONLY |
| VWAPF | 0.875 | 2006 / 2944 | -1.37 (-1.4) | -1.15 (-1.2) | 4/11 / 4/11 | +2.19 / -0.52 | 0.40 / 0.13 / 0.31 / 0.50 | 1.00 | 1.00 | no formal verdict (calibration 0.88) |
| Z1_SWING | 0.925 | 413 / 774 | -5.98 (-2.3) | -5.68 (-2.9) | 1/5 / 1/10 | +1.69 / -0.21 | 1.00 / 1.00 / 1.00 / 1.00 | 1.00 | 1.00 | NEGATIVE: REGIME-ONLY |
| G1_NQES | 0.907 | 2868 / 2868 | -3.13 (-6.4) | -3.79 (-5.4) | 0/11 / 0/11 | +0.85 / +0.06 | 1.00 / 1.00 / 1.00 / 1.00 | 1.00 | 1.00 | NEGATIVE: REGIME-ONLY |
| DISQ_1500_IMB | 0.943 | 2470 / 2470 | -1.83 (-3.2) | -1.84 (-2.5) | 0/11 / 2/11 | +2.54 / +2.11 | 0.78 / 0.62 / 0.84 / 0.79 | 1.00 | 1.00 | NEGATIVE: REGIME-ONLY |
| DISQ_1550_DRIFT | 0.832 | 2465 / 2465 | -2.44 (-5.3) | -2.94 (-4.7) | 0/11 / 1/11 | +0.12 / -0.04 | 0.99 / 0.99 / 0.99 / 0.99 | 1.00 | 1.00 | no formal verdict (calibration 0.83) |
Reading. (1) Nothing REPLICATES: every q_BH is 1.00 (the family max-T is 0.18-1.00; the smallest is OR15 in PCT, 0.18-0.25). (2) The four new lines are negative before 2023 in both frames, by large margins (G1: 0 of 11 years positive in both frames, t -6.4/-5.4; DIS-Q 15:00: 0 of 11 RAW). (3) PCT does not rescue anything: Q13 -2.1 -> -1.0, DIS-B -1.3 -> -1.5, DIS-C -3.6 -> -4.7, ONRTH -0.8 -> -1.5; DIS-K +0.55 -> -0.25 (the RAW positive does not survive the percent conversion; it was never significant); OR15 NYAM T2 +0.35 -> +1.12 (8 of 11 years positive in PCT, p 0.03 vs side shuffle, 0.01 vs delayed entry and 0.02 vs random day, but the shift5 placebo p is 0.71, i.e. delaying entry by 1-5 minutes does as well, and q_BH 1.00 after the family correction: NULL). (4) In-sample 2023-26 means in the PCT frame are lower than RAW for every line and negative for VWAPF, Z1 swing, DISQ 15:50 and about zero for G1: part of the 2023-26 'edge' of these lines is a fixed-point sizing effect at 2026 prices. (5) The calibration cut matters for formal verdicts only (five lines: DIS-K, VB2 NYPM T1, VB2 NYAM T3, VWAPF, DISQ 15:50); their signs agree with the verdicted lines.

## 4. One table: every watch candidate with its pre-2023 verdict (source file per row)
| watch candidate (RANKED LIST / DIS-T) | program | pre-2023 verdict | OOS mean pt per lot-trade (RAW / PCT) | source file |
|--|--|--|--|--|
| C1 T-FADE Z1 swing failed break (nyam) | Z1 / DIS-BM | NEGATIVE: REGIME-ONLY (t -2.3 / -2.9; 1 of 5-10 years positive) | -5.98 / -5.68 | DS3_OOS_REMAINING.md; /mnt/l2/l2vast/ds3_dbm/oos_*.pkl |
| C2 DIS-B P_REL_cont_m1.0 (pre-market) | S4a / DIS-W, DIS-BM | NEGATIVE: REGIME-ONLY (t -2.5 / -2.0) | -1.34 / -1.49 | DS3_HISTORY_EXTENSION.md; DS3_OOS_REMAINING.md |
| C3 DIS-B N_REL_rev_m0.5 (nyam) | S4a / DIS-AA | SURVIVES PRE-2023 on the weak excess-over-drift rule, not on the strong one; level -0.41 pt per trade pre vs +2.13 post (not run here) | -0.41 (V2 scale, DIS-AA) | DS3_FADE_OOS.md |
| C4 DIS-K BO COMP_HI nyam | Z2 / DIS-W, DIS-BM | no formal verdict (calibration 0.83); level +0.55 RAW (n.s., positive only in 2019/2020/2022), -0.25 PCT | +0.55 / -0.25 | DS3_HISTORY_EXTENSION.md; DS3_OOS_REMAINING.md |
| C5 DIS-C Sunday 18:30 with-trend | S4b / DIS-W, DIS-BM | NEGATIVE: REGIME-ONLY (t -4.6 / -4.4; 1 of 8 years positive) | -3.62 / -4.71 | DS3_HISTORY_EXTENSION.md; DS3_OOS_REMAINING.md |
| C6 DIS-E prevday-FAILURE nyam | S4b | NOT TESTABLE on owned data (refill-failure count needs L2/mbp; mbo starts 2017-05, mbp-1 $394 for 2021-23; not owned) | - | DS3_HISTORY_EXTENSION.md section 5 |
| C7 DIS-G (Z1) G1 NQ-ES ratio reversion nyam | Z1 / DIS-BM | NEGATIVE: REGIME-ONLY (t -6.4 / -5.4; 0 of 11 years positive) | -3.13 / -3.79 | DS3_OOS_REMAINING.md |
| C8 DIS-J N_CENT NYAM T4 | ZL-1 | NOT TESTABLE (NDX options open interest has no pre-2023 history on disk) | - | DS3_HISTORY_EXTENSION.md |
| C9 Q13 middle-tercile gap-fill | ZL-1 / DIS-W, DIS-BM | NEGATIVE: REGIME-ONLY (t -1.4 / -0.7) | -2.10 / -0.98 | DS3_HISTORY_EXTENSION.md; DS3_OOS_REMAINING.md |
| C10 DIS-Q 15:00 signed-volume imbalance fade | CAL / DIS-BM | NEGATIVE: REGIME-ONLY (t -3.2 / -2.5) | -1.83 / -1.84 | DS3_OOS_REMAINING.md |
| DIS-Q 15:50 drift fade | CAL / DIS-BM | no formal verdict (calibration 0.83); mean -2.44 / -2.94, t -5.3 / -4.7 | -2.44 / -2.94 | DS3_OOS_REMAINING.md |
| T-FADE VB2 NYPM T1 (live Shadow) | BASE-4 / DIS-W, DIS-BM, DIS-AA | no formal verdict (calibration 0.80); -0.95 / -0.82; DIS-AA excess-over-drift weak rule SURVIVES | -0.95 / -0.82 | DS3_FADE_OOS.md; DS3_HISTORY_EXTENSION.md |
| T-FADE VB2 NYAM T3 (live Shadow) | BASE-4 / DIS-W, DIS-BM | no formal verdict (calibration 0.89); sign robust: -2.31 / -2.65, t -4.2 / -4.5, 1 of 10 years positive | -2.31 / -2.65 | DS3_HISTORY_EXTENSION.md; DS3_OOS_REMAINING.md |
| T-FADE PD ASIA T2 (live Shadow) | BASE-4 / DIS-W, DIS-BM | NEGATIVE (marginal; -0.31 / -0.59) | -0.31 / -0.59 | same |
| T-FADE OR15 NYAM T2 (optional REGIME line) | BASE-4 / DIS-W, DIS-BM | NULL (+0.35 RAW / +1.12 PCT; all RAW gain from 2022; shift5 placebo p 0.71 in PCT: the edge is not entry-timing specific) | +0.35 / +1.12 | same |
| NYAM bundle books ONRTH | CAL / DIS-W, DIS-BM, DIS-AA | NEGATIVE (n.s.; -0.83 / -1.49); DIS-AA weak rule SURVIVES | -0.83 / -1.49 | same + DS3_FADE_OOS.md |
| NYAM bundle books VWAPF | CAL / DIS-W, DIS-BM, DIS-AA | no formal verdict (calibration 0.875); -1.37 / -1.15; DIS-AA: POST-2023 ONLY | -1.37 / -1.15 | same |
| NYAM bundle book ORBF and the 3-book bundle | CAL / DIS-AA | DIS-AA: ORBF +0.27 pt per trade pre, weak rule SURVIVES; bundle -0.49 pre; ORBF-B2 variant: not run here, owner not confirmed (ZL-2 has no DIS-BK) | +0.27 (ORBF, DIS-AA) | DS3_FADE_OOS.md |
| six live books' raw entries (ST, HM, WT, KB, SM, PE) | ZL-2 / DIS-Y | all six lost money 2013-2022 (-0.6 to -2.4 pt per trade) and made money in 2023-26; stack-level 1-min approximation failed validation (0.66-0.69) | -0.6 .. -2.4 | DS3_SIGNALS_2013.md |
| Q9 London sleeve off after wide low-ER Asia; sizers VT_Q1A and Z3_RVD30; T-INSTR YM U7 NYPM | ZL-2 / ZL-1 / T-INSTR | NOT RUN (overlays and sizers need the stack P&L, which failed 1-min validation; YM 1-min is owned and the U7 pocket could be run next) | - | - |

## 5. Limits
Same as DIS-W: one feed, volume-front additive back-adjustment with roll days dropped, 1-minute fills (late and rough: levels differ from the 1-s tables; correlations above), signal-level objects (no Trade-Health, locks, zones, 70/30). The DIS-Q volume sign is a bar proxy of the research feature (the research code itself uses it). The PCT frame is a per-roll-segment rescale, not a per-trade r. NYAM ORBF-B2 is not in this set: the lead named Z2's 'DIS-BK', but ZL-2 reports no DIS-BK assignment, so no owner is confirmed; BASE-4's DIS-AA ran ORBF. Not run (feasible): T-INSTR YM U7 NYPM pocket (YM 1-minute owned), RTY lines (RTY from 2017-07).

## WATCH LINES: PRE-2023 STATUS (appended by ZL-1, 2026-11-05; all programs, one table)
Sources: DIS-W (DS3_HISTORY_EXTENSION.md), DIS-BM (this file), DIS-BS (DS3_INSTR_OOS.md), DIS-AA (DS3_FADE_OOS.md), DIS-BK (DS3_ORBF_B2.md), DIS-Y (DS3_SIGNALS_2013.md). Level objects = mean points (or R) per trade of the 1-minute signal-level line, OOS 2013-01..2023-04-02; DIS-AA / DIS-BK also report excess over drift benchmarks.
| watch line | pre-2023 result | verdict | source |
|--|--|--|--|
| Z1 swing failed break (nyam) | -6.0 / -5.7 pt (raw / pct), t -2.3 / -2.9 | NEGATIVE: REGIME-ONLY | DS3_OOS_REMAINING.md |
| DIS-B P_REL_cont (pre) | -1.3 / -1.5, t -2.5 / -2.0 | NEGATIVE: REGIME-ONLY | DS3_HISTORY_EXTENSION.md, DS3_OOS_REMAINING.md |
| DIS-B N_REL_rev_m0.5 (nyam) | -0.41 pt per trade (V2); excess over drift +45 $/wk vs P1c, 7 of 10 years, CI (-59,+153) | weak rule SURVIVES, strong rule none; level negative | DS3_FADE_OOS.md |
| DIS-K BO COMP_HI (nyam) | +0.55 raw (n.s.), -0.25 pct | no formal verdict (calibration 0.83) | DS3_OOS_REMAINING.md |
| DIS-C Sunday 18:30 | -3.6 / -4.7, t -4.6 / -4.4 | NEGATIVE: REGIME-ONLY | same |
| DIS-E prevday-FAILURE (nyam) | not testable (refill-failure needs L2) | NOT TESTABLE | DS3_HISTORY_EXTENSION.md |
| DIS-G G1 NQ-ES ratio (nyam) | -3.1 / -3.8, t -6.4 / -5.4, 0 of 11 years positive | NEGATIVE: REGIME-ONLY | DS3_OOS_REMAINING.md |
| DIS-J N_CENT NYAM T4 | not testable (no pre-2023 options OI) | NOT TESTABLE | DS3_HISTORY_EXTENSION.md |
| Q13 middle-tercile gap-fill | -2.1 / -1.0 | NEGATIVE: REGIME-ONLY | same |
| DIS-Q 15:00 IMB fade | -1.8 / -1.8, t -3.2 / -2.5 | NEGATIVE: REGIME-ONLY | DS3_OOS_REMAINING.md |
| DIS-Q 15:50 DRIFT fade | -2.4 / -2.9 | no formal verdict (calibration 0.83) | same |
| T-INSTR YM U7 NY-PM pocket (75 pt) | -0.050 R raw (t -1.96), -0.040 R pct; 0 of 181 neighbourhood cells with q <= 0.10 | NEGATIVE: REGIME-ONLY | DS3_INSTR_OOS.md |
| T-INSTR BTC K7 London | 10 months only (CME BTC owned from 2022-01): -0.085 R, MDE 0.20 R | NO INFORMATION (not verdict-grade) | DS3_INSTR_OOS.md |
| NYAM ORBF-B2 (1-min close beyond) | signal-level excess over drift positive in 7 / 8 / 8 of 10 pre-2023 years (weak rule passes; strong only vs other-day and delayed fade, not vs P1c: CI [-12, +354]); post-2023 PRE -1,403 / X' -594 $/wk, tolerant gate fails; selection charge N = 350 | REGIME (NOW-ONLY) / Shadow-watch; weak pre-2023 support in excess-over-drift form | DS3_ORBF_B2.md |
| NYAM ORBF (per-second, 1-min proxy) | +0.27 pt per trade pre-2023 (V2), +26 $/wk; excess +171 vs P1c | weak rule SURVIVES (not a PASS) | DS3_FADE_OOS.md |
| NYAM ONRTH / VWAPF / 3-book bundle | ONRTH -0.83 / -1.49 pt (DIS-W / BM) vs +0.05 (DIS-AA V2); VWAPF no verdict, DIS-AA POST-2023 ONLY; bundle -0.49 pt, excess +331 $/wk vs P1c (CI -33..+724) | ONRTH NEGATIVE (n.s.); VWAPF POST-2023 ONLY; bundle weak rule SURVIVES | DS3_HISTORY_EXTENSION.md, DS3_FADE_OOS.md |
| T-FADE VB2 NYPM T1 / VB2 NYAM T3 / PD ASIA T2 / OR15 NYAM T2 | -0.95 (no verdict, DIS-AA weak rule survives) / -2.31 (t -4.2, no formal verdict, sign robust) / -0.31 (NEGATIVE marginal) / +0.35 raw, +1.12 pct (NULL: shift5 placebo p 0.71) | none replicates | DS3_HISTORY_EXTENSION.md, DS3_OOS_REMAINING.md |
| six live books' raw entries (ST HM WT KB SM PE) | all six lost money in 2013-2022 (-0.6 to -2.4 pt per trade) and made money in 2023-26 | 2023-26 in the best 5% of the 2013-2023 block bootstrap for 5 of 6 | DS3_SIGNALS_2013.md |
| Q9 London sleeve, sizers VT_Q1A / Z3_RVD30 | stack-level objects: the 1-minute stack approximation failed validation (0.66-0.69) | NOT RUN | DS3_SIGNALS_2013.md |

**Pooled-sleeve implication (one sentence): no watch line has positive pre-2023 evidence at the level of points per trade (the equal-weight sum of the 14 DIS-W / DIS-BM lines at their own lots was about -$3,160 a week in the percent frame over 2013-2023, only OR15 NYAM T2 positive and not significant), the only weak positive pre-2023 support is the NY-AM reversion family's signal-level EXCESS OVER DRIFT (ORBF, ORBF-B2, N_REL_rev, ONRTH, VB2 NYPM T1, the 3-book bundle on the weak rule, with confidence intervals that include zero), so a pooled sleeve of the 2026 watch lines should be treated as a 2026-regime sleeve with a pre-2023 expectation of zero or below, not as a diversified edge.**
