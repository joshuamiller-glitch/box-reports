# DS3_THL_HM_RETEST - HM-only loss-side re-test: prereg, seen-data analyses, forward spec (THLHM, 2026-10-29)

Research only. No live, execution-server or chart change; the forward register and every live file are untouched; nothing deleted, nothing killed, no replay workers. UNTOUCHED (trade date > 2026-02-06) never read. Fees per FEES.md ($4.84/contract RT = 0.242 pt, same in both arms, cancels in every paired delta). No account ids.
Prereg: l2vast/ds3/prereg/THL_HM_RETEST_prereg.md, sha256 261e9e1c0f54b3dcaa709abe9e19e1d3079509686da01c49776b219d3401f832 (includes amendment A1; first version 3500913171b2e95ded3a5bd13ca6f2909bf7a199e8301c642ab38a86371b9a0b), both logged in DECISIONS.md. Code l2vast/ds3/code/thl_hm/ (thl_hm_retest.py sha256 ce37776e...72db06, thl_hm_supp.py sha256 d25110b5...91ad; thl_rules originals untouched). Outputs l2vast/ds3/out/thl_hm/.

## 0. The honest position
**This is a re-test on data already seen.** The nine cells came out of a 158-rule search that had looked at X, PRE and HOLD. Nothing below is a fresh test, and the best any seen-data pass can be is CANDIDATE-SEEN ("worth a fresh test"). **The one fresh look has NOT been taken and cannot be taken until the user names a fresh window or the forward sample exists.** Disclosure: the thresholds were frozen after the six old-grid cells' THLB numbers had been seen; unseen when frozen were the three window-20 cells (not in the original 158: windows there were 10/30/60/120), the week-block bootstrap, the per-cell adjusted p and the power table.

## 1. The prereg in one screen
* Stream HM (stack HM book, 2,924 trades, 2023-04-03..2026-02-06, 60 stop / 60 target / 16:55 flat, 10 lots), same entries in both arms. Comparison = hold-to-stop (stored bracket intact).
* Cells L6_a{20,25,30}_r3_w{10,20,30}: eligibility = adverse excursion >= A pts; evaluated at the close of each second; conditions (as in live L6_a15_r3_w30): C1 price >= 4.0 pts worse than W seconds ago; C2 no new adverse extreme for >= W s and recovery from it <= 4.0 pts; C3 efficiency |net|/path over W s < 0.35; 3 of 3 required; exit = whole position at market at the decision-second close.
* Fill basis MEASURED = market exit +1 tick (0.25 pt) adverse, stop walk by year (0.85/1.13/1.74/1.71), P9 target correction; CONSERVATIVE label = basis C (stop walk +0.5, 3-s delay, 2 ticks, target 0.5 worse). N and MW also shown.
* Primary (frozen): L6_a30_r3_w10. Gates for CANDIDATE-SEEN, all required (no one-failure allowance): G1 mean>0 in X, PRE and HOLD; G2 week-block bootstrap 95% CI (B=10,000) excludes 0 on all seen data; G3 C, N, MW all > 0; G4 reality check, own adjusted p < 0.05 in the 161-cell family (HM 158 + 3 new cells); G5 timing-matched placebo rank >= 0.95; G6 grid neighbours agree in sign; G7 largest-year share <= 60%; G8 n >= 1,000.
* Fresh look (not taken): one look, logged as THLHM_FRESH, all nine cells; primary passes if M mean > 0 with week-block CI lower bound > 0, C mean > 0 and >= 7 of 9 cells positive -> CONFIRMED-FRESH (still needs a live shadow). Mean <= 0 -> DEAD. Positive but CI includes 0 -> INCONCLUSIVE, stays LEAD. Look allowed at >= 1,000 fresh HM trades or a user-named window with the stated power (A1).

## 2. HM trade counts (exact)
| window | label days | trades | trading days | weeks | trades/week | SD of a trade (hold-to-stop, pts) | hold-to-stop net pts/trade |
|---|---|---|---|---|---|---|---|
| X | 20230403..20240131 | 665 | 216 | 44 | 15.1 | 57.2 | +1.51 |
| PRE | 20240201..20250630 | 1,561 | 364 | 75 | 20.8 | 58.4 | +0.35 |
| HOLD | 20250701..20260206 | 698 | 157 | 32 | 21.8 | 57.3 | -0.43 |
| ALL seen | | 2,924 | 737 | 149 | 19.6 | 57.9 | +0.43 |

Per cell (ALL seen): armed trades (MAE >= A) and trades where the rule actually fires. The paired delta is exactly zero on the unarmed and the non-firing trades, so the information sits in the fired trades.
| A | armed | fired w10 | fired w20 | fired w30 |
|---|---|---|---|---|
| 20 | 2,100 | 1,471 | 1,770 | 1,823 |
| 25 | 1,950 | 1,357 | 1,632 | 1,682 |
| 30 | 1,829 | 1,240 | 1,491 | 1,548 |
Armed/fired by window (PRE/HOLD/X) for every cell: out/thl_hm/cells_windows.csv. The recomputed six old-grid cells match the sealed THLB deltas to 4e-6 pt (reproducibility check passed).

## 3. Effect by window, MEASURED basis (pts/trade, paired delta vs hold-to-stop, net of fees both arms; day-by-session cluster 95% CI; MDE = 2.8 SE)
| cell | PRE | HOLD | X | ALL [CI] (MDE) | N / MW / C (ALL) | placebo rank ALL | $/wk ALL (10 lots) |
|---|---|---|---|---|---|---|---|
| a20 w10 | +0.89 | +1.81 | +0.95 | +1.12 [-0.11,+2.35] (1.76) | 0.88/0.78/1.24 | 1.00 | 4,409 |
| a20 w20 | +0.66 | +1.15 | +0.85 | +0.82 [-0.59,+2.23] (2.02) | 0.49/0.40/1.04 | 0.95 | 3,220 |
| a20 w30 | +0.87 | +1.63 | +1.17 | +1.12 [-0.33,+2.57] (2.07) | 0.77/0.69/1.29 | 1.00 | 4,393 |
| a25 w10 | +1.22 | +1.37 | +0.45 | +1.08 [-0.05,+2.22] (1.62) | 0.89/0.76/1.19 | 0.92 | 4,248 |
| a25 w20 | +0.96 | +1.51 | +0.82 | +1.06 [-0.24,+2.36] (1.86) | 0.80/0.67/1.25 | 0.85 | 4,155 |
| a25 w30 | +0.91 | +1.76 | +1.27 | +1.19 [-0.14,+2.53] (1.91) | 0.92/0.79/1.35 | 0.95 | 4,682 |
| **a30 w10 (primary)** | +1.37 | +1.82 | +0.06 | +1.18 [+0.18,+2.18] (1.43) | 1.04/0.89/1.28 | 0.95 | 4,626 |
| a30 w20 (new) | +1.32 | +2.30 | +1.39 | +1.57 [+0.43,+2.71] (1.63) | 1.39/1.21/1.74 | 1.00 | 6,154 |
| a30 w30 | +1.19 | +1.92 | +1.43 | +1.42 [+0.23,+2.60] (1.69) | 1.22/1.05/1.57 | 0.98 | 5,565 |
(The ALL CI shown is the cluster CI; the gate CI is the week-block bootstrap in section 5.) By-year means (2023/2024/2025/2026, n 581/1,018/1,206/119) for the primary: -0.53 / +1.53 / +1.57 / +2.56 (2026 n is small); for a30 w20: +0.70 / +1.58 / +1.67 / +4.67. Files: by_year.csv, year_share.csv.

## 4. Power and the future sample needed
Per-trade effective SD (cluster-adjusted) sigma_eff: primary 27.6 pts, a30 w20 31.5. n80 = (2.8 sigma_eff / d)^2. HM runs 19.6 trades/week (live HMStrat shows 18 trades in its first full live week, consistent).
| cell | observed d | n80 at d (HM trades / weeks) | n80 at d/2 (winner's-curse haircut) | n80 at the PRE effect | MDE at 13 / 26 / 52 / 104 wk |
|---|---|---|---|---|---|
| a30 w10 (primary) | 1.18 | 4,304 / **219 wk** | 17,215 / 877 wk | 3,200 / 163 wk | 4.84 / 3.42 / 2.42 / 1.71 |
| a30 w20 | 1.57 | 3,167 / 161 wk | 12,668 / 646 wk | 4,474 / 228 wk | 5.52 / 3.91 / 2.76 / 1.95 |
| a30 w30 | 1.42 | 4,161 / 212 wk | 16,645 / 848 wk | 5,912 / 301 wk | 5.73 / 4.05 / 2.86 / 2.02 |
(All nine cells: out/thl_hm/power.csv; a20 w20 needs 901 weeks.) **Weeks until MDE equals the observed effect: 219 for the primary, 161 for a30 w20, i.e. 3-4 years of one book's trades.** Power of a forward look for the primary at the observed effect (half effect): 21 wk 14% (6%), 35 wk 20% (8%), 52 wk 28% (10%), 104 wk 49% (16%), 156 wk 66% (22%), 219 wk 80% (29%). A single-book forward test cannot confirm a +1.2 pt effect within a year; it can only reject a large one (a +2.4 pt effect is detectable at 52 weeks). The weekly view agrees: +$4.6k/wk mean against a weekly SD of $25.0k.

## 5. Block bootstrap by week on ALL already-seen data - NOT A FRESH TEST
B = 10,000, 149 weeks, seed 20261029, percentile 95% CI of the paired delta (pts/trade); C = CONSERVATIVE basis.
| cell | M mean | M CI | P(d>0) | C mean | C CI |
|---|---|---|---|---|---|
| a20 w10 | +1.12 | [+0.02,+2.21] | 0.977 | +1.24 | [+0.13,+2.32] |
| a20 w20 | +0.82 | [-0.49,+2.11] | 0.886 | +1.04 | [-0.26,+2.32] |
| a20 w30 | +1.12 | [-0.19,+2.41] | 0.953 | +1.29 | [-0.01,+2.58] |
| a25 w10 | +1.08 | [+0.05,+2.09] | 0.980 | +1.19 | [+0.16,+2.20] |
| a25 w20 | +1.06 | [-0.12,+2.20] | 0.962 | +1.25 | [+0.08,+2.40] |
| a25 w30 | +1.19 | [+0.03,+2.36] | 0.977 | +1.35 | [+0.18,+2.51] |
| **a30 w10** | +1.18 | [+0.17,+2.18] | 0.990 | +1.28 | [+0.28,+2.28] |
| a30 w20 | +1.57 | [+0.49,+2.61] | 0.998 | +1.74 | [+0.67,+2.78] |
| a30 w30 | +1.42 | [+0.34,+2.49] | 0.995 | +1.57 | [+0.48,+2.64] |
Per-window bootstraps (PRE, HOLD, X): out/thl_hm/boot_week.csv; no cell's CI excludes 0 in PRE or X, and only a30 w20 does in HOLD (+0.09..+4.50). The gain is a pooled-over-windows result; it does not stand in any single window.

## 6. Multiplicity (the part that decides it)
White reality check, week-block, studentised, per-cell single-step adjusted p:
| scope | best cell | p |
|---|---|---|
| PRE only, HM 158 (as in THLB) | a30 w10 | 0.262 (THLB 0.266) |
| PRE only, 161 | a30 w10 | 0.265 |
| ALL seen, 9 cells | a30 w20 | 0.0065 |
| ALL seen, HM 158 | a30 w30 | 0.074 |
| **ALL seen, 161 (G4)** | **a30 w20** | **0.0325** |
| ALL seen, **3,479 cells (22 streams x 158 + 3), supplementary** | a30 w20 | **0.5165** |
Per-cell adjusted p in the 161 family: a30 w20 0.033; a30 w30 0.075; a30 w10 (primary) 0.141; a25 w10 0.213; a20 w10 0.231; a25 w30 0.233; a25 w20 0.316; a20 w30 0.360; a20 w20 0.620. In the 3,479-cell family a30 w20 is 0.52 and the primary 0.90. HM was chosen as the nearest miss out of 22 streams, so the 3,479-family number is the more honest reading of "how surprising is this".

## 7. Seen-data gate result
| cell | G1 sign X/PRE/HOLD | G2 boot CI>0 | G3 C,N,MW>0 | G4 own adj p<0.05 | G5 placebo>=0.95 | G6 nbrs | G7 yr share<=60% | verdict |
|---|---|---|---|---|---|---|---|---|
| a20 w10 | pass | pass | pass | 0.231 FAIL | 1.00 | pass | 0.54 | NO-CANDIDATE |
| a20 w20 | pass | FAIL | pass | 0.620 FAIL | 0.95 | pass | 0.38 | NO-CANDIDATE |
| a20 w30 | pass | FAIL | pass | 0.360 FAIL | 1.00 | pass | 0.46 | NO-CANDIDATE |
| a25 w10 | pass | pass | pass | 0.213 FAIL | 0.92 FAIL | pass | 0.50 | NO-CANDIDATE |
| a25 w20 | pass | FAIL | pass | 0.316 FAIL | 0.85 FAIL | pass | 0.46 | NO-CANDIDATE |
| a25 w30 | pass | pass | pass | 0.233 FAIL | 0.95 | pass | 0.43 | NO-CANDIDATE |
| **a30 w10 (primary)** | pass (X +0.06) | pass | pass | **0.141 FAIL** | 0.95 | pass | 0.56 | **NO-CANDIDATE** |
| a30 w20 | pass | pass | pass | pass (0.0325) | 1.00 | pass | 0.55 | CANDIDATE-SEEN (nominal) |
| a30 w30 | pass | pass | pass | 0.075 FAIL | 0.98 | pass | 0.48 | NO-CANDIDATE |

**Reading it plainly.** The frozen primary (a30 w10) does NOT pass: the best-of-N correction (own p 0.141) fails, as it did in THLB. One cell, a30 w20 (a window that was not in the original grid and was found by scoring new cells on seen data), passes every gate as written; that earns it CANDIDATE-SEEN at most, because (a) it is the best of the 3 new cells on data that all the neighbours had already seen, (b) against the full 3,479-cell search it is p = 0.52, (c) no single window excludes zero except HOLD for this cell, and (d) 2023 for the primary is negative. It is a reason to run the fresh test, not evidence of an edge. HM is also the book whose hold-to-stop is weakest (+0.43 pt/trade), and the same rules are negative on the other books (pooled L6_a30_r3_w10 -0.23 PRE).

## 8. The forward test (accrues live as paper data without reading UNTOUCHED now)
Forward-register entry spec (a document only; the register and live files are not edited; to be registered by whoever owns ap_forward_register.py after the user approves). Format follows autopilot/forward/ap_forward_register.py (record JSON in l2vast/struct48/paper_all/<cell_id>.json, picked up by `watch`; verdict rules PROMOTE >= 6 weeks and z >= -1, RETIRE >= 8 weeks and z < -2, official weeks start Sunday 18:00 ET).
* Start: first entry on/after **Sunday 2026-11-01 18:00 ET (official week 2026-W45)**; entries before that are excluded (live HMStrat entries since 2026-10-20 exist but W43/44 are informational in the register). Nothing dated 2026-02-07 .. 2026-10-31 is read by this spec; that span stays sealed.
* Cell tags (nine, all HM, all paired against hold-to-stop on the same live HM entry): `THLHM_L6_a30_r3_w10` (PRIMARY), `THLHM_L6_a30_r3_w20`, `THLHM_L6_a30_r3_w30`, `THLHM_L6_a25_r3_w10`, `THLHM_L6_a25_r3_w20`, `THLHM_L6_a25_r3_w30`, `THLHM_L6_a20_r3_w10`, `THLHM_L6_a20_r3_w20`, `THLHM_L6_a20_r3_w30`. Compact tag: THLHM_a{A}_w{W}.
* object_type `trade_modifier`; tier `CANDIDATE` (the register only has CANDIDATE|PASS; the real status is LEAD / seen-data only, put that in `mechanism`); parameters {book:"HM", rule:"L6", adverse:A, required:3, window_s:W, exit:"market at decision-second close", basis:"MEASURED +1 tick, CONSERVATIVE label basis C", comparison:"hold-to-stop", prereg_sha256:"261e9e1c..."}.
* The exact rule is the section 1 rule: eligible at adverse excursion >= A; each second close, 3 of {>=4.0 pts adverse over W s; no new extreme for >= W s with recovery <= 4.0; efficiency < 0.35 over W s}; cut at market. The delta per trade = (pts of the loss-rule exit - pts of the stored 60/60 bracket on the same entry) x lots x $20, both net of $4.84/contract.
* Expectation fields (from ALL-seen, to be shown as expected, with the haircut flagged): expect_mean_wk = $4,626 (primary), $6,154 (a30 w20), $5,566 (a30 w30), $4,682 (a25 w30), $4,248 (a25 w10), $4,409 (a20 w10); expect_sd_wk = $24,993 / 26,457 / 26,856 / 28,964 / 25,450 / 27,094; per_trade_effect 1.18 / 1.57 / 1.42 / 1.19 / 1.08 / 1.12 pts. Because the register's z-test of realised vs expected has power ~ 28% in 52 weeks, a "RETIRE" call should not be read as proof either way; also state the haircut case (half) as the planning expectation.
* Shadow evaluator: `{"kind":"script","path":"autopilot/forward/cell_shadows/thlhm_<tag>.py"}` (to be written by the owner; trade_mult cannot express an intra-trade path rule). Because live HMStrat has the loss TH at 15/3/30 switched ON, the live HM exits are already cut; the evaluator must therefore score BOTH arms from the entry (time, side) and the 1-second path, not from the live exit. The research 1-s path array ends 2026-02-06, so the evaluator needs a 1-s (or tick) NQ series for 2026-11-01 onward (an ingestion task not done here). Without it the cells sit as AWAITING EVALUATOR.
* **Weeks to MDE:** for the primary, MDE reaches the observed +1.18 pt effect after 219 weeks (about 4,300 HM trades; about early 2031 from a 2026-11-01 start); 161 weeks for a30 w20; the half-effect planning case needs ~877 weeks. At 52 weeks (about 1,020 trades, 2027-10-31) the MDE is 2.4 pts (power 28% / 10%); at 104 weeks 1.7 pts. A1 lets the single fresh look run at >= 1,000 trades (about week 51, ~2027-10-24) with that stated power.

## 9. What can and cannot happen next
* The one fresh look cannot be taken until the user names a fresh window or the forward sample exists (>= 1,000 HM trades by A1, about 51 weeks from 2026-11-01).
* Window options for main to put to the user (all need the 1-s path extended past 2026-02-06, which this box does not have): 
  (A) forward-only from 2026-11-01 (nothing unlocked; ~51 weeks to 1,000 trades; power 28% at the observed effect, 10% at half). 
  (B) unlock UNTOUCHED 2026-02-07..2026-06-30 (about 21 weeks, ~410 HM trades; power 14% / 6%): inexpensive, but too thin to confirm anything and burns the span for every other study. 
  (C) unlock UNTOUCHED 2026-02-07..2026-10-31 (about 38 weeks, ~745 trades; power ~21% / 8%), then forward continues after it; best immediate sample but still underpowered. 
  (D) C plus forward, looked at once at the 1,000-trade mark (covers 2026-02-07 .. ~2027-02): pooled power ~28% / 10%, and a mean <= 0 would still kill the lead early. 
  Recommendation: D if the user is willing to unlock a span of UNTOUCHED, otherwise A with the forward tracker as a monitor; do not expect a confirmation either way inside a year unless the true effect is >= 2.4 pts.
* Open user decision: keep a30 w10 as the only primary (default) or add a30 w20 as co-primary with Holm at 0.025 each; a30 w20 is the only cell that passes all seen-data gates, but it was found after the primary was frozen.

## 10. Files
Prereg + sha: l2vast/ds3/prereg/THL_HM_RETEST_prereg.md / .sha256; code l2vast/ds3/code/thl_hm/{thl_hm_retest.py, thl_hm_supp.py}; outputs l2vast/ds3/out/thl_hm/{counts.csv, cells_windows.csv, boot_week.csv, year_share.csv, by_year.csv, power.csv, rc_nb.json, supp.json, hm9.npz}; DECISIONS.md lines THLHM PREREG and AMENDMENT A1.
